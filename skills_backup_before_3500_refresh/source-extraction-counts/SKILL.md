---
name: alma-source-extraction-counts
description: "Find sources blindly in ALMA continuum maps and turn them into a trustworthy catalog and number counts: noise maps and S/N thresholds, peak finders (SExtractor, BLOBCAT, LineSeeker, PyBDSF), fidelity/purity from the inverted map, completeness and flux boosting from injected sources, effective area, differential and cumulative counts with double power-law fits, and conversion of counts between wavelengths. Use when a task asks for a blind continuum catalog of an ALMA map or mosaic, a false-detection rate or detection threshold, completeness or deboosting corrections, (sub)mm number counts, the resolved fraction of the extragalactic background, or a source overdensity test around a target. Built from 95 ALMA papers (2013-2025), about 70 of them on-topic."
---

# Blind source extraction, completeness and number counts

Finds sources in an ALMA map without a prior position, decides which peaks are real, and corrects the
catalog for what was missed and for flux boosting so that counts (sources per flux per area) can be
computed. The two mistakes that matter most: (1) choosing a detection threshold without a validated
false-detection rate for the exact extraction (the inverted map is the most common calibration;
blank-field simulations, independent-beam estimates and per-peak false-alarm probabilities are also
used), since at S/N 3.5-4.5 a few to tens of percent of peaks are noise; and (2) quoting counts without
the completeness, flux-boosting and effective-area corrections, which all change fastest exactly at the
faint end where new ALMA counts are claimed.

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
- Method: extract on the map NOT corrected for the primary beam and correct fluxes for the primary beam
  afterwards (2018ApJ...869...71Z, 2015ApJ...807..128S, 2016ApJ...833...68A, 2014ApJ...795....5O; 4
  papers, my count). In a single pointing this map has roughly flat noise, but mosaics, heterogeneous
  archival coverage and imaging artifacts break that, so build a local noise map for the actual detection
  product and check it (local rms per source, 2016ApJ...833...68A; sensitivity-limited regions,
  2025ApJS..278...45F). Treat flat noise as a checked special case, not an assumption.
- Noise estimates seen: "the 68th percentile of the distribution of pixel values" (2018ApJ...869...71Z;
  the pack does not say whether of signed or absolute values, and for signed zero-mean Gaussian pixels
  the 68th percentile is about 0.47 sigma, so do not copy it literally); a local rms per source
  (2016ApJ...833...68A); 50 random 0.5'' apertures inside the primary beam (2019MNRAS.487.4648S); random
  blank-sky apertures (2014ApJ...788..125S). General practice alternative: (q84 - q16)/2 or 1.4826 x MAD
  of pixel values after masking sources.
- Deep surveys run on both a natural-weight and a tapered map, with separate thresholds, to catch
  extended sources (2020ApJ...897...91G, 2025ApJS..278...45F). See step 3 for merging the two lists.
- Set the search area and keep the paper's own quantity: inside the primary-beam FWHM contour, i.e. a
  radius of FWHM/2 (2015ApJ...807..128S, "within the FWHM primary beam"); a stated "radius 1.3 x primary
  beam FWHM" (2018ApJ...869...71Z; check whether radius or diameter is meant before copying); PB
  response >= 0.1 (2020ApJ...897...91G); down to 20% relative sensitivity (2025ApJS..278...45F, a
  sensitivity level, not necessarily the PB response). Write the search mask out explicitly.
- Software: CASA tclean products; mask bright targeted sources when the field was pointed at them (masking
  alone does not remove targeting bias; see Pitfalls).

### 2. Find peaks
- Goal: a candidate list deeper than the final cut, so fidelity and completeness can be modelled.
- Method: two thresholds, a low "extraction/flood" level and a higher peak cut:
  - SExtractor, 6 contiguous pixels above 1.8 sigma, keep peak S/N > 4.0 (2014ApJ...795....5O);
    min area 5 pixels, down to 2.5 sigma local, main sample > 3.5 sigma (2016ApJ...833...68A);
    > 3 sigma peaks, 4 sigma final (2015ApJ...807..128S); peaks > 2 sigma then S/N cut from the
    positive/negative comparison (2025ApJS..278...45F).
  - BLOBCAT flood fill with sigma_p = 4.8 and sigma_f = 2.7, chosen by scanning sigma_p 4-6 and
    sigma_f 2.5-4 for purity >= 0.8 (2018A&A...620A.152F). A non-ALMA methodological example of the
    same idea: SEAC flood fill with seed 5 sigma, flood 3 sigma and local rms, run on ATCA radio maps of
    a Galactic cluster (2019A&A...632A..38A); it is not demonstrated ALMA extraction practice.
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
- The inverted map only measures false positives if the noise is symmetric and there is no genuine
  negative signal. 2016ApJ...833...67W states this assumption explicitly ("negative candidates are all
  noise peaks; no absorption expected"). Check it: negative sidelobes of bright sources, absorption
  against a bright continuum source, and non-Gaussian artifacts all bias N_neg. Mask or model them first.
- Choose the threshold from it: 4.8 (natural) and 4.2 (tapered) for deep maps, 5.0/4.4 for wide maps
  (2025ApJS..278...45F); 50% fidelity at S/N 4.3 natural and 3.3 tapered (2020ApJ...897...91G,
  2020ApJ...901...79A); 98% purity at S/N >= 4.3 (2018ApJ...860..161S).
- Merging natural and tapered (or Wide and Deep) lists: the cards rarely state the merge rule.
  2025ApJS..278...45F reports 65 Wide sources plus only 4 additional Deep sources, so overlapping
  detections were not counted twice. Recommendation: match the lists within about one beam, keep one
  entry per source with a stated rule for which flux is adopted, and measure purity and completeness on
  the whole combined procedure (run the inverted maps and the injections through both detections and the
  merge), not on each list separately.
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
  `references/parameters.md`, which keeps sources per realization, realizations and totals apart.
  Typical: point sources or beam-shaped sources at random positions (2014ApJ...795....5O,
  2018ApJ...869...71Z), 20,000 point sources in total into a uv jackknife noise image
  (2020ApJ...897...91G; injected flux range not stated in the pack), 2 x 10^4 simulated maps with a
  power-law flux distribution of index -2 and sizes 0-0.5'' (2015ApJ...807..128S), 300 sources per run
  x 100 runs = 30,000 injections per flux value (2018A&A...620A.152F).
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
- Goal: counts with stated units and honest errors. Definitions (general practice): differential
  dN/dS in mJy^-1 deg^-2 (divide the summed weights by the linear bin width Delta S); per logarithmic
  interval dN/dlog10 S in deg^-2 dex^-1 (divide by Delta log10 S); cumulative N(>S) in deg^-2 (sum all
  weights above S, no bin-width division). 2014ApJ...795....5O uses the second form explicitly,
  n(S) = sum xi(S) / Delta log S, and tabulates log n per dlogS.
- Per-source weight: keep completeness and area bookkeeping separate so completeness is not counted
  twice. Two forms appear:
  - (1 - f_c) / (C(S) A_geom), with C(S) the completeness and A_geom the geometric area in which a source
    of flux S passes the S/N cut given the noise map (2014ApJ...795....5O xi(S) = (1 - f_c)/(C A_eff);
    2018ApJ...869...71Z (1 - f_cont)/(zeta A_eff)); or P_j / C_j / A (2016ApJ...833...68A).
  - (1 - f_c) / A_survey(S), with A_survey = sum_i C_i A_i already completeness-weighted
    (2015A&A...584A..78C). Do not also divide by C(S) here.
  2013MNRAS.432....2K weights each source by p = 2 - f_recovered - f_spurious and scales area as
  (88/126) x 0.35 deg^2.
- Bins: dlogS = 0.2 (2014ApJ...795....5O, 2015A&A...584A..78C); log S = 0.25 differential and 0.1
  cumulative (2020ApJ...897...91G). With few sources, use cumulative counts only (2016ApJ...833...68A).
- Errors: Poisson with Gehrels small-number intervals (2015A&A...584A..78C; 2025ApJS..278...45F uses
  Gehrels errors for its infrared luminosity function, not for counts) plus flux-error resampling, 1000
  draws (2013MNRAS.432....2K, 2020ApJ...897...91G); cosmic variance with the Moster et al. 2011 tool
  (2015A&A...584A..78C) or stated as omitted (2018A&A...620A.152F). Correlated flux-calibration error
  shifts all fluxes together: propagate it into fluxes, count bins and fitted parameters, or quantify it
  separately. 2017ApJ...835...98U states a 20% absolute flux uncertainty that is "not included" in its
  analysis.
- Robustness: recompute with tighter PB cuts (PB >= 0.5 and >= 0.9; faint end unchanged,
  2020ApJ...897...91G); drop possibly lensed sources (< 1 sigma change, 2015ApJ...807..128S).

### 7. Fit and compare the counts
- Model: double power law (DPL). Conventions differ, so record each paper's form and units and never
  move parameters between them:
  - differential DPL with N0 in mJy^-1 deg^-2: N0 = (4.4 +/- 0.6) x 10^4 mJy^-1 deg^-2, S0 = 0.10 mJy
    (2020ApJ...897...91G);
  - DPL with N0 in deg^-2: N0 = 390 deg^-2, S0 = 8.4 mJy (2015ApJ...807..128S; the pack does not give the
    written form);
  - written as N(>S) = N'/S' [ (S/S')^alpha + (S/S')^beta ]^-1 with N' in deg^-2 (2017ApJ...835...98U,
    2018PASJ...70...65U, from the pack aggregate; the N'/S' prefactor has units deg^-2 mJy^-1, which is
    the differential normalization, so check the paper before treating it as cumulative);
  - a cumulative DPL fitted at 3 mm, with a Schechter form tried and rejected (2018ApJ...869...71Z).
  To get cumulative counts from a differential model, integrate it above S; do not reuse differential
  parameters in a cumulative formula.
- Fitters: chi-square Levenberg-Marquardt (2018ApJ...869...71Z); least squares with Trust Region
  Reflective (2018A&A...620A.152F); P(D) forward modelling of the pixel histogram with a Cash statistic
  on a parameter grid, 1000 realizations per grid point (2020ApJ...897...91G). The cards often do not
  state the fit method (2015ApJ...807..128S).
- Convert other surveys to your wavelength before comparing: modified blackbody with beta = 1.5,
  Td = 35 K at z = 2.5 (2014ApJ...795....5O, 2015ApJ...806L..25S, 2017ApJ...835...98U,
  2018PASJ...70...65U; 4 papers, the most common choice); S proportional to nu^(2+beta) with beta = 1.8
  (2018ApJ...869...71Z); ALESS composite SED at z = 2.5, used to convert faint 1.2 and 1.3 mm counts to
  870 um with S870 = 2.4 x S1.2mm and S870 = 3.1 x S1.3mm (divide for the reverse direction;
  2015ApJ...807..128S); S870/S850 = 0.95 (2018ApJ...860..161S).
- The nu^(2+beta) scaling is a Rayleigh-Jeans, optically thin approximation (general practice). It fails
  when the observed frequency approaches the dust peak in the rest frame (high z, warm dust, short
  wavelengths) or the dust is optically thick; 2018ApJ...869...71Z itself assumes optically thick SEDs at
  rest-frame lambda < 100 um in its luminosity-function step. Check rest-frame frequencies and the
  assumed Td and beta, and use a full modified blackbody or template SED with a redshift distribution
  where the approximation fails.
- EBL: integrate the corrected counts and compare with the Planck background (2016ApJ...833...68A:
  55% from detections, 80% adding bright end and stacking; 2018A&A...620A.152F: 13.5% at 0.8 mJy). State
  the integration limits, keep the measured part and any extrapolated or stacked contribution separate,
  and propagate the background's own uncertainty: 2015A&A...584A..78C says CIB uncertainties mean "we are
  not able to exactly determine the fraction of CIB resolved."

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Final S/N cut, blind continuum | 4-5 | 3.5 to 5.5 | about 16 (my count) | 2013MNRAS.432....2K (3.5), 2015ApJ...807..128S (4), 2025ApJS..278...45F (4.8), 2018ApJ...869...71Z (5), 2018MNRAS.479.3879W (5.5) |
| Cut at prior (counterpart) positions | 1 sigma or so below blind | 3.5 to 5.0 | 2 | 2018MNRAS.479.3879W, 2020A&A...643A..53F |
| Low extraction / flood level | 2-3 sigma | 1.8 to 3 | 8 (my count) | 2014ApJ...795....5O (1.8), 2020ApJ...897...91G (2), 2016ApJ...833...68A (2.5), 2018A&A...620A.152F (2.7) |
| Minimum pixels | 5-6 | 2 to 6 | 5 (my count) | 2016ApJ...833...68A (5), 2014ApJ...795....5O (6), 2018ApJ...867..153C (2 above 5 sigma) |
| Per-source fidelity accepted | >= 0.5 | 0.5 | 2 (my count) | 2020ApJ...901...79A (0.5), 2020ApJ...897...91G (0.5) |
| Catalog purity above the cut | >= 0.8 required, often reported > 0.97 | >= 0.8 to 98% | 3 (my count) | 2018A&A...620A.152F (>= 0.8), 2025ApJS..278...45F (> 0.97), 2018ApJ...860..161S (98% at S/N >= 4.3) |
| Search area (keep each paper's quantity) | inside PB FWHM contour (radius FWHM/2) | PB FWHM contour; "radius 1.3 x PB FWHM"; PB >= 0.1; 20% relative sensitivity | 4 | 2015ApJ...807..128S, 2018ApJ...869...71Z, 2020ApJ...897...91G (PB), 2025ApJS..278...45F (sensitivity) |
| Total injected sources | thousands | 100 to 20,000 per catalog; 30,000 per flux value | 5 continuum papers state a total or give both factors (my count; plus 2 Galactic) | 2016ApJ...833...68A (100), 2013MNRAS.432....2K (7,400), 2020ApJ...897...91G (20,000), 2018A&A...620A.152F (300 x 100 per flux) |
| Simulated maps / realizations | 100 to 10^4 per map or bin | 100 per S/N bin to 2 x 10^4 maps | 4 (my count) | 2018ApJ...869...71Z (100 per S/N bin), 2015A&A...584A..78C (1000 per map; 10^4 for boosting), 2015ApJ...807..128S (2 x 10^4 maps), 2018A&A...620A.152F (100 runs per flux) |
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
| casa / casa imfit / casa simobserve / casa uvmodelfit / tclean / casa tclean (aggregate labels) | 11 / 4 / 2 / 2 / 1 / 1 | generic CASA steps (imaging, extraction on S/N maps in 2018ApJ...869...71Z), simulated observations for completeness (2020ApJS..251...14H, 2015A&A...584A..78C), fluxes and sizes |
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

- Threshold without a validated false-positive test (inverted map or one of the alternatives in step 3,
  with its assumptions checked). Contamination is 2% at 4 sigma in one catalog
  (2015ApJ...807..128S) but low-rms fields can have a high spurious fraction (2015ApJ...806L..25S), and one
  line-search paper treats negative-peak fidelity as an upper limit (2020ApJ...902..110D). Even at
  purity > 0.97, 1-2 of 69 sources may be spurious (2025ApJS..278...45F).
- Completeness tested only for point or beam-sized sources overestimates the recovered fraction
  (2019MNRAS.483.1624B, 2020ApJS..251...14H); fainter supplementary sources are larger (median 0.32'' vs
  0.18'', 2020A&A...643A..53F).
- Peak fluxes adopted for unresolved sources may be low by about 20% (2020A&A...643A..53F, which uses
  peak flux below theta_min); resolved flux can be missed in high-resolution maps (2016ApJ...833...68A).
- Targeted fields are not blank fields: "Below the LESS flux limit the source counts derived from our
  ALMA maps must be considered biased" because pointings were centred on bright sources
  (2013MNRAS.432....2K; also 2013ApJ...769L..27H). Masking the target removes the target itself
  (2017A&A...605A..42C excluded 2 arcsec around a serendipitous source) but does not remove this
  selection bias. Either model the targeting selection function or restrict the claimed counts to the
  regime where the selection is demonstrably valid (2015ApJ...807..128S built counts only at
  S870 > 7.5 mJy).
- Overdensity tests measure an angular excess, not physical association: 2018ApJ...867..153C notes its
  sample is not formally complete, has no redshifts for the continuum sources, and is limited by small
  field, cosmic variance and foreground sources; 2018PASJ...70...65U says SMG redshifts are mostly unknown
  and protocluster association unconfirmed. Compare against a null model passed through the same spatial
  coverage, noise map and extraction (2018ApJ...867..153C injected unresolved, unclustered sources drawn
  from blank-field counts), and say what redshift information exists.
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
- Injection-recovery for completeness and boosting, with input vs recovered flux agreeing within
  individual source uncertainties (2016ApJ...833...68A). 2020A&A...643A..53F also compared recovered to
  injected flux to quantify flux boosting, a bias check rather than an agreement claim.
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
- Are Poisson (Gehrels), flux-resampling and cosmic-variance terms all in the error bars, and is the
  correlated absolute flux-scale uncertainty propagated into fluxes, bins and fit parameters rather than
  only quoted (2017ApJ...835...98U left its 20% out)?
- Is the negative-map assumption (symmetric noise, no real negative signal) checked, and were natural
  and tapered lists merged before purity and completeness were measured?
- Are the count units (dN/dS, dN/dlogS or N(>S)) and the DPL convention stated, with completeness
  applied once (either in C(S) or in a completeness-weighted area, not both)?
- For counts compared across wavelengths, is the conversion SED stated and varied, and is the
  Rayleigh-Jeans approximation valid at the rest-frame frequencies involved?

## Source cards

Full list: `references/sources.md` (95 papers). Most informative for this technique:

- 2020ApJ...897...91G: LineSeeker on continuum, fidelity 50% at S/N 4.3, 20000 injections, P(D) fit.
- 2016ApJ...833...68A: SExtractor setup, erf fidelity and completeness, cumulative counts, EBL fraction.
- 2018A&A...620A.152F: BLOBCAT threshold scan, extended-source injections, DPL and Schechter fits.
- 2015ApJ...807..128S: aperture fluxes, 2 x 10^4 simulated maps, spline deboosting, bright-end counts.
- 2013MNRAS.432....2K: MCMC extraction, 7400 injections, 1.6% spurious at 3.5 sigma, resampled counts.
- 2015A&A...584A..78C: archival multi-field counts, boosting 1.09 at S/N 3.5, cosmic-variance errors.
- 2014ApJ...795....5O: SExtractor 1.8 sigma / 6 pixel setup, (1 - f_c)/(C A_eff) counts per dlogS.
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
- 2018ApJ...867..153C: overdensity test with injected unclustered sources, and its stated limits.
- 2018PASJ...70...65U: protocluster counts, DPL convention, unconfirmed association.
- 2019MNRAS.483.1624B: completeness logistic fit, beam-sized-only caveat (Galactic).
