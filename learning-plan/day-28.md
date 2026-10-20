# Day 28 — End-to-end and audit

[Previous day](day-27.md) · [Plan](../learning-plan.md) · [Next day](day-29.md)

**Goal:** Verify connected journeys rather than isolated methods.

- [ ] Learn: e2e tests exercise HTTP → guard → pipe → controller → service → DB; a framework log helps debugging, while a business audit trail records who made a significant change.
- [ ] Test member, professional, and admin journeys, including bad input, forbidden edits, duplicates, and logout. Add only the audit events required by agreed publication/moderation policy.
- [ ] Predict one unauthorized action and, if auditing applies, its expected audit event; verify the actual behavior.

**Done when:** The journeys pass and we can explain what is logged for debugging versus accountability.
