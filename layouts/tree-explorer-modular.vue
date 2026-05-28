<!--
  tree-explorer-modular — brutalist version of the folder stepper.

  Same slot contract as the legacy `tree-explorer`:
    default — slide title (h1)
    tree    — left-side file tree (typically a fenced code block)
    content — right-side content for the highlighted folder
    note    — optional admonition at the bottom right

  Plus brutalist chrome: meta-bar, BgLayers, TerminalPanel framing.

  Frontmatter:
    ---
    layout: tree-explorer-modular
    transition: none
    metaNumber: "05"
    metaSection: "ABERTURA"
    metaSubtitle: "stepper"
    noteType: warning   # info | warning | danger | tip
    metaRight: "app/Actions/"   # current focus, helpful for orientation
    ---
-->
<script setup lang="ts">
import { computed, useSlots } from 'vue'

const props = defineProps<{
  metaNumber?: string
  metaSection?: string
  metaSubtitle?: string
  metaRight?: string
  noteType?: 'info' | 'warning' | 'danger' | 'tip'
}>()

const slots = useSlots()
const hasNote = computed(() => !!slots.note)

const noteConfig = computed(() => {
  const configs = {
    info:    { icon: 'ℹ', accent: 'var(--accent-blue)',   bg: 'rgba(96, 165, 250, 0.06)', border: 'rgba(96, 165, 250, 0.4)' },
    warning: { icon: '⚠', accent: 'var(--accent-orange)', bg: 'rgba(255, 165, 58, 0.06)', border: 'rgba(255, 165, 58, 0.4)' },
    danger:  { icon: '✕', accent: 'var(--red)',           bg: 'rgba(255, 45, 32, 0.08)',  border: 'rgba(255, 45, 32, 0.45)' },
    tip:     { icon: '✓', accent: 'var(--accent-green)',  bg: 'rgba(110, 231, 161, 0.06)',border: 'rgba(110, 231, 161, 0.4)' },
  } as const
  return configs[props.noteType ?? 'info']
})
</script>

<template>
  <div class="brutalist-tree">
    <BgLayers vignette-pos="br" />

    <MetaBar
      v-if="metaNumber || metaSection"
      :number="metaNumber"
      :section="metaSection"
      :subtitle="metaSubtitle"
      :right="metaRight"
    />

    <div class="tree-body">
      <!-- Left: title + tree -->
      <div class="tree-left">
        <div class="tree-title"><slot /></div>
        <div class="tree-pane">
          <TerminalPanel path="~/projeto" cur="app/" status="tree">
            <div class="tree-content"><slot name="tree" /></div>
          </TerminalPanel>
        </div>
      </div>

      <!-- Right: content + admonition -->
      <div class="tree-right">
        <div class="tree-content-pane">
          <slot name="content" />
        </div>

        <div
          v-if="hasNote"
          class="tree-note"
          :style="{
            '--note-border': noteConfig.border,
            '--note-bg': noteConfig.bg,
            '--note-accent': noteConfig.accent,
          }"
        >
          <span class="tree-note-icon">{{ noteConfig.icon }}</span>
          <div class="tree-note-text"><slot name="note" /></div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.brutalist-tree {
  position: absolute;
  inset: 0;
  padding: 1.7rem 2.2rem 1.5rem;
  background: var(--ink);
  color: var(--bone);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  font-family: var(--font-mono);
}

.tree-body {
  flex: 1;
  display: grid;
  grid-template-columns: 36% 1fr;
  gap: 1.6rem;
  margin-top: 0.7rem;
  min-height: 0;
}

/* ─── left column ─── */
.tree-left {
  display: flex;
  flex-direction: column;
  min-height: 0;
  gap: 0.5rem;
}
.tree-title :deep(h1) {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 0.95rem;
  color: var(--bone);
  letter-spacing: 0.04em;
  text-transform: uppercase;
  margin: 0;
  opacity: 0.85;
}
.tree-pane {
  flex: 1;
  min-height: 0;
}
.tree-content {
  height: 100%;
  overflow: hidden;
}
.tree-content :deep(pre),
.tree-content :deep(.slidev-code-wrapper) { margin: 0; }
.tree-content :deep(.shiki) {
  font-size: 0.68rem !important;
  line-height: 1.4;
  background: transparent !important;
  padding: 0;
}

/* ─── right column ─── */
.tree-right {
  display: flex;
  flex-direction: column;
  min-height: 0;
  gap: 0.7rem;
}
.tree-content-pane {
  flex: 1;
  min-height: 0;
  overflow: hidden;
  padding: 0.4rem 0.2rem 0;
}
.tree-content-pane :deep(h3) {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 1rem;
  letter-spacing: 0.02em;
  color: var(--red);
  margin: 0 0 0.45rem;
}
.tree-content-pane :deep(pre),
.tree-content-pane :deep(.slidev-code-wrapper) { margin: 0; }
.tree-content-pane :deep(.shiki) {
  font-size: 0.72rem !important;
  line-height: 1.4;
  background: rgba(20, 20, 24, 0.4) !important;
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 3px;
  padding: 0.6rem 0.8rem;
}

/* ─── admonition note ─── */
.tree-note {
  flex-shrink: 0;
  display: flex;
  align-items: flex-start;
  gap: 0.55rem;
  padding: 0.6rem 0.85rem;
  border-radius: 3px;
  border-left: 3px solid var(--note-border);
  background: var(--note-bg);
  animation: slide-up 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.tree-note-icon {
  flex-shrink: 0;
  font-size: 0.9rem;
  line-height: 1.4;
  color: var(--note-accent);
}
.tree-note-text {
  font-family: var(--font-mono);
  font-size: 0.74rem;
  line-height: 1.5;
  color: #c8c2b6;
}
.tree-note-text :deep(p) { margin: 0; }
.tree-note-text :deep(strong) { color: var(--note-accent); font-weight: 700; }
.tree-note-text :deep(code) {
  font-size: 0.92em;
  padding: 0.05em 0.3em;
  border-radius: 2px;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid var(--frame);
}
</style>
