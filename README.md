# DEPOT: Plarail collection tracker

DEPOT is a desktop app (Electron) for keeping track of a Plarail collection (Takara Tomy's blue-track toy trains, plus track, scenery and accessories): what you own, what you paid and what it's worth now. It also keeps a wishlist and can export a price-free, view-only web page of your collection to share, with optional one-click publishing to GitHub Pages.

Built from [PADDOCK](https://github.com/tijayfly/paddock-diecast-tracker) (diecast) and [HANGAR](https://github.com/tijayfly/hangar-gunpla-tracker) (Gunpla). Unofficial fan-made tool, not affiliated with Takara Tomy.

## Features
- **Collection:** grid of box-shaped cards or a table, search, filter by product line (Plarail, Plarail Advance, Real Class, Thomas & Friends, Shinkansen series, event/shop exclusives, track, scenery, accessories) and sort by line and model number, name, operator, series, number of cars, rarity, price paid, value or profit/loss. Totals for trains, paid (and average per bought train), current value and P&L.
- **Item pages:** model number on the box (S-01, AS-02…), train name, operator (JR East, JR Central…), series (E5, N700S…), number of cars, powered or unpowered, light-up, features, rarity (standard, or limited: event, shop or lucky-bag exclusive, or discontinued), where and when you bought it, notes, photo, price paid, current value and P&L.
- **Add by name:** type it the way it's on the box, e.g. "S-01 Light-up E5 Hayabusa", "AS-02 N700S" or "R-01 straight rail". DEPOT works out the line, number, operator, series, cars and light-up, finds photos online (searching with プラレール / Plarail), and you check it all before saving.
- **Photos:** find photos for every entry without one in a single pass (weak matches are flagged under **Check photos**), or pick, paste or use your own photo per item.
- **Wishlist:** target prices, and **Got it!** moves an item into the collection.
- **Track, scenery and accessories** are tracked without counting as trains.
- **View mode:** the eye button in the header previews the shareable page with all prices and editing hidden.
- **View-only export:** writes a static page (no price data, and not where you bought things) to `view-only/`, and can publish it to a GitHub repo.
- Light and dark mode, and a phone-friendly layout for the exported page.

## Download (Windows)
Grab **DEPOT-1.0.0-portable.exe** from the [latest release](https://github.com/tijayfly/depot-plarail-tracker/releases/latest). There's nothing to install: put it in its own folder and run it. Windows SmartScreen may warn because the app isn't code-signed; click **More info → Run anyway**.

## Run from source
You need [Node.js](https://nodejs.org) (LTS).

```
npm install
npm start
```

On Windows you can double-click `Start DEPOT.bat` instead, which installs on first run.

To build a portable Windows .exe: `npm run dist` (output in `dist/`).

## Your data
- Running from source, everything is stored in `depot-data/` inside this folder: `collection.json` (plus a `.bak` of the previous save) and an `images/` folder. The portable .exe keeps `depot-data/` next to the .exe instead.
- `depot-data/` and `view-only/` are git-ignored, so your collection, prices and any tokens never end up in a repo.
- The first launch with no data starts you with a few **example entries** (`data/seed-collection.json`). Delete them from each item's page, or replace the seed file with your own before first launch.

## Current values
Current values are **dummy placeholders** by default (from the price paid, or a typical price for the product line, with discontinued and exclusive items drifting higher), so the app is usable out of the box. There's an eBay UK option in Settings (median asking price of Buy It Now listings) that needs your own eBay developer App ID and Cert ID; it hasn't been tested against the live eBay API yet.

## Publishing the view-only page to GitHub
1. Create a repo for the page and turn on GitHub Pages (Settings → Pages → Deploy from branch → main, root).
2. Create a fine-grained personal access token limited to that repo with **Contents: Read and write**.
3. In DEPOT: Settings → View-only page → enter `owner/repo` and the token, then **Publish now** (or tick "Also publish every time I export").

Only DEPOT's own files (index.html, data.js, app.js, match.js, styles.css, theme.js, logo.svg, .nojekyll, images/) are changed in that repo. The token is stored only in your local `depot-data/collection.json`.

## Notes
- Photos are found with a Bing image search in a hidden window and cached locally.
- The Bing lookup depends on the site's current layout and may need updating if they change.

## Licence
MIT. See [LICENSE](LICENSE).
