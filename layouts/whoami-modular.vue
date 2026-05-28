<template>
  <div class="whoami-modular">
    <div class="bg-grid" />
    <div class="bg-vignette" />
    <div class="bg-grain" />

    <!-- top metadata bar -->
    <div class="meta-bar">
      <span class="meta-tag">N°<b>02</b></span>
      <span class="meta-pipe">│</span>
      <span class="meta-track">WHOAMI · <b>quem tá falando</b></span>
      <span class="meta-fill" />
      <span class="meta-handle">◆ @danielhe4rt</span>
    </div>

    <!-- main two-column body -->
    <div class="body">

      <!-- left: title + avatar -->
      <div class="left-col">
        <div class="title-block">
          <div class="title-eyebrow">
            <span class="eyebrow-mark">◆</span>
            <span>antes de começar</span>
          </div>

          <h1 class="title">
            <span class="title-line title-line--outline">QUEM</span>
            <span class="title-line title-line--solid">
              SOU EU<span class="title-q">?</span>
            </span>
          </h1>

          <div class="title-rule">
            <span class="rule-block" />
            <span class="rule-line" />
            <span class="rule-tail">id · 01</span>
          </div>
        </div>

        <div class="avatar-block">
          <div class="avatar-frame">
            <img
              class="avatar-img"
              src="https://github.com/danielhe4rt.png"
              alt="Daniel He4rt"
            />
            <div class="avatar-scanlines" />
            <div class="avatar-glitch-overlay" />
            <div class="avatar-corner avatar-corner--tl">★ REC</div>
            <div class="avatar-corner avatar-corner--br">@danielhe4rt</div>
          </div>
          <div class="avatar-caption">
            <span class="cap-dot" />
            <span>session_id · talk · 40m</span>
          </div>
        </div>
      </div>

      <!-- right: terminal whoami output -->
      <div class="right-col">
        <div class="terminal">
          <div class="term-prompt">
            <span class="term-user">daniel</span><span class="term-at">@</span><span class="term-host">he4rt</span>
            <span class="term-sep">:</span>
            <span class="term-path">~</span>
            <span class="term-sep">$</span>
            <span class="term-cmd">whoami <span class="term-flag">--verbose</span></span>
            <span class="term-cursor">▮</span>
          </div>

          <div class="term-rule" />

          <div class="term-rows">
            <div class="term-row term-row--multi">
              <span class="term-key">roles</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <span class="role-line">
                  <mdi-account-tie class="term-icon" />
                  Tech Lead <span class="term-at-sym">@</span> <b>3Pontos</b>
                </span>
                <span class="role-line">
                  <mdi-rocket-launch class="term-icon" />
                  Senior SWE <span class="term-at-sym">@</span> <b>ScopeyOnSite</b>
                </span>
              </span>
            </div>

            <div class="term-row">
              <span class="term-key">first job</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <mdi-briefcase-outline class="term-icon" />
                <span class="g g-a">W1 Finance</span> · Fullstack
                <span class="term-tag">2018</span>
              </span>
            </div>

            <div class="term-row">
              <span class="term-key">since</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <mdi-code-tags class="term-icon" />
                <span class="term-tag term-tag--red">2011</span> ·
                servidores de <b>SA:MP</b>
              </span>
            </div>

            <div class="term-row term-row--multi">
              <span class="term-key">stack</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <mdi-code-braces class="term-icon" />
                PHP · <b>Laravel</b> · Rust · JS<br>
                <span class="term-sub">MySQL · ScyllaDB · PostgreSQL</span>
              </span>
            </div>

            <div class="term-row">
              <span class="term-key">livecoding</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <mdi-twitch class="term-icon term-icon--red" />
                <span class="g g-c">twitch.tv/<b>danielhe4rt</b></span>
                <span class="term-tag">6 anos</span>
              </span>
            </div>

            <div class="term-row">
              <span class="term-key">award</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <mdi-trophy class="term-icon" />
                Microsoft <b>MVP</b>
                <span class="term-tag">×3 anos</span>
              </span>
            </div>

            <div class="term-row">
              <span class="term-key">music</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <mdi-guitar-electric class="term-icon" />
                <span class="g g-b">instrumentos de corda</span>
              </span>
            </div>

            <div class="term-row">
              <span class="term-key">karaoke</span>
              <span class="term-arrow">→</span>
              <span class="term-value">
                <mdi-microphone class="term-icon" />
                Challenger <b>1350 PDL</b>
              </span>
            </div>
          </div>

          <div class="term-rule" />

          <div class="term-socials">
            <span class="socials-key">socials</span>
            <span class="term-arrow">→</span>
            <span class="socials-list">
              <span class="social-pill">
                <mdi-github class="social-icon social-icon--gh" />
                <b>github</b>
              </span>
              <span class="social-dot">·</span>
              <span class="social-pill">
                <mdi-instagram class="social-icon social-icon--ig" />
                <b>instagram</b>
              </span>
              <span class="social-dot">·</span>
              <span class="social-pill">
                <mdi-linkedin class="social-icon social-icon--li" />
                <b>linkedin</b>
              </span>
            </span>
            <span class="socials-tail">
              <span class="socials-tail-mark">⤷</span>
              todos <b class="socials-handle">@danielhe4rt</b>
            </span>
          </div>
        </div>
      </div>

    </div>

    <!-- footer -->
    <div class="footer-bar">
      <div class="footer-left">
        <div class="footer-name">
          DANIEL REIS
          <span class="footer-aka">a.k.a <b>@danielhe4rt</b></span>
        </div>
        <div class="footer-sub">tech lead @ 3pontos · senior swe @ scopeyonsite</div>
      </div>
      <div class="footer-right">
        <span class="prompt-label">press</span>
        <kbd class="key">SPACE</kbd>
        <span class="next-label">→ a história começa</span>
      </div>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@500;700;900&family=JetBrains+Mono:wght@400;500;700&family=Instrument+Serif:ital@0;1&display=swap');
</style>

<style scoped>
.whoami-modular {
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
  -webkit-mask-image: radial-gradient(ellipse at 30% 40%, #000 30%, transparent 80%);
  mask-image: radial-gradient(ellipse at 30% 40%, #000 30%, transparent 80%);
  pointer-events: none;
}
.bg-vignette {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(800px 600px at 90% 100%, rgba(255, 45, 32, 0.10), transparent 60%),
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

/* -------- body grid -------- */
.body {
  position: relative;
  flex: 1;
  display: grid;
  grid-template-columns: 16.5rem 1fr;
  gap: 1.8rem;
  align-items: stretch;
  padding: 0.9rem 0 0.6rem;
  min-height: 0;
}

/* -------- left column -------- */
.left-col {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  min-width: 0;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.2s;
}

.title-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  font-size: 0.92rem;
  color: #b9b3a9;
  margin-bottom: 0.15rem;
  letter-spacing: 0.01em;
}
.eyebrow-mark { color: var(--red); font-size: 0.6rem; }

.title {
  font-family: 'Big Shoulders Display', 'Archivo Black', sans-serif;
  font-weight: 900;
  font-size: 4.1rem;
  line-height: 0.92;
  margin: 0;
  display: flex;
  flex-direction: column;
}
.title-line { display: block; white-space: nowrap; }
.title-line--outline {
  color: transparent;
  -webkit-text-stroke: 1.6px var(--bone);
  opacity: 0.92;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.3s;
}
.title-line--solid {
  color: var(--bone);
  margin-left: 1.4rem;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.45s;
}
.title-q {
  color: var(--red);
  display: inline-block;
  text-shadow: 0 0 22px rgba(255, 45, 32, 0.45);
  margin-left: 0.04em;
}

.title-rule {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  margin: 0.5rem 0 0.2rem 1.4rem;
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

/* -------- avatar -------- */
.avatar-block {
  margin-top: 0.4rem;
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  animation: slide-up 0.6s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.55s;
}
.avatar-frame {
  position: relative;
  width: 11.5rem;
  height: 11.5rem;
  overflow: hidden;
  border: 1.5px solid var(--bone);
  background: #0c0c0e;
  box-shadow:
    8px 8px 0 -2px rgba(255, 45, 32, 0.6),
    0 12px 30px -10px rgba(0, 0, 0, 0.6);
  clip-path: polygon(
    0 0,
    100% 0,
    100% calc(100% - 18px),
    calc(100% - 18px) 100%,
    0 100%
  );
  animation: avatar-jitter 11s infinite both;
}
.avatar-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  filter: grayscale(0.4) contrast(1.05) brightness(0.95);
  mix-blend-mode: normal;
}
.avatar-scanlines {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-image: repeating-linear-gradient(
    0deg,
    transparent 0 2px,
    rgba(0, 0, 0, 0.22) 2px 3px
  );
  mix-blend-mode: multiply;
  opacity: 0.6;
}
.avatar-glitch-overlay {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background: linear-gradient(
    180deg,
    transparent 0%,
    rgba(255, 45, 32, 0.18) 45%,
    rgba(255, 255, 255, 0.08) 50%,
    rgba(255, 45, 32, 0.18) 55%,
    transparent 100%
  );
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

.avatar-caption {
  display: flex;
  align-items: center;
  gap: 0.45rem;
  font-size: 0.55rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--dim);
}
.cap-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--red);
  box-shadow: 0 0 8px rgba(255, 45, 32, 0.7);
  animation: cap-blink 1.4s steps(1) infinite;
}

/* -------- right column / terminal -------- */
.right-col {
  position: relative;
  display: flex;
  min-width: 0;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.4s;
}

.terminal {
  position: relative;
  flex: 1;
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 4px;
  background:
    linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75)),
    radial-gradient(ellipse at 100% 0%, rgba(255, 45, 32, 0.06), transparent 60%);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.04),
    0 20px 40px -20px rgba(0, 0, 0, 0.6);
  padding: 0.9rem 1.1rem;
  font-family: 'JetBrains Mono', monospace;
  overflow: hidden;
}

.term-prompt {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 0.25rem;
  font-size: 0.78rem;
  color: var(--bone);
}
.term-user { color: #6ee7a1; font-weight: 700; }
.term-at { color: var(--dim); }
.term-host { color: #60a5fa; font-weight: 700; }
.term-sep { color: var(--dim); }
.term-path { color: #c084fc; }
.term-cmd { color: var(--bone); }
.term-flag { color: #ffa53a; }
.term-cursor {
  display: inline-block;
  color: var(--red);
  animation: cursor-blink 1.1s steps(1) infinite;
  margin-left: 0.2rem;
}

.term-rule {
  height: 1px;
  background: linear-gradient(to right, var(--red) 0%, var(--red) 28px, #2a2a2c 28px, #2a2a2c 100%);
  margin: 0.55rem 0;
}

.term-rows {
  display: flex;
  flex-direction: column;
  gap: 0.32rem;
}

.term-row {
  display: grid;
  grid-template-columns: 6.4rem 1.2rem 1fr;
  align-items: baseline;
  gap: 0.3rem;
  font-size: 0.84rem;
  line-height: 1.35;
  animation: row-in 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.term-row:nth-child(1) { animation-delay: 0.6s; }
.term-row:nth-child(2) { animation-delay: 0.66s; }
.term-row:nth-child(3) { animation-delay: 0.72s; }
.term-row:nth-child(4) { animation-delay: 0.78s; }
.term-row:nth-child(5) { animation-delay: 0.84s; }
.term-row:nth-child(6) { animation-delay: 0.9s; }
.term-row:nth-child(7) { animation-delay: 0.96s; }
.term-row:nth-child(8) { animation-delay: 1.02s; }

.term-key {
  color: var(--dim);
  text-align: right;
  font-size: 0.76rem;
  letter-spacing: 0.04em;
  text-transform: lowercase;
}
.term-arrow {
  color: var(--red);
  font-weight: 700;
  text-align: center;
}
.term-value {
  color: #d6d0c4;
  display: inline-flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 0.35rem;
  min-width: 0;
}
.term-value b {
  color: var(--bone);
  font-weight: 700;
}
.term-value i {
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  color: #b9b3a9;
}
.term-row--multi .term-value {
  align-items: flex-start;
  line-height: 1.35;
}
.term-sub {
  color: var(--dim);
  font-size: 0.74rem;
  flex-basis: 100%;
}
.term-at-sym { color: var(--red); font-weight: 700; }

.term-icon {
  font-size: 0.95em;
  color: #a8a297;
  vertical-align: -0.1em;
}
.term-icon--red { color: var(--red); }
.term-icon--bone { color: var(--bone); }

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
.term-tag--red {
  color: var(--red);
  border-color: rgba(255, 45, 32, 0.5);
}

/* role multi-line value */
.role-line {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  flex-basis: 100%;
}
.role-line:not(:last-child) { margin-bottom: 0.1rem; }

/* social pills row */
.term-socials {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 0.45rem;
  font-size: 0.76rem;
  color: var(--bone);
  letter-spacing: 0.02em;
  margin-top: 0.05rem;
}
.socials-key {
  color: var(--dim);
  text-transform: lowercase;
  font-size: 0.74rem;
}
.socials-list {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  flex-wrap: wrap;
}
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
  letter-spacing: 0.02em;
}
.social-pill b { font-weight: 700; }
.social-icon { font-size: 0.95em; }
.social-icon--gh { color: var(--bone); }
.social-icon--ig { color: #ff5b8a; }
.social-icon--li { color: #60a5fa; }
.social-dot { color: var(--dim); opacity: 0.6; }

.socials-tail {
  margin-left: auto;
  color: var(--dim);
  font-style: italic;
  font-family: 'Instrument Serif', serif;
  font-size: 0.85rem;
}
.socials-tail-mark {
  color: var(--red);
  margin-right: 0.2rem;
  font-style: normal;
  font-family: 'JetBrains Mono', monospace;
}
.socials-handle {
  color: var(--red);
  font-style: normal;
  font-family: 'JetBrains Mono', monospace;
  font-weight: 700;
}

/* -------- footer -------- */
.footer-bar {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.4rem;
  padding-top: 0.55rem;
  border-top: 1px solid #1c1c1f;
  font-size: 0.66rem;
  letter-spacing: 0.12em;
  animation: fade-in 0.55s ease both;
  animation-delay: 1.2s;
}
.footer-name {
  color: var(--bone);
  font-weight: 700;
  letter-spacing: 0.22em;
  font-size: 0.78rem;
  display: inline-flex;
  align-items: baseline;
  gap: 0.5rem;
}
.footer-aka {
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  font-weight: 400;
  letter-spacing: 0.02em;
  color: var(--dim);
  font-size: 0.78rem;
  text-transform: none;
}
.footer-aka b {
  color: var(--red);
  font-weight: 700;
  font-family: 'JetBrains Mono', monospace;
  font-style: normal;
  letter-spacing: 0.02em;
}
.footer-sub {
  color: var(--dim);
  margin-top: 0.1rem;
  text-transform: lowercase;
  letter-spacing: 0.08em;
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

/* -------- glitch flickers (shared vocab with cover) -------- */
.g {
  display: inline-block;
  will-change: filter, transform, opacity;
}
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
@keyframes cursor-blink { 50% { opacity: 0; } }
@keyframes cap-blink    { 50% { opacity: 0.25; } }

@keyframes row-in {
  from { opacity: 0; transform: translateY(6px); }
  to   { opacity: 1; transform: translateY(0); }
}

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
  35%, 67%  { transform: translateY(-100%); opacity: 0; }
  68%, 70%  { opacity: 1; }
  71%       { transform: translateY(330%); opacity: 0; }
  72%, 100% { opacity: 0; }
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
