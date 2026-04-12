---
phase: 6
title: Plant name normalization and API integration
status: not-started
---

Wire up the Perenual plant API for name autocomplete and normalize plant names to title case.

## Plant API integration

- Backend service queries the Perenual API for plant name autocomplete and detail lookup
- Results are cached in the `PlantCache` table (keyed by Perenual ID) with a TTL to avoid hammering the external API
- New endpoint: `GET /plants/search?q=` — returns a list of matching plant names for frontend typeahead

## Title-case normalization

- Perenual API returns names in all lowercase (e.g. "tomato cherry")
- Normalize to title case when writing the name into the listing form from the autocomplete
- Normalization should happen at the point the value is selected, not on display

## Acceptance criteria

- [ ] `GET /plants/search?q=` returns autocomplete suggestions from Perenual (or cache)
- [ ] `PlantCache` entries are reused within TTL; stale entries are refreshed
- [ ] Frontend listing create/edit form uses the autocomplete typeahead for the plant name field
- [ ] Selected plant names are normalized to title case before being submitted
