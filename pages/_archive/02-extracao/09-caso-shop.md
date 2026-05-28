---
layout: brutalist-base
metaNumber: "17"
metaSection: "EXTRAÇÃO"
metaSubtitle: "caso real"
metaRight: "shop · 100+ files"
contentAlign: "top"
---

<TitleBlock
  eyebrow="o módulo que virou lixeira"
  outlined="O CASO"
  solid="SHOP"
  accent="/"
  tail="100+ arquivos · 3 responsabilidades"
  size="small"
/>

<div class="shop-grid">
<div class="shop-tree">

```text {all|2-4|5-7|8-10|11-14|all}
app-modules/shop/
├── Cart/
│   ├── Models/
│   └── Services/
├── Catalog/
│   ├── Models/
│   └── Services/
├── Checkout/
│   ├── Services/
│   └── Jobs/
├── Orders/
│   ├── Models/
│   └── Notifications/
├── Payment/
│   ├── Gateways/
│   └── Jobs/
└── Shipping/
    ├── Carriers/
    └── Services/
```

</div>
<div class="shop-resp">

<v-click>

<div class="resp-head">
<span class="resp-head-num">100+</span>
<span class="resp-head-label">arquivos · 3 responsabilidades misturadas</span>
</div>

<v-clicks>

<div class="resp-card resp-card--blue">
<div class="resp-card-head">
  <span class="resp-card-num">01</span>
  <span class="resp-card-name"><span class="g g-a">CATÁLOGO</span></span>
</div>
<div class="resp-card-body">produtos, categorias, preços, busca <span class="resp-tag">(dados)</span></div>
</div>

<div class="resp-card resp-card--purple">
<div class="resp-card-head">
  <span class="resp-card-num">02</span>
  <span class="resp-card-name">TRANSAÇÃO</span>
</div>
<div class="resp-card-body">carrinho, checkout, pagamento <span class="resp-tag">(fluxo de compra)</span></div>
</div>

<div class="resp-card resp-card--green">
<div class="resp-card-head">
  <span class="resp-card-num">03</span>
  <span class="resp-card-name">OPERAÇÃO</span>
</div>
<div class="resp-card-body">pedidos, estoque, envio <span class="resp-tag">(pós-venda)</span></div>
</div>

</v-clicks>

</v-click>

</div>
</div>

<style>
.shop-grid {
  display: grid;
  grid-template-columns: 44% 1fr;
  gap: 1.6rem;
  margin-top: 0.7rem;
}
.shop-tree :deep(pre) {
  margin: 0;
  background: transparent;
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 3px;
  padding: 0.7rem 0.9rem;
}
.shop-tree :deep(.shiki) {
  background: transparent !important;
  font-size: 0.72rem !important;
  line-height: 1.45;
}
.shop-resp {
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  min-width: 0;
}
.resp-head {
  display: flex;
  align-items: baseline;
  gap: 0.6rem;
  padding: 0.3rem 0 0.5rem;
  border-bottom: 1px dashed rgba(255,255,255,0.1);
  margin-bottom: 0.3rem;
}
.resp-head-num {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 1.5rem;
  color: var(--red);
  letter-spacing: -0.02em;
}
.resp-head-label {
  font-family: var(--font-mono);
  font-size: 0.66rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--dim);
}
.resp-card {
  padding: 0.5rem 0.7rem 0.6rem;
  border-radius: 3px;
  border-left: 3px solid var(--resp-accent, var(--red));
  background: linear-gradient(180deg, rgba(20,20,24,0.55), rgba(10,10,12,0.75));
  border-top: 1px solid rgba(255,255,255,0.05);
  border-right: 1px solid rgba(255,255,255,0.05);
  border-bottom: 1px solid rgba(255,255,255,0.05);
}
.resp-card--blue   { --resp-accent: var(--accent-blue); }
.resp-card--purple { --resp-accent: var(--accent-purple); }
.resp-card--green  { --resp-accent: var(--accent-green); }
.resp-card-head {
  display: flex;
  align-items: baseline;
  gap: 0.55rem;
  margin-bottom: 0.2rem;
}
.resp-card-num {
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--dim);
  font-weight: 700;
}
.resp-card-name {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 1.05rem;
  letter-spacing: 0.02em;
  color: var(--resp-accent);
}
.resp-card-body {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: #c8c2b6;
  line-height: 1.45;
}
.resp-tag {
  font-family: var(--font-serif);
  font-style: italic;
  color: var(--dim);
  font-size: 0.92em;
}
</style>

<!--
"No ecommerce, a gente já tinha modularizado. Mas nosso módulo shop tinha virado uma lixeira. 100+ arquivos fazendo 3 coisas completamente diferentes. Catálogo de produtos e processamento de pagamento estavam no mesmo módulo. Isso é tipo botar a lavanderia dentro da cozinha porque as duas usam água."
-->

---
layout: brutalist-base
metaNumber: "17.1"
metaSection: "EXTRAÇÃO"
metaSubtitle: "regra de ouro"
metaRight: "pergunta dupla"
contentAlign: "top"
---

<TitleBlock
  eyebrow="a pergunta que revela boundaries"
  outlined="SE EU"
  solid="DELETAR…"
  accent="?"
  tail="o teste dos dois lados"
  size="small"
/>

<div class="grid grid-cols-2 gap-6 mt-6">
<div>

<v-click>

<div class="rule-card">
<div class="rule-card-q">
  <span class="rule-q-quote">"</span>Se eu deletar o catálogo,<br>o checkout quebra?<span class="rule-q-quote">"</span>
</div>
<div class="rule-card-a">NÃO.</div>
<div class="rule-card-body">
O carrinho já tem snapshot dos produtos<br>
(preço, nome, SKU). Checkout não consulta<br>
o catálogo na hora de finalizar.
</div>
</div>

</v-click>

</div>
<div>

<v-click>

<div class="rule-card">
<div class="rule-card-q">
  <span class="rule-q-quote">"</span>Se eu deletar o checkout,<br>o catálogo quebra?<span class="rule-q-quote">"</span>
</div>
<div class="rule-card-a">NÃO.</div>
<div class="rule-card-body">
O catálogo exibe produtos.<br>
Ele não sabe e não precisa saber<br>
como o checkout funciona.
</div>
</div>

</v-click>

</div>
</div>

<v-click>

<div class="rule-final">
<span class="rule-final-mark">▸</span>
<div>
Se dois grupos de código não sabem da existência<br>
um do outro… eles não pertencem ao <b>mesmo módulo</b>.
</div>
</div>

</v-click>

<style>
.rule-card {
  padding: 0.85rem 1rem 0.9rem;
  border-radius: 3px;
  border: 1px solid rgba(255,255,255,0.07);
  border-left: 3px solid var(--accent-green);
  background: linear-gradient(180deg, rgba(20,20,24,0.55), rgba(10,10,12,0.75));
}
.rule-card-q {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.05rem;
  color: #c8c2b6;
  line-height: 1.4;
  margin-bottom: 0.5rem;
}
.rule-q-quote { color: var(--red); font-size: 1.3rem; line-height: 0; }
.rule-card-a {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 2.3rem;
  color: var(--accent-green);
  letter-spacing: -0.01em;
  line-height: 1;
  margin: 0.3rem 0 0.55rem;
}
.rule-card-body {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: #b9b3a9;
  line-height: 1.5;
}
.rule-final {
  margin-top: 1.6rem;
  padding: 0.95rem 1.2rem;
  border: 1px solid rgba(255, 45, 32, 0.35);
  border-left: 4px solid var(--red);
  background: linear-gradient(180deg, rgba(255,45,32,0.06), rgba(10,10,12,0.5));
  display: flex;
  gap: 0.85rem;
  align-items: flex-start;
}
.rule-final-mark {
  color: var(--red);
  font-size: 1.1rem;
  line-height: 1.5;
}
.rule-final > div {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 1.05rem;
  line-height: 1.5;
  color: var(--bone);
  letter-spacing: -0.005em;
}
.rule-final b { color: var(--red); }
</style>

<!--
"Essa é a regra de ouro: se dois pedaços de código não sabem da existência um do outro, eles não deveriam morar juntos. Catálogo não importa nenhuma classe de checkout. Checkout não importa nenhuma classe de catálogo. Não tem import direto entre eles. Achei meu boundary."
-->
