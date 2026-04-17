---
project: seedling-swapper
title: Allow listing owner to add a note when adjusting a claim quantity
status: open
priority: medium
created: 2026-04-16
---

When the listing owner adjusts a claim quantity via PATCH /claims/:id, they should be able to include an optional note explaining the adjustment (e.g. 'Only brought 2 plants instead of 3'). The note is claimant-facing: it should be displayed to the claimant in the UI on the listing detail page alongside their updated claim, and included in the CLAIM_UPDATED notification message.
