---
project: seedling-swapper
title: Third notification preference option displays blank
status: done
priority: medium
created: 2026-04-16
completed: 2026-04-16
commit: 21f8e5b01d3fe287255589c1e9d303619f0cf4bb
---

On the notification preferences UI, the third option in the list renders with a blank label. Likely related to the addition of CLAIM_UPDATED to the NotificationType enum — the preferences UI may have a hardcoded list that wasn't updated to include the new type.
