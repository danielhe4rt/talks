<!--
  MetaBar — the top metadata strip every brutalist slide has.

  Renders:  N°XX │ SECTION · subtitle  ──────  [●PHASE] right-text

  Props:
    number   — slide number ("04")
    section  — section name ("ABERTURA", "EXTRAÇÃO", "WHOAMI", ...)
    subtitle — small detail after section ("o legadão")
    right    — right-side text (handle, time, marker)
    phase    — optional TDD phase chip ('red' | 'refactor' | 'green' | 'diagnostico')

  Slots:
    right — overrides right-side content (for custom decorations)
-->
<script setup lang="ts">
defineProps<{
  number?: string
  section?: string
  subtitle?: string
  right?: string
  phase?: 'red' | 'refactor' | 'green' | 'diagnostico'
}>()

const phaseLabels: Record<string, string> = {
  red: 'RED',
  refactor: 'REFACTOR',
  green: 'GREEN',
  diagnostico: 'DIAGNÓSTICO',
}
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
      <span v-if="phase" class="phase-chip" :data-phase="phase">
        <span class="phase-dot" />
        <span class="phase-label">{{ phaseLabels[phase] }}</span>
      </span>
      <span v-if="phase && (right || $slots.right)" class="phase-sep">·</span>
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
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  color: var(--bone);
  font-weight: 700;
  letter-spacing: 0.1em;
}
.meta-right :deep(.accent) { color: var(--red); }

/* ============================
   Phase chip — TDD state badge
   ============================ */
.phase-chip {
  display: inline-flex;
  align-items: center;
  gap: 0.3rem;
  font-family: var(--font-mono);
  font-size: 0.6rem;
  font-weight: 700;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  padding: 0.15rem 0.5rem 0.18rem 0.4rem;
  border-radius: 2px;
  border-left: 2px solid var(--chip-color, var(--red));
  background: var(--chip-bg, rgba(255, 45, 32, 0.1));
  color: var(--chip-text, var(--bone));
  line-height: 1;
}
.phase-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--chip-color, var(--red));
  box-shadow: 0 0 6px var(--chip-color, var(--red));
}
.phase-label { color: var(--chip-text, var(--bone)); }

/* RED — clean Laravel red (alarm) */
.phase-chip[data-phase="red"] {
  --chip-color: var(--red);
  --chip-bg: rgba(255, 45, 32, 0.12);
  --chip-text: var(--bone);
}
/* REFACTOR — orange */
.phase-chip[data-phase="refactor"] {
  --chip-color: var(--accent-orange);
  --chip-bg: rgba(255, 165, 58, 0.12);
  --chip-text: var(--bone);
}
/* GREEN — pass */
.phase-chip[data-phase="green"] {
  --chip-color: var(--accent-green);
  --chip-bg: rgba(110, 231, 161, 0.12);
  --chip-text: var(--bone);
}
/* DIAGNÓSTICO — darker red-deep (survey/overview, not alarm) */
.phase-chip[data-phase="diagnostico"] {
  --chip-color: var(--red-deep);
  --chip-bg: rgba(196, 21, 12, 0.18);
  --chip-text: var(--bone);
}

.phase-sep {
  color: var(--frame);
  font-weight: 400;
}
</style>
