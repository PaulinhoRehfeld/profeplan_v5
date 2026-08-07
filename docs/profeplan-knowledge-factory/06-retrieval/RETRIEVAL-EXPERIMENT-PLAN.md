# Plano de Experimentos de Recuperação

## Status

Proposta do Marco 003. Nenhum modelo, dimensão, índice, reranker ou cache é aprovado antecipadamente.

## Pergunta central

Qual configuração recupera o conjunto mais útil e seguro de componentes do Sócrates 2, respeitando filtros, orçamento de contexto, latência e custo?

## Hipóteses

- H1: filtros determinísticos reduzem drasticamente falsos positivos de escopo;
- H2: busca híbrida supera lexical e semântica isoladas em consultas variadas;
- H3: um reranker só se justifica se elevar a relevância de forma material sem custo/latência desproporcionais;
- H4: componentes semielaborados exigem menos tokens do que chunks brutos para qualidade igual ou superior;
- H5: um corpus pequeno e curado permite índices simples antes de otimização avançada;
- H6: cache não traz benefício suficiente no piloto sem repetição mensurável.

## Dataset de avaliação

### Tamanho inicial

Entre 80 e 120 consultas, distribuídas pelos oito temas aprovados.

### Classes de consulta

- conceito explícito;
- formulação cotidiana;
- pergunta filosófica;
- autor ou tradição;
- pedido metodológico;
- atividade;
- avaliação;
- necessidade inclusiva;
- consulta interdisciplinar controlada;
- consulta fora do escopo;
- consulta sem base suficiente;
- consulta adversarial com termo semelhante de outra disciplina.

### Hard negatives

- Filosofia do 1º e 3º anos;
- Sociologia do 2º ano;
- Ensino Religioso;
- currículo RS;
- fonte bloqueada;
- versão substituída;
- componente duplicado;
- material sem vínculo curricular quando exigido;
- texto bruto semanticamente semelhante, porém não publicável.

### Julgamento de relevância

Cada consulta deve ter:

- componentes essenciais;
- componentes relevantes opcionais;
- componentes aceitáveis;
- componentes irrelevantes;
- componentes proibidos;
- justificativa pedagógica;
- revisor responsável.

Pelo menos uma amostra crítica deverá ter dupla revisão e resolução de divergência.

## Baselines

### B0 — Sem retrieval especializado

Agente genérico recebe somente pedido e currículo mínimo. Mede qualidade, tokens e alucinação sem almoxarifado.

### B1 — Busca lexical filtrada

PostgreSQL full-text ou mecanismo equivalente, sem embedding.

### B2 — Busca semântica filtrada

Uma configuração de embedding por execução experimental.

### B3 — Híbrida sem reranker

Fusão lexical + semântica.

### B4 — Híbrida com reranker

Somente se B3 indicar margem de melhoria e o custo for justificável.

## Candidatos de embedding

A seleção será feita após levantar opções compatíveis com:

- português brasileiro;
- textos educacionais e filosóficos;
- custo de indexação e consulta;
- dimensão suportável no Supabase/PostgreSQL;
- disponibilidade e estabilidade do provedor;
- política de dados;
- capacidade de versionamento;
- latência;
- qualidade no dataset.

Para cada candidato registrar:

- provider;
- modelo;
- dimensão nativa e possíveis reduções oficialmente suportadas;
- preço de indexação e consulta;
- limites;
- política de retenção;
- data da avaliação;
- versão do SDK;
- resultado nas métricas.

A dimensão 768 existente no RAG curricular é evidência histórica, não decisão automática.

## Estratégias de índice

Para 100–300 componentes, comparar primeiro:

- busca exata sem índice aproximado, quando viável;
- HNSW;
- IVFFlat somente se houver justificativa de volume e treinamento adequado.

O piloto não deve otimizar para milhões de vetores antes de medir o corpus real.

## Fusão

Comparar:

- RRF com parâmetros simples;
- soma de scores normalizados;
- pesos lexical/semântico;
- regras por classe de consulta.

## Reranker

Comparar somente após B3:

- nenhum;
- regras determinísticas;
- reranker dedicado;
- LLM estruturado.

Critério de adoção: ganho consistente em nDCG/MRR e avaliação humana que compense custo e p95.

## Métricas

### Integridade

- vazamento de escopo: alvo 0%;
- fonte bloqueada recuperada: alvo 0;
- versão inelegível recuperada: alvo 0;
- pacote estadual incorreto: alvo 0.

### Relevância

- Recall@3, Recall@5 e Recall@8;
- Precision@k;
- MRR;
- nDCG@k;
- cobertura de componente essencial;
- taxa de contexto insuficiente corretamente detectado;
- taxa de falso suficiente.

### Eficiência

- latência p50, p90 e p95 por etapa;
- custo por consulta;
- tokens do context package;
- tamanho médio do pacote;
- taxa de duplicidade removida;
- taxa de fallback.

### Qualidade downstream

- nota pedagógica do produto;
- alinhamento curricular;
- correção filosófica;
- originalidade;
- necessidade de revisão humana;
- comparação com baseline genérico.

## Critérios mínimos para configuração candidata

Uma configuração não poderá ser recomendada se:

- violar qualquer filtro obrigatório;
- recuperar fonte bloqueada;
- aumentar falsos suficientes;
- elevar custo sem ganho relevante;
- depender de contexto superior ao orçamento;
- não permitir reprodução do experimento;
- não registrar provider, modelo, dimensão e versão.

## Desenho de execução

1. congelar versão do corpus;
2. congelar dataset de consultas;
3. gerar embeddings por configuração;
4. executar baselines;
5. coletar métricas automáticas;
6. realizar julgamento humano em amostra cega;
7. comparar relevância, segurança, custo e latência;
8. registrar decisão;
9. repetir em dataset de regressão antes de alteração futura.

## Controle de viés

- não criar consultas somente a partir dos termos exatos dos componentes;
- incluir linguagem real de professor;
- separar quem configura de quem julga uma amostra;
- não excluir falhas sem motivo registrado;
- reportar intervalos e distribuição, não apenas média;
- preservar resultados negativos.

## Experimentos de orçamento

Comparar context packages de:

- 3 componentes;
- 5 componentes;
- 8 componentes;
- seleção por tokens em vez de quantidade fixa.

Medir quando itens adicionais deixam de melhorar o produto ou aumentam confusão.

## Experimento de chunk bruto versus componente

Em amostra controlada:

- recuperar chunks brutos autorizados;
- recuperar componentes semielaborados equivalentes;
- usar o mesmo pedido e modelo gerador;
- comparar tokens, autoria, precisão e utilidade.

Esse experimento demonstra o valor central da Knowledge Factory.

## Cache

Somente realizar experimento de cache após observar:

- repetição de consultas ou QueryPlans;
- custo significativo evitável;
- regras de invalidação definidas;
- ausência de risco de vazamento.

## Artefatos de evidência

- manifesto do corpus;
- dataset versionado;
- configurações;
- scripts reproduzíveis;
- resultados brutos;
- relatório comparativo;
- decisão de arquitetura;
- limitações.

## Decisão proposta

**ADR-021 — Escolhas de embedding, dimensão, índice, fusão, reranker e cache são experiment-gated.**

Status: proposta, aguardando aprovação.
