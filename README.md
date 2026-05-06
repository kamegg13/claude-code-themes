# Claude Themes — Marketplace

A public marketplace of Claude Code themes, ported from the most popular [Ghostty](https://ghostty-style.vercel.app) terminal configs.

## Installation

> Requires Claude Code **v2.1.118+** (plugin themes need this version).

### 1. Add the marketplace

In a Claude Code session, run:

```
/plugin marketplace add kamegg13/claude-code-themes
```

Claude Code clones the repo into `~/.claude/plugins/marketplaces/` and reads `.claude-plugin/marketplace.json` to discover available plugins.

### 2. Install the theme bundle

```
/plugin install ghostty-popular@claude-code-themes
```

The `@claude-code-themes` suffix explicitly targets this marketplace (useful when multiple marketplaces expose plugins with the same name).

### 3. Pick a theme

```
/theme
```

The 20 themes appear in the list as `custom:ghostty-popular:<slug>`, alongside the built-in presets. Select one — your choice is saved in `~/.claude/settings.json`.

### Edit a theme

Plugin themes are read-only. Press `Ctrl+E` while a theme is highlighted in `/theme` to copy its JSON into `~/.claude/themes/<slug>.json`. You can then edit the copy freely (Claude Code hot-reloads on save).

### Updates

```
/plugin marketplace update claude-code-themes
```

### Uninstall

```
/plugin uninstall ghostty-popular@claude-code-themes
/plugin marketplace remove claude-code-themes
```

## Available plugins

| Plugin | Description | Themes |
| :--- | :--- | :--- |
| `ghostty-popular` | Top 20 dark themes from ghostty-style | 20 |

## `ghostty-popular` — full list

Catppuccin Mocha · Catppuccin Macchiato · TokyoNight · TokyoNight Storm · TokyoNight Moon · Gruvbox Dark · Nord · Atom One Dark · Monokai Pro Octagon · Monokai Vivid · Cyberdream · Cyberpunk · Aura · Vague · Charleston · Whimsy · Argonaut · Black Metal · Grass · Neon Blue Split Contrast.

## ANSI palette → Claude Code tokens

Each theme derives its tokens from the Ghostty palette:

- `claude` / `remember` / `merged` ← magenta (palette[13])
- `planMode` ← blue · `ide` / `fastMode` / `suggestion` ← cyan
- `success` / `autoAccept` ← green · `error` ← red · `warning` / `permission` / `bashBorder` ← yellow
- `diffAdded` / `diffRemoved` ← red/green darkened (~75% toward black), `Dimmed` and `Word` variants derived
- `userMessageBackground` ← bg tinted with blue · `messageActionsBackground` ← bg tinted with magenta
- `selectionBg` ← theme's native selection · `inactive` / `subtle` ← bright black ANSI

## Contributing

Contributions are welcome — new themes, new bundles, or improvements to the token mapping.

### Add a theme to an existing bundle

1. **Fork** this repo and clone your fork.
2. Create a JSON file at `plugins/<bundle>/themes/<slug>.json` following this schema:
   ```json
   {
     "name": "Display Name",
     "base": "dark",
     "overrides": {
       "claude": "#a78bfa",
       "planMode": "#38bdf8"
     }
   }
   ```
   The full token reference lives in the [Claude Code docs](https://code.claude.com/docs/terminal-config#create-a-custom-theme).
3. Test locally: copy the file into `~/.claude/themes/` and run `/theme` to verify the rendering.
4. Open a PR with the theme and an entry in the README list.

### Create a new bundle

1. Create `plugins/<bundle-name>/` containing:
   - `.claude-plugin/plugin.json` (see `plugins/ghostty-popular/` as a reference)
   - `themes/` with the JSON files
2. Add an entry in `.claude-plugin/marketplace.json`.
3. Document the bundle in the README under "Available plugins".

### Guidelines

- **One PR per bundle or coherent set of themes** — don't mix multiple bundles.
- Theme names should preserve original attribution when porting from an existing scheme (Catppuccin, TokyoNight, etc.).
- No light themes in `ghostty-popular` — create a separate `ghostty-popular-light` bundle if needed.
- The ANSI → token mapping documented above should stay consistent within a bundle.

### Issues

To report a theme that renders poorly (low contrast on a particular token, unreadable diff colors), open an issue with a screenshot and the theme slug.

## Source

Palettes extracted from the public [ghostty-style.vercel.app](https://ghostty-style.vercel.app) API, itself sourced from [iTerm2-Color-Schemes](https://github.com/mbadolato/iTerm2-Color-Schemes). Credits to the original palette authors.

## License

MIT.
