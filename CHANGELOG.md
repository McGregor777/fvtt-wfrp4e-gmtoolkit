# Changelog
All notable changes to this project will be documented in this file.  The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## Unreleased
See [Issue Backlog](../../issues) and [Roadmap](../../milestones). 

## Version 0.6.3

- *Changed* Foundry compatibility to up to 0.7.10. WFRP4e system compatibility is up to 3.6.2.  
  - This is the final release of the GM Toolkit to support FVTT 0.7.x and WFRP4e 3.x.
- *Changed* manifest to point to latest release note for installation file and download link. 
  - Installation link will now consistently reference "https://github.com/Jagusti/fvtt-wfrp4e-gmtoolkit/releases/latest/download/module.json" rather than the raw repository file. 
  - Download link points to a version specific archive file. 
- *Added* links to release notes and bugs, as well as expanded [manifest+](https://foundryvtt.wiki/en/development/manifest-plus) fields to manifest
- *Removed* `wfrp4e` as an explicit dependency in manifest file (as this is sufficiently handled through the system declaration).
- *Added* dramatic test outcome hints (such as "Yes, and ..." or "No, but ...") to roll results descriptions in the chat log, depending on success levels. More information can be found on p152 of the core rulebook. 
- *Added* links to [ko-fi](https://ko-fi.com/jagusti) for those who may wish to support work on the Toolkit. The module is freeware, and there's no expectation or obligation to make a contribution, but any is welcome. 

## Version 0.6.2

General Module Stuff
- *Added* compatibility updates for WFRP4e version 3 and premium content,
  -  Replaced obsolete references to `WFRP_Utility` and `WFRP_Tables` with `game.wfrp4e.utility` and `game.wfrp4e.tables` respectively.
  -  Updated skill and characteristic test calls to use the new basicTest functionality.
  -  If premium core content module is not installed, the Token Hud Extension shortcuts for rolling on the Physical/Mental Mutation and Wrath of Gods tables will silently fail (avoiding a 'Table not found' error). 
- *Changed* minimum core Foundry compatibility to 0.7.9. Minimum WFRP4e system compatibility is 3.4.1.  

Macros
- *Changed* Set Token Vision and Light macro to use Normal Vision range if Night Vision is selected but the token does not have it. In fact, it sets the Dim Light range to the higher of the default Normal Vision range and the calculated Dim Vision range, which would be 0 if the token doesn't have Night Vision.
- *Fixed* a bug that could prevent advantage macros from updating or capping correctly. 
- *Changed* the 'Simply d100' macro to explicitly state the number of dice rolled. This was temporarily breaking on an earlier version of FVTT. While the current version does not break, this change is applied for full compatibility. 
- *Added* new module setting to export the chat log as part of the End of Session Routine. 
- *Fixed* a macro compendium error, restoring the Set Token Light and Vision macro. 
- *Fixed* translation strings for Add XP and Reset Fortune that would trigger console warnings. 

Token Hud Extension 
-  *Added* translation string for Little Prayer result, which can be rolled from Token Hud extensions.

Dark Whispers
- *Added* macro to Send Dark Whispers. GMs can target one or more player characters who have at least 1 Corruption with an offer from the Dark Gods. This supports the game feature described on page 183 of the WFRP 4e rulebook - basically to let something dodgy happen to reduce their Corruption by 1. Players can accept or reject the offer from the private chat message they are sent. Corruption is not automatically removed if the player accepts as:
  - there may be a significant delay in the narrative before the player is able to meet the conditions. 
  - the GM rather than the system should make the decision about whether the character has met the terms of the offer.
- *Added* a new system table with suggestions for Dark Whispers. This is available through a chat command (`/table darkwhispers`) but is also used by the Send Dark Whispers macro to prepopulate the dialog box and to give the GM a starting point for inspiration. 

## Version 0.6

General Module Stuff
- *Changed* minimum core Foundry compatibility to 0.7.5 and minimum WFRP4e system compatibility to 2.2.1 to support animated token light effects. 
- *Added* French translations for enhancements and changes to Version 0.5.1 (thanks to @LeRatierBretonnien).
- *Added* explicit dependency on WFRP4e system, as supported by Foundry 0.6.6.

Macros
- *Removed* dependency on external Furnace module. Macros should be re-imported from the macro compendium to take advantage. Thanks to Forien for support with this. 
- *Added* new custom icons for the Toolkit macros.
- *Added* `End of Session` macro which automatically runs end of session admin macros (`Add XP` and `Reset Fortune`), as well as ensuring the game is paused. 
- *Changed* macro compendium to include latest versions of macros. **Updated macros will need to be manually re-imported from the compendium.** 
- *Changed* macro code to improve notification and string handling. 

Token Hud Extension
- *Added* option to toggle token hud extensions. Hud extensions are enabled by default. This update also makes the token hud extension available to non-GMs, and each user can enable or disable it independently. 
- *Added* dynamic update to token hud when Advantage is increased, reduced or cleared. Any changes are visible immediately in the token hud resource bar if the token hud is active. This applies when using the relevant advantage macros as well as when starting or ending combat, depending on the Clear Advantage setting. 
- *Added* dynamic update to Token Hud Extension when using shortcuts to increment or decrement Resolve, Resilience, Fortune, Fate, Sin or Corruption. Any changes are visible immediately in the token hud resource bar if the token hud is active. 
- *Changed* Token Hud setting description to clarify that the hud extension is only shown on controlled tokens. GMs can generally see any token hud, but players will only see their own characters token hud. 
- *Added* option to always show Initiative in Token Hud Extension. Previously Initiative and Agility tooltips and shortcuts were only available in active scenes. This option is now enabled for all scenes by default. 
- *Added* a message to confirm when no changes are made when using the status change shortcuts to alter Fate, Fortune, Resolve or Resilience via the Token Hud Extension. This can occur when the status attribute is already at 0 or its maximum value.
- *Fixed* a console error that was thrown when chat messages were logged when status changes were made via the Token Hud Extension. 

Token Vision and Light
- *Added* module settings for the GM to:
  - define token vision distances for normal and Dark Vision in dim or night conditions. 
  - allow Night or Dark Vision even if token does not have the relevant talent or trait. 
- *Fixed* Night Vision to work with characters with the Trait, and not just characters with the Talent.
- *Changed* No Vision setting to also clear light emission from token.
- *Added* new light source options
  -  Soulfire (Magic Miscast).
  -  Matches (trappings).
- *Fixed* Storm Lantern lighting options. 
  - Broadbeam is treated as unshuttered and providing 360° illumination.
  - Shuttered eliminates light emission.
- *Added* colour and light animation effects to differentiate light sources. Preconfigured settings are documented on the [wiki](https://github.com/Jagusti/fvtt-wfrp4e-gmtoolkit/wiki/set-token-vision-and-light#light-sources). 
- *Changed* the bright radius of various light sources. Previously these were treated as half the dim radius. New values are documented on the [wiki](https://github.com/Jagusti/fvtt-wfrp4e-gmtoolkit/wiki/set-token-vision-and-light#light-sources). 
- *Changed* the application of Night Vision to require a minimum level of light in the scene. This is fulfilled by any of the following criteria:
  -  global darkness level of less than 1 (indicating some ambient light)
  -  the token itself having some kind of light source (conferring a dimLight setting > 0)
  -  global illumination being enabled on the scene. 

## Version 0.5.1
- *Fixed* typo in Add XP macro

## Version 0.5
- *Added* shortcut to make Track test (CTRL + SHIFT + Initiative hud extension).
- *Added* Strong-minded advances for determining maximum Resolve when increasing through Token Hud. 
- *Fixed* undeclared target error when adding Fortune through Token Hud.
- *Fixed* unlinked actor issue when adjusting advantage from selected token. 
- *Added* macro to toggle Token Vision and Global Illumination on the current viewed scene.
- *Added* user setting to optionally reset Advantage for all tokens (including non-combatants), at start and/or end of combat encounter.
- *Added* user setting to optionally activate scene after pulling everyone to it (always, never or prompt).
- *Added* user settings to configure default amount of XP to add, and optionally prompt for how many each time. Improved data input validation and handling.
- *Changed* startup checks to ensure that Furnace module is installed *and* has Advanced Macros enabled.
- *Added* multiple translation strings for various settings and prompts.
- *Added* French translations for enhancements and changes (thanks to @LeRatierBretonnien).
- *Changed* Foundry 0.6.2 compatibility.

## Version 0.4
- *Breaking changes* to token selection validation to make compatible with FVTT v0.6.0. All Advantage macros plus Set Token Vision and Light macro should be re-imported from the macro compendium. 
- *Added* interactions for Token Hud Extension: various skill and characteristic tests, status value adjustments and table rolls. Full details on https://github.com/Jagusti/fvtt-wfrp4e-gmtoolkit/wiki/token-hud-extensions. 
- *Added* Perception and Intuition to Token Hud.
- *Added* Swim value to Movement tip on Token Hud.
- *Fixed* alignment of first-child Token Hud icons. 

## Version 0.3.2
- *Added* Advanced macros in the Toolkit require Kakaroto's Furnace module. If this is not installed and active, a warning message is displayed. Console logs are included to confirm whether Furnace is installed and advanced macro support is enabled.

## Version 0.3.1
- *Fixed* Luck Talent translation in French translation file. Thanks to JDW for flagging. 

## Version 0.3

### Changed
- Extended and standardised localization strings.
- Refactored macros extensively to support translation and handling situations where no token is selected or targeted.
  - All macros are now fully localized.
  - Error and success notifications for macros are significantly improved.
- Rationalised console messages for macros.

### Added
- French translation support started. Thanks to @LeRatierBretonnien#2065!

## Version 0.2.1

### Changed
- Chat log for Add XP macro is reported from player rather than character.
- UI feedback for advantage macros improved to show change and new value, or no change if none made.

### Added
- Rather than silently failing or throwing a console error if a token hasn't been targeted or selected first, a UI notification is presented for all macros in the GM Toolkit as appropriate. 
- Added script files for Advantage macros. 

### Fixed
- Increase Advantage macro caps advantage at character max. Thanks to JDW#6422.
- Reduce Advantage macro no longer drops advantage below 0.
- Typo in Set Token and Light macro dropdown options.
- Macros relying on token selection no longer run when no token is selected. 

## Version 0.2

### Changed
- Added feature descriptions to changelog.
- Set macro icons and some descriptions.

### Fixed
- Typos in macro descriptions.
- Include macro pack and correct script pack for Token Hud Extensions (doh!)
- Fixed links to wiki and issue backlog.

## Version 0.1

### Added
- Token Hud Extension 
  - Add Movement and Initiative to Token Hud, including tooltips for modes and Initiative/Agility values. 
  - Add Fortune, Resolve, and Corruption to Token Hud, including tooltips for Fate, Resilience and Sin values.
- Macros (available from Compendium > Macro > GM Toolkit)
  - **Reset Fortune:**  reset Fortune for the *targeted* character to their Fate level, accounting for Luck talent advances.
  - **Set Token Vision and Light:** opens a dialog for quickly changing vision and lighting parameters of the *selected* token(s). Night Vision applies range enhancements. Blinded condition and Dark Vision trait are supported. Light sources range from candles through Storm Lantern, as well as Petty Magic, Witchlight, Glowing Skin and Ablaze condition. **Requires** The [Furnace]( https://github.com/kakaroto/fvtt-module-furnace/) module by KaKaRoTo#4756.
  - **Add XP:** adds 20XP (configurable in macro script) to *selected* tokens, confirming change and new levels in chat message. By DasSauerkraut#3215.
  - **Pull Everyone to Scene:** yanks every player into the scene that the GM is on. Does not activate the scene. 
  - **Add/Reduce/Clear Advantage:** three separate macros to add or remove 1 Advantage from the *selected* actor, or to reset their advantage.
  - **Simply d100:** sometimes you just need a quick d100 roll. Nothing else, nothing fancy. 
- Override styling for `Furnace` module Advanced Macro dialog. 
