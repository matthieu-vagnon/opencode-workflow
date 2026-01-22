# Patterns de Composants React

## Règles fondamentales

- Composants fonctionnels uniquement
- Props destructurées dans la signature
- Un fichier = un composant exporté (+ helpers privés si nécessaire)
- Taille max recommandée : ~150 lignes

## Patterns

### Presentational vs Container

```typescript
// Presentational — UI pure, aucune logique métier
function UserCard({ name, avatar, onEdit }: UserCardProps) {
  return (/* JSX */);
}

// Container — Connecte au domaine via hooks
function UserCardContainer({ userId }: { userId: string }) {
  const { user, updateUser } = useUser(userId);
  return <UserCard {...user} onEdit={updateUser} />;
}
```

### Compound Components

Pour des composants liés qui partagent un état implicite :

```typescript
<Tabs defaultValue="tab1">
  <Tabs.List>
    <Tabs.Trigger value="tab1">Tab 1</Tabs.Trigger>
  </Tabs.List>
  <Tabs.Content value="tab1">Content</Tabs.Content>
</Tabs>
```

## Props

- Préférer les unions aux booléens : `variant: 'primary' | 'secondary'` plutôt que `isPrimary`
- `children` pour la composition
- Defaults via destructuring : `{ size = 'md' }`

## Performance (mesurer avant d'optimiser)

| Outil         | Quand                                               |
| ------------- | --------------------------------------------------- |
| `React.memo`  | Composant re-rendu souvent avec mêmes props         |
| `useMemo`     | Calcul coûteux dans le render                       |
| `useCallback` | Référence stable pour les callbacks passés en props |
| `React.lazy`  | Code splitting par route/feature                    |

## Hooks

- Préfixe `use` obligatoire
- Appels au top-level uniquement (pas dans conditions/boucles)
- Extraire la logique complexe en hooks custom
