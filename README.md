# Splatterflow Portfolio

Public data for the Splatterflow app portfolio.

## Cross-promotion manifest

`cross-promo/manifest.json` is the single source of truth for the cross-promo
network (see the `CrossPromoKit` Swift package). Every app fetches it on launch
and shows the other apps. **Adding a new app = edit this file. No app code
changes, no resubmissions.**

Live URL the apps fetch:
`https://raw.githubusercontent.com/splatterflow/apps/main/cross-promo/manifest.json`

App icons live in `cross-promo/icons/<id>.png`. See `cross-promo/README.md` for
the schema and the pre-ship checklist.
