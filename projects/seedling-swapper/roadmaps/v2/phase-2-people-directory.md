---
phase: 2
title: People directory
status: not-started
---

A searchable directory of all members, making it easy to find and follow other users.

## Motivation
Currently the only way to reach a user's profile is via a listing they've posted. Users who haven't listed anything are undiscoverable, and there's no way to browse or search for people to follow.

## Implementation parts

### Part A — Backend: GET /users endpoint
- `GET /users` returns all members with public fields only (`id`, `displayName`, `location`, `avatarPath`)
- Optional `?search=` query param for case-insensitive filtering by display name or location
- When authenticated, each result includes an `isFollowing` boolean (avoids N+1 follow-status requests on the page)
- No sensitive fields (email, role) exposed

### Part B — Shared follow button component
- Extract follow/unfollow logic from `UserProfilePage` into a reusable `FollowButton` component
- Existing profile page behavior stays identical
- Component will be reused by Part C

### Part C — PeoplePage + navbar link
- New page at `/people` linked from the navbar
- Displays a grid of user cards: avatar, display name, location
- Debounced search input filtered via `?search=` query param
- Each card links to `/users/:id`
- Inline `FollowButton` on each card for authenticated users viewing someone else
- Empty state when no results match the search
