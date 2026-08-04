# Opendatasoft

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Open data platform with REST APIs for accessing public datasets from 1,000+ cities and organizations, providing standard OData and JSON query interfaces. Now operating as Huwise, the platform powers 3,000+ data marketplaces for government agencies, utilities, energy companies, banks, and transport organizations across 25 countries.

**Provider:** Huwise (formerly Opendatasoft)
**Website:** https://www.huwise.com/en/
**Developer Docs:** https://help.opendatasoft.com/
**GitHub:** https://github.com/opendatasoft

## APIs

### Explore API v2.1 (Current)
RESTful API for searching, browsing, and querying datasets on any Opendatasoft-powered portal.

- **Base URL:** `https://{domain}/api/explore/v2.1`
- **Docs:** https://help.opendatasoft.com/apis/ods-explore-v2/
- **Formats:** JSON
- **Auth:** API key (header or query param) or OAuth2; anonymous access for public datasets

Key endpoints:
- `GET /catalog/datasets` — list and search datasets
- `GET /catalog/datasets/{dataset_id}` — dataset metadata and schema
- `GET /catalog/datasets/{dataset_id}/records` — query records (ODSQL)
- `GET /catalog/datasets/{dataset_id}/exports/{format}` — bulk export
- `GET /catalog/datasets/{dataset_id}/aggregates` — aggregation/analysis
- `GET /catalog/facets` — catalog facet values

### OData API
OData 3.0 and 4.0 compliant interface for querying datasets using standard OData query parameters.

- **Base URL:** `https://{domain}/api/odata`
- **Docs:** https://help.opendatasoft.com/apis/odata/
- **Formats:** JSON, XML, ATOM
- **Auth:** API key or OAuth2; anonymous access for public datasets

### Explore API v1 (Deprecated)
Legacy search API — still operational but new projects should use v2.1.

- **Docs:** https://help.opendatasoft.com/apis/ods-search-v1/

## Authentication

| Method | How to Use |
|--------|-----------|
| API Key | `?apikey=YOUR_KEY` query param or `X-API-Key: YOUR_KEY` header |
| OAuth2 | Bearer token via `/oauth2/authorize/` and `/oauth2/token/` endpoints |
| Anonymous | No credentials needed for public datasets |

## Rate Limits

Rate limits are portal-specific and communicated via response headers:

| Header | Description |
|--------|-------------|
| `X-RateLimit-Limit` | Daily quota |
| `X-RateLimit-Remaining` | Remaining calls today |
| `X-RateLimit-Reset` | Unix timestamp of next reset |

- Anonymous users on public.opendatasoft.com: **10,000,000 calls/day**
- Records per request: **100** (up to 10,000 with pagination)
- HTTP 429 returned when quota is exceeded

## Plans

| Tier | Cost | Notes |
|------|------|-------|
| Anonymous | Free | Public datasets, up to 10M calls/day on public portal |
| Authenticated | Free | Register on portal for extended quota + restricted dataset access |
| Enterprise | Quote | Full Huwise platform license for deploying your own portal |

## Repository Contents

```
apis.yml                              # APIs.json 0.19 provider profile
plans/
  opendatasoft-explore-api.yml        # Explore API plans
  opendatasoft-odata-api.yml          # OData API plans
rate-limits/
  opendatasoft-explore-api.yml        # Explore API rate limits
  opendatasoft-odata-api.yml          # OData API rate limits
finops/
  opendatasoft.yml                    # FinOps guidance
```
