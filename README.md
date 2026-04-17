# Project Governance Docs

A small OpenClaw skill for two common documentation/governance workflows:

- **greenfield** — define the project before coding
- **retrofit** — document and govern the current implementation first

It also supports a simple workflow selector:

- `docs menu`
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

## Modes

### Greenfield
Use when the project has not started yet and you want foundation docs before coding.

### Retrofit
Use when the project already exists and you want docs/governance based on the current implementation first.

## Quick invoke

If you say `docs menu`, the skill should present:

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

## Usage examples

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
update impacted docs
```

### Before risky work
```text
backup project
```

### Recover from checkpoint
```text
restore project
```

## License

MIT
