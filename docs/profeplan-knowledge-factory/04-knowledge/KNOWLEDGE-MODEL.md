# Modelo de Conhecimento Pedagógico

## 1. Conceito central

O sistema não deve usar o livro inteiro como contexto de cada solicitação. As fontes são processadas antecipadamente e transformadas em componentes pedagógicos semielaborados.

## 2. Estados do conhecimento

### Fonte original

PDF, documento curricular, material próprio, obra licenciada ou outra fonte preservada com integridade e procedência.

### Fragmento de evidência

Trecho estruturalmente identificado, ligado à página, seção, imagem ou tabela de origem. Serve para auditoria e verificação, não como produto final.

### Componente pedagógico

Unidade autoral, estruturada e reutilizável que representa um conceito, estratégia, padrão avaliativo, orientação inclusiva ou outro elemento necessário à produção.

### Produto pedagógico

Resultado personalizado entregue ao professor, criado pela combinação de componentes, currículo e contexto.

## 3. Tipos iniciais de componentes

- conceitual;
- curricular;
- metodológico;
- atividade-base;
- avaliativo;
- contextualização;
- inclusão e acessibilidade;
- referência e rastreabilidade;
- editorial.

## 4. Campos mínimos

Cada componente deve possuir:

- identificador estável;
- título;
- tipo;
- conteúdo autoral;
- componente curricular;
- etapa;
- anos compatíveis;
- finalidades permitidas;
- relações com BNCC;
- relações com currículo estadual;
- palavras-chave;
- nível de complexidade;
- fontes de origem;
- classificação de licença;
- status de validação;
- versão;
- datas de criação e revisão;
- embedding, quando aplicável.

## 5. Exemplo conceitual

```json
{
  "id": "fil-em2-etica-liberdade-001",
  "type": "conceptual",
  "title": "Liberdade e responsabilidade moral",
  "authorial_content": "Síntese autoral consolidada para uso pedagógico.",
  "component": "Filosofia",
  "stage": "Ensino Médio",
  "grades": ["2"],
  "purposes": ["lesson_plan", "teaching_material", "assessment"],
  "curriculum_packages": ["MG"],
  "license_class": "licensed_or_owned",
  "validation_status": "reviewed",
  "source_refs": ["source-001#chapter-03"]
}
```

## 6. Vetorização

O embedding funciona como índice semântico. O conteúdo, os metadados e a procedência permanecem no banco relacional.

Nem todo campo precisa ser vetorizado. Campos objetivos, como ano, componente, Estado, licença e status, devem ser consultados por filtros.

## 7. Regra de granularidade

Um componente não deve ser:

- tão amplo quanto um capítulo completo;
- tão pequeno quanto uma frase isolada sem contexto;
- tão finalizado quanto um plano de aula pronto.

Ele deve conter conhecimento suficiente para ser reutilizado e aberto o bastante para permitir novas composições.

## 8. Deduplicação

Contribuições semelhantes de várias obras devem alimentar conceitos canônicos. A diversidade de fontes será preservada na procedência, sem criar dezenas de componentes praticamente iguais.
