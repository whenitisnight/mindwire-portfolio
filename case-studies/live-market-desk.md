# Restoring the live market desk

Documented October 27, 2026, from the version 1.2.0 implementation and October 26 verification.

## Goal

I wanted the recovered desk to retain the original chart experience while making its actual capabilities clear. An animated price display could otherwise suggest that the prediction engine had also been restored, even though the trained artifacts were still missing.

## Architecture

The desk uses the original TradingView advanced chart as its default, preserving familiar drawing, indicator, and interval controls. A native Coinbase chart remains available through a provider selector. The selection persists locally, so a provider failure does not force the same choice on every visit.

The embed waits for TradingView’s ready callback. One stalled initial frame receives an automatic retry; a subsequent timeout exposes explicit retry and native-chart controls. That gives the interface a bounded failure state while preserving the external provider’s chart capabilities. Provider loading and telemetry remain dependencies outside the application’s control.

Market connectivity and model availability have separate indicators. Public price updates drive the market desk. Application health declares the model offline, and no market quote or manual probability is substituted for model output.

## Resolving mixed order books

Asset switching exposed a concrete correctness problem: an ETH view could receive price levels from another product. The feed identifies the product on the event, so filtering only individual level updates was insufficient. A mismatched snapshot could also clear the selected book before any level filtering happened.

The book now validates the event’s product identifier before any mutation. Reconnects discard the previous state and wait for a matching snapshot. Incremental updates replace a price level’s quantity, zero quantities remove levels, and malformed prices or quantities are rejected. The result is a book whose state follows the selected product across switching and reconnects.

## Verification

The October 26 browser record shows live BTC candle changes, a 15-minute to one-minute interval change, and an ETH symbol change. After the isolation fix, ETH book levels appeared around the ETH quote without the previous BTC contamination. Three regression tests cover product isolation, snapshot gating and quantity changes, and invalid levels.

The same record includes a 390 × 844 viewport check without document overflow. TradingView rendered and updated despite failed telemetry requests. Initial embed stalls were observed, which is why retry and fallback behavior remain part of the interface. These checks support the inspected flows, not an uptime or latency guarantee.

## Remaining work

The chart is a functioning market-data surface. The missing trained artifacts and incomplete runtime still block model inference. Deployment verification and broader browser coverage also remain open. The [full verification record](../verification/2026-10-26-v1.2.md) keeps those limits attached to the results.
