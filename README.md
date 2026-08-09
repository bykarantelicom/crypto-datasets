# ByKaranteli Crypto Datasets

Free, CC0-licensed crypto market datasets, updated daily by an automated pipeline.
Maintained by [ByKaranteli](https://bykaranteli.com), a crypto derivatives terminal
built on Binance USDT-M perpetual data.

No API key, no rate limits on this repo, no attribution required (CC0).
If these datasets are useful, a link back to the source pages helps us keep them free.

## Datasets

| File | What it contains | Updated | Live source |
| --- | --- | --- | --- |
| [`data/daily-market.csv`](data/daily-market.csv) | One row per UTC day: BTC dominance %, ETH dominance %, total crypto market cap, 24h volume, stablecoin cap, Fear & Greed value + classification | daily | [bykaranteli.com/data](https://bykaranteli.com/data) |
| [`data/daily-symbols.csv`](data/daily-symbols.csv) | Per-symbol daily stats for tracked Binance USDT-M perpetuals: funding rate %, 24h open-interest change %, 24h price change % | daily | [bykaranteli.com/data](https://bykaranteli.com/data) |
| [`data/listings.csv`](data/listings.csv) | Perpetual listing/delisting tracker across 6 exchanges (Binance, OKX, Bybit, Gate, HTX, BingX): symbol, exchange, status, first seen, delisted at | daily | [bykaranteli.com/listings](https://bykaranteli.com/listings) |
| [`data/liquidations-daily.csv`](data/liquidations-daily.csv) | Daily long/short liquidation totals (USD) per symbol and exchange, recorded from public Binance, Bybit and OKX streams. Recorded events, not estimates; collection began 2026-07-30 | daily | [bykaranteli.com/liquidations](https://bykaranteli.com/liquidations) |
| [`data/etf-flows.csv`](data/etf-flows.csv) | US spot Bitcoin and Ethereum ETF daily flows: net inflow, total net assets, cumulative inflow, value traded (USD). Aggregated from SoSoValue public data | daily | [bykaranteli.com/etf](https://bykaranteli.com/etf) |
| [`data/cot-weekly.csv`](data/cot-weekly.csv) | Weekly CFTC Commitments of Traders positioning for CME Bitcoin, Micro Bitcoin, Ether and Micro Ether futures since 2018: open interest and per-category long/short contracts | weekly | [bykaranteli.com/cot](https://bykaranteli.com/cot) |
| [`data/premium-daily.csv`](data/premium-daily.csv) | Coinbase spot premium for BTC and ETH since 2017-08: US close, global close and the premium in % | daily | [bykaranteli.com/premium](https://bykaranteli.com/premium) |
| [`data/dvol-daily.csv`](data/dvol-daily.csv) | Deribit DVOL implied-volatility index for BTC and ETH since 2021-03, one row per currency per UTC day | daily | [bykaranteli.com/options](https://bykaranteli.com/options) |
| [`data/options-oi-daily.csv`](data/options-oi-daily.csv) | Deribit BTC and ETH options open-interest chain for the current day: instrument, expiry, strike, type, open interest, mark IV, underlying. Replaced each day, so earlier days live in this repo's git history | daily | [bykaranteli.com/options](https://bykaranteli.com/options) |
| [`data/indices-latest.json`](data/indices-latest.json) | Latest snapshot of our market indices: Fear & Greed, BTC dominance, stablecoin cap, Retail Euphoria Index, and the [Altcoin Season Index](https://bykaranteli.com/glossary/altcoin-season-index) | daily | [api](https://bykaranteli.com/api/public/indices) |

Column-level notes live in each dataset's header row. CFTC COT, Coinbase premium,
DVOL and ETF flows ship with backfilled history from their own start dates; our own
accumulation (daily market, per-symbol, listings, liquidations) started 2026-07-23
and grows one row per day from there.

## Live versions and more data

- Live JSON APIs (free, CORS-enabled, no key): `https://bykaranteli.com/api/public/indices`, `/api/public/heatmap`, `/api/public/pressure`, `/api/public/top-movers`
- [Altcoin Season Index (live)](https://bykaranteli.com/glossary/altcoin-season-index) · [Bitcoin dominance (live)](https://bykaranteli.com/glossary/btc-dominance) · [Fear & Greed (live)](https://bykaranteli.com/glossary/fear-and-greed)
- [Funding rate heatmap](https://bykaranteli.com/heatmap) · [Exchange listings tracker](https://bykaranteli.com/listings)
- Chinese versions of all public pages live under [bykaranteli.com/zh](https://bykaranteli.com/zh)

## Update pipeline

A daily job exports these files from the same database that serves
bykaranteli.com and pushes the diff here. If a day is missing, the pipeline
skipped rather than fabricate values; gaps are honest.

## License

[CC0 1.0 Universal](LICENSE): public domain dedication. Use the data for
anything, commercial or not, no permission needed.
