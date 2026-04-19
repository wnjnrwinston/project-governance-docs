# Project Governance Docs

A small OpenClaw skill for two common documentation/governance workflows:

- **greenfield** — define the project before coding
- **retrofit** — document and govern the current implementation first

It also supports a simple workflow selector:

- `docs menu`
- `/docsmenu`
- `greenfield`
- `retrofit`
- `update impacted docs`
- `backup project`
- `restore project`

## What it does

This skill helps keep project work practical and controlled by:
- defining foundation docs before implementation when a project is new
- documenting current reality first when a project already exists
- separating facts from assumptions
- keeping v1 scope minimal
- avoiding unnecessary redesign
- updating only impacted docs instead of refreshing everything
- using real backup/restore discipline instead of fake undo
- extracting compact lessons from repeated mistakes or ambiguity
- preferring bounded fallback behavior when tooling/build/lint/env inspection becomes unclear
- requiring compact proof of completion instead of weak "done" claims
- supporting small post-task review and pre-mortem discipline where it adds real value
- evaluating whether a strong repeated lesson should remain memory, become a checklist, or be promoted into a skill upgrade

## Lean learning-loop features

These upgrades are intentionally small and integrated into the existing workflows.
They do **not** add a new docs-menu mode.

Included behavior now covers:
- lesson extraction
- failure fallback behavior
- done + evidence discipline
- post-task review / teach-back
- light pre-mortem thinking
- skill-candidate judgement
- knowledge promotion lifecycle (`capture -> compress -> evaluate -> promote -> retain -> retire`)

## Why this project is useful

- small but operational
- reality-first retrofit behavior
- avoids fake rollback claims
- supports lesson extraction and evidence-backed completion
- keeps governance lean instead of bloated

## Contributing

Contributions are welcome.

This project works best when changes stay:
- small
- practical
- well-scoped
- aligned with the current workflow philosophy

### Good places to start
New contributors can help by:
- clarifying ambiguous wording
- improving examples
- tightening retrofit/greenfield guidance
- improving README clarity
- adding small reusable templates
- strengthening practical guardrails or decision rules

### Suggested contribution flow
- for small documentation or wording fixes, open a PR directly
- for larger workflow changes, open an issue or discussion first
- keep PRs focused and explain:
  - what changed
  - why
  - what was intentionally left unchanged

### Before proposing larger changes
It helps to explain:
- what problem the change solves
- why the current workflow is insufficient
- why a smaller change would not be enough

## Modes

### Greenfield
Use when the project has not started yet and you want foundation docs before coding.

**Default docs created:**
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

**Default docs created:**
- `docs/CURRENT_STATE.md`
- `docs/SPEC.md`
- `docs/ENGINEERING_RULES.md`
- `docs/GUARDRAILS.md`
- `docs/RUNBOOK.md`
- `docs/TASKS.md`

### Update impacted docs
Use after a completed change when only some docs became inaccurate.

**Expected behavior:**
- update only the docs affected by the latest change
- leave unrelated docs untouched if they are still accurate

### Backup project
Use before risky or multi-file changes.

**Expected behavior:**
- create a real checkpoint for the current clearly scoped project
- if project scope is unclear, ask which project/repo should be backed up
- prefer git if available
- otherwise create a manual backup

### Restore project
Use when you need to recover to a real checkpoint.

**Expected behavior:**
- restore the current clearly scoped project from a real backup/checkpoint if available
- if project scope is unclear, ask which project/repo should be restored
- say so clearly if no real restore path exists

## Quick invoke

If you say `docs menu` or `/docsmenu`, the skill should present:

1. `greenfield`
2. `retrofit`
3. `update impacted docs`
4. `backup project`
5. `restore project`

## Included files

```text
source/project-governance-docs/
├── SKILL.md
└── references/
    ├── decision-rules.md
    ├── doc-templates.md
    ├── greenfield-mode.md
    └── retrofit-mode.md

dist/project-governance-docs.skill
```

## Installation

### Option 1 — packaged skill
Download:
- `dist/project-governance-docs.skill`

Then install/import it using your OpenClaw skill import workflow.

### Option 2 — manual source install
Copy the skill folder from:
- `source/project-governance-docs/`

into your local OpenClaw skills directory, then reload/restart OpenClaw if needed.

## First use

After install, try:

```text
/docsmenu
```

That should present the 5 workflow options:
- `greenfield`
- `retrofit`
- `update impacted docs`
- `backup project`
- `restore project`

## Usage examples

### Show menu
```text
/docsmenu
```

### New project
```text
greenfield — before coding, define the project first. Create the foundation docs and keep v1 minimal.
```

### Existing project
```text
retrofit — check current state first, then make the docs based on the existing implementation. Do not redesign it.
```

### After a change
```text
update impacted docs — update only the docs affected by the latest confirmed change in the current project context.
```

### Before risky work
```text
backup project — create a real checkpoint for the current clearly scoped project; if the target project is unclear, ask which project/repo should be backed up first.
```

### Recover from checkpoint
```text
restore project — restore the current clearly scoped project from a real checkpoint; if the target project is unclear, ask which project/repo should be restored first.
```

## License

MIT
