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

## Brain map template
- Project state: `project-state.md`
- Active now:
- Key facts:
- Active decisions:
- Reusable patterns:
- Open tasks:
- Known risks:
- Lessons:
- Deprecated / stale:

## Brain project-state template
- Purpose:
- Current status:
- Active context:
- Implemented areas:
- Current priorities:
- Known gaps:
- Verification/startup notes:
- Last updated:

## Brain node template
```markdown
---
type: Fact | Decision | Pattern | Lesson | Task | Risk
status: Active | Deprecated
tags: []
relates_to: []
source: []
last_updated: YYYY-MM-DD
---

# Node Title

Short, specific statement of the durable knowledge.

## Why It Matters
How this prevents wrong future implementation or repeated context loss.

## Links
- Brain map: ../../brain-map.md
```

## Done + evidence mini-template
- Done when:
- Evidence checked:
- Docs impacted:
- Rollback/checkpoint note:

## Post-task review mini-template
- What changed:
- Why:
- Proof checked:
- Risk left:
- Lesson learned:
- Should this become a rule/checklist/guardrail item?

## Lesson extraction mini-template
- Incident:
- Cause:
- Prevention rule:
- Applies to:
- Permanence level: `temporary` | `project-specific` | `durable principle`

## Failure fallback mini-template
- Failure/uncertainty:
- Confirmed facts:
- Unknowns:
- Smallest safe next step:
- Fallback path if still unclear:

## Pre-mortem mini-template
- Likely break points:
- Safest checkpoint:
- Fastest rollback path:

## Skill Evolution Card
Use this only when a captured lesson may deserve stronger formalization.

- Candidate name:
- Problem it solves:
- What it does / what it can do:
- Why worth formalizing:
- Best type: `passive` | `active` | `toggle` | `triggered`
- Trigger / activation condition:
- Out-of-the-box capability:
- Out of scope:
- Best form: `new skill` | `skill upgrade` | `checklist only` | `memory only`
- Permanence level: `temporary` | `project-specific` | `durable principle`

### Skill Evolution Card examples

#### Example 1 — hardware control calibration guard
- Candidate name: Hardware Control Calibration Guard
- Problem it solves: teams in hardware/OSC/control-calibration style projects jump from idea to UI before device control paths and value mappings are verified
- What it does / what it can do: forces path -> value -> verified control flow before operator UI grows
- Why worth formalizing: repeated high-cost failure pattern in hardware/OSC work
- Best type: `passive`
- Trigger / activation condition: hardware control, OSC path discovery, device parameter automation
- Out-of-the-box capability: prompts verification-first workflow and rejects speculative UI-first reasoning in hardware/control-oriented work
- Out of scope: full protocol discovery, hardware simulation, vendor-specific deep automation
- Best form: `checklist only` or `skill upgrade`
- Permanence level: `project-specific`

#### Example 2 — impacted-docs review trigger
- Candidate name: Impacted Docs Review Trigger
- Problem it solves: implementation changes land but docs drift because no one asks which docs became inaccurate
- What it does / what it can do: prompts a narrow docs review after meaningful changes and keeps unrelated docs untouched
- Why worth formalizing: high-value discipline with low cost; prevents stale documentation
- Best type: `triggered`
- Trigger / activation condition: implementation or behavior change that may affect scope, runbook, current-state, or tasks
- Out-of-the-box capability: asks which docs changed naturally and prefers targeted doc edits
- Out of scope: full doc-pack rewrites, automatic documentation generation for everything
- Best form: `skill upgrade`
- Permanence level: `project-specific`

#### Example 3 — strict done + evidence mode
- Candidate name: Strict Done + Evidence Mode
- Problem it solves: tasks get declared done without enough proof, causing weak completion claims
- What it does / what it can do: requires compact proof fields such as done when, evidence checked, docs impacted, and rollback/checkpoint note
- Why worth formalizing: improves completion quality and review confidence without much overhead
- Best type: `toggle`
- Trigger / activation condition: risky work, multi-file work, or user request for stricter verification discipline
- Out-of-the-box capability: changes completion style from bare status to compact evidence-backed status
- Out of scope: mandatory heavyweight testing ceremony for trivial edits
- Best form: `skill upgrade`
- Permanence level: `project-specific`

## Knowledge Promotion Lifecycle
Use this to prevent lesson storage from becoming passive clutter.
Do not add this as a new docs-menu workflow.
Use it as a small internal promotion path.

### Stages
1. `capture`
   - store the lesson briefly
2. `compress`
   - reduce raw detail into a compact reusable lesson
3. `evaluate`
   - decide whether it stays memory-only or deserves stronger formalization
4. `promote`
   - convert into checklist, skill upgrade, or new skill if justified
5. `retain`
   - keep one compact source record or pointer
6. `retire`
   - avoid keeping duplicated passive copies once a stronger form exists

### Promotion status mini-template
- Promotion status: `unpromoted` | `compressed` | `promoted to checklist` | `promoted to skill upgrade` | `promoted to new skill` | `retired as duplicate/noise`
- Source retained?: yes/no
- Why retained or retired:

### Lifecycle rule of thumb
- do not delete useful source too early
- do not keep long raw notes and promoted forms duplicated forever
- prefer one compact retained source plus the promoted form

## Lock-flex-wait template
### Lock now
Items that must be decided before build proceeds.

### Keep flexible
Items that can be refined during implementation without destabilizing scope.

### Wait until after v1
Items that should explicitly not be pulled into immediate work.
