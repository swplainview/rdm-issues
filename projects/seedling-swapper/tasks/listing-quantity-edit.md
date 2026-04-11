---
project: seedling-swapper
title: 'Fix listing quantity edit: added plants marked as claimed'
status: open
priority: medium
created: 2026-04-11
---

When editing a listing to increase the quantity, the newly added plants are immediately marked as claimed instead of available.

Likely the update logic is diffing against claimed count incorrectly — it may be setting `availableQuantity` based on the old value rather than recalculating from `totalQuantity - claimedQuantity`.

Expected behaviour: increasing quantity adds available (unclaimed) plants; claimed count is unchanged.
