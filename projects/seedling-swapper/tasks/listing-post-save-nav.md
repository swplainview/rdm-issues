---
project: seedling-swapper
title: Navigate back to swap page after adding or editing a listing
status: done
priority: medium
created: 2026-04-11
completed: 2026-04-11
commit: c1f3235ea23d187f7c30d5fdb8eb8685c636eea1
---

After successfully creating or updating a listing (plant), the UI should redirect the user back to the parent swap page rather than leaving them on the listing form.

The swap ID is already available in context when the listing is saved, so the redirect target is known. Apply to both create and update flows.
