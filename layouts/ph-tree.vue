<script setup lang="ts">
// Folder stepper (same slot contract as tree-explorer): default = title,
// ::tree:: = the app/ tree (code block with the current line highlighted),
// ::content:: = h3 + file listing, ::note:: = callout typed by noteType.
// Use `transition: none` on every step so only the right side changes.
import { computed, useSlots } from 'vue'

const props = withDefaults(defineProps<{
  noteType?: 'info' | 'warning' | 'danger' | 'tip'
  meta?: string
}>(), {
  noteType: 'info',
})

const slots = useSlots()
const notes = {
  info: { label: 'repara', color: 'var(--ph-blue)' },
  warning: { label: 'atenção', color: 'var(--ph-amber)' },
  danger: { label: 'problema', color: 'var(--ph-crimson)' },
  tip: { label: 'dica', color: 'var(--ph-green, #3a6e28)' },
}
const note = computed(() => notes[props.noteType])
</script>

<template>
  <div class="ph-slide ph-slide--espresso ph-tree">
    <header class="ph-topbar">
      <img class="ph-topbar__logo" src="/images/phpeste-logo-cream.png" alt="PHPeste 2026">
      <div class="ph-tree__title"><slot /></div>
      <span class="ph-topbar__fill" />
      <span v-if="meta" class="ph-topbar__meta ph-mono">{{ meta }}</span>
    </header>

    <div class="ph-tree__body">
      <div class="ph-tree__tree">
        <slot name="tree" />
      </div>

      <div class="ph-tree__main">
        <div class="ph-tree__content">
          <slot name="content" />
        </div>
        <aside
          v-if="slots.note"
          class="ph-tree__note"
          :style="{ '--note': note.color }"
        >
          <span class="ph-badge ph-tree__note-badge" aria-hidden="true">
            <mdi-information-variant v-if="noteType === 'info'" />
            <mdi-alert v-else-if="noteType === 'warning'" />
            <mdi-alert-octagon v-else-if="noteType === 'danger'" />
            <mdi-lightbulb-on-outline v-else />
          </span>
          <div>
            <span class="ph-tree__note-label">{{ note.label }}</span>
            <div class="ph-tree__note-text"><slot name="note" /></div>
          </div>
        </aside>
      </div>
    </div>

    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-tree__title h1 {
  margin: 0 0 0 0.6rem;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 1.9rem;
  line-height: 1;
  color: var(--ph-off-white);
  text-transform: none;
  letter-spacing: 0;
}

.ph-tree__body {
  flex: 1;
  min-height: 0;
  display: grid;
  grid-template-columns: 13.5rem 1fr;
  gap: 1.6rem;
  padding: 1rem 2.6rem 1.3rem;
}

/* -------- code blocks become ink on paper -------- */
.ph-tree .slidev-code-wrapper { margin: 0 !important; }
.ph-tree .slidev-code {
  background: transparent !important;
  padding: 0 !important;
  font-family: var(--ph-font-mono) !important;
  line-height: 1.5 !important;
}
.ph-tree .slidev-code,
.ph-tree .slidev-code code { color: var(--ph-espresso) !important; }
.ph-tree .slidev-code span { color: inherit !important; }

/* left: the app/ tree */
.ph-tree__tree {
  align-self: stretch;
  padding: 0.8rem 0.9rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-radius: 4px;
  box-shadow: 6px 6px 0 var(--ph-orange);
  overflow: hidden;
}
.ph-tree__tree .slidev-code { font-size: 0.78rem !important; }
.ph-tree__tree .line { display: inline-block; width: 100%; padding: 0 0.3rem; border-radius: 3px; }
.ph-tree__tree .line.dishonored { opacity: 0.68; }
.ph-tree__tree .line.highlighted {
  background: var(--ph-yellow);
  font-weight: 600;
  opacity: 1;
}

/* right: listing + note */
.ph-tree__main { display: flex; flex-direction: column; gap: 0.9rem; min-width: 0; min-height: 0; }
.ph-tree__content { flex: 1; min-height: 0; display: flex; flex-direction: column; gap: 0.6rem; }
.ph-tree__content h3 {
  margin: 0;
  font-family: var(--ph-font-body);
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--ph-sand-lt);
}
.ph-tree__content h3 code {
  padding: 0.1rem 0.45rem;
  border-radius: 4px;
  background: var(--ph-orange);
  color: var(--ph-black);
  font-family: var(--ph-font-mono);
  font-size: 0.95em;
}
.ph-tree__content .slidev-code-wrapper {
  padding: 0.7rem 1rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-radius: 4px;
}
.ph-tree__content .slidev-code { font-size: 0.95rem !important; }
.ph-tree__content .slidev-code code { display: block; }
/* long listings flow into columns (and shrink a bit) instead of overflowing */
.ph-tree__content .slidev-code:has(.line:nth-child(14)) { font-size: 0.85rem !important; }
.ph-tree__content .slidev-code:has(.line:nth-child(14)) code { columns: 2; column-gap: 1.6rem; }
.ph-tree__content .slidev-code:has(.line:nth-child(30)) { font-size: 0.76rem !important; }
.ph-tree__content .slidev-code:has(.line:nth-child(30)) code { columns: 3; column-gap: 1.2rem; }
/* grouped listings (blank lines between groups): denser 2 columns */
.ph-tree .ph-tree__content .ph-dense pre.slidev-code { font-size: 0.8rem !important; line-height: 1.32 !important; }
.ph-tree .ph-tree__content .ph-dense pre.slidev-code code { columns: 2 !important; }
.ph-tree__content .line { display: inline-block; width: 100%; break-inside: avoid; }

.ph-tree__note {
  display: flex;
  align-items: flex-start;
  gap: 0.8rem;
  padding: 0.7rem 0.9rem;
  background: var(--ph-sand-lt);
  color: var(--ph-espresso);
  border-left: 6px solid var(--note);
  border-radius: 4px;
}
.ph-tree__note-badge { background: var(--note); width: 2.1rem; height: 2.1rem; flex: none; }
.ph-tree__note-label {
  font-family: var(--ph-font-ui);
  font-size: 0.68rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}
.ph-tree__note-text { font-size: 0.98rem; line-height: 1.4; }
.ph-tree__note-text p { margin: 0; }
.ph-tree__note-text strong { font-weight: 600; }
.ph-tree__note-text code {
  padding: 0 0.3rem;
  border-radius: 3px;
  background: var(--ph-off-white);
  font-family: var(--ph-font-mono);
  font-size: 0.85em;
}
</style>
