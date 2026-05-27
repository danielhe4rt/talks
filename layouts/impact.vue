<!--
  Impact layout — dramatic full-screen for numbers, statements, core messages.
  Features a subtle radial glow behind the main content.

  Usage:
  ```md
  ---
  layout: impact
  color: red     # red | yellow | green | blue | purple (default: yellow)
  ---

  # 487

  arquivos PHP · 19 diretórios · 0 boundaries
  ```
-->

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps({
  color: { type: String, default: 'yellow' },
  class: { type: String },
})

const glowColors = {
  red: 'rgba(239, 68, 68, 0.08)',
  yellow: 'rgba(234, 179, 8, 0.08)',
  green: 'rgba(34, 197, 94, 0.08)',
  blue: 'rgba(59, 130, 246, 0.08)',
  purple: 'rgba(168, 85, 247, 0.08)',
}

const accentColors = {
  red: '#ef4444',
  yellow: '#eab308',
  green: '#22c55e',
  blue: '#3b82f6',
  purple: '#a855f7',
}

const glowStyle = computed(() => ({
  '--impact-glow': glowColors[props.color] || glowColors.yellow,
  '--impact-accent': accentColors[props.color] || accentColors.yellow,
}))
</script>

<template>
  <div class="slidev-layout impact" :style="glowStyle" :class="$props.class">
    <div class="impact__glow" />
    <div class="impact__content">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.impact {
  position: relative;
  display: grid;
  place-items: center;
  height: 100%;
  width: 100%;
  text-align: center;
  overflow: hidden;
}

.impact__glow {
  position: absolute;
  inset: 0;
  background: radial-gradient(
    ellipse 60% 50% at 50% 45%,
    var(--impact-glow) 0%,
    transparent 70%
  );
  pointer-events: none;
}

.impact__content {
  position: relative;
  z-index: 1;
  max-width: 85%;
}

.impact :deep(h1) {
  font-size: 7rem;
  font-weight: 800;
  line-height: 1;
  letter-spacing: -0.04em;
  color: var(--impact-accent);
  margin-bottom: 0.25rem;
}

.impact :deep(h1 + p) {
  font-size: 1.25rem;
  opacity: 0.5;
  font-weight: 500;
  letter-spacing: 0.02em;
  margin-top: 0.5rem;
}

.impact :deep(h1 + p + *) {
  margin-top: 2rem;
}
</style>
