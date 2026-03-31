CRIMSON DESERT SAVE EDITOR — Language Pack Guide
=================================================

THERE ARE TWO TYPES OF TRANSLATION FILES
-----------------------------------------
1. NAME PACKS (this folder — language/names_XX.json)
   - Translates GAME DATA: item names, quest names, knowledge names
   - ~17,000 translated names per language
   - Downloaded separately, not bundled with exe
   - Install via Settings > "Import Translation" or "Download Name Pack"

2. UI TRANSLATIONS (locale/XX.json — bundled with exe)
   - Translates the EDITOR INTERFACE: tab names, buttons, labels, tooltips
   - ~166 UI strings
   - Saved as locale/ko.json, locale/ja.json, etc. next to the exe
   - Currently only English (en.json) and Japanese (ja.json) exist
   - To create one: copy locale/en.json, rename to locale/ko.json,
     translate the values, restart the editor

These are independent. You can have Korean item names (name pack)
with an English editor UI, or vice versa.


HOW TO INSTALL A NAME PACK (Game Data Translation)
---------------------------------------------------
1. Download a names_XX.json file from this folder
   (e.g. names_ko.json for Korean)

2. In the Save Editor, go to Settings (Edit menu or gear icon)

3. Click "Import Translation" and select the downloaded .json file

4. Restart the editor — item/quest/knowledge names will now show
   in your selected language

ALTERNATIVE: Click "Download Name Pack" in Settings to download
directly from GitHub without manually saving the file.


HOW TO INSTALL A UI TRANSLATION (Editor Interface)
---------------------------------------------------
1. Copy locale/en.json from next to the exe
2. Rename to locale/ko.json (or your language code)
3. Open in a text editor and translate the values (not the keys)
4. Restart the editor and select the language in Settings


AVAILABLE LANGUAGES
-------------------
names_de.json       - Deutsch (German)
names_es.json       - Espanol (Spanish)
names_es-mx.json    - Espanol Mexico (Mexican Spanish)
names_fr.json       - Francais (French)
names_it.json       - Italiano (Italian)
names_ja.json       - Japanese
names_ko.json       - Korean
names_pl.json       - Polski (Polish)
names_pt-br.json    - Portugues Brasil (Brazilian Portuguese)
names_ru.json       - Russian
names_tr.json       - Turkce (Turkish)
names_zh.json       - Simplified Chinese
names_zh-tw.json    - Traditional Chinese


FORMAT FOR TRANSLATORS
----------------------
Each language pack is a JSON file with this structure:

{
  "_language_name": "Korean",
  "items": { ... },
  "quests": { ... },
  "missions": { ... },
  "knowledge": { ... },
  "stores": { ... }
}

IMPORTANT: The file MUST have a "_language_name" key at the top level.
Without it, the editor will show an error:
  "missing language name field"

To create a new translation:
1. In Settings, click "Export English Template"
2. This creates a base file with all English strings
3. Translate the values (not the keys)
4. Add "_language_name": "Your Language Name" at the top
5. Save as names_XX.json and share with the community


TROUBLESHOOTING
---------------
Error: "missing language name field"
  -> Open the .json file in a text editor
  -> Add this line near the top (after the first {):
     "_language_name": "Korean"
  -> Save and try importing again

Error: "invalid JSON"
  -> Make sure the file is valid JSON (no trailing commas, proper quotes)
  -> Use a JSON validator: https://jsonlint.com/

Names not changing after import?
  -> Restart the editor after importing
  -> Check Settings to confirm the language is selected
