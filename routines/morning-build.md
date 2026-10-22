# Morning Build (Mon–Thu, plan ready by 5:45am PT)

Follow this when the user sends their marked TradingView screenshot (~5:00am PT).

1. **Read the rules.** Open `strategy/RULES.md` and `strategy/patterns.md`. Grade only against them.
2. **Calendar.** Search the web for today's high-impact (red-folder) events for USD, EUR, GBP, JPY, CHF, AUD, CAD and NZD. Convert times to PT. Only high impact.
3. **Read the screenshot.** List every S/R level the user marked, with its pair, price and timeframe (H1/M15). Note the Asian range (4:00–11:00pm PT) high/low if relevant.
4. **Look for setups.** For each pair, check whether a level has been broken and is being retested. Score the 5 checks honestly (close beyond, displacement, follow-through, M5 structure break, retest holds) and whether there's an engulfing or pin-bar trigger. If the screenshot can't show a check, mark it `false` and say why in `notes`.
5. **Price it.**
   - Entry: the retest.
   - SL: 2–3 pips beyond the retest swing.
   - TP: the next S/R level.
   - Under 1:2 R:R → not a trade. Put it on the watchlist with the reason.
6. **News.** For each setup, set `news.status` to `clear`, `blocked` (an event hasn't been released yet) or `requalified` (an event came out and the retest still holds).
7. **Verdict.** A headline and one or two plain sentences. "No trade today" is a normal answer. When there are no setups, fill `newsBlocks` and `watchFor` so the user knows what would change that.
8. **Write the file.** `docs/data/days/YYYY-MM-DD.json` (schema below), then add the date to `docs/data/index.json`. Remove the example day (`2026-10-22`) from the index the first time a real plan is written.
9. **Check and push.** Validate the JSON, commit as `Plan for YYYY-MM-DD`, and push to `main`. The site picks it up within about a minute (GitHub Pages) or 5 minutes (page auto-refresh).

Never commit screenshots, account IDs, balances or tokens. The repo is public.

## Day file schema
```json
{
  "date": "YYYY-MM-DD",
  "updatedAt": "YYYY-MM-DDTHH:MM:SS-07:00",
  "verdict": { "headline": "…", "reason": "…" },
  "calendar": [{ "time": "05:30", "currency": "USD", "event": "…", "impact": "high" }],
  "levels": [{ "id": "eu-1", "pair": "EUR_USD", "price": 1.123, "tf": "H1", "label": "H1 support (broken)" }],
  "setups": [{
    "id": "s1", "pair": "EUR_USD", "direction": "short",
    "pattern": "clean-br | asian-range | head-shoulders | double-top-bottom | flag-pennant",
    "levelId": "eu-1", "tpLevelId": "eu-2",
    "entry": 1.1228, "sl": 1.1243, "tp": 1.119,
    "checks": { "close": true, "displacement": true, "followThrough": true, "structure": true, "retest": true },
    "trigger": { "type": "engulfing | pinbar", "note": "…" },
    "news": { "status": "clear | blocked | requalified", "note": "…" },
    "notes": "…"
  }],
  "watchlist": [{ "pair": "GBP_USD", "level": 1.34, "missing": "…" }],
  "newsBlocks": ["…"],
  "watchFor": ["…"],
  "review": null
}
```
The page works out the grade itself (A = 5/5 + trigger, B = 4/5 + trigger, otherwise C). Leave `trigger` out when there is none.
