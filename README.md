# Crimson Desert - Offline Save Editor

BIG credits to @Gek a awesome dude from discord who help me with the decryption logic.

A standalone save editor for Crimson Desert. Edit your inventory, swap equipment, change stacks, modify enchants, inject stat buffs, manage sockets, expand storage, increase stack sizes — all offline, no mods required in-game.

## Download

Grab `CrimsonSaveEditor.exe` from the release. Single file, no installation needed.

## Features

- **PARC Insert (NEW)** — Add brand new items to your inventory without needing a donor item. Full tree verification ensures no crashes.
- **Clone to Vendor (NEW)** — Clone any sold item into a new vendor entry. Search by name, buy it back in-game for a fully correct item. Type-for-type swap required.
- **Inventory Editor** — View all items with names/icons, edit stack counts, batch edit, delete items
- **Equipment Editor** — Change enchant level (0-10), endurance, sharpness, duplicate gear for swapping
- **Item Swap** — Transform any item into another with category filters and 2,262 real game templates. Swap 1 from stack to keep the rest intact.
- **Repurchase (Vendor Swap)** — The most reliable swap method: sell junk, swap in editor, buy back
- **Socket Editor** — Swap Abyss Gear gems in equipment sockets (189 gems across 30+ categories)
- **ItemBuffs** — Edit base stats on any item in game data (damage, defense, speed, crit, resistances)
- **Max Stacks** — Increase all stackable item max stacks to 99/999/9999 (replaces FatStacks mod)
- **Equipment Sets** — Create, share, and apply stat buff presets as community sets via GitHub
- **Item Packs** — Download and apply curated item collections from the community (including dye packs and Dragon packs)
- **Community Mapping** — Help map every item in the game by scanning your saves
- **Community Mod Loader (NEW)** — Load community JSON mods alongside Save Editor patches. Drop `.json` files into `SEModLoad/Json/`, enable/disable with checkboxes, automatic conflict detection
- **ASI Plugin Manager (NEW)** — Install, enable/disable ASI plugins from `SEModLoad/ASI/` directly in the editor
- **GPatch** — Game file patches: mount death respawn timer, storage expansion (700 slots)
- **PABGB Browser** — Browse any game data file (Dev mode)
- **Give Item** — Pick any item from the database and a donor item to sacrifice
- **Backup/Restore** — Automatic backup before every save, pristine backup support
- **Auto-Find Saves** — Locates save files automatically (Steam, Epic, Game Pass, Linux Proton)
- **Font Scaling** — Edit menu: scale the UI to 100%, 125%, 150%, or 200%. Persists across restarts.
- **Guides Menu** — In-app guides for every tab explaining how to use each feature
- **10x Faster Loading** — C-backed ChaCha20 decryption, deferred PARC parsing

## How To Use

1. It's recommended that you **Close the game** HOWEVER it is not required it still works.
2. Run `CrimsonSaveEditor.exe`
3. Go to **File > Open Save File** or use the sidebar save browser
   - Right-click any save slot for quick actions (Open File Location, Copy Path)
   - Saves are typically at: `%LOCALAPPDATA%\Pearl Abyss\CD\save\<steamid>\slot100\save.save`
4. Make your edits
5. **File > Save** to write changes (a backup is created automatically)
6. Launch the game and load your save

**New to the editor?** Check the **Guides** menu for step-by-step instructions for each tab.

## Tabs

### Inventory
Browse all items in your save. Search by name, key, or category. Filter by source (Equipment, Inventory, Vendor, Bags). Use **Unknown Items** filter to find unmapped item keys from other players' saves.

Note: The save stores stacks as single entries — a stack of 90 stones is one save record that the game splits into multiple visual slots at runtime.

### Equipment
Shows all equipment with enchant, endurance, and sharpness. **Duplicate All Equipment** to create copies for swapping. Enchant items at a blacksmith in-game first for them to appear here.

### Item Swap
Select an item from Inventory, pick a target from the category-filtered database (2,262 items with real templates). **Swap (Single Item)** or **Swap All (Global)** to transform items.

**Warning:** Swapping equipment in inventory may cause items to not appear in-game. Use the **Repurchase tab** for reliable equipment swaps instead.

### Repurchase (Vendor Swap)
The **most reliable** way to get new gear:
1. Sell a junk item to any vendor in-game
2. Save, open in editor, find the sold item here
3. Use **Clone Selected to Vendor** — search by item name, pick a same-type target
4. Or use **Swap Selected Item** for a simple key swap
5. Save, load in-game, buy it back from the vendor

**Clone to Vendor usage:** Sell a helmet to a vendor. In the editor, select it and click Clone Selected to Vendor. Search "helmet" and pick the one you want. Save, reload, buy it back. The game creates a fully correct item.

**Type-for-type rule:** Glove->Glove works. Helm->Helm works. Glove->Helm does NOT work (unequippable). If you get a wrong-type item, sell it to a vendor, then Clone it to the correct type to fix it.

### Sockets (Abyss Gear)
Swap gems in equipment sockets. 189 Abyss Gears available including combat skills, stat buffs, resistances, banes, and gathering bonuses. Empty sockets must have a gem installed in-game first (Witch NPC > Create Socket > Embed Abyss Gear).

### ItemBuffs (Stat Editing)
Edit base stats on ANY item in the game data files. Extract iteminfo, search for items, apply presets:
- **Max All** — Max every stat value (flat to 999,999, rates to Lv 15)
- **Max DDD/DPV/HP** — Max specific stat types
- **Custom** — Pick any stat and set a specific value
- **Also apply Max Stacks** — Check the box to also set all stackable items to 99/999/9999 (replaces FatStacks mod, survives game updates)

Use **My Inventory** button to instantly list items from your loaded save.

Right-click items to add them to **Equipment Sets** — reusable buff presets you can share with the community.

**Requires admin privileges** to write game files. Use Restore Original or Steam Verify Integrity if issues occur.

### GPatch (Game Patches)
Apply game file patches that survive save changes:
- **Mount Death Respawn (1s)** — Sets all 32 mount/vehicle death respawn timers to 1 second (vanilla: ~90 min). Note: Dragon summon duration/cooldown is hardcoded and cannot be modified.
- **Storage Expansion (700)** — Expand warehouse, bank, and camp storage to 700 slots. Does NOT modify player inventory (which causes bugs).
- **Community Mod Loader** — Load community JSON mods from `SEModLoad/Json/` alongside SE patches. Automatic PABGB-to-PAZ offset conversion via PAMT index. Conflict detection between all mods.
- **ASI Plugin Manager** — Install/uninstall ASI plugins from `SEModLoad/ASI/`. Enable/disable with checkboxes. Auto-detects ASI loader DLL.

### Item Packs
Download community item collections from GitHub. Create your own packs to share loadouts with others.

### Community Mapping
Help map every item in Crimson Desert. Scan your saves to discover new item templates and upload them to the community database. The more saves we scan, the more items the editor can support.

## Adding Items

### PARC Insert (No Donor Needed)
The **Add New Item (PARC Insert)** button creates brand new items in your inventory:
1. Click **Add New Item (PARC Insert)** in the Inventory tab
2. Select the item (currently Narima's Horn for Dragon CD reset)
3. Set the quantity and confirm
4. Save and reload in-game (may require 2 reloads but not usually)

### Clone to Vendor (Best for Equipment)
The **Clone Selected to Vendor** button in the Repurchase tab is the best way to get equipment:
1. Sell any junk item to a vendor in-game, save
2. Open save in editor, go to Repurchase tab
3. Select the sold item, click **Clone Selected to Vendor**
4. Search for the item you want by name (must be same type as donor)
5. Save, reload, buy it back from the vendor

### Give Item (Donor System)
Transforms an existing item into the one you want:
1. Click **Give Item** in the Inventory tab
2. Search and select the item you want, set the quantity
3. Pick a donor item from your inventory to sacrifice
4. Confirm — the donor becomes the target item

**Tip:** Buy cheap materials from a vendor in-game to use as donors.

## Known Limitations

- **PARC Insert limited items** — Currently only Narima's Horn is confirmed for direct inventory insertion. More items coming as testing continues.
- **Type-for-type swaps only** — Vendor clone/swap must match equipment type (Glove->Glove, Helm->Helm). Cross-type produces unequippable items.
- **Equipment stats after swap** — Swapped equipment may show wrong damage/defense until unequip + re-equip
- **Empty sockets** — Cannot fill empty sockets from the editor, must install a gem in-game first
- **Dragon summon timer** — 15 min duration / 50 min cooldown is hardcoded in game executable, cannot be patched
- **Lobby saves** — Only `save.save` (in-game saves) are supported, not `lobby.save`
- **Longer load time** — Full tree verification adds processing time. Optimization in progress.

## Save File Locations

| Platform | Path |
|----------|------|
| Steam | `%LOCALAPPDATA%\Pearl Abyss\CD\save\<id>\slot100\save.save` |
| Epic | `%LOCALAPPDATA%\Pearl Abyss\CD_Epic\save\<id>\slot100\save.save` |
| Game Pass | `%LOCALAPPDATA%\Pearl Abyss\CD_GamePass\save\<id>\slot100\save.save` |
| Linux (Proton) | `~/.steam/steam/steamapps/compatdata/2623190/pfx/drive_c/users/steamuser/AppData/Local/Pearl Abyss/CD/save/<id>/slot100/save.save` |

Slot numbering: `slot0-2` = autosaves, `slot100-108` = manual saves (slot 1-9 in-game).

## Troubleshooting

**"HMAC mismatch" warning on load**
The save may be from a different game version or was partially corrupted. The editor will still try to load it.

**Game doesn't load the edited save**
Restore from the automatic backup (Backup/Restore tab) and try again. Make sure the game is fully closed before editing.

**No items shown after loading**
The save file might be a lobby save (`lobby.save`) which has minimal data. Use `save.save` instead.

**Corrupted backup file**
If a backup was created from an already-broken save, it will also be corrupt. Use an earlier backup or the pristine backup.

**Game says "installation failed" after patching**
The PAPGT integrity file may not have updated correctly. Click "Restore Original" in ItemBuffs tab, then try again. Or use Steam > Verify Integrity of Game Files.

## Technical Details

The editor handles the full save file crypto pipeline:
- **Decryption:** ChaCha20 (RFC 7539) — C-backed via `cryptography` library for 10x speed
- **Integrity:** HMAC-SHA256 verification
- **Compression:** LZ4 HC (high compression)
- **Format:** PARC (Pearl Abyss Reflect Container) binary serialization
- **Game Data:** iteminfo.pabgb / vehicleinfo.pabgb / inventory.pabgb editing via LZ4 repack into PAZ archives

## Credits

- Save format reverse engineering and editor by the Crimson Desert modding community
- @Gek — save decryption logic
- @Potter420 — iteminfo structural parser and stat injection research
- Item names maintained by community contributors
- Item icons from [questlog.gg](https://questlog.gg/crimson-desert)
- LZ4 compression by Yann Collet (BSD license)

---

## Changelog

### v2.5.5

**New: Community Mod Loader (GPatch tab)**
- Load community JSON mods alongside Save Editor patches — drop `.json` files into `Crimson Desert/bin64/SEModLoad/Json/`
- Automatic PABGB-to-PAZ offset conversion via PAMT index — no manual setup needed
- Enable/disable mods with checkboxes, conflict detection between all mods
- Compatible with mods from CD JSON Mod Manager, Nexus, and other community tools

**New: ASI Plugin Manager (GPatch tab)**
- Install, enable/disable ASI plugins from `SEModLoad/ASI/`
- Auto-detects ASI loader DLL (winmm.dll, version.dll, etc.)
- One-click install with companion `.ini` config files

**Changed**
- Storage expansion reduced from 900 to 700 (safer for stability)
- Item count spinboxes increased to 999,999 (silver and high-value items display correctly)
- ItemBuffs table columns auto-size to content (Name, Tier, Type all readable)
- Removed: Export as JSON/CDUMM ZIP (replaced by Community Mod Loader), Dragon menu items

### v2.5.4

**New: Unlock All Knowledge (Abyss Gates tab)**
- Injects ALL 5,500+ knowledge entries from game data
- Unlocks: most skills, ALL dyes/recipes/crafting manuals, full map + all fast travel, infinite ammo key items
- Big warning dialog — map reveal CANNOT be undone
- Auto-save prompt after applying

**Improved: ItemBuffs Editor**
- Rate stat cap removed — rates now support 0-255 (was hardcoded to 15). HealthRegen goes to 50, SkillExp to 10, etc.
- **Edit Selected Stat Only** — click any stat row, set a value, apply to just that one entry without touching others
- **Refinement Level selector** — choose which refinement level to apply presets to (Level 1, Level 2, etc.) instead of all at once
- All auto-save prompts added (Reveal Map, Show Nexus, Unlock Knowledge)

**New: Quest Editor (Tools > Quest Editor)**
- Fix bugged quests blocking progression
- Mark Quest Completed / Reset to In Progress
- Add Quest as Completed (PARC Insert) — insert quests you haven't encountered yet
- 633 quests + 5,450 missions with English display names from game localization
- Quest Database tab — browse all 6,780 quests + missions from game data

**Other**
- Item Effects section hidden (moved to Dev mode)
- Center status banner shows loading progress
- Version 2.5.4

### v2.5.3

**New: Quest Editor (Tools > Quest Editor)**
- Fix bugged quests that are stuck and blocking progression
- Opens in a separate window — main editor stays fast
- Shows all quests and missions from your save with English display names
- Search by quest name (e.g. "Wrestling Match", "Where Rumors Gather")
- **Mark Quest Completed** — skip past broken quests. Game auto-advances to next quest in chain.
- **Reset to In Progress** — undo a completion
- Built-in Save button with backup warning
- 633 quests and 5,450 missions with localized English names from game data

**New: Quest Database Tab**
- Browse all 898 quests + 5,882 missions from game data
- Search by key, internal name, or display name
- Find quest keys for any quest in the game, even ones you haven't encountered

**Other**
- Center status banner shows loading progress prominently above tabs
- Improved PARC external PO fixup — prevents false sentinel matches that corrupted FieldSaveData
- Re-Fog Map button (inverse of Reveal Map)
- Version 2.5.3

### v2.5.2

**New Features**
- **Re-Fog Map** — Inverse of Reveal Map. Covers your entire map in fog again. Available in both Abyss Gates and Debug tabs.
- **Abyss Gates tab** — Now a regular tab, no longer hidden behind Dev/Experimental mode.

**UI Improvements**
- Re-Fog button moved after Step 2 for clearer flow
- Step-by-step instructions with warning label for the reveal + nexus process

### v2.5.1

**New Features**
- **Show All Nexus Gate Locations** — Reveals all nexus/abyss gate locations on your map as ??? markers. Two-step process: Step 1 reveals fog of war, Step 2 injects community knowledge entries. Works on any save.
- **Improved PARC insertion safety** — Fixed false sentinel matching in external PO fixup. Prevents corruption of FieldSaveData gimmick lists when modifying other blocks. POs are now validated against the sentinel+12 pattern before being shifted.

**Bug Fixes**
- Fixed critical bug where knowledge injection corrupted FieldSaveData on saves with large gimmick lists (805+ blocks). False sentinel matches in UUID/timestamp data were being incorrectly shifted as payload offsets.
- Community knowledge data now loaded from bundled JSON instead of requiring community save file.

### v2.5.0

**New Features**
- **PARC Insert** — Add new items to inventory without donors. Full tree verification (63,000+ offsets validated) ensures no crashes. Currently limited to Narima's Horn (Dragon CD reset) while more items are tested.
- **Clone Selected to Vendor** — Clone any sold item into a new vendor entry. Search by item name, pick a same-type target. Buy it back for a fully correct item.
- **Item Search Dialog** — Search by item name across all insertion/clone flows. Shows name, key, and category.
- **Type-for-type rule** — Cross-type swaps (Glove->Helm) produce unequippable items. Editor now warns about this.
- **ItemBuffs Tab** — Edit base stats on any item in game data files with presets (God Mode, Max DDD, etc.)
- **F-Key Navigation** — F1-F12 shortcuts to switch tabs
- **Split Stack** — Split 1 from a stack without consuming the whole stack
- **Font Scaling** — 100%/125%/150%/200% in Edit menu

**Bug Fixes**
- Repurchase list always re-scans fresh (no stale data)
- Dragon cooldown offset corrected
- All reload messages updated (may require 2 reloads but not usually)

### v2.4.9.5

**Features**
- **Font Size Changer** — Scale UI to 100%, 125%, 150%, 200% (Edit menu, persists across restarts)
- **Swap 1 from Stack** — Consume only 1 unit when swapping stacked items
- **Item Effect Swap (GPatch)** — Swap consumable use-effects between items via effect hash patching
- **Community Packs** — BlackStar Dragon No Cooldown + 10 Dye Packs

**Bug Fixes**
- Repurchase list fix (scanner now re-scans fresh, no stale data)
- Dragon cooldown reduction offset corrected (ds+163 instead of ds+156)
- Mount tab removed (patches were not effective)

### v2.4.9

**New Features**
- **Max Stacks built-in** — Checkbox "Also apply Max Stacks" (99/999/9999) in ItemBuffs. Applied together with buffs in one click. Replaces FatStacks mod.
- **Storage Expansion (700)** — GPatch: warehouse, bank, camp storage to 700 slots. Structural parsing, survives updates. Player inventory untouched.
- **My Inventory button** — ItemBuffs: instantly list your save items that exist in iteminfo
- **PABGB Browser** — Dev mode: browse all 118 game data files with hex dump
- **Vendor-only donor filter** — Filter pack donors to vendor repurchase items only
- **Diagnostic tool** — crimson_diagnostic.py for debugging game file issues
- **10x faster load times** — C-backed ChaCha20 decryption
- **Loading progress dialog** — Shows decrypting/scanning/populating steps

**Game Patches**
- GPatch is now a normal tab (not behind Dev mode)
- Mount patch renamed to "Mount Death Respawn (1s)" — clarifies it's death respawn, not Dragon summon
- Max Inventory Slots patch removed (caused loot bugs)

**Bug Fixes**
- Slot limit removed — items in slots 200+ now visible (Bismuth Ore fix)
- Storage expand crash fixed (missing pamt_path argument)
- PAPGT integrity retry on failure
- Linux icon cache path crash fixed
- Bag Space Fix removed (obsolete)
- Max All Knowledge hidden (not working, needs research)

### v2.4.8

**New Features**
- **ItemBuffs stat editing rewrite** — Real binary format support (flat2/flat1/rate stat types). Max values, swap stat types within same class
- **Max Stacks built-in** — Replace FatStacks mod. Checkbox in ItemBuffs tab to set all stackable items to 99/999/9999. Applied together with buffs in one click. Survives game updates.
- **Storage Expansion (700)** — Expand warehouse, bank, camp storage to 700 slots via GPatch. Does NOT touch player inventory (avoids loot bugs)
- **Equipment Sets** — Create, share, and apply stat buff presets. Right-click items to add to sets. Import/Export via JSON, sync from GitHub
- **My Inventory button** — Instantly list items from your loaded save in ItemBuffs tab
- **Category filter on Swap tab** — Filter by All, Has Template, Equipment, Armor, Weapon, etc.
- **Socket search** — Search box on each socket slot to filter gems by name
- **73 missing Abyss Gears added** — Socket tab now has 189 gems (was 116)
- **PABGB Browser** — Browse any game data file in Dev mode (118 files)
- **Guides menu** — In-app step-by-step guides for every tab
- **View menu tab navigation** — Quick-jump to any tab
- **Save browser right-click** — Open File Location, Copy Path, Load Save
- **Unknown Items filter** — Find unrecognized item keys in inventory
- **Loading progress dialog** — Shows decrypting/scanning/populating steps
- **10x faster load times** — C-backed ChaCha20 crypto
- **Linux update check** — Directs Linux users to GitHub Releases
- **Vendor-only donor filter** — When applying packs, filter donors to vendor items only
- **Diagnostic tool** — crimson_diagnostic.py for debugging game file issues

**Game Patches (GPatch)**
- Mount Death Respawn (1s) — renamed from "No Mount Cooldown" (was misleading, only affects death respawn, not Dragon summon)
- Storage Expansion to 900 — structural parsing, survives game updates
- Max Inventory Slots patch removed (caused loot/pickup bugs)

**Bug Fixes**
- Tree-safe scanner — no more false matches in missions/skills/field data
- Template swap offset fix (was off by 4 bytes)
- Slot limit removed — items in slots 200+ now visible (was hiding 14+ items for users with expanded inventory)
- Bismuth Ore and similar items now detected correctly
- StoragePatcher backup method fixed
- Better error message for corrupted backups
- Template DB caching (was reloading JSON 66 times on startup)
- Vendor scan deduplication — faster load times
- PAPGT integrity update retry on failure
- Linux icon cache path fix (was crashing on startup)

### v2.4.7

**New Features**
- Edit item buffs — items with Defense can be maxed to 9999+ for base value
- Category filter for swap tab to make searching easier

**Bug Fixes**
- Binary scanning was causing false matches with missions and skills data. Tool now uses tree-based system that searches only inside inventory blob
