---
name: alma-paper-reproduction
description: "Reproduce a published ALMA analysis: build an answer key with tolerances from the paper, inventory what the paper leaves unstated or inherits from earlier papers, fetch only the data products needed, rerun the paper's own software in tested stages, match beam and noise before comparing, and report every residual mismatch and open item. Use when asked to reproduce, rediscover, re-derive or check a paper's numbers from ALMA archive data, when grading an agent's reproduction, or when an earlier paper's results must be rebuilt as input to new work. Built from 3225 ALMA papers (2012-2026)."
---

# Reproducing a published ALMA analysis

A reproduction is a comparison, not a re-analysis: every number you produce is judged against a number in the
paper, so the answer key and its tolerances come first and the data come second. The two failures that matter
most: (1) settings the paper never states or inherits silently from an earlier paper (line-free channels,
self-calibration, imaging parameters, completeness corrections) make your images noisier or your fluxes
different, and (2) comparing science numbers before your beam and rms match the paper's, so a processing
difference is reported as a scientific disagreement.

## Agent checklist

1. Before any download, write `answer_key.csv` from the paper's tables and text: quantity, value, error, error
   type (statistical, systematic, 3 sigma), location, tolerance. Many card answer keys carry "± not stated"
   (2017ApJ...847...92H, 2020PASJ...72...36T). Then the last quoted digit is only a rounding floor, not an
   error bar (general practice): build the tolerance from your own statistical error plus the flux-scale term
   (checklist below), never reject a match on rounding alone, and say which you used.
2. Inventory unstated and inherited settings. Most often missing (row sums over phrasings of the pack's "not
   stated" list, my count): line-free channels or continuum subtraction 521, CASA/pipeline version 367,
   self-calibration 237, flux calibrator or flux-scale uncertainty 181, cell and image size 160. Open every
   "as in Paper I" reference and copy what it fixes (2014A&A...570A..28V, 2026A&A...705A.197Z).
3. When the paper is silent, assume observatory pipeline calibration (pipeline phrasings dominate the
   "calibration as stated" aggregate; "manual" is stated by 6 papers over two phrasings) and a 10% absolute flux scale (103 "10%" +
   82 "~10%" rows), and flag each assumption in the report.
4. Fetch the smallest product that contains the answer: archive image or cube, then calibrated visibilities
   restored with the delivered scripts, then raw recalibration only if the paper did it or the products fail
   a check. Single Cycle 0 executions are already ~10-30 GB raw (2014ApJ...791...42Z), while imaged cubes are
   ~2 GB (2019MNRAS.485.4359S).
5. Use the paper's own software and the version it names; do not reimplement a fitter the paper ran from a
   public package (KinMS in 2019MNRAS.485.4359S, 3DBarolo in 2021A&A...645A..21G, uvmodelfit in
   2023PSJ.....4..206R).
6. Reproduce in stages and gate each stage with a number from the paper: beam, then rms, then continuum or
   line flux, then derived quantities. Do not start stage n+1 until stage n matches or the mismatch is
   explained.
7. Match beam and rms before comparing science numbers. There is no corpus-standard tolerance for "noise
   matches the paper" (the ~30% in 2020ApJS..247...15S is that paper's noise against the theoretical value,
   not a reproduction criterion). Recommendation (general practice): measure rms the same way and in the same
   region as the paper; if yours is more than about 10-20% above the paper's, treat it as a processing
   difference and find the missing step (self-calibration, flagged data, weighting, taper, binning, continuum
   channels) before comparing science numbers, and say so in the report.
8. Tolerance for flux-derived quantities = your statistical error, the paper's error and the flux-scale
   uncertainty, combined in quadrature (unless the paper's error already includes the scale term; check).
   Flux-scale defaults: 10% default; 5% in Band 3 (2024A&A...690A.232S); ~20% for early high-frequency data
   (2014ApJ...796...84R); the observatory's stated accuracy is about 5% in Bands 3-5, 10% in Bands 6-7 and 20% in
   Bands 8-10 (general practice). Ratios from the same execution and setup, positions and velocities do not get
   the flux-scale term; a spectral index or ratio between bands or datasets gets both datasets' terms.
9. Write `reproduction_report.md`: one verdict per answer-key row (match, within tolerance, explained
   mismatch, unexplained mismatch, not reproducible with data in hand), every assumed default, every open item.
10. "Done" means the code ran, the outputs exist and each was compared to the key (team lesson: in CosmicCoder
    agent runs a judge approved code that had been written but never executed).

## When to use

- A task gives a paper (or its summary) and ALMA data and asks you to find what the paper found (bottom-up or
  rediscovery tasks). The cards judged papers good rediscovery tasks when data are public, the recipe is short
  and results are numeric in tables (2016AJ....152..218I, card: "tabulated numeric fluxes provide answer keys";
  2014ApJ...784...62A, 2016ApJ...829....6W).
- Checking a published number before building on it, or rebuilding inputs from an earlier paper in a series
  (2019A&A...623A.153O repeats the energetics analysis of its predecessor on the same data).
- Grading or reviewing another agent's reproduction: use the Verification checks below as the rubric.

## When not to use

| Situation | Do instead |
|---|---|
| Open research question with no published answer to match | Pick method and data from the question; use the claim-verification and archival-data-reuse skills |
| You only need a literature number as input (distance, inclination, stellar mass) | Take it from the paper with its citation and uncertainty, as papers do (2019MNRAS.485.4359S: distance, MGE model and dust-disc inclination from the literature) |
| Checking whether a finding is real rather than whether a number repeats | claim-verification skill (null tests, injection tests, model comparison) |
| The paper's data are not public or the key inputs are private (a private-communication dust temperature and "in prep." 0.1 arcsec data in 2017ApJ...847...92H) | Reproduce what the public inputs allow and record the rest as open items; do not guess the private input |
| Theory or simulation paper compared with ALMA | Reproduce the observational comparison only (2021ApJ...907...80O) and treat the model as a separate task |

## Steps

**1. Build the answer key.** Goal: a machine-readable list of target numbers with tolerances.
- Take numbers from tables first, then text, then figures. Record the error type the paper states: 3 sigma
  intervals (2019MNRAS.485.4359S quotes the SMBH mass as 4.0e8 +1.6/-1.5 e8 Msun at fixed inclination and
  +3.5/-2.0 e8 with the inclination uncertainty included), "statistical, possibly underestimated"
  (2023MNRAS.523.2887M), "at least a factor of four" (2015A&A...576L..15O).
- Check whether the error includes the absolute flux scale: 2016ApJ...829....6W and 2019A&A...626A.126A add 10%;
  2020ApJS..247...15S states its 5-10% flux-scale uncertainty "is not included"; 2014ApJ...791...42Z quotes
  226 ± 1 mJy and the 10% absolute scale separately.
- Rewrite distance-scaled numbers in their scaling form (gas mass 0.5 [D/1 kpc]^2 Msun in 2019A&A...623A.153O)
  and note when a paper rescaled literature values to a new distance (2017ApJ...848L..11K, GAIA distance).
- Include intermediate keys you can test early: beam, rms per channel, continuum flux, number of detections.
- Check that closes it: every row has a value, an error or an explicit "not stated", and a tolerance rule.

**2. Inventory unstated and inherited conventions.** Goal: know every choice you will have to make.
- Make a table of settings the paper states, inherits, or omits (template in `references/unstated-defaults.md`).
- Trace each "following X", "as in Paper I", "described elsewhere" to the cited paper and read the relevant
  section. In series papers the reduction, region definitions and phase-tracking centre live in Paper I
  (2014A&A...570A..28V); corrected visibility weights, phase centres and execution-block flux offsets live in a
  companion paper (2026A&A...705A.197Z); the source size, offset positions and a continuum correction factor
  are fixed by earlier survey papers (2019A&A...623A..69M); self-calibration, calibrator setup and the robust
  0.5 plus taper recipe come from two earlier papers (2020ApJ...904..181L).
- Look for inherited statistical corrections: completeness, flux boosting and spurious fraction follow
  earlier number-count papers (2014ApJ...795....5O, 2013ApJ...768...91H; an alternative flux-boosting
  correction in 2015A&A...584A..78C). A series paper may apply such corrections without restating them.
- Look outside the main text: model inputs may sit only in a figure caption (2012ApJ...761L..20R), details may
  be deferred to papers "in preparation" (2012ApJ...757L...1H, 2013A&A...558A.123M), and a cited source can be
  missing from the text altogether (2025A&A...694A..86Y adopts 70 K with the citation marker missing).
- Literature inputs (catalogues, redshifts, magnifications, photometry) are part of the inventory: list each
  with its source (2024ApJ...965..108U fixes redshifts and magnifications from the survey catalogue paper).
- Check that closes it: no row says "unknown" without a planned default or an open-item entry.

**3. Get only the data products you need.** Goal: the minimum download that can produce the answer key.
- Decision rule. If the paper used archive products as delivered and the key is an image-plane quantity, use the
  products (cubes used without further treatment in 2020MNRAS.492.5121D; pipeline products in
  2016MNRAS.462L...6K; pipeline continuum maps in 2019ApJ...879..117K). If the paper re-imaged, self-calibrated, changed weighting or
  channel width, start from calibrated visibilities (2019ApJ...887...74F; natural-weighting reprocessing in
  2018ApJ...854...83T; 10 km/s instead of the archive's 20 km/s in 2017MNRAS.465.3461Z). Recalibrate from raw
  only when the paper did or a check fails (new flux model libraries in 2018A&A...616A.127R; a variable flux
  calibrator in 2020ApJ...904...78S; reweighting in 2017ApJ...849...68S).
- Restore calibrated measurement sets by running the delivered scripts (scriptForPI.py in 2019ApJS..244...40L;
  2021AJ....162..235Y; 2021ApJ...918...76C re-imaged in CASA 5.6.1-8; revised archive scripts in
  2021ApJ...907L..27A).
- Survey releases are often the paper's actual input: PHANGS-ALMA v4.0 cubes (2021A&A...656A.133Q), DSHARP
  visibilities (2021A&A...654A..35B), ALPINE DR1 (2021A&A...653A.111R), JVO first-look images
  (2021A&A...655A.113M).
- Delivered images can be the wrong starting point: under-cleaned (2020MNRAS.496.1834L), or used only for a
  preliminary check (2021A&A...653A.166C). Others found the delivered products already optimal
  (2015MNRAS.452.2258D) or saw no gain from recalibration (2016ApJ...830L..16B).
- Fetch by MOUS or product, not by project (general practice; astroquery can do this, check before use). In
  CosmicCoder agent runs one agent tried to pull about 4 TB by project code when a few products sufficed.
- Check that closes it: the files on disk cover the spectral windows, fields and epochs named in the paper, and
  their total size fits the environment.

**4. Match the paper's software.** Goal: remove software differences as an explanation.
- Use the CASA version the paper states, or the one the delivered scripts require; papers mixed pipeline
  versions by cycle (v4.7.2 and v5.4.1 in 2021ApJ...908..192S) and reduced with "various versions of CASA over
  the years" (2019A&A...623A.153O). If AIPS and CASA were used in parallel (2014ApJ...796...84R), note which
  produced the published map if known.
- Use released analysis code at the version cited (commit hashes in 2018ApJ...853..171G and
  2018ApJ...860..119G; a frozen Zenodo version of yclean in 2018ApJ...861...14C; DSHARP scripts in
  2018ApJ...869L..49I). If the code is not released, use the public package it was built on and record the gap
  (KinMS public but KINMS_MCMC not released at the time in 2017MNRAS.468.4675D).

**5. Reproduce in stages with tests.** Goal: localise any disagreement to one stage.
- Stage order: (a) calibration or product check, (b) imaging: beam and rms, (c) primary measurement: flux,
  size, spectrum, (d) derived physics: mass, temperature, column density, (e) the paper's model fit.
- Write each stage's outputs to files and print summaries only (team lesson: printing raw tables cost agents
  millions of input tokens).
- Gate each stage against the answer key. 2013A&A...560A.103M recalibrated and found its continuum flux consistent with
  the delivered one; 2023PSJ.....4..206R measured the same source by uvmodelfit (1.79 ±
  0.18 mJy) and in the image (1.73 ± 0.18 mJy).

**6. Match noise and beam before comparing.** Goal: compare like with like.
- Reproduce the stated beam by choosing weighting and taper: natural (2014ApJ...791...42Z), robust 0.5 then a
  taper to 0.14 arcsec (2020ApJ...904..181L), robust -1 for lines and -2 for continuum (2019MNRAS.485.4359S),
  1 arcsec tapered products for photometry (2021ApJ...908..192S).
- Measure rms where the paper did (emission-free area for continuum, a line-free channel for cubes,
  2020PASJ...72...36T). Expect achieved noise to differ from the request (72 versus 40 uJy/beam desired in
  2019A&A...626A.126A).
- If yours is noisier, test in turn: missing self-calibration (four rounds of phase-only self-calibration in
  2017ApJ...847...92H; intervals of 5, 2 and 1 min in 2017Icar..286..289L), extra flagging (2016ApJ...829L..23B,
  2020ApJS..247...15S), Hanning smoothing or binning (2020ApJS..247...15S), and data combination (combining
  configurations lowered channel rms from ~2 to ~0.7 mJy/beam in 2019A&A...623A.153O).
- Comparing across resolutions or instruments: convolve to the common lowest resolution on the same tracking
  centre (2014A&A...570A..28V), match single-dish maps by Gaussian convolution (54 arcsec kernel in
  2019ApJ...871...45S), or taper and smooth ALMA to the other array (2017ApJ...847...92H). Check interferometric
  flux loss against single-dish spectra (2012A&A...538L...9H, 2014A&A...570L..14R).

**7. Compare and explain every residual.** Goal: a verdict per key row, never one overall verdict.
- Common explanations to test, with corpus examples: flux calibrator value (2023PSJ.....4..206R set
  J0238+1636 to 1.11 Jy instead of the pipeline's 1.22 Jy), flux model libraries (2018A&A...616A.127R),
  inherited corrections (step 2), distance or cosmology (step 1), aperture or region definition (unstated in 24
  rows-sum of the "missing" list), and inconsistencies inside the paper (the card for 2021A&A...645A..21G notes
  internal numerical inconsistencies). Team lessons add smoothing of a published figure and table typos.
- Check that closes it: each mismatch has a tested cause, or is marked unexplained with what you tried.

**8. Record open items and stop.** Goal: a reproduction that ends.
- Stop a stage when it matches within tolerance, or when the remaining difference needs an input you cannot
  get (unreleased code, private data, a companion paper's correction table). Write the item down with what
  would settle it instead of iterating (team lesson: open-ended verification became a money pit).

## Parameter defaults and ranges

| Setting or threshold | Default | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Absolute flux-scale uncertainty | 10% | ~3 mJy (ACA calibrator) to ~20% | "10%" 103, "~10%" 82, "5%" 25, "~5%" 16, "15%" 15, "20%" 5 rows (pack aggregate) | 5% Band 3 (2024A&A...690A.232S); 5% with Titan (2017Icar..286..289L); ~10% Bands 6-7 (2017ApJ...847...92H); ~20% Cycle 0 at 994 um (2014ApJ...796...84R); 5% stated, ≥20% real (2019A&A...623A.153O); ~3 mJy (2025A&A...699L..11V) |
| Achieved noise versus theoretical (what papers report; not a reproduction tolerance) | within ~30% | 72 vs 40 uJy/beam requested | examples only | 2020ApJS..247...15S, 2019A&A...626A.126A |
| Weighting when unstated | match the stated beam; Briggs 0.5 is a frequent choice | natural to robust -2 | examples only | 0.5: 2020ApJ...904..181L, 2025A&A...699L..11V, 2020ApJS..247...15S; natural: 2016ApJ...829....6W, 2015A&A...576L..15O; 0.2: 2020PASJ...72...36T; 0.6: 2017ApJ...848L..11K |
| Self-calibration when stated | phase-only rounds, shortening intervals | 1-4 phase rounds, then amplitude | examples only | 2017ApJ...847...92H, 2017Icar..286..289L, 2014ApJ...796..117G, 2023PSJ.....4..206R (inf per EB, then per scan, then amplitude) |
| Raw data volume | estimate before fetching | ~1 GB to a few hundred GB | card estimates | ~10-30 GB one Cycle 0 EB (2014ApJ...791...42Z); 50-100 GB 7 EBs (2014ApJ...784...62A); 100-300 GB 13 EBs (2014A&A...566A.112M); few hundred GB line survey (2014Sci...345.1584B); ~1 GB single-dish maps (2019ApJ...871...45S) |
| Product volume | prefer products | ~2 GB to tens of GB | card estimates | cubes ~2 GB (2019MNRAS.485.4359S); a few GB of cubes vs 100-300 GB raw (2025A&A...694A..86Y); much smaller if calibrated maps used (2014ApJ...780..115D) |
| Detection threshold for faint sources | the paper's S/N cut | S/N 4-5 | example | completeness 47% at S/N 4.0 and 80% at 5.0 (2021ApJ...908..192S) |
| Reproducibility of a typical paper | expect gaps | card score modal value 3 (2014 papers; mixed scales) | pack aggregate | cards cite missing imaging, calibration and fit details |

## What papers most often leave unstated, and the default to assume

Counts are row sums over phrasings of the pack's "settings needed but not stated" list (my count; a row naming
two items counts for both). Flag every default you use. Longer table with physical constants:
`references/unstated-defaults.md`.

| Unstated item | Count | Default to assume (and flag) | Corpus basis |
|---|---|---|---|
| Line-free channels / continuum subtraction | 521 | choose channels free of all known lines; check the continuum flux against the paper | continuum-subtraction skill; 2017Icar..286..289L averages channels "far outside" the line |
| CASA / pipeline version | 367 | the version in the delivered scripts | 2019ApJS..244...40L, 2021ApJ...918...76C |
| Pipeline or manual calibration | 44 | pipeline as delivered | "calibration as stated" aggregate |
| Self-calibration intervals, rounds | 192 | none first; add phase-only rounds if your rms is above the paper's | 2017ApJ...847...92H; no gain in 2021A&A...648A..41V |
| Whether self-calibration was applied | 45 | treat as an open fork; try both if rms differs | same |
| Flux calibrator, flux-scale uncertainty | 181 | 10%; 5% Band 3 | aggregate; 2024A&A...690A.232S |
| Cell and image size | 160 | general practice: several pixels per beam, image covering the primary beam | none stated in pack |
| CLEAN threshold, masks | 89 | pipeline auto-masking thresholds | 2023PSJ.....4..206R |
| Primary-beam correction | 70 | fluxes on the PB-corrected image, noise on the flat-noise image (general practice) | 2012A&A...538L...9H used PB-corrected cubes; 2016A&A...589A..20V did not |
| Source or phase-centre coordinates | 44 | archive phase centre; series papers inherit it | 2014A&A...570A..28V |
| Moment-map clipping | 20 | see moment-maps skill | |
| uvmodelfit starting values | 11 | image-plane Gaussian fit | general practice |
| MCMC priors and settings (missing list) | 42 | uniform priors over the paper's stated ranges; check convergence | 2014ApJ...791...42Z lacks priors (card) |
| Analysis code (missing list) | 42 | the public package the paper names | 2017MNRAS.468.4675D |

## Software

- **Calibration and imaging:** CASA. Most stated versions: 4.7.2 (50), 4.7.0 (40), 5.4.0 (29), 4.5.3 (28),
  4.2.2, 4.3.1 and 5.1.1 (27 each) (pack aggregate, phrasings not merged). Calibration route as stated is
  overwhelmingly the observatory pipeline ("alma pipeline" 44, "casa pipeline" 44, "pipeline" 35, "standard
  alma pipeline" 27) against "manual" in 6 papers. Restore with the delivered scripts (2019ApJS..244...40L);
  pipeline auto-masking (2023PSJ.....4..206R); automated self-calibration (auto_selfcal, 2023PSJ.....4..206R).
  Calibrator flux models: Butler-JPL-Horizons 2012 / ALMA Memo 594 (2015A&A...576L..15O).
- **Primary measurements:** uvmodelfit (2014ApJ...788L..34P, 2016A&A...596A..75S, 2023PSJ.....4..206R),
  UVMULTIFIT (2015A&A...577L...4V), GILDAS uv fitting (2018MNRAS.481.1976Z), vis_sample (16 of 150 listed
  "code released" rows, my count).
- **Models the paper ran:** KinMS (2019MNRAS.485.4359S), 3DBarolo (2021A&A...645A..21G), MCFOST
  (2013A&A...557A.133D), UCL_CHEM (2014A&A...570A..28V), Weeds LTE (2023MNRAS.523.2887M), NEMESIS
  (2025PSJ.....6..107N), MAGPHYS (2021ApJ...908..192S), CIGALE and GLAFIC (2024ApJ...965..108U), frank
  (2026A&A...705A.197Z). Configurations are often the missing piece ("magphys configuration" 7, "3dbarolo
  configuration" 5, "cloudy input files" 5 in the missing list).
- **Line data:** CDMS and JPL via Splatalogue (2012ApJ...757L...1H, 2014ApJ...796..117G).
- **Released code is the exception:** of 150 listed "code released" rows, 28 say "not stated" and 8 mention
  "on request" (my count). See the analysis-software-map skill for the package per job.

## Pitfalls

- **Silent inheritance.** Corrections and design choices reused from earlier papers in a series without being
  restated (team lesson; step 2). Read the predecessor before declaring a mismatch.
- **Noise you cannot explain.** Reproduced images noisier than the paper's with no stated extra step (team
  lesson). Test self-calibration, flagging, weighting and data combination in turn (step 6).
- **Flux-scale drift.** The pipeline calibrator value can be off by ~10% for one execution
  (2023PSJ.....4..206R); flux model libraries change (2018A&A...616A.127R).
- **Error budgets that leave out the flux scale** (2020ApJS..247...15S) make the paper's quoted error too small
  as a tolerance for your recalibrated flux.
- **Mixed versions and parallel packages** (2019A&A...623A.153O, 2014ApJ...796...84R).
- **Inputs outside the paper:** captions (2012ApJ...761L..20R), "in prep." companions (2013A&A...558A.123M),
  missing citations (2025A&A...694A..86Y), private communications (2017ApJ...847...92H).
- **Whole-project downloads** and environments where CASA cannot be installed (team lesson). Older-cycle data
  needing reprocessing may be out of reach; use the products and record the limit.
- **Reimplementing a standard fitter** gave worse measurements than the paper (team lesson).
- **Stopping at the bright component.** Agents that characterised the obvious emission and stopped missed the
  faint compact signal that was the finding (team lesson). Keep every answer-key row in play until judged.

## Verification checks

- Every answer-key row has a verdict, a tolerance and the file and line of code that produced the number.
- Beam (major, minor, PA) and rms match the paper's stated values, or the difference is explained, before any
  science comparison.
- Flux-derived comparisons include the flux-scale term only when calibration differs; ratios and positions do
  not.
- Each assumed default is listed with its corpus basis; each inherited convention cites the earlier paper it
  came from.
- Cross-method check where cheap: image versus uv-plane flux (2023PSJ.....4..206R), recalibrated versus
  delivered continuum flux (2013A&A...560A.103M), interferometer versus single-dish flux (2014A&A...570L..14R).
- Open items list what would settle them. A referee will ask: was the code executed, does the reproduced
  noise match, and is any agreement claimed beyond the stated precision.

## Source cards

All member papers: `references/sources.md`. Most informative for this workflow: 2014A&A...570A..28V,
2026A&A...705A.197Z, 2019A&A...623A..69M, 2020ApJ...904..181L, 2019MNRAS.485.4359S, 2014ApJ...791...42Z,
2016ApJ...829....6W, 2023PSJ.....4..206R, 2020ApJS..247...15S, 2019A&A...623A.153O, 2017ApJ...847...92H,
2025A&A...694A..86Y, 2014ApJ...795....5O, 2018A&A...616A.127R, 2020ApJ...904...78S, 2019ApJS..244...40L,
2021ApJ...918...76C, 2020MNRAS.496.1834L, 2017MNRAS.465.3461Z, 2014A&A...570L..14R, 2019ApJ...871...45S,
2021ApJ...908..192S, 2024A&A...690A.232S, 2013A&A...560A.103M, 2021A&A...645A..21G.
