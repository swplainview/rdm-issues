---
project: seedling-swapper
title: Allow listing owner to add a note when adjusting a claim quantity
status: open
priority: medium
created: 2026-04-16
---

When the listing owner adjusts a claim quantity via PATCH /claims/:id, they should be able to include an optional note explaining the adjustment (e.g. 'Only brought 2 plants instead of 3'). The note should be surfaced to the claimant — likely included in the CLAIM_UPDATED notification message and/or displayed in the UI alongside the updated claim.
