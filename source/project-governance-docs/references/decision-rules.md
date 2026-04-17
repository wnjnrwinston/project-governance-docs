# Decision rules

## Decide greenfield vs retrofit

Choose **greenfield** when most of these are true:
- project has not started
- codebase is absent or trivial
- user asks for planning before coding
- user asks for brief/spec/architecture/decisions first

Choose **retrofit** when most of these are true:
- project already exists
- meaningful code is present
- user asks to document current reality
- user says not to restart or redesign
- user wants current-state docs, runbook, or task extraction from existing implementation

If mixed:
- inspect the workspace
- state what is confirmed
- state what is assumed
- choose the more conservative mode

## Quick menu vocabulary
Use these terms consistently:
- `docs menu` = show the workflow selector
- `greenfield` = foundation docs before implementation
- `retrofit` = current-state-first docs for an existing project
- `update impacted docs` = update only related docs
- `backup project` = create a real checkpoint
- `restore project` = restore from a real checkpoint or backup

## Decide whether plugin is necessary
Default to **skill only** when the problem is mainly:
- workflow guidance
- repeated document structure
- planning/governance behavior
- decision rules
- domain instructions

Consider **plugin** only when the task requires a new runtime capability such as:
- external API/tool integration not already available
- background event sources
- custom provider/tool surface
- system behavior that prompt+existing tools cannot reliably provide

## Decide what to lock now
Lock now if the item affects:
- scope boundaries
- required outputs
- safety constraints
- major workflow choice
- a fundamental technical decision that would cause rework if changed late

## Decide what can stay flexible
Keep flexible if the item affects:
- exact naming
- formatting details
- small internal structure choices
- implementation details that do not destabilize v1 scope

## Decide what to defer
Defer if the item is:
- useful but not required for first success
- speculative future-proofing
- a broader system generalization
- an integration that has not yet become necessary

## Separate facts from assumptions
Label as fact only when it is:
- directly stated by the user
- observed in code/files
- confirmed by execution or inspection

Label as assumption when it is:
- inferred from patterns
- likely but not verified
- dependent on missing environment information

## Separate critical from cosmetic
Critical:
- safety risks
- scope-breaking ambiguity
- wrong architectural baseline
- misleading docs that would cause bad implementation decisions
- operational gaps that block startup, verification, or recovery

Cosmetic:
- wording style
- naming polish
- formatting issues
- minor structure preferences
