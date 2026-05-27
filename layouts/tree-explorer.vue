<!--
  Tree Explorer layout — sidebar with tree, content panel, and bottom admonition.

  Usage:
  ```md
  ---
  layout: tree-explorer
  noteType: warning  # info | warning | danger | tip (default: info)
  ---

  # Title

  ::tree::
  ```text {13}
  app/
  ├── Models/    ← highlighted
  └── ...
  ```

  ::content::
  ### app/Models/ — 45 files
  ```text
  ├── Product.php
  └── ...
  ```

  ::note::
  Admonition text here — appears at the bottom-right.
  ```
-->

<script setup lang="ts">
import { computed, useSlots } from 'vue'

const props = defineProps({
  class: { type: String },
  noteType: { type: String, default: 'info' },
})

const slots = useSlots()
const hasNote = computed(() => !!slots.note)

const noteConfig = computed(() => {
  const configs = {
    info: {
      icon: 'ℹ',
      border: 'rgba(59, 130, 246, 0.4)',
      bg: 'rgba(59, 130, 246, 0.06)',
      accent: '#60a5fa',
    },
    warning: {
      icon: '⚠',
      border: 'rgba(234, 179, 8, 0.4)',
      bg: 'rgba(234, 179, 8, 0.06)',
      accent: '#facc15',
    },
    danger: {
      icon: '✕',
      border: 'rgba(239, 68, 68, 0.4)',
      bg: 'rgba(239, 68, 68, 0.06)',
      accent: '#f87171',
    },
    tip: {
      icon: '✓',
      border: 'rgba(34, 197, 94, 0.4)',
      bg: 'rgba(34, 197, 94, 0.06)',
      accent: '#4ade80',
    },
  }
  return configs[props.noteType] || configs.info
})
</script>

<template>
  <div class="slidev-layout tree-explorer">
    <!-- Left: title + tree -->
    <div class="tree-explorer__sidebar">
      <div class="tree-explorer__title">
        <slot />
      </div>
      <div class="tree-explorer__tree">
        <slot name="tree" />
      </div>
    </div>

    <div class="tree-explorer__divider" />

    <!-- Right: content + note -->
    <div class="tree-explorer__right">
      <div class="tree-explorer__content" :class="$props.class">
        <slot name="content" />
      </div>

      <div
        class="tree-explorer__note"
        :class="{ 'tree-explorer__note--empty': !hasNote }"
        :style="{
          '--note-border': noteConfig.border,
          '--note-bg': noteConfig.bg,
          '--note-accent': noteConfig.accent,
        }"
      >
        <span v-if="hasNote" class="tree-explorer__note-icon">{{ noteConfig.icon }}</span>
        <div v-if="hasNote" class="tree-explorer__note-text">
          <slot name="note" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.tree-explorer {
  display: grid;
  grid-template-columns: 38% 1px 1fr;
  height: 100%;
  width: 100%;
  overflow: hidden;
}

/* ── Left sidebar ── */

.tree-explorer__sidebar {
  display: flex;
  flex-direction: column;
  padding: 1.75rem 1.25rem 1.25rem 2.5rem;
  overflow: hidden;
}

.tree-explorer__title {
  flex-shrink: 0;
  margin-bottom: 0.25rem;
}

.tree-explorer__title :deep(h1) {
  font-size: 1.1rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  opacity: 0.5;
  margin: 0;
  white-space: nowrap;
}

.tree-explorer__tree {
  flex: 1;
  overflow-y: auto;
  overflow-x: hidden;
  min-height: 0;
}

.tree-explorer__tree :deep(pre),
.tree-explorer__tree :deep(.slidev-code-wrapper) {
  margin: 0;
}

.tree-explorer__tree :deep(.shiki) {
  font-size: 0.65rem !important;
  line-height: 1.4;
  padding: 0.25rem 0;
}

/* ── Divider ── */

.tree-explorer__divider {
  background: linear-gradient(
    to bottom,
    transparent 10%,
    rgba(255, 255, 255, 0.06) 30%,
    rgba(255, 255, 255, 0.06) 70%,
    transparent 90%
  );
  align-self: stretch;
}

/* ── Right panel ── */

.tree-explorer__right {
  display: flex;
  flex-direction: column;
  padding: 1.75rem 2.5rem 1.25rem 2rem;
  overflow: hidden;
  min-height: 0;
}

.tree-explorer__content {
  flex: 1;
  overflow-y: auto;
  min-height: 0;
}

.tree-explorer__content :deep(h3) {
  font-size: 1.15rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--slidev-theme-primary);
}

.tree-explorer__content :deep(pre),
.tree-explorer__content :deep(.slidev-code-wrapper) {
  margin: 0;
}

.tree-explorer__content :deep(.shiki) {
  font-size: 0.68rem !important;
  line-height: 1.35;
}

/* ── Bottom note (admonition) ── */

.tree-explorer__note {
  flex-shrink: 0;
  min-height: 3.25rem;
  margin-top: 0.75rem;
  padding: 0.6rem 0.85rem;
  border-radius: 6px;
  border-left: 3px solid var(--note-border);
  background: var(--note-bg);
  display: flex;
  align-items: flex-start;
  gap: 0.5rem;
}

.tree-explorer__note--empty {
  border-left-color: transparent;
  background: transparent;
}

.tree-explorer__note-icon {
  flex-shrink: 0;
  font-size: 0.8rem;
  line-height: 1.4;
  color: var(--note-accent);
}

.tree-explorer__note-text {
  font-size: 0.78rem;
  line-height: 1.45;
  opacity: 0.75;
}

.tree-explorer__note-text :deep(p) {
  margin: 0;
}

.tree-explorer__note-text :deep(strong) {
  color: var(--note-accent);
  font-weight: 600;
}

.tree-explorer__note-text :deep(code) {
  font-size: 0.72rem;
  padding: 0.1em 0.3em;
  border-radius: 3px;
  background: rgba(255, 255, 255, 0.06);
}
</style>
