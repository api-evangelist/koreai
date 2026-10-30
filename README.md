# Kore.ai

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Kore.ai is an enterprise conversational and agentic AI platform used to build, deploy, govern and observe AI agents for customer experience and employee experience work — contact center automation, voice AI, IT and HR service desks, agent assist, quality assurance and no-code agent orchestration. The company ships two API estates. The newer Agent Platform ("Artemis") on agents.kore.ai exposes an ABL Runtime API for chat, streaming, workflow invocation and session usage, an Agent Blueprint Language (ABL) DSL, and a 45-tool stdio MCP server (@koreai/arch-mcp-tools) that turns the platform's own control plane into agent tooling. The longer-established AI for Service estate on platform.kore.ai exposes a large REST surface across Automation AI, Search AI, Contact Center AI, Agent AI, Quality AI and Case Management, authenticated with JWT apps and governed by an assigned API-scope model. Kore.ai is headquartered in Orlando, Florida and is recognized as a Leader in the Gartner Magic Quadrant for Conversational AI, the Forrester Wave for Conversational AI Platforms and the Everest Group PEAK Matrix for Agentic AI Products.

**Areas:** Company · Artificial Intelligence · Conversational AI · Agents · Agent Platform · Contact Center · Customer Experience · Employee Experience · Voice · Automation · MCP · Enterprise Software

## Kore.ai on APIs.io

Everything profiled for Kore.ai is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/koreai/](https://apis.io/providers/koreai/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [Kore.ai AI for Service Platform APIs](https://apis.io/apis/koreai/koreai-ai-for-service-platform-apis/) — The AI for Service REST estate — Automation AI (bot lifecycle, NLP training, analytics, admin, data tables), Search AI (answer generation, content and chunk…
- [Kore.ai Arch MCP Server](https://apis.io/apis/koreai/koreai-arch-mcp-server/) — A stdio Model Context Protocol server, @koreai/arch-mcp-tools, that exposes the Kore.ai Agent Platform control plane to an MCP client as 45 tools across…
- [Kore.ai Chat API](https://apis.io/apis/koreai/koreai-chat-api/) — The Chat API from Kore.ai — 5 operation(s) for chat.
- [Kore.ai Conversation API](https://apis.io/apis/koreai/koreai-conversation-api/) — The Conversation API from Kore.ai — 3 operation(s) for conversation.
- [Kore.ai Workflows API](https://apis.io/apis/koreai/koreai-workflows-api/) — The Workflows API from Kore.ai — 4 operation(s) for workflows.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Koreai Webhooks](https://apis.io/asyncapis/koreai/koreai-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [arch-agent-platform](https://apis.io/servers/koreai/arch-agent-platform/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Koreai Abl Runtime Conversation Overlay](https://apis.io/overlays/koreai/koreai-abl-runtime-conversation-overlay/)
- [Koreai Abl Runtime Sessions Overlay](https://apis.io/overlays/koreai/koreai-abl-runtime-sessions-overlay/)
- [Koreai Abl Runtime Workflows Overlay](https://apis.io/overlays/koreai/koreai-abl-runtime-workflows-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Koreai Authentication](https://apis.io/security/koreai/koreai-authentication/)
- [Koreai Domain Security](https://apis.io/security/koreai/koreai-domain-security/)
- [Koreai Trust Center](https://apis.io/security/koreai/koreai-trust-center/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Koreai Plans Pricing](https://apis.io/plans/koreai/koreai-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Koreai Rate Limits](https://apis.io/rate-limits/koreai/koreai-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.kore.ai/)
- [Documentation](https://docs.kore.ai/)
- [Getting started](https://docs.kore.ai/agent-platform/getting-started)
- [API reference](https://docs.kore.ai/ai-for-service/apis/api-list)
- [Sign up](https://agents.kore.ai/auth/login)
- [Support](https://www.kore.ai/support)
- [Blog](https://www.kore.ai/blog)
- [Compliance](https://trust.kore.ai/)
- [Terms of service](https://www.kore.ai/terms-of-service)
- [Privacy policy](https://www.kore.ai/privacy-policy)
- [GitHub](https://github.com/Koredotcom)
- [Status](https://status.kore.com/)

## API Evangelist rating

**Kin Score 54.4** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 76.7 |
| Contract quality | 53.4 |
| Contract governance | 18.2 |
| Operational transparency | 50.0 |
| Developer ergonomics | 83.3 |
| Access clarity | 36.8 |

**Agent readiness 39.6** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 27.3** — AI & Biometrics

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/koreai/](https://apis.io/providers/koreai/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Kore.ai: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/koreai/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
