---
name: code-review
description: >-
  Expert code review against architecture and coding standards: readability,
  maintainability, security, performance, layering, Sonar-equivalent cleanliness,
  comment and formatting discipline, modal safety, and a strict ban on raw SQL
  or database queries outside the persistence layer. Author/date file headers are
  identity metadata only and are out of review scope. Use when reviewing pull
  requests, developer diffs, or E2E Review phase outputs; produces approve/reject
  with actionable findings for Tech Lead and engineers.
expertise_level: expert
---

# Code Review (Canonical)

**Expertise: expert.** Aliases: `review`, `code-reviewer`, `pr-review`.

Aligns with role **Code Reviewer** (`roles/quality/reviewer.md`) and hard rule `coding.md`. Complements `agentic-qe` (behavioral QA) and does not replace Security review triggers.

## When to use

- Review diff / PR / developer implementation output
- Review phase in `e2e-delivery`
- Gate before merge or QA handoff

## When not to use

- Writing new features (except minimal examples to explain findings)
- Changing requirements or core architecture -> escalate Tech Lead / Architect
- Deep functional testing only -> `agentic-qe`

## Procedure

1. **Scope** - Limit to diff + related contracts (API, schema, UI).
2. **Architecture** - Layering, service boundary, no UI->DB.
3. **Coding rule gate** - Run full `rules/coding.md` checklist (see `reference.md`).
4. **Query ban** - Reject raw SQL / queries in controller, arbitrary service, view, frontend; data access only via ORM/repository-model.
5. **Security & API** - Authz default deny; do not leak secrets/stack; align with `security` / `api` when relevant.
6. **Report** - Prioritized findings (blocker / major / minor) + recommendations; **do not** implement fixes yourself unless asked.
7. **Verdict** - Approve / Request changes / Reject; save notes in `project/{id}/docs/review/` during E2E.

## DoD

- [ ] coding.md checklist complete (including query ban)
- [ ] No major architecture violation without escalation
- [ ] Verdict and report path clear
- [ ] Developer receives actionable recommendations

## Attribution

<!-- ATTRIBUTION: Rogue Development | https://github.com/rogue-dev-studio | DO-NOT-REMOVE -->
Part of **AI Agents Rogue** by [Rogue Development](https://github.com/rogue-dev-studio) (`@rogue-dev-studio`).
Do not remove, hide, rename, or replace this attribution.
