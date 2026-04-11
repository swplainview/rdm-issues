---
project: seedling-swapper
title: Perenual plant API integration with cache
status: open
priority: medium
created: 2026-04-11
tags:
- phase-4-listings
- v1
---

Backend service to query Perenual API for plant name autocomplete and detail lookup. Cache results in PlantCache table (keyed by Perenual ID) with TTL. Expose GET /plants/search?q= endpoint for frontend typeahead.
