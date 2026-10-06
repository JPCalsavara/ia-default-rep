# Repositório Padrão (AI-First & Non-Tech Friendly)

Bem-vindo ao template de repositório padronizado. Este projeto foi desenhado do zero para atuar como uma base ultra-sólida para empresas e equipes que desejam velocidade, governança e integração nativa com Agentes de Inteligência Artificial, sem abrir mão da qualidade técnica corporativa.

## 💡 A Ideia do Projeto

Times compostos por pessoas "não-techs" (Product Owners, gestores) precisam transformar regras de negócio em código rapidamente. No entanto, delegar isso diretamente para IAs ou Desenvolvedores Juniores sem barreiras de segurança frequentemente resulta em "código espaguete", interfaces genéricas e bugs de produção.

Este repositório resolve isso implementando **Guardrails (Grades de Proteção)** no formato de **ADRs** e orquestrando o trabalho através de um fluxo estrito de **Skills (Agentes IA)**. A `main` é blindada por integração contínua (CI) e por um AI Gatekeeper (`JPCalsavara/ai-gatekeeper`), garantindo que apenas código com testes verdes e aderente às regras de negócio chegue em produção.

---

## 🧠 Skills Principais (O Pipeline de IA)

Nosso fluxo de desenvolvimento é operado por 6 skills principais, atuando como uma linha de montagem:

1. 🔍 **`refine-issue`**: Lê as Issues (criadas via formulário no GitHub) e traduz o pedido bruto para uma RFC detalhada de implementação técnica.
2. 🏛️ **`domain-modeling`**: Extrai vocabulários e atualiza o histórico de arquitetura e contexto do portal.
3. 👷 **`feature-builder`**: O engenheiro primário. Lê a RFC, desenvolve os testes TDD, cria componentes (via Shadcn UI) e escreve a lógica de negócio do Backend.
4. 🔄 **`refactor-builder`**: Responsável exclusivo por refatorações estruturais em código legado, com a premissa de que os testes devem continuar verdes.
5. 📦 **`git-flow`**: Empacota o código em commits semânticos (`feat:`, `fix:`) e gerencia a abertura dos Pull Requests.
6. 🕵️ **`code-review`**: Atua localmente revisando se o desenvolvedor (ou a IA) cumpriu fielmente o que estava descrito na RFC antes de enviar para o Gatekeeper da nuvem.

---

## 📄 O que é uma RFC? (Request for Comments)

Neste fluxo, a **RFC** é o plano de voo da funcionalidade.
Sempre que uma Issue é movida para desenvolvimento, o `refine-issue` gera uma RFC na pasta `.scratch/<feature>/rfc.md`. 
Ela descreve o **O Quê**, o **Por Quê** e o **Como** de forma estruturada. Antes de escrever uma única linha de código, o time (ou agente) deve consultar e concordar com o plano técnico proposto na RFC. Isso elimina o temido "desenvolvimento baseado em adivinhação".

---

## 🏛️ O que é uma ADR? (Architecture Decision Record)

Uma **ADR** é um documento curto que captura uma decisão arquitetural importante feita no projeto.
Enquanto as RFCs são passageiras (sobre uma feature específica), as **ADRs são leis permanentes** do repositório (ex: "Sempre usar UTC para datas", "Sempre armazenar dinheiro em centavos").

### Por que essas ADRs Padrões existem?
Elas servem para **blindar a IA** (e os novos programadores). IAs tendem a "alucinar" tecnologias diferentes a cada novo prompt. Tendo as ADRs documentadas na pasta `docs/adr/`, obrigamos a IA a consultar essas regras *antes* de codar. Isso impede que ela use cores feias do Tailwind, que esqueça do Soft Delete ou que crie tabelas vulneráveis a perda financeira.

### As nossas 11 ADRs base (e por que as escolhemos):

1. **`01-backend-layered-architecture`**: Padrão de camadas pragmático. Mais veloz que Clean Arch, mas organizado o suficiente para IAs lerem.
2. **`02-frontend-atomic-design`**: Mantém o React escalável (Atoms, Molecules, etc.).
3. **`03-currency-bigint-cents`**: Dinheiro sempre em inteiros. Evita falências por erro de ponto flutuante.
4. **`04-global-error-handling`**: Previsibilidade total no Frontend com respostas `{ "code": "...", "message": "..." }`.
5. **`05-soft-delete-default`**: Ninguém apaga dados de verdade por acidente (`deleted_at`).
6. **`06-utc-timezones`**: O fim dos bugs de fuso horário. O banco guarda UTC puro.
7. **`07-branch-protection-and-naming`**: O selo de garantia. Padrão de commits semânticos e bloqueios via `ai-gatekeeper`.
8. **`08-security-jwt-rbac`**: Autenticação fácil de consumir via mobile e Web (Token JWT sem estado).
9. **`09-data-governance-audit`**: LGPD aplicada no log (zero vazamento de senhas) e colunas de `created_by`.
10. **`10-financial-transactions-safety`**: Proteção com trava no banco (`SELECT FOR UPDATE`) para impedir concorrência em pagamentos.
11. **`11-frontend-design-system-and-ux`**: Consagra o `shadcn/ui` + `lucide-react` para beleza nativa, além de banir emojis e aspas corporativas artificiais.

Se você precisa tomar uma nova decisão que afetará a forma como o sistema é construído, crie uma nova ADR.
