<!--
  comunidades-modular — "as comunidades que eu faço parte hoje".

  A 4-card brutalist grid (He4rt · PHPSP · Filament BR · 3Pontos), each card
  color-coded with one accent from the deck palette. Replaces the earlier
  he4rt-solo slide. Self-contained (inline bg/meta/footer + shared keyframes)
  so it renders identically to whoami-modular without prop wiring.
-->
<template>
  <div class="comu-modular">
    <div class="bg-grid" />
    <div class="bg-vignette" />
    <div class="bg-grain" />

    <!-- top metadata bar -->
    <div class="meta-bar">
      <span class="meta-tag">N°<b>03</b></span>
      <span class="meta-pipe">│</span>
      <span class="meta-track">COMUNIDADES · <b>onde eu troco ideia</b></span>
      <span class="meta-fill" />
      <span class="meta-handle">◆ @danielhe4rt</span>
    </div>

    <!-- header band: title + subtitle -->
    <div class="head">
      <div class="title-block">
        <div class="title-eyebrow">
          <span class="eyebrow-mark">◆</span>
          <span>antes de começar</span>
        </div>
        <h1 class="title">
          <span class="title-line title-line--outline">ONDE EU</span>
          <span class="title-line title-line--solid">
            TROCO IDEIA<span class="title-dot">.</span>
          </span>
        </h1>
      </div>

      <div class="head-note">
        <span class="head-rule" />
        <p class="head-sub">
          as <b>4 comunidades</b> que eu<br>
          <span class="g g-a">faço parte</span> hoje.
        </p>
      </div>
    </div>

    <!-- 4-card grid -->
    <div class="cards">

      <!-- 01 · He4rt -->
      <div class="card card--purple">
        <div class="card-top">
          <span class="card-idx">01</span>
          <span class="card-tag">fundador</span>
        </div>
        <div class="card-glyph">
          <mdi-heart class="glyph-icon" />
        </div>
        <div class="card-name">He4rt Developers</div>
        <p class="card-desc">comunidade <b>open source</b> de devs br — estudo, mentoria e projeto juntos.</p>
        <div class="card-foot">
          <div class="card-meta">+20mil no discord · since 2018</div>
          <div class="card-link">
            <mdi-discord class="link-icon" />
            <span>discord.gg/<b>he4rt</b></span>
          </div>
        </div>
      </div>

      <!-- 02 · PHPSP -->
      <div class="card card--blue">
        <div class="card-top">
          <span class="card-idx">02</span>
          <span class="card-tag">membro</span>
        </div>
        <div class="card-glyph">
          <mdi-elephant class="glyph-icon" />
        </div>
        <div class="card-name">PHPSP</div>
        <p class="card-desc">grupo de devs <b>PHP</b> de são paulo — <b>pub</b> &amp; <b>talks</b> presenciais.</p>
        <div class="card-foot">
          <div class="card-meta">+10 anos · slack +2mil</div>
          <div class="card-link">
            <mdi-web class="link-icon" />
            <span><b>phpsp.org.br</b></span>
          </div>
        </div>
      </div>

      <!-- 03 · Filament BR -->
      <div class="card card--orange">
        <div class="card-top">
          <span class="card-idx">03</span>
          <span class="card-tag">membro</span>
        </div>
        <div class="card-glyph">
          <mdi-fire class="glyph-icon" />
        </div>
        <div class="card-name">Filament BR</div>
        <p class="card-desc">comunidade br de <b>FilamentPHP</b> — conteúdo, tutoriais e papo no discord.</p>
        <div class="card-foot">
          <div class="card-meta">filament ambassador</div>
          <div class="card-link">
            <mdi-web class="link-icon" />
            <span><b>filament.dev.br</b></span>
          </div>
        </div>
      </div>

      <!-- 04 · 3Pontos -->
      <div class="card card--silver">
        <div class="card-top">
          <span class="card-idx">04</span>
          <span class="card-tag">tech lead</span>
        </div>
        <div class="card-glyph">
          <mdi-dots-horizontal class="glyph-icon" />
        </div>
        <div class="card-name">3Pontos</div>
        <p class="card-desc">comunidade <b>+ banco de talentos</b> tech — onde eu trabalho hoje.</p>
        <div class="card-foot">
          <div class="card-meta">talento br pro mundo</div>
          <div class="card-link">
            <mdi-rocket-launch class="link-icon" />
            <span>recrutamento.<b>3pontos.com</b></span>
          </div>
        </div>
      </div>

    </div>

    <!-- footer -->
    <div class="footer-bar footer-bar--right-only">
      <div class="footer-right">
        <span class="prompt-label">press</span>
        <kbd class="key">SPACE</kbd>
        <span class="next-label">→ a 3pontos tá de olho</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.comu-modular {
  position: absolute;
  inset: 0;
  padding: 2.4rem 2.6rem 2rem;
  background: var(--ink, #0a0a0b);
  color: var(--bone, #f5f1ea);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  font-family: var(--font-mono, 'JetBrains Mono', ui-monospace, monospace);

  --red: #ff2d20;
  --bone: #f5f1ea;
  --ink: #0a0a0b;
  --dim: #6b6b6b;
  --accent-green:  #6ee7a1;
  --accent-blue:   #60a5fa;
  --accent-purple: #c084fc;
  --accent-orange: #ffa53a;
}

/* -------- backgrounds -------- */
.bg-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(to right, rgba(255, 255, 255, 0.025) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(255, 255, 255, 0.025) 1px, transparent 1px);
  background-size: 56px 56px;
  -webkit-mask-image: radial-gradient(ellipse at 50% 50%, #000 35%, transparent 85%);
  mask-image: radial-gradient(ellipse at 50% 50%, #000 35%, transparent 85%);
  pointer-events: none;
}
.bg-vignette {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(800px 600px at 85% 90%, rgba(255, 45, 32, 0.10), transparent 60%),
    radial-gradient(600px 400px at 10% 0%, rgba(255, 255, 255, 0.04), transparent 70%);
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

/* -------- header band -------- */
.head {
  position: relative;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 2rem;
  padding: 1.1rem 0 0.4rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.15s;
}
.title-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-serif, 'Instrument Serif', serif);
  font-style: italic;
  font-size: 0.92rem;
  color: #b9b3a9;
  margin-bottom: 0.2rem;
  letter-spacing: 0.01em;
}
.eyebrow-mark { color: var(--red); font-size: 0.6rem; }

.title {
  font-family: var(--font-display, 'Big Shoulders Display', 'Archivo Black', sans-serif);
  font-weight: 900;
  margin: 0;
  display: flex;
  align-items: baseline;
  gap: 0.9rem;
  line-height: 0.9;
}
.title-line { display: block; white-space: nowrap; }
.title-line--outline {
  color: transparent;
  -webkit-text-stroke: 1.6px var(--bone);
  opacity: 0.92;
  font-size: 2.7rem;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.25s;
}
.title-line--solid {
  color: var(--bone);
  font-size: 3.3rem;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.4s;
}
.title-dot {
  color: var(--red);
  text-shadow: 0 0 22px rgba(255, 45, 32, 0.45);
}

.head-note {
  display: flex;
  align-items: center;
  gap: 0.9rem;
  padding-bottom: 0.25rem;
}
.head-rule {
  width: 2px;
  height: 2.6rem;
  background: linear-gradient(to bottom, var(--red), transparent);
}
.head-sub {
  margin: 0;
  font-family: var(--font-serif, 'Instrument Serif', serif);
  font-style: italic;
  font-size: 1.05rem;
  line-height: 1.25;
  color: #b9b3a9;
  text-align: right;
}
.head-sub b {
  font-family: var(--font-mono, 'JetBrains Mono', monospace);
  font-style: normal;
  font-weight: 700;
  color: var(--bone);
  font-size: 0.88em;
}

/* -------- cards grid -------- */
.cards {
  position: relative;
  flex: 1;
  min-height: 0;
  margin-top: 0.7rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1rem;
}

.card {
  position: relative;
  display: flex;
  flex-direction: column;
  padding: 0.95rem 1rem 0.9rem;
  border-radius: 4px;
  border-left: 3px solid var(--accent, rgba(255, 255, 255, 0.18));
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  border-right: 1px solid rgba(255, 255, 255, 0.05);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  background:
    linear-gradient(180deg, rgba(20, 20, 24, 0.6), rgba(10, 10, 12, 0.8)),
    radial-gradient(circle at 100% 0%, var(--accent-glow, transparent), transparent 65%);
  box-shadow: 0 16px 34px -22px rgba(0, 0, 0, 0.7);
  overflow: hidden;
  animation: row-in 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.card::before {
  content: "";
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-image: repeating-linear-gradient(0deg, transparent 0 3px, rgba(0, 0, 0, 0.16) 3px 4px);
  mix-blend-mode: multiply;
  opacity: 0.25;
}
/* He4rt → roxo profundo · 3Pontos → prata · Filament → âmbar · PHPSP → azul */
.card--purple  { --accent: #8b5cf6;             --accent-glow: rgba(139, 92, 246, 0.15); }
.card--blue    { --accent: var(--accent-blue);  --accent-glow: rgba(96, 165, 250, 0.12); }
.card--orange  { --accent: var(--accent-orange); --accent-glow: rgba(255, 165, 58, 0.12); }
.card--silver  { --accent: #cfd4dd;             --accent-glow: rgba(207, 212, 221, 0.13); }
.card:nth-child(1) { animation-delay: 0.5s; }
.card:nth-child(2) { animation-delay: 0.62s; }
.card:nth-child(3) { animation-delay: 0.74s; }
.card:nth-child(4) { animation-delay: 0.86s; }

.card-top {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.card-idx {
  font-family: var(--font-display, 'Big Shoulders Display', sans-serif);
  font-weight: 900;
  font-size: 1.05rem;
  color: var(--accent);
  letter-spacing: 0.04em;
}
.card-tag {
  font-size: 0.56rem;
  font-weight: 700;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--bone);
  border: 1px solid var(--accent);
  border-radius: 2px;
  padding: 0.12rem 0.4rem;
  background: var(--accent-glow);
}

.card-glyph {
  position: relative;
  margin: 0.7rem 0 0.55rem;
  width: 2.9rem;
  height: 2.9rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1.5px solid var(--accent);
  border-radius: 3px;
  background: rgba(10, 10, 12, 0.6);
  clip-path: polygon(0 0, 100% 0, 100% calc(100% - 9px), calc(100% - 9px) 100%, 0 100%);
}
.glyph-icon { font-size: 1.5rem; color: var(--accent); }

.card-name {
  position: relative;
  font-family: var(--font-display, 'Big Shoulders Display', sans-serif);
  font-weight: 900;
  font-size: 1.32rem;
  line-height: 1;
  color: var(--bone);
  letter-spacing: 0.005em;
}
.card-desc {
  position: relative;
  margin: 0.4rem 0 0;
  font-size: 0.72rem;
  line-height: 1.45;
  color: #b6b0a4;
}
.card-desc b { color: var(--bone); font-weight: 700; }

.card-foot {
  position: relative;
  margin-top: auto;
  padding-top: 0.6rem;
}
.card-meta {
  font-size: 0.56rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--dim);
  margin-bottom: 0.35rem;
}
.card-link {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  font-size: 0.72rem;
  color: #d6d0c4;
  padding-top: 0.4rem;
  border-top: 1px solid rgba(255, 255, 255, 0.07);
  width: 100%;
}
.card-link b { color: var(--bone); font-weight: 700; }
.link-icon { font-size: 0.95rem; color: var(--accent); flex: none; }

/* -------- footer -------- */
.footer-bar {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.85rem;
  padding-top: 0.55rem;
  border-top: 1px solid #1c1c1f;
  font-size: 0.66rem;
  letter-spacing: 0.12em;
  animation: fade-in 0.55s ease both;
  animation-delay: 1.1s;
}
.footer-bar--right-only { justify-content: flex-end; }
.footer-right {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--dim);
  text-transform: uppercase;
}
.prompt-label { letter-spacing: 0.15em; }
.next-label {
  color: var(--bone);
  text-transform: lowercase;
  letter-spacing: 0.04em;
  font-style: italic;
  font-family: var(--font-serif, 'Instrument Serif', serif);
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

/* -------- glitch (shared vocab) -------- */
.g { display: inline-block; will-change: filter, transform, opacity; }
.g-a { animation: g-a 6.5s infinite both; }

/* -------- keyframes -------- */
@keyframes fade-in { from { opacity: 0; } to { opacity: 1; } }
@keyframes slide-up {
  from { opacity: 0; transform: translateY(14px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes title-wipe {
  from { opacity: 0; clip-path: inset(0 100% 0 0); }
  to   { opacity: 1; clip-path: inset(0 0 0 0); }
}
@keyframes row-in {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes g-a {
  0%, 90%   { filter: none; transform: none; color: inherit; opacity: 1; }
  91%       { filter: blur(1.4px); transform: translateX(2px); opacity: 0.55; color: var(--red); }
  92%       { filter: blur(0.4px); transform: translateX(-3px); opacity: 0.8; }
  93%       { filter: blur(0.9px) hue-rotate(40deg); transform: translateX(1px); }
  94%, 100% { filter: none; transform: none; opacity: 1; color: inherit; }
}
</style>
