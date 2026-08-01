---
name: Query INRIX Signals intersection metrics
description: Check availability, pull intersection metadata and metrics, and manage the customer namespace that scopes them, on the INRIX Signals Analytics API.
api: openapi/inrix-signals-analytics-openapi-original.json
operations:
  - intersectionAvailability
  - intersectionMetadata
  - intersectionMetrics
  - searchNamespaces
  - updateNamespace
  - deleteNamespace
---

# Query INRIX Signals intersection metrics

INRIX Signals delivers traffic-signal and intersection performance analytics from the INRIX IQ
backend. Base host: `https://signals-api.inrix.com`. This is the one INRIX surface that publishes a
real OpenAPI 3.0.1 document, live at `https://signals-api.inrix.com/openapi.json`.

## Authentication

The spec declares a single security scheme, `Bearer Token` (`http` / `bearer`, `bearerFormat: JWT`).
The token is the INRIX UAS access token — mint it as described in
`skills/inrix-authenticate-and-call.md` and send `Authorization: Bearer {token}`.

## 1. Check coverage before you query — `intersectionAvailability`

`GET /v1/metrics/intersections/availability`

Signals coverage is not universal. Ask what is available for your geography and time window before
requesting metrics, so you can distinguish "no coverage" from "no traffic".

## 2. Pull intersection metadata — `intersectionMetadata`

`POST /v1/metadata/intersections`

Returns the descriptive record for the intersections you are about to analyse — identity, geometry
and approach structure. Fetch this once and cache it; join it to the metrics in step 3 rather than
re-requesting it per metric pull.

## 3. Pull the metrics — `intersectionMetrics`

`POST /v1/metrics/intersections`

The analytical payload. Request bodies are JSON; responses are `application/json`.

> **Spec caveat, worth knowing before you write the client:** all three intersection operations
> declare **only a `201`** response in the published document, with no `4xx`/`5xx` responses modelled.
> Do not code against `200`, and do not assume the spec enumerates the error surface — fall back to
> the INRIX `statusId` registry in `errors/inrix-error-codes.yml`.

## 4. Manage the namespace that scopes your data

Signals data is partitioned by a customer namespace. Unlike the intersection operations, these three
*are* fully modelled (`200`, `400`, `401`, `404`, `500`):

- `searchNamespaces` — `POST /v1/namespace/search`, find your namespaces.
- `updateNamespace` — `PATCH /v1/namespace/{namespace}`, amend one.
- `deleteNamespace` — `DELETE /v1/namespace/{namespace}`.

## Rules

- **`deleteNamespace` is destructive and has no undo, no soft-delete and no idempotency key.**
  Call `searchNamespaces` and confirm the exact namespace string first. A `404` means it was already
  gone; a `400` means the namespace string itself was invalid.
- `401` on any namespace operation means the bearer token is missing, malformed or expired — renew
  via `Auth_RenewToken` and retry once, do not loop.
- Retry `500` with backoff. Never retry `400` unchanged.
- Timestamps follow ISO 8601 per `conventions/inrix-conventions.yml`.
