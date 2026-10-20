# Day 04 — Validate input

[Previous day](day-03.md) · [Plan](../learning-plan.md) · [Next day](day-05.md)

**Goal:** Reject bad input before it reaches business code.

- [ ] Learn: a DTO describes accepted input; a `ValidationPipe` checks it before the controller handler runs. This differs from a database constraint, which protects saved data.
- [ ] Define name/slug rules for future category writes. Test the pipe directly; do not expose an unprotected write route before admin authorization exists.
- [ ] Predict results for a bad slug and an extra field, then test them. Compare these failures to a duplicate slug at the DB layer.

**Done when:** Invalid input fails validation and we can explain where the failure happens in a request.
