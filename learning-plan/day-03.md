# Day 03 — Connect PostgreSQL

[Previous day](day-02.md) · [Plan](../learning-plan.md) · [Next day](day-04.md)

**Goal:** Persist the first real data without putting secrets in code.

- [ ] Learn: PostgreSQL saves data across restarts; a migration is a versioned database change; an injectable database provider gives services access to it.
- [ ] Choose one migration-capable library together. Configure local and test databases, create only the category table with a unique slug, and document migration commands.
- [ ] Predict what happens if two categories use the same slug. Verify with a persistence test; explain how the DB protects the rule even if application validation is bypassed.

**Done when:** A clean setup can run the migration and the duplicate-key test passes.
