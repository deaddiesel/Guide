# Contributing to Guide

Thanks for your interest in improving Guide! Here's how to help.

## Reporting bugs

Before opening an issue:
- Search existing issues (open AND closed) — your bug may already be reported
- Try the latest version of the mod — it may already be fixed
- Test in **single player** first. If it works in SP but not on a server, that's a strong clue

When opening a bug report, please include:

1. **Steps to reproduce.** Not "it crashes" but "typing `@image:` in a chapter with a missing PNG crashes the guide screen."
2. **Expected vs actual behavior.** What did you expect, what happened instead.
3. **Minecraft version + loader.** E.g. `1.21.1 NeoForge 21.1.248` or `1.20.1 Forge 47.4.20`.
4. **Guide mod version.** E.g. `1.4.0 (NeoForge)`.
5. **Other mods that might interact.** Especially: AutoModpack, JEI, anything modifying resource packs.
6. **Client log** for non-crash issues (`latest.log` from `.minecraft/logs/`), uploaded to https://mclo.gs or https://pastebin.com.
7. **Crash report** for crashes (`crash-reports/crash-*.txt`), uploaded the same way.

Issues without reproduction steps will be closed.

## Feature requests

Feature requests are welcome, but:
- Explain **why** you need it, not just what.
- Describe how you'd expect it to work.
- Check the roadmap first — it might already be planned.

I don't guarantee to implement everything, but I read every request.

## Pull requests

Please **open an issue or ask on Discord first** before sending a PR, except for:
- **Translation fixes** — send freely.
- **Typo fixes in docs** — send freely.

Pull requests must:
- Compile and run.
- Not break existing functionality.
- Follow the existing code style.

## Translations

Translations live in `src/main/resources/assets/guide/lang/`. Currently supported:
- `en_us.json`
- `ru_ru.json`

To add a new language:
1. Copy `en_us.json` → `<locale>.json` (e.g. `de_de.json`, `zh_cn.json`).
2. Translate the **values**, not the keys.
3. Open a PR.

**Do not use automatic translators.** Machine translations tend to miss context.

## Where else to get help

- **Discord:** https://discord.gg/GuRnzfp8f9
- **CurseForge comments:** https://www.curseforge.com/minecraft/mc-mods/guide/comments
- **Modrinth:** https://modrinth.com/mod/guide-mod
