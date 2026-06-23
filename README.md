# base44-prompt-builder

Skill de IA para construir no **Base44** com método: entidades de negócio bem definidas,
créditos economizados com os modos certos, e a decisão de lock-in tomada de olhos
abertos — antes de você investir semanas no que não pode levar embora.

---

## O problema que esta skill resolve

O Base44 tem a proposta mais conveniente da categoria: você descreve, ele entrega o app
inteiro — interface, banco, autenticação, tudo num backend já incluído, sem configurar
nada externo. A conveniência é real. Mas ela esconde duas armadilhas.

A primeira é de eficiência: sem estrutura, "descreva o que quer" vira tentativa e erro,
e cada geração consome crédito. Quem não conhece os modos de trabalho do Base44 gasta
crédito gerando quando poderia estar planejando de graça.

A segunda é mais séria e quase ninguém para para considerar: **no Base44, o código não é
seu**. O app roda no backend proprietário deles. Se um dia você precisar escalar além do
que a plataforma permite, ou migrar para outro lugar, é começar do zero. Para protótipos
e ferramentas internas isso pode ser perfeitamente aceitável — mas é uma decisão que tem
que ser consciente, tomada antes, não uma descoberta depois de semanas de trabalho.

## Como a skill foi pensada

A skill foi desenhada para extrair a conveniência do Base44 sem cair nas duas armadilhas:
ela força a **decisão de lock-in logo no início** e estrutura o trabalho no **vocabulário
e nos modos econômicos** que o Base44 oferece.

### Explorando as forças do Base44

- **O Base44 cria backend a partir de entidades de negócio.** A skill aproveita isso
  modelando o produto em entidades (Clientes, Pedidos, Produtos) e suas relações, em
  linguagem de negócio — exatamente o que o Base44 transforma em tabelas, relações e
  permissões automaticamente.
- **O Base44 tem Discuss mode** (conversar com a IA sem gerar código, a uma fração do
  crédito). A skill orienta a usar Discuss mode para todo o planejamento antes de gerar.
- **O Base44 tem Visual Edit mode** (ajuste visual direto, sem consumir crédito de
  mensagem). A skill direciona ajustes de aparência para lá.
- **O Base44 tem 20+ integrações prontas** (Stripe, Slack, Gmail, etc.). A skill coleta
  as integrações necessárias no brief, em vez de adicioná-las improvisadamente depois.

### Mitigando as fraquezas do Base44

- **O lock-in invisível.** Mitigado com um aviso explícito no início: a skill esclarece
  que o código não é exportável e te faz decidir, conscientemente, se o Base44 é a escolha
  certa para o seu caso antes de começar.
- **Desperdício de crédito.** Mitigado com um guia de quando usar cada modo: Discuss
  (planejar, custo baixo), Visual Edit (ajuste visual, sem custo) e geração (1 crédito,
  só quando vale).
- **Modelagem confusa por usar vocabulário errado.** Mitigada falando em entidades de
  negócio, não em schema SQL ou migrations — que não é como o Base44 pensa.
- **Expectativa de escalar para produção pesada.** Mitigada deixando claro o melhor caso
  de uso (protótipos, ferramentas internas, dashboards, MVPs) e sinalizando os limites
  para lógica server-side complexa.

## O que a skill faz, passo a passo

**Aviso de lock-in.** Antes de tudo, esclarece que o código fica no Base44 e pergunta se
isso faz sentido para o seu caso específico.

**Intake orientado a entidades.** Coleta as entidades de negócio, suas relações, os
papéis de usuário e as integrações externas necessárias.

**Modelagem em linguagem de negócio.** Produz o modelo de entidades no formato que o
Base44 entende — sem SQL, com relações e permissões por papel.

**Brief estruturado.** Monta o prompt inicial com entidades, fluxo e ordem de build,
pronto para colar no Base44.

**Guia de créditos e loop.** Orienta o uso de Discuss e Visual Edit para economizar, e
conduz o loop de feedback até o app pronto.

## Como usar

1. Carregue esta skill no seu chat de IA (Claude, ChatGPT, etc.)
2. Leia o aviso de lock-in e decida se o Base44 é a escolha certa para o seu caso
3. Responda o intake — com atenção a quais entidades e quais integrações
4. Use o Discuss mode do Base44 para alinhar antes de gerar
5. Cole o brief e siga o loop de feedback

A skill gera os prompts; você faz a ponte de copiar e colar para o Base44. Ela não
se conecta ao Base44 nem executa nada por você — é uma ferramenta de raciocínio e
especificação, não de automação.

## FAQ

**O que exatamente significa "o código não é meu"?**
O app roda no backend proprietário do Base44. Você não recebe um projeto de código que
possa hospedar ou continuar em outro lugar. Se sair da plataforma, reconstrói do zero.

**Então o Base44 é uma má escolha?**
Não — é uma escolha situacional. Para protótipo rápido, validação de ideia ou ferramenta
interna da equipe, a conveniência compensa. Para um produto que vai escalar e precisa de
portabilidade, pense duas vezes. A skill te ajuda a decidir.

**O que é Discuss mode e por que usar?**
É o modo de conversar com a IA do Base44 sem gerar código, a uma fração do crédito. Serve
para planejar e alinhar antes de gastar crédito gerando. A skill recomenda usá-lo para
todo o planejamento.

**Por que falar em "entidades" e não "tabelas"?**
Porque é assim que o Base44 pensa. Você descreve as entidades de negócio e ele cria as
tabelas, relações e permissões. Usar vocabulário de banco de dados atrapalha mais do que
ajuda.

**Dá para integrar com Stripe, Slack, etc.?**
Sim, o Base44 tem mais de 20 integrações prontas. A skill coleta quais você precisa no
brief. Lembre que integrações externas consomem um tipo de crédito separado.

**A skill se conecta ao Base44 automaticamente?**
Não. Ela gera os prompts e você usa no Base44. Funciona em qualquer chat de IA.

**Preciso ativar acessibilidade?**
Não. Acessibilidade é opcional e fica desligada por padrão. Logo no início do fluxo a
skill pergunta se o app terá interface web usada por terceiros ou se precisa atender a
requisito de acessibilidade. Se for uso interno, protótipo ou app da própria equipe,
responda que não e siga sem nenhum peso extra. Se responder que sim, a skill passa a
tratar acessibilidade como requisito de toda a UI, com base em
`references/accessibility-web.md`.

## Estrutura do repositório

```
SKILL.md                          # Ponto de entrada: papel e como usar
references/
  vibecode-core.md                # Processo de engenharia (compartilhado na família)
  platform-base44.md              # Entidades, Discuss/Visual Edit, lock-in, créditos
  archetypes.md                   # Guia de escolha de plataforma
  version-check.md                # Protocolo de auto-atualização
  accessibility-web.md            # Acessibilidade web (opcional, ver gate na Fase 1)
templates/
  PRD.md                          # Template de requisitos de produto
  DATA_MODEL.md                   # Template de modelo de dados
  USER_FLOW.md                    # Template de fluxo de usuário
scripts/
  validate_skill.py               # Validação local da skill
```

## Por que existem 6 skills e não uma só

Essa pergunta é legítima — o processo de fundo (especificar antes de gerar, modelar
dados, iterar de forma atômica, reancorar quando a IA perde o contexto) é o mesmo em
todas as plataformas. Seria tentador fazer uma skill única que cobre tudo.

Não fizemos, por três razões:

**1. Contexto desperdiçado.** Uma skill única carregaria as particularidades de seis
plataformas em toda sessão, sendo que você só usa uma. A maior parte do que entrasse no
contexto seria ruído para a sua tarefa. Skills separadas carregam só o que importa para
a plataforma que você escolheu.

**2. As plataformas divergem mais do que parecem.** O v0 gera componentes, não apps.
O a0.dev fala de telas e navegação, não de páginas e rotas. O Base44 não te dá o código.
O emergent usa MongoDB e um time de agentes; os outros não. Espremer tudo num fluxo único
exigiria tantos "se for plataforma X, faça Y" que o resultado seria confuso e frágil.

**3. Evolução independente.** Cada plataforma muda no seu ritmo. Quando uma lança um
recurso novo, a skill dela é atualizada sem tocar nas outras cinco.

O que é genuinamente compartilhado (o processo de engenharia) vive em um único arquivo,
`references/vibecode-core.md`, idêntico em todas as skills. Assim evitamos duplicação no
que importa e mantemos independência onde importa.

## Família vibecode

| Skill | Plataforma | Melhor para |
|---|---|---|
| [lovable-prompt-builder](https://github.com/AndreAlmeidaDC/lovable-prompt-builder) | Lovable | App web full-stack com fluxo guiado passo a passo |
| [bolt-prompt-builder](https://github.com/AndreAlmeidaDC/bolt-prompt-builder) | bolt.new | App web full-stack com brief único e controle total |
| [v0-prompt-builder](https://github.com/AndreAlmeidaDC/v0-prompt-builder) | v0 (Vercel) | Componentes React/shadcn de alta qualidade |
| [a0-prompt-builder](https://github.com/AndreAlmeidaDC/a0-prompt-builder) | a0.dev | App mobile nativo iOS/Android |
| **base44-prompt-builder** (esta skill) | Base44 | Ferramenta interna / protótipo com backend incluído |
| [emergent-prompt-builder](https://github.com/AndreAlmeidaDC/emergent-prompt-builder) | emergent.sh | Full-stack multi-agente (web + mobile), código seu |

## Licença

MIT — André Almeida
