# Mapa de Capacidades Técnicas

## Status

Proposta técnica do Marco 003. O inventário indica potencial de reutilização, não certifica que cada capacidade esteja pronta para produção.

## Critérios de classificação

- **Existente e candidata à reutilização:** há código ou estrutura concreta; precisa de testes de compatibilidade.
- **Existente, mas exige adaptação:** existe implementação parcial ou com contrato diferente do MVP.
- **Estrutura criada, implementação pendente:** há pacote ou documentação, mas não há evidência suficiente de fluxo funcional completo.
- **Nova capacidade:** não foi identificada implementação compatível.
- **Fora do MVP:** existe ou pode existir, mas não deve ser ampliada nesta fase.

## Inventário

| Capacidade | Local identificado no monorepo real | Classificação | Diretriz do MVP |
|---|---|---|---|
| Monorepo TypeScript/pnpm | raiz, `apps/*`, `packages/*` | existente e candidata | reutilizar após decisão do repositório |
| Aplicação do professor | `apps/web` | existente e candidata | integração mínima somente após backend estável |
| BFF/API | `apps/bff` | existente e candidata | expor contratos síncronos da OPP e consulta |
| Banco e Prisma | `packages/db` | existente, exige adaptação | avaliar convivência com migrations Supabase |
| Supabase/PostgreSQL | `supabase/migrations` | existente e candidata | preservar padrão, revisar RLS e versionamento |
| pgvector | migration de RAG curricular | existente, exige adaptação | não reutilizar dimensão/modelo sem experimento |
| Busca textual em português | migrations de RAG curricular | existente e candidata | reutilizar padrão após benchmark |
| RAG curricular MG | `industry-curriculum` e migrations | existente, exige adaptação | recortar Filosofia, 2º ano, MG e versionar pacote |
| Agente orquestrador | `packages/agents` | existente e candidata | adaptar para OPP e escopo Sócrates 2 |
| Registro de agentes | `packages/agents` | existente e candidata | manter infraestrutura comum, não duplicar por Estado |
| Agente de Filosofia | `packages/agents/src/disciplinas` | existente, exige adaptação | especializar por perfil, ano e permissões |
| Quality gate de formato | `packages/agents/src/qualidade` | existente e candidata | alinhar ao contrato de entrega |
| Validador BNCC/currículo | `packages/agents/src/qualidade` | existente, exige adaptação | suportar pacote curricular versionado |
| Privacy guard | `packages/agents/src/qualidade` | existente e candidata | ampliar minimização e registro de incidente |
| Detector de alucinação | `packages/agents/src/qualidade` | existente, exige evidência | calibrar com casos dourados; não tratá-lo como garantia |
| Scoring pedagógico | `packages/agents/src/qualidade` | existente, exige evidência | comparar com revisão humana |
| Guardião PDI/DUA | `packages/agents/src/qualidade` | existente, exige adaptação | aplicar requisitos mínimos do MVP, sem PDI completo |
| Antiplágio | `packages/agents/src/qualidade` | existente, exige adaptação | incluir comparação com fontes recuperadas e produtos |
| Feature flags e rollback | `packages/agents` | existente e candidata | obrigatórios para piloto controlado |
| Observabilidade dos agentes | `packages/agents/src/observability.ts` | existente, exige adaptação | incorporar OPP, retrieval e custos |
| Cliente OpenAI | `packages/ai` | existente e candidata | encapsular por contrato e política de modelos |
| Prompts e geração | `packages/ai` | existente, exige adaptação | separar templates por produto e versão |
| Tipos compartilhados | `packages/types` | existente e candidata | possível local dos contratos puros |
| Pacote PNLD | `packages/industry-pnld` | estrutura criada | implementar apenas ingestão piloto assistida |
| Gráfica | `packages/graphics-profeplan` | existente, fora do escopo avançado | somente contrato estruturado e saída simples |
| Registro de procedência e licença | não identificado de forma compatível | nova capacidade | obrigatório antes da ingestão |
| Versionamento de fontes | não identificado de forma compatível | nova capacidade | obrigatório |
| Segmentação estrutural auditável | não identificado de forma compatível | nova capacidade | fluxo assistido no MVP |
| Componentes pedagógicos canônicos | não identificado | nova capacidade | núcleo do almoxarifado |
| Evidências componente–fonte | não identificado | nova capacidade | obrigatório para rastreabilidade |
| Vínculos componente–currículo revisados | parcial no currículo | nova/adaptação | distinguir sugestão de vínculo aprovado |
| Política de acesso por agente | parcial no registro | nova/adaptação | escopo obrigatório do Sócrates 2 |
| Ordem de Produção Pedagógica | não identificado | nova capacidade | espinha dorsal de execução e auditoria |
| Context package limitado | não identificado | nova capacidade | máximo padrão de oito componentes |
| Estado de insuficiência | não identificado | nova capacidade | deve bloquear geração sem base suficiente |
| Fusão híbrida auditável | parcial | nova/adaptação | experimentar estratégia, não fixar por preferência |
| Reranqueamento | não identificado | experimental | somente após comparação objetiva |
| Contrato de entrega rastreável | não identificado | nova capacidade | quatro produtos mínimos |
| Harness de avaliação comparativa | não identificado | nova capacidade | Sócrates 2 versus agente genérico |
| Registro de custo por etapa | parcial | nova/adaptação | tokens, latência e custo por OPP |
| Curadoria administrativa | não há `apps/admin` no inventário observado | nova ou fluxo temporário | MVP pode usar scripts/fixtures revisados, sem painel completo |
| Workers dedicados | não há `apps/workers` no inventário observado | nova capacidade opcional | preferir jobs simples antes de novo aplicativo |

## Capacidade reutilizável não significa contrato preservado

A reutilização deverá obedecer às seguintes regras:

1. não importar tipos que contradigam os contratos aprovados;
2. não manter leitura pública direta de dados que tenham licença ou procedência controlada;
3. não fixar dimensão vetorial por compatibilidade histórica sem experimento;
4. não considerar um quality gate confiável apenas porque ele existe;
5. não acoplar Sócrates 2 a um prompt monolítico;
6. não duplicar fonte, componente ou currículo em vários pacotes;
7. não criar novo serviço quando um módulo do monorepo for suficiente.

## Lacunas críticas

As lacunas que bloqueiam o MVP são:

- repositório canônico não confirmado;
- contratos de domínio ainda não implementados;
- ausência de catálogo de fontes e permissões;
- ausência do modelo de componente pedagógico;
- ausência da OPP;
- ausência de avaliação objetiva da busca híbrida;
- ausência de harness de baseline e gates de aprovação do piloto;
- ausência de evidência de que os validadores atuais atendem os critérios do Marco 002.

## Estratégia de integração recomendada

No monorepo executável, a distribuição lógica proposta é:

- `packages/types`: contratos puros, enums e schemas sem dependência de infraestrutura;
- `packages/industry-pnld`: fonte, versão, segmento, procedência, destilação assistida e evidências;
- `packages/industry-curriculum`: pacotes curriculares, nós, vínculos e consulta determinística;
- `packages/db`: repositórios e persistência;
- `packages/ai`: embeddings, geração, orçamento e adapters de modelos;
- `packages/agents`: roteamento, Sócrates 2, OPP, composição e quality gates;
- `apps/bff`: endpoints do professor e endpoints internos autorizados;
- `apps/web`: experiência mínima do pedido e resultado;
- `supabase/migrations`: implementação física futura, somente após aprovação do modelo lógico;
- `packages/logger` e observabilidade existente: eventos, métricas e auditoria técnica;
- `packages/graphics-profeplan`: consumidor futuro do contrato de entrega, sem expansão no MVP.

## Decisão proposta

**ADR-016 — Reutilizar a arquitetura modular do monorepo, criando capacidades por responsabilidade e evitando um pacote monolítico `knowledge-factory`.**

Status: proposta, aguardando aprovação do Marco 003.
