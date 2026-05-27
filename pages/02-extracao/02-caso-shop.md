---

# O caso real: o módulo `shop` de 100+ arquivos

<div class="grid grid-cols-2 gap-6">
<div>

```text {all|2-4|5-7|8-10|11-14|all}
app-modules/shop/
├── Cart/
│   ├── Models/
│   └── Services/
├── Catalog/
│   ├── Models/
│   └── Services/
├── Checkout/
│   ├── Services/
│   └── Jobs/
├── Orders/
│   ├── Models/
│   └── Notifications/
├── Payment/
│   ├── Gateways/
│   └── Jobs/
└── Shipping/
    ├── Carriers/
    └── Services/
```

</div>
<div>

<v-click>

<div class="text-sm">

**100+ arquivos. 3 responsabilidades misturadas:**

</div>

<v-clicks>

<div class="mt-2 p-2 bg-blue-900/30 rounded border border-blue-500/30 text-sm">
<span class="text-blue-400 font-bold">1. CATÁLOGO</span><br>
produtos, categorias, preços, busca (dados)
</div>

<div class="mt-2 p-2 bg-purple-900/30 rounded border border-purple-500/30 text-sm">
<span class="text-purple-400 font-bold">2. TRANSAÇÃO</span><br>
carrinho, checkout, pagamento (fluxo de compra)
</div>

<div class="mt-2 p-2 bg-green-900/30 rounded border border-green-500/30 text-sm">
<span class="text-green-400 font-bold">3. OPERAÇÃO</span><br>
pedidos, estoque, envio (pós-venda)
</div>

</v-clicks>

</v-click>

</div>
</div>

<!--
"No ecommerce, a gente já tinha modularizado. Mas nosso módulo shop tinha virado uma lixeira. 100+ arquivos fazendo 3 coisas completamente diferentes. Catálogo de produtos e processamento de pagamento estavam no mesmo módulo. Isso é tipo botar a lavanderia dentro da cozinha porque as duas usam água."
-->

---

# A pergunta que revela os boundaries

<div class="grid grid-cols-2 gap-8 mt-4">
<div>

<v-click>

<div class="p-4 bg-gray-800/50 rounded-lg border border-gray-600/30">

**"Se eu deletar o catálogo, o checkout quebra?"**

<div class="mt-2 text-green-400 font-bold text-xl">NÃO.</div>
<div class="text-sm opacity-70">
O carrinho já tem snapshot dos produtos<br>
(preço, nome, SKU). Checkout não consulta<br>
o catálogo na hora de finalizar.
</div>

</div>

</v-click>

</div>
<div>

<v-click>

<div class="p-4 bg-gray-800/50 rounded-lg border border-gray-600/30">

**"Se eu deletar o checkout, o catálogo quebra?"**

<div class="mt-2 text-green-400 font-bold text-xl">NÃO.</div>
<div class="text-sm opacity-70">
O catálogo exibe produtos.<br>
Ele não sabe e não precisa saber<br>
como o checkout funciona.
</div>

</div>

</v-click>

</div>
</div>

<v-click>

<div class="mt-8 p-4 bg-yellow-900/40 rounded-lg border-2 border-yellow-500/50 text-center text-xl font-bold">
Se dois grupos de código não sabem da existência<br>
um do outro... eles não pertencem ao mesmo módulo.
</div>

</v-click>

<!--
"Essa é a regra de ouro: se dois pedaços de código não sabem da existência um do outro, eles não deveriam morar juntos. Catálogo não importa nenhuma classe de checkout. Checkout não importa nenhuma classe de catálogo. Eles se comunicam por um EVENTO — OrderPlaced. Achei meu boundary."
-->
