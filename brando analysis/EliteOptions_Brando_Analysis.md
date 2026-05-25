# EliteOptions / Brando — Honest Strategy Model (Phases 3 & 4)

**Prepared:** 2026-05-24 · **Analyst:** Cowork agentic study of the ELITE OPTIONS Discord
**Primary dataset:** `brandos-trade-alerts` (the `EliteOptions | Brando` APP bot), Nov 5 2024 → May 21 2026 (~18.5 months)
**Sample:** 2,090 raw option alerts → **844 reconstructed trade legs** across **489 campaigns** (+ 21 stock positions excluded from options stats)
**Companion file:** `brando_trades_per_leg.csv` (per-leg data) · `EliteOptions_ChannelMap_Phase1.md` (channel map)

---

## 0. Method, and why the numbers differ from his

A **leg** = one entry on a specific contract (ticker+strike+expiry) plus all of its scale-out sells. A **campaign** = an initial entry plus its rolls.

The single most important methodological choice, per your framework: **blended weighted return**, not "max profit at highest sell."

> blended ratio = (Σ proceeds across every partial sell, weighted by fraction sold) ÷ entry cost

Two rules that make this honest and that Brando's displayed numbers do not apply:
1. **Silent / expired positions = total loss.** When a contract has an entry but no visible profitable exit (very common with his 0DTE lottos that simply expire), the unsold remainder is valued at **zero**. This is what generates the real loss tail.
2. **Scale-outs are weighted by size, not best price.** Selling ¼ at the top and ¾ lower blends to far less than "max."

Reconstruction was validated leg-by-leg against the raw feed (campaign resets handled by expiring contracts at their expiration date; this is the fix that stops abandoned legs from masquerading as deep "rolls").

**Data-integrity note:** the authoritative statistics in this document are computed over the full **844-leg** set. The exported `brando_trades_per_leg.csv` contains **802** of those legs — ~42 rows (predominantly total-loss legs) were lost in export, so the CSV's *own* mean (+7.3%) is optimistic. Use the figures in this document (true mean **+2.3%**) as canonical; treat the CSV as a ~95% sample that is slightly winner-biased.

---

# PHASE 3 — Quantitative findings

## 1 & 2. Trade taxonomy and blended return by category

Categorised by what he *actually does*. Returns are **blended** (not max).

| Category | Count | Mean blended | Median | Win rate | Total-loss rate |
|---|---:|---:|---:|---:|---:|
| Initial breakout (depth 0, momentum name) | 195 | **+3.5%** | +18.4% | 65% | 24% |
| Lotto (short-dated / index / named catalyst) | 316 | **+1.1%** | +18.7% | 65% | 29% |
| First roll | 188 | **+3.1%** | +19.8% | 62% | 29% |
| Second roll | 43 | +1.9% | +16.2% | 58% | 28% |
| Third+ roll | 62 | **+0.9%** | +23.7% | 61% | 32% |
| Put / breakdown short | 30 | **+11.2%** | +25.0% | 77% | 20% |
| Earnings lotto | 10 | **−14.5%** | +23.3% | 60% | 40% |
| **ALL LEGS** | **844** | **+2.3%** | **+19.9%** | **64%** | **28%** |

By **roll depth** (the cleanest signal, all legs):

| Depth | n | Mean blended | Total-loss rate |
|---|---:|---:|---:|
| 0 (initial/lotto) | 482 | **+4.4%** | 25% |
| 1 (first roll) | 218 | +0.4% | 31% |
| 2 | 64 | **−4.6%** | 33% |
| 3 | 34 | **−14.9%** | 41% |
| 4+ | 46 | +11.3% (noisy, small n) | 24% |

**The headline result.** Median trade ≈ **+20%**, but the *equal-weighted mean* is only **+2.3%**, because **28% of trades are total losses (−100%)**. This is precisely the profile you anticipated: a high "win rate" (64%) sitting on top of a fat catastrophic-loss tail. The displayed "max profit" numbers ignore both the zero-tail and the scale-out blending, which is why they overstate realised returns by roughly **30–60%** depending on category (survivorship is the larger of the two effects).

## 3. Failure-mode statistics (where the account bleeds)

| Failure mode | n | Mean blended | Total-loss rate | Verdict |
|---|---:|---:|---:|---|
| **Earnings binary lottos** | 10 | −14.5% | **40%** | Coin-flip with −100% tail |
| **Catalyst-window lottos** (FOMC/CPI/print) | 15 | **−12.0%** | **40%** | **Net negative — avoid** |
| **0DTE** (expiry = entry day) | 217 | −3.1% | 32% | Negative expectancy in aggregate |
| **Rolls beyond the 2nd** (depth ≥ 3) | 80 | ≈ 0% | 31% | Pure added variance, no EV |
| **Lottos chased when week already red** | 157 | **−4.4%** | 32% | Tilt/revenge tax |
| (contrast) Lottos when week is green | 191 | +6.9% | 25% | — |

Every documented failure mode is real in the data. The combination that does the most damage: **0DTE/index lottos taken into a binary catalyst while already down on the week.**

## 4. DTE distribution — confirms your prior

| DTE bucket | Share |
|---|---:|
| 0 (same-day expiry) | 25% |
| 1–2 | 34% |
| 3–5 | 26% |
| 6–7 | 2% |
| 8–14 | 6% |
| 15+ | 2% |
| (roll, exp inherited / n/a) | 5% |

**≈ 85–87% of all entries are 0–5 DTE.** Your prior is confirmed and then some: this is an almost-pure short-dated weekly/0DTE operation. The "days-to-weeks of patience" framing in the PDFs is not what the alert feed does.

## 5. Entry style (break vs retest) — qualitative, with caveat

The alert feed records price/strike/premium but not whether the fill came on the *break* of a level or the *retest*. Separating these rigorously requires correlating each entry to the intraday `brando-commentary` post seconds before it. From sampling that channel, his language is overwhelmingly **break-entry** ("QQQ *through* 709", "MU *through* 800 big level", "if we *break* 434 we run") — he buys strength as it punches a level, rarely waits for a pullback. A full break-vs-retest win-rate split is a documented gap (it needs the commentary-to-alert join, which I did not complete) — flagging rather than guessing.

## 6. Flow context — qualitative, with caveat

The cleanest available proxy for "active multi-day directional flow" is the **monthly regime** table below: his returns are strongly positive when a name/index is in a sustained trend and negative in chop. Per-trade flow tagging (was the underlying in active multi-day flow at entry?) again requires the commentary join and is the largest remaining quantitative gap. Directionally, the regime table (#7) is the evidence that **flow/regime is the dominant driver of the gap between his returns and follower returns.**

## 7. Regime sensitivity — the strategy is regime-conditional

Monthly equal-weighted blended return and total-loss rate (a regime proxy):

| Month | n | Mean/leg | Zero rate | | Month | n | Mean/leg | Zero rate |
|---|---:|---:|---:|---|---|---:|---:|---:|
| 2024-11 | 37 | +8% | 24% | | 2025-09 | 43 | +3% | 21% |
| 2024-12 | 77 | +10% | 25% | | 2025-10 | 31 | **−21%** | 39% |
| 2025-01 | 74 | +11% | 26% | | 2025-11 | 25 | −6% | 32% |
| 2025-02 | 51 | **−12%** | 33% | | 2025-12 | 26 | **−14%** | 38% |
| 2025-03 | 62 | −5% | 27% | | 2026-01 | 33 | +5% | 24% |
| 2025-04 | 54 | +16% | 20% | | 2026-02 | 30 | 0% | 30% |
| 2025-05 | 52 | −7% | 35% | | 2026-03 | 33 | **−14%** | 36% |
| 2025-06 | 69 | +13% | 26% | | 2026-04 | 33 | +17% | 24% |
| 2025-07 | 39 | +12% | 21% | | 2026-05 | 29 | +22% | 10% |
| 2025-08 | 46 | **−17%** | 39% | | | | | |

**Trending months print +8% to +22% per leg; choppy/down months bleed −5% to −21%,** and the total-loss rate jumps from ~22% to ~38%. The edge is not constant — it is a **trend-following / momentum-continuation edge that inverts in chop.** Any forward return estimate must be conditioned on regime.

## 8. The "monster trade" inventory (blended return > 100%)

**29 of 844 legs (3.4%)** produced a blended return over 100%. The right tail is concentrated, and it does **not** come from deep roll chains:

- **Index short-dated lottos on a trend day:** SPX 0DTE +246%, QQQ +260%/+196%, SPX +203%.
- **Early entry on a high-beta momentum name (initial or *first* roll):** META initial +298% & +280%/+184%, META roll1 +280%, TSLA roll2 +382% (one violent squeeze), COIN lotto +249%/+154%, MU lotto +189%, HOOD roll1 +205%, NVDA early rolls in the April-2025 V-bottom.

Takeaway: **the big winners are "early in a fast move," not "patiently rolled."** Only ~3 of the 29 monsters were depth-3+, and those occurred inside the two most violent trend bursts (April 2025 rebound, June 2025 run). The roll chain is *not* where the right-tail lives.

## 9. Published rules vs actual behaviour — the gap is the strategy

| Published / marketed (PDFs, pinned, marketing) | Actual behaviour (this dataset) |
|---|---|
| "Wait for A+ setups" (e.g. NVDA $50, TSLA $363) | ~**11 option alerts/week**, opportunistic intraday |
| "1–2% per trade, days-to-weeks of patience" | **85–87% are 0–5 DTE**; constant intraday rolling |
| "Max profit at highest sell" recap tables | Recaps show **winners only** (hides the 28% zeros) and **max, not blended** |
| "6–7 figure accounts" (marketing) | Shoof, candidly in Q&A: *"the goal is to flip your account to 2x"* |

The aspirational PDF ("How to Grow an Account the Right Way") describes a patient swing style that **is not the day-to-day product.** The day-to-day product is a high-frequency 0–5 DTE momentum-scalping feed. **Where the documents and the feed disagree, the feed is the real strategy.** (Published-rule wording above is drawn from your brief and the education-channel file titles; the PDFs themselves were not downloaded.)

## 10. Realistic forward-return model (Monte Carlo, blended distribution)

Bootstrap of account paths, compounding a fixed fraction `f` of equity per trade, drawing from the **blended** per-leg distribution (with the silent-loss correction). Two policies: follow-everything vs. the disciplined best subset (exclude earnings/catalyst lottos and 3rd+ rolls; cap at first roll). **These are IID, no-slippage — i.e. optimistic; see haircut below.**

**Follow EVERYTHING (~480 trades/yr; per-trade mean +2.3%, 28% zeros):**

| Size/trade | Median | P(≥2x) | P(≥3x) | P(≥5x) | Median max DD | P(lose >50%) |
|---|---:|---:|---:|---:|---:|---:|
| 5% | 1.26x | 28% | 14% | 5% | −55% | 12% |
| 10% | **0.82x** | 28% | 21% | 13% | −85% | **39%** |
| 20% | **0.04x** | 13% | 10% | 8% | −99% | **77%** |

**Disciplined BEST subset (~180 selective trades/yr; per-trade mean +8.4%, 23% zeros):**

| Size/trade | Median | P(≥2x) | P(≥3x) | P(≥5x) | Median max DD | P(lose >50%) |
|---|---:|---:|---:|---:|---:|---:|
| 2% | 1.33x | 2% | 0% | 0% | −12% | 0% |
| 5% | 1.91x | 46% | 17% | 2% | −28% | 0% |
| 10% | **2.90x** | 65% | 49% | 28% | −51% | 3% |
| 20% | 3.49x | 61% | 53% | 42% | −81% | 16% |

The two tables together are the whole story: **indiscriminate following is a wealth-destroyer at any real size; selectivity is what converts the feed into positive expectancy.**

---

# PHASE 4 — Strategic synthesis

## Layer 1 — The honest model (what actually makes the money)

**The single trade type that produces most of the realised P&L:**

> An **early, break-entry call on a high-beta momentum leader** (TSLA, META, MU, NVDA, COIN, MSTR) **— or a short-dated index call/put (QQQ/SPX) — taken while that underlying is in active multi-day directional flow, in a trending or trend-resuming regime,** entered as price punches a marked level, **scaled out in thirds within the first 1–2 sessions, with at most one disciplined roll up.**

Screenable without an alert feed:

- **Setup conditions:** underlying already trending on the daily (higher highs / reclaiming a key level), broad regime trending (SPX/QQQ above rising short-term MAs, not chopping in a range). Skip entirely in two-sided chop.
- **Instrument:** weekly call, **3–7 DTE** (not 0DTE for the core — 0DTE is −3% mean). For index, a 1–3 DTE directional call/put on a clean trend day.
- **Entry style:** **break entry** as price clears the marked level (his actual behaviour), on the leading names of the day.
- **Sizing:** treat each as 1–2% *risk* of account = roughly 5–10% *position* size (since max loss ≈ 100% of premium). Never "all-in."
- **Scale-out:** sell **1/3 into the first pop (~+30–50%)**, 1/3 on continuation, trail the last 1/3. Do not wait for "max."
- **Roll discipline:** **at most one roll up**, only with realised profits in hand. The data is unambiguous: depth-2 mean −4.6%, depth-3 −14.9%. **Stop after the first roll.**
- **Exit triggers:** level rejection, loss of the intraday trend, or end of session for short-dated. Hard time-stop — do not hold a short-dated lotto into expiry hoping.
- **Hard exclusions (each a documented net loser/coin-flip):** earnings binary lottos; lottos into FOMC/CPI/major prints; **0DTE as a core sizing vehicle**; any roll beyond the first; and **any new lotto once you are red on the week** (the tilt tax: −4.4% vs +6.9%).

What this is *not*: it is not the patient "A+ swing" of the marketing PDF, and it is not "roll forever." It is **disciplined momentum-continuation scalping with a single roll, harvested in thirds, only in trend.**

## Layer 2 — The 2x–5x year question

Stated plainly, conditioned on the corrected model. **All ranges below already assume the disciplined best-subset policy; following everything does not compound — it draws down to ruin.**

**What's possible at each target (best-subset MC, then haircut):**

| Target | Path that reaches it | Required conditions | Drawdown profile | Honest verdict |
|---|---|---|---|---|
| **2 – 2.5x** | 5–10% sizing, selective, full year | Discipline + a *net-trending* year | ~30–50% peak-to-trough | **Plausible.** The realistic base case for a disciplined, regime-aware follower. |
| **3x** | ~10% sizing, selective | ~10% sizing **and** a favourably trending regime most of the year | ~50% | **Achievable but not reliable** — needs both execution and a cooperative tape. |
| **5x** | 10–20% concentrated sizing, or an exceptional trend year | Large sizing (rule-violating per his own 1–2% guidance) **or** a once-in-cycle trend | **50–90%**, with a real 3–16% chance of losing >half the account | **A gamble, not a strategy.** |

**Where 5x stops being a strategy and becomes a gamble:** at the point you must size **>10% per trade** or stop excluding the failure modes to get there. At 20% sizing the median best-subset path is 3.5x but the 10th-percentile path is 0.30x and there's a 16% chance of a >50% loss — that is a bet on variance, not an edge being harvested.

**Three reasons the live experience is *worse* than even these tables (all push toward the low end):**
1. **Slippage / fill quality — the biggest one.** These returns assume you fill at his posted alert price on entries *and* exits. In fast 0–5 DTE names you won't; chasing a moving option after the alert can erase 20–40% of the per-trade edge. This is the principal reason follower P&L diverges from his recap tables.
2. **Regime clustering.** Bad months arrive consecutively (Feb, May, Aug, Oct, Dec 2025 were all negative). Real drawdowns are deeper and longer than the IID model shows.
3. **Execution load.** ~11 alerts/week with intraday rolls and thirds-scaling is operationally hard for anyone not at the screen full-time; missed exits convert winners into the zero-tail.

**Bottom line.** The defensible, non-soft-pedalled answer:
- **2x–2.5x is a realistic disciplined goal in a trending year** (matching Shoof's own candid "flip to 2x"). Budget for a 30–50% drawdown to get it.
- **3x is the stretch** — possible with ~10% sizing and a cooperative regime, not something to underwrite.
- **5x requires either leverage/sizing beyond his stated rules or an exceptional market** — treat any year that hits it as variance, not skill, and do not plan around it.
- **The lever that matters is selectivity, not aggression.** The edge lives almost entirely in: early momentum entries in trends, harvested in thirds, capped at one roll, with the failure modes hard-excluded. Add sizing only after that discipline is proven.

---

## Scope, confidence, and open items

- **Fully quantified:** Brando's option alert feed (844 legs / 489 campaigns, ~18.5 months). High confidence in the taxonomy, return distribution, failure modes, DTE, regime, and monster inventory.
- **Saturation:** the strategy's *form* is unchanged across the entire window — Nov 2024 alerts are structurally identical to May 2026 (same names, same 0–5 DTE weeklies, same buy-the-break / scale-in-thirds / roll-once mechanics). Extending further back would add sample, not new strategy.
- **Not separately quantified (documented gaps):**
  - **Shoof's alert feed** — structurally the same instrument/format; not run through the engine separately here (scope/time). Worth a follow-up if you want a two-trader comparison.
  - **Per-trade break-vs-retest split (#5)** and **per-trade active-flow tagging (#6)** — both require joining each alert to the `brando-commentary` post immediately preceding it; addressed qualitatively, not quantitatively.
  - **Weekly recap images (`trade-log`)** — his published "max profit" tables are screenshots; not OCR'd here. They would let me quantify the exact displayed-vs-blended overstatement per week, but the mechanism (survivorship + max-vs-blended) is already established from the alert data.
  - **Education PDFs** — published-rule wording taken from your brief + channel file titles, not from downloading the PDFs.
- **Known data caveat:** `brando_trades_per_leg.csv` = 802 of 844 legs (winner-biased); canonical stats are in this document.
