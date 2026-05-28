<!--
  BgLayers — the 3 stacked background layers used by every brutalist slide.

  Props:
    vignettePos: where the red radial sits — "tr" / "br" / "tl" / "bl"
                 defaults to "br" (bottom-right). Use to vary slides.
-->
<script setup lang="ts">
defineProps<{
  vignettePos?: 'tr' | 'br' | 'tl' | 'bl'
}>()
</script>

<template>
  <div class="bg-grid" />
  <div class="bg-vignette" :data-pos="vignettePos || 'br'" />
  <div class="bg-grain" />
</template>

<style scoped>
.bg-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(to right,  rgba(255, 255, 255, 0.025) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(255, 255, 255, 0.025) 1px, transparent 1px);
  background-size: 56px 56px;
  -webkit-mask-image: radial-gradient(ellipse at 30% 40%, #000 30%, transparent 80%);
          mask-image: radial-gradient(ellipse at 30% 40%, #000 30%, transparent 80%);
  pointer-events: none;
}

.bg-vignette {
  position: absolute;
  inset: 0;
  pointer-events: none;
}
.bg-vignette[data-pos="br"] {
  background:
    radial-gradient(800px 600px at 85% 90%, rgba(255, 45, 32, 0.10), transparent 60%),
    radial-gradient(600px 400px at 10% 0%,  rgba(255, 255, 255, 0.04), transparent 70%);
}
.bg-vignette[data-pos="tr"] {
  background:
    radial-gradient(800px 600px at 90% 10%, rgba(255, 45, 32, 0.10), transparent 60%),
    radial-gradient(600px 400px at 10% 100%, rgba(255, 255, 255, 0.04), transparent 70%);
}
.bg-vignette[data-pos="bl"] {
  background:
    radial-gradient(800px 600px at 15% 90%, rgba(255, 45, 32, 0.10), transparent 60%),
    radial-gradient(600px 400px at 90% 0%, rgba(255, 255, 255, 0.04), transparent 70%);
}
.bg-vignette[data-pos="tl"] {
  background:
    radial-gradient(800px 600px at 10% 10%, rgba(255, 45, 32, 0.10), transparent 60%),
    radial-gradient(600px 400px at 90% 100%, rgba(255, 255, 255, 0.04), transparent 70%);
}

.bg-grain {
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='160' height='160'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='2' stitchTiles='stitch'/><feColorMatrix values='0 0 0 0 1  0 0 0 0 1  0 0 0 0 1  0 0 0 .07 0'/></filter><rect width='100%' height='100%' filter='url(%23n)'/></svg>");
  mix-blend-mode: overlay;
  opacity: 0.35;
  pointer-events: none;
}
</style>
