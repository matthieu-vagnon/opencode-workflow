# Architecture Hexagonale React

## Structure

```
src/
├── application/       # UI — Peut utiliser React librement
│   ├── components/    # Composants React
│   ├── hooks/         # Hooks métier (consomment le domaine)
│   ├── pages/         # Composants de route
│   └── providers/     # Context providers
├── domain/            # Métier — TypeScript pur, ZÉRO dépendance React
│   ├── entities/      # Modèles métier
│   ├── ports/         # Interfaces/contrats
│   └── lib/           # Fonctions pures
└── infrastructure/    # Externe — Implémente les ports
    ├── api/           # Clients HTTP/GraphQL
    └── config/        # Configuration, feature flags
```

## Règles par couche

### Domain (coeur)

- **Aucune** dépendance React (pas de JSX, pas de hooks)
- Fonctions pures, testables en isolation
- Définit les `ports` (interfaces) que l'infrastructure implémente

### Application (UI)

- Consomme le domaine via des hooks custom
- Composants découpés par responsabilité
- State management : `useState` → `useReducer` → Context → Zustand (escalade progressive)

### Infrastructure (adapters)

- Implémente les ports définis par le domaine
- Gère les side effects (API, storage, analytics)
- Transforme les réponses externes en entités domaine

## Principe de dépendance

```
Application → Domain ← Infrastructure
              ↑
         (ports/interfaces)
```

- Application et Infrastructure dépendent du Domain
- Domain ne dépend de rien d'externe
