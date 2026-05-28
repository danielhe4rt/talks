<!--
  brutalist-base — the universal modular layout.

  Use this layout for any slide that doesn't need a specialized structure.
  Provides:
    - BgLayers (grid + vignette + grain)
    - MetaBar at top (configurable via frontmatter props)
    - centered content slot for your markdown
    - optional FooterBar (off by default — pass `next` to enable)

  Frontmatter example:
    ---
    layout: brutalist-base
    metaNumber: "05"
    metaSection: "ABERTURA"
    metaSubtitle: "o legadão"
    metaRight: "ato 01/04"
    contentAlign: "center"   # center (default) | top | between
    ---
-->
<script setup lang="ts">
defineProps<{
  metaNumber?: string
  metaSection?: string
  metaSubtitle?: string
  metaRight?: string
  vignettePos?: 'tr' | 'br' | 'tl' | 'bl'
  next?: string
  contentAlign?: 'top' | 'center' | 'between'
}>()
</script>

<template>
  <div class="brutalist-base">
    <BgLayers :vignette-pos="vignettePos" />

    <MetaBar
      v-if="metaNumber || metaSection || metaRight"
      :number="metaNumber"
      :section="metaSection"
      :subtitle="metaSubtitle"
      :right="metaRight"
    />

    <div class="brutalist-content" :data-align="contentAlign || 'center'">
      <slot />
    </div>

    <FooterBar v-if="next" :next="next" />
  </div>
</template>

<style scoped>
.brutalist-base {
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

.brutalist-content {
  position: relative;
  flex: 1;
  min-height: 0;
  display: flex;
  flex-direction: column;
}
.brutalist-content[data-align="center"]  { justify-content: center; }
.brutalist-content[data-align="top"]     { justify-content: flex-start; padding-top: 0.6rem; }
.brutalist-content[data-align="between"] { justify-content: space-between; }

/* Style markdown content rendered into the slot for a sensible default look */
.brutalist-content :deep(h1) {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 3.6rem;
  line-height: 0.95;
  color: var(--bone);
  margin: 0 0 0.6rem;
  letter-spacing: -0.005em;
}
.brutalist-content :deep(h1 code) {
  font-family: var(--font-mono);
  background: rgba(255, 45, 32, 0.1);
  border: 1px solid rgba(255, 45, 32, 0.3);
  color: var(--bone);
  padding: 0.08em 0.35em;
  border-radius: 3px;
  font-size: 0.7em;
  font-weight: 700;
}
.brutalist-content :deep(h2) {
  font-family: var(--font-serif);
  font-style: italic;
  font-weight: 400;
  font-size: 1.45rem;
  color: #b9b3a9;
  margin: 0 0 1.1rem;
  letter-spacing: 0.005em;
}
.brutalist-content :deep(p) {
  color: #c8c2b6;
  line-height: 1.5;
  margin: 0 0 0.6rem;
}
.brutalist-content :deep(strong),
.brutalist-content :deep(b) { color: var(--bone); }
.brutalist-content :deep(code) {
  font-family: var(--font-mono);
  background: rgba(20, 20, 24, 0.6);
  border: 1px solid var(--frame);
  padding: 0.05em 0.35em;
  border-radius: 3px;
  font-size: 0.92em;
}
.brutalist-content :deep(pre) {
  background: rgba(10, 10, 12, 0.7);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 4px;
}
.brutalist-content :deep(a) {
  color: var(--red);
  text-decoration: none;
  border-bottom: 1px dashed rgba(255, 45, 32, 0.5);
}
.brutalist-content :deep(blockquote) {
  border-left: 3px solid var(--red);
  padding: 0.4rem 0.9rem;
  font-style: italic;
  font-family: var(--font-serif);
  color: #b9b3a9;
  margin: 0.8rem 0;
}
</style>
