# Doc templates

Use these as lean templates, not mandatory long forms.

## Greenfield foundation summary
- Project purpose
- Problem being solved
- Target users
- V1 intended outcome
- Must-have / nice-to-have / later
- Major risks
- Major assumptions
- Open questions

## Retrofit current-state summary
- System purpose
- Implemented modules
- Implemented flows
- Endpoints and flags
- Runtime/dependency assumptions
- Known gaps
- Critical risks
- Explicit uncertainty

## Scope section template
- In scope
- Out of scope
- Deferred
- Unknown / to confirm

## Acceptance criteria template
Use concrete criteria such as:
- route/flow exists and is documented
- operator can complete workflow end-to-end
- guardrails are explicit
- current behavior is preserved unless intentionally changed
- unknowns are marked, not hidden

## Risks section template
Split by class:
- Critical risks
- Important functional risks
- Cosmetic / documentation-only issues

## Assumptions section template
List only assumptions that matter for execution.
Mark them clearly as assumptions, not confirmed facts.

## Open questions template
Only include questions that affect:
- scope
- architecture choice
- delivery sequence
- safety
- operator workflow

## Task breakdown template
- Phase 0 / Foundation
- Phase 1 / Core implementation or documentation baseline
- Phase 2 / Verification
- Phase 3 / Deferred or post-v1

## Lock-flex-wait template
### Lock now
Items that must be decided before build proceeds.

### Keep flexible
Items that can be refined during implementation without destabilizing scope.

### Wait until after v1
Items that should explicitly not be pulled into immediate work.
