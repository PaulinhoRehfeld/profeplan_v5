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

**Consequência:** o Marco 001 foi encerrado antes da decomposição do MVP em Features e Stories. O Marco 002 foi encerrado após aprovação integral do backlog e dos critérios de implementação.

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

## Questões ainda não decididas

- modelo de embeddings;
- dimensão dos vetores;
- estratégia de reranqueamento;
- limite inicial exato de tokens por agente;
- política jurídica para cada categoria de obra PNLD;
- uso de uma ou várias tabelas físicas de embeddings;
- mecanismo de cache;
- formato de integração futura com a Gráfica;
- conjunto exato de fontes do piloto;
- versão oficial do recorte curricular MG usada no teste;
- professores que participarão da avaliação;
- limiares quantitativos finais de relevância e similaridade.

Essas questões passam ao Marco 003 e deverão ser decididas por evidência, contratos e requisitos das Stories aprovadas, não por preferência técnica isolada.
