<script setup lang="ts">
// Act divider: crimson section (the site's "Ingressos" block), giant stamped
// act number, h1 + one line from the default slot, and an act tracker.
import { computed } from 'vue'

const props = withDefaults(defineProps<{
  act: string
  total?: number
  eyebrow?: string
  duration?: string
}>(), {
  total: 4,
})

const current = computed(() => Number.parseInt(props.act, 10))
</script>

<template>
  <div class="ph-slide ph-slide--crimson ph-act">
    <header class="ph-topbar ph-rise">
      <img class="ph-topbar__logo" src="/images/phpeste-logo-cream.png" alt="PHPeste 2026">
      <span class="ph-topbar__fill" />
      <ol class="ph-act__tracker" :aria-label="`Ato ${current} de ${total}`">
        <li
          v-for="n in total"
          :key="n"
          :class="{ 'is-done': n < current, 'is-current': n === current }"
          aria-hidden="true"
        />
      </ol>
      <span class="ph-topbar__meta">ato {{ act }} de {{ String(total).padStart(2, '0') }}</span>
    </header>

    <div class="ph-act__body">
      <span class="ph-act__num ph-rise ph-rise--1" aria-hidden="true">{{ act }}</span>
      <div class="ph-act__text ph-rise ph-rise--2">
        <p v-if="eyebrow" class="ph-eyebrow">{{ eyebrow }}</p>
        <slot />
        <span v-if="duration" class="ph-act__duration">{{ duration }}</span>
      </div>
    </div>

    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-act__tracker {
  display: flex;
  gap: 0.5rem;
  margin: 0 0.4rem 0 0;
  padding: 0;
  list-style: none;
}
.ph-act__tracker li {
  width: 0.7rem;
  height: 0.7rem;
  border: 2px solid var(--ph-off-white);
  transform: rotate(45deg);
}
.ph-act__tracker li.is-done { background: var(--ph-off-white); opacity: 0.55; }
.ph-act__tracker li.is-current { background: var(--ph-yellow); border-color: var(--ph-yellow); }

.ph-act__body {
  flex: 1;
  display: grid;
  grid-template-columns: auto 1fr;
  align-items: center;
  gap: 2.4rem;
  padding: 0 2.6rem 1.4rem;
  min-height: 0;
}
.ph-act__num {
  font-family: var(--ph-font-display);
  font-size: 15rem;
  line-height: 0.8;
  color: var(--ph-yellow);
  text-shadow: 6px 6px 0 var(--ph-espresso);
}
.ph-act__text { display: flex; flex-direction: column; align-items: flex-start; gap: 0.8rem; }
.ph-act .ph-eyebrow { color: var(--ph-sand-lt); font-size: 1.2rem; }
.ph-act__text h1 {
  margin: 0;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 4.6rem;
  line-height: 0.95;
  color: var(--ph-off-white);
  text-shadow: 3px 4px 0 rgba(0, 0, 0, 0.35);
}
.ph-act__text p:not(.ph-eyebrow) {
  margin: 0;
  max-width: 28rem;
  padding-left: 0.9rem;
  border-left: 4px solid var(--ph-yellow);
  font-size: 1.4rem;
  font-style: italic;
  line-height: 1.35;
}
.ph-act__duration {
  padding: 0.3rem 0.7rem;
  border-radius: 4px;
  background: var(--ph-espresso);
  color: var(--ph-sand-lt);
  font-family: var(--ph-font-ui);
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}
</style>
