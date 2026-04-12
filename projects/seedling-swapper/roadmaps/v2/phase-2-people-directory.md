---
phase: 2
title: People directory
status: not-started
---

A searchable directory of all members, making it easy to find and follow other users.

## Motivation
Currently the only way to reach a user's profile is via a listing they've posted. Users who haven't listed anything are undiscoverable, and there's no way to browse or search for people to follow.

## Behavior
- New page at `/people` linked from the navbar
- Displays a grid/list of all members with their avatar, display name, and location
- Live search by display name or location (client-side filter or debounced API query)
- Each card links to the user's public profile (`/users/:id`)
- Follow/unfollow button inline on each card (for authenticated users viewing someone else)
- Empty state when no results match the search

## API
- `GET /users` — paginated or full list of users with public fields: `id`, `displayName`, `location`, `avatarPath`
- No sensitive fields (email, role) exposed

## Frontend
- `PeoplePage` component at `/people`
- Navbar link added alongside History
- Reuses follow/unfollow logic from `UserProfilePage`
