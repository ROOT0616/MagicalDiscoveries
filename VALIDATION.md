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
