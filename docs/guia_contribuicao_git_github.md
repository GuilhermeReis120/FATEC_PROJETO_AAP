# 📋 Padronização Git — NexusDev (Projeto Integrador)

> Guia de uso, boas práticas e convenções do Git para o projeto NexusDev.
> Repositório único, com 7 desenvolvedores.

---

## 🗂️ Estrutura do Repositório

Backend (Laravel) e frontend (Vue.js) convivem na mesma árvore de pastas, versionados juntos.

```
NexusDev/
├── backend/          ← Código Laravel (API, migrations, models, controllers)
├── frontend/          ← Código Vue.js (componentes, rotas, stores)
├── docker-compose.yml
└── Documentação/      ← Diagramas, atas, relatórios do PI
```

---

## 🌿 Modelo de Branches

O fluxo tem **3 níveis**, do mais individual ao mais estável:

```
feat/<nome>-<descricao>   →   stage   →   main
```

| Branch | Quem usa | Função |
|---|---|---|
| `main` | — | Produção. Só recebe merge de `stage`. |
| `stage` | Todo o time | Homologação/integração. Recebe merge das branches `feat/<nome>-<descricao>` via PR. |
| `feat/<nome>-<descricao>` | Quem está fazendo a feature | Branch de trabalho do dia a dia, criada a partir da `stage` atualizada. |

### Exemplos de nomes

```bash
feat/guilherme-autenticacao-jwt
feat/joao-tela-dashboard
feat/maria-diagrama-bpmn-vendas
```

### Regras

- Kebab-case, sem espaços, underscores ou acentos.
- Toda `feat/*` nasce da `stage` atualizada e volta pra ela via PR.
- Nunca commitar direto em `main` ou `stage`.

---

## 🔒 Proteção de Branches (configurar no GitHub)

Regras de disciplina no papel não seguram ninguém sob pressão de prazo — quem garante isso é a configuração do repositório. Em **Settings → Branches → Branch protection rules**, aplicar em `main` e `stage`:

- ☑️ Require a pull request before merging (bloqueia push direto).
- ☑️ Require approvals — mínimo **1** review antes do merge.
- ☑️ Require status checks to pass before merging (assim que houver CI configurado — ver seção abaixo).
- ☑️ Require branches to be up to date before merging (evita merge de branch desatualizada).
- ☑️ Do not allow force pushes.
- ☑️ Do not allow deletions.

Isso transforma as regras de "Nunca commitar direto em `main` ou `stage`" e "Nunca force push" (mais abaixo neste documento) em algo que o próprio GitHub recusa, em vez de depender só de acordo verbal entre os 7 integrantes.

---

## 🔄 Fluxo de Trabalho Diário

### 1. Trabalhando em uma feature

```bash
# 1. Atualizar a stage local
git checkout stage
git pull origin stage

# 2. Criar a branch da feature a partir da stage
git checkout -b feat/guilherme-autenticacao-jwt

# 3. Codar, testar localmente
# ...

# 4. Commitar (ver padrão de commits abaixo)
git add .
git commit -m "[Feat](Backend) Implementação da autenticação JWT com Sanctum"

# 5. Subir a feature
git push origin feat/guilherme-autenticacao-jwt

# 6. Abrir PR no GitHub: feat/guilherme-autenticacao-jwt → stage
```

> 💡 Se a `stage` avançou enquanto você trabalhava na feature, traga as atualizações pra dentro da sua branch (`git pull origin stage`, resolvendo conflitos localmente) antes de abrir o PR — é sempre mais seguro resolver conflito na sua própria branch do que deixar o GitHub tentar resolver automaticamente.

Após o merge, apague a `feat/*` (o próprio GitHub oferece esse botão na tela do PR).

### 2. Consolidando `stage` na `main`

Só o **responsável designado** (ex.: você, como scrum master) faz esse merge, e só depois que a `stage` foi testada em conjunto pelo time.

```bash
git checkout main
git pull origin main
git merge stage
git push origin main

# opcional: marcar o fim de uma sprint como uma versão
git tag -a v0.1.0 -m "Entrega Sprint 1"
git push origin v0.1.0
```

Nunca uma `feat/*` vai direto pra `main` — sempre passa pela `stage` primeiro.

> 💡 Como o PI tem 4 sprints com entregas fixas, uma tag por sprint (`v0.1.0`, `v0.2.0`...) na `main` facilita voltar no tempo depois pra ver "o que exatamente entregamos na Sprint 2" — sem precisar caçar o commit certo no histórico.

---

## ✏️ Padronização de Commits

### Formato

```
[Tipo](Local) Descrição objetiva no imperativo
```

### Tipos

| Tag | Uso |
|---|---|
| `[Feat]` | Algo novo (funcionalidade, arquivo, config, documentação nova) |
| `[Fix]` | Correção de bug, erro ou config quebrada |
| `[Refactor]` | Refatoração sem alterar comportamento externo |
| `[Docs]` | Atualização de documentação existente |
| `[Config]` | Alterações em arquivos de configuração (docker-compose, .env.example) |

### Locais

| Tag | Onde aplicar |
|---|---|
| `(Backend)` | Código Laravel — controllers, models, migrations, routes, services |
| `(Frontend)` | Código Vue.js — componentes, rotas, stores, assets |
| `(Documentação)` | Tudo dentro de `Documentação/` |
| `(Estrutura)` | Arquivos da raiz: `docker-compose.yml`, `.gitignore`, `README.md` |

### Exemplos

```bash
git commit -m "[Feat](Backend) Implementação da autenticação JWT com Sanctum"
git commit -m "[Feat](Frontend) Criação do componente de listagem de clientes"
git commit -m "[Fix](Backend) Correção da política de CORS para ambiente de desenvolvimento"
git commit -m "[Docs](Documentação) Atualização do diagrama BPMN de pós-venda"
git commit -m "[Config](Estrutura) Ajuste das variáveis de ambiente no .env.example"
```

### ❌ Evitar

```bash
git commit -m "ajustes"
git commit -m "fix"
git commit -m "implementei login e corrigi CORS e atualizei README"   # duas responsabilidades
```

> **Regra:** um commit = uma responsabilidade.

---

## 🔀 Fluxo de Pull Request

Todo merge pra `stage` ou `main` passa por PR — nunca push direto.

1. Push da branch `feat/<nome>-<descricao>`.
2. No GitHub: **Compare & pull request**.
3. Preencher a descrição (ver template abaixo).
4. Branch de destino: `stage` (para PRs de feature) ou `main` (só o responsável, a partir da `stage`).
5. Se houver CI configurado (ver seção seguinte), esperar os checks passarem antes de pedir review.
6. Pelo menos 1 review antes do merge em `stage`.
7. Após merge, apagar a `feat/*`.

### Template de PR

Em vez de colar esse checklist manualmente em cada PR, salvar como `.github/PULL_REQUEST_TEMPLATE.md` — o GitHub preenche automaticamente a descrição de toda PR nova com ele:

```markdown
## O que foi feito
Breve descrição do que foi implementado ou corrigido.

## Como testar
Passos para reproduzir/testar a alteração.

## Observações
Dependências, breaking changes, pontos de atenção (ex.: nova migration).
```

---

## ⚙️ CI (integração contínua)

Com 7 pessoas mesclando na `stage` toda semana, checar manualmente se o backend e o frontend continuam funcionando não escala. Um workflow simples de GitHub Actions, disparado em toda PR pra `stage` e `main`, já resolve a maior parte:

- Backend: `composer install`, `php artisan test` (ou `phpunit`).
- Frontend: `npm install`, `npm run lint`, `npm run build`.

Não precisa ser elaborado — mesmo rodando só lint + build já pega erro de sintaxe e import quebrado antes de chegar na `stage`. Isso é o "Require status checks to pass" mencionado na seção de proteção de branches: sem o CI configurado, essa opção não tem o que checar.

### CODEOWNERS (opcional, se o time crescer em especialização)

Se, com o tempo, ficar claro que certas pastas são "território" de alguém (ex.: migrations e models só passam por quem desenhou o banco), um arquivo `.github/CODEOWNERS` pode exigir a aprovação dessa pessoa automaticamente:

```
/backend/database/migrations/  @guilherme
/docker-compose.yml             @guilherme
```

---

## ⚠️ Precauções

### Nunca commitar direto em `main` ou `stage`

```bash
# ❌ Proibido
git checkout stage
git add . && git commit -m "..." && git push origin stage

# ✅ Correto: sempre via feat/<nome>-<descricao> + PR
```

### Nunca force push em `main` ou `stage`

```bash
# ❌ Jamais
git push origin main --force
git push origin stage --force

# Force push só é aceitável na sua própria feat/*, se ainda não foi mesclada em nenhum lugar.
```

### Migrations (atenção especial com 7 pessoas)

- Antes de criar uma migration nova, dê um aviso rápido no grupo — duas pessoas criando migrations parecidas ao mesmo tempo é a causa mais comum de conflito feio.
- Ao atualizar sua `feat/*` com a `stage`, rode `php artisan migrate:fresh` localmente (ambiente de dev, nunca em produção) pra garantir que as migrations de todo o time realmente funcionam juntas antes de abrir o PR.

### Arquivos sensíveis

```bash
# NUNCA commitar:
# - .env com senhas/chaves reais
# - Tokens de API, chaves SSH, credenciais de banco
# - node_modules/, vendor/

cat .gitignore   # confira antes de git add .
```

Se algo sensível foi commitado por engano, remova do histórico imediatamente e rotacione a credencial exposta.

---

## 📌 Referência Rápida

```bash
# === NOVA FEATURE ===
git checkout stage
git pull origin stage
git checkout -b feat/<seu-nome>-<descricao>
git add . && git commit -m "[Feat](Backend) Descrição objetiva"
git push origin feat/<seu-nome>-<descricao>
# → Abrir PR no GitHub: feat/<seu-nome>-<descricao> → stage

# === STAGE → MAIN (só o responsável) ===
git checkout main && git pull origin main
git merge stage
git push origin main
```

---

*Documento mantido em: `Documentação/padronizacao_git.md`*