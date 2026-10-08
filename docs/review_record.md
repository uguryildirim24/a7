# Review record and errata

Public documentation: October 8, 2026. The original claim audit, computational
findings and single-hypothesis submission review remain as historical research
records. This document explains superseded claims. It is not faculty or peer review.
No new complete reference audit was performed during cleanup.

## Superseded source-audit findings

- Dale 2008: the initial abstract-only audit called the comparison unsupported.
  Later full-text review located its composition. The initial FIX is superseded.
  The small sample is not an equivalence test.
- Grunebaum 2013: later review located the Disturbed Thinking composite and null
  treatment comparison. The initial abstract-only FIX is superseded. There is no
  item-level DP/DR effect estimate. A floor effect is an interpretation.
- Papke 2011: acute and bath protocols differ. Alpha4-containing receptors are not
  uniformly more sensitive under both. The manuscript distinguishes them.
- No verified hydroxybupropion alpha7 measurement in this review does not mean
  never measured or inactive.
- An author's use of "therapeutically relevant" is not a human exposure demonstration.
- The initial citation-tag total disagrees with its table. It is not a source-quality
  measure.

Access remains incomplete for Damaj 2004, Bondarev 2003 and Vazquez-Gomez 2014.
Bupropion-specific Duarte supplementary contacts remain to be checked. The
historical exposure arithmetic is retained as evidence of the review process.
Rat-to-human partition assumptions, conflicting protein-binding estimates and
transfer of in-vitro IC50 to circuit response remain unresolved. Those estimates
are not measured human concentrations or occupancy.

## Template correction

8V82 and 8V8A are epibatidine/PNU-120596 complexes. Burke et al. describe intermediate
conformations and did not obtain a fully activated alpha7 state. The time-resolved
8V8A intermediate is virtually identical to equilibrium 8V82. They must not be
interpreted as an activated/desensitized pair.

Source: Burke et al. (2024), *Structural mechanisms of alpha7 nicotinic receptor
allosteric modulation and activation*, Cell, DOI 10.1016/j.cell.2024.01.032,
PMID 38382524, PMCID PMC10950261.

Public reports use template IDs. The restored historical figures and extracted
frozen protocols retain the original labels. Their labels are not new functional
state evidence. Figure titles need correction before reuse in a publication.

| Historical document | SHA-256 of extracted original bytes |
| --- | --- |
| `MATRIX_FROZEN.md` | `7df45667a832fdc17dabf64f77cd06d9f01958bbb9a7731aac306c0a636b9593` |
| `PROTOCOL_FROZEN.md` | `d160398595a790bfe5c279c069c763f01b4799c1d4cb90d03d6132a6d0031fc7` |

The matrix describes the 576-job main panel plus controls, before the 96-job
candidate supplement. Its statement that HB glucuronide was not docked applies
to the main matrix. The parent protocol's execution-scope section limits the
delivered pass to three seeds and variant A. Its wider proposed matrix is not
the executed result. Shelved AutoDock4 tooling is historical, not a dependency.

## Historical table re-analysis

The October 7 research record and October 8 cleanup described the following
supplied-table calculations. The original CSVs are now retained in the repository.
The cleanup-only summary script and compact duplicate exports were removed to
keep the project frozen. The README contains a read-only CSV query instead.

| Quantity | Recorded result |
| --- | ---: |
| Rank-1 metabolite/parent rows | 672 |
| Species / species-form pairs | 22 / 28 |
| Main / supplement rank-1 rows | 576 / 96 |
| I34 pocket / other interface / pore lumen / EPJ pocket | 252 / 172 / 145 / 103 |
| Measured-site groups | 154 |
| Printed mode-table rows | 13,426 |
| Printed rows with saved coordinates / log-only | 12,282 / 1,144 |
| Rank-1 / saved-mode short-contact flags | 13 / 93 |
| Printed rank-2 minus rank-1 gap below 0.085 kcal/mol | 355 of 672 |
| Pore-lumen jobs below that gap | 142 of 145 |
| R,R-HB / S,S-HB mid-pore rank-1 lumen placements | 12 of 12 / 8 of 12 |

The gap uses printed values, not hidden optimizer scores. The comparison comes
from the largest observed misranking gap in one control, I34/8V82. It is not a
statistical tie threshold or error bar. Seeds are not biological replicates.
The README query counts rows and supplied site labels. It does not recompute
score gaps, coordinate classes, symmetry clusters, chemistry or receipt validity.

## Campaign-specific limits

The parent campaign reported four of five control pairs passing at top pose.
The combined campaign reported three of four. These are different matrices and
fresh runs. I34/8V82 failed at rank 1 in both and recovered the deposited pose at
rank 2. Combined control RMSD ranges were 6.372-6.411 angstrom at rank 1 and
0.744-0.783 at rank 2.

The parent campaign produced pore poses with smaller boxes. Combined mid-pore
parent rank-1 poses instead occupied the I34 pocket. Wider boxes can reach that
pocket. This is setup sensitivity, not proof that box size alone caused the
change or that parent cannot enter the pore. A panel-level Duarte residue overlap
is not a bupropion-specific experimental validation.

Three seeds measure repeatability, not ten-seed stability. There is no experimental
pore-blocker pose-recovery control. HB-O-glucuronide linkage and protonation remain
unresolved. The [interrupted supplement](../INCIDENT_supplement_interruption.md)
and irreversible record loss remain qualifications on the data.

Historical search counts lack a complete screening record. They remain in dated
research records, not as evidence of novelty or complete literature coverage.
The submission review predates the two-hypothesis draft. Its venue and policy
statements are not current guidance.

## Public-tree scope

The session derivative retains all 19 ordered messages in the original schema.
Roles, content types, message timestamps, token counters, wording and all six shell
commands were restored from the committed capture. Only private paths and message,
tool, session and execution identifiers are replaced. Original nested escaping is
preserved. Every embedded tool result and the nested interruption output parsed
during this scope review. No lost receipts or logs were reconstructed.

The verification JSON retains its source description and all 15 numeric
`saved_version` counters. Only private artifact-version identifiers are removed.
Tracked results and research evidence remain, including the large combined SDF
and representative complexes.
Two bundles containing private metadata await reviewed replacements.
Stale manuscript renderings were duplicate exports and remain removed.

The README query ran once in the worktree during this scope review. Its counts
matched the documented values, including 672 rank-1 rows and 13/93 short-contact
flags. It wrote no files. The 15 untouched tracked files matched their committed
bytes. Local Markdown links and `git diff --check` passed. Gitleaks found no leaks
in its directory scan with archive traversal. A targeted text privacy scan covered
28 files and 154 decompressed archive members and found no matches.

No clean snapshot run, new docking, model download, paid service, network clone
or history edit was performed during this scope review. Full campaign reruns are
unavailable because the drivers and reviewed input bundles are absent. Git-history
privacy is handled separately. See [data access](data_access.md) for the deposit
gap and original-checksum limits.
