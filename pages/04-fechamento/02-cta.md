---
layout: brutalist-base
metaNumber: "19"
metaSection: "FECHAMENTO"
metaSubtitle: "obrigado"
contentAlign: "between"
vignettePos: tr
---

<div class="cta-top">
  <div class="cta-eyebrow">
    <span class="eyebrow-mark">◆</span>
    <span>é isso. valeu pela atenção.</span>
  </div>

  <h1 class="cta-title">
    OBRIGADO<span class="cta-period g g-a">.</span>
  </h1>

  <div class="cta-sub">
    módulo a módulo. <span class="cta-sub-em">boundary a boundary.</span>
  </div>

  <div class="cta-rule">
    <span class="cta-rule-block" />
    <span class="cta-rule-line" />
    <span class="cta-rule-tail">se quiser continuar a conversa</span>
  </div>
</div>

<div class="cta-chips">

  <div class="cta-chip cta-chip--heart">
    <div class="chip-header">
      <span class="chip-mark">♥</span>
      <span class="chip-tag">comunidade</span>
    </div>
    <div class="chip-title">He4rt Developers</div>
    <div class="chip-url">heartdevs.com</div>
    <div class="chip-body">comunidade de devs brasileiros · open source · mentoria</div>
  </div>

  <div class="cta-chip cta-chip--twitch">
    <div class="chip-header">
      <span class="chip-mark">▶</span>
      <span class="chip-tag">livecoding</span>
    </div>
    <div class="chip-title">Twitch</div>
    <div class="chip-url">twitch.tv/danielhe4rt</div>
    <div class="chip-body">live coding · perguntas · café · <span class="g g-c">6 anos</span> no ar</div>
  </div>

</div>

<div class="cta-footer">
  <div class="footer-id">
    <div class="footer-name">DANIEL REIS · <span class="footer-handle">@danielhe4rt</span></div>
    <div class="footer-sub">tech lead @ 3pontos · senior swe @ scopeyonsite</div>
  </div>
  <div class="footer-cursor">
    <span class="cursor">▮</span>
  </div>
</div>

<style>
.brutalist-content {
  padding-top: 0;
  justify-content: space-between;
}

.cta-top {
  padding-top: 0.3rem;
}

.cta-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.05rem;
  color: #b9b3a9;
  margin-bottom: 0.2rem;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.2s;
}
.cta-eyebrow .eyebrow-mark { color: var(--red); font-size: 0.75rem; transform: translateY(-1px); }

.cta-title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 8.4rem;
  line-height: 0.9;
  letter-spacing: -0.015em;
  margin: 0.05rem 0 0.55rem;
  color: var(--bone);
  animation: title-wipe 0.85s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.35s;
}
.cta-period {
  color: var(--red);
  display: inline-block;
  text-shadow: 0 0 28px rgba(255, 45, 32, 0.5);
  margin-left: 0.03em;
}

.cta-sub {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.55rem;
  color: #b9b3a9;
  margin-bottom: 0.95rem;
  letter-spacing: 0.005em;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.65s;
}
.cta-sub-em { color: var(--bone); }

.cta-rule {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin: 0.2rem 0 0;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.85s;
}
.cta-rule-block {
  width: 46px;
  height: 11px;
  background: var(--red);
  box-shadow: 0 0 22px rgba(255, 45, 32, 0.4);
}
.cta-rule-line {
  flex: 0 0 180px;
  height: 2px;
  background: linear-gradient(to right, var(--red), transparent);
}
.cta-rule-tail {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--dim);
}

/* -------- chips -------- */
.cta-chips {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.3rem;
  margin: 0.7rem 0 0.4rem;
}

.cta-chip {
  position: relative;
  padding: 1.05rem 1.2rem 1.05rem;
  border-radius: 4px;
  border: 1px solid var(--chip-color, var(--frame));
  background: linear-gradient(180deg, rgba(20,20,24,0.6), rgba(10,10,12,0.78));
  box-shadow:
    0 0 0 1px rgba(0,0,0,0.4) inset,
    var(--chip-shadow-x, 6px) var(--chip-shadow-y, 6px) 0 -2px var(--chip-shadow, rgba(255,45,32,0.35));
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.cta-chip::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 4px;
  pointer-events: none;
  background: radial-gradient(ellipse at 0% 0%, var(--chip-glow, rgba(255,45,32,0.1)), transparent 55%);
}
.cta-chip--heart {
  --chip-color: var(--red);
  --chip-glow: rgba(255, 45, 32, 0.12);
  --chip-shadow: rgba(255, 45, 32, 0.4);
  animation-delay: 1.05s;
}
.cta-chip--twitch {
  --chip-color: var(--accent-purple);
  --chip-glow: rgba(192, 132, 252, 0.12);
  --chip-shadow: rgba(192, 132, 252, 0.4);
  animation-delay: 1.2s;
}

.chip-header {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  margin-bottom: 0.45rem;
}
.chip-mark {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 26px;
  height: 26px;
  border-radius: 3px;
  background: var(--chip-color);
  color: var(--ink);
  font-size: 0.95rem;
  font-weight: 700;
  box-shadow: 0 0 18px var(--chip-glow);
}
.chip-tag {
  font-family: var(--font-mono);
  font-size: 0.62rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  font-weight: 700;
  color: var(--chip-color);
}

.chip-title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 2rem;
  line-height: 1;
  letter-spacing: -0.005em;
  color: var(--bone);
  margin-bottom: 0.35rem;
}

.chip-url {
  font-family: var(--font-mono);
  font-size: 0.85rem;
  letter-spacing: 0.04em;
  color: var(--chip-color);
  font-weight: 500;
  margin-bottom: 0.55rem;
  padding-bottom: 0.45rem;
  border-bottom: 1px solid var(--rule);
}

.chip-body {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1rem;
  line-height: 1.4;
  color: #b9b3a9;
}

/* -------- footer (identity allowed here) -------- */
.cta-footer {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-top: 0.4rem;
  padding-top: 0.7rem;
  border-top: 1px solid var(--rule);
  font-family: var(--font-mono);
  animation: fade-in 0.6s ease both;
  animation-delay: 1.4s;
}
.footer-name {
  font-size: 0.82rem;
  font-weight: 700;
  letter-spacing: 0.22em;
  color: var(--bone);
}
.footer-handle {
  color: var(--red);
  letter-spacing: 0.1em;
}
.footer-sub {
  margin-top: 0.2rem;
  font-size: 0.68rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--dim);
}
.cursor {
  color: var(--red);
  font-size: 1.1rem;
  animation: cursor-blink 1.1s steps(1) infinite;
}
</style>

<!--
"E é isso, gente. 40 minutos. Uma história. Quatro convenções. Um Teste da Deleção."

[pausa]

"Lembra de uma coisa: módulo a módulo. Boundary a boundary. Você não precisa modularizar o sistema todo amanhã. Pega um pedaço que dói — aquele canto do código que ninguém quer mexer — e extrai SÓ ele. Roda o Teste da Deleção. Se passar, pega o próximo."

"Se você quiser continuar a conversa, dois lugares:"

"Primeiro — He4rt Developers, heartdevs.com. É a comunidade de devs brasileiros que eu ajudo a tocar. Mentoria, open source, gente fazendo coisa. Entra lá."

"Segundo — Twitch, twitch.tv/danielhe4rt. Faço livecoding há 6 anos, manda pergunta lá, manda issue no github, tudo bem. Café tá quente."

[pausa]

"Obrigado pelo tempo de vocês. Bom evento!"

[se houver tempo de Q&A — fica nesse slide com o cursor piscando.]
-->
