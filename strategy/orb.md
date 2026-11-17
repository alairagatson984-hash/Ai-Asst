# 9:30 Opening Range Breakout (ORB)

A separate, fully automatic strategy that runs on the dashboard's **Opening Range** tab. It isn't graded A/B/C and doesn't use the morning plan: the page works it out from live OANDA candles.

## Rules
- **Pairs:** the 7 majors (EUR/USD, GBP/USD, USD/JPY, USD/CHF, AUD/USD, USD/CAD, NZD/USD).
- **Time zone:** all times are shown in **Pacific (PT)**. The opening candle is the US open, 9:30am ET, which is always **6:30am PT** (both follow daylight saving together).
- **Opening range:** the 6:30–6:35am PT (9:30–9:35am ET) **M5 candle**. It is set only once that candle has fully closed. Its high and low are the range.
- **Breakout:** a later M5 candle **closes** above the range high (**BUY**) or below the range low (**SELL**). A wick through the line without a close outside does **not** count.
- **Trade 1:** whichever side closes outside first. No new trade-1 signals from candles that close after the cutoff (default **11:00am PT**, set in Pacific time).
- **Trade 2 (re-entry):** allowed only **after trade 1 has closed** (hit its stop or target).
  - The next **3 M5 candles** after the one that closed trade 1 form a **new consolidation range** (their high and low). The number of candles is set in Settings.
  - Trade 2 is the first M5 candle that **closes** outside the new range, either side. Its stop and target use the same settings, measured from the new range.
  - Trade 2 can trigger until setups expire (**2:00pm PT**).
  - Because the new range only starts after trade 1 closes, trade 2 can never be taken on the same breakout as trade 1.
- **Maximum two trades per pair per day.**
- **Entry:** the breakout candle's close.
- **Stop loss** (Settings → Opening Range Breakout):
  - *Opposite side of range* (default): BUY stop at the range low, SELL stop at the range high.
  - *Middle of range*.
  - *Fixed pips* from entry.
- **Take profit:** entry ± **2 × risk** by default (the multiple is configurable). R:R is shown on every signal.
- **Position size:** your normal risk % of the OANDA balance.
- **Outcome:** after each signal, the card tracks whether the stop or target was touched first. A candle that touches both counts as the stop.
- **Reset:** everything is recomputed from that day's candles, so it starts fresh at each day's 6:30am PT open. It's off on weekends.

## What it doesn't do
- It doesn't place trades. Signals only.
- It doesn't apply the news filter or the daily loss limit. Check those yourself before acting on a signal.
