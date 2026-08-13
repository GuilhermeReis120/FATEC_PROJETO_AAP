# 📁 FATEC — Projeto Integrador (NexusDev)
 
> Repositório central do **Projeto Integrador (PI)** da FATEC Barueri.
 
---
 
## 📌 Sobre o Projeto
 
Este repositório contém o **Projeto Integrador** do curso de **Gestão da Tecnologia da Informação (GTI)** da FATEC Barueri, desenvolvido por uma equipe de 7 alunos.
 
A proposta consiste em **identificar uma empresa real de pequeno porte** e, a partir de suas necessidades, **criar ou melhorar um sistema de software** que agregue valor ao negócio.
 
### A empresa parceira
 
A empresa escolhida é uma **software house** (Cristal) — uma empresa que desenvolve sistemas e soluções digitais para clientes. Como toda software house em fase de crescimento, ela enfrenta desafios comuns: gerenciar leads e clientes, acompanhar projetos em andamento, organizar sprints e centralizar a comunicação entre equipes e clientes.
 
### A solução proposta — NexusDev
 
Desenvolvimento de um sistema web integrado de **CRM + Gestor de Projetos**, construído sob medida para as necessidades operacionais da software house parceira.
 
O sistema permitirá:
 
- **CRM** — Gerenciamento do ciclo de vida do cliente: desde o primeiro contato (lead) até o pós-venda, com histórico de interações, propostas e contratos
- **Gestor de Projetos** — Acompanhamento de projetos em andamento, organização de sprints, controle de tarefas e visualização do progresso por equipe
---
 
## 🏗️ Estrutura do Repositório
 
Diferente de projetos anteriores, este é um **repositório único**, sem submódulos. Código e documentação convivem na mesma árvore de pastas.
 
```
NexusDev/
├── backend/                  ← Código Laravel (API, migrations, controllers)
├── frontend/                 ← Código Vue.js
├── database/                 ← Scripts e modelagem de banco
├── docs/
│   ├── BPMN/                 ← Diagramas de processos da empresa parceira
│   ├── Declaracao_PI/        ← Declaração e escopo do Projeto Integrador
│   ├── DER/                  ← Modelagem do banco de dados
│   ├── Monografia/           ← Monografia do PI
│   └── CONTRIBUTING.md       ← Guia de padronização Git do projeto
├── .gitignore
└── README.md
```
 
> **Regra simples:** tudo — código e documentação — vive neste mesmo repositório. Não há mais divisão em repositório principal + submodule de desenvolvimento.
 
---
 
## 💻 Stack de Tecnologia
 
A stack ainda está **em definição** pela equipe. Até o momento, as tecnologias em uso/avaliação são:
 
| Camada | Tecnologia (em avaliação) |
|---|---|
| Backend | Laravel (PHP) |
| Frontend | Vue.js 3 |
| Banco de Dados | MySQL |
| Infraestrutura | Docker + Docker Compose |
| Versionamento | Git + GitHub (repositório único) |
 
Este quadro será atualizado conforme a equipe fechar as decisões de arquitetura.
 
---
 
## 🚀 Como Clonar o Projeto
 
```bash
git clone git@github.com:<org>/NexusDev.git
cd NexusDev
```
 
Não há mais necessidade de `--recurse-submodules` — um clone padrão já traz todo o código e a documentação.
 
---
 
## 📂 Documentação
 
Toda a documentação do projeto está centralizada na pasta [`docs/`](./docs/).
 
| Arquivo / Pasta | Conteúdo |
|---|---|
| `docs/CONTRIBUTING.md` | Guia completo de uso do Git neste projeto: commits, branches e PRs |
| `docs/BPMN/` | Diagramas BPMN dos processos da empresa parceira |
| `docs/Declaracao_PI/` | Declaração e escopo do Projeto Integrador |
| `docs/DER/` | Modelagem do banco de dados |
| `docs/Monografia/` | Monografia do PI |
 
---
 
## 🔗 Links Rápidos
 
- 📋 [Guia de Padronização Git](./docs/CONTRIBUTING.md)
---
 
## 👥 Equipe
 
| Nome | Função |
|---|---|
| Guilherme Reis | Scrum Master / Dev Full-Stack |
| *(adicionar membros)* | — |
 
---
 
## 🎓 Informações Acadêmicas
 
| Campo | Informação |
|---|---|
| Instituição | FATEC Barueri |
| Curso | Gestão da Tecnologia da Informação |
| Disciplina | Projeto Integrador |
| Ano/Semestre (Início) | 2026/01 |
 
---
 
*Repositório único — código e documentação do Projeto Integrador NexusDev.*
 