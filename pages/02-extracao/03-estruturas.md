---
layout: statement-modular
metaNumber: "11"
metaSection: "EXTRAÇÃO"
metaSubtitle: "estruturas de pasta"
eyebrow: "uma pergunta antes do código"
---

# Tá, mas como organizamos<br>nossa estrutura de arquivos<span class="text-red-400">?</span>

<v-click>

<p>Bom… do jeito que você ficar confortável.</p>

</v-click>

<v-click>

<p class="dim">Deixa eu te mostrar 4 formas de organizar o <b>mesmo módulo</b>.</p>

</v-click>

<style>
.statement-content :deep(p.dim) {
  font-size: 1.15rem;
  opacity: 0.6;
}
.statement-content :deep(h1 .text-red-400) {
  color: var(--red);
}
</style>

<!--
"O teste falhou. Beleza. Mas antes de sair movendo arquivos, tem uma pergunta que sempre aparece: como eu organizo as pastas dentro do módulo?"

[click] "Resposta honesta: do jeito que seu time ficar confortável."

[click] "Pra provar isso, vou te mostrar o mesmo módulo — carrinho de compras — organizado de 4 formas completamente diferentes."
-->

---
layout: brutalist-base
metaNumber: "11.1"
metaSection: "EXTRAÇÃO"
metaSubtitle: "estrutura 1/4"
metaRight: "flat file"
contentAlign: "top"
---

# <span class="text-blue-400">Flat File</span>

<div class="struct-grid">
<div class="struct-left">

<div class="ns-tag">namespace App\Modules\Cart</div>

```text {*}{class:'!text-xs'}
app/Modules/Cart/
├── Cart.php
├── CartItem.php
├── CartService.php
├── PriceCalculator.php
└── ClearExpiredCartsJob.php
```

<div class="struct-count">5 arquivos · 0 subpastas</div>

</div>
<div class="struct-right">

<div class="struct-card struct-card--blue">
<div class="struct-card-tag">o que é</div>
<div class="struct-card-body">Todos os arquivos na raiz do módulo. Sem pastas, sem cerimônia.</div>
</div>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">quando usar</div>
<div class="struct-card-body">Módulo com <b class="text-blue-300">&lt; 15 arquivos</b>. Time pequeno. Início de extração.</div>
</div>

</v-click>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">referências</div>
<div class="struct-card-body">Go stdlib, pacotes Spatie simples (spatie/laravel-permission), micro-packages npm.</div>
</div>

</v-click>

</div>
</div>

<!--
"Flat file. Sem pastas, sem subdiretórios. Todos os arquivos na raiz do módulo. Parece bagunçado? Com 6 arquivos, não tem nada de bagunçado. Você abre a pasta e vê TUDO."

[click] "Quando usar? Quando o módulo é pequeno — menos de 15 arquivos. Time pequeno. Ou quando você tá começando a extrair e não quer se preocupar com estrutura ainda."

[click] "Referências: é assim que o Go organiza a standard library. Pacotes da Spatie também. Se funciona pra eles..."
-->

---
layout: brutalist-base
metaNumber: "11.2"
metaSection: "EXTRAÇÃO"
metaSubtitle: "estrutura 2/4"
metaRight: "laravel padrão"
contentAlign: "top"
---

# <span class="text-green-400">Laravel Padrão</span>

<div class="struct-grid">
<div class="struct-left">

<div class="ns-tag">namespace App\Modules\Cart</div>

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

<div class="struct-count">5 arquivos · 4 subpastas</div>

</div>
<div class="struct-right">

<div class="struct-card struct-card--green">
<div class="struct-card-tag">o que é</div>
<div class="struct-card-body">A mesma estrutura que <code>artisan make:*</code> gera. Models/, Jobs/, Services/.</div>
</div>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">quando usar</div>
<div class="struct-card-body">Time que <b class="text-green-300">já conhece Laravel</b>. Onboarding precisa ser rápido. <code>artisan make:*</code> funciona sem config.</div>
</div>

</v-click>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">referências</div>
<div class="struct-card-body">Laravel default, Laracasts, Laravel Beyond CRUD (Spatie). A maioria dos projetos Laravel do mundo.</div>
</div>

</v-click>

</div>
</div>

<!--
"Laravel padrão. A estrutura que todo dev Laravel conhece desde o primeiro tutorial. Models aqui, Jobs ali, Services lá. Exatamente o que o artisan gera."

[click] "Quando usar? Quando o time já conhece Laravel e o onboarding precisa ser instantâneo. O artisan make funciona sem nenhuma configuração extra."

[click] "Referências: é literalmente o default do framework. Laracasts ensina assim. A série Laravel Beyond CRUD da Spatie usa essa estrutura dentro dos módulos. Se é bom o suficiente pra Spatie..."
-->

---
layout: brutalist-base
metaNumber: "11.3"
metaSection: "EXTRAÇÃO"
metaSubtitle: "estrutura 3/4"
metaRight: "clean architecture"
contentAlign: "top"
---

# <span class="text-purple-400">Clean Architecture</span>

<div class="struct-grid">
<div class="struct-left">

<div class="ns-tag">namespace App\Modules\Cart</div>

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

<div class="struct-count">5 arquivos · 3 camadas</div>

</div>
<div class="struct-right">

<div class="struct-card struct-card--purple">
<div class="struct-card-tag">o que é</div>
<div class="struct-card-body">Separa <b>regras de negócio</b> (Domain) do <b>framework</b> (Infrastructure). Application orquestra.</div>
</div>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">quando usar</div>
<div class="struct-card-body">Regras de negócio <b class="text-purple-300">complexas</b> que precisam sobreviver a troca de framework ou de dependência externa.</div>
</div>

</v-click>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">referências</div>
<div class="struct-card-body">Clean Architecture (Uncle Bob), Hexagonal/Ports&Adapters, Lucid Architecture (Laravel).</div>
</div>

</v-click>

</div>
</div>

<!--
"Clean Architecture. Três camadas: Domain tem as regras de negócio puras — Cart como entidade, PriceCalculator como lógica de domínio. Application orquestra os use cases. Infrastructure tem os detalhes do framework — o Job do Laravel, integrações externas."

[click] "Quando usar? Quando suas regras de negócio são complexas e precisam sobreviver a uma troca de dependência externa. Se amanhã a regra de cálculo de preço muda, você só mexe no Domain."

[click] "Referências: é o que o Uncle Bob prega. Hexagonal Architecture é a mesma ideia com nome diferente. No mundo Laravel, o Lucid Architecture segue essa linha."
-->

---
layout: brutalist-base
metaNumber: "11.4"
metaSection: "EXTRAÇÃO"
metaSubtitle: "estrutura 4/4"
metaRight: "ddd-like"
contentAlign: "top"
---

# <span class="text-orange-400">DDD-like</span>

<div class="struct-grid">
<div class="struct-left">

<div class="ns-tag">namespace App\Modules\Cart</div>

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

<div class="struct-count">6 arquivos · 7 subpastas</div>

</div>
<div class="struct-right">

<div class="struct-card struct-card--orange">
<div class="struct-card-tag">o que é</div>
<div class="struct-card-body">Clean Architecture + padrões táticos: Actions, Aggregates, separação rígida por responsabilidade.</div>
</div>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">quando usar</div>
<div class="struct-card-body">Módulo <b class="text-orange-300">grande e complexo</b>. Time com experiência. Quando a separação por camada não é suficiente.</div>
</div>

</v-click>

<v-click>

<div class="struct-card">
<div class="struct-card-tag">referências</div>
<div class="struct-card-body">Domain-Driven Design (Eric Evans), Implementing DDD (Vaughn Vernon), Laravel Beyond CRUD (Spatie).</div>
</div>

</v-click>

</div>
</div>


<!--
"DDD-like. Parecido com Clean, mas vai mais fundo: Domain tem subpastas próprias separando Models de Services. Application separa Actions de Jobs. Cada coisa no seu lugar."

[click] "Quando usar? Quando o módulo é grande e complexo. Quando o time já tem experiência e a separação por camada simples não é suficiente. Se o time nunca trabalhou com essa granularidade, vai mais atrapalhar do que ajudar."

[click] "Referências: os livros do Eric Evans e Vaughn Vernon. No ecossistema Laravel, a série Beyond CRUD da Spatie é a principal referência."
-->

---
layout: impact-modular
metaNumber: "11.5"
metaSection: "EXTRAÇÃO"
metaSubtitle: "a virada conceitual"
color: green
---

# 4 estruturas<span class="impact-glyph">.</span>

O mesmo módulo. Os mesmos arquivos. A mesma responsabilidade.

<v-click>

<div class="impact-box">
<div class="impact-headline">
Não existe padrão certo.<br>
Existe o que <span class="g g-b">encaixa</span> pro seu time.
</div>
</div>

</v-click>

<v-click>

<div class="impact-foot">
O que importa é o <b class="impact-foot-strong">boundary</b>, não a <span class="impact-foot-dim">pasta</span>.
</div>

</v-click>

<style>
.impact-content :deep(h1) {
  font-size: 6rem;
}
.impact-content :deep(.impact-glyph) {
  color: var(--accent-green);
}
.impact-content :deep(.impact-box) {
  margin-top: 1.6rem;
  padding: 1.1rem 1.3rem;
  border: 1px solid rgba(110, 231, 161, 0.4);
  border-left: 4px solid var(--accent-green);
  background: linear-gradient(180deg, rgba(110,231,161,0.08), rgba(10,10,12,0.5));
  text-align: left;
}
.impact-content :deep(.impact-headline) {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 1.4rem;
  line-height: 1.4;
  color: var(--bone);
  letter-spacing: -0.005em;
}
.impact-content :deep(.impact-foot) {
  margin-top: 1.1rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.25rem;
  color: #b9b3a9;
}
.impact-content :deep(.impact-foot-strong) {
  color: var(--accent-green);
  font-style: normal;
  font-family: var(--font-mono);
}
.impact-content :deep(.impact-foot-dim) {
  color: var(--dim);
}
</style>

<!--
"4 estruturas completamente diferentes. Mas olha: o boundary é o MESMO. A responsabilidade é a MESMA. A estrutura de pastas é cosmética — ela não muda o que o módulo FAZ."

[click] "Não existe padrão certo. Flat file funciona. Laravel padrão funciona. Clean Architecture funciona. DDD funciona. COMO você organiza dentro do módulo é decisão do SEU time."

[click] "O que importa é o boundary, não a pasta. Agora que a gente sabe disso... vamos ver como encontrar esses boundaries num caso real."
-->
