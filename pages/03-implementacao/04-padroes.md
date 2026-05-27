---

# Padrões que emergiram

<v-clicks>

<div class="grid grid-cols-3 gap-4 mt-4">

<div class="p-4 bg-blue-900/30 rounded-lg border border-blue-500/30">
  <div class="text-blue-400 font-bold text-lg mb-2">Identity (IAM)</div>
  <div class="text-sm opacity-80">
    Como o sistema se identifica para <span class="text-yellow-400">outros sistemas</span>.<br>
    <span class="text-yellow-400">Não é User</span> — é credenciais externas.<br>
    <span class="opacity-60 mt-2 block">Chaves do Stripe, tokens do Correios, OAuth clients</span>
  </div>
</div>

<div class="p-4 bg-orange-900/30 rounded-lg border border-orange-500/30">
  <div class="text-orange-400 font-bold text-lg mb-2">Integration-*</div>
  <div class="text-sm opacity-80">
    Um módulo por sistema externo.<br>
    <span class="text-yellow-400">Adaptador isolado</span> — se trocar Stripe por PagSeguro, só um módulo muda.<br>
    <span class="opacity-60 mt-2 block">integration-stripe, integration-correios, integration-slack</span>
  </div>
</div>

<div class="p-4 bg-purple-900/30 rounded-lg border border-purple-500/30">
  <div class="text-purple-400 font-bold text-lg mb-2">Panel</div>
  <div class="text-sm opacity-80">
    Onde moram os items do <span class="text-yellow-400">Filament</span>.<br>
    Cada panel é um módulo separado.<br>
    <span class="opacity-60 mt-2 block">panel-admin, panel-app, panel-guest</span>
  </div>
</div>

</div>

</v-clicks>

<v-click>

<div class="mt-6 text-center text-sm opacity-60">
Você não precisa planejar esses módulos. Eles emergem quando você aplica o Teste da Deleção.
</div>

</v-click>

<!--
"Quando você modulariza, alguns padrões aparecem sozinhos. Identity: credenciais externas não são parte do User — chave do Stripe e token do Correios merecem um módulo próprio. Integration: um módulo por sistema externo, assim se trocar o Stripe por PagSeguro, só um módulo muda. Panel: se você usa Filament, cada panel (admin, app, guest) vira um módulo separado."

"Você não precisa planejar esses módulos de antemão. Eles emergem naturalmente quando você aplica o Teste da Deleção."
-->
