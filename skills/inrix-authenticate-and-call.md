---
name: Authenticate against INRIX and call a product API
description: Mint an INRIX UAS access token from an appId and hashToken, present it correctly, keep it fresh, and read the INRIX statusId envelope on every product API call.
api: openapi/inrix-user-accounts-openapi-original.json
operations:
  - Application_GetAppToken
  - Auth_CheckToken
  - Auth_RenewToken
---

# Authenticate against INRIX and call a product API

Every INRIX product API — Traffic, Parking, Analytics, Signals, Data Download, the data-upload
streams — is gated by one bearer access token minted by the INRIX User Accounts System (UAS) at
`https://uas-api.inrix.com`. There is no per-product credential.

## 1. Build the hashToken

INRIX issues you an `appId` (a GUID) and an `appKey`. The token request does **not** take the raw key.
Compute `hashToken` as the SHA-1 hash of the **lowercase**, UTF-8 encoded string `"AppId|AppKey"` —
the two values joined by a single pipe character.

## 2. Mint the access token — `Application_GetAppToken`

`GET https://uas-api.inrix.com/v1/appToken?appId={appId}&hashToken={hashToken}`

Send `Accept: application/json` (the service also speaks `application/xml`). The response carries the
token and its validity period.

## 3. Present the token

Two equivalent forms are documented; pick one and use it consistently:

- Header — `Authorization: Bearer {UAS-TOKEN}`
- Query string — `?accessToken={UAS-TOKEN}`

## 4. Cache it, then renew it

Cache the token and reuse it for subsequent requests until it is close to expiring. Do **not** mint a
token per request. Tokens are **not interchangeable between environments** — a production token will
not work against `*.beta.inrix.com` / `*.sandbox.inrix.com` / `*.qa.inrix.io` and vice versa.

- Check a token before relying on it — `Auth_CheckToken` (`POST /v1/validatetoken`).
- Refresh rather than re-mint — `Auth_RenewToken` (`GET /v1/renewtoken?refreshToken=…`).

## 5. Call the product API

Point at the product host, not the UAS host. For example:

- `https://segment-api.inrix.com/v1/segments/speed?box={lat1|lon1,lat2|lon2}&accesstoken={token}`
- `https://incident-api.inrix.com/v1/incidents?box={…}&incidentType=Incidents,Flow,Construction`

Bound every geospatial query with `box`, or `point` + `radius`, or a `segmentSet`. INRIX enforces
limits and rejects oversized queries.

## 6. Read the response envelope — not just the HTTP status

INRIX returns a numeric `statusId` and a `statusText` **alongside** the HTTP status code.
`statusId: 0` / `OK` means normal processing. Anything else is an error even when the transport looks
healthy. The full 360-entry registry is in `errors/inrix-error-codes.yml`. The ones you will hit most:

| statusId | statusText | HTTP | What to do |
|---|---|---|---|
| 41 / 42 | NoToken / BadToken | 400 | The token was missing or malformed — check how you attached it |
| 43 | TokenExpired | 401 | Renew via `Auth_RenewToken`, then retry once |
| 56 | Missing required parameter | 400 | Fix the request; do not retry as-is |
| 153 | Radius Exceed Limit | 400 | Shrink the radius |
| 154 | BoundingBox Exceed Limit | 400 | Shrink the bounding box |
| 13 | subscription expired | 400 | Account-level — contact support@inrix.com, do not retry |
| 90 | Service Call Timed Out | 500 | Safe to retry with backoff |

## Rules

- **Retry only on 5xx and on statusId 43 (after renewing).** 4xx with a statusId is a request defect.
- **There is no idempotency key.** INRIX documents no idempotency contract, so never blind-retry a
  write (a reservation, a data-stream upload) — reconcile first.
- **There are no rate-limit headers.** Quotas are contractual. Back off on 5xx rather than probing.
- Timestamps are ISO 8601 with either a `Z` designator or a `+hh:mm` / `-hh:mm` offset. The
  data-upload streams are the exception and take a UNIX timestamp in `ts`.
