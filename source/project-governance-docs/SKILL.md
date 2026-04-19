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
   - default docs: `docs/PROJECT_BRIEF.md`, `docs/SPEC.md`, `docs/ARCHITECTURE.md`, `docs/ENGINEERING_RULES.md`, `docs/GUARDRAILS.md`, `docs/RUNBOOK.md`, `docs/TASKS.md`, `docs/DECISIONS.md`
2. `retrofit` — document and govern the current implementation first
   - default docs: `docs/CURRENT_STATE.md`, `docs/SPEC.md`, `docs/ENGINEERING_RULES.md`, `docs/GUARDRAILS.md`, `docs/RUNBOOK.md`, `docs/TASKS.md`
3. `update impacted docs` — update only the documentation affected by the latest change
   - update only the docs that became inaccurate
4. `backup project` — create a real project checkpoint before risky changes
   - do not create governance docs by default
   - if the target project/repo is unclear, ask which one should be backed up
5. `restore project` — restore from the latest real checkpoint or backup
   - do not claim restore is possible unless a real checkpoint exists
   - if the target project/repo is unclear, ask which one should be restored

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

## Lean learning-loop upgrades

Use these upgrades only when they materially improve execution quality.
Keep them small, operational, and tied to repo reality.

### 1. Lesson extraction
When a mistake, near-miss, repeated confusion, or verification gap appears, compress it into a small reusable lesson.

Preferred format:
- incident
- cause
- prevention rule
- applies to
- permanence level

Permanence levels:
- `temporary` = useful for the next few tasks only
- `project-specific` = should stay with this repo/workflow
- `durable principle` = reusable across projects unless contradicted

Only promote a lesson when it helps avoid repeat failure.
Do not create a large lesson log by default.

### 2. Failure fallback behavior
When lint/build/env/api/tooling inspection becomes unclear or fails:
- stop broad implementation work
- separate what is confirmed from what is now uncertain
- reduce the task to the smallest verifiable next step
- prefer read/inspect/reproduce over speculation
- if ambiguity remains, propose a bounded fallback path rather than an invented fix

### 3. Done + evidence discipline
Do not treat "implemented" as enough by itself.
For meaningful work, prefer a compact done check:
- done when
- evidence checked
- docs impacted
- rollback/checkpoint note

Keep this compact.
Evidence can be inspection, command output, observed UI behavior, test result, or explicit limitation.

### 4. Post-task review / teach-back
After multi-step or risky work, include a short review:
- what changed
- why
- proof checked
- risk left
- lesson learned
- should this become a rule/checklist/guardrail item?

### 5. Pre-mortem thinking
Before risky or multi-file changes, briefly identify:
- likely break points
- safest checkpoint
- fastest rollback path if the change goes wrong

Keep this light.
Do not turn it into a ceremony for trivial edits.

### 6. Memory compression
When capturing lessons, distinguish:
- temporary lesson
- project-specific lesson
- durable principle

Do not store everything at the same level.
Prefer compressed lessons over long narrative unless the narrative is necessary.

### 7. Skill-candidate judgement
When a lesson seems strong enough to deserve more than memory alone, evaluate it with a small Skill Evolution Card.

Use it to answer:
- what problem it solves
- what it does / what it can do
- whether it is best expressed as `passive`, `active`, `toggle`, or `triggered`
- whether it should become a `new skill`, `skill upgrade`, `checklist only`, or remain `memory only`

Do not promote every good lesson into a skill.
Use the smallest form that gives real repeated value.

### 8. Knowledge promotion lifecycle
Treat captured lessons as material that may be promoted, not as storage that must grow forever.

Preferred path:
- capture
- compress
- evaluate
- promote
- retain
- retire

Keep one compact retained source when useful.
Avoid duplicated passive buildup once a stronger promoted form already exists.
Do not turn this into a new docs-menu workflow unless a truly separate user-facing workflow emerges later.

## Checkpoint and rollback rule

For in-progress projects:
- prefer git-based checkpoints before risky or multi-file changes
- if git is unavailable, prefer minimal manual backups of touched files
- describe rollback in `RUNBOOK.md` only when the rollback path is real
- if rollback is manual, say so explicitly
- if the active project target is not already clear from context, ask before running backup/restore workflow against a specific project or repo

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
