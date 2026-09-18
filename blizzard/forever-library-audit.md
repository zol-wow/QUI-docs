# Forever library audit

Audited 2026-09-18 from `/big-data/Github/QUI_Alpha`. Upstream source was fetched
directly; revisions below identify the inspected snapshots. No library update
found in this audit supplies a dedicated Forever defensive-spell dataset.
Existing local compatibility fixes remain intact.

## Every vendored library

Versions are LibStub minor revisions unless otherwise stated. Matching code
with expanded SVN keywords is treated as current, not as a pending upgrade.

| Library | Installed | Upstream inspected | Result |
|---|---:|---|---|
| AceAddon-3.0 | 13 | [Ace3 `1e98fc0`](https://github.com/WoWUIDev/Ace3/tree/1e98fc00874779334d7a3f0cb399c7ae9a15fead) | Current; only release keyword differs. |
| AceComm-3.0 | 14 | Same Ace3 snapshot | Current; only release keyword differs. |
| AceConsole-3.0 | 7 | Same Ace3 snapshot | Current; only release keyword differs. |
| AceDB-3.0 | 36 | Same Ace3 snapshot | Byte-identical, including upstream's September 18 Forever compatibility fix. |
| AceEvent-3.0 | 4 | Same Ace3 snapshot | Current; only release keyword differs. |
| AceSerializer-3.0 | 5 | Same Ace3 snapshot | Current; only release keyword differs. |
| CallbackHandler-1.0 | 8 | Same Ace3 snapshot | Current; only release keyword differs. |
| ChatThrottleLib | 32 | Same Ace3 snapshot | Byte-identical; secret-message protections already present. |
| LibStub | 2 | [Authoritative WoWAce source](https://repos.wowace.com/wow/libstub/trunk/LibStub.lua) | Current; only release keyword differs. Ace3's embedded copy has cosmetic differences and uses `string.match` instead of the equivalent WoW global `strmatch`. |
| LibCustomGlow-1.0 | 27, locally patched from 25 | [Upstream `4f8f5c2`](https://github.com/Stanzilla/LibCustomGlow/tree/4f8f5c2607d7384b26df9175bb99fa3df891b015) | Current upstream behavior plus QUI explicit-size and restricted-layout frame-pool fixes; preserve patches. |
| LibDataBroker-1.1 | 4 | [Upstream `1a63ede`](https://github.com/tekkub/libdatabroker-1-1/tree/1a63ede0248c11aa1ee415187c1f9c9489ce3e02) | Byte-identical. |
| LibDeflate | 1.0.2-release / 3 | [Upstream `afc3b78`](https://github.com/SafeteeWoW/LibDeflate/tree/afc3b78d12fb3bcfa6b21e5332031ad3d7572e19) | Current algorithm; local differences are formatting, comments/license placement and seven optional semicolons. Non-comment token comparison found no other difference. |
| LibDualSpec-1.0 | 33, locally patched from 32 | [Upstream `86985fe`](https://github.com/AdiAddons/LibDualSpec-1.0/tree/86985fe0d5a235b600c896194ad0bb1265937878) | Current plus QUI namespaced specialization and profile-name validation fixes. Upstream's unpackaged test block is absent as expected. |
| LibKeyBound-1.0 | 100004 | [Authoritative WoWAce source](https://repos.wowace.com/wow/libkeybound-1-0/trunk/LibKeyBound-1.0/LibKeyBound-1.0.lua) | Current plus two QUI `_G` lookups replacing removed `getglobal`. All nine locale files match apart from required packaged SVN revision substitutions. |
| LibOpenRaid-1.0 | 177 | [Upstream `8a6e6bd`](https://github.com/Tercioo/Open-Raid-Library/tree/8a6e6bdb2b6df4e628f24ff54b76d6d00239ea04) | Current. All dataset files are byte-identical. Preserve QUI Forever initialization guard and secret-value/aura-access protections in `LibOpenRaid.lua` and `GetPlayerInformation.lua`. |
| LibRangeCheck-3.0 | 36 | [Upstream `66370e7`](https://github.com/WeakAuras/LibRangeCheck-3.0/tree/66370e7a229395360bd910356be366557e05907f) | Current plus QUI secret-capability and pet-identity guards. Namespaced inventory API support already present. |
| LibSharedMedia-3.0 | 12000001 | [Authoritative WoWAce source, 12000002](https://repos.wowace.com/wow/libsharedmedia-3-0/trunk/LibSharedMedia-3.0/LibSharedMedia-3.0.lua) | Update available: rejects unknown file assets using `C_UIFileAsset.IsKnownFile`. Unrelated to defensive discovery; deferred because it changes media-registration behavior and requires a separate asset/registration check. |

`LibDFramework LICENSE.txt` and `LibSerialize LICENSE.txt` are license-only
artifacts; there is no vendored implementation or TOC load entry for either.
They are not installed runtime libraries to upgrade.

WoWAce raw sources do not expand SVN keywords. Downloaded SHA-256 receipts:

| Source | SHA-256 |
|---|---|
| LibStub.lua | `7ba7300471327c0de1b3e42a4edfd62cbad79bd30100d6377736d2c1080e9b96` |
| LibKeyBound-1.0.lua | `20df4aa74ae73ecb4e3cd4b8dcb483706b742494ead39cf4b6b167993fe1c7d1` |
| LibSharedMedia-3.0.lua | `ea359e44eae4355c51a49a69960c878889ee26adac9d72d1362c22a3db6af6d0` |

## Defensive candidate discovery

Forever's candidate picker now uses a narrow derivative of the already-vendored
LibOpenRaid Midnight dataset: the 73 spell-ID/class pairs classified by upstream
as personal defensives (`type = 2`). The derivative lives in
`QUI_Reminders/reminders/defensive_spell_classes.lua`; its source is
[`ThingsToMantain_Midnight.lua` at `8a6e6bd`](https://github.com/Tercioo/Open-Raid-Library/blob/8a6e6bdb2b6df4e628f24ff54b76d6d00239ea04/ThingsToMantain_Midnight.lua),
under the existing vendored `libs/LibOpenRaid/LICENSE`.

Candidates must belong to the player's class and pass the client's actual
spell-knowledge check. Retail specialization IDs, cooldown durations, talent
requirements and library communication/runtime initialization are not imported.
The candidate picker does not automatically add spells to the player's saved
priority list. Manual spell-ID entries remain available. A regression checks
every derived row against the existing source dataset to prevent silent drift.

The native contract is `C_SpellBook.IsSpellKnown`, documented in the pinned
Forever `SpellBookDocumentation.lua:738`: “Returns true if a player knows a
spell.” Its default bank is Player, and it also admits temporarily granted
abilities. Existing name/icon resolution uses the same client's spell APIs.

This is a source-grounded suggestion catalog, **not a complete verified Forever
gameplay dataset**. Known IDs retain upstream's classification; spell knowledge
alone cannot prove an ability's effect was not changed on Forever. Abilities
with new IDs, different ranks, or changed purpose require live confirmation and
can be supplied manually. The upstream Era, Burning Crusade, Wrath and Cataclysm
cooldown tables are empty; merely selecting those filenames cannot supply the
missing catalog. Upstream Pandaria also contains later-expansion spell IDs and
is not evidence of a Forever-specific mapping.

Pinned native alternatives were inspected: CooldownViewer metadata exposes
known/self-aura flags but no personal-defensive classifier; `IsExternalDefensive`
classifies external auras, and commentator tracked spells require commentator
player/cooldown data that may be absent. None establishes a complete general
player catalog.

## Validation

`lua tests/unit/forever_reminders_candidates_test.lua` failed against the old
discovery logic and passes with the change. It covers different Forever spec
IDs, actual-known filtering, class filtering, learning/unlearning, isolation
from another addon's global dataset, manual entries, source derivation, and
preserved Retail routing. Existing defensive secret-value and Forever library
initialization regressions pass. Focused Lua lint reports no warnings.

Live acceptance: open Reminders' defensive picker on Forever, confirm displayed
abilities and their effects, add one to the optional priority list, then test
its ready/unready state and callout. No in-client verification is claimed here.
