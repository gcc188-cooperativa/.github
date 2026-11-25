# Cooperativa de Transportes — GCC188/UFLA

Sistema web de apoio à gestão financeira de uma **cooperativa de transportes**: API REST, interface web (SPA) e ambiente executável em contêineres, desenvolvido na disciplina GCC188 (UFLA, 2026-2). A cooperativa reúne motoristas autônomos (*cooperandos*) que prestam serviços de transporte a *clientes*; ela intermedeia o fluxo financeiro — recebe o pagamento do cliente, retém a taxa e repassa o valor líquido ao cooperando — cobrindo contratos com ciclo de aprovação, cronogramas de pagamento, baixas, repasses, despesas e relatórios.

## Estrutura da organização

O projeto é uma organização com cinco repositórios (decisão D03/Δ01 do Design):

| Repositório | Conteúdo |
|---|---|
| [gcc188-docs](https://github.com/gcc188-cooperativa/gcc188-docs) | **Âncora** — requisitos, design e protótipo de telas; README principal com instruções de uso, tecnologias e desvios declarados |
| [gcc188-api-contract](https://github.com/gcc188-cooperativa/gcc188-api-contract) | Contrato OpenAPI 3.1 da API (fonte de verdade; gera pacotes Java/npm) |
| [gcc188-backend](https://github.com/gcc188-cooperativa/gcc188-backend) | API REST (Java 25 + Spring Boot 4, PostgreSQL 18), migrações e testes |
| [gcc188-front](https://github.com/gcc188-cooperativa/gcc188-front) | Interface web (React 19, Mantine 9) — telas, rotas e testes implementados |
| [gcc188-infra](https://github.com/gcc188-cooperativa/gcc188-infra) | Docker Compose, Caddy, backup, e2e e observabilidade |

Protótipo navegável das telas por perfil: <https://gcc188-cooperativa.github.io/gcc188-docs/>

## Regras de uso do Git (tarefa #21)

- **Ramos:** `master` protegido nos repositórios de documentação, contrato e infraestrutura; `develop` em backend e front. Trabalho em ramos curtos (`docs/*`, `feat/*`, `fix/*`, `test/*`), integrados por PR revisado e _squash merge_.
- **Commits:** _Conventional Commits_ `tipo(escopo): descrição`, com o escopo da área tocada (ex.: `docs(design)`, `feat(usuarios)`, `test(contrato)`). Ganchos locais com lefthook e as mesmas verificações no CI.
- **Tags:** baselines da documentação (`V0.1`, `V0.2`, `v0.3.0`) e versões de contrato, backend, front e infra; publicar somente após integrar e testar.
- **Rastreabilidade:** cada requisito funcional deve ser ligado ao cartão do Kanban, ao PR e ao commit que o implementa; não reescrever histórico já integrado.
