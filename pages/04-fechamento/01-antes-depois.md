---
layout: split-modular
metaNumber: "23"
metaSection: "FECHAMENTO"
metaSubtitle: "antes e depois"
beforeLabel: "ANTES"
afterLabel: "DEPOIS"
---

# O <span class="g g-a">antes</span> e depois

::before::

```text
app/
└── 487 arquivos PHP
    19 pastas por tipo técnico
    0 boundaries
    0 glossários
```

<div class="commentary commentary--before">
"O que esse sistema faz?"
</div>

::after::

```text
app/
└── 312 arquivos PHP (core)

app-modules/
└── 847 arquivos PHP
    10 módulos
    10 CONTEXT.md
    1 CONTEXT-MAP.md
    2.148 testes passando
```

<v-click>

<div class="commentary commentary--after">
"Cada módulo me diz o que faz."
</div>

</v-click>

<style scoped>
.commentary {
  margin-top: 0.8rem;
  padding: 0.55rem 0.75rem;
  border-radius: 3px;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.95rem;
  text-align: center;
  letter-spacing: 0.005em;
}
.commentary--before {
  background: rgba(255, 45, 32, 0.08);
  border: 1px solid rgba(255, 45, 32, 0.28);
  color: #f0c8c2;
}
.commentary--after {
  background: rgba(110, 231, 161, 0.08);
  border: 1px solid rgba(110, 231, 161, 0.28);
  color: #c8e7d3;
}
</style>

<!--
"487 arquivos numa pasta monolítica. Hoje: 312 no core e 847 distribuídos em 10 módulos. Cada módulo tem seu glossário, seus testes, seu namespace. E o mais importante: quando eu abro qualquer módulo, eu sei o que ele faz em 30 segundos."
-->
