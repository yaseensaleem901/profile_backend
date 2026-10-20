# Day 13 — Publish and read a profile

[Previous day](day-12.md) · [Plan](../learning-plan.md) · [Next day](day-14.md)

**Goal:** Make a completed profile visible only when its owner chooses to publish.

- [ ] Learn: the service enforces publishability; the database records published/draft state; the public response includes only safe profile fields.
- [ ] Agree mandatory fields and search-engine opt-in. Add explicit publish/unpublish plus public detail by slug.
- [ ] Predict anonymous reads of a draft, published profile, and just-unpublished profile; test that hidden profiles return `404`.

**Done when:** A visitor sees a published profile but cannot read its draft or private account data.
