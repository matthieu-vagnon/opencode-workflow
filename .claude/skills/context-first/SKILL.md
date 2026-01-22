---
name: context-first
description: Stratégie d'implémentation contextuelle, traite les fichiers fournis comme fondation immuable.
---

# Stratégie Context-First

Quand des fichiers sont fournis en contexte, traite-les comme la fondation autoritaire : types, classes, interfaces et structures existantes doivent être réutilisés tels quels.

## Workflow

1. **Analyser** — Lis attentivement les fichiers fournis, comprends l'architecture et les patterns existants
2. **Planifier** — Identifie les modifications nécessaires, demande des clarifications si besoin
3. **Implémenter** — Respecte strictement l'architecture, SOLID et KISS

## Règles strictes

| Règle                           | Description                                                                |
| ------------------------------- | -------------------------------------------------------------------------- |
| **Fichiers fournis uniquement** | Modifie SEULEMENT les fichiers explicitement fournis                       |
| **Pas de redéfinition**         | Ne recrée/duplique JAMAIS les types, classes ou interfaces existants       |
| **Pas de nouveaux fichiers**    | Demande confirmation explicite avant de créer un fichier                   |
| **Intégration > Expansion**     | Compose avec l'existant plutôt que d'introduire des structures parallèles  |
| **Blocage = Question**          | Si les contraintes bloquent, explique pourquoi et demande comment procéder |
