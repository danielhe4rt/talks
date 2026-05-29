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
layout: brutalist-base
metaNumber: "15.1"
metaSection: "EXTRAÇÃO"
metaSubtitle: "events vs imports"
metaPhase: refactor
metaRight: "Q2 · QUEM ESCUTA?"
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

<div class="grid grid-cols-[1fr_auto_1fr] gap-6 mt-3 items-center">

<div>

<div class="text-[10px] text-blue-400 font-bold uppercase tracking-wider mb-1.5">Checkout dispara</div>

```php {*}{class:'!text-[0.7rem] !leading-snug'}
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

<div class="text-[10px] text-green-400 font-bold uppercase tracking-wider mb-1.5">Payment escuta</div>

```php {*}{class:'!text-[0.7rem] !leading-snug'}
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

<div class="mt-3 p-2.5 bg-green-900/20 rounded-lg border border-green-500/20 text-center">
  <div class="text-xs">Checkout não importa Payment. Payment não importa Checkout.</div>
  <div class="text-sm font-bold text-green-400 mt-0.5">Zero imports cruzados.</div>
</div>

</v-click>

<!--
"Checkout cria o evento OrderPlaced. Só isso. Quem escuta?"

[click] "Payment. O Listener HandleOrderPlaced recebe o evento e chama ProcessPayment internamente. Olha: o import de ProcessPayment agora é INTERNO do módulo Payment. Checkout não sabe que essa classe existe."

[click] "Checkout não importa Payment. Payment não importa Checkout. Os dois módulos não se conhecem. O evento é o contrato entre eles. Zero imports cruzados."
-->
