# Daily learning index (30 focused sessions)

Use [USER_STORIES.MD](../USER_STORIES.MD) for business requirements and [the main plan](../learning-plan.md) for pacing. The linked `day-XX.md` file is the source of truth for each lesson and its completion check. The short checkboxes below are an optional combined overview; keep progress in the day file and main plan. None of these feature steps has been completed yet.

## [Day 01 — First request](day-01.md)

- [ ] Learn: HTTP request/response, `@Controller`, `@Get`, `@Injectable`, `@Module` and constructor injection using `src/main.ts`, `src/app.module.ts`, `src/app.controller.ts`, `src/app.service.ts`.
- [ ] Predict what `GET /` returns; run the starter test/request and draw `GET /` → controller → service → response (no guard, pipe or DB yet). Explain each file in your own words.

## [Day 02 — Design the relationships](day-02.md)

- [ ] Learn: table, row, primary/foreign key, unique constraint, one-to-many and join table. Sketch Account/Profile, Profile/Project, shared Service/Offering, Review, Collection/Item and Blog relationships.
- [ ] Sketch one shared `Web Development` service and two offerings: Yaseen at USD 10/hour and Abdullah at USD 15/hour. Record category versus industry and deletion/visibility questions in `USER_STORIES.MD`; review the diagram before creating tables.

## [Day 03 — Connect PostgreSQL](day-03.md)

- [ ] Learn: database provider/repository, dependency injection and versioned migration. Choose one migration-capable library, configure a local/test DB without committing secrets, migrate just the category table.
- [ ] Predict what a duplicate slug does; verify with a database test. Document setup/migration commands.

## [Day 04 — Validate input](day-04.md)

- [ ] Learn: DTO (the accepted request shape) and `ValidationPipe` (checks data before the controller uses it). Define length/slug rules for a future category write route and test the pipe directly; do not expose an unprotected write route.
- [ ] Predict bad slug and extra field results; test rejection. Compare DTO validation with the database's unique constraint.

## [Day 05 — Read categories](day-05.md)

- [ ] Learn: a feature module groups controller and service; injection lets a service use the database provider. Seed the eight proposed categories idempotently and expose only active categories via `GET /v1/categories`.
- [ ] Predict whether inactive categories appear; verify public read and stable order. Keep category writes closed until Day 11.

## [Day 06 — Errors and first tests](day-06.md)

- [ ] Learn: HTTP exceptions (`400`, `404`, `409`) and unit versus HTTP/e2e tests. Map bad input and duplicate slug to helpful, safe responses.
- [ ] Predict duplicate category slug and invalid input responses; test the service's safe conflict mapping and that invalid data cannot be saved.

## [Day 07 — Review and refactor](day-07.md)

- [ ] Without looking at notes, trace a category request through route → validation (if any) → service → DB → response. Explain why public reads have no auth guard.
- [ ] Run build/lint/tests; fix one confusing name or small test gap. Ask questions before Week 2.

## [Day 08 — Register an account](day-08.md)

- [ ] Learn: account entity, DTO validation, password hashing and unique email. Implement `POST /v1/auth/register` returning only safe account fields.
- [ ] Predict malformed email and duplicate registration results; test both and verify password hashes never appear in responses/logs.

## [Day 09 — Sign in and out](day-09.md)

- [ ] Learn: authentication proves identity; compare secure server-side cookie sessions with short-lived access/refresh tokens. Choose one and document revocation, browser storage and CSRF implications.
- [ ] Implement login/logout for the chosen approach; predict wrong-password and logged-out behavior, then test. Never store plaintext passwords.

## [Day 10 — Protect GET /me](day-10.md)

- [ ] Learn: a guard runs before a protected route and determines whether the request has a valid identity. Implement `GET /v1/me` behind authentication.
- [ ] Predict anonymous versus signed-in responses; test `401` and safe output. Trace controller → guard → service → account persistence.

## [Day 11 — Ownership and admin](day-11.md)

- [ ] Learn: authorization asks *may this identity do this action?* Introduce an explicit admin policy; protect category create/update/deactivate, and plan a reusable owner lookup for upcoming profile writes.
- [ ] Predict a member changing a category; test forbidden edit and successful admin edit. Never accept a self-declared admin flag from the client.

## [Day 12 — Save a profile draft](day-12.md)

- [ ] Learn: one-to-one relation, DTO field validation and unique public slug. Agree mandatory fields, location/industry/skills and website/contact policy before implementing owner-only draft create/edit.
- [ ] Predict a second profile for the same account and an invalid website URL; test both and a valid private draft.

## [Day 13 — Publish and read a profile](day-13.md)

- [ ] Learn: publication is a business rule in the service; the DB stores state, and public responses select safe fields. Add explicit publish/unpublish and public slug detail.
- [ ] Agree opt-in indexing and publication criteria; predict anonymous reads of a draft, published profile and newly unpublished profile; test `404` for hidden ones.

## [Day 14 — Review access boundaries](day-14.md)

- [ ] Learn: `401` = unauthenticated, `403` = not permitted, `404` can hide unavailable public content, `409` = conflicting data. Verify profile reads/writes as visitor, owner, another member and admin.
- [ ] Predict one cross-account edit before running the e2e test; fix any leak. Trace the full guarded request aloud.

## [Day 15 — Shared service catalog](day-15.md)

- [ ] Learn: taxonomy is shared data. Confirm whether a service belongs to one or multiple categories, then implement admin-controlled service types and public active list.
- [ ] Predict duplicate slug or deactivated service visibility; test; keep industry separate from category.

## [Day 16 — Professional offerings](day-16.md)

- [ ] Learn: a join record `ProfessionalService` stores per-professional offering details; unique (profile, service) blocks duplicates.
- [ ] Add owner-only offering write and public read; verify Yaseen's USD 10/hour and Abdullah's USD 15/hour offerings for the same service, and reject unauthorized rate edits.

## [Day 17 — Create portfolio work](day-17.md)

- [ ] Learn: one professional owns many projects. Create one project at a time with DTO validation, owner lookup and project link/media metadata.
- [ ] Predict a non-owner edit or invalid URL; test denial. Keep a new project private until publication is requested.

## [Day 18 — Public project visibility](day-18.md)

- [ ] Learn: a parent profile and its project can each have publication state; public queries must filter both. Add owner edit/unpublish and published project read.
- [ ] Predict whether a published project under a draft profile is visible; test it is not. Agree deleted/unpublished saved-project behavior for Day 24.

## [Day 19 — Basic discovery](day-19.md)

- [ ] Learn: query parameters versus path parameters and filtering in the persistence query. Search published profiles by keyword in agreed headline/skill/industry fields.
- [ ] Predict results when a matching profile is a draft; test exclusion and a real match.

## [Day 20 — Filter and paginate](day-20.md)

- [ ] Learn: query DTO validation, pagination, stable sorting and database indexes. Add combinable city/state and category filters, bounded page size and deterministic ordering.
- [ ] Predict combined-filter results and unsupported sort; test. Measure representative DB query time rather than promise a fixed speed.

## [Day 21 — Home feed and review](day-21.md)

- [ ] Agree manual featured selection versus a documented deterministic rule. Return up to six eligible published professionals plus active categories via existing public routes (or a thin home route only if useful).
- [ ] Predict whether an unpublished featured profile can appear; test exclusion. Run Week 3 regression tests and explain discovery's request path.

## [Day 22 — Read trustworthy reviews](day-22.md)

- [ ] Learn: a review belongs to an author and target profile; moderation controls public visibility. Decide eligibility with the product owner; until agreed, implement approved-only read endpoints, not open submissions. Use only clearly labeled test fixtures, never invented production testimonials.
- [ ] Predict whether pending reviews or reviews for draft profiles appear on a profile/home page; test neither appears. Never present invented testimonials as real.

## [Day 23 — Private collections](day-23.md)

- [ ] Learn: authentication guard identifies the member; ownership checks restrict which collection they can read/edit. Implement create/list/rename/delete private named collections.
- [ ] Predict member A reading member B's collection; test denial and own access.

## [Day 24 — Save projects](day-24.md)

- [ ] Learn: `CollectionItem` join table and unique (collection, project). Add/remove a public project in a member-owned collection; implement the agreed behavior for unpublished/deleted projects.
- [ ] Predict duplicate save and cross-member save results; test both. Profiles/services are not implicit collection items.

## [Day 25 — Publish blogs](day-25.md)

- [ ] Learn: editor/admin guard and draft/published state. Implement draft create/edit/publish, public paginated summary and slug detail; choose safe content handling before rendering HTML.
- [ ] Predict visitor reads of a draft and duplicate blog slug; test both.

## [Day 26 — Complete the home data](day-26.md)

- [ ] Return three published blog summaries and approved public testimonials using the public endpoints or a thin aggregation service; respect each feature's visibility policy.
- [ ] Predict what the home page receives if only two eligible blogs or zero approved reviews exist; test empty/short results without fabricated content.

## [Day 27 — Security basics](day-27.md)

- [ ] Learn: rate limiting/throttling, CORS origin rules, environment secrets, safe response DTOs and CSRF protection if using cookies. Apply safeguards to auth and write routes.
- [ ] Predict one accidental private-field or draft leak; verify the response is safe. Avoid logging passwords/tokens.

## [Day 28 — End-to-end and audit](day-28.md)

- [ ] Walk through a real member/professional/admin journey with HTTP/e2e tests, including validation errors, forbidden edits, DB uniqueness and logout.
- [ ] Distinguish Nest's diagnostic logger from a business audit event recording who published/unpublished or moderated a record; implement minimal audit only if needed by agreed policy. Predict an audit entry, then verify.

## [Day 29 — Runbook and deployment preparation](day-29.md)

- [ ] Document required environment variables, DB migration/backup/restore commands, secure initial admin setup and production start steps. Test a clean local setup; deployment is optional if no target is chosen.
- [ ] Predict a failed migration or unpublish effect; rehearse recovery. Keep frontend SEO/sitemap and visual performance ownership explicit.

## [Day 30 — Demo and knowledge check](day-30.md)

- [ ] Demo: register → sign in → draft/publish profile → add offering/project → search → save project → view approved reviews and blogs → sign out.
- [ ] Run build/lint/unit/e2e tests, list known limitations and deferred decisions. Explain one request end-to-end without prompts; update both checklists only for genuinely verified work.
