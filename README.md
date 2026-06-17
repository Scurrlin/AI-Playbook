# AI Building Playbook

This is a drag-and-drop playbook for building software with AI.

It is not a framework, package, or tool install. It is a small set of project files that help an AI assistant understand the project, follow the same working rules every time, and use repeatable slash-skill workflows.

## Drop Into Any Project

Add these to the root of your project:

- `AGENTS.md`
- `context/`
- `skills/`

Then fill in the placeholders in `AGENTS.md` and the files in `context/` with that project's actual goals, architecture, standards, constraints, current plan, and progress.

## What Each Part Is For

- `AGENTS.md` is the project-facing agent guide. Fill in its placeholders so it reads like it belongs to the project you dropped it into.
- `context/` is the project memory. It explains what the project is, how it is structured, what rules matter, and what is currently happening.
- `skills/` is the workflow library. Each slash command points to a matching `skills/<name>/SKILL.md` file.
- `integrations/` contains optional tool-specific layouts for Claude Code, Codex, and Cursor.
- `memory.md` is the per-session handoff file written by `/rememberSave` in the project root. It is transient session state, distinct from `context/progress-tracker.md`, which holds durable project status. It appears once you first save memory.

The README is for humans. `AGENTS.md` is the reusable agent guide the AI reads while working.

## Skill Commands

Use these in your AI chat when the moment calls for a specific workflow:

| Command | Use it when |
| ------- | ----------- |
| `/architect` | You want to think through a feature before building. |
| `/review` | You want to check completed work before moving on. |
| `/rememberSave` | You are ending a session and want to preserve handoff context. |
| `/rememberRestore` | You are starting a new session and want to pick up cleanly. |
| `/recover` | Repeated fixes are making the work worse. |
| `/imprint` | UI work created a reusable pattern that should stay consistent. |
| `/promptSave` | You want to design, optimize, and document a prompt or GPT as a reusable asset. |

If your AI tool supports slash skills, it can treat these as commands. If it does not, use the same slash text anyway; it tells the AI to read the matching file in `skills/` and follow it.

## How To Use It

1. Drop the playbook files into a project.
2. Fill in the relevant `context/` templates.
3. Ask the AI to read `AGENTS.md` before planning or changing code.
4. Use slash skills for planning, review, memory, recovery, and UI consistency.
5. Keep `context/` updated when decisions, architecture, standards, or progress change.

## Tool Integrations

The base playbook is plain Markdown. For tools with their own discovery folders, copy the matching integration into the project root after adding `AGENTS.md`, `context/`, and `skills/`.

### Claude Code

Copy:

```text
integrations/claude/.claude/
integrations/claude/CLAUDE.md
```

Into:

```text
<project-root>/.claude/
<project-root>/CLAUDE.md
```

Claude Code project skills live at `.claude/skills/<skill-name>/SKILL.md`. The `CLAUDE.md` file imports `AGENTS.md` so Claude Code reads the shared guide and context as its source of truth.

### Codex

Copy:

```text
integrations/codex/.agents/
```

Into:

```text
<project-root>/.agents/
```

Codex repo skills live at `.agents/skills/<skill-name>/SKILL.md`. Codex reads root `AGENTS.md` directly, so no extra routing file is needed.

### Cursor

Copy:

```text
integrations/cursor/.cursor/
```

Into:

```text
<project-root>/.cursor/
```

Cursor uses project rules at `.cursor/rules/*.mdc`. These rules route Cursor to the shared `AGENTS.md`, `context/`, and `skills/` files. Cursor also reads root `AGENTS.md` directly for straightforward project instructions.

### Keeping Integrations In Sync

The base `skills/` folder is the source of truth. The Claude and Codex integrations contain copies of each `SKILL.md`, so when you change a skill, update the matching copy under `integrations/claude/.claude/skills/` and `integrations/codex/.agents/skills/` as well. To avoid drift entirely, you can instead symlink those skill folders to the base `skills/` folder; both Claude Code and Codex follow symlinks when discovering skills.

## How This Should Feel

This playbook should not feel like busywork. It should make AI-assisted work clearer, calmer, and less likely to drift.

The docs are the source of truth. The skills are the repeatable workflows. Everything is plain Markdown, so the playbook stays portable and reusable.

## Credits

The minimal-implementation ladder in `AGENTS.md` and `context/code-standards.md` is adapted from [Ponytail](https://github.com/DietrichGebert/ponytail) (MIT).
