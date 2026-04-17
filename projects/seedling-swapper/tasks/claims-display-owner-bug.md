---
project: seedling-swapper
title: Listing owner sees others' claims displayed as their own
status: open
priority: medium
created: 2026-04-16
---

On the listing detail page, when logged in as the listing owner, claims made by other users appear in the 'Your claim' section instead of (or in addition to) the 'Who has claimed' section. The myClaims filter likely needs to check both listingId and userId against the current user.
