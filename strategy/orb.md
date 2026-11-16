# 9:30 Opening Range Breakout (ORB)

A separate, fully automatic strategy that runs on the dashboard's **9:30 ORB** tab. It isn't graded A/B/C and doesn't use the morning plan: the page works it out from live OANDA candles.

## Rules
- **Pairs:** the 7 majors (EUR/USD, GBP/USD, USD/JPY, USD/CHF, AUD/USD, USD/CAD, NZD/USD).
- **Time zone:** Eastern Time (ET), so it follows US daylight saving automatically. 9:30am ET is 6:30am PT.
- **Opening range:** the 9:30–9:35am ET **M5 candle**. It is set only once that candle has fully closed. Its high and low are the range.
- **Breakout:** a later M5 candle **closes** above the range high (**BUY**) or below the range low (**SELL**). A wick through the line without a close outside does **not** count.
- **One signal per pair per day:** whichever side closes outside first. No new signals from candles that close after the cutoff (default **11:00am ET**).
- **Entry:** the breakout candle's close.
- **Stop loss** (Settings → 9:30 ORB):
  - *Opposite side of range* (default): BUY stop at the range low, SELL stop at the range high.
  - *Middle of range*.
  - *Fixed pips* from entry.
- **Take profit:** entry ± **2 × risk** by default (the multiple is configurable). R:R is shown on every signal.
- **Position size:** your normal risk % of the OANDA balance.
- **Outcome:** after a signal, the card tracks whether the stop or target was touched first. A candle that touches both counts as the stop.
- **Reset:** everything is recomputed from that day's candles, so it starts fresh at each day's 9:30am ET open. It's off on weekends.

## What it doesn't do
- It doesn't place trades. Signals only.
- It doesn't apply the news filter or the daily loss limit. Check those yourself before acting on a signal.
