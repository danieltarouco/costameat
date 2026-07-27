---
score: 22
maxScore: 40
p0: 2
p1: 4
p2: 2
cognitiveLoad: 3/8
method: dual-agent
target: "index.html:panel-painel"
timestamp: 2026-07-27T20-19-03Z
slug: index-html-painel
---
# Critique — Costameat Painel

**Method:** dual-agent (A: Design Director / heurística · B: Detector CLI + evidência)
**Target:** `index.html` — `<section id="panel-painel">` (L1374–1410) + `renderPainel`, `renderPainelPizza`, `renderPainelBarras` (L3020–3313)
**Reference:** `DESIGN.md` — *The Distributor's Desk* (Bordeaux #991b1b + Stone + Teal, sem gradientes, sem emojis, warm-cool duality, Bordeaux isolation)
**Date:** 2026-07-27

---

## 1. Design Health Score

**Nielsen Heuristics: 22 / 40** — abaixo do bar shippable para uma ferramenta design-led. As duas maiores brechas são H4 (Consistência) e H9 (Recuperação de erro).

| # | Heurística | Nota | Falha principal |
|---|---|---|---|
| H1 | Visibility of system status | 3 | Mês visível + "hoje" destacado; falta "última atualização" (freshness). |
| H2 | Match with real world | 2 | "RCA 1400", "Qtde Entr." sem gloss/tooltip. |
| H3 | User control & freedom | 3 | Prev/next + dropdown + Hoje, mas sem atalhos de teclado nem compare-to-year-ago. |
| H4 | Consistency & standards | **1** | Roxo/ciano/slate/gradient no KPI 4 + donut com 10 cores arbitrárias; 4º KPI com anatomia diferente. |
| H5 | Error prevention | 3 | Read-only; navegação de mês limpa. |
| H6 | Recognition rather than recall | 2 | "Margem real" sem breakdown; códigos de departamento sem nome expandido. |
| H7 | Flexibility & efficiency | 2 | Sem atalhos, sem drilldown, sem compare-to. |
| H8 | Aesthetic & minimalist | 2 | Composição contida, mas paleta invasiva cria ruído. |
| H9 | Help users recover from errors | **2** | Emojis 📊 e 📅 em empty-states violam explicitamente o DESIGN.md. |
| H10 | Help & documentation | 2 | Sem fórmula de Margem real na tela; documentação só via `<title>` hover. |

**Cognitive Load: 3 / 8** — dashboard mostra tudo o tempo todo, sem herói, sem drilldown, sem chunking progressivo. Working-memory (RCA, códigos, fórmula) é a maior perda.

**Detector CLI (bundled):** exit code **2** · 171 findings totais · **17 findings no scope do Painel — 17/17 true positive** após triagem.

---

## 2. Design Specificity Verdict

O Painel é **apenas metade autoral do Costameat**. A única decisão verdadeiramente domain-specific — colorir cada barra diária por *margem realizada* (teal ≥12% → cyan 5–12% → warn 0–5% → danger negativa → stone "sem venda") — é exatamente o tipo de pensamento que um controller de distribuição precisa. Essa decisão sozinha vale muito.

Tudo em volta poderia ter vindo de um dashboard SaaS genérico: 4 KPIs em linha, um donut, um bar chart, um chip-toggle de mês. **A paleta trabalha ativamente contra o DESIGN.md**: o KPI "Vendido por canal" pinta a Cayena em **gradientes roxos** (`#8b5cf6 → #a855f7`) que não existem em lugar nenhum do Costameat; o donut cicla por **10 cores arbitrárias** (ciano, sky, âmbar, roxo, red-não-signal-red); o bar chart hardcoda **slate cool grays** (`#1e293b`, `#94a3b8`, `#f1f5f9`) no lugar dos stones quentes que dominam o app. Bordeaux — a voz da marca — aparece em **um único ponto** no Painel (o valor de Faturamento total).

**Se você tirasse o logo do topo, nenhum usuário saberia que produto está olhando.** Lê como um resumo de distribuição de alimentos, não como *o resumo do Costameat*.

---

## 3. What's Working (3 fortes específicos)

1. **Barras coloridas por faixa de margem** (`renderPainelBarras`, L3268–3273). Inverte a leitura padrão "barra maior = melhor dia" e força o controller a olhar rentabilidade, não volume. Um dia vermelho ao lado de uma parede de tealalways = história instantânea. Este é o momento em que o produto prova que entende o domínio.

2. **Delta chip pattern** (`painelDeltaChip`, L3020–3027). `▲ 3.2%` / `▼ 4.1%` / `→ 0.2%` em verde/vermelho/cinza, colado ao valor do KPI, com `tabular-nums` e — precisamente correto matematicamente — `pp` (percentage points) para margem, não `%`. Alguém pensou na matemática.

3. **Seletor de mês left-anchored** (chip-toggle L1376–1380). ‹ / dropdown / › em um único chip + botão ghost "Hoje" ao lado dá três affordances numa linha sem virar toolbar. Está autoralmente executado dentro do mandato "topbar quieta" do DESIGN.md.

---

## 4. Priority Issues

### **P0 — Cayena com gradiente roxo viola 3 regras simultaneamente**
**Onde:** `index.html:3115-3137` (KPI "Vendido por canal", `renderPainel`) — hex `#8b5cf6`, `#a855f7`, `transition: width`.
**Por que importa:** Roxo não existe em nenhum outro lugar do Costameat. DESIGN.md proíbe explicitamente gradientes em fills ("gradientes só existem em brand marks pontuais"), viola Warm-Cool Duality Rule e Bordeaux Isolation Rule. A `transition: width` ainda por cima é motion decorativa ("Movimento existe como resposta a ação, nunca como decoração"). É a violação mais densa do Painel inteiro.
**Fix:** Redesenhar como duas barras de solid fill: Cayena em `var(--primary)` (Bordeaux), Equipe Interna em `var(--ink-slate-soft)` ou `var(--stone-shelf-strong)`. Remover `transition: width`; se precisar animar, `transform: scaleX()` com `transform-origin: left`. Labels 12px 600 tabular-nums, values right-aligned.
**Comando:** `/colorize`

### **P0 — Donut cicla por 10 cores arbitrárias, 5 delas fora do sistema**
**Onde:** `index.html:3157` — `const COLORS = ["#0f766e", "#0891b2", "#8b5cf6", "#d97706", "#dc2626", "#16a34a", "#a855f7", "#0ea5e9", "#f59e0b", "#ef4444"]`.
**Por que importa:** Ciano, roxo (×2), sky, âmbar, `#ef4444` (que é red-genérico, não signal-danger `#dc2626`) — nenhum vive no DESIGN.md. Pior: no `% COLORS.length` (L3189), grupos 11+ **colidem** e dois departamentos recebem a mesma cor — bug de gráfico, não só de design. Para uma distribuidora com 15–20 grupos vai disparar.
**Fix:** Construir uma sequência categórica a partir da paleta autoral: `teal-controller` → `warn` → `info` → `danger-soft` → `ink-slate-soft` → tints do stone (2 variantes). Cap em 8 cores nomeadas; a partir de 9 grupos, top-8 + "Outros". Validar via `dataviz` skill palette.
**Comando:** `/colorize`

### **P1 — Bar chart hardcoda slate cool grays, quebra a warmth do app**
**Onde:** `index.html:3258, 3259, 3279, 3284, 3293, 3294, 3308` — `#1e293b`, `#94a3b8`, `#f1f5f9`, `#64748b`, `#e2e8f0`.
**Por que importa:** O DESIGN.md nomeia stone quente (`#1c1917`, `#57534e`, `#a8a29e`, `#e7e5e4`). Injetar slate esfria o card inteiro; ao lado da sidebar e topbar (quentes), o card parece portado de outro app.
**Fix:** Trocar por tokens: `var(--text)`, `var(--text-muted)`, `var(--border)`, `var(--border-strong)`. Chip escuro da linha "média" → `var(--ink-slate)` no lugar de `#1e293b`. Grid lines → `var(--border)`.
**Comando:** `/polish` + `/colorize`

### **P1 — Emojis 📊 e 📅 em empty-states violam explicitamente o DESIGN.md**
**Onde:** `index.html:3153` (📊 em `renderPainelPizza`), `index.html:3234` (📅 em `renderPainelBarras`).
**Por que importa:** DESIGN.md diz literalmente: "Don't adicionar emojis, mascotes, ilustrações ou personagens." Emojis renderizam inconsistentemente por OS, quebram o mandato "type disappears", e são inacessíveis (leitor de tela anuncia "gráfico crescente" ou "calendário" cru).
**Fix:** SVG inline em `var(--text-muted)` a 24px. Donut outline mínimo para o gráfico vazio; grid 2×2 de quadrados para as barras vazias. Componente `<span class="empty-icon">…</span>` reutilizável.
**Comando:** `/distill`

### **P1 — Bar chart fixo em ~1094px força scroll horizontal em viewports <1120px**
**Onde:** `index.html:3247-3250` (`barW=28, gap=6, chartW = padLeft + lastDay*(barW+gap) + gap`).
**Por que importa:** No tablet e no card padrão (~700–900px disponíveis), o usuário rola horizontalmente para ver o mês inteiro — antipattern conhecido. Text a 9–9.5px está **abaixo de qualquer mínimo de acessibilidade** (WCAG recomenda ≥12px para info essencial). Casey (mobile) só vê ~10 dias por vez num iPhone 375px.
**Fix:** Bar width calculada a partir do container. Abaixo de ~800px, chavear para *weekday-aggregated* (7 barras: seg–dom, médias) ou "one letter per day" no eixo x. Texto mínimo 11px.
**Comando:** `/adapt`

### **P1 — Legendas com hexes ad-hoc (ciano/slate) e raios fora da escala (2/3px)**
**Onde:** Donut legend L3207–3210 (12px, radius 3px), Barras legend L3305–3309 (radius 2px, `#0891b2`, `#e2e8f0`).
**Por que importa:** DESIGN.md rounded-scale é 4/6/8/12/16/pill. Ciano `#0891b2` introduz um segundo teal fora do único Controller Teal `#0f766e`. Custo visual baixo, mas mostra que a paleta não está cabeada aos tokens no código de render.
**Fix:** Radius → `4px` (r-sm). Ciano `#0891b2` → variante mais escura do teal (`color-mix(in oklab, var(--secondary), var(--ink) 15%)`) ou tint do stone. Slate `#e2e8f0` → `var(--stone-shelf)` ou `var(--border)`.
**Comando:** `/colorize` + `/polish`

### **P2 — KPI 4 tem anatomia diferente das outras três, quebra o ritmo do grid**
**Onde:** `index.html:3115-3137`. "Vendido por canal" traz duas mini progress bars onde os outros três KPIs trazem valor + delta + hint.
**Por que importa:** Num grid de 4 colunas, o peso visual do 4º slot é diferente (mais alto, sem número herói). A linha perde ritmo. E a métrica responde "qual proporção?" — mas o controller já sabe pela estrutura. Não há *decisão* atrelada: o que fazer com um 47/53?
**Fix:** Duas opções — (a) reestruturar como valor herói "Mix Cayena %" + delta chip + sparkline dos últimos 6 meses no hint (mesma anatomia dos irmãos); (b) promover a divisão de canal a um card próprio abaixo dos KPIs e colocar outra métrica no slot 4 (Ticket médio da NF, ou Melhor grupo do mês).
**Comando:** `/shape`

### **P2 — Ramp de tipografia com gaps (10/12/20px) usados mas não documentados**
**Onde:** Chip delta L3020–3026, L3106 (10px); labels de canal L3119, L3128 (12px); topbar title L396 (20px); tag sidebar L253, L262 (10px); subtitle topbar/card L330 (12px).
**Por que importa:** DESIGN.md declara 11/13/14/16/22, mas 10/12/20 estão em uso ativo pelo código. Ou a especificação está incompleta (mais provável — 20px do topbar é intencional), ou o código está drifando. Ambos precisam ser reconciliados.
**Fix:** Duas rotas: (a) documentar `label-xs 10px 600` e `body-md 12px 500` e `heading-topbar 20px 700` no `typography` table do DESIGN.md; (b) OU migrar tudo para 11/13/22 e aceitar reflow. Recomendo (a) — o uso já está estabilizado.
**Comando:** `/typeset` ou `/document`

---

## 5. Persona Red Flags

### **Alex — Controller de poder (usa diariamente, quer velocidade)**
- Sem navegação de mês por teclado (`←`/`→`).
- Sem compare-to-year-ago. Sazonalidade em food distribution é enorme; MoM é a comparação errada.
- Sem drilldown. Clicar numa fatia do donut não filtra; clicar num dia ruim não pula pra NFs. Alex precisa sair do Painel para responder qualquer follow-up.
- Sem decomposição da Margem real na tela (CMV vs imposto vs comissão). A regra de warn-color do DESIGN.md **foi feita pra isso** e não é usada.
- Sem export CSV do `days[]` do bar chart.

### **Sam — Usuário de acessibilidade (screen reader + alto contraste)**
- SVG charts sem `role="img"` nem `aria-label`. Só `<title>` em children, que leitores anunciam inconsistentemente.
- Legenda color-only para faixas de margem — deuteranopia (~5% dos homens) não distingue `#0f766e` de `#0891b2`, exatamente as duas faixas mais frequentes.
- Contraste de `#94a3b8` sobre branco = 2.7:1 (falha WCAG AA).
- Texto abaixo do mínimo (9–10.5px em labels de dia, tick de grid e valor no topo da barra).
- Delta chips com `▲`/`▼` puros, sem `aria-label="aumentou 3.2%"`.
- Tooltips `<title>` são hover-only — sem equivalente para toque ou teclado.

### **Casey — Controller mobile (checa números do caminhão)**
- Bar chart sempre em scroll horizontal em qualquer viewport <1120px.
- KPIs empilham em 1 coluna <560px → 4 cards altos antes dos gráficos = scroll longo até a história do mês.
- Setas do mês são hit targets ~24×24px (mín iOS = 44px).
- Linha do legend do donut com 4 colunas (código + nome + valor + %) elipsa agressivo.
- `<title>` SVG não dispara no tap — Casey não investiga um dia sem trocar pra desktop.

---

## 6. Minor Observations

- `.kpis` (L473) e `.painel-kpis-grid` (L1121) aplicam-se ao mesmo nó com specificity igual — resolução por ordem de stylesheet. Frágil. Escolher uma.
- `fmtMoneyShort` (L2993) trunca a 1 casa (`R$ 1,2M`) mas o centro do donut usa isso para totais que podem cair em `R$ 999k` quando o valor real é `R$ 999.400` — perda de precisão significativa para um controller.
- Linha "média diária" é dashed (L3292) e o chip escuro flutua na direita — cobre a barra do último dia quando a média é alta. Deslocar para a esquerda ou usar callout.
- `porDia[dKey]` (L3074–3080) descarta silenciosamente vendas cujo `v.data` não bate exatamente. Edge case defensivo mas silencioso.
- L3153 empty-state usa `<h3>` dentro de card cujo header já é `<h3>` — inconsistência de heading structure.
- `PAINEL_CAYENA_RCA = "1400"` hardcoded em L2915 — em ferramenta multi-tenant isso vai no state/config.
- Centro do donut escreve `#0f172a` (L3203) — deveria ser `var(--text)` (`#1c1917`). Mesmo problema de warmth do bar chart.
- Backdrop do modal `rgba(15,23,42,0.55)` sancionado pelo DESIGN.md, mas o backdrop de dialog `rgba(15,23,42,0.4)` (L4100) é o mesmo family com alpha diferente — cabear ambos a um `--overlay-*` token.
- Borda `#fca5a5` em botão danger (L371, L578) documentada explicitamente no DESIGN.md — promover a `--signal-danger-soft` token no design.json.
- Comentário L3023 `// p/ métricas onde subir é ruim (não usado aqui)` — dead code path.

---

## 7. Questions to Consider

1. **Por que Cayena é roxo, se nada mais no Costameat é roxo?** Cayena é uma marca externa com identidade própria, ou alguém pegou a "cor não usada" mais próxima do Tailwind? Se Cayena tem cor de marca real, respeite ela em todo lugar ou em nenhum.

2. **O que o controller deve *fazer* depois de olhar essa página?** O Painel termina em "aqui estão os números" sem próxima ação. Controller de distribuidora não olha margem pra admirar; olha pra corrigir um dia ruim. Onde está a tira "3 dias abaixo do seu threshold — investigar?"

3. **Por que 'Margem real' não tem decomposição no Painel?** É *o* número, e ainda assim o usuário precisa sair pra ver qual de CMV/imposto/comissão mexeu. A regra warn-color do DESIGN.md é feita justamente pra isso — e não é usada na página resumo.

4. **31 barras é o primitivo certo pra uma visão mensal, ou é uma tabela fingindo ser gráfico?** Um heatmap por dia-da-semana × semana-do-mês, ou small-multiples por grupo, daria pattern recognition em vez de aritmética-por-barra.

5. **Se sidebar e topbar são a voz de marca persistente, por que o Painel passa tanto tempo sem dizer Bordeaux?** O único toque Bordeaux (valor do Faturamento total) é *afogado* por roxo, ciano, teal, warn e danger no mesmo viewport. E se o "herói" do Painel fosse **um** momento Bordeaux (uma marca ao lado do nome do mês) que nomeia o report como *a visão do Costameat*, não como *uma* visão?

---

## 8. Sign-off

**Overall grade: C+ / B-.** O pensamento de domínio é real (barras por faixa de margem, delta chips, mês-âncora). A execução do design system briga ativamente com o DESIGN.md recém-escrito.

**Duas P0 (roxo/gradient no KPI 4 + paleta arbitrária do donut) e quatro P1 (slate cools + emojis + bar width fixa + legendas) bloqueiam o Painel de sentir *do Costameat* em vez de *um dashboard genérico*.**

**Ordem de ataque:** `colorize` (KPI 4 + donut + slate) → `distill` (emojis) → `adapt` (bar chart mobile) → `shape` (KPI 4 anatomy) → `typeset`/`document` (ramp tipografia).
