# Module anatomy

Source: [ADR-0002](../adr/0002-frontend-stack-and-feature-anatomy.md). Change the ADR and this file in the same pull request; if they disagree, the ADR wins.

Where this standard and `code-standard.md` disagree on structure or naming, this one wins.

## Layout

```
app/                     Expo Router routes only: thin screens that compose features
src/
  core/                  the core contract: API client (envelope, errors by code), session, realtime client,
                         configuration schema, i18n, theme, query client, storage
  features/<feature>/    kebab-case
    README.md
    domain/              types and pure functions; no React, no IO
    application/         use-case hooks that orchestrate ports; query keys
    infrastructure/      API adapters and mappers (DTO to domain and back), realtime subscriptions, device APIs
    ui/                  components
    index.ts             the feature's public surface
  shared/ui/             design-system primitives
  generated/             types generated from the backend's openapi.json
locales/                 es.json, en.json
```

## Features

`auth`, `onboarding`, `home`, `trends`, `news`, `capital`, `budgets`, `goals`, `profile`, `settings`, `billing`, `assistant`.

## Imports

| Layer | May import from |
| --- | --- |
| `domain` | itself and pure libraries |
| `application` | its feature's `domain`, and `src/core` |
| `infrastructure` | its feature's `domain`, `src/core`, `src/generated` |
| `ui` | its feature's `application` and `domain`, `src/shared/ui`, `src/core` |
| `app/` routes | a feature's `index.ts` only |
| another feature | only its `index.ts` |
| `src/core` | nothing in `features` |

dependency-cruiser enforces this (`bun run check:arch`), running on TypeScript 6.
