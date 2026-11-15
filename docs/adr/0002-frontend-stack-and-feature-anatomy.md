# ADR-0002: Frontend stack and feature anatomy

Status: Accepted
Date: 2026-11-15

## Context

Performance is the most important quality, including the compile and feedback loop. For the frontend the foundation design (section 5) finds one sensible way: Expo SDK 58 (React Native 0.88, Hermes V1, New Architecture, React Compiler on). Re.Pack with Rspack does not properly support Expo today and would cost Expo Router and EAS builds. The stack choices in section 7.1 are marked as **Calls**: the designer made them and the owner has not confirmed them. The chart library is open until spike F-11.

## Decision

- Use Expo SDK 58 with Expo Router, development builds and EAS. Keep React Compiler on.
- Use TypeScript strict with `noUncheckedIndexedAccess`. TypeScript 6 stays installed for Expo's tooling; TypeScript 7 runs the typecheck.
- Use oxlint (type-aware) and oxfmt, with bun as package manager and script runner.
- Use TanStack Query for server state, persisted to MMKV so Home paints from cache on a cold start. Realtime events patch or invalidate that cache. Use Zustand for the little client state. Keep tokens in expo-secure-store.
- Use Unistyles 3, FlashList, Reanimated, i18next with expo-localization, and react-hook-form with zod.
- Draw charts with a Skia candlestick chart. Choose the library in spike F-11; writing our own on Skia is the fallback.
- Use RevenueCat (`react-native-purchases`) for subscriptions.
- Test with Jest, jest-expo and React Native Testing Library, and Maestro for end-to-end flows.
- Lay out code as in `docs/standards/module-anatomy.md`: routes in `app/` only compose features; each feature in `src/features/<feature>/` has `domain`, `application`, `infrastructure`, `ui` and an `index.ts` public surface, with the import table of that standard.

## Consequences

The stack depends on recent releases, and Expo pins TypeScript 6 while the typecheck uses TypeScript 7. The import rules are enforced by dependency-cruiser (`bun run check:arch`), running on TypeScript 6. Coverage and budgets are in `docs/standards/testing.md` and `docs/standards/performance.md`.
