---
generated: '2026-07-27'
method: generated
name: Export a patient group with FHIR Bulk Data
description: Acquire a SMART Backend Services token, kick off a Group $export, poll to completion, and retrieve the exported FHIR entities.
api: openapi/advancedmd-fhir-bulk-api-openapi.json
operations:
  - 'POST /v1/oauth2/token'
  - 'GET /v1/r4/Group/{groupId}/$export'
  - 'GET /v1/fhir-bulk/status'
  - 'DELETE /v1/fhir-bulk/status'
  - 'GET /v1/fhir-bulk/fhir-resource/{batchId}/{fhirEntity}'
source: >-
  All five operations verified verbatim in openapi/advancedmd-fhir-bulk-api-openapi.json.
  Flow and required parameters follow https://fhir.advancedmd.com/fhir/bulk-api and
  https://fhir.advancedmd.com/fhir/launch-and-authorization.
---

# Export a patient group with FHIR Bulk Data

Population-scale retrieval for a whole patient group, using SMART Backend Services
authorization. This is the only AdvancedMD surface where `system/*.read` applies.

## Before you start
- Register an app requesting **only** the *FHIR Bulk API* product; one product per app.
  Email `InterOps@advancedmd.com` for approval and wait for the product to flip from
  *Pending Approval* to *Enabled*.
- Generate an RSA key pair and register the public key (or a `jku` JWK Set URL) with
  AdvancedMD. Production apps mint their own JWTs — the portal's
  `POST /v1/fhir-jwks/token` helper is explicitly test-only.

## Auth
1. **Build a one-time client assertion JWT**, signed **RS384**.
   Header: `alg=RS384`, `kid`, `typ=JWT`, optional `jku`.
   Claims: `iss` = `sub` = your `client_id`, `aud` = the token URL, `exp`, `jti` (nonce).
2. **Get a token** — `POST /v1/oauth2/token`,
   `Content-Type: application/x-www-form-urlencoded`, body:
   `grant_type=client_credentials`, `scope=system/*.read`,
   `client_assertion_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer`,
   `client_assertion=<jwt>`, plus AdvancedMD's additional `username`, `password` and
   `officekey` parameters for the provider account. The token is valid one hour.
   A malformed request returns `400` with `{error, error_description}`.

## Steps
1. **Kick off the export** — `GET /v1/r4/Group/{groupId}/$export` with required
   `OfficeKey`, `groupId` and `prefer=respond-async`; optional `_type` and `_since`.
   Expect `202 Accepted`; capture the job/batch identifier from the response.
   Test groups: `991900` and `991901`.
2. **Poll for completion** — `GET /v1/fhir-bulk/status`. `202` means still running;
   `200` returns the completion manifest listing the exported entities. Back off between
   polls; do not re-kick while a job is in flight.
3. **Retrieve each entity** — `GET /v1/fhir-bulk/fhir-resource/{batchId}/{fhirEntity}`
   once per entity named in the manifest.
4. **Cancel if needed** — `DELETE /v1/fhir-bulk/status` aborts a running job (`202`).

## Errors
- `400` — bad export parameters (unknown group, malformed `_type`/`_since`, missing `Prefer`)
  or a bad token request.
- `401` / `403` — token invalid, expired, or the scope/office key does not cover the group.
- `404` — unknown `batchId` or an entity not present in the manifest; re-read the manifest.
- `500` on status — the job failed server-side; re-kick and escalate if it recurs.
- `503` on kickoff — service busy; retry after a delay.
- Bodies are FHIR `OperationOutcome` (the Bulk API also publishes `OperationOutcomeWithID`,
  which carries the `jobId`). See `errors/advancedmd-problem-types.yml`.

## Retries and idempotency
The status, cancel and retrieval calls are safe to retry. **The kickoff is not** — each
`$export` call starts a *new* job and there is no idempotency key to deduplicate on. Always
poll `/v1/fhir-bulk/status` before re-kicking. The `client_assertion` JWT is one-time-use:
mint a fresh one per token request.

## Gotchas
- `system/*.read` is the only allowed system scope; there is no system write scope because
  the certified API is read-only.
- The Bulk token request is non-standard: `username`, `password` and `officekey` are
  required alongside the normal client-credentials parameters.
