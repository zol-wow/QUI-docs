---
layout: default
title: Changelog
nav_order: 5
---

# Changelog

This page summarizes the user-facing changes since the last mainline release. For every beta entry and technical fix, see the full [CHANGELOG.md](https://github.com/zol-wow/QUI/blob/main/CHANGELOG.md).

## Current Release: 5.3-beta2

{: .warning }
**WoW 12.1 only.** This build targets patch 12.1 (interface 120100) and will not load on the 12.0.x client.

QUI 5.3-beta2 adds alert controls, tighter combat-HUD layouts, and focused
Damage Meter and Chat corrections to the 5.3 beta line.

{: .important }
Back up your `WTF` folder before updating. Manual installs must copy every `QUI*` folder from the release zip into `Interface\AddOns\`.

## What's New in 5.3-beta2

### Damage Meter

- **Damage Meter rows open a reusable five-pane detail workspace** for spells,
  targets, attackers, and death recaps while row-hover details remain
  independent and interactive.
- **Historical sessions and individual windows have richer controls**, with
  persisted pane sizes and safer combat and Mythic+ state selection.
- **The detail workspace is resizable and remembers its dimensions.** Target
  rows drill down to their spells, and player hover details refresh item levels.

### Interface

- **Unrestricted Blizzard frames remain movable during combat**, while secure
  and proxy-owned frames continue to wait until combat ends.
- **Shared frame styling is more consistent** across Social, talents, Crafting
  Orders, tabs, text, and close controls.
- **Initiative Tasks use QUI's Objective Tracker styling**, and Mail's Open All
  action keeps the Mail window above overlapping moved panels.
- **Incoming Casts can collapse readable hidden icons** so visible casts pack
  together while restricted targets retain fixed-width gaps.
- **The Battle Res Counter can hide without charge information**, removing its
  unavailable icon between supported encounters and in unsupported content.
- **Player chat bodies preserve literal apostrophes and percent tokens** instead
  of treating ordinary messages as format templates.

### Combat UI

- **The Group Death Alert can name the killing blow**, optionally include the
  attacker, color the player name by class, limit alerts to instances, and use
  a configurable on-screen duration.
- **Aura Displays can play Blizzard-native sounds** when an aura is applied,
  gains stacks, or is removed.
- **Cooldown Manager entries have sound and text-to-speech alerts** for
  cooldown and aura state changes, with searchable sounds and previews.
- **Cooldown Manager no longer writes Blizzard's Edit Mode layouts during
  login.** Layout mismatches are detected without mutation and corrected through
  guided Edit Mode steps, preventing protected Cooldown Viewer errors.
- **Group Frame summon indicators handle secret status values safely** and
  refresh when combat ends.

## What's New in 5.2.3

### Alts

- **The Alts window can be resized from its bottom-right corner**, with its
  position, anchor, width, and height preserved across reloads.
- **Weeklies now shows column headers**, and both Weeklies and
  Currencies size their left-aligned columns from the rendered text.
- **An active Alts move or resize stops cleanly when combat begins**, preventing
  the window from continuing to follow the cursor through combat.

### Interface and utility

- **Aura Displays can use the shared HUD Visibility rules**, including combat,
  target, group, instance, mouseover, mount, location-hide, opacity, and fade
  controls without bypassing each display's gameplay visibility gates.
- **Currency tooltips show saved per-character balances**, while account-wide
  currencies render one live Warband total instead of duplicated character
  values.
- **Overflowing QUI Chat tabs open a direct picker**, and conversation tabs gain
  close buttons with predictable adjacent-tab selection after closing.
- **Newly opened moved Blizzard panels stay above overlapping panels** after QUI
  restores their saved positions.

### Profiles

- **Aura Displays and Group / Raid Frames can be pinned across all profiles**
  from one canonical source, including active-specialization layout settings.
- **Individual destination profiles can Ignore a global pin for local edits**
  and use Apply to restore the shared settings.

### Combat UI

- **Action Bar proc glows update as their current action changes**, including
  paging, special bars, flyouts, duplicate slots, and hidden-bar reveals,
  without disrupting Rotation Assist highlights.
- **Cooldown Manager swipes remain visible for the full cooldown** without
  flashing as a full overlay when their texture refreshes, including ordinary
  abilities and charge recharges.
- **Objective Tracker styling stays off Blizzard's native update and resize
  paths**, preserves native Scenario dimensions, and restores the Scenario
  tracker after QUI's Mythic+ timer closes.
- **Cooldown Manager waits for Blizzard to load its native viewer**, avoiding
  tainted settings callbacks during later loadout changes.
- **Manual castbar widths work when Auto-Width is off or the anchor is
  disabled**, and the settings preview shows the configured width.
- **Keybind scans skip OPie macro-editor widgets**, preventing its editor-only
  `GetAction` API from being called as an action button.
- **Expanding Group Frame aura settings keeps every following control in
  place**, including Targeted Spells, Dispel settings, and guidance text.
- **Inactive Aura Display movers remain usable in Layout Mode** at their saved
  size instead of collapsing when the display has no active icons.
- **Cooldown Manager pressed effects apply only to cooldown icon containers**,
  leaving buff icons unaffected.
- **Group Frame aura layering waits until combat ends** instead of reading
  protected frame state during combat.
- **Resource bars refresh automatically when Fluid Form changes forms**, so Cat
  Form combo points appear without a manual refresh.
- **Action Bar range and usability colors clear when their live condition
  ends**, including after mount and display changes.
- **New Action Bar tints respect autohide state**, staying hidden through full
  and partial fades until the bar is fully revealed.
- **Mythic+ enemy forces follow the selected Count, Percentage, or Both
  format**, including current and required counts alongside percentage when
  Both is selected.
- **Freshly shown nameplates initialize their absorb bar immediately** instead
  of waiting for a later health update.
- **Blizzard's vehicle exit button remains available when the active vehicle
  permits leaving**, while QUI continues to skin the surrounding override bar.
- **Cooldown Manager Edit Mode corrections save once and immediately require a
  reload**, avoiding protected Cooldown Viewer errors during continued play.
- **Micro Menu ownership stays with Blizzard during temporary UI transitions**,
  including Override Action Bars and Pet Battles, then completes a deferred
  cold-start build after Blizzard releases it.
- **The custom Info Bar Micro Menu no longer duplicates Blizzard's Shop
  button.** The native Micro Menu remains the supported path for opening the
  Shop.

## What's New in 5.2.2

### Profiles and displays

- **Feature settings can be shared across profiles**, including Aura Displays
  and Group / Raid Frames, without replacing click-cast bindings.
- **Tracked aura displays can keep inactive icons visible** with configurable
  placeholder behavior and styling.

### Combat feedback

- **Action Bar range and usability colors follow native state events** through
  paging, stance, combat, and slot changes without disrupting shared events.
- **Cooldown Manager cooldown icons support configurable pressed effects** and preserve
  cast highlights across reanchored, pooled, and remapped icons.
- **Cooldown and consumable state follows Blizzard's live sources**, including
  charge metadata, aura phases, item counts, and partial source updates.

### Group content and utility

- **Group-frame debuff gradients expose non-dispellable types** while actionable
  dispels keep their full overlay and cleanse-ready glow.
- **Group-frame click-casting supports items**, and raid releases can require
  Ctrl after a three-second safety delay.
- **The Lust Timer follows Blizzard's native aura state** during combat, while
  castbars, bank controls, and startup paths avoid protected mutations.

## What's New in 5.2.1

### Combat fixes

- **Incoming casts** can be tracked in a dedicated display alongside the rest
  of the QUI combat HUD.
- **Cooldown Manager aura and cooldown state** stays safe and complete through
  secret-value, target, roster, and combat refreshes.
- **Group-frame dispel indicators** follow live unit state, dispellable types,
  frame alpha, and Enrage coverage.

The broader 5.2 feature set remains available below.

### Profiles and setup

- **Named account-wide nameplate profiles** can be created, assigned by specialization, imported, and exported.
- **Aura displays have guided load-condition pickers** for classes, specializations, roles, and encounters, plus a faster create/list/preview workflow.
- **Quick feature toggles in the options sidebar** keep module switches close to the settings they control.

### Combat UI

- **Action bars stay responsive in combat**, including cooldowns, glows, pressed states, assisted-rotation indicators, paging, stance changes, and special bars.
- **Cooldown Manager tracking is more reliable** for spell variants, tracked buff bars, tooltips, keybind labels, frame levels, row opacity, and in-combat refreshes.
- **Group frames gain custom health colors and tracked-aura bar controls**, including orientation, styling, and expiring-state colors.

### Trackers and utility

- **The objective tracker has refreshed styling**, with improved icons and progress bars while preserving safe in-combat updates.
- **The Mythic+ timer keeps boss, objective, and weighted progress data current** through combat.
- **New 12.1 consumables and targeted mail, bag, tooltip, skinning, and help fixes** round out the release.

## Upgrade Notes

- Install 5.2 over the existing QUI folders; saved variables remain in `QUIDB` and `QUI_StorageDB`.
- Manual installs must copy every top-level `QUI*` folder from the release zip, not only the `QUI` folder.
- If a feature does not open, check `/qui` > **Module Addons** before troubleshooting its settings.
- Some account-cache data, especially offline inventory and equipment, repopulates as each character logs in.
