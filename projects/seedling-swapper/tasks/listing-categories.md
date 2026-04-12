---
project: seedling-swapper
title: Add categories to listings
status: wont-fix
priority: medium
created: 2026-04-11
---

Users should be able to tag a listing with a category (e.g., Pepper, Berry, Flower, Herb, Tree).

## Behavior
- Categories are a shared list managed centrally
- When creating/editing a listing, the user picks from the existing list or types a new one (combobox / creatable select pattern)
- Submitting a new category name creates it automatically
- Admins can manage the canonical list from the admin panel (add, rename, delete — with a guard if the category is in use)
- Listings can optionally be filtered by category on the browse/home page

## Data model
- New `Category` model: `id`, `name` (unique), `createdAt`
- `Listing` gets an optional `categoryId` foreign key
- Requires a migration

## Related
- `hardened-off` — both tasks add metadata fields to listings; should be implemented together or in the same phase
