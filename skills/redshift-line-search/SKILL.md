---
name: alma-redshift-line-search
description: "Determine spectroscopic redshifts from ALMA line data and run blind line searches in cubes: targeted [CII]/[OIII]/CO confirmation around an optical or Lya prior, serendipitous and companion searches, spectral scans of sources with no redshift, fidelity from negative peaks, completeness from injected lines, line identification and robust-redshift tests, Gaussian redshift fits, and upper limits for non-detections. Use when a task asks for a redshift from an ALMA spectrum, a search for line emitters or companions in a cube, a [CII]/[OIII] detection at high z, or a line luminosity function from a blind search. Built from 368 ALMA papers in the evidence pack (2012-2026), many of them off-topic regex matches on [CII]/[OIII]."
---

# Redshift determination and blind line searches

Measures where a line sits in frequency (and so z = nu_rest/nu_obs - 1), whether a peak in a cube is real,
and what fraction of real lines a search recovers. The two mistakes that matter most: (1) calling a single
peak a redshift when only one line is seen (a lone 3 mm line fits several CO transitions, and an "[CII]
companion" can be a low-z CO interloper), and (2) quoting a blind-search candidate without a fidelity
estimate from the negative (inverted) cube, since peaks at S/N ~5 are often noise.

Counts come from the pack (`packs/redshift-line-search.md`, 368 papers): its aggregates, or my own count of pack
lines where marked "(my count)". The regex matches any [CII]/[OIII] mention, so many papers are off-topic
(nearby Seyferts, Galactic regions, kinematics, e.g. 2024A&A...686A..46E, 2019A&A...632A.106L). I skip those
as examples but built no exclusion list, so aggregate counts are unfiltered. Table numbers are examples from
specific papers, not a consensus, unless the row says otherwise.

## When to use

- A target has a prior redshift (Lya, rest-UV, photo-z, quasar Mg II) and you need the systemic redshift from
  [CII] 158 um, [OIII] 88 um or CO: the most common situation in the pack (my reading; z ~ 4-8 galaxies and
  quasars, e.g. 2015ApJ...807..180W, 2020ApJ...897L..14Y, 2020MNRAS.493.4294B, 2025A&A...694A.171M).
- You must search a cube for line emitters with no prior position: deep fields (2016ApJ...833...67W,
  2019ApJ...882..139G), calibrator fields (2023MNRAS.519...34H), serendipitous emitters in targeted pointings
  (2021A&A...646A..76L, 2023Natur.617..261K), or quasar companions (2020ApJ...904..130V, 2025A&A...694A.171M).
- A dusty source has no redshift and you scan bands for CO/[CI] lines (2022MNRAS.511.3017U, 2024A&A...687A.288G);
  2022MNRAS.515..678B gives a test for when such redshifts are robust.
- You need a line upper limit at a known redshift (2014ApJ...792...34O, 2021A&A...646A..26B), the Lya-to-systemic
  offset (2015ApJ...807..180W, 2016Sci...352.1559I), or a line LF from blind detections (2021A&A...646A..76L,
  2025PASJ...77.1163H).

## When not to use

- Crowded line-rich Galactic or protostellar spectra (hot cores, COMs, line surveys): use `line-identification`.
- Continuum source finding, number counts and continuum completeness: use `source-extraction-counts`. Only the
  line-detection part (3D peaks, fidelity in channels) lives here.
- Stacking spectra for faint wings or mean signals: `stacking` (e.g. 2019A&A...630A..59B, 2019A&A...631A..78S).
- Kinematics, dynamical masses, outflows once detected: `galaxy-3d-kinematics`, `outflow-energetics`. Line-to-H2:
  `gas-mass-co-conversion`. PDR/CLOUDY line-ratio modelling (CLOUDY is third in the software aggregate) is elsewhere.
- Intervening absorbers: `absorption-lines` (2019MNRAS.490.1220K is in this pack but is an absorber search).
- Line-free channel choice and continuum removal details: `continuum-subtraction`.

## Steps

### 1. Fix the frequency setup and what lines can fall in it
- Method (general practice): nu_obs = nu_rest/(1+z). For a targeted line, center an SPW on the prior and check
  the velocity range against the prior's uncertainty. For a blind scan, list every CO, [CI], [CII], [OIII] line
  in band for each z. 2022MNRAS.515..678B plots bandwidths and line frequencies against z (its card names the
  tool redshift-search-graphs) and picks six tunings (3 in Band 3, 3 in Band 4) to maximize robust redshifts.
- Coverage loses lines: [C II] was missed in most of one sample "due to redshift uncertainty and gaps in spectral
  coverage" (2020ApJ...892..119M); the line of source Lya-2 was truncated by coverage, leaving its luminosity and
  redshift uncertain (2013ApJ...763..120C); a line at the bandwidth edge left derived quantities uncertain
  (2025A&A...694A.171M); an SPW was lost to the atmosphere (2019PASJ...71..109H) and marginal [C II] features were
  hit by an ozone line (2016Sci...352.1559I). One stack dropped channels with transmission < 0.5 (2019A&A...630A..59B).
- Record the spectral frame (TOPO, LSRK, BARY) and velocity convention of every cube and external spectrum
  (outframe = BARY, veltype = optical in 2023ApJ...945...69R; LSRK channels in 2020ApJ...904..131N). Put all
  spectra in one frame before comparing centroids: 2015ApJ...807..180W converted to LSR before comparing Lya with
  [CII]; 2016Sci...352.1559I applied a heliocentric correction to Lya. Define the sign of any offset (here
  positive = Lya redward of systemic, as in +430 km/s for CLM 1, 2015ApJ...807..180W).

### 2. Calibrate and image the cube
- Method: pipeline calibration in CASA, continuum subtraction (`uvcontsub` in the uv plane: 2020ApJ...904..130V,
  2025A&A...694A.171M; fitorder 1 excluding 2.5 x FWHM around the line, 2020ApJ...904..131N), `tclean` cubes.
  Check the measured rms against the theoretical noise (2021A&A...646A..26B).
- Weighting: natural for detection (2021A&A...646A..26B, 2020MNRAS.493.4294B, 2020MNRAS.499.5136C); robust 0.5
  when resolution matters (2020ApJ...904..130V, 2025NatAs...9.1553F); robust 2 for shallow fields
  (2025ApJ...987L..37W: 0.5 for 1.7 h, 2.0 for 0.8 h).
- Extended emission: a point-source finder misses it, so 2020MNRAS.499.5136C searched ten uv-tapered cubes
  (0.2" to 2" in 0.2" steps); 2021A&A...646A..26B tapered [C II] to 0.5" since [C II] may be 2-3 times the UV size.
- Channels: see the table; convert with dv ~ c dnu/nu_obs (general practice) and state both. Hanning smoothing
  correlates channels (15.626 MHz smoothed to ~28 km/s, 2021Sci...371..713L).
- Software: CASA is named in 155 matched steps (pack aggregate; tclean 32, uvcontsub 10), far more than anything else.

### 3. Targeted search at the prior position and velocity
- Method: extract a spectrum at the prior (or continuum) position, look within a velocity window of the prior,
  collapse a moment-0 map, re-extract. Windows: abs(v) < 500 km/s of Lya inside the primary beam, whose FWHM is
  16" (i.e. within an 8" half-power radius; 2017A&A...605A..42C); within 1000 km/s of [OIII] and 5" of the UV
  (2020MNRAS.499.5136C); -2000 to +700 km/s ([OIII]) and -2900 to +1300 km/s ([C II]), pixels > 3 x rms within 1"
  (2021A&A...646A..26B). Make the window cover the prior's redshift uncertainty.
- Moment-0 widths: 1.2 x FWHM (2020ApJ...904..130V, 2024ApJ...977L..46B), +/-1.4 sigma_line with a correction for
  the ~83% captured (2024ApJ...968....9W; factor ~1.20 in 2025A&A...694A.171M), or the highest-S/N range
  (2020MNRAS.493.4294B).
- Picking the window that maximizes S/N on a marginal line biases S/N upward (general practice).
  2020MNRAS.493.4294B checked its window by eye; 2021A&A...646A..26B rejected features because negative pixels of
  the same significance existed in the same maps.

### 4. Blind search for emitters in the full cube
- Matched filtering in frequency: run several kernel widths spanning the expected line widths and find peaks,
  e.g. 3, 5, 7, 9 channels with daofind (findclumps, 2016ApJ...833...67W), 3-19 channels (2025A&A...694A.171M),
  50-500 km/s with peak S/N 3.6 (2020MNRAS.499.5136C), ~90-550 km/s with seed S/N 3 in 118 cubes
  (2021A&A...646A..76L), smoothing up to 400 MHz with S/N > 3 (2020ApJ...904..130V). Other finders: LineSeeker,
  FindClump and MF3D (2019ApJ...882..139G); DBSCAN on connected voxels (2025A&A...696A..33P).
- Seed-and-grow: voxels > 3 sigma in one 15 MHz channel plus four neighbours > 2 sigma (~50 km/s minimum width),
  Gaussian fit, moment 0 over the FWHM, keep S/N > 5 inside the primary-beam FWHM with the target masked
  (2020ApJ...889...98M). Calibrator fields: 3 sigma voxels, then peak S/N > 4, reliability > 0.3, PB gain >= 0.3
  and width <= 1/4 of the cube (2023MNRAS.519...34H).
- Merge duplicates: one line found by several kernels or adjacent peaks is one candidate (2016ApJ...833...67W
  removed duplicates across kernels). Merge scales: one beam and 500 km/s (2020MNRAS.499.5136C), 1" and 280 MHz
  (2023Natur.617..261K), 2" (2025A&A...694A.171M). Keep one entry per (x, y, nu) group, record the kernel with
  the highest S/N, and use that same retained S/N in the fidelity (step 5) and completeness (step 6) curves.
- Run the identical search on the inverted cube (negative peaks) for step 5.
- Restrict the area and say whether a number is a radius or a diameter: sqrt(2) x primary-beam radius at 3 mm
  (53" at 84 GHz, 39" at 115 GHz) and a 30.9" radius at 1 mm (2016ApJ...833...67W); PB response >= 50%
  (2025A&A...696A..33P); "within the FWHM of the primary beam" (2020ApJ...889...98M), which as a region means a
  radius of FWHM/2, the half-power contour (general practice). Using the FWHM as a radius quadruples the area.
  Mask bright continuum sources and the main target.
- Software: findclumps (12 matched steps; not released per 2016ApJ...833...67W's card), interferopy (4; used
  with findclumps in 2025A&A...694A.171M), LineSeeker (4), Python + SpectralCube (2020ApJ...889...98M).

### 5. Fidelity (purity) from negative peaks
- Method: fidelity = 1 - N_neg/N_pos vs S/N and kernel width, assuming negative peaks are pure noise (no
  absorption expected) (2016ApJ...833...67W, 2021A&A...646A..76L, 2020ApJ...904..130V, 2025A&A...694A.171M).
  2016ApJ...833...67W fit an error function (C_3mm = 5.1, sigma_3mm = 0.4; C_1mm = 5.0, sigma_1mm = 0.8) and
  called it "not physically motivated".
- Single pointings have few negative peaks: 2025A&A...694A.171M pooled the catalogs of all its quasar fields.
  Pool only fields of similar depth and channel width.
- Cuts: >= 60% (2016ApJ...833...67W), >= 0.8 (2020ApJ...904..130V), > 85% at S/N >= 6.30 (2021A&A...646A..76L),
  > 0.9 (2019ApJ...882..136A; 2025A&A...694A.171M with SNR > 4); or a cut at the brightest negative peak
  (S/N 6.2, 2020MNRAS.495.3124H).
- Two-line sources: joint spurious probability = product of the two lines' probabilities, with N_eff for the
  second line = the number of CO transitions possible (2024A&A...687A.288G).
- Then vet visually: channel maps on and off the line (2020ApJ...904..130V).

### 6. Completeness from injected lines
- Inject Gaussian lines with random position, frequency, peak flux and width into the data (or noise) cubes and
  rerun the identical search: 2500 lines, 50-500 km/s, peaks 0.22-1.00 mJy at 3 mm (2016ApJ...833...67W);
  ~50000 lines in four primary-beam rings (2021A&A...646A..76L); peak S/N 2.0-7.0 x FWHM 36-396 km/s at 84
  positions with 100 repeats, 1,016,400 sources (2025PASJ...77.1163H).
- Report completeness vs peak flux and width; 2016ApJ...833...67W reached > 50% at peak > 0.45 mJy and
  width > 100 km/s at 3 mm.

### 7. Identify the line and the redshift
- Use a second line, an optical/NIR spec-z, or counterpart arguments. 2016ApJ...833...67W used multiple CO lines
  and spec-z, and assumed band 3 candidates with no optical/NIR counterpart are at z > 2. Single lines cannot give
  definitive redshifts (2020A&A...642A.155Z); [C II] emitters without [O III] or dust counterparts could be other
  lines at other redshifts (2025A&A...696A..88W).
- Spectral scans: call z robust only when every alternative is excluded. 2022MNRAS.515..678B excludes adjacent
  CO solutions within 5 sigma and needs S/N > 8 on the detected line to exclude alternatives by non-detection of
  other expected lines (assuming a thermalized CO SLED); 2022MNRAS.511.3017U uses the similar integrated fluxes
  of adjacent CO lines to exclude solutions for strong single lines.
- Association is separate from the search window: 2020ApJ...904..130V searched whole cubes, then conservatively
  assumed already detected candidates with abs(dv) < 2000 km/s are associated with the quasar;
  2025A&A...694A.171M used abs(dv) < 1000 km/s and found 2000 km/s gave the same result. Do not confuse this with
  the abs(v) < 500 km/s window used to search around a Lya prior (2017A&A...605A..42C). Pair or merger labels add
  a projected distance (<= 500 km/s and ~2.1 kpc, 2021A&A...653A.111R; < 3" and < 300 km/s, 2025A&A...693A.237I).
- With no redshift at all, some papers assume one for derived quantities (z = 2, range 1-3, 2017A&A...597A..41G);
  flag that as an assumption.

### 8. Fit the line and derive z, FWHM, flux, luminosity
- Fit a Gaussian, often plus a constant continuum, to the aperture spectrum (2020ApJ...904..130V;
  2017ApJ...849...91M with GILDAS; 2025A&A...694A.171M; with MCMC, 2026ApJ..1002L..28Y), or to a spectrum from a
  uv-plane fit (2024A&A...685A..80Z, GILDAS `uv_fit` on ALMA data). 2018MNRAS.481.1976Z took z from both the
  signal-weighted mean frequency and a Gaussian fit. z = nu_rest/nu_center - 1 and sigma_z = (1+z)
  sigma_nu_center/nu_center, where sigma_nu_center is the fit uncertainty on the line center, not the line width;
  equivalently (1+z) sigma_vc/c with sigma_vc the centroid-velocity uncertainty (general).
- Aperture: grow concentric apertures until the flux plateaus (0.1-3.0", giving 1.3-2.3" radii,
  2025A&A...694A.171M; 1.5" radius, 2024ApJ...977L..46B); say radius or diameter.
- Before reporting a total flux, check and state the losses: aperture (2015MNRAS.452...54M applied a 2.5
  correction derived from continuum serendipitous sources in the same aperture; ~20% in 2023Natur.617..261K),
  residual scaling on cleaned images (2020ApJ...904..130V, 0.4-1.5" radii), Gaussian flux outside a finite window
  (2024ApJ...968....9W, ~83% within +/-1.4 sigma; 2019ApJ...887..107F used a 270 km/s FWHM Gaussian to correct a
  100 km/s window), and resolved-out flux: simulations miss 20-40% when the beam matches the [C II] extent and up
  to 70% at SNR < 5, so total flux is uncertain by ~20-30% (2020MNRAS.499.5136C). uv-model fluxes depend on the
  assumed size; a PSF model underestimates extended sources (2018MNRAS.481.1976Z).
- Two components only when the data demand it: reduced chi2 (2018PASJ...70...36I), DeltaBIC > 5 and each
  component S/N > 3 (2025A&A...695A...6P). Fainter lines: fix the center to the [CII] z (2020ApJ...900..131L),
  tie FWHM to [CII] (2019ApJ...881...63N), or a Gaussian prior on z_sys from [CII] (2020MNRAS.492.1778M).
- Luminosity: L/Lsun = 1.04e-3 x S dv [Jy km/s] x nu_obs [GHz] x D_L^2 [Mpc] (2017ApJ...851..145M,
  2024A&A...690A.255D). About 27 of ~45 cosmology lines in the assumptions aggregate use flat LCDM, H0 = 70,
  Om = 0.3 (my count; e.g. 2026ApJ..1002L..28Y, 2018PASJ...70...36I); others use H0 = 67.4-67.8
  (2023Natur.617..261K, 2025A&A...694A.171M) or Om = 0.27-0.272 (2019PASJ...71..109H, 2020ApJ...889...98M).
- Precision reached: z = 6.1657 +/- 0.0003 (2015ApJ...807..180W), 8.31132 +/- 0.00037 (2020MNRAS.493.4294B),
  3.39548 +/- 0.00007 (2024A&A...685A..80Z).

### 9. Non-detections and upper limits
- 3 sigma from the rms at the prior position for an assumed width. Widths vary: 40 km/s (2014ApJ...792...34O),
  100 km/s with 400 as a check (2021A&A...646A..26B), 125 km/s = median FWHM of detections (2025ApJ...987L..37W),
  200 km/s (2019ApJ...881..124M), 400 km/s when only an optical z is known (2020A&A...641A.155V), 719 km/s from
  the redshift uncertainty plus mean FWHM (2018MNRAS.481.1976Z).
- Say which quantity the limit is on. A flux-density limit is per channel: < 720 uJy/beam over a 40 km/s
  channel (2014ApJ...792...34O). An integrated limit for a top-hat window W of N = W/dv independent channels of
  rms sigma_ch is I_lim = 3 sigma_ch dv sqrt(N) = 3 sigma_ch sqrt(W dv), growing as sqrt(W) (general practice;
  2021A&A...646A..26B used this scaling to put literature limits on one width; doubling the window raised the
  limit ~30% in 2025ApJ...987L..37W). State sigma_ch, dv, W, per-beam or aperture rms (multi-beam region:
  sqrt(N_beams) x moment-0 rms, 2024A&A...690A.255D), channel correlation (Hanning), and any Gaussian-wing
  correction.

### 10. Line luminosity function (only if you need one)
- Detections alone are not an LF: each source needs the volume in which it could have been found. Blind search:
  integrate the detectable volume per luminosity from each field's noise and PB response (2020ApJ...889...98M).
  The LF of 2021A&A...646A..76L rests on its fidelity and completeness; 2025A&A...695A.163B ran 1000 realisations
  with the same bins, volume, completeness and fidelity. Weight each source by fidelity/completeness (general
  practice) and say so; 2024A&A...684A.119P set all fidelities to 1 and ignored completeness.
- UV-selected sample: modified 1/Vmax, phi = 1/dlogL x sum(C_UV,j / V_j), C_UV the UV incompleteness per M_UV bin
  (2020ApJ...905..147Y); a lower limit because UV-faint [CII]-bright sources are missed. Keep the two estimators
  distinct; hand detailed LF fitting to a number-counts or LF workflow.

## Parameter defaults and ranges

Read column 2 as "most common in the pack" only where the count is 3 or more and the row says so; otherwise it
is an example. Choose settings from your channel width, line width and beam, and state them. Per-paper rows and
more examples: `references/parameters.md`.

| Parameter | Common choice or example | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Weighting for line cubes | natural (20) and robust 0.5 (~20), about equally; robust 2 (7) for shallow data | natural, robust 0.5-2 | my count of key-parameter lines; some papers use several | 2021A&A...646A..26B, 2020ApJ...904..130V, 2025ApJ...987L..37W |
| Channel width (frequency) | examples: 7.8, 15, 15.625, 30, 31.2 MHz | 7.8-62.5 MHz | 6 named here | 2016ApJ...833...67W (7.8/31.2), 2020ApJ...889...98M (15), 2015ApJ...807..180W (15.625), 2020ApJ...904..130V (30), 2020MNRAS.494.5542R (62.5) |
| Channel width (velocity) | 14-50 km/s for imaging; 100 km/s for searches | 5-100 km/s | 8 named here | 2025A&A...701A..85K (5), 2025ApJ...987L..37W (14), 2015ApJ...807..180W (17.5), 2025NatAs...9.1553F (20), 2014ApJ...792...34O (40), 2024ApJ...972..116I (50), 2018Natur.556..469M (100) |
| Frequency kernel for blind search | several widths spanning ~50 to ~500 km/s | ~50-1000 km/s | 9 (my count) | 2016ApJ...833...67W (3-9 ch), 2025A&A...694A.171M (3-19 ch), 2023Natur.617..261K (66-282 km/s), 2020MNRAS.499.5136C (50-500), 2021A&A...646A..76L (~90-550), 2025A&A...696A..33P (~50-1000) |
| Seed threshold | S/N 3 to 4 per kernel or voxel | 2.5 per channel over >= 3 channels to 5 | 9 (my count) | 2021A&A...646A..76L (3), 2020ApJ...889...98M (3), 2016ApJ...833...71A (3.5), 2020MNRAS.499.5136C (3.6), 2018Natur.556..469M (4), 2025ApJ...995..219F (2.5), 2021ApJ...914...36I (5) |
| Final detection cut | S/N >= 5 or a fidelity cut | S/N 3.5 (targeted, prior known) to 7 | 9 (my count) | 2020ApJ...905..147Y (3.5), 2016ApJ...833...69D (5), 2018MNRAS.481.1976Z (5), 2023Natur.617..261K (6.0), 2020MNRAS.495.3124H (6.2), 2024A&A...690A..55S (7) |
| Fidelity cut | 0.8-0.9 (4 of 5) | 0.6-0.9 | 5 | 2016ApJ...833...67W (0.6), 2020ApJ...904..130V (0.8), 2021A&A...646A..76L (0.85), 2019ApJ...882..136A (0.9), 2025A&A...694A.171M (0.9) |
| Duplicate merge scale | ~1-2" or one beam, and 300-500 km/s | 1" to 2"; 280 MHz to 2 x FWHM | 4 | 2020MNRAS.499.5136C, 2023Natur.617..261K, 2025A&A...694A.171M, 2025ApJ...988...19S |
| Injected lines for completeness | thousands to a million | 2500 to 1,016,400 | 3 | 2016ApJ...833...67W, 2021A&A...646A..76L, 2025PASJ...77.1163H |
| Search region (radius) | examples, geometry stated | sqrt(2) x PB radius (53"/39" at 3 mm), 30.9" or 23" radius, PB response >= 50%, within the PB FWHM (radius = FWHM/2) | 5 | 2016ApJ...833...67W, 2023Natur.617..261K, 2025A&A...696A..33P, 2020ApJ...889...98M, 2017A&A...605A..42C (PB FWHM 16") |
| Search window around a prior (targeted) | cover the prior's z uncertainty | abs(v) < 500 to -2900/+1300 km/s | 4 | 2017A&A...605A..42C (500 of Lya), 2020MNRAS.499.5136C (1000 of [OIII]), 2020MNRAS.495.3124H (1500), 2021A&A...646A..26B |
| Spectrum aperture (geometry stated) | ~1 beam, or where the curve of growth plateaus | 0.35" radius; 0.4-1.5" radii; 0.8" diameter; 1.3-2.3" radii; area of four beams | 13+ (my count) | 2017ApJ...851..145M (0.35" radius), 2020ApJ...904..130V (0.4-1.5" radii), 2026ApJ..1002L..28Y (0.8" diameter), 2025A&A...694A.171M (plateau, 1.3-2.3" radii), 2019A&A...630A..59B (four beam areas) |
| Moment-0 collapse | 1.2 x FWHM or +/-1.4 sigma | +/-1.4 sigma to 3 x FWHM, fixed 300 km/s, or highest-S/N range | 7 | 2020ApJ...904..130V, 2024ApJ...977L..46B, 2024ApJ...968....9W, 2025A&A...694A.171M, 2020ApJ...903...34A, 2018ApJ...867..140L, 2020MNRAS.493.4294B |
| Line profile model | Gaussian + constant | 1-2 Gaussians | top fitting-aggregate phrasings are Gaussian variants (profile 3, line fit 3, plus constant 2, single 2) | 2020ApJ...904..130V, 2025A&A...695A...6P |
| Width assumed for upper limits | no consensus; state yours | 40-719 km/s | 7 | 2014ApJ...792...34O (40), 2021A&A...646A..26B (100), 2025ApJ...987L..37W (125), 2019ApJ...881..124M (200), 2020A&A...641A.155V (400), 2018MNRAS.481.1976Z (719) |
| Companion association (after detection) | examples: abs(dv) < 1000 or < 2000 km/s | 1000-2000 km/s | 2 | 2025A&A...694A.171M, 2020ApJ...904..130V |
| Robust single-line redshift | exclude every alternative solution | S/N > 8 for exclusion by non-detection; 5 sigma | 1 | 2022MNRAS.515..678B |

## Software

From the pack's "Software named in the matched steps" aggregate (counts are matched steps, not papers):

| Software | Count | Used for |
|---|---|---|
| CASA (tclean 32, uvcontsub 10, immoments 3) | 155 | calibration, cubes, moment maps, simobserve mocks (2020MNRAS.499.5136C) |
| findclumps | 12 | blind 3D search, fidelity, completeness (2016ApJ...833...67W, 2021A&A...646A..76L, 2025A&A...694A.171M) |
| CASA imfit / imfit | 11 + 6 | 2D Gaussian position/size/flux of line maps (2020ApJ...904..130V, 2024ApJ...968....9W, 2021A&A...646A..26B) |
| GILDAS | 11 unfiltered | ALMA uv-plane `uv_fit` (2024A&A...685A..80Z, 2018MNRAS.481.1976Z); NOEMA [CII] spectra (2017ApJ...849...91M); some steps are off-topic GILDAS/CLASS work (2019A&A...632A.106L) |
| emcee | 10 | two-Gaussian MCMC fit of a [CII] spectrum (2024A&A...682A..54T); kinematic and morphology fits (2021Sci...371..713L, 2024A&A...691A.133V) |
| interferopy | 4 | S/N cubes and spectra with findclumps (2025A&A...694A.171M) |
| LineSeeker (4), MF3D | 4 | blind finders run alongside FindClump (2019ApJ...882..139G) |
| redshift-search-graphs | 4 | robust-redshift diagnostic and tuning choice (2022MNRAS.515..678B, per its card) |
| lmfit | 5 | 2D Sersic morphology (2024A&A...691A.133V), moment-0 sizes (2025ApJ...987L..37W); not line profiles |
| MAGPHYS / UVMULTIFIT | 7 / 6 | SEDs for counterpart redshift arguments (2016ApJ...833...67W) / uv-plane [CII] sizes (2025A&A...693A.237I) |
| curve_fit, daofind, SpectralCube, Line Stacker | < 3 each | stacked fit (2019A&A...630A..59B), findclumps peaks (2016ApJ...833...67W), seed-and-grow (2020ApJ...889...98M), stacking (2019A&A...631A..78S) |

Not recommended here: PyMC3 appears only in the off-topic LMC paper 2019A&A...632A.106L; PySpecKit (5) and
q3dfit (4) steps come from nearby-galaxy and optical-IFU work (2021A&A...645A..21G, 2025A&A...696A..88W).
Downstream tools (CLOUDY 25, 3DBarolo 14, PyNeb 12, PDR Toolbox 5 + 3, GalPak3D 5) belong to other skills.

## Pitfalls

- Single-line redshifts. "Single lines cannot give definitive redshifts" (2020A&A...642A.155Z); without continuum
  or optical/NIR counterparts, low-z CO interlopers cannot be ruled out (2020ApJ...889...98M, 2025A&A...696A..88W).
  Require a second line, an independent spec-z, or the exclusion test of 2022MNRAS.515..678B.
- Non-Gaussian noise. An excess of large negative voxels points to correlated noise and false positives
  (2020ApJ...889...98M); a candidate "could be systematic noise" (2014ApJ...795....5O). Check the voxel histogram.
- Low reliability near S/N 5 and the trials factor. Reliability may be ~50% at S/N = 5 (2017A&A...605A..42C);
  1-2 survey sources may be spurious and z > 9 detections marginal (2025ApJS..278...45F); one cube held ~180
  features at similar or higher S/N in 259793 independent beams (20" radius, 274 channels) (2024ApJ...964..146F).
- Purity and selection. Setting all fidelities to 1 hides spurious sources (2024A&A...684A.119P); blank-field
  densities from data about 3 times deeper need care as a baseline (2025A&A...694A.171M); UV-selected samples give
  a lower-limit LF (2020ApJ...905..147Y); a field LF can rest on one object (2021A&A...646A..76L); a companion
  search may be incomplete (2025A&A...696A..88W).
- Extended emission resolved out. Large emitters can be missed (2015MNRAS.451.1141M); sparse short baselines
  resolve out [CII] (2018ApJ...859...12G); tapering costs sensitivity and alone does not recover total flux
  (2020MNRAS.499.5136C).
- Coverage and atmosphere: gaps, band edges, bad windows (2020ApJ...892..119M, 2025A&A...694A.171M,
  2019PASJ...71..109H); limited bandwidth caps measurable velocities (2020ApJ...905...85S).
- Aperture size and geometry. Luminosities changed by ~2 with aperture size (2017ApJ...851..145M); one paper
  gives a 1.0" diameter in the text and a 1.0" radius in the appendix (2024ApJS..275...36F).
- Astrometry. ALMA-HST offsets of 0.1-0.2" are uncertain (2019ApJ...881..124M); one paper shifted ALMA by 0.25" to
  match HST, checked with foreground continuum sources (2017ApJ...851..145M); 2020MNRAS.499.5136C tied both to
  GAIA and judged offsets against a 0.2" ALMA astrometric error.
- Settings cards flag as not stated (my sums over the pack's list): CASA/pipeline version (~38), flux calibrator
  and flux-scale uncertainty (~28), line-free channels and continuum subtraction (~29), self-calibration (~7),
  primary-beam correction (~7), MCMC sampler/priors for line fits (2), and the findclumps pre-fidelity S/N
  threshold (2016ApJ...833...67W). Report all of these.

## Verification checks

What papers did:
- Inverted-cube fidelity (2016ApJ...833...67W, 2020ApJ...904..130V, 2021A&A...646A..76L, 2025A&A...694A.171M);
  visibilities split into three subsets with consistent line flux (2015MNRAS.452...54M); separate images of
  three tracks each showing a ~3 sigma peak (2016Sci...352.1559I).
- Noise: pixel S/N histogram Gaussian below S/N 4 (2016Sci...352.1559I); rms vs theoretical noise
  (2021A&A...646A..26B); noise from 1000 random apertures of the flux-aperture size (2025ApJ...995..150K).
- Recovery: a known companion and all emitters of an earlier survey recovered (2020ApJ...889...98M); injected-line
  completeness with the same pipeline (2016ApJ...833...67W, 2021A&A...646A..76L, 2025PASJ...77.1163H); simobserve
  mocks checked against repeat observations of the same targets (2020MNRAS.499.5136C).
- Independent redshifts: [CII] vs SINFONI within 1 sigma (2024A&A...685A..80Z); [C II] vs optical, no systematic
  offset, MAD 200 km/s (2018MNRAS.481.1976Z); [CII] vs [OIII] profiles (2020MNRAS.493.4294B).
- Flux methods: clipped vs Gaussian-fit flux (2020ApJ...900..131L, 2020ApJ...905..147Y); random apertures of the
  same geometry (2017ApJ...851..145M); GILDAS uv fit vs CASA uvmodelfit (2018MNRAS.481.1976Z).
- Sensitivity to choices: association limit 1000 vs 2000 km/s (2025A&A...694A.171M); limit window doubled
  (2025ApJ...987L..37W); second component only if BIC or chi2 favors it (2025A&A...695A...6P, 2018PASJ...70...36I).

What a careful referee adds:
- Fidelity per kernel width and per region (primary-beam rings), not one global curve.
- The S/N for the cut measured the same way in real and inverted cubes, after the same masks.
- For each redshift, the alternative transitions that fit the same frequency and why they are excluded.
- The trials factor of picking a velocity window or kernel after looking at the data.

## Source cards

Full list: `references/sources.md` (368 papers). Most informative for this technique:

- 2016ApJ...833...67W: findclumps search, fidelity function, 2500-line completeness, counterpart-based z.
- 2021A&A...646A..76L: serendipitous [CII] in 118 cubes, fidelity 85% at S/N 6.30, ~50000 injected lines.
- 2025A&A...694A.171M: findclumps companions, pooled fidelity > 0.9, merge radius, curve-of-growth apertures.
- 2020ApJ...904..130V: companion search in 56 quasar cubes, inverted cubes, abs(dv) < 2000 km/s association.
- 2020MNRAS.499.5136C: blind search in tapered cubes, duplicate rule, simulated missing flux.
- 2020ApJ...889...98M: seed-and-grow search, negative-voxel excess, interloper caveat.
- 2023Natur.617..261K: serendipitous [C II] emitters, kernel range, duplicate cropping, aperture loss.
- 2019ApJ...882..139G: LineSeeker, FindClump and MF3D kernels for a 3 mm deep-field search.
- 2023MNRAS.519...34H: untargeted CO search in calibrator fields with reliability and PB-gain cuts.
- 2025PASJ...77.1163H: million-source completeness grid for a [C II] LF.
- 2022MNRAS.515..678B: when a (sub)mm redshift is robust; tuning choice.
- 2024A&A...687A.288G: joint spurious probability for two-line redshifts.
- 2024ApJ...964..146F: trials factor of noise features in a large cube.
- 2015MNRAS.452...54M: z ~ 7 [CII] with split-data reliability test and limits.
- 2021A&A...646A..26B: targeted search window, negative-pixel rejection, width-scaled limits.
- 2015ApJ...807..180W: systemic z and Lya offsets in a common frame.
- 2024A&A...685A..80Z: uv-plane line extraction and SINFONI check.
