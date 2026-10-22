# Ai-Asst

TruLux Analytics: a personal London/NY-overlap forex dashboard. Claude updates it every trading morning with evidence-graded break-and-retest setups on the 7 majors.

**Live site:** https://alairagatson984-hash.github.io/Ai-Asst/

## Tabs
- **Today's Plan**: verdict, A/B setup cards with live status and 2% position sizes, C watchlist, red-folder events.
- **Markets**: live majors, 28-pair currency strength since the Asian open, an OANDA chart with your editable levels, the economic calendar.
- **Calculator**: units and lots at your risk %, R:R check, room left before the daily limit.
- **Journal / Analytics**: your OANDA practice trades, auto-matched to the plan, with stats by grade, pattern, pair and discipline.
- **Patterns**: the 7-pattern playbook with your stats.
- **Daily Review**: Claude's write-up after setups expire.
- **Settings**: OANDA practice token (saved in your browser only), risk rules, session times.

## Files
- `docs/`: the site (GitHub Pages serves `main` from `/docs`).
- `docs/data/days/`: one JSON file per trading day, written by Claude. `docs/data/index.json` lists them.
- `strategy/RULES.md`, `strategy/patterns.md`: the rules every setup is graded against.
- `routines/`: the morning-build and daily-review checklists Claude follows.
- `reference/`: the design references.

The repo is public. Tokens, account IDs, balances and screenshots are never committed.
