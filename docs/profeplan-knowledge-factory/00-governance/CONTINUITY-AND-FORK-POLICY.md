# Política de continuidade e fork das conversas

## Objetivo

Preservar o contexto estratégico, pedagógico, arquitetônico e documental do ProfePlan Knowledge Factory sem depender de uma única conversa longa.

## Princípio

Os forks não serão feitos por uma contagem rígida de mensagens. Eles ocorrerão ao final de marcos documentais, quando o contexto atual já estiver consolidado no GitHub e a próxima fase exigir outro foco.

## Responsabilidade do assistente

O assistente deverá:

1. acompanhar o volume e a complexidade da conversa;
2. avisar explicitamente quando um fork for recomendado;
3. não sugerir o fork antes de registrar as decisões no repositório;
4. criar um documento de continuidade antes de cada fork;
5. informar qual branch, pull request, documentos e pendências devem orientar a nova conversa;
6. fornecer uma mensagem inicial pronta para o novo fork.

## Responsabilidade do responsável pelo produto

O responsável pelo produto deverá:

1. realizar o fork somente após o aviso explícito;
2. iniciar a nova conversa a partir da mensagem de continuidade preparada;
3. manter o trabalho no mesmo projeto e repositório;
4. evitar iniciar decisões paralelas sobre o mesmo tema em conversas diferentes.

## Gatilhos de fork

Um fork deverá ser recomendado quando ocorrer pelo menos uma destas condições:

- conclusão de uma grande fase documental;
- mudança de arquitetura para implementação;
- mudança de Epics para Stories detalhadas;
- mudança de Stories para tarefas técnicas e código;
- acúmulo aproximado de 20 a 30 interações substanciais após o último marco;
- necessidade recorrente de recuperar decisões muito antigas;
- aumento do risco de contradição terminológica ou perda de contexto;
- solicitação explícita do responsável pelo produto.

A contagem de interações é apenas um indicador auxiliar. O critério principal será a conclusão de marcos.

## Marcos planejados

### Conversa atual

Escopo:

- visão da Knowledge Factory;
- modelo da loja, fábricas, almoxarifado e Gráfica;
- agentes especializados;
- modelo de conhecimento;
- currículos plugáveis;
- mapa de Epics;
- delimitação do MVP Sócrates 2.

### Primeiro fork recomendado

Será feito após a aprovação de:

- mapa de Epics;
- separação entre MVP, expansão e futuro;
- escopo fechado do MVP Sócrates 2;
- dependências principais entre Epics.

Tema da nova conversa:

- Features;
- User Stories;
- critérios de aceite;
- Definition of Ready;
- Definition of Done.

### Segundo fork recomendado

Será feito após a aprovação das Stories do MVP e dos critérios de aceite.

Tema da nova conversa:

- desenho técnico;
- banco de dados;
- contratos;
- APIs;
- tarefas técnicas;
- plano de implementação para o Codex.

### Terceiro fork recomendado

Será feito antes do início da implementação significativa.

Tema da nova conversa:

- acompanhamento dos pull requests do Codex;
- revisão arquitetônica;
- testes;
- correções;
- validação do piloto.

## Documento de continuidade

Antes de cada fork deverá ser criado um arquivo em:

`00-governance/continuity/`

Padrão de nome:

`CONTINUITY-YYYY-MM-DD-MILESTONE.md`

Cada documento deverá conter:

- objetivo da fase encerrada;
- decisões aprovadas;
- decisões rejeitadas ou substituídas;
- documentos criados ou atualizados;
- branch e pull request em uso;
- escopo do próximo ciclo;
- pendências;
- riscos;
- termos oficiais;
- instrução inicial para a nova conversa.

## Estado atual

Ainda não é necessário realizar um fork.

O próximo aviso deverá ocorrer após a aprovação do mapa de Epics e do escopo do MVP Sócrates 2.
