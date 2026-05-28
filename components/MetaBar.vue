<!--
  MetaBar — the top metadata strip every brutalist slide has.

  Renders:  N°XX │ SECTION · subtitle  ──────  right-text

  Props:
    number   — slide number ("04")
    section  — section name ("ABERTURA", "EXTRAÇÃO", "WHOAMI", ...)
    subtitle — small detail after section ("o legadão")
    right    — right-side text (handle, time, marker)

  Slots:
    right — overrides right-side content (for custom decorations)
-->
<script setup lang="ts">
defineProps<{
  number?: string
  section?: string
  subtitle?: string
  right?: string
}>()
</script>

<template>
  <div class="meta-bar">
    <span v-if="number" class="meta-tag">N°<b>{{ number }}</b></span>
    <span v-if="number && section" class="meta-pipe">│</span>
    <span v-if="section" class="meta-track">
      {{ section }}<template v-if="subtitle"> · <b>{{ subtitle }}</b></template>
    </span>
    <span class="meta-fill" />
    <span class="meta-right">
      <slot name="right">{{ right }}</slot>
    </span>
  </div>
</template>

<style scoped>
.meta-bar {
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-family: var(--font-mono);
  font-size: 0.68rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--dim);
  animation: fade-in 0.6s ease both;
}
.meta-tag b { color: var(--red); font-weight: 700; }
.meta-pipe { color: var(--frame); }
.meta-track b { color: var(--bone); font-weight: 700; }
.meta-fill {
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--frame) 30%, var(--frame) 70%, transparent);
  margin: 0 0.75rem;
}
.meta-right {
  color: var(--bone);
  font-weight: 700;
  letter-spacing: 0.1em;
}
.meta-right :deep(.accent) { color: var(--red); }
</style>
