<script setup lang="ts">
// Big number / verdict slide. Default slot: h1 (the number), a first
// paragraph (stats line), then free blocks — `.ph-impact__q` for the
// question and `.ph-impact__punch` for the stamped answer card.
withDefaults(defineProps<{
  tone?: 'orange' | 'espresso' | 'crimson' | 'sand'
  size?: 'number' | 'statement'
  eyebrow?: string
  meta?: string
}>(), {
  tone: 'orange',
  size: 'number',
})
</script>

<template>
  <div class="ph-slide ph-impact" :class="[`ph-slide--${tone}`, `ph-impact--${size}`]">
    <header class="ph-topbar">
      <img
        class="ph-topbar__logo"
        :src="tone === 'orange' || tone === 'sand' ? '/images/phpeste-logo-espresso.png' : '/images/phpeste-logo-cream.png'"
        alt="PHPeste 2026"
      >
      <span class="ph-topbar__fill" />
      <span v-if="meta" class="ph-topbar__meta">{{ meta }}</span>
    </header>

    <div class="ph-impact__body">
      <span v-if="eyebrow" class="ph-eyebrow ph-impact__eyebrow">{{ eyebrow }}</span>
      <slot />
    </div>

    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-impact__body {
  flex: 1;
  min-height: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.9rem;
  padding: 0 2.6rem 1.6rem;
  text-align: center;
}
.ph-impact__body h1 {
  margin: 0;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 10rem;
  line-height: 0.85;
  color: var(--ph-espresso);
  text-shadow: 6px 6px 0 var(--ph-yellow);
}
.ph-slide--espresso .ph-impact__body h1,
.ph-slide--crimson .ph-impact__body h1 { color: var(--ph-yellow); text-shadow: 6px 6px 0 var(--ph-black); }

.ph-impact--statement .ph-impact__body h1 {
  font-size: 3.8rem;
  line-height: 1.02;
  text-shadow: 4px 4px 0 var(--ph-yellow);
  max-width: 50rem;
}
.ph-impact--statement .ph-impact__body > p:first-of-type {
  font-family: var(--ph-font-body);
  font-size: 1.5rem;
  font-weight: 400;
  letter-spacing: 0;
  text-transform: none;
}
.ph-impact__eyebrow { font-size: 1.2rem; }
.ph-slide--orange .ph-impact__eyebrow,
.ph-slide--sand .ph-impact__eyebrow { color: var(--ph-espresso); }
.ph-slide--sand .ph-impact__q strong { text-decoration-color: var(--ph-crimson); }
.ph-impact__body > p:first-of-type {
  margin: 0;
  font-family: var(--ph-font-ui);
  font-size: 1rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  text-transform: uppercase;
}

.ph-impact__q {
  margin: 0.4rem 0 0;
  font-size: 1.55rem;
  line-height: 1.35;
}
.ph-impact__q strong,
.ph-impact__punch strong {
  font-weight: 600;
  text-decoration: underline;
  text-decoration-thickness: 4px;
  text-underline-offset: 5px;
}
.ph-slide--orange .ph-impact__q strong { text-decoration-color: var(--ph-yellow); }

.ph-impact__punch {
  margin-top: 0.4rem;
  padding: 0.8rem 1.4rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-radius: 4px;
  box-shadow: 6px 6px 0 var(--ph-espresso);
  font-size: 1.25rem;
  line-height: 1.4;
}
.ph-impact__punch strong { text-decoration-color: var(--ph-crimson); }
</style>
