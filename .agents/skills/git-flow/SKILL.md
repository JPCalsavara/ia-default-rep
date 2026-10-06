---
name: git-flow
description: Organiza a branch e cria o Pull Request padronizado para a main usando Conventional Commits.
---

# Git Flow

Use esta skill para formatar commits, resolver o versionamento do fluxo atual e empacotar tudo abrindo o PR (Pull Request) final.

## Regras
- **Conventional Commits**: O padrão do repositório exige commits semânticos:
  - `feat: <mensagem>`
  - `fix: <mensagem>`
  - `refactor: <mensagem>`
  - `docs: <mensagem>`
  - `chore: <mensagem>`
  - `test: <mensagem>`
- Verifique o status da branch com `git status` e `git diff`.
- Crie a mensagem do PR conectando-a explicitamente à RFC gerada no `.scratch/<feature>/`.
- O PR deve ter o status claro aguardando revisão do `code-review` e da pessoa (Tech Lead/PO) para entrar na `main`.
