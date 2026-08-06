# Arquitetura Técnica Incremental do MVP Sócrates 2

## Status

Proposta do Marco 003. Nenhuma onda autoriza código antes da aprovação do marco e da definição do repositório canônico.

## Princípio

A implementação será vertical e incremental. Cada onda deverá produzir uma capacidade verificável, preservar rastreabilidade e manter os gates das ondas anteriores.

Não será aceita a estratégia de criar primeiro todas as tabelas, depois todos os agentes e somente no final testar o fluxo. O MVP precisa provar cedo que uma fonte autorizada pode originar um componente, ser recuperada com filtro correto e sustentar um produto rastreável.

## Limites arquitetônicos

- um único agente piloto: Sócrates 2;
- um único pacote estadual ativo: MG;
- Filosofia do 2º ano do Ensino Médio;
- quatro produtos mínimos;
- ingestão assistida, não industrial;
- 100 a 300 componentes revisados;
- no máximo oito componentes no pacote principal de contexto;
- nenhuma Gráfica avançada;
- nenhuma expansão do EPIC-018;
- nenhuma escolha definitiva de embedding, dimensão, reranker ou cache sem experimento.

## Fluxo-alvo

```mermaid
flowchart LR
    A[Fonte autorizada] --> B[Registro e versão]
    B --> C[Segmentação assistida]
    C --> D[Destilação e revisão]
    D --> E[Componente pedagógico aprovado]
    E --> F[Vínculo curricular MG]
    F --> G[Indexação textual e vetorial]
    H[Pedido do professor] --> I[OPP]
    I --> J[Roteamento Sócrates 2]
    J --> K[Filtros obrigatórios]
    K --> L[Busca híbrida]
    L --> M[Context package]
    M --> N[Geração por contrato]
    N --> O[Quality gates]
    O --> P[Contrato de entrega]
    P --> Q[Avaliação e observabilidade]
```

## Onda 0 — Decisões e contratos

### Objetivo

Eliminar ambiguidades que causariam retrabalho de código.

### Entregas

- decisão do repositório canônico;
- contratos técnicos versionados;
- modelo lógico de dados;
- matriz de permissões e RLS;
- plano de experimentos de recuperação;
- fixtures mínimas e casos dourados;
- lotes Codex e primeiro PR definidos.

### Gate de saída

Nenhum contrato Must possui campo crítico pendente, e as Stories do primeiro lote cumprem a DoR.

## Onda 1 — Fundação contratual e catálogo de fontes

### Objetivo

Criar a base mais segura sem acessar modelos de IA nem criar busca vetorial.

### Capacidades

- tipos e schemas de fonte, versão e permissão;
- estados controlados de ciclo de vida;
- checksum e idempotência;
- contratos de auditoria;
- testes de fonte bloqueada e versão inválida;
- fixtures de fontes abertas, próprias, licenciadas e bloqueadas.

### Não inclui

- upload público;
- OCR;
- embeddings;
- geração;
- interface administrativa completa.

### Gate de saída

Nenhuma fonte sem autorização pode alcançar estado elegível para processamento gerativo.

## Onda 2 — Segmentação e componentes pedagógicos

### Objetivo

Provar a transformação assistida da matéria-prima em unidades semielaboradas auditáveis.

### Capacidades

- registro de arquivo e segmento;
- localização estrutural;
- tipologia de segmento;
- componente canônico e versão;
- evidências componente–fonte;
- revisão humana;
- estados `draft`, `in_review`, `approved`, `rejected`, `superseded`;
- deduplicação assistida.

### Gate de saída

Um conjunto inicial de componentes pode ser reconstruído até a fonte e somente versões aprovadas são elegíveis.

## Onda 3 — Pacote curricular e filtros determinísticos

### Objetivo

Garantir o território pedagógico antes de qualquer similaridade.

### Capacidades

- pacote MG versionado;
- nós curriculares do recorte Filosofia/EM/2º ano;
- vínculo revisável componente–currículo;
- política de escopo do Sócrates 2;
- consulta determinística por disciplina, etapa, ano, Estado, status e licença;
- testes de vazamento com hard negatives.

### Gate de saída

Candidatos de outro componente, ano, Estado ou licença são excluídos antes da busca textual ou vetorial.

## Onda 4 — Recuperação híbrida experimental

### Objetivo

Escolher a menor arquitetura de busca que atenda relevância, custo e latência.

### Capacidades

- baseline textual;
- candidatos de embeddings comparáveis;
- fusão de rankings;
- deduplicação;
- orçamento de contexto;
- estado de insuficiência;
- registro auditável do retrieval run;
- avaliação Recall@k, nDCG@k, MRR, p50/p95, custo e tokens.

### Gate de saída

A configuração candidata supera ou justifica sua complexidade em relação ao baseline, sem violar filtros.

## Onda 5 — OPP, roteamento e Sócrates 2

### Objetivo

Executar um pedido rastreável de ponta a ponta sem interface avançada.

### Capacidades

- contrato e máquina de estados da OPP;
- roteamento explícito;
- perfil técnico Sócrates 2;
- context package;
- geração de um produto por vez;
- templates versionados;
- separação entre conteúdo do professor e estudante;
- fallback fora de escopo.

### Gate de saída

Um pedido válido gera um produto estruturado; pedido fora do escopo ou sem base suficiente não improvisa.

## Onda 6 — Validação e entrega

### Objetivo

Garantir que a resposta somente seja aprovada após os gates não compensatórios.

### Capacidades

- formato;
- currículo;
- segurança e privacidade;
- qualidade filosófica e pedagógica;
- inclusão mínima;
- autoria e proximidade com fontes;
- rastreabilidade;
- contrato de entrega simples;
- relatório interno de validação.

### Gate de saída

Falha em qualquer gate Must impede status `approved` e entrega como produto validado.

## Onda 7 — Avaliação comparativa e piloto controlado

### Objetivo

Demonstrar que a especialização produz vantagem mensurável.

### Capacidades

- dataset dourado;
- agente genérico baseline;
- execução pareada;
- avaliação humana cega quando viável;
- métricas pedagógicas, curriculares, autorais, custo e latência;
- relatório de decisão continuar, corrigir ou encerrar;
- feature flag e rollback.

### Gate de saída

Decisão humana registrada com evidências suficientes. Somente depois poderá ser considerada expansão.

## Fronteiras síncronas e assíncronas

### Assíncrono

- ingestão de arquivo;
- extração e segmentação;
- geração de embeddings;
- deduplicação de estoque;
- reindexação;
- avaliações em lote;
- relatórios de experimento.

### Síncrono

- criação e validação inicial da OPP;
- roteamento;
- recuperação em estoque publicado;
- geração do produto;
- gates necessários à entrega;
- consulta do resultado.

O MVP pode iniciar jobs assíncronos por comandos ou funções existentes; não exige criar `apps/workers` antes de demonstrar necessidade operacional.

## Regra de dependência

```text
contrato → teste de contrato → persistência → serviço → endpoint/job → agente → interface
```

Nenhuma camada pode definir silenciosamente campos ou estados não existentes no contrato aprovado.

## Estratégia de falha

- falha de ingestão: fonte permanece registrada, processamento falha sem publicar segmento;
- falha de embedding: componente permanece aprovado, mas não entra no índice vetorial; busca textual pode operar conforme política;
- falha de retrieval: OPP recebe estado de insuficiência ou erro recuperável;
- falha de modelo: retry limitado e auditado; depois falha explícita;
- falha de gate: produto permanece rejeitado ou em revisão;
- falha de entrega: produto validado não é perdido; entrega pode ser repetida idempotentemente.

## Decisões propostas

- **ADR-017:** implementação em ondas verticais com gates cumulativos.
- **ADR-018:** ingestão e preparação assíncronas; solicitação e entrega predominantemente síncronas no MVP.
- **ADR-019:** contratos compartilhados precedem persistência e APIs.

Status: propostas, aguardando aprovação do Marco 003.
