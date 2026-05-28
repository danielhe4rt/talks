---
layout: brutalist-base
metaNumber: "18"
metaSection: "EXTRAÇÃO"
metaSubtitle: "o resultado"
metaRight: "1 → 3 módulos"
contentAlign: "top"
---

<TitleBlock
  eyebrow="depois da extração"
  outlined="3 MÓDULOS"
  solid="ONDE TINHA 1"
  accent="."
  tail="dependência unidirecional"
  size="small"
/>

<div class="result-mermaid">

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

</div>

<v-click>

<div class="result-checks">
  <span class="result-check"><span class="result-check-mark">✓</span>Unidirecional</span>
  <span class="result-check"><span class="result-check-mark">✓</span>Cada módulo tem responsabilidade clara</span>
  <span class="result-check"><span class="result-check-mark">✓</span>Boundaries definidos pelo Teste da Deleção</span>
</div>

</v-click>

<style>
.result-mermaid {
  margin-top: 0.5rem;
  flex: 1;
  min-height: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.result-mermaid :deep(.slidev-mermaid),
.result-mermaid :deep(svg) {
  max-height: 100%;
}
.result-checks {
  display: flex;
  justify-content: center;
  gap: 1.6rem;
  margin-top: 0.6rem;
  font-family: var(--font-mono);
  font-size: 0.78rem;
  color: #c8c2b6;
  letter-spacing: 0.02em;
}
.result-check {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
}
.result-check-mark {
  color: var(--accent-green);
  font-weight: 700;
}
</style>

<!--
"Saí de 1 módulo com 100+ arquivos pra 3 módulos com responsabilidade clara. E a chave é: a dependência é UNIDIRECIONAL. Payment depende de sales pra ler o pedido, mas sales NUNCA importa payment. Cada módulo sabe fazer a parte dele e só."

"Mais pra frente eu vou mostrar COMO esses módulos se comunicam na prática. Mas primeiro, vamos ver como eu fiz essa extração com código."
-->
