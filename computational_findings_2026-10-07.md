# Computational and full-text findings — 7 October 2026

Builds on `claim_audit_2026-10-07.md`. I don't repeat it. Nothing in the manuscript, the audit or any
data file was edited; this is the only file written. Scratch scripts are in `/private/tmp/a7_rpt/`
(`exposure.py`, `ties.py`, `box.py`, `best.py`) and rerun with `python3 -I`.

**Tags.** [VERIFIED] I read the source or reran the numbers myself today. [VERIFIED-ADV] an adversarial
checker independently reproduced or re-read it. [REPORTED] carried from one of the sub-analyses, source
named, I did not re-read it. [INFERENCE] reasoning on top of sources, not stated by them.
[UNVERIFIED] could not be checked. Long verbatim source quotes are kept out of this file on purpose
(they sit in the scratch logs under `/private/tmp/a7_exposure_audit/` and
`/private/tmp/a7s/`); numbers are given with the table or section they come from.

**Two things about the inputs you should know.**
1. The manuscript moved after the audit. Commits `05940b2` (Papke sentence), `784dc68` (Grunebaum
   sentence) and `09d56a7` (8V82/8V8A labels) landed today. Everything below is checked against the
   current text, not the baseline.
2. Parts of the multi-agent output reached me cut off mid-sentence: the exposure parameter table after
   the competing-targets row, the tail of the contrast-robustness analysis and its verdict, the end of
   the novelty answer on the four structures, and the completeness critic after its "docking archive is
   not portable" gap. Where that mattered I recomputed from the repo files (marked [VERIFIED]); where I
   couldn't, I say so.

---

## 1. What changed

1. **Dale 2008 (ref 19) is not an error.** The audit's FIX came from reading only the abstract. The full
   text says the comparison group is 8 of 8 depersonalization-disorder patients (2 depersonalization
   only, 6 with dissociative amnesia as well), and it shows the same prepulse-inhibition pattern as
   controls. Strike it from the errors list. The manuscript sentence stands. [VERIFIED]
2. **Grunebaum 2013 (ref 24) is not an error either, just thin, and it is already fixed.** The full text
   names the composite (HDRS-24 "Disturbed Thinking") and reports the null only as a grouped p > 0.1, no
   estimate. Commit `784dc68` already rewrote the sentence. Two inferences inside it should be labelled
   as inferences (§5). [VERIFIED]
3. **The Papke fix (`05940b2`) introduced a new factual error.** The manuscript now says the α4β2
   stoichiometries "were the more sensitive bupropion targets under both conditions." Under coapplication,
   (α4)2(β2)3 had IC50 72 µM, weaker than α7's 46 µM. Only the bath protocol puts all three α4 forms
   ahead of α7. Fix it (wording in §5). [VERIFIED from Table 4; an adversarial re-read of the PMC page
   caught it first]
4. **At therapeutic dosing, parent bupropion does not get near the α7 IC50.** Estimated unbound brain
   concentration at the 300 mg XL peak is 0.10–0.32 µM against 16–54 µM measured IC50s, so 50 to 530
   times too low on central assumptions, 17 to 2,400 times across the full uncertainty range (§2).
5. **Hydroxybupropion is the only therapeutic-dose candidate, and its α7 IC50 is the decisive missing
   number.** Its estimated unbound brain level is about 12 times the parent's (1.2–3.9 µM). It would need
   an α7 IC50 of about 11–35 µM to reach even 10% inhibition, and about 1.2–3.9 µM to reach half. Nobody
   has measured it, as far as I could find (§4).
6. **Docking: 52.8% of the 672 rank-1 poses beat their own rank-2 pose by less than the 0.085
   kcal/mol your I34/8V82 control mis-ranked by.** Among pore-lumen poses it is 98%. I reproduced
   this from the CSVs. It weakens the R,R 12/12 vs S,S 8/12 contrast as a result, and strengthens the
   methodological point (§3).
7. **The parent-pore contradiction is explained by the boxes, with data.** In the combined run the
   parent never has a pore-lumen rank-1 pose in any box. The parent-only run used smaller mid-pore boxes
   and scored about 1 kcal/mol worse. Details and replacement wording in §3.
8. **Novelty: still "not located", with two traps.** A 2024 *Biophys J* paper says bupropion "and its
   metabolites" inhibit α7 (pooled claim, not a measurement), and the Damaj 2004 full text, the one
   place an α7 arm could be hiding, is still unread (§4).
9. **Three corrections to the audit itself.** (a) §4.4 item 2 reasoned that Pandhare's
   "therapeutically-relevant" 112 µM cuts in favour of H1. The arithmetic says the opposite (§2.6).
   (b) §4.3 says Vázquez-Gómez used imipramine competition binding; its abstract also reports
   molecular docking. (c) The audit's totals line (36 OK / 8 / 1 / 2) doesn't match its own table,
   which counts 35 OK, 7 ABS, 2 FT, 1 OK/FT, 2 FIX = 47. Cosmetic.
10. **The `.pdf` and `.docx` renderings of the manuscript are stale** (dated 26 Sep; the `.md` was
    edited 7 Oct). CLAUDE.md says the `.md` is the source. Regenerate before anyone sends one anywhere.

**The overall picture.** The paper is weaker than the September version looked, and the audit's
"reference layer is clean" still holds. What's left is a hypothesis paper whose receptor-level premise
(drug reaches α7 at relevant concentration) fails for the parent at ordinary doses, survives only
conditionally through hydroxybupropion, and whose docking headline doesn't carry biology. What is
solid: every citation and every docking count reproduces; the guardrails are honoured; the unmeasured
experiment is real; and the docking reliability result is reproducible from the delivered files.

---

## 2. The exposure arithmetic

### 2.1 What it computes (and what it doesn't)

```
unbound brain ECF (µM) = total plasma (ng/mL) ÷ MW × fu × Kp,uu
fraction of response blocked = C ÷ (C + IC50)      (slope 1)
```

- `fu` = fraction of drug not stuck to plasma protein. `Kp,uu` = ratio of free drug in brain
  extracellular fluid to free drug in plasma; the receptor sees the free drug. ng/mL ÷ g/mol = µM, no
  other factor. MW 239.74 (parent), 255.74 (hydroxybupropion free base). I found no unit error.
- This is an **arithmetic comparison of reported concentrations with reported in vitro IC50s**. It is
  not occupancy, not a prediction of effect, and it uses no docking score. The slope-1 assumption and the
  assumption that an in vitro IC50 transfers unchanged to brain are mine, not sourced.
- The 450 mg/day figures are the 300 mg figures × 1.5, from the label's linear-kinetics statement.
  [INFERENCE]

### 2.2 Inputs

| Input | Value used | Where it comes from | Tag | Main uncertainty |
|---|---|---|---|---|
| Parent plasma Cmax, XL 300 mg/day, MDD patients at steady state | 81 ng/mL (IQR 68–106) = 0.338 µM | Kharasch/Lenze 2019, PMID 30460996, PMC6465131, Table 1, brand column | [VERIFIED] | Stable-remission MDD, one formulation; IQR not min–max; Cmax is the generous end (dosing-interval averages are about 25% lower) |
| Hydroxybupropion plasma Cmax, same | 1167 ng/mL (IQR 849–1382) = 4.56 µM; about 14× parent | same table | [VERIFIED] | CYP2B6\*6 carriers shift parent up, metabolite down |
| Same, interval averages | parent about 35 ng/mL, hydroxybupropion about 871 ng/mL (AUC/24) | the exposure sub-analysis | [REPORTED] | Derived from the AUC row; I didn't recompute |
| Label's ratio (rejected) | hydroxybupropion peak about 7× parent; AUC about 13× | Wellbutrin XL label §12.3 | [VERIFIED] | Measured ratios are about 14× (Cmax) and about 25× (AUC/24), so the label understates by about 2× |
| Plasma unbound fraction, label | 0.16 (84% bound); hydroxybupropion "similar" (no number) | label §12.3 | [VERIFIED] | Label gives no method |
| Plasma unbound fraction, primary measurement | 0.5 ± 0.1 (R-bupropion), 0.6 ± 0.1 (S-bupropion), 0.5 ± 0.1 (R,R- and S,S-hydroxybupropion); threohydrobupropion 1.0 ± 0.1; erythro 0.7 ± 0.1 | Sager 2017, PMC5164944, Methods (ultracentrifugation) and Table 1 | [VERIFIED] for R-bupropion and R,R-HB cells | **Conflicts with the label by about 3×.** I can't say which is right. Both are carried; neither is picked. ± is lab triplicate scatter, not between-patient spread |
| Brain/plasma unbound ratio Kp,uu | 1.9 parent, 1.7 hydroxybupropion (rat, steady state) | Cremers 2016, PMID 26916207 | [VERIFIED] abstract | **All rat.** Human value unmeasured. Bhattacharya 2023 and Bällgren 2024 give time-varying values below and above this [REPORTED]. My sensitivity range 0.5–3 is an assumption, not sourced |
| α7 IC50, parent only | 16 µM (30-min bath, probed with 60 µM ACh) to 54 µM; also 46 µM (coapplication) | Papke 2011 Table 4 [VERIFIED]; Vázquez-Gómez 2014 abstract [REPORTED] | | Different agonist levels and protocols; I'm not using Papke's fitted slopes |
| Hydroxybupropion α7 IC50 | **Unknown. Not measured in anything I located.** No number assigned | Evidence gap | | "Not located" is not "never measured" and not "inactive" |

### 2.3 Therapeutic dose (XL 300 mg/day, median Cmax)

Reproduced with `exposure.py`. [VERIFIED]

| | Total plasma | Unbound brain (fu 0.16 / fu 0.5) | Times below IC50 16 µM (fu 0.16 / 0.5) | Times below IC50 54 µM (fu 0.16 / 0.5) | Blocked at IC50 16 µM (fu 0.16 / 0.5), then at 54 µM |
|---|---|---|---|---|---|
| Parent | 0.34 µM | 0.10 / 0.32 µM | 156 / 50 | 526 / 168 | 0.6% / 2.0%, 0.2% / 0.6% |
| Hydroxybupropion, **if** its α7 IC50 were 16 or 54 µM (conditional, nothing measured) | 4.56 µM | 1.24 / 3.88 µM | 13 / 4 | 44 / 14 | 7.2% / 19.5%, 2.2% / 6.7% |

Fold-differences that matter:

- **Parent, central cases:** 50× (fu 0.5, IC50 16) up to 526× (fu 0.16, IC50 54) below the IC50.
- **Parent, full envelope** (fu 0.16–0.7, Kp,uu 0.5–3, plasma at the IQR ends): 0.023–0.93 µM, so 17× to
  2,380× below. At 450 mg/day: 0.034–1.39 µM; best case 11.5× below and 8% blocked at IC50 16 µM.
- **Even the most generous corner** (everything high, IC50 16 µM) blocks 5.5% at 300 mg, 8.0% at 450 mg.
- **Time-averaged** rather than peak: parent 0.044–0.139 µM. [REPORTED inputs, my arithmetic]
- **Hydroxybupropion over parent:** about 12× in unbound brain concentration at any fixed fu, because
  total plasma is 14× and Kp,uu is 1.7 vs 1.9.
- **Spans, so you know what drives uncertainty:** Kp,uu range 0.5–3 is a 6× span, plasma binding is 3.1×
  (0.16 vs 0.5), the α7 IC50 range is 3.4× (16 vs 54), peak vs average plasma is about 1.3×. The
  untested rat-to-human brain ratio is the largest single unknown.
- **What the parent would need.** To reach 10% block, total plasma has to be 449–4,732 ng/mL depending
  on fu and IC50 (5.5× to 58× the median Cmax). [VERIFIED, `exposure.py`]
- **What hydroxybupropion would need** at central unbound brain levels: an α7 IC50 of about 11 µM
  (fu 0.16) to 35 µM (fu 0.5) for 10% block; about 1.2 to 3.9 µM for 50%. That is, for even a modest
  therapeutic-dose effect it has to be about as potent at α7 as the parent is (11–35 µM vs the parent's
  16–54 µM), and for a strong effect much more potent. [INFERENCE on measured inputs]

### 2.4 Overdose (parent, case reports)

All concentrations are timed or peak plasma values from case reports, **not** taken at seizure onset, and
several are abstract-level only. The ranges are fu 0.16 → 0.5 at Kp,uu 1.9, slope 1.

| Plasma parent (ng/mL) | Case | Unbound brain (µM) | Blocked at IC50 16 µM | Blocked at 54 µM |
|---|---|---|---|---|
| 274 | XL 300 bottles plus olanzapine, EEG seizures; PMID 40633264 [VERIFIED abstract] | 0.35–1.09 | 2.1–6.4% | 0.6–2.0% |
| 334 | Peak with cardiotoxicity; status epilepticus about 3 h after admission; PMID 24131328 [VERIFIED abstract] | 0.42–1.32 | 2.6–7.6% | 0.8–2.4% |
| 879 | About 16 h, multiple seizures [REPORTED] | 1.11–3.48 | 6.5–17.9% | 2.0–6.1% |
| 1114 | 5.7 g SR, Tmax 8.25 h, seizure status not in abstract; PMID 20230334 [REPORTED] | 1.41–4.41 | 8.1–21.6% | 2.5–7.6% |
| 1400 | 12 g, 4 h, status epilepticus [REPORTED] | 1.78–5.55 | 10.0–25.7% | 3.2–9.3% |
| 3200 | 4.2 g, 6 h, seizures and cardiac arrest [REPORTED] | 4.06–12.68 | 20.2–44.2% | 7.0–19.0% |

- Overdose parent plasma is 3.4× to 39.5× the therapeutic Cmax. Hydroxybupropion in the two cases that
  report it (4302 and 4718 ng/mL) gives 4.6–5.0 µM unbound brain at fu 0.16 and 14–16 µM at fu 0.5. The
  hydroxybupropion α7 IC50 is still unknown, so those are conditional only.
- There is also a conference-abstract value (27,359 ng/mL parent, about 14 h) that would give 35–108 µM
  unbound. Lower tier, uncorroborated, not used for anything. [REPORTED]

### 2.5 What this means for which paper is defensible

- **H1 as "parent bupropion at ordinary doses blocks α7": not defensible.** Fifty-fold or more
  short of the IC50 on central assumptions. The audit asked whether there is ever enough drug; for the
  parent at 300–450 mg/day, no, by arithmetic. [INFERENCE on verified inputs]
- **H1 as "hydroxybupropion at ordinary doses blocks α7": defensible only as a conditional prediction.**
  Exposure is plausible (1.2–3.9 µM free in brain, up to about 15 µM in the corners at 450 mg/day), so the
  claim reduces to: does hydroxybupropion inhibit α7 below roughly 11–35 µM? That is the experiment your
  paper says should be run, and the arithmetic now tells you the threshold at which the answer would
  matter. This is the version I would build the paper around.
- **Overdose, parent: arithmetic permits partial block.** Roughly 2–44% at IC50 16 µM, 1–19% at 54 µM. That
  is a partial effect under the favourable assumptions, not an obvious seizure mechanism.
- **A pattern that cuts against the shared-mechanism hypothesis (H2) for the parent:** two of the
  seizure cases (274 and 334 ng/mL) have estimated parent unbound brain levels of only 0.35–1.3 µM, which
  is at most about 8% block at 16 µM. Either the sampled concentrations differ from those at seizure onset
  (they are timed or peak values, not onset values), or the parent-via-α7 route is not what drives
  those seizures. I can't separate these. [INFERENCE]
- **Duarte 2021's "clinical relevance" is not about bupropion.** It tested all seven antidepressants at
  20 µM because that is a brain level reached with fluoxetine. For bupropion the arithmetic above gives
  0.03–1.4 µM. [VERIFIED from the Duarte text; arithmetic mine]
- **The manuscript sentences to change.** §5 says "No new exposure model, dose conversion or occupancy
  estimate is produced here," and §8 repeats it. If you add this, both change, and so does "sufficient
  target exposure" in the abstract (keep it, but state it as conditional on hydroxybupropion).

### 2.6 Pandhare 2017 and the audit's inference

Pandhare's abstract calls hydroxybupropion's 5-HT3A IC50 (112 µM) "within its therapeutically-relevant
concentrations." Their full text justifies that by saying hydroxybupropion plasma levels run 10 to 100
times the parent's. Measured total Cmax is 4.56 µM, so 112 µM is about 25 times above plasma and 29–90
times above estimated unbound brain (1.1–3.3% block at the central cases). It is not within
therapeutic range by these numbers. The audit's §4.4 item 2 said that applying the same reasoning to
16–54 µM α7 "cuts in favour of H1." It cuts against it: both sets of IC50s are far above achievable
levels for ordinary dosing. [VERIFIED arithmetic; Pandhare full text read]

Other receptors, not to be read as α7: 5-HT3A IC50 87 µM (parent), 112–113 µM (hydroxybupropion);
α3β4\* 1.8 µM (parent); hydroxybupropion at α4β2 3.3 µM (S,S) and 31 µM (R,R). [REPORTED]

### 2.7 Caveats, once

Kp,uu is rat only. fu has an unresolved 3× conflict (label vs primary measurement). Cmax is the favourable
end. Overdose values are timed, not at seizure, and mostly abstract-level. Threohydrobupropion
(fu about 1.0 per Sager; AUC about 7× parent per the label [VERIFIED]) and erythrohydrobupropion are
absent from this arithmetic and their α7 activity is unmeasured; the threo metabolite may have the
largest free exposure of any compound, so it deserves its own line if you expand this.

---

## 3. The docking re-analysis

### 3.1 The mis-ranking floor, applied to all 672 jobs

Floor: your I34/8V82 control recovered the deposited pose at rank 2, with rank-2 minus rank-1 score gaps
of 0.028 / 0.085 / 0.071 kcal/mol across the three seeds (combined report §8). I computed the same gap
(rank 2 minus rank 1) for every job from `combined_log_evaluated_scores.csv`. All 672 jobs matched the
poses CSV; none has a negative gap; all have a rank 2. [VERIFIED, `ties.py`; reproduced by the
adversarial check]

| Gap below | Jobs | Share |
|---|---|---|
| 0.028 | 248 | 36.9% |
| 0.071 | 327 | 48.7% |
| 0.085 | 355 | 52.8% |

Median gap 0.0745; maximum 5.48. By rank-1 site, jobs inside 0.085: pore lumen 142 of 145 (98%), I34
pocket 104 of 252 (41%), other interface 92 of 172 (53%), EPJ pocket 17 of 103 (17%). [VERIFIED-ADV]

**Wording.** Say "within the control's observed mis-ranking gap," not "statistical ties." The floor is
three gaps from one ligand, one pocket and one receptor. It shows mis-ranking can happen at that scale;
it is not an error bar, and applying it to other ligands, boxes and receptors is an extrapolation. [from
the adversarial check]

### 3.2 The headline jobs

Midpore, 24 hydroxybupropion jobs. All numbers in this table are [VERIFIED] from the CSVs.

| | R,R-HB | S,S-HB |
|---|---|---|
| Rank-1 in pore lumen | 12/12 | 8/12 |
| Jobs inside the 0.085 gap | 12/12 (gaps 0.001–0.044) | 8/12 (the pore ones: 0.001–0.019) |
| Non-pore jobs | none | 4: 8V82 amine seed 3 (gap 0.437), 8V8A amine seed 1 (0.877), 8V8A neutral seeds 2 and 3 (0.347, 0.349) |
| Seed-to-seed score spread within a configuration | 0.01–0.12 | up to 0.66 (amine/8V82: −6.52, −6.52, −7.18) |
| Parent (BUP_R, BUP_S) rank-1 | all 12 at the I34 pocket; 3 of 12 inside the gap | |

What this does to the headline:

1. **20 of the 24 hydroxybupropion jobs are inside the gap**, so their rank-1 label carries little
   information about which pose Vina would rank first. The tied runner-up poses are, by the docking
   sub-analysis, the same pore-axis placement (radial offset under 0.8 Å), so the pore label doesn't flip
   inside the tie. That claim rests on a coordinate proxy I did not rerun. [REPORTED; the adversarial check
   did not re-run it]
2. **The 4 non-pore S,S jobs score 0.35–0.88 kcal/mol better than the pore pose.** The S,S "8/12"
   therefore partly reflects seeds that didn't find a better-scoring lateral pose. The two 8V8A neutral
   jobs (0.347, 0.349; −6.88, −6.90) are probably one pose reproduced, which is an inference from near-equal
   numbers, not something checked from coordinates. [INFERENCE]
3. **Across all four boxes, S,S's best-scoring rank-1 pose is outside the pore in all four
   form/receptor configurations; R,R's is in the pore in 3 of 4** (the exception, 8V8A amine, has its
   best pose in the outer-pore box at −6.32 against −6.08 for the mid-pore pore pose). For S,S the best
   pore pose is 0.35–1.03 kcal/mol worse than the best pose in any box. [VERIFIED, `best.py`] This is a
   descriptive tally of scores in a rigid-receptor search, not a preference or an affinity.
4. **Run-level statistics are invalid.** A Fisher exact test on 12/12 vs 8/12 gives one-sided p = 0.047,
   two-sided 0.093, but the 24 runs are 8 configurations × 3 seeds, not 24 independent experiments. At the
   configuration level R,R ≥ S,S in all four; the best possible sign-test p is 0.125. [VERIFIED for the
   run-level p; the configuration-level argument is the contrast sub-analysis, REPORTED] The gap is
   concentrated in 8V8A (3 of the 4 non-pore S,S runs). Three seeds measure repeatability, not stability.
5. **The 12/12 is not special.** Seven of the 22 species are 100% pore-lumen in the mid-pore box: R,R-HB
   and the six glucuronide species (two threo-, two erythro- and two hydroxybupropion-O-glucuronides).
   Overall 88 of 168 mid-pore rank-1 poses are pore-lumen. [VERIFIED] The large, charged glucuronides all
   landing in the pore looks like a box/size effect. [INFERENCE]
6. **Sampling caveat from your own report:** the frozen mid-pore boxes are about 29.8 × 29.8 × 31 Å,
   over Vina's 27,000 Å³ default heuristic, and there is no pore pose-recovery control. [VERIFIED,
   `MATRIX_FROZEN.md`]

Your manuscript sentence already says these are "descriptive computational outcomes, not ... site
preferences." That holds. What it lacks is the tie rate and the S,S cross-site margins.

### 3.3 The parent-pore contradiction

| | Parent-only run | Combined run |
|---|---|---|
| Parent rank-1 in pore lumen | 4 of 8 conditions (R 8V82 mid, R 8V8A mid, R 8V8A outer, S 8V8A mid) | **0 of 12 in every form/receptor configuration across all four boxes** |
| Mid-pore box | about 25.3 × 25.3 × 26.5 Å (8V82), 25.6 × 25.6 × 26.6 Å (8V8A) | about 29.8 × 29.8 × 31 Å |
| R, 8V82, mid-pore score | −5.61, pore lumen | −6.57, I34 pocket |
| Where the best-scoring parent pose sits (all boxes) | | R: I34 pocket in both receptors; S: **EPJ pocket** in both (−7.5 in 8V82, −6.5 in 8V8A) |

Sources: parent-only table in `parent_docking_findings.md` §3, box sizes from `search_regions.json` in the
parent tarball, combined values from the CSV. [VERIFIED] Scores across the two runs are not a validated
comparison, so read them as consistent with, not proof of, this explanation:

**The pore result in the parent-only run is probably box-limited.** The wider combined box can reach the
I34 pocket, and when it can, the best parent pose moves there and scores about 1 kcal/mol better. [INFERENCE]
Two further facts matter:

- **The I34 pocket is where the PAM sat.** I34 is the PDB component code for PNU-120596
  (N-(5-chloro-2,4-dimethoxyphenyl)-N'-(5-methyl-3-isoxazolyl)urea; RCSB chemical-component record, checked
  today). The prepared receptor files `8V82_prot.pdb` and `8V8A_prot.pdb` from the parent tarball have zero
  HETATM records [VERIFIED], so the pocket is empty in the docking receptor but keeps its ligand-bound
  shape. A PAM site is a plausible sink for
  anything hydrophobic, and 252 of 672 rank-1 poses land there (combined report §5). This is an
  inference, but the 252 figure is not.
- **Both templates are PAM-bound, and neither is an "activated" state** (§5, Burke row). That is already
  in §6 of the manuscript.

The audit's "same drug, same receptors, opposite answers" is right, and the boxes are why. It also
means the "agreement" with Duarte 2021 claimed in `parent_docking_findings.md` §5 is weaker than written:
Duarte's five named residues are a group-level result for seven drugs, and Duarte places bupropion
specifically toward rings 9′–16′. [REPORTED from the full text]

**Replacement wording for manuscript §6, second paragraph (for you to adapt):**

> In the matched mid-pore searches, R,R-hydroxybupropion gave pore-lumen rank-1 poses in 12 of 12 runs and
> S,S-hydroxybupropion in 8 of 12, while all 12 parent runs ended at the lateral I34 pocket. These are
> counts of rank-1 placements within one box. In 20 of the 24 hydroxybupropion runs the rank-1 score was
> within 0.085 kcal/mol of the rank-2 score, the gap by which the I34/8V82 control mis-ranked the deposited
> pose. The four non-pore S,S runs scored 0.35–0.88 kcal/mol better than a pore pose. Across all four
> boxes, parent never gave a pore-lumen rank-1 pose, whereas the earlier parent-only run, with smaller
> mid-pore boxes, did in four of eight conditions; site assignment is therefore box-dependent, and these
> results are not evidence that parent cannot enter the pore. They are not biological replicates, site
> preferences or affinities.

### 3.4 Why the reliability finding may be worth more than the claim it replaces

The pore contrast cannot carry biology: no pore control exists, the contrast is built mostly from poses
the scoring function cannot rank, it flips with box size, and both receptors carry a bound PAM. The
reliability result can carry weight: 52.8% of 672 rank-1 poses and 98% of pore calls sit inside the
control's own mis-ranking gap. It is reproducible from the delivered CSVs, uses the delivery's own
control, and speaks to something any docking user would want to know, that pose rank is not reliable at
the 0.1 kcal/mol scale and the pore is a flat, near-degenerate scoring region. The audit already called
the control failure the best thing in the delivery. This is its quantified version.

**Open and unverified here:** per-mode site labels don't exist for ranks above 1 (the SDF marks all 11,610
non-rank-1 records "not classified"). So whether the 213 tied off-axis jobs (I34, other interface, EPJ)
are robust to the tie is unknown; for 100 of them the rank-2 pose is at least 10 Å from rank 1. [REPORTED]
The pipeline scripts that would classify them are in `combined_bundle/scripts/` (`geometry.py`,
`analyse_metabolites.py`); the working-tree path named in CLAUDE.md does exist on this machine, though I
did not look inside it beyond listing it.

---

## 4. Novelty: what is unmeasured, stated so it survives

### 4.1 Hydroxybupropion at α7

**Safe statement:** "In the searches described, we located no measurement of the functional activity of
hydroxybupropion, radafaxine, threohydrobupropion or erythrohydrobupropion at α7 nicotinic receptors."
Not "never measured," not "first," not "no evidence exists."

What the searches did (PubMed via eutils, Europe PMC full text, ChEMBL, Crossref; 7 October 2026) [REPORTED]:

- Metabolite-term AND α7-term in PubMed titles/abstracts/MeSH: **0 records**.
- 152 unique abstracts from the metabolite/nicotinic/radafaxine/α7 queries and 358 abstracts citing the
  key α7 papers: 0 with both a metabolite term and an α7 term.
- Full texts opened and searched for a metabolite term near an α7 term, all negative: Lukas 2010
  (α7 appears only twice, in background), Carroll 2010 and 2011, Duarte 2021 (105 α7 mentions, no
  hydroxybupropion), and others. 13 Europe PMC full-text hits all incidental.
- ChEMBL has radafaxine activity rows only for α1β1γδ, α3β4, α4β2, α4β4; no CHRNA7 row.

**What is not excluded:**
- **Damaj 2004 full text is unread.** Closed access, no open copy. Its abstract reports α4β2 (S,S IC50
  3.3 µM) and refers to human nicotinic receptor subtypes without listing them. Lukas 2010 (same lab) describes its earlier panel as
  α3β4\*, α4β2, α4β4, α1\*, which makes an α7 arm unlikely, but that is inference. Needs the library.
- Guide to Pharmacology (needs an API key, not used), patents, theses, conference abstracts, Embase,
  Scopus, Web of Science: not searched.
- Papke 2011's metabolite status: its text covers bupropion only. [VERIFIED]

**Trap, and you need an answer ready.** A 2024 *Biophys J* paper (PMID 38678367; preprint bioRxiv 37873398)
writes that bupropion "and its metabolites" inhibit α7, α4β2 and α3β4 receptors. The references it cites for
that are parent-bupropion α7 papers and Damaj 2004. It is a pooled sentence, not a metabolite α7
measurement. Don't cite it as one; if a reviewer cites it at you, that is the answer. [REPORTED]

Also: reviews I checked (Bagdas 2019, Cui 2018) attribute hydroxybupropion block to α4β2 and α3β2,
not α7. [REPORTED]

### 4.2 Structural and docking prior art

- **Vázquez-Gómez 2014:** abstract reports whole-cell recording, calcium influx, [3H]imipramine
  competition binding **and molecular docking**, concluding a luminal site. Full text is closed;
  receptor model, software and poses are unknown to me. [VERIFIED abstract; UNVERIFIED beyond that]
- **Duarte 2021 (full text read):** rat α7 homology model built on human α4β2 (5KXI), 48.5% sequence
  identity, 66% coverage; Glide SP then XP in a pore-restricted 12 Å cube; 100 ns MD per complex; MM-GBSA.
  Seven antidepressants including bupropion, no metabolites. Its energies are MM-GBSA and not comparable
  with Vina scores. The rat and human M2 sequences are identical over positions 250–300, with the same
  numbering (both 502 residues), so Duarte's residue numbers map straight onto `contacts_uniprot`. The
  bupropion-specific contact table is in Supplementary Table S1/S2, which I did not read. [REPORTED]
- **Do 2024 (*Biophys J*):** Vina docking of bupropion into GLIC, a bacterial relative, found pore and
  non-pore intersubunit sites. Pandhare 2012 (Torpedo) and Arias 2016 (α4β2) report luminal and non-luminal
  bupropion sites (titles read only). [REPORTED]
- **PDB, 7 Oct 2026:** 53 entries match the α7 UniProt accessions. None I could find holds a small-molecule
  pore blocker. 9NX1 is α7 with conotoxin ImII (a peptide; its title confirmed by me, its pore
  placement not re-checked). An NMR-mapped ketamine site was reported without a deposited complex. [REPORTED]
- Same-day check of the structures you used: 8V82 (2.61 Å) and 8V8A (2.19 Å) both released 2024-02-21,
  8V89 resting, 7EKP 2021-05-19. [VERIFIED, RCSB API]

**What you can claim as new, honestly:** docking of the hydroxybupropion stereoisomers and other
metabolites into α7 (my searches found no docking or structural study of hydroxybupropion at any nAChR; a
search negative); experimental human coordinates; measured-site reporting across overlapping boxes; and
control-gated reporting with the failure disclosed. **What is not new:** parent bupropion in an α7 pore.
**Is it a "methodological step up"?** Partly. Human experimental coordinates beat a rat model on a
48.5%-identity template, but the M2 pore is identical in the two species, so the gain is small for the
pore. Duarte had flexibility, MD and free-energy scoring; you used rigid-receptor Vina with no dynamics,
so on protocol sophistication you are a step down.

**Unproposed.** I did not search whether anyone has proposed H1 or H2 in this pass. Manuscript §8 itself says
broad nicotinic explanations have appeared in public discussion, and `hypothesis_novelty_and_submission_review.md`
predates H2. Treat "unproposed" as unchecked.

---

## 5. Claim-by-claim verification

Verdicts: **Confirmed**, **Narrowed** (true but needs qualification), **Overturned** (the earlier
finding was wrong), **Open**. "Adv" notes where an adversarial check changed an earlier answer.

| Item | What the source says (number, location) | Verdict | Manuscript status and wording |
|---|---|---|---|
| **Dale 2008** (ref 19), PMC2526371, full text read | Groups: DID n = 8, "other dissociative" (DD) n = 8, controls n = 13. All 8 DD are depersonalization disorder (2 alone, 6 with amnesia), Method > Participants. PPI: controls and DD both significant at 30–150 ms, not at 420 ms; Group × SOA F(10,130) = 2.00, p < 0.04, quadratic trend absent only in DID (F = 3.38, p = 0.077). DES 40.5 (DD) vs 43.0 (DID) vs 10.4 (controls). | **Audit FIX overturned.** The sentence is supported; audit read the abstract only | No change required. Optional: "subgroup" → "comparison group" (it was separately recruited). Optional stronger sentence: the DD group was as dissociative as DID but had normal PPI; DID's deviation is prolonged inhibition and absent habituation, the opposite of a gating deficit. The null is underpowered (n = 8 per clinical group; authors flag it), not an equivalence result. Evidence CSV row already correct |
| **Grunebaum 2013** (ref 24), PMC4313534, full text read | Scale is the 24-item HDRS. "Disturbed Thinking" = lack of insight, depersonalization/derealization, paranoia, obsessions/compulsions (Fig. 1 footnote b). Result: no differential treatment effect, p > 0.1 (abstract says p > 0.05), grouped with other factors, no estimate or CI. n = 36 paroxetine, 74 total with bupropion n = 38. Psychosis was an exclusion. Bupropion 150 mg for weeks 1–2. Benzodiazepine dose higher in bupropion arm. Post hoc, small sample | **Audit FIX overturned to "thin, not unsupported"; already upgraded (`784dc68`)** | Current sentence is right. Label two inferences: "three of four items sit near floor" (my inference from the psychosis exclusion; say "are expected to") and "weak instrument." "Item 19" is also inference. Keep universal-absence wording ("no trial has reported ...") **out**; the pass proposed it, the commit didn't adopt it, keep it that way. Optional additions: the benzodiazepine confound; the same trial found no differential effect on HDRS Anxiety or Sleep, which weakly disfavours two rival explanations (inference) |
| **Papke 2011** (ref 4), PMC3083103 legacy HTML | Table 4 IC50 (coapplication / bath, µM): α7 46 ± 7 / 16 ± 3; (α4)3(β2)2 8.3 ± 1.2 / 5.9 ± 1.5; (α4)2(β2)3 72 ± 5 / 4.4 ± 2.3; α4β2α5 23 ± 2 / 2.8 ± 1.0. Text: the authors call α7 and (α4)3(β2)2 potency roughly unchanged between protocols. ACh 300 µM (acute, α7) and 60 µM (bath, α7) are in Methods | Numbers **Confirmed**. The "roughly unchanged" reading is the authors' characterization; the shift is 2.9× numerically. **Current manuscript wording Overturned in part** (Adv) | Fix §2: shifts are 2.9× (α7), 1.4× ((α4)3(β2)2), 16× ((α4)2(β2)3), 8× (α4β2α5), so "much larger at the α4β2 stoichiometries" holds for two of three. Proposed: "...the authors describe α7 potency as roughly unchanged between protocols, whereas (α4)2(β2)3 and α4β2α5 shifted much more (72 → 4.4 µM; 23 → 2.8 µM). Under bath application all three α4-containing forms were more potent than α7; under coapplication (α4)2(β2)3 was less potent." Minor: the Methods wording about 300 µM is phrased around partial agonists; the bupropion link is by cross-reference |
| **Burke 2024** (PMC10950261), 8V82/8V8A | Data availability names 8V82 "epibatidine and PNU-120596 complex" and 8V8A as the time-resolved desensitized intermediate with the same ligands; text calls the α7-epi/type II PAM complexes partially activated or partially desensitized, did not obtain a fully activated state, and the time-resolved state is virtually identical to the equilibrium structure | **Confirmed** (I re-read the passages) | Already corrected in `09d56a7`. Nuance: the time-resolved dataset also contained resting-like and asymmetric sub-populations; 8V8A is the majority intermediate |
| **Duarte 2021** (ref 6), full text | 50 µM: bupropion ratio 0.52 ± 0.04. At 20 µM, all seven antidepressants inhibited 17.7–42.3% of control (group range; bupropion's own value is in Fig. 2E, not read) | **Confirmed** at 50 µM; 20 µM **Narrowed**: supported at group level only | Fine as written. Duarte's 20 µM rationale is fluoxetine brain levels |
| **Vázquez-Gómez 2014** (ref 5) | Abstract: IC50 54 µM, Ki 63 µM, docking, imipramine binding, luminal site | Abstract **Confirmed**; full text **Open** | Audit §4.3 mischaracterized it as binding only |
| **Pandhare 2017** (ref 41) | 5-HT3A IC50 87 / 112 µM; full text bases the claim on a 10–100× plasma ratio | Numbers **Confirmed**; the therapeutic-relevance claim **Narrowed** by arithmetic (§2.6) | Don't carry the phrase into your text. Audit §4.4 inference **Overturned** |
| **Kharasch 2019** (not cited) | Table 1: parent Cmax 81 (68–106) ng/mL, hydroxybupropion 1167 (849–1382), brand XL 300 | **Confirmed** | Candidate citation for §5 |
| **Sager 2017** (not cited) | Table 1 fu,p 0.5 ± 0.1 (R-bupropion), 0.6 (S), 0.5 (R,R- and S,S-HB), threo 1.0, erythro 0.7 | **Confirmed**; **conflicts with label's 84%** | Cite both; report the 3× fu spread |
| **Label** (ref 1) | 84% bound; HB peak about 7× parent; HB AUC about 13×; threo AUC about 7×, erythro 1.4× | **Confirmed**; measured HB ratios are about twice the label's | |
| **Cremers 2016** (ref 38) | Kp,uu 1.9 and 1.7 (rat, steady state); human values predicted | **Confirmed** from abstract | |
| **Lukas 2010** (ref 7), full text read by novelty search | Panel α3β4\*, α4β2, α4β4, muscle; α7 mentioned twice in background | **Confirmed** [REPORTED] | |
| **Damaj 2004, Bondarev 2003** (refs 8, 9) | Abstract only. Bondarev: metabolites lacked affinity for nicotinic receptors in binding while inhibiting α3β4 flux | **Open** | Needs library |
| **Docking counts, §6** | 12/12, 8/12, 6/6 + 6/6, 13 and 93 clash flags, control table | **Confirmed** (audit; I reproduced the midpore counts again) | |
| **Tie rate 52.8%** | 355 of 672 | **Confirmed**, **Narrowed** by Adv to "within the control's observed gap"; four stated limits (§3.1, §3.2) | Add to §6 and the report's §8 |

Where an adversarial check ran: Papke (caught the error in the proposed wording and in the committed text),
the tie analysis (reproduced all counts; narrowed the interpretation), the metabolite-α7 search (not
refuted; added the *Biophys J* sentence and the unread Damaj text). I did not receive an adversarial verdict
for the exposure arithmetic or the contrast-robustness analysis, so I recomputed both from files and
marked what I could not redo.

---

## 6. What is still open

**Needs Lasell library access**
1. **Damaj 2004**, *Mol Pharmacol* 66:675. Closed. The only plausible place for a metabolite α7 arm.
2. **Bondarev 2003**, *Eur J Pharmacol* 474:85. Binding vs functional result.
3. **Vázquez-Gómez 2014**, *Eur J Pharmacol* 740:103. Closed, not in PMC. Contains docking, which nobody has
   read yet, and it is the paper that underwrites "luminal."
4. **Slemmer 2000** and **Alkondon 2005** (*JPET*). Not in PMC; you cite both. Abstract-level check is
   already solid, so these are lower priority.
5. The abstract-only citations whose open-access status I did not check: Townsend 2016 (MLA half),
   Medford 2016, Yin 2017, Rockley 2023, Silverstone 2008 (CD50 range), Bällgren 2024 (1.94 ± 0.57). Try
   PMC and Europe PMC first.
Dale 2008, Grunebaum 2013 and Papke 2011 no longer need the library.

**Needs your decision.** See §7.

**Doable computationally (no new docking)**
- Classify ranks above 1 with the pipeline scripts in `combined_bundle/scripts/` against the receptors in
  `parent_docking_inputs_and_poses.tar.gz`, to settle the 213 off-axis ties.
- Download Duarte's Supplementary Tables S1/S2 (open access) and compare bupropion's own contacts with
  your pore poses.
- Rerun the §8 PubMed counts with exact strings and a date. I did not find the September query strings.
- Add threohydrobupropion and erythrohydrobupropion lines to the exposure table.
- A sensitivity run with more seeds or a wider mid-pore search belongs in the pipeline outside this
  directory, and CLAUDE.md says not to regenerate results here. Your call.

---

## 7. Decisions for you

1. **One hypothesis or two (carried from the audit).** New evidence: parent-driven α7 block is
   arithmetically negligible at therapeutic doses and partial in overdose; two seizure cases sit at
   parent levels worth at most about 8% block; Dale shows high dissociation with normal PPI. H2 needs
   all three conditions and none are shown. **I'd keep H1 as the paper and shrink H2 to a short
   extension paragraph.** It makes the arithmetic and the novelty review consistent again.
2. **Therapeutic or overdose (carried).** The arithmetic answers part of it. **Frame H1 around
   hydroxybupropion at therapeutic exposure, as a conditional prediction with the 11–35 µM threshold, and
   treat the parent in overdose as a separate, smaller claim.**
3. **Add an exposure paragraph to §5.** It means rewriting the "no exposure model" sentences in §5 and
   §8. **Yes**, labelled as arithmetic, with the fu conflict and the rat-only Kp,uu stated once.
4. **Docking: keep or cut (carried), and how to lead.** **Keep, drop the R,R vs S,S contrast as a
   finding, and lead with the reliability result.** Adopt the §3.3 paragraph or something like it.
5. **Library order (updated).** Damaj 2004, Bondarev 2003, Vázquez-Gómez 2014. Grunebaum and Dale
   come off.
6. **Which professor (carried).** Unchanged. The audit's statement that the *Journal of Young
   Investigators* requires a sponsor was not rechecked here. Lead with the unmeasured experiment, the
   threshold, and the reliability result.
7. **§8 search counts (carried).** I'd drop the September numbers, keep the method, and replace them with a
   dated rerun. The 7 Oct metabolite × α7 result (0 records) is a ready replacement.
8. **Run the per-mode site classification?** I can do it from the bundle scripts; it needs no docking.
   **Yes.**
9. **Regenerate the PDF and DOCX, and update `hypothesis_novelty_and_submission_review.md`** (still
   single-hypothesis).

**Not decisions, just do:** fix the Papke sentence (§5); strike Dale from the errors list; label the two
inferences in the Grunebaum sentence; don't cite the *Biophys J* sentence as a metabolite α7 source; add
the tie rate to the report's §8 beside the 0.028 / 0.085 / 0.071 line.
