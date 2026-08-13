# 🌱 Base Sólida de Git e GitHub

> Guia para quem está começando do zero. O objetivo aqui não é decorar comando — é entender **o que cada coisa faz e por quê**, pra você conseguir resolver problemas sozinho(a) mesmo quando a situação não for exatamente igual a um exemplo deste guia.

---

## 1. O que é Git e o que é GitHub (são coisas diferentes!)

- **Git** é um programa que roda no seu computador e guarda o **histórico de tudo que você mudou** nos arquivos de um projeto — como um "controle de versões" bem detalhado. Ele funciona mesmo sem internet.
- **GitHub** é um site que guarda uma cópia do seu projeto Git na nuvem, pra várias pessoas trabalharem juntas no mesmo código sem se atropelar.

Ou seja: **Git = ferramenta local. GitHub = onde a cópia compartilhada mora.** Todo comando que começa com `git` roda no seu computador. Alguns deles (`push`, `pull`, `fetch`, `clone`) conversam com o GitHub pela internet.

---

## 2. Conceitos que você precisa entender antes de rodar qualquer comando

### Repositório (repo)
A pasta do projeto, com todo o histórico de mudanças guardado dentro de uma subpasta escondida (`.git`). Se essa pasta some, o histórico some com ela.

### Commit
Um "print" de como os arquivos estavam em um determinado momento, com uma mensagem explicando o que mudou. Commits pequenos e frequentes são melhores que um commit gigante no final do dia — se algo quebrar, é muito mais fácil achar em qual commit pequeno o problema entrou.

### Branch (ramificação)
Uma "linha do tempo" separada do projeto. Você pode criar uma branch pra testar algo sem bagunçar o código que já está funcionando em outra branch. No nosso projeto, cada pessoa tem a sua (`dev/<seu-nome>`), e dentro dela ainda existem branches menores pra cada tarefa (`feat/...`).

### Remoto (remote / origin)
O "endereço" do repositório no GitHub. Quando você vê `origin` num comando, é uma referência a esse endereço — não precisa decorar a URL toda vez.

### Área de stage (não confundir com a branch `stage` do projeto!)
Antes de fazer um commit, o Git tem uma "área de rascunho" onde você escolhe **quais arquivos alterados** vão entrar no próximo commit. É o que o `git add` faz. Isso é um conceito do Git em si — não tem relação com a branch chamada `stage` que a gente usa neste projeto pra homologação. São dois usos diferentes da mesma palavra, e isso confunde muita gente no início.

### HEAD
É só um ponteiro pra "onde você está agora". Quando você troca de branch, o HEAD se move com você. Se um dia aparecer a mensagem `detached HEAD`, quer dizer que você está "fora" de qualquer branch — normalmente basta um `git checkout nome-da-branch` pra voltar ao normal.

---

## 3. Configuração inicial (só uma vez, por computador)

```bash
# Diz ao Git quem é você (aparece nos seus commits)
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
```

### Chave SSH (pra não digitar senha toda hora ao conversar com o GitHub)

```bash
# Gera uma chave (se ainda não tiver uma)
ssh-keygen -t ed25519 -C "seu-email@exemplo.com"

# Mostra a chave pública, pra copiar e colar no GitHub
cat ~/.ssh/id_ed25519.pub
```

Depois, no GitHub: **Settings → SSH and GPG keys → New SSH key**, cole o conteúdo copiado. Isso é o que permite clonar/enviar código usando `git@github.com:...` em vez de `https://github.com/...`.

> Se ao rodar um comando o terminal pedir "Enter passphrase for key", é a senha que você mesmo definiu ao criar a chave SSH — não é bug, é proteção extra.

---

## 4. Os comandos que você vai usar 90% do tempo

### `git status`
Mostra o que mudou desde o último commit e em qual branch você está. **Rode isso o tempo todo** — é o comando mais seguro que existe, só mostra informação, não muda nada.

### `git clone <url>`
Baixa uma cópia completa de um repositório do GitHub pra sua máquina. Só é feito uma vez, no começo.

### `git checkout <branch>`
Troca de branch. Se a branch já existe no remoto mas não na sua máquina ainda, o Git é inteligente e cria a versão local automaticamente rastreando a remota.

### `git checkout -b <nova-branch>`
Cria uma branch nova (a partir da branch em que você está) e já muda pra ela.

### `git add <arquivo>` ou `git add .`
Coloca arquivos na "área de stage" (ver seção 2), preparando pro próximo commit. `git add .` adiciona tudo que mudou na pasta atual.

### `git commit -m "mensagem"`
Cria o "print" com os arquivos que estão na área de stage. A mensagem deve dizer *o que* foi feito, não *como* (ver padrão de commits no `CONTRIBUTING.md` do projeto).

### `git push origin <branch>`
Envia os commits que você fez localmente pro GitHub, na branch indicada.

### `git pull origin <branch>`
Baixa e já mescla as mudanças que estão no GitHub na branch indicada, dentro da branch em que você está agora.

### `git fetch origin`
Baixa informações sobre o que existe no remoto (branches novas, commits novos) **sem mesclar nada** na sua branch atual. É o comando mais seguro pra "ver o que tem de novo" antes de decidir o que fazer.

> **Regra de ouro:** `fetch` só olha, `pull` olha e já aplica. Na dúvida, use `fetch` primeiro.

### `git branch`
Lista as branches que existem na sua máquina. A branch com `*` na frente é a que você está agora.

### `git log`
Mostra o histórico de commits. Adicione `--oneline` (`git log --oneline`) pra ver um resumo mais legível.

### `git diff`
Mostra exatamente **quais linhas** mudaram nos arquivos, antes de você dar `add`. Ótimo pra revisar seu próprio trabalho antes de commitar.

---

## 5. O fluxo de trabalho no dia a dia (resumido)

O fluxo completo e específico do projeto está no `CONTRIBUTING.md` — aqui vai a lógica por trás dele, pra você entender o "porquê":

1. Você trabalha isolado(a) na sua própria branch (`feat/...`), sem afetar o código dos outros.
2. Quando termina, junta sua `feat/*` na sua branch pessoal (`dev/<seu-nome>`).
3. Periodicamente, sua `dev/<nome>` é enviada pra `stage`, onde o código de todo mundo se encontra e é testado junto.
4. Só depois de testado em conjunto, o responsável leva a `stage` pra `main` (produção).

Trabalhar assim evita que o erro de uma pessoa quebre o trabalho de todo o time enquanto ainda está sendo feito.

---

## 6. Conflitos de merge — o que são e como não ter medo deles

Um conflito acontece quando **duas pessoas mudaram a mesma linha do mesmo arquivo** de formas diferentes, e o Git não sabe qual versão manter. Não é erro, é normal, principalmente com 7 pessoas no mesmo projeto.

Quando acontece, o Git marca o arquivo assim:

```
<<<<<<< HEAD
sua versão da linha
=======
versão que veio de outra branch
>>>>>>> nome-da-outra-branch
```

O que fazer:
1. Abra o arquivo, decida qual versão (ou combinação das duas) deve ficar.
2. Apague as linhas `<<<<<<<`, `=======` e `>>>>>>>` — elas são só marcações do Git, não fazem parte do código.
3. Salve, dê `git add <arquivo>` e depois `git commit` normalmente (sem `-m`, o Git já sugere uma mensagem de merge).

---

## 7. Erros comuns e o que eles realmente significam

| Mensagem | O que está acontecendo | Solução |
|---|---|---|
| `fatal: no branch named 'X'` | Você tentou usar uma branch que não existe **localmente** | `git fetch origin` e depois `git checkout X` |
| `fatal: a branch named 'X' already exists` | Já existe uma branch com esse nome (às vezes por diferença de maiúscula/minúscula, comum no WSL) | `git branch -D X` pra apagar a local e recriar certo |
| `error: unable to delete 'X': remote ref does not exist` | Você tentou apagar no remoto algo que só existe localmente | Confirme com `git branch -a` onde a branch realmente existe |
| `Permission denied (publickey)` | Sua chave SSH não está cadastrada no GitHub, ou não foi carregada | Revise o passo 3 (chave SSH) |
| `Your branch is behind 'origin/X'` | Alguém enviou commits novos que você ainda não tem | `git pull origin X` |
| `Your branch and 'origin/X' have diverged` | Você e o remoto têm commits diferentes — precisa decidir como juntar | `git pull origin X` (vai gerar um merge) e resolver conflitos se aparecerem |
| Terminal pedindo `Enter passphrase for key` | Normal, é a senha da sua chave SSH | Só digitar |

---

## 8. Boas práticas que evitam 90% dos problemas

- Rode `git status` antes e depois de qualquer comando que você não tenha certeza do efeito.
- Nunca commite direto em `main` ou `stage` — sempre pela sua branch.
- Nomes de branch: sempre minúsculo, sempre kebab-case (`dev/guilherme`, nunca `dev/Guilherme`).
- Commits pequenos e frequentes, com mensagem clara — facilita achar problemas depois.
- Antes de começar qualquer tarefa nova, dê `git pull` ou `git fetch` pra garantir que está partindo do código mais atual.

---

## 9. Pra continuar aprendendo

Este guia cobre o suficiente pra trabalhar com autonomia no dia a dia. Pra aprofundar quando tiver tempo:
- [Learn Git Branching](https://learngitbranching.js.org/?locale=pt_BR) — visualiza branches e comandos interativamente, em português.
- [Documentação oficial do Git (git-scm.com)](https://git-scm.com/book/pt-br/v2) — livro completo, gratuito, em português.
- [GitHub Docs](https://docs.github.com/pt) — documentação oficial do GitHub, em português.

---

*Dúvida no dia a dia do projeto específico? Consulte o `CONTRIBUTING.md`. Dúvida de conceito de Git/GitHub em geral? Volte a este guia.*
