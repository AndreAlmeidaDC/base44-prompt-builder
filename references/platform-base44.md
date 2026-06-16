# Platform Reference — Base44

Base44 (base44.com) é um AI app builder com backend proprietário integrado.
Adquirido pela Wix em junho 2025 (~$80M). Disponível como app no ChatGPT ("@Base44").

> **Pré-requisito:** complete as Fases 1 a 4 do CORE antes de usar esta referência.
> Leia a seção de Lock-in antes de começar — é uma decisão com implicações sérias.

---

## ⚠️ Aviso Obrigatório: Lock-in de Código

O Base44 é o único app builder desta skill onde **você NÃO tem o código fonte**.
O app roda no backend proprietário do Base44.

Isso significa:
- Sem portabilidade: se você precisar migrar, terá que reescrever do zero.
- Se o Base44 mudar de preço drasticamente ou descontinuar um recurso, você está preso.
- Sem customização profunda de backend: você está limitado ao que a plataforma suporta.

**Quando vale usar mesmo assim:**
- Protótipos e validação de ideia rápida (antes de comprometer com dev real)
- Ferramentas internas de equipe onde portabilidade não é prioridade
- MVPs para validar demanda antes de contratar desenvolvimento
- Dashboards e CRMs simples que não precisam escalar muito

**Quando NÃO usar:**
- Produto que vai a produção com usuários reais e precisa escalar
- Lógica server-side complexa, APIs customizadas, microserviços
- Setores regulados (sem SOC 2, HIPAA, audit logs)
- Quando você precisar do código para continuar em outro ambiente

---

## O Conceito Central: Entidades (não schema, não tabelas)

O vocabulário do Base44 é orientado a **entidades de negócio**, não a banco de dados.
Você não escreve SQL. Você descreve o que o negócio precisa.

> "O app tem as entidades: Clientes, Pedidos, Produtos. Um Pedido pertence a um Cliente
> e contém vários Produtos."

O Base44 cria automaticamente:
- Tabelas com os campos necessários
- Relações entre entidades
- Permissões e políticas de acesso
- APIs CRUD

---

## Modos de Interação (economia de créditos)

**Modo normal (1 crédito/prompt):** gera ou modifica o app.

**Discuss mode (0.3 créditos/interação):** conversa com a IA SEM gerar código.
Use antes de gerar para: planejar, validar entendimento, explorar alternativas.
**Recomendado: use Discuss mode para toda a Fase 1 e 2 do CORE antes de gerar.**

**Visual Edit mode (sem crédito extra):** ajustes visuais diretos na interface
(cores, layout, texto) sem precisar de prompt.

**Integration credits:** sistema separado para integrações externas (Stripe, Slack, APIs).

---

## Perguntas adicionais de intake (Fase 1 do CORE)

Após as perguntas genéricas, adicione em Discuss mode:

12. Quais são as **entidades de negócio** do seu produto? (ex: Clientes, Pedidos,
    Produtos, Tarefas, Documentos, etc.)
13. Quais **integrações externas** precisará? O Base44 tem 20+ pré-construídas:
    Stripe, Gmail, Slack, Google Drive, Salesforce, Zapier — especifique quais.
14. Haverá **múltiplos tipos de usuário** com permissões diferentes?
    (admin, gerente, operador, cliente — descreva o que cada um pode fazer)
15. Tem um site existente para usar como referência? (o "Create from URL" pode ajudar)

---

## Modelagem de Entidades (Fase 2 do CORE — formato Base44)

Em vez de schema de banco, descreva as entidades em linguagem de negócio:

```
Entidades do [Nome do Produto]:

1. Cliente
   - Nome, email, telefone, empresa
   - Status: ativo / inativo
   - Relacionado a: Pedidos (1 cliente → N pedidos)

2. Pedido
   - Número, data, valor total, status (novo/em andamento/concluído/cancelado)
   - Pertence a: Cliente
   - Contém: Itens do Pedido

3. Produto
   - Nome, descrição, preço, estoque
   - Categoria: [lista de categorias]

4. Item do Pedido
   - Relacionado a: Pedido, Produto
   - Quantidade, preço unitário

Permissões:
- Admin: acesso completo a todas as entidades
- Vendedor: criar/editar Pedidos e Clientes; visualizar Produtos
- Viewer: somente leitura em tudo
```

---

## Brief Inicial (formato Base44)

```
# [Nome do Produto] — Base44 Brief

## Produto
[O que é, problema que resolve, usuário principal]

## Entidades Principais
[Lista de entidades com campos e relações da Fase 2]

## Usuários e Permissões
[Roles e o que cada um pode fazer]

## Funcionalidades do MVP (em ordem)
1. [Feature 1]: [o que o usuário faz]
2. [Feature 2]: [o que o usuário faz]
...

## Integrações necessárias
- [Integração 1]: [para quê]
- [Integração 2]: [para quê]

## Estilo visual
[Descrição do estilo: clean/corporativo/colorido, cores principais, tom]

## Build Order
1. Auth + roles de usuário
2. [Entidade principal] + CRUD básico
3. [Feature 1]
4. [Feature 2]
...
N. Integrações externas
N+1. Dashboard / relatórios
```

---

## Iteração no Base44

**Chat conversacional:** mudanças via prompt em linguagem natural.
> "Adiciona um campo de telefone no formulário de cliente"
> "Muda o status do pedido para ter também a opção 'aguardando pagamento'"

**Visual Edit mode:** para ajustes de aparência sem gastar créditos de prompt.
Clique em elementos da interface para editar diretamente.

**Dica:** use Discuss mode para validar a ideia de uma mudança antes de gerar.
Evita gastar crédito em algo que você ainda não tem certeza.

---

## Artefatos de Reancoragem (Fase 5.5 do CORE)

Quando o Base44 perder o fio, recole em Discuss mode:
- Lista de entidades e relações
- Roles e permissões definidos
- Integrações ativas
- Estado atual do app (o que já funciona)

---

## Integrações Disponíveis (pré-construídas no Base44)

Categorias disponíveis (verificar docs.base44.com para lista atual):
- **Pagamentos:** Stripe
- **Comunicação:** Gmail, Slack
- **Produtividade:** Google Drive, Zapier
- **CRM:** Salesforce
- **Automação:** Zapier, webhooks customizados
- **AI/Content:** integrações de AI content generation

Para ativar: mencione no prompt que precisa da integração e siga as instruções.
Integration credits são cobrados separadamente por uso (não por configuração).

---

## Limitações e Gotchas do Base44

- **Lock-in**: leia o aviso no topo desta referência antes de começar.
- **Não é app mobile nativa**: web responsivo, funciona bem em mobile,
  mas não é publicado na App Store/Google Play.
- **Escala limitada**: ótimo para protótipos e ferramentas internas. Para
  produção com volume real, prepare-se para encontrar limites.
- **Backend functions** (lógica mais complexa) requerem plano pago.
- **Custom domains** também requerem plano pago.
- **GitHub integration** disponível nos planos pagos.
- **Wix ownership**: adquirido em jun/2025. Estabilidade maior, mas evolução
  pode ser influenciada pela agenda da Wix.
