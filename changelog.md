---
layout: default
title: Changelog
nav_order: 5
---

# Changelog

This page summarizes the user-facing changes since the last mainline release. For every beta entry and technical fix, see the full [CHANGELOG.md](https://github.com/zol-wow/QUI/blob/main/CHANGELOG.md).

## Current Release: 5.2.2-beta9

{: .warning }
**WoW 12.1 only.** This build targets patch 12.1 (interface 120100) and will not load on the 12.0.x client.

QUI 5.2.2-beta9 continues the 5.2.2 beta line with safer raid releases,
group-frame dispel awareness, and more reliable combat feedback.

{: .important }
Back up your `WTF` folder before updating. Manual installs must copy every `QUI*` folder from the release zip into `Interface\AddOns\`.

## What's New in 5.2.2-beta9

### Group Content

- **Raid releases can require Ctrl after a three-second safety delay**, helping
  prevent accidental releases while a battle resurrection is available.
- **Group frames can show non-dispellable debuff types as health gradients**,
  while actionable dispels retain the full overlay and cleanse-ready glow.
- **Group-frame range fading preserves dead, offline, and other life-state
  visuals**, and hidden aura buttons no longer intercept mouse input.

### Combat Feedback

- **Action Bar range and usability colors follow native state events**, staying
  current through paging, stance, and combat transitions.
- **Cooldown Manager icons can mirror held button presses** with Off, Blizzard,
  or QUI effects configured per icon container.
- **Cast highlights and held-press effects follow reanchored, pooled, and
  remapped cooldown icons** without carrying stale state between abilities.

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
