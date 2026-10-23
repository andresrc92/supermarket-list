# Mercadito

A shopping-list app built from real supermarket tickets (Fresh Market / Disco and Macromercado, Montevideo). It runs as an installable Progressive Web App: one static page, no server, no build step.

## Features

- **Shop:** catalog of products from past tickets, with one search bar that suggests matches and offers to add a product when none is found.
- **Shopping list:** quantities, a per-store total for the whole list, and which store is cheapest.
- **Shopping now:** a picking screen grouped by aisle. Tap items as they go in the cart, with a progress bar and running total.
- **Previous orders:** past tickets with totals and one-tap reorder.
- **Unit price calculator:** compare $/L, $/kg or $/unit across sizes and packs (mL vs L, g vs kg).
- **Works offline** after the first visit, and installs to the home screen.

## Where data is saved

| Running as | List, products, prices | Ticket scanning |
|---|---|---|
| Installed PWA / any browser | This device (localStorage, survives refreshes and restarts) | Not available |
| Claude artifact (claude.ai or Claude app) | Synced privately to your Claude account | Available (uses your Claude usage) |

The PWA does not sync between devices. Adding a backend (for example Firebase/Firestore) is the next step for that.

## Run locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

Service workers need `http://localhost` or HTTPS; opening the file directly works but won't install or go offline.

## Deploy

Pushing to `main` deploys to GitHub Pages through `.github/workflows/pages.yml`. If the first run fails, enable Pages once: **Settings → Pages → Source: GitHub Actions**, then re-run the workflow.

When you change `index.html` or the icons, bump `VERSION` in `sw.js` so installed copies pick up the update.

## Files

- `index.html`: the whole app (HTML, CSS, JS, product illustrations as inline SVG)
- `manifest.webmanifest`: install metadata
- `sw.js`: offline cache
- `icons/`: app icons
