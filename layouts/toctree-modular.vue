<template>
  <div class="toctree-modular">
    <div class="bg-grid" />
    <div class="bg-vignette" />
    <div class="bg-grain" />

    <!-- meta bar -->
    <div class="meta-bar">
      <span class="meta-tag">N°<b>03</b></span>
      <span class="meta-pipe">│</span>
      <span class="meta-track">AGENDA · <b>roadmap</b></span>
      <span class="meta-fill" />
      <span class="meta-handle">◆ 40min total</span>
    </div>

    <!-- title -->
    <div class="title-block">
      <div class="title-left">
        <div class="title-eyebrow">
          <span class="eyebrow-mark">◆</span>
          <span>antes de mergulhar</span>
        </div>
        <h1 class="title">
          <span class="title-line title-line--outline">QUATRO</span>
          <span class="title-line title-line--solid">
            ATOS<span class="title-q">.</span>
          </span>
        </h1>
        <div class="title-rule">
          <span class="rule-block" />
          <span class="rule-line" />
          <span class="rule-tail">talk · roadmap</span>
        </div>
      </div>

      <div class="title-right">
        <div class="title-tagline">
          <span class="tagline-prompt">$</span>
          <span class="tagline-cmd">cat <span class="tagline-arg">itinerary.md</span></span>
        </div>
        <div class="title-summary">
          <span class="summary-num">4</span>
          <span class="summary-label">atos</span>
          <span class="summary-sep">·</span>
          <span class="summary-num">40</span>
          <span class="summary-label">minutos</span>
          <span class="summary-sep">·</span>
          <span class="summary-num">1</span>
          <span class="summary-label">viagem de extração</span>
        </div>
      </div>
    </div>

    <!-- 4 acts: TOC list -->
    <ol class="acts">
      <li class="act" style="--act-delay: 0.4s">
        <span class="act-num">01</span>
        <span class="act-title">O LEGADÃO</span>
        <span class="act-leader" />
        <span class="act-eta">~5 min</span>
      </li>
      <li class="act" style="--act-delay: 0.5s">
        <span class="act-num">02</span>
        <span class="act-title">EXTRAÇÃO</span>
        <span class="act-leader" />
        <span class="act-eta">~12 min</span>
      </li>
      <li class="act" style="--act-delay: 0.6s">
        <span class="act-num">03</span>
        <span class="act-title">IMPLEMENTAÇÃO</span>
        <span class="act-leader" />
        <span class="act-eta">~15 min</span>
      </li>
      <li class="act act--final" style="--act-delay: 0.7s">
        <span class="act-num">04</span>
        <span class="act-title">FECHAMENTO</span>
        <span class="act-leader" />
        <span class="act-eta">~8 min</span>
      </li>
    </ol>

    <!-- footer -->
    <div class="footer-bar">
      <div class="footer-right">
        <span class="prompt-label">press</span>
        <kbd class="key">SPACE</kbd>
        <span class="next-label">→ ato 01</span>
      </div>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@500;700;900&family=JetBrains+Mono:wght@400;500;700&family=Instrument+Serif:ital@0;1&display=swap');
</style>

<style scoped>
.toctree-modular {
  position: absolute;
  inset: 0;
  padding: 2.4rem 2.6rem 2rem;
  background: #0a0a0b;
  color: #f5f1ea;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  font-family: 'JetBrains Mono', ui-monospace, monospace;

  --red: #ff2d20;
  --red-deep: #c4150c;
  --bone: #f5f1ea;
  --ink: #0a0a0b;
  --dim: #6b6b6b;
}

/* -------- backgrounds -------- */
.bg-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(to right, rgba(255, 255, 255, 0.025) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(255, 255, 255, 0.025) 1px, transparent 1px);
  background-size: 56px 56px;
  -webkit-mask-image: radial-gradient(ellipse at 50% 50%, #000 30%, transparent 80%);
  mask-image: radial-gradient(ellipse at 50% 50%, #000 30%, transparent 80%);
  pointer-events: none;
}
.bg-vignette {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(900px 500px at 100% 50%, rgba(255, 45, 32, 0.10), transparent 60%),
    radial-gradient(600px 400px at 0% 0%, rgba(255, 255, 255, 0.04), transparent 70%);
  pointer-events: none;
}
.bg-grain {
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='160' height='160'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='2' stitchTiles='stitch'/><feColorMatrix values='0 0 0 0 1  0 0 0 0 1  0 0 0 0 1  0 0 0 .07 0'/></filter><rect width='100%' height='100%' filter='url(%23n)'/></svg>");
  mix-blend-mode: overlay;
  opacity: 0.35;
  pointer-events: none;
}

/* -------- meta bar -------- */
.meta-bar {
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 0.68rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--dim);
  animation: fade-in 0.6s ease both;
}
.meta-tag b { color: var(--red); font-weight: 700; }
.meta-pipe { color: #2a2a2c; }
.meta-track b { color: var(--bone); font-weight: 700; }
.meta-fill {
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, transparent, #2a2a2c 30%, #2a2a2c 70%, transparent);
  margin: 0 0.75rem;
}
.meta-handle { color: var(--bone); font-weight: 700; letter-spacing: 0.1em; }
.meta-handle::first-letter { color: var(--red); }

/* -------- title block (two-column header) -------- */
.title-block {
  position: relative;
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 2rem;
  align-items: end;
  margin-top: 0.8rem;
  padding-bottom: 0.9rem;
  border-bottom: 1px solid #1c1c1f;
}

.title-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  font-size: 0.92rem;
  color: #b9b3a9;
  margin-bottom: 0.1rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.2s;
}
.eyebrow-mark { color: var(--red); font-size: 0.6rem; }

.title {
  font-family: 'Big Shoulders Display', sans-serif;
  font-weight: 900;
  font-size: 3.8rem;
  line-height: 0.9;
  margin: 0;
  display: flex;
  align-items: baseline;
  gap: 0.8rem;
}
.title-line--outline {
  color: transparent;
  -webkit-text-stroke: 1.5px var(--bone);
  opacity: 0.92;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.3s;
}
.title-line--solid {
  color: var(--bone);
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.45s;
}
.title-q {
  color: var(--red);
  text-shadow: 0 0 22px rgba(255, 45, 32, 0.45);
  margin-left: 0.04em;
}

.title-rule {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  margin-top: 0.5rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.55s;
}
.rule-block {
  width: 38px;
  height: 9px;
  background: var(--red);
  box-shadow: 0 0 18px rgba(255, 45, 32, 0.35);
}
.rule-line {
  flex: 0 0 90px;
  height: 2px;
  background: linear-gradient(to right, var(--red), transparent);
}
.rule-tail {
  font-size: 0.6rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--dim);
}

.title-right {
  text-align: right;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.3s;
}
.title-tagline {
  font-size: 0.78rem;
  color: var(--bone);
  margin-bottom: 0.45rem;
}
.tagline-prompt { color: var(--red); font-weight: 700; margin-right: 0.35rem; }
.tagline-cmd { color: var(--bone); }
.tagline-arg { color: #c084fc; }

.title-summary {
  display: inline-flex;
  align-items: baseline;
  gap: 0.4rem;
  padding: 0.4rem 0.7rem;
  border: 1px solid #2a2a2c;
  border-radius: 3px;
  background: rgba(20, 20, 24, 0.4);
  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--dim);
}
.summary-num {
  font-family: 'Big Shoulders Display', sans-serif;
  font-weight: 900;
  font-size: 1.4rem;
  color: var(--red);
  line-height: 1;
}
.summary-label { color: var(--bone); }
.summary-sep { color: var(--dim); opacity: 0.6; }

/* -------- acts TOC list -------- */
.acts {
  position: relative;
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 0.4rem;
  list-style: none;
  padding: 0;
  margin: 1rem 0 0;
  min-height: 0;
}

.act {
  display: grid;
  grid-template-columns: 4.6rem auto 1fr auto;
  align-items: baseline;
  gap: 0.9rem;
  padding: 0.35rem 0.2rem 0.45rem;
  border-bottom: 1px solid #1c1c1f;
  animation: act-in 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: var(--act-delay, 0.4s);
}

.act-num {
  font-family: 'Big Shoulders Display', sans-serif;
  font-weight: 900;
  font-size: 3rem;
  line-height: 0.85;
  color: var(--red);
  letter-spacing: -0.02em;
  text-shadow: 0 0 22px rgba(255, 45, 32, 0.35);
  font-variant-numeric: tabular-nums;
}

.act-title {
  font-family: 'JetBrains Mono', monospace;
  font-weight: 700;
  font-size: 1.4rem;
  letter-spacing: 0.04em;
  color: var(--bone);
}

.act-leader {
  align-self: end;
  height: 1.1rem;
  background-image: radial-gradient(circle, var(--dim) 1px, transparent 1.5px);
  background-size: 8px 100%;
  background-position: 0 1em;
  background-repeat: repeat-x;
  opacity: 0.45;
  transform: translateY(-3px);
}

.act-eta {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.85rem;
  letter-spacing: 0.06em;
  color: var(--dim);
  font-variant-numeric: tabular-nums;
}

.act--final .act-title { color: var(--red); }
.act--final .act-eta   { color: var(--bone); }
.act--final            { border-bottom-color: rgba(255, 45, 32, 0.35); }

/* -------- footer -------- */
.footer-bar {
  position: relative;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  margin-top: 0.8rem;
  padding-top: 0.55rem;
  border-top: 1px solid #1c1c1f;
  font-size: 0.66rem;
  letter-spacing: 0.12em;
  animation: fade-in 0.55s ease both;
  animation-delay: 1.05s;
}
.footer-right {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--dim);
  text-transform: uppercase;
}
.next-label {
  color: var(--bone);
  text-transform: lowercase;
  letter-spacing: 0.04em;
  font-style: italic;
  font-family: 'Instrument Serif', serif;
  font-size: 0.78rem;
}
.key {
  display: inline-block;
  padding: 0.2rem 0.5rem;
  border: 1px solid #3a3a3d;
  border-bottom-width: 3px;
  border-radius: 4px;
  color: var(--bone);
  background: rgba(21, 21, 24, 0.5);
  font-size: 0.62rem;
  letter-spacing: 0.15em;
}

/* -------- glitch flickers -------- */
.g { display: inline-block; will-change: filter, transform, opacity; }
.g-a { animation: g-a 6.5s infinite both; }
.g-b { animation: g-b 8s infinite both; animation-delay: -2.4s; }
.g-c { animation: g-c 7.2s infinite both; animation-delay: -4.1s; }

/* -------- keyframes -------- */
@keyframes fade-in {
  from { opacity: 0; }
  to   { opacity: 1; }
}
@keyframes slide-up {
  from { opacity: 0; transform: translateY(14px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes title-wipe {
  from { opacity: 0; clip-path: inset(0 100% 0 0); }
  to   { opacity: 1; clip-path: inset(0 0 0 0); }
}
@keyframes act-in {
  from { opacity: 0; transform: translateX(-12px); }
  to   { opacity: 1; transform: translateX(0); }
}

@keyframes g-a {
  0%, 90%   { filter: none; transform: none; color: inherit; opacity: 1; }
  91%       { filter: blur(1.4px); transform: translateX(2px); opacity: 0.55; color: var(--red); }
  92%       { filter: blur(0.4px); transform: translateX(-3px); opacity: 0.8; }
  93%       { filter: blur(0.9px) hue-rotate(40deg); transform: translateX(1px); }
  94%, 100% { filter: none; transform: none; opacity: 1; color: inherit; }
}
@keyframes g-b {
  0%, 84%   { filter: none; opacity: 1; transform: none; letter-spacing: 0; }
  85%       { filter: blur(0.6px); opacity: 0.4; transform: skewX(-4deg); letter-spacing: 0.04em; }
  86%       { filter: blur(1.2px); opacity: 0.7; transform: skewX(2deg) translateY(-1px); }
  87%       { filter: blur(0.3px); opacity: 0.9; transform: none; letter-spacing: 0.01em; }
  88%, 100% { filter: none; opacity: 1; transform: none; letter-spacing: 0; }
}
@keyframes g-c {
  0%, 78%   { filter: none; transform: none; color: inherit; }
  79%       { filter: blur(0.9px) hue-rotate(20deg); transform: translate(2px, 1px); color: #60a5fa; }
  80%       { filter: blur(1.6px); transform: translate(-3px, -1px); opacity: 0.5; }
  81%       { filter: blur(0.5px); transform: translate(1px, 0); color: #ffa53a; }
  82%, 100% { filter: none; transform: none; color: inherit; opacity: 1; }
}
</style>
