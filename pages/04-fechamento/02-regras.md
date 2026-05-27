---
layout: default
---

# 4 regras pra levar pra casa

<div class="mt-6 space-y-3">

<v-clicks>

<div class="p-4 bg-blue-900/30 rounded-lg border border-blue-500/30">
  <span class="text-blue-400 font-bold text-xl">1.</span>
  <span class="text-lg font-bold ml-2">Extraia responsabilidades, não reorganize pastas.</span>
  <div class="text-sm opacity-70 ml-8 mt-1">
    O boundary importa mais que a estrutura. Flat, Clean, DDD — tanto faz, desde que o módulo seja isolado.
  </div>
</div>

<div class="p-4 bg-green-900/30 rounded-lg border border-green-500/30">
  <span class="text-green-400 font-bold text-xl">2.</span>
  <span class="text-lg font-bold ml-2">Módulos se comunicam por EVENTOS, não por imports.</span>
  <div class="text-sm opacity-70 ml-8 mt-1">
    <code>event(new OrderPlaced())</code> e quem quiser que escute. Zero acoplamento direto.
  </div>
</div>

<div class="p-4 bg-yellow-900/30 rounded-lg border border-yellow-500/30">
  <span class="text-yellow-400 font-bold text-xl">3.</span>
  <span class="text-lg font-bold ml-2">Comece pelo módulo que mais DÓI.</span>
  <div class="text-sm opacity-70 ml-8 mt-1">
    Não modularize o projeto inteiro de uma vez. Encontre o que mais dói e extraia esse.
  </div>
</div>

<div class="p-4 bg-purple-900/30 rounded-lg border border-purple-500/30">
  <span class="text-purple-400 font-bold text-xl">4.</span>
  <span class="text-lg font-bold ml-2">Documente as decisões, não o código.</span>
  <div class="text-sm opacity-70 ml-8 mt-1">
    <code>CONTEXT.md</code> com glossário de domínio. ADRs pra decisões difíceis. Doc que o agente lê.
  </div>
</div>

</v-clicks>

</div>

<!--
"Quatro coisas pra levar pra casa. Uma: extraia responsabilidades, não reorganize pastas. Não importa se é flat, clean ou DDD — o que importa é que o módulo é isolado. Dois: eventos como fronteira. Módulos não chamam código de outros módulos — eles disparam eventos e quem quiser escuta. Três: comece pelo que mais dói. Não precisa modularizar tudo amanhã. Quatro: documente as decisões. CONTEXT.md com o glossário do domínio. Não é doc que ninguém lê — é doc que o agente lê."
-->
