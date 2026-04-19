---
phase: 3
title: Display metadata on cards, detail page, and home filter
status: done
completed: 2026-04-19
commit: c9637806c6f0e6015feb10aa6280956998cab3af
---

## Context
Builds on phase 2. Surfaces the new fields to browsing users: category badge and hardened-off badge on listing cards, the same on the detail page, and a category filter dropdown on the home page.

## Steps
1. Write RTL tests for the updated ListingCard, ListingDetailPage, and HomePage filter before implementing
2. Add category badge (pill showing category name) and hardened-off badge (e.g. "Hardened off" label) to the listing card component; hide gracefully when not set
3. Add the same badges to `ListingDetailPage`
4. Add a category filter dropdown to `HomePage` — fetches the category list and filters the displayed listings client-side (or via a `?categoryId=` query param if preferred)
5. Ensure the filter resets correctly when "All categories" is selected

## Acceptance Criteria
- [ ] Listing cards show category badge when set (hidden when null)
- [ ] Listing cards show hardened-off badge when true (hidden when false)
- [ ] ListingDetailPage shows category and hardened-off status
- [ ] Home page has a working category filter
- [ ] Display and filter behaviour covered by RTL tests
