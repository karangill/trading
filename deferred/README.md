# Deferred Files

These files were created in the initial framework build but deferred during Sprint 1. They're not premature concepts — they're just not useful yet because the data they capture only becomes meaningful once enough trades exist to aggregate.

| File | Reactivate when |
|---|---|
| `setup_stats.csv` | After ~20 trades across multiple setup types — once aggregations are statistically meaningful (likely end of Sprint 1 or during Sprint 2 review) |
| `instrument_stats.csv` | After ~20 trades across multiple instrument buckets (shares, 0-14 DTE, 14-30, 30-60, 60-90, LEAPS) |
| `options_tracker.csv` | If we need contract-specific learning isolated from the main trade log (e.g., spread quality analysis, theta/IV decay attribution). Until then, all option-specific fields live in `trade_log.csv`. |

Until reactivation, aggregations can be computed on-demand from `trade_log.csv` by Claude during Weekly Review.

Don't delete — they have correct schemas and we'll want them later. Move back to project root when activating.
