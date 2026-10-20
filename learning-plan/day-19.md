# Day 19 — Basic discovery

[Previous day](day-18.md) · [Plan](../learning-plan.md) · [Next day](day-20.md)

**Goal:** Search the professionals who chose to be public.

- [ ] Learn: a query parameter such as `?query=designer` is optional search input; a path parameter identifies one resource. The service builds a safe DB filter.
- [ ] Add keyword search over agreed job-title/headline, skill, and industry fields for published profiles only.
- [ ] Predict results when the only keyword match is a draft profile; verify exclusion and a published match by HTTP test.

**Done when:** A visitor can search, and draft profiles cannot leak through the result list.
