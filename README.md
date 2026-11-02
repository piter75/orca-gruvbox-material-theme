# Gruvbox Material for Orca

Warm dark and light application themes using Gruvbox Material's **Material**
foreground palette and **Medium** background contrast, with matching syntax and
terminal colors.

Select **Gruvbox Material Dark Medium** or **Gruvbox Material Light Medium**
in Appearance, and select the corresponding theme in terminal settings.

Both themes use uniform panel backgrounds: Dark uses `#282828`, Light uses
`#fbf1c7`. The editor, file sidebar, project sidebar, cards, popovers and terminal
share that background. Subtle warm borders separate panels.

## Installation

Find **Gruvbox Material for Orca** by **piter75** in Orca's plugin catalog.
The plugin requires Orca **1.4.245 or newer**.

If the community listing has not appeared yet, install from this Git repository
through Orca's plugin settings:

```text
https://github.com/piter75/orca-gruvbox-material-theme
```

## Testing the 1.4.246 UI colors

The `material-ui-tokens` branch is an untagged development preview. It adds:

- Uniform tab backgrounds, normal/muted tab text, and an accent-colored active-tab indicator.
- Warm split dividers with an accent-colored hover state.
- Material blue links, green/red diffs, and Material Git file-status colors.
- Five chart colors: yellow, green, blue, purple, and orange.

Use Orca **1.4.246 or newer** to test these colors. Orca 1.4.245 ignores the new
UI tokens and retains its existing appearance; chart colors also apply there.
The manifest keeps the existing minimum version for compatibility.

With this branch checked out, add the repository folder under **Settings →
Plugins → Development folders…**, or run:

```sh
orca plugin dev load /path/to/orca-gruvbox-material-theme
```

The development folder overrides the installed plugin with the same identity.
Remove it from Development folders, or run `orca plugin dev unload` with the
same path, to return to the installed catalog release. This preview has no
version tag and does not update the community catalog.

Diff line backgrounds use upstream Material diff surfaces in Dark. Light uses
slightly lighter versions to preserve Orca's required chat-diff contrast.
Character and gutter tints are derived by Orca from the green/red hues.
Workspace selection, host badges, chat surfaces, syntax highlighting, and
terminal palettes retain their existing behavior.

## Development and releases

This repository contains one content-only plugin, with its manifest at the root.
No build or dependency installation is needed. Normal Git branches and Orca
worktrees can be used to develop both appearances together.

Validate with Orca 1.4.246 or newer:

```sh
orca plugin validate .
```

Before publishing a release, update `version` in `orca-plugin.json`, commit the
plugin changes, and validate the committed tree. Push a matching `vX.Y.Z` tag.
The public repository carries the `orca-plugin` topic for automatic community
discovery. Check its listing status at
[onorca.dev/plugins/piter75/orca-gruvbox-material-theme](https://www.onorca.dev/plugins/piter75/orca-gruvbox-material-theme).

## Variants and chat appearance

The plugin includes the upstream **Material** foreground palette and **Medium**
background contrast. Soft/Hard backgrounds and Mix/Original foreground palettes
are not included. Uniform panel backgrounds are the only layout delivered.

Orca applies its own background tint to dark native chat panels. Plugin themes
cannot override that tint with the current public theme tokens, so chat may
appear slightly lighter than the sidebars. The plugin does not change chat fonts
or require matching the terminal interface.

The panel layout was inspired by
[sainnhe/gruvbox-material-vscode at `91ff2deaecd2e89ec95ab488f4aee3f614f54031`](https://github.com/sainnhe/gruvbox-material-vscode/tree/91ff2deaecd2e89ec95ab488f4aee3f614f54031).

## Palette mapping

The palette and highlight mappings come from
[sainnhe/gruvbox-material at `11d779b26a9ab2b3db8c22c6ac9fb6e8ed4fea79`](https://github.com/sainnhe/gruvbox-material/tree/11d779b26a9ab2b3db8c22c6ac9fb6e8ed4fea79).
This is an unofficial Orca port, with the app token and TextMate scope mappings
maintained here.

| Orca role | Upstream palette role |
| --- | --- |
| App and editor background | `bg0` |
| Sidebar and project sidebar | `bg0` |
| Cards, popovers, secondary and muted surfaces | `bg0` |
| Hover, selected rows, terminal selection | `bg3` |
| Main text | `fg0` |
| Muted text | `grey2` |
| Inputs | Dark: `bg1`; Light: `bg3` |
| Panel borders | Dark: `bg3`; Light: `bg5` |
| Primary action and focus ring | Dark: `yellow`; Light: `red` (primary action adjusted below) |

Two Light app colors are darkened to satisfy Orca's 4.5:1 text contrast floor:
primary red is `#b94747` instead of `#c14a4a`, and muted text is `#726559` instead
of `#7c6f64`. Syntax colors retain the upstream palette and meet Orca's 3:1
syntax contrast floor on the editor background.

The syntax mapping uses red keywords, orange storage modifiers, operators and
tags, green strings and functions, yellow types and escapes, purple booleans,
numbers and decorators, aqua constants, blue variables and links, and italic
`grey1` comments.

Boolean rules target `constant.language.boolean`, `constant.language.true`, and
`constant.language.false`; storage modifiers use `storage.modifier`. Their
appearance depends on the scopes exposed by each language tokenizer. A tokenizer
that combines them with general keywords cannot distinguish these colors.

Terminal ANSI slots follow upstream's terminal mapping, including identical
normal and bright colors. Black uses Dark `bg5` / Light `fg0`, white uses Dark
`fg0` / Light `bg5`, and cyan uses `aqua`. The terminal background, foreground,
cursor and selection use `bg0`, `fg0`, `fg0` and `bg3`, respectively.

## Attribution

Gruvbox Material is MIT licensed, Copyright (c) 2020 sainnhe. The upstream notice
and the Orca port's license are included in [LICENSE](LICENSE).

The cover is an illustrative editor preview rendered from the plugin JSON,
rather than a captured Orca session.
