---
name: ts-test-writing
description: Implement tests in TypeScript.
---

# Testing Guidelines

## Principles

- **Test behavior**, not implementation
- **Avoid brittle tests** — do not test internal state
- **Mock only external dependencies** (API, storage)

## Selectors (Testing Library)

Priority order:

1. `getByRole` — native accessibility
2. `getByLabelText` — forms
3. `getByPlaceholderText` — inputs
4. `getByText` — text content
5. `getByTestId` — last resort

## Test Structure

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

## Test Doubles

- **Fake** — Simplified implementation (in-memory repository)
- **Stub** — Returns predefined values
- **Mock** — Verifies calls (use sparingly)

## Coverage

- Target **70%+** on critical business logic (domain)
- Do not aim for 100% — superficial tests have little value
