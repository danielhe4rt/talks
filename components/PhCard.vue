<script setup lang="ts">
// Off-white card with a coloured top edge, stamped icon, index and tag.
// Slots: #icon (an <mdi-*> icon), default (description), #link.
withDefaults(defineProps<{
  index?: string
  tag?: string
  name: string
  meta?: string
  accent?: 'orange' | 'yellow' | 'crimson' | 'espresso' | 'purple' | 'blue' | 'amber' | 'steel'
}>(), {
  accent: 'yellow',
})
</script>

<template>
  <article class="ph-card-x" :class="`ph-card-x--${accent}`">
    <div class="ph-card-x__top">
      <span v-if="$slots.icon" class="ph-badge"><slot name="icon" /></span>
      <span v-if="index" class="ph-card-x__index" aria-hidden="true">{{ index }}</span>
    </div>
    <span v-if="tag" class="ph-card-x__tag">{{ tag }}</span>
    <h2 class="ph-card-x__name">{{ name }}</h2>
    <div class="ph-card-x__desc"><slot /></div>
    <div v-if="meta || $slots.link" class="ph-card-x__foot">
      <p v-if="meta" class="ph-card-x__meta">{{ meta }}</p>
      <p v-if="$slots.link" class="ph-card-x__link"><slot name="link" /></p>
    </div>
  </article>
</template>

<style>
.ph-card-x {
  /* --accent paints the top edge; --ink paints badge + index and must keep
     >= 4.5:1 against off-white, so light accents fall back to crimson */
  --accent: var(--ph-yellow);
  --ink: var(--ph-crimson);
  display: flex;
  flex-direction: column;
  min-width: 0;
  padding: 0.9rem 1rem 1rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-top: 6px solid var(--accent);
  border-radius: 4px;
  box-shadow: 5px 5px 0 var(--ph-espresso);
}
.ph-card-x--orange { --accent: var(--ph-orange); }
.ph-card-x--crimson { --accent: var(--ph-crimson); }
.ph-card-x--espresso { --accent: var(--ph-espresso); }
.ph-card-x--purple { --accent: var(--ph-purple); --ink: var(--ph-purple); }
.ph-card-x--blue { --accent: var(--ph-blue); --ink: var(--ph-blue); }
.ph-card-x--amber { --accent: var(--ph-amber); --ink: var(--ph-amber); }
.ph-card-x--steel { --accent: var(--ph-steel); --ink: var(--ph-steel); }
.ph-card-x .ph-badge { background: var(--ink); }

.ph-card-x:nth-child(odd) .ph-badge { transform: rotate(-3deg); }
.ph-card-x:nth-child(even) .ph-badge { transform: rotate(2.5deg); }

.ph-card-x__top { display: flex; align-items: center; justify-content: space-between; }
.ph-card-x__index {
  font-family: var(--ph-font-display);
  font-size: 1.9rem;
  line-height: 1;
  color: var(--ink);
}
.ph-card-x__tag {
  align-self: flex-start;
  margin-top: 0.75rem;
  padding: 0.12rem 0.45rem;
  border-radius: 4px;
  background: var(--ph-espresso);
  color: var(--ph-sand-lt);
  font-family: var(--ph-font-ui);
  font-size: 0.66rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}
.ph-card-x__name {
  margin: 0.4rem 0 0.3rem;
  font-family: var(--ph-font-body);
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 1.15;
}
.ph-card-x__desc { flex: 1; font-size: 0.92rem; line-height: 1.4; }
.ph-card-x__desc p { margin: 0; }
.ph-card-x__desc strong { font-weight: 600; }
.ph-card-x__foot {
  margin-top: 0.7rem;
  padding-top: 0.55rem;
  border-top: 1.5px dashed var(--ph-sand);
  min-height: 4.2rem; /* keeps the dashed rule aligned across a row */
}
.ph-card-x__foot p { margin: 0; }
.ph-card-x__meta { font-size: 0.82rem; font-style: italic; }
.ph-card-x__link {
  display: flex;
  align-items: flex-start;
  gap: 0.35rem;
  margin-top: 0.15rem !important;
  font-family: var(--ph-font-mono);
  font-size: 0.74rem;
  font-weight: 600;
  overflow-wrap: anywhere;
}
.ph-card-x__link .slidev-icon { flex: none; color: var(--ink); }
</style>
