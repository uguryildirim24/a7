# Bupropion metabolites vs α7 nicotinic receptor — combined docking report

**Modeled docking study. Not experimental structures, not measured binding. Docking
scores are AutoDock Vina scores in kcal/mol; they are NOT Ki/IC50/affinity/occupancy and
carry no preference or clinical interpretation.** This report describes *where within α7*
each modeled ligand can be placed by docking, classified by the measured coordinates of
the pose — nothing about whether it binds, how tightly, or with what functional effect.

## 1. Scope and what this is / is not

- **Question addressed:** given the bupropion metabolite/parent panel and two α7
  cryo-EM conformations, where do docked poses land within the receptor (pore lumen,
  the EPJ orthosteric-adjacent pocket, the I34 intersubunit PAM pocket, or other
  interface), by measured coordinates?
- **Not addressed, and not inferable from this study:** functional antagonism, agonism
  or PAM activity; α7 activity of hydroxybupropion or any metabolite; any Ki/IC50/
  affinity/occupancy; mediation of bupropion-associated depersonalization (H1) or the
  link to seizure susceptibility (H2). Docking cannot prove any of these. No wet-lab
  experiment was performed.
- **No experimental pore-bound blocker control was included in this study.** The
  pore-region poses are modeled placements; they are not validated against a
  co-crystallised α7 channel blocker. This is a statement about the study's controls,
  **not** a claim that the anatomical pore itself is unestablished.
- Vina does **not** read input **partial charges**, but protonation is not
  scoring-neutral: it sets hydrogen-bond **donor/acceptor atom typing**, which feeds
  Vina's hydrogen-bond term (AutoDock Vina 1.2.7 `scoring_function.h` includes
  hydrophobic and H-bond terms; see the official FAQ,
  https://autodock-vina.readthedocs.io/en/latest/faq.html). So protonation/charge forms
  affect sterics, torsions, and H-bond atom typing — but no electrostatic or affinity
  conclusion is drawn from them.

## 2. Panel and design

- **22 species / 28 chemical forms** (these are distinct): 22 species = 18 metabolites
  + 2 parent references (R-/S-bupropion) + 2 supplement HB-O-glucuronide species. 28
  chemical forms = 24 main forms + 4 supplement forms (HB-O-glucuronide (2R3R)/(2S3S) ×
  net-0 zwitterion / net-1 anion). Species with two protonation forms (e.g.
  hydroxybupropion) contribute multiple forms.
- **Receptor states:** α7 nAChR, PDB **8V82** (activated) and **8V8A** (desensitized).
- **Search regions (per state):** mid-pore, outer-pore, orthosteric (ortho / EPJ), and
  lateral I34 pocket — 4 regions × 2 states = 8 region-states. Boxes deliberately
  **overlap**; ligand-inflated pore boxes extend laterally into the I34 pocket, so a
  pose's site is taken from its **measured coordinates**, never from the box it was
  searched in.
- **Seeds:** 3 per region-state. **Docking:** AutoDock Vina 1.2.7, exhaustiveness 32,
  `energy_range=3.0`.
- **Job counts:** 576 main metabolite jobs + 96 supplement jobs = **672 met/parent
  jobs**; plus **12 shared co-crystal control jobs** (EPJ, I34 × 2 states × 3 seeds).
  684 docking jobs total.

## 2a. Panel inventory, evidence class, protonation, and coverage gaps

The panel contains metabolites whose full stereochemistry and connectivity are resolved
in primary sources, plus two source-depicted candidates (below). It does **not** cover
every reported bupropion metabolite, and no claim is made that it does. Evidence class is
recorded per species; enumerating a metabolite's stereoisomers as chemically explicit
structures is **not** the same as human evidence resolving each individual stereoisomer.

| Chemical class | Species (docked) | Specimen / evidence class | Primary source |
|---|---|---|---|
| Parent reference | R-bupropion, S-bupropion | parent drug (reference, not a metabolite) | — |
| Hydroxybupropion (morpholinol) | (2R,3R), (2S,3S) | plasma, active circulating; stereoselective assay | Teitelbaum PMC4831137 |
| Threohydrobupropion | (1S,2S), (1R,2R) | plasma, active circulating | Teitelbaum PMC4831137 |
| Erythrohydrobupropion | (1R,2S), (1S,2R) | plasma, active circulating | Teitelbaum PMC4831137 |
| 4′-OH-bupropion | R, S | plasma + urine; NMR-confirmed (M1) | Sager PMC5026406 |
| threo-4′-OH-hydrobupropion | (1S,2S), (1R,2R) | 4′ regiochemistry by NMR in **urine**; a plasma hydroxy-hydro metabolite of **unresolved position** also detected | Sager PMC5026406 (structure); Connarn PMC5132048 (plasma M3, position unresolved) |
| erythro-4′-OH-hydrobupropion | (1R,2S), (1S,2R) | as above | Sager PMC5026406; Connarn PMC5132048 |
| Hydro β-D-glucuronides | threo (1S,2S),(1R,2R); erythro (1S,2R),(1R,2S) | **urine**; intact diastereomers quantified, stereochemistry reassigned with authentic standards | Teitelbaum PMC4970645; correction PMC5074468 |
| **HB-O-glucuronide candidate** (supplement) | (2R,3R), (2S,3S) | **source-depicted O-linked candidate; linkage NOT proven.** HB-glucuronide existence shown in vitro (peaks matching urine, no authentic standards) + assigned plasma M2 | Teitelbaum PMC4970645 Fig 1 (O-depiction); Gufford PMC4810769 (in-vitro (R,R)/(S,S)-HB incubations); Connarn PMC5132048 (M2) |
| Downstream acids | m-chlorohippuric acid; m-chlorobenzoic acid | urine (glycine conjugate); human radiolabel | m-Cl-benzoic acid PMID 3107223 |

Species count: **20 metabolite species + 2 parent references = 22 species** (28 chemical
forms). **Per-stereoisomer evidence varies:** individual configurations are resolved for
the hydro-glucuronide diastereomers (authentic standards) and the parent/hydro
enantiomers (stereoselective assay), and Gufford used (R,R)/(S,S)-hydroxybupropion
directly; but where a source gives a **group-level** identification (e.g. Sager's NMR
fixing the 4′-OH position of a threo/erythro hydro scaffold), it establishes the
constitution, not that every modelled stereoisomer is separately demonstrated in humans.

**HB-O-glucuronide qualification (supplement):** built at the morpholinol OH with the
physical aglycone configuration preserved (verified by in-silico cleavage back to the
named hydroxybupropion). The linkage is **not proven** — the Petsalo N-linkage hypothesis
(hydrolysis resistance of the morpholine-hydroxy conjugates M12/M13) is retained as
unresolved, not overturned. Quantitation in the source is by hydrolysis-subtraction
without authentic HB-glucuronide standards. Because the morpholinol pKa is unresolved,
both the net-0 zwitterion and net-1 anion were docked. The intact-conjugate CIP label at
C2 flips on O-glycosylation while physical configuration is preserved (a labelling
artefact, documented).

**Protonation — the exact modeled forms per species (from the combined table), as
preparation assumptions (no measured metabolite pKa, no population fractions claimed):**
- Parent (BUP_R, BUP_S), threo/erythrohydrobupropion (THB_1R2R, THB_1S2S, EHB_1R2S,
  EHB_1S2R), and threo/erythro-4′-OH-hydrobupropion (T4pOH_1R2R, T4pOH_1S2S, E4pOH_1R2S,
  E4pOH_1S2R): **amine_cation only.** These nitrogens are **secondary amines**; the
  protonated form was prepared on the assumption that the parent secondary-amine
  pKa ≈ 7.9 (and the secondary hydroamine pKa ≈ 9) leaves them substantially protonated
  at pH 7.4. These are **preparation assumptions from the parent/analogue chemistry, not
  measured metabolite pKa values.**
- Hydroxybupropion (HB_2R3R, HB_2S3S): **amine_cation + neutral** — the morpholine
  secondary-amine pKa is treated as **unresolved**, so both forms were docked.
- 4′-OH-bupropion (OH4p_R, OH4p_S): **amine_cation + zwitterion_phenolate_ammonium** —
  the phenol pKa is **predicted, not measured**, so a phenolate/ammonium zwitterion
  sensitivity form was included alongside the ammonium form.
- Hydro β-D-glucuronides (TGLUC_1R2R, TGLUC_1S2S, EGLUC_1R2S, EGLUC_1S2R):
  **zwitterion_carboxylate_ammonium** (glucuronic-acid carboxylate deprotonated at
  pH 7.4, amine protonated).
- Downstream acids (mCBA, mCHA): **anion** (carboxylate deprotonated at pH 7.4).
- HB-O-glucuronide candidates (HB_2R3R_OGLU, HB_2S3S_OGLU): **net-0 zwitterion + net-1
  anion** — morpholinol pKa unresolved, both docked.
- Vina ignores input partial charges; these forms set H-bond atom typing and polar-H
  count, and no electrostatic or affinity conclusion is drawn from them.

**CSV identifier map** (`combined_metabolite_poses.csv` `species` → chemical class; `form`
values in parentheses): BUP_R/BUP_S = parent bupropion (amine_cation); HB_2R3R/HB_2S3S =
hydroxybupropion (amine_cation, neutral); THB_1R2R/THB_1S2S = threohydrobupropion,
EHB_1R2S/EHB_1S2R = erythrohydrobupropion (amine_cation); OH4p_R/OH4p_S = 4′-OH-bupropion
(amine_cation, zwitterion_phenolate_ammonium); T4pOH_1R2R/T4pOH_1S2S =
threo-4′-OH-hydrobupropion, E4pOH_1R2S/E4pOH_1S2R = erythro-4′-OH-hydrobupropion
(amine_cation); TGLUC_1R2R/TGLUC_1S2S = threo hydro-glucuronide, EGLUC_1R2S/EGLUC_1S2R =
erythro hydro-glucuronide (zwitterion_carboxylate_ammonium); mCHA = m-chlorohippurate,
mCBA = m-chlorobenzoate (anion); HB_2R3R_OGLU/HB_2S3S_OGLU = HB-O-glucuronide candidate
(net0_zwitterion, netminus1_anion).

**Reported but NOT modeled (coverage gaps), each with its evidence gap:**
- **Sulfate conjugates** — Petsalo 2007 reports **three urinary sulfates**; conjugation
  positions must be read from the primary figures before a structure can be built.
- **Further glucuronides** — the Petsalo thesis enumerates the 20 urinary metabolites as
  **12 glucuronides + 3 sulfates + 1 glycine conjugate + 4 phase-I products**; the
  abstract's "eight glucuronides" are those **newly reported**, not a total. Connarn's
  **M4–M7** are proposed stereoisomeric hydro-glucuronides whose count/regiochemistry vs
  the four reassigned diastereomers is **not established** — not four extra proven species.
- **HB-glucuronide linkage/regiochemistry** (N- vs O-, position) unresolved; the O-linked
  candidate is docked as such, the N-linkage hypothesis retained.
- **Connarn M1** (ring-hydrated), **Sager M2** (reported absent clinically) / **M3**
  (urine, isomer unresolved), and **dihydroxylation products** — positions unresolved.
- Not every reported human metabolite, and not every stereoisomer, is experimentally
  established; the panel is explicitly a resolved-structure subset.

Primary sources (open-access identifiers): Teitelbaum PMC4831137
(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4831137/); Sager PMC5026406
(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5026406/); Connarn PMC5132048
(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5132048/); Teitelbaum PMC4970645
(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4970645/) and correction PMC5074468
(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5074468/); Gufford PMC4810769
(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4810769/); Petsalo 2007 PMID 17639567,
DOI 10.1002/rcm.3117 (https://doi.org/10.1002/rcm.3117) and the Petsalo Oulu thesis
(pp. 44–48; https://oulurepo.oulu.fi/bitstream/10024/35925/1/isbn978-951-42-9441-9.pdf); m-chlorobenzoic acid human radiolabel PMID 3107223
(https://pubmed.ncbi.nlm.nih.gov/3107223/). Database SMILES (e.g. DrugBank DBMET03478,
wrong formula C22H34ClNO4) were **not** trusted; every structure was built from primary
chemistry and verified independently.

## 3. Provenance and integrity (all gates FINAL)

| Batch | Jobs | Manifest SHA-256 | Status |
|---|---|---|---|
| Main metabolite + controls | 588 | `72b31dabc450802ab0cab2bcc8334084c9114409ae7752d0d8bf0a28addab26a` | FINAL (validate_final: []) |
| Supplement HB-O-glucuronide | 96 | `69642f35dda400d4dec88f9f9aa34f0c5fd92d47152a36077fccbd2ae30b636a` | FINAL |
| Combined met/parent | 672 | (delivery table) | FINAL |

- Every one of the 672 combined rows is verified against a real driver receipt
  (`returncode=0`, `ok=True`, `cached=False`, output SHA matches). Supplement: 96/96
  receipts rc0/ok/cached=False, output hashes match, 96 unique tags.
- Combined bundle triple gate = **FINAL** (main FINAL + supplement FINAL + combined
  FINAL), packaged as a metadata-free archive.

## 4. Saved coordinate modes vs log-only evaluated scores

Vina prints the mode-table scores to the log (the printed modes), but writes coordinates
only for the modes inside the default `energy_range=3.0` kcal/mol window.
"**ALL_MODES**" throughout this delivery means **all SAVED coordinate modes**. "Log-only"
means a **printed mode-table score whose coordinates were never emitted** — not every
optimizer-evaluated candidate.

- Combined **saved coordinate modes = 12,282** (main metabolite 10,752 + supplement
  1,530); this is exactly the combined SDF record count. The 141 shared-control saved
  modes are excluded from the combined met/parent SDF and retained in the raw control
  outputs.
- Combined **log-only scores = 1,144** (main 756 + supplement 388): printed mode-table
  docking scores whose **coordinates were never emitted**. They are retained in
  `combined_log_evaluated_scores.csv` (13,426 printed mode-table rows for the 672
  met/parent jobs) and were **not re-run** to recover coordinates. The 12 controls'
  printed/log-only scores stay in `metabolite_log_evaluated_scores.csv`.

## 5. Where the poses land (measured site, descriptive only)

Rank-1 measured-site distribution across the 672 combined poses (a diagnostic tally,
**not** occupancy or preference):

| Measured site | Rank-1 poses |
|---|---|
| I34 pocket (intersubunit PAM) | 252 |
| other interface | 172 |
| pore lumen | 145 |
| EPJ pocket (orthosteric-adjacent) | 103 |

**154** is the number of batch/species/form/state/measured-site **groups**
(`combined_by_measured_site.csv`); it is not a de-duplicated mode count. Within those
groups the saved `n_distinct_modes_C5_2A` sums to **261 C5-symmetry + ligand-automorphism
distinct modes** (unique-seed accounted). Per-species / per-form placement across both
states is shown in the figures (`combined_full_panel_sites.png`; per-compound coordinate
panels `combined_per_compound_8V82.png` (activated) and `combined_per_compound_8V8A.png`
(desensitized)). Raw counts run at 24 or 48 sampled poses per species (two-form species
= 48) and are **not** C5-deduplicated modes.

These placements are geometric locations only; they do not indicate binding, preference,
or affinity, and no site ranking is inferred from docking scores.

**Sampling caveat.** Mid-pore search boxes exceed Vina's 27,000 Å³ default heuristic
volume and emit the "search space volume is greater than 27000 Angstrom^3" note in every
mid-pore log; this is a sampling caveat, not a pass/fail condition. All jobs ran at
exhaustiveness 32, cpu 1 per job, seeds 20240601/20240602/20240603, 20 modes requested,
and Vina's unchanged default output `energy_range=3.0` kcal/mol.

## 6. Short-contact (clash) geometry flags — retained, never promoted

Threshold: any receptor-heavy / ligand heavy-atom pair **< 2.2 Å** (unchanged). These
are **geometry flags on modeled poses — not failed docking exits and not binding
evidence.** Flagged poses are retained and labelled; alternatives (rank > 1) are kept in
the raw poses and the ALL_MODES SDF and are never substituted for rank-1.

- **Rank-1 flagged poses: 13** (`combined_clash_flagged.csv`) — main 5 + supplement 8:
  - main: TGLUC_1S2S zwitterion(carboxylate/ammonium) ortho — 8V82 s01/s02/s03,
    8V8A s02/s03 (min 1.85–2.00 Å).
  - supplement: HB_2R3R_OGLU net-0 zwitterion ortho 8V82 s01/s02/s03; HB_2R3R_OGLU
    net-1 anion ortho 8V8A s01; HB_2S3S_OGLU net-0 zwitterion ortho 8V82 s01/s02/s03
    and 8V8A s03 (min 1.87–2.17 Å).
- **All-mode flagged saved modes: 93** (`combined_clash_allmodes.csv`) — main 51 +
  supplement 42 (includes rank-1 and alternatives).

## 7. HB-O-glucuronide qualification (supplement)

The HB-O-glucuronide forms are a **source-depicted O-linked candidate** (Teitelbaum
Fig 1), built at the morpholinol OH with the physical aglycone configuration preserved
(verified by in-silico cleavage back to the named hydroxybupropion). **The linkage is
not proven** — the N-linkage hypothesis is retained. Because morpholinol pKa is
unresolved, both the net-0 zwitterion (carboxylate + ammonium) and net-1 anion were
docked. The intact-conjugate CIP label at C2 flips on O-glycosylation (aglycone 2R,3R →
S at C2 in the conjugate) while physical configuration is preserved; this is a CIP
labelling artefact, documented and verified.

## 8. Control note

New-box co-crystal control recovery (top-pose RMSD to the deposited ligand, across the 3
seeds):

| Control | Receptor | Top-pose RMSD (Å) | Outcome |
|---|---|---|---|
| EPJ (epibatidine) | 8V82 | 0.426–0.454 | pass |
| EPJ (epibatidine) | 8V8A | 1.299–1.305 | pass |
| I34 (PAM) | 8V8A | 0.639–0.799 | pass |
| I34 (PAM) | 8V82 | 6.372–6.411 | **fails 3/3 at top pose** |

Three of the four control pairs pass. For **I34 in 8V82**, the correct pose is not the
top-ranked one (top-pose RMSD 6.372–6.411 Å) but is recovered at **rank-2** (0.744–0.783
Å); the rank-2 − rank-1 score gaps are only **0.028 / 0.085 / 0.071 kcal/mol** for seeds
20240601/02/03. This is a concrete, reproducible demonstration that the workflow's
scoring can mis-rank by a fraction of a kcal/mol, and is one more reason no score here is
treated as a preference or affinity statement.

## 9. Incident (record-preservation failure — not a clean run)

The supplement batch was **interrupted and relaunched**; it is not a clean single run.
A healthy runner was wrongly inferred dead from an `os.kill(pid,0)` `PermissionError`,
interrupted, and its 12 in-flight jobs' failure receipts/logs were then **deleted**,
violating the preserve-failures requirement. Those 12 originals are irretrievably lost;
the interrupted matrix jobs were retried by the replacement runner, which produced the
delivered data. Full account: `INCIDENT_supplement_interruption.md`; captured session
evidence: `hb-oglu-interruption-session-evidence.json` (SHA
`21cf235a9c7122452eaafc1a0972823e92f76a69f169221515a86dbc00d1fef0`). Both are included
in the final bundle.

## 10. Relation to the project hypotheses

This study **locates** metabolite poses within α7 conformations. It does **not** provide
evidence for α7 antagonism by bupropion or any metabolite, does **not** establish
hydroxybupropion α7 activity, and does **not** bear on whether α7 inhibition mediates
depersonalization (H1) or connects to seizure susceptibility (H2). Those questions
require direct receptor measurements. Docking scores cannot prove functional antagonism
or clinical causality, and alternative explanations (other nicotinic subtypes,
non-nicotinic mechanisms) remain open.

## 11. Key delivered artifacts

- Tables: `combined_metabolite_poses.csv` (672), `combined_by_measured_site.csv` (154),
  `combined_clash_flagged.csv` (13 rank-1), `combined_clash_allmodes.csv` (93 modes),
  `combined_log_evaluated_scores.csv` (13,426 rows / 1,144 log-only).
- Structures: `combined_poses_ALL_MODES.sdf` (12,282 saved modes),
  `combined_representative_complexes.tar.gz` (154 complexes),
  `combined_complex_coverage.json`.
- Figures: `combined_full_panel_sites.png`, `combined_per_compound_8V82.png`,
  `combined_per_compound_8V8A.png`.
- Provenance: main manifest (`72b31dab…`), supplement manifest (`69642f35…`), incident
  record + session evidence, full metadata-free bundle.
