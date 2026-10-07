# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this directory is

Not a software codebase. It is the **delivered, frozen output** of a computational study plus a
hypothesis manuscript: molecular docking of parent bupropion and its metabolites against the human
α7 nicotinic acetylcholine receptor (cryo-EM structures **8V82** and **8V8A**, both epibatidine/PNU-120596 complexes that Burke et al.
characterise as desensitized intermediates — 8V8A is virtually identical to 8V82 and neither is a
fully activated state, so they are NOT an activated/desensitized pair; **8V89** = resting, **7EKP**
also used as validation controls). There is no application to build, no test suite,
no server. Work here is reading, checking, analysing, and editing prose/data — not regenerating results.

**The docking pipeline source is not in this directory.** Drivers and analysis scripts
(`analyse_validation.py`, the job runners) were run elsewhere; the reports reference a working tree at
`/path/to/project/outputs/`
(referenced, not verified present). The **frozen protocols** live *inside the bundles*:
`PROTOCOL_FROZEN.md` (parent) and `MATRIX_FROZEN.md` (metabolite), frozen before any pose was
generated. Do not re-dock or "regenerate" anything here; if a run is genuinely needed, it happens in
that pipeline, not in this delivery.

## Three layers (this is the structure)

1. **Parent bupropion study** — `parent_docking_findings.md`, `parent_bupropion_poses.sdf`,
   `parent_pose_in_receptor.png`, `parent_docking_inputs_and_poses.tar.gz` (self-contained: receptors,
   maps checksums, control results, deposited reference CIFs, `PROTOCOL_FROZEN.md`). Parent only —
   hydroxybupropion is **not** docked in this layer.
2. **Combined metabolite study** — `combined_*`, `metabolite_delivery_*`, `hb-oglu-*`, `INCIDENT_*`.
   This is the checksummed delivery (`metabolite_delivery_SHA256SUMS.txt` covers exactly these 16 files).
   `combined_bundle.tar.gz` is the full 1720-entry self-contained bundle (manifests, `MATRIX_FROZEN.md`,
   `STATUS.txt`, per-job outputs).
3. **Literature review + manuscript** — `bupropion_receptor_evidence.csv` (104 obs / 84 papers, one
   row per observation), `bupropion_receptor_evidence_map.md`, `bupropion_alpha7_hypothesis_draft.md`
   (`.pdf`/`.docx` are renderings of the `.md` — edit the `.md`), `hypothesis_novelty_and_submission_review.md`.

## Data model (combined metabolite layer)

The reports are the authoritative narrative; the CSV/JSON/SDF are the evidence. Keep these consistent
when editing — the reports assert exact counts and they must not drift:

- `combined_metabolite_poses.csv` — **672** rank-1 rows (one per job: species × form × region × state × seed).
- `combined_poses_ALL_MODES.sdf` — **12,282** saved coordinate modes (= the SDF record count).
- `combined_log_evaluated_scores.csv` — **13,426** printed mode-table rows; of these **1,144** are
  "log-only" (score printed, coordinates never emitted, never re-run).
- `combined_by_measured_site.csv` — **154** batch/species/form/state/site groups (not a mode count);
  `combined_representative_complexes.tar.gz` holds **154** complexes; `combined_complex_coverage.json`
  is a 154-element array covering them.
- `combined_clash_flagged.csv` — **13** rank-1 short-contact poses; `combined_clash_allmodes.csv` — **93** modes.
- Panel: **22 species / 28 chemical forms** (distinct — species with two protonation forms contribute
  multiple forms). Jobs: **672 met/parent + 12 controls = 684**.
- Engine: **AutoDock Vina 1.2.7**, exhaustiveness 32, `energy_range=3.0`, seeds `20240601/02/03`
  (3 per region-state). A pose's `measured_site` comes from its coordinates, and search boxes overlap
  deliberately — **never read a pose's location off the box it was searched in.**
- Receptor numbering: 8V82/8V8A/8V89 use mature numbering (UniProt − 23); 7EKP uses UniProt numbering.

## Useful commands

Several files are large (30 MB SDF, 2.4 MB CSV, 5–55 MB tarballs). Do not `cat` them — inspect.

```bash
# Verify the metabolite delivery is intact (all 16 must report OK)
shasum -a 256 -c metabolite_delivery_SHA256SUMS.txt
```

```bash
# Inspect a data file without loading it: headers, row counts, a slice
head -1 combined_metabolite_poses.csv          # column names
tail -n +2 combined_metabolite_poses.csv | wc -l   # row count (expect 672)
```

```bash
# List a bundle's contents without extracting (extract into the scratchpad, never here)
tar tzf combined_bundle.tar.gz | head
```

```bash
# Column-aware CSV queries (csvkit / duckdb / python-pandas are the natural tools)
python3 -c "import pandas as pd; d=pd.read_csv('combined_metabolite_poses.csv'); print(d['measured_site'].value_counts())"
```

## Non-negotiable scientific guardrails

Every report in this directory is deliberately, repeatedly careful about the following. Preserve these
distinctions in anything you write, edit, or summarise — violating one silently corrupts the delivery's
central claim, which is that it does **not** overclaim.

- **Vina scores are docking scores in kcal/mol. They are NOT Ki, IC₅₀, affinity, occupancy, preference,
  or clinical effect.** Never convert them, never rank compounds by them as if by affinity. Vina's
  default scoring ignores input partial charges (protonation sets H-bond atom typing and sterics only).
- **Docking locates poses; it does not establish binding, functional antagonism/agonism/PAM activity,
  or clinical causality.** H1 (α7 → depersonalization) and H2 (shared α7 → seizure mechanism) are
  **hypotheses**, not findings. Nothing here proves the drug–receptor–circuit–symptom chain.
- **Hydroxybupropion α7 activity is unknown.** "Not measured in these panels" ≠ "never measured" ≠
  "inactive." Do not relabel α4β2 / α3β4 results as α7 results.
- **The HB-O-glucuronide supplement batch was interrupted and relaunched — never a clean run.** 12
  original failure receipts/logs were wrongly deleted and are unrecoverable (`INCIDENT_supplement_interruption.md`).
  Never describe the supplement as clean; **never delete failure receipts/logs** to satisfy a check.
- **Thresholds are frozen:** 2.0 Å RMSD pose-recovery success, < 2.2 Å heavy-atom clash flag. Do not
  relax them. Clash-flagged poses are retained and labelled, never promoted or substituted for rank-1.
  Absence of clashes is a narrow geometric check, not evidence of plausibility.
- **3 seeds = repeatability, not stability** (the 10-seed C3 stability criterion was not assessed).
- **Search negatives are not absence of literature.** "No record returned" ≠ "never studied." Avoid
  "first," "novel," "no evidence exists" from search counts alone.
- The HB-O-glucuronide linkage is a **source-depicted candidate, not proven** (the N-linkage hypothesis
  is retained). Structures were built from **primary chemistry**, not trusted database SMILES
  (e.g. DrugBank DBMET03478 has the wrong formula).
- **Nothing has been submitted or sent to anyone**; the manuscript needs human/faculty review. Do not
  imply submission, acceptance, priority, or completed peer review.

## Provenance

`metabolite_delivery_verification.json` records the delivery status and independent verification;
manifest SHA-256 gates are `FINAL` (main `72b31dab…`, supplement `69642f35…`). Every combined row
traces to a real driver receipt (`returncode=0`, `ok=True`, `cached=False`, output SHA matches). Keep
provenance and the incident disclosure attached to any derivative — they are part of the result, not
boilerplate.
