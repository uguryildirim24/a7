# Bupropion metabolites at human α7: panel, states, regions and job matrix — frozen before results

Target: human α7 nAChR, deposited cryo-EM structures 8V82 (activated) and 8V8A (desensitized).
This is **not** a proteome-wide target search: it reports where each metabolite docks *within α7*.
No score is converted to Ki, IC₅₀, affinity rank, occupancy or measured binding, and no absence of a
pose is evidence of non-binding.

Engine: AutoDock Vina 1.2.7, SHA-256 `823c2bbacf26d72183861322345f0a89736aca66c8e81054c66f93af5ad623f1`
— byte-identical to the binary used for the validated parent work. Vina's default scoring is
typed-atom based and **does not read input partial charges**; formal charges below set atom typing and
polar-hydrogen count, and no electrostatic conclusion is drawn from them.

## 1. Inventory and evidence class

Circulating (plasma) evidence:
* **OH-bupropion** (hydroxybupropion), the 2-(3-chlorophenyl)-3,5,5-trimethylmorpholin-2-ol;
  active circulating metabolite. Panel: (2R,3R) and (2S,3S).
* **threohydrobupropion** — (1S,2S) and (1R,2R); **erythrohydrobupropion** — (1R,2S) and (1S,2R).
  Stereo-descriptor assignment per Teitelbaum PMC4831137. Active circulating metabolites.
* **threo/erythro-4′-OH-hydrobupropion** — the docked structures are the **4′-hydroxylated**
  threo/erythro isomers, whose 4′ regiochemistry Sager PMC5026406 confirmed by NMR against
  synthesised standards in **urine-isolated** material. Connarn PMC5132048 detects a hydroxylated
  threo/erythrohydrobupropion (its "M3") in **plasma**, but its hydroxylation position is
  **unresolved** — the mass alone establishes that *a* hydroxylated hydro-metabolite circulates, not
  that these specific 4′ isomers are the plasma species. Structural identity (4′, from urine) and
  specimen (a hydroxy-hydro-metabolite of unknown position, in plasma) are kept separate; the earlier
  claim that Connarn's M3 establishes the exact 4′ structures in plasma was wrong and is withdrawn.
* **4′-OH-bupropion** — Sager PMC5026406 metabolite M1, NMR-confirmed; reported in plasma and urine.
* **β-D-glucuronides** of threo- and erythrohydrobupropion — Teitelbaum PMC4970645 quantified intact
  diastereomers in urine and **unequivocally reassigned** the stereochemistry of mislabelled
  commercial standards; the formal correction to Gufford is PMC5074468 (threo 1R,2R / 1S,2S labels
  swap; EGLUC1 = 1S,2R, EGLUC2 = 1R,2S). Corrected elution order and assignment, verbatim from
  PMC4970645: (1S,2S)-threo, (1S,2R)-erythro, (1R,2R)-threo, (1R,2S)-erythro.

Urine / downstream:
* **m-chlorohippuric acid** — glycine conjugate of m-chlorobenzoic acid.
* **m-chlorobenzoic acid** — human radiolabel study PMID 3107223.

In the inventory but **not docked — existence vs. dockable-structure separated per case**:
* **hydroxybupropion glucuronide** — its **existence is established**, not merely inferred: Gufford
  PMC4810769 directly observed two HB-glucuronide LC-MS peaks from incubations of **(R,R)- and
  (S,S)-hydroxybupropion** (the hydroxy metabolite itself, not the parent drug), matching urine
  (albeit without authentic HB-glucuronide standards), and Connarn PMC5132048 assigns its **M2** to
  hydroxybupropion glucuronidation. What is not resolved is the **linkage and position**: the Petsalo
  thesis (Oulu, pp. 44–48) proposes an **N-linkage** for the morpholine-hydroxy conjugates (its
  M12/M13) from their hydrolysis resistance, and O-linkage for others — these are **hypotheses to
  reconcile against later authentic-standard work, not adopted facts**, and neither linkage is
  assumed here. Because no single connectivity is established, no honest single structure can be
  docked. The earlier "tertiary hydroxyl is chemically atypical" argument was unsupported and is
  **removed**; hydrolysis resistance is in fact evidence bearing on N- vs O-linkage, not on whether
  the conjugate forms.
* **Sulfate conjugates** — **identified in a primary source**: Petsalo 2007 (PMID 17639567,
  DOI 10.1002/rcm.3117) reports **three urinary sulfate conjugates** (to the aromatic-hydroxy
  metabolite and to hydroxy-plus-hydrogenation metabolites). Not docked because the exact conjugation
  positions must be read off the primary figures before a structure could be built. The earlier
  statement that "sulfates were not identified in the cited sources" was **false** and is corrected.
* **Further glucuronides** — the Petsalo thesis (printed p. 44) enumerates the 20 urinary metabolites
  as **12 glucuronides + 3 sulfates + 1 glycine conjugate + 4 phase-I products**; the abstract's
  "eight glucuronide conjugates" are those **newly reported** there, not a total. Connarn's **M4–M7**
  are **proposed stereoisomeric hydro-glucuronide conjugates**; whether they are species *additional
  to* the four reassigned hydro-glucuronide diastereomers, or the same four, is **not established** by
  the MS data, so they are not counted as four extra species.
* **Connarn M1 (ring-hydrated bupropion)** — proposed from product-ion spectra only; position
  tentative.
* **Sager M2** — reported absent from clinical samples; **Sager M3** — urine, minor, not resolved to
  a single positional isomer.
* **Dihydroxylation products** (aromatic-ring and central-methyl, Petsalo, first reported there) —
  positions not resolved to single structures here.

## 1a. Species accounting (wording correction, panel unchanged)

The 24 chemical forms cover **20 species, of which 2 are the parent references** R- and S-bupropion.
The panel therefore contains **18 metabolite species**, not 20, and they are:

| group | species | n |
|---|---|---|
| hydroxybupropion (morpholinol) | (2R,3R), (2S,3S) | 2 |
| threohydrobupropion | (1S,2S), (1R,2R) | 2 |
| erythrohydrobupropion | (1R,2S), (1S,2R) | 2 |
| 4′-OH-bupropion | R, S | 2 |
| threo-4′-OH-hydrobupropion | (1S,2S), (1R,2R) | 2 |
| erythro-4′-OH-hydrobupropion | (1R,2S), (1S,2R) | 2 |
| hydro β-D-glucuronides | threo (1S,2S), (1R,2R); erythro (1S,2R), (1R,2S) | 4 |
| downstream acids | m-chlorohippuric acid, m-chlorobenzoic acid | 2 |

**This 18-species docking panel does not cover every reported bupropion metabolite, and is not
claimed to.** Petsalo 2007 alone detected 20 urinary metabolites; bupropion, its three active
metabolites and their urinary conjugates account for only ~23% of the dose (Sager PMC5026406), with
the 4′-OH series adding ~24% of urinary drug-related material. The panel contains the metabolites
whose full stereochemistry and connectivity are resolved in primary sources. Reported-but-not-docked,
each with its specific evidence gap: the **hydroxybupropion glucuronide** (exists per Gufford/Connarn;
linkage N- vs O- unresolved), **three sulfate conjugates** (Petsalo; positions to confirm), the
**further glucuronides** — the Petsalo thesis counts 12 glucuronides among the 20 urinary
metabolites — and Connarn's M4–M7 (count and regiochemistry not established), and the
**dihydroxylation products** (positions unresolved). "Glucuronides" in the
results below therefore means the **four reassigned hydro-glucuronide diastereomers only**. No
stereochemistry or linkage is invented for any structure whose configuration is not fixed in a
primary source.

**Enumerated stereoisomers vs. per-stereoisomer human evidence.** The panel enumerates each
constitutionally-identified metabolite's stereoisomers as chemically explicit, verified structures
(§2). That is not the same as human evidence resolving *each individual stereoisomer* as a distinct
detected species. Where a source resolves individual configurations — the hydro-glucuronide
diastereomers reassigned with authentic standards (Teitelbaum PMC4970645/PMC5074468), the parent and
hydro enantiomers by stereoselective assay (Teitelbaum PMC4831137), Gufford's (R,R)/(S,S)-HB
incubations — that per-stereoisomer evidence exists. Where a source gives a **group-level**
structural identification — e.g. Sager's NMR fixing the **4′-OH position** of a threo/erythro
hydro-metabolite — it establishes the constitution, **not** that every modelled stereoisomer of that
scaffold is separately demonstrated in humans. The docked stereoisomers are therefore best read as
chemically explicit configurations of experimentally identified metabolites, with per-stereoisomer
human confirmation varying by species and noted rather than assumed uniform.

Database SMILES were **not** trusted: DrugBank DBMET03478 carries methyl groups where the glucuronide
hydroxyls belong and formula C22H34ClNO4 instead of C19H28ClNO7. Every structure here was built from
the primary chemistry and verified independently (below).

Primary sources for the inventory: Teitelbaum PMC4831137 (hydro stereo-descriptors); Sager
PMC5026406 (4′-OH series, NMR); Connarn PMC5132048 (plasma metabolites, M2 = HB-glucuronidation);
Teitelbaum PMC4970645 and correction PMC5074468 (reassigned hydro-glucuronide stereochemistry);
Gufford PMC4810769 (HB-glucuronide LC-MS existence); Petsalo 2007 PMID 17639567 and the Petsalo Oulu
thesis (urinary sulfates, glucuronide count, N-/O-linkage hypotheses); PMID 3107223 (m-chlorobenzoic
acid).

## 2. Chemical verification performed before docking

* Formula and net charge computed per form; hydro glucuronides all give the correct neutral
  C19H28ClNO7.
* Stereocentres located **by named chemical position** (C1 = carbinol carbon bearing OH and aryl;
  C2 = adjacent carbon bearing N and CH₃; morpholinol C2/C3 equivalently), never by atom index —
  atom-index comparison after SMILES canonicalisation produced spurious mismatches.
* CIP codes at those named positions match the source labels for all species.
* Stereochemistry re-derived **from 3D coordinates** after embedding and MMFF optimisation, and
  checked against the 2D assignment by the same named-position rule: **24/24 forms agree**.
* β-D sugar identity confirmed by cleaving the aglycone C1–glycosidic O bond and matching the
  released fragment to β-D-glucopyranuronic acid (PubChem CID 441478): C6H10O7,
  InChIKey `AEMOLEFTQBMNLQ-QIUUJYRFSA-N`, all four conjugates.

## 3. Chemical forms at pH 7.4 (24 forms, 20 species)

Dominant form per species, with basis and uncertainty recorded in `panel_spec.json`:
* secondary *tert*-butylamines (threo/erythro and their 4′-OH analogues) → **ammonium**, pKa ≈ 9;
* bupropion and 4′-OH-bupropion → **ammonium** (bupropion pKa ≈ 7.9; moderate uncertainty);
* hydroxybupropion morpholinol → **ammonium and neutral both run**; no measured pKa was located in
  the cited sources, so the neutral fraction is genuinely unresolved (HIGH uncertainty);
* 4′-OH-bupropion additionally run as a **phenolate/ammonium zwitterion** sensitivity condition.
  DrugBank DBMET03472 lists ChemAxon-**predicted** acidic pKa 6.12 / basic 8.32 and net physiological
  charge 0. These are in-silico predictions, not measured pKa values; no population fraction is
  assigned to any form, and none is inferred from docking scores.
* carboxylic acids (m-chlorohippuric, m-chlorobenzoic) → **carboxylate**;
* glucuronides → **carboxylate + ammonium zwitterion**, net charge 0.

## 4. Search regions — four anatomically distinct sites, so nothing is forced into the pore

Uniform declared sizing rule: **anatomical extent + largest-ligand ensemble extent (11.6 Å, the
threo-glucuronide over 20 conformers) + 2 Å**, applied identically to every region.

| region | anchor | verified in receptor frame |
|---|---|---|
| mid-pore | 5-fold axis × M2 rings 2′–13′ | 1121 / 1179 receptor atoms, 723 / 716 M2-span atoms |
| outer-pore | 5-fold axis × M2 rings 13′–17′ | 640 / 614 receptor atoms, 421 / 405 M2-span atoms |
| orthosteric | deposited EPJ copy, chain A | 290 / 307 receptor atoms; reference fits with 6.4 Å margin |
| lateral I34 pocket | deposited I34 copy, chain A | 363 / 350 receptor atoms; reference fits with 6.2 Å margin |

All eight region–state boxes pass atom-coverage and, where a deposited ligand anchors them,
reference-containment checks. A box is a search region, not a location claim: attribution is by
measured axial/radial position, local lumen radius and residue contacts, never by which box ran.

## 5. Job matrix

* 24 chemical forms × 8 region–state combinations × **3 seeds** (20240601–20240603) = **576 runs**.
* Matched parent references R- and S-bupropion (ammonium) are included **inside** that matrix under
  identical regions, settings and seeds.
* Controls revalidated in the **new** boxes, since the sizing rule changed: EPJ in the orthosteric
  region and I34 in the lateral region, both receptor states, 3 seeds = **12 runs**.
* exhaustiveness 32, `--num_modes 20`, `--cpu 1`. Twenty modes are **requested**; the number
  actually written is whatever survives Vina's default 3 kcal/mol energy window, so it varies per run
  (observed range so far 4-20; several controls wrote only 3-4). The per-run count is reported, never
  assumed, and a narrow mode set is itself information about how tightly the energy window closes
  around one pose.
* The frozen mid-pore boxes (~29.8 x 29.8 x 31 A, about 27,600 A^3) exceed Vina's default heuristic
  volume, so those runs emit `Search space volume is greater than 27000 Angstrom^3`. This follows
  directly from the declared sizing rule -- the largest ligand's 11.6 A extent added to a lumen
  already ~17 A across -- and the regions are **left exactly as frozen**. It is recorded as a
  sampling-completeness caveat for the pore regions, alongside the absence of any pore pose-recovery
  control. Observed in 45 of 45 mid-pore logs and 0 of the others; outer-pore boxes stay under the
  threshold. Technical success is determined by exit code, a completely parsed output and matching
  provenance; warnings are reported separately and never gate a pass.
* Pore regions contain no deposited ligand, so **no pose-recovery control is possible there** — this
  is stated rather than substituted for.
* I34/8V82's known behaviour (deposited pose recovered at rank 2, ~0.75 Å, rank-1 displaced by
  0.109 kcal/mol) is preserved as the expected result, not treated as a new failure.

## 6. Analysis, fixed now

Pose agreement modulo the receptor's **C5 symmetry** (operators from Cα superposition of chain A onto
each chain, not an idealised 72° rotation) **and** each ligand's own stereochemistry-preserving graph
automorphisms, computed in place with no ligand-only alignment. Per pose: axial and radial position
against verified M2 rings, local lumen radius, radial fraction, M2-span contact fraction (side-chain
orientation not verified, so reported as M2 contacts), residue contacts with chain IDs, minimum
receptor distance and clashes below 2.2 Å. All lateral, ambiguous and failed outcomes are retained
and reported as such.

MD and free-energy calculations are **not** an automatic next step; feasibility is assessed after
these docking results are in hand.
