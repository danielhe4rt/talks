---
layout: section-modular
actNumber: "03"
actLabel: "ato 03 de 04"
eyebrow: "ato 3 · implementação"
outlined: "internachi/"
solid: "modular"
accent: "."
tail: "~15 min · técnico"
---

## na prática

<!--
"Beleza, achei os boundaries. Mas como eu implemento isso em Laravel? A resposta é o internachi/modular."
-->

---
layout: brutalist-base
metaNumber: "17"
metaSection: "IMPLEMENTAÇÃO"
metaSubtitle: "setup em 2 comandos"
contentAlign: "top"
---

# Setup em <span class="g g-a">2 comandos</span>

<div class="grid grid-cols-2 gap-6 mt-4">
<div>

```bash
# Instalar
composer require internachi/modular

# Criar um módulo
php artisan make:module payment
```

</div>
<div>

<v-click>

```text
app-modules/
└── payment/
    ├── composer.json
    ├── src/
    │   └── Providers/
    │       └── PaymentServiceProvider.php
    ├── config/
    ├── database/
    │   ├── factories/
    │   ├── migrations/
    │   └── seeders/
    ├── routes/
    ├── resources/
    └── tests/
```

</v-click>

</div>
</div>

<v-click>

<div class="mt-4 p-3 rounded border" style="background: rgba(110, 231, 161, 0.06); border-color: rgba(110, 231, 161, 0.25); text-align: center;">
Cada módulo é um <span style="color: var(--accent-green); font-weight: 700;">mini-package Laravel</span> com namespace próprio.
</div>

</v-click>

<!--
"Dois comandos. composer require e php artisan make:module. Pronto, você tem um módulo com estrutura completa — service provider, config, migrations, tests. Cada módulo é basicamente um mini-package Laravel com namespace próprio."
-->

---
layout: brutalist-base
metaNumber: "18"
metaSection: "IMPLEMENTAÇÃO"
metaSubtitle: "composer.json do módulo"
contentAlign: "top"
---

# O `composer.json` do módulo

```json {all|4-7|10-14|all}
{
    "name": "ecomdev/payment",
    "type": "library",
    "autoload": {
        "psr-4": {
            "EcomDev\\Payment\\": "src/"
        }
    },
    "extra": {
        "laravel": {
            "providers": [
                "EcomDev\\Payment\\Providers\\PaymentServiceProvider"
            ]
        }
    }
}
```

<v-click>

<div class="mt-4 flex gap-4 text-sm">
  <div class="flex-1 p-3 rounded" style="background: rgba(96, 165, 250, 0.08); border: 1px solid rgba(96, 165, 250, 0.3);">
    <span style="color: var(--accent-blue); font-weight: 700;">Namespace isolado</span><br>
    <code class="text-xs">EcomDev\Payment\</code> nunca colide com <code class="text-xs">EcomDev\Sales\</code>
  </div>
  <div class="flex-1 p-3 rounded" style="background: rgba(192, 132, 252, 0.08); border: 1px solid rgba(192, 132, 252, 0.3);">
    <span style="color: var(--accent-purple); font-weight: 700;">Auto-discovery</span><br>
    Service provider registra automaticamente. Zero config manual.
  </div>
</div>

</v-click>

<!--
"Cada módulo tem seu próprio composer.json. Isso dá namespace isolado — EcomDev\Payment\ nunca vai colidir com EcomDev\Sales\. E o service provider se registra automaticamente via Laravel package discovery. Zero configuração manual."
-->

---
layout: brutalist-base
metaNumber: "19"
metaSection: "IMPLEMENTAÇÃO"
metaSubtitle: "service provider"
contentAlign: "top"
---

# O Service Provider como <span class="g g-c">contrato</span>

```php {all|3-8|10-16|all}
class PaymentServiceProvider extends ServiceProvider
{
    public function register(): void
    {
        $this->app->singleton(
            PaymentGateway::class,
            StripePaymentGateway::class
        );
    }

    public function boot(): void
    {
        Event::listen(
            OrderPlaced::class,
            StartPaymentProcess::class
        );
    }
}
```

<v-click>

<div class="mt-4 p-3 rounded" style="background: rgba(255, 165, 58, 0.08); border: 1px solid rgba(255, 165, 58, 0.3); text-align: center;">
Quer entender o que um módulo faz? Lê o <span style="color: var(--accent-orange); font-weight: 700;">Service Provider</span>.<br>
<span class="text-sm" style="opacity: 0.6;">35 linhas. Não 100+ arquivos.</span>
</div>

</v-click>

<!--
"O service provider é o contrato público do módulo. Ele diz: 'eu escuto o evento OrderPlaced e respondo processando o pagamento'. Se você quer entender o que um módulo faz e como ele se conecta ao sistema, lê o service provider. 35 linhas. Não 100+ arquivos."

"Mas antes de mover qualquer arquivo, eu fiz uma coisa que mudou tudo..."
-->

---
layout: brutalist-base
metaNumber: "20"
metaSection: "IMPLEMENTAÇÃO"
metaSubtitle: "AI como devil's advocate"
contentAlign: "top"
---

# Antes de mover código: <span class="g g-b">questionei TUDO</span>

<div class="text-sm mb-4">

Usei AI como **devil's advocate**. 13 perguntas. 13 decisões documentadas.

</div>

<v-clicks>

<div class="p-3 rounded text-sm mb-3" style="background: rgba(20, 20, 24, 0.5); border: 1px solid rgba(255, 255, 255, 0.07);">
  <span style="color: var(--accent-orange);">❓</span> "O módulo payment deve disparar criação de envio diretamente ou só o evento PaymentConfirmed?"<br>
  <span class="ml-4" style="color: var(--accent-green);">→ Só o evento. Payment não sabe que envio existe.</span>
</div>

<div class="p-3 rounded text-sm mb-3" style="background: rgba(20, 20, 24, 0.5); border: 1px solid rgba(255, 255, 255, 0.07);">
  <span style="color: var(--accent-orange);">❓</span> "Onde fica o PaymentTransaction model — no módulo que produz ou no que armazena?"<br>
  <span class="ml-4" style="color: var(--accent-green);">→ No que armazena (sales). Dados ficam com quem persiste.</span>
</div>

<div class="p-3 rounded text-sm mb-3" style="background: rgba(20, 20, 24, 0.5); border: 1px solid rgba(255, 255, 255, 0.07);">
  <span style="color: var(--accent-orange);">❓</span> "Feature flags renomeiam ou mantêm prefixo antigo?"<br>
  <span class="ml-4" style="color: var(--accent-green);">→ Mantêm. Pennant grava no banco. Risco > estética.</span>
</div>

</v-clicks>

<v-click>

<div class="mt-2 p-3 rounded text-sm" style="background: rgba(96, 165, 250, 0.08); border: 1px solid rgba(96, 165, 250, 0.3); text-align: center;">
Cada decisão virou uma entrada no <code>CONTEXT.md</code> do módulo.<br>
<span style="opacity: 0.6;">Não é doc que ninguém lê. É doc que o <span style="color: var(--accent-blue); font-weight: 700;">AGENTE</span> lê.</span>
</div>

</v-click>

<!--
"Uma das coisas que mais ajudou nesse processo foi usar AI como devil's advocate. Antes de mover qualquer arquivo, passamos por 13 perguntas. Cada uma forçou uma decisão explícita. Cada decisão virou uma entrada no CONTEXT.md do módulo — um glossário vivo que define a linguagem do domínio."

"Não é documentação que ninguém lê. É documentação que o AGENTE lê. Quando a AI vai trabalhar no módulo, ela lê o CONTEXT.md primeiro e desafia qualquer mudança que viole o glossário."

"Agora sim, com as decisões tomadas, vamos ver o código..."
-->
