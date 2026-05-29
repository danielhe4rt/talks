---
layout: brutalist-base
metaNumber: "16"
metaSection: "CONVENÇÕES"
metaSubtitle: "panel · *"
contentAlign: "top"
clicks: 2
---

<div class="conv-head">
  <span class="conv-eyebrow"><span class="eyebrow-mark">◆</span> convenção <b>#2</b></span>
  <span class="conv-divider" />
  <span class="conv-tagline">um público · um painel</span>
</div>

<div class="conv-title-row">

# PANEL <span class="conv-glyph g g-b">·</span> <span class="conv-star">*</span>

<div class="conv-kicker">
  <div class="conv-kicker__top">— frontend fatiado por <b>audiência</b>.</div>
  <div class="conv-kicker__bot"><span class="serif-em">mesma régua dos outros</span> — <b>muda só o stack</b>.</div>
</div>

</div>

<div class="panels-grid">

<div class="panels-tabs">

<div class="ptab" :class="{ active: $clicks === 0 }">
  <span class="ptab__num">01</span>
  <div class="ptab__body">
    <span class="ptab__name">panel-admin</span>
    <span class="ptab__sub">acesso interno</span>
    <span class="ptab__stack">filament</span>
  </div>
  <span class="ptab__dot" />
</div>

<div class="ptab" :class="{ active: $clicks === 1 }">
  <span class="ptab__num">02</span>
  <div class="ptab__body">
    <span class="ptab__name">panel-app</span>
    <span class="ptab__sub">cliente logado</span>
    <span class="ptab__stack">livewire</span>
  </div>
  <span class="ptab__dot" />
</div>

<div class="ptab" :class="{ active: $clicks === 2 }">
  <span class="ptab__num">03</span>
  <div class="ptab__body">
    <span class="ptab__name">panel-guest</span>
    <span class="ptab__sub">público · landing</span>
    <span class="ptab__stack">blade · seo</span>
  </div>
  <span class="ptab__dot" />
</div>

</div>

<div class="panels-stage">

<div class="panel-frame" v-show="$clicks === 0">
  <div class="panel-frame__head">
    <span class="panel-frame__ns">namespace <b>Shop\PanelAdmin</b></span>
    <span class="panel-frame__audience">operação · suporte · financeiro</span>
  </div>

```text {*}{class:'!text-[0.78rem] !leading-snug'}
app-modules/panel-admin/
├── composer.json
├── src/
│   ├── Resources/
│   │   ├── Orders/
│   │   │   ├── OrderResource.php
│   │   │   ├── Pages/ListOrders.php
│   │   │   ├── Schemas/OrderForm.php
│   │   │   └── Tables/OrdersTable.php
│   │   ├── Products/ProductResource.php
│   │   └── Customers/CustomerResource.php
│   ├── Clusters/Catalog/CatalogCluster.php
│   ├── Pages/Dashboard.php
│   ├── Widgets/SalesOverview.php
│   └── AdminPanelProvider.php
└── resources/views/
```
</div>

<div class="panel-frame" v-show="$clicks === 1">
  <div class="panel-frame__head">
    <span class="panel-frame__ns">namespace <b>Shop\PanelApp</b></span>
    <span class="panel-frame__audience">quem já comprou e <span class="g g-c">voltou</span></span>
  </div>

```text {*}{class:'!text-[0.78rem] !leading-snug'}
app-modules/panel-app/
├── composer.json
├── src/
│   ├── Livewire/
│   │   ├── Dashboard.php
│   │   ├── OrderHistory.php
│   │   └── Timeline/Feed.php
│   ├── Pages/
│   │   ├── LoginPage.php
│   │   └── ProfilePage.php
│   └── PanelAppServiceProvider.php
└── resources/views/livewire/
```
</div>

<div class="panel-frame" v-show="$clicks === 2">
  <div class="panel-frame__head">
    <span class="panel-frame__ns">namespace <b>Shop\PanelGuest</b></span>
    <span class="panel-frame__audience">home · catálogo · landing</span>
  </div>

```text {*}{class:'!text-[0.78rem] !leading-snug'}
app-modules/panel-guest/
├── composer.json
├── src/
│   ├── Http/HomeController.php
│   └── PanelGuestServiceProvider.php
├── resources/views/
│   ├── home.blade.php
│   ├── catalog.blade.php
│   └── components/hero.blade.php
└── routes/web.php
```
</div>

</div>

</div>

<style>
.brutalist-content { padding-top: 0.2rem; }

.conv-title-row {
  display: flex;
  align-items: flex-end;
  gap: 1.2rem;
  margin: 0.05rem 0 0.55rem;
}
.brutalist-content :deep(.conv-title-row h1) {
  font-size: 2.8rem;
  line-height: 1;
  margin: 0;
  letter-spacing: -0.005em;
  flex: 0 0 auto;
}
.conv-glyph {
  color: var(--accent-purple);
  margin: 0 0.05em;
  font-weight: 900;
}
.conv-star {
  color: var(--accent-purple);
  text-shadow: 0 0 22px rgba(192, 132, 252, 0.45);
  font-weight: 900;
  margin-left: 0.05em;
}
.conv-kicker {
  display: flex;
  flex-direction: column;
  gap: 0.15rem;
  padding-bottom: 0.4rem;
  border-left: 1px solid rgba(192, 132, 252, 0.25);
  padding-left: 0.9rem;
  flex: 1 1 auto;
  min-width: 0;
}
.conv-kicker__top {
  font-family: var(--font-mono);
  font-size: 0.92rem;
  color: #c8c2b6;
  line-height: 1.3;
  letter-spacing: 0.01em;
}
.conv-kicker__top b { color: var(--bone); font-weight: 700; }
.conv-kicker__bot {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: #9a9a9a;
  line-height: 1.35;
  letter-spacing: 0.01em;
}
.conv-kicker__bot b { color: var(--bone); font-weight: 700; }
.conv-kicker__bot .serif-em {
  font-family: var(--font-serif);
  font-style: italic;
  color: #b9b3a9;
}

/* compact eyebrow + tagline strip */
.conv-head {
  display: flex;
  align-items: center;
  gap: 0.7rem;
  margin: 0 0 0.15rem;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.2s;
}
.conv-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.9rem;
  color: #b9b3a9;
}
.conv-eyebrow .eyebrow-mark { color: var(--red); font-size: 0.65rem; }
.conv-eyebrow b { color: var(--bone); font-style: normal; font-family: var(--font-mono); }
.conv-divider {
  flex: 0 0 80px;
  height: 1px;
  background: linear-gradient(to right, var(--accent-purple), transparent);
}
.conv-tagline {
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--dim);
}


/* === 2-col grid: tabs left, tree right === */
.panels-grid {
  display: grid;
  grid-template-columns: 0.85fr 1.6fr;
  gap: 1.4rem;
  align-items: stretch;
  margin-top: 0.3rem;
}

/* === vertical tabs === */
.panels-tabs {
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
}
.ptab {
  position: relative;
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
  gap: 0.7rem;
  padding: 0.6rem 0.85rem 0.65rem;
  border: 1px solid rgba(255,255,255,0.07);
  border-left: 3px solid rgba(192, 132, 252, 0.22);
  border-radius: 3px;
  background: linear-gradient(180deg, rgba(20,20,24,0.4), rgba(10,10,12,0.55));
  opacity: 0.45;
  filter: grayscale(0.4);
  transition: opacity 0.3s ease, filter 0.3s ease, border-color 0.3s ease,
              box-shadow 0.3s ease, transform 0.3s ease, background 0.3s ease;
}
.ptab.active {
  opacity: 1;
  filter: grayscale(0);
  border-left-color: var(--accent-purple);
  box-shadow: 0 0 0 1px rgba(192, 132, 252, 0.28),
              0 0 24px rgba(192, 132, 252, 0.18);
  background: linear-gradient(180deg, rgba(30,22,40,0.7), rgba(15,12,22,0.85));
  transform: translateX(2px);
}
.ptab__num {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 1.4rem;
  color: var(--accent-purple);
  letter-spacing: 0.02em;
  line-height: 1;
}
.ptab__body {
  display: flex;
  flex-direction: column;
  gap: 0.08rem;
  min-width: 0;
}
.ptab__name {
  font-family: var(--font-mono);
  font-size: 0.95rem;
  font-weight: 700;
  color: var(--bone);
  letter-spacing: 0.01em;
}
.ptab__sub {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.75rem;
  color: #b9b3a9;
  letter-spacing: 0.01em;
}
.ptab__stack {
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--dim);
  margin-top: 0.1rem;
}
.ptab__dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(192, 132, 252, 0.15);
  transition: background 0.3s ease, box-shadow 0.3s ease;
}
.ptab.active .ptab__dot {
  background: var(--accent-purple);
  box-shadow: 0 0 12px rgba(192, 132, 252, 0.7);
}

/* === panel stage (stacked, switches with v-click) === */
.panels-stage {
  position: relative;
  min-height: 18.5rem;
}
.panel-frame {
  position: absolute;
  inset: 0;
  padding: 0.6rem 0.85rem 0.55rem;
  border: 1px solid rgba(192, 132, 252, 0.22);
  border-left: 3px solid var(--accent-purple);
  border-radius: 3px;
  background: linear-gradient(180deg, rgba(20,20,24,0.6), rgba(10,10,12,0.78));
  display: flex;
  flex-direction: column;
  overflow: hidden;
  min-width: 0;
}
.panel-frame :deep(.shiki),
.panel-frame :deep(pre) {
  max-width: 100%;
  overflow-x: hidden;
}
.panel-frame__head {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 1rem;
  padding-bottom: 0.4rem;
  margin-bottom: 0.4rem;
  border-bottom: 1px solid rgba(255,255,255,0.06);
}
.panel-frame__ns {
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent-purple);
  font-weight: 700;
}
.panel-frame__ns b {
  font-weight: 700;
  color: var(--bone);
  letter-spacing: 0.05em;
}
.panel-frame__audience {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.8rem;
  color: #b9b3a9;
}
.panel-frame :deep(pre) {
  background: transparent !important;
  border: none !important;
  margin: 0;
  padding: 0;
}
.panel-frame :deep(.shiki) { background: transparent !important; }

</style>

<!--
"Convenção número dois: panel."

"O frontend fatia por AUDIÊNCIA. Cada painel vira módulo próprio — mesma régua de qualquer outro módulo: composer.json no topo, src/, resources/, ServiceProvider. Mas o STACK muda conforme o público. Olha só."

[estado inicial — panel-admin ativo]
"01: panel-admin. Stack: Filament. Quem mexe aqui é operação, suporte, financeiro — gente que trabalha NO produto, não COM o produto. Resources de Product, Order. Páginas de Dashboard. Widgets de overview. Tudo dentro de src/Filament/. namespace Shop\\PanelAdmin."

[click 1 — panel-app ativo]
"02: panel-app. Cliente logado. Stack: Livewire. Dashboard interativo, histórico de pedido, timeline. As pages de auth ficam em src/Pages/. Views em resources/views/livewire/. namespace Shop\\PanelApp. Quem já comprou e voltou."

[click 2 — panel-guest ativo]
"03: panel-guest. O público. Aqui o stack despe — é Blade puro. Home, catálogo, landing. Um HomeController, um ServiceProvider, e o resto é template. SEO friendly, sem peso de Livewire onde não precisa. namespace Shop\\PanelGuest."

"Repara: três pastas. Três composer.json. Três ServiceProviders. Três namespaces. Cada audiência tem o stack QUE ELA precisa — não o stack que o app inteiro usa. E NENHUM dos três sabe que os outros existem."

"O backend? Os mesmos módulos de domínio: sales, payment, fulfillment. Só muda a casca."

[transição] "Uma última coisa antes de fechar essa parte."
-->
