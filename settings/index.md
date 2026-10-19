---
layout: default
title: Settings Reference
nav_order: 4
has_children: true
---

# Settings Guide

This section mirrors the current in-game `/qui` options panel and is best used once you already know which parts of QUI you want to tune more deeply.

If you are still setting up, start with [Getting Started](../getting-started/) or the [Features](../features/) section first. Come back here when you want the detailed reference view.

![Actual QUI settings window]({{ '/assets/images/qui-group-frames-full.png' | relative_url }})
_The current `/qui` window uses a left-hand feature sidebar, breadcrumbs across the top, and page-specific tabs inside each tile._

![Actual QUI Appearance page]({{ '/assets/images/qui-appearance-ui-scale.png' | relative_url }})
_The Appearance tile is where theme, panel scale, fonts, skinning, and other shared presentation controls live._

## Section Links

Pages with three or more available sections show direct links in the left
navigation. Links follow the selected unit, reminder, or data provider and jump
to that section's heading. Smaller pages remain simple destinations. Group
Frames and Spell Reminders use the same navigation.

## Most-Visited Tiles

- **General** for profiles, import/export, integrations, and click-cast bindings
- **General → Feature Toggles** for enabling or disabling whole QUI feature addons
- **Unit Frames** and **Group Frames** for combat frame setup
- **Action Bars** and **Cooldown Manager** for your main combat HUD
- **Minimap & Datatext** and **Info Bar** for utility widgets
- **Appearance** for UI scale, fonts, autohide, HUD visibility, and frame levels
- **Bags** and **Alts** for optional inventory and account-wide tracking
- **Quality of Life** for session helpers and automation

## Main Navigation Groups

The sidebar groups related features together:

| Group | Features |
|-------|----------|
| **Setup** | Welcome, General, Help |
| **Frames & Bars** | Unit Frames, Group Frames, Nameplates, Action Bars |
| **Abilities & Auras** | Cooldown Manager, Resource Bars, Auras |
| **Interface** | Appearance, Minimap & Datatext, Info Bar, Chat & Tooltips, Bags, Alts |
| **Gameplay & Utilities** | Gameplay, Reminders, Quality of Life |

Find **Damage Meter** under **Gameplay**. Enable optional addon modules under
**General → Feature Toggles**. The [Module Addons guide](../getting-started/module-addons)
explains which modules are opt-in.

## General Tile Pages

The **General** tile is where the cross-feature setup pages now live:

| Page | Use it for |
|------|------------|
| **Profiles** | Creating, copying, deleting, and auto-switching profiles |
| **Pinned Globals** | Quick access to pinned settings |
| **Feature Toggles** | Enabling and disabling feature addons |
| **Import / Export** | Bundled presets and shareable setup strings |
| **Third-party** | Integration and anchoring setup for compatible tools |
| **Click-Cast** | Mouse-binding setup for unit and group frame interactions |
| **Options Window** | Options panel and reload behavior |

## Common Page Tabs

Many tiles then split again across a page-level tab strip. The most common examples are:

| Tile | Typical page tabs |
|------|-------------------|
| **Action Bars** | General, Buff/Debuff, Per-Bar |
| **Minimap & Datatext** | Minimap, Datatext |
| **Appearance** | UI Scale, Fonts, Skinning, Autohide, HUD Visibility, Frame Levels, Blizzard Mover |
| **Quality of Life** | FPS Preset, Combat Text, Automation, Popups, Salvage, Consumables, Macros, Distance, Panel, Reload |

## How To Use This Section

- Use it when you want the detailed toggle-by-toggle reference.
- Use the [Features](../features/) pages when you want plain-language guidance first.
- Use `/qui layout` when you need to drag or place frames on screen; use `/qui` when you want feature settings, toggles, styling, and behavior.
