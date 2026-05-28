<!--
  TerminalPanel — a dark "macOS-ish" terminal frame.

  Used wherever we want code-like content (whoami's whoami output, the
  cover's file-tree pane, etc.). Has a titlebar with macOS-style dots,
  a breadcrumb path, and an optional status tag, plus a content slot.

  Props:
    path   — breadcrumb shown in titlebar ("~/cart")
    cur    — emphasized current segment ("4 estruturas")
    status — small right-side label ("cycle", "tree -L 1")
    dotsRed — when true, first dot is muted red (default true for vibes)

  Slot:
    default — terminal content; arbitrary HTML / pre / code
-->
<script setup lang="ts">
defineProps<{
  path?: string
  cur?: string
  status?: string
  dotsRed?: boolean
}>()
</script>

<template>
  <div class="terminal">
    <div v-if="path || cur || status" class="term-titlebar">
      <span class="term-dots">
        <span class="term-dot" :class="{ 'term-dot--red': dotsRed !== false }" />
        <span class="term-dot" />
        <span class="term-dot" />
      </span>
      <span v-if="path || cur" class="term-path">
        <template v-if="path">{{ path }}</template>
        <template v-if="path && cur"> · </template>
        <span v-if="cur" class="term-path-cur">{{ cur }}</span>
      </span>
      <span v-if="status" class="term-status">{{ status }}</span>
    </div>

    <div class="term-body">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.terminal {
  position: relative;
  height: 100%;
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 4px;
  background:
    linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.75)),
    radial-gradient(ellipse at 100% 0%, rgba(255, 45, 32, 0.06), transparent 60%);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.04),
    0 20px 40px -20px rgba(0, 0, 0, 0.6);
  overflow: hidden;
  backdrop-filter: blur(2px);
  display: flex;
  flex-direction: column;
}

.term-titlebar {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  padding: 0.45rem 0.7rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
  font-family: var(--font-mono);
  font-size: 0.5rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #5a5a5d;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.025), transparent);
  flex-shrink: 0;
}

.term-dots { display: inline-flex; gap: 0.25rem; }
.term-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--frame);
  border: 1px solid rgba(255, 255, 255, 0.05);
}
.term-dot--red { background: #3a1e1c; }

.term-path { margin-left: 0.3rem; letter-spacing: 0.1em; }
.term-path-cur { color: var(--bone); font-weight: 700; }

.term-status {
  margin-left: auto;
  color: var(--red);
  opacity: 0.6;
  font-size: 0.45rem;
}

.term-body {
  position: relative;
  flex: 1;
  padding: 0.7rem 0.85rem;
  overflow: hidden;
  font-family: var(--font-mono);
}
</style>
