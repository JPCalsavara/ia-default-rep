---
name: refactor-builder
description: Refatora o código estruturalmente garantindo que a cobertura de testes E2E e de Integração permaneça verde.
---

# Refactor Builder

Use esta skill quando precisar reorganizar, limpar ou adequar o código existente às Architecture Decision Records (ADRs) globais sem alterar as regras de negócio de fato (comportamento).

## Fluxo de Refatoração

1. **Testes Antes**: Execute a suíte de testes de integração (backend) e E2E/Componentes (frontend). Garanta que tudo está verde ANTES de começar a mexer no código legado.
2. **Consultar o `CONTEXT.md` e ADRs**: Leia o `docs/adr/` e `CONTEXT.md` para entender como o código "deve" ficar estruturado.
3. **Refatorar Iterativamente**: 
   - Quebre o refatoramento em partes.
   - Aplique a alteração estrutural.
   - Se o refatoramento exigir alteração da estrutura do teste em si (ex: você extraiu um serviço), altere o teste mas mantenha a validação exata do comportamento.
4. **Testes Depois**: Execute os testes finais. Se passarem, o refatoramento foi concluído com sucesso. Se quebrarem e você não conseguir consertar, desfaça as mudanças ou faça um commit de rascunho.
