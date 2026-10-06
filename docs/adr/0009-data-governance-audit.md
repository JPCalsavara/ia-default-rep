# 9. Governança de Dados: Auditoria e LGPD

Date: 2026-10-06
Status: Accepted

## Context
Precisamos rastrear o ciclo de vida dos dados e garantir privacidade (LGPD by design) sem o custo exorbitante de implementar Event Sourcing puro.

## Decision
1. **Auditoria de Tabelas**: TODA tabela de negócio deverá conter obrigatoriamente as colunas `created_by` e `updated_by` (armazenando o ID do usuário que fez a ação), além do `deleted_at` (ADR 0005).
2. **Ofuscação de Logs**: É terminantemente proibido inserir `print()` ou `logger.info()` no Backend contendo PII (Senhas, Cartões de Crédito, Documentos Pessoais).

## Consequences
- Conformidade instantânea com políticas básicas de privacidade.
- Rastreio exato de "quem quebrou o quê" sem necessidade de ferramentas complexas.
