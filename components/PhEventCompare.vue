<!--
  PhEventCompare — import (acoplado) vs evento (desacoplado), PHPeste style.
  One button deletes Payment on both sides; the divergence is the lesson.
-->
<script setup lang="ts">
import { ref } from 'vue'

const deleted = ref(false)
</script>

<template>
  <div class="ph-ec">
    <section class="ph-ec__col is-fail">
      <span class="ph-psplit__label">acoplado · import</span>
      <p class="ph-ec__sub">Checkout <em>sabe</em> quem é Payment.</p>
      <div class="ph-ec__diag">
        <div class="ph-mod" :class="deleted ? 'is-broken' : 'is-focus'">
          <span class="ph-mod__name">Checkout</span>
          <span class="ph-mod__state">{{ deleted ? '✘ fatal error' : 'chama direto' }}</span>
        </div>
        <div class="ph-ec__wire" :class="{ 'is-cut': deleted }">
          <span>{{ deleted ? 'import quebrado' : 'use Payment\\…' }}</span>
        </div>
        <div class="ph-mod" :class="{ 'is-deleted': deleted }">
          <span class="ph-mod__name">Payment</span>
          <span class="ph-mod__state">{{ deleted ? 'deletado' : 'dependência' }}</span>
        </div>
      </div>
      <pre class="ph-files"><span class="is-ctx">// Checkout/PlaceOrder.php</span><span :class="{ 'is-gone': deleted }">use App\Modules\Payment\ProcessPayment;</span><span>(new ProcessPayment)->execute($order);</span></pre>
    </section>

    <section class="ph-ec__col is-ok">
      <span class="ph-psplit__label">desacoplado · evento</span>
      <p class="ph-ec__sub">Checkout avisa pro <em>vazio</em>.</p>
      <div class="ph-ec__diag">
        <div class="ph-mod is-ok">
          <span class="ph-mod__name">Checkout</span>
          <span class="ph-mod__state">dispara evento</span>
        </div>
        <div class="ph-ec__wire is-event">
          <span>OrderPlaced</span>
        </div>
        <div class="ph-mod" :class="{ 'is-deleted': deleted }">
          <span class="ph-mod__name">Payment</span>
          <span class="ph-mod__state">{{ deleted ? 'deletado · ninguém escuta' : 'listener' }}</span>
        </div>
      </div>
      <pre class="ph-files"><span class="is-ctx">// Checkout/PlaceOrder.php</span><span>use App\Modules\Checkout\Events\OrderPlaced;</span><span>OrderPlaced::dispatch($order);</span></pre>
    </section>

    <div class="ph-ec__bar">
      <button class="ph-ec__btn" type="button" :aria-pressed="deleted" @click="deleted = !deleted">
        <mdi-restore v-if="deleted" aria-hidden="true" />
        <mdi-delete-outline v-else aria-hidden="true" />
        {{ deleted ? 'restaurar Payment' : 'deletar Payment' }}
      </button>
      <p class="ph-ec__live" aria-live="polite">
        <template v-if="deleted">Esquerda: Checkout caiu junto. Direita: sistema intacto.</template>
      </p>
    </div>
  </div>
</template>

<style>
.ph-ec {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.6rem 2rem;
}
.ph-ec__col { --k: var(--ph-crimson); display: flex; flex-direction: column; gap: 0.55rem; min-width: 0; }
.ph-ec__col.is-ok { --k: var(--ph-green); }
.ph-ec__col .ph-psplit__label {
  align-self: flex-start;
  padding: 0.15rem 0.6rem;
  border-radius: 4px;
  background: var(--k);
  color: var(--ph-off-white);
  font-family: var(--ph-font-ui);
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}
.ph-ec__sub { margin: 0; font-size: 1.1rem; color: var(--ph-sand-lt); }
.ph-ec__sub em { font-weight: 600; }

.ph-ec__diag { display: grid; grid-template-columns: 1fr 7.5rem 1fr; align-items: center; gap: 0.5rem; }
.ph-ec__wire {
  position: relative;
  height: 2.2rem;
  display: grid;
  place-items: center;
  font-family: var(--ph-font-mono);
  font-size: 0.68rem;
  color: var(--ph-sand-lt);
}
.ph-ec__wire::before {
  content: '';
  position: absolute;
  left: 0; right: 0; top: 50%;
  border-top: 4px solid var(--ph-sand-lt);
}
.ph-ec__wire span { position: relative; padding: 0.05rem 0.35rem; background: var(--ph-espresso); border-radius: 3px; }
.ph-ec__wire.is-cut::before { border-top: 4px dashed var(--ph-yellow); }
.ph-ec__wire.is-cut span { color: var(--ph-yellow); }
.ph-ec__wire.is-event::before { border-top: 3px dotted var(--ph-sand); }
.ph-ec__wire.is-event span { background: var(--ph-green); color: var(--ph-off-white); font-weight: 600; }

.ph-ec .ph-files { font-size: 0.74rem; border-left: 6px solid var(--k); white-space: pre-wrap; }

.ph-ec__bar { grid-column: 1 / -1; display: flex; align-items: center; gap: 1rem; }
.ph-ec__btn {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  padding: 0.45rem 0.9rem;
  border: 2px solid var(--ph-espresso);
  border-radius: 4px;
  background: var(--ph-yellow);
  color: var(--ph-espresso);
  box-shadow: 4px 4px 0 var(--ph-black);
  font-family: var(--ph-font-ui);
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  cursor: pointer;
}
.ph-ec__btn:focus-visible { outline: 3px solid var(--ph-off-white); outline-offset: 3px; }
.ph-ec__btn[aria-pressed="true"] { background: var(--ph-sand-lt); }
.ph-ec__live { margin: 0; font-style: italic; color: var(--ph-sand-lt); }
</style>
