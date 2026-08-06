---
name: start-session
description: Starts a lærling workday session. Reads the most recent dagslogger from the log repository to restore context, then asks what is planned for today. Use when the user types /start-session, or says start dagen, god morgen, or ny arbeidsdag.
allowed-tools: Bash(git -C * pull *) Bash(git -C * status *)
---

# Start session

Opens a workday session for a lærling in IT-utvikling. Companion to `end-session`, which closes it and writes the log.

**Log repository:** `~/laerling-logg` — adjust if it lives elsewhere.

**The working directory is almost never the log repo.** The user starts Claude Code in whatever project they're working on that day. Always address the log repo by absolute path, and always pass `-C` to git so the command runs against the log repo regardless of where the session started. Never run a bare `git` command here — in another repo it either fails or touches the wrong history.

## Steps

1. **Restore context.** Read the three most recent files in `<repo>/logg/` (glob for `dagslogg-*.md`, sort by name descending — the ISO date makes filename order chronological order). Pay attention to **Neste steg** and **Det jeg fortsatt er usikker på** from the last day. If the folder is empty or missing, this is the first session; say so briefly and move on.

2. **Sync.** Run `git -C ~/laerling-logg pull` so a log written on another machine isn't missed. If it fails, mention it in one line and continue — a failed pull is not a reason to block the workday.

3. **Ask what's planned.** One question, conversational. If the last log left something open, lead with that: "Forrige gang sto det at du skulle se på X — er det der du starter?"

4. **Note silently.** Which kompetansemål the day looks likely to touch, per the mentor skill's `references/kompetansemaal.md`. Don't announce it. Nobody wants a læreplan briefing before their coffee.

Then stop and work. The session is just a normal working conversation from here; `laerling-mentor` governs how to teach during it.

## While the session runs

Track, without emitting log blocks after every task:

- tasks worked on
- kompetansemål touched
- what clicked, and what stayed muddy
- links that came up in the conversation

Say once, early, if it's relevant: only links that appear in this conversation can make it into the log. Pages read in their own browser are invisible unless pasted.

## Don't

- Deliver an agenda, a summary of the læreplan, or a motivational opener. One question about the plan.
- Announce that a session has "officially begun." There's no state machine here, just a conversation that ends with a log.
