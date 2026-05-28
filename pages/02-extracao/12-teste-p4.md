---
layout: deletion-test-modular
transition: none
metaNumber: "20"
metaSection: "EXTRAÇÃO"
metaSubtitle: "teste da deleção"
metaPhase: red
metaRight: "Q4 · FRAMEWORK"
---

# O Teste da Deleção™ <span>— Pergunta 4 · <span class="g g-c">framework</span></span>

::questions::

<!-- Pergunta 1: já passou (faded) -->
<div class="p-2.5 bg-green-900/10 rounded border border-green-500/15 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 1</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1 opacity-70">Listar todos os arquivos?</div>
</div>

<!-- Pergunta 2: já passou (faded) -->
<div class="p-2.5 bg-green-900/10 rounded border border-green-500/15 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 2</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1 opacity-70">Quanto do sistema quebra?</div>
</div>

<!-- Pergunta 3: já passou (faded) -->
<div class="p-2.5 bg-green-900/10 rounded border border-green-500/15 opacity-40">
  <div class="flex items-center justify-between">
    <span class="text-green-400 font-bold text-[10px] uppercase tracking-wider">Pergunta 3</span>
    <span class="text-green-400 font-bold text-sm">✓</span>
  </div>
  <div class="text-sm mt-1 opacity-70">Arquivo usado por outra feature?</div>
</div>

<!-- Pergunta 4: foco -->
<div v-click="1" class="p-2.5 bg-purple-900/20 rounded border border-purple-500/30">
  <div class="flex items-center justify-between">
    <span class="text-purple-300 font-bold text-[10px] uppercase tracking-wider">Pergunta 4</span>
    <span v-click="3" class="text-red-400 font-bold text-sm">✘</span>
  </div>
  <div class="text-sm mt-1">Apagar o módulo apaga <b class="text-purple-200">TUDO</b>?</div>
  <div v-click="3" class="text-[10px] text-red-300/70 mt-1">O framework ainda aponta pra ele.</div>
</div>

<!-- Progresso -->
<div v-click="3" class="mt-2 p-2.5 bg-red-900/25 rounded-lg border-2 border-red-500/40 text-center">
  <div class="flex justify-center gap-3 text-lg">
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
    <span class="text-green-400">✓</span>
    <span class="text-red-400">✘</span>
  </div>
</div>

::visual::

<!-- ============================== -->
<!-- VISUAL 1: rm + route:list      -->
<!-- ============================== -->
<div v-click="[1, 2]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-purple-300 mb-3">Tudo passou. Eu deleto o módulo, então.</div>
  <div class="font-mono text-[11px] leading-[1.7] p-3 bg-black/40 rounded border border-purple-500/20">
    <div><span class="text-red-400">$</span> <span class="opacity-80">rm -rf app/Modules/Payment</span></div>
    <div class="opacity-50">&nbsp;</div>
    <div><span class="text-red-400">$</span> <span class="opacity-80">php artisan route:list</span></div>
  </div>
  <div class="mt-3 text-xs opacity-60">Deveria rodar liso, né?</div>
</div>

<!-- ============================== -->
<!-- VISUAL 2: o erro                -->
<!-- ============================== -->
<div v-click="[2, 3]" class="absolute inset-0 flex flex-col justify-center overflow-hidden">
  <div class="text-xs font-bold text-red-400 mb-3">Mas aí vem o tapa:</div>
  <div class="font-mono text-[11px] leading-[1.7] p-3 bg-black/50 rounded border border-red-500/30">
    <div><span class="text-red-400">$</span> <span class="opacity-70">php artisan route:list</span></div>
    <div class="opacity-50">&nbsp;</div>
    <div class="text-red-400">❯ Error: Class</div>
    <div class="text-red-300 ml-3">"App\Modules\Payment\PaymentServiceProvider"</div>
    <div class="text-red-400">  not found.</div>
  </div>
  <div class="mt-3 p-2.5 bg-gray-900/60 rounded border border-yellow-500/30">
    <div class="text-[10px] text-yellow-300 uppercase tracking-wider mb-1">bootstrap/providers.php</div>
    <div class="font-mono text-[11px]">
      <div class="opacity-60">return [</div>
      <div class="opacity-60">&nbsp;&nbsp;App\Providers\AppServiceProvider::class,</div>
      <div class="bg-red-500/15 text-red-300 rounded px-1 -mx-0.5">&nbsp;&nbsp;App\Modules\Payment\PaymentServiceProvider::class,</div>
      <div class="opacity-60">];</div>
    </div>
  </div>
</div>

<!-- ============================== -->
<!-- VISUAL 3: O diagnóstico        -->
<!-- ============================== -->
<div v-click="3" class="absolute inset-0 flex flex-col items-center justify-center overflow-hidden">
  <div class="text-5xl font-black text-red-500/70 tracking-wider">QUASE</div>
  <div class="mt-5 p-4 bg-purple-900/25 rounded border border-purple-500/30 text-sm max-w-lg text-center">
    Você apagou o módulo.<br>
    <b class="text-purple-200">O framework ainda aponta pra ele.</b>
  </div>
  <div class="mt-4 text-xs opacity-50">Q4 falhou. Falta o último passo.</div>
</div>

<!--
[sem click — P1, P2 e P3 já ✓]
"Recapitulando: três perguntas passaram. Achei os arquivos, deletei sem quebrar nada, isolei o que era de todos. Tá pronto, né? Vou deletar o módulo Payment e o app continua rodando."

[click 1 — Pergunta 4 + terminal rm + route:list]
"rm -rf app/Modules/Payment. Pronto. Sumiu. Roda um php artisan route:list só pra confirmar que tá tudo certo."

[click 2 — erro + providers.php highlight]
"E aí vem o tapa: 'Class App\Modules\Payment\PaymentServiceProvider not found'. Por quê? Porque eu deletei a pasta, mas no bootstrap/providers.php ainda tem uma linha registrando o ServiceProvider desse módulo. O framework não sabe que ele foi embora."

[click 3 — ✘ + QUASE + diagnóstico]
"Você apagou o módulo. O framework ainda aponta pra ele. Q4 falhou — não por culpa do meu boundary, mas porque o Laravel exige registro manual em N lugares pra cada módulo existir. Falta um último passo."
-->
