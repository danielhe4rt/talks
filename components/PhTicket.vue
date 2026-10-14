<script setup lang="ts">
// Off-white card with a yellow top edge — the "Lote 3" ticket card from the
// PHPeste 2026 site. Use inside ph-* layouts.
defineProps<{
  label?: string
  title?: string
}>()
</script>

<template>
  <section class="ph-ticket">
    <p v-if="label" class="ph-ticket__label">{{ label }}</p>
    <h2 v-if="title" class="ph-ticket__title">{{ title }}</h2>
    <div class="ph-ticket__body">
      <slot />
    </div>
  </section>
</template>

<style>
.ph-ticket {
  position: relative;
  padding: 1.1rem 1.2rem 1.2rem;
  background: var(--ph-off-white, #faf6ef);
  color: var(--ph-espresso, #231208);
  border-radius: 4px;
  border-top: 5px solid var(--ph-yellow, #f5c828);
  box-shadow: 0 10px 32px rgba(0, 0, 0, 0.35);
}
.ph-ticket__label {
  margin: 0;
  font-family: var(--ph-font-ui);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}
.ph-ticket__title {
  margin: 0.3rem 0 0.7rem;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 1.7rem;
  line-height: 1.05;
  color: var(--ph-crimson, #a52830);
}
.ph-ticket__body { font-size: 0.95rem; }
.ph-ticket__body pre {
  margin: 0;
  font-family: var(--ph-font-mono);
  font-size: 0.85rem;
  line-height: 1.55;
  white-space: pre;
}
.ph-ticket__body p { margin: 0.6rem 0 0; font-style: italic; }
.ph-ticket__list { margin: 0; padding: 0; list-style: none; counter-reset: q; }
.ph-ticket__list li {
  counter-increment: q;
  display: flex;
  align-items: baseline;
  gap: 0.6rem;
  padding: 0.35rem 0;
  font-weight: 600;
}
.ph-ticket__list li + li { border-top: 1.5px dashed var(--ph-sand, #c4a07a); }
.ph-ticket__list li::before {
  content: counter(q, decimal-leading-zero);
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 1.2rem;
  color: var(--ph-crimson, #a52830);
}
.ph-ticket__body .ph-qr { display: block; margin-top: -0.2rem; width: 100%; height: auto; border-radius: 4px; }
.ph-ticket__body .ph-qr-url { font-style: normal; font-size: 0.72rem; font-weight: 600; text-align: center; }
</style>
