---
layout: statement
---

# Tá, mas como organizamos nossa estrutura de arquivos?

<v-click>

<div class="mt-6 text-xl opacity-70">
Bom... do jeito que você ficar confortável.
</div>

</v-click>

<v-click>

<div class="mt-4 text-base opacity-50">
Deixa eu te mostrar 4 formas de organizar o <b>mesmo módulo</b>.
</div>

</v-click>

<!--
"O teste falhou. Beleza. Mas antes de sair movendo arquivos, tem uma pergunta que sempre aparece: como eu organizo as pastas dentro do módulo?"

[click] "Resposta honesta: do jeito que seu time ficar confortável."

[click] "Pra provar isso, vou te mostrar o mesmo módulo — carrinho de compras — organizado de 4 formas completamente diferentes."
-->

---

# <span class="text-blue-400">Flat File</span>

<div class="grid grid-cols-[45%_1fr] gap-8 mt-4">
<div>

<div class="font-mono text-[10px] opacity-50 mb-1">namespace App\Modules\Cart</div>

```text {*}{class:'!text-xs'}
app/Modules/Cart/
├── Cart.php
├── CartItem.php
├── CartService.php
├── PriceCalculator.php
└── ClearExpiredCartsJob.php
```

<div class="mt-3 text-center text-sm opacity-40">5 arquivos · 0 subpastas</div>

</div>
<div>

<div class="space-y-4">

<div class="p-3 bg-blue-900/20 rounded border border-blue-500/20">
<div class="text-blue-400 font-bold text-xs uppercase tracking-wider mb-1">O que é</div>
<div class="text-sm opacity-80">Todos os arquivos na raiz do módulo. Sem pastas, sem cerimônia.</div>
</div>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Quando usar</div>
<div class="text-sm opacity-80">Módulo com <b class="text-blue-300">&lt; 15 arquivos</b>. Time pequeno. Início de extração.</div>
</div>

</v-click>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Referências</div>
<div class="text-sm opacity-80">Go stdlib, pacotes Spatie simples (spatie/laravel-permission), micro-packages npm.</div>
</div>

</v-click>

</div>

</div>
</div>

<!--
"Flat file. Sem pastas, sem subdiretórios. Todos os arquivos na raiz do módulo. Parece bagunçado? Com 6 arquivos, não tem nada de bagunçado. Você abre a pasta e vê TUDO."

[click] "Quando usar? Quando o módulo é pequeno — menos de 15 arquivos. Time pequeno. Ou quando você tá começando a extrair e não quer se preocupar com estrutura ainda."

[click] "Referências: é assim que o Go organiza a standard library. Pacotes da Spatie também. Se funciona pra eles..."
-->

---

# <span class="text-green-400">Laravel Padrão</span>

<div class="grid grid-cols-[45%_1fr] gap-8 mt-4">
<div>

<div class="font-mono text-[10px] opacity-50 mb-1">namespace App\Modules\Cart</div>

```text {*}{class:'!text-xs'}
app/Modules/Cart/
├── Models/
│   ├── Cart.php
│   └── CartItem.php
├── Services/
│   └── CartService.php
├── Jobs/
│   └── ClearExpiredCartsJob.php
└── Support/
    └── PriceCalculator.php
```

<div class="mt-3 text-center text-sm opacity-40">5 arquivos · 4 subpastas</div>

</div>
<div>

<div class="space-y-4">

<div class="p-3 bg-green-900/20 rounded border border-green-500/20">
<div class="text-green-400 font-bold text-xs uppercase tracking-wider mb-1">O que é</div>
<div class="text-sm opacity-80">A mesma estrutura que <code>artisan make:*</code> gera. Models/, Jobs/, Services/.</div>
</div>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Quando usar</div>
<div class="text-sm opacity-80">Time que <b class="text-green-300">já conhece Laravel</b>. Onboarding precisa ser rápido. <code>artisan make:*</code> funciona sem config.</div>
</div>

</v-click>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Referências</div>
<div class="text-sm opacity-80">Laravel default, Laracasts, Laravel Beyond CRUD (Spatie). A maioria dos projetos Laravel do mundo.</div>
</div>

</v-click>

</div>

</div>
</div>

<!--
"Laravel padrão. A estrutura que todo dev Laravel conhece desde o primeiro tutorial. Models aqui, Jobs ali, Services lá. Exatamente o que o artisan gera."

[click] "Quando usar? Quando o time já conhece Laravel e o onboarding precisa ser instantâneo. O artisan make funciona sem nenhuma configuração extra."

[click] "Referências: é literalmente o default do framework. Laracasts ensina assim. A série Laravel Beyond CRUD da Spatie usa essa estrutura dentro dos módulos. Se é bom o suficiente pra Spatie..."
-->

---

# <span class="text-purple-400">Clean Architecture</span>

<div class="grid grid-cols-[45%_1fr] gap-8 mt-4">
<div>

<div class="font-mono text-[10px] opacity-50 mb-1">namespace App\Modules\Cart</div>

```text {*}{class:'!text-xs'}
app/Modules/Cart/
├── Domain/
│   ├── Cart.php
│   ├── CartItem.php
│   └── PriceCalculator.php
├── Application/
│   └── CartService.php
└── Infrastructure/
    └── ClearExpiredCartsJob.php
```

<div class="mt-3 text-center text-sm opacity-40">5 arquivos · 3 camadas</div>

</div>
<div>

<div class="space-y-4">

<div class="p-3 bg-purple-900/20 rounded border border-purple-500/20">
<div class="text-purple-400 font-bold text-xs uppercase tracking-wider mb-1">O que é</div>
<div class="text-sm opacity-80">Separa <b>regras de negócio</b> (Domain) do <b>framework</b> (Infrastructure). Application orquestra.</div>
</div>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Quando usar</div>
<div class="text-sm opacity-80">Regras de negócio <b class="text-purple-300">complexas</b> que precisam sobreviver a troca de framework ou de dependência externa.</div>
</div>

</v-click>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Referências</div>
<div class="text-sm opacity-80">Clean Architecture (Uncle Bob), Hexagonal/Ports&Adapters, Lucid Architecture (Laravel).</div>
</div>

</v-click>

</div>

</div>
</div>

<!--
"Clean Architecture. Três camadas: Domain tem as regras de negócio puras — Cart como entidade, PriceCalculator como lógica de domínio. Application orquestra os use cases. Infrastructure tem os detalhes do framework — o Job do Laravel, integrações externas."

[click] "Quando usar? Quando suas regras de negócio são complexas e precisam sobreviver a uma troca de dependência externa. Se amanhã a regra de cálculo de preço muda, você só mexe no Domain."

[click] "Referências: é o que o Uncle Bob prega. Hexagonal Architecture é a mesma ideia com nome diferente. No mundo Laravel, o Lucid Architecture segue essa linha."
-->

---

# <span class="text-orange-400">DDD-like</span>

<div class="grid grid-cols-[45%_1fr] gap-8 mt-4">
<div>

<div class="font-mono text-[10px] opacity-50 mb-1">namespace App\Modules\Cart</div>

```text {*}{class:'!text-xs'}
app/Modules/Cart/
├── Domain/
│   ├── Models/
│   │   ├── Cart.php
│   │   └── CartItem.php
│   └── Services/
│       └── PriceCalculator.php
├── Application/
│   ├── Actions/
│   │   └── AddToCartAction.php
│   └── Jobs/
│       └── ClearExpiredCartsJob.php
└── Infrastructure/
    └── EloquentCartRepository.php
```

<div class="mt-3 text-center text-sm opacity-40">6 arquivos · 7 subpastas</div>

</div>
<div>

<div class="space-y-4">

<div class="p-3 bg-orange-900/20 rounded border border-orange-500/20">
<div class="text-orange-400 font-bold text-xs uppercase tracking-wider mb-1">O que é</div>
<div class="text-sm opacity-80">Clean Architecture + padrões táticos: Actions, Aggregates, separação rígida por responsabilidade.</div>
</div>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Quando usar</div>
<div class="text-sm opacity-80">Módulo <b class="text-orange-300">grande e complexo</b>. Time com experiência. Quando a separação por camada não é suficiente.</div>
</div>

</v-click>

<v-click>

<div class="p-3 bg-gray-800/40 rounded border border-gray-600/20">
<div class="text-gray-400 font-bold text-xs uppercase tracking-wider mb-1">Referências</div>
<div class="text-sm opacity-80">Domain-Driven Design (Eric Evans), Implementing DDD (Vaughn Vernon), Laravel Beyond CRUD (Spatie).</div>
</div>

</v-click>

</div>

</div>
</div>

<!--
"DDD-like. Parecido com Clean, mas vai mais fundo: Domain tem subpastas próprias separando Models de Services. Application separa Actions de Jobs. Cada coisa no seu lugar."

[click] "Quando usar? Quando o módulo é grande e complexo. Quando o time já tem experiência e a separação por camada simples não é suficiente. Se o time nunca trabalhou com essa granularidade, vai mais atrapalhar do que ajudar."

[click] "Referências: os livros do Eric Evans e Vaughn Vernon. No ecossistema Laravel, a série Beyond CRUD da Spatie é a principal referência."
-->

---
layout: impact
color: green
---

# 4 estruturas

O mesmo módulo. Os mesmos arquivos. A mesma responsabilidade.

<v-click>

<div class="mt-8 p-6 bg-yellow-900/40 rounded-lg border-2 border-yellow-500/50">
<div class="text-2xl font-bold text-yellow-400">
Não existe padrão certo.<br>
Existe o que encaixa pro seu time.
</div>
</div>

</v-click>

<v-click>

<div class="mt-6 text-lg opacity-70">
O que importa é o <span class="text-green-400 font-bold">boundary</span>, não a <span class="text-gray-400">pasta</span>.
</div>

</v-click>

<!--
"4 estruturas completamente diferentes. Mas olha: o boundary é o MESMO. A responsabilidade é a MESMA. A estrutura de pastas é cosmética — ela não muda o que o módulo FAZ."

[click] "Não existe padrão certo. Flat file funciona. Laravel padrão funciona. Clean Architecture funciona. DDD funciona. COMO você organiza dentro do módulo é decisão do SEU time."

[click] "O que importa é o boundary, não a pasta. Agora que a gente sabe disso... vamos ver como encontrar esses boundaries num caso real."
-->
