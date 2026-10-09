# VSCode — Obsidian Theme

> A faithful port of Microsoft Visual Studio 2026's Fluent visual language to Obsidian, with first-class macOS vibrancy support.

![VSCode 2026 theme preview](screenshot.png)

## Features

- **Light & Dark mode** — follows system color scheme; 2026 Dark uses `#121314` editor backgrounds, `#191A1B` sidebar/window surfaces and `#202122` menus/widgets
- **Theme accent colors** — `#0069CC` for 2026 Light, `#005FB8` for Light Modern, and `#2F72C4` for this theme's Dark palette; configurable per mode, with optional Obsidian accent override
- **VSCode syntax highlighting** — 2026 Light/Dark colors and optional Light Modern colors; the local **VSCode Code Scroll** companion supplies matching Prism token classification in Live Preview and Reading view
- **macOS Tahoe-style polish** — SF Pro / SF Mono system font stack, 8–12 px rounded corners, defocused-window dim, `prefers-reduced-motion` support
- **Vibrancy / translucency** — sidebar, status bar, command palette and modals get `backdrop-filter` blur when *Translucent window* is enabled
- **Overlay scrollbars** — hidden by default, fade in on hover, macOS-style
- **All third-party UI themed via CSS variables** — callouts (13 types), graph view, canvas, calendar, dataview — no hardcoded colors

## Screenshot

![VSCode 2026 light and dark preview](screenshot.png)

## Installation

### From Community Themes (recommended, after marketplace approval)
1. *Settings* → *Appearance* → *Themes* → *Manage*
2. Search **VSCode 2026**
3. *Install* → *Use*

### Manual
1. Download `manifest.json` and `theme.css` from the latest [Release](../../releases/latest).
2. Place them in `<vault>/.obsidian/themes/VSCode 2026/`.
3. *Settings* → *Appearance* → *Themes* → choose **VSCode 2026**.

## Recommended Settings (macOS)

- *Settings* → *Appearance* → enable **Translucent window** to activate vibrancy.
- *Settings* → *Appearance* → set **Base color scheme** to **Adapt to system** so the theme follows your system Light/Dark setting.
- Minimum Obsidian version: **1.5.0** (uses `color-mix()`, requires Chromium 111+).

## Customization

With **Style Settings** installed, open **Settings → Style Settings → VSCode → 浅色配色** to choose **VS Code 2026 Light** (default) or **VS Code Light Modern**. The preset changes light-mode interface colors and both editor and reading-view syntax colors. Dark mode keeps its existing palette. Monospace fonts, code sizes, Markdown layout and scrolling are independent of the preset.

Dark window surfaces follow Microsoft's [2026-dark.json](https://github.com/microsoft/vscode/blob/main/extensions/theme-defaults/themes/2026-dark.json). Editing and reading areas use `#121314`; sidebars, the activity bar, tab strip and active title/status bars use `#191A1B`. Inactive title/status bars use `#121314`; menus and widgets use `#202122`, with `#2A2B2C` separators. These surfaces stay opaque when translucency is enabled, preserving the official contrast between the editor and surrounding panels.

Light Modern follows Microsoft's [light_modern.json](https://github.com/microsoft/vscode/blob/main/extensions/theme-defaults/themes/light_modern.json), including its inherited Light+ syntax palette. It retains this theme's black bold text and non-italic code styling.

Under **Settings → Style Settings → VSCode**, **使用 Obsidian 强调色覆写** is off by default. Enable it to use **Appearance → Accent color**; disable it to use **主题强调色（浅色 / 深色）**, which provides separate light and dark color pickers and reset buttons. Neither option changes the saved Obsidian accent color.

Resetting a picker clears its custom color. Light mode then follows the selected preset (`#0069CC` for 2026 Light or `#005FB8` for Light Modern); dark mode returns to `#2F72C4`. Style Settings displays the 2026 Light value as its light default. Custom theme colors are retained while the Obsidian override is enabled. Buttons, focus indicators, checkboxes, links and accent backgrounds share the selected source, and button text contrasts with the actual accent background.

**两端对齐与自动断词** is enabled by default, including without Style Settings. Its switch controls justification and automatic hyphenation in both reading and editing views. The former `hyphenation-and-justification.css` snippet is integrated into the theme; it no longer needs to be enabled separately.

Keep the local **VSCode Code Scroll** plugin enabled for matching editable code highlighting and per-block horizontal scrolling in Live Preview. Reading-view code scrolls inside its frame while its copy button stays at the upper right.

**代码块自动折行** is off by default. Enable it in **Settings → Style Settings → VSCode** to wrap code in both views, including long words and paths. PDF export always wraps, even when the switch is off. With the companion plugin enabled, a return arrow marks each visual continuation; actual source-line endings stay unmarked. Arrows are painted and do not alter copied code.

**代码块行号** is also off by default. Enable it in the same section to number original code lines in both views and PDF, starting at 1 for each block. Blank lines are counted; visual continuations have no extra number. Numbers stay in the left gutter during horizontal scrolling and are excluded from copied code. Keep **VSCode Code Scroll** enabled for the line wrappers and editable-line numbers.

In `theme.css`, `--vscode-code-flair-top` and `--vscode-code-flair-right` position the Live Preview language/copy label. Lower top values move it up. `--vscode-code-wrap-marker-inset` (`12px`) controls the Live Preview return-arrow inset from the right edge. The label centers both language text and the copy/confirmation icon.

Line numbers use the quieter `--vscode-code-line-number-color`. In the editor, the cursor line uses `--vscode-code-active-line-background` and its number uses `--vscode-code-active-line-number-color`; the gutter shares the active row background, including while scrolling or wrapping. All three colors follow the current light/dark palette without changing syntax colors.

Every color is a CSS variable. Override in a snippet:

```css
/* .obsidian/snippets/my-tweaks.css */
.theme-dark {
  --code-keyword:       #C586C0;       /* purple keywords */
}
.theme-light {
  --background-primary: #FAFBFD;
}
```

Common variables to tweak:

| Variable | Purpose |
| --- | --- |
| `--interactive-accent` | Effective accent color; configure its source and light/dark colors through Style Settings |
| `--background-primary` / `--background-secondary` | Editor and sidebar backgrounds |
| `--code-{keyword,string,comment,function,variable,type,number,control}` | Syntax highlight tokens |
| `--callout-{note,tip,info,success,question,warning,failure,error,bug,example,quote,abstract,todo}` | Callout colors (RGB triplets) |
| `--radius-{s,m,l,xl}` | Corner radii (default: 6 / 8 / 12 / 16 px) |
| `--vibrancy-blur` / `--vibrancy-saturation` | macOS vibrancy strength |

## Credits

- Microsoft Visual Studio 2026 Fluent design tokens — [DevBlogs 2026/06/15](https://devblogs.microsoft.com/visualstudio/make-visual-studio-look-the-way-you-want/)
- VSCode Dark+ / Light+ syntax color palette — [microsoft/vscode](https://github.com/microsoft/vscode/tree/main/extensions/theme-defaults/themes)
- Inspired by [leozague/obsidian-vscode-dark-plus](https://github.com/leozague/obsidian-vscode-dark-plus) — built independently from scratch, no code reused.

## License

MIT — see [LICENSE](LICENSE).
