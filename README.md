# DeadShop

**Deadlock database** — every shop item and every playable hero, as an Obsidian vault.

**156 items** · Weapon 53 · Vitality 54 · Spirit 49 · Tiers 1–4 · **44 heroes**

Legendary (Street Brawl, tier 5) and Corrupted items are deliberately excluded — see [Sources.md](Sources.md).

## Use it as an Obsidian vault

Clone or download, then **Open folder as vault** in Obsidian.

```
DeadShop/
├── Items.base          ← the item database (native Obsidian Bases, 11 views)
├── Heroes.base         ← the hero database (native Obsidian Bases)
├── Heroes/             ← 44 hero notes
├── Items/
│   ├── Weapon/         ← 53 notes
│   ├── Vitality/       ← 54 notes
│   └── Spirit/         ← 49 notes
├── Database/           ← plain markdown tables (work without any plugin)
├── Dataview/           ← optional Dataview queries
├── Data/               ← items.csv + items.json export
├── Attachments/Icons/  ← in-game item icons
└── Guides/             ← how to query and extend the vault
```

Start with [`00 Home.md`](00%20Home.md).

### The database

[`Items.base`](Items.base) is an **Obsidian Bases** file — built in, no plugins required. Open it and get a
sortable, filterable table with views per slot, per tier, plus *Active Abilities* and *Upgrade chains*.

Every item note carries structured properties, so it is queryable too:

| property | example |
|---|---|
| `slot` | `Weapon` |
| `tier` / `cost` | `4` / `6400` |
| `activation` | `Passive`, `Active`, `Passive (Imbue)` |
| `group` | `More Health` |
| `effect` | `Grants +210 Bonus Health.` |
| `upgrades_to` / `upgraded_from` | `["Colossus", "Fortitude"]` |

### One note per item

Each note has the in-game stat table, the level-1 upgrade numbers, the upgrade path as `[[wiki links]]`,
and the real in-game item icon.

![item note](Attachments/Icons/extra-health.png)

## Data

Snapshot of **2026-10-15**, taken from the game's own files (client `client-6785`) via the
[deadlock.io API](https://deadlock.io/api/v1/items.json), with shop-card stat strings and upgrade lists
cross-checked against the [Dexerto Deadlock Wiki](https://www.dexerto.com/wikis/deadlock/items/).

Full provenance, coverage tables and refresh notes: **[Sources.md](Sources.md)**.

## Exports

- [`Data/items.csv`](Data/items.csv) — all 156 items as a flat spreadsheet
- [`Data/items.json`](Data/items.json) — the same data, script-ready

## Licence / attribution

Item names, stats and icons belong to Valve (Deadlock). This repository is an unofficial community
database; it is not affiliated with or endorsed by Valve.
