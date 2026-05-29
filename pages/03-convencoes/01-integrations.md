---
layout: brutalist-base
metaNumber: "15"
metaSection: "CONVENÇÕES"
metaSubtitle: "integration · *"
contentAlign: "top"
---

<div class="conv-eyebrow"><span class="eyebrow-mark">◆</span> convenção <b>#1</b></div>

# INTEGRATION <span class="conv-glyph g g-a">·</span> <span class="conv-star">*</span>

<div class="conv-rule">
  <span class="conv-rule-block" />
  <span class="conv-rule-line" />
  <span class="conv-rule-tail">um fornecedor · um módulo</span>
</div>

<div class="conv-grid">

<div class="conv-left">

<p class="conv-lede">Todo serviço externo vira <b>módulo próprio</b>. Mesmo se for só um SDK e três chamadas — ele tem casa.</p>

<p class="conv-aside"><i>nenhum domínio importa fornecedor direto. quem fala com o mundo lá fora vive sozinho na sua pasta.</i></p>

</div>

<div class="conv-right">

<div class="conv-ns-tag">namespace Shop\Integration\*</div>

```text {*}{class:'!text-[0.78rem]'}
app-modules/
├── integration-stripe/     → Shop\IntegrationStripe
├── integration-paypal/     → Shop\IntegrationPaypal
├── integration-correios/   → Shop\IntegrationCorreios
├── integration-twilio/     → Shop\IntegrationTwilio
├── integration-slack/      → Shop\IntegrationSlack
└── integration-github/     → Shop\IntegrationGithub
```

<div class="conv-count">6 fornecedores · 6 módulos · 0 acoplamento</div>

</div>

</div>

<div class="conv-tail">
1 fornecedor = 1 módulo. <b>Quebrou amanhã?</b> Você sabe <span class="g g-b">onde</span>.
</div>

<style>
.brutalist-content { padding-top: 0.3rem; }

.brutalist-content :deep(h1) {
  font-size: 4.6rem;
  line-height: 0.92;
  margin: 0.1rem 0 0.4rem;
  letter-spacing: -0.01em;
}
.conv-glyph {
  color: var(--accent-blue);
  margin: 0 0.15em;
  font-weight: 900;
}
.conv-star {
  color: var(--accent-blue);
  text-shadow: 0 0 22px rgba(96, 165, 250, 0.45);
  font-weight: 900;
  margin-left: 0.05em;
}

.conv-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1rem;
  color: #b9b3a9;
  margin-bottom: 0.2rem;
  animation: slide-up 0.5s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.2s;
}
.conv-eyebrow .eyebrow-mark { color: var(--red); font-size: 0.7rem; }
.conv-eyebrow b { color: var(--bone); font-style: normal; font-family: var(--font-mono); }

.conv-rule {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin: 0.4rem 0 0.9rem;
  animation: slide-up 0.55s cubic-bezier(0.2, 0.7, 0.2, 1) both;
  animation-delay: 0.55s;
}
.conv-rule-block {
  width: 38px;
  height: 9px;
  background: var(--accent-blue);
  box-shadow: 0 0 20px rgba(96, 165, 250, 0.45);
}
.conv-rule-line {
  flex: 0 0 140px;
  height: 2px;
  background: linear-gradient(to right, var(--accent-blue), transparent);
}
.conv-rule-tail {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--dim);
}

.conv-grid {
  display: grid;
  grid-template-columns: 1fr 1.05fr;
  gap: 2.2rem;
  align-items: start;
  margin-top: 0.4rem;
}

.conv-left { padding-top: 0.4rem; }
.conv-lede {
  font-family: var(--font-mono);
  font-size: 1.05rem;
  line-height: 1.55;
  color: #c8c2b6;
  margin: 0 0 0.9rem;
}
.conv-lede b { color: var(--bone); }
.conv-aside {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.05rem;
  color: var(--dim);
  line-height: 1.45;
  margin: 0;
  max-width: 26ch;
}

.conv-right {
  position: relative;
  padding: 1rem 1.1rem 0.8rem;
  border: 1px solid rgba(96, 165, 250, 0.22);
  border-left: 3px solid var(--accent-blue);
  border-radius: 3px;
  background: linear-gradient(180deg, rgba(20,20,24,0.6), rgba(10,10,12,0.78));
}
.conv-ns-tag {
  font-family: var(--font-mono);
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent-blue);
  font-weight: 700;
  margin-bottom: 0.45rem;
}
.conv-right :deep(pre) {
  background: transparent !important;
  border: none !important;
  margin: 0;
  padding: 0;
}
.conv-right :deep(.shiki) { background: transparent !important; }
.conv-count {
  margin-top: 0.6rem;
  font-family: var(--font-mono);
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--dim);
}

.conv-tail {
  margin-top: 1.4rem;
  padding-top: 0.7rem;
  border-top: 1px solid var(--rule);
  font-family: var(--font-mono);
  font-size: 0.9rem;
  color: #b9b3a9;
  letter-spacing: 0.01em;
}
.conv-tail b { color: var(--bone); }
</style>

<!--
"Convenção número um — e antes que alguém grite no chat: essas não são regras de modularização. São as MINHAS. Funcionam pro meu time. Talvez encaixem no seu, talvez não."

"Primeira: todo serviço externo vira módulo próprio. Stripe? `integration-stripe`. Correios? `integration-correios`. Slack pra alertas? `integration-slack`. Mesmo que seja só um SDK e três chamadas — ele tem casa."

"Por quê? Porque fornecedor quebra. SDK lança breaking change. Endpoint deprecia. Quando isso acontecer — e vai acontecer — você sabe onde ir. Você não vai sair caçando `Stripe::charge` em 30 arquivos pelo projeto."

"E o domínio nunca importa o fornecedor direto. O módulo `sales` não conhece Stripe. Ele dispara um evento. Quem ouve é `integration-stripe`. Trocou de gateway? Mexe num módulo. Só."

[transição] "Próxima convenção."
-->
