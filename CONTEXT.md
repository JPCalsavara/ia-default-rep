# Contexto da Aplicação

Este é o repositório central padronizado. Ele foi desenhado para ser previsível, fácil de configurar via CI/CD, e perfeitamente legível tanto por Desenvolvedores Juniores quanto por Agentes de Inteligência Artificial.

## Documentação de Domínio e Decisões
Todas as decisões estruturais invioláveis do projeto estão listadas nas [ADRs (Architecture Decision Records)](docs/adr/):

1. **01-backend-layered-architecture**: Pragmatic Layered Pattern (`app.py` -> `middlewares` -> `schemas/dtos` -> `controllers` -> `repositories` -> `models`).
2. **02-frontend-atomic-design**: Atoms, Molecules, Organisms, Templates, Pages.
3. **03-currency-bigint-cents**: O Backend e Banco de Dados apenas tratam inteiros para moedas (R$ 10,50 = `1050`).
4. **04-global-error-handling**: Respostas padronizadas `{ "code": "...", "message": "...", "details": [] }`.
5. **05-soft-delete-default**: Uso de `deleted_at` em todas as tabelas. Nada é apagado via `DELETE` SQL.
6. **06-utc-timezones**: Backend armazena e expõe ISO 8601 em UTC puro. Frontend converte para a localidade.
7. **07-branch-protection-and-naming**: Branches no formato `tipo/id-descricao`, issues prefixadas (`[Feat]`), e merge bloqueado exigindo testes + `ai-gatekeeper` + aprovação humana.
8. **08-security-jwt-rbac**: Autenticação via JSON Web Tokens com validação de Roles (`admin`, `user`) por Middlewares.
9. **09-data-governance-audit**: Rastreio com `created_by`/`updated_by`. Expressamente proibido logar PII no backend.
10. **10-financial-transactions-safety**: Prevenção de concorrência com `Idempotency-Key` e Row Locks (`SELECT FOR UPDATE`).
11. **11-frontend-design-system-and-ux**: Adoção do `shadcn/ui` (Tailwind Inline no JSX) + `lucide-react`. Proibido Emojis e jargões de IA nas telas. Textos sempre envelopados com `break-words`.

## Políticas do Projeto
- **Infra e CI**: Uso mandatório de `docker` e `docker-compose` para dev local. 
- **Merge Gates (`main`)**: É TERMINANTEMENTE proibido mergear na `main` sem que a Action de CI do Frontend (Cypress), do Backend (Integração) E o `JPCalsavara/ai-gatekeeper` tenham passado com sucesso, seguidos de uma aprovação humana.
- **Segredos**: Nunca commitar senhas, usar exclusivamente `.env` não versionados e injetados nos environments e CI.
- **API Specs**: O backend expõe o Swagger vivo.

## Regras para o Agente IA (Skills)
O pipeline de desenvolvimento via agentes atua com 6 ferramentas:
1. `refine-issue`: Transforma um card (GitHub Issue) numa `RFC` detalhada.
2. `domain-modeling`: Registra ADRs e vocabulário técnico aqui, no diretório de contexto.
3. `feature-builder`: Implementa novos recursos do zero orientados por Testes e à RFC.
4. `refactor-builder`: Exclusiva para modificar o esqueleto do sistema sem mudar comportamento, mantendo testes rodando.
5. `git-flow`: Prepara commits padronizados, assina branches e abre o MR/PR oficial.
6. `code-review`: Revisão e validação primária em ambiente local de dev (antes do commit/push para a Action oficial do Gatekeeper).
