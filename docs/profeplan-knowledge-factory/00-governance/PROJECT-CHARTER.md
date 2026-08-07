# Project Charter — ProfePlan Knowledge Factory

## 1. Visão

Construir uma infraestrutura de conhecimento pedagógico especializada para o ProfePlan, capaz de fornecer a agentes de IA componentes confiáveis, curriculares, autorais e adequados ao Ensino Fundamental II e ao Ensino Médio.

## 2. Problema

Modelos de linguagem genéricos podem produzir respostas superficiais, misturar componentes e anos escolares, recuperar conteúdo excessivo, consumir muitos tokens e reproduzir estruturas próximas às fontes consultadas. O ProfePlan precisa de uma camada própria de conhecimento, com escopo, procedência, currículo, permissões e critérios pedagógicos.

## 3. Solução proposta

Criar um sistema composto por:

1. fontes originais protegidas;
2. pipeline de extração e destilação;
3. componentes pedagógicos semielaborados;
4. metadados curriculares e jurídicos;
5. embeddings para busca semântica quando aplicável;
6. agentes especializados por componente, etapa e ano;
7. pacotes curriculares estaduais plugáveis;
8. orquestração por Ordem de Produção Pedagógica;
9. controle de qualidade pedagógico, curricular, autoral e inclusivo;
10. Gráfica ProfePlan para acabamento editorial.

## 4. Escopo inicial

- Ensino Fundamental II: 6º ao 9º ano;
- Ensino Médio: 1º ao 3º ano;
- currículo estadual inicial: Minas Gerais;
- próximo currículo: Rio Grande do Sul;
- piloto: Filosofia do 2º ano do Ensino Médio;
- agente piloto: Sócrates 2.

## 5. Fora do escopo inicial

- Educação Infantil;
- Ensino Fundamental I;
- Ensino Superior;
- duplicação de agentes por Estado;
- ingestão irrestrita de obras sem análise de direitos;
- geração automática sem rastreabilidade;
- implementação de código antes da aprovação documental.

## 6. Resultados esperados

- menor confusão entre disciplinas e anos;
- recuperação mais precisa;
- menor contexto enviado aos modelos;
- melhor controle de tokens e latência;
- maior qualidade pedagógica;
- materiais autorais e personalizados;
- rastreabilidade das fontes e decisões;
- expansão organizada para novos componentes e Estados.

## 7. Critérios de sucesso do piloto

O piloto será considerado promissor quando demonstrar:

- roteamento correto para o Sócrates 2;
- uso exclusivo do pacote curricular ativo;
- recuperação de poucos componentes altamente relevantes;
- produção coerente com Filosofia do 2º ano;
- ausência de mistura indevida com outros níveis;
- conformidade com as regras de autoria;
- tempo e custo de resposta aceitáveis;
- avaliação pedagógica positiva por revisores humanos.

## 8. Restrições

- stack principal do ProfePlan deve ser preservada;
- decisões técnicas devem ser registradas antes da implementação;
- materiais protegidos exigem classificação jurídica;
- agentes devem operar com privilégios mínimos de conhecimento;
- o professor deve receber um produto integrado, não respostas fragmentadas de vários agentes.
