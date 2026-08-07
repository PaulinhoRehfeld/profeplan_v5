# Registro de Riscos Técnicos — MVP Sócrates 2

## Status

Proposta do Marco 003. Probabilidade e impacto serão revisados a cada onda.

## Escala

- Probabilidade: Baixa, Média, Alta.
- Impacto: Baixo, Médio, Alto, Crítico.
- Prioridade: combinação qualitativa, com riscos críticos tratados como gates.

## Riscos

| ID | Risco | Prob. | Impacto | Mitigação | Gatilho/indicador |
|---|---|---:|---:|---|---|
| R-001 | implementação no repositório errado | Alta | Crítico | decidir repositório canônico antes do código | PR criado em repo sem monorepo |
| R-002 | duas fontes documentais concorrentes | Alta | Alto | sincronizar e definir fonte de verdade | divergência de ADR/Story |
| R-003 | duplicar capacidades já existentes | Média | Alto | inventário e adapter-first | novo módulo repete agents/curriculum |
| R-004 | reutilizar legado incompatível sem testes | Alta | Alto | contract tests e casos dourados | gate existente passa caso incorreto |
| R-005 | uso comercial de fonte sem permissão | Média | Crítico | catálogo, bloqueio por padrão, revisão jurídica | `unknown` chega ao retrieval |
| R-006 | revogação não propaga aos derivados | Média | Crítico | lineage e invalidação | produto novo usa fonte suspensa |
| R-007 | corpus piloto pobre ou enviesado | Alta | Alto | 100–300 componentes balanceados e revisados | temas/tipos sem cobertura |
| R-008 | componente vira material enlatado | Média | Alto | contrato semielaborado e avaliação de variação | respostas repetitivas |
| R-009 | destilação reproduz obra | Média | Crítico | autoria gate e revisão | sobreposição/estrutura excessiva |
| R-010 | currículo MG desatualizado ou recortado errado | Média | Crítico | pacote versionado e revisão especialista | código/nó não confirmado |
| R-011 | mistura de Estado, ano ou disciplina | Média | Crítico | filtros prévios + RLS/policy + hard negatives | candidato proibido no retrieval |
| R-012 | dimensão/modelo de embedding escolhidos por legado | Alta | Alto | experimento comparativo | decisão menciona apenas compatibilidade |
| R-013 | índice aproximado piora resultado em corpus pequeno | Média | Médio | comparar busca exata/HNSW/IVFFlat | Recall cai sem ganho de p95 |
| R-014 | reranker aumenta custo sem valor | Média | Alto | adotar apenas por ganho material | custo/p95 sobe e nDCG não |
| R-015 | falso estado de suficiência | Média | Crítico | critérios múltiplos e casos sem base | produto convincente sem evidência |
| R-016 | excesso de contexto/tokens | Alta | Alto | budget, máximo 8, medir 3/5/8 | crescimento sem ganho de qualidade |
| R-017 | retry em loop | Média | Alto | limite, códigos não-retryable | custo anormal por OPP |
| R-018 | dependência direta de provider nos agentes | Média | Alto | ModelPolicy e adapters | código do agente importa SDK |
| R-019 | mudança de preço/modelo quebra viabilidade | Média | Alto | tabela versionada e fallback | custo por OPP ultrapassa limite |
| R-020 | latência inviável | Média | Alto | spans, pipeline mínimo, reranker opcional | p95 impede uso em aula |
| R-021 | RLS incorreta ou recursiva | Média | Crítico | matriz, testes multi-tenant e revisão SQL | acesso cruzado/erro de política |
| R-022 | abuso de service role | Média | Crítico | backend-only, jobs restritos, auditoria | operação global sem filtro |
| R-023 | dados pessoais entram em prompt/embedding/log | Média | Crítico | minimização, redaction e testes | detector encontra dado em trace |
| R-024 | prompt injection em fonte | Média | Alto | tratar fontes como dados, gate de segurança | segmento instrui sistema |
| R-025 | auditoria armazena texto protegido | Média | Alto | IDs/hashes, retenção, redaction | log contém página/trecho extenso |
| R-026 | validadores dão falsa sensação de segurança | Alta | Crítico | calibrar com humanos, medir falsos negativos | gate passa erro conhecido |
| R-027 | avaliação humana inconsistente | Média | Alto | rubrica, treinamento, dupla revisão | baixa concordância |
| R-028 | baseline genérico artificialmente fraco | Média | Alto | prompt justo, mesmo modelo, avaliação cega | diferença não reproduzível |
| R-029 | piloto pequeno gera conclusão forte demais | Média | Alto | classificar inconclusivo e reportar limites | amostra insuficiente |
| R-030 | overfitting aos oito temas | Média | Médio | holdout e consultas variadas | queda fora do conjunto treinado |
| R-031 | scope creep para RS e novos agentes | Alta | Alto | EPIC-018 Won't e gate US-017.2 | tarefa Codex inclui expansão |
| R-032 | scope creep da Gráfica | Média | Médio | contrato simples, pacote avançado fora | PDF/PPTX entra no caminho crítico |
| R-033 | frontend antecipado mascara backend instável | Média | Alto | contrato e fluxo headless primeiro | UI criada sem gates reais |
| R-034 | migrations conflitam com Prisma/Supabase atual | Alta | Alto | inventário e PR separado | duplicação de tabela/tipo |
| R-035 | schema físico genérico demais | Média | Alto | modelo lógico e contratos antes da migration | JSONB absorve invariantes críticas |
| R-036 | schema físico rígido demais para experimentos | Média | Médio | embedding separado e configs versionadas | trocar modelo exige alterar componente |
| R-037 | jobs duplicados publicam duas vezes | Média | Alto | idempotência e estado atômico | duas versões/componentes idênticos |
| R-038 | falta de curadores para 100–300 componentes | Alta | Alto | piloto em lotes, rubrica e responsáveis | backlog de revisão cresce |
| R-039 | direitos/retencão sem decisão operacional | Média | Alto | pendências jurídicas antes de produção | fonte sem prazo/termo claro |
| R-040 | documentação não acompanha código | Alta | Alto | DoD, ADR e PR docs-first | contrato implementado diverge |
| R-041 | Codex amplia o escopo | Média | Alto | prompts por lote e stop conditions | arquivos fora do plano |
| R-042 | refactor não relacionado aumenta risco | Média | Médio | PR pequeno e diff review | muitos módulos alterados |
| R-043 | rollback insuficiente | Média | Alto | feature flags, migrations reversíveis | falha exige hotfix manual |
| R-044 | observabilidade vira vazamento | Média | Alto | atributos seguros e acesso restrito | prompts/outputs em logs |
| R-045 | modelo lógico não cabe no repo real | Média | Alto | adapter e análise antes de novo pacote | dependências circulares |

## Top risks antes do primeiro código

1. R-001 — repositório canônico;
2. R-002 — fonte documental;
3. R-005 — licença;
4. R-010 — currículo;
5. R-021/R-022 — RLS e service role;
6. R-026 — validadores não calibrados;
7. R-034 — conflitos de schema;
8. R-038 — capacidade de curadoria;
9. R-040 — divergência documentação/código;
10. R-041 — expansão pelo Codex.

## Riscos aceitos temporariamente no protótipo

Somente com registro:

- curadoria por comandos em vez de painel;
- busca lexical antes do vetor;
- ausência de cache;
- um produto por vez;
- conjunto pequeno de professores;
- métricas de custo inicialmente estimadas quando provider não reconciliar.

Não podem ser aceitos:

- fonte sem permissão;
- vazamento de tenant;
- produto entregue com gate Must falho;
- currículo/ano/Estado errado;
- rastreabilidade ausente;
- dados sensíveis desnecessários;
- reprodução indevida.

## Revisão do registro

- no início de cada lote;
- antes de migration;
- antes de habilitar provider;
- antes do piloto;
- após incidente;
- ao alterar contrato/modelo/pacote curricular.

Cada risco deverá receber owner na implementação. Owners não foram inventados no Marco 003.
