---
name: end-session
description: Ends a lærling workday session. Writes the day's dagslogg with kompetansemål, learnings and links into the log repository, then commits it. Use when the user types /end-session, or says avslutt dagen, oppsummer dagen, dagslogg, or hva har jeg lært i dag.
allowed-tools: Bash(git -C * add *) Bash(git -C * commit *) Bash(git -C * status *) Bash(git -C * diff *)
---

# End session

Closes the workday, writes the log, commits it. Never invoke this on your own — it writes to a repository, so the user decides when the day is over.

**Log repository:** `~/laerling-logg` — adjust if it lives elsewhere.
**Log path:** `~/laerling-logg/logg/dagslogg-YYYY-MM-DD.md`

## The working directory is not the log repo

The user starts Claude Code in whatever project they worked in that day. The log belongs somewhere else entirely.

- Write the log to its **absolute path**. Never a path relative to the current project.
- Run every git command with **`-C ~/laerling-logg`**, so it operates on the log repo no matter where the session started. A bare `git add` here either fails because the file is outside the repo, or — worse — stages something in the user's work repository.
- Before committing, confirm the target: `git -C ~/laerling-logg status --short` should show only the new log file.
- If a git command reports a different repository than the log repo, stop and tell the user rather than trying another form of the command.

A dagslogg accidentally committed into a Vestfold work repository means internal learning notes in a shared team history. Absolute paths and `-C` are what prevent that.

## Steps

### 1. Aggregate the day

Work from the whole conversation. Aggregate rather than concatenate: three 401s debugged is *one* learning about authentication. A kompetansemål touched five times is listed once, with the strongest example.

Read `references/kompetansemaal.md` from the `laerling-mentor` skill and quote the mål **verbatim** — this documentation gets assessed against the official læreplan wording.

### 2. Run the confidentiality check — before writing anything

This file is going into a git repository. Git history is durable and pushed history is hard to purge, so the filter runs before the write, not after.

**Never write into the log:**

- Secrets of any kind — API keys, tokens, passwords, connection strings. Not even partially, not even expired. Write "feilsøkte et API-token som ikke ble lastet i test-miljøet", never the token.
- Personopplysninger about colleagues, users or citizens — names, emails, fødselsnummer, case data. Roles instead of names: "en kollega i driftsteamet", not "Kari".
- Internal hostnames, IP addresses, internal URLs, server names, database names.
- Named third parties in a way that reveals a security weakness — "en leverandørintegrasjon feilet på autentisering" rather than naming the vendor and the flaw.

Describe **what was learned**, not **what the system looks like**. A log saying "learned how to trace a failing token through a deploy pipeline" is complete documentation and reveals nothing. That distinction is the whole skill here.

If something genuinely can't be described without sensitive detail, write the learning and note that the specifics are omitted. Then say so to the user in one line, so they know the log is deliberately thin there rather than assuming you missed it.

### 3. Write the file

`<repo>/logg/dagslogg-YYYY-MM-DD.md`, creating the folder if needed. Language: whatever the user has been writing in. Kompetansemål always in Norwegian.

```markdown
# Dagslogg — YYYY-MM-DD

## Hva jeg jobbet med
- [task, one line each, concrete]

## Kompetansemål dekket
- [verbatim mål] — [one line on how the day's work touched it]

## Hva jeg lærte
- [first person, specific, tied to real work]

## Det jeg fortsatt er usikker på
- [genuinely unresolved — omit the heading if there is nothing]

## Lenker og ressurser
- [title](url) — [why it was useful]

## Neste steg
- [what to pick up tomorrow]
```

**Honesty rules.** If they struggled, or the answer was ultimately handed to them, the log says so — "fikk hjelp til å forstå hvorfor" is a legitimate line. Never inflate. An inflated log documents competence that can't be demonstrated, which surfaces in front of an assessor at the worst possible moment. A quiet day gets a thin log; that is the correct output, not a failure.

`Det jeg fortsatt er usikker på` is the most useful section in the file. It's what goes to the veileder. Don't quietly drop it to make the day look better.

### 4. Show it before committing

Print the log in the conversation. Ask them to confirm or correct it. It's their documentation in their voice — they get the last word on what it says they learned.

### 5. Commit

After they confirm:

```
git -C ~/laerling-logg add logg/dagslogg-YYYY-MM-DD.md
git -C ~/laerling-logg commit -m "dagslogg: YYYY-MM-DD"
```

Then **ask before pushing.** Don't push automatically. A local commit is easy to amend; a pushed one is on a remote where fixing it means rewriting published history. One confirmation buys a lot of margin on a file that carries confidentiality risk.

If `git -C ~/laerling-logg status` shows unrelated staged changes, commit only the log file by path and say what was left alone. Never `git add .` here — and never `git add` without `-C`.

## Don't

- Invoke this yourself. Only the user ends the day.
- Reconstruct a plausible workday from thin material. If little was tracked, write the short honest log.
- `git add .`, `git commit -a`, git without `-C`, or push without asking.
- Skip the confidentiality check because the day felt routine. Routine days are when internal hostnames slip in.
