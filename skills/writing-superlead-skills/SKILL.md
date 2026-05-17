---
name: writing-superlead-skills
description: Use when creating, editing, or testing skills in this plugin - SuperLead
---

# Writing SuperLead Skills

## Overview

How to add or edit skills in this plugin. v0.1 — expect this to evolve.

This mirrors `SuperDesign:writing-design-skills` and is downstream of `obra/superpowers:writing-skills`. Same core idea: skills are not prose, they're behavior-shaping code.

## Core Rules

1. **Frontmatter has only `name` and `description`.** Both required. Description max 1024 chars.
2. **Description is triggers only, not workflow.** Start with "Use when…". Never summarize the skill's process — the agent will follow the description and skip the body.
3. **Names use letters, numbers, hyphens only.** Gerunds work well (`preparing-for-1on1`, `giving-feedback-to-a-report`).
4. **One skill, one purpose.** If the description has "and" linking two purposes, split.
5. **SKILL.md under ~500 lines.** Heavy reference goes in sibling files.

## Skill Anatomy

```
skills/<name>/
  SKILL.md
  reference-*.md      # optional, heavy reference
```

Bundled templates live separately at `<plugin-root>/templates/` — skills reference them by path.

## Description Rules (the trap)

```yaml
# BAD: summarizes workflow — agent reads this and skips skill body
description: Use when running 1:1s - pulls open threads, drafts agenda, logs after

# GOOD: triggers only
description: Use when about to start a 1:1 with a direct report - meeting starting in the next hour
```

When descriptions summarize workflow, the agent uses them as a shortcut and skips the actual content. The body becomes documentation the agent never reads.

## Body Structure (rough — adapt)

```
# Skill Name

## Overview
Core principle in 1-2 sentences.

## When to Use
Specific triggers. When NOT to use.

## The Process / Checklist
The actionable content.

## Output Template
What this skill produces.

## Common Rationalizations / Red Flags
(For rigid skills) Excuses that signal STOP.

## Pairs With
Other skills that come before/after.
```

## Working with the Vault

SuperLead skills read and write to a user vault at `~/Documents/SuperLead-vault` (or whatever is configured at `~/.superlead/config.json`).

When a skill needs to read/write vault files:

```bash
VAULT="$(jq -r '.vault_path // "~/Documents/SuperLead-vault"' ~/.superlead/config.json 2>/dev/null || echo "$HOME/Documents/SuperLead-vault")"
VAULT="${VAULT/#\~/$HOME}"
```

Skills should:
- Create the vault directory and standard subdirs (`people/reports/`, `1on1-logs/`, `people/_frameworks/`) on first write, not eagerly at install
- Copy starter templates from `<plugin-root>/templates/` into `<vault>/people/_frameworks/` on first run
- Use kebab-case filenames (`sarah-chen.md`, not `Sarah Chen.md`)
- Use ISO dates (`YYYY-MM-DD`) for time-stamped files

## Light Testing (v0.1)

Before merging:

1. **Read it cold.** Can Claude understand what it does and when to use it from a fresh start?
2. **Trigger test.** Fresh session, natural prompt — does the skill auto-fire?
3. **Pressure test (rigid skills).** Add deadline pressure: *"5 min until 1:1, just give me a quick prompt list."* Does the skill still enforce the discipline?
4. **Vault test.** Run on a real (or fake) vault. Does the skill correctly read existing data and write new data?

## Iteration

After every real-use session, check:
- Did a skill fail to fire when it should have? → adjust description triggers
- Did the agent follow the description instead of the body? → workflow leak in description
- Did the user override? → skill is wrong or triggers too broad
- Did the agent fail to find the vault? → config / path detection issue

## Pairs With

This is a meta-skill. Applied recursively to itself.
