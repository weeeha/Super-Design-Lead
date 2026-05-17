---
name: running-1on1
description: Use when a 1:1 with a direct report is actively happening or about to start (within the next 5 minutes), when capturing during a live meeting, or when the user says they're "in a 1:1 now"
---

# Running a 1:1

## Overview

Live execution of a 1:1. Assumes `preparing-for-1on1` already ran and produced an agenda. This skill is the in-meeting layer: holding structure, capturing notes, surfacing held topics at the right moment.

If prep didn't happen, this skill insists you do a 60-second compressed prep before continuing. You don't get to skip prep by claiming you're "already in the meeting."

## When to Use

- The 1:1 is starting now or in the next 5 minutes
- The 1:1 is in progress and you want capture support
- You're walking into a 1:1 that someone else (you, earlier) didn't fully prep for

**Don't use** for performance reviews, quarterly career conversations, or hard-feedback delivery — those have their own skills (`writing-performance-review`, `quarterly-career-conversation`, `giving-feedback-to-a-report`).

## The Structure

A useful 1:1 has these beats. Adapt order and weights based on what they bring.

| Beat | Default duration (30 min) | Default duration (45 min) |
|---|---|---|
| Their topics first | 10-15 min | 15-20 min |
| Open threads from us | 5-10 min | 10-15 min |
| Career / growth (if due) | 0-5 min weekly, 10-15 if due | 0-10 weekly, 15-20 if due |
| Feedback (if any held) | 5 min | 5-10 min |
| Close + action items | 5 min | 5 min |

**Their time first** is the most-violated rule. Don't open with your agenda. Open with "what's on your mind?" and let them set tone.

## The Process

### 1. Confirm prep happened

Check for a prep artifact (from `preparing-for-1on1`). If none:

> Pause. Even 60 seconds of compressed prep beats none. Read the report's vault file end-to-end. Note 3 open threads, 1 piece of feedback if held, and any career thread due. Then continue.

Do NOT skip this. Walking in cold guarantees a wasted meeting.

### 2. Open with their time

Default opener: *"What's on your mind?"* or *"What do you want to use our time for today?"*

Listen. Don't redirect to your agenda for the first 5-10 min unless they explicitly hand it back.

### 3. Capture while you listen

Maintain a running notes file in the structure of:

```markdown
## 1:1 — <name> — <date>

### What they brought
- [topic 1]
  - context: ...
  - what they need from me: ...
- [topic 2]
  - ...

### Open threads I raised
- [thread 1]
  - status: ...
  - next: ...

### Career
- [if discussed: what came up, action items]

### Feedback delivered
- [if any: what, how it landed]

### Action items
- [ ] me: ...
- [ ] them: ...

### To revisit next time
- [items that didn't get full air time]
```

Take notes openly (laptop or paper — let them see you noting things). Tells them you take this seriously and protects you both later.

### 4. Surface held items at natural transitions

When they pause or wrap a topic, transition with:

- *"Before we shift, anything else on [topic]?"*
- *"I want to make sure we cover [held item from prep]. Quick to bring up now?"*

Don't ambush. Don't dump.

### 5. Handle hard moments

If feedback delivery comes up: invoke `giving-feedback-to-a-report` for structure mid-meeting.

If career comes up: if `proposing-career-paths` hasn't run for this person recently, suggest doing it as a follow-up rather than improvising three paths live. Set a date.

If they're upset: stop the agenda. Listen. Don't fix immediately. *"That sounds hard. Tell me more."*

If you're surprised by something major (resignation hint, escalating conflict, mental health flag): treat as the conversation. Drop the agenda. Schedule follow-up.

### 6. Close

5 minutes before end:

1. Read back action items (yours and theirs)
2. Confirm timing: when will each be addressed
3. Ask: *"Anything we didn't get to that we should schedule separately?"*
4. End on time. Running over feels generous but signals poor structure.

### 7. Log immediately after

Invoke `logging-1on1` while the meeting is fresh. Don't defer — context degrades within hours.

## Output Template (in-meeting capture, fed to `logging-1on1`)

```
## 1:1 — <name> — <date> — <duration> min

### Their topics
- ...

### Our threads
- ...

### Career (if discussed)
- ...

### Feedback (if delivered)
- ...

### Action items
- [ ] me: ...
- [ ] them: ...

### Energy / signals (private notes)
- How were they today? What did I notice?
- Anything new about how they're handling work?
```

## Common Pitfalls

- **Opening with your agenda** — robs them of initiative. Open with their time.
- **Filling silence** — silence after a question is often where the real topic surfaces. Wait.
- **Solving in real time** — the impulse to fix a problem during the 1:1 robs them of agency. Ask, *"How are you thinking about this?"* before answering.
- **Skipping capture** — "I'll remember" — you won't. Notes during, log after.
- **Running over** — bleeds into the next thing, signals you're not in control.
- **Dropping career thread** — if it's due, raise it even when there's no time. Surface as: *"I want to do this justice — let's schedule 30 min next week specifically for career."*

## Pairs With

- `preparing-for-1on1` — runs before this skill (always)
- `logging-1on1` — runs immediately after this skill (always)
- `giving-feedback-to-a-report` — invoked mid-meeting if feedback delivery occurs
- `proposing-career-paths` — invoked as follow-up if career comes up but isn't prepped
- `coaching-a-stuck-report` — invoked as follow-up if signals of being stuck appear
