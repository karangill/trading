# EliteOptions / Shoof — blended-return analysis (and Brando comparison)

**Dataset:** `shoofs-trade-alerts` (the `Elite Options | Shoof` APP bot, posted as embeds), May 9 2025 → May 21 2026 (~12.5 months, full channel).
**Sample:** 1,661 parsed alerts → **543 reconstructed trade legs** across **380 campaigns**.
**Method:** identical engine to the Brando study — blended weighted returns, silent/expired positions = total loss, campaign reset at expiry. See `EliteOptions_Brando_Analysis.md` §0 for methodology.
**Companion file:** `shoof_trades_per_leg.csv` (CORRECTION-tagged rows restore the true aggregate).

---

## Headline: Shoof is the steadier, better-risk-managed trader

| Metric (blended) | **Shoof** | Brando | Read |
|---|---:|---:|---|
| Legs analyzed | 543 | 844 | Brando trades ~50% more |
| **Mean blended return / leg** | **+7.0%** | +2.3% | Shoof's edge per trade is ~3× |
| Median blended return | +22.0% | +19.9% | similar typical winner |
| Win rate | 65% | 64% | same |
| **Total-loss (−100%) rate** | **20%** | 28% | Shoof blows up far less often |
| Trades >100% (monsters) | 20 (3.7%) | 29 (3.4%) | same right-tail frequency |

Same median winner, but Shoof keeps **~8 percentage points more of the zero-tail off the books** — and that is the whole difference between a +2.3% and a +7.0% per-trade expectancy. The gap traces almost entirely to **instrument selection** (below).

## Why Shoof's tail is smaller — instrument & style

| | Shoof | Brando |
|---|---:|---:|
| 0-5 DTE share of entries | ~64% | ~87% |
| 8+ DTE (multi-day swing) share | **29%** | ~2% |
| 0DTE blended mean | **+6.1%** (profitable) | −3.1% (negative) |
| Catalyst (FOMC/CPI) lottos | **0 tagged** | net −12%, 40% zero |
| Earnings lottos | 3 (negligible) | 10, median −100% tail |
| Puts / breakdown trades | 53 legs, **+10.6% mean, +39.9% median** | 30 legs, +11.2% mean |

Shoof spreads across **3–7 DTE and multi-day swings**, trades a real **put book** (SPX/QQQ breakdowns + single names — his best-performing category by median), is **profitable even on 0DTE**, and **does not gamble catalysts**. Brando is a near-pure 0DTE/weekly momentum-roller. Same names (TSLA, META, COIN, MSTR, NVDA, AVGO, MU, CRWV, ARM), different risk envelope.

## Blended return by category (Shoof)

| Category | n | Mean | Median | Win | Zero |
|---|---:|---:|---:|---:|---:|
| Multi-day swing (8+ DTE)* | 155 | **+12.6%** | +23.6% | 68% | 17% |
| Initial (momentum entry) | 206 | +11.7% | +23.6% | 67% | 15% |
| Put / breakdown | 53 | +10.6% | +39.9% | 70% | 19% |
| Roll 2 | 17 | +9.3% | +21.5% | 76% | 24% |
| 0DTE* | 115 | +6.1% | +26.7% | 67% | 23% |
| First roll | 117 | +3.5% | +22.4% | 63% | 26% |
| Lotto | 137 | +1.3% | +16.7% | 62% | 22% |
| Third+ roll | 14 | **−5.2%** | +8.6% | 57% | 36% |

*\*DTE buckets overlap the category column; shown for comparison with Brando.*

**Same roll-depth lesson as Brando:** edge is in the initial entry and (modestly) the first roll; **rolls beyond the 2nd are negative (−5.2%)**. Cap rolls at one — true for both traders.

## Regime sensitivity — much steadier than Brando

Monthly blended mean / total-loss rate:

| Month | n | Mean | Zero | | Month | n | Mean | Zero |
|---|---:|---:|---:|---|---|---:|---:|---:|
| 2025-05 | 32 | +14% | 25% | | 2025-12 | 38 | **−15%** | 29% |
| 2025-06 | 49 | +14% | 18% | | 2026-01 | 48 | +4% | 15% |
| 2025-07 | 49 | +2% | 24% | | 2026-02 | 34 | +2% | 15% |
| 2025-08 | 47 | +11% | 19% | | 2026-03 | 32 | +1% | 22% |
| 2025-09 | 52 | +9% | 21% | | 2026-04 | 44 | +22% | 14% |
| 2025-10 | 61 | −3% | 25% | | 2026-05 | 23 | +19% | 13% |
| 2025-11 | 34 | +17% | 15% | | | | | |

Only **2 negative months** (Oct −3%, Dec −15%) vs Brando's 7, and Shoof's worst month (−15%) is shallower than Brando's worst (−21%). His multi-day/put exposure cushions the choppy stretches that wreck a pure-0DTE book.

## Monster trades (blended > 100%)

20 legs. Same sources as Brando — early entries on high-beta momentum names plus the occasional SPX 0DTE on a trend day: COIN +352%, AVGO +228%, SPX 0DTE +169%/+137%, AMZN +195%, CRWV +145%, TSLA squeeze rolls +157%/+140%, NFLX +112%, MSTR +113%, SBET/MDB small-cap runners ~+110%. The right tail is **"early in a fast move," not deep rolls** — identical conclusion to Brando.

## Displayed-vs-real note

Shoof posts the **same weekly recap template** in `trade-log` ("Max profit/loss at the highest sell"), so the **same ~1.5× headline inflation on winners documented for Brando applies to Shoof's published numbers** (see `EliteOptions_Displayed_vs_Real.md`). I did not separately OCR Shoof's recaps; the mechanism (highest-sell vs blended) and his per-trade scale-outs are identical in structure. My blended reconstruction is the de-inflated number.

## Bottom line

If you were going to follow one of the two **mechanically**, Shoof is the lower-variance, higher-expectancy choice: he avoids the three things that bleed Brando's account (0DTE-as-core, catalyst lottos, deep rolls) and carries a genuine multi-day + put book. The honest model and the 2–5x math in `EliteOptions_Brando_Analysis.md` Layer 1/2 apply to Shoof too, shifted favorably: with a +7% (vs +2.3%) per-leg mean and a 20% (vs 28%) zero-rate, the disciplined-subset 2–2.5x case is more attainable and the drawdowns shallower — but 5x is still a sizing/regime gamble, not a plan.

*Caveats: ~1% parser residual (a few `BOUGH` ticker artifacts / missing prices), same silent-loss conventions as Brando, IID/no-slippage where modeled. Not financial advice.*
