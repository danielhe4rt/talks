---
layout: deletion-test-modular
transition: none
metaNumber: "24"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaPhase: green
metaRight: "Q4 · INTERNACHI"
---

# O Teste da Deleção™ <span>— 4 de 4.</span>

::questions::

<!-- Pergunta 1: passou -->
<div class="p-1.5 bg-green-900/15 rounded border border-green-500/25">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-[12px] mt-0.5">Listar todos os arquivos?</div>
  <div class="text-[9px] text-green-300/70 mt-0.5">Cada feature na sua pasta.</div>
</div>

<!-- Pergunta 2: passou -->
<div class="p-1.5 bg-green-900/15 rounded border border-green-500/25">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-[12px] mt-0.5">Quanto do sistema quebra?</div>
  <div class="text-[9px] text-green-300/70 mt-0.5">Nada. Eventos no lugar de imports.</div>
</div>

<!-- Pergunta 3: passou -->
<div class="p-1.5 bg-green-900/15 rounded border border-green-500/25">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-[12px] mt-0.5">Arquivo usado por outra feature?</div>
  <div class="text-[9px] text-green-300/70 mt-0.5">Compartilhado virou Gateway.</div>
</div>

<!-- Pergunta 4: agora passa -->
<div v-click="1" class="p-1.5 bg-green-900/15 rounded border border-green-500/25">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 4</span>
    <span v-click="2" class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-[12px] mt-0.5">Apagar apaga TUDO?</div>
  <div v-click="2" class="text-[9px] text-green-300/70 mt-0.5">Auto-discovery + módulo encapsulado.</div>
</div>

<!-- Progresso final -->
<div v-click="2" class="mt-1 p-1.5 bg-green-900/35 rounded-lg border-2 border-green-500/50 text-center">
  <div class="flex justify-center gap-3 text-base">
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
  </div>
</div>

::visual::

<!-- ============================== -->
<!-- VISUAL 1: rm -rf + roda OK     -->
<!-- ============================== -->
<div v-click="[1, 2]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-green-400 mb-3">Deleto Payment de novo. Agora com internachi:</div>
  <div class="font-mono text-[11px] leading-[1.7] p-3 bg-black/40 rounded border border-green-500/25">
    <div><span class="text-green-400">$</span> <span class="opacity-80">rm -rf app-modules/payment</span></div>
    <div><span class="text-green-400">$</span> <span class="opacity-80">php artisan modules:sync</span></div>
    <div class="opacity-50">&nbsp;</div>
    <div><span class="text-green-400">$</span> <span class="opacity-80">php artisan route:list</span></div>
    <div class="opacity-50">&nbsp;</div>
    <div class="text-green-300">  GET   /cart</div>
    <div class="text-green-300">  POST  /checkout</div>
    <div class="text-green-300">  GET   /catalog/{slug}</div>
    <div class="opacity-40">  ... (sem nada de payment)</div>
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 2: 4 de 4               -->
<!-- ============================== -->
<div v-click="2" class="absolute inset-0 flex flex-col items-center justify-center overflow-hidden">
  <div class="text-[10rem] font-black text-green-500/80 tracking-tight leading-none">4<span class="opacity-60">/</span>4</div>
  <div class="mt-4 flex gap-4">
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-green-400 text-2xl">✓</span>
    <span class="text-green-400 text-2xl">✓</span>
  </div>
  <div class="mt-5 max-w-md text-center text-sm opacity-80">
    O boundary <b class="text-green-300">sobrevive</b><br>
    até ao framework.
  </div>
</div>

<!--
[sem click — P1, P2 e P3 já ✓, P4 ainda em foco esperando]
"Beleza, instalei internachi, reorganizei o módulo, providers.php tá limpo. Hora de rodar o Teste da Deleção pela última vez."

[click 1 — Pergunta 4 + terminal rm + modules:sync + route:list passa]
"Mesmo comando de antes, com o novo caminho: rm -rf app-modules/payment. Rodo modules:sync pra Composer redescobrir os pacotes. Daí artisan route:list. Dessa vez? As rotas do app continuam, as de Payment somem junto com a pasta. Sem erro. Sem provider órfão."

[click 2 — ✓ + 4/4]
"Q4 passou. As quatro passaram. Pode apagar o módulo. O framework não chora. O boundary sobrevive até ao framework. É essa a régua. O resto é encanamento."
-->
