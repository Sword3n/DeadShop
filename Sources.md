---
type: heroes-stats
game: Deadlock (Valve)
source: SteamDatabase/GameTracking-Deadlock master — game/citadel/pak01_dir/scripts/heroes.vdata
source_version: 6801
hero_count: 44
updated: 2026-10-24
---

# Sources

Item data snapshot **2026-10-15** from the game's own files.
Hero data snapshot **2026-10-24** (game files build **6801**, 2026-10-20).

## Primary source — shop items

**Deadlock.io API** — generated from the live game client, build `client-6785`
([source repo](https://github.com/SteamDatabase/GameTracking-Deadlock/tree/4e0f960a9d175b18757ac607c04e70f15dabe7e3/game)).

- Item list, slot, tier, cost, activation type, upgrade graph, in-game shop card properties:
  `https://deadlock.io/api/v1/items.json`
- Per-item pages: `https://deadlock.io/en/items/<slug>`
- In-game icons: served from `https://deadlock.io/assets/game/panorama/images/items/...`

The API exposes **156 public shop items** (`isPublicShopItem: true`, tiers 1–4 only), which
excludes the 17 Street Brawl legendaries and the Corrupted items by construction.

## Primary source — heroes

Hero stats and ability numbers come from Valve's **raw game files**, newest first:

- Hero data: `game/citadel/pak01_dir/scripts/heroes.vdata` (`CitadelHeroData_t`)
  → `m_mapStartingStats` holds the level-1 stat block
- Ability data: `game/citadel/pak01_dir/scripts/abilities.vdata` (`CitadelAbilityVData`)
  → `m_mapAbilityProperties` holds cooldown / duration / range / spirit cost / charges / damage
- Localisation (hero display names, ability names, role blurbs):
  `game/citadel/resource/localization/citadel_heroes/citadel_heroes_english.txt`
  and `.../citadel_gc_hero_names/citadel_gc_hero_names_english.txt`
- Repo: [SteamDatabase/GameTracking-Deadlock](https://github.com/SteamDatabase/GameTracking-Deadlock)
  (branch `master`, build 6801)

**Deadlock.io API** — same generated client snapshot (`client-6785`), used where the raw files
only give internal ids:

- Hero roster, playstyle, lore, gun archetype, asset paths:
  `https://deadlock.io/api/v1/heroes.json`
- Ability display names, descriptions, activation type:
  `https://deadlock.io/api/v1/abilities.json`
- Per-hero pages: `https://deadlock.io/en/heroes/<slug>`

> ⚠️ **The API roster is stale.** Its snapshot predates the *City Never Sleeps* update, so it
> lists 41 heroes and is missing **Baba**, **Violet** and **Nurse Harrow**, which launched
> 6, 16 and 20 October 2026. Those three are recovered from the raw game files plus the wiki.

## Secondary source — weapon stats, release dates, portraits

**Deadlock wiki** — [deadlock.wiki](https://deadlock.wiki) hero infoboxes.

- Weapon stats: DPS, bullet damage, ammo, bullets per second, reload time, bullet velocity
- **Release dates** — the authoritative "is this hero live?" signal
- Hero portraits: `https://cdn.deadlock.wiki/<Hero>_vertical.png`

The game files expose weapon stats only as **display-group references** (`EWeaponDPS`,
`EBulletDamage`, `EClipSize`, `ERoundsPerSecond` in `statDisplayGroups`) — the actual values
are not in the data, so the wiki infoboxes are the authoritative source for those numbers.

## Roster — how "is this hero live?" is decided

`m_bInDevelopment` / `m_bDisabled` in the game files **lag behind actual releases**, so they
are not used for the roster. The signal is:

1. A **deadlock.wiki** hero page exists **and** carries a `Release Date` → the hero is live.
2. Heroes in the files with no wiki page (or a wiki stub without a date) are internal/dev
   entries and are **excluded**.

Applying that rule to the 2026-10-24 game files gives **44 live heroes**, matching
[deadlockhandbook.com/heroes](https://deadlockhandbook.com/heroes/) ("44 heroes are playable
today"). The six *City Never Sleeps* heroes, launched one at a time on Tuesdays and Fridays:

| Hero | Release | In API snapshot? |
|---|---|---|
| Rat King | 2 Oct 2026 | yes |
| Baba | 6 Oct 2026 | **no** |
| Solomon | 9 Oct 2026 | yes |
| Deadman Danny | 13 Oct 2026 | yes |
| Violet | 16 Oct 2026 | **no** |
| Nurse Harrow | 20 Oct 2026 | **no** |

## Secondary source — shop item strings

**Dexerto Deadlock Wiki** — used for the shop-card stat strings and the "Upgrades To/From" lists where
the game files leave them implicit: `https://www.dexerto.com/wikis/deadlock/items/`

## Cross-checks

- **164 wiki vs game-file stat values** compared across all 41 API-era heroes — **0 discrepancies**
  (max delta 0.05 on sprint multipliers, which is wiki rounding). Health, regen, move speed and
  sprint speed agree exactly between two independent sources.
- Roster size cross-checked against the Deadlock Handbook (44) and the wiki roster page (44).
- Item values spot-checked against independent community databases (deadlock.io, deadlock.gs,
  deadlockhandbook, denypick, deadlockcounter.org) — e.g. Extra Health = +210 bonus health,
  Rapid Rounds = +9% fire rate.

## Coverage

### Shop items

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

### Heroes

| Metric | Value |
|---|---|
| Heroes | 44 |

## Exports

- `Data/items.csv` — all 156 items as a flat spreadsheet (name, slot, tier, cost, activation, group, effect, upgrade path, source, icon)
- `Data/items.json` — the same data with full structure, for scripting
- `Data/heroes.csv` — all 44 heroes (name, role, complexity, gun archetype, full stat block, weapon stats, ability list, release date, voice actor, playstyle, lore)
- `Data/heroes.json` — the same data with full structure, for scripting

## Refreshing

### Shop items

Re-fetch `https://deadlock.io/api/v1/items.json`, then regenerate the notes. Item notes are plain
markdown, so a regeneration script can overwrite them without losing any hand-written notes that live
outside `Items/`.

### Heroes

Three sources, in priority order:

```
# 1. raw game files (stats + ability numbers) — build 6801
https://raw.githubusercontent.com/SteamDatabase/GameTracking-Deadlock/master/game/citadel/pak01_dir/scripts/heroes.vdata
https://raw.githubusercontent.com/SteamDatabase/GameTracking-Deadlock/master/game/citadel/pak01_dir/scripts/abilities.vdata

# 2. Deadlock.io API (display names, descriptions, assets) — NOTE: roster lags, see above
https://deadlock.io/api/v1/heroes.json
https://deadlock.io/api/v1/abilities.json

# 3. deadlock.wiki (weapon stats, release dates, portraits)
https://deadlock.wiki/<Hero>
```

Parse notes:
- **hero blocks** live at one tab in `heroes.vdata`; stats at **three** tabs inside `m_mapStartingStats`
- **ability blocks** live at one tab in `abilities.vdata`; properties at three tabs inside `m_mapAbilityProperties`
- a wiki infobox page contains **two** stat blocks — the hero's own first, then a comparison table.
  Take the **first** occurrence of every label, or the numbers leak from another hero
  (Silver was picking up another hero's 955 HP instead of its own 830)
- hero internal id ≠ display name: `hero_artist` is **Violet**, `hero_nurse` is **Nurse Harrow**,
  `hero_baba` is **Baba**. Map via the localisation file, not by string-munging the id

Hero notes live in `Heroes/` and carry structured properties (`complexity`, `emaxhealth`,
`emaxmovespeed`, `weapon_dps`, `release_date`, `abilities`, …), so `Heroes.base` views and any
scripting work against them directly.
