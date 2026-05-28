---
layout: brutalist-base
metaNumber: "30"
metaSection: "IMPLEMENTAÇÃO"
metaSubtitle: "padrões que emergem"
contentAlign: "top"
---

# Padrões que <span class="g g-c">emergiram</span>

<v-clicks>

<div class="grid grid-cols-3 gap-4 mt-4">

<div class="p-4 rounded" style="background: rgba(96, 165, 250, 0.08); border: 1px solid rgba(96, 165, 250, 0.3);">
  <div class="font-bold text-lg mb-2" style="color: var(--accent-blue);">Identity (IAM)</div>
  <div class="text-sm" style="opacity: 0.85;">
    Como o sistema se identifica para <span style="color: var(--accent-orange);">outros sistemas</span>.<br>
    <span style="color: var(--accent-orange);">Não é User</span> — é credenciais externas.<br>
    <span class="mt-2 block" style="opacity: 0.6;">Chaves do Stripe, tokens do Correios, OAuth clients</span>
  </div>
</div>

<div class="p-4 rounded" style="background: rgba(255, 165, 58, 0.08); border: 1px solid rgba(255, 165, 58, 0.3);">
  <div class="font-bold text-lg mb-2" style="color: var(--accent-orange);">Integration-*</div>
  <div class="text-sm" style="opacity: 0.85;">
    Um módulo por sistema externo.<br>
    <span style="color: var(--accent-orange);">Adaptador isolado</span> — se trocar Stripe por PagSeguro, só um módulo muda.<br>
    <span class="mt-2 block" style="opacity: 0.6;">integration-stripe, integration-correios, integration-slack</span>
  </div>
</div>

<div class="p-4 rounded" style="background: rgba(192, 132, 252, 0.08); border: 1px solid rgba(192, 132, 252, 0.3);">
  <div class="font-bold text-lg mb-2" style="color: var(--accent-purple);"><span class="g g-c">Panel</span></div>
  <div class="text-sm" style="opacity: 0.85;">
    Onde moram os items do <span style="color: var(--accent-orange);">Filament</span>.<br>
    Cada panel é um módulo separado.<br>
    <span class="mt-2 block" style="opacity: 0.6;">panel-admin, panel-app, panel-guest</span>
  </div>
</div>

</div>

</v-clicks>

<v-click>

<div class="mt-6 text-center text-sm" style="opacity: 0.6;">
Você não precisa planejar esses módulos. Eles emergem quando você aplica o Teste da Deleção.
</div>

</v-click>

<!--
"Quando você modulariza, alguns padrões aparecem sozinhos. Identity: credenciais externas não são parte do User — chave do Stripe e token do Correios merecem um módulo próprio. Integration: um módulo por sistema externo, assim se trocar o Stripe por PagSeguro, só um módulo muda. Panel: se você usa Filament, cada panel (admin, app, guest) vira um módulo separado."

"Você não precisa planejar esses módulos de antemão. Eles emergem naturalmente quando você aplica o Teste da Deleção."
-->
