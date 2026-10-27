# Current status

Snapshot published October 27, 2026. Application version: **1.2.0**. The application verification cited here was performed on October 26, 2026; it does not establish continuous service availability.

## Purpose

I want the project to make event-contract research inspectable: the market context, contract terms, forecast timestamp, and final outcome should remain connected. The current scope supports that workflow with public data and manual forecasts while the original modeling system is being recovered.

## What exists

| Area | Current behavior | Evidence and limits |
| --- | --- | --- |
| Market desk | TradingView chart, native Coinbase chart fallback, quotes, order book, asset selection, and contract catalog | Live updates, interval and symbol changes, and selected desktop/mobile flows were checked locally. Provider outages and cadence remain external dependencies. |
| Contract research | Public quotes, one-minute trade-price history, expiry context, settlement rules, and forecast capture | A real contract and its history rendered in the local browser check. Spot context does not replace the contract’s settlement source. |
| Manual journal | Pre-close probability and quote snapshots, final outcome checks, Brier scores, archive/restore, CSV/JSON export | One real open-to-final lifecycle and controlled failure/correction fixtures were checked. Storage is local to the browser and origin. |
| Public interface | Introduction, market desk, research explanation, project page, and restricted Control Panel | Selected navigation and 390 × 844 layouts were checked. Login, registration, billing, and trading operations are absent. |
| Model engine | Explicitly offline status | The health endpoint declares the edition’s offline state. No trained inference is running or verified. |
| Delivery | Local application and this public documentation library | A production build passed locally. There is no public application deployment or hosted-environment verification. |

The [verification record](../verification/2026-10-26-v1.2.md) defines the scope behind these statements. It is a bounded record, not a claim that every feature or browser has been tested.

## Architecture decisions

The public-data proxy admits specific routes and parameters rather than accepting arbitrary upstream requests. TradingView supplies the advanced chart controls, with a native chart available when the embed is unavailable. A browser-local journal keeps the research workflow usable without accounts. The model indicator is separate from market connectivity, and administrative operations are disabled at the server boundary. The [architecture reference](architecture.md) explains the mechanisms and tradeoffs.

## Modeling recovery

Historical material describes two distinct efforts. Earlier research used Coinbase minute candles, synthetic contract targets, logistic and XGBoost models, and calibration experiments. Later BTC/ETH work used settled Kalshi labels, Coinbase context, logistic and histogram gradient boosting models, and time-based splits with calibration.

Some source snapshots, configuration, metadata, evaluation reports, and training history have been recovered. The later backend recovery contains 39 complete text snapshots across 37 original paths, alongside partial files. Six trained model binaries, later datasets, and parts of the runtime remain missing. The recovered text is not a complete runnable backend.

Those historical recipes describe prior work; they do not establish reproducible performance today. Synthetic settlement proxies, coarse source data near expiry, and incomplete provenance limit what can be inferred from the old reports. No historical accuracy, profit, or forecasting edge is claimed here.

## Implemented but not established

Timeouts, retries, request pacing, cache limits, and bounded queues exist in the implementation. Automated checks exercise selected error paths, but there is no production load, uptime, or cross-browser reliability result. The model availability UI is present; automatic validation of a restored scorer is not implemented. The production bundle exists; hosted feed behavior remains unverified.

## Remaining work

1. Recover the missing artifacts or define a reproducible retraining baseline with traceable datasets and labels.
2. Audit feature mapping, time alignment, quote freshness, calibration, and out-of-sample evaluation before connecting inference.
3. Add read-only model summaries only when artifact provenance and prediction timestamps can be verified.
4. Select a deployment environment and verify the public data routes, chart embed, and storage behavior there.
5. Address journal portability if the workflow expands beyond one browser. Import and cloud sync are not implemented.

An operational administrator system would be a separate future decision. The current “Admin access only” page does not provide administrator authentication or controls.
