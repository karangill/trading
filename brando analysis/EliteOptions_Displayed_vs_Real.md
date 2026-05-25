# Brando's published track record vs. blended reality — the displayed-vs-real test

**Question:** is the EliteOptions/Brando track record legit, or inflated/scammy?
**Method:** vision-read his weekly `trade-log` recap images and compare his published per-trade numbers, line-by-line, against the blended (size-weighted scale-out) return — using his *own* listed exits, so there's no dispute about the inputs.
**Sample:** 3 weeks, ~30 option trades, across a strong month and a choppy/down month. Prepared 2026-05-24.

---

## What his recap actually reports

Each weekly recap is a clean table with columns: *Date · Ticker/strike · Time of alert · Chart setup · Entry · Exit · **Max profit/loss at the highest sell** · Notes.*

The headline percentage column is, by his own label, **"max profit/loss at the highest sell"** — i.e. **(highest sell price ÷ entry) − 1**, applied to the *whole* position. But the Exit column shows he actually **scaled out** (e.g. ½ here, ¼ there). So the headline number is the return you'd have gotten only if you'd sold 100% at the single best tick — not what you (or he) actually realized scaling out.

**Two things this test settled — one in his favor, one against:**

### Finding 1 (in his favor): he does NOT hide the losers
This was my prior suspicion and it is **wrong**. In every week sampled — including the ugly ones — the **−100% total losses are listed right in the table** (UNH, TSLA, MU, AMD, SPX, PLTR, etc., all shown at −100%). Across the 30 trades, **12 were −100% and all 12 were displayed.** There is no survivorship scrub of the zero-tail. Credit where due: that is more honest than the typical paid-Discord recap.

### Finding 2 (against): the headline % systematically overstates realized returns
"Highest sell" vs. blended, on the **18 winning trades** sampled:

| | Displayed ("highest sell") | Blended (his own scale-outs) |
|---|---:|---:|
| Average winner | **+69.7%** | **+45.7%** |

**Blended ≈ 0.66× of displayed.** The headline overstates a typical winner by **~50%** (about +24 percentage points). The gap widens the more aggressively he scales out early and the higher the final tick spikes.

---

## Line-by-line examples (his exits → his number vs. the real one)

| Week | Ticker | Entry | His listed exits | His displayed | **Blended (real)** |
|---|---|---:|---|---:|---:|
| 8/20 | QQQ 565C | 2.11 | 2.84(½), **1.50(½)** | +34.6% | **+2.8%** |
| 8/15 | META 790C | 2.90 | 4.00(½), 4.40(¼), 6.10(¼) | +110.3% | **+59.5%** |
| 8/20 | QQQ 565P | 2.75 | 3.80(½), 4.40(¼), 5.50(¼) | +100.0% | **+59.1%** |
| 8/22 | SPX 6470C | 6.00 | 9.40(½), 10.50(¼), 13.40(¼) | +123.3% | **+77.9%** |
| 5/18 | QQQ 705P | 4.93 | 6.50(½), 7.10(¼), 8.13(¼) | +64.9% | **+43.2%** |
| 8/11 | BMNR 65C | 3.80 | 6.00(½), 6.70(¼), 9.00(¼) | +136.8% | **+82.2%** |

The QQQ 565C row is the cleanest illustration: he sold half at 2.84 and **half at 1.50 (a loss on that tranche)** — the real blended return is **+2.8%**, but it's published as **+34.6%** because one tranche briefly tagged 2.84.

---

## Weekly aggregate — the gap is big enough to change the story

Equal-weighted across every trade in the week (winners and the −100% losers he shows):

| Week | Regime | Displayed avg | **Blended avg** | Effect |
|---|---|---:|---:|---|
| 5/18–5/22 (2026) | up month, choppy week | −24.3% | **−31.7%** | both negative |
| 8/18–8/22 (2025) | down month | **+8.2%** | **−7.2%** | **flips losing week → winning-looking** |
| 8/11–8/15 (2025) | down month, up week | +23.4% | **+5.0%** | displayed ≈ 4–5× the real result |

The "highest sell" framing doesn't just pad winners — in the 8/18 week it **turns a −7% blended week into a +8% displayed week.** A prospective member reading the recaps sees a materially rosier, smoother equity curve than the blended reality.

---

## Verdict: legit trader, honest about losses, dishonest *headline math*

- **Not a scammer in the fraud sense.** The trades are real and posted live; the recaps even list the total losses. There's no fabricated track record and no hidden zero-tail.
- **But the published returns are systematically inflated by the "max-at-highest-sell" convention** — roughly **1.5× the realized blended return on winners**, and enough at the weekly level to flip down weeks into up-looking ones. This is the standard way trading services flatter a track record without technically lying: report the best exit, not the weighted one.
- **Practical read for you:** trust his *trade list* (entries, exits, that he shows losers), discount his *percentage column* by ~⅓ on winners, and never expect to realize the headline number — you can't sell your whole position at the single best tick, and slippage on a live feed widens the gap further.

**This refines the main analysis.** In `EliteOptions_Brando_Analysis.md` I attributed the ~30–60% overstatement mostly to survivorship; this test shows survivorship is *not* the mechanism (he shows the zeros) — it's almost entirely the **highest-sell-vs-blended** convention, measured here at **blended ≈ 0.66× of displayed on winners.** My independent blended reconstruction matched his listed exits to the cent on every trade checked, which also validates the per-leg dataset.

*Caveat: 3-week / ~30-trade sample, hand-verified. The pattern is highly consistent across regimes; a larger sample would tighten the 0.66× factor but is unlikely to change the conclusion. Not financial advice.*
