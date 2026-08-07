# Padrão de Pacotes Curriculares

## 1. Objetivo

Permitir que o mesmo agente opere com diferentes currículos estaduais sem duplicação de código, identidade ou repertório disciplinar.

## 2. Escopo inicial

- pacote MG: inicial;
- pacote RS: próxima implantação.

## 3. Conteúdo mínimo de um pacote

- identificação do Estado;
- etapa;
- ano;
- componente curricular;
- versão;
- vigência;
- documento-fonte;
- habilidades;
- objetos de conhecimento;
- unidades temáticas;
- progressões;
- orientações metodológicas;
- equivalências com a BNCC;
- referências regionais;
- status de validação.

## 4. Regra de ativação

Cada produção terá um único pacote estadual principal. O segundo pacote somente poderá ser consultado em modo comparativo explicitamente solicitado.

## 5. Prioridade documental

A interpretação curricular deve respeitar esta ordem:

1. legislação e diretrizes nacionais aplicáveis;
2. BNCC;
3. pacote curricular estadual ativo;
4. documentos da rede;
5. projeto pedagógico da escola;
6. planejamento e escolhas do professor.

## 6. Versionamento

Produtos gerados devem registrar qual versão do pacote curricular foi utilizada. Pacotes substituídos permanecem disponíveis para auditoria, mas não devem ser selecionados como padrão.

## 7. Exemplo de identificação

```json
{
  "curriculum_package_id": "br-mg-em-fil-2-v1",
  "country": "BR",
  "state": "MG",
  "stage": "Ensino Médio",
  "grade": "2",
  "component": "Filosofia",
  "status": "active",
  "effective_from": "a definir"
}
```

## 8. Separação entre currículo e conhecimento

O pacote curricular define o que deve orientar a aprendizagem. O repertório filosófico do Sócrates 2 permanece compartilhado. O pacote estadual não deve duplicar toda a base conceitual.
