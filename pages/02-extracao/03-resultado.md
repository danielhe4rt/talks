---

# O resultado: 3 módulos onde tinha 1

```mermaid {scale: 0.85}
flowchart TD
    subgraph L1["Layer 1 — Pedidos"]
        SALES["sales\n(pedidos, itens, status)"]
    end

    subgraph L2["Layer 2 — Pagamento"]
        PAY["payment\n(Stripe, PIX, boleto)"]
    end

    subgraph L3["Layer 3 — Entrega"]
        FULL["fulfillment\n(estoque, envio, rastreio)"]
    end

    SALES -->|"depende de"| PAY
    PAY -->|"depende de"| FULL

    style L1 fill:#1a365d,stroke:#3182ce,color:#fff
    style L2 fill:#234e52,stroke:#38b2ac,color:#fff
    style L3 fill:#44337a,stroke:#805ad5,color:#fff
    style SALES fill:#2b6cb0,stroke:#3182ce,color:#fff
    style PAY fill:#2c7a7b,stroke:#38b2ac,color:#fff
    style FULL fill:#553c9a,stroke:#805ad5,color:#fff
```

<v-click>

<div class="mt-2 flex justify-center gap-6 text-sm">
  <span class="text-green-400">✓ Unidirecional</span>
  <span class="text-green-400">✓ Cada módulo tem responsabilidade clara</span>
  <span class="text-green-400">✓ Boundaries definidos pelo Teste da Deleção</span>
</div>

</v-click>

<!--
"Saí de 1 módulo com 100+ arquivos pra 3 módulos com responsabilidade clara. E a chave é: a dependência é UNIDIRECIONAL. Payment depende de sales pra ler o pedido, mas sales NUNCA importa payment. Cada módulo sabe fazer a parte dele e só."

"Mais pra frente eu vou mostrar COMO esses módulos se comunicam na prática. Mas primeiro, vamos ver como eu fiz essa extração com código."
-->
