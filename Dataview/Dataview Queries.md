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

## Heroes, all

```dataview
TABLE role, complexity, emaxhealth, emaxmovespeed, esprintspeed, weapon_damage_per_second, release_date
FROM "Heroes"
SORT role ASC, complexity ASC, file.name ASC
```

## Tanks and Initiators

```dataview
TABLE role, complexity, emaxhealth, ebasehealthregen, weapon_damage_per_second
FROM "Heroes"
WHERE role = "Tank" OR role = "Initiator"
SORT role ASC, file.name ASC
```

## Gun carries

```dataview
TABLE complexity, weapon_damage_per_second, weapon_bullet_damage, weapon_ammo, weapon_bullets_per_sec
FROM "Heroes"
WHERE role = "Gun carry"
SORT weapon_damage_per_second DESC
```

## Spirit carries

```dataview
TABLE complexity, emaxhealth, emaxmovespeed, weapon_damage_per_second
FROM "Heroes"
WHERE role = "Spirit carry"
SORT file.name ASC
```

## Supports and Disruptors

```dataview
TABLE role, complexity, emaxhealth, weapon_damage_per_second
FROM "Heroes"
WHERE role = "Support" OR role = "Disruptor"
SORT role ASC, file.name ASC
```

## Count heroes by role

```dataview
TABLE length(rows) AS Heroes
FROM "Heroes"
GROUP BY role
```
