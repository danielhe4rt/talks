<script setup lang="ts">
// Teste da Deleção. Questions + verdict come from frontmatter and react to
// clicks; the ::visual:: slot holds the stage (stack steps with
// v-click="[a, b]" inside a .ph-stage). Declare `clicks: N` in the slide
// frontmatter, since the panel reads $clicks instead of registering.
//
// questions:
//   - text: Listar todos os arquivos?
//     show: 1          # click that reveals it (default 0)
//     at: 2            # click that resolves it (omit = stays as declared)
//     status: fail     # pass | fail | pending
//     detail: Espalhados em 8 pastas
// result: { at: 4, status: fail, label: FALHOU, score: 0 de 3 }
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

interface Question {
  text: string
  show?: number
  at?: number
  status?: 'pass' | 'fail' | 'pending'
  detail?: string
}
interface Result {
  at?: number
  status: 'pass' | 'fail' | 'almost'
  label: string
  score?: string
}

const props = defineProps<{
  questions?: Question[]
  result?: Result
  meta?: string
}>()

const { $clicks } = useSlideContext()
const clicks = computed(() => $clicks.value)

const rows = computed(() => (props.questions ?? []).map((q, i) => {
  const shown = clicks.value >= (q.show ?? 0)
  const resolved = q.at === undefined ? q.status !== 'pending' : clicks.value >= q.at
  const status = resolved ? (q.status ?? 'pending') : 'pending'
  const active = shown && !resolved && q.at !== undefined
  return { ...q, n: i + 1, shown, resolved, status, active }
}))

const anyActive = computed(() => rows.value.some(r => r.active))
const showResult = computed(() => !!props.result && clicks.value >= (props.result.at ?? 0))
const marks = { pass: '✓', fail: '✘', pending: '?' }
const labels = { pass: 'passou', fail: 'falhou', pending: 'pendente' }
</script>

<template>
  <div class="ph-slide ph-slide--espresso ph-del">
    <header class="ph-topbar">
      <img class="ph-topbar__logo" src="/images/phpeste-logo-cream.png" alt="PHPeste 2026">
      <div class="ph-del__title"><slot /></div>
      <span class="ph-topbar__fill" />
      <span v-if="meta" class="ph-topbar__meta">{{ meta }}</span>
    </header>

    <div class="ph-del__body">
      <aside class="ph-del__questions" aria-label="Perguntas do Teste da Deleção">
        <ol>
          <li
            v-for="q in rows"
            :key="q.n"
            class="ph-del__q"
            :class="[`is-${q.status}`, { 'is-hidden': !q.shown, 'is-active': q.active, 'is-dim': anyActive && !q.active }]"
          >
            <span class="ph-del__q-mark" :aria-label="labels[q.status]">{{ marks[q.status] }}</span>
            <span class="ph-del__q-body">
              <span class="ph-del__q-n">pergunta {{ q.n }}</span>
              <span class="ph-del__q-text">{{ q.text }}</span>
              <span v-if="q.detail && q.resolved" class="ph-del__q-detail">{{ q.detail }}</span>
            </span>
          </li>
        </ol>

        <div v-if="result" class="ph-del__result" :class="[`is-${result.status}`, { 'is-hidden': !showResult }]">
          <span class="ph-del__stamp">{{ result.label }}</span>
          <span v-if="result.score" class="ph-del__score">{{ result.score }}</span>
        </div>
      </aside>

      <section class="ph-del__visual">
        <slot name="visual" />
      </section>
    </div>

    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-del__title h1 {
  text-transform: none;
  letter-spacing: 0;
  margin: 0 0 0 0.6rem;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 1.75rem;
  line-height: 1;
  color: var(--ph-off-white);
}
.ph-del__title h1 em { font-style: normal; color: var(--ph-orange); }

.ph-del__body {
  flex: 1;
  min-height: 0;
  display: grid;
  grid-template-columns: 15.5rem 1fr;
  gap: 1.6rem;
  padding: 1rem 2.6rem 1.3rem;
}

/* -------- questions -------- */
.ph-del__questions { display: flex; flex-direction: column; gap: 0.7rem; min-height: 0; }
.ph-del__questions ol { margin: 0; padding: 0; list-style: none; display: flex; flex-direction: column; gap: 0.55rem; }
.ph-del__q {
  display: flex;
  gap: 0.7rem;
  padding: 0.6rem 0.7rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-radius: 4px;
  transition: opacity 0.3s, transform 0.3s, box-shadow 0.3s;
}
.ph-del__q.is-hidden { visibility: hidden; }
.ph-del__q.is-dim { opacity: 0.6; }
.ph-del__q.is-active { box-shadow: 5px 5px 0 var(--ph-orange); transform: translate(-2px, -2px); }

.ph-del__q-mark {
  flex: none;
  display: grid;
  place-items: center;
  width: 1.8rem;
  height: 1.8rem;
  border-radius: 4px;
  font-family: var(--ph-font-ui);
  font-size: 1rem;
  font-weight: 800;
  background: var(--ph-sand-lt);
  color: var(--ph-espresso);
  border: 1.5px dashed var(--ph-sand);
}
.ph-del__q.is-fail .ph-del__q-mark { background: var(--ph-crimson); color: var(--ph-off-white); border: 0; }
.ph-del__q.is-pass .ph-del__q-mark { background: var(--ph-green); color: var(--ph-off-white); border: 0; }

.ph-del__q-body { display: flex; flex-direction: column; min-width: 0; }
.ph-del__q-n {
  font-family: var(--ph-font-ui);
  font-size: 0.62rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}
.ph-del__q-text { font-size: 0.95rem; font-weight: 600; line-height: 1.3; }
.ph-del__q-detail { margin-top: 0.2rem; font-size: 0.82rem; font-style: italic; line-height: 1.3; }

/* -------- verdict stamp (carimbo) -------- */
.ph-del__result {
  margin-top: auto;
  display: flex;
  align-items: center;
  gap: 0.8rem;
}
.ph-del__result.is-hidden { visibility: hidden; }
.ph-del__stamp {
  --stamp: var(--ph-crimson);
  padding: 0.25rem 0.8rem;
  border: 3px solid var(--stamp);
  border-radius: 6px;
  color: var(--stamp);
  background: var(--ph-off-white);
  font-family: var(--ph-font-display);
  font-size: 1.45rem;
  line-height: 1.1;
  letter-spacing: 0.04em;
  white-space: nowrap;
  transform: rotate(-4deg);
  -webkit-mask-image: var(--ph-stamp-mask);
  mask-image: var(--ph-stamp-mask);
  mask-size: 120px 120px;
}
.ph-del__result.is-pass .ph-del__stamp { --stamp: var(--ph-green); }
.ph-del__result.is-almost .ph-del__stamp { --stamp: var(--ph-amber); }
.ph-del__score {
  font-family: var(--ph-font-ui);
  font-size: 0.85rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--ph-sand-lt);
  white-space: nowrap;
}

/* -------- visual stage -------- */
.ph-del__visual { position: relative; min-width: 0; min-height: 0; }
</style>
