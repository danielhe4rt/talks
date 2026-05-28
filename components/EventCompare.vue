<!--
  EventCompare — side-by-side brutalist editorial comparison of
  IMPORT (coupled) vs EVENTO (decoupled) module communication.

  One delete toggle (bottom). Same Payment deletion plays out on
  both columns simultaneously — the divergence is the lesson.

  Used in pages/02-extracao/06-evento-visual.md.
-->
<script setup lang="ts">
import { ref } from 'vue'

const deleted = ref(false)
function toggleDelete() { deleted.value = !deleted.value }
</script>

<template>
  <div class="ec">
    <!-- ROW 1 — display headers -->
    <div class="ec__grid ec__grid--heads">
      <div class="ec__col">
        <div class="ec__rail ec__rail--red">acoplado</div>
        <h2 class="ec__title ec__title--red">
          IMPORT<span class="g g-a">.</span>
        </h2>
        <p class="ec__sub">checkout <em>sabe</em> quem é payment</p>
      </div>

      <div class="ec__divider" aria-hidden="true">
        <span class="ec__vs">VS</span>
      </div>

      <div class="ec__col">
        <div class="ec__rail ec__rail--green">desacoplado</div>
        <h2 class="ec__title ec__title--green">
          EVENTO<span class="g g-c">.</span>
        </h2>
        <p class="ec__sub">checkout grita pro <em>vazio</em></p>
      </div>
    </div>

    <!-- ROW 2 — diagrams -->
    <div class="ec__grid ec__grid--diag">
      <!-- COUPLED diagram -->
      <div class="ec__col">
        <div class="ec__diag">
          <div class="ec__mod ec__mod--checkout" :class="{ 'ec__mod--err': deleted }">
            <span class="ec__mod-name">Checkout</span>
            <span class="ec__mod-state">
              <template v-if="deleted">✘ fatal error</template>
              <template v-else>chama direto</template>
            </span>
          </div>
          <div class="ec__wire" :class="{ 'ec__wire--broken': deleted }">
            <span class="ec__wire-label">
              <template v-if="deleted">💥 quebrou</template>
              <template v-else>use Payment\…</template>
            </span>
          </div>
          <div class="ec__mod ec__mod--payment" :class="{ 'ec__mod--deleted': deleted }">
            <span class="ec__mod-name">Payment</span>
            <span class="ec__mod-state">
              <template v-if="deleted">deletado</template>
              <template v-else>dependência</template>
            </span>
          </div>
        </div>
      </div>

      <div class="ec__divider" aria-hidden="true"></div>

      <!-- DECOUPLED diagram -->
      <div class="ec__col">
        <div class="ec__diag">
          <div class="ec__mod ec__mod--checkout">
            <span class="ec__mod-name">Checkout</span>
            <span class="ec__mod-state">dispatch event</span>
          </div>
          <div class="ec__broadcast">
            <span class="ec__pulse" />
            <span class="ec__pulse ec__pulse--2" />
            <span class="ec__pulse ec__pulse--3" />
            <span class="ec__event-chip">OrderPlaced</span>
          </div>
          <div class="ec__mod ec__mod--payment" :class="{ 'ec__mod--deleted': deleted }">
            <span class="ec__mod-name">Payment</span>
            <span class="ec__mod-state">
              <template v-if="deleted">deletado · sem ouvinte</template>
              <template v-else>listener</template>
            </span>
          </div>
        </div>
      </div>
    </div>

    <!-- ROW 3 — code rails -->
    <div class="ec__grid ec__grid--code">
      <div class="ec__col">
        <pre class="ec__code"><span class="t-com">// Checkout/PlaceOrder.php</span>
<span class="t-kw">use</span> App\Modules\<span :class="['t-cls', deleted && 't-broken']">Payment\ProcessPayment</span>;
(<span class="t-kw">new</span> ProcessPayment)-&gt;execute($order);</pre>
      </div>

      <div class="ec__divider" aria-hidden="true"></div>

      <div class="ec__col">
        <pre class="ec__code"><span class="t-com">// Checkout/PlaceOrder.php</span>
<span class="t-kw">use</span> App\Modules\Checkout\Events\<span class="t-ev">OrderPlaced</span>;
<span class="t-ev">OrderPlaced</span>::dispatch($order);
<span class="t-com">// quem escuta não é problema meu</span></pre>
      </div>
    </div>

    <!-- TOGGLE -->
    <div class="ec__toolbar">
      <button class="ec__toggle" :class="{ 'is-on': deleted }" @click="toggleDelete">
        <span class="ec__toggle-icon">{{ deleted ? '↻' : '⌫' }}</span>
        <span class="ec__toggle-label">
          {{ deleted ? 'restaurar Payment' : 'deletar Payment' }}
        </span>
        <span class="ec__toggle-hint">[ clique ]</span>
      </button>
    </div>
  </div>
</template>

<style scoped>
.ec {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  min-height: 0;
  padding-top: 0.4rem;
  font-family: var(--font-mono);
  position: relative;
}

/* shared grid */
.ec__grid {
  display: grid;
  grid-template-columns: 1fr 1px 1fr;
  column-gap: 2.2rem;
  align-items: stretch;
}
.ec__grid--heads { align-items: end; }
.ec__grid--diag  { flex: 1; min-height: 0; }
.ec__col { display: flex; flex-direction: column; min-width: 0; }

/* divider — vertical gradient rule */
.ec__divider {
  position: relative;
  background: linear-gradient(
    to bottom,
    transparent 0%,
    rgba(255,255,255,0.10) 18%,
    rgba(255,255,255,0.10) 82%,
    transparent 100%
  );
}
.ec__vs {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  background: var(--ink);
  padding: 0 0.35rem;
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 0.85rem;
  letter-spacing: 0.08em;
  color: var(--dim);
}

/* RAIL · rail label above title */
.ec__rail {
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.26em;
  text-transform: uppercase;
  font-weight: 700;
  padding: 0.15rem 0.5rem 0.15rem 0.55rem;
  align-self: flex-start;
  border-left: 2px solid;
  margin-bottom: 0.25rem;
}
.ec__rail--red   { color: var(--red);          border-color: var(--red); }
.ec__rail--green { color: var(--accent-green); border-color: var(--accent-green); }

/* TITLE · giant display */
.ec__title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 3.6rem;
  letter-spacing: -0.02em;
  margin: 0;
  line-height: 0.92;
  text-transform: uppercase;
}
.ec__title--red   { color: var(--red); }
.ec__title--green { color: var(--accent-green); }
.ec__title :deep(.g) { display: inline-block; }

/* SUB · editorial italic */
.ec__sub {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1rem;
  line-height: 1.35;
  color: #b9b3a9;
  margin: 0.35rem 0 0;
}
.ec__sub em {
  font-style: italic;
  color: var(--bone);
  border-bottom: 1px solid currentColor;
}

/* DIAGRAM rows */
.ec__diag {
  display: grid;
  grid-template-rows: auto 1fr auto;
  gap: 0.7rem;
  margin-top: 0.45rem;
  height: 100%;
  min-height: 0;
}

.ec__mod {
  border: 1px solid rgba(255,255,255,0.12);
  border-radius: 3px;
  padding: 0.65rem 0.95rem;
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 1rem;
  background: rgba(0,0,0,0.30);
  transition: border-color 0.3s ease, background 0.3s ease, opacity 0.3s ease;
  position: relative;
}
.ec__mod--checkout {
  border-color: var(--accent-blue);
  background: linear-gradient(180deg, rgba(96,165,250,0.08), rgba(96,165,250,0.02));
}
.ec__mod--checkout.ec__mod--err {
  border-color: var(--red);
  background: linear-gradient(180deg, rgba(255,45,32,0.15), rgba(255,45,32,0.04));
  animation: shake 0.4s ease;
}
.ec__mod--payment {
  border-color: var(--accent-orange);
  background: linear-gradient(180deg, rgba(255,165,58,0.07), rgba(255,165,58,0.01));
}
.ec__mod--deleted {
  border-style: dashed;
  border-color: rgba(255,255,255,0.18);
  background: transparent;
  opacity: 0.45;
}
.ec__mod--deleted .ec__mod-name { text-decoration: line-through; }

.ec__mod-name {
  font-weight: 700;
  font-size: 1.25rem;
  letter-spacing: -0.005em;
}
.ec__mod-state {
  font-size: 0.62rem;
  text-transform: uppercase;
  letter-spacing: 0.18em;
  color: var(--dim);
  white-space: nowrap;
}

/* COUPLED WIRE */
.ec__wire {
  position: relative;
  align-self: stretch;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 1.6rem;
}
.ec__wire::before {
  content: '';
  position: absolute;
  left: 5%; right: 5%; top: 50%;
  height: 2px;
  background: var(--accent-blue);
  box-shadow: 0 0 12px rgba(96,165,250,0.35);
  transition: background 0.3s, box-shadow 0.3s;
}
.ec__wire--broken::before {
  background: repeating-linear-gradient(
    90deg,
    var(--red) 0 10px,
    transparent 10px 16px
  );
  box-shadow: 0 0 14px rgba(255,45,32,0.30);
}
.ec__wire-label {
  position: relative;
  z-index: 1;
  background: var(--ink);
  padding: 0.05rem 0.65rem;
  font-size: 0.7rem;
  letter-spacing: 0.05em;
  color: var(--dim);
}
.ec__wire--broken .ec__wire-label { color: var(--red); font-weight: 700; }

/* DECOUPLED BROADCAST */
.ec__broadcast {
  position: relative;
  align-self: stretch;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 1.6rem;
}
.ec__pulse {
  position: absolute;
  left: 50%; top: 50%;
  transform: translate(-50%, -50%);
  width: 18px; height: 18px;
  border-radius: 50%;
  border: 1.5px solid var(--accent-green);
  opacity: 0;
  animation: pulse 2.4s infinite cubic-bezier(0.4, 0, 0.2, 1);
}
.ec__pulse--2 { animation-delay: 0.8s; }
.ec__pulse--3 { animation-delay: 1.6s; }
@keyframes pulse {
  0%   { transform: translate(-50%, -50%) scale(0.4); opacity: 0.75; }
  100% { transform: translate(-50%, -50%) scale(4.2);   opacity: 0; }
}
.ec__event-chip {
  position: relative;
  z-index: 1;
  background: var(--ink);
  border: 1px solid var(--accent-green);
  border-radius: 999px;
  padding: 0.2rem 0.7rem;
  font-size: 0.7rem;
  font-weight: 700;
  color: var(--accent-green);
  letter-spacing: 0.04em;
  box-shadow: 0 0 12px rgba(110,231,161,0.18);
}

/* CODE rails */
.ec__code {
  font-family: var(--font-mono);
  font-size: 0.78rem;
  line-height: 1.6;
  background: rgba(0,0,0,0.35);
  border: 1px solid rgba(255,255,255,0.06);
  border-left: 2px solid rgba(255,255,255,0.1);
  border-radius: 2px;
  padding: 0.65rem 0.9rem;
  margin: 0;
  color: #c8c2b6;
  overflow: hidden;
  white-space: pre;
}
.t-kw  { color: var(--accent-purple); font-weight: 600; }
.t-cls { color: var(--accent-blue); }
.t-ev  { color: var(--accent-green); font-weight: 600; }
.t-com { color: var(--dim); font-style: italic; }
.t-broken {
  color: var(--red);
  text-decoration: line-through;
  text-decoration-color: rgba(255,45,32,0.7);
}

/* TOOLBAR + TOGGLE */
.ec__toolbar {
  display: flex;
  justify-content: center;
  margin-top: 0.1rem;
}
.ec__toggle {
  background: transparent;
  border: 1px solid rgba(255,255,255,0.16);
  border-left: 3px solid var(--red);
  padding: 0.55rem 1.4rem;
  font-family: var(--font-mono);
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.20em;
  text-transform: uppercase;
  color: var(--bone);
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 0.7rem;
  transition: background 0.2s, border-color 0.2s, transform 0.06s;
}
.ec__toggle:hover {
  background: rgba(255,45,32,0.08);
  border-color: var(--red);
}
.ec__toggle:active { transform: translateY(1px); }
.ec__toggle.is-on {
  border-left-color: var(--accent-green);
  color: var(--accent-green);
}
.ec__toggle.is-on:hover { background: rgba(110,231,161,0.08); border-color: var(--accent-green); }
.ec__toggle-icon { font-size: 0.95rem; }
.ec__toggle-hint {
  font-size: 0.6rem;
  letter-spacing: 0.22em;
  color: var(--dim);
  font-weight: 500;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  20%      { transform: translateX(-4px); }
  40%      { transform: translateX(4px); }
  60%      { transform: translateX(-3px); }
  80%      { transform: translateX(2px); }
}
</style>
