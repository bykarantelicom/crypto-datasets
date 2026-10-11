# ByKaranteli Crypto Datasets

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22049575.svg)](https://doi.org/10.5281/zenodo.22049575)

> **Frozen on 2026-09-10.** This mirror is no longer refreshed. The files in
> `data/` and `releases/` do not change; the scope of their licence is set out
> under [Licence scope](#licence-scope) below.
> The same series continue to grow on [bykaranteli.com/data](https://bykaranteli.com/data)
> (CSV and JSON, a free account key, one year of history per file) and through
> the [public API](https://bykaranteli.com/developers) and the
> [MCP server](https://github.com/bykarantelicom/bykaranteli-mcp), under the
> [ByKaranteli Data Licence](https://bykaranteli.com/data#license): free for
> personal and research use with attribution, commercial use with the Business
> plan, redistribution of derived data with the Scale plan. Deeper data (raw
> events, 5-minute and hourly history, monthly bulk files) is sold per call or
> per plan: [pricing](https://bykaranteli.com/pricing).

Crypto market datasets recorded by [ByKaranteli](https://bykaranteli.com),
a crypto derivatives data platform, and published here daily between 2026-07-23
and 2026-09-10. If they are useful, a link back to the source pages is appreciated.

## Licence scope

The CC0 1.0 dedication in [LICENSE](LICENSE) covers ByKaranteli's own computations
in these files: aggregates across venues, daily totals computed from recorded
events, indices, scores, premiums and model outputs. It does not reach third-party
data in them: a venue's or provider's values as we received them (for example a
single venue's prices, open interest, funding or option chain) remain subject to
that source's terms, and we grant no right in them. See the
[Terms of Service, "Data, licences and attribution"](https://bykaranteli.com/terms).

On 2026-10-11 the files that carried a data provider's series were withdrawn from
`data/` and `releases/`: US spot ETF flows (`etf-flows.csv`, `etf-fund-flows.csv`),
market totals and the Fear & Greed value (`daily-market.csv`, `indices-latest.json`),
Deribit's DVOL index (`dvol-daily.csv`) and the per-metric file that combined them
(`metric-daily.csv`).

## Datasets

| File | What it contains | Updated | Live source |
| --- | --- | --- | --- |
| [`data/daily-symbols.csv`](data/daily-symbols.csv) | Per-symbol daily stats for tracked Binance USDT-M perpetuals: funding rate %, 24h open-interest change %, 24h price change % | daily | [bykaranteli.com/data](https://bykaranteli.com/data) |
| [`data/listings.csv`](data/listings.csv) | Perpetual listing/delisting tracker across 6 exchanges (Binance, OKX, Bybit, Gate, HTX, BingX): symbol, exchange, status, first seen, delisted at | daily | [bykaranteli.com/listings](https://bykaranteli.com/listings) |
| [`data/liquidations-daily.csv`](data/liquidations-daily.csv) | Daily long/short liquidation totals (USD) per symbol and exchange, recorded from six public exchange liquidation feeds (Binance, Bybit, OKX, Gate, HTX, dYdX). Recorded events, not estimates: a floor, not the sector total; collection began 2026-07-30 | daily | [bykaranteli.com/liquidations](https://bykaranteli.com/liquidations) |
| [`data/cot-weekly.csv`](data/cot-weekly.csv) | Weekly CFTC Commitments of Traders positioning for CME Bitcoin, Micro Bitcoin, Ether and Micro Ether futures since 2018: open interest and per-category long/short contracts | weekly | [bykaranteli.com/cot](https://bykaranteli.com/cot) |
| [`data/premium-daily.csv`](data/premium-daily.csv) | Coinbase spot premium for BTC and ETH since 2017-08: US close, global close and the premium in % | daily | [bykaranteli.com/premium](https://bykaranteli.com/premium) |
| [`data/options-oi-daily.csv`](data/options-oi-daily.csv) | Deribit BTC and ETH options open-interest chain for the current day: instrument, expiry, strike, type, open interest, mark IV, underlying. Replaced each day, so earlier days live in this repo's git history | daily | [bykaranteli.com/options](https://bykaranteli.com/options) |
| [`data/theme-indices-daily.csv`](data/theme-indices-daily.csv) | Eight equal-weight crypto narrative indices (AI, RWA, DePIN, meme, L1, L2, DeFi, quantum) from Binance daily closes, rebased to 100 on 2025-01-01, one row per theme per day; baskets are fixed lists that change only with a dated commit | daily | [bykaranteli.com/themes](https://bykaranteli.com/themes) |
| [`data/venue-markets-daily.csv`](data/venue-markets-daily.csv) | Per venue, market and symbol: the last snapshot of each UTC day with USD price, 24h volume, open interest and 8h-equivalent funding across 56 feeds on 43 exchanges, since 2026-08-21 | daily | [bykaranteli.com/venues](https://bykaranteli.com/venues) |
| [`data/whale-trades-daily.csv`](data/whale-trades-daily.csv) | Per symbol per day: count of $1M+ aggressive market prints, buy and sell notional and the buy share, from our own trade sockets (rolling 90 days) | daily | [bykaranteli.com/whales](https://bykaranteli.com/whales) |
| [`data/stablecoin-pegs-daily.csv`](data/stablecoin-pegs-daily.csv) | USDT, USDC, DAI and FDUSD per day: number of spot venues quoting them in USD terms and the min, median and max price at the day's last snapshot, since 2026-08-21 | daily | [bykaranteli.com/venues](https://bykaranteli.com/venues) |

Column-level notes live in each dataset's header row. CFTC COT and Coinbase premium
ship with backfilled history from their own start dates; our own accumulation
(per-symbol, listings, liquidations) started 2026-07-23 and grew one row per day
until the freeze.

## Live versions and more data

- Live JSON APIs (free account key, CORS-enabled): every product has one under `https://bykaranteli.com/api/public/<product>` (indices, heatmap, pressure, top-movers, liquidations via datasets, options, options/surface, etf, themes, factors, venues/markets, venues/lead-lag, whales, quantum, macro, network and more); the full list with parameters: [bykaranteli.com/openapi.json](https://bykaranteli.com/openapi.json)
- [Altcoin Season Index (live)](https://bykaranteli.com/glossary/altcoin-season-index) · [Bitcoin dominance (live)](https://bykaranteli.com/glossary/btc-dominance) · [Fear & Greed (live)](https://bykaranteli.com/glossary/fear-and-greed)
- [Funding rate heatmap](https://bykaranteli.com/heatmap) · [Exchange listings tracker](https://bykaranteli.com/listings)
- Chinese versions of all public pages live under [bykaranteli.com/zh](https://bykaranteli.com/zh)

## Update pipeline

Until 2026-09-10 a daily job exported these files from the same database that
serves bykaranteli.com and pushed the diff here; if a day was missing, the
pipeline skipped rather than fabricate values, so gaps are honest. The job is
stopped: the live, growing versions are served from
[bykaranteli.com/data](https://bykaranteli.com/data) and the quarterly frozen
releases in `releases/` are the last snapshots (less the files withdrawn on
2026-10-11).

## Citation

Every quarterly frozen release is archived on Zenodo with a DOI. Cite the
concept DOI for the dataset as a whole, or a version DOI for an exact snapshot:

> ByKaranteli (2026). ByKaranteli Crypto Datasets. Zenodo. https://doi.org/10.5281/zenodo.22049575

## License

ByKaranteli's own computations in the files of this repository:
[CC0 1.0 Universal](LICENSE), public domain dedication. Third-party data in them
stays under its sources' terms (see [Licence scope](#licence-scope)).

Data served live from bykaranteli.com after 2026-09-10 (downloads, API, MCP)
is under the [ByKaranteli Data Licence](https://bykaranteli.com/data#license):
personal and research use with the attribution line "Data: ByKaranteli
(bykaranteli.com)"; commercial use with the Business plan; redistribution of
derived data with the Scale plan; raw records are for your own use on every plan.
