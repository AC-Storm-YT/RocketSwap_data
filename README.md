# Rocket Swap

Rocket Swap is a Windows mod manager and local visual swapper for Rocket League. It imports and organizes cosmetic mods, generates visual item swaps, prepares selected changes for launch, and restores clean files after the game closes.

> [!IMPORTANT]
> Rocket Swap is an independent community project. It is not affiliated with, endorsed by, or sponsored by Psyonix, Epic Games, or Rocket League.
>
> Third-party mods are permitted only when they comply with the [Epic Games Terms of Service](https://legal.epicgames.com/epicgames/tos) and [Rocket League Code of Conduct](https://www.rocketleague.com/code-of-conduct). Rocket Swap modifies local game and profile files and is not officially supported. Violating those rules may result in account restrictions or a permanent ban.
>
> Use Rocket Swap entirely at your own risk and keep backups.

## Project status

Rocket Swap is currently in private beta. Access is verified through Discord and depends on the permissions returned by the Rocket Swap authentication service.

[Join the Rocket Swap Discord](https://discord.gg/dGxtZagQgB)

## Features

- Import, search, filter, preview, export, and safely remove Rocket League mods.
- Apply selected mods only for a Rocket League launch, then restore the original files when the game exits.
- Generate local item swaps by selecting an item to equip and an item to display.
- Apply supported paint variants, including painted items and custom Gold Rush colors.
- Add and swap player titles. Title changes are local and are limited to supported menu and inventory views.
- Spoof the locally displayed playlist rank and MMR. This does not change matchmaking, progression, rewards, or server-side rank data.
- Optionally substitute the display name Rocket League receives during a Rocket Swap launch by using a temporary, narrowly scoped local HTTPS proxy.
- Browse and install workshop maps from [BakkesPlugins](https://bakkesplugins.com/maps).
- Launch through Epic Games, Steam, or Heroic, with automatic detection or a manual platform override.
- Import supported `.upk`, `.bnk`, Rocket Swap export ZIP, mod-pack ZIP, and AlphaConsole-style ZIP files.
- Automatically maintain backups of modified game packages and affected profile saves.
- Check Rocket Swap updates and Rocket League version compatibility.
- Discord OAuth access control, a live Dashboard, an in-app Guide, and an operation Console.

## Requirements

For the app:

- Windows 10 or 11.
- Rocket League installed through Epic Games, Steam, or Heroic.
- Internet access for Discord authorization, compatibility/update checks, and online content such as workshop maps.
- A Discord account with access granted by the Rocket Swap server.

## Getting started

1. Download the installer.
2. Start Rocket Swap and accept the install-ID consent prompt.
3. Authorize with Discord in your browser, then return the generated code to the app when prompted.
4. Select the Rocket League installation folder named `rocketleague`.
5. Import a mod or configure an item, title, or local visual change.
6. Select the changes you want under **Equip Items**, then open **Launch**.
7. Start Rocket League through Rocket Swap so it can stage and later restore the selected changes.

Do not close Rocket Swap while it is applying or restoring files. The app blocks unsafe navigation and shutdown during critical operations, but an interrupted process can still require recovery on the next start.

## App sections

| Section | Purpose |
| --- | --- |
| **Dashboard** | Account, app status, game news, changelog, and common actions. |
| **Item Swapping** | Pick an equipped item, a visual donor, and supported paint settings to generate a local mod. |
| **Equip Items** | Installed mod library, categories, search, selection, import, export, and removal. |
| **Workshop Maps** | Search, filter, download, and install maps listed by BakkesPlugins. |
| **Titles** | Select, apply, restore, and locally swap supported player titles. |
| **Fake Rank** | Change the rank and MMR shown by the local client for supported playlists. |
| **Miscellaneous** | Security-sensitive utilities, including the optional Name Spoofing launch workflow and its risk notice. |
| **Launch** | Choose mods and launcher options, stage changes, and launch Rocket League. |
| **Guide** | In-app quick start and recovery guidance. |
| **Settings** | Change the Rocket League folder and run compatibility/update checks. |
| **Console** | View app, launcher, backend, and restore activity. |

## Mods and supported imports

Rocket Swap keeps the mod library beside the executable:

```text
mods\<Category>\<Mod Name>\
```

Standard import categories include Antenna, Avatar Border, Banner, Body, Boost, Boost Audio, Decal, Engine Audio, Goal Explosion, Hat/Topper, Paint, Titles, Trail, and Wheels.

Supported custom texture categories include Custom Decals, Custom Balls, and Custom Boost Meter. Custom Bodies and Custom Wheels are beta-gated in the importer. Paint support is still evolving, so some item and paint combinations can remain at their default color.

The importer accepts:

- Individual `.upk` and `.bnk` packages.
- Single-mod Rocket Swap export archives.
- Rocket Swap pack archives, conventionally named `mods.zip`.
- Supported AlphaConsole-style ZIP archives.

Generated item/title swaps are written into the same mod library and can be selected under **Equip Items** for the normal launch flow.

## Launch and restore behavior

Rocket Swap is designed to leave Rocket League clean while no managed session is active:

1. Original packages and affected profile saves are backed up.
2. Selected mods and generated changes are staged immediately before launch.
3. Rocket League is started through the selected launcher.
4. Rocket Swap watches the game process.
5. Managed changes are restored after Rocket League exits.

The launcher supports automatic platform detection plus Epic Games, Steam, and Heroic overrides. Optional controls include launching without selected mods, a no-EAC launch option, and JoyToKey compatibility when JoyToKey is installed.

The no-EAC option changes launcher arguments/settings; it is not an anti-cheat bypass and does not make restricted online play available.

## Local data and recovery

Runtime data is stored under:

```text
%APPDATA%\RocketSwapApp\
|-- Auth\
|-- Backups\
|-- Backend\
|-- Config\
|-- cache\
`-- settings.json
```

This folder contains the protected Discord session, consent/install-ID records, original-file backups, profile-save mirrors, generated backend configuration, cached icons, and app preferences. Older `%APPDATA%\Rocket Swap`, `%APPDATA%\RocketSwap`, and `%APPDATA%\RocketSwapEngine` data is migrated automatically when possible.

If a launch or restore is interrupted:

1. Close Rocket League.
2. Reopen Rocket Swap and allow its startup integrity checks to finish.
3. Review the **Console** for the first reported restore error.
4. Confirm the configured `rocketleague` folder in **Settings**.
5. Use the relevant restore action for titles, Fake Rank, or generated changes before launching again.

Do not delete `%APPDATA%\RocketSwapApp\Backups` while recovery is pending.

## Privacy and security

Rocket Swap uses Discord OAuth to verify identity, server membership, and app permissions. It stores a random install ID only after consent and saves the authenticated session under `%APPDATA%\RocketSwapApp\Auth`.

Rocket Swap does not ask for your Discord, Epic Games, or Steam password. The desktop client does not need access to Discord messages and does not hook Rocket League process memory. It does modify local package/profile files and can update launcher settings for requested launch options, which is why antivirus products may classify compiled helpers as suspicious.

### Name Spoofing security notice

Name Spoofing is optional and is protected by an explicit risk-acceptance notice. It activates only when Name Spoofing is armed and Rocket League is started from Rocket Swap's **Launch** page; launching the game externally does not activate it.

The feature uses a temporary local HTTPS interception proxy. Rocket Swap may create and trust a local root certificate and temporarily register itself as the Windows system proxy. Traffic decryption is restricted to Epic Games, Epic Online Services, and Psyonix domains, while the response change is restricted to the exact supported account endpoint and account ID entered by the user. Rocket Swap attempts to stop the proxy and remove certificate state after a failed launch, after Rocket League closes, or when the app closes.

HTTPS interception remains security-sensitive. An abnormal shutdown can leave a stale proxy setting or certificate behind, and game or service changes can make the feature unsafe or incompatible. Name Spoofing does not hide the authenticated account, redirect reports, prevent enforcement, or permanently change the Epic display name. Use it only on a Windows account and PC you control.

Only download builds from project links you trust.

## Disclaimer

Rocket League updates can invalidate package offsets and backups. The app performs game-version checks and can lock modification features when the installed build is unsupported, but no automated check can guarantee compatibility or account safety. Local visual swaps do not grant inventory items, alter ownership, or change server-side progression.

Use Rocket Swap and every optional feature entirely at your own risk. The Rocket Swap developers are not liable for account actions, data loss, security problems, stale proxy or certificate state, game issues, or any other consequences caused by using the app.
