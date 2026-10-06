# 7. Nomenclatura, Gatekeeper e Proteção da Branch Main

Date: 2026-10-06
Status: Accepted

## Context
Para escalar o time de desenvolvimento (IAs e humanos) mantendo a "main" sempre apta para deploy em produção, precisamos de regras estritas sobre como nomeamos branches/cards e quais são os portões de qualidade (gates) obrigatórios antes de um merge.

## Decision

### 1. Nomenclatura Padrão (Semântica)
- **Cards (Issues)**: Devem sempre ter um prefixo indicativo da intenção.
  - Ex: `[Feat] Criar tela de checkout`
  - Ex: `[Bug] Botão de pagamento não responde`
  - Ex: `[Chore] Atualizar dependências`
- **Branches**: Seguem a estrutura `tipo/ID_DO_CARD-descricao_curta`.
  - Ex: `feat/12-tela-checkout`
  - Ex: `fix/45-botao-pagamento`
  - Ex: `refactor/18-camada-controller`

### 2. Proteção da Branch `main` (Merge Gates)
A branch `main` será **protegida** via configurações de repositório (ex: Branch Protection Rules no GitHub). Nenhum push direto é permitido. Todo código deve vir de um Pull Request e passar pelos seguintes *status checks* obrigatórios:
1. **Passar nos Testes Backend**: Integração via Pytest/equivalente.
2. **Passar nos Testes Frontend**: E2E e Componentes via Cypress.
3. **AI Gatekeeper (`JPCalsavara/ai-gatekeeper`)**: O PR só pode ser mergeado se a Action do AI Gatekeeper analisar o código, validar aderência às ADRs/RFCs e dar "Aprovado".
4. **Code Review Humano**: Exige pelo menos 1 aprovação (`Approve`) de um Tech Lead, PO ou desenvolvedor par.

## Consequences
- O repositório torna-se a prova de quebras acidentais de build.
- A revisão via AI Gatekeeper desafoga os líderes humanos de revisarem lint/arquitetura, permitindo que a aprovação humana foque apenas em negócio.
- O histórico git (`git log`) fica extremamente legível graças à rastreabilidade de ID e prefixos.
