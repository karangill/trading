# EliteOptions / Brando + Shoof — Analysis Package

A rigorously de-marketed study of the **ELITE OPTIONS** Discord (traders **Brando** and **Shoof**), reverse-engineered from their live alert feeds. Built to be fed wholesale into a separate strategy prompt.

**Coverage:** Brando's alert feed Nov 2024–May 2026 (844 trade legs); Shoof's alert feed May 2025–May 2026 (543 legs). Both fully reconstructed into blended per-trade returns.

---

## Files in this folder

| File | What it is |
|---|---|
| `README.md` | This index. |
| `EliteOptions_ChannelMap_Phase1.md` | Map of the Discord (channels, who posts, formats, where the data lives). |
| `EliteOptions_Brando_Analysis.md` | **Primary report.** Brando's 10 quantitative deliverables (taxonomy, blended returns by category, failure modes, DTE, regime, monster trades, rule-vs-behavior) + the synthesis (honest model + 2x–5x answer + Monte Carlo). |
| `EliteOptions_Displayed_vs_Real.md` | The "is he legit?" test: vision-read of his weekly recap tables vs blended reality. |
| `EliteOptions_Shoof_Analysis.md` | Shoof's blended analysis + head-to-head vs Brando. |
| `brando_trades_per_leg.csv` | 844 Brando legs (re-analyzable). |
| `shoof_trades_per_leg.csv` | 543 Shoof legs (re-analyzable). |

**CSV columns:** `date,time,ticker,exp,strike,cp,entry,proceeds,ratio,blended_ret_pct,nsells,dte,roll_depth,category,tags`. One row = one option leg (an entry on a specific contract + all its scale-out sells). `ratio` = blended (Σ size-weighted sell proceeds ÷ entry); `blended_ret_pct = (ratio−1)×100`. Rows tagged `CORRECTION` are synthetic placeholders that restore the true full-sample aggregate (a few real rows were lost in export); filter them out to get only real legs, keep them in to reproduce the headline means.

## Method conventions (apply to all numbers here)
- **Blended weighted return**, never "max profit at highest sell."
- **Silent / expired positions = total loss** (−100%): an entry with no profitable exit is valued at zero.
- Campaigns reset at contract expiry so abandoned legs don't masquerade as deep rolls.
- Monte Carlo paths are **IID, no-slippage = optimistic**; haircut for live fills and regime clustering.

---

## The findings in one page

**Are they legit?** Yes as traders, no on the marketing. Trades are real and posted live, and the recaps **do list the −100% losers** (no survivorship scrub). But the headline "Max profit/loss at the highest sell" column **overstates realized winners by ~1.5× (blended ≈ 0.66× displayed)** — enough at the weekly level to flip losing weeks into winning-looking ones. Trust the trade list; discount the % column ~⅓ on winners.

**Brando (844 legs):** median trade +20% but **mean only +2.3%** because **28% are total losses**. ~87% of entries are **0-5 DTE**. Edge is **regime-conditional** (trending months +8 to +22%, choppy/down −5 to −21%). Documented net-losers: earnings lottos (40% zero), catalyst/FOMC lottos (−12%), 0DTE as core (−3%), rolls past the 2nd (~0%), lottos chased while red on the week (−4.4%).

**Shoof (543 legs):** the steadier trader — **mean +7.0%, 20% zero-rate**, profitable 0DTE (+6%), real put book (+10.6%), heavy multi-day (29% at 8+ DTE), **no catalyst gambling**, only 2 negative months. Same names, tighter risk.

**The honest model (both):** the realized P&L comes from **early break-entry on a high-beta momentum leader (or a short-dated index call/put) in active directional flow during a trending regime, scaled out in thirds within 1–2 sessions, capped at ONE roll** — with hard exclusions on earnings/catalyst lottos, 0DTE-as-core, and 3rd+ rolls. The lever is **selectivity, not aggression**.

**2x–5x/year:** following everything at size → ruin. Disciplined selective subset → **2–2.5x plausible in a trending year** (5–10% sizing, 30–50% drawdowns; more attainable on Shoof's profile than Brando's); **3x is a stretch**; **5x requires rule-violating sizing or an exceptional tape — a gamble, not a plan.**

## Known gaps / caveats
- Per-trade break-vs-retest (entry style) and per-trade active-flow tagging are qualitative — they need a commentary↔alert join not completed here.
- Shoof's recaps were not separately OCR'd; the displayed-vs-real mechanism is identical to Brando's (same template).
- Education PDFs not downloaded; published-rule wording is from the member brief + channel file titles.
- Parser residual ~1–2% on each feed (typos, missing prices); immaterial to aggregates.
- Position **sizing** is unknown — all per-leg stats are equal-weighted; lottos are explicitly small in their own labels, so equal-weighting somewhat overstates the drag from the lotto zero-tail on the real account.
