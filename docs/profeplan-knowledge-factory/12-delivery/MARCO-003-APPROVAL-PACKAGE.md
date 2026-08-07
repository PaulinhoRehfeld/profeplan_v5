# Pacote de Aprovação — Marco 003

## Status

Aprovado integralmente em 6 de agosto de 2026, sem ressalvas.

A aprovação confirma as ADRs 015 a 027 e autoriza a criação do checkpoint de continuidade e a preparação do Lote 0. Não autoriza automaticamente escrita de código.

## Objetivo do marco

Transformar o backlog aprovado em plano técnico executável, sem escolher por preferência tecnologias que dependem de evidência e sem ampliar o escopo do Sócrates 2.

## Descoberta crítica

Foram encontrados dois repositórios com papéis diferentes:

- `PaulinhoRehfeld/profeplan_v5`: documentação dos Marcos 001–003, sem monorepo executável;
- `PaulinhoRehfeld/profeplan`: monorepo com `apps`, `packages`, agentes, IA, banco, currículo, PNLD, Gráfica e migrations.

Decisão aprovada: `PaulinhoRehfeld/profeplan` é o repositório canônico de implementação. A documentação aprovada deverá ser sincronizada nele de forma controlada durante o Lote 0, antes do primeiro PR de código.

## Documentos técnicos criados

### Arquitetura

- `02-architecture/REPOSITORY-INTEGRATION-ASSESSMENT.md`
- `02-architecture/TECHNICAL-CAPABILITY-MAP.md`
- `02-architecture/INCREMENTAL-IMPLEMENTATION-ARCHITECTURE.md`
- `02-architecture/TOKEN-COST-LATENCY-OBSERVABILITY.md`

### Agente

- `03-agents/profiles/socrates-2/TECHNICAL-PROFILE.md`

### Conhecimento e currículo

- `04-knowledge/TECHNICAL-DOMAIN-CONTRACTS.md`
- `05-curriculum/CURRICULUM-PACKAGE-TECHNICAL-CONTRACT.md`

### Recuperação

- `06-retrieval/HYBRID-RETRIEVAL-ARCHITECTURE.md`
- `06-retrieval/RETRIEVAL-EXPERIMENT-PLAN.md`

### Produção, qualidade, dados e segurança

- `07-production/OPP-AND-DELIVERY-TECHNICAL-CONTRACT.md`
- `08-quality/VALIDATION-TECHNICAL-CONTRACTS.md`
- `09-data/LOGICAL-DATA-MODEL.md`
- `10-legal-security/SECURITY-RLS-AUDIT-MODEL.md`

### Testes e entrega

- `11-testing/TECHNICAL-TEST-AND-BASELINE-PLAN.md`
- `12-delivery/STORY-TO-TECHNICAL-MAP.md`
- `12-delivery/CODEX-IMPLEMENTATION-BATCHES.md`
- `12-delivery/FIRST-CODE-PR.md`
- `12-delivery/STORY-READINESS-ASSESSMENT.md`
- `12-delivery/TECHNICAL-RISK-REGISTER.md`

## Decisões aprovadas

### ADR-015

`PaulinhoRehfeld/profeplan` é o repositório canônico da implementação.

### ADR-016

Reutilizar módulos do monorepo por responsabilidade, sem pacote monolítico novo.

### ADR-017

Implementar em ondas verticais e cumulativas.

### ADR-018

Ingestão e preparação assíncronas; solicitação e entrega predominantemente síncronas no MVP.

### ADR-019

Adotar contract-first.

### ADR-020

Aplicar filtros determinísticos antes da busca lexical e semântica, com suficiência explícita.

### ADR-021

Embedding, dimensão, índice, fusão, reranker, orçamento e cache dependem de experimentos reproduzíveis.

### ADR-022

Corpus compartilhado acessado por serviços autorizados, sem leitura pública direta.

### ADR-023

Quality gates não compensatórios; validadores atuais precisam de calibração.

### ADR-024

ModelPolicy e observabilidade por etapa da OPP.

### ADR-025

Baseline justo e piloto controlado; evidência insuficiente é inconclusiva.

### ADR-026

Sócrates 2 como perfil versionado do runtime comum.

### ADR-027

Primeiro PR de código somente com contratos, fixtures e testes.

## Arquitetura incremental aprovada

1. Onda 0 — decisões, sincronização e contratos;
2. Onda 1 — fontes;
3. Onda 2 — segmentos e componentes;
4. Onda 3 — currículo e filtros;
5. Onda 4 — retrieval experimental;
6. Onda 5 — OPP e Sócrates 2;
7. Onda 6 — gates e entrega;
8. Onda 7 — avaliação e piloto.

## Lotes Codex

Foram aprovados os Lotes 0–12, com dependências, Stories, limites e condições de interrupção.

O Lote 0 sincroniza a documentação, confirma o baseline do monorepo e prepara a autorização específica do primeiro PR de código. O primeiro PR de código continua sendo o Lote 1 contract-first.

## Primeiro PR de código aprovado em princípio

Conteúdo permitido após autorização específica:

- contratos de domínio;
- enums;
- fixtures sintéticas;
- testes de schema e invariantes.

Exclusões obrigatórias:

- banco;
- migration;
- IA;
- embedding;
- API;
- agente;
- frontend;
- fonte real;
- Rio Grande do Sul;
- Gráfica avançada.

## Prontidão

### Ready de domínio

- US-001.1;
- US-001.2;
- US-002.1;
- US-002.2;
- US-004.1;
- US-004.2;
- US-010.1;
- US-014.1;
- US-015.1;
- US-016.1.

Essas Stories ainda não estão `Ready for Code`. O Lote 0 deverá confirmar branch, baseline, sincronização documental e comandos reais de validação do monorepo.

### Bloqueios restantes

- conclusão do Lote 0;
- fonte autorizada do piloto;
- versão curricular MG;
- schema físico e RLS;
- dataset de retrieval;
- experimentos;
- validadores calibrados;
- grupo piloto.

### Won't

US-018.1 e todo o EPIC-018 permanecem bloqueados.

## Confirmações formais da aprovação

1. `PaulinhoRehfeld/profeplan` é o repositório canônico de código;
2. a documentação aprovada será sincronizada nesse repositório antes da implementação;
3. a arquitetura será modular e reutilizará o monorepo;
4. as ondas e lotes Codex estão aprovados;
5. contratos precedem banco, API e IA;
6. filtros precedem similaridade;
7. escolhas de retrieval dependem de experimentos;
8. corpus global não terá leitura pública direta;
9. Sócrates 2 será perfil do runtime comum;
10. primeiro PR de código será contract-first;
11. nenhuma migration será criada no primeiro PR;
12. nenhum modelo de embedding será escolhido no primeiro PR;
13. EPIC-018 continuará bloqueado.

## Efeitos da aprovação

A aprovação autoriza:

1. atualizar ADR-015 a ADR-027 para aprovadas;
2. criar `00-governance/CONTINUITY-CHECKPOINT-003.md`;
3. registrar o fechamento do Marco 003 no PR nº 1;
4. realizar o próximo fork;
5. iniciar o Marco 004 pelo Lote 0 documental e de descoberta técnica.

## O que continua não autorizado

- merge automático do PR nº 1;
- escrita de código;
- migration;
- uso de fonte PNLD sem autorização;
- criação de embeddings;
- ativação de Sócrates 2;
- implementação de RS, novos agentes, novas disciplinas, Gráfica avançada, PDF ou PPTX sofisticados;
- envio de tarefa ampla e sem lote ao Codex.
