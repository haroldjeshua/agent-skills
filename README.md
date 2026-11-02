# Agent skills

Custom skills for OpenCode and other agents that support the `SKILL.md` format.

## Skills

### slop-audit

Audits interfaces and codebases for AI slop: the reflexive type, decoration, copy, and architecture choices that make generated work look generated.

- `SKILL.md`: audit process, severity triage, report format, and false-positive rules.
- `references/interface.md`: interface tells and the source audit.
- `references/codebase.md`: codebase tells and the source audit.

Install globally:

```powershell
npx skills add haroldjeshua/agent-skills@slop-audit -g -y
```

Update later:

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

Each skill lives in its own folder under `skills/`. A `SKILL.md` file with `name` and `description` frontmatter is the entry point.
