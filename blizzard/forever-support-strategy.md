# QUI Retail and WoW Forever support strategy

Research and implementation date: 2026-09-17. Status: initial Alpha support implemented and headless-validated; first live boot reported; build 69893 secure-execution workaround awaits live retest.
QUI source inspected: Alpha `ee58125e01f7b1da4d6e967a4d375ee914691c1d`.

**Alpha now uses one QUI codebase, two isolated client corpora, and one archive declaring both Retail and Forever. Client-specific changes are limited to documented API, bank, library, resource, and profile differences.**

## Implemented Alpha support

| Area | Current behavior |
|---|---|
| Client and packaging | All 14 first-party TOCs declare `120105, 16001` (12 addons ship). `core/client.lua` recognizes the verified `1.60.x` version family; `/qui client` prints flavor, version, build and interface. Release metadata is derived from all shipped TOCs and advertises `12.1.5` and `1.60.1`. |
| Corpus and checks | Pinned Forever FrameXML and API docs live under `tests/clients/forever/`, with separate taint index and LuaLS definitions. Extractors fail on bad documents. Local gates and CI check both corpora without altering Retail's derived data. |
| Shared runtime | Modern cooldown and unit/resource percentage paths use API capabilities. Specialization callers prefer `C_SpecializationInfo` APIs. RangeCheck preserves secret-safe GUID/pet handling on Forever. Unsupported bundled LibOpenRaid initialization is disabled there. |
| Bank and resources | Bank scans and sorting derive tab ranges from the client's enums. Forever retains Blizzard's bank UI and bag-equipping controls. Primary resource follows `UnitPowerType`; Retail-specific secondary resource bars are disabled on Forever pending verified mappings. |
| Profiles | New full/selected/nameplate exports carry client metadata; imports reject a different tagged client before applying settings. Metadata is not stored as profile settings. Existing untagged exports remain accepted for compatibility, so their client origin cannot be enforced. |

Validation: `JOBS=12 bash tools/test.sh` passed all nine gates, including 971 unit test files, 12 profile fixtures, both strict taint analyses, deterministic regeneration for both clients, and TOC parser checks. Focused regressions exercise real library initialization, modern API routing, both bank enum topologies, specialization without deprecated globals, and cross-client full/nameplate imports. The release packaging and metadata-generation blocks were exercised in temporary staging without upload. No commit, push or release has been performed. Drew subsequently supplied the first live boot log, described below.

Alpha limits: native Forever bank; no Forever secondary resource bars or bundled LibOpenRaid gameplay dataset. Automatic defensive-spell suggestions dependent on that dataset are unavailable. Spell/spec defaults, gameplay-specific modules, native skins and combat behavior still require live checks. A green static/headless suite is not full feature parity.

Live identity is now verified: Drew reported `/qui client` output `forever 1.60.1 (build 69893, interface 16001)`. The same boot produced repeated `RestrictedExecution.lua:79` failures with its captured local `loadstring_untainted=nil` while QUI built action bars.

### Build 69893 restricted-execution workaround

The source points to a Blizzard load-order defect: [EnvironmentCleanup.toc](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_EnvironmentCleanup/Blizzard_EnvironmentCleanup.toc) is `LoadFirst` but its dependency on `Blizzard_RestrictedAddOnEnvironment` permits only `classic, standard`, omitting `camelot`. The [cleanup implementation](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_EnvironmentCleanup/Mainline/EnvironmentCleanup.lua#L279) clears the global compiler. [RestrictedExecution](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_RestrictedAddOnEnvironment/RestrictedExecution.lua#L22) captures that global at load time and invokes it at line 79. The missing captured compiler is runtime-confirmed; the dependency omission is the source-supported explanation, not a directly observed startup trace.

`core/client.lua` marks only Forever build **69893** with `restrictedExecutionUnavailable`. QUI restores its action-bar presentation on the original Blizzard buttons and preserves native party/raid controls. Casting, paging, flyouts, press-and-hold and binding dispatch remain owned by Blizzard; QUI supplies button styling, text, sizing, spacing, rows, saved anchors and button-count reductions without compiling secure snippets. QUI clickcasting, Quick Salvage and protected-frame mover placement also skip their affected paths. Chat retains its existing ordinary Show fallback. The travel flyout now uses the native visibility driver `[combat] hide; ignore`, keeping manual open/close and combat hiding without compiling a snippet.

Do not test addon-visible `loadstring_untainted` for availability: Blizzard intentionally clears that global on working clients too. Do not replace it with ordinary `loadstring`; that cannot repair the captured local or recreate secure execution. The workaround preserves saved settings and leaves Retail's owned control paths active. Other Forever builds are not automatically classified as broken or verified fixed; repeat the live check when the build changes.

Workaround validation: all nine gates passed again, including **975 unit test files**, both strict client taint analyses, compile/lint, corpus freshness and generated-output checks. Native-preservation regressions fail when their guards are removed; travel behavior is exercised against the pinned Blizzard state-driver implementation.

### Restored action-bar presentation and chat initialization

The native presentation path in `actionbars_native.lua` preserves each original button's ID, parent, `.bar`, action attributes, scripts and event registrations. The pinned [SecureTemplates](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_FrameXML/SecureTemplates.lua) resolves native action pages through the original bar; native binding dispatch also selects override buttons when required. Creating replacement buttons with only a numeric page attribute would lose those contracts and combat press-and-hold updates.

QUI uses constant native visibility drivers for count reductions. [ActionBarMixin.UpdateShownButtons](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_ActionBar/Shared/ActionBar.lua#L203) respects their `statehidden` attribute during native combat refreshes. Increasing the count restores both buttons and their original parent containers. Geometry and skin updates wait until combat ends. QUI never installs override bindings on this path. Standard secondary bar enable switches use the native Settings proxy; Blizzard Edit Mode still controls each bar's maximum button count and contextual visibility. QUI caps its count to that maximum and explains it in the slider tooltip. Native proc glows and action behavior remain active; full owned-button feature parity is not claimed.

A subsequent live boot exposed a Settings registration race: `Settings.GetValue` returns nil before registration, while `Settings.SetValue` raises an error. The Settings namespace and action-bar frames can exist before their settings. The pinned registrar waits for `VARIABLES_LOADED` and `PLAYER_ENTERING_WORLD`, then emits documented `SETTINGS_LOADED`. QUI now checks `Settings.GetSetting` before each proxy write and refreshes on `SETTINGS_LOADED`, retaining combat deferral. This matches Blizzard's own `ActionBarController.lua:98–108`. Expanded regression coverage executes Blizzard's real Settings accessors for all seven secondary bars; the previous code reproduces the exact reported error. No direct toggle API bypass or error suppression is used.

A further live reload exposed an anchor cycle: Camelot enables `ACTION_BARS_RELATIVE_TO_BASE_POSITIONING`, and `EditModeManagerFrameMixin:UpdateBottomActionBarPositions` anchors default secondary bars to `MainActionBar`. A saved QUI relationship in the reverse direction therefore cycles even when the QUI profile itself is acyclic. Each native bar now uses an independent ordinary `QUI_ActionBar_<key>` presentation frame for QUI position/size relationships. All holders capture their initial screen position once before any profile anchor is applied. Native bars and original buttons attach geometrically to these holders while retaining their original parents and secure ownership. Native relayout can no longer introduce a reverse dependency into QUI's holder graph. Repeated refresh never recaptures a holder position from a moving native bar; tests cover the otherwise resulting drift, including a target with no saved anchor.

Native bar alpha follows holder fading. Holder hide/show requests update the existing button visibility drivers, and native visibility is mirrored back after refresh without becoming a permanent user-hidden state. The shared anchor-hidden state is honored even when a holder was already hidden. Combat defers layout and holder visibility synchronization until regen; native controls still follow Blizzard's own combat visibility immediately. In-game validation must include anchor-dependent visibility around pet/stance/vehicle transitions.

The reported chat failure is separate: `ChatFrameTemplate` runs `ChatFrameMixin:OnLoad`, which expects a `ScrollToBottomButton` supplied by `FloatingChatFrameTemplate`. QUI's hidden hyperlink handler now inherits only `InlineHyperlinkFrameTemplate`, retaining link clicks and hover behavior without constructing an incomplete chat frame. The regression reproduces the reported error with the old inheritance against both pinned clients.

Native action regressions execute the pinned state driver, action calculation and visibility code. They cover original control ownership, geometry, count hide/restore including hidden parent containers, native count limits, combat deferral, bonus pages and override binding dispatch. Replacing the visibility driver with ordinary `Hide()` makes the combat visibility assertion fail.

Restoration validation: `JOBS=12 bash tools/test.sh` passed all nine gates with **976 unit test files**, both client taint contracts, compile/lint, profile fixtures, corpus freshness and regenerated search/i18n checks. The subsequent Settings registration and independent anchor-holder fixes passed the same nine gates with 976 unit files; latest log: `/tmp/qui-forever-anchor-holders-final.log`. Changes remain uncommitted.

Next live acceptance: reload the patched Alpha on build 69893, verify QUI styling/position and an action click/keybind, then test paging, flyouts, combat entry/exit, Edit Mode count changes and native party/raid controls. No headless test proves in-game casting or repairs Blizzard's compiler.

### Paging-arrow anchor stability

Drew subsequently reported that the main-bar page arrows jump during paging and settle afterward. Pinned source confirms `ActionBarController_OnEvent` → `ValidateActionBarTransition` → `MainActionBar:Show()` → `UpdateVisibility` → Edit Mode bottom-bar positioning. That native pass reanchors MainActionBar before QUI's deferred presentation refresh; the native paging frame followed that movement while the action buttons already used QUI's stable holder.

Native presentation now anchors `ActionBarPageNumber` to the same holder once, preserving its original parent, native scripts, and XML offset (`BOTTOMRIGHT` to `BOTTOMLEFT`, -4, 9). Repeated refreshes leave this anchor alone. Generated region documentation says `ClearAllPoints` “Clears all points and immediately invalidates the rect”; the one-time setup avoids repeated invalidation. The regression reproduced movement before the deferred refresh, then passed with stable controls, native page labels/action slots and unchanged parent ownership. All nine gates passed with 980 unit files; log `/tmp/qui-forever-paging-anchor-final.log`. Drew subsequently confirmed the paging result looks good in-game; changes are uncommitted.

### Edit Mode preview icon bounds

Drew reported `IconDataProvider.lua:144` with `BaseIconFilenames=nil` when entering native Edit Mode on Forever 69893. `CooldownViewer.lua` creates an extras-only spellbook icon provider, then requests placeholder indices based on layout/category without bounding them to the available icons. With ten known-spell extras, indices 12 and 13 leave the valid list and index an uninitialized base macro-icon cache. The same defect exists in both pinned source versions; current live evidence is Forever. Opening a normal macro icon picker can incidentally initialize that cache, and closing it can clear it again.

`cdm_editmode_policy.lua` now installs an exact-build workaround on native cooldown viewer items, including already-active and newly acquired frames. Only their edit-mode fallback texture uses a lazy extras-only provider and wraps its index through `GetNumIcons()` (which always includes the question-mark entry). Native real spell/item/aura textures retain precedence, and native edit-mode indices/durations stay intact. No global provider method, private cache or native spell data is replaced. All nine gates passed (exit 0), including 981 unit files, 12 profile fixtures and both strict client taint analyses; log `/tmp/qui-forever-editmode-icons-final.log`. Live Edit Mode retest is pending; changes remain uncommitted.

## Micro-menu, bag bar, Info Bar and datatext support

Implemented 2026-09-17 after Drew authorized the takeover and related Info Bar/datatext audit. Native initialization now includes `microbar` and `bags`, reusing the existing Retail builders with ordinary containers and built-in visibility drivers on build 69893. QUI controls position, columns, size, spacing, clickthrough and fades; original native buttons retain their click/drag/tooltip behavior. Refresh, combat recovery, context yield/reclaim and Edit Mode position saving include both bars.

Camelot's loaded overrides determine the actual controls:

- `Blizzard_MicroMenu/Camelot/MicroMenuContainerOverrides.lua` supplies Spellbook, Talent and Legacy instead of Retail's PlayerSpells and Achievement entries. The takeover uses generated native order plus initialized layout membership, excluding dormant Retail globals and game-rule-disabled entries. Active Help occupies its own slot when Store is absent; the shared Store/Help overlap remains otherwise.
- `MainMenuBarBagManager:EnumerateBagButtons()` supplies registered bag controls, excluding gamepad counterparts. `C_ActionBar.ShouldShowKeyring` determines keyring inclusion; the disabled expand toggle stays excluded. Existing native bag/keyring artwork and proportions remain.
- Camelot `MicroMenu.BorderArt` and `BackgroundArt` are suppressed during QUI ownership and restored when native UI owns the menu. Original button anchors are captured once, so repeated refreshes do not corrupt context handoff.

Info Bar's menu substitutes Legacy for Achievements on Forever and uses the native Legacy bootstrap and unlock state. Travel spell availability uses documented `C_SpellBook.IsSpellInSpellBook` rather than the optional deprecated `IsSpellKnown` alias. Native panel dispatchers route Group Finder and Talents to the appropriate client UI.

Forever's loaded `Blizzard_PlayerSpells/Camelot/ClassTalents/Blizzard_ClassTalentsFrame.lua` activates Primary/Secondary talent groups with `C_SpecializationInfo.SetActiveSpecGroup`; API namespace presence does not make Retail specialization/loadout switching appropriate. The Info Bar spec switcher and Player Spec datatext follow unlocked native groups and active-group refresh events. Retail retains its specialization/loadout behavior. Other audited data providers and LDB hosting require no additional source-proven adaptation in this step.

Headless regressions exercise actual Camelot micro initialization, bag manager inventory, native Group Finder/Talents/Legacy dispatch, keyring on/off, Help fallback, dual-spec unlock/activation, combat guards, utility visibility, artwork, layout and deferred recovery. Validation: `JOBS=12 bash tools/test.sh` passed all nine gates (exit 0), including **980 unit test files**, 12 profile fixtures, both strict client taint analyses, lint/compile and generated data checks. Log: `/tmp/qui-forever-utility-infobar-final.log`. Changes remain uncommitted. Live acceptance remains required: utility click/drag/tooltip behavior, fades, profile reload and combat/context transitions cannot be established completely by headless checks.

## 1. Verified sources and what they establish

The new corpus exists in the same upstream repository already used by QUI:

| Target | Upstream branch | Build | Pinned commit |
|---|---|---|---|
| Forever beta | `forever` | `1.60.1.69893` | [`4d5d706b`](https://github.com/Gethe/wow-ui-source/tree/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069) |
| Retail live | `live` | `12.1.0.69814` | [`4e3cbb8c`](https://github.com/Gethe/wow-ui-source/tree/4e3cbb8c5609e4bfc332c0aebbfa4d79731fab59) |
| Retail PTR, currently vendored in QUI Alpha | `ptr2` | `12.1.5.69848` | [`f663342f`](https://github.com/Gethe/wow-ui-source/tree/f663342f08a6e06060b0d77628abf4e503907e67) |

The Forever snapshot contains 638 generated API Lua files and 4,401 files under `Interface/AddOns`. Compared with Alpha's 622 generated files: 541 are byte-identical, 80 changed, 17 are Forever-only, and one is PTR-only. These are file comparisons, not percentages of working addon compatibility. Retail live has 612 files; 500 match Forever after whitespace removal. Live/PTR differences must not be misreported as Forever-specific differences.

Forever's internal FrameXML flavor is **`camelot`**. Both [CooldownViewer](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_CooldownViewer/Blizzard_CooldownViewer.toc#L2) and [DamageMeter](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_DamageMeter/Blizzard_DamageMeter.toc#L2) explicitly declare `## AllowLoadGameType: standard, camelot`. Their generated API documents, plus duration utilities and secret predicates, are byte-identical to Alpha's corresponding documents. CDM has 22 of 27 implementation files identical to Alpha. DamageMeter has nine unchanged files, three changed files, and one added Camelot override.

This supports reusing QUI's modern systems. It does **not** justify treating Forever as an old Classic API client or promising full compatibility from a TOC change.

The generated [Unit documentation](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_APIDocumentationGenerated/UnitDocumentation.lua#L1506) gives `UnitHealthPercent` the flags `SecretReturns = true` and `SecretWhenCurveSecret = true`, with an optional curve argument. The [action cooldown entry](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_APIDocumentationGenerated/ActionBarFrameDocumentation.lua#L181) describes `GetActionCooldownDuration`: “Returns a duration object describing the active cooldown duration for an action.” Preserve QUI's secret-safe rendering and duration-object paths.

Source inspection establishes contracts and intended loading. It does not prove runtime API accessibility, combat behavior, gameplay availability, or a working QUI session.

## 2. Concrete compatibility risks

The following records the pre-implementation findings at the inspected Alpha commit. Numeric line references identify that baseline; implemented fixes are summarized above. Remaining acceptance requires live testing.

| Area | Evidence | Required approach |
|---|---|---|
| Version-number assumptions | `QUI_ActionBars/actionbars/actionbars.lua:23` uses interface `>=120000`; `actionbars_cooldowns.lua:61` requires that flag for duration objects. UnitFrames `unitframes.lua:146,159` and ResourceBars `resourcebars.lua:733` similarly gate modern percentage paths. | Verify actual Forever `GetBuildInfo()` output. Replace false version assumptions with checks for the specific documented contract. Do not classify capabilities by comparing product version numbers. |
| Bundled libraries | `libs/LibOpenRaid/LibOpenRaid.lua:38–50` enables older event/communications policy for interface `<=119999`; root TOC loads the Midnight data file. | Audit library initialization and datasets on Forever. Use verified upstream support where available; keep unsupported integration disabled until its behavior is checked. |
| Bank and frame structure | Camelot bank uses `C_Bank.ShouldUsePlayerBagsInBank()` and bag-slot paging; native unit frames route to Camelot templates and exclude multiple Retail class-power frames. | Adapt bank topology and loaded native frame structure at their existing ownership boundaries. Presence of `C_Bank` or a source file is insufficient. |
| Class/spec/profile data | Camelot talent visuals contain IDs `1482`, `1484`–`1491`; PlayerSpells disables the combined tab system. | Audit hardcoded spec mappings, spell defaults, talent loadouts, CDM catalogs, resources, and profile imports separately from reusable styling. |
| Startup, options, release | Core TOC includes many gameplay modules directly; seven suite addons load at login. Options directly includes their settings. Release assumes one numeric root interface and copies only the unsuffixed root TOC. | Apply one support policy to package/load lists, initialization, options, defaults, and publishing. Loader-only gating cannot cover independently loaded addons or file-scope initialization. |

Bank evidence: [Camelot BankFrame](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_UIPanels_Game/Camelot/BankFrame.lua#L86). Frame routing: [UnitFrame TOC](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_UnitFrame/Blizzard_UnitFrame.toc). Talent data: [ClassTalentUtil](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_PlayerSpells/Camelot/ClassTalents/Blizzard_ClassTalentUtil.lua#L13). Panel structure: [PlayerSpellsFrame](https://github.com/Gethe/wow-ui-source/blob/4d5d706b8e01c5ebe01c8dd9b7a07151d8d37069/Interface/AddOns/Blizzard_PlayerSpells/Camelot/Blizzard_PlayerSpellsFrame.lua#L58).

There are also smaller contract changes: action-slot search accepts an `ActionBarSet` with default `All`; gamepad support adds action-bar distinctions; several internationalization secret-argument policies differ from PTR. Audit actual QUI callers before deciding whether a changed declaration needs code changes. New defaulted arguments alone do not establish a break.

## 3. Minimum sustainable architecture

Keep core rendering, theme, layout, shared settings components, and each `QUI_*` suite shared. The small `core/client.lua` file loads before bundled libraries and records identity/build metadata. Specific capability checks remain at their existing consumers; unsupported subfeatures use narrow guards. Extend existing ownership boundaries when another proven difference appears instead of building a new plugin framework.

Distinguish **API capability**, **loaded UI structure**, and **gameplay availability**. A documented namespace can exist while a feature is unavailable in this game mode. Check load-on-demand objects after their owning Blizzard addon loads; a missing frame during early startup is not a permanent capability result. For example, CDM/meter are supported by explicit Camelot TOC evidence; Retail dungeon/prey/weekly systems need separate gameplay evidence before being exposed.

The initial implementation recognizes the verified `1.60.x` build-string family; Drew confirmed `forever 1.60.1` in the live client. The inspected ProjectConstants defines MAINLINE and CLASSIC, without a Forever-specific constant; Mainline BNet code supplies a MAINLINE fallback. No explicit `IsCamelot` helper was found. Do not invent `WOW_PROJECT_FOREVER`, assume CLASSIC, or assume MAINLINE proves Retail. The current package declares both numeric interfaces and does not depend on Blizzard's internal flavor-TOC routing. Broader Forever version-family matching needs evidence when its version changes.

Use targeted client data or adapters only for proven differences: bank slots, spec/spell configuration, native-frame skins. Avoid global fake Blizzard APIs and catch-all `pcall` wrappers. Retain secret/taint contracts even where out-of-combat values look ordinary.

Keep profile presentation settings reusable, with client-appropriate starter defaults. Independently installed clients already have separate SavedVariables locations; no database rewrite is needed merely to support two clients. New exports carry `_quiClient`; a tagged cross-client import is rejected. Existing untagged Retail imports remain compatible. A future presentation-only cross-client import needs explicit filtering of incompatible spell/spec/layout sections; the current change does not implement that conversion.

The authorized Alpha implementation uses one archive declaring both interfaces, with the same suite set and narrow runtime guards. `tools/toc_game_versions.py` parses the comma-separated TOC interfaces, validates suite consistency and emits game-version names for the publisher. Actual platform upload and both-client installation remain release acceptance checks. Separate archives remain an option only if live evidence requires different load lists.

## 4. Separate corpus and validation inputs

Preserve today's Retail paths and add one sibling corpus inside the existing tests submodule:

```text
tests/api-docs/                         existing selected Retail docs + index
tests/framexml/                         existing selected Retail FrameXML
tests/clients/forever/api-docs/          Forever docs + independent index
tests/clients/forever/framexml/          Forever FrameXML + version/provenance
```

Pin branch, SHA, build, extraction date, and comparison baseline. Populate both Forever mirrors from the same checkout. Never merge Forever files into the Retail corpus. Retail live and PTR remain separate selected baselines; report which was tested.

The tools now accept explicit input/output paths. Remaining analysis work stays separate from taint metadata:

1. Use `tools/test_taint.lua --update-index --corpus <docs> --index <output>` and `tools/generate_lua_definitions.lua --docs <docs> --out <directory> --globals none`; Retail defaults remain unchanged. Extraction now handles symbolic/computed documentation constants and fails on execution errors. These placeholders are not authoritative numeric gameplay constants. Exact regeneration commands are in `tests/clients/forever/README.md`.
2. Compare full generated tables for functions, arguments, results, events, enums, predicates, and structures. The existing taint index only emits flagged functions, so it cannot serve as an API-existence inventory. Cross-reference changes with actual QUI call sites; handle renamed/moved table declarations before declaring removals.
3. Select exactly one client's generated LuaLS library per workspace/check. `.luarc.json` currently includes all of `meta`; putting both client definitions underneath it would create a misleading union. Retail `.luacheckrc` fallback globals also must not make unavailable Forever APIs appear valid.
4. Resolve FrameXML by its actual TOC/XML load rules, including Camelot overrides. `tools/framexml_xml_graph.py` accepts another corpus root but currently prefers Retail paths. Keep client graphs separate and exclude raw duplicate corpora from general QUI code scans/compile checks.
5. Preserve current Retail gates; add selected-corpus regeneration checks and focused Forever boot/module tests. Include library initialization, absent optional APIs, real loaded-frame contracts, and post-load capability refresh. Do not make a universal stub environment that supplies every Retail global.

Headless checks need live verification: fresh login, `/qui`, profile creation/import, reload, edit mode, combat entry/exit, party/raid/PvP restrictions, and the specific module's behavior. Group these into per-feature smoke runs rather than declaring the entire product supported from one successful login.

## 5. Implementation sequence and acceptance criteria

The table retains the original rollout milestones and estimates for planning. Initial Alpha implementation covers the corpus/tooling foundation and targeted code/package changes across these phases; it does not satisfy the live acceptance criteria. Re-estimate remaining work after the first live boot.

| Phase | Deliverable | Acceptance | Initial estimate |
|---|---|---|---|
| 1 — Evidence | Pinned Forever corpus, isolated derived data, QUI-relevant delta report | No changes to Retail corpus; all source files accounted for; deterministic regeneration; identity/build probe recorded | 1–2 days |
| 2 — Boot | Client policy, correct library/version paths, minimal core/options/theme/chat package | Fresh Forever login, `/qui`, profile creation and reload; unsupported runtime/settings files remain inactive; Retail gates pass | 2–4 days |
| 3 — Shared systems | Native damage meter first; action bars/unit/group/nameplate frames; then CDM/resources | Each feature passes its own combat, reload, layout and class-data checks on both target clients; no replacement CDM/meter engine | 5–10 days, then re-estimate |
| 4 — Differences | Bank/bag topology, talent/spec data, native skins, client defaults and import handling | Verified behavior on the actual selected Blizzard frames; no silently misapplied spec/spell/profile data | Estimate after phase 2 inventory |
| 5 — Release | Dual-client Alpha archive plus corpus/client checks | Correct TOCs and bundled suites; verified game-version metadata on distribution platform; archive smoke-tested on both clients | 1–2 days after client gates pass |

First milestone: **a Forever beta package that reliably boots, opens settings, preserves profiles, and shows a working native-backed damage meter, while Retail regression gates remain green.** Full feature parity is a later acceptance target, not a prerequisite for a useful beta.

## Research receipt

Fetched pinned Forever and Retail live upstream checkouts; compared their generated docs with QUI Alpha's vendored PTR docs; inspected actual TOC routing, key API contracts and affected QUI callers. Three independent read-only reviews covered QUI architecture, corpus/tooling, and Forever FrameXML. Graphify was used for navigation and findings were checked against source.

Temporary research inputs: `/tmp/qui-forever-research-20260917`, `/tmp/qui-retail-live-research-20260917`; exploratory full-table comparisons: `/tmp/qui-forever-api-delta.tsv`, `/tmp/qui-forever-vs-live-api-delta.tsv`. These are disposable research artifacts, not the permanent corpus. Symbol comparison used symbolic enum/constant expressions; file metrics above came directly from source files.

After research, Drew authorized implementation and Alpha TOC support. The implementation and validation receipt is recorded above. Changes remain uncommitted across the root repository and its tests/docs submodules; next acceptance step is live Forever boot and module verification.
