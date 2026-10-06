# 2. Frontend Atomic Components

Date: 2026-10-06
Status: Accepted

## Context
O repositório terá um frontend que precisa escalar de forma sustentável sem virar um "macarrão" de componentes não reutilizáveis.

## Decision
Adotamos o padrão **Atomic Design** para componentes Frontend:
- **Atoms**: Componentes base, sem estado complexo ou dependências de negócio (ex: botões, inputs, tipografia).
- **Molecules**: Combinação de Atoms para formar uma UI um pouco mais complexa (ex: campo de busca com botão).
- **Organisms**: Seções de interface autossuficientes e com lógica de negócio (ex: Header, Formulário de Login).
- **Templates**: Estruturas de página sem dados reais injetados.
- **Pages**: O componente final que busca os dados da API e injeta nos Templates/Organisms.

## Consequences
- Reuso extremo de componentes UI.
- Testes de componentes (via Cypress) focados majoritariamente em Atoms, Molecules e Organisms.
