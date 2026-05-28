---
layout: split-modular
metaNumber: "15"
metaSection: "EXTRAÇÃO"
metaSubtitle: "events vs imports"
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
layout: brutalist-base
metaNumber: "15.1"
metaSection: "EXTRAÇÃO"
metaSubtitle: "events vs imports"
metaRight: "quem escuta?"
contentAlign: "top"
---

<TitleBlock
  eyebrow="o contrato entre módulos"
  outlined="QUEM"
  solid="ESCUTA"
  accent="?"
  tail="dispatch → listener"
  size="small"
/>

<div class="grid grid-cols-[1fr_auto_1fr] gap-6 mt-6 items-center">

<div>

<div class="text-xs text-blue-400 font-bold uppercase tracking-wider mb-2">Checkout dispara</div>

```php {*}{class:'!text-xs'}
// Checkout/Events/OrderPlaced.php

class OrderPlaced
{
    public function __construct(
        public Order $order,
    ) {}
}
```

</div>

<div class="text-2xl opacity-30">→</div>

<div>

<v-click>

<div class="text-xs text-green-400 font-bold uppercase tracking-wider mb-2">Payment escuta</div>

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

</v-click>

</div>

</div>

<v-click>

<div class="mt-6 p-4 bg-green-900/20 rounded-lg border border-green-500/20 text-center">
  <div class="text-sm">Checkout não importa Payment. Payment não importa Checkout.</div>
  <div class="text-base font-bold text-green-400 mt-1">Zero imports cruzados.</div>
</div>

</v-click>

<!--
"Checkout cria o evento OrderPlaced. Só isso. Quem escuta?"

[click] "Payment. O Listener HandleOrderPlaced recebe o evento e chama ProcessPayment internamente. Olha: o import de ProcessPayment agora é INTERNO do módulo Payment. Checkout não sabe que essa classe existe."

[click] "Checkout não importa Payment. Payment não importa Checkout. Os dois módulos não se conhecem. O evento é o contrato entre eles. Zero imports cruzados."
-->
