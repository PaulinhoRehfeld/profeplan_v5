# User Stories do MVP — Sócrates 2

## Convenção

- Identificador: `US-<EPIC>.<sequência>`.
- Cada Story está vinculada a uma Feature.
- Os critérios de aceite são cumulativos e testáveis.
- Uma Story somente poderá entrar em implementação quando cumprir a Definition of Ready.

---

## EPIC-001 — Governança

### US-001.1 — Consultar o baseline aprovado

**Feature:** F-001.1  
**Prioridade:** Must

Como membro da equipe ou agente de desenvolvimento, quero consultar uma fonte documental única do MVP para implementar sem reinterpretar decisões já aprovadas.

**Critérios de aceite**

- existe índice com links para escopo, ADRs, Epics, Features e Stories;
- documentos conflitantes são identificados antes da implementação;
- decisões aprovadas estão distinguidas de hipóteses e pendências;
- o escopo excluído está explicitamente registrado;
- nenhuma Story autoriza código fora do MVP.

### US-001.2 — Aplicar critérios de prontidão e conclusão

**Feature:** F-001.2  
**Prioridade:** Must

Como responsável pelo produto, quero critérios comuns para iniciar e concluir Stories, evitando trabalho incompleto ou aceite baseado apenas em código produzido.

**Critérios de aceite**

- DoR e DoD estão versionadas;
- toda Story Must referencia critérios verificáveis;
- itens sem fonte, dependência ou critério de teste não entram em implementação;
- documentação e evidências fazem parte do encerramento;
- exceções exigem decisão humana registrada.

## EPIC-002 — Fontes

### US-002.1 — Registrar uma fonte com procedência

**Feature:** F-002.1  
**Prioridade:** Must

Como curador de conhecimento, quero registrar uma fonte antes de processá-la para preservar origem, versão e localização de cada contribuição.

**Critérios de aceite**

- título, tipo, autoria ou entidade responsável, edição ou versão e origem são obrigatórios;
- a fonte recebe identificador único;
- checksum ou mecanismo equivalente identifica arquivo idêntico;
- capítulo, seção e páginas podem ser referenciados;
- ausência de campos obrigatórios impede publicação da fonte.

### US-002.2 — Autorizar ou bloquear uso na geração

**Feature:** F-002.2  
**Prioridade:** Must

Como responsável jurídico e editorial, quero classificar permissões de uso para impedir geração baseada em fontes não autorizadas.

**Critérios de aceite**

- cada fonte possui classe de licença e finalidade permitida;
- o status de geração aceita apenas valores controlados;
- fonte bloqueada não aparece no conjunto recuperável;
- alteração de permissão gera histórico;
- componente vinculado a fonte proibida não pode ser aprovado para geração.

## EPIC-003 — Ingestão

### US-003.1 — Ingerir uma fonte piloto de forma assistida

**Feature:** F-003.1  
**Prioridade:** Must

Como curador, quero processar uma fonte autorizada em pequena escala para validar o fluxo antes de automatizá-lo industrialmente.

**Critérios de aceite**

- somente fonte autorizada entra no fluxo;
- o texto extraído permanece vinculado à fonte e versão;
- falha de extração é registrada e não produz publicação parcial silenciosa;
- o curador pode revisar o resultado antes da próxima etapa;
- nenhum OCR ou processamento massivo é requisito para considerar a Story concluída.

### US-003.2 — Preservar a estrutura da fonte

**Feature:** F-003.2  
**Prioridade:** Must

Como curador, quero segmentar o conteúdo por capítulo, seção e tipo de bloco para não perder contexto durante a destilação.

**Critérios de aceite**

- cada segmento mantém localização de origem;
- tipos mínimos distinguem conceito, explicação, exemplo, atividade, questão e orientação;
- a ordem original pode ser reconstruída para auditoria;
- segmentos incompletos ou ambíguos ficam em revisão;
- segmentos não são publicados diretamente como componentes pedagógicos.

## EPIC-004 — Componentes pedagógicos

### US-004.1 — Criar um componente pedagógico canônico

**Feature:** F-004.1  
**Prioridade:** Must

Como curador pedagógico, quero registrar uma unidade semielaborada com metadados completos para que agentes recuperem conhecimento sem consultar capítulos inteiros.

**Critérios de aceite**

- o componente possui conteúdo autoral estruturado;
- componente curricular, etapa, ano, tema e tipo são obrigatórios;
- procedência, licença, versão e status são obrigatórios;
- o registro diferencia texto recuperável de metadados de filtro;
- um componente não é um plano de aula ou produto finalizado.

### US-004.2 — Classificar o componente pela tipologia do piloto

**Feature:** F-004.2  
**Prioridade:** Must

Como curador pedagógico, quero classificar cada componente em tipos conhecidos para recuperar ingredientes adequados a cada produto.

**Critérios de aceite**

- a tipologia inclui os sete tipos mínimos aprovados;
- o tipo principal é obrigatório;
- finalidades compatíveis com plano, texto, atividade ou avaliação são registradas;
- combinações inválidas são rejeitadas ou enviadas à revisão;
- a distribuição do estoque por tipo pode ser auditada.

### US-004.3 — Revisar e versionar um componente

**Feature:** F-004.3  
**Prioridade:** Must

Como revisor pedagógico, quero aprovar, reprovar ou substituir componentes mantendo histórico para impedir recuperação de conteúdo não validado.

**Critérios de aceite**

- somente status aprovado pode entrar na geração;
- toda mudança relevante cria nova versão ou histórico equivalente;
- reprovado e substituído permanecem auditáveis, mas não recuperáveis;
- aprovação registra responsável e data;
- nenhuma atualização sobrescreve silenciosamente a versão utilizada por produto anterior.

## EPIC-005 — Destilação e deduplicação

### US-005.1 — Destilar conteúdo em síntese autoral

**Feature:** F-005.1  
**Prioridade:** Must

Como curador pedagógico, quero transformar contribuições autorizadas em síntese própria para ampliar repertório sem reproduzir uma obra.

**Critérios de aceite**

- o componente registra quais fontes contribuíram;
- a redação não é cópia extensa de uma única fonte;
- fatos, interpretações e estratégias pedagógicas são distinguíveis;
- revisão humana confirma adequação antes da aprovação;
- fonte não autorizada não pode ser usada como contribuição gerativa.

### US-005.2 — Detectar e consolidar duplicidade

**Feature:** F-005.2  
**Prioridade:** Must

Como curador, quero identificar componentes redundantes para reduzir ruído, custo de recuperação e repetição no contexto.

**Critérios de aceite**

- o sistema ou processo sinaliza candidatos semelhantes;
- a decisão de unir, relacionar ou manter separados é registrada;
- a unidade canônica preserva referências das contribuições;
- divergências conceituais relevantes não são apagadas;
- componentes duplicados não aparecem simultaneamente sem justificativa.

## EPIC-006 — Currículo

### US-006.1 — Disponibilizar o pacote curricular MG do piloto

**Feature:** F-006.1  
**Prioridade:** Must

Como especialista curricular, quero disponibilizar o recorte vigente de Filosofia do 2º ano de MG para orientar a produção sem carregar o currículo completo.

**Critérios de aceite**

- o pacote registra Estado, versão, vigência, etapa, ano e componente;
- habilidades ou referências curriculares aplicáveis são identificáveis;
- itens fora de Filosofia do 2º ano não entram no recorte padrão;
- versão inativa não é usada sem seleção explícita;
- o pacote RS não é carregado no MVP.

### US-006.2 — Vincular componentes ao currículo

**Feature:** F-006.2  
**Prioridade:** Must

Como especialista curricular, quero relacionar componentes pedagógicos aos objetivos e habilidades aplicáveis para recuperar matérias-primas coerentes.

**Critérios de aceite**

- cada vínculo identifica componente e nó curricular;
- a justificativa do vínculo pode ser revisada;
- vínculos aprovados são distinguíveis de sugestões automáticas;
- o mesmo componente pode ter mais de um vínculo quando pedagogicamente justificado;
- ausência de vínculo aplicável é sinalizada no pedido que exige alinhamento curricular.

## EPIC-007 — Recuperação

### US-007.1 — Aplicar filtros antes da busca vetorial

**Feature:** F-007.1  
**Prioridade:** Must

Como agente Sócrates 2, quero restringir a pesquisa por escopo e permissão antes da similaridade para não receber materiais de outra disciplina, ano, Estado ou licença.

**Critérios de aceite**

- Filosofia, Ensino Médio, 2º ano e MG são filtros obrigatórios no piloto;
- somente componentes aprovados e autorizados são elegíveis;
- o tipo de produto restringe os tipos de componente quando aplicável;
- qualquer candidato fora do filtro é excluído antes da composição;
- a consulta registra os filtros efetivamente aplicados.

### US-007.2 — Realizar busca híbrida limitada

**Feature:** F-007.2  
**Prioridade:** Must

Como agente Sócrates 2, quero combinar busca textual e vetorial para recuperar poucos componentes relevantes ao pedido.

**Critérios de aceite**

- ambas as buscas operam apenas no conjunto filtrado;
- resultados possuem pontuação ou posição auditável;
- a fusão remove duplicidades;
- o pacote principal não ultrapassa oito componentes, salvo exceção registrada;
- capítulos completos não são enviados à geração.

### US-007.3 — Interromper quando não houver base suficiente

**Feature:** F-007.3  
**Prioridade:** Must

Como professor, quero que o sistema reconheça insuficiência de conhecimento para não receber material convincente, porém sem fundamento adequado.

**Critérios de aceite**

- ausência ou baixa relevância aciona estado de insuficiência;
- o sistema não completa lacunas com conteúdo não rastreado silenciosamente;
- a resposta informa limitação de forma útil;
- a OPP registra a falha e a etapa;
- o fluxo permite ajustar tema, fonte ou escopo sem perder o pedido original.

## EPIC-008 — Orquestração

### US-008.1 — Rotear pedido válido para Sócrates 2

**Feature:** F-008.1  
**Prioridade:** Must

Como professor, quero que um pedido de Filosofia do 2º ano seja enviado ao especialista correto sem selecionar agentes técnicos manualmente.

**Critérios de aceite**

- componente, etapa, ano, Estado e produto são identificados;
- pedido válido seleciona Sócrates 2;
- pedido de outro componente ou ano não é processado como Sócrates 2;
- ambiguidades são sinalizadas antes da geração;
- a decisão de roteamento fica registrada.

### US-008.2 — Coordenar validadores sem fragmentar a resposta

**Feature:** F-008.2  
**Prioridade:** Must

Como professor, quero receber um único produto integrado, embora validadores especializados participem do processo.

**Critérios de aceite**

- Sócrates 2 permanece agente principal;
- cada validador recebe somente os dados necessários;
- resultados de validação são devolvidos à OPP;
- respostas intermediárias não são entregues separadamente ao professor;
- falha de validador obrigatório impede entrega como aprovada.

## EPIC-009 — Sócrates 2

### US-009.1 — Operar dentro do perfil especializado

**Feature:** F-009.1  
**Prioridade:** Must

Como responsável pedagógico, quero que Sócrates 2 respeite seu domínio e seus bloqueios para evitar mistura de conteúdo e nível escolar.

**Critérios de aceite**

- o perfil declara Filosofia, Ensino Médio, 2º ano e currículo MG;
- acessos complementares exigem justificativa do fluxo;
- RS, outros anos e outras disciplinas ficam bloqueados por padrão;
- fonte não autorizada e componente não aprovado são inacessíveis;
- pedido fora do escopo gera fallback, não improvisação.

### US-009.2 — Produzir os quatro tipos mínimos

**Feature:** F-009.2  
**Prioridade:** Must

Como professor de Filosofia, quero gerar plano, texto, atividade ou avaliação adequados ao 2º ano para testar utilidade real da fábrica.

**Critérios de aceite**

- cada tipo possui contrato de saída identificável;
- o produto responde ao tema, duração e contexto informados;
- texto do professor e do estudante são separados quando aplicável;
- conteúdo utilizado é rastreável;
- todos os gates Must são executados antes da entrega aprovada.

### US-009.3 — Gerar pacote integrado de aula

**Feature:** F-009.3  
**Prioridade:** Should

Como professor, quero solicitar um pequeno pacote de aula para receber peças pedagogicamente coerentes entre si.

**Critérios de aceite**

- plano, texto, atividade e avaliação compartilham objetivo central;
- a avaliação mede aprendizagem prevista no plano;
- a atividade usa conceitos presentes no texto ou na mediação proposta;
- o tempo total é viável;
- cada peça pode ser identificada separadamente no contrato de entrega.

## EPIC-010 — OPP

### US-010.1 — Criar uma Ordem de Produção Pedagógica válida

**Feature:** F-010.1  
**Prioridade:** Must

Como sistema, quero transformar o pedido em OPP para preservar requisitos e coordenar a produção.

**Critérios de aceite**

- OPP possui identificador e versão;
- produto, tema, etapa, ano, componente e currículo são obrigatórios;
- duração, turma, metodologia e inclusão são registrados quando informados;
- campos incompatíveis impedem o início;
- alterações após início geram nova versão ou evento auditável.

### US-010.2 — Acompanhar a linha do tempo da produção

**Feature:** F-010.2  
**Prioridade:** Must

Como auditor ou equipe técnica, quero reconstruir cada etapa da OPP para investigar qualidade, custo e falhas.

**Critérios de aceite**

- estados de criação, recuperação, geração, validação e entrega são registrados;
- agentes e validadores participantes são identificáveis;
- componentes e versões utilizados ficam vinculados;
- falhas e regenerações não são apagadas;
- produto final aponta para a OPP correspondente.

## EPIC-011 — Geração e personalização

### US-011.1 — Planejar a composição antes de redigir

**Feature:** F-011.1  
**Prioridade:** Must

Como Sócrates 2, quero organizar objetivo, estrutura e componentes antes da redação para produzir material coerente e autoral.

**Critérios de aceite**

- existe representação interna do plano de composição;
- o plano seleciona apenas componentes recuperados e autorizados;
- o tipo de produto determina estrutura mínima;
- fragmentos não são simplesmente concatenados;
- o plano é registrado de forma suficiente para auditoria, sem expor raciocínio privado do modelo.

### US-011.2 — Personalizar segundo o contexto

**Feature:** F-011.2  
**Prioridade:** Must

Como professor, quero que duração, nível de leitura, metodologia, recursos e perfil da turma afetem materialmente o produto.

**Critérios de aceite**

- requisitos fornecidos aparecem refletidos no produto;
- aula de duração diferente apresenta organização temporal diferente;
- nível de leitura modifica linguagem sem eliminar rigor conceitual;
- recurso indisponível não é exigido;
- contexto não autoriza fugir do currículo ou da qualidade mínima.

### US-011.3 — Produzir variações controladas

**Feature:** F-011.3  
**Prioridade:** Should

Como professor, quero alternativas metodológicas sem receber respostas aleatórias ou desconectadas.

**Critérios de aceite**

- variações preservam objetivo, currículo e conceitos centrais;
- diferenças metodológicas são explícitas;
- componentes e fontes continuam rastreáveis;
- a variação não replica apenas sinônimos;
- cada alternativa informa impacto no tempo ou nos recursos.

## EPIC-012 — Qualidade

### US-012.1 — Validar currículo e conceitos

**Feature:** F-012.1  
**Prioridade:** Must

Como professor, quero receber material curricularmente pertinente e conceitualmente correto.

**Critérios de aceite**

- o produto aponta o recorte curricular utilizado;
- afirmações centrais são compatíveis com componentes aprovados;
- mistura de Estado, ano ou disciplina reprova o gate;
- erro conceitual relevante exige correção antes da entrega;
- resultado do gate fica registrado.

### US-012.2 — Validar coerência pedagógica

**Feature:** F-012.2  
**Prioridade:** Must

Como professor, quero que objetivos, desenvolvimento, atividade e avaliação formem uma sequência executável.

**Critérios de aceite**

- atividade contribui para o objetivo declarado;
- avaliação verifica aprendizagem prevista;
- duração é compatível com as etapas propostas;
- comandos são compreensíveis para o 2º ano;
- reprovação devolve motivos específicos para correção.

### US-012.3 — Comparar validação automática e docente

**Feature:** F-012.3  
**Prioridade:** Should

Como responsável pedagógico, quero comparar gates automáticos com parecer humano para identificar falsos positivos e falsos negativos.

**Critérios de aceite**

- amostra e rubrica são registradas;
- o docente pode concordar, discordar e justificar;
- divergências são classificadas;
- o resultado não altera automaticamente regras sem aprovação;
- aprendizados entram no relatório do piloto.

## EPIC-013 — Autoria e rastreabilidade

### US-013.1 — Bloquear proximidade lexical excessiva

**Feature:** F-013.1  
**Prioridade:** Must

Como responsável editorial, quero identificar reprodução excessiva das fontes para impedir entrega autoralmente insegura.

**Critérios de aceite**

- o produto é comparado às evidências recuperadas;
- sequências suspeitas são sinalizadas;
- atividade ou questão integral de fonte protegida é bloqueada;
- produto reprovado pode ser regenerado;
- limiares usados são versionados e tratados como hipótese de teste.

### US-013.2 — Registrar linhagem do produto

**Feature:** F-013.2  
**Prioridade:** Must

Como auditor, quero saber quais componentes e fontes sustentaram um produto sem expor indevidamente obras protegidas.

**Critérios de aceite**

- produto vincula IDs e versões dos componentes;
- cada componente vincula suas fontes e permissões;
- currículo e versão do perfil do agente são registrados;
- rastreabilidade interna não entrega texto restrito ao usuário final;
- a linhagem permanece disponível após atualização do acervo.

## EPIC-014 — Inclusão

### US-014.1 — Registrar necessidade inclusiva na OPP

**Feature:** F-014.1  
**Prioridade:** Must

Como professor, quero informar necessidades de acesso e participação desde o pedido para que sejam consideradas na produção.

**Critérios de aceite**

- a OPP aceita requisitos inclusivos estruturados e observações do professor;
- ausência de requisito não presume diagnóstico;
- o sistema não inventa laudo ou condição do estudante;
- requisitos incompatíveis são sinalizados;
- dados sensíveis seguem minimização e controle de acesso.

### US-014.2 — Validar cumprimento inclusivo mínimo

**Feature:** F-014.2  
**Prioridade:** Must

Como professor, quero confirmar que o material atende aos requisitos inclusivos solicitados.

**Critérios de aceite**

- instruções segmentadas são verificadas quando solicitadas;
- alternativas de resposta aparecem quando exigidas;
- redução textual não elimina objetivo essencial;
- o gate informa requisitos atendidos e não atendidos;
- descumprimento obrigatório impede entrega como aprovada.

## EPIC-015 — Contrato de entrega

### US-015.1 — Entregar produto pedagógico estruturado

**Feature:** F-015.1  
**Prioridade:** Must

Como módulo consumidor, quero receber um contrato estruturado para exibir, editar ou futuramente diagramar o conteúdo validado.

**Critérios de aceite**

- contrato possui versão e tipo de produto;
- conteúdo do professor e do estudante são distinguíveis;
- atividades, avaliação e referências internas possuem campos próprios;
- resultado dos gates e OPP são referenciados;
- o contrato não exige PDF ou PPTX para ser considerado válido.

### US-015.2 — Registrar requisitos para a futura Gráfica

**Feature:** F-015.2  
**Prioridade:** Should

Como futura Gráfica ProfePlan, quero receber indicações visuais e de acessibilidade sem interferir na autoria pedagógica.

**Critérios de aceite**

- hierarquia e tipos de bloco são informados;
- requisitos de acessibilidade visual podem ser registrados;
- formato desejado é preferência, não arquivo final do MVP;
- conteúdo validado não é alterado silenciosamente;
- ausência dessa Feature não bloqueia a prova pedagógica principal.

## EPIC-016 — Observabilidade

### US-016.1 — Medir o fluxo por OPP

**Feature:** F-016.1  
**Prioridade:** Must

Como equipe de produto, quero medir duração, falhas e etapas de cada OPP para localizar gargalos e comparar execuções.

**Critérios de aceite**

- início, término e status de cada etapa são registrados;
- falhas possuem categoria e mensagem segura;
- quantidade e IDs de componentes recuperados são auditáveis;
- modelo e versões relevantes são identificados;
- telemetria não registra conteúdo sensível desnecessário.

### US-016.2 — Medir tokens e custo

**Feature:** F-016.2  
**Prioridade:** Must

Como responsável financeiro e técnico, quero conhecer tokens e custo por etapa para avaliar viabilidade do SaaS.

**Critérios de aceite**

- entrada e saída são separadas por recuperação, geração e validação quando disponível;
- custo usa tabela de preço versionada ou registra que é estimativa;
- total por OPP pode ser calculado;
- falha de medição é explícita, não tratada como zero;
- dados permitem comparar Sócrates 2 e baseline genérico.

## EPIC-017 — Avaliação

### US-017.1 — Executar casos dourados contra baseline

**Feature:** F-017.1  
**Prioridade:** Must

Como equipe de produto, quero executar pedidos equivalentes no Sócrates 2 e em abordagem genérica para medir o benefício da especialização.

**Critérios de aceite**

- casos cobrem os quatro produtos mínimos e temas diversos;
- pedido e modelo são equivalentes quando possível;
- rubrica mede qualidade, currículo, ruído, autoria, tokens e latência;
- avaliadores não recebem indicação tendenciosa da origem quando houver avaliação cega;
- resultados brutos e consolidados são preservados.

### US-017.2 — Tomar decisão formal sobre o piloto

**Feature:** F-017.2  
**Prioridade:** Must

Como direção da WR Tech, quero decidir avançar, ajustar ou interromper com base em evidências pedagógicas, jurídicas, técnicas e econômicas.

**Critérios de aceite**

- avaliação docente está incluída;
- falhas e limitações estão registradas;
- tokens, custo e latência estão documentados;
- a decisão possui responsáveis e justificativa;
- EPIC-018 permanece bloqueado até decisão explícita de avanço.

## EPIC-018 — Expansão

### US-018.1 — Adicionar RS ou novo agente

**Feature:** F-018.1  
**Prioridade:** Won't no MVP

Esta Story não poderá receber status Ready durante o MVP. Sua abertura depende da conclusão e aprovação da US-017.2.
