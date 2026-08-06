# Contrato Técnico de Pacote Curricular

## Status

Proposta do Marco 003. Especializa o padrão curricular aprovado para implementação, sem criar schema físico.

## Objetivo

Permitir que o mesmo agente disciplinar opere com pacotes estaduais versionados, carregando somente o recorte aplicável ao pedido.

No MVP, apenas o pacote MG de Filosofia do 2º ano do Ensino Médio pode ficar ativo.

## CurriculumPackage

Campos mínimos:

| Campo | Regra |
|---|---|
| `id` | identificador imutável |
| `schemaVersion` | versão do contrato |
| `country` | `BR` no MVP |
| `state` | `MG` no MVP |
| `stage` | `high_school` |
| `grade` | `2` |
| `subject` | `philosophy` |
| `versionLabel` | identificador legível |
| `effectiveFrom` | início da vigência |
| `effectiveTo` | opcional |
| `status` | ciclo de vida controlado |
| `sourceVersionIds` | procedência oficial |
| `createdAt` | UTC |
| `approvedBy` e `approvedAt` | obrigatórios para ativação |

Status:

- `draft`;
- `in_review`;
- `active`;
- `superseded`;
- `suspended`;
- `retired`.

Invariantes:

- só um pacote principal pode estar ativo para a mesma combinação Estado/etapa/ano/componente em uma data;
- pacote RS não pode ser ativado no MVP;
- alteração do conteúdo curricular produz nova versão;
- produto histórico preserva o pacote e a versão utilizados;
- pacote inativo exige seleção administrativa explícita e nunca é padrão.

## CurriculumNode

Representa uma unidade consultável do pacote.

Campos:

- `id`;
- `packageId`;
- `parentNodeId`;
- `nodeType`;
- `officialCode`;
- `title`;
- `description`;
- `sequence`;
- `metadata`;
- `sourceLocation`;
- `status`.

`nodeType` mínimo:

- `area_competency`;
- `specific_competency`;
- `skill`;
- `learning_objective`;
- `knowledge_object`;
- `thematic_axis`;
- `guidance`;
- `period_reference`.

Regras:

- códigos oficiais são preservados sem fabricação de equivalências;
- ausência de código não invalida um nó quando o documento não o fornece;
- hierarquia e sequência devem ser reconstruíveis;
- texto oficial permanece distinguível de síntese interna.

## ComponentCurriculumLink

Relaciona uma versão de componente a um nó curricular.

Campos:

- `id`;
- `componentVersionId`;
- `curriculumNodeId`;
- `linkType`;
- `confidence`;
- `rationale`;
- `origin`;
- `reviewStatus`;
- `reviewedBy`;
- `reviewedAt`.

`linkType`:

- `direct`;
- `supporting`;
- `prerequisite`;
- `extension`;
- `assessment_evidence`.

`origin`:

- `human`;
- `rule_based`;
- `model_suggestion`.

Regras:

- sugestão de modelo não equivale a vínculo aprovado;
- retrieval curricular padrão usa apenas links aprovados;
- a justificativa é obrigatória para `direct` e `assessment_evidence`;
- o vínculo não altera o texto oficial do nó;
- um componente pode ter vários vínculos pedagogicamente justificados.

## CurriculumScope

Objeto calculado para uma OPP:

- `packageId`;
- `state`;
- `stage`;
- `grade`;
- `subject`;
- `effectiveDate`;
- `includedNodeIds`;
- `excludedNodeTypes`;
- `resolutionReason`;
- `resolvedAt`.

A resolução deve ser determinística. O agente não escolhe livremente o Estado ou ano.

## API lógica

### `resolveCurriculumPackage(input)`

Entrada:

- Estado;
- etapa;
- ano;
- componente;
- data de referência;
- versão explícita opcional.

Saída:

- pacote resolvido;
- motivo da resolução;
- avisos;
- falha tipada quando não houver pacote válido.

### `getCurriculumScope(input)`

Entrada:

- pacote;
- tema;
- tipo de produto;
- nós explicitamente solicitados.

Saída:

- escopo pequeno e rastreável;
- nós incluídos;
- evidência de origem;
- sinal de insuficiência.

### `validateCurriculumAlignment(input)`

Entrada:

- OPP;
- contrato de entrega;
- nós utilizados.

Saída:

- `pass`, `fail` ou `review`;
- achados estruturados;
- códigos e referências envolvidos;
- versão do validador.

## Compatibilidade com `industry-curriculum`

O pacote existente é candidato à reutilização para:

- parsing e ingestão de BNCC/CRMG;
- tipos curriculares;
- mecanismos de busca;
- scripts de carga;
- funções de mapeamento.

A reutilização exige verificar:

- se a versão oficial está registrada;
- se o recorte Filosofia/2º ano é confiável;
- se a procedência chega até o nó;
- se sugestões e vínculos aprovados estão separados;
- se a busca não mistura versões;
- se o contrato aceita pacote estadual futuro sem duplicar agente.

## Testes obrigatórios

- resolve MG válido;
- rejeita RS no MVP;
- rejeita outro ano;
- não escolhe pacote expirado como padrão;
- mantém códigos oficiais;
- preserva versão em produto histórico;
- impede vínculo sugerido não revisado no retrieval padrão;
- sinaliza tema sem nó ou vínculo suficiente.

## Fora do MVP

- modo comparativo MG/RS;
- composição entre vários Estados;
- atualização automática sem revisão;
- interface completa de gestão curricular;
- inferência de equivalências interestaduais.
