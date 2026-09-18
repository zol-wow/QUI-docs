---
layout: default
title: Profiles
parent: Settings Reference
nav_order: 11
---

# Profiles

The **General > Profiles** page manages AceDB profile storage, switching, and specialization-based auto-switching via LibDualSpec.

---

## Profile Management

QUI uses the AceDB-3.0 library for profile storage. All profile-level settings are stored under a named profile, and each character can be assigned to any available profile.

### Core Operations

| Operation | Description |
|---|---|
| **Switch Profile** | Change the active profile for the current character. All settings immediately update to reflect the selected profile. |
| **Create Profile** | Create a new empty profile with default settings. |
| **Copy Profile** | Copy all settings from an existing profile into the current one. This overwrites the current profile's settings. |
| **Delete Profile** | Permanently remove a profile. Cannot delete the currently active profile. |
| **Reset Profile** | Reset the current profile back to all default values. |

### Per-Character Assignment

Each character can independently select which profile to use. On Retail, all characters initially share the `"Default"` profile. Switching profiles on one character does not affect other characters unless they share the same profile.

On Forever, the temporary character-local storage workaround keeps each character's profiles separate, including `"Default"`. Use same-client profile export/import to copy settings between characters; changes do not synchronize.

### Reset All Movers

The **Reset All Movers** button resets all QUI frame positions to their default locations. This affects only frame anchoring/positioning data, not other profile settings. Use this when frame positions become misaligned or after importing a profile from another resolution.

---

## LibDualSpec Integration

When LibDualSpec-1.0 is available (it is bundled with QUI), automatic profile switching based on your active specialization is supported.

| Feature | Description |
|---|---|
| **Spec-Based Switching** | Assign a different profile to each of your specializations. When you change spec, QUI automatically switches to the assigned profile. |
| **Per-Spec Assignment** | Each specialization can be mapped to any available profile. |
| **Auto-Detection** | LibDualSpec is enabled automatically when the library is loaded. No manual activation is required. |

This is particularly useful for classes that have significantly different UI needs between specs (e.g., a healer spec with group frames versus a DPS spec with a minimal HUD).

---

## SavedVariables

QUI persists data across sessions using two WoW SavedVariables entries, declared in `QUI.toc`.

| Variable | Type | Description |
|---|---|---|
| `QUIDB` | table | Primary SavedVariables store managed by AceDB. Contains profile, character, and global settings. |
| `QUI_StorageDB` | table | Shared storage for tracked character and inventory data. Character-local on Forever during the workaround. |

On **Retail**, both use account-wide storage at
`WTF/Account/<account>/SavedVariables/QUI.lua`. On **Forever** only, both use
character storage at
`WTF/Account/<account>/<realm>/<character>/SavedVariables/QUI.lua` as a temporary
workaround for the client's persistence issue. Existing account-wide data is
**not automatically migrated**. Back up your `WTF` folder before updating; the
workaround is intended to be reverted once Blizzard fixes the underlying issue.

These are written to disk by the WoW client on logout, reload, or `/reload`. Manual editing of SavedVariables files is not recommended -- use the in-game profile import/export system instead.

---

## Config Panel Settings

Settings that control the appearance of the QUI options panel itself. Found in `db.profile`.

| Setting | Type | Default | Description |
|---|---|---|---|
| `configPanelScale` | number | `1.0` | Scale of the options panel window |
| `configPanelWidth` | number | `750` | Width of the options panel in pixels |
| `configPanelAlpha` | number | `0.97` | Opacity of the options panel background |
