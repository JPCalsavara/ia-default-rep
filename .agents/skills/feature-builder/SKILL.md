---
name: feature-builder
description: Orquestrador de desenvolvimento de ponta a ponta (E2E). Lê a RFC da branch, executa o ciclo TDD para Backend e Frontend, usa Shadcn UI e garante que a cobertura seja verde.
---

# Feature Builder

Use esta skill quando precisar construir uma funcionalidade de ponta a ponta a partir de uma `RFC` já estabelecida no repositório.

## Fluxo de Construção (Backend)
1. Leia a RFC alvo no `.scratch/<feature>/rfc.md`.
2. Escreva o **Teste de Integração** (TDD) para a nova rota que certifique as regras descritas na RFC.
3. Desenvolva o código seguindo a Layered Architecture (Middlewares -> Schemas -> Controllers -> Repositories -> Models).
4. Rode os testes e garanta o comportamento esperado.

## Fluxo de Construção (Frontend)
1. **Componentização e Design**:
   - Respeite o Atomic Design.
   - **CRÍTICO: Shadcn UI**. Antes de criar qualquer UI complexa (ex: botões padronizados, cards, seletores, modais), você **DEVE** tentar importar rodando o comando CLI: `npx shadcn@latest add [componente]`. NUNCA construa modais/popovers complexos do zero.
   - **Ícones**: Utilize EXCLUSIVAMENTE importações da biblioteca `lucide-react`.
2. **Responsividade**:
   - Use as diretivas Mobile-First.
   - Aplique sempre proteções em textos dinâmicos (ex: `break-words`, `truncate`).
3. Verifique o componente visualmente / escreva os testes Cypress correspondentes para cobrir as ações principais de clique e renderização.

## Finalização
Não faça commit de imediato se o frontend ou backend quebrarem. Itere rigorosamente rodando testes locais com `docker-compose` até a branch ficar estável. Quando terminar, repasse a bola para a skill `git-flow`.
