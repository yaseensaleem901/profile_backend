# Day 06 — Errors and first tests

[Previous day](day-05.md) · [Plan](../learning-plan.md) · [Next day](day-07.md)

**Goal:** Make failures understandable without leaking internal details.

- [ ] Learn: HTTP `400` means bad input, `404` missing resource, and `409` conflict. Unit tests isolate a class; e2e tests send HTTP requests through Nest.
- [ ] Map a category duplicate-slug failure to a safe conflict response; test invalid category input and the public category read.
- [ ] Predict both failure responses before running tests. Explain which check belongs to the pipe, service, or database.

**Done when:** Good requests and rejected inputs are covered by tests and no raw database error is returned to callers.
