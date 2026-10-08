# Data access and historical provenance

## Included evidence

The original literature CSV, five combined docking CSVs, complex-coverage JSON,
combined and parent SDFs, representative-complex archive, four figures and
historical research audits remain in the repository. These data files are unchanged
from HEAD before cleanup. All original rows and columns remain, including printed log-only modes
and short-contact flags. The README gives a Python standard-library query.

Relative paths in the tables are historical output names. They do not imply that
all referenced coordinates, logs or receipts are included. No public raw-data
fetch command or supported docking driver exists here.

| Table | Row meaning | Important columns |
| --- | --- | --- |
| `combined_metabolite_poses.csv` | One rank-1 pose per job | `batch`, `species`, `form`, `receptor`, `region_box`, `seed`, `pose_file`; `measured_site` is a supplied geometric classification; `score_top` is a Vina score in kcal/mol; distances ending `_A` are angstrom |
| `combined_log_evaluated_scores.csv` | One printed mode-table row | `batch`, `tag`, job identifiers, `log_mode_rank`, `vina_score_kcal_mol`, `coordinates_emitted`, `note`, `prefix_matches_pose` |
| `combined_by_measured_site.csv` | One batch/species/form/template/site group | `n_poses`, `n_unique_seeds`, `searched_from_boxes`, `n_distinct_modes_C5_2A`; groups are not total coordinate modes |
| `combined_clash_flagged.csv` | One flagged rank-1 pose | `pose_file`, job identifiers, `n_clashes_below_2p2A`, `min_receptor_dist_A` |
| `combined_clash_allmodes.csv` | One flagged saved mode | `batch`, `tag`, `mode_rank`, `is_rank1`, `n_pairs_below_2p2A`, `min_receptor_dist_A` |

A chemical form is a species/form pair, not a distinct `form` label alone.
Search boxes overlap. Never assign location from `region_box`. Short contacts use
the frozen below-2.2 angstrom criterion. Historical receipt-verification fields
record the earlier automated audit, not a new verification of raw files.

## Large artifacts and private bundles

Two bundles are omitted because they contain private metadata, not simply because
of their size. No reviewed replacement deposit or stable download identifier is
available yet. They were not copied elsewhere during cleanup. Their historical
hashes remain in the delivery records.

| Artifact | Original bytes | Availability |
| --- | ---: | --- |
| `combined_bundle.tar.gz` | 57,491,883 | Removed for privacy; reviewed replacement needed from Rolf |
| [combined saved coordinates](../combined_poses_ALL_MODES.sdf) | 30,477,421 | Included unchanged |
| [representative complexes](../combined_representative_complexes.tar.gz) | 43,955,863 | Included unchanged |
| `parent_docking_inputs_and_poses.tar.gz` | 5,332,746 | Removed for privacy; reviewed replacement needed from Rolf |

The combined SDF and representative complexes exceed 5 MB. A release or external
store would be suitable, but no real deposit exists to point to. They therefore
remain in the tree rather than losing tracked evidence. Rolf can arrange a deposit
and add its verified identifier before removing them from source git.

A clean clone can inspect the saved coordinates, but cannot rerun the original
campaign or repeat the complete receipt audit. Source PDB entries alone do not
reproduce receptor preparation, ligand preparation or search boxes.

Do not publish the old bundles unchanged. They contain local workspace paths and
an unredacted incident capture. The parent archive also contains platform metadata
and shelved map tooling. Remove private metadata, preserve scientific failure
records and disclose export changes. Never recreate lost records as originals.

## Historical verification

`metabolite_delivery_SHA256SUMS.txt` is the unchanged September 26, 2026 delivery
manifest, not a checksum manifest of the public tree. Its report, incident and
session-evidence hashes identify older bytes. Two private bundles are absent.
Running the full manifest against this tree will not pass.

`metabolite_delivery_verification.json` retains the historical verification fields
and hashes, with private artifact-version identifiers removed. The source description
and all 15 numeric `saved_version` counters remain. Status labels refer to the
original delivery, not current scientific validation. The frozen
protocols were extracted unchanged. Their hashes and corrections are in the
[review record](review_record.md).

The public session JSON is a redacted derivative linked to the original capture's
hash in the incident disclosure. It preserves the original structure, timestamps,
wording and commands. Only private paths and identifiers are replaced. Nested
JSON escaping is retained. It does not restore the 12 lost failure receipts or
12 partial logs.

Working-tree deletion does not remove old git objects. History review is handled
separately before publication.

## Deposit requirements

Rolf must select a deposit and confirm availability and reuse terms. Include actual
hashes, receptor and chemical-source attribution, control failures, clash flags
and the interruption disclosure. Correct figure titles to template IDs. Keep any
surviving original failure records. Disclose the missing interrupted records.
Add a real identifier here only after deposit verification.
