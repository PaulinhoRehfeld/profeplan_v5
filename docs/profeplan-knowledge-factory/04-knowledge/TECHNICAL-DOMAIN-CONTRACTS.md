# Contratos Técnicos do Domínio de Conhecimento

## Status

Proposta do Marco 003. Define semântica e validações; não define tabelas físicas nem migrations.

## Regras gerais

- identificadores são imutáveis;
- alterações relevantes produzem nova versão ou evento auditável;
- datas são armazenadas em UTC;
- enums são fechados e versionados;
- todo contrato possui `schemaVersion`;
- conteúdo publicado nunca é sobrescrito silenciosamente;
- referência externa não substitui procedência interna;
- dados sensíveis não entram em embeddings;
- a estrutura física pode evoluir sem mudar a semântica do contrato.

## 1. KnowledgeSource

Representa uma obra, documento ou conjunto de conteúdo cuja utilização foi avaliada.

### Campos obrigatórios

| Campo | Tipo lógico | Regra |
|---|---|---|
| `id` | UUID/ULID | imutável |
| `schemaVersion` | string | versão do contrato |
| `title` | string | não vazio |
| `sourceType` | enum | classe controlada |
| `responsibleEntity` | string | autor, editora, órgão ou WRtech |
| `origin` | string | localização ou sistema de origem |
| `licenseClass` | enum | obrigatório |
| `generationPermission` | enum | obrigatório |
| `status` | enum | ciclo de vida |
| `createdAt` | datetime | UTC |
| `createdBy` | actor reference | auditável |

### Campos condicionais

- `edition`;
- `publicationYear`;
- `isbnOrIdentifier`;
- `pnldCycle`;
- `jurisdiction`;
- `curriculumState`;
- `effectiveFrom` e `effectiveTo`;
- `storageObjectRef`;
- `reviewNotes`.

### Enums

`sourceType`:

- `official_curriculum`;
- `legislation`;
- `pnld_student_book`;
- `pnld_teacher_manual`;
- `open_educational_resource`;
- `wrtech_owned`;
- `licensed_third_party`;
- `teacher_private_document`;
- `other`.

`licenseClass`:

- `owned`;
- `open`;
- `public_official`;
- `licensed`;
- `restricted_review_only`;
- `unknown`;
- `blocked`.

`generationPermission`:

- `allowed`;
- `allowed_with_attribution`;
- `retrieval_only`;
- `review_only`;
- `blocked`.

`status`:

- `draft`;
- `pending_legal_review`;
- `active`;
- `suspended`;
- `retired`;
- `blocked`.

### Invariantes

- `unknown` ou `blocked` não permite geração;
- `review_only` não entra em retrieval produtivo;
- fonte suspensa ou retirada não cria novos componentes;
- alteração de licença invalida elegibilidade derivada até reavaliação;
- arquivos iguais são detectados por checksum, mas podem existir como versões distintas quando a procedência justificar.

## 2. SourceVersion

Representa uma manifestação temporal e verificável da fonte.

Campos:

- `id`;
- `sourceId`;
- `versionLabel`;
- `checksum`;
- `mimeType`;
- `byteSize`;
- `pageCount`, quando aplicável;
- `storageObjectRef`;
- `extractionStatus`;
- `effectiveFrom` e `effectiveTo`;
- `createdAt`;
- `supersedesVersionId`.

Invariantes:

- checksum obrigatório antes da ingestão;
- versão usada por componente ou produto não pode ser apagada fisicamente no fluxo normal;
- nova versão não altera a evidência histórica de produtos anteriores.

## 3. SourceSegment

Representa um bloco extraído, ainda não autoral e não publicável como produto.

Campos mínimos:

- `id`;
- `sourceVersionId`;
- `sequence`;
- `segmentType`;
- `rawText` ou referência protegida;
- `normalizedText`;
- `location`;
- `parentSegmentId`;
- `extractionMethod`;
- `extractionConfidence`;
- `reviewStatus`;
- `contentHash`;
- `createdAt`.

`segmentType` mínimo:

- `chapter`;
- `section`;
- `concept`;
- `explanation`;
- `example`;
- `activity`;
- `question`;
- `teacher_guidance`;
- `caption`;
- `table`;
- `other`.

`location` pode conter:

- página inicial/final;
- capítulo;
- seção;
- bloco;
- coordenadas estruturais quando necessárias.

Invariantes:

- segmento preserva ordem e localização;
- segmento não é recuperado diretamente por Sócrates 2 no fluxo padrão;
- texto protegido permanece em camada restrita;
- baixa confiança ou estrutura ambígua exige revisão.

## 4. PedagogicalComponent

Unidade canônica semielaborada do almoxarifado.

Campos mínimos:

- `id`;
- `canonicalKey`;
- `primaryType`;
- `title`;
- `subject`;
- `educationStage`;
- `grade`;
- `themes`;
- `intendedUses`;
- `status`;
- `currentVersionId`;
- `createdAt`;
- `createdBy`.

`primaryType` mínimo do piloto:

- `concept`;
- `conceptual_relation`;
- `essential_question`;
- `context_case`;
- `teaching_strategy`;
- `assessment_pattern`;
- `inclusion_guidance`.

`intendedUses`:

- `lesson_plan`;
- `didactic_text`;
- `reflective_activity`;
- `formative_assessment`;
- `integrated_lesson_package`.

Status:

- `draft`;
- `in_review`;
- `approved`;
- `rejected`;
- `superseded`;
- `suspended`.

Invariantes:

- somente `approved` é elegível para retrieval produtivo;
- componente não contém um plano ou produto final completo;
- Filosofia/EM/2º ano é obrigatório no estoque piloto;
- mudanças de conteúdo produzem nova versão.

## 5. PedagogicalComponentVersion

Conteúdo versionado e recuperável.

Campos mínimos:

- `id`;
- `componentId`;
- `versionNumber`;
- `authorialSummary`;
- `structuredContent`;
- `searchableText`;
- `keywords`;
- `commonMisconceptions`;
- `prerequisites`;
- `qualityStatus`;
- `approvedBy`;
- `approvedAt`;
- `supersedesVersionId`;
- `contentHash`.

`structuredContent` é validado conforme o tipo e não deve virar um campo livre sem contrato.

Invariantes:

- `searchableText` deve ser derivado de campos permitidos;
- conteúdo de fonte restrita não é copiado para síntese além do permitido;
- versão aprovada exige ao menos uma evidência autorizada ou justificativa de material próprio;
- conteúdo utilizado por OPP fica referenciado pela versão exata.

## 6. ComponentSourceEvidence

Relaciona componente a contribuição verificável.

Campos:

- `id`;
- `componentVersionId`;
- `sourceVersionId`;
- `sourceSegmentId`, quando houver;
- `contributionType`;
- `location`;
- `attributionRequired`;
- `reviewStatus`;
- `reviewedBy`;
- `reviewedAt`.

`contributionType`:

- `conceptual_basis`;
- `example_inspiration`;
- `methodological_basis`;
- `curricular_basis`;
- `fact_verification`;
- `contrast_or_divergence`.

Invariantes:

- evidência bloqueada torna a versão inelegível;
- uma evidência não autoriza reprodução integral;
- remoção lógica preserva trilha de auditoria.

## 7. ComponentEmbedding

Representa uma projeção experimental ou produtiva do componente.

Campos:

- `id`;
- `componentVersionId`;
- `embeddingPurpose`;
- `provider`;
- `model`;
- `dimension`;
- `normalization`;
- `sourceTextHash`;
- `experimentId`, quando experimental;
- `status`;
- `createdAt`;
- vetor em armazenamento compatível.

Regras:

- modelo e dimensão não fazem parte do contrato canônico do componente;
- múltiplos embeddings podem coexistir durante experimento;
- embedding obsoleto não altera a versão do componente;
- mudança em `searchableText` invalida embedding anterior;
- nenhum dado pessoal ou texto não autorizado entra no vetor.

## 8. DeduplicationDecision

Campos:

- `id`;
- `candidateComponentIds`;
- `decision`;
- `canonicalComponentId`;
- `rationale`;
- `decidedBy`;
- `decidedAt`;
- `algorithmVersion`, quando houver sugestão automática.

Decisões:

- `merge`;
- `relate`;
- `keep_separate`;
- `reject_candidate`;
- `pending_review`.

## Validação de contratos

Cada contrato deverá possuir:

- schema executável na implementação;
- testes de campo obrigatório;
- testes de enum inválido;
- testes de transição de estado;
- exemplos válidos e inválidos;
- versão documentada;
- serialização estável;
- regra de compatibilidade retroativa.

## Fora do contrato do MVP

- OCR industrial;
- extração automática irrestrita;
- publicação automática sem revisão;
- componentes de outras disciplinas/anos;
- material RS;
- armazenamento físico definitivo escolhido antecipadamente;
- algoritmo definitivo de deduplicação.
