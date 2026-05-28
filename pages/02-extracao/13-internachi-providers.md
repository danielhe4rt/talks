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

<div class="text-[10px] text-red-400 font-bold uppercase tracking-wider mb-2">bootstrap/providers.php</div>

```php {*}{class:'!text-xs'}
<?php

return [
    App\Providers\AppServiceProvider::class,
    App\Providers\RouteServiceProvider::class,

    App\Modules\Cart\CartServiceProvider::class,
    App\Modules\Catalog\CatalogServiceProvider::class,
    App\Modules\Checkout\CheckoutServiceProvider::class,
    App\Modules\Payment\PaymentServiceProvider::class,
    App\Modules\Shipping\ShippingServiceProvider::class,
    App\Modules\Subscriptions\SubscriptionsServiceProvider::class,
    App\Modules\Admin\AdminServiceProvider::class,
    App\Modules\Gateway\GatewayServiceProvider::class,
    // ... mais 1 linha pra CADA módulo novo
];
```

<div class="mt-3 p-2 bg-red-900/20 rounded text-xs text-red-300">
Cada módulo novo = <b>1 linha aqui</b>.<br>
Deletou pasta sem tirar daqui → app quebra.
</div>

::after::

<div class="text-[10px] text-green-400 font-bold uppercase tracking-wider mb-2">bootstrap/providers.php</div>

```php {*}{class:'!text-xs'}
<?php

return [
    App\Providers\AppServiceProvider::class,
    App\Providers\RouteServiceProvider::class,
];
```

<div class="mt-3 p-2 bg-green-900/20 rounded text-xs text-green-300">
<b>Auto-discovery cuida do resto.</b><br>
internachi varre <code>app/Modules/</code> sozinho.
</div>

<!--
"O internachi/modular resolve isso. Ele varre app/Modules/ no boot, encontra os ServiceProviders, registra automaticamente. Você nunca mais precisa tocar no providers.php pra adicionar ou tirar módulo."

"Olha o antes: cada módulo precisava de uma linha aqui. Esquece de tirar a linha quando deleta a pasta? App quebra na hora."

"Depois: providers.php tem só o que é do app core. Auto-discovery cuida do resto. Apagou a pasta? Some do bootstrap junto. O framework não fica apontando pro nada."
-->
