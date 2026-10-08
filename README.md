# a7

A frozen computational study of bupropion and metabolites at the alpha7 nicotinic receptor. It includes docking results, a literature review and a two-hypothesis manuscript.

## What this is

This is a research artifact collection, not an application or a supported docking
pipeline. The [Markdown manuscript](bupropion_alpha7_hypothesis_draft.md) is the
source document. No published paper or preprint is recorded here.

The study separates modeled locations from measured pharmacology. Docking scores
are not Ki, IC50, affinity, occupancy or clinical effects. The proposed receptor,
circuit and symptom links remain hypotheses.

## Inspect the included results

Python 3 is enough for this read-only query. It uses the standard library.
No installation, credentials, network, GPU or Vina executable is needed.
Run it from the repository root:

```bash
python3 -I - <<'PY'
import csv
from collections import Counter

with open('bupropion_receptor_evidence.csv', newline='', encoding='utf-8') as f:
    literature = list(csv.DictReader(f))
with open('combined_metabolite_poses.csv', newline='', encoding='utf-8') as f:
    poses = list(csv.DictReader(f))
print('Literature observations:', len(literature))
print('Distinct PMIDs:', len({r['pmid'] for r in literature if r['pmid']}))
print('Rank-1 jobs:', len(poses))
print('Species:', len({r['species'] for r in poses}))
print('Species/form pairs:', len({(r['species'], r['form']) for r in poses}))
print('Measured sites:', dict(sorted(Counter(r['measured_site'] for r in poses).items())))
for name in ('combined_by_measured_site.csv', 'combined_log_evaluated_scores.csv',
             'combined_clash_flagged.csv', 'combined_clash_allmodes.csv'):
    with open(name, newline='', encoding='utf-8') as f:
        print(name, len(list(csv.DictReader(f))))
PY
```

Expected counts are 104 literature observations, 84 distinct PMIDs, 672 rank-1
jobs, 22 species and 28 species/form pairs. Measured-site counts are 252 I34-pocket,
172 other-interface, 145 pore-lumen and 103 EPJ-pocket placements. The remaining
four tables contain 154, 13,426, 13 and 93 rows, respectively.

The query prints to stdout and writes no files. It counts supplied classifications.
It does not classify coordinates, validate chemistry or repeat the receipt audit.
There is no end-to-end docking command in this repository. The original drivers
were run elsewhere and are not included.

## Layout

| Path | Purpose |
| --- | --- |
| `bupropion_alpha7_hypothesis_draft.md` | Unsubmitted two-hypothesis manuscript |
| `bupropion_receptor_evidence.csv`, `bupropion_receptor_evidence_map.md` | Literature observations and overview |
| `parent_docking_findings.md` | Parent-only report and controls |
| `parent_bupropion_poses.sdf`, `parent_pose_in_receptor.png` | Parent coordinates and historical figure |
| `combined_*.csv`, `combined_complex_coverage.json`, `combined_*.png` | Combined result tables, coverage and historical figures |
| `combined_poses_ALL_MODES.sdf`, `combined_representative_complexes.tar.gz` | Saved combined coordinates and representative complexes |
| `metabolite_delivery_SHA256SUMS.txt`, `metabolite_delivery_verification.json` | Original delivery checksums and verification record |
| `claim_audit_2026-10-07.md`, `computational_findings_2026-10-07.md` | Historical research audits, including exploratory arithmetic |
| `hypothesis_novelty_and_submission_review.md` | Historical single-hypothesis review, not current venue guidance |
| `docs/review_record.md` | Corrections and limits on historical records |
| `docs/PROTOCOL_FROZEN.md`, `docs/MATRIX_FROZEN.md` | Historical method documents extracted from the archives |
| `INCIDENT_supplement_interruption.md`, `hb-oglu-interruption-session-evidence.json` | Record-loss disclosure and redacted session evidence |
| `docs/data_access.md` | Included data, omitted large artifacts and deposit gap |
| `CLAUDE.md` | Editing and scientific guardrails |

Tracked scientific evidence remains in the tree, including the combined SDF and
representative complexes. Stale PDF and DOCX exports were removed because they
duplicate an older manuscript. Two bundles containing private metadata are not
included. See [data access](docs/data_access.md). No reviewed replacement deposit
is available yet, so a clean clone cannot reproduce the full docking campaign.

Historical checksums identify the original delivery. They are not a checksum gate
for this edited tree. Public reports and session evidence have changed. The
verification JSON omits private artifact-version identifiers. Its source description
and numeric version counters remain. Session evidence retains the original structure,
timestamps and captured wording with targeted path and identifier redactions.
Included CSV files retain the original columns, rows and bytes. Their file paths are generic relative output
names, not personal filesystem paths.

## Limits

Three seeds show repeatability, not the unassessed ten-seed stability criterion.
Search boxes overlap. Site counts come from coordinates, not box names. Both 8V82
and 8V8A are ligand-bound intermediate templates, not an activated/desensitized
pair. Historical figures and frozen protocols retain old state labels. Read them
with the [errata](docs/review_record.md).

The combined report records three of four control pairs recovering the deposited
pose at rank 1. I34/8V82 failed there but recovered at rank 2. Short-contact flags
remain in the tables. No wet-lab experiment, MD or free-energy calculation is
supplied. No experimental pore-bound blocker control was available in this study.

Hydroxybupropion alpha7 activity was not verified in the reviewed sources. This is
not proof that it was never measured or is inactive. HB-O-glucuronide is a candidate
with unresolved linkage. Human target exposure and both causal hypotheses remain
unresolved. Historical exposure arithmetic is exploratory, not a human occupancy
measurement. Exact historical searches and full screening records are unavailable.
This is not a reproducible systematic review.

The supplement was interrupted and relaunched. An agent deleted 12 original
failure receipts and 12 partial logs. They are irretrievably lost. The incident
record and reviewed redacted session derivative remain attached to the result.
This must not be described as a clean run.

## How this was built

AI coding agents did much of the preparation, execution, analysis, checking and
writing under Rolf's direction. Rolf directed the research question and supplied
literature leads. The records describe automated chemistry, geometry, checksum
and citation checks, including corrections to earlier agent conclusions. They do
not document which calculations Rolf independently checked by hand. No completed
faculty review or peer review is recorded. Rolf's manual review and contribution
statement are still needed before publication.

Cleanup did not generate new docking or experimental results. It removed private
metadata, duplicate manuscript exports and bundles containing private records. No new inspection
tool or docking driver was retained.

## License and citation

[MIT](LICENSE) covers the repository's original material. Third-party papers,
software and deposited coordinates retain their own terms. No Vina binary or
third-party paper is redistributed here. The manuscript identifies primary sources.
Template attribution: Burke et al. (2024), *Structural mechanisms of alpha7
nicotinic receptor allosteric modulation and activation*, Cell,
DOI 10.1016/j.cell.2024.01.032. PDB identifiers used across the studies are 8V82,
8V8A, 8V89 and 7EKP.

There is no project DOI or public raw-data deposit yet. Cite the actual repository
revision for this draft and primary papers for their experimental findings.
Do not describe the manuscript as published.
