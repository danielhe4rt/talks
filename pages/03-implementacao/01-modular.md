---
layout: section
---

# `internachi/modular`
## na prática

<!--
"Beleza, achei os boundaries. Mas como eu implemento isso em Laravel? A resposta é o internachi/modular."
-->

---

# Setup em 2 comandos

<div class="grid grid-cols-2 gap-6">
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

<div class="mt-4 p-3 bg-green-900/30 rounded-lg border border-green-500/30 text-center">
Cada módulo é um <span class="text-green-400 font-bold">mini-package Laravel</span> com namespace próprio.
</div>

</v-click>

<!--
"Dois comandos. composer require e php artisan make:module. Pronto, você tem um módulo com estrutura completa — service provider, config, migrations, tests. Cada módulo é basicamente um mini-package Laravel com namespace próprio."
-->

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
  <div class="flex-1 p-3 bg-blue-900/30 rounded border border-blue-500/30">
    <span class="text-blue-400 font-bold">Namespace isolado</span><br>
    <code class="text-xs">EcomDev\Payment\</code> nunca colide com <code class="text-xs">EcomDev\Sales\</code>
  </div>
  <div class="flex-1 p-3 bg-purple-900/30 rounded border border-purple-500/30">
    <span class="text-purple-400 font-bold">Auto-discovery</span><br>
    Service provider registra automaticamente. Zero config manual.
  </div>
</div>

</v-click>

<!--
"Cada módulo tem seu próprio composer.json. Isso dá namespace isolado — EcomDev\Payment\ nunca vai colidir com EcomDev\Sales\. E o service provider se registra automaticamente via Laravel package discovery. Zero configuração manual."
-->

---

# O Service Provider como contrato

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

<div class="mt-4 p-3 bg-yellow-900/30 rounded-lg border border-yellow-500/30 text-center">
Quer entender o que um módulo faz? Lê o <span class="text-yellow-400 font-bold">Service Provider</span>.<br>
<span class="text-sm opacity-60">35 linhas. Não 100+ arquivos.</span>
</div>

</v-click>

<!--
"O service provider é o contrato público do módulo. Ele diz: 'eu escuto o evento OrderPlaced e respondo processando o pagamento'. Se você quer entender o que um módulo faz e como ele se conecta ao sistema, lê o service provider. 35 linhas. Não 100+ arquivos."

"Mas antes de mover qualquer arquivo, eu fiz uma coisa que mudou tudo..."
-->

---

# Antes de mover código: questionei TUDO

<div class="text-sm mb-4">

Usei AI como **devil's advocate**. 13 perguntas. 13 decisões documentadas.

</div>

<v-clicks>

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30 text-sm mb-3">
  <span class="text-yellow-400">❓</span> "O módulo payment deve disparar criação de envio diretamente ou só o evento PaymentConfirmed?"<br>
  <span class="ml-4 text-green-400">→ Só o evento. Payment não sabe que envio existe.</span>
</div>

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30 text-sm mb-3">
  <span class="text-yellow-400">❓</span> "Onde fica o PaymentTransaction model — no módulo que produz ou no que armazena?"<br>
  <span class="ml-4 text-green-400">→ No que armazena (sales). Dados ficam com quem persiste.</span>
</div>

<div class="p-3 bg-gray-800/50 rounded-lg border border-gray-600/30 text-sm mb-3">
  <span class="text-yellow-400">❓</span> "Feature flags renomeiam ou mantêm prefixo antigo?"<br>
  <span class="ml-4 text-green-400">→ Mantêm. Pennant grava no banco. Risco > estética.</span>
</div>

</v-clicks>

<v-click>

<div class="mt-2 p-3 bg-blue-900/30 rounded-lg border border-blue-500/30 text-sm text-center">
Cada decisão virou uma entrada no <code>CONTEXT.md</code> do módulo.<br>
<span class="opacity-60">Não é doc que ninguém lê. É doc que o <span class="text-blue-400 font-bold">AGENTE</span> lê.</span>
</div>

</v-click>

<!--
"Uma das coisas que mais ajudou nesse processo foi usar AI como devil's advocate. Antes de mover qualquer arquivo, passamos por 13 perguntas. Cada uma forçou uma decisão explícita. Cada decisão virou uma entrada no CONTEXT.md do módulo — um glossário vivo que define a linguagem do domínio."

"Não é documentação que ninguém lê. É documentação que o AGENTE lê. Quando a AI vai trabalhar no módulo, ela lê o CONTEXT.md primeiro e desafia qualquer mudança que viole o glossário."

"Agora sim, com as decisões tomadas, vamos ver o código..."
-->
