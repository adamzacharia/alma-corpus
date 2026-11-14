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
