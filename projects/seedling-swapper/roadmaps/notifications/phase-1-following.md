---
phase: 1
title: Following
status: done
completed: 2026-04-12
commit: 1db5e592f8526b8bac67e05b779454c11cc6ebff
---

Users can follow and unfollow each other. Follow state is visible on public profile pages.

## Schema
- `Follow` model: `id`, `followerId`, `followeeId`, `createdAt`, `@@unique([followerId, followeeId])`
- Add `following` and `followers` relations to `User`

## Backend
- `POST /users/:id/follow` — follow a user (auth required; 409 if already following or following self)
- `DELETE /users/:id/follow` — unfollow (auth required; 404 if not following)
- `GET /users/:id/follow` — returns `{ following: bool }` (auth required)

## Frontend
- `UserProfilePage`: show Follow/Unfollow button for authenticated users viewing someone else's profile
- Fetch follow state on page load; optimistic toggle on click
