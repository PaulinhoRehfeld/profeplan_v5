# Primeiro Pull Request de Código — Proposta

## Status

Proposta do Marco 003. Ainda não autorizado.

## Condições anteriores

O primeiro PR de código só poderá ser aberto após:

1. aprovação do Marco 003;
2. decisão do repositório canônico;
3. sincronização da documentação aprovada no repositório de implementação;
4. confirmação da branch base;
5. execução do build, typecheck e testes existentes sem alterações;
6. inventário dos padrões do pacote de tipos;
7. Stories selecionadas cumprirem a DoR.

## Repositório recomendado

Condicionalmente, `PaulinhoRehfeld/profeplan`, por conter o monorepo executável.

Caso outra decisão seja tomada, este documento deverá ser revisado antes do código.

## Título sugerido

`feat(knowledge-factory): add versioned domain contracts and fixtures`

## Objetivo único

Adicionar contratos puros, versionados e testáveis para o núcleo da Knowledge Factory, sem persistência, IA, API, migrations ou alteração de comportamento da aplicação.

## Por que este é o PR mais seguro

- não toca produção ou banco;
- não depende de provider;
- não exige fonte real;
- permite revisão conceitual antes da infraestrutura;
- fornece tipos únicos para os lotes seguintes;
- reduz risco de cada pacote criar schema próprio;
- pode ser revertido sem migração de dados;
- é testável com fixtures sintéticas.

## Escopo

### Contratos

- `KnowledgeSource`;
- `SourceVersion`;
- `SourcePermission`/evento;
- `SourceSegment`;
- `PedagogicalComponent`;
- `PedagogicalComponentVersion`;
- `ComponentSourceEvidence`;
- `CurriculumPackage`;
- `CurriculumNode`;
- `ComponentCurriculumLink`;
- `AgentProfile` e `AgentKnowledgeScope`;
- `ProductionOrder` e estados;
- `ProductionOrderEvent`;
- `QueryPlan`;
- `SufficiencyResult`;
- `ContextPackage`;
- `ValidationFinding`;
- `DeliveryContract` e payloads dos quatro produtos.

### Enums

- tipos de fonte;
- licença/permissão;
- estados de fonte, componente e OPP;
- tipos de componente;
- tipos de produto;
- resultados de gate;
- códigos de insuficiência.

### Fixtures

- exemplos válidos;
- campos obrigatórios ausentes;
- fonte bloqueada;
- componente draft e approved;
- MG válido e RS bloqueado;
- OPP válida e fora de escopo;
- contrato de entrega por produto.

### Testes

- schemas;
- enums inválidos;
- transições permitidas/proibidas;
- serialização;
- versões;
- invariantes puras;
- nenhuma dependência externa.

## Local proposto

Preferência:

- ampliar `packages/types` caso ele seja o pacote canônico de contratos sem dependências de domínio incompatíveis;
- ou criar subdiretório interno claramente nomeado dentro desse pacote.

Não criar novo pacote antes de o Codex demonstrar que `packages/types` é inadequado.

Estrutura indicativa, não obrigatória:

```text
packages/types/src/knowledge-factory/
├── source.ts
├── segment.ts
├── component.ts
├── curriculum.ts
├── agent.ts
├── production-order.ts
├── retrieval.ts
├── validation.ts
├── delivery.ts
├── enums.ts
├── index.ts
└── __tests__/
```

## Dependências

Preferir ferramentas de schema e teste já existentes no monorepo.

Se runtime schema exigir biblioteca nova:

- verificar se já existe em outro workspace;
- justificar escolha;
- comparar custo de dependência;
- obter aprovação antes de instalar.

## Stories parcialmente atendidas

Este PR não conclui integralmente as Stories de negócio, mas cria base verificável para:

- US-002.1;
- US-002.2;
- US-003.2;
- US-004.1;
- US-004.2;
- US-004.3;
- US-006.1;
- US-010.1;
- US-014.1;
- US-015.1;
- US-016.1.

A descrição do PR deve dizer explicitamente que são entregues apenas contratos e invariantes, não capacidades completas.

## Fora do escopo

- banco;
- Prisma;
- Supabase;
- migrations;
- RLS;
- buckets;
- embeddings;
- busca;
- OpenAI;
- agentes;
- prompts;
- BFF;
- frontend;
- Gráfica;
- dados PNLD reais;
- RS;
- novos agentes.

## Critérios de aceite

- contratos compilam em TypeScript strict;
- API pública do pacote é explícita;
- todos os contratos possuem versão;
- fixtures não contêm dados reais ou material protegido;
- invariantes críticas possuem testes;
- nenhum arquivo fora do pacote e documentação necessária é alterado, salvo configuração mínima justificada;
- build/typecheck/test do monorepo permanecem aprovados;
- nenhuma dependência é instalada sem aprovação;
- documentação aponta para os contratos aprovados do Marco 003;
- diff é revisável e não mistura refactor.

## Plano de rollback

- revert do PR;
- não há dado a migrar;
- não há feature flag necessária porque nenhum fluxo usa os contratos ainda;
- exportações novas não substituem contratos legados no primeiro PR.

## Prompt de abertura para o Codex

O prompt definitivo será criado após aprovação. Deverá começar por:

1. ler documentação;
2. analisar `packages/types` e tooling;
3. apresentar plano e arquivos;
4. identificar incompatibilidades;
5. aguardar a própria tarefa autorizada, sem ampliar escopo;
6. implementar somente contratos, fixtures e testes.

## Decisão proposta

**ADR-027 — O primeiro PR de código será contract-first, sem persistência, IA, API ou alteração de comportamento.**

Status: proposta, aguardando aprovação.
