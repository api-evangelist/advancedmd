---
generated: '2026-07-27'
method: generated
name: Pull a patient's clinical record with the Application Access APIs
description: Authenticate with patient-portal credentials against the legacy non-FHIR Application Access APIs, then read the clinical record and the C-CDA episode summary for a patient over a date range.
api: openapi/advancedmd-application-access-apis-swagger.json
operations:
  - 'POST /authenticate'
  - 'GET /demographics/patients/{patientid}'
  - 'GET /clinical/allergies'
  - 'GET /clinical/medications'
  - 'GET /clinical/problems'
  - 'GET /clinical/results'
  - 'GET /clinical/vitalsigns'
  - 'GET /clinical/episodesummaries'
source: >-
  All operations, parameters and response examples verified verbatim in
  openapi/advancedmd-application-access-apis-swagger.json (Swagger 2.0, version 1.0.1,
  host ptapi.advancedmd.com, basePath /pt-api), harvested from the AdvancedMD FHIR portal.
---

# Pull a patient's clinical record with the Application Access APIs

The legacy, non-FHIR patient API family. AdvancedMD lists it on the portal as **"Legacy
Patient APIs — do not select"** and steers new work to the FHIR Single API; use this only
for an existing integration or when you need the C-CDA episode summary. See
`lifecycle/advancedmd-lifecycle.yml`.

Base URL: `https://ptapi.advancedmd.com/pt-api`. All responses are JSON except the
episode summary, which is HL7 C-CDA v3 XML.

## Auth
Two credentials travel together on every call:
- `apikey: <your API key>` — issued when your app is approved.
- `Authorization: <bearer token>` — minted by `POST /authenticate`.

**Step 0** — `POST /authenticate` with `application/json` body
`{"username", "password", "officekey"}`. These are the patient's *Patient Portal*
credentials plus the practice's office key. The `200` response carries `token` and
`patientdata[]` — every patient the caller may read, each with `patientid`, `name`,
address fields and `dateofbirth`. `403` means the credentials or office key are wrong.

## Steps
1. **Authenticate** — `POST /authenticate`. Keep the `token` and pick a `patientid`.
2. **Read demographics** — `GET /demographics/patients/{patientid}`.
3. **Read the clinical record** — each of these takes required query parameters
   `patientid`, `startDate` and `endDate` (format `m/d/yyyy`, e.g. `1/1/2017`):
   - `GET /clinical/allergies`
   - `GET /clinical/problems`
   - `GET /clinical/medications`
   - `GET /clinical/orders`
   - `GET /clinical/procedures`
   - `GET /clinical/results`
   - `GET /clinical/vitalsigns`
   - `GET /clinical/immunizations`
   - `GET /clinical/implanteddevices`
   - `GET /clinical/smokingstatus`
   - `GET /clinical/goals`
   - `GET /clinical/plans`
   - `GET /clinical/assessments`
   - `GET /clinical/healthconcerns`
   - `GET /clinical/providers`
4. **Fetch the episode summary** — `GET /clinical/episodesummaries` returns a C-CDA v3
   `ClinicalDocument` (XML) for the date range. Parse it as CDA, not JSON.

## Paging
There is none. The `startDate`/`endDate` window is the only bound on response size —
walk long histories in chunks (e.g. one year at a time).

## Errors
- `401` — `{"title": "Unauthorized", "detail": "Invalid API key or bearer token."}`.
  Both the `apikey` header and the bearer token must be present.
- `403` — bad credentials on `POST /authenticate`.
- `429` — `{"title": "QuotaViolation", "detail": "Too many requests: Please wait and try
  your request again in about a minute."}`. Declared on **every** operation. There is no
  `Retry-After` header and no published quota — sleep ~60s and retry. See
  `rate-limits/advancedmd-rate-limits.yml`.

## Retries and idempotency
All `/clinical/*` and `/demographics/*` reads are safe to retry. `POST /authenticate`
mints a new session token each time — reuse the token you hold rather than re-authenticating
in a retry loop. No idempotency key exists; see `conventions/advancedmd-conventions.yml`.

## Gotchas
- Dates are US-format `m/d/yyyy`, not ISO 8601, and both bounds are **required**.
- The Swagger declares no `operationId` on any of the 18 operations — address them by
  method + path.
- The declared "Supported Version" is AdvancedMD v12.6, far behind the v25 the FHIR
  portal targets. Verify behaviour against your practice before relying on it.
