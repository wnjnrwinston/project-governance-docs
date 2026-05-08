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
- `docs menu` or `/docsmenu` = show the fixed workflow selector verbatim
- `updatedocs` = same as `update impacted docs`
- `greenfield` = foundation docs before implementation
- `retrofit` = current-state-first docs for an existing project
- `brain`, `infinite brain`, or `brain-first` = AI-maintained project memory for fresh-session continuity
- `update impacted docs` = update only related docs
- `backup project` = create a real checkpoint
- `restore project` = restore from a real checkpoint or backup

If the user sends one selector word by itself, treat it as an explicit workflow choice.
If `/docsmenu` appears after a long conversation, prefer fixed menu behavior over memory of prior custom menus.

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

## Decide whether a lesson should be extracted
Extract a lesson when one of these is true:
- the same mistake happened more than once
- the fix depended on a subtle repo-specific rule
- the failure mode is likely to recur during normal maintenance
- the lesson would improve review/checklist quality with one short rule

Do not extract a lesson when:
- it is obvious and unlikely to repeat
- it adds noise without changing future decisions
- it is only a one-off environmental accident with no reusable prevention rule

## Decide lesson permanence level
Use `temporary` when:
- the lesson matters only for the next few steps
- the repo is in a temporary intermediate state

Use `project-specific` when:
- the lesson depends on this repo's workflow, docs, or constraints
- future maintainers of this project should see it again

Use `durable principle` when:
- the lesson generalizes beyond this repo
- it improves future governance or implementation discipline across projects

## Decide fallback behavior when uncertain
If inspection/build/lint/tooling results are unclear:
- confirm what still works
- name the exact unknown
- reduce to the smallest testable step
- avoid broad fixes based on guesswork
- prefer a bounded fallback plan over speculative redesign

## Decide what counts as done
Prefer work to count as done only when there is compact evidence such as:
- inspected file change matches requested behavior
- command output supports the claim
- UI/route behavior was observed
- remaining uncertainty is explicitly named

"Done" without evidence is weak completion, not strong completion.

## Decide whether to create or update brain docs
Use brain-first docs when:
- the user wants fresh sessions to continue without long context replay
- the user wants Codex to maintain project memory
- a project has repeated context loss, repeated questions, or cross-session handoff friction
- an existing `docs/brain/brain-map.md` is present

Do not create brain docs when:
- the task is a one-off quick edit
- the project is too small to benefit
- the user only asked for read-only inspection
- the added node would duplicate obvious or low-value information

When brain docs exist, update only impacted brain docs after meaningful work.
The user should not be expected to maintain them manually.

## Decide when to require pre-mortem thinking
Use a light pre-mortem when work is:
- risky
- multi-file
- hard to roll back
- likely to affect workflow-critical docs or rules

Keep it short:
- likely break points
- safest checkpoint
- fastest rollback path

## Decide whether a lesson should become a skill candidate
Promote a lesson to skill-candidate review when:
- it keeps recurring across tasks
- it meaningfully changes future behavior rather than just recording history
- it has a clear capability that can be described, not just a vague good idea
- the best form may be stronger than memory alone

Then decide the smallest useful form:
- `memory only`
- `checklist only`
- `skill upgrade`
- `new skill`

Also decide the most natural behavior type:
- `passive`
- `active`
- `toggle`
- `triggered`

## Decide whether a captured lesson should be retained, promoted, or retired
After capture:
- retain briefly if the source case still matters
- compress when the raw form is noisier than the reusable lesson
- promote when the lesson now has clear repeated value as checklist or skill behavior
- retire duplicate passive copies when a stronger promoted form already exists

Default to keeping one compact source or pointer, not many repeated variants.
