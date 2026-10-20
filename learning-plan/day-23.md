# Day 23 — Private collections

[Previous day](day-22.md) · [Plan](../learning-plan.md) · [Next day](day-24.md)

**Goal:** Let a member organize private named lists.

- [ ] Learn: an auth guard identifies the caller, while a service ownership check ensures a specific collection belongs to that caller.
- [ ] Add create/list/rename/delete for the signed-in member's collections, with validated names; do not expose other members' lists.
- [ ] Predict member A reading or renaming member B's collection; test denial and a successful owner action.

**Done when:** Each member sees only their own collections and can rename one.
