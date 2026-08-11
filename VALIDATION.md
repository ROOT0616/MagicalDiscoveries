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
