---
layout: split-compare
---

# O antes e depois

::before::

```text
app/
└── 487 arquivos PHP
    19 pastas por tipo técnico
    0 boundaries
    0 glossários
```

<div class="mt-4 p-3 bg-red-900/30 rounded border border-red-500/30 text-sm text-center">
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

<div class="mt-4 p-3 bg-green-900/30 rounded border border-green-500/30 text-sm text-center">
"Cada módulo me diz o que faz."
</div>

</v-click>

<!--
"487 arquivos numa pasta monolítica. Hoje: 312 no core e 847 distribuídos em 10 módulos. Cada módulo tem seu glossário, seus testes, seu namespace. E o mais importante: quando eu abro qualquer módulo, eu sei o que ele faz em 30 segundos."
-->
