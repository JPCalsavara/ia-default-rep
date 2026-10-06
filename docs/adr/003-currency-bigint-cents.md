# 3. Currency em BIGINT (Centavos)

Date: 2026-10-06
Status: Accepted

## Context
O manuseio de dinheiro através de tipos Float ou numéricos quebrados causa perdas de precisão em operações matemáticas.

## Decision
Todos os valores financeiros em todo o sistema (Banco de Dados e Backend) serão armazenados e processados exclusivamente como **Inteiros em centavos (BIGINT)**.
- Exemplo: `R$ 10,50` é armazenado no banco como `1050`.
- O Backend nunca realiza formatação com vírgula, ele apenas transita inteiros.
- O Frontend é o único responsável por pegar o número `1050`, dividir por `100` e aplicar a máscara local de moeda (ex: `Intl.NumberFormat`).

## Consequences
- Matemática exata. Sem bugs de arredondamento no Python.
