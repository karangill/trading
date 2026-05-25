# Sprint 1 — Execution Discipline

**Sprint #:** 1
**Parent Quest:** Quest 1 — First $25k Realized Month
**Window:** 2026-05-25 → 2026-06-19 (4 weeks; option to extend by 1-2 weeks if trade count <15)
**Framework version:** v0.8
**Status:** Active
**Hypotheses under test:** H001 (sprint edge); H002 (grading rubric predictive validity). See `hypotheses_register.csv`

---

## Plan

### Primary objective

Generate clean execution data under the v0.6 framework to test whether the system + discretionary execution produces positive expected value with disciplined process compliance.

This Sprint is not about maximizing P&L. It's about producing the data that resolves H001 — and contributing trades toward the Quest 1 financial target as a byproduct of good process.

### Quest alignment

Sprint 1 is the first Sprint within Quest 1 (First $25k Realized Month). The Sprint's success criteria are framework-level (process compliance, A-Trade rate, no catastrophic loss, sufficient trade count). The Quest's success criterion is financial ($25k realized in a calendar month). The Sprint contributes to the Quest but isn't graded by it.

### Success criteria

All four must be met for Sprint to be judged passing:

- ≥90% process compliance (all trades have complete tickets + journals within 24 hours)
- ≥70% A-Trade rate (all four grades B+ with at least three A's)
- Zero catastrophic losses (no single-trade loss >2x planned max, no drawdown >8%)
- ≥15 trades logged (need data volume for any conclusion)

### Failure conditions

Any of these triggers Sprint extension or framework revision before continuation:

- <90% process compliance → extend Sprint or restructure framework
- Any catastrophic loss → Emergency Reset + framework review before resumption
- <15 trades by end of week 4 → extend Sprint OR review whether universe/setup criteria are too restrictive
- Pattern of low-grade trades → setup definitions reviewed and tightened in v0.4

### Sprint-specific rules (more restrictive than steady-state framework)

- Decision tree applied to every opportunity (Trading_OS.md § 6); if it doesn't route cleanly, it's not a trade
- Three flavors active in Sprint 1: **Strategic Allocation** (if cycle triggers — unlikely), **Trend** (60-180 DTE options on megacaps/quality names in confirmed trends), **Tactical** (3-21 DTE options on liquid names with active flow + near-term levels, including futures for index range plays)
- **Moonshot flavor LOCKED in Sprint 1** — requires edge demonstration (≥10 trades, ≥90% compliance, account up ≥5%). Earliest realistic activation: end of Sprint 1 or Sprint 2 if metrics achieved.
- Max simultaneous active positions: 3
- Prefer 0 over marginal trades — 0 trades beats a B-grade trade
- Narrow universe: 1-2 indices + 1-3 core stocks + 0-3 thematic declared at each Weekly Review (Tactical universe is broader — any liquid name in active flow)
- **Sizing Tier 1:** 1.0% max premium per campaign; flavor differentiation per Trading_OS.md § 13:
   - Trend: 1.5-2.5% per position (capped at Tier 1 max of 1.0% for Sprint 1)
   - Tactical: 0.5-1.5% per position (standard 0.75%)
   - Futures: 0.5-0.75% account
- Tier 2 unlocks at ≥10 trades with ≥90% compliance and positive aggregate R
- **Classification at pre-trade is BINDING.** Flavor determines management style for trade duration. Reclassifying mid-trade is Critical-severity rule violation.
- **Hard exclusions:**
   - Earnings binary lottos — excluded (~70% zero rate)
   - FOMC/CPI macro lottos — excluded (~40% zero rate)
   - 0DTE options as core sizing vehicle — excluded (-3.1% mean)
   - Trades while account YTD is red — excluded (-4.4% mean)
   - Third roll in any campaign — forbidden
   - Post-catalyst chop (1-2 sessions after FOMC, mega-cap earnings) — no Tactical trades unless clean level re-engagement
- No averaging down short-dated options
- Mandatory same-day or next-morning post-trade journal
- Mandatory Weekly Review every Sunday
- Mandatory mid-sprint check at end of week 2 (2026-06-07)
- Strategic Allocation Book: default state is BIL; framework ready if a cycle triggers but expectation is no triggers in 4 weeks

### Posture defaults during Sprint

- Default posture: **Selective**
- Aggressive posture **not allowed** during Sprint 1 — too early in calibration
- Defensive or No-Trade fine whenever conditions warrant
- Posture downgrades from circuit breakers (`Trading_OS.md` § 22) override default

### Focus list rules

- Declared at each Weekly Review
- 1-2 indices (SPY/QQQ) + 1-3 core stocks (from NVDA/TSLA/MSFT/META/AMZN/NOW/MSTR/BABA) + 0-3 thematic names
- Trades outside the focus list require documented Rule Exception in ticket
- More than 1 exception per week → review at Weekly Review

### What's intentionally deferred

- Setup Stats and Instrument Stats aggregations — insufficient data
- Higher sizing tiers (Tier 2+ unlock based on data)
- Phase 3 sized execution — depends on Quest 1 outcome

---

## In-Progress Tracking

> Updated weekly during Weekly Review and on demand after material events.

### Week 1 (2026-05-25 → 2026-05-31)

**Opening declaration (set by Weekly Review #1, 2026-05-25)**

**Window:** Tue 2026-05-26 → Fri 2026-05-29 (Memorial Day Mon 5/25 closed)

**Market context entering week:**
- SPY closed Fri 5/22 at $745.64 (-0.5% from ATH 749.53 set 5/14). 8th consecutive winning week — longest since 2023.
- QQQ closed $717.54; intraday 52w high 722.12 printed Fri 5/22, did NOT hold close (failed retest signal).
- VIX 16.70 compressed; 10Y ~4.6% elevated; Dow at ATH; Russell +0.91% Fri (broad participation).
- Dominant narrative: Iran-deal optimism. Headline risks: deal reversal, Trump EU tariff escalation, Warsh-Fed (sworn in 5/22) opening rhetoric.
- Macro events next week: Tue Consumer Confidence + Durable Goods; Thu Q1 GDP 2nd est; **Fri April PCE (binary event)**.
- Earnings (none in Core list): Wed AH MRVL/CRM/SNOW/SNPS; Thu AH DELL/COST/MDB/BBY/ADSK. None on the focus list for entry.

**Posture:** Selective. Target 1-3 A-grade tickets; zero is acceptable.

**Focus list:**
- *Tactical (indices, 2):* SPY, QQQ — long the confirmed 1h bullish range + retrace setup. Trigger = new 1h high prints (confirms range), wait for retrace into range, long bounce via futures (MES/MNQ or ES/NQ) targeting new high. Do NOT chase pre-confirmation.
- *Trend watchlist (situational quality, 5):* BABA, MSFT, NOW, EWZ, LMT — all at/reversing from daily/weekly bullish range lows per § 9. Use 1h/15m for entry timing. Instrument: 60-180 DTE slightly OTM calls. Tier 1 cap = 1.0% premium per campaign even though Trend standard range is 1.5-2.5%.
- *Thematic (0):* none for Week 1. DELL dropped as a candidate — +16% rip on 5/22 with no PA structure for a long entry, would just be chasing strength.
- *SA candidates under evaluation:* IBIT, ETHA — weekly compression / bullish reversal forming. NOT a Trading Book trade. First sub-tranche requires cycle file in `strategic_allocations/` BEFORE entry per § 21.

**Trigger-specific entry conditions per name:**
- SPY/QQQ: 1h bullish range must CONFIRM (new high after the higher low). Then wait for retrace. Only enter long on bounce confirmation off the retrace. Target = new range high. Tactical Single-Range, full exit at target per § 22.
- BABA, MSFT, NOW, EWZ, LMT: weekly/daily bullish range low confirmed per § 9 (low that took out prior low, then made a new high above prior highs). 1h/15m structural entry on the way back up. Trend flavor, ride toward ATH.
- IBIT/ETHA: cycle file Plan section drafted (macro qualification + 3-sub-tranche plan) BEFORE first 1h bullish range continuation triggers a tranche entry.

**Defensible narratives identified for ticket time (per Weekly Review #1 research):**

- **LMT:** *Defense supercycle driven by Trump FY27 $1.5T budget proposal (76% above FY26 $901B); F-35 procurement up 62%, PAC-3/MSE up 8x, THAAD up 9x; $186-194B backlog with $63B recognizable next 12 months; NATO permanent re-armament with international mix expanding to 31%.* Use the FY27 budget narrative as the lead. Do NOT use Iran/geopolitics narrative — cuts the wrong way right now.
- **EWZ:** narrative to be confirmed at ticket time — candidates: BRL strength, EM rotation off USD weakness, commodities cycle, Brazil-specific political/fiscal catalyst. Name one.
- **BABA:** China stimulus / regulatory thaw / valuation rebound. Acknowledge China regulatory risk in Notes.
- **MSFT, NOW:** Trend-friendly secular narratives (AI infrastructure, enterprise agentic workflows respectively); no narrative gap.
- **IBIT (BTC SA candidate):** *Structural ETF demand-supply imbalance (~10:1 absorption vs daily mining), compression at potential higher low vs prior cycle, three-month positive momentum signal, CLARITY Act regulatory clarity.* Accept that second/third sub-tranche could come at $65-70K if first 1h trigger fails — cycle file must document tolerance.
- **ETHA (ETH SA candidate):** *Compression at washed-out sentiment (down 36% YTD, 57% from ATH) + Glamsterdam upgrade 90-180 days out following Pectra Q2-2025 setup template + new staking-enabled ETHB ETF product driving structural flows + record on-chain whale accumulation (26.55M ETH, +32% YTD) while price suppressed.* Most asymmetric of the three setups by the numbers.

**Carry-forward flags for ticket time:**
- **LMT narrative:** structural thesis qualifies, but § 10 requires both technical AND narrative. Geopolitics cuts AGAINST defense right now (Iran-deal optimism = defense fade). LMT ticket must use the FY27 defense budget narrative (or NATO re-armament / Golden Dome / backlog visibility) — NOT Iran/Middle East tensions.
- **BABA:** idiosyncratic China regulatory risk. Acknowledge in ticket Notes, don't ignore.
- **EWZ:** Brazil narrative thesis required at ticket time (BRL strength / EM rotation / commodities cycle / political catalyst — name it).

**Hard exclusions Week 1:**
- No SPY/QQQ longs chasing breakouts through $749.53 / $722.12 pre-1h-range-confirmation. The trade is the retrace, not the chase.
- No fresh shares positions held into Fri PCE without explicit stress-gap loss documentation in ticket.
- No pre-earnings lottos (CRM, MRVL, COST, DELL, etc.) — evidence-based exclusion per § 13.
- No NVDA emotional add post-earnings.
- No Moonshot-flavor classifications (locked per § 13: requires 10+ trades, 90%+ compliance, account up 5%).
- No third roll on any campaign (§ 22 exclusion).
- No SA tranche entry without cycle file extant.

**Action items before/during Week 1:**
1. **Tue 5/26 open:** execute BIL purchase $298,898. Log in Daily Desk as compliance-noted (one-day Memorial Day slip, not a violation).
2. **Pre-Daily-Desk Tuesday:** mark daily/4h/1h levels for SPY, QQQ + the 5 Trend candidates. Confirm or reject each against § 9 HTF range low definition.
3. **This week, separate chat:** Long-Term Positioning chat to draft IBIT and ETHA cycle files in `strategic_allocations/` so SA entries are pre-authorized if 1h trigger fires.
4. **Daily emotional check:** opening-week itch is the predicted Week 1 failure mode. If a setup feels like "I need to start the sprint with a trade," that IS the emotional signal. Wait.

**Sprint metrics entering Week 1:**

| Metric | Target | Entering Week 1 |
|---|---|---|
| Trades logged | ≥15 | 0 |
| Process compliance | ≥90% | N/A (no trades yet) |
| A-Trade rate | ≥70% | N/A (no trades yet) |
| Rule violations | 0 critical | 0 |
| Drawdown | <8% guard | 0.0% |
| Sizing tier | Tier 1 (1.0% max premium/campaign) | Tier 1 |

**Week 1 tracking (filled at Week 1 close):**

- Trades: TBD
- Process compliance: TBD
- A-Trade rate: TBD
- P&L: TBD
- Notable events: TBD
- Rule violations: TBD
- Emotional patterns: TBD
- Sizing tier: Tier 1

### Week 2 (2026-06-01 → 2026-06-07)

(to be filled)

### Week 3 (2026-06-08 → 2026-06-14)

(to be filled)

### Week 4 (2026-06-15 → 2026-06-19)

(to be filled)

### Running totals

| Metric | Current | Target | Status |
|---|---|---|---|
| Trades logged | 0 | ≥15 | Below |
| Process compliance | — | ≥90% | — |
| A-Trade rate | — | ≥70% | — |
| Largest loss | — | <2x planned max | — |
| Current drawdown | 0% | <8% | OK |
| Rule violations | 0 | minimize | OK |
| Sizing tier | Tier 1 | Tier 2 likely by week 2-3 | — |

---

## Review

(filled at end of Sprint)

### Did we hit the success criteria?

(to be filled)

### Hypothesis resolution

- H001: (Resolved Positive / Resolved Negative / Inconclusive — extend)
- H002: (likely still open, insufficient data — needs Sprint 2 data)

### What worked

(to be filled)

### What didn't work

(to be filled)

### Framework changes warranted (v0.7 candidates)

(to be filled — promote to next Framework chat)

### Setup-specific findings

(to be filled — which setup types resolved as best/worst R)

### Emotional pattern findings

(to be filled)

### Quest 1 contribution

How much realized P&L did Sprint 1 contribute toward the Quest 1 $25k target?

(to be filled)

---

## Handoff to next Sprint

(filled at end of Sprint)

### Sprint 2 starting parameters

(to be filled based on Sprint outcomes)

### Framework v0.7 candidate changes

(to be filled)

### Open questions carried forward

(to be filled)
