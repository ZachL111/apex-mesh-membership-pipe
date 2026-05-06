# apex-mesh-membership-pipe

`apex-mesh-membership-pipe` explores distributed systems with a small SQL codebase and local fixtures. The technical goal is to implement an SQL distributed systems project for membership simulation kernel, using seeded input scenarios and deterministic summary checks.

## Purpose

The project exists to keep a narrow engineering decision visible and testable. For this repo, that decision is how quorum health and replica lag should influence a review result.

## Apex Mesh Membership Pipe Review Notes

The first comparison I would make is `replica lag` against `lease drift` because it shows where the rule is most opinionated.

## What Is Covered

- `fixtures/domain_review.csv` adds cases for quorum health and lease drift.
- `metadata/domain-review.json` records the same cases in structured form.
- `config/review-profile.json` captures the read order and the two review questions.
- `examples/apex-mesh-membership-walkthrough.md` walks through the case spread.
- The SQL code includes a review path for `replica lag` and `lease drift`.
- `docs/field-notes.md` explains the strongest and weakest cases.

## Implementation Notes

The repository has two validation layers: the original compact policy fixture and the domain review fixture. They are separate so one can change without hiding failures in the other.

The SQL checks add a separate view over the domain review fixture.

## Command

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/verify.ps1
```

## Audit Path

The verifier is intentionally local. It should fail if the fixture score math, lane assignment, or language-specific test drifts.

## Limits

The fixture set is small enough to audit by hand. The next useful expansion is malformed input coverage, not extra surface area.
