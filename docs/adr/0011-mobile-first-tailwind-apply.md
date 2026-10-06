# 11. Estilização: Mobile-First e Tailwind com `@apply`

Date: 2026-10-06
Status: Accepted

## Context
Garantir responsividade nativa (Mobile-First) em todos os componentes mantendo o código HTML extremamente limpo para as pessoas de produto e IAs lerem.

## Decision
Adotamos o **Tailwind CSS** usado de forma semântica.
- **Mobile-First**: A regra base do CSS é sempre para celular. Breakpoints (ex: `md:`, `lg:`) só entram para reajustar telas grandes.
- **Classes Semânticas no HTML**: O HTML usará classes legíveis como `<button class="btn-primary">`.
- **Diretiva `@apply`**: A lógica complexa e utilitária do Tailwind viverá no arquivo CSS do componente. 
  - Exemplo: `.btn-primary { @apply flex w-full bg-blue-500 rounded-md md:w-auto; }`

## Consequences
- Código limpo no Frontend (HTML livre da "poluição visual" utilitária).
- Pessoas não-tech podem entender a estrutura da interface mais rapidamente.
