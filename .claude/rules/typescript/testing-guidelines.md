# Guidelines de Test

## Principes

- **Tester le comportement**, pas l'implémentation
- **Éviter les tests fragiles** — ne pas tester le state interne
- **Mock uniquement les dépendances externes** (API, storage)

## Sélecteurs (Testing Library)

Ordre de priorité :

1. `getByRole` — accessibilité native
2. `getByLabelText` — formulaires
3. `getByPlaceholderText` — inputs
4. `getByText` — contenu textuel
5. `getByTestId` — dernier recours

## Structure d'un test

```typescript
describe('UserCard', () => {
  it('should display user name and trigger edit on button click', async () => {
    // Arrange
    const onEdit = vi.fn();
    render(<UserCard name="John" onEdit={onEdit} />);

    // Act
    await userEvent.click(screen.getByRole('button', { name: /edit/i }));

    // Assert
    expect(screen.getByText('John')).toBeInTheDocument();
    expect(onEdit).toHaveBeenCalledOnce();
  });
});
```

## Test doubles

- **Fake** — Implémentation simplifiée (in-memory repository)
- **Stub** — Retourne des valeurs prédéfinies
- **Mock** — Vérifie les appels (utiliser avec parcimonie)

## Coverage

- Viser **70%+** sur la logique métier critique (domain)
- Ne pas viser 100% — les tests superficiels ont peu de valeur
