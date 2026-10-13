---
layout: ph-section
tone: espresso
eyebrow: conceito antes do código
transition: fade
---

# Import ou evento?

Dois jeitos de um módulo falar com outro. **Um sobrevive** ao Teste da Deleção.

::content::

<PhEventCompare />

<!--
"Antes de eu mostrar o código, deixa eu te mostrar o CONCEITO visualmente."

[apresenta sem clicar — deixa a animação rodar]

"Esquerda: ACOPLADO. IMPORT. Checkout faz `use App\\Modules\\Payment` e chama direto. Olha o fio entre os dois — sólido, brilhante. É uma dependência."

"Direita: DESACOPLADO. EVENTO. Checkout não importa Payment. Checkout dispara `OrderPlaced::dispatch()` — olha as ondas, é um broadcast pro nada. Payment está ouvindo, mas Checkout não sabe disso. Não precisa saber."

[clica em DELETAR PAYMENT — os dois lados reagem simultaneamente]

"Apaguei Payment dos dois lados. Olha o que aconteceu."

"Esquerda: o fio quebrou. Checkout explodiu — fatal error. O import virou linha tracejada vermelha. Você apagou um módulo e o outro caiu junto."

"Direita: Payment sumiu tranquilo. O evento ainda dispara — Checkout não sabe que ninguém tá escutando, e não precisa saber. Sistema intacto."

"Isso é a diferença entre import e evento. Não é só estilo de código — é se o seu boundary sobrevive ao Teste da Deleção. Vamos ver como fica isso no código real."
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
