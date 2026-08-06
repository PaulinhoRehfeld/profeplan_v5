# Lotes de Implementação para o Codex

## Status

Proposta do Marco 003. Nenhum lote está autorizado até aprovação do marco e decisão do repositório canônico.

## Regras para todos os lotes

Cada tarefa do Codex deverá:

- citar Epics, Features e Stories;
- ler contratos e ADRs;
- declarar arquivos que pretende alterar;
- confirmar itens fora do escopo;
- produzir plano antes de editar;
- manter PR pequeno;
- incluir testes e evidências;
- não instalar dependência sem justificar;
- não criar migration fora do lote aprovado;
- não alterar frontend junto com domínio/banco sem necessidade;
- não escolher modelo ou vetor fora dos experimentos;
- parar e registrar conflito em vez de improvisar.

## Lote 0 — Sincronização e descoberta final

Tipo: documental/operacional, sem código de produto.

Objetivos:

- confirmar repositório canônico;
- copiar documentação aprovada para o monorepo;
- inventariar schema atual, branches, CI e módulos;
- mapear conflitos com tipos e migrations existentes;
- registrar comandos de build/teste;
- confirmar branch base.

Stories relacionadas:

- US-001.1;
- US-001.2.

Saída:

- documentação sincronizada;
- relatório de impacto;
- Stories do Lote 1 em Ready;
- nenhum comportamento alterado.

## Lote 1 — Contratos puros e fixtures

Objetivo:

Criar contratos versionados e testes sem banco, API, provider ou agente.

Escopo:

- fonte e versão;
- permissão;
- segmento;
- componente e versão;
- evidência;
- pacote curricular e nó;
- OPP e eventos;
- QueryPlan/ContextPackage;
- findings e entrega;
- enums e transições;
- fixtures válidas/inválidas.

Stories habilitadas:

- US-002.1;
- US-002.2;
- US-003.2 parcialmente;
- US-004.1;
- US-004.2;
- US-004.3 parcialmente;
- US-006.1 parcialmente;
- US-010.1;
- US-014.1;
- US-015.1;
- US-016.1 parcialmente.

Não inclui:

- migrations;
- Prisma;
- APIs;
- embeddings;
- OpenAI;
- prompts;
- agent runtime.

## Lote 2 — Domínio, ciclo de vida e repositórios abstratos

Objetivo:

Implementar regras de negócio independentes da persistência física.

Escopo:

- elegibilidade de fonte;
- transições de componente;
- vínculo curricular;
- máquina de estados da OPP;
- política do agente;
- auditoria lógica;
- interfaces de repositório;
- testes unitários.

Stories:

- US-002.*;
- US-004.*;
- US-006.* parcialmente;
- US-009.1 parcialmente;
- US-010.* parcialmente;
- US-013.2 parcialmente.

## Lote 3 — Persistência, migrations e RLS

Pré-requisito: modelo físico e plano de rollback aprovados em PR separado de revisão.

Objetivo:

Persistir fontes, componentes, currículo, OPP e auditoria com isolamento.

Escopo:

- análise e extensão do schema existente;
- migrations incrementais;
- repositórios concretos;
- RLS;
- funções administrativas mínimas;
- testes de integração e tenant isolation;
- seeds sintéticos.

Não inclui vetores se o experimento ainda não definiu configuração.

## Lote 4 — Ingestão piloto assistida

Objetivo:

Registrar arquivo autorizado, segmentar e produzir drafts revisáveis.

Escopo:

- ingest job;
- idempotência;
- localização estrutural;
- revisão por comando/fixture;
- destilação assistida;
- deduplicação candidata;
- eventos.

Stories:

- US-003.*;
- US-005.*.

Não inclui OCR industrial ou painel administrativo completo.

## Lote 5 — Pacote MG e filtros determinísticos

Objetivo:

Ativar somente o recorte curricular do piloto e garantir exclusões antes da similaridade.

Escopo:

- importação/normalização do pacote;
- nós;
- vínculos;
- resolução por vigência;
- AgentKnowledgeScope;
- hard negatives;
- consulta elegível.

Stories:

- US-006.*;
- US-007.1;
- US-009.1.

## Lote 6 — Harness de retrieval e baseline lexical

Objetivo:

Criar avaliação reproduzível antes de embeddings.

Escopo:

- dataset de consultas;
- relevance judgments;
- QueryPlan;
- busca lexical;
- RetrievalRun;
- métricas;
- suficiência inicial;
- orçamento.

Stories:

- US-007.1;
- parte de US-007.2;
- US-007.3;
- US-016.*;
- preparação de US-017.1.

## Lote 7 — Embeddings e busca híbrida experimental

Objetivo:

Executar candidatos de embedding e fusão sem promover configuração antes dos resultados.

Escopo:

- adapters;
- embeddings versionados;
- indexação experimental;
- busca semântica;
- fusão;
- reranker apenas em variante experimental;
- relatório.

Stories:

- US-007.2;
- US-016.*;
- parte de US-017.1.

## Lote 8 — OPP, roteamento e geração de um produto

Objetivo:

Primeiro slice executável de ponta a ponta com um produto, preferencialmente plano de aula.

Escopo:

- BFF mínimo;
- OPP;
- Sócrates 2;
- ContextPackage;
- CompositionPlan;
- ModelPolicy;
- schema de saída;
- feature flag;
- logs.

Stories:

- US-008.1;
- US-009.1;
- parte de US-009.2;
- US-010.*;
- US-011.1;
- parte de US-011.2;
- US-016.*.

## Lote 9 — Quality pipeline e entrega

Objetivo:

Impedir entrega sem aprovação e produzir contrato rastreável.

Escopo:

- gates G1–G12 em incrementos;
- adaptação de validadores existentes;
- autoria;
- inclusão;
- lineage;
- DeliveryContract;
- retry controlado.

Stories:

- US-008.2;
- US-012.*;
- US-013.*;
- US-014.2;
- US-015.1.

## Lote 10 — Quatro produtos e pacote integrado

Objetivo:

Expandir o slice validado para texto, atividade e avaliação.

Stories:

- conclusão de US-009.2;
- US-009.3 Should;
- US-011.2;
- US-011.3 Should;
- US-015.2 Should.

## Lote 11 — Interface mínima e piloto controlado

Objetivo:

Permitir pedido, acompanhamento e entrega na experiência existente.

Escopo:

- fluxo simples no `apps/web`;
- estados de erro/insuficiência;
- acessibilidade;
- grupo piloto;
- rollback;
- sem Gráfica avançada.

## Lote 12 — Avaliação comparativa e decisão

Objetivo:

Executar o piloto, comparar baseline e produzir decisão formal.

Stories:

- US-012.3;
- US-017.1;
- US-017.2.

## Dependências rígidas

```text
L0 → L1 → L2 → L3
L3 → L4 → L5 → L6 → L7
L5 + L6 → L8 → L9 → L10 → L11 → L12
```

L7 pode ser adiado se o baseline lexical atender temporariamente ao slice técnico, mas US-007.2 só será concluída após o experimento híbrido.

## Tamanho de PR

- um objetivo principal;
- preferencialmente um domínio/pacote;
- migrations separadas de frontend;
- experimentos separados de promoção produtiva;
- refactors não relacionados proibidos;
- documentação e testes no mesmo PR da capacidade.

## Critérios para interromper o Codex

- repositório divergente;
- contrato ausente;
- Story não Ready;
- migration conflitante;
- necessidade de nova dependência não aprovada;
- alteração de escopo;
- escolha de modelo sem experimento;
- impossibilidade de testar;
- exposição de dado/segredo;
- tentativa de incluir EPIC-018.
