---
layout: deletion-test-modular
transition: none
metaNumber: "16"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaPhase: green
metaRight: "Q2 · EVENTOS"
---

# O Teste da Deleção™ <span>— Pergunta 2 (de novo)</span>

::questions::

<!-- Pergunta 1: já passou -->
<div class="p-2.5 bg-green-900/10 rounded border border-green-500/15 opacity-50">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1 opacity-70">Listar todos os arquivos?</div>
</div>

<!-- Pergunta 2: agora passa -->
<div v-click="1" class="p-2.5 bg-orange-900/15 rounded border border-orange-500/20">
  <div class="flex items-center justify-between">
    <span class="text-orange-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span v-click="2" class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1">Quanto do sistema <b class="text-orange-300">quebra</b>?</div>
  <div v-click="2" class="text-[10px] text-green-300/70 mt-1">Nada. Sem imports cruzados.</div>
</div>

<!-- Pergunta 3: pendente -->
<div v-click="2" class="p-2.5 bg-red-900/15 rounded border border-red-500/20 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-red-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span class="text-gray-500 font-bold text-sm">?</span>
  </div>
  <div class="text-sm mt-1">Algum arquivo <b class="text-red-300">usado</b> por outra feature?</div>
</div>

<!-- Progresso -->
<div v-click="2" class="mt-2 p-2.5 bg-green-900/20 rounded-lg border-2 border-green-500/30 text-center">
  <div class="flex justify-center gap-3 text-lg">
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
    <span class="text-gray-500">?</span>
    <span class="text-gray-500">?</span>
  </div>
</div>

::visual::

<!-- ============================== -->
<!-- VISUAL 1: Módulos — todos ok   -->
<!-- ============================== -->
<div v-click="[1, 2]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
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
    <div class="px-3 py-2.5 bg-green-900/20 rounded border border-green-500/20 text-sm font-mono flex items-center justify-between">
      <span>Checkout/</span>
      <span class="text-green-400">✓ ok</span>
    </div>
    <div class="px-3 py-2.5 bg-green-900/20 rounded border border-green-500/20 text-sm font-mono flex items-center justify-between">
      <span>Shipping/</span>
      <span class="text-green-400">✓ ok</span>
    </div>
  </div>
  <div class="mt-4 p-3 bg-green-900/15 rounded border border-green-500/20 text-xs text-green-300">
    <b>Checkout não importa Payment.</b><br>
    O evento <code class="text-green-200">OrderPlaced</code> pertence ao Checkout.<br>
    Payment só escuta — se sumir, ninguém percebe.
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 2: Resultado ✓          -->
<!-- ============================== -->
<div v-click="2" class="absolute inset-0 flex flex-col items-center justify-center overflow-hidden">
  <div class="text-5xl font-black text-green-500/70 tracking-wider">2 de 4</div>
  <div class="mt-4 flex gap-4">
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-gray-500 text-2xl">?</span>
    <span class="text-gray-500 text-2xl">?</span>
  </div>
  <div class="mt-4 text-sm opacity-50">Faltam duas perguntas.</div>
</div>

<!--
[sem click — Pergunta 1 já ✓]
"Agora com eventos, vamos rodar o teste de novo. Deletei Payment/."

[click 1 — Pergunta 2 + módulos todos verdes]
"Cart? Ok. Catalog? Ok. Shipping? Ok. E Checkout? TAMBÉM OK! Checkout não importa mais nada de Payment. O evento OrderPlaced pertence ao próprio Checkout. Payment escuta, mas se Payment sumir, o evento dispara pro vazio. Ninguém quebra."

[click 2 — ✓ P2 + PASSOU + Pergunta 3 pendente]
"Pergunta 2: passou! Duas de três. Falta uma."
-->
