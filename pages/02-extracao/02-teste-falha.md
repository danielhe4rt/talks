---
layout: deletion-test
transition: none
---

# O Teste da Deleção™ <span class="text-sm font-normal opacity-40">— rodando no legadão</span>

::questions::

<!-- Pergunta 1: listar arquivos -->
<div v-click="1" class="p-2.5 bg-yellow-900/15 rounded border border-yellow-500/20">
  <div class="flex items-center justify-between">
    <span class="text-yellow-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span v-click="2" class="text-red-400 font-bold text-sm">✘</span>
  </div>
  <div class="text-sm mt-1">Listar <b class="text-yellow-300">todos</b> os arquivos de pagamento?</div>
  <div v-click="2" class="text-[10px] text-red-300/70 mt-1">Espalhados em 8 pastas</div>
</div>

<!-- Pergunta 2: quanto quebra -->
<div v-click="2" class="p-2.5 bg-orange-900/15 rounded border border-orange-500/20">
  <div class="flex items-center justify-between">
    <span class="text-orange-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span v-click="3" class="text-red-400 font-bold text-sm">✘</span>
  </div>
  <div class="text-sm mt-1">Quanto do sistema <b class="text-orange-300">quebra</b>?</div>
  <div v-click="3" class="text-[10px] text-red-300/70 mt-1">3 classes de outros domínios</div>
</div>

<!-- Pergunta 3: compartilhado -->
<div v-click="3" class="p-2.5 bg-red-900/15 rounded border border-red-500/20">
  <div class="flex items-center justify-between">
    <span class="text-red-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span v-click="4" class="text-red-400 font-bold text-sm">✘</span>
  </div>
  <div class="text-sm mt-1">Algum arquivo <b class="text-red-300">usado</b> por outra feature?</div>
  <div v-click="4" class="text-[10px] text-red-300/70 mt-1">Actions chamadas por 5 classes</div>
</div>

<!-- Resultado final -->
<div v-click="4" class="mt-2 p-2.5 bg-red-900/30 rounded-lg border-2 border-red-500/40 text-center">
  <div class="text-red-400 font-black text-base tracking-widest">FALHOU</div>
</div>

::visual::

<!-- ============================== -->
<!-- VISUAL 1: File tree espalhado  -->
<!-- ============================== -->
<div v-click="[1, 2]" class="absolute inset-0 overflow-auto">
  <div class="text-xs font-bold text-yellow-400 mb-2">Onde estão os arquivos de "pagamento"?</div>
  <div class="font-mono text-[11px] leading-[1.6]">
    <div class="opacity-30">app/</div>
    <div class="opacity-30">├── Actions/</div>
    <div class="opacity-30">│   ├── CreateOrderAction.php</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   ├── <b>ProcessPaymentAction.php</b></div>
    <div class="opacity-30">│   └── CalculateShippingAction.php</div>
    <div class="opacity-30">├── Jobs/</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   ├── <b>ChargePaymentJob.php</b></div>
    <div class="opacity-30">│   └── ProcessOrderJob.php</div>
    <div class="opacity-30">├── Services/</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   ├── <b>PaymentGatewayService.php</b></div>
    <div class="opacity-30">│   └── OrderService.php</div>
    <div class="opacity-30">├── Models/</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   ├── <b>Payment.php</b></div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   ├── <b>PaymentTransaction.php</b></div>
    <div class="opacity-30">│   └── Order.php</div>
    <div class="opacity-30">├── Http/Controllers/</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   └── <b>PaymentWebhookController.php</b></div>
    <div class="opacity-30">├── Notifications/</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   └── <b>PaymentConfirmation.php</b></div>
    <div class="opacity-30">├── Enums/</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">│   └── <b>PaymentStatus.php</b></div>
    <div class="opacity-30">└── Observers/</div>
    <div class="bg-yellow-500/15 text-yellow-300 rounded px-1 -mx-0.5">    └── <b>PaymentObserver.php</b></div>
  </div>
  <div class="mt-3 p-2 bg-red-900/25 rounded border border-red-500/25 text-xs text-red-300">
    <b>9 arquivos</b> em <b>8 pastas</b> diferentes. Você confia que pegou tudo?
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 2: Grafo de imports     -->
<!-- ============================== -->
<div v-click="[2, 3]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-orange-400 mb-4">Deletou "pagamento". O que quebra?</div>
  <div class="space-y-4">
    <div>
      <div class="font-mono text-xs text-gray-300">CreateOrderAction</div>
      <div class="flex items-center gap-1.5 ml-4 mt-1">
        <span class="text-gray-500 font-mono text-[10px]">↳ import</span>
        <span class="font-mono text-xs text-red-300 line-through">ProcessPaymentAction</span>
        <span class="text-red-500">💥</span>
      </div>
    </div>
    <div>
      <div class="font-mono text-xs text-gray-300">CheckoutController</div>
      <div class="flex items-center gap-1.5 ml-4 mt-1">
        <span class="text-gray-500 font-mono text-[10px]">↳ import</span>
        <span class="font-mono text-xs text-red-300 line-through">ChargePaymentJob</span>
        <span class="text-red-500">💥</span>
      </div>
    </div>
    <div>
      <div class="font-mono text-xs text-gray-300">OrderService</div>
      <div class="flex items-center gap-1.5 ml-4 mt-1">
        <span class="text-gray-500 font-mono text-[10px]">↳ import</span>
        <span class="font-mono text-xs text-red-300 line-through">PaymentGateway</span>
        <span class="text-red-500">💥</span>
      </div>
    </div>
  </div>
  <div class="mt-5 p-2.5 bg-red-900/25 rounded border border-red-500/25 text-xs text-red-300">
    <b>3 classes</b> de outros domínios quebram imediatamente.<br>
    Pedidos e Checkout dependem <b>diretamente</b> de Pagamento via import.
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 3: Uso compartilhado    -->
<!-- ============================== -->
<div v-click="[3, 4]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-red-400 mb-3">Arquivos de "pagamento" usados por outras features:</div>
  <div class="space-y-3">
    <div class="p-3 bg-gray-800/50 rounded border border-yellow-500/20">
      <div class="text-yellow-300 font-mono text-xs font-bold">ProcessPaymentAction.php</div>
      <div class="mt-2 space-y-1.5">
        <div class="flex items-center gap-2 text-xs">
          <span class="text-red-400 font-mono font-bold">←</span>
          <span class="opacity-80">CreateOrderAction.php</span>
          <span class="text-gray-500 text-[10px] bg-gray-700/50 px-1.5 rounded">pedidos</span>
        </div>
        <div class="flex items-center gap-2 text-xs">
          <span class="text-red-400 font-mono font-bold">←</span>
          <span class="opacity-80">RetryPaymentJob.php</span>
          <span class="text-gray-500 text-[10px] bg-gray-700/50 px-1.5 rounded">jobs</span>
        </div>
        <div class="flex items-center gap-2 text-xs">
          <span class="text-red-400 font-mono font-bold">←</span>
          <span class="opacity-80">AdminRefundController.php</span>
          <span class="text-gray-500 text-[10px] bg-gray-700/50 px-1.5 rounded">admin</span>
        </div>
      </div>
    </div>
    <div class="p-3 bg-gray-800/50 rounded border border-yellow-500/20">
      <div class="text-yellow-300 font-mono text-xs font-bold">PaymentGatewayService.php</div>
      <div class="mt-2 space-y-1.5">
        <div class="flex items-center gap-2 text-xs">
          <span class="text-red-400 font-mono font-bold">←</span>
          <span class="opacity-80">CheckoutService.php</span>
          <span class="text-gray-500 text-[10px] bg-gray-700/50 px-1.5 rounded">checkout</span>
        </div>
        <div class="flex items-center gap-2 text-xs">
          <span class="text-red-400 font-mono font-bold">←</span>
          <span class="opacity-80">SubscriptionJob.php</span>
          <span class="text-gray-500 text-[10px] bg-gray-700/50 px-1.5 rounded">assinaturas</span>
        </div>
      </div>
    </div>
  </div>
  <div class="mt-3 p-2 bg-red-900/25 rounded border border-red-500/25 text-xs text-red-300">
    <b>Acoplamento direto.</b> Nenhum arquivo é exclusivo de "pagamento".
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 4: Resultado FALHOU     -->
<!-- ============================== -->
<div v-click="4" class="absolute inset-0 flex flex-col items-center justify-center">
  <div class="text-7xl font-black text-red-500/70 tracking-widest">FALHOU</div>
  <div class="mt-4 flex gap-4">
    <span class="text-red-400 text-2xl">✘</span>
    <span class="text-red-400 text-2xl">✘</span>
    <span class="text-red-400 text-2xl">✘</span>
  </div>
  <div class="mt-4 text-sm opacity-50">O legadão não passa no Teste da Deleção.</div>
</div>

<!--
[sem click — slide aparece com título e layout vazio]
"Vamos rodar o Teste da Deleção no nosso legadão. A funcionalidade que vou tentar deletar: pagamento."

[click 1 — Pergunta 1 + file tree]
"Primeira pergunta: consigo listar todos os arquivos de pagamento? Olha só... ProcessPaymentAction tá em Actions. ChargePaymentJob tá em Jobs. PaymentGatewayService tá em Services. Payment e PaymentTransaction tão em Models. Webhook controller em Http. Notification em Notifications. Enum em Enums. Observer em Observers. São 9 arquivos espalhados em 8 pastas diferentes. Você confia que pegou tudo? Eu não confio."

[click 2 — ✘ P1 + Pergunta 2 + grafo de imports]
"Falhou. Segunda pergunta: se eu deletar esses 9 arquivos, quanto quebra? CreateOrderAction importa ProcessPaymentAction diretamente. CheckoutController importa ChargePaymentJob. OrderService importa PaymentGateway. Três classes de outros domínios quebram na hora. Pedidos e Checkout dependem diretamente de Pagamento."

[click 3 — ✘ P2 + Pergunta 3 + uso compartilhado]
"Falhou também. Terceira pergunta: algum desses arquivos é usado por outra feature? ProcessPaymentAction é chamada por CreateOrderAction de pedidos, por RetryPaymentJob de jobs, e por AdminRefundController do admin. PaymentGatewayService é chamada por CheckoutService e SubscriptionJob. Tudo acoplado."

[click 4 — ✘ P3 + FALHOU]
"Falhou as três. O legadão não passa no Teste da Deleção. E agora? Como a gente resolve isso?"
-->
