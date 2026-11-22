# Cooperativa de Transportes — GCC188/UFLA

Sistema web de apoio à gestão financeira de uma **cooperativa de transportes**: API REST, interface web (SPA) e ambiente executável em contêineres, desenvolvido na disciplina GCC188 (UFLA, 2026-2). A cooperativa reúne motoristas autônomos (*cooperandos*) que prestam serviços de transporte a *clientes*; ela intermedeia o fluxo financeiro — recebe o pagamento do cliente, retém a taxa e repassa o valor líquido ao cooperando — cobrindo contratos com ciclo de aprovação, cronogramas de pagamento, baixas, repasses, despesas e relatórios.

## Estrutura da organização

O projeto é uma organização com cinco repositórios (decisão D03/Δ01 do Design):

| Repositório | Conteúdo |
|---|---|
| [gcc188-docs](https://github.com/gcc188-cooperativa/gcc188-docs) | **Âncora** — requisitos, design e protótipo de telas; README principal com instruções de uso, tecnologias e desvios declarados |
| [gcc188-api-contract](https://github.com/gcc188-cooperativa/gcc188-api-contract) | Contrato OpenAPI 3.1 da API (fonte de verdade; gera pacotes Java/npm) |
| [gcc188-backend](https://github.com/gcc188-cooperativa/gcc188-backend) | API REST (Java 25 + Spring Boot 4, PostgreSQL 18), migrações e testes |
| [gcc188-front](https://github.com/gcc188-cooperativa/gcc188-front) | Interface web (React 19, Mantine 9) — reservado para a próxima sprint |
| [gcc188-infra](https://github.com/gcc188-cooperativa/gcc188-infra) | Docker Compose, Caddy, backup, e2e e observabilidade |

## Regras de uso do Git (tarefa #21)

Valem para os cinco repositórios da organização e estão detalhadas no README de cada um e no [Design, cap. 3](https://github.com/gcc188-cooperativa/gcc188-docs/blob/master/Design/Design.pdf):

- **Ramos:** `master` protegido; backend e front usam _Git Flow_ adaptado (`develop` + `feat/*`, `fix/*`, `docs/*`), enquanto `gcc188-api-contract`, `gcc188-infra` e `gcc188-docs` usam _trunk-based_ com ramos curtos. PR revisado, verificações obrigatórias e _squash merge_.
- **Commits:** _Conventional Commits_ `tipo(escopo): descrição (RF-xxx-NN ou RNF-xx)`; o escopo segue a lista de `commitlint.config.cjs` de cada repositório. Ex.: `feat(contratos): aprovar contrato e gerar pagamentos (RF-CTR-04)`. Referência sugerida na tarefa: [iuricode/padrões-de-commits](https://github.com/iuricode/padroes-de-commits); adotamos Conventional Commits em vez disso por compatibilidade com commitlint, Release Please e geração automática de changelog.
- **Pastas:** requisitos, design e padrões em `gcc188-docs/{Requisitos,Design,Padrões Adotados}`; código, contrato e infraestrutura em seus respectivos repositórios. Artefatos gerados, cobertura, segredos e arquivos locais ficam fora do Git via `.gitignore`.
- **`.gitignore`:** ignora artefatos locais deste repositório de perfil/organização.
  - `node_modules/`: dependências de tooling local, caso instaladas.
  - `.env`, `.env.*` (exceto `.env.example`): configuração local e segredos.
  - `.idea/`, `.vscode/`, `*.iml`, `*.log`, `.DS_Store`, `Thumbs.db`: metadados de IDE, logs e arquivos de SO.
- **Verificação:** ganchos `lefthook` (commitlint e, onde configurado, lint/testes locais) mais workflows de governança no CI; versões e _changelog_ por Release Please.

Protótipo navegável das telas por perfil: <https://gcc188-cooperativa.github.io/gcc188-docs/>
