# Profile Links — business requirements (working draft)

This file is the source of truth for *proposed* product behavior. It records the user's October 20, 2026 brief; unresolved choices are explicitly marked below. The visual references (WorkScout and Dribbble) are inspiration for the frontend, not an API contract. No marketplace payments, proposals, messaging, or job listings have been requested for the first backend.

## Product goal and actors

Help clients discover professionals who offer online services, inspect a credible public profile and portfolio, and follow a website/contact link. A visitor can browse without an account; a registered member can create collections and, subject to review policy, leave reviews. A professional manages their own profile, projects and service offerings. An admin manages taxonomy, blog publication and moderation. An account may also browse and save work; do not force mutually exclusive client/professional accounts.

## User stories

### Identity and profile

- As a member, I can sign up, sign in and sign out with validated credentials, so that my private changes belong to me.
- As a professional, I can create/edit my own profile with a unique public slug, name, headline, bio, location, industry, avatar, website and selected social links; I can control when it becomes public.
- As a visitor, I can open a published professional's profile and see identity, links, proof of work (projects), services, reviews and an appropriate way to inquire. Public URLs should be shareable and discoverable by search engines when the owner opts into publication.
- The frontend may describe profiles as “hiring-free” / “hire page included”; the meaning of “Hiring Free” needs confirmation before it becomes a data field or product promise.

### Services, projects and taxonomy

- As a professional, I can add multiple projects; each project has exactly one professional owner. A project may include a title, summary, media/link and relevant categories/skills; the exact fields will be refined when implemented.
- As a professional, I can offer multiple services. A service type is shared across professionals; my own hourly rate, description and availability (if used) belong to my *offering*, not to the shared service. For example, the `Web Development` service is one catalog entry: Yaseen offers it for USD 10/hour and Abdullah for USD 15/hour. This describes displayed rates, not on-platform payments.
- As a visitor, I can browse a dynamic API-driven category list. Initial category labels: Programming, Graphic Design, Digital Marketing, Writing, Video, AI Services, Music & Audio, Business Consulting. Admins manage additions/renames/order; public clients can only read active categories.
- As a visitor, I can search published professionals by keyword (job title, skill or industry), city/state and category; the URL/API should allow combining filters, pagination and a predictable sort. Industry and category are different concepts.

### Discovery and social proof

- As a visitor, I can see six published professionals featured on the home page, with a View Profile action and website link where available.
- As a visitor, I can read reviews associated with a professional in that professional's Reviews tab. Only approved, public reviews appear in home-page testimonials; reviews retain their author and target professional.
- The frontend can display clearly marked placeholder reviews during design, but live production social proof must not impersonate real clients. Review eligibility and moderation rules must be agreed before accepting public submissions.

### Collections

- As a signed-in member, I can create private, named collections (for example “Design” and “Minimal”), then save a professional's *project/work* into a chosen collection. A project may be in multiple collections; duplicates within one collection are not useful.
- As that member, I can view, remove or move my saved projects. Other members cannot read or modify my private collections. Saving entire profiles or services is a possible later extension, not an implicit first-version requirement.

### Editorial and static content

- As a visitor, I can read published blog summaries (three on the home page), browse articles and open a blog detail page by slug. An admin can draft, edit and publish posts.
- Home-page category cards, “What's on a profile”, “Everything you need to grow”, adaptable-profile cards, FAQ and footer can initially be frontend copy; do not create a CMS or extra backend models unless editing them becomes a requirement.
- The full-screen photographic hero, split search bar, restrained green (`#1F4B3F`) and white (`#FFFFFF`) palette, three navigation links, animations and responsive layout are frontend concerns; the backend supplies real search, categories, featured professionals, reviews and blogs.

## Proposed first-pass data relationships

- `Account` 1—0..1 `ProfessionalProfile`; `ProfessionalProfile` 1—many `Project`.
- `ProfessionalProfile` many—many `Service` via `ProfessionalService` (the offering/join record). `Service` holds the shared name/slug; `ProfessionalService` holds that professional's hourly rate, currency and any provider-specific details. Enforce one offering per (professional, service). Store money in minor units (for example USD 10/hour as 1000 cents), not floating-point numbers. `Service` can belong to one or more `Category`; decide whether multiple categories are necessary before schema work.
- `ProfessionalProfile` 1—many `Review`; `Review` also belongs to an author `Account`.
- `Account` 1—many `Collection`; `Collection` many—many `Project` via `CollectionItem`.
- `BlogPost` belongs to an author/editor `Account`; category catalog and industry taxonomy must remain distinct.
- Published/unpublished state matters for profiles, projects, reviews and blogs; unpublished content must not leak through public list/detail endpoints or search.

## Out of scope for the first slice

Payments, escrow, commissions, job-board listings, job applications, messages, booking, subscriptions, full-text search infrastructure, social login, an admin UI and a general-purpose CMS. We can revisit these when actual marketplace workflows are specified.

## Decisions to settle together, before the relevant day

1. Who may write a review, and how do we verify a genuine engagement without transactions on-platform? Until decided, plan read-only review display and moderation, not open posting.
2. Can one shared service have multiple categories, or exactly one? The shared service catalog and per-professional hourly offerings are confirmed; only category cardinality remains open.
3. Which fields are mandatory before a profile can be published? Is the website link the contact CTA, or do we need a separate email/contact method?
4. How are city/state/industry/skills normalized, and which countries are supported initially?
5. What does “Hiring Free” mean, and may Google index every published profile by default or only with explicit opt-in?
6. Should a collection initially save projects only (recommended from “freelancer's work”), or profiles/services too?
7. What makes a professional “featured” (manual admin selection versus deterministic recent/popular order)?

See [learning-plan.md](learning-plan.md) for the staged backend approach. Any decision here should be reflected in the relevant day's checklist before implementation.
