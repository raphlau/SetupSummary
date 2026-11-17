---
name: money-review
description: My money maths from my bank data: spending against my budgeting rule, free to spend until payday, the year view, low-balance and spending alerts. Use for any spending or saving question and in my routines.
---

# Money review (outline)

My scripts are in a private repo, so this is the shape of the skill rather than something you can run as is. Build your own scripts with Claude first (in a chat with the repo attached), with tests on made-up data, then write the skill around them.

## The rule that matters
<YOUR RULE, e.g. "I keep at least X% of what comes in each pay cycle">. A pay cycle runs from one payday to the day before the next. Every report leads with the verdict against this rule, in pounds, and gives the year to date as one net figure.

## Where things live
- **Scripts**: `money/fetch.py` (pulls from the bank aggregator's API), `money/ingest.py` (checks and maps rows), `money/money.py` (the maths) in <OWNER>/<REPO>, with `money/README.md` and tests. Never real data in the repo.
- **Rules note**: categories, regular payments, expected transfers and paydays, in `Notes/Claude/Topics/Spending rules.md`. The scripts read it, so changes are data, not code.
- **State files** on my PC in `<MONEY FOLDER>`: the running tally of the current cycle and the closed cycles, with checksums. The API token is a `.secret` file there.

## Setting up in a run
1. **Scripts**: use an existing clone if the run started with one; else `add_repo` if available; else clone with the read-only GitHub token (`.secret` file, download link only, fed to git through a credential helper that reads the file, never on a command line). Run the tests. If any fail or the repo can't be reached, give no money figures and say so in one line.
2. **Files in and out**: `create_download_link` + `curl -sS -o FILE URL`; back with `create_upload_link` + `curl -sS -T FILE URL`. Never hand-edit a state file.
3. **Bank data**: `fetch.py` with the API token from `secret/`, then `ingest.py`, so transactions never pass through the chat. Fall back to the connector only if the API fails, saving its pages exactly as returned.

## What each routine runs
- **Morning brief**: balances plus recent transactions, then `upcoming` (low-balance check). Nothing saved.
- **Evening wrap-up**: `tally` from the state file (saves the new state), then `daily` alerts since the last run.
- **Weekly review**: `tally --rebuild` (full recount, reports drift), `daily`, `year`.
- **Monthly review**: `close` (closes the cycle, revises earlier ones if late rows arrived), `year --table`, balances and `reconcile`, `upcoming` for the month ahead.

## How to report
- Use only numbers the scripts printed.
- Call out every overspend in pounds; give the year as one net figure, never a total of only the bad cycles.
- Ask about uncategorised rows (date, payee, amount), and add my answers to the rules note.
- Read-only everywhere except the money notes and state files. Never copy account, card or reference numbers, and keep balances and income out of built-in memory.

## Changing the scripts
Only when I ask or agree. Change the script, add a test with made-up data, run the tests, check on real data outside the repo, then commit and push.
