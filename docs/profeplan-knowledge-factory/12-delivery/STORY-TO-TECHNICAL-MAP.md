# Mapa de User Stories para Componentes Técnicos

## Status

Proposta do Marco 003. Os caminhos representam a arquitetura recomendada no monorepo executável e poderão ser ajustados após a decisão do repositório canônico.

## Legenda de alvos

- **Types:** `packages/types` ou pacote de contratos equivalente;
- **PNLD:** `packages/industry-pnld`;
- **Curriculum:** `packages/industry-curriculum`;
- **DB:** `packages/db` + migrations futuras;
- **AI:** `packages/ai`;
- **Agents:** `packages/agents`;
- **BFF:** `apps/bff`;
- **Web:** `apps/web`;
- **Logger:** `packages/logger`/observabilidade existente;
- **Graphics:** `packages/graphics-profeplan`, apenas contrato futuro.

## Mapeamento

| Story | Contratos/dados | Serviço ou módulo principal | API/job | Validadores e testes |
|---|---|---|---|---|
| US-001.1 Baseline aprovado | índice documental e ADRs | documentação | nenhum | link check, consistência documental |
| US-001.2 DoR/DoD | metadados de Story | governança/CI | gate de PR | checklist e evidência obrigatória |
| US-002.1 Registrar fonte | KnowledgeSource, SourceVersion | PNLD + DB | comando/API interna `registerSource` | schema, checksum, campos obrigatórios |
| US-002.2 Autorizar/bloquear | permission event | PNLD + segurança | `changeSourcePermission` | transição, auditoria, fonte bloqueada |
| US-003.1 Ingestão assistida | ingest job, version ref | PNLD | job `ingestSourceVersion` | idempotência, falha parcial, revisão |
| US-003.2 Preservar estrutura | SourceSegment | PNLD | job `segmentSource` | ordem, localização, tipos, baixa confiança |
| US-004.1 Componente canônico | Component, ComponentVersion | PNLD/knowledge + DB | `createComponentDraft` | contrato, não ser produto final, evidência |
| US-004.2 Tipologia | enums e regras por tipo | Types + PNLD | validação interna | combinações válidas e distribuição |
| US-004.3 Revisar/versionar | estados e histórico | PNLD + DB | `reviewComponent` | concorrência, histórico, elegibilidade |
| US-005.1 Destilação autoral | evidence + draft | PNLD + AI assistida | job/comando de destilação | similaridade, fonte permitida, revisão humana |
| US-005.2 Deduplicação | DeduplicationDecision | PNLD | job de candidatos + decisão humana | merge/relate/separate, divergências |
| US-006.1 Pacote MG | CurriculumPackage/Node | Curriculum + DB | ingestão/ativação interna | versão, vigência, recorte, bloqueio RS |
| US-006.2 Vínculos | ComponentCurriculumLink | Curriculum | `proposeLink`, `reviewLink` | sugestão versus aprovado, justificativa |
| US-007.1 Filtros prévios | QueryPlan, scope policy | retrieval em Curriculum/DB | `applyEligibilityFilters` | hard negatives, licença, tenant, status |
| US-007.2 Busca híbrida | RetrievalRun/Candidate | retrieval + AI adapter | `searchLexical`, `searchSemantic`, `fuse` | Recall@k, nDCG, máximo 8, dedup |
| US-007.3 Insuficiência | SufficiencyResult | retrieval + Agents | `assessSufficiency` | sem candidatos, baixa relevância, falso suficiente |
| US-008.1 Roteamento | AgentProfile/Scope | Agents | `resolveAgent` | outro ano/disciplina/Estado, ambiguidade |
| US-008.2 Coordenar gates | ValidationRun | Agents quality pipeline | `runRequiredGates` | ordem, erro de gate, resposta única |
| US-009.1 Perfil Sócrates 2 | profile + knowledge scope | Agents | registro/configuração | bloqueios, acesso complementar, fallback |
| US-009.2 Quatro produtos | product schemas | Agents + AI | `generateProduct` | contrato por produto, gates e rastreabilidade |
| US-009.3 Pacote integrado | integrated package schema | Agents | `generateIntegratedPackage` | coerência entre peças e tempo total |
| US-010.1 Criar OPP | ProductionOrder/version | Agents/domain + DB | BFF `createProductionOrder` | campos, idempotência, transições |
| US-010.2 Linha do tempo | OPPEvent | Agents + Logger/DB | `appendOppEvent`, consulta | reconstrução, retry e falhas preservadas |
| US-011.1 Plano de composição | CompositionPlan | Agents + AI | interno antes da geração | usa apenas contexto, estrutura por produto |
| US-011.2 Personalização | requisitos OPP | Agents + AI | geração | duração, leitura, recursos, sem fuga de escopo |
| US-011.3 Variações | variation request | Agents + AI | geração opcional | diferença real, custo, objetivo preservado |
| US-012.1 Currículo/conceitos | findings | quality pipeline | gates currículo/precisão | erros conceituais, mistura, código inventado |
| US-012.2 Coerência pedagógica | findings | quality pipeline | gate pedagógico | objetivo–atividade–avaliação–tempo |
| US-012.3 Automático × docente | judgments | avaliação | interface/comando de julgamento | concordância, falso positivo/negativo |
| US-013.1 Proximidade lexical | similarity finding | quality + PNLD | autoria gate | fontes recuperadas, atividade integral, thresholds |
| US-013.2 Linhagem | lineage refs | DB + delivery | `getProductLineage` interno | versões completas sem expor texto protegido |
| US-014.1 Necessidade inclusiva | requisitos funcionais | OPP/BFF/Web | criação de OPP | minimização, incompatibilidade, ausência de diagnóstico |
| US-014.2 Gate inclusivo | findings | quality | inclusion gate | instruções, alternativas, objetivo preservado |
| US-015.1 Entrega estruturada | DeliveryContract | Agents/BFF/Web | `deliverProduct`, `getProduct` | schema, OPP/gates, idempotência |
| US-015.2 Requisitos Gráfica | visual hints | Types + Graphics futuro | nenhum obrigatório | não altera conteúdo, ausência não bloqueia MVP |
| US-016.1 Medir OPP | traces/events/metrics | Logger/observability | instrumentação | spans, falhas seguras, conteúdo redigido |
| US-016.2 Tokens/custo | usage metrics | AI + Logger | instrumentação | tabela versionada, estimativa explícita, total |
| US-017.1 Casos dourados | EvaluationCase/Run | testing harness | execução em lote | paridade, cegamento, resultados preservados |
| US-017.2 Decisão do piloto | PilotDecision | governança | relatório/aprovação | evidências, responsáveis, EPIC-018 bloqueado |
| US-018.1 Expansão | não aplicável | bloqueado | nenhum | nunca Ready antes da US-017.2 |

## Endpoints mínimos candidatos

Os nomes são lógicos; transporte final dependerá do BFF existente.

### Professor

- criar OPP;
- consultar OPP;
- consultar produto entregue;
- solicitar ajuste permitido.

### Interno/curadoria

- registrar fonte;
- alterar permissão;
- iniciar ingestão;
- revisar segmentos;
- criar/revisar componente;
- revisar vínculo curricular;
- executar dataset de avaliação.

O MVP não exige expor todas essas operações em uma interface gráfica. Comandos internos autenticados e fixtures são aceitáveis quando documentados.

## Jobs mínimos

- ingestão de versão;
- segmentação;
- geração de embeddings;
- reindexação após mudança;
- sugestão de duplicidade;
- avaliação em lote.

## Regras de dependência por Story

- US-007.* depende de US-002.*, US-004.* e US-006.*;
- US-008.* depende de US-007.*, US-009.1 e US-010.*;
- US-009.2 depende de contratos de produto, OPP e retrieval;
- US-011.* depende de contexto rastreável;
- US-012–014 dependem de output estruturado e evidências;
- US-015.1 depende de aprovação dos gates;
- US-016.* deve entrar desde o primeiro fluxo, não ao final;
- US-017.* depende do fluxo completo e do baseline;
- US-018.1 permanece bloqueada.

## Regra para Codex

Cada tarefa técnica deverá citar:

- Story e Feature;
- contrato relevante;
- módulo alvo;
- testes obrigatórios;
- dependências;
- itens explicitamente fora do escopo;
- evidência de DoR.

Codex não poderá criar módulo novo apenas porque o mapeamento lógico não corresponde exatamente à árvore existente; deverá primeiro documentar a incompatibilidade.
