---
test: ../authenticate-as-standard-user-without-inheriting_test.md
status: passed
started: 2026-09-11T20:36:48.476Z
duration_s: 126
session_id: 13f74d5e-36e7-489d-8dac-e9f295acd178
---

# Authenticate as standard_user without inheriting administrative-only access — Result

## Step 1 ✓ passed (34.2s)
md5: ed1feaa3c2d6a64b6b7d8dd2792ebb78
Open https://qaplayground.com/bank/login in a fresh browser session and store the visible unauthenticated login page state as baseline_login_state.

## Step 2 ✓ passed (53s)
md5: 80cb3f3c605b06a82917fad37dade9a8
On the QA Playground Bank Demo login page at https://qaplayground.com/bank/login, sign in with username standard_user and password bank_sauce, then assert the session leaves the unauthenticated login state and shows the normal/full-access banking experience represented by standard_user.

## Step 3 ✓ passed (31.7s)
md5: 3e7bf9ce9d981e327bc73959fe192562
From the authenticated standard_user landing/dashboard and its visible banking navigation, inspect the role-specific content available in the session, then assert no administrative view, administrative data, or administrative-only capability is exposed.
