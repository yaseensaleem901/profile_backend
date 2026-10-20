# Day 24 — Save projects

[Previous day](day-23.md) · [Plan](../learning-plan.md) · [Next day](day-25.md)

**Goal:** Save a professional's work into a member-owned collection.

- [ ] Learn: `CollectionItem` joins a collection and project; unique (collection, project) prevents duplicate saves while allowing one project in different collections.
- [ ] Implement add/remove for a visible project, checking collection ownership and agreed unpublished/deleted-project behavior.
- [ ] Predict duplicate and cross-member saves; test them. Do not silently add profile/service saving to scope.

**Done when:** A member can save one project into two private collections but not twice into the same one.
