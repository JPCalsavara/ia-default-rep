# 12. Padrões de UI/UX, Copywriting e Prevenção de "IA-ísmos"

Date: 2026-10-06
Status: Accepted

## Context
Para garantir que a plataforma tenha um aspecto profissional, sofisticado e humano, precisamos blindar o Front-end e o Copywriting contra textos com "cara de inteligência artificial" e designs genéricos ou quebrados no mobile.

## Decision

### 1. Copywriting e Tom de Voz (Banimento de IA-ísmos)
- Fica expressamente **proibido** o uso de Emojis em textos da interface, mensagens de erro, alertas ou notificações.
- Fica **proibido** o uso excessivo e não natural de aspas (`""`), parênteses `()` explicativos e jargões robóticos (ex: "Em resumo", "Por fim", "É importante notar").
- Os textos devem ser curtos, diretos e com tom de voz estritamente profissional e humano.

### 2. Design System e Fuga do "Genérico"
- IAs e Desenvolvedores estão proibidos de usar cores padrão, fontes padrão e arredondamentos genéricos (ex: botões quadrados ou sombras rudimentares do Tailwind) sem intenção.
- **Referência Obrigatória**: Antes de construir componentes estruturais, deve-se extrair inspiração de um design maduro (ex: Dribbble).
- As cores, fontes e raios de borda (`border-radius`) da referência devem ser exportados como **Design Tokens** no arquivo `tailwind.config.js`.

### 3. Prevenção de Quebra (Text Overflow Mobile)
- É proibido renderizar strings dinâmicas (nomes, e-mails, descrições) em tela sem proteção de layout horizontal.
- Todo container de texto deve usar utilitários preventivos de quebra, como `break-words`, `truncate`, `hyphens-auto` ou `line-clamp-X`.
- Isso garante que a responsividade Mobile não sofra *overflow-x* ou perca a simetria ao carregar dados reais do banco.

## Consequences
- O produto final parecerá polido, com "cara de Dribbble", mesmo sendo desenvolvido por engenheiros de backend ou Agentes de IA.
- O texto na interface passará extrema credibilidade ao banir trejeitos de IA generativa.
