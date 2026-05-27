---
layout: section
---

# Encontrando Boundaries
## O Teste da Deleção

<!--
"Então se organizar por tipo técnico é o problema... qual é a alternativa? Vamos aprender a encontrar os boundaries — os limites naturais do seu código."
-->

---

# O Teste da Deleção™

<div class="text-lg mt-4">

Pega uma funcionalidade do seu sistema. <br>
Imagina que você deleta **TODOS** os arquivos dela.

</div>

<v-clicks>

<div class="mt-8 p-4 bg-yellow-900/20 rounded-lg border border-yellow-500/30">
<span class="text-yellow-400 font-bold text-lg">1.</span> Você consegue <span class="text-yellow-400 font-bold">listar todos os arquivos</span>?
</div>

<div class="mt-3 p-4 bg-orange-900/20 rounded-lg border border-orange-500/30">
<span class="text-orange-400 font-bold text-lg">2.</span> Quanto do sistema <span class="text-orange-400 font-bold">quebra</span>?
</div>

<div class="mt-3 p-4 bg-red-900/20 rounded-lg border border-red-500/30">
<span class="text-red-400 font-bold text-lg">3.</span> Algum desses arquivos é <span class="text-red-400 font-bold">usado por outra feature</span>?
</div>

</v-clicks>

<v-click>

<div class="mt-6 text-center text-lg opacity-70">
Vamos rodar esse teste no nosso legadão?
</div>

</v-click>

<!--
"Eu chamo isso de Teste da Deleção. É simples: pega uma funcionalidade — tipo processamento de pagamento — e imagina que deleta TUDO que é dela. 3 perguntas. Se alguma falha, você tem um problema de boundary."

[click] "Vamos rodar esse teste no nosso legadão e ver o que acontece?"
-->
