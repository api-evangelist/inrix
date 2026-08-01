# INRIX

INRIX is a Kirkland, Washington-based transportation analytics company that turns anonymized GPS probe
data from connected vehicles, mobile devices and fleets into real-time and historical road intelligence
for automakers, cities, departments of transportation, retailers and app developers.

- Website: https://inrix.com/
- Developers: https://inrix.com/developers/
- Documentation: https://docs.inrix.com/
- Console / sign up: https://iq.inrix.com/
- Status: https://status.inrix.com/
- Support: support@inrix.com

## Machine-readable contracts

INRIX publishes no spec index, but three real contracts are served from the API hosts and are captured
verbatim in `openapi/`:

| API | Spec | Operations | Source |
|---|---|---|---|
| INRIX User Accounts System (UAS) | Swagger 2.0 | 83 | https://uas-api.inrix.com/swagger/docs/v1 |
| INRIX Parkme | Swagger 2.0 | 4 | https://parking-api.inrix.com/api/swagger.json |
| INRIX Signals Analytics | OpenAPI 3.0.1 | 6 | https://signals-api.inrix.com/openapi.json |

The far larger Traffic, Parking v3, Analytics and data-stream surfaces are documented in HTML only.

## Artifacts

| Directory | What is in it |
|---|---|
| `openapi/` | The three harvested contracts, verbatim |
| `authentication/` | The UAS appToken flow, OAuth2-shaped endpoints and the legacy GetSecurityToken path |
| `errors/` | The 360-entry INRIX `statusId` registry, plus responses derived from the contracts |
| `conventions/` | Auth style, geospatial bounding, output fields, ISO 8601, error envelope, no idempotency |
| `lifecycle/` | Versioning, status page, environments, regions and observed deprecation notices |
| `changelog/` | Parking API change log and Mobile Client SDK release notes |
| `sandbox/` | The beta / sandbox / qa host map and the Stripe test-card note for parking reservations |
| `packages/` | The iOS CocoaPods library and the gated Android Artifactory SDK |
| `conformance/` | TPEG, OpenLR, TMC, ISO 8601, GeoJSON and the EU-U.S. Data Privacy Framework certification |
| `data-model/` | Entity graph derived from the contracts |
| `overlays/` | API Evangelist enhancements over each harvested spec |
| `skills/` | Three agent skills grounded in verified operationIds |
| `llms/` | Generated llms.txt |
| `mcp/` | A candidate tool surface — INRIX ships no MCP server |
| `well-known/` | Negative probe record: no `/.well-known/` documents on any host |
| `security/` | Probed TLS, HSTS, DNSSEC, CAA, SPF and DMARC posture |

## Honest gaps

INRIX publishes **no** security.txt, vulnerability-disclosure policy, bug bounty, trust center,
OpenID/OAuth discovery document, A2A agent card, MCP server, AsyncAPI, webhook or event-subscription
surface, idempotency contract, rate-limit headers, formal deprecation policy, public SLA, first-party
Postman workspace, or CLI. `inrix.com` returns HTTP 403 to non-browser clients.
