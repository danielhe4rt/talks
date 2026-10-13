<script setup lang="ts">
// Before / after. default slot = h1 (+ one optional paragraph),
// ::before:: / ::after:: = the two columns, ::footer:: = the rule the
// comparison lands on (use v-click on it when it's a reveal).
withDefaults(defineProps<{
  tone?: 'espresso' | 'sand'
  beforeLabel?: string
  afterLabel?: string
  beforeKind?: 'fail' | 'neutral' | 'info'
  afterKind?: 'ok' | 'neutral' | 'info'
  meta?: string
}>(), {
  tone: 'espresso',
  beforeLabel: 'antes',
  afterLabel: 'depois',
  beforeKind: 'fail',
  afterKind: 'ok',
})
</script>

<template>
  <div class="ph-slide ph-psplit" :class="`ph-slide--${tone}`">
    <header class="ph-topbar">
      <img
        class="ph-topbar__logo"
        :src="tone === 'espresso' ? '/images/phpeste-logo-cream.png' : '/images/phpeste-logo-espresso.png'"
        alt="PHPeste 2026"
      >
      <div class="ph-psplit__title"><slot /></div>
      <span class="ph-topbar__fill" />
      <span v-if="meta" class="ph-topbar__meta">{{ meta }}</span>
    </header>

    <div class="ph-psplit__body">
      <section class="ph-psplit__col" :class="`is-${beforeKind}`">
        <span class="ph-psplit__label">{{ beforeLabel }}</span>
        <div class="ph-psplit__content ph-ink"><slot name="before" /></div>
      </section>
      <span class="ph-psplit__arrow" aria-hidden="true">→</span>
      <section class="ph-psplit__col" :class="`is-${afterKind}`">
        <span class="ph-psplit__label">{{ afterLabel }}</span>
        <div class="ph-psplit__content ph-ink"><slot name="after" /></div>
      </section>
    </div>

    <div v-if="$slots.footer" class="ph-psplit__footer">
      <slot name="footer" />
    </div>

    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-psplit__title { display: flex; align-items: baseline; gap: 0.9rem; margin-left: 0.6rem; min-width: 0; }
.ph-psplit__title h1 {
  text-transform: none;
  letter-spacing: 0;
  margin: 0;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 1.75rem;
  line-height: 1;
}
.ph-slide--espresso .ph-psplit__title h1 { color: var(--ph-off-white); }
.ph-psplit__title h1 em { font-style: normal; color: var(--ph-orange); }
.ph-slide--sand .ph-psplit__title h1 em { color: var(--ph-crimson); }
.ph-psplit__title p { margin: 0; text-transform: none; letter-spacing: 0; font-style: italic; font-size: 0.95rem; color: var(--ph-sand); }
.ph-slide--sand .ph-psplit__title p { color: var(--ph-espresso); }

.ph-psplit__body {
  flex: 1;
  min-height: 0;
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 1rem;
  align-items: stretch;
  padding: 1rem 2.6rem 0.8rem;
}
.ph-psplit__arrow {
  align-self: center;
  font-family: var(--ph-font-display);
  font-size: 2.2rem;
  color: var(--ph-orange);
}
.ph-slide--sand .ph-psplit__arrow { color: var(--ph-crimson); }

.ph-psplit__col {
  --k: var(--ph-crimson);
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  min-width: 0;
  min-height: 0;
}
.ph-psplit__col.is-ok { --k: var(--ph-green); }
.ph-psplit__col.is-info { --k: var(--ph-blue); }
.ph-psplit__col.is-neutral { --k: var(--ph-steel); }
.ph-psplit__label {
  align-self: flex-start;
  padding: 0.15rem 0.6rem;
  border-radius: 4px;
  background: var(--k);
  color: var(--ph-off-white);
  font-family: var(--ph-font-ui);
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}
.ph-psplit__content { display: flex; flex-direction: column; gap: 0.6rem; min-height: 0; }
.ph-psplit__content > p { margin: 0; }
.ph-psplit__content .slidev-code { font-size: 0.8rem !important; line-height: 1.5 !important; }
.ph-psplit__content .slidev-code-wrapper { border-left: 6px solid var(--k) !important; }
.ph-psplit__content .ph-files { border-left: 6px solid var(--k); }

.ph-psplit__footer { padding: 0 2.6rem 0.9rem; }
.ph-psplit__footer > * { margin: 0; }
</style>
