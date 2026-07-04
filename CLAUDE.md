# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Public marketing website for **Barakah**, a private baby/family care tracking app for iOS. Data syncs via iCloud only — no accounts, no third-party servers (a point the site repeatedly emphasizes; keep messaging consistent with this).

Published via GitHub Pages at `https://Barakah-app.github.io/iOS`.

## Architecture

Three fully static, standalone HTML pages — no build step, no bundler, no package.json, no JavaScript anywhere in the site:

- `index.html` — landing page (hero, feature grid, privacy section)
- `privacy.html` — privacy policy
- `support.html` — support & FAQ

Each page is self-contained: all CSS lives in a `<style>` block in that page's own `<head>`. There is **no shared stylesheet**. `index.html` and `privacy.html`/`support.html` even define their own separate (and slightly different) sets of CSS custom properties (`--teal`, `--teal-dark`, `--cream`, etc.) in their own `:root`. When changing shared visual elements (colors, nav, fonts), you must edit each page individually — a change to one page's `<style>` block does not propagate to the others.

Assets live in `images/` (app icon, App Store badge, QR barcode). Referenced with relative paths (`images/icon.png`).

## Development

There is no build/lint/test tooling in this repo — it's plain HTML/CSS. To preview changes, just open the HTML file directly in a browser, or serve the directory with any static file server (e.g. `python3 -m http.server`).

Since deployment is via GitHub Pages serving these files directly, any change to `index.html`, `privacy.html`, `support.html`, or `images/` goes live on push to the default branch as-is — there's no intermediate build artifact to worry about.
