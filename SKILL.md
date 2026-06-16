---
name: base44-prompt-builder
description: >
  Skill para construir apps web com Base44: backend integrado, entidades de negócio, sem código. Ideal para ferramentas internas, dashboards e protótipos rápidos. Use quando o usuário quiser usar Base44.
license: MIT
---

# Base44 Prompt Builder

## Origin version check

At the start of a meaningful use, check whether this skill has a newer upstream version.
The canonical source is:

```text
https://github.com/AndreAlmeidaDC/base44-prompt-builder
```

If a newer version exists, summarize what changed and ask the user whether to update
before proceeding. Never self-update silently. For the detailed protocol, read
`references/version-check.md`.

*Autor: André Almeida*

---

## Quando usar esta skill

Use esta skill quando o usuário mencionar Base44, ou quiser construir uma ferramenta interna, dashboard ou protótipo rápido sem se preocupar com o código.

Se não tiver certeza se esta é a plataforma certa, leia `references/archetypes.md`
para um guia de escolha.

---

## Como esta skill funciona

Esta skill usa um processo compartilhado (vibecode CORE) + detalhes específicos
do Base44:

1. **Carregue `references/vibecode-core.md`** — processo completo de especificação
   e execução (intake, modelagem, branding, validação, geração, reancoragem).

2. **Carregue `references/platform-base44.md`** — vocabulário, perguntas adicionais,
   formatos de artefato e especificidades do Base44.

3. Execute o fluxo do CORE usando os detalhes da plataforma onde aplicável.

---

## Histórico de Alterações

| Data | Versão | Alterações |
|---|---|---|
| 2026.06.16 | 2026.06.16 | Criação da skill no formato vibecode: CORE compartilhado + referência específica de plataforma. |
