---
phase: 4
title: Admin overview dashboard
status: not-started
---

Add a summary dashboard to the admin panel giving a quick read on the health of the active swap.

## Features

- Stats card: active listing count, total claim count, unclaimed quantity
- Quick links to swap management, user management, and full label export
- Should be the landing page when an admin navigates to `/admin`

## Acceptance criteria

- [ ] `GET /admin/overview` returns aggregate stats (listing count, claim count, unclaimed quantity)
- [ ] Admin panel home (`/admin`) renders the dashboard with these stats
- [ ] Quick-action links to the existing swap, user, and label export pages are present
- [ ] Non-admins cannot access the endpoint or the page
