# Platform Reference — Base44

**Última verificação:** 2026-09-02, documentação oficial do Base44.

Base44 combina builder por IA, editor visual, Code tab, hosting gerenciado e recursos de backend. Também oferece exportação, integração GitHub e CLI para desenvolvimento local. O risco de dependência continua real, mas decorre de serviços e semânticas gerenciadas, não da ausência absoluta de código.

Fontes oficiais principais:

- https://docs.base44.com/Getting-Started/Quick-start-guide
- https://docs.base44.com/developers/app-code/editor/code-tab
- https://docs.base44.com/developers/app-code/local-development/github
- https://docs.base44.com/developers/references/cli/get-started/overview
- https://docs.base44.com/developers/backend/overview/local-dev/get-started
- https://docs.base44.com/developers/references/cli/commands/eject
- https://docs.base44.com/developers/backend/overview/project-structure

## Primeiro: identifique a superfície

Não misture quatro estados diferentes:

1. **Builder app:** construído e publicado pelo editor Base44.
2. **GitHub-synced app:** código sincronizado com um repositório; integração e regras de branch precisam ser verificadas antes da mudança.
3. **CLI backend project:** recursos declarados localmente em `base44/` e enviados por comandos específicos.
4. **Ejected project:** cópia independente com novo app ID; schemas e recursos são copiados, dados não.

Antes de qualquer prompt, registre qual superfície existe, quem é owner, qual ambiente é live e onde está a fonte de verdade.

## Código, GitHub e saída

Base44 permite visualizar/editar código, exportar ZIP/GitHub e trabalhar localmente. GitHub sync e eject têm semânticas próprias e podem ser irreversíveis ou criar um projeto separado.

A análise de portabilidade deve separar:

- frontend e funções exportáveis;
- schemas de entidades e configurações de recursos;
- dados existentes e processo de exportação/migração;
- autenticação e identidades;
- hosting e domínio;
- connectors e credenciais;
- agents e comportamentos gerenciados;
- logs, analytics e automações;
- substitutos fora da plataforma.

Nunca diga “sem lock-in” nem “reescrita total obrigatória” sem mapear essas camadas.

## Entidades e permissões

Modele em linguagem de negócio, mas não aceite permissões automáticas como prova de isolamento. Para cada entidade, defina:

- owner/tenant;
- campos e relações;
- quem pode criar, ler, editar e excluir;
- operações privilegiadas;
- validação e invariantes;
- retenção e deleção;
- teste negativo entre usuários/organizações.

## Functions, agents e connectors

Recursos locais podem incluir:

```text
base44/
  entities/
  functions/
  agents/
  connectors/
  auth/
```

Para cada recurso, registre contrato, dados acessados, ambiente, secrets, limites, idempotência, logs e confirmação humana.

Agents e connectors não recebem autonomia genérica. Ações externas, comunicação, pagamento, alteração de calendário, dados ou produção exigem escopo explícito e aprovação quando houver impacto.

## Desenvolvimento local

O CLI permite validar/sincronizar recursos, iniciar backend local e executar scripts. O backend local pode usar dados em memória e não deve ser confundido com produção.

Fluxo recomendado:

1. confirme projeto e credenciais da CLI;
2. revise `.app.jsonc`, `.gitignore` e ambientes;
3. puxe somente a configuração necessária;
4. rode backend e frontend localmente;
5. use dados sintéticos;
6. valide tipos, funções e fluxos;
7. revise diff;
8. só então proponha push/deploy.

Comandos como `auth pull` podem sobrescrever arquivo local, e `auth push` altera configuração remota. Trate ambos como ações de alto cuidado; não use `--yes` para pular confirmação em fluxo assistido.

## Discuss/plan prompt

```text
Analise o estado atual sem publicar nem alterar recursos live.

Superfície: [builder / GitHub sync / CLI / ejected]
Objetivo: [resultado]
Escopo: [recursos]
Preservar: [comportamentos/dados]

Entregue:
1. fatos observados;
2. entidades, funções, agents, connectors e auth envolvidos;
3. riscos de dados e permissões;
4. plano pequeno;
5. verificação local/clone;
6. rollback ou recuperação;
7. efeito sobre portabilidade.
```

## Prompt atômico

```text
Implemente somente [mudança] no ambiente não produtivo.

Recursos permitidos: [lista]
Preservar: [itens]
Contrato: [comportamento]
Permissões: [regras]
Dados de teste: sintéticos
Verificação: [passos]

Não publique, não execute deploy, auth push, connector write, pagamento ou migração.
Mostre mudanças, resultados e pontos cegos.
```

## Verificação e release

Antes de live:

- teste no clone/local quando possível;
- tipos regenerados quando recursos mudarem;
- permissões e isolamento testados;
- functions e agents com erro/timeout/retry controlados;
- connectors com escopo mínimo;
- dados e backups confirmados;
- diff/commit revisado;
- plano de saída atualizado;
- publish/deploy separado e aprovado.

## Claims voláteis

Planos, créditos, recursos, integrações e limites mudam. Verifique a documentação oficial no dia da decisão. Não grave preço ou disponibilidade de tier como regra permanente.
