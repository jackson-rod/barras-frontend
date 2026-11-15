# ADR-0003: Backend OpenAPI is the contract

Status: Accepted
Date: 2026-11-15

## Context

The backend generates `openapi.json` with utoipa and commits it. It is the contract between the two repositories, including realtime event names and payloads (foundation design, section 6.7). The server is the only authority on what a user may use; an anti-goal is Pro unlocked by the app alone (sections 2 and 7.3).

## Decision

- Vendor the backend's `openapi.json` at `api/openapi.json`, at a pinned version.
- Produce the types in `src/generated/` with `bun run api:generate`. Do not edit them by hand.
- The app never decides entitlements. It reads them from the session.

## Consequences

Updating the contract means vendoring a new `openapi.json` and regenerating types in the same change. CI fails when the generated types are stale.
