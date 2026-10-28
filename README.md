# AdvancedMD

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

AdvancedMD is a cloud practice-management, medical-billing and electronic health record (EHR) software company founded in 1999 and headquartered in South Jordan, Utah, serving independent ambulatory practices, mental-health and physical-medicine clinics, med spas and medical-billing services across the United States. A standalone company again since Francisco Partners acquired it from Global Payments in December 2024, AdvancedMD operates two clearly separated developer surfaces. The first is a public, no-cost HL7 FHIR R4 (4.0.1) read-only API estate published for ONC (g)(10) Cures Act certification at fhir.advancedmd.com, aligned to the US Core 6.1.0 Implementation Guide, authorized with SMART-on-FHIR OAuth 2.0 and covering both single-patient access and FHIR Bulk Data Access group export. The second is a gated proprietary Connect API estate (REST and XML-RPC) plus an ODBC data-access driver, which require a signed Certified API Developer Agreement with licensing and support fees before sandbox or production credentials are issued.

**Areas:** Healthcare · United States · Electronic Health Records · Practice Management · Medical Billing · FHIR · HL7 · SMART on FHIR · US Core · Interoperability · Revenue Cycle Management · Scheduling

## AdvancedMD on APIs.io

Everything profiled for AdvancedMD is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/advancedmd/](https://apis.io/providers/advancedmd/)** — or go straight to one of the APIs or properties below.

### APIs (33)

- [AdvancedMD FHIR Bulk JWKS API](https://apis.io/apis/advancedmd/advancedmd-fhir-bulk-jwks-api/) — Developer-portal helper API that mints JWT client assertions for testing the FHIR Bulk Data workflow. Documented as POST /v1/fhir-jwks/token with a…
- [AdvancedMD FHIR Endpoint Directory](https://apis.io/apis/advancedmd/advancedmd-fhir-endpoint-directory/) — Public, unauthenticated service base URL publication required of ONC-certified API suppliers. GET https://providerapi.advancedmd.com/v1/r4/endpoints returns…
- [AdvancedMD Connect APIs](https://apis.io/apis/advancedmd/advancedmd-connect-apis/) — AdvancedMD's proprietary partner API family, published in both XML-RPC and REST formats, which lets developers build companion applications that replicate…
- [AdvancedMD Authentication API](https://apis.io/apis/advancedmd/advancedmd-authentication-api/) — The Authentication API from AdvancedMD — 1 operation(s) for authentication.
- [AdvancedMD Cancel Bulk Data Export API](https://apis.io/apis/advancedmd/advancedmd-cancel-bulk-data-export-api/) — The Cancel Bulk Data Export API from AdvancedMD — 1 operation(s) for cancel bulk data export.
- [AdvancedMD Care Team API](https://apis.io/apis/advancedmd/advancedmd-careteam-api/) — The CareTeam API from AdvancedMD — 3 operation(s) for careteam.
- [AdvancedMD Check Data Export Status API](https://apis.io/apis/advancedmd/advancedmd-check-data-export-status-api/) — The Check Data Export Status API from AdvancedMD — 1 operation(s) for check data export status.
- [AdvancedMD Clinical API](https://apis.io/apis/advancedmd/advancedmd-clinical-api/) — The Clinical API from AdvancedMD — 15 operation(s) for clinical.
- [AdvancedMD Condition API](https://apis.io/apis/advancedmd/advancedmd-condition-api/) — The Condition API from AdvancedMD — 3 operation(s) for condition.
- [AdvancedMD Coverage API](https://apis.io/apis/advancedmd/advancedmd-coverage-api/) — The Coverage API from AdvancedMD — 3 operation(s) for coverage.
- [AdvancedMD Device API](https://apis.io/apis/advancedmd/advancedmd-device-api/) — The Device API from AdvancedMD — 3 operation(s) for device.
- [AdvancedMD Diagnostic Report API](https://apis.io/apis/advancedmd/advancedmd-diagnosticreport-api/) — The DiagnosticReport API from AdvancedMD — 3 operation(s) for diagnosticreport.
- [AdvancedMD Encounter API](https://apis.io/apis/advancedmd/advancedmd-encounter-api/) — The Encounter API from AdvancedMD — 2 operation(s) for encounter.
- [AdvancedMD Get FHIR Entity API](https://apis.io/apis/advancedmd/advancedmd-get-fhir-entity-api/) — The Get FHIR Entity API from AdvancedMD — 1 operation(s) for get fhir entity.
- [AdvancedMD Goal API](https://apis.io/apis/advancedmd/advancedmd-goal-api/) — The Goal API from AdvancedMD — 3 operation(s) for goal.
- [AdvancedMD Immunization API](https://apis.io/apis/advancedmd/advancedmd-immunization-api/) — The Immunization API from AdvancedMD — 3 operation(s) for immunization.
- [AdvancedMD Location API](https://apis.io/apis/advancedmd/advancedmd-location-api/) — The Location API from AdvancedMD — 2 operation(s) for location.
- [AdvancedMD Medication Dispense API](https://apis.io/apis/advancedmd/advancedmd-medicationdispense-api/) — The MedicationDispense API from AdvancedMD — 3 operation(s) for medicationdispense.
- [AdvancedMD Observation API](https://apis.io/apis/advancedmd/advancedmd-observation-api/) — The Observation API from AdvancedMD — 3 operation(s) for observation.
- [AdvancedMD Obtain Access Token API](https://apis.io/apis/advancedmd/advancedmd-obtain-access-token-api/) — The Obtain Access Token API from AdvancedMD — 1 operation(s) for obtain access token.
- [AdvancedMD Organization API](https://apis.io/apis/advancedmd/advancedmd-organization-api/) — The Organization API from AdvancedMD — 2 operation(s) for organization.
- [AdvancedMD Patient API](https://apis.io/apis/advancedmd/advancedmd-patient-api/) — The Patient API from AdvancedMD — 3 operation(s) for patient.
- [AdvancedMD Patient Demographics API](https://apis.io/apis/advancedmd/advancedmd-patient-demographics-api/) — The Patient Demographics API from AdvancedMD — 1 operation(s) for patient demographics.
- [AdvancedMD Practitioner API](https://apis.io/apis/advancedmd/advancedmd-practitioner-api/) — The Practitioner API from AdvancedMD — 2 operation(s) for practitioner.
- [AdvancedMD Procedure API](https://apis.io/apis/advancedmd/advancedmd-procedure-api/) — The Procedure API from AdvancedMD — 3 operation(s) for procedure.
- [AdvancedMD Provenance API](https://apis.io/apis/advancedmd/advancedmd-provenance-api/) — The Provenance API from AdvancedMD — 1 operation(s) for provenance.
- [AdvancedMD Related Person API](https://apis.io/apis/advancedmd/advancedmd-relatedperson-api/) — The RelatedPerson API from AdvancedMD — 3 operation(s) for relatedperson.
- [AdvancedMD Start Bulk Data Export API](https://apis.io/apis/advancedmd/advancedmd-start-bulk-data-export-api/) — The Start Bulk Data Export API from AdvancedMD — 1 operation(s) for start bulk data export.
- [AdvancedMD Allergy Intolerance API](https://apis.io/apis/advancedmd/advancedmd-allergy-intolerance-api/) — The Allergy Intolerance API from AdvancedMD — 3 operation(s) for allergy intolerance.
- [AdvancedMD Care plan API](https://apis.io/apis/advancedmd/advancedmd-care-plan-api/) — The Care plan API from AdvancedMD — 3 operation(s) for care plan.
- [AdvancedMD CCDA API](https://apis.io/apis/advancedmd/advancedmd-ccda-api/) — The CCDA API from AdvancedMD — 1 operation(s) for ccda.
- [AdvancedMD Document Reference API](https://apis.io/apis/advancedmd/advancedmd-document-reference-api/) — The Document Reference API from AdvancedMD — 4 operation(s) for document reference.
- [AdvancedMD Medication Request API](https://apis.io/apis/advancedmd/advancedmd-medication-request-api/) — The Medication Request API from AdvancedMD — 3 operation(s) for medication request.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [advancedmd](https://apis.io/servers/advancedmd/advancedmd/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Advancedmd Agentic Access](https://apis.io/agentic-access/advancedmd/advancedmd-agentic-access/)

#### Collections (3)

Postman and Open Collection request collections.

- [AdvancedMD Application Access APIs](https://apis.io/collections/advancedmd/open-advancedmd-application-access-apis-swagger/)
- [FHIR Bulk API](https://apis.io/collections/advancedmd/open-advancedmd-fhir-bulk-api/)
- [FHIR Single API - US Core 6.1.0](https://apis.io/collections/advancedmd/open-advancedmd-fhir-single-api/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Advancedmd Application Access Apis Overlay](https://apis.io/overlays/advancedmd/advancedmd-application-access-apis-overlay/)
- [Advancedmd Fhir Bulk Api Overlay](https://apis.io/overlays/advancedmd/advancedmd-fhir-bulk-api-overlay/)
- [Advancedmd Fhir Single Api Overlay](https://apis.io/overlays/advancedmd/advancedmd-fhir-single-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Advancedmd Authentication](https://apis.io/security/advancedmd/advancedmd-authentication/)
- [Advancedmd Domain Security](https://apis.io/security/advancedmd/advancedmd-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Advancedmd Scopes](https://apis.io/scopes/advancedmd/advancedmd-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Advancedmd Plans Pricing](https://apis.io/plans/advancedmd/advancedmd-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Advancedmd Rate Limits](https://apis.io/rate-limits/advancedmd/advancedmd-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.advancedmd.com/)
- [Documentation](https://www.advancedmd.com/group-practice/developer-solutions/)
- [Getting started](https://fhir.advancedmd.com/getting-started)
- [API reference](https://fhir.advancedmd.com/fhir/apis)
- [Pricing](https://www.advancedmd.com/software-pricing/)
- [Sign up](https://www.advancedmd.com/api-connection-request/)
- [Support](https://www.advancedmd.com/support/interoperability/)
- [Blog](https://www.advancedmd.com/blog/)
- [Security](https://www.advancedmd.com/medical-office-software/security/)
- [Compliance](https://www.advancedmd.com/ai-information)
- [Terms of service](https://fhir.advancedmd.com/terms-of-service)
- [Privacy policy](https://www.advancedmd.com/privacy-notice/)
- [GitHub](https://github.com/AdvancedMD)
- [Status](https://status.advancedmd.com/)

## API Evangelist rating

**Kin Score 51.6** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 69.6 |
| Contract quality | 50.8 |
| Contract governance | 18.2 |
| Operational transparency | 28.9 |
| Developer ergonomics | 32.7 |
| Access clarity | 73.7 |

**Agent readiness 38.2** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
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
| Operation Distinctiveness | — |

**Regulatory alignment 48.4** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/advancedmd/](https://apis.io/providers/advancedmd/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for AdvancedMD: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/advancedmd/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
