# 📁 NexusDev — Projeto Integrador FATEC

> Repositório central do Projeto Integrador (PI) da FATEC Barueri, com backend, frontend e documentação organizados em um mesmo monorepo.

---

## 📌 Sobre o projeto

Este repositório reúne o desenvolvimento do sistema NexusDev, projeto do curso de Gestão da Tecnologia da Informação (GTI), criado para atender às necessidades de uma software house parceira.

A proposta do sistema é integrar funcionalidades de:

- CRM, para gestão de leads, clientes, históricos e propostas;
- gestor de projetos, para acompanhamento de tarefas, sprints e progresso por equipe;
- centralização de comunicação e organização operacional entre áreas internas e clientes.

---

## 🏗️ Arquitetura do repositório

O projeto está organizado em um monorepo com três grandes blocos:

- `backend/`: aplicação principal da API e regras de negócio;
- `frontend/`: interface web do sistema;
- `docs/`: documentação técnica e acadêmica do projeto.

```bash
Projeto_Fatec_AAP/
├── .github/
│   └── workflows/
├── .gitignore
├── README.md
├── docs/
│   ├── Arquitetura/
│   ├── BPMN/
│   ├── Backlog/
│   ├── Casos de Uso/
│   ├── CONTRIBUTING.md
│   ├── DER/
│   ├── Declaracao_PI/
│   ├── Levantamento de Requisitos/
│   ├── Matriz_Rastreabilidade/
│   ├── Monografia/
│   ├── Padronizacao/
│   ├── Requisitos_Consolidados/
│   ├── UML/
│   ├── prompts/
│   └── stack/
└── README.md
```

> A estrutura demonstra a separação clara entre aplicação e documentação: o código da solução está em `backend/` e `frontend/`, enquanto a documentação do projeto fica em `docs/`.

---

## 🧩 Componentes do sistema

### Backend

Localizado em [`backend/`](./backend).

Responsável por:

- API REST / backend de aplicação;
- autenticação e autorização;
- regras de negócio;
- persistência e operações com banco de dados;
- comunicação com o frontend.

Mais detalhes podem ser consultados em [backend/README.md](./backend/README.md).

### Frontend

Localizado em [`frontend/`](./frontend).

Responsável por:

- interface do sistema;
- componentes visuais;
- consumo da API;
- experiência do usuário e fluxo das telas.

Mais detalhes podem ser consultados em [frontend/README.md](./frontend/README.md).

### Documentação

Localizado em [`docs/`](./docs).

Contém:

- backlog;
- BPMN;
- DER;
- requisitos;
- casos de uso;
- UML;
- monografia;
- material de apoio e padronização.

---

## 🚀 Como executar o projeto

### Pré-requisitos

- Git
- Node.js e npm
- PHP e Composer
- Banco de dados compatível com o backend Laravel

### 1) Clonar o repositório

```bash
git clone <url-do-repositorio>
cd Projeto_Fatec_AAP
```

### 2) Rodar o backend

```bash
cd backend
cp .env.example .env
composer install
php artisan key:generate
php artisan migrate
php artisan serve
```

A aplicação backend ficará disponível em:

```bash
http://127.0.0.1:8000
```

### 3) Rodar o frontend

Em outro terminal:

```bash
cd frontend
npm install
npm run dev
```

A aplicação frontend ficará disponível em:

```bash
http://localhost:5173
```

---

## 📚 Documentação do projeto

A documentação principal está centralizada em [`docs/`](./docs/).

| Pasta / Arquivo | Conteúdo |
|---|---|
| [`docs/CONTRIBUTING.md`](./docs/CONTRIBUTING.md) | Guia de padronização Git e fluxo de contribuição |
| [`docs/Backlog/`](./docs/Backlog) | Backlog do projeto |
| [`docs/BPMN/`](./docs/BPMN) | Diagramas BPMN |
| [`docs/DER/`](./docs/DER) | Modelagem de dados |
| [`docs/Declaracao_PI/`](./docs/Declaracao_PI) | Declaração e escopo do PI |
| [`docs/Levantamento de Requisitos/`](./docs/Levantamento%20de%20Requisitos) | Levantamento de requisitos, perfis, regras de negócio e material de análise |
| [`docs/UML/`](./docs/UML) | Diagramas UML e casos de uso |
| [`docs/Monografia/`](./docs/Monografia) | Arquivos da monografia |
| [`docs/prompts/`](./docs/prompts) | Modelo de prompts e materiais de apoio |
| [`docs/stack/`](./docs/stack) | Documentação de stack e arquitetura |

---

## 🔗 Links rápidos

- [Guia de padronização Git](./docs/CONTRIBUTING.md)
- [README do backend](./backend/README.md)
- [README do frontend](./frontend/README.md)
- [Documentação geral](./docs)

---

## 👥 Equipe

| Nome | Função |
|---|---|
| Guilherme Reis | Scrum Master / Dev Full-Stack |
| *(adicionar membros)* | — |

---

## 🎓 Informações acadêmicas

| Campo | Informação |
|---|---|
| Instituição | FATEC Barueri |
| Curso | Gestão da Tecnologia da Informação |
| Disciplina | Projeto Integrador |
| Ano/Semestre (Início) | 2026/01 |

---

*Repositório do Projeto Integrador NexusDev — backend, frontend e documentação em um mesmo ambiente de desenvolvimento.*