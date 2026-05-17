# SuperLead

A design-leadership methodology plugin for Claude Code. Skills for design managers — 1:1s, career conversations, feedback, hiring, coaching — backed by a file-based relationship store you maintain in Obsidian or a private GitHub repo.

**Status: v0.1.** 11 skills. Companion to [SuperDesign](https://github.com/weeeha/Super-Design-Skills).

## What it does

The hard parts of design management aren't intellectual — they're disciplinary. Prepping for the 1:1 you've already had 40 times. Giving feedback you've been holding for two weeks. Proposing three career paths when the obvious one is "next title."

SuperLead skills enforce that discipline. They:
- Read from and write to a markdown vault (your Obsidian or private repo)
- Prep you before 1:1s using everything the vault remembers
- Block one-option career conversations (the rigid spine, mirroring SuperDesign's `exploring-options`)
- Structure feedback through Observation → Impact → Ask before delivery
- Capture meetings into the vault so the next meeting is informed
- Help you ramp into hiring loops, performance cycles, coaching conversations

## Installation

```bash
/plugin marketplace add weeeha/Super-Design-Lead
/plugin install SuperLead@SuperLead-marketplace
```

Restart your session. The `SessionStart` hook injects the [`using-superlead`](skills/using-superlead/SKILL.md) meta-skill, which teaches Claude to invoke the other skills when they're relevant.

### Set up your vault

Create a config file at `~/.superlead/config.json`:

```json
{
  "vault_path": "/Users/you/Documents/Obsidian/Work"
}
```

If unset, SuperLead defaults to `~/Documents/SuperLead-vault`.

The vault can be:
- An **Obsidian vault** (wikilinks work natively)
- A **cloned private GitHub repo** (versioned, syncable across machines)
- Any folder of markdown files

Skills create the standard subdirectories (`people/reports/`, `1on1-logs/`, `people/_frameworks/`) lazily on first write.

## Skills

### Meta
| Skill | Tier | What it does |
|---|---|---|
| [`using-superlead`](skills/using-superlead/SKILL.md) | Bootstrap | Auto-injected at session start |
| [`writing-superlead-skills`](skills/writing-superlead-skills/SKILL.md) | Authoring | How to add or edit skills |

### Rigid spine (discipline under pressure)
| Skill | What it does |
|---|---|
| [`preparing-for-1on1`](skills/preparing-for-1on1/SKILL.md) | Never wing it — pulls from report file, drafts agenda from open threads + career context |
| [`proposing-career-paths`](skills/proposing-career-paths/SKILL.md) | 3+ growth paths, never just "next title." Five archetypes: depth, breadth, leadership, lateral, external |
| [`giving-feedback-to-a-report`](skills/giving-feedback-to-a-report/SKILL.md) | Observation → Impact → Ask. Three flavors. Anticipates response. Plans follow-up. |

### Flexible workflow
| Skill | What it does |
|---|---|
| [`running-1on1`](skills/running-1on1/SKILL.md) | In-meeting structure: their topics first, capture during, close on time |
| [`logging-1on1`](skills/logging-1on1/SKILL.md) | Post-meeting: append to report file + 1:1 log, update open threads |
| [`quarterly-career-conversation`](skills/quarterly-career-conversation/SKILL.md) | 45-60 min structured career check-in, with pre-work prompts |
| [`hiring-a-designer`](skills/hiring-a-designer/SKILL.md) | JD, loop design, prep, debrief, leveling, offer |
| [`coaching-a-stuck-report`](skills/coaching-a-stuck-report/SKILL.md) | Diagnose stuck flavor (skill / motivation / confidence / context / mismatch), match move |

### Utility
| Skill | What it does |
|---|---|
| [`what-do-i-know-about`](skills/what-do-i-know-about/SKILL.md) | Fast read-only recall across vault — person / topic / project / pattern |

## The vault structure

```
<your-vault>/
├── people/
│   ├── reports/
│   │   ├── sarah-chen.md
│   │   ├── alex-park.md
│   │   └── ...
│   └── _frameworks/                # customizable references
│       ├── design-career-ladder.md
│       ├── 1on1-template.md
│       ├── performance-review-template.md
│       ├── hiring-rubric.md
│       └── coaching-conversation-template.md
├── 1on1-logs/
│   └── YYYY-MM-DD-<report-name>.md
└── ideas-board.md
```

Starter versions of the `_frameworks/` files are bundled with the plugin at [templates/](templates/). Customize them for your org.

## How it works

1. Claude Code starts a session.
2. The `SessionStart` hook reads [`using-superlead/SKILL.md`](skills/using-superlead/SKILL.md) and injects it as session context.
3. That meta-skill teaches Claude: *"if there's a 1% chance a SuperLead skill applies, invoke it."*
4. As you work, Claude invokes the relevant skill — `preparing-for-1on1` when you mention an upcoming 1:1, `coaching-a-stuck-report` when you mention someone's struggling, etc.
5. Skills read/write your vault. Your context survives sessions.

## Companion: SuperDesign

If [SuperDesign](https://github.com/weeeha/Super-Design-Skills) is also installed:

- `giving-feedback-to-a-report` (manager-side of feedback delivery) pairs with `SuperDesign:critiquing` (design content critique)
- `proposing-career-paths` shares its disciplinary pattern with `SuperDesign:exploring-options` (3+ alternatives, never one)

Both plugins coexist cleanly. Each is independently useful.

## What's deliberately NOT in v0.1

- **`writing-performance-review`** — too big, gets its own skill in v0.2
- **`who-needs-attention`** — depends on having months of vault data
- **General management content** — this is design management specifically
- **Multi-harness support** — Claude Code only at v0.1
- **A web UI** — vault is markdown files; pick your editor

## Architecture

Inspired by [obra/superpowers](https://github.com/obra/superpowers). Same bootstrap + meta-skill pattern, adapted to design leadership.

The disciplinary spine: **never present one option, always present three.** Career paths follow the same rule SuperDesign uses for design directions, and for the same reason — one option is a decision in disguise.

## Versioning

```bash
./scripts/bump-version.sh --check     # see current versions
./scripts/bump-version.sh --audit     # scan for stale version strings
./scripts/bump-version.sh 0.2.0       # bump everything to 0.2.0
```

## License

MIT.

## Credit

Architecture inspired by [Jesse Vincent's superpowers](https://github.com/obra/superpowers).
