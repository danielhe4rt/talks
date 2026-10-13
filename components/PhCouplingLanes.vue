<!--
  PhCouplingLanes — import vs evento as two lanes, driven by slide clicks:
    click 0: both wired up
    click 1: Payment is deleted on both lanes (import lane breaks)
    click 2: the verdict
  Declare `clicks: 2` on the slide.
-->
<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $clicks } = useSlideContext()
const deleted = computed(() => $clicks.value >= 1)
const verdict = computed(() => $clicks.value >= 2)
</script>

<template>
  <div class="ph-lanes" :class="{ 'is-deleted': deleted }">
    <!-- IMPORT -->
    <section class="ph-lane ph-lane--import" aria-label="Import: Checkout chama Payment direto">
      <header class="ph-lane__head">
        <span class="ph-lane__kind">import</span>
        <span class="ph-lane__sub">Checkout <em>conhece</em> Payment</span>
      </header>

      <div class="ph-node" :class="{ 'is-down': deleted }">
        <span class="ph-node__name">Checkout</span>
        <span class="ph-node__state">{{ deleted ? '✘ Class not found' : 'chama Payment direto' }}</span>
      </div>

      <div class="ph-wire" :class="{ 'is-cut': deleted }">
        <span class="ph-wire__line ph-wire__line--a" />
        <span class="ph-wire__chip">
          <mdi-link-variant-off v-if="deleted" aria-hidden="true" />
          <mdi-link-variant v-else aria-hidden="true" />
          {{ deleted ? 'import quebrado' : 'use Payment\\ProcessPayment' }}
        </span>
        <span class="ph-wire__line ph-wire__line--b" />
      </div>

      <div class="ph-node" :class="{ 'is-gone': deleted }">
        <span class="ph-node__name">Payment</span>
        <span class="ph-node__state">{{ deleted ? 'deletado' : 'dependência' }}</span>
      </div>
    </section>

    <!-- EVENTO -->
    <section class="ph-lane ph-lane--event" aria-label="Evento: Checkout só avisa">
      <header class="ph-lane__head">
        <span class="ph-lane__kind">evento</span>
        <span class="ph-lane__sub">Checkout <em>só avisa</em></span>
      </header>

      <div class="ph-node is-up">
        <span class="ph-node__name">Checkout</span>
        <span class="ph-node__state">{{ deleted ? '✓ segue funcionando' : 'dispara OrderPlaced' }}</span>
      </div>

      <div class="ph-wire ph-wire--event">
        <span class="ph-waves" aria-hidden="true"><i /><i /><i /></span>
        <span class="ph-wire__chip">
          <mdi-bullhorn-outline aria-hidden="true" />
          {{ deleted ? 'OrderPlaced → pro vazio' : 'OrderPlaced' }}
        </span>
      </div>

      <div class="ph-node" :class="{ 'is-gone': deleted }">
        <span class="ph-node__name">Payment</span>
        <span class="ph-node__state">
          <mdi-ear-hearing v-if="!deleted" aria-hidden="true" />
          {{ deleted ? 'deletado · ninguém escuta' : 'escuta' }}
        </span>
      </div>
    </section>

    <p class="ph-lanes__verdict" :class="{ 'is-shown': verdict }">
      <strong>Import é um fio:</strong> corta um lado, o outro cai junto.
      <strong>Evento é um aviso:</strong> quem quiser, escuta.
    </p>
  </div>
</template>

<style>
.ph-lanes { display: flex; flex-direction: column; gap: 1rem; }

.ph-lane {
  --k: var(--ph-crimson);
  display: grid;
  grid-template-columns: 9.5rem 12.5rem 1fr 12.5rem;
  align-items: center;
  gap: 1rem;
  padding: 0.9rem 1.1rem;
  border: 2px solid rgba(240, 230, 211, 0.18);
  border-left: 8px solid var(--k);
  border-radius: 4px;
  background: rgba(13, 9, 6, 0.35);
}
.ph-lane--event { --k: var(--ph-green); }

.ph-lane__head { display: flex; flex-direction: column; gap: 0.25rem; }
.ph-lane__kind {
  align-self: flex-start;
  padding: 0.1rem 0.55rem;
  border-radius: 4px;
  background: var(--k);
  color: var(--ph-off-white);
  font-family: var(--ph-font-display);
  font-size: 1.5rem;
  line-height: 1.1;
}
.ph-lane__sub { font-size: 1rem; color: var(--ph-sand-lt); line-height: 1.3; }
.ph-lane__sub em { font-weight: 600; }

/* module cards */
.ph-node {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
  padding: 0.75rem 0.9rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-top: 7px solid var(--ph-sand);
  border-radius: 4px;
  box-shadow: 5px 5px 0 var(--ph-black);
  transition: border-color 0.3s, box-shadow 0.3s, opacity 0.3s, transform 0.3s;
}
.ph-node__name { font-family: var(--ph-font-mono); font-size: 1.25rem; font-weight: 700; }
.ph-node__state { display: inline-flex; align-items: center; gap: 0.3rem; font-size: 0.95rem; font-style: italic; }
.ph-node.is-up { border-top-color: var(--ph-green); }
.ph-node.is-down {
  border-top-color: var(--ph-crimson);
  box-shadow: 5px 5px 0 var(--ph-crimson);
  transform: rotate(-1.5deg);
}
.ph-node.is-down .ph-node__state { font-style: normal; font-weight: 700; color: var(--ph-crimson); }
.ph-node.is-gone {
  background: transparent;
  color: var(--ph-sand-lt);
  border: 2px dashed var(--ph-sand);
  box-shadow: none;
}

/* connectors */
.ph-wire { position: relative; display: flex; align-items: center; min-width: 0; }
.ph-wire__line { flex: 1; height: 6px; background: var(--ph-sand-lt); border-radius: 3px; transition: transform 0.4s, opacity 0.4s; }
.ph-wire__chip {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  padding: 0.25rem 0.6rem;
  border-radius: 4px;
  background: var(--ph-sand-lt);
  color: var(--ph-espresso);
  font-family: var(--ph-font-mono);
  font-size: 0.8rem;
  font-weight: 600;
  white-space: nowrap;
}
.ph-wire.is-cut .ph-wire__line { background: var(--ph-yellow); }
.ph-wire.is-cut .ph-wire__line--a { transform: translateX(-10px) rotate(-6deg); }
.ph-wire.is-cut .ph-wire__line--b { transform: translateX(10px) rotate(6deg); }
.ph-wire.is-cut .ph-wire__chip { background: var(--ph-yellow); }

.ph-wire--event { justify-content: center; border-top: 4px dotted rgba(240, 230, 211, 0.45); height: 0; }
.ph-wire--event .ph-wire__chip { position: relative; background: var(--ph-green); color: var(--ph-off-white); }
.is-deleted .ph-wire--event .ph-wire__chip { background: var(--ph-sand-lt); color: var(--ph-espresso); }

/* broadcast waves leaving Checkout */
.ph-waves { position: absolute; left: -0.6rem; top: 50%; width: 0; height: 0; }
.ph-waves i {
  position: absolute;
  left: 0; top: 0;
  width: 3.4rem; height: 3.4rem;
  margin: -1.7rem 0 0 -1.7rem;
  border: 3px solid var(--ph-green);
  border-left-color: transparent;
  border-radius: 50%;
  opacity: 0;
  animation: ph-wave 2.4s ease-out infinite;
}
.ph-waves i:nth-child(2) { animation-delay: 0.8s; }
.ph-waves i:nth-child(3) { animation-delay: 1.6s; }
@keyframes ph-wave {
  from { transform: scale(0.4); opacity: 0.9; }
  to { transform: scale(1.8); opacity: 0; }
}
@media (prefers-reduced-motion: reduce) {
  .ph-waves i { animation: none; opacity: 0.5; }
  .ph-waves i:nth-child(2) { transform: scale(1.3); opacity: 0.3; }
  .ph-waves i:nth-child(3) { display: none; }
}

/* verdict */
.ph-lanes__verdict {
  margin: 0.2rem 0 0;
  padding: 0.7rem 1rem;
  background: var(--ph-off-white);
  color: var(--ph-espresso);
  border: 2px solid var(--ph-espresso);
  border-left: 8px solid var(--ph-yellow);
  border-radius: 4px;
  box-shadow: 6px 6px 0 var(--ph-orange);
  font-size: 1.15rem;
  line-height: 1.4;
  visibility: hidden;
}
.ph-lanes__verdict.is-shown { visibility: visible; animation: ph-rise 0.4s ease-out both; }
.ph-lanes__verdict strong { font-weight: 600; }
</style>
