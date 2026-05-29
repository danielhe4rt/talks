---
layout: brutalist-base
metaNumber: "14"
metaSection: "EXTRAÇÃO"
metaSubtitle: "comunicação entre módulos"
metaPhase: refactor
metaRight: "Q2 · EVENTOS"
contentAlign: "top"
transition: fade
---

<div class="ev-intro">
  <span class="ev-intro__eyebrow">conceito antes do código</span>
  <p class="ev-intro__pitch">
    Dois jeitos de um módulo falar com outro.<br>
    Um sobrevive ao <span class="g g-b">Teste da Deleção</span>. O outro não.
  </p>
</div>

<EventCompare />

<style>
.ev-intro {
  margin-top: 0.2rem;
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
}
.ev-intro__eyebrow {
  font-family: var(--font-mono);
  font-size: 0.55rem;
  letter-spacing: 0.26em;
  text-transform: uppercase;
  color: var(--red);
  font-weight: 700;
}
.ev-intro__pitch {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.95rem;
  line-height: 1.3;
  color: #c8c2b6;
  margin: 0;
  max-width: 60%;
}
.ev-intro__pitch b,
.ev-intro__pitch strong {
  color: var(--bone);
  font-family: var(--font-mono);
  font-style: normal;
  font-weight: 700;
}
</style>

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
