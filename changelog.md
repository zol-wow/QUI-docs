---
layout: default
title: Changelog
nav_order: 5
---

# Changelog

This page summarizes the user-facing changes in each stable release. For every release entry and technical fix, see the full [CHANGELOG.md](https://github.com/zol-wow/QUI/blob/main/CHANGELOG.md).

## Current Release: 5.3.1

{: .warning }
**WoW 12.1 only.** This build targets patch 12.1 (interface 120100) and will not load on the 12.0.x client.

QUI 5.3.1 brings the beta improvements to stable. It adds optional defensive reminders, bonus-roll filtering, and
group-frame visibility options, with fixes for combat whispers, arena target
class colors, rotation suggestions, castbar anchors, and settings search.
It also updates Cooldown Manager aura tracking, buff layouts, glow refreshes,
and chat recipient routing, reduces startup and raid-frame work, and fixes
restricted achievement messages and saved minimap datatext positions.
The latest fixes keep buff icons from duplicating in combat, center visible
buff rows, refresh auras when target or focus changes, and honor pandemic
glow styles and chat realm-name preferences.
Native aura sound and text-to-speech configuration stays in Blizzard's
Cooldown Manager editor to prevent protected aura and cooldown errors.
New raid members now use your configured frame size. Native buff slots stay
distinct through combat, glow sizing avoids restricted-value errors, upgraded
bag items retain their correct item levels, and imported click-cast macros
keep their names.

{: .important }
Back up your `WTF` folder before updating. Manual installs must copy every `QUI*` folder from the release zip into `Interface\AddOns\`.

## What's New in 5.3.1

### Added

- **Reminders is a new optional module, off by default**, with defensive
  callouts driven by BigWigs, DBM, or Blizzard's encounter timeline. Configure
  per-spec defensive priorities and boss abilities under Gameplay → Reminders,
  with movable callouts, sound or text-to-speech, optional chat, and CDM glows.
- **Bonus Roll filters** under Quality of Life let you hide prompts by raid
  difficulty, boss, dungeon or Delve, or set a Mythic+ minimum key level.
  Filtering is off by default and saved per profile. Recover an unexpired
  hidden offer through its chat link, the settings page, or `/qui bonusroll show`.
- **Group Frames can hide raid groups 7 and 8 in Mythic raids**, while keeping
  those groups visible outside Mythic.
- **Group Frames can hide unit tooltips during combat.**

### Changed

- **Settings load when needed**, reducing startup work and avoiding repeated
  skin refreshes when the settings window is created.
- **Raid frames prepare only the selected layout** and reuse unit buttons,
  reducing allocations and repeated styling during roster updates.
- **Cooldown Manager uses Blizzard's native aura tracking for custom entries**,
  including Buff Bars, fallback Buff Icons, and custom containers. Aura alert
  settings explain native sound and text-to-speech limitations.

### Fixed

- **New party and raid members use your configured frame dimensions**,
  including separate raid groups, self frames, and spotlights.
- **Native Cooldown Manager proc and cast-highlight glows avoid restricted
  size errors**, preserving your chosen glow style and offsets.
- **Native buff slots stay distinct and retain their placement in combat**,
  keeping related buffs from collapsing into one icon and hiding duplicate
  base icons behind managed aura displays.
- **Bag item levels stay correct for upgraded copies of the same item**,
  with cached details kept separately for each item link.
- **Imported click-cast macros keep their names in the binding list**,
  instead of displaying only “Macro”.

- **Cooldown Manager keeps custom buff icons from duplicating in combat**
  when WoW restricts aura configuration.
- **Centered mixed buff rows follow the visible icons** as auras appear and
  expire, including during combat.
- **Target and focus aura tracking refreshes when you switch units**,
  including built-in buff mirrors and custom aura containers.
- **Pandemic glows honor the selected style, color, and offsets**, including
  per-spell overrides, and update when toggled during an active refresh window.
- **Chat honors your realm-name preference for restricted senders**,
  including guild chat.
- **Cooldown Manager avoids tainting Blizzard's native aura sound layouts**,
  preventing protected aura and cooldown errors. Configure or disable native
  sound-kit and text-to-speech aura alerts in Blizzard's Cooldown Manager
  settings; QUI's sound status explains this even when its alert checkbox is off.
- **Minimap datatext keeps its saved position during minimap refreshes**,
  preserving Layout Mode placement and preventing circular-anchor errors.
- **Achievement messages format correctly when WoW restricts their text or
  sender information**, including guild achievements.
- **Chat channel names without a numeric prefix no longer trigger formatting
  errors.**
- **Mixed Cooldown Manager buff rows retain configured spacing and alignment**,
  including custom auras, row wrapping, and group boundaries.
- **Cooldown Manager glow animations keep their progress during layout
  refreshes**, inactive proc animations stop, and unchanged aura filters and
  effect settings avoid repeated updates.
- **Native aura effects no longer trigger blocked animation-script warnings.**
- **Combat replies and sender clicks select the current whisper recipient**,
  including Battle.net links with restricted recipient information.
- **Chat channel context menus create a QUI tab filtered to that channel.**
- **Combat whispers opened through Reply, character links, or Battle.net use
  a visible QUI chat input**, preserving Blizzard's recipient selection and
  reply history.
- **Whispers from restricted identities use a shared Whispers tab.**
- **The chat input follows the active QUI window**, including after switching
  windows or deleting the active window.
- **Arena target health bars retain class colors when WoW restricts class
  information**, instead of falling back to hostility colors.
- **Rotation suggestions keep updating with Blizzard's assisted-combat
  highlight disabled**, both on Cooldown Manager icons and the standalone
  Rotation Assist icon. Unavailable suggestions clear instead of remaining stale.
- **Danders party and raid anchors no longer restrict player castbar resizing.**
- **Settings search skips restricted label text**, preventing errors while
  gathering searchable labels.
- **Pinning settings and unpinning unchanged values avoid unnecessary full
  addon refreshes.** Restoring a changed active value still applies it correctly.
- **Castbar anchor chains no longer let protected followers restrict castbar
  resizing.** Follower positions refresh as targets change, protected followers
  reconcile after combat, and absolute anchors account for frame scale.

## Previous Release: 5.3

> ⚠️ **WoW 12.1 ONLY.** This build targets patch 12.1 (interface 120100) and
> will not load on the 12.0.x client.

QUI 5.3 brings the 5.3 beta improvements to the stable release: expanded Aura
Displays, a richer Damage Meter workspace, combat alerts, and UI refinements.

### Added

- **Aura Displays support guided setup, templates, nested groups, share strings,
  draggable previews, gap collapsing, and Blizzard-native sound alerts.**
- **Damage Meter rows open a resizable five-pane detail workspace**, with richer
  historical-session controls and target-to-spell drilldowns.
- **Combat alerts include killing-blow details for Group Death Alert and
  per-entry sound and text-to-speech alerts for Cooldown Manager.**
- **Auto Accept Summons has Always and Out of Combat modes**, while dungeon
  teleports show cooldowns in the Mythic+ window, world map, and Info Bar.
- **Cooldown Manager buff icons have growth and anchor controls**, and minimap
  settings include Blizzard's native Rotate Minimap toggle.

### Improved

- **Settings and Blizzard-window skins have more consistent styling**, including
  the Character window, Social, talents, and Crafting Orders.
- **Alt equipment supports filtering, sorting, dedicated tooltips, and a guild
  column**, while weekly progress shows lockouts and compact Great Vault summaries.
- **Incoming Casts can collapse readable hidden icons**, and Battle Res Counter
  can hide when charge information is unavailable.

### Fixed

- **Cooldown Manager preserves native layouts, buff anchors, visibility, and
  unusable-spell tint** across loading, combat, and cooldown transitions.
- **Action bars preserve secure button state and possession key bindings**,
  recover cooldown animations after fades, and refresh layouts after minimap changes.
- **Unit-frame castbars defer restricted layout changes**, raid markers handle
  restricted indices, and dimmed group frames retain tooltips.
- **Damage Meter retains spell names and healing rows during combat.**
- **Bank money dialogs and guild-bank transfers work reliably**, including the
  combined All view and reopening the bank.
- **QUI Chat preserves literal messages, other addons retain their `/pull`
  commands, and weapon-oil timers refresh after zone changes.**
- **The Info Bar Shop button is restored.**

## Previous Release: 5.2.3

{: .warning }
**WoW 12.1 only.** This build targets patch 12.1 (interface 120100) and will not load on the 12.0.x client.

QUI 5.2.3 expands shared HUD visibility and cross-profile controls while
hardening Action Bars, Cooldown Manager, Blizzard-owned UI, and utility windows.

{: .important }
Back up your `WTF` folder before updating. Manual installs must copy every `QUI*` folder from the release zip into `Interface\AddOns\`.

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

## Previous Release: 5.2.2

{: .warning }
**WoW 12.1 only.** This build targets patch 12.1 (interface 120100) and will not load on the 12.0.x client.

QUI 5.2.2 expands profile sharing, combat feedback, and group tools while
hardening Cooldown Manager, protected UI, and native event handling.

{: .important }
Back up your `WTF` folder before updating. Manual installs must copy every `QUI*` folder from the release zip into `Interface\AddOns\`.

## What's New in 5.2.2

### Profiles and displays

- **Feature settings can be shared across profiles**, including Aura Displays
  and Group / Raid Frames, without replacing click-cast bindings.
- **Tracked aura displays can keep inactive icons visible** with configurable
  placeholder behavior and styling.

### Combat feedback

- **Action Bar range and usability colors follow native state events** through
  paging, stance, combat, and slot changes without disrupting shared events.
- **Cooldown Manager icons support configurable pressed effects** and preserve
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

- Install 5.3 over the existing QUI folders; saved variables remain in `QUIDB` and `QUI_StorageDB`.
- Manual installs must copy every top-level `QUI*` folder from the release zip, not only the `QUI` folder.
- If a feature does not open, check `/qui` > **Module Addons** before troubleshooting its settings.
- Some account-cache data, especially offline inventory and equipment, repopulates as each character logs in.
