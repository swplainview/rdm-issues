---
project: seedling-swapper
title: Show claimants on listing detail page
status: done
priority: medium
created: 2026-04-11
completed: 2026-04-11
commit: c59e22dc61d39cadbdda22d3ad2f14f6d09fa84a
---

Listing owners and admins should be able to see who has claimed units when viewing a listing detail page. Currently the GET /listings/:id/claims endpoint exists but the UI doesn't surface this information. Display claimant names and quantities in the listing detail view, visible only to the listing owner and admins.
