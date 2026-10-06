# Contexto da Aplicação

Este é o repositório central padronizado. Ele foi desenhado para ser previsível, fácil de configurar via CI/CD, e perfeitamente legível tanto por Desenvolvedores Juniores quanto por Agentes de Inteligência Artificial.

## Documentação de Domínio e Decisões
Todas as decisões estruturais invioláveis do projeto estão listadas nas [ADRs (Architecture Decision Records)](docs/adr/):

1. **Backend Layered Architecture**: Pragmatic Layered Pattern (`app.py` -> `middlewares` -> `schemas/dtos` -> `controllers` -> `repositories` -> `models`).
2. **Frontend Atomic Components**: Atoms, Molecules, Organisms, Templates, Pages.
3. **Currency em BIGINT (Centavos)**: O Backend e Banco de Dados apenas tratam inteiros para moedas (R$ 10,50 = `1050`).
4. **Tratamento Global de Erros de API**: Respostas padronizadas `{ "code": "...", "message": "...", "details": [] }`.
5. **Soft Delete por Padrão**: Uso de `deleted_at` em todas as tabelas. Nada é apagado via `DELETE` SQL.
6. **Timezones UTC Everywhere**: Backend armazena e expõe ISO 8601 em UTC puro. Frontend converte para a localidade.
7. **Nomenclatura, Gatekeeper e Proteção da Main**: Branches no formato `tipo/id-descricao`, issues prefixadas (`[Feat]`), e merge bloqueado exigindo testes + `ai-gatekeeper` + aprovação humana.

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
