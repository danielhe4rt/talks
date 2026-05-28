---
layout: statement-modular
metaNumber: "25"
metaSection: "FECHAMENTO"
metaSubtitle: "amanhã de manhã"
eyebrow: "leve isso pra casa"
accent: "?"
---

# Amanhã<br>de manhã<span class="accent-glyph">.</span>

<div class="cta-cmd">

```bash
$ tree app/ -d -L 1
```

</div>

<div class="cta-prompt">
Olha pro resultado.<br>
Se pergunta:
</div>

<v-click>

<div class="cta-punch">
"Olhando só pra essa estrutura...<br>
eu sei o que meu sistema <span class="g g-a">FAZ?</span>"
</div>

</v-click>

<v-click>

<div class="cta-afterglow">
Se a resposta for não,<br>
você sabe por onde começar.
</div>

</v-click>

<div class="cta-thanks">
<span class="thanks-block" />
<span class="thanks-label">obrigado</span>
<span class="thanks-handle">@danielhe4rt</span>
</div>

<style scoped>
.accent-glyph { color: var(--red); }

.cta-cmd {
  margin: 0.4rem 0 1rem;
  max-width: 30rem;
}
.cta-cmd :deep(pre) {
  background: rgba(10, 10, 12, 0.7) !important;
  border: 1px solid rgba(255, 45, 32, 0.25);
  border-left: 3px solid var(--red);
  border-radius: 3px;
  padding: 0.6rem 0.9rem;
  font-size: 0.85rem;
  box-shadow: 0 0 22px rgba(255, 45, 32, 0.08);
}
.cta-cmd :deep(.shiki) { background: transparent !important; }

.cta-prompt {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.25rem;
  color: #c8c2b6;
  line-height: 1.45;
  margin-bottom: 0.7rem;
}

.cta-punch {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 1.4rem;
  line-height: 1.35;
  color: var(--bone);
  letter-spacing: 0.005em;
  margin: 0.4rem 0 0.6rem;
  padding-left: 0.85rem;
  border-left: 3px solid var(--accent-orange);
  position: relative;
}
.cta-punch::before {
  content: "";
  position: absolute;
  inset: 0 auto 0 0;
  width: 3px;
  box-shadow: 0 0 14px rgba(255, 165, 58, 0.5);
}

.cta-afterglow {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1.05rem;
  color: #b9b3a9;
  line-height: 1.5;
  margin-top: 0.5rem;
}

.cta-thanks {
  position: absolute;
  right: 2.6rem;
  bottom: 2rem;
  display: inline-flex;
  align-items: center;
  gap: 0.55rem;
  font-family: var(--font-mono);
}
.thanks-block {
  width: 22px;
  height: 8px;
  background: var(--red);
  box-shadow: 0 0 14px rgba(255, 45, 32, 0.45);
}
.thanks-label {
  font-weight: 700;
  font-size: 0.72rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: var(--red);
}
.thanks-handle {
  font-size: 0.72rem;
  letter-spacing: 0.18em;
  text-transform: lowercase;
  color: var(--dim);
}
</style>

<!--
"Amanhã, roda tree app/ no seu projeto. Olha pro resultado. Se você não consegue dizer o que o sistema faz olhando pra estrutura... agora você sabe que o problema tem solução. Obrigado."
-->
