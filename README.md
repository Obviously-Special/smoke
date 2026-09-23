# Smoke — Find Needle in a Haystack Simulator Simulator

Smoke is a static, dependency-free parody storefront. The game is the storefront: find the one genuine **Needle in a Haystack Simulator** amid 80 suspiciously similar listings.

## Run locally

Open `index.html` in any modern browser. There is no build step, server, package manager, backend, external font, or API required.

## Configure the real game link

At the top of `script.js`, change this value before publishing:

```js
realGameUrl: "PUT_REAL_STEAM_URL_HERE"
```

`REAL_GAME_URL` is also declared immediately below the configuration object for easy discovery.

## Catalog content

The structured catalog is in `script.js` under **GAME DATABASE**. `realGame` is the single authentic listing and has the stable ID `real-needle-game` and `isRealGame: true`. Fake titles are split into `convincingTitles`, `plausibleTitles`, and `absurdTitles`; metadata is generated deterministically by `createGame()` from those clean title lists.

To add a game, add a title to one of those lists. To fully hand-author an entry, add an object matching `realGame`'s fields to `GAME_DATABASE`. Keep exactly one `isRealGame: true` entry.

## Deploy

### Cloudflare Pages

1. Put these files in a Git repository and push it.
2. In Cloudflare Pages, create a project from that repository.
3. Select no framework / static HTML. Leave build command blank and set output directory to `/`.
4. Deploy. Hash routing means no server rewrite rule is needed.

### GitHub Pages

1. Push this folder to a repository.
2. In **Settings → Pages**, choose **Deploy from a branch**.
3. Select the desired branch and the repository root (`/`).
4. Save. GitHub Pages serves `index.html` directly; hash routes work without additional configuration.

## Notes

Artwork and screenshots are procedural HTML/CSS rather than borrowed assets. Current-run progress lives in `sessionStorage`, so a refresh preserves it but closing the browser session normally does not. Smoke is a parody project and is not affiliated with Valve or Steam.

## Cover images

Cover rotation uses the local haystack images supplied in the project root. They are referenced by the `USER_COVER_PHOTOS` array in `script.js`, so adding or removing an image only requires updating that one list.
