---
layout: brutalist-base
metaNumber: "18.1"
metaSection: "FECHAMENTO"
metaSubtitle: "monólito modular"
metaRight: "a mesma conta · em escala"
contentAlign: "top"
---

<div class="mm-head">
  <div>
    <div class="mm-eyebrow"><span class="mm-mark">◆</span> e quando a escala muda tudo?</div>
    <h1 class="mm-title">os grandes fizeram a <span class="mm-em g g-b">mesma conta</span>.</h1>
  </div>
  <div class="mm-hero">
    <span class="mm-hero-num">−90<span class="mm-hero-pct">%</span></span>
    <span class="mm-hero-lbl">custo · Prime Video<br>distribuiu cedo → voltou pro monólito</span>
  </div>
</div>

<div class="mm-spectrum">
  <div class="mm-node mm-node--side">
    <span class="mm-dot" />
    <span class="mm-node-name">monólito clássico</span>
    <span class="mm-node-sub">acopla tudo num bolo</span>
  </div>
  <span class="mm-track" />
  <div class="mm-node mm-node--center">
    <span class="mm-dot mm-dot--win" />
    <span class="mm-node-name mm-node-name--win">MONÓLITO MODULAR</span>
    <span class="mm-node-sub mm-node-sub--win">o sweet spot</span>
  </div>
  <span class="mm-track" />
  <div class="mm-node mm-node--side">
    <span class="mm-dot" />
    <span class="mm-node-name">microsserviços</span>
    <span class="mm-node-sub">complexidade distribuída</span>
  </div>
</div>

<div class="mm-gains">

<v-click>
<div class="gain">
  <mdi-package-variant-closed class="gain-icon" />
  <div class="gain-body">
    <div class="gain-title">deploy único</div>
    <div class="gain-text">um pipeline de build, test e deploy — não 80 serviços pra orquestrar.</div>
  </div>
  <span class="gain-src">Shopify Eng.</span>
</div>
</v-click>

<v-click>
<div class="gain">
  <mdi-trending-down class="gain-icon" />
  <div class="gain-body">
    <div class="gain-title">distribuir cedo cobra caro</div>
    <div class="gain-text">rede + orquestração têm conta. in-process não tem — por isso voltaram.</div>
  </div>
  <span class="gain-src">Prime Video · 2023</span>
</div>
</v-click>

<v-click>
<div class="gain">
  <mdi-shield-check-outline class="gain-icon" />
  <div class="gain-body">
    <div class="gain-title">boundary que o time respeita</div>
    <div class="gain-text">interface pública + implementação encapsulada, com enforce por ferramenta.</div>
  </div>
  <span class="gain-src">Packwerk · internachi</span>
</div>
</v-click>

<v-click>
<div class="gain">
  <mdi-source-branch class="gain-icon" />
  <div class="gain-body">
    <div class="gain-title">saída evolutiva</div>
    <div class="gain-text">mudar boundary é barato. extrai um módulo pra microservice só quando doer.</div>
  </div>
  <span class="gain-src">Jovanović · Grzybek</span>
</div>
</v-click>

</div>

<v-click>

<div class="mm-tail">
do seu legado ao catálogo da Shopify, a régua é a mesma: <b>modulariza primeiro</b> — <span class="mm-tail-em">distribui só quando a dor justificar.</span>
</div>

</v-click>

<style>
.brutalist-content { padding-top: 0.1rem; }

/* ---------- header ---------- */
.mm-head {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 1.5rem;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.12s;
}
.mm-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.98rem;
  color: #b9b3a9;
  margin-bottom: 0.2rem;
}
.mm-mark { color: var(--accent-green); font-size: 0.7rem; }
.mm-title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 2.5rem;
  line-height: 0.98;
  color: var(--bone);
  margin: 0;
  letter-spacing: -0.01em;
}
.mm-title .mm-em { color: var(--accent-green); }

.mm-hero {
  flex: none;
  display: flex;
  align-items: center;
  gap: 0.7rem;
  padding: 0.5rem 0.9rem;
  border: 1px solid rgba(110, 231, 161, 0.25);
  border-left: 3px solid var(--accent-green);
  border-radius: 3px;
  background: linear-gradient(180deg, rgba(110,231,161,0.08), rgba(10,10,12,0.6));
}
.mm-hero-num {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 2.6rem;
  line-height: 0.85;
  color: var(--accent-green);
  text-shadow: 0 0 24px rgba(110, 231, 161, 0.35);
}
.mm-hero-pct { font-size: 1.4rem; margin-left: 0.05em; }
.mm-hero-lbl {
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--dim);
  line-height: 1.35;
}

/* ---------- spectrum ---------- */
.mm-spectrum {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  margin: 1.05rem 0 0.85rem;
  padding: 0.2rem 0;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.28s;
}
.mm-node {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.15rem;
  text-align: center;
  flex: none;
}
.mm-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--frame);
  border: 1px solid var(--dim);
  margin-bottom: 0.1rem;
}
.mm-dot--win {
  width: 16px;
  height: 16px;
  background: var(--accent-green);
  border: none;
  box-shadow: 0 0 16px rgba(110, 231, 161, 0.7);
}
.mm-node-name {
  font-family: var(--font-mono);
  font-size: 0.74rem;
  color: #9a958c;
  letter-spacing: 0.02em;
}
.mm-node-name--win {
  font-weight: 700;
  font-size: 0.92rem;
  color: var(--bone);
  letter-spacing: 0.1em;
}
.mm-node-sub {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.68rem;
  color: var(--dim);
}
.mm-node-sub--win { color: var(--accent-green); }
.mm-track {
  flex: 1 1 auto;
  max-width: 9rem;
  height: 2px;
  background: linear-gradient(to right, var(--frame), rgba(110, 231, 161, 0.5));
  align-self: flex-start;
  margin-top: 4px;
}
.mm-spectrum .mm-track:last-of-type {
  background: linear-gradient(to right, rgba(110, 231, 161, 0.5), var(--frame));
}

/* ---------- gains 2x2 ---------- */
.mm-gains {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.7rem;
}
.gain {
  display: grid;
  grid-template-columns: auto 1fr;
  grid-template-rows: auto auto;
  column-gap: 0.7rem;
  row-gap: 0.2rem;
  align-items: start;
  padding: 0.65rem 0.85rem 0.7rem;
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-left: 3px solid var(--accent-green);
  border-radius: 3px;
  background: linear-gradient(180deg, rgba(20,20,24,0.55), rgba(10,10,12,0.78));
}
.gain-icon {
  grid-row: 1 / 3;
  font-size: 1.5rem;
  color: var(--accent-green);
  margin-top: 0.15rem;
}
.gain-title {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 0.92rem;
  color: var(--bone);
  letter-spacing: 0.005em;
}
.gain-text {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.85rem;
  line-height: 1.35;
  color: #b9b3a9;
}
.gain-src {
  grid-column: 2;
  margin-top: 0.3rem;
  justify-self: start;
  font-family: var(--font-mono);
  font-size: 0.56rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--accent-green);
  border: 1px solid rgba(110, 231, 161, 0.3);
  border-radius: 2px;
  padding: 0.08rem 0.4rem;
  opacity: 0.85;
}

/* ---------- tail ---------- */
.mm-tail {
  margin-top: 0.85rem;
  padding-top: 0.6rem;
  border-top: 1px solid var(--rule);
  font-family: var(--font-mono);
  font-size: 0.98rem;
  color: #c8c2b6;
  text-align: center;
}
.mm-tail b { color: var(--bone); font-weight: 700; }
.mm-tail-em {
  font-family: var(--font-serif);
  font-style: italic;
  color: var(--accent-green);
}
</style>

<!--
"Eu acabei de mostrar a MINHA conta: quando o produto pivota, eu troco um módulo sem cirurgia. E aí vem a dúvida: tá, mas isso é exagero de quem tem um app pequeno? Não. Quando a escala muda tudo de verdade, os grandes fizeram exatamente a mesma conta."

[hero — Prime Video]
"A Amazon Prime Video é o exemplo que calou a galera: eles tinham microsserviços, distribuíram cedo demais, e VOLTARAM pro monólito — cortaram 90% do custo. Distribuir não é grátis: tem rede, tem orquestração."

[click 1] "Deploy único. Um pipeline de build, test e deploy. A Shopify roda um dos maiores monólitos Rails do mundo, mais de mil devs, num codebase só — modular, com boundaries impostos por ferramenta."

[click 2] "Distribuir cedo cobra caro: rede e orquestração têm conta. In-process não tem. Por isso a Prime Video voltou."

[click 3] "Boundary que o time respeita de verdade. Interface pública, implementação encapsulada, e o enforce vem de ferramenta — Packwerk na Shopify, internachi no nosso caso. É o mesmo boundary que segurou meu pivot no slide anterior."

[click 4] "E a saída evolutiva: mudar boundary num monólito modular é barato. Se um dia a escala doer DE VERDADE, você extrai aquele módulo pra microservice. Mas só quando doer — Milan Jovanović e Kamil Grzybek batem nessa tecla há anos."

[click 5 — tail] "Do seu legado ao catálogo da Shopify, a régua é a mesma: modulariza primeiro, distribui só quando a dor justificar a conta."

[transição] "Então, pra fechar de vez..."
-->
