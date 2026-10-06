# 13. Componentização Frontend: Shadcn UI e Lucide Icons

Date: 2026-10-06
Status: Accepted

## Context
Mesmo com as diretrizes de Mobile-First (ADR 0011) e fuga do "Genérico" (ADR 0012), desenhar componentes complexos (Selects, Modais, Calendários, Gráficos) do zero exige alto esforço, resulta em falhas de acessibilidade e despadroniza a interface. 

## Decision
1. **Adoção do `shadcn/ui`**: Fica estabelecido que o `shadcn/ui` é o Design System base do projeto.
   - Qualquer necessidade de interface estrutural (Botão, Dialog, Dropdown, Accordion, Data Table) DEVE obrigatoriamente tentar consumir um componente existente do shadcn via CLI (ex: `npx shadcn@latest add dialog`).
   - É proibido criar um componente complexo do zero usando `divs` cruas se já existir uma versão do `shadcn/ui` para o problema.
   
2. **Iconografia (`lucide-react`)**: Para manter a consistência de espessura de linha e design em todo o portal, a única biblioteca de ícones permitida é a `lucide-react` (nativa do ecossistema shadcn).

## Consequences
- O frontend ganha um visual premium (comparável ao Vercel/Linear) out-of-the-box.
- A acessibilidade (leitores de tela, navegação por teclado) passa a ser garantida pela biblioteca interna (Radix UI).
- O agente `feature-builder` ganha produtividade colossal apenas compondo as "peças de lego" instaladas.
