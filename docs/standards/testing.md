# Testing

Source: [backend ADR-0017](https://github.com/jackson-rod/barras-backend/blob/develop/docs/adr/0017-definition-of-done.md). If they disagree, the ADR wins.

## Tools

- Jest with jest-expo and React Native Testing Library for `domain`, `application`, `infrastructure` and `ui`.
- Maestro for end-to-end flows.

## Tests per layer

A change is done only when the same pull request contains tests for every layer it touches (spec section 9, item 1):

- Domain types are tested directly.
- Use cases are tested with fake ports.
- Mappers round trip in both directions.
- Routes are tested through e2e against the real app.
- Every adapter to an outside system has a contract test.
- Errors are asserted by `code`, never by message.

## Coverage

**Call** (spec section 9).

- 95% of lines in `domain` and `application`.
- 85% overall.

A change is done only when `verify` is green locally and in CI.
