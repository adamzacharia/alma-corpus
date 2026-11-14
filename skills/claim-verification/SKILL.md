---
name: alma-claim-verification
description: "Decide whether a finding from ALMA data is real, how far it can be pushed, and how to word it: the validation checks ALMA papers run (inverted-image and injection tests, flux recovery, assumption sweeps, information criteria, convergence, null and resampling tests), how they rule out alternative explanations, the support levels they reach (supported, partially supported, refuted) and how they decide they have done enough. Use when a worker, verifier or editor agent must accept, downgrade, reject or extend a draft finding, write it in a claim template, or decide to stop and record a question as open. Built from 3455 ALMA papers (2012-2026)."
---

# Claim verification and stopping rules

A finding is a claim about the sky that survived specific tests. ALMA papers rarely run a generic checklist:
they pick the check that answers the failure most likely for that claim type (noise peak, filtered flux,
degenerate model, rival mechanism, selection effect). Of 11,155 claims the cards rated, 7101 were supported,
3526 partially supported and 528 refuted (pack aggregate), so roughly one claim in three in published ALMA work
is stated as partial. The two mistakes that matter most: stating a conclusion more confidently than the checks
allow, and stopping on the bright obvious component before the faint signal that carried the result was tested.

## Agent checklist

1. Write the draft finding in the claim template below before judging it. If the experiment, the uncertainty or
   the code location is missing, the claim is not ready for a support level.
2. Confirm it was executed: the code ran, the output files exist and their numbers are the ones in the claim
   (in CosmicCoder agent runs, judges approved code that was written but never run).
3. Classify it (detection, measurement, model preference, interpretation, population trend, non-detection) and
   run the matching first check from the Steps table. Default detection rule when nothing else is set: the
   threshold where an inverted image or cube shows no peaks and fewer than 1 false detection is expected over
   the searched volume (2021ApJ...907..122M, 2021ApJ...908..192S, 2026A&A...706A.236M).
4. List at least two alternative explanations, including one instrumental or imaging one, and the test that
   separates each. If no test with the data in hand separates them, the claim is at most partially supported.
5. For a model preference, require a fixed threshold decided before fitting (Delta BIC > 10 in
   2025ApJ...985..243B and 2024ApJ...965..108U; ln evidence ratio >= 5 in 2024ApJ...971...17F) plus clean
   residuals; for MCMC, N/tau > 50 (2021AJ....162..235Y, 2025ApJ...988..106H).
6. Sweep the one or two assumptions that drive the number (temperature, opacity, alpha_CO, distance, collision
   rates) and report how far the result moves (2020NatAs...4..861C, 2021A&A...645A..21G).
7. Assign the support level with the wording rules below; never upgrade a claim because the story is nicer.
8. Stop when the claim's own decision criterion is met; record the question as open when the next separating
   test needs data you do not have (2025A&A...699A...5T, 2025ApJ...992L..18S). Do not loop on speculation.
9. Write down: the claim tuple, the check that backs it, every alternative and its status, and the open items.
10. Weak line claims (general practice): before any interpretation, check the identification (rest frequency
    and velocity against the source's systemic velocity, blends with nearby transitions, spw edges, atmospheric
    lines, continuum subtraction), count the channels, positions and lines searched (look-elsewhere), and get the
    false-alarm rate from the same search run on random positions or the inverted cube. Use enough null trials to
    resolve the tail you claim (a one-sided 3.5 sigma tail is p ~ 2e-4, so thousands of trials, not tens); with
    fewer, quote the empirical p as a bound. Integrated-intensity error for independent channels:
    sigma_I = rms_channel x dv x sqrt(N_channels). Channels are correlated when Hanning-smoothed or narrower than
    the spectral resolution; then measure sigma_I directly by integrating line-free windows of the same width, or
    scale by the correlation factor. Masking or seed thresholds (e.g. 4 sigma in 3 channels) are recipes for
    building moment maps, not detection criteria. If those checks are done and the data cannot go deeper,
    stop: report "tentative (local X sigma)" or a 3 sigma upper limit, no physical interpretation, and name the
    observation that would settle it (deeper integration, a second transition, another instrument).

## When to use

- A worker posts a finding and a verifier or editor must accept, downgrade or reject it.
- A reproduction disagrees with a paper and you must decide whether your number or theirs is the robust one.
- A faint feature (tentative line, compact component, residual arc) is about to be reported or dropped.
- A model was chosen among several and the claim depends on that choice (components, profiles, geometries).
- A correlation or population difference is being turned into a physical statement.
- An open-ended run needs a rule for when the evidence is enough.

## When not to use

| Situation | Use instead |
|---|---|
| Designing the injection or null test itself (mock sources, completeness curves) | the injection-null-tests skill, then return here to judge the result |
| Building the answer key and tolerances for reproducing a paper | the paper-reproduction skill |
| Choosing which package does the fit | the analysis-software-map skill; do not reimplement a standard fitter to verify a claim |
| Checking whether archive data from several projects can be combined | the archival-data-reuse skill |
| The claim is about method behaviour (imaging, self-calibration) rather than the source | the imaging-choices or self-calibration skill |

## Claim template

Fill every field. A missing field is itself a finding for the editor.

```
CLAIM <id>
Hypothesis:   <one sentence, testable with this data>
Experiment:   <data (project/MOUS, band, array), product used, method and package, key settings>
Result:       <number with uncertainty and units; S/N; what the uncertainty includes (statistical,
               flux scale, model systematics)>
Finding:      <what the result means physically, in one sentence>
Support:      supported | partially supported | tentative | refuted | open
Backed by:    <the check(s) that make it trustworthy, with their outcome, e.g. "no peaks beyond -5.2 sigma
               in inverted cube; injected lines recovered at 95% above X">
Alternatives: <each rival explanation -> ruled out by <test> | not excluded because <reason>>
Open items:   <what would change the support level and what data it needs>
Code:         <path:function or notebook cell; output file paths>
```

This mirrors how the cards decompose papers (hypothesis, experiment, result, finding, with a support level),
e.g. 2018MNRAS.481.1976Z and 2024AJ....167..232T in the pack excerpts.

## Steps

1. **Pin the claim and its type.** Goal: know which failure to test first. Write the template. Split compound
   claims: 2017ApJ...849...25L separates "five massive starless core candidates" (partially supported) from
   "fragmentation is thermal" (supported); 2020ApJ...905...25G separates vigorous accretion (supported) from
   absent disks (partially). Closing check: each sub-claim has one result and one uncertainty.

2. **Gate on execution.** Goal: no claim from unrun code. Rerun or open the outputs; confirm the plotted or
   tabled number matches the claim. Cards repeatedly flag papers whose prose and tables disagree
   (2021A&A...645A..21G kinetic powers; 2024AJ....167..232T mass priors and rms), so verify against the
   output file, not a summary. Closing check: the number in the claim is reproduced from a file.

3. **Run the first check for the claim type.**

   | Claim type | First check | Corpus example |
   |---|---|---|
   | Detection (blind) | Inverted image or cube, threshold at no negatives or <1 expected false source | 2021ApJ...907..122M, 2023ApJ...953...75H, 2019ApJS..244...40L |
   | Detection (known position or line) | 3 sigma at the fixed position, plus consecutive channels or a second line | 2024PSJ.....5..221C, 2024AJ....168..151J |
   | Molecular detection | Several unblended transitions match one LTE model; no predicted line missing | 2025A&A...702A..35D, 2024A&A...687A...8M, 2026ApJ..1004L...6D |
   | Flux, size, mass | Single-dish or ACA recovery, curve of growth, second estimator | 2018ApJ...857...19F, 2020ApJ...903...34A, 2018MNRAS.481.1976Z |
   | Model preference | Information criterion with a fixed threshold, residual maps, convergence | 2025ApJ...985..243B, 2025ApJ...995..108J, 2024ApJ...974..145S |
   | Physical interpretation | Alternatives table with a separating test for each | 2017ApJ...848L..11K, 2019AJ....157..251T |
   | Population trend or correlation | Shared-variable mock test, partial correlation, null and resampling tests | 2021ApJ...908..192S, 2025ApJ...995..108J, 2020ApJ...903..124B |
   | Non-detection | Several search methods, then an injection showing the signal would be seen | 2020MNRAS.498.4109J, 2025A&A...702A..18D |

   Closing check: the first check passed, or the claim is downgraded now. Full list with what each check
   protects against: `references/checks-catalogue.md`.

4. **Test robustness of the number.** Goal: the result does not hinge on one choice. Sweep the driving
   assumption (2020NatAs...4..861C: collision rates x0.1-10 changed HCN production by 2%; 2021A&A...645A..21G:
   a ULIRG alpha_CO left the main results unchanged); compare against an independent estimator or another
   sampler (2024A&A...688A.130H repeated inference with another sampler and without its contamination
   correction); match resolution before comparing with other samples (2018ApJ...857...19F smoothed to 40 pc and
   showed the difference with M51 was not a resolution artefact); for low S/N sizes, run injection-recovery
   (2024A&A...690A.197M, 1500 mock sources). Closing check: the sweep range and the shift are written into the
   Result field.

5. **Rule out the alternatives.** Goal: the interpretation is the best one, not the first one. Of 300 listed
   alternative lines, 189 use reject, rule-out or disfavour language and at least 15 explicitly keep the
   alternative open (my keyword count). Arguments papers used:

   | Argument | Example |
   |---|---|
   | Kinematics | outflow rejected because most emission is below escape velocity (2015ApJ...812...27A); gradient orientation differs from the jet (2013A&A...552L..10S) |
   | Energetics, temperature, timescale | a bubble would need ~1e7 supernovae (2012ApJ...760L..25E); a wind would imply 1e5 K gas (2013A&A...555A..73K); collect-and-collapse predicts 0.52 pc spacing vs ~0.1 pc observed (2017ApJ...849...25L) |
   | Predicted lines or counterparts | alternative redshifts rejected by missing companion lines (2013ApJ...767...88W, 2014ApJ...781L..39T); lensing rejected for lack of a counterpart (2016ApJ...827...34O) |
   | Persistence | a flare origin unlikely because the peak persists over four observations (2013ApJ...762L..21M) |
   | Instrument and imaging | beam squint, gain drift and decoherence tested (2016A&A...593A..44L); band-incoherent clumps rejected as phase artefacts (2015PASJ...67...72T); sidelobes removed (2014ApJ...795....5O) |
   | Spatial filtering | resolved-out emission tested as the cause of a deficit (2015ApJ...803...70S, 2015ApJ...810L...7V) |
   | Model fit | single-component source rejected with >6 sigma residuals (2013ApJ...779...67B); eccentricity explored and ruled out (2015ApJ...806..154C) |

   When no test separates them, say so: inflow vs warp "practically degenerate" (2014ApJ...782...62R),
   rotation vs free fall "cannot separate with current data" (2015ApJ...804...37L), a retrograde disk solution
   retained (2024AJ....167..232T). Closing check: every alternative in the template has a status.

6. **For population claims, attack the statistics.** Test whether both axes share a variable
   (2021ApJ...908..192S mock-data test); control for third variables with partial correlations and aperture
   expectations (2025ApJ...995..108J); normalise and see if the trend survives (2018ApJ...853..195W: the radius
   trend vanished per unit mass); run null tests (2020ApJ...903..124B: two 10,000-realisation tests, ~1% false
   positives) and resampling (2026A&A...705A.209L: drop 30% of the sample 500 times; 2022A&A...660A..14R:
   jackknife dropping 20%); bin only on physically motivated parameters to avoid p-hacking
   (2026MNRAS.546f2284B); degrade S/N to see whether the conclusion depends on depth (2024MNRAS.528.6768H).
   Closing check: the trend survives the null, the resampling and the shared-variable test.

7. **Assign the support level and word it** (rules below). Closing check: an editor reading only the Finding
   and Support fields would not overstate the result.

8. **Decide: stop, one more test, or open.** Use the stopping rules below. Closing check: the decision and its
   reason are in Open items.

## Support levels and how to word them

| Level | Use when | Wording seen in the pack |
|---|---|---|
| Supported | Primary check passed, the main alternative was tested and rejected, number robust to the assumption sweep | "not an artifact of resolution" (2018ApJ...857...19F); "first robust interstellar detection" after ten clean lines and 70 positions (2026ApJ..1004L...6D) |
| Partially supported | Result is real but the interpretation keeps a live alternative, or rests on one assumption, small numbers or marginal resolution | "evidence favors alignment, but does not uniquely establish it" (2024AJ....167..232T); "a disc origin is plausible but outflow/merger origins cannot be excluded at this resolution" (2015MNRAS.452...88K); "consistent with inflow but degenerate with a warp" (2014ApJ...782...62R) |
| Tentative | Detection or trend near threshold, one line, one epoch, or a p-value short of 3 sigma | "tentative outflow, to be confirmed with higher resolution" (2013A&A...558A.124C); "lower on average but not significant at 3 sigma" (2014ApJ...787...42C); "hint of phased flare, not significant" with p ~7% (2015ApJ...815...64W) |
| Refuted | The test was run and the hypothesis failed | flattening of counts disfavoured by the fitted slope (2024ApJS..275...36F); gas exhaustion "not the reason" (2024MNRAS.528.6768H); 12CO not optically thin (2020ApJ...905..122H) |
| Open | No available test separates the options | gap vs ring left open when the AIC difference is small (2024A&A...689L...5M); evidence "insufficient to confirm" shock-triggered star formation (2025A&A...693A.199C) |

In the 250 listed partially supported or refuted claims, the hedges are "possibly/may/could" (60),
"consistent with" (25), "likely" (23), "tentative" (14), "cannot be excluded/distinguished" (13),
"suggest" (10) and "plausible" (8) (my count). Rules: say which alternative survives and why ("cannot
exclude X because Y"); give the significance and number of independent elements; keep tentative sources out
of downstream figures and statistics as 2021A&A...654A..37D did; "consistent with" means the test did not
reject, not that it confirmed.

## Parameter defaults and ranges

| Decision | Common choice | Range seen | Examples |
|---|---|---|---|
| Blind continuum or line detection | S/N where inverted maps give no peaks and <1 false source | 4.0-6.2 peak S/N; purity 0.7-0.99 | 2021ApJ...908..192S (4), 2025A&A...699A.324H (4.2), 2023ApJ...953...75H (5.2), 2019ApJS..244...40L (5.40), 2021ApJ...907..122M (6.2), 2024MNRAS.528.5019H (purity 0.7 at S/N 3.6), 2024ApJS..275...36F (purity > 0.99) |
| Prior-position detection | 3 sigma | 3-4.35 | 2024PSJ.....5..221C, 2023ApJ...956..135W, 2019ApJS..244...40L |
| Non-detection | 3 sigma upper limit after several search methods | 3 sigma | 2021A&A...646A..26B, 2023MNRAS.523.2887M |
| Robust vs tentative line | robust at SNR >= 20 in one sample; 5 sigma for redshifts | 5-20 | 2021A&A...654A..37D, 2022MNRAS.511.3017U |
| Molecular detection | several unblended transitions >= 3 sigma | 5-35 lines | 2025A&A...702A..35D (>=5), 2026ApJ..1004L...6D (10), 2024MNRAS.533.1143M (35 above 5 sigma) |
| Resolved size or shape | peak S/N 8-10 | 4.5-10 | 2021A&A...654A..90L, 2015ApJ...799...81S, 2024A&A...686A.187P (4.5), 2024MNRAS.533.3098A (8) |
| Resolution for kinematics | >= 3-4 beams across the structure | 2-5 beams | 2020ApJ...904...77G (~3), 2025A&A...699A..80H (~4 per effective radius), 2025A&A...699A...5T (~5), 2026ApJ..1005...94N (zeta >= 2 for M_BH) |
| Model selection | Delta BIC > 10 | Delta AIC >~ 10; ln evidence >= 5; DIC > 10 | 2025ApJ...985..243B, 2024A&A...689L...5M, 2024ApJ...971...17F, 2021PSJ.....2..105T |
| Add a component | residual > 5 sigma | 3-5 sigma | 2022PASJ...74.1429T, 2021A&A...645A..21G, 2021MNRAS.503.1174K (3.5) |
| MCMC length | N/tau > 50 | 50-100 tau; R-hat < 1.01, ESS > 300 | 2021AJ....162..235Y, 2023ApJ...950...75I (100), 2024ApJ...974..145S |
| Monte Carlo or noise realisations | 100-1000 | 50-10,000 | 2021MNRAS.500.3667S (100), 2024ApJ...976..201F (1000), 2025A&A...695A.204V (50), 2020ApJ...903..124B (10,000) |
| Model-data agreement to stop iterating | within 10% | 5-10%; within 3 sigma; factor 2-3 for chemistry | 2023A&A...677A..76P, 2024ApJ...973..135H, 2021A&A...656A.150P, 2024A&A...687A.299L |
| Correlation significance | p < 0.05 with the coefficient quoted | p < 0.05 to 3 sigma | 2025ApJ...995..108J, 2014ApJ...787...42C |
| Statistics per bin | stated minimum | >= 40 independent measurements; >= 50 peaks; constraints > free parameters | 2024ApJ...974..257Z, 2020MNRAS.493.2872C, 2026A&A...712A.201J |

### Stopping rules

- Stop when the claim's own criterion is met and stated: self-calibration stops when peak S/N gains less than
  5% (2018ApJ...869L..41A, 2025MNRAS.538.2358S); fits stop when parameters are stable (2020ApJ...904...78S,
  150-200 steps); iterative models stop at 10% agreement (2023A&A...677A..76P).
- Stop extending a model when the aim does not need it, and say so: 2024ApJ...970..114T aimed only at an
  axisymmetric match; 2020ApJ...904...77G judged further sophistication unnecessary at ~3 beams;
  2024ApJ...969...56M stopped when the best fit was no better than zero signal.
- Get more data when the test needs range or epochs you lack: 2021MNRAS.502..521D added archival outbursts
  because one outburst spanned less than the 2 dex needed for a slope.
- Record open when the separating observation is not in hand: more epochs for time-dependent modelling
  (2025ApJ...992L..18S), kinematics for stronger physical conclusions (2025A&A...693L..17S), higher S/N for
  outflows (2020MNRAS.496..598C), no temperature claim beyond 120 au (2021ApJ...906..111T).
- In CosmicCoder agent runs, open-ended loops that re-verified claims the data could not settle cost most of
  the budget; apply one more test only if its outcome would change the support level.

## Software

The workflow pack has no software aggregate; counts below are my keyword counts over the pack. For job-by-job
routing use the analysis-software-map skill.

| Job | Packages named in the pack | Count / examples |
|---|---|---|
| Posterior sampling and convergence | MCMC (35 mentions), emcee (3), dynesty (1), MultiNest (1) | 2021Sci...371..713L, 2023MNRAS.520.1613M (dlogz 0.8), 2020Natur.584..201R (evidences flatten with prior volume) |
| Independent flux and size estimates | CASA uvmodelfit (visibilities) and imfit (images) (2 each), GILDAS (5) | 2018MNRAS.481.1976Z, 2014A&A...562A..67G |
| Source finding and purity | PyBDSF (1), GALFIT (2) | 2022MNRAS.515.3126I, 2021MNRAS.503.1174K |
| Cloud decomposition robustness | CPROPS / PYCPROPS (3) | 2018ApJ...857...19F (SIGDISCONT 0-999 tested), 2023ApJ...953..164M (10,000 bootstraps) |
| Kinematic model checks | KinMS (5), 3DBarolo (2), eddy, DISCMINER | 2025ApJ...995..108J, 2021A&A...645A..21G, 2022A&A...662A.121R, 2025ApJ...984L..13H |
| Excitation sensitivity | RADEX (26) | 2014A&A...570A..28V (three escape-probability geometries), 2020ApJ...905..122H |
| Nonparametric cross-checks | frank (6), rave | 2026A&A...705A.197Z, 2026A&A...705A.196H |
| Line identification | MADEX, CDMS, JPL, CASSIS | 2014A&A...569L...5M, 2024A&A...682A.127S |

## Pitfalls

- **A posteriori detections.** Signals called real after looking (2.3 sigma in 2018MNRAS.481.1976Z, card);
  choosing the extraction position with the most clean lines (2026ApJ..1004L...6D, card). Fix the rule first.
- **Correlations built into the axes.** Both axes containing the fitted radius (2021ApJ...908..192S, card);
  apertures that scale with the quantity being correlated (2025ApJ...995..108J, card).
- **Circular tuning.** Abundance factors tuned to match another tracer and then used as agreement
  (2017ApJ...849...25L, card).
- **Absence of evidence.** Missing rotation under high continuum opacity does not show disks are absent
  (2020ApJ...905...25G, card); a failed disk fit does not show the gas is non-rotating (2025ApJ...995..108J).
- **Formal errors as total errors.** MCMC errors do not cover flux calibration, binning or the profile family
  (2021ApJ...909..212K, card); visual convergence checks need sensitivity tests (2026A&A...705A.197Z, card).
- **Non-independent checks.** Two measurements from one session are not independent calibration checks
  (2020NatAs...4..861C, card); spectral indices mixing beams and epochs of a variable star
  (2017ApJ...841..130A, card).
- **Selection in stacks and samples.** Excluding non-detections from a stack can bias the mean
  (2018MNRAS.481.1976Z, card). Referee caveats most often cite a single object or galaxy (5 + 5) and
  qualitative model comparison (3) (pack aggregate).
- **The usual limitations.** In the 200 listed author limitations: resolution or beam (51), small sample or
  single source (24), missing flux or filtering (21), limits only (20), degeneracy (12), temperature (11),
  optical depth (10), S/N (10) (my count). Check each before upgrading a claim.
- **Recoverable scale.** A size larger than the maximum recoverable scale carries a large, model-dependent
  uncertainty (2021ApJ...908..192S flags its one such source); a missing-flux estimate that assumes smooth emission fails for compact filtered
  structure (2025ApJ...995..108J, card).
- **Team lessons (CosmicCoder runs).** Overconfident conclusions; stopping after the bright component and
  missing a faint compact signal; "novel" questions already answered with other datasets. A verifier asking
  "what is the most important question?" improved results.

## Verification checks

Before an agent reports a claim:

- The template is complete, including uncertainty, the backing check and a code path whose outputs exist.
- Detections quote the threshold rule and its false-detection basis (inverted map, mock sources or trial
  count), not just "5 sigma".
- Fluxes and masses state what fraction of single-dish or compact-array flux was recovered, or say it is
  unknown.
- Model preferences quote the criterion value and the residual check; posteriors quote the convergence
  statistic.
- Every alternative has a status; partial claims name the surviving alternative.
- Population claims list the null, resampling and shared-variable tests and their outcome.
- Open items are recorded with the data that would settle them.

What a referee or evaluator will check: whether each experiment is correct and traceable to code, whether the
conclusion follows at the stated support level, whether the error budget includes the flux scale and the
driving assumption, and whether internal numbers agree between tables and text (a common card caveat, e.g.
2021A&A...654A..37D velocity offsets, 2024AJ....167..232T rms values).

## Source cards

All member papers are in `references/sources.md`; the check table is in `references/checks-catalogue.md`.
Most informative for this workflow:

- Detection reliability: 2019ApJS..244...40L, 2021ApJ...907..122M, 2023ApJ...953...75H, 2021NatAs...5..319P,
  2022MNRAS.515.3126I, 2026ApJ...999...47L, 2024ApJS..275...36F
- Molecular detection and line identification: 2025A&A...702A..35D, 2026ApJ..1004L...6D, 2024A&A...687A...8M,
  2023MNRAS.523.2887M
- Measurement robustness: 2018MNRAS.481.1976Z, 2018ApJ...857...19F, 2020NatAs...4..861C, 2024A&A...690A.197M,
  2021A&A...645A..21G
- Model selection and convergence: 2025ApJ...985..243B, 2024ApJ...971...17F, 2024ApJ...974..145S,
  2026A&A...705A.197Z, 2021MNRAS.504.4123N
- Alternatives and interpretation: 2017ApJ...848L..11K, 2017ApJ...849...25L, 2015ApJ...812...27A,
  2016A&A...593A..44L, 2024AJ....167..232T
- Population statistics: 2021ApJ...908..192S, 2025ApJ...995..108J, 2020ApJ...903..124B, 2026A&A...705A.209L,
  2024MNRAS.528.6768H
