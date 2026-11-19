# Daily Review (Mon–Fri, ~2:15pm PT)

Setups expire at 2:00pm PT. This review is written afterwards, without input from the user.

1. Open today's `docs/data/days/YYYY-MM-DD.json`. If there's no file, there was no plan: stop.
   - **No-trade days still get a review.** With no setups, review the watchlist and levels instead: did any pair later break and retest by the rules (and what grade would it have been)? Was standing aside the right call? `planVsOutcome` is then an empty list.
2. For each setup, work out what price did after the plan (web search or the user's notes). Was the entry retested? Did it hit the TP or the SL first? Did it expire untouched? Did the break fail?
   - This sandbox can't reach OANDA, so actual fills come from the dashboard's Journal tab (the user's browser), which the user sends as a pasted block (see below). If they haven't sent it yet, review against price only, say so, and leave `review.trades` as an empty list.
3. Fill `review`:
   - `writtenAt`: the current time in PT.
   - `planVsOutcome`: one entry per setup: `{ "setupId", "result" (plain sentence), "r" (number or null) }`.
   - `mistakes`: a **list** of exactly these three checks, each starting with its label and a Yes/No answer, then which trades and why:
     - `"Late entry: Yes/No. …"`: entered more than 15 minutes after the signal or retest, or chased price away from the entry.
     - `"Closed by hand: Yes/No. …"`: closed a trade manually instead of letting the stop or target hit.
     - `"Followed my entry and retest rules: Yes/No. …"`: entered on the close and retest as the rules say, with the stop and target in place. Put every other rule break here (no stop, moved stop, slippage, a trade not from the plan or the Opening Range).
     - With no trades that day, answer each with `"No trades taken."`
   - `lessons`: a **list** of exactly these three, each starting with its label:
     - `"Repeat: …"`: what went right today that should be done again.
     - `"Improve tomorrow: …"`: the one or two things to fix for the next session.
     - `"Most profit: …"`: how to get the most out of the setups, for example which pair, setup or grade paid best, whether letting winners reach the full target or skipping weaker setups would have made more, in R. Base it on today's trades and signals, not on hindsight entries the rules didn't give.
   - `planVsOutcome`, `mistakes` and `lessons` must be JSON lists (`[...]`), never a single string. Only `gradingAudit` is a plain string.
   - `gradingAudit`: did the A/B/C grades hold up? Name anything that should have been graded differently, and why.
4. Validate the JSON, commit as `Review for YYYY-MM-DD`, and push to `main`.

## Trades the user took (pasted from the dashboard)
The user sends their trades by pasting a block that starts with **"TruLux trades for review: YYYY-MM-DD (PT)"**, copied from the Journal's *Copy trades for review* button. It can arrive in the review session after the 2:15pm review, or in any chat. When it does:
1. Open that day's `docs/data/days/YYYY-MM-DD.json`. Create a minimal day file (verdict "Calendar only", empty lists) if there isn't one, and add the date to `docs/data/index.json`.
2. Set `review.trades` to one entry per trade in the block, as a **list**:
   `{ "time": "6:42am PT", "trade": "EUR/USD BUY", "source": "Opening Range T1" | "Plan s1" | "Not from the plan or ORB", "grade": "A" | "B" | "C" | null, "r": number or null, "note": "one plain sentence" }`.
   The grade is the execution grade from the block (ORB trades) or the setup's grade (plan trades). The note says what was done well or badly, against the signal or plan.
3. Fold them into the rest of the review:
   - `mistakes`: answer the three checks above (Late entry, Closed by hand, Followed my entry and retest rules) from the pasted trades, naming the trades.
   - `lessons`: Repeat / Improve tomorrow / Most profit, as above, from the pasted trades.
   - `gradingAudit`: one or two sentences on execution: how many A/B/C, net R.
   - For plan setups, fill `planVsOutcome` from the real fills where you can.
4. If there's no review yet, write the full review as above, using the pasted trades. If there is one, only update those fields and keep the rest.
5. Use only what's in the block: R and pips. Never add dollar amounts, balances, units or account IDs (the repo is public). Validate the JSON, commit as `Review trades for YYYY-MM-DD` and push to `main`.

Never commit screenshots, account IDs, balances or tokens.
