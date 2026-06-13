# Opendatasoft

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
