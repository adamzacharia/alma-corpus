# Review task: an ALMA agent skill against its evidence pack

You are reviewing a skill file (SKILL.md, plus an optional parameters table) that another model wrote from the
EVIDENCE PACK below. The pack is built from methods cards of published ALMA papers; every quote in it was
mechanically verified against the paper text. The skill will be given to research agents that analyse ALMA data,
so wrong defaults or misattributed practice cause real errors. You have no file access: everything you need is in
this message.

Check, in this order:

1. **Attribution.** Every number, range, default, software attribution and "papers do X" claim that cites
   bibcodes: does the pack support it for those bibcodes? Flag claims the pack contradicts, claims cited to a paper
   whose pack entry says something else, and counts that do not match the pack aggregates.
2. **Unsupported practice.** Statements presented as literature practice with no support in the pack. (General
   background marked as general practice is fine if it is correct.)
3. **Scientific correctness.** Wrong formulas, wrong units, wrong CASA task/parameter names or semantics, unsafe
   advice, or a recommendation that contradicts the evidence.
4. **Omissions.** Important pitfalls, assumptions or validation checks that are clearly present in the pack (for
   example in "Limitations the authors admit" or "Settings cards flag as needed but not stated") but missing from
   the skill.
5. **Usability.** Anything an agent would misread or could not act on.
6. **Contamination and team lessons.** If a WRITER CONTEXT section is present: flag any mention of, or hint at,
   the held-out evaluation targets it names (objects, papers, or their numbers). Team lessons may appear only as
   labelled team experience in general form; flag any that is presented as literature practice or carries
   numbers not in the context.

Some skills are *workflow* skills (paper reproduction, claim verification, archival reuse, software map). Their
packs aggregate card fields such as inherited conventions, missing-for-reproduction items, validation checks and
software used. Lines marked "(card)" in the pack are the card author's inference; the skill should say so when it
leans on one. Review them with the same rules.

Output format (Markdown, nothing else):

```
# Codex review: <slug>
VERDICT: CLEAN | FIX
## Findings
- SR-01 | high|medium|low | <attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- SR-02 | ...
## Notes
<at most 5 lines: overall quality, anything the writer should know>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (injection-null-tests) ===
---
name: alma-injection-null-tests
description: "Decide whether an ALMA detection, flux, size, offset, correlation or completeness limit is real by putting synthetic sources or models through the same pipeline (image- or uv-plane injection, mock observations with simobserve/simalma/KinMS), by building empirical null distributions (inverted maps, sign-flip jackknifes of visibilities, simulated noise maps, random positions or velocities, shuffled data) and by Monte Carlo noise realisations. Use when quoting completeness, flux boosting or size bias, testing whether a faint peak, a centroid offset, a variability amplitude or a correlation exceeds what noise alone gives, setting a detection threshold, or reviewing someone else's claim of any of these. Built from 208 ALMA papers (2013-2026)."
---

# Injection-recovery, null and jackknife tests

Measures how often a pipeline finds, mismeasures or invents a signal, by feeding it data where the truth is
known: synthetic sources injected into the real noise, or data with the signal destroyed (inverted map,
sign-flipped visibilities, shuffled pairs, random positions). The two mistakes that matter most: (1) running
the injected or null data through a different (easier) pipeline than the real data, for example point-source
injections when the sources are resolved, which overestimates completeness (2019MNRAS.483.1624B,
2020ApJS..251...14H); (2) calling a peak, offset or delay significant from a Gaussian sigma when the real noise
is not Gaussian or many places were searched (2022A&A...666A..39M, 2025A&A...695A.204V).

> Always report: what was injected (profile, size, flux and width distributions), where (map, mask, exclusions,
> separations), how many per image and in total, the recovery rule (match radius, S/N cut), the null method and
> number of realisations, the random seeds, and the resulting curve with its error. The cards flag as unstated
> the method that made a set of simulated noise maps, the seeds of a jackknife and whether bright sources were
> removed before jackknifing (one card entry each, pack aggregates).

## Agent checklist

1. First find out whether the paper (or an earlier paper in its series) already gives completeness, boosting
   or fidelity curves. Corrections are often inherited ("see Paper IV" in 2023A&A...675A..85M). In CosmicCoder
   agent runs, a reproduction failed partly because such inherited corrections were not restated.
2. Inject into the real map or visibilities, on the residual or background after removing detected sources
   (2024A&A...690A..33L, 2020MNRAS.495.3409S). Keep injections at least about one beam from real sources and
   from each other: 1 arcsec exclusion around >4 sigma pixels (2021MNRAS.503.1174K), >=1 arcsec separation
   (2024A&A...692A..22Z), >2.5 arcsec separation and 5 arcsec from map edges (2024A&A...690A..33L).
3. Run the exact same imaging, finder, thresholds and flux method on injected and null data as on the real data
   (2025A&A...695A.204V re-images every jackknife; 2023PASJ...75..311K re-ran filtering and detection).
4. Default sizes: draw them from the measured size distribution, or use the median of the high-S/N sources and
   test point and large extremes (2023A&A...675A..85M). Never only point sources for resolved targets.
5. Default numbers (a recommended floor taken from the values below, not a rule any paper validated): >=100
   injections per flux bin and >=1000 Monte Carlo noise realisations. Papers use 100
   iterations x 20 sources per flux step (2024A&A...684A.119P), 10,000 per bin (2021ApJ...909..165Z), 1000
   realisations for errors (2016ApJ...832..187B, 2023A&A...675A..85M). Inject only ~5-20 per image per run
   (2022MNRAS.515.3126I, 2024A&A...684A.119P, 2025A&A...695A.163B) so injections do not blend.
6. Recovery rule default: matched within about one beam and above the real detection threshold, e.g. >4 sigma
   within 1.0 arcsec (2018PASJ...70...65U); match radii of 0.6-1.5 arcsec in the pack (2018ApJ...860..161S,
   2021ApJ...909..165Z).
7. Decision rule for any "is it real" question: build the null distribution empirically (inverted map,
   jackknife, random positions, shuffles) and quote the fraction of null trials at least as extreme as the data.
   Papers count it as significant at p < 0.05 with p = (b+1)/(n+1) (2026MNRAS.552g1573L) or when zero lies
   outside the 95% interval (2024ApJ...971...52M). For blind detections require a fidelity or likelihood-ratio
   criterion, not a sigma alone (2016ApJ...833...71A, 2025A&A...695A.204V).
8. Before stating the result, check that the null reproduces the real noise (negative-peak counts match the
   simulated noise maps in 2023A&A...675A..85M; jackknife noise matches cleaned noise maps in
   2025A&A...695A.204V), and that injected fluxes and sizes come back unbiased or are corrected.
9. Write down: completeness C(S, size), boosting ratio vs S/N, fidelity vs S/N, the null p-value with the number
   of trials, seeds, and the script path. Save tables to files; do not print them.

## When to use

- Completeness and flux boosting for a blind continuum or line catalog, or for a core or cloud census
  (2016ApJ...833...68A, 2024ApJS..275...36F, 2026ApJ...997..155M, 2017MNRAS.468.1769F). Catalog-level details
  (counts, effective area) are in `source-extraction-counts`; core CMF completeness in `core-extraction-cmf`.
- Bias and scatter of a measured size, flux or shape at low S/N (2017ApJ...846..108C, 2015ApJ...799...81S).
- Whether a faint peak or line is real (2025A&A...695A.204V, 2023MNRAS.519...34H, 2025PASJ...77.1163H).
- Whether a centroid offset between tracers or instruments exceeds the noise (2023PASJ...75..311K).
- Whether a correlation, clustering signal or time delay beats chance (2020ApJ...903..124B, 2026MNRAS.552g1573L,
  2026A&A...707A.221S, 2024ApJ...971...52M).
- Whether variability or a transient is above the systematics of time-sliced imaging (2023MNRAS.522...56V,
  2022A&A...666A..39M).
- Throughput loss and contrast limits after PSF subtraction or non-linear imaging (2021AJ....161..146J,
  2020A&A...633A.115K, 2024PASJ...76..437Y, 2021ApJ...923..121Y).
- Comparing a simulation with data: make mock observations, not raw model images (2020MNRAS.491.2506D,
  2022A&A...666A..39M, 2020MNRAS.494.5542R).

## When not to use

| Situation | Use instead |
|---|---|
| High-S/N source with Gaussian thermal noise and one pre-specified position | Analytic S/N and fit errors; injection adds little. Still check fit errors against a quick Monte Carlo (2017ApJ...846..108C found them consistent) |
| Error budget dominated by calibration or model inputs (flux scale, opacity, emissivity) | Propagate those inputs by Monte Carlo over the assumptions (2022A&A...659L...1L: errors dominated by model inputs; 2019A&A...623A.111H perturbs gain terms) rather than injecting sources |
| Number counts, effective area, DPL fits | `source-extraction-counts` (this skill gives only the injection and null machinery) |
| Core catalogs and CMF slopes | `core-extraction-cmf` |
| Stacked non-detections | `stacking` (2021A&A...649A.152K injects into stacks with position offsets) |
| Source size from visibilities | `uv-plane-fitting`; use injections here only to measure its bias |

## Steps

1. **Define the question and the statistic.** Goal: one number the test will produce (recovered fraction,
   flux ratio, offset, peak count, correlation coefficient, likelihood ratio). Write the decision threshold
   before running (p < 0.05 in 2026MNRAS.552g1573L; likelihood ratio k = 3 in 2025A&A...695A.204V; a variability
   factor threshold of 2 in 2023MNRAS.522...56V).
2. **Choose the test family.**

   | Question | Test | Examples |
   |---|---|---|
   | How many real sources do I miss, how biased are fluxes/sizes? | Inject-and-recover | 2024ApJS..275...36F, 2020MNRAS.495.3409S, 2017ApJ...846..108C |
   | How many detections are noise? | Inverted map, simulated noise maps, jackknife | 2016ApJ...833...69D, 2023A&A...675A..85M, 2025A&A...695A.204V |
   | Is a peak at a prior position real? | Same search at many random positions | 2024ApJ...962..128M (5000 random positions, 4 arcsec search) |
   | Is a correlation or clustering real? | Shuffle / permutation / random draws | 2020ApJ...903..124B, 2026MNRAS.552g1573L, 2026A&A...707A.221S |
   | Is an offset real? | Inject a model at the observed S/N, measure offsets | 2023PASJ...75..311K |
   | Is a feature an artefact of the data or method? | Split data (time, epoch, half sample), rerun | 2015ApJ...799...81S, 2021AJ....161..146J, 2024A&A...687A.293Q |
   | What does a model look like through ALMA? | Mock observation | 2023MNRAS.522...56V, 2022A&A...666A..39M, 2020MNRAS.491.2506D |

3. **Build the injection set.**
   - Profile: 2D Gaussians are the norm for continuum (2024A&A...690A..33L, 2026ApJ...997..155M); Sersic n = 1
     (2025A&A...704A.158C); beam-shaped for unresolved limits (2024ApJ...967...56C, 2018ApJ...853..160C).
     Lines: Gaussian spectral profiles (2024A&A...684A.119P, 2021ApJ...907..122M).
   - Sizes: uniform 0-0.9 arcsec FWHM (2019MNRAS.487.4648S), half-light 0.05-0.30 arcsec with axial ratio 0-1
     (2020MNRAS.495.3409S), 0.04-3.0 arcsec (2017ApJ...850...83F), FWHM 0.1-0.9 arcsec (2023MNRAS.522...56V).
   - Fluxes: a grid in S/N (peak S/N 2.0-7.0 in 0.5 steps with FWHM 36-396 km/s, 2025PASJ...77.1163H), a range
     in units of the noise (2.5-80 sigma, 2024ApJS..275...36F), a power law of index -2 (2019MNRAS.487.4648S), or
     drawn from a counts model (2020MNRAS.495.3409S; SIDES in 2023A&A...675A..85M). A realistic input
     distribution is needed when you want boosting from Eddington bias, not only from noise.
   - Line widths: 100-1600 km/s (2025A&A...695A.163B), 10-500 km/s (2023MNRAS.519...34H), 50-500 km/s
     (2016ApJ...833...67W).
4. **Place the injections.** Random positions in the searched area (PB response > 0.5 in 2024A&A...692A..22Z,
   > 40% in 2026ApJ...997..155M), on the source-subtracted background (2024A&A...690A..33L) or residual map
   (2020MNRAS.495.3409S), excluding real sources (2021MNRAS.503.1174K). For spectra, inject model profiles into
   spectra from random cube regions (2017ApJ...846..108C). For a super-resolution or PSF-subtracted image, put a
   test point source in an emission-free area (5% of target flux, 2024PASJ...76..437Y) or a grid of fake planets
   at several radii and position angles (every 10 pixels at 3 PAs, 2021AJ....161..146J; 60 deg steps,
   2020A&A...633A.115K).
5. **Inject in the right plane.** Image-plane injection is the common default (2023A&A...675A..85M). For
   visibility-based finders or fitters inject in the uv plane: CASA `cl.addcomponent`, `ft`, then `uvsub` with
   `reverse=True` (2025PASJ...77.1163H, which found results identical to `simobserve`). For whole mock
   observations use `simobserve`/`simanalyze` (2020ApJS..251...14H, 2023MNRAS.522...56V), `simalma` with real
   antenna gains (2022A&A...666A..39M) or KinMS for kinematic models (2020MNRAS.491.2506D).
6. **Recover with the identical pipeline.** Same finder and parameters (getsf in 2024A&A...690A..33L,
   astrodendro in 2026ApJ...997..155M, clumpfind in 2025PASJ...77.1163H), same flux method (uv fit in
   2020MNRAS.495.3409S), same match rule. For PSF subtraction, inject before subtraction and reprocess with each
   algorithm (2021AJ....161..146J).
7. **Build the null.** Pick the one that preserves the noise structure:
   - Inverted map: fidelity = (Npos - Nneg)/Npos (2016ApJ...833...69D); negative peaks as the false-positive
     proxy assume symmetric noise (2024MNRAS.528.5019H).
   - Simulated noise maps: 300 per field (2023A&A...675A..85M), compared with the negative-map counts.
   - Jackknife of visibilities: flip the sign of a random half of the visibilities and re-image, 50
     realisations (enough to recover the high-S/N tail), after removing sources above S/N ~50; not validated for
     bright extended emission or with the w-term (2025A&A...695A.204V, tool `jackknify`).
   - Blank mock cubes: Q = N_mock/N_real per (peak S/N, width) (2025PASJ...77.1163H).
   - Random positions or draws: 5000 random positions (2024ApJ...962..128M); 1000 random draws for a
     separation statistic (2026A&A...707A.221S).
   - Shuffles: keep x fixed, shuffle y, or draw unrelated y with the measured scatter, 10,000 times each
     (2020ApJ...903..124B); permutation after 10,000 Gaussian error realisations (2026MNRAS.552g1573L).
8. **Run Monte Carlo realisations for uncertainties.** Perturb the data by their errors and refit: 1000
   (2016ApJ...832..187B), 2500 per pixel with a 3 sigma detection rule (2018ApJ...863..193V), 10,000
   (2024MNRAS.533..771R), 300 with percentiles 15.9/84.1 (2021ApJ...908...19B); noise drawn from the measured 1D
   noise spectrum (2024MNRAS.52710221P). Use percentiles, not a symmetric sigma, when the distribution is skewed.
9. **Turn results into corrections.** Fit completeness with a logistic (2 entries in the fitting aggregate;
   2017MNRAS.468.1769F) or error function (2025PASJ...77.1163H, 2016ApJ...833...68A). Boosting from the running
   median of recovered/input flux vs S/N (2020MNRAS.495.3409S; divide imfit flux by the median ratio at peak
   S/N < 20 in 2025A&A...699A.324H). Apply completeness only where it is not tiny (flux correction where C > 0.5
   in 2026ApJ...997..155M; floor 10% in 2024ApJS..275...36F; drop C < 0.2 in 2020ApJ...902..110D).
10. **Decide and record.** State the statistic, its null distribution, the p-value or fidelity, and the
    corrections, with the test that backs each claim.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count, my count of pack lines) | Examples |
|---|---|---|---|---|
| Injections per image per run | 5-20 | 1-50 | 6 | 2022MNRAS.515.3126I (5), 2024A&A...684A.119P (20 continuum, 50 lines), 2025A&A...695A.163B (20), 2024ApJ...967...56C (10) |
| Total injections | 10^4-10^5 | 100 to 1,016,400 | 11 | 2016ApJ...833...68A (100), 2024A&A...690A..33L (~3800 per field), 2015ApJ...799...81S (20,000), 2017ApJ...846..108C (36,000), 2025PASJ...77.1163H (1,016,400) |
| Match radius | ~1 beam | 0.6-1.5 arcsec | 9 | 2018ApJ...860..161S (0.6), 2025A&A...699A.324H (0.7, S/N>4.2), 2024ApJS..275...36F (1.0), 2021ApJ...909..165Z (1.5, one beam) |
| Completeness level quoted | 90% | 50-90% | 4 | 2026ApJ...997..155M, 2024A&A...691A.248L (90%); 2017MNRAS.468.1769F (50%) |
| MC realisations for errors | 1000 (9 papers) | 50-100,000 | about 24 | 2016ApJ...832..187B, 2021A&A...654A..37D (1000); 2019A&A...623A.111H (100); 2026ApJ..1000..141K (100,000) |
| Jackknife realisations | 50 (visibility sign flip) | 50-500 | 2 | 2025A&A...695A.204V (50); 2022A&A...660A..14R (500, dropping 20% of spectra) |
| Null shuffles / permutations | 10,000 | 1000-10,000 | 3 | 2020ApJ...903..124B, 2026MNRAS.552g1573L, 2026A&A...707A.221S (1000) |
| Simulated noise maps | 300 per field | - | 1 | 2023A&A...675A..85M |
| Significance rule | p < 0.05 or outside 95% interval | 2 sigma Poisson to 7 sigma | 5 | 2026MNRAS.552g1573L, 2024ApJ...971...52M, 2025A&A...695A.204V, 2018ApJ...863..193V (3 sigma), 2022A&A...666A..39M (7 sigma) |
| Blind fidelity threshold | 50-70% | S/N 3.3-5.5 | 5 | 2020ApJ...897...91G (50% at S/N 4.3), 2016ApJ...833...71A (5.3 at 70%), 2024MNRAS.528.5019H (0.7 at 3.6), 2018MNRAS.479.3879W (5.5 blind) |
| Prior-position threshold | lower than blind | S/N 4.5-5.0 | 2 | 2016ApJ...833...71A (4.5 within 1 arcsec, 40% fidelity), 2018MNRAS.479.3879W (5.0, 15% contamination) |
| Boosting at low S/N | measured, not assumed | 1.09 at S/N 3.5 to 1.33 at S/N 3 | 4 | 2015A&A...584A..78C, 2022MNRAS.515.3126I (applied to upper limits), 2024ApJS..275...36F (10% below S/N 8) |

## Software

From the pack aggregate "Software named in the matched steps":

| Job | Package (count) | Setting that matters |
|---|---|---|
| Imaging, injection, mock observations | casa (24), tclean (5), simobserve (5 + 2 as "casa simobserve") | identical tclean settings for real and injected data; `cl.addcomponent` + `ft` + `uvsub(reverse=True)` for uv injection (2025PASJ...77.1163H) |
| Peak finding | sextractor (9), lineseeker (4), findclump (3 + 2 as findclumps), clumpfind (2), pybdsf (2), photutils (4) | same thresholds on real, inverted and injected data; FindClump in interferopy for jackknife peaks (2025A&A...695A.204V) |
| Flux and size recovery | imfit (6), uvmultifit (4), galfit (3), uvmcmcfit (1) | same fitter on injected sources; galfit recovery tested on 4000 models in 2015ApJ...799...81S |
| Structure finding | getsf (4), astrodendro (3) | same parameters as the science extraction |
| Visibility jackknife | jackknify (2) | remove bright sources first, re-image each realisation |
| Kinematic mocks | kinms (2) | beam and pixel matched to the data |
| Statistics | scipy (4), numpy (2), powerlaw (2), lmfit (2) | store seeds |

Reimplementing a finder or fitter for the injected data is the wrong default: the test is only valid if it
runs the same code as the measurement.

## Pitfalls

- **Easy injections.** Point or beam-sized sources overestimate completeness (2019MNRAS.483.1624B,
  2020ApJS..251...14H). Papers disagree on which is conservative: 2024A&A...692A..22Z calls point-like sources
  conservative. Run both point and realistic sizes and report the difference.
- **Fluxes tied to an assumed size.** At low S/N the measured flux depends on the model size
  (2018MNRAS.481.1976Z); test extremes (2023A&A...675A..85M tested point and 0.5 arcsec).
- **Size recovery needs S/N.** 68% of sizes were within 30% only at S/N >= 10 (2015ApJ...799...81S); a 3%
  upward bias and 20% scatter in 2017ApJ...846..108C.
- **Non-Gaussian noise.** Dynamic-range-limited residuals break Gaussian false-positive estimates
  (2022A&A...666A..39M); a 7 sigma threshold over ~10^4 beams there gives ~10^-8 only under Gaussianity. Prefer
  empirical nulls.
- **Searching many places.** In broad line scans about 3 +/- 2 spurious features at S/N 4-5 are expected, and
  a reported 5.8 sigma line came back at 2.9 sigma in the jackknife analysis (2025A&A...695A.204V).
- **Offsets that noise makes.** At S/N 5.2, 22% of injected clusters were recovered more than 30 arcsec away
  (2023PASJ...75..311K). Compare an offset with injected offsets at the same S/N before interpreting it.
- **Time-sliced imaging systematics.** A changing synthesized beam made constant sources vary by up to VF ~1.6;
  the paper adopted VF = 2 as the threshold (2023MNRAS.522...56V).
- **Mock data are not real data.** "Simulated mock data do not necessarily reproduce real observation
  properties" (2025PASJ...77.1163H); no ALMA simulator was applied in 2024A&A...691A..57M (an admitted
  limitation). Inject into real noise when you can.
- **Clustered or blended input.** Line-of-sight corrections that assume no clustering (2020MNRAS.495.3409S)
  and cloud blending near galaxy centres (2017MNRAS.468.1769F) bias recovery.
- **Inconclusive splits.** A second-epoch non-recovery with an injected source of the first-epoch flux was
  inconclusive because of inner artefacts (2021AJ....161..146J); say so rather than claim a refutation.
- **Untested delays.** A cross-correlation delay whose significance "was not independently tested"
  (2021ApJ...917...73W) should be reported as tentative.

## Verification checks

- The null reproduces the noise: simulated-map spurious counts consistent within 1 sigma with negative-map
  counts (2023A&A...675A..85M); jackknife negative-peak scatter consistent with Poisson (2025A&A...695A.204V).
- Injected sources are recovered in a mock with known truth (simulated S/N 4.9 sources recovered,
  2025A&A...695A.204V; synthetic transient recovered at peak S/N ~15, 2022A&A...666A..39M).
- Two injection routes agree (`simobserve` vs `cl.addcomponent`, 2025PASJ...77.1163H); image-plane and uv
  results agree (2017ApJ...846..108C); Sersic and aperture fluxes agree to +/-1.5% (2020MNRAS.495.3409S).
- Boosting from injection matches an Eddington-bias simulation (2023A&A...675A..85M).
- Monte Carlo errors are realistic against an independent check (Stokes V amplitude, 2019A&A...623A.111H; fit
  vs MC errors, 2017ApJ...846..108C).
- The correction choice is justified by injection (Gaussian correction chosen because it recovered injected
  cloud properties, 2017MNRAS.468.1769F).
- A referee will also ask: same pipeline? realistic sizes? enough trials per bin for the binomial error on the
  completeness (general practice: sqrt(C(1-C)/N), 3% for C = 0.9 and N = 100)? seeds and scripts saved? result
  stable across a jackknife by object (2024A&A...687A.293Q)?

## Source cards

Full list: `references/sources.md`. Most informative here:

- 2025A&A...695A.204V: visibility sign-flip jackknife, likelihood ratio, 50 realisations, limits of the method
- 2023A&A...675A..85M: image-plane injection, 300 noise maps, size extremes, Eddington check, MC counts
- 2020MNRAS.495.3409S: uv-plane injection into residual maps, boosting running median, end-to-end sims
- 2025PASJ...77.1163H: uv injection in CASA, 1,016,400 line injections, blank-mock purity Q and completeness C
- 2017ApJ...846..108C: 36,000 injected models for size bias, MC spectra in random cube regions
- 2015ApJ...799...81S: 20,000 injections for size recovery vs S/N, split-in-time imaging
- 2024A&A...690A..33L: Gaussian injections onto background maps with separation and edge rules, 90% limit
- 2026ApJ...997..155M: 5000 injection trials, PB > 40%, flux correction where C > 0.5
- 2024ApJS..275...36F: 1000 injections per field, 1 arcsec match, 10% flux correction below S/N 8
- 2016ApJ...833...68A: fidelity and completeness error-function fits
- 2016ApJ...833...69D: fidelity from positive and negative counts
- 2023PASJ...75..311K: injection test of a centroid offset
- 2024ApJ...962..128M: false-positive test at 5000 random positions
- 2020ApJ...903..124B: two shuffle null tests with 10,000 realisations
- 2026MNRAS.552g1573L: permutation null with p = (b+1)/(n+1)
- 2024ApJ...971...52M: Monte Carlo resampling for a time-delay significance
- 2023MNRAS.522...56V: simobserve of constant sources for variability systematics
- 2022A&A...666A..39M: simalma mock with injected transient, non-Gaussian noise caveat
- 2021AJ....161..146J: fake-planet throughput, split sequences, second-epoch injection
- 2019MNRAS.483.1624B: beam-sized injections overestimate completeness

=== WRITER CONTEXT (readers, team lessons, contamination rule; not a literature source) ===
# Who reads these skills, and what went wrong in their runs (CosmicCoder meeting notes, Oct-Nov 2026)

Distilled from the CosmicCoder agent meeting notes (all pages) for skill writers. This file is for YOU, the writer.
Do not quote it as a literature source. Lessons below may appear in a skill only as clearly labelled team experience
("in CosmicCoder agent runs ...") and only in general form.

## The readers

The skills are read by research agents working on ALMA data: single Claude Code agents, research frameworks
(Denario, AutoResearch) and teams of agents (questioner, worker, reviewer/validator, editor) that post findings to a
shared forum and are graded against published papers or by astronomers. Tasks come in two shapes:

- **Bottom-up / reproduction**: given an ALMA dataset (and maybe a literature summary), find what the paper found.
- **Top-down / novel**: given a research question, pick the method and the data, then answer it.

Evaluation decomposes a paper into (hypothesis, experiment, result, finding) tuples and asks: are the individual
experiments correct, are the final conclusions correct, are the findings significant, are they novel. Experts want
each experiment traceable to code.

## Lessons from the runs (write skills that prevent these)

1. **Agents reimplemented a naive version of a standard package** (a cube kinematics fitter) and got a worse
   measurement than the paper. Agents need to know which established tool does the job and reach for it.
2. **One dataset is rarely enough.** Good projects needed several datasets to clear up inconsistencies and to check
   earlier literature claims, plus tables and numbers from other papers. One framework gave up when a table from
   another paper was needed.
3. **Downloading whole projects is a trap.** An agent tried to fetch about 4 TB of raw data by project code; the
   analysis needed only specific products, which astroquery could fetch. Older-cycle data that needed
   reprocessing could not be processed in that environment (CASA/tclean was not installable on one HPC system).
   Archive image products were often usable as delivered.
4. **Unstated and inherited conventions break reproductions.** A paper in a series reused corrections (for
   example flux and number recovery from artificial source insertion) and design choices from its earlier
   papers without restating them. Reproduced images were noisier than the paper's and nobody could tell what
   extra preprocessing the authors had done.
5. **"Done" must mean executed and checked.** A framework's judge approved tasks when code had been written but
   not run. Stricter gates (the file ran, outputs exist and look sane) fixed it.
6. **Context flooding.** Agents printed huge raw tables into their context, costing millions of input tokens.
   Summarise; write tables to files.
7. **Overconfident conclusions.** One system's conclusions were "more confident than its evidence supports".
   Single agents stopped after minutes having characterised the obvious bright component and missed the faint
   compact signal that was the real finding.
8. **No stopping criterion.** Open-ended runs became a money pit, agents going back and forth verifying claims
   they could only speculate about given the data. Agents need a rule for when the evidence is enough and when a
   question cannot be settled with the data in hand (and should be written down as open).
9. **Verifiers and editors help.** Adding a verifier/editor that asked "what is the most important question?"
   raised scores; teams with worker and validate roles beat strict pipelines; adaptive iterative loops beat
   heavy fixed pipelines. Staged work (each stage with tests and an answer key, stop or retry by stage) worked for
   model reproductions; open items needing expert confirmation were recorded rather than forced.
10. **Novelty is easy to fake.** Ideation agents treated unpublished data as proof of a novel question without
    checking whether the same question had been answered with other datasets, and repackaged an observing
    proposal into analysis tasks instead of distinct hypotheses.
11. **Results need tolerances.** Reproductions reported agreement to stated precision (for example within 0.3% or
    "within reading precision" of a figure) and explained each remaining mismatch (smoothing of a published
    figure, a possible table typo) instead of declaring success or failure overall.

## Contamination rule (critical)

The team's evaluation tasks are held out of the corpus. Never name, describe or hint at their targets or results
in a skill: no L1521F / L1521F-IRS, no "CMF across Galactic environments" protocluster series, no z~6 quasar-host
[CII] kinematics sample results, no SZ quasar-feedback detection in HE 0515-4414, no specific numbers from those
papers. Write general practice from the pack. If a lesson above came from one of those tasks, state it only in
general form (as it is phrased above).

=== EVIDENCE PACK (injection-null-tests) ===
# Evidence pack: Injection-recovery, null and jackknife tests (`injection-null-tests`)

Scope: injected synthetic sources or models, null and jackknife tests, Monte Carlo realisations used to trust detections, fluxes, sizes, offsets and completeness

Built from 208 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2013-2026.
Matcher (regex over analysis steps): `inject|artificial (?:source|core|point|gaussian)|insert\w* (?:\w+ ){0,3}(?:source|model|gaussian)|mock (?:source|observation)|null test|jackknife|monte carlo (?:simulation|test|realization)|recover\w* (?:the )?(?:injected|input)|false[- ]positive`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- high_z_galaxies: 112
- star_formation: 55
- agn_and_quasars: 43
- nearby_galaxies: 32
- protoplanetary_disks: 22
- milky_way_ism: 19
- galaxy_clusters_and_sz: 17
- cosmology: 16
- transients: 12
- exoplanets: 8
- astrochemistry: 7
- debris_disks: 6
- stellar_physics: 5
- instrumentation: 3
- evolved_stars: 2

### Software named in the matched steps
- casa: 24
- sextractor: 9
- imfit: 6
- tclean: 5
- python: 5
- simobserve: 5
- getsf: 4
- scipy: 4
- uvmultifit: 4
- lineseeker: 4
- photutils: 4
- findclump: 3
- galfit: 3
- astrodendro: 3
- jackknify: 2
- powerlaw: 2
- ipag-adi pipeline: 2
- kinms: 2
- lmfit: 2
- numpy: 2
- casa simobserve: 2
- phantom: 2
- clumpfind: 2
- priism: 2
- mpfit: 2
- pybdsf: 2
- astropy: 2
- radmc-3d: 2
- iraf: 2
- eazy: 2
- starburst99: 2
- idl: 2
- ciao: 2
- wavdetect: 2
- esorex: 2
- findclumps: 2
- uvmcmcfit: 1
- interferopy: 1
- principal component analysis: 1
- sed animation: 1

### Fitting methods (most common phrasings)
- logistic function: 2
- Gaussian fit; errors from fit and Monte Carlo injection of model profiles in random cube regions: 1
- chi-square Gaussian fit to averaged visibilities vs uv distance: 1
- Two-dimensional Gaussian fits in the uv-plane with UVMCMCFIT: 1
- Monte Carlo sampling with Gaussian priors on fluxes and spectroscopic/photometric priors on redshift: 1
- Fit logarithmic double power-law function to non-zero flux density bins of each Monte Carlo realization: 1
- Maximum likelihood estimation (MLE) with Kolmogorov-Smirnov (KS) distance minimization (Clauset et al. 2009) coupled wi…: 1
- Seven-day bins for photon-index variations: 1
- ABC with 33 iterations (32 iterations with n=500 particles, final iteration with n=5000 particles, reaching D_tot < 0.0…: 1
- imfit elliptical Gaussian: 1
- galfit; bootstrap errors: 1
- grid of injected negative planets, no sampler: 1
- Least squares greybody; sampler/priors not stated: 1
- Least-squares ellipse fit; 1000 Monte Carlo realizations with Gaussian parameter errors give 1 sigma on ring parameters: 1
- Same two-component chi-square self-calibration as step 2: 1
- Running median window applied to dynamic range time series: 1
- Iterative 2D Gaussian fitting with CASA IMFIT varying fitting area and position offsets: 1
- Monte Carlo sampling (1000 iterations) from normal distribution with 20% standard deviation: 1
- Gaussian least squares with instrumental broadening incorporated; components added only if previous detected: 1
- Monte Carlo sampling (100,000 iterations); uniform prior on f_c in [0.77, 1.00], normal distribution on ΔI/I_c: 1
- MultiNest Bayesian inference; models CM, WM, TS compared via evidence and reduced chi2: 1
- Monte Carlo simulation with 40,000 realizations with Gaussian-added noise on flux and model parameters; error bars defi…: 1
- Monte Carlo simulation of 100,000 samples of 92 targets with Poisson 95% confidence level: 1
- Uncertainties on L_IR and M_dust by Monte Carlo simulations; points weighted by their uncertainties: 1
- chi-square minimisation of observed vs model visibilities with lmfit: 1
- Error-function fit of Q(x) and C(x); sampler, priors, likelihood not stated: 1
- Power-law fitting to histograms/cumulative distributions and Maximum Likelihood Estimation (MLE) via powerlaw package a…: 1
- Iterative convex optimization minimizing chi-squared + l1-norm + TSV cost function with NuFFT (N_iter = 1000); 2D Gauss…: 1
- Weighted Pearson correlation coefficient averaged across the 8 galaxies: 1
- Bisector fits; priors and likelihood not applicable: 1
- Visibility delta-component fitting via UVMULTIFIT; core spectral index power-law fit checked with reduced chi^2: 1
- Four empirical templates; additional AGN obscuration allowed: 1
- spline: 1
- Monte Carlo sampling: 1
- Non-linear least squares; errors from 1000 Monte Carlo realizations with normal noise; mean and std dev: 1
- Nested sampling with nessai using priors and conditions in Table 7: 1
- MPFIT Gaussians: 1
- Same scipy.curve_fit procedure as for the real data: 1
- Function fitting of the form a * S/N_peak^m + b * S/N_peak^n and interpolation in (S/N_peak, Theta_beam) bins: 1
- Best-fit = highest-probability grid point; 68%, 95% and 99.7% intervals from integrating the normalized likelihood; sec…: 1

### Validation checks used
- Fit errors consistent with Monte Carlo errors: 1
- Image-plane and uv results agree; injection tests for bias (3%) and scatter (20%): 1
- Tested sensitivity to assumed source sizes for low-S/N sources using point source and r_eff,obs = 0.5'' extreme cases: 1
- Compared simulated noise map spurious counts with negative mosaic detections and unassociated source counts: 1
- Compared against Paper IV counts and evaluated cosmic variance via three methods (empirical field-to-field variance, Dr…: 1
- Compared direct summation EBL values with double power-law integrated EBL and Planck/COBE estimates: 1
- Mock simobserve data show jackknife realizations match the noise structure and standard deviation of cleaned noise maps…: 1
- On simulated data FindClump on 50 jackknife realizations gave a smooth noise peak distribution and recovered the inject…: 1
- Jackknifed negative-peak PDF compared with the real data; scatter within the 95% interval is consistent with Poisson un…: 1
- Discarded W51-E (completeness limit 3.86 M_sun) and adopted the highest remaining field completeness limit (1.64 M_sun)…: 1
- Verified that the first KS distance minimum occurs at x_min = 1.40 M_sun (α = 2.07 ± 0.06), compatible with x_min = 1.6…: 1
- Reprocess injected cubes using the different ADI algorithms.: 1
- First-epoch split sequences and injections recover sources; second-epoch non-recovery is inconclusive.: 1
- Mass rate compared with earlier resolved CO study and MUSE integrated-spectrum results: 1
- Photon-index/flux anticorrelation confidence greater than 99.99%: 1
- Compared posterior predictions to observed structure functions (1-sigma envelopes), simultaneous NIR-X-ray flux pairs, …: 1
- point-source fits imply true size <=0.18'': 1
- injection recovery: 1
- Error budget adds retrieval, plate scale and true-north terms in quadrature: 1
- Fitted tau compared with computed tau_dust: 1
- Reduced chi2 0.6-2.3 (4 at z=0.1"): 1
- Gaussian correction selected because it recovers properties of injected clouds: 1
- Successful recovery of the injected synthetic transient in both 4 s and 12 s residual images with peak S/N of 15.194 an…: 1
- Manual inspection of residual snapshot sequences and verification against antenna elevation (< 25 deg exhibits signific…: 1
- Restricted HA range matching actual observations (-3h20m < HA < +1h) yields maximum systematic VF ~ 1.6; adopted conser…: 1
- Dedicated sensitivity tests in Appendix: varying explosion centre by +/-5 pixels (1000 realizations), adding synthetic …: 1
- Compared ALMA CO(1-0) flux to IRAM-30m (45% recovered): 1
- Checked saturation bottom of HCN J=2-1 at +5 km/s yielding lower limit f_c ~ 0.8, consistent with f_c >= 0.77: 1
- Grid of 36 fits with different data cuts; none statistically good: 1
- Tested T=25 K with no significant difference in gas distributions: 1
- Model-based albedo cross-check from Q_abs and Q_sca (omega = 0.56 over all angles; ~0.1 for restricted scattering angle…: 1
- Inferred apparent diameter of 9.6 mas is consistent with the point-like appearance (<40 mas) in the visibility curve.: 1
- Tested the Monte Carlo detection rate model on the BPMG sample itself (100,000 samples of 12 targets), reproducing the …: 1
- Model injection-recovery S/N; comparison with previous mid- and far-IR constraints.: 1
- Checked against X-ray, radio spectral index, magnetic field geometry and Sigma-r relation: 1
- Fake companion injection to correct flux loss: 1
- Completeness resilient to atmospheric variation: 1
- Sinusoidal Stokes V vs parallactic angle amplitude consistent with MC uncertainty: 1
- Mardling & Aarseth stability criterion and REBOUND N-body integration over 1000 outer periods: 1
- Compact sources too weak to produce offset; at S/N 5.2, 22% of injected clusters are recovered more than 30'' away: 1

### Key parameters and settings (bibcode: value)
- 2017ApJ...846..108C: line flux contained within 2'' circular radius
- 2017ApJ...846..108C: 36000 injected models, peak SNR 1-10, radius up to 2''
- 2023A&A...675A..85M: Peak-to-integrated flux ratios of 0.80 (A370) and 0.71 (AS1063) for 4.5 <= S/N < 5 sources
- 2023A&A...675A..85M: 300 simulated noise maps per cluster; 10^4 simulated SIDES point sources for Eddington bias check
- 2023A&A...675A..85M: 1000 realizations per lens model per cluster field
- 2023A&A...675A..85M: Parameter bounds: N_0 = 10^3 - 10^6 mJy deg^-2, S_0 = 0.01 - 1 mJy, alpha = 0 - 5, beta = -1 to 1
- 2025A&A...695A.204V: 50 jackknife realizations per observation, ~9 min per iteration on a 2019 MacBook Pro
- 2025A&A...695A.204V: line widths 100-500 km/s (3-11 channel widths)
- 2025A&A...695A.204V: peaks above S/N of 0 retained; duplicates merged within 0.2 arcsec and 0.2 GHz
- 2025A&A...695A.204V: SExtractor analysis and detection thresholds both set to 2
- 2025A&A...695A.204V: detection threshold gamma = 4 sigma, critical value k = 3
- 2024A&A...690A..33L: Gaussian FWHM = 3840 au; minimum separation > 2.5"; border exclusion = 5"; 10 flux bins (equivalent to 0.5-5 M_sun at 20 K, or 1-10 M_sun in W51-E); 4 draws pe…
- 2024A&A...690A..33L: x_min = 1.64 M_sun; n = 330 cores; 10^3 Monte Carlo trials with β ~ N(1.5, 0.2), T ~ N(T_core, σ_T), and Gaussian flux errors; 10^5 Salpeter synthetic trials.
- 2021AJ....161..146J: Fake planets every 10 pixels at 3 position angles; 100 ADU.
- 2021AJ....161..146J: Azimuthal average of throughput losses at each radius.
- 2021AJ....161..146J: Second-epoch injected source has the first-epoch flux.
- 2020MNRAS.491.2506D: 8 random integer rotations; 0°≤θpos<360°; 5°≤φinc≤85°
- 2020MNRAS.491.2506D: 64″×64″ mock velocity-map field
- 2020MNRAS.491.2506D: Galaxy radius = 98th percentile particle distance from centre of potential
- 2020MNRAS.491.2506D: Mock bmaj = 3″; stacked velocity-map dimensions 64×64×8
- 2020MNRAS.491.2506D: Non-numerical values and infinities replaced with 0 km s−1
- 2026A&A...707A..77H: minimum r_out = 1.49 kpc for CO (half the ALMA beam major axis); minimum 0.72 kpc for MUSE phases (half the MUSE PSF FWHM)
- 2026A&A...707A..77H: r_out is the distance of each bin centre to the SE nucleus
- 2025A&A...694A.291K: Bayesian block false positive rate 0.01 in all bands; local maximum exceeds both adjacent blocks
- 2025A&A...694A.291K: P1: MJD 57300–57550; P2: MJD 57550–57940; P3: MJD 57940–58400
- 2021ApJ...917...73W: 230 GHz structure function restricted to time lags < 50 minutes; VLT positive flux fraction target = 0.9; VLT skewness target = 3.44; M/K ratio R_obs = 12 +/- …
- 2015ApJ...799...81S: SNR>=10 required for 68% of sources recovered with fractional size error <30%
- 2025ApJ...990L..70L: optimal position is median over aperture radii 0.75 to 1.5 FWHM
- 2025ApJ...990L..70L: true north 2.0 +/- 0.6 deg; pixel scale 5.93 +/- 0.03 mas
- 2016ApJ...832..187B: Te=1e4 K; ne = 3e5, 3e6, 3e7 cm-3 for MM1D, MM1B, CM1
- 2018A&A...618A.120L: pv diagrams every 0.15" from z=0.1" to 1.75"
- 2017MNRAS.468.1769F: 50% completeness 3.35e5 Msun
- 2022A&A...666A..39M: Synthetic transient: peak ~207 mJy, duration ~42 s, centered at 10:52:01 UT, offset 5 arcsec East and 1 arcsec North of Sgr A*
- 2022A&A...666A..39M: Detection threshold: peak excursion of 7 times the instantaneous rms between consecutive images; at least 3 standard deviations in maxima between two consecuti…
- 2022A&A...666A..39M: Minimum duration: 12 s (three 4 s integration times)
- 2023MNRAS.522...56V: Source FWHM = 0.1 to 0.9 arcsec; peak flux density = 5 to 100 mJy beam^-1
- 2023MNRAS.522...56V: Hour angles = -5 h to +1 h (7 observations of 1 h each); pixel size = 0.05 arcsec; image size = 100 x 100 pixels
- 2026MNRAS.548ag325W: 1000 Monte Carlo iterations, 20% standard deviation per data point, 3-point moving average, percentiles: 25th, 75th, 95th
- 2018ApJ...863..193V: 2500 MC iterations for per-pixel maps
- 2026ApJ..1000..141K: 100,000 Monte Carlo realizations
- 2026ApJ..1000..141K: f_c uniform distribution in [0.77, 1.00]
- 2017MNRAS.464.4624S: Flat (uniform/log-uniform) priors on all parameters except Galactic reddening (Gaussian, mu=0.56, sigma=0.04)
- 2017MNRAS.464.4624S: UVOT UV filters and u band excluded in best fits
- 2014ApJ...796....1T: Box 1740 AU, finest cell 0.85 AU, sink radius 3.4 AU, n_inj=1.5e5 cm-3, T=13.5 K
- 2025MNRAS.541...71M: Ages 30 ± 10 Ma, 45 ± 5 Ma and 348 (+39/-54) Ma
- 2022A&A...659L...1L: Beaming factor eta = 1.175+-0.42 (restricted to >0.6)
- 2022A&A...659L...1L: Bolometric emissivity epsilon_b = 0.90+-0.06 (<1) and relative radio emissivity epsilon_r = 0.70+-0.13 (<1)
- 2022A&A...659L...1L: HV = 8.21+-0.05, HR = 7.75+-0.05, V-R = 0.46+-0.02, phase integral q ~ 0.4
- 2021MNRAS.502.5390P: Stellar masses 1.15 to 1.58 M_sun, [Fe/H]=0.0; Fisher test alpha = 0.05; grid R_BB = 0.01-1000 au, f_d = 10^-7 to 10^-2; evolution t_0 = 23 Myr (or 2 Myr), alp…
- 2025ApJ...989L..22B: ABA belt at 2–3 au; opening angle 5°; disruption threshold 10^7 erg g−1
- 2024A&A...691A..70N: Coupling efficiency 30%, injected energy 1e51 erg per SN
- 2020A&A...633A.115K: 5 sigma contrast; separations 0.14-1.20 arcsec in 0.054 arcsec steps; 60 deg PA increments
- 2020ApJS..251...14H: masses from flux assuming Td = 20 K
- 2019A&A...623A.111H: D-terms 1%, X-Y phase 2 deg, X-Y bandpass 0.1% and 0.5 deg, thermal 8.5e-5 Jy
- 2024A&A...691A..57M: M1=1.6, M2=0.4 Msun, ai=5 au, ao=35 au, Mdot=1.1e-6 Msun/yr, T1=2800 K, v_ini 8 or 15 km/s, M3=0.1/0.6/1.2 Msun
- 2023PASJ...75..311K: spectral index -0.7 assumed for the compact-source effect on peak y (at most 4%)
- 2019ESC.....3.2088S: n_H2 = 5e7 cm-3, T=150 K, zeta = 3e-17 s-1
- 2018MNRAS.481.1976Z: L_IR integrated over 8-1000 um from SED fitting
- 2018MNRAS.481.1976Z: <U> = L_IR/(125 M_dust)
- 2020MNRAS.495.3409S: five free parameters: R.A., Dec., flux density, half-light radius, axial ratio
- 2020MNRAS.495.3409S: optimisation repeated ten times from random starting values; lowest chi-square kept
- 2020MNRAS.495.3409S: boosting correction from running median of recovered/input flux vs detection significance
- 2020MNRAS.495.3409S: axial ratio uniform 0-1; half-light radius uniform 0.05-0.30 arcsec
- 2020MNRAS.495.3409S: emitters >= 0.05 mJy injected within 8.7 arcsec of recovered SCUBA-2 positions
- 2025PASJ...77.1163H: Peak S/N 2.0-7.0 in 0.5 steps (11), FWHM 36-396 km/s in 36 km/s steps (11), 121 parameter sets, 84 positions, 100 repeats, 1,016,400 sources
- 2025PASJ...77.1163H: x = (peak S/N, FWHM); Q and C fitted with error functions with parameters a1, b1, a2, b2 per FWHM
- 2026ApJ...997..155M: 5000 trials; primary beam response > 40%; 90% completeness threshold = 1.2 M_sun after excluding 5 clumps; flux correction applied where completeness > 0.5
- 2026ApJ...997..155M: M_min = 1.2 M_sun; 1000 Monte Carlo trials with mass scaling factor uniformly in 0.5-1.5
- 2021ApJ...923..121Y: Lambda_l = 10^5, Lambda_tsv = 10^9 (optimal from 5x5 grid)
- 2021ApJ...923..121Y: N_iter = 1000, 10-fold CV
- 2022A&A...663A..61P: Galaxy selection criteria: >= 3 environments, has bar and spiral arms, < 50% pixels removed by detection threshold (yields 8 galaxies with log M_* >= 10.6)
- 2022A&A...663A..61P: 50 Monte Carlo simulations per galaxy for correlation uncertainty
- 2024A&A...687A.293Q: SFE bootstrap within error bars, 10 000 realisations
- 2026A&A...712A.244H: 1000 Monte Carlo realizations; noise std devs: X-Y Phase = 2 deg, X-Y Bandpass amp = 0.1% (B4, B6) / 0.2% (B7), X-Y Bandpass phase = 0.5 deg, D-terms = 0.5% (B…
- 2021A&A...654A..37D: Templates span 0.03–30 μm; 1000 Monte Carlo realizations per source
- 2015ApJ...807..128S: completeness 93% at >4 sigma, ~100% at 5.5 sigma
- 2024A&A...682A..55M: 10^6 Monte Carlo realizations per case; uniform eccentricity priors [0.0, 0.7] and [0.0, 0.9]; mass ratio q = M_Sz65 / M_Sz66 (and inverted for Sz 66)
- 2018ApJ...864..174A: daofind sigma set to off-source noise for ALMA
- 2019ApJ...883...71C: reference frequency 230 GHz
- 2019ApJ...881...10B: ~100 line-free channels with |v_LOS - v_sys|>500 km/s used as noise
- 2021ApJ...912...21E: Broken power-law injection spectrum with q_1 = 1.5, q_2 = 2.5, and peak Lorentz factor gamma_b = 10^5 (and 10^4 for PTF10hgi)
- 2023A&A...674A..75N: 0.44'' beam for deconvolution; 1400 synthetic sources (~800 in ridge) with 0.6'' Gaussian FWHM in 10 mass bins from 0.16 to 2.4 M_sun across 4 synthetic images
- 2026MNRAS.550g1193B: For twocomponent_refreshed: fixed theta_obs = 0, log epsilon_e = -1, log epsilon_B = -2, xi_N = 1
- 2026A&A...706A.365M: Input delta_v = 1 km/s, gamma_tau = 4.0 (NE) and 8.0 (SW), f_c = 1.0 (NE) and 0.95 (SW); 13 (NE) and 5 (SW) Gaussians; noise rms 0.5%
- 2019ApJS..244...40L: 150+ representative images; 4225 realizations per image for FULL, 273 for PHYS; cross-match radius = 1.5 arcsec for PyBDSF completeness
- 2021ApJ...909..165Z: Flux density bins of 25 uJy, 10,000 repetitions per bin; recovered if within ~1.5'' (one synthesized beam) of the input position
- 2021ApJ...909..165Z: A_eff = 184 arcmin2; 100 Monte Carlo realizations
- 2021ApJ...909..165Z: Source MORA-10 removed for star-forming-only counts (about 40% synchrotron contamination)
- 2021ApJ...909..165Z: Grid: alpha_LF in [-0.6,-0.2] step 0.05; Psi_2 in [-8.8,-2.2] step 0.4; beta_em in [1.5,2.6] step 0.05
- 2021ApJ...909..165Z: Nelder-Mead: random initial starting point per realization, each search limited to 100 evaluations; z_cutoff = 5.5-9.0 added as fourth parameter
- 2021ApJ...909..165Z: Fixed: beta_LF = -3.0, gamma_1 = 2.8, gamma_2 = 1.0, Psi_1 = 0, z_turn = 1.6 - 0.09 Psi_2
- 2026ApJ...999...47L: SNR >= 5 sigma threshold; 100 simulation iterations
- 2026ApJ...999...47L: A_eff = 577 arcmin^2; 10^3 Monte Carlo iterations; flux density bins of 100 uJy; redshift bins of dz = 1
- 2026MNRAS.552g1573L: 10,000 Gaussian uncertainty realizations, followed by random permutation for null tests
- 2026MNRAS.552g1573L: p=(b+1)/(n+1); significance p<0.05
- 2020ApJ...903..124B: 10,000 realizations for each of two null tests; fixed measured x-values
- 2020ApJ...903..124B: Shuffle measured y-values or draw unrelated y-values with the measured intrinsic scatter
- 2021ApJS..257...43L: Inclination uncertainty +-5 deg (capped at 90 deg); M_star uncertainty ~0.1 dex; SFR uncertainty ~0.15 dex; distance uncertainty 0.03, 0.06, or 0.125 dex
- 2021ApJS..257...43L: Selection criteria: -75 deg < delta < +25 deg, i < 75 deg, d < 17 Mpc, log10 M_star > 9.75, log10(SFR/M_star) > -11 yr^-1
- 2024ApJ...976..198H: Injection-identification sequence repeated 40 times per setup
- 2024MNRAS.533..771R: Stopping criterion: no channel > 5 sigma and fitting region RMS < 1.5 times remainder RMS; 10,000 Monte Carlo realizations
- 2023ApJ...954..197I: N^2 = 36 modes (22 intermediate modes with 3.5 < sqrt(m^2+n^2) < 6.5), L = 3.6'', source mesh = 6.66 mas or 13.3 mas, |mu| <= 30
- 2015A&A...584A..78C: boost ~1.09 at S/N=3.5
- 2024A&A...683A.141R: Dust mixture 70% water ice and 30% astro-silicates; size distribution slope changed from -3.5 to -3.0; distance 162.9 pc; max dust size 1 cm
- 2019ApJ...881...43K: SFR 2.8 Msun/yr over 1 Myr
- 2024ApJ...974..279D: Other forward shock parameters kept fixed; lower frequency radio bands excluded
- 2017ApJ...844..123F: Redshift fixed (QSO z for composites, 2.5 otherwise)
- 2020ApJ...897...91G: fidelity 50% at S/N=4.3 (natural), 3.3 (tapered)
- 2020ApJ...897...91G: channel weights w=1/sigma_i^2
- 2020ApJ...897...91G: N0=1-100e3 mJy^-1 deg^-2, S0=0.05-1.0 mJy, alpha=1.5-5, beta -2 to 2; fluxes 0.03-2 mJy; histogram bins 4.3 uJy/beam
- 2024A&A...691A.248L: 9 redshift bins from z = 0.1 to 5.0; 6 stellar mass bins from log10(M*/Msun) = 8.5 to 12.0
- 2024A&A...691A.248L: Completeness threshold = 90%
- 2025ApJ...979..142N: 32 walkers, uniform prior -5.0 < alpha < 5.0, 5000 Monte Carlo samples with Gaussian(mean=1, std=0.1) for ALMA calibration error
- 2020MNRAS.498.4256C: 500,000 gas SPH particles; 125,000 dust particles
- 2020MNRAS.498.4256C: Adopted d = 5 for discs with q <~ 0.3
- 2023A&A...676A..67W: gamma = 1 (radiative); eta = 1/4 adopted for t_dyn; L = 1 x 10^34 erg s^-1 M_sun^-1 (1 x 10^40 erg s^-1 per 10^6 M_sun); epsilon = 10% adopted for M_cl
- 2024MNRAS.531.4045C: Inflow width W_in = 100 pc; Nuclear ring radius R_NR = 270 pc; Circular velocity V_c,NR = 170 km s^-1; Annulus inner semi-major axis = 240 pc, outer = 385 pc, …
- 2024ApJ...971...52M: 5000 Monte Carlo realizations, removing a random number of light curve points each time
- 2024ApJ...971...52M: Delay significant if zero is outside the 95% interval
- 2023A&A...674A.101M: Plasmon injection time t_0, core flux I_c (< 0.18 Jy), plasmon flux I_p, decay power beta, plasmon spectral index alpha_p, time delay Delta t, differential mag…
- 2013MNRAS.432....2K: 3.5 sigma limit: ~99% recovered, ~1.6% spurious
- 2024PASJ...76..437Y: Point-source flux 5% of target total flux, placed north of the star in an emission-free area within MRS
- 2019ApJ...871....5T: r_pk=95 au, sigma_r=10 au, Sigma_d,0=1.84e-2 g cm^-2, h_d=9.8 au, a_max=1 mm, gas Sigma ~ r^-1 for 8-320 au, h_g=13.2 au (r/95 au)^1.25, gas-to-dust 100
- 2019ApJ...881..124M: VR7 collapse 252.285-252.519 GHz (-20 to -320 km/s wrt Lyα)
- 2020MNRAS.494.5542R: 1000 noise realizations; S/N thresholds 1, 2, 3 averaged for the magnification
- 2020MNRAS.494.5542R: Mock sources: uniform ellipse 3.4x2.4 kpc and an FIR-luminosity-map source, forward-lensed with the SDP.81 lens model
- 2020MNRAS.494.5542R: CO(1-0), CO(7-6) and CO(9-8) assumed to follow the spatial distribution of CO(3-2), (8-7) and (10-9)
- 2025A&A...699A.324H: Recovery: peak S/N>4.2 within 0.7″ of injected position
- 2025A&A...699A.324H: For peak S/N<20, divide imfit flux by median measured-to-true flux ratio at that S/N
- 2025ApJ...987...77J: Low-mass cutoff = 3 M_sun; CMF power-law index Gamma = -1.00 and -1.35; initial pool size = 10^6 cores; 5000 repetitions per cloud; 10^6 iterations for Taurus+…
- 2022MNRAS.513.5790C: Time interval = 1.75 yr; fake point source flux = 126 uJy; disc inclination i = 130 deg, PA = 160.4 deg
- 2022MNRAS.517..632L: Radial bin size = 2 pc, PA = 1 deg, i = 9.3 deg
- 2026ApJS..284....3H: Dendrogram threshold = min + 5 * step; min_npix = 41 (F2100W) or 10 (F1000W); min_delta = 3 * step; min separation = 0.33'' (F1000W) or 0.17'' (F2100W); backgr…
- 2026ApJ..1000..231B: First forecast: truncated normal with mu ∼0.55 and standard deviation ≃0.2
- 2026A&A...705A.238V: Disk masses 1% to 10% of stellar mass
- 2026A&A...705A.238V: 1000 orbits simulated
- 2019ApJ...882..139G: Gaussian kernel sigma_GK 0-19 (LineSeeker); top-hat N=1-9 (FindClump); spatial kernels FWHM 0-4'' (MF3D)
- 2019ApJ...882..139G: peaks 0-2 mJy/beam, FWHM 0-~1000 km/s, 84.2-114.2 GHz
- 2023MNRAS.518.6142A: N_MC = 100 realizations
- 2023MNRAS.518.6142A: 4 stellar mass bins with 8-10 galaxies per bin (or 2 bins each when splitting detections and non-detections)
- 2023MNRAS.518.6142A: Starburst threshold: SFR_UV+IR > 3 x main sequence at z=7 (excluding 8.5 +/- 2.1 out of 45 galaxies on average)
- 2024ApJS..275...36F: 1,000 artificial sources per cluster; total flux range 2.5–80 × σ_cont.
- 2024ApJS..275...36F: Apply 10% flux correction below SNR = 8; completeness floor 10%.
- 2024ApJS..275...36F: Recovery within 1.0″ of injected position.
- 2025A&A...696A.151C: Completeness fluxes 0.58, 0.94 and 2.05 mJy for Groups 1, 2, 3 (rms < 0.06, 0.06-0.1, > 0.1 mJy/beam)
- 2021ApJ...916...97Y: 5000 Monte Carlo iterations for 12 Class 0 protostars (60,000 simulated data points); T_bol < 70 K threshold for young/Class 0 subset
- 2021ApJ...908...19B: 300 Monte Carlo realizations; 1 sigma from the 15.9 and 84.1 percentiles; oversampling fiducial s = 4
- 2024ApJ...977..121N: 3x3 Sobel kernels; per-channel width 2.5 km/s
- 2026A&A...706A.206H: Ensemble cuts: span >= 95% of the candidate's span and SNR_var < 5; 10 to 18% of the original 204 light curves remain
- 2020A&A...634A...9M: B = 2.6 uG for lobes
- 2025ApJ...984L..57O: Rc=120 au, gamma=0.8, Mdisk=0.1 Msun, alpha=1e-3, dust-to-gas 0.02, Mstar=0.8 Msun
- 2019Natur.572..211W: A_V up to 6 mag
- 2023A&A...679A.119R: Z = 0.1 - 2.0 Z_odot
- 2023A&A...679A.119R: 50% errors assumed on line ratios
- 2024A&A...687A..35R: E_SNII = 10^51 erg per SNII; xi = 0.01 per Msun x SFR for a Chabrier IMF
- 2024A&A...687A..35R: thin disc h = 0.3 kpc and thick disc h = 1.0 kpc
- 2026A&A...707A.221S: N_cores >= 8 (296 clumps); 1000 random draws for <l_random>; 500 Monte Carlo realizations with 20% Gaussian core mass uncertainty; >70% probability threshold f…
- 2020ApJ...901...71S: Aperture radii 1 to 27 pixels; 2 to 32 consecutive channels (~0.16 to 2.5 km/s)
- 2023PASA...40...17W: log Sigma_* bins: [0, 0.75), [0.75, 1.25), [1.25, 1.75), [1.75, 2.25), >= 2.25; non-detections set to log Sigma = -0.5; quantitative Sigma_mol comparisons rest…
- 2026MNRAS.552g1615S: 1 sigma confidence intervals from 1000 Monte Carlo simulations
- 2025A&A...694A.165T: False-positive probability threshold 1e-5 (falsesrc=-1, sigthresh=1e-5)
- 2023MNRAS.519...34H: Mock peak flux = 1 to 8 times cube r.m.s. (step 0.1), line width = uniform 10 to 500 km s^-1
- 2023MNRAS.519...34H: Reliability fit parameters: C = 6.24, sigma = 2.56, a = 0.65
- 2025A&A...696A..95G: N=5 neighbour estimator
- 2024A&A...686A.122A: ~800 sources in ten log-spaced mass bins between 0.15 and 3.0 Msun; Gaussian profile with FWHM 1.3 arcsec (3000 au)
- 2020MNRAS.499.2015T: Observed PSF FWHM about 63 mas (K1) and 66 mas (K2); 96 s exposures smeared by field rotation
- 2024MNRAS.535.2538Z: Maps restricted to regions where A/N exceeds the 99% false-positive threshold for each line
- 2019MNRAS.487.4648S: Injected fluxes from power law index -2, sizes uniform 0 to 0.9'' FWHM, recovery within 0.6''
- 2021ApJ...907..122M: Velocity bin widths: 80, 140, 300, 750 km s^-1
- 2021ApJ...907..122M: Peak SNR threshold > 6.2; velocity-integrated SNR > 8 within ±0.5 FWHM
- 2025ApJ...993..111W: Five lines per injection, repeated 10 times: 50 fake sources per field.
- 2025ApJ...993..111W: ALMA USB SNR≥8.0; LSB SNR over 7.0; same thresholds for NOEMA.
- 2024ApJ...967...56C: 10 cores per experiment, 10 repetitions per flux
- 2021PASJ...73S..35T: Expansion velocity ~50 km s^-1 (half of velocity separation)
- 2025ApJ...988..215K: Aperture sizes from l_ap,min ~100 pc to l_ap,max ~3 kpc (per-galaxy values in Table 2); 1000 realizations
- 2017ApJ...850...83F: sizes 0.04''-3.0''; random positions within 10'' radius; SNR bins 5-10, 10-20, 20-30
- 2022A&A...660A..14R: z_med = 5.52
- 2022A&A...660A..14R: 500 jackknife realizations removing 20% of spectra; 16th and 84th percentiles for error
- 2022A&A...660A..14R: 2 SFR bins of 17 objects each divided at log(SFR_TOT,med / M_sun yr^-1) = 1.16
- 2024A&A...692A..22Z: 20 sources per bin, normal random flux, random positions with PB response > 0.5 and separations of at least 1 arcsec
- 2024A&A...692A..22Z: recovered if extracted within 1 arcsec of the injected position
- 2018ApJ...867..153C: source = two or more adjacent pixels above 5σ
- 2021A&A...647A.194F: AzTEC/C159: 2 rings of radial width 0.23'', fixed i = 40 ± 10 deg, PA = 170 ± 10 deg
- 2021A&A...647A.194F: J1000+0234: 3 rings of radial width 0.2'', fixed i = 75 ± 10 deg, PA = 145 ± 5 deg
- 2024A&A...684A.119P: Continuum: 20 sources per image, 100 iterations per flux value, 0.02-0.46 mJy in steps of 0.02 mJy (46000 sources)
- 2024A&A...684A.119P: Lines: FWHM 100-1000 km/s and flux 0.02-0.5 Jy km/s, 50 sources per cube, 12500 sources total
- 2018ApJ...862...78C: Pixel size 1/5 of minimum beam FWHM; Band 6 beam 0.6" and RMS 13 uJy
- 2022ApJ...930...32C: 100 MC trials; SSA22 area = 0.28 deg^2; redshift bins 1 < z < 5 with width delta_z = 0.5; incompleteness factor = 1.6 (+0.6/-0.8)
- 2025PASP..137l4501T: Unresolved case: flux taken as peak value in the image; resolved case: flux in circular aperture of radius 3 sigma of the Gaussian
- 2023ApJ...945..121U: 0.5–7.0 keV band; wavdetect false-positive probability threshold = 10^-8; wavelet scales = sqrt(2) sequence (1 to 16 pixels)
- 2023ApJ...945..121U: Cross-match radius = root sum square of 3 sigma statistical error and 99% Chandra absolute astrometry uncertainty (1.4'')
- 2023ApJ...945..121U: Spectral extraction aperture radius = 1.5'' (A370-ID110) and 2.0'' (M0416-ID117, M0329-ID11)
- 2025ApJ...991L..38U: Convergence threshold delta_Te < 10 K; 10,000 Monte Carlo realizations
- 2016ApJ...832...37G: dust = 40% of metal mass; Kroupa IMF; WD01 dust, RV=3.15
- 2023MNRAS.522.6123Z: Frequencies >= 147 MHz; proton-to-electron energy ratio k = 1; Doppler boosting factor delta = 2-4; B_CMB = 3.25(1+z)^2 uG
- 2026A&A...706A.345K: K_IR = 1.73e-10 Msun/yr/Lsun
- 2018MNRAS.479.3879W: 5.5 sigma blind; 5.0 sigma at SIMPLE 3.6 um positions (15% contamination)
- 2021MNRAS.503.1174K: Artificial source flux range: 4.5 - 7.5 \mu Jy within 80'' radius; exclusion radius 1'' around >4\sigma pixels
- 2025A&A...695A.163B: S/N 2–18; widths 100–1600 km s−1; 20 injections per cube, ten repetitions.
- 2025A&A...695A.163B: Retain non-zero completeness cubes; exclude zero-completeness cubes.
- 2021A&A...649A.152K: 250 trials; F_in 0.01 to 0.18 mJy; 6 to 13 images per stack
- 2024ApJ...969...27B: 35 galaxies; 28 inside the MIRI/F560W footprint; z = 0.45–3.71
- 2020A&A...635A.119C: Delta chi2 > 16 for H-alpha-only, >9 per extra line
- 2024MNRAS.528.5019H: purity 0.7 corresponds to peak S/N = 3.6; 45 sources above threshold
- 2016ApJ...833...71A: thresholds: S/N=5.3 (70% fidelity) for blind; S/N=4.5 (40%) for optical-matched within 1''
- 2022MNRAS.515.3126I: Fitting region = 3 x 3 arcsec (1.5 x 1.8 arcsec for REBELS-40); 20,000 mock point sources (100 simulations per image x 5 sources); flux boosting factor = 1.33 …
- 2025ApJ...988..172H: assumed line FWHM 449 km/s; cube binned by a factor of 22; binned RMS ~98 uJy/beam/channel
- 2016ApJ...833...68A: 100 artificial sources total (10x10), matched within 1''; fidelity A=log10(42), B=1/4; completeness A'=log10(35), B'=0.45
- 2020Natur.584..201R: gas scale height h ~ 500 pc; t_D = h/sigma_m
- 2025A&A...704A.158C: 500 mock objects inserted per simulation run; Sersic index n = 1, fixed half-light radius R_h = 0.2 kpc; lensing magnification mu < 5 in A2744
- 2020PASJ...72...69Y: 30,000 artificial sources injected
- 2024ApJ...962..128M: 850 μm false-positive test: peak search within 4″ of 5000 random positions
- 2024ApJ...962..128M: 450 μm false-positive test: fluxes and errors at random positions
- 2024ApJ...961..120C: tau = 100 Myr; M200 = 9e12 Msun; c = 7.9; R500 = 80 kpc
- 2020ApJ...903..138A: 1.4 GHz matching radius 1.6'', false positives 1%
- 2020ApJ...903..138A: 610 MHz matching radius 2.0''
- 2016ApJ...833...69D: fidelity = (Npos-Nneg)/Npos
- 2020ApJ...889...98M: 10,000 Monte Carlo iterations
- 2024A&A...681A.110W: 195 sufficiently bright individual galaxies with Mstar > 10^10 M⊙; 100 Monte Carlo realizations per galaxy
- 2024MNRAS.52710221P: 1000 Monte Carlo realizations with Gaussian noise from the 1D noise spectrum; detection if flux/error > 2
- 2019PASJ...71L...3F: nu = 97 GHz, T = 64 days
- 2020ApJ...902..110D: FWHM 0-800 km/s, peak 0-3 mJy; drop completeness<0.2
- 2018PASJ...70...65U: recovered if >4 sigma and within 1.0 arcsec
- 2017A&A...604A.117C: starburst age lower limit 10 Myr; cloud sizes 50-100 pc
- 2016ApJ...833...67W: Peak flux 0.22-1.00 mJy (3mm), 0.5-2.0 mJy (1mm); widths 50-500 km/s
- 2018ApJ...860..161S: recovery within 0.6 arcsec of injected position


### Assumptions (bibcode: value)
- 2023A&A...675A..85M: Low-significance detections have observed effective radius r_eff,obs = 0.23'' and axial ratio q_obs = 0.58 (median of high-S/N sources)
- 2023A&A...675A..85M: Skip separate Eddington bias corrections since SIDES simulation flux enhancements match deboosting corrections
- 2023A&A...675A..85M: Modified black body with beta = 1.5, T_dust = 35 K, z = 2.5 when scaling literature counts from 850 um, 1.2 mm, and 1.3 mm to 1.1 mm
- 2025A&A...695A.204V: Visibility noise is additive, Gaussian, uncorrelated and zero-mean for well-calibrated data
- 2025A&A...695A.204V: Jackknifed peaks sample the false-detection distribution; peak distribution is a subset of the pixel-value distribution of a smoothed random Gaussian field
- 2024A&A...690A..33L: Synthetic core fluxes converted to mass using the mean temperature of the cores extracted in the corresponding region.
- 2024A&A...690A..33L: High-mass tail of the CMF follows a power-law distribution p(x) = C x^-α above x_min.
- 2020MNRAS.491.2506D: Centre of potential is the origin.
- 2026A&A...707A..77H: Optically thick outflow tau ~ 1 and L_bol ~ L_IR when assessing radiation pressure
- 2026A&A...707A..77H: Energetics treated as order-of-magnitude estimates because alpha_CO is highly uncertain
- 2025A&A...694A.291K: Flux measurements within each Bayesian block are consistent with a constant
- 2021ApJ...917...73W: Single homogeneous spherical/slab synchrotron-SSC zone; R_S = 1.2e10 m; D_s = 2.523e20 m; A_K = 2.46 mag; A_M = 1.00 mag; X-ray extinction factor k_X = 3.39; s…
- 2021ApJ...917...73W: Steady X-ray background equal for all three Chandra detector modes (chi_I = chi_G = chi_S)
- 2025ApJ...990L..70L: injected PSFs are Gaussian while the observed stellar PSFs are elliptical
- 2016ApJ...832..187B: beta=1.7 (MM1D uses 2.4)
- 2018A&A...618A.120L: Narrow circular ring at each z; V0=0 (no orbital motion) for inclination
- 2017MNRAS.468.1769F: Fake clouds follow Local Group size-linewidth-luminosity relations
- 2022A&A...666A..39M: Noise is assumed to follow a Gaussian distribution across ~10^4 beams in the field of view to estimate false positive probability (~10^-8 at 7 sigma)
- 2023MNRAS.522...56V: Artificial sources have constant intrinsic flux density; measured flux variations arise from the changing synthesized beam interacting with source structure an…
- 2026MNRAS.548ag325W: Ejecta are optically thin at the observed wavelengths, in local thermodynamic equilibrium (LTE), and at a uniform temperature; constant expansion velocity
- 2026ApJ..1000..141K: Lognormal column density distribution with parameters from Orion A GMC (mean N(H2) ~ 1.5e22 cm^-2)
- 2017MNRAS.464.4624S: SMC-like host extinction curve
- 2014ApJ...796....1T: Circular binary orbit, isothermal gas, self-gravity ignored, disk coplanar with orbit
- 2022A&A...659L...1L: 100% of measured 0.128+-0.012 mJy thermal flux comes from the nucleus; V_sun = -26.76, (V-R)_sun = 0.35
- 2021MNRAS.502.5390P: Constant disc radius over time during fractional luminosity decay; collisional timescale equals system age (23 Myr for BPMG, 1000 Myr for HD 10647 and HD 10908…
- 2025ApJ...989L..22B: Exozodi coplanar with α Cen AB; grains 1/3 amorphous silicates and 2/3 organic refractories by volume.
- 2024A&A...691A..70N: Energy of multiple SNe is additive
- 2020A&A...633A.115K: age 16 Myr (Sco-Cen)
- 2020ApJS..251...14H: Point-source-like emission model
- 2019A&A...623A.111H: Noise parameters are educated guesses
- 2024A&A...691A..57M: gamma = 1.2, mu = 2.38
- 2015ApJ...811L..19W: COND evolutionary models; 23 Myr age
- 2018MNRAS.481.1976Z: Modified black body beta = 2.0
- 2018MNRAS.481.1976Z: Measured fluxes with uncertainties used even when S/N < 3 instead of upper limits
- 2020MNRAS.495.3409S: Sersic index fixed at n = 1
- 2020MNRAS.495.3409S: input fluxes sampled from the Hatsukade et al. counts with low flux cut-off 0.05 mJy
- 2020MNRAS.495.3409S: input counts model is the best-fit Schechter parameterisation (no clustering)
- 2025PASJ...77.1163H: Mean [C II] redshift z = 6.2 for flux to luminosity conversion
- 2025PASJ...77.1163H: Flat Lambda-CDM with Omega_M = 0.3, Omega_Lambda = 0.7, h = 0.7
- 2025PASJ...77.1163H: Region considered where N_mock <= N_real and N_real > 0
- 2026ApJ...997..155M: Artificial cores have Gaussian profiles
- 2026ApJ...997..155M: Core mass uncertainty is 50%
- 2021ApJ...923..121Y: Non-negative brightness distribution constraint
- 2022A&A...663A..61P: Typical stellar scale height h_* = 300 pc for free-fall time calculation; atomic gas neglected in mid-plane hydrostatic pressure P_h
- 2024A&A...687A.293Q: SFE defined for molecular gas only, SFE = Sigma_SFR/Sigma_mol = 1/tau_dep
- 2026A&A...712A.244H: Single point source dominates emission at phase center
- 2024A&A...682A..55M: Disc midplane lies on the binary orbital plane; uniform eccentricity distribution; sin(i) orbital inclination distribution
- 2018ApJ...864..174A: Compact object is a point source
- 2019ApJ...883...71C: p=3.5, a_min=0.05 um, compact spherical grains; silicates/organics/ice 26/31/43%; vertically isothermal slab, isotropic scattering with effective sigma
- 2021ApJ...912...21E: Energy injection rate L proportional to t^-2 in CLOUDY; singly-ionized oxygen ejecta for free-free absorption in electron-positron PWN model; no ejecta feedback
- 2023A&A...674A..75N: Distance of 5.5 kpc; dust temperatures from Motte et al. (2018b) and Pouteau et al. (2022a); critical Bonnor-Ebert sphere relation at median T_dust = 23 K
- 2026MNRAS.550g1193B: Constant-density circumburst medium (n_0), z = 1.216, flat LambdaCDM cosmology (H_0 = 70 km s^-1 Mpc^-1, Omega_m = 0.3, Omega_Lambda = 0.7)
- 2018ApJ...862...94L: pressure behind RS equals that at FS; same p; constant microphysical parameters
- 2026ApJ..1004..182H: age 300 Myr, a_disk=50 au, forced eccentricity 0.03
- 2019ApJS..244...40L: Gaussian source morphology with axis ratio 0.2 to 1.0; PHYS simulation assumes 2SFM, Davidzon et al. (2017) SMF, Sargent et al. (2014) MS, van der Wel et al. (…
- 2021ApJ...909..165Z: Cosmology H0 = 67.7 km/s/Mpc, Omega_lambda = 0.69; Chabrier IMF for SFRs
- 2021ApJ...909..165Z: Dust effective opacity tau = 1 at rest 100 um; single beta_em across all redshifts; faint and bright slopes fixed with redshift
- 2021ApJ...909..165Z: AGN and synchrotron contribution negligible at these wavebands and flux ranges
- 2026ApJ...999...47L: Sources are unresolved point sources because the synthesized beam (~13 x 11 kpc at z=3) is well beyond the physical extent of dust emission
- 2026ApJ...999...47L: Cosmic variance calculated using standard assumptions and cookbook from Moster et al. (2011)
- 2026MNRAS.552g1573L: Gaussian measurement-uncertainty distributions
- 2021ApJS..257...43L: Catalog values from Leroy et al. (2019) and EDD represent the true underlying galaxy properties
- 2024ApJ...976..198H: Beam dilution affects Reff but not sigma_v or Mcl
- 2024ApJ...976..198H: Constant CO-to-H2 conversion factor and H2-dominated cloud masses
- 2024MNRAS.533..771R: Errors from fitting emission do not significantly propagate to overlapping absorption fits
- 2023ApJ...954..197I: Dirichlet boundary condition (delta psi = 0) on square of side L; peak-subtracted CLEAN intensities scaled by 1/1.6 to correct ~60% CLEAN boost.
- 2024A&A...683A.141R: 2 Jupiter-mass planet at about 96 au; Lagrangian dust particles entering the planet Hill radius reinjected elsewhere (no circumplanetary emission predicted)
- 2019MNRAS.483.1624B: Tested only beam-size sources, likely overestimating completeness
- 2017ApJ...836..223W: T = 20 K, kappa(1.3 mm) = 2.3 cm2/g, distance 150 pc
- 2019ApJ...881...43K: 10^51 erg per SN, equal wind contribution (50%)
- 2023NatAs...7...80U: Uniform density medium, energy injection E_iso propto t^0.25
- 2021ApJ...906...16S: alpha_ADAF=0.3, beta=0.5 fixed with tight priors
- 2024ApJ...974..279D: For the shell collision, collision time = start of rise (8.2 d), deceleration time = peak (18.1 d)
- 2017ApJ...844..123F: Constant dust temperature, local thermal equilibrium
- 2020ApJ...897...91G: double power-law number counts
- 2024A&A...691A.248L: Salpeter (1955) IMF and cosmology (Omega_M, Omega_Lambda, h) = [0.30, 0.70, 0.70]; factor 1.7 conversion from Chabrier (2003) IMF
- 2024A&A...691A.248L: Observed 1.6 um luminosity relates to stellar mass as M* = C * L_1.6um^alpha
- 2025ApJ...979..142N: Rayleigh-Jeans approximation: alpha = 2 + beta, with power-law dust opacity kappa_nu propto nu^beta
- 2020MNRAS.498.4256C: Dust treated as test particles (no dust self-gravity); one-fluid for a <= 2 mm, two-fluid for a > 2 mm
- 2023A&A...676A..67W: Self-similar thin-shell expansion with R_s = R and v_exp = v_ps = v_s (for radiative gamma = 1); dynamical age equals stellar population age; single dominant e…
- 2024MNRAS.531.4045C: Gas on circular orbits in nuclear ring; flat rotation curve in outer disc; cloud-cloud velocity dispersion sigma_cc = 10 km s^-1; negligible cloud formation be…
- 2024ApJ...971...52M: Cross-correlation responds to peak-peak, not peak-trough, matching
- 2018ApJ...853..160C: Artificial cores have synthesized-beam shape; positions random scaled to 7-m flux profile
- 2019ApJ...871....5T: Gas-to-dust mass ratio 100; CO abundance 1e-4; HCO+ 1e-9; turbulence 120 m/s; LTE
- 2017A&A...608A..98S: Turbulence in steady state, injection balanced by dissipation
- 2019ApJ...881..124M: MASOSA conservative limit assumes 200 km/s width and ~0.7'' beam
- 2020MNRAS.494.5542R: [O I] lines assumed to follow the FIR continuum surface brightness distribution
- 2025A&A...699A.324H: Artificial sources are point sources
- 2025ApJ...987...77J: Largest possible stellar mass m_up = 150 M_sun or 100 M_sun; SFE = 30%; largest probable core mass = m_up / SFE (500 M_sun or 333 M_sun); total core mass in se…
- 2022MNRAS.513.5790C: Stellar mass = 0.9 M_sun, distance = 113.4 pc; flat surface density out to 1 au radius for CPD optical depth estimate
- 2022MNRAS.517..632L: Infinitely thin 2D disc, circular orbits, spherical galaxy mass distribution for tidal radius, completely inelastic equal-mass clump collisions, Kolmogorov tur…
- 2026ApJ..1000..231B: Second forecast assumes the correct model is in the library.
- 2026ApJ..1000..231B: Mean-asymmetry uncertainty scales as sigma/sqrt(N) for independent samples.
- 2020MNRAS.493.5290S: Half of the detected 380 GHz H2O emission originates in the disc; the radio-core magnification represents the H2O disc
- 2020MNRAS.493.5290S: Half of the H2O emission originates in the anomalous feature
- 2015ApJ...806L..25S: literature counts converted to 870 um with modified blackbody beta=1.5, Td=35 K, z=2.5
- 2026A&A...705A.238V: Star at 150 pc in the hydro simulations
- 2023MNRAS.518.6142A: Non-parametric stellar masses from (cite: topping2022)
- 2023MNRAS.518.6142A: SFR_UV / (M_odot yr^-1) = 7.1e-29 * (L_UV / (erg/s/Hz))
- 2024ApJS..275...36F: Intrinsic size 0.15″, circular Gaussian; injected-source redshift z = 2.
- 2025A&A...696A.151C: Group 2 (76% of fields) completeness adopted as the overall reference
- 2021ApJ...916...97Y: Magnetic field and rotational axis are randomly oriented in 3D space, and measured disk radius is not affected by projection
- 2021ApJ...908...19B: Delta chi2 intervals not used for statistical errors because block averaging does not remove noise correlation
- 2024ApJ...977..121N: Velocity caustics dominate the intensity fluctuations in the 2.5 km/s channels
- 2024ApJ...977..121N: Turbulence injection scale in Centaurus may exceed the ~100 pc used for quiescent galaxies; 145.5 pc resolution assumed adequate for this pilot study
- 2026A&A...706A.206H: Type-A and Type-B variations affect non-SMBHB blazars the same way as the SMBHB candidates (stated as untested)
- 2020A&A...634A...9M: Jaffe & Perola isotropic electron distribution; no escape of particles (T_conf = infinity)
- 2025ApJ...984L..57O: Dust-to-gas ratio of 0.02 chosen to match the 1.3 mm flux of Elias 2-24
- 2019Natur.572..211W: Chabrier IMF; T_dust = 36.7 K with 5 K scatter
- 2023A&A...679A.119R: Semi-infinite parallel-plane slab morphology illuminated by external UV radiation, X-ray and CR contributions; Salpeter stellar IMF; mechanical heating due to …
- 2024A&A...687A..35R: SNIa neglected as high-z galaxies are SNII dominated
- 2024A&A...687A..35R: line-of-sight dispersion isotropic; thermal broadening negligible
- 2026A&A...707A.221S: 20% Gaussian uncertainty on core masses
- 2018A&A...620A.152F: ALMA sizes 1.4 times smaller than HST H-band sizes
- 2023MNRAS.519...34H: Mock sources are spatially unresolved Gaussian line profiles; negative detections represent pure noise peaks
- 2025A&A...696A..95G: LBGs span the entire redshift range 3.0<z<3.5
- 2024MNRAS.528L..76R: M_BH scales as D and L scales as D^2
- 2020ApJ...891L..33I: Equal injection power in protons and electrons
- 2019MNRAS.487.4648S: Intrinsic source sizes <0.6'' FWHM
- 2021ApJ...907..122M: Gaussian emission line profiles for completeness simulation
- 2025ApJ...993..111W: Injected lines are CO(4-3), single Gaussian and beam-shaped.
- 2024ApJ...967...56C: inserted cores have the same shape as the synthesized beam (unresolved limit)
- 2021PASJ...73S..35T: Supernova kinetic energy conversion efficiency of 5% (Kruijssen 2012); stellar wind energy conversion efficiency of 20% (Weaver et al. 1977)
- 2025A&A...701A..41D: The total 100-GHz luminosity is used, not only the coronal part, to stay consistent with the Ricci et al. correlation
- 2022A&A...660A..14R: Lambda-CDM cosmology with H_0 = 70 km s^-1 Mpc^-1, Omega_m = 0.3, Omega_Lambda = 0.7; Chabrier (2003) IMF
- 2024A&A...692A..22Z: artificial sources are point-like (conservative choice)
- 2018ApJ...867..153C: Injected sources unresolved and unclustered; blank-field Fujimoto2016 Schechter counts
- 2021A&A...647A.194F: Axi-symmetric rotating disc composed of concentric rings
- 2024A&A...684A.119P: Injected line is a Gaussian with the input FWHM
- 2018ApJ...862...78C: Sources are unresolved point sources
- 2022ApJ...930...32C: UDS and COSMOS S2CLS fields represent cosmic average density
- 2025PASP..137l4501T: Continuum subtraction and weighting skipped; no redshift flux-scaling correction because all mock fluxes equal
- 2017ApJ...843L..35W: Results same if source twice as large
- 2023ApJ...945..121U: ALMA positional uncertainty is negligible compared to Chandra
- 2025ApJ...991L..38U: SMC extinction curve with R_V = 2.74; Case B recombination with initial ne = 100 cm^-3 and Te = 10^4 K; Galactic extinction negligible; Te([O II]) = 0.7 * Te([…
- 2023MNRAS.522.6123Z: Unresolved flux densities at <= 1.4 GHz emanate only from NW and SE hotspots with flux ratio S_SE : S_NW = 15 : 1; hotspot occupies an elliptical cylinder volu…
- 2026A&A...706A.345K: Cosmology H0=70, Om=0.3, OL=0.7; Chabrier IMF
- 2021MNRAS.503.1174K: Sources are unresolved point sources smaller than the synthesized beam HPBW
- 2021A&A...649A.152K: Gaussian sources, FWHM 0.8 to 1.6 arcsec; position offsets Gaussian with sigma 0.12 arcsec
- 2024ApJ...969...27B: 1.2 mm selection is essentially a cold dust mass selection and effectively a cold molecular gas mass selection.
- 2018ApJ...861....7F: axis ratio 0.75 for model sources
- 2024MNRAS.528.5019H: Source extraction relies on Gaussian noise; negative peaks used as the false-positive proxy
- 2025ApJ...988..172H: Non-evolving CO luminosity function and fully thermalised CO SLED (over-estimates interlopers)
- 2020Natur.584..201R: all observed gas converted into stars for the baryonic (upper-limit) ETG comparison
- 2025A&A...704A.158C: Small number Poisson statistics (Gehrels 1986) for 1-sigma upper limits
- 2020A&A...643A...2B: Fluxes converted to 850 um using z=2.5 main-sequence Bethermin2017 SED template
- 2024ApJ...961..120C: Halo gas mass = 10% of halo mass
- 2026ApJ..1000L..10C: f_cav = 4
- 2026ApJ..1000L..10C: AGN activity time t_AGN = 100 Myr
- 2019ApJ...886...48A: power-law w=A theta^-0.8; Planck 2015 cosmology
- 2021MNRAS.504..172S: Planck XIII cosmology, sigma8=0.816
- 2019PASJ...71L...3F: Instantaneous injection of power-law electrons
- 2018ApJ...856..121G: Chabrier IMF; observed UV not extinction corrected
- 2016MNRAS.462.1989A: Fixed colour ratios S500/S250=1.55, S500/S350=1.12


### Limitations the authors admit
- 2017ApJ...846..108C: CO detection is only ~3 sigma peak SNR so 2D CO kinematics and central detail are limited
- 2017ApJ...846..108C: ALESS67.2 nature inconclusive
- 2023A&A...675A..85M: Nine out of 29 ALMA detections (and all but one of the faint-end contributors) lack reliable multiwavelength counterparts, requiring an assumed Gaussian redshift distribution (z = 2 +/- 0.5) and prev…
- 2023A&A...675A..85M: Some lens models (GLAFIC v4, Sharon v4, Williams v4/v4.1) do not fully cover the PB > 0.3 region (missing 0.7% to 19% of the area), where no magnification (mu = 1) had to be assumed.
- 2023A&A...675A..85M: Systematic discrepancies across different lens models reach up to ~0.6 dex in median differential counts, and for most sources model-to-model magnification discrepancies exceed individual model uncer…
- 2023A&A...675A..85M: The bright end of the number counts (> 1 mJy) is expected to be affected by cosmic variance due to the small survey area, missing massive (> 10^11 M_sun) bright galaxies.
- 2025A&A...695A.204V: Not evaluated for large extended bright emission
- 2025A&A...695A.204V: Validated only with the w-term neglected
- 2025A&A...695A.204V: Computationally intensive for large data sets; bright sources (S/N > 50) must be removed first
- 2024A&A...690A..33L: Gravitational boundedness is only a first-order thermal Bonnor-Ebert check because turbulence, external pressure, and magnetic field support are not currently available for each core.
- 2024A&A...690A..33L: 84 sources potentially contaminated by free-free emission were rejected rather than flux-corrected and retained (though re-introducing massive free-free-corrected cores would not alter the conclusion…
- 2024A&A...690A..33L: Cores are probed at 2700 au spatial resolution, leaving potential sub-fragmentation and multiplicity on scales below 1000 au (down to ~200 au disk scales) unresolved.
- 2021AJ....161..146J: ADI excludes the innermost disk regions.
- 2021AJ....161..146J: Elias 24 lies near residual artifacts and the RDI inner limit; the second epoch is inconclusive.
- 2021AJ....161..146J: Detection probabilities omit possible CPD emission.
- 2021AJ....161..146J: Disk extinction is omitted and may make sensitivity estimates optimistic.
- 2021AJ....161..146J: Direct-imaging mass estimates depend on uncalibrated formation-dependent luminosity relations.
- 2020MNRAS.491.2506D: Simulated training data have unproven assumptions, imperfect physics and a resolution/sample-size trade-off.
- 2020MNRAS.491.2506D: The CAE architecture was not optimized.
- 2020MNRAS.491.2506D: The 96th-percentile clipping level was arbitrary and not optimized.
- 2020MNRAS.491.2506D: The minimum usable S/N was not tested.
- 2020MNRAS.491.2506D: Low-κ selections can contain contaminants in heavily imbalanced samples.
- 2020MNRAS.491.2506D: Classification is sensitive to the proxy used for the centre of potential.
- 2020MNRAS.491.2506D: Position-angle accuracy was not benchmarked against existing dedicated methods.
- 2026A&A...707A..77H: Ionized outflow masses are lower limits due to the electron density floor
- 2026A&A...707A..77H: alpha_CO in outflows is highly uncertain, so energetics are order-of-magnitude estimates
- 2026A&A...707A..77H: Outflow presence in the NW nucleus is uncertain
- 2025A&A...694A.291K: Low Swift-BAT sensitivity limits detected X-ray local maxima
- 2025A&A...694A.291K: Missing VLBA data near C3 ejection limits core-flux/ejection comparison
- 2025A&A...694A.291K: Higher cadence and broadband SED modeling needed to clarify optical/gamma-ray correlation
- 2021ApJ...917...73W: Model NIR spectral index has an upper limit of ~ -0.8 (optically thin alpha ~ -1.0), steeper than the canonical NIR spectral index of -0.65 (or -0.4) observed for bright flares.
- 2021ApJ...917...73W: Variance at 230 GHz on the longest timescales (> 50 minutes) and epoch-to-epoch flux density offsets cannot be reproduced by the single-zone model.
- 2021ApJ...917...73W: The brightest observed NIR states (e.g., Do et al. 2019 flare) are underrepresented in the mock light curves (probability ~ 10^-3).
- 2021ApJ...917...73W: Significance of the submm-NIR cross-correlation delay was not independently tested (e.g., with a Granger causality test).
- 2015ApJ...799...81S: Four possibly lensed SMGs excluded; four SMGs lack redshifts; only one SMG at z>3.5
- 2025ApJ...990L..70L: Orbit fit lacks phase coverage; more epochs needed
- 2025ApJ...990L..70L: Cannot rule out that the H-alpha source differs from the K band source
- 2025ApJ...990L..70L: ALMA non-detection of the compact source may be due to resolving out with a smaller beam
- 2016ApJ...832..187B: SEDs lack points near peak so Tdust, tau, beta cannot be constrained simultaneously
- 2018A&A...618A.120L: Launching-radius inferences rely on a steady-state assumption; ACA data would be needed to rule out an envelope
- 2017MNRAS.468.1769F: Cloud blending in central region makes nuclear mass distribution suspect
- 2022A&A...666A..39M: The observations and residual snapshot images are dynamic-range limited rather than thermal-noise limited, even at 4-second integration times, due to finite fidelity of the mini-spiral model and subo…
- 2022A&A...666A..39M: The statistical false-positive calculation assumes a Gaussian noise distribution, which does not strictly hold because the snapshot residuals are dynamic-range limited and non-Gaussian.
- 2022A&A...666A..39M: Primary-beam attenuation is not corrected during the search, which reduces sensitivity toward the edges of the field of view.
- 2022A&A...666A..39M: Data taken at low antenna elevations (< 25 degrees) suffer severe atmospheric opacity and turbulence, causing high rms and quality loss.
- 2023MNRAS.522...56V: Dual-polarization mode (XX, YY) prevents recovery of Stokes V (circular polarization) and is insufficient to obtain full linear polarization without additional calibration.
- 2023MNRAS.522...56V: Poor weather conditions on 2017 December 29 and during epoch 4 degraded the sensitivity to 0.18-0.31 mJy beam^-1, worse than early theoretical predictions (~10-100 uJy).
- 2023MNRAS.522...56V: Systematic effects from a changing synthesized beam in time-sliced imaging limit the study of minor variability (VF <= 2) and noise widens the VF distribution envelope up to VF ~ 3-4 (1-h) and VF ~ 5…
- 2023MNRAS.522...56V: Visual inspection for faint sources introduces a selection bias toward regions with lower background noise.
- 2026MNRAS.548ag325W: SiO J=5-4 Epoch 2 cube is truncated at +2000 km s^-1 on the receding side due to insufficient spectral bandwidth.
- 2026MNRAS.548ag325W: High-velocity molecular emission in the ALMA cubes may be buried in noise or excluded by the spatial cut-off used to avoid contamination from the equatorial ring.
- 2026MNRAS.548ag325W: Explosion energy and energy deposition timescale are free parameters in the approximate ray-by-ray neutrino transport scheme, and 56Ni yields have uncertainties due to the electron fraction Ye.
- 2026MNRAS.548ag325W: Simulations do not include self-consistent chemical networks for molecule formation/destruction or dust condensation, relying instead on local elemental stoichiometry (C+O first, then Si+O).
- 2026MNRAS.548ag325W: Converting observed line intensities into fractional masses assumes optical thinness, LTE, and uniform temperature across the ejecta without full radiative transfer.
- 2026MNRAS.548ag325W: Progenitor and explosion models do not include initial stellar rotation or magnetic fields.
- 2018ApJ...863..193V: The cavity is poorly defined and may not be real
- 2018ApJ...863..193V: HST images manually aligned, so small-scale offsets between gas and UV may be missed
- 2026ApJ..1000..141K: The Band 3 and Band 4 observations were separated by ~9 months (October 2016 to July 2017) without simultaneous millimeter monitoring, though a few percent variability would shift T_CMB by < 0.1 K.
- 2026ApJ..1000..141K: The -6 km/s component cannot constrain f_c due to lack of saturation, leaving its T_ex uncertain.
- 2026ApJ..1000..141K: H13CN and H13CO+ transitions have low S/N (~3), limiting their statistical significance.
- 2017MNRAS.464.4624S: Poor temporal sampling limits constraints
- 2014ApJ...796....1T: Missing flux and outflow complicate other lines near systemic velocity; temperatures in hydrodynamics (isothermal 13.5 K) and radiative transfer (power law) are inconsistent.
- 2025MNRAS.541...71M: Inner belt fixed from a pure-silicate run may bias the composition result
- 2025MNRAS.541...71M: Larger than expected flux calibration uncertainty from bad weather
- 2025MNRAS.541...71M: Brightness asymmetry may not be real given calibration and uncertainties
- 2022A&A...659L...1L: Lack of knowledge of nucleus shape and spin parameters (pole orientation and shape) prevents thermophysical modeling.
- 2022A&A...659L...1L: Visibility fitting cannot distinguish between disk sizes smaller than ~40 mas given the ~65 mas resolution and measurement S/N.
- 2022A&A...659L...1L: Diameter and albedo uncertainties are dominated by model input errors, principally the uncertainty on the relative radio emissivity epsilon_r.
- 2022A&A...659L...1L: The assumed CO production rate of 4e28 mol s^-1 used in the dust velocity calculation is somewhat arbitrary.
- 2021MNRAS.502.5390P: Small number of targets in the BPMG (12 stars) and small number of spatially resolved discs limit the statistical significance of radius distribution comparisons.
- 2021MNRAS.502.5390P: HD 173167 and several stars in the 45 Myr and 150 Myr moving groups lack far-infrared photometry beyond 22 um (or only have IRAS upper limits), preventing firm conclusions on cold disc presence for t…
- 2021MNRAS.502.5390P: High ALMA upper limits for HD 14082A (<5.8 mJy) and HD 29391 (<3.5 mJy) due to the 14" phase-center offset (46% primary beam response) for HD 14082A and the small 0.2" beam for HD 29391.
- 2021MNRAS.502.5390P: Visual inspection of CO J=3-2 in HD 181327 yielded a non-detection, and a full gas analysis optimising detection across excitation conditions was not performed.
- 2021MNRAS.502.5390P: Minimum grain size s_min inferred for HD 15115 may be influenced by how the warm inner component was treated.
- 2021MNRAS.502.5390P: Catastrophic disruption threshold Q_D* varies by an order of magnitude depending on material and velocity-scaling method, leading to large uncertainties in minimum planetesimal sizes and disc masses.
- 2025ApJ...989L..22B: Only one JWST sighting; planet status cannot be confirmed.
- 2025ApJ...989L..22B: S1 orbit cannot be uniquely constrained; modeling links S1 and C1.
- 2025ApJ...989L..22B: Two photometric points leave substantial atmospheric degeneracies.
- 2025ApJ...989L..22B: Ring geometry, shadowing and emitting area are highly unconstrained.
- 2025ApJ...989L..22B: Exozodi sensitivity assumes binary-coplanar, near-edge-on disks and a tailored recovery method.
- 2025ApJ...989L..22B: JWST observations are insensitive to a possible exozodi interior to ∼0.4 au.
- 2025ApJ...989L..22B: June 1 ALMA phase tracking leaves the absolute image frame uncertain.
- 2025ApJ...989L..22B: Phase-calibrator absolute-position uncertainty limits absolute astrometry.
- 2025ApJ...989L..22B: February Roll 2 and April Roll 1 are lower quality because of centering offsets.
- 2024A&A...691A..70N: Expansion velocity is a lower limit because of projection effects
- 2024A&A...691A..70N: Three-dimensional geometry unknown; effects of clustered SNe not well understood; comprehensive kinematic analysis left to future work
- 2020A&A...633A.115K: Second ALMA epoch needed to confirm via proper motion
- 2020ApJS..251...14H: Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2
- 2019A&A...623A.111H: Limited wavelength coverage and angular resolution prevent distinguishing models
- 2024A&A...691A..57M: Parameter space degenerate; no ALMA simulator applied; pulsations missing
- 2023PASJ...75..311K: Weak-lensing mass errors are very large due to the limited number of background galaxies
- 2023PASJ...75..311K: Redshift of HSC J0947-0119 is photometric
- 2019ESC.....3.2088S: N159W-S ALMA analysis is preliminary, so no physical parameters given
- 2015ApJ...811L..19W: Disk brightness vs separation unreliable owing to residual PSF features; sliver at only 3.1 sigma and may arise from KLIP self-subtraction
- 2018MNRAS.481.1976Z: Fluxes depend critically on the assumed model size taken from optical images
- 2018MNRAS.481.1976Z: Source size cannot be constrained from individual sources because of low S/N
- 2018MNRAS.481.1976Z: Observed in a more extended configuration than requested, giving 5-10 times higher flux errors
- 2020MNRAS.495.3409S: multiplicity is a lower limit because the sample is very incomplete near 1 mJy
- 2020MNRAS.495.3409S: observational constraints on projected versus associated companions are weak
- 2020MNRAS.495.3409S: simulation-based line-of-sight correction assumes no clustering
- 2025PASJ...77.1163H: Simulated mock data do not necessarily reproduce real observation properties
- 2025PASJ...77.1163H: clumpfind cannot identify low-S/N clumps so a Gaussianity fit test was not done
- 2025PASJ...77.1163H: Observational constraints at high z are limited, so the LF shape is assumed
- 2025PASJ...77.1163H: Overdensities of clumps were found in replaced data after QA3, so instrumental effects remain possible
- 2026ApJ...997..155M: Core mass uncertainties are ~50%, largely from gas-to-dust mass ratio and dust opacity.
- 2026ApJ...997..155M: Reference protostellar lifetime (0.2 Myr) has an uncertainty of about a factor of two, and the statistical lifetime analysis assumes a constant star formation rate within each clump.
- 2026ApJ...997..155M: Limited sample size at the high-mass end causes the best-fit power-law index to depend slightly on the CMF representation and restricts discussion of later evolution from top-heavy CMF back to Salpet…
- 2026ApJ...997..155M: Virial analysis ignores external pressure and magnetic fields.
- 2021ApJ...923..121Y: SpM image suffers from artificial positive emissions in off-source areas due to non-negative constraints and thermal/systematic noise.
- 2021ApJ...923..121Y: T Tau Sa and Sb disk sizes (6x4 au and 7x3 au) are only slightly larger than the SpM effective resolution (5x4 au), so they are not sufficiently resolved and represent conservative upper limits.
- 2021ApJ...923..121Y: The T Tau N disk is optically thick at 1.3 mm, so the brightness temperature traces the disk atmosphere rather than the midplane, making derived dust surface densities and dust masses lower limits.
- 2021ApJ...923..121Y: There is no quantitative metric to distinguish the SpM image from the CLEAN model in reduced chi-squared, and potential bias in the SpM image remains an open question, requiring future ALMA observati…
- 2022A&A...663A..61P: At ~150 pc resolution, the lowest SFR pixels may not form enough stars to fully sample the IMF, making measured SFRs more uncertain in that regime.
- 2022A&A...663A..61P: Spiral arm masks from Querejeta et al. (2021) were identified partially using CO emission, which may introduce selection bias toward higher gas and SFR at fixed Sigma_*.
- 2022A&A...663A..61P: Fixing a single normalization C_norm across all environments means vertical normalization offsets between environments can be absorbed into the derived slopes C_* and C_mol.
- 2022A&A...663A..61P: Assuming a constant CO(2-1)-to-CO(1-0) ratio R_21 = 0.65 ignores central enhancements in R_21 (~0.18 dex), which can depress the measured C_mol slope by up to ~0.15.
- 2022A&A...663A..61P: Covariance between C_* and C_mol is partially an artifact of the fitting procedure and sample size.
- 2022A&A...663A..61P: Only 8 galaxies meet the criteria for single-galaxy multi-environment correlation analysis, which is too small to establish causal relations for third parameters.
- 2024A&A...687A.293Q: HI maps have coarse resolution (10-60 arcsec), so atomic-gas results are only at kpc scales
- 2024A&A...687A.293Q: Sample limited to galaxies with long continuous spiral segments, mostly grand-design

### Settings cards flag as needed but not stated
- casa version: 9
- casa version used for calibration and imaging: 3
- self-calibration solution intervals: 3
- image size and cell size: 3
- flux calibrator and flux scale uncertainty: 2
- casa version and pipeline version: 2
- line-free channel ranges for continuum subtraction: 2
- flux scale uncertainty: 2
- line-free channels used for continuum: 2
- casa version and alma pipeline version: 2
- exact line-free channels used for continuum maps: 2
- clean threshold, iterations and any robust/taper values for band 7 and band 3 imaging: 1
- calibration details for band 7 (pipeline/manual, casa version): 1
- line-free channels and continuum subtraction for co cube; frequency width of averaged co map: 1
- sinfoni reduced cubes (custom routines not released): 1
- mcmc priors, walkers and chain length for the rotating disk fit: 1
- uvmodelfit starting parameters: 1
- inclination value used for dynamical mass beyond <sin^2 i>=2/3 and exact r_e conversions: 1
- photometric flux calibration uncertainty of alma data: 1
- calibration details (pipeline vs manual, calibrators, self-calibration): 1
- exact continuum bandwidth and spectral window configuration: 1
- alma array configurations and baseline lengths for the observations: 1
- dbscan clustering hyperparameters (e.g., eps and min_samples) used for pixel grouping in source ext…: 1
- method used to generate the 300 simulated noise maps for spurious fraction estimation: 1
- exact fitting algorithm/sampler used to fit the double power-law function to the differential numbe…: 1
- exact line-free channel ranges excluded before uvcontsub for each of the three sources: 1
- tclean parameters other than natural weighting: cell size, image size, deconvolver, niter, threshol…: 1
- optical/jwst centre coordinates used for the 0.6 arcsec mask for glass-z10 and s5-z17-1 (only a tab…: 1
- random seeds used for the 50 jackknife realizations: 1
- full findclump/interferopy parameter settings beyond width range, s/n cut and duplicate-cropping ra…: 1
- how the peak pdfs are binned in s/n and how the l_fd integral and its uncertainty are computed: 1
- whether any bright sources were removed from the visibilities before jackknifing (s/n>50 advice): 1
- flux calibrators and whether the archive calms calibration was used unchanged for each project: 1
- casa version, calibration details, self-calibration parameters, and tclean imaging parameters (defe…: 1
- exact configuration parameters and user-defined spatial scale ranges passed to getsf and gext2d dur…: 1
- software or tool used to convolve the native continuum maps to the 2700 au spatial resolution: 1
- exact dsharp image filenames/releases and the mapping between targets, images and the ten acknowled…: 1
- naco observing-program identifiers and raw/calibration exposure identifiers.: 1
- ipag-adi version, bad-pixel and sky-removal settings, and numerical frame-rejection thresholds.: 1
- complete loci/sadi/radi settings beyond the stated fwhm and separation criterion; exact pca configu…: 1

## Paper excerpts (40 of 208, chosen for detail and spread over fields/years)

### 2017ApJ...846..108C: A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1 (2017; high_z_galaxies; observational_alma_primary)
- question: How do the sizes, spatial distributions and kinematics of dust, CO gas, H II regions and stars compare in the z=2.12 SMG ALESS67.1, and what does this imply for alpha_CO, IRX-beta and the Schmidt-Kennicutt relation?
- step 2: Extract CO(3-2) spectrum and line properties
  - method: Iterative procedure: weight-averaged map over best-guess width, curve-of-growth aperture, clean to 2 sigma, Gaussian fit, update FWHM until convergence [3.2 ALMA 12CO J=3–2: "Next the extracted spectrum is fitted with a Gaussian profile and the frequency width used for obtaining the averaged map is updated to be the FWHM of the spectral fit."]
  - software: CASA
  - parameter: line flux contained within 2'' circular radius [3.2 ALMA 12CO J=3–2: "all the line flux is contained within a circular radius of 2$''$"]
  - fitting: Gaussian fit; errors from fit and Monte Carlo injection of model profiles in random cube regions [3.2 ALMA 12CO J=3–2: "We create fake spectra by injecting model profile into spectra extracted from randomly selected regions of the data cube"]
  - validation: Fit errors consistent with Monte Carlo errors [3.2 ALMA 12CO J=3–2: "The errors are estimates from the fit, and they are consistent with the errors derived from a Monte Carlo simulation."]
- step 4: Measure CO half-light size
  - method: imfit on averaged map with bias correction from 36000 injected models, plus uv-plane chi-square Gaussian fit; uv-based result adopted [3.2 ALMA 12CO J=3–2: "We therefore adopt the *uv*-based measurement for the $^{12}$CO size."]
  - software: imfit
  - parameter: 36000 injected models, peak SNR 1-10, radius up to 2'' [3.2 ALMA 12CO J=3–2: "In total we inject 36000 models with the peak SNR, major axis, minor axis, and positional angle all randomized"]
  - fitting: chi-square Gaussian fit to averaged visibilities vs uv distance [3.2 ALMA 12CO J=3–2: "perform $\chi^2$ fitting assuming a Gaussian profile"]
  - validation: Image-plane and uv results agree; injection tests for bias (3%) and scatter (20%) [3.2 ALMA 12CO J=3–2: "We find a 3% upward bias in median (0.028$\pm$0.007) and a 20% scatter."]
- result: CO(3-2) redshift = 2.1196 ± 0.0009 dimensionless [3.2 ALMA 12CO J=3–2: "$z=2.1196\pm0.0009$"]
- result: CO(3-2) line flux = 4.2 ± 1.2 Jy km/s [3.2 ALMA 12CO J=3–2: "we derive a total line flux of 4.2$\pm$1.2 Jy km s$^{-1}$"]
- result: CO(3-2) line FWHM = 862 ± 195 km/s [3.2 ALMA 12CO J=3–2: "with a velocity FWHM of 862$\pm$195 km s$^{-1}$"]
- result: CO(3-2) half-light radius = 6.5 ± 0.9 kpc [3.2 ALMA 12CO J=3–2: "$r_{1/2,{\rm CO}}=6.5\pm0.9$ kpc"]
- result: Dust to CO size ratio = 5.2 ± 0.8 dimensionless [4.3 Sizes and morphology: "factor of 5.2$\pm$0.8 difference in half-light radius"]
- limitation (authors): CO detection is only ~3 sigma peak SNR so 2D CO kinematics and central detail are limited [4.1 Kinematics – CO and Halpha: "Our $^{12}$CO(J=3-2) detection does not have high enough SNR to produce 2D kinematic maps like H$\alpha$"]
- limitation (authors): ALESS67.2 nature inconclusive [3.1 ALMA 870 μm continuum: "so the nature of ALESS67.2 remains inconclusive"]
- not stated (card): CLEAN threshold, iterations and any robust/taper values for Band 7 and Band 3 imaging; Calibration details for Band 7 (pipeline/manual, CASA version); Line-free channels and continuum subtraction for CO cube; frequency width of averaged CO map; SINFONI reduced cubes (custom routines not released); MCMC priors, walkers and chain length for the rotating disk fit; uvmodelfit starting parameters; Inc…

### 2023A&A...675A..85M: The ALMA Frontier Fields Survey. VI. Lensing-corrected 1.1 mm number counts in Abell 2744, MACSJ0416.1-2403, MACSJ1149.5+2223, Abell 370, and Abell S1063 (2023; high_z_galaxies, galaxy_clusters_and_sz, cosmology; observational_alma_primary)
- question: Derive lensing-corrected 1.1 mm number counts down to flux densities fainter than 0.1 mJy towards five Hubble Frontier Fields galaxy clusters and determine their contribution to the extragalactic background light (EBL).
- step 2: Measure integrated flux densities and sizes of detected sources
  - method: For high-significance (S/N >= 5) sources, fit elliptical Gaussians in the uv-plane using UVMCMCFIT. For low-significance (4.5 <= S/N < 5) sources, scale peak intensities using median size parameters from high-S/N sources and source injecti… [Observations with ALMA: "We measure integrated flux densities in the *uv*-plane for our new high-significance detections as in Paper I, using the UVMCMCFIT python algorithm (cite: Bussmann2016)."] [Observations with ALMA: "As in Paper IV, we estimate the integrated flux densities of low-significance detections in A370 and AS1063 using source peak intensities; this choice is motivated by the large uncertainties in integrated source flux densities that are given at low S/N by two-dimensional Gaussian fits in the $uv$-plane."]
  - software: UVMCMCFIT
  - parameter: Peak-to-integrated flux ratios of 0.80 (A370) and 0.71 (AS1063) for 4.5 <= S/N < 5 sources [Observations with ALMA: "We conduct source injection simulations (see $\S$[3](#sect_method)), finding a typical ratio between the peak and integrated flux density for these size parameters of 0.80 and 0.71 in A370 and AS1063, respectively."]
  - assumption: Low-significance detections have observed effective radius r_eff,obs = 0.23'' and axial ratio q_obs = 0.58 (median of high-S/N sources) [Observations with ALMA: "We adopt as their observed effective radius and axial ratio the median values found for the high-significance sources. Including the five FFs, these are $r_{\textmd{eff,obs}}=0.23\ensuremath{''}$ and $q_{\textmd{obs}}=0.58$, respectively."]
  - fitting: Two-dimensional Gaussian fits in the uv-plane with UVMCMCFIT [Observations with ALMA: "We measure integrated flux densities in the *uv*-plane for our new high-significance detections as in Paper I, using the UVMCMCFIT python algorithm (cite: Bussmann2016)."]
  - validation: Tested sensitivity to assumed source sizes for low-S/N sources using point source and r_eff,obs = 0.5'' extreme cases [Comparison to previous works: "Since we have assumed a given image-plane source size for low-significance detections (11/29 of our sample), we explore the effect of varying this source size by testing two extreme cases."]
- step 4: Estimate image-plane completeness, flux deboosting, and spurious source fractions
  - method: Perform image-plane source injection simulations to derive completeness as a function of flux and size, and flux deboosting as a function of S/N. Extract sources from 300 simulated noise maps per cluster to determine spurious fraction p_fa… [Methodology: "We use source injection simulations, in the image-plane, to estimate the completeness and deboosting corrections (see Paper IV $\S$3.1 for details)."] [Methodology: "We compute the fraction of spurious sources as a function of S/N for each galaxy cluster, $p_{\textmd{false}}$, as the average ratio between the number of detections over a peak S/N in a set of 300 simulated noise maps and in the actual ALMA mosaic (see Paper IV and Paper IV Corrigendum)."]
  - parameter: 300 simulated noise maps per cluster; 10^4 simulated SIDES point sources for Eddington bias check [Methodology: "We compute the fraction of spurious sources as a function of S/N for each galaxy cluster, $p_{\textmd{false}}$, as the average ratio between the number of detections over a peak S/N in a set of 300 simulated noise maps and in the actual ALMA mosaic (see Paper IV and Paper IV Corrigendum)."] [Methodology: "We create sets of $10^4$ simulated point sources that follow the SIDES galaxy formation model (cite: Bethermin2017) distributions of both redshift and $1.1\,\textmd{mm}$ flux density, lens these sources using the “best” CATS v4 model for each cluster, inject and extract them in our ALMA mosaics down to $\textmd{S/N}=4…"]
  - assumption: Skip separate Eddington bias corrections since SIDES simulation flux enhancements match deboosting corrections [Methodology: "These ratios are consistent with the deboosting corrections obtained in Fig. [3](#fig_debcorr). We thus consider safe to skip Eddington bias corrections in this work."]
  - validation: Compared simulated noise map spurious counts with negative mosaic detections and unassociated source counts [Methodology: "Based on the source extraction on the simulated noise maps, the average number of spurious sources at $\textmd{S/N}\geq4.5$ is $0.93\pm1.33$ for A370 and $1.45\pm1.79$ for AS1063. This is consistent within $1\sigma$ with both the amount of spurious sources from the negative mosaics (zero and one, respectively) and the…"]
- step 6: Derive lensing-corrected differential and cumulative number counts via Monte Carlo simulations
  - method: Run 1000 Monte Carlo realizations per lens model per cluster drawing observed fluxes, peak intensities, redshifts, and lens mass reconstructions, computing demagnified fluxes and summing weights X_i = (1 - p_false,i) / (C_i * A_eff,i). Com… [Methodology: "We run 1000 realizations of the number counts per lens model per cluster field."] [Methodology: "X_i=\frac{1-p_{\textmd{false},i}}{C_i\,A_{\textmd{eff},i}}."]
  - parameter: 1000 realizations per lens model per cluster field [Methodology: "We run 1000 realizations of the number counts per lens model per cluster field."]
  - assumption: Modified black body with beta = 1.5, T_dust = 35 K, z = 2.5 when scaling literature counts from 850 um, 1.2 mm, and 1.3 mm to 1.1 mm [Comparison to previous works: "Since we include in our comparison counts derived at wavelengths other than $1.1\,\textmd{mm}$, we scale their estimates as $S_{1.1\,\textmd{mm}}=1.59\times S_{1.3\,\textmd{mm}}$, $S_{1.1\,\textmd{mm}}=1.27\times S_{1.2\,\textmd{mm}}$, and $S_{1.1\,\textmd{mm}}=0.51\times S_{850\,\mu\textmd{m}}$. These factors are obt…"]
  - fitting: Monte Carlo sampling with Gaussian priors on fluxes and spectroscopic/photometric priors on redshift [Methodology: "Simulated catalogs have, for each source $i$, integrated flux densities $S_{\textmd{obs},i}$ and peak intensities $S_{\textmd{obs,peak},i}$ drawn from Gaussian distributions centered in the measured values (see Table [\[tab_snr45gals\]](#tab_snr45gals)), and redshifts $z_i$ drawn from the values/distributions selected…"]
  - validation: Compared against Paper IV counts and evaluated cosmic variance via three methods (empirical field-to-field variance, Driver & Robotham 2010 Eq. 4, and Cosmic Variance Calculator v1.03) [Cosmic variance: "We obtain $1\sigma$ cosmic variance estimates using three different approaches."] [Cosmic variance: "Finally, we obtain another estimate using the Cosmic Variance Calculator v1.03[^6] by (cite: Trenti2008), where cosmic variance is computed via the two point correlation function in extended Press-Schechter theory."]
- step 7: Compute resolved and extrapolated Extragalactic Background Light (EBL) at 1.1 mm
  - method: Sum the integrated flux contribution across differential count bins in each Monte Carlo realization, and fit a double power-law function to non-zero bins of each realization to integrate down to S_lim = 0, 0.013, and 0.133 mJy. [Extragalactic background light: "Using the Monte Carlo realizations of our differential number counts, we compute the contribution to the extragalactic background light (EBL) provided by each of them, by adding up the contribution contained in each flux bin."] [Extragalactic background light: "In order to estimate the EBL derived from our counts at $1.1\,\textmd{mm}$ for any flux density limit, we fit a double power-law function (e.g., (cite: Scott2002)) to our differential number counts."]
  - parameter: Parameter bounds: N_0 = 10^3 - 10^6 mJy deg^-2, S_0 = 0.01 - 1 mJy, alpha = 0 - 5, beta = -1 to 1 [Extragalactic background light: "We consider the ranges $N_0=10^3-10^6\,\textmd{mJy}\,\textmd{deg}^{-2}$, $S_0=0.01-1\,\textmd{mJy}$, $\alpha=0-5$, and $\beta=-1$ to 1."]
  - fitting: Fit logarithmic double power-law function to non-zero flux density bins of each Monte Carlo realization [Extragalactic background light: "We fit Eq. [\[eq_dpl_dndlogs\]](#eq_dpl_dndlogs) to each realization of our differential number counts, including only flux density bins that have non-zero values (thus allowing to extrapolate our counts to flux densities outside the regime covered by our ALMA sources)."]
  - validation: Compared direct summation EBL values with double power-law integrated EBL and Planck/COBE estimates [Extragalactic background light: "We compare our estimates to that by the Planck collaboration (using their best-fit extended halo model, see (cite: Ade2014)) and a recent determination based on COBE/FIRAS and Planck observations (cite: Odegard2019)."]
- result: A370-ID01 uv-fitted integrated flux density at 1.1 mm = 1.925 ± +/- 0.088 mJy [Observations with ALMA: "| A370-ID01$^{a}$ | 02:39:56.57 | $-$01:34:26.40 | 25.1 | $1.624\pm0.065$ | $1.925\pm0.088$ | $0.22\pm0.03$ | 1.06$^{f}$ |"]
- result: A370-ID02 uv-fitted integrated flux density at 1.1 mm = 1.778 ± +/- 0.192 mJy [Observations with ALMA: "| A370-ID02$^{a}$ | 02:39:57.58 | $-$01:34:53.67 | 9.1 | $1.656\pm0.182$ | $1.778\pm0.192$ | $0.10\pm0.05$ | $2.581_{-0.180}^{+0.193}$$^{g}$ |"]
- result: A370-ID03 uv-fitted integrated flux density at 1.1 mm = 1.007 ± +/- 0.205 mJy [Observations with ALMA: "| A370-ID03$^{a}$ | 02:39:58.15 | $-$01:34:24.52 | 7.0 | $0.655\pm0.094$ | $1.007\pm0.205$ | $0.42\pm0.13$ | $1.258$$^{h}$ |"]
- result: AS1063-ID01 uv-fitted integrated flux density at 1.1 mm = 6.806 ± +/- 0.119 mJy [Observations with ALMA: "| AS1063-ID01$^{a}$ | 22:48:49.06 | $-$44:32:25.39 | 89.3 | $6.295\pm0.071$ | $6.806\pm0.119$ | $0.14\pm0.01$ | $2.511_{-0.113}^{+0.111}$$^{g}$ |"]
- result: AS1063-ID02 uv-fitted integrated flux density at 1.1 mm = 1.273 ± +/- 0.142 mJy [Observations with ALMA: "| AS1063-ID02$^{a}$ | 22:48:47.29 | $-$44:30:48.06 | 10.9 | $1.282\pm0.118$ | $1.273\pm0.142$ | $0.10\pm0.05$ | 1.438$^{f}$ |"]
- result: AS1063-ID03 uv-fitted integrated flux density at 1.1 mm = 1.396 ± +/- 0.399 mJy [Observations with ALMA: "| AS1063-ID03$^{a}$ | 22:48:46.58 | $-$44:30:46.83 | 5.2 | $0.648\pm0.124$ | $1.396\pm0.399$ | $0.45\pm0.14$ | $1.468_{-0.063}^{+0.065}$$^{g}$ |"]
- result: Combined cumulative number counts N(>S) at S > 0.013 mJy = 7.026e4 ± +19.59e4/-5.263e4 (MC), +5.528e4/-3.350e4 (Poisson) deg^-2 [Number counts for each Frontier Fields …: "| Combined | 0.024 | $0.000_{-0.000}^{+0.000}$ | $0.0_{-0.0}^{+0.0}\,_{-0.0}^{+1.8}$ | 0.013 | $(7.026_{-5.263}^{+19.59}\,_{-3.350}^{+5.528})\times10^4$ | $4.0_{-1.0}^{+4.0}\,_{-1.9}^{+3.1}$ |"]
- result: Combined cumulative number counts N(>S) at S > 0.042 mJy = 5.486e4 ± +15.01e4/-3.883e4 (MC), +4.316e4/-2.616e4 (Poisson) deg^-2 [Number counts for each Frontier Fields …: "| | 0.075 | $<1.013\times10^6$ | \<3.0 | 0.042 | $(5.486_{-3.883}^{+15.01}\,_{-2.616}^{+4.316})\times10^4$ | $4.0_{-1.0}^{+4.0}\,_{-1.9}^{+3.1}$ |"]
- result: Combined cumulative number counts N(>S) at S > 0.133 mJy = 1.740e4 ± +2.579e4/-1.089e4 (MC), +1.685e4/-0.944e4 (Poisson) deg^-2 [Number counts for each Frontier Fields …: "| | 0.237 | $(2.416_{-2.416}^{+5.012}\,_{-1.995}^{+5.529})\times10^4$ | $1.0_{-1.0}^{+2.0}\,_{-0.8}^{+2.3}$ | 0.133 | $(1.740_{-1.089}^{+2.579}\,_{-0.944}^{+1.685})\times10^4$ | $3.0_{-1.0}^{+4.0}\,_{-1.6}^{+2.9}$ |"]
- result: Combined cumulative number counts N(>S) at S > 0.422 mJy = 5.470e3 ± +4.068e3/-3.800e3 (MC), +7.180e3/-3.523e3 (Poisson) deg^-2 [Number counts for each Frontier Fields …: "| | 0.750 | $(7.929_{-4.688}^{+9.890}\,_{-5.106}^{+10.41})\times10^3$ | $2.0_{-1.0}^{+1.0}\,_{-1.3}^{+2.6}$ | 0.422 | $(5.470_{-3.800}^{+4.068}\,_{-3.523}^{+7.180})\times10^3$ | $2.0_{-1.0}^{+1.0}\,_{-1.3}^{+2.6}$ |"]
- result: Combined differential number counts dN/dlog(S) at S = 0.237 mJy = 2.416e4 ± +5.012e4/-2.416e4 (MC), +5.529e4/-1.995e4 (Poisson) deg^-2 [Number counts for each Frontier Fields …: "| | 0.237 | $(2.416_{-2.416}^{+5.012}\,_{-1.995}^{+5.529})\times10^4$ | $1.0_{-1.0}^{+2.0}\,_{-0.8}^{+2.3}$ | 0.133 | $(1.740_{-1.089}^{+2.579}\,_{-0.944}^{+1.685})\times10^4$ | $3.0_{-1.0}^{+4.0}\,_{-1.6}^{+2.9}$ |"]
- result: Combined differential number counts dN/dlog(S) at S = 0.750 mJy = 7.929e3 ± +9.890e3/-4.688e3 (MC), +10.41e3/-5.106e3 (Poisson) deg^-2 [Number counts for each Frontier Fields …: "| | 0.750 | $(7.929_{-4.688}^{+9.890}\,_{-5.106}^{+10.41})\times10^3$ | $2.0_{-1.0}^{+1.0}\,_{-1.3}^{+2.6}$ | 0.422 | $(5.470_{-3.800}^{+4.068}\,_{-3.523}^{+7.180})\times10^3$ | $2.0_{-1.0}^{+1.0}\,_{-1.3}^{+2.6}$ |"]
- result: Empirical field-to-field cosmic variance down to 0.013 mJy = 17 ± not stated % [Cosmic variance: "First, we derive the field-to-field variance directly from our cumulative counts, computing the variance from the median counts per cluster field down to $0.013\,\textmd{mJy}$. Dividing its square root by the number of clusters and the corresponding median combined counts, we obtain a relative uncertainty of 17%."]
- result: Resolved EBL contribution at 1.1 mm down to 0.013 mJy (direct summation) = 14.3 ± +12.2/-7.4 Jy deg^-2 [Extragalactic background light: "We find a median contribution of $14.3_{-7.4}^{+12.2}$ ($7.5_{-3.9}^{+6.4}$) $\textmd{Jy}\,\textmd{deg}^{-2}$ resolved in our demagnified sources at $1.1\,\textmd{mm}$ down to $0.013$ ($0.133$) $\textmd{mJy}$; here, uncertainties are computed from the 16th and 84th percentiles."]
- result: Resolved EBL contribution at 1.1 mm down to 0.133 mJy (direct summation) = 7.5 ± +6.4/-3.9 Jy deg^-2 [Extragalactic background light: "We find a median contribution of $14.3_{-7.4}^{+12.2}$ ($7.5_{-3.9}^{+6.4}$) $\textmd{Jy}\,\textmd{deg}^{-2}$ resolved in our demagnified sources at $1.1\,\textmd{mm}$ down to $0.013$ ($0.133$) $\textmd{mJy}$; here, uncertainties are computed from the 16th and 84th percentiles."]
- result: Double power-law fit parameter S_0 (turnover flux density) = 3.6e-2 ± +2.5e-2/-2.3e-2 mJy [Extragalactic background light: "From these fits, we find median parameters and associated uncertainties (from 16th and 84th percentiles) of $N_0=2.7_{-1.7}^{+5.0}\times10^5\,\textmd{mJy}\,\textmd{deg}^{-2}$, $S_0=3.6_{-2.3}^{+2.5}\times10^{-2}\,\textmd{mJy}$, $\alpha=2.8_{-0.8}^{+1.0}$, and $\beta=0.6_{-1.6}^{+0.4}$."]
- result: Total extrapolated EBL at 1.1 mm (double power-law fit integrated down to S_lim = 0 mJy) = 21.2 ± +40.4/-9.6 Jy deg^-2 [Extragalactic background light: "Using Eq. [\[eq_dpl_ebl\]](#eq_dpl_ebl) with the parameters found for each realization and $S_{\textmd{lim}}=0\,\textmd{mJy}$, we estimate a median total EBL associated with $1.1\,\textmd{mm}$ galaxies in the FFs of $21.2_{-9.6}^{+40.4}\,\textmd{Jy}\,\textmd{deg}^{-2}$."]
- limitation (authors): Nine out of 29 ALMA detections (and all but one of the faint-end contributors) lack reliable multiwavelength counterparts, requiring an assumed Gaussian redshift distribution (z = 2 +/- 0.5) and preventing detailed physical comparison with… [Source redshifts: "Nine detections have no reliable counterparts in the aforementioned catalogs. As in Paper IV, for these sources we assume a Gaussian redshift distribution centered at $z=2$ with $\sigma=0.5$, which is consistent within $1\sigma$ with average redshift values found for faint dusty galaxies from the literature (e.g. (cit…"]
- limitation (authors): Some lens models (GLAFIC v4, Sharon v4, Williams v4/v4.1) do not fully cover the PB > 0.3 region (missing 0.7% to 19% of the area), where no magnification (mu = 1) had to be assumed. [Lensing models: "A fraction of the region where the ALMA maps have $\textmd{PB}>0.3$ is not fully covered by the models GLAFIC v4 ($\sim2\%$ and $3\%$ for A2744 and AS1063, respectively), Sharon v4 ($\sim0.7\%$ for A370), Williams v4 ($\sim3\%$, $19\%$, $10\%$ and $14\%$ for A2744, MACSJ0416, MACSJ1149 and A370, respectively) and Will…"]
- limitation (authors): Systematic discrepancies across different lens models reach up to ~0.6 dex in median differential counts, and for most sources model-to-model magnification discrepancies exceed individual model uncertainties. [Methodology: "For most sources, the discrepancies in the median values predicted by different models exceed their individual uncertainties, as Fig. [5](#fig_magnif_gal) shows."]
- not stated (card): CASA version used for calibration and imaging; Calibration details (pipeline vs manual, calibrators, self-calibration); Exact continuum bandwidth and spectral window configuration; ALMA array configurations and baseline lengths for the observations; DBSCAN clustering hyperparameters (e.g., eps and min_samples) used for pixel grouping in source extraction; Method used to generate the 300 simulated…

### 2025A&A...695A.204V: Quantifying the detection likelihood of faint peaks in interferometric data through jackknifing: Test application on finding z &gt; 10 galaxy candidates (2025; high_z_galaxies, instrumentation; archival_reuse)
- question: How to quantify the detection likelihood of faint line peaks in interferometric data by jackknifing visibilities, tested on tentative [O III] 88 um detections toward three z>10 galaxy candidates
- step 2: Generate jackknife noise realizations
  - method: Randomly flip the sign of half of the visibilities in the visibility plane with different random seeds, then re-image each realization with the same imaging as the real data [3.1 Jackknifing: "by randomly multiplying half of the real and imaginary amplitudes of the visibilities by -1 and then rebinning, thereby averaging out the signal"] [3.1 Jackknifing: "Resampling the noise distributions requires that the cubes are re-imaged at every iteration."]
  - software: jackknify, CASA, tclean
  - parameter: 50 jackknife realizations per observation, ~9 min per iteration on a 2019 MacBook Pro [3.2.2 / 5.1: "from $\approx$ 50 realizations onward we recover the high-$S/N$ tail of the distribution; we decided to use 50 jackknife realizations throughout this work"] [5.1 Specific experiment set up: "takes $\approx 9$ minutes on a 2019 MacBook Pro with a 2.6 GHz 6-Core Intel Core i7 processor."]
  - assumption: Visibility noise is additive, Gaussian, uncorrelated and zero-mean for well-calibrated data [3.1 Jackknifing: "noise in the Fourier domain, unlike in the image plane, is additive and Gaussian"]
  - validation: Mock simobserve data show jackknife realizations match the noise structure and standard deviation of cleaned noise maps for source S/N below ~50 [4 Application to simulated ALMA data: "The simulated noise map and jackknifed realization exhibit the same noise structure, validating our jackknifing approach."] [4 Application to simulated ALMA data: "We find that our jackknifing approach is perfectly reliable for $S/N \lesssim 50$."]
- step 3: Find peaks in real and jackknifed cubes
  - method: Run FindClump (interferopy, SExtractor-based) on the real cube and each jackknifed cube, keep positive peaks within 0.6 arcsec of the optical centre, to build P_D and P_FD [5.1 Specific experiment set up: "We use `FindClump` (cite: Walter2016), as implemented in the `interferopy` package (cite: interferopy), to sample the distribution of positive peak values from both the real and jackknifed data."] [5.1 Specific experiment set up: "We mask out features outside a $0.6\ensuremath{''}$ radius of the optically derived center."]
  - software: FindClump, interferopy, SExtractor
  - parameter: line widths 100-500 km/s (3-11 channel widths) [5.1 Specific experiment set up: "we configure `FindClump` to search for emission lines with widths between $100 - 500$ km s$^{-1}$, corresponding to $3-11$ times the channel width."]
  - parameter: peaks above S/N of 0 retained; duplicates merged within 0.2 arcsec and 0.2 GHz [5.1 Specific experiment set up: "With `FindClump`, we identify peaks that exceed a signal-to-noise ratio ($S/N$) of 0"] [5.1 Specific experiment set up: "and within 0.2 GHz spectrally (roughly $4-5$ channels apart)."]
  - parameter: SExtractor analysis and detection thresholds both set to 2 [5.1 Specific experiment set up: "specifically the analysis and detection thresholds which we both set to 2 to better detect low $S/N$ clumps."]
  - validation: On simulated data FindClump on 50 jackknife realizations gave a smooth noise peak distribution and recovered the injected S/N = 4.9 sources [4 Application to simulated ALMA data: "By applying the line-finding algorithm to the real data (orange histogram), we recover the simulated continuum and lines sources, both with a $S/N = 4.9$."]
- step 4: Likelihood ratio test for blind line detection
  - method: Compute false-detection likelihood L_FD(gamma) from jackknifed peak PDF, multiply by number of real peaks for expected noise count, and form Lambda = L_D/L_FD; significant if Lambda >= k = 3 [3.2.2 Line detection inference through …: "Finally, an excess in the ratio is considered significant if the likelihood ratio exceeds a critical value $k$"] [5.1 Specific experiment set up: "We consider a detection to be significant if the excess of peaks in the real data with respect to the noise has at least a significance of $2\sigma$ based on Poisson statistics."]
  - software: jackknify, FindClump
  - parameter: detection threshold gamma = 4 sigma, critical value k = 3 [5.2 Results on blind line searches: "This does not exceed our detection threshold of $k = 3$"]
  - assumption: Jackknifed peaks sample the false-detection distribution; peak distribution is a subset of the pixel-value distribution of a smoothed random Gaussian field [3.2.2 Line detection inference through …: "can be approximated as a smoothed random Gaussian field."]
  - validation: Jackknifed negative-peak PDF compared with the real data; scatter within the 95% interval is consistent with Poisson uncertainty [3.2.2 Line detection inference through …: "the scatter in the jackknife realizations within the 95% confidence interval is consistent with the Poisson uncertainty in the real data for each bin"]
- result: GLASS-z12 expected noise peaks above S/N 4 (L_FD x N_peaks, N_peaks = 1150) = 1.3 ± 1.1 peaks [5.2 Results on blind line searches: "= 0.0011 \times 1150 = 1.3 \pm 1.1"]
- result: GLASS-z12 likelihood ratio Lambda(4 sigma) = 0.80 ± not stated dimensionless [5.2 Results on blind line searches: "which results in $\Lambda(4\sigma) = \mathcal{L}_{\rm D}(4\sigma) / \mathcal{L}_{\rm FD}(4\sigma) = 0.80$"]
- result: GLASS-z12 reported 5.8 sigma peak recovered at lower significance = 2.9 sigma, linewidth 280 km/s ± not stated sigma [5.2 Results on blind line searches: "We recover a peak at the same location but at a lower significance of $2.9\sigma$ for a linewidth of 280 km s$^{-1}$"]
- result: GLASS-z10 expected noise peaks at gamma > 4 sigma (N_peaks = 271) = 1.5 ± 1.2 peaks [5.2 Results on blind line searches: "we expect to find $1.5 \pm 1.2$ peaks at $\gamma > 4\sigma$"]
- result: GLASS-z10 likelihood ratio Lambda(4 sigma) = 1.4 ± not stated dimensionless [5.2 Results on blind line searches: "The likelihood ratio resulted in $\Lambda(\gamma = 4\sigma) = 1.4$."]
- result: GLASS-z10 previously reported 2.7 sigma line: L_FD and Lambda = L_FD = 0.19, Lambda = 0.9 ± not stated dimensionless [5.2 Results on blind line searches: "This line has a false detection likelihood of $\mathcal{L}_{\rm FD}(\gamma=2.7\sigma) = 0.19$ and a likelihood ratio test resulting in $\Lambda(\gamma = 2.7\sigma) = 0.9$."]
- result: S5-z17-1 expected noise peaks above S/N 4 (N_peaks = 221) = 0.7 ± 0.8 peaks [5.2 Results on blind line searches: "= 0.0032 \times 221= 0.7 \pm 0.8"]
- result: S5-z17-1 likelihood ratio Lambda(4 sigma) = 1.4 ± not stated dimensionless [5.2 Results on blind line searches: "since $\Lambda(\gamma=4\sigma) = 1.4$"]
- result: S5-z17-1 reported peak recovered: S/N and Lambda = 3.9 sigma, L_FD = 0.0060, Lambda = 2.2 ± not stated dimensionless [5.2 Results on blind line searches: "This line has a false detection likelihood of $\mathcal{L}_{\rm FD}(\gamma=3.9\sigma) = 0.0060$ and a likelihood ratio test resulting in $\Lambda(\gamma = 3.9\sigma) = 2.2$."]
- result: Simulated data Lambda(gamma = 4.0) = 13 ± not stated dimensionless [4 Application to simulated ALMA data: "the likelihood ratio tests yield $\Lambda(\gamma = 4.0) = 13$."]
- result: Expected spurious line features at S/N ~4-5 in broad ALMA line scans = ~3 ± 2 features [6 Summary & Implications: "we expect to find approximately $3 \pm 2$ line features with $S/N \sim 4-5$ in broad ALMA line scans"]
- limitation (authors): Not evaluated for large extended bright emission [Footnote 6: "We note that we did not evaluate the performance of jackknifing the visibilities in cases of large extended bright emission such as in molecular clouds within low-redshift galaxies."]
- limitation (authors): Validated only with the w-term neglected [Footnote 3: "However, we do note that our tools are validated only on data where the $w$-term was neglected."]
- limitation (authors): Computationally intensive for large data sets; bright sources (S/N > 50) must be removed first [3.1 Jackknifing: "Because of this, `jackknify` can become computationally intensive, particularly for large data sets."]
- not stated (card): Exact line-free channel ranges excluded before uvcontsub for each of the three sources; tclean parameters other than natural weighting: cell size, image size, deconvolver, niter, threshold, mask, channel width per source (only 46 km/s given for GLASS-z12); Optical/JWST centre coordinates used for the 0.6 arcsec mask for GLASS-z10 and S5-z17-1 (only a table, not text); Random seeds used for the 50…

### 2024A&A...690A..33L: ALMA-IMF: XV. Core mass function in the high-mass star formation regime (2024; star_formation, milky_way_ism; large_program_or_survey)
- question: Measure the core mass function (CMF) at a homogeneous physical resolution of 2700 au across 15 Milky Way high-mass protoclusters and test whether its high-mass slope differs from the canonical Salpeter IMF slope (α = 2.35).
- step 6: Determine mass completeness limits per field via synthetic core injection
  - method: Inject synthetic 2D circular Gaussian cores (FWHM = 3840 au) onto the source-subtracted background maps in 10 mass bins across 4 draws (~3800 synthetic cores per field), re-extract with getsf, and find the 90% recovery mass limit. [5.1. Completeness tests: "we injected synthetic cores on top of their background emission (i.e. the emission subtracted from each source). The synthetic cores are injected in the form of 2D circular Gaussian with a FWHM corresponding to 3840 au"] [5.1. Completeness tests: "We then extract the synthetic cores with the _getsf_ method (see Sect. 3.1). To obtain a good statistics in each bin of mass, we repeated this procedure four times per field."]
  - software: getsf
  - parameter: Gaussian FWHM = 3840 au; minimum separation > 2.5"; border exclusion = 5"; 10 flux bins (equivalent to 0.5-5 M_sun at 20 K, or 1-10 M_sun in W51-E); 4 draws per field (~3800 cores total); completeness threshold = 90%. [5.1. Completeness tests: "We inject these synthetic sources randomly, provided the centre of the cores are separated by more than 2.5 [′′] . We forbid the injection of sources within 5 [′′] of the border of the maps"] [5.1. Completeness tests: "The flux of the synthetic sources ranges from equivalent masses of 0.5 to 5 _M_ ⊙ in all fields for gas at 20 K, except in W51-E where we adopted a mass range of 1 to 10 _M_ ⊙ ."]
  - assumption: Synthetic core fluxes converted to mass using the mean temperature of the cores extracted in the corresponding region. [5.1. Completeness tests: "From these fluxes, we compute the mass of the synthetic cores when adopting the mean temperature of the cores extracted in the corresponding region."]
  - validation: Discarded W51-E (completeness limit 3.86 M_sun) and adopted the highest remaining field completeness limit (1.64 M_sun) as the global completeness limit. [5.1. Completeness tests: "We exclude W51-E from the analysis of the global CMF (see Sect. 6.1) and we restrict the core samples to cores exceeding 1.64 _M_ ⊙ to fit the high-mass tail of the CMF."]
- step 7: Fit the high-mass slope of the global CMF and quantify uncertainties and Salpeter tension
  - method: Fit a power-law PDF p(x) ∝ x^-α to the 330 bound cores above x_min = 1.64 M_sun (excluding W51-E) using Maximum Likelihood Estimation (MLE) and the Kolmogorov-Smirnov distance in the powerlaw Python package, propagate uncertainties via 10^… [5.2.1. Method: "We follow the procedure presented by Clauset et al. (2009), and use its implementation in the python package `powerlaw` presented by Alstott et al. (2014)."] [5.2.2. Uncertainty of the fit: "We show the resulting cumulative CMFs generated from 10 [3] trials in Fig. 6. Each draw is fitted via MLE (see Sect. 5.2.1), fixing _x_ min to 1.64 _M_ ⊙ ."]
  - software: powerlaw
  - parameter: x_min = 1.64 M_sun; n = 330 cores; 10^3 Monte Carlo trials with β ~ N(1.5, 0.2), T ~ N(T_core, σ_T), and Gaussian flux errors; 10^5 Salpeter synthetic trials. [5.2.1. Method: "We, therefore, select _x_ min = 1.64 _M_ ⊙, which corresponds to a core sample of 330 elements (excluding W51-E)."] [5.2.2 Uncertainty of the fit: "In our Monte Carlo simulation, the opacity index β can take random normal values with a mean value of 1.5"]
  - assumption: High-mass tail of the CMF follows a power-law distribution p(x) = C x^-α above x_min. [5.2.1. Method: "If we assume that the CMF can be represented by a power-law _p_ ( _x_ ) = _Cx_ [−][α], where _C_ is a constant, there must be some lower mass value, _x_ min, from which the power-law fit is accurate"]
  - fitting: Maximum likelihood estimation (MLE) with Kolmogorov-Smirnov (KS) distance minimization (Clauset et al. 2009) coupled with 10^3 Monte Carlo error propagation. [5.2.1. Method: "The originality of the method by Clauset et al. (2009) is to propose a method to determine the best parameters _x_ min and α using the Kolmogorov-Smirnov (KS) distance."] [5.2.2. Uncertainty of the fit: "We obtain a mean exponent value for the slope of the CMF of 1.97±0.06, where the uncertainty is the quadratic sum of the statistical uncertainty from Eq. 7 (σ ≃ 0.06) and from the uncertainties on the temperature, opacity index, and flux measurement uncertainties (σ ≃ 0.02)."]
  - validation: Verified that the first KS distance minimum occurs at x_min = 1.40 M_sun (α = 2.07 ± 0.06), compatible with x_min = 1.64 M_sun (α = 2.11 ± 0.06 before MC), and that sample size (330 cores) far exceeds the ~40-50 threshold for stable MLE in… [5.2.1. Method: "We note that _x_ min = 1.40 _M_ ⊙ corresponds to α = 2.07 ± 0.06, compatible with the α associated with _x_ min = 1.64 _M_ ⊙ ."] [5.2.1. Method: "Clauset et al. (2009) report stable index values when the sample exceeds ≈50 elements above the completeness limits."]
- result: Global mass completeness limit (excluding W51-E) = 1.64 ± not stated M_sun [abstract: "A power-law fit to the CMF of the sub-sample of cores above the 1.64 _M_ ⊙ completeness limit — 330 cores — through the maximum likelihood estimate technique yields a slope of 1.97 ± 0.06"]
- result: Number of bound cores above the 1.64 M_sun completeness limit (excluding W51-E) = 330 ± not stated dimensionless [5.2.1. Method: "We, therefore, select _x_ min = 1.64 _M_ ⊙, which corresponds to a core sample of 330 elements (excluding W51-E)."]
- result: CMF high-mass power-law slope α (direct MLE fit before Monte Carlo) = 2.11 ± 0.06 dimensionless [5.2.1. Method: "From that subsample, we obtain a power-law index fit α = 2.11 ± 0.06 [8] ."]
- result: CMF high-mass power-law slope α (with Monte Carlo uncertainties) = 1.97 ± 0.06 dimensionless [abstract: "A power-law fit to the CMF of the sub-sample of cores above the 1.64 _M_ ⊙ completeness limit — 330 cores — through the maximum likelihood estimate technique yields a slope of 1.97 ± 0.06, significantly flatter than the 2.35 Salpeter slope."]
- result: Statistical tension with the canonical Salpeter IMF slope (α = 2.35) = 2.4 ± not stated sigma [5.2.3. Comparison with the Salpeter-slo…: "Therefore, we report that the CMF in the protoclusters studied by ALMA-IMF is flatter than, and cannot reasonably be reconciled with the Salpeter-IMF slope to a 2.4σ level [9] ."]
- limitation (authors): Gravitational boundedness is only a first-order thermal Bonnor-Ebert check because turbulence, external pressure, and magnetic field support are not currently available for each core. [4.2.3. Core mass and boundedness: "We note that this is a first-order check of the boundedness of cores. A more accurate determination would require computing the equilibrium of each source taking into account its turbulence, external pressure, and magnetic field support in addition to the thermal support. Unfortunately, we lack all these pieces of inf…"]
- limitation (authors): 84 sources potentially contaminated by free-free emission were rejected rather than flux-corrected and retained (though re-introducing massive free-free-corrected cores would not alter the conclusion). [6.3. Limitations and perspectives: "Free-free emission: in Sect. 4.2, we rejected all sources that are arguably contaminated by free-free emission from our core sample. We ended up rejecting 84 sources (see Table 3)."]
- limitation (authors): Cores are probed at 2700 au spatial resolution, leaving potential sub-fragmentation and multiplicity on scales below 1000 au (down to ~200 au disk scales) unresolved. [6.3. Limitations and perspectives: "Sub-fragmentation: we probed the cores at a spatial resolution of 2700 au. Recent observations in the high-mass protostellar core G335 showed that a binary system, and perhaps even a triple system, could take place below 1000 au (Olguin et al. 2021, 2022)."]
- not stated (card): CASA version, calibration details, self-calibration parameters, and tclean imaging parameters (deferred to Paper II, Ginsburg et al. 2022); Exact configuration parameters and user-defined spatial scale ranges passed to getsf and GExt2D during source extraction; Software or tool used to convolve the native continuum maps to the 2700 au spatial resolution

### 2021AJ....161..146J: A Search for Companions via Direct Imaging in the DSHARP Planet-forming Disks (2021; protoplanetary_disks, exoplanets; multi_facility_alma_minor)
- question: Directly image planetary companions embedded into protoplanetary disks from the DSHARP sample.
- step 3: Measure contrast limits
  - method: Estimate local noise; inject and recover fake planets to correct throughput; normalize to the primary; correct small-number statistics. [Detection Limits: "Pixel-to-pixel noise maps of each ADI reduction were estimated within a sliding box of $1.5\times1.5$ *FWHM* in the NaCo field of view."] [Detection Limits: "The final $5\sigma$ contrast maps were obtained using the pixel-to-pixel noise maps divided by the flux loss and normalized by the relative calibration with the primary star"]
  - software: IPAG-ADI pipeline
  - parameter: Fake planets every 10 pixels at 3 position angles; 100 ADU. [Detection Limits: "fake planets were regularly injected (every 10 pixels at 3 different position angles, with a flux corresponding to 100 ADU) on the original data cubes before PSF subtraction."]
  - parameter: Azimuthal average of throughput losses at each radius. [Detection Limits: "by computing the azimuthal average of the flux losses for fake planets at the same radii(cite: 2010A&A...509A..52C; 2013A&A...553A..60R)."]
  - validation: Reprocess injected cubes using the different ADI algorithms. [Detection Limits: "The cubes were then reprocessed using the different ADI algorithms, allowing us to estimate the flux loss"]
- step 7: Test the Elias 24 candidate
  - method: Split the ADI sequence; inject fake planets at matching separation; obtain a second-epoch RDI observation and test bound/background injections. [Elias 24: "A first approach was to divide the original observing sequence into two, ensuring enough rotation of the field of view for the ADI algorithms to correctly process the images."] [Elias 24: "Fake planets were positioned at similar separations but different position angles ($0^{\circ}, 90^{\circ}$ and $180^{\circ}$) than the original signal."]
  - software: IPAG-ADI pipeline, Principal Component Analysis
  - parameter: Second-epoch injected source has the first-epoch flux. [Elias 24 second epoch observations: "we performed a test consisting on the injection of a fake planet with the same flux as derived in the first epoch."]
  - validation: First-epoch split sequences and injections recover sources; second-epoch non-recovery is inconclusive. [Elias 24: "In both sequences, the point-like signal was recovered at the same location for all the ADI methods used."] [Elias 24: "All the fake planets were recovered after the processing, producing similar point-like features as the original signal."]
- limitation (authors): ADI excludes the innermost disk regions. [Results: "In the majority of cases, the ADI reduction was limited to separations $\ge0.1-0.2"$, excluding the possibility of detections in the innermost regions of the systems (below $20-40$ AU)."]
- limitation (authors): Elias 24 lies near residual artifacts and the RDI inner limit; the second epoch is inconclusive. [Elias 24: "our ADI observations starts degrading at close separations in the inner region of the disk, as evidenced by the presence of artifacts that can be observed at separations similar to the alleged signal."]
- limitation (authors): Detection probabilities omit possible CPD emission. [Planet-disk interaction: comparison wit…: "the derived detection probabilities for all the disks in the sample do not take into account the possible presence of a circumplanetary disk (CPD), which might alter these values, although to an unknown extent."]
- not stated (card): Exact DSHARP image filenames/releases and the mapping between targets, images and the ten acknowledged ALMA project codes.; NaCo observing-program identifiers and raw/calibration exposure identifiers.; IPAG-ADI version, bad-pixel and sky-removal settings, and numerical frame-rejection thresholds.; Complete LOCI/sADI/rADI settings beyond the stated FWHM and separation criterion; exact PCA configur…

### 2020MNRAS.491.2506D: Using machine learning to study the kinematics of cold gas in galaxies (2020; nearby_galaxies; theory_or_simulation_compared_to_alma)
- question: Can a convolutional autoencoder trained on simulated velocity maps distinguish disturbed from ordered cold gas and recover position angles?
- step 2: Generate mock velocity maps
  - method: Align angular momentum with +z, rotate and displace galaxies, and generate mock observations directly from their 3D particle distributions using KinMS. [Data preparation: "Each galaxy was rotated so that their total angular momentum vector was aligned with the positive $z$-axis"] [Data preparation: "Using `KinMS` we generate simulated interferometric observations of galaxies directly from their 3D particle distributions."]
  - software: Python, KinMS
  - parameter: 8 random integer rotations; 0°≤θpos<360°; 5°≤φinc≤85° [Data preparation: "For any given distance projection, galaxies were given 8 random integer rotations in position-angle ($0^{\circ}\leq \theta_{\text{pos}}<360 ^{\circ}$) and inclination ($5^{\circ}\leq\phi_{\text{inc}}\leq85^{\circ}$)."]
  - parameter: 64″×64″ mock velocity-map field [Data preparation: "Each galaxy is displaced such that they fill a $64^{\prime\prime}\times64^{\prime\prime}$ mock velocity map image"]
  - parameter: Galaxy radius = 98th percentile particle distance from centre of potential [Data preparation: "Each galaxy’s radius is given as the $98$th percentile particle distance from its center of potential in kpc."]
  - parameter: Mock bmaj = 3″; stacked velocity-map dimensions 64×64×8 [Data preparation: "The EAGLE galaxies were passed to `KinMS` to create cubes of stacked velocity maps, with fixed mock beam sizes of $\text{bmaj} = 3^{\prime\prime}$, ready for labelling."] [Data preparation: "Each cube measured $64\times64\times8$ where $64\times64$ corresponds to the image dimensions (in pixels) and $8$ corresponds to snapshots during position-angle and inclination rotations."]
  - parameter: Non-numerical values and infinities replaced with 0 km s−1 [Data preparation: "It should be noted that we set all non-numerical values or infinities to a constant value, as passing such values to an ML algorithm will break its training."] [Data preparation: "We adopt $0$ $\text{km\,s}^{-1}$ as our constant (similarly to (cite: diaz_classifying_2019)) to minimise the the background influencing feature extraction."]
  - assumption: Centre of potential is the origin. [Data preparation: "using the centre of potential (as defined in the EAGLE Database, see (cite: the_eagle_team_eagle_2017)) as the origin."]
- limitation (authors): Simulated training data have unproven assumptions, imperfect physics and a resolution/sample-size trade-off. [EAGLE: "However, there are drawbacks, including: unproven model assumptions, imperfect physics, and trade-off between resolution and sample size due to computational constraints."]
- limitation (authors): The CAE architecture was not optimized. [Model training: Rotationally invariant …: "This means our CAE is unlikely to have the most optimised architecture"]
- limitation (authors): The 96th-percentile clipping level was arbitrary and not optimized. [Simulating noise: "Note that this choice of clipping at the $96$th percentile level is arbitrarily based on a handful of test cases and represents no specific parameter optimisation."]
- not stated (card): Which ALMA project and CO transition supplied each galaxy's exact velocity-map product.; Calibration and imaging provenance of the reused ALMA maps, including beam, channel width and moment-map masking.; ALMA input-map centring, spatial resampling, blank handling and velocity normalization.; Exact EAGLE query, adapted reading scripts and particle-weighting implementation in KinMS.; Training/test …

### 2026A&A...707A..77H: Massive dusty multiphase outflow in local merger shows no sign of slowing on kiloparsec scales (2026; nearby_galaxies; archival_reuse)
- question: Can an outflow identification method that uses MUSE stellar kinematics to define the quiescent gas in the ALMA CO(1-0) line profiles reveal the properties, multiphase structure and dust content of the outflow in the ULIRG merger IRAS20100-…
- step 7: Compute mass outflow rates, energetics and depletion time
  - method: Per-bin Mdot = M v / r summed over bins; momentum rate = Mdot v, kinetic power = Mdot v^2 / 2; depletion time = M_mol / Mdot_mol; coupling efficiency and momentum transfer compared with theoretical injection from star formation [5.2 Outflow mass and mass rate: "Summing over the contributions from all bins, we obtain the total outflow mass rates without assuming a specific geometry of the outflow."] [5.3 Outflow energetics: "its momentum rate ($\dot{p}_\mathrm{out}=\dot{M}_\mathrm{out}v_\mathrm{out}$) and kinetic power ($\dot{E}_\mathrm{kin,out}=\dot{M}_\mathrm{out}v_\mathrm{out}^2/2$)"]
  - parameter: minimum r_out = 1.49 kpc for CO (half the ALMA beam major axis); minimum 0.72 kpc for MUSE phases (half the MUSE PSF FWHM) [5.2 Outflow mass and mass rate: "of 1.49 kpc which corresponds to half the major axis"] [5.2 Outflow mass and mass rate: "of 0.72 kpc, equivalent to half the FWHM of the MUSE PSF for these observations."]
  - parameter: r_out is the distance of each bin centre to the SE nucleus [5.2 Outflow mass and mass rate: "where $r_\mathrm{out}$ is the distance of each bin center to the SE nucleus."]
  - assumption: Optically thick outflow tau ~ 1 and L_bol ~ L_IR when assessing radiation pressure [5.3 Outflow energetics: "assuming an optically thick outflow ($\tau \approx 1$) and $L_\mathrm{bol} \approx L_\mathrm{IR}$."]
  - assumption: Energetics treated as order-of-magnitude estimates because alpha_CO is highly uncertain [5.3 Outflow energetics: "Due to this, the comparisons and derived efficiencies in this section should be considered as order-of-magnitude estimates."]
  - validation: Mass rate compared with earlier resolved CO study and MUSE integrated-spectrum results [5.2 Outflow mass and mass rate: "find almost exactly the same mass outflow rate in their resolved study of CO(1-0) emission in IRAS20100-4156"]
- result: Cold molecular mass outflow rate = 700 ± +/-200 (Table 4) Msun/yr [5.2 Outflow mass and mass rate: "The cold molecular phase contributes by far the most to the total mass outflow rate with 700 $M_\odot$/yr."]
- result: Ionized outflow mass rate (Halpha), all bins vs high-velocity bins = 11 vs 10 ± not stated Msun/yr [5.2 Outflow mass and mass rate: "($10\,M_\odot$/yr compared to $11\,M_\odot$/yr)"]
- result: Mass loading factor of the molecular outflow = 3.5 ± not stated dimensionless [5.2 Outflow mass and mass rate: "This mass rate corresponds to a mass loading factor $\eta = \dot{M}_\mathrm{out,H_2}/\mathrm{SFR}$ of 3.5"]
- result: Momentum rate of the cold molecular outflow = 8.1e35 ± not stated dyn [5.3 Outflow energetics: "We find a momentum rate of $8.1\times10^{35}\,\mathrm{dyn}$ and a kinetic power of $7.8\times10^{42}\,\mathrm{erg/s}$ for the cold molecular phase of the outflow."]
- result: Kinetic power of the cold molecular outflow = 7.8e42 ± not stated erg/s [5.3 Outflow energetics: "We find a momentum rate of $8.1\times10^{35}\,\mathrm{dyn}$ and a kinetic power of $7.8\times10^{42}\,\mathrm{erg/s}$ for the cold molecular phase of the outflow."]
- result: Total kinetic power, all phases = 12e42 ± not stated erg/s [5.3 Outflow energetics: "The total kinetic power of the outflow is $12\times10^{42}\,\mathrm{erg/s}$"]
- result: Total momentum rate, all phases = 10e35 ± not stated dyn [5.3 Outflow energetics: "The total momentum rate of the outflow across all phases is $10\times10^{35}\,\mathrm{dyn}$"]
- result: Coupling efficiency required for a starburst-driven outflow = ~9% ± not stated percent [5.3 Outflow energetics: "this would require a coupling efficiency of $\sim9\%$ for a starburst driven outflow"]
- result: Molecular gas depletion timescale = 16 ± not stated Myr [5.5 Molecular gas depletion time: "We find a depletion timescale of 16 Myr"]
- limitation (authors): Ionized outflow masses are lower limits due to the electron density floor [4.2 Ionized gas tracers: "As a result, the global outflow masses we obtained should be treated as the lower limits for the actual outflow masses."]
- limitation (authors): alpha_CO in outflows is highly uncertain, so energetics are order-of-magnitude estimates [5.3 Outflow energetics: "For cold molecular gas in outflows, $\alpha_\mathrm{CO}$ is highly uncertain"]
- not stated (card): tclean parameters for the CO(1-0) cube: weighting and robust value, deconvolver, niter, threshold, masking, gridder, field/spw selection, output channel grid and velocity range; Line-free channels and polynomial order used in uvconsub continuum subtraction; Whether the archive calibration/pipeline products were used as-is or re-calibrated, and the flux/bandpass/phase calibrators; Noise estimate f…

### 2025A&A...694A.291K: Gamma-ray flares from the jet of the blazar CTA 102 in 2016─2018 (2025; agn_and_quasars; multi_facility_alma_minor)
- question: Physical mechanisms and emission-region locations of CTA 102 gamma-ray flares during 2016–2018
- step 3: Identify flares and spectral trends
  - method: Weighted-flux flare threshold, Bayesian blocks for local maxima, and Pearson correlation of photon index with flux [Multi-wavelength light curves: "We regard a threshold as $\left<F_{\omega}\right> + 3\sigma_{\omega} = 3.4 \times 10^{-6}$ ${\rm ph~cm^{-2}~s^{-1}}$ to define a flaring state."] [Multi-wavelength light curves: "We employed a Bayesian block analysis (cite: Scargle+2013) to identify the local maxima of multi-wavelength light curves."]
  - parameter: Bayesian block false positive rate 0.01 in all bands; local maximum exceeds both adjacent blocks [Multi-wavelength light curves: "In this analysis, we set a false positive rate of 0.01 (the probability of falsely reporting the detection of a change point) for all energy bands."] [Multi-wavelength light curves: "We identify a local maximum if the flux density of the block exceeds those of both previous and subsequent blocks."]
  - parameter: P1: MJD 57300–57550; P2: MJD 57550–57940; P3: MJD 57940–58400 [Multi-wavelength light curves: "This period extends from MJD 57550 to MJD 57940."] [Multi-wavelength light curves: "The periods preceding and following P2 within the overall flaring period were determined as P1 (MJD 57300–57550) and P3 (MJD 57940–58400), respectively."]
  - assumption: Flux measurements within each Bayesian block are consistent with a constant [Multi-wavelength light curves: "This method divides the light curves into blocks so that the flux measurements within each block are statistically consistent with a constant value."]
  - fitting: Seven-day bins for photon-index variations [Multi-wavelength light curves: "We searched for variations in the $\gamma$-ray photon index over the flaring period divided into seven-day time bins."]
  - validation: Photon-index/flux anticorrelation confidence greater than 99.99% [Multi-wavelength light curves: "we calculated the Pearson correlation coefficient, obtaining a value of $r_{\rm p} = -0.68$ for a confidence level greater than 99.99%."]
- result: Number of gamma-ray flares = six ± not stated dimensionless [Multi-wavelength light curves: "For the period from 2015 October 5 to 2018 October 9 (MJD 57300–58400), we identified six $\gamma$-ray flares"]
- result: Flare 3 peak gamma-ray flux at MJD 57750 = 1.415 × 10^{-5} ± ± 0.018 × 10^{-5} ph cm^{-2} s^{-1} [Multi-wavelength light curves: "Flare 3 is the brightest $\gamma$-ray flare, reaching a peak of $(1.415 \pm 0.018)\times 10^{-5}$ ${\rm ph~cm^{-2}~s^{-1}}$ on 2016 December 28 (MJD 57750)."]
- result: Flaring-period average gamma-ray photon index = 2.31 ± ± 0.01 dimensionless [Multi-wavelength light curves: "The $\gamma$-ray photon index varies between 1.98 and 2.62 with an average of $2.31 \pm 0.01$."]
- result: Gamma-ray photon-index/flux Pearson coefficient = -0.68 ± not stated dimensionless [Multi-wavelength light curves: "we calculated the Pearson correlation coefficient, obtaining a value of $r_{\rm p} = -0.68$ for a confidence level greater than 99.99%."]
- limitation (authors): Low Swift-BAT sensitivity limits detected X-ray local maxima [Multi-wavelength light curves: "The small number of local maxima in X-rays is mainly related to the relatively low sensitivity of *Swift*-BAT."]
- limitation (authors): Missing VLBA data near C3 ejection limits core-flux/ejection comparison [γ-ray flares in shock-shock interaction…: "The lack of 43 GHz VLBA data near the ejection time of C3 makes it challenging to study the relationship between the variation in the core flux density and the ejection of C3 from the core."]
- limitation (authors): Higher cadence and broadband SED modeling needed to clarify optical/gamma-ray correlation [γ-ray/optical correlations: "High-cadence observations and modeling of the broadband SED are needed for a clear understanding of the $\gamma$-optical correlation."]
- not stated (card): Exact ALMA measurement identifiers, epochs, flux densities and uncertainties selected from the inherited radio data.; ALMA flux extraction and calibration procedure inherited from KimSH+2022.; Rules for combining nearby radio frequencies, including any spectral correction, duplicate handling and cross-facility flux-scale adjustment.; Final DCF bin widths and lag grids for each frequency pair and …

### 2021ApJ...917...73W: Rapid Variability of Sgr A* across the Electromagnetic Spectrum (2021; agn_and_quasars, milky_way_ism; observational_alma_primary)
- question: Put the statistical properties of Sgr A*'s rapid variability across submillimeter, near-infrared, and X-ray wavelengths into the context of a single radiative model and determine the X-ray power spectral density.
- step 4: Fit single-zone synchrotron-SSC radiative model to submm, NIR, and X-ray variability
  - method: Simulate coupled slow and fast log-normal red-noise processes from shared Gaussian random numbers to drive optically thin synchrotron flux, cyclic magnetic field and source size evolution (injection, compression, expansion), self-absorptio… [Model Implementation: "and compare them via a suited distance function to the observed light curves in all three wavelength regimes."] [The Distance Function: "The factors of 10 and 50 are empirical and ensured that none of the additional distance terms starts to dominate"]
  - software: C++, MPI, Python 3, SED Animation
  - parameter: 230 GHz structure function restricted to time lags < 50 minutes; VLT positive flux fraction target = 0.9; VLT skewness target = 3.44; M/K ratio R_obs = 12 +/- 0.5 [The Distance Function: "The fraction of positive flux densities is 0.9."] [The Distance Function: "At an average (observed) flux density $S_{{K}} = 0.15$ mJy, (cite: 2018ApJ...863...15W) found the ratio of (observed) NIR flux densities at $M$ and $K$ bands to be $\Re_{\rm{obs}} = 12 \pm 0.5$."]
  - assumption: Single homogeneous spherical/slab synchrotron-SSC zone; R_S = 1.2e10 m; D_s = 2.523e20 m; A_K = 2.46 mag; A_M = 1.00 mag; X-ray extinction factor k_X = 3.39; slab-to-sphere volume factor 1.5 for electron density [Evolution of the Synchrotron Source and…: "Therefore we will proceed with the slab approximation and use the correction factor of $1.5$ when calculating electron densities from flux densities."] [Table 1: "| ${R}_{S}$ | $1.2\times 10^{10}$ | m |"]
  - assumption: Steady X-ray background equal for all three Chandra detector modes (chi_I = chi_G = chi_S) [Model Implementation: "we assumed that the steady X-ray background is equal for all three detector modes of Chandra"]
  - fitting: ABC with 33 iterations (32 iterations with n=500 particles, final iteration with n=5000 particles, reaching D_tot < 0.09 at acceptance rate 5e-5); posterior observables derived from 1000 mock light curves of 700 minutes duration [Results: "The final ABC run presented here is the result of 33 iterations, 32 with a particle size $n=500$ and the last with $n=5000$."] [Results: "We reached $D_{\rm{tot}}<0.09$ at an acceptance rate of $5\times10^{-5}$."]
  - validation: Compared posterior predictions to observed structure functions (1-sigma envelopes), simultaneous NIR-X-ray flux pairs, NIR CCDFs, spectral indices, steady SED limits, and 230 GHz-NIR cross-correlation delays [Results: "Figure 15 shows the structure functions with the corresponding 1$\sigma$ envelopes drawn from the posterior."] [Results: "Figure 17 compares the posterior of $(\log{S_{\rm{NIR}}}, \log{S_{{X}}})$ to observed flux-density pairs."]
- result: Power-law index of electron energy distribution (gamma_e) = 2.95 ± +0.21/-0.19 dimensionless [Table 2: "| $\gamma_{e}$ | flat on \[1.5, 4.0\] | $\phantom{-}2.95^{+0.21}_{-0.19}$ | power-law index of electron energy distribution |"]
- result: Minimum magnetic flux density (B_0) = 8.5 ± +1.8/-1.4 G [Table 2: "| $B_0$ \[G\] | log flat on \[$10^{-2}$, $10^3$\] | $\phantom{-}8.5^{+1.8}_{-1.4}$ | minimum magnetic flux density |"]
- result: Maximum physical source diameter (L_0) = 2.7 ± ±0.3 R_S [Table 2: "| $L_0$ \[$R_S$\] | log flat on \[$10^{-2}$, $10^3$\] | $\phantom{-}2.7\pm{0.3}$ | maximum physical source diameter |"]
- result: PSD slope of slow Gaussian process (gamma_slow) = 4.9 ± ±0.8 dimensionless [Table 2: "| $\gamma_{\rm{slow}}$ | flat on \[1.2, 6.5\] | $\phantom{-}4.9\pm{0.8}$ | PSD slope of slow Gaussian process |"]
- result: PSD slope of fast Gaussian process (gamma_fast) = 2.1 ± +0.4/-0.3 dimensionless [Table 2: "| $\gamma_{\rm{fast}}$ | flat on \[1.2, 9.5\] | $\phantom{-}2.1^{+0.4}_{-0.3}$ | PSD slope of fast Gaussian process |"]
- result: Correlation frequency of slow Gaussian process (f_b,slow) = 0.74 ± +0.13/-0.12 10^-2 minutes^-1 [Table 2: "| $f_{b,\rm{slow}}$ \[$10^{-2} \cdot \rm{minutes}^{-1}$\] | flat on \[0.001, 2.0\] | $\phantom{-}0.74^{+0.13}_{-0.12}$ | correlation frequency of slow Gaussian process |"]
- result: Correlation frequency of fast Gaussian process (f_b,fast) = 1.21 ± +0.29/-0.27 10^-2 minutes^-1 [Table 2: "| $f_{b,\rm{fast}}$ \[$10^{-2} \cdot \rm{minutes}^{-1}$\] | flat on \[0.001, 2.0\] | $\phantom{-}1.21^{+0.29}_{-0.27}$ | correlation frequency of fast Gaussian process |"]
- result: Measurement noise of 230 GHz (SMA and ALMA) observations (sigma_230GHz) = 0.08 ± ±0.01 Jy [Table 2: "| $\sigma_{230\,\mathrm{GHz}}$ \[Jy\] | Gaussian ($\mu = 0.15$, $\sigma=0.1$) | $\phantom{-}0.08\pm{0.01}$ | measurement noise of the 230 GHz (SMA and ALMA) |"]
- result: Measurement noise of 345 GHz (APEX and SMA) observations (sigma_345GHz) = 0.10 ± ±0.01 Jy [Table 2: "| $\sigma_{345\,\mathrm{GHz}}$ \[Jy\] | Gaussian ($\mu = 0.1$, $\sigma=0.1$) | $\phantom{-}0.10\pm{0.01}$ | measurement noise of the 345 GHz (APEX and SMA) |"]
- result: Time-dependent magnetic flux density B(t) = 12.7 ± +4.1/-2.9 G [Table 2: "| $B(t)$ \[G\] | | $\phantom{-}12.7^{+4.1}_{-2.9}$ | time-dependent magnetic flux density |"]
- result: Time-dependent source size L(t) = 2.20 ± +0.32/-0.30 R_S [Table 2: "| $L(t)$ \[$R_S$\] | | $\phantom{-}2.20^{+0.32}_{-0.30}$ | time-dependent source size |"]
- result: Time-dependent electron density n_e(t) = 4.3 ± +6.9/-2.7 10^7 cm^-3 [Table 2: "| $n_e(t)$ \[$10^7$ cm$^{-3}$\] | | $\phantom{-}4.3^{+6.9}_{-2.7}$ | time-dependent electron density |"]
- result: Time-dependent NIR spectral index alpha_NIR(t) = -1.65 ± +0.29/-0.30 dimensionless [Table 2: "| $\alpha_{\rm{NIR}}(t)$ | | $-1.65^{+0.29}_{-0.30}$ | time-dependent NIR spectral index (2.2 to 4.5 $\ensuremath{\mu}m$) |"]
- result: Time-dependent self-absorption turnover frequency nu_m(t) = 308 ± +96/-75 GHz [Table 2: "| $\nu_m(t)$ \[GHz\] | | $\phantom{-}308^{+96}_{-75}$ | time-dependent self-absorption turnover |"]
- result: Time-dependent cooling cutoff frequency nu_2(t) = 54 ± +111/-29 THz [Table 2: "| $\nu_2(t)$ \[THz\] | | $\phantom{-}54^{+111}_{-29}$ | time-dependent cooling cutoff frequency |"]
- result: Median brightness temperature at self-absorption turnover (T_b) = 1.8e10 ± not stated K [SED and Adiabatic expansion: "The median brightness temperature at the self-absorption turnover $T_b = 1.8\times10^{10}$ K."]
- limitation (authors): Model NIR spectral index has an upper limit of ~ -0.8 (optically thin alpha ~ -1.0), steeper than the canonical NIR spectral index of -0.65 (or -0.4) observed for bright flares. [Inconsistencies: "The model spectral index in the NIR has an upper limit $\alpha_{\rm{NIR}} \lesssim -0.8$ with many bright flares showing spectral indices as steep as $\alpha_{\rm{NIR}} \approx -1.2$ (Figure 21)."]
- limitation (authors): Variance at 230 GHz on the longest timescales (> 50 minutes) and epoch-to-epoch flux density offsets cannot be reproduced by the single-zone model. [Inconsistencies: "Another, potentially related, problem is the submm variability variance: at 230 GHz the variance at longest timescales cannot be reproduced by the model. This is the reason we did not include the last bin of the 230 GHz structure function in our distance function."]
- limitation (authors): The brightest observed NIR states (e.g., Do et al. 2019 flare) are underrepresented in the mock light curves (probability ~ 10^-3). [Inconsistencies: "Finally, our model gives the brightest observed NIR flare so far (cite: 2019ApJ...882L..27D) only ${\sim}10^{-3}$ probability. In other words, the brightest observed NIR states of Sgr A* are somewhat underrepresented in our mock light curves."]
- not stated (card): CASA version and ALMA pipeline version used for the 2016 ALMA observations; Which specific spectral windows and channels were excluded due to suspicious absorption features in the 2016 ALMA data; Whether self-calibration was performed on the 2016 ALMA observations; Image cell size, image dimensions, stopping threshold, and number of clean iterations for the ALMA clean task; Synthesized beam size …

### 2015ApJ...799...81S: The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Rest-frame Far-infrared Emission of Sub-millimeter Galaxies (2015; high_z_galaxies; observational_alma_primary)
- question: What are the size and morphology of the 870 um dust continuum emission of bright SMGs on 2-10 kpc scales, and how do they compare with sizes at other wavelengths and with quiescent galaxies?
- step 2: Test robustness of resolved sizes
  - method: Split-in-time imaging of UDS 204.0, phase calibrator size test, and 20,000 injected Gaussian simulations [2.2 Robustness of imaging: "we create 20,000 elliptical Gaussian model sources with a uniform distribution of peak SNR from 4 to 30"]
  - software: CASA
  - parameter: SNR>=10 required for 68% of sources recovered with fractional size error <30% [2.2 Robustness of imaging: "We find that this requirement is met for sources that are detected at a SNR $\geq$ 10"]
  - fitting: imfit elliptical Gaussian [Observations and Analysis, Robustness o…: "we use the imfit routine in casa to fit an elliptical Gaussian model (convolved with the synthesised beam) for the 870 $\mu$m emission from each SMG."]
  - validation: point-source fits imply true size <=0.18'' [2.2 Robustness of imaging: "we adopt this as an upper limit for the size of the unresolved SMGs"]
- step 5: Fit Sérsic profile to stack
  - method: Test galfit recovery on 4000 injected models; stack 23 SMGs and fit Sérsic [4.3.1 Sérsic index: "stack the 870 $\mu$m emission from the 23 SMGs detected at $>$ 10 $\sigma$ and use galfit to fit a Sérsic model to the stacked profile"]
  - software: galfit
  - fitting: galfit; bootstrap errors [Sérsic index: "stack the 870 $\mu$m emission from the 23 SMGs detected at $>$ 10 $\sigma$ and use galfit to fit a Sérsic model to the stacked profile."]
  - validation: injection recovery [4.3.1 Sérsic index: "half-light size of the model sources is recovered accurately at all values of SNR and Sérsic index"]
- result: stacked Sérsic index = 2.5 ± ±0.4 dimensionless [4.3.1 Sérsic index: "Sérsic index of $n$ = 2.5 $\pm$ 0.4 and a half-light radius of $R_{\rm e}$ = 0.17 $\pm$ 0.03$''$"]
- limitation (authors): Four possibly lensed SMGs excluded; four SMGs lack redshifts; only one SMG at z>3.5 [4.1 Physical size of SMGs: "An important caveat of this result is that only one SMG in our sample has a photometric redshift of $z \mathrel{\raise 0.35ex\hbox{$\scriptstyle >$}\kern-0.6em\lower 0.40ex\hbox{{$\scriptstyle \sim$}}}3.5$."]
- not stated (card): Gaussian taper width/uv-range for detection maps; clean threshold values, cell and image size, niter; bandpass calibrator and flux-scale uncertainty; photometric redshifts and L_FIR values per SMG (from Ma et al. in prep.); bootstrap iteration counts; exact conversion from FWHM to half-light radius and R80; details of stacking (centering, weighting)

### 2025ApJ...990L..70L: Discovery of Hα Emission from a Protoplanet Candidate around the Young Star 2MASS J16120668─3010270 with MagAO-X (2025; protoplanetary_disks, exoplanets; multi_facility_alma_minor)
- question: Is there an accreting protoplanet (H-alpha excess point source) inside the large dust gap of the 2MJ1612 disk, as seen with MagAO-X, and can it explain the gap?
- step 5: measure companion astrometry and contrast by forward modeling
  - method: negative fake planet injection grid with pyKLIP forward modeling; position minimizes flux in aperture, contrast minimizes RMS [2.3 Astrometry and Photometry of Planet…: "we obtained companion astrometry and photometry with the forward modeling feature in PyKLIP"] [2.3 Astrometry and Photometry of Planet…: "we minimized the root-mean-square (RMS) of the individual pixel values in the aperture centered on the optimized position"]
  - software: pyKLIP
  - parameter: optimal position is median over aperture radii 0.75 to 1.5 FWHM [2.3 Astrometry and Photometry of Planet…: "the optimal location is taken to be the median value of positions with minimized total flux with aperture radii ranging from 0.75 FWHM to 1.5 FWHM"]
  - parameter: true north 2.0 +/- 0.6 deg; pixel scale 5.93 +/- 0.03 mas [2.3 Astrometry and Photometry of Planet…: "For the true-north rotation correction, we adopted the value of 2.0$\pm$0.6$^\circ$."]
  - assumption: injected PSFs are Gaussian while the observed stellar PSFs are elliptical [3.2 H-alpha Variability and Line Flux: "the injected PSFs are assumed to be Gaussian while the stellar PSFs observed are elliptical"]
  - fitting: grid of injected negative planets, no sampler [2.3 Astrometry and Photometry of Planet…: "A grid of negative planets is injected into the datacube of combined frames around the initial position"]
  - validation: Error budget adds retrieval, plate scale and true-north terms in quadrature [2.3 Astrometry and Photometry of Planet…: "Adding the uncertainty from retrieval, plate scale, and true-north offset in quadrature"]
- result: H-alpha source separation from star (MagAO-X, two-epoch average) = 141.96 ± +/- 2.10 mas [abstract: "at a separation of 141.96$\pm$2.10 mas (23.45$\pm$0.29 au deprojected) from the star"]
- result: H-alpha source position angle (two-epoch average) = 159.00 ± +/- 0.55 deg [abstract: "position angle (PA)= 159.00$\pm$0.55$^\circ$"]
- result: Deprojected separation (abstract value) = 23.45 ± +/- 0.29 au [abstract: "(23.45$\pm$0.29 au deprojected)"]
- result: Deprojected separation (Results text value) = 23.8 ± +/- 1.7 au [3 Results and Discussion: "This translates to a de-projected separation of 23.8$\pm$1.7 au"]
- result: Final astrometric uncertainty on separation and PA = 2.97 mas and 0.78 deg ± not stated mas, deg [2.3 Astrometry and Photometry of Planet…: "the final uncertainty in separation and PA are respectively 2.97 mas and 0.78$^\circ$"]
- result: ASDI contrast, Apr 13 and Apr 16 = 4.0e-3 and 1.0e-3 ± +/- 0.9e-3 and +/- 0.4e-3 dimensionless [3 Results and Discussion: "The contrast of the sources in the ASDI images are (4.0$\pm$0.9)$\times$10$^{-3}$ and (1.0$\pm$0.4)$\times$10$^{-3}$ respectively for Apr 13 and 16."]
- limitation (authors): Orbit fit lacks phase coverage; more epochs needed [3.1 Comparison to SPHERE/IRDIS Observat…: "additional epochs are required to constrain the orbit meaningfully"]
- limitation (authors): Cannot rule out that the H-alpha source differs from the K band source [3.1 Comparison to SPHERE/IRDIS Observat…: "we cannot dismiss the possibility that the H$\alpha$ source has a different origin than the K band source"]
- limitation (authors): ALMA non-detection of the compact source may be due to resolving out with a smaller beam [3.4 Search for Outer Companions: "The non-detection in our ALMA maps may be due to the emission being resolved out with a smaller beam."]
- not stated (card): Self-calibration solution intervals, reference antenna and which spectral windows were used for self-calibration.; Line-free channel selection and image size and cell size for the final tclean image.; CASA pipeline version and flux calibrator used for the 2022.1.00646.S executions.; Flux rescaling factors applied when concatenating the seven earlier executions.; Project codes of the seven Band 6 …

### 2016ApJ...832..187B: The Massive Protostellar Cluster NGC 6334I at 220 au Resolution: Discovery of Further Multiplicity, Diversity, and a Hot Multi-core (2016; star_formation; observational_alma_primary)
- question: What is the multiplicity, nature and SED of the sources in the massive protocluster NGC6334I at ~220 AU resolution from 5 cm to 1.3 mm?
- step 4: SED modeling
  - method: Free-free model V of Olnon75 (fit r_e) plus modified greybody dust fits with fixed beta=1.7; uncertainties from 1000 Monte Carlo realizations [5.1 SEDs: "The uncertainties on the fitted parameters were obtained by computing the standard deviation of the fitted parameters obtained from fitting an ensemble of 1000 realizations"]
  - parameter: Te=1e4 K; ne = 3e5, 3e6, 3e7 cm-3 for MM1D, MM1B, CM1 [5.1 SEDs: "we set $n_e$ to $3\times10^5$, $3\times10^6$, and $3\times10^7$ cm$^{-3}$ for MM1D, MM1B, and CM1, respectively"]
  - assumption: beta=1.7 (MM1D uses 2.4) [5.1 SEDs: "we first chose to use a fixed value of $\beta=1.7$"]
  - fitting: Least squares greybody; sampler/priors not stated [Discussion, Spectral Energy Distributio…: "we fit the SED of each of these sources with a modified greybody function"]
  - validation: Fitted tau compared with computed tau_dust [5.1 SEDs: "shows that our modeling approach is self-consistent"]
- result: MM4A dust temperature = 98 ± +5/-6 K [Table 5: "| MM4A | 97 (5) | 98$^{+5}_{-6}$ | 5.3$^{+1.6}_{-1.0}$"]
- result: MM2A-core dust temperature = 152 ± +48/-19 K [Table 5: "| MM2Acore | 98 (4) | 152$^{+48}_{-19}$"]
- result: MM2B 7mm-1.3mm spectral index = 1.63 ± 0.44 dimensionless [5.2.3 The Hot Core MM2: "The SED of MM2B exhibits a 7 mm-1.3 mm spectral index of $1.63\pm0.44$"]
- result: MM1D beta = 2.4 ± not stated dimensionless [5.1 SEDs: "The fit shown in Fig. [6](#seds1) uses $\beta=2.4$"]
- limitation (authors): SEDs lack points near peak so Tdust, tau, beta cannot be constrained simultaneously [5.1 SEDs: "we are unable to accurately constrain $T_{dust}$, the greybody opacity ($\tau_\nu$), and the grain emissivity index ($\beta$) simultaneously"]
- not stated (card): Line-free channel ranges and threshold per spw; Image sizes, clean thresholds and masks; Self-calibration solution intervals; Greybody fit code and frequency/flux inputs details; Initial guesses for Gaussian fits and fitting software; Details of the rms measurement regions

### 2018A&A...618A.120L: The HH30 edge-on T Tauri star. A rotating and precessing monopolar outflow scrutinized by ALMA (2018; protoplanetary_disks, star_formation; observational_alma_primary)
- question: What is the origin of the small-scale molecular CO outflow of the edge-on T Tauri star HH30 (disk wind vs entrainment), and how is it linked to the disk and the binary/wiggling jet?
- step 5: Fit ring model to transverse pv diagrams
  - method: Gaussian fits of spectra at each transverse offset trace an ellipse, fitted with MPFITELLIPSE and converted to ring parameters (R, x_offset, Vz, Vr, Vphi); velocities 5-10 km/s excluded; errors doubled [4.3: "An ellipse is then fitted to the trace using the IDL MPFITELLIPSE procedure."]
  - software: IDL MPFITELLIPSE
  - parameter: pv diagrams every 0.15" from z=0.1" to 1.75" [4.4: "The fit is performed to each transverse pv diagram constructed every 0.15$^{\prime\prime}$ along the flow axis from z=0.1$^{\prime\prime}$ to z=1.75$^{\prime\prime}$."]
  - assumption: Narrow circular ring at each z; V0=0 (no orbital motion) for inclination [4.3: "we assume that the $^{12}$CO emission arises from a narrow circular ring of gas"]
  - fitting: Least-squares ellipse fit; 1000 Monte Carlo realizations with Gaussian parameter errors give 1 sigma on ring parameters [4.3: "We then compute 1000 sets of ellipse parameters by randomly drawing a realization for each parameter"]
  - validation: Reduced chi2 0.6-2.3 (4 at z=0.1") [4.4: "Reduced $\chi^2$ range between 0.6 and 2.3 except at the first position"]
- result: Cone semi-opening angle = 35 ± 0.7 deg [4.4: "The variation of radius is fully consistent with a cone of semi-opening angle 35$^{\circ}$ $\pm$ 0.7$^{\circ}$."]
- limitation (authors): Launching-radius inferences rely on a steady-state assumption; ACA data would be needed to rule out an envelope [5.2: "Although ACA observations would be required to image this component fully and definitely rule out an envelope around HH30"]
- not stated (card): Name of the phase/bandpass/flux calibrator quasars (blank in text); CASA version; Pipeline or manual calibration details and self-calibration; Cleaning mask, threshold, cell and image size in GILDAS; Exact spectral channels used for continuum; Details of rectangle for disk subtraction; ALMA project code (not printed in paper)

### 2017MNRAS.468.1769F: The varying mass distribution of molecular clouds across M83 (2017; nearby_galaxies, star_formation, milky_way_ism; archival_reuse)
- question: Does the molecular cloud mass distribution in M83 show a truncation mass that varies with galactocentric radius, like the young massive cluster population?
- step 2: Completeness by fake source injection
  - method: Inject 350 Gaussian clouds at 51 masses (1e5-1e6 Msun), 10 random offsets; fit logistic recovery function [GMC properties: "This process is repeated for 51 different mass values distributed logarithmically between $10^5~M_{\odot}$ and $10^6~M_{\odot}$."]
  - parameter: 50% completeness 3.35e5 Msun [GMC properties: "establishing a 50% completeness limit of $M_{\mathrm{GMC}} > 3.35\times 10^5~M_{\odot}$"]
  - assumption: Fake clouds follow Local Group size-linewidth-luminosity relations [GMC properties: "luminosities, sizes, and line widths set by the characteristic relationships established in the Local Group population"]
  - fitting: logistic function [Analysis - GMC properties: "We model the recovery fraction \[$f(M)$\] as a logistic function and fit the parameters of the function to obtain an analytic expression for the survey completeness"]
  - validation: Gaussian correction selected because it recovers properties of injected clouds [GMC properties: "We select this correction method over others based on it recovering the properties of clouds in our fake source injection test."]
- result: 50% completeness limit = 3.35e5 ± not stated Msun [GMC properties: "50% completeness limit of $M_{\mathrm{GMC}} > 3.35\times 10^5~M_{\odot}$"]
- result: Clouds above completeness limit = 711 ± not stated clouds [GMC properties: "Of the 873 clouds identified, 711 are above the 50% completeness limit."]
- limitation (authors): Cloud blending in central region makes nuclear mass distribution suspect [Systematic Effects: "We should therefore regard the clouds in the $R_g<0.45$ kpc bin as particularly suspect"]
- not stated (card): Exact imaging parameters of the JVO QA2 cube (weighting, cell size, deconvolver); CASA version used for the delivered data; Fake-cloud size and line-width parameters used in the injection test; Exact radial bin geometry, inclination and position angle used for deprojection; Method for surface-density and velocity-dispersion profiles in the Toomre/Jeans calculation (radial binning details); Recipe…

### 2022A&A...666A..39M: A first search of transients in the Galactic center from 230 GHz ALMA observations (2022; transients, milky_way_ism, agn_and_quasars; observational_alma_primary)
- question: Can second-to-minute timescale millimeter-wave radio transients be detected in the Galactic Center at 230 GHz using a novel two-component self-calibration procedure on ALMA observations?
- step 3: Validate transient detection pipeline on synthetic data
  - method: Simulate Track B (April 6) 230 GHz observations using CASA simalma with real Sgr A* light curves, the mini-spiral model, thermal noise, real antenna gains, and an injected Gaussian-like transient. Apply the two-component self-calibration, … [Simulated data: "We have simulated ALMA observations of Sgr A$^*$ corresponding to the array configuration, and exact observing times, of the true visibilities of Track B (April 6) in the 2017 EHT campaign by using the CASA task `simalma` with its default parameters for 230 GHz."] [Simulated data: "Once convergence of the self-calibration was achieved, we computed the residual visibilities (i.e., by subtracting the model of the minispiral and Sgr A$^*$) and generated the corresponding residual images for each integration time."]
  - software: CASA, simalma, tclean
  - parameter: Synthetic transient: peak ~207 mJy, duration ~42 s, centered at 10:52:01 UT, offset 5 arcsec East and 1 arcsec North of Sgr A* [Simulated data: "In addition to this, we have inserted a short transient, with amplitude evolution Gaussian-like, with a duration of $\sim42$ seconds and centered on 10:52:01 UT and located at 5 arcsec to the east of Sgr A$^*$ and 1 arcsec to the north. The peak flux density of the transient is $\sim207$ mJy (see Fig. [3](#fig:trans_a…"]
  - fitting: Same two-component chi-square self-calibration as step 2 [Simulated data: "We have calibrated the synthetic observations using the two-components’ self-calibration explained in Sect [4](#sec:stgy)."]
  - validation: Successful recovery of the injected synthetic transient in both 4 s and 12 s residual images with peak S/N of 15.194 and peak brightness ~200 mJy [Simulated data: "From time 10:51:27 UT (h) to 10:52:33 UT (h) we can see how a transient point source is appearing $\sim5$ arcsec to the East of Sgr A$^*$. The brightness peak is notably increasing to reach a maximum of $\sim$ 200 mJy, while the duration of the transient is approximately to 1 min."] [Some details on the synthetic transient: "Now, we can easily follow the evolution of the S/N and rms. In both cases, they start with relative low (close to the mean) and they start to increase progressively while they are advancing in time, until their maximum (15.19 , 1.32 mJy/beam respectively) is reached."]
- step 4: Search for transients in real ALMA residual snapshot images
  - method: Subtract the converged Sgr A* and mini-spiral model visibilities from each track (April 6, 7, 11), generate residual snapshot images at 4 s and 12 s cadences, track peak dynamic range (S/N) and rms using a running median window, apply dete… [Strategy for finding transients: "We have thus set the detection threshold of transients to peak excursion of 7 times the instantaneous rms between consecutive images, which also gives a very low probability of false detection from thermal noise."] [Strategy for finding transients: "In particular, the transient search has been performed considering two different time-search intervals, one defined by the observation cadence time (4 s) and the other one by three times the cadence time (12 s)."]
  - software: CASA, tclean
  - parameter: Detection threshold: peak excursion of 7 times the instantaneous rms between consecutive images; at least 3 standard deviations in maxima between two consecutive time-search intervals [Strategy for finding transients: "We have thus set the detection threshold of transients to peak excursion of 7 times the instantaneous rms between consecutive images, which also gives a very low probability of false detection from thermal noise."] [Strategy for finding transients: "Excursions of at least three standard deviation in the maxima between two consecutive time-search intervals are considered as a potential transient."]
  - parameter: Minimum duration: 12 s (three 4 s integration times) [Strategy for finding transients: "Therefore, on the one hand the minimum duration of a transient would be three times the integration time."] [Summary and conclusions: "by tracking events occurring for a duration of at least 12s (three times the ALMA integration time)."]
  - assumption: Noise is assumed to follow a Gaussian distribution across ~10^4 beams in the field of view to estimate false positive probability (~10^-8 at 7 sigma) [Strategy for finding transients: "Supposing that noise follows a normal distribution, we have computed the number of beams that form the image Fig. [2](#fig:minispirals) (which is $\approx10^4$), and we have found that the probability of getting at least one false positive transient detection in the field of view with a confidence of 7$\sigma$ is $\ap…"]
  - fitting: Running median window applied to dynamic range time series [Strategy for finding transients: "Such time-search intervals are defined following running median window at each epoch."]
  - validation: Manual inspection of residual snapshot sequences and verification against antenna elevation (< 25 deg exhibits significant quality loss) [Real data: "It is important to note that data corresponding to source elevation below 25$^\circ$ is exhibiting significant quality loss."] [Real data: "In any case, in Appendix [11](#sec:appendix_plots), detailed sequences of snapshots of transient candidates are shown. The aim of these plots is to verify whether the higher dynamic range in a particular UT is related to a point source in the image plane, or if the image is contaminated by systematic artifacts"]
- result: Instantaneous rms range on April 6 (Track B) = 2.138-7.210 ± not stated mJy/beam [Strategy for finding transients: "the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11"]
- result: Instantaneous rms range on April 7 (Track C) = 0.287-16.602 ± not stated mJy/beam [Strategy for finding transients: "the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11"]
- result: Instantaneous rms range on April 11 (Track E) = 2.522-15.661 ± not stated mJy/beam [Strategy for finding transients: "the instantaneous root-mean-square (rms) of our ALMA observations, ranged between $2.138-7.210$ mJy/beam in April 6, $0.287-16.602$ mJy/beam in April 7 and $2.522-15.661$ mJy/beam in April 11"]
- result: Residual image mean S/N for Track B (April 6) = 3.660 ± not stated dimensionless [Real data: "| 3.660 | 2.628 | 0.494 |"]
- result: Residual image mean rms for Track B (April 6) = 2.628 ± 0.494 mJy/beam [Real data: "| 3.660 | 2.628 | 0.494 |"]
- result: Residual image mean S/N for Track C (April 7) = 4.537 ± not stated dimensionless [Real data: "| 4.537 | 2.490 | 0.749 |"]
- result: Residual image mean rms for Track C (April 7) = 2.490 ± 0.749 mJy/beam [Real data: "| 4.537 | 2.490 | 0.749 |"]
- result: Residual image mean S/N for Track E (April 11) = 5.005 ± not stated dimensionless [Real data: "| 5.005 | 3.096 | 0.521 |"]
- result: Residual image mean rms for Track E (April 11) = 3.096 ± 0.521 mJy/beam [Real data: "| 5.005 | 3.096 | 0.521 |"]
- result: Number of reliable transient detections in 2017 EHT ALMA campaign = 0 ± not stated dimensionless [Real data: "Thus we can conclude that we have not found any reliable detection of transients in the ALMA observation during the 2017 EHT Campaign."]
- limitation (authors): The observations and residual snapshot images are dynamic-range limited rather than thermal-noise limited, even at 4-second integration times, due to finite fidelity of the mini-spiral model and suboptimal calibration in bad weather. [Introduction: "Indeed, and as we discuss in Sect. [6](#sec:realdata), we are limited by dynamic range (rather than by sensitivity) even at the level of the integration time used in the ALMA correlator (four seconds)."]
- limitation (authors): The statistical false-positive calculation assumes a Gaussian noise distribution, which does not strictly hold because the snapshot residuals are dynamic-range limited and non-Gaussian. [Strategy for finding transients: "In addition, one important assumption we have made is that we are working on a Gaussian distribution of the noise. This is not true, as as we are dynamic range limited in snapshots where potential excursions are seen."]
- limitation (authors): Primary-beam attenuation is not corrected during the search, which reduces sensitivity toward the edges of the field of view. [Strategy for finding transients: "An important point to highlight is that, with this strategy, the primary-beam response is not corrected. In the case a transient would be found, the primary-beam correction should be applied."]
- not stated (card): Exact tclean imaging parameters (weighting scheme, robust parameter, cell size, image pixel dimensions, niter, stopping threshold, and clean mask definition); ALMA project code in the paper text (linked as 2016.1.01154.V only in archive metadata); Quantitative threshold value used to flag visibilities with 'extremely high and nonrealistic rms'; Length (number of frames) of the running median wind…

### 2023MNRAS.522...56V: A systematic survey of millimetre-wavelength flaring variability of young stellar objects in the Orion Nebula Cluster (2023; star_formation, protoplanetary_disks, stellar_physics, transients; observational_alma_primary)
- question: What is the occurrence rate and nature of strong, short-term (minutes to days) millimeter-wavelength flaring variability in Young Stellar Objects (YSOs) in the Orion Nebula Cluster, and how do systematic time-sliced imaging effects and fla…
- step 2: Simulate ALMA observations to quantify systematic artificial variability
  - method: Generate 100 2D Gaussian constant artificial source models combined with 3 real background cutouts from the concatenated image (300 sky models), simulate visibilities across 7 hour angles (1 h each) using Simobserve, image with Simanalyze,… [Simulated observations to assess system…: "We made use of the Simobserve task in CASA to first simulate the visibilities consisting of 7 observations of 1 h integration time each all of them at different hour angles ranging from $-5$ h to $+1$ h"] [Simulated observations to assess system…: "This resulted in 300 input sky models whose visibilities were simulated for 7 different hour angles (HAs) on the sky and subsequently imaged with Simanalyze with a pixel size of 0.05 arcsec and an image size of 100 pixels per side."]
  - software: CASA, Simobserve, Simanalyze, IMFIT
  - parameter: Source FWHM = 0.1 to 0.9 arcsec; peak flux density = 5 to 100 mJy beam^-1 [Simulated observations to assess system…: "The artificial sources were 2D Gaussian models with a range of sizes for both major and minor axis equivalent to FWHM between 0.1 and 0.9 arcsec"] [Simulated observations to assess system…: "The amplitude of these model sources were set to cover a range of peak flux density between 5 and 100 mJy beam$^{-1}$."]
  - parameter: Hour angles = -5 h to +1 h (7 observations of 1 h each); pixel size = 0.05 arcsec; image size = 100 x 100 pixels [Simulated observations to assess system…: "consisting of 7 observations of 1 h integration time each all of them at different hour angles ranging from $-5$ h to $+1$ h"] [Simulated observations to assess system…: "subsequently imaged with Simanalyze with a pixel size of 0.05 arcsec and an image size of 100 pixels per side."]
  - assumption: Artificial sources have constant intrinsic flux density; measured flux variations arise from the changing synthesized beam interacting with source structure and complex background. [Simulated observations to assess system…: "we performed an analysis of simulated ALMA observations for a set of artificial, constant sources."]
  - fitting: Iterative 2D Gaussian fitting with CASA IMFIT varying fitting area and position offsets [Simulated observations to assess system…: "we obtained flux information using a Gaussian fitting algorithm based on the IMFIT task in CASA that iterates over each input source using different values for fitting area around the source and different offsets from the input position to avoid nearby contamination."]
  - validation: Restricted HA range matching actual observations (-3h20m < HA < +1h) yields maximum systematic VF ~ 1.6; adopted conservative systematic threshold of VF = 2. [Simulated observations to assess system…: "If we limit these simulations to $-$3h20m$<$HA$<+1$h, we then obtain a maximum systematic variability of VF$\sim$1.6."] [Simulated observations to assess system…: "a reasonable cut-off for systematic variability that can affect at least a sample of sources given certain conditions (e.g., source size in combination with a complex background) is VF$=$2."]
- result: Artificial variability factor (VF) range in full simulations = 1.1 to 2.1 ± not stated dimensionless [Simulated observations to assess system…: "These artificial variability spans a range of 1.1$\leq$VF$\leq$2.1 and a median value of VF$=$1.51."]
- result: Median artificial variability factor (VF) in simulations = 1.51 ± not stated dimensionless [Simulated observations to assess system…: "These artificial variability spans a range of 1.1$\leq$VF$\leq$2.1 and a median value of VF$=$1.51."]
- result: Maximum systematic variability factor for actual HA range (-3h20m < HA < +1h) = 1.6 ± not stated dimensionless [Simulated observations to assess system…: "If we limit these simulations to $-$3h20m$<$HA$<+1$h, we then obtain a maximum systematic variability of VF$\sim$1.6."]
- result: Adopted systematic variability cut-off threshold (VF) = 2 ± not stated dimensionless [Simulated observations to assess system…: "a reasonable cut-off for systematic variability that can affect at least a sample of sources given certain conditions (e.g., source size in combination with a complex background) is VF$=$2."]
- limitation (authors): Dual-polarization mode (XX, YY) prevents recovery of Stokes V (circular polarization) and is insufficient to obtain full linear polarization without additional calibration. [Observations and Data Reduction: "the observations were carried out in dual-polarization mode recording the XX and YY correlations that allow us to recover the Stokes I intensity maps (Stokes Q is also accessible but insufficient to obtain overall linear polarization without additional calibration)."]
- limitation (authors): Poor weather conditions on 2017 December 29 and during epoch 4 degraded the sensitivity to 0.18-0.31 mJy beam^-1, worse than early theoretical predictions (~10-100 uJy). [Introduction: "However, such sensitivity was not achieved in the ALMA band 3 observations that we are presenting here, which ranges between $\sim$100 and $\sim$300 $\mu$Jy"]
- limitation (authors): Systematic effects from a changing synthesized beam in time-sliced imaging limit the study of minor variability (VF <= 2) and noise widens the VF distribution envelope up to VF ~ 3-4 (1-h) and VF ~ 5-7 (20-min) for faint sources. [Simulated observations to assess system…: "While sources in our actual ALMA data with VF$\leq$2 may still show real variability, the main focus in our study is to find the strongest events and how often those occur rather than a detailed study of minor variability."]
- not stated (card): Stopping criteria (niter, threshold) and masking strategy used in CASA TCLEAN for the concatenated, 1-h, 20-min, 4-min, and 8-s images; Exact box sizes, offset grid values, and convergence criteria used in the iterative CASA IMFIT source extraction wrapper from Vargas-Gonzalez et al. (2021); Exact coordinates of the three background cutout regions extracted from the concatenated image for the Sim…

### 2026MNRAS.548ag325W: 3D insights into SN 1987A: ALMA observations compared to hydrodynamical explosion simulations (2026; transients, astrochemistry, milky_way_ism; observational_alma_primary)
- question: How do the three-dimensional spatial and velocity distributions of CO and SiO molecules in the ejecta of SN 1987A observed with ALMA compare with long-time 3D hydrodynamical supernova explosion simulations across different progenitor model…
- step 3: Derive observational fractional mass-velocity distributions and summary velocity parameters
  - method: Convert 3D spatial distances to 3D radial velocities by dividing radial distance by time since explosion. Bin fractional intensities in increments of 100 or 300 km s^-1. Apply a 3-point moving average and compute v_peak, width (difference … [Mass distributions: "Under these assumptions, the fractional mass at a given velocity is proportional to the fractional intensity."] [Mass distributions: "Depending on the spectral resolution of the respective data set, the radial velocity was binned in increments of $100\,$km s$^{-1}$ or $300\,$km s$^{-1}$."]
  - parameter: 1000 Monte Carlo iterations, 20% standard deviation per data point, 3-point moving average, percentiles: 25th, 75th, 95th [Mass distributions: "For each data point, we draw values from a normal distribution centred on the observed value, with a standard deviation of 20%, which corresponds to the uncertainty values estimated in Appendix 8 from both statistical and systematic effects."] [Mass distributions: "To reduce the influence of small-scale noise, we apply a 3-point moving average before calculating $v_\mathrm{peak}$ and width."]
  - assumption: Ejecta are optically thin at the observed wavelengths, in local thermodynamic equilibrium (LTE), and at a uniform temperature; constant expansion velocity [Mass distributions: "To derive these mass distributions, we assume that the ejecta has the following properties: 1. it is optically thin at the observed wavelengths; 2. it is in local thermodynamic equilibrium (LTE); 3. it has a uniform temperature."]
  - fitting: Monte Carlo sampling (1000 iterations) from normal distribution with 20% standard deviation [Mass distributions: "For each data point, we draw values from a normal distribution centred on the observed value, with a standard deviation of 20%"]
  - validation: Dedicated sensitivity tests in Appendix: varying explosion centre by +/-5 pixels (1000 realizations), adding synthetic Gaussian-filtered (sigma=3 pixels) noise (1000 realizations), and varying noise threshold by x0.5 to x2 [Position of the explosion site: "We estimate the associated error by varying the assumed centre of the explosion by up to $\pm5$ pixels N/S and E/W."] [Image noise: "We create the synthetic noise by first generating pure uncorrelated normally-distributed noise values in each pixel, and then applying a Gaussian filter with a standard deviation of 3 pixels."]
- result: CO J=2-1 mass distribution peak velocity (v_peak) = 1830 ± 210 km s^-1 [Table 2: "CO $J$=2-1 | 1830$\pm$210 | 1210$\pm$70 | 3980$\pm$40"]
- result: CO J=2-1 mass distribution velocity width = 1210 ± 70 km s^-1 [Table 2: "CO $J$=2-1 | 1830$\pm$210 | 1210$\pm$70 | 3980$\pm$40"]
- result: CO J=2-1 mass distribution maximal velocity (v_max, 95% mass) = 3980 ± 40 km s^-1 [Table 2: "CO $J$=2-1 | 1830$\pm$210 | 1210$\pm$70 | 3980$\pm$40"]
- result: SiO J=5-4 epoch 1 mass distribution peak velocity (v_peak) = 1730 ± 190 km s^-1 [Table 2: "SiO $J$=5-4 ep.1 | 1730$\pm$190 | 1180$\pm$60 | 3600$\pm$30"]
- result: SiO J=5-4 epoch 1 mass distribution velocity width = 1180 ± 60 km s^-1 [Table 2: "SiO $J$=5-4 ep.1 | 1730$\pm$190 | 1180$\pm$60 | 3600$\pm$30"]
- result: SiO J=5-4 epoch 1 mass distribution maximal velocity (v_max) = 3600 ± 30 km s^-1 [Table 2: "SiO $J$=5-4 ep.1 | 1730$\pm$190 | 1180$\pm$60 | 3600$\pm$30"]
- result: SiO J=5-4 epoch 2 mass distribution peak velocity (v_peak) = 1600 ± 80 km s^-1 [Table 2: "SiO $J$=5-4 ep.2 | 1600$\pm$80 | 870$\pm$60 | 3110$\pm$60"]
- result: SiO J=5-4 epoch 2 mass distribution velocity width = 870 ± 60 km s^-1 [Table 2: "SiO $J$=5-4 ep.2 | 1600$\pm$80 | 870$\pm$60 | 3110$\pm$60"]
- result: SiO J=5-4 epoch 2 mass distribution maximal velocity (v_max) = 3110 ± 60 km s^-1 [Table 2: "SiO $J$=5-4 ep.2 | 1600$\pm$80 | 870$\pm$60 | 3110$\pm$60"]
- result: SiO J=6-5 epoch 1 mass distribution peak velocity (v_peak) = 1820 ± 190 km s^-1 [Table 2: "SiO $J$=6-5 ep.1 | 1820$\pm$190 | 930$\pm$60 | 3220$\pm$50"]
- result: SiO J=6-5 epoch 1 mass distribution velocity width = 930 ± 60 km s^-1 [Table 2: "SiO $J$=6-5 ep.1 | 1820$\pm$190 | 930$\pm$60 | 3220$\pm$50"]
- result: SiO J=6-5 epoch 1 mass distribution maximal velocity (v_max) = 3220 ± 50 km s^-1 [Table 2: "SiO $J$=6-5 ep.1 | 1820$\pm$190 | 930$\pm$60 | 3220$\pm$50"]
- result: SiO J=6-5 epoch 2 mass distribution peak velocity (v_peak) = 1530 ± 100 km s^-1 [Table 2: "SiO $J$=6-5 ep.2 | 1530$\pm$100 | 1000$\pm$50 | 3510$\pm$70"]
- result: SiO J=6-5 epoch 2 mass distribution velocity width = 1000 ± 50 km s^-1 [Table 2: "SiO $J$=6-5 ep.2 | 1530$\pm$100 | 1000$\pm$50 | 3510$\pm$70"]
- result: SiO J=6-5 epoch 2 mass distribution maximal velocity (v_max) = 3510 ± 70 km s^-1 [Table 2: "SiO $J$=6-5 ep.2 | 1530$\pm$100 | 1000$\pm$50 | 3510$\pm$70"]
- result: SiO average mass distribution peak velocity (v_peak) = 1600 ± 110 km s^-1 [Table 2: "SiO (average) | 1600$\pm$110 | 1080$\pm$70 | 3560$\pm$50"]
- result: SiO average mass distribution velocity width = 1080 ± 70 km s^-1 [Table 2: "SiO (average) | 1600$\pm$110 | 1080$\pm$70 | 3560$\pm$50"]
- result: SiO average mass distribution maximal velocity (v_max) = 3560 ± 50 km s^-1 [Table 2: "SiO (average) | 1600$\pm$110 | 1080$\pm$70 | 3560$\pm$50"]
- limitation (authors): SiO J=5-4 Epoch 2 cube is truncated at +2000 km s^-1 on the receding side due to insufficient spectral bandwidth. [Integrated line profiles: "it can also be seen that the SiO 5–4 data from the second epoch of observations (green line, bottom panel) is truncated on the far side at a velocity of +2000 kms$^{-1}$, due to the bandwidth not being sufficient to cover the entire range of velocities."]
- limitation (authors): High-velocity molecular emission in the ALMA cubes may be buried in noise or excluded by the spatial cut-off used to avoid contamination from the equatorial ring. [Summary and discussion: "Too high model predictions for the velocity could simply mean that the material is not detected, because it is either buried in the noise, or it is at such high velocities that the ejecta are excluded by the truncation of the data to avoid contamination from the ring of SN 1987A."]
- limitation (authors): Explosion energy and energy deposition timescale are free parameters in the approximate ray-by-ray neutrino transport scheme, and 56Ni yields have uncertainties due to the electron fraction Ye. [Summary and discussion: "Our approximate approach of the neutrino transport allows us to choose the explosion energy (and the energy deposition time scale) as a free parameter, and it is not calculated self-consistently."]
- not stated (card): Exact CASA and ALMA pipeline versions used for calibration and imaging; Specific frequency/channel ranges used as line-free channels for continuum subtraction; Deconvolver, weighting scheme (for 2017 SiO 5-4 and Epoch 1), masking, and threshold parameters in CASA clean; Exact coordinates of the four off-source regions outside the equatorial ring used to calculate the MAD noise threshold; How the …

### 2018ApJ...863..193V: Molecular Gas Filaments and Star-forming Knots Beneath an X-Ray Cavity in RXC J1504-0248 (2018; galaxy_clusters_and_sz, nearby_galaxies, star_formation; observational_alma_primary)
- question: What are the mass, morphology, kinematics, origin and star formation of the molecular gas in the RXCJ1504 BCG, and how does it relate to an X-ray cavity?
- step 3: Extract and fit integrated and regional spectra
  - method: One or two Gaussian components fitted with LMFIT; Monte Carlo test with at least 1000 iterations and 3 sigma detection; numerical integration also done [3.2 Integrated Spectra: "Each spectral component was tested using a Monte Carlo analysis with at least 1000 iterations, with a detection requiring a $3\sigma$ significance (cite: Protassov02)."]
  - software: LMFIT
  - parameter: 2500 MC iterations for per-pixel maps [3.4 Molecular Gas Distribution and Kine…: "2500 iterations were used for the Monte Carlo analysis, with a detection requiring $3\sigma$ significance."]
  - fitting: Gaussian least squares with instrumental broadening incorporated; components added only if previous detected [3.2 Integrated Spectra: "The presence of one component was required before attempting to fit a second. Instrumental broadening has been incorporated into the model."]
  - validation: Compared ALMA CO(1-0) flux to IRAM-30m (45% recovered) [3.2 Integrated Spectra: "The integrated flux measured by ALMA is $45\pm8\%$ of this single dish measurement."]
- result: CO(3-2)/(1-0) flux ratio = 9.0 ± 0.4 dimensionless [3.2 Integrated Spectra: "${\rm CO~(3-2)/(1-0)} = 9.0\pm0.4$ in flux units"]
- limitation (authors): The cavity is poorly defined and may not be real [4.1 Gas Origin: "The feature identified as a potential cavity is poorly defined, so it is not clear if it is a real cavity."]
- limitation (authors): HST images manually aligned, so small-scale offsets between gas and UV may be missed [3.5 Spatial Correlation with UV Emission: "Spatial offsets between the molecular gas and young stars could be present, but would be missed due to this manual alignment."]
- not stated (card): Line-free channels and continuum-subtraction order for uvcontsub; Clean masks, threshold, niter, cell and image size; Self-calibration solution intervals; Exact HST data sets and pipeline products, and manual shifts beyond those quoted; Regions (polygon and extraction boxes) definitions for spectra and SFR; Flux calibrator and flux scale uncertainty; Extraction details of the Chandra surface brig…

### 2026ApJ..1000..141K: First Determination of the Cosmic Microwave Background Radiation Temperature at z = 0.68 Using Molecular Absorption Lines (2026; cosmology, agn_and_quasars, astrochemistry; archival_reuse)
- question: What is the cosmic microwave background (CMB) radiation temperature at z = 0.68 derived from rotational molecular absorption lines toward the lensed quasar B0218+357, and is it consistent with the standard Big Bang cosmological model?
- step 3: Compute optical depth profiles and propagate covering factor uncertainties
  - method: Monte Carlo sampling of continuum covering factor f_c and continuum-normalized absorption depth to compute optical depth probability distribution, followed by correction for lognormal column-density nonuniformity [Continuum Covering Factor: "For each velocity bin and each transition, we drew random and independent samples of $f_\mathrm{c}$ and $\Delta I/I_\mathrm{c}$ from their respective distributions and computed the optical depth using Equation (\[eq:taudef\])."] [Correction for Nonuniformity: "The resulting relation between $\tau_{\rm obs}$ and $\tau_{\rm real}$ is shown in Figure 1 of (cite: Kotani_2025). We applied this nonuniformity correction to all data points in the absorption spectra."]
  - software: NumPy, SciPy
  - parameter: 100,000 Monte Carlo realizations [Continuum Covering Factor: "Repeating this procedure 100,000 times yielded the probability distribution of the optical depth."]
  - parameter: f_c uniform distribution in [0.77, 1.00] [Continuum Covering Factor: "We assumed that $f_\mathrm{c}$ follows a uniform distribution between 0.77 and 1.00."]
  - assumption: Lognormal column density distribution with parameters from Orion A GMC (mean N(H2) ~ 1.5e22 cm^-2) [Correction for Nonuniformity: "In this study, we adopted the N-PDF parameters derived by (cite: Ma_2020) for the Orion A giant molecular cloud, which has a comparable mean column density of $\sim 1.5\times10^{22}\,{\rm cm}^{-2}$ (cite: Ma_2020), to compute the correction."]
  - fitting: Monte Carlo sampling (100,000 iterations); uniform prior on f_c in [0.77, 1.00], normal distribution on ΔI/I_c [Continuum Covering Factor: "We assumed that $f_\mathrm{c}$ follows a uniform distribution between 0.77 and 1.00."] [Continuum Covering Factor: "The absorption depth normalized by the continuum level, ${\Delta I/I_\mathrm{c}} = 1 - I_\mathrm{obs}$, is assumed to follow a normal distribution, with its mean and standard deviation given by the observed value and its uncertainty, respectively."]
  - validation: Checked saturation bottom of HCN J=2-1 at +5 km/s yielding lower limit f_c ~ 0.8, consistent with f_c >= 0.77 [Optical Depth: "If we assume that the optical depth becomes infinite at the absorption minimum, Equation (\[eq:taudef\]) yields a lower limit of $f_{\rm c} \sim 0.8$, which is consistent with the constraint $f_{\rm c} \ge 0.77$."]
- result: Peak optical depth of H13CN and H13CO+ J=2-1 lines = 0.10-0.15 ± not stated dimensionless [Optical Depth: "In contrast, the H$^{13}$CN and H$^{13}$CO$^{+}$ lines are optically thin in both transitions, with $\tau_{\rm max}\!\sim\!0.10$–0.15 for the *J*=2–1 lines and $\tau_{\rm max}\!\sim\!0.04$–0.05 for the *J*=3–2 lines."]
- result: Peak optical depth of H13CN and H13CO+ J=3-2 lines = 0.04-0.05 ± not stated dimensionless [Optical Depth: "In contrast, the H$^{13}$CN and H$^{13}$CO$^{+}$ lines are optically thin in both transitions, with $\tau_{\rm max}\!\sim\!0.10$–0.15 for the *J*=2–1 lines and $\tau_{\rm max}\!\sim\!0.04$–0.05 for the *J*=3–2 lines."]
- result: Continuum covering factor lower limit from HCN J=2-1 saturation = 0.8 ± not stated dimensionless [Optical Depth: "If we assume that the optical depth becomes infinite at the absorption minimum, Equation (\[eq:taudef\]) yields a lower limit of $f_{\rm c} \sim 0.8$, which is consistent with the constraint $f_{\rm c} \ge 0.77$."]
- limitation (authors): The Band 3 and Band 4 observations were separated by ~9 months (October 2016 to July 2017) without simultaneous millimeter monitoring, though a few percent variability would shift T_CMB by < 0.1 K. [Time Variability: "The Band 3 and Band 4 observations used in this study are separated by approximately nine months (from October 2016 to July 2017)"]
- limitation (authors): The -6 km/s component cannot constrain f_c due to lack of saturation, leaving its T_ex uncertain. [HCN, HCO+, and HNC: "In contrast, the $-6\,\mathrm{km\,s^{-1}}$ component shows no evidence of saturation, preventing a meaningful constraint on $f_\mathrm{c}$ in that velocity range; consequently, the associated $T_\mathrm{ex}$ remains uncertain."]
- limitation (authors): H13CN and H13CO+ transitions have low S/N (~3), limiting their statistical significance. [Summary and Future Prospects: "The excitation temperatures derived from H$^{13}$CN and H$^{13}$CO$^{+}$ are also consistent with the prediction of the standard Big Bang model, although their statistical significance is limited by the lower S/N of the data."]
- not stated (card): Exact CASA version and UVMULTIFIT version used for data reduction and visibility fitting; Rest frequencies, Einstein A coefficients, level energies, and partition function values/tables adopted for HCN, HCO+, HNC, H13CN, and H13CO+; Exact velocity ranges defining line-free continuum channels used in UVMULTIFIT to determine peak positions and normalize the absorption spectra; Explicit mathematical…

### 2017MNRAS.464.4624S: GRB 110715A: the peculiar multiwavelength evolution of the first afterglow detected by ALMA (2017; transients; multi_facility_alma_minor)
- question: What are the physical parameters of the jet and environment of GRB 110715A, constrained by broadband afterglow modelling of 17-band follow-up including the first ALMA GRB afterglow observation?
- step 1: Fit broadband afterglow with numerical forward-shock model
  - method: Numerical top-hat jet forward-shock model with energy injection or wind termination shock, fitted with Bayesian inference to X-ray, UV/optical/NIR, submm and radio data [Model and fitting description: "The best fit model parameters are found using Bayesian inference using the MultiNest tool (cite: 2009MNRAS.398.1601F)."]
  - software: MultiNest
  - parameter: Flat (uniform/log-uniform) priors on all parameters except Galactic reddening (Gaussian, mu=0.56, sigma=0.04) [Table 5: "(c) $\mu$ = 0.56, $\sigma$ = 0.04"]
  - parameter: UVOT UV filters and u band excluded in best fits [Model and fitting description: "We excluded the upper limits from the UV filters of UVOT as well as observations using its $u$-band filter"]
  - assumption: SMC-like host extinction curve [Model and fitting description: "we also determine the host dust extinction in the fit, which we assume follows an SMC-like extinction curve"]
  - fitting: MultiNest Bayesian inference; models CM, WM, TS compared via evidence and reduced chi2 [Model and fitting description: "We chose three different types of models that we expect have this behaviour"]
  - validation: Grid of 36 fits with different data cuts; none statistically good [The best fit: "However, none of them is either a statistically good fit or can fully explain the temporary flux increase at $\sim$0.3 days."]
- result: TS model electron index p = 1.8148 ± 0.0041 dimensionless [Table of best fit parameters: "$1.8148 \pm 0.0041$"]
- limitation (authors): Poor temporal sampling limits constraints [Conclusions: "This shows the need for better broadband sampling and more complex models"]
- not stated (card): ALMA calibration, CASA version, flux calibrator and imaging details; How the 4.9 mJy ALMA flux was measured (inherited from De Ugarte Postigo 2012); Full photometric table is only online; MultiNest settings (live points, tolerance); Likelihood form and systematic error treatment

### 2014ApJ...796....1T: Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE (2014; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Do gravitational torques from the central binary drive angular momentum exchange and infall in the circumbinary disk of L1551 NE, as seen in non-axisymmetric dust features and gas velocities?
- step 4: Hydrodynamic simulation of binary + circumbinary disk
  - method: 3D AMR isothermal simulation in a rotating frame with sink particles, gas injected at boundary with specific angular momentum for 300 AU centrifugal radius; adopt state after ~20 orbits [4.1 Nature of the Circumbinary Disk: "We adopted the simulation result after the $\sim$20 orbital periods of the binary ($\sim$4 $\times$ 10$^{4}$ $yr$)."]
  - software: SFUMATO
  - parameter: Box 1740 AU, finest cell 0.85 AU, sink radius 3.4 AU, n_inj=1.5e5 cm-3, T=13.5 K [Table 2: "Gas Number Density at the Boundary | 1.5 $\times$ 10$^{5}$ cm$^{-3}$"]
  - assumption: Circular binary orbit, isothermal gas, self-gravity ignored, disk coplanar with orbit [C.1 Model of the Hydrodynamic Simulation: "The self-gravity of the gas can be safely ignored"]
  - validation: Tested T=25 K with no significant difference in gas distributions [4.1 Nature of the Circumbinary Disk: "we confirmed that using a temperature of 25 K does not produce any significant differences in the gas distributions in our hydrodynamic simulations"]
- result: Model mass infall rate onto circumbinary disk = 3.3e-6 ± not stated Msun yr-1 [4.1 Nature of the Circumbinary Disk: "which give a comparable mass-infall rate from the envelope to the circumbinary disk of 3.3 $\times$ 10$^{-6}$ $M_{\odot}~yr^{-1}$"]
- limitation (authors): Missing flux and outflow complicate other lines near systemic velocity; temperatures in hydrodynamics (isothermal 13.5 K) and radiative transfer (power law) are inconsistent. [2 ALMA Observation and Data Reduction: "Closer to the systemic velocity, the spatial-kinematic structure in the other lines is complicated by the effects of missing flux as well as an outflow (see Appendix A)."]
- not stated (card): CASA version used for calibration and imaging; Clean threshold, mask, niter, cell and image size, and whether multiscale was used; Line-free channel ranges for continuum and constant continuum level; Details of the Keplerian subtraction implementation and Gaussian fit procedure; Simulation initial conditions, hydrodynamic code (SFUMATO modified) not public; simobserve inputs and noise settings; P…

### 2025MNRAS.541...71M: ALMA millimetre-wavelength imaging of HD 138965: new constraints on the debris dust composition and presence of planetary companions (2025; debris_disks, exoplanets; observational_alma_primary)
- question: What are the radial extent, width and inclination of the HD 138965 outer debris belt in ALMA 1.3 mm imaging, what dust composition fits, and what limits follow on the dust albedo and on planetary companions
- step 6: Constrain scattered-light brightness, albedo and companion masses from imaging
  - method: Inject model discs into SHARDDS data and reduce with classical ADI; RSM contrast curve converted to mass with AMES-COND; HST/ACS surface-brightness limit converted to albedo limit [3.5 Constraints from scattered light: "we inject model discs with an architecture consistent with the ALMA observation into the data cube. The cube was then reduced and stacked using the classical ADI algorithm."] [3.5 Constraints from scattered light: "The masses were converted from the measured contrast using the AMES-COND grid of models (cite: 2001Allard)."]
  - software: Regime Switching Model
  - parameter: Ages 30 ± 10 Ma, 45 ± 5 Ma and 348 (+39/-54) Ma [3.5 Constraints from scattered light: "The mass limit as a function of separation was calculated for ages of 30 $\pm$ 10 Ma (our inferred age), 45 $\pm$ 5 Ma (Argus association membership), and 348$^{+39}_{-54}$ Ma (from *Gaia*)."]
  - validation: Model-based albedo cross-check from Q_abs and Q_sca (omega = 0.56 over all angles; ~0.1 for restricted scattering angles) [3.5 Constraints from scattered light: "We infer a scattering albedo of $\omega = 0.56$ over all angles at a wavelength of 1.6 $\mu$m"]
- result: Scattering albedo upper limit (HST/ACS) = <=0.09 ± not stated dimensionless [3.5 Constraints from scattered light: "resulting in a limit of $\omega \leq 0.09$ at optical wavelengths"]
- result: SHARDDS 5-sigma surface brightness limit at 2'' = 83 ± not stated uJy/arcsec^2 [3.5 Constraints from scattered light: "we obtain a 5-$\sigma$ upper limit of 83 $\mu$Jy/arcsec$^{2}$"]
- result: Minimum integrated disc brightness detectable in SHARDDS = ~10 ± not stated mJy [3.5 Constraints from scattered light: "We find a minimum brightness of around 10 mJy is required for the disc to be detected in the SHARDDS data."]
- result: Companion mass limits near 80 au from contrast (31, 45, 348 Ma) = 4, 5, 15 ± not stated M_Jup [3.5 Constraints from scattered light: "we obtain upper limits to the mass of any companion of 4$~M_{\rm Jup}$ ($t_{\star} =$ 31 Ma), 5$~M_{\rm Jup}$ ($t_{\star} =$ 45 Ma), and 15$~M_{\rm Jup}$ ($t_{\star} =$ 348 Ma)"]
- result: Model albedo over all angles at 1.6 um = 0.56 ± not stated dimensionless [3.5 Constraints from scattered light: "We infer a scattering albedo of $\omega = 0.56$ over all angles at a wavelength of 1.6 $\mu$m"]
- limitation (authors): Inner belt fixed from a pure-silicate run may bias the composition result [3.4 Spectral energy distribution: "This may introduce an inherent bias toward astronomical silicate being the best solution for the outer belt."]
- limitation (authors): Larger than expected flux calibration uncertainty from bad weather [2.1 ALMA: "This indicates a larger than expected flux uncertainty for the calibration, and therefore imaging, of HD 138965."]
- not stated (card): Whether the ALMA pipeline or manual calibration was used, and the CASA / pipeline version; Self-calibration, if any, and the exact flagging applied to the flux calibrator; How the 4 SPWs were combined for continuum, and which channels were line-free; tclean settings: image size, cell size, deconvolver, masking, clean threshold, uv taper; How the visibilities were binned for the Galario fit (bin w…

### 2022A&A...659L...1L: Size and albedo of the largest detected Oort-cloud object: Comet C/2014 UN<SUB>271</SUB> (Bernardinelli-Bernstein) (2022; solar_system; observational_alma_primary)
- question: Determine the diameter and albedo of Oort-cloud comet C/2014 UN271 (Bernardinelli-Bernstein) from thermal measurements.
- step 4: Determine nucleus surface-equivalent diameter and geometric albedo via NEATM
  - method: Apply Near-Earth Asteroid Thermal Model (NEATM) to the 0.128+-0.012 mJy nucleus flux combined with converted optical absolute magnitudes HV and HR, iterating once on albedo and running 40,000 Monte Carlo realizations for uncertainties. [abstract: "From NEATM modelling combined with the $H_r$ magnitude, we determine a surface-equivalent diameter of 137$\pm$17 km and a red geometric albedo of 5.3$\pm$1.2 %."] [Nucleus diameter and albedo: "so iterating once on the albedo in NEATM was sufficient."]
  - parameter: Beaming factor eta = 1.175+-0.42 (restricted to >0.6) [Nucleus diameter and albedo: "we adopted a beaming factor $\eta$ = 1.175$\pm$0.42, based on measurements of 85 Centaurs and TNOs (cite: lellouch13; lellouch17)."] [Nucleus diameter and albedo: "In doing so, we restricted $\eta$ values to be $>$0.6 (cite: mommert12), as well as $\epsilon_b$ $<$ 1 and $\epsilon_r$ $<$ 1."]
  - parameter: Bolometric emissivity epsilon_b = 0.90+-0.06 (<1) and relative radio emissivity epsilon_r = 0.70+-0.13 (<1) [Nucleus diameter and albedo: "We also specified a bolometric emissivity $\epsilon_b$ = 0.90$\pm$0.06 and a *relative* radio emissivity $\epsilon_r$ = $\epsilon_{mm}$ / $\epsilon_b$ = 0.70$\pm$0.13"]
  - parameter: HV = 8.21+-0.05, HR = 7.75+-0.05, V-R = 0.46+-0.02, phase integral q ~ 0.4 [Nucleus diameter and albedo: "yielding $H_V$ = 8.21$\pm$0.05, $H_R$ = 7.75$\pm$0.05, and V-R = 0.46$\pm$0.02, i.e. $p_R$ = 1.11$\pm$0.02 $p_V$."] [Nucleus diameter and albedo: "(where a reasonable value of $q$, the phase integral, is $\sim$ 0.4)"]
  - assumption: 100% of measured 0.128+-0.012 mJy thermal flux comes from the nucleus; V_sun = -26.76, (V-R)_sun = 0.35 [Estimate of coma contribution: "In the rest of the paper, the measured thermal flux of 0.128$\pm$0.012 mJy is attributed to the nucleus only."] [Nucleus diameter and albedo: "Using V$_{\odot}$ = -26.76 and (V–R)$_{\odot}$ = 0.35, one obtains $D$ = 1330 km /$\sqrt{p_V}$ 10$^{-0.2 H_V}$ from V band and $D$ = 1132 km /$\sqrt{p_R}$ 10$^{-0.2 H_R}$ from R band."]
  - fitting: Monte Carlo simulation with 40,000 realizations with Gaussian-added noise on flux and model parameters; error bars defined as central 68.3% of results [Nucleus diameter and albedo: "we randomly generated a large set (40,000) of synthetic data and model inputs, based on gaussian-added noise on each parameter at the appropriate level (cite: mueller11), solving for $D$ and $p_R$ in each case."] [Results and discussion: "Those provided best fit values and error bars (defined to include the central 68.3 % of the results) for the diameter and albedo."]
  - validation: Inferred apparent diameter of 9.6 mas is consistent with the point-like appearance (<40 mas) in the visibility curve. [Results and discussion: "This yields an apparent diameter of 9.6 mas at $\Delta$ = 19.68 au, consistent with the point-like appearance of the object in the visibility curve (Fig. [\[fig:fit_uv\]](#fig:fit_uv))."]
- result: Nucleus surface-equivalent diameter (D) = 137 ± 17 km [abstract: "From NEATM modelling combined with the $H_r$ magnitude, we determine a surface-equivalent diameter of 137$\pm$17 km and a red geometric albedo of 5.3$\pm$1.2 %."]
- result: Nucleus apparent angular diameter = 9.6 ± not stated mas [Results and discussion: "This yields an apparent diameter of 9.6 mas at $\Delta$ = 19.68 au, consistent with the point-like appearance of the object in the visibility curve (Fig. [\[fig:fit_uv\]](#fig:fit_uv))."]
- result: Red geometric albedo (p_R) = 5.3 ± 1.2 % [abstract: "From NEATM modelling combined with the $H_r$ magnitude, we determine a surface-equivalent diameter of 137$\pm$17 km and a red geometric albedo of 5.3$\pm$1.2 %."]
- result: Visible geometric albedo (p_V) = 4.9 ± 1.1 % [Results and discussion: "Unlike the size, the albedo of , $p_V$ = 4.9$\pm$1.1 %, is completely in line with that of other, typically much smaller, comets (cite: lamy04; campins02)."]
- limitation (authors): Lack of knowledge of nucleus shape and spin parameters (pole orientation and shape) prevents thermophysical modeling. [Nucleus diameter and albedo: "In the lack of knowledge of nucleus shape and spin parameters (pole orientation and shape), a thermophysical model is pointless, and we instead adopted a NEATM model"]
- limitation (authors): Visibility fitting cannot distinguish between disk sizes smaller than ~40 mas given the ~65 mas resolution and measurement S/N. [Estimate of coma contribution: "From $\chi^2$ analysis, visibility fitting cannot distinguish between disk sizes smaller than $\sim$40 mas, which is to be expected given the $\sim$65 mas resolution achieved and the measurements’ S/N."]
- limitation (authors): Diameter and albedo uncertainties are dominated by model input errors, principally the uncertainty on the relative radio emissivity epsilon_r. [Results and discussion: "We find $D$ = 137$\pm$17 km [^1] and $p_R$ = 5.3$\pm$1.2 %, where error bars are dominated by model errors – and principally by the uncertainty on $\epsilon_r$."]
- not stated (card): Exact CASA version and ALMA pipeline version used for initial data reduction; Software or task used for uv-plane visibility fitting (e.g., CASA uvmodelfit, GILDAS, or custom script); Ephemeris file or JPL Horizons solution ID used to track the comet and define the predicted position before applying the (-0.0955", -0.2555") offset; Imaging parameters (cell size, image size, deconvolver, number of …

### 2021MNRAS.502.5390P: A ∼75 per cent occurrence rate of debris discs around F stars in the β Pic moving group (2021; debris_disks; archival_reuse)
- question: What is the occurrence rate and what are the properties of debris discs around F stars in the 23 Myr-old beta Pic moving group compared to other young moving groups and older field stars, and what explains the rapid decay in fractional lum…
- step 6: Compare populations, model evolutionary detection rates, and derive minimum planetesimal sizes
  - method: Verify Teff stability across age with MESA; compare detection rates across BPMG, 45 Myr, 150 Myr, and DEBRIS samples using Fisher's exact test; compute completeness grids in f_d vs R_BB space; simulate 100,000 evolved 92-star samples with … [Stellar population at different ages: "We use the “Modules for Experiments in Stellar Astrophysics” (cite: paxton-et-al-2011; paxton-et-al-2013; paxton-et-al-2015; choi-et-al-2016) to check the evolution of stellar temperature over time."] [Comparing the samples: "Using the DEBRIS sample as reference and Fisher’s exact test (cite: fisher-1956) we tested the hypothesis that the incidence rates for the BPMG, the 45 Myr group and the 150 Myr group are similar to the DEBRIS sample."]
  - software: MESA
  - parameter: Stellar masses 1.15 to 1.58 M_sun, [Fe/H]=0.0; Fisher test alpha = 0.05; grid R_BB = 0.01-1000 au, f_d = 10^-7 to 10^-2; evolution t_0 = 23 Myr (or 2 Myr), alpha = -1, -2; collisional e = i = 0.1, v_imp ~ 0.4 km/s [Stellar population at different ages: "We use the lowest ($1.15M_\text{sun}$) and highest ($1.58M_\text{sun}$) stellar masses in our sample of F stars to analyse its parameter space and assume a stellar metallicity of $[\text{Fe}/\text{H}]=0.0$."] [Fractional luminosity versus radius: "Using blackbody radii between 0.01 and 1000 au and fractional luminosities between $10^{-7}$ and $10^{-2}$ we generated a grid of fiducial discs assuming a pure blackbody model."]
  - assumption: Constant disc radius over time during fractional luminosity decay; collisional timescale equals system age (23 Myr for BPMG, 1000 Myr for HD 10647 and HD 109085); basalt and sand material laws [Same population scenario: "To describe the evolution process we use the collisional evolution model (§ [10](#sec:collisions)) and assume that the disc radius stays constant while the fractional luminosity decreases over time."] [Minimum sizes of planetesimals feeding …: "We calculate the minimum sizes of the planetesimals feeding the collisional cascade using eq. ([\[eq:timescale\]](#eq:timescale)) assuming that the collisional timescale, $t_\text{c}$, is similar to the age of the system."]
  - fitting: Monte Carlo simulation of 100,000 samples of 92 targets with Poisson 95% confidence level [Expected detection rates: "The dashed red line in Fig. [10](#fig:Evolution) shows that in this case the DEBRIS sample should have a detection rate of $41\pm10\,\%$ following Poisson statistics with a 95% confidence level."]
  - validation: Tested the Monte Carlo detection rate model on the BPMG sample itself (100,000 samples of 12 targets), reproducing the ~75% peak [Modelling detection rates: "To test the model we considered what it would predict for the BPMG, i.e. for a set of 100,000 samples each containing 12 targets randomly taken from the actual BPMG sample with the same age as the BPMG."]
- result: 45 Myr moving group F-star disc detection rate (total / FIR) = 37.9 / 55.0 ± +15.2/-11.3 / +22.1/-16.3 % [Other young moving groups: "| 45 Myr | 11 | 29 | 20 | $37.9^{+15.2}_{-11.3}$ | $55.0^{+22.1}_{-16.3}$ |"]
- result: 150 Myr moving group F-star disc detection rate (total / FIR) = 15.4 / 28.6 ± +20.3/-9.9 / +37.7/-28.5 % [Other young moving groups: "| 150 Myr | 2 | 13 | 7 | $15.4^{+20.3}_{-9.9}$ | $28.6^{+37.7}_{-28.5}$ |"]
- result: DEBRIS field F-star disc detection rate = 22.8 ± +6.2/-4.9 % [Field stars: "Thus, we update the number of detections for F stars in the DEBRIS sample to 21 out of 92 targets leading to a detection rate of $22.8^{+6.2}_{-4.9}$%."]
- result: Predicted DEBRIS detection rate from t^-1 collisional evolution of BPMG = 41 ± 10 % [Expected detection rates: "The dashed red line in Fig. [10](#fig:Evolution) shows that in this case the DEBRIS sample should have a detection rate of $41\pm10\,\%$ following Poisson statistics with a 95% confidence level."]
- result: Estimated mass of embedded planetary perturbers clearing dust in 100 Myr = 20 to 170 ± not stated M_earth [Fast depletion: "We find masses between 20 and 170 earth masses (corresponding to 1 and 10 Neptune masses)."]
- limitation (authors): Small number of targets in the BPMG (12 stars) and small number of spatially resolved discs limit the statistical significance of radius distribution comparisons. [Abstract: "However, this difference is not statistically significant due to the small number of targets."]
- limitation (authors): HD 173167 and several stars in the 45 Myr and 150 Myr moving groups lack far-infrared photometry beyond 22 um (or only have IRAS upper limits), preventing firm conclusions on cold disc presence for those stars. [Notes for particular targets: "The star HD 173167 only possesses photometric data up to 22$\mu$m so that we cannot draw any conclusions about a possible far-infrared excess."]
- limitation (authors): High ALMA upper limits for HD 14082A (<5.8 mJy) and HD 29391 (<3.5 mJy) due to the 14" phase-center offset (46% primary beam response) for HD 14082A and the small 0.2" beam for HD 29391. [ALMA reduction procedure: "The high values for the upper limits are caused by the relatively small beam used for the observation of HD 29391 and the fact that HD 14082A is significantly offset from the phase center, increasing the already high RMS of that observation."]
- not stated (card): Exact CASA and pipeline versions used for initial calibration of each individual archival ALMA project; tclean cell sizes, image dimensions, stopping thresholds, and multiscale scale sizes; Underlying weighting scheme (natural or Briggs robust value) used alongside the 0.7" uv-taper for HD 164249; Whether Phase-center shifting (fixvis) was applied before concatenating multi-epoch ALMA datasets to…

### 2025ApJ...989L..22B: Worlds Next Door: A Candidate Giant Planet Imaged in the Habitable Zone of α Centauri A. I. Observations, Orbital and Physical Properties, and Exozodi Upper Li… (2025; exoplanets, debris_disks, stellar_physics; multi_facility_alma_minor)
- question: Search for planets and exozodiacal disk emission in α Centauri A’s habitable zone; improve the stellar ephemeris with ALMA astrometry.
- step 4: Determine planet and exozodi detection limits
  - method: Convert Paper II sensitivity maps to blackbody temperatures; inject PSF-convolved exozodi models into MIRI datacubes and assess recovery. [Planet Detection Limits with JWST/MIRI: "We convert the 5$\sigma$ and S/N = 5 flux sensitivities (see Paper II) to effective temperatures ($T_{\rm eff}$) assuming a blackbody model and a typical planet radius of 1 $R_{\rm Jup}$"] [Exozodi Model Description: "we injected a number exozodiacal cloud models into the processed $\alpha$ Cen datacubes to set limits on extended “exozodiacal" emission"]
  - parameter: ABA belt at 2–3 au; opening angle 5°; disruption threshold 10^7 erg g−1 [Exozodi Model Description: "an asteroid belt analogue (ABA) located between 2–3 au"] [Exozodi Model Description: "we further assume a belt opening angle of 5$^\circ$, a size-independent catastrophic disruption threshold of $10^7$ erg g$^{-1}$"]
  - assumption: Exozodi coplanar with α Cen AB; grains 1/3 amorphous silicates and 2/3 organic refractories by volume. [Exozodi Model Description: "all exozodiacal disks considered here are assumed to be coplanar with the $\alpha$ Cen AB plane"] [Exozodi Model Description: "a grain composition of 1/3 amorphous silicates and 2/3 organic refractories by volume"]
  - validation: Model injection-recovery S/N; comparison with previous mid- and far-IR constraints. [Comparison with Previous Exozodi Search…: "The results of the injection-recovery analysis of our various exozodi models, presented in Paper II (cite: Aniket2025), are summarized by the corresponding S/N values"] [Comparison with Previous Exozodi Search…: "Excesses of our model disks in the far-IR for *Herschel* PACS70 and PACS100 observations are of even lower significance, consistent with previous non-detections."]
- result: S/N = 5 planet temperature sensitivity at 1–2 arcsec for 1 RJup = ≈250 ± not stated K [Planet Detection Limits with JWST/MIRI: "The MIRI F1550C observations are sensitive to $T_{\rm eff}\approx$ 250 K (1 $R_{\rm Jup}$) planets between 1$''$–2$''$ for a S/N = 5 detection threshold."]
- result: Coplanar exozodi luminosity-based sensitivity ZL = ≈5 ± not stated dimensionless [Comparison with Previous Exozodi Search…: "these observations are sensitive to emission from an exozodiacal cloud that is coplanar with the binary orbit at a level of $Z_L\!\approx\!5$ or $Z_\Sigma\!\approx\!8$"]
- result: Coplanar exozodi surface-density-based sensitivity ZΣ = ≈8 ± not stated dimensionless [Comparison with Previous Exozodi Search…: "these observations are sensitive to emission from an exozodiacal cloud that is coplanar with the binary orbit at a level of $Z_L\!\approx\!5$ or $Z_\Sigma\!\approx\!8$"]
- limitation (authors): Only one JWST sighting; planet status cannot be confirmed. [Conclusions: "However, with only a single sighting by JWST, the candidate cannot be unambiguously confirmed as a bona fide planet."]
- limitation (authors): S1 orbit cannot be uniquely constrained; modeling links S1 and C1. [Orbital Modeling of $S1$ + $C1$: "With only a single JWST/MIRI sighting (and non-detections at two other epochs), it is challenging to uniquely constrain the orbit of $S1$."]
- limitation (authors): Two photometric points leave substantial atmospheric degeneracies. [Planet Atmospheric Models: "Given the numerous atmospheric parameter degeneracies involved in fitting two photometric data points"]
- not stated (card): 2023 ALMA spectral-window centers, bandwidths, channelization and selected continuum channels.; 2023 ALMA array configurations, baselines, antenna counts and synthesized beams.; ALMA pipeline and software versions, calibration scripts, flux/bandpass calibrators and flagging.; ALMA imaging task, weighting, pixel scale, image dimensions, deconvolution and any self-calibration.; Position estimator a…

### 2024A&A...691A..70N: Disruption of a massive molecular cloud by a supernova in the Galactic Centre: Initial results from the ACES project (2024; milky_way_ism; large_program_or_survey)
- question: What is the origin of the massive ring-like molecular structure M0.8-0.2 in the Galactic Centre (young-star feedback, supernova feedback, cloud-cloud collision, shear, or line-of-sight coincidence)?
- step 6: Compare ring energetics with supernova feedback
  - method: Compare kinetic energy to ~10^51 erg per SN with coupling efficiency; estimate minimum number of SNe; test hypernova and Sigma-r relation [4.2 Feedback from supernova(e): "To derive an approximate minimum number of SNe required to power the expansion of the structure, we assumed a generous coupling efficiency of 30$\%$ and an injected energy of $10^{51}$ erg."]
  - parameter: Coupling efficiency 30%, injected energy 1e51 erg per SN [4.2 Feedback from supernova(e): "we assumed a generous coupling efficiency of 30$\%$ and an injected energy of $10^{51}$ erg"]
  - assumption: Energy of multiple SNe is additive [4.2 Feedback from supernova(e): "Assuming the impact of multiple SNe is additive"]
  - validation: Checked against X-ray, radio spectral index, magnetic field geometry and Sigma-r relation [4.2 Feedback from supernova(e): "We also checked for consistency with the typical relationship held by SNRs between radio surface brightness and size"]
- result: Minimum number of SNe to power the expansion = 8 ± not stated dimensionless [4.2 Feedback from supernova(e): "we find eight SNe are required"]
- limitation (authors): Expansion velocity is a lower limit because of projection effects [3.2 Kinematics and expansion: "We acknowledge that this estimate is a lower limit due to projection effects"]
- limitation (authors): Three-dimensional geometry unknown; effects of clustered SNe not well understood; comprehensive kinematic analysis left to future work [3.3 Mass, energy, and momentum: "In the absence of prior knowledge regarding the three-dimensional structure of the molecular cloud"]
- not stated (card): Exact ACES pipeline modifications (size mitigation, divergent-clean fixes), weighting/robust, cell size, image size, deconvolver and masks for the cubes; Continuum subtraction method and line-free channels for the line cubes; Feathering parameters (uv cutoffs, scaling factor) for ACA/TP/12 m and for the GBT combination; How the four mosaics were stitched and the weighting scheme used; Exact area/…

### 2020A&A...633A.115K: ALMA and NACO observations towards the young exoring transit system J1407 (V1400 Cen) (2020; exoplanets, debris_disks; observational_alma_primary)
- question: Can thermal emission from the putative ring system that occulted J1407 in 2007 be directly detected with ALMA and NACO, and what are its orbital parameters?
- step 3: NACO PCA-ADI contrast and mass limits
  - method: PynPoint PCA with 5 components, fake companion injection, Mawet14 small-sample correction, AMES-Cond conversion to mass [3 Observations with NACO: "We determined that 5 PCA components is a reasonable compromise between speckle removal and sky background sensitivity"]
  - software: PynPoint
  - parameter: 5 sigma contrast; separations 0.14-1.20 arcsec in 0.054 arcsec steps; 60 deg PA increments [3 Observations with NACO: "at various angular separations (0.14 to 1.20 arcsec in 0.054 arcsecond steps) and position angles (at 60 degree increments starting from 0 degrees)"]
  - assumption: age 16 Myr (Sco-Cen) [3 Observations with NACO: "assume an age of 16 Myr corresponding to the age of Sco-Cen"]
  - validation: Fake companion injection to correct flux loss [3 Observations with NACO: "fake point sources are injected at several radii from the star into the data, and then the recovered flux is measured after the pipeline data reduction."]
- result: NACO mass limit at 30 au = 6 ± not stated MJup [3 Observations with NACO: "down to $6M_{Jup}$ at 30au (0.25 arcsec) and dropping to less than $4M_{Jup}$ beyond 100au"]
- limitation (authors): Second ALMA epoch needed to confirm via proper motion [8 Conclusions: "An observation with ALMA three or more years after the 2017 detection will show this proper motion with enough significance"]
- not stated (card): Image size, cell size and any clean threshold/iterations for the ALMA image; Exact ALMA MOUS/execution identifiers and pipeline version; Whether all three executions were concatenated and how; Grain size distributions and mass settings used in MCMax grid; Imfit region/fitting details; NACO reduction parameters beyond PCA=5 (centering, frame selection, data archive ID)

### 2020ApJS..251...14H: CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone (2020; milky_way_ism, star_formation; multi_facility_alma_minor)
- question: Which compact sources (<10'', ~0.4 pc) exist in the 1.3 mm SMA CMZoom continuum maps of the Central Molecular Zone, what are their properties and completeness, and what do they imply for CMZ star formation potential?
- step 3: Completeness and false-positive from simulated observations
  - method: Inject 10 point sources, simobserve, tclean, make RMS map, dendrogram and prune, count recovered sources [3.2 Source Recovery and Simulated Obser…: "A given point-source is considered to be recovered if its coordinates are located anywhere within a pruned leaf."]
  - software: CASA simobserve, CASA tclean, AATM
  - parameter: masses from flux assuming Td = 20 K [3.2 Source Recovery and Simulated Obser…: "we assume a constant dust temperature of 20K"]
  - assumption: Point-source-like emission model [3.2 Source Recovery and Simulated Obser…: "can be modeled by point-source-like emission for the purposes of this simplistic completeness estimate."]
  - validation: Completeness resilient to atmospheric variation [3.2 Source Recovery and Simulated Obser…: "The completeness results for our catalogs constructed from the simulated observations is resilient to variations typical in atmospheric conditions"]
- result: 95% completeness mass, robust = 80 ± not stated Msun [3.2 Source Recovery and Simulated Obser…: "point-sources above 80 solar masses, under the typical observational conditions for the *CMZoom* survey, are detected with more than 95% completeness"]
- result: 95% completeness mass, high-completeness = ~50 ± not stated Msun [4.5 High-Completeness Catalog: "with a 95% completeness of $\sim 50$ M$_\odot$ (assuming T$_d$=20K)"]
- limitation (authors): Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2 [3.2 Source Recovery and Simulated Obser…: "These mass completeness estimates account only for the observational biases in observing point-source-like emission"]
- not stated (card): Exact dendrogram parameter values in the appendix-referenced setup (min_value, min_npix, min_delta numeric values beyond 3 MJy/sr scaling); Access/processing of CMZoom SMA maps from Dataverse versus Paper I imaging details; Simulated observation antenna configuration, integration time and weather settings; Herschel temperature map not yet published (in prep.); Exact point-source flux values and m…

### 2019A&A...623A.111H: Magnetic field at a jet base: extreme Faraday rotation in 3C 273 revealed by ALMA (2019; agn_and_quasars; observational_alma_primary)
- question: What is the Faraday rotation measure and magnetic field structure at the jet base of 3C 273, probed by full-polarization ALMA 1 mm observations?
- step 2: Estimate systematic uncertainties
  - method: 100 Monte Carlo realizations perturbing gain terms with Gaussian noise (Table A.1) [2. ALMA observations and data reduction: "We report the standard deviation of the 100 MC simulations as the uncertainty for each parameter in Table 1."]
  - parameter: D-terms 1%, X-Y phase 2 deg, X-Y bandpass 0.1% and 0.5 deg, thermal 8.5e-5 Jy [Table A.1: "D-terms (real and imag) 0 1%"]
  - assumption: Noise parameters are educated guesses [Appendix A: "The noise parameters given in Table A.1 are based on an educated guess"]
  - validation: Sinusoidal Stokes V vs parallactic angle amplitude consistent with MC uncertainty [Appendix A.2: "which indicates that our Monte Carlo estimates of polarimetric uncertainties are realistic"]
- limitation (authors): Limited wavelength coverage and angular resolution prevent distinguishing models [4. Discussion: "because of the limited wavelength coverage and angular resolution, our observations cannot distinguish between the two cases"]
- not stated (card): Solution intervals for gaincal self-calibration and bandpass; Initial and final bandpass/polarization calibrator details beyond 3C279; Fitting priors/sampler and initial values for qu-fitting; multi-component fits are non-unique; RM synthesis weighting settings; Exact data used for lower-frequency RM fit and fit weighting

### 2024A&A...691A..57M: SPH modelling of AGB wind morphology in hierarchical triple systems and a comparison to observation of R Aql (2024; evolved_stars; theory_or_simulation_compared_to_alma)
- question: How do coplanar hierarchical triple systems shape AGB outflows, and could R Aql's complex wind be shaped by such a system?
- step 1: Run SPH simulations of triple and binary AGB winds
  - method: PHANTOM SPH with sink particles and wind injection; free-wind approximation; H I cooling [2.1 Input physics SPH model: "We perform hydrodynamic simulations of an AGB outflow in a hierarchical triple system with the smoothed-particle hydrodynamics (SPH) code PHANTOM (cite: phantom)."]
  - software: PHANTOM, REBOUND
  - parameter: M1=1.6, M2=0.4 Msun, ai=5 au, ao=35 au, Mdot=1.1e-6 Msun/yr, T1=2800 K, v_ini 8 or 15 km/s, M3=0.1/0.6/1.2 Msun [Table 1: "$a_{\rm{o}}$ | \[au\] | $35$ |"]
  - assumption: gamma = 1.2, mu = 2.38 [2.1 Input physics SPH model: "We adopt constant values of the polytropic index $\gamma = 1.2$ and the mean molecular weight $\mu = 2.38$"]
  - validation: Mardling & Aarseth stability criterion and REBOUND N-body integration over 1000 outer periods [2.2 Grid setup triples: "the orbit of all systems is integrated with the REBOUND N-body code (cite: rebound) over $1000$ outer orbital periods $P_{\rm o}$, to confirm the stability of the orbits."]
- result: Inner binary orbital period = 7.91 ± not stated yr [2.2 Grid setup triples: "The orbital period of the inner binary $M_{\rm 1}$–$M_{\rm 2}$ is $P_{\rm i} = 7.91 \, {\rm yrs}$"]
- result: Outer orbital period for M3=0.6 Msun = 128.5 ± not stated yr [2.2 Grid setup triples: "$P_{\rm o} = 143.0, 128.5 \, {\rm and}\, 115.8 \, {\rm yrs}$"]
- result: Measured flattening ratio, triple v08 models = ~0.5 ± not stated dimensionless [4.2 Impact of different wind velocity: "This measured $R_{\rm f}$ is approximately $0.5$ for all masses of $M_3$."]
- limitation (authors): Parameter space degenerate; no ALMA simulator applied; pulsations missing [5.2 Comparison to synthetic observation: "the SPH models lack some physics such as the impact of the stellar pulsations, that may affect the wind morphology"]
- not stated (card): ALMA project code and CASA/pipeline versions for the ATOMIUM R Aql data; SPH particle number and resolution; MAGRITTE grid/mesh settings, image resolution and velocity channel setup; Procedure used to measure arc spacing in observed channel maps; Why the simulated model was not convolved with the ALMA beam

### 2023PASJ...75..311K: Galaxy clusters at z ∼ 1 imaged by ALMA with the Sunyaev-Zel'dovich effect (2023; galaxy_clusters_and_sz; observational_alma_primary)
- question: Reveal the thermodynamic structure (pressure, temperature, density, entropy, cooling time) of two z~1 galaxy clusters, RCS J2319+0038 and HSC J0947-0119, from high-resolution ALMA Band 3 SZE images combined with Chandra, HSC and ACT data, …
- step 9: Test the origin of the ACT SZE centroid offset
  - method: Cluster-injection simulations in the real ACT map with model cluster and compact sources, re-running filtering and detection, plus comparison with Hilton21 position recovery statistics [4.5 Origin of the offset of the ACT SZE…: "We injected a model cluster and model sources to the real ACT map, re-ran filtering and cluster-detection procedures, and assessed the accuracy of the recovered cluster position."]
  - parameter: spectral index -0.7 assumed for the compact-source effect on peak y (at most 4%) [4.5 Origin of the offset of the ACT SZE…: "by at most $4\%$ for a spectral index of $-0.7$"]
  - validation: Compact sources too weak to produce offset; at S/N 5.2, 22% of injected clusters are recovered more than 30'' away [4.5 Origin of the offset of the ACT SZE…: "22% of the injected clusters in the simulations are recovered at $> 30''$ away from the position at which the cluster model was inserted"]
- result: Offset of ACT centroid from ALMA and Chandra centres, RCS J2319+0038 = ~30'' (230 h70^-1 kpc) ± not stated arcsec [3.2.1 RCS J2319+0038: "is offset from the centers of the ALMA and *Chandra* images by $\sim 30''$ (230 $h_{70}^{-1}$kpc)"]
- limitation (authors): Weak-lensing mass errors are very large due to the limited number of background galaxies [3.3 Galaxy density and weak lensing mass: "Note that the errors on $M_{500}$ from weak lensing are very large for these distant clusters, owing to the limited number of background galaxies."]
- limitation (authors): Redshift of HSC J0947-0119 is photometric [Introduction: "Given the lack of accurate spectroscopic measurements"]
- not stated (card): Field-centre coordinates and compact-source RA/Dec for both clusters are blank in the supplied text, so source positions for uvmodelfit/subtraction and the cluster centres are missing; tclean parameters beyond those listed (niter, gain, cycle factors, convergence settings, field phase centres, gridder, image size) are only given by reference to Kitayama20; Exact line-affected frequency ranges and…

### 2019ESC.....3.2088S: Complex Organic Molecules in Star-Forming Regions of the Magellanic Clouds (2019; astrochemistry, star_formation; multi_facility_alma_minor)
- question: What is known about complex organic molecules in Magellanic Cloud star-forming regions, and how do observations compare with chemical models?
- step 3: Hot core model calculation for LMC/SMC ices
  - method: Taquet et al. dynamical-chemical model with fixed physical conditions and instant ice injection, ice abundances scaled by elemental depletions [5.2.2: "the physical conditions are fixed in time and the ices are injected instantaneously into the hot gas at $t=0$"]
  - parameter: n_H2 = 5e7 cm-3, T=150 K, zeta = 3e-17 s-1 [5.2.2: "$n_{\rm H_2} = 5 \times 10^7$ cm$^{-3}$, $T$=150 K, and a cosmic-ray ionization rate $\zeta = 3\times10^{-17}$ s$^{-1}$"]
  - validation: Compared model CH3OCH3/CH3OH and HCOOCH3/CH3OH ratios with N113 observations [5.2.2: "the observed CH$_3$OCH$_3$/CH$_3$OH ratios in A1 ($\sim$0.1) and B3 ($\sim$0.2) are about an order of magnitude higher than the calculated values ($\sim$0.01)"]
- result: Model CH3OCH3/CH3OH vs observed in LMC = model ~0.01 vs observed ~0.1 (A1), ~0.2 (B3) ± not stated dimensionless [5.2.2: "the observed CH$_3$OCH$_3$/CH$_3$OH ratios in A1 ($\sim$0.1) and B3 ($\sim$0.2) are about an order of magnitude higher than the calculated values ($\sim$0.01)"]
- limitation (authors): N159W-S ALMA analysis is preliminary, so no physical parameters given [4.2.1: "Since the analysis of the ALMA data is preliminary, we do not provide physical parameters for N159W–S"]
- not stated (card): Image size and cell size; Line-free channel ranges; Mask and clean threshold; Spectral resolution of the cube; LTE fitting method and software for N159W-S; Phase and bandpass calibrator details beyond names; Continuum subtraction method

### 2015ApJ...811L..19W: Gemini Planet Imager Observations of the AU Microscopii Debris Disk: Asymmetries within One Arcsecond (2015; debris_disks; multi_facility_alma_minor)
- question: What is the morphology of the AU Mic debris disk within 1 arcsec, and are there planets or compact clumps, as seen with GPI?
- step 3: Planet sensitivity
  - method: Contrast curve via Mawet et al. 2014, planet injection, Monte-Carlo completeness with COND models [Sensitivity to Planets: "we ran a Monte-Carlo analysis as described by (cite: nielsen) to determine the completeness of our data."]
  - assumption: COND evolutionary models; 23 Myr age [Sensitivity to Planets: "assuming COND models (cite: baraffe03)"]
- result: K1 candidate separation = 544 ± 4 mas [Sensitivity to Planets: "at a separation of 544$\pm$4 mas, a PA of $130.2\ensuremath{^\circ}$$\pm$$0.9\ensuremath{^\circ}$"]
- result: K1 candidate contrast = 1.1e-5 ± 0.3e-5 dimensionless [Sensitivity to Planets: "a *K1* contrast of 1.1$\pm$0.3 $\times 10^{-5}$"]
- limitation (authors): Disk brightness vs separation unreliable owing to residual PSF features; sliver at only 3.1 sigma and may arise from KLIP self-subtraction [Analysis of the Debris Disk: "We cannot rule out that the apparent morphology is influenced by KLIP self-subtraction."]
- not stated (card): ALMA data were not reprocessed; the reduced ALMA images came from MacGregor via private communication; GPI data availability not given

### 2018MNRAS.481.1976Z: The [C II] emission as a molecular gas mass tracer in galaxies at low and high redshifts (2018; high_z_galaxies; observational_alma_primary)
- question: Are z~2 main-sequence galaxies [C II] deficient, and what physical parameter drives [C II] luminosity (is [C II] an empirical molecular gas mass tracer)?
- step 9: Measure continuum fluxes and fit IR SEDs for L_IR, M_dust and <U>
  - method: Exponential-profile uv fits of the 450 and 850 um continuum, combined with Spitzer and Herschel photometry in Draine & Li model and modified black body fits [2.4 Continuum emission: "We extracted the continuum flux by fitting the data with an exponential profile, adopting the same procedure described in Section"] [2.4 Continuum emission: "we fitted the IR photometry with (cite: Draine2007) models, supplemented by the use of a single temperature modified black body (MBB) fit to derive a representative dust temperature of the ISM"]
  - software: GILDAS
  - parameter: L_IR integrated over 8-1000 um from SED fitting [Table 1: "IR luminosity integrated over the wavelength range 8 – 1000 $\mu$m as estimated from SED fitting"]
  - parameter: <U> = L_IR/(125 M_dust) [2.4 Continuum emission: "We also determined the average radiation field intensity as $\langle U\rangle = L_{\mathrm{IR}}/(125 M_{\mathrm{dust}})$"]
  - assumption: Modified black body beta = 2.0 [3.1 The [C II] deficit: "with fixed $\beta$ = 2.0 (the same as used in the SED fitting for our sample galaxies)"]
  - assumption: Measured fluxes with uncertainties used even when S/N < 3 instead of upper limits [2.4 Continuum emission: "In these fits we considered the measured *Spitzer*, *Herschel*, and ALMA flux (even if S/N $<$ 3, e.g. there is no detection)"]
  - fitting: Uncertainties on L_IR and M_dust by Monte Carlo simulations; points weighted by their uncertainties [2.4 Continuum emission: "Uncertainties on $L_{\mathrm{IR}}$ and $M_{\mathrm{dust}}$ were quantified using Monte Carlo simulations"] [2.4 Continuum emission: "The contribution of each photometric point to the best fit is weighted by its associated uncertainty."]
  - validation: Conclusions unchanged if upper limits are used in the fits; median L_IR and M_dust agree with literature MS values [2.4 Continuum emission: "If we were to use upper limits in these fits instead our conclusions would not have changed."]
- result: Range of L_IR (8-1000 um) of the sample = 3.5e11 - 1.2e12 ± not stated Lsun [2.4 Continuum emission: "lie between $3.5 \times 10^{11}$ – $1.2 \times 10^{12}$ L$_{\odot}$"]
- limitation (authors): Fluxes depend critically on the assumed model size taken from optical images [2.3.1 Individual [C II] detections: "However, the returned fluxes critically depend on the model size that we used and that we determined from the optical images."]
- limitation (authors): Source size cannot be constrained from individual sources because of low S/N [2.3.1 Individual [C II] detections: "Unfortunately, the size of the emission cannot be constrained from the data on individual sources, given the limited S/N ratio."]
- limitation (authors): Observed in a more extended configuration than requested, giving 5-10 times higher flux errors [2.2 Details of ALMA observations: "Our sources were therefore resolved."]
- not stated (card): CASA and pipeline version used for the Band 9 and Band 7 reductions, and whether the archive-delivered calibration was used as is; Flux, bandpass and phase calibrators and the Band 9 flux scale uncertainty; Whether any self-calibration was done; Which array (12-m / 7-m) and antenna numbers were used; Exact channel ranges (optimal channel range) used for each detection and the line-free channels u…

### 2020MNRAS.495.3409S: An ALMA survey of the brightest sub-millimetre sources in the SCUBA-2-COSMOS field (2020; high_z_galaxies; large_program_or_survey)
- question: Using ALMA 870-um continuum maps of the brightest SCUBA-2 sources in COSMOS: what is the intrinsic bright-end 870-um number count, how much does blending/multiplicity affect single-dish sources, and what is the photometric redshift distrib…
- step 4: measure total flux densities and correct flux boosting
  - method: uv-plane fit of Sersic profiles with proFit + galario + lmfit; correction from simulated injections [2.3 Flux Estimation: "Calibrated visibilities for each ALMA target were extracted using casa and modelled using a custom written code utilising three publically-available packages."]
  - software: CASA, proFit, galario, lmfit
  - parameter: five free parameters: R.A., Dec., flux density, half-light radius, axial ratio [2.3 Flux Estimation: "we leave five parameters of our model free to vary (R.A., Dec., flux density, half-light radius, and axial ratio)"]
  - parameter: optimisation repeated ten times from random starting values; lowest chi-square kept [2.3 Flux Estimation: "repeating the parameter optimisation ten times using randomly-selected starting parameter values"]
  - parameter: boosting correction from running median of recovered/input flux vs detection significance [2.3 Flux Estimation: "We use the running median to correct the flux densities of the sources in our AS2COSMOS catalogue, based on their detection significance"]
  - assumption: Sersic index fixed at n = 1 [2.3 Flux Estimation: "we fix the Sersic index at $n$ = 1"]
  - fitting: chi-square minimisation of observed vs model visibilities with lmfit [2.3 Flux Estimation: "and the lmfit non-linear optimisation suite"]
  - validation: 10^6 injected-source simulations; Sersic fluxes agree with aperture fluxes (after aperture correction) at the +/-1.5 per cent level [2.3 Flux Estimation: "agreement with the results of our Sersic profile fitting at the $\pm$ 1.5 per cent level, on average"] [2.3 Flux Estimation: "Each simulated data set is constructed by injecting a single model source into the residual data for a randomly selected AS2COSMOS target."]
- step 5: estimate completeness of the ALMA survey
  - method: Monte Carlo injection of model sources with random sizes and fluxes into residual maps, then rerun detection and modelling [2.3 Flux Estimation: "We run our source-detection and visibility-modelling procedures on the simulated data"]
  - parameter: axial ratio uniform 0-1; half-light radius uniform 0.05-0.30 arcsec [2.3 Flux Estimation: "drawn at random from a uniform distribution between zero and one, and 0.05$''$ and 0.30$''$, respectively"]
  - assumption: input fluxes sampled from the Hatsukade et al. counts with low flux cut-off 0.05 mJy [2.3 Flux Estimation: "is randomly sampled from the parameterised estimate of the sub- / millimetre counts presented by (cite: Hatsukade18)"]
  - validation: completeness > 99.9 per cent for sources with half-light radii < 1 arcsec [2.4 Completeness and Flux Recovery: "we estimate that our survey is $>$ 99.9 per cent complete for sources with half-light radii $<$ 1$''$"]
- step 6: compare ALMA and SCUBA-2 flux scales with end-to-end simulations
  - method: convolve ALMA model images with the SCUBA-2 beam; compare to observed and deboosted SCUBA-2 fluxes; 100 end-to-end S2COSMOS simulations to separate Eddington bias from line-of-sight multiplicity [2.4 Completeness and Flux Recovery: "We create 100 simulated maps of the S2COSMOS survey following the prescription in (cite: Simpson19)"]
  - parameter: emitters >= 0.05 mJy injected within 8.7 arcsec of recovered SCUBA-2 positions [2.4 Completeness and Flux Recovery: "that were injected within 8.7$''$ of each of the recovered SCUBA-2 positions"]
  - assumption: input counts model is the best-fit Schechter parameterisation (no clustering) [2.4 Completeness and Flux Recovery: "with the best-fit parameterisation for the sub-millimetre number counts as the input model"]
  - validation: median convolved ALMA/deboosted SCUBA-2 flux ratio 0.99 +/- 0.01 [2.4 Completeness and Flux Recovery: "we find a median ratio of convolved ALMA to deboosted SCUBA-2 flux density of 0.99 $\pm$ 0.01"]
- result: flux boosting of a 4.8 sigma source = 15 per cent ± not stated per cent [2.3 Flux Estimation: "On average the recovered flux density of a 4.8 $\sigma$ source in our simulation is boosted by 15 per cent"]
- result: average aperture correction = 1.44 ± 0.01 dimensionless [2.3 Flux Estimation: "average aperture correction of 1.44 $\pm$ 0.01"]
- result: median convolved ALMA / deboosted SCUBA-2 flux ratio = 0.99 ± 0.01 dimensionless [2.4 Completeness and Flux Recovery: "we find a median ratio of convolved ALMA to deboosted SCUBA-2 flux density of 0.99 $\pm$ 0.01"]
- limitation (authors): multiplicity is a lower limit because the sample is very incomplete near 1 mJy [3.3 Multiplicity: "our estimate of the multiplicity of SCUBA-2 sources is undoubtably a lower limit"]
- limitation (authors): observational constraints on projected versus associated companions are weak [3.3 Multiplicity: "current observational constraints on the relative mix of projected and associated companions in blended SMG maps are weak"]
- limitation (authors): simulation-based line-of-sight correction assumes no clustering [2.4 Completeness and Flux Recovery: "the statistical correction for line-of-sight multiplicity assumes no clustering"]
- not stated (card): tclean deconvolver, specmode/gridder, niter and the auto-masking parameters (sidelobethreshold, noisethreshold, etc.) behind the sigma thresholds; the exact uv-taper applied to each of the 182 maps and the ALMA execution blocks / CASA pipeline versions used for each of the seven archival projects; which archival project corresponds to which of the 24 archival S2COSMOS sources; SExtractor configur…

### 2025PASJ...77.1163H: ALMA deep field in SSA22: Reconstructed [C II] luminosity function at z = 6 (2025; high_z_galaxies; observational_alma_primary)
- question: Why two [C II] line emitter candidates in the ADF22 Cycle 2 data were spurious (statistics, TDM smoothing, non-Gaussian noise, technical problems), and how to reconstruct the [C II] luminosity function at z~6 with completeness and contamin…
- step 4: Inject artificial line sources in the visibility plane
  - method: Define Gaussian-profile sources per channel, build with cl.addcomponent, Fourier transform with ft, copy model into corrected data via uvsub reverse=True, then image [The Mock Observations, Artificial Sourc…: "We prepare a source model with `cl.addcomponent` and Fourier-transform the model using `ft`."] [The Mock Observations, Artificial Sourc…: "Then we use `uvsub` with a parameter reverse=True since the command is usually to subtract the model in UV-plane."]
  - software: CASA 4.5.3, cl.addcomponent, ft, uvsub
  - parameter: Peak S/N 2.0-7.0 in 0.5 steps (11), FWHM 36-396 km/s in 36 km/s steps (11), 121 parameter sets, 84 positions, 100 repeats, 1,016,400 sources [The Mock Observations, Source Injection: "Therefore, we inject artificial sources with 121 parameter sets of the artificial source."] [The Mock Observations, Source Injection: "Then 84 positions in total."]
  - assumption: Mean [C II] redshift z = 6.2 for flux to luminosity conversion [The Mock Observations, Source Injection: "assuming the average \[C ii\] redshift to be $z = 6.2$."]
  - assumption: Flat Lambda-CDM with Omega_M = 0.3, Omega_Lambda = 0.7, h = 0.7 [Introduction: "we adopt the standard $\Lambda$-CDM cosmology with a matter density $\Omega_{\rm M} = 0.3$, a cosmological constant $\Omega_{\rm \Lambda} = 0.7$, and a Hubble constant $h = 0.7$"]
  - validation: simobserve and cl.addcomponent injection results are identical [The Mock Observations, Artificial Sourc…: "Note that the results using `simobserve` and `cl.addcomponent` are identical."]
- step 5: Derive contamination rate Q and completeness C
  - method: Run clumpfind on smoothed S/N cubes of blank mocks (N_mock), real data (N_real) and injected cubes (N_out vs N_inj); Q = N_mock/N_real and C = N_out/N_inj as functions of (peak S/N, FWHM); fit error functions and classify into Categories I… [The Detection Methods, Detection Classes: "are the cumulative number of clumps in the real and the blank mock field without injected sources, respectively, as a function of $x$."] [The Detection Methods, Detection Classes: "We calculate the value of completeness $C(x)$ by injecting an artificial source and checking if the source is detected by the source-extracting process."]
  - software: clumpfind
  - parameter: x = (peak S/N, FWHM); Q and C fitted with error functions with parameters a1, b1, a2, b2 per FWHM [The Detection Methods, Detection Classes: "The results of $Q(x)$ and $C(x)$ can be approximated with the error function (e.g., (cite: hatsukade2016)):"]
  - assumption: Region considered where N_mock <= N_real and N_real > 0 [The Detection Methods, Detection Classes: "We consider the region where $N_{\rm mock} \leq N_{\rm real}$ and $N_{\rm real} > 0$"]
  - fitting: Error-function fit of Q(x) and C(x); sampler, priors, likelihood not stated [The Detection Methods, Detection Classes: "The results of $Q(x)$ and $C(x)$ can be approximated with the error function (e.g., (cite: hatsukade2016)):"]
  - validation: Detected ADF22 candidates fall at the boundary between Category II and III, consistent with non-detection in Cycle 5 [Results, The detectability: "According to our analysis, the detected sources are at the boundary between Category II and III, meaning the detections are likely affected by noise contamination."]
- result: False detections per datacube above 6 sigma (100 blank mock mosaics, previous source-finding method) = 0.43 ± 0.67 per datacube [abstract: "Using 100 blank mock-mosaic datasets, we show 0.43 $\pm$ 0.67 false detections per datacube with the previous source-finding method."]
- result: Contamination inflection point a1 vs FWHM = 2,4,...,22 channels = 6.50, 6.42, 6.50, 6.50, 6.50, 6.50, 6.18, 5.87, 5.67, 5.54, 4.94 ± not stated sigma [Table (fit parameters of Q): "6.50 | 6.42 | 6.50 | 6.50 | 6.50 | 6.50 | 6.18 | 5.87 | 5.67 | 5.54 | 4.94"]
- result: Completeness inflection point a2 vs FWHM = 2,4,...,22 channels = 4.71, 3.61, 3.03, 2.96, 2.40, 2.15, 2.16, 1.98, 1.00, 2.35, 1.71 ± not stated sigma [Table (fit parameters of C): "4.71 | 3.61 | 3.03 | 2.96 | 2.40 | 2.15 | 2.16 | 1.98 | 1.00 | 2.35 | 1.71"]
- limitation (authors): Simulated mock data do not necessarily reproduce real observation properties [The Mock Observations: "In this case, the dataset does not necessarily reproduce the properties of real observations."]
- limitation (authors): clumpfind cannot identify low-S/N clumps so a Gaussianity fit test was not done [Results, Statistical Fluctuation: "it is important to note that the clumpfind method is not capable of identifying clumps with low SN ratios; therefore, we did not perform this particular test."]
- limitation (authors): Observational constraints at high z are limited, so the LF shape is assumed [The LF Reconstruction: "Owing to the limitation of observational constraints at high-$z$, we make the simplest assumption"]
- not stated (card): clumpfind parameters other than the 'low' threshold of 4.5 (high threshold, step levels, minimum clump size); The weighting table used to weight N_cor by luminosity bin (referred to as Tab. weighting but not given in the text); tclean/clean parameters for the real and mock cubes (weighting, robust, cell size, deconvolver, niter, threshold, masking); Line-free channels or fit order used in uvconts…

### 2026ApJ...997..155M: The ALMA Survey of 70 µm Dark High-mass Clumps in Early Stages (ASHES). XIII. Core Mass Function, Lifetime, and Growth of Prestellar Cores (2026; star_formation, milky_way_ism; large_program_or_survey)
- question: What are the universality, power-law slope, lifetime, and mass growth properties of the prestellar core mass function (CMF) in the earliest stages of high-mass star formation within 70 μm dark IRDC clumps?
- step 3: Evaluate mass completeness, apply flux recovery correction, and select final core sample
  - method: Insert artificial Gaussian cores into continuum images at uniformly random positions where primary beam response > 40%, run astrodendro 5000 times to measure detection rate and flux recovery per mass bin, exclude 5 clumps with lowest compl… [Completeness: "We calculated the mass completeness by inserting an artificial Gaussian core into the continuum images and varying the core mass."] [Completeness: "We repeated the test 5000 times and calculated the mean detection rate per mass bin from region to region to determine the 90% completeness level."]
  - software: astrodendro
  - parameter: 5000 trials; primary beam response > 40%; 90% completeness threshold = 1.2 M_sun after excluding 5 clumps; flux correction applied where completeness > 0.5 [Completeness: "The inserted position of core center was uniformly random in a region where the primary beam response was higher than 40% to avoid cores located at the edge, consistent with the core identification process."] [Completeness: "After this selection, our sample ensures a 90% completeness level above 1.2 $M_\odot$, resulting in a final sample of 715 cores for the CMF analysis."]
  - assumption: Artificial cores have Gaussian profiles [Completeness: "We calculated the mass completeness by inserting an artificial Gaussian core into the continuum images and varying the core mass."]
  - validation: Compared CMF slopes before and after flux recovery correction [Completeness: "The CMFs of the selected 715 cores before and after flux correction are shown in the middle and right panels of Figure [1](#fig:cmf-all)."]
- step 4: Construct CMFs and fit power-law slopes
  - method: Construct differential histograms (using numpy Freedman Diaconis Estimator for bin edges), variable-bin complementary cumulative distributions, and unbinned distributions; fit power-law indices above 1.2 M_sun and evaluate 1sigma uncertain… [Core Mass: "The bin size was determined with a task in `numpy` of *histogram bin edges* as Freedman Diaconis Estimator (fd), which takes into account data size."] [Prestellar CMF: "Also, we performed the fitting using maximum likelihood estimates (MLE; Figures [3](#fig:cmf_prebound) (c) and (f)) as developed by (cite: Clauset09), following one of the ALMA-IMF studies by (cite: Louvet24) and implemented in the Python package, `powerlaw` (cite: Alstott14)."]
  - software: Numpy, powerlaw
  - parameter: M_min = 1.2 M_sun; 1000 Monte Carlo trials with mass scaling factor uniformly in 0.5-1.5 [Prestellar CMF: "The black lines represent the best fit of the power law index above the lowest 90% completeness level of 1.2 $M_\odot$, $dN/dM \propto M^\alpha$, $N(> \mathrm{log} M) \propto M^{\alpha +1}$, or $P(m) = - rac{\alpha +1}{M_{ m min}} \left( rac{m}{M_{ m min}} ight)^{\alpha}$."] [Prestellar CMF: "We multiplied a random value in the range of 0.5–1.5 for each core mass in one trial and produced the CMF. We repeated this simulation 1000 times and calculated a 1 sigma value coming from the mass uncertainty."]
  - assumption: Core mass uncertainty is 50% [Prestellar CMF: "Considering a 50% uncertainty in core masses (Section [3.1](#sec:mass)), we performed a Monte Carlo simulation to assess how the CMF changes."]
  - fitting: Power-law fitting to histograms/cumulative distributions and Maximum Likelihood Estimation (MLE) via powerlaw package above 1.2 M_sun [Prestellar CMF: "MLE determines the best-fit power-law slope directly from the unbinned data by maximizing the likelihood of the observed distribution, avoiding biases from histogram binning."]
  - validation: Compared three different CMF representations/fitting methods (differential histogram, variable-bin cumulative distribution, and unbinned MLE) [Prestellar CMF: "In addition to the standard differential histogram, to avoid arbitrariness of binning and to directly compare with other references, we also derived the complementary cumulative distribution with variable-size bins, Figure [3](#fig:cmf_prebound) (b) and 3(e), following the recommendations of (cite: MaizApellaniz05) an…"]
- result: Final selected core sample size (34 clumps) = 715 ± not stated cores [Completeness: "After this selection, our sample ensures a 90% completeness level above 1.2 $M_\odot$, resulting in a final sample of 715 cores for the CMF analysis."]
- result: Prestellar core candidates in selected sample = 461 ± not stated cores [Completeness: "Among the 715 cores in the middle panel, the numbers of prestellar core candidates, warm cores, and outflow cores are 461, 178, and 76, respectively."]
- result: Protostellar cores in selected sample = 254 ± not stated cores [Abstract: "We study the CMF in the earliest stage of high-mass star formation using 461 prestellar core candidates and 254 protostellar cores as a part of the ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES)."]
- result: Gravitationally bound prestellar cores in selected sample = 130 ± not stated cores [Prestellar CMF: "Our prestellar core sample consists of 461 cores without any signs of protostars detected by ALMA such as molecular outflows and warm gas tracers. It includes 130 gravitationally bound cores based on virial analysis."]
- result: 90% mass completeness level across all 39 clumps = 0.3-4.5 (median ~0.6) ± not stated M_sun [Completeness: "The completeness level ranges from 0.3–4.5 $M_\odot$ with a median of $\sim$0.6 $M_\odot$."]
- result: 90% mass completeness threshold for selected 34 clumps = 1.2 ± not stated M_sun [Completeness: "After this selection, our sample ensures a 90% completeness level above 1.2 $M_\odot$, resulting in a final sample of 715 cores for the CMF analysis."]
- result: CMF power-law slope (all selected cores, differential histogram before flux correction) = -1.92 ± 0.12 dimensionless [Completeness: "As expected from the recovered flux plot, the flux correction mostly affects low-mass cores near 1 $M_\odot$, and it makes a slightly steeper slope from -1.92$\pm$0.12 to -2.02$\pm$0.11."]
- result: CMF power-law slope (all selected cores, differential histogram after flux correction) = -2.02 ± 0.11 dimensionless [Completeness: "As expected from the recovered flux plot, the flux correction mostly affects low-mass cores near 1 $M_\odot$, and it makes a slightly steeper slope from -1.92$\pm$0.12 to -2.02$\pm$0.11."]
- result: CMF power-law slope (all selected cores, MLE) = -2.05 ± 0.04 dimensionless [Abstract: "The CMF, including both protostellar and prestellar cores, has a power-law slope of -2.05$\pm$0.04, shallower than Salpeter’s IMF slope of -2.35."]
- result: CMF power-law slope (gravitationally bound prestellar cores, MLE) = -2.32 ± 0.30 dimensionless [Abstract: "Conversely, the CMF of gravitationally bound, prestellar cores has a steeper slope (-2.32$\pm$0.30), indistinguishable from Salpeter’s slope."]
- result: CMF power-law slope range (prestellar core candidates across methods) = -2.65 to -2.38 ± not stated dimensionless [Prestellar CMF: "The best fit $\alpha$ was -2.65 to -2.38 for prestellar core candidates (including bound and unbound cores) and -2.53 to -1.83 for bound prestellar cores."]
- result: CMF power-law slope range (gravitationally bound prestellar cores across methods) = -2.53 to -1.83 ± not stated dimensionless [Prestellar CMF: "The best fit $\alpha$ was -2.65 to -2.38 for prestellar core candidates (including bound and unbound cores) and -2.53 to -1.83 for bound prestellar cores."]
- result: CMF power-law slope using getsf cores = -1.78 ± 0.12 dimensionless [Core Identification: astrodendro VS get…: "The power-law fit was applied to the CMFs with $M > 1.2 M_\odot$, and the best-fit parameters are $\alpha = -1.92\pm0.12$ and $-1.78\pm0.12$ for `astrodendro` and `getsf`, respectively."]
- limitation (authors): Core mass uncertainties are ~50%, largely from gas-to-dust mass ratio and dust opacity. [Core Mass: "The uncertainties of mass is $\sim$50%, largely contributed from the gas-to-dust mass ratio and the dust opacity (cite: Morii23)."]
- limitation (authors): Reference protostellar lifetime (0.2 Myr) has an uncertainty of about a factor of two, and the statistical lifetime analysis assumes a constant star formation rate within each clump. [Lifetime of Prestellar Cores: "As discussed in (cite: Valeille-Manet25), this has an uncertainty of about a factor of two."]
- limitation (authors): Limited sample size at the high-mass end causes the best-fit power-law index to depend slightly on the CMF representation and restricts discussion of later evolution from top-heavy CMF back to Salpeter IMF. [Prestellar CMF: "This figure shows that the power-law index $\alpha$ slightly depends on the representations of the mass distribution in such a limited sample size at the high-mass end."]
- not stated (card): ALMA calibration and imaging parameters (e.g., CASA version, tclean weighting, robust parameter, multiscale scales, continuum subtraction), which are deferred to Sanhueza et al. (2019) and Morii et al. (2023); Exact astrodendro parameters (min_value, min_delta, min_npix) used for core identification and artificial core recovery tests, deferred to Morii et al. (2023); Individual source distances a…

### 2021ApJ...923..121Y: ALMA Super-resolution Imaging of T Tau: r = 12 au Gap in the Compact Dust Disk around T Tau N (2021; protoplanetary_disks, star_formation; archival_reuse)
- question: Explore several au-scale substructures in the compact protoplanetary disks around the T Tau triple star system using sparse modeling super-resolution imaging of ALMA 1.3 mm continuum data.
- step 2: Super-resolution image reconstruction with Sparse Modeling (SpM) and evaluation of effective resolution and noise
  - method: Reconstruct image from self-calibrated visibilities using PRIISM ver.0.3.0 by minimizing cost function with chi-squared, l1-norm, and TSV regularizers; select optimal (Lambda_l, Lambda_tsv) via 10-fold cross-validation over 5x5 grid; evalu… [Imaging with Sparse Modeling: "The self-calibrated visibility data were adopted for the image reconstruction with the latest SpM imaging task, $\tt PRIISM$, ver.0.3.0 (cite: nakazato2020) working with $\tt CASA$."] [Imaging with Sparse Modeling: "In this study, we used the 10-fold CV implemented in $\tt PRIISM$ and searched for the optimal parameter set with $5\times5$ sets of regularization parameters, which are $\Lambda_{l} = (10^{3},10^{4}, ...,10^{7}$) and $\Lambda_{tsv} =(10^{7}, 10^{8}, ..., 10^{11}$)."]
  - software: PRIISM, CASA, DIFMAP
  - parameter: Lambda_l = 10^5, Lambda_tsv = 10^9 (optimal from 5x5 grid) [Imaging with Sparse Modeling: "In other words, the image of ($\Lambda_{l}$, $\Lambda_{tsv}$) $=$ ($10^{5},10^{9}$) is selected as the optimal one."]
  - parameter: N_iter = 1000, 10-fold CV [Imaging with Sparse Modeling: "In the imaging using $\tt PRIISM$, we used non-uniform fast Fourier transform (NuFFT) algorithms to compute the Fourier transform and perform iterative fitting of the model to visibility data ($N_{\rm iter} = 1000$) until the iteration algorithm converges."]
  - assumption: Non-negative brightness distribution constraint [SpM image and evaluation of its noise l…: "This is because non-negative constraints have been adopted in the SpM imaging algorithm, and artificial emissions with positive intensity may be present in the off-source area."]
  - fitting: Iterative convex optimization minimizing chi-squared + l1-norm + TSV cost function with NuFFT (N_iter = 1000); 2D Gaussian fit to injected 7.1 mJy point source. [Imaging with Sparse Modeling: "In the imaging using $\tt PRIISM$, we used non-uniform fast Fourier transform (NuFFT) algorithms to compute the Fourier transform and perform iterative fitting of the model to visibility data ($N_{\rm iter} = 1000$) until the iteration algorithm converges."] [Imaging with Sparse Modeling: "In the SpM images, effective resolution was evaluated with an elliptical Gaussian fit to the point source (see Figure 9)."]
  - validation: 10-fold cross-validation error (CVE), comparison of total fluxes above I_DT with CLEAN (>5 sigma), and comparison of radial visibility profiles and reduced chi-squared (1.18 for SpM vs 1.31 for CLEAN image). [Results, SpM image and evaluation of it…: "the total fluxes of these sources obtained from the SpM image above the $I_{\rm DT}$ level are generally consistent with the values obtained from the CLEAN image above $5\sigma$ levels."] [Comparison between CLEAN and SpM Images: "Finally, all the visibility models corresponding to the three images (CLEAN image, CLEAN model, and SpM) have resulted in the reduced $\chi^2$ of around unity: 1.31 for the CLEAN image, 1.18 for the CLEAN model, and 1.18 for the SpM, respectively."]
- result: Effective spatial resolution of optimal SpM image (theta_eff) = 0''.038 x 0''.027 (5 x 4 au) ± not stated arcsec (au) [Imaging with Sparse Modeling: "The reconstructed image for the optimal parameter provides the FWHM size (i.e., effective spatial resolution) of the point source, $\theta_{\rm eff} = 0''.038 \times 0''.027$ (or $5\times 4$ au) with a PA of $45.3^{\circ}$ and recovers a total flux of $7.9$ mJy ($\sim10\%$ higher than the input value)."]
- result: T Tau N 1.3 mm total flux density (SpM, >I_DT) = 174.4 ± not stated mJy [Disk Structure of T Tau N: "| T Tau N | 175.0 | 4.0 | 174.4 | 9.1 | $(04^{h}21^{m}59^{s}.4475$, $+19^{d}32^{m}06^{s}.1731)$ |"]
- result: T Tau Sa 1.3 mm flux density (SpM, >I_DT) = 7.1 ± not stated mJy [Disk Structure of T Tau N: "| T Tau Sa | $-$ | $-$ | 7.1 | 5.1 | $(04^{h}21^{m}59^{s}.4362$, $+19^{d}.32^{m}.05^{s}.5131)$ |"]
- result: T Tau Sb 1.3 mm flux density (SpM, >I_DT) = 0.8 ± not stated mJy [Disk Structure of T Tau N: "| T Tau Sb | $-$ | $-$ | 0.8 | 0.8 | $(04^{h}21^{m}59^{s}.4365$, $+19^{d}.32^{m}.05^{s}.6131)$ |"]
- limitation (authors): SpM image suffers from artificial positive emissions in off-source areas due to non-negative constraints and thermal/systematic noise. [SpM image and evaluation of its noise l…: "As described in (cite: yamaguchi2020), owing to both thermal and systematic noise, an SpM image suffers from (unexpected) positive emissions in its off-source area (i.e., outside the target source area)."]
- limitation (authors): T Tau Sa and Sb disk sizes (6x4 au and 7x3 au) are only slightly larger than the SpM effective resolution (5x4 au), so they are not sufficiently resolved and represent conservative upper limits. [Dust Emissions from T Tau Sa and Sb: "These disk sizes are slightly larger than the effective spatial resolution of the SpM image ($\theta_{\rm eff} = 5\times 4$ au) and not resolved sufficiently. Hence, these sizes should be considered to be the conservative upper limits."]
- limitation (authors): The T Tau N disk is optically thick at 1.3 mm, so the brightness temperature traces the disk atmosphere rather than the midplane, making derived dust surface densities and dust masses lower limits. [Physical Properties of T Tau N Disk: "It should be noted that a disk midplane temperature will generally be lower than $T_{\mathrm{br}}(r)$ at optically thick regions. Thus, dust surface densities (and dust masses) estimated in what follows would be lower limits in such a case."]
- not stated (card): Pixel size (cell size) and image dimensions (number of pixels) used in PRIISM SpM reconstruction and tclean; Spectral window bandwidths and channel averaging applied to the continuum visibilities prior to PRIISM and tclean; Exact numerical value of the DSHARP dust opacity kappa_nu,I at 225.5 GHz used in the surface density calculation; Clean threshold and masking strategy used during tclean and s…

### 2022A&A...663A..61P: Variations in the Σ<SUB>SFR</SUB> ‒ Σ<SUB>mol</SUB> ‒ Σ<SUB>⋆</SUB> plane across galactic environments in PHANGS galaxies (2022; nearby_galaxies, star_formation; large_program_or_survey)
- question: Test the universality of the 2D star-forming plane relating star formation rate surface density, stellar mass surface density, and molecular gas surface density across different galactic environments at 150 pc spatial resolution.
- step 6: Correlate single-galaxy environmental plane slopes with local physical and stellar population parameters
  - method: Select 8 galaxies satisfying environmental and detection criteria, fit C_*, C_mol, and C_norm per environment within each galaxy, compute environmental averages of 13 physical parameters, and compute the overall average weighted Pearson co… [What drives the environmental variation…: "To perform this exploration, we measure $C_{\star}$, $C_{\rm mol}$ and $C_{\rm norm}$ in each environment of each individual galaxy in our sample (following the same procedure detailed in Sec. [3.2](#sec:fit)), and search for correlations between the coefficients obtained in each environment, and a set of additional p…"] [What drives the environmental variation…: "Out of our sample, 8 galaxies satisfy the listed conditions (NGC 1300, NGC 1365, NGC 1512, NGC 1566, NGC 1672, NGC 3627, NGC 4303, NGC 4321)."]
  - software: PyMC3
  - parameter: Galaxy selection criteria: >= 3 environments, has bar and spiral arms, < 50% pixels removed by detection threshold (yields 8 galaxies with log M_* >= 10.6) [What drives the environmental variation…: "1. Probe at least three different environments. 2. Host galaxy has a bar and spiral arms. 3. Fraction of pixels removed due to the imposed detection threshold is $<50\%$."]
  - parameter: 50 Monte Carlo simulations per galaxy for correlation uncertainty [What drives the environmental variation…: "For each galaxy, the uncertainty in its correlation coefficient $\rho_{i}$ (i.e., between the plane coefficients and each one of the parameters listed) is estimated by performing $50$ Monte-Carlo simulations, perturbing the measured $C_{\star}$ and $C_{\rm mol}$ for each environment in each iteration."]
  - assumption: Typical stellar scale height h_* = 300 pc for free-fall time calculation; atomic gas neglected in mid-plane hydrostatic pressure P_h [What drives the environmental variation…: "and $h_{\star}$ is the typical stellar scale height, for which we adopt a value of $300$ pc (cite: Utomo2018)."] [What drives the environmental variation…: "This approach neglects the contribution from atomic gas, however, the relative contribution of atomic gas with respect to molecular gas in these galaxies and this regime of $\Sigma_{\rm mol}$ values is expected to be subdominant (cite: Bigiel2008; Schruba2019)."]
  - fitting: Weighted Pearson correlation coefficient averaged across the 8 galaxies [What drives the environmental variation…: "We compute the mean of the distribution of these quantities in each environment (considering only those pixels that were used for the fitting of the plane), and measure the weighted Pearson’s correlation coefficient ($\rho$) between these environ­mental-averaged quantities and the corresponding coefficients."]
  - validation: 50 Monte Carlo iterations perturbing C_* and C_mol with standard error propagation [What drives the environmental variation…: "For each galaxy, the uncertainty in its correlation coefficient $\rho_{i}$ (i.e., between the plane coefficients and each one of the parameters listed) is estimated by performing $50$ Monte-Carlo simulations, perturbing the measured $C_{\star}$ and $C_{\rm mol}$ for each environment in each iteration. The uncertainty …"]
- result: Overall Pearson correlation <rho> between C_mol and <tau / t_ff> = 0.77 ± not stated dimensionless [What drives the environmental variation…: "For this reason, we focus on the following high-$\rho$ parameter, $\langle \tau / t_{\rm ff} \rangle$ ($\langle \rho \rangle \sim 0.77$)."]
- result: Overall Pearson correlation <rho> between C_mol and <sigma_Halpha> = 0.72 ± not stated dimensionless [Summary: "We find a strong correlation of $C_{\rm mol}$ with depletion time and H$\alpha$ velocity dispersion ($\langle \rho \rangle \sim 0.77$ and $0.72$, respectively)"]
- result: Overall Pearson correlation <rho> between C_* and <log SFE> = 0.68 ± not stated dimensionless [What drives the environmental variation…: "Nevertheless, we still see a correlation of $C_{\star}$ with $\log \mathrm{SFE}$ ($\langle \rho \rangle \sim 0.68$)."]
- limitation (authors): At ~150 pc resolution, the lowest SFR pixels may not form enough stars to fully sample the IMF, making measured SFRs more uncertain in that regime. [Star formation rate measurements: "We acknowledge that Eq. [\[eq:sfr\]](#eq:sfr) assumes a fully sampled IMF, and that the lowest SFR pixels (especially at the ${\sim}150$ pc resolution of our data) may not form enough stars to fully sample the IMF. Hence, the measured SFR is more uncertain in this regime."]
- limitation (authors): Spiral arm masks from Querejeta et al. (2021) were identified partially using CO emission, which may introduce selection bias toward higher gas and SFR at fixed Sigma_*. [Nondetections in our data: "The spiral arms defined by (cite: Querejeta2021) tend to have more gas and more star formation at fixed $\Sigma_\star$. Because they were identified partially based on multiwavelength data that trace gas and SFR, this is somewhat by construction."]
- limitation (authors): Fixing a single normalization C_norm across all environments means vertical normalization offsets between environments can be absorbed into the derived slopes C_* and C_mol. [Fitting technique: "Because we keep $C_{\rm norm}$ fixed, our fitting method may allow some of the signal associated with normalization variation to the derived slopes ($C_{\star}$ and/or $C_{\rm mol}$)."]
- not stated (card): Exact bin width in log(Sigma_*) used to compute the 60% detection fraction thresholds for each environment; Exact numerical values of the lower/upper log(Sigma_*) cutoffs resulting from the 60% detection fraction cut for each galactic environment; Exact radial metallicity gradient parameters per galaxy used to compute the fiducial metallicity-dependent alpha_CO maps; Exact World Coordinate System…

### 2024A&A...687A.293Q: Do spiral arms enhance star formation efficiency? (2024; nearby_galaxies, star_formation; archival_reuse)
- question: Do spiral arms enhance star formation efficiency, or only gather gas? Measured via arm/interarm contrasts in stellar mass, molecular gas, SFR and SFE at ~100 pc in 28 PHANGS spiral galaxies
- step 6: Compare contrast distributions and correlations, and test SFE enhancement
  - method: Medians and 16-84 percentiles over bins; KS test grand-design vs rest, jackknife by galaxy; Spearman correlations and bisector fits of gas/SFR/SFE contrasts versus stellar contrast; bootstrap and half-sample jackknife for SFE median [3.2 Grand-design spirals show larger co…: "We ran a Kolmogorov-Smirnov test for the two populations"] [3.3 Correlations among contrasts: "In the case of CO, the slope from a bisector fit is $m=1.8$, while for SFR it is even steeper, $m=2.9$."]
  - parameter: SFE bootstrap within error bars, 10 000 realisations [3.4 Star formation efficiency in spiral…: "If we bootstrap the SFE values within their error bars"]
  - assumption: SFE defined for molecular gas only, SFE = Sigma_SFR/Sigma_mol = 1/tau_dep [3.4 Star formation efficiency in spiral…: "We emphasise that by default we consider the efficiency associated with molecular gas only"]
  - fitting: Bisector fits; priors and likelihood not applicable [3.3 Correlations among contrasts: "In the case of CO, the slope from a bisector fit is $m=1.8$, while for SFR it is even steeper, $m=2.9$."]
  - validation: Jackknife and bootstrap confirm SFE median above unity at about 4 sigma [3.4 Star formation efficiency in spiral…: "we confirm that the enhancement of the median with respect to unity is statistically significant"]
- result: Median SFE contrast across all radial bins (nominal) = 1.16 ± +1.23/-0.58 (16th-84th percentile) dimensionless [3.4 Star formation efficiency in spiral…: "The median SFE contrast across all radial bins is $1.16$."]
- result: Radial bins with SFE higher in spiral arms = 244 of 422 ± not stated bins [3.4 Star formation efficiency in spiral…: "From a total of 422 radial bins, we find 244 bins in which SFE is higher in spiral arms (while in 178 bins it is higher in interarm regions)."]
- result: Median SFE contrast for top 50% and top 10% of stellar contrasts = 1.40 and 2.34 ± not stated dimensionless [3.4 Star formation efficiency in spiral…: "the median SFE contrast rises to $1.40$, and goes up to $2.34$ if we focus on the top 10% of"]
- result: Bisector slopes of Sigma_mol and Sigma_SFR contrast versus Sigma_star contrast (spiral segments) = 1.8 and 2.9 ± 1.83 ± 0.46 and 2.89 ± 1.29 (appendix table) dimensionless [3.3 Correlations among contrasts: "In the case of CO, the slope from a bisector fit is $m=1.8$, while for SFR it is even steeper, $m=2.9$."]
- result: Spearman rank coefficients of Sigma_mol and Sigma_SFR contrast versus Sigma_star contrast = 0.73 and 0.61 ± not stated dimensionless [3.3 Correlations among contrasts: "The Spearman rank correlation coefficients are $0.73$ and $0.61$, respectively."]
- result: Sigma_SFR versus Sigma_mol contrast: Spearman rho and slope = rho = 0.78, slope m = 1.6 ± slope 1.61 ± 0.25 (appendix table) dimensionless [3.3 Correlations among contrasts: "we find an even stronger correlation ($\rho=0.78$)"]
- result: Spearman correlation of SFE contrast with Sigma_star contrast = 0.34 ± not stated dimensionless [3.3 Correlations among contrasts: "the correlation between the contrasts in SFE and stellar surface density is much weaker ($\rho = 0.34$)"]
- result: KS test, SFE contrast grand-design vs rest = p = 0.49 ± not stated dimensionless [3.2 Grand-design spirals show larger co…: "This is not the case for SFE contrasts, though ($p=0.49$), which do not show a significant difference for grand-design spirals."]
- limitation (authors): HI maps have coarse resolution (10-60 arcsec), so atomic-gas results are only at kpc scales [3.5 Atomic gas contrast and its effect …: "We caution that the limited resolution of the H I observations might wash out some of these effects."]
- limitation (authors): Sample limited to galaxies with long continuous spiral segments, mostly grand-design [2 Data and methods: "This choice limits our study to galaxies with long and continuous spiral segments"]
- limitation (authors): Azimuthal variations of alpha_CO are not negligible; a 0.1 dex uncertainty is assumed [2.2 Molecular gas surface densities: "However, azimuthal variations in the real $\alpha_{\rm CO}$ are not completely negligible"]
- not stated (card): ALMA calibration, imaging, and moment-map construction are not described; they live in the PHANGS-ALMA release papers.; The conversion from continuum-subtracted Halpha flux to SFR (calibration constant, IMF) is not given, and the narrow-band Halpha maps are in prep. (Razza et al.).; Exact alpha_CO formula and coefficients, and the metallicity gradient used per galaxy, are not given.; How the narr…

## All papers in this technique

- 2013ApJ...769L..27H (2013): Faint End of 1.3 mm Number Counts Revealed by ALMA
- 2013ApJ...773L..34K (2013): Carbon Monoxide in the Cold Debris of Supernova 1987A
- 2013MNRAS.432....2K (2013): An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: high-resolution 870 μm source counts
- 2014ApJ...795....5O (2014): Faint Submillimeter Galaxies Revealed by Multifield Deep ALMA Observations: Number Counts, Spatial Clustering, and a Dark Submillimeter Lin…
- 2014ApJ...796....1T (2014): Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE
- 2015A&A...584A..78C (2015): ALMA constraints on the faint millimetre source number counts and their contribution to the cosmic infrared background
- 2015ApJ...799...81S (2015): The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Rest-frame Far-infrared Emission of Sub-millimeter Galaxies
- 2015ApJ...806L..25S (2015): ALMA Detected Overdensity of Sub-millimeter Sources Around WISE/NVSS-selected z ~ 2 Dusty Quasars
- 2015ApJ...807..128S (2015): The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Bright-end of the Sub-millimeter Number Counts
- 2015ApJ...811L..19W (2015): Gemini Planet Imager Observations of the AU Microscopii Debris Disk: Asymmetries within One Arcsecond
- 2016ApJ...820...82C (2016): The SCUBA-2 Cosmology Legacy Survey: Multiwavelength Counterparts to 10<SUP>3</SUP> Submillimeter Galaxies in the UKIDSS-UDS Field
- 2016ApJ...822...36O (2016): ALMACAL I: First Dual-band Number Counts from a Deep and Wide ALMA Submillimeter Survey, Free from Cosmic Variance
- 2016ApJ...832...37G (2016): ALMA Observations of Lyα Blob 1: Halo Substructure Illuminated from Within
- 2016ApJ...832..187B (2016): The Massive Protostellar Cluster NGC 6334I at 220 au Resolution: Discovery of Further Multiplicity, Diversity, and a Hot Multi-core
- 2016ApJ...833...67W (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Survey Description
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833...69D (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Luminosity Functions and the Evolution of the Cosmic Density of Molecular Gas
- 2016ApJ...833...71A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Search for [CII] Line and Dust Emission in 6
- 2016ApJS..222....1F (2016): ALMA Census of Faint 1.2 mm Sources Down to ~ 0.02 mJy: Extragalactic Background Light and Dust-poor, High-z Galaxies
- 2016MNRAS.462.1192L (2016): Estimating sizes of faint, distant galaxies in the submillimetre regime
- 2016MNRAS.462.1989A (2016): HerMES: a search for high-redshift dusty galaxies in the HerMES Large Mode Survey - catalogue, number counts and early results
- 2016PASJ...68...36H (2016): SXDF-ALMA 2-arcmin<SUP>2</SUP> deep survey: 1.1-mm number counts
- 2017A&A...604A.117C (2017): Planck's dusty GEMS. IV. Star formation and feedback in a maximum starburst at z = 3 seen at 60-pc resolution
- 2017A&A...608A..98S (2017): Inefficient jet-induced star formation in Centaurus A. High resolution ALMA observations of the northern filaments
- 2017ApJ...835...98U (2017): ALMA Deep Field in SSA22: Source Catalog and Number Counts
- 2017ApJ...835..286I (2017): Extremely Red Submillimeter Galaxies: New z ≳ 4-6 Candidates Discovered using ALMA and Jansky VLA
- 2017ApJ...836..130R (2017): Alma Observations of Massive Molecular Gas Filaments Encasing Radio Bubbles in the Phoenix Cluster
- 2017ApJ...836..223W (2017): An ALMA and MagAO Study of the Substellar Companion GQ Lup B*
- 2017ApJ...843L..35W (2017): ALMA Observations of the Gravitational Lens SDP.9
- 2017ApJ...844..123F (2017): The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters …
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...850...83F (2017): Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034…
- 2017MNRAS.464.4624S (2017): GRB 110715A: the peculiar multiwavelength evolution of the first afterglow detected by ALMA
- 2017MNRAS.466..861D (2017): A deep ALMA image of the Hubble Ultra Deep Field
- 2017MNRAS.468.1769F (2017): The varying mass distribution of molecular clouds across M83
- 2017MNRAS.468.3468G (2017): Molecular gas on large circumgalactic scales at z = 3.47
- 2017MNRAS.472.4024R (2017): Close entrainment of massive molecular gas flows by radio bubbles in the central galaxy of Abell 1795
- 2018A&A...611A..22S (2018): Jekyll &amp; Hyde: quiescence and extreme obscuration in a pair of massive galaxies 1.5 Gyr after the Big Bang
- 2018A&A...618A.120L (2018): The HH30 edge-on T Tauri star. A rotating and precessing monopolar outflow scrutinized by ALMA
- 2018A&A...620A.125M (2018): The ALMA Frontier Fields Survey. IV. Lensing-corrected 1.1 mm number counts in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223
- 2018A&A...620A.152F (2018): GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies
- 2018ApJ...853..160C (2018): The Core Mass Function in the Massive Protocluster G286.21+0.17 Revealed by ALMA
- 2018ApJ...856..121G (2018): Starburst to Quiescent from HST/ALMA: Stars and Dust Unveil Minor Mergers in Submillimeter Galaxies at z ∼ 4.5
- 2018ApJ...860..161S (2018): An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: Number Counts of Submillimeter Galaxies
- 2018ApJ...861....7F (2018): ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exp…
- 2018ApJ...861..100C (2018): An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: Identifying Candidate z ∼ 4.5 [C II] Emitters
- 2018ApJ...862...78C (2018): An Analysis of ALMA Deep Fields and the Perceived Dearth of High-z Galaxies
- 2018ApJ...862...94L (2018): First ALMA Light Curve Constrains Refreshed Reverse Shocks and Jet Magnetization in GRB 161219B
- 2018ApJ...862..105L (2018): The Core Mass Function across Galactic Environments. II. Infrared Dark Cloud Clumps
- 2018ApJ...863..193V (2018): Molecular Gas Filaments and Star-forming Knots Beneath an X-Ray Cavity in RXC J1504-0248
- 2018ApJ...864..174A (2018): The 30 Year Search for the Compact Object in SN 1987A
- 2018ApJ...867..153C (2018): No Evidence for Millimeter Continuum Source Overdensities in the Environments of z ≳ 6 Quasars
- 2018ApJ...869...71Z (2018): Constraining the Volume Density of Dusty Star-forming Galaxies through the First 3 mm Number Counts from ALMA
- 2018MNRAS.479.3879W (2018): An ALMA survey of CO in submillimetre galaxies: companions, triggering, and the environment in blended sources
- 2018MNRAS.481.1976Z (2018): The [C II] emission as a molecular gas mass tracer in galaxies at low and high redshifts
- 2018PASJ...70...65U (2018): ALMA deep field in SSA22: Survey design and source catalog of a 20 arcmin<SUP>2</SUP> survey at 1.1 mm
- 2019A&A...623A.111H (2019): Magnetic field at a jet base: extreme Faraday rotation in 3C 273 revealed by ALMA
- 2019ApJ...871....5T (2019): The Flared Gas Structure of the Transitional Disk around Sz 91
- 2019ApJ...881...10B (2019): A Precision Measurement of the Mass of the Black Hole in NGC 3258 from High-resolution ALMA Observations of Its Circumnuclear Disk
- 2019ApJ...881...43K (2019): The Molecular Outflow in NGC 253 at a Resolution of Two Parsecs
- 2019ApJ...881..124M (2019): Resolved UV and [C II] Structures of Luminous Galaxies within the Epoch of Reionization
- 2019ApJ...882..138D (2019): The ALMA Spectroscopic Survey in the HUDF: CO Luminosity Functions and the Molecular Gas Content of Galaxies through Cosmic History
- 2019ApJ...882..139G (2019): The Atacama Large Millimeter/submillimeter Array Spectroscopic Survey in the Hubble Ultra Deep Field: CO Emission Lines and 3 mm Continuum …
- 2019ApJ...883...71C (2019): The Radial Distribution of Dust Particles in the HL Tau Disk from ALMA and VLA Observations
- 2019ApJ...883L..29L (2019): First [N II]122 μm Line Detection in a QSO-SMG Pair BRI 1202-0725 at z = 4.69
- 2019ApJ...886...48A (2019): Multi-wavelength Properties of Radio- and Machine-learning-identified Counterparts to Submillimeter Sources in S2COSMOS
- 2019ApJ...887...55C (2019): Physical Characterization of an Unlensed, Dusty Star-forming Galaxy at z = 5.85
- 2019ApJS..244...40L (2019): Automated Mining of the ALMA Archive in the COSMOS Field (A<SUP>3</SUP>COSMOS). I. Robust ALMA Continuum Photometry Catalogs and Stellar Ma…
- 2019ESC.....3.2088S (2019): Complex Organic Molecules in Star-Forming Regions of the Magellanic Clouds
- 2019MNRAS.483.1624B (2019): An ALMA archival study of the clump mass function in the Large Magellanic Cloud
- 2019MNRAS.486.4304S (2019): Revealing dust-obscured star formation in CLJ1449+0856, a cluster at z = 2
- 2019MNRAS.487.4648S (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: source catalogue and properties
- 2019Natur.572..211W (2019): A dominant population of optically invisible massive galaxies in the early Universe
- 2019PASJ...71L...3F (2019): First detection of PSR B1259-63/LS 2883 in the millimeter and submillimeter wavelengths with ALMA
- 2020A&A...633A.115K (2020): ALMA and NACO observations towards the young exoring transit system J1407 (V1400 Cen)
- 2020A&A...634A...9M (2020): The flickering nuclear activity of Fornax A
- 2020A&A...635A.119C (2020): Extended Hα over compact far-infrared continuum in dusty submillimeter galaxies. Insights into dust distributions and star-formation rates …
- 2020A&A...643A...2B (2020): The ALPINE-ALMA [CII] survey: Data processing, catalogs, and statistical source properties
- 2020AJ....159..118U (2020): Near-infrared Imaging of a Spiral in the CQ Tau Disk
- 2020ApJ...889...98M (2020): Investigating Overdensities around z &gt; 6 Galaxies through ALMA Observations of [C II]
- 2020ApJ...891...64F (2020): Truth or Delusion? A Possible Gravitational Lensing Interpretation of the Ultraluminous Quasar SDSS J010013.02+280225.8 at z = 6.30
- 2020ApJ...891L..33I (2020): On the Origin of High-energy Neutrinos from NGC 1068: The Role of Nonthermal Coronal Activity
- 2020ApJ...897...91G (2020): The ALMA Spectroscopic Survey in the HUDF: Deep 1.2 mm Continuum Number Counts
- 2020ApJ...897..122L (2020): PHANGS CO Kinematics: Disk Orientations and Rotation Curves at 150 pc Resolution
- 2020ApJ...901...71S (2020): Low-level Carbon Monoxide Line Polarization in Two Protoplanetary Disks: HD 142527 and IM Lup
- 2020ApJ...902..110D (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Multiband Constraints on Line-luminosity Functions and the Cosmic Density of …
- 2020ApJ...903..124B (2020): Hints for Icy Pebble Migration Feeding an Oxygen-rich Chemistry in the Inner Planet-forming Region of Disks
- 2020ApJ...903..138A (2020): An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: The Far-infrared/Radio Correlation for High-redshift Dusty Star-for…
- 2020ApJS..251...14H (2020): CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone
- 2020MNRAS.491.2506D (2020): Using machine learning to study the kinematics of cold gas in galaxies
- 2020MNRAS.493.5290S (2020): Smoke on the water: CO and H<SUB>2</SUB>O in a circumnuclear disc around a quasar at redshift 2.64
- 2020MNRAS.494.5542R (2020): Full of Orions: a 200-pc mapping of the interstellar medium in the redshift-3 lensed dusty star-forming galaxy SDP.81
- 2020MNRAS.495.2332K (2020): ALMACAL VII: first interferometric number counts at 650 μm
- 2020MNRAS.495.3409S (2020): An ALMA survey of the brightest sub-millimetre sources in the SCUBA-2-COSMOS field
- 2020MNRAS.498.4256C (2020): The observational impact of dust trapping in self-gravitating discs
- 2020MNRAS.499.2015T (2020): Planet migration, resonant locking, and accretion streams in PDS 70: comparing models and data
- 2020Natur.584..201R (2020): A dynamically cold disk galaxy in the early Universe
- 2020PASJ...72...69Y (2020): ALMA twenty-six arcmin<SUP>2</SUP> survey of GOODS-S at one millimeter (ASAGAO): Millimeter properties of stellar mass selected galaxies
- 2021A&A...646A..76L (2021): The ALPINE-ALMA [C II] survey. Luminosity function of serendipitous [C II] line emitters at z ∼ 5
- 2021A&A...647A.194F (2021): Fast rotating and low-turbulence discs at z ≃ 4.5: Dynamical evidence of their evolution into local early-type galaxies
- 2021A&A...649A.152K (2021): The ALPINE-ALMA [CII] survey. Obscured star formation rate density and main sequence of star-forming galaxies at z &gt; 4
- 2021A&A...654A..37D (2021): Kinematics and star formation of high-redshift hot dust-obscured quasars as seen by ALMA
- 2021AJ....161..146J (2021): A Search for Companions via Direct Imaging in the DSHARP Planet-forming Disks
- 2021ApJ...906...16S (2021): A New Feedback Cycle in the Archetypal Cooling Flow Group NGC 5044
- 2021ApJ...907..122M (2021): FIR-luminous [C II] Emitters in the ALMA-SCUBA-2 COSMOS Survey (AS2COSMOS): The Nature of Submillimeter Galaxies in a 10 Comoving Megaparse…
- 2021ApJ...908...19B (2021): Black Hole Mass Measurements of Radio Galaxies NGC 315 and NGC 4261 Using ALMA CO Observations
- 2021ApJ...909..165Z (2021): The Evolution of the IR Luminosity Function and Dust-obscured Star Formation over the Past 13 Billion Years
- 2021ApJ...912...21E (2021): Late-time Radio and Millimeter Observations of Superluminous Supernovae and Long Gamma-Ray Bursts: Implications for Central Engines, Fast R…
- 2021ApJ...916...97Y (2021): No Impact of Core-scale Magnetic Field, Turbulence, or Velocity Gradient on Sizes of Protostellar Disks in Orion A
- 2021ApJ...917...73W (2021): Rapid Variability of Sgr A* across the Electromagnetic Spectrum
- 2021ApJ...923..121Y (2021): ALMA Super-resolution Imaging of T Tau: r = 12 au Gap in the Compact Dust Disk around T Tau N
- 2021ApJS..257...43L (2021): PHANGS-ALMA: Arcsecond CO(2-1) Imaging of Nearby Star-forming Galaxies
- 2021MNRAS.502.5390P (2021): A ∼75 per cent occurrence rate of debris discs around F stars in the β Pic moving group
- 2021MNRAS.503.1174K (2021): Feedback factory: multiple faint radio jets detected in a cluster at z = 2
- 2021MNRAS.504..172S (2021): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: halo masses for submillimetre galaxies
- 2021PASJ...73S..35T (2021): The formation of young massive clusters triggered by cloud-cloud collisions in the Antennae galaxies NGC 4038/NGC 4039
- 2022A&A...659L...1L (2022): Size and albedo of the largest detected Oort-cloud object: Comet C/2014 UN<SUB>271</SUB> (Bernardinelli-Bernstein)
- 2022A&A...660A..14R (2022): The ALPINE-ALMA [CII] survey: The population of [CII]-undetected galaxies and their role in the L<SUB>[CII]</SUB>-SFR relation
- 2022A&A...663A..61P (2022): Variations in the Σ<SUB>SFR</SUB> ‒ Σ<SUB>mol</SUB> ‒ Σ<SUB>⋆</SUB> plane across galactic environments in PHANGS galaxies
- 2022A&A...666A..39M (2022): A first search of transients in the Galactic center from 230 GHz ALMA observations
- 2022ApJ...930...32C (2022): Searching Far and Long. I. Pilot ALMA 2 mm Follow-up of Bright Dusty Galaxies as a Redshift Filter
- 2022MNRAS.513.5790C (2022): Variable structure in the PDS 70 disc and uncertainties in radio-interferometric image restoration
- 2022MNRAS.515.3126I (2022): The ALMA REBELS Survey: dust continuum detections at z &gt; 6.5
- 2022MNRAS.517..632L (2022): WISDOM Project - XII. Clump properties and turbulence regulated by clump-clump collisions in the dwarf galaxy NGC 404
- 2023A&A...674A..75N (2023): ALMA-IMF. V. Prestellar and protostellar core populations in the W43 cloud complex
- 2023A&A...674A.101M (2023): Cosmo-tomography toward PKS 1830‒211: Variability of the quasar and of its foreground molecular absorption monitored with ALMA
- 2023A&A...675A..85M (2023): The ALMA Frontier Fields Survey. VI. Lensing-corrected 1.1 mm number counts in Abell 2744, MACSJ0416.1-2403, MACSJ1149.5+2223, Abell 370, a…
- 2023A&A...676A..67W (2023): Quantifying the energetics of molecular superbubbles in PHANGS galaxies
- 2023A&A...679A.119R (2023): PRUSSIC. II. ALMA imaging of dense-gas tracers in SDP.81: Evidence for low mechanical heating and a sub-solar metallicity in a z = 3.04 dus…
- 2023ApJ...945..121U (2023): ALMA Lensing Cluster Survey: Properties of Millimeter Galaxies Hosting X-Ray-detected Active Galactic Nuclei
- 2023ApJ...954..197I (2023): ALMA Measurement of 10 kpc Scale Lensing-power Spectra toward the Lensed Quasar MG J0414+0534
- 2023MNRAS.518.6142A (2023): The ALMA REBELS survey: the dust-obscured cosmic star formation rate density at redshift 7
- 2023MNRAS.519...34H (2023): ALMACAL VIII: a pilot survey for untargeted extragalactic CO emission lines in deep ALMA calibration data
- 2023MNRAS.522...56V (2023): A systematic survey of millimetre-wavelength flaring variability of young stellar objects in the Orion Nebula Cluster
- 2023MNRAS.522.6123Z (2023): Revisiting the Dragonfly galaxy - I. High-resolution ALMA and VLA observations of the radio hotspots in a hyper-luminous infrared galaxy at…
- 2023NatAs...7...80U (2023): Simultaneous radio and optical polarimetry of GRB 191221B afterglow
- 2023PASA...40...17W (2023): VERTICO V: The environmentally driven evolution of the inner cold gas discs of Virgo cluster galaxies
- 2023PASJ...75..311K (2023): Galaxy clusters at z ∼ 1 imaged by ALMA with the Sunyaev-Zel'dovich effect
- 2024A&A...681A.110W (2024): A<SUP>3</SUP>COSMOS: Dissecting the gas content of star-forming galaxies across the main sequence at 1.2 ≤ z &lt; 1.6
- 2024A&A...682A..55M (2024): High-resolution ALMA observations of compact discs in the wide-binary system Sz 65 and Sz 66
- 2024A&A...683A.141R (2024): AB Aur, a Rosetta stone for studies of planet formation. III. Continuum observations at 2 and 7 mm
- 2024A&A...684A..23T (2024): Fitting pseudo-Sérsic (Spergel) light profiles to galaxies in interferometric data: The excellence of the uυ-plane
- 2024A&A...684A.119P (2024): ALMA survey of a massive node of the Cosmic Web at z ∼ 3. I. Discovery of a large overdensity of CO emitters
- 2024A&A...686A.122A (2024): ALMA-IMF. X. The core population in the evolved W33-Main (G012.80) protocluster
- 2024A&A...687A..35R (2024): Dynamical modelling and the origin of gas turbulence in z ∼ 4.5 galaxies
- 2024A&A...687A.293Q (2024): Do spiral arms enhance star formation efficiency?
- 2024A&A...690A..33L (2024): ALMA-IMF: XV. Core mass function in the high-mass star formation regime
- 2024A&A...691A..57M (2024): SPH modelling of AGB wind morphology in hierarchical triple systems and a comparison to observation of R Aql
- 2024A&A...691A..70N (2024): Disruption of a massive molecular cloud by a supernova in the Galactic Centre: Initial results from the ACES project
- 2024A&A...691A.248L (2024): The role of stellar mass in the cosmic history of star formation as seen by Herschel and ALMA
- 2024A&A...692A..22Z (2024): ASW<SUP>2</SUP>DF: Census of the obscured star formation in a galaxy cluster in formation at z = 2.2
- 2024ApJ...961..120C (2024): Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus
- 2024ApJ...962..128M (2024): Comparing SCUBA-2 and ALMA Selections of Faint Dusty Star-forming Galaxies in A2744
- 2024ApJ...967...56C (2024): Investigations of Massive Filaments and Star Formation (INFANT). I. Core Identification and Core Mass Function
- 2024ApJ...969...27B (2024): MIDIS: JWST/MIRI Reveals the Stellar Structure of ALMA-selected Galaxies in the Hubble Ultra Deep Field at Cosmic Noon
- 2024ApJ...971...52M (2024): Multiwavelength Observations of Sgr A*. II. 2019 July 21 and 26
- 2024ApJ...974..279D (2024): A Millimeter Rebrightening in GRB 210702A
- 2024ApJ...976..198H (2024): Whole-disk Sampling of Molecular Clouds in M83
- 2024ApJ...977..121N (2024): Exploring Magnetic Fields in a Merging Galaxy: Comparing Polarization and Velocity Gradient in the Centaurus Galaxy
- 2024ApJ...977..251H (2024): Molecular Gas Mass Measurements of an Active, Starburst Galaxy at z ≍ 2.6 Using ALMA Observations of the [C I], CO, and Dust Emission
- 2024ApJS..275...36F (2024): ALMA Lensing Cluster Survey: Deep 1.2 mm Number Counts and Infrared Luminosity Functions at z ≃ 1─8
- 2024MNRAS.52710221P (2024): Enhanced star formation and metallicity deficit in the USS 1558-003 forming protocluster at z = 2.53
- 2024MNRAS.528.5019H (2024): An optimal ALMA image of the Hubble Ultra Deep Field in the era of JWST: obscured star formation and the cosmic far-infrared background
- 2024MNRAS.528L..76R (2024): A fundamental plane of black hole accretion at millimetre wavelengths
- 2024MNRAS.531.4045C (2024): WISDOM Project - XXI. Giant molecular clouds in the central region of the barred spiral galaxy NGC 613: a steep size-linewidth relation
- 2024MNRAS.533..771R (2024): Two distinct molecular cloud populations detected in massive galaxies
- 2024MNRAS.535.2538Z (2024): A resolved, multiwavelength study of gas-rich dwarf galaxies in the Fornax cluster using MUSE, MeerKAT, and ALMA
- 2024PASJ...76..437Y (2024): ALMA 2D super-resolution imaging of Taurus-Auriga protoplanetary disks: Probing statistical properties of disk substructures
- 2025A&A...694A.165T (2025): X-ray view of a massive node of the Cosmic Web at z ∼ 3: I. An exceptional overdensity of rapidly accreting supermassive black holes
- 2025A&A...694A.291K (2025): Gamma-ray flares from the jet of the blazar CTA 102 in 2016─2018
- 2025A&A...695A.163B (2025): ALMACAL: XIII. Evolution of the CO luminosity function and the molecular gas mass density out to z ∼ 6
- 2025A&A...695A.204V (2025): Quantifying the detection likelihood of faint peaks in interferometric data through jackknifing: Test application on finding z &gt; 10 gala…
- 2025A&A...696A..95G (2025): Connecting the growth of galaxies to the large-scale environment in a massive node of the Cosmic Web at z ∼ 3
- 2025A&A...696A.151C (2025): ALMAGAL: III. Compact source catalog: Fragmentation statistics and physical evolution of the core population
- 2025A&A...699A.324H (2025): ADF22+: A declining faint end in the far-infrared luminosity function in the SSA22 protocluster at z = 3.09
- 2025A&A...701A..41D (2025): Millimeter emission from supermassive black hole coronae
- 2025A&A...704A.158C (2025): Pushing JWST to the extremes: Search and scrutiny of bright galaxy candidates at z ≃ 15─30
- 2025ApJ...979..142N (2025): Peculiar Dust Emission within the Orion Molecular Cloud
- 2025ApJ...984L..57O (2025): The Ophiuchus DIsk Survey Employing ALMA (ODISEA): A Unified Evolutionary Sequence of Planet-driven Substructures Explaining the Diversity …
- 2025ApJ...985..194P (2025): Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies
- 2025ApJ...987...77J (2025): Why is the Star Formation Rate Proportional to Dense Gas Mass?
- 2025ApJ...988..172H (2025): The Centre of Attention: A Powerful Radio Galaxy Pinpoints a Near-infrared-dark Protocluster at z ∼ 3.9
- 2025ApJ...988..215K (2025): Timescales of Polycyclic Aromatic Hydrocarbon and Dust Continuum Emission from Gas Clouds Compared to Molecular Gas Cloud Lifetimes in PHAN…
- 2025ApJ...989L..22B (2025): Worlds Next Door: A Candidate Giant Planet Imaged in the Habitable Zone of α Centauri A. I. Observations, Orbital and Physical Properties, …
- 2025ApJ...990L..70L (2025): Discovery of Hα Emission from a Protoplanet Candidate around the Young Star 2MASS J16120668─3010270 with MagAO-X
- 2025ApJ...991L..38U (2025): RIOJA. JWST and ALMA Unveil the Inhomogeneous and Complex Interstellar Medium Structure in a Star-forming Galaxy at z = 6.81
- 2025ApJ...993..111W (2025): A Multiwavelength Study of ELAN Environments (AMUSE<SUP>2</SUP>): The Impact of Dense Environment on Massive Dusty Star-forming Galaxies at…
- 2025MNRAS.541...71M (2025): ALMA millimetre-wavelength imaging of HD 138965: new constraints on the debris dust composition and presence of planetary companions
- 2025PASJ...77.1163H (2025): ALMA deep field in SSA22: Reconstructed [C II] luminosity function at z = 6
- 2025PASP..137l4501T (2025): The ViSta Method for Stacking in the Fourier Domain and its Application to the Dusty Star-forming Galaxies in the ALMA Science Archive
- 2026A&A...705A.238V (2026): Astrometric view of companions in the inner dust cavities of protoplanetary discs
- 2026A&A...706A.206H (2026): The Atacama Cosmology Telescope: Observations of supermassive black hole binary candidates: Strong sinusoidal variations at 95, 147, and 22…
- 2026A&A...706A.345K (2026): Evolution of the infrared luminosity function and its corresponding dust-obscured star formation rate density out to z ∼ 6
- 2026A&A...706A.365M (2026): A sub-ppm upper limit on the cosmological variations of the fine structure constant α
- 2026A&A...707A..77H (2026): Massive dusty multiphase outflow in local merger shows no sign of slowing on kiloparsec scales
- 2026A&A...707A.221S (2026): ALMAGAL: VI. The spatial distribution of dense cores during the evolution of cluster-forming massive clumps
- 2026A&A...712A.244H (2026): Multiband ALMA polarimetry of the jet base and kiloparsec-scale jet of 3C 273: A multicomponent Faraday structure in the nucleus
- 2026ApJ...997..155M (2026): The ALMA Survey of 70 µm Dark High-mass Clumps in Early Stages (ASHES). XIII. Core Mass Function, Lifetime, and Growth of Prestellar Cores
- 2026ApJ...999...47L (2026): The Extended Mapping Obscuration to Reionization with ALMA (Ex-MORA) Survey: 5σ Source Catalog and Redshift Distribution
- 2026ApJ..1000..141K (2026): First Determination of the Cosmic Microwave Background Radiation Temperature at z = 0.68 Using Molecular Absorption Lines
- 2026ApJ..1000..231B (2026): Ring Asymmetry and Spin in M87*
- 2026ApJ..1000L..10C (2026): An Overabundance of Radio Active Galactic Nuclei in the SPT2349─56 Protocluster: Preheating the Intracluster Medium
- 2026ApJ..1004..182H (2026): A Radially Broad Collisional Cascade in the Debris Disk of γ Ophiuchi Observed by JWST
- 2026ApJS..284....3H (2026): The Hidden Life of Stars: Embedded Beginnings to Asymptotic Giant Branch Endings in the PHANGS─JWST Sample. I. Catalog of Mid-infrared Sour…
- 2026MNRAS.548ag325W (2026): 3D insights into SN 1987A: ALMA observations compared to hydrodynamical explosion simulations
- 2026MNRAS.550g1193B (2026): GOTO identification and broad-band modelling of the counterpart to the SVOM GRB 250818B
- 2026MNRAS.552g1573L (2026): The ALMA EGO-10 survey of massive protoclusters: correlation of 1.3 mm continuum source clustering with evolutionary state
- 2026MNRAS.552g1615S (2026): The efficient star-forming regions of stripped-envelope supernovae
