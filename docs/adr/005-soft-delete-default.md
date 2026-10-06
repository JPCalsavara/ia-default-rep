# 5. Soft Delete por Padrão

Date: 2026-10-06
Status: Accepted

## Context
Usuários da plataforma (especialmente em ambientes não-tech) apagam dados por acidente com frequência. O Hard Delete causa a perda irreversível de histórico.

## Decision
Todas as tabelas de negócio utilizarão **Soft Delete**.
- Deve haver uma coluna `deleted_at` (TIMESTAMP NULL).
- Queries de listagem devem sempre verificar `WHERE deleted_at IS NULL`.
- O comando SQL `DELETE` está banido da aplicação, exceto em tabelas específicas de vínculo n-para-n de curta duração ou dados de log efêmeros.

## Consequences
- O banco de dados cresce mais rápido, mas a segurança em recuperação de dados compensa inteiramente.
