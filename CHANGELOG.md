# BisTooltip Changelog

## Version 1.2.0-3.3.5a

### New Features

1. **Dual Source Support** - Items now show both boss drops AND emblem vendors in tooltips
   - Example: "Source: [Icecrown Citadel 25HM] - The Lich King | Emblem of Ascension x95"
   - Colors match the emblem type (purple for Ascension, blue for Frost, etc.)

2. **Tier Combining for BIS Phases** - Consecutive BIS tiers are now combined
   - Instead of "T7 BIS / T8 BIS / T9 BIS / T10 BIS"
   - Shows: "|cff00ff00BIS T7-T10|r" (green colored)
   - Also works for ALT ranks: "|cffffa500ALT2 T8-T10|r" (orange colored)

3. **Emblem Filter Mode** - New checkbox in BIS Checklist mode
   - Toggle "Emblems only" to show only items purchasable with emblems
   - Shows total emblems needed per currency type in real-time
   - Side panel groups items by emblem currency with individual costs
   - Export includes a full "EMBLEM SHOPPING LIST" section

4. **Custom Server Support** - Added EmblemData.lua for Emblem of Ascension
   - Easy to configure emblem vendor items
   - Supports any custom currency
   - Includes `/bisemblem` command to check item emblem info

5. **Improved Gem Stat Display** - Gems now show abbreviated stats
   - Example: "20STR/15STA" instead of gem names
   - Supports all WotLK stats: STR, AGI, INT, SPI, STA, SP, AP, HIT, CRIT, HASTE, EXP, ARP, DEF, DODGE, PARRY, BLOCK, MP5, RES

### Bug Fixes

1. **Fixed Config.lua dropdown bug** - Select widget now uses correct callback signatures

2. **Removed global table pollution** - `table.contains` moved to Utils module

3. **Added nil checks for spec icons** - Defensive checks throughout

4. **Fixed emblem color display** - Now uses proper colors from Constants

### Improvements

1. **EmblemData.lua** - Comprehensive emblem vendor database:
   - Pre-configured with Emblem of Frost tier 10 items
   - Pre-configured with Emblem of Triumph items
   - Template for Emblem of Ascension (custom server)
   - `/bisemblem [itemId]` command to check emblem info

2. **Enhanced stat abbreviations** - More comprehensive mappings for gem parsing

3. **Instance difficulty tags** - Shows 10N, 25N, 10HM, 25HM in sources

4. **Emblem summary in UI** - Real-time display of total emblems needed

### Configuration

**Adding Emblem of Ascension items:**

Edit `EmblemData.lua` and uncomment/add items in the `ASCENSION_ITEMS` table:

```lua
local ASCENSION_ITEMS = {
    [51312] = 95,  -- Sanctified Scourgelord Helmet
    [51314] = 60,  -- Sanctified Scourgelord Shoulderplates
    -- Add more: [itemId] = cost
}
```

**Checking if an item is available from emblems:**

```
/bisemblem 50356
```

Output: `Corroded Skeleton Key (ID: 50356): Emblem of Frost x60`

### File Structure

```
Bistooltip/
├── Utils.lua        - Shared utility functions
├── Constants.lua    - UI/config constants, emblem data, tier combining
├── EmblemData.lua   - Emblem vendor item mappings (customize here!)
├── Core.lua         - Addon initialization, equipment cache
├── Config.lua       - Settings and configuration
├── Bistooltip.lua   - Tooltip enhancement
├── Bislist.lua      - Main BIS list window UI
└── Bistooltip.toc   - Load order
```

### Dependencies

- Ace3 libraries (required)
- DataStore, DataStore_Inventory (optional)

---

## Version 1.1.0-3.3.5a

### Bug Fixes

1. **Fixed Config.lua dropdown bug** - The `data_source` select widget was using incorrect callback signatures

2. **Removed global table pollution** - `table.contains` moved to Utils module

3. **Added nil checks for spec icons** - Defensive checks throughout

4. **Fixed TOC Author field**

### Performance Improvements

1. **Tooltip refresh cooldown** (0.1s)
2. **Tooltip caching** (1 second TTL)
3. **Source caching**

### New Features

1. **Enhanced slash commands**: `/bis`, `/bis config`, `/bis reload`
2. **New Utils.lua module** - Shared utility functions
3. **New Constants.lua module** - Centralized configuration
