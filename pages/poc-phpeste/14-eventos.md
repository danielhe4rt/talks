---
layout: ph-section
tone: espresso
eyebrow: conceito antes do código
transition: fade
clicks: 2
---

# Import ou evento?

Apaga o Payment e vê **quem cai junto**.

::content::

<PhCouplingLanes />

<!--
"Antes do código, o CONCEITO. Dois jeitos de um módulo falar com outro."

"Em cima: IMPORT. Checkout faz `use App\Modules\Payment` e chama direto. Olha o fio entre os dois — é uma dependência. Checkout CONHECE Payment."

"Embaixo: EVENTO. Checkout não importa Payment. Ele dispara `OrderPlaced` — olha as ondas, é um aviso pro ar. Payment escuta, mas Checkout nem sabe disso. Não precisa saber."

[click — Payment some dos dois lados]

"Apaguei Payment nas duas linhas. Em cima: o fio arrebentou. Checkout caiu junto — Class not found. Apagou um módulo, o outro foi junto."

"Embaixo: Payment sumiu e Checkout segue funcionando. O evento continua disparando — pro vazio. Ninguém escuta, e tá tudo bem."

[click — veredito]

"Import é um fio: corta um lado, o outro cai. Evento é um aviso: quem quiser, escuta. Não é estilo de código — é se o seu boundary sobrevive ao Teste da Deleção. Bora ver no código."
-->

---
layout: ph-split
beforeLabel: acoplado
afterLabel: desacoplado
---

# E se Checkout só <em>avisasse</em>?

::before::

<p class="ph-file-label">Checkout/PlaceOrder.php</p>

```php {2,8-9}
<?php
use App\Modules\Payment\ProcessPayment;

class PlaceOrder
{
    public function execute(Order $order)
    {
        $order->save();
        (new ProcessPayment)->execute($order);
    }
}
```

<p class="ph-callout ph-callout--fail">Checkout <strong>importa</strong> Payment. Deletou Payment → Checkout quebra.</p>

::after::

<p class="ph-file-label">Checkout/PlaceOrder.php</p>

```php {2,8-9}
<?php
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

<p class="ph-callout ph-callout--ok">Checkout <strong>avisa</strong> que o pedido foi criado. Não sabe — e não precisa saber — quem escuta.</p>

<!--
"Olha o código acoplado: PlaceOrder importa ProcessPayment diretamente. Se Payment não existe, Checkout explode."

"E se ao invés de CHAMAR Payment, Checkout só AVISASSE que o pedido foi criado? Dispatch de um evento. OrderPlaced. Pronto. Checkout não importa NADA de Payment. Zero dependência."
-->

---
layout: ph-split
beforeLabel: checkout dispara
afterLabel: payment escuta
beforeKind: info
---

# <em>Quem</em> escuta?

Zero imports cruzados.

::before::

<p class="ph-file-label">Checkout/Events/OrderPlaced.php</p>

```php
<?php
namespace App\Modules\Checkout\Events;

class OrderPlaced
{
    public function __construct(
        public Order $order,
    ) {}
}
```

<p class="ph-callout">O evento <strong>pertence ao Checkout</strong>. Ele só cria e dispara.</p>

::after::

<p class="ph-file-label">Payment/Listeners/HandleOrderPlaced.php</p>

```php {6-10}
<?php
use App\Modules\Checkout\Events\OrderPlaced;

class HandleOrderPlaced
{
    public function handle(OrderPlaced $event)
    {
        (new ProcessPayment)
            ->execute($event->order);
    }
}
```

<p class="ph-callout ph-callout--ok">Payment escuta e chama <code>ProcessPayment</code> <strong>por dentro</strong>. Se Payment sumir, o evento dispara pro vazio.</p>

<!--
"Checkout cria o evento OrderPlaced. Só isso. Não sabe quem escuta."

"Do outro lado, Payment escuta: o Listener HandleOrderPlaced recebe o evento e chama ProcessPayment internamente. O import de ProcessPayment agora é INTERNO do módulo Payment."

"Checkout não importa Payment. Payment não importa Checkout. Os dois módulos não se conhecem. O evento é o contrato entre eles. Zero imports cruzados."
-->
