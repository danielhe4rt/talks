---
layout: deletion-test-modular
transition: none
metaNumber: "13"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaRight: "Q2 · coupling"
---

# O Teste da Deleção™ <span>— Pergunta 2 · <span class="g g-c">coupling</span></span>

::questions::

<!-- Pergunta 1: já passou -->
<div class="p-2.5 bg-green-900/10 rounded border border-green-500/15 opacity-50">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1 opacity-70">Listar todos os arquivos?</div>
</div>

<!-- Pergunta 2: foco -->
<div v-click="1" class="p-2.5 bg-orange-900/15 rounded border border-orange-500/20">
  <div class="flex items-center justify-between">
    <span class="text-orange-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span v-click="3" class="text-yellow-400 font-bold text-sm">⚠</span>
  </div>
  <div class="text-sm mt-1">Quanto do sistema <b class="text-orange-300">quebra</b>?</div>
  <div v-click="3" class="text-[10px] text-yellow-300/70 mt-1">Ainda quebra, mas agora você SABE onde.</div>
</div>

<!-- Pergunta 3: pendente -->
<div v-click="3" class="p-2.5 bg-red-900/15 rounded border border-red-500/20 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-red-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span class="text-gray-500 font-bold text-sm">?</span>
  </div>
  <div class="text-sm mt-1">Algum arquivo <b class="text-red-300">usado</b> por outra feature?</div>
</div>

<!-- Progresso -->
<div v-click="3" class="mt-2 p-2.5 bg-yellow-900/20 rounded-lg border-2 border-yellow-500/30 text-center">
  <div class="flex justify-center gap-3 text-lg">
    <span class="text-green-400">✓</span>
    <span class="text-yellow-400">⚠</span>
    <span class="text-gray-500">?</span>
  </div>
</div>

::visual::

<!-- ============================== -->
<!-- VISUAL 1: Módulos + Payment deletado -->
<!-- ============================== -->
<div v-click="[1, 2]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-orange-400 mb-4">Deletei app/Modules/Payment/. O que aconteceu?</div>
  <div class="grid grid-cols-2 gap-3">
    <div class="px-3 py-2.5 bg-gray-700/40 rounded border border-gray-500/20 text-sm font-mono">
      <span class="opacity-70">Cart/</span>
    </div>
    <div class="px-3 py-2.5 bg-gray-700/40 rounded border border-gray-500/20 text-sm font-mono">
      <span class="opacity-70">Catalog/</span>
    </div>
    <div class="px-3 py-2.5 bg-gray-700/40 rounded border border-gray-500/20 text-sm font-mono">
      <span class="opacity-70">Checkout/</span>
    </div>
    <div class="px-3 py-2.5 bg-gray-700/40 rounded border border-gray-500/20 text-sm font-mono">
      <span class="opacity-70">Shipping/</span>
    </div>
  </div>
  <div class="mt-3 px-3 py-2.5 bg-red-900/30 rounded border border-red-500/30 text-sm font-mono line-through text-red-300/60 text-center">
    Payment/  ← DELETADO
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 2: Resultado por módulo -->
<!-- ============================== -->
<div v-click="[2, 3]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-orange-400 mb-4">Deletei app/Modules/Payment/. O que aconteceu?</div>
  <div class="grid grid-cols-2 gap-3">
    <div class="px-3 py-2.5 bg-green-900/20 rounded border border-green-500/20 text-sm font-mono flex items-center justify-between">
      <span>Cart/</span>
      <span class="text-green-400">✓ ok</span>
    </div>
    <div class="px-3 py-2.5 bg-green-900/20 rounded border border-green-500/20 text-sm font-mono flex items-center justify-between">
      <span>Catalog/</span>
      <span class="text-green-400">✓ ok</span>
    </div>
    <div class="px-3 py-2.5 bg-red-900/20 rounded border border-red-500/30 text-sm font-mono flex items-center justify-between">
      <span class="text-red-300">Checkout/</span>
      <span class="text-red-400">💥</span>
    </div>
    <div class="px-3 py-2.5 bg-green-900/20 rounded border border-green-500/20 text-sm font-mono flex items-center justify-between">
      <span>Shipping/</span>
      <span class="text-green-400">✓ ok</span>
    </div>
  </div>
  <div class="mt-4 p-3 bg-gray-800/50 rounded border border-red-500/20">
    <div class="text-[10px] text-gray-400 uppercase tracking-wider mb-1">O import que quebra:</div>
    <div class="font-mono text-xs text-red-300">
      Checkout/PlaceOrder.php
    </div>
    <div class="font-mono text-[10px] text-red-300/70 mt-1 ml-2">
      use App\Modules\<span class="line-through">Payment</span>\ProcessPayment;
    </div>
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 3: Conclusão diagnóstico -->
<!-- ============================== -->
<div v-click="3" class="absolute inset-0 flex flex-col items-center justify-center overflow-hidden">
  <div class="text-5xl font-black text-yellow-400/70 tracking-wider">DIAGNÓSTICO</div>
  <div class="mt-5 space-y-2 text-sm">
    <div class="flex items-center gap-3">
      <span class="text-green-400 text-lg">✓</span>
      <span class="opacity-70">4 módulos sobrevivem</span>
    </div>
    <div class="flex items-center gap-3">
      <span class="text-red-400 text-lg">✘</span>
      <span class="opacity-70">1 módulo quebra (Checkout → Payment)</span>
    </div>
  </div>
  <div class="mt-5 p-3 bg-yellow-900/20 rounded border border-yellow-500/25 text-center text-sm max-w-md">
    Mas agora o problema tem <b class="text-yellow-300">nome</b> e <b class="text-yellow-300">endereço</b>.
  </div>
</div>

<!--
[sem click — slide aparece com Pergunta 1 já ✓]
"Pergunta 1 passou. Agora a segunda: se eu deletar Payment/, quanto do sistema quebra?"

[click 1 — Pergunta 2 + módulos com Payment deletado]
"Deletei app/Modules/Payment/ inteiro. 5 módulos, tirei 1. O que acontece com os outros 4?"

[click 2 — resultados por módulo + import que quebra]
"Cart? Funciona. Catalog? Funciona. Shipping? Funciona. Checkout? QUEBRA. Por quê? Porque PlaceOrder.php faz um use direto: App\Modules\Payment\ProcessPayment. Esse import é um fio que liga Checkout a Payment. Cortou Payment, Checkout cai junto."

[click 3 — ⚠️ + diagnóstico + conclusão]
"Antes, quando o código tava espalhado, 3 classes quebravam e eu nem sabia por quê. Agora: 1 módulo quebra e eu sei EXATAMENTE qual import causa isso. O problema tem nome e endereço. Ainda não resolvi, mas agora eu consigo enxergar."
-->
