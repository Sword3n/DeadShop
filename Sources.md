# Sources

Data snapshot taken **2026-10-15** from the game's own files.

## Primary source

**Deadlock.io API** — generated from the live game client, build `client-6785`
([source repo](https://github.com/SteamDatabase/GameTracking-Deadlock/tree/4e0f960a9d175b18757ac607c04e70f15dabe7e3/game)).

- Item list, slot, tier, cost, activation type, upgrade graph, in-game shop card properties:
  `https://deadlock.io/api/v1/items.json`
- Per-item pages: `https://deadlock.io/en/items/<slug>`
- In-game icons: served from `https://deadlock.io/assets/game/panorama/images/items/...`

The API exposes **156 public shop items** (`isPublicShopItem: true`, tiers 1–4 only), which
excludes the 17 Street Brawl legendaries and the Corrupted items by construction.

## Secondary source

**Dexerto Deadlock Wiki** — used for the shop-card stat strings and the "Upgrades To/From" lists where
the game files leave them implicit: `https://www.dexerto.com/wikis/deadlock/items/`

## Cross-checks

Spot-checked values against independent community databases (deadlock.io, deadlock.gs, deadlockhandbook,
denypick, deadlockcounter.org) — e.g. Extra Health = +210 bonus health, Rapid Rounds = +9% fire rate.

## Coverage

| Slot | Items |
|---|---|
| Weapon | 53 |
| Vitality | 54 |
| Spirit | 49 |
| **Total** | **156** |

| Tier | Cost | Items |
|---|---|---|
| Tier 1 | 800 | 23 |
| Tier 2 | 1,600 | 43 |
| Tier 3 | 3,200 | 46 |
| Tier 4 | 6,400 | 44 |

## Exports

- `Data/items.csv` — all 156 items as a flat spreadsheet (name, slot, tier, cost, activation, group, effect, upgrade path, source, icon)
- `Data/items.json` — the same data with full structure, for scripting

## Refreshing

Re-fetch `https://deadlock.io/api/v1/items.json`, then regenerate the notes. Item notes are plain
markdown, so a regeneration script can overwrite them without losing any hand-written notes that live
outside `Items/`.
