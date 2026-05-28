<!--
  TitleBlock — the signature brutalist title pattern.

  Renders an optional italic-serif eyebrow, a two-line display title
  (first line outlined, second solid with a red accent glyph), and an
  optional red rule + small uppercase tail.

  Props:
    eyebrow  — small italic line above the title ("antes de mergulhar")
    outlined — first line of the title (rendered in -webkit-text-stroke)
    solid    — second line of the title (solid bone color)
    accent   — colored glyph appended to the solid line ("/", "?", ".")
    tail     — small uppercase text shown after the red rule
    size     — "cover" (huge, 6.2rem) | "normal" (4.1rem, default) | "small" (3rem)

  Variants are pure CSS — set `size` to scale.
-->
<script setup lang="ts">
defineProps<{
  eyebrow?: string
  outlined?: string
  solid?: string
  accent?: string
  tail?: string
  size?: 'cover' | 'normal' | 'small'
}>()
</script>

<template>
  <div class="title-block" :data-size="size || 'normal'">
    <div v-if="eyebrow" class="title-eyebrow">
      <span class="eyebrow-mark">◆</span>
      <span>{{ eyebrow }}</span>
    </div>

    <h1 v-if="outlined || solid" class="title">
      <span v-if="outlined" class="title-line title-line--outline">{{ outlined }}</span>
      <span v-if="solid" class="title-line title-line--solid">
        {{ solid }}<span v-if="accent" class="title-accent">{{ accent }}</span>
      </span>
    </h1>

    <div v-if="tail" class="title-rule">
      <span class="rule-block" />
      <span class="rule-line" />
      <span class="rule-tail">{{ tail }}</span>
    </div>
  </div>
</template>

<style scoped>
.title-block { position: relative; }

.title-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1rem;
  color: #b9b3a9;
  margin-bottom: 0.25rem;
  letter-spacing: 0.01em;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.25s;
}
.eyebrow-mark { color: var(--red); font-size: 0.7rem; transform: translateY(-1px); }

.title {
  font-family: var(--font-display);
  font-weight: 900;
  letter-spacing: -0.005em;
  margin: 0;
  display: flex;
  flex-direction: column;
}
.title[data-size="cover"]  { font-size: 6.2rem; line-height: 0.92; padding-top: 0.15rem; }
.title-block[data-size="cover"]  .title { font-size: 6.2rem; line-height: 0.92; padding-top: 0.15rem; }
.title-block[data-size="normal"] .title { font-size: 4.1rem; line-height: 0.92; }
.title-block[data-size="small"]  .title { font-size: 3rem;   line-height: 0.94; }

.title-line { display: block; white-space: nowrap; }

.title-line--outline {
  color: transparent;
  -webkit-text-stroke: 1.6px var(--bone);
  opacity: 0.92;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.35s;
}
.title-block[data-size="cover"] .title-line--outline { -webkit-text-stroke-width: 2px; }

.title-line--solid {
  color: var(--bone);
  margin-left: 1.4rem;
  animation: title-wipe 0.7s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.55s;
}
.title-block[data-size="cover"] .title-line--solid { margin-left: 2.5rem; }

.title-accent {
  color: var(--red);
  display: inline-block;
  text-shadow: 0 0 22px rgba(255, 45, 32, 0.45);
  margin-left: 0.04em;
}

.title-rule {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin: 0.85rem 0 0.5rem 1.4rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.85s;
}
.title-block[data-size="cover"] .title-rule { margin-left: 2.5rem; gap: 0.75rem; margin-top: 1.3rem; }

.rule-block {
  width: 46px;
  height: 11px;
  background: var(--red);
  box-shadow: 0 0 22px rgba(255, 45, 32, 0.4);
}
.title-block[data-size="cover"] .rule-block { width: 56px; height: 14px; }
.title-block[data-size="small"]  .rule-block { width: 38px; height: 9px; }

.rule-line {
  flex: 0 0 180px;
  height: 2px;
  background: linear-gradient(to right, var(--red), transparent);
}
.title-block[data-size="cover"] .rule-line { flex-basis: 220px; }
.title-block[data-size="small"]  .rule-line { flex-basis: 90px; }

.rule-tail {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--dim);
}
</style>
