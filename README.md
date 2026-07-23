# Quick Quote — Home Inspection Estimates

A self-contained, installable web app for building on-site quotes. No backend,
no build step — works fully offline once installed on a device.

## Features

- **Client details** — name, phone (auto-formats as you type), email, property address
- **Military / First Responder discount** — one-tap toggle, knocks a set % off the entire quote
- **Tier pricing by square footage** — three tiers, each with a flat base price up
  to a set square footage, then a per-square-foot rate beyond that
- **Per-tier add-on discount** — higher tiers can automatically discount every
  selected add-on by a set percentage
- **Editable add-ons** — toggle on/off per quote; add, rename, reprice, or remove
- **Mileage-based add-ons** — certain add-ons (e.g. Radon) calculate their own
  extra cost from miles entered × a per-mile rate × a trip multiplier, since
  some services need multiple trips out
- **Sample-based add-ons** — mold-type add-ons include a set number of samples
  in the base price, with a stepper to add more at a set price each
- **Standalone services** — a separate list of services (Radon, Sewer Scope,
  Mold, Water Quality, Commercial Mold, Pre-Drywall) that can be quoted on
  their own, without requiring a full inspection tier
- **Trip mileage** — a general miles field for the inspection visit itself,
  free for the first stretch (55 miles by default), then billed at the same
  per-mile rate for everything beyond that
- **Saved quotes** — search, reopen and edit any saved quote (updates it in
  place), or delete it
- **Export backup** — download all saved quotes as a JSON file
- **Fully offline** — installs to the home screen and keeps working with zero
  signal after the first load

## Current defaults

These are just the starting values on a fresh install — everything below is
editable per-device in the app's **Settings** tab, with no code changes needed.

**Tiers**

| Tier | Base price | Flat through | Rate beyond | Add-on discount |
|---|---|---|---|---|
| Plus | $400 | 1,000 sq ft | $0.08/sq ft | — |
| Premium | $620 | 1,000 sq ft | $0.12/sq ft | 15% off add-ons |
| Prestige | $1,100 | 1,000 sq ft | $0.16/sq ft | 30% off add-ons |

**Add-ons (with a tier)**

| Add-on | Price | Notes |
|---|---|---|
| Mold | $345 | 3 samples included, +$32 each after |
| Pools and Spa | $125 | |
| Radon | $200 | +miles × $0.76 × 2 trips |
| Sewer Scope | $230 | |
| Water Quality | $275 | |
| 360 Tour | $200 | |
| 360 Tour with Floor Plan | $240 | |

**Standalone services (no tier required)**

| Service | Price | Notes |
|---|---|---|
| Sewer Scope | $275 | +miles × $0.76 × 2 trips |
| Mold | $345 | 3 samples included, +$32 each after |
| Water Quality | $300 | |
| Commercial Mold | $475 | |
| Radon | $200 | +miles × $0.76 × 4 trips |
| Pre-Drywall | $250 | +miles × $0.76 × 2 trips |

**Global**: mileage rate $0.76/mile · first 55 miles free on trip mileage ·
Military/First Responder discount 5% off the whole quote.

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

## Updating the app

**Pricing, tiers, add-ons, mileage rate, discounts** — no code changes
needed. Use the **Settings** tab on the device itself; it saves there
automatically. This only affects that one device — teammates installing fresh
will get whatever is in `index.html`'s defaults, and existing installs keep
whatever they already have saved locally.

**Anything else (a fix, new feature, layout change)** — edit `index.html`
and/or `sw.js`, then:

1. Replace the changed file(s) in the repo (pencil icon → paste new content → commit).
2. **Bump the cache version** at the top of `sw.js` — e.g. `quick-quote-v10` →
   `quick-quote-v11` — any time `index.html` changes. This is what forces
   already-installed copies to fetch the update instead of quietly continuing
   to serve the old cached version. Skipping this step is the most common
   reason a fix doesn't seem to show up.
3. Open the app once with a connection so it grabs the update. After that it
   works offline again as normal.
