---
phase: 3
title: 'Listing metadata: categories and hardened-off indicator'
status: not-started
---

Add two metadata fields to listings: category tagging and a hardened-off indicator.

## Categories

Users can tag a listing with a category (e.g., Pepper, Berry, Flower, Herb, Tree).

- New `Category` model: `id`, `name` (unique), `createdAt`
- `Listing` gets an optional `categoryId` foreign key; migration required
- Create/edit listing form: combobox/creatable-select pattern — pick from the existing list or type a new name to create it automatically
- Admins can manage the canonical category list from the admin panel (add, rename, delete — with a guard if the category is in use)
- Home/browse page: optional filter by category

## Hardened-off indicator

Add a boolean flag so listers can indicate whether a seedling has been hardened off.

- Add `hardenedOff Boolean @default(false)` to the `Listing` model; migration required
- Optional checkbox in create/edit listing forms
- Display on listing cards and detail page (badge or icon)

## Acceptance criteria

- [ ] `Category` table exists; `Listing.categoryId` nullable FK
- [ ] `Listing.hardenedOff` boolean column with default false
- [ ] POST /listings and PATCH /listings/:id accept `categoryId` (optional) and `hardenedOff` (optional)
- [ ] GET /listings and GET /listings/:id include `category` and `hardenedOff` in response
- [ ] Frontend create/edit form has category combobox and hardened-off checkbox
- [ ] Listing cards and detail page display category and hardened-off status
- [ ] Admin panel has a category management section
- [ ] Home page has a category filter
