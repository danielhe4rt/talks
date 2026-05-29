---
layout: split-modular
transition: none
metaNumber: "23"
metaSection: "EXTRAÇÃO"
metaSubtitle: "internachi/modular"
metaPhase: refactor
metaRight: "Q4 · ESTRUTURA"
beforeLabel: ESPALHADO
afterLabel: ENCAPSULADO
---

# O módulo é uma <span class="text-green-400">mini-app</span>.

::before::

<div class="text-[10px] text-red-400 font-bold uppercase tracking-wider mb-1.5">laravel padrão</div>

```text {*}{class:'!text-[0.7rem] !leading-snug'}
app/Modules/Payment/
├── Services/
└── Models/

resources/views/
└── payment/             ← view do módulo
    └── checkout.blade.php

config/
└── payment.php          ← config do módulo

database/migrations/
└── 2024_01_payment.php  ← migration

routes/
└── payment.php          ← rotas
```

<div class="mt-2 p-2 bg-red-900/20 rounded text-[11px] text-red-300">
Pasta do módulo é só pedaço.<br>
View, config, migration, rota estão <b>fora</b>.
</div>

::after::

<div class="text-[10px] text-green-400 font-bold uppercase tracking-wider mb-1.5">internachi</div>

```text {*}{class:'!text-[0.68rem] !leading-snug'}
app-modules/payment/
├── composer.json            ← pacote Composer
├── src/
│   ├── Services/
│   ├── Models/
│   └── PaymentServiceProvider.php
├── resources/
│   └── views/
│       └── checkout.blade.php
├── config/
│   └── payment.php
├── database/
│   └── migrations/
│       └── 2024_01_payment.php
└── routes/
    └── web.php
```

<div class="mt-2 p-2 bg-green-900/20 rounded text-[11px] text-green-300">
<b>Apaga a pasta. Apaga TUDO de payment.</b><br>
View, config, migration, rota — tudo junto.
</div>

<!--
"Mas tem outra coisa que o internachi faz, que vai mais fundo: ele muda O QUE É o módulo. No Laravel padrão, a pasta do módulo só tem Services e Models. Mas a view fica em resources/views, a config fica em config/, a migration fica em database/migrations, a rota fica em routes/. Espalhado de novo."

"Você 'extraiu' o módulo, mas só extraiu o código PHP. O resto da feature continua espalhado pelo projeto."

"No internachi, o módulo vira uma mini-app dentro de app-modules/payment/. Tudo que pertence a Payment mora ali: o composer.json no topo, src/, resources/, config/, database/, routes/. O ServiceProvider do próprio módulo registra cada coisa no Laravel via package discovery."

"Aí sim: apaga a pasta, apaga TUDO de payment. View, config, migration, rota — tudo junto. O boundary fica de verdade."
-->
