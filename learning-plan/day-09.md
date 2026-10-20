# Day 09 — Sign in and out

[Previous day](day-08.md) · [Plan](../learning-plan.md) · [Next day](day-10.md)

**Goal:** Establish and end a member's authenticated identity.

- [ ] Learn: authentication answers “who are you?” Compare revocable server-side cookie sessions with short-lived access/refresh tokens; decide how logout, browser storage, and CSRF protection will work.
- [ ] Implement login and logout for the agreed strategy; compare the submitted password to its stored hash without revealing which credential was wrong.
- [ ] Predict wrong-password and post-logout results; test them and a successful login. Keep passwords and tokens out of logs.

**Done when:** Login works and logout makes the chosen credential unusable according to the documented strategy.
