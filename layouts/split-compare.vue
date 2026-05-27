<!--
  Split Compare layout — before/after with visual divider and labels.
  Left = "before" (red tint), Right = "after" (green tint).

  Usage:
  ```md
  ---
  layout: split-compare
  ---

  # Title

  ::before::
  Before content

  ::after::
  After content
  ```
-->

<script setup lang="ts">
defineProps({
  class: { type: String },
  beforeLabel: { type: String, default: 'ANTES' },
  afterLabel: { type: String, default: 'DEPOIS' },
})
</script>

<template>
  <div class="slidev-layout split-compare" :class="$props.class">
    <div class="split-compare__header">
      <slot />
    </div>

    <div class="split-compare__panels">
      <div class="split-compare__before">
        <div class="split-compare__label split-compare__label--before">
          {{ beforeLabel }}
        </div>
        <div class="split-compare__panel-content">
          <slot name="before" />
        </div>
      </div>

      <div class="split-compare__divider">
        <div class="split-compare__divider-line" />
      </div>

      <div class="split-compare__after">
        <div class="split-compare__label split-compare__label--after">
          {{ afterLabel }}
        </div>
        <div class="split-compare__panel-content">
          <slot name="after" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.split-compare {
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  padding: 1.75rem 2.5rem 1.5rem;
  overflow: hidden;
}

.split-compare__header {
  flex-shrink: 0;
  margin-bottom: 1rem;
}

.split-compare__header :deep(h1) {
  font-size: 1.75rem;
  margin: 0;
}

.split-compare__panels {
  flex: 1;
  display: grid;
  grid-template-columns: 1fr 1px 1fr;
  gap: 0;
  min-height: 0;
}

.split-compare__before,
.split-compare__after {
  display: flex;
  flex-direction: column;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  overflow: hidden;
}

.split-compare__before {
  background: rgba(239, 68, 68, 0.04);
  border: 1px solid rgba(239, 68, 68, 0.1);
  margin-right: 0.75rem;
}

.split-compare__after {
  background: rgba(34, 197, 94, 0.04);
  border: 1px solid rgba(34, 197, 94, 0.1);
  margin-left: 0.75rem;
}

.split-compare__label {
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  margin-bottom: 0.75rem;
  flex-shrink: 0;
}

.split-compare__label--before {
  color: rgba(239, 68, 68, 0.6);
}

.split-compare__label--after {
  color: rgba(34, 197, 94, 0.6);
}

.split-compare__panel-content {
  flex: 1;
  overflow-y: auto;
}

.split-compare__panel-content :deep(pre),
.split-compare__panel-content :deep(.slidev-code-wrapper) {
  margin: 0;
}

.split-compare__panel-content :deep(.shiki) {
  font-size: 0.75rem !important;
}

.split-compare__divider {
  display: flex;
  align-items: center;
  justify-content: center;
}

.split-compare__divider-line {
  width: 1px;
  height: 70%;
  background: linear-gradient(
    to bottom,
    transparent,
    rgba(255, 255, 255, 0.1),
    transparent
  );
}
</style>
