# OpenVoxel ModLoader

Unofficial modding layer for [OpenVoxel](https://open-voxel.net) **0.0.8**. It runs the game through the official launcher and never patches the game or launcher files: a Java agent wraps the client in memory, and server features are a plugin for the official dedicated server.

**Website & docs:** https://openvoxel-modloader.github.io

## Download

| | Latest release | What's inside |
|---|---|---|
| **Client** | [ModLoader-Client-v1.0.0-vgame-0.0.8.zip](https://github.com/OpenVoxel-ModLoader/ModLoader-Client/releases/latest/download/ModLoader-Client-v1.0.0-vgame-0.0.8.zip) | Loader jar, `launch.bat` / `launch.ps1` / `launch.sh`, `instance/` (mods, config, lang, resourcepacks, sounds, music) |
| **Server** | [ModLoader-Server-v1.0.0-vgame-0.0.8.zip](https://github.com/OpenVoxel-ModLoader/ModLoader-Server/releases/latest/download/ModLoader-Server-v1.0.0-vgame-0.0.8.zip) | Core plugin jar, `start.bat` / `start.ps1` / `start.sh`, `server.properties.yml`, `mods/` |

**Client:** unzip next to `OpenVoxelLauncher.exe`, run `launch.*`, select version **0.0.8-Debug** in the launcher, press PLAY. Mods go into `ModLoader-Client/instance/mods`.

**Server:** unzip anywhere, put the official `openvoxel-server-0.0.8-SNAPSHOT.jar` at `server/openvoxel-server.jar`, drop plugins into `mods/`, run `start.*`.

## What it adds

- Minecraft-style menus, Survival and Creative modes, first-person hand/held block, F3 debug screen
- Hunger, armor, swords, pickaxes/shovels/axes with mining times, item drops (Q), fall damage, sneaking/sprinting, rebindable controls
- Crafting (2x2 and crafting table), chests, beds, a tabbed creative inventory
- Minecraft skins (64x32 / 64x64 / 128x128, both layers, Steve/Alex), capes, elytra wings, in-game skin upload
- Chat colors (`&a`, `&#rrggbb`), command history, Tab completion, `/help`, scrolling
- Resource packs, sound packs, music folder, languages (EN/ES, mods can add more)
- Server: interactive console, colored chat/commands, utility commands, plugin loading from `mods/`
- A small Java API for mods: commands, translations, config, items, recipes, HUD drawing, engine events

## Repositories

| Repository | Purpose |
|---|---|
| [ModLoader-Client](https://github.com/OpenVoxel-ModLoader/ModLoader-Client) | Client loader (Java agent + ASM), launch scripts, instance layout |
| [ModLoader-Server](https://github.com/OpenVoxel-ModLoader/ModLoader-Server) | Server core plugin, start scripts |
| [ModLoader-ModsExamples](https://github.com/OpenVoxel-ModLoader/ModLoader-ModsExamples) | Example client mods and a Gradle `mod-template` |
| [ModLoader-Server-Example](https://github.com/OpenVoxel-ModLoader/ModLoader-Server-Example) | Example server plugin (Hunger Games) |
| [ModLoader](https://github.com/OpenVoxel-ModLoader/ModLoader) | Umbrella repo: architecture, changelog, setup scripts |
| [openvoxel-modloader.github.io](https://github.com/OpenVoxel-ModLoader/openvoxel-modloader.github.io) | Website: docs, tutorials, mod catalogue |

## Making mods

1. Copy [`mod-template`](https://github.com/OpenVoxel-ModLoader/ModLoader-ModsExamples/tree/master/mod-template).
2. Implement `ClientMod` (`onLoad`, `onGameReady`, `onFrame`, `onShutdown`) and use `ModContext` for commands, chat, config, items and recipes.
3. Build with Gradle or `build.sh` / `build.bat` against the game jar and the loader jar (Java 11).
4. Drop the jar into `instance/mods`.

Start with [Your first mod](https://openvoxel-modloader.github.io/#/tutorials/first-mod) and the [API reference](https://openvoxel-modloader.github.io/#/docs/api). Server plugins: [Your first server plugin](https://openvoxel-modloader.github.io/#/tutorials/server-plugin).

## Requirements

- OpenVoxel installed through the official launcher (version 0.0.8-Debug downloaded)
- Windows or Linux; the game ships its own Java 11 runtime
- For developing mods: JDK 11+

All projects are MIT licensed. OpenVoxel is a separate project; this organization is not affiliated with its developers.
