# Agent skills

harv's custom/personal agent skills. A small collection of `SKILL.md` packages for OpenCode and other agents that support the open agent skills format.

## Skills

| Skill | Description |
| --- | --- |
| [slop-audit](skills/slop-audit/SKILL.md) | Audits interfaces and codebases for AI slop: reflexive type, decoration, copy, and architecture choices that make generated work look generated. |

## Install

```powershell
npx skills add haroldjeshua/agent-skills@slop-audit -g -y
```

Drop `-g` to install into the current project instead.

## Update

```powershell
npx skills update
```

## Structure

```text
skills/
└── slop-audit/
    ├── SKILL.md
    └── references/
        ├── interface.md
        └── codebase.md
```

Each skill lives in its own folder under `skills/`. A `SKILL.md` file with `name` and `description` frontmatter is the entry point. Reference files sit beside it and are linked from `SKILL.md`.

## Adding a skill

1. Create `skills/<name>/SKILL.md`.
2. Add `name` and `description` frontmatter.
3. Put reference files beside it and link them from `SKILL.md`.
4. Copy the folder into your global skills directory or install it with `npx skills`.

## Compatibility

Works with agents that support the `SKILL.md` format and the `npx skills` CLI.
