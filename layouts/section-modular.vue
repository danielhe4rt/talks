<!--
  section-modular — act / section divider.

  Drop in massive number + outlined/solid title with red rule.
  Used for "01 O LEGADÃO", "02 EXTRAÇÃO" style transitions.

  Frontmatter:
    ---
    layout: section-modular
    actNumber: "01"
    actLabel:  "ato 01 de 04"
    eyebrow:   "primeiro ato"
    outlined:  "O"
    solid:     "LEGADÃO"
    accent:    "."
    tail:      "~5 min"
    next:      "pastas"   # optional
    ---
-->
<script setup lang="ts">
defineProps<{
  actNumber?: string
  actLabel?: string
  eyebrow?: string
  outlined?: string
  solid?: string
  accent?: string
  tail?: string
  next?: string
}>()
</script>

<template>
  <div class="brutalist-section">
    <BgLayers vignette-pos="bl" />

    <MetaBar
      :number="actNumber"
      section="ATO"
      :subtitle="actLabel"
    />

    <div class="section-body">
      <div class="act-big-num">{{ actNumber }}</div>

      <TitleBlock
        :eyebrow="eyebrow"
        :outlined="outlined"
        :solid="solid"
        :accent="accent"
        :tail="tail"
        size="cover"
      />

      <div class="section-slot">
        <slot />
      </div>
    </div>

    <FooterBar v-if="next" :next="next" />
  </div>
</template>

<style scoped>
.brutalist-section {
  position: absolute;
  inset: 0;
  padding: 2.6rem 2.6rem 2.1rem;
  background: var(--ink);
  color: var(--bone);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  font-family: var(--font-mono);
}

.section-body {
  position: relative;
  flex: 1;
  min-height: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.act-big-num {
  position: absolute;
  top: 0;
  right: 0;
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 16rem;
  line-height: 0.82;
  color: var(--red);
  opacity: 0.14;
  letter-spacing: -0.03em;
  pointer-events: none;
  text-shadow: 0 0 60px rgba(255, 45, 32, 0.2);
  font-variant-numeric: tabular-nums;
  animation: slide-up 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.15s;
}

.section-slot {
  margin-top: 1.4rem;
  font-family: var(--font-mono);
  color: #c8c2b6;
  max-width: 80%;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 1.05s;
}
.section-slot :deep(p) {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.4rem;
  color: #b9b3a9;
  line-height: 1.35;
  margin: 0 0 0.5rem;
}
.section-slot :deep(strong) { color: var(--bone); font-style: normal; }
.section-slot :deep(h2) {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 0.9rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--dim);
  margin: 0 0 0.6rem;
}
</style>
