# Recording forecasts before the outcome is known

Documented October 27, 2026, from the version 1.1.0 journal retained in version 1.2.0 and its October 26 verification.

## Goal

I wanted the research workspace to preserve what a forecast meant at the time it was made. A probability entered after closing, an overwritten quote benchmark, or a preliminary result treated as final would make later comparisons misleading.

## Mechanism

Saving a forecast re-fetches the contract and checks that it is still open. The response must have been received within 30 seconds, and the YES probability must be between 0% and 100%. The record keeps that probability, its note, the contract snapshot, receipt time, capture time, and a valid YES bid/ask midpoint when available. One forecast is accepted per ticker, including archived records.

Outcome checks match the contract ticker and require a finalized or settled YES/NO result without a provisional flag. The original forecast and quote snapshot remain unchanged when the result is checked again. Controlled fixtures exercise settlement corrections; failed requests preserve the prior record.

The Brier calculation is `(p - y)^2`, with YES represented by 1 and NO by 0. The paired comparison includes only finalized records with a valid captured midpoint, using the same records for both scores. Archived forecasts remain in aggregates and exports, so hiding an entry cannot improve the score. A midpoint is a comparison reference, not a promised execution price.

## Verification

An isolated local browser collection captured a 50% test forecast while a real contract was open. After closing, the final NO outcome was retrieved. The forecast scored 0.2500, and the captured 63.5% midpoint scored 0.4032. This single observation verifies the calculation and lifecycle; it provides no evidence of predictive advantage.

Reload persistence, archive/restore, pre-close outcome checks, and CSV/JSON downloads were also checked. Automated cases cover late or stale captures, duplicate records, storage failures, result corrections, paired comparisons, and formula-like CSV text. See the [dated verification record](../verification/2026-10-26-v1.2.md).

## Tradeoffs

Local storage keeps the workflow accessible without registration, but it is tied to a browser and origin. The interface preserves original records; the underlying storage and device clock are still editable. The journal therefore supports personal research rather than an independently trusted audit trail.

Exports preserve the collection for external review. Import and cloud sync remain future work. Small, self-selected or correlated samples cannot establish forecasting performance, and Brier scores do not measure profit, fees, liquidity, or execution quality.
