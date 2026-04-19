---
phase: 2
title: Create and edit listing form UI
status: done
completed: 2026-04-19
commit: d103b000e1f6f93e5f244b4210334395fa9b9268
---

## Context
Builds on the API from phase 1. Adds the category combobox and hardened-off checkbox to `CreateListingPage` and `EditListingPage`. The combobox uses a creatable-select pattern: users can pick from existing categories or type a new name (which auto-creates via the API on submit).

## Steps
1. Write RTL tests for the updated create and edit forms before implementing
2. Add a `GET /categories` public endpoint (or reuse `/admin/categories`) so the frontend can fetch existing category names — add backend test for this
3. Build a `CategoryCombobox` component: fetches category list on mount, renders a searchable dropdown, "Create <name>" option when no match, controlled by `categoryId` state
4. Add `CategoryCombobox` to `CreateListingPage` and `EditListingPage`; wire `categoryId` into the POST/PATCH payload
5. Add hardened-off checkbox to both forms; wire `hardenedOff` into the payload
6. On `EditListingPage`, pre-populate both fields from the existing listing data

## Acceptance Criteria
- [ ] Category combobox renders existing categories from the API
- [ ] Typing a new name and submitting creates a new category and assigns it
- [ ] Hardened-off checkbox submits `hardenedOff: true/false` correctly
- [ ] Edit form pre-populates category and hardened-off from existing listing
- [ ] Form behaviour covered by RTL tests
