# Profile Links — 30-day beginner NestJS plan

Status: planning only. No feature APIs, PostgreSQL schema or auth implementation yet. The repository currently contains the default NestJS starter controller/service and Vitest tests. [USER_STORIES.MD](USER_STORIES.MD) is the working business specification; [the day index](learning-plan/daily-checklist.md) links to one lesson file per day.

## What we are building

A PostgreSQL-backed, versioned NestJS API for public profiles and discovery, with authenticated profile/project/service management, curated categories, professional reviews, private collections, published blogs and a small home-page feed. Keep the learning project incremental: each day should finish with one observable behavior and a test (or, on design days, a reviewed diagram/decision). Build real-user safeguards into the slices rather than adding them at the end.

### Proposed module boundaries (not generated yet)

- `Auth` / `Accounts`: registration, sign-in, sign-out, session lifecycle, account identity and role/ownership checks.
- `Professionals`: public/private profiles, links, publication and featured state.
- `Categories` / `Services`: admin-curated category/service catalog and professional-specific offerings. One shared `Web Development` service can have Yaseen's USD 10/hour offering and Abdullah's USD 15/hour offering.
- `Projects`: work owned by one professional.
- `Discovery`: combined search filters and pagination over published records.
- `Reviews`: professional-targeted reviews with author and moderation status.
- `Collections`: private lists and project saves.
- `Blogs`: draft/published editorial posts.
- `Home`: read-only assembly of categories, up to six featured professionals, approved reviews and up to three published blogs; start with existing module services and introduce an aggregator only if it improves clarity.

Prefer one Nest app and one PostgreSQL database initially. Pick and document a single migration-capable database library before Day 3 (Prisma, TypeORM, or another appropriate option); this is a learning decision, not an installed dependency. Keep unique slugs, foreign keys, join-table uniqueness and useful search indexes in the database as well as validating requests.

## How a request will move through NestJS

For an authenticated write such as adding a project: HTTP request → route match → authentication guard (who is signed in) → DTO and `ValidationPipe` (shape, field lengths and URL rules) → controller handler → service ownership/policy check (may they edit *this* professional?) and business rules → persistence transaction/repository (project and relationships) → response DTO. Nest guards run **before** route pipes; do not assume a guard sees already-validated DTO input. A public search skips the auth guard but still validates query parameters and returns only published profiles. Expect errors to be translated to consistent `400`, `401`, `403`, `404` or `409` responses. Verify both successful and denied requests with tests.

Controllers express HTTP contracts; DTOs/pipes reject bad input at the edge; guards/policies enforce identity and access; services enforce domain rules; persistence protects relational invariants. Framework logs help diagnose requests and failures; a business audit trail, if added for profile publication/review moderation, records *who changed what and when*. They are not interchangeable, and secrets/credentials never belong in either log.

## Suggested API surface (illustrative, not a locked contract)

- `POST /v1/auth/register`, `POST /v1/auth/login`, `POST /v1/auth/logout`, `GET /v1/me`.
- `GET /v1/categories`, `GET /v1/services`, `GET /v1/professionals?query=&industry=&city=&state=&category=&page=`.
- `GET /v1/professionals/:slug`, authenticated profile create/update/publish routes; nested service-offering and project write routes scoped to the owner.
- `GET /v1/professionals/:slug/reviews`; review submission route only after eligibility policy is settled.
- `GET/POST /v1/me/collections`, collection item add/remove endpoints scoped to the signed-in owner.
- `GET /v1/blogs`, `GET /v1/blogs/:slug`; protected editorial write/publish routes.
- `GET /v1/home` only if one aggregated request improves frontend loading; otherwise use the public endpoints above.

Use stable IDs internally and slugs for public URLs; paginate lists, whitelist sort/filter inputs, and return only safe public fields. The frontend owns hero images, card transitions, testimonials animation and FAQ layout. Search/indexing performance is a measurement goal, not a promise of a 200 ms response before real data exists; frontend LCP/CLS targets cannot be guaranteed by the API alone.

## Pace and teaching contract

Thirty focused sessions over roughly one month, aiming for 60–90 minutes each. A few design/review days prevent piling up unfinished features; some days may need more time if the database or environment is unfamiliar. Trim optional polish before rushing through security or tests. Each linked day file has its own checklist, not a requirement to build a whole module in one sitting.

For **each** day: start with a plain-English definition and one small example; point to the current file and show where an HTTP request travels (route → guard if protected → validation/pipe → controller handler → service → database → response); ask for a prediction; implement one slice together; run a request and a test; explain *why* it behaved that way. A controller receives HTTP input, a service holds business rules, a module connects them via dependency injection, and a DTO describes input. We will introduce guards, interceptors and exception filters only when a real need appears. Framework logs are for debugging; a business audit trail is a separate record of who made a significant change.

## Week 1 — Learn the skeleton and the data boundary

- [ ] [Day 01 — First request](learning-plan/day-01.md): controller, service, module; trace and test the starter `GET /`.
- [ ] [Day 02 — Design the relationships](learning-plan/day-02.md): tables, foreign keys, one-to-many and join tables; sketch only.
- [ ] [Day 03 — Connect PostgreSQL](learning-plan/day-03.md): database provider and migration; create one small table.
- [ ] [Day 04 — Validate input](learning-plan/day-04.md): DTO and `ValidationPipe`; reject malformed requests.
- [ ] [Day 05 — Read categories](learning-plan/day-05.md): modules, injected providers and public reads; serve active categories.
- [ ] [Day 06 — Errors and first tests](learning-plan/day-06.md): HTTP exceptions and unit/e2e tests; verify bad and good requests.
- [ ] [Day 07 — Review and refactor](learning-plan/day-07.md): retrace a request independently; close Week 1 gaps.

## Week 2 — Identity and publishable profiles

- [ ] [Day 08 — Register an account](learning-plan/day-08.md): account model, password hashing and unique email.
- [ ] [Day 09 — Sign in and out](learning-plan/day-09.md): choose session/token strategy; implement login/logout safely.
- [ ] [Day 10 — Protect `GET /me`](learning-plan/day-10.md): authentication guard and request identity.
- [ ] [Day 11 — Ownership and admin](learning-plan/day-11.md): authorization versus authentication; restrict edits.
- [ ] [Day 12 — Save a profile draft](learning-plan/day-12.md): profile DTO, unique slug and one profile per account.
- [ ] [Day 13 — Publish and read a profile](learning-plan/day-13.md): public projection versus private draft.
- [ ] [Day 14 — Review access boundaries](learning-plan/day-14.md): test anonymous, owner, other member and admin.

## Week 3 — Work, services and discovery

- [ ] [Day 15 — Shared service catalog](learning-plan/day-15.md): controlled service types and categories.
- [ ] [Day 16 — Professional offerings](learning-plan/day-16.md): many-to-many join with provider-specific fields.
- [ ] [Day 17 — Create portfolio work](learning-plan/day-17.md): owned project writes and validation.
- [ ] [Day 18 — Public project visibility](learning-plan/day-18.md): hide drafts and enforce owner changes.
- [ ] [Day 19 — Basic discovery](learning-plan/day-19.md): search published professionals by keyword.
- [ ] [Day 20 — Filter and paginate](learning-plan/day-20.md): city/state, category, safe sorting and page limits.
- [ ] [Day 21 — Home feed and review](learning-plan/day-21.md): up to six eligible featured profiles, categories; consolidate tests.

## Week 4 — Social proof, saved work and editorial content

- [ ] [Day 22 — Read trustworthy reviews](learning-plan/day-22.md): approved-only output; no public submission without an eligibility policy.
- [ ] [Day 23 — Private collections](learning-plan/day-23.md): member-owned collection CRUD.
- [ ] [Day 24 — Save projects](learning-plan/day-24.md): unique collection-item join; add/remove work.
- [ ] [Day 25 — Publish blogs](learning-plan/day-25.md): draft/published editor flow and public detail.
- [ ] [Day 26 — Complete the home data](learning-plan/day-26.md): up to three blog summaries and approved testimonials.
- [ ] [Day 27 — Security basics](learning-plan/day-27.md): throttling, CORS, secrets, CSRF as applicable, safe output.
- [ ] [Day 28 — End-to-end and audit](learning-plan/day-28.md): multi-role journeys; logging versus audit events.

## Final 2 days — Make it usable

- [ ] [Day 29 — Runbook and deployment preparation](learning-plan/day-29.md): configuration, migrations, backups and production boot checks.
- [ ] [Day 30 — Demo and knowledge check](learning-plan/day-30.md): run full journey, test suite and explain a request unaided.

Check off a day in its day file and here only after its prediction, behavior and test/design outcome are reviewed; a passing test is not proof that the concept is understood. The shared service catalog and per-professional hourly rates are settled; whether a service can belong to multiple categories remains open. Other product-policy decisions are made on the relevant day and written back to [USER_STORIES.MD](USER_STORIES.MD): what makes a profile publishable and indexable; location/industry/skills; review eligibility; project-only collections; featured selection; and what “Hiring Free” means. Until review eligibility is agreed, Day 22 is read-only. Website links are not silently treated as an in-app messaging system; SEO pages and visual layout remain frontend responsibilities.
