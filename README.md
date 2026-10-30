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

INRIX is a Kirkland, Washington-based transportation analytics company that turns anonymized GPS probe data from connected vehicles, mobile devices and fleets into real-time and historical road intelligence for automakers, cities, departments of transportation, retailers and app developers. Its developer surface is organized around the INRIX IQ platform and documented at docs.inrix.com, spanning Traffic APIs (segment speed, safety alerts/incidents, traffic tiles, routing, drive time polygons, traffic cameras, dangerous slowdowns, fuel stations and TPEG Connect), Parking APIs (INRIX Parking Services 3.0, formerly ParkMe: lots, blocks, occupancy and probability, destinations and reservations), Analytics APIs (trade area trips, trip trends, visits, dangerous roads and Roadway Analytics), Signals intersection analytics, a Data Download Service for map and XD network releases, and data-upload streams for GPS, XFCD and parking events. All access is brokered through the INRIX User Accounts System (UAS), which exchanges an appId and a SHA-1 hashToken for a bearer access token used across every product API.

**Areas:** Transportation · Traffic · Mobility · Parking · Geospatial · Location Data · Analytics · Automotive · Smart Cities · Routing · Connected Vehicles · Road Network

## INRIX on APIs.io

Everything profiled for INRIX is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/inrix/](https://apis.io/providers/inrix/)** — or go straight to one of the APIs or properties below.

### APIs (29)

- [INRIX Segment Speed API](https://apis.io/apis/inrix/inrix-segment-speed-api/) — Real-time, historical and predicted speed, travel time and reference speed for INRIX XD and TMC road segments, queried by bounding box, radius, point,…
- [INRIX Safety Alerts (Incidents) API](https://apis.io/apis/inrix/inrix-safety-alerts-incidents-api/) — Roadway incident, construction, flow, event and hazard alerts within a bounding box, radius or along a route, with TMC and OpenLR location referencing and…
- [INRIX Traffic Tiles API](https://apis.io/apis/inrix/inrix-traffic-tiles-api/) — Pre-rendered raster traffic tiles for map overlays, addressed by quadkey and rendered from live INRIX speed data.
- [INRIX Fuel Stations API](https://apis.io/apis/inrix/inrix-fuel-stations-api/) — Fuel station locations, brands, amenities and current fuel prices by grade, searchable by bounding box, radius or station identifier.
- [INRIX Dangerous Slowdowns API](https://apis.io/apis/inrix/inrix-dangerous-slowdowns-api/) — Detects and reports sudden, unexpected slowdowns on the road network so vehicles and drivers can be warned ahead of a hazard.
- [INRIX Dangerous Roads API](https://apis.io/apis/inrix/inrix-dangerous-roads-api/) — Ranked collision and safety risk scoring for road segments, used to identify the most dangerous roads and intersections in a geography.
- [INRIX Trade Area Trips API](https://apis.io/apis/inrix/inrix-trade-area-trips-api/) — Aggregated, anonymized trip origin-destination counts into and out of a defined trade area or location polygon, for retail site selection and location…
- [INRIX Trip Trends Reports API](https://apis.io/apis/inrix/inrix-trip-trends-reports-api/) — Trip volume and travel-behaviour trend reports over time for a geography, including seasonal adjustment and data-quality metadata.
- [INRIX Roadway Analytics Data Downloader API](https://apis.io/apis/inrix/inrix-roadway-analytics-data-downloader-api/) — Asynchronous report and bulk speed-data downloader for INRIX Roadway Analytics: submit a report request, poll its status and retrieve the generated dataset.
- [INRIX Data Download Service](https://apis.io/apis/inrix/inrix-data-download-service/) — Queries and downloads static INRIX data deliverables organized by product, dataset and file - beginning with map releases (XD added/removed/replaced, TMC…
- [INRIX Data Upload Service (GPS, XFCD and Parking Event Streams)](https://apis.io/apis/inrix/inrix-data-upload-service-gps-xfcd-and-parking-event-streams/) — Inbound data streams for partners contributing probe data to INRIX: batched JSON POSTs of GPS points, extended floating car data (XFCD) readings, and…
- [INRIX Gateway Map Version API](https://apis.io/apis/inrix/inrix-gateway-map-version-api/) — Reports the current INRIX map and XD network version in use, so consumers can align segment identifiers with the correct map release.
- [INRIX Connected Services Gateway API](https://apis.io/apis/inrix/inrix-connected-services-gateway-api/) — The long-standing INRIX Connected Services gateway (Inrix.ashx), which serves routing, drive time polygons, traffic cameras, road speed at points, segment…
- [INRIX TPEG Connect](https://apis.io/apis/inrix/inrix-tpeg-connect/) — Delivers INRIX traffic, incident, parking, weather and fuel content in TISA TPEG format over HTTP POST sessions, with incremental deltas, configurable…
- [INRIX Visits Analytics API](https://apis.io/apis/inrix/inrix-visits-analytics-api/) — Anonymized visit counts and dwell analytics for points of interest and custom polygons, derived from INRIX device and vehicle movement data.
- [INRIX Accounts API](https://apis.io/apis/inrix/inrix-accounts-api/) — The accounts API from INRIX — 1 operation(s) for accounts.
- [INRIX Application API](https://apis.io/apis/inrix/inrix-application-api/) — The Application API from INRIX — 9 operation(s) for application.
- [INRIX Auth API](https://apis.io/apis/inrix/inrix-auth-api/) — The Auth API from INRIX — 6 operation(s) for auth.
- [INRIX Developer API](https://apis.io/apis/inrix/inrix-developer-api/) — The Developer API from INRIX — 2 operation(s) for developer.
- [INRIX Device API](https://apis.io/apis/inrix/inrix-device-api/) — The Device API from INRIX — 3 operation(s) for device.
- [INRIX Metadata API](https://apis.io/apis/inrix/inrix-metadata-api/) — The Metadata API from INRIX — 1 operation(s) for metadata.
- [INRIX Metrics API](https://apis.io/apis/inrix/inrix-metrics-api/) — The Metrics API from INRIX — 2 operation(s) for metrics.
- [INRIX Namespace Management API](https://apis.io/apis/inrix/inrix-namespace-management-api/) — APIs for managing intersection namespace subscriptions
- [INRIX User API](https://apis.io/apis/inrix/inrix-user-api/) — The User API from INRIX — 18 operation(s) for user.
- [INRIX Caniparkhere API](https://apis.io/apis/inrix/inrix-caniparkhere-api/) — The Caniparkhere API from INRIX — 1 operation(s) for caniparkhere.
- [INRIX Openspots API](https://apis.io/apis/inrix/inrix-openspots-api/) — The Openspots API from INRIX — 2 operation(s) for openspots.
- [INRIX Application Management API](https://apis.io/apis/inrix/inrix-application-management-api/) — The Application Management API from INRIX — 9 operation(s) for application management.
- [INRIX Email Template API](https://apis.io/apis/inrix/inrix-email-template-api/) — The Email Template API from INRIX — 2 operation(s) for email template.
- [INRIX User Group API](https://apis.io/apis/inrix/inrix-user-group-api/) — The User Group API from INRIX — 8 operation(s) for user group.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [inrix](https://apis.io/servers/inrix/inrix/)

#### Collections (3)

Postman and Open Collection request collections.

- [INRIX Parkme API](https://apis.io/collections/inrix/open-inrix-parkme-openapi-original/)
- [INRIX Analytics Webservice Template API](https://apis.io/collections/inrix/open-inrix-signals-analytics-openapi-original/)
- [Inrix.UserAccounts.Web](https://apis.io/collections/inrix/open-inrix-user-accounts-openapi-original/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Inrix Parkme Overlay](https://apis.io/overlays/inrix/inrix-parkme-overlay/)
- [Inrix Signals Analytics Overlay](https://apis.io/overlays/inrix/inrix-signals-analytics-overlay/)
- [Inrix User Accounts Overlay](https://apis.io/overlays/inrix/inrix-user-accounts-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Inrix Authentication](https://apis.io/security/inrix/inrix-authentication/)
- [Inrix Domain Security](https://apis.io/security/inrix/inrix-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://inrix.com/)
- [Documentation](https://docs.inrix.com/)
- [Getting started](https://docs.inrix.com/authentication/getting_authorized/)
- [API reference](https://docs.inrix.com/traffic/general_info/)
- [Pricing](https://inrix.com/contact/)
- [Sign up](https://iq.inrix.com/)
- [Changelog](https://docs.inrix.com/parking/change_log/)
- [Blog](https://inrix.com/blog/)
- [Terms of service](https://inrix.com/site-terms/)
- [Privacy policy](https://inrix.com/site-privacy-policy/)
- [GitHub](https://github.com/INRIX)
- [Status](https://status.inrix.com/)

## API Evangelist rating

**Kin Score 50.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 41.5 |
| Contract governance | 18.2 |
| Operational transparency | 34.2 |
| Developer ergonomics | 73.2 |
| Access clarity | 46.1 |

**Agent readiness 18.2** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
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

**Regulatory alignment 29.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/inrix/](https://apis.io/providers/inrix/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for INRIX: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/inrix/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
