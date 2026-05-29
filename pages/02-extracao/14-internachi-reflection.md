---
layout: brutalist-base
transition: none
metaNumber: "22"
metaSection: "EXTRAÇÃO"
metaSubtitle: "internachi/modular"
metaPhase: refactor
metaRight: "Q4 · COMPOSER"
contentAlign: "top"
---

<div class="cmp-head">
  <span class="cmp-eyebrow"><span class="cmp-eyebrow__mark">◆</span> por baixo do capô</span>
  <h2 class="cmp-title">
    cada módulo é um <span class="cmp-title__hit">pacote composer<span class="cmp-title__dot">.</span></span>
  </h2>
</div>

<div class="composer-grid">

<div class="composer-panel">
  <div class="composer-panel__head">
    <span class="composer-panel__tag">raiz</span>
    <span class="composer-panel__path">composer.json</span>
  </div>

```json {*}{class:'!text-[0.62rem] !leading-snug'}
{
  "require": {
    "internachi/modular": "^3.0",
    "shop/payment":  "*",
    "shop/checkout": "*",
    "shop/gateway":  "*"
    // ... 1 entry por módulo
  },
  "repositories": [
    { "type": "path", "url": "app-modules/*" }
  ]
}
```

  <div class="composer-panel__note">
    Composer trata cada pasta de <code>app-modules/*</code> como pacote local.
  </div>
</div>

<div class="composer-panel">
  <div class="composer-panel__head">
    <span class="composer-panel__tag composer-panel__tag--mod">módulo</span>
    <span class="composer-panel__path">app-modules/payment/composer.json</span>
  </div>

```json {*}{class:'!text-[0.62rem] !leading-snug'}
{
  "name": "shop/payment",
  "autoload": {
    "psr-4": { "Shop\\Payment\\": "src/" }
  },
  "extra": {
    "laravel": {
      "providers": [
        "Shop\\Payment\\PaymentServiceProvider"
      ]
    }
  }
}
```

  <div class="composer-panel__note">
    <b>Package discovery</b> do Laravel registra o provider sozinho.
  </div>
</div>

</div>

<div class="composer-takeaway">
  <span class="ct-mark">▶</span>
  <span>Composer carrega. Laravel auto-descobre. Você nunca mais toca em <code>providers.php</code>.</span>
</div>

<style>
.cmp-head {
  display: flex;
  align-items: baseline;
  gap: 1rem;
  margin-top: 0.1rem;
}
.cmp-eyebrow {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.92rem;
  color: #b9b3a9;
  letter-spacing: 0.01em;
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  white-space: nowrap;
}
.cmp-eyebrow__mark { color: var(--red); font-size: 0.6rem; transform: translateY(-1px); }
.cmp-title {
  font-family: var(--font-display);
  font-weight: 900;
  font-size: 2.4rem;
  line-height: 1;
  letter-spacing: -0.01em;
  color: var(--bone);
  margin: 0;
  text-transform: uppercase;
}
.cmp-title__hit { color: var(--bone); }
.cmp-title__dot { color: var(--red); text-shadow: 0 0 16px rgba(255,45,32,0.45); }

.composer-grid {
  margin-top: 0.85rem;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.85rem;
}
.composer-panel {
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 3px;
  background: linear-gradient(180deg, rgba(20,20,24,0.55), rgba(10,10,12,0.75));
  padding: 0.5rem 0.6rem 0.6rem;
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}
.composer-panel__head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.6rem;
  padding-bottom: 0.3rem;
  border-bottom: 1px solid rgba(255,255,255,0.06);
}
.composer-panel__tag {
  font-family: var(--font-mono);
  font-size: 0.55rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--accent-purple);
  font-weight: 700;
  padding: 0.12rem 0.4rem;
  border: 1px solid var(--accent-purple);
  border-radius: 2px;
}
.composer-panel__tag--mod {
  color: var(--accent-green);
  border-color: var(--accent-green);
}
.composer-panel__path {
  font-family: var(--font-mono);
  font-size: 0.62rem;
  color: var(--dim);
  letter-spacing: 0.02em;
  font-style: italic;
}
.composer-panel :deep(pre) {
  margin: 0;
  border-radius: 2px;
}
.composer-panel__note {
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.72rem;
  line-height: 1.35;
  color: #b9b3a9;
}
.composer-panel__note b {
  font-family: var(--font-mono);
  font-style: normal;
  color: var(--bone);
  font-weight: 700;
}
.composer-panel__note code {
  font-family: var(--font-mono);
  font-style: normal;
  font-size: 0.68rem;
  color: var(--accent-green);
  background: rgba(74, 222, 128, 0.08);
  padding: 0.05rem 0.28rem;
  border-radius: 2px;
}
.composer-takeaway {
  margin-top: 0.65rem;
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 0.95rem;
  color: #c8c2b6;
  padding: 0.45rem 0.85rem;
  border-left: 3px solid var(--accent-purple);
  background: linear-gradient(90deg, rgba(192, 132, 252, 0.08), transparent);
}
.composer-takeaway code {
  font-family: var(--font-mono);
  font-style: normal;
  font-size: 0.82rem;
  color: var(--bone);
  background: rgba(255,255,255,0.05);
  padding: 0.05rem 0.35rem;
  border-radius: 2px;
}
.ct-mark { color: var(--accent-purple); font-family: var(--font-mono); font-size: 0.72rem; }
</style>

<!--
"A mágica do internachi não é reflection, não é scanner mágico. É Composer."

"Olha o composer.json da raiz — esquerda. Eu adiciono `internachi/modular` como dep e crio uma path repository apontando pra `app-modules/*`. Daí cada pasta lá dentro vira um pacote Composer local."

"E o composer.json do módulo — direita. Cada módulo tem o seu. Nome, autoload PSR-4, e o pulo do gato: `extra.laravel.providers`. Isso é package discovery padrão do Laravel — quando o Composer monta o autoload, o Laravel lê esse extra e registra o ServiceProvider sozinho."

"O internachi te dá um `php artisan modules:make` pra gerar essa estrutura e um `modules:sync` pra manter o require do raiz alinhado com o que existe em `app-modules/`. Mas o mecanismo é Composer + package discovery. Padrão Laravel."

"Take-away: Composer carrega. Laravel auto-descobre. Você nunca mais toca em providers.php."

[transição] "Beleza, mas o que é que mora dentro de uma dessas pastas? Vou te mostrar."
-->
