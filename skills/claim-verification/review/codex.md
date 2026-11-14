# Codex review: claim-verification
VERDICT: FIX
## Findings

- SR-01 | medium | attribution | “one claim in three in published ALMA work is stated as partial” | The totals match, but the aggregate counts support levels **assigned by cards**, not qualifications stated by authors. | Say “31.6% of card-rated claims were classified as partially supported”; do not infer authors’ wording.

- SR-02 | high | science | “no negatives or <1 expected false source” | Zero observed negative peaks does not establish an expected false count below one. The pack’s 2023ApJ...953...75H entry reports no negatives at S/N 5.2 **and only 83% purity**. Checklist item 3 also combines conditions that the cited papers establish separately. | Distinguish negative-peak thresholds, estimated purity and expected false counts; calibrate the chosen statistic over the actual search and report its uncertainty.

- SR-03 | medium | attribution | “4.0–6.2 peak S/N; purity 0.7–0.99” | The same row cites S/N **3.6** for 2024MNRAS.528.5019H and purity **>0.99** for 2024ApJS..275...36F. Both fall outside the stated bounds. | Correct the bounds and preserve strict inequalities; distinguish peak thresholds from compound finder criteria.

- SR-04 | medium | attribution | “3 sigma at the fixed position, plus consecutive channels or a second line” | 2024PSJ.....5..221C supplies the known-location 3σ criterion. 2024AJ....168..151J instead requires detections **in both bands and at least five consecutive significant channels**; it does not supply this interchangeable “or” rule. | Present these as separate, study-specific criteria with their conjunctions intact.

- SR-05 | medium | attribution | “robust at SNR >= 20 in one sample” | For 2021A&A...654A..37D, the quoted excerpt says four lines **were robustly detected with SNR ≥20**. It does not establish 20 as the required acceptance threshold separating robust from tentative detections. | Describe achieved significance rather than promoting it to a detection cutoff.

- SR-06 | medium | unsupported | “Common choice”; “Resolution for kinematics >= 3–4 beams” | The pack provides examples, not frequencies establishing common defaults. The resolution row also combines three beams across a velocity gradient, four beams inside an effective radius, five across a component, and the specialized ζ = 2r_soi/θ_FWHM black-hole criterion. | Rename the table “Study-specific examples”; retain each scale definition and scientific objective rather than giving a transferable beam-count range.

- SR-07 | high | science | “Tentative … one line, one epoch, or a p-value short of 3 sigma” | These are not sufficient conditions for tentativeness. The pack rates the single detected CO transition in 2020MNRAS.491.1174M as supported, and the correlation with p = 0.02 in 2025ApJ...995..108J as supported. | Base the label on identification, search trials, reliability and robustness; remove automatic downgrades for one transition, one epoch or significance below 3σ.

- SR-08 | medium | science | “quote the empirical p as a bound” | An empirical exceedance fraction is an estimate, not automatically a probability bound; zero exceedances especially cannot justify p = 0. | Report trial and exceedance counts with a confidence bound or calibrated Monte Carlo p-value. State when the simulation cannot resolve the claimed tail.

- SR-09 | medium | science | “ln evidence >= 5” | The model-selection row drops “ratio.” The pack’s 2024ApJ...971...17F criterion is **ln evidence ratio ≥5**, not an absolute log evidence threshold. | Write Δln Z = ln(Z_complex/Z_simple) ≥5; define the subtraction direction for BIC, AIC and DIC differences too.

- SR-10 | medium | usability | “Rescale the likelihood … by sqrt(2N)” | The pack describes rescaling **log-likelihood** in 2021MNRAS.504.4123N. The catalogue leaves the operation and N undefined, making an uncertainty correction easy to apply backwards. | Identify this as a paper-specific heuristic requiring its full definition; recommend an explicitly defined correlated-noise likelihood rather than an unspecified rescaling.

- SR-11 | medium | attribution | “Add a component when residuals exceed 5 sigma, stop below 3 sigma” | Only 2022PASJ...74.1429T supplies that particular before/after pair. The cited 2024MNRAS.533..771R stops when no channel exceeds **5σ** and the fitting-region RMS is **<1.5 times** the remaining spectrum; other examples use >3σ or ≥3.5σ. | Give separate rules per paper and retain the additional RMS condition.

- SR-12 | medium | unsupported | “Pre-registered binning” | The pack’s 2026MNRAS.546f2284B entry states restriction to three physically motivated parameters to avoid p-hacking. It does not establish preregistration. | Rename this “Restricted, physically motivated binning”; label preregistration separately as a recommendation.

- SR-13 | medium | attribution | “Wording seen in the pack” | Several quotation-marked examples, including “evidence favors alignment, but does not uniquely establish it” for 2024AJ....167..232T, are card finding summaries rather than quoted author wording. | Label these as card paraphrases or suggested wording; reserve author quotations for the supplied verbatim excerpts.

- SR-14 | high | omission | “Non-detection … 3 sigma upper limit” | The workflow lacks an explicit gate confirming that the expected line and its full plausible velocity range were observed. The pack’s 2021A&A...654A..37D limitation says one line falls entirely outside the SPW and another is only partly covered. | Check frequency/velocity conventions and usable spectral coverage before declaring a non-detection, setting a full-line limit or refuting detectability.

- SR-15 | medium | omission | “3 sigma upper limit … no physical interpretation” | A limit needs an assumed linewidth, extraction region and noise treatment; molecular column limits additionally depend on excitation and source size. The 2023MNRAS.523.2887M card flags adopted temperature/size, blends and baseline uncertainty. Conversely, the pack’s 2017PASJ...69...20H uses a non-detection to support a physical constraint. | State limit assumptions and systematics; permit conditional physical bounds while distinguishing them from detections or unconstrained absence claims.

- SR-16 | medium | science | “keep tentative sources out of downstream figures and statistics” | 2021A&A...654A..37D excludes one source from its later figures and discussion; that does not justify universal exclusion. Selection-dependent removal can bias population estimates, consistent with the skill’s own stacking warning from 2018MNRAS.481.1976Z. | Retain flagged candidates in auditable catalogues and use appropriate censoring, reliability weighting or inclusion/exclusion sensitivity tests.

- SR-17 | medium | omission | “the trend survives the null, the resampling and the shared-variable test” | These checks do not address repeated observations of the same underlying source. The 2021ApJ...908..192S card explicitly flags multiple lensed images and clumps, requiring treatment of independence and repeated-source weighting. | Define the independent sampling unit; group repeated images/components appropriately in uncertainties and resampling.

- SR-18 | medium | attribution | “Excitation sensitivity | RADEX … 2020ApJ...905..122H” | This routing example obscures the software actually used. That excerpt explicitly says the authors used their **own non-LTE code**, tested against published results and RADEX. | Distinguish the inference implementation from its validation reference.

- SR-19 | medium | unsupported | “The two mistakes that matter most … stopping on the bright obvious component” | This opening presents an unlabelled general ranking; the faint-component lesson comes from WRITER CONTEXT lesson 7, not a literature aggregate. | Label the passage as general CosmicCoder team experience and remove the unsupported “matter most” ranking.

## Notes
The support totals are correct, and many numerical examples are faithfully reproduced.
The main repair is separating paper-specific observations, card interpretations and recommended agent policy.
No explicit held-out target leakage was found.