# Conventions TypeScript

## Typage strict

- `strict: true` obligatoire dans tsconfig
- Jamais de `any` — utiliser `unknown` si le type est réellement inconnu
- Types explicites sur les paramètres et retours de fonctions

## Choix de syntaxe

| Cas                   | Utiliser             | Exemple                                                                |
| --------------------- | -------------------- | ---------------------------------------------------------------------- |
| Objets/contrats       | `interface`          | `interface User { id: string }`                                        |
| Unions/intersections  | `type`               | `type Status = 'active' \| 'inactive'`                                 |
| Constantes            | `as const`           | `const ROLES = ['admin', 'user'] as const`                             |
| Discrimination d'état | Discriminated unions | `type State = { status: 'loading' } \| { status: 'success'; data: T }` |

## Utilitaires natifs à privilégier

- `Partial<T>`, `Required<T>` — optionalité
- `Pick<T, K>`, `Omit<T, K>` — sélection de propriétés
- `Record<K, V>` — dictionnaires typés
- `ReturnType<T>`, `Parameters<T>` — inférence de fonctions
- `Awaited<T>` — unwrap de Promises

## Type guards

```typescript
function isUser(value: unknown): value is User {
  return typeof value === "object" && value !== null && "id" in value;
}
```

## Éviter

- `// @ts-ignore` et `// @ts-expect-error` sans justification
- Types trop larges (`object`, `Function`)
- Assertions de type (`as`) sauf cas légitimes (ex: DOM)
