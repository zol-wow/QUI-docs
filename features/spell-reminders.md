---
layout: default
title: Spell Reminders
parent: Features
nav_order: 25
---

# Spell reminders

Spell Reminders displays cooldown prompts for your spells. Power Infusion also
highlights allies using offensive buffs and supports whisper requests with a
priority list or rotation. The reminder controls cover BeKindRemind's timing,
appearance, speech, encounter triggers and load filters. Raid-marker requests
are excluded.

## Set up a reminder

1. Open `/qui` and choose **Reminders → Spell Reminders**. The other tab,
   **Defensive Reminders**, contains boss ability callouts. The Reminders module
   switch controls whether either system loads.
2. Turn on **Enable Spell Reminders**.
3. Add the **Power Infusion Preset**, **Innervate Preset**, or enter a spell ID
   and click **Add Spell**.
4. Choose when to show it on the **Timing** tab. A ready duration of zero keeps
   the ready icon visible until the spell is cast.
5. Use **Preview / Drag** or Layout Mode to place the reminder. **Appearance**
   controls its icon, label, font, glow and animation.

**Sounds** provides sound effects, ready and early speech, and spoken countdowns.
**Load Conditions** limits a reminder to known spells, a class, specializations,
combat or content types. Empty specialization and content selections allow all.
An encounter-start reminder displays for the configured ready duration, or ten
seconds when that duration is zero. It announces readiness only when the spell
is reported ready.

## Power Infusion

The PI preset adds three tabs:

| Tab | Controls |
| --- | --- |
| PI Tracking | Raid, dungeon and focus tracking; group-frame highlights; recipient icons; buff durations; focus reminders; separate raid, party and focus sound switches |
| Tracked Buffs | Offensive buff selection, custom buff IDs, and optional separate lists for each context |
| Requests | Whisper requests, priority and rotation lists, frame highlights, icons and sounds |

PI tracking defaults to Holy and Discipline priests. A friendly group focus
takes priority over other group members. Without a group focus, tracking uses
the raid or dungeon list and skips tanks and healers unless explicitly listed.
The dungeon list also covers parties outside instances.
Your character is excluded from buff tracking. A friendly focus outside the
group can have its own alert without suppressing group tracking.

The PI preset starts with group-frame highlights and focus alerts enabled.
Raid and dungeon recipient icons, sounds and whisper requests are optional.
Highlight styles include pixel, proc, border, fill and a countdown bar.
Recipient icons use fixed positions during combat, so inactive recipients can
leave gaps. Their size and font follow the reminder's Appearance settings.

Frame discovery covers QUI, Blizzard, ElvUI, Grid2, Danders, Ellesmere, Buzzard,
VuhDo and Mich raid frames. Changes to protected displays wait until WoW allows
them, which can mean the end of a Mythic+ dungeon.

## Whisper lists

WoW can hide whisper senders and message text. Any qualifying whisper therefore
selects a recipient from your configured list. It does not select the sender.
Use `Name-Realm` to distinguish players with the same name.

Priority mode picks the first listed player currently in your group. Rotation
mode picks the next available entry and advances on your PI cast. You can drag
names into order, repeat the rotation, or reset it manually. Requests work only
in a group, in combat, while PI is ready or inside the configured early window.
Whispers during cooldown are discarded. Casting PI, leaving combat, or changing
the roster clears the current request.

## Cooldown timing and sounds

WoW can show an exact cooldown while hiding its numeric timing from addons.
The icon can still use the native display, but early sounds and spoken
countdowns need readable timing. **Allow Estimated Early Alerts** is off by
default for every spell. If enabled, it uses your last cast and the configured
cooldown when exact timing is hidden. Cooldown reductions can make it inaccurate.
An expired estimate never marks a spell ready.

For sounds when an ally activates a tracked cooldown, choose **Alert Sound**
on **PI Tracking** and enable **Sound on Party Cooldowns**, **Sound on Raid
Cooldowns**, or **Sound on Focus Cooldowns**. Selecting a sound alone does not
enable a trigger. **Test Alert Sound** previews the selected file and channel.
Party and raid sound recipients follow the tracking lists and focus priority.
Tracked-buff sounds stop as soon as PI is cast or reported unavailable. They
require confirmed PI readiness, even with an early window or always-on visual
tracking. An expired cooldown estimate cannot enable them.

WoW allows removing native aura sounds during combat but blocks registering
them again until combat and encounter restrictions lift. If PI becomes ready
mid-fight, these sounds remain silent until those restrictions lift. They can
resume between Mythic+ pulls while buff details remain hidden. Sound and
recipient changes follow the same restrictions. The combat-only filter does
not affect native tracked-buff sounds.

For a spoken PI-ready reminder, open **Sounds**, enable **Speak When Ready**,
enter **Ready Announcement**, and select **Voice**. **Test Voice** previews the
phrase with that voice. Early announcements have a separate phrase field.
WoW's native tracked-buff audio accepts sound files but does not expose a TTS
trigger. To hear speech when an ally gains a tracked buff, use a recorded sound
registered through SharedMedia.

Reminders and their anchors travel with QUI profiles. Select **Timers / Widgets**
for the reminder settings, and **Layout** to include relative frame anchors.

Both systems run in the `QUI_Reminders` addon. Disabling that module stops both
after a reload and keeps their saved settings. Each tab retains its own enable
switch, so you can use spell reminders without enabling defensive callouts.
