# OG Revise — clean re-upload (7 files, no renaming)

You said you'd delete everything from the `OGinfo` repo and upload a fresh set.
These **7 files are already named exactly right** — upload them as-is, do not
rename anything.

## Files to upload (all into the repo ROOT of `OGinfo`)

1. `index.html`              ← THE APP (this is the whole OG Revise app)
2. `manifest.webmanifest`
3. `sw.js`
4. `icon-192.png`
5. `icon-512.png`
6. `icon-192-maskable.png`
7. `icon-512-maskable.png`

That's the complete set. Nothing else is needed for the app to work.

## Steps

1. In your `OGinfo` repo, delete the old files (Add file area → or delete each).
   Old leftovers to make sure are GONE: `OG-Revise-PWA-v2.html`, any old
   `index.html`, `PWA_INSTALL_README.md` (optional to keep).
2. **Add file → Upload files** → drag in all 7 files above → Commit.
3. Wait ~1 minute for the green `github-pages` deployment to finish
   (repo → Deployments, or Settings → Pages shows "Your site is live").
4. Open **`https://ayesh1991.github.io/OGinfo/`** in Safari.
   → The app loads directly. No 404, no redirect, no loader page.

## Then install to Home Screen (do it in THIS order)

1. Make sure the **app** is on screen and the tab title reads *OG Revise*
   (not "Page not found").
2. Delete any old OG Revise / "Page not found" icon already on your home screen.
3. Share → **Add to Home Screen** → Add.
4. Launch from the new icon → full-screen app, works offline for the shell.

## Why this is now correct (what was wrong before)

- The app file had been renamed/removed, so the old `index.html` loader
  redirected to a file that no longer existed → 404.
- Now **the app IS `index.html`** — it lives at the folder root, so
  `https://ayesh1991.github.io/OGinfo/` serves the app directly. There is no
  second file to point at, so nothing can mismatch.
- `manifest.webmanifest` `start_url`/`scope` = `/OGinfo/` (the folder root = the
  app). `sw.js` caches `index.html` as the shell. Every reference checked and
  resolves.

## Sanity check (optional but reassuring)

After deploying, these should ALL load:
- `https://ayesh1991.github.io/OGinfo/`                     → the app
- `https://ayesh1991.github.io/OGinfo/manifest.webmanifest` → JSON text
- `https://ayesh1991.github.io/OGinfo/sw.js`                → script text
- `https://ayesh1991.github.io/OGinfo/icon-192.png`         → the icon

## Not part of this upload (leave them as they are)

Your **Uploader** and **Team** apps live in their own separate folders and do
NOT depend on any of these files. They were never the cause of the 404, so you
don't need to touch them.

## If you ever move the folder

The manifest uses `/OGinfo/`. If you rename the repo/folder, change the three
`/OGinfo/` lines in `manifest.webmanifest` to the new path. Nothing else needs
editing.
