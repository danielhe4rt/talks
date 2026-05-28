<!--
  deletion-test-modular — brutalist version of the interactive deletion test.

  Same slot contract as the legacy `deletion-test`:
    default   — slide title (h1)
    questions — left ~32% panel (the 3 numbered questions, click-driven)
    visual    — right ~68% panel (the visual showing what's happening)

  v-click directives in the page MUST be preserved exactly — the speaker
  relies on them to advance the demo state-by-state.

  Frontmatter:
    ---
    layout: deletion-test-modular
    transition: none
    metaNumber: "09"
    metaSection: "EXTRAÇÃO"
    metaSubtitle: "teste da deleção"
    metaRight: "Q1 · legadão"
    ---
-->
<script setup lang="ts">
defineProps<{
  metaNumber?: string
  metaSection?: string
  metaSubtitle?: string
  metaRight?: string
}>()
</script>

<template>
  <div class="brutalist-deletion">
    <BgLayers vignette-pos="br" />

    <MetaBar
      v-if="metaNumber || metaSection"
      :number="metaNumber"
      :section="metaSection"
      :subtitle="metaSubtitle"
      :right="metaRight"
    />

    <div class="dt-title">
      <slot />
    </div>

    <div class="dt-body">
      <div class="dt-questions">
        <slot name="questions" />
      </div>
      <div class="dt-divider" />
      <div class="dt-visual">
        <div class="dt-visual-inner">
          <slot name="visual" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.brutalist-deletion {
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

.dt-title {
  flex-shrink: 0;
  margin-top: 0.5rem;
  margin-bottom: 0.6rem;
}
.dt-title :deep(h1) {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 1.05rem;
  letter-spacing: 0.04em;
  color: var(--bone);
  margin: 0;
}
.dt-title :deep(h1 span) {
  font-family: var(--font-serif);
  font-style: italic;
  font-weight: 400;
  color: var(--dim);
}

.dt-body {
  flex: 1;
  display: grid;
  grid-template-columns: 32% 1px 1fr;
  min-height: 0;
  overflow: hidden;
  gap: 0;
}

.dt-questions {
  padding-right: 1.1rem;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 0.55rem;
}
/* Inherit existing yellow/orange/red question styling from page-level classes */
.dt-questions :deep(> div) {
  font-family: var(--font-mono);
}

.dt-divider {
  background: linear-gradient(
    to bottom,
    transparent 5%,
    rgba(255, 255, 255, 0.07) 25%,
    rgba(255, 255, 255, 0.07) 75%,
    transparent 95%
  );
}

.dt-visual {
  padding-left: 1.3rem;
  overflow: hidden;
}
.dt-visual-inner {
  position: relative;
  width: 100%;
  height: 100%;
}
.dt-visual :deep(.slidev-vclick-target) {
  transition: opacity 0.3s ease;
}

/* Subtle red drip on top-right corner of questions panel to tie to brand */
.dt-questions::before {
  content: "";
  position: absolute;
  top: 0;
  left: 2.2rem;
  width: 28px;
  height: 4px;
  background: var(--red);
  box-shadow: 0 0 14px rgba(255, 45, 32, 0.4);
  margin-top: 1.7rem;
}
</style>
