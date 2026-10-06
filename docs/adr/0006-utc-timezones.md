# 6. Timezones UTC Everywhere

Date: 2026-10-06
Status: Accepted

## Context
Datas com diferentes fusos horários no servidor geram bugs de agendamento e inconsistência no painel dos usuários de locais distintos.

## Decision
A aplicação operará 100% em **UTC**.
- Banco de dados: Armazena TIMESTAMPTZ ou TIMESTAMP em UTC puro.
- Backend (Python): Processa os objetos DateTime em UTC e retorna no JSON em ISO 8601 (terminando em Z).
- Frontend: Captura a data ISO e converte para o horário local dinâmico do navegador de quem está visualizando.

## Consequences
- Complexidade das datas retirada completamente do Backend e migrada para a camada visual (Frontend).
