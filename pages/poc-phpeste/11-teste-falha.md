---
layout: ph-deletion
transition: none
meta: legadão · pagamento
clicks: 4
questions:
  - text: Listar todos os arquivos de pagamento?
    show: 1
    at: 2
    status: fail
    detail: Espalhados em 8 pastas.
  - text: Quanto do sistema quebra?
    show: 2
    at: 3
    status: fail
    detail: 3 classes de outros domínios.
  - text: Algum arquivo é usado por outra feature?
    show: 3
    at: 4
    status: fail
    detail: Pedidos, checkout, reembolso e antifraude.
result: { at: 4, status: fail, label: FALHOU, score: 0 de 3 }
---

# Teste da Deleção · <em>no legadão</em>

::visual::

<div class="ph-step" v-click.hide="1">
  <p class="ph-step__title">A feature que eu vou tentar deletar: <strong>pagamento</strong>.</p>
</div>

<div class="ph-step" v-click="[1, 2]">
  <p class="ph-step__title">Onde estão os arquivos de “pagamento”?</p>
<pre class="ph-files ph-files--cols"><span class="is-ctx">app/Actions/</span><span class="is-hit">└── ProcessPaymentAction.php</span><span class="is-ctx">app/Jobs/</span><span class="is-hit">└── ChargePaymentJob.php</span><span class="is-ctx">app/Services/</span><span class="is-hit">└── PaymentGatewayService.php</span><span class="is-ctx">app/Models/</span><span class="is-hit">├── Payment.php</span><span class="is-hit">└── PaymentTransaction.php</span><span class="is-ctx">app/Http/Controllers/</span><span class="is-hit">└── PaymentWebhookController.php</span><span class="is-ctx">app/Notifications/</span><span class="is-hit">└── PaymentFailedNotification.php</span><span class="is-ctx">app/Enums/</span><span class="is-hit">└── PaymentStatus.php</span><span class="is-ctx">app/Observers/</span><span class="is-hit">└── PaymentObserver.php</span></pre>
  <p class="ph-callout ph-callout--fail"><strong>9 arquivos em 8 pastas.</strong> Você confia que pegou tudo?</p>
</div>

<div class="ph-step" v-click="[2, 3]">
  <p class="ph-step__title">Deletei “pagamento”. O que quebra?</p>
  <div class="ph-deps">
    <div class="ph-dep"><code>CreateOrderAction</code><span class="ph-dep__verb">importa</span><code class="is-broken">ProcessPaymentAction</code><span class="ph-dep__tag">pedidos</span></div>
    <div class="ph-dep"><code>CheckoutController</code><span class="ph-dep__verb">importa</span><code class="is-broken">ChargePaymentJob</code><span class="ph-dep__tag">checkout</span></div>
    <div class="ph-dep"><code>OrderService</code><span class="ph-dep__verb">importa</span><code class="is-broken">PaymentGatewayService</code><span class="ph-dep__tag">pedidos</span></div>
  </div>
  <p class="ph-callout ph-callout--fail"><strong>3 classes de outros domínios</strong> quebram na hora. Pedidos e checkout dependem de pagamento via import.</p>
</div>

<div class="ph-step" v-click="[3, 4]">
  <p class="ph-step__title">Arquivos de “pagamento” usados por outras features:</p>
  <div class="ph-deps">
    <div class="ph-dep"><code>ProcessPaymentAction</code><span class="ph-dep__verb">← usado por</span><code>CreateOrderAction</code><span class="ph-dep__tag">pedidos</span></div>
    <div class="ph-dep"><code>ProcessPaymentAction</code><span class="ph-dep__verb">← usado por</span><code>ProcessCheckoutAction</code><span class="ph-dep__tag">checkout</span></div>
    <div class="ph-dep"><code>PaymentGatewayService</code><span class="ph-dep__verb">← usado por</span><code>RefundService</code><span class="ph-dep__tag">reembolso</span></div>
    <div class="ph-dep"><code>PaymentGatewayService</code><span class="ph-dep__verb">← usado por</span><code>FraudDetectionService</code><span class="ph-dep__tag">antifraude</span></div>
  </div>
  <p class="ph-callout ph-callout--fail">Acoplamento direto. <strong>Nenhum arquivo é exclusivo de “pagamento”.</strong></p>
</div>

<div class="ph-step" v-click="4">
  <p class="ph-score">0 / 3</p>
  <p class="ph-step__title" style="text-align:center">O legadão não passa no Teste da Deleção.</p>
</div>

<!--
[sem click — slide aparece com título e layout vazio]
"Vamos rodar o Teste da Deleção no nosso legadão. A funcionalidade que vou tentar deletar: pagamento."

[click 1 — Pergunta 1 + file tree]
"Primeira pergunta: consigo listar todos os arquivos de pagamento? Olha só... ProcessPaymentAction tá em Actions. ChargePaymentJob tá em Jobs. PaymentGatewayService tá em Services. Payment e PaymentTransaction tão em Models. Webhook controller em Http. Notification em Notifications. Enum em Enums. Observer em Observers. São 9 arquivos espalhados em 8 pastas diferentes. Você confia que pegou tudo? Eu não confio."

[click 2 — ✘ P1 + Pergunta 2 + grafo de imports]
"Falhou. Segunda pergunta: se eu deletar esses 9 arquivos, quanto quebra? CreateOrderAction importa ProcessPaymentAction diretamente. CheckoutController importa ChargePaymentJob. OrderService importa PaymentGatewayService. Três classes de outros domínios quebram na hora. Pedidos e Checkout dependem diretamente de Pagamento."

[click 3 — ✘ P2 + Pergunta 3 + uso compartilhado]
"Falhou também. Terceira pergunta: algum desses arquivos é usado por outra feature? ProcessPaymentAction é chamada por CreateOrderAction, de pedidos, e por ProcessCheckoutAction, do checkout. PaymentGatewayService é chamada pelo RefundService, de reembolso, e pelo FraudDetectionService, do antifraude. Tudo acoplado."

[click 4 — ✘ P3 + FALHOU]
"Falhou as três. O legadão não passa no Teste da Deleção. E agora? Como a gente resolve isso?"
-->
