# Estratégia de Tokens, Custo, Latência e Observabilidade

## Status

Proposta do Marco 003. Os valores iniciais são orçamentos de projeto e deverão ser calibrados no piloto.

## Objetivo

Garantir que especialização e rastreabilidade não criem um fluxo caro, lento ou impossível de operar.

## Princípios

- medir por OPP e por etapa;
- não enviar ao modelo o que pode ser resolvido deterministicamente;
- não enviar texto bruto quando componente aprovado basta;
- registrar tokens reais retornados pelo provedor;
- estimativas não substituem uso real;
- custos de retry são atribuídos à OPP;
- p95 importa mais que média isolada;
- logs não armazenam conteúdo completo por conveniência;
- feature flags permitem desligar etapas experimentais.

## Etapas mensuradas

1. validação da OPP;
2. resolução curricular;
3. construção do QueryPlan;
4. busca lexical;
5. embedding da consulta;
6. busca semântica;
7. fusão/deduplicação;
8. reranking, quando existir;
9. montagem do contexto;
10. geração;
11. cada quality gate;
12. entrega.

## Orçamento de contexto

### Entradas fixas

- contrato do agente;
- contrato do produto;
- instruções de segurança;
- requisitos da OPP;
- escopo curricular compacto.

### Entradas recuperadas

- máximo padrão de oito componentes;
- conteúdo somente da versão aprovada;
- metadados essenciais;
- referências e atribuições;
- sem capítulos completos.

### Limites propostos para experimento

Não são compromissos definitivos:

- `maxRetrievedComponents`: 8;
- `targetRetrievedComponents`: 3–5;
- `maxContextTokens`: faixa a calibrar por modelo e produto;
- `maxOutputTokens`: diferente por produto;
- `maxRetries`: 1 ou 2 conforme gate e custo;
- `maxValidationModelCalls`: orçamento explícito.

O contrato técnico deverá usar políticas configuráveis, não números espalhados no código.

## TokenBudgetDecision

Campos:

- `oppId`;
- `productType`;
- `modelPolicyId`;
- `estimatedFixedTokens`;
- `estimatedContextTokens`;
- `estimatedOutputTokens`;
- `hardLimit`;
- `selectedComponentIds`;
- `excludedForBudget`;
- `decisionReason`;
- `budgetVersion`.

## Custos

Registrar por execução:

- provider;
- modelo;
- preço vigente na configuração interna;
- input tokens;
- cached input, quando aplicável;
- output tokens;
- chamadas auxiliares;
- embedding tokens;
- reranker;
- custo estimado e custo reconciliado;
- moeda;
- tabela de preços versionada;
- timestamp.

Não embutir preço em regras do domínio.

## Latência

Métricas:

- p50;
- p90;
- p95;
- p99 para investigação;
- timeout;
- retries;
- tempo em fila para jobs;
- tempo por gate;
- tempo de provedor;
- tempo de banco.

Acordos iniciais deverão ser definidos após baseline da infraestrutura real. O Marco 003 não inventa SLA sem medição.

## Traces

Um trace por OPP, com spans:

- `opp.validate`;
- `curriculum.resolve`;
- `retrieval.plan`;
- `retrieval.lexical`;
- `retrieval.embedding`;
- `retrieval.semantic`;
- `retrieval.fusion`;
- `retrieval.rerank`;
- `context.assemble`;
- `generation.run`;
- `validation.<gate>`;
- `delivery.run`.

Atributos seguros:

- IDs e versões;
- tenant pseudonimizado ou ID interno;
- produto;
- status;
- quantidades;
- tokens;
- custo;
- latência;
- códigos de falha;
- feature flags.

Não registrar texto completo como atributo.

## Métricas operacionais

### Retrieval

- candidatos por canal;
- itens após filtro;
- itens finais;
- taxa de insuficiência;
- fallback lexical;
- relevância offline;
- vazamento de escopo;
- tamanho do contexto.

### Geração

- tokens por produto;
- custo por produto;
- retries;
- falhas de schema;
- modelo utilizado;
- taxa de sucesso.

### Qualidade

- aprovação por gate;
- revisão humana;
- falso positivo/negativo;
- autoria;
- alinhamento;
- incidentes.

### Negócio/piloto

- tempo poupado percebido;
- taxa de material aproveitável;
- edição necessária;
- preferência versus baseline;
- abandono;
- pedidos fora de escopo.

## Logs estruturados

Campos básicos:

- timestamp;
- level;
- service/module;
- eventName;
- correlationId;
- oppId;
- runId;
- tenantId minimizado;
- status;
- durationMs;
- errorCode;
- metadata segura.

Redação automática deve remover:

- chaves;
- bearer tokens;
- e-mails;
- nomes;
- conteúdo integral;
- trechos protegidos;
- prompts completos.

## Alertas

Alertas Must:

- qualquer vazamento de tenant;
- fonte bloqueada recuperada;
- pacote curricular incorreto;
- produto entregue após gate falho;
- taxa anormal de erro;
- custo por OPP acima do hard limit;
- loop de retry;
- falha de auditoria;
- indisponibilidade de corpus.

Alertas Should:

- aumento de p95;
- crescimento de contexto;
- queda de relevância no conjunto de regressão;
- aumento de insuficiência;
- drift de avaliação humana.

## ModelPolicy

A política centraliza:

- modelos permitidos por finalidade;
- limites de tokens;
- timeout;
- retry;
- fallback;
- temperatura e parâmetros;
- política de dados;
- vigência;
- feature flag;
- versão.

O agente referencia uma política; não instancia cliente diretamente.

## Comparação com agente genérico

Medir com o mesmo pedido e, quando tecnicamente possível, o mesmo modelo:

- tokens fixos;
- tokens de contexto;
- tokens de saída;
- custo;
- latência;
- qualidade;
- edição humana;
- erros de escopo;
- rastreabilidade.

## Gates econômicos

A aprovação do MVP não requer o menor custo absoluto, mas exige:

- custo mensurável;
- ausência de chamadas redundantes;
- orçamento configurável;
- justificativa para reranker e validadores com modelo;
- comparação com baseline;
- caminho para redução sem comprometer gates.

## Decisão proposta

**ADR-024 — Tokens, custo e latência são observados por etapa da OPP; modelos são acessados por políticas versionadas e não diretamente pelos agentes.**

Status: proposta, aguardando aprovação.
