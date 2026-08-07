# Decision Log

## Convenção

- Status: proposto, aprovado, substituído ou rejeitado.
- Toda decisão técnica relevante deve registrar contexto, decisão, consequências e riscos.

## ADR-001 — Escopo educacional

**Status:** aprovado

O ProfePlan atenderá apenas Ensino Fundamental II e Ensino Médio nesta fase.

**Consequência:** todos os modelos, filtros e testes devem excluir Educação Infantil, Fundamental I e Ensino Superior.

## ADR-002 — Especialização dos agentes

**Status:** aprovado

Os perfis de agentes serão especializados por componente curricular, etapa e ano.

**Consequência:** Filosofia do 2º ano será atendida pelo perfil Sócrates 2.

## ADR-003 — Currículos estaduais plugáveis

**Status:** aprovado

Currículos estaduais serão pacotes versionados carregados conforme o contexto do professor.

## ADR-004 — Mesmo agente para MG e RS

**Status:** aprovado

O mesmo agente poderá operar com Minas Gerais ou Rio Grande do Sul. Não haverá duplicação por Estado.

**Risco controlado:** impedir carregamento simultâneo de currículos, salvo em modo comparativo explícito.

## ADR-005 — Componentes pedagógicos semielaborados

**Status:** aprovado

As fontes serão transformadas em componentes estruturados. O almoxarifado não armazenará apenas páginas brutas nem apenas produtos finalizados.

## ADR-006 — Filtros antes da busca vetorial

**Status:** aprovado

A recuperação aplicará filtros por componente, etapa, ano, currículo, finalidade, licença e status de validação antes da similaridade semântica.

## ADR-007 — Piloto Sócrates 2

**Status:** aprovado

O primeiro experimento será Filosofia do 2º ano do Ensino Médio, inicialmente com currículo de Minas Gerais.

## ADR-008 — Produção separada da Gráfica

**Status:** aprovado

Agentes pedagógicos produzem e validam o conteúdo. A Gráfica realiza acabamento editorial e exportação.

## ADR-009 — Documentação antes do código

**Status:** aprovado

Nenhuma implementação será iniciada antes da aprovação dos documentos essenciais.

## ADR-010 — Infraestrutura comum, perfis especializados

**Status:** aprovado

Sócrates 2 e os demais especialistas serão configurações sobre uma infraestrutura comum, evitando duplicação de código, prompts e bancos.

## ADR-011 — Continuidade por marcos e forks controlados

**Status:** aprovado

A continuidade do projeto entre conversas será feita por marcos documentais, e não por uma contagem rígida de mensagens. O assistente deverá avisar quando o fork for necessário e registrar previamente um documento de continuidade no GitHub.

**Consequência:** o Marco 001 foi encerrado antes da decomposição do MVP em Features e Stories. O Marco 002 foi encerrado após aprovação integral do backlog e dos critérios de implementação. O Marco 003 foi encerrado após aprovação integral do plano técnico anterior ao código.

**Risco controlado:** evitar perda de decisões, duplicação de discussões e divergência entre conversas paralelas.

## ADR-012 — Epics selecionados para o MVP

**Status:** aprovado no Marco 002

Os EPIC-001 a EPIC-017 participam do MVP em escopo reduzido e explícito. O EPIC-018 permanece fora do MVP.

**Contexto:** o piloto precisa validar o fluxo completo de fontes, componentes, currículo, recuperação, agente, geração, gates, entrega, métricas e avaliação.

**Consequência:** um Epic selecionado não autoriza suas capacidades de Fase 2 ou Fase 3. O detalhamento válido é o documento `12-delivery/MVP-EPIC-SELECTION.md`.

**Risco controlado:** impedir que “MVP completo” seja interpretado como ingestão industrial, Gráfica avançada, RS ou novos agentes.

## ADR-013 — Priorização MoSCoW e preservação dos gates

**Status:** aprovado no Marco 002

O backlog do MVP será classificado em Must, Should, Could e Won't. Em conflito de prazo ou custo, Should e Could serão adiadas antes de reduzir gates jurídicos, pedagógicos, curriculares, autorais, inclusivos ou de rastreabilidade.

**Consequência:** aparência visual, variedade e automações auxiliares não compensam falhas bloqueantes.

**Risco controlado:** evitar um MVP visualmente atraente, mas pedagogicamente ou juridicamente inseguro.

## ADR-014 — Aprovação baseada em evidências não compensatórias

**Status:** aprovado no Marco 002

O MVP não será aprovado por média simples entre dimensões. Fonte proibida, erro conceitual relevante, ausência de rastreabilidade, reprodução extensa, mistura curricular ou falha de privacidade são bloqueadores independentes.

**Consequência:** a matriz de aceite utilizará gates bloqueantes e estados aprovado, reprovado, inconclusivo e não aplicável.

**Risco controlado:** impedir que criatividade, velocidade ou baixo custo escondam falhas críticas.

## ADR-015 — Repositório canônico da implementação

**Status:** aprovado no Marco 003

`PaulinhoRehfeld/profeplan` é o repositório canônico da implementação da Knowledge Factory. A documentação aprovada nos Marcos 001–003 deverá ser sincronizada de forma controlada nesse monorepo durante o Lote 0, antes do primeiro PR de código.

**Contexto:** `profeplan_v5` contém a documentação dos marcos, enquanto `profeplan` contém apps, packages, agentes, IA, banco e migrations.

**Consequência:** nenhuma Story recebe `Ready for Code` antes da conclusão do Lote 0 e da confirmação do baseline técnico no repositório canônico.

**Risco controlado:** evitar implementação em repositório sem runtime e divergência entre documentação e código.

## ADR-016 — Reutilização modular do monorepo

**Status:** aprovado no Marco 003

A Knowledge Factory será distribuída pelos módulos responsáveis — types, industry-pnld, industry-curriculum, db, ai, agents, bff, web e observabilidade — evitando um novo pacote monolítico sem necessidade.

## ADR-017 — Implementação em ondas verticais

**Status:** aprovado no Marco 003

A implementação seguirá ondas cumulativas, com capacidade testável e gate de saída em cada uma.

## ADR-018 — Fronteiras síncronas e assíncronas

**Status:** aprovado no Marco 003

Ingestão, segmentação, embeddings e avaliações em lote serão assíncronos; criação da OPP, retrieval em estoque publicado, geração, gates e entrega serão predominantemente síncronos no MVP.

## ADR-019 — Contract-first

**Status:** aprovado no Marco 003

Contratos compartilhados e testes precederão persistência, APIs, modelos e agentes.

## ADR-020 — Recuperação híbrida filtrada

**Status:** aprovado no Marco 003

Filtros determinísticos serão aplicados antes das buscas lexical e semântica. A fusão será auditável e o pipeline terá estado explícito de insuficiência.

## ADR-021 — Escolhas de retrieval orientadas por experimentos

**Status:** aprovado no Marco 003

Embedding, dimensão, índice, fusão, reranker, orçamento e cache serão escolhidos por experimento reproduzível, não por preferência ou legado.

## ADR-022 — Corpus compartilhado sem leitura pública direta

**Status:** aprovado no Marco 003

Conhecimento global será acessado por serviços autorizados. Licença, status, perfil do agente e escopo participam da autorização.

## ADR-023 — Quality gates calibrados e não compensatórios

**Status:** aprovado no Marco 003

Validadores existentes só entram no pipeline obrigatório após avaliação contra casos dourados. Erro de gate Must bloqueia aprovação.

## ADR-024 — ModelPolicy e observabilidade por OPP

**Status:** aprovado no Marco 003

Agentes não acessam SDKs de provedor diretamente. Modelos, limites, retry e fallback são resolvidos por política versionada; tokens, custo e latência são medidos por etapa da OPP.

## ADR-025 — Baseline justo e piloto controlado

**Status:** aprovado no Marco 003

A avaliação usa casos dourados, execução pareada e baseline genérico justo. Evidência insuficiente resulta em piloto inconclusivo.

## ADR-026 — Sócrates 2 como perfil do runtime comum

**Status:** aprovado no Marco 003

Sócrates 2 será um perfil versionado com escopo, produtos, ferramentas e bloqueios, não um agente duplicado por Estado ou ano.

## ADR-027 — Primeiro PR de código contract-first

**Status:** aprovado no Marco 003

O primeiro PR de código conterá somente contratos, enums, fixtures e testes, sem banco, migrations, IA, API ou mudança de comportamento.

## Questões ainda não decididas

### Gate anterior ao código

- branch base e nome da branch do primeiro PR no repositório canônico;
- mecanismo de sincronização e validação da documentação durante o Lote 0;
- resultado do build, typecheck, lint e testes do monorepo no baseline confirmado.

### Fontes e currículo

- conjunto exato de fontes autorizadas do piloto;
- política jurídica final para cada categoria de obra PNLD;
- versão oficial do recorte curricular MG;
- responsáveis humanos por curadoria, currículo, jurídico e avaliação.

### Experimentos

- modelo de embeddings;
- dimensão dos vetores;
- índice vetorial;
- estratégia de fusão;
- necessidade de reranqueamento;
- limiares de relevância e suficiência;
- orçamento exato de tokens;
- mecanismo de cache.

### Persistência e operação

- divisão física entre Prisma e SQL Supabase;
- nomes e schemas de tabelas;
- retenção exata;
- ferramenta de jobs assíncronos;
- SLAs e limites econômicos;
- formato futuro da integração com a Gráfica.

### Piloto

- professores participantes;
- tamanho final da amostra;
- rubrica e avaliadores;
- critérios quantitativos finais de avanço.

Essas questões permanecem deliberadamente abertas até evidência, decisão humana ou lote correspondente.
