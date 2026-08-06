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
- Rio Grande do Sul: próxima implantação.

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
- próximo pacote curricular: Rio Grande do Sul.

## Princípio central

> Padronizar o processo de produção, sem padronizar excessivamente o produto final.

A recuperação deverá aplicar filtros pedagógicos, curriculares e jurídicos antes da busca vetorial. O agente não deverá consultar indiscriminadamente todo o acervo.

## Documentos principais

### Governança

- [Project Charter](00-governance/PROJECT-CHARTER.md)
- [Decision Log](00-governance/DECISION-LOG.md)
- [Política de continuidade e forks](00-governance/CONTINUITY-AND-FORK-POLICY.md)

### Arquitetura

- [Visão geral da arquitetura](02-architecture/ARCHITECTURE-OVERVIEW.md)
- [Perfil do agente Sócrates 2](03-agents/profiles/socrates-2/README.md)
- [Modelo de conhecimento](04-knowledge/KNOWLEDGE-MODEL.md)
- [Padrão de pacotes curriculares](05-curriculum/CURRICULUM-PACKAGE-STANDARD.md)
- [Pipeline de recuperação](06-retrieval/RETRIEVAL-PIPELINE.md)
- [Ordem de Produção Pedagógica](07-production/PEDAGOGICAL-PRODUCTION-ORDER.md)

### Entrega

- [Mapa de Epics](12-delivery/EPICS.md)
- [Escopo do MVP Sócrates 2](12-delivery/MVP-SOCRATES-2.md)

## Política de continuidade

O assistente deverá avisar quando um fork de conversa for recomendado. O próximo fork somente deverá ocorrer após a aprovação do mapa de Epics e do escopo do MVP Sócrates 2, com documento de continuidade previamente registrado no GitHub.

## Estado do projeto

Fase atual: documentação, arquitetura e delimitação do MVP.

Nenhuma implementação deve começar antes da aprovação do escopo, modelo de conhecimento, contratos dos agentes, fluxo de recuperação, Epics, Stories e critérios de qualidade.
