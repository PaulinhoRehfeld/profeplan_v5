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

### Arquitetura

- [Visão geral da arquitetura](02-architecture/ARCHITECTURE-OVERVIEW.md)
- [Perfil do agente Sócrates 2](03-agents/profiles/socrates-2/README.md)
- [Modelo de conhecimento](04-knowledge/KNOWLEDGE-MODEL.md)
- [Padrão de pacotes curriculares](05-curriculum/CURRICULUM-PACKAGE-STANDARD.md)
- [Pipeline de recuperação](06-retrieval/RETRIEVAL-PIPELINE.md)
- [Ordem de Produção Pedagógica](07-production/PEDAGOGICAL-PRODUCTION-ORDER.md)

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

### Testes e avaliação

- [Matriz de aceite do MVP](11-testing/MVP-ACCEPTANCE-MATRIX.md)
- [Casos de falha e critérios de exclusão](11-testing/FAILURE-AND-EXCLUSION-CASES.md)

## Política de continuidade

O assistente deverá avisar quando um fork de conversa for recomendado. O Marco 001 já foi encerrado. O próximo fork somente ocorrerá após a aprovação humana do pacote documental do Marco 002:

- seleção de Epics do MVP;
- Features;
- User Stories;
- critérios de aceite;
- dependências;
- prioridades MoSCoW;
- Definition of Ready;
- Definition of Done;
- casos de falha e exclusão.

Antes do próximo fork deverá ser criado `00-governance/CONTINUITY-CHECKPOINT-002.md`.

## Estado do projeto

Fase atual: documentação do backlog e critérios de implementação do MVP.

Nenhum código foi autorizado nesta fase. A implementação somente poderá começar após aprovação do Marco 002 e preparação do pacote técnico para o Codex.
