# Retrofit mode

Use this mode when the project is already in progress and existing code should be treated as the baseline.

## Goal
Retrofit documentation and governance onto the current codebase based on observed reality first.

## Default doc set
Create these docs unless the user narrows scope:
- `docs/CURRENT_STATE.md`
- `docs/SPEC.md`
- `docs/ENGINEERING_RULES.md`
- `docs/GUARDRAILS.md`
- `docs/RUNBOOK.md`
- `docs/TASKS.md`

## Required working method
1. inspect the actual codebase first
2. identify implemented modules, flows, endpoints, dependencies, flags, and operational assumptions
3. mark uncertainty explicitly
4. document gaps between code and desired design clearly
5. propose only minimal corrective changes when necessary

## Writing rules

### CURRENT_STATE
Describe the system as it exists today.
Include:
- modules
- flows
- endpoints
- flags/toggles
- dependencies
- launcher/runtime assumptions
- known gaps
- explicit uncertainty

### SPEC
Define target scope from this point forward.
Include:
- what remains in scope now
- acceptance criteria
- out-of-scope work
- deferred work

Treat the existing implementation as the starting baseline, not as something to reimagine.

### ENGINEERING_RULES
Focus on:
- preventing broad refactors
- preserving working calibrated/validated behavior
- keeping fixes local
- maintaining compatibility unless change is justified

### GUARDRAILS
Define:
- forbidden changes
- safety boundaries
- hard scope control
- high-risk areas where accidental redesign would be harmful

### RUNBOOK
Document current reality:
- startup
- stop/restart
- verification
- recovery/rollback steps for the current system

If rollback is manual or partial, say so clearly.

### TASKS
Convert remaining work into actionable tasks.
Separate:
- critical risks
- important consistency fixes
- bounded improvements
- deferred ideas

## Documentation maintenance after each task
After implementation work:
- update only the impacted docs
- do not rewrite all governance docs by default
- if current behavior changed, update `CURRENT_STATE.md`
- if scope or acceptance changed, update `SPEC.md`
- if operational steps changed, update `RUNBOOK.md`
- if remaining work changed, update `TASKS.md`
- leave unrelated docs untouched if they are still accurate

## Checkpoint and rollback discipline
Before risky fixes or multi-file changes:
- prefer git checkpoints when available
- otherwise create minimal manual backups of touched files
- describe rollback in `RUNBOOK.md` only if it actually exists
- if recovery is manual reapply/restore work, say so directly

## Risk handling
Separate:
- critical operational or product risk
- functional mismatch
- cosmetic inconsistency

## Anti-patterns
Do not:
- invent architecture that does not exist
- rewrite the project in docs to look cleaner
- perform broad refactors as part of documentation work
- change unrelated code while investigating
