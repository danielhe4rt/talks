<!--
  obrigado-modular — closing "thank you" screen in the whoami visual language
  (terminal + glitchy avatar + social pills) PLUS the 3Pontos recruitment QR
  on the same screen.

  Self-contained (inline bg/meta/avatar/terminal/qr + shared keyframes), like
  whoami-modular.vue and recruit-modular.vue, so it renders identically without
  prop wiring. QR points to recrutamento.3pontos.com (public/images/recruit-qr.png).
-->
<template>
  <div class="obrigado-modular">
    <div class="bg-grid" />
    <div class="bg-vignette" />
    <div class="bg-grain" />

    <!-- top metadata bar -->
    <div class="meta-bar">
      <span class="meta-tag">N°<b>19</b></span>
      <span class="meta-pipe">│</span>
      <span class="meta-track">FECHAMENTO · <b>obrigado</b></span>
      <span class="meta-fill" />
      <span class="meta-handle">◆ @danielhe4rt</span>
    </div>

    <!-- header -->
    <div class="ob-head">
      <div class="ob-head-left">
        <div class="ob-eyebrow">
          <span class="eyebrow-mark">◆</span>
          <span>é isso. valeu pela atenção.</span>
        </div>
        <h1 class="ob-title">
          OBRIGADO<span class="ob-period g g-a">.</span>
        </h1>
      </div>
      <div class="ob-sub">
        módulo a módulo.<br>
        <span class="ob-sub-em">boundary a boundary.</span>
      </div>
    </div>

    <!-- body: avatar · terminal · qr -->
    <div class="ob-body">

      <!-- avatar -->
      <div class="avatar-col">
        <div class="avatar-frame">
          <img class="avatar-img" src="https://github.com/danielhe4rt.png" alt="Daniel He4rt" />
          <div class="avatar-scanlines" />
          <div class="avatar-glitch-overlay" />
          <div class="avatar-corner avatar-corner--tl">★ FIM</div>
          <div class="avatar-corner avatar-corner--br">@danielhe4rt</div>
        </div>
        <div class="avatar-cap">
          <span class="cap-name">DANIEL REIS</span>
          <span class="cap-role">tech lead @ 3pontos</span>
        </div>
      </div>

      <!-- terminal: continue a conversa -->
      <div class="terminal">
        <div class="term-prompt">
          <span class="term-user">daniel</span><span class="term-at">@</span><span class="term-host">he4rt</span>
          <span class="term-sep">:</span>
          <span class="term-path">~</span>
          <span class="term-sep">$</span>
          <span class="term-cmd">./continua_a_conversa.sh</span>
          <span class="term-cursor">▮</span>
        </div>

        <div class="term-rule" />

        <div class="term-rows">
          <div class="term-row">
            <span class="term-key">comunidade</span>
            <span class="term-arrow">→</span>
            <span class="term-value">
              <mdi-heart class="term-icon term-icon--red" />
              <b>heartdevs.com</b>
              <span class="term-tag term-tag--red">entra aí</span>
            </span>
          </div>

          <div class="term-row">
            <span class="term-key">livecoding</span>
            <span class="term-arrow">→</span>
            <span class="term-value">
              <mdi-twitch class="term-icon term-icon--purple" />
              twitch.tv/<b>danielhe4rt</b>
              <span class="term-tag">6 anos no ar</span>
            </span>
          </div>

          <div class="term-row">
            <span class="term-key">código</span>
            <span class="term-arrow">→</span>
            <span class="term-value">
              <mdi-github class="term-icon" />
              github.com/<b>danielhe4rt</b>
            </span>
          </div>
        </div>

        <div class="term-rule" />

        <div class="term-socials">
          <span class="socials-key">socials</span>
          <span class="term-arrow">→</span>
          <span class="socials-list">
            <span class="social-pill"><mdi-github class="social-icon social-icon--gh" /><b>github</b></span>
            <span class="social-dot">·</span>
            <span class="social-pill"><mdi-instagram class="social-icon social-icon--ig" /><b>instagram</b></span>
            <span class="social-dot">·</span>
            <span class="social-pill"><mdi-linkedin class="social-icon social-icon--li" /><b>linkedin</b></span>
          </span>
          <span class="socials-tail">
            <span class="socials-tail-mark">⤷</span>
            todos <b class="socials-handle">@danielhe4rt</b>
          </span>
        </div>
      </div>

      <!-- recruitment QR -->
      <div class="qr-col">
        <div class="qr-frame">
          <img class="qr-img" src="/images/recruit-qr.png" alt="QR · recrutamento.3pontos.com" />
          <div class="qr-scanlines" />
          <div class="qr-corner qr-corner--tl">★ SCAN</div>
          <div class="qr-corner qr-corner--br">vaga</div>
        </div>
        <div class="qr-cap">
          <span class="qr-cap-tag">banco de talentos</span>
          <span class="qr-cap-url">recrutamento.<b>3pontos.com</b></span>
        </div>
      </div>

    </div>
  </div>
</template>

<style scoped>
.obrigado-modular {
  position: absolute;
  inset: 0;
  padding: 2.2rem 2.6rem 1.9rem;
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
  --accent-purple: #c084fc;
  --accent-green: #6ee7a1;
}

/* -------- backgrounds -------- */
.bg-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(to right, rgba(255, 255, 255, 0.025) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(255, 255, 255, 0.025) 1px, transparent 1px);
  background-size: 56px 56px;
  -webkit-mask-image: radial-gradient(ellipse at 50% 45%, #000 35%, transparent 82%);
  mask-image: radial-gradient(ellipse at 50% 45%, #000 35%, transparent 82%);
  pointer-events: none;
}
.bg-vignette {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(800px 600px at 92% 8%, rgba(255, 45, 32, 0.10), transparent 60%),
    radial-gradient(600px 400px at 5% 100%, rgba(255, 255, 255, 0.04), transparent 70%);
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

/* -------- header -------- */
.ob-head {
  position: relative;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 2rem;
  padding: 0.9rem 0 0.3rem;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.15s;
}
.ob-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-serif, 'Instrument Serif', serif);
  font-style: italic;
  font-size: 1rem;
  color: #b9b3a9;
  margin-bottom: 0.1rem;
}
.ob-eyebrow .eyebrow-mark { color: var(--red); font-size: 0.7rem; transform: translateY(-1px); }
.ob-title {
  font-family: var(--font-display, 'Big Shoulders Display', sans-serif);
  font-weight: 900;
  font-size: 4.6rem;
  line-height: 0.88;
  letter-spacing: -0.015em;
  margin: 0;
  color: var(--bone);
  animation: title-wipe 0.8s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.3s;
}
.ob-period {
  color: var(--red);
  display: inline-block;
  text-shadow: 0 0 28px rgba(255, 45, 32, 0.5);
  margin-left: 0.03em;
}
.ob-sub {
  font-family: var(--font-serif, 'Instrument Serif', serif);
  font-style: italic;
  font-size: 1.2rem;
  line-height: 1.25;
  color: #b9b3a9;
  text-align: right;
  padding-bottom: 0.35rem;
}
.ob-sub-em { color: var(--bone); }

/* -------- body grid -------- */
.ob-body {
  position: relative;
  flex: 1;
  min-height: 0;
  display: grid;
  grid-template-columns: 11rem 1fr 12.5rem;
  gap: 1.6rem;
  align-items: stretch;
  padding-top: 0.8rem;
}

/* -------- avatar -------- */
.avatar-col {
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  animation: slide-up 0.6s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.5s;
}
.avatar-frame {
  position: relative;
  width: 100%;
  aspect-ratio: 1;
  overflow: hidden;
  border: 1.5px solid var(--bone);
  background: #0c0c0e;
  box-shadow:
    8px 8px 0 -2px rgba(255, 45, 32, 0.6),
    0 12px 30px -10px rgba(0, 0, 0, 0.6);
  clip-path: polygon(0 0, 100% 0, 100% calc(100% - 18px), calc(100% - 18px) 100%, 0 100%);
  animation: avatar-jitter 11s infinite both;
}
.avatar-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  filter: grayscale(0.4) contrast(1.05) brightness(0.95);
}
.avatar-scanlines {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-image: repeating-linear-gradient(0deg, transparent 0 2px, rgba(0, 0, 0, 0.22) 2px 3px);
  mix-blend-mode: multiply;
  opacity: 0.6;
}
.avatar-glitch-overlay {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background: linear-gradient(180deg, transparent 0%, rgba(255, 45, 32, 0.18) 45%, rgba(255, 255, 255, 0.08) 50%, rgba(255, 45, 32, 0.18) 55%, transparent 100%);
  height: 30%;
  opacity: 0;
  mix-blend-mode: screen;
  animation: avatar-sweep 11s infinite;
}
.avatar-corner {
  position: absolute;
  font-size: 0.5rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 700;
  padding: 0.15rem 0.4rem;
  background: var(--red);
  color: var(--bone);
  z-index: 2;
}
.avatar-corner--tl { top: 0; left: 0; }
.avatar-corner--br {
  bottom: 0;
  right: 0;
  background: rgba(10, 10, 11, 0.85);
  color: var(--bone);
  border: 1px solid rgba(255, 255, 255, 0.15);
  transform: translate(-18px, 0);
}
.avatar-cap {
  display: flex;
  flex-direction: column;
  gap: 0.1rem;
}
.cap-name {
  font-size: 0.74rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  color: var(--bone);
}
.cap-role {
  font-size: 0.56rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--dim);
}

/* -------- terminal -------- */
.terminal {
  position: relative;
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 4px;
  background:
    linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75)),
    radial-gradient(ellipse at 100% 0%, rgba(255, 45, 32, 0.06), transparent 60%);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.04), 0 20px 40px -20px rgba(0, 0, 0, 0.6);
  padding: 1rem 1.2rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.4s;
}
.term-prompt {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 0.25rem;
  font-size: 0.82rem;
  color: var(--bone);
}
.term-user { color: #6ee7a1; font-weight: 700; }
.term-at { color: var(--dim); }
.term-host { color: var(--red); font-weight: 700; }
.term-sep { color: var(--dim); }
.term-path { color: #c084fc; }
.term-cmd { color: var(--bone); }
.term-cursor {
  display: inline-block;
  color: var(--red);
  animation: cursor-blink 1.1s steps(1) infinite;
  margin-left: 0.2rem;
}
.term-rule {
  height: 1px;
  background: linear-gradient(to right, var(--red) 0%, var(--red) 28px, #2a2a2c 28px, #2a2a2c 100%);
  margin: 0.7rem 0;
}
.term-rows { display: flex; flex-direction: column; gap: 0.55rem; }
.term-row {
  display: grid;
  grid-template-columns: 6.4rem 1.2rem 1fr;
  align-items: baseline;
  gap: 0.3rem;
  font-size: 0.9rem;
  line-height: 1.35;
  animation: row-in 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.term-row:nth-child(1) { animation-delay: 0.6s; }
.term-row:nth-child(2) { animation-delay: 0.7s; }
.term-row:nth-child(3) { animation-delay: 0.8s; }
.term-key {
  color: var(--dim);
  text-align: right;
  font-size: 0.76rem;
  letter-spacing: 0.04em;
  text-transform: lowercase;
}
.term-arrow { color: var(--red); font-weight: 700; text-align: center; }
.term-value {
  color: #d6d0c4;
  display: inline-flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 0.35rem;
  min-width: 0;
}
.term-value b { color: var(--bone); font-weight: 700; }
.term-icon { font-size: 0.95em; color: #a8a297; vertical-align: -0.1em; }
.term-icon--red { color: var(--red); }
.term-icon--purple { color: var(--accent-purple); }
.term-tag {
  display: inline-block;
  font-size: 0.62rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  color: var(--dim);
  border: 1px solid #2a2a2c;
  padding: 0.05rem 0.35rem;
  border-radius: 2px;
  transform: translateY(-1px);
}
.term-tag--red { color: var(--red); border-color: rgba(255, 45, 32, 0.5); }

.term-socials {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 0.45rem;
  font-size: 0.76rem;
  color: var(--bone);
  animation: row-in 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.95s;
}
.socials-key { color: var(--dim); text-transform: lowercase; font-size: 0.74rem; }
.socials-list { display: inline-flex; align-items: center; gap: 0.35rem; flex-wrap: wrap; }
.social-pill {
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  padding: 0.06rem 0.4rem;
  border: 1px solid #2a2a2c;
  border-radius: 2px;
  background: rgba(20, 20, 24, 0.5);
  color: var(--bone);
  font-size: 0.72rem;
}
.social-icon { font-size: 0.95em; }
.social-icon--gh { color: var(--bone); }
.social-icon--ig { color: #ff5b8a; }
.social-icon--li { color: #60a5fa; }
.social-dot { color: var(--dim); opacity: 0.6; }
.socials-tail {
  margin-left: auto;
  color: var(--dim);
  font-style: italic;
  font-family: var(--font-serif, 'Instrument Serif', serif);
  font-size: 0.85rem;
}
.socials-tail-mark { color: var(--red); margin-right: 0.2rem; font-style: normal; font-family: var(--font-mono); }
.socials-handle { color: var(--red); font-style: normal; font-family: var(--font-mono); font-weight: 700; }

/* -------- qr -------- */
.qr-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.6rem;
  justify-content: flex-start;
  animation: slide-up 0.6s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.6s;
}
.qr-frame {
  position: relative;
  width: 100%;
  aspect-ratio: 1;
  overflow: hidden;
  border: 1.5px solid var(--bone);
  background: var(--bone);
  box-shadow:
    8px 8px 0 -2px rgba(255, 45, 32, 0.6),
    0 12px 30px -10px rgba(0, 0, 0, 0.6);
  clip-path: polygon(0 0, 100% 0, 100% calc(100% - 18px), calc(100% - 18px) 100%, 0 100%);
}
.qr-img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
  background: var(--bone);
  padding: 0.5rem;
}
.qr-scanlines {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-image: repeating-linear-gradient(0deg, transparent 0 2px, rgba(0, 0, 0, 0.10) 2px 3px);
  mix-blend-mode: multiply;
  opacity: 0.4;
}
.qr-corner {
  position: absolute;
  font-size: 0.5rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 700;
  padding: 0.15rem 0.4rem;
  background: var(--red);
  color: var(--bone);
  z-index: 2;
}
.qr-corner--tl { top: 0; left: 0; }
.qr-corner--br {
  bottom: 0;
  right: 0;
  background: rgba(10, 10, 11, 0.85);
  color: var(--bone);
  border: 1px solid rgba(255, 255, 255, 0.15);
  transform: translate(-18px, 0);
}
.qr-cap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.15rem;
  text-align: center;
}
.qr-cap-tag {
  font-size: 0.56rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--dim);
}
.qr-cap-url { font-size: 0.74rem; color: var(--red); }
.qr-cap-url b { color: var(--bone); font-weight: 700; }

/* -------- glitch + keyframes -------- */
.g { display: inline-block; will-change: filter, transform, opacity; }
.g-a { animation: g-a 6.5s infinite both; }

@keyframes fade-in { from { opacity: 0; } to { opacity: 1; } }
@keyframes slide-up { from { opacity: 0; transform: translateY(14px); } to { opacity: 1; transform: translateY(0); } }
@keyframes title-wipe { from { opacity: 0; clip-path: inset(0 100% 0 0); } to { opacity: 1; clip-path: inset(0 0 0 0); } }
@keyframes cursor-blink { 50% { opacity: 0; } }
@keyframes row-in { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

@keyframes avatar-jitter {
  0%, 30%   { transform: none; filter: none; }
  31%       { transform: translateX(-3px); filter: hue-rotate(20deg) saturate(1.4); }
  32%       { transform: translateX(4px) skewY(-0.5deg); }
  33%       { transform: translateX(-2px); filter: contrast(1.3) saturate(0.6); }
  34%, 67%  { transform: none; filter: none; }
  68%       { transform: translateY(-2px) skewX(0.5deg); filter: brightness(1.15); }
  69%       { transform: translateY(2px); filter: hue-rotate(-15deg); }
  70%, 100% { transform: none; filter: none; }
}
@keyframes avatar-sweep {
  0%, 30%   { transform: translateY(-100%); opacity: 0; }
  31%, 33%  { opacity: 1; }
  34%       { transform: translateY(330%); opacity: 0; }
  35%, 100% { transform: translateY(-100%); opacity: 0; }
}
@keyframes g-a {
  0%, 90%   { filter: none; transform: none; color: inherit; opacity: 1; }
  91%       { filter: blur(1.4px); transform: translateX(2px); opacity: 0.55; color: var(--red); }
  92%       { filter: blur(0.4px); transform: translateX(-3px); opacity: 0.8; }
  93%       { filter: blur(0.9px) hue-rotate(40deg); transform: translateX(1px); }
  94%, 100% { filter: none; transform: none; opacity: 1; color: inherit; }
}
</style>
