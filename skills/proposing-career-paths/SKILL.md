---
name: proposing-career-paths
description: Use when a report asks about promotion, when a quarterly career conversation is due, when their growth has stalled, or when their next step feels obvious (especially then)
---

# Proposing Career Paths

## Overview

**Never propose one career path. Always present at least three.**

A single path forecloses the conversation and pushes the report toward what's easiest to imagine — usually "next title." Three meaningfully different paths force a real conversation about what they want, what they're good at, and what the org needs.

This is the SuperDesign `exploring-options` discipline, applied to careers.

**Violating the letter of the rule is violating the spirit.**

## The Iron Law

```
NO CAREER CONVERSATION WITH ONE PATH
```

If you find yourself preparing to say "your next step is X," stop. Generate two more distinct paths before continuing.

**No exceptions:**
- Not for "obvious" promotions
- Not for "they've already decided"
- Not for "the ladder only has one direction"
- Not for "I don't have time to think of alternatives"

## What Counts as "Three Different Paths"

Paths must be **meaningfully distinct mental models**, not flavors of the same idea.

| Bad: same idea different label | Good: different mental models |
|---|---|
| Senior → Staff → Principal (the ladder, three steps) | Depth (Staff IC), breadth (cross-functional design lead), management (EM track) |
| Senior in checkout team, Senior in growth, Senior in platform | IC depth, design system ownership, design ops |
| "Promotion in 12 months", "promotion in 18 months", "promotion in 24 months" | Promotion track, lateral expansion track, sabbatical/recharge track |

**Test:** If they pick one path, do the others die for now? If yes — they were real alternatives.

## The Five Path Archetypes

When generating three paths, draw from these five. The right three depend on the person and org:

1. **Depth** — same IC track, deeper craft. Next level via mastery of current area.
2. **Breadth** — same level, wider surface. New domain, new product area, cross-functional design lead.
3. **Leadership** — management track. Move to EM or design lead role.
4. **Lateral** — different design discipline. Product → systems, IC → research, etc.
5. **External growth** — secondment, sabbatical, conference circuit, open-source. Career growth that isn't a title change.

Most career conversations skip 3-5 entirely. Including them surfaces real options the report wouldn't think to ask for.

## The Process

### 1. Pull the report's context

Read their vault file. Specifically:
- Current level and role
- Last career goal they stated (date, what they said)
- Strengths (from notes, perf reviews)
- Gaps for next level (from career frame section)
- What they care about (from "what I know about them")

If the career frame section is empty or stale, the conversation is more open-ended — start by asking what they want.

### 2. Read the design career ladder

Pull `<vault>/people/_frameworks/design-career-ladder.md` if it exists. If not, prompt the user to set one up using the starter template.

The ladder grounds the conversation in real expectations, not vibes.

### 3. Generate at least three distinct paths

Apply the archetypes. For each path:

- **Path name** (one phrase)
- **Mental model** (1-2 sentences — what is this person becoming?)
- **What they'd do in the next 6 months** (concrete projects/scope)
- **Tradeoff** (what this optimizes for, what it sacrifices)
- **Org fit** (does the org have room for this? what would need to be true?)
- **Their fit** (based on what you know about them, is this likely to motivate them?)

### 4. State your recommendation

Three options without a recommendation is a quiz. Three options with a recommendation is a design conversation.

Pick the path you'd recommend based on:
- What they've said they want
- What they're good at
- What the org needs / can support

Lead with your recommendation, then walk through the alternatives.

### 5. Bring all three to the conversation

Don't withhold the rejected paths. The report needs to see what was considered and why it wasn't chosen — that's how they learn to map their own career.

## Output Template

```
## Career Paths — <name> — <date>

### Where they are now
- Level: <current>
- Tenure: <years>
- Last career goal stated (<date>): <quote>

### Option A — <path name> (the recommendation)
- Mental model: ...
- Next 6 months: ...
- Tradeoff: optimizes for X, sacrifices Y
- Org fit: ...
- Their fit: ...

### Option B — <path name>
[same structure]

### Option C — <path name>
[same structure]

### Why A over B and C
[2-3 sentences]

### Risks to flag in the conversation
- [risk 1, e.g., "this path requires backfill that doesn't exist yet"]
- [risk 2]

### What I'd ask them
- "Of these three, which one most matches how you want to grow?"
- "Anything missing that we should be considering?"
```

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "They've already said they want X" | They said it because X was the only option presented. Show them what else exists. |
| "There's only one ladder rung above them" | Then the path isn't "promotion" — it's depth, breadth, or lateral. Generate alternatives. |
| "We don't have headcount for option B or C" | Then surface that as a risk, not a reason to hide the option. |
| "The exec leadership won't approve management track for them yet" | Then management track has a longer timeline. Still a valid path. |
| "Three options will confuse them" | One option is the foreclosure. Three is the conversation. |
| "I already explored options in my head" | Articulate three or you didn't. |
| "Their next step is obvious" | Especially then. Obviousness is the trap. |

## Red Flags — STOP

- About to present one path
- "Your next step is..."
- "Let's talk about promotion to..."
- "I think you should..."
- "Obviously, the next thing for you is..."

**All mean: stop. Generate two more distinct paths.**

## Pairs With

- `preparing-for-1on1` — if prep flagged career thread due, this fires before the meeting
- `quarterly-career-conversation` — uses this skill for the path-options portion
- `running-1on1` — when career comes up mid-meeting, this still applies (even if compressed)
- `coaching-a-stuck-report` — if they're stuck, options open up the conversation
- `SuperDesign:exploring-options` — same disciplinary pattern, applied to designs instead of careers
