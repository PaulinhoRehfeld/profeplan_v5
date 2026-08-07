# Contratos Técnicos de Validação

## Status

Proposta do Marco 003. Alinha os quality gates existentes aos gates não compensatórios aprovados no Marco 002.

## Princípio

Um texto convincente não é produto aprovado. A aprovação depende de gates estruturados, versionados e auditáveis.

## ValidationRun

Campos mínimos:

- `id`;
- `oppId`;
- `generationRunId`;
- `productVersionId`;
- `pipelineVersion`;
- `requiredGateIds`;
- `status`;
- `startedAt`;
- `completedAt`;
- `summary`;
- `decision`;
- `decidedByPolicyVersion`.

Status:

- `pending`;
- `running`;
- `passed`;
- `failed`;
- `review_required`;
- `error`.

## ValidationFinding

Campos:

- `id`;
- `validationRunId`;
- `gateId`;
- `gateVersion`;
- `severity`;
- `code`;
- `message`;
- `location`;
- `evidenceRefs`;
- `suggestedAction`;
- `status`;
- `createdAt`.

Severidade:

- `info`;
- `warning`;
- `error`;
- `critical`.

## Resultado de gate

Cada gate retorna:

- `pass`;
- `fail`;
- `review`;
- `error`;
- achados estruturados;
- versão;
- duração;
- dados de entrada referenciados por ID/hash;
- justificativa.

`error` em gate Must não equivale a `pass`; bloqueia aprovação.

## Gates do MVP

### G1 — ContractFormatGate

Verifica:

- schema do produto;
- campos obrigatórios;
- tipos;
- separação professor/estudante;
- consistência de enum;
- versão do contrato.

Falhas críticas:

- JSON inválido;
- campo obrigatório ausente;
- conteúdo fora do payload permitido;
- tentativa de incluir dados técnicos no produto.

Candidato à reutilização: `FormatValidator`, após adaptação ao contrato novo.

### G2 — ScopeAndRoutingGate

Verifica:

- Filosofia;
- Ensino Médio;
- 2º ano;
- MG;
- produto permitido;
- perfil Sócrates 2;
- ausência de expansão indevida.

Falha é não compensatória.

### G3 — CurriculumAlignmentGate

Verifica:

- pacote e versão;
- nós curriculares utilizados;
- objetivo e conteúdo;
- atividade e avaliação;
- inexistência de código inventado;
- vínculo revisado.

Candidato à reutilização: `BNCCValidator`, com contrato de pacote versionado.

### G4 — KnowledgeProvenanceGate

Verifica:

- componentes usados;
- versões aprovadas;
- evidências autorizadas;
- fontes ativas;
- atribuição necessária;
- ausência de segmento bruto proibido.

Nova capacidade obrigatória.

### G5 — PhilosophicalAccuracyGate

Verifica:

- correção conceitual;
- distinção de autores e tradições;
- ausência de anacronismo relevante;
- separação entre posição filosófica e fato;
- adequação ao 2º ano;
- tratamento de divergências.

Pode combinar regras, avaliação por modelo e revisão humana. Nenhum método isolado é garantia.

### G6 — PedagogicalQualityGate

Verifica:

- objetivo claro;
- coerência objetivo–atividade–avaliação;
- viabilidade temporal;
- instruções executáveis;
- adequação da carga cognitiva;
- utilidade ao professor;
- nível de leitura.

Candidato à reutilização: `ContentScorer`, após calibração com avaliação humana.

### G7 — InclusionAccessibilityGate

Verifica requisitos informados na OPP e mínimos do produto:

- instruções em etapas;
- alternativas de participação quando solicitadas;
- linguagem e estrutura;
- orientação funcional, sem diagnóstico inventado;
- ausência de exclusão ou estigmatização.

Candidato à reutilização: `PDIGuardian`, reduzido ao contrato do MVP.

### G8 — PrivacySecurityGate

Verifica:

- dados pessoais desnecessários;
- prompt injection ou instrução vinda da fonte;
- segredo técnico;
- conteúdo interno;
- vazamento entre tenant;
- texto protegido exposto.

Candidato à reutilização: `PrivacyGuard`, ampliado.

### G9 — AuthorialIntegrityGate

Verifica:

- sobreposição lexical com fontes;
- sequência estrutural excessivamente próxima;
- reprodução de atividade/questão;
- atribuição;
- diversidade de contribuições;
- originalidade funcional.

Candidato parcial: `AntiPlagiarismScorer`; deverá comparar também com fontes recuperadas, não apenas produtos anteriores.

### G10 — GroundingAndSufficiencyGate

Verifica:

- context package suficiente;
- afirmações centrais sustentadas;
- ausência de preenchimento silencioso;
- consistência com as evidências;
- tratamento de incerteza.

Candidato parcial: `HallucinationDetector`, após calibragem.

### G11 — ProductSpecificGate

Por produto:

- plano: etapas e tempos somam de forma viável;
- texto: progressão e conceitos;
- atividade: comandos e produto esperado;
- avaliação: habilidade, item, critério e gabarito;
- pacote: coerência entre peças.

### G12 — TraceabilityGate

Verifica:

- OPP;
- QueryPlan;
- retrieval run;
- componentes e versões;
- pacote curricular;
- generation run;
- modelos e prompts;
- validation run;
- contrato de entrega.

Nova capacidade obrigatória.

## Política de decisão

### Aprovação

Somente quando:

- todos os gates Must retornam `pass`;
- nenhum achado crítico está aberto;
- warnings permitidos estão registrados;
- contrato de entrega é válido;
- rastreabilidade está completa.

### Revisão

Quando:

- gate explicitamente permite julgamento humano;
- conflito filosófico legítimo exige decisão;
- similaridade autoral está em faixa intermediária;
- alinhamento curricular é plausível, mas não confirmado.

### Reprovação

Quando:

- qualquer gate Must falha;
- fonte ou licença inválida;
- conteúdo fora do escopo;
- erro filosófico relevante;
- vazamento de dado;
- reprodução indevida;
- rastreabilidade incompleta.

## Retry

Retry automático somente para falhas potencialmente corrigíveis:

- schema incompleto;
- formatação;
- instrução não atendida;
- pequenas inconsistências.

Não usar retry para:

- falta de fonte;
- licença bloqueada;
- pacote curricular ausente;
- pedido fora de escopo;
- vazamento de segurança;
- erro repetido após limite.

Cada retry:

- cria nova tentativa;
- registra motivo;
- tem limite;
- preserva output anterior;
- contabiliza custo.

## Avaliação dos validadores existentes

Antes de reutilizar, cada validador atual deverá passar por:

- inventário de entradas/saídas;
- testes com casos dourados;
- precisão e recall em casos de falha;
- taxa de falso positivo;
- taxa de falso negativo;
- custo e latência;
- revisão de tratamento de dados;
- compatibilidade com Findings estruturados.

## Métricas

- taxa de aprovação;
- taxa de revisão;
- falhas por gate;
- falso negativo crítico;
- falso positivo;
- retries por produto;
- custo de validação;
- latência p50/p95;
- concordância com revisão humana;
- incidentes evitados.

## Testes obrigatórios

- um caso positivo por produto;
- um caso negativo por gate;
- gate em erro;
- achados múltiplos;
- retry permitido;
- retry proibido;
- produto tecnicamente válido, mas filosoficamente errado;
- produto criativo, mas sem fonte;
- produto alinhado, mas copiado;
- produto bom, mas com dado pessoal;
- rastreabilidade quebrada;
- validador antigo discordando do julgamento humano.

## Decisão proposta

**ADR-023 — O pipeline de qualidade usa gates estruturados e não compensatórios; validadores existentes só serão reutilizados após avaliação contra casos dourados.**

Status: proposta, aguardando aprovação.
