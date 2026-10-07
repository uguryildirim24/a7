# Bupropion, its metabolites and α7: what the experiments actually show

**26 September 2026 · Receptor evidence and connection audit · Both hypotheses formulated**

The table now contains **104 observations from 84 papers**, with the compound, receptor, preparation, assay, source location and verification level recorded separately. [Open the evidence table](/path/to/project/outputs/bupropion_receptor_evidence.csv). The completed deeper pass adds 26 more papers beyond the previous 58, including circuit experiments, negative findings, clinical gating studies and alternative mechanisms. The separate hypothesis document now develops both proposed mechanisms. Rows include direct experiments, downstream findings and comparator studies; they are not 104 independent confirmations. This is a focused critical review with explicit coverage limits, not an exhaustive systematic review.

**Current assessment:** experimental support is strongest for parent bupropion inhibiting α7. There is also evidence linking α7 to inhibitory circuits and documenting dissociative experiences during some focal seizures. The proposed connection through particular bupropion metabolites, at human brain exposures, remains a testable hypothesis. Docking supplies candidate locations for testing; it does not establish this causal chain.

## Both hypotheses are now formulated

The [completed hypothesis document](/path/to/project/outputs/bupropion_alpha7_hypothesis_draft.pdf) sets out the dissociation hypothesis and the shared graded-mechanism hypothesis, with separate predictions and rejection criteria. It incorporates the following additional checks:

- Bertelsen 2015 did not find the proposed P50/PPI association.
- The 2014 injury study showed increased alpha7 activity alongside reduced GABA inhibition.
- The 2020 septum–hippocampus seizure circuit experiment identified somatostatin cells, rather than PV cells, as its necessary downstream population.
- A 2024 rat disposition study separated active uptake from intracellular trapping; it did not establish human alpha7 occupancy.
- A retracted 2019 alpha7/seizure paper was excluded. Conference-only GABAA and deuterated-compound patent results remain qualified supplementary leads.

These corrections are reflected in the expanded CSV and the cited hypothesis document.

## Direct α7 pharmacology

**Parent bupropion has direct experimental activity at α7, but its measured potency depends on the assay.** Papke et al. (2011), now included in the revised draft, found that human α7 expressed in frog oocytes had an IC₅₀ of **46 ± 7 µM during coapplication** and **16 ± 3 µM after 30 minutes of bath exposure**. These protocols also used different acetylcholine concentrations, so the difference cannot be attributed solely to exposure time. [Primary Table 4 and Figure 7](https://pmc.ncbi.nlm.nih.gov/articles/PMC3083103/)

| Parent-bupropion experiment | What was measured | What we can say |
|---|---|---|
| Slemmer 2000 | Functional inhibition of α3β2, α4β2 and α7 | α7 inhibition exists; subtype rankings belong to that assay. [Paper](https://pubmed.ncbi.nlm.nih.gov/10991997/) |
| Alkondon & Albuquerque 2005 | Rat hippocampal interneuron responses at 1 µM | Reported inhibition: α7-like 0%, α4β2-like 15%, α3β4-like 56%. [Paper](https://pubmed.ncbi.nlm.nih.gov/15647329/) |
| Papke 2011 | Human α7 in oocytes; acute and prolonged application | 46 versus 16 µM IC₅₀ under the two protocols above. [Paper](https://pubmed.ncbi.nlm.nih.gov/21285282/) |
| Vázquez-Gómez 2014 | Expressed α7 plus native neuronal recordings | Calcium-response IC₅₀ 54 µM; binding estimate Kᵢ 63 µM; partial native-current inhibition at 10 µM. [Paper](https://pubmed.ncbi.nlm.nih.gov/25016090/) |
| Duarte 2021 | Rat CA1 interneuron α7-containing currents | At 50 µM, current was 0.52 ± 0.04 of control; inhibition also occurred at 20 µM. The ratio is not a separately fitted IC₅₀. [Paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC7918632/) |

These results are not one combined dose-response curve. They use different receptor preparations, agonists, timing and endpoints. None measures receptor inhibition in a person taking therapeutic bupropion.

## Hydroxybupropion: the receptor distinction matters

I inspected the full methods and Table 1 of Lukas et al. (2010), including the human cell lines and receptor panel. These are functional IC₅₀ values in µM; lower means greater inhibitory potency **within this assay**.

| Compound | α4β2 | α3β4* | α7 |
|---|---:|---:|---|
| Parent bupropion | 12 | 1.8 | Not in this assay panel |
| (2S,3S)-hydroxybupropion | 3.3 | 11 | Not in this assay panel |
| (2R,3R)-hydroxybupropion | 31 | 6.5 | Not in this assay panel |

The S,S metabolite is more potent than parent at α4β2, but both hydroxy forms are less potent at α3β4*. The panel also includes α4β4 and muscle receptors. The asterisk permits additional receptor subunits. [Lukas 2010, Table 1](https://pmc.ncbi.nlm.nih.gov/articles/PMC2895766/)

Carroll et al. (2011) repeats parent/hydroxy reference entries with a footnote attributing them to an earlier reference. I have not counted these controls as an independent replication. Some entries differ between the papers, so the evidence table retains study-specific values. Lukas 2010 belongs to the same research lineage and explicitly discusses earlier S,S results; its Table 1 does not carry the same reuse footnote. The available text therefore does not justify either calling all its entries copied or counting them as an independent laboratory replication. [Carroll 2011, Table 1](https://pmc.ncbi.nlm.nih.gov/articles/PMC3048909/) · [Lukas 2010](https://pmc.ncbi.nlm.nih.gov/articles/PMC2895766/)

**The α7 potency of each hydroxy stereoisomer remains unverified in the sources extracted here.** “Not measured in these panels” is supported; “nobody has ever measured it” is not. Nor can a general statement about “most nicotinic receptors” establish weaker or stronger α7 activity.

## Coverage of the actual metabolites

| Compound or family | Direct α7 measurement verified in this pass? | Other relevant evidence |
|---|---|---|
| Parent bupropion | Yes; mostly unresolved/racemic material | Multiple functional preparations; no verified separate R-versus-S α7 comparison here |
| R,R- and S,S-hydroxybupropion | No | Direct stereoselective non-α7 nicotinic assays above |
| Threohydrobupropion | No | Bondarev 2003 reports α3β4 functional inhibition for tested metabolites and includes threo isomers; complete PDF remains to be read. Optical signs must not be silently converted to absolute configurations. [Paper](https://pubmed.ncbi.nlm.nih.gov/12909199/) |
| Erythrohydrobupropion | No | No compound-specific receptor result established by the extracted studies |
| 4′-hydroxylated metabolites | No | Structural/metabolic identification must be distinguished from receptor pharmacology |
| Hydroxy/hydro glucuronides, other conjugates and downstream acids | No | Docking inclusion is not evidence of measured α7 activity or brain exposure |

“No” here means **not verified in this pass**, not inactive and not proven absent from all literature. Synthetic bupropion analogues and the photoprobe SADU-3-72 are kept separate from human metabolites.

## Findings that prevent a misleading α7-only story

- **Binding location is not settled by a docking pose.** Torpedo muscle-receptor photolabeling supports both a pore region and an αM1 region. A 2024 bacterial GLIC study combines docking with mutagenesis and currents to support an intersubunit site. These inform possibilities, but neither locates a metabolite in human α7. [Pandhare 2012](https://pmc.ncbi.nlm.nih.gov/articles/PMC3315157/) · [Do 2024](https://pmc.ncbi.nlm.nih.gov/articles/PMC11309978/)
- **The same drugs affect other channels.** Direct hydroxybupropion experiments also exist at 5-HT₃ receptors. Those results stay in their own receptor category; the authors’ clinical-exposure interpretations are not treated as measured human target engagement. [Pandhare 2017](https://pmc.ncbi.nlm.nih.gov/articles/PMC5148637/) · [Stuebler & Jansen 2020](https://pmc.ncbi.nlm.nih.gov/articles/PMC6978693/)
- **Human-cell seizure screening supplies competing mechanisms.** Rockley et al. (2023) found bupropion inhibition at α4β2 and potassium channels in a 14-channel panel, plus changes in bursting in human stem-cell-derived neuronal cultures. The panel did not include α7, and these experiments do not identify which channel caused the network changes. [Primary paper, methods and results](https://www.apconix.com/wp-content/uploads/2024/01/An-Integrated-approach.pdf)
- **A downstream α7-related result is not an α7 potency assay.** The 2021 human-macrophage paper measured cytokine changes with bupropion. It does not directly measure selective channel inhibition at its applied concentration. [Ríos 2021](https://pmc.ncbi.nlm.nih.gov/articles/PMC8102909/)
- **Human imaging does not automatically demonstrate drug occupancy.** A 48-smoker PET study found α4β2* receptor measures declined with smoking reduction or cessation, with no treatment-type difference between bupropion, counseling and placebo. It did not measure α7 engagement. [Brody 2013](https://pubmed.ncbi.nlm.nih.gov/23429692/)
- **Another directly measured channel effect deserves consideration.** Bupropion inhibited mouse TRESK expressed in HEK cells, with an IC₅₀ of 160 ± 17 µM; rat TREK-2 was unaffected under the tested conditions. This is an alternative channel observation, without demonstrated human engagement or seizure mediation. [Park 2016, results and Figure 2](https://pmc.ncbi.nlm.nih.gov/articles/PMC4930906/)

## What the published brain-distribution studies establish

Cremers et al. measured unbound bupropion and hydroxybupropion in rat plasma and brain extracellular fluid by microdialysis. Their fitted steady-state ratios were 1.9 and 1.7. The human concentrations in that paper were translated **predictions**, not direct measurements in human brains. [Cremers 2016, abstract](https://pubmed.ncbi.nlm.nih.gov/26916207/)

Bhattacharya et al. used stereoselective measurements and companion equilibrium dialysis in rats. Brain/plasma unbound ratios changed over time; at 4–6 hours they were below one for parent enantiomers and approximately one for metabolites formed after parent administration. These methods differ from microdialysis, so the papers should not be treated as interchangeable measurements or a simple contradiction. Neither establishes human α7 inhibition by a particular metabolite. Total tissue accumulation, unbound exposure and receptor inhibition are separate measurements. No new exposure model was fitted here. [Bhattacharya 2023, abstract](https://pubmed.ncbi.nlm.nih.gov/36823342/)

## Testing the proposed connections

**The supporting pieces exist, but several experiments challenge a single-direction chain from α7 blockade to failed filtering, depersonalization and seizures.** This is an interpretation across the studies below, not a result demonstrated by any one experiment.

| Proposed connection | What supports it | What limits the connection |
|---|---|---|
| α7 activity influences inhibitory neurons | Paired recordings show α7-dependent inhibition of pyramidal cells. [Buhler 2002](https://pubmed.ncbi.nlm.nih.gov/11784770/) | Nicotinic activation can also disinhibit pyramidal cells, and α7 can reduce GABA responses **onto interneurons**. The target cell and circuit matter. [Ji 2000](https://pubmed.ncbi.nlm.nih.gov/10805668/) · [Wanaverbecq 2007](https://pmc.ncbi.nlm.nih.gov/articles/PMC2889598/) |
| Reduced α7 signaling can facilitate seizures | Local MLA shortened seizure latencies in a mouse pilocarpine model; the α7 agonist did not significantly improve those outcomes. [Sun 2021](https://pmc.ncbi.nlm.nih.gov/articles/PMC8072353/) | Systemic MLA instead reduced nicotine-induced seizures in another study, and α7-null mice retained similar nicotine seizure dose-response curves. These are different challenges, routes and interventions. [Iha 2017](https://pmc.ncbi.nlm.nih.gov/articles/PMC5298991/) · [Franceschini 2002](https://pubmed.ncbi.nlm.nih.gov/11834293/) |
| Bupropion metabolites can contribute to convulsive effects | Hydroxy, threo and erythro metabolites produced convulsions in an acute mouse comparison. [Silverstone 2008](https://pmc.ncbi.nlm.nih.gov/articles/PMC2576274/) | No receptor was measured; stereoisomers were not separately resolved. Equimolar injected doses do not establish a human risk ranking or α7 mediation. |
| Nicotinic signaling affects sensory gating | A small DMXB-A trial improved P50 inhibition in schizophrenia. [Olincy 2006](https://pubmed.ncbi.nlm.nih.gov/16754836/) | An α7 PAM trial found no P50 benefit; α4β2 also contributes to paired-click responses in mice. Different ligands/populations are not direct replications. [Winterer 2013](https://pubmed.ncbi.nlm.nih.gov/22766391/) · [Radek 2006](https://pubmed.ncbi.nlm.nih.gov/16767415/) |
| Altered sensory processing relates to depersonalization | DP patients showed reduced early suppression of unattended visual stimuli. [Schabinger 2018](https://pubmed.ncbi.nlm.nih.gov/29486234/) | This was visual P1, not auditory P50 or α7. A small depersonalization subgroup in a separate PPI study broadly resembled controls. [Dale 2008](https://pmc.ncbi.nlm.nih.gov/articles/PMC2526371/) |

### Direct challenges we must retain

**Bupropion did not impair PPI in the Mori mouse experiment**, including after sensitization. This directly challenges a prediction that bupropion invariably impairs sensorimotor gating. It does not settle its effects on human P50 or DPDR. [Mori 2013](https://pubmed.ncbi.nlm.nih.gov/23993950/)

**Even bupropion’s seizure effects vary with the model and dose.** Tutka et al. found protection against maximal electroshock at lower doses and convulsions at higher doses, with no effect on the tested PTZ/kainate outcomes. No α7 mechanism was established. [Tutka 2004](https://pubmed.ncbi.nlm.nih.gov/15363958/) Stitzel’s intracerebroventricular experiments also differed from Iha’s systemic protocol: MLA did not prevent nicotine seizures and caused seizures itself. These findings should not be pooled as interchangeable α7 tests. [Stitzel 2000](https://pubmed.ncbi.nlm.nih.gov/10942032/)

**“Unreality” in a paper title need not mean DPDR.** Croft’s P50 study concerned perceptual anomalies and magical ideation in 36 healthy volunteers. It is a correlational schizotypy result, not evidence of bupropion-induced depersonalization. [Croft 2001](https://pubmed.ncbi.nlm.nih.gov/11566161/)

### What remains unconnected

**A further circuit experiment supports one part of the proposed mechanism.** In rat hippocampal slices, Townsend et al. found that an α7 agonist increased inhibitory GABA currents and reduced evoked pyramidal firing. MLA increased evoked firing and blocked the agonist effect. This supports an α7-dependent inhibitory influence in that preparation; bupropion, its metabolites, DPDR and seizures were not tested. [Townsend 2016, Figures 2 and 5](https://pmc.ncbi.nlm.nih.gov/articles/PMC5133305/)

**Human seizure-associated dissociation is documented.** Heydrich et al. retrospectively studied nine patients with ictal depersonalization-like experiences and seven with derealization-like experiences, plus 28 epilepsy controls. Depersonalization was predominantly associated with frontal seizure networks and derealization with temporal networks. These were selected patients with drug-resistant focal epilepsy; patients reporting both experiences together were excluded. This supports a clinical overlap worth investigating, but does not show that primary DPDR is epilepsy or identify bupropion or α7 as the cause. [Heydrich 2019, methods and results](https://pmc.ncbi.nlm.nih.gov/articles/PMC6764488/)

**A bupropion clinical trial must be interpreted at the endpoint it actually reports.** In a post hoc comparison of bupropion XL and paroxetine CR in 74 depressed adults, a composite “Disturbed Thinking” score included depersonalization/derealization together with other symptoms. There was no differential treatment effect on that factor. This cannot be converted into a separate positive or negative DPDR result, and no α7 mechanism was measured. [Grunebaum 2013, results and Figure 1 footnote](https://pmc.ncbi.nlm.nih.gov/articles/PMC4313534/)

The studies reviewed here do not establish that therapeutic bupropion or a particular metabolite inhibits α7 enough in a relevant human circuit to cause DPDR, nor that DPDR and seizures are points on one α7-driven dose continuum. Sun’s PV interpretation uses staining and pharmacology rather than a PV-specific receptor deletion. The human epilepsy-tissue study found MLA-associated changes in glutamatergic events, but its accessible abstract does not give enough detail to infer their direction or transfer them to DPDR. [Banerjee 2020](https://doi.org/10.1007/s00702-020-02239-2)

Our docking remains preliminary evidence about modeled locations. It cannot supply a missing metabolite IC₅₀, determine the net effect on a brain circuit, or complete this clinical causal chain. A defensible hypothesis must specify the compound/form, circuit, exposure and measurable outcome, and allow the possibility of no effect or an opposite effect.

## What has been searched—and what remains open

Consensus was used for discovery, followed by primary PubMed records, PMC/NCBI and Europe PMC text, and targeted web searches. The three initial PubMed searches returned 727 parent/nicotinic records, 29 metabolite/receptor records and 13 minor-metabolite/receptor records: **755 unique records after deduplication**. This is a discovery pool, not 755 papers read.

All 17 records from the targeted drug/metabolite–α7 query were screened; one lacked an abstract and received title screening only. The 84 selected papers in the evidence table have explicit access levels: full-text sections/tables, indexed primary sections, or abstract only. Earlier follow-ups added 18 and then six primary metadata records. The deeper pass added six explicit PubMed searches, a 45-edge Scite backward graph, targeted Consensus discovery and 26 additional extracted papers. Metadata and discovery counts are separate from papers read. Consensus searches sometimes returned unrelated papers; those results were not treated as evidence that a topic has no literature.

Reference lists and Europe PMC forward-citation lists for Damaj 2004, Bondarev 2003 and Vázquez-Gómez 2014 were retrieved; their 169, 80 and 17 indexed citing records are overlapping discovery leads, not independent experiments or a completed citation-context audit. One historical-code search expanded into unrelated records and was rejected; the corrected search is retained in the working log.

**Scite citation tracing now covers three core studies:** Damaj 2004 returned 210 incoming edges, 104 with snippets; Papke 2011 returned 61, with 38 containing snippets; Vázquez-Gómez 2014 returned 22, with 13 containing snippets. None of these graphs was truncated within Scite's resolved coverage. These are overlapping citation links, not counts of full papers read or all citations worldwide. Relevant contexts and supporting-labeled edges were checked; full-text follow-up remains selective. Two preprint/journal pairs in the Vázquez graph must be collapsed when counting studies.

The nine citing papers with supporting-labeled edges to Damaj concern a mixture of pharmacokinetics, transporter effects, behavior and non-α7 receptor data. The two supporting-labeled edges to Papke concern neonicotinoids and zebrafish receptor pharmacology. These labels do not establish nine or two new demonstrations of metabolite inhibition of human α7. The original Damaj article remains full-text restricted through Scite, and Bondarev returned no readable body text; previously verified primary abstracts remain the basis for their evidence-table entries.

One extraction error was caught: a Scite citation snippet rendered a concentration as 20 mM, while the retrieved primary text reports 20 µM. The primary text controls the value; no potency or exposure conclusion is based on the corrupted snippet. [Stuebler & Jansen, Figure 7 and discussion](https://pmc.ncbi.nlm.nih.gov/articles/PMC6978693/)

Remaining work before calling the review comprehensive:

1. Obtain and inspect the complete original Damaj 2004 and Bondarev 2003 articles and supplements; their abstracts do not settle every subtype question.
2. Finish screening the broader discovery pool and citation trails, with reasons for exclusions. Receptor data can occur in papers whose titles do not name bupropion.
3. Extend Scite tracing beyond the three core graphs and inspect the surrounding text of unresolved relevant citations. Scite access is working; access to some original full texts remains restricted.
4. Extend the targeted circuit/sensory review into a fuller clinical assessment if a comprehensive review is pursued. The current formulation of both hypotheses already incorporates contradictory and null findings. Neither a positive citation count nor an automated support/contrast label establishes replication of our specific claim.

Both hypotheses have now been written in the linked revised manuscript. The literature work and document revision used the preserved docking results; no new docking, exposure model or circuit simulation was performed.
