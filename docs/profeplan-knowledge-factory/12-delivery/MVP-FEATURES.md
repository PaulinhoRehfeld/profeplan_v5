# Features do MVP — Sócrates 2

## Convenção

- Identificador: `F-<EPIC>.<sequência>`.
- Prioridade: Must, Should, Could ou Won't.
- Uma Feature Must bloqueia a conclusão do MVP quando não entregue.
- Features Should e Could somente podem entrar após as Must das quais dependem.

---

## EPIC-001 — Governança e fundação

### F-001.1 — Baseline documental do MVP

- **Prioridade:** Must
- **Valor:** fornece ao Codex e à equipe uma fonte única de decisões aprovadas.
- **Entregas:** escopo, ADRs, glossário, Epics, Features, Stories e critérios.
- **Dependências:** nenhuma.

### F-001.2 — Governança de prontidão e conclusão

- **Prioridade:** Must
- **Valor:** impede entrada de Stories incompletas e encerramento sem evidências.
- **Entregas:** Definition of Ready, Definition of Done e fluxo de mudança.
- **Dependências:** F-001.1.

## EPIC-002 — Fontes e direitos de uso

### F-002.1 — Registro de fonte e procedência

- **Prioridade:** Must
- **Valor:** torna cada matéria-prima identificável e auditável.
- **Entregas:** identificação, edição, versão, origem, localização e checksum.
- **Dependências:** F-001.1.

### F-002.2 — Política de autorização para geração

- **Prioridade:** Must
- **Valor:** impede que conteúdo não autorizado entre na produção.
- **Entregas:** classe de licença, usos permitidos, restrições, status e bloqueio.
- **Dependências:** F-002.1.

## EPIC-003 — Ingestão e leitura estrutural

### F-003.1 — Ingestão assistida do conjunto piloto

- **Prioridade:** Must
- **Valor:** permite testar o fluxo sem exigir automação industrial.
- **Entregas:** entrada controlada, extração textual e vínculo com a fonte.
- **Dependências:** F-002.2.

### F-003.2 — Segmentação e classificação estrutural

- **Prioridade:** Must
- **Valor:** preserva capítulos, seções e tipos de bloco antes da destilação.
- **Entregas:** seção, página, tipo de bloco, ordem e estado de revisão.
- **Dependências:** F-003.1.

## EPIC-004 — Componentes pedagógicos semielaborados

### F-004.1 — Esquema canônico de componente pedagógico

- **Prioridade:** Must
- **Valor:** estabelece uma unidade reutilizável sem transformar a fonte em produto pronto.
- **Entregas:** conteúdo autoral, metadados pedagógicos, procedência, licença, versão e status.
- **Dependências:** F-003.2.

### F-004.2 — Tipologia mínima do piloto

- **Prioridade:** Must
- **Valor:** garante variedade suficiente para plano, texto, atividade e avaliação.
- **Entregas:** conceito, contexto, problema filosófico, metodologia, atividade-base, avaliação e inclusão.
- **Dependências:** F-004.1.

### F-004.3 — Ciclo de revisão e versionamento

- **Prioridade:** Must
- **Valor:** impede recuperação de rascunhos ou componentes reprovados.
- **Entregas:** rascunho, em revisão, aprovado, reprovado, substituído e histórico.
- **Dependências:** F-004.1.

## EPIC-005 — Destilação e deduplicação

### F-005.1 — Destilação autoral rastreável

- **Prioridade:** Must
- **Valor:** transforma contribuições de fontes em conhecimento pedagógico próprio.
- **Entregas:** síntese autoral, contribuições utilizadas e revisão humana.
- **Dependências:** F-004.1 e F-002.2.

### F-005.2 — Consolidação e duplicidade básica

- **Prioridade:** Must
- **Valor:** reduz repetição no almoxarifado e no contexto do agente.
- **Entregas:** comparação, sugestão de unidade canônica, vínculo e decisão humana.
- **Dependências:** F-005.1.

## EPIC-006 — Pacotes curriculares plugáveis

### F-006.1 — Pacote curricular MG do piloto

- **Prioridade:** Must
- **Valor:** fornece o recorte curricular obrigatório ao Sócrates 2.
- **Entregas:** versão, vigência, etapa, ano, componente, habilidades e objetos aplicáveis.
- **Dependências:** F-001.1.

### F-006.2 — Vínculo componente–currículo

- **Prioridade:** Must
- **Valor:** permite recuperar matéria-prima compatível com a intenção curricular.
- **Entregas:** vínculos, justificativa, confiança e validação humana.
- **Dependências:** F-004.3 e F-006.1.

## EPIC-007 — Almoxarifado e busca híbrida

### F-007.1 — Filtros pedagógicos e jurídicos obrigatórios

- **Prioridade:** Must
- **Valor:** restringe o universo antes da busca semântica.
- **Entregas:** componente, etapa, ano, currículo, tipo, licença e status.
- **Dependências:** F-002.2, F-004.3 e F-006.2.

### F-007.2 — Busca textual e vetorial com fusão simples

- **Prioridade:** Must
- **Valor:** recupera proximidade lexical e semântica sem busca global irrestrita.
- **Entregas:** candidatos, pontuações, fusão, limite e justificativa de seleção.
- **Dependências:** F-007.1.

### F-007.3 — Suficiência e fallback de conhecimento

- **Prioridade:** Must
- **Valor:** evita que o agente improvise quando o estoque não sustenta o pedido.
- **Entregas:** limiar inicial, sinalização de insuficiência, recusa ou pedido de ajuste.
- **Dependências:** F-007.2.

## EPIC-008 — Orquestração multiagente

### F-008.1 — Roteamento pedagógico para Sócrates 2

- **Prioridade:** Must
- **Valor:** encaminha somente pedidos compatíveis ao perfil especialista.
- **Entregas:** classificação de componente, etapa, ano, Estado, produto e agente.
- **Dependências:** F-006.1 e F-007.1.

### F-008.2 — Coordenação de validadores lógicos

- **Prioridade:** Must
- **Valor:** mantém autoria principal no Sócrates 2 e aciona gates especializados.
- **Entregas:** sequência, entradas, saídas, estados e registro dos validadores.
- **Dependências:** F-008.1.

## EPIC-009 — Agente Sócrates 2

### F-009.1 — Perfil operacional e limites

- **Prioridade:** Must
- **Valor:** transforma o nome do agente em um contrato executável e testável.
- **Entregas:** identidade, escopo, acessos, bloqueios, ferramentas e fallback.
- **Dependências:** F-008.1.

### F-009.2 — Produção dos quatro produtos mínimos

- **Prioridade:** Must
- **Valor:** comprova utilidade pedagógica em formatos diferentes.
- **Entregas:** plano de aula, texto didático, atividade reflexiva e avaliação formativa curta.
- **Dependências:** F-009.1 e F-007.3.

### F-009.3 — Pacote integrado de aula

- **Prioridade:** Should
- **Valor:** testa coerência entre produtos produzidos para o mesmo pedido.
- **Entregas:** conjunto com objetivos, texto, atividade e avaliação relacionados.
- **Dependências:** F-009.2.

## EPIC-010 — Ordem de Produção Pedagógica

### F-010.1 — Criação e validação da OPP

- **Prioridade:** Must
- **Valor:** transforma o pedido do professor em instrução estruturada.
- **Entregas:** contexto, produto, currículo, tema, duração, metodologia, inclusão e entregáveis.
- **Dependências:** F-008.1.

### F-010.2 — Linha do tempo e auditoria da produção

- **Prioridade:** Must
- **Valor:** permite reconstruir como o produto foi gerado.
- **Entregas:** estados, agentes, componentes, validações, versões, falhas e resultado.
- **Dependências:** F-010.1 e F-008.2.

## EPIC-011 — Geração autoral e personalização

### F-011.1 — Planejamento interno antes da redação

- **Prioridade:** Must
- **Valor:** reduz colagem de fragmentos e melhora coerência didática.
- **Entregas:** objetivo, estrutura, seleção de componentes e estratégia de composição.
- **Dependências:** F-010.1 e F-007.2.

### F-011.2 — Personalização por contexto da turma

- **Prioridade:** Must
- **Valor:** evita produto genérico ou enlatado.
- **Entregas:** duração, nível de leitura, metodologia, recursos, perfil e necessidade inclusiva.
- **Dependências:** F-011.1.

### F-011.3 — Variações controladas

- **Prioridade:** Should
- **Valor:** demonstra criatividade sem perder currículo e rastreabilidade.
- **Entregas:** alternativas metodológicas ou de atividade com invariantes registrados.
- **Dependências:** F-011.2.

## EPIC-012 — Qualidade pedagógica, curricular e factual

### F-012.1 — Gate curricular e conceitual

- **Prioridade:** Must
- **Valor:** impede entrega fora do currículo ou com erro filosófico relevante.
- **Entregas:** alinhamento, conceitos, evidências, aprovação ou retorno.
- **Dependências:** F-006.2 e F-009.2.

### F-012.2 — Gate de coerência pedagógica

- **Prioridade:** Must
- **Valor:** verifica relação entre objetivo, conteúdo, atividade e avaliação.
- **Entregas:** coerência, duração, clareza, adequação escolar e correção solicitada.
- **Dependências:** F-009.2 e F-011.2.

### F-012.3 — Revisão humana amostral

- **Prioridade:** Should
- **Valor:** valida se os gates automáticos correspondem ao julgamento docente.
- **Entregas:** parecer, divergência, decisão e aprendizado registrado.
- **Dependências:** F-012.1 e F-012.2.

## EPIC-013 — Guardião autoral e rastreabilidade

### F-013.1 — Verificação lexical e bloqueios autorais

- **Prioridade:** Must
- **Valor:** reduz reprodução extensa e uso indevido de atividades ou questões.
- **Entregas:** similaridade, trechos sinalizados, decisão, bloqueio e regeneração.
- **Dependências:** F-005.1 e F-009.2.

### F-013.2 — Registro de linhagem do produto

- **Prioridade:** Must
- **Valor:** relaciona o produto aos componentes e fontes sem expor conteúdo restrito.
- **Entregas:** IDs, versões, contribuições, currículo e validações.
- **Dependências:** F-010.2 e F-013.1.

## EPIC-014 — Inclusão e acessibilidade

### F-014.1 — Requisitos inclusivos na origem do pedido

- **Prioridade:** Must
- **Valor:** incorpora inclusão no processo, não apenas no acabamento.
- **Entregas:** necessidades, preferências, alternativas e critérios na OPP.
- **Dependências:** F-010.1.

### F-014.2 — Gate inclusivo mínimo

- **Prioridade:** Must
- **Valor:** verifica linguagem, segmentação, alternativas e carga textual solicitada.
- **Entregas:** checklist, evidências, aprovação ou retorno.
- **Dependências:** F-014.1 e F-009.2.

## EPIC-015 — Contrato de entrega

### F-015.1 — Contrato estruturado de produto pedagógico

- **Prioridade:** Must
- **Valor:** separa conteúdo validado de diagramação futura.
- **Entregas:** metadados, conteúdo do professor, conteúdo do estudante, atividades, avaliação e referências internas.
- **Dependências:** F-012.2, F-013.2 e F-014.2.

### F-015.2 — Pré-requisitos visuais e de acessibilidade

- **Prioridade:** Should
- **Valor:** prepara a futura Gráfica sem implementá-la no MVP.
- **Entregas:** estrutura, hierarquia, requisitos visuais, formato desejado e restrições.
- **Dependências:** F-015.1.

## EPIC-016 — Observabilidade, tokens, custo e latência

### F-016.1 — Telemetria do fluxo do MVP

- **Prioridade:** Must
- **Valor:** permite localizar gargalos e comparar execuções.
- **Entregas:** duração por etapa, status, erros, recuperação, modelo e versões.
- **Dependências:** F-010.2.

### F-016.2 — Contabilidade de tokens e custo

- **Prioridade:** Must
- **Valor:** testa a hipótese de eficiência da especialização.
- **Entregas:** tokens de entrada e saída por etapa, custo estimado e totais por OPP.
- **Dependências:** F-016.1.

## EPIC-017 — Avaliação do piloto

### F-017.1 — Casos dourados e baseline genérico

- **Prioridade:** Must
- **Valor:** mede benefício real da arquitetura especializada.
- **Entregas:** pedidos equivalentes, rubrica, resultados e comparação.
- **Dependências:** todas as Features Must anteriores.

### F-017.2 — Avaliação docente e decisão de continuidade

- **Prioridade:** Must
- **Valor:** impede expansão baseada apenas em métricas técnicas.
- **Entregas:** amostras, pareceres, consolidação, decisão de avançar, ajustar ou interromper.
- **Dependências:** F-017.1.

## EPIC-018 — Expansão

### F-018.1 — Pacote RS e novos agentes

- **Prioridade:** Won't no MVP
- **Motivo:** somente poderá entrar após decisão formal de continuidade no EPIC-017.
