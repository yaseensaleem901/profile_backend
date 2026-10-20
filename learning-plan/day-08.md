# Day 08 — Register an account

[Previous day](day-07.md) · [Plan](../learning-plan.md) · [Next day](day-09.md)

**Goal:** Create an account without exposing a password.

- [ ] Learn: a password hash is a one-way stored verifier, not the original password; a unique email prevents duplicate accounts.
- [ ] Add account persistence, validated registration DTO, and `POST /v1/auth/register`. Return only safe fields; never log or return the hash.
- [ ] Predict malformed-email and duplicate-email outcomes. Test registration, rejection, and the absence of credentials in the response.

**Done when:** A valid account persists and unsafe inputs/duplicate email fail safely.
