

# NexusDev — Projeto Integrador FATEC

> Plataforma proposta para centralizar o cadastro de clientes, o histórico de interações e a elaboração de propostas comerciais de uma software house.

## Sobre o projeto

O **NexusDev** é desenvolvido no âmbito do Projeto Integrador do curso de Gestão da Tecnologia da Informação da FATEC Barueri. A solução usa o **Krayin CRM** como base para o cadastro direto de clientes, o registro do histórico de interações e a elaboração de propostas comerciais.

O sistema é direcionado aos usuários internos da organização. Os perfis de acesso considerados no escopo atual são **Administrador**, **Gestor** e **Usuário operacional**, respeitando as permissões atribuídas a cada perfil.

## Escopo e diretrizes

- O Krayin CRM é utilizado como solução-base para as funcionalidades de CRM; o projeto não propõe desenvolver um CRM do zero.
- As funcionalidades e extensões do NexusDev devem respeitar os requisitos e as prioridades consolidados na documentação do projeto.
- O acesso é destinado aos perfis internos definidos para a solução.
- O Trello é utilizado como ferramenta externa de organização do trabalho da equipe acadêmica. **Não representa uma integração funcional do sistema NexusDev.**

## Organização deste repositório

Este repositório concentra principalmente a documentação técnica e acadêmica do NexusDev. Na versão atual, a raiz contém o README, as configurações de GitHub e a pasta `docs/`; não há diretórios `backend/` ou `frontend/` publicados nesta estrutura.

```text
FATEC_PROJETO_AAP/
├── .github/
│   └── workflows/
│       └── pr-check.yml
├── .gitignore
├── README.md
└── docs/
    ├── Arquitetura/
    ├── BPMN/
    ├── DER/
    ├── Declaracao_PI/
    ├── Levantamento_de_Requisitos/
    ├── Matriz_Rastreabilidade/
    ├── Monografia/
    ├── Padronizacao/
    ├── Requisitos_Consolidados/
    ├── UML/
    ├── prompts/
    └── stack/
```

## Documentação

Para localizar as especificações vigentes e os artefatos da entrega, consulte o [índice geral da documentação](./docs/INDICE_GERAL.md).

A documentação está organizada por assunto:

| Diretório | Conteúdo |
|---|---|
| [Arquitetura](./docs/Arquitetura) | Definições e organização dos módulos da solução |
| [BPMN](./docs/BPMN) | Modelagem dos processos de negócio |
| [DER](./docs/DER) | Diagrama e documentação do modelo de dados |
| [Declaração do PI](./docs/Declaracao_PI) | Documento de formalização do Projeto Integrador |
| [Levantamento de Requisitos](./docs/Levantamento%20de%20Requisitos) | Histórico do levantamento e da evolução do escopo |
| [Matriz de Rastreabilidade](./docs/Matriz_Rastreabilidade) | Relação entre requisitos e artefatos do projeto |
| [Monografia](./docs/Monografia) | Documento acadêmico do projeto |
| [Padronização](./docs/Padronizacao) | Materiais de referência e padronização |
| [Requisitos Consolidados](./docs/Requisitos_Consolidados) | Requisitos e regras de negócio consolidados |
| [UML](./docs/UML) | Casos de uso e diagramas UML |
| [Prompts e materiais de apoio](./docs/prompts) | Modelos e referências de apoio ao desenvolvimento |
| [Stack](./docs/stack) | Definições de tecnologia e arquitetura |

### Links úteis

- [Guia de contribuição e fluxo Git](./docs/guia_contribuicao_git_github.md)
- [Quadro de acompanhamento da equipe no Trello](https://trello.com/b/alTkE0Y8/209-aap2-aap3-c%C3%B3digo5)

## Fluxo de contribuição

As contribuições devem seguir o fluxo e os padrões descritos em [docs/guia_contribuicao_git_github.md](./docs/guia_contribuicao_git_github.md). Antes de iniciar uma alteração, consulte a documentação relacionada, mantenha os arquivos organizados em seus diretórios e utilize pull requests para revisão conforme as regras do repositório.

## Contexto acadêmico

| Campo | Informação |
|---|---|
| Instituição | FATEC Barueri |
| Curso | Gestão da Tecnologia da Informação |
| Componente | Projeto Integrador |
| Projeto | NexusDev |

---

Este repositório reúne os artefatos de análise, modelagem e documentação do Projeto Integrador NexusDev.

