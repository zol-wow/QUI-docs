# Action-bar rank upgrades implementation plan

**Goal:** Add the approved optional Forever action-bar upgrade behavior, on by default as requested.

**Design:** While enabled, remember active spellbook ranks and replace only action slots containing the previous highest known rank when a new highest rank is learned. Keep deliberate lower ranks and macros. Establish a baseline without modifying bars on login, enable, or profile change. Defer changes during combat or an occupied cursor; revalidate pending slots and spell availability before applying them.

**Implementation:** A local module, `actionbars_uprank.lua`, owns the spellbook snapshot, pending actions and event frame. It exposes `ns.ActionBarsSpellRanks.Refresh()` for settings/profile updates and works with either action-bar engine. Existing defaults and the Forever General settings page own the boolean setting. Native spellbook rank checks determine rank relationships; ambiguous names fail closed.

**Constraints:** No commits, pushes or new worktree. Preserve the existing bag and Composer changes. No new dependencies or saved rank snapshots. No mutation of macros or automatic migration of existing low-rank slots.

1. [x] Add runtime regression tests, observe failure, implement rank snapshots and deferred updates. Check old-highest versus intentional lower ranks, repeated learns, reordered events, slot edits, profile/setting changes, ambiguous names and failed pickup.
2. [x] Add the default-on Forever setting, refresh hook and TOC entry with focused integration coverage. Regenerate affected locale/search caches and default fixtures; document the setting.
3. [x] Review the final implementation independently, run `tools/test.sh`, attempt Graphify update without forcing a shrink, and record the handoff.

**Added report:** Reminders restored Encounter Journal tier zero. Validate saved tiers against the current native range before restoring; regress invalid tiers, loading retries, valid selection restoration and real enumeration failures.

**Review focus:** Cursor ownership; out-of-combat action writes; stale queued slot identity; rank snapshots after spec changes; same-name unrelated spells. Live WoW behavior remains a separate verification step.

**Verification:** All nine gates passed, including 1,375 unit files and 12 profile fixtures. Independent review found no blockers, including the startup baseline correction. Graphify refused to overwrite the existing graph because of its shrink safeguard. Receipt: `/tmp/qui-action-ranks-journal-final-gates.log`; graph log: `/tmp/qui-action-ranks-graph-final.log`.
