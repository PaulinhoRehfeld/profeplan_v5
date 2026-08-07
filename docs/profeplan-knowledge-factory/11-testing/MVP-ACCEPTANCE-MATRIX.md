# Matriz de aceite — MVP Sócrates 2

## Objetivo

Consolidar os gates que devem ser demonstrados no fluxo de ponta a ponta. Os critérios detalhados permanecem nas User Stories; esta matriz define as evidências mínimas de aceitação do MVP.

## Escala de resultado

- **Aprovado:** critério atendido com evidência suficiente;
- **Reprovado:** critério não atendido;
- **Inconclusivo:** evidência ausente ou insuficiente;
- **Não aplicável:** somente quando justificado e aprovado.

## Gates de entrada

| Gate | Critério | Evidência mínima | Bloqueia geração? |
|---|---|---|---|
| G-01 Fonte identificada | origem, versão e localização registradas | registro da fonte | Sim |
| G-02 Permissão válida | geração autorizada | classe de licença e status | Sim |
| G-03 Estrutura preservada | seção e tipo de bloco auditáveis | segmentos de exemplo | Sim |
| G-04 Componente aprovado | metadados, versão e revisão | componente aprovado | Sim |
| G-05 Currículo ativo | MG, Filosofia, EM, 2º ano | pacote e versão | Sim |

## Gates de recuperação

| Gate | Critério | Evidência mínima | Bloqueia geração? |
|---|---|---|---|
| G-06 Filtros prévios | disciplina, etapa, ano, Estado, licença e status aplicados antes do vetor | log da consulta | Sim |
| G-07 Relevância | componentes pertinentes ao pedido | resultados e avaliação | Sim quando insuficiente |
| G-08 Limite de contexto | até oito componentes principais, salvo exceção | pacote de produção | Sim quando injustificado |
| G-09 Ausência de mistura | nenhum item inelegível | conjunto recuperado | Sim |
| G-10 Suficiência | base adequada ou fallback explícito | decisão registrada | Sim |

## Gates de produção

| Gate | Critério | Evidência mínima | Bloqueia entrega? |
|---|---|---|---|
| G-11 Roteamento correto | Sócrates 2 somente para escopo válido | decisão de roteamento | Sim |
| G-12 OPP válida | requisitos e versões registrados | OPP | Sim |
| G-13 Planejamento de composição | estrutura anterior à redação | registro de composição | Sim |
| G-14 Personalização | contexto informado modifica o produto | comparação de saídas | Sim quando requisito obrigatório |
| G-15 Contrato de produto | saída estruturada e versionada | contrato validado | Sim |

## Gates de qualidade

| Gate | Critério | Evidência mínima | Bloqueia entrega aprovada? |
|---|---|---|---|
| G-16 Currículo | alinhamento ao recorte MG | parecer do gate | Sim |
| G-17 Correção conceitual | ausência de erro filosófico relevante | parecer e evidências | Sim |
| G-18 Coerência pedagógica | objetivo, conteúdo, atividade e avaliação relacionados | rubrica | Sim |
| G-19 Viabilidade temporal | execução compatível com duração | análise de tempo | Sim |
| G-20 Clareza e nível | adequado ao 2º ano | rubrica docente | Sim |
| G-21 Inclusão | requisitos solicitados atendidos | checklist | Sim |
| G-22 Autoria | ausência de reprodução extensa | relatório lexical | Sim |
| G-23 Rastreabilidade | produto → componentes → fontes | linhagem | Sim |

## Gates operacionais

| Gate | Critério | Evidência mínima | Bloqueia avaliação do piloto? |
|---|---|---|---|
| G-24 Telemetria | etapas, duração, falhas e versões registradas | evento por OPP | Sim |
| G-25 Tokens | entrada e saída mensuráveis ou ausência explícita | relatório | Sim para comparação |
| G-26 Custo | custo calculável com preço versionado | relatório | Sim para viabilidade |
| G-27 Repetibilidade | casos podem ser reexecutados com histórico | execuções | Sim |
| G-28 Segurança de logs | sem dado sensível ou conteúdo restrito desnecessário | inspeção | Sim |

## Gates de avaliação

| Gate | Critério | Evidência mínima | Bloqueia expansão? |
|---|---|---|---|
| G-29 Casos dourados | quatro produtos e temas diversos | suíte executada | Sim |
| G-30 Baseline comparável | pedido e condições equivalentes | pares de execução | Sim |
| G-31 Avaliação docente | rubrica e pareceres | amostras avaliadas | Sim |
| G-32 Falhas registradas | resultados negativos não omitidos | relatório completo | Sim |
| G-33 Decisão formal | avançar, ajustar ou interromper | decisão assinada por papel responsável | Sim |

## Critérios globais para aprovação do MVP

O MVP somente poderá ser aprovado quando:

1. todos os gates bloqueantes aplicáveis estiverem aprovados;
2. não houver uso de fonte sem permissão;
3. não houver mistura indevida recorrente;
4. os quatro produtos mínimos tiverem casos aprovados;
5. baseline e Sócrates 2 tiverem sido comparados;
6. tokens, custo e latência estiverem documentados;
7. professores tiverem avaliado amostras;
8. falhas e exclusões estiverem registradas;
9. houver decisão formal de continuidade;
10. EPIC-018 permanecer fora até essa decisão.

## Aprovação condicional

Aprovação condicional somente poderá ocorrer para iniciar novo ciclo de correção, não expansão. Deve registrar:

- gates pendentes;
- risco;
- prazo ou condição de reavaliação;
- responsável;
- funcionalidades bloqueadas.

## Proibição de média compensatória

Uma pontuação alta em criatividade, velocidade ou aparência não compensa:

- fonte proibida;
- erro conceitual relevante;
- ausência de rastreabilidade;
- reprodução extensa;
- mistura curricular;
- falha de privacidade;
- gate obrigatório ignorado.
