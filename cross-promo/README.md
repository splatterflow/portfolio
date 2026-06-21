# Cross-Promo Manifest

This is the single source of truth for the portfolio cross-promotion network
(see `CrossPromoKit`). Every app fetches this file on launch and shows the other
apps in its "More Apps" surfaces. **Adding a new app = edit this file. No app
code changes, no resubmissions.**

## Hosting (GitHub raw — chosen)

1. Put this folder in a **public** repo, e.g. `splatterflow/apps`.
2. The live URL each app fetches is the raw URL of `manifest.json`:
   `https://raw.githubusercontent.com/<user>/<repo>/main/cross-promo/manifest.json`
3. Set that exact URL in each app's `CrossPromo.swift` (`manifestURL`).
4. App icons go in `cross-promo/icons/<id>.png` (~120×120, transparent or square).

> GitHub raw is CDN-cached for a few minutes — fine for a manifest that changes
> rarely. For instant updates later, move to Cloudflare Pages with the same path.

## Schema (per app)

| field        | required | notes                                                        |
|--------------|----------|--------------------------------------------------------------|
| `id`         | yes      | stable slug; also used as the SKAN campaign token            |
| `bundleId`   | yes      | each app self-excludes its own bundle id                     |
| `appStoreId` | yes      | numeric App Store ID (for SKStoreProductViewController)      |
| `name`       | yes      | display name                                                 |
| `tagline`    | no       | one short benefit line                                       |
| `iconURL`    | no       | falls back to a letter tile if missing/unreachable           |
| `urlScheme`  | no       | used with `canOpenURL` to hide already-installed apps        |
| `weight`     | no       | higher = shown first; **boost a freshly launched app**       |
| `active`     | no       | set `false` to pull an app without removing it (default true)|
| `countries`  | no       | ISO regions to restrict to (null = everywhere)               |
| `minIOS`     | no       | hide on older devices (e.g. "17.0")                          |

## TODO before this is live

- [ ] Replace `0000000000` App Store IDs with the real numeric IDs.
- [ ] Push the icons to `cross-promo/icons/`.
- [ ] Confirm the repo path in each app's `CrossPromo.swift`.
- [ ] Each app must register its own `urlScheme` (CFBundleURLTypes) and list the
      others in `LSApplicationQueriesSchemes` for installed-app filtering.
