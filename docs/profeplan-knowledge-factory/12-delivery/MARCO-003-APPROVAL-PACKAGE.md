# Pacote de Aprovação — Marco 003

## Status

Aguardando aprovação humana. Nenhum código foi autorizado.

## Objetivo do marco

Transformar o backlog aprovado em plano técnico executável, sem escolher por preferência tecnologias que dependem de evidência e sem ampliar o escopo do Sócrates 2.

## Descoberta crítica

Foram encontrados dois repositórios com papéis diferentes:

- `PaulinhoRehfeld/profeplan_v5`: documentação dos Marcos 001–003, sem monorepo executável;
- `PaulinhoRehfeld/profeplan`: monorepo com `apps`, `packages`, agentes, IA, banco, currículo, PNLD, Gráfica e migrations.

Recomendação: confirmar `PaulinhoRehfeld/profeplan` como repositório canônico de implementação e sincronizar nele a documentação aprovada antes do primeiro PR de código.

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

## Resumo das decisões propostas

### ADR-015

Confirmar o repositório canônico antes do código. Recomendação: `PaulinhoRehfeld/profeplan`.

### ADR-016

Reutilizar módulos do monorepo por responsabilidade, sem pacote monolítico novo.

### ADR-017

Implementar em ondas verticais e cumulativas.

### ADR-018

Ingestão/preparação assíncronas; solicitação/entrega predominantemente síncronas.

### ADR-019

Contract-first.

### ADR-020

Filtros determinísticos antes da busca lexical e semântica; suficiência explícita.

### ADR-021

Embedding, dimensão, índice, fusão, reranker, orçamento e cache dependem de experimentos.

### ADR-022

Corpus compartilhado acessado por serviços autorizados, não por leitura pública direta.

### ADR-023

Quality gates não compensatórios; validadores atuais precisam de calibração.

### ADR-024

ModelPolicy e observabilidade por etapa da OPP.

### ADR-025

Baseline justo e piloto controlado; evidência insuficiente é inconclusiva.

### ADR-026

Sócrates 2 como perfil do runtime comum.

### ADR-027

Primeiro PR de código somente com contratos, fixtures e testes.

## Arquitetura incremental

1. Onda 0 — decisões e contratos;
2. Onda 1 — fontes;
3. Onda 2 — segmentos/componentes;
4. Onda 3 — currículo/filtros;
5. Onda 4 — retrieval experimental;
6. Onda 5 — OPP/Sócrates 2;
7. Onda 6 — gates/entrega;
8. Onda 7 — avaliação/piloto.

## Lotes Codex

Foram definidos Lotes 0–12, com dependências, Stories, limites e condições de interrupção.

O Lote 0 sincroniza documentação e confirma baseline. O primeiro PR de código é o Lote 1 contract-first.

## Primeiro PR de código proposto

Conteúdo:

- contratos de domínio;
- enums;
- fixtures sintéticas;
- testes de schema e invariantes.

Exclusões:

- banco;
- migration;
- IA;
- embedding;
- API;
- agente;
- frontend;
- fonte real;
- RS;
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

Elas ainda não estão `Ready for Code` por causa dos gates globais.

### Bloqueios principais

- repositório canônico;
- fonte autorizada do piloto;
- versão curricular MG;
- schema físico/RLS;
- dataset de retrieval;
- experimentos;
- validadores calibrados;
- grupo piloto.

### Won't

US-018.1 e todo o EPIC-018 permanecem bloqueados.

## Pontos que a aprovação do Marco 003 deve confirmar

1. `PaulinhoRehfeld/profeplan` será o repositório canônico de código;
2. a documentação aprovada será sincronizada nesse repositório antes da implementação;
3. a arquitetura será modular, reutilizando o monorepo;
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

## Aprovação possível

### Aprovação integral

Aprova ADR-015 a ADR-027 e autoriza preparar o checkpoint e o prompt do Lote 0. Não autoriza automaticamente o primeiro PR de código; o Lote 0 deverá confirmar baseline e documentação no repositório canônico.

### Aprovação com ressalvas

As ressalvas deverão identificar ADR/documento e alteração necessária.

### Reprovação parcial

Decisões não aprovadas permanecem bloqueantes quando afetarem segurança, contrato ou repositório.

## O que acontecerá após aprovação

1. atualizar ADR-015 a ADR-027 para aprovadas;
2. criar `00-governance/CONTINUITY-CHECKPOINT-003.md`;
3. registrar fechamento no PR nº 1;
4. avisar explicitamente o próximo fork;
5. no Marco 004, executar o Lote 0 documental no repositório canônico;
6. somente depois preparar a autorização específica do primeiro PR de código.

## O que não acontecerá automaticamente

- merge do PR nº 1;
- escrita de código;
- migration;
- uso de fonte PNLD;
- criação de embeddings;
- ativação de Sócrates 2;
- envio de tarefa ampla ao Codex.
