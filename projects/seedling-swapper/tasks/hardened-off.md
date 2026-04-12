---
project: seedling-swapper
title: Add hardened-off indicator to listings
status: wont-fix
priority: medium
created: 2026-04-12
---

Add a checkbox to the create/edit listing form to indicate whether a seedling has been hardened off.

## Changes
- Add `hardenedOff Boolean @default(false)` field to the `Listing` model
- Migration to add the column
- Include the field in create/edit listing API (optional, defaults false)
- Add a checkbox to CreateListingPage and EditListingPage
- Display the status on ListingDetailPage and listing cards (e.g. a small badge or icon)

## Related
- `listing-categories` — both tasks add metadata fields to listings; should be implemented together or in the same phase
