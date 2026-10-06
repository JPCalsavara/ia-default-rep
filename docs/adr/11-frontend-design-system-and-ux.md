# 011. Frontend Design System, Shadcn UI e UX

Date: 2026-10-06
Status: Accepted

## Context
Decisões anteriores sobre limpeza de HTML (`@apply`) e referências externas (`Dribbble`) entraram em conflito com a velocidade e o ecossistema do `shadcn/ui`, que gera Tailwind utilitário diretamente no JSX. Precisávamos eleger uma única fonte de verdade para garantir um visual elegante, anti-robótico e rápido de codar.

## Decision

### 1. Supremacia do `shadcn/ui` e Tailwind Nativo
- O Design System da aplicação é governado nativamente pelo **`shadcn/ui`**. As cores, bordas e espaçamentos usam o sistema de CSS Variables embutido na biblioteca.
- É **proibido** criar modais, selects ou componentes complexos do zero via `divs`. O agente DEVE rodar `npx shadcn@latest add [componente]`.
- As classes utilitárias do Tailwind no JSX/HTML estão **autorizadas** e são o padrão (encerra-se a obrigatoriedade de abstrair no arquivo CSS com `@apply`).
- Ícones globais usam obrigatoriamente a biblioteca `lucide-react`.

### 2. Prevenção de Quebra de Tela (Mobile-First)
- Textos dinâmicos nunca podem causar *overflow-x*. Todo container de texto deve usar defesas utilitárias (`break-words`, `truncate` ou `line-clamp-X`).

### 3. Copywriting (Anti-IA-ísmos)
- Fica expressamente **proibido** o uso de Emojis em textos da interface.
- Fica **proibido** o uso excessivo de aspas (`""`), parênteses `()` explicativos e jargões robóticos (ex: "Em resumo", "Por fim", "É importante notar"). A linguagem é estritamente limpa e profissional.

## Consequences
- O visual é premium "out-of-the-box" sem esforço adicional de UI Design.
- O código avança mais rápido, e as IAs se sentem em casa operando Tailwind no JSX.
- A interface passa confiança humana ao rejeitar as bizarrices clássicas de texto gerado por Inteligência Artificial.
