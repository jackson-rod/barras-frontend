# ADR-0001: Record architecture decisions

Status: Accepted
Date: 2026-11-15

## Context

Barras is built by a small team with AI agents, across two repositories. Without a written record, decisions get re-debated and agents invent new patterns in single modules. The foundation design (section 10) fixes where documentation lives.

## Decision

Record every architecture decision as an ADR in `docs/adr/`, named `NNNN-title.md`, and list it in the index `docs/adr/README.md`. A new or changed decision is a new ADR in the same pull request. Do not delete old ADRs; supersede them with a new one.

## Consequences

Each decision costs a short document. The definition of done requires it, and the structure check enforces that ADRs appear in the index.
