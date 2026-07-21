# Quick Quote — Home Inspection Estimates

A self-contained, installable web app for building on-site quotes. No backend,
no build step — works fully offline once installed on a device.

## Deploy to GitHub Pages

1. Create a new **public** repo on GitHub (e.g. `quick-quote`).
2. Upload all files in this folder to the repo root, keeping the `icons/`
   folder structure intact:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icons/icon-180.png`, `icons/icon-192.png`, `icons/icon-512.png`
3. In the repo, go to **Settings → Pages**.
4. Under **Source**, choose **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
5. GitHub gives you a URL after a minute or two, typically:
   `https://<your-username>.github.io/<repo-name>/`

## Install on iPhone / iPad

1. Open the GitHub Pages URL in **Safari**.
2. Tap **Share → Add to Home Screen**.
3. Launch it from the home screen icon — it opens full-screen, no browser bar.

After the first open, the service worker (`sw.js`) caches everything, so the
app keeps working with no signal at all. Quotes and pricing are stored
per-device using local storage, so they don't sync between devices — use the
in-app **Export saved quotes** button (Settings tab) if you want a backup or
to move quotes to another device manually.

## Updating later

Any time you edit `index.html` and push the change to GitHub, the app checks
for a new version the next time it's opened with a connection, and caches the
update for offline use after that.
