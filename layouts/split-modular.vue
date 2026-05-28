<!--
  split-modular — two-column "before / after" comparison.

  Replaces the legacy `split-compare` layout. Uses ::before:: and ::after::
  slot syntax for Slidev. Each side has a labeled corner, a red rule, and
  tinted background (red for before, green-ish for after).

  Frontmatter:
    ---
    layout: split-modular
    metaNumber: "14"
    metaSection: "EXTRAÇÃO"
    metaSubtitle: "events"
    beforeLabel: ACOPLADO
    afterLabel: DESACOPLADO
    ---

    # title in markdown body

    ::before::
    ... before content ...

    ::after::
    ... after content ...
-->
<script setup lang="ts">
defineProps<{
  metaNumber?: string
  metaSection?: string
  metaSubtitle?: string
  metaRight?: string
  beforeLabel?: string
  afterLabel?: string
}>()
</script>

<template>
  <div class="brutalist-split">
    <BgLayers vignette-pos="br" />

    <MetaBar
      v-if="metaNumber || metaSection"
      :number="metaNumber"
      :section="metaSection"
      :subtitle="metaSubtitle"
      :right="metaRight"
    />

    <div class="split-title">
      <slot />
    </div>

    <div class="split-body">
      <div class="split-side split-side--before">
        <div class="side-corner">
          <span class="corner-block" />
          <span class="corner-label">{{ beforeLabel || 'ANTES' }}</span>
        </div>
        <div class="side-content">
          <slot name="before" />
        </div>
      </div>

      <div class="split-divider">
        <span class="divider-mark">▶</span>
      </div>

      <div class="split-side split-side--after">
        <div class="side-corner">
          <span class="corner-block corner-block--green" />
          <span class="corner-label corner-label--green">{{ afterLabel || 'DEPOIS' }}</span>
        </div>
        <div class="side-content">
          <slot name="after" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.brutalist-split {
  position: absolute;
  inset: 0;
  padding: 2.2rem 2.4rem 1.8rem;
  background: var(--ink);
  color: var(--bone);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  font-family: var(--font-mono);
}

.split-title {
  margin-top: 0.7rem;
  margin-bottom: 0.6rem;
  flex: 0 0 auto;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.15s;
}
.split-title :deep(h1) {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 1.3rem;
  letter-spacing: 0.02em;
  color: var(--bone);
  margin: 0 0 0.3rem;
}
.split-title :deep(h1 .text-green-400) { color: var(--accent-green); }
.split-title :deep(h1 .text-red-400)   { color: var(--red); }
.split-title :deep(p) {
  color: #b9b3a9;
  font-family: var(--font-serif);
  font-style: italic;
  margin: 0;
  font-size: 0.95rem;
}

.split-body {
  flex: 1;
  display: grid;
  grid-template-columns: 1fr 1.5rem 1fr;
  gap: 0;
  min-height: 0;
  align-items: stretch;
}

.split-side {
  position: relative;
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 3px;
  background:
    linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75));
  padding: 1.1rem 1rem 0.9rem;
  display: flex;
  flex-direction: column;
  min-width: 0;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.split-side--before {
  background:
    radial-gradient(ellipse at 0% 100%, rgba(255, 45, 32, 0.08), transparent 60%),
    linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75));
  border-color: rgba(255, 45, 32, 0.18);
  animation-delay: 0.25s;
}
.split-side--after {
  background:
    radial-gradient(ellipse at 100% 100%, rgba(110, 231, 161, 0.08), transparent 60%),
    linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75));
  border-color: rgba(110, 231, 161, 0.2);
  animation-delay: 0.4s;
}

.side-corner {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  margin-bottom: 0.55rem;
}
.corner-block {
  width: 22px;
  height: 8px;
  background: var(--red);
  box-shadow: 0 0 14px rgba(255, 45, 32, 0.4);
}
.corner-block--green {
  background: var(--accent-green);
  box-shadow: 0 0 14px rgba(110, 231, 161, 0.35);
}
.corner-label {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 0.68rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--red);
}
.corner-label--green { color: var(--accent-green); }

.side-content {
  flex: 1;
  min-height: 0;
  overflow: hidden;
}
.side-content :deep(pre) {
  margin: 0;
  background: transparent;
  border: none;
  font-size: 0.7rem;
  line-height: 1.45;
}
.side-content :deep(.shiki) { background: transparent !important; }

.split-divider {
  display: flex;
  align-items: center;
  justify-content: center;
}
.divider-mark {
  color: var(--red);
  font-family: var(--font-mono);
  font-size: 1.2rem;
  opacity: 0.55;
  animation: divider-pulse 2.2s ease-in-out infinite;
}

@keyframes divider-pulse {
  0%, 100% { opacity: 0.35; transform: translateX(0); }
  50%      { opacity: 0.85; transform: translateX(2px); }
}
</style>
