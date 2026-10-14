---
layout: ph-impact
tone: orange
size: statement
eyebrow: uma pergunta antes do código
---

# Tá, mas como organizamos nossa estrutura de arquivos?

<v-click>

<p class="ph-impact__q">Bom… <strong>do jeito que você ficar confortável.</strong></p>

</v-click>

<v-click>

<div class="ph-impact__punch">Deixa eu te mostrar 4 formas de organizar o <strong>mesmo módulo</strong>.</div>

</v-click>

<!--
"O teste falhou. Beleza. Mas antes de sair movendo arquivos, tem uma pergunta que sempre aparece: como eu organizo as pastas dentro do módulo?"

[click] "Resposta honesta: do jeito que seu time ficar confortável."

[click] "Pra provar isso, vou te mostrar o mesmo módulo — carrinho de compras — organizado de 4 formas completamente diferentes."
-->

---
layout: ph-section
tone: sand
eyebrow: estrutura 1 de 4 · o mesmo módulo Cart
transition: fade
---

# Flat File

Todos os arquivos na raiz do módulo. Sem pastas, sem cerimônia.

::content::

<div class="ph-split" style="grid-template-columns: 19rem 1fr">

<PhTicket class="ph-ticket--tree" label="app/Modules/Cart/" title="5 arquivos · 0 subpastas">
<pre>├── Cart.php
├── CartItem.php
├── CartService.php
├── PriceCalculator.php
└── ClearExpiredCartsJob.php</pre>
</PhTicket>

<div class="ph-panel">

<v-clicks>

- <mdi-clock-check-outline /> **Quando usar:** Módulo com menos de 15 arquivos. Time pequeno. Início de extração.
- <mdi-bookshelf /> **Referências:** Go stdlib, pacotes simples da Spatie (spatie/laravel-permission), micro-packages npm.

</v-clicks>

</div>
</div>

<!--
"Flat file. Sem pastas, sem subdiretórios. Todos os arquivos na raiz do módulo. Parece bagunçado? Com 5 arquivos, não tem nada de bagunçado. Você abre a pasta e vê TUDO."

[click] "Quando usar? Quando o módulo é pequeno — menos de 15 arquivos. Time pequeno. Ou quando você tá começando a extrair e não quer se preocupar com estrutura ainda."

[click] "Referências: é assim que o Go organiza a standard library. Pacotes da Spatie também. Se funciona pra eles..."
-->

---
layout: ph-section
tone: sand
eyebrow: estrutura 2 de 4 · o mesmo módulo Cart
transition: fade
---

# Laravel Padrão

A mesma estrutura que `artisan make:*` gera: Models/, Jobs/, Services/.

::content::

<div class="ph-split" style="grid-template-columns: 19rem 1fr">

<PhTicket class="ph-ticket--tree" label="app/Modules/Cart/" title="5 arquivos · 4 subpastas">
<pre>├── Models/
│   ├── Cart.php
│   └── CartItem.php
├── Services/
│   └── CartService.php
├── Jobs/
│   └── ClearExpiredCartsJob.php
└── Support/
    └── PriceCalculator.php</pre>
</PhTicket>

<div class="ph-panel">

<v-clicks>

- <mdi-clock-check-outline /> **Quando usar:** Time que já conhece Laravel. Onboarding rápido. `artisan make:*` funciona sem config.
- <mdi-bookshelf /> **Referências:** Laravel default, Laracasts, Laravel Beyond CRUD (Spatie). A maioria dos projetos Laravel do mundo.

</v-clicks>

</div>
</div>

<!--
"Laravel padrão. A estrutura que todo dev Laravel conhece desde o primeiro tutorial. Models aqui, Jobs ali, Services lá. Exatamente o que o artisan gera."

[click] "Quando usar? Quando o time já conhece Laravel e o onboarding precisa ser instantâneo. O artisan make funciona sem nenhuma configuração extra."

[click] "Referências: é literalmente o default do framework. Laracasts ensina assim. A série Laravel Beyond CRUD da Spatie usa essa estrutura dentro dos módulos. Se é bom o suficiente pra Spatie..."
-->

---
layout: ph-section
tone: sand
eyebrow: estrutura 3 de 4 · o mesmo módulo Cart
transition: fade
---

# Clean Architecture

Separa **regras de negócio** (Domain) do **framework** (Infrastructure). Application orquestra.

::content::

<div class="ph-split" style="grid-template-columns: 19rem 1fr">

<PhTicket class="ph-ticket--tree" label="app/Modules/Cart/" title="5 arquivos · 3 camadas">
<pre>├── Domain/
│   ├── Cart.php
│   ├── CartItem.php
│   └── PriceCalculator.php
├── Application/
│   └── CartService.php
└── Infrastructure/
    └── ClearExpiredCartsJob.php</pre>
</PhTicket>

<div class="ph-panel">

<v-clicks>

- <mdi-clock-check-outline /> **Quando usar:** Regras de negócio complexas, que precisam sobreviver a troca de framework ou de dependência externa.
- <mdi-bookshelf /> **Referências:** Clean Architecture (Uncle Bob), Hexagonal / Ports & Adapters, Lucid Architecture (Laravel).

</v-clicks>

</div>
</div>

<!--
"Clean Architecture. Três camadas: Domain tem as regras de negócio puras — Cart como entidade, PriceCalculator como lógica de domínio. Application orquestra os use cases. Infrastructure tem os detalhes do framework — o Job do Laravel, integrações externas."

[click] "Quando usar? Quando suas regras de negócio são complexas e precisam sobreviver a uma troca de dependência externa. Se amanhã a regra de cálculo de preço muda, você só mexe no Domain."

[click] "Referências: é o que o Uncle Bob prega. Hexagonal Architecture é a mesma ideia com nome diferente. No mundo Laravel, o Lucid Architecture segue essa linha."
-->

---
layout: ph-section
tone: sand
eyebrow: estrutura 4 de 4 · o mesmo módulo Cart
transition: fade
---

# DDD-like

Clean Architecture + padrões táticos: Aggregates, serviços de domínio, separação rígida por responsabilidade.

::content::

<div class="ph-split" style="grid-template-columns: 19rem 1fr">

<PhTicket class="ph-ticket--tree" label="app/Modules/Cart/" title="5 arquivos · 7 subpastas">
<pre>├── Domain/
│   ├── Models/
│   │   ├── Cart.php
│   │   └── CartItem.php
│   └── Services/
│       └── PriceCalculator.php
├── Application/
│   └── Services/
│       └── CartService.php
└── Infrastructure/
    └── Jobs/
        └── ClearExpiredCartsJob.php</pre>
</PhTicket>

<div class="ph-panel">

<v-clicks>

- <mdi-clock-check-outline /> **Quando usar:** Módulo grande e complexo. Time com experiência. Quando separar por camada não basta.
- <mdi-bookshelf /> **Referências:** Domain-Driven Design (Eric Evans), Implementing DDD (Vaughn Vernon), Laravel Beyond CRUD (Spatie).

</v-clicks>

</div>
</div>

<!--
"DDD-like. Parecido com Clean, mas vai mais fundo: cada camada ganha subpastas. Domain separa Models de Services, Application tem os seus Services, Infrastructure guarda os Jobs. Os mesmos 5 arquivos — só que cada um no seu escaninho."

[click] "Quando usar? Quando o módulo é grande e complexo. Quando o time já tem experiência e a separação por camada simples não é suficiente. Se o time nunca trabalhou com essa granularidade, vai mais atrapalhar do que ajudar."

[click] "Referências: os livros do Eric Evans e Vaughn Vernon. No ecossistema Laravel, a série Beyond CRUD da Spatie é a principal referência."
-->

---
layout: ph-impact
tone: orange
size: statement
---

# 4 estruturas.

O mesmo módulo. Os mesmos 5 arquivos. A mesma responsabilidade.

<v-click>

<p class="ph-impact__q">Não existe padrão certo. <strong>Existe o que encaixa pro seu time.</strong></p>

</v-click>

<v-click>

<div class="ph-impact__punch">O que importa é o <strong>boundary</strong>, não a pasta.</div>

</v-click>

<!--
"4 estruturas completamente diferentes. Mas olha: o boundary é o MESMO. A responsabilidade é a MESMA. A estrutura de pastas é cosmética — ela não muda o que o módulo FAZ."

[click] "Não existe padrão certo. Flat file funciona. Laravel padrão funciona. Clean Architecture funciona. DDD funciona. COMO você organiza dentro do módulo é decisão do SEU time."

[click] "O que importa é o boundary, não a pasta. Então bora: junta tudo de pagamento num lugar só e roda o teste de novo."
-->
