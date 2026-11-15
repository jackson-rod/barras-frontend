# Architecture decision records

An ADR records one decision: the forces behind it, the rule, and what it costs. An ADR outranks `CLAUDE.md`. If an area has no ADR, stop and ask, or propose one; do not invent a new pattern in one module. To add one, copy the shape of an existing ADR, take the next number, name the file `NNNN-title.md`, and add a row to the table below in the same pull request.

The statuses are `Proposed`, `Accepted` and `Superseded by ADR-NNNN` (a **Call**, see ADR-0001). A new ADR is `Proposed` until the owner accepts it. A decision is changed by a new ADR: the ADR it replaces gets the status `Superseded by ADR-NNNN` and its Decision is not rewritten.

| ADR | Title | Status |
| --- | --- | --- |
| [0001](0001-record-architecture-decisions.md) | Record architecture decisions | Accepted |
| [0002](0002-frontend-stack-and-feature-anatomy.md) | Frontend stack and feature anatomy | Accepted |
| [0003](0003-backend-openapi-is-the-contract.md) | Backend OpenAPI is the contract | Accepted |
