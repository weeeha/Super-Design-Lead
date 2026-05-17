---
name: logging-1on1
description: Use immediately after a 1:1 ends, when capturing meeting notes into the vault, or when the user says "log the 1:1" or mentions wrapping up a 1:1
---

# Logging a 1:1

## Overview

Capture the just-finished 1:1 into the vault before context fades. Within the hour, ideally within 10 minutes of the meeting ending.

Updates two places:
1. The report's file (`<vault>/people/reports/<name>.md`) — history, open threads, what-I-know section
2. The 1:1 log (`<vault>/1on1-logs/YYYY-MM-DD-<name>.md`) — full meeting record

## When to Use

- Immediately after a 1:1 ends
- When `running-1on1` produced in-meeting capture and you're wrapping up
- When the user says "log the 1:1 we just had"

**Don't use** if more than 24 hours have passed — the log will be lossy and risk inaccuracy. Better to capture what you remember as "rough notes" in the report file and note that the proper log was missed.

## The Process

### 1. Locate vault files

```bash
VAULT="$(jq -r '.vault_path // "~/Documents/SuperLead-vault"' ~/.superlead/config.json 2>/dev/null || echo "$HOME/Documents/SuperLead-vault")"
VAULT="${VAULT/#\~/$HOME}"

REPORT_FILE="$VAULT/people/reports/<name-kebab>.md"
LOG_FILE="$VAULT/1on1-logs/$(date +%Y-%m-%d)-<name-kebab>.md"

mkdir -p "$VAULT/1on1-logs"
```

### 2. Write the 1:1 log file

Full record of the meeting. This file is append-only — never edit past logs, only add corrections.

```markdown
---
date: YYYY-MM-DD
report: <name>
duration: <min>
type: weekly | quarterly | adhoc
---

# 1:1 — <name> — YYYY-MM-DD

## Their topics
[topics they brought, paraphrased + key quotes]

## Our threads discussed
[items from your side, with outcomes]

## Career
[if discussed]

## Feedback delivered
[if any — what, how it landed]

## Action items
- [ ] me: <action> (by <date>)
- [ ] them: <action> (by <date>)

## Energy / signals (private notes)
- How were they today?
- What did I notice that's worth tracking?

## Carryover to next 1:1
- [items not fully addressed]
```

### 3. Update the report file

Three sections to update in `<vault>/people/reports/<name>.md`:

#### a. 1:1 history (prepend latest)

```markdown
## 1:1 history
- YYYY-MM-DD — [[YYYY-MM-DD-<name>|notes]] — topics: <one-line summary>
- (previous entries...)
```

The wikilink to the log file works in Obsidian; in plain markdown it's a relative path.

#### b. Open threads

- Add new open threads from action items
- Mark resolved threads as done (don't delete — strike-through or mark `(resolved YYYY-MM-DD)`)
- Surface threads that have been open >3 weeks as flags for the next prep

```markdown
## Open threads
- [ ] [thread] — opened YYYY-MM-DD, last touched YYYY-MM-DD
- [ ] ~~[resolved thread]~~ (resolved YYYY-MM-DD)
```

#### c. What I know about them (update if new context)

If the meeting revealed new context (motivation, stressor, communication style, life event you should track sensitively), update this section. Use confidence markers:

```markdown
## What I know about <name>
- Cares about: <list, with last-updated dates>
- Stresses: <list>
- Communication style: <list>
- Personal context: <only what they shared with you, only what affects work>
```

### 4. Update the career frame if discussed

If career came up, update `## Career` in the report file with:
- Date of last career conversation
- Their stated goal (verbatim if possible)
- Active development areas

### 5. Diff and confirm

Before saving, show the user:
- What's being appended to the log
- What sections of the report file are being updated (diff style)
- Anything you're unsure about

Wait for "looks good" or corrections before writing.

## Output Template

```
## Logging 1:1 — <name> — YYYY-MM-DD

### Log file (new)
<path>: <line count> lines, type: weekly | quarterly | adhoc

### Report file updates
- 1:1 history: prepended 1 entry
- Open threads: +<N> added, <M> marked resolved
- What I know: updated section "<which>"
- Career: <updated | no change>

### Carryover threads for next prep
- <thread 1>
- <thread 2>

### Flags
- <any threads open >3 weeks, surface for attention>

Ready to write? (y / edit / cancel)
```

## Common Pitfalls

- **Logging too late.** 1:1 context degrades within hours. If you wait until the next day, you'll lose the energy/signals layer.
- **Editing past logs.** Logs are append-only. If you got something wrong, add a correction in a later log, don't rewrite history.
- **Skipping the energy/signals layer.** This is the part Notion and 1:1 docs miss. Capture how they were, not just what they said.
- **Dumping verbatim transcript.** Logs are summaries plus key quotes, not stenography.
- **Forgetting to update open threads.** The threads section is what `preparing-for-1on1` reads from next time. Stale threads = bad prep next round.

## Pairs With

- `running-1on1` — runs immediately before this skill
- `preparing-for-1on1` — reads the file this skill updates
- `what-do-i-know-about` — uses the accumulated logs and updated report file
