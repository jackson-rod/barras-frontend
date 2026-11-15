# Barras frontend docs

## What this repository is

`barras-frontend` is the Barras mobile app for iOS and Android: React Native with TypeScript, built with Expo. Barras shows people in Colombia who invest their money and the market in one place. The backend lives in `barras-backend` (Rust). The two repositories talk through the backend's `openapi.json`.

The app is organised as Expo Router routes in `app/` and features in `src/features/<feature>/`, each split into `domain`, `application`, `infrastructure` and `ui`. See [module anatomy](standards/module-anatomy.md). Everything in this repository is in English, except the app's own interface text, which is Spanish (es-CO) first and English second.

## How we work

1. A ticket starts with a spec in `docs/specs/BAR-<n>-<topic>.md`: intent, behaviour, routes, schema changes, error codes, tests.
2. The owner approves the spec.
3. An implementation plan is written from the spec.
4. The code is written test first, and `verify` passes.
5. The pull request updates the module README, the schema doc and any ADR it touches.

Standards: [code standard](standards/code-standard.md), [module anatomy](standards/module-anatomy.md), [performance](standards/performance.md), [testing](standards/testing.md). Decisions: [ADR index](adr/README.md).

## Product-wide docs

The plan, the schema and the contract ADRs live in `barras-backend`, in [docs](https://github.com/jackson-rod/barras-backend/tree/develop/docs):

- [Foundation design](https://github.com/jackson-rod/barras-backend/tree/develop/docs/specs)
- [Schema](https://github.com/jackson-rod/barras-backend/tree/develop/docs/schema)
- [ADR index](https://github.com/jackson-rod/barras-backend/tree/develop/docs/adr)
