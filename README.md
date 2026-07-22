# Quick Quote — Home Inspection Estimates

A self-contained, installable web app for building on-site quotes. No backend,
no build step — works fully offline once installed on a device.

## Install on iPhone / iPad

1. Open the GitHub Pages URL in **Safari**.
2. Tap **Share → Add to Home Screen**.
3. Launch it from the home screen icon — it opens full-screen, no browser bar.

After the first open, the service worker (`sw.js`) caches everything, so the
app keeps working with no signal at all. Quotes and pricing are stored
per-device using local storage, so they don't sync between devices — use the
in-app **Export saved quotes** button (Settings tab) if you want a backup or
to move quotes to another device manually.
