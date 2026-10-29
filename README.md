# Appsmith

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

Appsmith is an open source (Apache-2.0) low-code platform for building internal tools, admin panels and workflow applications on top of 25+ databases and any REST or GraphQL API. It runs self-hosted via Docker, Kubernetes or Helm, or as Appsmith Cloud. Its agent surface is a first-party Model Context Protocol server bundled into the Appsmith image and fronted at /mcp, exposing 61 tools that build and edit applications under the calling user's own permissions; it ships disabled by default and requires a per-user mcp_ token. Appsmith publishes no public REST API reference: the platform API at /api/v1 is undocumented editor traffic and its springdoc OpenAPI surface is disabled by default and authenticated when enabled.

**Areas:** Low-Code · Open Source · Internal Tools · Workflow Automation · Developer Tools

## Appsmith on APIs.io

Everything profiled for Appsmith is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/appsmith/](https://apis.io/providers/appsmith/)** — or go straight to one of the APIs or properties below.

### APIs (3)

- [Appsmith Applications API](https://apis.io/apis/appsmith/appsmith-applications-api/) — Low-code application management
- [Appsmith Workspaces API](https://apis.io/apis/appsmith/appsmith-workspaces-api/) — Workspace organization and management
- [Appsmith Data Sources API](https://apis.io/apis/appsmith/appsmith-data-sources-api/) — Connected datasource management

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Appsmith MCP server](https://apis.io/servers/appsmith/appsmith-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Appsmith Agentic Access](https://apis.io/agentic-access/appsmith/appsmith-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [Application](https://apis.io/schemas/appsmith/application/)

#### JSON Structure (1)

Data models expressed in JSON Structure.

- [Application Structure](https://apis.io/json-structure/appsmith/application-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Appsmith Context](https://apis.io/jsonld/appsmith/appsmith-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Appsmith Vocabulary](https://apis.io/vocabularies/appsmith/appsmith-vocabulary/)

#### Examples (1)

Example requests and responses.

- [Application Example](https://apis.io/examples/appsmith/application-example/)

#### Collections (3)

Postman and Open Collection request collections.

- [Appsmith Applications API](https://apis.io/collections/appsmith/open-appsmith-applications-api/)
- [Appsmith Applications Datasources API](https://apis.io/collections/appsmith/open-appsmith-datasources-api/)
- [Appsmith Applications Workspaces API](https://apis.io/collections/appsmith/open-appsmith-workspaces-api/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Appsmith Applications Api Phrasing Overlay](https://apis.io/overlays/appsmith/appsmith-applications-api-phrasing-overlay/)
- [Appsmith Data Sources Api Phrasing Overlay](https://apis.io/overlays/appsmith/appsmith-data-sources-api-phrasing-overlay/)
- [Appsmith Workspaces Api Phrasing Overlay](https://apis.io/overlays/appsmith/appsmith-workspaces-api-phrasing-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Appsmith — jsonschema rules](https://apis.io/rules/appsmith/appsmith-jsonschema-spectral-rules/)
- [Appsmith API Rules](https://apis.io/rules/appsmith/appsmith-spectral-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Appsmith Authentication](https://apis.io/security/appsmith/appsmith-authentication/)
- [Appsmith Domain Security](https://apis.io/security/appsmith/appsmith-domain-security/)
- [Appsmith Trust Center](https://apis.io/security/appsmith/appsmith-trust-center/)
- [Appsmith Vulnerability Disclosure](https://apis.io/security/appsmith/appsmith-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Appsmith Plans Pricing](https://apis.io/plans/appsmith/appsmith-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Appsmith Rate Limits](https://apis.io/rate-limits/appsmith/appsmith-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Appsmith Finops](https://apis.io/finops/appsmith/appsmith-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.appsmith.com)
- [Documentation](https://docs.appsmith.com)
- [Getting started](https://docs.appsmith.com/getting-started)
- [Pricing](https://www.appsmith.com/pricing)
- [Sign up](https://app.appsmith.com/user/signup)
- [Support](https://community.appsmith.com)
- [Blog](https://www.appsmith.com/blog)
- [Compliance](https://security.appsmith.com/)
- [Terms of service](https://www.appsmith.com/terms-and-conditions)
- [Privacy policy](https://www.appsmith.com/privacy-policy)
- [GitHub](https://github.com/appsmithorg)
- [Status](https://status.appsmith.com)

## API Evangelist rating

**Kin Score 65.6** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 61.7 |
| Contract quality | 64.5 |
| Contract governance | 27.3 |
| Operational transparency | 68.4 |
| Developer ergonomics | 44.6 |
| Access clarity | 78.9 |

**Agent readiness 34.0** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | templated |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 35.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/appsmith/](https://apis.io/providers/appsmith/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Appsmith: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/appsmith/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
