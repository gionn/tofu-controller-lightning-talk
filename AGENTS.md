# AGENTS.md

Guidance for AI coding assistants working in this repository.

## What this is

A [Slidev](https://sli.dev) slide deck for a 15-minute lightning talk, "Evolution, not revolution": pushing Terraform into Kubernetes GitOps with [tofu-controller](https://github.com/flux-iac/tofu-controller). `slides.md` is the only deck — one short statement or diagram per slide, with speaker notes in the trailing HTML comment on each slide. Note the `package.json` name is `tofu-controller`, while the repo is `gionn/tofu-controller-lightning-talk`.

## Commands

- `npm install` — install dependencies. The project uses npm (`package-lock.json`); `pnpm-workspace.yaml` is vestigial, so don't reach for pnpm.
- `npm run dev` — Slidev dev server with live reload at http://localhost:3030 (the `dev` script passes `--open`, so it launches a browser automatically)
- `npm run build` — build the static SPA into `dist/`
- `npm run export` — export to PDF/PNG/PPTX; writes a `slides-export.*` file to the repo root (gitignored). Needs `playwright-chromium`, an optional peer dependency that is **not** installed by default, so the first export must add it (which downloads a browser binary).

No test suite, linter, or CI is configured.

## Slide writing conventions

- Big-statement headlines (the `layout: statement` slides, and other slide titles that are a single punchy line) don't end with a period. A multi-clause line keeps the periods that separate its internal beats (e.g. `Don't rewrite. Run it in **Kubernetes**`), just not the trailing one.
- Body copy, bullet lists, and captions (e.g. the trade-offs slide) keep normal sentence punctuation.
- Every slide carries a trailing `<!-- ... -->` block: these are presenter notes, not hidden comments, so add one to any new slide.

## Structure

- `slides.md` — the entry point and only deck; slides are separated by `---` dividers, each slide's YAML frontmatter controls layout/transition for that slide, and the trailing HTML comment on each slide holds speaker notes. Headmatter sets `theme: default`, `colorSchema: dark`, `duration: 15min`; `@slidev/theme-seriph` is installed but unused.
- `style.css` — global overrides for the default theme (dark background, accent color, statement-layout type size), auto-loaded by Slidev since it sits next to `slides.md`
- `global-bottom.vue` — Slidev auto-registers this root file as a global-layer component (no import needed); despite the name it floats the current slide number in the top-right corner

## Slidev reference

A vendored copy of the Slidev skill (`SKILL.md` plus ~50 topic references on syntax, layouts, animation markers, and export) lives in `.agents/skills/slidev/`. It is gitignored, installed via `npx skills add slidevjs/slidev` and pinned in `skills-lock.json` — consult it for Slidev specifics rather than guessing.

## Deployment

Static output (`dist/`) is deployed as an SPA with catch-all rewrites to `index.html`, configured for both Netlify (`netlify.toml`, Node 24) and Vercel (`vercel.json`) — either platform can build/host this from the same repo.
