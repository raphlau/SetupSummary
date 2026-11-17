---
description: Claude's structured action list for me: things I need to do or am waiting on, with due dates and status. Maintained by the routines; my own TODO note is a separate brain-dump
---
# Actions

Claude's own list of what I need to do or am waiting on. The routines keep it up to date; I can also ask any chat to add, change or close an item. My own TODO note stays my brain-dump and isn't changed from here.

## How the routines use it
- One row per action. IDs (A1, A2...) are never reused.
- **Status**: `open` (mine to do), `waiting` (on someone else), `done`, `dropped`.
- **Due**: a real deadline or the date it needs doing by; blank if there isn't one. **Waiting on**: who, when status is waiting.
- **Source**: where it came from (email, calendar, a note, bank data, or "me").
- **Next look**: when to raise it again. Routines don't raise an item before then unless something changed.
- Morning brief: open items due within 7 days or overdue, and waiting items whose next look has come. Evening wrap-up: adds new items from today's email, calendar and bank data, and closes ones the evidence shows are done (saying so in the report). Sunday review: goes through the whole list, asks about stale items, and moves done or dropped items older than 30 days to the archive.
- Write actions in plain words, starting with a verb. No account, card or reference numbers.
- In anything I read (reports, chat replies), describe the action in words, never by its ID: I don't read this file, so "A11" means nothing to me. The IDs are for the notes and the Routine log only.

## Open and waiting
| ID | Action | Due | Status | Waiting on | Source | Added | Next look |
|---|---|---|---|---|---|---|---|
| A1 | Renew the bank connection consents | 2027-01-31 | open | | Bank data | 2026-11-01 | 2027-01-17 |
| A2 | Hear back from the plumber about the quote | | waiting | Plumber | email | 2026-11-01 | 2026-11-08 |

## Done and dropped (last 30 days)
| ID | Action | Closed | How |
|---|---|---|---|
