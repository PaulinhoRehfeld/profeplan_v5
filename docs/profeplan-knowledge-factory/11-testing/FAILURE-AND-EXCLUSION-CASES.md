# Casos de falha e critérios de exclusão — MVP Sócrates 2

## Objetivo

Definir comportamentos que o MVP deve rejeitar, interromper, sinalizar ou excluir das métricas de sucesso. Uma resposta gerada não equivale a uma execução bem-sucedida.

## Estados esperados

- **rejeitado:** entrada inválida ou proibida;
- **bloqueado:** regra jurídica, curricular, autoral ou de segurança impede continuidade;
- **insuficiente:** não há base de conhecimento adequada;
- **reprovado:** produto falhou em gate obrigatório;
- **inconclusivo:** não há evidência suficiente para aprovar ou reprovar;
- **falha técnica:** erro de infraestrutura ou integração;
- **concluído com ressalva:** somente para limitações não bloqueantes previamente definidas;
- **aprovado:** todos os gates Must aplicáveis foram atendidos.

## Casos de falha por domínio

### Fontes e direitos

#### FC-001 — Fonte sem procedência

- **Cenário:** arquivo ou texto sem origem, versão ou responsável identificável.
- **Comportamento esperado:** rejeitar ingestão ou manter em quarentena.
- **Não pode ocorrer:** criação de componente aprovado.

#### FC-002 — Fonte sem permissão para geração

- **Cenário:** licença desconhecida, proibida ou restrita ao uso não gerativo.
- **Comportamento esperado:** bloquear publicação e recuperação.
- **Não pode ocorrer:** uso indireto por meio de componente derivado.

#### FC-003 — Alteração posterior de permissão

- **Cenário:** fonte antes autorizada passa a bloqueada.
- **Comportamento esperado:** impedir novas gerações e preservar auditoria de produtos anteriores.
- **Não pode ocorrer:** apagar histórico para simular conformidade retroativa.

### Ingestão e estrutura

#### FC-004 — Extração parcial tratada como completa

- **Cenário:** páginas ou seções falham sem sinalização.
- **Comportamento esperado:** marcar incompletude e impedir publicação silenciosa.

#### FC-005 — Perda da localização de origem

- **Cenário:** segmento não pode ser relacionado a capítulo, seção ou página.
- **Comportamento esperado:** enviar à revisão ou rejeitar.

#### FC-006 — Atividade confundida com explicação

- **Cenário:** classificação estrutural incorreta.
- **Comportamento esperado:** impedir uso até revisão.

### Componentes pedagógicos

#### FC-007 — Componente sem metadados obrigatórios

- **Comportamento esperado:** não permitir status aprovado.

#### FC-008 — Componente em rascunho recuperado

- **Comportamento esperado:** excluir antes da busca textual ou vetorial.

#### FC-009 — Produto final armazenado como matéria-prima

- **Cenário:** plano completo ou avaliação pronta é cadastrado como componente comum.
- **Comportamento esperado:** rejeitar ou reclassificar mediante revisão.

#### FC-010 — Duplicidade não consolidada

- **Cenário:** vários componentes quase idênticos dominam a recuperação.
- **Comportamento esperado:** sinalizar concentração e impedir pacote redundante.

### Currículo

#### FC-011 — Mistura de MG e RS

- **Comportamento esperado:** reprovar roteamento ou gate curricular.

#### FC-012 — Filosofia de outro ano

- **Comportamento esperado:** excluir antes da busca.

#### FC-013 — Versão curricular inativa utilizada silenciosamente

- **Comportamento esperado:** bloquear ou exigir seleção explícita e registrada.

#### FC-014 — Vínculo curricular sem validação

- **Comportamento esperado:** não tratar sugestão automática como vínculo aprovado.

### Recuperação

#### FC-015 — Busca vetorial executada antes dos filtros

- **Comportamento esperado:** considerar implementação inválida e falhar o teste arquitetônico.

#### FC-016 — Recuperação de fonte bloqueada

- **Comportamento esperado:** bloquear o fluxo e abrir incidente de segurança/conformidade.

#### FC-017 — Pacote com mais de oito componentes sem justificativa

- **Comportamento esperado:** registrar exceção, reduzir ou reprovar montagem do contexto.

#### FC-018 — Baixa relevância tratada como suficiência

- **Comportamento esperado:** acionar fallback e não improvisar material completo.

#### FC-019 — Capítulo completo enviado ao modelo

- **Comportamento esperado:** bloquear montagem de contexto no fluxo padrão.

### Roteamento e agentes

#### FC-020 — Pedido de outra disciplina roteado ao Sócrates 2

- **Comportamento esperado:** rejeitar ou encaminhar ao fallback de escopo.

#### FC-021 — Pedido ambíguo processado sem confirmação

- **Comportamento esperado:** sinalizar ambiguidade antes da geração.

#### FC-022 — Agente acessa domínio bloqueado

- **Comportamento esperado:** negar acesso, registrar tentativa e interromper se o dado for obrigatório.

#### FC-023 — Validador obrigatório indisponível

- **Comportamento esperado:** não entregar como aprovado; registrar estado inconclusivo ou falha técnica.

### Ordem de Produção Pedagógica

#### FC-024 — OPP com campos incompatíveis

- **Exemplo:** Filosofia, 2º ano, currículo RS no MVP.
- **Comportamento esperado:** rejeitar antes da recuperação.

#### FC-025 — Alteração silenciosa da OPP

- **Comportamento esperado:** exigir versão ou evento auditável.

#### FC-026 — Produto sem vínculo à OPP

- **Comportamento esperado:** considerar entrega inválida.

### Geração e personalização

#### FC-027 — Concatenação de fragmentos

- **Comportamento esperado:** reprovar gate autoral ou pedagógico.

#### FC-028 — Contexto da turma ignorado

- **Comportamento esperado:** reprovar aderência quando requisito obrigatório não aparece no produto.

#### FC-029 — Recurso inexistente exigido

- **Comportamento esperado:** corrigir antes da entrega.

#### FC-030 — Duração inviável

- **Comportamento esperado:** reprovar gate pedagógico.

#### FC-031 — Variação apenas lexical

- **Comportamento esperado:** não considerar como variação metodológica válida.

### Qualidade e autoria

#### FC-032 — Erro filosófico relevante

- **Comportamento esperado:** reprovar e corrigir; não entregar como ressalva.

#### FC-033 — Atividade não relacionada ao objetivo

- **Comportamento esperado:** reprovar coerência pedagógica.

#### FC-034 — Avaliação não mede aprendizagem prevista

- **Comportamento esperado:** reprovar coerência.

#### FC-035 — Reprodução extensa detectada

- **Comportamento esperado:** bloquear, registrar e regenerar.

#### FC-036 — Linhagem incompleta

- **Comportamento esperado:** impedir entrega aprovada.

### Inclusão e privacidade

#### FC-037 — Diagnóstico inventado

- **Comportamento esperado:** bloquear afirmação e registrar falha de segurança pedagógica.

#### FC-038 — Necessidade inclusiva obrigatória ignorada

- **Comportamento esperado:** reprovar gate inclusivo.

#### FC-039 — Simplificação elimina conceito central

- **Comportamento esperado:** reprovar qualidade conceitual.

#### FC-040 — Dado sensível desnecessário em log

- **Comportamento esperado:** remover, corrigir telemetria e tratar como incidente.

### Contrato de entrega

#### FC-041 — Conteúdo de professor e estudante misturados

- **Comportamento esperado:** rejeitar contrato.

#### FC-042 — Gate reprovado omitido do contrato

- **Comportamento esperado:** bloquear entrega.

#### FC-043 — PDF ou PPTX tratado como requisito do MVP

- **Comportamento esperado:** classificar como expansão indevida de escopo.

### Observabilidade

#### FC-044 — Falha de medição registrada como zero

- **Comportamento esperado:** marcar dado ausente ou erro de telemetria.

#### FC-045 — Tokens agregados sem separação comparável

- **Comportamento esperado:** considerar evidência insuficiente para baseline.

#### FC-046 — OPP sem identificação nas métricas

- **Comportamento esperado:** excluir execução de análise comparativa e corrigir rastreabilidade.

### Avaliação

#### FC-047 — Baseline recebe pedido diferente

- **Comportamento esperado:** invalidar comparação.

#### FC-048 — Avaliação docente sem rubrica

- **Comportamento esperado:** tratar como comentário qualitativo, não como escore comparável.

#### FC-049 — Expansão iniciada antes da decisão

- **Comportamento esperado:** interromper EPIC-018 e registrar violação de governança.

#### FC-050 — Apenas casos bem-sucedidos são reportados

- **Comportamento esperado:** reprovar relatório do piloto por viés de seleção.

## Critérios de exclusão das métricas de sucesso

Uma execução deve ser excluída do conjunto principal de comparação quando:

- pedido ou configuração diverge do par comparável;
- versão do modelo não está registrada;
- telemetria essencial falhou;
- OPP não pode ser reconstruída;
- fonte ou componente perdeu rastreabilidade;
- houve intervenção manual não registrada;
- gate obrigatório foi ignorado;
- resultado foi selecionado entre múltiplas tentativas sem registrar as demais;
- avaliador recebeu informação que comprometeu avaliação cega planejada;
- ambiente apresentou falha externa que impediu execução equivalente.

A exclusão deve ser registrada com motivo. Dados excluídos não devem ser apagados.

## Critérios de reprovação do MVP

O piloto não poderá ser aprovado quando ocorrer qualquer uma destas condições sem correção demonstrada:

- mistura recorrente de disciplina, ano ou Estado;
- uso de fonte não autorizada;
- incapacidade de rastrear componentes usados;
- reprodução extensa não bloqueada;
- ausência de fallback para insuficiência;
- entrega sem gates obrigatórios;
- impossibilidade de medir custo e latência de forma comparável;
- avaliação docente indicar inutilidade pedagógica recorrente;
- arquitetura especializada não demonstrar benefício suficiente frente ao baseline;
- expansão necessária para que o piloto pareça funcional.

## Critérios de resultado inconclusivo

O piloto deve ser considerado inconclusivo, e não aprovado, quando:

- amostra de casos dourados é insuficiente;
- número ou diversidade de componentes não cobre os temas selecionados;
- professores avaliadores são insuficientes para a decisão proposta;
- telemetria não permite comparação;
- fontes do piloto mudam durante o teste sem controle de versão;
- limiares são alterados repetidamente após observar resultados sem registrar o ajuste;
- o baseline não é comparável.

## Regra de correção

Toda correção deve preservar:

- entrada original;
- versão anterior;
- motivo da falha;
- alteração realizada;
- nova execução;
- resultado dos gates;
- impacto nas métricas.
