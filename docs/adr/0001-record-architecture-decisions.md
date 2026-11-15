# ADR-0001: Record architecture decisions

Status: Accepted
Date: 2026-11-15

## Context

Barras is built by a small team with AI agents, across two repositories. Without a written record, decisions get re-debated and agents invent new patterns in single modules. The foundation design (section 10) fixes where documentation lives. The statuses and the supersede rule below are a **Call** of the designer, taken from the structure check in the BAR-2 plan, not confirmed by the owner.

## Decision

Record every architecture decision as an ADR in `docs/adr/`, named `NNNN-title.md`, and list it in the index `docs/adr/README.md`. A new or changed decision is an ADR, listed in the index.

The statuses are `Proposed`, `Accepted` and `Superseded by ADR-NNNN`. A new ADR is `Proposed` until the owner accepts it. A decision is changed by a new ADR: the ADR it replaces gets the status `Superseded by ADR-NNNN` and its Decision is not rewritten.

## Consequences

Each decision costs a short document. The definition of done requires it.
