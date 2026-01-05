# BiS-Tooltip (WotLK 3.3.5a Backport + Custom Server Extensions)

This is a backport of **BiS-Tooltip** for **Wrath of the Lich King 3.3.5a**, extended with a **BiS Checklist UI**, **multi-source item support**, and **custom server features** (including **Ascension 5M Emblems** and custom item IDs).

Original addon (retail clients): https://www.curseforge.com/wow/addons/bis-tooltip

---

## What it does

- Adds **Best-in-Slot (BiS)** and **phase/tier** hints directly to item tooltips.
- Provides a **BiS window** and a **Checklist view** to track missing gear.
- Shows **where an item comes from** (raid boss source) and can also display **alternative sources** (e.g., emblem vendor).

---

## Highlights

### Tooltip
- BiS / Alt ranking and phase information.
- **Multiple sources** for the same item (e.g. boss drop + emblem vendor).
- **BOE info** (Bind on Equip) displayed directly in the tooltip.

### BiS Checklist UI
- Dedicated checklist panel for tracking missing items.
- Slot grouping with optional enchants and gem suggestions.
- Gem display uses **stat abbreviations** (e.g. `20STR`, `12SP/10SPI`) instead of long gem names.
- Export-friendly output (easy to copy/paste).

### Custom server support
- **Ascension 5M Emblem vendor** support (Emblem of Ascension):
  - Items can be grouped by emblem cost.
  - Total emblem cost summary for the visible checklist.
- Supports server-specific custom item IDs, including **new legendary weapons** added on the server.

### Performance / stability
- Source caching and tooltip computation caching.
- Safer frame cleanup to avoid UI leftovers after closing/reopening panels.
- Defensive nil-checks to reduce edge-case errors.

---

## Installation

1. Download / clone this repository.
2. Copy the folder to:
   - `World of Warcraft 3.3.5a/Interface/AddOns/Bistooltip/`
3. Make sure the included **Ace3** libraries are present (already bundled here).
4. Launch the game and enable the addon in the AddOns menu.

Optional (recommended):
- **DataStore** + **DataStore_Inventory** (enables broader inventory checks across bank/alts).

---

## Usage

### Slash commands
- `/bis` or `/bistooltip` — toggle the BiS window
- `/bis config` — open settings
- `/bis reload` — reload data
- `/bis help` — show help

---

## Notes for custom servers

If your server uses custom currencies/items/loot sources:
- Update `Loot_Sources.lua` and/or `EmblemData.lua` to match your realm.
- If you add new custom items (including legendaries), include their item IDs in the appropriate tables so the addon can display sources and costs.

---

## License

MIT License (see `LICENSE`).
