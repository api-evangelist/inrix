# INRIX

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
