---
name: koreai-invoke-deployed-agent
description: Send a message to a deployed Kore.ai Agent Platform agent, streaming or non-streaming, and handle the platform's error and rate-limit semantics correctly.
api: Kore.ai Agent Platform ABL Runtime API — Conversation
operations:
  - runtime.agent.chat
  - runtime.agent.complete
  - runtime.agent.stream
---

# Invoke a deployed Kore.ai agent

Every operation named here is verified against
`openapi/koreai-abl-runtime-conversation-openapi.json`. Do not call an operation that is
not in this list.

## Before you start

- Base URL is `https://agents.kore.ai` for USA-Central. Other regions use a prefixed host
  (`uk-agents.kore.ai`, `de-agents.kore.ai`, `jp-agents.kore.ai`, `au-agents.kore.ai`,
  `sg-agents.kore.ai`, `uae-agents.kore.ai`, `ksa-agents.kore.ai`, `ind-agents.kore.ai`,
  `us-swift-agents.kore.ai`). Pick the host your workspace lives in — the wrong region is
  not a redirect, it is a different tenant.
- Authenticate with `Authorization: Bearer <token>`, where the token is either a JWT issued
  after login or a long-lived API key prefixed `abl_`. Service-to-service callers may
  instead send `X-API-Key`. See `authentication/koreai-authentication.yml`.
- You need the `projectSlug`, the environment segment `env`, and the `agentSlug`. These are
  slugs, not the IDs the management surface uses.

## Choose the operation

| Need | Operation | Path |
| --- | --- | --- |
| Conversational turn, full response | `runtime.agent.chat` | `POST /api/v1/project/{projectSlug}/{env}/agent/{agentSlug}/chat` |
| One-shot completion, no session | `runtime.agent.complete` | `POST /api/v1/project/{projectSlug}/{env}/agent/{agentSlug}/complete` |
| Token-by-token output | `runtime.agent.stream` | `POST /api/v1/project/{projectSlug}/{env}/agent/{agentSlug}/stream` |

Do **not** use `runtime.legacyChat.agent`, `runtime.legacyChat.stream`,
`runtime.legacyChat.complete` or `runtime.legacyChat.createSession`. All four are marked
`deprecated: true` in the published spec and the spec names the deployment-scoped routes
above as the replacement.

## Streaming

`runtime.agent.stream` returns `Content-Type: text/event-stream`. Handle three named
events — `text_delta` (incremental output), `usage` (input/output token counts) and
`complete` (final totals plus `latencyMs`). A `: heartbeat` comment arrives every 15
seconds; ignore it, and do not treat 15 seconds of only-heartbeats as a stall.

## Reading the response

Success is `{"success": true, "data": {...}}`, though some endpoints return a
domain-specific top-level key instead of `data`. `success` is always present — branch on it,
not on the presence of `data`.

Errors are `{"success": false, "error": {"code": "...", "message": "..."}}`, and some
endpoints return the simplified `{"error": "..."}` string form instead. Handle both.

## Failure handling

| Status | Code | What to do |
| --- | --- | --- |
| 400 | `BAD_REQUEST` / `VALIDATION_ERROR` | Fix the request. Do not retry unchanged. |
| 401 | `UNAUTHORIZED` | Token expired or wrong. Re-authenticate; do not retry with the same credential. |
| 403 | `FORBIDDEN` | The credential lacks the required scope. Escalate to a human. |
| 404 | `NOT_FOUND` | Confirm the slug **and** that you are on the right region host. Note: a cross-tenant access attempt also returns 404, not 403. |
| 413 | — | Body over 1 MB. Split the payload. |
| 429 | `RATE_LIMIT_EXCEEDED` | Back off. There is **no** `Retry-After` and **no** `X-RateLimit-*` header — you cannot see how close you are, so use exponential backoff. |
| 429 | `QUEUE_FULL` | Read `retryAfterMs` from the error payload and wait that long. |
| 500 | `INTERNAL_ERROR` | Retry once after a short delay, then escalate. |
| 503 | `SERVICE_UNAVAILABLE` | Retry later. |

## Retry safety

There is **no `Idempotency-Key` header** on this API. A retried `chat` or `complete` POST
whose outcome you do not know may produce a second agent turn. If a request times out with
an unknown outcome, read session state before retrying rather than firing again. See
`conventions/koreai-conventions.yml`.
