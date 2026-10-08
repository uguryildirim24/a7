# Novelty and submission review

Historical September 26, 2026 record for an older single-hypothesis draft.
The manuscript now has two hypotheses. Venue and policy descriptions below are
historical, not current submission guidance. Read with
[the corrections](docs/review_record.md).

**26 September 2026 — companion to the hypothesis manuscript draft.** Scope: the proposed α7 contribution to bupropion-associated depersonalization, with the completed metabolite docking as preliminary structural analysis. No new docking, exposure simulation, circuit simulation or laboratory experiment was run. The monitoring automation remains paused. Nothing was submitted or sent to another person.

## Assessment

The material supports a **faculty-review draft of a hypothesis paper with exploratory computational results**. It does not currently support a claim that α7 blockade causes bupropion-associated depersonalization. The specific synthesis and stereoisomer-resolved structural observations may be a contribution; this focused audit does not establish priority or guarantee journal acceptance.

The proposed title keeps the causal claim open: *Could α7 nicotinic receptor inhibition contribute to bupropion-associated depersonalization? A mechanistic hypothesis with exploratory stereoisomer-resolved docking.*

## What is established already

| Topic | Prior evidence | Consequence for novelty |
|---|---|---|
| Bupropion inhibits nicotinic receptors | Slemmer et al., 2000, PMID 10991997 | Not a new observation |
| Parent bupropion inhibits α7 | Vázquez-Gómez et al., 2014, PMID 25016090; Duarte et al., 2021, PMID 33668529 | The receptor interaction cannot be presented as a discovery of this project |
| Hydroxybupropion has stereoselective transporter/nicotinic actions | Damaj et al., 2004, PMID 15322260; Carroll et al., 2011, PMID 21319801 | A metabolite-based or broadly nicotinic explanation is not itself novel |
| α7-related pharmacology can influence sensory processing | Luntz-Leybman et al., 1992, PMID 1525643; Olincy et al., 2006, PMID 16754836 | Background for a hypothesis, not a direct bridge to depersonalization |
| α7/P50 effects are not uniformly positive | Winterer et al., 2013, PMID 22766391 | A necessary counterexample; do not write a one-direction receptor-to-gating rule |
| Sensory gating has non-α7 contributions | Radek et al., 2006, PMID 16767415 | α4β2 is a competing mechanism |
| Depersonalization appears in bupropion labeling | Current DailyMed XL label, section 6.2 | Postmarketing observation, not frequency or causal proof |

The primary-source links and verified bibliographic metadata are in the manuscript references. The publication dates, rather than search-engine crawl dates, were used.

## Material correction found during this audit

An earlier synthesis claimed no P50 or prepulse-inhibition measurements in depersonalization disorder. **Dale et al. (2008), PMID 18830396**, contradicts that blanket claim: eight participants had depersonalization disorder, including six with dissociative amnesia. The findings do not establish an α7 or bupropion mechanism. [Primary paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC2526371/)

The draft includes that study and distinguishes P50 sensory gating, startle prepulse inhibition and subjective depersonalization. The older source artifact was preserved rather than silently overwritten. The audit also found an LSD study measuring both altered subjective experiences and prepulse inhibition (Schmid et al., 2015, PMID 25575620); drug-induced depersonalization is therefore not an unstudied electrophysiological domain. Its pharmacology does not establish an α7 mechanism.

## Focused search record and its limits

Source: NCBI PubMed ESearch, 26 September 2026, default automatic term mapping, relevance sort, maximum 1,000 returned IDs. Exact query translations and returned IDs are retained in the local working search log. Public APIs were called without an email parameter or personal identifiers.

| Query | Hits | Screening interpretation |
|---|---:|---|
| `(bupropion OR hydroxybupropion) AND (depersonalization OR depersonalisation OR derealization OR derealisation)` | 1 | PMID 41783550: an OCD treatment case with pre-existing derealization and intolerance of several drugs; not a test of the proposed α7 mechanism |
| `(alpha7 OR "alpha 7" OR CHRNA7 OR "alpha-7") AND (depersonalization OR depersonalisation OR derealization OR derealisation)` | 0 | No record returned by this particular indexed query; not proof of global absence |
| `hydroxybupropion AND (alpha7 OR "alpha 7" OR CHRNA7 OR "alpha-7")` | 0 | Insufficient to claim that metabolite α7 pharmacology has never been measured |
| `(depersonalization OR depersonalisation OR derealization OR derealisation) AND ("sensory gating" OR "prepulse inhibition" OR P50)` | 3 | PMIDs 37626488, 37857620, 25575620: PTSD fear extinction, ketamine altered states, and LSD effects; the relevant Dale subgroup was discovered through full-text searching, illustrating an indexing limitation |
| `(depersonalization OR depersonalisation OR derealization OR derealisation) AND (cholinergic OR nicotine OR nicotinic)` | 8 | Titles/abstracts included burnout-related depersonalization, case reports and other cholinergic contexts; none established the proposed bupropion–α7 clinical chain |
| `hydroxybupropion AND (nicotinic OR CHRNA7)` | 13 | Targeted titles/abstracts reviewed for metabolite pharmacology; findings at α4β2, α3β4 and other receptors must not be relabeled as α7 results |

A broader bupropion/nicotinic discovery query was also saved, but its complete result set was **not** systematically screened. Targeted primary-paper and full-text searches supplemented the indexed queries. This is not a PRISMA review or an exhaustive search of all databases, preprints, patents and unpublished work. Do not use “first,” “never studied,” “no evidence exists,” or “novel mechanism demonstrated” on the basis of these counts. A librarian-assisted citation search and faculty assessment of novelty remain appropriate before submission.

Full text for Damaj et al. (2004) could not be retrieved from the public publisher/repository links tested. The PubMed record and the authors’ institutional abstract were verified. The draft uses only the reported transporter/α4β2 findings and makes no claim about an uninspected α7 table. The full article should be checked through legitimate institutional access before the final literature review is approved. This access limit is not evidence of absent data.

## What our data add—and the boundaries

- The completed, unchanged matrix supplies a chemical-form- and stereoisomer-resolved map of modeled locations across two α7 templates and four search regions. It contains 672 metabolite/parent jobs plus 12 controls, 12,282 emitted metabolite/parent poses and 154 representative complexes.
- The strongest repeatability observation among the six main metabolite stereoisomers is (2R,3R)-hydroxybupropion: pore placement in all three mid-pore seeds within each of two forms and two states. This is an exploratory observation made after examining the full panel, not a preregistered stereoisomer-superiority test.
- Counts are not binding probabilities, biological sample sizes or evidence of greater affinity. Other sites and receptor/form conditions remain visible.
- Parent-only and matched-panel campaigns used different box extents and gave different rank-1 location patterns. Preserve this setup sensitivity; do not claim parent bupropion cannot occupy the pore.
- The I34/8V82 rank-1 failure, rank-2 recovery, 13 rank-1 short-contact flags and 93 all-mode flags remain in the results. There was no experimental pore-blocker control in this study.
- The loss of 12 historical interrupted-job receipts/logs is disclosed. The final target matrix has successful receipts, but the historical failure files are not recoverable and cannot be claimed preserved.
- The two hydroxybupropion O-glucuronide species remain structurally qualified candidates; the broader panel is not a complete inventory of every human metabolite.

## Submission routes checked

**Medical Hypotheses — a potential format match.** The publisher’s stated scope includes theoretical biomedical papers and hypotheses with incomplete experimental support, with editorial and external review of premise, originality and plausibility. This fits the *type* of manuscript; it does not establish that this particular draft meets the journal’s novelty threshold. The current journal-specific author guide could not be retrieved in this session, so word limits, fees, required declarations and the final submission checklist are not verified here. [Publisher scope](https://shop.elsevier.com/journals/medical-hypotheses/0306-9877)

**Journal of Young Investigators — conditional undergraduate route.** Its official FAQ accepts theoretical work only with a qualified sponsor who will verify the calculations; advisor oversight is also required for reviews. Original research must be written by the undergraduate author(s), and a supervisor-signed contract is required. A suitable faculty mentor is therefore a real eligibility requirement for this route. The linked AI-policy PDF could not be retrieved by the research tool; its contents and suitability for this AI-assisted workflow remain unverified. The similarly named `young-innovator.org` is not the Journal of Young Investigators and was not used as its policy source. [FAQ](https://www.jyi.org/submit/submission-faq) · [Submission page](https://www.jyi.org/submit)

**AI disclosure must describe the actual work.** Elsevier’s current general policy requires disclosure of AI assistance and puts responsibility for verification and interpretation on human authors. AI use in the research process belongs in Methods, beyond a writing-only disclosure. The draft therefore describes orchestration, preparation, analysis, checks and writing assistance, and does not assert that human author/faculty review has already occurred. [Publisher policy](https://www.elsevier.com/about/policies-and-standards/generative-ai-policies-for-journals)

## Faculty review needed before a submission decision

1. Does the causal proposal add a useful, sufficiently distinct synthesis once competing nicotinic, catecholaminergic and clinical explanations are considered?
2. Are the source-qualified metabolite identities, protonation assumptions, receptor preparations and geometric classification appropriate for the limited structural claim? Can the reviewer reproduce selected results from the frozen inputs?
3. Should the paper remain a hypothesis article with docking as supplementary material, or would a narrower computational-methods report be more defensible? The current draft takes the former approach.
4. Does the human author understand and endorse every argument and calculation, and can the venue’s authorship, AI, data-access and integrity requirements be met?

The draft is complete enough for this review. It still needs author/affiliation information, substantive human revision, confirmed contributions and declarations, a final venue-specific format check, and a persistent public data location if required. No faculty agreement, institutional approval, public repository deposit, journal acceptance or submission is implied.
