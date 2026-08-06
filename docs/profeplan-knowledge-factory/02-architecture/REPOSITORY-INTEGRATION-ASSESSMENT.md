# Avaliação de Repositórios e Integração

## Status

Proposta técnica do Marco 003. Não autoriza implementação.

## Objetivo

Registrar onde a ProfePlan Knowledge Factory poderá ser implementada, quais evidências foram encontradas nos repositórios acessíveis e qual decisão precisa ser tomada antes do primeiro Pull Request de código.

## Repositórios analisados

### `PaulinhoRehfeld/profeplan_v5`

Branch analisada: `docs/profeplan-knowledge-factory`.

Situação observada:

- contém o `README.md` raiz e a documentação criada nos Marcos 001 e 002;
- não contém `package.json`;
- não contém diretórios `apps`, `packages` ou `supabase`;
- não contém aplicações, migrations, serviços, testes ou código executável;
- atualmente funciona como repositório documental da Knowledge Factory.

Conclusão: não existe base técnica suficiente nesse repositório para integrar o MVP sem antes importar ou reconstruir o monorepo.

### `PaulinhoRehfeld/profeplan`

Branch analisada: `main`, somente leitura durante o Marco 003.

Situação observada:

- monorepo privado em TypeScript, gerenciado por pnpm;
- workspaces em `apps/*` e `packages/*`;
- aplicação web e BFF;
- pacote de agentes com orquestrador, registro de agentes disciplinares, quality gates, feature flags e observabilidade;
- pacote de IA com cliente OpenAI, prompts e fluxos de geração;
- pacote de banco com Prisma e acesso ao Supabase;
- pacote de tipos compartilhados;
- pacote `industry-curriculum` para BNCC e currículo de Minas Gerais;
- pacote `industry-pnld` criado, porém documentado como estrutura ainda pendente de implementação;
- migrations de Supabase, incluindo pgvector, RAG curricular, busca textual e políticas de RLS;
- pacote de Gráfica existente, embora a Gráfica avançada permaneça fora do MVP Sócrates 2.

Conclusão: este é o único repositório analisado que possui uma base executável compatível com a arquitetura aprovada.

## Divergência identificada

A documentação está no repositório `profeplan_v5`, mas o código funcional está no repositório `profeplan`.

Essa divergência impede autorizar o Codex a escrever código sem uma decisão formal. Caso contrário, existem três riscos:

1. implementar código em um repositório vazio e duplicar a plataforma;
2. implementar no monorepo real sem que a documentação esteja disponível no mesmo contexto;
3. manter duas fontes de verdade concorrentes.

## Alternativas

### Alternativa A — `profeplan` como repositório canônico de código

A documentação permanece temporariamente em `profeplan_v5`, mas é copiada ou migrada para `profeplan` antes do primeiro lote de implementação.

Vantagens:

- reutiliza o monorepo real;
- preserva agentes, currículo, IA, banco, BFF e testes existentes;
- reduz duplicação;
- permite PRs incrementais menores.

Riscos:

- exige validar se `profeplan` é realmente a versão de produção pretendida;
- requer sincronização ou migração da documentação;
- o nome do repositório pode não refletir a intenção de versão 5.

### Alternativa B — `profeplan_v5` como novo repositório canônico

O monorepo de `profeplan` é portado, reorganizado ou reconstruído em `profeplan_v5` antes da Knowledge Factory.

Vantagens:

- preserva a intenção explícita de trabalhar em uma versão 5;
- permite uma limpeza estrutural antes da implementação.

Riscos:

- transforma a migração do produto em pré-requisito do MVP;
- amplia muito o escopo;
- cria risco de regressão e perda de capacidades existentes;
- atrasa o experimento pedagógico.

### Alternativa C — repositório separado para a Knowledge Factory

A Knowledge Factory vira serviço independente e se integra por contratos ao ProfePlan.

Vantagens:

- alto desacoplamento;
- ciclo de implantação independente;
- possível reutilização futura por outros produtos da WRtech.

Riscos:

- infraestrutura, autenticação, observabilidade e operação adicionais;
- maior complexidade distribuída no MVP;
- risco de duplicar contratos e dados;
- contraria a decisão atual de validar primeiro o piloto pequeno.

## Recomendação técnica

Adotar a Alternativa A, condicionada à confirmação humana de que `PaulinhoRehfeld/profeplan` é o monorepo ativo que deverá receber as próximas implementações.

A recomendação não autoriza escrita nesse repositório. Ela deverá ser aprovada como decisão arquitetônica antes do primeiro PR de código.

## Estratégia de documentação

Após a decisão:

1. manter o PR nº 1 de `profeplan_v5` como histórico dos Marcos 001–003;
2. copiar a documentação aprovada para `profeplan/docs/profeplan-knowledge-factory/`, preservando histórico e referências;
3. criar no repositório canônico um índice que aponte para ADRs, Stories, contratos e lotes Codex;
4. proibir implementação baseada apenas em cópias locais ou trechos de conversa;
5. evitar manutenção paralela indefinida dos mesmos documentos em dois repositórios.

## Gate obrigatório

Nenhuma Story de implementação poderá receber status `Ready for Code` enquanto não houver:

- decisão sobre o repositório canônico;
- confirmação da branch base;
- confirmação de que a documentação aprovada está acessível ao Codex nesse repositório;
- inventário mínimo das capacidades reutilizáveis;
- definição de como o histórico do PR documental será preservado.

## Decisão pendente proposta

**ADR-015 — Repositório canônico da implementação da Knowledge Factory.**

Status no Marco 003: proposta, aguardando aprovação humana.
