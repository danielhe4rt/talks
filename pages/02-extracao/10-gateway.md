---
layout: split-modular
transition: none
metaNumber: "18"
metaSection: "EXTRAÇÃO"
metaSubtitle: "extraindo o leak"
metaPhase: refactor
metaRight: "Q3 · GATEWAY"
beforeLabel: ANTES
afterLabel: DEPOIS
---

# Extrai o que é <span class="text-green-400">de todos</span>.

::before::

<div class="text-[10px] text-red-400 font-bold uppercase tracking-wider mb-2">leak dentro de Payment</div>

```text {*}{class:'!text-xs'}
app/Modules/
├── Payment/
│   ├── ProcessPayment.php
│   ├── PaymentGatewayService.php  ← leak
│   └── ...
├── Subscriptions/
│   └── RecurringChargeJob.php   ─┐
├── Checkout/                     │ todos
│   └── PlaceOrder.php            │ chamam
└── Admin/                        │ direto
    └── RefundController.php     ─┘
```

<div class="mt-3 p-2 bg-red-900/20 rounded text-xs text-red-300">
Mora em Payment, mas 3 features importam direto.<br>
Mudou Payment → quebra Subscriptions <i>e</i> Admin.
</div>

::after::

<div class="text-[10px] text-green-400 font-bold uppercase tracking-wider mb-2">gateway vira módulo</div>

```text {*}{class:'!text-xs'}
app/Modules/
├── Gateway/                     ← novo
│   ├── GatewayContract.php
│   └── StripeGateway.php
├── Payment/
│   └── ProcessPayment.php       ─┐
├── Subscriptions/                │ todos
│   └── RecurringChargeJob.php    │ usam
└── Admin/                        │ Gateway
    └── RefundController.php     ─┘
```

<div class="mt-3 p-2 bg-green-900/20 rounded text-xs text-green-300">
Gateway é o contrato. Payment, Subscriptions e Admin<br>
dependem dele — não um do outro.
</div>

<v-click>

<div class="mt-3 p-2.5 bg-bone/5 rounded border-l-4 border-green-500 text-sm">
Se <b class="text-green-400">3 módulos usam</b>, não pertence a 1 — <b>vira módulo</b>.
</div>

</v-click>

<!--
"O leak não é um problema de pasta. É um problema de pertencimento. PaymentGatewayService morava em Payment, mas Payment não era dono — só era um dos consumidores."

"A regra é simples: se 3 módulos usam o arquivo, ele não pertence a nenhum dos 3. Vira um módulo novo. Gateway."

"Olha o depois: Gateway vira um módulo de verdade. GatewayContract é a interface. StripeGateway é a implementação. Payment, Subscriptions e Admin todos passam a depender de Gateway — não um do outro. Os 3 ficam acoplados ao MESMO contrato, não a si mesmos."

[click — regra]
"Se 3 módulos usam, não pertence a 1, vira módulo. Anota essa."
-->
