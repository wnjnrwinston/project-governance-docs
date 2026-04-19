# Greenfield mode

Use this mode when the project has not started yet or when the user explicitly wants planning before implementation.

## Goal
Create the project foundation before production code begins.

## Default doc set
Create these docs unless the user narrows scope:
- `docs/PROJECT_BRIEF.md`
- `docs/SPEC.md`
- `docs/ARCHITECTURE.md`
- `docs/ENGINEERING_RULES.md`
- `docs/GUARDRAILS.md`
- `docs/RUNBOOK.md`
- `docs/TASKS.md`
- `docs/DECISIONS.md`

## Required outputs before coding
Before any production implementation, produce:
1. project foundation summary
2. v1 scope definition
3. risk and assumptions list
4. phased implementation plan
5. open questions that must be answered before build starts

Then propose:
- what should be locked now
- what can remain flexible
- what should explicitly wait until after v1

## Writing rules

### PROJECT_BRIEF
Include:
- purpose of the project
- problem being solved
- target users
- intended v1 outcome
- must-have vs nice-to-have vs later

### SPEC
Include:
- target v1 scope
- major workflows
- acceptance criteria
- in-scope / out-of-scope / deferred / unknown

### ARCHITECTURE
Include:
- planned technical direction only
- intended stack
- app structure
- major modules
- data flow
- boundaries
- explicit assumptions

Do not overdesign. Use the smallest architecture that can plausibly support v1.

### ENGINEERING_RULES
Define rules that prevent:
- overengineering
- unnecessary abstraction
- premature optimization
- building for imagined future requirements

### GUARDRAILS
Define:
- hard boundaries
- forbidden changes
- safety constraints
- scope-control rules

### RUNBOOK
Define only what is actually known for v1:
- expected startup flow
- local development assumptions
- environment setup assumptions
- validation steps
- deployment assumptions

Mark unknown operational items clearly.

### TASKS
Split work into phases:
- foundation work
- core implementation
- verification
- deferred work

### DECISIONS
Track:
- early decisions already made
- assumptions
- open questions
- unresolved tradeoffs

## Documentation maintenance after implementation starts
Once implementation exists:
- update only the docs affected by the completed work
- do not refresh the entire doc pack by default
- if a task changes only scope, update `SPEC.md` and possibly `TASKS.md`
- if a task changes only implementation reality, update only the relevant current-state or runbook docs if they exist in that project

## Checkpoint and rollback planning
Before risky implementation work begins, prefer defining one real checkpoint strategy:
- git commit/checkpoint if the project is in version control
- minimal backup of touched files if not

Do not promise undo unless a real mechanism exists.
If rollback will be manual, state that clearly in planning and runbook notes.

## Risk handling
Call out early:
- requirement ambiguity
- missing product decisions
- unknown integrations
- deployment uncertainty
- scope creep risk

## Lean learning-loop additions
Even in greenfield mode, keep learning-loop behavior small and practical:
- for risky work, do a short pre-mortem
- prefer done + evidence over bare completion claims
- if an early planning mistake reveals a reusable rule, compress it into a short lesson with a permanence level

Do not turn greenfield planning into a memory-system redesign.

## Anti-patterns
Do not:
- write architecture for a system bigger than v1
- smuggle implementation into vague planning language
- claim decisions are final if they are still assumptions
- convert nice-to-have ideas into must-have scope
