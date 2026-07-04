# OG Revise → installable offline PWA

You now have **6 files** that live together in the **same GitHub Pages folder**
as your app (the folder that serves `ayesh1991.github.io/OGinfo/`):

| File | What it is |
|------|-----------|
| `OG-Revise-PWA-v2.html` | the app (as before) |
| `manifest.webmanifest` | makes it installable (name, icons, colours) |
| `sw.js` | service worker — offline app-shell caching |
| `icon-192.png` / `icon-512.png` | home-screen icons |
| `icon-192-maskable.png` / `icon-512-maskable.png` | icons for Android's adaptive shapes |

## Deploy (GitHub web UI)

1. Open your repo folder that hosts the app (the one with `OG-Revise-PWA-v2.html`).
2. **Upload all 6 files** into that same folder (drag them in, commit).
3. Done. No build step, no config.

> All paths are **relative** (`./sw.js`, `icon-192.png`, …), so it works at
> `/OGinfo/` or any sub-path without editing anything.

## Two things to check once

- **Filename match.** The manifest's `start_url` is `./OG-Revise-PWA-v2.html`.
  If your deployed app file is named something else (e.g. `index.html`), edit
  that one line in `manifest.webmanifest` to match.
- **Same folder.** `sw.js` and `manifest.webmanifest` must sit **beside** the
  HTML, not in a sub-folder — a service worker can only control its own folder.

## Install it

- **iPhone/iPad (Safari):** open the app → Share → **Add to Home Screen**.
- **Android (Chrome):** an **⬇ Install** button appears in the app header, or use
  the browser menu → *Install app*.
- After installing, it launches full-screen from your home screen with the OG
  Revise icon, and the **app shell loads even with no connection** (your Drive
  content still needs a connection to sync, which the header badge now shows).

## Updating later

When you deploy a new build of the HTML, bump `CACHE_VERSION` at the top of
`sw.js` (e.g. `og-revise-v1` → `og-revise-v2`) and re-upload it. Old caches are
cleared automatically and the app shows a small “update ready” note.

## The new sync badge

The header pill now reflects real state:

- **Synced** (green) — connected, nothing pending
- **Syncing…** (amber ↻) — a Drive read/write is in flight
- **Offline** (grey) — no connection; your work stays local and syncs later
- **Reconnect** (red, pulsing) — Drive session expired; tap to sign in again
