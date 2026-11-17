# MAP NAVI — Document Catalog

**Purpose:** one entry point for project audits, approved decisions, implementation reports, and test evidence.

## Document categories

| Folder | What belongs here | Rule |
|---|---|---|
| [AUDITS](AUDITS/README.md) | Audits, reviews, risk assessments, code and UX inspections | Findings must distinguish verified facts from hypotheses |
| [DECISIONS](DECISIONS/README.md) | Decisions explicitly approved by the project owner | Record the decision, date, scope, and consequences |
| [IMPLEMENTATION](IMPLEMENTATION/README.md) | Reports of completed or partial implementation | State branch, commit, files changed, and what was not done |
| [TESTS](TESTS/README.md) | Test plans, test runs, results, defects, and retests | Separate automated checks from manual/device testing |

## Current project documents

| Document | Category / role | Status |
|---|---|---|
| [Project handoff — 13 Nov 2026](CLAUDE_HANDOFF_MAP_NAVI_2026-11-13.md) | Project context and handoff reference | Existing |
| [Implementation & release tracker — 15 Nov 2026](IMPLEMENTATION_RELEASE_TRACKER_2026-11-15.md) | Implementation / release tracking | Existing |
| [Popup system specification — 16 Nov 2026](https://github.com/basana/map-navi-project-map/blob/docs/popup-system-spec-2026-11-16/POPUP_SYSTEM_SPEC_2026-11-16.md) | Approved popup rules and implementation specification | Separate branch; not merged |
| [Popup Manager implementation PR #4](https://github.com/basana/turret-tales-christmas/pull/4) | Implementation review | Draft PR; not merged or deployed |

## Latest stabilization records

- [Reset and Popup Manager focused checks](TESTS/2026-11-17_reset-popup-manager-focused-checks.md) — focused harness results and explicit browser/device test gaps.
- [Reset and Popup Manager integration record](IMPLEMENTATION/2026-11-17_reset-popup-manager-integration.md) — isolated branch, implementation scope, validation and release state.

## File naming

Use:

`YYYY-MM-DD_short-topic.md`

If useful, add a clear status suffix, for example `YYYY-MM-DD_popup-manager_implementation-report.md`.

## Minimum document header

Every new report should identify:
- **Date**
- **Category**
- **Status:** draft / in review / approved / completed / blocked
- **Scope**
- **Source branch and commit** (for code-related work)
- **Evidence / links**
- **Open issues and next step**

## Working rules

1. A document in **DECISIONS** is authoritative only when its status explicitly says **APPROVED**.
2. An audit finding is not automatically an approved requirement.
3. An implementation report must not imply that code was tested, merged, or deployed unless that happened and is evidenced.
4. Test reports must name the test environment and distinguish passed, failed, skipped, and not tested.
5. Keep original reports intact. Add a dated follow-up rather than silently rewriting historical evidence.
6. Use links to these documents in chat instead of pasting long reports repeatedly. The catalog is the index; the detailed documents remain the source of truth.
7. Do not put credentials, private passenger data, or precise personal location history in project documents.

## Project boundary

This catalog is documentation-only. Creating it does not authorize changes to the live application, merging implementation branches, or deployment.
