# 10. Segurança em Transações Financeiras

Date: 2026-10-06
Status: Accepted

## Context
Sistemas que lidam com moeda (mesmo em BIGINT - ADR 0003) estão suscetíveis a "duplos cliques" do lado do cliente e a condições de corrida (Race Conditions) em requisições simultâneas.

## Decision
1. **Chaves de Idempotência**: Toda rota HTTP `POST` ou `PUT` que altera saldo/status financeiro deve exigir um Header `Idempotency-Key` único enviado pelo Frontend. O Backend verifica se a chave já foi processada. Se sim, ignora a cobrança e retorna o resultado anterior salvo.
2. **Row Locks no Banco (ACID)**: Ao atualizar saldos, o Repository deve utilizar `SELECT ... FOR UPDATE` para travar a linha do banco de dados temporariamente até o `COMMIT`, forçando transações concorrentes a esperarem na fila.

## Consequences
- Elimina o risco de duplo faturamento e saldos negativos por falha de paralelismo.
