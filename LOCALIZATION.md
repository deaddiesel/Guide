# Localization Guide

Translation files live in `src/main/resources/assets/guide/lang/`.
Currently supported: `en_us.json`, `ru_ru.json`.

## Key naming convention
- `guide.theme.*` — theme display names
- `guide.button.*` — UI button labels
- `guide.tooltip.*` — hover tooltips
- `guide.error.*` — error messages
- `guide.video.*` — media player strings
- `item.guide.*` — item names
- `key.guide.*` — keybind descriptions

## Adding a new language
1. Copy `en_us.json` → `<locale>.json` (e.g. `de_de.json`)
2. Translate all values, do NOT change keys
3. Open a PR

## Note on comments
JSON lang files cannot contain comments — Minecraft parses them strictly.
Keep translations clean and rely on this document for context.
