<script setup lang="ts">
withDefaults(defineProps<{
  date?: string
  city?: string
  track?: string
  speaker?: string
  handle?: string
  role?: string
}>(), {
  date: 'Sexta · 16 de outubro de 2026',
  city: 'São Luís · MA',
  track: 'Arquitetura',
  speaker: 'Daniel Reis',
  handle: '@danielhe4rt',
  role: 'senior swe @ scopeyonsite',
})
</script>

<template>
  <div class="ph-slide ph-slide--espresso ph-cover">
    <!-- river/wave from the event hero: decorative only -->
    <svg class="ph-cover__wave" viewBox="0 0 600 400" aria-hidden="true">
      <path d="M-20 330 C 120 250, 210 380, 330 300 S 520 150, 640 210" />
    </svg>

    <header class="ph-topbar ph-rise">
      <img class="ph-topbar__logo" src="/images/phpeste-logo-cream.png" alt="PHPeste 2026">
      <span class="ph-topbar__fill" />
      <span class="ph-topbar__meta">
        <mdi-map-marker-outline aria-hidden="true" />{{ city }}
      </span>
      <span class="ph-pill ph-cover__track">
        <mdi-bank-outline aria-hidden="true" />{{ track }}
      </span>
    </header>

    <div class="ph-cover__body">
      <div class="ph-cover__main">
        <p class="ph-stamp ph-rise ph-rise--1">{{ date }}</p>
        <slot />
      </div>

      <aside v-if="$slots.aside" class="ph-cover__aside ph-rise ph-rise--3">
        <slot name="aside" />
      </aside>
    </div>

    <footer class="ph-footer ph-rise ph-rise--4">
      <div>
        <p class="ph-footer__name">{{ speaker }} <span class="ph-cover__handle">{{ handle }}</span></p>
        <p class="ph-footer__sub">{{ role }}</p>
      </div>
      <span class="ph-hint" aria-hidden="true">aperte <kbd class="ph-kbd">espaço</kbd></span>
    </footer>
    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-cover__wave {
  position: absolute;
  right: -4rem;
  bottom: -2rem;
  width: 44rem;
  fill: none;
  stroke: var(--ph-orange);
  stroke-width: 46;
  stroke-linecap: round;
  opacity: 0.1;
  pointer-events: none;
}

.ph-cover__track { color: var(--ph-yellow); }

.ph-cover__body {
  position: relative;
  z-index: 1;
  flex: 1;
  display: grid;
  grid-template-columns: 1fr 17rem;
  gap: 2.4rem;
  align-items: center;
  padding: 0 2.6rem;
  min-height: 0;
}

.ph-cover__main { display: flex; flex-direction: column; align-items: flex-start; gap: 0.9rem; }

/* default slot: eyebrow paragraph, h1, subtitle paragraph */
.ph-cover__main h1 {
  margin: 0;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 4.3rem;
  line-height: 0.95;
  color: var(--ph-off-white);
  text-shadow: 2px 3px 0 rgba(0, 0, 0, 0.4);
  animation: ph-rise 0.6s 0.25s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.ph-cover__main h1 em {
  display: block;
  font-style: normal;
  color: var(--ph-orange);
}
.ph-cover__main p:not(.ph-stamp) {
  margin: 0;
  max-width: 36rem;
  font-size: 1.35rem;
  line-height: 1.4;
  color: var(--ph-sand-lt);
  animation: ph-rise 0.6s 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.ph-cover__main p.ph-eyebrow {
  font-size: 1.1rem;
  font-style: italic;
  color: var(--ph-sand);
  margin-bottom: -0.4rem;
}
.ph-cover__main strong {
  font-weight: 600;
  color: var(--ph-yellow);
  text-decoration: underline;
  text-decoration-thickness: 3px;
  text-underline-offset: 5px;
  text-decoration-color: var(--ph-crimson);
}

.ph-cover__handle {
  margin-left: 0.5rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  text-transform: none;
  color: var(--ph-orange);
}
.ph-cover .ph-footer__sub { color: var(--ph-sand); }
.ph-cover .ph-hint { color: var(--ph-sand); }
</style>
