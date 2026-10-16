---
layout: ph-act
act: "04"
eyebrow: ato 4 · fechamento
duration: ~6 min · o que isso compra
---

# Valeu a pena?

O dia em que o produto pivota.

<!--
"Último ato."
-->

---
layout: ph-section
tone: sand
eyebrow: o que isso compra é uma coisa só
hint: e não é só comigo
clicks: 3
---

# Quando o produto pivotar.

E ele **vai**. É só questão de quando.

::content::

<div class="ph-split" style="grid-template-columns: 1fr 1fr; align-items: start">

<PhTicket class="ph-ticket--tree" label="trocar de gateway de pagamento" title="2 operações">
<pre class="ph-diff"><span class="is-del">− integration-stripe/    apaga a pasta</span>
<span class="is-add">+ integration-pagarme/   adiciona a nova</span></pre>
</PhTicket>

<div class="ph-panel">

<v-clicks at="1">

- <mdi-cart-outline /> **checkout/** nem fica sabendo
- <mdi-credit-card-outline /> **payment/** intacto
- <mdi-file-sign /> **gateway/** mesmo contrato, outra implementação

</v-clicks>

</div>
</div>

<div class="ph-split" style="grid-template-columns: 1fr; margin-top: 0.9rem; gap: 0.6rem">
<p class="ph-callout ph-callout--ok" v-click="2"><strong>De brinde, no dia a dia:</strong> merge sem conflito · teste isolado · cada coisa num lugar.</p>
<div class="ph-verdict" v-click="3" style="padding: 0.7rem 1rem"><p style="font-size: 1.2rem">Boundary não é sobre hoje — <strong>é sobre o dia que tudo muda.</strong></p></div>
</div>

<!--
"Tá. A gente passou por boundary, deletion test, eventos, internachi, convenções. Vale a pergunta honesta: valeu a pena toda essa zona? E a resposta — o que isso COMPRA de verdade — é uma coisa só."

"Quando o produto pivotar. E ele vai pivotar — é só questão de quando."

[estado inicial — o diff de cima]
"Cliente decidiu trocar de gateway: sai Stripe, entra Pagar.me. Em vez de uma cirurgia de dias caçando referências espalhadas, é isso: apaga a pasta integration-stripe inteira, adiciona integration-pagarme. Duas operações."

[click 1 — os módulos de domínio]
"E o domínio? Checkout nem fica sabendo. Payment, intacto. E o Gateway? Mesmo contrato — só mudou quem implementa. Ninguém quebra, porque ninguém importava a integração direto — o boundary segurou."

[click 2 — bônus]
"Todo o resto — merge sem conflito, teste isolado, cada coisa num lugar — isso vem de brinde no dia a dia. Importante, mas é consequência."

[click 3 — punch]
"Porque no fim, boundary não é sobre hoje. Hoje qualquer estrutura funciona. Boundary é sobre o dia que tudo muda — e esse dia sempre chega."

[transição] "E não é só comigo, não..."
-->

---
layout: ph-section
tone: espresso
eyebrow: e quando a escala muda tudo?
clicks: 5
---

# A mesma conta, em escala.

Prime Video, 2023: **−90% de custo** ao juntar um serviço num processo só.

::content::

<div class="ph-spectrum">
  <div class="ph-spectrum__node"><span class="ph-spectrum__name">monólito clássico</span><span class="ph-spectrum__sub">acopla tudo num bolo</span></div>
  <div class="ph-spectrum__node is-win"><span class="ph-spectrum__name">Monólito modular</span><span class="ph-spectrum__sub">o ponto de equilíbrio</span></div>
  <div class="ph-spectrum__node"><span class="ph-spectrum__name">microsserviços</span><span class="ph-spectrum__sub">complexidade distribuída</span></div>
</div>

<div class="ph-gains" style="margin-top: 0.7rem">
  <div class="ph-gain" v-click="1"><span class="ph-badge"><mdi-package-variant-closed /></span><span class="ph-gain__title">Deploy único</span><span class="ph-gain__text">Um pipeline, não 80 serviços pra orquestrar.</span><span class="ph-src">Shopify Engineering</span></div>
  <div class="ph-gain" v-click="2"><span class="ph-badge"><mdi-trending-down /></span><span class="ph-gain__title">Distribuir cedo cobra caro</span><span class="ph-gain__text">Rede e orquestração têm conta. Em processo, não.</span><span class="ph-src">Prime Video · 2023</span></div>
  <div class="ph-gain" v-click="3"><span class="ph-badge"><mdi-shield-check-outline /></span><span class="ph-gain__title">Boundary que o time respeita</span><span class="ph-gain__text">Interface pública, enforce por ferramenta.</span><span class="ph-src">Packwerk · internachi</span></div>
  <div class="ph-gain" v-click="4"><span class="ph-badge"><mdi-source-branch /></span><span class="ph-gain__title">Saída evolutiva</span><span class="ph-gain__text">Extrai pra microsserviço só quando doer.</span><span class="ph-src">Jovanović · Grzybek</span></div>
</div>

<p class="ph-rule-text" v-click="5" style="color: var(--ph-sand-lt); margin-top: 0.5rem">modulariza primeiro — distribui só quando a dor justificar.</p>

<!--
"Eu acabei de mostrar a MINHA conta: quando o produto pivota, eu troco um módulo sem cirurgia. E aí vem a dúvida: tá, mas isso é exagero de quem tem um app pequeno? Não. Quando a escala muda tudo de verdade, os grandes fizeram exatamente a mesma conta."

[hero — Prime Video]
"O exemplo que calou a galera foi a Amazon Prime Video, em 2023: o time que monitora a qualidade dos vídeos tinha montado o serviço distribuído, em pedacinhos serverless. Juntaram tudo num processo só — um monólito — e o custo caiu 90%. Distribuir não é grátis: tem rede, tem orquestração."

[click 1] "Deploy único. Um pipeline de build, test e deploy. A Shopify roda um dos maiores monólitos Rails do mundo, milhares de devs num codebase só — modular, com boundaries impostos por ferramenta."

[click 2] "Distribuir cedo cobra caro: rede e orquestração têm conta. In-process não tem. Por isso a Prime Video consolidou."

[click 3] "Boundary que o time respeita de verdade. Interface pública, implementação encapsulada, e o enforce vem de ferramenta — Packwerk na Shopify, internachi no nosso caso. É o mesmo boundary que segurou meu pivot no slide anterior."

[click 4] "E a saída evolutiva: mudar boundary num monólito modular é barato. Se um dia a escala doer DE VERDADE, você extrai aquele módulo pra microservice. Mas só quando doer — Milan Jovanović e Kamil Grzybek batem nessa tecla há anos."

[click 5 — tail] "Do seu legado ao catálogo da Shopify, a régua é a mesma: modulariza primeiro, distribui só quando a dor justificar a conta."

[transição] "Então, pra fechar de vez..."
-->

---
layout: ph-whoami
transition: fade
when: Sexta · 16/10
---

# Obrigado!

Módulo a módulo. **Boundary a boundary.**

- <mdi-heart /> **heartdevs.com** · comunidade, mentoria, open source
- <mdi-twitch /> **twitch.tv/danielhe4rt** · livecoding, 6 anos no ar
- <mdi-github /> **github.com/danielhe4rt** · o código

<!--
"E é isso, gente. 40 minutos. Uma história. Duas convenções. Um Teste da Deleção."

[pausa]

"Lembra de uma coisa: módulo a módulo. Boundary a boundary. Você não precisa modularizar o sistema todo amanhã. Pega um pedaço que dói — aquele canto do código que ninguém quer mexer — e extrai SÓ ele. Roda o Teste da Deleção. Se passar, pega o próximo."

"Se quiser continuar a conversa: He4rt Developers em heartdevs.com — comunidade de devs br, mentoria, open source. Livecoding na Twitch, twitch.tv/danielhe4rt, 6 anos no ar. E o código tá no github.com/danielhe4rt."


[pausa]

"Obrigado pelo tempo de vocês. Bom evento!"

[Q&A — fica nesse slide com o cursor piscando.]
-->
