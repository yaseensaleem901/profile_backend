# Day 12 — Save a profile draft

[Previous day](day-11.md) · [Plan](../learning-plan.md) · [Next day](day-13.md)

**Goal:** Give a professional one private, editable profile.

- [ ] Learn: a one-to-one relationship allows at most one profile per account; a public slug is a unique URL-friendly name. DTOs validate input; DB constraints enforce uniqueness.
- [ ] Agree required profile fields, location/industry/skills, and the contact link in `USER_STORIES.MD`. Add owner-only draft create/edit with validated URLs.
- [ ] Predict a second profile for one account and an invalid website URL. Test both rejections and a valid draft.

**Done when:** Its owner can save a draft and other members cannot edit it.
