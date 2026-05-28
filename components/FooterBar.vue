<!--
  FooterBar — optional bottom strip.

  Default behaviour:
    Right-aligned "press SPACE → next" with a kbd-styled key.

  When `next` is empty, the right side is hidden — useful for slides
  that don't need any footer at all (then prefer omitting the component
  entirely instead).

  Slot `left` lets a slide override the left side with custom content.

  IMPORTANT:
    Only the cover and whoami should show personal identity here.
    From toctree onward, leave the left side empty.
-->
<script setup lang="ts">
defineProps<{
  next?: string
}>()
</script>

<template>
  <div class="footer-bar" :class="{ 'footer-bar--right-only': !$slots.left }">
    <div v-if="$slots.left" class="footer-left">
      <slot name="left" />
    </div>
    <div v-if="next" class="footer-right">
      <span class="prompt-label">press</span>
      <kbd class="key">SPACE</kbd>
      <span class="next-label">→ {{ next }}</span>
    </div>
  </div>
</template>

<style scoped>
.footer-bar {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.85rem;
  padding-top: 0.55rem;
  border-top: 1px solid var(--rule);
  font-family: var(--font-mono);
  font-size: 0.68rem;
  letter-spacing: 0.12em;
  animation: fade-in 0.55s ease both;
  animation-delay: 1.2s;
}
.footer-bar--right-only { justify-content: flex-end; }

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
</style>
