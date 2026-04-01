# Task: Add Scope 3 Emission Tracking

## Background

The application currently tracks **Scope 1** (direct emissions) and **Scope 2** (energy-related emissions). Your task is to extend it with **Scope 3** (value chain) emissions.

## What to Build

### 1. Extend the Data Model

- Add `SCOPE_3` to the `EmissionScope` enum in the shared library
- Add a `subcategory` field to the `EmissionEntry` entity for Scope 3 entries
- The subcategory should be **nullable** (only Scope 3 entries have one)

### 2. Update the API

- Ensure Scope 3 entries can be created, read, updated, and deleted
- Add validation:
  - `subcategory` is **required** when scope is `SCOPE_3`
  - `subcategory` is **forbidden** (must be null/undefined) when scope is `SCOPE_1` or `SCOPE_2`
- Update the DTO and shared interface accordingly

### 3. Update the UI

- The emission entry form should show a **subcategory dropdown** when Scope 3 is selected
- The list view should display the subcategory column (show "—" for Scope 1/2 entries)
- The existing Scope 1/2 flows must **not break**

## Scope 3 Subcategories to Support

| Subcategory | Description |
|-------------|-------------|
| Business travel | Flights, hotels, rental cars |
| Employee commuting | Daily commute of employees |
| Purchased goods & services | Upstream supply chain emissions |
| Waste generated in operations | Waste disposal and treatment |
| Upstream transportation | Inbound logistics and distribution |

## Acceptance Criteria

- [ ] `SCOPE_3` is available as a scope option in the form
- [ ] Selecting Scope 3 shows a subcategory dropdown with the 5 options above
- [ ] Selecting Scope 1 or 2 hides the subcategory dropdown
- [ ] API validates: subcategory required for Scope 3, forbidden for Scope 1/2
- [ ] List view shows subcategory for Scope 3 entries
- [ ] Existing Scope 1/2 entries and flows are unchanged

## Hints

- Look at how existing Scope 1/2 entries work — **follow the same patterns**
- You can use AI coding tools (Cursor, Claude Code, etc.) freely — we want to see how you work with them
- The app uses `synchronize: true`, so schema changes apply automatically. Writing a proper TypeORM migration is a **bonus**.
- **Ask questions!** Clarifying requirements is part of the assessment.

## Time Budget

This task is designed to be completable in **30–45 minutes**.
