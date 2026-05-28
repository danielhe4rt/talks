---
transition: fade
---

# Comunicação entre módulos

<EventFlow />

<!--
"Antes de eu mostrar o código, deixa eu te mostrar o CONCEITO visualmente."

[interativo — speaker alterna entre os modos e deleta Payment]

"No modo acoplado, Checkout importa Payment diretamente. Olha o código embaixo: use Payment\ProcessPayment. Se eu deletar Payment... boom. Checkout explode. Fatal Error."

[toggle para desacoplado]

"Agora no modo desacoplado. Checkout não importa Payment. Checkout dispara um EVENTO — OrderPlaced. Olha as ondas: é um broadcast. Checkout tá gritando pra quem quiser ouvir. Payment escuta."

[deleta Payment no modo desacoplado]

"Deletei Payment. E o Checkout? Sistema intacto. O evento ainda dispara, mas ninguém tá escutando. E tá tudo bem. Checkout não sabe e não precisa saber que Payment existia."

"Isso é a diferença entre import direto e comunicação por evento. Vamos ver como fica no código."
-->
