---
name: quarterly-career-conversation
description: Use when a quarterly career check-in is due, when the report asks to discuss career growth, when more than 3 months have passed since the last career conversation, or when planning a perf cycle career talk
---

# Quarterly Career Conversation

## Overview

A scheduled, structured career conversation. Deeper than weekly 1:1 — uses dedicated time (45-60 min) to step back from project work and look at trajectory.

Run quarterly at minimum. More often if the report is in transition (new role, recent promotion, recent struggle, considering a change).

## When to Use

- Quarterly cadence hit (>3 months since last)
- Report explicitly asks about career
- Big career inflection upcoming (perf cycle, promotion case, role change)
- You're noticing growth has stalled or accelerated

**Don't use** for everyday 1:1s — those have a career touch but not the full structure. And don't use for hard performance conversations — those are corrective feedback (`giving-feedback-to-a-report`), not career discussions.

## Pre-Conversation

### 1. Schedule properly

- 45-60 minutes, blocked separately from weekly 1:1
- Not on a Friday afternoon
- Quiet space, video-on if remote

### 2. Pre-work for both of you

Send these to the report 2-3 days before:

```
"Let's use our time to step back from current projects and look at growth.

Before we meet, can you spend ~30 min on:

1. What's energized you in the last quarter? Specific moments.
2. What's drained you? Specific moments.
3. Where do you think you're growing? Where are you stuck?
4. What do you want to be doing in 12 months? In 3 years?
5. What support / opportunity from me would help most?

You don't need to write it up — just reflect. We'll discuss together."
```

### 3. Your pre-work

Run `preparing-for-1on1` AND additionally pull:
- The design career ladder (`<vault>/people/_frameworks/design-career-ladder.md`)
- Last quarterly career notes (search 1on1-logs for `type: quarterly`)
- Performance review history if available
- Any feedback themes from the last 90 days (from logs)

Run `proposing-career-paths` with this context — generate 3+ paths and tradeoffs.

## The Conversation

### Beat 1 — Reflection (15 min, their voice first)

Open: *"Walk me through how the last quarter felt for you, growth-wise."*

Listen. Take notes. Specifically capture:
- Energy patterns — what fed them, what drained them
- Where they think they grew
- Where they think they're stuck
- Any frustrations they haven't surfaced before

Don't argue. Reflect back to confirm: *"So if I'm hearing right, what energized you was X, and what felt stuck was Y. Did I get that?"*

### Beat 2 — Your observations (10 min)

Share your view of their growth this quarter:
- Specific strengths you've seen develop
- Specific gaps you've noticed
- Where you've seen them stretch successfully
- Where you've seen them avoid stretch

Be specific. "You handled the X project well" is weak. "In the X project, I noticed you led the cross-functional sync without me prompting — that's a Staff-level move you weren't doing 6 months ago" is useful.

### Beat 3 — Mapping to the ladder (10 min)

Pull up the career ladder. Walk through expectations for their current level. Where are they exceeding? Where are they meeting? Where are they below?

Be honest. This is the conversation where the report learns whether they're tracking toward next level or not. Avoid happy-talk that misleads them about timing.

### Beat 4 — Path options (15 min)

Present the 3+ paths from `proposing-career-paths`. Walk through each:
- Mental model
- 6-month concrete picture
- Tradeoff
- Org fit
- Their fit

Your recommendation, briefly. Then:

> *"Of these three, which one most matches how you want to grow? Or is there a fourth that we should consider?"*

Listen to their reaction. Their fit matters most. If they react to a non-recommended path with energy you haven't seen in months, take that seriously.

### Beat 5 — 6-month plan (10 min)

Collaborate on:
- Which path
- Concrete projects/scope changes that test the path
- Skills/capabilities to develop
- What you'll do to help (mentorship, intro, sponsorship, stretch assignment)
- What they'll do
- How we'll know it's working (3-month checkpoint)

### Beat 6 — Close

- Capture the plan in writing (you draft, share with them within 24 hours)
- Schedule the 3-month check
- Confirm: *"Did this conversation give you what you needed?"*

If the answer is "no" or "not really" — that's a Red Flag. Schedule a 30-min follow-up to address what was missing.

## After

Log thoroughly via `logging-1on1` with `type: quarterly`. Update the report file's Career section in full:

```markdown
## Career
- Current frame: <last-discussed-level / path>
- Stated goal (YYYY-MM-DD): "verbatim from this conversation"
- Active development areas:
  - <area 1> — how we're testing growth
  - <area 2>
- Manager observations (YYYY-MM-DD):
  - Strengths developed: ...
  - Gaps: ...
  - Stretch readiness: ...
- 6-month plan: <summary>
- 3-month check scheduled: YYYY-MM-DD
- Path options presented (this conversation):
  - A: <name> (chosen)
  - B: <name>
  - C: <name>
```

## Common Pitfalls

- **Skipping pre-work.** They show up unprepared = the conversation surfaces less. Send the pre-work prompt.
- **Mapping to ladder vaguely.** Use concrete level language. Quantify.
- **Avoiding the hard truth.** If they're not tracking toward what they want, say so kindly. Don't let them be surprised at perf review.
- **Selling one path.** You did `proposing-career-paths` — bring all three.
- **No 3-month check.** Plan without checkpoint = plan that drifts.
- **Doing it in 1:1 slot.** Weekly time is for tactical. Career needs dedicated time.

## Pairs With

- `preparing-for-1on1` — pre-work step, deeper for this conversation
- `proposing-career-paths` — feeds Beat 4
- `logging-1on1` — captures the conversation
- `giving-feedback-to-a-report` — for any feedback that emerges during reflection (deliver separately if hard)
- `coaching-a-stuck-report` — if reflection surfaces being stuck, this is the follow-up
