# 8. Segurança: JWT e Controle de Acesso (RBAC)

Date: 2026-10-06
Status: Accepted

## Context
APIs precisam identificar quem está chamando e se essa pessoa tem permissão para realizar a ação, sem depender de sessões de servidor (Stateful) para facilitar a escalabilidade.

## Decision
Adotamos **JWT (JSON Web Tokens)** trafegados no header `Authorization: Bearer <token>`.
- O payload do JWT deve conter o `user_id` e a lista de `roles` (ex: `["admin", "user"]`).
- O Backend usará Middlewares de RBAC (Role-Based Access Control) que inspecionam o JWT ANTES da requisição chegar no Controller. Se não tiver a role, retorna `403 Forbidden` automaticamente no padrão de Erro Global (ADR 0004).

## Consequences
- Autenticação "Stateless" pronta para escalar.
- Facilita integrações no Frontend e em futuros aplicativos Mobile nativos.
