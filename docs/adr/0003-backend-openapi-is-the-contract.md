# ADR-0003: Backend OpenAPI is the contract

Status: Accepted
Date: 2026-11-15

## Context

The backend generates `openapi.json` with utoipa and commits it. It is the contract between the two repositories, including realtime event names and payloads (foundation design, section 6.7). The server is the only authority on what a user may use; an anti-goal is Pro unlocked by the app alone (sections 2 and 7.3).

## Decision

The contract itself is decided in the backend repository, in [backend ADR-0002](https://github.com/jackson-rod/barras-backend/blob/develop/docs/adr/0002-two-repositories-openapi-contract.md) and, for the response envelope, [backend ADR-0005](https://github.com/jackson-rod/barras-backend/blob/develop/docs/adr/0005-http-contract.md). This ADR records only how the app consumes it.

- Vendor the backend's `openapi.json` at `api/openapi.json`, at a pinned version.
- Produce the types in `src/generated/` with `bun run api:generate`. Do not edit them by hand.
- The app never decides entitlements. It reads them from the session.

## Consequences

Updating the contract means vendoring a new `openapi.json` and regenerating types in the same change. CI fails when the generated types are stale.
