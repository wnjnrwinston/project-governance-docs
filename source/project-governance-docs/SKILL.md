---
name: project-governance-docs
description: Create project planning, governance, and execution docs for either a new project or an existing codebase. Use when a user asks to define a project before coding, create brief/spec/architecture/runbook/tasks/decisions docs, retrofit governance onto a project already in progress, or document current state first before further implementation. Especially use for requests about project foundation, v1 scope, acceptance criteria, engineering rules, guardrails, phased tasks, risks, assumptions, and open questions.
---

# Project Governance Docs

Create the smallest useful governance/doc pack for the user's actual project state.

Default goal:
- define or document the project clearly
- control scope
- avoid invented architecture
- separate facts from assumptions
- make the next implementation steps obvious

## Quick invoke

If the user says `docs menu` or `/docsmenu`, present this fixed menu:

## Docs Menu
Choose one:

1. `greenfield` — define the project before coding
2. `retrofit` — document and govern the current implementation first
3. `update impacted docs` — update only the documentation affected by the latest change
4. `backup project` — create a real project checkpoint before risky changes
5. `restore project` — restore from the latest real checkpoint or backup

Reply with one option name to continue.

Treat `docs menu` and `/docsmenu` as workflow selectors, not as literal system commands.

## Workflow decision

First decide which mode applies.

### Mode 1: Greenfield foundation
Use this when:
- the user says the project has not started yet
- there is no meaningful implementation yet
- the user wants planning before coding
- the user asks for project brief/spec/architecture/decisions first
- the user selects `greenfield` from `docs menu`

Then read:
- `references/greenfield-mode.md`
- `references/doc-templates.md`

### Mode 2: Retrofit governance
Use this when:
- the user says the project is already in progress
- code already exists and should be inspected first
- the user wants current-state docs, governance, rules, runbook, or tasks based on observed reality
- the user explicitly says not to restart or redesign the project
- the user selects `retrofit` from `docs menu`

Then read:
- `references/retrofit-mode.md`
- `references/doc-templates.md`

If classification is ambiguous, inspect the workspace first and state the uncertainty explicitly.

## Core rules

Always:
- document current reality first when code exists
- distinguish confirmed facts from assumptions
- distinguish must-have / in-scope from nice-to-have / deferred
- keep v1 minimal and buildable
- identify critical risks separately from cosmetic issues
- prefer practical execution over elegant overdesign
- update only the docs actually affected by the change
- prefer a real checkpoint or rollback path before risky implementation work

Never:
- invent architecture that is not justified by the project state
- broaden a narrow task into a general system redesign
- hide unknowns; mark them clearly
- treat assumptions as decisions already locked
- rewrite the entire doc set when only one or two docs changed
- claim rollback or undo exists unless it is real for that project

## Documentation maintenance rule

After a task:
- update only the impacted docs
- do not rewrite unrelated docs
- if implementation changed but existing docs are still accurate, leave them alone
- if no behavior, scope, rule, operation, or task status changed, no doc update is required
- prefer targeted edits over broad doc refreshes

## Checkpoint and rollback rule

For in-progress projects:
- prefer git-based checkpoints before risky or multi-file changes
- if git is unavailable, prefer minimal manual backups of touched files
- describe rollback in `RUNBOOK.md` only when the rollback path is real
- if rollback is manual, say so explicitly

## Output requirements

Produce:
- a clear project foundation or current-state summary
- scope definition
- risks and assumptions
- phased implementation/task plan
- open questions that matter

Use concise docs with explicit section headers.

## Decision aids

For mode-specific decision rules and doc requirements, read:
- `references/decision-rules.md`

## Notes on architecture and plugins

This skill is for documentation, scope, governance, and planning work.
It is not a reason by itself to introduce new plugins, services, or abstractions.
If a user asks whether a plugin is necessary, default to:
- skill/workflow first for behavioral or documentation problems
- plugin only for truly missing runtime/tool capability
