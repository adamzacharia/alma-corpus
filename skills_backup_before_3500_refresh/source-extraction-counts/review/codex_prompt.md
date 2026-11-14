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

=== SKILL.md (source-extraction-counts) ===
---
name: alma-source-extraction-counts
description: "Find sources blindly in ALMA continuum maps and turn them into a trustworthy catalog and number counts: noise maps and S/N thresholds, peak finders (SExtractor, BLOBCAT, LineSeeker, PyBDSF), fidelity/purity from the inverted map, completeness and flux boosting from injected sources, effective area, differential and cumulative counts with double power-law fits, and conversion of counts between wavelengths. Use when a task asks for a blind continuum catalog of an ALMA map or mosaic, a false-detection rate or detection threshold, completeness or deboosting corrections, (sub)mm number counts, the resolved fraction of the extragalactic background, or a source overdensity test around a target. Built from 95 ALMA papers (2013-2025), about 70 of them on-topic."
---

# Blind source extraction, completeness and number counts

Finds sources in an ALMA map without a prior position, decides which peaks are real, and corrects the
catalog for what was missed and for flux boosting so that counts (sources per flux per area) can be
computed. The two mistakes that matter most: (1) choosing a detection threshold without measuring the
false-detection rate on the inverted (negative) map, since at S/N 3.5-4.5 a few to tens of percent of
peaks are noise; and (2) quoting counts without the completeness, flux-boosting and effective-area
corrections, which all change fastest exactly at the faint end where new ALMA counts are claimed.

Counts below come from the pack (`packs/source-extraction-counts.md`): either its aggregate tables
(counts of matched steps, over all 95 papers) or my own count of pack lines, marked "(my count)". About
20-25 pack papers are clearly off-topic regex matches (SMBH dynamics, polarization, lens models, optical
SExtractor runs, EHT simulations, e.g. 2025ApJ...992..211N, 2016A&A...593A..44L, 2020A&A...636A...5R,
2015ApJ...811L..19W, 2020ApJ...895...84Y). My counts exclude them; the aggregate counts cannot, and I
say where that matters.

## When to use

- Blind continuum catalog of a single pointing, many archival pointings or a contiguous mosaic, usually
  at 1.1-1.3 mm, 870 um or 3 mm (deep fields: 2016ApJ...833...68A, 2020ApJ...897...91G,
  2018A&A...620A.152F, 2017ApJ...835...98U; archival multi-field: 2014ApJ...795....5O,
  2015A&A...584A..78C, 2018ApJ...869...71Z).
- Follow-up of single-dish sources to resolve multiplicity and get bright-end counts
  (2013MNRAS.432....2K, 2015ApJ...807..128S, 2018ApJ...860..161S, 2019MNRAS.487.4648S).
- Setting a detection threshold and reporting purity/fidelity and completeness for any ALMA detection list.
- Number counts, double power-law fits, and the fraction of the extragalactic background (EBL/CIB) resolved
  (2016ApJ...833...68A, 2015A&A...584A..78C, 2018A&A...620A.152F).
- Overdensity tests: counts around a quasar or in a protocluster field compared with blank-field counts
  (2015ApJ...806L..25S, 2018ApJ...867..153C, 2018PASJ...70...65U).
- Fainter supplementary catalogs that use priors from other wavelengths (2020A&A...643A..53F,
  2018MNRAS.479.3879W).

## When not to use

- Blind line searches in cubes, line fidelity in channels, line luminosity functions and redshifts: use
  `redshift-line-search`. The ASPECS line papers in this pack (2016ApJ...833...67W, 2020ApJ...902..110D)
  are covered better there; only their fidelity logic is borrowed here.
- Galactic dense cores and clumps, core mass functions, dendrograms/ClumpFind in star-forming regions: use
  `core-extraction-cmf` (pack examples it shares: 2020A&A...635A...2S, 2020ApJS..251...14H,
  2019MNRAS.483.1624B, 2018ApJ...853..160C).
- Mean signal of undetected sources (stacking on prior positions, faint-end EBL from stacks): use
  `stacking`. This skill handles individually detected sources.
- GMC catalogs and mass spectra from CO cubes: use `gmc-decomposition-virial` (2018ApJ...857...19F,
  2017ApJ...841...43E are only mass-spectrum examples here).
- Imaging choices themselves (weighting, taper, cleaning depth): `imaging-choices`. Source sizes from
  visibilities: `uv-plane-fitting`.

## Steps

### 1. Build the detection image and its noise map
- Goal: an S/N map whose noise is close to Gaussian and uniform in meaning across the field.
- Method: extract on the map NOT corrected for the primary beam, where noise is flat, and correct fluxes
  for the primary beam afterwards (2018ApJ...869...71Z, 2015ApJ...807..128S, 2016ApJ...833...68A,
  2014ApJ...795....5O; 5 papers, my count). Noise estimates seen: the 68th percentile of pixel values
  (2018ApJ...869...71Z); a local rms per source (2016ApJ...833...68A, 2019A&A...632A..38A); 50 random
  0.5'' apertures inside the primary beam (2019MNRAS.487.4648S); random blank-sky apertures
  (2014ApJ...788..125S).
- Deep surveys run on both a natural-weight and a tapered map, with separate thresholds, to catch
  extended sources (2020ApJ...897...91G, 2025ApJS..278...45F, 2018A&A...620A.152F).
- Set the search area: within the primary-beam FWHM (2015ApJ...807..128S), out to 1.3x the PB FWHM
  (2018ApJ...869...71Z), or down to PB response 0.1-0.2 (2020ApJ...897...91G, 2025ApJS..278...45F).
- Software: CASA tclean products; mask bright targeted sources when the field was pointed at them.

### 2. Find peaks
- Goal: a candidate list deeper than the final cut, so fidelity and completeness can be modelled.
- Method: two thresholds, a low "extraction/flood" level and a higher peak cut:
  - SExtractor, 6 contiguous pixels above 1.8 sigma, keep peak S/N > 4.0 (2014ApJ...795....5O);
    min area 5 pixels, down to 2.5 sigma local, main sample > 3.5 sigma (2016ApJ...833...68A);
    > 3 sigma peaks, 4 sigma final (2015ApJ...807..128S); peaks > 2 sigma then S/N cut from the
    positive/negative comparison (2025ApJS..278...45F).
  - BLOBCAT flood fill with sigma_p = 4.8 and sigma_f = 2.7, chosen by scanning sigma_p 4-6 and
    sigma_f 2.5-4 for purity >= 0.8 (2018A&A...620A.152F). SEAC seed 5 sigma, flood 3 sigma
    (2019A&A...632A..38A).
  - LineSeeker run on a continuum map: pixels with S/N >= 2 grouped by DBSCAN (2020ApJ...897...91G).
  - Peaks above 2.5 sigma fitted with elliptical Gaussians by MH-MCMC (2013MNRAS.432....2K); 2D Gaussian
    fits at S/N > 3.5 whose size is consistent with the beam within 1.5x (2015A&A...584A..78C).
- Visual inspection removes artifacts and peaks in high-noise regions (2020A&A...635A...2S removed 43 of
  185 automatic detections, a Galactic example).

### 3. Measure purity / fidelity from the inverted map
- Goal: the fraction of candidates at each S/N that are noise.
- Method: multiply the map by -1, run the identical extraction, and compare counts:
  fidelity (purity) = (N_pos - N_neg)/N_pos (2016ApJ...833...69D, 2025ApJS..278...45F,
  2018A&A...620A.152F), or fit it vs S/N with an error function (2016ApJ...833...68A; the same form for
  lines in 2016ApJ...833...67W). At least 10 continuum papers in the pack use the inverted map (my count).
- Choose the threshold from it: 4.8 (natural) and 4.2 (tapered) for deep maps, 5.0/4.4 for wide maps
  (2025ApJS..278...45F); 50% fidelity at S/N 4.3 natural and 3.3 tapered (2020ApJ...897...91G,
  2020ApJ...901...79A); 98% purity at S/N >= 4.3 (2018ApJ...860..161S).
- Alternatives: blank-field simulations (300 simulated maps, 2015A&A...584A..78C); injecting into
  source-removed maps to count spurious recoveries (1.6% spurious above 3.5 sigma, 2013MNRAS.432....2K);
  expected false positives from the number of independent beams (4.8 sigma gives 0.6 expected,
  2020A&A...640A..27V); a specific probability of false alarm per peak (2017A&A...604A.115V).
- Counterpart checks add evidence: three ASPECS sources without NIR counterparts are flagged as likely
  false (2020ApJ...897...91G); prior positions allow a lower threshold (5.0 sigma at IRAC positions vs
  5.5 blind, 2018MNRAS.479.3879W; 3.5-4.8 sigma with IRAC/VLA matches, 2020A&A...643A..53F).

### 4. Completeness and flux boosting from injected sources
- Goal: recovered fraction vs flux (and size), and the output/input flux ratio vs S/N.
- Method: inject artificial sources into the real map (or a noise image), rerun the identical extraction,
  match within a radius, repeat many times. Setups vary widely; see the table below and
  `references/parameters.md`. Typical: point sources or beam-shaped sources at random positions
  (2014ApJ...795....5O, 2018ApJ...869...71Z), 20,000 point sources into a uv jackknife noise image
  (2020ApJ...897...91G), 2 x 10^4 simulated maps with a power-law flux distribution of index -2 and sizes
  0-0.5'' (2015ApJ...807..128S).
- Match radius: one synthesized beam (2018ApJ...869...71Z), 0.6'' (2018ApJ...860..161S,
  2019MNRAS.487.4648S), 1'' (2016ApJ...833...68A, 2018PASJ...70...65U).
- Flux boosting: divide each flux by the median S_out/S_in at its S/N (2014ApJ...795....5O); spline fit in
  0.25 sigma bins (2015ApJ...807..128S). Sizes seen: 1.09 at S/N 3.5 (2015A&A...584A..78C); ~11% at 50%
  fidelity and <= 3% at S/N ~5 (2020ApJ...897...91G).
- Completeness values seen: 93% above 4 sigma, ~100% at 5.5 sigma (2015ApJ...807..128S); ~99% above
  3.5 sigma (2013MNRAS.432....2K); 94% at 1.2 mJy for point sources (2018A&A...620A.152F).
- Inject extended sources too: ALMA sizes of 0.2-0.9'' FWHM (2018A&A...620A.152F) or 0-0.9''
  (2019MNRAS.487.4648S). Point-only tests overestimate completeness (2019MNRAS.483.1624B,
  2020ApJS..251...14H).

### 5. Measure fluxes and sizes
- Goal: total flux densities that are not biased low for resolved sources.
- Method: 2D Gaussian fit, peak flux for unresolved sources (2016ApJ...833...68A); aperture flux in a
  0.8'' radius with a 4% aperture correction (2015ApJ...807..128S); point-source peak flux from an MCMC
  fit (2013MNRAS.432....2K); circular Gaussian in the uv plane with CASA uvmodelfit, treating sizes below
  theta_min = 0.88 theta_beam / sqrt(S/N) as unresolved (2020A&A...643A..53F). 2018A&A...620A.152F
  compared PyBDSM, GALFIT, BLOBCAT and uvmodelfit before choosing.
- Software: CASA imfit (4 matched steps), CASA uvmodelfit (2), GALFIT (8, but mostly optical/IR images).

### 6. Effective area and counts
- Goal: differential n(S) and cumulative N(>S) in deg^-2 with honest errors.
- Method: each source contributes (1 - f_contam) / (C(S) A_eff(S)) to its bin (2014ApJ...795....5O,
  2015A&A...584A..78C, 2018ApJ...869...71Z), or P_j / C_j / A (2016ApJ...833...68A), where A_eff(S) is the
  area in which a source of flux S would pass the S/N cut given the primary-beam-weighted noise
  (A_survey = sum C_i A_i, 2015A&A...584A..78C). 2013MNRAS.432....2K weights each source by recovered and
  spurious fractions and scales area as (88/126) x 0.35 deg^2.
- Bins: dlogS = 0.2 (2014ApJ...795....5O, 2015A&A...584A..78C); 0.25 differential and 0.1 cumulative
  (2020ApJ...897...91G). With few sources, use cumulative counts only (2016ApJ...833...68A).
- Errors: Poisson with Gehrels small-number intervals (2015A&A...584A..78C, 2025ApJS..278...45F) plus
  flux-error resampling, 1000 draws (2013MNRAS.432....2K, 2020ApJ...897...91G); cosmic variance with the
  Moster et al. 2011 tool (2015A&A...584A..78C) or stated as omitted (2018A&A...620A.152F).
- Robustness: recompute with tighter PB cuts (PB >= 0.5 and >= 0.9; faint end unchanged,
  2020ApJ...897...91G); drop possibly lensed sources (< 1 sigma change, 2015ApJ...807..128S).

### 7. Fit and compare the counts
- Model: double power law, N(>S) = (N0/S0) [ (S/S0)^alpha + (S/S0)^beta ]^-1 (the form in the pack
  aggregates); a Schechter form was tried and rejected at 3 mm (2018ApJ...869...71Z).
- Fitters: chi-square Levenberg-Marquardt (2018ApJ...869...71Z); least squares with Trust Region
  Reflective (2018A&A...620A.152F); P(D) forward modelling of the pixel histogram with a Cash statistic
  on a parameter grid, 1000 realizations per grid point (2020ApJ...897...91G). The cards often do not
  state the fit method (2015ApJ...807..128S).
- Convert other surveys to your wavelength before comparing: modified blackbody with beta = 1.5,
  Td = 35 K at z = 2.5 (2014ApJ...795....5O, 2015ApJ...806L..25S, 2017ApJ...835...98U,
  2018PASJ...70...65U; 4 papers, the most common choice); S proportional to nu^(2+beta) with beta = 1.8
  (2018ApJ...869...71Z); ALESS composite SED at z = 2.5 giving factors 2.4 and 3.1 from 870 um to 1.2 and
  1.3 mm (2015ApJ...807..128S); S870/S850 = 0.95 (2018ApJ...860..161S).
- EBL: integrate the corrected counts and compare with the Planck background (2016ApJ...833...68A:
  55% from detections, 80% adding bright end and stacking; 2018A&A...620A.152F: 13.5% at 0.8 mJy).

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Final S/N cut, blind continuum | 4-5 | 3.5 to 5.5 | about 16 (my count) | 2013MNRAS.432....2K (3.5), 2015ApJ...807..128S (4), 2025ApJS..278...45F (4.8), 2018ApJ...869...71Z (5), 2018MNRAS.479.3879W (5.5) |
| Cut at prior (counterpart) positions | 1 sigma or so below blind | 3.5 to 5.0 | 2 | 2018MNRAS.479.3879W, 2020A&A...643A..53F |
| Low extraction / flood level | 2-3 sigma | 1.8 to 3 | 8 (my count) | 2014ApJ...795....5O (1.8), 2020ApJ...897...91G (2), 2016ApJ...833...68A (2.5), 2018A&A...620A.152F (2.7) |
| Minimum pixels | 5-6 | 2 to 6 | 5 (my count) | 2016ApJ...833...68A (5), 2014ApJ...795....5O (6), 2018ApJ...867..153C (2 above 5 sigma) |
| Purity / fidelity accepted | >= 0.5 per source, or catalog purity >= 0.8 | 0.5 to 0.97 | 4 (my count) | 2020ApJ...901...79A (0.5), 2020ApJ...897...91G (0.5), 2018A&A...620A.152F (0.8), 2025ApJS..278...45F (>0.97) |
| Search radius | PB FWHM | PB FWHM to 1.3x PB FWHM; PB >= 0.1-0.2 | 4 | 2015ApJ...807..128S, 2018ApJ...869...71Z, 2020ApJ...897...91G, 2025ApJS..278...45F |
| Injected sources | thousands per map set | 100 to 2 x 10^4 | 10 (my count) | 2016ApJ...833...68A (100), 2013MNRAS.432....2K (7400), 2020ApJ...897...91G (20000) |
| Injected sizes | point and 0.2-0.9'' FWHM | 0 to 0.9'' | 4 | 2015ApJ...807..128S, 2018A&A...620A.152F, 2019MNRAS.487.4648S, 2016ApJ...833...68A (point) |
| Recovery match radius | 0.6-1'' or one beam | 0.6'' to 1'' | 5 | 2018ApJ...869...71Z, 2018ApJ...860..161S, 2016ApJ...833...68A |
| Flux boosting at threshold | about 10% near the cut | 1.09 at S/N 3.5; <= 3% at S/N 5 | 3 | 2015A&A...584A..78C, 2020ApJ...897...91G, 2015ApJ...807..128S |
| Count bin width | dlogS 0.2 | 0.1 (cumulative) to 0.25 | 3 | 2014ApJ...795....5O, 2015A&A...584A..78C, 2020ApJ...897...91G |
| SED for wavelength conversion | MBB beta 1.5, Td 35 K, z 2.5 | beta 1.5-1.8; ALESS or Bethermin2017 templates | 8 (my count) | 2017ApJ...835...98U, 2018ApJ...869...71Z, 2015ApJ...807..128S, 2020A&A...643A...2B |

Longer per-paper setups (injection numbers, flux ranges, fitted DPL parameters): `references/parameters.md`.

## Software

From the pack's "Software named in the matched steps" aggregate (matched steps over all 95 papers; the
off-topic papers inflate SExtractor and GALFIT):

| Software | Count | Used for |
|---|---|---|
| SExtractor (incl. 2.5.0, sewpy wrapper) | 39 + 1 + 1 | continuum peak finding (2014ApJ...795....5O, 2016ApJ...833...68A, 2025ApJS..278...45F). At least 8 of these steps run on HST/JWST/IRAC images in off-topic or counterpart steps (my count, e.g. 2025NatAs...9.1553F, 2020ApJ...889..137M) |
| CASA (tclean, simobserve, imfit, uvmodelfit) | 11, 2, 4, 2 | imaging, simulated observations for completeness (2020ApJS..251...14H, 2015A&A...584A..78C), fluxes and sizes |
| findclumps / LineSeeker | 7 / 3 | line searches (see `redshift-line-search`); LineSeeker also on a 1.2 mm continuum map (2020ApJ...897...91G) |
| BLOBCAT | 5 | flood-fill extraction with peak and flood thresholds (2018A&A...620A.152F, 2020A&A...643A..53F) |
| GALFIT | 8 | mostly optical/IR morphology; ALMA PSF flux fits in 2018A&A...620A.152F |
| Aegean | 3 | named in the aggregate only; no excerpt describes its settings |
| PyBDSF / PyBDSM | 2 / 1 | Gaussian-decomposition extraction, compared in 2018A&A...620A.152F |
| ClumpFind, astrodendro | 2, 1 | Galactic clumps (use `core-extraction-cmf`) |
| Moster et al. 2011 cosmic variance tool | 1 | cosmic-variance errors on counts (2015A&A...584A..78C) |

Recommendation: SExtractor or BLOBCAT on the non-PB-corrected S/N map are the most common blind finders in
the pack. Whatever the finder, run it unchanged on the inverted map and on the injected maps; the
correction terms are only valid for the exact configuration used.

## Pitfalls

- Threshold without a negative-map test. Contamination is 2% at 4 sigma in one catalog
  (2015ApJ...807..128S) but low-rms fields can have a high spurious fraction (2015ApJ...806L..25S), and one
  line-search paper treats negative-peak fidelity as an upper limit (2020ApJ...902..110D). Even at
  purity > 0.97, 1-2 of 69 sources may be spurious (2025ApJS..278...45F).
- Completeness tested only for point or beam-sized sources overestimates the recovered fraction
  (2019MNRAS.483.1624B, 2020ApJS..251...14H); fainter supplementary sources are larger (median 0.32'' vs
  0.18'', 2020A&A...643A..53F).
- Peak fluxes of marginally resolved sources may be low by about 20% (2020A&A...643A..53F); resolved flux
  can be missed in high-resolution maps (2016ApJ...833...68A).
- Targeted fields are not blank fields: counts below the parent survey limit are biased when pointings
  were centred on bright sources (2013MNRAS.432....2K, 2013ApJ...769L..27H). Exclude the target and its
  surroundings (2017A&A...605A..42C excluded 2 arcsec around a serendipitous source).
- Small areas: cosmic variance often dominates or is omitted (2018ApJ...869...71Z, 2016ApJ...833...68A,
  2018A&A...620A.152F; ~42-58% for a pencil beam in 2020ApJ...892...66M). Bright and faint ends rest on few
  sources (2015ApJ...807..128S).
- Requiring a counterpart biases the sample toward massive galaxies (2020A&A...643A..53F).
- Primary-beam edges: a phase-centre rounding error may have dropped ~11 galaxies at PB edges
  (2019MNRAS.487.4648S). CASA < 5.0 7m mosaic flux scaling overestimated Band 6 by ~8% and Band 3 by ~2%
  (2019MNRAS.483.1624B).
- Wavelength conversion is model-dependent; counts compared across bands inherit the assumed SED.
- What the cards rarely state (from the pack's "not stated" aggregate): CASA version (6 papers), flux
  calibrator and flux-scale uncertainty (5 + 3 + 2), image and cell size, the deboosting prescription, the
  source-finder parameters beyond the threshold, and the fit method for the double power law. Report these.

## Verification checks

What papers did:
- Inverted-map counts at each S/N, and purity = (N_pos - N_neg)/N_pos above the cut (2025ApJS..278...45F,
  2018A&A...620A.152F, 2015ApJ...807..128S).
- Injection-recovery for completeness and boosting, with input vs recovered flux agreeing within errors
  (2016ApJ...833...68A, 2020A&A...643A..53F).
- Counts stable under tighter PB cuts (2020ApJ...897...91G) and after removing lensed sources
  (2015ApJ...807..128S); deboosting robust to the assumed count slope (+/- 10%, 2015ApJ...807..128S).
- Two independent count estimates agree (direct counts vs P(D), 2020ApJ...897...91G); consistent boost
  from simulations and an analytic Eddington-bias prescription (2015A&A...584A..78C).
- Re-reduced archival fluxes match archive products (2018ApJ...869...71Z); ALMA fluxes summed in the
  single-dish beam match single-dish fluxes (median ratio 0.83 at 3.5 sigma, 2013MNRAS.432....2K).
- Counts compared with literature and models such as SIDES (2018A&A...620A.152F, 2014ApJ...795....5O).
- Counterpart fractions in HST/IRAC/VLA (2018A&A...620A.152F, 2020A&A...643A..53F).

What a careful referee adds:
- Is the expected number of false sources (sum of 1 - fidelity) stated for the final catalog?
- Were injections done with the same finder settings, the same map (not PB-corrected), and realistic sizes?
- Is A_eff(S) computed from the actual noise map, and are bins below 50% completeness flagged or dropped?
- Are Poisson (Gehrels), flux-resampling and cosmic-variance terms all in the error bars?
- For counts compared across wavelengths, is the conversion SED stated and varied?

## Source cards

Full list: `references/sources.md` (95 papers). Most informative for this technique:

- 2020ApJ...897...91G: LineSeeker on continuum, fidelity 50% at S/N 4.3, 20000 injections, P(D) fit.
- 2016ApJ...833...68A: SExtractor setup, erf fidelity and completeness, cumulative counts, EBL fraction.
- 2018A&A...620A.152F: BLOBCAT threshold scan, extended-source injections, DPL and Schechter fits.
- 2015ApJ...807..128S: aperture fluxes, 2 x 10^4 simulated maps, spline deboosting, bright-end counts.
- 2013MNRAS.432....2K: MCMC extraction, 7400 injections, 1.6% spurious at 3.5 sigma, resampled counts.
- 2015A&A...584A..78C: archival multi-field counts, boosting 1.09 at S/N 3.5, cosmic-variance errors.
- 2014ApJ...795....5O: SExtractor 1.8 sigma / 6 pixel setup, (1 - f_c)/(C A_eff) counts.
- 2018ApJ...869...71Z: 3 mm counts from 135 archival maps, 5 sigma, DPL by Levenberg-Marquardt.
- 2025ApJS..278...45F: natural and tapered thresholds from the positive/negative comparison.
- 2018ApJ...860..161S: 98% purity at S/N >= 4.3, 0.6'' recovery radius.
- 2019MNRAS.487.4648S: random-aperture noise, sized injections, PB-edge caveat.
- 2020A&A...643A..53F: prior-based supplementary catalog, theta_min for unresolved sources.
- 2017ApJ...835...98U: SSA22 catalog and counts, MBB conversion of literature counts.
- 2020A&A...640A..27V: threshold from the number of independent beams.
- 2017A&A...604A.115V: probability of false alarm per peak.
- 2016ApJ...833...67W: fidelity error-function form (line search).
- 2015ApJ...806L..25S: overdensity around quasars, spurious-fraction caveat.
- 2018ApJ...867..153C: overdensity test with injected unclustered sources.
- 2019MNRAS.483.1624B: completeness logistic fit, beam-sized-only caveat (Galactic).

=== references/parameters.md ===
# Per-paper settings for blind extraction, fidelity, completeness and counts

All values are from the evidence pack `packs/source-extraction-counts.md` (verified quotes in the cards).
"Not stated" means the card flags it as missing.

## Detection setups

| Bibcode | Finder | Detection image | Thresholds | Notes |
|---|---|---|---|---|
| 2014ApJ...795....5O | SExtractor | maps before PB correction | 6 contiguous pixels > 1.8 sigma; peak S/N > 4.0 | spurious count from negative map |
| 2016ApJ...833...68A | SExtractor | non-PB-corrected 1.2 mm map | min area 5 pixels (1.5''); extract to 2.5 sigma local; main sample > 3.5 sigma, counts extended to 3 sigma | 2D Gaussian fluxes, peak for unresolved |
| 2015ApJ...807..128S | SExtractor + CASA imfit | 0.8'' "detection" maps, non-PB-corrected | > 3 sigma peaks; 4 sigma cut gives 52 SMGs | 0.8'' radius aperture, 4% correction |
| 2025ApJS..278...45F | SExtractor 2.5.0 | natural and tapered, Wide and Deep | Wide 5.0 / 4.4; Deep 4.8 / 4.2 (natural / tapered); to 20% relative sensitivity | thresholds where positives exceed negatives |
| 2018A&A...620A.152F | BLOBCAT | S/N map of 0.60'' mosaic | sigma_p = 4.8, sigma_f = 2.7 (scan 4-6, 2.5-4) | purity >= 0.8 required |
| 2020ApJ...897...91G | LineSeeker (DBSCAN) | natural and tapered 1.2 mm | pixels S/N >= 2 grouped; fidelity 50% at 4.3 (natural), 3.3 (tapered) | DBSCAN eps/min samples not stated |
| 2013MNRAS.432....2K | IDL code, MH-MCMC Gaussian fits | 88 ALMA maps | peaks > 2.5 sigma; catalog > 3.5 sigma | point-source peak flux adopted |
| 2015A&A...584A..78C | 2D Gaussian fitting (tool not named) | 18 continuum maps | S/N > 3.5, size within 1.5x beam | 50 sources |
| 2018ApJ...869...71Z | CASA, iterative masking | S/N maps, uncorrected PB | 5 sigma; radius 1.3x PB FWHM | noise = 68th percentile of pixels |
| 2018ApJ...860..161S | not stated in pack | 870 um maps | S/N >= 4.3 gives 98% purity | recovery within 0.6'' |
| 2015ApJ...806L..25S | not stated in pack | quasar fields | 3.75 sigma; 5.25 sigma high-confidence in low-rms fields | high spurious fraction in low-rms fields |
| 2018MNRAS.479.3879W | not stated in pack | SMG fields | 5.5 sigma blind; 5.0 sigma at IRAC 3.6 um positions (15% contamination) | |
| 2020A&A...643A..53F | BLOBCAT + GALFIT | 0.60'' tapered image | 3.5-4.8 sigma with IRAC < 0.3'' or < 0.7'' plus radio | purity 48% within 0.7'' of IRAC |
| 2020A&A...640A..27V | blind peak search | disk survey map | > 4.8 sigma, 0.6 expected false positives from independent beams | |
| 2019ApJ...871..109P | not stated in pack | serendipitous fields | 3.9 sigma; 176 sources | no completeness or counts |
| 2018ApJ...867..153C | not stated in pack | quasar fields | two or more adjacent pixels above 5 sigma | |
| 2016A&A...586A..70L | SExtractor | wavelet-filtered Band 3+6+7 | 4.5 sigma, min 5 pixels | background counts vs Hatsukade et al. 2013 |
| 2019A&A...632A..38A | SEAC flood fill | ATCA / ALMA radio maps | seed 5 sigma, flood 3 sigma, local rms | Galactic cluster |

## Injection-recovery setups

| Bibcode | Injected | Repeats | Flux / S/N range | Sizes | Recovered if |
|---|---|---|---|---|---|
| 2018ApJ...869...71Z | random positions | 100 per S/N bin | S/N 3.0-7.0, step 0.1 | not stated | within one synthesized beam |
| 2020ApJ...897...91G | 20,000 point sources into uv jackknife noise image | | fluxes 0.03-2 mJy (P(D) grid) | point | |
| 2015ApJ...807..128S | 2 x 10^4 simulated maps | | power law index -2 | 0-0.5'' | |
| 2018A&A...620A.152F | 300 per run | 100 runs per flux | 0.5-2.4 mJy | 0.2-0.9'' FWHM (ALMA 1.4x smaller than HST H) | |
| 2015A&A...584A..78C | 4-8 per simulation | 1000 per map (completeness); 10^4 (boosting) | 0.05-1 mJy; S/N 3-8 | | S/N >= 3.5 |
| 2016ApJ...833...68A | 10 point sources | 10 (100 total) | 10-300 uJy | point | within 1'' |
| 2013MNRAS.432....2K | 5 per source-removed map | 16 per map (7,400 total) | | | |
| 2014ApJ...795....5O | flux-scaled synthesized beams | | S/N 2-9 | beam | |
| 2019MNRAS.487.4648S | | | power law index -2 | uniform 0-0.9'' FWHM | within 0.6'' |
| 2018ApJ...860..161S | | | | | within 0.6'' |
| 2018PASJ...70...65U | | | | | > 4 sigma and within 1.0'' |
| 2018ApJ...867..153C | unresolved, unclustered | | Fujimoto 2016 Schechter counts | point | |
| 2020ApJS..251...14H | 10 point sources, CASA simobserve + tclean | | | point | inside a pruned leaf |
| 2019MNRAS.483.1624B | 600 beam-sized Gaussians per mass bin | | | beam | ClumpFind rerun; logistic fit |

## Fidelity and completeness parameterizations

- Error function vs S/N for fidelity and completeness: fidelity A = log10(42), B = 1/4; completeness
  A' = log10(35), B' = 0.45; both 50% at 3 sigma (2016ApJ...833...68A).
- Line-search fidelity (same idea): C_3mm = 5.1, C_1mm = 5.0, sigma_3mm = 0.4, sigma_1mm = 0.8; 60/80/95%
  fidelity at S/N 5.17/5.34/5.57 (3 mm) (2016ApJ...833...67W).
- Gaussian noise tails plus a power-law signal, fitted to negative then positive peak distributions
  (2020ApJ...902..110D).
- Per-source weight p = 2 - f_recovered - f_spurious, with f vs S/N parametrizations not stated
  (2013MNRAS.432....2K).

## Count fits reported

| Bibcode | Band | Model and fitter | Parameters |
|---|---|---|---|
| 2020ApJ...897...91G | 1.2 mm | differential DPL; direct counts and P(D) (Cash statistic grid) | S0 = 0.10 +/- 0.02 mJy, N0 = (4.4 +/- 0.6) x 10^4 mJy^-1 deg^-2; P(D) grid N0 1-100 x 10^3, S0 0.05-1.0 mJy, alpha 1.5-5, beta -2 to 2 |
| 2015ApJ...807..128S | 870 um, S > 7.5 mJy | DPL, fit method not stated | S0 = 8.4 +/- 0.6 mJy, N0 = 390 (+110/-80) deg^-2, alpha = 1.9 +/- 0.2, beta = 10.5 (+3.0/-3.2) |
| 2018ApJ...869...71Z | 3 mm | cumulative DPL, chi-square Levenberg-Marquardt; Schechter rejected | alpha = 1.4 +/- 0.5, beta = 3.4 +/- 0.5, S0 = 0.11 (+0.22/-0.03) mJy |
| 2018A&A...620A.152F | 1.1 mm | DPL and Schechter, least squares (Trust Region Reflective) | completeness 94% at 1.2 mJy for point sources |
| 2013MNRAS.432....2K | 870 um | cumulative counts with 1000 flux resamples | N(> 4.2 mJy) = 167.3 (28.6) deg^-2 |
| 2014ApJ...795....5O | 1.2 mm | differential, dlogS = 0.2, Poisson errors | log n = 4.83 (+0.37/-0.45) at 0.13 mJy |

## Count errors

- Poisson (Gehrels) dominates in small fields (2015A&A...584A..78C); cosmic variance from the Moster et al.
  2011 tool with z = 3.5, dz = 3, M* = 10^10.5 Msun (2015A&A...584A..78C).
- 1000 Gaussian flux resamplings, scatter per bin added (2020ApJ...897...91G, 2013MNRAS.432....2K).
- Cosmic variance omitted (2018A&A...620A.152F); counts likely biased low by cosmic variance
  (2018ApJ...869...71Z); 42-58% for a pencil-beam survey (2020ApJ...892...66M).

=== EVIDENCE PACK (source-extraction-counts) ===
# Evidence pack: Blind source extraction, number counts and completeness (`source-extraction-counts`)

Scope: finding sources in continuum/line maps, false-positive rates, completeness and counts

Built from 95 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2013-2025.
Matcher (regex over analysis steps): `number counts|source extraction|blind (?:source|detection|search)|completeness|flux boosting|deboost|false detection|spurious|sextractor|pybdsf|blobcat|positive and negative|fidelity`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- high_z_galaxies: 67
- agn_and_quasars: 18
- star_formation: 15
- nearby_galaxies: 13
- cosmology: 10
- milky_way_ism: 8
- galaxy_clusters_and_sz: 8
- protoplanetary_disks: 3
- instrumentation: 2
- transients: 2
- other: 1
- debris_disks: 1
- stellar_physics: 1
- solar_system: 1

### Software named in the matched steps
- sextractor: 39
- casa: 11
- galfit: 8
- findclumps: 7
- blobcat: 5
- casa imfit: 4
- eazy: 4
- lineseeker: 3
- aegean: 3
- clumpfind: 2
- casa simobserve: 2
- casa uvmodelfit: 2
- iraf: 2
- aips: 2
- magphys: 2
- pybdsf: 2
- tclean: 1
- mpdaf: 1
- galpak3d: 1
- sextractor 2.5.0: 1
- ezgal: 1
- tinytim: 1
- drizzlepac/astrodrizzle: 1
- mgefit: 1
- sewpy: 1
- astrodendro: 1
- aatm: 1
- casa tclean: 1
- miriad imdiff: 1
- glafic: 1
- ps4c: 1
- camb: 1
- eht-imaging: 1
- pybdsm: 1
- ds9: 1
- iraf imexamine: 1
- moster et al. 2011 cosmic variance tool: 1
- seac: 1
- parseltongue: 1
- iraf daofind: 1

### Fitting methods (most common phrasings)
- chi-square Levenberg-Marquardt: 1
- maximum likelihood, flat priors: 1
- grid search minimizing Cash statistic C=-2lnL with Poisson likelihood: 1
- Gaussian line fits: 1
- MCMC: 1
- spline: 1
- Double power law; fitting method not stated: 1
- logistic function: 1
- non-negative combination of E, Sbc, Im and AGN templates: 1
- MGE fit: 1
- Power-law fit; no sampler stated: 1
- Maximum likelihood factor minimizing XX-YY image difference: 1
- MCMC; Gaussian priors on photometric redshifts of four image sets: 1
- Galfit PSF fits in 5x5 arcsec box; Sersic index fixed to 1 in comparison fits: 1
- least squares with Trust Region Reflective algorithm: 1
- GALFIT simultaneous fit with bounded parameters: 1
- Errorbars from 1000 bootstraps: 1
- error-function parameterization of fidelity vs S/N, not physically motivated: 1
- Gaussian noise tails plus power-law signal fitted to negative then positive distributions: 1
- Gaussian mixture model (2 components, full covariance chosen by BIC) after removing 19 AGN points; orthogonal distance …: 1
- MH-MCMC; fitting error from posterior after correcting for chain autocorrelation: 1
- Maximum likelihood (Rosolowsky 2005) accounting for mass uncertainties: 1
- double power law N(>S)=N'/S'[(S/S')^alpha+(S/S')^beta]^-1; fitting algorithm not stated: 1
- cubic spline: 1
- models scaled to data points: 1
- Monte Carlo 100 times per galaxy for 1 sigma errors: 1
- M* = C L^alpha power law per redshift bin: 1
- Double power law N(>S)=N'/S'[(S/S')^alpha+(S/S')^beta]^-1 fitted to blank-field counts: 1
- non-linear least squares; 1σ from variance of parameter estimates: 1
- Gaussian profile fit; integrated SNR over twice expected FWHM: 1
- Gaussian fit to tentative line: 1
- 2D Gaussian in image plane (imfit): 1
- Power-law fit with perturbation method (Curran 2014) for 1 sigma errors: 1
- single-component 2D Gaussian: 1
- Power-law extrapolation to five faintest count points for CIB: 1
- single Gaussian, weighted least squares: 1
- Gaussian profile, chi-square fit in uv plane: 1
- Gaussian line fit: 1
- three Sersic kernel: 1
- zero-point calibration with 2146 spec-z: 1

### Validation checks used
- Compared re-reduced fluxes with archive maps: 1
- Recovered within a synthesized beam: 1
- Schechter function also tried and rejected: 1
- flux boosting ~11% at fidelity 50%, <=3% at S/N~5: 1
- repeated with PB>=0.5 and PB>=0.9; faint end unchanged: 1
- compared to direct counts: 1
- Agrees with earlier G2 and G6 metallicities: 1
- chi2 minimisation and residual map inspection: 1
- Inverted maps give contamination of ~2% at 4 sigma: 1
- slope varied within Karim13 1-sigma changes correction by 10%: 1
- Removing three possibly lensed SMGs changes parameters by less than 1 sigma: 1
- purity p=(Npos-Nneg)/Npos > 0.97: 1
- Compared with ALCS DPL, other observations and models: 1
- Tested contamination and host reddening: 1
- Ideal NRMSE curve from convolved reference image: 1
- compared with Smith21 MGE: 1
- Visual inspection to remove sources in noisy regions and clean artifacts: 1
- Predicted fragments compared to higher-resolution observations (source 43: 2, source 44: 9 vs 7): 1
- Parameter study of delta and kernel in Appendix: 1
- Completeness resilient to atmospheric variation: 1
- Residuals consistent with thermal noise; CI emission XX/YY ~1 away from absorption: 1
- Three-halo model tested and rejected: 1
- Compared PS4C counts with DZ16 estimates: 1
- Observed FWHM 0.113'' matches l=0.04'': 1
- Tested on simulated map with known sources: 1
- Positive vs negative detections; HST counterpart fraction as a check: 1
- Consistency of methods; residuals below 3 sigma for 21/23: 1
- Comparison with SIDES and literature counts: 1
- Completeness via artificial sources: 1
- Cross-check with rho_* / <T_BBG>: 1
- SExtractor run gave 178 clouds, same slope in overlapping mass range: 1
- maps multiplied by -1 to count negative sources; 300 simulated blank-field maps: 1
- Compared with Hogg & Turner Eq. 4 prescription using Schechter prior; slopes consistent: 1
- Poisson errors dominate; counts from within one primary beam consistent: 1
- Visual inspection and comparison with Do10 8.6 GHz fluxes: 1
- n=2 for all components gives sizes within ~50%: 1
- Counts compared with Hatsukade et al. (2013): 1
- 4.8σ chosen to give <1 expected false positive (0.6): 1
- Fidelity from negative vs positive counts; completeness via simulated sources: 1
- Fidelity from negative/positive peak ratio treated as an upper limit: 1

### Key parameters and settings (bibcode: value)
- 2018ApJ...869...71Z: threshold 5 sigma; radius 1.3 x primary beam FWHM
- 2020ApJ...897...91G: fidelity 50% at S/N=4.3 (natural), 3.3 (tapered)
- 2020ApJ...897...91G: bins log S = 0.25 differential, 0.1 cumulative; area 1.16e-3 deg^2 (PB>=0.1)
- 2020ApJ...897...91G: N0=1-100e3 mJy^-1 deg^-2, S0=0.05-1.0 mJy, alpha=1.5-5, beta -2 to 2; fluxes 0.03-2 mJy; histogram bins 4.3 uJy/beam
- 2015ApJ...807..128S: 4 sigma threshold gives 52 SMGs
- 2015ApJ...807..128S: completeness 93% at >4 sigma, ~100% at 5.5 sigma
- 2015ApJ...807..128S: faint counts converted using ALESS composite SED at z=2.5 (factors 2.4 and 3.1)
- 2025ApJS..278...45F: Deep thresholds 4.8 (natural), 4.2 (tapered); regions down to 20% relative sensitivity
- 2020A&A...635A...2S: 185 automatic detections, 142 after manual removal
- 2020A&A...635A...2S: Completeness 2 Msun; temperature test 20-100 K, 100000 trials; epsilon0 = 0.4, p = 1.3
- 2020ApJS..251...14H: min value = 3x global noise (3 MJy/sr); min pixels ~ half average beam; min significance = global low noise
- 2020ApJS..251...14H: masses from flux assuming Td = 20 K
- 2016A&A...593A..44L: 2.5 km/s velocity channels; CI 12m data tapered at 1.5"
- 2018ApJ...866...48U: positional error 0.5'' for all images
- 2018ApJ...858...85P: r=0.05, Planck best fit cosmology
- 2018A&A...620A.152F: sigma_p = 4.8, sigma_f = 2.7
- 2020ApJ...889..137M: Effective area 0.41 deg2; 23 color-selected, 6 remaining after multi-band selection
- 2020ApJ...889..137M: T_BBG = T_age - T_SF - 0.2 Gyr, T_SF = 2 tau_SFH
- 2017ApJ...841...43E: 2 or more pixels above I(CO)=200 Jy/beam m/s; at least 2 channels above 2 sigma
- 2017ApJ...841...43E: 10 contiguous pixels above 10 sigma
- 2015A&A...584A..78C: S/N>3.5; 50 sources detected
- 2015A&A...584A..78C: boost ~1.09 at S/N=3.5
- 2015A&A...584A..78C: cosmic variance with z=3.5, dz=3, M*=10^10.5 Msun
- 2019A&A...632A..38A: seed 5 sigma, flood 3 sigma, local rms from noise map
- 2025NatAs...9.1553F: DETECT_MINAREA=9, DETECT_THRESH=2.0, DEBLEND_NTHRESH=64, DEBLEND_MINCONT=0.0001; Sersic n=1
- 2016ApJ...833...67W: Candidates kept within sqrt2 x primary beam radius at 3mm (53'' at 84 GHz, 39'' at 115 GHz) and 30.9'' radius at 1mm
- 2016ApJ...833...67W: C_3mm=5.1, C_1mm=5.0, sigma_3mm=0.4, sigma_1mm=0.8
- 2016ApJ...833...67W: Peak flux 0.22-1.00 mJy (3mm), 0.5-2.0 mJy (1mm); widths 50-500 km/s
- 2020ApJ...902..110D: FWHM 0-800 km/s, peak 0-3 mJy; drop completeness<0.2
- 2019ApJ...887...88E: Sigma_mol completeness ~4 Msun/pc2 (3 sigma, 10 km/s)
- 2013MNRAS.432....2K: 3.5 sigma limit: ~99% recovered, ~1.6% spurious
- 2013MNRAS.432....2K: A_ALMA = (88/126) x 0.35 deg^2
- 2025ApJ...995..219F: S/N>2.5 per channel across >=3 continuous channels
- 2016ApJ...833...68A: minimum area 5 pixels (1.5''); extraction down to 2.5 sigma local; main sample >3.5 sigma
- 2016ApJ...833...68A: 100 artificial sources total (10x10), matched within 1''; fidelity A=log10(42), B=1/4; completeness A'=log10(35), B'=0.45
- 2016ApJ...833...68A: extended to 3 sigma, where fidelity and completeness are both 50%
- 2020A&A...643A..53F: cross-match radius 0.60'' for VLA and K-band; IRAC considered within 0.7''
- 2020A&A...643A..53F: theta_min = 0.88 theta_beam/sqrt(S/N), theta_beam=0.60''
- 2018ApJ...857...19F: completeness limit 8e3 Msun
- 2014ApJ...795....5O: 6 contiguous pixels above 1.8 sigma; final SNR>4.0
- 2017ApJ...835...98U: 5 sigma detection limit; 17 FULL/LORES + 1 DEEP/HIRES-only source
- 2019ApJ...881...10B: distance D_L=35.8 and 28.0 Mpc for +-1 sigma
- 2015ApJ...806L..25S: threshold 3.75 sigma; high-confidence 5.25 sigma in low-rms fields
- 2018ApJ...860..161S: SNR>=4.3 gives 98% purity
- 2018ApJ...860..161S: recovery within 0.6 arcsec of injected position
- 2020ApJ...901...79A: fidelity >0.5 for main sample; 50% fidelity at S/N=4.3
- 2018ApJ...856..118H: log tau 8.5-10.0, age 0.1-10 Gyr, AV 0-3, solar metallicity
- 2019MNRAS.487.4648S: 50 random 0.5'' apertures in primary beam for noise
- 2019MNRAS.487.4648S: Injected fluxes from power law index -2, sizes uniform 0 to 0.9'' FWHM, recovery within 0.6''
- 2020ApJ...892...66M: Stellar masses from MAGPHYS using 0.37-8.0 um photometry plus 1.2 mm flux
- 2018ApJ...861L..18U: lognormal width 0.5 dex, 10^6 samples
- 2018PASJ...70...65U: recovered if >4 sigma and within 1.0 arcsec
- 2021A&A...645A.120F: CIV doublet ratio fixed to 2:1, common width, red component fixed 2.6 Å from blue
- 2017ApJ...848L..22B: DEBLEND MINCONT = 0.0005
- 2014ApJ...788..125S: 3 sigma detection threshold; errors from random blank-sky apertures
- 2018MNRAS.479.3879W: 5.5 sigma blind; 5.0 sigma at SIMPLE 3.6 um positions (15% contamination)
- 2021ApJ...908..163M: Nch=2-5, S/N threshold 1.5, 2, 2.5, 3; Npx=2,3,4
- 2017ApJ...850...83F: redshift bins 0-1, 1-2, 2-4, 4-6; L0 = Schechter L* at z~3
- 2020ApJ...905..147Y: redshift slices 4.403-4.585 and 5.135-5.85; luminosity bins 0.5 dex
- 2019ApJ...871..109P: threshold 3.9 sigma; 176 sources
- 2018ApJ...867..153C: source = two or more adjacent pixels above 5σ
- 2020ApJS..247...61F: HST mosaics at 0.06" pixel scale registered to Gaia; ECDFS E(B-V)=0.0069 mag
- 2017MNRAS.469.4683C: Clumps: >=5 pixels above 5 sigma residual
- 2019ApJ...887...37U: Rayleigh-Jeans conversion; area 1.69e4 arcsec^2; L'_upp=1e12, L'_min=1e8 K km/s pc^2
- 2017ApJ...849..154S: bins of 300 km/s stepped by 100 km/s, >4 sigma
- 2017A&A...605A..42C: |v|<500 km/s from Lya; primary beam FWHM 16 arcsec; exclude 2 arcsec around serendipitous source
- 2019ApJ...879...54L: segmentation threshold 1.5-3 times background rms
- 2019ApJ...882..136A: fidelity > 0.9 gives 16 candidates
- 2016ApJ...833...69D: fidelity = (Npos-Nneg)/Npos
- 2017PASJ...69...45H: low threshold >= 4.5
- 2017MNRAS.469.2235K: initial r_e = 1 kpc, n=1.4; fit region 2 arcsec square


### Assumptions (bibcode: value)
- 2018ApJ...869...71Z: Fluxes scaled to 3 mm with S proportional to nu^(2+beta), beta=1.8
- 2018ApJ...869...71Z: Optically thick SEDs at rest-frame lambda<100 um
- 2020ApJ...897...91G: double power-law number counts
- 2015ApJ...807..128S: Salpeter IMF for SFR; S870-LFIR relation from ALESS
- 2019MNRAS.483.1624B: Tested only beam-size sources, likely overestimating completeness
- 2025ApJS..278...45F: Td=35 K, beta=1.8
- 2018Sci...362.1034D: Z=0.008, Chabrier IMF, exponentially declining SFHs
- 2020ApJ...895...84Y: Data 2 MS-CLEAN at nominal resolution is trusted reference
- 2025ApJ...992..211N: constant M/L, no dark matter in the center
- 2020A&A...635A...2S: IMF slope -1.35 (Salpeter/Kroupa) for comparison
- 2020ApJS..251...14H: Point-source-like emission model
- 2016A&A...593A..44L: Foreground CI absorber has negligible Tex and identical tau for X and Y
- 2018ApJ...858...85P: Polarization angle uniformly distributed; C_B ≈ C_E ≈ C_U ≈ C_Q
- 2015ApJ...811L..19W: COND evolutionary models; 23 Myr age
- 2018A&A...620A.152F: sources point-like in 0.60 arcsec mosaic
- 2018A&A...620A.152F: ALMA sizes 1.4 times smaller than HST H-band sizes
- 2020ApJ...889..137M: All three candidates are real BBGs at 4.8<=z<=7.8
- 2017ApJ...841...43E: Bruzual & Charlot models, solar abundance, exponentially decaying SFH with 10 Myr decay time
- 2016ApJ...833...67W: Negative candidates are all noise peaks; no absorption expected
- 2016ApJ...833...67W: Low (Milky Way) and high (M82) excitation bounds
- 2019ApJ...887...88E: Fixed inclination 70 deg
- 2013MNRAS.432....2K: Gaussian flux errors
- 2014ApJ...795....5O: Modified blackbody beta=1.5, Td=35 K at z=2.5 for flux/SFR scaling
- 2016ApJ...823..160D: same dust temperatures in Chamaeleon I as in Perseus; emission compact/unresolved
- 2017ApJ...835...98U: Literature counts scaled to 1.1 mm with modified blackbody beta=1.5, T=35 K, z=2.5
- 2019ApJ...881...10B: M_BH proportional to adopted angular size distance
- 2015ApJ...806L..25S: literature counts converted to 870 um with modified blackbody beta=1.5, Td=35 K, z=2.5
- 2018ApJ...853..160C: Artificial cores have synthesized-beam shape; positions random scaled to 7-m flux profile
- 2018ApJ...860..161S: S870/S850 = 0.95
- 2018ApJ...856..118H: BC03 templates, exponentially declining SFH, Calzetti extinction, Chabrier IMF
- 2019MNRAS.487.4648S: Intrinsic source sizes <0.6'' FWHM
- 2018PASJ...70...65U: Fluxes scaled to 1.1 mm with modified blackbody, beta=1.5, T=35 K, z=2.5
- 2020ApJ...905..147Y: Area A=2 sq.deg (cancels out)
- 2020A&A...643A...2B: Fluxes converted to 850 um using z=2.5 main-sequence Bethermin2017 SED template
- 2018ApJ...867..153C: Injected sources unresolved and unclustered; blank-field Fujimoto2016 Schechter counts
- 2020ApJ...904..130V: candidates with |dv|<2000 km/s taken as [C II] companions
- 2017MNRAS.469.4683C: E(B-V) 0 to 0.9 mag, Calzetti law
- 2019ApJ...887...37U: Faint-end slope alpha=-0.2 fixed
- 2016A&A...596A..75S: ALMA source treated as point-like at Ks position in I814 prior
- 2016ApJ...833..195W: Optically faint population is 41% of faint-end EBL


### Limitations the authors admit
- 2018ApJ...869...71Z: Counts likely biased low by cosmic variance; small sample
- 2020ApJ...897...91G: Three sources lack NIR counterparts and are likely false detections
- 2019MNRAS.485.1595P: CO-to-H2 conversion factor is uncertain, so masses are expressed as functions of alpha_CO
- 2019MNRAS.485.1595P: Analysis of G0 hampered by the bright quasar; GalPak3D did not converge for several galaxies
- 2015ApJ...807..128S: Small number statistics at both ends of the counts
- 2019MNRAS.483.1624B: CASA <5.0 7m mosaic flux scaling issue: Band 6 overestimated ~8 per cent, Band 3 ~2 per cent, not corrected
- 2019MNRAS.483.1624B: Completeness tested only for beam-sized sources
- 2025ApJS..278...45F: 1-2 sources may be spurious; no completeness correction for IRLF; z>9 detections marginal
- 2018Sci...362.1034D: U1 may be at a different redshift; stellar mass and SFR uncertain by factor of 2
- 2020ApJ...895...84Y: SpM images have larger asymmetric residuals due to self-calibration with MS-CLEAN; degree of super-resolution for Data 2 not established
- 2025ApJ...992..211N: Distance uncertainty (69.3 vs 46.4 Mpc) gives ~30% systematic in MBH, dominant error
- 2020A&A...635A...2S: Temperatures assumed rather than measured; unresolved multiplicity biases CMF
- 2020A&A...635A...2S: Low number statistics limit Q-parameter conclusions
- 2020ApJS..251...14H: Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2
- 2016A&A...593A..44L: Absolute flux uncertain (~20%) because Titan scans were largely flagged; single epoch only.
- 2018ApJ...866...48U: Mass and concentration strongly correlated so mass systematic uncertainty may be large
- 2018ApJ...858...85P: Planck detections may be biased upward toward high fractional polarization; forecasts limited to ≤150 GHz, excluding dusty galaxies
- 2020ApJ...891...64F: Lens model poorly constrained; magnification uncertain by a factor of a few
- 2017A&A...604A.115V: Flux measurements of 1b+3b are highly uncertain because of source shape
- 2015ApJ...811L..19W: Disk brightness vs separation unreliable owing to residual PSF features; sliver at only 3.1 sigma and may arise from KLIP self-subtraction
- 2024ApJ...967...27R: Low number statistics and low completeness
- 2020A&A...636A...5R: Only one GRMHD snapshot and two electron models used; results may not generalize.
- 2018A&A...620A.152F: Cosmic variance not included in count errors; the HST-dark status of three sources needs further investigation
- 2020ApJ...889..137M: SFRD is a lower limit; contamination by AGN not excluded; spectroscopic confirmation needed
- 2017ApJ...841...43E: Mass ratios are not true efficiencies as the association of complex with cloud is unknown
- 2015A&A...584A..78C: CIB uncertainties prevent a precise resolved fraction; no source redshifts or SEDs
- 2019A&A...632A..38A: Diffuse emission may be misattributed to stars; errors are potentially underestimates
- 2025NatAs...9.1553F: Magnification systematic uncertainty up to ~25%
- 2025NatAs...9.1553F: Clump number may increase with better data; ALMA beam larger than clumps so gas mass only for 7 clumps
- 2016A&A...586A..70L: Irregular, sparse time sampling prevents robust variability analysis; VI are lower limits.
- 2020A&A...640A..27V: Stellar mass differences and binarity cannot be accounted for in the comparison
- 2020A&A...640A..27V: Kaplan-Meier assumption of nondetection independence not met at low masses
- 2024ApJ...964...18C: Data concentrated in narrow metallicity range 8.4-8.6, limiting metallicity analysis
- 2016ApJ...833...67W: Survey area small, limited by ALMA early-science time
- 2020ApJ...902..110D: Constant alpha_CO may be invalid at z>3
- 2019ApJ...887...88E: Large scatter, projection effects and warped disk uncertainty in the KS fits; XCO uncertainty in CND
- 2013MNRAS.432....2K: Counts below the LESS flux limit are biased because fields were targeted near brighter sources
- 2025ApJ...995..219F: Lens model systematics not included; mass-sheet degeneracy possibly unbroken
- 2025ApJ...995..219F: Gas mass is a lower limit given alpha_CO
- 2019MNRAS.485.1188B: Planck and ALMA data are non-simultaneous so blazar variability adds dispersion
- 2020ApJ...895..126H: Oph and Tau/Aur SMA samples are flux-limited and biased bright
- 2020ApJ...895..126H: Correlation tests do not include upper limits and uncertainties
- 2016ApJ...833...68A: Small area makes counts and EBL fraction subject to cosmic variance.
- 2016ApJ...833...68A: Flux may be missed for resolved sources given small beam; beta result affected.
- 2020A&A...643A..53F: Requiring an IRAC counterpart may reject real sources and bias toward massive galaxies.
- 2020A&A...643A..53F: Peak fluxes for unresolved sources may be underestimated by about 20%.
- 2018ApJ...857...19F: Missed flux relative to APEX (median 63% recovered), possibly low surface brightness emission
- 2018ApJ...857...19F: Sampled range of environments limited to inner rising rotation curve
- 2014ApJ...795....5O: Small number of fields and unknown redshift distribution of faint SMGs give large bias uncertainties; SLE-1 could be systematic noise
- 2016ApJ...823..160D: Mass uncertainties dominated by dust temperature and opacity assumptions
- 2016ApJ...823..160D: Only two simulations; full parameter space needed
- 2024A&A...685A..80Z: Clump C is tentative and needs confirmation; dynamical modelling is beyond scope
- 2017ApJ...835...98U: Absolute flux uncertainty (20%) not included; missing fainter/diffuse emission for AzTEC1; seven sources lack zspec so field counts are conservative
- 2020MNRAS.495.2332K: Residual jet contamination and lensing remain possible; small survey area limits constraint on shape of counts.
- 2019ApJ...881...10B: Model not a formally acceptable fit (chi^2_nu=1.179); correlated noise; local irregularities in velocity/dispersion fields
- 2019ApJ...881...10B: Distance disagreements among estimates imply M_BH may lie in (2.0-3.8)e9 Msun
- 2015ApJ...806L..25S: High spurious fraction in low-rms fields; sub-sample lacks most radio-loud sources
- 2018ApJ...853..160C: Temperature assumed uniform at 20 K; masses uncertain by factor ~2; possible fragmentation at higher resolution
- 2018ApJ...860..161S: Multiplicity is a lower limit since catalogue is incomplete at 1 mJy
- 2018ApJ...860..161S: Spectroscopic coverage sparse so photo-zs used
- 2020ApJ...901...79A: MAGPHYS stellar masses may be systematically underestimated; small source numbers may drive redshift trend
- 2018ApJ...856..118H: Gas mass may be overestimated by ~1.5 if cluster galaxies are more metal-rich
- 2018ApJ...856..118H: Patchy Band 7 coverage so number density is a lower limit
- 2013ApJ...769L..27H: Counts from targeted fields may show excess; comparison with 870 um counts not quantitative
- 2019MNRAS.486.4304S: Redshift fixed at 2 and photo-z uncertainty may contaminate SFRs for outer sources
- 2019MNRAS.487.4648S: Phase-centre rounding error may have missed ~11 galaxies at primary beam edges
- 2020ApJ...892...66M: Pencil-beam survey affected by cosmic variance (~42-58%)
- 2020ApJ...892...66M: Dust-based gas may be biased against atomic phase; low-metallicity GDR relation uncertain
- 2018ApJ...861L..18U: Low-mass galaxy measurements subject to biases; central alpha_CO variation deferred
- 2013ApJ...768...91H: Some reliability estimates are lower limits; several maps are poor quality due to low elevation observations.
- 2018PASJ...70...65U: SMG redshifts mostly unknown; association with proto-cluster unconfirmed
- 2018PASJ...70...65U: Angular resolution not uniform; map insensitive to faint extended emission
- 2021A&A...645A.120F: Low S/N; Lyα and HeII severely affected by night sky lines
- 2021A&A...645A.120F: Mass uncertainty excludes errors on X_[CI], Q10, A10
- 2017ApJ...848L..22B: Merger-time interpretation assumes equal probability of all merger times
- 2014ApJ...788..125S: Stellar masses have systematic uncertainties up to 5x because SFHs are unconstrained
- 2018MNRAS.479.3879W: Spatial resolution ~1 arcsec insensitive to late-stage mergers, minor mergers and gas-poor companions
- 2018MNRAS.479.3879W: Targeted fields more sensitive to line-of-sight than sky-plane structure; small sample
- 2021ApJ...908..163M: Q10 cannot be constrained without other line ratios; the tentative line is not confirmed in Data1.
- 2019ApJ...884..112T: A significant fraction of the spatial overlaps may arise by chance
- 2019ApJ...884..112T: Small number of sources and solar-metallicity region only
- 2017ApJ...850...83F: Sample not complete at fixed stellar mass
- 2017ApJ...850...83F: Size measurement unreliable for compact/faint sources in low-resolution maps
- 2020ApJ...905..147Y: UV selection misses UV-faint [C II]-bright sources, so LFs are strict lower limits; the Schechter fit has large errors
- 2018MNRAS.475.1288S: Whole-galaxy SFRs cannot rule out short-timescale local impact
- 2019ApJ...871..109P: Sample incomplete and no completeness or number counts
- 2020A&A...643A...2B: Stacked-SED sample selection imperfect; conversion may be inaccurate for outliers
- 2018ApJ...867..153C: Sample is not formally complete; no redshifts for the continuum sources
- 2018ApJ...867..153C: Small field of view, cosmic variance, and foreground sources limit the test
- 2020ApJS..247...61F: Spitzer blending can overestimate stellar masses; about one-third have contaminated Spitzer photometry
- 2020ApJS..247...61F: f-factor is the largest uncertainty in the Halpha measurement
- 2018MNRAS.481.1631B: L_FIR depends on assumed dust temperature and SED from a single 1.3 mm point; beta errors are large
- 2020ApJ...904..130V: Single dust temperature assumed; position offsets not corrected for differential chromatic refraction; sizes only for bright central emission
- 2017MNRAS.469.4683C: Clump SFRs vary by up to ~1 dex between methods and clump R51/alpha_CO are poorly constrained
- 2021A&A...646A..76L: Field LF based on a single source; large uncertainties
- 2019ApJ...887...37U: Error on cross-shot noise is a lower estimate; CO(3-2)/CO(4-3) cannot be separated with low sensitivity
- 2017ApJ...849..154S: Gas and dynamical masses depend strongly on alpha_CO and assumed radius/inclination; comparison samples are small
- 2017ApJ...849..154S: FIR luminosities may be unreliable and driven by 1.25 mm flux
- 2017ApJ...846..108C: CO detection is only ~3 sigma peak SNR so 2D CO kinematics and central detail are limited
- 2017ApJ...846..108C: ALESS67.2 nature inconclusive
- 2016A&A...596A..75S: Herschel fluxes of the SMG derived through indirect procedure with unverified assumptions; Y-band scatters ~2 sigma from best fit
- 2019ApJ...874...27T: Photometric constraints are weak (large K_S uncertainty) and the metallicity uncertainty is large
- 2017A&A...605A..42C: Cycle 2 Band 6 sensitivity worse than requested due to phase calibrator failure
- 2017A&A...605A..42C: Blind-search reliability may be ~50% at S/N=5 per other works
- 2019ApJ...887..107F: Faint AGN or past AGN activity cannot be ruled out; faint continuum or satellites could mimic the broad wing
- 2019ApJ...882..138D: Local bin affected by cosmic variance and tiny volume
- 2017ApJ...839...58S: Constant size assumption makes optical depth and true Td lower limits
- 2019ApJ...879...54L: Foreground dust screen assumption means mass maps are a lower limit to central mass; sample biased to optically bright SMGs
- 2019ApJ...882..136A: Low number of sources gives large statistical uncertainties; half the sample unresolved in CO
- 2016ApJ...833...69D: rho(H2) is a lower limit as faint end not recovered; Poisson errors and cosmic variance large
- 2017PASJ...69...45H: One candidate may be spurious; LF from one source
- 2017MNRAS.469.2235K: Large uncertainties in morphological parameters for faint members
- 2017ApJ...842L..21N: Heterogeneous cluster and field samples; possible SFR systematics and selection bias
- 2016ApJ...833..195W: Low S/N prevents meaningful size constraint; EBL values are upper limits; stacked sample misses optically faint sources
- 2017A&A...602A..54M: 53% of spectral indices are lower limits; monochromatic dust temperature analysis is simplistic.
- 2017MNRAS.465L..89P: The association with the z=1.96 galaxy is not definitive
- 2017MNRAS.466..861D: Small field size and cosmic variance; faint sources' total fluxes uncertain
- 2017A&A...606A..17M: Gas masses depend on uniform Galactic alpha_CO; may be overestimated by factor >~8 if alpha_CO ~0.8
- 2017A&A...606A..17M: Selection bias at z>~3 toward warmer, brighter sources
- 2016ApJ...833...72B: Results depend strongly on assumed dust temperature and SED

### Settings cards flag as needed but not stated
- casa version: 6
- flux calibrator and flux scale uncertainty: 5
- flux scale uncertainty: 3
- bootstrap procedure details: 2
- image size and cell size: 2
- flux calibration uncertainty: 2
- cell size and image size: 2
- casa version and pipeline version: 2
- line-free channels used for continuum subtraction: 2
- uvmodelfit starting parameters: 2
- cell size and image size for tclean: 2
- exact per-map list of 135 maps and their rms: 1
- snr threshold used for candidate pixels beyond 5 sigma, mask handling details: 1
- flux deboosting prescription details: 1
- model code/grid for psi2 and z_cutoff fit: 1
- redshift info for the sources used: 1
- image size and cell size for tclean: 1
- which channels were flagged as line-contaminated: 1
- exact observation dates, configurations and time on source: 1
- lineseeker parameters (dbscan eps/min samples): 1
- grid spacing and sampling for p(d) parameter grid: 1
- flux density measurement aperture details (deferred to gl2019): 1
- magphys settings and galaxy properties (in aravena2019b): 1
- details of the triple power-law fit procedure: 1
- self-calibration solution intervals and imaging parameters for the continuum model: 1
- line-free channels for uvcontsub and the fit order: 1
- cleaning threshold, masks and niter in tclean: 1
- duchamp parameters other than the 5-sigma threshold: 1
- galpak3d priors, model choice and initial conditions: 1
- simulation parameters and post-processing details (in a separate paper): 1
- alma flux scale uncertainty: 1
- flux model/setup for j0238+166 beyond 0.59 jy and casa calibration script details: 1
- clean niter, threshold and mask details beyond sigma levels: 1
- exact parameters of spline flux deboosting fit: 1
- fit method (likelihood/sampler) for the double power law: 1
- ma et al. s870-lfir relation used for luminosity/sfr: 1
- scuba-2 beam model and 2014 august s2cls catalog (geach et al. in prep.): 1
- line-free channel/spw selections per field for continuum imaging: 1
- exact uv-trim values for band 3 and taper values per field (partly in table): 1
- auto-masking code is only in a thesis appendix: 1

## Paper excerpts (40 of 95, chosen for detail and spread over fields/years)

### 2018ApJ...869...71Z: Constraining the Volume Density of Dusty Star-forming Galaxies through the First 3 mm Number Counts from ALMA (2018; high_z_galaxies; archival_reuse)
- question: What are the 3 mm galaxy number counts from archival ALMA Band 3 data, and what do they imply for the volume density of DSFGs and their contribution to the CSFRD at z>4?
- step 2: Blind source extraction
  - method: SNR maps from uncorrected PB maps, noise = 68th percentile of pixels, 5 sigma threshold, iterative masking [2.2 Source extraction: "The noise is assumed to be the $68^{th}$ percentile of the distribution of pixel values of the map"]
  - software: CASA
  - parameter: threshold 5 sigma; radius 1.3 x primary beam FWHM [2.2 Source extraction: "here we adopt a conservative threshold of $5\sigma$ to minimize the contamination fraction"]
  - assumption: Fluxes scaled to 3 mm with S proportional to nu^(2+beta), beta=1.8 [Footnote 1: "assuming $S_\nu\propto\nu^{2+\beta}$, with $\beta=1.8$"]
  - validation: Compared re-reduced fluxes with archive maps [2.1 ALMA Band 3 archival data: "are in very good agreement with the values measured on the maps available through the archive"]
- step 3: Contamination, completeness, flux boosting
  - method: Inverted maps for false detections; Monte Carlo source injection (100 realizations per SNR bin) [2.3 Completeness: "After 100 realizations per SNR bin, ranging from 3.0 to 7.0 in steps of 0.1"]
  - validation: Recovered within a synthesized beam [2.3 Completeness: "A source is considered recovered if it is detected within a synthesized beam of the input random position."]
- step 4: Cumulative number counts and fit
  - method: N_i=(1-f_cont)/(zeta A_eff) summed; Monte Carlo and Poisson errors; double power law fit [3 Number Counts: "were inferred using a minimum $\chi^2$ method through a Levenberg-Marquardt algorithm"]
  - fitting: chi-square Levenberg-Marquardt [3 Number Counts: "were inferred using a minimum $\chi^2$ method through a Levenberg-Marquardt algorithm"]
  - validation: Schechter function also tried and rejected [3 Number Counts: "it reproduce neither the behavior of the data at the brightest flux densities"]
- step 5: Constrain IRLF evolution
  - method: Fit model number counts for psi2 (-6.5 to -2.0) and z_cutoff (9 to 5) by maximum likelihood with flat priors [4 Constraining the infrared galaxy lumi…: "through a maximum likelihood approach, using flat prior distributions for both $\psi_2$ and $z_{\rm cutoff}$"]
  - assumption: Optically thick SEDs at rest-frame lambda<100 um [4 Constraining the infrared galaxy lumi…: "The constraints described above assume optically thick SEDs at rest-frame $\lambda<100\,\rm\mu m$"]
  - fitting: maximum likelihood, flat priors [4 Constraining the infrared galaxy lumi…: "using flat prior distributions for both $\psi_2$ and $z_{\rm cutoff}$"]
- result: Sources detected >5 sigma = 16 ± not stated sources [2.2 Source extraction: "The 16 serendipitously-detected 3 mm sources at $>5\sigma$"]
- result: Double power-law alpha = 1.4 ± 0.5 dimensionless [3 Number Counts: "$\alpha=1.4\pm0.5$ and $\beta=3.4\pm0.5$"]
- result: Double power-law S0 = 0.11 ± +0.22/-0.03 mJy [3 Number Counts: "$S_0=0.11^{+0.22}_{-0.03}\rm\,mJy$"]
- result: psi2 best fit = -4.2 ± +1.6/-0.8 dimensionless [4 Constraining the infrared galaxy lumi…: "best-fit value of $\Psi_2=-4.2^{+1.6}_{-0.8}$"]
- result: DSFG share of CSFRD at z~4-5 = 35-85 ± 68% confidence interval percent [4 Constraining the infrared galaxy lumi…: "DSFGs contribute $\approx35-85\%$ of the total CSFRD at $z\approx4-5$"]
- result: False detection rate at 5 sigma = <=5 ± not stated percent [2.3 Completeness: "a false detection rate of $\lesssim5\%$ is expected at our adopted threshold"]
- limitation (authors): Counts likely biased low by cosmic variance; small sample [3 Number Counts: "These estimations are likely to be low biased by cosmic variance"]
- not stated (card): Exact per-map list of 135 maps and their rms; SNR threshold used for candidate pixels beyond 5 sigma, mask handling details; Casa version; Flux deboosting prescription details; Model code/grid for psi2 and z_cutoff fit; Redshift info for the sources used

### 2020ApJ...897...91G: The ALMA Spectroscopic Survey in the HUDF: Deep 1.2 mm Continuum Number Counts (2020; high_z_galaxies, cosmology; large_program_or_survey)
- question: What are the deep 1.2 mm continuum number counts in the HUDF, do they flatten at faint flux densities, and what fraction of the 1.2 mm extragalactic background light do the detected sources recover?
- step 2: Source extraction, fidelity, completeness
  - method: LineSeeker with DBSCAN on S/N>=2 pixels; fidelity from negative/positive counts; completeness by injecting 20,000 point sources into uv jackknife noise image [3.1 Source search: "We selected all the pixels with new $\rm{S/N}\geq2$ and grouped them together using Density-Based Spatial Clustering of Applications with Noise (DBSCAN) algorithm"]
  - software: LineSeeker
  - parameter: fidelity 50% at S/N=4.3 (natural), 3.3 (tapered) [3.1 Source search: "($\rm S/N=4.3$ for the natural image and $\rm S/N=3.3$ for the tapered image)"]
  - validation: flux boosting ~11% at fidelity 50%, <=3% at S/N~5 [3.1 Source search: "We estimate an excess of $\approx11\%$ in the measured flux density for the sources detected with fidelity equal to $50\%$."]
- step 3: Direct number counts
  - method: sum of fidelity/completeness over bins divided by area; errors Poisson plus 1000 Gaussian resamplings [3.2 Direct number counts: "We repeated this process 1000 times and measured the scatter per bin."]
  - parameter: bins log S = 0.25 differential, 0.1 cumulative; area 1.16e-3 deg^2 (PB>=0.1) [3.2 Direct number counts: "The size of the bins is $\log{S_{\nu}}=0.25$ for the differential number counts and $\log{S_{\nu}}=0.1$ for the cumulative number counts."]
  - validation: repeated with PB>=0.5 and PB>=0.9; faint end unchanged [3.2 Direct number counts: "the number counts in the faint end remained the same"]
- step 5: P(D) forward modeling
  - method: inject sources following double power law into blank image, convolve with dirty beam, add noise image, compare pixel histogram to dirty image; 1000 iterations per parameter set [3.3.3 P(D) analysis: "This process was repeated 1000 times to obtain the pixel distribution of noise plus injected sources for a given combination of parameters."]
  - software: tclean
  - parameter: N0=1-100e3 mJy^-1 deg^-2, S0=0.05-1.0 mJy, alpha=1.5-5, beta -2 to 2; fluxes 0.03-2 mJy; histogram bins 4.3 uJy/beam [3.3.3 P(D) analysis: "$\alpha=1.5\text{--}5$ and $\beta$ between $-2$ and $+2$"]
  - assumption: double power-law number counts [3.3.3 P(D) analysis: "we assumed that the differential number counts can be well described by a double power-law function"]
  - fitting: grid search minimizing Cash statistic C=-2lnL with Poisson likelihood [3.3.3 P(D) analysis: "we minimize the associated quantity given by"]
  - validation: compared to direct counts [5.1 Number Counts: "the results from the two independent method show excellent agreement"]
- result: Number of high-fidelity sources = 35 ± not stated sources [abstract: "We detect 35 sources at high significance (Fidelity $\geq0.5$), 32 of these have well characterized near-infrared HST counterparts."]
- result: Differential DPL break S0 = 0.10 ± ±0.02 mJy [Table 2: "$0.10 \pm 0.02$"]
- result: Differential DPL N0 = 4.4e4 ± ±0.6e4 mJy^-1 deg^-2 [Table 2: "$(4.4\pm0.6)\times10^4\thinspace{\rm mJy^{-1}deg^{-2}}$"]
- limitation (authors): Three sources lack NIR counterparts and are likely false detections [4 Results: "make them good candidates to be false detections"]
- not stated (card): Image size and cell size for tclean; Which channels were flagged as line-contaminated; Exact observation dates, configurations and time on source; LineSeeker parameters (DBSCAN eps/min samples); Grid spacing and sampling for P(D) parameter grid; Flux density measurement aperture details (deferred to GL2019); MAGPHYS settings and galaxy properties (in Aravena2019b); Details of the triple power-law…

### 2019MNRAS.485.1595P: Multiphase circumgalactic medium probed with MUSE and ALMA (2019; nearby_galaxies, milky_way_ism; observational_alma_primary)
- question: What galaxies (stellar and molecular gas) are associated with the strong HI absorber at z=0.313 toward Q1130-1449, and is the absorption linked to a single galaxy or a group/CGM structure?
- step 4: MUSE line fluxes, SFR and metallicity
  - method: Gaussian fits to nebular lines, Balmer-decrement dust correction, Kennicutt98 SFR, strong-line metallicities [3.2 Physical Properties of the Galaxy G…: "We measured the emission fluxes from a Gaussian fit to the nebular lines."]
  - software: MPDAF, Sextractor
  - fitting: Gaussian line fits [Physical Properties of the Galaxy Group: "We measured the emission fluxes from a Gaussian fit to the nebular lines."]
  - validation: Agrees with earlier G2 and G6 metallicities [3.2 Physical Properties of the Galaxy G…: "Our estimates agreed within the errors with earlier measurements of G2 and G6 metallicities by (cite: kacprzak10b)."]
- step 5: 3D morpho-kinematics and dynamical masses
  - method: GalPak3D MCMC fit of [OIII]/Halpha and CO cubes; Mdyn=Vmax^2 r1/2/G; halo mass from spherical collapse [3.3 Morphological and Kinematical Prope…: "we used the GalPak$^{\rm 3D}$ algorithm (cite: bouche15) which compares directly the data cube with a parametric model"]
  - software: GalPak3D, Sextractor
  - fitting: MCMC [3.3 Morphological and Kinematical Prope…: "The algorithm uses a Markov Chain Monte Carlo (MCMC) approach with a proposed distribution of the parameters"]
  - validation: chi2 minimisation and residual map inspection [3.3 Morphological and Kinematical Prope…: "We assessed the quality of the fit from a $\chi^2$ minimisation as well as the inspection of the residual maps."]
- result: Vmax G2 (CO) = 134 ± ±14 km/s [Table 4: "| **G2** | 2$\pm$1 | 76$\pm$3 | 117$\pm$2 | 134$\pm$14 |"]
- limitation (authors): CO-to-H2 conversion factor is uncertain, so masses are expressed as functions of alpha_CO [3.2 Physical Properties of the Galaxy G…: "Estimates of the corresponding H$_2$ molecular masses however rely on the rather uncertain CO-H$_2$ conversion factor"]
- limitation (authors): Analysis of G0 hampered by the bright quasar; GalPak3D did not converge for several galaxies [3.3 Morphological and Kinematical Prope…: "The analysis of galaxy G0 is hampered by the proximity to the bright quasar (2.3 arcsec)."]
- not stated (card): Self-calibration solution intervals and imaging parameters for the continuum model; Line-free channels for uvcontsub and the fit order; Cleaning threshold, masks and niter in tclean; Duchamp parameters other than the 5-sigma threshold; GalPak3D priors, model choice and initial conditions; Simulation parameters and post-processing details (in a separate paper); ALMA flux scale uncertainty

### 2015ApJ...807..128S: The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Bright-end of the Sub-millimeter Number Counts (2015; high_z_galaxies; large_program_or_survey)
- question: How often are bright SCUBA-2 850 um sources blends of multiple SMGs, and what are the intrinsic bright-end number counts and the origin of the multiplicity?
- step 2: Extract source catalog
  - method: SExtractor on 0.8'' detection maps, >3 sigma peaks, integrated flux in 0.8'' radius aperture, 4% correction, 4 sigma cut [3 Source Extraction: "We search the low–resolution 0.8$''$ “detection” maps and identify all $>$ $3$ $\sigma$ “peaks” in the non–primary–beam corrected maps."]
  - software: SExtractor, CASA imfit
  - parameter: 4 sigma threshold gives 52 SMGs [3 Source Extraction: "Applying a $4$ $\sigma$ cut to our source catalog yields 52 SMGs, within the FWHM primary beam of the 30 ALMA maps."]
  - validation: Inverted maps give contamination of ~2% at 4 sigma [3 Source Extraction: "corresponding to a contamination of 2 % when considering our entire catalog"]
- step 3: Completeness and flux deboosting via simulations
  - method: 2e4 simulated maps with injected sources (power-law index -2, sizes 0-0.5''); spline fit of median output/input flux in 0.25 sigma bins [3.1 Completeness & Reliability: "we create 2 $\times$ 10$^{4}$ simulated ALMA maps."]
  - parameter: completeness 93% at >4 sigma, ~100% at 5.5 sigma [3.1 Completeness & Reliability: "The completeness is 93 % at $>$ 4 $\sigma$, rising to about 100 % at 5.5 $\sigma$"]
  - fitting: spline [3.1 Completeness & Reliability: "We fit a spline to the median of each bin"]
  - validation: slope varied within Karim13 1-sigma changes correction by 10% [3.1 Completeness & Reliability: "changes the correction by $\pm$ 10% at a detection limit of 4 $\sigma$"]
- step 6: Number counts and double power-law fit
  - method: Counts at S870>7.5 mJy with area correction for selection incompleteness; fit double power law to combined ALMA samples [4.2 Number Counts: "we choose to construct the number counts from our ALMA source catalog at $S_{870}$ $>$ 7.5 mJy."]
  - parameter: faint counts converted using ALESS composite SED at z=2.5 (factors 2.4 and 3.1) [4.2 Number Counts: "flux conversion factors are 2.4 $\times$ and 3.1 $\times$, at 1.2 mm and 1.3 mm, respectively"]
  - assumption: Salpeter IMF for SFR; S870-LFIR relation from ALESS [4.2 Number Counts: "or a SFR of $\sim$10$^{3}$ $\mathrel{\rm M_{\odot}\,yr^{-1}}$ (for a Salpeter IMF)"]
  - fitting: Double power law; fitting method not stated [4.2 Number Counts: "we choose to model the counts with a double–power law of the form"]
  - validation: Removing three possibly lensed SMGs changes parameters by less than 1 sigma [4.2 Number Counts: "change by less than their associated 1–$\sigma$ uncertainties"]
- result: SMGs detected at >4 sigma = 52 ± not stated count [abstract: "We detect 52 sub-millimeter galaxies (SMGs) at $>$ 4 $\sigma$ significance in our 30 ALMA maps."]
- result: Double power-law break S0 = 8.4 ± +/-0.6 mJy [4.2 Number Counts: "$S_{0}$ = 8.4$_{-0.6}^{+0.6}$ mJy"]
- result: Double power-law N0 = 390 ± +110/-80 deg^-2 [4.2 Number Counts: "$N_{0}$ = 390$_{-80}^{+110}$ deg$^{-2}$"]
- result: Slopes alpha, beta = alpha=1.9, beta=10.5 ± +/-0.2; +3.0/-3.2 dimensionless [4.2 Number Counts: "$\alpha$ = 1.9$_{-0.2}^{+0.2}$ and $\beta$ = 10.5$_{-3.2}^{+3.0}$"]
- limitation (authors): Small number statistics at both ends of the counts [4.2 Number Counts: "the samples are small and are still dominated by small number statistics"]
- not stated (card): Flux model/setup for J0238+166 beyond 0.59 Jy and CASA calibration script details; clean niter, threshold and mask details beyond sigma levels; Exact parameters of spline flux deboosting fit; Bootstrap procedure details; Fit method (likelihood/sampler) for the double power law; Ma et al. S870-LFIR relation used for luminosity/SFR; SCUBA-2 beam model and 2014 August S2CLS catalog (Geach et al. in …

### 2019MNRAS.483.1624B: An ALMA archival study of the clump mass function in the Large Magellanic Cloud (2019; star_formation, nearby_galaxies; archival_reuse)
- question: What is the dust-derived clump mass function of star forming regions in the LMC, and how does it compare with Milky Way core/clump mass functions?
- step 5: Completeness correction
  - method: Inject 600 beam-sized Gaussian sources per mass bin, rerun ClumpFind, fit logistic function; N_corr=N/f using dor curve [3.4 Completeness corrections: "We inject 600 synthetic sources per mass bin."]
  - software: ClumpFind
  - assumption: Tested only beam-size sources, likely overestimating completeness [3.4 Completeness corrections: "our completeness estimates are likely overestimating the total fraction of clumps recovered for a given mass."]
  - fitting: logistic function [3.4 Completeness corrections: "We fit each completeness curve with a standard logistic function"]
- limitation (authors): CASA <5.0 7m mosaic flux scaling issue: Band 6 overestimated ~8 per cent, Band 3 ~2 per cent, not corrected [footnote 3: "the Band 6 flux densities are overestimated by \sim 8 per cent and Band 3 by \sim 2 per cent."]
- limitation (authors): Completeness tested only for beam-sized sources [3.4 Completeness corrections: "we only tested source recovery for sources that were the same size as the synthesized beam"]
- not stated (card): Line-free channel/spw selections per field for continuum imaging; Exact uv-trim values for Band 3 and taper values per field (partly in table); Auto-masking code is only in a thesis appendix; Band 3 and Band 6 central frequencies used in the combination; Data weights/flux calibrator choices per project; Completeness fit parameters for dor are only in a figure

### 2025ApJS..278...45F: DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey (2025; high_z_galaxies, galaxy_clusters_and_sz; large_program_or_survey)
- question: Establish a joint ALMA and JWST legacy field in Abell 2744 and, through a blind 1.2-mm survey with NIRCam/NIRSpec counterparts, characterize the faint dust continuum sources, HST-/JWST-dark galaxies, a z=6.33 [CII] emitter, z>9 galaxies, a…
- step 2: Blind source extraction with purity estimate
  - method: sextractor positive peaks above 2 sigma; negative-peak analysis on inverted maps; SNR thresholds chosen where positives exceed negatives [3.1 ALMA Source Extraction: "thus adopt the SNR thresholds at 5.0 and 4.4 in the *Wide*-natural and -tapered maps, respectively."]
  - software: SExtractor 2.5.0
  - parameter: Deep thresholds 4.8 (natural), 4.2 (tapered); regions down to 20% relative sensitivity [3.1: "we set the SNR thresholds at 4.8 and 4.2 for the deep-natural and -tapered maps, respectively."]
  - validation: purity p=(Npos-Nneg)/Npos > 0.97 [3.1: "demonstrating the high purity $p>0.97$ of our ALMA sources"]
- step 8: Infrared luminosity function
  - method: IRLF at z=1-5 and z=8-11 following ALCS method; modified blackbody Td=35 K, beta=1.8; Gehrels Poisson errors; no completeness correction [4.5: "We assume the modified black body with the dust temperature of $T_{\rm d}=35$ K and the dust-emissivity index $\beta_{\rm d}=1.8$ (cite: mauerhofer2023)."]
  - assumption: Td=35 K, beta=1.8 [4.5: "dust temperature of $T_{\rm d}=35$ K"]
  - validation: Compared with ALCS DPL, other observations and models [4.5: "Our measurements are consistent with the previous measurements and the model predictions within their scatters."]
- result: Number of continuum sources = 69 (65 Wide + 4 Deep) ± not stated sources [3.1: "we identify 65 ALMA sources from the *Wide* maps and an additional 4 ALMA sources from the deep maps"]
- result: Purity = >0.97 ± not stated dimensionless [3.1: "high purity $p>0.97$"]
- limitation (authors): 1-2 sources may be spurious; no completeness correction for IRLF; z>9 detections marginal [3.1: "This implies that $\sim$1–2 out of the 69 sources might be spurious"]
- not stated (card): Flux calibrator and flux-scale uncertainty; Which channels/spectral windows used for continuum maps; Cube-based line search method and S/N criteria (only prior-based [CII] search described); Details of aperture photometry for the [CII] line optimized extraction; Final Wide/Deep PB-corrected noise maps and mosaic phase centers; Full SED fitting and NIRSpec reduction details (deferred to Wang et al…

### 2018Sci...362.1034D: The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6 (2018; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is the hyper-luminous obscured quasar W2246−0526 (z=4.6) undergoing a multiple merger, with dusty bridges and tidal tails connecting it to companion galaxies?
- step 4: Stellar mass and SFR via SED fitting
  - method: Empirical AGN + galaxy templates (Assef 2010), mass-to-light via ezgal/Galaxev [Materials and Methods: "we follow (10) and derive the mass-to-light ratio of the host using the code ezgal (52) and the Galaxev stellar population SED models (53)"]
  - software: ezgal, Sextractor
  - assumption: Z=0.008, Chabrier IMF, exponentially declining SFHs [Materials and Methods: "with a metallicity Z = 0.008 (≡ 0.4 Z ¤, where Z ¤ is the metallicity of the Sun) and a Chabrier IMF"]
  - fitting: non-negative combination of E, Sbc, Im and AGN templates [Materials and Methods: "An object is modeled as a non-negative combination of an old stellar population (E template), an intermediate stellar population (Sbc template), a young stellar population (Im template) and an AGN."]
  - validation: Tested contamination and host reddening [Materials and Methods: "the change in M ★ would be well within the error of a factor of two quoted below"]
- limitation (authors): U1 may be at a different redshift; stellar mass and SFR uncertain by factor of 2 [Materials and Methods: "both with an uncertainty of a factor of 2"]
- not stated (card): Line-free channels / how continuum cube was built from SPWs and which channels were discarded; Flux calibration details (pipeline vs manual) and flux scale uncertainty; Mask for extended emission/companions during cleaning; Aperture photometry method for companions and tail; Image size and cell size; Self-calibration use

### 2020ApJ...895...84Y: Super-resolution Imaging of the Protoplanetary Disk HD 142527 Using Sparse Modeling (2020; protoplanetary_disks, instrumentation; archival_reuse)
- question: Can sparse modeling (l1+TSV) imaging applied to ALMA data reproduce super-resolution structure (finer than the beam) of the HD 142527 disk with higher fidelity than MS-CLEAN?
- step 4: Fidelity versus resolution (NRMSE)
  - method: Convolve images with beams of fraction R of Data 1 nominal beam; compute NRMSE in image and gradient (Prewitt) domains against Data 2 MS-CLEAN reference; optimal resolution is minimum, worse of two domains [3.2 Fidelity at Multi-resolution: "The beam size providing the minimum NRMSE may be considered as an optimal resolution"]
  - assumption: Data 2 MS-CLEAN at nominal resolution is trusted reference [3.2 Fidelity at Multi-resolution: "The Data 2 MS-CLEAN at its nominal resolution is therefore the best choice as the reference image."]
  - validation: Ideal NRMSE curve from convolved reference image [3.2 Fidelity at Multi-resolution: "The solid green line shows the ideal NRMSE curves between the non-convolved and the convolved reference images"]
- result: Optimal resolution Data 1 SpM, image domain = 23 x 16 (41%) ± not stated mas [Table 1: "23 $\times$ 16 (41 $\%$)"]
- result: Optimal resolution Data 1 MS-CLEAN, gradient domain = 34 x 24 (60%) ± not stated mas [Table 1: "34 $\times$ 24 (60 $\%$)"]
- result: Data 1 SpM NRMSE plateau at R<=41% = 5-10% image domain, 10-15% gradient domain ± not stated percent [3.2 Fidelity at Multi-resolution: "with typical ranges of $5-10~\%$ in the image domain and $10-15~\%$ in the gradient domain"]
- limitation (authors): SpM images have larger asymmetric residuals due to self-calibration with MS-CLEAN; degree of super-resolution for Data 2 not established [5 Conclusion: "SpM images have more asymmetric and larger residuals, while MS-CLEAN images have nearly symmetric residuals distributions."]
- not stated (card): SpM code/implementation used (not named or released); Selected optimal (Lambda_l, Lambda_t) per spectral window; Clean masks, thresholds, iteration counts, cell/image size for MS-CLEAN; Number of self-cal iterations and exact steps; Calibrator for Data 1 flux scale; Frequency ordering/weighting when averaging four SPW images; Reference position of the star for radial profiles

### 2025ApJ...992..211N: Revisiting the Supermassive Black Hole Mass of NGC 7052 Using High Spatial Resolution Molecular Gas Observed with ALMA (2025; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: What is the SMBH mass and stellar I-band M/L of NGC 7052 from 12CO(2-1) kinematics at 0.3 arcsec resolution, with an improved stellar plus molecular gas mass model?
- step 4: Stellar mass model from HST
  - method: PSF (TinyTim) deconvolved, masked MGE fit of WFC F814W sky-subtracted image [3.2 Our improved stellar-mass model: "we first decomposed the PSF into an MGE, which was then used as input for the subsequent MGE fit of the F814W masked and sky-subtracted image"]
  - software: MgeFit, TinyTim, Drizzlepac/AstroDrizzle, SExtractor
  - assumption: constant M/L, no dark matter in the center [3.2 Our improved stellar-mass model: "by assuming a constant *M/L* (taken from its best-fit constrained in Section [4.4](#sec:results)) and ignoring the contribution of dark matter in the central region"]
  - fitting: MGE fit [Our improved stellar-mass model: "we first decomposed the PSF into an MGE, which was then used as input for the subsequent MGE fit of the F814W masked and sky-subtracted image"]
  - validation: compared with Smith21 MGE [3.2 Our improved stellar-mass model: "For a sanity check, we compared our derived stellar mass model with the one from (cite: Smith21)"]
- limitation (authors): Distance uncertainty (69.3 vs 46.4 Mpc) gives ~30% systematic in MBH, dominant error [4.5.1 Distances: "This discrepancy results in a systematic uncertainty of $\sim$30% in $M_{\rm BH}$"]
- not stated (card): Line-free channel ranges for uvcontsub; Self-calibration solution intervals and number of rounds; Cleaning niter/threshold details and exact tclean parameters; Rest-frame velocity convention details and exact cube channel start; Exact MGE fit settings and masks; SkySampler/KinMS settings beyond those given (e.g. initial guesses); The continuum flux in text (29.1 mJy) differs from Table 1 (24.9 mJ…

### 2020A&A...635A...2S: Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA (2020; star_formation, milky_way_ism; observational_alma_primary)
- question: What are the core mass function, spatial distribution of cores and mass segregation in the star-forming clusters of NGC 6334, and how do they relate to cluster evolutionary stage and fragmentation physics?
- step 2: Extract compact source catalogue
  - method: SExtractor via sewpy with 6 sigma detection and 24 sigma deblending thresholds, min 5 pixels; visual removal of artifacts [3.1 Continuum source identification: "we used a detection threshold of $6\sigma$, where $\sigma$ is the rms noise level, and a deblending threshold of $24\sigma$."]
  - software: SExtractor, sewpy
  - parameter: 185 automatic detections, 142 after manual removal [3.1 Continuum source identification: "A total of 185 sources were automatically identified by `SExtractor`."]
  - validation: Visual inspection to remove sources in noisy regions and clean artifacts [3.1 Continuum source identification: "After visual inspection, we manually removed those located in regions of the map with a higher rms noise level"]
- step 5: CMF slope, completeness and bias tests
  - method: Power-law fit of dN/dlnM above 2 Msun; Monte Carlo completeness; random-temperature test; Jeans-fragmentation resolution test [5.1 Core mass function: "We fitted a power-law function given by $dN/d\ln(M) \propto M^{\alpha}$ to the CMFs for the range of masses above the completenes level."]
  - parameter: Completeness 2 Msun; temperature test 20-100 K, 100000 trials; epsilon0 = 0.4, p = 1.3 [5.1.2 Resolution bias in the determinat…: "We find that $\epsilon_0=0.4$ and $p=1.3$ reproduce a slope of $-1.35$ in the CMF"]
  - assumption: IMF slope -1.35 (Salpeter/Kroupa) for comparison [5.1 Core mass function: "The measured slope for the high-mass end of CMF in NGC 6334 clusters is not consistent with the $-1.35$ value of the IMF"]
  - fitting: Power-law fit; no sampler stated [5.1 Core mass function: "We fitted a power-law function given by $dN/d\ln(M) \propto M^{\alpha}$ to the CMFs for the range of masses above the completenes level."]
  - validation: Predicted fragments compared to higher-resolution observations (source 43: 2, source 44: 9 vs 7) [5.1.2 Resolution bias in the determinat…: "For source 44 we estimate 9 fragments, in agreement with the 7 components that have been resolved with a resolution of $0.2\ensuremath{''}$."]
- result: Number of compact sources = 142 ± not stated sources [3.1 Continuum source identification: "The final catalogue of ALMA continuum sources contains 142 objects."]
- result: CMF slope alpha, whole sample = -1.1 ± 0.02 dimensionless [5.1 Core mass function: "We obtain a value of $\alpha=-1.1\pm0.02$ for the whole sample"]
- result: Mass completeness limit = 2 ± not stated Msun [5.1 Core mass function: "In the following, we consider our mass completeness limit to be 2 $M_\odot$."]
- result: CMF slope range under random temperatures = -0.7 to -1.46 ± std 0.10 dimensionless [5.1.1 Temperature bias in the determina…: "We find the slope $\alpha$ to be in the range $-0.7$–$-1.46$, with a standard deviation of 0.10."]
- limitation (authors): Temperatures assumed rather than measured; unresolved multiplicity biases CMF [5.1 Core mass function: "the measured slope can be biased due to the uncertainty in temperature determination and the unresolved multiplicity in the massive cores."]
- limitation (authors): Low number statistics limit Q-parameter conclusions [4.2 Spatial structure of the clusters i…: "the total number of sources in that cluster (10) limits the conclusions that can be derived from this analysis."]
- not stated (card): Line-free channel ranges used for continuum; tclean multiscale scales, image size, masking and threshold; Self-calibration solution intervals; SExtractor parameters beyond thresholds (filter, mesh size); Hyperparameters of the seven scikit-learn clustering algorithms; How the SExtractor flux was corrected for ACA/combined images and which image (super-resolution vs combined) was used for the cata…

### 2020ApJS..251...14H: CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone (2020; milky_way_ism, star_formation; multi_facility_alma_minor)
- question: Which compact sources (<10'', ~0.4 pc) exist in the 1.3 mm SMA CMZoom continuum maps of the Central Molecular Zone, what are their properties and completeness, and what do they imply for CMZ star formation potential?
- step 2: Run dendrogram and prune leaves by local noise
  - method: Dendrogram on continuum map in MJy/sr, then keep leaves with peak >6 sigma (robust) or >4 sigma (high-completeness) and mean >2 sigma of local RMS [3.1 Pruned Dendrogram Algorithm: "the former prioritizing only the most robust leaves with a peak flux at least 6$\sigma$ above the local RMS estimate and the latter prioritizing a higher catalog completeness, which includes leaves with a peak flux at least 4$\sigma$ above the local RMS estimate."]
  - software: astrodendro
  - parameter: min value = 3x global noise (3 MJy/sr); min pixels ~ half average beam; min significance = global low noise [3.1 Pruned Dendrogram Algorithm: "The minimum pixel value is chosen to be a factor of three greater than this global noise estimate."]
  - validation: Parameter study of delta and kernel in Appendix [8 Catalog Parameter Studies: "we find that the mass and radius distribution of leaf properties in the catalog is well preserved"]
- step 3: Completeness and false-positive from simulated observations
  - method: Inject 10 point sources, simobserve, tclean, make RMS map, dendrogram and prune, count recovered sources [3.2 Source Recovery and Simulated Obser…: "A given point-source is considered to be recovered if its coordinates are located anywhere within a pruned leaf."]
  - software: CASA simobserve, CASA tclean, AATM
  - parameter: masses from flux assuming Td = 20 K [3.2 Source Recovery and Simulated Obser…: "we assume a constant dust temperature of 20K"]
  - assumption: Point-source-like emission model [3.2 Source Recovery and Simulated Obser…: "can be modeled by point-source-like emission for the purposes of this simplistic completeness estimate."]
  - validation: Completeness resilient to atmospheric variation [3.2 Source Recovery and Simulated Obser…: "The completeness results for our catalogs constructed from the simulated observations is resilient to variations typical in atmospheric conditions"]
- result: Robust catalog leaves = 285 ± not stated leaves [4.1 Leaf Distribution in l-b Space: "The robust catalog contains 285 leaves"]
- result: High-completeness catalog leaves = 816 ± not stated leaves [4.5 High-Completeness Catalog: "The change produces a catalog of 816 leaves as compared to the robust catalog with its 285 leaves."]
- result: 95% completeness mass, robust = 80 ± not stated Msun [3.2 Source Recovery and Simulated Obser…: "point-sources above 80 solar masses, under the typical observational conditions for the *CMZoom* survey, are detected with more than 95% completeness"]
- result: 95% completeness mass, high-completeness = ~50 ± not stated Msun [4.5 High-Completeness Catalog: "with a 95% completeness of $\sim 50$ M$_\odot$ (assuming T$_d$=20K)"]
- limitation (authors): Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2 [3.2 Source Recovery and Simulated Obser…: "These mass completeness estimates account only for the observational biases in observing point-source-like emission"]
- not stated (card): Exact dendrogram parameter values in the appendix-referenced setup (min_value, min_npix, min_delta numeric values beyond 3 MJy/sr scaling); Access/processing of CMZoom SMA maps from Dataverse versus Paper I imaging details; Simulated observation antenna configuration, integration time and weather settings; Herschel temperature map not yet published (in prep.); Exact point-source flux values and m…

### 2016A&A...593A..44L: The 492 GHz emission of Sgr A* constrained by ALMA (2016; milky_way_ism, agn_and_quasars; observational_alma_primary)
- question: Characterize the polarized continuum emission of Sgr A* at ~492 GHz (intensity, polarization position angle, polarization percentage) and compare with lower-frequency observations.
- step 4: Gauge spurious polarization using CI line and Titan
  - method: Miriad imdiff to find XX/YY multiplicative factor in CI images over a box region, per scan and per 2.5 km/s channel; compare with continuum ratio and absorption [3.2 Spectral line data: "We used the Miriad task `imdiff` to systematically estimate the multiplicative factor that minimizes the difference between the XX and YY synthesized images of CI"]
  - software: Miriad imdiff
  - parameter: 2.5 km/s velocity channels; CI 12m data tapered at 1.5" [3.2 Spectral line data: "for every 2.5 km s$^{-1}$ wide velocity channels"]
  - assumption: Foreground CI absorber has negligible Tex and identical tau for X and Y [3.2 Spectral line data: "it is safe to assume that $T_{ex}$ is negligible, and the gas optical depth $\tau$ is identical for the orthogonal linear polarizations X and Y."]
  - fitting: Maximum likelihood factor minimizing XX-YY image difference [Results, Spectral line data: "estimate the multiplicative factor that minimizes the difference between the XX and YY synthesized images of CI in a maximum likelihood sense"]
  - validation: Residuals consistent with thermal noise; CI emission XX/YY ~1 away from absorption [3.2 Spectral line data: "we found that $R(\nu, t)$, and its time integration, are consistent with thermal noise."]
- result: Peak CI absorption XX/YY ratio near vlsr~20 km/s = ~1.3 ± not stated dimensionless [3.2 Spectral line data: "The local peak value of $F_{XX}^{CI}(\nu)$ / $F_{YY}^{CI}(\nu)$ is $\sim$1.3 (or 0.11 in logarithm)."]
- result: Std of CI XX/YY away from 20 km/s = 0.043 ± not stated dimensionless [3.2 Spectral line data: "is 0.043."]
- result: Titan XX/YY continuum difference = ~3 ± not stated % [3.2 Spectral line data: "The continuum emission from Titan shows a $\sim$3% intensity difference between the XX and the YY correlations."]
- limitation (authors): Absolute flux uncertain (~20%) because Titan scans were largely flagged; single epoch only. [2 Observations and Data Reduction: "The scans on Titan were largely flagged due to interference from spectral lines."]
- not stated (card): Line-free channel ranges used for uvcontsub; Polynomial order of uvcontsub fit; Flagging details; Model flux/shape used in demos for self-calibration; How the bootstrap errors in the XX/YY fits were computed; Image size and cell size; Titan flux model used for flux scaling

### 2018ApJ...866...48U: A Cool Core Disturbed: Observational Evidence for the Coexistence of Subsonic Sloshing Gas and Stripped Shock-heated Gas around the Core of RX J1347.5-1145 (2018; galaxy_clusters_and_sz; multi_facility_alma_minor)
- question: Does the cool core of RX J1347.5-1145 slosh sub-sonically, and is the southeast substructure shock-heated stripped gas from an infalling subcluster, from joint Chandra, ALMA SZE and HST lensing data?
- step 5: Strong-lensing mass model and DM cross-section limit
  - method: GLAFIC parametrized NFW halos, member galaxies, multipole perturbations constrained by 21 images; MCMC errors; surface density within 25 kpc of subcluster peak gives sigma/m limit with tau<1 [4.1 Central mass distribution: "We used the `GLAFIC` software package (cite: Oguri10) for our mass modeling."]
  - software: GLAFIC, SExtractor
  - parameter: positional error 0.5'' for all images [4.1 Central mass distribution: "We assumed a positional error of $0.5\ensuremath{''}$ for all the multiple images"]
  - fitting: MCMC; Gaussian priors on photometric redshifts of four image sets [4.1 Central mass distribution: "we included Gaussian priors based on their photometric redshifts"]
  - validation: Three-halo model tested and rejected [4.1 Central mass distribution: "We therefore neglect the third dark halo component in the rest of this paper."]
- result: Subcluster virial mass = 2.8e14 ± +2.4/-1.1 h^-1 Msun [4.1 Central mass distribution: "$2.8^{+2.4}_{-1.1} \times 10^{14}$ $h^{-1}$$M_\odot$ for the subcluster"]
- result: DM self-interaction cross section upper limit (95% CL) = 3.7 ± not stated h^-1 cm^2 g^-1 [5.3 Self-interaction cross section for …: "$\sigma_{\rm DM} / m < 3.7\,h^{-1}$ cm$^2$ g$^{-1}$"]
- limitation (authors): Mass and concentration strongly correlated so mass systematic uncertainty may be large [4.1 Central mass distribution: "The obtained mass and concentration parameter are correlated strongly, therefore the systematic uncertainty of the mass estimates might be large."]
- not stated (card): ALMA imaging parameters (weighting, deconvolver, cell size, masking, uv range) are only in Kitayama et al. 2016; ALMA calibration details and flux calibrator; Conversion of ALMA SZE to pressure/Compton y and residual SZE noise levels; Exact regions and pixel selection for the equation-of-state measurement; GLAFIC priors and MCMC settings

### 2018ApJ...858...85P: Forecasting the Contribution of Polarized Extragalactic Radio Sources in CMB Observations (2018; cosmology, agn_and_quasars; multi_facility_alma_minor)
- question: How does the fractional polarization of extragalactic radio sources depend on frequency (1.4-217 GHz), and how much do polarized ERS contaminate CMB B-mode observations of current and forthcoming experiments?
- step 3: forecast ERS contamination for CMB experiments
  - method: Compute number counts and Poissonian power spectra with PS4C, compare with CAMB CMB and rescaled Galactic foregrounds [Forecasts for forthcoming CMB ground-ba…: "we assume their distribution in the sky to be Poissonian"]
  - software: PS4C, CAMB
  - parameter: r=0.05, Planck best fit cosmology [Forecasts for forthcoming CMB ground-ba…: "assuming the *Planck* best fit cosmological parameters (cite: 2016A&A...594A..13P) and a tensor to scalar ratio $r=0.05$"]
  - assumption: Polarization angle uniformly distributed; C_B ≈ C_E ≈ C_U ≈ C_Q [Forecasts for forthcoming CMB ground-ba…: "we can approximate $C_{\ell} ^B\simeq C_{\ell} ^E\simeq C_{\ell} ^U\simeq C_{\ell} ^Q$"]
  - validation: Compared PS4C counts with DZ16 estimates [PS4C with future space missions: "Comparison of surface densities of polarized ERSs brighter than $P_{4 \sigma}$ estimated by (cite: 2016arXiv160907263D)(DZ16) and by PS4C."]
- result: Max polarized sources detected at 3 sigma by CMB-S3 LA (30 GHz) = 2329 ± not stated sources [PS4C with current and forthcoming CMB g…: "the maximum number of polarized sources detected above a $3\sigma$ level and using the large aperture telescope is $2329$"]
- limitation (authors): Planck detections may be biased upward toward high fractional polarization; forecasts limited to ≤150 GHz, excluding dusty galaxies [The Second Planck Catalogue of Compact …: "the statistics of ERS polarization can be biased upward"]
- not stated (card): ALMA 95 GHz data processing, calibration, project code and polarization measurements (deferred to Galluzzi et al. 2018); Number of bootstrap resamplings N_resamp and exact bin choices; Fit method for log-normal and linear fits

### 2020ApJ...891...64F: Truth or Delusion? A Possible Gravitational Lensing Interpretation of the Ultraluminous Quasar SDSS J010013.02+280225.8 at z = 6.30 (2020; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is the resolved quadruple ALMA 1-mm continuum structure of the z=6.30 quasar J0100+2802 due to strong gravitational lensing or to multiple star-forming regions, and how would lensing change its BH mass?
- step 4: Test HST single-component morphology with mock PSF injection
  - method: Measure HST PSF from stars; inject three PSFs in 2:1:1 ratio at varying separation l; compare FWHM [3.2 Comparison with HST: "Finally, we measure the FWHM values for the single-like component in the mock HST map as a function of $l$."]
  - software: SExtractor
  - validation: Observed FWHM 0.113'' matches l=0.04'' [3.2 Comparison with HST: "We also find that the FWHM of J0100+2802 corresponds to the simulation results with $l=0.''04$."]
- result: HST emission FWHM = 0.113 ± not stated arcsec [3.2 Comparison with HST: "the FWHM for J0100+2802 in the observed HST map that is estimated to be $0.''113$"]
- result: HST PSF FWHM = 0.103 ± ±0.003 arcsec [3.2 Comparison with HST: "The FWHM of the PSF is estimated to be $0.''103$ $\pm$ $0.''003$"]
- limitation (authors): Lens model poorly constrained; magnification uncertain by a factor of a few [4 Discussion: "our estimate of the total magnification factor should be uncertain by a factor of a few or so"]
- not stated (card): Spectral window line-free channel selection; Cell size and image size; Exact tclean parameters (niter, gain, mask settings); glafic fitting setup details and best-fit SIE parameters (other than Einstein radius and e); How the 0.8'' aperture flux and peak positions were measured; Details of simobserve configuration and noise

### 2017A&A...604A.115V: The correct estimate of the probability of false detection of the matched filter in weak-signal detection problems . II. Further results with application to a … (2017; other, star_formation; archival_reuse)
- question: How to quantify the reliability of individual weak point-source detections in matched-filtered maps via a specific probability of false alarm (SPFA), and whether it reveals faint sources in ALMA and ATCA maps
- step 4: Compute SPFA and Poisson-binomial false detection counts
  - method: alpha = 1-[Psi(z_max)]^Np per peak, removing confirmed detections; Poisson-binomial for N_FD [3 Specific probability of false alarm: "& = 1-\left[ \Psi(z_{\rm max}) \right]^{N_p}."]
  - validation: Tested on simulated map with known sources [5 A numerical experiment: "This result is in good agreement with the true $N_{\rm FD} =6$."]
- result: SPFA of sources 1a, 2a in M1 = 8.8e-2, 2.0e-2 ± not stated dimensionless [6 Application to real ALMA maps: "in M1 the SPFA is $8.8 \times 10^{-2}$ and $2.0 \times 10^{-2}$ for the sources 1a and 2a"]
- result: SPFA of sources 1b-4b in M2 = 5.7e-1, 5.0e-1, 1.4e-1, 1.3e-1 ± not stated dimensionless [6 Application to real ALMA maps: "whereas in M2 it is $5.7 \times 10^{-1}$, $5.0 \times 10^{-1}$, $1.4 \times 10^{-1}$, and $1.3 \times 10^{-1}$ for the sources 1b-4b"]
- result: SPFA of sources 1c-3c in M3 = 3.2e-1, 2.7e-1, 4.0e-3 ± not stated dimensionless [6 Application to real ALMA maps: "The SPFA is equal to $3.2 \times 10^{-1}$, $2.7 \times 10^{-1}$ and $4.0 \times 10^{-3}$ for the detections 1c-3c, respectively."]
- limitation (authors): Flux measurements of 1b+3b are highly uncertain because of source shape [6 Application to real ALMA maps: "The fluxes measurement are therefore subject to a large uncertainty that depends on the chosen source shape."]
- not stated (card): Line-free channel selection and spectral setup; Number of iterations, threshold, and mask for clean; Pixel (cell) size of the maps; Calibration details and the CASA pipeline/manual choice; Source masking regions and how the Gaussian filtering scale was set; Code for the SPFA computation (not released); Flux-scale uncertainty

### 2015ApJ...811L..19W: Gemini Planet Imager Observations of the AU Microscopii Debris Disk: Asymmetries within One Arcsecond (2015; debris_disks; multi_facility_alma_minor)
- question: What is the morphology of the AU Mic debris disk within 1 arcsec, and are there planets or compact clumps, as seen with GPI?
- step 3: Planet sensitivity
  - method: Contrast curve via Mawet et al. 2014, planet injection, Monte-Carlo completeness with COND models [Sensitivity to Planets: "we ran a Monte-Carlo analysis as described by (cite: nielsen) to determine the completeness of our data."]
  - assumption: COND evolutionary models; 23 Myr age [Sensitivity to Planets: "assuming COND models (cite: baraffe03)"]
- result: K1 candidate separation = 544 ± 4 mas [Sensitivity to Planets: "at a separation of 544$\pm$4 mas, a PA of $130.2\ensuremath{^\circ}$$\pm$$0.9\ensuremath{^\circ}$"]
- result: K1 candidate contrast = 1.1e-5 ± 0.3e-5 dimensionless [Sensitivity to Planets: "a *K1* contrast of 1.1$\pm$0.3 $\times 10^{-5}$"]
- limitation (authors): Disk brightness vs separation unreliable owing to residual PSF features; sliver at only 3.1 sigma and may arise from KLIP self-subtraction [Analysis of the Debris Disk: "We cannot rule out that the apparent morphology is influenced by KLIP self-subtraction."]
- not stated (card): ALMA data were not reprocessed; the reduced ALMA images came from MacGregor via private communication; GPI data availability not given

### 2024ApJ...967...27R: Exploring the Mpc Environment of the Quasar ULAS J1342+0928 at z = 7.54 (2024; agn_and_quasars, high_z_galaxies; multi_facility_alma_minor)
- question: Is the z = 7.54 quasar ULAS J1342+0928 surrounded by an overdensity of Lyman-break galaxies in its ~1 pMpc^2 environment?
- step 4: Completeness test vs GOODS
  - method: Reselect with only three HST filters in GOODS catalog and compare to z=7-8 sources [6.1: "Hence, we recover in total only 31/125, i.e. $\sim25\%$ of the sources."]
  - software: EAZY
- result: Recovered fraction in GOODS test = 31/125 (~25%) ± not stated dimensionless [6.1: "Hence, we recover in total only 31/125, i.e. $\sim25\%$ of the sources."]
- limitation (authors): Low number statistics and low completeness [6.2: "Note that this measurement is limited by low number statistics."]
- not stated (card): ALMA data reduction details (the ALMA data are not reprocessed here); QSO-LBG clustering calculation details and excess formula inputs

### 2020A&A...636A...5R: SYMBA: An end-to-end VLBI synthetic data generation pipeline. Simulating Event Horizon Telescope observations of M 87 (2020; instrumentation, agn_and_quasars; technical_calibration_or_instrument)
- question: How can realistic synthetic mm-VLBI (EHT) data with atmospheric, instrumental and calibration effects be generated and calibrated, and how well can GRMHD models of M87 be recovered with current and future EHT arrays?
- step 3: Reconstruct images and quantify fidelity
  - method: RML imaging and normalized cross-correlation with the input model convolved with varying beams [7.2 Crescent and GRMHD image reconstruc…: "We compute the normalized cross-correlation (cite: eht-paperIV) between the reconstructed image $X$ and the input model image $Y$"]
  - software: eht-imaging
- limitation (authors): Only one GRMHD snapshot and two electron models used; results may not generalize. [8.1 κ-jet versus thermal-jet model: "We note that we have only used one GRMHD snapshot with two specific electron temperature models."]
- not stated (card): Exact eht-imaging regularizer weights and iteration schedule; MeqSilhouette and rPICARD version numbers; Random seeds for noise and pointing draws; Exact GRMHD model image files

### 2018A&A...620A.152F: GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies (2018; high_z_galaxies; observational_alma_primary)
- question: Which galaxies does a blind, contiguous 69 arcmin2 ALMA 1.1 mm survey of GOODS-South detect, and what are their counterparts (including HST-dark galaxies), redshifts, masses, AGN fraction and number counts?
- step 3: Detect sources and set thresholds
  - method: BLOBCAT flood fill on SNR map of 0.60 arcsec mosaic; scan sigma_p 4-6 and sigma_f 2.5-4; require purity (Np-Nn)/Np >= 0.8 from inverted map [3 Source Detection: "This leads to $\sigma_p$ = 4.8 $\sigma$ when fixing the value of $\sigma_f$ = 2.7 $\sigma$"]
  - software: BLOBCAT
  - parameter: sigma_p = 4.8, sigma_f = 2.7 [3 Source Detection: "Hence we decided to set $\sigma_p$ = 4.8 $\sigma$ and $\sigma_f$ = 2.7 $\sigma$ to produce our catalogue of ALMA detections."]
  - validation: Positive vs negative detections; HST counterpart fraction as a check [3 Source Detection: "The difference between positive and negative detections for each pair of ($\sigma_p$, $\sigma_f$) values provides the expected number of real sources."]
- step 4: Measure fluxes and sizes
  - method: Blobcat peak, Galfit PSF fitting, PyBDSM, uvmodelfit; stacking; point-source assumption with corrections for AGS17 and AGS18 [4.1 Creation of the catalogue: "we compared different flux extraction methods and softwares: `PyBDSM` (cite: Mohan2015); `Galfit` (cite: Peng2010); `Blobcat` (cite: Hales2012)."]
  - software: BLOBCAT, Galfit, PyBDSM, CASA uvmodelfit
  - assumption: sources point-like in 0.60 arcsec mosaic [4.1 Creation of the catalogue: "we assume that the galaxies detected in the 0$''$60-mosaic are point-like."]
  - fitting: Galfit PSF fits in 5x5 arcsec box; Sersic index fixed to 1 in comparison fits [4.5 Galaxy sizes: "the Sersic index was frozen to n = 1"]
  - validation: Consistency of methods; residuals below 3 sigma for 21/23 [4.5 Galaxy sizes: "The residuals of 21/23 detections do not have a peak greater than 3 $\sigma$ in a radius of 1$''$ around the source."]
- step 6: Completeness, flux boosting, effective area, number counts
  - method: Inject 300 artificial sources per run, 100 runs per flux 0.5-2.4 mJy, sizes FWHM 0.2-0.9 arcsec; deboost; correct purity, completeness and effective area; fit DPL and Schechter functions [5.1 Completeness: "We inject 300 artificial sources of a given flux, and repeat this procedure 100 times for each flux density."]
  - assumption: ALMA sizes 1.4 times smaller than HST H-band sizes [5.1 Completeness: "We took the hypothesis that ALMA sizes are 1.4 times smaller than the size measured in HST $H$-band"]
  - fitting: least squares with Trust Region Reflective algorithm [5.4 Cumulative and differential number …: "We use a least squares method with the Trust Region Reflective algorithm for these two fitted-functions."]
  - validation: Comparison with SIDES and literature counts [5.4 Cumulative and differential number …: "The (cite: Bethermin2017) prediction is in good agreement with the number counts derived in this study, for the two bins with the lowest fluxes."]
- result: Number of main-catalogue detections = 20 ± not stated sources [4.1 Creation of the catalogue: "we obtain a total of 20 detections down to a flux density limit of $S_{1.1mm}$ $\approx$ 880 $\mu$Jy"]
- result: Expected spurious sources = 4 ± ±2 sources [4.1 Creation of the catalogue: "suggests the presence of 4$\pm$2"]
- result: Completeness at 1.2 mJy for point sources = 94 ± ±1% percent [5.1 Completeness: "at 1.2 mJy, our sample is 94$\pm$1% complete for point sources"]
- result: EBL fraction resolved at 0.8 mJy = 13.5 ± +9.0/-8.6 percent [5.5 Contribution to the cosmic infrared…: "We have resolved only 13.5$_{-8.6}^{+9.0}$% of the EBL into individual galaxies at 0.8 mJy."]
- result: Median compact size from uvmodelfit = 0.18 ± not stated arcsec FWHM [4.5 Galaxy sizes: "The median size of our sample of 20 galaxies is 0$''$18"]
- limitation (authors): Cosmic variance not included in count errors; the HST-dark status of three sources needs further investigation [5.4 Cumulative and differential number …: "Cosmic variance was not taken into account in the calculation of the errors."]
- not stated (card): CASA version and pipeline version; Exact CLEAN/tclean parameters (cell, image size, uv-taper values, weighting); Primary-beam cutoff and sub-mosaic combination details; Exact BLOBCAT settings beyond sigma_p and sigma_f; Flux scale uncertainty and self-calibration; Details of FAST/EAZY fits (templates, priors); Astrometric offset table for each galaxy

### 2020ApJ...889..137M: Balmer Break Galaxy Candidates at z ∼ 6: A Potential View on the Star Formation Activity at z ≳ 14 (2020; high_z_galaxies; multi_facility_alma_minor)
- question: Are there Balmer break galaxies at z~6 in COSMOS, and what do they imply for the stellar mass density and the star-formation rate density of their progenitors at z>14?
- step 1: Select BBG candidates by color
  - method: SExtractor on [3.6] image, K-[3.6] > 1.75 and K-[3.6] > 2.4([3.6]-[4.5])+1.05, then remove detections in X-ray, FIR, radio and optical [3.4 Expected colors: "K - [3.6] > 1.75, \label{eq:BBGcriteria1}\\ K - [3.6] > 2.4 ([3.6] - [4.5]) + 1.05."]
  - software: SExtractor, IRAF
  - parameter: Effective area 0.41 deg2; 23 color-selected, 6 remaining after multi-band selection [4.1 NIR Color Selection: "We identified 23 objects satisfying the BBG color criteria, which are referred to as the color-selected sample in the following sections."]
  - validation: Completeness via artificial sources [4.1 NIR Color Selection: "We estimated the completeness of our source extraction by detecting artificial sources randomly embedded in the [3.6]-band image."]
- step 4: Stellar mass density and progenitor SFRD
  - method: n_BBG corrected for completeness; SMD from best-fit masses; SFRD = <SFR> x n_prog using 10^6 combinations of MC-best models [7.3 Cosmic star-formation activity: "We made $10^6$ combinations of three MC-best BBG models from the randomly selected 100 MC realizations for each object"]
  - parameter: T_BBG = T_age - T_SF - 0.2 Gyr, T_SF = 2 tau_SFH [7.3 Cosmic star-formation activity: "Assuming the BBG observable time duration as $T_{\rm BBG} = T_{\rm age} - T_{\rm SF} - 0.2\,{\rm Gyr}$ with $T_{\rm SF} = 2 \times \tau_{\rm SFH}$"]
  - assumption: All three candidates are real BBGs at 4.8<=z<=7.8 [7.2 Stellar mass density: "Assuming all of the three BBG candidates without ALMA detections to be passive galaxies at $4.8 \leq z \leq 7.8$"]
  - validation: Cross-check with rho_* / <T_BBG> [7.3 Cosmic star-formation activity: "$\rho_{\rm SFR} \approx (2.4 \times 10^4\,M_{\odot}\,{\rm Mpc}^{-3}) / (0.56\,{\rm Gyr}) = 4.3 \times 10^{-5}\,M_{\odot}\,{\rm yr}^{-1}\,{\rm Mpc}^{-3}$"]
- result: Number density of BBGs = 4.9e-7 ± +4.8/-2.7 e-7 Mpc^-3 comoving [7.2 Stellar mass density: "we estimate the number density of the BBGs as $n_{\rm BBG} = (4.9_{-2.7}^{+4.8}) \times 10^{-7}$ Mpc$^{-3}$ (comoving)"]
- result: Stellar mass density at z~6 = 2.4e4 ± +2.3/-1.3 e4 Msun Mpc^-3 [7.2 Stellar mass density: "we obtained the SMD of $(2.4_{-1.3}^{+2.3}) \times 10^4\,M_\odot$ Mpc$^{-3}$"]
- result: Progenitor SFRD at z>~14 (99.7% range) = 2.4e-5 to 1.2e-4 ± 3 sigma range Msun yr^-1 Mpc^-3 [7.3 Cosmic star-formation activity: "$2.4 \times 10^{-5} \lesssim {\rm SFRD} / M_\odot\,{\rm yr}^{-1}\,{\rm Mpc}^{-3} \lesssim 1.2 \times 10^{-4}$ at $z \ensuremath{\gtrsim} 14$"]
- limitation (authors): SFRD is a lower limit; contamination by AGN not excluded; spectroscopic confirmation needed [8 Conclusion: "direct evidence of the BBG, i.e., spectroscopic confirmation of the Balmer break by coming *James Webb Space Telescope* ($JWST$; (cite: Gardner+06)), is needed."]
- not stated (card): Archive flux-calibrator names/flux values for ALMA were not given per execution; Aperture and imfit starting parameters for the ALMA upper limits (e.g., 3 sigma vs 1 sigma) not fully specified; Image size and cell size not given; The detailed SED template grids steps, MC seeds, and PANHIT version not given; Completeness and effective volume computation details for SMD not fully given

### 2017ApJ...841...43E: ALMA CO Clouds and Young Star Complexes in the Interacting Galaxies IC 2163 and NGC 2207 (2017; nearby_galaxies, star_formation; observational_alma_primary)
- question: What are the mass distributions of CO clouds in IC 2163 and NGC 2207, and how do clouds relate to young star complexes seen with HST?
- step 1: identify CO clouds
  - method: Visual identification in DS9 on masked CO surface density image; cuts on pixel intensity, channel count and resolution; SExtractor as comparison [2.2 Identification of CO Clouds: "we identified 327 discrete CO clouds by eye in the resulting surface density image in DS9"]
  - software: DS9, SExtractor
  - parameter: 2 or more pixels above I(CO)=200 Jy/beam m/s; at least 2 channels above 2 sigma [2.2 Identification of CO Clouds: "clouds that contained 2 or more pixels (2 px = 1.0” = 170 pc at the assumed distance of 35 Mpc) above a CO intensity $I(CO)= 200$ Jy beam$^{-1}$ m s$^{-1}$"]
  - validation: SExtractor run gave 178 clouds, same slope in overlapping mass range [2.3 CO Masses: "the mass function for clouds identified by SExtractor has the same slope in the$\log_{10}(M/M_\odot)$ range of 6.6 to 7.6"]
- step 4: star complex ages and masses from HST
  - method: SExtractor on F439W, photometry in other filters, population synthesis fits [2.5 Star-forming Complexes and CO Clouds: "we ran SExtractor on the F439W images for each galaxy to identify the most prominent star-forming regions"]
  - software: SExtractor, IRAF imexamine
  - parameter: 10 contiguous pixels above 10 sigma [2.5 Star-forming Complexes and CO Clouds: "restricted to 10 contiguous pixels greater than the $10\sigma$ threshold"]
  - assumption: Bruzual & Charlot models, solar abundance, exponentially decaying SFH with 10 Myr decay time [2.5 Star-forming Complexes and CO Clouds: "The star formation history for each region was assumed to be a decaying exponential with a decay time of 10 Myr."]
- result: Number of CO clouds = 249 ± not stated clouds [2.2 Identification of CO Clouds: "The final number of clouds was then 249"]
- result: Star complex mass slope = -0.7 ± 0.1 dimensionless [2.5 Star-forming Complexes and CO Clouds: "The slopes are the same, $-0.7\pm 0.1$"]
- limitation (authors): Mass ratios are not true efficiencies as the association of complex with cloud is unknown [2.6 Correlations: "we do not know which complex formed in which cloud"]
- not stated (card): Details of ALMA calibration and imaging (CASA version, weighting, cleaning, flux calibrator); Mask smoothing parameters and velocity continuity thresholds; Exact bin edges/fit ranges for mass function slopes; Cloud rectangle photometry boundaries; Cloud catalog not given

### 2015A&A...584A..78C: ALMA constraints on the faint millimetre source number counts and their contribution to the cosmic infrared background (2015; high_z_galaxies, cosmology; archival_reuse)
- question: What are the faint (sub-mJy) number counts of millimetre sources at 1.1 and 1.3 mm from deep ALMA maps, and what fraction of the cosmic infrared background do they resolve?
- step 2: Extract sources and set the detection threshold
  - method: 2D Gaussian fit candidates with S/N>3.5 and size consistent with beam (at most 1.5x beam); negative-map test and blank-field simulations used to assess spurious sources [3.1 Source catalogue: "the size of the 2D Gaussian fitting the putative source must be consistent, within the errors, with the beam size of the selected map (or at most marginally resolved, within 1.5 times the beam size)."]
  - software: CASA simobserve
  - parameter: S/N>3.5; 50 sources detected [3.1 Source catalogue: "In the 18 continuum maps, we detected 50 sources with S/N in the range 3.5-38.4, and none of them appear to be marginally resolved."]
  - validation: maps multiplied by -1 to count negative sources; 300 simulated blank-field maps [6 ALMA noise fluctuations: "The number of negative sources is equal to those of positive ones at any S/N"]
- step 3: Completeness and effective survey area
  - method: Inject artificial sources, 1000 iterations per map, 4-8 per simulation, in 0.05-1 mJy; recovered if S/N>=3.5; A_survey = sum C_i A_i [3.2 Completeness and survey area: "we iterated the procedure of inserting artificial sources for each continuum map 1000 times, using four to eight artificial sources in each simulation for each field."]
- step 4: Flux boosting correction
  - method: Inject sources with S/N 3-8 in maps not corrected for primary beam, 10^4 repeats, boost = S_out/S_in vs S/N [3.3 Flux boosting: "We repeated this simulation for each ALMA continuum map $10^4$ times."]
  - parameter: boost ~1.09 at S/N=3.5 [3.3 Flux boosting: "At S/N = 3.5, the boost fraction is $\simeq$1.09"]
  - validation: Compared with Hogg & Turner Eq. 4 prescription using Schechter prior; slopes consistent [4.1 Differential number counts: "the slopes obtained with this correction factor are consistent with those obtained using a boost factor estimated in Sec."]
- step 6: Differential number counts with uncertainties
  - method: Sum of (1-f_c)/A_survey in bins of dLogS=0.2, scaled to 1; f_c = negative/positive ratio at source S/N; errors from Poisson (Gehrels), cosmic variance (Moster tool), completeness/boosting [4.1 Differential number counts: "Therefore, the contribution of each source to the number counts is (1-$f_{\rm c}$) divided by its respective effective survey area $A_{\rm survey}(S)$."]
  - software: Moster et al. 2011 cosmic variance tool
  - parameter: cosmic variance with z=3.5, dz=3, M*=10^10.5 Msun [4.1 Differential number counts: "We assume a mean redshift of $z=3.5$, a redshift bin size of $dz = 3,$ and a stellar mass of 10$^{10.5}$ $\mathrm{M}_{\odot}$"]
  - validation: Poisson errors dominate; counts from within one primary beam consistent [4.1 Differential number counts: "the uncertainty on logarithmic differential number counts is completely dominated by the Poisson errors."]
- result: Number of detected sources = 50 ± not stated sources [3.1 Source catalogue: "In the 18 continuum maps, we detected 50 sources with S/N in the range 3.5-38.4"]
- result: Flux boost at S/N=3.5 = 1.09 ± not stated dimensionless [3.3 Flux boosting: "At S/N = 3.5, the boost fraction is $\simeq$1.09"]
- limitation (authors): CIB uncertainties prevent a precise resolved fraction; no source redshifts or SEDs [4.5 Cosmic infrared background: "we are not able to exactly determine the fraction of CIB resolved."]
- not stated (card): Source-extraction code and the exact Gaussian-fitting tool used for 2D source fitting are not named; Image size, cell size, clean threshold and iterations for each map; Which line channels were flagged as line-free in each field; Manual data-weight rescaling factors for BDF fields; Precise source flux catalogue (positions, fluxes, S/N) for all 50 sources; Binning edges and the counts per bin; Sch…

### 2019A&A...632A..38A: A radio census of the massive stellar cluster Westerlund 1 (2019; star_formation, stellar_physics; multi_facility_alma_minor)
- question: Measure radio fluxes, spectral indices and mass-loss rates of massive stars in Westerlund 1 with ATCA (compared with earlier ALMA 100 GHz data) and characterise the diffuse cluster emission
- step 2: Extract source fluxes
  - method: SEAC floodfill source extraction with watershed segmentation (NOISE and GAUSS) for core/total components [3 Analysis: "These were set at 5$\sigma$ for the seed threshold and 3$\sigma$ for the flood threshold."]
  - software: SEAC, AIPS, ParselTongue
  - parameter: seed 5 sigma, flood 3 sigma, local rms from noise map [3 Analysis: "The value of $\sigma$ is the rms value of the local spatial region."]
  - validation: Visual inspection and comparison with Do10 8.6 GHz fluxes [3.2 Confirmation of ATCA detected Sourc…: "this required a thorough visual inspection of the SEAC results, for all segmentation options, on each dataset"]
- result: Stellar radio detections in FULLCONCAT = 30 ± not stated stars [5.1 Stellar sources: "These radio observations led to 30 radio detections of known stellar sources in Westerlund 1"]
- limitation (authors): Diffuse emission may be misattributed to stars; errors are potentially underestimates [3.2 Confirmation of ATCA detected Sourc…: "Errors quoted in this paper are therefore potentially underestimates of the true uncertainty on these values"]
- not stated (card): Archival ALMA data reduction details (done in the earlier paper); Terminal velocities and Teff values adopted per star for the mass-loss rates; Exact taper parameters for TAPER5/TAPER9/TAPERALMA; SEAC grid cell number and per-source segmentation parameters; ATCA project codes and exact data location; Number of ALMA Band 3 data details (configuration, beam)

### 2025NatAs...9.1553F: Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn (2025; high_z_galaxies; observational_alma_primary)
- question: How do the internal clumpy substructure and the underlying gas dynamics of a lensed young galaxy at z=6.072 relate, and how does this compare with simulations?
- step 4: Identify clumps and measure sizes in NIRCam F150W
  - method: SExtractor detection then simultaneous 16-component GALFIT Sersic fit [7. Properties of the individual star-fo…: "All 16 components are then fitted simultaneously within this adjusted region."]
  - software: SExtractor, GALFIT
  - parameter: DETECT_MINAREA=9, DETECT_THRESH=2.0, DEBLEND_NTHRESH=64, DEBLEND_MINCONT=0.0001; Sersic n=1 [7. Properties of the individual star-fo…: "except for DETECT_MINAREA = 9, DETECT_THRESH = 2.0, DEBLEND_NTHRESH = 64, and DEBLEND_MINCONT = 0.0001"]
  - fitting: GALFIT simultaneous fit with bounded parameters [7. Properties of the individual star-fo…: "All 16 components are then fitted simultaneously within this adjusted region."]
  - validation: n=2 for all components gives sizes within ~50% [7. Properties of the individual star-fo…: "the resulting output sizes are consistent with our original results with the $n=1$ assumption within $\sim50\%$"]
- result: Clump flux fraction in F150W = 69.9 ± not stated percent [7. Properties of the individual star-fo…: "the sum of the fluxes from the 15 clumps accounts for 69.9% of the total flux"]
- limitation (authors): Magnification systematic uncertainty up to ~25% [4. Lens model: "we conclude that the magnification uncertainty in this study does not exceed $\sim$25%"]
- limitation (authors): Clump number may increase with better data; ALMA beam larger than clumps so gas mass only for 7 clumps [7. Properties of the individual star-fo…: "while this number could be increased with further high-resolution observations in the future"]
- not stated (card): Line-free channels and frequency range used for continuum fit; Source-plane reconstruction algorithm details and resulting cube pixel scale; 3DBarolo parameter file settings (ring widths, normalization details, masking thresholds); Calibrators and flux-scale uncertainty for ALMA data; Exact SExtractor/GALFIT convergence setup and PSF used for GALFIT; How [C II] luminosity per pixel was derived fr…

### 2016A&A...586A..70L: Anatomy of a blazar in the (sub-)millimeter: ALMA observations of PKS 0521-365 (2016; agn_and_quasars; archival_reuse)
- question: What are the synchrotron and thermal (sub-)millimeter emission properties of the components of the blazar PKS 0521-365 (core, jet, counter-jet, hot spot, perpendicular structure), and how do they vary in time and frequency?
- step 3: Detect point sources
  - method: SExtractor on WT-filtered band 3+6+7 at 4.5 sigma, minimum 5 pixels [3 (Sub-)millimeter distribution: "using the SExtractor software (Bertin & Arnouts, 1996) at a 4.5-$\sigma$ level with a minimum of 5 pixels per sources"]
  - software: SExtractor
  - validation: Counts compared with Hatsukade et al. (2013) [3 (Sub-)millimeter distribution: "this estimation is similar, but lower, to the one derived by Hatsukade et al. (2013) using ALMA fields at 238 GHz"]
- result: Detected point sources in 1'x1' box = 16 ± not stated sources [3 (Sub-)millimeter distribution: "A total of 16 sources are detected in a $1\ensuremath{'}\times1\ensuremath{'}$ box"]
- limitation (authors): Irregular, sparse time sampling prevents robust variability analysis; VI are lower limits. [4 (Sub-)millimeter variability: "These values of the VI must be considered as lower limit during the year 2012 since the sampling is sparser than the variability"]
- not stated (card): CASA version and whether archive calibration or manual scripts were used; Flux calibrator and flux scale uncertainty; Self-calibration solution intervals and iterations; CLEAN parameters (cell, image size, threshold, masks); Wavelet pixel size and per-scale noise estimation method; Region definitions (polygons) for jet and counter-jet; Method of stacking datasets for the counter-jet; Spectral ind…

### 2020A&A...640A..27V: Protoplanetary disk masses in NGC 2024: Evidence for two populations (2020; protoplanetary_disks, star_formation; observational_alma_primary)
- question: How does external photoevaporation and environment affect the dust masses of disks across the young NGC 2024 cluster, compared with other star-forming regions?
- step 4: Search for new sources and stack nondetections
  - method: Blind search for >4.8σ peaks checked in both images; weighted stack of 122 nondetections with detections masked [3.2.3 Point sources without near infrar…: "These sources were first identified by performing a blind search for $>4.8\,\sigma$ peaks in the data"]
  - validation: 4.8σ chosen to give <1 expected false positive (0.6) [3.2.3 Point sources without near infrar…: "we expect less than one false positive given the number of independent beams in the full image (0.6 on average)."]
- result: Stacked nondetection 3σ limit = 20 uJy (<0.96 M_Mars) ± not stated uJy [3.2.4 Stacking analysis of nondetections: "The resulting $3\sigma$ mass limit for the stacked sources is $20\,\mu$Jy, or $< 0.96\,M_{\text{Mars}}$."]
- limitation (authors): Stellar mass differences and binarity cannot be accounted for in the comparison [4.2 Comparison to other star-forming re…: "we cannot take into account possible differences in stellar masses, even though these may be significant"]
- limitation (authors): Kaplan-Meier assumption of nondetection independence not met at low masses [3.2 Dust masses of NGC 2024 disks: "The third requirement is not met"]
- not stated (card): tclean cell size, image size, deconvolver, threshold and masks; Line-free channels flagged; Self-calibration solution intervals and reference antenna; Details of aperture photometry (aperture size, background); Which Kaplan-Meier implementation was used; How spectral indices of IRS 2 and IRC 101 were computed; CASA calibration pipeline version and manual vs pipeline calibration

### 2024ApJ...964...18C: Resolved Measurements of the CO-to-H<SUB>2</SUB> Conversion Factor in 37 Nearby Galaxies (2024; nearby_galaxies, milky_way_ism; multi_facility_alma_minor)
- question: How does the CO-to-H2 conversion factor (alpha_CO) vary at 2 kpc resolution across 37 nearby galaxies, and how does it scale with local and galaxy-integrated quantities, especially stellar mass surface density?
- step 3: Regress alpha_CO on local and galaxy-averaged quantities
  - method: Spearman-type correlation and linear regression log alpha_CO = m x + b in completeness >50% zone [4.1 Correlations with Local Conditions: "we perform linear regression with the functional form: $$\begin{equation} \log\ensuremath{\alpha_{\rm CO}}=mx+b,"]
  - fitting: Errorbars from 1000 bootstraps [4.1 Correlations with Local Conditions: "We first bootstrap the measurements by 1000 times with uncertainties"]
- limitation (authors): Data concentrated in narrow metallicity range 8.4-8.6, limiting metallicity analysis [4.1 Correlations with Local Conditions: "$>80\%$ of our data is concentrated in a small dynamic range of $8.4 \leq \ensuremath{12+\log({\rm O/H})}\leq 8.6$."]
- not stated (card): Exact PHANGS-ALMA CO(2-1) product version, moment-map masking and noise maps; Dust SED fit outputs (J. Chastenet et al. in prep.) and uncertainty maps; Binning details for plots and regression method for linear fits; HI processing for EveryTHINGS and PHANGS-VLA (in preparation)

### 2016ApJ...833...67W: ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Survey Description (2016; high_z_galaxies; large_program_or_survey)
- question: Obtain an unbiased census of molecular gas (CO, [CII]) and dust continuum emission in high-redshift galaxies via full band 3 and band 6 frequency scans of the Hubble Ultra Deep Field, and characterize the line candidates.
- step 3: Blind line search for positive and negative peaks
  - method: findclumps: floating averages over 3,5,7,9-channel windows on 7.8 MHz (3mm) and 31.2 MHz (1mm) cubes, peak finding with daofind, trimmed by primary beam radius, duplicates removed, bright continuum sources masked [3.1 The blind line search: "we ran our search over 3, 5, 7, and 9–channel windows, i.e., kernel line widths of $\sim$50–300 km s$^{-1}$"]
  - software: IRAF daofind, findclumps
  - parameter: Candidates kept within sqrt2 x primary beam radius at 3mm (53'' at 84 GHz, 39'' at 115 GHz) and 30.9'' radius at 1mm [3.1 The blind line search: "within a fixed radius of $30.9''$ at 1mm (given that the latter is a mosaic)"]
  - assumption: Negative candidates are all noise peaks; no absorption expected [3.1.1 Fidelity: "all the ‘negative’ line candidates will be noise peaks, while the ‘positive’ line candidates will be a mixture of noise peaks and genuine lines"]
  - validation: Fidelity from negative vs positive counts; completeness via simulated sources [Completeness: "We address this by inserting artificial line sources of various strengths and widths in our data cubes, then calculating our ability to recover them in our line search."]
- step 4: Compute fidelity
  - method: fidelity = 1 - N_neg/N_pos; fitted with error function; require fidelity >=60% and >2 sigma in consecutive channels [3.1.1 Fidelity: "For the analysis of our blind search, we request a fidelity level of 60% or higher."]
  - software: findclumps
  - parameter: C_3mm=5.1, C_1mm=5.0, sigma_3mm=0.4, sigma_1mm=0.8 [3.1.1 Fidelity: "where $C_{\rm 3mm}$=5.1, $C_{\rm 1mm}$=5.0, $\sigma_{\rm 3mm}$=0.4, $\sigma_{\rm 1mm}$=0.8"]
  - fitting: error-function parameterization of fidelity vs S/N, not physically motivated [Fidelity: "While not physically motivated, the following error function provides a good description of the observed trend, with the following parameterization:"]
- step 5: Measure completeness
  - method: Inject 2500 Gaussian artificial lines with random position, frequency, flux and width; rerun search [3.1.2 Completeness: "adding 2500 artificial line sources to the data cube, re–running our line searching algorithm, and comparing the number of recovered sources with the input catalog"]
  - software: findclumps
  - parameter: Peak flux 0.22-1.00 mJy (3mm), 0.5-2.0 mJy (1mm); widths 50-500 km/s [3.1.2 Completeness: "The line widths span the range 50–500 km s$^{-1}$."]
- step 7: Compare detected line counts with MAGPHYS expectations
  - method: Scale da Cunha et al. predicted line number counts to survey area and compare with observed counts, no completeness/fidelity correction [4 Comparison with expectations: "For this back–of–the envelope calculation, we do not correct our measurements for completeness or fidelity"]
  - software: MAGPHYS
  - assumption: Low (Milky Way) and high (M82) excitation bounds [4 Comparison with expectations: "the low–excitation case of the global Milky Way disk, and the high–excitation case of the nucleus of the local starburst galaxy M82"]
- result: Band 3 line candidates = 10 ± <4 spurious count [3.2.1 Properties: "Our blind search resulted in 10 line candidates from the 3 mm search, and 11 line candidates from the 1 mm search"]
- result: Band 6 line candidates = 11 ± <4 spurious count [3.2.1 Properties: "Our blind search resulted in 10 line candidates from the 3 mm search, and 11 line candidates from the 1 mm search"]
- result: 3mm fidelity 60/80/95% S/N = 5.17, 5.34, 5.57 ± not stated dimensionless [3.1.1 Fidelity: "This implies that we reach 60, 80, and 95% fidelity levels at $S/N$=$5.17$, $5.34$, and $5.57$ at 3mm"]
- result: 1mm fidelity 60/80/95% S/N = 5.15, 5.50, 5.97 ± not stated dimensionless [3.1.1 Fidelity: "and at $S/N$=$5.15$, $5.50$, and $5.97$ at 1mm"]
- result: 3mm 50% completeness peak flux = >0.45 for widths >100 ± not stated mJy (km/s for width) [3.1.2 Completeness: "At 3mm, the completeness is $>50$% for peak flux densities $F_\nu^{\rm line}>0.45$ mJy, and for line widths $\Delta v>100$ km s$^{-1}$."]
- result: 1mm 50% completeness peak flux = >0.8 for widths >100 ± not stated mJy (km/s for width) [3.1.2 Completeness: "The line search in the 1mm mosaic shows a completeness $>50$% for peak flux densities $>$0.8 mJy and widths $>100$ km s$^{-1}$."]
- limitation (authors): Survey area small, limited by ALMA early-science time [5 Summary: "The current size of the survey is admittedly small, limited by the amount of time available in ALMA ‘early science’."]
- not stated (card): Exact line-free channels used for continuum maps; S/N threshold used in findclumps/daofind before fidelity cut; Cleaning (deconvolution) parameters, thresholds and masks for cubes; Flux calibration scale uncertainty; Band 6 CASA/pipeline version; findclumps code is not released; Execution block selection/flagging beyond pipeline; Spectral line fitting method for flux, FWHM and uncertainties

### 2020ApJ...902..110D: The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Multiband Constraints on Line-luminosity Functions and the Cosmic Density of Molecular Gas (2020; high_z_galaxies, milky_way_ism; large_program_or_survey)
- question: What are the CO and atomic-line luminosity functions in the ASPECS 1.2 mm cube combined with the 3 mm results, and how does the cosmic molecular gas density rho_H2 evolve with redshift?
- step 1: Line search
  - method: FINDCLUMPS with floating channel average; positive and negative peaks, S/N>4 [3.1: "We search for emission lines in the original and the continuum-subtracted ASPECS LP 1.2 mm cubes using FINDCLUMPS"]
  - software: FINDCLUMPS
  - fitting: Gaussian noise tails plus power-law signal fitted to negative then positive distributions [3.1: "we fit the observed distribution of the noise peaks with the tails of a Gaussian function centered at zero, and the additional signal due to real sources as a power law."]
  - validation: Fidelity from negative/positive peak ratio treated as an upper limit [3.1: "we conservatively treat these estimates of the fidelity as upper limits"]
- step 2: Completeness
  - method: Inject 8000 mock 3D Gaussian lines, rerun search [3.1: "A total of 8000 mock lines were injected, $>3000$ of which reside within the area with $>50$% primary beam response."]
  - parameter: FWHM 0-800 km/s, peak 0-3 mJy; drop completeness<0.2 [3.1: "We drop all line candidates with a completeness of $<0.2$ from our analysis."]
- step 6: Luminosity functions and rho_H2
  - method: 5000 realizations; keep lines by fidelity; 0.5 dex bins; Gehrels Poisson errors; completeness and volume correction; sum over detections for rho_H2 [3.5: "we create 5000 realizations of the luminosity functions, folding in all of the uncertainties"]
  - validation: Compared with alternative treatments of lines without counterparts and cosmic variance simulations [Identification of line candidates witho…: "To first order, the $\rho_{\rm H2}$ evolution is unaffected by our treatment of the sources without a counterpart in the catalog."]
- result: Line candidates with fidelity>0.2 = 234 ± not stated count [3.1: "The final catalog from the line search consists of 234 line candidates with fidelity $>0.2$, 75 with fidelity $>0.5$, and 35 with fidelity $>0.8$."]
- result: Decline in rho_H2 from z~1.5 to present = ~6 ± not stated factor [4.3: "followed by a $\sim 6\times$ decline to the present day"]
- result: CO luminosity function offset CO(2-1) vs CO(5-4) at z~1.43 = ~0.5 ± not stated dex [4.1.1: "The inferred CO luminosity functions show an offset of about 0.5 dex in luminosity for a fixed number density."]
- limitation (authors): Constant alpha_CO may be invalid at z>3 [4.3: "The arguments presented in Sec. [3.4] for a Galactic value may not be valid at $z\mathrel{\rlap{\lower 3pt \hbox{$\sim$}} \raise 2.0pt \hbox{$>$}}3$"]
- not stated (card): Observing details (executions, integration time, project calibrator details); FINDCLUMPS kernel widths and code availability; Priors and chain settings of the custom MCMC line-fit; CASA version; Exact line-free channels used for continuum subtraction; Fidelity fit parameter values; Final cube and catalog of 234 line candidates (not given in the paper)

### 2019ApJ...887...88E: Star Formation Efficiencies at Giant Molecular Cloud Scales in the Molecular Disk of the Elliptical Galaxy NGC 5128 (Centaurus A) (2019; nearby_galaxies, agn_and_quasars, milky_way_ism; observational_alma_primary)
- question: What is the resolved Kennicutt-Schmidt star formation law and star formation efficiency at GMC scales (~40 pc) in the molecular disk of the elliptical galaxy Cen A?
- step 5: Build resolved KS law and SFE maps at 43 pc
  - method: Regrid CO and 8 um PAH to 2.4" pixels; SFR surface density via log Sigma_SFR = 0.844 log Sigma_L8 - 30.923; inclination correction 70 deg; fit orthogonal distance regression [5 Spatially Resolved KS Law: "The pixel size in our analysis is 2.4$''$ (or 43 pc, i.e. that of the 8 $\mu$m map)."]
  - software: scikit-learn
  - parameter: Sigma_mol completeness ~4 Msun/pc2 (3 sigma, 10 km/s) [5 Spatially Resolved KS Law: "complete down to surface densities of $\Sigma_{\rm mol} \simeq 4\,M_\odot\,{\rm pc}^{-2}$"]
  - assumption: Fixed inclination 70 deg [5 Spatially Resolved KS Law: "Our surface density maps have been corrected by a fixed inclination of 70$^\circ$."]
  - fitting: Gaussian mixture model (2 components, full covariance chosen by BIC) after removing 19 AGN points; orthogonal distance regression [5.1 KS Law: "A Bayesian Information Criterion (BIC) selects the best model, which is the one obtained with the full covariance matrix"]
  - validation: Compared fit with Boquien et al. 2011 calibration [5 Spatially Resolved KS Law: "The two fits have a very similar slope but the (cite: 2011AJ....142..111B) intercept is slightly higher than the one we find."]
- result: Global SFE = 0.6 (depletion time 1.5 Gyr) ± not stated Gyr^-1 [5.2 SFE: "so the SFE is 0.6 Gyr$^{-1}$ (or depletion time $\tau =$ 1.5 Gyr)"]
- result: KS slope (orthogonal regression), all data = 0.63 (intercept -2.4) ± not stated dimensionless [5.1 KS Law: "The slope of the orthogonal distance regression fit to the data points characterizing the SF law is $N$ = 0.63 (intercept is –2.4)."]
- result: KS slope in CND = 0.28 (intercept -1.6) ± not stated dimensionless [5.1 KS Law: "for the CND $N$ = 0.28, and intercept –1.6"]
- result: Mean SFE CND / outer disk = 0.32 / 1.29 ± stddev 0.24 / 0.93 Gyr^-1 [Table 2: "| CND | 1.65 | 0.32 | 0.26 | 0.24 |"]
- limitation (authors): Large scatter, projection effects and warped disk uncertainty in the KS fits; XCO uncertainty in CND [5.1 KS Law: "We note however that the scatter is large"]
- not stated (card): Imaging parameters (weighting, robust, tclean deconvolver, mosaic gridder, cleaning threshold) are not given; Final synthesized beam and rms noise of the combined cube; Line-free channels used for continuum subtraction; How TP data were combined with interferometer data (feather vs joint deconvolution); Spitzer map convolution/regridding details and the AGN-contaminated pixel mask; GMM initialisa…

### 2013MNRAS.432....2K: An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: high-resolution 870 μm source counts (2013; high_z_galaxies; observational_alma_primary)
- question: Do the single-dish 870-um SMG number counts, especially the bright end, hold up when the LESS sources are resolved at ~1.5 arcsec with ALMA, or are they inflated by blending of multiple fainter SMGs?
- step 2: Extract sources
  - method: Peaks above 2.5 sigma modelled with MH-MCMC elliptical Gaussian fits in 2x2 arcsec regions; point-source three-parameter model peak flux adopted [3.1 Source extraction and characterizat…: "Metropolis-Hastings Markov chain Monte Carlo (MH-MCMC) algorithm to determine the best six parameter fit for an elliptical Gaussian"]
  - software: IDL source extraction code
  - fitting: MH-MCMC; fitting error from posterior after correcting for chain autocorrelation [3.1 Source extraction and characterizat…: "For each parameter in the fit its posterior distribution determines the fitting error, after correcting for auto-correlation in the Markov chain."]
- step 3: Determine detection threshold via simulations
  - method: Insert five sources into source-removed maps, 16 times per map (7,400 sources), rerun extraction; measure recovered and spurious fractions [3.2 Source extraction efficiency and fl…: "This process is repeated 16 times per map. Thus, in total we insert 7,400 sources into the 88 ALMA maps."]
  - parameter: 3.5 sigma limit: ~99% recovered, ~1.6% spurious [3.2 Source extraction efficiency and fl…: "the source extraction recovers $\sim$ 99% of all $>$ 3.5$\sigma$ sources, while a sample selected above this threshold contains only $\sim$ 1.6% spurious detections"]
  - validation: Compared summed ALMA fluxes weighted by LABOCA beam with W09 deboosted fluxes [3.2 Source extraction efficiency and fl…: "the resulting median ALMA/LABOCA flux density ratio and bootstrap error is 0.83$^{+0.09}_{-0.04}$"]
- step 4: Derive differential and cumulative counts
  - method: Per-source probability p=2-f_recovered-f_spurious, summed per flux bin and normalised by effective area; 1000 flux resamples, standard deviation added in quadrature to Poisson error [4.1 Derivation of ALMA 870 um source co…: "derive the counts for 1,000 resamples"]
  - parameter: A_ALMA = (88/126) x 0.35 deg^2 [4.1 Derivation of ALMA 870 um source co…: "where $N_{\rm{maps}}({\rm ALMA})=$ 88 is the number of ALMA maps used in this study, $A_{\rm{LESS}}=$ 0.35 deg$^2$"]
  - assumption: Gaussian flux errors [4.1 Derivation of ALMA 870 um source co…: "We thereby assume that the individual error distributions are Gaussian"]
- result: Number of >3.5 sigma SMGs in 88 maps = 99 ± not stated sources [3.2 Source extraction efficiency and fl…: "In total we detect 99 individual SMGs at $>$ 3.5 $\sigma$ in the 88 maps used."]
- result: Median ALMA/LABOCA flux ratio (3.5 sigma) = 0.83 ± +0.09/-0.04 dimensionless [3.2 Source extraction efficiency and fl…: "the resulting median ALMA/LABOCA flux density ratio and bootstrap error is 0.83$^{+0.09}_{-0.04}$"]
- result: Median ALMA/LABOCA flux ratio (3 sigma) = 0.97 ± +0.07/-0.04 dimensionless [3.2 Source extraction efficiency and fl…: "results in a median flux ratio of 0.97$^{+0.07}_{-0.04}$"]
- result: Cumulative counts N(>4.2 mJy) = 167.3 ± 28.6 deg^-2 [Table 1: "| $4.2$ | 167.3 $~(28.6)$ |"]
- limitation (authors): Counts below the LESS flux limit are biased because fields were targeted near brighter sources [4.1 Derivation of ALMA 870 um source co…: "Below the LESS flux limit the source counts derived from our ALMA maps must be considered biased"]
- not stated (card): CASA version and calibration steps (deferred to H13); Imaging task parameters, clean threshold and masks; Source finder code is not public/named; Parametrisations of f_recovered and f_spurious versus SNR; Which 88 maps were selected, and the bin edges for the counts; Flux scale uncertainty

### 2017ApJ...838..114K: ALMA Observations of Starless Core Substructure in Ophiuchus (2017; star_formation; observational_alma_primary)
- question: Do starless cores in Ophiuchus show compact substructure in ALMA Band 3 continuum, and is the number of detections consistent with turbulent fragmentation predictions (vs Chamaeleon I)?
- step 1: Select and classify targets
  - method: Classify SCUBA cores as protostellar if within 15" of a Spitzer YSO; remove six spurious cores using SCUBA-2 [2.1 Target Selection: SCUBA: "We apply a simple definition that protostellar dense cores are separated by no more than 15$''$ (i.e., roughly one SCUBA 850 $\mu m$ beam) from one (or more) *Spitzer*-identified YSOs."]
  - validation: Compared with SCUBA-2 Pattle15 catalogue [2.1.1 Comparison of SCUBA and SCUBA-2 d…: "We examined our adopted dense core catalogue using this improved SCUBA-2 dataset."]
- not stated (card): tclean/clean parameters: weighting/robust, cell and image size, threshold, niter; Self-calibration solution intervals and which fields were self-calibrated; CASA version and pipeline version; Flux calibrator and flux scale uncertainty; Detection threshold / source-finding criteria beyond 'compact sources' (apart from source 37 at 4.9 sigma); Which fields were mosaicked in what way (imaging parame…

### 2025ApJ...995..219F: PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon (2025; high_z_galaxies, star_formation; observational_alma_primary)
- question: Is the Planck-selected lensed source PJ0846+15 a single DSFG or a strongly lensed protocluster core at z~2.67, and what are its lens model, SFR, gas/dust masses, dynamical mass and kinematics?
- step 2: Blind search for CO(3-2) detections
  - method: FindClumps blind search after by-eye inspection [3 The CO Detections: "utilizing the `FindClumps` algorithm (cite: Walter_2016) built into the `Interferopy` python package (cite: interferopy)."]
  - software: Interferopy
  - parameter: S/N>2.5 per channel across >=3 continuous channels [3 The CO Detections: "we impose a criterion of S/N$>2.5$ per channel, across $\geq3$ continuous channels."]
  - validation: Counterparts sought in F160W, r', z' [3 The CO Detections: "We search for any counterparts in F160W, r$^{\prime}$ and z$^{\prime}$ to further corroborate secure detections."]
- result: Number of CO(3-2) detections = 18 (11 sources) ± not stated dimensionless [3 The CO Detections: "In total we report 18 CO(3–2) detections"]
- limitation (authors): Lens model systematics not included; mass-sheet degeneracy possibly unbroken [4.4 The J0846 Model Results: "We acknowledge that this does not account for the systematics that arise from cluster lens modeling, that likely dominate the overall uncertainties."]
- limitation (authors): Gas mass is a lower limit given alpha_CO [5.2 Estimates of molecular gas and dust…: "thereby sets a lower limit for the molecular gas masses"]
- not stated (card): Line-free channel ranges and continuum-subtraction fit order; Clean threshold, niter, masking and deconvolver for tclean; Self-calibration and flux calibrator details; ALMA flux scale uncertainty; Exact line-extraction aperture masks and multi-Gaussian fit initial conditions; Lens model GLAFIC constraints, priors, parameter ranges, and MCMC settings (walkers, steps); Mass absorption coefficient u…

### 2019MNRAS.485.1188B: ALMA photometry of extragalactic radio sources (2019; agn_and_quasars, cosmology; data_release_or_catalog)
- question: Can ALMA calibrator photometry validate the Planck PCNT photometry, positions and completeness, and be used to extrapolate 100 GHz radio source counts to higher ALMA bands?
- step 3: Assess PCNT completeness
  - method: Fraction of ACC objects with PCNT counterparts (SNR>=3) versus ALMA flux density; 10,000 Gaussian simulations for 143 GHz [2 Validation: "we have performed 10,000 simulations of *Planck* observations of the 100 ALMA calibrators."]
  - validation: Compared with PCCS2 90% completeness limits [2 Validation: "At 100, 217, 353 and 545 GHz our results are in excellent agreement with the estimates of the 90% completeness limits given by (cite: PCCS2)."]
- result: PCNT 90% completeness at 100/143/217/353/545 GHz = 266/312/170/296/597 ± not stated mJy [Table 1: "| 100 | 269 | 266 | 562 |"]
- limitation (authors): Planck and ALMA data are non-simultaneous so blazar variability adds dispersion [Footnote 5: "Blazars are known to be strongly variable and *Planck* and ALMA measurements are non-simultaneous."]
- not stated (card): ACSC measurement procedure and raw flux values; How ACSC and ALMACAL entries were merged/duplicates handled; How characteristic band frequencies (e.g. 95 GHz) were derived; Cross-match procedure details beyond the 3 arcmin radius; Binning used for validation and completeness plots; Method for fitting polynomial representations of counts

### 2020ApJ...895..126H: The Evolution of Dust Disk Sizes from a Homogeneous Analysis of 1-10 Myr old Stars (2020; protoplanetary_disks, solar_system; archival_reuse)
- question: How do dust disk sizes, and their relations to mm luminosity and stellar properties, differ among star-forming regions of different ages when derived homogeneously, and how does the Solar System's outer edge compare?
- step 4: Sample selection
  - method: Remove multiples with separation <=2"; remove 15 spurious models with size uncertainty >66% of size inspected by eye [10 Determination and removal of spuriou…: "Of the 23 disks that meet this metric, we find 15 that are obviously problematic, and hence removed them from our analysis"]
- result: Disks with estimated sizes = 152 (50 Lupus, 58 Cha I, 44 USco) ± not stated disks [4.1 Subsample: "This leaves us with 152 disks: 50 from Lupus, 58 from Cha I and 44 from USco which we include in our analysis."]
- limitation (authors): Oph and Tau/Aur SMA samples are flux-limited and biased bright [2.1 Oph and Tau/Aur: "the Oph and Tau/Aur samples come from flux-limited SMA observations, and consequently are biased towards brighter objects"]
- limitation (authors): Correlation tests do not include upper limits and uncertainties [5.1 Relations: "A limitation of all these statistical tests is that they do not include upper-limits and uncertainties in the assessment."]
- not stated (card): Exact channel/time averaging per source; Weighting/robust and imaging parameters (visibility fitting only, uv-data weights); Flux calibration uncertainty; Line-free channel selection / handling of CO line contamination in band 7; Exact Lmm conversion (flux integration, fluxes used) from Andrews2018a; Exact MCMC convergence criterion per source; Rule for choosing between resolved and unresolved mo…

### 2016ApJ...833...68A: The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Properties of the Faintest… (2016; high_z_galaxies, cosmology; large_program_or_survey)
- question: What are the 1.2-mm continuum number counts, the resolved fraction of the extragalactic background, and the properties of the faint dusty star-forming galaxies detected in the ASPECS Hubble UDF field?
- step 1: Detect sources and measure fluxes
  - method: SExtractor detection on non-PB-corrected maps; 2D Gaussian fit, peak flux used for unresolved sources [3.1 Source detection and flux measureme…: "We compute fluxes based on 2-dimensional Gaussian fit centered at the location of the SExtractor detection."]
  - software: SExtractor
  - parameter: minimum area 5 pixels (1.5''); extraction down to 2.5 sigma local; main sample >3.5 sigma [3.1 Source detection and flux measureme…: "We use a minimum area of 5 pixels ($1.5''$) for detection, extracting sources down to 2.5$\sigma$, where $\sigma$ is evaluated locally for each source."]
  - validation: fitted values agree with pixel values at source positions [3.1 Source detection and flux measureme…: "These fitted values are in agreement with the actual pixel values at the position of the sources."]
- step 2: Compute fidelity and completeness
  - method: Fidelity from detections in inverted negative map; completeness from Monte Carlo injection of artificial point sources; both parametrised with erf functions [3.2 Fidelity and completeness: "We ingest 10 artificial point-like sources with randomly generated flux levels (between $10-300 \mu$Jy) in the ALMA map."]
  - parameter: 100 artificial sources total (10x10), matched within 1''; fidelity A=log10(42), B=1/4; completeness A'=log10(35), B'=0.45 [3.2 Fidelity and completeness: "We repeat this process 10 times, for a total of 100 artificial sources."]
  - validation: input and recovered flux densities agree within uncertainties [3.2 Fidelity and completeness: "the input and recovered flux densities agree well within individual source uncertainties."]
- step 3: Derive cumulative number counts
  - method: N(S_i) = (1/A) sum P_j/C_j, summed cumulatively; Poisson plus flux errors [5 Number counts: "Since we are limited by the modest number of detections, we compute the cumulative number counts rather than computing differential counts"]
  - parameter: extended to 3 sigma, where fidelity and completeness are both 50% [5 Number counts: "we extend our number count measurements down to significances of $3\sigma$."]
  - validation: compared with literature counts [5 Number counts: "Our ALMA UDF observations appear to be in general agreement with these earlier measurements"]
- step 8: Compute EBL contribution
  - method: Integrate fidelity/completeness-corrected counts, add bright end from Karim+13 and Oteo+15 and stacking contributions of m2+m3; compare with Planck EBL at 242 GHz [7.1 Integrated intensity and fraction o…: "we directly integrate the number counts, corrected for fidelity and completeness, down to the faintest flux bin ($S_{\rm 1.2mm}\sim37\mu$Jy)."]
- result: Number of sources >3.5 sigma at 1.2 mm = 9 ± not stated sources [3.1 Source detection and flux measureme…: "Nine sources are detected in the 1.2-mm map at a significance above 3.5$\sigma$."]
- result: Integrated intensity from number counts = 7.8 ± 0.4 Jy/deg2 [7.1 Integrated intensity and fraction o…: "We obtain an integrated intensity of $7.8\pm0.4$ Jy deg$^{-2}$."]
- result: Fraction of Planck EBL from individual detections = 55% ± 4% percent [7.2 Nature of the sources that make up …: "This makes up $55\pm4\%$ of the EBL measured by *Planck* at 242 GHz"]
- result: Total EBL fraction with bright end and stacking = 80% ± 7% percent [7.1 Integrated intensity and fraction o…: "which makes up $80\pm7\%$ ($\sim77--84\%$) of the EBL at 242 GHz measured by *Planck*."]
- result: EBL extra contribution from stacking = 2.8 ± 0.5 Jy/deg2 [7.1 Integrated intensity and fraction o…: "We find an extra contribution of $2.8\pm0.5$ Jy deg$^{-2}$ or $\sim20\pm4\%$ of the EBL at 242 GHz."]
- limitation (authors): Small area makes counts and EBL fraction subject to cosmic variance. [7.3 The effect of cosmic variance: "measurements covering $\sim$1 arcmin$^{-2}$ or less of the sky, aiming to resolve the sources contributing to this background will be most likely highly affected by cosmic variance."]
- limitation (authors): Flux may be missed for resolved sources given small beam; beta result affected. [5.2 Stacking in the 3-mm continuum: "we could be missing flux that could contribute to a larger $\beta$ value."]
- not stated (card): CASA version and calibration/imaging details (robust, uv taper, cell size, image size, continuum channel selection), deferred to Paper I; Exact SExtractor configuration beyond minimum area and threshold; Whether the 1.2 mm map used is the collapsed cube of all channels with line masking; Weighting scheme for the Gaussian peak fitting and error estimates; MAGPHYS priors and parameter grids; Exact …

### 2020A&A...643A..53F: GOODS-ALMA: Using IRAC and VLA to probe fainter millimeter galaxies (2020; high_z_galaxies; observational_alma_primary)
- question: Can cross-matching 3.5-4.8 sigma ALMA 1.1 mm detections with IRAC, VLA and K-band catalogs yield a robust supplementary catalog of fainter millimeter galaxies, and how do their properties differ from the Main Catalog?
- step 2: Blind extraction at 3.5 sigma and counterpart cross-match
  - method: Extract sources down to 3.5 sigma in the 0.60'' image, cross-match with IRAC, VLA and K-band; keep IRAC within 0.3'' or within 0.7'' plus radio counterpart [4.2.1: "an IRAC counterpart either *(i)* closer than 0.3$''$ or *(ii)* closer than 0.7$''$ but associated with a radio counterpart in the 3 GHz catalog."]
  - software: BLOBCAT, GALFIT
  - parameter: cross-match radius 0.60'' for VLA and K-band; IRAC considered within 0.7'' [4.2.1: "It is equal to 0.60$''$, the FWHM of the tapered 1.1 mm ALMA image, for the cross-match with the VLA and ZFOURGE $K$-band catalogs."]
  - validation: Negative-image purity, Monte Carlo random association probabilities, comparison with ASAGAO/HUDF/ASPECS, KS test of stellar masses [4.2.1: "We randomly define a position within GOODS–South and then measure the distance to its closest IRAC neighbor"]
- step 3: Measure fluxes and sizes
  - method: uvmodelfit circular Gaussian in uv-plane; sizes below theta_min treated as unresolved and peak flux used [5.2 Flux and size measurements: "Flux densities of the Supplementary Catalog sources were measured by fitting the light profiles with a circular Gaussian in the *uv*-plane, using `uvmodelfit` in `CASA`"]
  - software: CASA
  - parameter: theta_min = 0.88 theta_beam/sqrt(S/N), theta_beam=0.60'' [5.2 Flux and size measurements: "\theta_{min}\,\simeq\,0.88\frac{\theta_{beam}}{\sqrt{\text{S/N}}}"]
  - validation: Injection-recovery test for flux boosting [5.2 Flux and size measurements: "we compared the recovered flux to the injected flux"]
- result: Supplementary Catalog size = 16 ± not stated sources [7 Conclusions: "In total we find 16 galaxies in the Supplementary Catalog that bring the total sample of GOODS-ALMA 1.1 mm sources to 35 galaxies."]
- result: Median 1.1 mm FWHM size, Supplementary vs Main = 0.32'' vs 0.18'' ± not stated arcsec [6.3 Sizes: "The median ALMA 1.1 mm FWHM of the galaxies in the Supplementary Catalog is indeed 0.32$''$ as compared to 0.18$''$"]
- result: Half-light radius, Supplementary vs Main = 1.3 kpc vs 0.65 kpc ± not stated kpc [6.3 Sizes: "is 1.3 kpc as compared to only 0.65 kpc for the Main Catalog"]
- result: Purity within 0.7'' of IRAC sources = 48 ± not stated % [4.2.1: "we get a much improved purity of 48% with 15 negative peaks"]
- result: KS test p-value, massive counterparts in positive vs negative image = 1.2e-2 ± not stated dimensionless [4.3: "A Kolmogorov-Smirnov (KS) test on these data gives a p-value of 1.2$\times$10$^{-2}$ between these two samples"]
- limitation (authors): Requiring an IRAC counterpart may reject real sources and bias toward massive galaxies. [4.2.1: "this criterion may lead us to reject real ALMA sources without any IRAC counterpart with the possible consequence of biasing our sample toward the most massive galaxies"]
- limitation (authors): Peak fluxes for unresolved sources may be underestimated by about 20%. [5.2 Flux and size measurements: "they may be lower by about 20 %"]
- not stated (card): ALMA calibration and imaging details (CASA version, weighting, robust, clean parameters) deferred to Franco2018; Tapering parameters (uv-taper values); Exact injection-recovery source distribution and flux model; IRAC deblending GALFIT model parameters; FAST++ input photometry and grid parameters; Radio catalog is unpublished (Rujopakarn et al., in prep.); uvmodelfit starting parameters

### 2018ApJ...857...19F: The ALMA View of GMCs in NGC 300: Physical Properties and Scaling Relations at 10 pc Resolution (2018; nearby_galaxies, milky_way_ism, star_formation; observational_alma_primary)
- question: Do GMCs in NGC 300, resolved at 10 pc and 1 km/s, follow the Milky Way scaling relations and mass spectrum, and what sets GMC properties (global vs local environment such as pressure)?
- step 5: Fit mass spectrum
  - method: Maximum-likelihood fit of cumulative M_lum distribution with truncated and untruncated power laws above completeness limit 8e3 Msun [5.1 GMC Mass Spectrum: "We fit the cumulative mass distribution of $M_{\rm lum}$ in our full sample of GMCs using the `mspecfit.pro` IDL code"]
  - software: mspecfit.pro (IDL)
  - parameter: completeness limit 8e3 Msun [5.1 GMC Mass Spectrum: "We adopt a completeness limit of $8\times10^3~\ensuremath{M_{\odot}}$ based on our observational sensitivity."]
  - fitting: Maximum likelihood (Rosolowsky 2005) accounting for mass uncertainties [5.1 GMC Mass Spectrum: "implements a maximum likelihood algorithm to account for uncertainties in both cloud mass and the number distribution"]
  - validation: Truncated fit significantly better than untruncated [5.1 GMC Mass Spectrum: "The truncated power law is a significantly better fit to this cloud population than the standard form"]
- result: Truncated mass spectrum slope gamma = -1.76 ± 0.07 dimensionless [5.1 GMC Mass Spectrum: "we derive a slope of $\gamma = -1.76\pm0.07$ with a truncation mass $M_0 = 9.0\pm2.2\times10^5~\ensuremath{M_{\odot}}$"]
- result: Truncation mass M0 = 9.0e5 ± 2.2e5 Msun [5.1 GMC Mass Spectrum: "$M_0 = 9.0\pm2.2\times10^5~\ensuremath{M_{\odot}}$ and $N_u = 8.3\pm3.0$ clouds"]
- result: Untruncated slope = -1.90 ± 0.05 dimensionless [5.1 GMC Mass Spectrum: "The best-fit straight power law has an exponent of $\gamma=-1.90\pm0.05$"]
- limitation (authors): Missed flux relative to APEX (median 63% recovered), possibly low surface brightness emission [2.5 Comparison to APEX single dish obse…: "This means there may be low surface brightness CO emission we are unable to detect in the ALMA data."]
- limitation (authors): Sampled range of environments limited to inner rising rotation curve [4.2 The GMC distribution across NGC 300: "so the range of environments sampled in this study is somewhat limited"]
- not stated (card): Exact CASA version used for re-imaging (only calibration version 4.3.0 given); Hand-drawn CLEAN polygons per region are not provided; Line-free channel ranges for noise estimation; Exact CPROPS modifications (elliptical beam) code not public (private communication); Per-region alpha_CO values from F14 not tabulated here; uv-taper/robust not needed (natural) but tclean parameters like gridder/nite…

### 2014ApJ...795....5O: Faint Submillimeter Galaxies Revealed by Multifield Deep ALMA Observations: Number Counts, Spatial Clustering, and a Dark Submillimeter Line Emitter (2014; high_z_galaxies; archival_reuse)
- question: What are the 1.2 mm number counts and clustering (galaxy bias) of faint (0.1-1 mJy) SMGs in multifield deep ALMA maps, and what is a serendipitous line emitter (SLE-1)?
- step 1: Extract sources and apply SNR cut
  - method: SExtractor on maps before PB correction; negative maps for spurious fraction; keep peak SNR>4 [3.1 Source Extraction: "A collection of at least six contiguous pixels above the $1.8 \sigma$ noise level are identified as an object."]
  - software: SExtractor
  - parameter: 6 contiguous pixels above 1.8 sigma; final SNR>4.0 [3.1 Source Extraction: "We limit the catalogs to objects whose peak SNR is higher than $4.0$."]
  - validation: Negative-map extraction [3.1 Source Extraction: "The number of spurious sources is obtained by extracting sources from the negative map in the same manner as that for the positive map."]
- step 2: Completeness and flux deboosting
  - method: Inject flux-scaled synthesized beams (SNR 2-9) at random positions, re-extract; deboost by S_out/S_in [3.2: "To obtain the de-boosted flux density, we divide the observed flux density of a detected source by the ratio $S_{\rm out} / S_{\rm in}$"]
  - software: SExtractor
- step 3: Differential number counts
  - method: xi(S)=(1-fc)/(C Aeff), summed in bins of dlogS=0.2, scaled to 1; Poisson errors [4.1: "we calculate a sum of the contributions, $n(S) = \sum \xi(S) / \Delta \log S$ in each logarithmic flux density bin"]
  - assumption: Modified blackbody beta=1.5, Td=35 K at z=2.5 for flux/SFR scaling [1: "spectral index of $\beta_{\rm d} = 1.5$ and dust temperature of $T_{\rm d} = 35$ K"]
  - validation: Compared with Hatsukade+2013, Knudsen+2008, models [4.2: "are broadly consistent with our results within the $1 \sigma$ uncertainties."]
- result: Number of faint SMGs detected (SNR>4) = 11 ± not stated sources [3.1 Source Extraction: "In the $10$ ALMA maps, we detect eleven SMGs with SNRs of $4.1-6.1$."]
- result: Differential count at 0.13 mJy = log n = 4.83 ± +0.37/-0.45 deg^-2 per dlogS [Table 3: "$0.13$ | $4.83^{+0.37}_{-0.45}$"]
- limitation (authors): Small number of fields and unknown redshift distribution of faint SMGs give large bias uncertainties; SLE-1 could be systematic noise [5: "Since the number of the pencil-beam survey fields is small, our estimates on galaxy biases have relatively large uncertainties."]
- not stated (card): CASA version and imaging parameters (weighting, robust, cell, size, cleaning); Continuum channel selection and line-free channels; Flux calibration accuracy; Map 2 reduction details (unpublished); Archival project-to-map mapping and details of archival reductions; Number of artificial sources and trials in completeness simulations; Priors/optimization for chi2 fits; Line search algorithm for the …

## All papers in this technique

- 2013ApJ...768...91H (2013): An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: Source Catalog and Multiplicity
- 2013ApJ...769L..27H (2013): Faint End of 1.3 mm Number Counts Revealed by ALMA
- 2013MNRAS.432....2K (2013): An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: high-resolution 870 μm source counts
- 2014ApJ...788..125S (2014): An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: The Redshift Distribution and Evolution of Submillimeter…
- 2014ApJ...795....5O (2014): Faint Submillimeter Galaxies Revealed by Multifield Deep ALMA Observations: Number Counts, Spatial Clustering, and a Dark Submillimeter Lin…
- 2015A&A...584A..78C (2015): ALMA constraints on the faint millimetre source number counts and their contribution to the cosmic infrared background
- 2015ApJ...806L..25S (2015): ALMA Detected Overdensity of Sub-millimeter Sources Around WISE/NVSS-selected z ~ 2 Dusty Quasars
- 2015ApJ...807..128S (2015): The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Bright-end of the Sub-millimeter Number Counts
- 2015ApJ...811L..19W (2015): Gemini Planet Imager Observations of the AU Microscopii Debris Disk: Asymmetries within One Arcsecond
- 2016A&A...586A..70L (2016): Anatomy of a blazar in the (sub-)millimeter: ALMA observations of PKS 0521-365
- 2016A&A...593A..44L (2016): The 492 GHz emission of Sgr A* constrained by ALMA
- 2016A&A...596A..75S (2016): Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z 3.3
- 2016ApJ...823..160D (2016): An ALMA Search for Substructure, Fragmentation, and Hidden Protostars in Starless Cores in Chamaeleon I
- 2016ApJ...833...67W (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Survey Description
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833...69D (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Luminosity Functions and the Evolution of the Cosmic Density of Molecular Gas
- 2016ApJ...833...72B (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Infrared Excess of UV-Selected z = 2-10 Galaxies as a Function of UV-Continuu…
- 2016ApJ...833..195W (2016): The SXDF-ALMA 2-arcmin<SUP>2</SUP> Deep Survey: Stacking Rest-frame Near-infrared Selected Objects
- 2017A&A...602A..54M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: The extent of the radio-emitting region revealed by 3 GHz imaging with the Ve…
- 2017A&A...604A.115V (2017): The correct estimate of the probability of false detection of the matched filter in weak-signal detection problems . II. Further results wi…
- 2017A&A...605A..42C (2017): Extended ionised and clumpy gas in a normal galaxy at z = 7.1 revealed by ALMA
- 2017A&A...606A..17M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution …
- 2017ApJ...835...98U (2017): ALMA Deep Field in SSA22: Source Catalog and Number Counts
- 2017ApJ...838..114K (2017): ALMA Observations of Starless Core Substructure in Ophiuchus
- 2017ApJ...839...58S (2017): The SCUBA-2 Cosmology Legacy Survey: Multi-wavelength Properties of ALMA-identified Submillimeter Galaxies in UKIDSS UDS
- 2017ApJ...841...43E (2017): ALMA CO Clouds and Young Star Complexes in the Interacting Galaxies IC 2163 and NGC 2207
- 2017ApJ...842L..21N (2017): ALMA Observations of Gas-rich Galaxies in z ∼ 1.6 Galaxy Clusters: Evidence for Higher Gas Fractions in High-density Environments
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...848L..22B (2017): The Electromagnetic Counterpart of the Binary Neutron Star Merger LIGO/Virgo GW170817. VII. Properties of the Host Galaxy and Constraints o…
- 2017ApJ...849..154S (2017): ALMA Pinpoints a Strong Overdensity of U/LIRGs in the Massive Cluster XCS J2215 at z = 1.46
- 2017ApJ...850...83F (2017): Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034…
- 2017MNRAS.465L..89P (2017): A revised host galaxy association for GRB 020819B: a high-redshift dusty starburst, not a low-redshift gas-poor spiral
- 2017MNRAS.466..861D (2017): A deep ALMA image of the Hubble Ultra Deep Field
- 2017MNRAS.469.2235K (2017): Bimodal morphologies of massive galaxies at the core of a protocluster at z = 3.09 and the strong size growth of a brightest cluster galaxy
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2017PASJ...69...45H (2017): ALMA deep field in SSA22: Blindly detected CO emitters and [C II] emitter candidates
- 2018A&A...620A.152F (2018): GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies
- 2018ApJ...853..160C (2018): The Core Mass Function in the Massive Protocluster G286.21+0.17 Revealed by ALMA
- 2018ApJ...856..118H (2018): Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46
- 2018ApJ...857...19F (2018): The ALMA View of GMCs in NGC 300: Physical Properties and Scaling Relations at 10 pc Resolution
- 2018ApJ...858...85P (2018): Forecasting the Contribution of Polarized Extragalactic Radio Sources in CMB Observations
- 2018ApJ...860..161S (2018): An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: Number Counts of Submillimeter Galaxies
- 2018ApJ...861L..18U (2018): Star Formation Efficiency per Free-fall Time in nearby Galaxies
- 2018ApJ...866...48U (2018): A Cool Core Disturbed: Observational Evidence for the Coexistence of Subsonic Sloshing Gas and Stripped Shock-heated Gas around the Core of…
- 2018ApJ...867..153C (2018): No Evidence for Millimeter Continuum Source Overdensities in the Environments of z ≳ 6 Quasars
- 2018ApJ...869...71Z (2018): Constraining the Volume Density of Dusty Star-forming Galaxies through the First 3 mm Number Counts from ALMA
- 2018MNRAS.475.1288S (2018): Identifying the subtle signatures of feedback from distant AGN using ALMA observations and the EAGLE hydrodynamical simulations
- 2018MNRAS.479.3879W (2018): An ALMA survey of CO in submillimetre galaxies: companions, triggering, and the environment in blended sources
- 2018MNRAS.481.1631B (2018): Obscured star formation in bright z ≃ 7 Lyman-break galaxies
- 2018PASJ...70...65U (2018): ALMA deep field in SSA22: Survey design and source catalog of a 20 arcmin<SUP>2</SUP> survey at 1.1 mm
- 2018Sci...362.1034D (2018): The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6
- 2019A&A...632A..38A (2019): A radio census of the massive stellar cluster Westerlund 1
- 2019ApJ...871..109P (2019): Multiband Optical and Near-Infrared Properties of Faint Submillimeter Galaxies with Serendipitous ALMA Detections
- 2019ApJ...874...27T (2019): Detection of the Far-infrared [O III] and Dust Emission in a Galaxy at Redshift 8.312: Early Metal Enrichment in the Heart of the Reionizat…
- 2019ApJ...879...54L (2019): Revealing the Stellar Mass and Dust Distributions of Submillimeter Galaxies at Redshift 2
- 2019ApJ...881...10B (2019): A Precision Measurement of the Mass of the Black Hole in NGC 3258 from High-resolution ALMA Observations of Its Circumnuclear Disk
- 2019ApJ...882..136A (2019): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Evolution of the Molecular Gas in CO-selected Galaxies
- 2019ApJ...882..138D (2019): The ALMA Spectroscopic Survey in the HUDF: CO Luminosity Functions and the Molecular Gas Content of Galaxies through Cosmic History
- 2019ApJ...884..112T (2019): An ALMA/HST Study of Millimeter Dust Emission and Star Clusters
- 2019ApJ...887...37U (2019): The ALMA Spectroscopic Survey in the HUDF: Constraining Cumulative CO Emission at 1 ≲ z ≲ 4 with Power Spectrum Analysis of ASPECS LP Data …
- 2019ApJ...887...88E (2019): Star Formation Efficiencies at Giant Molecular Cloud Scales in the Molecular Disk of the Elliptical Galaxy NGC 5128 (Centaurus A)
- 2019ApJ...887..107F (2019): First Identification of 10 kpc [C II] 158 μm Halos around Star-forming Galaxies at z = 5-7
- 2019MNRAS.483.1624B (2019): An ALMA archival study of the clump mass function in the Large Magellanic Cloud
- 2019MNRAS.485.1188B (2019): ALMA photometry of extragalactic radio sources
- 2019MNRAS.485.1595P (2019): Multiphase circumgalactic medium probed with MUSE and ALMA
- 2019MNRAS.486.4304S (2019): Revealing dust-obscured star formation in CLJ1449+0856, a cluster at z = 2
- 2019MNRAS.487.4648S (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: source catalogue and properties
- 2020A&A...635A...2S (2020): Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA
- 2020A&A...636A...5R (2020): SYMBA: An end-to-end VLBI synthetic data generation pipeline. Simulating Event Horizon Telescope observations of M 87
- 2020A&A...640A..27V (2020): Protoplanetary disk masses in NGC 2024: Evidence for two populations
- 2020A&A...643A...2B (2020): The ALPINE-ALMA [CII] survey: Data processing, catalogs, and statistical source properties
- 2020A&A...643A..53F (2020): GOODS-ALMA: Using IRAC and VLA to probe fainter millimeter galaxies
- 2020ApJ...889..137M (2020): Balmer Break Galaxy Candidates at z ∼ 6: A Potential View on the Star Formation Activity at z ≳ 14
- 2020ApJ...891...64F (2020): Truth or Delusion? A Possible Gravitational Lensing Interpretation of the Ultraluminous Quasar SDSS J010013.02+280225.8 at z = 6.30
- 2020ApJ...892...66M (2020): The ALMA Spectroscopic Survey in the HUDF: The Cosmic Dust and Gas Mass Densities in Galaxies up to z ∼ 3
- 2020ApJ...895...84Y (2020): Super-resolution Imaging of the Protoplanetary Disk HD 142527 Using Sparse Modeling
- 2020ApJ...895..126H (2020): The Evolution of Dust Disk Sizes from a Homogeneous Analysis of 1-10 Myr old Stars
- 2020ApJ...897...91G (2020): The ALMA Spectroscopic Survey in the HUDF: Deep 1.2 mm Continuum Number Counts
- 2020ApJ...901...79A (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies
- 2020ApJ...902..110D (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Multiband Constraints on Line-luminosity Functions and the Cosmic Density of …
- 2020ApJ...904..130V (2020): Kiloparsec-scale ALMA Imaging of [C II] and Dust Continuum Emission of 27 Quasar Host Galaxies at z ∼ 6
- 2020ApJ...905..147Y (2020): The ALPINE-ALMA [C II] Survey: [C II] 158 μm Emission Line Luminosity Functions at z ∼ 4-6
- 2020ApJS..247...61F (2020): The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements
- 2020ApJS..251...14H (2020): CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone
- 2020MNRAS.495.2332K (2020): ALMACAL VII: first interferometric number counts at 650 μm
- 2021A&A...645A.120F (2021): ALMA and MUSE observations reveal a quiescent multi-phase circumgalactic medium around the z ≃ 3.6 radio galaxy 4C 19.71
- 2021A&A...646A..76L (2021): The ALPINE-ALMA [C II] survey. Luminosity function of serendipitous [C II] line emitters at z ∼ 5
- 2021ApJ...908..163M (2021): Extremely Low Molecular Gas Content in the Vicinity of a Red Nugget Galaxy at z = 1.91
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024ApJ...964...18C (2024): Resolved Measurements of the CO-to-H<SUB>2</SUB> Conversion Factor in 37 Nearby Galaxies
- 2024ApJ...967...27R (2024): Exploring the Mpc Environment of the Quasar ULAS J1342+0928 at z = 7.54
- 2025ApJ...992..211N (2025): Revisiting the Supermassive Black Hole Mass of NGC 7052 Using High Spatial Resolution Molecular Gas Observed with ALMA
- 2025ApJ...995..219F (2025): PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon
- 2025ApJS..278...45F (2025): DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey
- 2025NatAs...9.1553F (2025): Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn
