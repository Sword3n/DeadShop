# Getting Started


## Heroes

The vault also carries a **hero database** — all 44 playable heroes with base stats, weapon stats and abilities.

- **[[Heroes.base]]** — native Obsidian Bases
- [[Database/Heroes stats]] — static table of every hero: health, regen, move, sprint, stamina, melee, dash, DPS, bullet damage, ammo, fire rate, reload, release date
- [[Database/Heroes abilities]] — 176 abilities with cooldown, duration, range, spirit cost, charges, damage
- `Data/heroes.csv` / `Data/heroes.json` — heroes as a spreadsheet / script-ready JSON

Every hero note carries structured properties (`complexity`, `emaxhealth`, `emaxmovespeed`,
`weapon_dps`, `release_date`, `abilities`, …), so you can filter, sort and script against them
exactly like items.

Release dates and weapon stats come from [deadlock.wiki](https://deadlock.wiki); stat and ability
numbers come from Valve's raw game files. See [[Sources.md]] for the full breakdown — including why
the roster is 44 and not the 41 the Deadlock.io API still reports.
