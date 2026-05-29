---
layout: split-modular
metaNumber: "15"
metaSection: "EXTRAÇÃO"
metaSubtitle: "events vs imports"
metaPhase: refactor
metaRight: "Q2 · BEFORE/AFTER"
beforeLabel: ACOPLADO
afterLabel: DESACOPLADO
---

# E se Checkout só <span class="text-green-400">avisasse</span> ao invés de <span class="text-red-400">chamar</span>?

::before::

```php {*}{class:'!text-xs'}
// Checkout/PlaceOrder.php

use App\Modules\Payment\ProcessPayment;

class PlaceOrder
{
    public function execute(Order $order)
    {
        $order->save();

        (new ProcessPayment)
            ->execute($order);
    }
}
```

<div class="mt-3 p-2 bg-red-900/20 rounded text-xs text-red-300">
Checkout <b>importa</b> Payment.<br>
Deletou Payment → Checkout quebra.
</div>

::after::

```php {*}{class:'!text-xs'}
// Checkout/PlaceOrder.php

use App\Modules\Checkout\Events\OrderPlaced;

class PlaceOrder
{
    public function execute(Order $order)
    {
        $order->save();

        OrderPlaced::dispatch($order);
    }
}
```

<div class="mt-3 p-2 bg-green-900/20 rounded text-xs text-green-300">
Checkout <b>avisa</b> que o pedido foi criado.<br>
Não sabe e não precisa saber quem escuta.
</div>

<!--
"Olha o código acoplado: PlaceOrder importa ProcessPayment diretamente. Se Payment não existe, Checkout explode."

"E se ao invés de CHAMAR Payment, Checkout só AVISASSE que o pedido foi criado? Dispatch de um evento. OrderPlaced. Pronto. Checkout não importa NADA de Payment. Zero dependência."
-->

---
layout: split-modular
metaNumber: "15.1"
metaSection: "EXTRAÇÃO"
metaSubtitle: "events vs imports"
metaPhase: refactor
metaRight: "Q2 · QUEM ESCUTA?"
beforeLabel: CHECKOUT DISPARA
afterLabel: PAYMENT ESCUTA
beforeColor: blue
---

# QUEM <span class="text-green-400">escuta</span>?

Checkout não importa Payment. Payment não importa Checkout — **zero imports cruzados.**

::before::

```php {*}{class:'!text-xs'}
// Checkout/Events/OrderPlaced.php

class OrderPlaced
{
    public function __construct(
        public Order $order,
    ) {}
}
```

<div class="mt-3 p-2 bg-blue-900/20 rounded text-xs text-blue-300">
Checkout só cria o evento.<br>
Não sabe quem escuta.
</div>

::after::

```php {*}{class:'!text-xs'}
// Payment/Listeners/HandleOrderPlaced.php

class HandleOrderPlaced
{
    public function handle(OrderPlaced $event)
    {
        (new ProcessPayment)
            ->execute($event->order);
    }
}
```

<div class="mt-3 p-2 bg-green-900/20 rounded text-xs text-green-300">
Payment escuta e chama<br>
ProcessPayment internamente.
</div>

<!--
"Checkout cria o evento OrderPlaced. Só isso. Não sabe quem escuta."

"Do outro lado, Payment escuta: o Listener HandleOrderPlaced recebe o evento e chama ProcessPayment internamente. O import de ProcessPayment agora é INTERNO do módulo Payment."

"Checkout não importa Payment. Payment não importa Checkout. Os dois módulos não se conhecem. O evento é o contrato entre eles. Zero imports cruzados."
-->
