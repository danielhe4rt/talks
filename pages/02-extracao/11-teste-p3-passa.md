---
layout: deletion-test-modular
transition: none
metaNumber: "19"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaPhase: green
metaRight: "Q3 · 3 DE 3"
---

# O Teste da Deleção™ <span>— 3 de 3</span>

::questions::

<!-- Pergunta 1: passou -->
<div class="p-2.5 bg-green-900/15 rounded border border-green-500/25">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1">Listar todos os arquivos?</div>
  <div class="text-[10px] text-green-300/70 mt-1">Cada feature na sua pasta.</div>
</div>

<!-- Pergunta 2: passou -->
<div v-click="1" class="p-2.5 bg-green-900/15 rounded border border-green-500/25">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1">Quanto do sistema quebra?</div>
  <div class="text-[10px] text-green-300/70 mt-1">Nada. Eventos no lugar de imports.</div>
</div>

<!-- Pergunta 3: agora passa -->
<div v-click="2" class="p-2.5 bg-green-900/15 rounded border border-green-500/25">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span v-click="3" class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1">Arquivo usado por outra feature?</div>
  <div v-click="3" class="text-[10px] text-green-300/70 mt-1">Não. O que era compartilhado virou Gateway.</div>
</div>

<!-- Progresso -->
<div v-click="3" class="mt-2 p-2.5 bg-green-900/30 rounded-lg border-2 border-green-500/40 text-center">
  <div class="flex justify-center gap-3 text-lg">
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
  </div>
</div>

::visual::

<!-- ============================== -->
<!-- VISUAL 1: 3 módulos isolados   -->
<!-- ============================== -->
<div v-click="[1, 3]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-green-400 mb-5">Cada módulo passa o teste sozinho:</div>
  <div class="grid grid-cols-3 gap-3">
    <div class="p-3 bg-green-900/15 rounded border border-green-500/25">
      <div class="text-[10px] text-gray-400 uppercase tracking-wider mb-1">Modules/</div>
      <div class="text-green-300 font-mono text-sm font-bold mb-2">Payment</div>
      <div class="space-y-1 text-[11px] font-mono opacity-80">
        <div>✓ listo</div>
        <div>✓ não quebra</div>
        <div>✓ ninguém depende</div>
      </div>
    </div>
    <div class="p-3 bg-green-900/15 rounded border border-green-500/25">
      <div class="text-[10px] text-gray-400 uppercase tracking-wider mb-1">Modules/</div>
      <div class="text-green-300 font-mono text-sm font-bold mb-2">Gateway</div>
      <div class="space-y-1 text-[11px] font-mono opacity-80">
        <div>✓ listo</div>
        <div>✓ não quebra</div>
        <div>✓ contrato explícito</div>
      </div>
    </div>
    <div class="p-3 bg-green-900/15 rounded border border-green-500/25">
      <div class="text-[10px] text-gray-400 uppercase tracking-wider mb-1">Modules/</div>
      <div class="text-green-300 font-mono text-sm font-bold mb-2">Subscriptions</div>
      <div class="space-y-1 text-[11px] font-mono opacity-80">
        <div>✓ listo</div>
        <div>✓ não quebra</div>
        <div>✓ usa Gateway</div>
      </div>
    </div>
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 2: 3 de 3 + rug-pull P4 -->
<!-- ============================== -->
<div v-click="3" class="absolute inset-0 flex flex-col items-center justify-center overflow-hidden">
  <div class="text-[10rem] font-black text-green-500/80 tracking-tight leading-none">3<span class="opacity-60">/</span>3</div>
  <div class="mt-4 flex gap-4">
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-green-400 text-2xl">✓</span>
  </div>
  <div class="mt-5 max-w-lg text-center text-sm opacity-80">
    <b class="text-green-300">3 / 3 — passou.</b> <span class="text-purple-300">✶</span> Mas espera.<br>
    Tem uma <b class="text-purple-300">4ª pergunta</b>. Você só faz quando tem módulos.
  </div>
</div>

<!--
[sem click — P1 já ✓]
"Recapitulando: Q1 passou quando agrupei por feature."

[click 1 — P2 ✓]
"Q2 passou quando troquei imports por eventos."

[click 2 — P3 em foco]
"E Q3?"

[click 3 — P3 ✓ + 3/3 + rug-pull P4]
"Q3 passou quando o arquivo que servia 3 features virou um módulo próprio: Gateway. Três de três. O teste passou."

[pausa de meio segundo, deixa a plateia respirar]

"Mas… espera. Tem uma quarta pergunta. Eu nunca falei dela antes porque não dava pra fazer: ela só existe quando você tem módulos de verdade. Agora a gente tem. Bora rodar a P4."
-->
