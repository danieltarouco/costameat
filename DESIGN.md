---
name: Costameat
description: Gestão de custos de entrada e margem real para distribuidora de alimentos
colors:
  bordeaux: "#991b1b"
  bordeaux-deep: "#7f1d1d"
  bordeaux-cellar: "#450a0a"
  bordeaux-veil: "#fef2f2"
  teal-controller: "#0f766e"
  teal-veil: "#ecfdf5"
  stone-canvas: "#fafaf9"
  stone-card: "#ffffff"
  stone-hush: "#f5f5f4"
  stone-shelf: "#f0efed"
  ink-slate: "#1c1917"
  ink-slate-soft: "#57534e"
  ink-slate-muted: "#a8a29e"
  ink-inverse: "#ffffff"
  border-line: "#e7e5e4"
  border-strong: "#d6d3d1"
  signal-danger: "#dc2626"
  signal-danger-veil: "#fee2e2"
  signal-warn: "#d97706"
  signal-warn-veil: "#fef3c7"
  signal-ok: "#16a34a"
  signal-ok-veil: "#dcfce7"
  signal-info: "#0369a1"
  signal-info-veil: "#e0f2fe"
typography:
  display:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "28px"
    fontWeight: 700
    lineHeight: 1.1
    letterSpacing: "-0.02em"
  headline:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "22px"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "-0.01em"
  title:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "16px"
    fontWeight: 600
    lineHeight: 1.3
    letterSpacing: "-0.005em"
  body:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "14px"
    fontWeight: 400
    lineHeight: 1.5
  body-sm:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "13px"
    fontWeight: 400
    lineHeight: 1.5
  label:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "11px"
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: "0.06em"
rounded:
  sm: "4px"
  md: "6px"
  lg: "8px"
  xl: "12px"
  2xl: "16px"
  pill: "999px"
spacing:
  s-1: "4px"
  s-2: "8px"
  s-3: "12px"
  s-4: "16px"
  s-5: "20px"
  s-6: "24px"
  s-7: "32px"
  s-8: "40px"
components:
  button-primary:
    backgroundColor: "{colors.bordeaux}"
    textColor: "{colors.ink-inverse}"
    rounded: "{rounded.md}"
    padding: "7px 12px"
    typography: "{typography.body-sm}"
  button-primary-hover:
    backgroundColor: "{colors.bordeaux-deep}"
  button-secondary:
    backgroundColor: "{colors.stone-card}"
    textColor: "{colors.ink-slate}"
    rounded: "{rounded.md}"
    padding: "7px 12px"
    typography: "{typography.body-sm}"
  button-secondary-hover:
    backgroundColor: "{colors.stone-hush}"
  button-ghost:
    backgroundColor: "transparent"
    textColor: "{colors.ink-slate-soft}"
    rounded: "{rounded.md}"
    padding: "7px 12px"
  button-danger:
    backgroundColor: "{colors.stone-card}"
    textColor: "{colors.signal-danger}"
    rounded: "{rounded.md}"
    padding: "7px 12px"
  card:
    backgroundColor: "{colors.stone-card}"
    rounded: "{rounded.xl}"
    padding: "0"
  chip-info:
    backgroundColor: "{colors.signal-info-veil}"
    textColor: "{colors.signal-info}"
    rounded: "{rounded.pill}"
    padding: "2px 9px"
    typography: "{typography.label}"
  chip-ok:
    backgroundColor: "{colors.signal-ok-veil}"
    textColor: "{colors.signal-ok}"
    rounded: "{rounded.pill}"
    padding: "2px 9px"
  chip-danger:
    backgroundColor: "{colors.signal-danger-veil}"
    textColor: "{colors.signal-danger}"
    rounded: "{rounded.pill}"
    padding: "2px 9px"
  input:
    backgroundColor: "{colors.stone-card}"
    textColor: "{colors.ink-slate}"
    rounded: "{rounded.md}"
    padding: "8px 10px"
    typography: "{typography.body-sm}"
  sidebar:
    backgroundColor: "{colors.stone-card}"
    textColor: "{colors.ink-slate-soft}"
    width: "248px"
  sidebar-item-active:
    backgroundColor: "{colors.bordeaux-veil}"
    textColor: "{colors.bordeaux}"
    rounded: "{rounded.md}"
  topbar:
    backgroundColor: "{colors.stone-card}"
    height: "auto"
---

# Design System: Costameat

## Overview

**Creative North Star: "The Distributor's Desk"**

Costameat é a mesa de trabalho de quem administra a distribuição — planilhas grandes e legíveis, decisões diárias tomadas em ritmo, informação densa porém calma. A interface recede pra deixar o dado brilhar: números tabulares alinhados, tabelas que respiram sem inchar, cor apenas nos pontos onde uma ação importa. Nada de mascote, nada de ilustração, nada de floreio: a ferramenta é o produto.

O sistema tem uma personalidade dupla que nunca disputa espaço na mesma superfície. **Bordeaux** (o vermelho profundo da marca) fica confinado a ações primárias, chips de risco e o mark de identidade — nunca cobre grandes áreas. **Stone** (o palete quente de pedra e cal) domina 90% da tela, criando o silêncio necessário pra ler tabelas de 200+ linhas sem cansar. **Teal** aparece só como accent secundário controladoria/financeiro (nos valores líquidos e KPI de volume).

A elevação é sutil e layered: sombras muito discretas separam camadas (topbar sobre conteúdo, card sobre fundo, modal sobre página) sem chamar atenção. Movimento existe como resposta a ação, nunca como decoração.

**Key Characteristics:**
- Sidebar fixa 248px, topbar branca sticky, main-area com padding generoso
- Tipografia system-native (SF/Segoe/Roboto), sem web-fonts, foco em performance de render em telas grandes
- Números tabulares em toda tabela financeira (`font-variant-numeric: tabular-nums`)
- Chips arredondados (999px), cards com corner 12px, botões com corner 6px — hierarquia por radius
- Sem gradientes em fundos ou botões; gradientes só existem em brand marks pontuais (login mark, avatar da sidebar)
- Estados de erro/atenção comunicados por chips coloridos ou linhas destacadas, nunca por overlay dramático

## Colors

Palette warm-neutral-first: 90% da UI é stone (bege quente derivado da paleta Tailwind stone), com Costameat Bordeaux como voz única de ação e identidade.

### Primary
- **Costameat Bordeaux** (#991b1b): a voz de ação. Botões primários, ícone de item de menu ativo na sidebar, chips de alerta crítico, brand mark. Nunca cobre mais de 10% da tela.
- **Costameat Bordeaux Deep** (#7f1d1d): estado hover/pressed do Bordeaux. Também usa nos brand marks (gradiente Bordeaux → Deep).
- **Costameat Bordeaux Cellar** (#450a0a): o ponto mais escuro do gradiente do login e ícones de marca — quase preto-vinho.
- **Costameat Bordeaux Veil** (#fef2f2): fundo de item de menu ativo, fundo de chip red, fundo de alertas de perigo. Rosa-carne pastel que carrega o burgundy sem gritar.

### Secondary
- **Controller Teal** (#0f766e): accent secundário de controladoria/finanças. Aparece em: valor líquido de saldo, chip verde de sucesso, ícone de PM Líquido. Nunca compete com Bordeaux — se aparecerem lado a lado, Bordeaux ganha.
- **Controller Teal Veil** (#ecfdf5): fundo verde suave para chips e estados de sucesso.

### Neutral (Stone)
- **Stone Canvas** (#fafaf9): background da app. Bege-branco frio, o silêncio de fundo.
- **Stone Card** (#ffffff): superfície de cards, sidebar, topbar. Branco puro sobre o canvas quente.
- **Stone Hush** (#f5f5f4): fundo de linhas alternadas de tabela, fundo de estados hover.
- **Stone Shelf** (#f0efed): fundo de campos de busca dentro de toolbars, chip-toggle track.
- **Ink Slate** (#1c1917): texto principal. Quase preto quente.
- **Ink Slate Soft** (#57534e): texto secundário, ícones, hints.
- **Ink Slate Muted** (#a8a29e): texto muted, footer de detalhes.
- **Border Line** (#e7e5e4): divisor padrão entre linhas de tabela e cards.
- **Border Strong** (#d6d3d1): borda de inputs e chips outlined.

### Signal
- **Signal Danger** (#dc2626): erros, deleções, valores em vermelho absoluto.
- **Signal Warn** (#d97706): CMV, imposto, comissão nas tabelas (todos os "custos que consomem receita" aparecem em warn — âncora visual pro raciocínio de margem).
- **Signal Ok** (#16a34a): margens positivas, mensagens de sucesso, chip verde.
- **Signal Info** (#0369a1): banners informativos, chips info default.

### Named Rules
**The Bordeaux Isolation Rule.** Bordeaux nunca aparece em grandes áreas de fundo. Sua função é ativar decisão (botão), sinalizar risco (chip red, avatar), ou marcar identidade (brand mark). Se você está pintando mais de 10% da tela de Bordeaux, você está enfraquecendo o sinal — pare.

**The Warm-Cool Duality Rule.** Bordeaux (quente) e Teal (frio) nunca dividem o palco. Bordeaux domina ação/marca; Teal aparece só como accent secundário em finanças (valor líquido, sucesso). Se ambos apareceriam juntos numa mesma tabela ou card, Bordeaux vence e Teal recua.

## Typography

**Font Family:** System stack (`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`)
**Mono Family:** System mono stack (`ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, monospace`) — reservado para debug (linhas extraídas do PDF), nunca para conteúdo.

**Character:** Type que desaparece. System fonts se moldam ao SO do usuário, mantêm renderização ótima em telas grandes, e nunca competem com o dado. Nada de web-fonts, nada de display serifs, nada de curvas decorativas.

### Hierarchy
- **Display** (700, 28px, line-height 1.1, letter-spacing -0.02em): logo do login. Aparece uma vez.
- **Headline** (700, 22px, line-height 1.2, letter-spacing -0.01em): valores de KPI (Faturamento total, Margem Real, Volume). É onde o número precisa gritar — mas ainda com peso restrained.
- **Title** (600, 16px, line-height 1.3): título da página no topbar; título de card ("Faturamento por grupo").
- **Body** (400, 14px, line-height 1.5): base do sistema. Todo texto de conteúdo, células de tabela.
- **Body Small** (400, 13px, line-height 1.5): tabelas mais densas, botões, inputs.
- **Label** (600, 11px, line-height 1.2, letter-spacing 0.06em, UPPERCASE): labels de KPI, headers de tabela, hint text acima de campos.

### Named Rules
**The Numbers Are Tabular Rule.** Todo número financeiro (valores, quantidades, percentuais) usa `font-variant-numeric: tabular-nums`. Colunas de tabela ficam alinhadas verticalmente sem precisar de `text-align: right` no valor absoluto — os dígitos ocupam a mesma largura, escaneabilidade é o resultado.

**The No-Serifs Rule.** O sistema é 100% sans-serif system. Nada de Playfair, Georgia, Merriweather ou qualquer serif decorativa. O sistema serve pra ler dado, não pra apresentar prosa editorial.

## Layout

**App Shell:** grid `248px 1fr` — sidebar fixa à esquerda, content à direita. Quando `body.sidebar-collapsed`, sidebar encolhe pra 68px (só ícones) e o content se expande. Transição suave (180ms).

**Topbar:** sticky top:0, background stone-card, border-bottom line, padding `14px 28px`. Título da página + subtítulo à esquerda, ações à direita.

**Main content:** padding `28px`, max-width `1500px`, esticado pra ocupar 100% até o teto. Não centralizado — deixa alinhado à esquerda pra tabelas grandes respirarem.

**Grid de KPIs:** `repeat(auto-fit, minmax(220px, 1fr))`, gap 12px. Painel usa `repeat(4, 1fr)` no desktop, colapsa pra 2 col em `<1100px` e 1 col em `<560px`.

**Spacing scale (grid 4px):** 4, 8, 12, 16, 20, 24, 32, 40. Padding de card é 18-22px; padding de célula de tabela é 8-12px; gap entre elementos de KPI é 12px.

**Breakpoints:**
- `<560px`: mobile — KPIs em 1 coluna, sidebar vira drawer com hambúrguer
- `<980px`: tablet — sidebar vira drawer, main-grid do Painel colapsa
- `<1100px`: KPIs do Painel 2 cols
- `<720px`: topbar reduzido, tabs padding compacto

### Named Rules
**The Left-Anchored Rule.** Conteúdo não centraliza. Tudo alinha à esquerda a partir do padding 28px do main. Tabelas de 12 colunas cabem sem precisar horizontal scroll até 1400px.

## Elevation & Depth

Sistema **layered sutil**: 5 níveis de sombra muito discretos, aplicados em camadas cumulativas. Cards e superfícies são visualmente separados por sombra + border-line, nunca por só sombra. Modais e overlays têm shadow-xl + backdrop-filter blur pra criar dominância clara.

### Shadow Vocabulary
- **shadow-xs** (`0 1px 2px rgba(15, 23, 42, 0.04)`): cards e KPIs em repouso. Quase imperceptível — apenas separação de superfície.
- **shadow-sm** (`0 1px 3px rgba(15, 23, 42, 0.06), 0 1px 2px rgba(15, 23, 42, 0.04)`): hover de KPI, quando card ganha `translateY(-1px)`.
- **shadow-md** (`0 4px 6px -1px rgba(15, 23, 42, 0.08), 0 2px 4px -2px rgba(15, 23, 42, 0.05)`): topbar quando sticky, botões primários em hover.
- **shadow-lg** (`0 10px 15px -3px rgba(15, 23, 42, 0.10), 0 4px 6px -4px rgba(15, 23, 42, 0.06)`): drawer da sidebar mobile.
- **shadow-xl** (`0 20px 25px -5px rgba(15, 23, 42, 0.12), 0 8px 10px -6px rgba(15, 23, 42, 0.08)`): modais e login card. Único momento onde a sombra vira claramente perceptível.

### Named Rules
**The Layered But Quiet Rule.** Sombras existem em cada superfície, mas são tão sutis que só se percebem se somem. A profundidade é resultado do conjunto (border + shadow-xs + background sutilmente diferente), não de um efeito individual.

## Shapes

Radius forma uma hierarquia intencional que ancora o significado:
- **4px (r-sm):** células de input inline, tags pequenas dentro de tabela.
- **6px (r-md):** botões, inputs padrão, sidebar items, chip-toggle. É o radius do "elemento de ação".
- **8px (r-lg):** cards internos menores, formulários inline.
- **12px (r-xl):** cards principais. É o radius do "container de dados".
- **16px (r-2xl):** login card. O único momento com radius grande.
- **999px (pill):** chips, avatars, scrollbar thumb. O radius da "identidade circular".

Bordas: `1px solid` sempre, cor Border Line em repouso, Border Strong em elementos formais (inputs). Cards com border + shadow-xs formam o "papel sobre canvas" característico.

## Components

### Buttons
- **Shape:** radius 6px (r-md) em todos os variants.
- **Primary:** background Bordeaux, texto Ink Inverse, padding `7px 12px`, transição 120ms. Hover vai para Bordeaux Deep. Peso de fonte 500-600.
- **Secondary:** background Stone Card, texto Ink Slate, border 1px Border Strong. Hover: background Stone Hush.
- **Ghost:** background transparent, texto Ink Slate Soft. Hover: background Stone Shelf + texto Ink Slate.
- **Danger:** background Stone Card, texto Signal Danger, border 1px `#fca5a5`. Hover: background Signal Danger Veil.
- **Small variant** (`.small`): padding `4px 9px`, font 12px. Usado em ações de linha de tabela.
- **Focus ring** (todos): halo 3px `rgba(153, 27, 27, 0.22)` — o Bordeaux Veil de foco.

### Chips
- **Shape:** pill (999px).
- **Style:** padding `2px 9px`, font 11px 600 uppercase, letter-spacing 0.02em.
- **Variants:** `chip` (info default: fundo info-veil, texto info-strong), `chip.gray`, `chip.green` (ok), `chip.orange` (warn), `chip.red` (danger), `chip.brand` (Bordeaux Veil + Bordeaux).

### Cards / Containers
- **Corner:** 12px (r-xl) para cards principais; 8px (r-lg) para cards secundários.
- **Background:** Stone Card.
- **Shadow:** shadow-xs em repouso; nunca shadow-sm+ em cards estáticos.
- **Border:** 1px Border Line.
- **Card Header pattern:** `padding: 18px 22px 14px`, border-bottom Border Line, com title (16px 700) + subtitle (12px muted) empilhados.
- **Internal padding:** 18-22px em cards principais.

### KPIs
- **Container:** grid `repeat(auto-fit, minmax(220px, 1fr))`, gap 12px.
- **Card:** background Stone Card, border 1px Border Line, radius 8px, padding 16px, shadow-xs em repouso.
- **Hover:** translateY(-1px), shadow-sm, border-color Border Strong. Uma barra Bordeaux 3px aparece à esquerda (::before, opacity 0→1) — é o único momento onde Bordeaux aparece sem ser ação.
- **Label:** typography label (11px 600 uppercase). Cor Ink Slate Soft.
- **Value:** 22px 700, letter-spacing -0.01em, tabular-nums. Cor semântica (Bordeaux, Ok, Warn, Danger).
- **Hint:** 11px muted, abaixo do value.

### Inputs
- **Style:** background Stone Card, border 1px Border Strong, radius 6px, padding `8px 10px`, font 13px.
- **Focus:** border Bordeaux + box-shadow 0 0 0 3px `rgba(153, 27, 27, 0.22)`.
- **Inline inputs (`.inline`):** border transparent em repouso, aparecem só em hover — para edição in-place em tabelas.
- **Number inputs:** text-align right, tabular-nums.

### Sidebar
- **Width:** 248px expandida, 68px colapsada.
- **Background:** Stone Card.
- **Brand row:** padding `18px 16px 16px 20px`, border-bottom Border Line. Contém: brand mark (36×36 gradiente Bordeaux→Cellar radius 6px), brand text (nome bold + tag uppercase 10px muted), botão collapse (26×26 border).
- **Section labels:** typography label, cor Ink Slate Muted, padding `16px 12px 8px`.
- **Nav item:** padding `9px 12px`, gap 10px (ícone SVG 18px + label 13.5px), border-radius 6px. Hover: background Stone Hush. Ativo: background Bordeaux Veil + texto Bordeaux + ícone Bordeaux, font-weight 600.
- **Footer:** avatar circular Bordeaux gradient com inicial + nome/email empilhados + botão logout 30×30 border.

### Topbar
- **Sticky:** top 0, z-index 20.
- **Height:** auto (`padding: 14px 28px`).
- **Background:** Stone Card, border-bottom Border Line.
- **Título:** 20px 700, letter-spacing -0.02em (Title escala acima). Subtítulo 12.5px muted.
- **Ações:** flex right, gap 8px. Botões small com ícones SVG 14px.

### Tables
- **Head:** background Stone Hush, sticky top 0, padding `10px 12px`, font 11px 600 uppercase letter-spacing 0.05em, cor Ink Slate Soft, border-bottom Border Line.
- **Body cells:** padding `9px 12px`, border-bottom Border Line.
- **Rows:** hover Stone Hush; nth-child(even) `#fafbfc`.
- **Números:** `.num` aplica `text-align: right; font-variant-numeric: tabular-nums`.
- **Footer total:** background Ink Slate (escuro), texto branco, padding 11px 12px, font-weight 600.

### Modals
- **Backdrop:** fixed inset:0, `rgba(15,23,42,0.55)` + `backdrop-filter: blur(2px)`.
- **Panel:** background Stone Card, radius 12px (xl), max-width 560px, shadow-xl, animation slide-in 280ms cubic-bezier.
- **Header/footer:** padding `14px 20px`, borders Line.

### Chip-Toggle (segmented control)
- **Track:** background Stone Shelf, padding 3px, radius 6px, gap 2px.
- **Button:** padding `5px 12px`, font 12px 500, radius 4px.
- **Active:** background Stone Card, texto Ink Slate, shadow-xs, font-weight 600.

### Login Screen (signature component)
- **Overlay:** fixed inset:0, background gradient burgundy radial (`Bordeaux Cellar 0% → Deep 40% → Bordeaux 100%`).
- **Card:** Stone Card, radius 16px (2xl), padding `36px 32px 28px`, max-width 420px, shadow-xl.
- **Brand mark:** 56×56 rounded, background Stone Card, contém SVG mark (gradient Bordeaux→Cellar, sparkline em branco), shadow com tint burgundy.
- **Logo text:** Display font (28px 800 -0.025em), cor Ink Slate.
- **Divider:** "Acesse sua conta" com linhas laterais Border Line.

## Do's and Don'ts

### Do:
- **Do** usar Costameat Bordeaux apenas em ações primárias, chips de alerta crítico, item ativo da sidebar e brand marks. Nunca cobrir grandes áreas.
- **Do** aplicar `tabular-nums` em toda célula com número — a legibilidade em tabelas de 200+ linhas depende disso.
- **Do** usar Signal Warn (âmbar) pra todo custo que consome receita (CMV, imposto, comissão) — cria uma âncora visual pro raciocínio de margem.
- **Do** manter labels em uppercase (11px 600 letter-spacing 0.06em) — labels não são conteúdo, são metadados.
- **Do** limitar radius: 6px em ações (botões, sidebar item), 12px em containers de dado (cards), pill em identidades (chips).
- **Do** empilhar KPIs em cards com accent bar Bordeaux 3px aparecendo só no hover — é o momento sancionado do Bordeaux fora de ação.

### Don't:
- **Don't** usar Bordeaux como fundo de área grande (header cheio, banner, section-heading). O sinal vira ruído.
- **Don't** trazer web-fonts, display serifs (Playfair, Georgia, Merriweather), display sans (Space Grotesk, Inter alta hierarquia) ou qualquer fonte customizada. System stack é o padrão.
- **Don't** usar gradientes em fundos, botões ou cards. Gradientes só existem em brand marks pontuais (login SVG, avatar da sidebar).
- **Don't** adicionar emojis, mascotes, ilustrações ou personagens. Se a interface precisa desses recursos pra ser calorosa, algo está errado nos dados.
- **Don't** competir Bordeaux e Teal na mesma superfície. Bordeaux vence em ação e marca; Teal só aparece como accent de valor líquido/sucesso onde Bordeaux não está.
- **Don't** usar shadow-md ou mais forte em cards estáticos. Shadows são resposta a estado (hover, focus, modal).
- **Don't** centralizar main content ou tabelas. Left-anchored do padding 28px é a regra.
