---
name: Get quotes and price history for US-listed stocks
description: Fetch a real-time quote, then pull adjusted intraday and end-of-day history, splits, and dividends for one or more tickers from the StockData API.
api: openapi/stockdata-stock-data-api-openapi.yml
operations: [getStockQuote, getIntradayAdjusted, getEndOfDayData, getStockSplits, getStockDividends]
generated: '2026-07-22'
method: generated
---

# Get quotes and price history

Base URL: `https://api.stockdata.org/v1`. Every request is a GET and must carry `api_token=<token from the StockData dashboard>` as a query parameter (see `authentication/stockdata-authentication.yml`).

## Steps

1. **Real-time quote** — call `getStockQuote` (`GET /data/quote`) with `symbols` as a comma-separated ticker list (e.g. `AAPL,MSFT,TSLA`). Add `extended_hours=true` for pre/post market prices and `key_by_ticker=true` to key results by symbol. Symbol count per request is capped by plan (3 on Free, up to 100 on Pro).
2. **Intraday history** — call `getIntradayAdjusted` (`GET /data/intraday/adjusted`) with `symbols` (one symbol on most plans). If the requested date range exceeds the plan's history window, the API clamps to the max interval.
3. **End-of-day history** — call `getEndOfDayData` (`GET /data/eod`); the same endpoint also serves EOD crypto and forex data.
4. **Corporate actions** — call `getStockSplits` (`GET /data/splits`) and `getStockDividends` (`GET /data/dividends`) per ticker to adjust or annotate the series.

## Rules

- All list responses arrive as `{"meta": {...}, "data": [...]}`; check `meta.returned` against `meta.limit`.
- On `429` (`rate_limit_reached`) back off 60 seconds; on `402` (`usage_limit_reached`) the daily plan quota is exhausted — stop rather than retry (see `errors/stockdata-problem-types.yml`).
- All operations are read-only GETs — safe to retry after transient `500`/`503`.
- Data is indicative and not appropriate for trading purposes (provider disclaimer).
