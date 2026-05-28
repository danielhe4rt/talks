---
layout: brutalist-base
transition: none
metaNumber: "22"
metaSection: "EXTRAÇÃO"
metaSubtitle: "internachi/modular"
metaPhase: refactor
metaRight: "Q4 · REFLECTION"
contentAlign: "top"
---

<TitleBlock
  eyebrow="por baixo do capô"
  outlined="A MÁGICA"
  solid="É REFLECTION"
  accent="."
  tail="≈ 10 LINHAS"
  size="small"
/>

<div class="refl-wrap">

```php {*}{class:'!text-xs'}
// internachi/modular — versão simplificada

foreach (glob(base_path('app/Modules/*'), GLOB_ONLYDIR) as $path) {
    $module   = basename($path);
    $provider = "App\\Modules\\{$module}\\{$module}ServiceProvider";

    if (class_exists($provider)) {
        (new ReflectionClass($provider))
            ->newInstance($this->app)
            ->register();
    }
}
```

<div class="refl-takeaway">
<span class="refl-mark">▶</span>
<span>Você deleta a pasta. O scanner não acha. O app continua de boa.</span>
</div>

</div>

<style>
.refl-wrap {
  margin-top: 0.6rem;
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
}
.refl-wrap :deep(pre) {
  margin: 0;
  font-size: 0.7rem;
  line-height: 1.45;
}
.refl-takeaway {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  font-family: var(--font-serif);
  font-style: italic;
  font-size: 1rem;
  color: #c8c2b6;
  padding: 0.5rem 0.85rem;
  border-left: 3px solid var(--accent-purple);
  background: linear-gradient(90deg, rgba(192, 132, 252, 0.08), transparent);
  align-self: flex-start;
}
.refl-mark { color: var(--accent-purple); font-family: var(--font-mono); font-size: 0.75rem; }
</style>

<!--
"A mágica do internachi é boba. É ReflectionClass. Glob na pasta app/Modules/, pra cada subpasta tenta instanciar o ServiceProvider correspondente, e registra."

"Não tem feitiço. Tem só 10 linhas que assumem uma convenção: cada módulo tem um ServiceProvider com o mesmo nome da pasta."

"E o detalhe importante: você deleta a pasta. O scanner faz glob, não acha mais o caminho, não tenta carregar. O app continua de boa. Sem linha pra editar, sem cache pra limpar."
-->
