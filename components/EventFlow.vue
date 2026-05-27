<script setup lang="ts">
import { ref, computed } from 'vue'

const mode = ref<'coupled' | 'decoupled'>('coupled')
const deleted = ref(false)

const isCoupled = computed(() => mode.value === 'coupled')
const hasError = computed(() => deleted.value && isCoupled.value)
const isHealthy = computed(() => deleted.value && !isCoupled.value)

function toggleMode() {
  mode.value = isCoupled.value ? 'decoupled' : 'coupled'
  deleted.value = false
}

function toggleDelete() {
  deleted.value = !deleted.value
}
</script>

<template>
  <div class="ef">
    <svg class="ef__canvas" viewBox="0 0 800 200" preserveAspectRatio="xMidYMid meet">
      <defs>
        <marker id="ef-a" markerWidth="7" markerHeight="5" refX="7" refY="2.5" orient="auto">
          <path d="M0,0 L7,2.5 L0,5" fill="none" stroke="rgba(255,255,255,0.25)" stroke-width="1.2" />
        </marker>
        <marker id="ef-ar" markerWidth="7" markerHeight="5" refX="7" refY="2.5" orient="auto">
          <path d="M0,0 L7,2.5 L0,5" fill="none" stroke="#ef4444" stroke-width="1.2" />
        </marker>
        <marker id="ef-ag" markerWidth="7" markerHeight="5" refX="7" refY="2.5" orient="auto">
          <path d="M0,0 L7,2.5 L0,5" fill="none" stroke="#4ade80" stroke-width="1.2" />
        </marker>
      </defs>

      <!-- ── DIM MODULES ── -->
      <g opacity="0.2">
        <rect x="20" y="10" width="75" height="28" rx="4" fill="none" stroke="rgba(255,255,255,0.2)" />
        <text x="57" y="29" text-anchor="middle" fill="rgba(255,255,255,0.5)" font-size="9" font-family="'Fira Code',monospace">Cart</text>
      </g>
      <g opacity="0.2">
        <rect x="20" y="162" width="75" height="28" rx="4" fill="none" stroke="rgba(255,255,255,0.2)" />
        <text x="57" y="181" text-anchor="middle" fill="rgba(255,255,255,0.5)" font-size="9" font-family="'Fira Code',monospace">Catalog</text>
      </g>
      <g opacity="0.2">
        <rect x="705" y="10" width="75" height="28" rx="4" fill="none" stroke="rgba(255,255,255,0.2)" />
        <text x="742" y="29" text-anchor="middle" fill="rgba(255,255,255,0.5)" font-size="9" font-family="'Fira Code',monospace">Shipping</text>
      </g>

      <!-- ── CHECKOUT ── -->
      <g>
        <rect v-if="hasError" x="198" y="48" width="124" height="74" rx="9"
              fill="rgba(239,68,68,0.06)" />
        <rect v-if="isHealthy" x="198" y="48" width="124" height="74" rx="9"
              fill="rgba(74,222,128,0.04)" />

        <rect x="200" y="50" width="120" height="70" rx="7"
              :fill="hasError ? 'rgba(239,68,68,0.04)' : 'rgba(96,165,250,0.04)'"
              :stroke="hasError ? '#ef4444' : '#60a5fa'" stroke-width="1.5"
              style="transition: all 0.4s" />
        <text x="260" y="80" text-anchor="middle"
              :fill="hasError ? '#ef4444' : '#60a5fa'"
              font-size="12" font-weight="700" font-family="'Fira Code',monospace"
              style="transition: fill 0.4s">Checkout</text>
        <text x="260" y="94" text-anchor="middle" fill="rgba(255,255,255,0.2)" font-size="7.5">
          {{ isCoupled ? 'import direto' : 'dispatch event' }}
        </text>

        <text v-if="hasError" x="260" y="110" text-anchor="middle"
              fill="#ef4444" font-size="8" font-weight="600">✘ Fatal Error</text>
        <text v-if="isHealthy" x="260" y="110" text-anchor="middle"
              fill="#4ade80" font-size="8" font-weight="600">✓ Funciona</text>
      </g>

      <!-- ── COUPLED CONNECTION ── -->
      <g v-if="isCoupled">
        <line x1="322" y1="85" x2="478" y2="85"
              :stroke="hasError ? '#ef4444' : 'rgba(255,255,255,0.18)'"
              :stroke-width="hasError ? 1.5 : 1.2"
              :stroke-dasharray="hasError ? '4 3' : 'none'"
              :marker-end="hasError ? 'url(#ef-ar)' : 'url(#ef-a)'"
              style="transition: all 0.4s" />
        <text x="400" y="76" text-anchor="middle"
              :fill="hasError ? '#ef4444' : 'rgba(255,255,255,0.2)'"
              font-size="7.5" font-family="'Fira Code',monospace"
              style="transition: fill 0.4s">
          {{ hasError ? '💥 QUEBROU' : 'use Payment\\...' }}
        </text>

        <circle v-if="!hasError" cx="325" cy="85" r="2" fill="#60a5fa" opacity="0">
          <animate attributeName="cx" from="325" to="475" dur="2s" repeatCount="indefinite" />
          <animate attributeName="opacity" values="0;0.8;0.8;0" keyTimes="0;0.08;0.85;1" dur="2s" repeatCount="indefinite" />
        </circle>
      </g>

      <!-- ── DECOUPLED CONNECTION ── -->
      <g v-else>
        <circle cx="325" cy="85" fill="none" stroke="#4ade80" opacity="0">
          <animate attributeName="r" from="3" to="50" dur="2.5s" repeatCount="indefinite" />
          <animate attributeName="opacity" from="0.35" to="0" dur="2.5s" repeatCount="indefinite" />
        </circle>
        <circle cx="325" cy="85" fill="none" stroke="#4ade80" opacity="0">
          <animate attributeName="r" from="3" to="50" dur="2.5s" begin="0.5s" repeatCount="indefinite" />
          <animate attributeName="opacity" from="0.2" to="0" dur="2.5s" begin="0.5s" repeatCount="indefinite" />
        </circle>

        <rect x="348" y="70" width="68" height="14" rx="7"
              fill="rgba(74,222,128,0.08)" stroke="#4ade80" stroke-width="0.7" />
        <text x="382" y="81" text-anchor="middle" fill="#4ade80" font-size="7.5" font-weight="600">OrderPlaced</text>

        <line v-if="!deleted" x1="418" y1="85" x2="478" y2="85"
              stroke="#4ade80" stroke-width="0.8" stroke-dasharray="3 2"
              marker-end="url(#ef-ag)" opacity="0.3" />

        <circle v-if="!deleted" cx="325" cy="85" r="2" fill="#4ade80" opacity="0">
          <animate attributeName="cx" from="325" to="475" dur="2.5s" repeatCount="indefinite" />
          <animate attributeName="opacity" values="0;0.6;0.6;0" keyTimes="0;0.1;0.75;1" dur="2.5s" repeatCount="indefinite" />
        </circle>
      </g>

      <!-- ── PAYMENT ── -->
      <g :style="{ opacity: deleted ? 0.1 : 1, transition: 'opacity 0.5s' }">
        <rect x="480" y="50" width="120" height="70" rx="7"
              fill="rgba(249,115,22,0.04)"
              :stroke="deleted ? 'rgba(255,255,255,0.06)' : '#f97316'"
              :stroke-width="deleted ? 0.8 : 1.5"
              :stroke-dasharray="deleted ? '3 2' : 'none'"
              style="transition: all 0.4s" />
        <text x="540" y="80" text-anchor="middle"
              :fill="deleted ? 'rgba(255,255,255,0.15)' : '#f97316'"
              font-size="12" font-weight="700" font-family="'Fira Code',monospace"
              style="transition: fill 0.4s">Payment</text>
        <text v-if="!deleted" x="540" y="94" text-anchor="middle" fill="rgba(255,255,255,0.2)" font-size="7.5">
          {{ isCoupled ? 'dependência' : '📡 listener' }}
        </text>
      </g>

      <!-- Deleted X -->
      <g v-if="deleted" opacity="0.5">
        <line x1="492" y1="58" x2="588" y2="112" stroke="#ef4444" stroke-width="2" stroke-linecap="round" />
        <line x1="588" y1="58" x2="492" y2="112" stroke="#ef4444" stroke-width="2" stroke-linecap="round" />
      </g>

      <!-- ── RESULT BADGE ── -->
      <g v-if="hasError">
        <rect x="325" y="148" width="150" height="22" rx="4"
              fill="rgba(239,68,68,0.06)" stroke="rgba(239,68,68,0.2)" stroke-width="0.8" />
        <text x="400" y="163" text-anchor="middle" fill="#fca5a5" font-size="9" font-weight="600">
          Checkout quebra 💥
        </text>
      </g>
      <g v-if="isHealthy">
        <rect x="315" y="148" width="170" height="22" rx="4"
              fill="rgba(74,222,128,0.04)" stroke="rgba(74,222,128,0.15)" stroke-width="0.8" />
        <text x="400" y="163" text-anchor="middle" fill="#86efac" font-size="9" font-weight="600">
          Sistema intacto ✓
        </text>
      </g>
    </svg>

    <!-- Controls -->
    <div class="ef__controls">
      <button @click="toggleMode" class="ef__btn"
              :class="isCoupled ? 'ef__btn--red' : 'ef__btn--green'">
        {{ isCoupled ? '🔗 Acoplado (import direto)' : '📡 Desacoplado (evento)' }}
      </button>
      <button @click="toggleDelete" class="ef__btn ef__btn--ghost">
        {{ deleted ? '↩ Restaurar Payment' : '🗑 Deletar Payment' }}
      </button>
    </div>

    <!-- Code snippet -->
    <div class="ef__code">
      <div class="ef__code-file">Checkout/PlaceOrder.php</div>
      <div v-if="isCoupled" class="ef__code-body">
        <span class="c-kw">use</span> App\Modules\<span :class="hasError ? 'c-err' : 'c-cls'">Payment</span>\ProcessPayment;
        <br />(new ProcessPayment)-&gt;execute($order);
      </div>
      <div v-else class="ef__code-body">
        <span class="c-kw">use</span> App\Modules\<span class="c-cls">Checkout</span>\Events\<span class="c-ev">OrderPlaced</span>;
        <br />OrderPlaced::dispatch($order);
        <span class="c-dim"> // quem escuta não é problema meu</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.ef {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.ef__canvas {
  width: 100%;
  display: block;
}

.ef__controls {
  display: flex;
  gap: 8px;
  justify-content: center;
  flex-shrink: 0;
}

.ef__btn {
  padding: 5px 14px;
  border-radius: 6px;
  font-size: 11px;
  font-weight: 600;
  cursor: pointer;
  border: 1px solid;
  transition: all 0.2s;
  background: transparent;
  color: #fff;
  font-family: inherit;
}

.ef__btn--red {
  border-color: rgba(239, 68, 68, 0.4);
  color: #fca5a5;
}
.ef__btn--red:hover {
  background: rgba(239, 68, 68, 0.1);
}

.ef__btn--green {
  border-color: rgba(74, 222, 128, 0.4);
  color: #86efac;
}
.ef__btn--green:hover {
  background: rgba(74, 222, 128, 0.1);
}

.ef__btn--ghost {
  border-color: rgba(255, 255, 255, 0.12);
  color: rgba(255, 255, 255, 0.5);
}
.ef__btn--ghost:hover {
  background: rgba(255, 255, 255, 0.05);
}

.ef__code {
  background: rgba(0, 0, 0, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 6px;
  padding: 6px 12px;
  font-family: 'Fira Code', monospace;
  font-size: 11px;
  line-height: 1.5;
  flex-shrink: 0;
}

.ef__code-file {
  font-size: 9px;
  color: rgba(255, 255, 255, 0.2);
  margin-bottom: 2px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.ef__code-body {
  color: rgba(255, 255, 255, 0.6);
}

.c-kw { color: #c084fc; }
.c-cls { color: #60a5fa; }
.c-ev { color: #4ade80; }
.c-err { color: #ef4444; text-decoration: line-through; }
.c-dim { color: rgba(255, 255, 255, 0.2); }
</style>
