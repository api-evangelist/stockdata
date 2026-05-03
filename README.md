# StockData

StockData.org provides free real-time, intraday, and historical stock, forex, and cryptocurrency market data along with global financial news and sentiment analysis. The REST API delivers market data for US-listed stocks including OHLCV data, splits, dividends, and entity-level news sentiment from 5,000+ sources in 30+ languages.

**URL:** [https://raw.githubusercontent.com/api-evangelist/stockdata/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/stockdata/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Finance
- Financial Data
- Stock Market
- Market Data
- News
- Sentiment Analysis

## Timestamps

- **Created:** 2025-02-24
- **Modified:** 2026-05-02

## APIs

### StockData API

Real-time stock quotes, intraday and historical OHLCV data, splits, dividends, global financial news with entity-level sentiment analysis, and entity search.

**Human URL:** [https://www.stockdata.org/](https://www.stockdata.org/)

#### Tags

- Finance, Financial Data, Stock Market, Market Data, News, Sentiment Analysis

#### Properties

- [Documentation](https://www.stockdata.org/documentation)
- [Website](https://www.stockdata.org/)
- [OpenAPI](openapi/stockdata-openapi.yml)

## OpenAPI Specifications

| Spec | Operations | Description |
|---|---|---|
| [stockdata-openapi.yml](openapi/stockdata-openapi.yml) | 16 | Full StockData REST API — quotes, intraday, EOD, splits, dividends, news, entities |

## Capabilities

### Workflow Capabilities

| Capability | Tools | Description |
|---|---|---|
| [market-data-intelligence.yaml](capabilities/market-data-intelligence.yaml) | 8 | Unified market data and news intelligence for quant analysts and algorithmic traders |

### Shared Definitions

| Definition | Resources | Description |
|---|---|---|
| [shared/stockdata.yaml](capabilities/shared/stockdata.yaml) | 8 | StockData API consumed definition |

## Rules

| Ruleset | Description |
|---|---|
| [stockdata-rules.yml](rules/stockdata-rules.yml) | Spectral ruleset enforcing StockData API conventions |

## JSON Schema

| Schema | Description |
|---|---|
| [stockdata-quote-schema.json](json-schema/stockdata-quote-schema.json) | Real-time stock quote data schema |
| [stockdata-news-article-schema.json](json-schema/stockdata-news-article-schema.json) | Financial news article with entity sentiment schema |

## JSON Structure

| Structure | Description |
|---|---|
| [stockdata-quote-structure.json](json-structure/stockdata-quote-structure.json) | Stock quote API response document structure |

## JSON-LD

| Context | Description |
|---|---|
| [stockdata-context.jsonld](json-ld/stockdata-context.jsonld) | JSON-LD context mapping StockData vocabulary to schema.org and FIBO |

## Examples

| Example | Description |
|---|---|
| [stockdata-get-stock-quote-example.json](examples/stockdata-get-stock-quote-example.json) | Get real-time quotes for AAPL and MSFT |
| [stockdata-get-financial-news-example.json](examples/stockdata-get-financial-news-example.json) | Get positive-sentiment financial news for AAPL |

## Vocabulary

| Vocabulary | Description |
|---|---|
| [stockdata-vocabulary.yml](vocabulary/stockdata-vocabulary.yml) | Domain vocabulary covering market data, corporate actions, and news sentiment |

## Common Properties

- [Portal](https://www.stockdata.org/)
- [Documentation](https://www.stockdata.org/documentation)
- [Sign Up](https://www.stockdata.org/register)
- [Pricing](https://www.stockdata.org/pricing)
- [Website](https://www.stockdata.org/)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
