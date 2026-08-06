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

## Questões ainda não decididas

- modelo de embeddings;
- dimensão dos vetores;
- estratégia de reranqueamento;
- limite inicial exato de tokens por agente;
- política jurídica para cada categoria de obra PNLD;
- uso de uma ou várias tabelas físicas de embeddings;
- mecanismo de cache;
- formato de integração futura com a Gráfica.
