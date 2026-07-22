---
name: Monitor financial news and sentiment for a watchlist
description: Build a filtered news feed with entity-level sentiment, find trending entities, and aggregate sentiment statistics over time with the StockData News API.
api: openapi/stockdata-news-api-openapi.yml
operations: [getFinancialNews, getSimilarNews, getNewsStatsIntraday, getTrendingEntities, getNewsSources]
generated: '2026-07-22'
method: generated
---

# Monitor news and sentiment

Base URL: `https://api.stockdata.org/v1`. Authenticate every GET with the `api_token` query parameter.

## Steps

1. **Pull the feed** — call `getFinancialNews` (`GET /news/all`) with `symbols=<watchlist>` and `filter_entities=true` so the `entities` array only contains the requested symbols. Filter further with `language`, `industries`, `countries`, `published_after`/`published_before`, and sentiment bounds (`sentiment_gte`, `sentiment_lte` — e.g. `sentiment_gte=0.1` for positive coverage).
2. **Paginate** — use `page` + `limit`; the plan sets the max `limit`, `meta.found` gives the total, and the result set is capped at 20,000.
3. **Expand a story** — call `getSimilarNews` (`GET /news/similar/{uuid}`) with an article's `uuid` to cluster related coverage.
4. **Trend detection** — call `getTrendingEntities` (`GET /news/stats/trending`) to rank entities mentioned more than normal, and `getNewsStatsIntraday` (`GET /news/stats/intraday`) with `interval=day&group_by=symbol` for day-by-day mention/sentiment counts.
5. **Curate sources** — call `getNewsSources` (`GET /news/sources`) and prefer the `domains`/`exclude_domains` filters over `source_ids` (many source_ids map to one domain).

## Rules

- Sentiment scores are per-entity (`entities[].sentiment_score`), not per-article; average across highlights when summarizing.
- Responses use the `meta`/`data` envelope; errors use `{"error": {"code", "message"}}` (see `errors/stockdata-problem-types.yml`).
- `403 endpoint_access_restricted` means the stats/aggregation endpoints are not on the current plan — degrade to the base feed instead of retrying.
