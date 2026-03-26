# Crimson Desert - Offline Save Editor

BIG credits to @Gek a awesome dude from discord who help me with the decryption logic.

A standalone save editor for Crimson Desert. Edit your inventory, swap equipment, change stacks, modify enchants, inject stat buffs, manage sockets — all offline, no mods required in-game.

## Download

Grab `CrimsonSaveEditor.exe` from the release. Single file, no installation needed.

## Features

- **Inventory Editor** — View all items with names/icons, edit stack counts, batch edit, delete items
- **Equipment Editor** — Change enchant level (0-10), endurance, sharpness, duplicate gear for swapping
- **Item Swap** — Transform any item into another with category filters and 2,262 real game templates
- **Repurchase (Vendor Swap)** — The most reliable swap method: sell junk, swap in editor, buy back
- **Socket Editor** — Swap Abyss Gear gems in equipment sockets (189 gems across 30+ categories)
- **ItemBuffs** — Edit base stats on any item in game data (damage, defense, speed, crit, resistances)
- **Equipment Sets** — Create, share, and apply stat buff presets as community sets via GitHub
- **Item Packs** — Download and apply curated item collections from the community
- **Community Mapping** — Help map every item in the game by scanning your saves
- **GPatch** — Optional game file patches (experimental)
- **Give Item** — Pick any item from the database and a donor item to sacrifice
- **Backup/Restore** — Automatic backup before every save, pristine backup support
- **Auto-Find Saves** — Locates save files automatically (Steam, Epic, Game Pass, Linux Proton)
- **Guides Menu** — In-app guides for every tab explaining how to use each feature

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
3. Swap it to the item you want
4. Save, load in-game, buy it back from the vendor

### Sockets (Abyss Gear)
Swap gems in equipment sockets. 189 Abyss Gears available including combat skills, stat buffs, resistances, banes, and gathering bonuses. Empty sockets must have a gem installed in-game first (Witch NPC > Create Socket > Embed Abyss Gear).

### ItemBuffs (Stat Editing)
Edit base stats on ANY item in the game data files. Extract iteminfo, search for items, apply presets:
- **Max All** — Max every stat value (flat to 999,999, rates to Lv 15)
- **Max DDD/DPV/HP** — Max specific stat types
- **Custom** — Pick any stat and set a specific value

Right-click items to add them to **Equipment Sets** — reusable buff presets you can share with the community.

**Requires admin privileges** to write game files. Use Restore Original or Steam Verify Integrity if issues occur.

### Item Packs
Download community item collections from GitHub. Create your own packs to share loadouts with others.

### Community Mapping
Help map every item in Crimson Desert. Scan your saves to discover new item templates and upload them to the community database. The more saves we scan, the more items the editor can support.

## Give Item (Donor System)

Since the save format uses fixed record structures, new items can't be inserted directly. Instead, the **Give Item** feature transforms an existing item into the one you want:

1. Click **Give Item** in the Inventory tab
2. Search and select the item you want, set the quantity
3. Pick a donor item from your inventory to sacrifice
4. Confirm — the donor becomes the target item

**Tip:** Buy cheap materials from a vendor in-game to use as donors.

## Known Limitations

- **No item insertion** — Can't add entirely new items, only transform existing ones (donor system)
- **Equipment stats after swap** — Swapped equipment may show wrong damage/defense until unequip + re-equip
- **Store/Mercenary items** — Read-only, cannot be edited
- **Empty sockets** — Cannot fill empty sockets from the editor, must install a gem in-game first
- **Lobby saves** — Only `save.save` (in-game saves) are supported, not `lobby.save`

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

## Technical Details

The editor handles the full save file crypto pipeline:
- **Decryption:** ChaCha20 (RFC 7539)
- **Integrity:** HMAC-SHA256 verification
- **Compression:** LZ4 HC (high compression)
- **Format:** PARC (Pearl Abyss Reflect Container) binary serialization
- **Game Data:** iteminfo.pabgb stat editing via LZ4 repack into PAZ archives

## Credits

- Save format reverse engineering and editor by the Crimson Desert modding community
- @Gek — save decryption logic
- @Potter420 — iteminfo structural parser
- Item names maintained by community contributors
- Item icons from [questlog.gg](https://questlog.gg/crimson-desert)
- LZ4 compression by Yann Collet (BSD license)

---

## Changelog

### v2.4.8 — Releasing Soon

**New Features**
- **ItemBuffs stat editing** — Edit base item stats in game data. Example: max Defense to 999,999. Real binary format support (flat2/flat1/rate stat types)
- **Equipment Sets** — Create, share, and apply stat buff presets. Right-click items to add to sets. Import/Export via JSON, sync from GitHub
- **Category filter on Swap tab** — Filter by All, Has Template, Equipment, Armor, Weapon, Shield, Accessory, etc.
- **Socket search** — Search box on each socket slot to filter gems by name
- **73 missing Abyss Gears added** — Socket tab now has 189 gems (was 116), including Greater Banes, Moon Slashes, Infinite Arrows, Boss skills
- **Guides menu** — In-app guides for every tab with step-by-step instructions
- **View menu tab navigation** — Quick-jump to any tab from the View menu
- **Save browser right-click** — Open File Location, Copy Path, Load Save
- **Unknown Items filter** — Filter inventory to show only unrecognized item keys
- **Community tab purpose label** — Explains the community mapping mission

**Changelog**
- Category filter dropdown on swap tab (All, Equipment, Armor, Weapon, etc.)
- "Has Template" option shows only the 2,262 items with real game data
- 2,262 templates loaded (was 585)
- Smart buff application: edits VALUE only for matching stats, preserves refinement progression
- Description label under each preset/stat explaining what it does
- Confirmation dialog shows strategy (SAFE EDIT / REPLACE / OVERWRITE) and what gets touched
- "Set currently loaded folder as default" checkbox for Linux/custom paths
- Linux Steam Proton path auto-detection
- Warning popup after saving reminds users to save in-game before more edits
- Red warning on Swap tab about equipment disappearing — use Repurchase instead
- Socket tab help text explaining empty socket limitations
- Inventory info label explaining save vs in-game display differences
- Template DB caching — no more reloading JSON 66 times on startup
- Vendor scan deduplication — faster load times
- Dye pack split into 10 packs of 5 (was 1 pack of 50, caused issues)
- Waypoint and Faction tabs hidden behind Dev mode (WIP)
- Template Swap buttons hidden behind Dev mode (bitmask corruption bug)
- Potter420 credit in red

**Bug Fixes**
- Tree-safe scanner — binary scanning was matching items in missions/skills/field data. Now only scans inside inventory/equipment/store PARC blocks
- Template swap offset fix — was off by 4 bytes, corrupting saves
- Better error message for corrupted backup files
- Schema parser fixes: num_root_entries is u32 not u16, field_count is u16 not u8

### v2.4.7

**New Features**
- Edit item buffs — items with Defense can be maxed to 9999+ for base value
- Category filter for swap tab to make searching easier

**Changelog**
- Category filter dropdown on swap tab
- Template Swap field-level patching
- block_size detection for template swap
- 2,262 templates loaded (was 585)
- Tree-safe scanner + swap — no more writes outside item blocks
- Smart buff application with strategy dialog
- "Set currently loaded folder as default" checkbox
- Linux Steam Proton path auto-detection

**Bug Fixes**
- Binary scanning was causing false matches with missions and skills data. Tool now uses tree-based system that searches only inside inventory blob
