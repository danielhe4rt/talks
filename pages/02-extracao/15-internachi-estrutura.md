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

<StructTree
  root="projeto/"
  accent="red"
  fs="0.76rem"
  :tree="[
    { name: 'app/Modules/Payment/', kind: 'dir', children: [
      { name: 'Services/', kind: 'support' },
      { name: 'Models/', kind: 'support' },
    ] },
    { name: 'resources/views/payment/checkout.blade.php', kind: 'domain', note: '← view', noteKind: 'danger' },
    { name: 'config/payment.php', kind: 'domain', note: '← config', noteKind: 'danger' },
    { name: 'database/migrations/2024_01_payment.php', kind: 'domain', note: '← migration', noteKind: 'danger' },
    { name: 'routes/payment.php', kind: 'domain', note: '← rotas', noteKind: 'danger' },
  ]"
/>

<div class="mt-2 p-2 bg-red-900/20 rounded text-[11px] text-red-300">
Pasta do módulo é só pedaço.<br>
View, config, migration, rota estão <b>fora</b>.
</div>

::after::

<div class="text-[10px] text-green-400 font-bold uppercase tracking-wider mb-1.5">internachi</div>

<StructTree
  root="app-modules/payment/"
  accent="green"
  fs="0.7rem"
  :tree="[
    { name: 'composer.json', kind: 'domain', note: '← pacote Composer', noteKind: 'ok' },
    { name: 'src/', kind: 'dir', children: [
      { name: 'Services/', kind: 'dir' },
      { name: 'Models/', kind: 'dir' },
      { name: 'PaymentServiceProvider.php', kind: 'support' },
    ] },
    { name: 'resources/', kind: 'dir', children: [
      { name: 'views/', kind: 'dir', children: [
        { name: 'checkout.blade.php', kind: 'support' },
      ] },
    ] },
    { name: 'config/', kind: 'dir', children: [
      { name: 'payment.php', kind: 'support' },
    ] },
    { name: 'database/', kind: 'dir', children: [
      { name: 'migrations/', kind: 'dir', children: [
        { name: '2024_01_payment.php', kind: 'support' },
      ] },
    ] },
    { name: 'routes/', kind: 'dir', children: [
      { name: 'web.php', kind: 'support' },
    ] },
  ]"
/>

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
