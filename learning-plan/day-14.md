# Day 14 — Review access boundaries

[Previous day](day-13.md) · [Plan](../learning-plan.md) · [Next day](day-15.md)

**Goal:** Verify profile permissions from four perspectives.

- [ ] Learn: `401` means no valid identity, `403` means authenticated but not allowed, `404` can conceal a non-public profile, and `409` signals a conflict.
- [ ] Test profile create/edit/publish/read as a visitor, owner, other member, and admin. Trace route → guard → pipe → controller → service ownership check → DB.
- [ ] Predict whether member A can edit member B's profile before running the e2e test; investigate any cross-account leak.

**Done when:** The allowed and denied cases have tests and you can explain their different statuses.
