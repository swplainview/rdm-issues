---
phase: 1
title: Claim quantity adjustment by listing owner
status: not-started
---

Allow the owner of a listing to manually adjust the quantity allocated to a specific claim — for example, to accommodate a partial fulfillment or correct an over-claim.

## Motivation
Swappers sometimes bring fewer plants than expected. The listing owner needs a way to reduce a claimant's quantity rather than cancelling the claim entirely.

## Behavior
- On the listing detail page, the owner sees an editable quantity next to each claimant in the "Who has claimed" section
- Changing a quantity updates the claim and recalculates `remainingQuantity` on the listing accordingly
- A reduction cannot bring a claim below 1 (owner should cancel the claim instead)
- An increase cannot exceed the current `remainingQuantity` plus the original claim quantity
- The claimant receives a `CLAIM_UPDATED` notification (if the notification system supports it)

## API
- `PATCH /claims/:id` — update `quantity` on a claim (restricted to listing owner or admin)

## Data model
- No schema changes required
