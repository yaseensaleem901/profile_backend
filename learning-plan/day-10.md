# Day 10 — Protect GET /me

[Previous day](day-09.md) · [Plan](../learning-plan.md) · [Next day](day-11.md)

**Goal:** Read only the currently signed-in member's safe account fields.

- [ ] Learn: an authentication guard runs before route pipes and the controller handler; it rejects requests without valid identity.
- [ ] Add guarded `GET /v1/me`. Trace route → guard → controller → service → account persistence → safe response.
- [ ] Predict anonymous, valid, and logged-out responses. Test `401` for invalid identity and verify password hashes never appear.

**Done when:** Only a valid authenticated member can retrieve their own safe data.
