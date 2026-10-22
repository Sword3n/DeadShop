# Dataview Queries

Optional — these queries work if you install the **Dataview** community plugin.
The vault is fully usable without it: see [[Items.base]] (native Bases) and [[Database/All Items]].

## All items, grouped by slot

```dataview
TABLE tier, cost, activation, group, effect
FROM "Items"
SORT slot ASC, tier ASC, file.name ASC
```

## Tier 4 items only

```dataview
TABLE slot, cost, activation, effect
FROM "Items"
WHERE tier = 4
SORT file.name ASC
```

## Active abilities (Active / Imbue)

```dataview
TABLE slot, tier, cost, effect
FROM "Items"
WHERE activation != "Passive"
SORT tier ASC, file.name ASC
```

## Upgrade chains

```dataview
TABLE upgrades_to, upgraded_from
FROM "Items"
WHERE length(upgrades_to) > 0 OR length(upgraded_from) > 0
SORT file.name ASC
```

## Count by slot

```dataview
TABLE length(rows) AS Items
FROM "Items"
GROUP BY slot
```
