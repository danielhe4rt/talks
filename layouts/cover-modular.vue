<template>
  <div class="cover-modular">
    <div class="bg-grid" />
    <div class="bg-vignette" />
    <div class="bg-grain" />

    <!-- file-tree pane (right side, glitching states) -->
    <div class="tree-pane">
      <div class="tree-frame">
        <div class="tree-titlebar">
          <span class="tree-dots">
            <span class="tree-dot" />
            <span class="tree-dot" />
            <span class="tree-dot" />
          </span>
          <span class="tree-path">~/cart · <span class="tree-path-cur">4 estruturas</span></span>
          <span class="tree-status">cycle</span>
        </div>

        <div class="tree-body">
          <!-- state 1: Laravel Padrão -->
          <pre class="tree-state tree-state--1">app/Modules/Cart/
├── <span class="tree-mod tree-mod--green">Models</span>/
│   ├── Cart.php
│   └── <span class="g g-a">CartItem.php</span>
├── <span class="tree-mod tree-mod--green">Services</span>/
│   └── <span class="g g-c">CartService.php</span>
├── <span class="tree-mod tree-mod--green">Jobs</span>/
│   └── ClearExpiredCartsJob.php
└── <span class="tree-mod tree-mod--green">Support</span>/
    └── <span class="g g-b">PriceCalculator.php</span></pre>

          <!-- state 2: Flat File -->
          <pre class="tree-state tree-state--2">app/Modules/Cart/
├── Cart.php
├── <span class="g g-c">CartItem.php</span>
├── <span class="g g-a">CartService.php</span>
├── PriceCalculator.php
└── <span class="g g-b">ClearExpiredCartsJob.php</span></pre>

          <!-- state 3: Clean Architecture -->
          <pre class="tree-state tree-state--3">app/Modules/Cart/
├── <span class="tree-mod tree-mod--purple">Domain</span>/
│   ├── Cart.php
│   ├── <span class="g g-b">CartItem.php</span>
│   └── <span class="g g-a">PriceCalculator.php</span>
├── <span class="tree-mod tree-mod--purple">Application</span>/
│   └── CartService.php
└── <span class="tree-mod tree-mod--purple">Infrastructure</span>/
    └── <span class="g g-c">ClearExpiredCartsJob.php</span></pre>

          <!-- state 4: DDD-like -->
          <pre class="tree-state tree-state--4">app/Modules/Cart/
├── <span class="tree-mod tree-mod--orange">Domain</span>/
│   ├── Models/
│   │   ├── Cart.php
│   │   └── <span class="g g-a">CartItem.php</span>
│   └── Services/
│       └── <span class="g g-b">PriceCalculator.php</span>
├── <span class="tree-mod tree-mod--orange">Application</span>/
│   ├── Actions/
│   │   └── <span class="g g-c">AddToCartAction.php</span>
│   └── Jobs/
│       └── ClearExpiredCartsJob.php
└── <span class="tree-mod tree-mod--orange">Infrastructure</span>/
    └── <span class="g g-a">EloquentCartRepository.php</span></pre>

          <!-- scanline + sweep overlays -->
          <div class="tree-scanlines" />
          <div class="tree-sweep" />
        </div>
      </div>
    </div>

    <!-- top metadata bar -->
    <div class="meta-bar">
      <span class="meta-tag">N°<b>01</b></span>
      <span class="meta-pipe">│</span>
      <span class="meta-track">LARAVEL TRACK · <b>40min</b></span>
      <span class="meta-fill" />
      <span class="meta-year">MMXXV</span>
    </div>

    <!-- middle area: title vertically centered -->
    <div class="middle-area">

    <!-- title block -->
    <div class="title-block">
      <div class="title-eyebrow">
        <span class="eyebrow-mark">◆</span>
        <span>um talk sobre</span>
      </div>

      <h1 class="title">
        <span class="title-line title-line--outline">LARAVEL</span>
        <span class="title-line title-line--solid">
          MODULAR<span class="title-slash">/</span>
        </span>
      </h1>

      <div class="title-rule">
        <span class="rule-block" />
        <span class="rule-line" />
        <span class="rule-tail">v1.0</span>
      </div>

      <div class="tagline">
        <div class="tagline-row">
          <span class="tagline-prompt">&gt;</span>
          deixa os <b>pensamentos intrusivos</b> vencerem
        </div>
        <div class="tagline-row tagline-row--cont">
          <span class="tagline-arrow">⟶</span>
          <code class="tagline-code">rm -rf</code> sua <b>codebase</b>
        </div>
      </div>
    </div>

    </div><!-- /middle-area -->

    <!-- stat strip -->
    <div class="stat-strip">
      <div class="stat">
        <span class="stat-num">19</span>
        <span class="stat-label">pastas</span>
      </div>
      <span class="stat-sep" />
      <div class="stat">
        <span class="stat-num">487</span>
        <span class="stat-label">arquivos</span>
      </div>
      <span class="stat-sep" />
      <div class="stat stat--accent">
        <span class="stat-num">01</span>
        <span class="stat-label">mentira</span>
      </div>
    </div>

    <!-- footer -->
    <div class="footer-bar">
      <div class="footer-left">
        <div class="footer-name">DANIEL HE4RT</div>
        <div class="footer-sub">@danielhe4rt · tech lead @ 3pontos</div>
      </div>
      <div class="footer-right">
        <span class="prompt-label">press</span>
        <kbd class="key">SPACE</kbd>
        <span class="cursor">▮</span>
      </div>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@500;700;900&family=JetBrains+Mono:wght@400;500;700&family=Instrument+Serif:ital@0;1&display=swap');
</style>

<style scoped>
.cover-modular {
  position: absolute;
  inset: 0;
  padding: 2.6rem 2.6rem 2.1rem;
  background: #0a0a0b;
  color: #f5f1ea;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
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

/* -------- middle area (vertical center) -------- */
.middle-area {
  position: relative;
  flex: 1;
  display: flex;
  align-items: center;
  margin: 0.6rem 0;
}

/* -------- file-tree pane -------- */
.tree-pane {
  position: absolute;
  top: 44%;
  right: 2.6rem;
  transform: translateY(-50%);
  width: 19.5rem;
  height: 16.5rem;
  pointer-events: none;
  z-index: 1;
  animation: tree-pane-in 1s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.7s;
}
.tree-frame {
  position: relative;
  height: 100%;
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 4px;
  background:
    linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75)),
    radial-gradient(ellipse at 80% 0%, rgba(255, 45, 32, 0.06), transparent 60%);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.04),
    0 20px 40px -20px rgba(0, 0, 0, 0.6);
  overflow: hidden;
  backdrop-filter: blur(2px);
}
.tree-titlebar {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  padding: 0.45rem 0.7rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.5rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #5a5a5d;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.025), transparent);
}
.tree-dots {
  display: inline-flex;
  gap: 0.25rem;
}
.tree-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #2a2a2c;
  border: 1px solid rgba(255, 255, 255, 0.05);
}
.tree-dot:first-child { background: #3a1e1c; }
.tree-path {
  margin-left: 0.3rem;
  letter-spacing: 0.1em;
}
.tree-path-cur {
  color: var(--bone);
  font-weight: 700;
}
.tree-status {
  margin-left: auto;
  color: var(--red);
  opacity: 0.6;
  font-size: 0.45rem;
}

.tree-body {
  position: relative;
  height: calc(100% - 1.6rem);
  padding: 0.7rem 0.85rem;
  overflow: hidden;
}

.tree-state {
  position: absolute;
  top: 0.7rem;
  left: 0.85rem;
  right: 0.85rem;
  margin: 0;
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  line-height: 1.45;
  color: #b8b2a6;
  white-space: pre;
  font-weight: 400;
  letter-spacing: 0;
}

.tree-state--1 { animation: tree-cycle-1 16s infinite both; }
.tree-state--2 { animation: tree-cycle-2 16s infinite both; }
.tree-state--3 { animation: tree-cycle-3 16s infinite both; }
.tree-state--4 { animation: tree-cycle-4 16s infinite both; }

.tree-mark {
  font-size: 0.55rem;
  margin-left: 0.4rem;
}
.tree-mark--strike { color: var(--red); opacity: 0.8; }
.tree-mark--warn { color: #ffa53a; opacity: 0.8; }
.tree-corrupt {
  color: var(--red);
  background: rgba(255, 45, 32, 0.12);
  padding: 0 2px;
}
.tree-mod {
  color: var(--bone);
  font-weight: 700;
  padding: 0 3px;
  border-left: 2px solid var(--red);
  margin-left: -3px;
  background: rgba(255, 45, 32, 0.08);
}
.tree-mod--green  { border-left-color: #6ee7a1; background: rgba(110, 231, 161, 0.08); }
.tree-mod--blue   { border-left-color: #60a5fa; background: rgba(96, 165, 250, 0.08); }
.tree-mod--purple { border-left-color: #c084fc; background: rgba(192, 132, 252, 0.08); }
.tree-mod--orange { border-left-color: #ffa53a; background: rgba(255, 165, 58, 0.08); }

/* per-item glitch flickers — 3 variants with different rhythms */
.g {
  display: inline-block;
  will-change: filter, transform, opacity;
}
.g-a { animation: g-a 6.5s infinite both; }
.g-b { animation: g-b 8s infinite both;  animation-delay: -2.4s; }
.g-c { animation: g-c 7.2s infinite both; animation-delay: -4.1s; }

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

/* CRT scanlines */
.tree-scanlines {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-image: repeating-linear-gradient(
    0deg,
    transparent 0 2px,
    rgba(255, 255, 255, 0.018) 2px 3px
  );
  mix-blend-mode: overlay;
}

/* periodic glitch sweep */
.tree-sweep {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background: linear-gradient(
    180deg,
    transparent 0%,
    rgba(255, 45, 32, 0.18) 40%,
    rgba(255, 255, 255, 0.06) 50%,
    rgba(255, 45, 32, 0.18) 60%,
    transparent 100%
  );
  height: 30%;
  animation: tree-sweep 12s infinite;
  opacity: 0;
  mix-blend-mode: screen;
}

@keyframes tree-pane-in {
  from { opacity: 0; transform: translate(20px, -50%); }
  to   { opacity: 1; transform: translate(0, -50%); }
}

/* 4-state cycle: each state visible ~22%, glitch transitions ~3% */
@keyframes tree-cycle-1 {
  0%, 22%   { opacity: 1; transform: none; filter: none; }
  23%       { opacity: 0.4; transform: translateX(-3px) skewX(-1deg); filter: hue-rotate(40deg) saturate(1.8); }
  24%       { opacity: 0.15; transform: translateX(4px); }
  25%, 97%  { opacity: 0; }
  98%       { opacity: 0.3; transform: translateX(-2px); filter: hue-rotate(30deg); }
  99%       { opacity: 0.7; transform: none; filter: none; }
  100%      { opacity: 1; }
}

@keyframes tree-cycle-2 {
  0%, 22%   { opacity: 0; }
  23%       { opacity: 0.3; transform: translateX(3px) skewX(1deg); filter: hue-rotate(20deg); }
  24%       { opacity: 0.6; transform: translateX(-2px); }
  25%, 47%  { opacity: 1; transform: none; filter: none; }
  48%       { opacity: 0.4; transform: translateX(-3px) skewX(-1deg); filter: hue-rotate(40deg); }
  49%, 100% { opacity: 0; }
}

@keyframes tree-cycle-3 {
  0%, 47%   { opacity: 0; }
  48%       { opacity: 0.3; transform: translateX(3px) skewX(1deg); filter: hue-rotate(20deg); }
  49%       { opacity: 0.6; transform: translateX(-2px); }
  50%, 72%  { opacity: 1; transform: none; filter: none; }
  73%       { opacity: 0.4; transform: translateX(-3px) skewX(-1deg); filter: hue-rotate(40deg); }
  74%, 100% { opacity: 0; }
}

@keyframes tree-cycle-4 {
  0%, 72%   { opacity: 0; }
  73%       { opacity: 0.3; transform: translateX(3px) skewX(1deg); filter: hue-rotate(20deg); }
  74%       { opacity: 0.6; transform: translateX(-2px); }
  75%, 96%  { opacity: 1; transform: none; filter: none; }
  97%       { opacity: 0.4; transform: translateX(-3px); filter: hue-rotate(30deg); }
  98%, 100% { opacity: 0; }
}

@keyframes tree-sweep {
  0%, 21%   { transform: translateY(-100%); opacity: 0; }
  22%, 24%  { opacity: 1; }
  25%       { transform: translateY(330%); opacity: 0; }
  26%, 46%  { transform: translateY(-100%); opacity: 0; }
  47%, 49%  { opacity: 1; }
  50%       { transform: translateY(330%); opacity: 0; }
  51%, 71%  { transform: translateY(-100%); opacity: 0; }
  72%, 74%  { opacity: 1; }
  75%       { transform: translateY(330%); opacity: 0; }
  76%, 96%  { transform: translateY(-100%); opacity: 0; }
  97%, 99%  { opacity: 1; }
  100%      { transform: translateY(330%); opacity: 0; }
}

/* -------- meta bar -------- */
.meta-bar {
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.68rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--dim);
  animation: fade-in 0.6s ease both;
  animation-delay: 0.05s;
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
.meta-year { color: var(--bone); font-weight: 700; }

/* -------- title -------- */
.title-block {
  position: relative;
  max-width: 92%;
}
.title-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  font-size: 1rem;
  color: #b9b3a9;
  margin-bottom: 0.25rem;
  letter-spacing: 0.01em;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.25s;
}
.eyebrow-mark {
  color: var(--red);
  font-size: 0.7rem;
  transform: translateY(-1px);
}

.title {
  font-family: 'Big Shoulders Display', 'Archivo Black', sans-serif;
  font-weight: 900;
  font-size: 6.2rem;
  line-height: 0.92;
  letter-spacing: -0.005em;
  margin: 0;
  padding-top: 0.15rem;
  display: flex;
  flex-direction: column;
}

.title-line {
  display: block;
  white-space: nowrap;
}

.title-line--outline {
  color: transparent;
  -webkit-text-stroke: 2px var(--bone);
  opacity: 0.92;
  animation: title-wipe 0.8s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.35s;
}

.title-line--solid {
  color: var(--bone);
  margin-left: 1.8rem;
  position: relative;
  animation: title-wipe 0.8s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.55s;
}

.title-slash {
  color: var(--red);
  display: inline-block;
  transform: translateY(-0.04em);
  margin-left: 0.05em;
  text-shadow: 0 0 24px rgba(255, 45, 32, 0.45);
}

.title-rule {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin: 0.9rem 0 0.6rem 1.8rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.85s;
}
.rule-block {
  width: 46px;
  height: 11px;
  background: var(--red);
  box-shadow: 0 0 22px rgba(255, 45, 32, 0.4);
}
.rule-line {
  flex: 0 0 180px;
  height: 2px;
  background: linear-gradient(to right, var(--red), transparent);
}
.rule-tail {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--dim);
}

.tagline {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.88rem;
  margin-left: 1.8rem;
  color: #c8c2b6;
  letter-spacing: 0.01em;
  line-height: 1.5;
  max-width: 32rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 1s;
}
.tagline-row {
  display: flex;
  align-items: center;
  gap: 0.45rem;
  white-space: nowrap;
}
.tagline-row--cont {
  padding-left: 1.05rem;
}
.tagline-prompt {
  color: var(--red);
  font-weight: 700;
}
.tagline-code {
  background: rgba(255, 45, 32, 0.08);
  border: 1px solid rgba(255, 45, 32, 0.25);
  color: var(--bone);
  padding: 0.08em 0.45em;
  border-radius: 3px;
  font-weight: 500;
  font-size: 0.98em;
}
.tagline-arrow {
  color: var(--red);
  display: inline-block;
  transform: translateY(-1px);
}
.tagline b {
  color: var(--bone);
  font-weight: 700;
}

/* -------- stat strip -------- */
.stat-strip {
  position: relative;
  display: flex;
  align-items: flex-end;
  gap: 1.8rem;
  border-top: 1px solid #1c1c1f;
  border-bottom: 1px solid #1c1c1f;
  padding: 0.75rem 0;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 1.15s;
}
.stat {
  display: flex;
  align-items: baseline;
  gap: 0.55rem;
}
.stat-num {
  font-family: 'Big Shoulders Display', sans-serif;
  font-weight: 900;
  font-size: 2.1rem;
  line-height: 1;
  color: var(--bone);
  letter-spacing: -0.01em;
  font-variant-numeric: tabular-nums;
}
.stat--accent .stat-num {
  color: var(--red);
  text-shadow: 0 0 28px rgba(255, 45, 32, 0.4);
}
.stat-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.68rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--dim);
}
.stat-sep {
  width: 1px;
  height: 30px;
  background: #2a2a2c;
  align-self: center;
}

/* -------- footer -------- */
.footer-bar {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.85rem;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.68rem;
  letter-spacing: 0.12em;
  animation: fade-in 0.55s ease both;
  animation-delay: 1.3s;
}
.footer-name {
  color: var(--bone);
  font-weight: 700;
  letter-spacing: 0.22em;
  font-size: 0.82rem;
}
.footer-sub {
  color: var(--dim);
  margin-top: 0.15rem;
  text-transform: lowercase;
  letter-spacing: 0.08em;
}
.footer-right {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  color: var(--dim);
  text-transform: uppercase;
}
.key {
  display: inline-block;
  padding: 0.25rem 0.55rem;
  border: 1px solid #3a3a3d;
  border-bottom-width: 3px;
  border-radius: 4px;
  color: var(--bone);
  background: rgba(21, 21, 24, 0.5);
  font-size: 0.68rem;
  letter-spacing: 0.15em;
}
.cursor {
  color: var(--red);
  animation: blink 1.1s steps(1) infinite;
  font-size: 0.9rem;
  margin-left: 0.15rem;
}

/* -------- animations -------- */
@keyframes fade-in {
  from { opacity: 0; }
  to   { opacity: 1; }
}
@keyframes slide-up {
  from { opacity: 0; transform: translateY(18px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes title-wipe {
  from { opacity: 0; clip-path: inset(0 100% 0 0); }
  to   { opacity: 1; clip-path: inset(0 0 0 0); }
}
@keyframes blink {
  50% { opacity: 0; }
}
</style>
