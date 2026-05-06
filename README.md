# Claude Themes — Marketplace

Marketplace public de thèmes Claude Code, portés depuis les configurations [Ghostty](https://ghostty-style.vercel.app) les plus populaires.

## Installation

> Prérequis : Claude Code **v2.1.118+** (les thèmes via plugin nécessitent cette version).

### 1. Ajoute le marketplace

Dans une session Claude Code, exécute la commande :

```
/plugin marketplace add kamegg13/claude-code-themes
```

Claude Code clone le repo dans `~/.claude/plugins/marketplaces/` et lit `.claude-plugin/marketplace.json` pour découvrir les plugins disponibles.

### 2. Installe le bundle de thèmes

```
/plugin install ghostty-popular@claude-code-themes
```

Le suffixe `@claude-code-themes` cible explicitement ce marketplace (utile si plusieurs marketplaces exposent un plugin du même nom).

### 3. Active un thème

```
/theme
```

Les 20 thèmes apparaissent au format `custom:ghostty-popular:<slug>` dans la liste, à côté des présets intégrés. Sélectionne-en un — la préférence est sauvegardée dans `~/.claude/settings.json`.

### Modifier un thème

Les thèmes de plugin sont en lecture seule. Appuie sur `Ctrl+E` sur un thème en surbrillance dans `/theme` pour copier le JSON dans `~/.claude/themes/<slug>.json`. Tu pourras ensuite éditer la copie librement (Claude Code recharge à chaud à chaque sauvegarde).

### Mises à jour

```
/plugin marketplace update claude-code-themes
```

### Désinstallation

```
/plugin uninstall ghostty-popular@claude-code-themes
/plugin marketplace remove claude-code-themes
```

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

## Contribuer

Les contributions sont bienvenues — nouveaux thèmes, nouveaux bundles, ou améliorations du mapping de tokens.

### Ajouter un thème à un bundle existant

1. **Fork** ce repo et clone ta fork.
2. Crée un fichier JSON dans `plugins/<bundle>/themes/<slug>.json` en respectant le schéma :
   ```json
   {
     "name": "Nom Affiché",
     "base": "dark",
     "overrides": {
       "claude": "#a78bfa",
       "planMode": "#38bdf8"
     }
   }
   ```
   La référence complète des tokens est dans la [doc Claude Code](https://code.claude.com/docs/fr/terminal-config#cr%C3%A9er-un-th%C3%A8me-personnalis%C3%A9).
3. Teste en local : copie le fichier dans `~/.claude/themes/` et lance `/theme` pour vérifier le rendu.
4. Ouvre une PR avec le thème + une mention dans la liste du README.

### Créer un nouveau bundle

1. Crée `plugins/<nom-bundle>/` avec :
   - `.claude-plugin/plugin.json` (cf. exemple dans `plugins/ghostty-popular/`)
   - `themes/` contenant les fichiers JSON
2. Ajoute une entrée dans `.claude-plugin/marketplace.json`.
3. Documente le bundle dans le README (section « Plugins disponibles »).

### Règles

- Une **PR par bundle ou ensemble cohérent de thèmes** (ne mélange pas plusieurs bundles).
- Les noms de thème respectent l'attribution d'origine quand le thème est un port d'un schéma existant (Catppuccin, TokyoNight, etc.).
- Pas de thèmes light dans `ghostty-popular` — créer un bundle séparé `ghostty-popular-light` si besoin.
- Le mapping ANSI → tokens documenté ci-dessus doit rester cohérent au sein d'un bundle.

### Issues

Pour signaler un thème mal rendu (contraste faible sur un token particulier, couleur diff illisible), ouvre une issue avec une capture et le slug du thème.

## Source

Palettes extraites de l'API publique de [ghostty-style.vercel.app](https://ghostty-style.vercel.app), elle-même alimentée par [iTerm2-Color-Schemes](https://github.com/mbadolato/iTerm2-Color-Schemes). Crédits aux auteurs originaux des palettes.

## Licence

MIT.
