# CONTEXT.md — Modular Talk

Domain language and key decisions for this presentation project.

## Glossary

### Talk concepts

- **Legadão**: The monolithic Laravel project used as the opening hook. A fictional ecommerce with 487 PHP files in 19 directories organized by technical type. NOT a real project name — it's the colloquial term for "legacy mess" used in the narrative.

- **Organização por tipo técnico**: The anti-pattern the talk argues against. Grouping files by what they ARE (Models/, Services/, Jobs/) instead of what they DO. The Laravel default that `artisan make:*` enforces.

- **Boundary**: The natural separation between groups of code that don't know about each other's existence. Found via the Deletion Test.

- **Teste da Deleção™**: The talk's framework for finding boundaries. Three questions: (1) Can you list all files for a feature? (2) How much breaks if you delete them? (3) Are any used by other features?

- **Extração**: The process of moving code from a monolithic `app/` into isolated modules. The talk distinguishes "extração conceitual" (understanding WHAT to extract) from "extração técnica" (HOW to extract with tooling).

- **Core message**: "Não existe padrão certo. Existe o que encaixa pro seu time." — folder structure (flat, clean arch, DDD, Laravel default) is cosmetic. What matters is the boundary and unidirectional dependencies.

### Module names (ecommerce example)

- **sales**: Orders, items, status. The top layer. Depends on nobody.
- **payment**: Stripe, PIX, boleto. Listens to `OrderPlaced`. Depends on sales.
- **fulfillment**: Stock, shipping, tracking. Listens to `PaymentConfirmed`. Depends on payment.
- **Identity (IAM)**: External credentials — Stripe keys, Correios tokens, OAuth clients. NOT the User model.
- **Integration-\***: One module per external system. `integration-stripe`, `integration-correios`, `integration-slack`.
- **Panel**: Filament panels as modules. `panel-admin`, `panel-app`, `panel-guest`.

### Events (boundary contracts)

- **OrderPlaced**: Fired by sales when an order is created. Payment listens.
- **PaymentConfirmed**: Fired by payment when charge succeeds. Fulfillment listens.

### Key decisions

- **"Quem armazena é o dono"**: When a model causes circular dependency, it belongs to the module that STORES the data, not the one that PRODUCES it. Example: `PaymentTransaction` lives in sales (not payment) because `Order->transactions()` is a sales relationship.

- **Aditiva-depois-destrutiva**: When extracting, add the new code path first (coexisting with the old), then remove the old one. Never do both at once — risk of duplicate side effects (e.g., charging a customer twice).

- **Feature flags keep old prefixes**: Pennant stores flag names in the database. Renaming requires data migration across all tenants. Pragmatic decision: aesthetic inconsistency < production risk. `ShopFreeShipping` stays even though it now belongs to fulfillment.

## Narrative arc

```
00-intro     → Conference ritual: cover, whoami, agenda
01-abertura  → Shared pain: "quem já mexeu num legadão?" + folder stepper + meme + emotional turn
02-extracao  → Conceptual: boundaries, Deletion Test, shop case, 4 folder structures (core message)
03-implementacao → Technical: internachi/modular, before/after code, errors intercalated, 3 patterns
04-fechamento → Numbers, 4 rules, CTA "roda tree app/ amanhã"
```

## 4 rules (closing)

1. "Extraia responsabilidades, não reorganize pastas."
2. "Módulos se comunicam por EVENTOS, não por imports."
3. "Comece pelo módulo que mais DÓI."
4. "Documente as decisões, não o código."
