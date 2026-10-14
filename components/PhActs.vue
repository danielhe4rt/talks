<script setup lang="ts">
// Talk agenda: a proportional time bar (azulejo colours) on top of the act
// list. Each act's colour links its bar segment to its row; minutes are
// always written out, so colour is never the only cue.
import { computed } from 'vue'

interface Act {
  title: string
  desc?: string
  min: number
}

const props = defineProps<{ acts: Act[] }>()

// bg + text pairs, all >= 4.5:1
const tones = [
  { bg: 'var(--ph-crimson)', fg: 'var(--ph-off-white)' },
  { bg: 'var(--ph-yellow)', fg: 'var(--ph-espresso)' },
  { bg: 'var(--ph-espresso)', fg: 'var(--ph-sand-lt)' },
  { bg: 'var(--ph-orange)', fg: 'var(--ph-black)' },
]

const rows = computed(() => props.acts.map((act, i) => ({
  ...act,
  num: String(i + 1).padStart(2, '0'),
  tone: tones[i % tones.length],
})))
</script>

<template>
  <div class="ph-acts">
    <div class="ph-acts__bar" aria-hidden="true">
      <span
        v-for="row in rows"
        :key="row.num"
        class="ph-acts__seg"
        :style="{ flex: `${row.min} 1 0`, background: row.tone.bg, color: row.tone.fg }"
      >{{ row.num }}</span>
    </div>

    <ol class="ph-acts__list">
      <li
        v-for="row in rows"
        :key="row.num"
        class="ph-acts__row"
        :style="{ '--tone': row.tone.bg }"
      >
        <span class="ph-acts__num">{{ row.num }}</span>
        <span class="ph-acts__text">
          <span class="ph-acts__title">{{ row.title }}</span>
          <span v-if="row.desc" class="ph-acts__desc">{{ row.desc }}</span>
        </span>
        <span class="ph-acts__min">~{{ row.min }} min</span>
      </li>
    </ol>
  </div>
</template>

<style>
.ph-acts {
  position: relative;
  padding: 0.9rem 1.2rem 0.4rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-radius: 4px;
  box-shadow: 6px 6px 0 var(--ph-espresso);
}

.ph-acts__bar {
  display: flex;
  gap: 5px;
  height: 1.6rem;
}
.ph-acts__seg {
  display: flex;
  align-items: center;
  padding-left: 0.5rem;
  border: 2px solid var(--ph-espresso);
  border-radius: 4px;
  font-family: var(--ph-font-display);
  font-size: 0.95rem;
}
.ph-acts__list { margin: 0.4rem 0 0; padding: 0; list-style: none; }
.ph-acts__row {
  display: grid;
  grid-template-columns: 3.2rem 1fr auto;
  align-items: center;
  gap: 0.9rem;
  padding: 0.5rem 0 0.5rem 0.8rem;
  border-left: 6px solid var(--tone);
}
.ph-acts__row + .ph-acts__row { border-top: 1.5px dashed var(--ph-sand); }
.ph-acts__num {
  font-family: var(--ph-font-display);
  font-size: 2rem;
  line-height: 1;
  color: var(--ph-crimson);
}
.ph-acts__text { display: flex; flex-direction: column; min-width: 0; }
.ph-acts__title {
  font-family: var(--ph-font-ui);
  font-size: 1.05rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}
.ph-acts__desc { font-size: 0.95rem; font-style: italic; line-height: 1.35; }
.ph-acts__min {
  padding: 0.2rem 0.55rem;
  border-radius: 4px;
  background: var(--ph-espresso);
  color: var(--ph-sand-lt);
  font-family: var(--ph-font-ui);
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  white-space: nowrap;
}
</style>
