---
name: readme
description: Génère ou met à jour le README.md du projet en analysant la structure et les fichiers de configuration.
argument-hint: "[create|update]"
---

# Skill README Generator

Génère ou met à jour le fichier `README.md` à la racine du projet.

## Workflow

1. **Analyser le projet**
   - Lire `package.json` (ou équivalent) pour les métadonnées
   - Lire `.claude/CLAUDE.md` et `.claude/rules/` pour comprendre le contexte
   - Scanner la structure des dossiers (`src/`, `lib/`, `app/`, etc.)
   - Identifier le stack technique utilisé

2. **Collecter les informations existantes**
   - Si `README.md` existe : le lire pour préserver le contenu personnalisé
   - Identifier les sections à conserver vs régénérer

3. **Générer le contenu**
   - Suivre la structure ci-dessous
   - Utiliser un ton professionnel et concis
   - Pas d'emojis sauf si demandé explicitement

## Structure du README

```markdown
# Nom du Projet

Description courte et percutante (1-2 phrases).

## Features

- Feature 1
- Feature 2

## Tech Stack

| Catégorie | Technologies |
| --------- | ------------ |
| Frontend  | ...          |
| Backend   | ...          |

## Getting Started

### Prerequisites

- Node.js >= X.X
- pnpm/npm

### Installation

\`\`\`bash
pnpm install
\`\`\`

### Development

\`\`\`bash
pnpm dev
\`\`\`

## Project Structure

\`\`\`
src/
├── ...
\`\`\`

## Scripts

| Script | Description |
| ------ | ----------- |
| `dev`  | ...         |

## License

MIT (ou autre)
```

## Règles

- **Ne jamais inventer** de fonctionnalités non présentes dans le code
- **Préserver** les sections personnalisées existantes (Contributing, Acknowledgments, etc.)
- **Adapter** la structure selon le type de projet (lib, app, monorepo)
- Si `$ARGUMENTS` = "create" : générer un nouveau README
- Si `$ARGUMENTS` = "update" : mettre à jour en préservant le contenu existant
- Sans argument : détecter automatiquement (update si existe, create sinon)
