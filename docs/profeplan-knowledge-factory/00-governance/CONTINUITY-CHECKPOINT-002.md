# Continuidade — Marco 002

## Status

Marco aprovado integralmente em 6 de agosto de 2026, sem alterações solicitadas.

Este documento encerra a fase de decomposição do MVP Sócrates 2 em Epics selecionados, Features, User Stories, critérios de aceite, dependências, prioridades, Definition of Ready, Definition of Done, gates de aceitação e casos de falha.

## Repositório e fluxo de trabalho

- Repositório: `PaulinhoRehfeld/profeplan_v5`
- Branch: `docs/profeplan-knowledge-factory`
- Pull request: `#1 — docs: iniciar ProfePlan Knowledge Factory`
- Fase encerrada: backlog funcional e critérios de implementação do MVP
- Código de produção alterado: não
- Migrations alteradas: não
- Banco alterado: não
- Dependências alteradas: não

## Base herdada do Marco 001

Permanecem aprovadas:

1. atendimento exclusivo ao Ensino Fundamental II e Ensino Médio;
2. agentes especializados por componente, etapa e ano;
3. infraestrutura comum com perfis especializados;
4. currículos estaduais como pacotes versionados e plugáveis;
5. mesmo agente para MG e RS, sem duplicação por Estado;
6. currículo de Minas Gerais como primeiro pacote;
7. Rio Grande do Sul somente após a validação do piloto;
8. piloto com Filosofia do 2º ano do Ensino Médio;
9. agente piloto Sócrates 2;
10. estoque inicial entre 100 e 300 componentes pedagógicos revisados;
11. quatro produtos mínimos: plano, texto, atividade e avaliação formativa;
12. filtros pedagógicos, curriculares, jurídicos e de validação antes da busca vetorial;
13. componentes semielaborados como matéria-prima;
14. produção pedagógica separada da Gráfica;
15. comparação obrigatória com agente genérico;
16. documentação antes do código.

## Decisões aprovadas no Marco 002

### ADR-012 — Epics do MVP

- EPIC-001 a EPIC-017 participam do MVP em escopo reduzido;
- EPIC-018 permanece fora do MVP;
- a presença de um Epic no MVP não autoriza capacidades de Fase 2 ou Fase 3.

### ADR-013 — Priorização MoSCoW

- 35 Features classificadas como Must;
- 4 Features classificadas como Should;
- itens Could somente podem ser detalhados após estabilidade das Must;
- expansão para RS e novos agentes permanece Won't no MVP;
- gates jurídicos, pedagógicos, curriculares, autorais, inclusivos e de rastreabilidade não podem ser removidos para preservar prazo ou aparência visual.

### ADR-014 — Gates não compensatórios

O MVP não será aprovado por média simples. São bloqueadores independentes:

- fonte proibida;
- erro conceitual relevante;
- ausência de rastreabilidade;
- reprodução extensa;
- mistura curricular;
- falha de privacidade;
- descumprimento de requisito inclusivo obrigatório;
- ausência de fallback quando o conhecimento for insuficiente.

## Entregáveis aprovados

### Backlog e governança

- `12-delivery/MVP-EPIC-SELECTION.md`
- `12-delivery/MVP-FEATURES.md`
- `12-delivery/MVP-USER-STORIES.md`
- `12-delivery/MOSCOW-PRIORITIZATION.md`
- `12-delivery/MVP-DEPENDENCY-MAP.md`
- `12-delivery/DEFINITION-OF-READY.md`
- `12-delivery/DEFINITION-OF-DONE.md`

### Testes e aceitação

- `11-testing/MVP-ACCEPTANCE-MATRIX.md`
- `11-testing/FAILURE-AND-EXCLUSION-CASES.md`

## Conteúdo quantitativo aprovado

- 17 Epics selecionados em escopo reduzido;
- EPIC-018 bloqueado;
- 39 Features pertencentes ao MVP;
- 35 Features Must;
- 4 Features Should;
- 39 User Stories correspondentes;
- 1 Feature e 1 Story Won't apenas para registrar o bloqueio do EPIC-018;
- 33 gates de aceite;
- 50 casos de falha e exclusão;
- cadeia crítica organizada em ondas de execução.

## Cadeia de implementação aprovada

1. contratos e governança;
2. fontes e componentes;
3. currículo e recuperação;
4. roteamento, agente e OPP;
5. produção;
6. gates e contrato de entrega;
7. observabilidade, baseline e decisão.

### Bloqueios permanentes durante o MVP

- não executar busca vetorial antes dos filtros;
- não publicar componentes sem revisão e autorização;
- não gerar produtos sem OPP válida;
- não entregar produto aprovado sem gates Must;
- não tratar ausência de telemetria como custo ou tokens iguais a zero;
- não iniciar RS ou novos agentes antes da decisão formal do EPIC-017;
- não usar PDF, PPTX ou interface visual como substitutos da prova pedagógica.

## Definition of Ready aprovada

Uma Story somente poderá ser entregue ao Codex quando possuir, conforme aplicável:

- valor e escopo definidos;
- contrato de entrada e saída;
- critérios de aceite testáveis;
- dependências resolvidas;
- fontes e dados disponíveis;
- regras de segurança, licença e acesso;
- fallback;
- estratégia de teste;
- evidência esperada;
- aprovação dos papéis aplicáveis.

## Definition of Done aprovada

Código escrito não é suficiente. O Done exige, conforme aplicável:

- critérios de aceite atendidos;
- testes do caminho principal e das falhas;
- revisão técnica;
- revisão pedagógica;
- revisão jurídica ou de segurança;
- rastreabilidade;
- gates executados;
- observabilidade;
- documentação atualizada;
- evidências anexadas;
- ausência de ampliação silenciosa de escopo.

## Próxima fase — Marco 003

A próxima conversa deverá produzir o plano técnico de implementação antes de autorizar código.

### Objetivos

1. analisar a estrutura real do repositório e identificar onde a Knowledge Factory se integrará;
2. converter as ondas aprovadas em plano técnico incremental;
3. mapear Stories para serviços, módulos, schemas, APIs, jobs, testes e observabilidade;
4. definir contratos técnicos para fonte, segmento, componente, pacote curricular, OPP, recuperação, validação e entrega;
5. propor o modelo lógico de dados sem criar migrations;
6. propor arquitetura de busca híbrida e experimentos de embeddings sem fixar prematuramente modelo ou dimensão;
7. definir estratégia de segurança, RLS, auditoria e minimização de dados;
8. definir estratégia de testes, fixtures, casos dourados e baseline;
9. preparar lotes de tarefas para o Codex;
10. definir o primeiro lote de implementação, limitado à Onda 0 e à menor parte segura da Onda 1.

## Regra para o Marco 003

Ainda não autorizar implementação ampla.

O Marco 003 deverá primeiro produzir documentação técnica suficiente para responder:

- quais partes já existem no repositório;
- quais partes serão novas;
- quais contratos são estáveis;
- quais decisões técnicas exigem experimento;
- quais Stories podem realmente receber status Ready;
- qual será o menor PR de código seguro;
- como impedir que o Codex reinterprete o produto.

## Questões transferidas ao Marco 003

- modelo de embeddings;
- dimensão dos vetores;
- estratégia de reranqueamento;
- orçamento inicial exato de tokens;
- uma ou várias tabelas físicas de embeddings;
- estratégia de cache;
- formato técnico do contrato com a futura Gráfica;
- conjunto exato de fontes do piloto;
- versão oficial do recorte curricular MG;
- professores avaliadores;
- limiares quantitativos de relevância e similaridade;
- preço e modelo usados para estimativa de custo.

Esses pontos devem ser tratados como decisões orientadas por requisitos e experimentos, não como escolhas livres do implementador.

## Regra de continuidade

Este é o ponto oficial para realizar o segundo fork da conversa.

A nova conversa deverá manter esforço alto e continuar trabalhando na mesma branch e no mesmo Pull Request.

## Mensagem pronta para iniciar o fork

> Estamos continuando a documentação da ProfePlan Knowledge Factory no repositório `PaulinhoRehfeld/profeplan_v5`, branch `docs/profeplan-knowledge-factory`, Pull Request nº 1. Os Marcos 001 e 002 foram aprovados integralmente. Leia `docs/profeplan-knowledge-factory/00-governance/CONTINUITY-CHECKPOINT-002.md`, o `README.md`, o `DECISION-LOG.md`, `12-delivery/MVP-DEPENDENCY-MAP.md`, `12-delivery/DEFINITION-OF-READY.md`, `12-delivery/DEFINITION-OF-DONE.md` e `11-testing/MVP-ACCEPTANCE-MATRIX.md`. Continue em esforço alto e trabalhe diretamente na mesma branch e PR. Não escreva código ainda. A próxima tarefa é criar o plano técnico de implementação do MVP Sócrates 2: análise do repositório, arquitetura técnica incremental, contratos, modelo lógico de dados, serviços, segurança, testes, observabilidade, experimentos e lotes de tarefas para o Codex. Preserve todas as decisões anteriores e avise quando chegar o próximo fork. Antes dele, crie `CONTINUITY-CHECKPOINT-003.md`.

## Critério para o próximo fork

O próximo fork somente deverá ocorrer após a aprovação de:

- análise técnica do repositório;
- arquitetura técnica incremental;
- contratos técnicos;
- modelo lógico de dados;
- estratégia de segurança;
- estratégia de testes e observabilidade;
- plano de experimentos;
- lotes de tarefas para o Codex;
- definição do primeiro PR de código.

Antes desse fork deverá ser criado `CONTINUITY-CHECKPOINT-003.md`.
