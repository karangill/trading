# Campaigns Index

Every active campaign gets its own markdown file in this folder. Each file follows the same four-section lifecycle: **Plan → In-Progress Tracking → Review → Handoff**.

A **campaign** is one continuous bet on one ticker in one direction across one or more trades, sharing a single invalidation. See `Trading_OS.md` § 16 for full definition.

Campaigns are distinct from phases:
- **Phases** are time-boxed, sequential framework milestones (e.g., Sprint 1). One at a time.
- **Campaigns** are event-triggered, can run in parallel, open and close based on market events.

## File naming convention

`campaign_YYYY-MM-DD_TICKER_short-name.md`

The date is the campaign open date. Short name describes the thesis (e.g., `nvda_earnings-runup`, `spy_breakout-retest`, `tsla_breakdown`).

Example: `campaign_2026-05-27_NVDA_post-earnings-breakout.md`

## Lifecycle status values

- **Planned** — file exists, Plan section filled, first ticket exists, position not yet entered
- **Active** — at least one entry executed, position partially or fully open
- **Closed** — fully exited (won, lost, or invalidated), Review section filled
- **Aborted** — Plan section exists but campaign never executed (didn't trigger, market moved past, posture changed)

## File template structure

Each campaign file has these sections:

1. **Header** — Campaign ID, ticker, direction, open date, status, links to tickets
2. **Plan** — Thesis (technical + narrative), invalidation, target zones, profit-taking plan, max campaign risk
3. **In-Progress Tracking** — Trade-by-trade actions, observations, evolving thesis
4. **Review** — Did the thesis play out? Grading. Lessons.
5. **Handoff** — Any open questions or framework feedback

## Active campaigns

(none yet)

## Closed campaigns

(none yet)
