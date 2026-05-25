# Strategic Allocation Cycles Index

Each Strategic Allocation cycle gets its own markdown file. A cycle is one complete deployment on a single asset: trigger → tranching → trend hold → structural break exit → return to BIL.

See `Trading_OS.md` § 19 for the full discipline.

## File naming convention

`cycle_YYYY-MM-DD_ASSET_short-name.md`

The date is the cycle open date (first tranche). Short name describes the trigger (e.g., `gold_dislocation`, `spy_post-correction-reclaim`, `btc_bottoming`).

Example: `cycle_2026-08-15_GLD_macro-dislocation.md`

## Lifecycle status values

- **Planned** — Plan section filled, awaiting trigger conditions
- **Active** — at least one tranche entered, cycle running
- **Closed** — full exit executed, Review section filled, capital returned to BIL
- **Aborted** — cycle was planned but invalidated before any tranche entered

## File template structure

1. Header — Cycle ID, asset, open date, current status, target allocation, actual deployed
2. Plan — Thesis (technical + narrative), trigger criteria met, target allocation, tranching schedule
3. Tracking — Tranche-by-tranche entries (date, size, price, structural signal), evolving observations
4. Review — Did the trend play out? Exit reasoning. Lessons.
5. Handoff — State at exit, capital returned to BIL, what we learned

## Active cycles

(none yet)

## Closed cycles

(none yet)

## 401k cycles

When activated at Quest 2 close, 401k Strategic Allocation cycles use prefix `401k_cycle_YYYY-MM-DD_ASSET_short-name.md`.
