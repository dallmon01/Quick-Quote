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
