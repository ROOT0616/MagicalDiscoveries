# 2.0.0-beta3.0.3

First Stellaris 4.5.2 Chapter I runtime-log follow-up.

- Added the three engine-required Heavenly passage localization keys in English
  and Japanese: BYPASS_MD_HEAVENES_HOLE, ENTRY_BYPASS_MD_HEAVENES_HOLE and
  EXIT_BYPASS_MD_HEAVENES_HOLE. These were the only three entries in the supplied
  beta3.0.2 error.log. The bypass definition and travel behavior are unchanged.
- Recorded the user's new-game Chapter I test, six screenshots and event log.
  The four main stage descriptions/tooltips display; the two optional events
  also appeared. Research-option availability is user-reported; a research-screen
  capture, prerequisite tests and save/reload remain pending.
- Added bypass-localization coverage to the static release check.

# 2.0.0-beta3.0.2

Stellaris 4.5.2 static compatibility review and English localization hotfix.

- Retargeted descriptor and portable Launcher metadata to Stellaris 4.5.x;
  the installed reference build is Cygnus v4.5.2 (9776).
- Checked the existing four exact-path overrides against installed Vanilla.
  Their base content still matches; only the existing MD additions remain.
- Verified technology prerequisites, scripted references, event links and pictures
  against the installed game files. This is not a runtime certification.
- Fixed an unescaped quotation pair in the English Alchemy description.
- Added the missing English bombardment event title and all sixteen resource-
  deficit event strings, including machine-empire description branches.
- Added a portable Launcher descriptor and a new-game runtime test checklist.
- Kept gameplay definitions, technology IDs and story migration unchanged.
- Use a new 4.5.2 campaign for validation. Loading 4.4 saves is not guaranteed.

# 2.0.0-beta3.0.1

Chapter I readability and technology-tree hotfix.

- Fixed malformed multiline Japanese/English localization introduced in beta3.0.
  This caused the blank `Magical Civilization` event description.
- Replaced invalid `GFX_evt_laboratory` with current Vanilla
  `GFX_evt_physics_research`.
- Chapter I events now state explicitly when Magical Science and Alchemy are
  granted, when Mithril is discovered, and exactly which three guaranteed
  research options are added at Situation completion.
- Advanced Magical Science / Advanced Alchemy can no longer roll before the
  Magical Awakening Situation is complete.
- White Magic and Black Magic application branches now start only after a
  magical civilization is established.
- Rebuilt the Society magic branch:
  Black Magic -> Attack Magic;
  White Magic -> Defensive Magic;
  White Magic -> White Magic Court;
  Magical Forces requires both Attack and Defensive Magic;
  Elite Magical Forces additionally requires the normal Magical Forces tech;
  Barrier Magic follows the advanced White/Defensive branch.
- Tightened the alchemical material ladder:
  Mithril -> Orichalcum -> Ultimate Alchemy -> Philosopher's Stone -> Adamantite.
- Removed an unfinished `value = x` placeholder in Adamantite Hull AI weighting.

# 2.0.0-beta3.0

Story Rework, Chapter I: Magical Awakening.

- Introduced the new canonical beta3 story flags:
  `md_magic_stage_1/2/3`, `md_alchemy_stage_1/2/3`,
  `md_magic_civilization_established`, and `md_mithril_discovered`.
- Centralized all old `BuyGrimoireFlag*` / `BuyAlchemyFlag*` compatibility in
  scripted triggers and a one-time migration effect.
- New beta3 progression no longer writes the old purchase-era flags.
- Added yearly beta2 -> beta3 save migration (`magical_discoveries.90`).
- Rebuilt Magical Awakening as the complete first chapter:
  reproducibility -> Magical Science -> Alchemy -> Mithril -> magical civilization.
- `tech_magical_science` is now granted directly at 25% Situation progress.
- `tech_alchemy` is now granted directly at 50% Situation progress.
- Mithril is discovered narratively at 75%.
- On completion, `tech_mithril_refinery`, `tech_advanced_magical_science`,
  and `tech_advanced_alchemy` are guaranteed research options.
- All existing technology potential checks now use beta3 scripted story triggers
  rather than directly referencing the old purchase flags.
- Added two optional Situation story events whose decisions are remembered for
  later beta3 chapters: laboratory safety and the treatment of ancient folklore.
- Rejecting the initial magical research now suspends it for ten years instead
  of permanently deleting the entire story path.
- Disabled the automatic beta2 Necronomicon purchase event. The old event remains
  console-accessible only until beta3.1 replaces it with the sealed-archive story.
- God-Skin distribution now recognizes beta3 magical civilizations instead of
  requiring the old `MeetMagicFlag`.

# 2.0.0-beta2.8

Countermeasure pacing and Fallen Empire story pass.

- Reduced `GOD_SKIN_PROJECT` from 20,000 to 4,000 Society research.
- Reduced `MYTHICAL_DECAY_PROJECT` from 20,000 to 6,000 Engineering research.
- Added both projects to the Crises section of the Situation Log.
- Added a one-time 60% chance of a Fallen Empire diplomatic transmission shortly
  after GOD_SKIN_PROJECT becomes available.
- The contact prefers an empire already selected by Vanilla's
  `awaken_guardians_of_the_galaxy` logic.
- After contact, an eligible Fanatic Materialist/Xenophile Fallen Empire has a
  35% chance to lose the normal Guardian delay flags, allowing Vanilla's existing
  `fallen_empires_awakening.4` system to awaken it shortly afterward.
- Vanilla's normal Guardian awakening roll remains intact.
- Tightened the Heavenly normal-starbase fallback after beta2.7 still logged an
  invalid `starbase_exd_0` design.

# 2.0.0-beta2.7

Heavenly starbase compatibility hotfix.

- Rebased the normal Heavenly `starbase_exd_0` design on the exact current
  Stellaris 4.4 Vanilla extradimensional starbase section/component layout.
- Preserved the Heavenly name, country type and adaptive country-level scaling.
- Fixes runtime failure to create occupied-system Heavenly starbases because
  the legacy custom design was rejected as an invalid mobile/FTL-capable starbase.

# 2.0.0-beta2.6

- Corrected `descriptor.mod` back to `supported_version="4.4.*"`; earlier beta packaging accidentally replaced this field with the MOD version.
Adaptive Heavenly Realm balance pass.

- Replaced the old fixed 46-61 ship Heavenly combat formations with compact
  12-ship formations: 1 God, 3 Goddesses and 8 Divine Soldiers.
- Added reactive scaling from the strongest playable empire's actual
  `trigger:fleet_power`, following Stellaris 4.4 awakened-FE scaling principles.
- Base Heavenly sustainable military target is about 110% of the strongest empire.
- Crisis Strength is applied through softened factors rather than raw x5/x10/x25 multiplication.
- Anchor networks raise the sustainable target gradually (up to +50%).
- High-output mod environments use adaptive combat-stat tiers instead of hundreds of ships.
- Initial forces are generated only until the target is reached.
- Early, periodic and anchor reinforcements now occur only after Heavenly losses
  or when the galaxy has grown beyond the current Heavenly force.

# 2.0.0-beta2.5

Heavenly invasion-order parser hotfix.

- Parameterized the internal trigger IDs used by `md_heaven_assign_invasion_orders`.
- Assigned a unique compile-time `EVENT_ID` to all five invasion-order call sites.
- Removes the duplicate trigger-ID errors reported after the successful beta2.4 fleet-movement test.

# 2.0.0-beta2.4

Heavenly fleet AI and naming hotfix.

- Fixed Heavenly species random-name generation by assigning `Hevenlyname` directly in `create_species`.
- Fixed the fleet sequential-name format from `%C%` to current Stellaris `$C$`.
- Added generic Heavenly ship-name fallback and an explicit portal name.
- Added deterministic invasion orders for Heavenly combat fleets using the current 4.4 fleet `queue_actions` / `find_closest_system` system.
- Applied invasion orders to initial, reinforcement and later Heavenly combat fleets.
- Added yearly retrofit event `magical_discoveries_crisis.22` so already-spawned fleets in test saves can receive the new orders.
- Removed the unsupported Armageddon bombardment-stance assignment from the custom Heavenly fleet.
- Added a fallback option to `magical_discoveries_crisis.1009` so AI empires always have a valid response.

# 2.0.0-beta2.3

Heavenly crisis runtime hardening for Stellaris 4.4.6.

- Added the generic `galactic_crisis_happened` flag when the Heavenly Realm invades.
- Updated Heavenly crisis spawn-system exclusions to the current 4.4 extradimensional-crisis rules.
- Updated portal invulnerability targeting from `random_owned_ship` to current `random_controlled_ship`.
- Added explicit Armageddon bombardment stance to the initial Heavenly invasion fleet.
- Added current generic Galactic Custodian / Galactic Emperor crisis announcements.
- Saved the empire that accepted the Necronomicon as `md_necronomicon_country` for later story use.
- Reworked the first Heavenly fleet-kill reward so all surviving magical empires receive the divine-material project.
- Added a fallback that gives the project to the victorious empire if no magical empire survives, preventing a crisis deadlock.

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
