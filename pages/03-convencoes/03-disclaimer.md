---
layout: statement-modular
metaNumber: "17"
metaSection: "CONVENÇÕES"
metaSubtitle: "a sua casa, suas regras"
eyebrow: "antes de você copiar isso pro seu projeto"
---

# Essas <span class="strike-thin">não</span> são regras.

<v-click>

<p>São as <b>MINHAS</b>. E funcionam <span class="serif-em">porque eu sei explicar pro meu time</span> — não porque saí num post-it na parede da Apple.</p>

</v-click>

<v-click>

<p>As suas vão diferir. <span class="serif-em ok">Tá tudo bem.</span></p>

</v-click>

<div class="disclaimer-tail">
convenções <span class="tail-em">emergem do time</span>, não de mim
</div>

<style>
.statement-content :deep(h1) {
  font-size: 4.6rem;
  line-height: 0.96;
  color: var(--bone);
  letter-spacing: -0.005em;
  margin-bottom: 1.3rem;
}
.statement-content :deep(p) {
  font-family: var(--font-mono);
  font-style: normal;
  font-size: 1.2rem;
  line-height: 1.55;
  color: #c8c2b6;
  margin: 0 0 0.75rem;
  max-width: 64ch;
}
.statement-content :deep(p b) {
  color: var(--bone);
  font-weight: 700;
}
.statement-content :deep(.serif-em) {
  font-family: var(--font-serif);
  font-style: italic;
  color: #b9b3a9;
}
.statement-content :deep(.serif-em.ok) {
  color: var(--bone);
}

.disclaimer-tail {
  margin-top: 1.6rem;
  padding-top: 0.7rem;
  border-top: 1px solid var(--rule);
  font-family: var(--font-mono);
  font-size: 0.7rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--dim);
}
.tail-em { color: var(--bone); font-weight: 700; }
</style>

<style>
/* unscoped so the pseudo-element on .strike-thin can apply */
.strike-thin {
  position: relative;
  color: var(--dim);
  font-weight: 700;
}
.strike-thin::after {
  content: "";
  position: absolute;
  left: -6%;
  right: -6%;
  top: 51%;
  height: 6px;
  background: var(--red);
  box-shadow: 0 0 16px rgba(255, 45, 32, 0.45);
  transform: rotate(-2deg);
  pointer-events: none;
}
</style>

<!--
"E agora a parte mais importante dessas duas convenções que eu acabei de mostrar."

"Elas não são regras. Não saíram de um livro, não tô fundando uma escola, ninguém vai te dar nota baixa em code review por não seguir."

[click] "Elas são as MINHAS. E funcionam porque eu sei explicar pro meu time. Eu consigo justificar cada decisão. Quando entra dev novo na 3Pontos, eu desenho no quadro por que `integration-stripe` é um módulo separado — e isso faz sentido pra ele."

[click] "As suas vão diferir. Talvez seu time prefira `vendors/` em vez de `integration-*`. Talvez vocês usem um painel só. Talvez tenham seis painéis. Tá tudo bem. De verdade."

"O que NÃO funciona é copiar a convenção de um talk e empurrar goela abaixo no time sem conversa. Isso sempre quebra. O que faz convenção pegar é o time inteiro entender o porquê."

[transição] "Beleza. Já chega de regrinha. Vamos pra parte que vale a pena — o que você ganha fazendo tudo isso."
-->
