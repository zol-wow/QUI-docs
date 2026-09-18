---
layout: default
title: Changelog
nav_order: 5
---

# Changelog

This page summarizes the user-facing changes since the last mainline release. For every beta entry and technical fix, see the full [CHANGELOG.md](https://github.com/zol-wow/QUI/blob/beta/CHANGELOG.md).

## Current Release: 5.3.2-beta3

{: .warning }
**WoW 12.1 only.** This build targets patch 12.1 (interface 120100) and will not load on the 12.0.x client.

The 5.3.2 beta line starts from stable 5.3.1.
This beta adds optional, location-specific resurrection automation and improves
damage-meter text readability when outlines are disabled.

{: .important }
Back up your `WTF` folder before updating. Manual installs must copy every `QUI*` folder from the release zip into `Interface\AddOns\`.

## What's New in 5.3.2-beta3

### Added

- **Auto Accept Resurrection** under QoL → Automation offers separate settings
  for dungeons, raids, PvP, and the open world. Each defaults to **Off**, with
  **Out of Combat** and **Always** options. **Always** also accepts battle
  resurrections during combat. Hold **Shift** when an offer arrives to keep it
  manual; offers with resurrection sickness or a recovery delay stay manual.

### Fixed

- **Damage Meter text is easier to read without font outlines.** Bright fills
  automatically darken behind light text while preserving their hue and opacity,
  and unoutlined window text gets a black shadow. Dark-text and outlined bar
  styles keep their original fills.

### Beta Line

- Beta1 started the 5.3.2 beta line from the stable 5.3.1 release.

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

### Beta Line

- Carries forward the v5.3 runtime after synchronizing beta with main.

## What's New in 5.3-beta15

### Alt Tracking

- **Alt equipment supports filtering, sorting, scrolling, and dedicated item
  tooltips**, with an optional guild column in the roster.
- **Weekly progress shows lockouts inline**, with row toggles and compact
  Great Vault summaries.

### Latest UI Fixes

- **Possession abilities stay visible on Action Bar 1 with your usual keys**
  when Blizzard falls back to the main bar, even after fade timers expire.
  Normal fading resumes when possession ends.
- **Focus and other unit frames display raid markers when WoW restricts marker
  values**, instead of hiding them.
- **Bundled libraries handle restricted chat values and updated inventory APIs**,
  with compatibility improvements to profile options.
- **Cooldown Manager preserves unusable-spell tint across cooldown transitions**,
  defers settings refreshes, and avoids writing to Blizzard's layout serializer.
- **Dimmed group frames retain their tooltips.** Fully hidden frames still
  suppress them.
- **The info bar sits below foreground UI**, the gold datatext keeps its gold
  color, and minimap general toggles use two columns.

### Aura Displays

- **Encounter-gated Aura Display groups activate during combat**, and individual
  editing previews stay visible when their group uses dynamic packing.
- **Aura Display imports reject malformed legacy duration and color settings**
  before they can cause rendering errors.
- **Aura Display visibility and sound processing do less repeated work during combat.**
- **Aura Displays have templates, guided setup, and custom creation.** Browse
  spells with clearer same-name variants, choose a display style, and configure
  its unit, position, and load conditions.
- **Aura Displays support nested groups, draggable previews, and share strings**
  for individual displays or whole groups, with configurable spacing,
  alignment, and sizing.
- **Aura Displays can collapse gaps left by inactive tracked icons.** Compatible
  grouped displays watching the same unit can also pack together.
### Quality of Life and Travel

- **QUI preserves other addons’ `/pull` commands** during registration and cleanup.

- **Auto-accepted summons now close Blizzard's confirmation popup**, including
  summons accepted after combat or a teleport finishes.
- **Group Death Alert settings now live under QoL → Notifications.** Existing
  pinned alert settings open the new tab.
- **Auto Accept Summons offers Off, Always, and Out of Combat modes.** Always
  waits until combat ends before accepting a still-active summon; Out of Combat
  leaves summons received during combat for manual confirmation.
- **Dungeon teleport buttons show cooldowns** in the Mythic+ window and world
  map, while the Info Bar travel flyout shows countdowns for known teleports.
- **QoL Automation settings stay in two columns**, including the final DELETE
  confirmation control.

### Damage Meter

- **Death recaps retain the selected death**, including when the same player
  dies multiple times and when the detail view refreshes.
- **Spell names and healing rows remain visible during combat.** When
  restricted values prevent combining healing and absorbs, the native healing
  view remains available.
- **Damage Meter rows open a reusable five-pane detail workspace** for spells,
  targets, attackers, and death recaps while row-hover details remain
  independent and interactive.
- **Historical sessions and individual windows have richer controls**, with
  persisted pane sizes and safer combat and Mythic+ state selection.
- **The detail workspace is resizable and remembers its dimensions.** Target
  rows drill down to their spells, and player hover details refresh item levels.

### Interface

- **The custom Info Bar Shop button is restored with its beta13 behavior.**
  It opens and closes Blizzard's shop and remains disabled during combat.
- **The MicroMenu finishes initializing after a temporary owner releases it.**
- **Rotate Minimap is available in minimap settings** and follows Blizzard's
  native rotation setting, including changes made outside QUI.
- **Action-bar suppression preserves Blizzard's secure button state**, and
  cooldown animations recover when faded buttons become visible again.
- **Cooldown Manager icons stay correctly hidden and anchored**, with more
  consistent viewer visibility when Blizzard refreshes it.

- **Weapon-oil timers refresh after entering an instance or changing zones**
  to recover missing enchantment durations.
- **Right-side Blizzard action bars recover their positioning after minimap
  updates.** The hidden Blizzard minimap cluster now recalculates its bounds
  after button visibility and layout changes.
- **Unrestricted Blizzard frames remain movable during combat**, while secure
  and proxy-owned frames continue to wait until combat ends.
- **Shared frame styling is more consistent** across Social, talents, Crafting
  Orders, tabs, text, and close controls.
- **QUI settings have clearer contrast and more consistent interaction states.**
  Tooltips fade smoothly, scrolling is animated, and buttons, checkboxes,
  dropdowns, tabs, and disabled controls share consistent visual feedback.
- **The Character window skin now covers its full chrome**, including the
  shell, bottom tabs, equipment and title popouts, and Reputation and Currency
  panes. Character and Inspect settings flyouts now share the same styling and
  scrolling behavior.
- **Initiative Tasks use QUI's Objective Tracker styling**, and Mail's Open All
  action keeps the Mail window above overlapping moved panels.
- **Incoming Casts can collapse readable hidden icons** so visible casts pack
  together while restricted targets retain fixed-width gaps.
- **The Battle Res Counter can hide without charge information**, removing its
  unavailable icon between supported encounters and in unsupported content.
- **Player chat bodies preserve literal apostrophes and percent tokens** instead
  of treating ordinary messages as format templates.

### Bags

- **Bank and guild-bank money dialogs accept exact gold, silver, and copper**
  and close cleanly with their bank window.
- **Guild-bank item transfers work from the displayed tab**, including the
  combined All view, and continue working after closing and reopening the bank.

### Combat UI

- **Cooldown Manager buff icons have growth direction and anchor controls.**
  Grow centered, left, right, up, or down; choose which edge stays fixed during
  free placement. Existing anchors to other frames remain in control.

- **Cooldown Manager respects per-spell duration-text visibility overrides**
  on native icons, and settings tooltips remain above the override panel.
- **Replaced Blizzard buff bars stay hidden through HUD fades**, and tracked
  bars refresh after closing Blizzard's Cooldown Manager settings.
- **Hidden unit-frame castbars can appear during combat** when Blizzard allows
  the frame to be shown.
- **Unit-frame castbars no longer trigger blocked resize errors during combat.**
- **Unit-frame castbars defer restricted layout changes** and retry their
  positioning without attaching to protected targets.
- **Boss castbars keep one cancellable retry while Blizzard restricts updates**,
  avoiding repeated retry chains during combat.
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
- **Incoming Casts and group-frame targeted-spell markers remain reliable
  through combat transitions** without creating new UI elements during combat.
- **Cooldown Manager leaves Blizzard's native viewer setting under Blizzard's
  control.** Replaced native buff bars hide during early loading and restore
  correctly when suppression is disabled.
- **Cooldown Manager shows setup instructions when Blizzard's native viewers
  are disabled**, without changing Blizzard's settings.

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

- Install this release over the existing QUI folders; saved variables remain in `QUIDB` and `QUI_StorageDB`.
- Manual installs must copy every top-level `QUI*` folder from the release zip, not only the `QUI` folder.
- If a feature does not open, check `/qui` > **Module Addons** before troubleshooting its settings.
- Some account-cache data, especially offline inventory and equipment, repopulates as each character logs in.
