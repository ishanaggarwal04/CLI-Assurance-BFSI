---
test: ../keep-the-funding-operation-unavailable-to-an-unauthenticated_test.md
status: passed
started: 2026-09-11T20:59:00.170Z
duration_s: 52
session_id: 583f382b-9cf4-4658-bf50-e579ddac86e2
---

# Keep the funding operation unavailable to an unauthenticated visitor — Result

## Step 1 ✓ passed (15.2s)
md5: 5011f335c96087c5ae6f815fedb390d3
Open https://qaplayground.com/bank/login in a fresh browser session and remain unauthenticated.

## Step 2 ✓ passed (32.3s)
md5: f72c96ddf31fa4a9ccaf3dffe3fc2fd8
From the unauthenticated experience, inspect the visible page and any normal visible navigation available without signing in for access into banking functionality, then assert no authenticated banking page and no deposit, add-funds, or equivalent balance-increase control becomes available.
