# Claude Themes — Marketplace

Marketplace public de thèmes Claude Code, portés depuis les configurations [Ghostty](https://ghostty-style.vercel.app) les plus populaires.

## Installation

Dans Claude Code (v2.1.118+) :

```
/plugin marketplace add karim/claude-themes
/plugin install ghostty-popular@claude-themes
```

Les thèmes apparaissent ensuite dans `/theme`. Sélectionne-en un — il sera persisté comme `custom:ghostty-popular:<slug>` dans ta config.

> `Ctrl+E` sur un thème copie le JSON dans `~/.claude/themes/` pour le modifier.

## Plugins disponibles

| Plugin | Description | Thèmes |
| :--- | :--- | :--- |
| `ghostty-popular` | Top 20 thèmes dark de ghostty-style | 20 |

## `ghostty-popular` — liste

Catppuccin Mocha · Catppuccin Macchiato · TokyoNight · TokyoNight Storm · TokyoNight Moon · Gruvbox Dark · Nord · Atom One Dark · Monokai Pro Octagon · Monokai Vivid · Cyberdream · Cyberpunk · Aura · Vague · Charleston · Whimsy · Argonaut · Black Metal · Grass · Neon Blue Split Contrast.

## Mapping palette ANSI → tokens Claude Code

Chaque thème dérive ses tokens depuis la palette Ghostty :

- `claude` / `remember` / `merged` ← magenta (palette[13])
- `planMode` ← blue · `ide` / `fastMode` / `suggestion` ← cyan
- `success` / `autoAccept` ← green · `error` ← red · `warning` / `permission` / `bashBorder` ← yellow
- `diffAdded` / `diffRemoved` ← red/green assombris (~75 % vers noir), variantes `Dimmed` et `Word` dérivées
- `userMessageBackground` ← bg teinté de blue · `messageActionsBackground` ← bg teinté de magenta
- `selectionBg` ← sélection native du thème · `inactive` / `subtle` ← noir brillant ANSI

## Source

Palettes extraites de l'API publique de [ghostty-style.vercel.app](https://ghostty-style.vercel.app), elle-même alimentée par [iTerm2-Color-Schemes](https://github.com/mbadolato/iTerm2-Color-Schemes). Crédits aux auteurs originaux des palettes.

## Licence

MIT.
