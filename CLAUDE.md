# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Slidev presentation for a ~40min talk titled "Como eu descobri que meu app/Services/ era uma mentira" — a Portuguese BR talk about Laravel modularization, targeting Laravel devs who have never modularized.

**Core message**: "Não existe padrão certo de pastas. Existe o que encaixa pro seu time." — the talk argues that the important thing is extracting responsibilities into modules with clear boundaries, not which folder structure you use (flat, clean arch, DDD, Laravel default).

**Narrative style**: Story-first journey. Opens with shared experience ("quem já mexeu num legadão?"), builds empathy, then walks through the speaker's real extraction process with errors and lessons learned. NOT a top-down tutorial.

**Language**: All slide content and speaker notes are in Portuguese BR.

## Commands

```bash
pnpm run dev      # Start dev server at http://localhost:3030
pnpm run build    # Build static SPA to dist/
pnpm run export   # Export to PDF (requires playwright-chromium)
```

## Architecture

### Main files

- **slides.md** — Only frontmatter (theme, title, transitions) + `src:` imports to pages. No inline slide content.
- **layouts/** — Custom Vue layouts (see below)
- **components/** — Vue components usable directly in slides (e.g. `<Counter />`)
- **snippets/** — External code files importable via `<<< @/snippets/file.ts#region`

### Key dependencies

- `@vue-flow/core` (^1.48.2) — powers the interactive `EventFlow.vue` diagram
- `@iconify-json/mdi` (devDep) — Material Design Icons available in slides via `<mdi-icon-name />`

### Slide pages structure

Pages are organized in numbered subfolders matching the talk's narrative sections:

```
pages/
├── 00-intro/              # Cover, whoami, comunidades, recruit (3Pontos QR), agenda (4 atos)
├── 01-abertura/           # Ato 01 · O legadão (~5 min)
│   ├── 01-legadao.md          # Act divider
│   ├── 02-legadao-pastas.md   # Stepper: all 18 folders, 210 files (tree-explorer layout) → impact
│   └── 04-virada.md           # Emotional turn ("isolar em pedaços")
├── 02-extracao/           # Ato 02 · Teste da Deleção (~22 min)
│   ├── 01-boundaries.md       # Act divider + the 3 questions
│   ├── 02-teste-falha.md      # Q1-Q3 fail on the legadão (payment: 9 files in 8 folders)
│   ├── 03-estruturas.md       # 4 folder patterns for the same module (core message)
│   ├── 04…08                  # Q1 passes (app/Modules), Q2 fails → events → passes
│   ├── 09…11                  # Q3 leak → Gateway module → 3/3
│   └── 12…16                  # Q4 (framework) → internachi/modular → 4/4
├── 03-convencoes/         # Ato 03 · Convenções (~7 min): 00-ato, integration-*, panel-*, disclaimer
├── 04-fechamento/         # Ato 04 · Fechamento (~6 min): 00-ato, payoff (pivot), monólito modular, CTA
├── poc-phpeste/           # PHPeste 2026 identity POC (entry: poc-phpeste.md, ph-* layouts)
└── _archive/              # Unused older slides (not in slides.md)
```

### Custom layouts (`layouts/`)

| Layout | File | Slots | Props | Purpose |
|--------|------|-------|-------|---------|
| `tree-explorer` | `tree-explorer.vue` | `default` (title), `::tree::`, `::content::`, `::note::` | `noteType`: info/warning/danger/tip | Two-column stepper with admonition. Left=tree, Right=files+note |
| `whoami` | `whoami.vue` | `default` (bio) | `image`, `handle`, `full_name`, `has_socials` | Profile with circular avatar |
| `impact` | `impact.vue` | `default` | `color`: red/yellow/green/blue/purple | Big number/statement with radial glow |
| `split-compare` | `split-compare.vue` | `default` (title), `::before::`, `::after::` | `beforeLabel`, `afterLabel` | Before/after with colored tints |
| `deletion-test` | `deletion-test.vue` | `default` (title), `::questions::`, `::visual::` | — | Title row + questions/visual split (32%/68%) for interactive deletion test |

### PHPeste 2026 layouts (`ph-*`, used by `poc-phpeste.md`)

Shared tokens and helpers live in `styles/phpeste.css` (palette, Rubik Dirt + Lora, azulejo stripe, stamped badges, stage classes `.ph-step/.ph-files/.ph-dep/.ph-callout/.ph-mods/.ph-term/.ph-score/.ph-ink`). Only the colour pairs listed at the top of that file are allowed for text (WCAG AA).

| Layout | Use |
|--------|-----|
| `ph-cover`, `ph-whoami` | Opening slides |
| `ph-section` | Generic content slide (`tone: espresso/orange/sand`, eyebrow, h1 + note, `::content::`, hint) |
| `ph-act` | Act divider (crimson, act number, tracker) |
| `ph-tree` | Folder stepper (same slots as `tree-explorer`) |
| `ph-impact` | Big number or statement (`size: number/statement`) |
| `ph-deletion` | Teste da Deleção: `questions`/`result` in frontmatter react to clicks; set `clicks: N`; stage in `::visual::` |
| `ph-split` | Before/after with `::before::`, `::after::`, `::footer::` |

Extra stage classes: `.ph-tabs/.ph-tab` (click-driven tabs), `.ph-spectrum`, `.ph-gains/.ph-gain`, `.ph-diff`, `.ph-verdict`, `.ph-q1`, `.ph-depmap`. The closing slide reuses `ph-whoami`.

Components: `PhCard`, `PhTicket`, `PhActs` (agenda bar), `PhCouplingLanes` (import vs evento, click-driven). Inside raw `<pre>` blocks never leave an empty line (markdown closes the HTML block) — use `&nbsp;`. Pages imported via `src:` sometimes miss HMR; restart the dev server before trusting a screenshot.

### Components (`components/`)

| Component | Purpose |
|-----------|---------|
| `Counter.vue` | Simple interactive counter (Slidev demo) |
| `EventFlow.vue` | Interactive Vue Flow diagram: coupled vs decoupled module communication. Uses `@vue-flow/core`. Togglable mode (coupled/decoupled) + delete simulation |
| `EventFlowModule.vue` | SVG module node renderer used inside `EventFlow.vue` |

### Stepper pattern (`02-legadao-pastas.md`)

The folder walkthrough uses `tree-explorer` layout with `transition: none` on every slide so only the right panel content changes. Each slide has an HTML comment header for navigation:
```
<!-- ============================================ -->
<!-- STEPPER: app/Actions/ (line 2)               -->
<!-- ============================================ -->
```

Order follows the tree top-to-bottom: Actions → Data → Enums → Events → Http → Jobs → Listeners → Livewire → Mail → Models → Notifications → Observers → Services → Rest → Impact(210).

The same `transition: none` stepper pattern is reused in `02-extracao/` (slides `02-teste-falha` through `08-teste-p2-passa`) with the `deletion-test` layout — each slide progresses the interactive deletion test while keeping the questions panel stable. Note that `03-estruturas.md` is a separate topic interleaved in this range, not part of the stepper.

## Slidev Conventions

- Slides are separated by `---` in markdown
- Frontmatter at top of file configures theme, transitions, title, duration
- Per-slide frontmatter goes between `---` separators (layout, class, transition, level)
- Speaker notes go in `<!-- comment blocks -->` at the end of each slide
- Vue components and `<script setup>` blocks work inline in slides
- Code blocks support line highlighting (`{1|2-3|all}`), magic-move animations, and Monaco editor
- Diagrams via Mermaid and PlantUML in fenced code blocks
- Click animations via `v-click`, `v-after` directives
- Theme: `seriph` (dark mode). Available seriph layouts: cover, fact, intro, quote, section, statement. Plus Slidev core: default, center, two-cols, two-cols-header, image-left, image-right, full, end, etc.

## Ecommerce example data

The talk uses a fictional ecommerce project as the running example. The opening stepper shows all 18 `app/` folders and 210 PHP files; per-folder counts must add up to that total: Models(45, listing is an excerpt), Http(25), Services(22), Jobs(18), Actions(15), Events(12), Listeners(10), Data(10), Enums(8), Livewire(8), Mail(6), Notifications(6), Observers(5), rest(20: Console, Exceptions, Policies, Providers, Support). Every file the deletion test cites must exist in the stepper.

Module names used from act 02 onward: Cart, Catalog, Checkout, Payment, Shipping. Story of the payment module: Q2 cuts Checkout's import with the `OrderPlaced` event (Checkout never calls Payment again); Q3 finds the leak *inside* Payment — `PaymentGatewayService` is shared by three features living there (cobrança, reembolso, antifraude) — so Gateway becomes a module (contract) and Refunds and Fraud move out of Payment. Acts 03–04 reuse these names (lowercase as internachi `app-modules/*`); `integration-stripe` implements the Gateway contract. The 4 folder structures in `03-estruturas` must show the same 5 Cart files.

The talk's 4th deletion-test question is a reveal at the end of act 02 — don't mention "4 perguntas" before it (agenda, cover).

## Deployment

Configured for both Netlify (`netlify.toml`) and Vercel (`vercel.json`). Build output goes to `dist/`. Node >= 22.12 required (Slidev 53).

## Agent skills

### Issue tracker

Issues tracked as local markdown files under `.scratch/`. See `docs/agents/issue-tracker.md`.

### Triage labels

Default label vocabulary (needs-triage, needs-info, ready-for-agent, ready-for-human, wontfix). See `docs/agents/triage-labels.md`.

### Domain docs

Single-context layout — one `CONTEXT.md` + `docs/adr/` at repo root. See `docs/agents/domain.md`.
