# Day 05 — Read categories

[Previous day](day-04.md) · [Plan](../learning-plan.md) · [Next day](day-06.md)

**Goal:** Serve the category cards from real data.

- [ ] Learn: a feature module groups a controller and service; the service uses an injected persistence provider. Public reads need no authentication guard.
- [ ] Seed the eight categories in `USER_STORIES.MD` without duplicating them on reruns. Add `GET /v1/categories` showing active categories in a stable order.
- [ ] Predict whether an inactive category appears; verify with a request and test. Keep write routes closed until admin authorization on Day 11.

**Done when:** Changing active category data changes the API response without changing frontend code.
