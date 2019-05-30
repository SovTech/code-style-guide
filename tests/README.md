# SovTech Test Guide

### Describe block

Wrap all tests in a describe block for the function or component. The text in the describe block should include the name of the function or component being tested.

```typescript
  describe('registerStakeholder()', () => {
```

### Test block

The name of the test block should state what is being *given* and what *should* be returned

```typescript
  test('given a valid cellNumber: should return a new guest stakeholder', async () => {
```
