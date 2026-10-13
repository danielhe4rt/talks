---
layout: ph-act
act: "03"
eyebrow: ato 3 · convenções
duration: ~7 min · dia a dia do time
---

# As minhas convenções.

integration-* e panel-*: o que funciona pro meu time.

<!--
"O teste passou. Isso é o método. Agora: como isso fica no dia a dia do meu time? Duas convenções que a gente usa na 3Pontos."
-->

---
layout: ph-section
tone: sand
eyebrow: convenção 1 · um fornecedor, um módulo
hint: próxima convenção
clicks: 1
---

# Integration-*

Todo serviço externo vira **módulo próprio**. Mesmo se for só um SDK e três chamadas.

::content::

<div class="ph-split" style="grid-template-columns: 1fr 1fr">

<PhTicket class="ph-ticket--tree" label="app-modules/" title="6 fornecedores · 6 módulos">
<pre>integration-stripe/    → Shop\IntegrationStripe
integration-paypal/    → Shop\IntegrationPaypal
integration-correios/  → Shop\IntegrationCorreios
integration-twilio/    → Shop\IntegrationTwilio
integration-slack/     → Shop\IntegrationSlack
integration-github/    → Shop\IntegrationGithub</pre>
</PhTicket>

<div class="ph-deps">
  <div class="ph-dep"><code>Payment</code><span class="ph-dep__verb">fala com</span><code>GatewayContract</code><span class="ph-dep__tag">gateway</span></div>
  <div class="ph-dep"><code>integration-stripe</code><span class="ph-dep__verb">implementa</span><code>GatewayContract</code><span class="ph-dep__tag">fornecedor</span></div>
  <p class="ph-callout ph-callout--ok">Lembra do <strong>Gateway</strong>? Ele fica com o contrato. A Stripe mora sozinha na sua pasta — <strong>nenhum domínio importa fornecedor direto</strong>.</p>
  <p class="ph-callout ph-callout--warn" v-click="1">SDK mudou, endpoint depreciou? <strong>Quebrou amanhã, você sabe onde.</strong></p>
</div>

</div>

<!--
"Convenção número um — e antes que alguém levante a mão: essas não são regras de modularização. São as MINHAS. Funcionam pro meu time. Talvez encaixem no seu, talvez não."

"Primeira: todo serviço externo vira módulo próprio. Stripe? `integration-stripe`. Correios? `integration-correios`. Slack pra alertas? `integration-slack`. Mesmo que seja só um SDK e três chamadas — ele tem casa."

"Por quê? Porque fornecedor quebra. SDK lança breaking change. Endpoint deprecia. Quando isso acontecer — e vai acontecer — você sabe onde ir. Você não vai sair caçando `Stripe::charge` em 30 arquivos pelo projeto."

"E o domínio nunca importa o fornecedor direto. Lembra do Gateway do Teste da Deleção? Ele fica só com o contrato. O StripeGateway sai de lá e vira `integration-stripe`, que implementa esse contrato. Payment fala com o Gateway — nunca com a Stripe. Trocou de gateway? Mexe num módulo. Só."

[transição] "Próxima convenção."
-->

---
layout: ph-section
tone: espresso
eyebrow: convenção 2 · um público, um painel
hint: uma última coisa
clicks: 2
---

# Panel-*

Frontend fatiado por **audiência**. Mesma régua dos outros módulos — **muda só o stack**.

::content::

<div class="ph-split" style="grid-template-columns: 15rem 1fr">
<div class="ph-tabs">
  <div class="ph-tab" :class="{ 'is-active': $clicks === 0 }"><span class="ph-tab__num">01</span><span class="ph-tab__name">panel-admin</span><span class="ph-tab__sub">operação · suporte · financeiro</span><span class="ph-tab__stack">filament</span></div>
  <div class="ph-tab" :class="{ 'is-active': $clicks === 1 }"><span class="ph-tab__num">02</span><span class="ph-tab__name">panel-app</span><span class="ph-tab__sub">cliente logado</span><span class="ph-tab__stack">livewire</span></div>
  <div class="ph-tab" :class="{ 'is-active': $clicks === 2 }"><span class="ph-tab__num">03</span><span class="ph-tab__name">panel-guest</span><span class="ph-tab__sub">público · landing · SEO</span><span class="ph-tab__stack">blade</span></div>
</div>

<div>
<div class="ph-tabpane" v-show="$clicks === 0">
  <p class="ph-file-label">namespace Shop\PanelAdmin</p>
<pre class="ph-files"><span>app-modules/panel-admin/</span><span class="is-ctx">├── composer.json</span><span>├── src/</span><span class="is-hit">│   ├── Resources/Orders/OrderResource.php</span><span class="is-ctx">│   │   ├── Pages/ListOrders.php</span><span class="is-ctx">│   │   ├── Schemas/OrderForm.php</span><span class="is-ctx">│   │   └── Tables/OrdersTable.php</span><span class="is-hit">│   ├── Resources/Products/ProductResource.php</span><span class="is-ctx">│   ├── Clusters/Catalog/CatalogCluster.php</span><span class="is-ctx">│   ├── Pages/Dashboard.php</span><span class="is-ctx">│   ├── Widgets/SalesOverview.php</span><span class="is-hit">│   └── AdminPanelProvider.php</span><span class="is-ctx">└── resources/views/</span></pre>
</div>
<div class="ph-tabpane" v-show="$clicks === 1">
  <p class="ph-file-label">namespace Shop\PanelApp</p>
<pre class="ph-files"><span>app-modules/panel-app/</span><span class="is-ctx">├── composer.json</span><span>├── src/</span><span class="is-hit">│   ├── Livewire/Dashboard.php</span><span class="is-hit">│   ├── Livewire/OrderHistory.php</span><span class="is-ctx">│   ├── Livewire/Timeline/Feed.php</span><span class="is-ctx">│   ├── Pages/LoginPage.php</span><span class="is-ctx">│   ├── Pages/ProfilePage.php</span><span class="is-hit">│   └── PanelAppServiceProvider.php</span><span class="is-ctx">└── resources/views/livewire/</span></pre>
</div>
<div class="ph-tabpane" v-show="$clicks === 2">
  <p class="ph-file-label">namespace Shop\PanelGuest</p>
<pre class="ph-files"><span>app-modules/panel-guest/</span><span class="is-ctx">├── composer.json</span><span>├── src/</span><span class="is-ctx">│   ├── Http/HomeController.php</span><span class="is-hit">│   └── PanelGuestServiceProvider.php</span><span>├── resources/views/</span><span class="is-hit">│   ├── home.blade.php</span><span class="is-hit">│   ├── catalog.blade.php</span><span class="is-ctx">│   └── components/hero.blade.php</span><span class="is-ctx">└── routes/web.php</span></pre>
</div>
<p class="ph-callout ph-callout--ok" style="margin-top: 0.6rem">Três pastas, três providers, três namespaces. <strong>Nenhum sabe que os outros existem</strong> — e o backend é o mesmo.</p>
</div>
</div>

<!--
"Convenção número dois: panel."

"O frontend fatia por AUDIÊNCIA. Cada painel vira módulo próprio — mesma régua de qualquer outro módulo: composer.json no topo, src/, resources/, ServiceProvider. Mas o STACK muda conforme o público. Olha só."

[estado inicial — panel-admin ativo]
"01: panel-admin. Stack: Filament. Quem mexe aqui é operação, suporte, financeiro — gente que trabalha NO produto, não COM o produto. Resources de Product, Order. Páginas de Dashboard. Widgets de overview. Tudo dentro de src/Resources/, src/Pages/ e src/Widgets/. namespace Shop\\PanelAdmin."

[click 1 — panel-app ativo]
"02: panel-app. Cliente logado. Stack: Livewire. Dashboard interativo, histórico de pedido, timeline. As pages de auth ficam em src/Pages/. Views em resources/views/livewire/. namespace Shop\\PanelApp. Quem já comprou e voltou."

[click 2 — panel-guest ativo]
"03: panel-guest. O público. Aqui o stack despe — é Blade puro. Home, catálogo, landing. Um HomeController, um ServiceProvider, e o resto é template. SEO friendly, sem peso de Livewire onde não precisa. namespace Shop\\PanelGuest."

"Repara: três pastas. Três composer.json. Três ServiceProviders. Três namespaces. Cada audiência tem o stack QUE ELA precisa — não o stack que o app inteiro usa. E NENHUM dos três sabe que os outros existem."

"O backend? Os mesmos módulos de domínio do Teste da Deleção: checkout, payment, shipping. Só muda a casca."

[transição] "Uma última coisa antes de fechar essa parte."
-->

---
layout: ph-impact
tone: sand
size: statement
eyebrow: antes de você copiar isso pro seu projeto
---

# Essas não são regras.

<v-click>

<p class="ph-impact__q">São as <strong>minhas</strong>. E funcionam porque eu sei explicar pro meu time.</p>

</v-click>

<v-click>

<div class="ph-impact__punch">As suas vão diferir. <strong>Tá tudo bem</strong> — convenção emerge do time.</div>

</v-click>

<!--
"E agora a parte mais importante dessas duas convenções que eu acabei de mostrar."

"Elas não são regras. Não saíram de um livro, não tô fundando uma escola, ninguém vai te dar nota baixa em code review por não seguir."

[click] "Elas são as MINHAS. E funcionam porque eu sei explicar pro meu time. Eu consigo justificar cada decisão. Quando entra dev novo na 3Pontos, eu desenho no quadro por que `integration-stripe` é um módulo separado — e isso faz sentido pra ele."

[click] "As suas vão diferir. Talvez seu time prefira `vendors/` em vez de `integration-*`. Talvez vocês usem um painel só. Talvez tenham seis painéis. Tá tudo bem. De verdade."

"O que NÃO funciona é copiar a convenção de um talk e empurrar goela abaixo no time sem conversa. Isso sempre quebra. O que faz convenção pegar é o time inteiro entender o porquê."

[transição] "Beleza. Já chega de regrinha. Vamos pra parte que vale a pena — o que você ganha fazendo tudo isso."
-->
