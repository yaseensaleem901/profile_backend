# Day 27 — Security basics

[Previous day](day-26.md) · [Plan](../learning-plan.md) · [Next day](day-28.md)

**Goal:** Check common ways an otherwise working API could expose users.

- [ ] Learn: throttling limits repeated login attempts; CORS controls which browser origins may call the API; environment variables keep secrets out of source; CSRF matters for cookie-authenticated writes.
- [ ] Apply safeguards appropriate to the chosen auth approach, validate external URLs, and return only safe DTO fields.
- [ ] Predict one possible draft or secret leak; test that the response and framework logs do not reveal it.

**Done when:** Auth/write boundaries are tested and secrets, drafts, and private collections remain private.
