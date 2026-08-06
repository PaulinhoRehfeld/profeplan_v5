# Definition of Done — MVP Sócrates 2

## Objetivo

Definir quando uma Story pode ser considerada concluída. Código escrito ou resposta visualmente convincente não são suficientes.

## Regra principal

Uma Story está Done somente quando implementação, testes, documentação, evidências, segurança, qualidade pedagógica e observabilidade aplicáveis estiverem concluídos e revisados.

## Checklist geral

### Implementação

- [ ] critérios de aceite foram atendidos;
- [ ] contratos aprovados foram respeitados;
- [ ] não houve ampliação silenciosa de escopo;
- [ ] código ou configuração seguem padrões do repositório;
- [ ] não existem segredos, tokens ou credenciais versionados;
- [ ] mudanças são reversíveis ou possuem estratégia de desativação.

### Testes

- [ ] caminho principal está testado;
- [ ] casos de falha previstos estão testados;
- [ ] permissões e bloqueios estão testados;
- [ ] testes não usam dados pessoais reais;
- [ ] resultados são reproduzíveis dentro dos limites probabilísticos documentados;
- [ ] testes automatizados aplicáveis passam;
- [ ] testes humanos aplicáveis possuem evidência registrada.

### Pedagogia e currículo

- [ ] impacto pedagógico foi revisado quando aplicável;
- [ ] currículo, etapa, ano e componente corretos foram verificados;
- [ ] objetivo, conteúdo, atividade e avaliação são coerentes quando presentes;
- [ ] linguagem e complexidade são adequadas ao 2º ano do Ensino Médio;
- [ ] não há mistura silenciosa de MG com outro currículo;
- [ ] decisão pedagógica relevante permanece sujeita a revisão humana.

### Fontes, autoria e rastreabilidade

- [ ] fontes utilizadas estão identificadas e autorizadas;
- [ ] versões de fontes e componentes são rastreáveis;
- [ ] conteúdo bloqueado ou em revisão não foi usado;
- [ ] verificação autoral aplicável foi executada;
- [ ] reprodução extensa detectada foi corrigida ou bloqueada;
- [ ] produto ou componente aponta para sua linhagem interna.

### Inclusão, segurança e privacidade

- [ ] requisitos inclusivos informados foram verificados;
- [ ] dados foram minimizados;
- [ ] controles de acesso aplicáveis foram testados;
- [ ] logs não expõem conteúdo protegido ou dado sensível sem necessidade;
- [ ] mensagens de erro são seguras e úteis;
- [ ] riscos residuais estão documentados.

### Observabilidade e custo

- [ ] eventos necessários estão registrados;
- [ ] falhas podem ser localizadas por OPP ou identificador equivalente;
- [ ] tokens e custo são medidos ou a impossibilidade é explicitamente registrada;
- [ ] latência ou duração da etapa pode ser analisada;
- [ ] ausência de telemetria não é tratada como valor zero;
- [ ] métricas não coletam conteúdo desnecessário.

### Documentação

- [ ] documento arquitetônico afetado foi atualizado;
- [ ] ADR foi criado ou atualizado quando houve decisão relevante;
- [ ] contratos e exemplos refletem o comportamento entregue;
- [ ] limitações e itens não implementados permanecem explícitos;
- [ ] instruções para teste e validação estão disponíveis;
- [ ] backlog e status da Story foram atualizados.

### Revisão e integração

- [ ] revisão técnica concluída;
- [ ] revisão pedagógica concluída quando aplicável;
- [ ] revisão jurídica ou de segurança concluída quando aplicável;
- [ ] evidências foram anexadas ao PR ou documento de validação;
- [ ] não existem pendências Must ocultas;
- [ ] a mudança está pronta para integração segundo a estratégia de branch vigente.

## Condições adicionais por categoria

### Fonte e ingestão

- uma fonte não pode ser considerada concluída sem procedência, licença e status;
- extração parcial deve estar explicitamente marcada;
- falhas de extração devem ser auditáveis;
- revisão humana do conjunto piloto deve estar registrada.

### Componente pedagógico

- possui metadados obrigatórios;
- possui procedência e versão;
- possui status aprovado para ser recuperável;
- não é produto final disfarçado;
- vínculo curricular aplicável foi revisado.

### Recuperação

- filtros são aplicados antes da busca vetorial;
- casos inelegíveis são excluídos nos testes;
- resultados recuperados são auditáveis;
- fallback de insuficiência funciona;
- limites e limiares experimentais estão versionados.

### Geração

- usa somente componentes elegíveis;
- registra OPP, agente, versão e contexto aplicável;
- executa gates obrigatórios;
- entrega contrato estruturado válido;
- não depende de PDF ou PPTX avançado.

### Validação

- registra aprovado, reprovado ou inconclusivo;
- registra justificativa e evidências;
- reprovação impede entrega como aprovada;
- correção ou regeneração mantém histórico;
- comparação humana é preservada quando prevista.

### Avaliação do piloto

- casos dourados foram executados;
- baseline genérico foi executado em condições comparáveis;
- métricas técnicas e pareceres docentes foram consolidados;
- limitações foram registradas;
- decisão de avançar, ajustar ou interromper foi formalizada;
- EPIC-018 continua bloqueado até aprovação explícita.

## Situações que impedem Done

Uma Story não pode ser encerrada quando:

- funciona apenas em demonstração manual não documentada;
- atende ao caminho feliz, mas ignora bloqueios obrigatórios;
- mistura disciplinas, anos ou currículos;
- usa fonte sem autorização registrada;
- entrega conteúdo sem rastreabilidade;
- falha silenciosamente;
- não mede o que afirma otimizar;
- depende de intervenção não registrada;
- possui teste desativado ou evidência ausente;
- documentação contradiz a implementação;
- item Won't foi incorporado sem decisão.

## Evidência mínima

Cada Story concluída deverá apontar, conforme aplicável, para:

- PR ou commit;
- testes executados;
- exemplos de entrada e saída;
- registros de telemetria;
- parecer pedagógico;
- parecer de autoria ou licença;
- atualização documental;
- decisão de aceite.

## Aprovação final

O aceite técnico não substitui o aceite pedagógico. O aceite pedagógico não substitui segurança, rastreabilidade ou direitos de uso. O Done exige a combinação dos papéis aplicáveis à Story.
