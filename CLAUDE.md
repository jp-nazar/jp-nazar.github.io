# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal CV/portfolio site for Juan Pablo Nazar. Single static HTML file deployed via GitHub Pages. No build step, no framework, no dependencies, no Jekyll.

- **Live URL**: `https://jp-nazar.github.io/jp-nazar/` (until repo is renamed to `jp-nazar.github.io`)
- **GitHub**: `https://github.com/jp-nazar/jp-nazar`

## Deployment

Push to `master` branch → GitHub Pages auto-deploys. Changes live within ~1 minute.

```bash
git push origin master
```

## File structure

```
index.html   ← entire site (HTML + CSS inline)
avatar.jpg   ← headshot (byn.jpg copied from sources/)
sources/     ← PDFs and reference markdown, not served
```

No `_config.yml`, no `_layouts/`, no `Gemfile`. Pure static HTML.

## Internationalization (i18n)

Inline JS at bottom of `<body>`. No external files, no fetch.

- **Languages**: English (default), Spanish
- **Toggle**: fixed pill button top-right corner (`#lang-toggle`), shows target lang (ES/EN)
- **Persistence**: `localStorage` key `lang`
- **Mechanism**: `data-i18n="key"` attributes on translatable elements; `setLang(lang)` swaps `textContent` for all matches
- **Translations object**: inline `const translations = { en: {...}, es: {...} }` — all keys listed there

### Adding/editing translations

1. Find element in HTML, check its `data-i18n` key
2. Edit both `translations.en[key]` and `translations.es[key]` in the `<script>` block
3. To add a new translatable element: add `data-i18n="newkey"` to element, add key to both lang objects

### What is NOT translated

Proper nouns, URLs, tech brand names (React, Node.js, AWS…), company names, email, GitHub/LinkedIn handles.

## CSS architecture

CSS custom properties in `:root`:
- `--bg` `#0f1117` · `--surface` `#161b22` · `--border` `#21262d`
- `--text` `#e6edf3` · `--muted` `#8b949e`
- `--accent` `#4ec9b0` · `--accent-dim` `#1d3a35`

Dark theme only. Single centered column `max-width: 720px`.

Key classes:
- `.header-inner` — flex row: avatar + name/tagline
- `.avatar` — 80px circular headshot
- `.links a` — pill-shaped nav links (email, GitHub, LinkedIn)
- `.lang-btn` — fixed top-right lang toggle button (`#lang-toggle`)
- `.job` / `.job.current` — timeline entry (left border + dot); current job uses accent border
- `.pill` / `.pill.accent` — skill tags
- `.extras-list` — bulleted list with accent `▸` markers

## Sections (in order)

1. **Header** — avatar, name, tagline, contact links
2. **About** — 2-sentence bio
3. **Skills** — 4 groups: Frontend / Backend & Database / Infrastructure & Deployment / Testing
4. **Experience** — 3 jobs: Improving (current), Mediastream, Fabricamos
5. **Education** — Universidad San Sebastián
6. **Highlights** — ADA, SERCOTEC, Startup Weekend
7. **Footer** — GitHub link

## Content notes

- GitHub username: `jp-nazar` (old: `nazius` — do not use)
- LinkedIn: `cl.linkedin.com/in/jpnazar`
- Email: `jp.nazar@gmail.com`
- Source PDFs in `sources/` have full work history if more detail needed
