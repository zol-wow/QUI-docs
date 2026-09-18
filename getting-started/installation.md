---
layout: default
title: Installation
parent: Getting Started
nav_order: 1
---

# Installation

This alpha supports **World of Warcraft Midnight 12.1.5 PTR** and experimental
**WoW Forever 1.60.1**, using the same archive. See the [alpha release notes](../changelog)
for Forever feature limits.

## Fastest Option: Addon Manager

For most players, the easiest path is an addon manager.

1. Open the **CurseForge** or **WoWUp** application.
2. Search for **"QUI Community Edition"**.
3. Select the **Alpha** release channel for your target client and click **Install**.
4. The app handles updates automatically.

## Manual Install

1. Download **5.5.0-ptr-alpha8** from one of these sources:
   - [GitHub Releases](https://github.com/zol-wow/QUI/releases)
   - [CurseForge](https://www.curseforge.com/wow/addons/qui-community-edition)
2. Extract the downloaded zip file.
3. Copy every top-level `QUI*` folder from the zip into the target client's `Interface\AddOns\` directory. Use the installation folder for the PTR or Forever client you will launch.
4. Make sure the folder structure is correct -- `QUI.toc` should be directly inside `Interface\AddOns\QUI\`, `QUI_Options.toc` should be directly inside `Interface\AddOns\QUI_Options\`, and the other `QUI_*` folders should sit beside them.

{: .important }
QUI is a multi-folder addon suite. If you manually copy only `QUI`, the options panel and feature modules will be missing.

## Confirm It Loaded Correctly

1. Launch World of Warcraft.
2. On the character select screen, click **AddOns** in the lower-left corner.
3. Confirm that **QUI** and its `QUI_*` modules appear together in the addon list and are enabled as desired.
4. Log in to a character and type `/rl` to reload the UI.
5. Type `/qui` to open the options panel and confirm QUI is running.

## If Something Looks Wrong

- If QUI does not appear in the addon list, check that the folders are not nested twice.
- If `/qui` does nothing, confirm `QUI_Options` is installed and enabled, then reload once and try again.
- If the addon loads but the screen looks unfinished, continue to [First Setup](first-setup) before assuming anything is broken.

Compatible integrations are detected automatically when they are present, but QUI does not need extra addons to work.

## Alpha Upgrade Safety

Before installing an alpha build, back up your `WTF` folder. QUI takes automatic profile backups for some schema migrations, but a full `WTF` backup is still the safest rollback path.

{: .warning }
**Forever only:** this release temporarily saves QUI profiles and tracked data
per character to work around the client's persistence issue. Old account-wide
data is not automatically migrated, and characters no longer share that data.
Keep your backup and any same-client profile exports before upgrading; a
character may open with a fresh setup. **Retail retains normal account-wide
storage.** The workaround is intended to be reverted after Blizzard fixes the
issue. See [Profiles](profiles) for details.
