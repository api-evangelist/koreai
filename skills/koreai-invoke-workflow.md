---
name: koreai-invoke-workflow
description: Execute a Kore.ai Agent Platform workflow — deployment-scoped, by id, or pinned to a version — and poll an asynchronous execution to completion.
api: Kore.ai Agent Platform ABL Runtime API — Workflows
operations:
  - runtime.workflow.invoke
  - runtime.workflow.execute
  - runtime.workflow.executeVersion
  - runtime.workflow.getExecution
---

# Execute a Kore.ai workflow

Every operation named here is verified against
`openapi/koreai-abl-runtime-workflows-openapi.json`.

## Pick the right entry point

| Situation | Operation | Path |
| --- | --- | --- |
| You have project + environment + workflow slugs (the normal deployed path) | `runtime.workflow.invoke` | `POST /api/v1/project/{projectSlug}/{env}/workflow/{workflowSlug}/invoke` |
| You have a bare `workflowId` | `runtime.workflow.execute` | `POST /api/v1/workflows/{workflowId}/execute` |
| You must pin behaviour to a specific published version | `runtime.workflow.executeVersion` | `POST /api/v1/workflows/{workflowId}/versions/{version}/execute` |
| You need the outcome of an async run | `runtime.workflow.getExecution` | `GET /api/v1/workflows/{workflowId}/executions/{executionId}` |

`runtime.workflow.invoke` supports a `?mode=` query parameter for synchronous versus
asynchronous invocation — read the spec's parameter description rather than assuming a
default.

**Prefer `executeVersion` for anything repeatable.** Versions are immutable on this
platform; executing by workflow id alone follows whatever is currently deployed, so the same
call can change behaviour underneath you after a promotion.

## Asynchronous runs

When a run is asynchronous you get an `executionId`. Poll
`runtime.workflow.getExecution` for status. Do not re-`execute` because a poll has not
returned yet — there is no idempotency key on this API, so a second execute is a second run.

## Input validation

Since release v1.4.0 (2026-07-30) start-input defaults and required-input validation are
applied **server-side on every trigger path** — cron, webhook, connector-polling and
agent-triggered, not just Studio's Run dialog. A workflow that ran from the UI can still
reject your inputs; validate against the spec's request body, and treat a 400
`VALIDATION_ERROR` as a contract problem, not a transient one.

## Errors and limits

Same envelope and codes as the conversation surface — see
`errors/koreai-problem-types.yml`. Watch specifically for `429 QUEUE_FULL`, which is a
concurrency signal rather than a rate limit: reduce parallelism and wait `retryAfterMs`
from the error payload. There is no `Retry-After` header.

## Reversibility

Executing a workflow is not reversible. Deployment state is: a retired deployment can be
returned to its previous active state with
`POST /api/projects/{projectId}/deployments/{deploymentId}/rollback`, but the provider does
not state a window for that, and there is no undelete for projects, agents or tools. See
`conventions/koreai-conventions.yml`.
