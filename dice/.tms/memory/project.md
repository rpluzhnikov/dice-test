# Project — dice

**Stack:** web
**Test case language:** ru
**Last updated:** 2026-06-19

## What this project is

dice — a dice-rolling game/web app. Users roll dice (RNG-driven) in the
browser. <Expand this once the actual feature set is confirmed from the spec.>

## What kinds of testing live in this TMS

<Check all that apply — the plugin uses this to decide which skills to
load for workers.>

- [x] Functional UI testing
- [x] API / contract testing
- [ ] Mobile (iOS / Android / both)
- [x] Security (manual QA scope per OWASP ASVS L1)
- [ ] Accessibility (manual verifiable subset)
- [ ] Localization / i18n
- [ ] Performance (load tracked elsewhere)
- [x] Other: Regression / Smoke cycles

## Hard rules for this project

<Things the plugin should never violate. Replace/extend with this
project's actual rules — these are defaults seeded by /setup.>

- (default) Never include real customer data in test data, even hashed.
- (default) Use only test/staging environments and credentials for
  browser QA — never production.

## Preferences

`auto_save_learnings`: false
  When false (default), the plugin asks before saving anything to
  `learned/*`. When true, the plugin saves automatically and tells
  the user what was saved.

`default_priority`: medium
  Priority assigned to new cases when the worker can't infer it from
  the checklist tier.

`default_status_on_create`: draft
  Status assigned to new cases. Lead/user promotes to `active` after
  human review.
