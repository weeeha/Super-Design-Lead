---
name: what-do-i-know-about
description: Use when needing to recall context about a person, topic, project, or thread from the vault - before a meeting, when something comes up unexpectedly, or when preparing async communication
---

# What Do I Know About

## Overview

Recall skill. Pulls everything the vault knows about a person, topic, project, or thread — across report files and 1:1 logs.

Useful when:
- Someone is about to walk into your office and you need context fast
- Preparing async communication that depends on history
- A topic comes up in a meeting and you can't remember the last time it was discussed
- Reviewing whether something is actually new or has been raised before

This skill is read-only. Doesn't write to the vault.

## When to Use

- Before any meeting where context matters and prep didn't happen
- When a thread comes up and you can't remember the history
- When deciding whether to raise something you've half-forgotten
- When pattern-matching across multiple reports ("am I hearing this from everyone?")

**Don't use** for full 1:1 prep — that's `preparing-for-1on1`. This is for fast, single-topic recall.

## The Process

### 1. Locate vault

```bash
VAULT="$(jq -r '.vault_path // "~/Documents/SuperLead-vault"' ~/.superlead/config.json 2>/dev/null || echo "$HOME/Documents/SuperLead-vault")"
VAULT="${VAULT/#\~/$HOME}"
```

### 2. Determine query type

The skill handles four types of recall:

| Query | Search scope | Example |
|---|---|---|
| **Person** | One report file + their 1:1 logs | "What do I know about Sarah Chen?" |
| **Topic** | All report files + all 1:1 logs | "When did design system come up last?" |
| **Project** | All vault files | "What's the history on the checkout redesign?" |
| **Pattern** | All vault files | "Who's mentioned burnout recently?" |

Ask the user which type if ambiguous.

### 3. Search

For person:
```bash
cat "$VAULT/people/reports/<name-kebab>.md"
grep -l "<name>" "$VAULT/1on1-logs/"*.md | sort -r | head -10 | xargs cat
```

For topic / project / pattern:
```bash
grep -l -i "<term>" "$VAULT"/**/*.md | sort -r
# then read recent matches
```

Search recent first (last 30, 60, 90 days) — older context is usually less relevant.

### 4. Synthesize

Don't dump raw matches. Organize:

```
## What I know about <query> — <date>

### Most recent
- YYYY-MM-DD: <one-line summary> — [link]

### Themes (across recent matches)
- <theme 1>: appears in <N> recent logs/files
- <theme 2>: ...

### Open threads
- <thread 1>: opened YYYY-MM-DD, last touched YYYY-MM-DD, status: <status>

### Key context
- <2-3 most important things to know>

### What I don't know / gaps
- <things that would help that aren't in the vault>
```

Be honest about gaps. The vault holds what was captured; if a topic is recent or under-logged, say so.

### 5. Output

If the recall is for an upcoming meeting, mark which items are time-sensitive ("raise in next 1:1") vs ambient ("background context").

## Output Template

```
## Recall — "<query>" — <date>

### Query type
[ ] Person  [ ] Topic  [ ] Project  [ ] Pattern

### Most recent (last 30 days)
- YYYY-MM-DD: <summary> — [[<file-link>]]
- ...

### Themes
- <theme>: <evidence>

### Open threads
- [ ] <thread> — opened YYYY-MM-DD, last touched YYYY-MM-DD

### Key context (3-5 bullets)
- <most important fact 1>
- ...

### Gaps / what I don't know
- <thing 1>
- <thing 2>
```

## Common Pitfalls

- **Dumping every match.** Synthesize. Five themed bullets beats fifty raw lines.
- **Ignoring date.** Old context can mislead. Mark recency.
- **Not flagging gaps.** What's absent from the vault matters as much as what's there.
- **Searching too narrowly.** Topics use multiple words ("burnout" / "stretched" / "tired"). Try variations.
- **Searching too broadly.** Person + topic together ("Sarah's career") is sharper than topic alone.

## Pairs With

- `preparing-for-1on1` — full prep flow; this skill is faster, single-purpose recall
- `coaching-a-stuck-report` — pattern recall to diagnose flavor of stuck
- `hiring-a-designer` — recall on prior hires for leveling comparison
