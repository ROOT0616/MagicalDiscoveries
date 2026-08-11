# 2.0.0-beta2.2

Second Stellaris 4.4.6 runtime hotfix.

- Reduced the runtime `error.log` from the beta2.1 test to the remaining three warning families.
- Replaced the duplicate `zz_MD_galactic_community_effects.txt` definition with an intentional exact-path override of the complete Stellaris 4.4.6 Vanilla `galactic_community_effects.txt`, adding only Heavenly-focus cleanup.
- Added required AI-weight description keys to the Heavenly Realm Galactic Focus resolution.
- Disabled auto-generation of default Adamantite ship designs at galaxy creation to avoid custom ship-size namelist failures.

# 2.0.0-beta2.1

Runtime hotfix based on the first Stellaris 4.4.6 test log.

- Removed the accidental full shadow of Vanilla `galactic_community_effects.txt`.
- Modernized custom jobs for the 4.4 `swappable_data` job schema.
- Replaced removed triggers/modifiers (`has_job`, `num_pops`, `pop_growth_speed`, `leader_age`).
- Updated deficit growth penalties to current 4.4 modifiers.
- Added required building sets and corrected colony/planet flag scope.
- Retargeted Heavenly ships to current Vanilla extradimensional ship sizes/entities.
- Removed obsolete duplicated Swarm portrait assets and use the current extradimensional portrait.
- Added missing Longinus, Magical Awakening and Heavenly dialogue localization.
- Updated Adamantite ship construction to the current Titan construction triggers.
- Fixed resource-group overrides to shadow the intended Vanilla interface files exactly.
- Rebased the Galactic Focus category onto the exact current Vanilla 4.4 category file, eliminating the duplicate category definition while retaining the Heavenly focus entry.
- Added aliases for generated modifier icons reported missing by the runtime log.

# Changelog

## 2.0.0-beta2

- Replaced the old MTTH book-purchase introduction with the **Magical Awakening** Situation.
- Added deterministic yearly story gatekeepers and removed random bi-yearly discovery rolls.
- Preserved legacy technology unlock flags so the existing technology tree remains compatible.
- Added staged magical/alchemical progression through a narrative Situation.
- Reworked the Necronomicon into a deliberate mid-game point-of-no-return choice.
- Replaced the old immediate Heaven encounter prelude with a ten-year omen sequence.
- Added redundant delayed crisis schedulers to avoid losing the crisis when one triggering empire is destroyed.
- Reworked the first anti-Heaven breakthrough to trigger from destroying a real Heavenly fleet.
- Split story conditions/effects into scripted triggers and scripted effects.
- Retained the existing Heaven invasion backend (fleet spawning, anchors, portal, GC integration) for beta2 stability.
- Removed obsolete Vanilla overrides for Defender of the Galaxy, orbital bombardment rules and Curator initializers.

## 2.0.0-beta1

- Initial Stellaris 4.4 compatibility pass.
