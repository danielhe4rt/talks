<!--
  StructTree — a colored, legible folder tree (replaces tiny monochrome
  `text` code blocks across the deck).

  Rendering language (consistent everywhere):
    - folders   → the chosen `accent` color, bold (the "scaffolding")
    - domain    → fixed red ◆ marker + bright name  (the file(s) the story
                  is about — tracked by eye across slides)
    - support   → dim · marker (everything else)
    - note      → optional inline tag after a node ("← leak", "← novo", …)

  Two modes:

  1) Variant mode — the cart module in one of 4 structures
     (02-extracao/03-estruturas.md). Single source of truth.
       <StructTree variant="flat" accent="blue" />

  2) Ad-hoc mode — pass your own tree (e.g. 02-extracao/10-gateway.md).
       <StructTree
         root="app/Modules/"
         accent="red"
         compact
         :tree="[{ name:'Payment/', kind:'dir', children:[…] }]"
       />
     In ad-hoc mode the namespace line and legend are hidden by default;
     pass `ns="…"` or `:legend="true"` to show them.
-->
<script setup lang="ts">
import { computed } from 'vue'

type Kind = 'dir' | 'domain' | 'support'
type Note = 'danger' | 'ok' | 'dim'
interface Node { name: string; kind: Kind; note?: string; noteKind?: Note; children?: Node[] }

const props = defineProps<{
  variant?: 'flat' | 'laravel' | 'clean' | 'ddd'
  accent?: 'red' | 'blue' | 'green' | 'purple' | 'orange'
  /* ad-hoc mode */
  tree?: Node[]
  root?: string
  count?: string
  ns?: string
  legend?: boolean
  compact?: boolean
  /** explicit font-size override, e.g. "0.72rem" (wins over `compact`) */
  fs?: string
}>()

const VARIANTS: Record<string, { root: string; count: string; tree: Node[] }> = {
  flat: {
    root: 'app/Modules/Cart/',
    count: '5 arquivos · 0 subpastas',
    tree: [
      { name: 'Cart.php', kind: 'domain' },
      { name: 'CartItem.php', kind: 'domain' },
      { name: 'CartService.php', kind: 'support' },
      { name: 'PriceCalculator.php', kind: 'domain' },
      { name: 'ClearExpiredCartsJob.php', kind: 'support' },
    ],
  },
  laravel: {
    root: 'app/Modules/Cart/',
    count: '5 arquivos · 4 subpastas',
    tree: [
      { name: 'Models/', kind: 'dir', children: [
        { name: 'Cart.php', kind: 'domain' },
        { name: 'CartItem.php', kind: 'domain' },
      ] },
      { name: 'Services/', kind: 'dir', children: [
        { name: 'CartService.php', kind: 'support' },
      ] },
      { name: 'Jobs/', kind: 'dir', children: [
        { name: 'ClearExpiredCartsJob.php', kind: 'support' },
      ] },
      { name: 'Support/', kind: 'dir', children: [
        { name: 'PriceCalculator.php', kind: 'domain' },
      ] },
    ],
  },
  clean: {
    root: 'app/Modules/Cart/',
    count: '5 arquivos · 3 camadas',
    tree: [
      { name: 'Domain/', kind: 'dir', children: [
        { name: 'Cart.php', kind: 'domain' },
        { name: 'CartItem.php', kind: 'domain' },
        { name: 'PriceCalculator.php', kind: 'domain' },
      ] },
      { name: 'Application/', kind: 'dir', children: [
        { name: 'CartService.php', kind: 'support' },
      ] },
      { name: 'Infrastructure/', kind: 'dir', children: [
        { name: 'ClearExpiredCartsJob.php', kind: 'support' },
      ] },
    ],
  },
  ddd: {
    root: 'app/Modules/Cart/',
    count: '6 arquivos · 7 subpastas',
    tree: [
      { name: 'Domain/', kind: 'dir', children: [
        { name: 'Models/', kind: 'dir', children: [
          { name: 'Cart.php', kind: 'domain' },
          { name: 'CartItem.php', kind: 'domain' },
        ] },
        { name: 'Services/', kind: 'dir', children: [
          { name: 'PriceCalculator.php', kind: 'domain' },
        ] },
      ] },
      { name: 'Application/', kind: 'dir', children: [
        { name: 'Actions/', kind: 'dir', children: [
          { name: 'AddToCartAction.php', kind: 'support' },
        ] },
        { name: 'Jobs/', kind: 'dir', children: [
          { name: 'ClearExpiredCartsJob.php', kind: 'support' },
        ] },
      ] },
      { name: 'Infrastructure/', kind: 'dir', children: [
        { name: 'EloquentCartRepository.php', kind: 'support' },
      ] },
    ],
  },
}

const isAdHoc = computed(() => Array.isArray(props.tree))
const data = computed(() =>
  isAdHoc.value
    ? { root: props.root || '', count: props.count || '', tree: props.tree as Node[] }
    : VARIANTS[props.variant || 'flat'],
)
const ns = computed(() =>
  props.ns !== undefined ? props.ns : (isAdHoc.value ? '' : 'namespace App\\Modules\\Cart'),
)
const showLegend = computed(() =>
  props.legend !== undefined ? props.legend : !isAdHoc.value,
)
const showFoot = computed(() => Boolean(data.value.count) || showLegend.value)

interface Line { prefix: string; name: string; kind: Kind; note?: string; noteKind?: Note }
function flatten(nodes: Node[], parentPrefix = '', acc: Line[] = []): Line[] {
  nodes.forEach((node, i) => {
    const last = i === nodes.length - 1
    acc.push({
      prefix: parentPrefix + (last ? '└── ' : '├── '),
      name: node.name,
      kind: node.kind,
      note: node.note,
      noteKind: node.noteKind,
    })
    if (node.children) flatten(node.children, parentPrefix + (last ? '    ' : '│   '), acc)
  })
  return acc
}
const lines = computed(() => flatten(data.value.tree))

const marker = (k: Kind) => (k === 'domain' ? '◆' : k === 'support' ? '·' : '')
</script>

<template>
  <div class="st" :class="{ 'st--compact': compact }">
    <div v-if="ns" class="st-ns">{{ ns }}</div>

    <div class="st-tree" :data-accent="accent || 'blue'" :style="fs ? { '--st-fs': fs } : undefined">
      <div class="st-root">{{ data.root }}</div>
      <div
        v-for="(line, i) in lines"
        :key="i"
        class="st-line"
        :class="`st-line--${line.kind}`"
        :style="{ animationDelay: 0.12 + i * 0.035 + 's' }"
      >
        <span class="st-prefix">{{ line.prefix }}</span>
        <span class="st-marker">{{ marker(line.kind) }}</span>
        <span class="st-name">{{ line.name }}</span>
        <span v-if="line.note" class="st-note" :class="`st-note--${line.noteKind || 'dim'}`">{{ line.note }}</span>
      </div>
    </div>

    <div v-if="showFoot" class="st-foot">
      <span v-if="data.count" class="st-count">{{ data.count }}</span>
      <span v-if="showLegend" class="st-legend">
        <span class="lg lg--domain"><b>◆</b> domínio</span>
        <span class="lg lg--support"><b>·</b> suporte</span>
      </span>
    </div>
  </div>
</template>

<style scoped>
.st {
  display: flex;
  flex-direction: column;
  min-width: 0;
}

.st-ns {
  font-family: var(--font-mono);
  font-size: 0.66rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--dim);
  margin-bottom: 0.55rem;
}

.st-tree {
  --acc: var(--bone);
  --st-fs: 0.92rem;
  --st-lh: 1.5;
  font-family: var(--font-mono);
  font-size: var(--st-fs);
  line-height: var(--st-lh);
  padding: 0.7rem 0.9rem 0.75rem;
  border-radius: 4px;
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-left: 3px solid var(--acc);
  background: linear-gradient(180deg, rgba(20, 20, 24, 0.55), rgba(10, 10, 12, 0.78));
  box-shadow: 0 16px 34px -22px rgba(0, 0, 0, 0.7);
}
.st--compact .st-tree { --st-fs: 0.8rem; --st-lh: 1.45; padding: 0.55rem 0.75rem 0.6rem; }

.st-tree[data-accent="red"]    { --acc: var(--red); }
.st-tree[data-accent="blue"]   { --acc: var(--accent-blue); }
.st-tree[data-accent="green"]  { --acc: var(--accent-green); }
.st-tree[data-accent="purple"] { --acc: var(--accent-purple); }
.st-tree[data-accent="orange"] { --acc: var(--accent-orange); }

.st-root {
  color: var(--acc);
  font-weight: 700;
  margin-bottom: 0.1rem;
  animation: st-row 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}

.st-line {
  display: flex;
  align-items: baseline;
  white-space: pre;
  animation: st-row 0.4s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}
.st-prefix { color: #45454a; }
.st-marker {
  display: inline-block;
  width: 1.1ch;
  text-align: center;
  flex: none;
}
.st-name { white-space: pre; }

/* folders — the changing scaffolding, in the pattern accent */
.st-line--dir .st-name {
  color: var(--acc);
  font-weight: 700;
}

/* domain / highlight — fixed red ◆, the file(s) the story is about */
.st-line--domain .st-marker {
  color: var(--red);
  text-shadow: 0 0 10px rgba(255, 45, 32, 0.55);
}
.st-line--domain .st-name {
  color: var(--bone);
  font-weight: 700;
}

/* support — services / jobs / consumers, dimmed */
.st-line--support .st-marker { color: var(--dim); }
.st-line--support .st-name   { color: #8f8a80; }

/* inline note tag ("← leak", "← novo", …) */
.st-note {
  margin-left: 0.6ch;
  font-weight: 700;
  white-space: nowrap;
}
.st-note--danger { color: var(--accent-orange); }
.st-note--ok     { color: var(--accent-green); }
.st-note--dim    { color: var(--dim); }

.st-foot {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.8rem;
  margin-top: 0.55rem;
  flex-wrap: wrap;
}
.st-count {
  font-family: var(--font-mono);
  font-size: 0.64rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--dim);
}
.st-legend {
  display: inline-flex;
  align-items: center;
  gap: 0.7rem;
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--dim);
}
.lg { display: inline-flex; align-items: center; gap: 0.3rem; }
.lg--domain b { color: var(--red); }
.lg--support b { color: var(--dim); font-weight: 700; }

@keyframes st-row {
  from { opacity: 0; transform: translateX(-6px); }
  to   { opacity: 1; transform: translateX(0); }
}
</style>
