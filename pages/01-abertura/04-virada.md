---
layout: statement-modular
metaNumber: "08"
metaSection: "ABERTURA"
metaSubtitle: "a virada"
eyebrow: "e aí?"
accent: "?"
---

# E aí? O que faz?

<div class="virada-list">

<v-clicks>

<div class="vl-row">
  <span class="vl-mark">✓</span>
  <span class="vl-text">desistir.</span>
  <span class="vl-meta">— por uns 3 meses.</span>
</div>

<div class="vl-row">
  <span class="vl-mark">✓</span>
  <span class="vl-text">trocar de empresa.</span>
  <span class="vl-meta">— mesmo legado, CNPJ diferente.</span>
</div>

<div class="vl-row">
  <span class="vl-mark">✓</span>
  <span class="vl-text">reescrever do zero.</span>
  <span class="vl-meta">— 6 meses, 0 entregas, stakeholder cancelou.</span>
</div>

<div class="vl-row">
  <span class="vl-mark">✓</span>
  <span class="vl-text">fingir que não vi.</span>
  <span class="vl-meta">— funciona até a próxima sprint.</span>
</div>

</v-clicks>

<v-click>

<div class="vl-rule">
  <span>nada disso resolve.</span>
</div>

</v-click>

<v-click>

<div class="vl-final">
  <div class="vl-final-line">
    <span class="vl-mark vl-mark--win">✓</span>
    <span class="vl-final-text">ISOLAR EM <span class="g g-a">PEDAÇOS</span>.</span>
  </div>
  <p class="vl-final-sub">
    <strong>sem refatorar do zero</strong> — só extraindo o que já estava lá.
  </p>
</div>

</v-click>

</div>

<style>
.virada-list {
  margin-top: 1.4rem;
  font-family: var(--font-mono);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
}

/* tried-and-failed rows */
.vl-row {
  display: flex;
  align-items: baseline;
  gap: 1.1rem;
  font-size: 1.1rem;
  color: var(--dim);
  letter-spacing: 0.005em;
}
.vl-mark {
  color: var(--accent-orange);
  font-weight: 700;
  display: inline-block;
  min-width: 1.4rem;
  text-align: center;
}
.vl-text {
  font-weight: 500;
  color: #9a9a9a;
}
.vl-meta {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.95rem;
  color: #6b6b6b;
}

/* dividing rule */
.vl-rule {
  margin: 0.7rem 0 0.3rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.05rem;
  color: #6b6b6b;
  letter-spacing: 0.04em;
  display: flex;
  align-items: center;
  gap: 0.8rem;
  max-width: 70%;
}
.vl-rule::before,
.vl-rule::after {
  content: '';
  flex: 1;
  height: 1px;
  background: rgba(255,255,255,0.10);
}

/* the answer */
.vl-final {
  margin-top: 0.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
.vl-final-line {
  display: flex;
  align-items: baseline;
  gap: 1.1rem;
}
.vl-final .vl-mark--win {
  color: var(--accent-green);
  font-size: 1.5rem;
}
.vl-final-text {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 3.1rem;
  letter-spacing: -0.01em;
  line-height: 0.95;
  color: var(--bone);
  text-transform: uppercase;
}
.vl-final-text :deep(.g) {
  color: var(--accent-green);
  display: inline-block;
}
.vl-final-sub {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.15rem;
  color: #b9b3a9;
  margin: 0.25rem 0 0 2.5rem;
  max-width: 70%;
  line-height: 1.4;
}
.vl-final-sub strong {
  font-style: normal;
  font-family: var(--font-mono);
  color: var(--accent-green);
  font-weight: 700;
  letter-spacing: 0.01em;
}
</style>

<!--
"Beleza. Você se deparou com esse legadão. E aí? O que faz?"

[pausa dramática]

[click 1] "Já desisti. Saí do projeto por uns 3 meses. Voltei. Mesmo problema, mesma pasta app/, mesmo 487 arquivos."

[click 2] "Já troquei de empresa. Adivinha? Mesmo legado. CNPJ diferente."

[click 3] "Já reescrevi do zero. 6 meses fechado num branch. 0 entregas. Stakeholder cancelou o projeto antes do release."

[click 4] "Já fingi que não vi. Empurrei pra frente. Funciona — até a próxima sprint."

[click 5 — pausa] "Nada disso resolve."

[click 6] "O que funcionou foi isso aqui: ISOLAR EM PEDAÇOS. Pega o problema, quebra em boundaries, ataca um por vez. SEM refatorar do zero. Só extraindo o que JÁ estava lá. O código tá lá. As responsabilidades tão lá. Só tão na pasta errada."

[transição] "E pra extrair, eu precisei de um método. Um teste pra saber onde corta. Vou te apresentar."
-->
