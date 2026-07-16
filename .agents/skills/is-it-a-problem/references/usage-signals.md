# Usage signals — common schema traps

Reference for gates 2-4 of is-it-a-problem. These are the traps that can invalidate an impact analysis if ignored.

## Signals for "is this real usage?"

For the entity under analysis, cross:
- distinct sessions or activities
- number of distinct actors or evaluators
- span in days between first and last activity
- days since the last activity
- who acted most recently

A single event at 100% in one sitting, with a span of zero, is a plausible one-off test — not evidence of sustained real use. Multiple actors and a multi-month span are much stronger signals of genuine longitudinal use.

## Traps

- Cloning, seeding, or copy actions can inflate counts. A record that appears N times because of generated copies is not evidence of N real users.
- "Session" may not mean the same thing as the business activity under analysis. Define the unit of activity explicitly before counting.
- A copied record can look like fresh usage. Compare the current record with the prior one to see whether it is a true new event or a duplicate.
- Expiration, validity, or lifecycle logic may not be copied during cloning or provisioning. Any metric tied to that logic may silently undercount or no-op.
- Ownership or tenancy fields can be inconsistent. Do not assume the relationship between a record and its parent organization is always straightforward.
- Filled in does not mean used. A record that was created and abandoned may have incomplete data. Compare completed rows against total rows to separate real completion from empty shells.
- Demo seeds or test data can pollute the numbers. Exclude them before counting anything.
- Prefer a real event timestamp over a manually set date. A large gap between the two often indicates a backfill or bulk import rather than organic usage.

## Access constraint

If read-only production access is unavailable, say so plainly before running exploratory queries. Do not imply that a safe read-only path exists when it does not.

## Getting schema context on demand

Use the repository's schema helper or documentation tooling to pull specific model definitions on demand rather than loading the whole schema at once. This keeps context light while still allowing deeper analysis when needed.
