# Continuidade — Marco 003

## Status

Marco 003 aprovado integralmente em 6 de agosto de 2026, sem ressalvas.

Este documento encerra a fase de plano técnico de implementação do MVP Sócrates 2 anterior ao código e estabelece o ponto oficial para o próximo fork da conversa.

## Repositório e fluxo de trabalho do marco encerrado

- repositório documental: `PaulinhoRehfeld/profeplan_v5`;
- branch documental: `docs/profeplan-knowledge-factory`;
- Pull Request documental: `#1 — docs: iniciar ProfePlan Knowledge Factory`;
- repositório canônico da implementação aprovado: `PaulinhoRehfeld/profeplan`;
- código de produção alterado no Marco 003: não;
- migrations alteradas: não;
- banco alterado: não;
- dependências alteradas: não;
- embeddings criados: não;
- modelos escolhidos: não.

## Objetivo cumprido

O Marco 003 converteu os Marcos 001 e 002 em um plano técnico incremental, auditável e executável pelo Codex, preservando o princípio de documentação antes do código.

Foram cumpridos os seguintes objetivos:

1. análise da estrutura real dos repositórios;
2. identificação do local de integração da Knowledge Factory;
3. separação entre capacidades existentes, reutilizáveis, adaptáveis e novas;
4. conversão das ondas aprovadas em arquitetura técnica incremental;
5. mapeamento das User Stories para módulos, serviços, schemas, APIs, jobs, agentes, validadores e testes;
6. definição dos contratos técnicos de fontes, segmentos, componentes, currículo, OPP, recuperação, validação e entrega;
7. proposta do modelo lógico de dados sem migrations;
8. definição de segurança, RLS, auditoria, permissões e minimização;
9. arquitetura da busca híbrida e plano experimental;
10. estratégia de tokens, custos, latência e observabilidade;
11. estratégia de fixtures, casos dourados, baseline genérico e testes de falha;
12. organização dos Lotes 0–12 para o Codex;
13. definição do menor e mais seguro primeiro PR de código;
14. avaliação de prontidão das Stories;
15. registro de riscos, trade-offs e decisões pendentes.

## Descoberta estrutural decisiva

A inspeção encontrou dois repositórios com funções distintas:

### `PaulinhoRehfeld/profeplan_v5`

Contém a documentação da ProfePlan Knowledge Factory produzida nos Marcos 001–003. Não contém o monorepo executável necessário para a integração técnica.

### `PaulinhoRehfeld/profeplan`

Contém o monorepo executável com aplicações, pacotes, agentes, IA, banco, currículo, PNLD, Gráfica e migrations.

### Decisão aprovada

`PaulinhoRehfeld/profeplan` será o repositório canônico da implementação.

A documentação dos Marcos 001–003 deverá ser sincronizada nele de forma controlada durante o Lote 0. Essa sincronização não deverá apagar, reinterpretar ou resumir silenciosamente as decisões aprovadas.

## ADRs aprovadas no Marco 003

### ADR-015 — Repositório canônico

`PaulinhoRehfeld/profeplan` é o repositório canônico da implementação.

### ADR-016 — Reutilização modular

A Knowledge Factory será integrada aos módulos responsáveis do monorepo, evitando um pacote monolítico sem justificativa.

### ADR-017 — Ondas verticais

A implementação seguirá ondas cumulativas, cada uma com capacidade testável e gate de saída.

### ADR-018 — Síncrono e assíncrono

Ingestão, segmentação, embeddings e avaliações em lote serão assíncronos. O fluxo principal da OPP será predominantemente síncrono no MVP.

### ADR-019 — Contract-first

Contratos compartilhados e testes precedem banco, APIs, modelos e agentes.

### ADR-020 — Recuperação híbrida filtrada

Filtros determinísticos serão aplicados antes da busca lexical e semântica. A insuficiência de base será um estado explícito.

### ADR-021 — Retrieval orientado por experimentos

Modelo de embedding, dimensão, índice, fusão, reranking, orçamento e cache serão escolhidos por evidência experimental.

### ADR-022 — Corpus compartilhado protegido

O corpus global não terá leitura pública direta. O acesso ocorrerá por serviços autorizados e políticas de escopo, licença e status.

### ADR-023 — Quality gates calibrados

Validadores existentes só serão obrigatórios após calibração contra casos dourados. Falhas Must não serão compensadas por outros resultados.

### ADR-024 — ModelPolicy e observabilidade

Agentes não acessarão diretamente SDKs de provedores. Modelos, limites, retry e fallback serão controlados por política versionada. Tokens, custos e latência serão medidos por etapa da OPP.

### ADR-025 — Baseline e piloto controlado

A comparação usará casos dourados, execução pareada e baseline genérico justo. Evidência insuficiente produzirá resultado inconclusivo.

### ADR-026 — Sócrates 2 como perfil

Sócrates 2 será um perfil versionado sobre o runtime comum, não uma duplicação de agente por Estado ou ano.

### ADR-027 — Primeiro PR contract-first

O primeiro PR de código conterá somente contratos, enums, fixtures sintéticas e testes de invariantes.

## Arquitetura incremental aprovada

### Onda 0 — Decisão, sincronização e contratos

Confirmar o monorepo, sincronizar documentação, validar baseline e preparar contratos.

### Onda 1 — Fontes

Registrar procedência, versão, checksum, licença e autorização de uso.

### Onda 2 — Segmentos e componentes

Preservar estrutura da fonte, destilar conteúdo autoral, revisar, versionar e deduplicar componentes.

### Onda 3 — Currículo e filtros

Disponibilizar o pacote curricular MG do piloto e aplicar filtros obrigatórios antes da recuperação.

### Onda 4 — Retrieval experimental

Implementar e comparar busca lexical, semântica, fusão, suficiência e alternativas de reranking.

### Onda 5 — OPP e Sócrates 2

Criar OPP, rotear o pedido e executar o perfil Sócrates 2 sobre o runtime comum.

### Onda 6 — Gates e entrega

Executar validações obrigatórias e produzir contrato estruturado de entrega.

### Onda 7 — Avaliação e piloto

Executar casos dourados, comparar com baseline e registrar decisão formal de avanço, ajuste ou interrupção.

## Lotes Codex aprovados

Foram aprovados os Lotes 0–12 descritos em:

`12-delivery/CODEX-IMPLEMENTATION-BATCHES.md`

A execução deverá respeitar:

- dependências entre lotes;
- limites de escopo;
- gates de entrada e saída;
- condições de interrupção;
- Definition of Ready;
- Definition of Done;
- bloqueios jurídicos, pedagógicos, curriculares, autorais, inclusivos e de segurança.

Nenhum lote autoriza execução ampla ou paralela fora da cadeia aprovada.

## Primeiro PR de código

O primeiro PR de código será preparado somente após a conclusão e aprovação do Lote 0.

### Conteúdo permitido

- contratos de domínio;
- enums controlados;
- schemas executáveis;
- fixtures sintéticas;
- testes de schema;
- testes de invariantes;
- documentação técnica diretamente relacionada.

### Conteúdo proibido

- tabelas físicas;
- migrations;
- RLS real;
- APIs;
- jobs;
- agentes executáveis;
- prompts;
- acesso a modelos;
- embeddings;
- escolha de dimensão vetorial;
- frontend;
- fontes reais;
- PNLD real;
- Rio Grande do Sul;
- novos agentes;
- novas disciplinas;
- Gráfica avançada;
- PDF sofisticado;
- PPTX sofisticado.

## Stories com Ready de domínio

As seguintes Stories possuem maturidade de domínio para o primeiro ciclo de contratos:

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

Elas ainda não estão automaticamente `Ready for Code`.

O status `Ready for Code` exige conclusão do Lote 0, confirmação dos comandos reais do monorepo, definição da branch do primeiro PR e autorização humana específica.

## Stories bloqueadas

Permanecem bloqueadas enquanto dependências específicas não forem resolvidas:

- ingestão por falta da fonte piloto autorizada;
- currículo por falta da versão oficial do recorte MG;
- persistência por falta do schema físico e da revisão RLS;
- retrieval por falta do dataset e dos experimentos;
- gates por falta da calibração dos validadores;
- piloto por falta do grupo docente e da rubrica final.

## Bloqueio permanente do MVP

EPIC-018 e US-018.1 permanecem `Won't no MVP`.

Não implementar nesta fase:

- Rio Grande do Sul;
- novos agentes;
- novas disciplinas;
- ingestão nacional em escala;
- Gráfica avançada;
- PDF sofisticado;
- PPTX sofisticado.

## Decisões rejeitadas ou não adotadas

Não foram aprovadas as seguintes abordagens:

- escolher embedding por preferência ou pela existência do vetor legado de 768 dimensões;
- escolher índice vetorial antes de medir o corpus do piloto;
- expor o corpus global por política de leitura pública;
- criar migrations no primeiro PR;
- duplicar Sócrates 2 por Estado;
- construir um pacote monolítico novo sem analisar os módulos existentes;
- autorizar código antes do Lote 0;
- tratar score médio como compensação para falha crítica;
- expandir o escopo pelo EPIC-018.

## Questões pendentes para os próximos lotes

### Lote 0

- branch base do primeiro PR no repositório canônico;
- nome da branch de implementação;
- método de sincronização da documentação;
- comandos reais de install, build, lint, typecheck e test;
- estado atual do CI;
- módulos exatos que receberão os contratos;
- conflitos entre código atual e documentação aprovada.

### Fontes e currículo

- conjunto exato de fontes do piloto;
- autorização jurídica de cada fonte;
- recorte curricular MG vigente;
- responsáveis por curadoria, currículo e jurídico.

### Retrieval

- modelo de embedding;
- dimensão;
- índice;
- pesos da busca híbrida;
- método de fusão;
- necessidade de reranker;
- limiares de relevância e suficiência;
- cache.

### Operação

- schemas físicos;
- divisão entre Prisma e SQL Supabase;
- jobs assíncronos;
- retenção;
- limites econômicos;
- SLAs.

### Piloto

- professores participantes;
- tamanho da amostra;
- avaliadores;
- rubrica final;
- critérios quantitativos de avanço.

## Riscos prioritários transferidos ao Marco 004

1. divergência entre `profeplan_v5` e `profeplan` durante a sincronização;
2. baseline do monorepo já estar quebrado antes da Knowledge Factory;
3. módulos existentes terem nomes promissores, mas maturidade insuficiente;
4. contratos novos colidirem com tipos legados;
5. migrations existentes de RAG induzirem decisões prematuras;
6. RLS legado permitir acesso mais amplo que o contrato aprovado;
7. o Codex extrapolar o Lote 0 ou antecipar código;
8. documentação ser copiada sem preservar histórico e links;
9. EPIC-018 entrar por dependência indireta;
10. aprovação do Marco 003 ser confundida com autorização geral de implementação.

## Documentos criados ou atualizados no Marco 003

### Governança

- `00-governance/DECISION-LOG.md`;
- `00-governance/CONTINUITY-CHECKPOINT-003.md`;
- `README.md`.

### Arquitetura

- `02-architecture/REPOSITORY-INTEGRATION-ASSESSMENT.md`;
- `02-architecture/TECHNICAL-CAPABILITY-MAP.md`;
- `02-architecture/INCREMENTAL-IMPLEMENTATION-ARCHITECTURE.md`;
- `02-architecture/TOKEN-COST-LATENCY-OBSERVABILITY.md`.

### Agentes

- `03-agents/profiles/socrates-2/TECHNICAL-PROFILE.md`.

### Conhecimento e currículo

- `04-knowledge/TECHNICAL-DOMAIN-CONTRACTS.md`;
- `05-curriculum/CURRICULUM-PACKAGE-TECHNICAL-CONTRACT.md`.

### Recuperação

- `06-retrieval/HYBRID-RETRIEVAL-ARCHITECTURE.md`;
- `06-retrieval/RETRIEVAL-EXPERIMENT-PLAN.md`.

### Produção, qualidade, dados e segurança

- `07-production/OPP-AND-DELIVERY-TECHNICAL-CONTRACT.md`;
- `08-quality/VALIDATION-TECHNICAL-CONTRACTS.md`;
- `09-data/LOGICAL-DATA-MODEL.md`;
- `10-legal-security/SECURITY-RLS-AUDIT-MODEL.md`.

### Testes e entrega

- `11-testing/TECHNICAL-TEST-AND-BASELINE-PLAN.md`;
- `12-delivery/STORY-TO-TECHNICAL-MAP.md`;
- `12-delivery/CODEX-IMPLEMENTATION-BATCHES.md`;
- `12-delivery/FIRST-CODE-PR.md`;
- `12-delivery/STORY-READINESS-ASSESSMENT.md`;
- `12-delivery/TECHNICAL-RISK-REGISTER.md`;
- `12-delivery/MARCO-003-APPROVAL-PACKAGE.md`.

## Termos oficiais preservados

- ProfePlan Knowledge Factory;
- Sócrates 2;
- componente pedagógico semielaborado;
- almoxarifado inteligente;
- pacote curricular;
- Ordem de Produção Pedagógica — OPP;
- retrieval híbrido;
- filtros antes da similaridade;
- quality gates não compensatórios;
- ModelPolicy;
- contrato de entrega;
- Gráfica ProfePlan;
- caso dourado;
- baseline genérico;
- Ready de domínio;
- Ready for Code;
- Lote 0;
- contract-first.

## Escopo do Marco 004

O Marco 004 deverá executar exclusivamente o Lote 0 antes de qualquer implementação significativa.

### Objetivos

1. acessar `PaulinhoRehfeld/profeplan`;
2. inspecionar branch, CI e baseline atuais;
3. identificar comandos reais do monorepo;
4. executar ou auditar install, build, typecheck, lint e testes;
5. registrar falhas preexistentes separadamente;
6. sincronizar a documentação aprovada dos Marcos 001–003;
7. confirmar os módulos de destino dos contratos;
8. produzir um relatório de diferenças entre plano e código;
9. preparar uma tarefa Codex restrita para o primeiro PR contract-first;
10. solicitar autorização humana específica antes de escrever código.

### Restrições

- não escrever código de produto;
- não criar migrations;
- não alterar banco;
- não escolher embedding;
- não criar vetor;
- não ingerir fonte real;
- não ativar agente;
- não implementar EPIC-018;
- não alterar Gráfica, PDF ou PPTX sofisticados.

## Critério para autorização do primeiro PR

O primeiro PR de código somente poderá ser autorizado quando o Marco 004 comprovar:

- documentação sincronizada;
- baseline técnico conhecido;
- branch definida;
- módulos de destino confirmados;
- contratos sem conflito arquitetônico conhecido;
- comandos de validação documentados;
- escopo do PR limitado ao Lote 1;
- critérios de aceite e rollback definidos.

## Próximo fork

**Este é o ponto oficial para realizar o próximo fork da conversa.**

O novo chat deverá iniciar o Marco 004 e trabalhar no repositório canônico `PaulinhoRehfeld/profeplan`, sem escrever código antes de concluir o Lote 0 e receber autorização específica.

## Mensagem pronta para iniciar o Marco 004

> Estamos continuando a ProfePlan Knowledge Factory. Os Marcos 001, 002 e 003 foram aprovados integralmente. Leia primeiro `docs/profeplan-knowledge-factory/00-governance/CONTINUITY-CHECKPOINT-003.md` no repositório `PaulinhoRehfeld/profeplan_v5`, branch `docs/profeplan-knowledge-factory`, Pull Request nº 1. Leia também o `README.md`, o `DECISION-LOG.md`, `12-delivery/CODEX-IMPLEMENTATION-BATCHES.md`, `12-delivery/FIRST-CODE-PR.md`, `12-delivery/STORY-READINESS-ASSESSMENT.md` e `12-delivery/TECHNICAL-RISK-REGISTER.md`. O repositório canônico de implementação aprovado é `PaulinhoRehfeld/profeplan`. Inicie o Marco 004 executando somente o Lote 0: inspecione o monorepo real, confirme branch e baseline, audite install/build/typecheck/lint/test, identifique falhas preexistentes, sincronize de forma controlada a documentação aprovada e confirme os módulos de destino. Não escreva código, não crie migrations, não escolha embedding, não use fonte real e não implemente o EPIC-018. Ao final do Lote 0, prepare a autorização específica do primeiro PR contract-first para revisão humana.

## Critério para o próximo checkpoint

O próximo checkpoint deverá ser criado após a conclusão e aprovação do Lote 0, antes da autorização ou execução do primeiro PR de código.
