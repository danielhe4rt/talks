---
layout: deletion-test-modular
transition: none
metaNumber: "12"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaPhase: green
metaRight: "Q1 · MODULAR"
---

# O Teste da Deleção™ <span>— rodando nos módulos</span>

::questions::

<!-- Pergunta 1: listar arquivos -->
<div v-click="1" class="p-2.5 bg-yellow-900/15 rounded border border-yellow-500/20">
  <div class="flex items-center justify-between">
    <span class="text-yellow-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span v-click="2" class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1">Listar <b class="text-yellow-300">todos</b> os arquivos de pagamento?</div>
  <div v-click="2" class="text-[10px] text-green-300/70 mt-1">Tudo em app/Modules/Payment/</div>
</div>

<!-- Pergunta 2: pendente -->
<div v-click="2" class="p-2.5 bg-orange-900/15 rounded border border-orange-500/20 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-orange-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span class="text-gray-500 font-bold text-sm">?</span>
  </div>
  <div class="text-sm mt-1">Quanto do sistema <b class="text-orange-300">quebra</b>?</div>
</div>

<!-- Pergunta 3: pendente -->
<div v-click="2" class="p-2.5 bg-red-900/15 rounded border border-red-500/20 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-red-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span class="text-gray-500 font-bold text-sm">?</span>
  </div>
  <div class="text-sm mt-1">Algum arquivo <b class="text-red-300">usado</b> por outra feature?</div>
</div>

::visual::

<!-- Tree modular com flat files -->
<div v-click="[1, 2]" class="absolute inset-0 overflow-auto">
  <div class="text-xs font-bold text-yellow-400 mb-2">Onde estão os arquivos de "pagamento"?</div>
  <div class="font-mono text-[11px] leading-[1.7]">
    <div class="opacity-40">app/Modules/</div>
    <div class="opacity-40">├── Cart/</div>
    <div class="opacity-30">│   ├── Cart.php</div>
    <div class="opacity-30">│   ├── CartItem.php</div>
    <div class="opacity-30">│   └── ...</div>
    <div class="opacity-40">├── Catalog/</div>
    <div class="opacity-30">│   ├── Product.php</div>
    <div class="opacity-30">│   ├── Category.php</div>
    <div class="opacity-30">│   └── ...</div>
    <div class="opacity-40">├── Checkout/</div>
    <div class="opacity-30">│   ├── PlaceOrder.php</div>
    <div class="opacity-30">│   ├── OrderSummary.php</div>
    <div class="opacity-30">│   └── ...</div>
    <div class="bg-green-500/15 text-green-300 rounded px-1 -mx-0.5">├── <b>Payment/</b></div>
    <div class="bg-green-500/10 text-green-300/80 rounded px-1 -mx-0.5">│   ├── <b>ProcessPayment.php</b></div>
    <div class="bg-green-500/10 text-green-300/80 rounded px-1 -mx-0.5">│   ├── <b>PaymentGateway.php</b></div>
    <div class="bg-green-500/10 text-green-300/80 rounded px-1 -mx-0.5">│   ├── <b>ChargePayment.php</b></div>
    <div class="bg-green-500/10 text-green-300/80 rounded px-1 -mx-0.5">│   └── <b>...</b></div>
    <div class="opacity-40">└── Shipping/</div>
    <div class="opacity-30">    ├── CalculateShipping.php</div>
    <div class="opacity-30">    ├── ShipmentTracker.php</div>
    <div class="opacity-30">    └── ...</div>
  </div>
</div>

<!-- Resultado: Pergunta 1 passa -->
<div v-click="2" class="absolute inset-0 flex flex-col items-center justify-center">
  <div class="text-6xl font-black text-green-500/70 tracking-wider">1 de 3</div>
  <div class="mt-4 flex gap-4 items-center">
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-gray-500 text-2xl">?</span>
    <span class="text-gray-500 text-2xl">?</span>
  </div>
  <div class="mt-4 text-sm opacity-50">Agora consigo listar. Mas será que o resto passa?</div>
</div>

<!--
[sem click — slide aparece com título e layout vazio]
"Beleza, a gente viu que não existe padrão certo de pasta. Mas uma coisa todas as 4 estruturas tinham em comum: os arquivos de pagamento ficam JUNTOS. Vamos rodar o Teste da Deleção de novo."

[click 1 — Pergunta 1 + tree modular]
"Primeira pergunta: consigo listar todos os arquivos de pagamento? Olha a diferença. Antes, 9 arquivos em 8 pastas. Agora: tudo em app/Modules/Payment/. Abro UMA pasta e vejo tudo."

[click 2 — ✓ P1 + perguntas 2 e 3 pendentes + resultado parcial]
"Passou! Primeira vez que essa pergunta passa. Mas e as outras duas? Quanto quebra se eu deletar? Algum arquivo é compartilhado? Essas a gente ainda precisa resolver. Vamos ver num caso real."
-->
