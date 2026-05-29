<!--
  recruit-modular — single recruitment / job-opening slide for 3Pontos.

  Self-contained brutalist layout (same vocabulary as whoami-modular.vue):
  BgLayers grid/vignette/grain, meta-bar strip, outline+solid display title
  with red rule-block, terminal `key → value` rows on the left, and a framed
  QR-code placeholder on the right that echoes the avatar-frame treatment.

  ── QR CODE ──────────────────────────────────────────────────────────────
  The right panel shows a dashed placeholder by default. To drop in the real
  QR image, the speaker just passes a `qr` prop via the page frontmatter:

      ---
      layout: recruit-modular
      qr: /images/recruit-qr.png
      ---

  (put the file at  public/images/recruit-qr.png  — Slidev serves /public at /)
  When `qr` is set, the <img> renders and the placeholder is hidden. No other
  edits needed. The QR should point to https://recrutamento.3pontos.com
  ──────────────────────────────────────────────────────────────────────────
-->
<script setup lang="ts">
defineProps<{
  /** Optional path to the real QR image, e.g. "/images/recruit-qr.png".
   *  When unset, a framed placeholder is shown instead. */
  qr?: string
}>()
</script>

<template>
  <div class="recruit-modular">
    <BgLayers vignette-pos="tr" />

    <!-- top metadata bar -->
    <div class="meta-bar">
      <span class="meta-tag">N°<b>04</b></span>
      <span class="meta-pipe">│</span>
      <span class="meta-track">BANCO DE TALENTOS · <b>3pontos tá de olho</b></span>
      <span class="meta-fill" />
      <span class="meta-handle">◆ recrutamento.3pontos.com</span>
    </div>

    <!-- main two-column body -->
    <div class="body">

      <!-- left: title + pitch -->
      <div class="left-col">
        <div class="title-block">
          <div class="title-eyebrow">
            <span class="eyebrow-mark">◆</span>
            <span>já que falei da 3pontos…</span>
          </div>

          <h1 class="title">
            <span class="title-line title-line--outline">ENTRA NO</span>
            <span class="title-line title-line--solid">
              <span class="g g-a">RADAR</span><span class="title-q">.</span>
            </span>
          </h1>

          <div class="title-rule">
            <span class="rule-block" />
            <span class="rule-line" />
            <span class="rule-tail">3pontos · talent pool</span>
          </div>
        </div>

        <!-- pitch: terminal-style key → value rows -->
        <div class="pitch">
          <div class="pitch-row">
            <mdi-radar class="pitch-icon" />
            <span class="pitch-key">o que é</span>
            <span class="pitch-arrow">→</span>
            <span class="pitch-value">
              <b>banco de talentos</b> tech da 3pontos —
              talento br pro mundo
            </span>
          </div>

          <div class="pitch-row">
            <mdi-account-plus class="pitch-icon" />
            <span class="pitch-key">como é</span>
            <span class="pitch-arrow">→</span>
            <span class="pitch-value">
              cadastra teu perfil, fica no <b>radar</b> —
              te chamam quando bater a vaga
            </span>
          </div>

          <div class="pitch-row">
            <mdi-sword-cross class="pitch-icon pitch-icon--red" />
            <span class="pitch-key">a plataforma</span>
            <span class="pitch-arrow">→</span>
            <span class="pitch-value">
              <span class="g g-c">recruit party quest</span> —
              <b>PHP 8.5</b> · Laravel · modular monolith + DDD
            </span>
          </div>

          <div class="pitch-row">
            <mdi-github class="pitch-icon" />
            <span class="pitch-key">open source</span>
            <span class="pitch-arrow">→</span>
            <span class="pitch-value">
              github.com/<b>3pontos-tech</b>/recruit-party-quest
            </span>
          </div>
        </div>

        <div class="pitch-note">
          <span class="note-mark">⤷</span>
          é tudo aquilo que a gente acabou de falar —
          <b>módulos, boundaries, eventos</b> — só que num projeto de verdade.
        </div>
      </div>

      <!-- right: QR code placeholder / image -->
      <div class="right-col">
        <div class="qr-block">
          <div class="qr-frame">
            <!-- real image when `qr` prop is set -->
            <img
              v-if="qr"
              class="qr-img"
              :src="qr"
              alt="QR code · recrutamento.3pontos.com"
            />
            <!-- placeholder otherwise -->
            <div v-else class="qr-placeholder">
              <mdi-qrcode class="qr-ph-icon" />
              <div class="qr-ph-label">[ QR CODE ]</div>
              <div class="qr-ph-hint">aponte a câmera</div>
            </div>

            <div class="qr-scanlines" />
            <div class="qr-corner qr-corner--tl">★ SCAN</div>
            <div class="qr-corner qr-corner--br">talento</div>
          </div>

          <div class="qr-caption">
            <span class="cap-dot" />
            <span>cadastra em <b class="qr-url">recrutamento.3pontos.com</b></span>
          </div>
        </div>
      </div>

    </div>

    <!-- footer hint (left empty per convention) -->
    <div class="footer-bar footer-bar--right-only">
      <div class="footer-right">
        <span class="prompt-label">press</span>
        <kbd class="key">SPACE</kbd>
        <span class="next-label">→ de volta pra história</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.recruit-modular {
  position: absolute;
  inset: 0;
  padding: 2.4rem 2.6rem 2rem;
  background: var(--ink);
  color: var(--bone);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  font-family: var(--font-mono);
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
.meta-pipe { color: var(--frame); }
.meta-track b { color: var(--bone); font-weight: 700; }
.meta-fill {
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--frame) 30%, var(--frame) 70%, transparent);
  margin: 0 0.75rem;
}
.meta-handle { color: var(--bone); font-weight: 700; letter-spacing: 0.1em; }
.meta-handle::first-letter { color: var(--red); }

/* -------- body grid -------- */
.body {
  position: relative;
  flex: 1;
  display: grid;
  grid-template-columns: 1fr 16.5rem;
  gap: 2rem;
  align-items: stretch;
  padding: 1rem 0 0.6rem;
  min-height: 0;
}

/* -------- left column -------- */
.left-col {
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
  min-width: 0;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.2s;
}

.title-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.95rem;
  color: #b9b3a9;
  margin-bottom: 0.15rem;
  letter-spacing: 0.01em;
}
.eyebrow-mark { color: var(--red); font-size: 0.6rem; }

.title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 4.6rem;
  line-height: 0.9;
  margin: 0;
  display: flex;
  flex-direction: column;
}
.title-line { display: block; white-space: nowrap; }
.title-line--outline {
  color: transparent;
  -webkit-text-stroke: 1.8px var(--bone);
  opacity: 0.92;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.3s;
}
.title-line--solid {
  color: var(--bone);
  margin-left: 1.6rem;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.45s;
}
.title-q {
  color: var(--red);
  display: inline-block;
  text-shadow: 0 0 22px rgba(255, 45, 32, 0.45);
  margin-left: 0.02em;
}

.title-rule {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  margin: 0.4rem 0 0.1rem 1.6rem;
}
.rule-block {
  width: 42px;
  height: 10px;
  background: var(--red);
  box-shadow: 0 0 18px rgba(255, 45, 32, 0.35);
}
.rule-line {
  flex: 0 0 120px;
  height: 2px;
  background: linear-gradient(to right, var(--red), transparent);
}
.rule-tail {
  font-size: 0.6rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--dim);
}

/* -------- pitch rows -------- */
.pitch {
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  margin-top: 0.3rem;
}
.pitch-row {
  display: grid;
  grid-template-columns: 1.4rem 6rem 1.1rem 1fr;
  align-items: baseline;
  gap: 0.45rem;
  font-size: 0.86rem;
  line-height: 1.4;
  animation: row-in 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.pitch-row:nth-child(1) { animation-delay: 0.55s; }
.pitch-row:nth-child(2) { animation-delay: 0.65s; }
.pitch-row:nth-child(3) { animation-delay: 0.75s; }
.pitch-row:nth-child(4) { animation-delay: 0.85s; }

.pitch-icon {
  font-size: 1rem;
  color: #a8a297;
  align-self: center;
  transform: translateY(1px);
}
.pitch-icon--red { color: var(--red); }
.pitch-key {
  color: var(--dim);
  font-size: 0.74rem;
  letter-spacing: 0.04em;
  text-transform: lowercase;
}
.pitch-arrow {
  color: var(--red);
  font-weight: 700;
  text-align: center;
}
.pitch-value {
  color: #d6d0c4;
  min-width: 0;
}
.pitch-value b { color: var(--bone); font-weight: 700; }
.pitch-sub {
  color: var(--dim);
  font-size: 0.74rem;
}

.pitch-note {
  margin-top: 0.2rem;
  padding-top: 0.7rem;
  border-top: 1px solid var(--rule);
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.98rem;
  color: #b9b3a9;
  line-height: 1.45;
  animation: fade-in 0.6s ease both;
  animation-delay: 1s;
}
.pitch-note b {
  color: var(--bone);
  font-family: var(--font-mono);
  font-style: normal;
  font-weight: 700;
  font-size: 0.86em;
  letter-spacing: 0.01em;
}
.note-mark {
  color: var(--red);
  font-family: var(--font-mono);
  font-style: normal;
  margin-right: 0.3rem;
}

/* -------- right column / QR -------- */
.right-col {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-width: 0;
  animation: slide-up 0.6s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.5s;
}

.qr-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.7rem;
}

.qr-frame {
  position: relative;
  width: 14rem;
  height: 14rem;
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
  animation: qr-jitter 11s infinite both;
}

.qr-img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
  background: var(--bone);
  padding: 0.6rem;
}

.qr-placeholder {
  position: absolute;
  inset: 0.85rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.4rem;
  border: 1.5px dashed rgba(245, 241, 234, 0.35);
  border-radius: 3px;
  color: var(--dim);
}
.qr-ph-icon {
  font-size: 3.4rem;
  color: rgba(245, 241, 234, 0.55);
}
.qr-ph-label {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.16em;
  color: var(--bone);
}
.qr-ph-hint {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.82rem;
  color: var(--dim);
}

.qr-scanlines {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-image: repeating-linear-gradient(
    0deg,
    transparent 0 2px,
    rgba(0, 0, 0, 0.22) 2px 3px
  );
  mix-blend-mode: multiply;
  opacity: 0.5;
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

.qr-caption {
  display: flex;
  align-items: center;
  gap: 0.45rem;
  font-size: 0.64rem;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--dim);
}
.qr-caption b { font-weight: 700; }
.qr-url {
  color: var(--red);
  letter-spacing: 0.02em;
  text-transform: none;
}
.cap-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--red);
  box-shadow: 0 0 8px rgba(255, 45, 32, 0.7);
  animation: cap-blink 1.4s steps(1) infinite;
}

/* -------- footer -------- */
.footer-bar {
  position: relative;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  margin-top: 0.4rem;
  padding-top: 0.55rem;
  border-top: 1px solid var(--rule);
  font-size: 0.66rem;
  letter-spacing: 0.12em;
  animation: fade-in 0.55s ease both;
  animation-delay: 1.2s;
}
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
  font-family: var(--font-serif);
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

/* -------- local keyframes (entrance + frame jitter) -------- */
@keyframes row-in {
  from { opacity: 0; transform: translateY(6px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes cap-blink { 50% { opacity: 0.25; } }

@keyframes qr-jitter {
  0%, 40%   { transform: none; filter: none; }
  41%       { transform: translateX(-3px); filter: hue-rotate(20deg) saturate(1.4); }
  42%       { transform: translateX(4px) skewY(-0.5deg); }
  43%       { transform: translateX(-2px); filter: contrast(1.3) saturate(0.6); }
  44%, 100% { transform: none; filter: none; }
}
</style>
