---
name: base44-prompt-builder
description: >
  Guides planning, building, repairing, testing and releasing managed web apps with the current Base44 builder, Code tab, GitHub sync and CLI. Use when the user mentions Base44, Base44 entities, functions, agents, connectors, local development, eject, or asks for structured Base44 prompts. Inspect the existing app and choose managed-platform trade-offs explicitly.
license: MIT
---

# Base44 Prompt Builder

This skill treats Base44 as a managed application platform with editable/exportable code and proprietary service semantics. It does not repeat the obsolete claim that users never receive code.

## Origin version check

Canonical source:

```text
https://github.com/AndreAlmeidaDC/base44-prompt-builder
```

At meaningful use, follow `references/version-check.md`. Never self-update silently.

## Load order

1. Read `references/vibecode-core.md`.
2. Read `references/platform-base44.md`.
3. Use `references/archetypes.md` only when platform choice is open.
4. Apply the smallest project mode that fits.

## Non-negotiable boundaries

- Inspect existing app, repository or exported code before prescribing structure.
- Separate builder app, GitHub-synced app, CLI backend project and ejected project.
- Model entities, functions, agents, connectors and auth only when required.
- Treat data ownership, service dependency and exit path as architecture decisions.
- Test locally or in a clone before changing live resources.
- Do not push auth, deploy resources, publish, connect production data, spend money or perform external writes without explicit approval.

## Output

Return only the artifact needed now: app knowledge, Discuss/plan prompt, entity contract, atomic build prompt, local/CLI prompt, verification prompt or exit plan.

## Change history

| Date | Version | Change |
|---|---|---|
| 2026-09-02 | 2026.09.02 | Rebuilt around current code access, GitHub sync, CLI/local development, eject, managed services, agents/connectors and explicit exit planning. |
