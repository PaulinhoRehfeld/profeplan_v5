# Mapa de dependências — MVP Sócrates 2

## Objetivo

Organizar a ordem lógica de execução e impedir que o Codex implemente geração, busca ou agentes antes das capacidades que garantem segurança, currículo e rastreabilidade.

## Cadeia crítica

```mermaid
flowchart TD
    A[F-001.1 Baseline] --> B[F-001.2 DoR e DoD]
    A --> C[F-002.1 Registro de fonte]
    C --> D[F-002.2 Autorização]
    D --> E[F-003.1 Ingestão]
    E --> F[F-003.2 Estrutura]
    F --> G[F-004.1 Esquema de componente]
    G --> H[F-004.2 Tipologia]
    G --> I[F-004.3 Revisão e versão]
    D --> J[F-005.1 Destilação]
    G --> J
    J --> K[F-005.2 Deduplicação]
    A --> L[F-006.1 Currículo MG]
    I --> M[F-006.2 Vínculo curricular]
    L --> M
    D --> N[F-007.1 Filtros]
    I --> N
    M --> N
    N --> O[F-007.2 Busca híbrida]
    O --> P[F-007.3 Suficiência]
    L --> Q[F-008.1 Roteamento]
    N --> Q
    Q --> R[F-009.1 Perfil Sócrates 2]
    Q --> S[F-010.1 OPP]
    R --> T[F-009.2 Produtos mínimos]
    P --> T
    S --> U[F-011.1 Plano de composição]
    O --> U
    U --> V[F-011.2 Personalização]
    T --> W[F-012.1 Gate curricular]
    V --> X[F-012.2 Gate pedagógico]
    J --> Y[F-013.1 Gate autoral]
    T --> Y
    S --> Z[F-014.1 Requisitos inclusivos]
    T --> AA[F-014.2 Gate inclusivo]
    Z --> AA
    W --> AB[F-015.1 Contrato de entrega]
    X --> AB
    Y --> AC[F-013.2 Linhagem]
    AC --> AB
    AA --> AB
    S --> AD[F-010.2 Auditoria da OPP]
    Q --> AE[F-008.2 Validadores]
    AE --> AD
    AD --> AF[F-016.1 Telemetria]
    AF --> AG[F-016.2 Tokens e custo]
    AB --> AH[F-017.1 Casos dourados]
    AG --> AH
    AH --> AI[F-017.2 Decisão]
    AI -. aprovação .-> AJ[EPIC-018 Expansão]
```

## Ondas recomendadas

### Onda 0 — Contratos e governança

- F-001.1;
- F-001.2;
- contratos documentais das fontes, componentes, currículo, OPP e entrega.

**Saída:** backlog implementável sem lacunas conceituais.

### Onda 1 — Fontes e componentes

- F-002.1 e F-002.2;
- F-003.1 e F-003.2;
- F-004.1, F-004.2 e F-004.3;
- F-005.1 e F-005.2.

**Saída:** pequeno estoque revisado, autorizado e rastreável.

### Onda 2 — Currículo e recuperação

- F-006.1 e F-006.2;
- F-007.1, F-007.2 e F-007.3.

**Saída:** recuperação restrita, híbrida e capaz de reconhecer insuficiência.

### Onda 3 — Roteamento, agente e OPP

- F-008.1;
- F-009.1;
- F-010.1;
- F-008.2;
- F-010.2.

**Saída:** pedido válido convertido em fluxo auditável do Sócrates 2.

### Onda 4 — Produção

- F-009.2;
- F-011.1;
- F-011.2.

**Saída:** quatro produtos mínimos geráveis com personalização básica.

### Onda 5 — Gates e contrato

- F-012.1 e F-012.2;
- F-013.1 e F-013.2;
- F-014.1 e F-014.2;
- F-015.1.

**Saída:** produto validado, rastreável e entregue em contrato estruturado.

### Onda 6 — Evidência e decisão

- F-016.1 e F-016.2;
- F-017.1 e F-017.2.

**Saída:** comparação com baseline e decisão formal.

### Onda opcional — Should

- F-009.3;
- F-011.3;
- F-012.3;
- F-015.2.

Somente após estabilidade das Must correspondentes.

## Bloqueios explícitos

- não implementar busca vetorial antes dos filtros obrigatórios;
- não publicar componentes antes de revisão e autorização;
- não gerar produtos antes de roteamento e OPP válidos;
- não entregar produto aprovado sem os gates Must;
- não comparar custos sem telemetria identificável;
- não iniciar RS ou novos agentes antes da US-017.2;
- não usar interface visual como substituta de contratos e critérios de aceite.

## Dependências externas ainda não fechadas

- fontes exatas juridicamente utilizáveis;
- versão oficial do recorte curricular MG;
- professores avaliadores;
- modelo ou modelos usados no benchmark;
- preços usados para cálculo de custo;
- limiares experimentais de relevância e similaridade.

Essas dependências devem estar resolvidas na Story que as utilizar, conforme a Definition of Ready.
