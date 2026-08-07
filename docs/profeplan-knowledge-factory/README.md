# ProfePlan Knowledge Factory

## Propósito

O ProfePlan Knowledge Factory é o projeto arquitetural responsável por transformar fontes curriculares, pedagógicas e bibliográficas em componentes de conhecimento estruturados, rastreáveis e recuperáveis por agentes especializados.

O objetivo não é armazenar materiais finalizados para mera reprodução. O sistema deverá manter matérias-primas pedagógicas semielaboradas, previamente processadas, classificadas e, quando adequado, vetorizadas. Agentes especializados combinarão esses componentes para gerar produtos autorais, personalizados e alinhados ao contexto do professor.

## Escopo educacional

O ProfePlan atende exclusivamente:

- Ensino Fundamental II: 6º, 7º, 8º e 9º anos;
- Ensino Médio: 1º, 2º e 3º anos.

Currículos estaduais previstos nesta fase:

- Minas Gerais: currículo inicial;
- Rio Grande do Sul: próxima implantação, bloqueada até a validação do piloto.

O mesmo agente disciplinar poderá operar com diferentes pacotes curriculares estaduais. Não haverá duplicação de agentes por Estado.

## Metáfora operacional

- ProfePlan: loja e central de entrega;
- fontes originais: matérias-primas brutas;
- componentes pedagógicos: matérias-primas semielaboradas;
- repositório de componentes: almoxarifado inteligente;
- agentes especializados: fábricas;
- agente coordenador: central de produção;
- validadores: controle de qualidade;
- Gráfica ProfePlan: acabamento editorial;
- planejamentos, materiais e avaliações: produtos pedagógicos.

## Piloto

O primeiro piloto será:

- componente: Filosofia;
- etapa: Ensino Médio;
- ano: 2º ano;
- agente: Sócrates 2;
- currículo inicial: Minas Gerais;
- próximo pacote curricular: Rio Grande do Sul, fora do MVP.

## Princípio central

> Padronizar o processo de produção, sem padronizar excessivamente o produto final.

A recuperação deverá aplicar filtros pedagógicos, curriculares e jurídicos antes da busca vetorial. O agente não deverá consultar indiscriminadamente todo o acervo.

## Documentos principais

### Governança

- [Project Charter](00-governance/PROJECT-CHARTER.md)
- [Decision Log](00-governance/DECISION-LOG.md)
- [Política de continuidade e forks](00-governance/CONTINUITY-AND-FORK-POLICY.md)
- [Checkpoint do Marco 001](00-governance/CONTINUITY-CHECKPOINT-001.md)
- [Checkpoint do Marco 002](00-governance/CONTINUITY-CHECKPOINT-002.md)
- [Checkpoint do Marco 003](00-governance/CONTINUITY-CHECKPOINT-003.md)

### Arquitetura conceitual

- [Visão geral da arquitetura](02-architecture/ARCHITECTURE-OVERVIEW.md)
- [Perfil do agente Sócrates 2](03-agents/profiles/socrates-2/README.md)
- [Modelo de conhecimento](04-knowledge/KNOWLEDGE-MODEL.md)
- [Padrão de pacotes curriculares](05-curriculum/CURRICULUM-PACKAGE-STANDARD.md)
- [Pipeline de recuperação](06-retrieval/RETRIEVAL-PIPELINE.md)
- [Ordem de Produção Pedagógica](07-production/PEDAGOGICAL-PRODUCTION-ORDER.md)

### Marco 003 — arquitetura técnica aprovada

- [Avaliação dos repositórios](02-architecture/REPOSITORY-INTEGRATION-ASSESSMENT.md)
- [Mapa de capacidades técnicas](02-architecture/TECHNICAL-CAPABILITY-MAP.md)
- [Arquitetura incremental](02-architecture/INCREMENTAL-IMPLEMENTATION-ARCHITECTURE.md)
- [Tokens, custo, latência e observabilidade](02-architecture/TOKEN-COST-LATENCY-OBSERVABILITY.md)
- [Perfil técnico do Sócrates 2](03-agents/profiles/socrates-2/TECHNICAL-PROFILE.md)
- [Contratos técnicos do conhecimento](04-knowledge/TECHNICAL-DOMAIN-CONTRACTS.md)
- [Contrato técnico curricular](05-curriculum/CURRICULUM-PACKAGE-TECHNICAL-CONTRACT.md)
- [Arquitetura de retrieval híbrido](06-retrieval/HYBRID-RETRIEVAL-ARCHITECTURE.md)
- [Plano de experimentos de retrieval](06-retrieval/RETRIEVAL-EXPERIMENT-PLAN.md)
- [Contrato técnico da OPP e entrega](07-production/OPP-AND-DELIVERY-TECHNICAL-CONTRACT.md)
- [Contratos de validação](08-quality/VALIDATION-TECHNICAL-CONTRACTS.md)
- [Modelo lógico de dados](09-data/LOGICAL-DATA-MODEL.md)
- [Segurança, RLS, auditoria e minimização](10-legal-security/SECURITY-RLS-AUDIT-MODEL.md)
- [Plano técnico de testes e baseline](11-testing/TECHNICAL-TEST-AND-BASELINE-PLAN.md)

### Entrega e backlog

- [Mapa geral de Epics](12-delivery/EPICS.md)
- [Escopo do MVP Sócrates 2](12-delivery/MVP-SOCRATES-2.md)
- [Seleção formal de Epics do MVP](12-delivery/MVP-EPIC-SELECTION.md)
- [Features do MVP](12-delivery/MVP-FEATURES.md)
- [User Stories e critérios de aceite](12-delivery/MVP-USER-STORIES.md)
- [Priorização MoSCoW](12-delivery/MOSCOW-PRIORITIZATION.md)
- [Mapa de dependências](12-delivery/MVP-DEPENDENCY-MAP.md)
- [Definition of Ready](12-delivery/DEFINITION-OF-READY.md)
- [Definition of Done](12-delivery/DEFINITION-OF-DONE.md)
- [Mapa Stories → técnica](12-delivery/STORY-TO-TECHNICAL-MAP.md)
- [Lotes Codex](12-delivery/CODEX-IMPLEMENTATION-BATCHES.md)
- [Primeiro PR de código proposto](12-delivery/FIRST-CODE-PR.md)
- [Prontidão das Stories](12-delivery/STORY-READINESS-ASSESSMENT.md)
- [Registro de riscos](12-delivery/TECHNICAL-RISK-REGISTER.md)
- [Pacote de aprovação do Marco 003](12-delivery/MARCO-003-APPROVAL-PACKAGE.md)

### Testes e avaliação

- [Matriz de aceite do MVP](11-testing/MVP-ACCEPTANCE-MATRIX.md)
- [Casos de falha e critérios de exclusão](11-testing/FAILURE-AND-EXCLUSION-CASES.md)
- [Plano técnico de testes, fixtures e baseline](11-testing/TECHNICAL-TEST-AND-BASELINE-PLAN.md)

## Marcos aprovados

### Marco 001

Aprovou visão, arquitetura, agentes, currículos plugáveis, conhecimento semielaborado, escopo e MVP do Sócrates 2.

### Marco 002

Aprovou integralmente, sem alterações:

- EPIC-001 a EPIC-017 em escopo reduzido;
- EPIC-018 bloqueado;
- Features e User Stories do MVP;
- critérios de aceite;
- prioridades MoSCoW;
- dependências;
- Definition of Ready;
- Definition of Done;
- gates de aceite;
- casos de falha e exclusão;
- ADR-012, ADR-013 e ADR-014.

### Marco 003

Aprovado integralmente em 6 de agosto de 2026, sem ressalvas.

Aprovou:

- `PaulinhoRehfeld/profeplan` como repositório canônico da implementação;
- sincronização controlada da documentação durante o Lote 0;
- separação entre capacidades existentes, adaptáveis e novas;
- arquitetura incremental em ondas;
- contratos técnicos antes de banco, APIs e IA;
- modelo lógico de dados sem migrations;
- segurança, RLS, auditoria e minimização;
- retrieval híbrido com filtros antes da similaridade;
- experimentos obrigatórios para embedding, dimensão, índice, fusão, reranking, orçamento e cache;
- ModelPolicy, tokens, custo, latência e observabilidade por OPP;
- fixtures, casos dourados e baseline genérico;
- mapeamento técnico das Stories;
- Lotes 0–12 para o Codex;
- primeiro PR de código contract-first;
- ADR-015 a ADR-027.

A aprovação do Marco 003 não autorizou automaticamente escrita de código.

## Política de continuidade

O Marco 003 está encerrado e o checkpoint de continuidade foi criado.

**Este é o momento oficial do próximo fork.**

O Marco 004 deverá ser iniciado em uma nova conversa e executar primeiro o Lote 0:

1. trabalhar no repositório canônico `PaulinhoRehfeld/profeplan`;
2. confirmar branch base e baseline técnico real;
3. executar ou auditar build, typecheck, lint e testes existentes;
4. sincronizar a documentação aprovada dos Marcos 001–003;
5. validar os destinos dos módulos no monorepo;
6. preparar a autorização específica do primeiro PR contract-first;
7. não escrever código de produto antes dessa autorização.

## Estado do projeto

Fase atual: Marcos 001, 002 e 003 aprovados. Próximo passo: fork para o Marco 004 e execução do Lote 0.

Nenhum código, migration, banco, dependência, modelo, embedding ou integração de produção foi alterado durante o Marco 003.
