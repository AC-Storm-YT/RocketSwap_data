# Rocket Swap

Rocket Swap is a Windows mod manager and item swapper for Rocket League. It helps you import, organize, preview, select, launch, and restore Rocket League cosmetic mods.

> Rocket Swap is not affiliated with, endorsed by, or sponsored by Psyonix, Epic Games, or Rocket League. Use mods responsibly and keep backups.

---

## Status

Rocket Swap is currently in private beta.

Access is controlled through Discord roles. For now, only the **Beta Tester** role grants app access. Guest and staff-style roles can appear in the profile UI, but they do not grant any kind of app access.

---

## Security & False Positives

Rocket Swap modifies local Rocket League package files when applying mods, restores vanilla files from backups, launches Rocket League through your installed launcher, and includes helper scripts for swap generation. Antivirus tools may flag this type of behavior because it looks similar to generic patching or automation software.

Rocket Swap does not:

* Steal Discord credentials.
* Read private Discord messages.
* Ask for your Discord password.
* Hook into Rocket League memory.
* Include paid/proprietary Rocket League item files.
* Require your Epic Games or Steam password.

Rocket Swap does:

* Ask Discord for identity and server-role verification.
* Store a protected local auth session under `%AppData%\Rocket Swap\Auth`.
* Store a local install ID after user consent.
* Back up original game files before replacing them.
* Restore launcher-applied mods after Rocket League closes.

---

## Core Features

* Discord OAuth login with Cloudflare Worker role validation.
* Private beta access using the `canUseApp` permission.
* Rocket League install-folder detection and validation.
* Mod grid with search, category filters, selectable cards, previews, paint tags, quality tags, and replacement labels.
* Launcher flow that applies selected mods only when launching the game.
* Automatic restore of launcher-applied mods after Rocket League closes.
* Import support for `.upk`, `.bnk`, Rocket Swap exports, mod packs, and supported AlphaConsole-style ZIPs.
* Export support for single mods and multi-mod packs.
* Safe removal flow that restores vanilla files before deleting active mods.
* Swaps tab powered by the embedded Rocket Swap engine.
* Wheel paint generation and colored Gold Rush boost generation.
* Icon cache synced from the RocketSwap data repository.
* Multiple UI themes, streamer mode, and optional error logging.

---

## Supported Mod Categories

Rocket Swap organizes installed mods under the local `mods` folder next to the app executable.

Standard categories:

* Antenna
* Avatar Border
* Banner
* Body
* Boost
* Boost Audio
* Decal
* Engine Audio
* Goal Explosion
* Hat / Topper
* Paint
* Trail
* Wheels

Custom texture categories:

* Custom Decals
* Custom Balls
* Custom Boost Meter

Generated/special mod flows:

* Painted wheels
* Colored Gold Rush boost
* Custom decal packs
* Custom ball textures
* Custom boost meter textures

---

## Discord Access & Privacy

Rocket Swap uses Discord OAuth so the app can verify that the signed-in account belongs to the official Rocket Swap Discord and has the required beta role.

Current Discord entry point:

[Join the Rocket Swap Discord](https://discord.gg/dGxtZagQgB)

The app asks for Discord authorization in the login window. After approval, the browser shows a short code that is pasted back into Rocket Swap.

The auth system validates:

* Discord user identity.
* Server membership.
* Required role membership.
* Whether the account is allowed by the private `permissions.json` file.
* Whether the current install has user consent.

The only app permission currently used by Rocket Swap is:

* `canUseApp`

---

## How To Use

1. Join the official Rocket Swap Discord.
2. Make sure your Discord account has the Beta Tester role.
3. Open Rocket Swap.
4. Accept the local install-ID consent prompt.
5. Click **Authorize with Discord**.
6. Approve the Discord OAuth request in your browser.
7. Paste the generated code back into Rocket Swap.
8. Select your Rocket League installation folder named `rocketleague`.
9. Import mods, generate swaps, or select existing mods.
10. Press **Launch** to apply the selected mods and start Rocket League.

Selected mods become active when Rocket Swap launches the game. After Rocket League closes, launcher-applied mods are restored back to the clean game state.

---

## Launcher

The launcher page handles the full game-start flow for modded sessions.

Supported launcher modes:

* Auto detect
* Epic Games
* Steam
* Heroic

Launcher options include:

* Launch without mods.
* Launch without Easy Anti-Cheat.
* JoyToKey compatibility.
* Manual launcher platform override.

Rocket Swap checks if Rocket League is already running before applying mods. If files were modified for a launcher session, Rocket Swap tracks them and restores them when the game exits.

---

## Swaps Tab

The Swaps tab embeds the Rocket Swap engine directly inside the app.

Current engine:

* Rocket Swap 1.0

The bundled item database currently contains more than 9,000 Rocket League items across 18 categories. The engine lets you choose a target item, choose a donor item, and generate a local mod folder automatically.

Supported swap categories include:

* Body
* Decal
* Wheels
* Rocket Boost
* Goal Explosion
* Trail
* Paint Finish
* Player Banner
* Antenna
* Topper
* Boost Audio
* Engine Audio
* Avatar Border

Some database categories are visible but marked unsupported when the engine cannot safely generate a mod for them yet.

The engine can also generate:

* Painted wheel variants.
* Colored Gold Rush boost variants.

Generated mods are routed into the normal Rocket Swap `mods` folder and then appear in the main mod grid.

---

## Importing Mods

Rocket Swap can import:

* `.upk` files
* `.bnk` files
* Single Rocket Swap export ZIPs
* Rocket Swap mod pack ZIPs named `mods.zip`
* Supported AlphaConsole-style ZIPs

Imported mods are placed into the selected category and named using the item name plus replacement metadata when available.

Rocket Swap blocks unsafe ZIP paths during extraction so archives cannot write outside the intended import folder.

---

## Exporting Mods

The export window lets you select installed mods and create a portable ZIP.

Single-mod exports include:

* Mod files
* Category metadata
* Replacement metadata
* Rocket Swap export manifest

Multi-mod exports create a pack with metadata for every selected mod.

Rocket Swap skips backup files and existing export metadata when building an export.

---

## Removing Mods

The remove window lists installed mods by category and lets you delete selected mods safely.

If a selected mod is currently active, Rocket Swap attempts to restore the vanilla game file from backup before deleting the mod folder. If the restore cannot be completed, the app avoids deleting files that would leave Rocket League in a bad state.

Custom texture categories use the bundled backend restore actions so generated texture changes can be reverted properly.

## Cloudflare Auth Worker

The auth worker lives in:

```text
cloudflare\rocket-swap-auth-worker
```

It handles:

* Discord OAuth callback flow.
* Session signing.
* Discord guild and role validation.
* GitHub-hosted permission config loading.
* Active-user tracking.
* Audit/usage webhooks.
* Health checks.

The private permissions repository should expose a `permissions.json` file. The current app expects that file to define Rocket Swap roles and the `canUseApp` permission.

Never commit secrets. Configure Cloudflare, Discord, GitHub, and webhook tokens as Worker secrets or repository secrets.

---

## Community

[Join the Rocket Swap Discord](https://discord.gg/dGxtZagQgB)