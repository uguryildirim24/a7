# Claim audit — 7 October 2026

Historical research record. Read with [the corrections](docs/review_record.md).
Several findings below were superseded. The first-person check claims refer to
the October 7, 2026 agent review, not checks repeated during public cleanup.

Independent check of `bupropion_alpha7_hypothesis_draft.md` against its own sources and its own data.
Nothing in the manuscript was edited. This file is the audit only.

**What I checked.** All 47 references: does each one exist, is it attributed correctly, and does it say
what the text says it says. Every docking number in the text against the CSV outputs. Internal
consistency between the manuscript and the two docking reports.

**How.** Crossref for DOI metadata (title, journal, year, first author), PubMed E-utilities for PMIDs
and abstracts, the DailyMed SPL XML for the label, and the repo's own CSVs for the docking counts.

---

## 1. Headline

| Finding | Result |
|---|---|
| Fabricated or misattributed references | **None.** 45/45 DOIs resolve; year, journal, first author and title all match. The two non-DOI citations check out too. |
| References cited but absent from the list, or listed but never cited | **None.** All 47 appear in both. |
| Docking numbers in the text vs. the CSVs | **Every one matches exactly.** |
| Claims that need work | **4 specific items**, listed in §4. |

The biggest risk going in was invented citations. That risk is clear. The reference layer and the
numbers are the strongest part of this delivery, and the guardrails in `CLAUDE.md` were genuinely
honoured — the evidence table even flags an internal stereochemistry inconsistency inside Damaj's own
abstract, which is a thing a careless pass would have copied straight through.

"Mostly GPT slop" is not what the citations show. The weakness is elsewhere: in how much the prose
hedges, in two sourcing gaps, and in one scientific contradiction the text mentions in a single
clause when it deserves a paragraph.

---

## 2. Citation audit — all 47

Tags: **OK** = the source says this, verified · **ABS** = confirmed from the abstract only, full text
not read · **FT** = the specific number or detail lives in the full text and was taken from indexed
text or a table, not the PDF · **FIX** = does not match the source as written

| # | Source | What the text claims | Tag | Note |
|---|---|---|---|---|
| 1 | DailyMed Wellbutrin XL | Label lists depersonalization + derealization as postmarketing nervous-system events; says voluntary reports can't establish frequency or causality | **OK** | Verified verbatim in §6.2. Both terms present under Nervous System; the disclaimer is quoted almost word for word. Seizure warning is §5.3. |
| 2 | Slemmer 2000 | Compared several nicotinic subtypes | **OK** | Abstract: blocks α3β2, α4β2 and α7; ~50× and ~12× more effective at α3β2/α4β2 than α7. Text's wording is more cautious than the source. |
| 3 | Alkondon 2005 | No inhibition of the α7-like response at 1 µM, despite effects on other classes | **OK** | Abstract: 56 / 15 / **0%** inhibition of type III / II / IA at 1 µM. Exact. "α7-like" is the right hedge — the paper says "likely representing". |
| 4 | Papke 2011 | Human α7 IC₅₀ 46 ± 7 µM coapplication, 16 ± 3 µM after 30 min bath; protocols also differed in ACh | **FT** | From Table 4 via indexed full text, not the PDF. The ACh caveat is sourced (60 µM bath vs 300 µM acute). Holds, but rests on indexed text. |
| 5 | Vázquez-Gómez 2014 | 54 µM calcium-response IC₅₀ and native-neuron inhibition | **OK** | Abstract: IC₅₀ = 54 µM, Kᵢ = 63 µM, hippocampal interneurons inhibited at 10 µM. Exact. |
| 6 | Duarte 2021 | Inhibition of rat α7 currents at 20 and 50 µM | **FT** | 50 µM figure is in Results §2.2 / Fig 2; the 20 µM point is recorded in the evidence table but not independently re-checked here. Text correctly says *rat*. |
| 7 | Lukas 2010 | S,S-hydroxybupropion more potent than parent at α4β2, R,R less potent; panel contained no α7 | **OK** | All six §2 table values trace to Table 1, verified as full text. The no-α7 claim is a negative read off that table. |
| 8 | Damaj 2004 | Abstract supports stereoselective α4β2 pharmacology | **ABS** | Confirmed: (2S,3S) α4β2 IC₅₀ 3.3 µM, more potent than comparator and racemate — matching Lukas independently. Full text not read. The abstract labels its comparator inconsistently ((2S,3R) in one place, (2R,3R) in another); the evidence table already flags this. |
| 9 | Bondarev 2003 | Abstract supports tested-metabolite α3β4 functional inhibition | **ABS** | Confirmed. **Also in the abstract and not in the manuscript:** "Bupropion and its metabolites lacked affinity for nicotinic acetylcholinergic receptors" in the binding assay. See §4.4. |
| 10 | Albuquerque 2000 | Human cortical + rat hippocampal nicotinic control of interneuron output, inhibition or disinhibition depending on the connection | **OK** | Abstract says exactly this, including the species and the conditionality. |
| 11 | Ji & Dani 2000 | (same claim group) | **OK** | Abstract: ACh excitation of CA1 interneurons "could induce either inhibition or disinhibition of pyramidal neurons". |
| 12 | Pidoplichko 2013 | Rat BLA: a condition in which α7 activity favours inhibition over excitation | **OK** | Abstract: "the inhibitory currents are enhanced significantly more than the exc[itatory]". The hedge "a condition in which" is correct. |
| 13 | Townsend 2016 | Increased inhibitory currents and reduced pyramidal firing under α7 agonist; MLA increased evoked firing | **ABS** | First half confirmed (increased spontaneous GABA IPSCs, moderate suppression of excitability, rat CA1). The MLA half is not in the abstract. |
| 14 | Olincy 2006 | Small DMXB-A trial reported P50 improvement | **OK** | "Significant improvement in P50 inhibition also occurred." n = 12, so "small" is fair. |
| 15 | Shiina 2010 | Tropisetron trial reported P50 improvement | **OK** | "significantly improved auditory sensory gating P50 deficits in non-smoking patients". The 5-HT₃ caveat in the text is appropriate. |
| 16 | Winterer 2013 | α7 PAM trial did not | **OK** | "No indication was found that JNJ-39393406 has the potential to reverse… sensory P50 gating." |
| 17 | Bertelsen 2015 | No association of the tested variant with P50 or PPI, despite association with schizophrenia and a startle finding | **OK** | Matches the abstract point for point. This is also the paper §8 self-corrects on — correctly. |
| 18 | Schabinger 2018 | Reduced early suppression of unattended visual stimuli in depersonalization | **OK** | "decreased suppression of stimuli at unattended locations… over P1". Exact. |
| 19 | Dale 2008 | Small **depersonalization** subgroup broadly resembled controls on PPI; abnormalities were in a separate dissociative-identity group | **FIX** | The abstract compares DID vs **"other dissociative disorders"** vs controls. It never names a depersonalization subgroup and never says that group resembled controls. See §4.1. |
| 20 | Mori 2013 | Bupropion did not disrupt PPI in mice | **OK** | "bupropion did not disrupt prepulse inhibition, even in bupropion-sensitized mice". Exact. |
| 21 | Medford 2016 | Reduced insula response to emotional stimuli; prefrontal pattern; small follow-up neither blinded nor placebo controlled | **ABS** | Insula finding confirmed both ways (reduced with symptoms, increased with improvement). The prefrontal detail and the design limitations are not in the abstract. |
| 22 | Sedeño 2014 | A single-patient interoception study | **OK** | "a patient with DD and controls", heartbeat detection + fMRI connectivity. Exact, including "single-patient". |
| 23 | Jia 2025 | Later connectivity study implicating self-referential processing, without measuring α7 | **OK** | Matches. |
| 24 | Grunebaum 2013 | In a bupropion–paroxetine comparison, the composite containing a DP/DR item showed no differential treatment effect | **FIX** | The abstract never mentions depersonalization, derealization, or that item. See §4.2. |
| 25 | Sun 2021 | Reducing α7 raised CA1 excitability and shortened pilocarpine latency; agonist did not significantly help | **OK** | Exact, including the null for increasing α7 activity. The PV caveat is the manuscript's own critique, correctly flagged as not established. |
| 26 | Wang 2020 | Septum–hippocampus cholinergic pathway suppressed seizures via somatostatin interneurons; silencing PV cells did not reverse it | **OK** | Abstract: inhibiting SST-positive "(rather than parvalbumin-positive)" neurons reversed the antiseizure effect. Precisely right — and the text correctly does *not* call this an α7 result. |
| 27 | Wang 2025 (huperzine) | Linked seizure protection to septal–dCA1 cholinergic signalling and α7 | **OK** | "α7 nicotinic acetylcholine receptors in the dCA1 region mediate the anti-seizures cholinergic circuit". |
| 28 | Silverstone 2008 | Hydroxy, threo and erythro preparations more convulsive than parent; equimolar doses; enantiomers not separated; parent CD₅₀ beyond tested range | **OK/FT** | "All metabolites were associated with a greater percentage of seizures compared to bupropion"; equimolar 25/50/75 mg/kg confirmed. The CD₅₀-beyond-range point needs the full text (and is consistent with Tutka's 119.7 mg/kg). |
| 29 | Tutka 2004 | Lower-dose protection against electroshock, higher-dose convulsions | **OK** | CD₅₀ 119.7 mg/kg; 15–30 mg/kg protective against MES, ED₅₀ 19.4. No effect on PTZ or kainate — supports "depends on the model". |
| 30 | Heydrich 2019 | Nine ictal depersonalization-like, seven derealization-like; former frontal, latter temporal | **OK** | n = 9 and n = 7 exact; frontal (dorsal premotor) vs temporal exact. |
| 31 | Gil 2002 | Gain-of-function α7 mutants more susceptible to nicotine seizures; MLA suppressed them | **OK** | L250T increases current amplitude and decreases desensitization — "gain-of-function" is right. MLA inhibited. |
| 32 | Iha 2017 | In another nicotine model MLA was protective | **OK** | "methyllycaconitine also significantly inhibited nicotine-induced seizures". |
| 33 | Franceschini 2002 | α7-null mice retained similar nicotine seizure dose-response curves | **OK** | Exact. This is the paper's strongest counterweight and it is used honestly. |
| 34 | Yin 2017 | No consistent behavioural or EEG phenotype in Chrna7-deficient mice | **ABS** | Behavioural half supported by title and abstract. The EEG half needs the results section. |
| 35 | Zheng 2021 (cytisine) | Reduced recurrent seizures via α7, but bulk GABA did not increase | **OK** | "decreased glutamate levels **without altering GABA levels**"; α-bgt blocked the effects. Exact. |
| 36 | Qian 2024 (tropisetron) | (same claim group) | **OK** | "lowered glutamate levels **without affecting GABA levels**". Exact. |
| 37 | Zapukhliak 2021 | α7-restricted blockade failed to change some discharges; mecamylamine worked | **OK** | "mecamylamine abolished… while antagonists of α7 and α4β2, MLA and DhβE, had no effect". Exact. |
| 38 | Cremers 2016 | Unbound brain/plasma ratios 1.9 parent, 1.7 hydroxybupropion; human values were predictions | **OK** | Both numbers in the abstract; the title itself says "Predict Human Brain Concentrations". |
| 39 | Bhattacharya 2023 | Time-varying, stereoselective ratios by a different method | **OK** | Supported. Notably: unbound R,R-hydroxybupropion exposure ran 1.5× higher than S,S in plasma and brain. |
| 40 | Bällgren 2024 | Parent whole-brain unbound/plasma ratio 1.94 ± 0.57, with intracellular accumulation assessed separately | **ABS** | The number is in the results, not the abstract. The abstract also ties this transporter class to drug-induced seizures — relevant and unused. |
| 41 | Pandhare 2017 | Parent and hydroxybupropion affect 5-HT₃ | **OK** | IC₅₀ 87 µM and 112 µM. **The abstract also says hydroxybupropion's value is "within its therapeutically-relevant concentrations"** — see §4.4. |
| 42 | Stuebler 2020 | (same claim group) | **OK** | 5-HT₃AB 840 / 526 µM; 5-HT₃A 87 / 113 µM. |
| 43 | Rockley 2023 | Bupropion affected α4β2 and potassium channels in a human-channel/network screen | **ABS** | Panel and design confirmed; bupropion's specific per-channel hits need the compound table. The panel includes α4β2 but **no α7**. |
| 44 | Park 2016 | TRESK inhibition measured separately | **OK** | "bupropion inhibited TRESK, but had no effect on TREK-2". Exact. |
| 45 | Kobayashi 2004 | Bupropion was an exception to GIRK inhibition | **OK** | "except fluvoxamine, zimelidine, and bupropion". Exact — a careful use of a negative result. |
| 46 | Almeida-Suhett 2014 | Reported reduced GABA inhibition alongside **increased** α7 currents, not α7 loss | **OK** | Confirmed: "significant increases in the surface expression and current mediated by α7-nAChR were observed". The §8 self-correction is right. |
| 47 | Lucas-Meunier 2009 | Emphasised α4β2-related inhibition and other cholinergic effects | **OK** | "DHβE, the selective α4β2 nicotinic receptor antagonist, induced a depression of inhibition." Correct, and "other cholinergic effects" fairly covers the α*β4 presynaptic result. |

**Totals: 36 OK · 8 abstract-only or full-text-dependent · 1 OK/FT · 2 FIX.**

---

## 3. Docking numbers in the text vs. the data

Every figure in §6 of the manuscript, checked against the CSVs in this directory.

| Claim in §6 | Checked against | Result |
|---|---|---|
| 22 species, 20 candidates + 2 parent references | `combined_metabolite_poses.csv` | **Matches.** 22 distinct species; `BUP_R` + `BUP_S` are the two parent references. |
| Represented by 28 forms | same | **Matches.** 28 distinct (species, form) pairs from 7 form types. |
| 672 metabolite/parent calculations + 12 shared controls | same | **Matches.** 672 rank-1 rows. Controls = EPJ, I34 × 2 states × 3 seeds = 12. |
| 8V82 activated, 8V8A desensitized, four regions per state, three seeds | same | **Matches.** 336 rows per receptor; four region boxes (`midpore`, `outerpore`, `ortho`, `lateral_I34`) at 168 each. |
| R,R-hydroxybupropion: pore-lumen rank 1 in 12/12 across two forms and two states | same, `HB_2R3R` + `region_box=midpore` | **Matches exactly.** 12 runs, 12 `pore_lumen`. Two forms (amine_cation, neutral), two states. |
| S,S-hydroxybupropion: 8/12 | `HB_2S3S` | **Matches exactly.** 8 `pore_lumen`, 4 `other_interface`. |
| Parent rank-1 in those boxes landed at the lateral I34 pocket | `BUP_R`, `BUP_S` | **Matches.** 6/6 each → `I34_pocket`. |
| 13 rank-1 poses and 93 saved modes carried the short-contact flag | `combined_clash_flagged.csv`, `combined_clash_allmodes.csv` | **Matches.** 13 and 93 rows. |
| 3 of 4 control pairs recovered at rank 1; I34/8V82 failed (6.372–6.411 Å), recovered at rank 2 (0.744–0.783 Å) | `combined_metabolite_docking_report.md` §8 | **Matches exactly.** |
| No experimental pore-bound blocker control | same report | **Matches.** Stated there too. |
| Earlier parent-only searches also produced pore poses | `parent_docking_findings.md` §3 | **Matches** — and this is the one that needs more than a clause. See §4.3. |

No drift. Not one number off.

---

## 4. The things that actually need work

### 4.1 Dale 2008 is described as a depersonalization group; its abstract doesn't say that — **FIX**

The text says "Dale et al.'s small depersonalization subgroup broadly resembled controls on PPI."
The abstract's three groups are dissociative identity disorder, **"other dissociative disorders"**, and
non-diagnosed controls. It reports findings *about the DID group* and never characterises the
comparison group as depersonalization, nor states that it resembled controls.

Either the full text identifies that group's composition — in which case cite it that way — or the
sentence has to go. Note the direction of the error is conservative: the claim is used *against* H1,
so fixing it may slightly strengthen the hypothesis. It's still wrong as written, and it is exactly
the sort of thing a reviewer checks.

### 4.2 The only clinical datum on bupropion and depersonalization is not in the source abstract — **FIX**

The text says that in Grunebaum's bupropion–paroxetine trial, "the composite containing a DP/DR item
showed no differential treatment effect." The abstract reports a treatment effect on HDRS *psychic
depression* and says nothing about depersonalization, derealization, or any such item.

It is true that the Hamilton scale carries a depersonalization/derealization item, so the claim is
plausible — but as written it asserts a specific negative result about a sub-item from a post-hoc
cluster analysis, sourced to an abstract that doesn't contain it. This is the manuscript's **only**
human clinical observation bearing on the actual symptom. It needs the full text and the cluster
table, or it needs to be removed and the gap stated plainly.

### 4.3 Parent bupropion lands in the pore in one of your own studies and not the other

This is the real scientific vulnerability, and it is not a citation problem.

- **Combined metabolite run:** parent in the mid-pore box → lateral I34 pocket, 6/6. R,R-hydroxybupropion → pore lumen, 12/12. That contrast is the paper's headline structural observation.
- **Parent-only run** (`parent_docking_findings.md` §3): parent R and S, same two receptors, mid-pore and outer-pore → **pore lumen** in four of eight conditions, with tight pose clustering.

Same drug, same receptors, opposite answers. The explanation is in the repo: the two campaigns used
**different boxes** — the parent study explicitly fixed a box-definition defect ("the original 'lumen'
box was 27 × 27 × 39 Å"), and the combined report calls its controls "new-box". So the within-study
comparison in the combined run is the legitimate one, because every species there shared the same
boxes.

But the manuscript compresses all of that into eight words: "so the contrast is sensitive to setup."
That is not enough for the claim it is carrying. Worse, two independent experimental papers you
already cite point the *other* way: Vázquez-Gómez (ref 5) concludes a **luminal** site for parent
bupropion from imipramine competition binding, and Duarte (ref 6) has bupropion acting **within the
ion channel**. So "parent went to a side pocket" sits against your own cited literature.

The defensible version of this claim is narrower and stronger: *within matched boxes in a single run,
R,R-hydroxybupropion placed in the lumen more consistently than parent did; site assignment is
box-dependent, and this is not evidence that parent cannot enter the pore — published binding work
suggests it can.* That costs you nothing you actually had and removes the opening.

Related, and worth one line in the text: the repo contains two control tables for the same I34/8V82
pair with different pass fractions (4 of 5 in the parent study, 3 of 4 in the combined study) and
slightly different RMSDs (6.359–6.373 vs 6.372–6.411 Å). Both are correct for their own run. Anyone
reading both files will ask. Say which set §6 is reporting.

### 4.4 Two things in abstracts you cite that argue against the hypothesis, and aren't in the text

Not errors — omissions. Both are in abstracts already in the reference list, so a reviewer will find
them in minutes.

1. **Bondarev (ref 9):** "Bupropion and its metabolites **lacked affinity** for nicotinic acetylcholinergic receptors" in that binding assay, even while antagonising α3β4 flux. The evidence table captures this; the manuscript doesn't. A functional-inhibition-without-binding-affinity result is directly relevant to a paper proposing a binding pose.
2. **Pandhare (ref 41):** hydroxybupropion inhibits 5-HT₃A at 112 µM, and the authors call that "within its therapeutically-relevant concentrations." The manuscript says competing pharmacology is "substantial" but never does the arithmetic. If 112 µM counts as therapeutically relevant for hydroxybupropion, the same reasoning has to be applied to the 16–54 µM α7 numbers — which cuts in *favour* of H1. Either way, the comparison belongs in §5 explicitly rather than being left for the reader.

### 4.5 Two smaller things

- **§8's search counts** (208 drug–nicotinic records, 38 dissociation/gating, 191 α7–seizure, zero α7–depersonalization, "528 journal records") are process claims from the September session. PubMed counts drift daily, so these are unverifiable after the fact and will not reproduce. Either date-stamp each query with its exact string, or drop the numbers and keep the method description. The paper's own guardrail — search negatives are not absence of literature — applies to its own counts.
- **`hypothesis_novelty_and_submission_review.md`** was written against a single-hypothesis draft: its proposed title is "Could α7 nicotinic receptor inhibition contribute to bupropion-associated depersonalization?" with no mention of H2. The manuscript is now a two-hypothesis paper. The assessment, the novelty argument and the venue reasoning were never updated for the seizure hypothesis.

---

## 5. The science, plainly

### What α7 is

The α7 nicotinic acetylcholine receptor is an ion channel sitting in the membranes of brain cells.
Five identical α7 protein subunits form a ring around a central pore. Acetylcholine (or choline)
binds at the top, the pore opens for a few milliseconds, positive ions — sodium and, unusually for
this family, a lot of calcium — flow in, and the cell depolarises. Then it shuts itself off very fast.
Two of its traits matter here: high calcium permeability, and extremely rapid desensitization.

Why it could matter for symptoms: α7 channels sit on **inhibitory interneurons** — the GABA-releasing
cells that keep principal neurons in check. Activate α7 on an interneuron and it fires more, so the
principal cells it targets get more inhibition. **Block** α7 and you remove a layer of that inhibitory
control. That is the mechanism both hypotheses rest on, and refs 12 and 13 are the clean
demonstrations of it.

The catch, which your paper handles well: α7 is on many cell types, including excitatory ones. Whether
blocking it nets more or less excitation depends on which cells it was working on. Refs 10 and 11
show nicotinic activation producing either inhibition or disinhibition in the same slice depending on
the connection. Ref 33 shows mice with no α7 at all seizing from nicotine exactly like normal mice.
That is why §4's "why a universal continuum is not supported" is the right section to have written.

### Why bupropion and its metabolites

Bupropion is a nicotinic antagonist — that has been established since Slemmer 2000 (ref 2) and is the
accepted account of why it helps with smoking cessation. It blocks α7 specifically (refs 4, 5, 6), but
**weakly** compared with other nicotinic subtypes: Slemmer found it roughly 50× and 12× more effective
at α3β2 and α4β2 than at α7.

The metabolites are where the real opening is. Bupropion is extensively metabolised, and
hydroxybupropion circulates at several times the parent's concentration. Its α7 activity has
**never been measured** — Lukas's panel (ref 7) has α4β2, α3β4, α4β4 and muscle receptors, and no α7.
That gap is genuine, and it is the honest contribution of this paper: not "we found a mechanism" but
"here is a specific, cheap, unmeasured experiment that someone should run, and here is the geometry to
test." Keep that framing; it is defensible in a way a mechanism claim is not.

### What docking can and can't tell you

Docking takes a receptor structure and a small molecule, tries the molecule in many positions and
conformations inside a defined box, scores each one with an empirical function, and ranks them. It
answers one question: *can this molecule fit here, and in what geometry?*

It does **not** give you binding affinity. A Vina score in kcal/mol is not a free energy you can turn
into a Kᵢ or an IC₅₀, and the numbers are not comparable between different molecules as though they
were potencies. It does not tell you whether binding happens in a living brain at achievable
concentrations, and it says nothing about what the receptor does afterwards — blocked, activated,
modulated. Those are three different functional outcomes from the same pose.

**You have your own proof of this, and it is the best thing in the delivery.** The I34/8V82 control:
the experimentally determined pose from the deposited structure *was found* by the search, but ranked
**second**, beaten by a wrong pose by **0.028–0.085 kcal/mol** across three seeds. If the scoring
function mis-ranks the known right answer by less than a tenth of a kcal/mol, then ranking different
compounds by score is meaningless. You demonstrated the limitation of your own method, in your own
control, and didn't retune it away. Lead with that when you talk to a professor — it is the single
most credible move in the whole project.

### The question a reviewer will ask first

α7 IC₅₀ values for bupropion run **16–54 µM** (refs 4, 5). Therapeutic plasma concentrations are far
below that, and the measured unbound brain/plasma ratio is about 1.9 (ref 38) — close to 1, not a
large multiplier. So: **at normal doses, is there ever enough drug at the receptor to inhibit it?**

The manuscript knows this is the crux — §5 exists for it and the abstract says docking "supplies
neither potency nor human target engagement." But it never writes the arithmetic down. That is the
first thing anyone competent will ask, and the answer determines whether this is a hypothesis about
ordinary treatment or only about overdose. Both are publishable; they are not the same paper. Note
that overdose is where bupropion seizures actually cluster, so the high-exposure version of H2 may be
the stronger one.

---

## 6. Decisions only you can make

I'm not making these for you. Each one changes what the paper is.

1. **One hypothesis or two?** H2 (shared α7 mechanism for dissociation and seizures) needs three
   conditions demonstrated, by §4's own admission, and none of them are. It is the more interesting
   claim and the more exposed one. Dropping it gives you a tighter paper and makes the existing
   novelty review valid again; keeping it means rewriting that review.
2. **Therapeutic exposure or overdose?** Write the concentration arithmetic explicitly and pick the
   regime you're claiming. This decision cascades into the abstract, §5, and both hypotheses.
3. **Keep the docking as a structural prediction, or cut it?** Recommended: keep it, narrowed to
   §4.3's wording, and lead with the control failure as a methods strength. The alternative — cutting
   it — loses your only original data.
4. **Which papers to request from Lasell.** My ranking by what it changes: **Grunebaum 2013** (fixes
   §4.2, your only clinical datum), **Dale 2008** (fixes §4.1), **Damaj 2004** and **Bondarev 2003**
   (the two the paper admits it never read; both central), then Papke 2011 and Lukas 2010 to move
   those from indexed text to the actual PDFs. That's six, and the first two are the ones that fix
   errors rather than upgrade sourcing.
5. **Which professor.** This needs a biochem or neuropharmacology faculty member who will put their
   name to the premise. The Journal of Young Investigators route *requires* a sponsor who verifies the
   calculations, so this isn't optional — it's an eligibility condition. Tell me who's plausible at
   Lasell and we'll draft the email together; it should lead with the specific unmeasured experiment
   and the control failure, not with the hypothesis.
6. **Fix or delete the §8 search counts** (§4.5).

### Not a decision — just do it

- §4.1 and §4.2 are factual errors and should be corrected or cut regardless of everything above.
- §4.4's two omissions should go in; they're already in your reference list.
- Say which control set §6 reports (§4.3, last paragraph).

---

*Audit method: Crossref REST API for DOI metadata; NCBI E-utilities (esearch/efetch) for PMIDs and
abstracts; DailyMed SPL XML for the label; repo CSVs for all docking counts. No docking, simulation or
re-analysis was run, and the manuscript was not edited. Where a claim depends on full text that wasn't
accessible, it is tagged ABS or FT rather than treated as verified — "plausible" is not "checked."*
