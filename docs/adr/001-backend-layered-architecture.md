# 1. Backend Layered Architecture (Padrão da Imagem)

Date: 2026-10-06
Status: Accepted

## Context
Precisamos de um padrão de arquitetura para Python Backend (FastAPI/Flask/Django) que seja altamente previsível para agentes de IA e fácil de entender para desenvolvedores juniores. O Strict Clean Architecture foi avaliado, mas descartado devido à alta complexidade (boilerplate excessivo) para uma empresa com times não-tech e que busca agilidade.

## Decision
Adotamos a **Arquitetura em Camadas Pragmática** baseada no fluxo:
`app.py` -> `middlewares` -> `schemas/dtos` -> `resource` / `controllers` -> `repositories` -> `models` -> `database`

- **Middlewares**: Interceptações de request/response (Auth, logging).
- **Schemas / DTOs**: Validação estrita de entrada e saída (ex: Pydantic).
- **Controllers / Resources**: Ponto de entrada da rota HTTP. Coordena o fluxo, mas não contém regra de negócio pesada ou queries SQL.
- **Repositories**: A única camada autorizada a falar com o banco de dados. Retorna Models.
- **Models**: Representação exata das tabelas do banco de dados (ORM).

## Consequences
- Fluxo de dados é unidirecional e sempre previsível.
- IAs e Devs saberão exatamente onde injetar código ou onde debugar, pois a responsabilidade de cada arquivo é única e nominal.
