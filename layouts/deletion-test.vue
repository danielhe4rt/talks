<!--
  Deletion Test layout — title row + questions/visual split.

  Usage:
  ```md
  ---
  layout: deletion-test
  ---

  # O Teste da Deleção™

  ::questions::
  Left panel content (32%)

  ::visual::
  Right panel content (68%) — use absolute positioning for overlapping panels
  ```
-->

<script setup lang="ts">
defineProps({
  class: { type: String },
})
</script>

<template>
  <div class="slidev-layout deletion-test" :class="$props.class">
    <div class="deletion-test__title">
      <slot />
    </div>
    <div class="deletion-test__body">
      <div class="deletion-test__questions">
        <slot name="questions" />
      </div>
      <div class="deletion-test__divider" />
      <div class="deletion-test__visual">
        <div class="deletion-test__visual-inner">
          <slot name="visual" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.deletion-test {
  display: flex;
  flex-direction: column;
  height: 100%;
  padding: 1.5rem 2.5rem 1.25rem;
  overflow: hidden;
}

.deletion-test__title {
  flex-shrink: 0;
  margin-bottom: 0.75rem;
}

.deletion-test__title :deep(h1) {
  font-size: 1.35rem;
  font-weight: 800;
  letter-spacing: -0.02em;
  margin: 0;
}

.deletion-test__body {
  flex: 1;
  display: grid;
  grid-template-columns: 32% 1px 1fr;
  min-height: 0;
  overflow: hidden;
}

.deletion-test__questions {
  padding-right: 1.25rem;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 0.6rem;
}

.deletion-test__divider {
  background: linear-gradient(
    to bottom,
    transparent 5%,
    rgba(255, 255, 255, 0.06) 25%,
    rgba(255, 255, 255, 0.06) 75%,
    transparent 95%
  );
}

.deletion-test__visual {
  padding-left: 1.5rem;
  overflow: hidden;
}

.deletion-test__visual-inner {
  position: relative;
  width: 100%;
  height: 100%;
}

/* Crossfade for overlapping visual panels */
.deletion-test__visual :deep(.slidev-vclick-target) {
  transition: opacity 0.3s ease;
}
</style>
