# Modelo de Segurança, RLS, Auditoria e Minimização

## Status

Proposta do Marco 003. As políticas físicas serão implementadas somente após aprovação e análise do schema canônico.

## Objetivos

- impedir acesso entre tenants;
- impedir agentes de acessar conhecimento fora do escopo;
- proteger fontes restritas e textos brutos;
- garantir que licença seja requisito de autorização, não apenas metadado;
- minimizar dados de professores e estudantes;
- preservar auditoria sem registrar conteúdo sensível desnecessário;
- restringir service role e operações administrativas.

## Princípios

1. negar por padrão;
2. menor privilégio;
3. separação entre leitura de professor, curadoria e processamento técnico;
4. licença e status participam da autorização;
5. agente não acessa tabelas livremente; usa serviços/repositórios com política;
6. RLS não substitui validação de aplicação, e validação de aplicação não substitui RLS;
7. nenhum dado real de estudante é necessário ao corpus global;
8. logs evitam prompts completos quando hashes, IDs e métricas bastarem;
9. credenciais nunca aparecem em OPP, eventos ou contrato de entrega;
10. toda elevação administrativa é auditada.

## Atores

### `teacher`

Pode:

- criar e ler as próprias OPPs;
- ler produtos autorizados do próprio tenant;
- consultar status e avisos permitidos;
- fornecer contexto minimizado.

Não pode:

- ler fontes brutas;
- ler componentes protegidos diretamente;
- alterar licença;
- aprovar componente;
- ler OPP de outro tenant;
- selecionar service role ou configuração interna.

### `curator`

Pode:

- registrar fontes autorizadas;
- revisar segmentos;
- criar e revisar componentes;
- propor vínculos curriculares;
- executar ingestão assistida dentro do escopo atribuído.

Não pode:

- conceder licença jurídica sem papel correspondente;
- alterar logs;
- acessar dados de professor sem necessidade;
- ativar pacote curricular sozinho quando exigir dupla aprovação.

### `legal_editorial_reviewer`

Pode:

- classificar licença e finalidade;
- bloquear ou suspender fonte;
- revisar exigência de atribuição;
- consultar evidência de uso.

### `curriculum_reviewer`

Pode:

- revisar pacotes e vínculos;
- ativar versão aprovada conforme política;
- não acessa texto bruto protegido além do necessário.

### `system_worker`

Identidade técnica restrita a jobs:

- lê somente itens elegíveis para o job;
- escreve resultados previstos;
- não contorna licença;
- usa idempotência;
- não possui acesso administrativo geral por conveniência.

### `auditor`

Leitura restrita a eventos, versões e evidências necessárias. Dados pessoais são mascarados quando possível.

### `service_role`

Uso excepcional e encapsulado. Proibido no cliente. Cada operação deve ser justificada, monitorada e limitada a backend/job.

## Classificação de dados

| Classe | Exemplos | Tratamento |
|---|---|---|
| público oficial | currículo publicado | leitura controlada pelo serviço; não necessariamente tabela pública |
| global curado | componentes aprovados | acesso apenas por retrieval autorizado |
| protegido por licença | livros, segmentos brutos | camada restrita e finalidade controlada |
| tenant privado | OPP, produtos, preferências | RLS por tenant e usuário |
| sensível educacional | adaptações, contexto individual | minimização e acesso estrito |
| segredo técnico | chaves, tokens | secret manager; nunca persistir em domínio |
| auditoria | eventos, hashes, achados | append-only, acesso restrito |

## Estratégia lógica de RLS

### Corpus global

Não deve usar `USING (true)` como padrão apenas por ser conhecimento compartilhado.

Acesso recomendado:

- professores não consultam tabelas diretamente;
- serviços autenticados executam retrieval com políticas;
- leitura administrativa por papel;
- escrita somente por curadoria/job autorizado;
- fonte restrita nunca é exposta no contrato do professor.

### Dados de tenant

Política conceitual:

```text
tenant_id = tenant atual
AND usuário pertence ao tenant
AND ação é permitida pelo papel
```

Para OPP individual, pode haver adicionalmente:

```text
requester_id = usuário atual
OR papel administrativo autorizado no tenant
```

### Jobs

- jobs recebem IDs específicos, não consultas globais irrestritas;
- service role não é justificativa para ignorar filtro de licença;
- cada job registra ator técnico, propósito e correlação;
- falha não deixa estado parcialmente publicado.

## Política de agente

O escopo do agente é aplicado em três camadas:

1. contrato do perfil;
2. QueryPlan e filtros de serviço;
3. política de acesso/persistência.

Para Sócrates 2:

- componente `philosophy`;
- etapa `high_school`;
- ano `2`;
- Estado `MG`;
- pacote ativo aprovado;
- produtos permitidos;
- status aprovado;
- licença elegível;
- limite de contexto;
- acesso interdisciplinar bloqueado por padrão.

Prompt não é controle de segurança.

## Minimização de dados na OPP

Permitido quando necessário:

- tamanho aproximado da turma;
- nível geral de leitura;
- recursos disponíveis;
- tempo;
- metodologia preferida;
- necessidade inclusiva em termos funcionais.

Evitar:

- nome do estudante;
- CPF;
- e-mail;
- diagnóstico detalhado;
- laudo;
- endereço;
- nota individual;
- observação disciplinar identificável.

Exemplo preferido:

> “A turma precisa de instruções em etapas e opção de resposta oral.”

Em vez de:

> “O aluno X possui o diagnóstico Y e o laudo Z.”

## Embeddings e privacidade

- somente campos autorizados e não pessoais;
- registrar hash do texto de origem;
- reindexar quando permissão mudar;
- vetores de conteúdo privado são isolados por tenant e finalidade, caso essa capacidade exista futuramente;
- o MVP não exige embedding de documentos privados de professor;
- exclusão/revogação deve alcançar embeddings derivados.

## Auditoria

Eventos mínimos:

- criação/alteração de fonte;
- mudança de licença;
- ingestão;
- revisão de segmento;
- criação/aprovação/reprovação de componente;
- ativação de pacote curricular;
- mudança de perfil do agente;
- retrieval com filtros e versões;
- geração e modelo utilizado;
- gate executado;
- aprovação/rejeição;
- entrega;
- acesso administrativo;
- exportação;
- incidente.

Cada evento contém:

- ID;
- ator;
- papel;
- tenant quando aplicável;
- ação;
- recurso e versão;
- timestamp;
- correlation ID;
- resultado;
- motivo;
- metadados minimizados.

Logs não devem conter automaticamente:

- livro completo;
- segmento bruto;
- prompt completo;
- resposta integral;
- dados pessoais;
- chave de API.

## Integridade de auditoria

- eventos append-only;
- proibir update/delete comum;
- retenção e exportação controladas;
- sequência ou hash encadeado pode ser avaliado conforme risco;
- relógio e timezone consistentes;
- alterações administrativas deixam evento independente.

## Segregação de ambientes

- desenvolvimento usa fixtures sintéticas;
- homologação usa corpus autorizado e dados fictícios;
- produção usa fontes aprovadas;
- credenciais e buckets distintos;
- nenhum dump de produção no ambiente de desenvolvimento sem processo autorizado.

## Threat scenarios mínimos

1. professor tenta ler OPP de outro tenant;
2. frontend chama tabela global diretamente;
3. worker usa service role para recuperar fonte bloqueada;
4. alteração de licença não invalida componente;
5. prompt injection dentro de uma fonte;
6. texto de estudante entra no embedding;
7. log armazena obra protegida;
8. usuário manipula `grade` para acessar outro agente;
9. pacote RS é ativado no MVP;
10. produto rejeitado é entregue por endpoint alternativo;
11. retry duplica cobrança e produto;
12. admin amplia papel sem auditoria.

## Testes de RLS e autorização

- matriz papel × recurso × ação;
- tenant A versus tenant B;
- usuário sem papel;
- service role somente em backend;
- fonte bloqueada;
- componente suspenso;
- produto rejeitado;
- pacote inativo;
- acesso direto versus serviço;
- revogação de licença;
- tentativa de enum/ID manipulado.

## Pendências jurídicas/operacionais

- períodos exatos de retenção;
- processo de autorização de editoras;
- papel formal de encarregado e auditor;
- política de uso de outputs de provedores;
- critérios de anonimização;
- resposta a incidente e SLA;
- política de exclusão de dados de tenant.

## Decisão proposta

**ADR-022 — Corpus compartilhado não implica leitura pública direta; acesso ocorre por serviços autorizados, com licença, status e escopo como condições de autorização.**

Status: proposta, aguardando aprovação.
