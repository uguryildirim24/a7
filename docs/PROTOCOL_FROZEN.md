# Corrected parent-bupropion docking protocol — frozen before results

Scope: **parent bupropion only**, at human α7. Hydroxybupropion is out of scope.
No score is converted to Ki, IC50, occupancy or clinical effect. Nothing here
establishes that a directly observed α7 parent-bupropion pose exists.

Frozen: before any parent pose was generated. Controls and criteria below were fixed
first; none was adjusted afterwards.

## 1. Engine choice, and why it is not a third method

AutoDock Vina 1.2.7 (binary from the original worker workspace, checksum recorded in
`run_manifest.json`).

The earlier switch toward AutoDock4 was motivated by an apparent pose-recovery failure
that was **false**. The original `analyse_validation.py::sym_rmsd` computed `n` in its
first branch and never used it, then truncated the cost matrix with
`linear_sum_assignment(D[:n,:n])` while the docked coordinate array still carried
Meeko's polar hydrogens and the reference had hydrogens removed — so hydrogens were
matched against heavy atoms and trailing reference heavy atoms were dropped.

Re-measured with chemistry-valid correspondence (`corrected/rmsd_check.py`: CCD
element/bond graph from the deposited entry, Meeko `REMARK SMILES IDX` mapping, heavy
atoms only, symmetry-aware, computed in place with no alignment), the original Vina
runs recover all twelve co-crystal top poses at ≤2.0 Å. AutoDock4 recovers 2 of 5, and
two of its three failures are the zero-interaction runs produced by the map-readiness
race. Vina is therefore the pose-validated engine available, and is used as such.

## 2. Known engine limitation, stated rather than tested away

Vina's default scoring function is typed-atom based (gauss, repulsion, hydrophobic,
hbond, rotatable-bond penalty) and **does not read the partial charges** written into
the input PDBQT. Neutral and protonated parent inputs therefore differ only through
atom typing and polar-hydrogen count, not through electrostatics. The neutral vs
protonated comparison below is reported on that basis and does **not** constitute a
test of charge effects. "Site physics" remains an untested hypothesis, not a diagnosis.

## 3. Site definition, from primary evidence and receptor geometry

Duarte 2021 (PMID 33668529) built a homology model of **rat** α7 with Prime from human
α4β2 **5KXI** (48.47% identity), sought the site "along the ion channel from the
extracellular region (L278, 16' ring) to the cytoplasmic side (S263, 2' ring)", docked
with **Glide SP then XP in a 12 Å cube**, then ran **100 ns Desmond membrane MD** and
MM-GBSA. Their Table 1 places bupropion's post-MD contacts at **L278, L277, V274**
(ΔG −37.5 ± 3.07 kcal/mol). Vázquez-Gómez 2014 (PMID 25016090) provides the measured
pharmacology — IC50 54 µM on α7 Ca²⁺ influx, Ki 63 µM against [³H]imipramine — with
the luminal assignment coming from radioligand competition plus homology-model docking.

A Vina/AutoDock recreation is therefore a **different protocol**, not a reproduction of
Duarte 2021: different receptor model (deposited human cryo-EM structures, not a rat
homology model from an α4β2 template), different search engine and scoring function,
and no membrane MD or MM-GBSA rescoring stage.

M2 ring positions are located per structure by motif alignment with the identity of
every named residue asserted in all five chains (E260, S263, I266, T267, L270, S271,
T273, V274, L277, L278 — 50/50 checks pass in 8V82, 8V8A, 8V89, 7EKP). This also
verifies the numbering offset: 8V82/8V8A/8V89 use mature numbering (UniProt − 23),
7EKP uses UniProt numbering. The pore axis is the pentamer 5-fold axis.

## 4. Search regions, pre-declared, with the box caveat

Measured local lumen radius (distance from the 5-fold axis to the nearest receptor
heavy atom in a ±2 Å axial slab): 4.2–4.6 Å at the −1'/2' gate, rising to 6.9–8.5 Å at
13'–17'.

Two parent search regions are run, both declared in advance, so that no conclusion
rests on one box choice:

* **variant A (anatomical region + ligand extent)** — lumen over the M2 ring span
  expanded by the parent's own maximum extent, the conventional AutoDock sizing rule.
* **variant B (tight)** — lateral half-width = max local lumen radius over the span
  + 2 Å.

A grid box is a search region, not a location claim, and receptor atoms outside a box
still contribute to the energies evaluated inside it — a sparsely occupied box is not
an empty or invalid one. At this receptor's dimensions no box can enclose the lumen
without also admitting the adjacent intersubunit crevices, so **site attribution is
never taken from the box**. The original run's "lumen" box was 27 × 27 × 39 Å, which
is why a pose 11.96 Å off the pore axis, with an atom 0.03 Å outside the box face, was
still reported as a lumen result.

The orthosteric region is also run as a non-pore reference, since the α7 site of the
parent is not directly established by any deposited structure: across 22 human α7
entries the complete non-polymer inventory is 9Z9, CA, CLR, EPJ, I33, I34, IVM, NAG,
NCT, POV, R16, XG3, YLI, YLR — **no pore-bound blocker**.

## 5. Pose attribution, measured not labelled

For every pose: centroid axial coordinate against that structure's verified rings,
centroid radial distance, local lumen radius at that height, radial fraction
(radius / local lumen radius), pore-facing contact fraction (share of contacted
residues that are M2 pore-lining, UniProt 260–281), residue contacts within 4.0 Å,
minimum receptor distance and clash count below 2.2 Å.

The earlier fixed 5 Å centroid-radius cut is **not** used to classify; with measured
wall radii of 4.2–8.5 Å varying by state and height it is not definitive anatomy. It
is reported as a reference value only. A pore claim requires radial fraction ≤ 1.0
**and** pore-facing fraction ≥ 0.5, with the underlying numbers shown either way.

## 6. Ligands

Parent bupropion only. Both enantiomers explicitly (**R** and **S**): the drug is a
racemate and both α7 measurements above were made on the racemate, so neither
enantiomer is privileged.

Bupropion's amine is **secondary** (the nitrogen bridges the α-carbon and a *tert*-butyl
group); an earlier draft of this section called it tertiary. Its pKa ≈ 7.9 leaves it
substantially protonated at pH 7.4, so the **protonated** form is the one run here.

Receptor states: 8V82 (activated, epibatidine + PNU-120596) and 8V8A (desensitized).

### 6a. Execution scope of this first bounded pass

Deliberately narrower than the matrix the rest of this document would permit, so the
parent-only finish line stays bounded and nothing runs on autopilot:

* parent: **protonated R and S**, outer-pore and mid-pore regions (variant A sizing),
  8V82 and 8V8A, **3 independent seeds** per condition — 24 parent jobs;
* controls: the 5 co-crystal recoveries, **3 seeds** each — 15 jobs;
* the duplicate identical-input check — 2 jobs.

The neutral forms, the tight variant-B box and the orthosteric reference region are
**not** run automatically. They are follow-ups to be requested only if this pass raises
a specific question that they would answer.

Three seeds do not satisfy the ten-seed stability rule in §8, and no result below is
described as if they did. Three-seed agreement is reported as **repeatability across
three seeds**, which is weaker evidence than stability and is labelled that way
wherever it appears.

## 7. Controls, run fresh in this corrected run

1. **Co-crystal pose recovery**, 5 independent seeds each: EPJ in 8V82 and 8V8A,
   I34 in 8V82 and 8V8A, I33 in 7EKP. Prepared ligand is the docking INPUT; the
   deposited copy is the REFERENCE. Inputs are origin-centred by construction, so the
   starting coordinates carry no information about the answer.
2. **Duplicate identical-input check**: a byte-identical pair of this run's own parent
   inputs — `bup_S_prot.pdbqt` and `bup_S_prot_DUP.pdbqt`, both SHA-256
   `bcbdfcb72e03d363d07eb10fafe1745c3986972768e072cc6566f7e8aa8a618b` — run at the same
   seed in the same region; scores and poses must be identical.

   This is **not** a re-run of the original anomaly's files. Those were
   `lig/bupropion_probe_prot.pdbqt` and `lig/panel_bupropion_prot.pdbqt` (both SHA-256
   `7e662f0ebb5793d5384298d494680a86773d8dd8539adab2f6b11cac12d0f7ba`), which scored
   +1.193 and −6.823 against maps still being written. A freshly built,
   enantiomer-specific pair is used here instead, so this check establishes that the
   corrected pipeline is deterministic for identical bytes. It is *consistent with* the
   earlier split having been a map-race artefact; it does not by itself re-test those
   files and does not close that anomaly by direct repetition.
3. **Seed stability**: ≥10 independent seeds for every parent condition.

## 8. Success criteria, fixed now

* **C1** engine accepted for geometry if ≥4 of 5 co-crystal controls give a majority-seed
  top-pose RMSD ≤ 2.0 Å. No retroactive relaxation to 2.5 Å.
* **C2** duplicate identical inputs must give |Δscore| < 0.01 kcal/mol and pose RMSD
  < 0.01 Å. Failure here is a technical fault, not a result.
* **C3** a parent condition is "stable" if top-score SD ≤ 0.5 kcal/mol across ≥10 seeds
  and ≥50% of seed top poses lie within 2.0 Å of the modal pose; otherwise it is
  reported as unstable search. **This pass runs 3 seeds, so C3 is not assessed** — the
  three-seed result is reported as repeatability, not stability.
* **C3a** pose agreement is computed **modulo the receptor's C5 symmetry**. α7 is a
  homopentamer: the same pose occupied in five symmetry-related subunits is one binding
  mode, not five, and would otherwise register as false instability. The five operators
  are derived from the structure itself by least-squares superposition of chain A's Cα
  atoms onto each of the five chains, not from an idealised 72° rotation, so
  pseudo-symmetry is handled correctly. Ligand atom correspondence is simultaneously
  minimised over the ligand's own graph automorphisms (for bupropion, the three
  equivalent *tert*-butyl methyls). RMSD between two poses is then the minimum over the
  5 receptor operators × the ligand automorphisms, computed **in place** — no
  ligand-only alignment is ever used, since that would discard exactly the positional
  information being tested. The occupied chain ID and the full contact list are retained
  for every pose regardless of which operator matched.
* **C4** a pore-lumen attribution requires the §5 thresholds. Off-site and lateral poses
  are retained and reported as such, never relabelled.

Not used as gates, by explicit instruction and because both are unsound: the
seven-compound apparent-IC50 ranking panel (it mixes two measured IC50s with five
single-concentration inversions) and the active-vs-decoy separation (the decoys are
unassayed, so they are not established non-binders).

## 9. Map integrity (AutoDock4 path, retained but not on the parent critical path)

All nine corrected map sets pass: autogrid4 exit 0, "Successful Completion" in the
.glg, 13 maps plus .fld, per-map point count equal to prod(NELEMENTS+1) from its own
header, all values finite and non-trivial, SHA-256 recorded per file, directory then
set read-only. Existing complete sets are verified and reused; nothing is deleted, and
a set that fails verification is left in place while a rebuild goes to a new path.
The original run's six zero-interaction outputs are excluded from all interpretation.
