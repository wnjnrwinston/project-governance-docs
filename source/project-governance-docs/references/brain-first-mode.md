# Brain-first mode

Use this mode when the user wants AI-readable project memory to be the primary continuity layer across fresh sessions.

## Goal
Keep project context small, precise, and retrievable so a new Codex session can continue without reading long docs or asking repeated baseline questions.

## Default doc set
Create or maintain:
- `docs/brain/brain-map.md`
- `docs/brain/project-state.md`
- `docs/brain/nodes/facts/`
- `docs/brain/nodes/decisions/`
- `docs/brain/nodes/patterns/`
- `docs/brain/nodes/lessons/`
- `docs/brain/nodes/tasks/`
- `docs/brain/nodes/risks/`

Optional legacy docs may still exist, but do not require the user to read or maintain them.

## Fresh-session entrypoint
When starting work in a project with brain docs:
1. read `docs/brain/brain-map.md`
2. read `docs/brain/project-state.md`
3. open only the linked nodes relevant to the current task
4. inspect code when a node is stale, ambiguous, or conflicts with implementation

Do not default to reading every node.
Do not default to reading every long governance doc.

## Fresh-session activation
For strongest continuity, the project should have a small repo-level `AGENTS.md` pointer that tells future Codex sessions to read `docs/brain/brain-map.md` first.

Before writing or changing `AGENTS.md`:
- inspect whether it already exists
- ask whether to merge, replace, or keep it unchanged
- never overwrite existing project instructions silently

If no `AGENTS.md` pointer exists, the user can still start a fresh session by saying: `Rujuk docs/brain/brain-map.md dulu, kemudian sambung task ini.`

## Brain-map requirements
`brain-map.md` should be a concise map of content, not a narrative.

Include:
- project snapshot link
- active feature/task links
- key decisions
- reusable patterns
- known risks
- lessons that prevent repeated mistakes
- deprecated or stale-node section when needed

Keep it scannable enough for a fresh agent to route itself quickly.

## Project-state requirements
`project-state.md` is a short AI snapshot.

Include:
- purpose
- current status
- active branch/context if known
- implemented areas
- current priorities
- known gaps
- verification/startup notes
- last updated date

Keep it short. Prefer links to nodes over long explanations.

## Atomic node rules
One node = one durable concept.

Good node candidates:
- a technical decision that affects future implementation
- a reusable coding or UI pattern
- a confirmed project fact that agents often need
- a recurring lesson or trap
- an active task or risk that controls sequencing

Bad node candidates:
- obvious one-off details
- temporary scratch notes
- duplicated prose from another file
- speculation not confirmed by user, code, or execution

## Node frontmatter
Every node should start with:

```yaml
---
type: Fact | Decision | Pattern | Lesson | Task | Risk
status: Active | Deprecated
tags: []
relates_to: []
source: []
last_updated: YYYY-MM-DD
---
```

Use `source` for code paths, docs, user decisions, commands, or observed behavior.

## Linking rules
- Every node should link back to `../../brain-map.md` or be listed from `brain-map.md`.
- Link to related nodes only when the relationship is real.
- Avoid artificial links just to make a graph look dense.
- Prefer stable relative links.

## Maintenance after work
After meaningful work, Codex should check:
- Did project state change?
- Did a decision change?
- Did a reusable pattern emerge?
- Did a lesson or trap appear?
- Did an active task complete or become blocked?
- Did a risk appear, disappear, or change severity?
- Does `brain-map.md` need a new or updated link?

Update only impacted brain docs.
Do not ask the user to maintain brain docs manually.

## Deprecation rule
Do not silently rewrite history when a decision changes.

Prefer:
- mark the old node `status: Deprecated`
- add a short reason
- link to the replacement node
- update `brain-map.md`

Delete nodes only when they are pure noise or were created by mistake.

## Obsidian compatibility
Use plain Markdown and YAML frontmatter.
Obsidian is a viewer, not a dependency.
The project must remain usable by Codex and Git without Obsidian.

## Anti-patterns
Do not:
- create a node for every minor implementation detail
- make brain docs longer than the code context they are meant to replace
- let `brain-map.md` become a second README
- treat stale brain docs as truth when code inspection contradicts them
- push maintenance work back to the user by default
