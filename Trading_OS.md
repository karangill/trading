# KSG Trading Operating System

**Operational Instructions & Framework — v0.8**
**Last updated:** 2026-05-25

Source-of-truth document for trading philosophy, setups, sizing, risk rules, grading, and review process. Updated by Claude directly via filesystem MCP whenever a chat formally promotes a change. Plain markdown so it's diff-friendly, portable, and editable in any tool.

---

## Table of Contents

1. Mission & Long-Term Vision
2. Current State Snapshot
3. Progression Structure (Mission → Quest → Sprint)
4. The Two Trade Categories
5. The Three Books (organized by intent)
6. The Decision Tree
7. Core Philosophy
8. Approved Universe
9. HTF Range Definition
10. Trade Qualification Rule
11. Timeframe Hierarchy
12. Instrument Selection
13. Sizing & Risk Rules
14. Capital Allocation Across Books
15. Scaling, Adds, Compounding, and Rolls
16. Profit-Taking Rules (Trading Book)
17. Invalidation & Exit Rules
18. Overnight Risk Rules
19. Pre-Trade Ticket
20. Campaign Definition
21. Strategic Allocation Book Mechanics
22. Trading Book Mechanics
23. Asymmetric Bet Book (Deferred)
24. Daily Routine
25. Weekly Routine
26. Post-Trade Review & Grading
27. Loss Limits & Drawdown Circuit Breakers
28. Emergency Reset
29. Account Architecture (Brokerage + 401k)
30. Source Material Map
31. Framework Evolution Log
32. Glossary

---

## 1. Mission & Long-Term Vision

### Mission

Develop trading into a major wealth-compounding pillar — resolve whether systematic discretionary edge produces 7+ figure annual income, and ultimately whether trading can carry the account toward 8 figures over the next 2-3 years.

### Near-term financial context

Current BX income that trading would need to approach or replace by late summer 2026: **$52k/month**. Starting capital base: **$373,622.84** (brokerage) + **$117,000** (Solo 401k, out of scope for Sprint 1-2).

### The two goals

1. **Long-term wealth accumulation** — durable compounding via Strategic Accumulation
2. **Rapid capital multiplication** — active returns via Trading Book Catalyst and Single-Range plays

### Goal vs outcome

The goal is **a process that demonstrably produces edge under disciplined execution**. Dollar P&L is the downstream evidence, not the goal itself. A profitable trading week with rule violations is a failed week. A break-even trading week with full process compliance is a passing week during Sprint phases.

---

## 2. Current State Snapshot

> Updated weekly during Weekly Review and on demand after any material event. The single artifact any chat pulls on initialization to know "where we are right now."

| Field | Value | Notes |
|---|---|---|
| Snapshot date | 2026-05-24 (Weekly Review #1) | Run Mon 5/25 due to Memorial Day market closure |
| Brokerage account equity | $373,622.84 | IBKR confirmed; unchanged — no trades since v0.8 |
| 401k equity | $117,000 | Out of scope for Sprint 1-2; activate at Quest 2 close for Strategic Allocation only |
| Peak equity (brokerage) | $373,622.84 | — |
| Current drawdown % | 0.0% | — |
| Cash (liquid buffer) | 100% ($373,622.84) | BIL purchase slipped from Mon 5/25 (Memorial Day) to Tue 5/26 open |
| BIL (Strategic Allocation reserve) | 0% ($0) — PENDING | Execute $298,898 (80%) Tue 5/26 open; one-day slip documented, not a violation |
| Current Quest | Quest 1: First $25k Realized Month | Outcome-defined; review at 4 weeks |
| Current Sprint | Sprint 1: Execution Discipline | 2026-05-25 → ~2026-06-19 |
| Sprint week | Week 1 (Tue 2026-05-26 → Fri 2026-05-29) | First Daily Desk: Tue 2026-05-26 (Mon was Memorial Day) |
| Sizing tier (Trading Book) | Tier 1: Sprint start | 1.0% max premium per campaign; 0.50% standard |
| Daily posture | Selective | Per Weekly Review #1; Aggressive not allowed in Sprint 1 per Sprint file |
| **Trading Book** | | |
| Tactical focus (indices) | SPY, QQQ | Long on confirmed 1h bullish range + retrace; futures (MES/MNQ); target = new range high |
| Trend watchlist (situational quality, § 4 Flavor 3) | BABA, MSFT, NOW, EWZ, LMT | All at/reversing from daily/weekly bullish range lows; 1h/15m for entry timing; 60-180 DTE OTM calls |
| Thematic focus | (none) | DELL dropped — +16% rip on 5/22 with no PA structure for a long entry. Wait for actual setup. |
| Active campaigns | 0 | See `campaigns/` |
| Open premium | $0 / 0% account | — |
| **Strategic Allocation Book** | | |
| Direct-buy assets deployed | 0% | Max possible: 80% across cycles |
| Megacap accumulation options deployed | 0% | Tracked separately within SA book |
| Total in BIL reserve | $0 (pending; $298,898 Tue 5/26) | Treasury yield clock starts Tue |
| **SA candidates under evaluation** | IBIT, ETHA | Weekly compression / bullish reversal forming; watching for 1h bullish range continuations as potential first-tranche triggers. Cycle file in `strategic_allocations/` required BEFORE first sub-tranche. |
| **Asymmetric Bet Book** | | |
| Status | Deferred until Sprint 3+ | See § 23 |
| **Other** | | |
| Pending tickets | 0 | — |
| Trades logged (Sprint 1) | 0 | Tier 2 unlocks at 10 |
| Process compliance | — | Computed once first trade logged |
| A-Trade % | — | — |
| Rule violations (sprint) | 0 | — |
| Open hypotheses | H001, H002 | See `hypotheses_register.csv` |
| Guard rail status | GREEN | No P&L data yet |
| Most recent trade | — | — |
| Emergency Reset state | None | — |

### Strategic Allocation Status by Asset

| Asset | Status | Cycle ID | Sub-Tranche # | Target % | Deployed % | Avg Cost | Current Price | Unrealized P&L | Nearest Exit Trigger |
|---|---|---|---|---|---|---|---|---|---|
| SPY (direct) | In BIL (pending Tue) | — | — | 22% (max) | 0% | — | $745.64 (5/22 close) | — | — |
| QQQ (direct) | In BIL (pending Tue) | — | — | 18% (max) | 0% | — | $717.54 (5/22 close) | — | — |
| GLD (direct) | In BIL (pending Tue) | — | — | 25% (max) | 0% | — | ~$4,523 (5/22) | — | — |
| IBIT (direct) | **SA candidate — watching** | — | — | 10% (max) | 0% | — | BTC ~$77K | — | Trigger watch: 1h bullish range continuation; cycle file required before entry |
| ETHA (direct) | **SA candidate — watching** | — | — | 5% (max) | 0% | — | — | — | Trigger watch: 1h bullish range continuation; cycle file required before entry |
| MSFT (via options) | Not active | — | — | n/a | 0% | — | — | — | — |
| META (via options) | Not active | — | — | n/a | 0% | — | — | — | — |
| NVDA (via options) | Not active | — | — | n/a | 0% | — | — | — | — |
| AMZN (via options) | Not active | — | — | n/a | 0% | — | — | — | — |

---

## 3. Progression Structure (Mission → Quest → Sprint)

Three nested levels plus daily/weekly rhythm.

### Mission

Decade-level "why." Defined in § 1.

### Quest

Outcome-defined financial milestone arc. Each Quest has its own file in `quests/quest_N_short-name.md` following Plan → Tracking → Review → Handoff.

| Quest | Success criteria | Status |
|---|---|---|
| Quest 1: First $25k Realized Month | ≥$25k realized P&L in a calendar month at ≥90% process compliance; review at 4 weeks regardless | Active |
| Quest 2: Approach BX Replacement | Two consecutive months with ≥$40k realized P&L | Planned |
| Quest 3: BX Replaced | Three consecutive months with ≥$52k realized P&L, drawdown contained | Planned |
| Quest 4: 8-Figure Trajectory | TBD post-Quest 3 | Planned |

### Sprint

3-6 week time-boxed framework-iteration block within a Quest. Each Sprint has its own file in `sprints/sprint_N_short-name.md`.

| Sprint | Parent Quest | Framework version | Status |
|---|---|---|---|
| Sprint 1: Execution Discipline | Quest 1 | v0.6 | Active 2026-05-25 → ~2026-06-19 |
| Sprint 2: Calibration | Quest 1 (if needed) | v0.7 | Planned |

### Week / Day

Tactical execution. Weekly Review Sundays (§ 25); Daily Desk each market day (§ 24).

---

## 4. The Unified Framework — One Trade Type, Four Flavors

Every active trade in the system is the same underlying skill: **identify a structural setup, classify by hold intent and underlying behavior, select the matched instrument, manage to structural exit.**

Four flavors of this trade, distinguished by hold intent (which drives instrument choice) and underlying universe (which drives realistic upside):

### Flavor 1: Strategic Allocation

- **Hold intent:** Indefinite. Held until HTF structural floor breaks.
- **Universe:** SPY, QQQ, GLD, IBIT (BTC), ETHA (ETH). Restricted to non-zero-risk macro assets where indefinite hold is safe.
- **Instrument:** Direct shares.
- **Why shares:** No DTE forcing exit. Indefinite hold capability matches macro cycle timeframes (months to years). Tax efficiency on long holds.
- **Entry:** 3 sub-tranches following 1H structural confirmations.
- **Per-asset caps:** SPY 22%, QQQ 18%, GLD 25%, IBIT 10%, ETHA 5%. Max 80% total deployed.
- **Management:** Migrating protective stop based on most recent 1H structural floor.
- **Exit:** Weekly structural break, exhaustion signals, or macro regime change.

### Flavor 2: Moonshot

- **Hold intent:** Multi-month. Held until catalyst resolves or thesis breaks.
- **Universe:** Sub-$100 (preferably sub-$50) names with capacity for outlier moves (3-30x). Identifiable binary catalyst window. Multi-year base or compression.
- **Instrument:** 6-12 month moderately OTM options or LEAPS.
- **Why long-dated OTM options:** Captures convexity from large underlying moves with bounded risk (premium = max loss). Avoids gap risk inherent in volatile names. Cheap contract pricing allows meaningful upside on small capital.
- **Sizing:** Profit-funded — see § 13 for full mechanism.
- **Management:** Patience. No mid-trade reclassification. Trim ladder at 3x/5x/10x.
- **Exit:** Catalyst resolution, thesis break, or DTE forcing roll/exit at 90 days remaining.

### Flavor 3: Trend

- **Hold intent:** Weeks to a few months. Held until structural floor breaks or target hit.
- **Universe:** Megacap or quality names in confirmed multi-month trends. MSFT, META, NVDA, AMZN, NOW, plus situational quality names.
- **Instrument:** 60-180 DTE slightly OTM options.
- **Why medium-DTE options:** Matches expected hold timeframe. Theta drag tolerable. Slightly OTM gives good delta-per-dollar without paying too much for time.
- **Sizing:** 1.5-2.5% per position (full tier max for A-grade setups).
- **Management:** Migrating protective stop. Profit-taking ladder at structural levels.
- **Exit:** Structural floor break, target reached, DTE forcing decision.

### Flavor 4: Tactical

- **Hold intent:** Hours to weeks. Held until target hit or invalidation.
- **Universe:** Any liquid name with active flow + clear near-term level. Brando-style trades, intraday range plays, short-term continuations.
- **Instrument:** 3-21 DTE slightly OTM or ATM options. Or futures for index range plays.
- **Why short-dated:** Matches expected hold. Premium is cheap because of short DTE. Full exit at target captures the move without theta penalty.
- **Sizing:** 0.5-1.5% per position. Futures at 0.5-0.75% account risk.
- **Management:** Fast exits. Full exit at previous high/low (for range plays) or near-term level extension (for continuation). Max 1 roll if continuation visible.
- **Exit:** Target hit (full exit), invalidation, time stop, or roll exhausted.

### Same skill, different parameters

All four flavors use the same chart-reading skill: identify structural break or breakdown, define invalidation, define target, enter on confirmation. What differs is timeframe of analysis, underlying selection, instrument matching, and management discipline.

### Classification binds management

**Classification at pre-trade ticket is binding for the duration of the trade.** A trade entered as Tactical must be managed as Tactical (fast exits, target-or-invalidation). A trade entered as Moonshot must be managed as Moonshot (multi-month patience, trim ladder). 

**Reclassifying mid-trade is a Critical-severity rule violation.** The most common failure mode is "I entered as Tactical, it's working so well, I'll let it run as a Trend." This rationalization is exactly what produces blown-up trades. If you want exposure beyond your original classification's hold timeframe, take a separate trade with appropriate sizing in the new flavor — don't morph the existing position.

Trades that don't fit any flavor are not trades.

---

## 5. The Three Books (organized by intent)

Capital is organized into three books by **investment intent**, not by instrument. Each book contains positions of various instruments matched to the intent.

| Book | Intent | Universe | Instruments | Active management |
|---|---|---|---|---|
| **Strategic Allocation Book** | Ride HTF moves from cyclical range lows to range highs | SPY/QQQ/GLD/IBIT/ETHA + megacap names | Shares (direct-buy assets) + OTM Calls (megacap names) | 1H sub-tranching with migrating structural stop |
| **Trading Book** | Tactical returns from single-range plays and catalyst events | Core + Thematic | Futures (index range plays), Options (stocks, catalysts), Puts (shorts) | Active per-trade management |
| **Asymmetric Bet Book** | Multi-year LEAPS positions on thematic theses | Any single name with defensible thesis | LEAPS only | **Deferred until Sprint 3+** |

### Books work together — unified analysis, separate expression

The three books share the same chart-reading process. A structural read on any asset produces information that routes to whichever book matches the **intent** of the trade:

- HTF range bottom + multi-month thesis → Strategic Allocation Book
- LTF range trade + days-to-weeks thesis → Trading Book Single-Range
- Consolidation + catalyst → Trading Book Catalyst
- Multi-year thematic thesis → Asymmetric Bet Book (when activated)

The same chart can produce different trades in different books at different times. The decision tree (§ 6) routes opportunities mechanically.

---

## 6. The Decision Tree

Every opportunity routes through four questions:

### Question 1: Is this a structural play?

**Yes** → continue to Question 2
**No** → continue to Question 3

### Question 2: Is this at the HTF range low (long) or HTF range high (short)?

**Yes** → Strategic Accumulation play in Strategic Allocation Book
**No** → Trading Book Single-Range play

### Question 3: Is this an Active Flow Tactical (Setup E) opportunity?

**Yes (active multi-day flow + near-term level + regime alignment)** → Setup E in Trading Book
**No** → continue to Question 4

### Question 4: Is this consolidation + identifiable catalyst with IV compression?

**Yes** → Catalyst play in Trading Book (rare, small subcategory)
**No** → Not a trade

### Instrument selection (after categorization)

| Trade type | Asset | Instrument |
|---|---|---|
| Strategic Accumulation, long | SPY, QQQ, GLD, IBIT, ETHA | Direct shares, 3 sub-tranches |
| Strategic Accumulation, long | MSFT, META, NVDA, AMZN | One full-size OTM call per accumulation event (no scaling) |
| Trading Book Single-Range, long | SPY, QQQ, GLD, IBIT, ETHA | Futures (MES/MNQ/ES/NQ or equivalent) |
| Trading Book Single-Range, long | Individual stock | OTM calls |
| Trading Book Single-Range, short | SPY, QQQ | Futures (or puts) |
| Trading Book Single-Range, short | Individual stock | OTM puts |
| Setup E (E1 or E2) | Active flow momentum name | 3-7 DTE weekly calls (bullish) or puts (bearish) |
| Catalyst play | Any | Options only (calls or puts), 7-30 DTE |

The decision tree is mechanical. Run it on every opportunity.

---

## 7. Core Philosophy

The edge is not prediction alone.

**Structural opportunity + market regime alignment + disciplined instrument selection + predefined risk + professional management.**

The operating system prioritizes:

- Daily / weekly / 4h / 1h market structure
- SPY / SPX / QQQ regime
- Fundamental and narrative alignment
- Key levels and clean invalidation
- Asymmetric risk/reward
- Bounded capital commitment (options for gap-risk-prone names)
- Cycle-based macro allocation (Strategic Allocation Book)
- Strict gap-risk management
- Profit protection
- Narrow watchlist focus
- Detailed journaling and review

**Unified chart reading across books:** all books read charts the same way. What differs is timeframe context and instrument expression.

**Capital efficiency principle:** options provide bounded *capital commitment* in addition to bounded risk. A 1% premium position controls notional exposure equivalent to a much larger share position, while tying up only 1% of capital. This lets the framework be opportunistic across multiple simultaneous setups without ever being capital-constrained.

---

## 8. Approved Universe

### Strategic Allocation Universe

**Direct-buy (shares):**
- SPY / SPX
- QQQ
- GLD
- IBIT (BTC exposure)
- ETHA (ETH exposure)

**Megacap via options (OTM calls only, no shares to avoid gap risk):**
- MSFT
- META
- NVDA
- AMZN

### Trading Book Universe

**Core Tier (default focus):**
- Indices: SPY / SPX, QQQ
- Megacaps: NVDA, TSLA, MSFT, META, AMZN, NOW, MSTR, BABA

**Thematic Tier (rotating, 0-3 names):**
Names from current themes that have structurally good setups developing. Updated at each Weekly Review. Examples:
- Quantum: QBTS, IONQ, RGTI
- Energy transition: BE, PLUG, FCEL
- Other thematic catalysts as they emerge

**Thematic-tier trade requirements:**
- Liquid options market — tight spreads, sufficient open interest at major strikes
- If options aren't liquid enough to enter and exit cleanly, the name is not tradeable

### Asymmetric Bet Universe

Deferred until Sprint 3+. When activated: any single name with defensible multi-year thesis.

### Active execution rule

Trading Book usually narrows to **1-2 indices + 1-3 core stocks + 0-3 thematic** as the week's focus list. Declared in Weekly Review and recorded in the Snapshot. Trades outside the focus list require documented exception in the ticket. More than one universe exception per week triggers a review.

---

## 9. HTF Range Definition

**Bullish HTF range low:** a low that took out a previous low and then made a new high above the prior high. This is the failed-breakdown / Wyckoff-spring pattern that establishes a new bullish range.

**Bearish HTF range high:** a high that took out a previous high and then made a new low below the prior low. This is the failed-breakout / Wyckoff-upthrust pattern that establishes a new bearish range.

For Strategic Accumulation purposes, "HTF" means **weekly minimum, ideally monthly.** The range must be visible on the weekly chart with the failed-breakdown / new-high structure clearly established.

For Trading Book Single-Range plays, "HTF" can mean **daily** — a daily-level range with the same failed-breakdown / new-high (or failed-breakout / new-low) structure.

The structural test:
- For Strategic Accumulation: did a low on the weekly take out a prior weekly low and then produce a higher high above prior weekly highs?
- For Trading Book Single-Range: did a low on the daily take out a prior daily low and then produce a higher high above prior daily highs?

If yes, the structural setup qualifies. If not, it's not a structural play in this framework.

---

## 10. Trade Qualification Rule

Every trade in every book must have **both** technical and narrative justification, captured explicitly in the Pre-Trade Ticket in separate fields.

If a trade has technical structure but no narrative, **wait**. If it has narrative but no technical structure, **wait**. Both, or no trade.

---

## 11. Timeframe Hierarchy

- **Monthly:** macro regime; Strategic Allocation cycle context
- **Weekly:** major regime, major support/resistance, primary Strategic Allocation timeframe
- **Daily:** primary Trading Book setup timeframe; secondary Strategic Allocation confirmation
- **4h / 1h:** Trading Book execution; Strategic Allocation entry mechanism within HTF range
- **15m / 5m:** entry timing only

**Core rule:** lower timeframes cannot create the trade. They only confirm or reject a higher-timeframe trade idea. LTF noise against an intact HTF thesis is not invalidation.

**Book-specific timeframe minimums:**

- **Strategic Allocation:** HTF setup on weekly minimum; 1H execution mechanism
- **Trading Book Single-Range:** HTF setup on daily minimum; 1H/4H/15m execution
- **Trading Book Catalyst:** consolidation visible on daily or weekly; catalyst event-dated

---

## 12. Instrument Selection

### Strategic Allocation — direct-buy assets

For SPY, QQQ, GLD, IBIT, ETHA: shares only. 3 sub-tranches across the accumulation cycle following 1H structural confirmations.

### Strategic Allocation — megacap names (via options)

For MSFT, META, NVDA, AMZN: OTM call options only (no shares — eliminates gap risk on single-name positions).

**Strike selection:**
- Slightly to moderately OTM (delta 0.30-0.50)
- Strike well below target so target reaches deep ITM
- Liquid strikes only

**DTE selection:**
- 1.5x the asset's typical retracement timeframe for a similar-magnitude move
- Typically 90-180 DTE for megacap multi-month moves
- LEAPS (365+ DTE) acceptable for very high-conviction multi-quarter theses

**Sizing:** one full-size position per accumulation event (no sub-tranching due to contract granularity at most tiers). Tier-max sizing for high-conviction structural setup with tight 1H invalidation.

**Why no sub-tranching on megacap options:** at $373k account / Tier 1, contract premiums of $1,500-3,000 prevent splitting into 3 meaningful sub-tranches. Single full-size entry is the honest answer. The framework's structural invalidation exit protects against full-premium loss — if 1H structure breaks, you exit at typically 25-40% loss on premium, not 100%.

### Trading Book — index range plays

For SPY/QQQ longs and shorts: futures (MES/MNQ for smaller positions, ES/NQ for larger).

**Why futures:**
- Capital-efficient leverage (Reg-T 2:1 on shares vs. high implicit leverage on futures)
- No theta decay (cleaner directional exposure than options for short-timeframe range plays)
- Reliable execution
- Single-range plays close within days to weeks, well before contract expiration

**Contract selection:** use whichever micro/mini/full-size contract gives you the desired risk allocation at the selected stop distance. No fixed mapping; calibrated per trade.

### Trading Book — individual stock range plays

For longs: OTM calls. For shorts: OTM puts.

**Strike selection:** slightly OTM (delta 0.30-0.45). DTE matched to expected resolution timeframe + buffer (typically 14-45 days).

### Trading Book — catalyst plays

Options only — calls for bullish catalysts, puts for bearish.

**Strike selection:** ATM or slightly OTM. DTE: catalyst date + small buffer (typically 7-30 days). IV expansion is part of the edge — favor entries when IV is in the lower 30% of recent range.

### Asymmetric Bet Book — LEAPS

Deferred. When activated: 1-2 year LEAPS at 0.30-0.50 delta, premium = max risk.

---

## 13. Sizing & Risk Rules

### Premium = max risk principle (options)

For options, premium deployed = max risk. There is no "planned stop %" — options can gap to near-zero on a single bad open. The position is sized assuming premium goes to zero. If that loss is acceptable, the trade is appropriately sized.

This does NOT mean "hold to zero regardless." Exit on structural invalidation per § 17. But the *sizing* decision is made assuming the worst case is realized.

### Futures sizing — stop-based

For futures (Trading Book index range plays):
- Risk per trade: 0.5-0.75% account (slightly more conservative than options tier max due to execution risk)
- Position size = (account × risk %) / (stop distance in points × contract multiplier)
- Stop placement: at structural invalidation + small buffer (3-5 ticks on indices) to avoid wick/spread-out

### Graduated sizing tiers (Trading Book)

Per-campaign sizing scales with demonstrated process and realized P&L. Larger size is earned, not claimed.

| Tier | Trigger | Max premium per campaign | Standard size |
|---|---|---|---|
| **Tier 1: Sprint start** | Sprint 1 active | 1.0% account | 0.50% |
| **Tier 2: Calibrated** | ≥10 trades logged AND ≥90% process compliance AND positive aggregate R | 1.5% | 0.75% |
| **Tier 3: Cruising** | ≥20 trades AND ≥90% process compliance AND account up >10% from start | 2.5% | 1.25% |
| **Tier 4: Full-conviction sizing** | ≥35 trades AND demonstrated edge holding AND account up >25% from start | 3.5% for A-grade with clear catalyst | 1.5% |
| **Tier 5+** | TBD post-Quest 1 | — | — |

**Drawdown drops you back a tier.** If circuit breakers in § 27 trigger, sizing tier drops to the previous tier until re-earned. Asymmetric — easier to lose tier than re-earn it.

### Sizing differentiation by flavor

Each flavor has distinct sizing logic appropriate to its risk/return profile:

**Strategic Allocation:** Per-asset caps as specified in § 4. 3 sub-tranches of ~33% each.

**Trend (options):** 1.5-2.5% account per position. Full tier max for A-grade setups with tight 1H invalidation and quantifiable target.

**Tactical (options):** 0.5-1.5% account per position. Higher frequency, smaller per-trade size. Futures at 0.5-0.75% account risk.

**Moonshot (profit-funded sizing) — the wealth-creation mechanism:**

Moonshot is the only flavor where sizing scales with demonstrated performance rather than fixed % of account. This mirrors the Brando-style approach of grinding small profits then deploying earned capital into high-conviction asymmetric bets.

**Locked until edge demonstrated:**
- ≥ 10 closed trades AND
- ≥ 90% process compliance AND
- Account up ≥ 5% from year-start

Before these gates are cleared, Moonshot Book is paused. No Moonshot positions allowed.

**Once unlocked:**
- Single Moonshot max premium: 30-40% of YTD realized profits
- Total Moonshot capital deployed at any time: max 50% of YTD realized profits
- Maximum simultaneous Moonshot positions: 3

**Drawdown protection:**
- If YTD realized P&L goes negative, Moonshot Book pauses until back to break-even
- This guarantees Moonshots are always funded from earned profits, never from core capital

**Annual reset:**
- Each calendar year starts fresh. YTD profit counter resets January 1.
- Edge-demonstration gates must be cleared again in Q1 of each new year (note: this is asymmetric — reaching 10 trades + 5% should happen quickly if the framework is working)

**The mechanism in practice:**

Example with $373k starting account:

- Q1: Tactical + Trend grinding builds $25k realized profit (account at $398k)
- Edge gates cleared (10+ trades, 90%+ compliance, account up 6.7%)
- Moonshot Book unlocks
- First Moonshot allowable: 30-40% of $25k = $7-10k premium
- Take a Moonshot at $8k premium on a sub-$50 name with binary catalyst (e.g., biotech Phase 3 readout, BTC-correlated name at major support)
- If it zeros: lose $8k, account at $390k, still up from start. Resume grinding.
- If it hits 10x: gain $80k, account at $478k, realized profit now $105k
- Next Moonshot allowable: 30-40% of $105k = $32-42k premium. Materially larger bet, but still funded entirely from earned capital.

The base account is always protected. Bets scale with demonstrated success. This is the structured path to outsized returns without catastrophic risk.

**Why this works:**

- Mathematically: produces convexity via Moonshot multipliers (10-30x on premium) while bounding loss to already-earned money
- Psychologically: removes the trader-mind temptation to oversize early. Big bets are *earned*, not claimed.
- Operationally: H1 is necessarily conservative (small profits = small Moonshots). H2 can be more aggressive (accumulated profits = larger bets). This naturally enforces "prove edge first, then size up."

### Lotto sizing (legacy concept, mostly absorbed by Moonshot)

The lotto concept from earlier versions is mostly absorbed by Moonshot Book. A few specific exceptions remain for truly speculative trades:

- True lottos: 0.10-0.20% of account equity per lotto, drawn from realized profit pool
- Multiple simultaneous lottos: max 0.50% total
- These are distinct from Moonshots because they lack the structural setup + catalyst window + capacity-for-outlier-move qualification
- Most "lotto" instincts are either disciplined into Moonshot trades or skipped

**Excluded from any sizing tier:**
- Earnings binary lottos (~70% zero rate, documented)
- FOMC/CPI/macro catalyst lottos (~40% zero rate, -12% mean)
- 0DTE options as a sizing vehicle (-3.1% mean across documented dataset)
- Any trade taken while account YTD is red (-4.4% mean vs +6.9% green)

These exclusions are evidence-based, not theoretical. Per the Brando research dataset of 844 trades.

---

## 14. Capital Allocation Across Books

Approximate target capital allocation when fully deployed across all activities:

| Use | Target % of account | Notes |
|---|---|---|
| Strategic Allocation positions (direct + megacap options) | Up to 80% when fully deployed across cycles | Realistic operating: 20-40% |
| Trading Book open premium | 8-12% maximum at any time | Sum of all open options + futures margin |
| Asymmetric Bet Book (when activated) | Up to 3% account | Premium across all LEAPS positions |
| BIL reserve | Remainder | Earning Treasury yield |

Practical reality during Sprint 1:
- Strategic Allocation: 0-20% (cycles unlikely to trigger in 4-week window)
- Trading Book: 3-8% open premium
- BIL: 70-95%

The framework lets you be opportunistic across multiple simultaneous setups without being capital-constrained. Every dollar not in an active position is earning Treasury yield.

---

## 15. Scaling, Adds, Compounding, and Rolls

Three distinct concepts.

### Compounding (concept)

Using realized profit from a working campaign to extend exposure on the same thesis. The strategic principle.

### Rolling (mechanic)

Closing one options contract and opening another at adjusted strike/expiration to express the same thesis with refreshed time value. One way to implement compounding.

### Add (action)

Putting additional capital into an existing campaign — fresh (allocated capital within initial scale-in plan) or compounding (funded by realized profit).

### Scaling rules

**Trading Book:**
- Scale into confirmation, not weakness
- Do not average down short-dated options
- Add only if thesis strengthens AND total campaign risk remains within tier-allowed sizing
- Compounding adds only with realized profit

**Strategic Allocation — direct-buy:**
- 3 sub-tranches across the cycle following 1H structural confirmations
- See § 21 for full mechanics

**Strategic Allocation — megacap options:**
- One full-size entry per accumulation event (no scaling within an entry)
- Multiple separate accumulation events possible within the same cycle if structure presents repeatedly

**Asymmetric Bet:**
- Original entry + max 2 adds, each requiring 100%+ from prior entry AND objective structural inflection

---

## 16. Profit-Taking Rules (Trading Book)

### Hierarchy

1. **Structural triggers control timing.** Trims at planned technical levels (previous high for longs, previous low for shorts).
2. **Account-% triggers control mandatory protection** regardless of structure. Large Unrealized Gain Rule below.
3. **% gain triggers (options) are default cadence** and failsafe when structural levels are far.

When two triggers fire simultaneously, take the more conservative action.

### Options default trims

Used as default cadence when no structural target is at hand, AND as failsafe when structural levels are far and gain has gotten outsized:

- **+30-50% option gain:** trim 25-50%
- **+75-100%:** trim additional portion
- **+150-200%:** protect aggressively / consider runner only
- Runner allowed only if original capital or meaningful profit secured

### Large Unrealized Gain Rule

Expressed as % of account equity:

- **+0.5% account unrealized:** review protection (documented decision required)
- **+1.0% account unrealized:** mandatory partial profit OR documented hedge
- **+1.5% account unrealized:** cannot remain fully exposed without explicit documented reason

Failing to act at +1.0% or +1.5% without documentation is a Critical-severity rule violation.

### Trading Book Single-Range plays — full exit at target

Single-range plays exit fully at the previous high (longs) or previous low (shorts). No trimming, no runners — the trade is defined by the range. Once the opposite side is reached, the trade is complete.

If target is approaching expiration without being hit, time-stop applies: exit by DTE of 7-14 days regardless.

### Strategic Allocation profit-taking

See § 21 for full mechanics. Short version: no profit-taking during the trend; full exit on structural break or major exhaustion signal.

---

## 17. Invalidation & Exit Rules

**Default: exit on structural invalidation, regardless of premium remaining or P&L state. Hope isn't a strategy.**

### What counts as invalidation

Invalidation defined at the timeframe the trade was created on:

- Strategic Allocation: most recent successful 1H structural floor breaks
- Trading Book Single-Range: 1H/4H/15m range structure breaks
- Trading Book Catalyst: consolidation invalidated OR catalyst resolution unfavorable
- All trades: setup-specific invalidation defined in the original ticket

LTF price action against an intact HTF thesis is **not invalidation**.

### What invalidation requires

- Exit immediately (the position, not after watching for retrace)
- Document in `trade_actions.csv` with reason = "invalidation"
- Update campaign or cycle file Tracking section
- Campaign closes if fully exited

### Capped risk does NOT change this rule

Options have capped risk by construction. This does not justify holding through a broken thesis. Exit on invalidation, take the small loss.

### The "wait for retrace" trap

The instinct that "support broke but price may retrace to break-even" is rationalization, not strategy. Hope isn't a strategy. The framework default is: exit on invalidation, take the small loss.

### Futures stop placement

For futures trades, place hard stops at structural invalidation + small buffer (3-5 ticks on indices) to avoid wick/spread-out execution.

---

## 18. Overnight Risk Rules

Before holding overnight, the ticket (or campaign file mid-campaign) must answer:

1. Is there earnings?
2. Is there macro/event risk?
3. Is there geopolitical risk?
4. What is normal gap risk?
5. What is stress gap risk?
6. What is max dollar loss under stress gap?
7. **Is that loss acceptable? (Y/N)**
8. Would options express this better?

Question 7 must be answered explicitly Y/N. If N, position must be reduced or closed before close.

For options positions, overnight gap risk is bounded by premium — so question 4-7 are typically not concerns for options-only trades. They apply primarily to futures positions held overnight.

---

## 19. Pre-Trade Ticket

**No trade without a ticket. No exceptions.**

Any missing field is automatic Process Grade F. See § 26.

Tickets are created only for trades intended to execute. Passed/missed ideas tracked in `watchlist.csv` resolution column.

### Required fields

- Ticket ID
- Date / time
- Ticker
- Book (Strategic Allocation / Trading / Asymmetric Bet)
- Trade category (Structural / Setup E Active Flow / Catalyst)
- Trade subtype (Strategic Accumulation / Trading Book Single-Range / Setup E-E1 / Setup E-E2 / Catalyst)
- Universe tier (Core / Thematic / SA-Direct / SA-Megacap / Active Flow)
- Direction (Long / Short)
- Instrument (Shares / Futures / Calls / Puts / LEAPS)
- DTE bucket (0-7 / 7-14 / 14-30 / 30-60 / 60-180 / 180+)
- Flow context (Active multi-day flow / Single-session move / Pending binary event / Post-catalyst chop / Not applicable)
- Entry style if Setup E (Break / Retest)
- Roll number in campaign (0 / 1 / 2 — value 3 not permitted)
- Flow driver named (if Setup E): sector cycle / earnings cycle / related-asset spillover / macro tailwind / clean technical trend
- **Technical thesis** (specific level/structure)
- **Narrative thesis** (specific catalyst/macro/sector logic)
- Market regime (SPY/QQQ context)
- Entry trigger
- Entry price
- Invalidation (specific structural level)
- Target zone (previous high/low for single-range; HTF range high/low for SA; near-term level extension for Setup E; catalyst-driven for catalyst plays)
- Entry-to-invalidation distance ($ and %)
- Entry-to-target distance ($ and %)
- Implied R:R
- Reward / risk
- Position size
- Max planned loss $
- Max loss % account
- Option expiration / strike / DTE / delta / premium (if options)
- Futures contract (if futures)
- Liquidity OK? Y/N
- Profit plan (specific trim levels per setup type)
- Overnight plan
- Emotional state (Calm / Focused / Frustrated / FOMO / Revenge / Euphoric / Tired)
- Setup grade (pre-trade A / B / C; D or below = don't take)
- **Rule exceptions, if any**
- Sizing tier in effect
- Campaign ID (if joining existing campaign, else "new")
- Notes

---

## 20. Campaign Definition

A **campaign** is a sequence of one or more trades on the same ticker, same direction, expressing the same continuous thesis, sharing a single invalidation. Opens with the first entry. Closes when fully flat or invalidation triggers.

Campaign duration is irrelevant — a 20-minute single-range play and a 6-month Strategic Accumulation are both campaigns.

### When a new campaign starts

- Direction flips
- Thesis materially changes
- Invalidation moves to a structurally different level
- Position fully exited and re-initiated

### Campaign-level discipline

- Each campaign has a file in `campaigns/` named `campaign_YYYY-MM-DD_TICKER_short-name.md`
- File lifecycle: Plan → Tracking → Review → Handoff
- Trades within share Campaign ID in `trade_log.csv`, `trade_actions.csv`, `open_positions.csv`, `mistake_log.csv`

Strategic Accumulation cycles use the same campaign structure, tracked in `strategic_allocations/` rather than `campaigns/`.

---

## 21. Strategic Allocation Book Mechanics

The Strategic Allocation Book is the long-term wealth accumulation engine. It captures HTF moves from cyclical range lows to range highs.

### Core principle

Each asset cycles between two states:
- **Inactive** (default — capital in BIL earning yield, or simply not allocated)
- **Active accumulation** (cycle running — entries via 1H structural confirmations, held against migrating structural floor, exited on structural break)

### Universe and per-asset target allocations (direct-buy)

| Asset | Max allocation at full deployment | Rationale |
|---|---|---|
| SPY | 22% of account equity | Core US equity exposure |
| QQQ | 18% | Tech tilt |
| GLD | 25% | Elevated for current macro regime |
| IBIT (BTC) | 10% | Digital store of value |
| ETHA (ETH) | 5% | Smart-contract platform exposure |
| **Direct-buy total max** | **80%** | Practical only at major cross-asset reset events |

### Megacap accumulation via options

For MSFT, META, NVDA, AMZN: no fixed per-asset cap. Sized per Trading Book tier rules because risk is bounded by premium.

Megacap accumulation occurs when a megacap shows an HTF range low (weekly+ scale) with defensible thesis. Position is one full-size OTM call, sized at tier max.

### Macro qualification (precondition)

Before attempting accumulation in any asset, document a **defensible macro reason** in the cycle file. Any of the following qualify:

- Major dislocation event with macro catalyst identified
- Asset at a major prior weekly/monthly support level (HTF range low per § 9)
- Weekly bottoming structure forming (higher low confirmed)
- Macro thesis suggests mispricing and mean reversion
- Trend resumption: asset consolidated above major prior level, breaking higher with confirmation

Macro qualification is the gate to start looking, not the trigger to enter. The structural mechanism (1H structural exits) is what actually protects against bad cycles.

### Entry mechanism — direct-buy assets (3 sub-tranches)

When macro is qualified and 1H structural range presents within the HTF context:

1. Identify the range: high, low, fib retracement zones, structural invalidation
2. Plan 3 sub-tranches at structural moments:
   - Sub-tranche 1: First 1H structural confirmation
   - Sub-tranche 2: Higher low confirmed OR continuation pullback
   - Sub-tranche 3: Further confirmation / continuation breakout
3. Total deployment per cycle = target allocation, split equally across 3 sub-tranches (~33% each)

### Entry mechanism — megacap via options (full-size single entry)

For MSFT, META, NVDA, AMZN: enter full-size OTM call on the highest-probability 1H structural confirmation. No sub-tranching due to contract granularity.

The protective stop is the 1H structural invalidation. If structure breaks, exit at typically 25-40% premium loss — not 100%. The framework's structural discipline contains the risk even on full-size single entries.

Multiple separate accumulation events can occur in the same cycle if 1H structure presents repeatedly. Each is a new ticket and a new full-size position.

### Position management — migrating protective stop

**There is no graduation period.** The position is always one Strategic Allocation position with a single protective stop. The stop migrates upward with successful accumulation.

- **Direct-buy:** stop is the most recent successful 1H structural floor across all sub-tranches deployed
- **Megacap options:** stop is the 1H structural invalidation of the most recent successful entry

The position becomes increasingly "risk-free" as accumulation progresses at higher prices.

### What doesn't trigger management actions

- 1H wiggles not breaking the most recent successful structural floor
- 4H bearish patterns not breaking weekly support
- News-driven intraday volatility not breaking structure
- Profit-taking instincts during a trend (no trimming Strategic Allocation positions)

**Rule:** if the most recent successful 1H structural floor is intact, the position is intact. Sit on your hands.

### Exit triggers

Exit is **full position out**, not trim. When exit fires, capital returns to BIL (direct-buy) or closes the options position.

Any one fires:

1. Most recent 1H structural floor breaks
2. Weekly close below major structural support that the position was predicated on
3. Weekly bearish reversal candle after extended trend
4. Major geopolitical / macro regime change invalidating the original thesis
5. Weekly RSI extreme divergence (>75 with bearish divergence over 3+ months)
6. Macro qualification invalidated during accumulation phase

For options positions, an additional exit:

7. DTE drops below 30 days without target hit AND no clear continuation — exit or roll forward at 30 DTE if thesis intact and warrants additional time

### Re-entry after exit

If structural break is a fakeout and price recovers: not automatic re-entry. Each re-entry requires a fresh structural setup:

- New high after exit → wait
- Pullback from new high to form a new higher low → new accumulation opportunity at the higher base
- Re-dislocation → new accumulation opportunity

### BIL rest state (direct-buy capital)

When direct-buy capital is not deployed in an active cycle, it lives in BIL earning ~5% yield. Default state is BIL.

### Strategic Allocation file structure

Each cycle has a file in `strategic_allocations/` named `cycle_YYYY-MM-DD_ASSET_short-name.md`:
- Plan section: macro qualification, target allocation, expected entry mechanism
- Tracking section: each entry with date, structural signal, screenshot
- Review section: at cycle close
- Handoff section: lessons for next cycle

Every entry requires a screenshot of the 1H structure showing what justified the entry.

### What Strategic Allocation is NOT

- Not "buy and hold forever" — every position has a structural exit
- Not active trading — once a position is established, weekly + 1H structural checks suffice
- Not swing trading — entries graduate to part of the long-term position
- Not exempt from discipline — the 1H structural exits ARE the discipline
- Not short — bear markets are expressed via Trading Book puts

---

## 22. Trading Book Mechanics

The Trading Book is the active returns engine — single-range plays and catalyst events.

### Single-Range plays

**Identification:** Daily/4H/15m range with clear high and low. Long from range low; short from range high. Exit at opposite side of range (previous high or previous low).

**Universe:** Core + Thematic.

**Instrument selection:**
- Long SPY/QQQ → futures (MES/MNQ or ES/NQ)
- Long individual stock → OTM calls
- Short SPY/QQQ → futures or puts
- Short individual stock → OTM puts

**Sizing:** 60-75% of tier max for options; 0.5-0.75% account for futures.

**Exit:**
- Target (opposite side of range): full exit
- Invalidation (1H/4H/15m structural break): full exit
- Time-stop (DTE < 7-14 days, target not approached): full exit

**Profit-taking during the move:** none — single-range plays are taken to the previous high/low fully.

### Catalyst plays (small subcategory — see also Setup E)

**Identification:** Consolidation + identifiable catalyst within DTE + IV in lower 30% of recent range. The catalyst is the trigger AND the binary event being traded (e.g., FOMC, earnings).

**Important distinction from Setup E:** A true catalyst trade plays the moment of the catalyst itself with IV expansion as the edge. Setup E plays the multi-day flow that develops after a catalyst (or independent of one). Most trades that look catalyst-driven are actually Setup E. Pure catalyst trades are rare — maybe 5-10% of Trading Book volume.

**Universe:** Core + Thematic.

**Instrument:** Options only — calls for bullish, puts for bearish.

**Sizing:** Tier max for true catalyst plays where IV compression is real and event is binary.

**Strike selection:** ATM or slightly OTM.

**DTE selection:** catalyst date + small buffer (typically 7-30 days).

**Exit:**
- Catalyst resolution: exit per outcome and price action
- Pre-catalyst invalidation (consolidation breaks adversely): exit
- Profit-taking ladder applies (§ 16)

**Earnings binary lottos explicitly EXCLUDED:** Short-dated OTM options into pending earnings with no consolidation setup have a ~70% zero rate (per Brando trade log analysis). Not a sizing question — an exclusion category. If taken, treat as pure speculation with separate accounting.

### Setup E — Active Flow Tactical

This is the Brando-style trade. Short-dated weekly options on momentum names in active multi-day directional flow, entered at near-term levels.

**Master skill: Active Flow Recognition.** This is upstream of everything else in Setup E and likely accounts for most of the gap between successful execution and follower-style losses. Before any Setup E trade qualifies, the underlying must be in an established multi-day directional run with a named narrative:

- Sector cycle (e.g., semis ripping, banks selling off)
- Earnings cycle effect (post-earnings drift, sympathy moves)
- Related-asset spillover (BTC up → IBIT/MSTR up)
- Macro tailwind (rate cut expectations driving rate-sensitive names)
- Clean technical trend established over multiple sessions

Levels form constantly. Active flow is rare-ish. If you can't name the flow driver in one sentence, Setup E doesn't apply — it's just a level without context.

**Identification (all required):**
1. Active multi-day directional flow on the underlying with named narrative
2. SPX/QQQ regime alignment (don't fight the index)
3. Near-term level identified (30-min consolidation high/low, prior session extreme, round number, recent swing)
4. Defined invalidation (specific price where the level fails)

**Entry styles (track separately):**

**E1 — Break entry:** enter as price punches through the level
- Faster fill, captures the initial impulse
- Risk: false breaks happen; some entries fail immediately
- Better in strong regime + clear flow context

**E2 — Retest entry:** enter on pullback to broken level after clean break
- Better price, structural confirmation that level is holding as new support/resistance
- Risk: misses some entries that don't pull back
- Better in choppier conditions or when premium is high

**Universe:** Any liquid name in active flow. Not restricted to Core + Thematic for Setup E specifically — active flow is the qualifier, not the universe. But options must be liquid (tight spreads, sufficient OI at strikes used).

**Instrument:** 3-7 DTE weekly options. Calls for bullish flow; puts for bearish flow. Slightly OTM strikes typical.

**Sizing:**
- Standard: 1-2% premium of account
- A+ confirmation (active flow + clean level + strong regime alignment): up to 3% premium
- Sized for full zero — disaster acceptance is baked in

**Profit-taking (specific to Setup E):**
- First trim 40-50% of position at +40-60% premium gain
- Second trim 25% at extension to next near-term level
- Runner 25% with hard time stop before final expiry day
- Trim levels are firmer than other setups because short DTE means theta acceleration is brutal if held

**Rolling discipline (CRITICAL):**
- First roll: 20-25% of realized profit, smaller premium, next strike
- Second roll: only on explicit continuation + still aligned regime, smaller again
- **Third roll: FORBIDDEN.** Documented evidence: third rolls have >50% loss rate in Brando's trade log. Multiple zeros traced to third rolls (MU 470C, MU 425C, MU 390C, COIN 215C, SPX 6740C as examples).
- Roll number tracked in pre-trade ticket; value 3 not permitted

**Exit triggers:**
- Target hit and trims executed per profit-taking ladder
- Underlying breaks the level it was entered on (invalidation)
- Flow narrative breaks (e.g., sector rolls over, related-asset reverses)
- Hard time stop: exit by end of final session before expiry regardless
- Roll exhausted (2 rolls completed, no third permitted)

**Exclusions for Setup E:**
- Earnings binary lottos (separate exclusion category)
- Post-catalyst chop window: 1-2 sessions after major catalysts (FOMC, mega-cap earnings) = no Setup E unless clean level re-engagement is visible. Default no-trade in that window.
- Names without active flow context: a level is not enough — flow must be named

**Expected performance (Brando trade log baseline):**
- ~50-65% blended return on premium per winner
- ~19% total-zero rate (1 in 5 trades)
- Annual ceiling for disciplined execution: 1.75-2x normal markets, up to 2.5x trending year
- Below that ceiling = execution problems; above = oversizing or selective showcasing

### Trade type allocation expectation per Sprint

Approximate proportions during normal operation:
- Single-Range plays: 50-60% of Trading Book volume
- Setup E (Active Flow Tactical): 30-40% of volume
- Catalyst plays (true catalyst, IV compression): 5-10% of volume

Sprint 1 specifically: take all three types as they present. Setup E requires deliberate practice since the active flow recognition skill is new. Expect Setup E grades to be weakest early. Data from Sprint 1 reveals which type produces your edge.

---

## 23. Asymmetric Bet Book (Deferred)

**Status: Deferred until Sprint 3+.**

The Asymmetric Bet Book is for multi-year LEAPS positions on thematic single names with defensible long-term theses.

### Why deferred

- The QBTS-type "I saw a great daily setup" opportunity is solved by the Trading Book's Thematic Tier
- Asymmetric Bets are a low-EV, low-operational-cost book that only matters in the rare 5-20x outcome
- Sprint 1-2 focus is on Trading Book and Strategic Allocation
- Revisit at Sprint 3 once core books are operationally stable

### Planned design (for future activation)

- Universe: any single name with defensible multi-year thesis
- Instrument: 1-2 year LEAPS at 0.30-0.50 delta
- Sizing: 0.5% account per position (premium = position size = max loss)
- Maximum book exposure: 3% account total
- No active management except roll forward at ~6 months remaining DTE if thesis intact
- Profit-taking: trim at 3x / 5x / 10x / 20x (20% / 20% / 25% / 25%)
- Exit only on objective external thesis-break, never on price action
- Scaling: original entry + max 2 adds, each requiring 100%+ from prior entry AND objective structural inflection
- Max total exposure per name: 1.5% account

To be formalized when activated.

---

## 24. Daily Routine

### Pre-market

1. Check SPY/QQQ futures and overnight movement
2. Review macro/news/events
3. Mark key daily/4h/1h levels for focus tickers (core + thematic)
4. Review current open Trading Book positions
5. Check Strategic Allocation state — any cycles active? approaching trigger or exit?
6. Identify 0-3 possible Trading Book trades
7. Define triggers, invalidations, targets
8. Decide posture: Aggressive / Selective / Defensive / No-Trade
9. Append row to `daily_desk.csv`

### During market

- Watch only planned names
- No random ticker chasing
- Use intraday PA only at pre-planned levels
- Document entry before or immediately after execution (Pre-Trade Ticket)
- Update `trade_actions.csv` after any action
- No emotional add
- No unplanned overnight hold

### End of day

1. Record all actions in `trade_actions.csv`
2. Update `open_positions.csv`
3. Reassess overnight risk on any open positions (futures especially)
4. Note emotional state
5. Prepare next-day levels
6. Update `risk_drawdown.csv` and `capital_allocation.csv` with EOD equity
7. Post-trade journal for any trades closed today
8. Mark daily completion in `daily_desk.csv`

---

## 25. Weekly Routine

### Weekend Review (Sunday)

1. Review SPY/QQQ weekly/daily structure
2. Identify market regime
3. Review macro calendar
4. Review earnings calendar
5. Select Trading Book focus list: 1-2 indices + 1-3 core stocks + 0-3 thematic
6. Define setups for each
7. Review Strategic Allocation status — any cycles approaching trigger or exit?
8. Review prior week's trades — what worked, what didn't, classifications correct?
9. Identify mistakes and strengths
10. Set weekly posture
11. Update Snapshot in `Trading_OS.md`
12. Append row to `weekly_review.csv`
13. Update current Sprint file's Tracking section
14. Update `capital_allocation.csv` snapshot

### Weekly metrics tracked

- Total P&L by book
- Realized + unrealized P&L
- BIL yield earned
- Trade count by category (Single-Range / Catalyst)
- Win rate, average R, largest win/loss
- Rule violations
- Process compliance %
- A-Trade %
- Best/worst setup type
- Capital deployment by book

---

## 26. Post-Trade Review & Grading

Every trade is graded on four dimensions. **Grades reflect process, not outcome.**

Strategic Allocation cycles use a parallel review at cycle close (Plan → Tracking → Review → Handoff in the cycle file), not the four-grade rubric on each entry. The cycle as a whole gets a review.

### Setup Grade

- **A:** All Setup requirements met; multiple higher-timeframe confirmations; full technical + narrative alignment; clean invalidation; room to target; market regime supports
- **B:** Qualifies fully with one minor weakness
- **C:** Marginal qualification — meets bar with notable gaps
- **D:** Below threshold — should not have been taken
- **F:** Did not qualify

### Execution Grade

- **A:** Entered at planned trigger, planned price (or better), planned size, planned instrument, planned time
- **B:** Minor deviation
- **C:** Notable deviation (chased entry, off-plan on size or instrument)
- **D:** Major deviation
- **F:** Multiple plan parameters violated

### Management Grade

- **A:** All trims at planned levels; invalidation respected; profit protection at thresholds; no unplanned adds; overnight per plan
- **B:** Minor deviation
- **C:** Notable deviation
- **D:** Major deviation
- **F:** Multiple major deviations or position effectively unmanaged

### Process Grade

- **A:** Ticket 100% complete; all rules followed; journal same day; zero exceptions
- **B:** Ticket 100% complete; all rules followed; journal next morning; zero exceptions
- **C:** Ticket 100% complete; one minor rule deviation documented
- **D:** Ticket 100% complete; one material rule violation logged
- **F:** Any missing ticket field, OR rule violation without documentation, OR no journal within 24 hours

Process Grade **cannot exceed C** if anything entered the Mistake Log.

### Derived metrics

- **Trade Quality** = lowest of the four grades
- **A-Trade flag** = all four ≥ B AND at least three are A

A-Trade % is the primary process metric during Sprint phases.

---

## 27. Loss Limits & Drawdown Circuit Breakers

Computed against full account equity. Strategic Allocation mark-to-market drawdowns do NOT trigger these — only realized losses from Trading Book operations and Strategic Allocation cycle exits.

**Sizing tier drops one level on any circuit breaker activation.**

### Daily loss limits (Trading Book realized)

- **Daily loss > 1.0%:** stop opening new trades for remainder of day
- **Daily loss > 2.0%:** Emergency Reset trigger; sizing tier drops
- **Daily loss > 3.0%:** hard halt; all open positions reviewed for immediate close

### Weekly loss limits (Trading Book realized)

- **Weekly loss > 2.5%:** posture downgraded to Defensive for remainder of week
- **Weekly loss > 4.0%:** Emergency Reset trigger; sizing tier drops
- **Weekly loss > 6.0%:** hard halt remainder of week; mandatory weekend postmortem

### Drawdown circuit breaker (Trading Book peak-to-current)

- **Drawdown 3-5%:** posture downgraded to Selective minimum; sizing tier drops one level
- **Drawdown 5-8%:** posture downgraded to Defensive; per-trade sizing reduced 50%; tier drops two levels
- **Drawdown 8-12%:** hard halt; mandatory Framework Review before resuming
- **Drawdown >12%:** full Emergency Reset including possible framework re-architecture

---

## 28. Emergency Reset

Pre-built off-ramp. Triggered by guard rail OR trader judgment.

### Mandatory triggers (any one)

- Daily loss > 2.0% Trading Book realized
- Weekly loss > 4.0% Trading Book realized
- Trading Book drawdown > 6.0% from peak
- 3 consecutive losing trades
- Any Critical-severity rule violation logged
- Any rule violation flagged Repeated for second time in single week
- 2 consecutive tickets with documented emotional state of Frustrated / FOMO / Revenge / Euphoric
- Any trade taken without a ticket
- Any single-trade loss exceeding planned max by >50%
- Failure to exit on documented invalidation
- Strategic Allocation violation: allocating outside framework

### Discretionary triggers

- Emotional state may be compromising decisions
- Significant unexplained P&L variance from plan
- Personal life event likely to compromise focus
- Account balance milestone materially changed psychology

### What Emergency Reset does

1. All new Trading Book entries halted immediately
2. All open Trading Book positions reviewed within 24 hours — close if not defensible
3. Strategic Allocation positions NOT automatically affected
4. Mandatory documented postmortem within 48 hours
5. Minimum 24-hour cooling-off before next ticket
6. Returning posture set to Selective maximum for first full week
7. Sizing tier dropped for first 5 trades after reset
8. Postmortem promoted into Mistake Log and Framework Evolution Log

### Coming off Emergency Reset

- Postmortem complete and logged
- 5 consecutive trades at Trade Quality ≥ B
- No new rule violations during reduced-size return
- Snapshot updated to reflect normal state

---

## 29. Account Architecture (Brokerage + 401k)

### Brokerage account (~$373,622)

Houses all three books and futures trading.

### Solo 401k (~$117,000)

**Out of scope for Sprint 1-2.** At Quest 2 close, mirror Strategic Allocation in the 401k:
- Same direct-buy universe (SPY/QQQ/GLD/IBIT/ETHA)
- Same cycle-based discipline
- No options trading in 401k
- No futures in 401k
- Tracked in parallel with separate cycle files prefixed `401k_`

### Capital tracking

All capital deployment tracked in `capital_allocation.csv`:
- Brokerage total equity
- Trading Book open premium + futures margin
- Strategic Allocation deployed per asset (direct + megacap options)
- BIL balance
- 401k total + breakdown (when activated)
- Combined household total

Updated daily at EOD or after material capital movement.

---

## 30. Source Material Map

Elite Options materials and other PDFs in the Claude.ai Project are reference inputs, not the governing system. This doc is the governing source.

Key extracted ideas:

- A+ setups require technical confirmation, themes, and market alignment
- SPX/QQQ regime matters for individual stock breakouts
- Support/resistance is strongest when repeated across higher timeframes
- Options should have liquidity and volume; strikes within expected/implied move
- Day trades may use shorter DTE; swing trades 1-3 months DTE
- Profit-taking should be proactive; options can flip quickly
- Compounding adds should use only realized profits
- Journal everything; protect downside first

---

## 31. Framework Evolution Log

| Date | Change | Reason |
|---|---|---|
| 2026-05-22 | v0.1 initial framework | Original consolidation from prior notes and Elite Options materials |
| 2026-05-23 | v0.2 — migration to local markdown/CSV; Snapshot, four-grade rubric, Setup E, campaign definition, loss limits, Emergency Reset triggers, profit-taking hierarchy, ticket schema improvements, universe enforcement, sizing caps, phases concept, hypotheses + intervention logs, Live Position Management chat | Filesystem MCP enables in-place editing; v0.1 had internal contradictions and missing definitions |
| 2026-05-23 | v0.3 — options sizing rewrite (premium = max risk); graduated sizing tiers; Mission/Quest/Sprint structure; invalidation rule simplified; Compounding/Rolling/Add terminology; Lotto definition tightened; Large Gain Rule to % of equity; tickets only for executable trades; Sprint defined | Multiple structural refinements; eliminated edge cases that risked encoding hope as strategy |
| 2026-05-23 | v0.4 — Three Books architecture (Trading / Strategic Allocation / Asymmetric Bet) | Three genuinely different activities with distinct universes, instruments, and disciplines |
| 2026-05-23 | v0.4 — Strategic Allocation cycle-based with BIL rest state; weekly/monthly structural triggers; progressive tranching; weighted universe with elevated gold; re-entry on pullback-to-higher-low; cost basis irrelevant; Thematic Tier added to Trading Book; options-only Trading Book; Asymmetric Bets deferred; 401k accounted for; BIL rest state | Major structural improvements addressing real gaps |
| 2026-05-23 | v0.4 — Trading Google Calendar integrated | Same pattern as Cycling OS; makes framework rhythm visible in time |
| 2026-05-23 | v0.5 — Strategic Allocation rewritten around 1H structural accumulation with migrating protective stop | v0.4's progressive weekly tranching didn't match user's mental model. Structural failure mechanism (1H exits) is the real protection; macro qualification permissive |
| 2026-05-23 | v0.5 — BTC/ETH via IBIT/ETHA; equal sub-tranche sizing | $0 commission, 401k compatibility, cleaner tax. DCA logic favors equal sizing |
| 2026-05-23 | v0.5 — Books work together: unified 1H analysis feeds both Strategic Allocation (shares, bullish) and Trading Book (options, bidirectional). SA never goes short; bear markets via Trading Book puts | Resolves the v0.4-v0.5 gap where Setup C on SA was undefined. Right instrument for each direction |
| 2026-05-23 | v0.6 — Two trade category framework (Structural / Catalyst); Three Books reorganized by intent not instrument; decision tree as canonical opportunity-routing logic | The previous framework had multiple paths that could apply to a given setup. The Two Categories + Decision Tree make routing mechanical |
| 2026-05-23 | v0.6 — HTF Range definition operationalized (low that took out prior low and made new high; high that took out prior high and made new low) | Replaces "major weekly structure" with a testable definition |
| 2026-05-23 | v0.6 — Megacap names (MSFT/META/NVDA/AMZN) added to Strategic Allocation Book via OTM call options | The MSFT-style structural accumulation thesis is a real opportunity that options express cleanly without gap risk. Activates what was previously deferred Tier B SA |
| 2026-05-23 | v0.6 — Futures introduced for Trading Book index range plays (SPY/QQQ longs and shorts) | Cleaner instrument for short-timeframe single-range plays on indices. Capital-efficient leverage; no theta; reliable execution. Sized at 0.5-0.75% account |
| 2026-05-23 | v0.6 — Sizing differentiation by trade type within tier; max simultaneous positions per tier; capital allocation across books (max SA 80%, max TB open premium 8-12%) | Catalyst plays at tier max, single-range at 60-75%, futures at 0.5-0.75%. Position-count caps prevent attention dilution |
| 2026-05-23 | v0.6 — Megacap Strategic Accumulation: full-size single entry per accumulation event (no sub-tranching) | Contract granularity at Tier 1-2 prevents real sub-tranching. Structural exit discipline contains risk on full-size single entries |
| 2026-05-23 | v0.6 — DTE selection rule: 1.5x typical retracement timeframe for similar-magnitude move | Asset-calibrated rather than fixed |
| 2026-05-23 | v0.6 — Trading Book Single-Range exit at previous high/low (full exit, no trim); time-stop at 7-14 DTE if target not approached | Single-range plays defined by the range; exit is mechanical |
| 2026-05-23 | v0.7 — Setup E (Active Flow Tactical) added as Category 2, replacing the broader "Catalyst" category as the primary asymmetric-returns trade type. Catalyst plays demoted to small subcategory (~5-10% of volume). | Brando trade log analysis (96 trades, 11 weeks) revealed his style is NOT primarily catalyst-driven. It's short-dated weekly options on active-flow names at near-term levels. Active flow recognition is the master skill upstream of level identification. The framework's previous "catalyst" framing was a misreading. Pure catalyst trades exist but are rare. |
| 2026-05-23 | v0.7 — Setup E sub-styles E1 (break entry) and E2 (retest entry) tracked separately; rolling discipline formalized (max 2 rolls per campaign, third forbidden); earnings binary lottos explicitly excluded; post-catalyst chop window codified | Documented evidence from Brando trade log: third rolls have >50% loss rate (MU 470C, MU 425C, MU 390C, COIN 215C, SPX 6740C); earnings binary lottos zero at ~70% rate; post-catalyst chop produces repeated zeros. Each is an evidence-based exclusion or cap, not theoretical. |
| 2026-05-23 | v0.7 — Realistic return ceiling acknowledged: 1.75-2x annual normal markets, up to 2.5x trending year, ~19% total-zero rate. Marketing claims of 6-7x in months not encoded into framework. | Honest math from Brando trade log: 5 of 11 weeks strong winners, 3 mixed, 3 net negative; average winner blended 50-65%, not the max-trim numbers shown in marketing. The realistic ceiling supports Quest 1 ($25k/mo) easily and Quest 2 ($40k/mo) in trending years; Quest 3 ($52k/mo sustained) is hard; "8 figures in 2-3 years" requires multi-year compounding closer to 5-8 year horizon. |
| 2026-05-23 | v0.7 — Pre-trade ticket required fields expanded: DTE bucket, Flow context, Entry style if Setup E, Roll number in campaign, Flow driver named | Brando-style discipline requires explicit pre-trade classification to prevent post-hoc rationalization and to enable Sprint Review to aggregate by trade type. Roll number especially — the third roll is statistically documented as poison. |
| 2026-05-25 | v0.8 — Complete architectural collapse: "Two Categories with Setup E" replaced with "One trade type, four flavors" (Strategic Allocation, Moonshot, Trend, Tactical). Three Books concept retired; all active trading flavors share one framework. | Brando research dataset analysis (844 legs, plus foundational INO+BAC verification) revealed that the previous architecture was over-segmented. What looks like different trade types is actually the same chart-reading skill applied at different timeframes with different instruments. The four-flavor model captures the real variation: hold intent, universe restriction, instrument matching, sizing logic. |
| 2026-05-25 | v0.8 — Asymmetric Bet Book absorbed into Moonshot flavor and activated (no longer deferred to Sprint 3+) | Moonshot is the wealth-creation mechanism that the previous "Asymmetric Bet Book" was trying to be but never operationalized. Activated under strict profit-funded sizing (§ 13) to provide structured access to outlier returns without catastrophic risk. |
| 2026-05-25 | v0.8 — Profit-funded sizing for Moonshot Book: gated by edge demonstration (≥10 trades, ≥90% compliance, account up ≥5%); single Moonshot max 30-40% of YTD realized profits; paused if YTD goes negative; annual reset | Mirrors the Brando $6k→$10k→$25k pattern of grinding small profits then deploying earned capital into high-conviction asymmetric bets. Mathematically produces convexity while bounding loss to earned money. Psychologically removes oversize-early temptation. |
| 2026-05-25 | v0.8 — Classification at pre-trade ticket binds management discipline for trade duration; reclassification mid-trade is Critical-severity violation | Most common failure mode is "entered as Tactical, going well, let it run as Trend." The classification gates management style. Want exposure beyond original classification's hold timeframe? Take a separate trade in the new flavor, don't morph the existing position. |
| 2026-05-25 | v0.8 — Documented exclusions codified: earnings binary lottos (~70% zero), FOMC/CPI lottos (~40% zero), 0DTE-as-core (-3.1% mean), trades while YTD red (-4.4% mean) | Evidence-based from 844-leg Brando dataset. Not theoretical — these are statistically documented failure modes that have produced the worst outcomes in actual options trading at similar style. |

---

## 32. Glossary

| Term | Definition |
|---|---|
| Mission | Decade-level vision. See § 1. |
| Quest | Outcome-defined financial milestone arc. See § 3. |
| Sprint | 3-6 week time-boxed framework-iteration block within a Quest. See § 3. |
| Strategic Allocation Book | Long-term wealth accumulation engine. HTF range bottom to range top. Shares (direct) or OTM calls (megacaps). See § 21. |
| Trading Book | Active returns engine. Single-range plays + catalyst plays. Futures/options. See § 22. |
| Asymmetric Bet Book | Multi-year LEAPS book. Deferred. See § 23. |
| Strategic Accumulation | Trade type — HTF range bottom long held to HTF range top. See § 4, § 21. |
| Trading Book Single-Range | Trade type — tactical range play, long or short, exit at previous high/low. See § 4, § 22. |
| Catalyst play | Trade type — consolidation + identifiable event + IV expansion edge. See § 4, § 22. |
| Campaign | One continuous bet on one ticker, one direction, across one or more trades. See § 20. |
| HTF Range Low | A low that took out a prior low and then made a new high above prior highs. See § 9. |
| HTF Range High | A high that took out a prior high and then made a new low below prior lows. See § 9. |
| Decision Tree | The three-question routing logic for every opportunity. See § 6. |
| Process Compliance % | % of trades with complete ticket + timely journal |
| A-Trade | Trade graded all four ≥ B with at least three A. See § 26. |
| Trade Quality | Lowest of the four post-trade grades |
| R / R-multiple | Trade P&L as multiple of planned max loss |
| Posture | Daily/weekly aggressiveness: Aggressive / Selective / Defensive / No-Trade |
| Sizing Tier | Tier 1-4 determining max per-campaign premium. Earned by trade count + compliance + account performance. See § 13. |
| DTE | Days to expiration (options) |
| LEAPS | Long-term equity anticipation securities — options >12 months DTE |
| Invalidation | Pre-defined level at which thesis is wrong and position closes |
| Lotto | Low-probability, high-reward options trade funded from realized profit |
| BIL | Short-term Treasury ETF used as rest state for Strategic Allocation reserve. ~5% yield. |
| Sub-tranche | One of 3 entries within a direct-buy Strategic Allocation cycle (~33% of target each) |
| Hypothesis | Falsifiable claim tracked in `hypotheses_register.csv` |
| Intervention | Deliberate framework change logged in `intervention_log.csv` |
| Emergency Reset | Pre-built off-ramp. See § 28. |
| Snapshot | Top of `Trading_OS.md`. Current state read by all chats on init. See § 2. |
