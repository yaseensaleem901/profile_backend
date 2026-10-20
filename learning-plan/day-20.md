# Day 20 — Filter and paginate

[Previous day](day-19.md) · [Plan](../learning-plan.md) · [Next day](day-21.md)

**Goal:** Keep discovery predictable as results grow.

- [ ] Learn: pagination returns one bounded page; stable sorting prevents records jumping between pages; indexes help the DB find matching rows.
- [ ] Validate query input. Combine keyword, city/state, and category filters with a bounded page size and allowlisted sort.
- [ ] Predict combined-filter and unsupported-sort results; test both. Measure a representative query rather than promise an unmeasured speed.

**Done when:** Public results are filtered, ordered, paginated, and limited to published profiles.
