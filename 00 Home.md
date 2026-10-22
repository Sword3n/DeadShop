# DeadShop

> [!title] Deadlock shop database
> **156 items** — the full Deadlock Curiosity Shop, without Street Brawl legendaries or Corrupted items.

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

## Browse the database

- **[[Items.base]]** — the sortable / filterable database (native Obsidian **Bases**, no plugins needed)
- [[Database/All Items]] — static table of every item
- [[Database/Weapon Items]] · [[Database/Vitality Items]] · [[Database/Spirit Items]]
- `Data/items.csv` / `Data/items.json` — the whole table as a spreadsheet / script-ready JSON

## How it's organised

```
DeadShop/
├── Items.base          ← the database (Bases views)
├── Items/
│   ├── Weapon/         ← 53 notes
│   ├── Vitality/       ← 54 notes
│   └── Spirit/         ← 49 notes
├── Database/           ← plain markdown tables (work without any plugin)
├── Data/               ← items.csv + items.json export of the full table
├── Dataview/           ← optional Dataview queries
├── Attachments/Icons/  ← in-game item icons
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
