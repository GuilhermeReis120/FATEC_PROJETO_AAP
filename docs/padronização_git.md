# 📋 Padronização Git — FATEC_PROJETO_AAP

> Guia de uso, boas práticas e convenções do Git para o projeto AAP da FATEC.  
> Aplicável ao repositório principal e ao submodule de desenvolvimento.

---

## 🗂️ Estrutura do Repositório

```
FATEC_PROJETO_AAP/                  ← Repositório principal (este guia)
├── Dev_projeto_aap_fatec/          ← Submodule → DEV_FATEC_PROJETO_AAP
├── Documentação/                   ← Arquivos de documentação do projeto
└── .gitmodules                     ← Configuração do submodule
```

O projeto é dividido em **dois repositórios Git distintos**:

| Repositório | Função | URL |
|---|---|---|
| `FATEC_PROJETO_AAP` | Repositório "guarda-chuva": agrupa documentação e o submodule de dev | `github.com/GuilhermeReis120/FATEC_PROJETO_AAP` |
| `DEV_FATEC_PROJETO_AAP` | Código-fonte real do projeto (backend Laravel + frontend Vue) | `github.com/GuilhermeReis120/DEV_FATEC_PROJETO_AAP` |

> ⚠️ **Regra de ouro:** alterações de código vão no submodule. Alterações de documentação vão no repositório principal. Os dois possuem commits e branches independentes.

---

## 🚀 Primeiros Passos — Clone e Configuração

### Clonando o projeto completo (com submodule)

```bash
# Clona o repositório principal E inicializa o submodule automaticamente
git clone --recurse-submodules git@github.com:GuilhermeReis120/FATEC_PROJETO_AAP.git
```

### Se já clonou sem o submodule

```bash
git clone git@github.com:GuilhermeReis120/FATEC_PROJETO_AAP.git
cd FATEC_PROJETO_AAP

# Inicializa e baixa o submodule manualmente
git submodule init
git submodule update
```

### Verificar se o submodule está ok

```bash
git submodule status
# Saída esperada: commit hash + nome da pasta + branch
# Ex: 961761e1... Dev_projeto_aap_fatec (main)
```

---

## 🔄 Fluxo de Trabalho Diário

### No repositório principal (Documentação / Estrutura)

```bash
# 1. Garantir que está atualizado
git checkout main
git pull origin main

# 2. Criar branch para a alteração (ver seção de branches)
git checkout -b feat/documentacao/adicionar-diagramas-bpmn

# 3. Fazer as alterações nos arquivos
# ...edite os arquivos necessários...

# 4. Adicionar ao stage
git add .
# ou de forma seletiva:
git add Documentação/nome-do-arquivo.md

# 5. Commitar (ver seção de commits)
git commit -m "[Feat](Documentação) Adição dos diagramas BPMN do fluxo de vendas"

# 6. Enviar a branch para o remoto
git push origin feat/documentacao/adicionar-diagramas-bpmn

# 7. Abrir Pull Request no GitHub (ver seção de PR)
```

### No submodule (Dev-backend / Dev-frontend)

```bash
# 1. Entrar na pasta do submodule
cd Dev_projeto_aap_fatec

# 2. Garantir que está atualizado
git checkout main
git pull origin main

# 3. Criar branch para a alteração
git checkout -b feat/dev-backend/implementar-autenticacao-jwt

# 4. Fazer as alterações no código
# ...edite os arquivos necessários...

# 5. Adicionar e commitar
git add .
git commit -m "[Feat](Dev-backend) Implementação da autenticação JWT com Laravel Sanctum"

# 6. Enviar a branch para o remoto do submodule
git push origin feat/dev-backend/implementar-autenticacao-jwt

# 7. Abrir Pull Request no GitHub do submodule
# 8. Após merge, voltar ao repo principal para atualizar o ponteiro
```

### Atualizando o ponteiro do submodule no repo principal

Após o merge de uma branch no submodule, o repositório principal precisa registrar o novo commit:

```bash
# Voltar para a raiz do projeto principal
cd ..

# Atualizar o submodule para o commit mais recente da main
git submodule update --remote Dev_projeto_aap_fatec

# Verificar o que mudou
git status
# Deve aparecer: "modified: Dev_projeto_aap_fatec (new commits)"

# Criar branch e commitar a atualização do ponteiro
git checkout -b feat/estrutura/atualizar-submodule-autenticacao
git add Dev_projeto_aap_fatec
git commit -m "[Feat](Estrutura) Atualização do ponteiro do submodule após merge de autenticação JWT"
git push origin feat/estrutura/atualizar-submodule-autenticacao

# Abrir PR no repositório principal
```

---

## ✏️ Padronização de Commits

### Formato

```
[Tipo](Local) Descrição objetiva no imperativo
```

### Tipos disponíveis

| Tag | Uso |
|---|---|
| `[Feat]` | Adição de algo novo (funcionalidade, arquivo, configuração, documentação nova) |
| `[Fix]` | Correção de bug, erro, texto incorreto ou configuração quebrada |
| `[Refactor]` | Refatoração de código sem alterar comportamento externo |
| `[Docs]` | Atualização exclusiva de documentação (README, comentários, guias) |
| `[Config]` | Alterações em arquivos de configuração (docker-compose, .env.example, etc.) |

> 💡 `[Docs]` é para pequenas correções em documentos existentes. Para documentos novos, use `[Feat]`.

### Locais disponíveis

| Tag | Onde aplicar |
|---|---|
| `(Estrutura)` | Arquivos da raiz do repo principal: `.gitmodules`, `docker-compose.yml`, `README.md` |
| `(Dev-frontend)` | Código Vue.js — componentes, rotas, stores, assets |
| `(Dev-backend)` | Código Laravel — controllers, models, migrations, routes, services |
| `(Documentação)` | Tudo dentro da pasta `Documentação/` — diagramas, PDFs, relatórios |

### Exemplos reais

```bash
# Novas funcionalidades
git commit -m "[Feat](Dev-backend) Implementação da stack de desenvolvimento do backend"
git commit -m "[Feat](Dev-frontend) Criação do componente de listagem de clientes"
git commit -m "[Feat](Documentação) Adição do diagrama BPMN de pós-venda"
git commit -m "[Feat](Estrutura) Configuração do Docker Compose com backend e frontend"

# Correções
git commit -m "[Fix](Dev-backend) Correção da política de CORS para ambiente de desenvolvimento"
git commit -m "[Fix](Dev-frontend) Correção da URL base do Axios no arquivo de configuração"
git commit -m "[Fix](Documentação) Correção de nomenclatura nas raias do diagrama BPMN"
git commit -m "[Fix](Estrutura) Correção do path do volume no docker-compose"

# Refatorações e configs
git commit -m "[Refactor](Dev-backend) Extração da lógica de autenticação para AuthService"
git commit -m "[Config](Estrutura) Atualização das variáveis de ambiente no .env.example"
git commit -m "[Docs](Documentação) Atualização do README com instruções de instalação"
```

### ❌ O que evitar nos commits

```bash
# Ruim — vago demais
git commit -m "ajustes"
git commit -m "update"
git commit -m "fix"

# Ruim — sem padrão
git commit -m "Adicionei o login"
git commit -m "corrigindo bug no backend"

# Ruim — múltiplas responsabilidades num único commit
git commit -m "implementei login e corrigi CORS e atualizei README"
```

> **Regra:** um commit = uma responsabilidade. Se precisou usar "e" na mensagem, provavelmente são dois commits.

---

## 🌿 Padronização de Branches

### Formato

```
tipo/local/descricao-em-kebab-case
```

### Exemplos

```bash
# Novas features
feat/dev-backend/implementar-autenticacao-jwt
feat/dev-frontend/criar-tela-de-dashboard
feat/documentacao/adicionar-diagrama-bpmn-vendas
feat/estrutura/configurar-docker-compose

# Correções
fix/dev-backend/corrigir-cors-producao
fix/dev-frontend/corrigir-rota-de-clientes
fix/documentacao/corrigir-nomenclatura-bpmn
fix/estrutura/corrigir-volume-docker

# Refatorações
refactor/dev-backend/extrair-service-de-relatorios
refactor/dev-frontend/reorganizar-estrutura-de-componentes
```

### Regras para branches

- Usar sempre **kebab-case** (letras minúsculas, separadas por hífen)
- Nunca usar espaços, underscores ou caracteres especiais
- Nome deve ser curto mas descritivo o suficiente para entender sem abrir o PR
- Nunca commitar diretamente em `main` — toda alteração passa por branch + PR

---

## 🔀 Fluxo de Pull Request (PR)

Após commitar e enviar a branch, **sempre abrir um Pull Request** para mesclar na `main`.

### Passo a passo no GitHub

1. Acesse o repositório no GitHub
2. Clique em **"Compare & pull request"** (aparece automaticamente após o push)  
   — ou vá em **Pull requests → New pull request**
3. Preencha o PR seguindo o padrão:

**Título do PR:** igual ao commit principal
```
[Feat](Dev-backend) Implementação da autenticação JWT com Laravel Sanctum
```

**Descrição do PR (sugerida):**
```markdown
## O que foi feito
Breve descrição do que foi implementado ou corrigido.

## Como testar
Passos para reproduzir/testar a alteração, se aplicável.

## Observações
Dependências, breaking changes, ou pontos de atenção.
```

4. Selecione `main` como branch de destino
5. Clique em **"Create pull request"**
6. Após revisão (ou auto-aprovação), clique em **"Merge pull request"**
7. **Delete a branch** após o merge para manter o repositório limpo

---

## ⚠️ Precauções e Cuidados

### Sobre o submodule

```bash
# ✅ SEMPRE entre na pasta do submodule para trabalhar no código
cd Dev_projeto_aap_fatec

# ❌ NUNCA rode git add/commit na raiz do projeto principal pensando
# que está commitando código. Você estaria commitando apenas o ponteiro.

# ✅ Ao clonar, SEMPRE use --recurse-submodules ou rode submodule init/update
# Se a pasta Dev_projeto_aap_fatec estiver vazia, é porque o submodule não foi inicializado.

# ✅ Após merge no submodule, atualize o ponteiro no repo principal
git submodule update --remote Dev_projeto_aap_fatec
```

### Nunca commitar direto na main

```bash
# ❌ Proibido
git checkout main
git add .
git commit -m "..."
git push origin main

# ✅ Correto
git checkout -b feat/dev-backend/nova-funcionalidade
# ... faz as alterações ...
git push origin feat/dev-backend/nova-funcionalidade
# Abre PR no GitHub
```

### Antes de começar qualquer alteração

```bash
# Sempre sincronize com o remoto antes de criar sua branch
git checkout main
git pull origin main

# No submodule, faça o mesmo
cd Dev_projeto_aap_fatec
git checkout main
git pull origin main
cd ..
```

### Nunca force push na main

```bash
# ❌ Jamais
git push origin main --force

# Isso sobrescreve o histórico e pode destruir trabalho de outros colaboradores.
# Force push só é permitido em branches pessoais de feature, nunca em main.
```

### Cuidado com arquivos sensíveis

```bash
# NUNCA commite:
# - Arquivos .env com senhas/chaves reais
# - Tokens de API, chaves SSH, credenciais de banco
# - node_modules/, vendor/ (dependências)

# Verifique o .gitignore antes de git add .
cat .gitignore

# Se commitou algo sensível por engano, remova do histórico imediatamente
# e considere rotacionar as credenciais expostas.
```

### Sincronização entre repositório principal e submodule

```bash
# O repositório principal armazena apenas um "ponteiro" (hash do commit)
# para o submodule, não o código em si.
#
# Se você fizer git clone sem --recurse-submodules, a pasta
# Dev_projeto_aap_fatec estará vazia. Isso é normal. Basta rodar:
git submodule init
git submodule update
```

---

## 📌 Referência Rápida

```bash
# === SETUP INICIAL ===
git clone --recurse-submodules git@github.com:GuilhermeReis120/FATEC_PROJETO_AAP.git
cd FATEC_PROJETO_AAP

# === INÍCIO DE QUALQUER TAREFA ===
git checkout main && git pull origin main
# (ou dentro do submodule)
cd Dev_projeto_aap_fatec && git checkout main && git pull origin main && cd ..

# === CRIAR BRANCH ===
git checkout -b feat/dev-backend/nome-da-feature

# === COMMITAR ===
git add .
git commit -m "[Feat](Dev-backend) Descrição objetiva"

# === ENVIAR E ABRIR PR ===
git push origin feat/dev-backend/nome-da-feature
# → Abrir Pull Request no GitHub

# === ATUALIZAR SUBMODULE APÓS MERGE ===
git submodule update --remote Dev_projeto_aap_fatec
git checkout -b feat/estrutura/atualizar-submodule-nome
git add Dev_projeto_aap_fatec
git commit -m "[Feat](Estrutura) Atualização do ponteiro do submodule após merge de nome-da-feature"
git push origin feat/estrutura/atualizar-submodule-nome
# → Abrir Pull Request no repositório principal
```

---

*Documento mantido em: `Documentação/padronização_git.md`*  
*Repositório: [FATEC_PROJETO_AAP](https://github.com/GuilhermeReis120/FATEC_PROJETO_AAP)*
