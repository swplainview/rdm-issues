---
project: seedling-swapper
title: 'Fix listing quantity edit: added plants marked as claimed'
status: done
priority: medium
created: 2026-04-11
completed: 2026-04-11
commit: 85ab396a3a6f906046f1411963609dc9901756d6
---

When editing a listing to increase the quantity, the newly added plants are immediately marked as claimed instead of available.

Likely the update logic is diffing against claimed count incorrectly — it may be setting `availableQuantity` based on the old value rather than recalculating from `totalQuantity - claimedQuantity`.

Expected behaviour: increasing quantity adds available (unclaimed) plants; claimed count is unchanged.
