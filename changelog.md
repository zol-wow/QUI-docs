---
layout: default
title: Changelog
nav_order: 5
---

# Changelog

This page summarizes the user-facing changes since the last mainline release. For every release entry and technical fix, see the full [CHANGELOG.md](https://github.com/zol-wow/QUI/blob/alpha/CHANGELOG.md).

## Current Release: 5.5.0-ptr-alpha10

{: .warning }
**Alpha branch targets: WoW 12.1.7 PTR and WoW Forever 1.60.1.** The branch's manifests declare interfaces 120107 and 16001. Forever support is experimental.

QUI 5.5.0-ptr-alpha10 includes the 5.3.2 beta updates through beta9, current
Forever build 70205 compatibility, and native-window skinning fixes. Earlier
Forever features and cumulative PTR and stable improvements remain included
below.

{: .important }
Back up your `WTF` folder before updating. Manual installs must copy every `QUI*` folder from the release zip into `Interface\AddOns\`.

## Unreleased Alpha Integration

The Alpha branch now includes Beta updates through 5.5.2-beta9, including
native-window styling, options navigation, restricted geometry fixes, and
Forever 70425 compatibility.
The latest published Alpha release remains 5.5.0-ptr-alpha10 and predates the
branch's 12.1.7 PTR corpus refresh. Retail API documentation and FrameXML now
follow PTR build 12.1.7.70424; Forever retains build 1.60.1.70425.
Mail window styling follows the native page buttons and instance refreshes,
including newly populated inbox rows and opened-mail attachments.

### Added

- **Encounter Debuffs** is a new Aura Display selection that hides player- and
  pet-applied debuffs and common noise. Existing displays keep their current
  selection until changed.
- **Spell Reminders** for Power Infusion, Innervate, and custom spells provide
  cooldown prompts, sounds, spoken alerts, and load conditions. Enable them
  under **Reminders → Spell Reminders**. Power Infusion adds offensive-buff
  tracking, group-frame highlights, focus alerts, and optional whisper-triggered
  priority or rotation lists; configured lists choose the recipient.
- **Recipe tooltips** show characters under **Can learn** and **Already known**,
  using each character's last checked result. Known or unlearnable recipes
  receive red tint in bags and storage when **Mark Unusable Items** is enabled.
  It defaults on for new profiles and the Starter Profile; existing settings
  are preserved.
- **Opening the Underlight Angler artifact** now shows the helper directly over
  the artifact window, on its tree tab. The overlay hides the Checklist tab;
  `/quiangler` opens the standalone helper on its Checklist tab.

### Fixed

- **Guild and Communities chat messages and input follow the global font**,
  including when the window loads after login.
- **Group frames appear reliably after a fresh login**, without requiring
  `/reload` to initialize them.

## v5.5.2-beta9

### Fixed

- Objective Tracker quest and profession recipe text now uses the correct layout
  height, preventing wrapped text and font changes from overlapping nearby items.
- Objective Tracker restores Max Height immediately during refreshes, including
  unrestricted combat updates, preventing extra objectives from briefly flashing
  before they are hidden.

## v5.5.2-beta8

### Fixed

- Expanded group aura settings retain their height so the Targeted Spells and
  Dispel sections below them no longer overlap the editor.
- Objective Tracker **Max Height** can expand beyond Blizzard's saved height,
  providing more room for tracked quests and recipes.

## v5.5.2-beta7

### Fixed

- Settings pages no longer flash or fade when switching modules or subpages.
  Navigation flyouts retain their entrance animation.
- Paging arrows use native images so fonts without triangle symbols no longer
  display missing-character boxes, including on vendor page buttons.

## v5.5.2-beta6

### Fixed

- Character and Inspect windows now recognize permanent glove enchants and show
  the missing-enchant marker when gloves have no enchant applied.
- Options navigation keeps its full scrolling area when the window is resized,
  including when layout updates briefly report a zero-height content area.
- World Map quest and campaign headers retain readable title and progress text
  after native updates, with campaign backgrounds below the text and spacing
  beneath the next objective.
- Objective Tracker collapse buttons keep their QUI plus/minus glyphs without
  native artwork reappearing behind them.

## v5.5.2-beta5 - 2026-10-17

### Fixed

- Spell Reminder settings list saved reminders, explain each control, and adapt
  their tabs and scrolling to the available space.
- Reminder previews preserve their position through settings updates. Power
  Infusion recipient previews are included in the drag area, and reminders
  expose their anchoring controls in Layout Mode.
- Layout Mode adds settings gears and a chooser for overlapping movers. Its
  settings panel adapts to its content, keeps controls from overlapping, and
  refreshes offsets and anchor selections when reopened.
- Reminder movers follow icon size and enable changes without resetting ongoing
  placement. Preview artwork stops during combat so normal cooldown displays
  and saved gameplay visibility take effect.
- Character window tabs retain the correct sizing and background when reopened.
  Disabling Character Pane enhancements leaves native tab sizing and controls
  unchanged.

## v5.5.2-beta4 - 2026-10-16

### Fixed

- Missing raid-buff icons now show the current spell rank after spell changes,
  while retaining saved spell selections and hidden-buff settings.
- The native external-event minimap shortcut remains visible and clickable when
  QUI hides the minimap backdrop.
- Character experience and reputation track backgrounds align with their native
  fill areas on WoW Forever.
- Stable windows no longer retain decorative footer, divider, and panel artwork
  over QUI styling. Native slot states, models, and controls remain intact.
- **Hide Border (Top)** supports the new WoW Forever minimap header textures and
  restores native hover and pressed effects when disabled or in Edit Mode.

### Compatibility

- Refreshed Retail and WoW Forever API and interface references. WoW Forever
  support remains experimental.

## v5.5.2-beta3 - 2026-10-16

### Fixed

- Fixed Lua errors when rounded surfaces update on Blizzard frames with
  restricted positioning. Rounded borders retain their native anchors and resume
  pixel alignment when measurements become available.

## v5.5.2-beta2 - 2026-10-15

### Fixed

- The Adventure Guide's Delves tab from Delve Companion no longer merges into
  the Dungeons tab. It sits between Suggested Content and Dungeons with QUI
  styling.

## v5.5.2-beta1 - 2026-10-15

### Beta Line

- Starts the 5.5.2 beta line from stable 5.5.1.
- Updates release versions only; runtime behavior is unchanged from 5.5.1.

## v5.5.1 - 2026-10-13

### Fixed

- Fixed a Lua error that could interrupt the loot window when transmog markers
  were enabled, including for items such as Stinging Nettle.

## v5.5.1-beta1 - 2026-10-13

### Fixed

- Fixed a Lua error that could interrupt the loot window when transmog markers
  were enabled, including for items such as Stinging Nettle.

## v5.5.0 - 2026-10-11

> **Stable release.** One download supports WoW 12.1.0 live Retail,
> WoW 12.1.5 PTR, and WoW Forever 1.60.1 (interfaces 120100, 120105, and 16001).
> Forever support remains experimental.

QUI 5.5.0 brings the improvements since stable 5.3.1 to the stable channel,
including Spell Reminders, the Underlight Angler Helper, Satin appearance,
expanded native-window styling, and Forever compatibility.

### Added

- **Spell Reminders** provide cooldown prompts, sounds, spoken alerts, and load
  conditions for Power Infusion, Innervate, and custom spells. Enable them under
  **Reminders → Spell Reminders**; they default to Off. **Power Infusion
  coordination** adds offensive-buff tracking, group-frame highlights, focus
  alerts, and optional whisper-triggered priority or rotation lists. Configured
  lists choose the recipient. Estimated early alerts are optional and never
  mark a spell ready.
- **Underlight Angler Helper** provides an unlock checklist, a restored artifact
  trait tree with purchase confirmations, and fishing tips for alts. The module
  ships enabled and can be toggled under **Module Addons**. `/angler` or
  `/quiangler` opens the standalone Checklist; opening the Underlight Angler
  artifact shows the helper on its tree tab, without the Checklist tab.
- **Quality of Life → Automation** adds optional automatic resurrection
  acceptance and appearance-buff removal, both Off by default. Resurrection
  modes are separate for dungeons, raids, PvP, and the open world; hold Shift to
  keep an offer manual. Appearance removal lets you select supported
  transformations and profession outfits, waits for combat and aura
  restrictions to end, and preserves fishing outfits while casting. **Keystone
  Reroll Reminder** shows “Re-roll key?” after eligible dungeon completions;
  it defaults to enabled for 15 seconds, with Off and 15/30/60-second controls.
- **Damage Meter result sharing** sends the selected metric and segment to
  Party, Raid, or Whisper from **Share Results**. Choose Top 3, Top 5, Top 10,
  or All; the default is five data rows, All is capped at 40, and reports use
  the shared chat-throttling queue.
- **Encounter Debuffs** is a new Aura Display selection that hides player- and
  pet-applied debuffs and common noise. Existing displays retain their selected
  filter until changed.

### Improved

- **Satin appearance and rounded native controls** give QUI surfaces, bars,
  icons, and Blizzard windows a consistent finish while retaining configured
  colors and native interactions. Satin is the default; the profile-selectable
  Legacy finish remains available. **Objective Tracker appearance** now offers
  theme, custom-color, transparent, or Blizzard-opacity backgrounds,
  independent opacity, and shared or custom border colors. These controls are
  included in profile exports.
- **Settings navigation and previews** have streamlined layouts, responsive
  sizing, section navigation, updated search routes, and translations. Pages
  build when selected and search jumps wait for layout to settle. Nameplate
  previews fit their viewport, with preview controls accessible by scrolling.
- **Layout Mode and Aura Displays** preserve precision when moving or nudging
  anchored groups. Shift-drag aligns frame edges, detaching clears pending
  anchors, and right-click settings for aura displays and groups expose
  **Anchor To**, attachment points, and offsets. Vertical growth, wrapping,
  outlines, and row spacing match live layouts; action-bar size and spacing
  previews update their buttons while dragging.
- **Recipe tooltips and bag tinting** show which characters can learn a recipe
  or already know it, using each character's last checked result. Known or
  unavailable recipes receive red tint when **Mark Unusable Items** is enabled;
  it defaults on for new profiles and the Starter Profile, while existing
  saved choices remain intact. **Damage Meter text without outlines** gains a
  black shadow and readable fills on bright bars, preserving hue and opacity.
- **Forever compatibility** includes native swing timer appearance and Layout
  Mode controls, native combo points and druid mana, character stats and sidebar
  navigation, bank and group frames, mouse-button clickcasting, Quick Salvage,
  and optional Legacy System and Pet Stable skins, both Off by default.
  Blizzard handles swing timing. Profile exports identify their client and
  reject imports tagged for a different client; existing untagged exports remain
  compatible. GSE integration remains unavailable on Forever.

### Fixed

- **Combat and cooldown updates** respect native receiver restrictions and
  repaint deferred Action Bar, Group Frame, bag, and world-map teleport
  cooldowns when allowed. Consumable-check layout waits until combat ends,
  Spell Reminders retry initialization when restrictions lift, and Cooldown
  Manager reuses released icons. Hidden player castbars retain Edit Mode
  geometry, and action-bar range indicators avoid duplicate scans while keeping
  range tint active independently of usability coloring.
- **Profiles survive character-identity changes**, including existing regional
  character-name changes and Forever talent-group specialization switching.
  Existing long profile names remain selected after login and work with profile
  and specialization selection; new names retain the supported length limit.
  Forever reload buttons and confirmation dialogs use the supported reload path.
- **Native windows retain their layout and controls**, including World Map
  navigation and campaign headers, character tabs and model controls, and
  protected Spellbook sizing after combat. Rounded surfaces avoid errors from
  restricted coordinates. Journals, achievements, professions, auctions,
  social panels, mail, and interaction dialogs style recycled rows correctly;
  hidden bank, guild-bank, and macro icon selectors no longer fail before first
  opening. Standalone item and pet tooltips keep native content layout, status
  bars retain hover tooltips, and Suggested Content paging arrows remain readable.
- **Objective Tracker and loot layouts stay consistent.** The tracker retains
  its configured anchor during native panel updates, and scenario text stages
  keep native spacing and height with QUI-styled headers, countdowns, and bars.
  Loot notifications refresh changed or empty slots; loot windows preserve
  scrolling and click controls, and timers follow remaining time. Loot History
  has matching timer borders, scrollbar styling, and a visible resize grip;
  setting changes take effect on reload, with consistent installed artwork if
  reload is deferred. Encounter power bars retain native timers.
- **Bags, group frames, chat, and movable panels refresh reliably.** Category
  bags honor sort key and reverse settings after sorting, stack changes, and
  item-detail updates. Group frames initialize on a fresh login without a
  reload. Guild and Communities messages and input follow the global font;
  unroutable channel notices are skipped and guild communication respects
  speaking permissions. Gold tooltips deduplicate legacy realm-name aliases.
  Selected movable panels stay in front, Talents opens safely when mover setup
  is disabled or deferred, and loot windows and previews use the supported
  item-quality color API.

## v5.5.0-beta3 - 2026-10-11

### Fixed

- World Map navigation and campaign headers preserve native layout state while
  retaining QUI styling.
- Scenario text stages retain native spacing and height while their headers,
  countdowns, and status bars keep QUI styling.
- Loot History's countdown fits its track and follows remaining time, with
  matching timer borders, scrollbar styling, and a visible resize grip.
- Loot History setting changes take effect on reload. Deferring the reload keeps
  the installed timer layout and artwork consistent.

## v5.5.0-beta2 - 2026-10-11

### Added and Changed

- **Objective Tracker appearance controls** offer QUI theme, custom-color,
  transparent, or Blizzard-opacity backgrounds, independent background opacity,
  and shared or custom border colors. These settings are included in profile
  exports.
- **Settings pages build when selected**, with section and search jumps waiting
  for the layout to settle. Nameplate previews fit their viewport and keep
  preview controls accessible by scrolling.

### Fixed

- The Objective Tracker stays at its configured anchor during native panel
  updates, and Layout Mode moves its holder with consistent scaled coordinates.
- Scenario headers, countdowns, and status bars retain QUI styling during native
  widget updates. Simple stages use tighter spacing while preserving native
  timers, layout, and interactions.
- Character tabs retain native state and ownership. Protected Spellbook control
  sizing waits until combat ends.
- Rounded surfaces handle restricted native coordinates and dimensions without
  secret-value comparison or arithmetic errors.
- Forever bank bag slots receive quality borders, and unavailable live bank
  choices are disabled. Social invite borders fit their controls, and the
  Encounter Journal keeps its circular overview portrait.

## v5.5.0-beta1 - 2026-10-10

> **Alpha promoted to Beta.** One download supports WoW 12.1.0 live Retail,
> WoW 12.1.5 PTR, and WoW Forever 1.60.1 (interfaces 120100, 120105, and 16001).
> Forever support remains experimental.

### Added and Changed

- **Satin appearance** provides a profile-selectable finish across QUI surfaces
  and icons, with matching Starter profile defaults.
- **Rounded native panels and controls** extend consistent styling across
  Blizzard windows, character controls, gameplay displays, bars, and icons while
  preserving native interactions, configured borders, and profession colors.
- **Native window refinements** cover journals, achievements, professions,
  auction listings, social panels, mail, and interaction dialogs, including
  recycled rows and controls. Character and Inspect windows retain native
  model controls and Forever sidebar geometry.
- **Options navigation and previews** use streamlined layouts, responsive sizing,
  and updated search routes and translations.
- **Forever client support** includes native swing timer controls, resource bars,
  character stats and sidebar behavior, bank and group frames, clickcasting,
  Quick Salvage, and optional Legacy System and Pet Stable skins. Profile exports
  identify their client to prevent importing settings from a different client.
- **All Beta11 features and fixes remain included**, including Spell Reminders,
  Encounter Debuffs, recipe knowledge tinting, the Angler overlay checklist,
  Guild and Communities fonts, and cold-login group frame initialization.

### Fixed

- Existing bag profiles retain their saved unusable-item tint preference.
- Spell Reminders retry initialization when execution restrictions end.
- Existing long profile names remain selected after login and continue to work
  with profile selection and specialization switching. New profile names retain
  the supported length limit.
- Existing profiles survive regional character-name changes, and Forever
  specialization profiles follow the native talent groups.
- Hidden bank, guild-bank, and macro icon selectors no longer trigger a
  ScrollBox initialization error before their first opening.
- Standalone item and pet-ability tooltips receive matching chrome while
  preserving their native content layout. Status tracking bars retain hover
  tooltips, and Suggested Content paging shows readable arrows.

## What's New in 5.5.0-ptr-alpha10

### Forever Native Compatibility and Skinning

- **Forever build 70205 uses QUI's shared secure controls again**, including
  owned action buttons, paging, flyouts, press-and-hold, group headers, hover
  keyboard/wheel clickcasting, chat visibility, and protected panel movement
  and scaling. This follows Blizzard's repaired secure-environment load order.
  GSE integration remains unavailable, and Quick Salvage remains outside combat.
  Native Cooldown Manager preview textures now stay under Blizzard's ownership.
- **The current Forever character sidebar supports all four tabs**: stats,
  equipment, titles, and pet. Character and Inspect skins follow native mode
  tabs and acquired stat rows; switching away from the character equipment
  page removes QUI overlays and restores the native panel bounds.
- **Existing skins follow the native windows loaded on Forever**, including
  Group Finder, professions, Collections, and currency/statistics panels.
  Flight Map skinning also covers the native taxi window, and Guild Registrar
  skinning covers the guild charter window. New **Legacy System** and **Pet
  Stable** skins are optional and default to Off; native selection, rewards,
  dragging, and purchase controls retain Blizzard's behavior.
- **Loot updates retain the open window's position and make every slot
  reachable**, preserving modified-click and master-loot context. Roll timers
  follow native remaining time, including queued and restored rolls; cancelling
  all rolls clears their queue. Encounter power bars handle maximum-power
  changes, while vehicle health/mana visibility, buff timers, and pitch controls
  stay native. Vehicle geometry changes wait until combat ends.
- **Selective skin exports and imports retain optional panel choices**, and
  settings search includes both client variants while showing controls for
  your client. Forever omits the Keystone skin control because its client does
  not load that native window. See the
  [Forever support strategy](blizzard/forever-support-strategy).

### Included Beta Additions

- **Keystone reroll reminder duration** can be set to **15, 30, or 60 seconds**
  under **Quality of Life → Automation**. The default remains 15 seconds;
  changes apply to the next reminder and are included in profile exports.
- **Underlight Angler Helper** adds an unlock checklist, a restored artifact
  trait tree with purchase confirmations, and fishing tips for alts. Open it
  with `/angler` or `/quiangler`; configure it under **Module Addons**.
- **Keystone Reroll Reminder** can be enabled or disabled under **Quality of Life
  → Automation** and defaults to enabled.
- **Share damage-meter results** from the window header's **Share Results** menu
  to Party, Raid or Whisper. Select **Rows → Top 3 / Top 5 / Top 10 / All**;
  five data rows plus the heading is the default, and All is capped at 40 rows.
  The choice is saved per window. Instance groups use instance chat, and outgoing
  reports use the shared chat-throttling queue.
- **Keystone reroll reminder** displays a large “Re-roll key?” prompt after a
  non-practice dungeon completion when the completed key level is at least your
  refreshed owned key level. The prompt expires after the configured duration,
  which defaults to 15 seconds.
- **Optional appearance-buff removal** under Quality of Life → Automation lets
  you choose which supported transformations and profession outfits to remove.
  The feature defaults to Off.
  Removal waits until combat and aura restrictions end, and fishing outfits
  stay active while casting. Equipped transmog and class forms are unchanged.

### Included Beta Fixes

- **Shift-drag anchoring in Layout Mode aligns frame edges flush**, with left,
  center, or right alignment above and below a target, and top, center, or bottom
  alignment beside it. Moving and nudging anchored frames preserve alignment
  without rounding drift, and detached frames stay detached when changes are saved.
- **Aura Display outlines and previews match vertical growth and wrapping**,
  including icon spacing, row spacing, and edge alignment. Right-clicking an
  individual display or group in Layout Mode opens its Position controls,
  including **Anchor To** and offsets.
- **Action-bar buttons update while dragging size and spacing settings**,
  keeping the preview consistent with the actual button layout.
- **Category bag views honor the selected sort key and reverse order** and
  refresh when sort settings, item details, or stack counts change. Completing
  a sort also refreshes the bag view.
- **Keystone reroll reminders retry unavailable owned-key data for up to five
  seconds** after completion instead of stopping after the first check.
- **Consumable-check layout waits until combat ends**, including ready checks,
  avoiding protected UI work during combat.
- **Gold tooltips no longer double-count characters whose realm name changed
  punctuation or spacing**, such as Kelthuzad and Kel'Thuzad. Removing a
  character also clears matching legacy entries so they stay removed.
- **Action-bar range indicators avoid duplicate full-bar scans** on clients with
  native range events. Range tint remains active when usability coloring is off,
  and configured hidden buttons are tracked before they become visible.
- **Chat skips channel notices that have no valid destination**, matching native
  chat routing while preserving invitations and system errors.
- **Guild addon communication respects speaking permissions**, avoiding automatic
  guild messages when you cannot speak in guild chat. Group communication remains
  available.
- **Opening Talents avoids a panel-initialization error** when movable-panel
  setup is disabled or deferred.
- **Resurrection automation accepts eligible raid offers reliably**, including
  offers without a visible popup. Out of Combat mode checks the resurrector's
  combat state, accepts unidentified offerers, and preserves the Shift override
  and recovery exclusions.
- **Cooldown Manager reuses released icons**, preventing abandoned frames from
  accumulating during repeated layout changes. Hiding the Blizzard player
  castbar also preserves the geometry needed by Edit Mode.
- **Movable Blizzard panels stay in front when selected**, including during
  merchant updates. Party keystones follow the instance window, the lust timer
  stays below other panels, and extra ability buttons retain safe layout ownership.
- **Battle.net friend invite menus hide disabled entries for other games**,
  keeping the available invite choices easier to find.
- **Damage Meter text is easier to read without font outlines.** Bright fills
  automatically darken behind light text while preserving their hue and opacity,
  and unoutlined window text gets a black shadow. Dark-text and outlined bar
  styles keep their original fills.

## What's New in 5.5.0-ptr-alpha9

Historical release notes from September 18, 2026. The storage and verification
caveats below describe that release at the time; they are not current Alpha10
limits. The alpha8 upgrade guidance still applies.

### Account-Wide Storage Restored

- **Forever and Retail now both use account-wide `QUIDB` and `QUI_StorageDB`.**
  Alpha8's Forever-only character-local workaround has been removed because it
  did not establish a reliable fix. Early SavedVariables loading is retained.
- **The reported Forever persistence issue remains unresolved.** Restoring the
  original storage declaration does not establish that settings will persist.

{: .warning }
**Before updating from alpha8 on Forever, export any profile settings you want
to keep and back up your `WTF` folder.** Alpha8's character-local data is **not
automatically migrated back** to account-wide storage. After updating, import
your same-client profile export to restore those settings if needed. Profile
exports do not include tracked data in `QUI_StorageDB`; keep the full `WTF`
backup to preserve that data.

### Included from Alpha8

- **Native swing timers now have QUI controls** under Gameplay → Swing Timers.
  Configure main-hand, off-hand, and ranged bars independently, including size,
  texture, text, and visibility. Layout Mode previews all three bars and lets
  you move and resize them while Blizzard continues to handle weapon timing.
- **QUI's bank and group frames now have Forever support.** The custom bank
  uses native bag equipment and purchase controls, with paging in the All view.
  Party, raid, and spotlight frames use native group-header controls; mouse
  buttons and modifier clickcasting are available.
- **Quick Salvage works outside combat**, and Blizzard Frame Mover can position
  registered, open native panels while preserving Blizzard's clamping.
- **Resource bars support rogue and energy-form druid combo points**, plus mana
  in other non-mana druid forms. Defensive suggestions use known spells from
  upstream class metadata; manual spell IDs remain available.
- **Character stats follow Forever's native categories, values, and tooltips**,
  including corrected resistance labels. The stats panel fits its native
  viewport, refreshes after stat changes, and follows the correct sidebar tabs.

### Included from Alpha7

- **Auto Accept Resurrection** under QoL → Automation offers separate settings
  for dungeons, raids, PvP, and the open world. Each defaults to **Off**, with
  **Out of Combat** and **Always** options. **Always** also accepts battle
  resurrections during combat. Hold **Shift** when an offer arrives to keep it
  manual; offers with resurrection sickness or a recovery delay stay manual.
- **Damage Meter automatically darkens bright bars behind light text when an
  outline is disabled**, improving readability for colors such as priest white
  and rogue yellow. No-outline text also receives a shadow. This applies to
  the main meter, spell and target breakdowns, and death recaps.
- **Forever profile identity migration preserves character selections and
  Cooldown Manager ownership within the loaded database.** This is separate
  from the storage declaration change above, which does not migrate alpha8's
  character-local data.
  Invalid profile names are rejected before creation,
  selection, or spec assignment; invalid saved spec mappings are skipped
  without deleting their data.
- **Forever Reload buttons and confirmations use the client's supported
  reload action**, including the settings sidebar and post-combat prompt.
- **Forever character tabs and reputation bars avoid the reported layout and
  styling errors.** Native main-bar dividers stay hidden, the Info Bar Legacy
  button opens its panel, and item-quality colors use the supported API.
- **Secure-execution and Cooldown Manager workarounds now apply across Forever
  builds**, retaining native action-button and group-control behavior and
  avoiding missing-icon errors in Edit Mode previews.

### Included from Alpha6

- **The same alpha archive now supports WoW Forever 1.60.1 and Midnight
  12.1.5 PTR.** Type `/qui client` to check the detected client and build.
- **Forever keeps Blizzard's action buttons** while
  avoiding its reported secure-execution failure. QUI styles and positions
  native action bars, waits for settings registration, and
  prevents native layout changes from creating circular anchors.
- **Collections tabs open and switch without the reported script-hook error**,
  keeping their icons and selected-tab highlight. Chat hyperlink handling
  also avoids constructing an incomplete native chat frame.
- **New profile exports identify their client**, and imports reject a different
  tagged client before applying settings. Older untagged exports remain accepted.

### Alpha9 Limits (Historical)

Alpha10 restores the secure controls listed above; the following describes
alpha9 as released on September 18, 2026.

- **GSE integration remains unavailable.** Hover keyboard and mouse-wheel
  clickcasting are also unavailable; saved bindings are retained.
- **Protected-frame movement is limited to registered, open native panels.**
  Arbitrary protected popups and protected scaling remain unsupported. Native
  action-bar controls remain subject to Blizzard's Edit Mode limits.
- **Defensive suggestions are not a complete Forever dataset.** Known-spell
  filtering does not verify every effect, and other resource mappings still
  need client-specific verification.
- **Forever persistence remains unresolved.** Both clients use account-wide
  storage again, but alpha8's character-local data is not automatically migrated.
- Headless checks cover both clients. Combat behavior, native skins, spell/spec
  defaults, and other gameplay-specific features still need live verification.
  See the [Forever support strategy](https://github.com/zol-wow/QUI-docs/blob/alpha/blizzard/forever-support-strategy.md).

### Included PTR Features and Fixes

- **Stable 5.3.1 fixes are now included**, covering native buff placement,
  centered buff rows, target and focus aura refreshes, chat realm names,
  new raid-member sizes, upgraded bag item levels, and imported macro names.
- **Pandemic glows follow the configured icon size when WoW restricts
  frame dimensions**, including after resizing, while retaining the chosen
  glow style, color, and offsets.
- **The custom Info Bar Shop button is restored**, preserving existing settings
  and its established opening and closing behavior.
- **PTR aura controls add optional caster labels, pandemic pulses, and entry
  flashes.** Search uses native Unicode case folding.
- **Possession abilities stay visible and keep your usual keys**, including
  after fade timers expire. Raid markers remain visible with restricted values.
- **Encounter-gated Aura Displays prepare before combat**, and individual
  previews restore group packing when closed. Imports validate legacy duration
  settings, and aura sound settings reconcile without render-time changes.
- **Damage Meter keeps the selected death recap across refreshes**, and boss
  castbars coalesce deferred retries and cancel them when the cast ends.
- **Cooldown Manager explains when Blizzard's native viewers are disabled.**
  Microbar ownership recovers after Blizzard releases it.

## Integrated from Stable 5.3.1


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

## Included Features and Improvements

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
- **The custom Info Bar Micro Menu includes the Shop button**, preserving its
  existing visibility setting and store toggle behavior.

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
