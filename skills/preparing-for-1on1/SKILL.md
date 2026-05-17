---
name: preparing-for-1on1
description: Use when a 1:1 with a direct report is starting in the next hour, when blocking time before a 1:1, or when the user mentions an upcoming 1:1 with a report by name
---

# Preparing for a 1:1

## Overview

Never wing a 1:1. Even a 5-minute prep is the difference between a useful conversation and a status update with eye contact.

This skill pulls everything you should remember from the report's vault file and drafts an agenda that uses the time on what matters.

**Violating the letter of the rule is violating the spirit.** A "quick prep" that skips the file read is not prep.

## The Iron Law

```
NO 1:1 WITHOUT READING THE REPORT FILE FIRST
```

Walking in cold? You're wasting both your time and theirs.

**No exceptions for:**
- "I just talked to them yesterday"
- "It's a quick check-in"
- "I remember what we discussed"
- "I'm too slammed to prep"

If you can't spare 5 minutes to prep, reschedule. A skipped 1:1 is better than a wasted one.

## The Process

### 1. Locate the report file

```bash
VAULT="$(jq -r '.vault_path // "~/Documents/SuperLead-vault"' ~/.superlead/config.json 2>/dev/null || echo "$HOME/Documents/SuperLead-vault")"
VAULT="${VAULT/#\~/$HOME}"
REPORT_FILE="$VAULT/people/reports/<report-name-kebab>.md"
```

If the file doesn't exist, **stop and run the onboarding step**:
- Create the file from the template at `<plugin-root>/templates/report-file-template.md`
- Ask the user the bare-minimum questions to fill the frontmatter (role, level, joined date, current focus)
- Save it
- Then continue prep

### 2. Read the report file end-to-end

Pull every section into context:
- Frontmatter (current role, level, joined date)
- Current state (focus, OKRs)
- What I know about them (motivations, stressors, communication style)
- Career frame (last career goal discussed, gaps for next level)
- 1:1 history (last 3 entries — what was discussed, what's open)
- Open threads (action items still pending)
- Performance review pointers

If sections are missing or stale (>3 months old), flag it.

### 3. Draft the agenda

Standard structure (adapt to length — 30 min, 45 min, 60 min):

```
## 1:1 Agenda — <name> — <date>

### Their time first (default 50%)
- [open question for them to bring up anything]
- Active threads they're working through:
  - [thread 1 with brief context]
  - [thread 2]

### Open threads from us (from previous 1:1s — list, don't fill the whole time)
- [open thread 1] — last touched <date>
- [open thread 2]

### Career / growth thread (default once every 2-3 weeks, not every 1:1)
- [career thread to revisit if due] OR (skip if recently covered)

### Feedback I owe them (if any)
- [specific feedback held since last 1:1]

### What I need from them (if any)
- [specific ask]

### Time to close
- Confirm action items captured
- Anything we didn't cover that needs scheduling separately
```

### 4. Surface conflicts and risks

Before the meeting, scan for:
- **Anything you've been avoiding** — uncomfortable feedback, a hard conversation, a deferred decision. Don't skip. If you're tempted to defer again, that's a Red Flag (see below).
- **Sensitive timing** — recent org news, performance pressure, personal events you know about. Adjust tone but don't dodge topics.
- **Their stress signals** — if your notes say they're stretched, lead with workload check before adding new asks.

### 5. Output the prep

Print the agenda to the user with three sections clearly marked:
1. **Agenda for the meeting** (above)
2. **What to remember** — 3-5 bullets summarizing key context (motivations, current stress, last big topic)
3. **What you might be avoiding** — if anything was flagged in step 4, surface it explicitly

## Output Template

```
## 1:1 Prep — <name> — <date>

### What to remember
- <key context 1>
- <key context 2>
- <key context 3>

### Agenda (<duration>)
<the agenda from step 3>

### Things I'm tempted to skip (don't)
- <hard conversation 1>  [or: "none flagged"]
- <feedback held too long>
- <deferred decision>

### File last updated: <date>
```

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "I just talked to them yesterday" | Yesterday's context fades. The file holds it. Read anyway. |
| "5 min prep is overkill" | 5 min prep prevents 30 min wasted. Run it. |
| "I'll just check the agenda doc in Notion" | The vault file has personal context the agenda doc doesn't. Read both. |
| "Career talk can wait another week" | Career deferral is the #1 management failure. If due, raise it. |
| "I don't have time for hard feedback today" | Hard feedback degrades with time. Today is when. |
| "Their open threads from last time will resolve themselves" | They won't. Threads close when revisited. |
| "I know what they want to talk about" | You don't. Ask. |

## Red Flags — STOP

- About to start a 1:1 without reading the file
- "I'll figure out what to talk about in the meeting"
- About to defer feedback for the third time
- About to skip the career thread "just this once"
- "We're tight on time, let's keep it casual"

**All mean: stop. Open the file. Read. Prep.**

## Pairs With

- `running-1on1` — fires during the meeting using this prep
- `logging-1on1` — fires after the meeting, updates the file
- `proposing-career-paths` — if prep surfaces a career conversation due
- `giving-feedback-to-a-report` — if prep surfaces feedback that's been delayed
- `what-do-i-know-about` — alternative recall if the report file is light
