# 0TA - Zero Token Architecture

A satirical landing page for the revolutionary, carbon-based processing framework that doesn't require a credit card, a data center, or a high-speed internet connection.

**Stop prompting. Start thinking.**

## About

0TA is a tongue-in-cheek response to AI dependency culture. It reframes "using your brain" as a cutting-edge tech product, complete with specs, benchmarks, pricing tiers, and user reviews.

The site is a single static HTML page with inline CSS, SVG illustrations, and zero external dependencies.

## Local development

Requires [just](https://just.systems/) and Node.js (for npx).

```sh
just serve
```

This starts a local server with hot-reloading via browser-sync. Edit `index.html` and the browser refreshes automatically.

## Deployment

The site deploys to GitHub Pages via a GitHub Actions workflow on every push to `main`.

To enable it on a new repo:
1. Push to a GitHub repository
2. Go to **Settings > Pages > Source** and select **GitHub Actions**

The workflow handles the rest.

## Design system

### Themes

The site supports three color modes via a toggle in the top-right corner:

| Mode | Behavior |
|------|----------|
| **Dark** | Terminal aesthetic -- dark background, green accent |
| **Light** | Warm paper tone, deep green accent |
| **Auto** | Follows system `prefers-color-scheme` preference |

The active theme is persisted in `localStorage` under the key `0ta-theme`.

### Design tokens

All colors are defined as CSS custom properties on `:root` (dark) and `[data-theme="light"]`. Key tokens:

| Token | Purpose |
|-------|---------|
| `--bg` | Page background |
| `--bg-elevated` | Cards, modals, steps |
| `--bg-inset` | Recessed surfaces (terminal bg) |
| `--text` | Primary text |
| `--muted` | Secondary text |
| `--accent` | Brand green (links, headings, borders) |
| `--accent-soft` | Dimmed accent (citations, labels) |
| `--danger` | Error red |
| `--warn` | Warning amber |

### SVG theming

Inline SVG illustrations use CSS utility classes instead of hardcoded colors so they adapt to the active theme:

- `svg-accent`, `svg-muted`, `svg-danger`, `svg-warn` -- fill classes
- `svg-s-accent`, `svg-s-danger`, `svg-s-border` -- stroke classes
- `svg-surface`, `svg-inset` -- background fill classes

## Project structure

```
.
├── index.html              # The entire site (HTML, CSS, JS, inline SVGs)
├── justfile                # Local dev commands
├── favicon.svg             # Vector favicon (modern browsers)
├── favicon.ico             # Raster favicon fallback
├── apple-touch-icon.png    # iOS home screen icon
├── logo.svg                # Full 0TA logo
├── og-image.svg            # Social share image (source)
├── og-image.png            # Social share image (raster)
└── .github/
    └── workflows/
        └── pages.yml       # GitHub Pages deployment
```
