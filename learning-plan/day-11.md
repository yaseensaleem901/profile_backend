# Day 11 — Ownership and admin

[Previous day](day-10.md) · [Plan](../learning-plan.md) · [Next day](day-12.md)

**Goal:** Separate “signed in” from “allowed to change this.”

- [ ] Learn: authorization is a permission check; admin status comes from trusted account data, never a client-submitted flag. Resource ownership is checked against saved owner IDs.
- [ ] Agree how the first admin is created securely. Protect category create/update/deactivate; outline a reusable owner lookup for profile writes.
- [ ] Predict a regular member's category edit and an admin's edit; test forbidden and allowed results.

**Done when:** A normal member cannot alter the catalog but an authorized admin can.
