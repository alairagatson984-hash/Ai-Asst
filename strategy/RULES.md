# Trading Rules

The rules Claude grades every setup against. If a setup doesn't pass these, the answer is **no trade**. A day with no trade is a normal result. The goal is evidence-based opportunities, not a trade idea every day.

## Market and schedule
- **Pairs:** EUR/USD, GBP/USD, USD/JPY, USD/CHF, AUD/USD, USD/CAD, NZD/USD (the 7 majors).
- **Time zone:** Pacific (PT). All times below are PT.
- **Trading window:** London/New York overlap, starting **6:00am PT**. No fixed end time.
- **Setup expiry:** every setup expires at **2:00pm PT** (end of the NY day).
- **Days:** Monday–Friday.
- **Asian range:** high/low from **4:00pm–11:00pm PT** (the previous evening). Used as a level.
- **London range:** high/low from **1:00–6:00am PT** (4:00–9:00am ET). Used as a level, with its own rules below.

## Direction
- From support/resistance only. No higher-timeframe bias filter.

## Timeframes
- **H1 and M15:** find the important swing levels and S/R.
- **M5:** confirm the market structure break.
- Chart patterns (H&S, double top/bottom, flags) are read on **M15 and H1**.

## Entry model: break and retest
A setup is scored on 6 evidence checks (the 6th was added 2026-11-06):

1. **Close beyond:** a candle body closes beyond the S/R level.
2. **Displacement:** the break is a strong, full-bodied candle, not a slow drift.
3. **Follow-through:** the next candle(s) keep going instead of snapping back inside.
4. **M5 structure break:** price takes out the most recent M5 swing in the break direction.
5. **Retest holds:** price comes back to the level and rejects it from the other side.
6. **EMA + RSI agree** (read on M15; EMA 20, EMA 50, RSI 14 with 70/30 levels). Both must hold:
   - **EMA trend:** the EMA 20 is on the trade side of the EMA 50 (below it for shorts, above it for longs), and price is on the trade side of the EMA 20. This avoids buying into a downtrend or selling into an uptrend. A fresh EMA 20 crossover in the trade direction also passes.
   - **RSI room:** RSI is not already exhausted against the trade. For a short, RSI is not below 30 (oversold) at the retest. For a long, RSI is not above 70 (overbought). If RSI is turning back out of the zone against the trade, the check fails.
   - If the indicators aren't visible on the screenshot, mark it `false` and say why.

Plus the **candle trigger** at the retest. One of:
- **Engulfing** (bullish for longs, bearish for shorts)
- **Pin bar / rejection wick** into the level, closing back on the break side

## Grades
| Grade | Evidence checks | Candle trigger | Shown as |
|---|---|---|---|
| **A** | 6 of 6 | Required | Trade |
| **B** | 5 of 6 | Required | Trade (lower confidence) |
| **C** | Anything else (4 or fewer, or no candle trigger) | — | Watchlist only |

- If a break fails (price closes back through the level) before 2:00pm PT, the setup is **downgraded to C**.

## Stops, targets and R:R
- **Stop loss:** 2–3 pips beyond the retest swing.
- **Take profit:** the next S/R level.
- **Minimum R:R is 1:2.** If the next S/R gives less than 1:2, it's not a trade.
- Opportunities are **ranked by R:R** (highest first).
- **Management:** set and forget. No moving the SL, no partials.

## London range breakout
Adapted from the *NQ London Breakout* checklist and applied to the 7 majors. The London range is a level like any other: the entry, grading (6 checks + candle trigger) and stop follow the rules above. On top of that:
- **Range:** the highest high and lowest low of the M5 candles from **1:00–6:00am PT** (4:00–9:00am ET).
- **Breaks count only from 6:30am PT** (9:30am ET, the US stock open). A break before 6:30am PT doesn't count. The break must be fresh: an M5 candle closing beyond the London high or low after 6:30am PT, with the previous candle closing inside the range.
- **One London trade per pair per day.** Whichever side breaks first is that day's direction, win or lose. The other side is ignored for the rest of the day.
- **Entry:** the usual break and retest, graded A/B/C as normal.
- **Stop loss:** 2–3 pips beyond the most recent swing (the retest swing): below it for longs, above it for shorts.
- **Take profit:** a fixed **2:1** (entry ± 2 × risk) for this pattern, instead of the next S/R.
- **Expiry:** 2:00pm PT, like every other setup.
- The range isn't finished until 6:00am PT, after the morning plan. The dashboard's **Today's Plan** works it out live from OANDA and shows which side broke first.

## Risk
- **2% of the account per trade.** Position size = (balance × 2%) ÷ (SL distance in price × pip value).
- **Daily loss limit: −4%** of the account, counting **closed losses only**. Once it's hit, no new setups for the rest of the day.

## News filter
High-impact news is a **filter, not a buy/sell signal**.
- Any red-folder event on either currency of a pair **blocks** new entries on that pair before the release.
- After the release, a setup can **requalify** if the break-and-retest still holds by the rules above.
- US data often comes out at 5:30am PT, right before the window. Always check it.
