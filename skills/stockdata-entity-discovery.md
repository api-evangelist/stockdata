---
name: Discover entities and build symbol filters
description: Resolve company names to symbols and enumerate the entity types and industries used to filter StockData news and market data.
api: openapi/stockdata-entities-api-openapi.yml
operations: [searchEntities, listEntityTypes, listIndustries]
generated: '2026-07-22'
method: generated
---

# Discover entities

Base URL: `https://api.stockdata.org/v1`. Authenticate every GET with the `api_token` query parameter.

## Steps

1. **Resolve names to symbols** — call `searchEntities` (`GET /entity/search`) with a free-text query; each hit returns `symbol`, `name`, `type`, `industry`, `exchange`, `mic_code`, `country`, and `currency`. Use the returned `symbol` values in the `symbols` parameter of the Stock Data and News APIs.
2. **Enumerate types** — call `listEntityTypes` (`GET /entity/type/list`) to get the valid values for the News API `entity_types` filter (equities, cryptocurrencies, currencies, ...).
3. **Enumerate industries** — call `listIndustries` (`GET /entity/industry/list`) to get valid `industries` filter values.

## Rules

- Entity search is the join point between the three StockData APIs — the `symbol`/ticker is the shared key (see `data-model/stockdata-data-model.yml`).
- Cache the type and industry lists; they change rarely and each call counts against the daily plan quota.
- Handle the standard error envelope and rate-limit headers per `conventions/stockdata-conventions.yml`.
