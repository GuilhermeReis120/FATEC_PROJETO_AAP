# 📁 FATEC — Projeto AAP

> Repositório central de documentação do **projeto interdisciplinar** da FATEC.

---

## 📌 Sobre o Projeto

Este repositório faz parte do **Projeto Interdisciplinar** do curso de **Gestão da Tecnologia da Infomração(GTI)** da FATEC Barueri.

A proposta da disciplina consiste em **identificar uma empresa real de pequeno porte** e, a partir de suas necessidades, **criar ou melhorar um sistema de software** que agregue valor ao negócio.

### A empresa parceira

A empresa escolhida é uma **software house** — uma empresa que desenvolve sistemas e soluções digitais para clientes. Como toda software house em fase de crescimento, ela enfrenta desafios comuns: gerenciar leads e clientes, acompanhar projetos em andamento, organizar sprints e centralizar a comunicação entre equipes e clientes.

### A solução proposta

Desenvolvimento de um sistema web integrado de **CRM + Gestor de Projetos**, construído sob medida para as necessidades operacionais da software house parceira.

O sistema permitirá:

- **CRM** — Gerenciamento do ciclo de vida do cliente: desde o primeiro contato (lead) até o pós-venda, com histórico de interações, propostas e contratos
- **Gestor de Projetos** — Acompanhamento de projetos em andamento, organização de sprints, controle de tarefas e visualização do progresso por equipe

---

## 🏗️ Estrutura dos Repositórios

Este projeto está dividido em **dois repositórios Git** com responsabilidades bem definidas:

```
FATEC_PROJETO_AAP/                    ← Você está aqui
├── Dev_projeto_aap_fatec/            ← Submodule → código-fonte
├── Documentação/                     ← Toda a documentação do projeto
│   ├── padronização_git.md           ← Guia de uso do Git neste projeto
│   └── ...                          ← Diagramas, relatórios, protótipos, etc.
└── .gitmodules
```

| Repositório | Responsabilidade |
|---|---|
| **`FATEC_PROJETO_AAP`** *(este)* | Central de documentação: diagramas BPMN, modelagem de dados, protótipos, relatórios, regras de negócio, guias de uso, monográfia. |
| **`DEV_FATEC_PROJETO_AAP`** *(submodule)* | Todo o código-fonte: backend Laravel, frontend Vue.js, configurações Docker e scripts de banco |

> **Regra simples:** Se é documentação → vai aqui. Se é código → vai no submodule.

---

## 💻 Stack de Tecnologia

| Camada | Tecnologia |
|---|---|
| Backend | Laravel (PHP) |
| Frontend | Vue.js 3 |
| Banco de Dados | MySQL |
| Infraestrutura | Docker + Docker Compose |
| Versionamento | Git + GitHub (com submodule) |

---

## 🚀 Como Clonar o Projeto

> Atenção: o projeto usa **Git Submodule**. É necessário clonar com a flag correta para obter o código de desenvolvimento junto.

```bash
# Clone completo (repositório principal + submodule de desenvolvimento)
git clone --recurse-submodules git@github.com:GuilhermeReis120/FATEC_PROJETO_AAP.git
```

Se você já clonou sem o submodule e a pasta `Dev_projeto_aap_fatec` está vazia:

```bash
git submodule init
git submodule update
```

Para acessar o repositório de desenvolvimento diretamente:

```bash
cd Dev_projeto_aap_fatec
```

---

## 📂 Documentação

Toda a documentação do projeto está centralizada na pasta [`Documentação/`](./Documentação/).

| Arquivo / Pasta | Conteúdo |
|---|---|
| `padronização_git.md` | Guia completo de uso do Git neste projeto: commits, branches, PRs e submodule |
| *(em construção)* | Diagramas BPMN dos processos da empresa |
| *(em construção)* | Modelagem do banco de dados (DER) |
| *(em construção)* | Protótipos de telas (Figma / wireframes) |
| *(em construção)* | Regras de negócio e requisitos do sistema |

---

## 🔗 Links Rápidos

- 🔧 [Repositório de Desenvolvimento (Submodule)](https://github.com/GuilhermeReis120/DEV_FATEC_PROJETO_AAP)
- 📋 [Guia de Padronização Git](./Documentação/padronização_git.md)

---

## 👥 Equipe

| Nome | Função |
|---|---|
| Guilherme Reis | Dev Full-Stack / Documentação |
| *(adicionar membros)* | — |

---

## 🎓 Informações Acadêmicas

| Campo | Informação |
|---|---|
| Instituição | FATEC |
| Curso | Gestão da Tecnologia da Informação |
| Disciplina | Projeto Integrador |
| Ano/Semestre (Início) | 2026/01 |

---

*Repositório principal — documentação e estrutura do projeto. Para o código-fonte, acesse o [submodule de desenvolvimento](https://github.com/GuilhermeReis120/DEV_FATEC_PROJETO_AAP).*
