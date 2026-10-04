# Spell reminders

Agreed scope: a shared editor under Reminders > Spell Reminders, with Power
Infusion and Innervate presets and reminders for other player spells. Include
BeKindRemind's timing, icon styling, animation, text-to-speech, encounter-start
and load filters. Exclude raid-marker requests. Estimated early countdowns are
an explicit per-spell option, disabled by default.

Power Infusion adds independent raid, dungeon and focus tracking, selectable
offensive buffs and custom buff IDs, player allowlists, group-frame highlights,
recipient alerts, focus reminders, and whisper priority/rotation lists.

## Settings

The dedicated Reminders menu has Defensive Reminders and Spell Reminders tabs.
Both runtimes live in QUI_Reminders and share its addon module switch, while
each system keeps its own enable setting and saved profile keys. Settings load
through QUI_Options; opening the spell page with QUI_Reminders disabled shows
instructions for enabling the module. Initialization runs after all spell
tracking files have loaded, including when the module loads after login.

The page owns a reminder selector and an editor with Timing, Appearance,
Sounds, Load conditions, and PI-only Tracking and Requests tabs. New reminders
are explicitly added; existing QUI profiles remain quiet until enabled.
Positions are per reminder, shared by its own cooldown and recipient alerts,
with preview dragging and Layout Mode support. Configuration travels with QUI
profiles and the Timers / Widgets export category. Relative frame anchors use
the existing Layout export category.

## Implementation

- Separate configuration and timing decisions from frames and events.
- Use current WoW cooldown APIs. Never treat an elapsed estimate as proof that
  a spell is ready. Forward restricted durations only to supported UI methods.
- Let Blizzard's AuraContainer select buffs and control aura-slot visibility.
  Aura-driven artwork must have no addon scripts in its subtree.
- Register raid, party and focus aura sounds through the native aura-sound API,
  with independent switches. Remove them when PI is cast or unavailable, and
  require confirmed PI readiness before registering them again. Combat and
  encounter restrictions can delay re-registration; explain this next to their
  setting. Retry sound setup between pulls, separately from the stricter
  aura-artwork setup. Native aura audio accepts recorded files, so custom TTS
  phrases apply to player cooldown reminders.
- Ignore whisper payloads. Any qualifying whisper selects from the configured
  list; it does not identify the sender. Clear requests after casting, combat,
  roster or profile changes. Advance rotation only on the player's PI cast.
- Keep frame discovery separate so QUI, Blizzard and third-party group frames
  can be supported without changing tracking policy.

Use the supplied addons as behavior references and implement with QUI's own
components. Validate timing, secret-value boundaries, recipient selection,
roster changes, options navigation, exports, Lua 5.1 compilation and lint.
Actual protected UI behavior and third-party frames also need in-game QA.
