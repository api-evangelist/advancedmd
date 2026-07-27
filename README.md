# AdvancedMD

AdvancedMD is a cloud practice-management, medical-billing and electronic health record (EHR) software company founded in 1999 and headquartered in South Jordan, Utah. It serves independent ambulatory practices, mental-health and physical-medicine clinics, med spas and medical-billing services across the United States, and has operated as a standalone company again since Francisco Partners acquired it from Global Payments in December 2024.

AdvancedMD runs two clearly separated developer surfaces.

**Public regulatory FHIR estate.** The [AdvancedMD FHIR Portal](https://fhir.advancedmd.com/) publishes the ONC (g)(10) Cures Act APIs at no cost: a read-only HL7 FHIR R4 (4.0.1) API aligned to the US Core Implementation Guide STU 6.1.0, a FHIR Bulk Data Access group-export API, and a test-only JWKS helper. Authorization is SMART-on-FHIR OAuth 2.0 — authorization-code with PKCE for single-patient apps, client-credentials with a `private_key_jwt` assertion and `system/*.read` for Bulk. Base URLs are organization-specific under `https://providerapi.advancedmd.com/v1/r4/{orgId}`, and the full customer endpoint directory is published as a FHIR Bundle and a CSV.

**Gated Connect API estate.** The proprietary Connect APIs (REST and XML-RPC) and a read-only ODBC driver cover patient engagement, scheduling, clinical forms, payments and revenue-cycle management. They require a signed Certified API Developer Agreement, with licensing and support fees, before sandbox or production credentials are issued. No endpoints or specifications are published outside that agreement, so none are catalogued here.

## APIs

| API | Base URL | Contract |
| --- | --- | --- |
| [FHIR Single API (US Core 6.1.0)](https://fhir.advancedmd.com/fhir/single-api) | `https://providerapi.advancedmd.com/v1/r4` | [OpenAPI 3.0.1](openapi/advancedmd-fhir-single-api-openapi.json) · [CapabilityStatement](fhir/advancedmd-fhir-r4-capabilitystatement.json) |
| [FHIR Bulk API](https://fhir.advancedmd.com/fhir/bulk-api) | `https://providerapi.advancedmd.com` | [OpenAPI 3.0.1](openapi/advancedmd-fhir-bulk-api-openapi.json) |
| [FHIR Bulk JWKS API](https://fhir.advancedmd.com/fhir/bulk-api) | `https://providerapi.advancedmd.com` | Prose documentation only |
| [FHIR Endpoint Directory](https://fhir.advancedmd.com/fhir/base-urls) | `https://providerapi.advancedmd.com/v1/r4` | FHIR Bundle at `/endpoints` |
| [Connect APIs](https://www.advancedmd.com/group-practice/developer-solutions/) | Not published | Gated behind a developer agreement |

## Harvested artifacts

- `openapi/advancedmd-fhir-single-api-openapi.json` — OpenAPI 3.0.1, 58 paths, 21 FHIR resource tags
- `openapi/advancedmd-fhir-bulk-api-openapi.json` — OpenAPI 3.0.1, 4 paths
- `fhir/advancedmd-fhir-r4-capabilitystatement.json` — FHIR R4 CapabilityStatement, 25 resources, instantiates US Core and Bulk Data
- `fhir/advancedmd-smart-configuration.json` — SMART-on-FHIR discovery document
- `fhir/advancedmd-openid-configuration.json` — OpenID Connect discovery document

Provenance and HTTP statuses for every probe are recorded in [`review.yml`](review.yml).

## Links

- Website — https://www.advancedmd.com/
- FHIR developer portal — https://fhir.advancedmd.com/
- Developer portal (Connect APIs) — https://developer.advancedmd.com/
- Developer solutions — https://www.advancedmd.com/group-practice/developer-solutions/
- Getting started — https://fhir.advancedmd.com/getting-started
- Interoperability support — https://www.advancedmd.com/support/interoperability/
- API connection request — https://www.advancedmd.com/api-connection-request/
- Status — https://status.advancedmd.com/
- Pricing — https://www.advancedmd.com/software-pricing/
- Blog — https://www.advancedmd.com/blog/
