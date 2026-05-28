---
layout: section-modular
actNumber: "02"
actLabel: "ato 02 de 04"
eyebrow: "ato 2 · extração"
outlined: "ACHAR OS"
solid: "BOUNDARIES"
accent: "."
tail: "~12 min · conceitual"
---

## o teste da deleção · como achar os limites do seu código

<!--
"Então se organizar por tipo técnico é o problema... qual é a alternativa? Vamos aprender a encontrar os boundaries — os limites naturais do seu código."
-->

---
layout: brutalist-base
metaNumber: "09"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaRight: "regras · 3"
---

<TitleBlock
  eyebrow="o método"
  outlined="O TESTE"
  solid="DA DELEÇÃO"
  accent="™"
  tail="4 PERGUNTAS"
  size="normal"
/>

<div class="dt-intro">

<p class="dt-prompt">
Pega uma funcionalidade do seu sistema.<br>
Imagina que você deleta <b>TODOS</b> os arquivos dela.
</p>

<div class="dt-cards">

<v-clicks>

<div class="dt-card dt-card--q1">
  <div class="dt-card-head">
    <span class="dt-card-num">01</span>
    <span class="dt-card-tag">listar</span>
  </div>
  <div class="dt-card-body">
    Você consegue <b>listar todos os arquivos</b>?
  </div>
</div>

<div class="dt-card dt-card--q2">
  <div class="dt-card-head">
    <span class="dt-card-num">02</span>
    <span class="dt-card-tag">quebra</span>
  </div>
  <div class="dt-card-body">
    Quanto do sistema <b>quebra</b>?
  </div>
</div>

<div class="dt-card dt-card--q3">
  <div class="dt-card-head">
    <span class="dt-card-num">03</span>
    <span class="dt-card-tag">compartilhado</span>
  </div>
  <div class="dt-card-body">
    Algum desses arquivos é <b>usado por outra feature</b>?
  </div>
</div>

</v-clicks>

<div class="dt-card dt-card--q4">
  <div class="dt-card-head">
    <span class="dt-card-num">04</span>
    <span class="dt-card-tag">framework</span>
  </div>
  <div class="dt-card-body">
    Apagar o módulo <b>realmente apaga TUDO</b>?
  </div>
  <div class="dt-card-await">[ requer módulos ]</div>
</div>

</div>

<v-click>

<div class="dt-tail">
  <span class="dt-tail-mark">▶</span>
  <span>Vamos rodar esse teste no nosso legadão.</span>
</div>

</v-click>

</div>

<style>
.dt-intro {
  margin-top: 1.6rem;
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
}
.dt-prompt {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.35rem !important;
  color: #c8c2b6 !important;
  margin: 0 !important;
  line-height: 1.45 !important;
  max-width: 70%;
}
.dt-prompt b {
  font-family: var(--font-mono);
  font-style: normal;
  color: var(--red);
  letter-spacing: 0.05em;
}
.dt-cards {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.75rem;
  margin-top: 0.4rem;
}
.dt-card {
  border: 1px solid rgba(255,255,255,0.08);
  border-left: 3px solid var(--card-accent, var(--red));
  background: linear-gradient(180deg, rgba(20,20,24,0.55), rgba(10,10,12,0.75));
  padding: 0.75rem 0.85rem 0.85rem;
  border-radius: 3px;
  display: flex;
  flex-direction: column;
  gap: 0.45rem;
}
.dt-card--q1 { --card-accent: #facc15; }
.dt-card--q2 { --card-accent: #fb923c; }
.dt-card--q3 { --card-accent: var(--red); }
.dt-card--q4 {
  --card-accent: var(--accent-purple);
  opacity: 0.5;
  background: linear-gradient(180deg, rgba(20,20,24,0.4), rgba(10,10,12,0.6));
}
.dt-card--q4 .dt-card-body { color: #8a8478; }
.dt-card--q4 .dt-card-body b { color: #b9b3a9; }
.dt-card-await {
  font-family: var(--font-mono);
  font-size: 0.55rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--accent-purple);
  margin-top: 0.1rem;
  opacity: 0.75;
}
.dt-card-head {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
}
.dt-card-num {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 1.5rem;
  color: var(--card-accent, var(--red));
  line-height: 1;
}
.dt-card-tag {
  font-family: var(--font-mono);
  font-size: 0.58rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--dim);
}
.dt-card-body {
  font-family: var(--font-mono);
  font-size: 0.85rem;
  line-height: 1.45;
  color: #c8c2b6;
}
.dt-card-body b {
  color: var(--bone);
  font-weight: 700;
}
.dt-tail {
  display: inline-flex;
  align-items: center;
  gap: 0.55rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1rem;
  color: #b9b3a9;
  margin-top: 0.2rem;
}
.dt-tail-mark { color: var(--red); font-size: 0.7rem; }
</style>

<!--
"Eu chamo isso de Teste da Deleção. É simples: pega uma funcionalidade — tipo processamento de pagamento — e imagina que deleta TUDO que é dela. 3 perguntas. Se alguma falha, você tem um problema de boundary."

[click] "Vamos rodar esse teste no nosso legadão e ver o que acontece?"
-->
