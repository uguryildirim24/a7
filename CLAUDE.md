# Working on a7

This is a frozen research artifact collection. It is not a supported docking
pipeline. Read [README.md](README.md) first. There is no application, server or
test suite. The original drivers and analysis scripts were run elsewhere.

Rolf directs the research questions and AI-assisted work. The source manuscript
is `bupropion_alpha7_hypothesis_draft.md`. It is an unsubmitted draft. No completed
faculty review or peer review is recorded.

## Evidence and inspection

Keep tracked tables, coordinates, figures and research audits. They are evidence,
not junk. The parent and combined campaigns used different matrices. Their
control results must not be combined into one tally.

Use the read-only Python CSV query in the README. No packages, credentials or
external data are required for that query. It counts supplied classifications,
not raw coordinates. No end-to-end docking command exists here.

Two bundles containing private metadata are excluded pending a reviewed deposit.
The large combined SDF and representative complexes stay until a real deposit is
available. Availability and historical checksums are in `docs/data_access.md`. The original
16-file checksum manifest is not a gate for this edited public tree.

## Scientific guardrails

- Vina scores are docking scores, not Ki, IC50, affinity, occupancy or clinical effects.
- Docking gives candidate geometries, not binding or functional activity.
- 8V82 and 8V8A are not an activated/desensitized pair. Use template IDs.
- Three seeds measure repeatability, not the unassessed ten-seed stability criterion.
- Search boxes overlap. Site labels come from coordinates, not box names.
- Keep the failed top-pose I34/8V82 control and short-contact flags visible.
- Keep the 2.0 angstrom pose-recovery and below-2.2 angstrom clash thresholds fixed.
- Hydroxybupropion alpha7 activity was not verified in the reviewed sources.
  This is not proof that it was never measured or is inactive.
- HB-O-glucuronide is a source-depicted candidate with unresolved linkage.
- The supplement was interrupted and relaunched. Twelve original failure receipts
  and twelve partial logs are lost. Never reconstruct them as originals.
- Public session evidence is explicitly redacted and linked to the original hash.
- Frozen protocols and historical figures retain old labels. Read the errata in
  `docs/review_record.md`. Do not silently overwrite scientific evidence.
- Search negatives do not establish novelty or complete literature coverage.
- Do not imply submission, demonstrated clinical causality or human target engagement.

Never put personal health notes, private records, local account paths or credentials
in public files. Do not add features, tests, compatibility layers or automatic
reruns. Do not commit or push. Submit a diff for Rolf's review.
