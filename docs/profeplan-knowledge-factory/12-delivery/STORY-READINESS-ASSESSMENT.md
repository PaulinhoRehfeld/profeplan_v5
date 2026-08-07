# Avaliação de Prontidão das User Stories

## Status

Proposta do Marco 003. `Ready` nesta avaliação significa que a documentação e os critérios estão suficientemente definidos; não autoriza código antes dos gates globais.

## Gates globais que bloqueiam todo código

- Marco 003 não aprovado;
- repositório canônico não decidido;
- documentação não sincronizada no repositório de implementação;
- branch base e baseline de CI não confirmados;
- primeiro lote não autorizado.

Enquanto esses gates existirem, nenhuma Story é `Ready for Code`, mesmo que esteja `Ready de domínio`.

## Categorias

- **Ready de domínio:** requisitos e contratos suficientes para detalhamento técnico/primeiro lote.
- **Ready condicional:** ficará Ready após dependência explícita já mapeada.
- **Blocked — evidência/fonte:** depende de fontes autorizadas, corpus ou revisão.
- **Blocked — experimento:** decisão técnica depende de benchmark.
- **Blocked — infraestrutura:** depende de persistência, RLS ou runtime anterior.
- **Blocked — fluxo completo:** depende de ondas posteriores.
- **Won't:** proibida no MVP.

## Avaliação por Story

| Story | Estado Marco 003 | Bloqueio ou próximo gate |
|---|---|---|
| US-001.1 | Ready de domínio | sincronizar baseline no repositório canônico |
| US-001.2 | Ready de domínio | integrar DoR/DoD ao fluxo de PR |
| US-002.1 | Ready de domínio | decisão de repositório e contrato em código |
| US-002.2 | Ready de domínio | validação jurídica dos valores e papéis finais |
| US-003.1 | Blocked — evidência/fonte | selecionar fonte piloto autorizada e processo de revisão |
| US-003.2 | Ready condicional | contrato de segmento + ferramenta de ingestão do Lote 4 |
| US-004.1 | Ready de domínio | contratos e repositório abstrato |
| US-004.2 | Ready de domínio | validar sete tipos com curadoria do piloto |
| US-004.3 | Ready condicional | persistência, concorrência e papéis de revisão |
| US-005.1 | Blocked — evidência/fonte | fonte piloto, rubrica autoral e revisão humana |
| US-005.2 | Blocked — experimento | corpus inicial e candidatos de similaridade |
| US-006.1 | Ready condicional | inventário e validação do recorte curricular oficial MG |
| US-006.2 | Ready condicional | componentes piloto + fluxo de revisão de vínculo |
| US-007.1 | Ready condicional | persistência elegível, pacote MG e política de agente |
| US-007.2 | Blocked — experimento | dataset, embeddings, fusão e benchmark |
| US-007.3 | Ready condicional | calibrar suficiência no dataset de retrieval |
| US-008.1 | Blocked — infraestrutura | OPP, AgentProfile e filtros implementados |
| US-008.2 | Blocked — fluxo completo | quality pipeline adaptado e OPP |
| US-009.1 | Ready condicional | avaliar AgentFilosofia existente e implementar profile |
| US-009.2 | Blocked — fluxo completo | retrieval, OPP, geração e gates |
| US-009.3 | Blocked — fluxo completo | quatro produtos individuais estáveis |
| US-010.1 | Ready de domínio | contratos + serviço/persistência em lotes posteriores |
| US-010.2 | Ready condicional | event store lógico/persistência/observabilidade |
| US-011.1 | Ready condicional | ContextPackage e um produto definido |
| US-011.2 | Blocked — fluxo completo | geração funcional e fixtures de contexto |
| US-011.3 | Blocked — fluxo completo | produto base aprovado; prioridade Should |
| US-012.1 | Ready condicional | casos dourados e adaptação dos validadores |
| US-012.2 | Ready condicional | rubrica e produtos estruturados |
| US-012.3 | Blocked — fluxo completo | amostra de produtos e docentes avaliadores |
| US-013.1 | Blocked — experimento | fontes autorizadas, thresholds e corpus |
| US-013.2 | Ready condicional | entidades persistidas e lineage end-to-end |
| US-014.1 | Ready de domínio | contrato e revisão de minimização |
| US-014.2 | Ready condicional | produtos e casos inclusivos dourados |
| US-015.1 | Ready de domínio | contrato implementado; entrega depende de gates |
| US-015.2 | Ready condicional | contrato de hints; Should, não bloqueia MVP central |
| US-016.1 | Ready de domínio | adaptar observabilidade existente desde o Lote 1/2 |
| US-016.2 | Ready condicional | ModelPolicy, dados reais de provider e tabela versionada |
| US-017.1 | Blocked — fluxo completo | pipeline completo, baseline e dataset congelado |
| US-017.2 | Blocked — fluxo completo | resultados do piloto e decisão humana |
| US-018.1 | Won't | bloqueada até aprovação explícita da US-017.2 |

## Stories candidatas ao primeiro ciclo

Após os gates globais, as primeiras Stories que podem sustentar trabalho técnico são:

- US-001.1;
- US-001.2;
- US-002.1;
- US-002.2;
- US-004.1;
- US-004.2;
- US-010.1;
- US-014.1;
- US-015.1;
- US-016.1.

Isso não significa concluí-las integralmente no primeiro PR. O primeiro PR entrega os contratos e invariantes necessários.

## Evidências necessárias para promover Stories

### Fonte e ingestão

- fonte selecionada;
- licença/permissão documentada;
- arquivo/versão disponível;
- responsável pela revisão;
- fixture ou amostra segura.

### Currículo

- documento oficial e versão;
- recorte validado;
- responsável curricular;
- códigos e nomenclatura confirmados.

### Retrieval

- corpus congelado;
- dataset de consultas;
- julgamentos;
- candidatos técnicos;
- métricas e critérios.

### Agente/gates

- perfil implementado;
- casos dourados;
- validadores avaliados;
- ModelPolicy;
- output schema.

### Piloto

- grupo de professores;
- consentimento e fluxo de feedback;
- baseline;
- rubrica;
- política de exclusão;
- decisão executiva.

## Regra de mudança de estado

Toda promoção para `Ready for Code` deverá registrar:

- data;
- responsável;
- versão da Story;
- dependências concluídas;
- documentos lidos;
- arquivos/módulos alvo;
- testes;
- riscos;
- PR/lote autorizado.

O Codex não decide sozinho que uma Story está Ready.
