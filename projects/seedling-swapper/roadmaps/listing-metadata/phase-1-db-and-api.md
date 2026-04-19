---
phase: 1
title: DB migrations and API layer
status: not-started
---

## Context
Everything else depends on the database schema and updated API. This phase adds the `Category` model, the `categoryId` FK on `Listing`, and the `hardenedOff` boolean — then updates listing routes to accept and return both fields, and adds admin category CRUD endpoints.

## Steps
1. Add `Category` model (`id`, `name` unique, `createdAt`) and `categoryId` optional FK on `Listing` to `schema.prisma`
2. Add `hardenedOff Boolean @default(false)` to `Listing` in `schema.prisma`
3. Run `prisma migrate dev` to generate and apply the migration
4. Write backend tests (Supertest) covering the new fields on POST/PATCH/GET listing routes and the admin category endpoints before implementing
5. Update `POST /listings` and `PATCH /listings/:id` to accept optional `categoryId` and `hardenedOff`
6. Update `GET /listings` and `GET /listings/:id` to include `category` relation and `hardenedOff` in response
7. Add admin category routes under `/admin/categories`:
   - `GET /admin/categories` — list all with in-use count
   - `POST /admin/categories` — create (unique name)
   - `PATCH /admin/categories/:id` — rename
   - `DELETE /admin/categories/:id` — delete (guard: reject if any listing uses it)

## Acceptance Criteria
- [ ] `Category` table exists; `Listing.categoryId` nullable FK
- [ ] `Listing.hardenedOff` boolean column with default false
- [ ] POST /listings and PATCH /listings/:id accept `categoryId` (optional) and `hardenedOff` (optional)
- [ ] GET /listings and GET /listings/:id include `category` object and `hardenedOff` in response
- [ ] GET /admin/categories returns all categories with usage counts
- [ ] POST /admin/categories creates a category (rejects duplicate names)
- [ ] PATCH /admin/categories/:id renames a category
- [ ] DELETE /admin/categories/:id deletes (returns 409 if category is in use)
- [ ] All new behaviour covered by Supertest tests
