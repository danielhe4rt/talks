---
layout: split-modular
transition: none
metaNumber: "21"
metaSection: "EXTRAÇÃO"
metaSubtitle: "auto-discovery"
metaPhase: refactor
metaRight: "Q4 · PROVIDERS"
beforeLabel: ANTES
afterLabel: DEPOIS
---

# `internachi/modular` <span>— sem mais providers.php</span>

::before::

<div class="text-[10px] text-red-400 font-bold uppercase tracking-wider mb-1.5">bootstrap/providers.php</div>

```php {*}{class:'!text-[0.7rem] !leading-snug'}
<?php

return [
    App\Providers\AppServiceProvider::class,
    App\Providers\RouteServiceProvider::class,

    App\Modules\Cart\CartServiceProvider::class,
    App\Modules\Catalog\CatalogServiceProvider::class,
    App\Modules\Checkout\CheckoutServiceProvider::class,
    App\Modules\Payment\PaymentServiceProvider::class,
    App\Modules\Shipping\ShippingServiceProvider::class,
    App\Modules\Admin\AdminServiceProvider::class,
    App\Modules\Gateway\GatewayServiceProvider::class,
    // ... 1 linha pra CADA módulo novo
];
```

<div class="mt-2 p-2 bg-red-900/20 rounded text-[11px] text-red-300">
Cada módulo novo = <b>1 linha aqui</b>.<br>
Deletou pasta sem tirar daqui → app quebra.
</div>

::after::

<div class="text-[10px] text-green-400 font-bold uppercase tracking-wider mb-1.5">bootstrap/providers.php</div>

```php {*}{class:'!text-[0.7rem] !leading-snug'}
<?php

return [
    App\Providers\AppServiceProvider::class,
    App\Providers\RouteServiceProvider::class,
];
```

<div class="mt-2 p-2 bg-green-900/20 rounded text-[11px] text-green-300">
Cada módulo declara seu provider no <b>próprio composer.json</b>.<br>
Laravel <b>auto-descobre</b>. Você nunca mais toca aqui.
</div>

<!--
"O internachi/modular muda a régua: cada módulo vira um pacote Composer com seu próprio composer.json. Quem registra o ServiceProvider é o package discovery do Laravel — não o seu bootstrap/providers.php."

"Antes: cada módulo precisava de uma linha aqui. Esquece de tirar a linha quando deleta a pasta? App quebra na hora."

"Depois: providers.php tem só o que é do app core. Quem cuida dos módulos é o Composer + package discovery. Apagou a pasta? Some do bootstrap junto. Sem provider órfão."

[transição] "Mas como é que isso funciona por baixo? Vou te mostrar."
-->
