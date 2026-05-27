---
layout: statement
---

# Fiz a extração e... deu merda.

3 erros reais. 3 lições aprendidas.

<!--
"Até agora parece lindo. Mas vou ser honesto com vocês: eu errei. E errei feio. Vamos falar dos erros."
-->

---

# Erro 1: Dependência circular surpresa

<div class="text-sm mb-4">

O modelo `PaymentTransaction` — quem é o dono?

</div>

```mermaid {scale: 0.8}
flowchart LR
    A["sales\n(Order\n.transactions())"] -->|"importa\nPaymentTransaction"| B["payment\n(gera transações)"]
    B -->|"importa\nOrder"| A
    style A fill:#991b1b,stroke:#ef4444,color:#fff
    style B fill:#991b1b,stroke:#ef4444,color:#fff
```

<v-click>

<div class="mt-4 p-3 bg-red-900/30 rounded-lg border border-red-500/30 text-sm">
<span class="text-red-400 font-bold">Meu erro:</span> achei que <code>PaymentTransaction</code> pertencia ao módulo <code>payment</code>, porque é o payment que cria transações. Mas <code>Order</code> — que mora em <code>sales</code> — tem um <code>->transactions()</code> relationship.
</div>

</v-click>

<!--
"Primeiro erro: achei que PaymentTransaction pertencia ao payment, porque é o módulo que cria transações. Mas Order — que mora em sales — tem um ->transactions() relationship. Resultado: sales importa payment, payment importa sales. Circular de novo."
-->

---

# Solução: quem é o dono dos dados?

<div class="p-4 bg-yellow-900/40 rounded-lg border-2 border-yellow-500/50 text-center text-xl font-bold mb-6">
O modelo fica com quem <span class="text-yellow-400">ARMAZENA</span>,<br> não com quem <span class="text-yellow-400">PRODUZ</span>.
</div>

<v-clicks>

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30 text-sm mb-3">
<span class="opacity-60">PaymentTransaction é um registro de dados do pedido.</span><br>
Payment <span class="text-blue-400">PRODUZ</span> transações. Sales <span class="text-green-400">ARMAZENA</span> transações.
</div>

<div class="p-3 bg-green-900/30 rounded-lg border border-green-500/30 text-sm mb-3">
→ <code>PaymentTransaction</code> mora em <code>sales</code>.<br>
→ <code>payment</code> usa o modelo como dependência.
</div>

<div class="flex justify-center gap-4 text-sm">
  <span class="text-green-400">✓ Unidirecional mantido</span>
  <span class="opacity-60">payment → sales</span>
  <span class="opacity-60">sales → ninguém</span>
</div>

</v-clicks>

<!--
"A regra que salva: o modelo fica com quem ARMAZENA, não com quem PRODUZ. PaymentTransaction é um dado do pedido — assim como Order, OrderItem, tudo que é persistência. O payment produz a transação, mas quem guarda é sales. Movi o modelo pra sales, e a dependência circular sumiu."
-->

---

# Erro 2: Listeners duplicados

<div class="text-sm mb-4">

**Bug:** Cliente cobrado em DOBRO

</div>

```text
1. PlaceOrder dispatches ChargePaymentJob              ← código antigo
2. StartPaymentProcess dispatches ChargePaymentJob     ← código novo

Pedido chega → ChargePaymentJob × 2 → 💳 COBROU DUAS VEZES 🐛
```

<v-click>

<div class="mt-4 text-sm mb-2 font-bold">Solução: abordagem ADITIVA-DEPOIS-DESTRUTIVA</div>

<v-clicks>

<div class="flex flex-col gap-2 text-sm">
  <div class="p-2 bg-green-900/30 rounded border border-green-500/30 flex items-center gap-2">
    <span class="text-green-400 font-mono font-bold">#1</span> Adiciona novo listener (coexiste com o antigo) <span class="ml-auto opacity-60">← seguro</span>
  </div>
  <div class="p-2 bg-green-900/30 rounded border border-green-500/30 flex items-center gap-2">
    <span class="text-green-400 font-mono font-bold">#2</span> Extrai o módulo, remove dispatch antigo <span class="ml-auto opacity-60">← seguro</span>
  </div>
  <div class="p-2 bg-green-900/30 rounded border border-green-500/30 flex items-center gap-2">
    <span class="text-green-400 font-mono font-bold">#3</span> Move código adjacente <span class="ml-auto opacity-60">← seguro</span>
  </div>
  <div class="p-2 bg-green-900/30 rounded border border-green-500/30 flex items-center gap-2">
    <span class="text-green-400 font-mono font-bold">#4</span> Limpa código morto do módulo original <span class="ml-auto opacity-60">← seguro</span>
  </div>
</div>

</v-clicks>

</v-click>

<!--
"Segundo erro — ou quase-erro. Durante a extração, por um momento tínhamos dois caminhos cobrando o cliente. O código antigo ainda fazia ChargePaymentJob E o listener novo também. Duas cobranças pra mesma compra. Imagina receber duas cobranças de 500 reais no cartão."

"A solução foi sequenciar a extração em 4 steps independentes. Primeiro adiciona o novo caminho sem remover o antigo. O sistema tolera o duplicado graças a um idempotency guard no gateway. Depois remove o caminho antigo. Cada step é deployável e reversível."
-->

---

# Erro 3: Feature flags com prefixo errado

<div class="grid grid-cols-2 gap-6 mt-4">
<div>

```text
Feature flags do pagamento:

  ShopFreeShipping
    ← prefixo "Shop" mas agora
      mora em fulfillment

  ShopInstallmentPayment
    ← prefixo "Shop" mas agora
      mora em payment
```

</div>
<div>

<v-click>

<div class="text-sm">

**Renomear?**

<v-clicks>

<div class="mt-2 p-2 bg-red-900/30 rounded border border-red-500/30">
Pennant grava o nome da flag <span class="text-red-400 font-bold">no banco</span>
</div>

<div class="mt-2 p-2 bg-red-900/30 rounded border border-red-500/30">
Precisa de data migration pra <span class="text-red-400 font-bold">todos os tenants</span>
</div>

<div class="mt-2 p-2 bg-red-900/30 rounded border border-red-500/30">
Risco: flag ligada vira <span class="text-red-400 font-bold">desligada</span> durante deploy
</div>

<div class="mt-3 p-3 bg-yellow-900/40 rounded-lg border-2 border-yellow-500/50 font-bold text-center">
Decisão: manter o prefixo "Shop"<br>
<span class="text-sm font-normal opacity-70">Inconsistência estética &lt; risco de produção</span>
</div>

</v-clicks>

</div>

</v-click>

</div>
</div>

<!--
"Terceiro: feature flags. As flags se chamavam ShopFreeShipping, ShopInstallmentPayment. Com a extração, elas agora pertencem ao fulfillment e payment. Renomear seria mais 'limpo', mas o Pennant salva o nome da flag no banco. Renomear = migration de dados pra todos os tenants. Decisão pragmática: mantém o prefixo errado. Inconsistência estética é barato. Deploy quebrado é caro."
-->
