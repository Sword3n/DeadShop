# DeadShop

> [!title] Deadlock database
> **156 shop items** + **44 heroes** — the full Deadlock Curiosity Shop (no Street Brawl legendaries or Corrupted items) and every playable hero with base stats, weapon stats and abilities.

| | |
|---|---|
| **Total items** | 156 |
| **Weapon** | 53 |
| **Vitality** | 54 |
| **Spirit** | 49 |
| **Tier 1** (800) | 23 |
| **Tier 2** (1,600) | 43 |
| **Tier 3** (3,200) | 46 |
| **Tier 4** (6,400) | 44 |
| **Active abilities** | 44 + 8 imbue |
| **Passive** | 104 |
| **Heroes** | 44 |

## Browse the database

- **[[Items.base]]** — the sortable / filterable database (native Obsidian **Bases**, no plugins needed)
- [[Database/All Items]] — static table of every item
- [[Database/Weapon Items]] · [[Database/Vitality Items]] · [[Database/Spirit Items]]
- `Data/items.csv` / `Data/items.json` — the whole table as a spreadsheet / script-ready JSON

## Heroes

- **[[Heroes.base]]** — the hero database (native Obsidian **Bases**, sortable / filterable)
- [[Database/Heroes stats]] — static table of every hero with base stats + weapon stats (DPS, bullet damage, ammo, fire rate)
- [[Database/Heroes abilities]] — every ability with cooldown, duration, range, cost, damage
- `Data/heroes.csv` / `Data/heroes.json` — heroes as a spreadsheet / script-ready JSON

## How it's organised

```
DeadShop/
├── Items.base          ← the item database (Bases views)
├── Heroes.base         ← the hero database (Bases views)
├── Heroes/             ← 44 hero notes (stats, weapon stats, abilities, playstyle, lore)
├── Items/
│   ├── Weapon/         ← 53 notes
│   ├── Vitality/       ← 54 notes
│   └── Spirit/         ← 49 notes
├── Database/           ← plain markdown tables (work without any plugin)
├── Data/               ← items.csv + items.json export of the full table
├── Dataview/           ← optional Dataview queries
├── Attachments/Icons/  ← in-game item icons
├── Attachments/Heroes/ ← 44 in-game hero portraits
├── Guides/             ← how to use & extend this vault
└── Sources.md          ← where the data comes from
```

Every item note carries structured properties (`slot`, `tier`, `cost`, `activation`, `group`, `effect`,
`upgrades_to`, `upgraded_from`), so you can filter, sort and script against them.

## Start here

- [[Guides/Getting Started]] — how to query and extend the database
- [[Sources.md]] — data provenance and update notes

---

### All items

![[Items.base#All Items]]

---

### All heroes

![[Heroes.base#All Heroes]]
