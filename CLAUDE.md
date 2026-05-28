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
├── 00-intro/              # Cover, whoami, agenda
│   ├── 01-cover.md
│   ├── 02-whoami.md
│   └── 03-toctree.md
├── 01-abertura/           # Storytelling opening: legadão, meme, virada
│   ├── 01-legadao.md          # Section intro
│   ├── 02-legadao-pastas.md   # Stepper: ALL 19 folders expanded (tree-explorer layout)
│   ├── 03-meme.md             # index.php humor
│   └── 04-virada.md           # Emotional turn
├── 02-extracao/           # Conceptual: boundaries, deletion test, folder structures
│   ├── 01-boundaries.md       # Section intro + deletion test concept
│   ├── 02-teste-falha.md      # Deletion test Q1: scattered files → fails (deletion-test layout)
│   ├── 03-estruturas.md       # 4 folder patterns for same module (core message)
│   ├── 04-reteste.md          # Deletion test Q1 retest: modular → passes
│   ├── 05-teste-p2.md         # Deletion test Q2: cross-module coupling
│   ├── 06-evento-visual.md    # Interactive EventFlow diagram (coupled vs decoupled)
│   ├── 07-eventos.md          # Before/after: imports vs events (split-compare)
│   ├── 08-teste-p2-passa.md   # Deletion test Q2 retest: events → passes
│   ├── 09-caso-shop.md        # Real-world shop module (100+ files)
│   └── 10-resultado.md        # Mermaid: 1 shop → sales, payment, fulfillment
├── 03-implementacao/      # Technical: modular, code, errors, patterns
│   ├── 01-modular.md      # internachi/modular + AI as devil's advocate
│   ├── 02-before-after.md # Magic-move code diffs
│   ├── 03-erros.md        # 3 real errors intercalated with story
│   └── 04-padroes.md      # 3 patterns: Identity, Integration-*, Panel
├── 04-fechamento/         # Closing: numbers, rules, CTA
│   ├── 01-antes-depois.md
│   ├── 02-regras.md       # 4 rules (improved)
│   └── 03-cta.md
```

### Custom layouts (`layouts/`)

| Layout | File | Slots | Props | Purpose |
|--------|------|-------|-------|---------|
| `tree-explorer` | `tree-explorer.vue` | `default` (title), `::tree::`, `::content::`, `::note::` | `noteType`: info/warning/danger/tip | Two-column stepper with admonition. Left=tree, Right=files+note |
| `whoami` | `whoami.vue` | `default` (bio) | `image`, `handle`, `full_name`, `has_socials` | Profile with circular avatar |
| `impact` | `impact.vue` | `default` | `color`: red/yellow/green/blue/purple | Big number/statement with radial glow |
| `split-compare` | `split-compare.vue` | `default` (title), `::before::`, `::after::` | `beforeLabel`, `afterLabel` | Before/after with colored tints |
| `deletion-test` | `deletion-test.vue` | `default` (title), `::questions::`, `::visual::` | — | Title row + questions/visual split (32%/68%) for interactive deletion test |

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

Order follows the tree top-to-bottom: Actions → Data → Enums → Events → Http → Jobs → Listeners → Livewire → Mail → Models → Notifications → Observers → Services → Rest → Impact(487).

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

The talk uses a fictional ecommerce project as the running example. The tree shown in the opening stepper has 487 PHP files across 19 directories. Key folder counts: Models(45), Services(22), Http(25), Jobs(18), Actions(15), Events(12), Listeners(10), Data(10), Enums(8), Livewire(8), Mail(6), Notifications(6), Observers(5). The extraction splits a monolithic `shop` module into: sales, payment, fulfillment.

## Deployment

Configured for both Netlify (`netlify.toml`) and Vercel (`vercel.json`). Build output goes to `dist/`. Node 20 required.

## Agent skills

### Issue tracker

Issues tracked as local markdown files under `.scratch/`. See `docs/agents/issue-tracker.md`.

### Triage labels

Default label vocabulary (needs-triage, needs-info, ready-for-agent, ready-for-human, wontfix). See `docs/agents/triage-labels.md`.

### Domain docs

Single-context layout — one `CONTEXT.md` + `docs/adr/` at repo root. See `docs/agents/domain.md`.
