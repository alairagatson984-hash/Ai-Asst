# Daily Review (Mon–Thu, ~2:15pm PT)

Setups expire at 2:00pm PT. This review is written afterwards, without input from the user.

1. Open today's `docs/data/days/YYYY-MM-DD.json`. If there's no file, there was no plan: stop.
2. For each setup, work out what price did after the plan (web search or the user's notes). Was the entry retested? Did it hit the TP or the SL first? Did it expire untouched? Did the break fail?
   - This sandbox can't reach OANDA, so actual fills come from the dashboard's Journal tab (the user's browser). If the user shared results, use them; otherwise review the setups against price only and say so.
3. Fill `review`:
   - `writtenAt`: the current time in PT.
   - `planVsOutcome`: one entry per setup: `{ "setupId", "result" (plain sentence), "r" (number or null) }`.
   - `mistakes`: rule breaks or execution problems. "None" is fine.
   - `lessons`: one or two takeaways tied to a pattern or check.
   - `gradingAudit`: did the A/B/C grades hold up? Name anything that should have been graded differently, and why.
4. Validate the JSON, commit as `Review for YYYY-MM-DD`, and push to `main`.

Never commit screenshots, account IDs, balances or tokens.
