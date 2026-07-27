---
generated: '2026-07-27'
method: generated
name: Launch a SMART app and read a patient's record
description: Complete the SMART-on-FHIR authorization_code + PKCE flow against AdvancedMD, then read the US Core resources for the patient in context.
api: openapi/advancedmd-fhir-single-api-openapi.json
operations:
  - 'GET /Patient/{id}'
  - 'Patients Search using POST'
  - 'GET /Condition'
  - 'GET /AllergyIntolerance'
  - 'GET /MedicationRequest'
  - 'Observations Search using POST'
  - 'DocumentReferenceFetchDocref'
source: >-
  Operations verified verbatim in openapi/advancedmd-fhir-single-api-openapi.json.
  Authorization steps follow https://fhir.advancedmd.com/fhir/launch-and-authorization;
  scopes come from fhir/advancedmd-smart-configuration.json.
---

# Launch a SMART app and read a patient's record

AdvancedMD's certified FHIR API is **read-only** (ONC 170.315(g)(10)). There is no
create/update/delete — plan for retrieval only.

## Before you start
- Register an app at https://fhir.advancedmd.com, request **only** the *FHIR Single Patient API*
  product, then email `InterOps@advancedmd.com` with subject
  `FHIR App Approval Request for Appname: [Your Appname]` and your redirect URL. Approval takes days.
- The app's **Key** is the `client_id`; the **Secret** is the `client_secret`.
- Test credentials and the two test organizations live in `sandbox/advancedmd-sandbox.yml`.

## Resolve the base URL first
Every path is organization-scoped: `https://providerapi.advancedmd.com/v1/r4/{orgId}/…`.
Find `{orgId}` in the public endpoint directory —
`GET https://providerapi.advancedmd.com/v1/r4/endpoints` (a FHIR Bundle of Endpoint +
Organization) — or the CSV at https://fhir.advancedmd.com/files/baseurl_organizations.csv.
Test orgs are `174` and `175`.

## Auth
1. **Discover.** `GET {base}/.well-known/smart-configuration` — confirms the endpoints below.
2. **Authorize.** Redirect the browser to
   `https://providerapi.advancedmd.com/v1/oauth2/authorize` with `response_type=code`,
   `client_id`, `redirect_uri` (pre-registered), `state`, `aud=https://providerapi.advancedmd.com/v1/r4`,
   `scope`, and — for public clients — `code_challenge` + `code_challenge_method=S256`.
   The default working scope set is `openid fhirUser offline_access online_access patient/*.read`.
3. **Exchange.** `POST https://providerapi.advancedmd.com/v1/oauth2/token`,
   `Content-Type: application/x-www-form-urlencoded`, `Authorization: Basic base64(client_id:client_secret)`,
   body `grant_type=authorization_code&code=…&redirect_uri=…` (plus `code_verifier` when using PKCE).
   The authorization code expires in about a minute. The response carries `access_token`
   (`expires_in` ≈ 3599), `refresh_token`, `patient`, `fhirUser` and the granted `scope`.
4. Send `Authorization: Bearer <access_token>` on every call. See `scopes/advancedmd-scopes.yml`.

## Steps
1. **Read the patient in context** — `GET /Patient/{id}` where `{id}` is the `patient` value
   returned with the token. Confirms the context before anything else.
2. **Search patients (when a provider app must pick one)** — `Patients Search using POST`
   (`POST /Patient/_search`, `application/x-www-form-urlencoded`). Use the POST form so
   identifiers never land in a URL or a log.
3. **Pull the problem list** — `GET /Condition` with `patient={id}`.
4. **Pull allergies** — `GET /AllergyIntolerance` with `patient={id}`.
5. **Pull medications** — `GET /MedicationRequest`, and `GET /MedicationDispense` for fills.
6. **Pull vitals and labs** — `Observations Search using POST` (`POST /Observation/_search`)
   with `patient` and `category`; `GET /DiagnosticReport` for grouped results.
7. **Fetch clinical documents** — `DocumentReferenceFetchDocref` (`GET /DocumentReference/$docref`)
   with `patient={id}`; follow `content[].attachment.url` to retrieve each document.

Every resource type also offers `GET /{Resource}` (search), `GET /{Resource}/{id}` (read)
and, for 17 of them, `POST /{Resource}/_search`. Read `fhir/advancedmd-fhir-r4-capabilitystatement.json`
for the supported search parameters per resource.

## Paging
Responses are FHIR Bundles. Follow `Bundle.link[relation="next"]` verbatim until it is
absent. Do not construct page URLs yourself.

## Errors
- `401` — token missing/expired. Refresh with the `refresh_token`; re-authorize if that fails.
- `403` — the granted scope or patient context does not cover the resource. Request the
  granular `patient/<Resource>.read` (or `.rs`) scope.
- Bodies are FHIR `OperationOutcome`, not `problem+json`. See `errors/advancedmd-problem-types.yml`.

## Retries and idempotency
Every operation in this skill is a read (`POST /{Resource}/_search` is the FHIR-standard safe
search transport, not a write), so all of them are safe to retry. There is no
`Idempotency-Key` header anywhere in the estate — see `conventions/advancedmd-conventions.yml`.

## Gotchas
- A `user/*.read` token still carries a fixed patient context: a request with no explicit
  `patient` parameter is answered for the launch patient only.
- AdvancedMD documents user-level scopes as advertised but "not yet supported" in practice.
- Two-legged OAuth for general system-to-system access is not supported; `system/*.read`
  exists only for the Bulk Data flow.
