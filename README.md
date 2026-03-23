# Crimson Desert - Offline Save Editor

A standalone save editor for Crimson Desert. Edit your inventory, swap equipment, change stacks, modify enchants — all offline, no mods required in-game.

## Download

Grab `CrimsonSaveEditor.exe` from the release. Single file, no installation needed.

## Features

- **Inventory Editor** — View all items with names, edit stack counts, batch edit multiple items
- **Equipment Editor** — Change enchant level (0-10), endurance, and sharpness on equipment
- **Item Swap** — Transform any item into another by selecting from the 6000+ item database
- **Give Item** — Pick any item from the database and a donor item to sacrifice — the donor becomes the new item
- **Item Database** — Browse, search, and filter all known items. Sync latest names from GitHub
- **Backup/Restore** — Automatic backup before every save. Restore from any previous backup
- **Auto-Find Saves** — Automatically locates your save files (Steam, Epic, Game Pass)

## How To Use

1. It's recommended that you **Close the game** HOWEVER it is not required it still works.
    (the editor works on save files directly)
3. Run `CrimsonSaveEditor.exe`
4. Go to **File > Open Save File** or use **Tools > Auto-Find Save**
   - Saves are typically at: `%LOCALAPPDATA%\Pearl Abyss\CD\save\<steamid>\slot0\save.save`
5. Make your edits
6. **File > Save** to write changes (a backup is created automatically)
7. Launch the game and load your save

## Tabs

### Inventory
Browse all items in your save. Select one or more items, set a new stack count, and click **Set Stack**. Use **Give Item** to add a new item by sacrificing a donor.

Store and Mercenary items are read-only (editing them corrupts the save).

### Equipment
Shows all equipment with enchant, endurance, and sharpness values. Select items and set new values. Enchant affects attack/defense (game recalculates from item type + enchant level).

### Item Swap
Select an item from the Inventory tab, switch to this tab, pick the target item from the database, and click Swap. Works for equipment-to-equipment and item-to-item swaps.

**Note:** Swapped equipment may show wrong icons or stats until you unequip and re-equip in-game. This is cosmetic — the game recalculates stats from the item type.

### Item Database
Browse all 6000+ known items. Search by name or key. Click **Sync from GitHub** to pull the latest community item names.

### Backup/Restore
Lists all automatic backups with timestamps. Select one and click Restore to roll back. You can also manually create a backup at any time.

## Give Item (Donor System)

Since the save format uses fixed record structures, new items can't be inserted directly. Instead, the **Give Item** feature transforms an existing item into the one you want:

1. Click **Give Item** in the Inventory tab
2. **Step 1:** Search and select the item you want from the database, set the quantity
3. **Step 2:** Pick a donor item from your inventory to sacrifice (same-category donors are highlighted)
4. Confirm — the donor becomes the target item

**Tip:** Buy cheap materials from a vendor in-game to use as donors.

## Technical Details

The editor handles the full save file crypto pipeline:
- **Decryption:** ChaCha20 (RFC 7539)
- **Integrity:** HMAC-SHA256 verification
- **Compression:** LZ4 HC (high compression) — saves are typically 10-15% smaller after editing
- **Format:** PARC (Pearl Abyss Reflect Container) binary serialization

The smaller file size after editing is normal. The game uses standard LZ4 (fast mode) while the editor uses LZ4 HC (high compression). The decompressed data is identical — just packed more efficiently.

## Item Names

Item names are bundled with the editor (6000+ items). The database is community-maintained at:

**[github.com/NattKh/CrimsonDesertCommunityItemMapping](https://github.com/NattKh/CrimsonDesertCommunityItemMapping)**

Use the **Sync from GitHub** button in the Item Database tab to pull updates. If no local database is found on first launch, it downloads automatically.

## Known Limitations

- **No item insertion** — Can't add entirely new items, only transform existing ones (donor system)
- **Equipment stats after swap** — Swapped equipment may show wrong damage/defense until unequip + re-equip
- **Store/Mercenary items** — Read-only, cannot be edited
- **Lobby saves** — Only `save.save` (in-game saves) are supported, not `lobby.save`

## Save File Locations

| Platform | Path |
|----------|------|
| Steam | `%LOCALAPPDATA%\Pearl Abyss\CD\save\<id>\slot0\save.save` |
| Epic | `%LOCALAPPDATA%\Pearl Abyss\CD_Epic\save\<id>\slot0\save.save` |
| Game Pass | `%LOCALAPPDATA%\Pearl Abyss\CD_GamePass\save\<id>\slot0\save.save` |

Each `slot` folder is a separate save slot. `slot0` through `slot104` etc.

## Troubleshooting

**"HMAC mismatch" warning on load**
The save may be from a different game version or was partially corrupted. The editor will still try to load it.

**Game doesn't load the edited save**
Restore from the automatic backup (Backup/Restore tab) and try again. Make sure the game is fully closed before editing.

**No items shown after loading**
The save file might be a lobby save (`lobby.save`) which has minimal data. Use `save.save` instead.

## Credits

- Save format reverse engineering and editor by the Crimson Desert modding community
- Item names maintained by community contributors
- LZ4 compression by Yann Collet (BSD license)
