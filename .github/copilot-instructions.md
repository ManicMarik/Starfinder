# Copilot instructions

This repo holds Starfinder house rules (Markdown) and is the workspace for a new
**Fantasy Grounds Classic/Unity ruleset** for Starfinder.

## Ruleset conventions
- A ruleset is a folder with `base.xml` as the entry point; it is zipped and renamed `.pak`.
- Declare UI with XML (`windowclass`, `template`, `string`, `icon`, `script`), logic in Lua.
- Prefer layering on the CoreRPG ruleset (`<importruleset>CoreRPG</importruleset>`) and override
  only what is needed. Reuse CoreRPG templates and managers.
- Lua: global manager tables, `onInit()` entry points, `DB.*` API for data access, 4-space indent.
- XML: 2-space indent, well-formed, one windowclass per file where practical.
- Keep strings in `strings/strings_starfinder.xml`; never hardcode UI text.
- Follow Starfinder rules from the Markdown docs in the repo root; house rules take precedence.
- Reference docs: https://fantasygroundsunity.atlassian.net/wiki/spaces/FGCP/
