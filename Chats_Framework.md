# KSG Trading OS — Chats Framework

**Top layer of the OS — interaction layer**
**Last updated:** 2026-05-23 (v0.4)

Defines how chats are organized, launched, and how their outputs promote into the doc or CSV files.

---

## 1. Architecture Recap

The Trading OS has three layers plus a meta layer:

| Layer | Artifact | Purpose |
|---|---|---|
| Base | CSV files + per-campaign markdown in `campaigns/` + per-cycle markdown in `strategic_allocations/` | Ground truth — what actually happened |
| Middle | `Trading_OS.md` | How we think and decide — three books, philosophy, setups, rules, grading |
| Top | Chats in this project | Where we apply, observe, decide, and revise |
| Calendar | **Trading** Google Calendar | Where the plan lives in time — daily desks, weekly reviews, sprint milestones, macro events. Updated by Claude during reviews. |
| Meta | Framework chat | Where the framework itself gets revised |

Each chat type below has a defined purpose, a launch prompt, and a promotion path.

---

## 2. Chat Types

### 2.1 Framework / Trading Operating System

- **Cadence:** Ad-hoc; whenever framework needs revision. Mandatory at end of each Sprint.
- **Purpose:** Revise the operational doc, CSV structure, or chats framework itself.
- **Inputs:** Current state of `Trading_OS.md` + CSV files; recent friction points or gaps
- **Outputs:** Updated `Trading_OS.md` (with Framework Evolution Log entry); updated CSV structure; updated `Chats_Framework.md` if chats change; new rows in `intervention_log.csv` and `hypotheses_register.csv` if applicable

**Launch prompt:**

```
Initialize a Framework Evolution session for the KSG Trading OS.

Context: I want to evolve the framework itself, not execute trades within it.

Read Trading_OS.md + CSVs + Chats_Framework.md, give me your current read on:
  1. What the framework is doing well
  2. What's missing, broken, or drifting
  3. Whether decision rules and hypotheses are still calibrated to evidence

Then propose specific changes. Update the files directly via filesystem.
```

### 2.2 Weekly Review

- **Cadence:** Weekly, Sunday evening (Friday afternoon acceptable if needed)
- **Purpose:** Read the week's data, update Snapshot, plan next week's focus list and posture, check Strategic Allocation status. Catches drift before it compounds.
- **Inputs:** Last 7 days of `trade_log.csv`, `trade_actions.csv`, `mistake_log.csv`, `daily_desk.csv`, `risk_drawdown.csv`, `capital_allocation.csv`; current Sprint file; current Snapshot
- **Outputs:** Updated Snapshot in `Trading_OS.md` § 2; row in `weekly_review.csv`; updated `capital_allocation.csv`; next-week Trading Book focus list (core + thematic); posture; phase file Tracking updated; any guard rail actions

**Launch prompt:**

```
Weekly Review for week ending [DATE].

Read Trading_OS.md Snapshot and the week's data. Walk me through:
  1. SPY/QQQ weekly/daily structure; market regime
  2. Macro and earnings calendar for next week
  3. Open Trading Book positions and overnight risk
  4. Strategic Allocation status — any cycles approaching trigger? any active cycles approaching exit?
  5. Prior week realized + unrealized P&L by book
  6. Process compliance %, A-Trade %, rule violations
  7. Best and worst trades; emotional patterns
  8. Next-week Trading Book focus: 1-2 indices + 1-3 core + 0-3 thematic
  9. Posture for the week

Update Snapshot, append to weekly_review.csv, update capital_allocation.csv,
update Sprint file. Be direct about process gaps.
```

### 2.3 Daily Trading Desk

- **Cadence:** Daily — pre-market for setup, EOD for reconciliation
- **Purpose:** Pre-market planning + EOD reconciliation
- **Inputs:** Pre-market: SPY/QQQ futures + overnight + macro/news (web search); current Snapshot; current focus list; open positions. EOD: today's actions, open positions, today's P&L
- **Outputs:** Row in `daily_desk.csv` (pre-market + EOD); updated `open_positions.csv`; updated `risk_drawdown.csv` and `capital_allocation.csv` (EOD); updated `watchlist.csv` if focus changes

**Launch prompt (pre-market):**

```
It's pre-market on [DATE]. Walk me through the desk routine.

Read Trading_OS.md Snapshot and current focus list. Then:
  1. Pull SPY/QQQ overnight + macro/news context via web search
  2. Mark key daily/4h levels for core + thematic focus tickers
  3. Review open Trading Book positions and overnight gap exposure
  4. Check active Strategic Allocation cycles — any exit triggers approaching?
  5. Identify 0-3 actionable Trading Book ideas with trigger/invalidation/target
  6. Recommend daily posture: Aggressive / Selective / Defensive / No-Trade
  7. State what NOT to trade today

Append row to daily_desk.csv.
```

**Launch prompt (EOD):**

```
End of day on [DATE]. Walk me through EOD reconciliation.

I'll tell you what happened today. Then:
  1. Update open_positions.csv with current exposure and unrealized P&L
  2. Update risk_drawdown.csv with EOD equity
  3. Update capital_allocation.csv with current book allocations
  4. Capture emotional state and what worked / didn't
  5. Prep tomorrow's levels for focus tickers
  6. Flag any guard rail status changes

Mark daily_desk.csv EOD complete.
```

### 2.4 Pre-Trade Tickets

- **Cadence:** Whenever a Trading Book trade idea is being evaluated
- **Purpose:** Pressure-test a Trading Book idea against the framework before capital is committed
- **Inputs:** Current Snapshot; current focus list and posture; the proposed trade idea
- **Outputs:** Row in `pre_trade_tickets.csv` (Take / Pass / Wait); if Take, into `open_positions.csv` + `trade_actions.csv`; new campaign file in `campaigns/` if opens a new campaign

**Launch prompt:**

```
I see a Trading Book opportunity on [TICKER]. Pressure-test it.

Read Trading_OS.md Snapshot and current focus list / posture. Walk me through:
  1. Universe tier (Core / Thematic / outside-universe requiring exception)
  2. Setup classification (A/B/C/D)
  3. Higher timeframe structure (weekly/daily/4h alignment)
  4. Market regime check (SPY/QQQ context, sector alignment)
  5. Technical thesis (specific level/structure) AND narrative thesis (specific catalyst)
  6. Trigger / invalidation / target zone
  7. Risk/reward
  8. Options contract selection (DTE, strike, delta, premium); liquidity check
  9. Sizing per current tier; max premium = max risk
  10. Profit-taking plan with specific trim levels
  11. Overnight plan
  12. Emotional state check
  13. Setup grade (pre-trade A/B/C, or below = don't take)
  14. Rule exceptions, if any
  15. Decision: Take / Pass / Wait

If Take, append ticket to pre_trade_tickets.csv and either open new
campaign file or link to existing Campaign ID.

Reject marginal setups — 0 trades beats a B-grade trade during the Sprint.
Watch for emotional language; pause if you detect it.
```

### 2.5 Long-Term Positioning

- **Cadence:** Event-triggered — when a Strategic Allocation cycle opportunity emerges OR when an active cycle approaches exit. Realistically 2-6 times per year.
- **Purpose:** Pressure-test Strategic Allocation entries, manage tranching, identify exits. Slow, macro-deliberate context — not trading-day timeframe.
- **Inputs:** Current Snapshot; current Strategic Allocation status per asset; macro context (web search); the dislocation/inflection observation OR the active cycle's current state
- **Outputs:** New file in `strategic_allocations/` for new cycles (Plan section); tranche entries logged in cycle file + `trade_actions.csv`; for exits, cycle file Review section filled, capital returned to BIL accounting; updated Snapshot

**Launch prompt:**

```
Long-Term Positioning chat — [ASSET / topic].

Context: [new opportunity (dislocation/inflection) OR active cycle management OR exit decision]

Read Trading_OS.md § 19 + relevant cycle file (if any) + Snapshot. Then:

  IF NEW OPPORTUNITY:
    1. Pull macro context (web search) for the asset's regime
    2. Verify trigger criteria per § 19 — major weekly/monthly structural setup, confirmation candle, defensible thesis
    3. Reject if conditions don't meet bar; do NOT manufacture a setup
    4. If valid: define cycle thesis, target allocation, tranching schedule
    5. Create cycle file in strategic_allocations/

  IF ACTIVE CYCLE TRANCHE:
    1. Verify minimum time gate met (1-2 weeks since last tranche)
    2. Verify structural trigger for this tranche level
    3. Execute and log tranche in cycle file + trade_actions.csv

  IF EXIT TRIGGER:
    1. Verify which exit trigger fired per § 19
    2. Plan full exit over 1-3 days
    3. Fill Review section in cycle file
    4. Return capital to BIL accounting; update Snapshot

This is the slow chat. Do NOT make decisions in 5 minutes. The market gives
these opportunities 2-6 times per year; the framework's job is to NOT chase
fake ones.
```

### 2.6 Live Position Management

- **Cadence:** During market hours when an active Trading Book position hits a decision point
- **Purpose:** Manage open Trading Book positions in real time without bleeding into Pre-Trade Tickets (entry) or Post-Trade Journal (post-close)
- **Inputs:** Campaign file; current `open_positions.csv` row; current price action and event
- **Outputs:** Row in `trade_actions.csv`; updated `open_positions.csv`; campaign file Tracking section updated; if rule violation, row in `mistake_log.csv`

**Launch prompt:**

```
I have an active Trading Book position on [TICKER] hitting a decision point.

Read the campaign file and current open_positions.csv row. Then:
  1. State the current campaign thesis and where we are vs plan
  2. Identify which trigger we're at (structural target, % gain trim, account-% threshold, invalidation, news)
  3. Apply profit-taking hierarchy: structural controls timing, account-% triggers mandatory
  4. Recommend specific action: trim X / add X / roll / exit / hold / hedge
  5. Capture emotional state — if I'm reaching for a justification, call it
  6. Document action and reasoning

Append to trade_actions.csv. Update open_positions.csv and campaign file.

Do NOT rubber-stamp emotional adds or "let it run" without checking thresholds.
```

### 2.7 Post-Trade Journal

- **Cadence:** After every closed Trading Book trade or fully closed campaign
- **Purpose:** Document the full lifecycle, grade all four dimensions, extract lessons
- **Inputs:** Campaign file or trade history; original ticket; all `trade_actions.csv` rows for the campaign
- **Outputs:** Row in `trade_log.csv` with all four grades + Trade Quality + A-Trade; row(s) in `mistake_log.csv` for violations; campaign file Review section filled; campaign Closed if fully exited

**Launch prompt:**

```
I closed a Trading Book trade or campaign. Walk me through the post-trade journal.

Read Trading_OS.md § 23 (grading scale) + the campaign file + the original ticket. Then:
  1. Original thesis (technical + narrative) — was it valid in hindsight?
  2. Entry / exits / size / instrument / P&L / R-multiple
  3. Process compliance: ticket complete? journal timely? rule violations?
  4. Risk discipline: invalidation respected? sizing per plan?
  5. Profit protection: +0.5/+1.0/+1.5% account thresholds honored?
  6. Management decisions: each add/trim/roll/exit reasoned?
  7. Emotional state through the trade
  8. Four grades: Setup, Execution, Management, Process
  9. Trade Quality (lowest of four) and A-Trade Y/N
  10. Lessons — flag anything for framework feedback

Append to trade_log.csv. Log violations in mistake_log.csv. Fill campaign
Review section. Mark campaign Closed if fully exited.

A losing trade can be an A. A winning trade can be a C or worse.
```

### 2.8 Emergency Reset

- **Cadence:** Triggered by guard rail (mandatory) OR trader-initiated (discretionary). See `Trading_OS.md` § 25.
- **Purpose:** Stop the bleeding. Force a pause, postmortem, and controlled return.
- **Inputs:** What triggered the reset; current open positions; recent trade history; emotional state
- **Outputs:** Documented postmortem; entries in `mistake_log.csv`; Snapshot updated to Reset state; Sprint file Tracking updated; if framework change needed, `intervention_log.csv`

**Launch prompt:**

```
Emergency Reset. Pause everything.

Read Trading_OS.md § 25. Then:
  1. State which trigger fired (or that this is discretionary)
  2. Review every open Trading Book position — close anything not defensible
  3. Strategic Allocation positions NOT automatically affected (their own exit rules)
  4. Stop all new entries
  5. Walk me through the postmortem: what happened, root cause, prevention rule
  6. Set return parameters: 24hr cooling off, Selective posture, lower sizing tier
  7. Log everything in mistake_log.csv and update Snapshot
  8. If framework change is warranted, draft it for the next Framework chat

Do NOT let me talk you out of any step. The point of this chat is that the
in-the-moment trader's judgment is the thing being overridden.
```

---

## 3. Promotion Paths

| Output type | Promotes to | Why |
|---|---|---|
| Pre-market plan | `daily_desk.csv`; `watchlist.csv` updated | Daily state of play |
| EOD reconciliation | `daily_desk.csv` EOD complete; `risk_drawdown.csv`; `capital_allocation.csv`; `open_positions.csv` | Ground truth at end of session |
| New Trading Book ticket (Take) | `pre_trade_tickets.csv`; new campaign file if applicable | Pre-entry documentation |
| Pass / Wait | `watchlist.csv` resolution column | Discipline of recording even non-trades |
| Strategic Allocation cycle plan | New file in `strategic_allocations/` | Cycle ownership |
| Strategic Allocation tranche | `trade_actions.csv` + cycle file Tracking | Tranche-by-tranche audit trail |
| Strategic Allocation exit | Cycle file Review section + capital_allocation.csv update | Cycle close |
| Position event (trim/add/roll/exit) | `trade_actions.csv`; `open_positions.csv`; campaign/cycle file | Live action log |
| Closed Trading Book trade | `trade_log.csv` with four grades; campaign Review | Trade database |
| Rule violation | `mistake_log.csv`; Process Grade capped at C | Mistakes don't disappear |
| Weekly aggregation | `weekly_review.csv`; Snapshot updated; `capital_allocation.csv` | Weekly state |
| Sprint review | Sprint Review filled; new Sprint file; Snapshot updated | Sprint accountability |
| Quest review | Quest Review filled; new Quest file if Quest closes | Quest accountability |
| New hypothesis | `hypotheses_register.csv` | Falsifiable claim tracking |
| Resolved hypothesis | `hypotheses_register.csv` updated; framework change if warranted | Learning |
| Framework change | `Trading_OS.md` + Evolution Log row + `intervention_log.csv` row | Deliberate change |
| Emergency Reset postmortem | `mistake_log.csv`; Snapshot updated; possible `intervention_log.csv` | Reset is logged |

---

## 4. Chat Hygiene

### Naming convention

`[Chat Type] — [Date or scope]`

Examples:
- Daily Trading Desk — 2026-05-25
- Pre-Trade Ticket — NVDA breakout 2026-05-27
- Long-Term Positioning — GLD dislocation cycle planning 2026-08-15
- Post-Trade Journal — NVDA campaign 2026-06-03
- Weekly Review — 2026-05-31
- Live Position Management — TSLA add decision 2026-05-29
- Emergency Reset — 2026-06-02
- Framework — Sprint 1 mid-review

### Closing a chat

Before ending any chat, the closing summary must list:

- Decisions made
- Files updated (and what changed)
- Open questions / parking-lot items
- Next chat type and approximate time

### When chats should split vs continue

- **Continue:** same scope, same trading day, same campaign/cycle
- **Split:** new day, new campaign/cycle, new ticker, or moving from one chat type to another
- **Always split:** when moving from execution-level (Daily Desk / Tickets / Live Mgmt / Long-Term Positioning entries) to review-level (Weekly Review, Post-Trade Journal, Framework)

### Default behaviors expected from Claude in any chat

- Read `Trading_OS.md` Snapshot on initialization
- Push back when data contradicts narrative; don't soften reads
- Surface guard rail flags proactively
- Distinguish "what the rules say" from "what your gut says"
- Update files directly via filesystem
- Detect emotional language (FOMO, frustration, revenge, euphoria) and pause
- Reject marginal setups during Sprint phase — 0 trades beats a B-grade trade
- For Strategic Allocation: refuse to manufacture a cycle trigger if conditions aren't met
- Never reinterpret rules to make a marginal trade fit
- **Maintain the Trading Google Calendar as the time-bound layer of the plan:** during Weekly Review, add earnings/FOMC/macro events for the week ahead; during Sprint Review, ensure next Sprint's calendar events exist; during cycle entries, add follow-up tranche reminders if relevant

---

## 5. Calendar Maintenance Convention

The **Trading** Google Calendar holds the time-bound layer of the OS.

Calendar ID: `43fc9b5c4b733683b4d2c81f5b9bc675707df951327f22985bc485acd64e6f22@group.calendar.google.com`
Time zone: America/New_York

### Event types

| Type | Format | When created |
|---|---|---|
| Pre-Market Daily Desk | Timed 8:00am ET, recurring Mon-Fri, popup at start | One-time setup |
| Market Open | Timed 9:29am ET, recurring Mon-Fri, popup 15 min before | One-time setup |
| EOD Recon & Daily Journal | Timed 4:00pm ET, recurring Mon-Fri, popup at start | One-time setup |
| Weekly Review | Timed Sun 7:00pm ET, recurring, popup 60 min + 24 hr before | One-time setup |
| Sprint Start | All-day on Sprint start date | At Sprint kickoff |
| Sprint Mid-Review | Timed evening at end of week 2, popup 24 hr before | At Sprint kickoff |
| Sprint End / Review | Timed evening on Sprint close date, popup 24 hr + 7 days before | At Sprint kickoff |
| Quest Time Guard | Timed evening on Quest review date, popup 24 hr + 7 days before | At Quest open |
| Macro events (FOMC, CPI, NFP, earnings) | Timed on event date, popup as appropriate | Added during Weekly Review for the week ahead |
| Watch [TICKER] [LEVEL] | All-day on the day(s) the level is being watched | During Daily Desk; describes specific trigger conditions in event description |
| Strategic Allocation cycle trigger watch | All-day; created when an asset shows pre-trigger conditions | During Long-Term Positioning chat |

### Naming convention with emoji prefixes for visual scanning

- 📋 Pre-Market Daily Desk
- 🔔 Market Open
- 🏁 EOD Recon & Daily Journal
- 📊 Weekly Review
- 🎯 Sprint / Quest milestones
- 🌐 Macro events (FOMC, CPI, NFP, earnings)
- 👀 Watch [TICKER] [LEVEL]
- 🚨 Strategic Allocation cycle trigger watch

### Macro events to add during Weekly Review

Each Weekly Review, scan the upcoming week and add events to the Trading calendar for:

- FOMC meeting days and announcement times
- CPI, PPI, PCE, NFP release dates (8:30am ET typically)
- Earnings dates for any focus list ticker that has earnings during the week
- Major Treasury auctions if relevant
- Any pre-known geopolitical events with potential market impact

These events should have descriptions noting the expected impact and any pre-defined action (e.g., "close positions before close on FOMC day" if that's the rule).

### Why timed events for routines (not all-day)

Unlike Cycling which uses all-day events for workouts (variable daily schedule), trading routines are anchored to market hours. Pre-market starts at a specific time; close happens at a specific time; the weekly cadence has specific anchor times. Timed events match the actual structure.

### Why the EOD reminder is at 4:00pm not later

Close discipline is highest-leverage immediately after the close. Allowing journals to slip toward bedtime invites them being skipped. 4:00pm popup catches the moment when emotional residue is freshest and details are most accurate.

The Process Grade rule (§ 23) caps at F for journals missed beyond 24 hours. The calendar event makes the 24-hour clock visible.

### Updating the calendar when framework changes

When Sprint dates change (extension, restructure), update the Sprint-related events. When Quest closes and next Quest opens, archive old Quest events and create new ones. When chat types or routines change in `Chats_Framework.md`, update the recurring event descriptions to match.

The calendar reflects the framework, not the other way around. If the calendar and the framework drift apart, the calendar is wrong; update it.
