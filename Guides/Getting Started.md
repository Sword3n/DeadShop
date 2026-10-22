# Getting Started

## What's in this vault

A database of every item purchasable in the Deadlock Curiosity Shop (**156** items), excluding:

- **Legendary** items — the 17 Street Brawl exclusives (Tier 5, 9,999 souls). They never appear in a normal match.
- **Corrupted** items — upgraded Tier 3/4 versions handed out by The Broker's exchange or the Street Brawl
  Round 5 draft. They roll a random drawback each match, so they are not a fixed item you can buy.

Everything else is in: **Weapon (53)**, **Vitality (54)**, **Spirit (49)**.

## Three ways to browse

| | What it needs | What you get |
|---|---|---|
| [[Items.base]] | nothing — Obsidian Bases is built in | sortable, filterable database tables |
| [[Database/All Items]] | nothing | plain markdown tables, always readable |
| [[Dataview/Dataview Queries]] | Dataview community plugin | custom queries and aggregations |

## Item note anatomy

Every note in `Items/` follows the same shape:

```markdown
---
name: "Extra Health"
slot: Vitality
tier: 1
cost: 800
activation: Passive
group: "More Health"
effect: "Grants +210 Bonus Health."
icon: "[[Attachments/Icons/extra-health.png]]"
upgrades_to: ["Colossus", "Fortitude"]
upgraded_from: []
tags: [item, vitality, tier-1]
source: https://deadlock.io/en/items/extra-health
---
```

The body then holds the in-game stats table, the level-1 upgrade numbers, the upgrade path
(`[[...]]` links, so you can jump along the upgrade chain) and the source links.

## Filtering in Bases

Open `Items.base` — it already ships with views per slot, per tier, plus *Active Abilities* and
*Upgrade chains*. To build your own view, add one to `Items.base`:

```yaml
  - type: table
    name: My build
    filters:
      and:
        - file.inFolder("Items")
        - slot == "Spirit"
        - cost <= 3200
    order:
      - file.name
      - tier
      - cost
    sort:
      - property: tier
        direction: ASC
```

## Filtering with Dataview

```dataview
TABLE tier, cost, activation, effect
FROM "Items"
WHERE slot = "Vitality" AND tier >= 3
SORT cost DESC
```

## Extending it

- **Add a hero column**: add `hero: ["Bebop", "Haze"]` to the frontmatter of the notes you track, then
  add `hero` to the `order:` list of a view.
- **Add notes**: drop a new `.md` file into `Items/<Slot>/` with the same frontmatter keys and it shows up
  in every view automatically.
- **Add a build**: create a note under `Builds/` that links items with `[[Item Name]]` — the graph view
  will connect the whole chain.
