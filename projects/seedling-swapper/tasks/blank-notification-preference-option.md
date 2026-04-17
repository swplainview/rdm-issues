---
project: seedling-swapper
title: Third notification preference option displays blank
status: open
priority: medium
created: 2026-04-16
---

On the notification preferences UI, the third option in the list renders with a blank label. Likely related to the addition of CLAIM_UPDATED to the NotificationType enum — the preferences UI may have a hardcoded list that wasn't updated to include the new type.
