<!--
  impact-modular — single bold statement / number / one-liner.

  Used for moments where one big claim needs to land. Replaces the
  legacy `impact` layout. Optional accent color via prop.

  Frontmatter:
    ---
    layout: impact-modular
    metaNumber: "06"
    metaSection: "ABERTURA"
    metaSubtitle: "the index.php meme"
    color: red    # red (default) | yellow | green | blue | purple
    ---
-->
<script setup lang="ts">
defineProps<{
  metaNumber?: string
  metaSection?: string
  metaSubtitle?: string
  metaRight?: string
  metaPhase?: 'red' | 'refactor' | 'green' | 'diagnostico'
  color?: 'red' | 'yellow' | 'green' | 'blue' | 'purple'
  vignettePos?: 'tr' | 'br' | 'tl' | 'bl'
}>()
</script>

<template>
  <div class="brutalist-impact" :data-color="color || 'red'">
    <BgLayers :vignette-pos="vignettePos || 'tr'" />

    <MetaBar
      v-if="metaNumber || metaSection"
      :number="metaNumber"
      :section="metaSection"
      :subtitle="metaSubtitle"
      :right="metaRight"
      :phase="metaPhase"
    />

    <div class="impact-body">
      <div class="impact-glow" />
      <div class="impact-content">
        <slot />
      </div>
    </div>
  </div>
</template>

<style scoped>
.brutalist-impact {
  position: absolute;
  inset: 0;
  padding: 2.4rem 2.6rem 2rem;
  background: var(--ink);
  color: var(--bone);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  font-family: var(--font-mono);

  --impact-color: var(--red);
}
.brutalist-impact[data-color="yellow"] { --impact-color: var(--accent-orange); }
.brutalist-impact[data-color="green"]  { --impact-color: var(--accent-green); }
.brutalist-impact[data-color="blue"]   { --impact-color: var(--accent-blue); }
.brutalist-impact[data-color="purple"] { --impact-color: var(--accent-purple); }

.impact-body {
  position: relative;
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.impact-glow {
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at 50% 50%, color-mix(in oklab, var(--impact-color), transparent 75%), transparent 60%);
  pointer-events: none;
  animation: fade-in 0.8s ease both;
}

.impact-content {
  position: relative;
  z-index: 1;
  max-width: 80%;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.25s;
}

.impact-content :deep(h1) {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 7rem;
  line-height: 0.9;
  color: var(--impact-color);
  margin: 0;
  letter-spacing: -0.015em;
  text-shadow: 0 0 40px color-mix(in oklab, var(--impact-color), transparent 60%);
}
.impact-content :deep(h1 code) {
  font-family: var(--font-mono);
  background: transparent;
  border: none;
  color: var(--impact-color);
}
.impact-content :deep(p) {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.6rem;
  color: #b9b3a9;
  line-height: 1.35;
  margin: 1.2rem 0 0;
}
.impact-content :deep(pre),
.impact-content :deep(code) {
  font-family: var(--font-mono);
}
</style>
