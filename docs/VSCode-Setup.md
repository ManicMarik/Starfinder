# VS Code setup for a Fantasy Grounds ruleset

## 1. Prerequisites
- [VS Code](https://code.visualstudio.com/), Git, and Fantasy Grounds (Classic or Unity).
- A GitHub account with Copilot access.
- Optional: set env var `FG_DATA` to your FG data folder (e.g. `%APPDATA%\SmiteWorks\Fantasy Grounds` on Windows,
  `~/SmiteWorks/Fantasy Grounds` on Mac/Linux).

## 2. Open the workspace
```
git clone https://github.com/ManicMarik/Starfinder
code Starfinder
```
Accept the prompt to install recommended extensions (`.vscode/extensions.json`): Copilot, Copilot Chat,
Lua (sumneko), XML (Red Hat), EditorConfig, Spell Checker, Markdown All in One.

## 3. Ruleset layout
```
base.xml            entry point (name, description, importruleset CoreRPG)
common/ campaign/ ruleset/   XML windowclasses, templates
scripts/            Lua managers
graphics/           icons, frames, images
strings/            strings_starfinder.xml
```
Create these as you go. Minimum `base.xml`:
```xml
<?xml version="1.0" encoding="iso-8859-1"?>
<root version="4.0" logo="">
  <properties>
    <name>Starfinder</name>
    <version>1.0</version>
    <author>Your Name</author>
    <description>Starfinder ruleset</description>
    <ruleset>CoreRPG</ruleset>
  </properties>
</root>
```
Get CoreRPG source by unzipping `rulesets/CoreRPG.pak` into a folder outside this repo for reference.

## 4. Develop, build, test
- Run task **Package ruleset (.pak)** (Ctrl+Shift+B) to produce `dist/Starfinder.pak`.
- Run **Deploy to Fantasy Grounds rulesets folder** to copy it to `$FG_DATA/rulesets`.
  Alternatively, develop in place: place/symlink the unzipped folder in `rulesets/`; FG loads unpacked folders.
- In FG, create a campaign with the Starfinder ruleset; use `/reload` in chat to reload after changes,
  and enable the console (`/console`) to see Lua/XML errors.

## 5. Copilot
1. Install **GitHub Copilot** and **Copilot Chat**, then sign in (Accounts icon, bottom-left).
2. `.github/copilot-instructions.md` is loaded automatically and tells Copilot about FG conventions;
   `github.copilot.chat.codeGeneration.useInstructionFiles` is already enabled.
3. Tips: attach CoreRPG files as context (`#file`) when asking for overrides; ask for
   "CoreRPG-compatible windowclass XML + Lua"; use `@workspace` to query the house-rule docs.
4. Always review generated Lua/XML in FG's console; Copilot may invent API names. Check against the FG API docs.
5. Optional: use Copilot coding agent by assigning GitHub issues to Copilot.

## 6. Settings summary
`.vscode/settings.json` configures Lua 5.3 with FG globals, XML validation, indentation, and Copilot.
Add any extra FG globals to `Lua.diagnostics.globals`.
