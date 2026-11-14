# Review task: a REFRESHED ALMA agent skill against its rebuilt evidence pack

The skill below was first written from a ~1,600-paper corpus, reviewed, and fixed (the fix record is the
RECONCILIATION section). The corpus then grew to ~3,500 papers, the evidence pack was rebuilt, and a writer began
updating the skill to the new pack. The writer may have been cut off before finishing, so expect a mix: some
counts and ranges updated to the new pack, others still at the old values, and possibly a half-edited section.

Apply every check from the standard review (attribution, unsupported practice, scientific correctness, omissions,
usability: see below), and also these refresh checks:

A. **Stale or mixed numbers.** Paper counts, "used in N papers", common choices and ranges that do not match the
   NEW pack aggregates (the old corpus was about half the size, so old counts are usually roughly half). The
   description line's "Built from N ALMA papers" must match the pack.
B. **Lost fixes.** Any item the RECONCILIATION marks FIXED that the current skill has undone or reintroduced.
C. **Broken edits.** Duplicated sections, contradictory statements left from an unfinished rewrite, tables whose
   rows disagree with the text, dangling references.
D. **Length.** Over ~300 lines is a low-severity usability finding; say what could move to references/parameters.md.

Standard checks, in this order:
1. Attribution: every number, range, default, software attribution and "papers do X" claim that cites bibcodes is
   supported by the pack for those bibcodes; counts match the pack aggregates.
2. Unsupported practice presented as literature practice.
3. Scientific correctness: formulas, units, CASA task/parameter names and semantics, unsafe advice.
4. Omissions: important pitfalls, assumptions or validation checks clearly present in the pack but missing.
5. Usability: anything an agent would misread or could not act on.

You have no file access: everything you need is in this message.

Output format (Markdown, nothing else):

```
# Codex refresh review: <slug>
VERDICT: CLEAN | FIX
REFRESH: COMPLETE | PARTIAL   (PARTIAL if any section still carries old-pack numbers or an unfinished edit)
## Findings
- RR-01 | high|medium|low | <stale|lost-fix|broken-edit|length|attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- RR-02 | ...
## Notes
<at most 5 lines>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (redshift-line-search) ===
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

=== references/parameters.md ===
# Per-paper settings for redshift and line searches (from the evidence pack)

Every entry is taken from `packs/redshift-line-search.md` (key parameters, assumptions, excerpts). "Not stated"
means the card flags it as missing. A blank cell means the pack does not give that setting for that paper; do
not fill it from another row.

## Blind and serendipitous searches

| Paper | Search method | Seed / cut | Fidelity / reliability | Completeness | Region |
|---|---|---|---|---|---|
| 2016ApJ...833...67W | findclumps, 3/5/7/9-channel averages on 7.8 MHz (3 mm) and 31.2 MHz (1 mm) cubes, daofind | seed not stated; >2 sigma in consecutive channels | 1 - N_neg/N_pos, error-function fit (C_3mm 5.1, sigma 0.4; C_1mm 5.0, sigma 0.8); keep >= 60%; 60/80/95% at S/N 5.17/5.34/5.57 (3 mm) and 5.15/5.50/5.97 (1 mm) | 2500 injected lines, 50-500 km/s, peaks 0.22-1.00 mJy (3 mm) and 0.5-2.0 mJy (1 mm) | radius: sqrt(2) x PB radius at 3 mm (53" at 84 GHz, 39" at 115 GHz), 30.9" at 1 mm |
| 2016ApJ...833...69D | not given in the pack (same ASPECS field as 2016ApJ...833...67W by title; its search settings are not transferred here) | S/N > 5; 21 candidates (10 at 3 mm, 11 at 1 mm) | | | |
| 2019ApJ...882..136A | not given in the pack (ASPECS by title) | | fidelity > 0.9 gives 16 candidates | | |
| 2021A&A...646A..76L | findclumps on 118 cubes, kernels ~90-550 km/s | S/N 3 seed | > 85% (S/N >= 6.30), plus two ~50% lines with counterparts; 14 lines final | ~50000 injected lines, four PB rings | |
| 2020ApJ...904..130V | per-channel S/N > 3, Gaussian smoothing in frequency up to 400 MHz, 56 cubes | S/N 3 | >= 0.8 from inverted cubes; visual vetting | not stated | |
| 2020ApJ...889...98M | > 3 sigma in one 15 MHz channel, four neighbours > 2 sigma (~50 km/s), moment 0 over FWHM | S/N > 5 | visual inspection; negative-voxel excess noted | recovers known emitters | within the PB FWHM (half-power contour); target masked |
| 2015MNRAS.451.1141M | blind [CII] search at z ~ 4.5 | 6 sigma | | | |
| 2018Natur.556..469M | 100 km/s channels | SNR > 4 peaks; 14 candidates all SNR > 6.3 | | | |
| 2025ApJ...995..219F | per-channel | S/N > 2.5 across >= 3 contiguous channels | | | |
| 2024A&A...690A..55S | | robust lines sigma > 7, p_chance < 0.001; P_chance < 5% for masking lines | | | |
| 2017A&A...605A..42C | targeted window | abs(v) < 500 km/s of Lya | reliability may be ~50% at S/N = 5 | | PB FWHM 16" (diameter); 2" excluded around a serendipitous source |
| 2025ApJS..278...45F | survey LF | 5 sigma and FWHM = 200 km/s assumed for LF | 1-2 sources may be spurious | no completeness correction for IR LF | |
| 2020MNRAS.499.5136C | custom finder on natural-weighted cubes plus ten uv tapers (0.2-2"), trial widths 50-500 km/s | peak SNR 3.6; within 1000 km/s of [OIII] and 5" of UV | | simobserve mocks for missing flux | duplicates: one beam and 500 km/s |
| 2023Natur.617..261K | windows of 4-17 channels (~66-282 km/s) | S/N > 6.0 | | | radius 23" across 4 SPWs; duplicates cropped at 1" and 280 MHz |
| 2025A&A...694A.171M | findclumps + interferopy, 3-19 channel windows | SNR > 4; abs(dv) < 1000 km/s (2000 gives the same) | > 0.9, negative/positive catalogs pooled over all fields | | merge radius 2" |
| 2019ApJ...882..139G | LineSeeker (Gaussian sigma 0-19 ch), FindClump (top-hat N = 1-9), MF3D (spatial 0-4") | | | | |
| 2023MNRAS.519...34H | 3 sigma voxels, >= 2 pixels, >= 3 channels | peak S/N > 4; width <= 1/4 of the cube | reliability R > 0.3 | | PB gain >= 0.3 |
| 2025A&A...696A..33P | DBSCAN on connected voxels, kernels ~50-1000 km/s | | | | PB response >= 50% |
| 2020MNRAS.495.3124H | seven cubes, widths one channel to 1000 km/s | S/N 6.2 (set by the negative peaks) | | | +/-1500 km/s around z = 4.304 |
| 2016ApJ...833...71A | Gaussian kernels 180-500 km/s | S/N > 3.5 | | | |
| 2021ApJ...914...36I | | > 5 sigma peak and >= 2 contiguous channels > 3 sigma, +/-1000 km/s | | | |
| 2022A&A...665A.107T | line scan | S/N > 3 per channel over >= 20 adjacent channels (>= 150 km/s) | | | |
| 2025ApJ...988...19S | | | | | duplicates pruned within 2 x FWHM and 1.5 x beam |
| 2025PASJ...77.1163H | | | | peak S/N 2.0-7.0 x FWHM 36-396 km/s, 84 positions, 100 repeats, 1,016,400 sources | |
| 2024ApJ...964..146F | | ~180 features at similar or higher S/N in 259793 independent beams (20" radius, 274 channels) | | | |

## Targeted detection thresholds and widths

| Paper | Setting |
|---|---|
| 2020ApJ...905..147Y | detection SNR_peak >= 3.5 (75 detections, 43 non-detections) |
| 2020A&A...643A...1L | detection S/N > 3.5 |
| 2014ApJ...792...34O | 3 sigma limit, assumed width 40 km/s, 40 km/s channels |
| 2015MNRAS.452...54M | 3 sigma limits in 100 km/s bins; 7 sigma offset clump |
| 2019ApJ...881..124M | conservative limit assumes 200 km/s width and ~0.7" beam |
| 2020A&A...641A.155V | 3 sigma, Delta v = 400 km/s when only optical z available |
| 2019ApJ...887..107F | single Gaussian FWHM 270 km/s used to correct a 100 km/s window |
| 2019ApJ...887..144J | acceptable line widths 100 to 1000 km/s |
| 2021A&A...646A..26B | 3 sigma; collapses of 100 (fiducial) and 400 km/s; pixels > 3 x rms within 1"; rms scales as sqrt(width) |
| 2025ApJ...987L..37W | 3 sigma over [-125, 125] km/s = median FWHM; doubling the window raises the limit ~30% |
| 2018MNRAS.481.1976Z | 3 sigma over 719 km/s (3 x MAD redshift accuracy in quadrature with mean FWHM); detections > 5 sigma |
| 2021ApJ...918...69U | 320 km/s assumed width for a 3 sigma CO(4-3) limit |
| 2023A&A...673A.157D | fixed Gaussian FWHM 375 km/s; 3 sigma threshold |
| 2025ApJ...985L...8U | 3 sigma limits over 500 km/s |

## Line fitting and redshift

| Paper | Setting |
|---|---|
| 2020ApJ...904..130V | single Gaussian + constant; aperture radii 0.4-1.5" with residual scaling |
| 2026ApJ..1002L..28Y | Gaussian + constant by MCMC; 0.8" diameter apertures |
| 2017ApJ...849...91M | flat continuum + Gaussian, GILDAS |
| 2018PASJ...70...36I | single Gaussian, 1.5" diameter; double Gaussian tested by reduced chi2 (1.05 vs 1.24) |
| 2025A&A...695A...6P | two components only if DeltaBIC > 5 and both S/N > 3 |
| 2020ApJ...900..131L | center fixed to [CII] redshift; 0.8" radius aperture |
| 2019ApJ...881...63N | same FWHM as [CII] for all lines |
| 2020MNRAS.492.1778M | Gaussian prior on z_sys (6.5285, 0.001) from [CII] |
| 2020ApJ...905...85S | systemic z from [CII] or S/N-weighted stacked CO lines |
| 2017ApJ...851..145M | L/Lsun = 1.04e-3 x S dv x nu_obs x D_L^2 |
| 2025A&A...694A.171M | aperture where concentric-aperture flux plateaus (1.3-2.3" radii); flat continuum + Gaussian; moment 0 over +/-1.4 sigma, flux x ~1.20 |
| 2018MNRAS.481.1976Z | z from signal-weighted mean frequency and Gaussian fit; uv-plane exponential with optical size (GILDAS uv_fit) |
| 2024A&A...690A.255D | luminosity error = sqrt(N_beams) x moment-0 rms |
| 2023Natur.617..261K | 0.24" radius extraction; aperture loss correction ~20% |

## Redshifts from spectral scans (no prior z)

| Paper | Setting |
|---|---|
| 2022MNRAS.515..678B | robust if adjacent CO solutions within 5 sigma are excluded; S/N > 8 needed to exclude alternatives by non-detection; 6 tunings (3 in Band 3, 3 in Band 4); non-robust z weighted 50% in its figure of merit |
| 2022MNRAS.511.3017U | adjacent CO lines have similar integrated fluxes, so strong single lines can exclude solutions |
| 2024A&A...687A.288G | N_eff for the second line = number of possible CO transitions; joint spurious probability = product; S/N > 6 lines spurious probability < 1e-6 |

## Assumptions that travel with [CII] redshift papers

Dust for L_FIR when the continuum is also measured: T_dust = 47 K, beta = 1.6 in many quasar papers
(2020ApJ...904..130V, 2026ApJ..1002L..28Y, 2019ApJ...887...40W, 2018ApJ...854...97D, 2020ApJ...897L..14Y,
2025A&A...694A.171M); alternatives 30 K (2015ApJ...807..180W), 35 K (2017ApJ...851..145M), 40 K with beta 1.5
(2020MNRAS.499.5136C, 2016Sci...352.1559I), 45 K (2025ApJS..278...45F, 2021A&A...646A..26B). These belong
to the `dust-continuum-mass` and `sed-fitting` skills; state them, do not tune them here.

=== RECONCILIATION (first review, fixes to keep) ===
# Reconciliation: redshift-line-search
- SR-01 | FIXED | Step 1 now says the line of source Lya-2 was truncated, leaving its luminosity and redshift uncertain (pack line 419, 2013ApJ...763..120C).
- SR-02 | FIXED | Split into a targeted search-window row (abs(v) < 500 km/s of Lya, 2017A&A...605A..42C) and a post-detection companion-association row (abs(dv) < 2000 km/s, 2020ApJ...904..130V); step 7 explains the difference.
- SR-03 | FIXED | GILDAS row now separates ALMA uv_fit (2024A&A...685A..80Z) from NOEMA clic/mapping spectra (2017ApJ...849...91M) and labels 6 as the unfiltered aggregate, with the GILDAS/CLASS step from the off-topic LMC paper excluded.
- SR-04 | FIXED | Software table splits emcee / curve_fit / lmfit by use: lmfit marked as 2D Sersic morphology (2024A&A...691A.133V); PyMC3 dropped from recommendations as LMC-only (2019A&A...632A.106L).
- SR-05 | FIXED | Step 2 and the table give separate frequency (7.8-31.2 MHz) and velocity (17-100 km/s) channel examples, each with its paper, plus dv ~ c dnu/nu_obs.
- SR-06 | FIXED | parameters.md no longer copies 2016ApJ...833...67W's kernels, completeness and region into the 2016ApJ...833...69D and 2019ApJ...882..136A rows; those cells are blank, with a note that blanks are not inherited.
- SR-07 | FIXED | Removed the "about 124 on-topic" and "eight off-topic" counts; the skill now says some papers are off-topic, gives two examples, and says the aggregate counts are unfiltered.
- SR-08 | FIXED | Table column renamed "Common choice or example"; single-paper rows now read "example:", with a note that only rows with 3+ papers and an explicit tally count as common. Weighting row now reads natural 6 vs robust 0.5 5, about equal.
- SR-09 | FIXED | Step 9 now separates flux-density limits (720 uJy/beam over 40 km/s, 2014ApJ...792...34O) from integrated limits, gives I_lim = 3 sigma_ch dv sqrt(N), and asks for the rms definition, channel correlation and window correction to be stated.
- SR-10 | FIXED | Step 1 now asks you to record the frame and velocity convention, convert before comparing centroids (LSR conversion in 2015ApJ...807..180W), and define the sign of the offset.
- SR-11 | FIXED | Step 4 adds duplicate merging across kernels (2016ApJ...833...67W "duplicates removed") and requires the retained S/N to feed fidelity and completeness.
- SR-12 | FIXED | Added step 10: blind detectable volume with per-field noise and PB (2020ApJ...889...98M) vs UV-selected modified 1/Vmax (2020ApJ...905..147Y), kept distinct; fidelity/completeness weighting for 2021A&A...646A..76L marked as not shown in the pack.
- SR-13 | FIXED | Step 8 now asks for flux losses to be checked before a total flux is reported: aperture correction 2.5 (2015MNRAS.452...54M), residual scaling (2020ApJ...904..130V), finite-window Gaussian losses (2024ApJ...968....9W ~83%, 2019ApJ...887..107F).
- SR-14 | FIXED | Search-region text and table now say radius vs diameter: PB FWHM 16" is a diameter (8" half-power radius), "within the PB FWHM" means radius FWHM/2, and the step warns that using the FWHM as a radius quadruples the area.
- SR-15 | FIXED | Aperture row lists each geometry explicitly: 0.35" radius, 0.4-1.5" radii, 0.8" radius, 0.8" diameter, 1.5" diameter, single beam, area of four beams, 3 sigma isophote.
- SR-16 | FIXED | sigma_z now uses sigma_nu_center (fit uncertainty on the line center) or centroid-velocity uncertainty, explicitly not the line width.
- SR-17 | FIXED | All "|dv|" and "|v|" in tables (SKILL.md and parameters.md) replaced with abs(dv) and abs(v).

=== EVIDENCE PACK (redshift-line-search, rebuilt) ===
# Evidence pack: Redshift determination and blind line searches (`redshift-line-search`)

Scope: spectral scans and line searches for redshifts, [CII]/[OIII] at high z

Built from 368 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `spectroscopic redshift|redshift (?:determin|identif|search|confirm)|line search|line scan|spectral scan|findclumps|mf3d|blind line|\[cii\]|\[c ii\]|\[oiii\]|\[o iii\]`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- high_z_galaxies: 321
- agn_and_quasars: 126
- nearby_galaxies: 46
- star_formation: 44
- milky_way_ism: 20
- galaxy_clusters_and_sz: 14
- cosmology: 11
- astrochemistry: 8
- transients: 5
- evolved_stars: 2
- stellar_physics: 2
- protoplanetary_disks: 1
- other: 1
- instrumentation: 1

### Software named in the matched steps
- casa: 155
- tclean: 32
- cloudy: 25
- 3dbarolo: 14
- pyneb: 12
- findclumps: 12
- gildas: 11
- casa imfit: 11
- uvcontsub: 10
- emcee: 10
- sextractor: 7
- galfit: 7
- magphys: 7
- cigale: 7
- uvmultifit: 6
- imfit: 6
- dynesty: 6
- bpass: 6
- pyspeckit: 5
- galpak3d: 5
- bagpipes: 5
- lmfit: 5
- pdr toolbox: 5
- essence: 5
- python: 4
- interferopy: 4
- q3dfit: 4
- visilens: 4
- multinest: 4
- redshift-search-graphs: 4
- prospector: 4
- lineseeker: 4
- lephare: 4
- gist: 3
- pdrtoolbox: 3
- immoments: 3
- ppxf: 3
- scikit-learn: 3
- starburst99: 3
- pyautofit: 3

### Fitting methods (most common phrasings)
- Gaussian profile: 3
- Gaussian line fit: 3
- MCMC: 2
- Gaussian plus constant: 2
- Gaussian fit: 2
- single Gaussian: 2
- 1D Gaussian fit using scipy curve_fit: 1
- Visibility fitting in UVMULTIFIT with uncertainties from the post-fit covariance matrix and error propagation: 1
- Kolmogorov-Smirnov test to compare size distributions across multiplicity classes: 1
- Single and double exponential disk fitting in UVMULTIFIT evaluated with reduced chi^2: 1
- Linear regression fitting (y = m log10 EW_Lya + b) and Spearman's rank correlation test: 1
- CASA imfit for deconvolved [CII] sizes: 1
- Modified blackbody to reproduce FIR emission; optimizer and likelihood not stated: 1
- Best-fit log L_[CII] versus log SFR; linear fits of offset Δ versus z; sampler, priors, likelihood and upper-limit trea…: 1
- Gaussian fit to the 1D spectrum (details not stated): 1
- uv-plane model fit with GILDAS; uncertainties from the fit: 1
- Exponential profile with free scale length fitted in uv space: 1
- Linear fit in log space; Pearson correlation coefficient quoted: 1
- Linear fits with quoted slopes and scatter: 1
- Single Gaussian per companion; velocity shift, width and intensity fitted: 1
- Single Gaussian when detected: 1
- 2D Gaussian fit to the moment 0 map (CASA lmfit): 1
- SFR the only free parameter of Yun & Carilli SED model: 1
- Prior: lognormal step function peaked at molecular gas mass, 0.3 dex dispersion: 1
- Gaussian fits compared by chi2/d.o.f.; single 37.6/22, double 21.1/19; sampler/priors not stated: 1
- Fixed theoretical doublet flux ratios; line kinematics tied to [O III].: 1
- Do not separate disc and outflow in the Balmer narrow component because BLR emission prevents a good three-component se…: 1
- Hβ intensity is the only free parameter after tying its kinematics to [O III].: 1
- one Gaussian component: 1
- chi2 minimisation, scipy optimize curve_fit; 1G chi2_nu=8.6 vs 2G 3.7: 1
- PySpecKit χ² minimization; one to three Gaussians.: 1
- Same Gaussian-fitting method as for individual regions; AoN >3.: 1
- Shared velocity-widths; same component-addition criteria as [O iii], maximum two Gaussians.: 1
- uniform priors on intensity, half-normal on width, half-uniform on separation: 1
- Starlight stellar continuum fit using Bruzual & Charlot (2003) single stellar population models: 1
- MCMC; priors not stated: 1
- MCMC, power law: 1
- Least-squares fits; parameter errors from Monte Carlo methods: 1
- Two-dimensional Gaussian fit per spectral channel: 1
- Single Gaussian per line; centroid and FWHM free: 1

### Validation checks used
- Checked against higher-resolution JWST images (Lines et al. 2024) and kinematical analyses (Posses et al. 2024).: 1
- Visual inspection confirming the +-2 sigma velocity range includes almost all [C II] line emission.: 1
- Checked residual maps for absence of >2 sigma peaks in the central 2" region and compared with ALPINE-only visibility f…: 1
- Checked positional offsets between [C II], UV, and FIR emission peaks.: 1
- Checked residual visibility flux excess at the shortest uv-distance bin (20 klambda) against standard deviation.: 1
- Compared profiles against noise levels from random apertures on blank regions and re-tested after excluding IR-bright g…: 1
- Evaluated p-values of Spearman's rank correlation tests.: 1
- Compare spatial offsets with ALMA astrometric uncertainty: 1
- Three recovered candidates have significance >3.8σ and redshifts matching either [OIII] or Lyα: 1
- Unresolved mock-source luminosities match inputs and SNR agrees with ETC; peak>10σ images recover flux within 10%: 1
- Simulations agree with observed flux differences; fluxes and extents agree with published measurements: 1
- Validated on repeat HZ observations; correction uncertainty limits total-flux accuracy to ~20%-30%: 1
- Compare UV+FIR SFRs with literature SED-fitting SFRs for the nine targets: 1
- Compare with De-Looze:2014 local relation and Schaerer:2020 z=4-5 fit; test sensitivity to SED-based SFRs: 1
- Compare ratios with local dwarf galaxies and published simulations: 1
- Updated data still require log U_ion≈−2 and PDR covering fraction 10% in the published interpretation: 1
- Detections robust against the model used for the 1D spectrum extraction; positions consistent with HST peaks: 1
- Compared with optical redshifts: no systematic difference, MAD of 200 km/s: 1
- CASA uvmodelfit gives consistent fluxes; Gaussian model also consistent; channel-to-channel scatter consistent with err…: 1
- Size uncertainty from GILDAS checked against amplitude versus uv range; unresolved-source probability < 1e-5: 1
- Expected false detections < 0.1 among the six sources for the 2.3 sigma tentative signals; average ratio from stacking …: 1
- Dust-based and Schmidt-Kennicutt gas masses consistent for galaxies with 850 um detections: 1
- Scatter of L_[CII]-L'_CO relation compared with that of alpha_[CII]; starburst (SPT) and local samples compared: 1
- Rescaled [CII]/CO ratio compared with the 2000-10000 range in the literature: 1
- Spectral validation of each companion: 1
- Doubling the velocity range would raise the L_[CII] upper limit by ~30%: 1
- Compared with the Zanella et al. 2018 M_H2-L_[CII] relation: 1
- SFR_IR consistent with SFR_SED of Falkendal et al. 2019 for TN J0121+1320, and for the two shallow fields; 4C+19.71 hig…: 1
- Positions on the SFR-M_star plane called uncertain because most measurements are upper limits: 1
- Compared with released data products; consistent fluxes: 1
- [CII] SFRs used as confirmation: 1
- Spectroastrometric mass consistent; inclination check assuming symmetric flux gives i=6±3 (SMG), 2±2 (QSO): 1
- double Gaussian preferred at >99.9% confidence from the chi2 difference: 1
- extended emission seen in several contiguous channels over -500 to +500 km/s: 1
- varying T_ex in [100, 1000] K changes M_out by only ~20%: 1
- Blueshifted broad emission coincides with high velocity dispersion, confirming the previously tentative outflow.: 1
- Stacks of 100 empty positions gave spurious SNR ~0.4; 1000 jackknife stacks excluding 5 sources gave ~11% mean luminosi…: 1
- Subsamples by FWHM, L_AGN, SFR; stack in luminosity density; fixed 8 kpc aperture; Decarli18 sample alone gives SNR~2; …: 1
- Assuming T from 100 to 1000 K changes mass by only 20%: 1
- Inspect residuals and require substantial improvement for multicomponent [O iii] fits.: 1

### Key parameters and settings (bibcode: value)
- 2025A&A...693A.237I: projected angular separation < ~3 arcsec and velocity offset < 300 km/s for pairs; FIR S/N < 5 or overlapping UV blobs for multiple-UV
- 2025A&A...693A.237I: 1-arcsec aperture; 20 km/s channel width; +-2 sigma velocity range (95% flux); nchan = 1
- 2025A&A...693A.237I: Sérsic index n = 1 (exponential disk); 6 free parameters (R.A., Decl., total flux density, major-axis FWHM, minor-to-major axis ratio q, position angle); q fix…
- 2025A&A...693A.237I: Excluded CRISTAL-21 from FIR size comparison due to unreliable FIR size measurement
- 2025A&A...693A.237I: 16 single galaxies; 20 klambda and 100 klambda uv-distance bins; average redshift z = 5.22
- 2025A&A...693A.237I: 10 single galaxies; natural weighting; cleaned down to 1.5 sigma with 3" aperture mask; z = 5.22
- 2025A&A...693A.237I: Rest-frame EW_Lya obtained by multiplying observed-frame EW_Lya by (1 + z)^-1
- 2020MNRAS.499.5136C: Ten taper values: 0.2'' to 2'' in steps of 0.2''
- 2020MNRAS.499.5136C: Search within 1000 km s−1 of [OIII] and within 5'' of the UV counterpart
- 2020MNRAS.499.5136C: Trial widths 50–500 km s−1; peak SNR threshold 3.6
- 2020MNRAS.499.5136C: Duplicate discrimination: one ALMA beam and |Δv=500| km s−1
- 2020MNRAS.499.5136C: First set: 100 synthetic observations for each of the five most compact configurations at 230 and 410 GHz
- 2020MNRAS.499.5136C: Fixed exposure times: [CII] 16 minutes; [OIII] 6.5 hours; point-source significance ~10σ
- 2020MNRAS.499.5136C: Variable-exposure simulations: 0.4''<θ_beam<2''; 5<σ<140 mJy km s−1 beam−1
- 2020MNRAS.499.5136C: C12=2012.1.00523.S; L17=2017.1.00428.L; nominal angular resolutions 0.7'' and 1''
- 2020MNRAS.499.5136C: Split HZ4 L17 data into six parts and use one part to match C12 noise
- 2020MNRAS.499.5136C: Normalise each predicted curve to weighted mean flux at the average θ_beam/D_source of the two datasets
- 2020MNRAS.499.5136C: Measured/input flux table indexed by SNR and θ_beam/D_source
- 2020MNRAS.499.5136C: Modified blackbody: T_dust=40 K; β=1.5
- 2020MNRAS.499.5136C: Asymmetric uncertainty −0.2 dex, +0.4 dex on L_FIR, SFR_IR and total SFR
- 2020MNRAS.499.5136C: Correction factors depend on angular resolution, emission size and detection SNR
- 2018MNRAS.481.1976Z: Secure detection: emission line significance > 5 sigma in the optimal channel range
- 2018MNRAS.481.1976Z: Exponential model size = effective radius from HST stellar mass map (R_e in Table 2)
- 2018MNRAS.481.1976Z: Line map averaged over 719 km/s (3 x MAD redshift accuracy summed in quadrature with average detected line FWHM)
- 2018MNRAS.481.1976Z: Rest-frame 158 um continuum removed from the stack by reducing the flux by 10%
- 2018MNRAS.481.1976Z: SFR = 1e-10 L_IR (Kennicutt 1998); SK relation dispersion 0.2 dex
- 2018MNRAS.481.1976Z: alpha_CO metallicity dependence: log alpha_CO = 0.64 - 1.5 (12 + log(O/H) - 8.7)
- 2018MNRAS.481.1976Z: Rescaling implies L_[CII]/L_CO ~ 6000
- 2025ApJ...987L..37W: robust = +0.5 (1.7 h fields) and +2.0 (0.8 h fields)
- 2025ApJ...987L..37W: S/N >~ 3 collapsed over 125 km/s
- 2025ApJ...987L..37W: Velocity window equals the median FWHM of all fitted [C II] lines
- 2025ApJ...987L..37W: Overlap correction f = (1 - P_overlap) f_fit applied at J0121 [C II]-C and radio core
- 2025ApJ...987L..37W: Q10 = 0.48
- 2025ApJ...987L..37W: A10 = 7.93e-8 s^-1
- 2025ApJ...987L..37W: K(n) = 8.87 - 0.831n + 0.0241n^2 and K(q) = [0.87 + 0.38 exp(-3.71(1-q))]^2
- 2025ApJ...987L..37W: For J0205-[C II], r_e = 2 sqrt(theta_400GHz)
- 2025ApJ...987L..37W: L_IR integrated over 8-1000 um
- 2013A&A...559A..29C: ROBUST=1.5; 0.15" pixel; 28 km/s channels
- 2013A&A...559A..29C: 10^5 MCMC trials; pixels with S/N>=3; Mdyn within 5 kpc
- 2021ApJ...908..235I: velocity resolution 100 km/s, channel rms 0.13 mJy/beam
- 2021ApJ...908..235I: continuum map 1 sigma = 17.6 uJy/beam
- 2021ApJ...908..235I: chi2/d.o.f. computed over +-1200 km/s
- 2021ApJ...908..235I: R_out = 3.5, 6.4, 5.1 kpc for blobs A-C
- 2021ApJ...908..235I: X_C+ = 1.4e-4, T_ex = 200 K, n_crit ~3e3 cm^-3
- 2024A&A...690A.277M: 4750–7000 Å; ignore 5780–6050 Å affected by laser guide stars.
- 2024A&A...690A.277M: Stellar S/N = 50: 426 bins; emission-line S/N = 100: 762 bins.
- 2024A&A...690A.277M: Stellar S/N window: 5580–5680 Å; emission binning based on continuum-subtracted [O III] λ5007.
- 2024A&A...690A.277M: [O III] image: 10 Å line window minus an equal-width window 50 Å redwards.
- 2024A&A...690A.277M: Spaxel S/N > 0.1 for emission and > 1.0 for stars; minimum 50 contiguous spaxels.
- 2024A&A...690A.277M: Initial velocity/dispersion: narrow 0/100 km s^-1; broad outflow and BLR −500/500 km s^-1.
- 2024A&A...690A.277M: Use pPXF stellar fit multiplied by a second-order Legendre polynomial for the stellar and AGN continuum.
- 2024A&A...690A.277M: Single narrow Gaussian for [O III] and [N II]; narrow and broad Gaussians for Hα and Hβ.
- 2024A&A...690A.277M: Star formation: η < −0.5; AGN: η > 0.5; intermediate region composite.
- 2024A&A...690A.277M: Integrated [S II] spectrum in a nuclear aperture of diameter 2″.
- 2019A&A...630A..59B: n=48; channels with atmospheric transmission <0.5 excluded
- 2019A&A...630A..59B: v_out=|Delta v|+FWHM_broad/2; R_out~3.5 kpc
- 2021A&A...645A..21G: Add second/third components for residuals >3 times the standard deviation; retain multicomponent [O iii] fits when residuals improve considerably.
- 2021A&A...645A..21G: [O iii] AoN >3; doublet shares velocity and widths; widths exceed instrumental FWHM ~2.5 Å.
- 2021A&A...645A..21G: For CO component offsets >100 km s^-1 from the previous region, seek continuity in disk velocities.
- 2021A&A...645A..21G: Slice widths 2.4″; heights ~6″–10″ according to [O iii] extent.
- 2021A&A...645A..21G: Maximum two Gaussians for diagnostic-line fits; theoretical [N II] doublet ratios.
- 2021A&A...645A..21G: M_[O iii] normalization 4.0×10^7 M_⊙; luminosity normalization 10^44 erg/s; density normalization 1000 cm^-3.
- 2019A&A...632A.106L: components 10, 15; min width 1, 2 km/s; min separation 0, 1, 2 km/s
- 2019A&A...632A.106L: cloud size 1-10 pc; atomic T=100 K; molecular T=50 K; n_e/n_H=1e-4
- 2021A&A...650A.117N: S/N >= 4 for bright lines (Halpha, [O III] 5007) and S/N >= 2 for faint lines (Hbeta, [N II] 6584, [S II] 6718)
- 2015ApJ...801..123W: i=55 deg assumed when unresolved (J2229+1457, J1148, J1120)
- 2020MNRAS.496.2155Z: L(Hα) = 4πD²F(Hα); SFR = L(Hα)/(1.86 × 10^41)
- 2020MNRAS.496.2155Z: Hα and BPT diagnostic lines require S/N > 3
- 2020MNRAS.496.2155Z: BPT: [OIII]λ5007/Hβ and [NII]λ6583/Hα; Kauffmann2003 star-forming boundary; Kewley2001 composite upper boundary
- 2024A&A...689A.101C: chi2_nu acceptance limit of 4 sigma around 1
- 2024A&A...684A.107M: LSR velocity range = -250 to +350 km s^-1; exclude centroids > 1 arcsec from V605 Aql or with Gaussian FWHM > 1.5 arcsec
- 2024A&A...684A.107M: inclination i = 63 +/- 4 deg; PA = 63 deg
- 2018MNRAS.476.4949D: Tex = 125 K, FWHM 1 km/s, source size 0.5 arcsec (beam dilution 0.5)
- 2016A&A...592A..83K: Chemistry evolved to 10 Myr
- 2025A&A...702A.276P: velocity resolution 0.82 km/s in Band 7 SPW 4
- 2025A&A...694A.171M: Aperture radii listed per source in the 1D table (1.3-2.3'')
- 2025A&A...694A.171M: Line window = Gaussian-fit peak +/-1.4 sigma (~83% of line flux)
- 2025A&A...694A.171M: Flux correction factor ~1.20
- 2025A&A...694A.171M: T_dust = 47 K, beta = 1.6
- 2025A&A...694A.171M: L_FIR = 0.75 L_TIR for the adopted model
- 2025A&A...694A.171M: alpha_CII = 30 Msun/Lsun; inclination 46 deg
- 2025A&A...694A.171M: Null rejected for p-values < 0.05
- 2025A&A...694A.171M: Fidelity > 0.9; SNR > 4; |dv| < 1000 km/s; merge radius 2''
- 2020MNRAS.494.5542R: Peak S/N 5.6 sigma for CO(3-2) and ~5 for CO(10-9)
- 2020MNRAS.494.5542R: Sky-plane pixel size 25 mas; every second pixel cast back, so beam sub-sampled by ~4
- 2020MNRAS.494.5542R: Primary beam approximated by an elliptical Gaussian
- 2020MNRAS.494.5542R: Visibility noise from the scatter over 10-minute intervals rather than the Sigma column
- 2020MNRAS.494.5542R: [C II] reconstructed in 62.50 MHz (~40 km/s) channels with lambda_S optimized per channel; moment-0 and moment-1 maps made (pixels with SNR <= 1 masked for mom…
- 2020MNRAS.494.5542R: Reconstructions re-sampled onto a Cartesian grid of 200x200 pc pixels
- 2020MNRAS.494.5542R: CO(1-0), CO(7-6) and CO(9-8) assumed to follow the spatial distribution of CO(3-2), (8-7) and (10-9)
- 2020MNRAS.494.5542R: Line ratios: [C II]/FIR, [C II]/CO(5-4), [C II]/CO(3-2), CO(8-7)/CO(5-4), CO(10-9)/CO(5-4)
- 2020MNRAS.494.5542R: Pixels with SNR >= 3 treated as detections, SNR < 3 as 3-sigma upper limits
- 2020MNRAS.494.5542R: PDR fraction of [C II] adopted f_PDR = 0.8
- 2020MNRAS.494.5542R: Solutions with G0/n <= 1e-3 discarded as unphysical
- 2020MNRAS.494.5542R: Error budget per pixel: 10 per cent flux calibration, lens-model scatter, and mock-source systematic (6 to 65 per cent)
- 2020MNRAS.494.5542R: n_e = 1.1e-4 n; phi_PAH = 0.5 in the photoelectric heating rate
- 2020MNRAS.494.5542R: f_CII computed per pixel from CO(5-4) S/N >= 3 pixels using the Bothwell 2013 conversion and alpha_CO from CR18
- 2019ApJ...876..112R: 5 mas pixels, 1024x1024, auto-mask SNR 2
- 2019ApJ...876..112R: uv-bin size varied 5 to 50 klambda
- 2019ApJ...876..112R: 25 mas pixel cubes, natural weighting
- 2019ApJ...876..112R: f_[CII]^PDR=0.8; factor 2 correction for optically thin [CII]
- 2025A&A...696A..88W: robust = +0.5 for J0121 and 4C19; robust = +2.0 for J0205 and 4C03
- 2025A&A...696A..88W: 14 km/s channels
- 2025A&A...696A..88W: Aperture radius 0.1 arcsec
- 2025A&A...696A..88W: Number of components chosen by q3dfit up to a user-set maximum
- 2025A&A...696A..88W: Detection at >~3 sigma; apertures 1x or 2x the major beam
- 2025A&A...696A..88W: J0121-B: initial PA = 193 deg, i = 60 deg, varied by +/-15 deg; best fit PA = 187 deg, i = 61 deg
- 2025A&A...696A..88W: 4C19: initial PA = 100 deg, i = 10 deg, varied by +/-15 and +/-30 deg; best fit PA = 93 deg, i = 30 deg
- 2025A&A...696A..88W: Ring separation half the beam major axis; centre fixed to initial guess
- 2025A&A...696A..88W: n = 1, q = 1, k = 1.8; r_e set to PSF or major beam (2 theta for J0205-[C II] and 4C03-[C II]); R = 0.11 arcsec PSF for unresolved [O III] blobs
- 2025A&A...696A..88W: Extinction correction with Halpha/Hbeta = 3.1
- 2025A&A...696A..88W: Solar metallicity, A_V = 1.5 mag from Balmer decrement, Calzetti law
- 2015MNRAS.449.2883G: accept if reduced chi2 < 1+5*sqrt(2 n_dof)
- 2020MNRAS.492.3194S: second Gaussian accepted if Delta BIC > 2; residuals also inspected visually
- 2020MNRAS.492.3194S: [O III] 5007/4959 flux ratio fixed at 2.99; [N II] 6583/6548 ratio fixed at 3.06
- 2020MNRAS.492.3194S: sky-line residual wavelengths masked; noise taken as the RMS of the emission-line free region
- 2020MNRAS.492.3194S: final maps re-binned to 0.1 arcsec
- 2020MNRAS.492.3194S: outflow slice limit set at 2 x FWHM from the outflow component centre in the integrated spectrum
- 2020MNRAS.492.3194S: Type 1 BLR component fixed in velocity and width to the nuclear-spectrum values, only flux free
- 2024A&A...686A..46E: vsys input 1893 km/s for [OIII]
- 2024A&A...686A..46E: Cardelli extinction law, R_V=3.1; intrinsic Ha/Hb=3.1; mu=1.4; central pixel r = half pixel size
- 2017ApJ...836....8T: robust = 0.5
- 2021ApJ...909..204F: 3″ sampling; Gaussian spectral dispersion 1/4 spectral resolution; Gaussian spatial dispersion 1/2 spatial resolution
- 2021ApJ...909..204F: Spatial resolution 15.6 arcseconds; resolving power 1167; unresolved FWHM 257 km s^-1
- 2021ApJ...909..204F: Circular 15.6″ diameter apertures; centers in Table 2
- 2021ApJ...909..204F: Centers on far-IR peaks or 20 cm continuum regions
- 2021ApJ...909..204F: Two GALEX, five SDSS, four IRAC bands; MIPS 24 μm; PACS 70, 100, 160 μm; SPIRE 250 μm
- 2021ApJ...909..204F: [C II]: one or two pseudo-Voigt functions; CO: combination of pseudo-Voigt functions
- 2021ApJ...909..204F: [C II]/FIR comparison with GOALS
- 2018ApJ...853..111J: Te = 8000 K; CNM n=100 cm-3, T=40 K; WNM n=1 cm-3, T=8000 K
- 2023MNRAS.519.2030H: robust = 2.0, velocity resolution ~9 km s^-1
- 2023MNRAS.519.2030H: moment 0 integration range ~ -180 km s^-1 to ~ 110 km s^-1
- 2023MNRAS.519.2030H: moment 1 detection threshold > 4 sigma
- 2025PASJ...77..432U: [CII] high-res: Briggs robust = 0.5
- 2025PASJ...77..432U: [CII] low-res: natural weighting with uvtaper = 0.75 arcsec
- 2025PASJ...77..432U: NIRCam: snowball removal, wisp subtraction, 1/f noise subtraction; PSFs matched to F444W
- 2025PASJ...77..432U: 3DBarolo search: SNRCUT=4.5, GROWTHCUT=4.5, MINCHANNELS=3 on a cube with 40 km/s bins
- 2025PASJ...77..432U: 870 um fit masked 5 sigma peaks
- 2025PASJ...77..432U: Free: kinematic centre, PA, inclination, Vsys, Vrot, sigma; scale height fixed to 300 pc
- 2025PASJ...77..432U: Ring width 0.097 arcsec (0.2 arcsec cube) and 0.35 arcsec (0.9 arcsec cube)
- 2025PASJ...77..432U: spacepar grid: Vrot 1-700 km/s, sigma 1-100 km/s, steps of 2 km/s
- 2025PASJ...77..432U: alpha_CO = 2.5
- 2025PASJ...77..432U: kappa = sqrt(2) Vrot / r
- 2025PASJ...77..432U: Dusty core profile fit on 0.04 arcsec resolution image
- 2021A&A...646A..26B: natural weighting; tapers up to 0.35'' and 0.5'' ([C II]); spectral resolution from native to ~200 km/s
- 2021A&A...646A..26B: Search range -2000 to 700 km/s ([O III]) and -2900 to 1300 km/s ([C II]) relative to expected line position
- 2021A&A...646A..26B: 5 sigma desired for a firm detection; marginal features also examined
- 2021A&A...646A..26B: Fiducial line FWHM 100 km/s, also 400 km/s
- 2021A&A...646A..26B: T_d = 45 K for SFR_IR; velocity-integrated rms scales as sqrt(line width)
- 2021A&A...646A..26B: Solar oxygen abundance 12+log(O/H) = 8.69
- 2021A&A...646A..26B: Redshift fixed to 7.664 and escape fraction zero; Z = 0.0001-0.02; A_V = 0-0.5 in steps of 0.05
- 2021A&A...646A..26B: 7 data points, 4 fitted parameters, 3 degrees of freedom; age restricted to 300 Myr for the alternative solutions
- 2016Sci...352.1559I: Integrated over -300 to +230 km/s
- 2016Sci...352.1559I: Z grid 0.0004–0.05; T_IGM 0.20–0.45; Rgs = 1 or 2; age lower limit 1 Myr
- 2024ApJ...972..116I: robust = 2.0; 50 km/s channels; 3 sigma clean depth
- 2024ApJ...972..116I: aperture diameters 1.5'', 1.0'', 6.0''
- 2024ApJ...972..116I: rest frequency 1900.5369 GHz; SFR calibration uncertainty factor of two
- 2024ApJ...972..116I: C1: 0.96'' x 0.68'', i = 45 deg; C2 + Bridge: 0.85'' x 0.35'', i = 66 deg
- 2024ApJ...972..116I: X_C+ = 1.4e-4, T_ex = 200 K, high density limit (n >> n_crit ~ 3e3 cm^-3), R_out = 1.5 kpc, V_out = FWHM/2
- 2013ApJ...773...44W: Tdust=47 K, beta=1.6 for four sources; J2054-0005 Tdust free with Herschel 350 um
- 2020ApJ...903...34A: 30 MHz channel width; beam ~0.42'' x 0.37''; rms ~0.24 mJy/beam
- 2020ApJ...903...34A: aperture radius 1.5'' (8.3 kpc); epsilon ~ 0.6
- 2020ApJ...903...34A: 700 km/s collapse width equals 3 x [C II] FWHM
- 2026A&A...707A..77H: detection threshold A_G/N_G > 3
- 2026A&A...707A..77H: [SII] ratio R constrained to 0.44 to 1.45; electron density below 50 cm^-3 treated as an upper limit of 50 cm^-3
- 2026A&A...707A..77H: NaI optical depth ratio tau_0,blue = 2 tau_0,red; NaI y = 0.9, a_Na = -5.69, b_dust = -0.95
- 2019A&A...631A..78S: FWHM_min = 270 km/s; mean stacked channel width 60 km/s
- 2019A&A...631A..78S: z=6.236, R=11.5 kpc (2"), v=493 km/s
- 2022ApJ...941...47S: PACS cube spatial pixel = 3 arcsec; MUSE cube spatial pixel = 0.4 arcsec; MUSE velocity shifts = -28.5 km/s (barycentric) and +0.9 km/s (LSRK)
- 2022ApJ...941...47S: SNR threshold = 5
- 2022ApJ...941...47S: Circular aperture diameter = 10.7 arcsec; ALMA aperture = 14.3'' x 7.7'' ellipse
- 2022ApJ...941...47S: 3-sigma lower limits used when Hbeta is barely visible
- 2026ApJ..1004..194F: Velocity channel width 25 km/s; clean threshold 3x pixel-by-pixel dirty RMS; 500 iterations max
- 2026ApJ..1004..194F: Rest-frequency of each cube set from the [C II] redshift
- 2026ApJ..1004..194F: 130 multiple images of 40 source galaxies (14 with spectroscopic redshifts); five NFW components, cluster galaxies, external shear, m=3 and 4 multipoles
- 2026ApJ..1004..194F: Image-position error 0.8 arcsec; best-fit RMS offset 0.64 arcsec
- 2026ApJ..1004..194F: R_ion = 3.6 (fiducial); 5.7 (high alternative)
- 2026ApJ..1004..194F: Blackbody T = 50000 K; cosmic-ray background; plane-parallel, constant density; ISM abundances with PAH grains; stop at log N_H = 23; iterate to converge
- 2026ApJ..1004..194F: Grid 1<log G0<6 and 2<log n_H<7, both in 0.29 dex steps
- 2021ApJ...917...99Y: robust = 0.5
- 2021ApJ...917...99Y: linear function for UVCONTSUB
- 2021ApJ...917...99Y: aperture diameter = 2.0''
- 2021ApJ...917...99Y: Lens redshift = [0.67], Source redshift = [6.5187], Lens Mass = [2.06x10^10 M_sun], Lens e = [0.65], Lens PA = [94.58 deg] (in default model)
- 2021ApJ...917...99Y: source-plane pixel size = 0.04''
- 2021ApJ...917...99Y: integrated flux SNR > 10 threshold for moment 1 and 2
- 2021ApJ...917...99Y: mu_[C II] = 3.44, mu_cont = 4.53
- 2021ApJ...917...99Y: 4 elliptical annuli with width R_eff = 0.136''
- 2019ApJ...887...40W: robust=0.5; 17 km/s channels
- 2019ApJ...887...40W: rings at 0 to 0.6'' with width 0.1''
- 2019ApJ...887...40W: Disk centre fixed at [CII] Gaussian peak; V_sys=0; radius 0.35''
- 2024ApJ...977L..46B: aperture radius 1.5''; cumulative flux plateaus there for both optical and [C II] centroids
- 2024ApJ...977L..46B: line images average channels across 1.2xFWHM
- 2024ApJ...977L..46B: R = 1.75 +/- 0.25 kpc
- 2024ApJ...977L..46B: sigma = 88 +/- 17 km/s
- 2015ApJ...807..180W: robust = 1; 15.625 MHz channels
- 2020ApJ...900..131L: aperture radius 0.8"
- 2020ApJ...900..131L: T_ex = T_kin = 228 K
- 2020ApJ...900..131L: Tdust=40 K, beta=1.6
- 2026ApJ..1002..100T: [O III] PSF FWHM 0.054 arcsec
- 2019ApJ...870...65I: alpha~0.03, h/R~0.05, eta~0.1
- 2021MNRAS.500.3802H: ~50 channels centred on peak of CO(1) emission
- 2021MNRAS.500.3802H: sigma_smooth = 1.5 spaxels
- 2021MNRAS.500.3802H: mask threshold > 1 sigma within ~200 x 200 spaxels
- 2019A&A...621A..83S: eta=0.1; Lbol=6.7 LX(2-10keV); Lbol=90 L[OIII]
- 2024A&A...687A..35R: free: R_eff, I_e, centre (x0, y0), ellipticity, PA, for both gas and dust
- 2024A&A...687A..35R: uniform priors
- 2024A&A...687A..35R: Sersic index fixed to 1 for all fits except BRI1335-0417 dust (free); a preliminary free-n fit varied n within 0.2 and 10.0
- 2024A&A...687A..35R: SGP38326-1 and -2 fitted simultaneously; small companion SGP38326-3 masked
- 2024A&A...687A..35R: sigma = standard deviation of residual map after subtracting the moment 0 map rotated by 180 deg
- 2024A&A...687A..35R: log M* uniform 9 - 12; stellar Sersic n uniform 0.2 - 10; R_eff,* uniform between R_eff of dust and of [CII]
- 2024A&A...687A..35R: M_gas = L_CO x gas_norm, with gas_norm uniform 0 - 10
- 2024A&A...687A..35R: NFW concentration fixed at 3.4; baryon fraction uniform in log between 1e-6 and 0.187 (log f_bar -6 to -0.73)
- 2024A&A...687A..35R: BRI1335-0417: baryon fraction fixed to the cosmological value in the fiducial model
- 2023Natur.617..261K: frequency window sizes = 4 to 17 channels (≈ 66–282 km s^-1)
- 2023Natur.617..261K: duplicate cropping offsets = 1" and 280 MHz (300 km s^-1)
- 2023Natur.617..261K: S/N > 6.0 selection threshold
- 2023Natur.617..261K: Survey volume: circular radius 23" across 4 SPWs (7380 km s^-1 total velocity interval)
- 2023Natur.617..261K: extraction aperture radius = 0.24"
- 2023Natur.617..261K: primary beam response = 67% ([C II]1030A), 47% ([C II]1030B)
- 2023Natur.617..261K: aperture loss correction ≈ 20%
- 2023Natur.617..261K: HST aperture diameter = 0.7"
- 2023Natur.617..261K: MUSE search radius ≈ 3" (20 pkpc) and ±500 km s^-1
- 2017ApJ...851..145M: L_CII/Lsun = 1.04e-3 x S dv x nu_obs x D_L^2, D_L = 64457.8 Mpc
- 2017ApJ...851..145M: T_d = 35 K, beta_IR = 1.5
- 2024ApJ...971...17F: Fit only S/N ≥ 3; component flux between 3σ continuum noise and line peak.
- 2024ApJ...971...17F: NLR FWHM upper limit 1400 km s^-1; lower limit set by instrumental spectral resolution.
- 2024ApJ...971...17F: [O III] 5007/4959 = 3.01; [N II] 6583/6548 = 2.95.
- 2024ApJ...971...17F: L_bol = 9.8 λL_5100; L_bol = 3500 L_5007.
- 2021A&A...654A..37D: Physical areas = π R_160μm,eff²; intrinsic continuum half-light radius = FWHM/2
- 2021A&A...654A..37D: [C ii]/L_IR = [5,0.2] × 10−3; SFR/L_IR = 1.48 × 10−10 [M⊙ yr−1]/[L⊙]
- 2024MNRAS.528.6768H: S/N >2 in Hα, Hβ, [OIII] λ5007 and [NII] λ6584
- 2024MNRAS.528.6768H: Star-forming BPT classification; Hα EW >6 Å; log Σ_M* >7
- 2024MNRAS.528.6768H: SFR [M_⊙ yr^-1] = 7.9 × 10^-42 L(Hα) [ergs s^-1]
- 2019PASJ...71..109H: Integration 481.7-482.6 GHz (J2054), 484.1-485.0 GHz (J2310)
- 2022ApJ...928..150T: DBSCAN min_samples = 3 pixels, max distance = 4; pixel selection threshold = 4.45 * MAD (~3-sigma)
- 2022ApJ...928..150T: Line candidate selection: |v| < 400 km/s and SNR > 3
- 2019ApJ...881..147S: 11 free parameters; seeing 0.66''
- 2025A&A...699A..80H: Velocity coverage −1000 to +1000 km s−1 relative to ALPINE [C ii] frequency.
- 2025A&A...699A..80H: Natural; Briggs robust = 0.5; Natural with 1″ taper.
- 2025A&A...699A..80H: auto-multithresh thresholds 2, 4.5, 2, 0.0; nsigma = 1; σ = 1.4826 × MAD.
- 2025A&A...699A..80H: Aperture radius 0.5″, approximately 3 kpc.
- 2025A&A...699A..80H: Approximately 1 kpc resolution; θ_beam approximately 0.16″.
- 2025A&A...699A..80H: CRISTAL Σ_FIR approximately 10^9–10^11 L⊙ kpc−2; fit redshift range z approximately 3–6.
- 2021ApJ...914...36I: Moment-0 velocity integration range +/- 900 km s^-1; aperture 2 sigma contour of moment-0 map; chi^2 evaluated over +/- 1000 km s^-1; wing center fixed to core…
- 2021ApJ...914...36I: Core frequency range 235.270-235.455 GHz; Wing uv fit frequency ranges 234.970-235.166 GHz and 235.559-235.756 GHz (+/- 250-500 km s^-1), 50 klambda bins, <300…
- 2021ApJ...914...36I: 5 sigma detection threshold for continuum; >5 sigma peak and >=2 contiguous channels with >3 sigma for line emitters; velocity range +/- 1000 km s^-1
- 2021ApJ...914...36I: v_out = FWHM_wing / 2 = 499 +/- 113 km s^-1; R_out < 1.3 kpc (half of 3 sigma wing FWHM limit)
- 2021ApJ...914...36I: 6 concentric rings with 0''.1 width; 5 sigma clipping; fixed dynamical center to quasar position and V_sys = 0 km s^-1; best-fit i = 25 deg and PA = 87 deg; in…
- 2016ApJ...832..151P: AzTEC-3 aperture 1.5''x1.3''
- 2016ApJ...832..151P: Cloudy 13.03; inner radius 3 kpc; B field 1e-5 G
- 2024ApJ...977..190X: 418 × 2 models; log n_H [cm−3] = 2–7 in 19 models, approximately 0.29 dex steps.
- 2024ApJ...977..190X: PDR log G0 = 1–7; XDR log F_X [erg s−1 cm−2] = −2.4–2.4.
- 2024ApJ...977..190X: log(N_H/cm−2) = 23.
- 2024ApJ...977..190X: Fix PDR log n_H = 3.4 and log G0 = 3.9 for both objects in constrained PDR+XDR fits.
- 2014ApJ...792...34O: 40 km/s channels; 7.5 GHz continuum bandwidth
- 2023ApJ...942L..24K: STIS aperture 5 pixels (0''.25); OSIRIS aperture 0''.3 diameter; MUSE apertures 0''.15 diameter; Voronoi binning S/N=10 for [O III]; 3 pixel median filter on M…
- 2023ApJ...942L..24K: CaT region 8350–8900 Å; Voronoi S/N = 35 for stellar kinematics, S/N = 10 for [O III]; ALMA CO(2-1) cube channel width 15 km s^-1, robust = 0.5
- 2024ApJ...966..228R: n_e = 250 cm^-3
- 2019ApJ...880..157D: Tex=100 K; Tdust=35-45 K; beta=1.6
- 2022ApJ...934..173S: EW(Halpha) = 14 Angstrom division cut
- 2022ApJ...934..173S: S/N > 3 in Halpha, Hbeta, [OIII]5007, and [SII]6717,31 for Sigma_SFR
- 2024A&A...689A.145S: Mean epsilon ~ 0.37 (Briggs) and ~ 0.31 (natural) in the [C ii] channels
- 2024A&A...689A.145S: ALMA: naturally-weighted cube in 20 km/s channels smoothed with a sigma = 30 km/s spectral Gaussian and a sigma = 0.1″ spatial Gaussian, rms measured in signal…
- 2024A&A...689A.145S: MUSE: 250 km/s FWHM template, S/N >= 2 between 6729 and 6776 Angstrom, spaxels with fewer than three voxels above threshold excluded, regions under 55 connecte…
- 2024A&A...689A.145S: [C ii] map integrated between 342.293 GHz and 344.006 GHz (1492.7 km/s)
- 2024A&A...689A.145S: Seven free parameters; priors: broad Gaussian on center and effective radius, uniform intensity 0 to image maximum, Gaussian Sersic index (mean 1, sigma 1) lim…
- 2024A&A...689A.145S: Map integrated between 342.088 GHz and 342.454 GHz, which encloses 85% of the line flux
- 2024A&A...689A.145S: 5 sigma detection limit with sigma = 38.8 uJy; T_dust = 45 K, beta_dust = 1.5, nu L_nu(158 um)/L_FIR = 0.185; L_FIR integrated between 42 and 122 um
- 2024A&A...689A.145S: kappa_[CII] = 1.5 Msun/Lsun; R = 2.63 kpc (projected aperture short side); mean inclination 57.3 deg
- 2022A&A...665A.107T: 3 sigma threshold for [CII] moment maps; >2 sigma velocity-integrated map region for spectral extraction
- 2022A&A...665A.107T: Annulus thickness: 0.1 arcsec for [CII] and dust continuum, 0.25 arcsec for CO(6-5); background rms area: 10 x 20 arcsec^2
- 2022A&A...665A.107T: Centre fixed to continuum peak; PA = 200 deg; inclination i = 25 deg (from initial free run, explored [20, 45] deg); initial guesses v_rot = 50 km/s, sigma_gas…
- 2022A&A...665A.107T: v_out,blue = -490 km/s, v_out,red = 535 km/s (98% integrated wing flux velocity); R_out,blue = 0.6 kpc, R_out,red = 0.3 kpc (or R_out ~ 1 kpc clean beam for lo…
- 2022A&A...665A.107T: Line scan threshold: S/N > 3 per spectral channel over at least 20 adjacent channels (Delta v >= 150 km/s); uvtaper = 0.5 arcsec for continuum search.
- 2016ApJ...833...67W: Candidates kept within sqrt2 x primary beam radius at 3mm (53'' at 84 GHz, 39'' at 115 GHz) and 30.9'' radius at 1mm
- 2016ApJ...833...67W: C_3mm=5.1, C_1mm=5.0, sigma_3mm=0.4, sigma_1mm=0.8
- 2016ApJ...833...67W: Peak flux 0.22-1.00 mJy (3mm), 0.5-2.0 mJy (1mm); widths 50-500 km/s
- 2026ApJ..1002L..28Y: aperture diameter 0.8''
- 2015A&A...576L...2S: µ = 49 ± 5
- 2023MNRAS.519.1293D: HST FOV = 11.9 x 10.6 arcsec^2
- 2023MNRAS.519.1293D: AGN continuum spectral index = 1.5; AGN bolometric luminosity = 2.5 x 10^43 erg s^-1; electron densities from [S II]6716/6731 at T = 10000 K; free parameters: …
- 2024A&A...686A..48N: Excluded non-detected galaxies (UGC 11763, UGC 2982, NGC 5734) from correlation analysis; 12 galaxies used for [N II]122/[O III]88
- 2022A&A...661A.136G: 45 SSPs (3 metallicities, 15 stellar ages); continuum S/N > 5.0 threshold
- 2025ApJ...981..135S: Total circular aperture diameter = 1.8''
- 2025ApJ...981..135S: Sky background annulus = 0.95'' to 1.95''
- 2025ApJ...981..135S: Component apertures: E = 1.4x0.80, W = 1.1x0.66, E-core = 0.44x0.44, W-core = 0.44x0.44, N-tail = 0.70x0.40, S-tail = 1.0x0.50 arcsec^2
- 2025ApJ...981..135S: z = 7.1520 (fixed)
- 2025ApJ...981..135S: n_H = 100 cm^-3 (fixed in Bagpipes CLOUDY models)
- 2025ApJ...981..135S: Old stellar component: constant SF from 600 to 100 Myr ago with Z_star = 0.5 Z_sun
- 2025ApJ...981..135S: Dust parameters fixed: alpha_U = 2, U_max = 10^7, q_PAH = 2.5%
- 2025ApJ...981..135S: Aperture dust attenuation corrections: E (A_V = 1.2 mag), W (0.34 mag), E-core (0.72 mag)
- 2025ApJ...981..135S: Convolved beam = 0.38''
- 2025ApJ...981..135S: CLOUDY stopping criterion: electron fraction = 10^-2; SFH = 10-Myr constant star formation
- 2021Sci...371..713L: 102 channels of 15.626 MHz (~14 km s^-1) width; Hanning smoothed to ~28 km s^-1
- 2021Sci...371..713L: Briggs robust = 0.5; Boolean mask smoothed to 0.4'' clipped at 3 sigma_s; cleaned to 3 sigma_d
- 2021Sci...371..713L: threshVelocity = 1; 9 rings of width 0.06''
- 2021Sci...371..713L: z_0 = 300 pc (fixed); V_rad = 0 (fixed); PA = 40 deg (fixed after run 1); i = 25 +/- 3 deg (from run 2)
- 2021Sci...371..713L: Gaussian PSF = 0.123'' x 0.095'' at PA = -63.9 deg for ALMA continuum; Sersic index n = 1, projected axis ratio = 0.9, center fixed to [C II] disk; 5 iteration…
- 2021Sci...371..713L: Gas and stellar disk exponential vertical scale height = 300 pc; stellar disk exponential radial scale length = 700 pc; bulge De Vaucouleurs R_e = 300 pc; comp…
- 2021Sci...371..713L: EMCEE: 200 walkers, 1000 burn-in iterations, 2000 production iterations, stretch move parameter a = 2
- 2018PASJ...70...36I: 1.5 arcsec diameter circular aperture
- 2026ApJ..1000..312Z: 5 BAL and 11 non-BAL spectra; J0056+2241 excluded
- 2026ApJ..1000..312Z: R_out([CII]) = 3.0 kpc; BAL R_out 1-100 pc; v_BAL = 2.5e4 km/s; T ~ 100–1000 K; n >> n_crit
- 2021A&A...645A..33B: CO(1-0) upper limit = 3 x rms of velocity-integrated JVLA map over 685 km/s for J0801+5210, assuming CO(5-4) FWHM
- 2021A&A...645A..33B: v_circ = 1.3 x dv_blue-red / (2 sin i), dv ~350 km/s at ~5 sigma contours of BAROLO model
- 2026MNRAS.549ag781K: aperture radius = 1.5 arcsec, maximum Gaussians = 2, [O III]5007:[O III]4959 = 3:1
- 2020MNRAS.498.1560J: Tacconi18 comparison limited to within +/-0.05 of the sample redshift range, CO-based measurements only
- 2024ApJ...977L...9Z: Gaussian with A, sigma, nu_cent free and flat zero continuum
- 2024ApJ...977L...9Z: Line width 186 +/- 58 km/s adopted; search around 433.96 GHz
- 2024ApJ...977L...9Z: magnification mu = 1.3
- 2024ApJ...977L...9Z: log L_Hbeta = 42.16 (+0.09/-0.13) erg/s
- 2024ApJ...977L...9Z: sigma = 79 +/- 25 km/s; r_1/2 = 39 +/- 11 pc or 105 +/- 9 pc
- 2024ApJ...977L...9Z: L52/L88 < 5.6 (3 sigma)
- 2023MNRAS.521.1045R: Cleaning threshold: 3x RMS (AzTEC1, BRI1335-0417, J081740), 1.5x RMS (SGP38326)
- 2023MNRAS.521.1045R: Briggs robust = 2 (cubes: AzTEC1, J081740, SGP38326; continuum: J081740, SGP38326) and robust = 0.5 (cube: BRI1335-0417; continuum: AzTEC1, BRI1335-0417)
- 2023MNRAS.521.1045R: Cell size: 0.02"/px (AzTEC1, SGP38326), 0.03"/px (BRI1335-0417, J081740); uvtaper: 0.1" for SGP38326
- 2023MNRAS.521.1045R: SNRCUT = 3.5, 3.0, 3.5, 3.0, 3.5 and GROWTHCUT = 2.5, 2.5, 2.5, 2.0, 3.0 for AzTEC1, BRI1335-0417, J081740, SGP38326-1, SGP38326-2
- 2023MNRAS.521.1045R: NT = 4 for pseudo 4-sigma contour
- 2023MNRAS.521.1045R: Fiducial run: Z0 = 0 (razor-thin disc), minimising on total flux map; Thick-disc run: full 3D cube mode, PA fixed to morphological PA, inclination and Z0 free
- 2023MNRAS.521.1045R: NRADII = 4, 5, 4, 5, 3 and RADSEP = 0.11", 0.15", 0.13", 0.13", 0.12" for AzTEC1, BRI1335-0417, J081740, SGP38326-1, SGP38326-2
- 2023MNRAS.521.1045R: LINEAR = 0.43 (AzTEC1, BRI1335-0417), 0.51 (J081740, SGP38326-1, SGP38326-2); SIDE = approaching (BRI1335-0417), both (all others)
- 2017ApJ...845..175J: 15.6 MHz ~17 km/s channels; natural weighting
- 2017ApJ...845..175J: core 169 to -77 km/s; sub-galaxies -94 to -305 km/s
- 2024A&A...682A..54T: uniform priors; narrow and broad mean frequencies not overlapping
- 2024A&A...682A..54T: R 2.4-5.5 kpc; v_out=560 km/s
- 2013ApJ...770...13W: 15 channels of 15.625 MHz integrated
- 2021ApJ...908...53W: Observed-frame 1mm continuum and [C ii]-based redshift
- 2026A&A...707A.376C: MOKA3D conical outflow maximum extension = 5 arcsec (~470 pc), PA = 235 deg; energetics radial extent Delta R = 284 pc (~3")
- 2022MNRAS.514.5035L: S/N > 3 threshold for Halpha and CO; radial annuli width = 200 pc, step = 100 pc
- 2025A&A...701A..85K: Band 6 robust = 0.5, 5 km/s channels
- 2025A&A...701A..85K: Band 8 channels of 15.625 MHz (~11 km/s)
- 2025A&A...701A..85K: Line redshifts 7.1329 ([CII]) and 7.1334 ([OIII])
- 2025A&A...701A..85K: Five components (violet, blue, green, yellow, red), blue and red each with two sub-components; components first identified in [CII] and recovered in [OIII]
- 2025A&A...701A..85K: Velocity gradients modelled with an empirical arctan model (truncation velocity and radius)
- 2025A&A...701A..85K: Violet (red) component not fit in Band 6 (Band 8) maps; photometry taken in a 0.2'' radius aperture on the residual map; positions of faint components fixed, f…
- 2025A&A...701A..85K: Component sizes from 2D Gaussian FWHM of the model; effective radius taken as HWHM
- 2023A&A...673A.116K: Single beam extraction; 3-sigma upper limits including 0.1% ALMA calibration uncertainty
- 2023A&A...673A.116K: Lens parameters: (x_L, y_L), ellipticity e_L, position angle phi_L; Source parameters: Sersic profile with (x_S, y_S), flux density, Sersic index, half-light r…
- 2023A&A...673A.116K: Apertures: BRI0952 (2.1'' x 1.45''), Comp-SW (1.13'' x 0.57''), Comp-N (1.3'' x 0.62''), AzTEC-3 (circle r = 2.4''), LBG-3 (1.2'' x 1.5''), Gal-S (2.6'' x 1.7'…
- 2023A&A...673A.116K: L_IR integrated from 8-1000 um; Bagpipes mass range 10^8 - 10^14 M_sun, metallicity range 0.01 - 1.0 Z_sun; Modified blackbody T = 45 K, beta = 1.7
- 2023A&A...673A.116K: R_out = 7.5 kpc (AzTEC-3), R_out = 2.3 kpc (BRI0952, lensing corrected with mu = 3); v_outf = 0.5 x FWHM_broad
- 2019ApJ...876....1T: MCMC 20,000 iterations
- 2019ApJ...876....1T: CO luminosity multiplied by 2; [CII]ion/[NII]=2
- 2012A&A...542L..34N: pressure-equilibrium cloud; N scales as Z^2 above 0.23 Zsun; Orion grains
- 2020ApJ...895...74N: robust = 0.5
- 2025A&A...701A..48D: K_c = 1.14 for NGC 6860; central negative pixels interpolated
- 2019ApJ...880....2W: moment-0 over -300 to 300 km/s
- 2020MNRAS.496..943D: Halpha outflow channel v = 306 km/s, PA ~ 17 deg
- 2024ApJ...961...71F: Line frequency 263.6995 +/- 0.004 GHz
- 2024ApJ...961...71F: Dust temperature 45 K (also 60 K and 80 K tested), beta = 1.8, mu = 20
- 2024ApJ...961...71F: Mask: pixels >2 sigma in the moment-0 map
- 2024ApJ...961...71F: Narrow map 263.62-263.72 GHz; broad map 263.73-263.92 GHz
- 2024ApJ...961...71F: Lensing magnification mu = 22 applied to the Table values (except flux densities)
- 2024ApJ...961...71F: M_H2 = 5.1e8 Msun, r = 27 pc
- 2023ApJ...945...69R: fitspw = all spws excluding serendipitous CO (J=5-4) channels from SSTSL2 J021856.14-051951.4
- 2023ApJ...945...69R: [O III] bin width = 20 km s^-1; [C II] bin width = 25 km s^-1
- 2023ApJ...945...69R: weighting = natural, outframe = BARY, veltype = optical
- 2023ApJ...945...69R: Optimal [O III] Cycles 2+3 uv-taper = 0.3"
- 2023ApJ...945...69R: [O III] velocity integration ranges: -310 to +250 km s^-1 (Cycle 3), -280 to +260 km s^-1 (Cycles 2+3); detailed clump ranges in Table 4
- 2023ApJ...945...69R: [C II] velocity integration ranges: -80 to +145 km s^-1 (Cycle 1, Cycles 1+3, Cycle 7, Cycles 1+3+7), -70 to +155 km s^-1 (Cycle 3), -80 to +120 km s^-1 (Cycle…
- 2023ApJ...945...69R: specfit ngauss = 2 (clump A), ngauss = 3 (clumps C' and C'')
- 2023ApJ...945...69R: 3σ clipping iterated 10 times for background rms
- 2023ApJ...945...69R: θ_beam = sqrt(1.2" x 0.77"); D_source = 1.99" ± 1.04" (4.5σ) and 1.1" (3.6σ); SBD correction factors = 0.60 ± 0.20 (4.5σ) and 0.48 ± 0.12 (3.6σ)
- 2019ApJ...871...85L: taper 500 klambda; bins 25, 150, 300 km/s
- 2024A&A...683A.169W: fitted region from [O III] narrow-band image with S/N > 5
- 2024A&A...683A.169W: lines fitted simultaneously with the same velocity shift and width per component
- 2024A&A...683A.169W: shock models: pre-shock density 100 cm^-3, v_shock >= 200 km/s
- 2021A&A...654A..90L: Systemic velocity channel = [-300, 300] km s^-1; outflow channels: v < -300 km s^-1 and v > 300 km s^-1 (also tested > 600 km s^-1); [N II] and [O III] doublet…
- 2024MNRAS.535..729P: Branch division at log N2 <= -0.6 vs log N2 > -0.6
- 2025ApJ...991L..38U: pixel size = 0.05'', PSF FWHM = 0.21'' at 5.125 um, extraction threshold >= 2 sigma in [O III]5008 map, aperture correction = 10%
- 2025ApJ...991L..38U: natural weighting, 30 km s^-1 channel width, integration range 434.2-434.9 GHz (480 km s^-1)
- 2025ApJ...991L..38U: Convergence threshold delta_Te < 10 K; 10,000 Monte Carlo realizations
- 2025ApJ...991L..38U: 3sigma threshold for Halpha and Hbeta maps; 2sigma [O III]5008 isophotal aperture; 10% aperture correction
- 2025ApJ...991L..38U: Component 1: (Te,1, ne,1) = (26,000 K, 500 cm^-3); Component 2: (Te,2, ne,2) = (8,000 K, 50 cm^-3)
- 2022MNRAS.515.1751W: tclean threshold set to 3x theoretical sensitivity
- 2022MNRAS.515.1751W: 0.6'' uv taper for total [O III] and [C II] line fluxes; |v| > 1000 km/s for mfs continuum
- 2022MNRAS.515.1751W: 0.6'' tapered cubes for [O III] and [C II]; contiguous spaxels >= 2σ; untapered natural cube for [N II]
- 2022MNRAS.515.1751W: log10 U from -4 to -0.5 (step 0.5); log10(n_H [cm^-3]) from 0.5 to 3 (fiducial 10^2 cm^-3); Z_*/Z_sun in {0.005, 0.05, 0.2, 1}; X_α/Fe,neb = 1 and 4; stopping …
- 2022MNRAS.515.1751W: AstroDrizzle final_pixfrac = 0.8, pixel size = 0.065''; ratio maps where both lines >= 3σ; aperture circles with radius 1.5x mean circularised beam; 2σ thresho…
- 2016ApJ...816...37V: L_FIR 42.5–122.5 um; L_TIR 8–1000 um rest-frame
- 2016ApJ...816...37V: Rotation curve rising linearly to 150 km/s at 0.1 arcsec then flat
- 2024A&A...682A.166F: grid: A_V 10^1-10^4 mag, Z 0.05-2, nH 10^2-10^5, alpha_ox -1.4 to -0.4, log U -3 to 0.5; 15% model-ratio uncertainty
- 2015MNRAS.451.1141M: detection threshold 6 sigma
- 2023MNRAS.519.5807D: Modified black-body emissivity index beta = 1.2; 100 Monte Carlo iterations for 160 um upper limits
- 2024ApJ...963..115L: S/N > 3 for H-alpha and H-beta, > 2 for [OIII] and [NII], > 2.5 for CO, HCN, HCO+
- 2024ApJ...963..115L: retired: H-alpha EW < 3 A and S/N > 3 in H-alpha
- 2024A&A...682A..24A: natural weighting; continuum excludes [CII] within 2xFWHM when detected
- 2024A&A...682A..24A: 23 [CII] and 16 continuum detections from first-year data, plus 5 pilot [CII] detections, giving 28 galaxies
- 2024A&A...682A..24A: log(L_[CII]) = (-1.28+-0.21) + (0.98+-0.02) log(M_mol); alpha_[CII] ~ 30
- 2024A&A...682A..24A: alpha_CO range 1.0 to 4.36 Msun (K km/s pc^2)^-1
- 2024A&A...682A..24A: delta_GDR = 1000-3000 expected from MZ and Remy-Ruyer relation
- 2024A&A...682A..24A: log(L_[CII],lim) = 7.5
- 2020Natur.584..201R: self-calibration solint 100 s; 28 channels of 25.7 km/s
- 2020Natur.584..201R: conjugate gradient tolerance 1e-12 (typical source-inversion accuracy 1e-6)
- 2020Natur.584..201R: 163190 visibilities per channel
- 2020Natur.584..201R: rotation curve function V_t, R_t, beta, xi; exponential velocity dispersion profile; no radial variation of inclination and position angle; gas surface density…
- 2020Natur.584..201R: four-step optimisation scheme for lens mass model and source kinematics
- 2020Natur.584..201R: R_gas = 0.9 kpc from exponential fit to azimuthally averaged zeroth-moment rings, fixed in V_gas
- 2020Natur.584..201R: [CII] luminosity 1.8e9 Lsun used with alpha_[CII] to get gas mass
- 2018ApJ...854...97D: T_dust=47 K, beta=1.6, kappa=0.77 (nu/352 GHz)^beta cm^2/g
- 2024A&A...690A.232S: Use [OIII] flux and intrinsic reddening factor 9.5 from (cite: bentz4329).
- 2025MNRAS.537.1163A: Pixels shown only where SNR_G > 5 (SNR_G^2 = chi2_G - chi2_line)
- 2025MNRAS.537.1163A: radsep = 0.025 arcsec
- 2025MNRAS.537.1163A: Initial guesses vrot 330, vdisp 37 km/s, inc 47 deg, pa 115 deg; free: vrot vdisp inc pa vsys
- 2025MNRAS.537.1163A: wfunc = 2 (cos^2 weighting), ftype = 2, norm = local, twostage = true, regtype = 1
- 2025MNRAS.537.1163A: Disc scale height z0 = 0.0138 arcsec (100 pc)
- 2025MNRAS.537.1163A: Bar criterion (i): ellipticity rises to e_max > 0.25 with roughly constant PA; criterion (ii): ellipticity drops by at least 0.1 and PA changes by at least 10 …
- 2021ApJ...909..130R: uv cut: <= 1000 klambda for C43-6; weighting: natural; uv tapers: none, 0.5 arcsec, 1.0 arcsec; cube channel widths: 50-500 MHz (25-225 km/s)
- 2021ApJ...909..130R: Aperture radius R <= 3 kpc, uv-taper = 1.0 arcsec, bandwidth = 250 MHz (110 km/s) centered at 667.97 GHz
- 2021ApJ...909..130R: Total flux grid: 0 to 50 mJy; primary beam FWHM: 9.0 arcsec at 680 GHz; bandwidth: 250 MHz
- 2021ApJ...909..130R: Z = 0.05 Z_sun, n_e = 10 and 100 cm^-3, starburst age step = 0.5 Myr (0.5-5.0 Myr), log U = -4.0 to -1.5
- 2018ApJ...867..140L: moment-0 maps collapsed over 300 km/s centered at +/-155 km/s
- 2024PASA...41..114S: SDSS selection: [OIII] and [NeIII] at >= 2.5 sigma, [NeII] at >= 2 sigma
- 2025ApJ...988...19S: Duplicates pruned within 2xFWHM and 1.5x the beamsize
- 2025ApJ...988...19S: Lensing magnification 1.17x
- 2025ApJ...988...19S: r_e = 260 pc
- 2025ApJ...988...19S: Cloudy grids at fixed log U = -3.0 and -2.0, bracketing log U = -2.5 +/- 0.5
- 2025ApJ...988...19S: Cloudy grid with a 1 Myr old input stellar population
- 2021A&A...653A.111R: minor component S/N >= 3 (integrated flux divided by rms times FWHM)
- 2021A&A...653A.111R: velocity separation <= 500 km/s
- 2021A&A...653A.111R: projected-distance threshold ~2.1 kpc (average [CII] size) for secure mergers
- 2021A&A...653A.111R: r_p = theta x d_A(z_m) at the mean redshift of the two components
- 2021A&A...653A.111R: L_2 corresponds to F_2,[CII] = F_1,[CII]/4
- 2024MNRAS.527.4420M: MUSE apertures 30 arcsec and 3 arcsec
- 2025ApJ...995..150K: natural weighting, 0.1" pixel, 50 km/s channel
- 2025ApJ...995..150K: uv-taper Gaussian width 0.7"
- 2025ApJ...995..150K: Noise from 1000 random circular apertures with same size as flux apertures
- 2025ApJ...995..150K: xi from 1.33 (zero metallicity) to 1.39 (solar)
- 2025ApJ...995..150K: Up to three Gaussians for G395H; number chosen by Delta AIC > 20
- 2021Sci...372.1201T: Briggs robust = 0.0 (continuum) and 0.5 ([C II]); channel width = 20 km s^-1; clean threshold = 1.5x rms (continuum) and 1.0x rms ([C II]); moment mask thresho…
- 2021Sci...372.1201T: Central 0.5" region used for PaFit
- 2021Sci...372.1201T: PA = 4.5°, inclination = 37.8°; radial annulus 1.6 kpc to 7.2 kpc; m = 1, 2, 3, 4; bilinear spline interpolation
- 2021Sci...372.1201T: M_gas = 5 x 10^10 M_sun; SNR > 4 in at least 4 velocity channels
- 2019ApJ...881..124M: VR7 collapse 252.285-252.519 GHz (-20 to -320 km/s wrt Lyα)
- 2025ApJ...985..243B: 4'' x 4'' window centered on source; mask threshold 2 sigma
- 2025ApJ...985..243B: Uncertainty: RMS of channels outside +/-1 FWHM of the line centroid
- 2025ApJ...985..243B: Median FWHM_[CII] = 260 (+50/-80) km/s; median individual S/N = 14 +/- 3
- 2025ApJ...985..243B: A galaxy enters a subsample only if its pixel count on that side of the threshold exceeds the number of pixels in the synthesized beam
- 2025ApJ...985..243B: Low-Sigma_SFR stack: 11 of 15 galaxies; high-Sigma_SFR stack: 9 of 15
- 2025ApJ...985..243B: R_out = 6 kpc
- 2025ApJ...985..243B: Median sample SFR = 52 Msun/yr used for the full-stack eta_m
- 2023MNRAS.518.3183L: Initial aperture center: alpha = 09:59:30.459, delta = 2.08.02.586; area equal to beam width
- 2023MNRAS.518.3183L: 3 sigma moment-0 threshold mask
- 2023MNRAS.518.3183L: 18 channels on either side of central emission channel (velocity range of 540 km s^-1)
- 2023MNRAS.518.3183L: 3 sigma moment-0 mask for moment-1 and moment-2 maps
- 2023MNRAS.518.3183L: Annulus bin width = 0.1"
- 2023MNRAS.518.3183L: Sersic index n free, and fixed n = 1.0
- 2023MNRAS.518.3183L: Halo detection threshold: > 4 sigma outside central beam (up to 10 kpc) or beyond rest-frame UV emission
- 2023MNRAS.518.3183L: Seven circular apertures with radii of 0.05" and 0.02"
- 2018ApJ...859...12G: bins 75 klambda for continuum; 300 klambda ([CII] ALESS 61.1, UDS 47.0) and 75 klambda (ALESS 65.1, 73.1)
- 2024ApJ...970...30M: SEARCH: primary SNR cut 4.5 sigma, secondary 3.5 sigma, at least 30 pixels, significant flux in at least 2 consecutive channels
- 2024ApJ...970...30M: Ring geometry: maximum radius 0.8 x CO FWHM major axis; minimum ring radius = beam minor axis / 2.5; minimum model radius 0
- 2024ApJ...970...30M: Initial guesses Vmax = 150 km/s, Vsigma = 30 km/s; inclination and PA initial guesses from [C II] modeling
- 2024ApJ...970...30M: 1000 runs per approach: r41 fixed at 0.63, and r41 drawn from normal 0.63 +/- 0.44
- 2024ApJ...970...30M: [C II] PDR fraction f_neutral = 0.83 from Croxall et al. 2017
- 2024ApJ...970...30M: alpha_CO,MW = 4.36 Msun/(K km/s pc^2); r41 = 0.63
- 2022MNRAS.515..678B: Signal-to-noise > 8 sigma required to exclude alternative CO redshift solutions from non-detections
- 2022MNRAS.515..678B: Redshift distributions smoothed by dz approx 0.5
- 2022MNRAS.515..678B: Robust CO detection threshold: adjacent solutions within 5 sigma excluded
- 2022MNRAS.515..678B: 6 tunings total (3 in Band 3 and 3 in Band 4)
- 2022MNRAS.515..678B: Non-robust redshifts weighted down by 50% in figure of merit
- 2019ApJ...874...27T: tau_SFH = ±0.01, ±0.1, ±1, ±10 Gyr; Z = 0.0001-0.02; A_V = 0-5; f_esc free
- 2025A&A...700A.285W: Voronoi min S/N 20 in 5080–5260 Å; CB09 templates; [NII], [OIII] ratio fixed to 2.96
- 2024ApJ...964..146F: ~180 features at similar or higher S/N in 259793 independent beams within 20 arcsec radius and 274 channels
- 2024ApJ...964..146F: F356W fit fixes axis ratio, PA and Sersic index from F150W
- 2021ApJ...918...69U: 2 sigma voxel threshold connected in velocity space; 0.9" pseudo-slit width
- 2021ApJ...918...69U: d = 1" aperture for 1.0" resolution individual source extraction; 320 km/s assumed velocity width for 3 sigma CO(4-3) upper limit on ALMA4
- 2021ApJ...918...69U: NFW concentration c = 4.5; projection factors 2/pi (distance) and 1/sqrt(3) (velocity)
- 2025PASJ...77..139I: Lensing magnification corrected for literature objects
- 2025PASJ...77..139I: L_FIR(PDR) = 0.22 L_FIR; L_[CII](PDR) = 0.83 L_[CII]; L_[OI] multiplied by 2
- 2025PASJ...77..139I: Spectrum at 30 km/s resolution
- 2020ApJ...904..131N: robust = 0.5; clean to 2 sigma within 2 arcsec radius mask
- 2020ApJ...904..131N: uvcontsub with fitorder = 1, excluding 2.5xFWHM around the line
- 2020ApJ...904..131N: specmode = mfs; multi-scale scales 0, 1, 3, 5, 10 beams; 2 arcsec radius mask to 2 sigma
- 2020ApJ...904..131N: Velocity bins of fixed 30 km/s or 0.2 sigma_line; channels chosen with im.advisechansel in LSRK, nearest neighbour
- 2025ApJ...993..204H: Extraction diameters: 0.6 arcsec for J0217-0208 and J1211-0118; 1.0 arcsec for SXDF-NB1006-2
- 2025ApJ...993..204H: Scale pipeline error spectra to line-free standard deviations, accounting for spatial correlations
- 2025ApJ...993..204H: Free parameters: V-band dust optical depth, metallicity, star formation history, total stellar mass; fixed spectroscopic redshift
- 2025ApJ...993..204H: Five SFH bins: 0–10 Myr first bin; remaining bins logarithmically spaced to z = 30; constant SFR in each bin
- 2025ApJ...993..204H: Seven free parameters: ne,1, ne,2, Te,1, Te,2, 12+log(O/H), O32, and L[OIII]5007,1/L[OIII]5007,2
- 2023ApJ...952...48H: velocity range -200 to +200 km s^-1
- 2023ApJ...952...48H: velocity resolution 50 km s^-1
- 2023ApJ...952...48H: r_61 = 0.28 +0.04/-0.02, r_71 = 0.17 +0.02/-0.02
- 2023ApJ...952...48H: alpha_CO = 25 M_sun (K km s^-1 pc^2)^-1 (range 5 - 25 for Z = 0.2 - 0.8 Z_sun)
- 2023ApJ...952...48H: DGR ≈ (1.8 - 53) x 10^-4
- 2018A&A...611A..22S: Disk centroid fixed to dust continuum; parameter ranges h, i, PA, I0, vsys, sigma_v, rt, vt
- 2024ApJ...963...19N: Re-calibration of SPT0441-46 OH motivated by high noise in images from the original calibration; for SPT2132-58 [CII], a discontinuous noise jump between adjac…
- 2024ApJ...963...19N: Channel widths (km/s): SPT0202-61 50, SPT0418-47 70, SPT0441-46 75, SPT2132-58 150, SPT2319-55 75; same widths for [CII]
- 2024ApJ...963...19N: CLEAN threshold 1.5x thermal noise measured in the channel map at the central velocity of the higher-frequency OH doublet component
- 2024ApJ...963...19N: Integration regions where continuum is detected above 3 sigma
- 2024ApJ...963...19N: 3 sigma threshold for a statistically significant detection
- 2024ApJ...963...19N: Absorption patches counted as genuine only if coincident with dust continuum and deeper than any patch not coincident with the continuum (spurious patches seen…
- 2022A&A...660A..14R: 34 selected out of 43 [CII] non-detections (S/N < 3.5 in [CII])
- 2022A&A...660A..14R: z_med = 5.52
- 2022A&A...660A..14R: 500 jackknife realizations removing 20% of spectra; 16th and 84th percentiles for error
- 2022A&A...660A..14R: 2 SFR bins of 17 objects each divided at log(SFR_TOT,med / M_sun yr^-1) = 1.16
- 2022A&A...660A..14R: Average uncertainty on total SFR ~ 0.2 dex
- 2024A&A...690A.255D: pixel 0.15", channel 25 km/s, natural weighting
- 2024A&A...690A.255D: L_[CII] = 1.04e-3 F D_L^2 nu_obs (L_sun, Mpc, GHz)
- 2024A&A...690A.255D: Luminosity error = sqrt(N) x rms of moment-0 map, N = beams in region
- 2024A&A...690A.255D: Conclusions based primarily on FWHM-based aperture
- 2024A&A...690A.255D: Cold-phase carbon: T < 5e4 K
- 2023A&A...673A.157D: Fixed Gaussian FWHM = 375 km/s
- 2023A&A...673A.157D: 3-sigma detection threshold and upper limits
- 2023A&A...673A.157D: C(60/100) = 0.84
- 2018Natur.556..469M: 100 km/s channels, SNR>4 peaks; 14 candidates all with SNR>6.3
- 2025ApJ...987...61R: Circular aperture diameters: 1.45 arcsec (main [CII]), 0.35 arcsec (satellite [CII]), 1.05 arcsec (main continuum), 0.4 arcsec (satellite continuum)
- 2025ApJ...987...61R: wk2020 model grid (A_V = 7, Z = 1); 1σ pixel masks at L_[CII] > 1.3 × 10^8 L_sun/px and L_FIR > 5 × 10^10 L_sun/px; fixed n = 10^4 cm^-3 for resolved G map
- 2025ApJ...987...61R: n_H = 6 × 10^3 cm^-3, G = 5 × 10^3 G_0, M_m = 4.5 × 10^10 M_sun, α_CO = 0.8 M_sun (K km s^-1 pc^2)^-1, I_CII = 10^-3 erg s^-1 cm^-2 sr^-1, R = 0.456 arcsec = 3…
- 2021A&A...652A.128J: 52 sources (23 multiple images); good-z sub-sample of 36 spectroscopic sources; high-SFR sub-sample above the median SFR; SFR-z sub-sample is the intersection
- 2021A&A...652A.128J: weights proportional to inverse square of local RMS, noise estimated in an area of 12.96 arcsec^2 (81x81 pixels) around the source, sources not masked
- 2021A&A...652A.128J: sources discarded if the cube edge is closer than one beam from the stack centre
- 2021A&A...652A.128J: integration width about twice the ALPINE median FWHM of ~252 km/s
- 2025A&A...701A..31P: Metallicity free, 0.03 to 0.7 Zsun
- 2025A&A...701A..31P: Electron density 100-1000 cm^-3; logU from -3.5 to -1.5
- 2025A&A...701A..31P: SFR(UV) for solar metallicity and constant SFH over 100 Myr
- 2025A&A...701A..31P: Velocity dispersions 103 +/- 17 and 132 +/- 19 km/s for E and W
- 2020MNRAS.494.4090C: Use CO(5-4) or CO(4-3), depending on redshift.
- 2020MNRAS.494.4090C: SPT0125–50, SPT0300–46, SPT0243–49 and SPT0550–53 have 50% to 70% coverage; truncate [C ii] integration to [N ii] coverage.
- 2020MNRAS.494.4090C: [C ii]/[N ii] ≈2 for H ii; >≈9 for PDR/XDR.
- 2020MNRAS.494.4090C: [N ii] significant: [C ii]/[N ii] <10; insignificant: >10.
- 2024A&A...686A.156D: multifrequency mode; Briggs Robust = 0.5; clean to 2.5×RMS.
- 2024A&A...686A.156D: Aperture step: 1 pixel; initial radius equals beam major axis; centred on [CII] barycentre.
- 2024A&A...686A.156D: Examine residual components near +400 and −400 km/s.
- 2018Natur.557..392H: Fiducial tau=100 Myr; Chabrier IMF 0.1-100 Msun; Calzetti law; escape fraction 0
- 2024A&A...684A..33K: Assumed CO(2–1) linewidth equals [C II] FWHM; velocity range encompasses 84% of the emission
- 2024A&A...684A..33K: Detection threshold 4 sigma
- 2024A&A...684A..33K: alpha_CO = 0.8 (K km/s pc^2)^-1, r_2,1 = 1
- 2021ApJ...921...97J: Briggs weighting, robust = 0.5
- 2021ApJ...921...97J: Spectral cube velocity averaging = 100 km s^-1; Moment 0 single channel width = 1000 km s^-1 (W) and 500 km s^-1 (E)
- 2021ApJ...921...97J: Spectral extraction apertures: 2.5'' (W) and 1.2'' (E)
- 2021ApJ...921...97J: [CII] template FWHM = 779 +/- 25 km s^-1 (W) and 371 +/- 12 km s^-1 (E)
- 2021ApJ...921...97J: Integration range: line center - 3*sigma_v to line center + 3*sigma_v; 3000 Monte Carlo iterations
- 2025PASJ...77.1163H: Peak S/N 2.0-7.0 in 0.5 steps (11), FWHM 36-396 km/s in 36 km/s steps (11), 121 parameter sets, 84 positions, 100 repeats, 1,016,400 sources
- 2025PASJ...77.1163H: Survey volume of the unsmoothed cube 2200 Mpc^-3 (sic), typically 120 channels; gamma < -0.3 satisfies the S12 and H19 constraints
- 2025PASJ...77.1163H: Single Gaussian fit of output lines; typical RMS 0.8 mJy/beam; observed frequency 260 GHz; mean z = 6.2
- 2021ApJ...907..122M: γ = 2; NFW concentration parameter c = 3.5
- 2021ApJ...907..122M: Full survey volume = 2.2 x 10^6 cMpc^3; baryon-to-dark matter ratio f_baryon ~ 1/6; ε = 0.01, 0.1, 1.0
- 2017A&A...605A..42C: |v|<500 km/s from Lya; primary beam FWHM 16 arcsec; exclude 2 arcsec around serendipitous source
- 2024A&A...692A..34C: Stop at 1 sigma RMS of 12 uJy/beam; beam 0.38 x 0.3 arcsec; polarised-intensity RMS 8.5 uJy/beam
- 2024A&A...692A..34C: Natural weighting instead of the robust weighting of the earlier paper
- 2024A&A...692A..34C: Median velocity dispersion of 140 km/s in the region with polarisation
- 2024A&A...692A..34C: [C II] line dispersion 140 km/s at the polarised region; density 50 cm^-3
- 2020MNRAS.495.3124H: Line widths from a single channel to 1000 km/s FWHM
- 2020MNRAS.495.3124H: Velocity range +/-1500 km/s about z = 4.304
- 2020MNRAS.495.3124H: Seven cubes searched; core [CII] threshold S/N 6.2 (negative-peak limit)
- 2020MNRAS.495.3124H: Initial 2 arcsec-diameter circular apertures; channels binned by 4 ([CII]) and 2 (CO(4-3))
- 2016ApJ...833...71A: Gaussian kernels 180-500 km/s; S/N>3.5
- 2025NatAs...9.1553F: robust 0.5, 20 km/s channels, 0.05" pixels
- 2025NatAs...9.1553F: free: V, sigma, PA, inclination; ring width (0.5-1.0) x PSF FWHM; AZIM normalization
- 2025NatAs...9.1553F: alpha_[CII]=31 Msun/Lsun
- 2020ApJ...905..147Y: detection SNR_peak >= 3.5 (75 detections, 43 non-detections)
- 2020ApJ...905..147Y: redshift slices 4.403-4.585 and 5.135-5.85; luminosity bins 0.5 dex
- 2017ApJ...842L..16L: uncertainty on C(60/100) ~0.15
- 2024ApJ...968....9W: T_dust=47 K, beta=1.6; T_ex=100 K for C+
- 2024ApJ...968....9W: D=1.5×FWHM major axis; i=arccos(b/a)
- 2021MNRAS.505.4838L: Three to four dark matter halos for parametric models
- 2021MNRAS.505.4838L: 1.5 x seeing diameter extraction aperture; spectral binning factor of 30; redshift search range z = 0 to z = 8
- 2019ApJ...874L..30V: Model velocities -216 to +216 km/s, excluding channels affected by close companion
- 2024A&A...687A.288G: all lines S/N>6 have spurious probability < 1e-6 (Jin) and 100% reliability (Walter)
- 2024A&A...687A.288G: N_Eff for second line = number of CO transitions possible for the first line
- 2024A&A...687A.288G: joint spurious probability = product of first and second line probabilities
- 2022MNRAS.511.1303V: f = 0.44 (differential dust attenuation factor, also tested f = 0.7); lambda = 3727 A
- 2022MNRAS.511.1303V: log(n_H / cm^-3) = [0.5, 2] (and extended on plots to 3), Z = [0.1, 0.5, 1.0] Z_sun, -3.0 < log(U) < -0.5 in steps of 0.5 dex, stopping criterion A_v = 100 mag…
- 2024MNRAS.529L...1J: Aperture 1.0'' x 0.6'' (double the [OIII] deconvolved FWHM)
- 2024MNRAS.529L...1J: alpha_NT=0.8, f_th=0.1
- 2020MNRAS.493.4294B: moment 0 integrated over -140 to +140 km/s
- 2019MNRAS.487L..81L: mu=2 (YD4), mu=10 (JD1)
- 2022PASJ...74.1429T: Spectral resolution = 100 km s^-1, Briggs robust = 2.0, integration range = -250 to +250 km s^-1
- 2022PASJ...74.1429T: Sersic index n = 0.5 (circular Gaussian), point source for -200 km s^-1 channel of [N II] 205 um, two circular Gaussian sources for +100 km s^-1 channel of [O …
- 2017MNRAS.466.2825B: zeta_CR = 1e-15 s^-1; integrate to Av=7; vturb = 1.5 km/s
- 2025A&A...695A...6P: narrow sigma 0-250 km/s; broad width at least 20% larger; broad amplitude <50% of narrow
- 2025A&A...695A...6P: n_e=200 cm^-3, Z=0.5 Zsun, R_out~2 kpc (ionized), 1.3 kpc (neutral)
- 2021ApJ...908..192S: HLS1623: IRAC and ALMA only for MAGPHYS
- 2019ApJS..244...40L: lines predicted: CO (2 <= J_upper <= 10), [C I] (370, 609 um), [N II] (122, 205 um), [C II] (158 um)
- 2024MNRAS.535.1533B: Channel binning factor = 16 for initial line search; line exclusion window = 0.4 GHz for undetected expected lines
- 2024MNRAS.535.1533B: Natural weighting for continuum; briggsbwtaper with robust = 2 for cubes; uv-taper = 0.05 arcsec
- 2024MNRAS.535.1533B: T_d = 35 K, beta_dust = 2.0 for resolved Band 7 MBB; beta_dust = 2.0 for Herschel MBB fit
- 2023MNRAS.523.4654T: CO comparison done at common 0.24 x 0.18 arcsec resolution
- 2023MNRAS.523.4654T: [C II] cube convolved to continuum resolution; masked moment: kernel 2x beam and 2x channel width, mask threshold = rms of original cube
- 2019ApJ...884..154W: peak SNR ~8 each; primary beam response 0.57 and 0.29
- 2024A&A...688A.146A: spaxel scale = 0.05 arcsec; [C II] integration range = -1000 to +1200 km s^-1 (w.r.t. z=6.900); S/N threshold for [C II] moment 1 and 2 = 2.3
- 2024A&A...688A.146A: Virial factor K = 5 +/- 0.1; M_star / M_h = 0.015 - 0.03; systemic redshift z_sys = 6.902 (at W galaxy)
- 2020PASJ...72...69Y: redshift fixed to ZFOURGE photometric or spectroscopic redshift
- 2018MNRAS.475..492K: GalPaK3D MCMC chain of 15,000 runs, 10 parameters
- 2024ApJ...977..161V: Briggs robust = 0.5
- 2024ApJ...977..161V: clean threshold 0.55 mJy (1.4 x dirty-cube RMS)
- 2024ApJ...977..161V: alpha_CII = 7.3 +/- 1.2 Msun/Lsun
- 2020PASJ...72...29O: 100 km s^-1 channel binning; 1''.0 diameter aperture for spectra; 0''.5 radius aperture for upper limit photometry; velocity center 458.184 GHz; velocity width…
- 2020PASJ...72...29O: z = 3.150; D_L = 26951.9 Mpc; nu_rest([C II]) = 1900.5 GHz
- 2019ApJ...881L..23B: epsilon = 0.4; aperture radius 1.3"
- 2025NatAs...9..155Z: [OIII] line width free but common; 5007/4959 peak ratio fixed to 3
- 2025NatAs...9..155Z: Grid log(ne)=0-10 cm^-3, log(Te)=3.7-4.5 K
- 2023A&A...673A.153P: 5 sigma_flux threshold for [C II]; 3 sigma_flux threshold for [O III]; vmin and vmax at 16th and 84th percentiles of best-fitting Gaussian
- 2023A&A...673A.153P: alpha_[CII] = 30 M_sun/L_sun; correction factor = 1.6 on sigma_gas; flat prior on sigma_gas in [0, 300] km s^-1; flat prior on inc within +/- 3 sigma of flux-m…
- 2024ApJ...974..145S: Minimum annulus size 0.14 inches of arc (∼0.7 kpc); S/N threshold 20; use 19/20 bands, omitting F140M
- 2024ApJ...974..145S: SFH bin widths: 5, 25, 70, 100, 100, 150 Myr; final three bins logarithmically fill remaining cosmic time
- 2024ApJ...974..145S: A_v in [0,2.5], dust index in [-1,0.4]; stellar metallicity sampled linearly from 0.01Z_⊙ to 2Z_⊙; log(U) in [-4,-1]
- 2020MNRAS.495.3409S: taper to 0.4 arcsec FWHM synthesized beam; median 1.0 mJy/beam per 32 MHz channel
- 2020MNRAS.495.3409S: adaptive binning to max 1.5 x beam FWHM until SNR > 5
- 2025ApJ...989..160I: Feature at ~9280 A, expected Lyman-alpha at z ~ 6.63
- 2025ApJ...989..160I: Graybody fit with beta = 1.5; continuum under Hbeta+[OIII] taken as mean of F335M and F410M
- 2021A&A...652A..66P: grid of 270x2 models in n_H, G0 or F_X, N_H
- 2024ApJ...964...39G: Narrow-line-only fit: all lines fixed to the same velocity width with a flat broad prior up to 800 km/s
- 2024ApJ...964...39G: Two-component fit: narrow lines fixed in width over 50-150 km/s; narrow Halpha/Hbeta prior range 3-20
- 2024ApJ...964...39G: Instrumental resolution increased by a uniform factor of 1.3; model grid oversamples native resolution by factor of four
- 2020A&A...643A...7G: 0.15'' pixels, 500 iterations, 3 sigma threshold
- 2019ApJ...887..144J: Acceptable linewidths 100 to 1000 km/s
- 2024A&A...691A.133V: n in [0.1,3], I0 in [0,2 Imax]; 77 um best parameters used as priors for other maps
- 2022MNRAS.515.3126I: cell size = 0.15 arcsec, natural weighting, automasking threshold = 2 sigma, line exclusion = 2 x FWHM
- 2022MNRAS.515.3126I: IMF mass cutoff = 0.1 - 300 M_sun
- 2016ApJ...833...69D: 21 line candidates (10 at 3mm, 11 at 1mm); S/N>5
- 2024ApJ...971...47F: Burst SFR 10 Msun/yr, length 50 Myr
- 2024ApJ...971...47F: f = 0.44 and 0.7
- 2020ApJ...889...98M: 3 sigma peak, 4 channels >2 sigma (~50 km/s minimum width), S/N>5
- 2026ApJ..1000..308W: [O II] doublet ratio fixed to unity; [O III] and [N II] doublets fixed to 1/3
- 2019ApJ...882..168P: 18 free parameters HZ10, 12 for HZ9
- 2026A&A...706A.174A: Cube mask 16″ x 10″ elliptical; velocity binning about 100 km/s
- 2024A&A...691L...2S: Spectroscopic redshifts from CO observations
- 2024A&A...691L...2S: Significant AGN IR contribution: AGN fraction >0.05; 3mm.01 and 3mm.09
- 2020A&A...633A..90G: 25 km/s channels; cubes centered on brightest pixel
- 2020A&A...633A..90G: v_out~500 km/s, R_out~6 kpc
- 2025PASP..137l4501T: Unlensed or moderately resolved sources only; spectroscopic redshift required
- 2019ApJ...882..139G: Gaussian kernel sigma_GK 0-19 (LineSeeker); top-hat N=1-9 (FindClump); spatial kernels FWHM 0-4'' (MF3D)
- 2024ApJ...972..111L: ~0.8" aperture and peak pixel 0.1"
- 2020ApJ...900....1F: FWHM_major = 0.826 r_e,major; r_e = r_e,major sqrt(q); source center fixed from imfit
- 2020ApJ...900....1F: Halo: S_ext,[CII] >= 4 sigma, FIR and UV < 3 sigma
- 2017ApJ...850...83F: CLEAN to 3 sigma_d in boxes around >=50,20,10,5 sigma_d peaks
- 2025ApJ...987L...2H: [C II] limit L < 6e7 Lsun; metallicity Z/Zsun = 0.17
- 2025ApJ...987L...2H: log(M_Z/L_[OIII]) = -1.0 +/- 0.2 for L_[OIII]/L_[CII] > 3
- 2020A&A...643A...1L: detection threshold S/N>3.5
- 2024ApJ...961..120C: Channels averaged to 15.625 MHz; continuum from line-free channels at 147 and 231 GHz
- 2023ApJ...953...75H: Flat priors: beta in [-0.7, 0.4], E(B-V) in [0, 10], redshift z in [0, 8]; SFR averaged over past 30 Myr
- 2024ApJ...962L..11W: aperture diameter 1.0'' (SMG-A, SMG-B); 0.3'' (SMG-C)
- 2024ApJ...962L..11W: background [C II] number from cumulative number density with L_[CII] > 10^8.2 Lsun; background LAEs measured at r>50 cMpc
- 2024ApJ...962L..11W: quasar-LAE cross-correlation length r0QG = 7.7 h^-1 Mpc (gamma=1.8), derived from r0QQ and r0GG
- 2020MNRAS.498.4192F: Exclude channels closer than ±3σ width of [N ii] 205 μm or [C ii] 158 μm.
- 2026ApJ..1004...22F: 3-sigma JWST/NIRCam rest-frame optical continuum mask
- 2023MNRAS.524..923Z: log(tau/yr^-1) in [6.5, 10] in log-steps of 0.1; ages in log-steps of 0.1 from 100 Myr to age of Universe; A_V in [0, 6] mag; Z = 0.008, 0.02, 0.05
- 2025A&A...699A.324H: Photometric-redshift summaries: 16th–50th–84th percentiles
- 2025A&A...699A.324H: Reported member sample: spectroscopic redshifts within Δz=0.1 of z=3.09
- 2022MNRAS.516.5618P: Circular aperture radius 0.3 to 2.0 arcsec (continuum sources, S/N optimised at 5000-5200 Å) or 0.5 arcsec (emitters and HST priors); redshift confidence flags…
- 2024MNRAS.528.5019H: two metallicities (0.2 Zsun, Zsun); exponentially declining star-formation histories with tau 0.1 to 15 Gyr
- 2022NatCo..13.4574G: CubEx nebula & 3D CGM gas extraction: SNR > 3, spatial Gaussian filter 0.4'' (2 pixels), spectral Gaussian filter 1.25 Angstrom (1 layer); line search: 1'' ape…
- 2018ApJ...861..100C: [C II] images from within ±1 FWHM of line peak
- 2024A&A...684A.119P: Common bins of 0.4 dex, repeated twice with 0.1 dex shifts
- 2024A&A...684A.119P: All fidelities set to 1; completeness corrections ignored
- 2019ApJ...882..136A: fidelity > 0.9 gives 16 candidates
- 2026ApJ...999...47L: 5 age bins (10, 30, 100, 300, 600 Myr), log U in [-3, -1], Av in [0, 6], M_star in [10^6, 10^13] M_sun, metallicity in [10^-3, 10^0.4]
- 2021A&A...647A.194F: NFW halo with c_200 = 3.4 and M_200 = 2 × 10^12 M_sun
- 2016A&A...593L...2N: CI and CO luminosities scaled by 0.46 for beam contamination
- 2024A&A...690A..55S: P_chance<5% for masking lines; robust lines sigma>7, p_chance<0.001
- 2020Natur.581..269N: 9 or 10 free parameters
- 2024ApJS..275...36F: 30 and 60 km s^-1 spectra; integrated-flux detection > 5σ in both.
- 2024ApJS..275...36F: Aperture stated inconsistently: 1.0″ diameter in main text, 1.0″ radius in appendix.
- 2021ApJ...908..146C: Bruzual and Charlot (2003) templates
- 2024A&A...691A.153L: 1-comp: 20 < σ < 300 km s^-1; 2-comp: 20 < σ_n < 120 km s^-1, 140 < σ_b < 300 km s^-1; 3x3 spaxel averaging
- 2020A&A...643A...6C: DEIMOS spectra boxcar smoothed with 100 km/s window
- 2018MNRAS.473.1909G: v_cont = 700 km/s
- 2022MNRAS.511.3017U: Spectroscopic redshift uncertainty < 0.001
- 2025ApJ...988...48N: SCUBA-2 sources with SNR > 4 within 8 arcmin (~10 h^-1 cMpc) of LATIS2-D2-00 or LATIS2-D2-07
- 2025ApJ...988...48N: Jin18 match found for 92% of sources
- 2025ApJ...988...48N: 61 sources after photo-z cut; 16 removed by spectroscopic z and 7 by archival ALMA proposals, leaving 38
- 2023MNRAS.519...34H: detection threshold = 3 sigma, minimum spatial size = 2 pixels (0.3 arcsec), minimum spectral width = 3 channels
- 2023MNRAS.519...34H: candidate cuts: peak S/N > 4, reliability R > 0.3, primary beam gain >= 0.3, line width <= 1/4 of cube spectral extent
- 2022MNRAS.510.3734D: Magnification factors: mu = 5.5 for CO(1-0) and 3290um dust, mu = 5.6 for [CI](1-0), mu = 5.9 for [CII]
- 2018A&A...619A..39F: spectra from 0.5 arcsec radius region
- 2026MNRAS.546ag049F: kappa_UV = 7.2e-29 (erg s^-1 Hz^-1)^-1; kappa_IR = 1.1e-10 L_sun^-1; kappa_Halpha = 4.977e-42 (erg s^-1)^-1
- 2025ApJ...990L..31B: channels |v|>1000 km/s for fit; hogbom; natural weighting
- 2021MNRAS.502.1797R: g - r > 1, -1 < r - i < 1 (or r - i < 2 relaxed), and 1.5(r - i) < g - r - 0.8; >5 sigma in i and >3 sigma in r
- 2017ApJ...836L...2B: robust = 0.5; 30 km/s channels
- 2025A&A...695A.163B: J=1–4; 1000 realisations; same bins, volume, completeness and fidelity.
- 2020A&A...643A...8G: E(B-V) 0.0 to 5
- 2024ApJ...969...27B: Δz/(1+z) = 0.1 search window
- 2024ApJ...969...27B: FRESCO F444W; GrismR; R ∼ 1600
- 2020A&A...643A...3S: SFR(UV)=1.59e-10 L_UV/Lsun; SFR(IR)=1.40e-10 L_IR/Lsun (Chabrier)
- 2025A&A...696A..33P: Kernel width corresponds to typical line FWHM ~50-1000 km/s; source extraction restricted to PB response >= 50%
- 2025A&A...696A..33P: Source extraction by DBSCAN clustering of connected voxels
- 2025A&A...693A.309S: Continuum power law with fixed slope 3.7 in frequency
- 2026ApJ..1000..159M: natural weighting
- 2026ApJ..1000..159M: line exclusion window = ±300 km s^-1
- 2021A&A...649A.152K: natural weighting
- 2021A&A...649A.152K: non-detections: exclude data within 500 km/s of expected [CII]
- 2023A&A...678A.116A: Gaussian filter of 50 km/s and redshift step of 0.01 (for IRAM spectrum search)
- 2025A&A...693A.190J: PB > 0.5; 1<=z<5; 10^8<=M*<=10^12 Msun; 0.001<=SFR<=10^3 Msun/yr; magnification <100
- 2020ApJS..247...61F: Requires z_IS+wind from at least three absorption lines and no -99 flag
- 2024A&A...686A..85A: [OIII]5008/Halpha = 2 (range 1 to 3.5 for uncertainties)
- 2025A&A...695A.204V: detection threshold gamma = 4 sigma, critical value k = 3
- 2020A&A...641A.155V: upper limits: 3 sigma, Delta v = 400 km/s when only optical z available
- 2024A&A...685A.138V: Q21=0.05-0.4
- 2024A&A...690A.197M: uv taper scales: 0.25'', 0.5'', 1.0'', 2.0''; final smoothed beam: 3.0''; search aperture radius: 0.5''; RMS calculated with 3σ clipping where PB response is 0…
- 2025ApJ...994....4A: Common FWHM for three lines; wavelength offset limited to +/-5 A; doublet ratios fixed to 3
- 2024A&A...683A..64A: seven shell parameters: v_exp, N_HI, tau_d, T, z_sys, EW, FWHM
- 2020MNRAS.496..875R: L_FIR(8-1000)/L_FIR(40-400) ~ 1.4 on average
- 2026MNRAS.549ag931B: WSU candidate instantaneous sideband bandwidths of 8 GHz (3 tunings) and 14 GHz (2 tunings covering 67-115 GHz)
- 2020ApJ...902...37D: Gaussian smoothing sigma = 1.0 pixel; moment-zero S/N cut of 1.0
- 2026ApJ..1003..206S: native: Briggs robust=0.5, no uv taper; tapered: robust=2.0 with Gaussian taper FWHM=1.0 arcsec
- 2026ApJ..1003..206S: channels within 500 km/s of the quasar [CII] line centre flagged to avoid boosting the continuum
- 2025ApJ...985L...8U: velocity width 500 km/s; limits at 3 sigma; adopted z_[OIII]=3.0851 for QG2 (most dominant peak)
- 2024A&A...690L..16J: lines at 222.52 GHz (S/N=11 or 23) and 223.27 GHz in Band 6; 95.4 GHz in Band 3
- ... 6 more

### Assumptions (bibcode: value)
- 2025A&A...693A.237I: Single Gaussian line profile (double Gaussian for CRISTAL-22a)
- 2025A&A...693A.237I: 2D exponential disk profile (n = 1); standard LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7
- 2025A&A...693A.237I: Single Sérsic n = 1 profile for UV (except CRISTAL-13) and circular exponential disk for FIR continuum
- 2025A&A...693A.237I: Two concentric exponential disk components for double-component fit; average redshift z = 5.22
- 2025A&A...693A.237I: Average redshift z = 5.22
- 2020MNRAS.499.5136C: Finder optimised for point-source emission; tapered cubes used to detect extended emission
- 2020MNRAS.499.5136C: 2D Gaussian surface brightness; [CII] and [OIII] major axes 0.8'' and 0.45''; random axis ratio 0.1<b/a<1.0 and position angle
- 2020MNRAS.499.5136C: Both luminosities 5×10^8 L⊙; fluxes 0.43 and 0.21 Jy km s−1; width 200 km s−1
- 2020MNRAS.499.5136C: Exclude other overlapping sources with multi-component morphology
- 2020MNRAS.499.5136C: For upper limits, [CII] extent about twice UV extent
- 2020MNRAS.499.5136C: Conditional MS0451-H correction assumes [CII] as extended as the UV region
- 2020MNRAS.499.5136C: Kennicutt:2012 SFR relations; kroupa:01 IMF
- 2020MNRAS.499.5136C: Use UV+FIR SFR for comparison with the local relation
- 2020MNRAS.499.5136C: Uniform total SFR based on UV and IR luminosities
- 2020MNRAS.499.5136C: Interpret line ratios through ISM properties including PDR covering fraction, density, metallicity and C/O abundance
- 2018MNRAS.481.1976Z: [C II] emission follows an exponential disk with the optical size; a PSF model would underestimate fluxes
- 2018MNRAS.481.1976Z: Stack size fixed to the average optical size of the sources entering the stack
- 2018MNRAS.481.1976Z: Chabrier IMF; flat LCDM with Om = 0.3, OL = 0.7, H0 = 70
- 2018MNRAS.481.1976Z: alpha_CO slope of -1 or -2 would not change conclusions
- 2018MNRAS.481.1976Z: Starbursts defined as > 4 times above the main sequence
- 2018MNRAS.481.1976Z: SFR estimates from the literature taken at face value
- 2025ApJ...987L..37W: Host disk size of 5 kpc
- 2025ApJ...987L..37W: [C I]-to-H2 abundance ratio X_[CI] = 3e-5
- 2025ApJ...987L..37W: [C I] is a good H2 tracer in the radiation fields of bright quasars, where the [C II]-H2 relation may not hold
- 2025ApJ...987L..37W: q = 1 and n = 1, which gives an upper limit on M_dyn^dis
- 2025ApJ...987L..37W: Clouds are virialized and dispersion-dominated
- 2025ApJ...987L..37W: Contamination from hotter dust (T >~ 60 K) is negligible at the cold-dust peak
- 2013A&A...559A..29C: SMG faint component fixed at 250 km/s
- 2013A&A...559A..29C: Td=65 K (SMG), 50 K (QSO); k~nu^1.5; Salpeter IMF; alpha_CO=0.6 with factor 2 systematic
- 2013A&A...559A..29C: Circular rotation, potential from disk mass, Sigma=Sigma0 exp(-r/r0), center and r0 from [CII] surface brightness
- 2021ApJ...908..235I: core component attributed to the host galaxy and used for the systemic redshift
- 2021ApJ...908..235I: SFR_[CII] is an upper limit because part of [C II] may come from the quasar narrow line region
- 2021ApJ...908..235I: high density limit n >> n_crit, giving a lower limit on M_out
- 2021ApJ...908..235I: 70% of [C II] arises from PDRs (factor 0.7)
- 2021ApJ...908..235I: projection correction averages to unity over all angles; entire extended structure assumed to be outflow
- 2021ApJ...908..235I: T_d = 35 K
- 2024A&A...690A.277M: [O III] broadening traces kinematically disrupted gas rather than the BLR.
- 2024A&A...690A.277M: Broad Balmer component is BLR emission; narrow Balmer component combines disc and outflow.
- 2024A&A...690A.277M: Case B coefficient 3.03 × 10^-14 cm^3 s^-1; Te = 10^4 K.
- 2019A&A...630A..59B: optically thin [CII], n>>n_crit, X_C+~1e-4, T=200 K, 0.7 PDR fraction
- 2021A&A...645A..21G: Fixed [O iii] doublet ratio 1/3.
- 2021A&A...645A..21G: Narrow [O iii] traces disk rotation; broader components trace non-circular motions.
- 2021A&A...645A..21G: Molecular outflow lies in the galaxy plane.
- 2021A&A...645A..21G: Use previously identified disk components to set a common rest frame.
- 2021A&A...645A..21G: Intrinsic Hα/Hβ =2.86; Calzetti attenuation law, R_V =3.12.
- 2021A&A...645A..21G: NLR gas temperature 10^4 K.
- 2021A&A...645A..21G: C =1; equal-density ionizing clouds.
- 2021A&A...645A..21G: NLR [O/H] =9.0; solar [O/H] ~8.86.
- 2021A&A...645A..21G: Fully ionized gas; electron temperature 10^4 K.
- 2019A&A...632A.106L: ionized gas at 10000 K
- 2019A&A...632A.106L: all tracers peak at same velocity per cloud
- 2019A&A...632A.106L: X'_CO = 2e20 cm-2 (K km/s)-1 for CO-bright H2; thermal pressure equilibrium by default
- 2021A&A...650A.117N: Galactic foreground E(B-V) = 0.01 mag, Milky Way extinction law (Pei 1992), R_V = 3.08
- 2015ApJ...801..123W: Symmetric line model
- 2015ApJ...801..123W: All dust heated by stars, not quasar; Chabrier IMF
- 2015ApJ...801..123W: [C II] gas in an inclined disk; BH mass uncertainty +0.3 dex (0.45 dex if Eddington-based)
- 2020MNRAS.496.2155Z: 20 Mpc common distance
- 2020MNRAS.496.2155Z: Pure star-forming Hα gives a lower SFR limit; adding composite regions gives an upper limit
- 2024A&A...689A.101C: Only physical bulk properties used; no fits with spectral lines, IR emission or redshift
- 2024A&A...689A.101C: Models taken from empirical literature rather than PDR or simulation-based models, to reduce assumptions
- 2024A&A...684A.107M: V_sys = +103 km s^-1
- 2024A&A...684A.107M: Radial velocity vector with homologous expansion at each point; molecular disk does not emit optically but absorbs optical emission behind it.
- 2020MNRAS.498.3624L: Alpha is kept fixed, so Delta F/F = -Delta mu/mu
- 2020MNRAS.498.3624L: [CII] and CO lines co-spatially distributed (similar widths)
- 2018MNRAS.476.4949D: LTE; local ISM 32S/34S = 22; solar 32S/33S=125, 32S/36S=4747
- 2016A&A...592A..83K: Disk gaps in mm opacity not included in the models
- 2025A&A...702A.276P: 10 km/s line width assumed for the HCN J=4-3 upper limit
- 2026ApJ..1003...26O: XO=3e-4, Te=1e4 K, fV=1/3, all O in O2+, He singly ionized
- 2025A&A...694A.171M: Sources may be extended, so a source-centred aperture is used
- 2025A&A...694A.171M: Gaussian line profile
- 2025A&A...694A.171M: [CII] defines the systemic redshift
- 2025A&A...694A.171M: Optically thin dust; fixed T_dust and beta from literature
- 2025A&A...694A.171M: Cosmology H0=67.8, OmegaM=0.3, OmegaL=0.7
- 2025A&A...694A.171M: Unresolved system, dispersion dominated (sigma = 0.75 FWHM); inclination from literature median
- 2025A&A...694A.171M: Positive emission = real sources + noise; negative emission = noise only
- 2020MNRAS.494.5542R: Lens mass model fixed to R15a (SIE with external shear)
- 2020MNRAS.494.5542R: [O I] lines assumed to follow the FIR continuum surface brightness distribution
- 2020MNRAS.494.5542R: Solar metallicity PDRToolbox model, semi-infinite slab, uniform density
- 2020MNRAS.494.5542R: Optically thin tracers (FIR, [C II]) predictions doubled for multi-sided illumination; CO lines optically thick
- 2020MNRAS.494.5542R: PDR surface temperature taken as the gas temperature in the [C II]-emitting layer; [C II] optically thin; dense gas above critical density
- 2019ApJ...876..112R: circularly symmetric Gaussian profile
- 2019ApJ...876..112R: exponential disc (Sersic n=1)
- 2019ApJ...876..112R: linear mapping 160-um to SFR; no AGN contribution; universal IMF
- 2019ApJ...876..112R: CO(3-2) optically thick, FIR continuum thin; [CII] optically thin adopted
- 2025A&A...696A..88W: Doublet ratios fixed by atomic physics ([O III] and [N II] = 3; [S II] ratio limited to 0.4375-1.4484; [O II] doublet ratio = 1)
- 2025A&A...696A..88W: Lines detected in Band 8 are [C II] at redshifts similar to the central HzRGs
- 2025A&A...696A..88W: Gravitational interaction with the central AGN ignored; masses from unresolved sizes are upper limits (dispersion) or lower limits (rotation R)
- 2025A&A...696A..88W: Case B recombination
- 2025A&A...696A..88W: Optical continuum flux proportional to stellar mass when deriving the detection limit
- 2015MNRAS.449.2883G: same filling factors for [CII] and CO
- 2015MNRAS.449.2883G: Tex,CO(1-0)=Td~35 K
- 2015MNRAS.449.2883G: alpha_CO = 0.8 (and 2) Msun/(K km/s pc2); 70% of [CII] from PDRs
- 2020MNRAS.492.3194S: Halpha and [N II] come from the same gas (tied velocity and width)
- 2020MNRAS.492.3194S: Offsets between outflow and FIR may reflect differential dust obscuration of [O III]
- 2024A&A...686A..46E: Broad component is outflow; n_H ~ n_e
- 2017ApJ...836....8T: Inclined rotating disk, v_circ = 0.75 FWHM/sin i; Td=47 K, beta=1.6; gas-to-dust 100
- 2017ApJ...836....8T: Host mass grows only via star formation at CE01-based SFR
- 2021ApJ...909..204F: FIR and 7.7 μm PAH emission are star-formation diagnostics
- 2018ApJ...853..111J: Carbon abundance (C/H)SMC = 2.8e-5
- 2023MNRAS.519.2030H: Spectroscopic redshift z = 0.3214, CO(3-2) rest frequency = 345.796 GHz
- 2025PASJ...77..432U: F444W (rest-frame ~1 um) taken as a tracer of stellar mass distribution
- 2025PASJ...77..432U: Rotation velocity approximately equals circular velocity (rotation supported, Vrot/sigma=8.8)
- 2025PASJ...77..432U: Non-axisymmetric gas distribution handled by renormalising flux per spatial pixel to the observed intensity map
- 2025PASJ...77..432U: CO(1-0) profile same as [CII]; CO is not well resolved by JVLA
- 2021A&A...646A..26B: [C II] emitting region may be 2-3 times larger than the UV component, motivating the 0.5'' taper
- 2021A&A...646A..26B: Target unresolved with native beams; no continuum subtraction
- 2021A&A...646A..26B: UV magnitude error bars assumed symmetric and equal to the larger error
- 2021A&A...646A..26B: Constant SFR; [C II] upper limit not included
- 2016Sci...352.1559I: T_dust = 40 K, beta = 1.5
- 2016Sci...352.1559I: Salpeter IMF 0.1–100 Msun, constant SFH, Calzetti law
- 2024ApJ...972..116I: [CII] excited primarily by star formation (SFRs are upper limits if quasar contributes)
- 2024ApJ...972..116I: Flat LCDM H0 = 70 km/s/Mpc, Omega_M = 0.3, Omega_Lambda = 0.7
- 2024ApJ...972..116I: [CII] emission arises from thin rotating disks; inclination from deconvolved axis ratio
- 2024ApJ...972..116I: Wing is due to outflow (symmetric wing disfavors unseen companions); 70% of [CII] from neutral PDRs; constant outflow velocity
- 2013ApJ...773...44W: Tdust=47 K, beta=1.6 (mean of high-z FIR-luminous quasars)
- 2020ApJ...903...34A: SFR-L[CII] relation calibrated for z>5 galaxies applied to the quasar host
- 2026A&A...707A..77H: Metallicity for the outflow taken from the quiescent line components because strong-line metallicities cannot be applied to shock/LINER-like gas; [O/H]_sun = 8…
- 2026A&A...707A..77H: Quoted ionized masses are lower limits because of the electron density floor
- 2019A&A...631A..78S: X_C+=1.4e-4, T=200 K, n>>ncrit~3e3 cm^-3, constant outflow velocity
- 2022ApJ...941...47S: Telescope background is stable and dominates total flux over weak target flux
- 2022ApJ...941...47S: Circular ring rotating with constant angular velocity Omega; distance = 31.1 Mpc (70 pc/arcsec)
- 2017A&A...602A..49H: equal [CII] and CO filling factors; Tex,CO = dust temperature
- 2017A&A...602A..49H: each galaxy is a single PDR component; FIR not halved
- 2026ApJ..1004..194F: Threshold and iteration limits do not affect data quality because no bright sources are in the fields
- 2026ApJ..1004..194F: [N II] line width equal to the [C II] FWHM
- 2026ApJ..1004..194F: L_IR integrated over rest-frame 8-1000 um
- 2026ApJ..1004..194F: R_ion range 1.5-5.7 from Witstok2022 models; [N II] arises only in ionized gas
- 2026ApJ..1004..194F: Grain and gas metallicity scaled to JWST oxygen abundances 12+log(O/H) = 8.45, 8.05, 8.63, 8.50; Habing flux definition of G0
- 2026ApJ..1004..194F: Same metallicity for ionized and neutral gas (JWST abundances from ionized-gas lines)
- 2021ApJ...917...99Y: Singular isothermal ellipsoid (SIE) lens mass distribution and single Sérsic source profile
- 2021ApJ...917...99Y: Default lensing model mapping from image plane to source plane
- 2021ApJ...917...99Y: LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7
- 2021ApJ...917...99Y: Dust continuum traces molecular gas (for CO magnification) and SFR surface density
- 2019ApJ...887...40W: T_dust=47 K, beta=1.6; FIR 42.5-122.5 um; H0=71, Om=0.27, OL=0.73
- 2019ApJ...887...40W: Simple circular rotating disk
- 2024ApJ...977L..46B: Dispersion-dominated system (no rotation in channel maps); dynamical mass comparable to stellar mass or bulge mass for the main-sequence and local-relation com…
- 2024ApJ...977L..46B: Flat LCDM, H0 = 70 km/s/Mpc, Omega_M = 0.30
- 2024ApJ...977L..46B: Dust-obscured star formation dominates for massive galaxies; host galaxy contribution does not vary on scales of months
- 2015ApJ...807..180W: Td=30 K, beta=1.6; no CMB correction
- 2020ApJ...900..131L: Solar abundances (Asplund09); LTE
- 2026ApJ..1002..100T: Elevated ratio interpreted as CO dissociation by the AGN-driven ionized outflow; southern cone not detected in HST because of obscuration
- 2019ApJ...870...65I: Extinction correction via Balmer decrement
- 2019ApJ...870...65I: M_BH = 6.7e8 Msun
- 2021MNRAS.500.3802H: Systemic velocity defined from GAMA spectroscopic redshift
- 2019A&A...621A..83S: accretion efficiency 0.1
- 2024A&A...687A..35R: [CII] emission traces the total gas distribution, so gas surface density is proportional to [CII] surface brightness
- 2024A&A...687A..35R: discs razor-thin, inclination from ellipticity (cos^2 i = 1 - eps)
- 2024A&A...687A..35R: gas disc scale length R_gas = R_eff,[CII]/1.678 for an exponential profile
- 2024A&A...687A..35R: isotropic velocity ellipsoid and disc thickness constant with radius
- 2024A&A...687A..35R: gas follows an exponential razor-thin disc with the [CII] scale length
- 2024A&A...687A..35R: spherical NFW halo
- 2024A&A...687A..35R: stellar component spherical with Sersic light profile
- 2023Natur.617..261K: Relevant velocity interval for absorber association is ±700 km s^-1 around each absorber (contiguous 2280 km s^-1 interval)
- 2023Natur.617..261K: CO(6-5) luminosity function at z = 2 also applies to CO(7-6) and CO(8-7)
- 2023Natur.617..261K: Flat ΛCDM cosmology with Ω_Λ = 0.69, Ω_M = 0.31, H_0 = 67.7 km s^-1 Mpc^-1
- 2023Natur.617..261K: log10(SFR) = -7.06 + 1.0 log10(L_[C II] / L_sun)
- 2023Natur.617..261K: νL_ν / L_IR = 0.13 at ν = 1900 GHz (modified blackbody with β = 1.8, T_dust = 41 K)
- 2023Natur.617..261K: SFR_IR (M_sun yr^-1) = 1.01 x 10^-10 L_IR (L_sun) for Chabrier IMF
- 2023Natur.617..261K: SFR_FUV (M_sun yr^-1) = 0.72 x 10^-28 L_ν (erg s^-1 Hz^-1)
- 2017ApJ...851..145M: Offset is due to astrometry errors, not physical
- 2017ApJ...851..145M: LCDM with Om=0.70, OL=0.30, H0=70
- 2017ApJ...851..145M: CMB contribution removed; [CII] line contamination negligible
- 2024ApJ...971...17F: Gaussian line profiles for simplicity and efficiency.
- 2024ApJ...971...17F: Overlapping positive and negative velocity contours can represent emission from both cones.
- 2024ApJ...971...17F: Distance = 23.7 Mpc; apply literature galaxy subtraction and reddening correction.
- 2024ApJ...971...17F: [O III] luminosity represents an average over at least 2,000 years.
- 2012ApJ...752L..30W: beta = 1.5; dust T = 35 K (SMG), 60 K (quasar); cosmology (0.73, 0.27, 0.71)
- 2021A&A...654A..37D: Flat cosmology: ΩM = 0.28, ΩΛ = 0.72, H0 = 70 km s−1 Mpc−1
- 2021A&A...654A..37D: For comparison samples: L_IR/L_FIR ≃ 1.7 where needed; ALPINE line and continuum sizes assumed equal
- 2021A&A...654A..37D: Resolved emission used to avoid AGN contamination; Kroupa IMF
- 2021A&A...654A..37D: Exclude SFR estimates from assumed stellar histories to avoid an intrinsic SFR–stellar-mass correlation
- 2024MNRAS.528.6768H: Intrinsic Hα/Hβ = 2.86; Milky Way extinction curve
- 2024MNRAS.528.6768H: Chabrier IMF
- 2019PASJ...71..109H: Flat LCDM, Om=0.272, H0=70.4
- 2022ApJ...928..150T: For Level 3 data, the source is assumed to be smaller than the FIFI-LS beam
- 2025A&A...699A..80H: JvM correction not applied; impact expected to be minimal after deep cleaning.
- 2025A&A...699A..80H: Flat universe: ΩM = 0.3, ΩΛ = 0.7, H0 = 70 km s−1 Mpc−1.
- 2025A&A...699A..80H: T_dust = 50 K.
- 2025A&A...699A..80H: Z = 0.2 Z⊙ expected for CRISTAL-13 in the photo-evaporation model comparison.
- 2025A&A...699A..80H: Interpreting [C ii]/FIR as photoelectric heating efficiency assumes dust photoelectric heating dominates and [C ii] is the main cold-neutral-gas coolant.
- 2021ApJ...914...36I: [C II] excited primarily by star formation; De Looze et al. (2014) local H II/starburst calibration log(SFR_[CII]) = -7.06 + 1.0 * log(L_[CII]/L_sun)
- 2021ApJ...914...36I: Circular Gaussian geometry for uv visibility models
- 2021ApJ...914...36I: Constant outflow; high-density limit (n >> n_crit ~ 3 x 10^3 cm^-3); PDR fraction = 0.7; X_C+ = 1.4 x 10^-4; T_ex = 200 K; total multi-phase outflow rate ~3x (…
- 2021ApJ...914...36I: Concentric tilted rings with uniform inclination and PA; spherical Plummer gravitational potential for bulge; V_rot at scale length (~220 km s^-1) equals halo …
- 2016ApJ...832..151P: Gaussian spatial profiles
- 2016ApJ...832..151P: Solar abundances (N11), Orion-like dust
- 2016ApJ...832..151P: Optically thin lines; C+/N+ ~1.8
- 2024ApJ...977..190X: Radiative processes dominate over non-radiative mechanisms.
- 2024ApJ...977..190X: All line emission arises in neutral or molecular gas; HII contribution to [CII] ignored.
- 2024ApJ...977..190X: FIR dust continuum and fine structure lines primarily originate in the star-forming PDR.
- 2014ApJ...792...34O: [CII] line width of 40 km/s
- 2023ApJ...942L..24K: Kewley et al. (2006) strong-line AGN diagnostic classifications
- 2023ApJ...942L..24K: X-Shooter Spectral Library DR2 stellar templates
- 2024ApJ...966..228R: solar 12+log(O/H)=8.69
- 2019ApJ...880..157D: Optically thin [CII], LTE, C/H=2.95e-4, gas-to-dust 100 for comparison, Tdust=35 K adopted
- 2022ApJ...934..173S: eDIG is negligible in high EW(Halpha) (>14 Angstrom) group and non-negligible in low EW(Halpha) group; Cardelli et al. (1989) extinction curve, intrinsic Halph…
- 2024A&A...689A.145S: Dust and gas have disk-like geometries, share the same inclination and are optically thin (for the axis-ratio comparison)
- 2024A&A...689A.145S: T_dust = 45 K modified blackbody with beta_dust = 1.5, chosen to roughly describe the average SED of z > 4 star-forming galaxies; limits rise 1.7x and 2.4x for…
- 2024A&A...689A.145S: Optically thin [C ii], negligible background, collisions dominated by atomic hydrogen, maximal excitation (T >> 90 K, n >> 1e3 cm^-3) and solar abundance; mass…
- 2022A&A...665A.107T: For M_HI: n >> n_crit (n_crit ~ 3 x 10^3 cm^-3), C+ abundance X_C+ ~ 10^-4, gas temperature T = 200 K.
- 2022A&A...665A.107T: Flat rotation curve for Q_gas calculation; inclinations i > 30 deg ruled out because M_dyn must exceed M_H2 = 4.2 x 10^10 M_sun; inclinations i < 20 deg ruled …
- 2022A&A...665A.107T: Time-averaged expelled shells or clumps geometry (Rupke et al. 2005); PDR parameters T = 200 K, X_C+ = 10^-4, n >> n_crit; L_bol = 3.13 x 10^47 erg s^-1.
- 2022A&A...665A.107T: For Serenity-18 upper limits: T_dust = 40 K, beta = 1.5, source size equal to clean beam, [CII] line width = 200 km/s, and SFR - L_[CII] relations from Carnian…
- 2016ApJ...833...67W: Negative candidates are all noise peaks; no absorption expected
- 2026ApJ..1002L..28Y: T_dust=47 K, beta=1.6, kappa=0.077 (nu/352 GHz)^beta
- 2026ApJ..1002L..28Y: Flat LCDM, Om=0.3, H0=70
- 2015A&A...576L...2S: Missing short-spacing flux negligible
- 2023MNRAS.519.1293D: Emission peak in HST F814W, GMOS broad Halpha peak, and ALMA CO(3-2) kinematic centre all correspond to the AGN position
- 2023MNRAS.519.1293D: T = 10,000 K for [S II] density calculation; bolometric correction of 600 for [O III]5007; distance from AGN equals projected distance for Regions 2 (2.8 x 10^…
- 2024A&A...686A..48N: L_bol = 1.15 L_IR; SFR = (1 - alpha_AGN) x 10^-10 L_IR (Chabrier IMF)
- 2022A&A...661A.136G: Chabrier (2003) IMF converted to Kroupa (2001) IMF by adding 0.15 dex
- 2025ApJ...981..135S: 5% absolute flux uncertainty included in photometric uncertainties
- 2025ApJ...981..135S: Calzetti (2000) dust attenuation law
- 2025ApJ...981..135S: Kroupa (2001) IMF from 0.1 to 300 M_sun and BPASS Delta log(alpha/Fe) = +0.6
- 2025ApJ...981..135S: Gas-phase metallicity identical to stellar metallicity
- 2025ApJ...981..135S: Plane-parallel geometry under constant pressure; electron density n_e ~ 200-400 cm^-3; T_e = 1.2x10^4 K for PyNeb n_e calculation
- 2021Sci...371..713L: Planck 2018 LambdaCDM cosmology (Omega_m = 0.315, Omega_Lambda = 0.685, H_0 = 67.4 km s^-1 Mpc^-1, 0.1'' = 657.7 pc at z = 4.7555); fully axisymmetric disk mod…
- 2021Sci...371..713L: [C II] radial profile traces cold gas disk; dust continuum radial profile traces stellar disk; spherical De Vaucouleurs bulge includes central SMBH (<10% mass)…
- 2018PASJ...70...36I: H0=70, OmegaM=0.3, OmegaL=0.7
- 2018PASJ...70...36I: Kroupa IMF; young stars heat [CII]; AGN contribution neglected; dispersion ~0.3 dex not in errors
- 2026ApJ..1000..312Z: X_C+ = 1e-4; mu = 1.4; broad component primarily AGN-driven
- 2021A&A...645A..33B: Ladder ratios from Carilli and Walter 2013; alternative ladders change L'CO(1-0) by factor >=2 lower or ~1.3 higher
- 2026MNRAS.549ag781K: Solar metallicity of the gas; broad Gaussian component represents outflowing gas
- 2017ApJ...849...91M: T_d = 47 K, beta = 1.6, optically thin
- 2019MNRAS.483.4586F: alpha_CO: 0.8 ULIRGs, 1.2 LIRGs, 4.4 others
- 2024ApJ...977L...9Z: Line expected within frequency range set by JWST NIRSpec/MIRI redshifts
- 2024ApJ...977L...9Z: Magnification-corrected SFR from SED fitting and Halpha
- 2024ApJ...977L...9Z: Hbeta luminosity inferred from Halpha assuming zero dust attenuation; relation does not evolve with redshift
- 2024ApJ...977L...9Z: Spherical geometry; virial radius equals the half-light radius
- 2024ApJ...977L...9Z: Sersic n = 1 and 1.5, axis ratios q = 0.3-0.7 in the alternative approach
- 2023MNRAS.521.1045R: Razor-thin disc (Z0 = 0) for fiducial models; constant disc thickness with radius for thick-disc test
- 2023MNRAS.521.1045R: Circular orbits with no large-scale radial or vertical motions; razor-thin disc (Z0 = 0) for fiducial fit; azimuthal surface density normalisation
- 2017ApJ...845..175J: Metallicity 1.0 or 0.1 Zsun; flat cosmology (0.692,0.308,0.678)
- 2017ApJ...845..175J: T_dust=30 K, beta=1.6, FIR 42.5-122.5 um, uniform across source
- 2024A&A...682A..54T: PDR L[CII]-to-gas mass conversion
- 2021ApJ...908...53W: Haro 11 as an analog for high-z quasar hosts
- 2021ApJ...908...53W: Flat cosmology: H0=68.5 km s−1 Mpc−1, ΩM=0.3, ΩΛ=0.7
- 2026A&A...707A.376C: Outflowing gas is fully ionized by the AGN (dust-free AGN clouds, dusty SF clouds with equal metallicity); constant flux density over time in each spaxel
- 2025A&A...701A..85K: Choice of decomposition is somewhat arbitrary and driven by data complexity and S/N; inclination fixed to 30 deg for all components (bracketed values are fixed)
- 2025A&A...701A..85K: Single modified blackbody with spectral index beta = 1.7; T_dust = 41 K for violet and red
- 2025A&A...701A..85K: Plotted errors do not include size uncertainties
- 2025A&A...701A..85K: Components may not be virialized, but estimates considered meaningful
- 2023A&A...673A.116K: Lens is at z = 0.632; companion magnifications assumed to be mu_comp-N = mu_comp-SW = 1
- 2023A&A...673A.116K: Emission in nearby companion sources is [C II] based on close spatial proximity to primary targets
- 2023A&A...673A.116K: Flat LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7; Chabrier IMF; Constant star formation history and Calzetti reddening l…
- 2023A&A...673A.116K: PDR conditions: X_C+ = 1.4 x 10^-4, T = 200 K, n >> n_crit
- 2019ApJ...876....1T: Plane-parallel slab PDRs; [CII] and dust optically thin, CO thick
- 2019ApJ...876....1T: Stellar metallicity lower than gas-phase by factor 5
- 2024ApJ...970....9B: Dust temperature 47 K, beta=1.6
- 2024ApJ...970....9B: C+ abundance 1.4e-4 per H, T=200 K, n>>n_crit (lower limit)
- 2020ApJ...895...74N: [CII] traces systemic redshift
- 2024ApJ...961...71F: Dust emission co-spatial with the galaxy; dust temperature is the major uncertainty
- 2024ApJ...961...71F: Narrow [C ii] associated with the UV-bright clump of radius 27 pc
- 2024ApJ...961...71F: Virial equilibrium for the narrow component
- 2023ApJ...945...69R: z = 7.212; rest-frame frequencies 3393.006 GHz ([O III] 88 μm) and 1900.54 GHz ([C II] 158 μm)
- 2023ApJ...945...69R: H_0 = 70 km s^-1 Mpc^-1, Ω_M = 0.3, Ω_Λ = 0.7, 1" = 5.134 kpc at z = 7.212
- 2019ApJ...871...85L: 30% of [CII] from non-PDR; CO intensities multiplied by 2
- 2024A&A...683A.169W: 2 Zsun Groves model grids chosen as indicated by [N II]/Halpha
- 2013ApJ...763..120C: [CII]/H = 1.4e-4; conical or bi-conical geometry; n >> n_c
- 2024MNRAS.535..729P: Intrinsic line ratios [N II] 6583 / [N II] 6548 = 3.05 and [O III] 5007 / [O III] 4959 = 2.98 from Storey & Zeippen (2000)
- 2017FrASS...4...49T: Inclination from major-to-minor axis ratio of [C II] region
- 2025ApJ...991L..38U: Adopted aperture misses ~10% of total flux based on curve-of-growth analysis
- 2025ApJ...991L..38U: SMC extinction curve with R_V = 2.74; Case B recombination with initial ne = 100 cm^-3 and Te = 10^4 K; Galactic extinction negligible; Te([O II]) = 0.7 * Te([…
- 2025ApJ...991L..38U: A_V = 0 outside the 3sigma detection region of Halpha and Hbeta
- 2025ApJ...991L..38U: n_O++,i = n_e,i * 10^-4 (12 + log(O++/H+) = 8); 10% absolute flux calibration uncertainty on both [O III]5008 and [O III]88
- 2022MNRAS.515.1751W: Antenna efficiency factor η ~ 0.7 (A_eff ~ 80 m^2 for 12-m dishes)
- 2022MNRAS.515.1751W: COS-2987030247 is unresolved in [N II] 205 μm
- 2022MNRAS.515.1751W: Zanella et al. (2018) calibration holds at z ~ 7
- 2022MNRAS.515.1751W: 1D plane-parallel ionisation-bounded nebula; Salpeter IMF (1-100 M_sun) with interacting binaries; Orion-like graphite and silicate grains; turbulent velocity …
- 2016ApJ...816...37V: Td=47 K, beta=1.6, tau<<1 at lambda>40 um; Kroupa IMF; emission powered by star formation
- 2024A&A...682A.166F: Pure AGN radiation, spherical covering factor unity, constant density, T_BB=1e6 K, alpha_uv=-0.5, alpha_x=-1, cosmic-ray background included
- 2023MNRAS.519.5807D: Cosmology: H_o = 71 km s^-1 Mpc^-1, Omega_m = 0.27, Omega_lambda = 0.73; modified black-body with beta = 1.2
- 2024A&A...682A..24A: Non-detections may be [CII]-faint or have redshifts outside the scan range, so are excluded
- 2024A&A...682A..24A: [CII] calibration holds for massive main-sequence galaxies at z~7; molecular gas dominates the baryon budget at z>6
- 2024A&A...682A..24A: Dust temperature 46 K for L_IR from a single continuum measurement
- 2024A&A...682A..24A: alpha_[CII] ~ 30 Msun/Lsun; uncertainties include the calibration uncertainty
- 2020Natur.584..201R: LCDM cosmology, H0 = 67.8 km/s/Mpc, Omega_m = 0.308, Omega_Lambda = 0.691
- 2020Natur.584..201R: lens is a cored elliptical power-law profile plus external shear
- 2020Natur.584..201R: NFW halo with fixed concentration c = 3.06 (mean at z = 4.22 for halo masses 1e10-1e13 Msun)
- 2020Natur.584..201R: gas disk thickness independent of radius, thin, exponential surface density
- 2020Natur.584..201R: alpha_[CII] uniform prior within +/-3 s.d. around mean 30 Msun/Lsun (range 3.8-238)
- 2018ApJ...854...97D: Single modified blackbody, T_dust=47 K, beta=1.6; Planck15 cosmology
- 2018ApJ...854...97D: T_dust=47 K
- 2024A&A...690A.232S: Photoionized-gas mm emission is free–free emission.
- 2020ApJ...897L..14Y: T_d = 47 K, beta = 1.6, CMB effect included
- 2025MNRAS.537.1163A: Common centre set at the shared stellar and dust peak
- 2025MNRAS.537.1163A: Radial flows not modelled (vrad = 0); locally axisymmetric model
- 2021ApJ...909..130R: Magnification factors mu = 43, 25, and 16 for R = 1, 2, and 3 kpc apertures (main arc contains 95% of total flux); flat LambdaCDM cosmology with Omega_m = 0.31…
- 2021ApJ...909..130R: Primary beam response approximated by a Gaussian.
- 2021ApJ...909..130R: Uniform ISM, 1D plane-parallel geometry, instantaneous starburst with stellar rotation, no PDR contribution.
- 2021ApJ...909..130R: Magnification mu = 16; CO line ratio r_2/1 = 0.6; Galactic alpha_CO = 4.4 M_sun/(K km s^-1 pc^2); M_H2(M20) = 132 x L_[CII]^0.97; M_H2(Z18) = 30 x L_[CII].
- 2018ApJ...867..140L: T_dust = 41 K, beta = 1.5, bolometric factor 1.91, Kennicutt 1998 SFR
- 2018ApJ...867..140L: Lens within 0.2 arcsec of HST optical centroid; no external shear
- 2014ApJ...795....5O: M82 CO ladder; Iono+2009 L'CO-LIR relation; Td=35 K, beta=1.5
- 2020ApJ...900...37E: T_dust=47±3 K, beta=1.6±0.1, kappa=0.77(nu/352GHz)^beta cm2/g
- 2025ApJ...988...19S: H0=70, Omega_m=0.3, Omega_Lambda=0.7 cosmology
- 2025ApJ...988...19S: Dispersion-dominated; [OIII] radius equals the rest-UV effective radius
- 2025ApJ...988...19S: Flat underlying continuum for the F770W excess of 27.5 +/- 5.6 nJy
- 2025ApJ...988...19S: Higher densities or older stellar ages would give higher metallicity (up to solar)
- 2021A&A...653A.111R: A velocity separation <= 500 km/s indicates a gravitationally bound system
- 2021A&A...653A.111R: Stellar mass of the system splits into primary and secondary with mass ratio mu = 4 as the major/minor threshold
- 2021A&A...653A.111R: 12% of the [CII]-ratio-only subsample is assumed to be minor mergers (from the 7 of 8 sources with mu_K < 4)
- 2017ApJ...837..146V: T_gas = T_dust; Td = 47, 41 or 30 K; constant dust temperature
- 2014A&A...565A..59D: [CII] traces molecular gas kinematics
- 2025ApJ...995..150K: D_L = 65862.5 Mpc at z=6.60 for luminosity conversion
- 2025ApJ...995..150K: Atomic HI gas mass ignored
- 2025ApJ...995..150K: Solar 12+log(O/H)=8.69 and metal mass fraction 0.0134; primordial He fraction 0.2485
- 2025ApJ...995..150K: n_e = 100 cm^-3 (PRISM cannot resolve [OII] doublet)
- 2021Sci...372.1201T: Thin disk relation q = cos(i) used to convert dust continuum axis ratio to inclination
- 2021Sci...372.1201T: Polar coordinate center is the peak intensity pixel in the [C II] image
- 2021Sci...372.1201T: [C II] intensity distribution traces total gas surface density
- 2019ApJ...881..124M: MASOSA conservative limit assumes 200 km/s width and ~0.7'' beam
- 2024A&A...684A..56K: Other lines follow bulk kinematics of [CII]
- 2025ApJ...985..243B: [CII] luminosity traces SFR via the Lagache et al. relation; the threshold depends on this calibration choice
- 2025ApJ...985..243B: C+ abundance per hydrogen atom 1.4e-4
- 2025ApJ...985..243B: Gas density equal to the critical density; gas temperature 100 K
- 2023MNRAS.518.3183L: Vanilla LambdaCDM cosmology with Omega_m = 0.3, Omega_Lambda = 0.7, H_0 = 70 km s^-1 Mpc^-1
- 2023MNRAS.518.3183L: Independent centering of HST and [CII] profiles removes residual systematic astrometric offsets
- 2018ApJ...859...12G: remaining FIR fraction originates from the annulus
- 2024ApJ...970...30M: Rotating gaseous disk made of concentric rings, convolved with the beam
- 2024ApJ...970...30M: Single plane-parallel PDR slab; CO luminosities doubled for optical thickness; no optical-thickness correction to [C II] and FIR
- 2024ApJ...970...30M: Locally calibrated alpha_CO(Z) relation applies; result judged unphysical
- 2022MNRAS.515..678B: Maximum thermalized CO SLED profile where velocity-integrated fluxes increase with J^2
- 2022MNRAS.515..678B: 1-sigma uncertainty in sub-mm photometric redshifts is typically 13% or 7% in Delta z / (1+z)
- 2022MNRAS.515..678B: Remove frequency regions opaque under normal observing conditions (PWV > 0.5 mm, transmission > 80% of the peak)
- 2022MNRAS.515..678B: Average redshift of HerBS sample is z_bar approx 2.5 and SPT sample is z_bar = 3.5
- 2022MNRAS.515..678B: Photometric redshift uncertainty Delta z / (1+z) approx 7%
- 2019ApJ...874...27T: Bruzual & Charlot 2003, Chabrier IMF 0.1-100 Msun; Calzetti/SMC/MW extinction; Inoue14b IGM transmission
- 2024ApJ...964..146F: Continuum emission assumed unresolved; [OIII] assumed spatially unresolved
- 2024ApJ...964..146F: Te from direct method (NIRSpec); same emitting region for the two lines
- 2021ApJ...918...69U: Cosmology: Omega_m = 0.3, Omega_Lambda = 0.7, H_0 = 70 km s^-1 Mpc^-1
- 2021ApJ...918...69U: Modified blackbody radiation with beta = 1.8 and T_d = 40 K for dust mass
- 2021ApJ...918...69U: Chabrier IMF and ALESS SMG SED templates for L_IR and SFR_IR
- 2021ApJ...918...69U: Brightness temperature ratio r_41 = 0.61 +- 0.13 and CO-to-H2 conversion factor alpha_CO = 3.6 M_sun (K km s^-1 pc^2)^-1
- 2021ApJ...918...69U: NFW mass profile with spherical geometry; Case-B recombination and Chabrier IMF for UV SFR and Ly-alpha luminosity
- 2019ApJ...870...80L: constant flux-to-luminosity ratio, i.e. constant dust temperature
- 2019ApJ...870...80L: [CII] traces gas; M_g=1.5e11 Msun; a=sqrt(3); sigma_r used as upper limit on turbulent dispersion
- 2025PASJ...77..139I: SFR converted to L_FIR assuming Salpeter IMF for the local relation
- 2025PASJ...77..139I: Lines assumed to arise from PDRs, not XDRs, for the subsequent modeling
- 2025PASJ...77..139I: Plane-parallel PDR geometry; Z/Zsun = 1.0; [C II], [O I] and dust co-spatial; [C II] purely from PDR after removing 17% H II fraction
- 2025PASJ...77..139I: [O I] emission arises in the same regions as [C II]
- 2020ApJ...904..131N: Gaussian line profile when correcting for the tails beyond 1.2xFWHM (factor 1.19)
- 2020ApJ...904..131N: Recomputed weights comparable across datasets so no single source dominates the average
- 2020ApJ...904..131N: Extended component described by an exponential function
- 2018ApJ...869L..22W: O/H=5.9e-4, most oxygen doubly ionized, gas-to-dust ~100, constant SFR
- 2025ApJ...993..204H: [OIII]5007/4959 = 2.98; [NII]6584/6548 = 2.94; equal widths within each doublet
- 2025ApJ...993..204H: Referenced stellar IMF, dust attenuation law, and IGM attenuation model
- 2025ApJ...993..204H: Two regions share metallicity and O32; region 1 is lower density
- 2023ApJ...952...48H: CO emitting region size does not exceed that of [CII] emission (covered by the uv-tapered beam)
- 2023ApJ...952...48H: X[CI]/X[H2] ~ 1.6 x 10^-5 (and up to 10x higher conversion factor at low Z)
- 2023ApJ...952...48H: HII region contribution to [CII] is ~30% and CMB attenuation factor for [CII] is f_CMB = 0.5 - 1.0
- 2023ApJ...952...48H: Gas is predominantly in the molecular phase for the dust-based estimate
- 2023ApJ...952...48H: Divide optically thin emission luminosities by a factor of 2 for spherical cloud geometry; PDR fraction of [CII] is 70%
- 2018A&A...611A..22S: Solar metallicity with factor two uncertainty; alpha_CO = 2
- 2024ApJ...963...19N: [CII] emission traces the rotating disc; OH absorption strength also depends on the background continuum brightness, so morphologies need not match exactly
- 2022A&A...660A..14R: Redshift obtained from the peak of the Ly-alpha line can be corrected using the observed velocity offset distribution between Ly-alpha and [CII]
- 2022A&A...660A..14R: Lambda-CDM cosmology with H_0 = 70 km s^-1 Mpc^-1, Omega_m = 0.3, Omega_Lambda = 0.7; Chabrier (2003) IMF
- 2022A&A...660A..14R: SFR_TOT = SFR(UV) + SFR(IR), where SFR(IR) for continuum-undetected galaxies comes from the IRX-beta relation of Fudamoto et al. (2020); Chabrier IMF (De Looze…
- 2019PASJ...71...71H: T_d = 50 K, beta_d = 1.5 for literature sample
- 2019PASJ...71...71H: Constant SFH; Calzetti attenuation same for stellar and nebular; Chabrier IMF 0.1-100 Msun
- 2024A&A...690A.255D: Flat LCDM with Planck 2016 parameters
- 2024A&A...690A.255D: Cold-phase carbon mass is a proxy for [CII] luminosity; no radiative transfer
- 2023A&A...673A.157D: All lines have the same Gaussian width of 375 km/s as [C II]
- 2023A&A...673A.157D: Gas-to-dust ratio delta_g/d = 100, alpha_CO = 0.8 M_sun (K km s^-1 pc^2)^-1, CO line ratio r_71 = 0.38 (for mass) or 0.20 (inferred from dust), T_ex = T_gas, Z…
- 2018Natur.556..469M: alpha_CO = 0.8, r41 = 0.41, helium factor 1.36, SFR/S870 = 150±50
- 2025ApJ...987...61R: [C II] luminosity multiplied by 3/4 (25% ionized gas contribution); [O I] 63 μm luminosity multiplied by 2 (optically thick spherical clouds); constant dust te…
- 2025ApJ...987...61R: Identical uniform-density spherical clouds illuminated externally by uniform FUV field G; n_H ~ n_H2; solar abundances
- 2021A&A...652A.128J: stacking positions from catalogue coordinates; line aligned using catalogue redshift and [C II] rest frequency
- 2021A&A...652A.128J: L[CII] formula of Solomon and Vanden Bout 2005
- 2021A&A...652A.128J: sub-solar metallicity of the sample
- 2016MNRAS.462L...6K: T = 35 K, beta = 1.6, Chabrier IMF, CMB correction 14-20% missed continuum
- 2025A&A...701A..31P: Bruzual and Charlot 2003 models, Chabrier IMF, Calzetti attenuation law, Draine 2014 dust emission
- 2025A&A...701A..31P: Solar and 0.29 Zsun metallicity cases
- 2025A&A...701A..31P: System near relaxation, not rotation-dominated; treated as an upper limit
- 2020MNRAS.494.4090C: High-SNR CO widths define the velocity range for both fine-structure lines.
- 2020MNRAS.494.4090C: Metallicity grids: log(n) = 1.5 or 3; log(U) = -3.5.
- 2020MNRAS.494.4090C: L_FIR ∝ T_dust^4
- 2017ApJ...834L..16U: cosmology Om=0.3, OL=0.7, H0=70
- 2024A&A...686A.156D: Λ-CDM: h0=0.7, ΩΛ=0.3 and Ωm=0.3, as printed.
- 2024A&A...686A.156D: α[CII] = 31 M⊙/L⊙.
- 2024A&A...686A.156D: 158 μm continuum represents obscured star formation.
- 2024A&A...686A.156D: LIR/L158 = 1/0.113; κIR = 1.47×10−10 M⊙/L⊙, in the printed units.
- 2024A&A...686A.156D: An offset broad component can indicate an outflow, but an infalling merging object can also produce an additional component.
- 2020ApJ...904..130V: modified blackbody T_d=47 K, beta=1.6; Kroupa IMF; L_TIR=1.41 L_FIR; SED systematic factor ~2-3
- 2020ApJ...904..130V: candidates with |dv|<2000 km/s taken as [C II] companions
- 2020ApJ...904..130V: single dust temperature everywhere
- 2018Natur.557..392H: mu=10 fiducial
- 2024A&A...684A..33K: CO(2–1) emission has the same linewidth as [C II] and the systemic velocity of the other CO transitions
- 2024A&A...684A..33K: CO(2–1) line width equals the [C II] width (highest S/N prior)
- 2024A&A...684A..33K: CO(2–1) emission has the same size as the [C II] emission
- 2024A&A...684A..33K: ULIRG-like alpha_CO=0.8 (alpha_CO,tot = alpha_CO,intr / f_CMB with the CMB correction)
- 2021ApJ...921...97J: Velocity separation of ~750 km s^-1 between W and E based on [CII] observations
- 2021ApJ...921...97J: Molecular lines share the same kinematic profile as the [CII] template; unresolved ATCA CO(3-2) flux distributed between W and E by scaling to CO(6-5); flat La…
- 2017ApJ...850..108W: Td=47 K, beta=1.6, Chabrier IMF, all dust heated by star formation
- 2025PASJ...77.1163H: Mean [C II] redshift z = 6.2 for flux to luminosity conversion
- 2025PASJ...77.1163H: Flat Lambda-CDM with Omega_M = 0.3, Omega_Lambda = 0.7, h = 0.7
- 2025PASJ...77.1163H: Line widths follow the observed L[CII]-FWHM correlation; local LF shape applied at high z
- 2025PASJ...77.1163H: All sources in the datacube are [C II] emitters and no other lines are detected
- 2021ApJ...907..122M: Typical SMG SEDs (Arp220, Cosmic Eyelash, composite SMGs)
- 2021ApJ...907..122M: Idealised spherical collapse model (Barkana & Loeb 2001); flat rotation curve V_rot equal to circular velocity of isothermal sphere host halo; thin circular di…
- 2021ApJ...907..122M: log SFR = -7.06 + 1.00 * log L_[C II] with 0.27 dex 1-σ dispersion (De Looze et al. 2014); baryon accretion rate formula from McBride et al. (2009); halo mass …
- 2024A&A...692A..34C: Turbulence dominates the line width; equipartition between turbulent kinetic and magnetic energy
- 2020MNRAS.495.3124H: Searching dirty cubes avoids cleaning artefacts
- 2016ApJ...833...71A: Factor 2 correction to UV SFR to get total SFR
- 2025NatAs...9.1553F: circular rotation
- 2025NatAs...9.1553F: Dark matter negligible in dynamical mass; gas-to-dust ~1e3 for cross-check
- 2020ApJ...905..147Y: Area A=2 sq.deg (cancels out)
- 2020ApJ...905..147Y: alpha_[CII] ~30 Msun/Lsun with 0.3 dex scatter (M_mol/L_[CII]=15-60)
- 2017ApJ...842L..16L: beta = 1.8
- 2024ApJ...968....9W: dust-to-gas ratio 100, molecular fraction 0.75
- 2024ApJ...968....9W: [C II] from thin rotating disk
- 2021MNRAS.505.4838L: Pseudo isothermal elliptical mass distributions and empirical scaling relations for parametric models; dark matter follows smoothed luminosity-weighted galaxy …
- 2021MNRAS.505.4838L: Magnification factor mu = 31 for intrinsic EW upper limit
- 2024A&A...687A.288G: Noise at phase centre approximately Gaussian (Jin method)
- 2024A&A...687A.288G: Lines are CO or [CI](1-0) transitions
- 2022MNRAS.511.1303V: Chabrier (2003) IMF (conversion factor 1.77 from Salpeter); stacked FIR SED dust temperature 43 +/- 5 K; Calzetti (2000) and Reddy et al. (2015) reddening curv…
- 2022MNRAS.511.1303V: Plane-parallel geometry including Orion-type grains and PAHs; single H II region; gas-phase metallicity fixed to 0.5 Z_sun from UV absorption analysis
- 2017MNRAS.466..138K: Half of intrinsic flux missed due to CMB; thermally excited CO(3-2); alpha_CO = 4
- 2024MNRAS.529L...1J: Dust emitted from about the same area as the [OIII] emission; kappa_0=0.04 m^2/kg at 250 GHz
- 2024MNRAS.529L...1J: beta_IR above ~2.5 is rarely seen
- 2024MNRAS.529L...1J: Z'~0.25 for the dust-to-gas ratio
- 2020MNRAS.493.4294B: CMB attenuation of [C II] not corrected; mu = 1.43
- 2019MNRAS.487L..81L: Line FWHM=100 km/s
- 2024A&A...685A..80Z: Clumps unresolved
- 2022PASJ...74.1429T: Systemic redshift z = 6.0244 +/- 0.0003
- 2022PASJ...74.1429T: Circular Gaussian source profile (n = 0.5) or point source
- 2017MNRAS.466.2825B: Solar undepleted elemental abundances; UMIST 2012 subset network
- 2025A&A...695A...6P: [OIII]5007/4959=2.98, [NII]6584/6548=2.94
- 2025A&A...695A...6P: [CII] k at T=1e4 K, n_H=1e4 cm^-3 (lower limit)
- 2021ApJ...908..192S: Chabrier IMF; delayed exponential SFH; two-component dust absorption; UV/IR energy balance
- 2021ApJ...908..192S: Flat LambdaCDM; h=0.7; Omega_m=0.3
- 2019ApJS..244...40L: Empirical line-L_IR correlations from De Looze et al. (2011), Zhao et al. (2013, 2016), Sargent et al. (2014), Liu et al. (2015), Valentino et al. (2018)
- 2024MNRAS.535.1533B: Multiple components in a field have the same colour temperature and redshift; beta_dust = 2.0
- 2023MNRAS.523.4654T: constant emissivity per unit mass for line tracers; constant dust-to-gas ratio for dust
- 2023MNRAS.523.4654T: [C II] moment map traces the distribution of star-formation-heated dust
- 2024A&A...688A.146A: NFW dark-matter halo profile; 0.4 dex stellar mass reduction for sources without MIRI photometry following Papovich et al. (2023) and Wang et al. (2024)
- 2020PASJ...72...69Y: AGN contribution (if any) is negligible for the derived physical properties
- 2020PASJ...72...69Y: only photometric errors are used; absolute flux calibration systematics are not included
- 2024ApJ...977..161V: alpha_CII from Rizzo et al. 2020; the literature range is 5-30
- 2020PASJ...72...29O: Expected [C II] frequency set by z_DLA = 3.150 (458.184 GHz); FWHM([C II]) = 700 km s^-1 adopted from lowest FWHM of Ly-alpha emission in Christensen et al. (2…
- 2020PASJ...72...29O: Flat cosmology with Omega_m = 0.3, Omega_Lambda = 0.7, H_0 = 70 km s^-1 Mpc^-1
- 2020PASJ...72...29O: Case B recombination Ly-alpha/H-alpha intensity ratio of 8.7; Kennicutt (1998) SFR(H-alpha) and SFR(FIR) calibrations; [C II]/FIR = 10^-2.5 (or scatter 10^-3.6…
- 2025NatAs...9..155Z: Negligible [NII] contribution to Halpha
- 2025NatAs...9..155Z: Typical Te=10,000 K for the quoted density limit
- 2023A&A...673A.153P: M_rot = M_* + M_gas; alpha_[CII] = 30 M_sun/L_sun with 0.2 dex uncertainty.
- 2019MNRAS.488.5029H: Afterglow spectral slopes alpha=-1/2 to 1/3 (Sari1998)
- 2024ApJ...974..145S: Chabrier IMF; spectroscopic redshift fixed; FSPS, MILES library, MIST isochrones
- 2024ApJ...974..145S: Young-star attenuation twice that of other stars; fixed Draine IR SED; no fitted IR AGN contribution
- 2020MNRAS.495.3409S: [CII] is the most likely line identification (later confirmed by CO(5-4) from another paper); lensing amplification not corrected
- 2020MNRAS.495.3409S: pairs in a ~10^13 Msun NFW halo have ~700 km/s velocity separation at ~20 kpc projected separation (following Wardlow et al.)
- 2017ApJ...845..154V: Majority of [C II] from same region as CO and [C I]
- 2025ApJ...989..160I: Adopted z_spec = 6.6312 +/- 0.0019 for the whole analysis
- 2021A&A...652A..66P: [CII]ion/[NII]205 ~3 as in HII regions; metallicity likely high
- 2021A&A...652A..66P: single plane-parallel semi-infinite cloud illuminated by PDR or XDR field
- 2019ApJ...886L..35P: modified blackbody with T = 35 K and beta = 1.6
- 2024ApJ...964...39G: Radial velocities of all lines tied together; broad Halpha width constrained within a factor of two of Hbeta; case B recombination
- 2019ApJ...887..144J: Gaussian noise
- 2024A&A...691A.133V: LCDM H0=70, OmegaM=0.3, OmegaL=0.7
- 2022MNRAS.515.3126I: Constant star formation history, sub-solar metallicity, Chabrier (2003) IMF, Calzetti et al. (2000) dust extinction curve
- 2024ApJ...971...47F: Starburst reddening curve k'(lambda) from Calzetti et al.
- 2020ApJ...889...98M: Flat LCDM, h=0.7, Omega_L=0.73, Omega_M=0.27
- 2026ApJ..1000..308W: Case B Halpha/Hbeta=2.86, Calzetti curve, f=0.56
- 2026ApJ..1000..308W: log(O/H)=-3.6 (0.5 Zsun)
- 2021A&A...646A..76L: non-evolving L[CII]-SFR relation
- 2026A&A...706A.174A: Foreground extinction from Lupus-I at 24 micron negligible
- 2020A&A...643A...2B: kappa_IR=1.02e-10, kappa_FUV=1.47e-10 Msun/yr/Lsun (Chabrier IMF)
- 2024A&A...691L...2S: Delayed-tau star formation history; flexible Calzetti attenuation curve; DL07 IR models; nebular and AGN emission
- 2020A&A...633A..90G: n>n_crit, X_C+=1.4e-4, T=60-200 K, 70% of [C II] from PDRs, optically thin
- 2017A&A...597A..41G: z=2 (range 1-3) for sources without spectroscopic redshift
- 2025PASP..137l4501T: Spectroscopic redshift of each source is accurate
- 2024ApJ...972..111L: Companions at 12–33 kpc projected distance with ~1500 km/s velocity
- 2020ApJ...900....1F: Sersic index n=1
- 2017ApJ...850...83F: [CII] contamination by chance negligible (~1-2% of sources, <=10% of continuum)
- 2025ApJ...987L...2H: Oxygen abundance log(O/H) = 7.92 (Z/Zsun = 0.17; solar 12+log(O/H) = 8.69)
- 2020A&A...643A...1L: De Looze 2014 relation for predicted L[CII]; flat LCDM H0=70, Om=0.3
- 2024ApJ...961..120C: <sin i> = pi/4 ≈ 0.79
- 2023ApJ...953...75H: Chabrier (2003) IMF; Planck 2018 cosmology; two Noll et al. (2009) / Calzetti et al. (2000) modified dust attenuation curves with old-star attenuation forced s…
- 2019ApJ...887..107F: beta=1.8, Td=35 K, single Gaussian line FWHM 270 km/s to correct 100 km/s window
- 2024ApJ...962L..11W: Fixed slope gamma=1.8 for all comparison profiles
- 2020MNRAS.498.4192F: Single 2D Gaussian source model.
- 2026ApJ..1004...22F: Case B recombination for Balmer decrement dust correction
- 2026ApJ..1004...22F: ne = 400 cm^-3 assumed for Te(O++) derivation, Te = 2 x 10^4 K assumed for ne derivation
- 2023MNRAS.524..923Z: Bruzual & Charlot (2003) models, Chabrier (2003) IMF, delayed SFHs, Calzetti et al. (2000) dust attenuation curve, E(B-V)_star = 0.58 E(B-V)_nebular
- 2022MNRAS.516.5618P: H0 = 68 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7 cosmology
- 2024MNRAS.528.5019H: Bruzual-Charlot templates, Chabrier IMF, Calzetti attenuation law
- 2022NatCo..13.4574G: LambdaCDM cosmology (Omega_Lambda0 = 0.69, Omega_m0 = 0.31, Omega_b0 = 0.05, H0 = 67.7 km/s/Mpc); linear galaxy bias b = 2.8 ± 0.4; Chabrier IMF for HST SFRs
- 2024A&A...684A.119P: Modified black body with T_dust = 20-45 K and beta = 1.5-2.0, CMB contrast included
- 2020ApJ...905...85S: systemic redshift from [CII] (5 sources) or S/N-weighted stacked CO lines
- 2026ApJ...999...47L: LambdaCDM cosmology with Planck 2020 parameters (H0 = 67.4 km s^-1 Mpc^-1), Chabrier IMF, Calzetti (2000) dust attenuation law
- 2021A&A...647A.194F: Planck Collaboration et al. (2018) cosmology (6.70 kpc/'' for AzTEC/C159, 6.72 kpc/'' for J1000+0234); v_rot = v_c; optical R_e = 1.4 * R_e,FIR; exponential sc…
- 2019ApJ...870L..19N: Flat LCDM, Omega_lambda=0.7, H0=70 km/s/Mpc
- 2024ApJ...977L..36H: Calzetti et al. (2000) extinction law, Case B recombination Hβ/Hδ = 3.78 for T_e = 1.6 x 10^4 K, T_e = 18000 ± 4000 K in PyNeb, solar oxygen abundance 12 + log…
- 2016A&A...593L...2N: CO optically thick
- 2024A&A...690A..55S: Modified blackbody with beta~1.7
- 2020Natur.581..269N: Infinitely thin disk; thick disk tested
- 2017PASJ...69...45H: LCDM Om=0.3, OL=0.7, h=0.7; Chabrier IMF
- 2024ApJS..275...36F: Single-line identities chosen using photometric-redshift distributions.
- 2021ApJ...908..146C: Chabrier IMF for stellar masses and SFRs
- 2017A&A...608A.138G: Redshift of nearest counterpart applies to the line
- 2024A&A...691A.153L: [N II]λ6583/[N II]λ6548 and [O III]λ5007/[O III]λ4959 fixed to 2.99; [O II] and [S II] doublet ratios bounded by theoretical limits for 1-10^5 cm^-3
- 2025A&A...699A.256P: Td = 45 K, beta=1.5, uncertainty from Td 40-60 K
- 2022MNRAS.511.3017U: Adjacent CO spectral lines typically have similar integrated line fluxes, allowing exclusion of redshift solutions for strong single-line detections
- 2017ApJ...840...78D: Chabrier IMF
- 2025ApJ...988...48N: optical/NIR photo-z uncertainty 2 sigma ~ 0.76, allowing z_phot ~ 1.9-3.4
- 2019ApJ...882...10N: Gas physical conditions constant across the galaxy at fiducial values
- 2024A&A...686A.187P: L_IR computed from rest-frame 158 um emission assuming the Bethermin et al. (2017) SED
- 2022MNRAS.510.3734D: alpha_CO = 3.0 +/- 0.5 M_sun (K km s^-1 pc^2)^-1 with 1.36 helium factor and mean GDR = 135; alpha_[CI] = 18.8 M_sun (K km s^-1 pc^2)^-1; alpha_CII = 30 M_sun/…
- 2026MNRAS.546ag049F: Chabrier (2003) IMF with mass limits 0.1-100 M_sun; constant SFH and Z_* = 0.1 Z_sun for standard UV/IR conversions; T_e = 10^4 K and solar metallicity for sta…
- 2020ApJ...892..119M: Cosmology Om=0.3, OL=0.7, H0=70
- 2016ApJ...826..112S: LFIR integrated over rest-frame 42.5-122.5 um
- 2021MNRAS.502.1797R: SFR for LBG1-3 calculated as 1.4e-28 L_nu(1500 A) M_sun yr^-1 with extinction estimated from r - i colour
- 2025A&A...695A.163B: Lowest detectable CO transition; perturb luminosity and excitation scaling within linear uncertainties.
- 2020A&A...643A...8G: Chabrier IMF
- 2020A&A...643A...3S: Template similar to modified blackbody T_d=42 K, beta=1.5
- 2022A&A...665A...3J: For ID9316 CO(5-4) on the edge of the spectrum, line flux is estimated assuming an identical line profile to CO(4-3)
- 2021MNRAS.504..928P: Power-law X-ray spectrum with intrinsic photon index Gamma_int from Luo et al. (2017)
- 2026ApJ..1000..159M: Target sources are unresolved / point-like at continuum and S/N is low enough not to require cleaning
- 2019ApJ...881...63N: Same FWHM as [CII] for all lines
- 2025A&A...695A..23S: Same alpha_CO and CO SLED as for the new data; r_7,6=0.65, r_6,5=0.9, r_2,1=1 for the comparison sample
- 2026A&A...706A.285C: Gas-to-dust mass ratio of 100 for Sigma_Md to gas mass surface density
- 2026A&A...706A.285C: T_CMB(z=6.5)=20.5 K in the optically thick theoretical relation
- 2020A&A...642A.155Z: Typical dust temperature ~38-40 K at these redshifts (Schreiber18)
- 2025A&A...693A.190J: Spectroscopic redshifts used where available, otherwise photometric; SFR and stellar mass corrected for magnification
- 2016ApJ...816L...6D: f_g ~ 1 extreme case; cosmology Omega_M=0.3, Omega_L=0.7, H0=70
- 2024A&A...686A..85A: Flat optical continuum in F_nu extrapolated to the Halpha wavelength
- 2025A&A...695A.204V: Jackknifed peaks sample the false-detection distribution; peak distribution is a subset of the pixel-value distribution of a smoothed random Gaussian field
- 2024A&A...685A.138V: X_[CI] ~1.5e-5 scaled linearly to ~25% Zsun
- 2020MNRAS.491L..18J: flat LCDM, Om=0.3, OL=0.7, H0=70
- 2024A&A...690A.197M: Excluding ±0.45 GHz avoids broad [C II] line contamination (FWHM/2 ~ 250 km s^-1); 3.0'' beam includes all flux density within a single beam
- 2025ApJ...994....4A: E(B-V)_stellar/E(B-V)_nebular = 0.83; Kennicutt (1998) SFR relation modified for Chabrier IMF
- 2020MNRAS.492.1778M: Gaussian prior on z_sys (6.5285, 0.001) from [CII]
- 2024A&A...683A..64A: homogeneous spherical expanding shell with mixed HI and dust, central source
- 2026MNRAS.549ag931B: Fiducial DSFG with L_IR = 10^12 L_sun, CO SLED scaling from Hagimoto et al. (2023), HerBS and SPT redshift distributions, and analytical sensitivity equation f…
- 2020ApJ...890..171J: gas and dust co-spatial; sigma<=100 km/s upper limit
- 2025ApJS..278...45F: Modified blackbody Td=45 K, beta=1.8 for L_IR; FWHM=200 km/s and 5 sigma for LF
- 2024MNRAS.530.4887W: Multiple ALMA sources within the Herschel beam with only one spectroscopic redshift are physically connected at that redshift.
- 2025A&A...700A.278R: extended component 13% of FIR; 20% of [CII] from ionised gas; geometric factor of two
- 2026A&A...705A..39P: SFR from IR luminosity with 1.73e-10 Msun/yr/Lsun (Salpeter); H2 from [CII] conversion


### Limitations the authors admit
- 2025A&A...693A.237I: Multiplicity classification is morphological and does not incorporate kinematical state (e.g., CRISTAL-05 appears single in UV/[C II] morphology but is a line-of-sight pair kinematically), and some H…
- 2025A&A...693A.237I: Limited sample size prevents statistically distinguishing [C II] size distributions across multiplicity classes and yields large uncertainties in size ratios.
- 2025A&A...693A.237I: FIR continuum visibilities have lower S/N than [C II] and were modeled with a single circular exponential disk, preventing fair comparison in multiple-UV and multiple-[C II] systems and yielding an u…
- 2025A&A...693A.237I: Available Ly-alpha measurements come from slit spectroscopy and only probe global properties without spatial information.
- 2020MNRAS.499.5136C: Correction-factor uncertainty prevents total-flux accuracy better than ~20%-30%
- 2020MNRAS.499.5136C: Correction factors may be inappropriate for very complicated morphologies
- 2020MNRAS.499.5136C: Low statistics above z=7 prevent a definitive evolution measurement
- 2020MNRAS.499.5136C: Tapering sacrifices sensitivity and does not by itself recover total galaxy emission
- 2020MNRAS.499.5136C: MS0451-H line association is unconfirmed; magnification systematics and differential magnification complicate its luminosity
- 2020MNRAS.499.5136C: BDF-3299 satellite and CGM interpretations require more sensitive [CII] or JWST observations
- 2018MNRAS.481.1976Z: Fluxes depend critically on the assumed model size taken from optical images
- 2018MNRAS.481.1976Z: Source size cannot be constrained from individual sources because of low S/N
- 2018MNRAS.481.1976Z: Observed in a more extended configuration than requested, giving 5-10 times higher flux errors
- 2025ApJ...987L..37W: Deeper and higher-resolution [C I] data are needed to determine M_H2 accurately
- 2025ApJ...987L..37W: [C I] extraction apertures overlap in fields with multiple [C II] companions
- 2025ApJ...987L..37W: Positions on the SFR-M_star plane are uncertain because most measurements are upper limits
- 2013A&A...559A..29C: Inclination poorly constrained, so mass is poorly constrained
- 2021ApJ...908..235I: The nature of the extended structure cannot be identified with current data
- 2021ApJ...908..235I: Outflow mass is a lower limit and rates measured at only three positions
- 2021ApJ...908..235I: Extended [C II] in negative velocity channels needs deeper observations to confirm
- 2021ApJ...908..235I: SFR estimates are upper limits because AGN contamination is neglected
- 2024A&A...690A.277M: Central approximately 0.7″ stellar kinematics cannot be fitted accurately because AGN emission dilutes stellar absorption.
- 2024A&A...690A.277M: The minimum cluster size of 50 spaxels is arbitrary.
- 2024A&A...690A.277M: The Hβ outflow component is buried beneath a broad component with FWHM approximately 1600 km s^-1.
- 2019A&A...630A..59B: Interferometric data may miss extended diffuse emission; stacking dilutes orientations
- 2021A&A...645A..21G: Large-scale faint CO emission could not be modelled with BAROLO; velocity extrapolation and brightness-based identification were used.
- 2021A&A...645A..21G: CO conversion factor poorly constrained; molecular masses depend on α_CO and line ratio.
- 2021A&A...645A..21G: Electron density is the largest ionized-mass uncertainty; [S II] can give lower densities than auroral/transauroral diagnostics.
- 2021A&A...645A..21G: Intrinsic spiral-arm asymmetry could affect the inferred gas deficit.
- 2021A&A...645A..21G: Spiral-arm masses exclude nuclear regions containing much of the molecular mass.
- 2021A&A...645A..21G: Wind model assumes spherical symmetry and omits ISM resistance.
- 2019A&A...632A.106L: limited HI spatial resolution is the main caveat
- 2021A&A...650A.117N: Scheduled ALMA Band 9 observations could not be performed due to weather constraints.
- 2021A&A...650A.117N: The faint ATCA 5.5 GHz extended emission near the GRB site is at the ~5 sigma level, so there is no guarantee that it is real and it is too faint to split in time or frequency.
- 2021A&A...650A.117N: Small angular sizes (< 0.2''), faintness, and strong host foreground emission prevent MUSE from clarifying the nature of individual clumps C-G and K-M.
- 2021A&A...650A.117N: Low S/N in the outskirts of the galaxy prevents measuring E(B-V)_host, EW(Halpha), or a secure SFR at the GRB explosion site.
- 2021A&A...650A.117N: Apparent lower metallicity in region B and high velocity dispersions (~60 km s^-1) in the outskirts could be affected by low-number statistics or low S/N.
- 2015ApJ...801..123W: Dynamical masses highly uncertain (unknown gas structure, marginal resolution, missed extended gas); no formal errors
- 2015ApJ...801..123W: Missing red-wing data of J0055+0146 may bias size and inclination
- 2020MNRAS.496.2155Z: Sample biased towards higher-mass, star-forming galaxies
- 2020MNRAS.496.2155Z: Six Paper I detections lack inclusion in this study
- 2020MNRAS.496.2155Z: FCC290 has only partial MUSE coverage
- 2020MNRAS.496.2155Z: BPT boundaries and composite Hα contributions are uncertain
- 2020MNRAS.496.2155Z: FCC312 MUSE mosaic gap causes a local depletion-time overestimate
- 2020MNRAS.496.2155Z: FCC290 feedback lifetime and separation may be biased by insufficient resolution and blending
- 2020MNRAS.496.2155Z: Poor statistics and projected distances prevent isolating the cluster-location effect
- 2020MNRAS.496.2155Z: Comparisons with B08 differ in CO transition, conversion factor, SFR tracer, sample and resolution
- 2024A&A...689A.101C: ALPINE sample biased toward star-forming galaxies
- 2024A&A...689A.101C: Error budget excludes foregrounds and sky noise
- 2024A&A...689A.101C: Multiple Schechter fits are valid and change the extrapolated counts
- 2024A&A...684A.107M: Subtraction of the surrounding old nebula emission from the central ejecta spectrum is imperfect due to spatial surface brightness variations in the outer nebula.
- 2024A&A...684A.107M: MEGARA data cubes lack absolute astrometric positioning, and there is a 0.26 arcsec (1.3 pixel) offset in the fitted stellar continuum position between VPH481-MR and VPH665-HR.
- 2024A&A...684A.107M: SHAPE does not include radiative transfer physics, so the spatially varying dust extinction from the disk had to be approximated with an arbitrary emission law.
- 2020MNRAS.498.3624L: Unexplained 20.3 km/s offset of CO(7-6), probably systematic
- 2020MNRAS.498.3624L: Differential lensing in compact lensed J0439+1634 may distort line profiles and shift line positions
- 2018MNRAS.476.4949D: H2S column uncertain by an order of magnitude due to unknown HDS/H2S
- 2016A&A...592A..83K: Gas-to-dust ratio and radial gas extent dominate uncertainty; mm-opacity gaps not modelled
- 2025A&A...702A.276P: Incomplete orbital phase coverage across all ALMA bands: only orbital phase 0.43 has near-complete multi-band coverage (Bands 1, 3, 4, 6, 7), while the full pre-burst dataset spans 104 days (46% of t…
- 2025A&A...702A.276P: In Band 1a, 180-degree Walsh switching was turned off, and in Band 1b one continuum spectral window was accidentally centered at 40 GHz instead of 46 GHz.
- 2025A&A...702A.276P: The difference between the softest individual 2016/17 VLA spectral index and the 2024 ALMA spectral index is only 0.26 +/- 0.13, a 2-sigma effect, requiring deeper observations over a full orbit for …
- 2025A&A...702A.276P: The analytical stellar wind model neglects geometrical effects, assumes an isotropic, isothermal, fully ionized power-law wind, and has inherent inconsistencies when estimating mass-loss rate at a fi…
- 2026ApJ..1003...26O: Molecular emission contaminated by nearby protostars; Tex choice gives minimum mass
- 2019A&A...626A..70S: Higher signal-to-noise CRRL detections needed to constrain properties independently
- 2025A&A...694A.171M: Low SNR and limited spatial resolution prevent firm conclusions on kinematics
- 2025A&A...694A.171M: Radio data are non-simultaneous so SED shapes may be affected by variability
- 2025A&A...694A.171M: PSO055-00 [CII] line lies at the edge of the bandwidth; derived quantities uncertain
- 2025A&A...694A.171M: A full SED fit of synchrotron and dust components is out of scope given limited data
- 2025A&A...694A.171M: The data are about 3 times shallower than those used to determine the blank-field number density
- 2020MNRAS.494.5542R: CO(3-2) has low S/N and must be interpreted carefully
- 2020MNRAS.494.5542R: Agreement of the PDR models with line ratios is largely due to large systematic uncertainties on CO(3-2) and CO(10-9) reconstructions
- 2020MNRAS.494.5542R: Semi-infinite uniform-density slab models are likely too simplistic for a clumpy ISM
- 2020MNRAS.494.5542R: Low surface-brightness CO(10-9) component could be a modelling artifact
- 2020MNRAS.494.5542R: T_dust from rest-frame 160-350 um is limited because the data lie on the Rayleigh-Jeans tail
- 2019ApJ...876..112R: Only two galaxies; extended [CII] likely resolved out
- 2025A&A...696A..88W: Companion search is not complete
- 2025A&A...696A..88W: Dispersion-based masses are upper limits because sizes of unresolved sources are overestimated
- 2025A&A...696A..88W: [C II] emitters without [O III] or dust counterparts could be other lines at other redshifts
- 2015MNRAS.449.2883G: PDR sizes and molecular gas sizes are rough/uncertain
- 2020MNRAS.492.3194S: Sample limited to sources with existing FIR and Halpha detections, so all lie on or above the star-forming main sequence
- 2020MNRAS.492.3194S: Effects of outflows could occur below the resolution of the data (a few kpc) or on long timescales
- 2020MNRAS.492.3194S: ID2 FIR flux may be partly synchrotron contaminated
- 2024A&A...686A..46E: Molecular outflow quantities are upper limits due to possible bar
- 2024A&A...686A..46E: Inflow within 0.4" not confirmable (only two radial points)
- 2017ApJ...836....8T: M_dyn is uncertain: extended emission missed, inclination from marginally resolved sizes, beam smearing
- 2017ApJ...836....8T: Small sample limits interpretation
- 2021ApJ...909..204F: FIFI-LS spectral resolution cannot clearly separate all [C II] components.
- 2021ApJ...909..204F: Normal PDR emission may dilute an excess in one velocity component of region E.
- 2021ApJ...909..204F: Synthetic MIPS PSF subtraction slightly over-subtracts parts of the first and second Airy rings.
- 2021ApJ...909..204F: Low X-ray photon statistics require combined spectra.
- 2021ApJ...909..204F: Parallel SOFIA 88.3 μm observations have insufficient signal-to-noise for science results.
- 2021ApJ...909..204F: Origin of trailing gas remains unclear; refined gas-inclusive minor-merger simulations are beyond scope.
- 2018ApJ...853..111J: XCO from 13CO is highly uncertain (LTE, abundance ratios, beam dilution)
- 2018ApJ...853..111J: AV estimate smoothed at ~40" and biased low by single dust temperature
- 2023MNRAS.519.2030H: HI and H2 gas do not necessarily trace each other or share physical association, so comparing molecular gas (CO) kinematics in the non-repeating FRB host with atomic gas (HI) kinematics in repeating …
- 2023MNRAS.519.2030H: A_flux for the FRB 180924B host (1.05 +/- 0.16) lies on the boundary of the asymmetry definition because kinetic information can be lost during the flux integration process.
- 2023MNRAS.519.2030H: Observations of molecular gas in FRB host galaxies are still limited to a very small sample.
- 2025PASJ...77..432U: Stellar mass profile outside R~8 kpc is extrapolated for lack of sensitivity
- 2025PASJ...77..432U: CO(1-0) is not well resolved by the JVLA, so the Toomre Q rests on assumed profile
- 2025PASJ...77..432U: Limited profile sampling prevents fitting a third (bar) component in the stellar profile
- 2025PASJ...77..432U: Limited NIRCam spatial coverage and few Gaia stars make absolute astrometry hard
- 2021A&A...646A..26B: SFH and age poorly constrained with limited rest-frame optical/UV data
- 2021A&A...646A..26B: Upper limit does not exclude higher metallicity
- 2016Sci...352.1559I: Low SNR; origin of possible high-velocity components uncertain; [C II] marginal features affected by ozone line
- 2024ApJ...972..116I: Only statistical errors shown; calibration uncertainty ~10% absolute flux
- 2024ApJ...972..116I: Dust results are sensitive to assumed T_dust and beta
- 2024ApJ...972..116I: Host masses are hard to estimate because of the highly dynamic nature of the system; M_H2 and SFR from [CII] are not independent
- 2024ApJ...972..116I: Outflow evidence is tentative and needs higher angular resolution and sensitivity
- 2013ApJ...773...44W: Limited resolution gives only constraints on size; morphology uncertain, large errors on minor axis and PA affect inclination and Mdyn.
- 2013ApJ...773...44W: [C II] may trace only the central starburst, underestimating bulge mass.
- 2020ApJ...903...34A: Only two continuum points on the Rayleigh-Jeans tail, so dust temperature and SED shape unconstrained; dust mass has at least a factor of two systematic uncertainty
- 2020ApJ...903...34A: Black hole mass systematic errors (~0.5 dex) not included; virial calibration may be inadequate for WLQs
- 2020ApJ...903...34A: Shielding gas between disk and BLR cannot be excluded without X-ray spectroscopy
- 2026A&A...707A..77H: Ionized outflow masses are lower limits due to the electron density floor
- 2026A&A...707A..77H: alpha_CO in outflows is highly uncertain, so energetics are order-of-magnitude estimates
- 2026A&A...707A..77H: Outflow presence in the NW nucleus is uncertain
- 2019A&A...631A..78S: Assumes a single broad Gaussian outflow profile; broad emission could be from interacting galaxies; low-velocity outflows not detectable
- 2022ApJ...941...47S: Excluding SPIRE 250 um photometry to preserve spatial resolution reduces the accuracy of total far-IR flux estimates.
- 2022ApJ...941...47S: Strong stellar absorption in the optical spectra prevents measuring Hbeta and [OIII] in emission in many apertures.
- 2022ApJ...941...47S: The ALMA beam (14.3'' x 7.7'') intercepts multiple molecular clouds with slightly different velocities along the inclined ring, artificially broadening the CO line profile except at the major axis ex…
- 2022ApJ...941...47S: Herschel/PACS velocity resolution is insufficient to resolve multiple velocity components of [CII] along the ring.

### Settings cards flag as needed but not stated
- casa version: 17
- flux calibrator and flux scale uncertainty: 10
- casa version and pipeline version: 5
- flux calibrators and flux scale uncertainty: 5
- line-free channels used for continuum subtraction: 4
- casa version and whether the pipeline or manual scripts were used: 4
- continuum subtraction and line-free channels: 4
- casa version and alma pipeline version used for calibration and imaging: 4
- flux calibrator and flux-scale uncertainty: 4
- whether self-calibration was applied: 3
- line-free channels and continuum subtraction: 3
- primary beam correction details: 3
- flux calibrators and flux-scale uncertainty: 3
- cell size, image size, clean threshold and masks: 3
- clean threshold, mask, cell and image size: 3
- flux calibration uncertainty: 2
- primary-beam correction details: 2
- flux, bandpass and phase calibrators: 2
- line-free channels used for continuum and uvcontsub: 2
- flux scale uncertainty: 2
- primary beam correction: 2
- line-free channels and continuum subtraction method: 2
- line-free channel ranges for continuum: 2
- exact line-free channels used for continuum maps: 2
- mcmc sampler, priors and likelihood for gaussian line fits: 2
- whether any self-calibration was applied: 2
- exact casa version and pipeline version used for calibration and imaging: 2
- continuum subtraction method and line-free channels: 2
- casa version and alma pipeline version for each project: 2
- casa version used: 2
- line-free channels and continuum-subtraction method: 2
- casa version used for reprocessing: 2
- line-free channel ranges for continuum subtraction: 2
- source coordinates: 2
- stacking procedure details: 2
- flux, bandpass and phase calibrators and flux-scale uncertainty: 2
- continuum-subtraction and line-free channels: 2
- pipeline version: 2
- continuum-subtraction method and line-free channels: 2
- self-calibration usage: 2

## Paper excerpts (40 of 368, chosen for detail and spread over fields/years)

### 2025A&A...693A.237I: The ALMA-CRISTAL Survey: Spatial extent of [CII] line emission in star-forming galaxies at z = 4−6 (2025; high_z_galaxies; large_program_or_survey)
- question: Investigate the spatial extent, structure, and physical origin of [C II] line emission in star-forming galaxies at z = 4-6, including a search for an extended secondary halo component.
- step 1: Classify galaxies by multiplicity
  - method: Visual classification into four categories (single, pair, multiple-UV, multiple-[C II]) based on HST/WFC3 F160W rest-frame UV images and ALMA [C II] line distributions. [3.1. Classification based on multiplici…: "In this study, we take a step forward to add information from the [C ii] line distribution to visually classify the CRISTAL sample into four categories"]
  - parameter: projected angular separation < ~3 arcsec and velocity offset < 300 km/s for pairs; FIR S/N < 5 or overlapping UV blobs for multiple-UV [3.1. Classification based on multiplici…: "a pair of [C ii] line detections with a projected angular separation of less than ∼ 3 arcsec. The velocity offset among the pair is confirmed to be small (<300 km/s)"]
  - validation: Checked against higher-resolution JWST images (Lines et al. 2024) and kinematical analyses (Posses et al. 2024). [3.1 Classification based on multiplicity: "three galaxies (CRISTAL-11, CRISTAL15, and CRISTAL-17) classified as single have pair-like morphology when looked with sharper images taken by James Webb Space Telescope"]
- step 2: Extract [C II] spectra and create velocity-binned visibility datasets
  - method: Extract 1D spectrum in a 1-arcsec aperture from the 20 km/s data cube, fit a 1D Gaussian (double Gaussian for CRISTAL-22a) to define the +-2 sigma (95% flux) velocity range, subtract continuum in uv-plane, and bin visibilities over this ve… [3.2.1. [C ii ] line emission: "(1) extract spectrum with a 1-arcsec aperture from the data cube (20 km/s width per channel)."] [3.2.1 [C ii] line emission: "contains 95 % (= [2.5 %, 97.5 %]) of the total [C ii] line flux, corresponding to 4σ (±2σ from the central frequency ν 0 ) width of Gaussian (≈ 1.7 Gaussian FWHM)."]
  - software: CASA/tclean, scipy (curve_fit), CASA/uvcontsub, CASA/mstransform
  - parameter: 1-arcsec aperture; 20 km/s channel width; +-2 sigma velocity range (95% flux); nchan = 1 [3.2.1. [C ii ] line emission: "(1) extract spectrum with a 1-arcsec aperture from the data cube (20 km/s width per channel)."] [3.2.1. [C ii ] line emission: "We then binned the visibilities into a single channel by specifying `nchan` `=` `1` in the `CASA/mstransform` task."]
  - assumption: Single Gaussian line profile (double Gaussian for CRISTAL-22a) [3.2.1 [C ii] line emission: "As an exceptional case, we fit the [C ii] spectrum of CRISTAL22a, which shows a clear double-peaked line profile, with a double Gaussian."]
  - fitting: 1D Gaussian fit using scipy curve_fit [3.2.1. [C ii ] line emission: "(2) fit the extracted spectrum with a single Gaussian _f_(ν) ∝ exp[(ν − ν 0)2 /2σ2] using the `curve_fit` function within the `scipy` package (Virtanen et al. 2020)."]
  - validation: Visual inspection confirming the +-2 sigma velocity range includes almost all [C II] line emission. [3.2.1. [C ii ] line emission: "The ±2σ velocity range includes almost all of the [C ii] line emission, which assures that the [C ii] size measurements will be performed by fitting the representative velocity range of the emission."]
- step 3: Measure [C II] structural parameters via visibility modeling
  - method: Fit binned [C II] visibilities directly with 2D exponential disk models (1-component for single/multiple-UV, 2-component for pair/multiple-[C II]) and convert major-axis FWHM and axis ratio to circularized effective radius Re,[CII] and lum… [3.2.1. [C ii ] line emission: "We used the `UVMULTIFIT` (Martí-Vidal et al. 2014) to model the visibilities of the [C ii] line emission in the CRISTAL sample."] [3.2.1. [C ii ] line emission: "For a 2-D exponential disk model, the major axis FWHM and major axis effective radius can be related as _R_ _e_,major = 1.21 × FWHM, therefore we obtained a circularized effective radius by calculating _R_ _e_,[CII] = 1.21 × FWHM √_q_, where _q_ is the minor-to-major axis ratio."]
  - software: UVMULTIFIT
  - parameter: Sérsic index n = 1 (exponential disk); 6 free parameters (R.A., Decl., total flux density, major-axis FWHM, minor-to-major axis ratio q, position angle); q fixed to 1 when peak S/N < 8 [3.2.1 [C ii] line emission: "exponential disk model ( _n_ = 1) for all of the [C ii] components and first allow six parameters (R.A., Decl., total flux density, major-axis FWHM, minorto-major axis ratio, and position angle of major axis) free."]
  - assumption: 2D exponential disk profile (n = 1); standard LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7 [1. Introduction: "Throughout this paper, we assume a standard ΛCDM cosmology with _H_ 0 = 70 km s−1 Mpc−1, Ω M = 0.3, and Ω Λ = 0.7."] [3.2.1. [C ii ] line emission: "We assumed a two-dimensional (2-D) exponential disk model (_n_ = 1) for all of the [C ii] components"]
  - fitting: Visibility fitting in UVMULTIFIT with uncertainties from the post-fit covariance matrix and error propagation [3.2.1. [C ii ] line emission: "We estimate the uncertainty by using error propagation. For the uncertainty of each parameter (FWHM and _q_), we adopt the output from the `UVMULTIFIT`, which is estimated from the post-fit covariance matrix (Martí-Vidal et al. 2014)."]
  - validation: Checked residual maps for absence of >2 sigma peaks in the central 2" region and compared with ALPINE-only visibility fits in Appendix B. [3.2.1. [C ii ] line emission: "As can be seen in Figure 3, the best-fit model characterizes the observed [C ii] line emission well and no signal greater than 2σ significance level is present in the central 2′′-region, securing the validity of the fitting."] [3.2.1. [C ii ] line emission: "To fairly compare with the fitting results from the low-resolution archival data alone, we iterate the above procedure by only using the data taken in the ALPINE Survey."]
- step 4: Compare [C II] sizes with rest-frame UV and FIR continuum sizes
  - method: Calculate ratios of circularized [C II] effective radii to rest-frame UV (HST F160W GALFIT) and FIR (ALMA Band-7 UVMULTIFIT) effective radii from Mitsuhashi et al. (2024) and compare across multiplicity classes. [3.2.2. Rest-frame UV and FIR continuum …: "To evaluate the spatial extent of [C ii] line emission, we refer to two continuum size measurements (observing wavelengths of 1.6 µm and 870 µm), which were both performed in Mitsuhashi et al. (2024)."] [4.1. Size comparison: "We start by comparing the measured effective radii among different tracers (rest-frame UV and FIR continua) to characterize the spatial extent of the [C ii] line emission in the context of star formation activity."]
  - software: GALFIT, SExtractor, UVMULTIFIT
  - parameter: Excluded CRISTAL-21 from FIR size comparison due to unreliable FIR size measurement [4.1. Size comparison: "One galaxy that is well below the one-to-one line is CRISTAL-21, which has an unreliable FIR size measurement due to the insufficient S/N of the visibility data, particularly at short _uv_ distances. Therefore, hereafter, we do not include the results of CRISTAL-21 when the FIR radius is related to the discussions."]
  - assumption: Single Sérsic n = 1 profile for UV (except CRISTAL-13) and circular exponential disk for FIR continuum [3.2.2. Rest-frame UV and FIR continuum …: "A single Sérsic model with an index of _n_ = 1 is assumed (except for CRISTAL-13), and nearby objects seen in the HST images are masked by using `SExtractor` (Bertin & Arnouts 1996)."]
  - fitting: Kolmogorov-Smirnov test to compare size distributions across multiplicity classes [3.2.1. [C ii ] line emission: "Although we expect to find larger [C ii] sizes in pair and multiple-UV systems compared to single systems, we were unable to statistically distinguish their size distributions by performing the Kolmogorov-Smirnov test (with _p_ values of 0.23 and 0.12 for the pair and multiple-UV, respectively), largely due to our lim…"]
  - validation: Checked positional offsets between [C II], UV, and FIR emission peaks. [4.1. Size comparison: "We note that the median (average) positional offset between the [C ii] line and rest-frame UV continuum emission is 0.11 (0.14) arcsec (∼ 0.5 kpc in a physical scale), which is smaller than the typical synthesized beam size of the CRISTAL data."]
- step 5: Test for a secondary extended [C II] halo component via visibility stacking
  - method: Extract real part of visibilities for 16 single galaxies (excluding CRISTAL-23c), stack visibilities and normalized residual visibilities, and perform single-component and concentric double-component ('galaxy' + 'halo') exponential disk fi… [4.2. Constituent of [C ii ] line emissi…: "To further confirm this, we stack the visibility data of 16 single galaxies and again perform the visibility modeling in the same manner. We perform both single component and double component fittings."] [4.2. Constituent of [C ii ] line emissi…: "In order to avoid the stacked visibility data being skewed by the bright objects in which the amplitude of residual visibility is also bright, we normalize the residual visibility by the total [C ii] flux obtained from the best-fit model before the stacking."]
  - software: casatool ms (getdata), UVMULTIFIT
  - parameter: 16 single galaxies; 20 klambda and 100 klambda uv-distance bins; average redshift z = 5.22 [4.2 Constituent of [C ii] line emission: "we stack the visibility data of 16 single galaxies and again perform the visibility modeling in the same manner."] [4.2. Constituent of [C ii ] line emissi…: "We show the average values per both 20 kλ and 100 kλ bins, but no clear excess can be found in either case."]
  - assumption: Two concentric exponential disk components for double-component fit; average redshift z = 5.22 [4.2. Constituent of [C ii ] line emissi…: "Here, we assume two concentric exponential disk components."]
  - fitting: Single and double exponential disk fitting in UVMULTIFIT evaluated with reduced chi^2 [4.2. Constituent of [C ii ] line emissi…: "Since the fittings converge to the same reduced χ2 value, we cannot statistically favor either the single or double component model."]
  - validation: Checked residual visibility flux excess at the shortest uv-distance bin (20 klambda) against standard deviation. [4.2. Constituent of [C ii ] line emissi…: "At the smallest 20 kλ bin of the residual visibility, we find a flux excess of 0.15 mJy (1.2σ significance level)."]
- step 6: Measure radial surface density profiles of stacked [C II] and FIR continuum
  - method: Shift phase centers to [C II] peaks, stack visibilities of 10 single galaxies detected in both [C II] and FIR using CASA/concat, image with CASA/tclean, and extract radial surface density profiles and their ratio Sigma_[CII]/Sigma_IR. [4.3.3. [C ii ] deficit in the central r…: "To inspect this, we stacked ten single galaxies, in which both [C ii] line and FIR continuum emission is detected. The stacking was performed in visibility using the `CASA/concat` task. The phase centers of individual visibility data are shifted to match the coordinates at which the [C ii] line emission peaks."]
  - software: CASA/concat, CASA/tclean
  - parameter: 10 single galaxies; natural weighting; cleaned down to 1.5 sigma with 3" aperture mask; z = 5.22 [4.3.3. [C ii ] deficit in the central r…: "We image both stacked [C ii] line and FIR continuum emission using the `CASA/tclean` task with natural weighting, and clean down to 1.5σ noise level by applying 3′′ aperture mask, where σ is the rms noise level of the dirty image."]
  - assumption: Average redshift z = 5.22 [Figure 10 caption: "The top axis is converted to a physical scale assuming an average redshift of _z_ = 5.22 among the stacked sample."]
  - validation: Compared profiles against noise levels from random apertures on blank regions and re-tested after excluding IR-bright galaxies (CRISTAL-21 and CRISTAL-24). [4.3.3. [C ii ] deficit in the central r…: "Beyond a beam-convolved radius of 1′′, the surface densities of [C ii] line and FIR continuum emission become comparable to the surface densities derived from setting random apertures, and the emission is likely not genuine."] [4.3.3. [C ii ] deficit in the central r…: "However, our interest here is the radial variation in Σ [CII] /Σ IR, and so we have confirmed that the overall trend is unchanged when such exceptionally IR-bright galaxies are excluded from the stacking."]
- step 7: Analyze correlations of [C II] properties with SFR surface density and Lyman-alpha equivalent width
  - method: Perform linear regression fitting and Spearman's rank correlation tests between [C II] size, size ratios, and surface densities against Sigma_SFR_IR and rest-frame EW_Lya. [4.3.1. Outflows: "Figure 9 shows the [C ii] size and [C ii]-to-UV size ratio as a function of the SFR IR surface density (Σ SFR IR = SFR IR /2π_R_ 2 _e_,FIR) of the CRISTAL galaxies."] [4.4. Connection to Ly α and H α emission: "To study how the [C ii] line properties of our sample correlate with Lyα emission, we plot the [C ii] line surface density (Σ [CII] = _L_ [CII] /2π_R_ 2 _e_,[CII]), the [C ii]-to-IR surface density ratio (Σ [CII] /Σ IR) within the [C ii] effective radius, and the [C ii]-to-UV size ratio (_R_ _e_,[CII] /_R_ _e_,UV) as …"]
  - parameter: Rest-frame EW_Lya obtained by multiplying observed-frame EW_Lya by (1 + z)^-1 [4.4. Connection to Ly α and H α emission: "Here, we convert the EW Lyα reported in the observed-frame to the rest-frame by applying a correction factor of (1+ _z_)−1."]
  - fitting: Linear regression fitting (y = m log10 EW_Lya + b) and Spearman's rank correlation test [4.4. Connection to Ly α and H α emission: "We perform a linear regression fitting for each correlation and present the fitting results in Table 3."] [Table 3: "Parameters are determined from the form of _y_ = _m_ log 10 EW Lyα + _b_."]
  - validation: Evaluated p-values of Spearman's rank correlation tests. [4.4 Connection to Lyα and Hα emission: "with a Spearman’s rank correlation coefficient of −0.51 and a _p_ value of 0.039."]
- result: Average [C II] effective radius <Re,[CII]> = 1.90 ± 0.77 kpc [3.2.1. [C ii ] line emission: "We calculate an average value and standard deviation of the [C ii] sizes of ⟨_R_ _e_,[CII]⟩ = 1.90 ± 0.77 kpc."]
- result: Average [C II]-to-UV size ratio <Re,[CII]/Re,UV> (entire sample) = 2.90 ± 1.40 dimensionless [4.1. Size comparison: "The size ratio (_R_ _e_,[CII] /_R_ _e_,UV) ranges from 0.94 (CRISTAL-16) to 5.03 (CRISTAL-20) with the average value and standard deviation of ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.90 ± 1.40."]
- result: Average [C II]-to-FIR size ratio <Re,[CII]/Re,FIR> (entire sample) = 1.54 ± 0.63 dimensionless [4.1. Size comparison: "We calculate the average size ratio and standard deviation of ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.54 ± 0.63."]
- result: Average [C II]-to-UV size ratio <Re,[CII]/Re,UV> (single galaxies) = 3.21 ± 1.42 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Average [C II]-to-FIR size ratio <Re,[CII]/Re,FIR> (single galaxies) = 1.62 ± 0.69 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Average [C II]-to-UV size ratio <Re,[CII]/Re,UV> (pair systems) = 2.38 ± 1.22 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Average [C II]-to-FIR size ratio <Re,[CII]/Re,FIR> (pair systems) = 1.36 ± 0.45 dimensionless [4.1. Size comparison: "For galaxies classified as single, we derive ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 3.21 ± 1.42 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.62 ± 0.69, while for pair systems we find ⟨_R_ _e_,[CII] /_R_ _e_,UV⟩ = 2.38 ± 1.22 and ⟨_R_ _e_,[CII] /_R_ _e_,FIR⟩ = 1.36 ± 0.45."]
- result: Stacked visibility single-component [C II] effective radius Re,[CII] = 1.97 ± 0.10 kpc [4.2 Constituent of [C ii] line emission: "The model is characterized by an effective radius of _R_ _e_,[CII] = 1.97 ± 0.10 kpc"]
- result: Stacked visibility double-component galaxy effective radius Re,gal = 1.91 ± 0.20 kpc [4.2. Constituent of [C ii ] line emissi…: "The brighter component (1.68 ± 0.23 mJy; hereafter “galaxy” component) has a radius of _R_ _e_,gal = 1.91 ± 0.20 kpc, which is similar to the best-fit single component."]
- result: Stacked visibility double-component halo effective radius Re,halo = 9.17 ± 28.2 kpc [4.2. Constituent of [C ii ] line emissi…: "The other component (0.16 ± 0.27 mJy; hereafter “halo” component) has an extended radius of _R_ _e_,halo = 9.17 ± 28.2 kpc."]
- result: Stacked visibility halo flux fraction = 8.7 ± 13.4 % [4.2. Constituent of [C ii ] line emissi…: "The flux of the “halo” component constitutes 8.7 ± 13.4 % of the total flux"]
- result: Stacked image [C II] effective radius Re,[CII] = 1.97 ± 0.17 kpc [4.3.3. [C ii ] deficit in the central r…: "Both [C ii] line and FIR continuum emission exhibit an extended structure beyond the PSF Gaussian profile with an effective radius of 1.97 ± 0.17 kpc and 1.53 ± 0.22 kpc, respectively."]
- result: Stacked image FIR continuum effective radius Re,FIR = 1.53 ± 0.22 kpc [4.3.3. [C ii ] deficit in the central r…: "Both [C ii] line and FIR continuum emission exhibit an extended structure beyond the PSF Gaussian profile with an effective radius of 1.97 ± 0.17 kpc and 1.53 ± 0.22 kpc, respectively."]
- result: CRISTAL-01a [C II] effective radius Re,[CII] = 3.05 ± 1.19 kpc [Table 1: "CRISTAL-01a 10:00:54.508 2:34:34.46 0.68 ± 0.16 789 3.05 ± 1.19 0.59 ± 0.27 21 ± 24 8.62"]
- result: CRISTAL-02 [C II] effective radius Re,[CII] = 2.58 ± 0.28 kpc [Table 1: "CRISTAL-02 10:00:21.499 2:35:11.01 2.63 ± 0.16 533 2.58 ± 0.28 0.52 ± 0.07 153 ± 5 9.31"]
- result: CRISTAL-05 [C II] effective radius Re,[CII] = 1.57 ± 0.28 kpc [Table 1: "CRISTAL-05 10:00:09.422 2:20:13.84 0.94 ± 0.08 523 1.57 ± 0.28 0.31 ± 0.08 160 ± 5 8.90"]
- result: CRISTAL-24 [C II] effective radius Re,[CII] = 3.00 ± 1.03 kpc [Table 1: "CRISTAL-24 10:00:02.715 2:37:39.99 14.76 ± 2.50 1291 3.00 ± 1.03 0.74 ± 0.25 92 ± 31 9.96"]
- result: CRISTAL-25 [C II] effective radius Re,[CII] = 2.45 ± 0.35 kpc [Table 1: "CRISTAL-25 10:01:12.502 2:18:52.55 3.35 ± 0.19 477 2.45 ± 0.35 0.65 ± 0.10 35 ± 10 9.32"]
- result: Spearman correlation coefficient (log10 Sigma_[CII] vs log10 EW_Lya) = -0.51 ± not stated dimensionless [4.4 Connection to Lyα and Hα emission: "with a Spearman’s rank correlation coefficient of −0.51 and a _p_ value of 0.039."]
- limitation (authors): Multiplicity classification is morphological and does not incorporate kinematical state (e.g., CRISTAL-05 appears single in UV/[C II] morphology but is a line-of-sight pair kinematically), and some HST-single sources are pairs in sharper J… [3.1. Classification based on multiplici…: "We note, however, that this is still a crude classification, as we do not consider the dynamical state of each galaxy obtained from kinematical analysis."]
- limitation (authors): Limited sample size prevents statistically distinguishing [C II] size distributions across multiplicity classes and yields large uncertainties in size ratios. [3.2.1. [C ii ] line emission: "Although we expect to find larger [C ii] sizes in pair and multiple-UV systems compared to single systems, we were unable to statistically distinguish their size distributions by performing the Kolmogorov-Smirnov test (with _p_ values of 0.23 and 0.12 for the pair and multiple-UV, respectively), largely due to our lim…"]
- limitation (authors): FIR continuum visibilities have lower S/N than [C II] and were modeled with a single circular exponential disk, preventing fair comparison in multiple-UV and multiple-[C II] systems and yielding an unreliable FIR size for CRISTAL-21. [3.2.2. Rest-frame UV and FIR continuum …: "Unlike [C ii] line emission, all of the FIR continuum emission was fit in a single exponential disk component due to the lower S/N detection compared to the [C ii] line emission."]
- not stated (card): Exact CASA version used for data reduction and analysis; Calibration procedure (pipeline vs manual) and self-calibration details for CRISTAL survey data; Which specific targets used Briggs (R = 0.5) vs Natural (R = 2.0) weighting for initial spectrum extraction; Exact frequency channel ranges used for continuum subtraction in uvcontsub for each target; Exact central frequencies (nu_0) used for sp…

### 2020MNRAS.499.5136C: Missing [C II] emission from early galaxies (2020; high_z_galaxies; archival_reuse)
- question: Does surface brightness dimming explain missing [CII], the [CII]-SFR deficit, and high [OIII]/[CII] ratios at z>6?
- step 1: Align optical and ALMA images
  - method: Match ALMA calibrator and foreground sources to GAIA DR1; compare [CII] and rest-frame UV locations [Observations and data analysis: "The relative astrometry of ALMA and *HST* images have been calibrated by matching ALMA calibrator and foreground sources (if any) to the GAIA Data Release 1 catalogue (cite: Gaia-Collaboration:2016)."]
  - validation: Compare spatial offsets with ALMA astrometric uncertainty [BDF-3299: "In this case the spatial offset is $3.5$ times larger than the $\sigma_p=0.2\ensuremath{''}$ and is unlikely to be related to the astrometric calibration of ALMA dataset."]
- step 2: Find faint extended lines
  - method: Image calibrated data with natural weighting and a taper grid; average frequency channels over trial widths, find peaks, remove duplicates and select the highest-confidence candidate [Observations and data analysis: "We have used a natural weighting that returns the best surface brightness sensitivity."] [Blind-line search method: "The code generates channel maps with different input line widths by averaging the ALMA datacube in frequency."]
  - software: CASA, tclean, customised line finder code, Python
  - parameter: Ten taper values: 0.2'' to 2'' in steps of 0.2'' [SXDF-NB1006-2, A2744-YD4, and MACSJJ149…: "from 0.2$''$ to 2$''$ in steps of 0.2$''$."] [SXDF-NB1006-2, A2744-YD4, and MACSJJ149…: "We have thus generated 10 different ALMA cubes for each target"]
  - parameter: Search within 1000 km s−1 of [OIII] and within 5'' of the UV counterpart [Blind-line search method: "For our study, we have searched candidate lines within 1000 ${\rm km~s^{-1}}$ from the \[O$\scriptstyle\rm III$\] and within 5$''$ from the UV counterpart."]
  - parameter: Trial widths 50–500 km s−1; peak SNR threshold 3.6 [Blind-line search method: "we have used a set of different line widths from 50 ${\rm km~s^{-1}}$ to 500 ${\rm km~s^{-1}}$."] [Blind-line search method: "The SNR threshold of the peaks has been fixed to 3.6"]
  - parameter: Duplicate discrimination: one ALMA beam and |Δv=500| km s−1 [Blind-line search method: "Finally, we have set a distance of one ALMA beam and $|\Delta v = 500|$ ${\rm km~s^{-1}}$ to discriminate duplicates."]
  - assumption: Finder optimised for point-source emission; tapered cubes used to detect extended emission [Blind-line search method: "We note that our line finder code is optimised to detect point-source emission."] [Blind-line search method: "To detect extended emission, we have generated *uv*-tapered datacubes with different angular resolution for each target and run our customised code on them"]
  - validation: Three recovered candidates have significance >3.8σ and redshifts matching either [OIII] or Lyα [SXDF-NB1006-2, A2744-YD4, and MACSJJ149…: "In all three galaxies we have found a candidate line with a significance level $>3.8\sigma$ in the integrated *uv*-tapered map at the redshift of either \[O$\scriptstyle\rm III$\] or Ly$\alpha$ line."]
- step 5: Simulate resolution and sensitivity losses
  - method: Generate mock interferometric observations with simobserve; vary array configuration and exposure time; measure flux with the real-image prescription [Simulations: "We have used the `simobserve` task of `CASA` to produce mock interferometric observations of galaxies at $z\sim7$."] [Simulations: "In the second set of mock interferometric data we have run several simulations for each array configuration with different t$_{\rm exp}$."]
  - software: CASA, simobserve, ALMA exposure time calculator
  - parameter: First set: 100 synthetic observations for each of the five most compact configurations at 230 and 410 GHz [Simulations: "we have computed 100 synthetic observations for each of the five most compact array configurations at the observed line frequencies of 230 GHz and 410 GHz"]
  - parameter: Fixed exposure times: [CII] 16 minutes; [OIII] 6.5 hours; point-source significance ~10σ [Simulations: "t$_{\rm exp}$ = 16 minutes for the \[C$\scriptstyle\rm II$\] pointings and t$_{\rm exp}$ = 6.5 hours for the \[O$\scriptstyle\rm III$\] pointings."] [Simulations: "Such t$_{\rm exp}$ enable the detection of the two FIR lines with a level of significance of $\sim$10$\sigma$ if the target is a point-like source."]
  - parameter: Variable-exposure simulations: 0.4''<θ_beam<2''; 5<σ<140 mJy km s−1 beam−1 [Simulations: "($0.4\ensuremath{''}<\theta_{\rm beam}<2\ensuremath{''}$)"] [Simulations: "($5~{\rm mJy~km s^{-1}~beam^{-1}} < \sigma < 140~{\rm mJy~km~s^{-1}~beam^{-1}}$)."]
  - assumption: 2D Gaussian surface brightness; [CII] and [OIII] major axes 0.8'' and 0.45''; random axis ratio 0.1<b/a<1.0 and position angle [Simulations: "we have used a 2D Gaussian profile"] [Simulations: "fixed to 0.8$''$ ($\approx4.6$ kpc) and 0.45$''$ ($\approx2.6$ kpc), respectively for the two FIR lines."]
  - assumption: Both luminosities 5×10^8 L⊙; fluxes 0.43 and 0.21 Jy km s−1; width 200 km s−1 [Simulations: "For simplicity, we have assumed $L_{\rm [CII]}$ = $L_{\rm [OIII]}$ = $5\times10^{8}$ L${_\odot}$ for all mock sources."] [Simulations: "set the integrated flux density to 0.43 Jy ${\rm km~s^{-1}}$ for the \[C$\scriptstyle\rm II$\] sources and 0.21 Jy ${\rm km~s^{-1}}$ for the \[O$\scriptstyle\rm III$\] mock targets, and assumed a line width of 200 ${\rm km~s^{-1}}$."]
  - validation: Unresolved mock-source luminosities match inputs and SNR agrees with ETC; peak>10σ images recover flux within 10% [Simulations with fixed exposure times: "The measured line luminosities are consistent with our input values as well."] [Simulations with fixed exposure times: "which is consistent with that returned by the ALMA ETC."]
- step 6: Validate missing-flux predictions on repeat observations
  - method: Compare HZ1, HZ3 and HZ4 in C12 and L17 at similar sensitivity; use fixed target-specific velocity windows and the same flux prescription [Comparing mock data with observations: "we have analysed only three sources, HZ1, HZ3, and HZ4"] [Data calibration and analysis of HZ1, H…: "collapsing the datacubes over a fixed velocity range, depending on the target, for both datasets."]
  - software: CASA, imfit
  - parameter: C12=2012.1.00523.S; L17=2017.1.00428.L; nominal angular resolutions 0.7'' and 1'' [Comparing mock data with observations: "The two datasets, 2012.1.00523.S and 2017.1.00428.L (hereafter C12 and L17), have an angular resolution of $0.7\ensuremath{''}$ and $1\ensuremath{''}$, respectively."]
  - parameter: Split HZ4 L17 data into six parts and use one part to match C12 noise [Data calibration and analysis of HZ1, H…: "split the 2017.1.00428.L, i.e. ALPINE, dataset in six ($\approx2.5^2$) parts and generated the \[C$\scriptstyle\rm II$\] datacube from one of the various sub-datasets"] [Data calibration and analysis of HZ1, H…: "a noise level as high as that of the 2012.1.00523.S program"]
  - parameter: Normalise each predicted curve to weighted mean flux at the average θ_beam/D_source of the two datasets [Comparing mock data with observations: "For each target we normalise the prediction curve to the weighted mean flux at the average $\theta_{\rm beam}$/D$_{\rm source}$ values of the two datasets."]
  - assumption: Exclude other overlapping sources with multi-component morphology [Comparing mock data with observations: "the other targets show a multi-component morphology (cite: Carniani:2018) that would lead to a more complex and ambiguous interpretation with respect to current simulations."]
  - fitting: CASA imfit for deconvolved [CII] sizes [Data calibration and analysis of HZ1, H…: "We have also used the `imfit` task in `CASA` to estimate the deconvolved size of \[C$\scriptstyle\rm II$\] emission."]
  - validation: Simulations agree with observed flux differences; fluxes and extents agree with published measurements [Comparing mock data with observations: "The simulations are fully consistent with the observations"] [Data calibration and analysis of HZ1, H…: "source extension estimates are in agreement within the error with those reported by (cite: Capak:2015), (cite: Bethermin:2020), and (cite: Fujimoto:2020)."]
- step 7: Correct luminosities for missing extended emission
  - method: Apply simulation-derived flux corrections using beam size, detection SNR and emission extent; correct individual components when appropriate [\[C$\scriptstyle\rm II$\] as tracer of …: "Based on our simulations, we have corrected the observed \[C$\scriptstyle\rm II$\] luminosities depending on the ALMA beam, SNR of the detection, and extent of \[C$\scriptstyle\rm II$\] emission."] [Comparing mock data with observations: "the correction factor can be applied to each individual component with its relative size."]
  - parameter: Measured/input flux table indexed by SNR and θ_beam/D_source [Results from ALMA simulations: "the ratio between the measured flux density and the input model as a function of signal-to-noise ratio of the detection and the angular resolution normalised by the source size."]
  - assumption: For upper limits, [CII] extent about twice UV extent [\[C$\scriptstyle\rm II$\] as tracer of …: "we assume that the \[C$\scriptstyle\rm II$\] line is about two times larger than the UV (cite: Carniani:2018; Fujimoto:2020)."]
  - assumption: Conditional MS0451-H correction assumes [CII] as extended as the UV region [MS0451-H: "If we assume that the \[C$\scriptstyle\rm II$\] emission is as extended as the UV region, our simulations expect that $\sim60-80\%$ of the carbon emission is missed in current ALMA observations."]
  - validation: Validated on repeat HZ observations; correction uncertainty limits total-flux accuracy to ~20%-30% [Comparing mock data with observations: "The simulations are fully consistent with the observations"] [Comparing mock data with observations: "the total flux cannot be estimated with an error lower than $\sim20\%-30\%$."]
- step 8: Estimate uniform total SFRs
  - method: For continuum detections add SFR_IR from FIR luminosity to SFR_UV; otherwise use SFR_UV without dust correction; associate [CII] and UV components [\[C$\scriptstyle\rm II$\] as tracer of …: "the total SFR has been estimated by adding the SFR$_{\rm IR}$ based on $L_{\rm FIR}$ to the SFR$_{\rm UV}$ calculated from the UV luminosity."] [\[C$\scriptstyle\rm II$\] as tracer of …: "we have assumed a total SFR$\approx$SFR$_{\rm UV}$ with no dust correction for those galaxies without continuum detection."]
  - parameter: Modified blackbody: T_dust=40 K; β=1.5 [\[C$\scriptstyle\rm II$\] as tracer of …: "We have used a modified blackbody with dust temperature $T_{\rm dust} = 40$ K and emissivity index $\beta=1.5$"]
  - parameter: Asymmetric uncertainty −0.2 dex, +0.4 dex on L_FIR, SFR_IR and total SFR [\[C$\scriptstyle\rm II$\] as tracer of …: "we have associated an asymmetric uncertainty of -0.2 dex and +0.4 dex to the $L_{\rm FIR}$ estimates, and thus to the SFR$_{\rm IR}$ and total SFR."]
  - assumption: Kennicutt:2012 SFR relations; kroupa:01 IMF [Introduction: "SFR estimates have been calculated by using the relations reported in (cite: Kennicutt:2012), assuming a (cite: kroupa:01) IMF."]
  - fitting: Modified blackbody to reproduce FIR emission; optimizer and likelihood not stated [\[C$\scriptstyle\rm II$\] as tracer of …: "We have used a modified blackbody with dust temperature $T_{\rm dust} = 40$ K and emissivity index $\beta=1.5$ to reproduce the FIR emission"]
  - validation: Compare UV+FIR SFRs with literature SED-fitting SFRs for the nine targets [\[C$\scriptstyle\rm II$\] as tracer of …: "by adopting both the SFR estimated from the UV+FIR luminosity, or from SED fitting, when available in the literature."]
- step 9: Fit the [CII]-SFR relation and redshift offsets
  - method: Include all ALMA-observed z>6 star-forming galaxies; fit the corrected log luminosity–log SFR relation and linear redshift dependence of offsets; compare corrected and uncorrected samples [\[C$\scriptstyle\rm II$\] as tracer of …: "in this analysis we include all star-forming galaxies at $z>6$ observed with ALMA so far."] [\[C$\scriptstyle\rm II$\] as tracer of …: "The resulting best fit for the SBD-corrected data is $\log L_{\rm [CII]} = (1.1\pm0.2)\log SFR + (6.8\pm0.2)$"]
  - assumption: Use UV+FIR SFR for comparison with the local relation [\[C$\scriptstyle\rm II$\] as tracer of …: "In the rest of the work, we use the SFR from UV+FIR luminosity since it is the same method used to determine the local $L_{\rm [CII]}$-SFR relation (cite: De-Looze:2014)."]
  - fitting: Best-fit log L_[CII] versus log SFR; linear fits of offset Δ versus z; sampler, priors, likelihood and upper-limit treatment not stated [\[C$\scriptstyle\rm II$\] as tracer of …: "The resulting best fit for the SBD-corrected data is $\log L_{\rm [CII]} = (1.1\pm0.2)\log SFR + (6.8\pm0.2)$"] [\[C$\scriptstyle\rm II$\] as tracer of …: "A linear fit of the total sample gives:"]
  - validation: Compare with De-Looze:2014 local relation and Schaerer:2020 z=4-5 fit; test sensitivity to SED-based SFRs [\[C$\scriptstyle\rm II$\] as tracer of …: "consistent within the errors with both the local relation by (cite: De-Looze:2014) and the $z=4-5$ fitting result reported by (cite: Schaerer:2020)."] [\[C$\scriptstyle\rm II$\] as tracer of …: "if we adopt the SFR from SED fitting, high-$z$ galaxies appear systematically below the local relation."]
- step 10: Compare corrected FIR line ratios
  - method: Calculate [OIII]/[CII] before and after missing-flux corrections; inspect dependence on SFR and UV+FIR bolometric luminosity [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "the line ratios have been estimated directly from the measurements"] [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "the line luminosities have been corrected for the “missing” extended emission due to the effect of the SBD"]
  - parameter: Correction factors depend on angular resolution, emission size and detection SNR [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "depending on the angular resolution, emission size, and SNR of the detections."]
  - assumption: Uniform total SFR based on UV and IR luminosities [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "we adopt a uniform approach to estimate the total SFR of each galaxy, which is based on the L$_{\rm UV}$ and L$_{\rm IR}$"]
  - validation: Compare ratios with local dwarf galaxies and published simulations [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "more consistent with local dwarf galaxies (cite: Madden:2013; Cormier:2015) and simulations (cite: Pallottini:2017a; Pallottini:2019; Katz:2019; Arata:2020; Lupi:2020b)"]
- step 11: Interpret corrected line-to-SFR ratios
  - method: Compare updated [CII]/SFR estimates with Harikane:2019 Cloudy calculations [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "By using Cloudy calculations, (cite: Harikane:2019)"] [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "The new $L_{\rm [CII]}$/SFR estimates locate the high-$z$ galaxies in the range $6.4< \log(L_{\rm [CII]}/SFR)<7.4$"]
  - software: Cloudy (published calculations)
  - assumption: Interpret line ratios through ISM properties including PDR covering fraction, density, metallicity and C/O abundance [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "As discussed in (cite: Harikane:2019), the $L_{\rm [OIII]}$/$L_{\rm [CII]}$ depends mainly on ISM properties such as PDR covering fraction, density, metallicity, and C/O abundance ratio."]
  - validation: Updated data still require log U_ion≈−2 and PDR covering fraction 10% in the published interpretation [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "$\log U_{\rm ion}\approx -2$ and a PDR covering fraction of 10% are still requested to reproduce $L_{\rm [CII]}$/SFR ratios."]
- result: BDF-3299 [CII] displacement from UV emission = ~0.7 ± not stated arcsec [BDF-3299: "spatially offset by $\sim0.7$$''$ ($\sim3.7$ kpc) from the UV emission"]
- result: Simulated missing [CII] flux when beam is comparable to source size = 20-40 ± not stated % [Comparing mock data with observations: "predicting that we miss 20-40% of the total flux when the ALMA beam size is similar to the \[C$\scriptstyle\rm II$\] extension"]
- result: Maximum missing-flux fraction for SNR<5 = 70 ± not stated % [Summary and Conclusions: "The fraction of missing flux increases up to 70% when the line is detected with a SNR$<5$."]
- result: Mock [OIII]/[CII] line-ratio bias at ~1 arcsec = 1.15 ± not stated dimensionless [Simulations with fixed exposure times: "At angular resolutions of $\sim1$$''$ we infer an average line ratio that is 1.15 times larger than the input value."]
- result: Mock [OIII]/[CII] ratio at 0.6 arcsec; intrinsic ratio=1 = 1.35 ± not stated dimensionless [Simulations with fixed exposure times: "specifically: 1.35 and 2.1 at 0.6$''$ and 0.4$''$, respectively."]
- result: Mock [OIII]/[CII] ratio at 0.4 arcsec; intrinsic ratio=1 = 2.1 ± not stated dimensionless [Simulations with fixed exposure times: "specifically: 1.35 and 2.1 at 0.6$''$ and 0.4$''$, respectively."]
- result: HZ1 [CII] integrated flux, L17 = 0.58 ± ±0.08 Jy km s−1 [Table 2: "$0.58\pm0.08$"]
- result: HZ1 [CII] integrated flux, C12 = 0.36 ± ±0.09 Jy km s−1 [Table 2: "$0.36\pm0.09$"]
- result: HZ3 [CII] integrated flux, L17 = 0.92 ± ±0.08 Jy km s−1 [Table 2: "$0.92\pm0.08$"]
- result: HZ3 [CII] integrated flux, C12 = 0.67 ± ±0.15 Jy km s−1 [Table 2: "$0.67\pm0.15$"]
- result: HZ4 [CII] integrated flux, full L17 = 0.89 ± ±0.05 Jy km s−1 [Table 2: "$0.89\pm0.05$"]
- result: HZ4 [CII] integrated flux, noise-matched cropped L17 = 0.87 ± ±0.18 Jy km s−1 [Table 2: "($0.87\pm0.18$)$^{(c)}$"]
- result: HZ4 [CII] integrated flux, C12 = 0.64 ± ±0.16 Jy km s−1 [Table 2: "$0.64\pm0.16$"]
- result: Corrected log L_[CII]–log SFR slope = 1.1 ± ±0.2 dimensionless [\[C$\scriptstyle\rm II$\] as tracer of …: "$\log L_{\rm [CII]} = (1.1\pm0.2)\log SFR + (6.8\pm0.2)$"]
- result: Corrected log L_[CII]–log SFR intercept = 6.8 ± ±0.2 dimensionless [\[C$\scriptstyle\rm II$\] as tracer of …: "$\log L_{\rm [CII]} = (1.1\pm0.2)\log SFR + (6.8\pm0.2)$"]
- result: MACS1149-JD1 SBD-corrected [OIII]/[CII] = 4.2 ± ±1.4 dimensionless [Individual targets: results: "$4.2\pm1.4$"]
- result: A2744-YD4 SBD-corrected [OIII]/[CII] = 3.2 ± ±1.3 dimensionless [Individual targets: results: "$3.2\pm1.3$"]
- result: MACSJ0416-Y1 SBD-corrected [OIII]/[CII] = 8 ± ±2 dimensionless [Individual targets: results: "$8\pm2$"]
- result: SXDF-NB1006-2 SBD-corrected [OIII]/[CII] = 4.3 ± ±1.4 dimensionless [Individual targets: results: "$4.3\pm1.4$"]
- result: B14-65666 SBD-corrected [OIII]/[CII] = 2.8 ± ±0.5 dimensionless [Individual targets: results: "$2.8\pm0.5$"]
- result: BDF-3329 table entry SBD-corrected [OIII]/[CII] = 1.8 ± ±0.5 dimensionless [Individual targets: results: "$1.8\pm0.5$"]
- result: J0217 SBD-corrected [OIII]/[CII] = 5.7 ± ±0.9 dimensionless [Individual targets: results: "$5.7\pm0.9$"]
- result: J0235 SBD-corrected [OIII]/[CII] = 7.8 ± ±1.4 dimensionless [Individual targets: results: "$7.8\pm1.4$"]
- result: J1211 SBD-corrected [OIII]/[CII] = 3.4 ± ±0.6 dimensionless [Individual targets: results: "$3.4\pm0.6$"]
- result: Ionisation parameter required by published-model interpretation of updated data = ≈-2 ± not stated dimensionless [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "$\log U_{\rm ion}\approx -2$ and a PDR covering fraction of 10% are still requested to reproduce $L_{\rm [CII]}$/SFR ratios."]
- result: PDR covering fraction required by published-model interpretation of updated data = 10 ± not stated % [\[O$\scriptstyle\rm III$\] over \[C$\sc…: "$\log U_{\rm ion}\approx -2$ and a PDR covering fraction of 10% are still requested to reproduce $L_{\rm [CII]}$/SFR ratios."]
- result: MS0451-H potential [CII] line SNR = 4.2 ± not stated dimensionless [MS0451-H: "The \[C$\scriptstyle\rm II$\] emission is detected in the integrated map with an SNR $= 4.2$"]
- result: MS0451-H conditional total [CII] luminosity after SBD correction = 1.2-2.4×10^6(μ/100) ± not stated L⊙ [MS0451-H: "$= 1.2-2.4\times 10^{6}(\mu/100)$ L${_\odot}$"]
- limitation (authors): Correction-factor uncertainty prevents total-flux accuracy better than ~20%-30% [Comparing mock data with observations: "the correction factors suffer from large uncertainty and the total flux cannot be estimated with an error lower than $\sim20\%-30\%$."]
- limitation (authors): Correction factors may be inappropriate for very complicated morphologies [Comparing mock data with observations: "Moreover, our correction factors may not be appropriate for very complicated morphologies."]
- limitation (authors): Low statistics above z=7 prevent a definitive evolution measurement [\[C$\scriptstyle\rm II$\] as tracer of …: "the low statistics at $z>7$ does not allow us to determine definitively whether the $L_{\rm [CII]}$-SFR relation evolves with redshift or not."]
- not stated (card): Complete target-to-project mapping, exact target coordinates, spectral-window selections and native channel widths.; Numerical CASA and pipeline versions for each dataset; these are deferred to archive pipeline scripts.; tclean deconvolver, image dimensions, cleaning masks, stopping thresholds and exact per-cube imaging commands.; Whether continuum subtraction was performed and, if so, its task, …

### 2018MNRAS.481.1976Z: The [C II] emission as a molecular gas mass tracer in galaxies at low and high redshifts (2018; high_z_galaxies; observational_alma_primary)
- question: Are z~2 main-sequence galaxies [C II] deficient, and what physical parameter drives [C II] luminosity (is [C II] an empirical molecular gas mass tracer)?
- step 4: Search for [C II] emission by iterative uv-plane spectral extraction
  - method: Fit a source model (PSF, Gaussian or exponential) in the uv plane channel by channel to all four sidebands at the astrometry-corrected HST position; average channels maximising S/N, refit position, and iterate to convergence [2.3 [C II] emission line measurements: "to all four sidebands and channel per channel"] [2.3 [C II] emission line measurements: "we averaged the data over the channels maximizing the detection S/N"]
  - software: GILDAS
  - parameter: Secure detection: emission line significance > 5 sigma in the optimal channel range [2.3.1 Individual [C II] detections: "they have emission line significance $> 5 \sigma$ in the optimal channel range"]
  - validation: Detections robust against the model used for the 1D spectrum extraction; positions consistent with HST peaks [2.3.1 Individual [C II] detections: "The detections are robust against the model used for the extraction of the 1D spectra"]
- step 5: Measure [C II] redshifts of detections
  - method: Signal-weighted mean frequency within the line channels and Gaussian fit of the 1D spectrum [2.3.1 Individual [C II] detections: "1) we computed the signal-weighted average frequency within the line channels, and 2) we fitted the 1D spectrum with a Gaussian function"]
  - software: GILDAS
  - fitting: Gaussian fit to the 1D spectrum (details not stated) [2.3.1 Individual [C II] detections: "2) we fitted the 1D spectrum with a Gaussian function"]
  - validation: Compared with optical redshifts: no systematic difference, MAD of 200 km/s [2.3.1 Individual [C II] detections: "They generally agree, with no significant systematic difference and a median absolute deviation (MAD) of 200 km s$^{-1}$"]
- step 6: Measure total [C II] fluxes of the four detections
  - method: Fit velocity-averaged line maps in the uv plane with the Fourier transform of a 2D exponential with fixed size and centre from the optical images (GILDAS uv_fit) [2.3.1 Individual [C II] detections: "by fitting their average emission line maps in the *uv* plane with exponential models"] [2.3 [C II] emission line measurements: "We fixed the size and center of the model on the basis of the effective radius and peak coordinates derived from the optical images"]
  - software: GILDAS, CASA
  - parameter: Exponential model size = effective radius from HST stellar mass map (R_e in Table 2) [2.3 [C II] emission line measurements: "We fixed the size and center of the model on the basis of the effective radius and peak coordinates derived from the optical images"]
  - assumption: [C II] emission follows an exponential disk with the optical size; a PSF model would underestimate fluxes [2.3.1 Individual [C II] detections: "whereas by using a PSF model instead we would have underestimated the fluxes"]
  - fitting: uv-plane model fit with GILDAS; uncertainties from the fit [2.3 [C II] emission line measurements: "We then extracted the"]
  - validation: CASA uvmodelfit gives consistent fluxes; Gaussian model also consistent; channel-to-channel scatter consistent with errors [2.3.1 Individual [C II] detections: "We checked that fluxes and uncertainties determined with the `uvmodelfit` task provided by CASA would give consistent results."] [2.3.1 Individual [C II] detections: "we verified that the uncertainties associated to the flux measurement in each channel are consistent with the channel to channel fluctuations"]
- step 7: Stack the four detections to measure the average [C II] size
  - method: Align detections at HST positions, co-add visibilities and fit an exponential profile with free size [2.3.1 Individual [C II] detections: "stacked them (coadding all visibilities) to increase the S/N"] [2.3.1 Individual [C II] detections: "We then fitted the stacked data with an exponential profile, leaving its size free to vary during the fit."]
  - software: GILDAS
  - fitting: Exponential profile with free scale length fitted in uv space [2.3.1 Individual [C II] detections: "We then fitted the stacked data with an exponential profile, leaving its size free to vary during the fit."]
  - validation: Size uncertainty from GILDAS checked against amplitude versus uv range; unresolved-source probability < 1e-5 [2.3.1 Individual [C II] detections: "The reported size uncertainty was estimated by GILDAS in the fit and the modelling of the signal amplitude versus *uv* range signal shows that it is reliable"]
- step 8: Tentative detections, upper limits and average [C II] stack
  - method: For undetected sources, measure at fixed HST position with exponential models of fixed optical size, averaging over 719 km/s around the optical redshift; 3 sigma upper limits; stack detections plus tentative detections plus ID2910 in the u… [2.3.2 Tentative and non detections: "using exponential models with the fixed optical size for each galaxy and conservatively averaging"] [2.3.2 Tentative and non detections: "For the four sources with no detected signal we considered $3\sigma$ flux upper limits"]
  - software: GILDAS
  - parameter: Line map averaged over 719 km/s (3 x MAD redshift accuracy summed in quadrature with average detected line FWHM) [2.3.2 Tentative and non detections: "we created emission line maps by averaging channels over 719 km s$^{-1}$"]
  - parameter: Rest-frame 158 um continuum removed from the stack by reducing the flux by 10% [2.3.3 Average [C II] signal: "We finally subtracted the contribution of the rest-frame 158 $\mu$m continuum by decreasing the estimated flux by 10%"]
  - assumption: Stack size fixed to the average optical size of the sources entering the stack [2.3.3 Average [C II] signal: "We fitted the resulting map with an exponential model with size fixed to the average optical size of the sources entering the stacking."]
  - validation: Expected false detections < 0.1 among the six sources for the 2.3 sigma tentative signals; average ratio from stacking agrees with the mean of individual ratios [2.3.2 Tentative and non detections: "Furthermore, when considering the six sources discussed above, we expect to find $<0.1$ false detections."]
- step 10: Estimate molecular gas masses of the sample
  - method: (1) M_mol = delta_GDR x M_dust with metallicity from stellar mass via a mass-metallicity relation; (2) integrated Schmidt-Kennicutt relation from SFR; the Schmidt-Kennicutt masses are adopted; [C II]-based masses use alpha_[CII] = 31 Msun/… [2.4 Continuum emission: "Given their stellar mass and the mass-metallicity relation by (cite: Zahid2014) we estimated their gas phase metallicity."] [2.4 Continuum emission: "In the following we use the $M_{\mathrm{mol}}$ obtained from the Schmit-Kennicutt relation"]
  - parameter: SFR = 1e-10 L_IR (Kennicutt 1998); SK relation dispersion 0.2 dex [Table 2: "$SFR = 10^{-10}L_{\mathrm{IR}}$"]
  - assumption: Chabrier IMF; flat LCDM with Om = 0.3, OL = 0.7, H0 = 70 [1 Introduction: "We assumed a (cite: Chabrier2003) initial mass function (IMF)"]
  - validation: Dust-based and Schmidt-Kennicutt gas masses consistent for galaxies with 850 um detections [2.4 Continuum emission: "we concluded that both methods give consistent results"]
- step 11: Compile literature samples and fit L_[CII] versus M_mol and alpha_[CII]
  - method: Homogenise literature samples (IR luminosities to 8-1000 um, metallicities to Pettini2004 calibration, alpha_CO = f(metallicity) for CO-based masses), fit the log-log L_[CII]-M_mol relation, and compute alpha_[CII] = L_[CII]/M_mol medians … [C. Literature data: "Also we homogenized all the IR luminosities reporting them to the 8 – 1000 $\mu$m range."] [3.4 Invariance of alpha_[CII] with gas …: "we converted all metallicity estimates to the calibration by (cite: Pettini2004) using the parametrizations by (cite: Kewley2008)"]
  - parameter: alpha_CO metallicity dependence: log alpha_CO = 0.64 - 1.5 (12 + log(O/H) - 8.7) [3.4 Invariance of alpha_[CII] with gas …: "\log \alpha_{\mathrm{CO}} = 0.64 - 1.5 (12 + \log (O/H) - 8.7)"]
  - assumption: alpha_CO slope of -1 or -2 would not change conclusions [3.4 Invariance of alpha_[CII] with gas …: "would not change our conclusions"]
  - fitting: Linear fit in log space; Pearson correlation coefficient quoted [3.2 [C II] as a tracer of molecular gas: "The Pearson test yields a coefficient $\rho = 0.97$"]
  - validation: Scatter of L_[CII]-L'_CO relation compared with that of alpha_[CII]; starburst (SPT) and local samples compared [3.2 [C II] as a tracer of molecular gas: "The mean absolute deviation of the relation is $\sim$ 0.2 dex, similar to that of the $L_{\rm [C~{\small II}]}$ - $M_{\rm mol}$ relation."]
- step 12: Compare L_[CII]/L_IR versus sSFR/sSFR_MS with depletion-time models
  - method: Bin samples by distance from the main sequence, overplot Sargent2014 and Scoville2017 depletion-time models rescaled to the main-sequence [CII]/IR ratio and convolved with a 0.2 dex Gaussian [3.3 The dependence of the [C II]-to-IR …: "predicting how the depletion time of galaxies changes as a function of their distance from the main-sequence and rescaled them"] [3.3 The dependence of the [C II]-to-IR …: "we convolved the models by (cite: Sargent2014) and (cite: Scoville2017) with a Gaussian function with FWHM $\sim$ 0.2 dex"]
  - parameter: Rescaling implies L_[CII]/L_CO ~ 6000 [3.3 The dependence of the [C II]-to-IR …: "we estimated $L_{\mathrm{[C~{\small II}]}}/L_{\mathrm{CO}} \sim 6000$"]
  - assumption: Starbursts defined as > 4 times above the main sequence [1 Introduction: "Throughout this paper we will consider as starbursts all the sources that fall $> 4$ times above the main sequence (cite: Rodighiero2011)."]
  - validation: Rescaled [CII]/CO ratio compared with the 2000-10000 range in the literature [3.3 The dependence of the [C II]-to-IR …: "This is in good agreement with the typical values reported in the literature and ranging between 2000 – 10000"]
- step 13: Test dependence of alpha_[CII] on metallicity and of L_[CII]/SFR on metallicity
  - method: Linear fits of alpha_[CII] versus metallicity and of L_[CII]/SFR_TOT versus SFR_IR/SFR_TOT and metallicity for local low-metallicity galaxies [3.4 Invariance of alpha_[CII] with gas …: "When fitting the data with a linear function we obtain a slope of $-0.2 \pm 0.2$"]
  - assumption: SFR estimates from the literature taken at face value [3.5 Implications for surveys at z > 2: "taking at face value the SFR estimates from the literature"]
  - fitting: Linear fits with quoted slopes and scatter [3.4 Invariance of alpha_[CII] with gas …: "and a standard deviation of 0.3 dex"]
- result: [C II] luminosity, ID9347 (detection) = 0.95 ± 0.30 1e9 Lsun [Table 1: "21.28 $\pm$ 6.73 | 0.95 $\pm$ 0.30 | 11.80 $\pm$ 0.05 | $1.51^{+0.51}_{-0.50}$"]
- result: [C II] luminosity, ID6515 (detection) = 1.23 ± 0.33 1e9 Lsun [Table 1: "24.50 $\pm$ 6.57 | 1.23 $\pm$ 0.33 | 11.68 $\pm$ 0.04 | $2.57^{+0.73}_{-0.73}$"]
- result: [C II] luminosity, ID10076 (detection) = 2.40 ± 0.76 1e9 Lsun [Table 1: "29.03 $\pm$ 9.14 | 2.40 $\pm$ 0.76 | 11.91 $\pm$ 0.03 | $2.95^{+0.96}_{-0.96}$"]
- result: [C II] luminosity, ID9834 (detection) = 1.29 ± 0.19 1e9 Lsun [Table 1: "15.34 $\pm$ 2.21 | 1.29 $\pm$ 0.19 | 11.99 $\pm$ 0.02 | $1.32^{+0.22}_{-0.22}$"]
- result: [C II] flux and luminosity of the average stack (7 galaxies) = F_[CII] = 15.59 mJy; L_[CII] = 1.25 (1e9 Lsun) ± 1.79 (flux); 0.14 (luminosity) mJy; 1e9 Lsun [Table 1: "15.59 $\pm$ 1.79 | 1.25 $\pm$ 0.14 | 11.81 $\pm$ 0.05"]
- result: Average L_[CII]/L_IR of the stack = 1.94e-3 ± +0.34/-0.32 (1e-3) dimensionless [2.3.3 Average [C II] signal: "stacking of the seven targets mentioned above is $(1.94^{+0.34}_{-0.32})\times 10^{-3}$"]
- result: [C II] exponential scale length of the 4-detection stack = 0.65 arcsec (~4-7 kpc) ± 0.15 arcsec arcsec [2.3.1 Individual [C II] detections: "$0.65\pm0.15''$ (corresponding to $\sim$ 4 – 7 kpc)"]
- result: Average L_[CII]/L_IR of our data and scatter = ~1.9e-3; scatter ~0.15 dex ± not stated dimensionless [3.1 The [C II] deficit: "The average $L_{\mathrm{[C~{\small II}]}}/L_{\mathrm{IR}}$ ratio of our data is $\sim 1.9 \times 10^{-3}$, and has a scatter of $\sim$ 0.15 dex"]
- result: L_[CII]-M_mol relation: log L = -1.28 + 0.98 log M_mol (dispersion 0.3 dex) = intercept -1.28, slope 0.98 ± +/-0.21 (intercept), +/-0.02 (slope) dimensionless [3.2 [C II] as a tracer of molecular gas: "\log L_{\mathrm{[C~{\small II}]}} = -1.28(\pm 0.21) + 0.98(\pm 0.02) \log M_{\mathrm{mol}}"]
- result: Median alpha_[CII] for main-sequence galaxies = 31 ± MAD 0.2 dex (standard deviation 0.3 dex) Msun/Lsun [3.2 [C II] as a tracer of molecular gas: "we get a median $\alpha_{\mathrm{[C~{\small II}]}} = 31$ M$_\odot$/L$_\odot$ with a median absolute deviation of 0.2 dex"]
- result: Median alpha_[CII], local sample = 28 ± MAD 0.2 dex Msun/Lsun [Table 3 (alpha_[CII] estimates): "| Local | 30 | 0.3 | 28 | 0.2 |"]
- result: Median alpha_[CII], high-z sample = 38 ± MAD 0.1 dex Msun/Lsun [Table 3 (alpha_[CII] estimates): "| High-$z$ | 35 | 0.2 | 38 | 0.1 |"]
- result: Median alpha_[CII], SPT lensed starburst sample = 22 ± not stated Msun/Lsun [3.2 [C II] as a tracer of molecular gas: "We obtained a median $\alpha_{\mathrm{[CII]}} = 22$ M$_\odot$/L$_\odot$ for this sample"]
- result: L_[CII]/L_CO implied by rescaled depletion-time models = ~6000 ± not stated dimensionless [3.3 The dependence of the [C II]-to-IR …: "we estimated $L_{\mathrm{[C~{\small II}]}}/L_{\mathrm{CO}} \sim 6000$"]
- result: Slope of alpha_[CII] versus metallicity = -0.2 ± 0.2 dimensionless [3.4 Invariance of alpha_[CII] with gas …: "we obtain a slope of $-0.2 \pm 0.2$"]
- result: Fit of L_[CII]/SFR_TOT versus metallicity: intercept and slope = intercept -3.8, slope 1.3 (dispersion 0.2 dex) ± +/-2.8, +/-0.3 dimensionless [3.5 Implications for surveys at z > 2: "-3.8(\pm 2.8) + 1.3(\pm 0.3) [12 + \log (O/H)]"]
- limitation (authors): Fluxes depend critically on the assumed model size taken from optical images [2.3.1 Individual [C II] detections: "However, the returned fluxes critically depend on the model size that we used and that we determined from the optical images."]
- limitation (authors): Source size cannot be constrained from individual sources because of low S/N [2.3.1 Individual [C II] detections: "Unfortunately, the size of the emission cannot be constrained from the data on individual sources, given the limited S/N ratio."]
- limitation (authors): Observed in a more extended configuration than requested, giving 5-10 times higher flux errors [2.2 Details of ALMA observations: "Our sources were therefore resolved."]
- not stated (card): CASA and pipeline version used for the Band 9 and Band 7 reductions, and whether the archive-delivered calibration was used as is; Flux, bandpass and phase calibrators and the Band 9 flux scale uncertainty; Whether any self-calibration was done; Which array (12-m / 7-m) and antenna numbers were used; Exact channel ranges (optimal channel range) used for each detection and the line-free channels u…

### 2025ApJ...987L..37W: Gas-poor Hosts and Gas-rich Companions of z ≍ 3.5 Radio Active Galactic Nuclei: ALMA Insights into Jet Triggering and Feedback (2025; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Where is the cold gas (traced by [C II] and [C I]) around four z~3.5 radio AGN: in the host galaxies or in nearby companion clouds, and what does that imply for jet triggering and feedback?
- step 1: Image the ALMA Band 8 data into [C II] cubes and continuum maps
  - method: tclean with Briggs weighting; [C II] cubes from two combined spectral windows at 14 km/s per channel; continuum maps from single spectral windows [Sample and data: "We cleaned the ALMA data via the task `tclean` using the Common Astronomy Software Applications for Radio Astronomy v6.6.0"] [Sample and data: "The final \[C II\] cubes, constructed with two spectral windows combined, have $\Delta v=14\,\rm km\,s^{-1}$ per channel."]
  - software: CASA v6.6.0, tclean
  - parameter: robust = +0.5 (1.7 h fields) and +2.0 (0.8 h fields) [Sample and data: "Briggs weighting of robust$=+0.5$ for the two targets with 1.7 hours of exposure each (TN J0121+1320 and 4C+19.71) and robust$=+2.0$ for the other two with 0.8 hours of exposure each (TN J0205+2242 and 4C+03.24)"]
- step 2: Select the [C II] companions
  - method: Visual check over the Band 8 primary beam and spectral bandwidth, then S/N >~ 3 over 125 km/s and spectral validation (summary of the companion-paper selection) [Analysis: "The \[C II\] companions are selected first based on visual check in the field of ALMA Band 8 primary beam ($\sim10\ensuremath{''}\times10\ensuremath{''}$) over the spectral bandwidth of $\sim5300\,\rm km\,s^{-1}$."] [Analysis: "The companions are then checked to have a signal-to-noise ratio (S/N) $\gtrsim3$ collapsed over $125\,\rm km\,s^{-1}$ and are validated spectrally."]
  - parameter: S/N >~ 3 collapsed over 125 km/s [Analysis: "The companions are then checked to have a signal-to-noise ratio (S/N) $\gtrsim3$ collapsed over $125\,\rm km\,s^{-1}$ and are validated spectrally."]
  - validation: Spectral validation of each companion [Analysis: "The companions are then checked to have a signal-to-noise ratio (S/N) $\gtrsim3$ collapsed over $125\,\rm km\,s^{-1}$ and are validated spectrally."]
- step 3: Extract and fit the [C II] spectra of each companion
  - method: Custom elliptical extraction apertures drawn from the moment 0 morphology, followed by single-Gaussian line fits [Analysis: "To maximize the S/N of the \[C II\] detections, we customize the extraction apertures based on their morphology in the moment 0 maps (color dotted ellipses)."] [Analysis: "We then perform single-Gaussian fitting to \[C II\] line."]
  - fitting: Single Gaussian per companion; velocity shift, width and intensity fitted [Analysis: "We then perform single-Gaussian fitting to \[C II\] line."]
- step 4: Estimate [C II] upper limits at the radio core (AGN host)
  - method: Assume a 5 kpc disk and take the 3 sigma intensity upper limit over [-125, 125] km/s (shifted by the [O III] offset for 4C+19.71) [Analysis: "we estimate the \[C II\] upper limits at the radio core by assuming a disk size of 5 kpc (cite: Venemans_2020)"] [Analysis: "we take the $3\sigma$ \[C II\] intensity upper limit from a velocity range of \[$-125$, 125\]$\,\rm km\,s^{-1}$"]
  - parameter: Velocity window equals the median FWHM of all fitted [C II] lines [Analysis: "This range equals to the median full width at half maximum (FWHM) of all fitted \[C II\] lines"]
  - assumption: Host disk size of 5 kpc [Analysis: "we estimate the \[C II\] upper limits at the radio core by assuming a disk size of 5 kpc (cite: Venemans_2020)"]
  - validation: Doubling the velocity range would raise the L_[CII] upper limit by ~30% [Analysis: "If we double the velocity range, i.e., two times of FWHM, the estimated $L_{\rm [\textup{C\,\textsc{\lowercase{ii}}}]}$ upper limit at radio core would be $\sim30\%$ higher."]
- step 5: Re-extract the archival [C I] spectra at the [C II] companion positions
  - method: Apertures of the Band 3 beam size at the [C II] positions, single-Gaussian fit when detected, 3 sigma upper limit over [-125, 125] km/s otherwise, with an overlap correction for blended apertures [Analysis: "we re-extract the \[C I\] spectra at the same position as \[C II\] companions using apertures corresponding to the Band 3 synthesized beam size"] [Analysis: "We then perform single-Gaussian fitting to the \[C I\] line when detected."]
  - parameter: Overlap correction f = (1 - P_overlap) f_fit applied at J0121 [C II]-C and radio core [Analysis: "we correct \[C I\] at \[C II\]-C and radio core for overlap, $f_{\rm [\textup{C\,\textsc{\lowercase{i}}}]} = (1-P_{\rm overlap})f_{\rm [\textup{C\,\textsc{\lowercase{i}}}],fit}$, where $P_{\rm overlap}$ is the percentage of overlap"]
  - fitting: Single Gaussian when detected [Analysis: "We then perform single-Gaussian fitting to the \[C I\] line when detected."]
- step 7: Derive the molecular gas mass from [C I](1-0)
  - method: M_H2 from the [C I](1-0) luminosity following Kolwa et al., with a 1375.8/(Q10(1+z)) prefactor [Analysis: "we calculate $M_{\rm H_{2}}$ solely based on \[C I\](1-0) following (cite: kolwa2023)"] [Analysis: "\frac{1375.8}{Q_{10}(1+z)} \times"]
  - parameter: Q10 = 0.48 [Analysis: "where the excitation factor $Q_{10}$ is assumed as $Q_{10}=0.48$"]
  - parameter: A10 = 7.93e-8 s^-1 [Analysis: "$A_{10}$ is the Einstein A-coefficient with $A_{10}=7.93\times10^{-8}\,\rm s^{-1}$"]
  - assumption: [C I]-to-H2 abundance ratio X_[CI] = 3e-5 [Analysis: "the \[C I\]-to-$\rm H_{2}$ ratio is assumed as $X_{[\textup{C\,\textsc{\lowercase{i}}}]}=3\times10^{-5}$"]
  - assumption: [C I] is a good H2 tracer in the radiation fields of bright quasars, where the [C II]-H2 relation may not hold [Analysis: "The neutral carbon fine structure transitions are found to be a good tracer of cold molecular gas in these extreme fields"]
  - validation: Compared with the Zanella et al. 2018 M_H2-L_[CII] relation [Discussion and conclusion: "Three of our detections generally follow the relation while the majority have a tendency to fall below it especially for brighter \[C II\] emitters ($>10^{9}\,L_{\odot}$)."]
- step 8: Estimate dispersion-dominated dynamical masses of the companions
  - method: M_dyn^dis = K(n) K(q) sigma_v^2 r_e / G, with r_e from a 2D Gaussian fit to the [C II] moment 0 map [Analysis: "we can estimate the dynamical masses of these systems assuming that they are dispersion-dominated"] [Analysis: "We perform a 2D Gaussian fit to the \[C II\] moment 0 maps using `lmfit` task in CASA and take $r_{e}=\sqrt{\rm FWHM_{x}\times FWHM_{y}}/2$"]
  - software: CASA (lmfit task)
  - parameter: K(n) = 8.87 - 0.831n + 0.0241n^2 and K(q) = [0.87 + 0.38 exp(-3.71(1-q))]^2 [Analysis: "$K(n)=8.87-0.831n+0.0241n^{2}$ is a function of Sérsic index, $n$, and $K(q)=[0.87+0.38e^{-3.71(1-q)}]^{2}$ is a function of axis ratio, $q$"]
  - parameter: For J0205-[C II], r_e = 2 sqrt(theta_400GHz) [Analysis: "For J0205-\[C II\], we use $r_{e}=2\sqrt{\theta_{\rm 400\,GHz}}$."]
  - assumption: q = 1 and n = 1, which gives an upper limit on M_dyn^dis [Analysis: "we take $q=1$ and $n=1$ in this calculation which returns the upper limit of $M_{\rm dyn}^{\rm dis}$"]
  - assumption: Clouds are virialized and dispersion-dominated [Analysis: "If the \[C II\] emitting gas clouds are virialized, we can estimate the dynamical masses of these systems assuming that they are dispersion-dominated"]
  - fitting: 2D Gaussian fit to the moment 0 map (CASA lmfit) [Analysis: "We perform a 2D Gaussian fit to the \[C II\] moment 0 maps using `lmfit` task in CASA and take $r_{e}=\sqrt{\rm FWHM_{x}\times FWHM_{y}}/2$"]
- step 9: Derive L_IR and SFR_IR from the Band 8 continuum
  - method: Continuum flux extracted at the same position and aperture as [C II]; L_158um = L_IR/0.13 and SFR_IR = 2.64e-44 L_IR; 3 sigma upper limits for non-detections [Analysis: "We extract the continuum flux at the same position and from the same aperture as the \[C II\] emissions."] [Analysis: "using $L_{\rm 158\,\mu m}=L_{\rm IR}/0.13$ and then to SFR with ${\rm SFR}_{\rm IR}=2.64\times10^{-44}L_{\rm IR} [\frac{M_{\odot}\,{\rm yr}^{-1}}{\rm erg\,s^{-1}}]$ (cite: MandD_2014)"]
  - parameter: L_IR integrated over 8-1000 um [Analysis: "we convert the monochromatic luminosity into the total IR luminosity (integrated in $8-1000\,\rm \mu m$)"]
  - assumption: Contamination from hotter dust (T >~ 60 K) is negligible at the cold-dust peak [Analysis: "We note that we are observing at the peak frequency of cold dust emission where the contamination of hotter dust, $T\gtrsim60\,\rm K$, in HzRGs is known to be negligible"]
  - validation: SFR_IR consistent with SFR_SED of Falkendal et al. 2019 for TN J0121+1320, and for the two shallow fields; 4C+19.71 higher by ~2 [Analysis: "Our SFR$_{\rm IR}$ estimate in this work is consistent with (cite: Falkendal_2019) SED fitting measurements of TN J0121+1320"]
- step 10: Place companions in scaling relations and estimate zeroth-order stellar masses
  - method: Assume gas fraction ~1 so M_star = M_dyn/2, then compare M_H2-L_[CII], L_[CII]/L_IR-L_IR and SFR-M_star with literature samples [Analysis: "Adopting a gas mass fraction of $\sim1$ (cite: Geach_2011; Lehnert_2016), we estimate zeroth-order stellar mass estimates, $M_{\star}=M_{\rm dyn}/2$"]
  - validation: Positions on the SFR-M_star plane called uncertain because most measurements are upper limits [Discussion and conclusion: "We caution that, given most of our measurements are upper limits, the positions of our companions on the SFR-$M_{\star}$ plane are uncertain."]
- result: [C II] luminosity upper limits at the radio core = <~1e9 ± not stated Lsun [Discussion and conclusion: "$L_{[\textup{C\,\textsc{\lowercase{ii}}}]}$ upper limits at the radio core are estimated to be $\lesssim10^{9}\,L_{\odot}$"]
- result: Median L_[CII]/L_IR ratio = 9.4e-4 ± not stated dimensionless [Discussion and conclusion: "Our sample has a median $L_{\rm [\textup{C\,\textsc{\lowercase{ii}}}]}/L_{\rm IR}$ ratio of $9.4\times10^{-4}$"]
- result: Median [C II] line width sigma_v = 105 ± not stated km/s [Discussion and conclusion: "The \[C II\] line widths are generally narrower than the pure ionized gas tracer with a median $\sigma_{v}=105\,\rm km\,s^{-1}$"]
- result: M_H2 from [C I] of J0121-[C II]-B = 2.7e10 ± +/-0.8e10 Msun [Table 1: "11.6$\pm$3.4 | 2.7$\pm0.8$ | 696$\pm$66 | 26(9.0)$^{\S}$"]
- result: SFR_IR of J0121-[C II]-B = 696 ± +/-66 Msun/yr [Table 1: "11.6$\pm$3.4 | 2.7$\pm0.8$ | 696$\pm$66 | 26(9.0)$^{\S}$"]
- result: Dispersion-dominated M_dyn upper limit of J0121-[C II]-B (disk-rotation value in parentheses) = 26e10 (9.0e10) ± not stated Msun [Table 1: "11.6$\pm$3.4 | 2.7$\pm0.8$ | 696$\pm$66 | 26(9.0)$^{\S}$"]
- result: M_H2 from [C I] of 4C19-[C II] = 1.9e10 ± +/-0.7e10 Msun [Table 1: "8$\pm$3 | 1.9$\pm$0.7 | 449$\pm$18 | 29(7.0)$^{\S}$"]
- result: SFR_IR of 4C19-[C II] = 449 ± +/-18 Msun/yr [Table 1: "8$\pm$3 | 1.9$\pm$0.7 | 449$\pm$18 | 29(7.0)$^{\S}$"]
- result: Dispersion-dominated M_dyn upper limit of 4C19-[C II] (disk-rotation value in parentheses) = 29e10 (7.0e10) ± not stated Msun [Table 1: "8$\pm$3 | 1.9$\pm$0.7 | 449$\pm$18 | 29(7.0)$^{\S}$"]
- limitation (authors): Deeper and higher-resolution [C I] data are needed to determine M_H2 accurately [Discussion and conclusion: "Deeper and higher spatial resolution \[C I\] are required to more accurately determine the $M_{\rm H_{2}, [\textup{C\,\textsc{\lowercase{i}}}]}$"]
- limitation (authors): [C I] extraction apertures overlap in fields with multiple [C II] companions [Analysis: "We caution that for fields of TN J0121+1320 and 4C+03.24 where multiple \[C II\] companions are detected, the extraction apertures of \[C I\] may be overlapped."]
- limitation (authors): Positions on the SFR-M_star plane are uncertain because most measurements are upper limits [Discussion and conclusion: "We caution that, given most of our measurements are upper limits, the positions of our companions on the SFR-$M_{\star}$ plane are uncertain."]
- not stated (card): Calibration details for both ALMA datasets (pipeline vs manual, CASA version for calibration, flux and bandpass calibrators, self-calibration, flux-scale uncertainty); these are deferred to the companion paper; tclean settings beyond robust: deconvolver, cell size, image size, niter/threshold, masks, uv taper, primary-beam correction; Whether and how continuum was subtracted from the [C II] cubes…

### 2013A&A...559A..29C: Strongly star-forming rotating disks in a complex merging system at z = 4.7 as revealed by ALMA (2013; high_z_galaxies, agn_and_quasars; archival_reuse)
- question: Do the QSO host and the SMG in BR1202-0725 at z=4.7 show regularly rotating disks or merger-disturbed kinematics in [CII], and what are their dynamical masses and BH-host relation?
- step 1: Calibrate, self-calibrate and image continuum and [CII] cube
  - method: CASA calibration, self-cal, CLEAN, uv continuum subtraction [Observations and data reduction: "The data were calibrated by using the CASA software."]
  - software: CASA
  - parameter: ROBUST=1.5; 0.15" pixel; 28 km/s channels [Observations and data reduction: "The spatial scale is 0.15$^{\prime\prime}$ per pixel"]
  - validation: Compared with released data products; consistent fluxes [Observations and data reduction: "Continuum and line fluxes are consistent within the errors"]
- step 2: Fit integrated spectra
  - method: Two-Gaussian fits to [CII]; redshifts from Gaussian fit [3 Results: "The redshifts of the two sources are determined from a Gaussian fit to the \[CII\] lines"]
  - assumption: SMG faint component fixed at 250 km/s [3 Results: "with the fainter component fixed at 250 km/s"]
- step 3: Derive SFR and gas mass
  - method: SED fit for LFIR, Kennicutt relation, [CII] calibration, CO-based gas mass [2 Star formation rate and gas mass: "SFR = 1.73\times 10^{-10} (L_{FIR}/L_\odot)\, M_\odot/yr"]
  - assumption: Td=65 K (SMG), 50 K (QSO); k~nu^1.5; Salpeter IMF; alpha_CO=0.6 with factor 2 systematic [2 Star formation rate and gas mass: "T$_d$ = 65 K for the SMG and T$_d$ = 50 K for the QSO"]
  - fitting: SFR the only free parameter of Yun & Carilli SED model [2 Star formation rate and gas mass: "the latter depends on the SFR, which is the only free parameter of our SED fit"]
  - validation: [CII] SFRs used as confirmation [2 Star formation rate and gas mass: "considered the values based on \[CII\] just as a confirmation of the very high SFR"]
- step 5: Fit rotating disk to velocity maps
  - method: Thin exponential disk model, chi2 minimization with MPFIT/AMOEBA then MCMC, with and without gas-mass prior [4.1 The submillimeter galaxy BR1202 Nor…: "The best-fit parameter values for the kinematical model were found using the MPFIT (cite: markwardt:2009) and AMOEBA algorithms in the IDL environment."]
  - software: MPFIT, AMOEBA, EXOFAST IDL
  - parameter: 10^5 MCMC trials; pixels with S/N>=3; Mdyn within 5 kpc [4.1 The submillimeter galaxy BR1202 Nor…: "obtained from the MCMC with $10^5$ trials with (red) and without (green) the dynamical mass prior"]
  - assumption: Circular rotation, potential from disk mass, Sigma=Sigma0 exp(-r/r0), center and r0 from [CII] surface brightness [4.1 The submillimeter galaxy BR1202 Nor…: "We assumed that the gas is circularly rotating in a thin disk"]
  - fitting: Prior: lognormal step function peaked at molecular gas mass, 0.3 dex dispersion [4.1 The submillimeter galaxy BR1202 Nor…: "the dispersion is $0.3$ dex, corresponding to a factor 2"]
  - validation: Spectroastrometric mass consistent; inclination check assuming symmetric flux gives i=6±3 (SMG), 2±2 (QSO) [4.1 The submillimeter galaxy BR1202 Nor…: "the resulting disk inclination is in the range $i=6^\circ\pm3^\circ$ (90% confidence)"]
- result: Continuum flux 900 um N / S = 15.8 / 14.8 ± 2.4 / 2.2 mJy [Table 1: "Integrated continuum flux at 900 $\mu$m \[mJy\] | 15.8$\pm$2.4 | 14.8$\pm$2.2"]
- result: Projected N-S distance = 23.5 ± 0.3 kpc [3 Results: "The projected distance between the two continuum sources is 23.5$\pm$0.3 kpc."]
- result: log Mdyn SMG = 10.8 ± 0.6 log Msun [4.1 The submillimeter galaxy BR1202 Nor…: "$Log_{10}({\rm M}_{\rm SMG}/ {\rm M}_\odot) =10.8 \pm 0.6$"]
- result: SMG inclination = 25 ± 15 deg [4.1 The submillimeter galaxy BR1202 Nor…: "$i = 25^\circ\pm 15^\circ$"]
- result: log Mdyn QSO = 10.6 ± +0.8/-0.4 log Msun [4.2 The quasar BR1202 South: "$Log_{10}({\rm M}_{\rm QSO}/ {\rm M}_\odot) =10.6^{+0.8}_{-0.4}$"]
- result: QSO inclination = 15 ± 10 deg [4.2 The quasar BR1202 South: "$i = 15^\circ\pm 10^\circ$"]
- result: Molecular mass SMG / QSO = 4.6 / 3.2 (1e10) ± 1.7 / 1.2 Msun [2 Star formation rate and gas mass: "$M_{CO} = (4.6\pm 1.7)\times 10^{10}$$\mathrm{M}_{\odot}$"]
- result: SFR from LFIR SMG / QSO = 2600 / 3200 ± not stated Msun/yr [2 Star formation rate and gas mass: "one obtains $\sim 2600$ and $\sim 3200$ M$_{\odot}$ yr$^{-1}$ for the SMG and QSO"]
- limitation (authors): Inclination poorly constrained, so mass is poorly constrained [4.1 The submillimeter galaxy BR1202 Nor…: "the inclination cannot be well constrained from the data"]
- not stated (card): Exact CASA version and calibration script; Channel ranges identified as line-free; CLEAN threshold, masks, iterations; Parameter priors/bounds and MCMC chain settings; Spectroastrometry velocity cuts defining blue/red channels; Disk model code not released; Exact SED fitting details

### 2021ApJ...908..235I: Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XII. Extended [C II] Structure (Merger or Outflow) in a z = 6.72 Red Quasar (2021; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is the highest-redshift red quasar (z = 6.72) in a merger-driven to outflow-driven transition: what are its FIR continuum and extended [C II] properties, and is the extended [C II] structure companion/merging galaxies or a cold AGN-driven …
- step 1: Image the [C II] cube and FIR continuum
  - method: tclean with natural weighting; first clean cube including continuum to 3 sigma to find the line; integrate line-free channels into continuum map; subtract continuum in the uv plane with a first-order polynomial; average channels to 100 km/s [ALMA Observations: "All images were reconstructed with the `tclean` task using natural weighting to maximize the sensitivity."] [ALMA Observations: "which was subtracted in the $uv$ plane by using the first-order polynomial before making the final line cube."]
  - software: CASA 5.6, tclean
  - parameter: velocity resolution 100 km/s, channel rms 0.13 mJy/beam [ALMA Observations: "We averaged several channels to obtain a velocity resolution of 100 km s$^{-1}$, which resulted in a 1$\sigma$ channel sensitivity of 0.13 mJy beam$^{-1}$"]
  - parameter: continuum map 1 sigma = 17.6 uJy/beam [ALMA Observations: "(1$\sigma$ = 17.6 $\mu$Jy beam$^{-1}$)"]
- step 4: Fit the area-integrated [C II] spectrum
  - method: single Gaussian then double Gaussian fit (core + wing) to the spectrum integrated within a 1.5'' radius of the nucleus where [C II] is detected above 3 sigma [[C II] line emission: "area-integrated spectrum measured over the region within $1\ensuremath{''}.5$ radius of the nucleus"] [[C II] line emission: "We first fit the spectrum with a single Gaussian function"]
  - parameter: chi2/d.o.f. computed over +-1200 km/s [[C II] line emission: "(estimated over $\pm$1200 km s$^{-1}$ range)"]
  - assumption: core component attributed to the host galaxy and used for the systemic redshift [[C II] line emission: "We naively attribute the core component in the double Gaussian fit to the host galaxy itself"]
  - fitting: Gaussian fits compared by chi2/d.o.f.; single 37.6/22, double 21.1/19; sampler/priors not stated [[C II] line emission: "we found $\chi^2$/d.o.f. = 37.6/22"] [[C II] line emission: "This works fairly well with a returned $\chi^2$/d.o.f. = 21.1/19."]
  - validation: double Gaussian preferred at >99.9% confidence from the chi2 difference [[C II] line emission: "With this difference in $\chi^2$, this model is preferred at $>99.9\%$ confidence."]
- step 5: Derive [C II] luminosity, SFR and equivalent width
  - method: [C II] SFR from the core L_[CII] with a literature calibration; rest-frame EW from the [C II] core flux and the 1.2 mm continuum flux density [[C II] line emission: "giving $108 \pm 7~M_\odot$ yr$^{-1}$ with the (cite: 2011MNRAS.416.2712D) calibration, which has $\sim 0.3$ dex dispersion."]
  - assumption: SFR_[CII] is an upper limit because part of [C II] may come from the quasar narrow line region [[C II] line emission: "Again, this would be an upper limit"]
- step 6: Characterize extended [C II] at positions A-C
  - method: spectra at three off-centre positions (A, B, C) give line centre, FWHM, flux and L_[CII]; extended structure judged real from several contiguous velocity channels [[C II] line emission: "The extended structure that is directly connected to the continuum-bright core region is real, as we see positive signals from several contiguous velocity channels measured there"]
  - validation: extended emission seen in several contiguous channels over -500 to +500 km/s [[C II] line emission: "The extended structure that is directly connected to the continuum-bright core region is real"]
- step 8: Estimate outflow mass, rate, kinetic power and momentum load for blobs A-C
  - method: Mdot_out = M_out v_out / R_out with v_out = |dv| + FWHM/2; M_out from L_[CII] under the high-density limit (lower limit); kinetic power and momentum load from the standard formulae [Cold neutral outflows?: "We define the outflow rate as $\dot{M}_{\rm out} = M_{\rm out} v_{\rm out}/R_{\rm out}$"] [Cold neutral outflows?: "For $v_{\rm out}$, we adopt $|\Delta v| + {\rm FWHM}/2$"]
  - parameter: R_out = 3.5, 6.4, 5.1 kpc for blobs A-C [Cold neutral outflows?: "as 3.5, 6.4, and 5.1 kpc for the blobs A–C, respectively."]
  - parameter: X_C+ = 1.4e-4, T_ex = 200 K, n_crit ~3e3 cm^-3 [Cold neutral outflows?: "we adopt $X_{\rm C^+} = 1.4 \times 10^{-4}$ and $T_{\rm ex} = 200$ K"] [Cold neutral outflows?: "the line critical density ($\sim 3 \times 10^3$ cm$^{-3}$)"]
  - assumption: high density limit n >> n_crit, giving a lower limit on M_out [Cold neutral outflows?: "we here assume the high density limit ($n \gg n_{\rm crit}$) to provide a"]
  - assumption: 70% of [C II] arises from PDRs (factor 0.7) [Cold neutral outflows?: "The factor 0.7 in the first parenthesis indicates a typical fraction of"]
  - assumption: projection correction averages to unity over all angles; entire extended structure assumed to be outflow [Cold neutral outflows?: "the average of this factor over all angles is unity."] [Cold neutral outflows?: "by assuming that the extended structure is formed fully due to cold outflows."]
  - validation: varying T_ex in [100, 1000] K changes M_out by only ~20% [Cold neutral outflows?: "varying $T_{\rm ex} \in [100, 1000]$ K changes the inferred $M_{\rm out}$ by only $\sim 20\%$."]
- step 9: Constrain star formation in potential companions
  - method: 3 sigma upper limit on SFR_IR at the extended [C II] regions from undetected FIR continuum, with T_d = 35 K; compare with HSC y-band depth [Companion/merging galaxies?: "An inferred $3\sigma$ upper limit on SFR$_{\rm IR}$ by assuming a modest $T_d$ of 35 K (cite: 2012ApJS..203....9U) is only $\sim 10~M_\odot$ yr$^{-1}$."]
  - assumption: T_d = 35 K [Companion/merging galaxies?: "by assuming a modest $T_d$ of 35 K"]
- result: Systemic redshift z_[CII] (core component) = 6.7224 ± 0.0003 dimensionless [[C II] line emission: "providing its systemic redshift as $z_{\rm [CII]} = 6.7224 \pm 0.0003$"]
- result: chi2/d.o.f. single Gaussian fit = 37.6/22 ± not stated dimensionless [[C II] line emission: "we found $\chi^2$/d.o.f. = 37.6/22"]
- result: chi2/d.o.f. double Gaussian fit = 21.1/19 ± not stated dimensionless [[C II] line emission: "This works fairly well with a returned $\chi^2$/d.o.f. = 21.1/19."]
- result: Total [C II] luminosity (core + wing) = 1.9e9 ± 0.1e9 Lsun [Summary: "we found the line luminosity of $L_{\rm [CII]} = (1.9 \pm 0.1) \times 10^9~L_\odot$."]
- result: Rest-frame [C II] equivalent width = 0.67 ± 0.05 um [[C II] line emission: "$\rm{EW}_{\rm [CII]} = 0.67 \pm 0.05$ $\ensuremath{\mu}m$"]
- result: SFR from [C II] core luminosity = 108 ± 7 Msun/yr [[C II] line emission: "giving $108 \pm 7~M_\odot$ yr$^{-1}$ with the (cite: 2011MNRAS.416.2712D) calibration"]
- result: Extent of [C II] emission (radius) = ~1'' (5.4 kpc) ± not stated arcsec / kpc [[C II] line emission: "extending to $r \sim 1\ensuremath{''}$ (5.4 kpc)"]
- result: FWHM of [C II] at extended regions = ~630-780 ± not stated km/s [abstract: "(FWHM $\sim 630-780$ km s$^{-1}$)"]
- result: Total atomic outflow mass (blobs A-C) = 9.0e8 ± 0.9e8 Msun [Cold neutral outflows?: "the total atomic outflow mass and outflow rate are $M_{\rm out,A-C} = 9.0 \pm 0.9) \times 10^8~M_\odot$ and $\dot{M}_{\rm out,A-C} = 97 \pm 15$ $M_\odot$ yr$^{-1}$, respectively."]
- result: Total atomic outflow rate (blobs A-C, lower limit) = 97 ± 15 Msun/yr [Cold neutral outflows?: "the total atomic outflow mass and outflow rate are $M_{\rm out,A-C} = 9.0 \pm 0.9) \times 10^8~M_\odot$ and $\dot{M}_{\rm out,A-C} = 97 \pm 15$ $M_\odot$ yr$^{-1}$, respectively."]
- result: Black hole accretion rate = ~12.5 ± not stated Msun/yr [Cold neutral outflows?: "($\dot{M}_{\rm BH} \sim 12.5~M_\odot$ yr$^{-1}$)"]
- result: Possible total outflow rate including molecular phase = >~300 ± not stated Msun/yr [Cold neutral outflows?: "$\dot{M}_{\rm tot} \gtrsim 300~M_\odot$ yr$^{-1}$"]
- result: 3 sigma upper limit SFR_IR at extended [C II] regions (T_d = 35 K) = ~10 ± not stated Msun/yr [Companion/merging galaxies?: "is only $\sim 10~M_\odot$ yr$^{-1}$."]
- limitation (authors): The nature of the extended structure cannot be identified with current data [abstract: "Although it is not practical to identify the nature of this extended structure"]
- limitation (authors): Outflow mass is a lower limit and rates measured at only three positions [Cold neutral outflows?: "As our computation provided a lower limit on $M_{\rm out}$, and we measured rates only at the three selected positions"]
- limitation (authors): Extended [C II] in negative velocity channels needs deeper observations to confirm [[C II] line emission: "but deeper observations are required to confirm its existence"]
- not stated (card): tclean parameters: cell size, image size, niter, deconvolver, robust (only 'natural' given), masking and clean threshold for the final images; Whether the archive/pipeline calibration was used as delivered or manually reprocessed, and any extra flagging; Spectral window setup, channel widths before averaging, and the exact line-free channel ranges used for the continuum; Whether the continuum map…

### 2024A&A...690A.277M: Gas flows in the central region of the Seyfert galaxy NGC 4593 with MUSE (2024; nearby_galaxies, agn_and_quasars; multi_facility_alma_minor)
- question: Stellar kinematics, ionised gas flows, AGN feeding and feedback around the nucleus of NGC 4593.
- step 2: Prepare and bin the MUSE spectra
  - method: Process the reduced MUSE cube with GIST; mask spaxels and make separate stellar and emission-line Voronoi binnings. [MUSE data processing: "We used the galaxy IFU spectroscopic tool (`GIST`), version 3.1.0 to process the data cube."] [MUSE data processing: "Spatial masking was performed to remove defunct spaxels and those with a signal-to-noise ratio (S/N) below the given threshold before we binned the data."]
  - software: GIST, Voronoi binning code
  - parameter: 4750–7000 Å; ignore 5780–6050 Å affected by laser guide stars. [MUSE data processing: "The input data cube was read using `GIST` and the wavelength range is shortened to $4750\,\r{A}- 7000\,\r{A}$."] [MUSE data processing: "Above $7000\,\r{A}$, there is contamination due to strong sky lines, and the range $5780\,\r{A} - 6050\,\r{A}$, which is affected by the laser guide stars was,ignored."]
  - parameter: Stellar S/N = 50: 426 bins; emission-line S/N = 100: 762 bins. [MUSE data processing: "We required an ${\rm S/N}=50$ per stellar bin and a total of 426 Voronoi bins were generated."] [MUSE data processing: "For the emission line binning, we required an ${\rm S/N}=100$ and in this case, a total of 762 Voronoi bins were generated."]
  - parameter: Stellar S/N window: 5580–5680 Å; emission binning based on continuum-subtracted [O III] λ5007. [MUSE data processing: "For the stellar component we computed the median S/N from the rest-frame wavelength range 5580 – 5680 Å, which does not include any strong emission lines."] [MUSE data processing: "The emission line or ionised gas binning was made based on a \[O III\] $\lambda$5007 continuum-subtracted image."]
  - parameter: [O III] image: 10 Å line window minus an equal-width window 50 Å redwards. [MUSE data processing: "We built the image by integrating the data cube flux in a $10\,\AA$ window centred on the \[O III\] $\lambda$5007 rest-frame wavelength of NGC 4593, and by subtracting the integrated flux in a window of equal width but $50\,\AA$ redwards."]
  - parameter: Spaxel S/N > 0.1 for emission and > 1.0 for stars; minimum 50 contiguous spaxels. [MUSE data processing: "We considered spaxels with an S/N greater than 0.1 and 1.0 for the emission line and stellar binning, respectively."] [MUSE data processing: "To avoid these spaxels from being accreted into Voronoi bins we modified GIST to consider clusters with a minimum of 50 contiguous spaxels for the binning."]
- step 4: Separate disc and outflow kinematics
  - method: Fit narrow and broad Gaussian components to [O III] λ5007 at bin level with PyGandALF. [MUSE data processing: "the Gas and Absorption Line Fitting`PyGandALF` module (cite: sarzi2006sauron; falcon2006sauron) from the `GIST` pipeline, which was run on the bin level to perform the emission line analysis."] [Emission lines: "Therefore, we performed two Gaussian fits, narrow and broad, which correspond to the narrow and outflow components, respectively."]
  - software: PyGandALF, GIST
  - parameter: Initial velocity/dispersion: narrow 0/100 km s^-1; broad outflow and BLR −500/500 km s^-1. [MUSE data processing: "The initial guess for the velocity and velocity dispersion is 0 and $\mathrm{100\,km~s^{-1}}$ for the narrow-component, while for the broad outflow and BLR components, the initial guess is -500 and $\mathrm{500\,km~s^{-1}}$ respectively."]
  - parameter: Use pPXF stellar fit multiplied by a second-order Legendre polynomial for the stellar and AGN continuum. [MUSE data processing: "In any case, we used the stellar fit from `pPXF` as input to `PyGandALF`, multiplied by a second-order Legendre polynomial."] [MUSE data processing: "This component accounts for the underlying stellar and AGN continuum."]
  - assumption: [O III] broadening traces kinematically disrupted gas rather than the BLR. [MUSE data processing: "Hence, any broadening of the \[O III\] line profiles will be associated with kinematically disrupted gas, and not with the BLR."]
  - fitting: Fixed theoretical doublet flux ratios; line kinematics tied to [O III]. [MUSE data processing: "We reduced the number of degrees of freedom in the fits by fixing the flux ratios of several doublets to their theoretically estimated values ((cite: storey2000theoretical)), which are listed in Table [1](#table 1)."] [MUSE data processing: "We also tied the kinematics of all the lines considered here to those of \[O III\], since otherwise it would be impossible to successfully fit the H$\alpha$+\[N II\] blend."]
  - validation: Blueshifted broad emission coincides with high velocity dispersion, confirming the previously tentative outflow. [Emission lines: "This coincides with a region of high velocity dispersion (up to 250 km s$^{-1}$), confirming the presence of outflowing gas, as first tentatively reported by (cite: ruschel2021agnifs)."]
- step 5: Map ionisation mechanisms
  - method: Resolved BPT diagrams from narrow [N II]/Hα and [O III]/Hβ flux ratios; map η. [Resolved BPT diagrams: Ionisation mecha…: "The maps used the \[N II\]$\,\lambda$6583/H$\alpha$ and \[O III\]$\,\lambda$5007/H$\beta$ narrow line flux ratios."] [Resolved BPT diagrams: Ionisation mecha…: "We used the parameter $\eta$ defined by (cite: erroz2019muse) as an indicator of the strength of the ionisation mechanism, given by the distance of a given point to the curves."]
  - software: PyGandALF, GIST
  - parameter: Single narrow Gaussian for [O III] and [N II]; narrow and broad Gaussians for Hα and Hβ. [Resolved BPT diagrams: Ionisation mecha…: "we fitted the \[O III\] $\lambda$5007 and \[N II\] $\lambda$6583 lines with a narrow Gaussian component, and H$\alpha$ and H$\beta$ with two (narrow and broad) Gaussians."]
  - parameter: Star formation: η < −0.5; AGN: η > 0.5; intermediate region composite. [Resolved BPT diagrams: Ionisation mecha…: "The region below the dashed line is considered to be ionised by star formation ($\eta < -0.5$), and the region above the solid line is ionised by the AGN ($\eta > 0.5$)."] [Resolved BPT diagrams: Ionisation mecha…: "The region between the two lines is considered to be composite and is ionised by a mix of the two mechanisms."]
  - assumption: Broad Balmer component is BLR emission; narrow Balmer component combines disc and outflow. [Resolved BPT diagrams: Ionisation mecha…: "The broad-component fitted to H$\alpha$ and H$\beta$ corresponds to emission from the BLR, and the narrow Gaussian includes the disc and outflow components."]
  - fitting: Do not separate disc and outflow in the Balmer narrow component because BLR emission prevents a good three-component separation. [Resolved BPT diagrams: Ionisation mecha…: "We did not consider the latter as two separate kinematic components as we did in previous sections because the BLR component makes it impossible to achieve a good separation into three components for the H$\alpha$ and H$\beta$ lines."]
- step 6: Estimate ionised outflow mass
  - method: Fit outflow Hβ intensity with [O III] kinematics fixed; use integrated broad [S II] emission to estimate density; apply the Rose et al. Hβ mass estimator. [Physical properties of the outflowing g…: "To measure the H$\beta$ line flux and hence obtain its luminosity, we first tied its kinematics to those of \[O III\]$\,\lambda$5007 to reduce the uncertainties."] [Physical properties of the outflowing g…: "Using this spectrum and the flux of the broad-components that we fitted, we obtained an electron density of $n_{\rm e}= 400\,{\rm cm}^3$."]
  - parameter: Integrated [S II] spectrum in a nuclear aperture of diameter 2″. [Physical properties of the outflowing g…: "We thus constructed an integrated \[S II\] spectrum within a diameter of $2\ensuremath{''}$, centred on the galaxy nucleus (see Fig. [7](#fig:7)) as shown in (cite: sanders2015mosdef)."]
  - assumption: Case B coefficient 3.03 × 10^-14 cm^3 s^-1; Te = 10^4 K. [Physical properties of the outflowing g…: "is the effective Case B coefficient (we adopted $\mathrm {3.03 \times 10 ^{-14}\,cm^{3}\,s^{-1}}$), which corresponds to an electron temperature $T_{\rm e} = 10^4\,{\rm K}$ (cite: osterbrock2006astrophysics)"]
  - fitting: Hβ intensity is the only free parameter after tying its kinematics to [O III]. [Physical properties of the outflowing g…: "We then fitted the emission line profile leaving the intensity as the only free parameter"] [Physical properties of the outflowing g…: "To measure the H$\beta$ line flux and hence obtain its luminosity, we first tied its kinematics to those of \[O III\]$\,\lambda$5007 to reduce the uncertainties."]
- result: Narrow [O III] velocity amplitude = ∼90 ± not stated km s^-1 [Emission lines: "although with a smaller velocity amplitude of $\sim90$ km s$^{-1}$."]
- result: Broad [O III] blueshifted velocity = up to -200 ± not stated km s^-1 [Emission lines: "The kinematic maps show blue-shifted velocities of up to $-200$ km s$^{-1}$ on the east side of the galaxy, within a radius of $\sim$2$''$ (340 pc)."]
- result: Broad [O III] velocity dispersion = up to 250 ± not stated km s^-1 [Emission lines: "This coincides with a region of high velocity dispersion (up to 250 km s$^{-1}$), confirming the presence of outflowing gas, as first tentatively reported by (cite: ruschel2021agnifs)."]
- result: Outflow radius = 2″ (340) ± not stated pc [Physical properties of the outflowing g…: "The outflow radius, $R_{\rm out}$, was estimated to be 2$''$ (340 pc) from the nucleus, as measured from the right panel of Fig. [4](#Fig.4)."]
- result: Central BPT η = >1 ± not stated dimensionless [Resolved BPT diagrams: Ionisation mecha…: "It reveals higher ionisation parameter values in the central $\sim$4$''$(680 pc) in diameter of the galaxy ($\eta > 1$), as well as values of 0.75\<$\eta$\<1 towards the west."]
- result: Diameter of central region with η > 1 = ∼4″ (680) ± not stated pc [Resolved BPT diagrams: Ionisation mecha…: "It reveals higher ionisation parameter values in the central $\sim$4$''$(680 pc) in diameter of the galaxy ($\eta > 1$), as well as values of 0.75\<$\eta$\<1 towards the west."]
- result: Outflow Hβ luminosity lower limit = 4.7×10^39 ± not stated erg s^-1 [Physical properties of the outflowing g…: "As a result, the H$\beta$ luminosity that we measure, $4.7\times10^{39}$ erg s$^{-1}$, and all the derived quantities are lower limits."]
- result: Electron density = 400 ± not stated cm^-3 [Discussion: "In the case of NGC 4593, the values of the outflow radius and the electron density are $\sim340$ pc and 400 cm$^{-3}$, respectively"]
- result: Ionised outflow mass = ≥1.589×10^35 ± not stated kg [Physical properties of the outflowing g…: "Using this electron density, we measure a total mass of the outflow of $M_{\rm out}\geq 1.589\times 10^{35}$ kg which corresponds to $0.799\times 10^5 \,M_{\ensuremath{\odot}}$."]
- limitation (authors): Central approximately 0.7″ stellar kinematics cannot be fitted accurately because AGN emission dilutes stellar absorption. [Stellar kinematics: "We were unable to accurately fit the stellar kinematics in the central $\sim 0.7\ensuremath{''}$ (120 pc) of the galaxy"]
- limitation (authors): The minimum cluster size of 50 spaxels is arbitrary. [MUSE data processing: "The number of 50 spaxels is arbitrary."]
- not stated (card): ALMA calibrated visibility or delivered image identifiers and whether archive products were used unchanged.; ALMA calibration procedure, software versions and any self-calibration.; ALMA imaging weights, deconvolution settings, beam axes, pixel scale and primary-beam treatment.; CO(1-0) continuum subtraction, velocity integration limits, noise and contour levels.; Numerical HST–ALMA astrometric s…

### 2019A&A...630A..59B: Widespread QSO-driven outflows in the early Universe (2019; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Do high-z QSOs show faint broad [CII] wings tracing cold outflows, detectable by stacking archival ALMA [CII] data?
- step 2: Extract spectra and fit [CII] core per source
  - method: Spectra from region of four beams; single Gaussian fit for redshift and core parameters [Sample and data reduction: "we extracted the continuum-subtracted [CII] spectra from a region with an area of four beams"]
  - fitting: one Gaussian component [Sample and data reduction: "The line parameters describing the [CII] core emission were derived by fitting each spectrum with one Gaussian component model."]
- step 3: Stack spectra and cubes
  - method: Variance-weighted stack with weights 1/sigma^2 per channel after aligning at [CII] rest frequency and centering on continuum peak; both 1D spectra and 3D cubes [Methods: "We applied a standard variance-weighted stacking, i.e. we used a weighting factor $w_{\rm j,k}=1/\sigma_{\rm j,k}^2$"]
  - parameter: n=48; channels with atmospheric transmission <0.5 excluded [Methods: "We did not include in the stack spectral regions corresponding to an atmospheric transmission $<0.5$ for a 1 mm precipitable water vapour."]
  - validation: Stacks of 100 empty positions gave spurious SNR ~0.4; 1000 jackknife stacks excluding 5 sources gave ~11% mean luminosity variation [Methods: "This resulted into an average spurious signal-to-noise ratio of $\sim0.4$ for the stack of the total sample."]
- step 4: Fit broad [CII] wings
  - method: chi2 minimisation with core Gaussian plus broad Gaussian, all parameters free, weights W'_k [4.1 Stacked spectrum: "The $\chi^2$ minimisation of the fit was performed by using for each channel the weight $W^\prime_{\rm k}$ (see Eq. 1) and all the model parameters were free to vary in the fit with no constrains."]
  - software: scipy curve_fit
  - fitting: chi2 minimisation, scipy optimize curve_fit; 1G chi2_nu=8.6 vs 2G 3.7 [Appendix A: spectral fitting: "by using the python *scipy optimize* package *curve_fit*"]
  - validation: Subsamples by FWHM, L_AGN, SFR; stack in luminosity density; fixed 8 kpc aperture; Decarli18 sample alone gives SNR~2; excluding 3 companion QSOs [4.3 Outflow detectability: "As further verification, we also excluded these particular three QSOs from the stack and found no significant variation in the luminosity of the broad [CII] wings."]
- step 6: Outflow mass, rate, power, momentum load
  - method: Hailey-Dunsheath10 mass relation; Mdot=v M/R; Edot=0.5 Mdot v^2; momentum load vs L_AGN/c [Discussion: "$$\dot{M}_{\rm out} = \frac{v_{\rm out} \times M_{\rm out}}{R_{\rm out}}$$"]
  - parameter: v_out=|Delta v|+FWHM_broad/2; R_out~3.5 kpc [Discussion: "$v_{\rm out}= |\Delta v_{\rm broad}| + \rm FWHM_{[CII]}^{broad}/2$"]
  - assumption: optically thin [CII], n>>n_crit, X_C+~1e-4, T=200 K, 0.7 PDR fraction [Discussion: "we consider a conservative $X_{\rm C^+}\sim10^{-4}$ and a gas temperature of 200 K, both typical of PDRs"]
  - validation: Assuming T from 100 to 1000 K changes mass by only 20% [Discussion: "Assuming a temperature from 100 K to 1000 K would imply a variation of only 20% in the resulting gas mass."]
- result: FWHM of broad [CII] component, whole stack = 1730 ± 210 km/s [Table 1: "1730 $\pm$ 210"]
- result: FWHM of [CII] core, whole stack = 390 ± 30 km/s [4.1 Stacked spectrum: "FWHM$^{\rm core}_{\rm[CII]}$ = 390 $\pm30$ km s$^{-1}$"]
- result: Broad [CII] significance (fit) = 5.6 ± not stated sigma [4.1 Stacked spectrum: "The significance estimated through the fitting analysis is $5.6\sigma$."]
- result: L_[CII] broad, whole stack = 4.1 ± 0.7 1e8 Lsun [Table 1: "4.1$\pm$0.7"]
- result: Broad-to-narrow flux ratio f_[CII] = 0.22 ± 0.04 dimensionless [Table 1: "0.22 $\pm$ 0.04"]
- result: Broad component velocity shift = -90 ± 40 km/s [Table 1: "-90 $\pm$ 40"]
- result: Outflowing neutral gas mass = 3.7e8 ± 0.7e8 Msun [Discussion: "$M_{\rm out} = (3.7\pm0.7) \times10^8$ M$_\odot$"]
- result: Mass outflow rate, whole stack = 100 ± 20 Msun/yr [Discussion: "$\dot{M}_{\rm out} = 100\pm20$ M$_\odot$ yr$^{-1}$"]
- result: Sensitivity improvement vs Cicone15 J1148+5251 = ~14 ± not stated dimensionless [4.1 Stacked spectrum: "a factor of $\sim14$ lower than that of the J1148$+$5251 observations of (cite: Cicone15)"]
- limitation (authors): Interferometric data may miss extended diffuse emission; stacking dilutes orientations [Conclusions: "we cannot exclude that additional, more extended emission is present but missed by the interferometric data used for the stacking."]
- not stated (card): List of the 48 QSOs with per-source flux scaling/calibration corrections (table not in text); Exact clean threshold and iteration count per source; Which sources were calibrated manually vs pipeline; Exact aperture definition/centering and handling of channels with partial coverage; Initial guesses for the Gaussian fits; How the 100 empty positions were chosen; Fruchter&Hook-based cube regridding…

### 2021A&A...645A..21G: Multiphase feedback processes in the Sy2 galaxy NGC 5643 (2021; nearby_galaxies, agn_and_quasars; archival_reuse)
- question: Investigate the AGN-driven outflow in the cold molecular and ionized gas phases of NGC 5643.
- step 4: Fit regional molecular and ionized spectra
  - method: Extract 91 regions with 1.2″ × 1.2″ apertures; fit CO and [O iii] with Gaussian components using PySpecKit. [Region selection: "To study the kinematics of the ionized and molecular gas of NGC 5643, we selected 91 different regions."] [Region selection: "we chose 1.2$\ensuremath{''}\times$1.2$\ensuremath{''}$ square apertures which are $\sim$2.5 times the MUSE FWHM"]
  - software: PySpecKit
  - parameter: Add second/third components for residuals >3 times the standard deviation; retain multicomponent [O iii] fits when residuals improve considerably. [CO(2-1) data — Individual regions: "only when necessary (significant residuals of the fit; $>$3 times the standard deviation) we used two or three Gaussians for the fit."] [MUSE data — Individual regions: "Finally, we only considered for the analysis those fits using two/three components when the residuals improved considerably"]
  - parameter: [O iii] AoN >3; doublet shares velocity and widths; widths exceed instrumental FWHM ~2.5 Å. [MUSE data — Individual regions: "we fit the \[O iii\] doublet emission lines (when the \[O iii\]$\lambda$5007$\AA$ emission line has AoN$>$3) simultaneously with the same velocity and widths"] [MUSE data — Individual regions: "which are always larger than the instrumental one (i.e. MUSE nominal spectral resolution FWHM$\sim$2.5$\AA$)."]
  - assumption: Fixed [O iii] doublet ratio 1/3. [MUSE data — Individual regions: "We also fixed the \[O iii\] doublet to its theoretical value (1/3; (cite: Osterbrock06))."]
  - fitting: PySpecKit χ² minimization; one to three Gaussians. [CO(2-1) data — Individual regions: "We used the *PySpecKit* code (cite: Ginsburg11), which produces the best fit using the minimization of $\chi^2$."] [CO(2-1) data — Individual regions: "only when necessary (significant residuals of the fit; $>$3 times the standard deviation) we used two or three Gaussians for the fit."]
  - validation: Inspect residuals and require substantial improvement for multicomponent [O iii] fits. [MUSE data — Individual regions: "Finally, we only considered for the analysis those fits using two/three components when the residuals improved considerably"]
- step 5: Separate rotation, inflow and outflow
  - method: Identify rotating components with the disk model, brightness and velocity continuity; subtract disk velocities; use bar and cone geometry to distinguish inflow/outflow. [Stacking regions: "When possible (high signal-to-noise ratio) we use the derived rotating disk model to identify the rotation component. Otherwise, we select the brightest line which we associated with the galaxy disk."] [Spatially resolved kinematics: "Once we identified the rotation disk components, we subtract the corresponding velocity of the galaxy disk component in each selected region from the other non-circular velocity components."]
  - parameter: For CO component offsets >100 km s^-1 from the previous region, seek continuity in disk velocities. [Stacking regions: "The only exceptions are those cases that present a large offset ($>$100 km s$^{-1}$) with respect to the immediate previous region. In this situation we look for continuity in the galaxy disk velocities."]
  - assumption: Narrow [O iii] traces disk rotation; broader components trace non-circular motions. [Position-velocity diagrams: "supports our assumption that this \[O iii\] component traces the galaxy rotation and thus the broad components the non-circular movements (i.e. the outflow)."]
  - assumption: Molecular outflow lies in the galaxy plane. [Position-velocity diagrams: "Therefore, for the molecular gas outflowing motions we make the reasonable assumption that they take place in the plane of the galaxy."]
  - validation: Check rotation-component velocities against stellar kinematics and major-axis position–velocity diagrams. [Stacking regions: "we check that the identified rotation disk component is in agreement within the errors with those of the stellar kinematics derived from the MUSE data"] [Position-velocity diagrams: "the \[O iii\] narrow component velocities (black circles) along the same axis, which are in excellent agreement with the CO(2-1) galaxy rotation curve."]
- step 6: Measure faint outflow components in stacked slices
  - method: Stack 1.2″ square-aperture spectra in east–west slices after shifting to a common rest frame; divide slices north/south and fit lines with AoN >3. [Region selection: "We constructed the slices by stacking spectra extracted with 1.2$\ensuremath{''}\times$1.2$\ensuremath{''}$ square apertures and shifted them to a common rest-frame wavelength reference."] [Stacking regions: "Using the large scale stellar bar orientation (see eg. (cite: Mulchaey97)), we divide the slices selected along the outflow, in northern and southern regions."]
  - software: PySpecKit
  - parameter: Slice widths 2.4″; heights ~6″–10″ according to [O iii] extent. [Region selection: "We defined slices with widths of 2.4$''$ and heights ranging from $\sim$6$''$ to $\sim$10$''$ depending on the extent of the \[O iii\] emission."]
  - assumption: Use previously identified disk components to set a common rest frame. [Stacking regions: "Once we have identified where the rotation disk components are we shift the velocities to a common rest-frame wavelength."]
  - fitting: Same Gaussian-fitting method as for individual regions; AoN >3. [CO(2-1) data — Radial profile along the…: "we fit all the emission lines with AoN$>$3 for each slice spectrum using the same method"] [MUSE data — Radial profile along the ou…: "for each slice along the outflow we fit all the ionized gas emission lines with AoN$>$3."]
  - validation: Compare [O iii] profiles with NGC 7009 instrumental profiles; broad wings cannot be explained by the instrumental response. [Stacking regions: "To characterize it we use VLT/MUSE data of the planetary nebula NGC 7009, which is an unresolved source"] [Stacking regions: "We find that the MUSE/VLT instrumental profile at $\lambda$5007$\AA$ is slightly asymmetry, but the detected broad lines in our work cannot be explained by an instrumental effect."]
- step 7: Correct extinction and estimate electron density
  - method: Fit Balmer and [S II] lines with shared velocity-widths; use Hα/Hβ for extinction and PyNeb temden with [S II] ratios for density. [MUSE data — Radial profile along the ou…: "for the slices we fit the H$\alpha$, H$\beta$ and \[S II\]$\lambda$6718,6732$\AA$ emission lines using the same velocity-widths to estimate the extinction and the electron density."] [MUSE data — Radial profile along the ou…: "we use the PyNeb"]
  - software: PySpecKit, PyNeb, temden
  - parameter: Maximum two Gaussians for diagnostic-line fits; theoretical [N II] doublet ratios. [MUSE data — Radial profile along the ou…: "Note that we only used a maximum of two Gaussians for the fits. We also fixed the \[N II\] doublet ratios to their theoretical values (e.g. (cite: Osterbrock06))."]
  - assumption: Intrinsic Hα/Hβ =2.86; Calzetti attenuation law, R_V =3.12. [MUSE data — Radial profile along the ou…: "For the extinction correction, we assumed an intrinsic ratio of H$\alpha$/H$\beta=$2.86 and the (cite: Calzetti00) attenuation law (R$_V=$3.12)."]
  - assumption: NLR gas temperature 10^4 K. [MUSE data — Radial profile along the ou…: "under the assumption of the typical narrow line region (NLR) gas temperature on Seyfert galaxies (10$^4$ K; e.g. (cite: Vaona12))."]
  - fitting: Shared velocity-widths; same component-addition criteria as [O iii], maximum two Gaussians. [MUSE data — Radial profile along the ou…: "As for \[O iii\], we used the same criteria to include one or two Gaussians in each individual fit. Note that we only used a maximum of two Gaussians for the fits."]
  - validation: Density increases toward the AGN, in agreement with previous Seyfert studies. [MUSE data — Radial profile along the ou…: "In agreement with previous works on Seyfert galaxies (e.g. (cite: Bennert06a; Bennert06b)), the observed gas density of the NLR gas in NGC 5643 increases with decreasing distance from the AGN."]
- step 10: Derive ionized outflow masses
  - method: Apply Fiore17 [O iii] luminosity/electron-density mass estimator to extinction-corrected outflow components; multiply M_[O iii] by 3. [Spatially resolved outflow properties: "we used the extinction-corrected \[O iii\] luminosities of the outflowing component and derived electron densities using the same methodology as in (cite: Fiore17)"] [Spatially resolved outflow properties: "We finally assumed that the total ionized gas mass is $3\times M_{\rm [O\,III]}$ (cite: Fiore17)."]
  - parameter: M_[O iii] normalization 4.0×10^7 M_⊙; luminosity normalization 10^44 erg/s; density normalization 1000 cm^-3. [Spatially resolved outflow properties: "\rm M_{\rm \rm out}^{\rm [O\,III]} = 4.0\times 10^{7}~\rm M_\odot \left(\frac{C}{10^{\rm O/H}} \right)\left(\frac{\rm L_{[O\,III]~{\rm out}}}{10^{44}~{\rm erg/s}} \right)\left(\frac{n_{\rm e}}{1000~{\rm cm^{-3}}} \right)^{-1}"]
  - assumption: C =1; equal-density ionizing clouds. [Spatially resolved outflow properties: "This last parameter can be approximated as C$=$1 under the assumption that all ionizing gas clouds have the same density (see e.g. (cite: Cano12) for further details)."]
  - assumption: NLR [O/H] =9.0; solar [O/H] ~8.86. [Spatially resolved outflow properties: "For the oxygen abundance we used the median value of \[O/H\]$=$9.0 derived for the NLR of NGC 5643 (cite: Storchi-Bergmann98)."] [Spatially resolved outflow properties: "10$^{\rm [O/H]}$ is the oxygen abundance in solar units (\[O/H\]$_\odot\sim$8.86; (cite: Centeno08))"]
  - assumption: Fully ionized gas; electron temperature 10^4 K. [Spatially resolved outflow properties: "Note that this estimate also assumes a fully ionized gas with an electron temperature of 10$^4$ K."]
  - validation: Also derive outflow properties without extinction correction. [Observed outflow properties: "Here we also derived the various outflow properties profiles (see Fig. [19](#c1)) without taking into account the extinction correction."]
- result: Median narrow [O iii] velocity dispersion, instrument-corrected = 97 ± ±20 km s^-1 [MUSE data — Individual regions: "$\sigma_{\rm narrow}^{\rm [O\,III]}=$97$\pm$20 km s$^{-1}$"]
- result: Median broad [O iii] velocity dispersion, instrument-corrected = 233 ± ±75 km s^-1 [MUSE data — Individual regions: "the broad component has $\sigma_{\rm broad}^{\rm [O\,III]}=$233$\pm$75 km s$^{-1}$, where the $\sigma$ values are corrected by the instrumental FWHM."]
- result: Median projected central velocity of molecular non-circular motions = 44 ± ±29 km s^-1 [Spatially resolved kinematics: "The median value (projected) for central velocity of the molecular phase non-circular motions is 44$\pm$29 km s$^{-1}$ with most regions showing velocities below 100 km s$^{-1}$."]
- result: Maximum projected ionized outflow central velocity near the AGN = ~720 ± not stated km s^-1 [Spatially resolved kinematics: "The ionized gas outflow normally shows larger velocities, reaching central velocities of $\sim$720 km s$^{-1}$ (projected) in regions close to the AGN."]
- result: Total extinction-corrected ionized outflow mass = 8.5×10^4 ± +1.6/-0.7 ×10^4 M_⊙ [Spatially resolved outflow properties: "| Ionized gas outflow mass (M$_{\odot}$) | (4.2$\pm_{0.4}^{1.4}$)$\times$10$^4$ | (4.3$\pm_{0.3}^{0.2}$)$\times$10$^4$ | (8.5$\pm_{0.7}^{1.6}$)$\times$10$^4$ |"]
- result: Total ionized outflow mass without extinction correction = 2.8×10^4 ± +0.4/-0.2 ×10^4 M_⊙ [Observed outflow properties: "| Ionized gas outflow mass (M$_{\odot}$) | (2.1$\pm_{0.1}^{0.3}$)$\times$10$^4$ | (0.7$\pm0.1$)$\times$10$^4$ | (2.8$\pm_{0.2}^{0.4}$)$\times$10$^4$ |"]
- limitation (authors): Large-scale faint CO emission could not be modelled with BAROLO; velocity extrapolation and brightness-based identification were used. [CO(2-1) data — Individual regions: "Since we could not model the large-scale faint emission with BAROLO, we extrapolated the velocity field when possible to identify the galaxy disk emission line in the fitted kinematic components."]
- limitation (authors): CO conversion factor poorly constrained; molecular masses depend on α_CO and line ratio. [CO-to-H$_2$ conversion factor: "the CO-to-H$_2$ conversion factor is poorly constrained for Seyfert galaxies."]
- limitation (authors): Electron density is the largest ionized-mass uncertainty; [S II] can give lower densities than auroral/transauroral diagnostics. [Spatially resolved outflow properties: "The largest source of uncertainty in this measure is related to the electron density (see e.g. (cite: Harrison18))."]
- not stated (card): ALMA calibration software/version, calibrators, flux-scale uncertainty and any self-calibration inherited from Herrero18.; Exact reduced ALMA cube identifier or download location; calibration and imaging scripts if starting from visibilities.; ALMA image pixel size, dimensions, cleaning thresholds/masks, primary-beam treatment and compact/extended array-combination procedure.; Exact coordinates a…

### 2019A&A...632A.106L: Physical conditions in the gas phases of the giant H II region LMC-N 11. II. Origin of [C II] and fraction of CO-dark gas (2019; nearby_galaxies, milky_way_ism; multi_facility_alma_minor)
- question: What is the origin of the [C II] 158 um line in LMC-N 11, and what fraction of the molecular gas is CO-dark H2?
- step 1: Compare integrated profiles and test for ionized-gas [C II]
  - method: Gaussian fits to line profiles; line-width, [N II]/[C II] and (CII+OI)/PAH diagnostics [3.2.2: "We can then compare the observed [N ii]/[C ii] ratio to the theoretical value in the ionized gas"]
  - software: GILDAS/CLASS
  - assumption: ionized gas at 10000 K [3.1 Comparison of the spectral profiles: "For a temperature of $10\,000$ K"]
  - validation: several independent methods agree [Section 3.2.3 Photoelectric heating eff…: "Overall, the results obtained with ([C ii]+[O i])/PAH, together with those obtained in Sections [3.2.1](#sec:linewidth) and [3.2.2](#sec:ciiorigin_nii), suggest that most of the [C ii] arises in the neutral gas."]
- step 2: Bayesian decomposition of CO, [C II], HI profiles
  - method: Simultaneous fit of N components with shared velocity and width, independent intensities, via MCMC [4.1 Profile decomposition: "We use a Bayesian approach with the Markov Chain Monte Carlo (MCMC) `PyMC3` code (cite: Salvatier2016a) along with the Metropolis-Hastings sampling algorithm."]
  - software: PyMC3
  - parameter: components 10, 15; min width 1, 2 km/s; min separation 0, 1, 2 km/s [Table 4: "| Minimum line width ($\sigma_{\rm min}$) | fixed | $1, 2$ km s$^{-1}$ |"]
  - assumption: all tracers peak at same velocity per cloud [4.1 Profile decomposition: "all tracers (CO, [C ii], H i) are assumed to peak at the same velocity for any given cloud."]
  - fitting: uniform priors on intensity, half-normal on width, half-uniform on separation [Table 4: "| Line width | free, half-normal | $>\sigma_{\rm min}$ |"]
  - validation: different input parameters tested; results stable [Section 4.1 Profile decomposition: "We also performed decompositions allowing potentially different line widths for each tracer for any given velocity component, but the main results shown in the following remain unchanged."]
- step 3: Derive CO-dark H2 with collisional [C II] model
  - method: C+ level populations with H0, H2, e- collisions; atomic [C II] subtracted, remainder attributed to H2 [4.3.2 Modeling strategy: "The \[C ii\] intensity from the molecular gas is inferred from the difference of the estimated \[C ii\] emission in the atomic phase with the observed \[C ii\]."]
  - parameter: cloud size 1-10 pc; atomic T=100 K; molecular T=50 K; n_e/n_H=1e-4 [4.3.2 Modeling strategy: "The ionization fraction is fixed to a value of $n_e/n_{\rm H}=10^{-4}$"]
  - assumption: X'_CO = 2e20 cm-2 (K km/s)-1 for CO-bright H2; thermal pressure equilibrium by default [2.4 CO (1-0): "$X'_{\rm CO}=2\times10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$"]
  - validation: compared with literature f_dark estimates [4.4.2: "The $f_{\rm dark}$ values we find are in good agreement with the estimates of (cite: Galametz2016a)"]
- result: fraction of [C II] attributable to CO-dark H2 = >95 ± not stated % [4.4.1: "Globally, we find that $>95$% of the [C ii] emission across all pointings can be attributed to CO-dark H$_2$ gas"]
- result: CO-dark fraction f_dark = ≳60 ± not stated % [4.4.2: "most of the molecular gas is CO-dark overall, with $f_{\rm dark}\gtrsim60\%$"]
- result: effective X_CO = 10^21-22 ± not stated (K km/s)^-1 cm^-2 [4.4.2: "lies in the range $10^{21-22}$ (K km s$^{-1}$)$^{-1}$ for most of the bright velocity components"]
- result: CO-dark H2 thermal pressure = 10^3.5-5 ± not stated K cm-3 [4.3.2: "corresponding to a pressure of $10^{3.5-5}$ K cm$^{-3}$"]
- limitation (authors): limited HI spatial resolution is the main caveat [5 Conclusions: "The main caveat concerns the derived column density and number density in the atomic medium, with limited spatial resolution"]
- not stated (card): ALMA calibration and imaging details (CASA version, weighting, masks); MCMC settings: number of iterations, burn-in, tuning, and likelihood noise model; Exact atomic and molecular column-density grids and the C+ collisional rates used; Mapping of ALMA spectra to GREAT pointings (aperture/center)

### 2021A&A...650A.117N: The host galaxy of the short GRB 050709 (2021; transients, nearby_galaxies, star_formation; multi_facility_alma_minor)
- question: Characterize the physical properties (star formation rate, metallicity, gas kinematics, excitation mechanisms, merger history) of the host galaxy of short GRB 050709 and constrain late-time radio emission.
- step 4: Reduce VLT/MUSE IFU data and separate stellar and gas-phase emission
  - method: Reduce MUSE exposures with the ESO MUSE pipeline, remove telluric absorption with molecfit, align astrometry to HST/F814W with SAOimage DS9 using point source Q, correct for Galactic foreground extinction, and fit and subtract stellar cont… [3.4. VLT/MUSE spectroscopy: "The data were reduced in a standard fashion following Krühler et al. (2017), using version 1.2.1 of the MUSE data reduction pipeline provided by ESO (Weilbacher et al. 2012, 2014)."] [3.4. VLT/MUSE spectroscopy: "Telluric absorption lines in the spectrum were taken into account by using the molecfit software package (Smette et al. 2015)."]
  - software: MUSE data reduction pipeline, molecfit, SAOimage DS9, Starlight
  - parameter: S/N >= 4 for bright lines (Halpha, [O III] 5007) and S/N >= 2 for faint lines (Hbeta, [N II] 6584, [S II] 6718) [4. Results: "We required S / N ≥ 4 for the bright lines (Hα, [O iii ] λ 5007) and S / N ≥ 2 for the faint lines (Hβ, [N ii ] λ 6584, [S ii ] λ 6718)."]
  - assumption: Galactic foreground E(B-V) = 0.01 mag, Milky Way extinction law (Pei 1992), R_V = 3.08 [3.4. VLT/MUSE spectroscopy: "The data were corrected for Galactic foreground reddening ( E ( B − V ) = 0.01 mag; Schlafly & Finkbeiner 2011), assuming an average Milky Way extinction law (Pei 1992) and R V = 3.08."]
  - fitting: Starlight stellar continuum fit using Bruzual & Charlot (2003) single stellar population models [3.4. VLT/MUSE spectroscopy: "To summarize, we used the Starlight software package (Cid Fernandes et al. 2005, 2009) to model the stellar continuum using a combination of single stellar population models (Bruzual & Charlot 2003) and then subtracted the fitted stellar continuum model to obtain the gas-phase-only data cube."]
  - validation: Visual inspection of Balmer absorption removal in gas-phase cube [3.4. VLT/MUSE spectroscopy: "Figure 3 does show some indication of absorption close to the Balmer lines; the Starlight fits then remove these absorption features, such that the gas-phase-only cube no longer contains any absorption lines."]
- result: Host galaxy redshift (VLT/MUSE) = 0.1607 ± 0.0001 dimensionless [4. Results: "The MUSE data revealed that the entire host is a source of emission lines at a common redshift of z = 0.1607 ± 0.0001."]
- limitation (authors): Scheduled ALMA Band 9 observations could not be performed due to weather constraints. [3.3. ALMA millimeter observations: "Unfortunately, due to weather constraints observations in band 9 could not be performed despite being scheduled."]
- limitation (authors): The faint ATCA 5.5 GHz extended emission near the GRB site is at the ~5 sigma level, so there is no guarantee that it is real and it is too faint to split in time or frequency. [3.2. ATCA radio-continuum observations: "We conclude that there may be some extended emission at the GRB explosion site at the 5σ level. This is too faint to perform a more detailed analysis (e.g., splitting in time or frequency). It does not look like a spurious source, but at the S/N level at which we detect it there is no guarantee that it is real."]
- limitation (authors): Small angular sizes (< 0.2''), faintness, and strong host foreground emission prevent MUSE from clarifying the nature of individual clumps C-G and K-M. [4.1. The nature of objects C-G and K-M: "While the HST image seems to provide compelling evidence that these are star-forming regions, young luminous stellar clusters, or background (foreground) galaxies, their individual nature cannot be clarified with certainty using the MUSE data cube."]
- not stated (card): CASA tclean cell size, image size, and deconvolver settings for ALMA imaging; Relative data weights applied when combining the C40-6 and C40-3 ALMA execution blocks; Exact emission line profile fitting procedure/code used to extract line fluxes, velocities, and velocity dispersions from the gas-phase MUSE cube

### 2015ApJ...801..123W: Star Formation Rate and Dynamical Mass of 10<SUP>8</SUP> Solar Mass Black Hole Host Galaxies At Redshift 6 (2015; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the star formation rates, [C II]/FIR ratios, velocity dispersions and dynamical masses of z~6 quasar hosts with ~1e8 Msun black holes, and do they lie on local M_BH-sigma and M_BH-M_dyn relations?
- step 2: Fit [C II] line profile
  - method: Single Gaussian plus flat continuum fitted with MCMC; extra 10% in quadrature on flux and FWHM for missing channels [Results: "A single Gaussian plus flat continuum model was fit to the available data using a Markov-Chain Monte Carlo (MCMC)."] [Results: "We add in quadrature an extra 10% uncertainty in both the line flux and FWHM due to the missing channels."]
  - assumption: Symmetric line model [Results: "This is because a symmetric line model is used"]
  - fitting: MCMC; priors not stated [Results: "A single Gaussian plus flat continuum model was fit to the available data using a Markov-Chain Monte Carlo (MCMC)."]
  - validation: Continuum level of fit consistent with continuum from line-free basebands (J2229+1457) [Results: "The continuum level of the fit is again consistent with the independent continuum level determined from the three line-free basebands."]
- step 4: Convert continuum and [C II] to L_FIR and SFR
  - method: Greybody T_d=47 K, beta=1.6; SFR=1.5e-10 L_FIR; SFR=1.0e-7 L_[CII] [Results: "As in we adopt a greybody spectrum with dust temperature, $T_{\rm d} =47$ K and emissivity index, $\beta=1.6$."]
  - assumption: All dust heated by stars, not quasar; Chabrier IMF [Results: "We note that this assumes that all the dust contributing to the 1.2 mm continuum is heated by hot stars and not by the quasar."]
- step 6: Fit L_FIR-L_[CII] relation at z>5
  - method: Single power-law fit to 12 z>5 sources with MCMC including observational uncertainties [4.2: "We fit the 12 $z>5$ sources with a single power-law model of the dependence of $L_{\rm FIR}$ on $L_{\rm [CII]}$ incorporating the observational (but not systematic) uncertainties using a MCMC procedure."]
  - fitting: MCMC, power law [Discussion, The [C ii] – far-IR luminos…: "We fit the 12 $z>5$ sources with a single power-law model of the dependence of $L_{\rm FIR}$ on $L_{\rm [CII]}$ incorporating the observational (but not systematic) uncertainties using a MCMC procedure."]
- step 7: Derive sigma and M_dyn
  - method: FWHM20 = 1.5 FWHM; v_cir=0.75 FWHM/sin i with i=arccos(a_min/a_maj); M_dyn=1.16e5 v_cir^2 D Msun, D=1.5x deconvolved FWHM [4.3: "The circular velocity is therefore $v_{\rm cir}=0.75 \,$FWHM$_{\rm [CII]} / \sin i$."] [4.3: "$M_{\rm dyn} \approx 1.16\times 10^5\, v_{\rm cir}^2 \,D \,M_\odot$"]
  - parameter: i=55 deg assumed when unresolved (J2229+1457, J1148, J1120) [4.3: "An inclination of $i=55^{\circ}$ is assumed as this is the median inclination angle for the resolved sources in this paper and (cite: Wang:2013)."]
  - assumption: [C II] gas in an inclined disk; BH mass uncertainty +0.3 dex (0.45 dex if Eddington-based) [4.3: "The \[C ii\] emitting gas is assumed to be in an inclined disk"]
  - validation: Compared J1148 M_dyn with CO-based literature value [4.3: "For comparison (cite: Walter:2004) determined a dynamical mass from CO emission in this quasar of $5.5\times 10^{10}\,M_\odot$"]
- result: FWHM [C II] J0055+0146 = 359 ± ±45 km/s [Table 1: "FWHM$_{\rm [CII]}$ | $359 \pm 45$ km s$^{-1}$ | $351 \pm 39$ km s$^{-1}$"]
- result: FWHM [C II] J2229+1457 = 351 ± ±39 km/s [Table 1: "FWHM$_{\rm [CII]}$ | $359 \pm 45$ km s$^{-1}$ | $351 \pm 39$ km s$^{-1}$"]
- result: L_FIR J0055+0146 = 4.85e11 ± ±0.78e11 Lsun [Table 1: "$(4.85 \pm 0.78) \times 10^{11}$ | $(1.24 \pm 0.67) \times 10^{11}$"]
- result: SFR_FIR J0055+0146 / J2229+1457 = 73 / 19 ± ±12 / ±10 Msun/yr [Table 1: "SFR$_{\rm FIR}\,(M_\odot\,{\rm yr}^{-1})$ | $73 \pm 12$ | $19 \pm 10$"]
- result: L_FIR-L_[CII] best fit = log L_FIR = 0.59 + 1.27 log L_[CII] ± not stated dimensionless [4.2: "\log_{10} L_{\rm FIR}=0.59+1.27 \log_{10} L_{\rm [CII]}."]
- result: M_dyn J0055+0146 / J0210-0456 / J2229+1457 = 4.2e10 / 1.3e10 / 4.4e10 ± not stated Msun [Table 2: "$207 \pm 45$ | $4.2\times 10^{10}$"]
- result: sigma J0055+0146 / J2229+1457 = 207 / 241 ± ±45 / ±51 km/s [Table 2: "$241 \pm 51$ | $4.4\times 10^{10}$"]
- limitation (authors): Dynamical masses highly uncertain (unknown gas structure, marginal resolution, missed extended gas); no formal errors [4.3: "We note that there is considerable uncertainty on these values due to the unknown spatial and velocity structure of the gas"]
- limitation (authors): Missing red-wing data of J0055+0146 may bias size and inclination [Results: "We note that the missing data in the red wing of the \[C ii\] line may cause a bias in the size and inclination"]
- not stated (card): CASA version and imaging parameters (weighting, robust, cell, image size, cleaning); Channel range used to build the continuum and the [C II] maps; Flux scale uncertainty and Neptune model used; Priors, sampler and number of walkers for the MCMC line fit and power-law fit; Rest frequency/frequency of the continuum conversion and how monochromatic flux was extrapolated to L_FIR; Exact sample list …

### 2020MNRAS.496.2155Z: AlFoCS + Fornax3D: resolved star formation in the Fornax cluster with ALMA and MUSE (2020; star_formation, nearby_galaxies, milky_way_ism; archival_reuse)
- question: Do 9 Fornax cluster galaxies follow traditional star formation relations, and how do depletion times vary within galaxies and with galaxy properties?
- step 3: Construct matched SFR surface-density maps
  - method: Convert Balmer-decrement-corrected Hα flux to luminosity and SFR; divide by spaxel area; classify ionisation; convolve and regrid to ALMA. [Star formation rate surface densities: "SFR maps are obtained by calculating star formation rates from the Balmer decrement corrected H$\alpha$ maps"] [Star formation rate surface densities: "The SFR is then divided by the spaxel area in kpc$^2$ to obtain the SFR surface density"]
  - parameter: L(Hα) = 4πD²F(Hα); SFR = L(Hα)/(1.86 × 10^41) [Star formation rate surface densities: "\text{SFR} \left( M_\odot\ \text{yr}^{-1} \right) = \frac{L \left( \text{H}_\alpha \right)}{1.86 \times 10^{41}},"] [Star formation rate surface densities: "L \left( \text{H}_\alpha \right) = 4 \pi D^2 F \left( \text{H}_\alpha \right),"]
  - parameter: Hα and BPT diagnostic lines require S/N > 3 [Star formation rate surface densities: "Only spaxels with H$\alpha$ detections (S/N $>$ 3) are considered."] [Star formation rate surface densities: "Only spaxels with sufficient S/N ($>$3) in these lines to reliably determine the nature of the H$\alpha$ emission were included in the maps)."]
  - parameter: BPT: [OIII]λ5007/Hβ and [NII]λ6583/Hα; Kauffmann2003 star-forming boundary; Kewley2001 composite upper boundary [Star formation rate surface densities: "using the \[OIII\]$\lambda5007$/H$\beta$ and \[NII\]$\lambda 6583$/H$\alpha$ line ratios."] [Star formation rate surface densities: "The boundary line from (cite: Kauffmann2003) was used as a cut-off to define which pixels contain star-forming H$\alpha$, and the one from (cite: Kewley2001) as an upper limit for composites."]
  - assumption: 20 Mpc common distance [Introduction: "we adopt the distance to the Fornax cluster (20 Mpc, (cite: Blakeslee2009)) as a common distance to all galaxies."]
  - assumption: Pure star-forming Hα gives a lower SFR limit; adding composite regions gives an upper limit [Star formation rate surface densities: "Since emission from composite regions is only partly due to star formation, including these regions allows us to set an upper limit to the total star formation rate of each system."] [Star formation rate surface densities: "A corresponding lower limit can be set by removing these spaxels entirely."]
  - validation: Repeat analysis with star-forming-only and star-forming-plus-composite Hα [Star formation rate surface densities: "we consider two cases throughout this paper: one where only the spaxels strictly dominated by star formation are taken into account, and one where spaxels classified as “composite” are included also."]
- limitation (authors): Sample biased towards higher-mass, star-forming galaxies [The sample: "As F3D targeted only the brightest galaxies ($m_B < 15$), and AlFoCS is mostly IR selected, the sample is likely biased towards higher-mass, star forming galaxies."]
- limitation (authors): Six Paper I detections lack inclusion in this study [The sample: "6 galaxies detected in Paper I are not included here: the large spiral FCC121 (NGC1365), the edge-on spiral FCC67 (NGC1351A), and four dwarf galaxies with disturbed molecular gas reservoirs."]
- limitation (authors): FCC290 has only partial MUSE coverage [H$\alpha$ data: "An exception is FCC290, which was only observed partially"]
- not stated (card): Per-galaxy CO image filenames, exact synthesized beams, and moment-map noise maps.; Manual calibration scripts, calibrator identities, flagging, and flux-scale procedure from Paper I.; Continuum-subtraction task, fit order, and line-free channel selections.; CLEAN stopping thresholds, image dimensions, interactive masks, and masked-moment thresholds and smoothing.; Per-galaxy metallicities, their…

### 2024A&A...689A.101C: [CII] luminosity models and large-scale image cubes based on COSMOS 2020 and ALPINE-ALMA [CII] data back to the epoch of reionisation (2024; cosmology, high_z_galaxies; theory_or_simulation_compared_to_alma)
- question: Build mock [CII] line intensity mapping cubes from the COSMOS 2020 catalogue with literature and ALPINE-derived [CII] luminosity models, to give lower limits on power spectra and S/N forecasts for FYST EoR-Spec
- step 2: Derive ALPINE-based [CII] luminosity models m1-m4
  - method: Least-squares fits of L[CII] to combinations of bulk properties (SFR, stellar mass, sSFR, metallicity), on individual galaxies and on 5-bin averages, then selection of acceptable models [[CII] modelling: "These fits were applied to all 65 data points using standard least-squares fitting procedures, as well as to these data points sorted into 5 bins."]
  - parameter: chi2_nu acceptance limit of 4 sigma around 1 [ALPINE model checks: "A model was viewed as acceptable when its $\chi^2_\nu$ is within $4\,\sigma$ of the expected value for a good model, 1."]
  - assumption: Only physical bulk properties used; no fits with spectral lines, IR emission or redshift [[CII] modelling: "We did not attempt to fit models with spectral lines (such as \[OIII\]), IR emission, or redshift"]
  - fitting: Least-squares fits; parameter errors from Monte Carlo methods [[CII] modelling: "We calculated the errors in the fit parameters using Monte Carlo methods."]
  - validation: Outlier-input test, comparison of resulting L[CII] distributions with ALPINE (<20% difference in mean and standard deviation) and a physical-sense check [ALPINE model checks: "If these distributions had similar means and standard deviations ($<20$% difference), we accepted the model."] [ALPINE model checks: "Finally, we checked that each model made basic physical sense."]
- step 3: Apply [CII] models to FARMER LP galaxies
  - method: Apply the literature and ALPINE [CII] models to the bulk properties of each galaxy to get L[CII] [Method: "We applied the \[CII\] models to the bulk property data (i.e. stellar masses, SFRs) of the sub-sample to estimate \[CII\] luminosity data"]
  - assumption: Models taken from empirical literature rather than PDR or simulation-based models, to reduce assumptions [[CII] modelling: "We took models from previous literature that used empirical data instead of those that used PDR modelling and other simulations, in order to reduce the number of assumptions made when creating our intensity cubes and power spectra."]
- result: Model m2 coefficients (log L[CII] = a + b log Mstar) = a=4.02, b=0.476 ± a +/-0.35, b +/-0.035 dimensionless [[CII] modelling: "4.02(\pm0.35)+0.476(\pm0.035)"]
- result: Model m3 coefficients (a, SFR term, Mstar term) = a=3.31, SFR coeff=-0.33, Mstar coeff=0.601 ± +/-0.38, +/-0.16, +/-0.057 dimensionless [[CII] modelling: "3.31(\pm0.38)-0.33(\pm0.16)"]
- result: Model m1 leading coefficients (a, Mstar term) = a=48.22, Mstar coeff=-3.49 ± +/-12.07, +/-2.24 dimensionless [[CII] modelling: "48.22(\pm12.07)-3.49(\pm2.24)"]
- result: Model m4 leading coefficients (a, sSFR term) = a=6.14, sSFR coeff=-0.31 ± +/-1.29, +/-0.15 dimensionless [[CII] modelling: "6.14(\pm1.29)-0.31(\pm0.15)"]
- limitation (authors): ALPINE sample biased toward star-forming galaxies [Data: ALPINE: "this sample is biased towards SFGs over quiescent galaxies"]
- limitation (authors): Error budget excludes foregrounds and sky noise [Error analysis: "While we cannot presently include all possible error contributions, such as errors from foreground contamination removal and sky noise"]
- limitation (authors): Multiple Schechter fits are valid and change the extrapolated counts [Extrapolating from mass and luminosity …: "In many cases we could produce multiple valid Schechter fits for a given function"]
- not stated (card): Identifiers and values of the 65 ALPINE galaxies (stellar mass, SFR, L[CII] with errors) are not tabulated; they must be taken from the public ALPINE catalogues; Number of Monte Carlo draws and error model used for the fit-parameter uncertainties; Which least-squares routine and weights were used for the model fits and the 5-bin fits; Random seeds and sampling used for the ten random stellar-mask…

### 2024A&A...684A.107M: Optical tomography of the born-again ejecta of A 58 (2024; evolved_stars, stellar_physics; multi_facility_alma_minor)
- question: What is the morpho-kinematic and 3D physical structure of the H-deficient ionized and molecular ejecta in the born-again planetary nebula A 58?
- step 2: Sub-resolution spatial-kinematic tomography of optical emission and alignment with HST and ALMA
  - method: Determine the position of the central star V605 Aql by fitting a 2D Gaussian to collapsed line-free continuum images from MEGARA cubes, then fit 2D Gaussians to the [O III] and [N II] emission in each spectral channel (-250 to +350 km s^-1… [3.2.1. Relative location of V605 Aql an…: "The position of V605 Aql was then determined by adjusting a two-dimensional Gaussian to the stellar emission located near the center of the image."] [3.3. Boosting the Tomography Spatial Re…: "The high S/N achieved in the MEGARA data actually allows increasing the accuracy of the spatial location of the emission at each velocity channel by a factor ≈10 by the determining the position of the centroid of the optical emission through a two-dimensional Gaussian fit (Condon 1997)."]
  - parameter: LSR velocity range = -250 to +350 km s^-1; exclude centroids > 1 arcsec from V605 Aql or with Gaussian FWHM > 1.5 arcsec [3.3. Boosting the Tomography Spatial Re…: "These fittings were conducted for channels within the LSR velocity range from −250 to +350 km s−1."] [3.3. Boosting the Tomography Spatial Re…: "Channels with associated centroids located more than 1′′ away from the position of V605 Aql or with Gaussian FWHM exceeding 1′′.5 in any of its axes were excluded."]
  - assumption: V_sys = +103 km s^-1 [3.3. Boosting the Tomography Spatial Re…: "The centroids and FWHMs are represented with a color code indicating their velocity with respect to the adopted systemic velocity of +103 km s−1."]
  - fitting: Two-dimensional Gaussian fit per spectral channel [3.3. Boosting the Tomography Spatial Re…: "The high S/N achieved in the MEGARA data actually allows increasing the accuracy of the spatial location of the emission at each velocity channel by a factor ≈10 by the determining the position of the centroid of the optical emission through a two-dimensional Gaussian fit (Condon 1997)."]
- step 3: 3D spatio-kinematic modeling of the ionized and molecular ejecta
  - method: Construct a 3D morpho-kinematic mesh model in SHAPE combining a radially expanding molecular disk and hourglass-shaped ionized bipolar lobes, applying an ad hoc emission law to mimic dust extinction behind the disk and radial falloff, and … [4.1. Physical Structure of the H-poor E…: "The upper-left panel of this figure shows a spatio-kinematic model created with the software SHAPE (Steffen et al. 2011) consisting of a bipolar structure and a radially expanding disk inclined at an angle of i = 63◦± 4◦ with respect to the line of sight."] [4.1. Physical Structure of the H-poor E…: "Instead an arbitrary emission law has been included in the model to simulate both the effects of extinction (emission decreasing with the optical depth along the line of sight and very particularly behind the molecular disk) and distance to the CSPN (emission decreasing with radial distance to the CSPN)."]
  - software: SHAPE
  - parameter: inclination i = 63 +/- 4 deg; PA = 63 deg [4.1. Physical Structure of the H-poor E…: "The upper-left panel of this figure shows a spatio-kinematic model created with the software SHAPE (Steffen et al. 2011) consisting of a bipolar structure and a radially expanding disk inclined at an angle of i = 63◦± 4◦ with respect to the line of sight."] [4.1. Physical Structure of the H-poor E…: "These structures, oriented along a PA of 63◦ (as proposed by Tafoya et al. 2022), produce the image shown in the upper-right panel of the figure."]
  - assumption: Radial velocity vector with homologous expansion at each point; molecular disk does not emit optically but absorbs optical emission behind it. [4.1. Physical Structure of the H-poor E…: "The molecular disk is not expected to emit in the optical emission line, but it rather extincts the emission behind it."] [4.1. Physical Structure of the H-poor E…: "Considering this physical structure for the ionized material and assuming a radial velocity vector with homologous expansion at each point, it is possible to interpret the behavior of the [O iii] emission centroids shown in Fig. 3."]
  - validation: Visual comparison of the synthetic [O III] image rendered from SHAPE with the HST [O III] image. [4.1. Physical Structure of the H-poor E…: "The bottom panels show the HST [O iii] image (left) and a synthetic image rendered from the SHAPE model (right)."]
- result: Position angle of aligned low-velocity [O III] centroids = 60 ± not stated deg [3.3. Boosting the Tomography Spatial Re…: "The color code reveals that those centroids of the [O iii] emission line presumed to belong to the disk are actually aligned along a distinct direction, PA=60◦, while those at higher velocities deviate from this orientation."]
- limitation (authors): Subtraction of the surrounding old nebula emission from the central ejecta spectrum is imperfect due to spatial surface brightness variations in the outer nebula. [3.1. Spectral Line Profiles: "These residuals most likely result from spatial variations of the emission of the surrounding old nebula (see, e.g., figure 2 in Guerrero & Manchado 1996)."]
- limitation (authors): MEGARA data cubes lack absolute astrometric positioning, and there is a 0.26 arcsec (1.3 pixel) offset in the fitted stellar continuum position between VPH481-MR and VPH665-HR. [3.2.1. Relative location of V605 Aql an…: "At any rate there is no information on the absolute positioning of the MEGARA data cubes, which compromises a comparison of the spatial properties of the optical outflow with the HST and ALMA observations."]
- limitation (authors): SHAPE does not include radiative transfer physics, so the spatially varying dust extinction from the disk had to be approximated with an arbitrary emission law. [4.1. Physical Structure of the H-poor E…: "In this sense it should be noted that SHAPE does not account for radiative transfer physics, thus the effects of the spatially-varying extinction caused by the disk cannot be modeled."]
- not stated (card): All ALMA calibration and imaging parameters (deferred to Tafoya et al. 2022); Exact mathematical form and parameters of the ad hoc emission and extinction law used in the SHAPE 3D model; Exact geometric dimensions and expansion velocity parameters of the hourglass lobes in SHAPE; Software tool used to compute the ALMA HCN(4-3) zeroth and first moment maps

### 2020MNRAS.498.3624L: Constraints on the electron-to-proton mass ratio variation at the epoch of reionization (2020; cosmology, high_z_galaxies, agn_and_quasars; archival_reuse)
- question: Constrain variation of the electron-to-proton mass ratio mu at z > 6 from velocity offsets between [CI]/[CII] fine-structure lines and CO rotational lines in two quasar hosts, and combine with all other Delta mu/mu estimates to test a reds…
- step 2: Fit line profiles of J0439+1634
  - method: Single-component Gaussian fit to each of [CII], [CI], CO(6-5), CO(7-6), CO(9-8); CO(10-9) excluded because blended [3.1 Constraints on mu-variation at z=6.…: "Each individual line was fitted by a single-component Gaussian model (shown by red)."] [3.1 Constraints on mu-variation at z=6.…: "We do not use the last one since it is blended with the H"]
  - assumption: Alpha is kept fixed, so Delta F/F = -Delta mu/mu [Data and method: "Therefore, in this paper we will assume that $\alpha$ is kept fixed."]
  - fitting: Single Gaussian per line; centroid and FWHM free [3.1 Constraints on mu-variation at z=6.…: "Each individual line was fitted by a single-component Gaussian model (shown by red)."]
  - validation: Chi-squared per degree of freedom of about 1 [3.1 Constraints on mu-variation at z=6.…: "with the minimum values of $\chi^2$ per degrees of freedom of about 1"]
- step 4: Delta mu/mu from J2310+1855 at z=6.003
  - method: Average five CO redshifts from L20 and compare with [CII] redshift [3.2 Constraints on mu-variation at z=6.…: "With $z_{\rm fs} = z_{\scriptscriptstyle \rm [CII]} = 6.0031(2)$ the updated result at $z = 6.003$ yields $\Delta\mu/\mu$ = $(2.3\pm3.4)\times10^{-5}$ ($1\sigma$)."] [3.2 Constraints on mu-variation at z=6.…: "From this dataset we selected CO lines obtained with the highest angular resolution and with redshifts measured with errors"]
  - assumption: [CII] and CO lines co-spatially distributed (similar widths) [3.2 Constraints on mu-variation at z=6.…: "The width of [CII] is in good agreement with CO lines, i.e., they all are, most probably, co-spatially distributed."]
- result: Delta mu/mu at z=6.003 (J2310+1855) = 2.3 ± 3.4e-5 (1 sigma) dimensionless (x1e-5) [Summary: "yields $\Delta\mu/\mu$ $= (2.3 \pm 3.4)\times10^{-5}$ at $z = 6.003$."]
- result: CO(7-6) velocity offset from [CII] in J0439+1634 = 20.3 ± not stated km/s [3.1 Constraints on mu-variation at z=6.…: "with the velocity offset $\Delta V = 20.3$ km s$^{-1}$"]
- limitation (authors): Unexplained 20.3 km/s offset of CO(7-6), probably systematic [3.1 Constraints on mu-variation at z=6.…: "The reason for such a large velocity offset is unclear and probably due to some systematic effects"]
- limitation (authors): Differential lensing in compact lensed J0439+1634 may distort line profiles and shift line positions [Data and method: "This may modify the offset between the relative positions of spectral lines."]
- not stated (card): How the weighted mean and its error are computed for combining redshifts and for the final z=6.3 mean (formula, treatment of Doppler noise term); How the uncertainty on <z>_fs and <z>_rot and on Delta mu/mu is propagated; Which individual line redshifts for J0439+1634 are averaged (Table 1 values) and the exact data points and weights, including any systematic terms, entering the regression for k…

### 2018MNRAS.476.4949D: The ALMA-PILS survey: the sulphur connection between protostars and comets: IRAS 16293-2422 B and 67P/Churyumov-Gerasimenko (2018; astrochemistry, star_formation; archival_reuse)
- question: What is the sulphur-bearing molecule inventory at ~60 au from IRAS 16293-2422 B, and how do its molecular ratios compare with those of comet 67P/C-G measured by ROSINA?
- step 1: line search and LTE modelling
  - method: Line search and LTE modelling at one-beam SW offset of source B, then synthetic spectra [3 Results and analysis: "The initial line searching and local thermal equilibrium (LTE) modelling have been carried out with CASSIS"]
  - software: CASSIS, IDL
  - parameter: Tex = 125 K, FWHM 1 km/s, source size 0.5 arcsec (beam dilution 0.5) [3 Results and analysis: "assuming a constant $T_{\text{ex}}=125$ K for all species"]
  - assumption: LTE; local ISM 32S/34S = 22; solar 32S/33S=125, 32S/36S=4747 [3 Results and analysis: "($^{32}$S/$^{34}$S $=22$)"]
  - fitting: Best fit by eye on a grid of synthetic spectra, 25 K Tex steps [3 Results and analysis: "determined as best-fitting by eye based on a grid of synthetic spectra with $25$ K steps"]
  - validation: LTE checked via non-LTE for methanol in Jorgensen2016 [3 Results and analysis: "This assumption has also been quantified for the case of methanol (CH$_{3}$OH) in section $5.1$ of (cite: Jorgensen2016)."]
- result: SO2 column density = 1.5e15 ± not stated cm-2 [3.1 SO2: "at a column density of $1.5\times10^{15}$ cm$^{-2}$"]
- result: OCS column density (best estimate from three isotopologues) = 2.8e17 ± 0.7e17 cm-2 [3.3 OCS: "$\left( 2.8\pm0.7 \right)\times10^{17}$ cm$^{-2}$ and is the best estimate of the column density of OCS"]
- result: H2S column density (D/H=0.05) = 1.9e17 ± 0.3e17 cm-2 [3.5 H2S: "$\left( 1.9\pm0.3 \right)\times10^{17}$ cm$^{-2}$ is the best estimate of the column density of H$_{2}$S"]
- result: CH3SH column density = 5.5e15 ± not stated cm-2 [3.6 CH3SH and other species: "at a column density of $5.5\times10^{15}$ cm$^{-2}$"]
- result: 32S/33S in IRAS 16293 B = 93 ± 11 dimensionless [3.3 OCS: "$^{32}$S/$^{33}$S$ for IRAS 16293–2422 B to be $93\pm11$"]
- result: HDCS/H2CS = 0.1 ± 0.014 dimensionless [3.4 H2CS: "HDCS/H$_{2}$CS ratio to be $0.1\pm0.014$"]
- limitation (authors): H2S column uncertain by an order of magnitude due to unknown HDS/H2S [5 Conclusions: "the unknown HDS/H$_{2}$S ratio leaves the column density of H$_{2}$S uncertain by at least an order of magnitude"]
- not stated (card): Exact line lists and partition functions/CDMS-JPL entries per molecule for all lines; Column density table values and the fitted spectra in machine-readable form; Exact pixel coordinates of the one-beam offset position; Imaging/calibration parameters (in Jorgensen2016)

### 2016A&A...592A..83K: Volatile-carbon locking and release in protoplanetary disks. A study of TW Hya and HD 100546 (2016; protoplanetary_disks, astrochemistry; multi_facility_alma_minor)
- question: What is the gas-phase carbon abundance in the warm Herbig disk HD 100546 and the cold T Tauri disk TW Hya, and how are volatile carbon locking and release governed?
- step 1: Fit physical-chemical disk models with DALI
  - method: Source-specific DALI model grids fitted to SED, resolved CO 3-2 radial profile, CO ladder, [OI], [CI], [CII], HD and C2H data [5. Analysis: "we have run source-specific model grids using the 2D physical-chemical code, DALI"]
  - software: DALI
  - parameter: Chemistry evolved to 10 Myr [5. Analysis: "We let the chemistry evolve to 10 Myr to match the ages of the two disks."]
  - assumption: Disk gaps in mm opacity not included in the models [5. Analysis: "We do not presently include these in our modelling"]
  - fitting: Range of well-fitting models chosen by eye, about 100 models per source [5. Analysis: "The range of well-fitting models was chosen by eye through con"]
  - validation: APEX CO 3-2 flux checked against ALMA flux from Walsh et al. 2014a [Appendix B: "We have also checked that the total CO 3–2 line flux in our APEX data is the same as that recovered from the ALMA observation of Walsh et al. (2014a)."]
- result: [C]/[H]gas HD 100546 = (0.1-1.5)e-4 ± range of well-fitting models dimensionless [abstract: "[C]/[H] gas = (0.1−1.5)×10 [−][4]"]
- result: [C]/[H]gas TW Hya = (0.2-5.0)e-6 ± range of well-fitting models dimensionless [5.2 TW Hya: carbon and oxygen are under…: "ratio of (0.2 − 5.0) × 10 [−][6]"]
- result: HD 100546 total disk mass upper limit = ≤0.1 ± not stated Msun [abstract: "place an upper limit on the total disk mass of ≤ 0.1 M ⊙"]
- result: TW Hya best-fit disk gas mass = 2.3e-2 ± not stated Msun [5.2 TW Hya: carbon and oxygen are under…: "Our best-fit disk mass, M disk = 2.3 × 10 [−][2] M ⊙"]
- limitation (authors): Gas-to-dust ratio and radial gas extent dominate uncertainty; mm-opacity gaps not modelled [5. Analysis: "The two main sources of uncertainty are the radial extent of the gas disk and the gas to dust ratio."]
- not stated (card): ALMA calibration, imaging and CO 3-2 radial-profile extraction (done in Walsh et al. 2014a and Rosenfeld et al. 2012; not described); How model fits were compared with data (chi2 or other; fit chosen by eye); DALI chemical network and parameter grid details; Which ALMA project corresponds to which source

### 2025A&A...702A.276P: The pre-eruption state of T CrB as observed with ALMA in 2024 (2025; stellar_physics, transients, evolved_stars; observational_alma_primary)
- question: What is the pre-eruption state of T CrB and what are the properties (density, temperature, ionization) of the circumstellar medium and red giant wind into which the imminent nova ejecta will expand?
- step 1: Search for spectral line emission and derive line upper limits
  - method: Per-day, per-SPW continuum-subtracted full spectral resolution cubes were searched using the ALMA QA Pipeline line search algorithm and visual inspection; a 2-sigma upper limit on HCN v=0 J=4-3 in combined Band 7+7b SPW 4 was derived from … [Observations: "Each spectral window (SPW) underwent the sophisticated line search of the ALMA QA Pipeline (cite: 2023PASP..135g4501H) and was in addition scrutinized by visual inspection."] [Calibration, imaging, and flux density …: "On a per-day, per-SPW basis (after continuum subtraction) with full spectral resolution to search for line emission."]
  - software: ALMA Pipeline, CASA
  - parameter: velocity resolution 0.82 km/s in Band 7 SPW 4 [Spectral and spatial analysis: "The line emission in this spectral and spatial region is best constrained in band 7 (7 and 7b combined), spectral window 4 (velocity resolution 0.82 km/s, see also Tab. [1](#table:speclimits))."]
  - assumption: 10 km/s line width assumed for the HCN J=4-3 upper limit [Spectral and spatial analysis: "We thus obtain a $2 \sigma$ upper limit on the line surface brightness (assuming a 10 km/s line width) for any potential line in spectral window 4 from the peak channel of that spectral window with a value of 3.1 mJy/beam."]
  - validation: Visual inspection of all SPWs and peak channel images confirming noise-like appearance [Observations: "Each spectral window (SPW) underwent the sophisticated line search of the ALMA QA Pipeline (cite: 2023PASP..135g4501H) and was in addition scrutinized by visual inspection."] [Spectral and spatial analysis: "The image of the peak and all other channels look like noise (Fig. [4](#fig:trc-b7-peak))."]
- result: Line surface brightness 2-sigma upper limit in Band 7 SPW 4 (HCN J=4-3) = 3.1 ± 2 sigma upper limit mJy/beam [Spectral and spatial analysis: "We thus obtain a $2 \sigma$ upper limit on the line surface brightness (assuming a 10 km/s line width) for any potential line in spectral window 4 from the peak channel of that spectral window with a value of 3.1 mJy/beam."]
- limitation (authors): Incomplete orbital phase coverage across all ALMA bands: only orbital phase 0.43 has near-complete multi-band coverage (Bands 1, 3, 4, 6, 7), while the full pre-burst dataset spans 104 days (46% of the orbit). [Spectral and spatial analysis: "Our pre-burst observations of T CrB span nearly half a rotation of the system (46% from phase 0.4328 to 0.8889) but we are far from having a complete coverage of all bands at all orbital phases."]
- limitation (authors): In Band 1a, 180-degree Walsh switching was turned off, and in Band 1b one continuum spectral window was accidentally centered at 40 GHz instead of 46 GHz. [Observations: "Among these, the band 1 observation (marked "1a" in column "ALMA Band") was taken with 180$^\circ$ Walsh switching turned off"]
- limitation (authors): The difference between the softest individual 2016/17 VLA spectral index and the 2024 ALMA spectral index is only 0.26 +/- 0.13, a 2-sigma effect, requiring deeper observations over a full orbit for firmer conclusions. [Spectral re-analysis of the 2016/17 VLA…: "However, the difference between the softest VLA index and ours is only 0.26$\pm$0.13, a 2 sigma effect. Deeper observations covering the entire orbital period would be needed to draw firmer conclusions."]
- not stated (card): Exact CASA and ALMA Pipeline version numbers used for calibration and tclean imaging; Image sizes (imsize in pixels) for each band and combined images; Exact dimensions and position angles of the tight elliptical clean masks and cleaning stopping thresholds; How statistical and systematic flux calibration uncertainties were combined when weighting the scipy.optimize.curve_fit power-law fits; Whic…

### 2026ApJ..1003...26O: The SOMA Atomic Outflow Survey. I. An Atomic O I and Highly Ionized O III Outflow from Massive Protostar G11.94-00.62 (2026; star_formation; multi_facility_alma_minor)
- question: What do far-infrared [O III] and [O I] lines from SOFIA/FIFI-LS, supported by archival ALMA molecular lines, reveal about the outflow and protostellar properties of massive protostar G11.94-0.62?
- step 3: Estimate ionized outflow mass flux
  - method: PyNeb [O III] emissivity vs ne, Te linked to column density with extinction correction [4.6.1 The Ionized Outflow: "Using `PyNeb` (cite: 2015A&A...573A..42L), we calculate the emissivity of [O III] at given values of $n_e$ and $T_e$"]
  - software: PyNeb
  - assumption: XO=3e-4, Te=1e4 K, fV=1/3, all O in O2+, He singly ionized [4.6.1 The Ionized Outflow: "adopt an O abundance of $X_{\rm O}=3\times10^{-4}$ with respect to H nuclei."]
  - validation: Self-consistency of ne and nH [Mass and Momentum Outflow Rates, The Io…: "Thus, approximately self-consistent results are achieved for the case $n_e=300\:{\rm cm}^{-3}$, which implies $N_{\rm H}\simeq8.7\times10^{19}\:{\rm cm}^{-2}$ and $n_{\rm H}\simeq 325\:{\rm cm}^{-3}$"]
- result: Ionized outflow mass flux = 1.2e-4 ± not stated Msun/yr [Table 3: "Ionized | 0.116 | 211 | 24.5 | 980 | $1.2\times10^{-4}$"]
- limitation (authors): Molecular emission contaminated by nearby protostars; Tex choice gives minimum mass [4.3 Additional Outflow Tracers: "The molecular emission from these protostars contaminates the analysis of the outflow morphology from G11.94"]
- not stated (card): ALMA total power 12CO data project code and processing; Imaging parameters (robust, cell, mask, deconvolver) for combined 12m+7m 13CO, C18O, H2CO, CH3OH cubes; Velocity channels and moment ranges for blue/red maps; Which project provided TP and the 13CO/C18O data; Details of the 12CO mass-calculation formulae (opacity correction, inclination)

### 2019A&A...626A..70S: Carbon radio recombination lines from gigahertz to megahertz frequencies towards Orion A (2019; milky_way_ism, star_formation; multi_facility_alma_minor)
- question: How do carbon radio recombination lines from MHz to GHz frequencies relate to the 158 um [CII] line in the Veil and the dense PDR of Orion A, and what physical conditions do they imply?
- step 2: Constrain gas T and ne from ratios with [CII]
  - method: Compare ratios to departure-coefficient models; [CII] column from [13CII] [4.2.3 Combined constraints: "this sets a lower limit to the gas thermal pressure of $5\times10^{7}$ K cm$^{-3}$."]
  - software: CRRLpy
- result: C30alpha/[CII] ratio = 1.4e-4 ± 0.2e-4 dimensionless [4.2.2 CRRLs and FIR [CII] line: "For the C$30\alpha/$\[CII\] ratio we have a value of $(1.4\pm0.2)\times10^{-4}$."]
- result: Thermal pressure lower limit (dense PDR) = 5e7 ± not stated K cm^-3 [4.2.3 Combined constraints: "this sets a lower limit to the gas thermal pressure of $5\times10^{7}$ K cm$^{-3}$."]
- limitation (authors): Higher signal-to-noise CRRL detections needed to constrain properties independently [4.2.1 CRRLs: "higher signal-to-noise detections of the observed lines are required."]
- not stated (card): ALMA C30alpha cube processing, beam, rms and flux scale (in Bally et al. 2017); How C30alpha line intensity was integrated over the 40 arcsec region; Smoothing to common resolution for line ratios

### 2025A&A...694A.171M: The host galaxies of radio-loud quasars at z &gt; 5 with ALMA (2025; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: How do the cool gas ([CII]) and dust properties, morphology, kinematics, companions and synchrotron contribution of z>5 radio-loud quasar host galaxies compare with radio-quiet quasar hosts, and is there a signature of radio-jet interactio…
- step 1: Extract and fit 1D [CII] spectra
  - method: Extract spectrum in circular aperture centred on the quasar; aperture radius set where flux in concentric apertures (0.1'' to 3.0'') plateaus; fit flat continuum plus Gaussian line [3.1 [CII] line measurements: "We determine the best aperture by extracting the flux of the quasars in concentric apertures from 0.1$''$ up to 3.0$''$, and choosing the radius at which the flux encounters a plateau."] [3.1 [CII] line measurements: "Once the best aperture is found, we extract the one dimensional spectra, and fit them with a flat continuum and a Gaussian line."]
  - parameter: Aperture radii listed per source in the 1D table (1.3-2.3'') [Table (1D [CII] fit) notes: "The spectra were extracted from different apertures"]
  - assumption: Sources may be extended, so a source-centred aperture is used [3.1 [CII] line measurements: "In order to properly account for potentially extended sources, we extract our one dimensional spectrum for each source in an aperture centered on the quasar position"]
  - fitting: Flat continuum plus single Gaussian line; routine, priors and likelihood not stated [3.1 [CII] line measurements: "we extract the one dimensional spectra, and fit them with a flat continuum and a Gaussian line."]
- step 2: Build continuum-subtracted [CII] cubes and moment-0 maps; measure line flux with 2D Gaussian
  - method: Choose line window at Gaussian-fit peak +/-1.4 sigma, uvcontsub in uv space, re-image with tclean (robust=2), moment-0 maps, 2D Gaussian fit in CASA, correct flux by ~1.20 [3.1 [CII] line measurements: "The continuum subtraction is done in the *uv* space using the CASA task *uvcontsub*."] [3.1 [CII] line measurements: "selecting a small rectangular region around the source."]
  - software: CASA, tclean, uvcontsub
  - parameter: Line window = Gaussian-fit peak +/-1.4 sigma (~83% of line flux) [3.1 [CII] line measurements: "this recovers $\sim 83\%$ of the total line flux and maximizes the SNR, in case of a perfectly Gaussian line profile (e.g. (cite: decarli2018), (cite: novak2020), appendix A)"]
  - parameter: Flux correction factor ~1.20 [3.1 [CII] line measurements: "therefore the 2D flux need to be corrected by a factor of $\sim$1.20 (e.g. (cite: decarli2018))"]
  - assumption: Gaussian line profile [3.1 [CII] line measurements: "in case of a perfectly Gaussian line profile"]
  - fitting: 2D Gaussian fit within CASA to the moment-0 map in a small rectangular region [3.1 [CII] line measurements: "selecting a small rectangular region around the source."]
  - validation: Sizes consistent with beam; PSO352-15 results consistent with Rojas et al. [3.1 [CII] line measurements: "our results for the quasar PSO352-15 are consistent with those presented in (cite: rojas2021)"]
- step 5: Estimate redshifts from [CII] and velocity offsets of UV lines
  - method: Redshift from [CII] peak; compare to literature Mg II, Lya and template redshifts as velocity offsets [4.2 Redshift estimations: "We estimate the redshifts of the quasars in our sample from the peak of the"]
  - assumption: [CII] defines the systemic redshift [4.2 Redshift estimations: "with respect to lines arising from the ISM in the host galaxy, considered the rest-frame of the system"]
- step 7: Derive L_CII, dust mass, L_FIR/L_TIR, SFRs, [CII] EW
  - method: L_CII from line flux (Carilli & Walter relation); optically thin modified black body scaled to 1900 GHz continuum with CMB correction; integrate for L_FIR (42.5-122.5 um) and L_TIR (8-1000 um); SFR_CII from De Looze 2014; SFR_IR from Kenni… [4.4 IR and [CII] luminosities, SFRs and…: "in the optically thin scenario, the observed continuum flux density can be derived as follows"] [4.4 IR and [CII] luminosities, SFRs and…: "by integrating the SED between 8 and 1000 $\mu$m (e.g. (cite: kennicutt2012))"]
  - parameter: T_dust = 47 K, beta = 1.6 [4.4 IR and [CII] luminosities, SFRs and…: "$T_{\rm dust} = 47 K$ and $\beta = 1.6$"]
  - parameter: L_FIR = 0.75 L_TIR for the adopted model [4.4 IR and [CII] luminosities, SFRs and…: "which is equivalent to $L_{\rm FIR} = 0.75 L_{\rm TIR}$ for the model considered here."]
  - assumption: Optically thin dust; fixed T_dust and beta from literature [4.4 IR and [CII] luminosities, SFRs and…: "in the optically thin scenario, the observed continuum flux density can be derived as follows"] [4.4 IR and [CII] luminosities, SFRs and…: "Here, we consider values for dust temperature and $\beta$ typically used in the literature"]
  - assumption: Cosmology H0=67.8, OmegaM=0.3, OmegaL=0.7 [1 Introduction: "with $H_{0} = 67.8$ km s${-1}$ Mpc$^{-1}$, $\Omega_{M} = 0.3$ and $\Omega_{\Lambda} = 0.7$."]
  - fitting: Dust mass obtained by scaling the model to the observed flux; no sampling [4.4 IR and [CII] luminosities, SFRs and…: "We scale the above function to the observed continuum flux densities at"]
- step 8: Estimate dynamical and molecular gas masses
  - method: Dispersion-dominated M_dyn from [CII] size (major axis of 2D Gaussian) and FWHM with inclination 46 deg; M_H2 from L_CII with alpha_CII=30 Msun/Lsun [4.6 Mass Budget: "we estimate the dynamical masses of the host galaxies presented here in a simplified way, following (cite: decarli2018)."] [4.6 Mass Budget: "We utilize an angle $i=46^{\circ}$"]
  - parameter: alpha_CII = 30 Msun/Lsun; inclination 46 deg [4.6 Mass Budget: "with $\alpha_{\rm [C\,II]} = 30 M_{\odot} L_{\odot}^{-1}$."]
  - assumption: Unresolved system, dispersion dominated (sigma = 0.75 FWHM); inclination from literature median [4.6 Mass Budget: "under the assumption that the system is dominated by dispersion"] [4.6 Mass Budget: "We utilize an angle $i=46^{\circ}$"]
  - validation: Compared with RQ quasar literature dynamical masses [4.6 Mass Budget: "This is broadly consistent with values similarly obtained for RQ quasars in the literature"]
- step 9: Compare RL and RQ quasar hosts (distributions, KS test, [CII] deficit, UV luminosity)
  - method: Re-derive quantities consistently for literature RQ (76) and RL sources; compare L_CII, EW, FWHM, SFR distributions with Kolmogorov-Smirnov tests; plot L_CII/L_FIR vs L_FIR and vs M1450 [4.4 IR and [CII] luminosities, SFRs and…: "We performed a Kolmogorov-Smirnov (KS) test in order to assess if these properties are taken from the same underlying distribution"] [4.1 Literature Sample: "For all the sources from the literature, we re-derive IR and"]
  - parameter: Null rejected for p-values < 0.05 [4.4 IR and [CII] luminosities, SFRs and…: "For p-values $<0.05$, we can reject the null hypothesis"]
- step 10: Search for [CII] line-emitting companions
  - method: Run findclumps on continuum-subtracted cubes with floating-average channel windows of 3-19 channels; merge entries closer than 2''; fidelity from negative/positive detections pooled across fields; require fidelity>0.9, SNR>4, within +/-100… [4.8 Companions: "In this work, we use spectral windows of width between 3 and 19 channels."] [4.8 Companions: "we compute the fidelity considering the catalogs obtained from of all the quasars fields at once"]
  - software: findclumps, interferopy
  - parameter: Fidelity > 0.9; SNR > 4; |dv| < 1000 km/s; merge radius 2'' [4.8 Companions: "we assume a fidelity threshold as calculated in each channel of 90% (Fidelity$>$0.9)."] [4.8 Companions: "We crop multiple entries by discarding sources which are closer than 2$''$"]
  - assumption: Positive emission = real sources + noise; negative emission = noise only [4.8 Companions: "Under the assumption that the positive emission comprehends real astrophysical sources and noise, while the negative emission are due only to noise"]
  - validation: Changing the velocity limit to 2000 km/s does not change the results; fidelity check applied [Footnote 6: "We note that changing this limit to $\Delta v > \pm 2000$ km s$^{-1}$ does not change our final resuls."]
- result: [CII] flux corrected, J0131-0321 = 0.480 ± 0.095 Jy km/s [Table (2D fit results): "0.480$\pm$0.095"]
- result: [CII] flux corrected, PSO055-00 = 0.339 ± 0.028 Jy km/s [Table (2D fit results): "0.339$\pm$0.028"]
- result: [CII] flux corrected, PSO135+16 = 3.017 ± 0.111 Jy km/s [Table (2D fit results): "3.017$\pm$0.111"]
- result: [CII] flux corrected, J1034+2033 = 0.416 ± 0.041 Jy km/s [Table (2D fit results): "0.416$\pm$0.041"]
- result: [CII] flux corrected, PSO352-15 = 0.837 ± 0.112 Jy km/s [Table (2D fit results): "0.837$\pm$0.112"]
- result: [CII] redshift, J0131-0321 = 5.1928 ± 0.0006 dimensionless [Table (1D [CII] fit): "5.1928$\pm$0.0006"]
- result: [CII] redshift, PSO055-00 = 5.7183 ± 0.0005 dimensionless [Table (1D [CII] fit): "5.7183$\pm$0.0005"]
- result: [CII] redshift, PSO135+16 = 5.7183 ± 0.002 dimensionless [Table (1D [CII] fit): "5.7183$\pm$0.002"]
- result: [CII] redshift, J1034+2033 = 4.9921 ± 0.0005 dimensionless [Table (1D [CII] fit): "4.9921$\pm$0.0005"]
- result: [CII] redshift, PSO352-15 = 5.8315 ± 0.0007 dimensionless [Table (1D [CII] fit): "5.8315$\pm$0.0007"]
- result: [CII] FWHM (J0131-0321, PSO055-00, PSO135+16, J1034+2033, PSO352-15) = 170, 150, 340, 190, 390 ± 70, 60, 29, 80, 90 km/s [Table (1D [CII] fit): "170$\pm$70"]
- result: L_CII, J0131-0321 = 3.8e8 ± 0.8e8 Lsun [Table (derived [CII] properties): "3.8$\pm$0.8"]
- result: L_CII, PSO055-00 = 3.1e8 ± 0.3e8 Lsun [Table (derived [CII] properties): "3.1$\pm$0.3"]
- result: L_CII, PSO135+16 = 27.7e8 ± 1.0e8 Lsun [Table (derived [CII] properties): "27.7$\pm$1.0"]
- result: L_CII, J1034+2033 = 3.1e8 ± 0.3e8 Lsun [Table (derived [CII] properties): "3.1$\pm$0.3"]
- result: L_CII, PSO352-15 = 7.9e8 ± 1.1e8 Lsun [Table (derived [CII] properties): "7.9$\pm$1.1"]
- result: SFR_[CII], J0131-0321 = 40 ± 9 Msun/yr [Table (derived [CII] properties): "40$\pm$9"]
- result: SFR_[CII], PSO055-00 = 32 ± 3 Msun/yr [Table (derived [CII] properties): "32$\pm$3"]
- result: SFR_[CII], PSO135+16 = 416 ± 18 Msun/yr [Table (derived [CII] properties): "416$\pm$18"]
- result: SFR_[CII], J1034+2033 = 32 ± 4 Msun/yr [Table (derived [CII] properties): "32$\pm$4"]
- result: SFR_[CII], PSO352-15 = 95 ± 15 Msun/yr [Table (derived [CII] properties): "95$\pm$15"]
- result: M_dyn, J0131-0321 = 4.8e10 ± 4.0e10 Msun [Table (derived [CII] properties): "4.8$\pm$4.0"]
- result: M_dyn, PSO055-00 = 2.8e10 ± 2.2e10 Msun [Table (derived [CII] properties): "2.8$\pm$2.2"]
- result: M_dyn, PSO135+16 = 15.0e10 ± 1.8e10 Msun [Table (derived [CII] properties): "15.0$\pm$1.8"]
- result: M_dyn, J1034+2033 = 5.8e10 ± 4.9e10 Msun [Table (derived [CII] properties): "5.8$\pm$4.9"]
- result: M_dyn, PSO352-15 = 23.3e10 ± 10.7e10 Msun [Table (derived [CII] properties): "23.3$\pm$10.7"]
- result: M_H2 from [CII] (J0131-0321, PSO055-00, PSO135+16, J1034+2033, PSO352-15) = 11e9, 9.3e9, 83e9, 9.3e9, 24e9 ± 2.0e9, 0.8e9, 3.0e9, 0.9e9, 3.0e9 Msun [Table (derived [CII] properties): "11$\pm$2.0"]
- result: L_FIR (total continuum as dust), J0131-0321 = 32.4e11 ± 0.85e11 Lsun [Table (derived continuum properties): "32.4$\pm$0.85"]
- result: L_FIR (total continuum as dust), PSO135+16 = 78.8e11 ± 2.9e11 Lsun [Table (derived continuum properties): "78.8$\pm$2.9"]
- result: L_FIR (total continuum as dust), J1034+2033 = 2.4e11 ± 0.4e11 Lsun [Table (derived continuum properties): "2.4$\pm$0.4"]
- result: Velocity offset Mg II minus [CII], J0131-0321 = -127 ± not stated km/s [4.2 Redshift estimations: "is very small, i.e. $\Delta v_{\rm Mg\,II- [C\,II]} = -127$ km s$^{-1}$."]
- result: Velocity offset Lya/template minus [CII]: mean, median, st.dev = -1269, -770, 2271 ± not stated km/s [4.2 Redshift estimations: "of $-1269$, $-770$, and $2271$ km s$^{-1}$, respectively."]
- result: KS-test p-values RL vs RQ for L_CII and SFR_[CII] = 0.04 and 0.04 ± not stated dimensionless [Table (RL vs RQ statistics): "0.04"]
- result: KS-test p-values RL vs RQ for EW and FWHM = 0.24 and 0.14 ± not stated dimensionless [4.4 IR and [CII] luminosities, SFRs and…: "we calculate a p-value of 0.24 and 0.14 for EW and FWHM distributions, respectively"]
- result: Number of line-emitting companion candidates found around the five Band 7 RL quasars = 0 ± not stated dimensionless [4.8 Companions: "Considering all the above conditions, we do not recover any companion candidate in our RL quasars fields."]
- result: Expected companions at this depth in 26 RQ quasar fields = 3 (~10% of fields) ± not stated dimensionless [4.8 Companions: "Hence, at the depth of our work, one would expect to recover 3"]
- result: Expected blank-field sources in the 5 RL fields within dv<1000 km/s = <0.02 ± not stated dimensionless [4.8 Companions: "we would expect to observe $<$0.02 sources."]
- limitation (authors): Low SNR and limited spatial resolution prevent firm conclusions on kinematics [3.1 [CII] line measurements: "due to the low SNR and the limited spatial resolution of the maps, we are not able to draw stronger conclusions on their kinematics"]
- limitation (authors): Radio data are non-simultaneous so SED shapes may be affected by variability [4.3 Radio and (sub-)mm SED: "hence the radio intrinsic SED shape might be altered by variability effects"]
- limitation (authors): PSO055-00 [CII] line lies at the edge of the bandwidth; derived quantities uncertain [3.1 [CII] line measurements: "The emission line for the quasar PSO055-00 is found at the edge of the bandwidth"]
- not stated (card): tclean cell size, image size, niter, threshold, masking, deconvolver, and primary-beam correction are not given; Which channels were used as line-free for the continuum maps and for uvcontsub, and the uvcontsub fit order; How the Gaussian fit and its uncertainties were done in 1D spectra (initial guesses, fitting routine, error estimation) and the 2D Gaussian fit box in CASA; Flux calibrator, cal…

### 2020MNRAS.494.5542R: Full of Orions: a 200-pc mapping of the interstellar medium in the redshift-3 lensed dusty star-forming galaxy SDP.81 (2020; high_z_galaxies, milky_way_ism; observational_alma_primary)
- question: Map the ISM of the lensed z=3.042 DSFG SDP.81 at ~200 pc resolution: spatial distribution of FIR continuum, CO and [C II]; gas cooling budget; PDR conditions (FUV field, density, surface temperature) and the origin of the [C II]/FIR deficit
- step 2: Make Cleaned images to check detections and integrated fluxes
  - method: Cleaned frequency-integrated maps of Band 8 continuum, [C II], CO(3-2), CO(10-9) with natural weighting and 0.2 arcsec outer taper [3.1 Data preparation and imaging: "obtained using natural weighting and an outer Gaussian taper of 0.2 arcsec"]
  - software: CASA
  - parameter: Peak S/N 5.6 sigma for CO(3-2) and ~5 for CO(10-9) [3.1.1 ALMA Band 3: "with a peak S/N of 5.6$\sigma$"] [3.1.3 ALMA Long Baseline Campaign: "(peak image-plane SN$\simeq5$, Fig. [1](#fig:cleaned))"]
  - validation: Band 3 continuum AGN flux of the lens compared with synchrotron spectrum from Tamura et al. 2015, consistent within 2 sigma [3.1.1 ALMA Band 3: "The observed flux is consistent with the (cite: Tamura2015) synchrotron spectrum for the foreground AGN within $2\sigma$."]
- step 3: Reconstruct source-plane maps by visibility-plane lens modelling
  - method: Fixed parametric SIE+shear lens model; source on an adaptive Delaunay triangular grid; penalty function combining visibility chi^2 with source-plane regularization; lambda_S re-optimized per dataset (and per [C II] channel) [3.2 Lens modelling: "To summarize, this technique uses a parametric lens model, while the source is reconstructed on an adaptive triangular grid obtained via the Delaunay tessellation."] [3.2 Lens modelling: "Keeping the lens mass model fixed, we re-optimize for the offset between the lens center and phase-tracking centre"]
  - software: lens-modelling code of Rybak et al. 2015a (not named)
  - parameter: Sky-plane pixel size 25 mas; every second pixel cast back, so beam sub-sampled by ~4 [3.2 Lens modelling: "The sky-plane pixel size is set to 25 mas"]
  - parameter: Primary beam approximated by an elliptical Gaussian [3.2 Lens modelling: "The primary beam response is approximated by an elliptical Gaussian."]
  - parameter: Visibility noise from the scatter over 10-minute intervals rather than the Sigma column [3.2 Lens modelling: "rather than from the Sigma column of the ALMA Measurement Set files"]
  - parameter: [C II] reconstructed in 62.50 MHz (~40 km/s) channels with lambda_S optimized per channel; moment-0 and moment-1 maps made (pixels with SNR <= 1 masked for moment 1) [3.3.2 [CII] emission: "We frequency-averaged the line into channels 62.50 MHz ($\sim40$ km s$^{-1}$) wide"] [3.3.2 [CII] emission: "For the moment-one map, we mask pixels with SNR$\leq$1 in each channel before calculating the velocity map."]
  - parameter: Reconstructions re-sampled onto a Cartesian grid of 200x200 pc pixels [3.3 Source-plane reconstructions: "we re-sample the reconstructed source onto a Cartesian grid with 200$\times$200 pc pixels"]
  - assumption: Lens mass model fixed to R15a (SIE with external shear) [3.2 Lens modelling: "which follows a singular isothermal ellipsoid profile with an external shear component"]
  - fitting: Minimization of a penalty function: visibility-space chi^2 plus source-plane regularization term lambda_S (R_s s)^T R_s s; no sampler or priors stated [3.2 Lens modelling: "with a source-plane regularization to constrain the problem and prevent noise-fitting"]
  - validation: Residuals in the dirty-image plane; mock-data lens-modelling tests (Appendix B) recover mean surface brightness within 10-15 per cent (~20 per cent for CO(3-2)) [3.3 Source-plane reconstructions: "we further assess the reliability of the source-plane reconstruction by performing our lens modelling analysis on mock datasets in Appendix"] [3.3 Source-plane reconstructions: "with the mean surface brightness recovered within 10–15 per cent for most datasets ($\sim$20 per cent for CO(3–2))"]
- step 6: Gas cooling budget, CO SLED and CO-FIR correlations
  - method: Compare source-plane [C II], [O I] and CO line luminosities; unobserved CO lines scaled with Class I ULIRG ratios; Pearson correlation of CO or [C II] with FIR per pixel (SNR >= 3) with 1000 Monte Carlo realizations [4.2.1 [CII] dominates the gas cooling b…: "assuming that the CO line ratios in SDP.81 match CO ratios of the Class I ULIRGs from (cite: Rosenberg2015)"] [4.2.2 CO spectral energy distribution: "for each pixel with SNR$\geq$3 in both tracers"]
  - parameter: CO(1-0), CO(7-6) and CO(9-8) assumed to follow the spatial distribution of CO(3-2), (8-7) and (10-9) [4.2 Emission lines: "we assume that the CO(1–0), (7–6) and (9–8) lines follow the same spatial distribution as the CO(3–2), (8–7) and (10–9) lines, respectively"]
  - assumption: [O I] lines assumed to follow the FIR continuum surface brightness distribution [4.2.1 [CII] dominates the gas cooling b…: "Assuming both lines follow the FIR continuum surface brightness distribution, we obtain the de-lensed source-plane luminosities"]
  - validation: CO SLED well reproduced (chi^2 <= 1) by PDRToolbox models without mechanical heating [4.2.2 CO spectral energy distribution: "As the SDP.81 CO ladder is well-reproduced ($\chi^2\leq1$) by the PDRToolbox models which do not include mechanical heating"]
- step 8: Measure the global and resolved [C II]/FIR ratio and its slope with Sigma_SFR
  - method: Ratio of source-plane [C II] and FIR luminosities, globally and per 200 pc pixel; log-log slope vs Sigma_SFR by orthogonal distance regression [4.3 [CII]/FIR ratio and deficit: "using orthogonal distance regression, similar to the slope of $-0.7$ derived by (cite: Lamarche2018) for SDP.11"]
  - fitting: Orthogonal distance regression of log Sigma_SFR vs log([C II]/FIR) [4.3 [CII]/FIR ratio and deficit: "using orthogonal distance regression"]
  - validation: Compared with Smith et al. 2017 trend and other high-z resolved studies; isolated outlying low-ratio pixels judged lens-modelling artifacts [4.3 [CII]/FIR ratio and deficit: "these are likely lens-modelling artifacts"]
- step 9: PDR modelling of G, n and T_PDR (global and per 200 pc pixel)
  - method: Chi^2 comparison of observed line ratios with PDRToolbox predictions over a G-n grid, including 3-sigma upper limits following Sawicki 2012; maximum a posteriori model for the global fit [5.1 Modelling setup: "Following (cite: Sawicki2012), we include the $3\sigma$ upper limits as"] [5.2 Global PDR model: "The maximum a posteriori model gives $G = 10^{3.1\pm0.1}~G_0$, $n = 10^{4.9\pm0.1}$ cm$^{-3}$, with a reduced $\chi^2=0.96$."]
  - software: PDRToolbox
  - parameter: Line ratios: [C II]/FIR, [C II]/CO(5-4), [C II]/CO(3-2), CO(8-7)/CO(5-4), CO(10-9)/CO(5-4) [5.1 Modelling setup: "For the comparison with observations, we consider the following independent line ratios: \[C ii\]/FIR, \[C ii\]/CO(5–4), \[C ii\]/CO(3–2), CO(8–7)/CO(5–4) and CO(10–9)/CO(5–4)."]
  - parameter: Pixels with SNR >= 3 treated as detections, SNR < 3 as 3-sigma upper limits [5.1 Modelling setup: "for pixels with SNR$<3$, we adopt $3\sigma$ upper limits."]
  - parameter: PDR fraction of [C II] adopted f_PDR = 0.8 [5.1 Modelling setup: "we adopt a conservative estimate of the $f_\mathrm{[CII]}^\mathrm{PDR}=0.8$"]
  - parameter: Solutions with G0/n <= 1e-3 discarded as unphysical [5.3 Resolved PDR model: "we discard the solutions with $G_0/n$(H)$\leq10^{-3}$, which would imply an unphysically large source"]
  - parameter: Error budget per pixel: 10 per cent flux calibration, lens-model scatter, and mock-source systematic (6 to 65 per cent) [5.3 Resolved PDR model: "Flux calibration uncertainty, assumed to be 10 per cent in each Band."] [5.3 Resolved PDR model: "These vary between 6 per cent (FIR continuum) to 30 per cent for CO(10–9) and 65 per cent for CO(3–2)"]
  - assumption: Solar metallicity PDRToolbox model, semi-infinite slab, uniform density [5.1 Modelling setup: "we consider the $Z=1~Z_\odot$ default PDRToolbox model as appropriate for dust-rich ISM of SDP.81"]
  - assumption: Optically thin tracers (FIR, [C II]) predictions doubled for multi-sided illumination; CO lines optically thick [5.1 Modelling setup: "for the optically-thin tracers, both the sides facing to and away from the observer will contribute to the observed flux, and the predicted fluxes need to be doubled."]
  - fitting: Chi^2 minimization on a 0.05 dex G-n grid with upper-limit term (Sawicki 2012); no sampler or priors stated [5.1 Modelling setup: "We re-sample them onto a finer grid (steps of 0.05 dex), using a degree 2 spline for interpolation."]
  - validation: Models reproduce line ratios with reduced chi^2 <= 5; shifts of <= 0.5 dex in G and n under an order-unity bias in the line ratios; detections-only fit changes G, n by <= 0.1 dex [5.4.1 Caveats and limitations: "The PDRToolbox models reproduce the observed line ratios well (reduced $\chi^2\leq5$)"] [5.1 Modelling setup: "We find that the inferred $G$, $n$(H) values shift by $\leq0.5$ dex even in such an extreme scenario"]
- step 10: Test mechanisms behind the [C II]/FIR deficit
  - method: Compare reduced photoelectric heating (Wolfire 2003), AGN X-ray influence and C+ thermal saturation (Munoz & Oh 2016, with correction f_CII for the gas fraction traced by [C II]) against the resolved maps [5.4 What drives the [CII]/FIR deficit i…: "we consider the following mechanisms: (1) thermal saturation of the \[C ii\] fine-structure levels; (2) reduced gas heating due to positive grain charging; (3) AGN contribution."]
  - parameter: n_e = 1.1e-4 n; phi_PAH = 0.5 in the photoelectric heating rate [5.4.1 Reduced photoelectric heating: "Assuming $n_e=1.1\times10^{-4}\,n$ and $\phi_\mathrm{PAH}=0.5$"]
  - parameter: f_CII computed per pixel from CO(5-4) S/N >= 3 pixels using the Bothwell 2013 conversion and alpha_CO from CR18 [5.4.3 C+ thermal saturation: "by using the (cite: Bothwell2013) conversion factor and $\alpha_\mathrm{CO}$ from (cite: CR18)"]
  - assumption: PDR surface temperature taken as the gas temperature in the [C II]-emitting layer; [C II] optically thin; dense gas above critical density [5.4.3 C+ thermal saturation: "This allows us to take the PDR surface temperature $T_\mathrm{PDR}$ as indicative of the gas temperature in the \[C ii\]-emitting regions."]
  - fitting: Power-law slope of [C II]/FIR vs Sigma_SFR fitted before and after the f_CII correction [5.4.3 C+ thermal saturation: "we obtain a best-fitting power-law slope of $=-0.55\pm0.02$"]
  - validation: Corrected slope -0.55 +/- 0.02 matches the thermal-saturation prediction (-0.5); uncorrected slope 0.65 +/- 0.01 is in tension [5.4.3 C+ thermal saturation: "in line with the (cite: MunozOh2016) prediction"]
- result: Median source-plane resolution = ~30 mas (~200 pc) ± not stated mas / pc [3.3 Source-plane reconstructions: "The median source-plane resolution is $\sim$30 mas, which corresponds to $\sim$200 parsec"]
- result: Band 3 continuum flux of the lens-galaxy AGN = 52 ± 10 uJy [3.1.1 ALMA Band 3: "with a total flux of 52$\pm$10 $\mu$Jy"]
- result: Image-plane [C II] integrated line flux = 170 ± 20 Jy km/s [3.1.2 ALMA Band 8: "integrated line flux of 170$\pm$20 Jy km s$^{1}$"]
- result: Spatially integrated [C II]/FIR luminosity ratio = 1.5e-3 ± 0.3e-3 dimensionless [4.3 [CII]/FIR ratio and deficit: "FIR luminosity ratio of $(1.5 \pm 0.3)\times 10^{-3}$"]
- result: [C II]/FIR slope vs Sigma_SFR = -0.75 ± 0.01 dimensionless [4.3 [CII]/FIR ratio and deficit: "slope of $-0.75\pm0.01$, using orthogonal distance regression"]
- result: Pearson correlation of CO(3-2), CO(5-4), CO(8-7), CO(10-9) with FIR = 0.401, 0.847, 0.821, 0.664 ± 0.010, 0.006, 0.006, 0.09 dimensionless [4.2.2 CO spectral energy distribution: "We find $R_\mathrm{CO(3-2)/FIR}=0.401\pm0.010$, $R_\mathrm{CO(5-4)/FIR}=0.847\pm0.006$, $R_\mathrm{CO(8-7)/FIR}=0.821\pm0.006$ and $R_\mathrm{CO(10-9)/FIR}=0.664\pm0.09$."]
- result: Global PDR FUV field G = 10^3.1 ± +/-0.1 dex G0 [5.2 Global PDR model: "The maximum a posteriori model gives $G = 10^{3.1\pm0.1}~G_0$, $n = 10^{4.9\pm0.1}$ cm$^{-3}$, with a reduced $\chi^2=0.96$."]
- result: Global PDR gas density n = 10^4.9 ± +/-0.1 dex cm^-3 [5.2 Global PDR model: "The maximum a posteriori model gives $G = 10^{3.1\pm0.1}~G_0$, $n = 10^{4.9\pm0.1}$ cm$^{-3}$, with a reduced $\chi^2=0.96$."]
- result: Resolved PDR G and n in the central FIR-bright region = G = 10^3.5-10^4.0 G0; n(H) = 10^5.0-10^5.5 cm^-3 ± typical ~0.2 dex G0; cm^-3 [5.3 Resolved PDR model: "we find strong FUV fields with $G=10^{3.5} - 10^{4.0}~G_0$, and high density $n$(H)=$10^{5.0}-10^{5.5}$ cm$^{-3}$, with a typical uncertainty of $\sim0.2$ dex"]
- result: East-West gradient in G = 10^3.0 to 10^4.0 ± +/-0.2 and +/-0.1 dex G0 [5.3 Resolved PDR model: "$G$ increases from $10^{3.0\pm0.2}$ to $10^{4.0\pm0.1}~G_0$"]
- result: PDR surface temperature = ~150 K (outskirts) to 1500 K (FIR-bright clumps) ± S/N <= 5 across the source K [5.3 Resolved PDR model: "The PDR surface temperature $T_\mathrm{PDR}$ varies from about 150 K in the outskirts to 1500 K in the FIR-bright clumps."]
- result: Resolved [C II]/FIR minimum in FIR-bright clumps = ~(2-3)e-4 ± not stated dimensionless [4.3 [CII]/FIR ratio and deficit: "down to $\sim(2-3)\times10^{-4}$ in the two FIR-bright clumps"]
- result: Fraction of [C II] luminosity from Sigma_SFR <= 10 Msun/yr/kpc^2 = ~50 per cent ± not stated per cent [3.3.2 [CII] emission: "$\sim$50 per cent of the total \[C ii\] luminosity arises from regions with"]
- result: [C II]/FIR slope after f_CII correction = -0.55 ± 0.02 dimensionless [5.4.3 C+ thermal saturation: "we obtain a best-fitting power-law slope of $=-0.55\pm0.02$"]
- result: [C II]/FIR slope without f_CII correction = 0.65 (as printed alpha) ± 0.01 dimensionless [5.4.3 C+ thermal saturation: "yields $\alpha=0.65\pm0.01$"]
- result: Mean f_CII (fraction of gas traced by [C II]) = 0.32 ± 16 (as printed) dimensionless [5.4.3 C+ thermal saturation: "we obtain a mean $f_\mathrm{[CII]}=0.32\pm16$"]
- result: Source-plane X-ray luminosity if all XMM flux is from a northern-clump AGN = ~2e44 ± not stated erg/s [5.4.2 AGN effects: "we find a source-plane X-ray luminosity $L_\mathrm{0.5-8.0~keV}\simeq2\times10^{44}$ erg s$^{-1}$ (uncorrected for obscuration)"]
- limitation (authors): CO(3-2) has low S/N and must be interpreted carefully [3.3.3 CO(3-2) emission: "it must be interpreted carefully"]
- limitation (authors): Agreement of the PDR models with line ratios is largely due to large systematic uncertainties on CO(3-2) and CO(10-9) reconstructions [6 Conclusions: "We emphasise that the agreement between the observed line ratios and the simplistic PDR models is largely due to significant systematic uncertainties on the CO(3–2) and CO(10–9) source reconstructions."]
- limitation (authors): Semi-infinite uniform-density slab models are likely too simplistic for a clumpy ISM [5.4.1 Caveats and limitations: "Our semi-infinite, uniform-density slab models (even after adjusting for multi-side illumination) are likely too simplistic"]
- not stated (card): The lens-modelling code itself is not named or stated as public; its regularization form (R_s), the converged lambda_S values and the optimizer settings are not given; Full lens mass model parameters (SIE and shear values) are only referenced to R15a; Flux, bandpass and phase calibrators, and any self-calibration, for the Band 3, Band 8 and LBC data are not given; CASA tasks and parameters used f…

### 2019ApJ...876..112R: Strong Far-ultraviolet Fields Drive the [C II]/Far-infrared Deficit in z ∼ 3 Dusty, Star-forming Galaxies (2019; high_z_galaxies, star_formation; observational_alma_primary)
- question: What drives the resolved [CII]/FIR deficit in two z~3 SMGs, and how do [CII] and 160-um continuum sizes compare to CO(3-2)?
- step 1: Image continuum and [CII] cubes
  - method: Calibrate with ALMA pipeline, subtract continuum, image with multi-scale WSClean natural weighting [3.1.1 Imaging: "We perform synthesis imaging of the visibility data using the Ws-Clean algorithm introduced by (cite: Offringa2014), specifically its multi-scale version (cite: Offringa2017)."]
  - software: CASA, WSClean
  - parameter: 5 mas pixels, 1024x1024, auto-mask SNR 2 [3.1.1 Imaging: "We use the automatic SNR-based masking, with `auto-mask` SNR threshold of 2."]
  - validation: CO(3-2) re-imaged identically; changes <=10% in rms and luminosity [3.1.1 Imaging: "these result in minor ($\leq$10%) changes in the rms noise and the inferred CO(3–2) luminosity"]
- step 2: Measure source sizes by uv-plane fitting
  - method: Fit radially binned visibilities with 1 Gaussian, 2 Gaussians, or Gaussian+constant; F-test for model selection [3.2 uv-plane analysis: "we compare the two models using the F-test (cite: Bevington1969)."]
  - parameter: uv-bin size varied 5 to 50 klambda [3.2 uv-plane analysis: "we vary the $uv$-bin size from 5 to 50 k$\lambda$."]
  - assumption: circularly symmetric Gaussian profile [3.2 uv-plane analysis: "we assume the surface brightness distribution to follow a circularly symmetric Gaussian profile."]
  - fitting: least-squares visibility fits; two-component preferred at p>0.95 for [CII] in 49.1 and continuum in 57.1 [3.2 uv-plane analysis: "The two-component model is strongly ($p>0.95$) preferred for the \[C II\] emission in ALESS 49.1 and the continuum emission in ALESS 57.1."]
  - validation: Mock ALMA observations: 1000 noise realizations per injected source [3.2.1 Robustness: "generating 1000 datasets with different noise realizations for each source"]
- step 3: Kinematic modelling of [CII]
  - method: 3D rotating exponential disc model fit to cubes [3.3: "We model the velocity-fields using the GalPak3D software (cite: Bouche2015)."]
  - software: GalPak3D
  - parameter: 25 mas pixel cubes, natural weighting [3.3: "we re-sampled our data onto cubes with a pixel size of 25 mas, using natural weighting"]
  - assumption: exponential disc (Sersic n=1) [3.3: "we assume an exponential disc profile"]
  - fitting: Monte-Carlo approach (GalPak3D) [3.3: "GalPak3D uses a Monte-Carlo approach to extract the kinematic and morphological parameters"]
  - validation: inclinations agree with CO(3-2) values within 1-2 sigma [3.3: "agree with those derived from CO(3–2) imaging by (cite: CR18) within 1–2$\sigma$ uncertainty"]
- step 5: Resolved [CII]/FIR vs Sigma_SFR
  - method: Bin maps into 1-beam pixels (SNR>=2), SFR from SED fits linearly mapped to 160-um; compare with Smith 2017 and fit power law [4.3: "binning the \[C II\] and 160-$\mu$m continuum maps (Fig. 1) into pixels 1 beamwidth large; only pixels for which both the \[C II\] and 160-$\mu$m continuum have SNR$\geq$2 are considered."]
  - assumption: linear mapping 160-um to SFR; no AGN contribution; universal IMF [4.3: "(1) a linear mapping between the rest-frame 160-$\mu$m emission and SFR; (2) no AGN contribution to the rest-frame FIR luminosity; (3) universal IMF"]
  - fitting: power-law fit gives slope -0.53±0.12 [4.5.1: "we obtain a best-fitting slope of $\gamma = -0.53\pm0.12$"]
  - validation: compared with thermal-saturation slope -0.5 [4.5.1: "This is in agreement with the thermal-saturation model slope of $\gamma = -0.5$"]
- step 6: PDR modelling for G0, n, T_PDR
  - method: Compare [CII]/CO(3-2) and [CII]/FIR in central R<=2 kpc with PDRToolbox models [4.4: "We now use our resolved \[C II\]/CO(3–2)/FIR observations to infer the $G_0$ and $n$ using the PDR models from the PDRToolbox library"]
  - software: PDRToolbox
  - parameter: f_[CII]^PDR=0.8; factor 2 correction for optically thin [CII] [4.4: "we adopt a conservative (i.e., low) estimate of $f_\mathrm{[CII]}^\mathrm{PDR} = 0.8$."]
  - assumption: CO(3-2) optically thick, FIR continuum thin; [CII] optically thin adopted [4.4: "we adopt the values derived for the optically-thin \]C II\] for the rest of this paper."]
  - fitting: contour fits in G0-n space [4.4: "Figure 9 shows the contours in the $G_0$/$n$ space"]
- result: Compact [CII] half-light radius ALESS 49.1 = 1.01 ± 0.12 kpc [3.2: "have half-light radii of 1.01$\pm$0.12 kpc and 8.7$\pm$1.6 kpc, respectively"]
- result: Extended [CII] half-light radius ALESS 49.1 = 8.7 ± 1.6 kpc [3.2: "have half-light radii of 1.01$\pm$0.12 kpc and 8.7$\pm$1.6 kpc, respectively"]
- result: [CII] size ratio relative to CO(3-2), ALESS 49.1 / 57.1 = 2.0 / 3.9 ± 0.4 / 0.7 dimensionless [4.1.2: "the \[C II\] emission is $2.0\pm0.4$ (ALESS 49.1) and $3.9\pm0.7$ (ALESS 57.1) times more compact than CO(3–2)"]
- result: Resolved [CII]/FIR vs Sigma_SFR slope = -0.53 ± 0.12 dimensionless [4.5.1: "we obtain a best-fitting slope of $\gamma = -0.53\pm0.12$"]
- result: log G0 (optically thin), ALESS 49.1 = 4.1 ± +0.3/-0.3 dimensionless [Table 2: "| $\log G_0$ | | $4.1^{+0.3}_{-0.3}$ | $4.2^{+0.9}_{-0.4}$ |"]
- result: log n(H) (optically thin), ALESS 49.1 = 4.7 ± +0.4/-0.2 cm^-3 [Table 2: "| $\log n$(H) | \[cm$^{-3}]$ | $4.7^{+0.4}_{-0.2}$ | $4.1^{+0.5}_{-0.4}$ |"]
- result: T_PDR (optically thin), ALESS 49.1 / 57.1 = 720 / 670 ± 200 / 170 K [Table 2: "| $T_\mathrm{PDR}$ | \[K\] | $720\pm200$ | $670\pm170$ |"]
- result: Dynamical mass within 2 kpc, ALESS 49.1 = 6.2e10 ± 5.5e10 Msun [4.2: "$M_{dyn}$ ($R\leq$2 kpc) = $(6.2\pm5.5)\times10^{10}$ and $(2.7\pm1.6)\times10^{10}$ M$\odot$"]
- result: [CII]/FIR radial slope alpha ALESS 49.1 = 0.41 ± 0.06 dimensionless [4.3: "($\alpha = 0.41\pm0.06$)"]
- limitation (authors): Only two galaxies; extended [CII] likely resolved out [Conclusions: "With only two galaxies in our sample, it is difficult to generalize our conclusions to the entire population of submillimeter galaxies."]
- not stated (card): WSClean version and multi-scale scale list, channel-dependent threshold values, niter; Which channels are line-free and the exact flagged channels; Self-calibration or flux calibrator not given; uv-fit software, uv-bin choice for final results, and fitting priors/likelihood; GalPak3D configuration, priors and run settings; SED-to-FIR luminosity conversion and L_FIR definition for resolved maps; P…

### 2025A&A...696A..88W: JWST + ALMA ubiquitously discover companion systems within ≲18 kpc around four z ≍ 3.5 luminous radio-loud AGN (2025; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Are there companion systems (mergers, gas clouds) within ~18 kpc of four z~3.5 radio galaxies, found jointly from JWST/NIRSpec IFU [O III] kinematics and ALMA Band 8 [C II]?
- step 3: Image the ALMA Band 8 cubes and continuum
  - method: CASA tclean cubes with two [C II] spws cleaned together, no uv continuum subtraction, primary-beam correction, smoothing to 14 km/s; continuum maps from individual spws [2.3 ALMA Band 8: "The task `tclean` was used to clean the cube down to a $2\sigma$ level."] [2.3 ALMA Band 8: "together without continuum subtraction in the $uv-$plane."]
  - software: CASA, tclean
  - parameter: robust = +0.5 for J0121 and 4C19; robust = +2.0 for J0205 and 4C03 [Table 1: "Robust = +0.5 Briggs weighting was applied for TN J0121+1320 and 4C+19.71 and robust = +2.0 Briggs weighting was applied for TN J0205+2242 and 4C+03.24."]
  - parameter: 14 km/s channels [2.3 ALMA Band 8: "The final cubes were smoothed to $14,\rm km,s^{-1}$ per channel."]
- step 5: Identify and fit [O III] companions
  - method: Visually inspect [O III]5007 channel maps for kinematically distinct blobs, then fit r=0.1 arcsec aperture spectra with q3dfit (all bright lines fitted together with tied Gaussian components) and map velocities spaxel-by-spaxel in [O III] … [3.1 Warm ionized gas kinematics: "Specifically, we visually inspect the"] [3.1 Warm ionized gas kinematics: "The fitting is done simultaneously for all bright emission lines covered"]
  - software: q3dfit
  - parameter: Aperture radius 0.1 arcsec [3.1 Warm ionized gas kinematics: "by fitting $r=0.1\ensuremath{''}$ aperture-extracted spectra"]
  - parameter: Number of components chosen by q3dfit up to a user-set maximum [3.1 Warm ionized gas kinematics: "The optimized number of components are determined by `q3dfit`, with a maximum allowed number as input."]
  - assumption: Doublet ratios fixed by atomic physics ([O III] and [N II] = 3; [S II] ratio limited to 0.4375-1.4484; [O II] doublet ratio = 1) [3.1 Warm ionized gas kinematics: "The flux ratios of doublets are set according to atomic physics"]
  - fitting: q3dfit multi-Gaussian fit with kinematically tied lines; sampler, priors and likelihood not stated [3.1 Warm ionized gas kinematics: "while keeping the Gaussian components for different lines kinematically tied (cite: Vayner_2023Q3D; Wang_2024)"]
  - validation: Companion spectra compared with the same fit at the central AGN position [3.1 Warm ionized gas kinematics: "For comparison, we also fit the spectra at central AGN positions through the same procedure"]
- step 6: Detect and fit [C II] emitters in ALMA cubes
  - method: Make moment 0 maps from channels with emission, extract 1D spectra in apertures (1x major beam for J0121 and 4C19; 2x for J0205 and 4C03), fit one Gaussian per spectrum [3.2 [C II] emitters: "moment 0 maps constructed from velocity channels where emission is detected"] [3.2 [C II] emitters: "For the field of TN J0121+1320 and 4C+19.71, we use apertures with the size of the major synthesized beam."]
  - software: CASA
  - parameter: Detection at >~3 sigma; apertures 1x or 2x the major beam [3.2 [C II] emitters: "we increase the aperture to twice the size of major synthesized beam to increase the S/N"]
  - assumption: Lines detected in Band 8 are [C II] at redshifts similar to the central HzRGs [3.2 [C II] emitters: "we assume the lines detected by ALMA Band 8 are"]
  - fitting: Single Gaussian per 1D spectrum; fitting code not stated [3.2 [C II] emitters: "We perform line fitting to the 1D spectra with one Gaussian component"]
  - validation: Comparison with [O III] counterpart at the same position and with dust continuum [3.2 [C II] emitters: "To compare the warm and cold ionized gas at the position of"]
- step 7: Fit disk kinematics of the two bright [C II] companions
  - method: 3DBarolo tilted-ring fits to J0121-[C II]-B and 4C19-[C II] on cubes smoothed to 28 km/s, with NORM=AZIM and fixed centres; 4C19 fitted in two steps (all free parameters, then geometry fixed) [3.2 [C II] emitters: "we also conduct spatial fitting using $^{\rm 3D}$BAROLO"] [3D BAROLO fit of [C II]: "We set `NORM=AZIM` so that the observed moment-0 map is azimuthally averaged to obtain"]
  - software: 3DBarolo
  - parameter: J0121-B: initial PA = 193 deg, i = 60 deg, varied by +/-15 deg; best fit PA = 187 deg, i = 61 deg [3D BAROLO fit of [C II]: "The initial values of $PA$ and $i$ are set to 193$^{\circ}$ and 60$^{\circ}$."] [3D BAROLO fit of [C II]: "$PA$ and $i$ are 187$^{\circ}$ and 61$^{\circ}$, respectively"]
  - parameter: 4C19: initial PA = 100 deg, i = 10 deg, varied by +/-15 and +/-30 deg; best fit PA = 93 deg, i = 30 deg [3D BAROLO fit of [C II]: "The initial values of $PA$ and $i$ are 100$^{\circ}$ and 10$^{\circ}$."] [3D BAROLO fit of [C II]: "$PA$ and $i$ are 93$^{\circ}$ and 30$^{\circ}$, respectively"]
  - parameter: Ring separation half the beam major axis; centre fixed to initial guess [3D BAROLO fit of [C II]: "The separation between rings is set to half the width of beam major axis by default."] [3D BAROLO fit of [C II]: "The center coordinates ($x_{0}$, $y_{0}$) are fixed to the initial guess."]
  - fitting: Free parameters v_sys, PA, i, v_rot, sigma_v minimised by 3DBarolo (cost function not stated) [3D BAROLO fit of [C II]: "Initial value of other parameters are guessed by $^{\rm 3D}$BAROLO."]
  - validation: Residual moment 2 and position-velocity diagrams inspected; inclination of 4C19 flagged as resolution-limited [3D BAROLO fit of [C II]: "We note that the $i$ fit of 4C19-\[C ii\] is limited by angular resolution and should be treated with caution."]
- step 8: Estimate dynamical masses of companions
  - method: Dispersion-dominated M_dyn = K(n)K(q) sigma_v^2 r_e / G; rotation M_dyn = k r v_rot^2 / G, with csc^2 i left free for [O III] companions [5.1 Companion kinematics and masses: "Under this assumption, we estimate $M_{\rm dyn}$ following (cite: ubler_2023)"] [5.1 Companion kinematics and masses: "For J0121-\[C ii\]-B and 4C19-\[C ii\], we obtain $r$ and $v_{\rm rot}$ from $^{\rm 3D}$BAROLO"]
  - software: 3DBarolo
  - parameter: n = 1, q = 1, k = 1.8; r_e set to PSF or major beam (2 theta for J0205-[C II] and 4C03-[C II]); R = 0.11 arcsec PSF for unresolved [O III] blobs [5.1 Companion kinematics and masses: "For simplicity, we take $q=1$."] [5.1 Companion kinematics and masses: "We take $k=1.8$ (cite: deGraaff_2024)."]
  - assumption: Gravitational interaction with the central AGN ignored; masses from unresolved sizes are upper limits (dispersion) or lower limits (rotation R) [5.1 Companion kinematics and masses: "we ignore gravitational interactions between the companion and the central AGN"] [5.1 Companion kinematics and masses: "We stress that this mass estimate should be treated as an upper limit, as the size is overestimated."]
- step 9: Check ionisation mechanism of [O III] companions
  - method: Build [O III]/H-beta vs [N II]/H-alpha and [S II]/H-alpha diagrams from the 1D fits and classify against Kewley et al. empirical lines [5.2 Nature of [O III] companions: "We use both the \[O iii\]/H$\beta$-\[N ii\]/H$\alpha$ and \[O iii\]/H$\beta$-\[S ii\]/H$\alpha$ diagnostics."]
  - software: q3dfit
  - parameter: Extinction correction with Halpha/Hbeta = 3.1 [5.2 Nature of [O III] companions: "by adopting the canonical value of $F_{\rm H\alpha}/F_{\rm H\beta}=3.1$"]
  - assumption: Case B recombination [5.2 Nature of [O III] companions: "assuming Case B recombination (cite: Veilleux_1987; Osterbrock_2006)"]
- step 10: Zeroth-order stellar mass of J0121-[C II]-B
  - method: Overlay a Bagpipes single starburst spectrum on the aperture-extracted optical continuum and read off the consistent stellar mass; derive a 3 sigma limit from the 8 sigma continuum detection [4.1.2 Results of companion search: "We find that this continuum level could be consistent with a galaxy with $M_{\star}=10^{9.9}\,M_{\odot}$."] [5.1 Companion kinematics and masses: "we find that the continuum of J0121-\[C ii\]-B is detected at $\sim8\sigma$"]
  - software: Bagpipes
  - parameter: Solar metallicity, A_V = 1.5 mag from Balmer decrement, Calzetti law [4.1.2 Results of companion search: "The extinction is set to $A_{V}=1.5\,$mag based on Balmer decrement and (cite: Calzetti_2000) law."]
  - assumption: Optical continuum flux proportional to stellar mass when deriving the detection limit [5.1 Companion kinematics and masses: "if optical continuum flux is directly proportional to stellar mass"]
  - fitting: Not a fit: model spectrum overlaid and compared by eye [4.1.2 Results of companion search: "This model spectrum should simply be considered as a zeroth order indication of the stellar mass."]
- result: J0121-[O III] velocity offset and width = Delta v = 434 km/s; sigma_v = 95 ± +/-2 (Delta v from Table); +/-3 (sigma_v) km/s [4.1.2 Results of companion search: "is $434\,\rm km\,s^{-1}$ redshifted from the systemic velocity and has a width $\sigma_{v}=95\pm3\,\rm km\,s^{-1}$"]
- result: J0205-[O III] velocity offset = -1426 ± +/-8 km/s [4.2 Companion search of TN J0205+2242: "has $\Delta v=-1426\,\rm km\,s^{-1}$ with respect to the systemic redshift of"]
- result: J0205-[O III] velocity dispersion = 309 ± +/-7 km/s [4.2 Companion search of TN J0205+2242: "The fitted line width is relatively broad with $\sigma_{v}=309\,\rm km\,s^{-1}$"]
- result: 4C03-[O III] velocity offset = 1395 ± +/-47 km/s [4.3 Companions of 4C+03.24: "precisely, $\Delta v=1395\pm47\,\rm km\,s^{-1}$ using fitting results from Table"]
- result: 4C03-[O III] narrow and broad component dispersions = 55 (narrow); 574 (broad) ± +/-16; +/-5 km/s [4.3 Companions of 4C+03.24: "$\sigma_{v}=55\pm16\,\rm km\,s^{-1}$ and $574\pm5\,\rm km\,s^{-1}$, respectively"]
- result: 4C19-[O III] velocity offset and dispersion = Delta v = -584; sigma_v = 210 ± Table: +/-9 and +/-9 km/s [4.4 Companion search of 4C+19.71: "with $\Delta v=-584\,\rm km\,s^{-1}$ and $\sigma_{v}=210\,\rm km\,s^{-1}$"]
- result: J0121-[C II]-B redshift, offset, dispersion and flux = z = 3.5197; Delta v = 49 km/s; sigma_v = 345 km/s; flux 2.49 Jy km/s ± z +/-0.0003; Delta v +/-19; sigma_v +/-19; flux +/-0.12 km/s; Jy km/s [Table of 1D [C II] fits: "3.5197$\pm$0.0003 | 49$\pm$19 | 345$\pm$19 | 2.49$\pm$0.12"]
- result: 4C19-[C II] redshift, offset, dispersion and flux = z = 3.5881; Delta v = -71 km/s; sigma_v = 256 km/s; flux 1.62 Jy km/s ± z +/-0.0002; Delta v +/-12; sigma_v +/-12; flux +/-0.06 km/s; Jy km/s [Table of 1D [C II] fits: "3.5881$\pm$0.0002 | -71$\pm$12 | 256$\pm$12 | 1.62$\pm$0.06"]
- result: 4C19-[C II] positional accuracy and chance coincidence with the AGN = ~0.019 arcsec; ~5% probability the dust is at the AGN position ± not stated arcsec; percent [4.4 Companion search of 4C+19.71: "there is only a $5\%$ probability that the dust is at the same position as the AGN"]
- result: J0121-[C II]-B 3DBarolo best-fit PA and inclination = PA = 187 deg; i = 61 deg ± not stated degrees [3D BAROLO fit of [C II]: "$PA$ and $i$ are 187$^{\circ}$ and 61$^{\circ}$, respectively"]
- result: 4C19-[C II] 3DBarolo best-fit PA and inclination = PA = 93 deg; i = 30 deg ± not stated degrees [3D BAROLO fit of [C II]: "$PA$ and $i$ are 93$^{\circ}$ and 30$^{\circ}$, respectively"]
- result: J0121-[C II]-B dynamical mass (dispersion; rotation) = 48; 9.0 (x10^10 Msun); d_RG = 6.4 kpc ± not stated 1e10 Msun [Table 2: "(01:21:42.667, +13:20:58.52) | 0.88/6.4 | 48 | 9.0"]
- result: 4C19-[C II] dynamical mass (dispersion; rotation) = 32; 7.0 (x10^10 Msun); d_RG = 0.3 kpc ± not stated 1e10 Msun [Table 2: "(21:44:07.515, +19:29:14.59) | 0.04/0.3 | 32 | 7.0"]
- result: Range of companion dispersion-based dynamical masses = approximately 1e10 to 1e11 Msun (upper limits) ± not stated Msun [5.1 Companion kinematics and masses: "are approximately $10^{10-11}\,M_{\odot}$"]
- result: J0121-[C II]-B stellar mass (zeroth order) = 10^9.9 ± not stated (zeroth order) Msun [4.1.2 Results of companion search: "consistent with a galaxy with $M_{\star}=10^{9.9}\,M_{\odot}$"]
- result: 3 sigma stellar mass detection limit in the NIRSpec cubes = ~10^9.5 ± not stated Msun [5.1 Companion kinematics and masses: "the $3\sigma$ $M_{\star}$ detection limit in the cube is $\sim10^{9.5}\,M_{\odot}$"]
- result: ALMA [C II] cube rms per channel = 3.0, 1.3, 1.1, 1.0 (J0121, J0205, 4C03, 4C19 in text order) ± not stated mJy/beam [2.3 ALMA Band 8: "The rms noise of the \[C ii\] cubes at the systemic redshift are $3.0\,\rm mJy\,beam^{-1}$, $1.3\,\rm mJy\,beam^{-1}$, $1.1\,\rm mJy\,beam^{-1}$, and $1.0\,\rm mJy\,beam^{-1}$ per channel"]
- result: ALMA Band 8 continuum 3 sigma upper limits (two non-detections) = 0.28 and 0.25 ± not stated mJy/beam [2.3 ALMA Band 8: "we report $3\sigma$ upper limits of $0.28\,\rm mJy\,beam^{-1}$ and $0.25\,\rm mJy\,beam^{-1}$"]
- limitation (authors): Companion search is not complete [3 Analysis: "We note that our analysis may not be complete in the sense of detecting all possible companion sources in the fields of the radio galaxies"]
- limitation (authors): Dispersion-based masses are upper limits because sizes of unresolved sources are overestimated [5.1 Companion kinematics and masses: "We stress that this mass estimate should be treated as an upper limit, as the size is overestimated."]
- limitation (authors): [C II] emitters without [O III] or dust counterparts could be other lines at other redshifts [3.2 [C II] emitters: "Without further information, we cannot rule out the possibility that the"]
- not stated (card): Line-free channels or velocity ranges used to build moment-0 maps and continuum; tclean cell size, image size, masking strategy, deconvolver, niter and threshold details; Whether the ALMA calibration used the pipeline or manual scripts, and the pipeline version; Flux calibrator and flux-scale uncertainty for the Band 8 data; Whether 7m or total-power data were used (the paper uses only the C43-5 …

### 2015MNRAS.449.2883G: The nature of the [C II] emission in dusty star-forming galaxies from the SPT survey (2015; high_z_galaxies, milky_way_ism; multi_facility_alma_minor)
- question: What is the nature of [CII] emission in lensed SPT dusty star-forming galaxies, and what ISM conditions explain the [CII]/CO(1-0) and [CII]/FIR ratios?
- step 1: reduce APEX [CII] spectra
  - method: CLASS processing, linear baseline subtraction, regrid to ~90 km/s [2.2 APEX/FLASH: "We subtracted linear baselines from the individual spectra in each of the two FFTS units, and regridded to a velocity resolution of $\sim90$ km s$^{-1}$"]
  - software: CLASS
- step 2: compare CO and [CII] line profiles
  - method: Single/double Gaussian fits, joint fit with one scaling parameter [3.1: "We then simultaneously fit the single or double Gaussian profile (depending on what is necessary to fit the profiles individually) to the CO and [CII] velocity profiles"]
  - parameter: accept if reduced chi2 < 1+5*sqrt(2 n_dof) [3.1: "We accept the single Gaussian fit if the reduced $\chi^2$ does not exceed 1+5$\times \sqrt{2 n_\textrm{dof}}$"]
  - fitting: chi2 Gaussian fits [3.1 Velocity profiles and line fluxes: "We accept the single Gaussian fit if the reduced $\chi^2$ does not exceed 1+5$\times \sqrt{2 n_\textrm{dof}}$, where $n_\textrm{dof}$ is the number of degrees of freedom."]
  - validation: FWHM cross-checked with velocity-weighted moments [3.1: "we also fit the spectra by taking velocity-weighted moments, and find fully consistent results."]
- step 4: constrain excitation temperature and optical depth from [CII]/CO(1-0)
  - method: Source-function model of luminosity ratio compared with observed ratio [5.1.1: "We now generalise this line ratio method by comparing the source functions."]
  - assumption: same filling factors for [CII] and CO [5.1.1 Determining the optical depth of …: "where we have assumed that the \[CII\] and CO emitting gas have the same filling factors"]
  - assumption: Tex,CO(1-0)=Td~35 K [5.1.3: "allows us to fix the $T_{\text{ex,CO(1--0)}}$ = $T_{\text{d}}$ $\simeq35\,$K"]
- step 5: compare with PDR models
  - method: Place sources on [CII]/FIR vs CO/FIR diagnostic diagram with Kaufman99 tracks to estimate G0 and n [5.2.1: "we obtain a rough estimate of the radiation field strength and the gas density of $100<G_0<8000$"]
  - assumption: alpha_CO = 0.8 (and 2) Msun/(K km/s pc2); 70% of [CII] from PDRs [5.2.1 Implications of the photodissocia…: "(cite: hailey-dunsheath10) assume that 70% of the \[CII\] emission originates from PDRs"]
  - validation: PDR sizes compared with lens model radii [5.2.1 Implications of the photodissocia…: "The estimated radii of the PDRs, while fairly uncertain, are comparable to the source sizes determined by the lens models."]
- result: [CII] detections = 17 of 20 ± not stated sources [3 Results: "We have 17 [CII] emission line detections (16 with FLASH and one with *Herschel* SPIRE FTS)"]
- result: L[CII]/L_CO(1-0) = 5200 ± 1800 dimensionless [4.4: "we determine the $L_{\text{[C{\scriptsize II}]}}/L_{\text{CO(1--0)}}$ ratio to be $5200\pm1800$"]
- result: [CII] FWHM range = ~210-820 ± not stated km/s [3.1: "The resulting FWHMs are in the range $\sim210-820\,$km/s."]
- result: G0 range = 100-8000 ± not stated Habing [5.2.1: "$100<G_0<8000$ and $10^{2}\,$cm$^{-3}<n<10^5$ cm$^{-3}$"]
- limitation (authors): PDR sizes and molecular gas sizes are rough/uncertain [5.2.1: "The sizes estimated using this method are quite uncertain"]
- not stated (card): ALMA data reduction, CASA version and imaging settings for CO spectra; Extraction apertures for ALMA CO spectra; ATCA CO(1-0) fluxes (forthcoming paper); Comparison sample table (Gracia-Carpio in prep); SED photometry inputs for L_FIR

### 2020MNRAS.492.3194S: KASHz: No evidence for ionised outflows instantaneously suppressing star formation in moderate luminosity AGN at z ∼ 1.4-2.6 (2020; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Is there a spatial anti-correlation between ionised outflows ([O III]) and star formation (traced by Halpha and rest-frame FIR) in eight z=1.4-2.6 moderate-luminosity AGN, and is Halpha a reliable star-formation tracer in these hosts?
- step 5: Extract IFU spectra and fit emission lines
  - method: Extract spectra in a 5 kpc nuclear aperture and a maximum aperture around the continuum peak; fit [O III], Halpha, [N II] and Hbeta with one or two Gaussians, choosing the second component by BIC [3.1.1 Extracting spectra and emission-l…: "From each data cube we extracted spectra from two different circular apertures centred on the continuum peak: (a) a nuclear aperture within 5 kpc diameter"] [3.1.1 Extracting spectra and emission-l…: "each line was fitted with one or two Gaussian components, with the centroids, FWHM and fluxes (normalisation) as free parameters."]
  - software: lmfit
  - parameter: second Gaussian accepted if Delta BIC > 2; residuals also inspected visually [3.1.1 Extracting spectra and emission-l…: "(using $\Delta$BIC$>2$ as boundary for choosing a more complex model)"]
  - parameter: [O III] 5007/4959 flux ratio fixed at 2.99; [N II] 6583/6548 ratio fixed at 3.06 [3.1.1 Extracting spectra and emission-l…: "We tied the line widths and central velocities of the two lines and fixed the \[O iii\]$\lambda$5007/\[O iii\]$\lambda$4959 flux ratio to be 2.99"] [3.1.1 Extracting spectra and emission-l…: "flux ratio was fixed to be 3.06 (based on the atomic transition probability; (cite: Osterbrock06))"]
  - parameter: sky-line residual wavelengths masked; noise taken as the RMS of the emission-line free region [3.1.1 Extracting spectra and emission-l…: "The noise of the spectra was estimated as the RMS of the emission-line free region in the spectrum."]
  - assumption: Halpha and [N II] come from the same gas (tied velocity and width) [3.1.1 Extracting spectra and emission-l…: "This approach, which assumes that the H$\alpha$ and \[N ii\] emission comes from the same gas, is commonly used in high-redshift observations to limit the number of free parameters"]
  - fitting: Least-squares fit with lmfit; Monte Carlo errors from 500 noise realisations [3.1.1 Extracting spectra and emission-l…: "Best-fit solutions, and the uncertainties, for the free parameters were obtained using the Python `lmfit` least-square library."] [3.1.1 Extracting spectra and emission-l…: "We repeated this 500 times to build a distribution of all free parameters."]
  - validation: Monte Carlo errors consistent with lmfit errors [3.1.1 Extracting spectra and emission-l…: "are consistent with the errors estimated by the `lmfit`"]
- step 7: Map narrow Halpha and the [O III] outflow
  - method: Spaxel-by-spaxel line fitting on spectra binned over 0.2 arcsec for Halpha; for [O III] a narrow-band image of the blue-shifted outflow velocity slice, because a second component could not be fitted per spaxel [3.1.3 Emission-line maps: "We binned the spectra by averaging the nearby spaxels within radius of 0.2 arcsec."] [3.1.3 Emission-line maps: "we employed a different method to map the outflow for these 5 targets by creating a narrow-band image in the spectral region of the outflow."]
  - software: lmfit
  - parameter: final maps re-binned to 0.1 arcsec [3.1.3 Emission-line maps: "The final maps were re-binned to 0.1 arcsec."]
  - parameter: outflow slice limit set at 2 x FWHM from the outflow component centre in the integrated spectrum [3.1.3 Emission-line maps: "The blueward limit of the outflow velocity slice was defined from the galaxy integrated spectra, as 2$\times$ FWHM from the centre of the outflow component."]
  - parameter: Type 1 BLR component fixed in velocity and width to the nuclear-spectrum values, only flux free [3.1.3 Emission-line maps: "we fixed the central velocity and line-width of the BLR component to be the same as that obtained from the nuclear spectrum"]
  - fitting: Same procedure as the integrated spectra [3.1.3 Emission-line maps: "We fitted the \[O iii\] and H$\alpha$ emission lines in the binned spatial spaxels using the same overall procedure as described in"]
  - validation: Results not sensitive to the exact outflow velocity-slice definition [3.1.3 Emission-line maps: "are not sensitive to the exact definition of the velocity slice for the outflow"]
- step 11: Compare outflow location with Halpha and FIR star formation, and re-analyse ID6
  - method: Overlay the [O III] outflow peak (brightest pixel) on Halpha maps and FIR contours, look for cavities and offsets; for ID6 repeat the analysis on the H-band and the earlier HK-band cube and compare with rest-frame U-band HST emission [4.4 Star formation and AGN driven outfl…: "we found the center of the outflow as a location of the brightest pixel in the outflow map"] [4.4.1 No clear evidence of feedback in …: "Therefore, we repeated our analyses on the $HK$ grating data"]
  - assumption: Offsets between outflow and FIR may reflect differential dust obscuration of [O III] [4.4 Star formation and AGN driven outfl…: "However, this could just be due to differential obscuration by the dust"]
  - validation: ID6 cavity in Halpha only appears with the original Cresci et al. HK data cube; the three non-outflow targets show no different star-formation morphology [4.4.1 No clear evidence of feedback in …: "We find that it is only when we use the same fully-reduced $HK$ data cube as that used by (cite: Cresci15) that we are able to observe a cavity in H$\alpha$ at the location of the outflow"] [4.4 Star formation and AGN driven outfl…: "we do not see any systematic different star formation morphologies compared to those with detected AGN-outflow"]
- result: Number of targets with an [O III] outflow = 5 of 8 ± not stated dimensionless [4.4 Star formation and AGN driven outfl…: "We detected ionised gas outflows in five out of the eight objects in our sample"]
- result: Broad [O III] component FWHM for the five outflow targets = 500-950 ± not stated km s^-1 [4.1 Overview of the emission-line prope…: "These latter five targets have second, broad components with FWHM$=$ 500–950 km s$^{-1}$"]
- result: Offset between outflow peak and FIR peak (ID1, ID4, ID6), median over sample = 1.7-6.4 for the three sources; median 2.3 ± +2.6/-1.3 (on the median) kpc [4.4 Star formation and AGN driven outfl…: "in three sources (ID1, ID4 and ID6) we see a significant offsets of 1.7–6.4 kpc between the outflows and the FIR emission (with a median value of 2.3$^{+2.6}_{-1.3}$ kpc across the full sample)"]
- limitation (authors): Sample limited to sources with existing FIR and Halpha detections, so all lie on or above the star-forming main sequence [4.5 Implications of our results: "it is limited to sources with existing detections in FIR and H$\alpha$ emission, resulting in all of the sources lying on, or above, the ‘main sequence’ of star formation"]
- limitation (authors): Effects of outflows could occur below the resolution of the data (a few kpc) or on long timescales [4.5 Implications of our results: "However, impact from these outflows could be occurring on spatial scales below those to which we are sensitive (i.e., $<$a few kiloparsec)"]
- limitation (authors): ID2 FIR flux may be partly synchrotron contaminated [2.4 SED fitting and sample properties: "some contamination to the ALMA flux for this single source does not influence our main conclusions in this work"]
- not stated (card): Width (uv-taper FWHM) of the Gaussian taper used for each IFU-matched ALMA map; tclean parameters: niter, threshold, cell size, image size, mask definition, deconvolver, number of channels or spectral windows used for the continuum; Which spectral windows and bandwidth went into each continuum image, and any line-free channel selection; ALMA array configurations, observing dates and flux calibrat…

### 2024A&A...686A..46E: AGN feedback in the Local Universe: Multiphase outflow of the Seyfert galaxy NGC 5506 (2024; nearby_galaxies, agn_and_quasars; multi_facility_alma_minor)
- question: How do the molecular (ALMA CO(3-2)) and ionised ([OIII], GTC/MEGARA) outflow phases of the Seyfert galaxy NGC 5506 compare, and how do they couple to the disc?
- step 3: Fit MEGARA lines with Gaussians
  - method: Spaxel-by-spaxel ALUCINE fit with 1 or 2 Gaussians, AoN>3; broad = outflow, narrow = rotation [5.1 Gaussian decomposition: "The ALUCINE code determines, based on the AoN $>3$ cut, whether one or two Gaussians are necessary for each spaxel."]
  - software: ALUCINE
  - parameter: vsys input 1893 km/s for [OIII] [5.1 Gaussian decomposition: "we achieved better results by setting $v_{sys, \text{[OIII]}}=1893$ km s$^{-1}$"]
  - validation: Residual maps (Appendix) [Goodness of ALUCINE fit: "See Fig. [21](#fig:residuals)."]
- step 4: Non-parametric [OIII] velocities
  - method: Percentile velocities (v02..v98, W80, Δv) from sum of two Gaussians per spaxel [5.2 Non-parametric [OIII] velocities: "For every spaxel we calculate the velocities corresponding to different percentiles to the flux contained in the modelled line profile"]
- step 5: Ionised outflow mass and rate
  - method: logU from Baron & Netzer 2019 line-ratio relation -> n_e; extinction-corrected broad [OIII] luminosity; M = mu m_H L/(gamma n_e); Mdot = M v/R [5.3 The [OIII] outflow mass: "Finally, the ionised outflow mass $M_{\rm out}^{\rm ion}$ is given by (cite: rose18; baron19):"]
  - parameter: Cardelli extinction law, R_V=3.1; intrinsic Ha/Hb=3.1; mu=1.4; central pixel r = half pixel size [5.3 The [OIII] outflow mass: "we assume an intrinsic ratio $H \alpha / H \beta = 3.1$, and we use the (cite: cardelli89) extinction law ($R_V = 3.1$)"]
  - assumption: Broad component is outflow; n_H ~ n_e [5.3 The [OIII] outflow mass: "we consider the flux of the broad component as the outflow (whereas the narrow component is associated to the ordered gas rotation)"]
  - validation: Compared logU, n_e, L[OIII] with Davies et al. 2020 X-shooter values [5.3 The [OIII] outflow mass: "We recover a median value of $\log U = -2.9$, in agreement with the integrated value of $-2.87 \pm 0.12$ found by (cite: davies20)"]
- result: Median logU of broad [OIII] = -2.9 ± not stated dimensionless [5.3 The [OIII] outflow mass: "We recover a median value of $\log U = -2.9$"]
- result: Max electron density = 8.5e5 ± not stated cm-3 [5.3 The [OIII] outflow mass: "The maximum $n_{e, \text{max}} = 8.5 \times 10^5$ cm$^{-3}$ is exactly at the AGN position."]
- result: Ionised outflow mass = 9.8e4 ± not stated Msun [5.3 The [OIII] outflow mass: "We calculated a total ionised outflowing mass of $M_{\rm out}^{\rm ion} = 9.8 \times 10^4$ M$_{\odot}$."]
- result: Ionised outflow velocity (R=525 pc) = 422 ± 97 km/s [5.4 The ionised mass outflow rate: "we find $v_{\rm out}^{\rm ion} = 422 \pm 97$ km s$^{-1}$"]
- result: Ionised mass outflow rate = 0.076 ± 0.017 Msun/yr [5.4 The ionised mass outflow rate: "$\dot{M}_{\rm out}^{\rm ion} = 0.076 \pm 0.017$ M$_{\odot}$ yr$^{-1}$"]
- result: Max W80 = 826 ± not stated km/s [5.2 Non-parametric [OIII] velocities: "The maximum value observed is $W_{80, max} = 826$ km s$^{-1}$ located $\sim 6 \ensuremath{''}$ W."]
- limitation (authors): Molecular outflow quantities are upper limits due to possible bar [6.1 The case for elliptical motions due…: "we cannot rule out the potential existence of a bar within the central kiloparsec."]
- limitation (authors): Inflow within 0.4" not confirmable (only two radial points) [4.2 Rotating disc with a radial velocit…: "but since we only have two radial points we could not confirm this finding"]
- not stated (card): ALMA calibration, pipeline/CASA versions, imaging parameters (robust, channel width, rms) of the datacube (in García-Burillo+2021); Observing dates, configurations, and time on source for ALMA; 3DBarolo settings: mask/threshold, normalisation type, fitting function, version; Which CO moment/flux integration and region used for M_out; how CO(3-2) flux converted to mass numerically; ALUCINE setting…

### 2017ApJ...836....8T: ALMA Observations Show Major Mergers Among the Host Galaxies of Fast-growing, High-redshift Supermassive Black Holes (2017; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Are major mergers important drivers of rapid early SMBH growth, as tested with ALMA continuum and [C II] observations of six z≃4.8 quasar hosts, three FIR-bright and three FIR-faint?
- step 1: Image continuum and [C II] cubes
  - method: Observatory scripts for visibilities, then CLEAN with Briggs robust 0.5; continuum from two upper windows; uv continuum subtraction for [C II] from the lower two [2.2.2 Data Reduction and Spectral Measu…: "[C II ] emission line images were constructed by subtracting the continuum emission from the other two, lower frequency spectral windows, in the UV space"]
  - software: CASA
  - parameter: robust = 0.5 [2.2.2 Data Reduction and Spectral Measu…: "with robustness parameter set to 0.5"]
  - validation: Checked for no residual continuum in line images [2.2.2 Data Reduction and Spectral Measu…: "We verified that the resulting [C II ] emission line images have no residual continuum signal in them."]
- step 4: Dynamical, dust and gas masses
  - method: M_dyn = 9.8e8 (D_[CII]/kpc)(FWHM/100 km/s)^2 / sin^2(i) Msun, with cos(i) = a_min/a_maj; dust mass from optically thin dust; gas mass via gas-to-dust 100 [3.3.2 Host and companion galaxy masses: "Rough estimates of gas masses can then be inferred by assuming a (uniform) gas-to-dust ratio of 100."]
  - assumption: Inclined rotating disk, v_circ = 0.75 FWHM/sin i; Td=47 K, beta=1.6; gas-to-dust 100 [3.3.2 Host and companion galaxy masses: "in which the circular velocity is given by v circ = 0.75 × FWHM / sin ( i )."]
  - validation: Caveats discussed; no independent check [3.3.2 Host and companion galaxy masses: "Such dynamical mass estimates carry significant uncertainties due to the different assumptions required to derive them"]
- step 5: Compare with SF main sequence and BH-host relations; assess mergers
  - method: Compare SFR vs M_dyn with the main-sequence relation; BH growth rate from L_bol with eta=0.1; compare M_BH/M_dyn with local ellipticals; identify companions via continuum and [C II] redshift [3.3.3 SMBH-host galaxy relations: "the radiative efficiency is assumed to be η = 0.1."]
  - software: MATLAB package for astronomy and astrophysics
  - assumption: Host mass grows only via star formation at CE01-based SFR [3.3.3 SMBH-host galaxy relations: "we assume that the mass grows only due to the formation of new stars at a rate determined by the CE01-based SFRs"]
  - validation: Chance-coincidence estimates from deep-survey number counts [3.1 Source detection and identification: "cannot be attributed to chance coincidence"]
- result: Dust masses of quasar hosts = (0.4-4.8)e8 ± not stated Msun [3.3.2 Host and companion galaxy masses: "The dust masses we derive are in the range M dust ∼ (0.4 − 4.8) × 10 8 M ⊙ for the quasar hosts"]
- result: Inclination-corrected M_dyn of quasar hosts = (3.7-7.5)e10 ± not stated Msun [3.3.2 Host and companion galaxy masses: "we obtain dynamical masses of M dyn ≃ (3.7 − 7.5) × 10 10 M ⊙ for the quasar hosts"]
- result: M_BH/M_dyn = 1/260 to 1/10 ± not stated dimensionless [3.3.3 SMBH-host galaxy relations: "which are in the range M BH /M dyn ∼ 1/260 − 1/10"]
- limitation (authors): M_dyn is uncertain: extended emission missed, inclination from marginally resolved sizes, beam smearing [3.3.2 Host and companion galaxy masses: "our ALMA data may not be able to detect the more extended lower surface brightness [C II ]-emitting regions, thus underestimating D [C II ]"]
- limitation (authors): Small sample limits interpretation [3.4 Major mergers among hosts of fast-g…: "The small size of our sample naturally limits the scope of our interpretation"]
- not stated (card): CLEAN parameters: deconvolver, threshold, masks, iterations, image size; Line-free channels and exact spectral windows used for continuum subtraction; Flux calibrator and flux scale uncertainty; Whether pipeline or manual calibration scripts were used and which pipeline version; Aperture and fitting details for the 2D Gaussian fits; How inclinations were bounded for unresolved sources; Primary be…

### 2021ApJ...909..204F: [C II] and CO Emission along the Bar and Counter-arms of NGC 7479 (2021; nearby_galaxies, agn_and_quasars; archival_reuse)
- question: Origin, distribution, and kinematics of CO and [C II] emission along the bar and counter-arms of NGC 7479.
- step 1: Prepare the [C II] comparison cube
  - method: Reduce with the FIFI-LS pipeline, correct atmospheric transmission with ATRAN, and project reduced data into a spectral cube. [SOFIA Observations: "The data were reduced using the FIFI-LS pipeline (cite: 2020ASPC..Vacca)."] [SOFIA Observations: "the data were corrected for atmospheric transmission using the ATRAN model (cite: 1992nstc.rept.....L)"]
  - software: FIFI-LS pipeline, ATRAN
  - parameter: 3″ sampling; Gaussian spectral dispersion 1/4 spectral resolution; Gaussian spatial dispersion 1/2 spatial resolution [SOFIA Observations: "with a fine grid of 3$''$ sampling using a Gaussian spectral kernel with a dispersion equal to 1/4 of the spectral resolution"] [SOFIA Observations: "a Gaussian spatial kernel with a dispersion equal to 1/2 the spatial resolution."]
  - parameter: Spatial resolution 15.6 arcseconds; resolving power 1167; unresolved FWHM 257 km s^-1 [SOFIA Observations: "The spectral resolving power of FIFI-LS is 1167, meaning that an unresolved line has a FWHM of 257 km s$^{-1}$."] [SOFIA Observations: "The spatial resolution of the instrument is 15.6 arcseconds"]
  - validation: Projection parameters conserve instrumental spatial and spectral resolutions. [SOFIA Observations: "These parameters produced a data cube that conserves the instrumental spectral and spatial resolutions."]
- step 3: Measure matched-resolution aperture photometry
  - method: Define 12 apertures, degrade images and the CO cube to [C II] resolution, and measure multiband flux densities. [Origin And Distribution of Gas Emission: "we defined 12 different apertures with a diameter of 15.6 arcseconds, equivalent to the spatial resolution of our \[C II\] map."] [Origin And Distribution of Gas Emission: "To compare the emission at these bands with the \[C II\] emission, we degraded the spatial resolution of each image to that of the \[C II\] spectral cube."]
  - parameter: Circular 15.6″ diameter apertures; centers in Table 2 [Table 2: "Each region consists of a circular aperture with a 15.6$''$ diameter and the reported center."]
  - parameter: Centers on far-IR peaks or 20 cm continuum regions [Origin And Distribution of Gas Emission: "Each aperture covers a different part of the bar and is centered either on a peak of the far-IR emission, or on a region with 20 cm radio continuum emission."]
  - parameter: Two GALEX, five SDSS, four IRAC bands; MIPS 24 μm; PACS 70, 100, 160 μm; SPIRE 250 μm [Origin And Distribution of Gas Emission: "we measured the flux densities in the two GALEX bands, five SDSS bands, four IRAC bands, the MIPS 24 $\mu$m image, the PACS 70, 100, and 160 $\mu$m images and the SPIRE 250 $\mu$m image."]
- step 5: Measure aperture line luminosities
  - method: Fit aperture [C II] and CO profiles with pseudo-Voigt functions and derive line luminosities. [Origin And Distribution of Gas Emission: "the middle panel shows the \[C II\] line from the apertures fitted with one or two pseudo-Voigt functions (red lines)."] [Origin And Distribution of Gas Emission: "The right panel, finally, shows the CO lines fitted again with a combination of pseudo-Voigt functions."]
  - parameter: [C II]: one or two pseudo-Voigt functions; CO: combination of pseudo-Voigt functions [Origin And Distribution of Gas Emission: "the middle panel shows the \[C II\] line from the apertures fitted with one or two pseudo-Voigt functions (red lines)."] [Origin And Distribution of Gas Emission: "The right panel, finally, shows the CO lines fitted again with a combination of pseudo-Voigt functions."]
  - fitting: Pseudo-Voigt profile fitting; optimizer, likelihood, bounds, and component-selection criterion not stated. [Origin And Distribution of Gas Emission: "The right panel, finally, shows the CO lines fitted again with a combination of pseudo-Voigt functions."]
  - validation: Compare profiles with rescaled Hα profiles. [Origin And Distribution of Gas Emission: "The profile of the H$\alpha$ line, rescaled to the \[C II\] and CO lines, is shown with a green shade."]
- step 6: Diagnose gas-heating mechanisms
  - method: Compare [C II], CO, FIR, and PAH diagnostics with PDR models and galaxy samples. [Relative Strength of CO and \[C II\] Em…: "shows the relationship between the \[C II\] and CO emission in the different apertures, normalized to the far-IR emission."] [Relative Strength of CO and \[C II\] Em…: "We show, for reference, a grid of PDR models from (cite: Kaufman1999)."]
  - parameter: [C II]/FIR comparison with GOALS [Infrared Diagnostics: "we compare the values of the \[C II\]/FIR ratios in the different apertures on NGC 7479 with values from the GOALS sample."]
  - assumption: FIR and 7.7 μm PAH emission are star-formation diagnostics [Infrared Diagnostics: "The far-IR emission (between 8 and 1000 $\mu$m) has been shown to be a good estimator of star formation (cite: Kennicutt1998)."] [Infrared Diagnostics: "Another quantity that correlates very well with the star formation rate is the emission at 7.7 $\mu$m from the polycyclic aromatic hydrocarbons (cite: Peters2004)."]
  - validation: Check multiple infrared diagnostics; note possible dilution between the two [C II] components in E. [Infrared Diagnostics: "the corresponding region E (at the tip of the northern jet) does not seem to have anomalous ratios in these two diagnostics."] [Infrared Diagnostics: "any excess in this ratio in one component may be diluted by normal PDR emission from the other."]
- result: Region C [C II] luminosity = 6.30 ± ± 0.98 10^6 L_sun [Table 2: "| C | 23:04:56.48 +12:20:03.6 | 0.90 | 6.30 $\pm$ 0.98 | 0.75 $\pm$ 0.03 |"]
- result: Region C CO luminosity = 0.75 ± ± 0.03 10^3 L_sun [Table 2: "| C | 23:04:56.48 +12:20:03.6 | 0.90 | 6.30 $\pm$ 0.98 | 0.75 $\pm$ 0.03 |"]
- result: Region E [C II] luminosity = 3.64 ± ± 0.80 10^6 L_sun [Table 2: "| E | 23:04:55.82 +12:19:48.7 | 0.63 | 3.64 $\pm$ 0.80 | 0.44 $\pm$ 0.02 |"]
- result: Region E CO luminosity = 0.44 ± ± 0.02 10^3 L_sun [Table 2: "| E | 23:04:55.82 +12:19:48.7 | 0.63 | 3.64 $\pm$ 0.80 | 0.44 $\pm$ 0.02 |"]
- result: Region I [C II] luminosity = 6.99 ± ± 0.08 10^6 L_sun [Table 2: "| I | 23:04:57.34 +12:18:57.9 | 0.79 | 6.99 $\pm$ 0.08 | 0.51 $\pm$ 0.01 |"]
- result: Region I CO luminosity = 0.51 ± ± 0.01 10^3 L_sun [Table 2: "| I | 23:04:57.34 +12:18:57.9 | 0.79 | 6.99 $\pm$ 0.08 | 0.51 $\pm$ 0.01 |"]
- result: Region K [C II] luminosity = 3.88 ± ± 0.38 10^6 L_sun [Table 2: "| K | 23:04:55.19 +12:18:57.7 | 0.48 | 3.88 $\pm$ 0.38 | 0.25 $\pm$ 0.01 |"]
- result: Region K CO luminosity = 0.25 ± ± 0.01 10^3 L_sun [Table 2: "| K | 23:04:55.19 +12:18:57.7 | 0.48 | 3.88 $\pm$ 0.38 | 0.25 $\pm$ 0.01 |"]
- limitation (authors): FIFI-LS spectral resolution cannot clearly separate all [C II] components. [Merging Remnants: "Unfortunately, the spectral resolution of FIFI-LS is not good enough to clearly separate the two components."]
- limitation (authors): Normal PDR emission may dilute an excess in one velocity component of region E. [Infrared Diagnostics: "any excess in this ratio in one component may be diluted by normal PDR emission from the other."]
- not stated (card): ALMA calibration provenance, software versions, flagging, calibrators, and absolute flux uncertainty.; ALMA imaging task, weighting and robust value, deconvolution settings, masks, stopping threshold, pixel size, and image dimensions.; ALMA continuum subtraction, line-free channels, primary-beam treatment, and measured cube rms.; ALMA spatial-frequency coverage and treatment of potentially missin…

### 2018ApJ...853..111J: First Results from the Herschel and ALMA Spectroscopic Surveys of the SMC: The Relationship between [C II]-bright Gas and CO-bright Gas at Low Metallicity (2018; nearby_galaxies, milky_way_ism, star_formation; multi_facility_alma_minor)
- question: How does [C II]-bright molecular gas relate to CO-bright gas at low metallicity in the SMC, and what does this imply for the CO-to-H2 conversion factor?
- step 4: Remove ionized and atomic gas contributions to [C II]
  - method: Ionized from [N II] 205um and Halpha EM; atomic from HI with WNM/CNM assumptions (50/50) [4.2. I[C II] Contribution from Atomic G…: "We assume that 50% of NHi associated with the CO emission is associated with the CNM and the other 50% with the WNM"]
  - parameter: Te = 8000 K; CNM n=100 cm-3, T=40 K; WNM n=1 cm-3, T=8000 K [4.1. I[C II] Contribution from Ionized …: "We assume Te = 8000 K, appropriate for Galactic H ii regions"]
  - validation: Halpha estimate consistent with [N II]-based upper limit on ne [4.1. I_[C II] Contribution from Ionized…: "consistent with the upper limit on _n_ e determined from the [N ii] 122 _µ_ m/205 _µ_ m values (see Section 3.2)."]
- step 5: Convert remaining [C II] to NH2
  - method: Method 1: fixed T=90 K, n=4000 cm-3; Method 2: PDR Toolbox with SMC models gives n and G0, then SMC [C II] cooling rates [4.3. Converting I[C II] to NH2: "Using PDR models tuned to the SMC conditions (see Appendix A) to estimate n and the FUV radiation field intensity"]
  - software: PDR Toolbox
  - assumption: Carbon abundance (C/H)SMC = 2.8e-5 [4. ESTIMATING H2 USING [C II] AND 12CO: "We assume a carbon abundance ((C _/_ H) SMC ) that is the Milky Way abundance scaled by the metallicity of the SMC"]
  - fitting: Nearest model grid match to [C II], [O I], TIR per pixel [4.3.2. Method 2: PDR Model: "We use the [C ii], [O i], and total-infrared (TIR) intensity images as inputs to determine the nearest volume density and FUV radiation field strength in the model grids"]
  - validation: Two methods agree within factor ~1.5 [4.5. NH2 Estimates: "Table 6 shows that average column densities and total H2 masses for both methods are different by at most a factor of ∼ 1.5."]
- step 6: Convert CO to NH2 and combine; derive XCO and molecular-to-atomic ratio
  - method: Galactic XCO = 2e20 for CO (2-1 assumed thermalized to 1-0); total NH2 = [C II]-traced + CO-traced; XCO vs AV compared with models [4.4. Converting ICO to NH2: "we use a Galactic CO-to-H2 conversion factor XCO = 2 × 1020 cm−2 (K km−1 s−1)−1"]
  - fitting: Linear fits of NH2 vs ICO [Figure 19 caption: "The thick dashed colored lines show the linear fits to the data"]
  - validation: Uncertainty budget (quadrature ~50%, adopt factor 2); compared to Wolfire 2010 and Glover & Mac Low 2011 [4.5.1. Estimating Uncertainties: "we choose to adopt an uncertainty of a factor of ∼ 2 for the mass of H2."]
- result: Ionized-gas fraction of [C II] from [N II] = at most 5% ± not stated percent [3.2. [N ii] and Contribution from Ioniz…: "suggests that the contribution of ionized gas to [C ii] is at most 5%."]
- result: Fraction of molecular gas traced by [C II] = ~70% on average ± not stated percent [5.3. Comparing [C ii]-bright and CO-bri…: "with ∼ 70% of the molecular gas coming from [C ii]-bright regions on average."]
- result: Average XCO in regions = ~5 XCO,MW ± factor ~2 in NH2 dimensionless [5.4. The CO-to-H2 Conversion Factor in …: "The values we find for our regions have on average a conversion factor of XCO ∼ 5 XCO,MW."]
- result: Peak NH2/NHI = ~1.5; CO detected out to ~0.5 ± not stated dimensionless [5.5. 12CO and the Molecular to Atomic T…: "we observe peak molecularto-atomic ratios of NH2/NHi ∼ 1.5"]
- result: Total systematic uncertainty on [C II]-based H2 = ~±50% (adopted factor ~2) ± not stated percent [4.5.1. Estimating Uncertainties: "produces a total uncertainty estimate of ∼±50%."]
- limitation (authors): XCO from 13CO is highly uncertain (LTE, abundance ratios, beam dilution) [3.6. Estimating XCO Using 13CO: "we caution the reader that there is a large degree of uncertainty on this estimate."]
- limitation (authors): AV estimate smoothed at ~40" and biased low by single dust temperature [3.8. 12CO-to-[C ii] Ratio: "A high dust temperature results in underestimating τ160 and AV."]
- not stated (card): Line-free channels / velocity ranges used for integrated intensity and RMS; Cell size and image size for ACA cubes; Exact clean threshold in Jy and mask definitions; Flux calibrator and ACA flux scale uncertainty; Wolfire et al. (2017) cooling curves are unpublished; Details of AV regridding and pixel-matching procedure; Integration velocity ranges for 12CO/13CO maps (partly in Table 5)

### 2023MNRAS.519.2030H: The molecular gas kinematics in the host galaxy of non-repeating FRB 180924B (2023; transients, high_z_galaxies; archival_reuse)
- question: What is the molecular gas kinematic structure in the host galaxy of the non-repeating FRB 180924B, and how does it compare to the gas environments of repeating FRB host galaxies?
- step 1: Image CO(3-2) data cube and generate moment maps
  - method: Image calibrated visibility data using CASA tclean with Briggs robust=2.0 at ~9 km s^-1 resolution, convert to rest-frame using z=0.3214 and CO(3-2) rest frequency 345.796 GHz, and create moment 0 and moment 1 maps in CARTA [Observation and Data analysis: "The data cube is obtained with the `CASA` task `tclean()` by setting the robust parameter of $2.0$ for Briggs weighting with a velocity resolution of $\sim$9 km s$^{-1}$."] [Observation and Data analysis: "The velocity-integrated intensity (moment 0) map and the velocity structure (moment 1) map are obtained by Cube Analysis and Rendering Tool for Astronomy (CARTA) (cite: Comrie2021)."]
  - software: CASA, tclean, CARTA
  - parameter: robust = 2.0, velocity resolution ~9 km s^-1 [Observation and Data analysis: "The data cube is obtained with the `CASA` task `tclean()` by setting the robust parameter of $2.0$ for Briggs weighting with a velocity resolution of $\sim$9 km s$^{-1}$."]
  - parameter: moment 0 integration range ~ -180 km s^-1 to ~ 110 km s^-1 [CO emission line detection: "Figure [1](#fig.1) (left) shows the velocity-integrated intensity map with the integration range of $\sim -180$ km s$^{-1}$ to $\sim 110$ km s$^{-1}$."]
  - parameter: moment 1 detection threshold > 4 sigma [Asymmetric CO spectrum: "Furthermore, figure [4](#fig.4) shows the velocity field of the region with CO (3-2) emission-line detection higher than $4 \sigma$."]
  - assumption: Spectroscopic redshift z = 0.3214, CO(3-2) rest frequency = 345.796 GHz [Observation and Data analysis: "The observed frequency of the data cube is converted to the rest-frame frequency using the spectroscopic redshift of $z=0.3214$ (cite: Bannister2019)."] [Observation and Data analysis: "The Doppler velocity is calculated using the rest-frame frequency of the CO (3-2) emission line, i.e., 345.796 GHz."]
- result: CO(3-2) velocity gradient range = -180 to 8 ± not stated km s^-1 [Abstract: "The CO (3-2) velocity map also indicates an asymmetric velocity gradient from $-180$ km s$^{-1}$ to 8 km s$^{-1}$."]
- limitation (authors): HI and H2 gas do not necessarily trace each other or share physical association, so comparing molecular gas (CO) kinematics in the non-repeating FRB host with atomic gas (HI) kinematics in repeating FRB hosts is not strictly direct. [Discussion and conclusion: "However, we note that the HI and H$_{\rm 2}$ gas do not necessarily trace each other or are not necessarily physically associated."]
- limitation (authors): A_flux for the FRB 180924B host (1.05 +/- 0.16) lies on the boundary of the asymmetry definition because kinetic information can be lost during the flux integration process. [Asymmetric CO spectrum: "A$_{\rm flux}$ of the host galaxy of FRB 180924B is on the boundary of the asymmetry, whereas A$_{\rm peak}$ indicates the clear asymmetric kinematics."]
- limitation (authors): Observations of molecular gas in FRB host galaxies are still limited to a very small sample. [Discussion and conclusion: "However, the observation of molecular gas in FRB host galaxies is still limited. Therefore, more observations are essential to understand the relationship between the gas kinematics and FRB progenitor."]
- not stated (card): Whether continuum subtraction (e.g., uvcontsub) was performed prior to imaging the CO(3-2) line cube; Image cell size, image size, cleaning threshold, and masking strategy in CASA tclean; Cosmological parameters (H0, Omega_m, Omega_Lambda) used to calculate luminosity distance D_L and physical scale (kpc/arcsec); Exact rms noise level of the 9 km s^-1 channel cube and the integrated intensity maps

### 2025PASJ...77..432U: ADF22-WEB: A giant barred spiral starburst galaxy in the z = 3.1 SSA22 protocluster core (2025; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: How did the giant, rapidly rotating, barred spiral starburst ADF22.A1 (z=3.1, SSA22 proto-cluster core, obscured AGN) form its disk, bar and bulge, and how do its angular momentum and SMBH-bulge mass ratio compare with local galaxies?
- step 1: Image ALMA and JVLA data and reduce JWST NIRCam
  - method: ALMA data reduced in CASA (6.5.0 or 6.1.0) and imaged with tclean per project; JVLA calibrated with the CASA VLA pipeline and imaged with tclean; NIRCam reduced with the JWST pipeline 1.8.4 following the CEERS recipe [ALMA observations: "Data reduction was performed using version 6.5.0. of the Common Astronomy Software Applications (CASA) package."] [JWST NIRCam imaging: "Data reduction was performed using the JWST calibration pipeline (v.1.8.4), following the recipe provided by the CEERS team (cite: 2023ApJ...946L..12B)."]
  - software: CASA, tclean, JWST calibration pipeline
  - parameter: [CII] high-res: Briggs robust = 0.5 [ALMA observations: "After continuum subtraction the data were mapped with the tclean task, adopting Briggs weighting (robust = 0.5)."]
  - parameter: [CII] low-res: natural weighting with uvtaper = 0.75 arcsec [ALMA observations: "Imaging used the the tclean task adopting natural weighting and uvtaper=0.75$^{\prime\prime}$, to trace extended emission"]
  - parameter: NIRCam: snowball removal, wisp subtraction, 1/f noise subtraction; PSFs matched to F444W [JWST NIRCam imaging: "We applied “snowball” removal, wisp subtraction and “1/f” noise subtraction in addition to the standard reduction."] [JWST NIRCam imaging: "The point spread function (PSF) of each image was matched to that of the F444W image."]
- step 4: Fit Sersic profiles to stellar, dust and [CII] emission
  - method: galfit Sersic fit to F444W; Sersic fit to the 0.2 arcsec 870 um map (5 sigma peaks masked); Sersic fit to the [CII] moment-0 map extracted with 3DBarolo (no bright-emission mask) [Profile Fit: "We performed Sérsic profile fitting using the F444W image using galfit"] [Profile Fit: "We fit a Sérsic profile without a bright emission mask and obtained $r_{\rm e, [CII]}=7.6\pm0.2$ kpc and Sérsic index $n=0.4\pm0.1$."]
  - software: galfit, 3DBarolo
  - parameter: 3DBarolo search: SNRCUT=4.5, GROWTHCUT=4.5, MINCHANNELS=3 on a cube with 40 km/s bins [Profile Fit: "The genuine emission was identified with the search task with SNRCUT=4.5, GROWTHCUT=4.5, and MINCHANNELS=3."]
  - parameter: 870 um fit masked 5 sigma peaks [Profile Fit: "We masked $5\sigma$ peaks as presented in (cite: 2019ApJ...876..130H)"]
  - assumption: F444W (rest-frame ~1 um) taken as a tracer of stellar mass distribution [Profile Fit: "which is expected to be sensitive to stellar mass distribution."]
  - fitting: Sersic profile fits (galfit); sampler and priors not stated [Profile Fit: "The best-fit model and residula images are shown in Fig."]
  - validation: Residual images inspected; models leave residuals from core, clumps and spiral arms [Profile Fit: "We note that the models still leave residuals, which demonstrate the power of high-resolution images at the 0.2$^{\prime\prime}$ resolution."]
- step 5: Model [CII] kinematics and derive rotation curve
  - method: 3DBarolo rotating-disk fits to the 0.2 arcsec cube (40 km/s bins, Hanning smoothed) and to a 0.9 arcsec smoothed cube with parameters fixed to the high-res medians; spacepar used to constrain velocity dispersion; arctangent model fitted to… [Kinematic modeling: "The $^{\rm 3D}$barolo package was utilized to model the"] [Kinematic modeling: "We fit the rotation curve based on the 0.9$^{\prime\prime}$ cube with an arctangent model:"]
  - software: 3DBarolo
  - parameter: Free: kinematic centre, PA, inclination, Vsys, Vrot, sigma; scale height fixed to 300 pc [Kinematic modeling: "were free-parameters. The scale-height of the disc was fixed to be 300 pc"]
  - parameter: Ring width 0.097 arcsec (0.2 arcsec cube) and 0.35 arcsec (0.9 arcsec cube) [Kinematic modeling: "We adopted a ring width of $0.097^{\prime\prime}$, which is half of the resolution element"] [Kinematic modeling: "We adopt a ring width of 0.$^{\prime\prime}$35, which is 40% of the resolution element"]
  - parameter: spacepar grid: Vrot 1-700 km/s, sigma 1-100 km/s, steps of 2 km/s [Kinematic modeling: "The explored parameter space is a range of $V_{\rm rot}$ from 1 to 700 km s$^{-1}$ and $\sigma$ from 1 to 100 km s$^{-1}$, respectively."] [Kinematic modeling: "Steps are 2 km s$^{-1}$ for each."]
  - assumption: Rotation velocity approximately equals circular velocity (rotation supported, Vrot/sigma=8.8) [Kinematic modeling: "Based on this result, we assume that the rotation velocity is approximated equal to the circular velocity."]
  - assumption: Non-axisymmetric gas distribution handled by renormalising flux per spatial pixel to the observed intensity map [Kinematic modeling: "a disk model with non-axisymmetric gas distributions was studied by renormalizing the flux density of each spatial pixel to the observed intensity map."]
  - fitting: 3DBarolo disk fit; arctangent rotation curve v(r) = (2/pi) v_inf arctan(r/r_t); optimiser and priors not stated [Kinematic modeling: "The best fit model is also shown in Fig."]
  - validation: PV diagrams of model vs observed; velocity dispersion checked with a 20 km/s-bin cube giving a similar range [Kinematic modeling: "This test resulted in a similar $\sigma$ range, which support the validity of the measurement with the original cube."] [Kinematic modeling: "In this case, the model generally reproduces the observed emission."]
- step 7: Derive molecular gas mass, gas fraction and Toomre Q
  - method: CO(1-0) flux from JVLA image with casa imfit converted to L'CO and gas mass with alpha_CO = 2.5; Toomre Q = sigma kappa / (pi G Sigma_gas) evaluated at r_e,[CII] using [CII] kinematics [Molecular gas mass and Toomre-Q paramter: "The total line flux measured using the casa/imfit task was ($0.20\pm0.03$) Jy km s$^{-1}$"] [Molecular gas mass and Toomre-Q paramter: "We calculate the Toomre-Q parameter, calculating $\kappa$ at $r_{\rm e, [CII]}$ and averaged molecular gas mass surface density within the radius."]
  - software: CASA imfit
  - parameter: alpha_CO = 2.5 [Molecular gas mass and Toomre-Q paramter: "We adopt $\alpha_{\rm CO}\simeq2.5$ as a representative value"]
  - parameter: kappa = sqrt(2) Vrot / r [Molecular gas mass and Toomre-Q paramter: "we approximate it as $\kappa=\sqrt{2}V_{\rm rot}/r$"]
  - assumption: CO(1-0) profile same as [CII]; CO is not well resolved by JVLA [Molecular gas mass and Toomre-Q paramter: "The CO(1–0) emission is not well resolved with JVLA"]
- step 9: Identify bar and test AGN outflow contribution
  - method: Offset ridges and dusty core identified in the 1.1 mm map and confirmed in the 630 um map; bar length from elliptical apertures around the ridges; two PV diagrams along the ridges and residual [CII] velocity map after 3DBarolo model subtra… [a bar traced in dust continuum: "The bar length is roughly estimated as the major axis of elliptical apertures which encompass the offset ridges delineated with 1.1 mm dust continuum"] [a bar traced in gas kinematics: "To further diagnose the origin of the non-circular motion, we derive two PV-diagrams along the offset-ridges"]
  - software: 3DBarolo
  - parameter: Dusty core profile fit on 0.04 arcsec resolution image [a bar traced in dust continuum: "Profile fit for the dusty core in the high angular resolution image (0.04$^{\prime\prime}$) shows"]
  - validation: Same structure seen in the 630 um map [a bar traced in dust continuum: "The same structure is present in the 630 $\mu$m map, demonstrating that these structures are securely detected."]
- result: F444W effective radius = 7.0 ± 0.1 kpc [Profile Fit: "This best-fit model has an effective radius $r_{\rm e, F444w}=7.0\pm0.1$ kpc and Sérsic index $n=1.7\pm0.1$."]
- result: F444W Sersic index = 1.7 ± 0.1 dimensionless [Profile Fit: "This best-fit model has an effective radius $r_{\rm e, F444w}=7.0\pm0.1$ kpc and Sérsic index $n=1.7\pm0.1$."]
- result: 870 um effective radius = 4.7 ± 0.1 kpc [Profile Fit: "which yielded the best-fit model with an effective radius $r_{\rm e, 870}=4.7\pm0.1$ kpc and Sérsic index $n=0.9\pm0.1$."]
- result: [CII] effective radius = 7.6 ± 0.2 kpc [Profile Fit: "We fit a Sérsic profile without a bright emission mask and obtained $r_{\rm e, [CII]}=7.6\pm0.2$ kpc and Sérsic index $n=0.4\pm0.1$."]
- result: [CII] moment-0 peak flux = 1.95 ± 0.07 Jy beam^-1 km s^-1 [Profile Fit: "peak flux is $1.95\pm0.07$ Jy beam$^{-1}$ km s$^{-1}$"]
- result: Median inclination = 73 ± 4 (typical error) deg [Kinematic modeling: "The median value is $i=73$ deg."]
- result: Median position angle = 92 ± 5 deg [Kinematic modeling: "(a median value PA=92 deg with errors of 5 deg)"]
- result: Representative velocity dispersion = 60 ± not stated km/s [Kinematic modeling: "We conservatively adopt a representative $\sigma=60$ km s$^{-1}$."]
- result: Arctangent fit asymptotic velocity = 540 ± not stated km/s [Kinematic modeling: "with $v_{\infty}=540$ km s$^{-1}$ and ${r_t}=0.52$ kpc."]
- result: Arctangent scale radius = 0.52 ± not stated kpc [Kinematic modeling: "with $v_{\infty}=540$ km s$^{-1}$ and ${r_t}=0.52$ kpc."]
- result: Rotation velocity at r = 2 r_e = 530 ± 10 km/s [abstract: "ADF22.A1 is a giant spiral galaxy with the kinematics of a rotating disk with rotation velocity $V_{\rm rot}=530\pm10$ km s$^{-1}$ and diameter $>30$ kpc."]
- result: Vrot / sigma = 8.8 ± 1.5 dimensionless [Kinematic modeling: "the ratio between the rotation velocity and velocity dispersion is $V_{\rm rot}/\sigma=8.8\pm1.5$."]
- result: CO(1-0) line flux = 0.20 ± 0.03 Jy km s^-1 [Molecular gas mass and Toomre-Q paramter: "The total line flux measured using the casa/imfit task was ($0.20\pm0.03$) Jy km s$^{-1}$, which corresponds to a line luminosity $L^{\prime}_{\rm CO(1-0)}=(8.1\pm1.4)\times10^{10}$ K km s$^{-1}$ pc$^2$."]
- result: CO(1-0) line luminosity L' = 8.1e10 ± 1.4e10 K km s^-1 pc^2 [Molecular gas mass and Toomre-Q paramter: "which corresponds to a line luminosity $L^{\prime}_{\rm CO(1-0)}=(8.1\pm1.4)\times10^{10}$ K km s$^{-1}$ pc$^2$."]
- result: Molecular gas mass (alpha_CO=2.5) = 2.0e11 ± 0.4e11 Msun [Molecular gas mass and Toomre-Q paramter: "This gives the molecular gas mass $M_{\rm gas}=(\alpha_{\rm CO}/2.5)\times(2.0\pm0.4)\times10^{11}$ M$_\odot$."]
- result: Gas mass fraction = 0.45 ± 0.10 dimensionless [Molecular gas mass and Toomre-Q paramter: "gas mass fraction $f_{\rm gas}=M_{\rm gas}/(M_{*}+M_{\rm gas})=0.45\pm0.10$."]
- result: Toomre Q = 0.7 ± 0.2 dimensionless [Molecular gas mass and Toomre-Q paramter: "The calculated $Q=0.7\pm0.2$ supports a scenario that the gas disk is gravitationally unstable"]
- result: Bar length (radius) = ~3.3 ± not stated kpc [a bar traced in dust continuum: "The estimated bar size is $r\approx3.3$ kpc."]
- result: Dusty core effective radius = 670 ± 30 pc [a bar traced in dust continuum: "shows $r_{\rm e}=670\pm30$ pc and $n=0.6\pm0.1$."]
- result: Dusty core Sersic index = 0.6 ± 0.1 dimensionless [a bar traced in dust continuum: "shows $r_{\rm e}=670\pm30$ pc and $n=0.6\pm0.1$."]
- limitation (authors): Stellar mass profile outside R~8 kpc is extrapolated for lack of sensitivity [Resolved stellar profile and specific s…: "is not sufficient to uncover the stellar mass surface distribution in outer parts due to the lack of sensitivity"]
- limitation (authors): CO(1-0) is not well resolved by the JVLA, so the Toomre Q rests on assumed profile [Molecular gas mass and Toomre-Q paramter: "The CO(1–0) emission is not well resolved with JVLA"]
- limitation (authors): Limited profile sampling prevents fitting a third (bar) component in the stellar profile [Resolved stellar profile and specific s…: "but the limited sampling of the profile prevent us from adding the third component."]
- not stated (card): Whether ALMA data were calibrated with the standard pipeline or manually, flux/bandpass/phase calibrators and any self-calibration for each project; Cell size, image size, niter/threshold, cleaning masks and deconvolver for all tclean runs; primary-beam correction; Continuum-subtraction method (e.g. uvcontsub order) and line-free channel ranges used for the [CII] cube; spectral setup of the Band …

### 2021A&A...646A..26B: A puzzling non-detection of [O III] and [C II] from a z ≈ 7.7 galaxy observed with ALMA (2021; high_z_galaxies; observational_alma_primary)
- question: Characterize the ISM of the z=7.664 Lyman-alpha emitting galaxy z7_GSD_3811 via [O III] 88 um, [C II] 158 um and dust continuum, combined with rest-frame UV data, and compare with other high-redshift galaxies and local galaxies
- step 2: image cubes and continuum, with tapering
  - method: CASA clean with natural weighting; dirty image rms measured first, then cleaning threshold set to 2x rms; several spectral resolutions and tapers [3 ALMA observations and imaging: "Imaging was done using the CASA task `clean`."] [3 ALMA observations and imaging: "For the clean image, we set the cleaning threshold to 2 times the rms measured in the dirty image."]
  - software: CASA clean
  - parameter: natural weighting; tapers up to 0.35'' and 0.5'' ([C II]); spectral resolution from native to ~200 km/s [3 ALMA observations and imaging: "We create image cubes and continuum images using a natural weighting."] [3 ALMA observations and imaging: "We have also created \[C ii\] image cubes with a tapering parameter of $0.5\ensuremath{''}$"]
  - assumption: [C II] emitting region may be 2-3 times larger than the UV component, motivating the 0.5'' taper [3 ALMA observations and imaging: "since recent results indicate that the \[C ii\]-emitting region may be 2 – 3 times larger than the UV component"]
  - validation: Measured rms in dirty images checked against theoretical noise [3 ALMA observations and imaging: "We verify that the measured rms in these images is consistent with the theoretically expected noise level."]
- step 3: search for line emission near the target
  - method: Visual inspection of cubes in velocity slices, then systematic search for pixels above 3x rms within 1'' of the target; moment-0 maps and spectra; imfit integrated SNR for brightest features [4.1 Upper limits for the [O III] and [C…: "In the search for potential signal, we select all pixels above 3 times the image rms within $1\ensuremath{''}$ of the target position."] [4.1 Upper limits for the [O III] and [C…: "we calculate an integrated SNR by fitting a 2D-Gaussian using the CASA task `imfit`"]
  - software: CASA imfit
  - parameter: Search range -2000 to 700 km/s ([O III]) and -2900 to 1300 km/s ([C II]) relative to expected line position [4.1 Upper limits for the [O III] and [C…: "For the \[O iii\] line, we search for line emission between $\approx -2000 \text{ to } 700 \ \mathrm{km \ s^{-1}}$ relative to the expected position of the line"]
  - parameter: 5 sigma desired for a firm detection; marginal features also examined [4.1 Upper limits for the [O III] and [C…: "Ideally, in order to claim a firm detection, we would want a signal at the $5\sigma$ level."]
  - fitting: 2D Gaussian fit with imfit for brightest candidate features [4.1 Upper limits for the [O III] and [C…: "we calculate an integrated SNR by fitting a 2D-Gaussian using the CASA task `imfit`"]
  - validation: Features rejected for large spatial/velocity offsets and because negative pixels of equal significance exist; pixel noise Gaussianity checked [4.1 Upper limits for the [O III] and [C…: "In most of our collapsed maps, we are also able to find collections of negative pixels at the same significance as the positive ones"]
- step 4: derive 3 sigma upper limits on [O III] and [C II] line luminosities
  - method: Integrated rms measured in images collapsed over 100 and 400 km/s around expected line positions; 3 sigma used as upper limit assuming unresolved source [4.1 Upper limits for the [O III] and [C…: "we thus calculate the integrated rms in a collapse of $\Delta v = 100$ and $400 \ \mathrm{km \ s^{-1}}$ around the expected positions of the lines given the source redshift"] [3 ALMA observations and imaging: "We adopted a 3$\sigma$ threshold as an upper limit for a non-detection in our analysis."]
  - software: CASA
  - parameter: Fiducial line FWHM 100 km/s, also 400 km/s [4.1 Upper limits for the [O III] and [C…: "Thus, as our fiducial line width for both the \[C ii\] and \[O iii\] line width, we use $100 \ \mathrm{km \ s^{-1}}$."]
  - assumption: Target unresolved with native beams; no continuum subtraction [4.1 Upper limits for the [O III] and [C…: "Assuming that the target is unresolved with the native beam sizes, these fluxes correspond to $3\sigma$ upper limits on the line luminosities"]
  - validation: Variation of integrated rms with assumed line centre is about +/-2% (band 8) and +2%/-4% (band 6) between -500 and 250 km/s [4.1 Upper limits for the [O III] and [C…: "Thus, different assumptions on the line centers should not alter our results significantly."]
- step 6: compare [C II] luminosity and SFR with local and high-z relations
  - method: UV and IR SFRs from Kennicutt & Evans relations; UV+IR SFR with IR 1 sigma limit as upper error bar; compare with Matthee et al. compilation rescaled to 100 km/s and De Looze local relations [4.3 The [C II]-SFR relation: "Using the UV magnitude and the relationship between UV luminosity and SFR by (cite: kennicutt_star_2012)"] [4.3 The [C II]-SFR relation: "we have gone back to the individual publications and re-scaled all the upper limits to the same line-width as z7_GSD_3811"]
  - parameter: T_d = 45 K for SFR_IR; velocity-integrated rms scales as sqrt(line width) [4.3 The [C II]-SFR relation: "by assuming that the velocity-integrated rms scales as the square root of the line width"]
  - assumption: UV magnitude error bars assumed symmetric and equal to the larger error [4.3 The [C II]-SFR relation: "assume that the error bars are symmetric and equal to the larger error presented there"]
  - validation: Comparison repeated for 4x wider line and with 6 sigma upper limits [4.3 The [C II]-SFR relation: "Even if we assume a \[C ii\] line which is 4 times wider, our upper limit still places z7_GSD_3811 below the local relations"]
- step 8: compare L[O III]/L_UV with high-z detections and local dwarfs
  - method: Compute L_UV for literature [O III] detections (with lensing magnification) and compare the L[O III]/L_UV upper limit with high-z objects and local dwarf galaxies versus oxygen abundance [4.5 [O III] and UV luminosity: "While we consider effects of lensing magnification, the lensing errors are not included."] [4.5 [O III] and UV luminosity: "Our $3 \sigma$ upper limit places z7_GSD_3811 at similar $L_{O iii} / L_{\mathrm{UV}}$ ratio as nearby dwarf galaxies that have an oxygen abundance of $\approx 4\%$ to $30\%$ of the solar abundance."]
  - parameter: Solar oxygen abundance 12+log(O/H) = 8.69 [4.5 [O III] and UV luminosity: "where we use $12 \ + \ \mathrm{log_{10}}(n_O/n_H)_{\odot} \ = \ 8.69$ (cite: asplund_chemical_2009)"]
  - validation: Result repeated for a 4x wider line [4.5 [O III] and UV luminosity: "This value does not change significantly in the case that we assume a four times wider line."]
- step 9: SED fitting with ALMA upper limits
  - method: PANHIT SED fit to HST/HAWK-I photometry plus ALMA [O III] and band 6/8 continuum upper limits, constant SFR, Chabrier IMF, GALAXEV stellar models, Calzetti attenuation [5 SED fitting: "we fit the SED using the PANHIT code"] [5 SED fitting: "We assume a Chabrier initial mass function (cite: chabrier_galactic_2003) and a single stellar component."]
  - software: PANHIT
  - parameter: Redshift fixed to 7.664 and escape fraction zero; Z = 0.0001-0.02; A_V = 0-0.5 in steps of 0.05 [5 SED fitting: "In the SED fitting procedure, we fix the redshift to $z=7.664$ and the escape fraction of ionizing photons to zero."] [5 SED fitting: "The metallicity range used for the fitting is $Z = 0.0001$ – $0.02$"]
  - parameter: 7 data points, 4 fitted parameters, 3 degrees of freedom; age restricted to 300 Myr for the alternative solutions [5 SED fitting: "This leaves us with 7 observed data-points and 4 parameters to be fitted, leading to 3 degrees of freedom."] [5 SED fitting: "If we restrict the age of our constant SFR models to 300 Myr"]
  - assumption: Constant SFR; [C II] upper limit not included [5 SED fitting: "we assume the simplified case of a constant SFR"] [5 SED fitting: "We do not include the upper limit on the \[C ii\] line"]
  - fitting: Chi-square minimisation with PANHIT; priors not stated [5 SED fitting: "the best-fitting solution ($\chi_{\nu}^2 \ = \ 3.40$) obtained from PANHIT"]
  - validation: Exponentially increasing SFRs and SMC extinction law tested; fits not essentially different [5 SED fitting: "Note that we have also performed tests with exponentially increasing SFRs, which produce fits that are not essentially different than the ones obtained from a constant SFR model."]
- result: [O III] 88 um and [C II] 158 um 3 sigma luminosity upper limits (100 km/s) = L[OIII] < 1.6e8; L[CII] < 4.0e7 ± not stated Lsun [abstract: "with $3\sigma$ upper limits of $1.6 \ \times \ 10^{8} \ \mathrm{L_{\odot}}$ and $4.0 \ \times \ 10^{7} \ \mathrm{L_{\odot}}$, respectively."]
- result: [O III] 3 sigma luminosity upper limit for 400 km/s line width = < 3.2e8 ± not stated Lsun [4.1 Upper limits for the [O III] and [C…: "$L_{\mathrm{[O iii]}} < 3.2 \ \times \ 10^{8} \ \mathrm{L_{\odot}}$"]
- result: [C II] 3 sigma luminosity upper limit for 400 km/s line width = < 7.5e7 ± not stated Lsun [4.1 Upper limits for the [O III] and [C…: "$L_{\mathrm{[C ii]}} < 7.5 \ \times \ 10^{7} \ \mathrm{L_{\odot}}$"]
- result: Collapsed [O III] image rms (100 and 400 km/s) = 23 and 44 ± not stated mJy km/s/beam [4.1 Upper limits for the [O III] and [C…: "The measured rms in our collapsed \[O iii\] images is $23$ and $44 \ \mathrm{mJy\ km \ s^{-1} \ beam^{-1}}$ for $\Delta v = 100$ and $400 \ \mathrm{km \ s^{-1}}$, respectively."]
- result: Collapsed [C II] image rms (100 and 400 km/s) = 9.8 and 19 ± not stated mJy km/s/beam [4.1 Upper limits for the [O III] and [C…: "For the corresponding \[C ii\] images, we measure an rms of $9.8$ and $19 \ \mathrm{mJy\ km \ s^{-1} \ beam^{-1}}$, respectively."]
- result: UV SFR = 12 (+1/-1) ± +1/-1 Msun/yr [4.3 The [C II]-SFR relation: "we find a UV SFR for z7_GSD_3811 of $\mathrm{SFR_{UV}} \ = \ 12_{-1}^{+1} \ \mathrm{M_{\odot}} \ \mathrm{yr^{-1}}$"]
- result: IR SFR upper limit (1 sigma, T_d = 45 K) = < 4.5 ± not stated Msun/yr [4.3 The [C II]-SFR relation: "we derive an IR SFR of $\mathrm{SFR_{IR}} \ < 4.5 \ \mathrm{M_{\odot}} \ \mathrm{yr^{-1}}$ ($1\sigma$) for a dust temperature of 45 K."]
- result: UV+IR SFR = 12 (+5/-1) ± +5/-1 Msun/yr [4.3 The [C II]-SFR relation: "$\mathrm{SFR_{UV+IR}} \ = \ 12_{-1}^{+5} \ \mathrm{M_{\odot}} \ \mathrm{yr^{-1}}$"]
- result: L[O III]/L_UV upper limit relative to MACS0416_Y1 and SXDF-NB1006-2 = factor ~12 and ~5 lower ± not stated dimensionless [4.5 [O III] and UV luminosity: "is a factor $\sim 12$ and $\sim 5$ times lower than the ratio observed in MACS0416_Y1"]
- result: Mean oxygen abundance of local dwarfs with L[O III]/L_UV lower than the target = ~9% of solar ± not stated fraction of solar [4.5 [O III] and UV luminosity: "The mean oxygen abundance of nearby dwarf galaxies with $L_{O iii} / L_{\mathrm{UV}}$ lower than z7_GSD_3811 is $\approx 9\%$ of the solar value."]
- result: Metallicity upper limit from [C II] vs Vallini et al. 2015 relation (100 km/s) = Z <~ 0.08 Zsun (0.12 Zsun for 400 km/s) ± not stated Zsun [6 Discussion & Summary: "we find that the values we obtain are consistent with a metallicity of $Z\lesssim 0.08 \ \mathrm{Z_{\odot}}$ for a line-width of $\Delta v = 100 \ \mathrm{km \ s^{-1}}$."]
- result: Formal best-fit PANHIT solution (chi2_nu, age, Z) = chi2_nu 3.40, age 0.57 Gyr, Z 0.0004 ± not stated chi2_nu dimensionless; Gyr; Z as mass fraction [5 SED fitting: "Formally, the best-fitting solution ($\chi_{\nu}^2 \ = \ 3.40$) obtained from PANHIT gives a high age of $0.57 \ \mathrm{Gyr}$ and a low metallicity of $Z \ = \ 0.0004$."]
- result: Best-fit PANHIT SFR and stellar mass = SFR 7.95 Msun/yr; M* 3.05e9 Msun ± not stated Msun/yr; Msun [5 SED fitting: "The star formation rate of the model is $\mathrm{SFR} \ = \ 7.95 \ \mathrm{M_{\odot}yr^{-1}}$, with a stellar mass of $M_{\star} \ = \ 3.05 \times 10^{9} \ \mathrm{M_{\odot}}$"]
- result: Alternative solutions for age-limited fits = Young: 2 Myr, Z = 0.0001; two older solutions at 0.29 Gyr with Z = 0.02 and Z = 0.0004 ± not stated Myr, Gyr, Z [5 SED fitting: "Here we find a Young solution (with an age of $2 \ \mathrm{Myr}$) with low metallicity ($Z \ = \ 0.0001$), and two older solutions (with ages of $0.29 \ \mathrm{Gyr}$)"]
- limitation (authors): SFH and age poorly constrained with limited rest-frame optical/UV data [6 Discussion & Summary: "With the limited number of observations in the rest-frame optical and UV, it is difficult to accurately constrain the SFH and age (and therefore also the SFR) of the object."]
- limitation (authors): Upper limit does not exclude higher metallicity [6 Discussion & Summary: "Thus, we emphasize that our upper limit does not exclude the possibility that the object has a higher metallicity"]
- not stated (card): Cell size, image size, niter and clean masks for the cubes and continuum images; Which channels or SPW edges were flagged or excluded in the combined cycle 3 and cycle 5 band 6 data; Exact taper values used for each tapered cube and the exact velocity-binned channel widths; Array type (12 m versus 7 m) and configuration names for each execution block; Primary beam correction treatment for the upp…

### 2016Sci...352.1559I: Detection of an oxygen emission line from a high-redshift galaxy in the reionization epoch (2016; high_z_galaxies; observational_alma_primary)
- question: What are the ISM properties (oxygen abundance, dust, neutral gas) of a z=7.2 Lyman-alpha emitter, probed via [O III] 88 um and [C II] 158 um, and do they allow ionizing photon escape?
- step 1: Calibrate and image ALMA data
  - method: Standard CASA calibration, manual flagging, natural-weighted clean plus uv-tapered [O III] image [Materials and Methods: "we also make a $uv$-tapered image with `outertaper` = $0.''3$ to achieve a good detection"]
  - software: CASA
  - validation: Separate images for three tracks each show ~3 sigma peak [Results: "We find a $\sim 3\sigma$ peak at the position of SXDF-NB1006-2 in every image"]
- step 2: Measure [O III] flux and redshift
  - method: Gaussian fit to spectrum for redshift; imfit Gaussian fit of tapered integrated intensity image, beam-deconvolved [Results: "fitting the tapered integrated intensity image to a Gaussian using a CASA task, `imfit`, and deconvolving the clean beam"]
  - software: CASA imfit
  - parameter: Integrated over -300 to +230 km/s [Results: "integrated over $-300$ to $+230$ km s$^{-1}$"]
  - fitting: Gaussian [Velocity offset between Ly$\alpha$ and …: "First, we have made a fitting with a Gaussian function and obtained the following results: $A=(1.67\pm0.15)\times10^{-18}$ erg s$^{-1}$ cm$^{-2}$ Å$^{-1}$"]
  - validation: Pixel SNR histogram Gaussian below SNR 4 [Results: "is well described by a Gaussian (i.e., normal distribution) at the pixel values below SNR $<4$"]
- step 3: Upper limits on [C II] and continuum; TIR
  - method: 3 sigma limits; TIR from modified blackbody integrated 8–1000 um [Dust continuum: "integrated over the rest-frame wavelengths of 8–1000 $\mu$m"]
  - assumption: T_dust = 40 K, beta = 1.5 [Dust continuum: "the dust temperature and emissivity index are assumed to be $T_{\rm dust}=40$ K and $\beta = 1.5$, respectively"]
- step 4: Lyα velocity offset
  - method: Asymmetric Gaussian fit to Lyα profile vs [O III] systemic redshift, heliocentric correction [Velocity offset between Ly$\alpha$ and …: "We have performed a profile fitting of the Ly$\alpha$ line with an asymmetric Gaussian function"]
  - fitting: Asymmetric Gaussian with sigma fixed at 4.71 A [Velocity offset between Ly$\alpha$ and …: "Next, we have made a fitting with an asymmetric Gaussian function with a fixed $\sigma=4.71$ Å from the Gaussian fit"]
- step 5: SED fitting for physical properties
  - method: chi^2 minimization over PEGASE2 models with nebular lines and Lyα IGM transmission, using 8 constraints including [O III] flux and IR limit [Spectral energy distribution modeling: "This is based on a standard $\chi^2$ minimization method"]
  - software: PEGASE, cloudy
  - parameter: Z grid 0.0004–0.05; T_IGM 0.20–0.45; Rgs = 1 or 2; age lower limit 1 Myr [Spectral energy distribution modeling, …: "$Z=0.0004$, 0.001, 0.002, 0.004, 0.008, 0.02($=Z_\odot)$, or 0.05, $T_{\rm Ly\alpha}^{\rm IGM}=0.20$, 0.30, 0.35, 0.40, or 0.45, and $R_{\rm gs}=1$ or 2."]
  - assumption: Salpeter IMF 0.1–100 Msun, constant SFH, Calzetti law [Stellar continuum: "A constant star formation history is also assumed for simplicity."]
  - fitting: 68.4% ranges via Delta chi2<1 [Spectral energy distribution modeling, …: "The resultant best-fit values and their 68.4% ranges (i.e. $\Delta \chi^2<1$) are summarized in Table S4"]
  - validation: Alternative upper-limit treatments give same best-fit [Spectral energy distribution modeling: "We have tried these two methods and found that the best-fit parameters do not change"]
- result: [O III] 88um line significance = 5.3 ± not stated sigma [main text: "The [O iii] line is detected with a significance of $5.3\sigma$"]
- result: [O III] integrated intensity = 0.45 ± 0.09 Jy km/s [Table S1: "Integrated intensity (Jy km s$^{-1}$) | $0.45 \pm 0.09$"]
- result: [O III] luminosity = 3.8e35 ± 0.8e35 W [Table 1: "$3.8(\pm0.8)\times10^{35}$"]
- result: [O III] redshift = 7.2120 ± 0.0003 dimensionless [Table 1: "Redshift of [O iii] 88 $\mu$m | $7.2120 \pm 0.0003$"]
- result: [C II] flux upper limit = <5.3e-22 ± 3 sigma W m^-2 [Table S1: "$< 5.3 \times 10^{-22}$ $(3\sigma)$"]
- result: Total IR luminosity limit (40 K) = <2.9e37 ± 3 sigma W [Table 1: "$<2.9\times10^{37}$ ($3\sigma$)"]
- result: Lyα velocity offset = +110 ± 30 km/s [Table 1: "$+1.1(\pm0.3)\times10^2$"]
- result: Escape fraction of ionizing photons = 0.54 ± +0.17/-0.54 dimensionless [Table 1: "Escape fraction of ionizing photons | $0.54_{-0.54}^{+0.17}$"]
- result: log stellar mass = 8.54 ± +0.79/-0.22 log Msun [Table 1: "$8.54_{-0.22}^{+0.79}$"]
- limitation (authors): Low SNR; origin of possible high-velocity components uncertain; [C II] marginal features affected by ozone line [Possible kinematics signature: "we can not conclude the origin of the possible high-velocity components because of the limited SNR for the moment"]
- not stated (card): Line-free channels / velocity-axis and channel settings for clean; Exact clean threshold in mJy, image size and cell size; Mask definition for clean; Details of the Monte Carlo Schechter integration; Grid spacing for SFR, age, E(B-V), fesc in SED fit; Aperture/position used for spectrum extraction

### 2024ApJ...972..116I: Merging Gas-rich Galaxies That Harbor Low-luminosity Twin Quasars at z = 6.05: A Promising Progenitor of the Most Luminous Quasars (2024; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the gas content, star formation, dynamics and possible outflows of the host galaxies of a low-luminosity quasar-quasar pair at z = 6.05, and is the pair a progenitor of the most luminous quasars?
- step 1: image the [CII] cube and continuum
  - method: Pipeline-calibrated data re-imaged with CASA tclean (Briggs robust = 2.0); line-free channels give the continuum map; uvcontsub (first-order) removes continuum before the cube; channels averaged to 50 km/s [ALMA Observations: "All images presented in this work were reconstructed using the `tclean` task down to $3\sigma$ level, with Briggs weighting (robust = 2.0) to maximize the point source sensitivity."] [ALMA Observations: "which we subtracted in the $uv$ plane using the task `uvcontsub` with a first-order polynomial function, before making the line cube."]
  - software: CASA, tclean, uvcontsub
  - parameter: robust = 2.0; 50 km/s channels; 3 sigma clean depth [ALMA Observations: "with Briggs weighting (robust = 2.0) to maximize the point source sensitivity"]
- step 2: measure [CII] fluxes, redshifts and line widths in apertures
  - method: Circular apertures (1.5'' diameter for C1, 1.0'' for C2 + Bridge and Tail, 6.0'' for the whole system) on the velocity-integrated map; single Gaussian fits to the spectra for redshift and FWHM [Table 1 notes: "We used 1$''$.5 and 1$''$.0 diameter apertures to extract the emission properties of C1 and the other components, respectively."] [Table 1 notes: "The redshifts were determined from single Gaussian fittings to the \[C II\] spectra"]
  - software: CASA, MIRIAD
  - parameter: aperture diameters 1.5'', 1.0'', 6.0'' [From [CII] emission: "The total \[C II\] line flux measured with a $6''.0$ diameter aperture is 6.6 Jy km s$^{-1}$"]
  - fitting: Single Gaussian to each spectrum; sampler/priors not stated [Table 1 notes: "The redshifts were determined from single Gaussian fittings to the \[C II\] spectra"]
- step 3: derive [CII] luminosity, SFR and molecular gas mass
  - method: L_[CII] from flux via Solomon & Vanden Bout; SFR_[CII] from De Looze 2014 calibration; M_H2 ~ 30 L_[CII] from Zanella 2018 [From [CII] emission: "Following (cite: 2005ARA&A..43..677S), the"] [From [CII] emission: "we can estimate the SFR using the (cite: 2014A&A...568A..62D) calibration based on local H II/starburst galaxies"]
  - parameter: rest frequency 1900.5369 GHz; SFR calibration uncertainty factor of two [From [CII] emission: "$\nu_{\rm rest}$ is the rest frequency of 1900.5369 GHz"] [From [CII] emission: "with a factor of two calibration uncertainty"]
  - assumption: [CII] excited primarily by star formation (SFRs are upper limits if quasar contributes) [From [CII] emission: "By further assuming that the \[C II\] line is excited primarily by star formation"]
  - assumption: Flat LCDM H0 = 70 km/s/Mpc, Omega_M = 0.3, Omega_Lambda = 0.7 [Our target: a pair of quasars at z = 6.…: "with $H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$"]
  - validation: Noted that M_H2 and SFR_[CII] are not independent; compared with other z > 6 quasars [From [CII] emission: "Hence, the \[C II\]-based $M_{\rm H2}$ and SFR$_{\rm [CII]}$ reported here are not necessarily independent."]
- step 5: map global velocity field and estimate dynamical masses
  - method: Moment-1 (and moment-2) maps with immoments and 3.5 sigma clipping; beam-deconvolved imfit sizes give inclination from axis ratio; thin-disk M_dyn with D = 1.5 a_maj and V_circ = 0.75 FWHM/sin i [Global gas dynamics: "generated with the CASA task `immoments` with $3.5\sigma$ clipping to avoid noisy pixels."] [Global gas dynamics: "The disk size is approximated as $D = 1.5 \times a_{\rm maj}$ to account for spatially extended low-level emission, and the circular velocity as $V_{\rm circ} = 0.75 \times {\rm FWHM}_{\rm [CII]}/\sin i$"]
  - software: CASA, immoments, imfit
  - parameter: C1: 0.96'' x 0.68'', i = 45 deg; C2 + Bridge: 0.85'' x 0.35'', i = 66 deg [Global gas dynamics: "$a_{\rm maj} \times a_{\rm min} = (0''.96 \pm 0''.09) \times (0''.68 \pm 0''.07)$ and $i = 45\ensuremath{^\circ}$ for C1"]
  - assumption: [CII] emission arises from thin rotating disks; inclination from deconvolved axis ratio [Global gas dynamics: "Here, the \[C II\] emission of these galaxies is assumed to be mainly originating from thin rotating disks."] [Global gas dynamics: "The inclination angles ($i$) of the disks are determined from the axis ratios of the beam-deconvolved Gaussian fits to the emitting regions."]
  - validation: M_dyn compared with M_H2 (comparable) [Global gas dynamics: "we found that their $M_{\rm dyn}$ are comparable to $M_{\rm H2}$"]
- step 6: test for and quantify a [CII] outflow at C1
  - method: Fit the C1 spectrum (single synthesized beam) with single and double Gaussians (second centroid fixed to first); broad wing treated as outflow; M_out from L_[CII],broad with X_C+, T_ex; outflow rate M_out V_out / R_out; total rate = 3x neu… [Potential indication of AGN feedback: "we next fit the data with a double Gaussian model (Figure [4](#fig4)c) by fixing the centroid of the second Gaussian to that of the first Gaussian"] [Potential indication of AGN feedback: "we obtain a neutral outflow rate of $\dot{M}_{\rm out, neutral} = M_{\rm out}V_{\rm out}/R_{\rm out} = 229 \pm 73~M_\odot$ yr$^{-1}$"]
  - software: CASA
  - parameter: X_C+ = 1.4e-4, T_ex = 200 K, high density limit (n >> n_crit ~ 3e3 cm^-3), R_out = 1.5 kpc, V_out = FWHM/2 [Potential indication of AGN feedback: "we estimated $M_{\rm out} = (5.6 \pm 1.5) \times 10^8~M_\odot$ for $X_{\rm C^+} = 1.4 \times 10^{-4}$ and $T_{\rm ex} = 200$ K"] [Potential indication of AGN feedback: "This gives the characteristic size (spatial extent) of $R_{\rm out} = 1.5$ kpc."]
  - assumption: Wing is due to outflow (symmetric wing disfavors unseen companions); 70% of [CII] from neutral PDRs; constant outflow velocity [Potential indication of AGN feedback: "We assumed that 70% of the \[C II\] emission originates from neutral photodissociation regions (cite: 1997ARA&A..35..179H)."] [Potential indication of AGN feedback: "The nearly symmetric appearance of the broad wing at C1 disfavors nearby (unseen) companions as its physical origin"]
  - fitting: Gaussian (chi-square) fits of single and double Gaussian to the C1 spectrum; sampler and priors not stated [Potential indication of AGN feedback: "We first fit the spectrum with a single Gaussian model"]
  - validation: chi2/d.o.f. 85.5/56 = 1.53 (single) vs 42.7/54 = 0.79 (double) over +/-1500 km/s; double Gaussian statistically preferred [Potential indication of AGN feedback: "the single Gaussian fit returns $\chi^2$/d.o.f. = 85.5/56 = 1.53 whereas the double Gaussian fit returns $\chi^2$/d.o.f. = 42.7/54 = 0.79"]
- result: [CII] redshift of C1 = 6.0561 ± 0.0002 dimensionless [Table 1: "6.0561 $\pm$ 0.0002"]
- result: [CII] FWHM of C1 = 594 ± 20 km/s [Table 1: "$594 \pm 20$"]
- result: [CII] line flux of C1 = 3.67 ± 0.19 Jy km/s [Table 1: "$3.67 \pm 0.19$"]
- result: [CII] line flux, 6.0'' aperture (whole system) = 6.6 ± not stated Jy km/s [From [CII] emission: "is 6.6 Jy km s$^{-1}$, which translates to $L_{\rm [CII]}$, SFR$_{\rm [CII]}$, and $M_{\rm H2}$ of $6.3 \times 10^9~L_\odot$, 550 $M_\odot$ yr$^{-1}$, and $1.9 \times 10^{11}~M_\odot$, respectively."]
- result: L_[CII] total (6.0'' aperture) = 6.3e9 ± not stated L_sun [From [CII] emission: "is 6.6 Jy km s$^{-1}$, which translates to $L_{\rm [CII]}$, SFR$_{\rm [CII]}$, and $M_{\rm H2}$ of $6.3 \times 10^9~L_\odot$, 550 $M_\odot$ yr$^{-1}$, and $1.9 \times 10^{11}~M_\odot$, respectively."]
- result: SFR_[CII] total (6.0'' aperture) = 550 ± factor of two calibration uncertainty M_sun/yr [From [CII] emission: "is 6.6 Jy km s$^{-1}$, which translates to $L_{\rm [CII]}$, SFR$_{\rm [CII]}$, and $M_{\rm H2}$ of $6.3 \times 10^9~L_\odot$, 550 $M_\odot$ yr$^{-1}$, and $1.9 \times 10^{11}~M_\odot$, respectively."]
- result: M_H2 total (6.0'' aperture, [CII]-based) = 1.9e11 ± not stated M_sun [From [CII] emission: "is 6.6 Jy km s$^{-1}$, which translates to $L_{\rm [CII]}$, SFR$_{\rm [CII]}$, and $M_{\rm H2}$ of $6.3 \times 10^9~L_\odot$, 550 $M_\odot$ yr$^{-1}$, and $1.9 \times 10^{11}~M_\odot$, respectively."]
- result: L_[CII] of C1 = 3.5e9 ± 0.18e9 (Table 1) L_sun [From [CII] emission: "The brightest \[C II\] emission originates from C1 ($3.5 \times 10^9~L_\odot$)"]
- result: SFR_[CII] of C1 and C2 + Bridge = 305 (C1); 75 (C2 + Bridge) ± 16 (C1); 11 (C2 + Bridge) M_sun/yr [From [CII] emission: "we find SFR$_{\rm [CII]} = 305 \pm 16~M_\odot$ yr$^{-1}$ in C1 and $75 \pm 11~M_\odot$ yr$^{-1}$ in C2 + Bridge"]
- result: M_H2 of C1, C2 + Bridge, Tail = ~10, ~2.6, ~1.5 (x1e10) ± not stated M_sun [From [CII] emission: "we found $M_{\rm H2} \sim 10, 2.6, 1.5 \times 10^{10}~M_\odot$ in the regions of C1, C2 + Bridge, and Tail, respectively"]
- result: Dynamical mass of C1 and C2 = ~9e10 (C1); ~5e10 (C2) ± not stated M_sun [Global gas dynamics: "we estimate that $M_{\rm dyn} \sim 9 \times 10^{10}~M_\odot$ for C1, and $\sim 5 \times 10^{10}~M_\odot$ for C2, respectively."]
- result: Broad-wing Gaussian FWHM at C1 = 1194 ± 193 km/s [Potential indication of AGN feedback: "the broad wing component has (peak amplitude, center, FWHM) = ($0.48 \pm 0.11$ mJy beam$^{-1}$, 269.314 GHz (fixed), $1194 \pm 193$ km s$^{-1}$)"]
- result: FWHM at high-dispersion NE and SW positions = 928 (NE); 602 (SW) ± 72; 75 km/s [Potential indication of AGN feedback: "FWHM = $928 \pm 72$ km s$^{-1}$ at NE, $602 \pm 75$ km s$^{-1}$ at SW"]
- result: L_[CII] of the broad component at C1 = 5.83e8 ± 0.16e8 L_sun [Potential indication of AGN feedback: "$L_{\rm [CII]} = (5.83 \pm 0.16) \times 10^8~L_\odot$"]
- result: Outflowing atomic mass M_out = 5.6e8 ± 1.5e8 M_sun [Potential indication of AGN feedback: "we estimated $M_{\rm out} = (5.6 \pm 1.5) \times 10^8~M_\odot$ for $X_{\rm C^+} = 1.4 \times 10^{-4}$ and $T_{\rm ex} = 200$ K"]
- result: Outflow velocity V_out = FWHM/2 = 597 ± 97 km/s [Potential indication of AGN feedback: "Assuming an outflow velocity of $V_{\rm out} = {\rm FWHM}/2 = 597 \pm 97$ km s$^{-1}$"]
- result: Neutral outflow rate = 229 ± 73 M_sun/yr [Potential indication of AGN feedback: "we obtain a neutral outflow rate of $\dot{M}_{\rm out, neutral} = M_{\rm out}V_{\rm out}/R_{\rm out} = 229 \pm 73~M_\odot$ yr$^{-1}$"]
- result: Mass loading factor (multiphase-corrected) = >~2-3 ± not stated dimensionless [abstract: "The expected mass loading factor of the outflows, after accounting for multiphase gas, is $\gtrsim 2-3$"]
- result: Outflow kinetic energy rate = ~2.6e43 ± not stated erg/s [Potential indication of AGN feedback: "we compute its kinetic energy as $\sim 2.6 \times 10^{43}$ erg s$^{-1}$. This is only 0.4% of the quasar bolometric luminosity of C1"]
- limitation (authors): Only statistical errors shown; calibration uncertainty ~10% absolute flux [ALMA Observations: "In this paper, we show only statistical errors unless mentioned otherwise."]
- limitation (authors): Dust results are sensitive to assumed T_dust and beta [From FIR continuum emission: "We emphasize that these results are sensitive to the assumed values of $T_{\rm dust}$ and $\beta$"]
- limitation (authors): Host masses are hard to estimate because of the highly dynamic nature of the system; M_H2 and SFR from [CII] are not independent [Global gas dynamics: "The actual masses of the host galaxies of C1 and C2, and their ratio, are hard to estimate at this moment given the highly dynamic nature of the system."]
- not stated (card): Line-free channel ranges / frequency ranges used for the continuum map and uvcontsub fit; tclean cell size, image size, clean threshold in mJy, masking and number of iterations; Whether and how the pipeline calibration was manually modified or self-calibrated; Primary-beam correction details and whether the cube was primary-beam corrected before photometry; Exact definition of the 50 km/s channel…

### 2013ApJ...773...44W: Star Formation and Gas Kinematics of Quasar Host Galaxies at z ~ 6: New Insights from ALMA (2013; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the star formation activity, gas distribution, kinematics and dynamical masses of the host galaxies of five z~6 quasars, traced by [C II] 158 um and dust continuum with ALMA?
- step 2: Measure [C II] line parameters and continuum
  - method: Subtract continuum in uv plane, integrate intensity over line-emitting region per channel, fit single Gaussian [3 Results: "calculate the line spectra by integrating the intensity over the line-emitting region in each channel, and fit the spectra with a Gaussian profile."]
  - software: CASA
  - fitting: single Gaussian profile [Table 2: "redshift, flux, and FWHM line width of the [C II] line fitted to a single Gaussian line profile"]
  - validation: Continuum flux densities compared with MAMBO values [3 Results: "which is in very good agreement with the MAMBO value"]
- step 3: Derive [C II] luminosity and FIR luminosity
  - method: L_CII from Solomon & Vanden Bout formula; L_FIR (42.5-122.5 um) from modified blackbody fit to ALMA, MAMBO, PdBI, SCUBA data [3 Results: "We then estimate their FIR luminosities ($\rm L_{FIR}$) by fitting a modified black body"]
  - parameter: Tdust=47 K, beta=1.6 for four sources; J2054-0005 Tdust free with Herschel 350 um [3 Results: "leave $\rm T_{dust}$ as a free parameter. The fit suggests $\rm T_{dust}=52\pm6$ K"]
  - assumption: Tdust=47 K, beta=1.6 (mean of high-z FIR-luminous quasars) [3 Results: "we adopt a dust temperature of $\rm T_{dust}=47$ K and emissivity index of $\rm \beta=1.6$"]
  - fitting: modified blackbody S_nu ~ nu^(3+beta)/(exp(h nu/kT)-1); sampler/priors not stated [Results: "fitting a modified black body (i.e., $\rm S_{\nu}\sim {\nu}^{3+\beta}/(exp(h\nu /kT_{dust})-1)$"]
  - validation: Sensitivity to Tdust=50 K (+20%) and Tdust=41 K, beta=1.95 (-8%) [3 Results: "could be larger by up to 20% if a higher dust temperature of 50K is assumed"]
- step 6: Search for serendipitous line emitters
  - method: Bayesian line search in cubes; candidate probabilities [4.3 Search for [CII] line emitters asso…: "We do not find any candidate detections of serendipitous line emission in our data with probabilities above $25\%$."]
- result: [C II] luminosity range = 1.6 to 8.7e9 ± not stated Lsun [3 Results: "The derived line luminosities are in the range of 1.6 to 8.7$\rm \times10^{9}\,L_{\odot}$."]
- result: [C II]-to-FIR luminosity ratio = 2.9-5.1e-4 ± not stated dimensionless [abstract: "the [C II]-to-FIR luminosity ratios are $\rm 2.9-5.1\times10^{-4}$"]
- result: J2310+1855 263 GHz continuum flux density = 8.91 ± 0.08 mJy [Table 2: "J2310+1855 | 50 | 6.0031$\pm$0.0002 | 8.83$\pm$0.44 | 393$\pm$21 | 0.5 | 263 | 8.91$\pm$0.08 | 0.06"]
- result: J2310+1855 [C II] redshift = 6.0031 ± 0.0002 dimensionless [Table 2: "J2310+1855 | 50 | 6.0031$\pm$0.0002 | 8.83$\pm$0.44 | 393$\pm$21"]
- result: J2054-0005 Tdust and LFIR = Tdust=52, LFIR=8.0e12 ± ±6 K; ±3.3e12 K; Lsun [3 Results: "The fit suggests $\rm T_{dust}=52\pm6$ K and $\rm L_{FIR}=(8.0\pm3.3)\times10^{12}\,L_{\odot}$."]
- result: LFIR for other four sources = 5-17e12 ± not stated Lsun [3 Results: "in the range 42.5-122.5 $\mu$m of 5$-$17$\rm \times10^{12}\,L_{\odot}$"]
- result: J2310+1855 CO(6-5) line luminosity = 5.4e8 ± 0.5e8 Lsun [3 Results: "which is $\rm (5.4\pm0.5)\times10^{8}\,L_{\odot}$"]
- result: [C II]/CO(1-0) luminosity ratio = 2400 to 4700 ± not stated dimensionless [4.1 Distributions of gas, dust, and sta…: "The calculated [C II]-to-CO (1-0) line luminosity ratios are about 2400 to 4700"]
- limitation (authors): Limited resolution gives only constraints on size; morphology uncertain, large errors on minor axis and PA affect inclination and Mdyn. [4.2 Dynamical masses traced by the [C I…: "there are still large uncertainties in the intrinsic source morphology measurements; the deconvolved minor axis and position angle measurements of some of the objects show large error bars."]
- limitation (authors): [C II] may trace only the central starburst, underestimating bulge mass. [4.2 Dynamical masses traced by the [C I…: "This may underestimate the total masses within the spheroidal stellar bulges."]
- not stated (card): CASA version and calibration scripts/pipeline; Imaging parameters: weighting/robust, cell size, image size, deconvolver, cleaning masks; Line-free channels used for continuum subtraction; Region used to integrate spectra and velocity-map construction details; Eddington-accretion SMBH mass formula details; Exact Gaussian line fit procedure for spectra; Which MAMBO/PdBI/SCUBA data points entered ea…

### 2020ApJ...903...34A: Probing the Nature of High-redshift Weak Emission Line Quasars: A Young Quasar with a Starburst Host Galaxy (2020; agn_and_quasars, high_z_galaxies; multi_facility_alma_minor)
- question: What is the nature of the weak emission line quasar PSO J083+11 at z=6.34 (young quasar vs lensing vs soft continuum), and what are the properties of its host galaxy from ALMA [C II] and dust continuum?
- step 5: Subtract continuum and make [C II] cubes
  - method: Mask line channels, median continuum model, subtract from visibilities, image cubes [Sub-millimeter observation with ALMA: "Then, we masked out the line-containing channels and used a simple median approximation to model the continuum. After that, we produced continuum-free data by subtracting the continuum model from visibilities."]
  - software: CASA
  - parameter: 30 MHz channel width; beam ~0.42'' x 0.37''; rms ~0.24 mJy/beam [Sub-millimeter observation with ALMA: "The final imaged cubes have 30 MHz channel width, a synthesized beam of around $0.42\ensuremath{''}\times0.37\ensuremath{''}$, and a root-mean-square (rms) noise level of $\sim 0.24$ mJy beam$^{-1}$."]
- step 6: Extract [C II] spectrum and fit line flux, FWHM and redshift
  - method: Spectrum from a 1.5'' radius aperture (8.3 kpc); aperture flux scaled by epsilon = C/(D-R) applied to the dirty image flux; Gaussian fit [[C II] spectral profile: "The \[C II\] spectrum is extracted with an aperture radius of 1.5$''$ (equivalent to 8.3 kpc) to maximize the recoverable emission."] [[C II] spectral profile: "Then, the scaling factor for correction is $\epsilon = C/(D-R)$."]
  - parameter: aperture radius 1.5'' (8.3 kpc); epsilon ~ 0.6 [[C II] spectral profile: "In our case, $\epsilon \approx 0.6$."]
  - fitting: Gaussian fit to the extracted spectrum (fitting code and uncertainty method not stated) [[C II] spectral profile: "a Gaussian fit results in the integrated \[C II\] line flux of of $10.22 \pm 0.35$ Jy km s$^{-1}$"]
  - validation: Aperture radius chosen because no further [C II] flux is recovered outside it; final-image flux would be ~10% larger [[C II] spectral profile: "We chose this value, because there is no further \[C II\] flux recovered outside this radius."] [[C II] spectral profile: "Note that if using the final image only to measure the flux, we would obtain $\sim10\%$ larger values."]
- step 8: Make [C II] moment maps and measure sizes and velocity structure
  - method: Moment 0 over 700 km/s (3 x FWHM); moment 1 and 2 maps; sizes from 2D Gaussian fits to continuum and [C II] emission [Moment maps for [C II] and dust continu…: "The moment zero map of \[C II\] is also created by collapsing the 700 km s$^{-1}$ cube width"] [Moment maps for [C II] and dust continu…: "These sizes are defined as the major and minor axis FWHMs of 2D Gaussian function, which is fitted to those emissions."]
  - parameter: 700 km/s collapse width equals 3 x [C II] FWHM [Moment maps for [C II] and dust continu…: "This width is equivalent to $3 \times$ \[C II\] FWHM."]
  - fitting: 2D Gaussian fit (details not stated) [Moment maps for [C II] and dust continu…: "These sizes are defined as the major and minor axis FWHMs of 2D Gaussian function, which is fitted to those emissions."]
- step 9: Derive [C II] luminosity and [C II]-based SFR
  - method: L[CII] from Carilli & Walter formula; SFR from the De Looze et al. L[CII] scaling relation with a factor ~2.5 systematic uncertainty [Star formation rate: "To derive a star formation rate in the quasar host galaxy we first calculate the \[C II\] 158 $\mu$m line luminosity following (cite: 2013ARA&A..51..105C):"] [Star formation rate: "However, one needs to take into account a factor of $\sim 2.5$ for the systematic uncertainty from the scaling relation"]
  - assumption: SFR-L[CII] relation calibrated for z>5 galaxies applied to the quasar host [Star formation rate: "scaling relations for $z>5$ galaxies"]
  - validation: SFR[CII] consistent with SFR from TIR [Star formation rate: "This is consistent with SFR estimate based on the \[C II\] luminosity above."]
- result: [C II] redshift = 6.3401 ± 0.0004 dimensionless [[C II] spectral profile: "a Gaussian fit results in the integrated \[C II\] line flux of of $10.22 \pm 0.35$ Jy km s$^{-1}$, FWHM of $229 \pm 5$ km s$^{-1}$, and a redshift of $6.3401 \pm 0.0004$"]
- result: [C II] integrated line flux = 10.22 ± 0.35 Jy km/s [[C II] spectral profile: "a Gaussian fit results in the integrated \[C II\] line flux of of $10.22 \pm 0.35$ Jy km s$^{-1}$, FWHM of $229 \pm 5$ km s$^{-1}$, and a redshift of $6.3401 \pm 0.0004$"]
- result: [C II] FWHM = 229 ± 5 km/s [[C II] spectral profile: "a Gaussian fit results in the integrated \[C II\] line flux of of $10.22 \pm 0.35$ Jy km s$^{-1}$, FWHM of $229 \pm 5$ km s$^{-1}$, and a redshift of $6.3401 \pm 0.0004$"]
- result: Flux scaling factor epsilon = ~0.6 ± not stated dimensionless [[C II] spectral profile: "In our case, $\epsilon \approx 0.6$."]
- result: Mg II velocity offset relative to [C II] = 237 ± 150 km/s [[C II] spectral profile: "the Mg II (quasar broad line region tracer) is redshifted by $237 \pm 150$ km s$^{-1}$"]
- result: Continuum and [C II] sizes (major x minor FWHM) = continuum 2.3 x 1.7; [C II] 8.2 x 4.3 ± approximate kpc [Moment maps for [C II] and dust continu…: "approximate sizes of 2.3 kpc $\times$ 1.7 kpc and 8.2 kpc $\times$ 4.3 kpc, respectively"]
- result: [C II] line luminosity = 1.04e10 ± 0.04e10 Lsun [Star formation rate: "We obtain a luminosity of $L_{\rm [C\,\textsc{ii}]} = (1.04 \pm 0.04) \times 10^{10}\,L_\odot$"]
- result: SFR from [C II] (central value) = ~1990 ± factor ~2.5 systematic Msun/yr [Star formation rate: "This will give us value of SFR$_{\rm [C\,\textsc{ii}]} \sim 1990\,M_\odot\,\mathrm{yr^{-1}}$."]
- result: SFR from [C II] (possible range) = 800-4900 ± range Msun/yr [Star formation rate: "possible range of derived SFR for PSO J083+11 SFR$_{\rm [C\,\textsc{ii}]} = 800-4900\,M_\odot\,\mathrm{yr^{-1}}$"]
- limitation (authors): Only two continuum points on the Rayleigh-Jeans tail, so dust temperature and SED shape unconstrained; dust mass has at least a factor of two systematic uncertainty [Star formation rate: "Note that we only have 2 data points of continuum measurements – at 244 and 258 GHz – both of them located on the Rayleigh–Jeans tail and not reaching the dust SED peak."]
- limitation (authors): Black hole mass systematic errors (~0.5 dex) not included; virial calibration may be inadequate for WLQs [Black hole mass and Eddington ratio: "However, please note that we did not explicitly add the systematic errors which tend to be larger ($\approx 0.5$ dex) compared to random measurement errors"]
- limitation (authors): Shielding gas between disk and BLR cannot be excluded without X-ray spectroscopy [Summary and Conclusion: "However, we cannot completely rule out the possibility of the presence of shielding gas between accretion disk and BLR due to the lack of X-ray spectroscopy."]
- not stated (card): CASA version and ALMA pipeline version/release used for calibration, and whether the archive products were used as delivered; Flux, bandpass and phase calibrators and the absolute flux scale uncertainty; Spectral window layout and which channels were treated as line-free for the median continuum model (and the [C II] channel range masked); tclean parameters not given: cell size, image size, decon…

### 2026A&A...707A..77H: Massive dusty multiphase outflow in local merger shows no sign of slowing on kiloparsec scales (2026; nearby_galaxies; archival_reuse)
- question: Can an outflow identification method that uses MUSE stellar kinematics to define the quiescent gas in the ALMA CO(1-0) line profiles reveal the properties, multiphase structure and dust content of the outflow in the ULIRG merger IRAS20100-…
- step 6: Derive ionized and neutral atomic outflow masses and velocities from MUSE
  - method: Ionized mass from Halpha and [OIII] luminosities scaled by electron density from the [SII] ratio; neutral mass from NaI doublet absorption fit with an optical-depth model, column density and covering fraction [4.2 Ionized gas tracers: "We calculated the electron densities for each bin from the ratio between the \[SII\]$\lambda$6716 and \[SII\]$\lambda$6731 emission lines"] [9 Sodium absorption line fitting: "From the hydrogen column density, we can calculate the outflowing neutral atomic gas mass in each bin as"]
  - software: lmfit (python), GandALF
  - parameter: detection threshold A_G/N_G > 3 [4.2 Ionized gas tracers: "We set our threshold for a detection at $A_\mathrm{G}/N_\mathrm{G} > 3$"]
  - parameter: [SII] ratio R constrained to 0.44 to 1.45; electron density below 50 cm^-3 treated as an upper limit of 50 cm^-3 [4.2 Ionized gas tracers: "to lie within 0.44 and 1.45"] [4.2 Ionized gas tracers: "We accounted for this by treating electron densities below $50\,\mathrm{cm^{-3}}$ as upper limits with value $50\,\mathrm{cm^{-3}}$ in our calculations"]
  - parameter: NaI optical depth ratio tau_0,blue = 2 tau_0,red; NaI y = 0.9, a_Na = -5.69, b_dust = -0.95 [9 Sodium absorption line fitting: "so we set $\tau_\mathrm{0,blue} = 2\tau_\mathrm{0,red}$ for this fit."] [9 Sodium absorption line fitting: "we adopt values of $y=0.9$, $a_\mathrm{Na}=-5.69$, and $b_\mathrm{dust}=-0.95$ respectively from (cite: SavageSodiumAbundance1996) and (cite: rupkeOutflowsInfraredLuminousStarbursts2005)."]
  - assumption: Metallicity for the outflow taken from the quiescent line components because strong-line metallicities cannot be applied to shock/LINER-like gas; [O/H]_sun = 8.77 [4.3 Outflow ionization state and metall…: "We used the quiescent line components to derive metallicities for the outflow in each bin"] [4.3 Outflow ionization state and metall…: "we adopted a value of 8.77, to be consistent with (cite: dopitaChemicalAbundancesHighredshift2016)"]
  - assumption: Quoted ionized masses are lower limits because of the electron density floor [4.2 Ionized gas tracers: "As a result, the global outflow masses we obtained should be treated as the lower limits for the actual outflow masses."]
  - fitting: NaI model fitted per Voronoi bin with python lmfit; [SII] amplitudes re-fitted with lmfit keeping GandALF kinematics fixed [9 Sodium absorption line fitting: "We can then construct the intensity profile with properly modeled NaI doublet absorption using Eq. [\[eq:intensity_sodium\]](#eq:intensity_sodium), and fit the resulting model to the MUSE data in each Voronoi bin."] [4.2 Ionized gas tracers: "python package to re-fit the amplitudes of both main and wing components for both lines"]
- result: Characteristic outflow velocities (SE blue side: molecular, neutral, ionized high-velocity) = 160 / 360 / 430 ± not stated km/s [5.1 Outflow velocity structure: "The cold molecular gas has the lowest characteristic velocity with 160 km/s, followed by the neutral atomic phase with 360 km/s, and the ionized phase with 430 km/s"]
- result: SE neutral atomic outflow mass = 51e7 ± +/-12e7 (Table 4) Msun [4.4 Neutral atomic gas: "At $51\times10^7M_\odot$, the neutral outflow phase carries about five times the mass of the ionized phase traced by H$\alpha$ emission"]
- limitation (authors): Ionized outflow masses are lower limits due to the electron density floor [4.2 Ionized gas tracers: "As a result, the global outflow masses we obtained should be treated as the lower limits for the actual outflow masses."]
- limitation (authors): alpha_CO in outflows is highly uncertain, so energetics are order-of-magnitude estimates [5.3 Outflow energetics: "For cold molecular gas in outflows, $\alpha_\mathrm{CO}$ is highly uncertain"]
- not stated (card): tclean parameters for the CO(1-0) cube: weighting and robust value, deconvolver, niter, threshold, masking, gridder, field/spw selection, output channel grid and velocity range; Line-free channels and polynomial order used in uvconsub continuum subtraction; Whether the archive calibration/pipeline products were used as-is or re-calibrated, and the flux/bandpass/phase calibrators; Noise estimate f…

### 2019A&A...631A..78S: A spectral stacking analysis to search for faint outflow signatures in z ∼ 6 quasars (2019; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Is there a faint broad high-velocity [C II] component indicating outflows in the stacked spectra and cubes of z~6 quasars?
- step 3: Velocity re-binning to common FWHM
  - method: Rebin channels so each [CII] FWHM covers same number of channels, normalised to narrowest line [4.1 Velocity re-binning: "$cw_{rebin}\,=\,cw_{orig}\,\times\,\rm FWHM_{orig}/FWHM_{min}$"]
  - software: Line Stacker
  - parameter: FWHM_min = 270 km/s; mean stacked channel width 60 km/s [4.1 Velocity re-binning: "the channel width of the stacked spectrum is taken as the mean channel width of all the individual spectra once re-binned, for our sample that corresponds to 60 km s$^{\rm -1}$"]
  - validation: Mock stacking without outflow: >2 sigma broad excess in 2-5% of straightforward stacks, none without noise [6.1 Spectral line stacking methods: "excess emission due to a broad component is found at $>2\sigma$ 2-5% of the time"]
- step 6: Estimate mean outflow rate
  - method: Hailey-Dunsheath mass from broad [CII] luminosity; v = 0.5 FWHM; Mdot = M v / R [5.2 A sub-sample with outflow signatures: "$\dot{M}_{outf} = M_{outf}/\tau_{dyn} = M_{outf}\times\upsilon_{outf}/R$"]
  - parameter: z=6.236, R=11.5 kpc (2"), v=493 km/s [5.2 A sub-sample with outflow signatures: "For the mean redshift of 6.236, a radius of $R = 11.5kpc$ (2$^{\prime\prime}$), and $\upsilon_{outf} = 493$ km s$^{\rm -1}$"]
  - assumption: X_C+=1.4e-4, T=200 K, n>>ncrit~3e3 cm^-3, constant outflow velocity [5.2 A sub-sample with outflow signatures: "we assume that X$_{\rm C^+} = 1.4\times10^{-4}$, T $=$ 200 K, and $n>>n_{crit}$"]
- result: Mean outflow rate, max sub-sample = 45 ± ±21 Msun/yr [5.2 A sub-sample with outflow signatures: "calculate that $\dot{M}_{outf} = 45\pm21$ M$_\odot$ yr$^{-1}$"]
- limitation (authors): Assumes a single broad Gaussian outflow profile; broad emission could be from interacting galaxies; low-velocity outflows not detectable [5.2 A sub-sample with outflow signatures: "we have assumed that the outflow emission signature has the spectral profile of a single broad Gaussian"]
- not stated (card): Line Stacker code is 'Jolly et al. in prep' and not released; Line-free channel ranges for uvcontsub and fit orders; Exact manual calibration scripts, flagging and which sources were recalibrated; How sigma significance of excess emission is normalised; Fitting method and starting guesses for the two-Gaussian fit; Grade definition and exact threshold details of sub-sample ranking; Exact moment-0 …

## All papers in this technique

- 2012A&A...542L..34N (2012): ALMA reveals a chemically evolved submillimeter galaxy at z = 4.76
- 2012ApJ...752L..30W (2012): [C II] Line Emission in Massive Star-forming Galaxies at z = 4.7
- 2013A&A...559A..29C (2013): Strongly star-forming rotating disks in a complex merging system at z = 4.7 as revealed by ALMA
- 2013ApJ...763..120C (2013): The Anatomy of an Extreme Starburst within 1.3 Gyr of the Big Bang Revealed by ALMA
- 2013ApJ...770...13W (2013): Redshift 6.4 Host Galaxies of 10<SUP>8</SUP> Solar Mass Black Holes: Low Star Formation Rate and Dynamical Mass
- 2013ApJ...773...44W (2013): Star Formation and Gas Kinematics of Quasar Host Galaxies at z ~ 6: New Insights from ALMA
- 2013MNRAS.431L..88H (2013): Physical conditions of the gas in an ALMA [C ii]-identified submillimetre galaxy at z = 4.44.
- 2014A&A...565A..59D (2014): ALMA resolves turbulent, rotating [CII] emission in a young starburst galaxy at z = 4.8
- 2014ApJ...792...34O (2014): ALMA Observation of 158 μm [C II] Line and Dust Continuum of a z = 7 Normally Star-forming Galaxy in the Epoch of Reionization
- 2014ApJ...795....5O (2014): Faint Submillimeter Galaxies Revealed by Multifield Deep ALMA Observations: Number Counts, Spatial Clustering, and a Dark Submillimeter Lin…
- 2015A&A...576L...2S (2015): ALMA detection of [C ii] 158 μm emission from a strongly lensed z = 2.013 star-forming galaxy
- 2015ApJ...801..123W (2015): Star Formation Rate and Dynamical Mass of 10<SUP>8</SUP> Solar Mass Black Hole Host Galaxies At Redshift 6
- 2015ApJ...807..180W (2015): Star Formation and the Interstellar Medium in z &gt; 6 UV-luminous Lyman-break Galaxies
- 2015MNRAS.449.2883G (2015): The nature of the [C II] emission in dusty star-forming galaxies from the SPT survey
- 2015MNRAS.451.1141M (2015): The ALMA Patchy Deep Survey: a blind search for [C II] emitters at z ∼ 4.5
- 2015MNRAS.452...54M (2015): The assembly of `normal' galaxies at z ∼ 7 probed by ALMA
- 2015Natur.522..455C (2015): Galaxies at redshifts 5 to 6 with systematically low dust content and high [C II] emission
- 2016A&A...592A..83K (2016): Volatile-carbon locking and release in protoplanetary disks. A study of TW Hya and HD 100546
- 2016A&A...593L...2N (2016): Planck's Dusty GEMS. II. Extended [CII] emission and absorption in the Garnet at z = 3.4 seen with ALMA
- 2016ApJ...816...37V (2016): Bright [C II] and Dust Emission in Three z &gt; 6.6 Quasar Host Galaxies Observed by ALMA
- 2016ApJ...816L...6D (2016): The Strikingly Uniform, Highly Turbulent Interstellar Medium of the Most Luminous Galaxy in the Universe
- 2016ApJ...826..112S (2016): ALMA Imaging and Gravitational Lens Models of South Pole Telescope—Selected Dusty, Star-Forming Galaxies at High Redshifts
- 2016ApJ...827...34O (2016): Witnessing the Birth of the Red Sequence: ALMA High-resolution Imaging of [C II] and Dust in Two Interacting Ultra-red Starbursts at z = 4.…
- 2016ApJ...829L..11P (2016): Tracing the Reionization Epoch with ALMA: [C II] Emission in z ∼ 7 Galaxies
- 2016ApJ...832..151P (2016): ALMA Reveals Weak [N II] Emission in "Typical" Galaxies and Intense Starbursts at z = 5-6
- 2016ApJ...833...67W (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Survey Description
- 2016ApJ...833...69D (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Luminosity Functions and the Evolution of the Cosmic Density of Molecular Gas
- 2016ApJ...833...70D (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Molecular Gas Reservoirs in High-redshift Galaxies
- 2016ApJ...833...71A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Search for [CII] Line and Dust Emission in 6
- 2016MNRAS.462L...6K (2016): [C II] emission in z ∼ 6 strongly lensed, star-forming galaxies
- 2016Sci...352.1559I (2016): Detection of an oxygen emission line from a high-redshift galaxy in the reionization epoch
- 2017A&A...597A..41G (2017): The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223
- 2017A&A...602A..49H (2017): VALES. II. The physical conditions of interstellar gas in normal star-forming galaxies up to z = 0.2 revealed by ALMA
- 2017A&A...605A..42C (2017): Extended ionised and clumpy gas in a normal galaxy at z = 7.1 revealed by ALMA
- 2017A&A...608A.138G (2017): The ALMA Frontier Fields Survey. III. 1.1 mm emission line identifications in Abell 2744, MACSJ 0416.1-2403, MACSJ 1149.5+2223, Abell 370, …
- 2017ApJ...834L..16U (2017): ALMA Reveals Strong [C II] Emission in a Galaxy Embedded in a Giant Lyα Blob at z = 3.1
- 2017ApJ...836....8T (2017): ALMA Observations Show Major Mergers Among the Host Galaxies of Fast-growing, High-redshift Supermassive Black Holes
- 2017ApJ...836L...2B (2017): ALMA [C II] 158 μm Detection of a Redshift 7 Lensed Galaxy behind RXJ1347.1-1145
- 2017ApJ...837..146V (2017): The Compact, ∼1 kpc Host Galaxy of a Quasar at a Redshift of 7.1
- 2017ApJ...837L..21L (2017): Dust in the Reionization Era: ALMA Observations of a z = 8.38 Gravitationally Lensed Galaxy
- 2017ApJ...840...78D (2017): An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: Spectroscopic Redshifts
- 2017ApJ...842L..15S (2017): ISM Properties of a Massive Dusty Star-forming Galaxy Discovered at z ∼ 7
- 2017ApJ...842L..16L (2017): ALMA [N II] 205 μm Imaging Spectroscopy of the Interacting Galaxy System BRI 1202-0725 at Redshift 4.7
- 2017ApJ...842L..21N (2017): ALMA Observations of Gas-rich Galaxies in z ∼ 1.6 Galaxy Clusters: Evidence for Higher Gas Fractions in High-density Environments
- 2017ApJ...845..154V (2017): Molecular Gas in Three z ∼ 7 Quasar Host Galaxies
- 2017ApJ...845..175J (2017): Galaxy Formation through Filamentary Accretion at z = 6.1
- 2017ApJ...849...91M (2017): Physical Properties of 15 Quasars at z ≳ 6.5
- 2017ApJ...850...83F (2017): Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034…
- 2017ApJ...850..108W (2017): A Wide Dispersion in Star Formation Rate and Dynamical Mass of 10<SUP>8</SUP> Solar Mass Black Hole Host Galaxies at Redshift 6
- 2017ApJ...851..145M (2017): ALMA Reveals Metals yet No Dust within Multiple Components in CR7
- 2017FrASS...4...49T (2017): Fast-growing SMBHs in Fast-growing Galaxies, at High Redshifts: the Role of Major Mergers as Revealed by ALMA
- 2017MNRAS.465L..89P (2017): A revised host galaxy association for GRB 020819B: a high-redshift dusty starburst, not a low-redshift gas-poor spiral
- 2017MNRAS.466..138K (2017): A merger in the dusty, z = 7.5 galaxy A1689-zD1?
- 2017MNRAS.466.2825B (2017): ALMA observations of atomic carbon in z ∼ 4 dusty star-forming galaxies
- 2017PASJ...69...45H (2017): ALMA deep field in SSA22: Blindly detected CO emitters and [C II] emitter candidates
- 2017Sci...355.1285N (2017): [C II] 158-μm emission from the host galaxies of damped Lyman-alpha systems
- 2018A&A...611A..22S (2018): Jekyll &amp; Hyde: quiescence and extreme obscuration in a pair of massive galaxies 1.5 Gyr after the Big Bang
- 2018A&A...617A..82B (2018): The WISSH quasars project. V. ALMA reveals the assembly of a giant galaxy around a z = 4.4 hyper-luminous QSO
- 2018A&A...619A..39F (2018): The dense molecular gas in the z ∼ 6 QSO SDSS J231038.88+185519.7 resolved by ALMA
- 2018ApJ...853..111J (2018): First Results from the Herschel and ALMA Spectroscopic Surveys of the SMC: The Relationship between [C II]-bright Gas and CO-bright Gas at …
- 2018ApJ...854...97D (2018): An ALMA [C II] Survey of 27 Quasars at z &gt; 5.94
- 2018ApJ...854L...7C (2018): ALMA Detection of Extended [C II] Emission in Himiko at z = 6.6
- 2018ApJ...856..118H (2018): Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46
- 2018ApJ...859...12G (2018): The Dust and [C II] Morphologies of Redshift ∼4.5 Sub-millimeter Galaxies at ∼200 pc Resolution: The Absence of Large Clumps in the Interst…
- 2018ApJ...861...43P (2018): Hidden in Plain Sight: A Massive, Dusty Starburst in a Galaxy Protocluster at z = 5.7 in the COSMOS Field
- 2018ApJ...861..100C (2018): An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: Identifying Candidate z ∼ 4.5 [C II] Emitters
- 2018ApJ...866..159V (2018): Dust Emission in an Accretion-rate-limited Sample of z ≳ 6 Quasars
- 2018ApJ...867..140L (2018): Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing
- 2018ApJ...869L..22W (2018): No Evidence for Enhanced [O III] 88 μm Emission in a z ∼ 6 Quasar Compared to Its Companion Starbursting Galaxy
- 2018MNRAS.473.1909G (2018): ALMA suggests outflows in z ∼ 5.5 galaxies
- 2018MNRAS.475..492K (2018): ALMACAL - III. A combined ALMA and MUSE survey for neutral, molecular, and ionized gas in an H I-absorption-selected system
- 2018MNRAS.476.4949D (2018): The ALMA-PILS survey: the sulphur connection between protostars and comets: IRAS 16293-2422 B and 67P/Churyumov-Gerasimenko
- 2018MNRAS.478.1170C (2018): Kiloparsec-scale gaseous clumps and star formation at z = 5-7
- 2018MNRAS.481.1976Z (2018): The [C II] emission as a molecular gas mass tracer in galaxies at low and high redshifts
- 2018Natur.553...51M (2018): Galaxy growth in a massive halo in the first billion years of cosmic history
- 2018Natur.553..178S (2018): Rotation in [C II]-emitting gas in two galaxies at a redshift of 6.8
- 2018Natur.556..469M (2018): A massive core for a cluster of galaxies at a redshift of 4.3
- 2018Natur.557..392H (2018): The onset of star formation 250 million years after the Big Bang
- 2018PASJ...70...36I (2018): Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). III. Star formation properties of the host galaxies at z ≳ 6 studied with AL…
- 2018Sci...362.1034D (2018): The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6
- 2019A&A...621A..83S (2019): Outflows in the inner kiloparsec of NGC 1566 as revealed by molecular (ALMA) and ionized gas (Gemini-GMOS/IFU) kinematics
- 2019A&A...626A..70S (2019): Carbon radio recombination lines from gigahertz to megahertz frequencies towards Orion A
- 2019A&A...630A..59B (2019): Widespread QSO-driven outflows in the early Universe
- 2019A&A...631A..78S (2019): A spectral stacking analysis to search for faint outflow signatures in z ∼ 6 quasars
- 2019A&A...631A.167D (2019): A dense, solar metallicity ISM in the z = 4.2 dusty star-forming galaxy SPT 0418-47
- 2019A&A...632A.106L (2019): Physical conditions in the gas phases of the giant H II region LMC-N 11. II. Origin of [C II] and fraction of CO-dark gas
- 2019ApJ...870...65I (2019): Discovery of Dying Active Galactic Nucleus in Arp 187: Experience of Drastic Luminosity Decline within 10<SUP>4</SUP> yr
- 2019ApJ...870...80L (2019): Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7
- 2019ApJ...870L..19N (2019): [C II] 158 μm Emission from z ∼ 4 H I Absorption-selected Galaxies
- 2019ApJ...871...85L (2019): The ISM Properties and Gas Kinematics of a Redshift 3 Massive Dusty Star-forming Galaxy
- 2019ApJ...872..117G (2019): Confirming Herschel Candidate Protoclusters from ALMA/VLA CO Observations
- 2019ApJ...874...27T (2019): Detection of the Far-infrared [O III] and Dust Emission in a Galaxy at Redshift 8.312: Early Metal Enrichment in the Heart of the Reionizat…
- 2019ApJ...874L..30V (2019): 400 pc Imaging of a Massive Quasar Host Galaxy at a Redshift of 6.6
- 2019ApJ...876....1T (2019): CNO Emission of an Unlensed Submillimeter Galaxy at z = 4.3
- 2019ApJ...876..112R (2019): Strong Far-ultraviolet Fields Drive the [C II]/Far-infrared Deficit in z ∼ 3 Dusty, Star-forming Galaxies
- 2019ApJ...880....2W (2019): Spatially Resolved Interstellar Medium and Highly Excited Dense Molecular Gas in the Most Luminous Quasar at z = 6.327
- 2019ApJ...880..157D (2019): ALMA and HST Kiloparsec-scale Imaging of a Quasar-galaxy Merger at Z ≈ 6.2
- 2019ApJ...881...63N (2019): An ALMA Multiline Survey of the Interstellar Medium of the Redshift 7.5 Quasar Host Galaxy J1342+0928
- 2019ApJ...881..124M (2019): Resolved UV and [C II] Structures of Luminous Galaxies within the Epoch of Reionization
- 2019ApJ...881..147S (2019): Positive and Negative Feedback of AGN Outflows in NGC 5728
- 2019ApJ...881L..23B (2019): The z = 7.54 Quasar ULAS J1342+0928 Is Hosted by a Galaxy Merger
- 2019ApJ...882....1L (2019): CO and Fine-structure Lines Reveal Low Metallicity in a Stellar-mass-rich Galaxy at z ∼ 1?
- 2019ApJ...882...10N (2019): Resolved [C II] Emission from z &gt; 6 Quasar Host-Companion Galaxy Pairs
- 2019ApJ...882..136A (2019): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Evolution of the Molecular Gas in CO-selected Galaxies
- 2019ApJ...882..138D (2019): The ALMA Spectroscopic Survey in the HUDF: CO Luminosity Functions and the Molecular Gas Content of Galaxies through Cosmic History
- 2019ApJ...882..139G (2019): The Atacama Large Millimeter/submillimeter Array Spectroscopic Survey in the Hubble Ultra Deep Field: CO Emission Lines and 3 mm Continuum …
- 2019ApJ...882..168P (2019): Low Star Formation Efficiency in Typical Galaxies at z = 5-6
- 2019ApJ...884..154W (2019): Discovery of a Dark, Massive, ALMA-only Galaxy at z ∼ 5-6 in a Tiny 3 mm Survey
- 2019ApJ...886L..35P (2019): ALMA C II 158 μm Imaging of an H I-selected Major Merger at z ∼ 4
- 2019ApJ...887...40W (2019): Resolving the Interstellar Medium in the Nuclear Region of Two z = 5.78 Quasar Host Galaxies with ALMA
- 2019ApJ...887..107F (2019): First Identification of 10 kpc [C II] 158 μm Halos around Star-forming Galaxies at z = 5-7
- 2019ApJ...887..144J (2019): Discovery of Four Apparently Cold Dusty Galaxies at z = 3.62-5.85 in the COSMOS Field: Direct Evidence of Cosmic Microwave Background Impac…
- 2019ApJ...887..183Z (2019): On the Gas Content, Star Formation Efficiency, and Environmental Quenching of Massive Galaxies in Protoclusters at z ≈ 2.0-2.5
- 2019ApJS..244...40L (2019): Automated Mining of the ALMA Archive in the COSMOS Field (A<SUP>3</SUP>COSMOS). I. Robust ALMA Continuum Photometry Catalogs and Stellar Ma…
- 2019MNRAS.483.4586F (2019): Cold molecular outflows in the local Universe and their feedback effect on galaxies
- 2019MNRAS.485.1595P (2019): Multiphase circumgalactic medium probed with MUSE and ALMA
- 2019MNRAS.487L..81L (2019): The absence of [C II] 158 μm emission in spectroscopically confirmed galaxies at z &gt; 8
- 2019MNRAS.488.5029H (2019): Star-formation rates of two GRB host galaxies at z ∼ 2 and a [C II] deficit observed with ALMA
- 2019MNRAS.490.1220K (2019): ALMACAL - VI. Molecular gas mass density across cosmic time via a blind search for intervening molecular absorbers
- 2019PASJ...71...71H (2019): Big Three Dragons: A z = 7.15 Lyman-break galaxy detected in [O III] 88 μm, [C II] 158 μm, and dust continuum with ALMA
- 2019PASJ...71..109H (2019): Detections of [O III] 88 μm in two quasars in the reionization epoch
- 2019PASJ...71..111I (2019): Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). VIII. A less biased view of the early co-evolution of black holes and host g…
- 2020A&A...633A..90G (2020): The ALPINE-ALMA [C II] survey: Star-formation-driven outflows and circumgalactic enrichment in the early Universe
- 2020A&A...641A.124L (2020): Etching glass in the early Universe: Luminous HF and H<SUB>2</SUB>O emission in a QSO-SMG pair at z = 4.7
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A.155Z (2020): GOODS-ALMA: Optically dark ALMA galaxies shed light on a cluster in formation at z = 3.5
- 2020A&A...643A...1L (2020): The ALPINE-ALMA [CII] survey. Survey strategy, observations, and sample properties of 118 star-forming galaxies at 4 &lt; z &lt; 6
- 2020A&A...643A...2B (2020): The ALPINE-ALMA [CII] survey: Data processing, catalogs, and statistical source properties
- 2020A&A...643A...3S (2020): The ALPINE-ALMA [C II] survey. Little to no evolution in the [C II]-SFR relation over the last 13 Gyr
- 2020A&A...643A...5D (2020): The ALPINE-ALMA [C II] survey. Molecular gas budget in the early Universe as traced by [C II]
- 2020A&A...643A...6C (2020): The ALPINE-ALMA [CII] survey. Small Lyα-[CII] velocity offsets in main-sequence galaxies at 4.4 &lt; z &lt; 6
- 2020A&A...643A...7G (2020): The ALPINE-ALMA [CII] survey. Circumgalactic medium pollution and gas mixing by tidal stripping in a merging system at z ∼ 4.57
- 2020A&A...643A...8G (2020): The ALPINE-ALMA [CII] survey. The nature, luminosity function, and star formation history of dusty galaxies up to z ≃ 6
- 2020ApJ...889...98M (2020): Investigating Overdensities around z &gt; 6 Galaxies through ALMA Observations of [C II]
- 2020ApJ...889..141T (2020): A Noncorotating Gas Component in an Extreme Starburst at z = 4.3
- 2020ApJ...889..162L (2020): Probing the Full CO Spectral Line Energy Distribution (SLED) in the Nuclear Region of a Quasar-starburst System at z = 6.003
- 2020ApJ...890..171J (2020): The Redshift and Star Formation Mode of AzTEC2: A Pair of Massive Galaxies at z = 4.63
- 2020ApJ...892..119M (2020): Measuring the Heating and Cooling of the Interstellar Medium at High Redshift: PAH and [C II] Observations of the Same Star-forming Galaxie…
- 2020ApJ...895...74N (2020): ALMA Observations of Quasar Host Galaxies at z ≃ 4.8
- 2020ApJ...896...93H (2020): Large Population of ALMA Galaxies at z &gt; 6 with Very High [O III] 88 μm to [C II] 158 μm Flux Ratios: Evidence of Extremely High Ionizat…
- 2020ApJ...897L..14Y (2020): Pōniuā'ena: A Luminous z = 7.5 Quasar Hosting a 1.5 Billion Solar Mass Black Hole
- 2020ApJ...900....1F (2020): The ALPINE-ALMA [C II] Survey: Size of Individual Star-forming Galaxies at z = 4-6 and Their Extended Halo Structure
- 2020ApJ...900...37E (2020): Detecting and Characterizing Young Quasars. I. Systemic Redshifts and Proximity Zone Measurements
- 2020ApJ...900..131L (2020): Ionized and Atomic Interstellar Medium in the z = 6.003 Quasar SDSS J2310+1855
- 2020ApJ...902...37D (2020): The Ionized- and Cool-gas Content of the BR1202-0725 System as Seen by MUSE and ALMA
- 2020ApJ...902..110D (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Multiband Constraints on Line-luminosity Functions and the Cosmic Density of …
- 2020ApJ...903...34A (2020): Probing the Nature of High-redshift Weak Emission Line Quasars: A Young Quasar with a Starburst Host Galaxy
- 2020ApJ...904..130V (2020): Kiloparsec-scale ALMA Imaging of [C II] and Dust Continuum Emission of 27 Quasar Host Galaxies at z ∼ 6
- 2020ApJ...904..131N (2020): No Evidence for [C II] Halos or High-velocity Outflows in z ≳ 6 Quasar Host Galaxies
- 2020ApJ...905...85S (2020): Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc …
- 2020ApJ...905..147Y (2020): The ALPINE-ALMA [C II] Survey: [C II] 158 μm Emission Line Luminosity Functions at z ∼ 4-6
- 2020ApJS..247...61F (2020): The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements
- 2020MNRAS.491L..18J (2020): The ALPINE-ALMA [C II] survey: a triple merger at z ∼ 4.56
- 2020MNRAS.492.1778M (2020): Resolved Lyman-α properties of a luminous Lyman-break galaxy in a large ionized bubble at z = 6.53
- 2020MNRAS.492.3194S (2020): KASHz: No evidence for ionised outflows instantaneously suppressing star formation in moderate luminosity AGN at z ∼ 1.4-2.6
- 2020MNRAS.493.4294B (2020): ALMA uncovers the [C II] emission and warm dust continuum in a z = 8.31 Lyman break galaxy
- 2020MNRAS.494.4090C (2020): The [C II]/[N II] ratio in 3 &lt; z &lt; 6 sub-millimetre galaxies from the South Pole Telescope survey
- 2020MNRAS.494.5542R (2020): Full of Orions: a 200-pc mapping of the interstellar medium in the redshift-3 lensed dusty star-forming galaxy SDP.81
- 2020MNRAS.495.3124H (2020): Megaparsec-scale structure around the protocluster core SPT2349-56 at z = 4.3
- 2020MNRAS.495.3409S (2020): An ALMA survey of the brightest sub-millimetre sources in the SCUBA-2-COSMOS field
- 2020MNRAS.496..875R (2020): The ALPINE-ALMA [C II] Survey: on the nature of an extremely obscured serendipitous galaxy
- 2020MNRAS.496..943D (2020): The nuclear region of NGC 613 - II. Kinematics and stellar archaeology
- 2020MNRAS.496.2155Z (2020): AlFoCS + Fornax3D: resolved star formation in the Fornax cluster with ALMA and MUSE
- 2020MNRAS.498.1560J (2020): High molecular gas content and star formation rates in local galaxies that host quasars, outflows, and jets
- 2020MNRAS.498.3624L (2020): Constraints on the electron-to-proton mass ratio variation at the epoch of reionization
- 2020MNRAS.498.4192F (2020): ALMA characterizes the dust temperature of z ∼ 5.5 star-forming galaxies
- 2020MNRAS.499.5136C (2020): Missing [C II] emission from early galaxies
- 2020Natur.581..269N (2020): A cold, massive, rotating disk galaxy 1.5 billion years after the Big Bang
- 2020Natur.584..201R (2020): A dynamically cold disk galaxy in the early Universe
- 2020PASJ...72...29O (2020): ALMA band 8 observations of DLA 2233+131 at z = 3.150
- 2020PASJ...72...69Y (2020): ALMA twenty-six arcmin<SUP>2</SUP> survey of GOODS-S at one millimeter (ASAGAO): Millimeter properties of stellar mass selected galaxies
- 2021A&A...645A..21G (2021): Multiphase feedback processes in the Sy2 galaxy NGC 5643
- 2021A&A...645A..33B (2021): The WISSH quasars project. IX. Cold gas content and environment of luminous QSOs at z ∼ 2.4-4.7
- 2021A&A...646A..26B (2021): A puzzling non-detection of [O III] and [C II] from a z ≈ 7.7 galaxy observed with ALMA
- 2021A&A...646A..76L (2021): The ALPINE-ALMA [C II] survey. Luminosity function of serendipitous [C II] line emitters at z ∼ 5
- 2021A&A...647A.194F (2021): Fast rotating and low-turbulence discs at z ≃ 4.5: Dynamical evidence of their evolution into local early-type galaxies
- 2021A&A...649A.152K (2021): The ALPINE-ALMA [CII] survey. Obscured star formation rate density and main sequence of star-forming galaxies at z &gt; 4
- 2021A&A...650A.117N (2021): The host galaxy of the short GRB 050709
- 2021A&A...652A..66P (2021): ALMA multiline survey of the ISM in two quasar host-companion galaxy pairs at z &gt; 6
- 2021A&A...652A.128J (2021): ALMA Lensing Cluster Survey: A spectral stacking analysis of [C II] in lensed z ∼ 6 galaxies
- 2021A&A...653A.111R (2021): The ALPINE-ALMA [CII] survey. The contribution of major mergers to the galaxy mass assembly at z ∼ 5
- 2021A&A...654A..37D (2021): Kinematics and star formation of high-redshift hot dust-obscured quasars as seen by ALMA
- 2021A&A...654A..90L (2021): SUPER. V. ALMA continuum observations of z ∼ 2 AGN and the elusive evidence of outflows influencing star formation
- 2021ApJ...907..122M (2021): FIR-luminous [C II] Emitters in the ALMA-SCUBA-2 COSMOS Survey (AS2COSMOS): The Nature of Submillimeter Galaxies in a 10 Comoving Megaparse…
- 2021ApJ...908...53W (2021): Revealing the Accretion Physics of Supermassive Black Holes at Redshift z ∼ 7 with Chandra and Infrared Observations
- 2021ApJ...908..146C (2021): ALMA Lensing Cluster Survey: An ALMA Galaxy Signposting a MUSE Galaxy Group at z = 4.3 Behind "El Gordo"
- 2021ApJ...908..192S (2021): ALMA 1.3 mm Survey of Lensed Submillimeter Galaxies Selected by Herschel: Discovery of Spatially Extended SMGs and Implications
- 2021ApJ...908..235I (2021): Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XII. Extended [C II] Structure (Merger or Outflow) in a z = 6.72 Red Quasar
- 2021ApJ...909..130R (2021): Ultrafaint [C II] Emission in a Redshift = 2 Gravitationally Lensed Metal-poor Dwarf Galaxy
- 2021ApJ...909..204F (2021): [C II] and CO Emission along the Bar and Counter-arms of NGC 7479
- 2021ApJ...914...36I (2021): Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XIII. Large-scale Feedback and Star Formation in a Low-luminosity Quasar at …
- 2021ApJ...917...99Y (2021): ALMA Observations of the Sub-kpc Structure of the Host Galaxy of a z = 6.5 Lensed Quasar: A Rotationally Supported Hyper-Starburst System a…
- 2021ApJ...918...69U (2021): ALMA Observations of Lyα Blob 1: Multiple Major Mergers and Widely Distributed Interstellar Media
- 2021ApJ...921...97J (2021): Molecular Line Observations in Two Dusty Star-forming Galaxies at z = 6.9
- 2021MNRAS.500.3802H (2021): Centrally concentrated molecular gas driving galactic-scale ionized gas outflows in star-forming galaxies
- 2021MNRAS.502.1797R (2021): Optical and near-infrared observations of the SPT2349-56 proto-cluster core at z = 4.3
- 2021MNRAS.504..928P (2021): Unveiling the nature of 11 dusty star-forming galaxies at the peak of cosmic star formation history
- 2021MNRAS.505.4838L (2021): ALMA Lensing Cluster Survey: a strongly lensed multiply imaged dusty system at z ≥ 6
- 2021MNRAS.506..562P (2021): Dust in the central parsecs of unobscured AGN: more challenges to the torus
- 2021Sci...371..713L (2021): A massive stellar bulge in a regularly rotating galaxy 1.2 billion years after the Big Bang
- 2021Sci...372.1201T (2021): Spiral morphology in an intensely star-forming disk galaxy more than 12 billion years ago
- 2022A&A...660A..14R (2022): The ALPINE-ALMA [CII] survey: The population of [CII]-undetected galaxies and their role in the L<SUB>[CII]</SUB>-SFR relation
- 2022A&A...661A.136G (2022): The molecular gas resolved by ALMA in the low-metallicity merging dwarf galaxy Haro 11
- 2022A&A...665A...3J (2022): Diagnosing deceivingly cold dusty galaxies at 3.5 &lt; z &lt; 6: A substantial population of compact starbursts with high infrared optical …
- 2022A&A...665A.107T (2022): Black hole and host galaxy growth in an isolated z ∼ 6 QSO observed with ALMA
- 2022ApJ...928..150T (2022): Probing Multiphase Gas in Local Massive Elliptical Galaxies via Multiwavelength Observations
- 2022ApJ...934..173S (2022): The ALMaQUEST Survey. VIII. What Causes the Discrepancy in the Velocity between the CO and Hα Rotation Curves in Galaxies?
- 2022ApJ...941...47S (2022): A Molecular Gas Ring Hidden in the Sombrero Galaxy
- 2022MNRAS.510.3734D (2022): A high-resolution investigation of the multiphase ISM in a galaxy during the first two billion years
- 2022MNRAS.511.1303V (2022): The ALPINE-ALMA [C II] survey: Investigation of 10 galaxies at z 4.5 with [O II] and [C II] line emission - ISM properties and [O II]-SFR r…
- 2022MNRAS.511.3017U (2022): The bright extragalactic ALMA redshift survey (BEARS) I: redshifts of bright gravitationally lensed galaxies from the Herschel ATLAS
- 2022MNRAS.514.5035L (2022): WISDOM project - XI. Star formation efficiency in the bulge of the AGN-host Galaxy NGC 3169 with SITELLE and ALMA
- 2022MNRAS.515..678B (2022): High-z Sudoku: a diagnostic tool for identifying robust (sub)mm redshifts
- 2022MNRAS.515.1751W (2022): Dual constraints with ALMA: new [O III] 88-μm and dust-continuum observations reveal the ISM conditions of luminous LBGs at z 7
- 2022MNRAS.515.3126I (2022): The ALMA REBELS Survey: dust continuum detections at z &gt; 6.5
- 2022MNRAS.516.5618P (2022): MUSE-ALMA haloes VII: survey science goals &amp; design, data processing and final catalogues
- 2022NatCo..13.4574G (2022): Detection of companion galaxies around hot dust-obscured hyper-luminous galaxy W0410-0913
- 2022PASJ...74.1429T (2022): Central concentration of warm and dense molecular gas in a strongly lensed submillimeter galaxy at z = 6
- 2023A&A...673A.116K (2023): Exploring the environment, magnetic fields, and feedback effects of massive high-redshift galaxies with [C II]
- 2023A&A...673A.153P (2023): ALMA hints at the presence of turbulent disk galaxies at z &gt; 5
- 2023A&A...673A.157D (2023): A comprehensive view of the interstellar medium in a quasar host galaxy at z ≈ 6.4
- 2023A&A...678A.116A (2023): Tracing obscured galaxy build-up at high redshift using deep radio surveys
- 2023ApJ...942L..24K (2023): UGC 4211: A Confirmed Dual Active Galactic Nucleus in the Local Universe at 230 pc Nuclear Separation
- 2023ApJ...945...69R (2023): Updated Measurements of [O III] 88 μm, [C II] 158 μm, and Dust Continuum Emission from a z = 7.2 Galaxy
- 2023ApJ...952...48H (2023): Big Three Dragons: Molecular Gas in a Bright Lyman-break Galaxy at z = 7.15
- 2023ApJ...953...75H (2023): Characterizing CO Emitters in the SSA22-AzTEC26 Field
- 2023MNRAS.518.3183L (2023): An extended [C II] halo around a massive star-forming galaxy at z = 5.3
- 2023MNRAS.519...34H (2023): ALMACAL VIII: a pilot survey for untargeted extragalactic CO emission lines in deep ALMA calibration data
- 2023MNRAS.519.1293D (2023): A closer look at NGC 7314 nuclear region: a multiwavelength analysis of the Seyfert nucleus and its surroundings
- 2023MNRAS.519.2030H (2023): The molecular gas kinematics in the host galaxy of non-repeating FRB 180924B
- 2023MNRAS.519.5807D (2023): Deep Herschel observations of the 2 Jy sample: assessing the non-thermal and AGN contributions to the far-IR continuum
- 2023MNRAS.521.1045R (2023): Regular rotation and low turbulence in a diverse sample of z ∼ 4.5 galaxies observed with ALMA
- 2023MNRAS.523.4654T (2023): Spatially resolved dust properties and quasar-galaxy decomposition of a hyper-luminous infrared galaxy at z = 4.4
- 2023MNRAS.524..923Z (2023): The large molecular gas fraction of post-starburst galaxies at z &gt; 1
- 2023Natur.617..261K (2023): Compact [C II] emitters around a C IV absorption complex at redshift 5.7
- 2024A&A...682A..24A (2024): The ALMA Reionization Era Bright Emission Line Survey: The molecular gas content of galaxies at z 7
- 2024A&A...682A..54T (2024): HYPERION. Interacting companion and outflow in the most luminous z &gt; 6 quasar
- 2024A&A...682A.166F (2024): A benchmark for extreme conditions of the multiphase interstellar medium in the most luminous hot dust-obscured galaxy at z = 4.6
- 2024A&A...683A..64A (2024): Extended Lyman-α emission towards the SPT2349-56 protocluster at z = 4.3
- 2024A&A...683A.169W (2024): JWST discovers an AGN ionization cone but only weak radiatively driven feedback in a powerful z ≈ 3.5 radio-loud AGN
- 2024A&A...684A..24P (2024): GA-NIFS: Early-stage feedback in a heavily obscured active galactic nucleus at z = 4.76
- 2024A&A...684A..33K (2024): The cold molecular gas in z ≳ 6 quasar host galaxies
- 2024A&A...684A..56K (2024): Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O
- 2024A&A...684A.107M (2024): Optical tomography of the born-again ejecta of A 58
- 2024A&A...684A.119P (2024): ALMA survey of a massive node of the Cosmic Web at z ∼ 3. I. Discovery of a large overdensity of CO emitters
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024A&A...685A.138V (2024): The cold interstellar medium of a normal sub-L<SUP>⋆</SUP> galaxy at the end of reionization
- 2024A&A...686A..46E (2024): AGN feedback in the Local Universe: Multiphase outflow of the Seyfert galaxy NGC 5506
- 2024A&A...686A..48N (2024): CON-quest. II. Spatially and spectrally resolved HCN/HCO<SUP>+</SUP> line ratios in local luminous and ultraluminous infrared galaxies
- 2024A&A...686A..85A (2024): Spatially resolved Hα and ionizing photon production efficiency in the lensed galaxy MACS1149-JD1 at a redshift of 9.11
- 2024A&A...686A.156D (2024): ALMA-ALPINE [CII] survey: The sub-kpc morphology of three main sequence galaxy systems at z ∼ 4.5 revealed by ALMA
- 2024A&A...686A.187P (2024): The ALPINE-ALMA [CII] survey: Dust emission effective radius up to 3 kpc in the early Universe
- 2024A&A...687A..35R (2024): Dynamical modelling and the origin of gas turbulence in z ∼ 4.5 galaxies
- 2024A&A...687A.288G (2024): Dark progenitors and massive descendants: A first ALMA perspective of radio-selected near-IR-dark galaxies in the COSMOS field
- 2024A&A...688A.146A (2024): GA-NIFS: The core of an extremely massive protocluster at the epoch of reionisation probed with JWST/NIRSpec
- 2024A&A...689A.101C (2024): [CII] luminosity models and large-scale image cubes based on COSMOS 2020 and ALPINE-ALMA [CII] data back to the epoch of reionisation
- 2024A&A...689A.145S (2024): The ALMA-CRISTAL survey: Discovery of a 15 kpc-long gas plume in a z = 4.54 Lyman-α blob
- 2024A&A...690A..55S (2024): NOEMA formIng Cluster survEy (NICE): Characterizing eight massive galaxy groups at 1.5 &lt; z &lt; 4 in the COSMOS field
- 2024A&A...690A.197M (2024): The ALMA-CRISTAL survey: Widespread dust-obscured star formation in typical star-forming galaxies at z = 4─6
- 2024A&A...690A.232S (2024): Joint ALMA/X-ray monitoring of the radio-quiet type 1 active galactic nucleus IC 4329A
- 2024A&A...690A.255D (2024): Carbon envelopes around merging galaxies at z ∼ 4.5
- 2024A&A...690A.277M (2024): Gas flows in the central region of the Seyfert galaxy NGC 4593 with MUSE
- 2024A&A...690L..16J (2024): A photo-z cautionary tale: Redshift confirmation of COSBO-7 at z = 2.625
- 2024A&A...691A.133V (2024): The ALMA-CRISTAL survey: Dust temperature and physical conditions of the interstellar medium in a typical galaxy at z = 5.66
- 2024A&A...691A.153L (2024): GA-NIFS: JWST/NIRSpec IFS view of the z ∼ 3.5 galaxy GS5001 and its close environment at the core of a large-scale overdensity
- 2024A&A...691L...2S (2024): The tight correlation between PAH and CO emission from z ∼ 0 to 4
- 2024A&A...692A..34C (2024): A kiloparsec-scale ordered magnetic field in a galaxy at z = 5.6
- 2024ApJ...961...71F (2024): The Extended [C II] under Construction? Observation of the Brightest High-z Lensed Star-forming Galaxy at z = 6.2
- 2024ApJ...961..120C (2024): Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus
- 2024ApJ...962L..11W (2024): A Massive Protocluster Anchored by a Luminous Quasar at z = 6.63
- 2024ApJ...963...19N (2024): On the Evidence for Molecular Outflows in High-redshift Dusty Star-forming Galaxies
- 2024ApJ...963..115L (2024): The ALMaQUEST Survey. XII. Dense Molecular Gas as Traced by HCN and HCO<SUP>+</SUP> in Green Valley Galaxies
- 2024ApJ...964...39G (2024): UNCOVER Spectroscopy Confirms the Surprising Ubiquity of Active Galactic Nuclei in Red Sources at z &gt; 5
- 2024ApJ...964..146F (2024): JWST and ALMA Multiple-line Study in and around a Galaxy at z = 8.496: Optical to Far-Infrared Line Ratios and the Onset of an Outflow Prom…
- 2024ApJ...966..130R (2024): Investigating the Drivers of Electron Temperature Variations in H II Regions with Keck-KCWI and VLT-MUSE
- 2024ApJ...966..228R (2024): The MUSE Ultra Deep Field (MUDF). V. Characterizing the Mass─Metallicity Relation for Low-mass Galaxies at z ∼ 1─2
- 2024ApJ...968....9W (2024): A Spatially Resolved [C II] Survey of 31 z ∼ 7 Massive Galaxies Hosting Luminous Quasars
- 2024ApJ...969...27B (2024): MIDIS: JWST/MIRI Reveals the Stellar Structure of ALMA-selected Galaxies in the Hubble Ultra Deep Field at Cosmic Noon
- 2024ApJ...970....9B (2024): Multiphase Black Hole Feedback and a Bright [C II] Halo in a LoBAL Quasar at z ∼ 6.6
- 2024ApJ...970...30M (2024): First Constraints on the Interstellar Medium Conditions of a Low-mass, Highly Obscured z = 4.27 Main-sequence Galaxy
- 2024ApJ...971...17F (2024): An Analysis of Active Galactic Nucleus-driven Outflows in the Seyfert 1 Galaxy NGC 3227
- 2024ApJ...971...47F (2024): Dead or Alive? How Bursty Star Formation and Patchy Dust Can Cause Temporary Quiescence in High-redshift Galaxies
- 2024ApJ...972..111L (2024): Ongoing and Fossil Large-scale Outflows Detected in a High-redshift Radio Galaxy: [C II] Observations of TN J0924-2201 at z = 5.174
- 2024ApJ...972..116I (2024): Merging Gas-rich Galaxies That Harbor Low-luminosity Twin Quasars at z = 6.05: A Promising Progenitor of the Most Luminous Quasars
- 2024ApJ...974..145S (2024): UNCOVER NIRSpec/PRISM Spectroscopy Unveils Evidence of Early Core Formation in a Massive, Centrally Dusty Quiescent Galaxy at z <SUB>spec</…
- 2024ApJ...976...70L (2024): The ALMA-CRISTAL Survey: Spatially Resolved Star Formation Activity and Dust Content in 4 &lt; z &lt; 6 Star-forming Galaxies
- 2024ApJ...977..161V (2024): Kinematic Analysis of z = 4.3 Galaxies in the SPT2349─56 Protocluster Core
- 2024ApJ...977..190X (2024): Constraining the Excitation of Molecular Gas in Two Quasar-starburst Systems at z ∼ 6
- 2024ApJ...977L...9Z (2024): ALMA Detection of [O III] 88 μm at z = 12.33: Exploring the Nature and Evolution of GHZ2 as a Massive Compact Stellar System
- 2024ApJ...977L..36H (2024): Detailed Study of Stars and Gas in a z = 8.3 Massive Merger with Extreme Dust Conditions
- 2024ApJ...977L..46B (2024): [C II] Properties and Far-infrared Variability of a z = 7 Blazar
- 2024ApJS..275...36F (2024): ALMA Lensing Cluster Survey: Deep 1.2 mm Number Counts and Infrared Luminosity Functions at z ≃ 1─8
- 2024MNRAS.527.4420M (2024): The Quasar Feedback Survey: characterizing CO excitation in quasar host galaxies
- 2024MNRAS.528.5019H (2024): An optimal ALMA image of the Hubble Ultra Deep Field in the era of JWST: obscured star formation and the cosmic far-infrared background
- 2024MNRAS.528.6768H (2024): The ALMaQUEST Survey XIV: do radial molecular gas flows affect the star-forming ability of barred galaxies?
- 2024MNRAS.529L...1J (2024): New constraints on the molecular gas content of a z 8 galaxy from JVLA CO(J = 2-1) observations
- 2024MNRAS.530.4887W (2024): Little evolution of dust emissivity in bright infrared galaxies from 2 &lt; z &lt; 6
- 2024MNRAS.535..729P (2024): The spatially resolved relation between dust, gas, and metal abundance with the TYPHOON survey
- 2024MNRAS.535.1533B (2024): A novel high-z submm galaxy efficient line survey in ALMA Bands 3 through 8 - an ANGELS pilot
- 2024PASA...41..114S (2024): A jet-induced shock in a young, powerful radio galaxy at z = 3.00
- 2025A&A...693A.190J (2025): ALMA Lensing Cluster Survey: Dust mass measurements as a function of redshift, stellar mass, and star formation rate from z = 1 to z = 5
- 2025A&A...693A.237I (2025): The ALMA-CRISTAL Survey: Spatial extent of [CII] line emission in star-forming galaxies at z = 4−6
- 2025A&A...693A.309S (2025): Behind the dust veil: A panchromatic view of an optically dark galaxy at z = 4.82
- 2025A&A...694A..82S (2025): The ALPINE-ALMA [CII] Survey: Unveiling the baryon evolution in the interstellar medium of z ∼ 5 star-forming galaxies
- 2025A&A...694A.171M (2025): The host galaxies of radio-loud quasars at z &gt; 5 with ALMA
- 2025A&A...695A...6P (2025): GA-NIFS: Multiphase analysis of a star-forming galaxy at z ∼ 5.5
- 2025A&A...695A..23S (2025): Molecular gas and dust properties in z &gt; 7 quasar hosts
- 2025A&A...695A.163B (2025): ALMACAL: XIII. Evolution of the CO luminosity function and the molecular gas mass density out to z ∼ 6
- 2025A&A...695A.204V (2025): Quantifying the detection likelihood of faint peaks in interferometric data through jackknifing: Test application on finding z &gt; 10 gala…
- 2025A&A...696A..33P (2025): The MUSE Ultra Deep Field (MUDF): VII. Probing high-redshift gas structures in the surroundings of ALMA-identified massive dusty galaxies
- 2025A&A...696A..88W (2025): JWST + ALMA ubiquitously discover companion systems within ≲18 kpc around four z ≍ 3.5 luminous radio-loud AGN
- 2025A&A...698A.204H (2025): An ALMA spectroscopic survey of the Planck high-redshift object PLCK G073.4−57.5 confirms two protoclusters
- 2025A&A...699A..80H (2025): The ALMA-CRISTAL survey: Gas, dust, and stars in star-forming galaxies when the Universe was ∼1 Gyr old: I. Survey overview and case studies
- 2025A&A...699A.256P (2025): The ALMA-CRISTAL survey: Extended [CII] emission in an interacting galaxy system at z ∼ 5.5
- 2025A&A...699A.324H (2025): ADF22+: A declining faint end in the far-infrared luminosity function in the SSA22 protocluster at z = 3.09
- 2025A&A...700A.278R (2025): CO(1─0) imaging reveals 10-kiloparsec molecular gas reservoirs around star-forming galaxies at high redshift
- 2025A&A...700A.285W (2025): Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593
- 2025A&A...701A..31P (2025): Spatially resolved Hα emission in B14-65666: Compact starbursts, ionizing efficiency, and gas kinematics in an advanced merger at the Epoch…
- 2025A&A...701A..48D (2025): NGC 6860, Mrk 915, and MCG -01-24-012: I. Spatial anticorrelation between cold molecular and ionized gas distributions in Seyfert galaxies
- 2025A&A...701A..85K (2025): Early galaxy evolution: The complex interstellar medium distribution of the z ∼ 7 galaxy A1689-zD1
- 2025A&A...701A.234Z (2025): Noema formIng Cluster survEy (NICE): A census of star formation and cold gas properties in massive protoclusters at 1.5 &lt; z &lt; 4
- 2025A&A...702A.276P (2025): The pre-eruption state of T CrB as observed with ALMA in 2024
- 2025ApJ...981..135S (2025): RIOJA. Complex Dusty Starbursts in a Major Merger B14-65666 at z = 7.15
- 2025ApJ...985..243B (2025): The ALMA-CRISTAL Survey: Weak Evidence for Star-formation-driven Outflows in z ∼ 5 Main-sequence Galaxies
- 2025ApJ...985L...8U (2025): ADF22-WEB: Detection of a Molecular Gas Reservoir in a Massive Quiescent Galaxy Located in a z ≍ 3 Protocluster Core
- 2025ApJ...987...61R (2025): Resolved ALMA [C II] 158 μm Observations at Cosmic Noon: Interstellar Medium Structure and Dynamics of the Starbursting QSO SDSS J1000
- 2025ApJ...987L...2H (2025): Dissecting the Massive Pristine, Neutral Gas Reservoir of a Remarkably Bright Galaxy at z = 14.179
- 2025ApJ...987L..37W (2025): Gas-poor Hosts and Gas-rich Companions of z ≍ 3.5 Radio Active Galactic Nuclei: ALMA Insights into Jet Triggering and Feedback
- 2025ApJ...988...19S (2025): Detection of [O III]<SUB>88 μm</SUB> in JADES-GS-z14-0 at z = 14.1793
- 2025ApJ...988...48N (2025): LATIS: Comparing Galaxy and IGM Tomography Maps as Tracers of Large-scale Structure and Protoclusters at z ∼ 2.5
- 2025ApJ...989..115T (2025): ALMA Lensing Cluster Survey: Physical Characterization of Near-infrared-dark Intrinsically Faint ALMA Sources at z = 2─4
- 2025ApJ...989..160I (2025): MIDIS: MIRI Uncovers Virgil, the First Little Red Dot with Clear Detection of Its Host Galaxy at z ≃ 6.6
- 2025ApJ...990L..31B (2025): ALMA Reveals Bright Circumgalactic Emission and a Biconical Outflow in z ∼ 6.4 Quasar PSOJ183+05
- 2025ApJ...990L..61C (2025): An Upper Limit of 10<SUP>6</SUP> M<SUB>⊙</SUB> in Dust from ALMA Observations in 60 Little Red Dots
- 2025ApJ...991L..38U (2025): RIOJA. JWST and ALMA Unveil the Inhomogeneous and Complex Interstellar Medium Structure in a Star-forming Galaxy at z = 6.81
- 2025ApJ...993..204H (2025): JWST and ALMA Joint Analysis with [O II] λλ3726, 3729, [O III] λ4363, [O III] 88 μm, and [O III] 52 μm: Multizone Evolution of Electron Den…
- 2025ApJ...994....4A (2025): Enhanced Gas-phase Metallicities and Suppressed Outflows for Galaxies in a Rich Cluster Core at Cosmic Noon
- 2025ApJ...995..150K (2025): Comprehensive JWST+ALMA Study on the Extended Lyα Emitters, Himiko, and CR7 at z ∼ 7: Blue Major Merger Systems in Stark Contrast to Submil…
- 2025ApJ...995..219F (2025): PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon
- 2025ApJS..278...45F (2025): DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey
- 2025MNRAS.537.1163A (2025): The onset of bar formation in a massive galaxy at z ~ 3.8
- 2025NatAs...9..155Z (2025): A luminous and young galaxy at z = 12.33 revealed by a JWST/MIRI detection of Hα and [O III]
- 2025NatAs...9.1553F (2025): Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn
- 2025PASJ...77..139I (2025): Detection of the [O I] 63 µm emission line from the z = 6.04 quasar J2054-0005
- 2025PASJ...77..432U (2025): ADF22-WEB: A giant barred spiral starburst galaxy in the z = 3.1 SSA22 protocluster core
- 2025PASJ...77.1163H (2025): ALMA deep field in SSA22: Reconstructed [C II] luminosity function at z = 6
- 2025PASP..137l4501T (2025): The ViSta Method for Stacking in the Fourier Domain and its Application to the Dusty Star-forming Galaxies in the ALMA Science Archive
- 2026A&A...705A..39P (2026): High-z [OI] emission lines: COLDSIM simulations and ALMA observations
- 2026A&A...706A.174A (2026): Hiding behind a curtain of dust: Gas and dust properties of an ultra-luminous strongly-lensed z = 3.75 galaxy behind the Milky Way disc
- 2026A&A...706A.236M (2026): A deep ALMA Band 3 survey of HDFS/MUSE3D: Survey description and initial results
- 2026A&A...706A.285C (2026): Infrared emission from z ∼ 6.5 quasar host galaxies: a direct estimate of dust physical properties
- 2026A&A...707A..77H (2026): Massive dusty multiphase outflow in local merger shows no sign of slowing on kiloparsec scales
- 2026A&A...707A.376C (2026): MIRACLE: II. Unveiling the multiphase gas interplay in the circumnuclear region of NGC 1365 via multicloud modeling
- 2026ApJ...999...47L (2026): The Extended Mapping Obscuration to Reionization with ALMA (Ex-MORA) Survey: 5σ Source Catalog and Redshift Distribution
- 2026ApJ..1000..159M (2026): Low Dust Mass and High Star Formation Efficiency at z &gt; 12 from Deep ALMA Observations
- 2026ApJ..1000..308W (2026): The ALPINE-CRISTAL-JWST Survey: Chemical Abundance Comparison between the ISM and CGM of Main-sequence Galaxies at z = 4─6
- 2026ApJ..1000..312Z (2026): A Potential Link between Nuclear Winds and Cold Gas Outflows on Kiloparsec Scales in Reionization-era Quasars
- 2026ApJ..1002..100T (2026): Multiphase Gas Structure in the Circumnuclear Region of NGC 5506 Observed with ALMA
- 2026ApJ..1002..170S (2026): The Two-component Circumgalactic Medium Emission around z ∼ 2 Radio-loud Quasars
- 2026ApJ..1002L..28Y (2026): A Close Quasar Pair in a Massive Galaxy Merger at z = 5.7
- 2026ApJ..1003...26O (2026): The SOMA Atomic Outflow Survey. I. An Atomic O I and Highly Ionized O III Outflow from Massive Protostar G11.94-00.62
- 2026ApJ..1003..206S (2026): The Identification of Two JWST/NIRCam-dark Starburst Galaxies at z = 6.6 with ALMA
- 2026ApJ..1004...22F (2026): The ALPINE─CRISTAL─JWST Survey: The Fast Metal Enrichment of Massive Galaxies at z ∼ 5
- 2026ApJ..1004..194F (2026): ALMA Observations of [O I] 145 μm and [N II] 205 μm Emission Lines from Star-forming Galaxies at z ∼ 7
- 2026MNRAS.546ag049F (2026): REBELS-IFU: Steeply rising star formation histories and the importance of dust obscuration in massive z ≃ 7 galaxies revealed by multiwavel…
- 2026MNRAS.549ag781K (2026): GOALS-JWST: resolved multiphase molecular gas in IRAS 20551-4250 using JWST and ALMA
- 2026MNRAS.549ag931B (2026): ALMA Band 2 line survey of a z = 3.44 clumpy strongly lensed submillimetre galaxy
- 2026MNRAS.552g1615S (2026): The efficient star-forming regions of stripped-envelope supernovae
