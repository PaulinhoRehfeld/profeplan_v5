# Perfil Técnico — Sócrates 2

## Status

Proposta do Marco 003. Complementa o perfil pedagógico aprovado; não substitui sua identidade nem seus limites.

## Princípio de implementação

Sócrates 2 não será uma aplicação, banco ou classe totalmente independente. Será um perfil versionado executado pelo runtime comum de agentes, com políticas, ferramentas e contratos restritos.

## Identificação

- `agentCode`: `SOCRATES_2`;
- `displayName`: `Sócrates 2`;
- `subject`: `philosophy`;
- `educationStage`: `high_school`;
- `grade`: `2`;
- `defaultState`: `MG`;
- `status`: controlado por feature flag;
- `profileVersion`: obrigatório;
- `promptPolicyVersion`: obrigatório;
- `knowledgeScopeVersion`: obrigatório.

## Produtos permitidos

- plano de aula;
- texto didático;
- atividade reflexiva;
- avaliação formativa curta;
- pacote integrado, apenas como Should.

## Política de conhecimento

### Filtros obrigatórios

- Filosofia;
- Ensino Médio;
- 2º ano;
- pacote curricular MG ativo;
- componente aprovado;
- versão corrente ou explicitamente selecionada;
- fonte elegível;
- finalidade compatível com o produto.

### Bloqueios

- Rio Grande do Sul;
- outros Estados;
- outros componentes;
- 1º ou 3º ano;
- Fundamental II;
- fontes desconhecidas/bloqueadas;
- segmentos brutos como contexto padrão;
- componentes em draft/review/rejected/superseded;
- dados privados de outro tenant.

### Acesso complementar

Interdisciplinaridade não significa consulta global. No MVP, um componente complementar só entra quando:

- estiver explicitamente classificado como apoio à Filosofia do 2º ano;
- tiver vínculo e finalidade aprovados;
- passar pelos mesmos filtros de licença e status;
- a OPP ou QueryPlan justificar;
- o evento registrar o motivo.

Não há chamada a outro agente disciplinar no fluxo padrão do MVP.

## Ferramentas lógicas permitidas

- validar OPP;
- resolver pacote curricular;
- construir QueryPlan;
- recuperar componentes;
- avaliar suficiência;
- montar CompositionPlan;
- chamar geração por ModelPolicy;
- executar quality pipeline;
- montar DeliveryContract;
- registrar eventos e métricas.

## Ferramentas proibidas

- consulta SQL livre;
- acesso direto a bucket de fontes;
- alteração de licença;
- aprovação de componente;
- ativação curricular;
- modificação de RLS;
- seleção arbitrária de modelo;
- acesso a credenciais;
- entrega que contorne gates.

## Entrada

Sócrates 2 recebe uma OPP validada, não texto livre cru sem contrato.

Campos mínimos:

- tipo de produto;
- tema;
- etapa/ano/componente;
- Estado/pacote;
- duração quando aplicável;
- contexto funcional;
- requisitos inclusivos;
- preferências permitidas.

## Saída intermediária

### CompositionPlan

Não representa raciocínio privado. É um plano operacional auditável:

- objetivo;
- estrutura do produto;
- IDs de componentes selecionados;
- papel de cada componente;
- nós curriculares;
- estratégia metodológica;
- avaliação prevista;
- requisitos inclusivos;
- orçamento;
- avisos.

## Saída final

Somente payload compatível com o DeliveryContract. Texto livre fora do schema é tratado como falha de formato.

## Runtime

O runtime comum deve fornecer:

- registry;
- feature flags;
- ModelPolicy;
- retry controlado;
- correlation ID;
- observabilidade;
- cancellation/timeout;
- quality pipeline;
- rollback para fluxo anterior, quando aplicável;
- injeção de dependências testáveis.

## Relação com o agente de Filosofia existente

A implementação atual de `AgentFilosofia` é candidata à reutilização, porém deverá ser avaliada quanto a:

- especialização por ano;
- pacote estadual;
- acesso por componentes, não prompt amplo;
- saída estruturada por produto;
- integração com OPP;
- ModelPolicy;
- gates novos;
- ausência de conhecimento hardcoded conflitante;
- testes existentes.

Estratégias possíveis:

1. adicionar perfil `SOCRATES_2` ao agente de Filosofia existente;
2. criar adapter do agente existente para o novo runtime/contratos;
3. substituir apenas partes incompatíveis.

Não criar `AgentFilosofiaMG2`, `AgentFilosofiaRS2` etc.

## Feature flags

Flags mínimas propostas:

- `knowledge_factory_enabled`;
- `socrates_2_enabled`;
- `hybrid_retrieval_enabled`;
- `reranker_enabled`;
- `new_quality_pipeline_enabled`;
- `pilot_group_percentage` ou lista controlada;
- `baseline_comparison_enabled`.

Flags não substituem autorização; somente controlam rollout.

## Política de modelos

Sócrates 2 referencia finalidades:

- `query_embedding`;
- `product_generation`;
- `validation_assistance`;
- `reranking`, se aprovado.

O perfil não fixa provider/modelo. A ModelPolicy resolve configuração vigente e registra a escolha.

## Timeout e retry

- timeout por etapa;
- retry somente em falha transitória ou output corrigível;
- limite configurável;
- sem retry para ausência de base, licença ou escopo;
- cada tentativa preservada;
- custo cumulativo registrado.

## Fallbacks

- fora do escopo: recusa funcional e roteamento futuro, não improvisação;
- currículo ausente: bloqueio;
- conhecimento insuficiente: retorno útil de insuficiência;
- vetor indisponível: modo lexical permitido se política e qualidade aceitarem;
- modelo indisponível: fallback permitido apenas pela ModelPolicy;
- gate falho: revisão/rejeição.

## Testes específicos

- pedido válido;
- outro ano;
- outra disciplina;
- MG versus RS;
- fonte bloqueada;
- componente draft;
- oito componentes;
- insuficiência;
- produto por tipo;
- contexto inclusivo;
- output inválido;
- gate falho;
- feature flag desligada;
- rollback;
- comparação baseline.

## Decisão proposta

**ADR-026 — Sócrates 2 é um perfil versionado sobre o runtime comum de agentes, com políticas de conhecimento e produto, não uma implementação duplicada por Estado/ano.**

Status: proposta, aguardando aprovação.
