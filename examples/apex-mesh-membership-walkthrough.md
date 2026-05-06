# Apex Mesh Membership Pipe Walkthrough

I use this file as a small checklist before changing the SQL implementation.

| Case | Focus | Score | Lane |
| --- | --- | ---: | --- |
| baseline | quorum health | 131 | watch |
| stress | lease drift | 106 | watch |
| edge | replica lag | 209 | ship |
| recovery | membership churn | 184 | ship |
| stale | quorum health | 200 | ship |

Start with `edge` and `stress`. They create the widest contrast in this repository's fixture set, which makes them better review anchors than the middle cases.

The next useful expansion would be a malformed fixture around lease drift and membership churn.
