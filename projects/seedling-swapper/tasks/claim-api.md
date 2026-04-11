---
project: seedling-swapper
title: Claim API
status: open
priority: medium
created: 2026-04-11
tags:
- phase-5-claiming
- v1
---

POST /listings/:id/claims with quantity. Validate: swap active, listing has enough remaining quantity, user hasn't already claimed this listing (or allow and sum). Decrement available count atomically. GET /listings/:id/claims (admin). GET /users/me/claims.
