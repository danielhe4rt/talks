---
layout: deletion-test-modular
transition: none
metaNumber: "17"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaPhase: red
metaRight: "Q3 · LEAKS"
---

# O Teste da Deleção™ <span>— Pergunta 3 · <span class="g g-a">leaks</span></span>

::questions::

<!-- Pergunta 1: já passou (faded) -->
<div class="p-2.5 bg-green-900/10 rounded border border-green-500/15 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1 opacity-70">Listar todos os arquivos?</div>
</div>

<!-- Pergunta 2: já passou (faded) -->
<div class="p-2.5 bg-green-900/10 rounded border border-green-500/15 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1 opacity-70">Quanto do sistema quebra?</div>
</div>

<!-- Pergunta 3: foco -->
<div v-click="1" class="p-2.5 bg-red-900/15 rounded border border-red-500/25">
  <div class="flex items-center justify-between">
    <span class="text-red-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span v-click="3" class="text-red-400 font-bold text-sm">✘</span>
  </div>
  <div class="text-sm mt-1">Algum arquivo é <b class="text-red-300">usado por outra feature</b>?</div>
  <div v-click="3" class="text-[10px] text-red-300/70 mt-1">3 features chamam o mesmo arquivo.</div>
</div>

<!-- Progresso -->
<div v-click="3" class="mt-2 p-2.5 bg-red-900/25 rounded-lg border-2 border-red-500/40 text-center">
  <div class="flex justify-center gap-3 text-lg">
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
    <span class="text-red-400">✘</span>
  </div>
</div>

::visual::

<!-- ============================== -->
<!-- VISUAL 1: Arquivo no centro    -->
<!-- ============================== -->
<div v-click="[1, 2]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-red-400 mb-5">Tudo bem isolado. Mas… olha esse arquivo:</div>
  <div class="flex justify-center">
    <div class="px-4 py-3 bg-gray-800/60 rounded border border-yellow-500/30 text-center">
      <div class="text-[10px] text-gray-400 uppercase tracking-wider mb-1">app/Modules/Payment/</div>
      <div class="text-yellow-300 font-mono text-sm font-bold">PaymentGatewayService.php</div>
    </div>
  </div>
  <div class="mt-5 text-xs opacity-60 text-center">Mora dentro de Payment. Mas quem chama?</div>
</div>

<!-- ============================== -->
<!-- VISUAL 2: Arrows from consumers -->
<!-- ============================== -->
<div v-click="[2, 3]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-red-400 mb-4">3 consumidores diferentes batem no mesmo arquivo:</div>

  <div class="flex justify-center">
    <div class="px-4 py-3 bg-gray-800/60 rounded border border-yellow-500/40 text-center">
      <div class="text-[10px] text-gray-400 uppercase tracking-wider mb-1">app/Modules/Payment/</div>
      <div class="text-yellow-300 font-mono text-sm font-bold">PaymentGatewayService.php</div>
    </div>
  </div>

  <div class="mt-5 grid grid-cols-3 gap-3">
    <div class="p-2.5 bg-gray-900/60 rounded border border-red-500/20">
      <div class="text-red-400 font-mono text-[10px] font-bold mb-0.5">↑ chamado por</div>
      <div class="font-mono text-xs text-bone">Checkout/<br>PlaceOrder.php</div>
      <div class="mt-1 inline-block text-[9px] uppercase tracking-wider text-gray-500 bg-gray-800/60 px-1.5 rounded">checkout</div>
    </div>
    <div class="p-2.5 bg-gray-900/60 rounded border border-red-500/20">
      <div class="text-red-400 font-mono text-[10px] font-bold mb-0.5">↑ chamado por</div>
      <div class="font-mono text-xs text-bone">Subscriptions/<br>RecurringChargeJob.php</div>
      <div class="mt-1 inline-block text-[9px] uppercase tracking-wider text-gray-500 bg-gray-800/60 px-1.5 rounded">subscriptions</div>
    </div>
    <div class="p-2.5 bg-gray-900/60 rounded border border-red-500/20">
      <div class="text-red-400 font-mono text-[10px] font-bold mb-0.5">↑ chamado por</div>
      <div class="font-mono text-xs text-bone">Admin/<br>RefundController.php</div>
      <div class="mt-1 inline-block text-[9px] uppercase tracking-wider text-gray-500 bg-gray-800/60 px-1.5 rounded">admin</div>
    </div>
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 3: Diagnóstico final    -->
<!-- ============================== -->
<div v-click="3" class="absolute inset-0 flex flex-col items-center justify-center overflow-hidden">
  <div class="text-6xl font-black text-red-500/70 tracking-wider">LEAK</div>
  <div class="mt-5 p-4 bg-red-900/25 rounded border border-red-500/30 text-sm max-w-lg text-center">
    <b class="text-red-300">3 features</b> compartilham esse arquivo.<br>
    Ele não é <b class="text-red-300">Payment</b> — é <b class="text-yellow-300">Gateway</b>.
  </div>
  <div class="mt-4 text-xs opacity-50">Q3 falhou. Mas agora eu sei <i>onde</i>.</div>
</div>

<!--
[sem click — Pergunta 1 e 2 já ✓, ainda sem foco no painel]
"Q1 e Q2 passaram. Beleza. Mas tem uma terceira pergunta que ninguém gosta de fazer: dos arquivos que mora dentro do módulo, algum é usado por outra feature?"

[click 1 — Pergunta 3 + arquivo no centro]
"Pega o PaymentGatewayService. Tá lá dentro de Modules/Payment/. Tudo certinho, né? Aparentemente sim. Mas quem CHAMA esse arquivo?"

[click 2 — 3 consumidores aparecem]
"Checkout chama na hora de fechar o pedido. Subscriptions chama no Job de cobrança recorrente. Admin chama quando faz refund. Três features. Três domínios diferentes. UM arquivo."

[click 3 — ✘ + LEAK + diagnóstico]
"Isso é leak. O arquivo mora em Payment, mas Payment não é dono dele — 3 features dependem. Ele não é Payment, é Gateway. E enquanto ele tiver esse nome e esse endereço errado, qualquer mudança em Payment vaza pros outros 2 módulos. Q3 falhou. Mas pelo menos agora eu sei onde."
-->
