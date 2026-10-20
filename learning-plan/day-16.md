# Day 16 — Professional offerings

[Previous day](day-15.md) · [Plan](../learning-plan.md) · [Next day](day-17.md)

**Goal:** Let professionals set their own hourly rate for a shared service.

- [ ] Learn: the `ProfessionalService` join record connects a profile and shared service; its fields hold the provider's hourly rate (minor units plus currency), description and any agreed availability.
- [ ] Add owner-only offering writes and safe public reads. Enforce unique (profile, service) in the database.
- [ ] Predict Yaseen offering `Web Development` at USD 10/hour and Abdullah at USD 15/hour. Test both public rates and a non-owner edit attempt; changing either rate must not change the shared service or the other's offering.

**Done when:** Shared service data is reused and one professional cannot modify another's offering.
