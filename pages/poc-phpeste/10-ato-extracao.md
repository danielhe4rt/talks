---
layout: ph-act
act: "02"
eyebrow: ato 2 · teste da deleção
duration: ~22 min · do conceito ao framework
---

# Achar os boundaries.

Como achar os limites do seu código — sem reescrever nada.

<!--
"Então se organizar por tipo técnico é o problema... qual é a alternativa? Vamos aprender a encontrar os boundaries — os limites naturais do seu código."
-->

---
layout: ph-section
tone: sand
eyebrow: o método
hint: rodar no legadão
clicks: 1
---

# O Teste da Deleção

Pega uma funcionalidade. Imagina que você **deleta todos os arquivos dela**.

::content::

<div class="ph-grid" style="--cols: 3">
  <PhCard index="01" tag="listar" name="Você consegue listar todos os arquivos?" accent="yellow">
    <template #icon><mdi-format-list-checks /></template>
    Se precisa caçar em 8 pastas, o boundary não existe.
  </PhCard>
  <PhCard index="02" tag="quebra" name="Quanto do sistema quebra?" accent="orange">
    <template #icon><mdi-flash-alert-outline /></template>
    Cada import vindo de fora é um fio que arrebenta junto.
  </PhCard>
  <PhCard index="03" tag="compartilhado" name="Algum arquivo é usado por outra feature?" accent="crimson">
    <template #icon><mdi-share-variant-outline /></template>
    Se é de todo mundo, não é de ninguém.
  </PhCard>
</div>

<p class="ph-rule-text" v-click>vamos rodar esse teste no nosso legadão.</p>

<!--
"Eu chamo isso de Teste da Deleção. É simples: pega uma funcionalidade — tipo processamento de pagamento — e imagina que deleta TUDO que é dela. 3 perguntas. Se alguma falha, você tem um problema de boundary."

[click] "Vamos rodar esse teste no nosso legadão e ver o que acontece?"
-->
