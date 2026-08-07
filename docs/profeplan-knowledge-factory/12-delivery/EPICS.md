# Mapa de Epics — ProfePlan Knowledge Factory

## Objetivo

Organizar a construção da Knowledge Factory em capacidades de produto e arquitetura, evitando iniciar tarefas técnicas antes de definir valor pedagógico, escopo, dependências e critérios de conclusão.

## Classificação de fases

- **Fase 0 — Fundação documental:** decisões, contratos e critérios antes do código.
- **Fase 1 — MVP Sócrates 2:** fluxo mínimo completo e validável para Filosofia do 2º ano do Ensino Médio, currículo de Minas Gerais.
- **Fase 2 — Consolidação:** robustez, automação, Rio Grande do Sul, autoria e qualidade ampliadas.
- **Fase 3 — Escala:** novos componentes, anos, Estados e formatos de entrega.

## Regra de priorização

O MVP deverá validar o ciclo completo:

`fonte autorizada → componente pedagógico → currículo → recuperação → Sócrates 2 → produto autoral → validação → entrega`

Não será considerado MVP um conjunto de partes isoladas que não produza uma resposta pedagógica rastreável de ponta a ponta.

---

## EPIC-001 — Governança e fundação arquitetônica

**Fase:** 0  
**Prioridade:** obrigatória antes do código

### Objetivo

Estabelecer escopo, terminologia, decisões, papéis, critérios de prontidão e limites arquitetônicos da Knowledge Factory.

### Valor

Evita que o Codex ou a equipe técnica implementem uma solução genérica de RAG desconectada do ProfePlan.

### Capacidades

- Project Charter;
- escopo educacional;
- princípios;
- Decision Log;
- glossário;
- política de continuidade e forks;
- Definition of Ready e Definition of Done;
- governança de mudanças.

### Critério de conclusão

As decisões essenciais do MVP estão aprovadas, versionadas e sem contradições documentais relevantes.

---

## EPIC-002 — Governança das fontes e direitos de uso

**Fase:** 1  
**Prioridade:** crítica

### Objetivo

Registrar cada fonte, sua procedência, versão, titularidade, finalidade permitida e restrições antes de utilizá-la na geração.

### Valor

Protege a WR Tech contra uso indevido de obras e garante rastreabilidade das matérias-primas.

### Capacidades do MVP

- cadastro de fonte;
- classificação de licença;
- status de autorização para geração;
- checksum e identificação de duplicidade;
- referência a obra, edição, capítulo e páginas;
- bloqueio de fontes não autorizadas.

### Não incluído no MVP

- negociação automatizada com editoras;
- gestão financeira de royalties;
- portal externo para titulares.

### Dependências

EPIC-001.

### Critério de conclusão

Nenhum componente utilizado pelo Sócrates 2 pode existir sem origem e permissão registradas.

---

## EPIC-003 — Ingestão e leitura estrutural das fontes

**Fase:** 1, com automação ampliada na Fase 2  
**Prioridade:** alta

### Objetivo

Transformar fontes autorizadas em conteúdo estruturalmente identificável, preservando capítulos, seções, tipos de bloco e localização de origem.

### Capacidades do MVP

- ingestão controlada de pequeno conjunto piloto;
- extração textual;
- registro de capítulos e seções;
- classificação inicial de blocos;
- vínculo com a fonte;
- revisão humana antes da publicação.

### Estratégia do MVP

A ingestão poderá ser assistida ou semiautomática. O objetivo inicial não é processar dezenas de coleções, mas validar a qualidade da transformação.

### Não incluído no MVP

- processamento massivo;
- OCR industrial;
- interpretação completa de todas as imagens e diagramas;
- filas de ingestão em grande escala.

### Dependências

EPIC-002.

### Critério de conclusão

O conjunto piloto pode ser processado e auditado sem perder sua procedência estrutural.

---

## EPIC-004 — Modelo de componentes pedagógicos semielaborados

**Fase:** 1  
**Prioridade:** crítica

### Objetivo

Definir e armazenar as matérias-primas pedagógicas que serão recuperadas pelos agentes.

### Valor

Impede que a IA trabalhe apenas com páginas brutas ou planos prontos, preservando eficiência e criatividade.

### Capacidades do MVP

- tipos de componente;
- conteúdo autoral estruturado;
- componente, etapa e ano;
- tema e conceitos;
- finalidades pedagógicas;
- nível cognitivo;
- vínculos curriculares;
- procedência;
- licença;
- status de revisão;
- versão;
- campos destinados a embeddings.

### Tipos mínimos do piloto

- conceitual;
- contextualização;
- problema filosófico;
- estratégia metodológica;
- atividade-base;
- avaliação formativa;
- orientação inclusiva.

### Dependências

EPIC-002 e EPIC-003.

### Critério de conclusão

O piloto possui componentes suficientes para gerar materiais sem recorrer diretamente a capítulos inteiros durante a resposta.

---

## EPIC-005 — Destilação, consolidação e deduplicação do conhecimento

**Fase:** 1, amadurecimento na Fase 2  
**Prioridade:** crítica

### Objetivo

Converter contribuições das fontes em unidades autorais, consolidadas e não redundantes.

### Capacidades do MVP

- síntese autoral;
- comparação entre fontes;
- registro de contribuições;
- detecção básica de duplicidade;
- unidade canônica por conceito;
- preservação de divergências relevantes;
- revisão humana do conjunto piloto.

### Não incluído no MVP

- consolidação automática irrestrita;
- publicação automática sem revisão;
- resolução autônoma de controvérsias acadêmicas.

### Dependências

EPIC-004.

### Critério de conclusão

Os componentes do piloto são utilizáveis sem reproduzir a estrutura ou redação de uma única obra como resposta final.

---

## EPIC-006 — Pacotes curriculares plugáveis

**Fase:** MG na Fase 1; RS na Fase 2  
**Prioridade:** crítica

### Objetivo

Disponibilizar currículos nacionais e estaduais como pacotes versionados, sem duplicar agentes.

### Capacidades do MVP

- pacote BNCC aplicável;
- pacote Minas Gerais;
- metadados de versão e vigência;
- estrutura por etapa, ano e componente;
- vínculos entre habilidades e componentes pedagógicos;
- seleção de um currículo estadual principal;
- proibição de mistura silenciosa entre Estados.

### Fase 2

- pacote Rio Grande do Sul;
- testes de equivalência e diferenças;
- modo comparativo explícito.

### Dependências

EPIC-001 e EPIC-004.

### Critério de conclusão do MVP

Sócrates 2 recupera apenas o recorte curricular de Filosofia do 2º ano de Minas Gerais necessário à solicitação.

---

## EPIC-007 — Almoxarifado inteligente e busca híbrida

**Fase:** 1  
**Prioridade:** crítica

### Objetivo

Recuperar poucos componentes pertinentes, aplicando restrições estruturadas antes da similaridade semântica.

### Capacidades do MVP

- filtros por componente, etapa e ano;
- filtro por currículo ativo;
- filtro por tipo de componente;
- filtro por licença e autorização;
- filtro por status de validação;
- busca textual e vetorial;
- limite de resultados;
- registro dos componentes recuperados;
- pontuação de relevância;
- fallback quando não houver conhecimento suficiente.

### Não incluído no MVP

- busca global irrestrita;
- múltiplas estratégias avançadas de reranqueamento;
- cache distribuído complexo;
- recuperação entre todos os componentes curriculares.

### Dependências

EPIC-004, EPIC-005 e EPIC-006.

### Critério de conclusão

Consultas do piloto recuperam conjuntos pequenos e corretos sem mistura de disciplina, etapa, ano ou Estado.

---

## EPIC-008 — Orquestração multiagente e roteamento pedagógico

**Fase:** 1  
**Prioridade:** alta

### Objetivo

Interpretar a solicitação, selecionar o perfil especializado e coordenar agentes auxiliares somente quando necessário.

### Capacidades do MVP

- roteamento para Sócrates 2;
- definição do agente principal;
- acesso controlado a validadores;
- contrato de comunicação entre agentes;
- proibição de pesquisa global pelo agente;
- fallback para pedido fora do escopo;
- registro da sequência de execução.

### Estratégia do MVP

O sistema pode começar com poucos papéis lógicos sobre infraestrutura comum. Não é necessário criar dezenas de agentes executáveis independentes.

### Dependências

EPIC-001 e EPIC-007.

### Critério de conclusão

Uma solicitação válida de Filosofia do 2º ano é encaminhada ao Sócrates 2 com o pacote curricular e o escopo corretos.

---

## EPIC-009 — Agente piloto Sócrates 2

**Fase:** 1  
**Prioridade:** crítica

### Objetivo

Produzir materiais de Filosofia para o 2º ano do Ensino Médio utilizando componentes autorizados, currículo ativo e contexto do professor.

### Capacidades do MVP

- identidade e limites de atuação;
- linguagem adequada à etapa;
- repertório filosófico do piloto;
- problematização filosófica;
- construção de objetivos e metodologia;
- criação de conteúdo autoral;
- uso de contexto de turma e duração;
- solicitação de apoio aos validadores;
- recusa ou sinalização quando faltar base suficiente.

### Produtos mínimos do piloto

- plano de aula;
- texto didático curto ou médio;
- atividade reflexiva;
- instrumento de avaliação formativa.

### Não incluído no MVP

- todos os tipos de planejamento do ProfePlan;
- Filosofia do 1º e 3º anos;
- integração irrestrita com outras disciplinas;
- produção massiva em lote.

### Dependências

EPIC-006, EPIC-007 e EPIC-008.

### Critério de conclusão

Sócrates 2 produz um conjunto coerente de materiais que possa ser avaliado por professor especialista e rastreado até seus componentes.

---

## EPIC-010 — Ordem de Produção Pedagógica

**Fase:** 1  
**Prioridade:** alta

### Objetivo

Representar o pedido do professor e acompanhar todas as etapas de produção, validação e entrega.

### Capacidades do MVP

- identificação do pedido;
- professor, etapa, ano e componente;
- currículo ativo;
- tipo de produto;
- tema, duração e metodologia;
- requisitos de inclusão;
- entregáveis;
- agentes participantes;
- status de produção;
- componentes recuperados;
- validações realizadas;
- versão do produto.

### Dependências

EPIC-008 e EPIC-009.

### Critério de conclusão

Cada produto piloto possui uma Ordem de Produção Pedagógica auditável do pedido até a entrega.

---

## EPIC-011 — Geração autoral e personalização

**Fase:** 1  
**Prioridade:** crítica

### Objetivo

Combinar componentes semielaborados e contexto do professor em produtos novos, coerentes e não enlatados.

### Capacidades do MVP

- planejamento antes da redação;
- síntese multifonte;
- adaptação por duração;
- adequação à etapa e ao ano;
- metodologia solicitada;
- nível de leitura;
- recursos disponíveis;
- geração de variações controladas;
- separação entre conteúdo do professor e do estudante.

### Dependências

EPIC-009 e EPIC-010.

### Critério de conclusão

Pedidos semelhantes com contextos diferentes produzem materiais coerentemente diferentes, mantendo o mesmo rigor curricular.

---

## EPIC-012 — Qualidade pedagógica, curricular e factual

**Fase:** 1  
**Prioridade:** crítica

### Objetivo

Impedir a entrega de materiais incoerentes, inadequados ao currículo ou conceitualmente frágeis.

### Capacidades do MVP

- validação curricular;
- coerência entre objetivo, atividade e avaliação;
- adequação ao tempo;
- adequação à faixa escolar;
- clareza de comandos;
- verificação factual e conceitual;
- identificação de lacunas;
- aprovação, reprovação ou retorno para correção.

### Dependências

EPIC-009 e EPIC-011.

### Critério de conclusão

Nenhum produto é entregue sem registrar o resultado dos gates mínimos de qualidade.

---

## EPIC-013 — Guardião autoral e rastreabilidade

**Fase:** 1, aprofundamento na Fase 2  
**Prioridade:** crítica

### Objetivo

Reduzir reprodução indevida e registrar como o produto foi fundamentado.

### Capacidades do MVP

- comparação lexical básica com fontes recuperadas;
- detecção de sequências excessivamente semelhantes;
- bloqueio de reprodução integral de atividades e questões;
- registro das fontes e componentes utilizados;
- aviso de risco;
- regeneração quando necessário.

### Fase 2

- análise semântica de proximidade estrutural;
- políticas diferenciadas por categoria de fonte;
- painéis de auditoria.

### Dependências

EPIC-002, EPIC-005 e EPIC-011.

### Critério de conclusão

O produto piloto apresenta rastreabilidade interna e não contém reprodução extensa detectável das fontes usadas.

---

## EPIC-014 — Inclusão e acessibilidade pedagógica

**Fase:** núcleo mínimo na Fase 1; ampliação na Fase 2  
**Prioridade:** alta

### Objetivo

Incorporar acessibilidade e inclusão desde a ordem de produção, e não apenas adaptar o produto ao final.

### Capacidades do MVP

- instruções segmentadas;
- alternativas de resposta;
- redução de carga textual quando solicitada;
- apoio visual descrito;
- critérios de linguagem clara;
- registro dos requisitos inclusivos na OPP;
- validação de cumprimento.

### Não incluído no MVP

- geração completa de PDI;
- biblioteca abrangente por diagnóstico;
- substituição de avaliação profissional;
- todas as tecnologias assistivas.

### Dependências

EPIC-010, EPIC-011 e EPIC-012.

### Critério de conclusão

O piloto consegue aplicar pelo menos um conjunto explícito de requisitos inclusivos e demonstrar sua presença no produto.

---

## EPIC-015 — Contrato de entrega e Gráfica

**Fase:** contrato mínimo na Fase 1; automação editorial na Fase 2  
**Prioridade:** média no MVP

### Objetivo

Separar conteúdo pedagógico validado de sua apresentação e exportação final.

### Capacidades do MVP

- contrato estruturado de saída;
- blocos do produto identificados;
- distinção entre material do professor e do estudante;
- versão textual ou estruturada utilizável no ProfePlan;
- indicação de requisitos de acessibilidade e formato.

### Não incluído no MVP

- geração avançada de PDF e PPTX;
- múltiplos temas visuais;
- infográficos automáticos complexos;
- acabamento editorial industrial.

### Dependências

EPIC-011, EPIC-012 e EPIC-014.

### Critério de conclusão

O conteúdo validado é entregue em contrato estável que a futura Gráfica possa consumir sem reinterpretar o mérito pedagógico.

---

## EPIC-016 — Observabilidade, tokens, custo e latência

**Fase:** 1  
**Prioridade:** alta

### Objetivo

Medir se a arquitetura especializada realmente reduz ruído, tokens, custo e tempo de resposta.

### Capacidades do MVP

- tokens por etapa;
- componentes recuperados;
- duração da recuperação;
- duração da geração;
- modelo utilizado;
- falhas e retries;
- orçamento por agente;
- custo estimado por produção;
- comparação com baseline genérico.

### Dependências

Todos os Epics executáveis do MVP.

### Critério de conclusão

O piloto produz métricas suficientes para decidir se a arquitetura deve ser mantida, ajustada ou simplificada.

---

## EPIC-017 — Avaliação do piloto Sócrates 2

**Fase:** 1  
**Prioridade:** obrigatória para encerrar o MVP

### Objetivo

Avaliar qualidade, precisão, originalidade, custo, latência e utilidade para professores reais.

### Capacidades do MVP

- conjunto de perguntas douradas;
- casos esperados;
- casos de falha;
- rubrica pedagógica;
- avaliação curricular;
- avaliação de autoria;
- testes de isolamento por disciplina, ano e Estado;
- feedback de professores;
- relatório de go/no-go.

### Dependências

EPIC-009 a EPIC-016.

### Critério de conclusão

Existe evidência documentada de que o piloto entrega valor e uma decisão explícita sobre expansão.

---

## EPIC-018 — Expansão para RS, novos agentes e componentes

**Fase:** 2 e 3  
**Prioridade:** posterior ao piloto

### Objetivo

Replicar a infraestrutura validada sem duplicar código ou criar agentes isolados por Estado.

### Capacidades futuras

- pacote curricular RS;
- Filosofia 1 e 3;
- Sociologia;
- demais componentes do Ensino Médio;
- componentes do Ensino Fundamental II;
- novos Estados;
- novas categorias de produto;
- Gráfica avançada;
- processamento de acervo em escala.

### Dependências

EPIC-017 aprovado com decisão de expansão.

### Critério de início

Não deverá começar antes da conclusão e avaliação do MVP Sócrates 2.

---

## Recorte oficial do MVP

### Epics integralmente incluídos

- EPIC-001 — Governança e fundação arquitetônica;
- EPIC-002 — Governança das fontes;
- EPIC-004 — Componentes pedagógicos;
- EPIC-006 — Pacote curricular MG;
- EPIC-007 — Busca híbrida;
- EPIC-008 — Orquestração e roteamento;
- EPIC-009 — Sócrates 2;
- EPIC-010 — Ordem de Produção Pedagógica;
- EPIC-011 — Geração autoral;
- EPIC-012 — Qualidade;
- EPIC-016 — Observabilidade;
- EPIC-017 — Avaliação do piloto.

### Epics incluídos em versão mínima

- EPIC-003 — ingestão assistida de conjunto pequeno;
- EPIC-005 — destilação e deduplicação com revisão humana;
- EPIC-013 — controle autoral básico e rastreabilidade;
- EPIC-014 — inclusão básica orientada por requisitos;
- EPIC-015 — contrato de entrega, sem Gráfica avançada.

### Fora do MVP

- currículo do Rio Grande do Sul em produção;
- outros agentes curriculares;
- processamento massivo de PNLD;
- Gráfica automatizada avançada;
- PDI completo;
- integrações amplas com outros módulos;
- execução multiestado simultânea;
- expansão nacional.

## Ordem macro de execução

```mermaid
flowchart LR
    A[Governança] --> B[Fontes e permissões]
    B --> C[Ingestão piloto]
    C --> D[Componentes pedagógicos]
    D --> E[Destilação e revisão]
    E --> F[Currículo MG]
    F --> G[Busca híbrida]
    G --> H[Orquestração]
    H --> I[Sócrates 2]
    I --> J[OPP e geração autoral]
    J --> K[Qualidade, inclusão e autoria]
    K --> L[Contrato de entrega]
    L --> M[Métricas e avaliação]
```

## Decisão pendente para aprovação humana

A estrutura propõe que a Gráfica avançada não faça parte do MVP. O MVP validará um contrato estruturado de entrega; PDF, PPTX e diagramação industrial entrarão após a prova de qualidade da fábrica de conhecimento.
