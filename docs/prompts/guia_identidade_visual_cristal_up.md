# Cristal UP! — Identidade Visual & Design System

**Documento de referência para projetos**
Fonte: engenharia reversa do site em produção `https://www.cristalup.tech/`
Extraído em: 12 de agosto de 2026
Stack detectada: Next.js (App Router) + Tailwind CSS + shadcn/ui + `next/font` (Inter)

---

## Sumário

1. [Visão geral da marca](#1-visão-geral-da-marca)
2. [Logo e assets](#2-logo-e-assets)
3. [Paleta de cores](#3-paleta-de-cores)
4. [Gradientes e efeitos de luz](#4-gradientes-e-efeitos-de-luz)
5. [Tipografia](#5-tipografia)
6. [Espaçamento, grid e layout](#6-espaçamento-grid-e-layout)
7. [Raios, bordas e sombras](#7-raios-bordas-e-sombras)
8. [Componentes](#8-componentes)
9. [Movimento e interação](#9-movimento-e-interação)
10. [Estrutura de seções do site](#10-estrutura-de-seções-do-site)
11. [Tom de voz e conteúdo](#11-tom-de-voz-e-conteúdo)
12. [Acessibilidade e contraste](#12-acessibilidade-e-contraste)
13. [Tokens prontos para código](#13-tokens-prontos-para-código)
14. [Regras de uso](#14-regras-de-uso)
15. [Lacunas e pontos a confirmar](#15-lacunas-e-pontos-a-confirmar)

---

## 1. Visão geral da marca

| Item | Valor |
|---|---|
| **Nome** | Cristal UP! |
| **Assinatura no logo** | Cristal UP! — Soluções Digitais |
| **Título institucional (meta title)** | Cristal UP! Softwares Customizáveis |
| **Ano de fundação (selo do rodapé)** | since 2026 |
| **Domínio** | cristalup.tech |
| **Categoria** | Software house / desenvolvimento sob medida e automação de processos |
| **Produtos próprios** | UP Finance (gestão financeira), UP Bot (chatbots customizáveis) |

**Posicionamento declarado:** "Automatizamos processos e criamos sistemas inteligentes para o seu negócio."

**Mission / Vision / Values (do site):**

- **Missão** — implementar tecnologias de gestão empresarial.
- **Visão** — ser referência em softwares personalizados.
- **Valores** — Inovação, Transparência, Coragem, Eficiência.
- **Diferenciais** — personalização total, reuniões semanais de alinhamento, stack moderna (Python, Docker, AWS, Next.js, TypeScript).

**Personalidade visual em uma frase:** *tech premium noturno* — fundo azul-marinho quase preto, roxo elétrico como única cor de marca, tipografia geométrica pesada em caixa alta, superfícies de vidro (glassmorphism) e brilhos roxos difusos.

---

## 2. Logo e assets

### 2.1 Arquivos

| Asset | Caminho | Dimensões nativas | Observações |
|---|---|---|---|
| Logo principal (horizontal) | `/logo.svg` | 204 × 47 px | Monocromático — todos os paths com `fill="white"`. Símbolo (cristal/diamante em V) + wordmark "CRISTAL" + tagline "SOLUÇÕES DIGITAIS" |
| Logo do rodapé (selo vertical) | `/logofooter.svg` | 164 × 127 px | Monocromático branco. Símbolo grande + "since / 2026" nas laterais + wordmark + tagline |
| Ilustração hero | `/mainimg.svg` | 540 × 457 px | SVG com imagem raster embutida (`pattern0`), ~800 KB |
| Ilustração de contato | `/contact2.svg` | 210 × 150 px | Ilustração vetorial colorida (pessoa em computador), paleta violeta |
| Case UP Finance | `/upfinance.jpg` | 1899 × 920 px | Screenshot do produto |
| Case UP Bot | `/chatbot.jpg` | 817 × 1600 px | Screenshot vertical (mobile) |

### 2.2 Construção do símbolo

O símbolo é um **cristal/diamante estilizado em formato de V** — duas facetas triangulares que convergem para baixo, sugerindo simultaneamente:

- **cristal** → transparência, clareza, valor (reforça o valor "Transparência");
- **V / seta para baixo invertida** → o "UP" do nome, movimento ascendente;
- **facetas** → múltiplas soluções sob medida.

### 2.3 Regras de aplicação

- **Cor única:** branco (`#FFFFFF`) sobre fundos escuros. Não há versão colorida em produção.
- **Tamanho de exibição no header:** `160px` de largura em mobile, `200px` em `md+` (`w-[160px] md:w-[200px] h-auto`) — a altura é sempre automática, preservando a proporção 204:47 (≈ 4,34:1).
- **Interação:** no header o logo tem `hover:opacity-80` com transição de `200ms`.
- **Área de respiro mínima:** reservar no mínimo a altura do símbolo (≈ 47 px na escala nativa) em todos os lados.
- **Versão para fundo claro:** não existe. Se um projeto exigir, produzir versão em `#000319` (não em preto puro) para manter coerência com o azul-marinho da marca.

### 2.4 Ilustrações — paleta interna

A ilustração `/contact2.svg` define o estilo ilustrativo da marca (flat, violeta, com sombras chapadas):

```
Violetas claros   #F3F2FC  #EEE6FD  #E6E4F5  #D2BFFE
Violetas médios   #927AFF  #7660DB  #706AA6  #5C5694
Violetas escuros  #5745A2  #4A4380  #202960  #1A214D  #192A52  #203460
Pele / acentos    #FFC2B3  #FFAA94  #F09C86  #C9875A  #FF8484
Neutro            #FFFFFF
```

Ao encomendar novas ilustrações, manter essa faixa: violetas dessaturados + um único acento coral/salmão.

---

## 3. Paleta de cores

### 3.1 Cores de marca (variáveis CSS declaradas no projeto)

| Token no código | Hex | Amostra | Papel |
|---|---|---|---|
| `--roxo` | `#902FED` | 🟣 | **Cor primária da marca.** Botões, texto de destaque, glows |
| `--lightViolet` | `#F2DEFF` | ⬜ | Violeta claríssimo — fundos claros, destaques suaves |
| `--gradientStart` | `#982FED` | 🟣 | Início do gradiente da marca |
| `--gradientCor1` | `#5B39F7` | 🔵 | Parada 2 do gradiente |
| `--gradientCor2` | `#4C67E0` | 🔵 | Parada 3 do gradiente |
| `--gradientCor3` | `#48A7F7` | 🔵 | Parada 4 do gradiente |
| `--gradientEnd` | `#45DBED` | 🩵 | Fim do gradiente (ciano) |

> O gradiente **roxo → azul → ciano** é o ativo cromático mais distintivo da marca e está declarado nas variáveis, embora seja usado com parcimônia na página atual. Em novos projetos ele é o recurso natural para elementos hero, ícones e bordas animadas.

### 3.2 Neutros e superfícies

| Token | Valor | Papel |
|---|---|---|
| `--black-100` | `#000319` | **Fundo principal do site** (azul-marinho quase preto) |
| `body` background | `#09090B` | Fundo do documento (zinc-950) — visível fora do `<main>` |
| `--black-200` | `rgba(17, 25, 40, 0.75)` | Superfície de card translúcido |
| `--black-300` | `hsla(0, 0%, 100%, 0.125)` | Borda sutil sobre escuro |
| `--white` | `#FFFFFF` | Títulos de maior peso |
| `#FAFAFA` | `rgb(250,250,250)` | **Cor de texto padrão** (169 ocorrências) |
| `--white-100` | `#BEC1DD` | Texto secundário azulado |
| `--white-200` | `#C1C2D3` | Texto secundário azulado (variante) |
| `#D1D5DB` | gray-300 | Texto de apoio / parágrafos |
| `#9CA3AF` | gray-400 | Texto terciário, legendas |
| `rgba(255,255,255,0.5)` | — | Texto de baixa ênfase (24 ocorrências) |

### 3.3 Roxos aplicados na interface

Além de `#902FED`, o site usa a escala `violet`/`purple` do Tailwind. **Isto é uma inconsistência do site atual** — em novos projetos, padronizar.

| Uso | Valor | Onde aparece |
|---|---|---|
| Botão primário — repouso | `#902FED` | `bg-[#902FED]` — hero, CTA da seção "por que nós" |
| Botão primário — hover | `#7E22CE` / `#7C1FE0` | duas variantes usadas em botões diferentes |
| Botão secundário — repouso | `#9333EA` (purple-600) | `bg-purple-600` — botão "Quero saber mais" nos cards |
| Botão secundário — hover | `#A855F7` (purple-500) | `hover:bg-purple-500` |
| Acento de link / foco | `#8B5CF6` (violet-500) | `hover:text-[#8B5CF6]`, `focus:border-[#8B5CF6]` |
| Texto de destaque | `#C084FC` (purple-400) | `text-purple-400` |
| Texto de destaque (marca) | `#902FED` | `text-[#902FED]` — palavras em destaque nos títulos |
| Roxo profundo (gradiente) | `#6A0DAD` | usado a 5% de opacidade em overlays |

**Recomendação de padronização:**

```
purple-brand        #902FED   ← primário, único roxo de preenchimento
purple-brand-hover  #7E22CE   ← hover do primário (padronizar; descartar #7C1FE0)
purple-accent       #A855F7   ← texto de destaque sobre escuro (contraste AA)
purple-focus        #8B5CF6   ← anel de foco e bordas de input em foco
```

### 3.4 Cores funcionais

| Papel | Valor | Nota |
|---|---|---|
| WhatsApp (marca externa) | `#25D366` | Botão "WhatsApp Chat" e ícone no header |
| Erro / destrutivo | `hsl(0 62.8% 30.6%)` ≈ `#7F1D1D` | Token shadcn (dark) |
| Sucesso (fundo claro) | `#E9FCEB` | Fundo de mensagem de sucesso no formulário |
| Info (fundo claro) | `#EFF6FF` | Fundo de mensagem informativa |
| Azul institucional | `#3B82F6` | Ícone de envelope no header ("Entrar em contato") |
| Borda de input | `#4B5563` (gray-600) | Formulário de contato |

### 3.5 Tokens shadcn/ui (tema dark ativo)

O projeto roda com a classe `dark` no `<body>` e usa o tema **zinc** padrão do shadcn/ui:

```css
--background: 240 10% 3.9%;      --foreground: 0 0% 98%;
--card: 240 10% 3.9%;            --card-foreground: 0 0% 98%;
--popover: 240 10% 3.9%;         --popover-foreground: 0 0% 98%;
--primary: 0 0% 98%;             --primary-foreground: 240 5.9% 10%;
--secondary: 240 3.7% 15.9%;     --secondary-foreground: 0 0% 98%;
--muted: 240 3.7% 15.9%;         --muted-foreground: 240 5% 64.9%;
--accent: 240 3.7% 15.9%;        --accent-foreground: 0 0% 98%;
--destructive: 0 62.8% 30.6%;    --destructive-foreground: 0 0% 98%;
--border: 240 3.7% 15.9%;        --input: 240 3.7% 15.9%;
--ring: 240 4.9% 83.9%;          --radius: 0.5rem;
```

> ⚠️ **Ponto de atenção:** `--primary` do shadcn é branco, não o roxo da marca. Componentes shadcn instalados "de fábrica" não herdam a cor da marca. Em novos projetos, sobrescrever `--primary` para o roxo (`267 84% 55%` ≈ `#902FED`) e `--ring` para o violeta de foco.

---

## 4. Gradientes e efeitos de luz

### 4.1 Gradiente da marca (definido em variáveis)

```css
background: linear-gradient(
  90deg,
  #982FED 0%,    /* gradientStart */
  #5B39F7 25%,   /* gradientCor1 */
  #4C67E0 50%,   /* gradientCor2 */
  #48A7F7 75%,   /* gradientCor3 */
  #45DBED 100%   /* gradientEnd */
);
```

Aplicações naturais: texto com `bg-clip-text`, bordas animadas, ícones, barras de progresso, divisores.

### 4.2 Overlays em uso no site

```css
/* Vinheta de topo→base sobre seções */
linear-gradient(rgba(0,0,0,0), rgba(10,10,15,0.2), rgba(10,10,15,0.4));

/* Fade para o fundo escuro no fim das seções */
linear-gradient(rgba(26,15,46,0.3), rgba(13,13,22,0.6), rgb(7,7,12));

/* Tint roxo diagonal em cards */
linear-gradient(to bottom right, rgba(144,47,237,0.10), transparent, rgba(106,13,173,0.05));

/* Tint violeta em superfícies */
linear-gradient(to top right, rgba(139,92,246,0.20), transparent);
linear-gradient(to bottom right, rgba(139,92,246,0.10), transparent);

/* Sangria de cor a partir do topo */
linear-gradient(rgba(144,47,237,0.10), transparent);
```

**Padrão:** overlays de cor nunca passam de **20% de opacidade**. A cor entra como atmosfera, não como preenchimento.

### 4.3 Glows

```css
/* Glow do botão primário */
box-shadow: 0 0 20px rgba(144, 47, 237, 0.25);

/* Glow sutil de card */
box-shadow: 0 0 20px rgba(144, 47, 237, 0.05);

/* Glow de imagem/ilustração */
filter: drop-shadow(0 0 40px rgba(139, 92, 246, 0.35));

/* Hover de card */
box-shadow: 0 25px 50px -12px rgba(168, 85, 247, 0.20);  /* purple-500/20 */
```

### 4.4 Orbes de fundo

Elementos decorativos usam `blur-2xl` (40px) e `blur-3xl` (64px) sobre círculos roxos de baixa opacidade — a técnica que cria o "brilho" difuso ao redor de títulos e cards.

### 4.5 Grade de fundo

O site aplica uma **grade de linhas finas** sobre o fundo escuro (visível nas capturas), reforçando o aspecto técnico/blueprint. Manter em novos projetos como textura de fundo padrão.

---

## 5. Tipografia

### 5.1 Família

| Item | Valor |
|---|---|
| **Fonte única** | **Inter** (variável, eixo de peso `100 900`) |
| Carregamento | `next/font/google` — self-hosted, sem `<link>` externo |
| Fallback | stack `ui-sans-serif, system-ui, sans-serif` |
| Alternativa web-safe | `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif` |

Não há fonte serifada, display ou mono na marca. **Inter faz todo o trabalho** — a diferenciação vem de peso, caixa e tracking.

### 5.2 Pesos em uso

| Classe | Peso | Uso |
|---|---|---|
| `font-light` | 300 | Raro — textos de apoio grandes |
| — (normal) | 400 | Parágrafos, labels |
| `font-medium` | 500 | Botões, links de navegação |
| `font-semibold` | 600 | Subtítulos de card |
| `font-bold` | 700 | Todos os títulos de seção |

### 5.3 Escala aplicada

| Elemento | Tamanho | Line-height | Peso | Tracking | Cor |
|---|---|---|---|---|---|
| **Título hero** | `48px` (`text-5xl`) | `66px` (`leading-snug`) | 700 | `1.2px` (`tracking-wide`) | `#FFFFFF` |
| **Título de seção** (`.heading`) | `36px` base → `48px` em `lg` | `40px` → `48px` (`leading-tight`) | 700 | normal ou `1.2px` | `#FAFAFA` |
| Título de card (h2) | `36px` (`text-4xl`) | `40px` | 400–600 | normal | `#FAFAFA` |
| Subtítulo (h3) | `30px` (`text-3xl`) | `36px` | 600 | normal | `#FAFAFA` |
| Título menor (h4) | `24px` (`text-2xl`) | `32px` | 600 | normal | `#FAFAFA` |
| Lead / destaque | `20px` (`text-xl`) | `28px` | 400 | normal | `#D1D5DB` |
| Corpo | `16px` (`text-base`) | `24px` (`leading-relaxed`) | 400 | normal | `#D1D5DB` |
| Corpo pequeno / botão de card | `14px` (`text-sm`) | `20px` | 400–500 | normal | `#9CA3AF` |
| Eyebrow / label | `14px` | `20px` | 500–700 | `tracking-wider` + `uppercase` | `#C084FC` ou `#FAFAFA` |

**Utilitário `.heading` (definido no CSS do projeto):**

```css
.heading {
  text-align: center;
  font-size: 2.25rem;   /* 36px */
  line-height: 2.5rem;  /* 40px */
  font-weight: 700;
}
```

### 5.4 Regra de composição dos títulos

O padrão editorial da marca é: **título em caixa alta, branco, com uma parte da frase em roxo.**

```
CONSTRUINDO TECNOLOGIA QUE
TRANSFORMA NEGÓCIOS        ← em #902FED / purple-400
```

```
Automatizamos processos e criamos sistemas inteligentes
para o seu negócio.        ← em #902FED
```

- Títulos de seção: **CAIXA ALTA**, `tracking-wide`/`tracking-wider`.
- Título hero: caixa mista (sentence case), `tracking-wide`.
- O trecho em roxo é sempre o **benefício** ou o **objeto** da frase, nunca o verbo.

### 5.5 Tracking e leading disponíveis

```
tracking-tighter (-0.05em)  tracking-tight (-0.025em)
tracking-wide (0.025em)     tracking-wider (0.05em)
leading-tight (1.25)        leading-snug (1.375)      leading-relaxed (1.625)
```

---

## 6. Espaçamento, grid e layout

### 6.1 Contêineres

| Token | Largura | Uso |
|---|---|---|
| `max-w-7xl` | 1280px | Contêiner principal de seções |
| `max-w-6xl` | 1152px | Blocos de conteúdo largos |
| `max-w-4xl` | 896px | Blocos de texto centralizados |
| `max-w-2xl` | 672px | Parágrafos de apoio |
| `max-w-[650px]` | 650px | Formulário / coluna de texto |
| `max-w-lg` | 512px | Cards estreitos |
| `max-w-md` | 448px | Cards / caixas de formulário |
| `max-w-[89vw]` | 89vw | Limite responsivo do hero |

### 6.2 Padding horizontal do wrapper

```html
<main class="mx-auto px-5 sm:px-10 overflow-clip bg-black-100">
```

→ **20px** em mobile, **40px** a partir de `sm` (640px).

### 6.3 Ritmo vertical das seções

| Seção | Padding vertical |
|---|---|
| `#choice`, `#projects`, `#services`, `#contact` | `py-20` = **80px** |
| `#us` | `py-24` = **96px** |
| Gap interno entre blocos | `gap-16` = **64px** |

**Escala de espaçamento** (Tailwind, base 4px): `4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48 · 64 · 80 · 96`.

### 6.4 Grid

O site usa um padrão único e simples:

```html
<div class="grid grid-cols-1 md:grid-cols-2 gap-8">
```

Uma coluna em mobile, duas a partir de `768px`. Não há grids de 3 ou 4 colunas.

### 6.5 Breakpoints (Tailwind default)

| Nome | Min-width |
|---|---|
| `sm` | 640px |
| `md` | 768px — **quebra principal do site** (nav mobile, grid) |
| `lg` | 1024px — escala de títulos |
| `xl` | 1280px |
| `2xl` | 1536px |

---

## 7. Raios, bordas e sombras

### 7.1 Border radius

| Token | Valor | Uso |
|---|---|---|
| `--radius` (shadcn) | `0.5rem` = 8px | Base dos componentes shadcn |
| `rounded-lg` | 8px | Inputs, textarea, botão fantasma |
| `rounded-xl` | **12px** | **Padrão dos botões e imagens** |
| `rounded-2xl` | 16px | Cards |
| `rounded-3xl` | 24px | Painéis e superfícies grandes |
| `rounded-full` | 9999px | Ícones circulares (WhatsApp, envelope), badges |

**Regra:** botões e imagens → `rounded-xl` (12px). Cards → `rounded-2xl`/`rounded-3xl`. Nada com cantos retos.

### 7.2 Bordas

| Token | Valor | Uso |
|---|---|---|
| `border-white/10` | `rgba(255,255,255,0.10)` | **Borda padrão de card de vidro** |
| `border-white/20` | `rgba(255,255,255,0.20)` | Borda em hover / ênfase |
| `border-gray-600` | `#4B5563` | Inputs e botão fantasma |
| `--black-300` | `hsla(0,0%,100%,0.125)` | Alias para borda sutil |

Espessura sempre `1px`.

### 7.3 Superfícies de vidro (glassmorphism)

```css
/* Card de vidro padrão */
background: rgba(0, 0, 0, 0.30);          /* bg-black/30 */
border: 1px solid rgba(255,255,255,0.10); /* border-white/10 */
backdrop-filter: blur(12px);              /* backdrop-blur-md */
border-radius: 16px;                      /* rounded-2xl */
```

Variantes de fundo em uso: `bg-black/30`, `bg-black/20`, `bg-white/5`, `bg-white/10`.
Variantes de blur: `backdrop-blur-[2px]` (sutil), `backdrop-blur-md` (12px).

### 7.4 Sombras

| Nome | Valor | Uso |
|---|---|---|
| Glow primário | `0 0 20px rgba(144,47,237,0.25)` | Botão primário |
| Glow sutil | `0 0 20px rgba(144,47,237,0.05)` | Card em repouso |
| `shadow-lg` | `0 10px 15px -3px rgb(0 0 0 / .1), 0 4px 6px -4px rgb(0 0 0 / .1)` | Botões |
| `shadow-xl` | `0 20px 25px -5px rgb(0 0 0 / .1)` | Cards elevados |
| `shadow-2xl` | `0 25px 50px -12px rgb(0 0 0 / .25)` | Painéis |
| Glow de hover | `hover:shadow-purple-500/20`, `hover:shadow-[#8B5CF6]/30` | Cards e CTAs |
| Drop-shadow de imagem | `drop-shadow(0 0 40px rgba(139,92,246,0.35))` | Ilustrações |

---

## 8. Componentes

### 8.1 Botão primário

```html
<a class="w-full sm:w-auto px-6 py-3 rounded-xl
          bg-[#902FED] text-white font-medium
          flex items-center justify-center gap-2
          shadow-[0_0_20px_rgba(144,47,237,0.25)]
          hover:bg-[#7E22CE] transition-all">
  Falar com um especialista <IconeWhatsApp />
</a>
```

| Propriedade | Valor |
|---|---|
| Fundo | `#902FED` |
| Fundo hover | `#7E22CE` (variante grande usa `#7C1FE0` — padronizar) |
| Texto | `#FFFFFF`, `16px`, peso 500 |
| Padding | `12px 24px` (variante grande: `12px 32px`, texto `18px`) |
| Raio | `12px` |
| Sombra | `0 0 20px rgba(144,47,237,0.25)` |
| Ícone | à direita, `gap: 8px` |
| Largura | `100%` em mobile, `auto` em `sm+` |
| Transição | `all`, `300ms` |

### 8.2 Botão secundário (revelado em hover no card)

```html
<a class="opacity-0 group-hover:opacity-100 transition-all duration-300
          bg-purple-600 hover:bg-purple-500
          px-5 py-2 rounded-xl text-sm font-medium text-white">
  Quero saber mais
</a>
```

Fundo `#9333EA` → hover `#A855F7`; padding `8px 20px`; texto `14px` peso 500.

### 8.3 Botão fantasma

```html
<button class="px-4 py-2 rounded-lg border border-gray-600 text-gray-300">
  Limpar
</button>
```

Sem preenchimento; borda `1px #4B5563`; texto `#D1D5DB`; raio `8px`.

### 8.4 Botão WhatsApp

Fundo `#25D366`, texto branco, `rounded-lg`, ícone à esquerda com `gap-2`.
⚠️ Branco sobre `#25D366` tem contraste **1,98:1** — ver [seção 12](#12-acessibilidade-e-contraste).

### 8.5 Input / Textarea

```html
<input class="pl-10 w-full p-3 rounded-lg
              bg-black/30 border border-gray-600
              text-white placeholder-gray-400
              focus:border-[#8B5CF6] focus:outline-none" />
```

| Propriedade | Valor |
|---|---|
| Fundo | `rgba(0,0,0,0.30)` |
| Borda | `1px solid #4B5563` |
| Borda em foco | `#8B5CF6` |
| Raio | `8px` |
| Padding | `12px`; `padding-left: 40px` quando há ícone |
| Texto | `#FFFFFF` |
| Placeholder | `#9CA3AF` — ex.: "Seu nome completo" |

### 8.6 Card de conteúdo (vidro)

```html
<div class="group relative rounded-2xl p-8
            bg-black/30 backdrop-blur-md border border-white/10
            bg-gradient-to-br from-[#902FED]/10 via-transparent to-[#6A0DAD]/5
            shadow-[0_0_20px_rgba(144,47,237,0.05)]
            hover:border-white/20 hover:shadow-purple-500/20
            transition-all duration-300">
```

### 8.7 Card de estágio (processo em 3 etapas)

Padrão de interação notável: o conteúdo padrão desaparece em hover e o CTA aparece.

```html
<div class="group ...">
  <div class="flex justify-center mb-6
              group-hover:opacity-0 group-hover:-translate-y-4
              transition duration-300">
    1º Estágio
  </div>
  <!-- ... título + bullets ... -->
  <a class="opacity-0 group-hover:opacity-100 transition-all duration-300
            bg-purple-600 hover:bg-purple-500 px-5 py-2 rounded-xl text-sm font-medium">
    Quero saber mais
  </a>
</div>
```

Bullets usam o marcador `•` como caractere, não `list-style`.

### 8.8 Header / Navegação

- Posição fixa no topo, fundo translúcido com blur.
- Logo à esquerda (`160px` / `200px`).
- Links à direita: "Serviços", "Quem somos" — texto `#FAFAFA`, hover `#8B5CF6`, peso 500.
- Dois ícones circulares (`rounded-full`) com rótulo ao lado:
  - **WhatsApp** — círculo `#25D366`
  - **Entrar em contato** — círculo `#3B82F6`, ícone de envelope
- Em mobile (`< md`): links colapsam em botão hambúrguer `text-2xl text-white` (`md:hidden`).

### 8.9 Footer

- Selo vertical do logo (`/logofooter.svg`) à esquerda.
- Colunas: **LINKS RÁPIDOS** (Serviços, Quem somos, Cases) e **CANAIS** (Instagram, LinkedIn).
- Títulos de coluna em **CAIXA ALTA roxa** (`#C084FC` / `#902FED`), `tracking-wider`.
- Itens de lista com marcador `•`.
- Acima do footer, bloco de fechamento com título grande em caixa alta e destaque roxo.
- Fundo com glow roxo difuso no canto inferior esquerdo.

---

## 9. Movimento e interação

| Duração | Uso |
|---|---|
| `200ms` | Micro-hovers (opacidade do logo) |
| **`300ms`** | **Padrão** — botões, cards, revelações |
| `500ms` | Transformações maiores |

**Animação nomeada:** `animate-float` — flutuação vertical contínua em elementos decorativos/ilustrações.

**Padrões de hover:**

- Botão primário: troca de fundo (`#902FED` → `#7E22CE`).
- Card: `border-white/10` → `border-white/20` + ganho de glow roxo.
- Card de estágio: conteúdo padrão sai (`opacity-0` + `-translate-y-4`), CTA entra (`opacity-0` → `opacity-100`).
- Link de nav: cor → `#8B5CF6`.
- Logo: `opacity` → `0.8`.

**Propriedade animada:** quase sempre `transition-all` (aceitável no volume atual; em projetos maiores, preferir `transition-colors`/`transition-opacity` por performance).

---

## 10. Estrutura de seções do site

| Ordem | `id` | Título | Padding | Papel |
|---|---|---|---|---|
| 1 | *(hero)* | "Automatizamos processos e criamos sistemas inteligentes **para o seu negócio.**" | — | Proposta de valor + CTA WhatsApp |
| 2 | — | "Transforme seus processos manuais em **soluções inteligentes.**" | — | Lista de capacidades + ilustração |
| 3 | `choice` | "POR QUE SOMOS A ESCOLHA CERTA PARA O SEU NEGÓCIO?" | `py-20` | 3 diferenciais + CTA |
| 4 | `projects` | "NOSSOS CASES" | `py-20` | UP Finance e UP Bot |
| 5 | `us` | "QUEM SOMOS NÓS?" | `py-24` | História, Missão, Visão, Valores, Diferenciais |
| 6 | `services` | "Serviços que Impulsionam Seu Negócio" | `py-20` | Processo em 3 estágios |
| 7 | `contact` | "Pronto para dar o próximo passo?" | `py-20` | Formulário + WhatsApp + ilustração |
| 8 | *(footer)* | "CONSTRUINDO TECNOLOGIA QUE **TRANSFORMA NEGÓCIOS**" | — | Fechamento + links + canais |

**Navegação âncora:** `#services`, `#us`, `#projects` (rótulo "Cases"), `#contact`.

**Formulário de contato:** campos com ícone à esquerda, placeholders descritivos ("Seu nome completo"), ações "Limpar" (fantasma) e "Enviar mensagem" (primário com ícone de avião de papel), mais fallback "Ou fale diretamente pelo WhatsApp:" com botão verde.

---

## 11. Tom de voz e conteúdo

### 11.1 Princípios

1. **Segunda pessoa, sempre.** "*seu* negócio", "*você* terá mais tempo". O leitor é o protagonista.
2. **Nós fazemos, você ganha.** Verbo na primeira pessoa do plural ("Automatizamos", "Criamos", "Eliminamos", "Desenvolvemos") + benefício para o cliente.
3. **Antítese manual → inteligente.** A construção retórica central da marca: "Transforme seus processos *manuais* em soluções *inteligentes*."
4. **Negação de concorrente genérico.** "Nada de modelos prontos." "Não desaparecemos depois que entregamos."
5. **Frases curtas, sem jargão vazio.** Termos técnicos aparecem apenas na lista de stack.
6. **Reforço de reciprocidade e processo.** Prazos, reuniões semanais, suporte contínuo — combate ao medo de abandono pós-entrega.

### 11.2 Vocabulário da marca

| Usar | Evitar |
|---|---|
| sob medida, personalizado, exclusivo, customizável | template, modelo, padrão |
| automatizar, eliminar tarefas manuais | otimizar (vago) |
| produtividade, eficiência, resultados reais | sinergia, disruptivo, inovador (isolado) |
| suporte contínuo, acompanhamento dedicado | pós-venda |
| solução inteligente | solução completa |

### 11.3 Padrões de CTA

Sempre em **primeira pessoa do desejo do cliente** ou convite direto:

```
Falar com um especialista
Quero transformar meu negócio
Quero saber mais
Entre em contato
Enviar mensagem
WhatsApp Chat
```

Nunca "Saiba mais", "Clique aqui" ou "Enviar".

### 11.4 Fórmula de título de seção

```
[EYEBROW EM CAIXA ALTA MENOR]
Título em caixa alta com destaque em ROXO
Subtítulo em uma frase, cinza claro, centralizado, max-w-2xl
```

---

## 12. Acessibilidade e contraste

Contrastes calculados (WCAG 2.1) contra o fundo principal `#000319`:

| Combinação | Razão | Nível |
|---|---|---|
| `#FFFFFF` sobre `#000319` | **20,45:1** | AAA |
| `#FAFAFA` sobre `#000319` | **19,59:1** | AAA |
| `#FAFAFA` sobre `#09090B` | **19,06:1** | AAA |
| `#F2DEFF` sobre `#000319` | **16,23:1** | AAA |
| `#D1D5DB` sobre `#000319` | **13,88:1** | AAA |
| `#BEC1DD` sobre `#000319` | **11,55:1** | AAA |
| `#9CA3AF` sobre `#000319` | **8,05:1** | AAA |
| `#C084FC` sobre `#000319` | **7,74:1** | AAA |
| `#A855F7` sobre `#000319` | **5,17:1** | AA |
| `#8B5CF6` sobre `#000319` | **4,83:1** | AA |
| `#902FED` sobre `#000319` | **3,71:1** | ⚠️ Apenas texto grande (AA Large) |
| `#FFFFFF` sobre `#902FED` | **5,50:1** | AA |
| `#FFFFFF` sobre `#7E22CE` | **6,98:1** | AA |
| `#FFFFFF` sobre `#9333EA` | **5,38:1** | AA |
| `#FFFFFF` sobre `#25D366` | **1,98:1** | ❌ Falha |

### Recomendações

1. **`#902FED` como cor de texto** só passa em texto grande (≥ 24px ou ≥ 19px bold). Nos títulos de seção (48px bold) está correto; **não usar em texto de corpo ou links pequenos.** Para texto pequeno em roxo, usar `#A855F7` (5,17:1) ou `#C084FC` (7,74:1).
2. **Botão WhatsApp verde:** texto branco sobre `#25D366` falha (1,98:1). Usar texto escuro (`#0B141A`, ≈ 9,9:1) ou escurecer o fundo para `#128C7E` (verde escuro oficial do WhatsApp, ≈ 4,0:1 com branco). Manter o verde `#25D366` apenas no ícone.
3. **Anel de foco:** o site usa `focus:border-[#8B5CF6]` com `focus:outline-none`, o que remove o indicador nativo. Adicionar `focus-visible:ring-2 focus-visible:ring-[#8B5CF6] focus-visible:ring-offset-2 focus-visible:ring-offset-[#000319]` para navegação por teclado.
4. **Texto a `rgba(255,255,255,0.5)`** (usado 24×) resulta em ≈ 8,4:1 sobre o fundo — aceitável, mas evitar sobre superfícies de vidro claras.
5. **Interações apenas em hover:** os CTAs "Quero saber mais" dos cards de estágio ficam com `opacity-0` até o hover — invisíveis em touch e para leitores de tela dependendo da implementação. Garantir visibilidade em `:focus-within` e em telas touch.
6. **Hierarquia de headings:** há `h1` repetido em várias seções (títulos de seção usam `h1`). Corrigir para um único `h1` (hero) e `h2` nas seções.
7. **`prefers-reduced-motion`:** `animate-float` e as transições devem ser desativadas nessa media query.

---

## 13. Tokens prontos para código

### 13.1 CSS custom properties

```css
:root {
  /* ---- Marca ---- */
  --cu-purple:            #902FED;
  --cu-purple-hover:      #7E22CE;
  --cu-purple-accent:     #A855F7;
  --cu-purple-light:      #C084FC;
  --cu-purple-focus:      #8B5CF6;
  --cu-purple-deep:       #6A0DAD;
  --cu-violet-lightest:   #F2DEFF;

  /* ---- Gradiente da marca ---- */
  --cu-grad-start:        #982FED;
  --cu-grad-1:            #5B39F7;
  --cu-grad-2:            #4C67E0;
  --cu-grad-3:            #48A7F7;
  --cu-grad-end:          #45DBED;
  --cu-gradient: linear-gradient(90deg,
    var(--cu-grad-start) 0%, var(--cu-grad-1) 25%,
    var(--cu-grad-2) 50%, var(--cu-grad-3) 75%,
    var(--cu-grad-end) 100%);

  /* ---- Superfícies ---- */
  --cu-bg:                #000319;
  --cu-bg-alt:            #09090B;
  --cu-surface:           rgba(0, 0, 0, 0.30);
  --cu-surface-raised:    rgba(255, 255, 255, 0.05);
  --cu-surface-glass:     rgba(17, 25, 40, 0.75);

  /* ---- Bordas ---- */
  --cu-border:            rgba(255, 255, 255, 0.10);
  --cu-border-strong:     rgba(255, 255, 255, 0.20);
  --cu-border-input:      #4B5563;

  /* ---- Texto ---- */
  --cu-text:              #FAFAFA;
  --cu-text-strong:       #FFFFFF;
  --cu-text-muted:        #D1D5DB;
  --cu-text-subtle:       #9CA3AF;
  --cu-text-blue-tint:    #BEC1DD;

  /* ---- Funcional ---- */
  --cu-whatsapp:          #25D366;
  --cu-whatsapp-dark:     #128C7E;
  --cu-info:              #3B82F6;

  /* ---- Raios ---- */
  --cu-radius-sm:         8px;
  --cu-radius:            12px;
  --cu-radius-lg:         16px;
  --cu-radius-xl:         24px;
  --cu-radius-full:       9999px;

  /* ---- Sombras ---- */
  --cu-glow:              0 0 20px rgba(144, 47, 237, 0.25);
  --cu-glow-subtle:       0 0 20px rgba(144, 47, 237, 0.05);
  --cu-glow-image:        0 0 40px rgba(139, 92, 246, 0.35);

  /* ---- Tipografia ---- */
  --cu-font: Inter, ui-sans-serif, system-ui, sans-serif;

  /* ---- Movimento ---- */
  --cu-transition:        300ms;
  --cu-transition-fast:   200ms;
  --cu-transition-slow:   500ms;
}
```

### 13.2 Tailwind config

```js
// tailwind.config.ts
export default {
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        purple: {
          brand:  '#902FED',
          hover:  '#7E22CE',
          accent: '#A855F7',
          light:  '#C084FC',
          focus:  '#8B5CF6',
          deep:   '#6A0DAD',
        },
        cristal: {
          bg:      '#000319',
          bgAlt:   '#09090B',
          text:    '#FAFAFA',
          muted:   '#D1D5DB',
          subtle:  '#9CA3AF',
          tint:    '#BEC1DD',
          violet:  '#F2DEFF',
        },
        whatsapp: { DEFAULT: '#25D366', dark: '#128C7E' },
      },
      backgroundImage: {
        'cristal-gradient':
          'linear-gradient(90deg,#982FED 0%,#5B39F7 25%,#4C67E0 50%,#48A7F7 75%,#45DBED 100%)',
      },
      boxShadow: {
        glow:       '0 0 20px rgba(144,47,237,0.25)',
        'glow-sm':  '0 0 20px rgba(144,47,237,0.05)',
      },
      dropShadow: {
        glow: '0 0 40px rgba(139,92,246,0.35)',
      },
      borderRadius: { DEFAULT: '12px' },
      fontFamily: { sans: ['Inter', 'ui-sans-serif', 'system-ui', 'sans-serif'] },
      keyframes: {
        float: {
          '0%,100%': { transform: 'translateY(0)' },
          '50%':     { transform: 'translateY(-12px)' },
        },
      },
      animation: { float: 'float 6s ease-in-out infinite' },
    },
  },
}
```

### 13.3 Sobrescrita dos tokens shadcn/ui para a marca

```css
.dark {
  --background: 232 100% 5%;    /* #000319 */
  --foreground: 0 0% 98%;
  --card: 232 100% 5%;
  --primary: 269 84% 55%;       /* #902FED — substitui o branco padrão */
  --primary-foreground: 0 0% 100%;
  --ring: 258 90% 66%;          /* #8B5CF6 */
  --border: 0 0% 100% / 0.10;
  --radius: 0.75rem;            /* 12px, alinhado ao rounded-xl da marca */
}
```

### 13.4 Design tokens (JSON)

```json
{
  "color": {
    "brand": { "purple": "#902FED", "purpleHover": "#7E22CE", "purpleAccent": "#A855F7",
               "purpleLight": "#C084FC", "purpleFocus": "#8B5CF6", "violetLightest": "#F2DEFF" },
    "gradient": ["#982FED", "#5B39F7", "#4C67E0", "#48A7F7", "#45DBED"],
    "surface": { "bg": "#000319", "bgAlt": "#09090B",
                 "glass": "rgba(0,0,0,0.30)", "raised": "rgba(255,255,255,0.05)" },
    "text": { "default": "#FAFAFA", "strong": "#FFFFFF",
              "muted": "#D1D5DB", "subtle": "#9CA3AF", "tint": "#BEC1DD" },
    "border": { "default": "rgba(255,255,255,0.10)", "strong": "rgba(255,255,255,0.20)",
                "input": "#4B5563" },
    "functional": { "whatsapp": "#25D366", "whatsappDark": "#128C7E", "info": "#3B82F6" }
  },
  "font": { "family": "Inter", "weights": [300, 400, 500, 600, 700],
            "sizes": { "sm": 14, "base": 16, "lg": 18, "xl": 20,
                       "2xl": 24, "3xl": 30, "4xl": 36, "5xl": 48 } },
  "radius": { "sm": 8, "md": 12, "lg": 16, "xl": 24, "full": 9999 },
  "space": [4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96],
  "container": { "page": 1280, "content": 896, "text": 672, "form": 650 },
  "motion": { "fast": 200, "default": 300, "slow": 500 },
  "breakpoints": { "sm": 640, "md": 768, "lg": 1024, "xl": 1280, "2xl": 1536 }
}
```

---

## 14. Regras de uso

### ✅ Faça

- Use `#000319` como fundo base, não preto puro — o azul-marinho é parte da identidade.
- Mantenha o roxo como **única** cor de marca; deixe o resto neutro.
- Mantenha overlays de cor **abaixo de 20% de opacidade**.
- Use `rounded-xl` (12px) em botões e imagens.
- Componha títulos em caixa alta com **um trecho em roxo**.
- Aplique `0 0 20px rgba(144,47,237,0.25)` no botão primário — é a assinatura visual do CTA.
- Use Inter em todos os pesos; a diferenciação vem de peso e tracking, não de outra fonte.
- Mantenha o ritmo de `py-20` / `py-24` entre seções.
- Use a grade fina de fundo como textura padrão.
- Escreva CTAs em primeira pessoa do desejo ("Quero…", "Falar com…").

### ❌ Não faça

- Não use o logo sobre fundo claro sem produzir uma versão em `#000319`.
- Não use `#902FED` em texto abaixo de 24px (contraste 3,71:1).
- Não use texto branco sobre o verde `#25D366`.
- Não introduza uma segunda fonte ou uma segunda cor de marca.
- Não misture `#902FED`, `#9333EA` e `#8B5CF6` como cores de preenchimento no mesmo projeto — escolha uma por papel.
- Não use cantos retos (`rounded-none`) em superfícies.
- Não deixe CTAs visíveis apenas em `:hover` sem alternativa para touch e teclado.
- Não use gradiente do logo — ele é monocromático branco.
- Não escreva "Saiba mais" ou "Clique aqui".
- Não prometa entrega sem mencionar processo/suporte — é parte do posicionamento.

---

## 15. Lacunas e pontos a confirmar

Itens que não podem ser determinados só pelo site em produção e que valem confirmar com a equipe antes de usar em um projeto novo:

1. **Arquivo-fonte vetorial do logo** (AI/Figma) e versão empilhada/monograma isolado.
2. **Versão colorida ou em gradiente do logo** — existe alguma para fundos claros?
3. **Favicon e ícones PWA** — não foram encontrados `link[rel=icon]` explícitos no HTML.
4. **Metadados sociais** (`og:image`, `og:title`, `theme-color`) — não localizados; recomenda-se definir.
5. **Padronização do hover do botão primário** — o site usa `#7E22CE` e `#7C1FE0` em botões diferentes. Definir um.
6. **Uso pretendido do gradiente roxo→ciano** — está declarado em variáveis mas quase não aparece. É reserva para o futuro ou legado?
7. **Tema claro** — as variáveis do shadcn para light mode existem, mas o site força `dark`. Há intenção de tema claro?
8. **Escala de ícones** — o site usa ícones inline (Instagram, LinkedIn, WhatsApp, envelope, avião de papel). Confirmar a biblioteca (aparenta ser `react-icons`) e o tamanho padrão.
9. **Iconografia própria** — não há set proprietário; definir se a marca adota `lucide`, `react-icons` ou set customizado.
10. **Fonte de exibição alternativa** — o hero renderiza Inter em 700 com tracking positivo; se a marca quiser mais personalidade, avaliar uma display geométrica em par com Inter.

---

**Fonte:** [cristalup.tech](https://www.cristalup.tech/) — extração de CSS custom properties, estilos computados, folhas de estilo, assets SVG e cópia de todas as seções da página.
