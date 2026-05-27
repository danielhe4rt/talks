---
layout: section
---

# Encontrando Boundaries
## O Teste da Deleção

<!--
"Então se organizar por tipo técnico é o problema... qual é a alternativa? Vamos aprender a encontrar os boundaries — os limites naturais do seu código."
-->

---

# O Teste da Deleção&trade;

<div class="text-lg">

Pega uma funcionalidade do seu sistema. <br>
Imagina que você deleta **TODOS** os arquivos dela.

</div>

<v-clicks>

<div class="mt-6 p-4 bg-gray-800/50 rounded-lg border border-gray-600/30">
<span class="text-yellow-400 font-bold">Pergunta 1:</span> Você consegue <span class="text-yellow-400">listar todos os arquivos</span>?<br>
<span class="opacity-60 ml-4">→ Se não consegue, você não tem boundary.</span>
</div>

<div class="mt-3 p-4 bg-gray-800/50 rounded-lg border border-gray-600/30">
<span class="text-orange-400 font-bold">Pergunta 2:</span> Quanto do sistema <span class="text-orange-400">quebra</span>?<br>
<span class="opacity-60 ml-4">→ Se quebra TUDO, seu código é um bolo. Não um sistema modular.</span>
</div>

<div class="mt-3 p-4 bg-gray-800/50 rounded-lg border border-gray-600/30">
<span class="text-red-400 font-bold">Pergunta 3:</span> Algum desses arquivos é <span class="text-red-400">usado por outra feature</span>?<br>
<span class="opacity-60 ml-4">→ Se sim, ali tem um acoplamento pra resolver.</span>
</div>

</v-clicks>

<!--
"Eu chamo isso de Teste da Deleção. Pega o processamento de pedido do exemplo anterior. Se eu deletar tudo que é de pedido — service, job, model, enum, evento, listener, observer — o resto do sistema continua funcionando? Se a resposta é 'não sei', você tem um problema. Se a resposta é 'quebra tudo', você tem um GRANDE problema."
-->
