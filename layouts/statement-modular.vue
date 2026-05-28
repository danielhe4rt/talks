<!--
  statement-modular — emotional turn / "what now?" slides.

  A bold prompt followed by progressive reveals (use <v-clicks>). Tuned
  for slides that build tension via successive lines (e.g., the virada
  slide listing "Desiste? / Reescreve? / Finge que não viu?").

  Slot:
    default — the markdown content, typically with <v-clicks> blocks.

  Frontmatter:
    ---
    layout: statement-modular
    metaNumber: "07"
    metaSection: "ABERTURA"
    metaSubtitle: "a virada"
    eyebrow: "and now?"
    accent: "?"
    ---
-->
<script setup lang="ts">
defineProps<{
  metaNumber?: string
  metaSection?: string
  metaSubtitle?: string
  metaRight?: string
  eyebrow?: string
  accent?: string
  vignettePos?: 'tr' | 'br' | 'tl' | 'bl'
}>()
</script>

<template>
  <div class="brutalist-statement">
    <BgLayers :vignette-pos="vignettePos || 'tr'" />

    <MetaBar
      v-if="metaNumber || metaSection"
      :number="metaNumber"
      :section="metaSection"
      :subtitle="metaSubtitle"
      :right="metaRight"
    />

    <div class="statement-body">
      <div v-if="eyebrow" class="statement-eyebrow">
        <span class="eyebrow-mark">◆</span>
        <span>{{ eyebrow }}</span>
      </div>

      <div class="statement-content">
        <slot />
      </div>
    </div>
  </div>
</template>

<style scoped>
.brutalist-statement {
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

.statement-body {
  position: relative;
  flex: 1;
  min-height: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 90%;
}

.statement-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.1rem;
  color: #b9b3a9;
  margin-bottom: 0.6rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.2s;
}
.eyebrow-mark { color: var(--red); font-size: 0.7rem; transform: translateY(-1px); }

.statement-content {
  font-family: var(--font-mono);
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.35s;
}

/* The h1 is the punch line — brutalist display, no nonsense */
.statement-content :deep(h1) {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 4.4rem;
  line-height: 0.95;
  color: var(--bone);
  margin: 0 0 1.4rem;
  letter-spacing: -0.005em;
}
.statement-content :deep(h1 code) {
  font-family: var(--font-mono);
  background: rgba(255, 45, 32, 0.1);
  border: 1px solid rgba(255, 45, 32, 0.3);
  color: var(--bone);
  padding: 0.08em 0.35em;
  border-radius: 3px;
  font-size: 0.55em;
  font-weight: 700;
}
.statement-content :deep(p) {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.5rem;
  color: #c8c2b6;
  line-height: 1.4;
  margin: 0 0 0.5rem;
}
.statement-content :deep(strong),
.statement-content :deep(b) { color: var(--bone); font-style: normal; }

/* progressive reveal items get a subtle red-square marker */
.statement-content :deep(.v-click),
.statement-content :deep(p) {
  position: relative;
}
.statement-content :deep(div) { line-height: 1.5; }
</style>
