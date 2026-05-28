---
layout: brutalist-base
metaNumber: "24"
metaSection: "FECHAMENTO"
metaSubtitle: "4 regras pra levar pra casa"
contentAlign: "top"
---

<div class="rules-header">
  <span class="rules-eyebrow"><span class="eyebrow-mark">◆</span> leve isso pra casa</span>
  <h1 class="rules-title">
    <span class="rules-outline">4 REGRAS</span>
    <span class="rules-solid">PRA LEVAR<span class="rules-glyph">.</span></span>
  </h1>
</div>

<div class="rules-grid">

<v-clicks>

<div class="rule rule--blue">
  <div class="rule-head">
    <span class="rule-num">01</span>
    <span class="rule-tag">boundaries</span>
  </div>
  <div class="rule-body">
    Extraia <span class="g g-a">responsabilidades</span>, não reorganize pastas.
  </div>
  <div class="rule-foot">
    O boundary importa mais que a estrutura. Flat, Clean, DDD — tanto faz, desde que o módulo seja isolado.
  </div>
</div>

<div class="rule rule--green">
  <div class="rule-head">
    <span class="rule-num">02</span>
    <span class="rule-tag">events</span>
  </div>
  <div class="rule-body">
    Módulos se comunicam por <span class="g g-b">EVENTOS</span>, não por imports.
  </div>
  <div class="rule-foot">
    <code>event(new OrderPlaced())</code> e quem quiser que escute. Zero acoplamento direto.
  </div>
</div>

<div class="rule rule--yellow">
  <div class="rule-head">
    <span class="rule-num">03</span>
    <span class="rule-tag">priority</span>
  </div>
  <div class="rule-body">
    Comece pelo módulo que mais DÓI.
  </div>
  <div class="rule-foot">
    Não modularize o projeto inteiro de uma vez. Encontre o que mais dói e extraia esse.
  </div>
</div>

<div class="rule rule--purple">
  <div class="rule-head">
    <span class="rule-num">04</span>
    <span class="rule-tag">context</span>
  </div>
  <div class="rule-body">
    Documente as decisões, não o código.
  </div>
  <div class="rule-foot">
    <code>CONTEXT.md</code> com glossário de domínio. ADRs pra decisões difíceis. Doc que o agente lê.
  </div>
</div>

</v-clicks>

</div>

<style scoped>
.rules-header {
  margin-bottom: 0.9rem;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.15s;
}

.rules-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.95rem;
  color: #b9b3a9;
  margin-bottom: 0.25rem;
}
.eyebrow-mark { color: var(--red); font-size: 0.65rem; }

.rules-title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 2.6rem;
  line-height: 0.95;
  color: var(--bone);
  margin: 0;
  letter-spacing: -0.005em;
  display: flex;
  gap: 0.55rem;
  align-items: baseline;
}
.rules-outline {
  -webkit-text-stroke: 1.5px var(--bone);
  color: transparent;
}
.rules-solid {
  color: var(--bone);
  position: relative;
}
.rules-glyph {
  color: var(--red);
  margin-left: 0.05em;
}

.rules-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.7rem 0.9rem;
  margin-top: 0.4rem;
}

.rule {
  position: relative;
  padding: 0.75rem 0.9rem 0.85rem;
  border-radius: 3px;
  background: linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75));
  border: 1px solid rgba(255, 255, 255, 0.07);
  font-family: var(--font-mono);
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  overflow: hidden;
}
.rule::before {
  content: "";
  position: absolute;
  inset: 0 auto 0 0;
  width: 3px;
  background: var(--rule-accent, var(--red));
  box-shadow: 0 0 14px var(--rule-glow, rgba(255, 45, 32, 0.4));
}

.rule--blue   { --rule-accent: var(--accent-blue);   --rule-glow: rgba(96, 165, 250, 0.35); }
.rule--green  { --rule-accent: var(--accent-green);  --rule-glow: rgba(110, 231, 161, 0.35); }
.rule--yellow { --rule-accent: var(--accent-orange); --rule-glow: rgba(255, 165, 58, 0.35); }
.rule--purple { --rule-accent: var(--accent-purple); --rule-glow: rgba(192, 132, 252, 0.35); }

.rule-head {
  display: flex;
  align-items: baseline;
  gap: 0.6rem;
}
.rule-num {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 1.55rem;
  line-height: 1;
  color: var(--rule-accent);
  letter-spacing: 0;
}
.rule-tag {
  font-family: var(--font-mono);
  font-size: 0.62rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--dim);
}

.rule-body {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 0.92rem;
  line-height: 1.35;
  color: var(--bone);
  letter-spacing: 0.005em;
}

.rule-foot {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.78rem;
  line-height: 1.45;
  color: #b9b3a9;
}
.rule-foot code {
  font-family: var(--font-mono);
  font-style: normal;
  background: rgba(255, 45, 32, 0.1);
  border: 1px solid rgba(255, 45, 32, 0.28);
  color: var(--bone);
  padding: 0.05em 0.35em;
  border-radius: 3px;
  font-size: 0.85em;
}
</style>

<!--
"Quatro coisas pra levar pra casa. Uma: extraia responsabilidades, não reorganize pastas. Não importa se é flat, clean ou DDD — o que importa é que o módulo é isolado. Dois: eventos como fronteira. Módulos não chamam código de outros módulos — eles disparam eventos e quem quiser escuta. Três: comece pelo que mais dói. Não precisa modularizar tudo amanhã. Quatro: documente as decisões. CONTEXT.md com o glossário do domínio. Não é doc que ninguém lê — é doc que o agente lê."
-->
