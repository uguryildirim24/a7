# Parent bupropion at α7: corrected docking, controls, and what it does and does not show

Scope: **parent bupropion only**. Hydroxybupropion was not docked and is not discussed here as a
docking result. No score anywhere below is converted to Ki, IC₅₀, occupancy or clinical effect, and
no pose below is an experimental structure. Protocol and success criteria were frozen in
`PROTOCOL_FROZEN.md` before any parent pose was generated.

## 1. Three defects found and fixed before results

**RMSD measurement was wrong, and the earlier "Vina failed pose recovery" conclusion was false.**
`analyse_validation.py::sym_rmsd` computed a truncation length in its first branch and never used it,
then truncated the cost matrix with `linear_sum_assignment(D[:n,:n])` while the docked coordinates
still carried Meeko's polar hydrogens and the reference had hydrogens removed — matching hydrogens to
heavy atoms and silently dropping trailing reference heavy atoms. Re-measured with chemically valid
correspondence (CCD element/bond graph from the deposited entry, Meeko `REMARK SMILES IDX` mapping,
heavy atoms only, symmetry-aware, computed in place with **no alignment**), all twelve original Vina
top poses recover the deposited geometry at ≤ 2.0 Å. Two independent implementations agree to the
digit. Vina is therefore the pose-validated engine here and was used; no third method was tried.

**Box label was being read as anatomical location.** The original "lumen" box was 27 × 27 × 39 Å, so
the bupropion pose reported as a lumen result sits 11.96 Å off the pore axis with an atom 0.03 Å
outside the box face, contacting M1 and M2–M3-loop residues at a subunit interface. Location is now
measured, never inferred from the box.

**A three-residue frame shift in the site definition.** The M2 motif `EKISLGITVLLSLTVFMLLVAE` begins
at E260, not S263, and an earlier alignment mapped its first residue to S263 — displacing every ring
label three residues toward the intracellular side and the outer-pore box centre by 4.8 Å. Ring
positions are now mapped positionally from observed residue IDs and the identity of all ten named
residues is asserted in all five chains: **50/50 checks pass** in 8V82, 8V8A, 8V89 and 7EKP. This also
verifies the numbering offset independently — 8V82/8V8A/8V89 use mature numbering (UniProt − 23),
7EKP uses UniProt numbering.

## 2. Controls (fresh runs, 3 seeds each)

Prepared ligand is the docking **input** (origin-centred, so it carries no information about the
answer); the **deposited** copy in the receptor frame is the reference. Protonation states match the
preparations used in the originally validated campaign.

| ligand | receptor | input | seeds ≤ 2.0 Å (top pose) | top-pose RMSD (Å) |
|---|---|---|---|---|
| EPJ (epibatidine) | 8V82 | protonated | 3/3 | 0.428 – 0.442 |
| EPJ | 8V8A | protonated | 3/3 | 1.292 – 1.295 |
| I33 (EVP-6124 analogue) | 7EKP | protonated | 3/3 | 0.586 – 0.606 |
| I34 (PAM) | 8V8A | neutral | 3/3 | 0.614 – 0.696 |
| I34 | 8V82 | neutral | **0/3** | 6.359 – 6.373 |
| EPJ | 8V82 / 8V8A | neutral (extra condition) | 3/3, 3/3 | 0.370 – 1.287 / 0.240 – 0.248 |
| I33 | 7EKP | neutral (extra condition) | 3/3 | 0.538 – 0.545 |

**C1 met: 4 of 5 ligand–receptor pairs pass at top pose**, against a threshold of ≥ 4 of 5. The 2.0 Å
criterion was not relaxed.

**The one failure, diagnosed specifically.** I34 in 8V82 recovers the deposited pose at **rank 2**,
0.745 – 0.766 Å, in 3 of 3 seeds. The rank-1 pose that displaces it is 6.36 Å away and scores only
**0.109 kcal/mol** better (−7.565 vs −7.456) — far inside Vina's own scoring resolution. The five I34
copies are 19.3 – 31.2 Å apart, so this is a placement inversion within one pocket, not a different
site. This supports a scoring **misranking in these runs**: the search does locate the deposited geometry,
but the function does not put it first. It does not establish that the preparation is correct in every
respect, and RMSD alone does not establish that the two poses occupy the same pocket — 6.36 Å is
smaller than the 19.3 Å inter-copy spacing, which rules out a different copy but does not resolve
sub-pocket identity. The same ligand and preparation do recover at rank 1 in 8V8A.

**Duplicate identical-input check passes exactly.** The two byte-identical inputs used here are the
corrected run's own pair, SHA-256 `bcbdfcb72e03d363d07eb10fafe1745c3986972768e072cc6566f7e8aa8a618b`
(not the original worker's pair, `7e662f0e…c12d0f7ba`, which is a separate historical file). Same seed
and same region give Δscore = **0.000000** kcal/mol and top-pose RMSD = **0.000000** Å. This establishes that the corrected pipeline is
deterministic for identical input bytes. It is *consistent with* the earlier +1.193 / −6.823 split
having been a map-race artefact rather than anything about bupropion, but it does not re-run those
files and so does not close that anomaly by direct repetition.

## 3. Parent bupropion poses

Protonated R and S (the amine is **secondary**, pKa ≈ 7.9), in 8V82 (activated) and 8V8A
(desensitized), in the outer-pore and mid-pore regions, 3 seeds each — 24 runs, all completed.
Pose agreement is computed modulo the receptor's **C5 symmetry** (operators derived from the structure
by Cα superposition of chain A onto each chain, not an idealised 72° rotation) and the ligand's graph
automorphisms, in place.

| enantiomer | receptor | region | score (kcal/mol) | SD | C5 clusters | pairwise RMSD (Å) | location |
|---|---|---|---|---|---|---|---|
| R | 8V82 | mid-pore | −5.614 | 0.008 | 1 | 0.074 – 0.093 | pore lumen |
| R | 8V8A | mid-pore | −5.543 | 0.013 | 1 | 0.076 – 0.128 | pore lumen |
| R | 8V8A | outer-pore | −5.256 | 0.017 | 1 | 0.063 – 0.085 | pore lumen |
| S | 8V8A | mid-pore | −5.278 | 0.020 | 1 | 0.079 – 0.123 | pore lumen |
| S | 8V82 | outer-pore | −5.770 | 0.079 | 1 | 0.116 – 0.223 | lateral interface |
| S | 8V82 | mid-pore | −5.473 | 0.436 | 2 | 0.049 – 20.18 | mixed |
| R | 8V82 | outer-pore | −6.196 | 0.279 | 3 | 2.464 – 6.242 | lateral interface |
| S | 8V8A | outer-pore | −5.207 | 0.314 | 3 | 2.979 – 12.808 | mixed |

**Five of eight conditions give a single C5-aware pose cluster across three seeds**, with pairwise
RMSD below 0.25 Å. Three do not. With three seeds this is **repeatability, not stability** — the
ten-seed stability criterion C3 was not assessed and is not claimed.

No pose contains a steric clash: **zero receptor–ligand heavy-atom pairs below 2.2 Å** across all 24
runs, with minimum heavy-atom distances of 2.70 – 3.39 Å. Absence of clashes is a narrow check — it
rules out overlapping atoms and nothing more, and is not evidence that a pose is energetically or
physiologically plausible.

## 4. Site inspection: what the parent poses actually contact

Location is measured against each structure's own verified rings and its local lumen radius
(4.2 – 4.6 Å at the −1′/2′ gate, 6.9 – 8.5 Å at 13′–17′). Lumen poses sit at radial fractions
0.07 – 0.64 of the local lumen radius with **M2-span contact fractions** of 0.91 – 1.00; lateral
poses sit at 1.49 – 2.02 with fractions 0.46 – 0.60. This fraction counts contacts with residues in
the M2 span (UniProt 260–281); **side-chain orientation was not verified**, so it should be read as
"M2 contacts", not as confirmed pore-facing contacts.

**In the four conditions that gave a single C5-aware cluster** (R mid-pore in 8V82 and 8V8A, R
outer-pore in 8V8A, S mid-pore in 8V8A), the two enantiomers occupy different depths:

* **R** contacts L270, S271, T273, V274 — the 9′–13′ mid/upper M2 rings, in both receptor states;
* **S** contacts S263, I266, T267 (and E260/G259 in 8V8A) — the 2′–6′ narrow end.

This pattern is **not** established for S in the two mixed conditions: S mid-pore in 8V82 split 2
seeds on-axis at axial −27.2 against 1 lateral seed, and S outer-pore in 8V8A gave three clusters (2
lumen, 1 lateral). Those mixed outcomes are retained in the tables and are not averaged away.

Taken together, the pore-lumen poses recover **all five of the key residues Duarte 2021 names from its
docking stage — S263, I266, T267, T273, V274 — plus L277 from its Table 1**. L278 appears only in the
lateral interface poses, never in a lumen pose.

## 5. What this does and does not reproduce from the literature

**Reproduced.** An independent protocol, on deposited human cryo-EM structures, places protonated
parent bupropion inside the M2 lumen in contact with the same pore-lining residues that Duarte 2021
reported from a rat homology model — including all five residues it lists as key contacts from its
docking stage (S263, I266, T267, T273, V274), plus L277 from its post-MD Table 1. That the two agree on residue identity despite sharing neither
receptor model nor engine is the substantive positive result here.

**Not reproduced, and not attempted.** This is a **different protocol**, not a reproduction: Duarte
2021 used a Prime homology model of **rat** α7 built from human α4β2 **5KXI** (48.47% identity),
**Glide SP then XP in a 12 Å cube**, then **100 ns Desmond membrane MD** and MM-GBSA. Here: deposited
human structures, Vina 1.2.7, no MD, no MM-GBSA. Their Table 1 values (bupropion ΔG −37.5 ± 3.07
kcal/mol) are MM-GBSA energies and are **not comparable** to the Vina scores above; no ranking
comparison against their seven-compound series was made or should be inferred.

**The scoring does not prefer the lumen.** In the activated state 8V82 the lateral interface poses
score better than the lumen poses (mean −5.98 vs −5.46 kcal/mol; best lateral −6.49). Only in the
desensitized state 8V8A do lumen poses dominate the sampled set (11 of 12 runs). A pore assignment
therefore does **not** follow from the scores; it follows from where the poses are, which is why
location is reported separately from score throughout.

## 6. Limits, stated plainly

* Three seeds per condition is repeatability. Stability was not assessed.
* One box-sizing variant (anatomical region + ligand extent) was run; the tight variant and the
  orthosteric reference region were deliberately not run in this bounded pass. Neutral parent forms
  were not run.
* Vina's default scoring is typed-atom based and **ignores the partial charges** in its input, so the
  neutral/protonated distinction here is one of typing and polar-hydrogen count, not electrostatics.
  The earlier "site physics" diagnosis remains an **untested hypothesis**, not a finding.
* One lateral pose has a single atom 0.03 Å outside its box face; it is reported as lateral, not
  excluded and not relabelled.
* Across 22 deposited human α7 entries the complete non-polymer inventory is 9Z9, CA, CLR, EPJ, I33,
  I34, IVM, NAG, NCT, POV, R16, XG3, YLI, YLR — **no pore-bound blocker**. There is no experimental
  α7 pore pose for any blocker to validate a pore assignment against. Agreement with Duarte 2021 is
  agreement between two models, not confirmation against measurement.
* The seven-compound apparent-IC₅₀ ranking panel and the active-versus-decoy separation from the
  earlier design are **not** used as gates: the panel mixes two measured IC₅₀ values with five
  single-concentration inversions, and the decoys are unassayed rather than established non-binders.

## 7. Standing conclusions on the parent

1. Parent bupropion **experimentally inhibits α7** — IC₅₀ 54 µM on α7 Ca²⁺ influx and Kᵢ 63 µM against
   [³H]imipramine (Vázquez-Gómez 2014, PMID 25016090), reproduced as ~48% inhibition at 50 µM in
   native rat CA1 interneurons (Duarte 2021, PMID 33668529). This is measured pharmacology and does
   not depend on any docking result.
2. The **precise α7 binding site is not directly established.** The luminal assignment rests on
   radioligand competition plus homology-model docking; no deposited α7 structure contains a
   pore-bound blocker.
3. Docking here **does** produce repeatable, clash-free parent poses inside the M2 lumen contacting
   the published residues — but it does not prefer them on score in the activated state, and a
   modelled pose is not an observed one.
4. **Hydroxybupropion α7 binding remains unknown**, unchanged and unaddressed by any of the above.
