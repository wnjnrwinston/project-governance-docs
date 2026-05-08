# Project Governance Docs

A small OpenClaw skill for practical project governance workflows:

- **greenfield** - define the project before coding
- **retrofit** - document and govern the current implementation first
- **brain** - maintain an AI-readable Infinite Brain for fresh-session continuity

It also supports a simple workflow selector:

- `docs menu`
- `/docsmenu`
- `updatedocs`
- `greenfield`
- `retrofit`
- `brain`
- `infinite brain`
- `brain-first`
- `update impacted docs`
- `backup project`
- `restore project`

## What It Does

This skill helps keep project work practical and controlled by:

- defining foundation docs before implementation when a project is new
- documenting current reality first when a project already exists
- creating and maintaining concise brain docs for AI fresh sessions
- separating facts from assumptions
- keeping v1 scope minimal
- avoiding unnecessary redesign
- updating only impacted docs instead of refreshing everything
- reading `docs/brain/brain-map.md` first when brain docs exist
- using real backup/restore discipline instead of fake undo
- extracting compact lessons from repeated mistakes or ambiguity
- preferring bounded fallback behavior when tooling/build/lint/env inspection becomes unclear
- requiring compact proof of completion instead of weak "done" claims

## Modes

### Greenfield

Use when the project has not started yet and you want foundation docs before coding.

Default docs created:

- `docs/PROJECT_BRIEF.md`
- `docs/SPEC.md`
- `docs/ARCHITECTURE.md`
- `docs/ENGINEERING_RULES.md`
- `docs/GUARDRAILS.md`
- `docs/RUNBOOK.md`
- `docs/TASKS.md`
- `docs/DECISIONS.md`

### Retrofit

Use when the project already exists and you want docs/governance based on the current implementation first.

Default docs created:

- `docs/CURRENT_STATE.md`
- `docs/SPEC.md`
- `docs/ENGINEERING_RULES.md`
- `docs/GUARDRAILS.md`
- `docs/RUNBOOK.md`
- `docs/TASKS.md`

### Brain

Use when you want Codex/AI to maintain a compact project memory layer that a fresh session can read first.

Default docs created:

- `docs/brain/brain-map.md`
- `docs/brain/project-state.md`
- `docs/brain/nodes/facts/`
- `docs/brain/nodes/decisions/`
- `docs/brain/nodes/patterns/`
- `docs/brain/nodes/lessons/`
- `docs/brain/nodes/tasks/`
- `docs/brain/nodes/risks/`

Expected behavior:

- read `docs/brain/brain-map.md` before broad planning or implementation work
- open only the linked nodes relevant to the current task
- update only impacted brain nodes after meaningful work
- keep Obsidian optional; Markdown and Git remain enough

### Update Impacted Docs

Use after a completed change when only some docs became inaccurate.

Expected behavior:

- update only the docs affected by the latest change
- leave unrelated docs untouched if they are still accurate

### Backup Project

Use before risky or multi-file changes.

Expected behavior:

- create a real checkpoint for the current clearly scoped project
- if project scope is unclear, ask which project/repo should be backed up
- prefer git if available
- otherwise create a manual backup

### Restore Project

Use when you need to recover to a real checkpoint.

Expected behavior:

- restore the current clearly scoped project from a real backup/checkpoint if available
- if project scope is unclear, ask which project/repo should be restored
- say so clearly if no real restore path exists

## Quick Invoke

If you say `docs menu` or `/docsmenu`, the skill should present the fixed menu verbatim and should not improvise a custom version:

1. `greenfield`
2. `retrofit`
3. `update impacted docs`
4. `backup project`
5. `restore project`
6. `brain`

Additional selector behavior:

- `updatedocs` = alias for `update impacted docs`
- `greenfield`, `retrofit`, `brain`, `infinite brain`, `brain-first`, `backup project`, and `restore project` can be sent by themselves as direct workflow selections
- if the workflow choice is already explicit, continue directly instead of showing the menu again
- if `/docsmenu` appears after a long conversation, prefer the fixed menu behavior over remembered custom menus

## Lean Learning-Loop Features

These upgrades are intentionally small and integrated into the existing workflows.

Included behavior covers:

- lesson extraction
- failure fallback behavior
- done + evidence discipline
- post-task review / teach-back
- light pre-mortem thinking
- skill-candidate judgement
- knowledge promotion lifecycle (`capture -> compress -> evaluate -> promote -> retain -> retire`)

## Included Files

```text
index.html
styles.css
source/project-governance-docs/
  SKILL.md
  references/
    brain-first-mode.md
    decision-rules.md
    doc-templates.md
    greenfield-mode.md
    retrofit-mode.md

dist/project-governance-docs.skill
```

## Installation

### Option 1 - Packaged Skill

Download:

- `dist/project-governance-docs.skill`

Then install/import it using your OpenClaw skill import workflow.

### Option 2 - Manual Source Install

Copy the skill folder from:

- `source/project-governance-docs/`

into your local OpenClaw skills directory, then reload/restart OpenClaw if needed.

## First Use

After install, try:

```text
/docsmenu
```

That should present:

- `greenfield`
- `retrofit`
- `update impacted docs`
- `backup project`
- `restore project`
- `brain`

## Usage Examples

### Show Menu

```text
/docsmenu
```

### New Project

```text
greenfield - before coding, define the project first. Create the foundation docs and keep v1 minimal.
```

### Existing Project

```text
retrofit - check current state first, then make the docs based on the existing implementation. Do not redesign it.
```

### Fresh-Session Brain

```text
brain - setup docs/brain/brain-map.md, project-state.md, and a small set of atomic nodes so a new AI session can continue without replaying the whole chat.
```

### After A Change

```text
update impacted docs - update only the docs affected by the latest confirmed change in the current project context.
```

### Before Risky Work

```text
backup project - create a real checkpoint for the current clearly scoped project; if the target project is unclear, ask which project/repo should be backed up first.
```

### Recover From Checkpoint

```text
restore project - restore the current clearly scoped project from a real checkpoint; if the target project is unclear, ask which project/repo should be restored first.
```

## Contributing

Contributions are welcome. Keep changes small, practical, well-scoped, and aligned with the current workflow philosophy.

## License

MIT
