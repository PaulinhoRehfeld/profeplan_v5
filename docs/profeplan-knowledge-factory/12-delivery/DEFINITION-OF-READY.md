# Definition of Ready — MVP Sócrates 2

## Objetivo

Definir as condições mínimas para que uma User Story possa ser entregue ao Codex ou à equipe técnica para planejamento e implementação.

## Regra principal

Uma Story não está Ready apenas porque possui um título. Ela precisa estar suficientemente definida para que a implementação não exija reinventar o produto, o currículo ou os critérios pedagógicos.

## Checklist obrigatório

### Valor e escopo

- [ ] possui identificador único;
- [ ] está vinculada a um Epic e a uma Feature aprovados;
- [ ] expressa valor para professor, curador, revisor, auditor ou operação;
- [ ] pertence ao escopo do MVP;
- [ ] não depende de capacidade classificada como Won't;
- [ ] itens fora do escopo estão explicitados quando houver risco de expansão.

### Decisões e contratos

- [ ] respeita os ADRs vigentes;
- [ ] possui contrato de entrada definido;
- [ ] possui contrato de saída definido;
- [ ] estados e erros relevantes estão descritos;
- [ ] campos obrigatórios e opcionais estão distinguíveis;
- [ ] termos usados existem no glossário ou são definidos na própria Story.

### Critérios de aceite

- [ ] possui critérios observáveis e testáveis;
- [ ] critérios cobrem o caminho principal;
- [ ] critérios cobrem pelo menos um caso de falha relevante;
- [ ] requisitos pedagógicos não foram reduzidos a validação meramente técnica;
- [ ] quando aplicável, há critérios curriculares, autorais, inclusivos e de segurança;
- [ ] não contém expressões vagas como “funcionar bem”, “ser inteligente” ou “ser rápido” sem medida ou evidência.

### Dependências

- [ ] dependências anteriores estão concluídas ou formalmente disponíveis;
- [ ] fonte documental aplicável está identificada;
- [ ] dados, fixtures ou exemplos necessários estão disponíveis ou planejados;
- [ ] integração externa necessária está confirmada;
- [ ] decisões ainda pendentes não impedem a implementação;
- [ ] risco de bloqueio está registrado.

### Dados, segurança e direitos

- [ ] dados pessoais necessários foram minimizados;
- [ ] nenhum dado real de estudante é exigido para teste;
- [ ] permissões de acesso estão definidas quando aplicável;
- [ ] fontes utilizadas possuem situação jurídica registrada;
- [ ] conteúdo bloqueado ou em revisão não é tratado como dado válido;
- [ ] requisitos de auditoria e retenção estão identificados.

### IA e avaliação

- [ ] papel do modelo está definido;
- [ ] entradas e saídas do modelo estão delimitadas;
- [ ] fallback para insuficiência ou erro está descrito;
- [ ] comportamento determinístico e probabilístico estão diferenciados;
- [ ] métrica ou rubrica de avaliação está definida quando aplicável;
- [ ] baseline ou caso dourado está disponível para Story de avaliação.

### Implementação e validação

- [ ] estratégia de teste é conhecida;
- [ ] evidência esperada de conclusão está definida;
- [ ] observabilidade necessária está descrita;
- [ ] rollback ou desativação é possível quando houver risco relevante;
- [ ] prioridade MoSCoW está registrada;
- [ ] responsável pela aprovação está identificado por papel, ainda que o nome seja definido depois.

## Condições adicionais por categoria

### Stories de fonte ou conhecimento

Devem possuir:

- exemplo de fonte autorizada;
- metadados mínimos;
- regra de aprovação;
- regra de bloqueio;
- vínculo de procedência.

### Stories curriculares

Devem possuir:

- documento oficial de referência;
- versão e vigência;
- recorte por Estado, etapa, ano e componente;
- regra contra mistura de currículos.

### Stories de recuperação

Devem possuir:

- filtros obrigatórios;
- conjunto de teste com itens elegíveis e inelegíveis;
- limite inicial tratável como hipótese;
- comportamento de insuficiência;
- métrica de relevância ou avaliação humana.

### Stories de geração

Devem possuir:

- tipo de produto;
- estrutura mínima;
- contexto mínimo do professor;
- componentes recuperáveis de exemplo;
- gates obrigatórios;
- caso dourado esperado.

### Stories de validação

Devem possuir:

- rubrica;
- resultado aprovado, reprovado e inconclusivo;
- comportamento de correção;
- registro da decisão;
- autoridade humana de revisão.

## Situações que impedem Ready

Uma Story não pode ser marcada Ready quando:

- amplia o escopo para RS, novo agente ou nova etapa;
- exige fonte ainda não classificada juridicamente;
- não possui critérios de aceite testáveis;
- depende de tecnologia escolhida apenas por conveniência;
- pede código antes do contrato;
- mistura Feature Must com item Won't;
- remove supervisão humana de decisão pedagógica ou jurídica;
- trata ausência de medição como sucesso;
- pressupõe dados reais de estudantes sem necessidade.

## Aprovação

A marcação Ready exige, no mínimo:

- validação de produto/arquitetura;
- validação pedagógica quando houver impacto educacional;
- validação técnica de viabilidade;
- validação jurídica ou de segurança quando houver fonte protegida ou dado sensível.

A ausência de um papel aplicável deve ser registrada, não presumida.
