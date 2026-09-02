# base44-prompt-builder

Workflow skill for the current Base44 platform.

The legacy edition claimed Base44 exposed no source code and required a total rewrite to leave. Current official workflows include the Code tab, ZIP/GitHub export, two-way GitHub sync, CLI-based local development and `eject`. The managed backend, authentication, hosting, data and resource semantics still create dependency that must be mapped rather than denied.

## Core sequence

```text
inspect mode -> map managed resources -> plan -> atomic change -> verify -> approved deploy/publish
```

## Supported surfaces

- AI/visual builder;
- Code tab;
- GitHub-synced application;
- CLI backend project;
- local development;
- ejected project;
- entities, functions, agents, connectors and auth.

## Verification

```bash
python3 scripts/validate_skill.py
```

Version `2026.09.02` is a breaking correction of the old no-code/no-export model.
