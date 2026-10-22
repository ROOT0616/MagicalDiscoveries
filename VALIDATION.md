# Validation notes - 2.0.0-beta2

Target: Stellaris 4.4.x, based on the user-provided Vanilla 4.4 files.

Static checks performed:
- Balanced braces and quoted strings in script/GFX files.
- Duplicate event ID scan.
- Event references from on_actions and special projects.
- Technology prerequisite references.
- New Situation type and start_situation usage compared with current Vanilla examples.
- GFX event pictures verified against the provided Vanilla interface files.
- New scripted trigger/effect names checked for internal references.
- Localization key duplication scan.
- Removed obsolete Vanilla override files.

Not yet verified:
- Runtime parser/error.log in Stellaris.
- AI pacing and balance of the new Situation.
- Full Heaven crisis completion in an actual campaign.
- Compatibility with other mods overriding Galactic Focus or resource groups.

## 2.0.0-beta2.1 runtime-log fixes

Validated against the user-provided Stellaris Pegasus v4.4.6 Vanilla files and the first runtime `error.log`.
Targeted the first-load parser/scope/definition errors before further story work.

## 2.0.0-beta2.2 runtime-log follow-up

The second Stellaris 4.4.6 `error.log` contained only:
1. duplicate `repeal_all_galactic_focus_resolutions`,
2. missing descriptions for nine resolution AI-weight modifiers,
3. automatic class-name generation failures for `md_adamantite_ship`.

beta2.2 targets exactly those remaining startup-log warnings.

## 2.0.0-beta2.3 Heavenly crisis validation

Compared the Heavenly crisis entry event against Stellaris 4.4.6 `crisis_events_2.txt`.

Runtime-test target:
- Necronomicon accepted;
- Heavenly omen events fire;
- Heavenly Realm country, portal, starbase and initial fleet spawn;
- no new `error.log` entries;
- first Heavenly fleet destruction enables `GOD_SKIN_PROJECT`;
- `GOD_SKIN_PROJECT` -> `MYTHICAL_DECAY_PROJECT` -> `tech_mythical_decay`.

## 2.0.0-beta2.4 Heavenly fleet test fixes

Based on the runtime report where Heavenly fleets remained at the portal for multiple years.

Runtime log findings addressed:
- missing EXD species namelist;
- malformed Heavenly fleet sequential-name format;
- missing random portal name;
- `magical_discoveries_crisis.1009` lacking valid AI options;
- unsupported custom-fleet bombardment stance.

Strategic movement is now explicitly scripted with the Stellaris 4.4 `queue_actions`,
`find_closest_system`, `space_owner`, and `move_to` interfaces verified in the supplied Vanilla files.

Heavenly combat-fleet creation sites updated: 4.

## 2.0.0-beta2.5 trigger-ID validation

The beta2.4 runtime log showed that `md_heaven_assign_invasion_orders` was expanded
at five script locations while its internal trigger IDs were constant. Stellaris
requires trigger IDs to be globally unique.

The effect now uses `$EVENT_ID$.while` and `$EVENT_ID$.target`, following the
parameterized trigger-ID pattern used by current Stellaris 4.4 Vanilla scripted
effects. Each call site supplies a distinct `EVENT_ID`.

## 2.0.0-beta2.6 adaptive Heavenly balance

Vanilla 4.4.6 references used:
- `add_awakened_fallen_empire_fleet` in
  `common/scripted_effects/fallen_empire_scripted_effects.txt`, including
  `ordered_playable_country`, `trigger:fleet_power`, target variables and bounded scaling.
- current `check_galaxy_setup_value` usage for `crisis_strength_scale`.

Model:
- formation: 1 God / 3 Goddesses / 8 Divine Soldiers;
- base target: strongest playable fleet power x 1.10;
- crisis-strength soft factors: 0.75 / 1.00 / 1.20 / 1.40 / 1.80;
- anchor factors: 1.00 / 1.15 / 1.30 / 1.50;
- high-power combat tiers begin at 500k / 2M / 10M / 50M / 200M.

A save created after the old Heavenly invasion already contains the oversized
fleets, so actual balance must be tested from a pre-invasion save.

- Descriptor validation: `version="2.0.0-beta2.6"`, `supported_version="4.4.*"`.

## 2.0.0-beta2.7 Heavenly starbase

Runtime error addressed:
`Trying to create a starbase with an invalid starbase design ... for ship size starbase_exd_0`.

The Heavenly normal-starbase design now uses the exact current Stellaris 4.4
Vanilla `ed_starbase_key` layout and Vanilla extradimensional components.
The MD-specific `angel_starbase_key` remains defined but is no longer used by
the normal Heavenly starbase.

## 2.0.0-beta2.8

Verified against supplied Stellaris 4.4.6 Vanilla:
- `awaken_guardians_of_the_galaxy`;
- `fallen_empires_awakening.4`;
- `guardians_of_the_galaxy`;
- `timed_guardians_of_the_galaxy`;
- `timed_guardians_of_the_galaxy_2`;
- diplomatic `picture_event_data` with a Fallen Empire event target;
- `situation_log_category = crises`.

Pacing:
- GOD_SKIN_PROJECT = 4,000 Society.
- MYTHICAL_DECAY_PROJECT = 6,000 Engineering.

Fallen Empire:
- 60% one-time contact chance.
- 35% accelerated Guardian chance after contact for a valid non-machine,
  non-hive Fanatic Materialist/Xenophile Fallen Empire with >60k fleet power.
- Actual awakening/transformation remains Vanilla's responsibility.

## 2.0.0-beta3.0 — Chapter I / story-state validation

Verified against supplied Stellaris 4.4.6 Vanilla before implementation:

- `give_technology = { tech = ... }` is current and used by Vanilla.
- `add_research_option = tech_xxx` is current and used by Vanilla.
- `set_timed_country_flag` is current.
- `country_has_situation = { SITUATION = ... }` is current.
- Situation `on_monthly -> random_events`, `situation_event`, `set_situation_flag`,
  `has_situation_flag`, and `on_first_enter` are current.
- No Vanilla technology, Situation, event or global definition is overridden.

Canonical beta3 Chapter I state:

- 25%: `md_magic_stage_1`, grants `tech_magical_science`.
- 50%: `md_magic_stage_2`, `md_alchemy_stage_1`, grants `tech_alchemy`.
- 75%: `md_magic_stage_3`, `md_alchemy_stage_2`, `md_mithril_discovered`.
- 100%: `md_alchemy_stage_3`, `md_magic_civilization_established`;
  guarantees Mithril Refining, Advanced Magical Science and Advanced Alchemy.

Legacy handling:

- old purchase-era flags are read only through scripted compatibility triggers
  and the one-time migration effect;
- new beta3 story progression does not set them;
- the beta2 Necronomicon purchase gate is disabled pending beta3.1.

## 2.0.0-beta3.0.1

Runtime issues reproduced from the user test:
- malformed Chapter I localization;
- invalid event picture `GFX_evt_laboratory`;
- unset variable `x` in `tech_md_adamantite_hull`.

Technology structure after this patch:

Core:
`tech_magical_science`
-> `tech_advanced_magical_science`
-> `tech_ultimate_magical_science`

Society:
- Black Magic -> Attack Magic -> Advanced Attack Magic.
- White Magic -> Defensive Magic -> Advanced Defensive Magic.
- White Magic -> White Magic Court.
- Advanced White Magic + Advanced Defensive Magic -> Barrier Magic.
- Magical Forces requires Attack + Defensive Magic.
- Elite Magical Forces also requires Magical Forces itself.

Materials:
Mithril -> Orichalcum -> Ultimate Alchemy -> Philosopher's Stone -> Adamantite.

## 2.0.0-beta3.0.2 — installed Stellaris 4.5.2 review

Reference: the user's installed `launcher-settings.json` reports
`Cygnus v4.5.2 (9776)`, `modsCompatibilityVersion = 4.5`.
Review date: 2026-10-22 (Asia/Tokyo).

The project archives under `sources/` are read-only. Their common/events/interface
text files match the corresponding installed files. Their original version/date
of acquisition is not established here: this does not demonstrate that every
engine behavior is unchanged between 4.4.6 and 4.5.2. Earlier version labels in
this document are historical; this review uses the installed game directly.

Static review covers script delimiters/strings, duplicate event IDs and
localization keys, direct and nested event localization, UTF-8 BOM, technology
prerequisite existence and cycles, MD scripted references, event call links,
event pictures and referenced Vanilla definitions. Core Chapter I ordering
and civilization gates are retained from beta3.0.1.

Exact-path overrides retained, checked against installed 4.5.2:

- `common/resolution_categories/00_resolution_categories.txt`: adds only
  `resolution_galactic_focus_crisis_heavenly` to the Galactic Focus category.
- `common/scripted_effects/galactic_community_effects.txt`: extends
  `repeal_all_galactic_focus_resolutions` with Heavenly flag/resolution cleanup.
- `interface/resource_groups/sectors_other_resource_groups.txt`: MD resources.
- `interface/resource_groups/topbar_other_resource_groups.txt`: MD resources.

These files can conflict with other mods replacing the same paths/definitions.
No new Vanilla override is introduced in this release. No replace_path is used.

Save compatibility:

- The beta3.0.1 -> beta3.0.2 content changes preserve all gameplay IDs and state.
- Existing beta2 -> beta3 yearly migration remains unchanged.
- Loading a 4.4 campaign in game version 4.5.2 is not guaranteed. A new 4.5.2
  campaign is required as the baseline for this release's runtime validation.
- No save-conversion operation is performed or claimed.

Runtime NOT YET VERIFIED: startup/parser log with MD enabled, Chapter I stages,
research draws, building/job production, Heavenly invasion/AI, and save/reload.
An existing empty error.log from a session without enabled mods is not evidence
of MD compatibility. The Launcher target version is metadata, not a test result.
Follow the README checklist and retain the fresh error.log/game.log.
