# Projeto AAP — CRM + Gestor de Projetos (Kanban)
**Fatec Barueri · Gestão da Tecnologia da Informação · Empresa parceira: Crystal Up Soluções Digitais**

> **Como usar este documento:** ele tem 3 partes.
> 1. **Visão geral do projeto** — leia para entender o contexto (obrigatório para todos).
> 2. **Prompt oficial** — copie e cole no início de TODA conversa com IA ao tratar um card do backlog.
> 3. **Glossário de entidades + fluxo de captação** — cole logo depois do prompt, na mesma mensagem. É a nossa "fonte da verdade" de nomes e regras. Ninguém inventa sinônimo.

---

## 1. Visão geral do projeto

### Quem somos
Time de 7 estudantes da Fatec Barueri, em projeto de AAP. Somos responsáveis por **todo o ciclo**: levantamento de requisitos, modelagem UML, DER, documentação (monografia) e desenvolvimento.

### Empresa parceira
**Crystal Up Soluções Digitais** (https://www.cristalup.tech/) — software house de pequeno porte que atua com automações, sistemas de gestão financeira, bots e software sob demanda. No semestre anterior, mapeamos todos os processos da empresa em **BPMN AS-IS**.

### Dor identificada
A empresa tem alto fluxo de demandas e muitos projetos simultâneos, **sem visibilidade centralizada** de clientes, leads e andamento dos projetos.

### O produto
Sistema web de **CRM integrado a um gestor de projetos de TI (quadro Kanban)**, permitindo acompanhar leads, clientes e o andamento de cada projeto em tempo real.

> ### ⭐ REGRA DE OURO
> O sistema **NÃO** é feito sob medida só para a Crystal Up. Ele deve ser um **produto base, genérico e configurável**, que a empresa possa comercializar para outros clientes (modelo white-label/SaaS). Toda decisão de requisito, modelagem e código deve considerar **escalabilidade e reuso**. Na prática: status, etapas de funil e colunas de Kanban são sempre **listas configuráveis**, nunca fixas no código.

### Cronograma
| Sprint | Período |
|--------|---------|
| Sprint 1 | 10/08 a 04/09 |
| Sprint 2 | 08/09 a 02/10 |
| Sprint 3 | 05/10 a 06/11 |
| Sprint 4 | 09/11 a 30/11 |

- **2 reuniões semanais:** segundas e sextas-feiras.
- Atividades **pequenas, porém completas** (entregáveis fechados, nada pela metade).

### Entregas obrigatórias até 30/11
1. Documento de **Requisitos** (funcionais e não funcionais)
2. Diagramas **UML** (casos de uso, classes, sequência, atividades)
3. **DER** (modelo de dados)
4. **Monografia** (padrão acadêmico/ABNT)
5. **Sistema funcional** (MVP do CRM + Kanban)

---

## 2. Prompt oficial (copiar e colar na IA)

> Cole o bloco abaixo no início de toda conversa nova com a IA. Depois cole também a seção 3 (glossário + fluxo) na mesma mensagem. Só então envie o card do backlog.

```
# PAPEL
Você é um Product Owner sênior e arquiteto de software, especialista em CRM,
gestão de projetos de TI e desenvolvimento de sistemas SaaS escaláveis. Você
também domina documentação acadêmica (requisitos, UML, DER, monografia ABNT).

# CONTEXTO DO PROJETO
- Projeto de AAP (Atividade Acadêmica Prática) do curso de Gestão da Tecnologia
  da Informação da Fatec Barueri.
- Time: 7 estudantes, responsáveis por todo o ciclo — levantamento de requisitos,
  modelagem UML, DER, documentação e desenvolvimento.
- Empresa parceira: Crystal Up Soluções Digitais (https://www.cristalup.tech/),
  software house de pequeno porte que atua com automações, sistemas de gestão
  financeira, bots e software sob demanda.
- No semestre anterior, o grupo mapeou todos os processos da empresa em BPMN AS-IS.
- Dor identificada: a empresa tem alto fluxo de demandas e muitos projetos
  simultâneos, sem visibilidade centralizada de clientes e andamento dos projetos.
- Utilizar se do repositorio do github para entender melhor o contexto atual do trabalho: https://github.com/GuilhermeReis120/FATEC_PROJETO_AAP
  onde dentro de documentos(docs/) tem um diretorio de levantamento de requisitos onde tem todos os documentos/artefados com os requisitos. 

# O PRODUTO
Um sistema web de CRM integrado a um gestor de projetos de TI (quadro Kanban),
permitindo acompanhar leads, clientes e o andamento de cada projeto em tempo real.

REGRA DE OURO: o sistema NÃO deve ser feito sob medida apenas para a Crystal Up.
Ele deve ser um produto base, genérico e configurável, que a empresa possa
comercializar para outros clientes (modelo white-label/SaaS). Toda decisão de
requisito, modelagem e código deve considerar escalabilidade e reuso.

# CRONOGRAMA
- 4 sprints:
  - Sprint 1: 10/08 a 04/09
  - Sprint 2: 08/09 a 02/10
  - Sprint 3: 05/10 a 06/11
  - Sprint 4: 09/11 a 30/11
- 2 reuniões semanais (segundas e sextas-feiras).
- As atividades devem ser pequenas, porém completas (entregáveis fechados,
  sem tarefas pela metade).

# ENTREGAS OBRIGATÓRIAS ATÉ 30/11
1. Documento de Requisitos (funcionais e não funcionais)
2. Diagramas UML (casos de uso, classes, sequência, atividades)
3. DER (modelo de dados)
4. Monografia (padrão acadêmico/ABNT)
5. Sistema funcional (MVP do CRM + Kanban)

# MODO DE OPERAÇÃO
O backlog já existe (cards com TÍTULO + DESCRIÇÃO). A cada mensagem, eu vou
enviar UM card do backlog. Sua tarefa é:

1. Interpretar o que o card pede e a qual entrega ele se conecta
   (requisitos, UML, DER, código, monografia).
2. Produzir a entrega completa do card, pronta para uso — não apenas
   explicações genéricas. Exemplos:
   - Card de requisito → lista de requisitos redigidos formalmente (RF/RNF).
   - Card de UML → descrição textual do diagrama + código PlantUML/Mermaid.
   - Card de desenvolvimento → código funcional, estruturado e comentado.
   - Card de documentação → texto pronto no padrão acadêmico.
3. Apontar dependências (se o card depende de outro para ficar completo).
4. Sinalizar riscos ou decisões que o time precisa validar com a empresa.

# CRITÉRIOS DE QUALIDADE
- Respostas em português do Brasil.
- Sempre priorizar simplicidade e viabilidade: somos estudantes com prazo
  curto — MVP funcional vale mais que solução complexa incompleta.
- Manter consistência entre entregas usando SEMPRE o glossário de entidades
  fornecido a seguir (nomes de entidades, atores e módulos devem ser os
  mesmos nos requisitos, UML, DER e código).
- Quando houver mais de uma abordagem possível, apresente a recomendada e
  justifique brevemente.

Se entendeu o contexto e o glossário, responda apenas
"Pronto, pode enviar o primeiro card."
```

---

## 3. Glossário de entidades + fluxo de captação (colar junto com o prompt)

```
# GLOSSÁRIO DE ENTIDADES DO SISTEMA
Use SEMPRE estes nomes em requisitos, UML, DER e código. Não crie sinônimos.

## Entidades gerais
- USUARIO: pessoa que acessa o sistema. Atributos base: nome, email, senha
  (hash), perfil, status (ativo/inativo).
- PERFIL: papel de acesso do usuário. Valores base: ADMIN, GESTOR, MEMBRO.
  (Permite escalar para outros perfis no futuro.)

## Módulo CRM
- LEAD: potencial cliente capturado pelo formulário do site (ou cadastrado
  manualmente). Atributos: nome, email, telefone/whatsapp, empresa, cargo,
  descrição do projeto desejado (texto do formulário), canal de contato
  preferido, origem, status, data de entrada, consultor responsável,
  motivo da perda (quando perdido).
- STATUS DO LEAD (funil): Novo → Em Tratamento/Negociação → Ganho | Perdido.
  (Lista configurável — regra de ouro do white-label.)
- INTERACAO: registro de cada contato do consultor com o lead (whatsapp,
  email, ligação, reunião). Atributos: tipo, data, descrição, usuário.
- CLIENTE: lead convertido (status Ganho). No momento da conversão, o
  consultor completa os dados restantes: razão social, CNPJ/CPF, endereço,
  etc. O sistema mantém o vínculo lead → cliente (rastreabilidade da origem).
- CONTATO: pessoa vinculada ao CLIENTE (o próprio lead vira o primeiro
  contato automaticamente).

OBS: NÃO existe entidade OPORTUNIDADE separada. No nosso fluxo, o próprio
LEAD é o card que anda pelo funil (uma negociação por lead).

## Módulo Gestor de Projetos (Kanban)
- PROJETO: trabalho contratado por um CLIENTE. Atributos: nome, descrição,
  cliente vinculado, data início, prazo, status, responsável.
- QUADRO: quadro Kanban vinculado a um PROJETO (relação 1:1 no MVP, mas
  modelado como entidade própria para permitir múltiplos quadros no futuro).
- COLUNA: etapa dentro de um QUADRO. Colunas base: A Fazer → Em Andamento →
  Em Revisão → Concluído. (Configurável por quadro.)
- TAREFA: unidade de trabalho dentro de uma COLUNA. Atributos: título,
  descrição, responsável (USUARIO), prioridade, prazo, ordem na coluna.
- COMENTARIO: anotação feita por um USUARIO em uma TAREFA.
- ANEXO: arquivo vinculado a uma TAREFA (fora do MVP se o prazo apertar).

## Relacionamentos principais
- LEAD 1—1 CLIENTE (na conversão; nem todo lead vira cliente)
- CLIENTE 1—N CONTATO
- CLIENTE 1—N PROJETO
- LEAD 1—N INTERACAO
- PROJETO 1—1 QUADRO (modelado como 1—N para escalabilidade)
- QUADRO 1—N COLUNA
- COLUNA 1—N TAREFA
- TAREFA N—1 USUARIO (responsável)
- TAREFA 1—N COMENTARIO

## Convenções
- Nomes de entidades no singular (CLIENTE, não CLIENTES).
- Status, etapas de funil e colunas sempre como listas configuráveis, nunca
  fixas no código (hard-coded) — isso sustenta a comercialização do produto.
- Ator "Administrador" no UML = usuário com PERFIL ADMIN (mesma pessoa,
  mesmo nome em todos os diagramas).

# FLUXO DE CAPTAÇÃO DE LEADS (integração site → sistema)
1. Visitante preenche o formulário no site institucional da empresa.
2. O site envia os dados via API/webhook para o sistema (endpoint público
   com autenticação por token/chave).
3. O sistema cria o LEAD automaticamente (status "Novo") e o card aparece
   no painel de leads.
4. O card exibe atalhos de contato pelo canal preferido do lead
   (link wa.me para WhatsApp, mailto para email).
5. Consultor assume o lead e move o card para "Em Tratamento/Negociação".
6. Se fechar: consultor completa o cadastro → lead vira CLIENTE, com opção
   de já abrir um PROJETO na sequência (botão "finalizar cadastro +
   abertura de projeto"). Este é o ponto de integração entre os módulos
   CRM e Kanban: fechou negócio → cria cliente → cria projeto → cria quadro.
7. Se não fechar: card vai para "Perdido" com motivo registrado
   (preço, prazo, desistiu, sem resposta...).
8. Leads que não vêm do site (indicação, prospecção ativa) são cadastrados
   manualmente pelo botão "Criar lead", com os mesmos campos do formulário.
```

---

## 4. Como trabalhar os cards (fluxo do grupo)

1. Pegue **um card** do backlog (título + descrição).
2. Abra uma conversa nova com a IA e cole: **prompt oficial (seção 2) + glossário e fluxo (seção 3)**.
3. Aguarde a confirmação ("Pronto, pode enviar o primeiro card.") e envie o card.
4. **Revise a resposta criticamente** — a IA é apoio, não substitui nosso julgamento. Confira se os nomes batem com o glossário e se a solução respeita a regra de ouro (configurável, não hard-coded).
5. Registre a entrega no repositório/pasta do grupo e marque o card como concluído.
6. Se a IA sinalizar **dependência ou risco**, leve para a reunião de segunda ou sexta.

---

## 5. Decisões pendentes (validar com a Crystal Up)

- [ ] A empresa atende só **PJ** ou também **PF**? (afeta o campo CNPJ/CPF)
- [ ] O **quadro Kanban por projeto** atende, ou eles também querem uma **visão geral** de todos os projetos (dashboard)? Possivelmente os dois.
- [ ] Quais **motivos de perda** de lead eles querem na lista inicial?
- [ ] Quais campos exatos o **formulário do site** atual coleta? (o endpoint da API precisa espelhar isso)
- [ ] Confirmar o **canal de contato preferido** que aparece no formulário (WhatsApp, email, telefone?)

## 6. Decisões técnicas pendentes (definir no grupo)

- [ ] **Stack tecnológica** (ex.: React + Node + PostgreSQL, PHP + MySQL...). Assim que definida, adicionar ao prompt oficial na seção CONTEXTO — isso muda as respostas de código e DER.
- [ ] Repositório e organização de pastas das entregas (requisitos, UML, DER, código, monografia).
- [ ] Divisão dos cards entre os 7 integrantes por sprint.

---

*Documento vivo — atualizar conforme as decisões forem tomadas. Última atualização: 12/08/2026.*
