# Rocket Swap

Rocket Swap is a Windows mod manager and visual-customization toolkit for Rocket League. It organizes cosmetic mods, creates item and title swaps, provides optional overlays and quality-of-life tools, launches the game through supported platforms, and restores launch-managed files after each session. Workshop maps, Custom Sounds, and Custom Car Colors intentionally remain applied until you use their restore controls.

> [!IMPORTANT]
> Rocket Swap is an independent community project. It is not affiliated with, endorsed by, or sponsored by Psyonix, Epic Games, or Rocket League.
>
> Third-party mods are permitted only when they comply with the [Epic Games Terms of Service](https://legal.epicgames.com/epicgames/tos) and [Rocket League Code of Conduct](https://www.rocketleague.com/code-of-conduct). Rocket Swap modifies local game and profile files and includes optional security-sensitive features. These changes are not officially supported and may carry account or system risk.
>
> Use Rocket Swap entirely at your own risk and keep its backups intact.

## Project status

Rocket Swap is currently in private beta. This README reflects desktop client **v1.5.5**. Access is verified through Discord and depends on the permissions returned by the Rocket Swap authentication service.

[Join the Rocket Swap Discord](https://discord.gg/dGxtZagQgB)

## Feature overview

### Mods and visual swaps

- Import, search, filter, preview, equip, export, and safely remove Rocket League mods.
- Build local visual item swaps from a catalog of more than 9,000 items.
- Swap supported painted variants and configure a custom Gold Rush boost color.
- Replace an owned/equipped player title with another catalog style or design a custom local title with color and glow controls.
- Import Rocket Swap archives and supported AlphaConsole-style custom textures.
- Browse BakkesPlugins workshop maps and install them over a selected Labs arena with per-arena backup and restore.

### Tracker, overlays, and customization tools

- Track live match data, recent matches, session performance, player information, score, and ball speed.
- Build draggable in-game tracker overlays for rank, MMR, score, session record, player stats, match events, and recent matches.
- Display a configurable controller or keyboard-and-mouse input overlay.
- Create up to 20 custom Quick Chat bindings for keyboard or controller.
- Replace 11 supported game sound events with short custom audio clips.
- Add custom primary and accent rows to the garage color palette, including gradients.
- Spoof the rank/MMR displayed by the local client for supported playlists.
- Optionally publish Rocket Swap and available match context through Discord Rich Presence.

### Launch and recovery

- Launch Rocket League through Epic Games, Steam, or Heroic, with automatic detection or a manual platform override.
- Apply selected launch-managed changes and restore original packages, proxy state, and temporary launch assets after the game exits, while preserving new profile progress through a protected working mirror.
- Launch without selected mods or start JoyToKey automatically when it is installed.
- Recover interrupted item, title, profile, custom-texture, workshop-map, and optional start-screen operations.
- Check for Rocket Swap updates and block incompatible modification workflows when the installed Rocket League build is unsupported.

## Requirements

- Windows 10 or Windows 11.
- Rocket League installed through Epic Games, Steam, or Heroic.
- An Internet connection at every startup for Discord session validation and required app/game compatibility checks, plus online features such as news, rank lookups, and workshop maps.
- A Discord account with access granted by the Rocket Swap server.
- Permission to approve Windows elevation when a feature needs protected game, launcher, hosts-file, certificate, or proxy changes.

A source build requires the .NET 10 SDK. A framework-dependent binary also requires the .NET 10 Desktop Runtime unless its installer bundles that runtime.

## Getting started

1. Download and install Rocket Swap from a project link you trust.
2. Start the app, review the Terms of Service and Privacy Policy, select the acknowledgement, and choose **Accept & Continue**.
3. Authorize with Discord in your browser, then return the generated code to Rocket Swap when prompted. The app creates an app-specific Windows device key; it does not identify the PC by collecting hardware serial numbers.
4. Select the Rocket League installation folder named `rocketleague`.
5. Import a mod or configure an item, title, overlay, or other visual feature.
6. Select launch-managed mods under **Equip Items**, then open **Launch**.
7. Start Rocket League through Rocket Swap so it can stage and later restore the selected changes.

Do not force-close Rocket Swap while it is applying or restoring files. The app blocks unsafe navigation and shutdown during critical operations, but an interrupted process may still need startup recovery.

## App sections

| Section | Purpose |
| --- | --- |
| **Dashboard** | View account and game status, Rocket League news, changelog entries, recent app information, and quick actions. |
| **Item Swapping** | Choose an owned/equipped target, a visual donor from the same item slot, and compatible paint settings. |
| **Equip Items** | Search the installed mod library, browse categories, preview and select mods, and open import, export, or removal tools. |
| **Workshop Maps** | Search and filter BakkesPlugins maps, install one over a selected Labs arena, and restore the original arena. |
| **Tracker** | Enable live tracking and view Overview, Analytics, Matches, Players, Overlays, and Settings. |
| **Overlay** | Configure and run the controller or keyboard-and-mouse input display. |
| **Titles** | Create catalog-based title swaps or a custom local title and select the generated visual for a Rocket Swap launch. |
| **Fake Rank** | Change the rank and MMR shown by the local client for supported playlists. |
| **Name Spoofing** | Arm an optional, match-visible display-name substitution for the next Rocket Swap launch. |
| **Miscellaneous** | Open Custom Quick Chat, Custom Sounds, and Custom Car Colors. |
| **Launch** | Choose the platform and launch options, apply selected changes, start the game, and monitor restoration. |
| **Guide** | Read the in-app quick start, feature notes, and recovery guidance. |
| **Settings** | Select the game folder, check for updates, verify game files, create a system report, choose a language/theme, and control Discord Rich Presence. |
| **Console** | Inspect app, launcher, backend, compatibility, and restore activity. |
| **Account/Profile** | View access roles and permissions, refresh or change the authorized PC, sign out, and customize the local profile banner/accent. |

Some modification pages are temporarily locked while Rocket League is running or a restore is pending. Monitoring pages such as Dashboard, Tracker, Overlay, Launch, and Console remain available when it is safe to show them.

## Mods and supported imports

Rocket Swap keeps its installed mod library beside the executable:

```text
mods\<Category>\<Mod Name>\
```

Standard categories include Antenna, Avatar Border, Banner, Body, Boost, Boost Audio, Decal, Engine Audio, Goal Explosion, Hat/Topper, Paint, Player Anthem, Titles, Trail, and Wheels.

Supported custom texture categories are Custom Decals, Custom Balls, and Custom Boost Meter. Although older importer labels may mention Custom Bodies or Custom Wheels, those categories are not available in the current **Equip Items** flow. Paint compatibility continues to evolve, so some item and paint combinations may remain at their default color.

The importer accepts:

- Individual `.upk` and `.bnk` packages.
- Single-mod Rocket Swap export archives.
- Rocket Swap mod-pack archives, conventionally named `mods.zip`.
- Supported AlphaConsole-style ZIP archives, including recognized custom-texture layouts.

You can drag supported files into the importer or browse for them. Generated item and title swaps are saved into the same library and selected through the normal **Equip Items** launch flow.

The export tool creates a portable ZIP for one selected mod or a `mods.zip` pack for multiple selections. Safe removal restores an active standard mod or custom texture before deleting it and retains any backup still used by another mod. If Rocket Swap cannot restore a selected mod safely, it leaves that mod in place and reports the problem.

## Item Swapping

Item Swapping uses a two-step visual replacement:

1. Select the item you own or have equipped. This is the target whose identity remains in the inventory.
2. Select the item you want it to look like from the same compatible slot.
3. Choose a supported paint, then generate and select the swap for the next launch.

The catalog supports search, item-slot and rarity filtering, artwork previews, and an optional **Show Owned Only** filter. To refresh owned-item detection, start Rocket League to the main menu, close it normally, and reopen Rocket Swap so it can read the updated local inventory cache.

Rocket Swap checks full, partial, or unsupported paint compatibility before generating a swap. Custom Gold Rush color controls are available when Gold Rush is the visual donor. Generated choices persist between app restarts, but only one selected swap can target the same equipped item at a time.

Item swaps are visual substitutions. They do not grant items, change ownership, create tradable inventory, or alter server-side progression.

## Titles

The Titles page has two workflows:

- **Catalog swap:** choose a source title you own or have equipped, then choose the title style to display locally.
- **Custom title:** choose the owned/equipped source title, enter custom text, and select a supported color and glow style in the live preview.

The generated title mod is staged during the normal Rocket Swap launch. The source title renders with the selected appearance on this PC; other players continue to receive the account's real title. Because the replacement is keyed to the source title ID, another player using that same source title may also look swapped on your screen. The current Titles page does not expose a separate manual restore button; launch cleanup and startup recovery own the proxy lifecycle.

Live title swapping is security-sensitive and uses a launch-scoped local HTTPS proxy. Read [Live Title Swap security notice](#live-title-swap-security-notice) before enabling it.

## Workshop Maps

Workshop Maps provides an online browser backed by [BakkesPlugins](https://bakkesplugins.com/maps), with search, category filters, sorting, and paging. A downloaded map can be a direct `.upk`/`.udk` package or a ZIP containing a supported map package.

Before installation, choose an installed `Labs_*.upk` arena as the target. Rocket Swap backs up that arena, installs the selected workshop map in its place, and offers **Restore Original**. Close Rocket League before installing or restoring a map. Local-file map importing is not part of the current Workshop Maps page.

## Tracker and tracker overlays

Tracker is disabled by default. When enabled, Rocket Swap configures Rocket League's local stats feed and listens on the local machine for match telemetry. The Tracker includes:

- Live score, teams, player stats, match events, ball speed, and playlist information when available.
- Session wins/losses and performance analytics.
- Up to 100 recent matches stored locally.
- Player/profile information and optional Tracker Network/MMR-service lookups when a supported platform identifier is available. Enabling those lookups sends the relevant platform/player identifier to the third-party service.
- A reset action for local session data, match history, and the event feed.

The overlay editor can enable and position Rank, MMR, Live Score, Ball Speed, Session Record, Player Stats, Match Feed, and Recent Matches widgets. Widgets can be dragged and resized in edit mode, then saved and locked into click-through mode. Global overlay controls include scale, opacity, accent color, reset positions, and visibility only while Rocket League is active.

Discord Rich Presence is also disabled by default. If enabled in Settings, it uses local Discord IPC to publish Rocket Swap activity and available game context such as playlist, MMR, score, or match state. It does not require Discord account credentials in the desktop client.

## Input Overlay

The **Overlay** page provides a topmost input display for:

- PlayStation 4 controllers.
- PlayStation 5 controllers.
- Xbox-compatible controllers.
- Keyboard and mouse using the included Akuma-style layout.

You can choose controller colors, pressed-input highlights, screen position or custom X/Y placement, 30-100% opacity, and 50-200% scale. An option limits the overlay to times when Rocket League is the foreground game, and another can reopen it automatically when the Overlay page is used. Keyboard-and-mouse mode uses Windows low-level input hooks while active; it does not read Rocket League process memory.

Legacy input statistics/APM, stick trails, numeric trigger labels, backdrop controls, and FPS/frame-time widgets are not part of the current integrated overlay.

## Miscellaneous tools

### Custom Quick Chat

Create up to 20 enabled keyboard or controller shortcuts, each with a message of up to 128 characters and an **All Chat** or **Team Chat** destination. Quick Chat uses Rocket League's normal text-chat input and triggers only while Rocket League is the foreground window. Bindings are stored locally and can be edited, disabled, or removed.

### Custom Sounds

Replace any of 11 supported events: Flip Reset, Crossbar/Goalpost, Jump, Double Jump, Dodge/Flip, Demolition, Goal, Save, Epic Save, Assist, and Demolish stat feedback. The importer accepts MP3, WAV, OGG, FLAC, and M4A audio, with a maximum processed duration of 30 seconds.

Rocket Swap patches the relevant Wwise sound bank, validates stock backups, and provides an individual restore-to-default action. Close Rocket League before applying or restoring sounds; changes take effect after the next game start.

### Custom Car Colors

Add up to six primary and accent color rows beneath the original garage palette instead of replacing the built-in rows. Each swatch can use an exact color or gradient, and rows can be added, removed, enabled, disabled, applied, or restored. Close Rocket League before applying or restoring palette changes.

## Fake Rank

Fake Rank changes only what the local Rocket League client displays for these supported playlists:

- Duel (1v1), Doubles (2v2), and Standard (3v3).
- Heatseeker, Rumble, Hoops, Snow Day, and Dropshot variants exposed by the app.

You can choose Unranked through Supersonic Legend and set an MMR from 0 to 5,000. The app backs up the affected local profile data and provides a restore action.

Fake Rank does not change matchmaking, competitive progress, season reward level, earned rewards, or server-side rank/MMR.

## Name Spoofing

Name Spoofing is an optional launch-only workflow for an Epic account. Enter the 32-character Epic Account ID and a substitute name, or use **Auto-Fill** to read the account ID already stored by Epic Games Launcher. Auto-Fill does not request an Epic password or authentication token.

After you accept the dedicated risk notice, the feature is armed for the next launch from Rocket Swap. Unlike item, title, and Fake Rank visuals, the substituted name is sent into the online session and can be seen by other players in the match. It is not a permanent Epic display-name change.

Name Spoofing can create a trusted local certificate and temporarily change the Windows system proxy. Read [Name Spoofing security notice](#name-spoofing-security-notice) before using it.

## Launch and restore behavior

Rocket Swap is designed to leave Rocket League clean while no managed session is active:

1. Validate the configured game build and selected operations.
2. Recover or restore stale state from an interrupted earlier session.
3. Back up original packages, workshop targets, clean emergency profile data, and launch assets as required.
4. Apply selected standard mods, custom textures, item/title swaps, prepared Fake Rank data, and other launch-managed changes. Custom Sounds and Custom Car Colors are applied and restored from their own pages instead.
5. Start Rocket League through the selected Epic Games, Steam, or Heroic path.
6. Monitor the game process and keep required launch-scoped services active.
7. Restore temporary packages and system state after Rocket League exits. Where a launch-managed profile mirror is used, retain the newest post-session save while preserving clean emergency backups.

Launch options include automatic/manual platform selection, **Launch without mods**, and automatic JoyToKey startup when JoyToKey is installed. The former no-EAC option has been retired: Rocket Swap removes its legacy argument and uses Rocket League's normal Easy Anti-Cheat launch path.

Rocket Swap may also prepare an optional branded start-screen asset in Rocket League's launcher WebCache. This decoration never controls whether the game may launch: if preparation fails, launch continues without it. The original cached asset is journaled and restored after the session or during startup recovery.

Keep Rocket Swap open until the game closes and restoration completes. If a required restore cannot finish safely, the app records pending state, protects the relevant backups, and retries recovery at startup.

After a detected Rocket League update, Rocket Swap may archive incompatible custom-texture backups, clear stale applied state, and reset saved mod selections before rebuilding compatible backups.

## Settings, updates, and diagnostics

Settings provides:

- Rocket League folder selection.
- Manual update and compatibility checks.
- Launcher-assisted Rocket League file verification.
- A bundled RocketSwap System Report for diagnostics.
- English, French, Spanish, and Arabic interface choices.
- Multiple color themes.
- The off-by-default Discord Rich Presence toggle.

The app can mark an affected page unavailable when a remote status report identifies a broken feature. A network failure does not disable every page; local status defaults remain available unless another compatibility or recovery guard applies.

Use the **Console** to find the first meaningful error from an import, backend, launch, or restore operation. System Report is intended for collecting diagnostics to share through the project's support channel; review any report before sharing it.

## Local data and recovery

Primary runtime data is stored under:

```text
%APPDATA%\RocketSwapApp\
|-- Auth\
|-- Backups\
|-- Backend\
|-- Config\
|-- Tracker\
|-- cache\
`-- settings.json
```

Additional feature folders are created there as needed for car colors, custom sounds and textures, item/title configurations, logs, temporary work, resources, and recovery journals. Input Overlay preferences use `%APPDATA%\RLInputOverlay\settings.txt`. A small number of updater settings and opt-in error logs may be stored beside the executable.

The main roaming app-data folder contains the Windows DPAPI-protected Discord session, legal-acceptance receipt, original-file backups, profile-save mirrors, generated backend configuration, cached icons, tracker history, and app preferences. Active device-key metadata is stored under `%LOCALAPPDATA%\RocketSwapApp\Auth`, while the non-exportable private device key remains in its selected Windows Key Storage Provider. Name Spoofing and Live Title Swap keep recovery state under `%LOCALAPPDATA%\RocketSwap\NameSpoofing` and `%LOCALAPPDATA%\RocketSwap\TitleProxy`. Older `%APPDATA%\Rocket Swap`, `%APPDATA%\RocketSwap`, and `%APPDATA%\RocketSwapEngine` data is migrated automatically when possible.

If a launch or restore is interrupted:

1. Close Rocket League and its launcher if the Console says a protected file is still in use.
2. Reopen Rocket Swap and allow startup integrity checks to finish.
3. Review the **Console** and act on the first restore error shown.
4. Confirm the configured `rocketleague` folder in **Settings**.
5. Use **Workshop Maps > Restore Original**, **Fake Rank > Restore Ranks**, **Item Swapping > Clear Swaps**, or the sound/car-color restore action when it matches the failed operation.
6. If automatic recovery still fails, preserve the backups, collect the Console/System Report details, and ask the project support channel before making further changes.
7. Use launcher file verification only after Rocket Swap has finished or support has confirmed that its pending restore can be abandoned.

Do not delete `%APPDATA%\RocketSwapApp\Backups` while recovery is pending.

## Privacy and security

### Authentication and device authorization

Rocket Swap uses Discord OAuth to verify identity, server membership, and app permissions. Before authentication, the app presents the current versioned Terms of Service and Privacy Policy and requires an unchecked acknowledgement followed by **Accept & Continue**. The service records the accepted document versions and content hashes.

New authorizations use an app-specific ECDSA P-256 device key created through Windows CNG. Rocket Swap prefers TPM-backed storage when available and otherwise uses the Windows software key provider with a non-exportable policy. Only the public key and derived key identifier are sent to the authentication service; motherboard, CPU, disk, firmware, MAC-address, and other raw hardware identifiers are not collected. Existing installations can migrate their earlier random installation link, and **Change PC** provides a fresh-Discord-authentication replacement flow that revokes older sessions.

Rocket Swap does not ask for Discord, Epic Games, or Steam passwords. The desktop client does not need access to Discord messages and does not hook Rocket League process memory. It does modify local packages, profile saves, launcher cache files, and requested Windows network/certificate settings, so antivirus products may classify compiled helpers as suspicious.

### Live Title Swap security notice

Live Title Swap is optional and requires explicit risk acknowledgement. It activates only for a title swap selected through Rocket Swap's normal launch flow.

The feature starts a local reverse HTTPS proxy scoped to Rocket League's title-catalog service. It verifies the upstream signed catalog, changes only the selected player-title entries, and re-signs the local response. To route that catalog request, Rocket Swap may temporarily add an exact hosts-file entry and trust a short-lived local certificate in both the Local Machine and Current User Windows trusted-root stores. Administrator approval is required.

Rocket Swap journals the exact hosts and certificate state it owns and attempts to remove it after a failed launch, after Rocket League exits, when Rocket Swap closes, and during startup recovery. HTTPS interception remains security-sensitive: an abnormal shutdown or external system change can leave stale state or prevent cleanup. Use the feature only on a Windows account and PC you control.

### Name Spoofing security notice

Name Spoofing is optional and is protected by its own explicit risk-acceptance notice. It activates only while armed and when Rocket League is started from Rocket Swap's **Launch** page; launching the game externally does not activate it.

The feature uses a temporary local HTTPS interception proxy. Rocket Swap may create and trust a local root certificate and temporarily register itself as the Windows system proxy. Decryption is restricted to Epic Games, Epic Online Services, and Psyonix traffic used by the workflow, while rewriting is restricted to the supported account endpoint and exact account ID entered by the user. Unrelated traffic is passed through without the name substitution.

Rocket Swap attempts to stop the proxy and remove its certificate/proxy state after a failed launch, after Rocket League closes, or when the app closes. An abnormal shutdown can leave a stale system proxy or certificate behind, and game or service changes can make the feature unsafe or incompatible.

The substituted name is match-visible, but Name Spoofing does not hide the authenticated account, redirect reports, prevent enforcement, or permanently change the Epic display name. The developer warns that using it may violate game or platform rules and could lead to account action. Use it only on a Windows account and PC you control.

Only download builds from project links you trust.

## Disclaimer

Rocket League updates can invalidate package offsets, sound-bank mappings, profiles, launch integrations, and backups. Rocket Swap performs version checks and can lock modification features for unsupported builds, but no automated check can guarantee compatibility or account safety.

Local visual swaps do not grant inventory items, alter ownership, or change server-side progression. Name Spoofing is a separate match-visible feature with additional risk.

Use Rocket Swap and every optional feature entirely at your own risk. The Rocket Swap developers are not liable for account actions, data loss, security problems, stale proxy or certificate state, game issues, or any other consequences caused by using the app.
