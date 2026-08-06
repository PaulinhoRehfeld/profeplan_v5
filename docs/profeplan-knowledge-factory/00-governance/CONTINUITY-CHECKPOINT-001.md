# Continuidade — Marco 001

## Status

Marco aprovado em 6 de agosto de 2026.

Este documento encerra a fase inicial de visão, arquitetura, mapa de Epics e definição do MVP do agente piloto Sócrates 2.

## Repositório e fluxo de trabalho

- Repositório: `PaulinhoRehfeld/profeplan_v5`
- Branch: `docs/profeplan-knowledge-factory`
- Pull request: `#1 — docs: iniciar ProfePlan Knowledge Factory`
- Fase atual: documentação e arquitetura
- Código de produção alterado: não
- Migrations alteradas: não
- Dependências alteradas: não

## Decisões aprovadas

1. O ProfePlan atenderá somente Ensino Fundamental II e Ensino Médio.
2. O Ensino Fundamental II compreenderá 6º, 7º, 8º e 9º anos.
3. O Ensino Médio compreenderá 1º, 2º e 3º anos.
4. Os agentes serão especializados por componente curricular, etapa e ano.
5. A infraestrutura será comum, com perfis especializados, sem duplicação de código por agente.
6. Currículos estaduais serão pacotes versionados e plugáveis.
7. O mesmo agente poderá trabalhar com MG ou RS.
8. Um produto utilizará somente um currículo estadual principal, salvo modo comparativo explícito.
9. Minas Gerais será o pacote inicial.
10. Rio Grande do Sul será a próxima implantação curricular.
11. O piloto será Filosofia do 2º ano do Ensino Médio.
12. O agente piloto será Sócrates 2.
13. As matérias-primas serão componentes pedagógicos semielaborados, estruturados, rastreáveis e vetorizados quando aplicável.
14. Filtros pedagógicos, curriculares, jurídicos e de validação serão aplicados antes da busca vetorial.
15. A produção pedagógica será separada do acabamento editorial da Gráfica.
16. A produção será coordenada por uma Ordem de Produção Pedagógica.
17. A documentação precederá a implementação.
18. O trabalho continuará em esforço alto enquanto forem tomadas decisões arquitetônicas, de escopo e de aceitação.

## MVP aprovado

### Escopo

- componente: Filosofia;
- etapa: Ensino Médio;
- ano: 2º ano;
- currículo inicial: Minas Gerais;
- agente: Sócrates 2;
- estoque inicial: entre 100 e 300 componentes pedagógicos revisados;
- fontes: pequeno conjunto autorizado, aberto, próprio ou licenciado;
- comparação obrigatória: Sócrates 2 versus agente genérico.

### Produtos mínimos

1. plano de aula;
2. texto didático;
3. atividade reflexiva;
4. avaliação formativa curta.

### Temas iniciais sugeridos

- ética e moral;
- liberdade e responsabilidade;
- conhecimento, verdade e opinião;
- política, poder e cidadania;
- ciência e senso comum;
- fé e razão;
- identidade e existência;
- tecnologia, ética e sociedade.

### Fora do MVP

- Gráfica avançada;
- geração sofisticada de PDF;
- geração sofisticada de apresentações;
- múltiplos componentes curriculares simultâneos;
- múltiplos Estados simultâneos;
- produção automática em escala nacional;
- ingestão indiscriminada de coleções PNLD;
- autonomia total sem validação humana.

## Epics aprovados

O mapa atual contém 18 Epics:

1. governança e fundação arquitetônica;
2. governança das fontes e direitos de uso;
3. ingestão e leitura estrutural;
4. componentes pedagógicos semielaborados;
5. destilação e deduplicação;
6. pacotes curriculares plugáveis;
7. almoxarifado inteligente e busca híbrida;
8. orquestração multiagente;
9. agente piloto Sócrates 2;
10. Ordem de Produção Pedagógica;
11. geração autoral e personalização;
12. qualidade pedagógica e curricular;
13. Guardião Autoral e rastreabilidade;
14. inclusão e acessibilidade;
15. contrato de entrega e Gráfica;
16. observabilidade, tokens, custo e latência;
17. avaliação do piloto;
18. expansão para RS e novos agentes.

## Próxima fase

A próxima conversa deverá trabalhar exclusivamente na decomposição do MVP em:

1. Features;
2. User Stories;
3. critérios de aceite;
4. dependências;
5. prioridades;
6. Definition of Ready;
7. Definition of Done;
8. casos de falha e critérios de exclusão.

Não iniciar código nessa fase.

## Ordem sugerida da próxima fase

1. selecionar os Epics efetivamente pertencentes ao MVP;
2. criar as Features de cada Epic do MVP;
3. criar Stories orientadas ao valor pedagógico e operacional;
4. definir critérios de aceite testáveis;
5. identificar dependências entre Stories;
6. classificar em Must, Should, Could e Won't;
7. definir Definition of Ready;
8. definir Definition of Done;
9. preparar o pacote documental para o Codex.

## Questões ainda pendentes

- modelo específico de embeddings;
- dimensão dos vetores;
- estratégia de reranqueamento;
- orçamento exato de tokens por agente;
- política jurídica detalhada por categoria de obra PNLD;
- organização física das tabelas de embeddings;
- estratégia de cache;
- formato técnico do contrato futuro com a Gráfica;
- conjunto exato de fontes do piloto;
- critérios quantitativos finais para aprovar o piloto.

Essas questões não devem ser decididas por conveniência técnica antes de existirem Stories e critérios de aceite que as justifiquem.

## Regra de continuidade

Este é o ponto oficial para realizar um fork da conversa.

A nova conversa deverá manter esforço alto e utilizar este documento, o README do projeto, o mapa de Epics e o documento do MVP como fontes primárias.

## Mensagem pronta para iniciar o fork

> Estamos continuando a documentação da ProfePlan Knowledge Factory no repositório `PaulinhoRehfeld/profeplan_v5`, branch `docs/profeplan-knowledge-factory`, pull request #1. O Marco 001 foi aprovado e está documentado em `docs/profeplan-knowledge-factory/00-governance/CONTINUITY-CHECKPOINT-001.md`. Leia esse documento, o `README.md`, `12-delivery/EPICS.md` e `12-delivery/MVP-SOCRATES-2.md`. Não escreva código. Continue em esforço alto. A próxima tarefa é selecionar os Epics do MVP e criar Features, User Stories, critérios de aceite, dependências, prioridades, Definition of Ready e Definition of Done para o piloto Sócrates 2.

## Critério para o próximo fork

O próximo fork deverá ocorrer somente após a aprovação de:

- Features do MVP;
- User Stories do MVP;
- critérios de aceite;
- prioridades;
- Definition of Ready;
- Definition of Done.

Antes desse próximo fork, deverá ser criado o documento `CONTINUITY-CHECKPOINT-002.md`.
