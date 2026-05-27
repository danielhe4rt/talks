<script setup lang="ts">
defineProps({
  x: { type: Number, required: true },
  y: { type: Number, required: true },
  width: { type: Number, default: 130 },
  height: { type: Number, default: 70 },
  name: { type: String, required: true },
  subtitle: { type: String, default: '' },
  color: { type: String, default: '#60a5fa' },
  status: { type: String, default: 'active' },
  dim: { type: Boolean, default: false },
})
</script>

<template>
  <g :transform="`translate(${x}, ${y})`"
     :opacity="dim ? 0.2 : (status === 'deleted' ? 0.12 : 1)"
     style="transition: opacity 0.5s ease">

    <rect v-if="status === 'error'" x="-3" y="-3"
          :width="width + 6" :height="height + 6" rx="11"
          fill="rgba(239,68,68,0.1)" />
    <rect v-if="status === 'healthy'" x="-3" y="-3"
          :width="width + 6" :height="height + 6" rx="11"
          fill="rgba(74,222,128,0.07)" />

    <rect :width="width" :height="height" rx="8"
          :fill="status === 'error'
            ? 'rgba(239,68,68,0.06)'
            : `rgba(${parseInt(color.slice(1,3),16)},${parseInt(color.slice(3,5),16)},${parseInt(color.slice(5,7),16)},0.06)`"
          :stroke="status === 'error' ? '#ef4444' : color"
          :stroke-width="dim ? 1 : 2"
          :stroke-dasharray="status === 'deleted' ? '4 3' : 'none'"
          style="transition: all 0.4s ease" />

    <text :x="width / 2" :y="subtitle ? height / 2 - 8 : height / 2 - 2"
          text-anchor="middle"
          :fill="status === 'error' ? '#ef4444' : (dim ? 'rgba(255,255,255,0.4)' : color)"
          font-size="14" font-weight="700"
          font-family="'Fira Code', monospace"
          style="transition: fill 0.4s ease">
      {{ name }}
    </text>

    <text v-if="subtitle && status === 'active'"
          :x="width / 2" :y="height / 2 + 8"
          text-anchor="middle" fill="rgba(255,255,255,0.3)"
          font-size="9">
      {{ subtitle }}
    </text>

    <text v-if="status === 'error'"
          :x="width / 2" :y="height / 2 + 22"
          text-anchor="middle" fill="#ef4444"
          font-size="10" font-weight="600">
      ✘ Fatal Error
    </text>
    <text v-if="status === 'healthy'"
          :x="width / 2" :y="height / 2 + 22"
          text-anchor="middle" fill="#4ade80"
          font-size="10" font-weight="600">
      ✓ Funciona
    </text>

    <g v-if="status === 'deleted'" opacity="0.7">
      <line :x1="12" :y1="12" :x2="width - 12" :y2="height - 12"
            stroke="#ef4444" stroke-width="2.5" stroke-linecap="round" />
      <line :x1="width - 12" :y1="12" :x2="12" :y2="height - 12"
            stroke="#ef4444" stroke-width="2.5" stroke-linecap="round" />
    </g>
  </g>
</template>
