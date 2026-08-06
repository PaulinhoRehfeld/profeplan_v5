# Plano Técnico de Testes, Fixtures, Casos Dourados e Baseline

## Status

Proposta do Marco 003. Complementa a matriz de aceite e os casos de falha aprovados no Marco 002.

## Pirâmide de testes

### 1. Contratos

- schemas válidos e inválidos;
- enums;
- transições de estado;
- compatibilidade de versões;
- serialização;
- idempotência.

### 2. Domínio

- elegibilidade de fonte;
- aprovação de componente;
- vínculo curricular;
- política de agente;
- máquina de estados da OPP;
- suficiência;
- decisão de gates.

### 3. Persistência e RLS

- repositórios;
- transações;
- concorrência;
- tenant isolation;
- papéis;
- service role;
- auditoria;
- rollback.

### 4. Serviços

- ingestão;
- retrieval;
- geração;
- validação;
- entrega;
- falhas de dependência;
- timeouts e retries.

### 5. Integração

- fonte → segmento → componente;
- componente → currículo → índice;
- OPP → retrieval → geração;
- geração → gates → entrega;
- revogação de fonte → inelegibilidade;
- atualização de componente → reindexação.

### 6. E2E do MVP

- quatro tipos de produto;
- oito temas;
- casos inclusivos;
- insuficiência;
- fora de escopo;
- baseline genérico;
- rollback por feature flag.

## Fixtures

### Fontes

- `source_wrtech_owned_valid`;
- `source_official_curriculum_mg`;
- `source_open_with_attribution`;
- `source_licensed_valid`;
- `source_unknown_license`;
- `source_blocked`;
- `source_suspended_after_use`;
- `source_duplicate_checksum`;
- `source_new_version`.

Todas as fixtures usam conteúdo sintético ou autorizado. Nenhum livro real protegido é incluído no repositório de testes.

### Segmentos

- capítulo/seção válidos;
- conceito;
- explicação;
- exemplo;
- atividade que não pode virar componente diretamente;
- baixa confiança;
- localização ausente;
- prompt injection textual;
- segmento duplicado.

### Componentes

- sete tipos mínimos;
- aprovado;
- draft;
- rejected;
- superseded;
- bloqueado por fonte;
- sem evidência;
- duplicado;
- divergência filosófica legítima;
- hard negative de outra disciplina/ano/Estado.

### Currículo

- pacote MG ativo;
- pacote MG expirado;
- pacote RS bloqueado;
- nós com e sem código;
- vínculo aprovado;
- vínculo sugerido não aprovado;
- tema sem vínculo.

### OPP

- uma válida por produto;
- campos ausentes;
- outro ano;
- outra disciplina;
- RS;
- duração incompatível;
- necessidade inclusiva funcional;
- dado pessoal excessivo;
- chave idempotente repetida.

## Casos dourados pedagógicos

Distribuição mínima:

| Tema | Plano | Texto | Atividade | Avaliação |
|---|---:|---:|---:|---:|
| ética e moral | 2 | 2 | 2 | 2 |
| liberdade e responsabilidade | 2 | 2 | 2 | 2 |
| conhecimento, verdade e opinião | 2 | 2 | 2 | 2 |
| política, poder e cidadania | 2 | 2 | 2 | 2 |
| ciência e senso comum | 2 | 2 | 2 | 2 |
| fé e razão | 2 | 2 | 2 | 2 |
| identidade e existência | 2 | 2 | 2 | 2 |
| tecnologia, ética e sociedade | 2 | 2 | 2 | 2 |

Isso produz 64 combinações-base; o dataset poderá usar subconjunto balanceado no início, preservando cobertura.

Cada caso contém:

- pedido realista;
- OPP esperada;
- pacote curricular esperado;
- componentes essenciais/aceitáveis/proibidos;
- resultado mínimo esperado;
- erros fatais;
- rubrica;
- revisão humana;
- versão.

## Rubrica pedagógica

Dimensões propostas, sem compensar gates fatais:

- correção filosófica;
- alinhamento curricular;
- adequação ao 2º ano;
- coerência pedagógica;
- clareza;
- viabilidade;
- profundidade;
- criatividade funcional;
- inclusão;
- autoria;
- utilidade ao professor.

Escala de quatro ou cinco níveis deverá ter descritores observáveis, evitando nota intuitiva isolada.

## Baseline genérico

### Objetivo

Demonstrar se a arquitetura especializada acrescenta valor suficiente.

### Controle

- mesmo pedido;
- mesma versão do pedido;
- mesmo modelo, quando possível;
- mesma janela temporal;
- sem acesso ao almoxarifado especializado;
- currículo mínimo equivalente explicitamente definido;
- temperatura e limite de saída comparáveis;
- ordem das respostas randomizada na avaliação humana.

### Comparações

- preferência cega;
- nota por dimensão;
- erros fatais;
- edição necessária;
- tokens;
- custo;
- latência;
- rastreabilidade;
- consistência entre execuções.

### Proibição

Não enfraquecer artificialmente o baseline com prompt ruim. A comparação deve ser justa.

## Testes de retrieval

- dataset de 80–120 consultas;
- lexical, semântico e híbrido;
- hard negatives;
- Recall@k, Precision@k, MRR e nDCG;
- falsos suficientes;
- filtros com alvo zero de vazamento;
- orçamento de 3, 5 e 8 componentes;
- chunks brutos versus componentes.

## Testes de validadores

Para cada gate:

- positivos claros;
- negativos claros;
- casos limítrofes;
- erro do próprio validador;
- concordância humana;
- falso positivo;
- falso negativo;
- custo e latência;
- versão.

## Testes de falha

Integrar os 50 casos do documento aprovado, incluindo:

- fonte proibida;
- currículo errado;
- agente errado;
- RLS;
- insuficiência;
- provider indisponível;
- timeout;
- retry;
- gate crítico;
- entrega indevida;
- auditoria ausente;
- revogação posterior.

## Testes não funcionais

### Segurança

- tenant isolation;
- manipulação de IDs;
- prompt injection;
- exfiltração;
- segredo em log;
- abuso de service role.

### Performance

- p50/p95 por etapa;
- concorrência limitada do piloto;
- corpus 100, 300 e expansão simulada;
- reindexação;
- carga de avaliações em lote.

### Resiliência

- banco indisponível;
- embedding indisponível;
- modelo indisponível;
- resposta inválida;
- job duplicado;
- interrupção entre etapas;
- rollback de feature flag.

### Acessibilidade

Quando houver interface mínima:

- teclado;
- leitor de tela;
- labels;
- estados de erro;
- contraste;
- linguagem clara;
- responsividade.

## Ambientes

- unitário: sem serviços externos;
- integração: banco isolado e fixtures;
- experimento: corpus congelado e configuração versionada;
- homologação: dados fictícios e fontes autorizadas;
- produção piloto: feature flag e grupo controlado.

## Evidências de conclusão

Cada Story Done registra:

- testes executados;
- resultado;
- versão dos fixtures;
- coverage relevante;
- métricas;
- logs/trace de exemplo minimizado;
- limitações;
- decisão humana quando exigida.

## Critérios para piloto inconclusivo

- amostra insuficiente;
- baseline injusto;
- corpus não equilibrado;
- alteração de modelo durante comparação;
- falhas técnicas dominam a avaliação;
- baixa concordância sem resolução;
- dados excluídos sem justificativa;
- custo ou latência não registrados.

## Decisão proposta

**ADR-025 — O piloto usa casos dourados versionados, baseline justo e avaliação pareada; resultado sem controle suficiente é inconclusivo, não aprovado.**

Status: proposta, aguardando aprovação.
