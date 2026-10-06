# 4. Tratamento Global de Erros de API

Date: 2026-10-06
Status: Accepted

## Context
Erros não padronizados entre rotas e domínios dificultam que o Frontend trate exceções ou exiba mensagens padronizadas.

## Decision
Todo retorno HTTP com status code >= 400 deve seguir estritamente o formato JSON de erro da empresa:
```json
{
  "code": "STRING_UPPERCASE",
  "message": "Mensagem humana padrão de fallback",
  "details": [
     {"field": "nome", "issue": "obrigatório"}
  ]
}
```
- O Frontend usa o campo `code` para traduções locais.
- Nunca retorne `String` crua ou chaves dinâmicas soltas. O formato do contrato acima é inviolável.

## Consequences
- Maior resiliência no Frontend, que passa a prever o payload exato de qualquer erro HTTP.
