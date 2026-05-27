---

# Não existe padrão certo de pastas

O módulo `payment` organizado de **4 formas diferentes**:

<div class="grid grid-cols-2 gap-4 mt-2">

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30">
<div class="text-blue-400 font-bold text-sm mb-1">FLAT FILE</div>

```text {*}{class:'!text-xs'}
payment/
├── ChargePayment.php
├── ConfirmPayment.php
├── PaymentGateway.php
├── PaymentTransaction.php
├── StripeGateway.php
└── PaymentServiceProvider.php
```

</div>

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30">
<div class="text-green-400 font-bold text-sm mb-1">LARAVEL PADRÃO</div>

```text {*}{class:'!text-xs'}
payment/
├── Jobs/
│   ├── ChargePaymentJob.php
│   └── ConfirmPaymentJob.php
├── Models/
│   └── PaymentTransaction.php
├── Services/
│   └── PaymentGatewayService.php
└── Providers/
    └── PaymentServiceProvider.php
```

</div>

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30">
<div class="text-purple-400 font-bold text-sm mb-1">CLEAN ARCHITECTURE</div>

```text {*}{class:'!text-xs'}
payment/
├── Domain/
│   ├── PaymentGateway.php
│   └── PaymentTransaction.php
├── Application/
│   ├── ChargePayment.php
│   └── ConfirmPayment.php
└── Infrastructure/
    └── StripeGateway.php
```

</div>

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30">
<div class="text-orange-400 font-bold text-sm mb-1">DDD-LIKE</div>

```text {*}{class:'!text-xs'}
payment/
├── Domain/
│   ├── PaymentTransaction.php
│   └── PaymentGateway.php
├── Application/
│   ├── Commands/
│   │   └── ChargePayment.php
│   └── Listeners/
│       └── StartPaymentProcess.php
└── Infrastructure/
    └── StripePaymentGateway.php
```

</div>

</div>

<!--
"4 estruturas completamente diferentes. Mas olha: o boundary é o MESMO. O evento é o MESMO. A dependência unidirecional é a MESMA. A estrutura de pastas é cosmética — ela não muda o que o módulo FAZ nem como ele se conecta ao resto do sistema."
-->

---
layout: impact
color: green
---

# 4 estruturas

O mesmo boundary. O mesmo evento. A mesma dependência.

<v-click>

<div class="mt-8 p-6 bg-yellow-900/40 rounded-lg border-2 border-yellow-500/50">
<div class="text-2xl font-bold text-yellow-400">
Não existe padrão certo.<br>
Existe o que encaixa pro seu time.
</div>
</div>

</v-click>

<v-click>

<div class="mt-6 text-lg opacity-70">
O que importa é o <span class="text-green-400 font-bold">boundary</span>, não a <span class="text-gray-400">pasta</span>.
</div>

</v-click>

<!--
"Não existe padrão certo. Flat file funciona. Laravel padrão funciona. Clean Architecture funciona. DDD funciona. O que importa é que payment é um módulo isolado que escuta OrderPlaced e dispara PaymentConfirmed. COMO você organiza dentro dele é decisão do SEU time."

"Agora que a gente entendeu O QUÊ extrair e POR QUÊ... deixa eu mostrar COMO eu fiz isso na prática."
-->
