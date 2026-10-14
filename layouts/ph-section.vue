<script setup lang="ts">
// Generic PHPeste content slide: topbar, header (default slot: eyebrow + h1 +
// one paragraph), body (::content::), footer hint and the azulejo stripe.
// `tone` alternates the section colours like the event site does.
withDefaults(defineProps<{
  tone?: 'espresso' | 'orange' | 'sand'
  eyebrow?: string
  hint?: string
  meta?: string
}>(), {
  tone: 'sand',
  meta: '@danielhe4rt',
})
</script>

<template>
  <div class="ph-slide ph-section" :class="`ph-slide--${tone}`">
    <header class="ph-topbar ph-rise">
      <img
        class="ph-topbar__logo"
        :src="tone === 'espresso' ? '/images/phpeste-logo-cream.png' : '/images/phpeste-logo-espresso.png'"
        alt="PHPeste 2026"
      >
      <span class="ph-topbar__fill" />
      <span v-if="meta" class="ph-topbar__meta">{{ meta }}</span>
    </header>

    <div class="ph-section__head ph-rise ph-rise--1">
      <p v-if="eyebrow" class="ph-eyebrow">{{ eyebrow }}</p>
      <slot />
    </div>

    <div class="ph-section__content ph-rise ph-rise--2">
      <slot name="content" />
    </div>

    <footer v-if="hint" class="ph-footer ph-section__footer ph-rise ph-rise--4">
      <span />
      <span class="ph-hint">aperte <kbd class="ph-kbd">espaço</kbd> <i>→ {{ hint }}</i></span>
    </footer>
    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-section__head {
  display: grid;
  grid-template-columns: auto 1fr;
  grid-template-areas: "eyebrow eyebrow" "title note";
  column-gap: 2rem;
  align-items: end;
  padding: 0.9rem 2.6rem 0;
}
.ph-section__head .ph-eyebrow { grid-area: eyebrow; margin-bottom: 0.2rem; }
.ph-slide--orange .ph-section__head .ph-eyebrow,
.ph-slide--sand .ph-section__head .ph-eyebrow { color: var(--ph-espresso); }
.ph-section__head h1 {
  grid-area: title;
  margin: 0;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 3.2rem;
  line-height: 1;
}
.ph-slide--espresso .ph-section__head h1 { color: var(--ph-off-white); text-shadow: 2px 3px 0 rgba(0, 0, 0, 0.4); }
.ph-section__head p:not(.ph-eyebrow) {
  grid-area: note;
  justify-self: end;
  margin: 0 0 0.35rem;
  max-width: 19rem;
  padding-left: 0.9rem;
  border-left: 4px solid var(--ph-crimson);
  font-size: 1.05rem;
  line-height: 1.35;
}
.ph-slide--espresso .ph-section__head p:not(.ph-eyebrow) { border-left-color: var(--ph-orange); }
.ph-section__head strong { font-weight: 600; }

.ph-section__content {
  flex: 1;
  min-height: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 1rem 2.6rem 0.8rem;
}

.ph-section__footer { padding-bottom: 0.8rem; }
.ph-section .ph-hint i {
  font-family: var(--ph-font-body);
  font-size: 0.95rem;
  letter-spacing: 0;
  text-transform: none;
}

/* grid helper for card rows */
.ph-grid {
  display: grid;
  grid-template-columns: repeat(var(--cols, 4), 1fr);
  gap: 1.1rem;
}
</style>
