---
name: alma-redshift-line-search
description: "Determine spectroscopic redshifts from ALMA line data and run blind line searches in cubes: targeted [CII]/[OIII]/CO confirmation around an optical or Lya prior, serendipitous and companion searches, fidelity from negative peaks, completeness from injected lines, line identification and Gaussian redshift fits, and upper limits for non-detections. Use when a task asks for a redshift from an ALMA spectrum, a search for line emitters or companions in a cube, a [CII]/[OIII] detection at high z, or a line luminosity function from a blind search. Built from 132 ALMA papers in the evidence pack (2012-2026), a few of them off-topic regex matches."
---

# Redshift determination and blind line searches

Measures where a line sits in frequency (and so z = nu_rest/nu_obs - 1), whether a peak in a cube is real,
and what fraction of real lines a search recovers. The two mistakes that matter most: (1) calling a single
peak a redshift when only one line is seen (a lone 3 mm line fits several CO transitions, and an "[CII]
companion" can be a low-z CO interloper), and (2) quoting a blind-search candidate without a fidelity
estimate from the negative (inverted) cube, since peaks at S/N ~5 are often noise.

Counts below come from the pack (`packs/redshift-line-search.md`): its aggregate tables, or my own count of
pack lines where marked "(my count)". Some pack papers are off-topic regex matches (nearby Seyfert or Galactic
work, e.g. 2024A&A...686A..46E, 2019A&A...632A.106L); I ignore those when I cite examples, but I did not build a
full exclusion list, so the aggregate counts below are unfiltered. Numbers in the parameter table are examples
seen in specific papers, not a literature consensus, unless the row says otherwise.

## When to use

- A target has a prior redshift (Lya, rest-UV, photo-z, quasar Mg II) and you need the systemic redshift from
  [CII] 158 um, [OIII] 88 um or CO: the most common situation in the pack excerpts (my reading; z ~ 4-8 galaxies and quasars,
  e.g. 2015ApJ...807..180W, 2020ApJ...897L..14Y, 2020MNRAS.493.4294B).
- You must search a cube for line emitters with no prior position: deep-field surveys
  (2016ApJ...833...67W), serendipitous emitters in targeted pointings (2021A&A...646A..76L), or companions
  around quasars (2020ApJ...904..130V, 2020ApJ...889...98M).
- You need a [CII] upper limit for a non-detection at a known optical redshift (2014ApJ...792...34O,
  2015MNRAS.452...54M).
- You need the Lya-to-systemic velocity offset (2015ApJ...807..180W, 2017ApJ...851..145M).
- You are building a line luminosity function from blind detections (2021A&A...646A..76L, 2020ApJ...905..147Y).

## When not to use

- Crowded line-rich Galactic or protostellar spectra (hot cores, COMs, line surveys of star-forming regions):
  use the `line-identification` skill. This skill assumes a few bright extragalactic lines.
- Finding continuum sources, number counts and continuum completeness: use `source-extraction-counts`.
  Only the line-detection part (3D peaks, fidelity in channels) lives here.
- Stacking many spectra for faint wings or mean signals: see `stacking` (e.g. the broad-wing stacks of
  2019A&A...630A..59B and 2019A&A...631A..78S).
- Rotation curves, dynamical masses, outflow rates once the line is detected: see `galaxy-3d-kinematics` and
  `outflow-energetics`. Line-to-H2 conversions: `gas-mass-co-conversion`.
- Intervening absorbers against bright calibrators: `absorption-lines` (2019MNRAS.490.1220K is in this pack but
  is an absorber search).
- Line-free channel choice and continuum removal details: `continuum-subtraction`.

## Steps

### 1. Fix the frequency setup and what lines can fall in it
- Goal: know which transitions each SPW can contain for the plausible redshift range before looking.
- Method (general practice): nu_obs = nu_rest/(1+z). For a targeted line, center an SPW on the prior and
  check the velocity range it covers against the prior's uncertainty. For a blind scan, list every CO ladder
  line, [CI], [CII], [OIII] that lands in band for each z.
- What papers show: spectral coverage gaps lose lines. [C II] was missed in most of one sample "due to redshift
  uncertainty and gaps in spectral coverage" (2020ApJ...892..119M); the line of source Lya-2 was truncated by coverage,
  leaving its luminosity and redshift uncertain (2013ApJ...763..120C); a whole SPW was lost to atmospheric absorption (2019PASJ...71..109H). One stack
  dropped channels with atmospheric transmission < 0.5 (2019A&A...630A..59B).
- Record the spectral reference frame (TOPO, LSRK, BARY) and velocity convention (radio, optical) of every cube
  and external spectrum. Before comparing centroids, put all spectra in the same frame; 2015ApJ...807..180W
  converted spectra to LSR before comparing the Lya centroid with the [CII] redshift. Define the sign of any
  velocity offset (here positive = Lya redward of systemic, as in +430 km/s for CLM 1, 2015ApJ...807..180W).
- Software: CASA (`listobs`), Splatalogue-style rest frequencies (general practice).

### 2. Calibrate and image the cube
- Goal: a cube whose noise is close to Gaussian and whose channels match the expected line width.
- Method: pipeline calibration in CASA, continuum subtraction (`uvcontsub` in the uv plane is common:
  2020ApJ...904..130V, 2026ApJ..1002L..28Y, 2018A&A...617A..82B), `tclean` cubes.
- Weighting: natural weighting for detection (2014ApJ...792...34O, 2020MNRAS.493.4294B,
  2018A&A...617A..82B); robust 0.5 when resolution matters (2020ApJ...904..130V, 2019ApJ...887...40W,
  2025NatAs...9.1553F).
- Channels: frequency spacings seen include 7.8 MHz (3 mm) and 31.2 MHz (1 mm) cubes (2016ApJ...833...67W),
  15 MHz (2020ApJ...889...98M), 15.625 MHz = 17.5 km/s (2015ApJ...807..180W) and 30 MHz (2020ApJ...904..130V);
  velocity widths seen include 40 km/s (2014ApJ...792...34O) and 100 km/s (2018Natur.556..469M). Convert with
  dv ~ c dnu/nu_obs (general practice) and state both.
- Software: CASA is named in 40 matched steps (pack aggregate), far more than anything else.

### 3. Targeted search at the prior position and velocity
- Goal: detect the line near a known position and z.
- Method: extract a spectrum in an aperture at the prior (or continuum) position; look within a velocity window
  of the prior; collapse a moment-0 map over the line; re-extract. Examples: spectrum at continuum peaks
  (2012ApJ...752L..30W); search within abs(v) < 500 km/s of Lya inside the primary beam, whose FWHM is 16"
  (i.e. within an 8" half-power radius; 2017A&A...605A..42C); collapse range chosen relative to Lya (2019ApJ...881..124M).
- For moment-0 widths papers use 1.2 x FWHM (2020ApJ...904..130V), +/-1.4 sigma_line with a flux correction for
  the ~83% captured (2024ApJ...968....9W), or the range giving highest S/N (2020MNRAS.493.4294B).
- Beware of picking the window that maximizes S/N on a marginal line: it biases S/N upward (general
  practice). 2020MNRAS.493.4294B checked its window against by-eye inspection.

### 4. Blind search for emitters in the full cube
- Goal: list candidate line peaks anywhere in (x, y, nu).
- Method as papers do it:
  - Matched filtering in frequency: average 3, 5, 7, 9 channels (kernel widths ~50-300 km/s) and find peaks
    with daofind (findclumps, 2016ApJ...833...67W); ALPINE used kernels ~90-550 km/s and a seed S/N of 3 in
    118 cubes (2021A&A...646A..76L); Gaussian smoothing in frequency up to 400 MHz with an S/N > 3 seed
    (2020ApJ...904..130V).
  - Seed-and-grow: voxels > 3 sigma in one 15 MHz channel, then four neighbouring channels > 2 sigma (~50 km/s
    minimum width), Gaussian fit, moment 0 over the FWHM, keep S/N > 5 inside the primary-beam FWHM with
    the main target masked (2020ApJ...889...98M).
  - Merge duplicates: the same line found by several kernels or adjacent peaks is one candidate.
    2016ApJ...833...67W removed duplicates from the overlapping kernel runs. Keep one entry per (x, y, nu)
    group, record which kernel gave the highest S/N, and use that same retained S/N in the fidelity (step 5)
    and completeness (step 6) curves.
  - Run the same search on the inverted cube (negative peaks) for fidelity (step 5).
- Restrict the search area and say whether a number is a radius or a diameter. Examples: within sqrt(2) x
  primary-beam radius at 3 mm (53" at 84 GHz, 39" at 115 GHz) and a 30.9" radius at 1 mm
  (2016ApJ...833...67W); "within the FWHM of the primary beam" (2020ApJ...889...98M), which as a region means
  a radius of FWHM/2, the half-power contour (general practice); 16" PB FWHM (2017A&A...605A..42C). Using the
  FWHM as a radius quadruples the area. Mask bright continuum sources and the main target.
- Software: findclumps (10 matched steps in the pack aggregate; the code is not released per
  2016ApJ...833...67W's card), IRAF daofind, Python + SpectralCube (2020ApJ...889...98M).

### 5. Fidelity (purity) from negative peaks
- Goal: probability that a candidate at a given S/N is real.
- Method: fidelity = 1 - N_neg/N_pos as a function of S/N and kernel width, assuming negative peaks are pure
  noise (no absorption expected) (2016ApJ...833...67W, 2021A&A...646A..76L, 2020ApJ...904..130V).
  2016ApJ...833...67W fit fidelity vs S/N with an error function (C_3mm = 5.1, sigma_3mm = 0.4;
  C_1mm = 5.0, sigma_1mm = 0.8) and stated it is "not physically motivated".
- Cuts used: fidelity >= 60% (2016ApJ...833...67W), >= 0.8 (2020ApJ...904..130V), > 85% at S/N >= 6.30
  (2021A&A...646A..76L), > 0.9 giving 16 candidates (2019ApJ...882..136A).
- Then visual vetting: channel maps on and off the line (2020ApJ...904..130V).

### 6. Completeness from injected lines
- Goal: fraction of real lines of given flux and width the search recovers.
- Method: inject Gaussian lines with random position, frequency, peak flux and width into the data (or noise)
  cubes and rerun the identical search. 2500 lines, widths 50-500 km/s, peaks 0.22-1.00 mJy at 3 mm
  (2016ApJ...833...67W); ~50000 lines in four primary-beam rings (2021A&A...646A..76L).
- Report completeness vs peak flux and width; 2016ApJ...833...67W reached > 50% at peak > 0.45 mJy and
  width > 100 km/s at 3 mm.

### 7. Identify the line and the redshift
- Goal: map each candidate to a transition and z.
- Method: use a second line, an existing optical/NIR spectroscopic redshift, or counterpart arguments.
  2016ApJ...833...67W used multiple CO lines and spec-z, and assumed band 3 candidates with no optical/NIR
  counterpart are at z > 2. Single lines cannot give definitive redshifts (2020A&A...642A.155Z).
  Association is a separate step from the search window: 2020ApJ...904..130V searched whole cubes, then
  conservatively assumed already detected candidates with abs(dv) < 2000 km/s are associated with the quasar.
  Do not confuse this with the abs(v) < 500 km/s window used to search for the line of a target around its Lya
  prior (2017A&A...605A..42C).
- Where no redshift exists at all, some papers assume one for derived quantities (z = 2, range 1-3,
  2017A&A...597A..41G); flag that as an assumption.

### 8. Fit the line and derive z, FWHM, flux, luminosity
- Method: Gaussian (often plus a constant continuum) fit to the aperture spectrum: single Gaussian plus
  constant (2020ApJ...904..130V), flat continuum plus Gaussian (2017ApJ...849...91M, GILDAS), Gaussian plus
  constant with MCMC (2026ApJ..1002L..28Y), Gaussian on the spectrum from a uv-plane fit
  (2024A&A...685A..80Z, GILDAS `uv_fit` on ALMA data). z = nu_rest/nu_center - 1 and
  sigma_z = (1+z) sigma_nu_center/nu_center, where sigma_nu_center is the fit uncertainty on the line center,
  not the line width; equivalently (1+z) sigma_vc/c with sigma_vc the centroid-velocity uncertainty (general).
- Before reporting a total flux, check and state the flux losses: aperture losses (2015MNRAS.452...54M applied
  an aperture correction of 2.5, derived from continuum serendipitous sources measured in the same aperture),
  residual scaling for apertures on a cleaned image (2020ApJ...904..130V, 0.4-1.5" radii), and the fraction of
  a Gaussian inside a finite window (2024ApJ...968....9W corrected for the ~83% within +/-1.4 sigma;
  2019ApJ...887..107F used a 270 km/s FWHM Gaussian to correct a 100 km/s window).
- Two components only when the data demand it: reduced chi2 comparison (2018PASJ...70...36I), DeltaBIC > 5
  and each component S/N > 3 (2025A&A...695A...6P).
- Fainter lines of the same source: fix the center to the [CII] redshift (2020ApJ...900..131L), tie FWHM to
  [CII] (2019ApJ...881...63N), or put a Gaussian prior on z_sys from [CII] (2020MNRAS.492.1778M).
- Luminosity: L/Lsun = 1.04e-3 x S dv [Jy km/s] x nu_obs [GHz] x D_L^2 [Mpc] (2017ApJ...851..145M). 8 of the
  pack's cosmology assumption lines use flat LCDM with H0 = 70, Om = 0.3 (my count; e.g. 2026ApJ..1002L..28Y,
  2018PASJ...70...36I); others use Om = 0.27-0.272 (2019PASJ...71..109H, 2020ApJ...889...98M). State yours.
- Typical precision reached: z = 6.1657 +/- 0.0003 (2015ApJ...807..180W), 7.5149 +/- 0.0004
  (2020ApJ...897L..14Y), 8.31132 +/- 0.00037 (2020MNRAS.493.4294B), 3.39548 +/- 0.00007
  (2024A&A...685A..80Z).

### 9. Non-detections and upper limits
- Method: 3 sigma limit from the rms at the prior position, for an assumed line width. Assumed widths vary
  widely: 40 km/s (2014ApJ...792...34O), 100 km/s (2015MNRAS.452...54M), 200 km/s (2019ApJ...881..124M),
  400 km/s when only an optical z is known (2020A&A...641A.155V).
- Say which quantity the limit is on. A flux-density limit is per channel: 2014ApJ...792...34O quotes
  < 720 uJy/beam over a 40 km/s channel. An integrated-flux limit for a top-hat window of width W made of N =
  W/dv independent channels of rms sigma_ch is I_lim = 3 sigma_ch dv sqrt(N) = 3 sigma_ch sqrt(W dv), so it
  grows as sqrt(W) (general practice). State sigma_ch, dv, W, whether the rms is per beam or in an aperture,
  any channel correlation (Hanning smoothing makes adjacent channels non-independent), and any correction for
  the part of a Gaussian line outside W.

### 10. Line luminosity function (only if you need one)
- The detections alone are not an LF: each source needs the volume in which it could have been found.
- Blind search: integrate the detectable volume per luminosity using each field's noise and the primary-beam
  response (2020ApJ...889...98M). The serendipitous LF of 2021A&A...646A..76L rests on the fidelity and
  completeness it measured (steps 5-6); the pack does not show the exact weighting, so state how you apply
  them (general practice: weight each source by fidelity/completeness).
- Targeted, UV-selected sample: a modified 1/Vmax, phi = 1/dlogL x sum(C_UV,j / V_j), with C_UV the UV
  incompleteness per M_UV bin from the UV LF (2020ApJ...905..147Y); this LF is a lower limit because UV-faint
  [CII]-bright sources are missed. Keep the two estimators distinct; hand detailed LF fitting to a
  number-counts or LF workflow.

## Parameter defaults and ranges

Read the second column as "most common in the pack" only where the papers count is 3 or more and the row
says so; otherwise it is an example from the named paper. Choose your own setting from your channel width,
expected line width and beam, and state it.

| Parameter | Common choice or example | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Weighting for detection cubes | natural (6) and robust 0.5 (5), about equally | natural, robust 0.5, robust 1 | natural 6, robust 0.5 5, robust 1 1 (my count of pack lines) | 2014ApJ...792...34O, 2020ApJ...904..130V, 2015ApJ...807..180W |
| Channel width (frequency) | examples: 7.8, 15, 15.625, 30, 31.2 MHz | 7.8-31.2 MHz | 5 named here | 2016ApJ...833...67W (7.8/31.2 MHz), 2020ApJ...889...98M (15 MHz), 2015ApJ...807..180W (15.625 MHz), 2020ApJ...904..130V (30 MHz) |
| Channel width (velocity) | examples: 17-40 km/s; 100 km/s for a blind search | 17-100 km/s | 6 named here | 2019ApJ...887...40W (17 km/s), 2015ApJ...807..180W (17.5 km/s), 2025NatAs...9.1553F (20 km/s), 2017ApJ...836L...2B (30 km/s), 2014ApJ...792...34O (40 km/s), 2018Natur.556..469M (100 km/s) |
| Frequency kernel for blind search | example: 3, 5, 7, 9 channels (~50-300 km/s) | ~50-550 km/s, or smoothing up to 400 MHz | 3 | 2016ApJ...833...67W, 2021A&A...646A..76L (~90-550 km/s), 2020ApJ...904..130V (up to 400 MHz) |
| Seed threshold | S/N 3 per voxel/kernel (3 of the 5) | 2.5 per channel over >= 3 channels to 4 | 5 (my count) | 2021A&A...646A..76L, 2020ApJ...889...98M, 2020ApJ...904..130V, 2025ApJ...995..219F (2.5), 2018Natur.556..469M (4) |
| Final detection cut | S/N >= 5 or a fidelity cut | S/N 3.5 (targeted, prior known) to 7 | 8 (my count) | 2020ApJ...905..147Y (3.5), 2016ApJ...833...69D (5), 2015MNRAS.451.1141M (6), 2024A&A...690A..55S (7) |
| Fidelity cut | 0.8-0.9 (3 of the 4) | 0.6-0.9 | 4 | 2016ApJ...833...67W (0.6), 2020ApJ...904..130V (0.8), 2021A&A...646A..76L (0.85), 2019ApJ...882..136A (0.9) |
| Injected lines for completeness | thousands | 2500 to ~50000 | 2 | 2016ApJ...833...67W, 2021A&A...646A..76L |
| Search region (radius) | examples, geometry stated | sqrt(2) x PB radius (53"/39" at 3 mm), 30.9" radius at 1 mm, within the PB FWHM (radius = FWHM/2) | 3 | 2016ApJ...833...67W, 2020ApJ...889...98M, 2017A&A...605A..42C (PB FWHM 16") |
| Search window around a prior (targeted) | example: abs(v) < 500 km/s of Lya | not varied in the pack | 1 | 2017A&A...605A..42C |
| Spectrum aperture (geometry stated) | ~1 beam, or 0.8-1.5" | 0.35" radius; 0.4-1.5" radii; 0.8" radius; 0.8" diameter; 1.5" diameter; single beam; area of four beams; 3 sigma isophote | 13 (my count) | 2017ApJ...851..145M (0.35" radius), 2020ApJ...904..130V (0.4-1.5" radii), 2020ApJ...900..131L (0.8" radius), 2026ApJ..1002L..28Y (0.8" diameter), 2018PASJ...70...36I (1.5" diameter), 2019A&A...630A..59B (four beam areas) |
| Moment-0 collapse | example: 1.2 x FWHM | +/-1.4 sigma to fixed 280-300 km/s, or highest-S/N range | 4 | 2020ApJ...904..130V, 2024ApJ...968....9W, 2020MNRAS.493.4294B, 2018ApJ...867..140L |
| Line profile model | Gaussian + constant | 1-2 Gaussians | 24 one-dimensional Gaussian phrasings in the fitting aggregate (my count) | 2020ApJ...904..130V, 2025A&A...695A...6P |
| Width assumed for upper limits | no consensus; state yours | 40-400 km/s | 4 | 2014ApJ...792...34O (40), 2015MNRAS.452...54M (100), 2019ApJ...881..124M (200), 2020A&A...641A.155V (400) |
| Companion association (after detection) | example: abs(dv) < 2000 km/s | not varied in the pack | 1 | 2020ApJ...904..130V |

Per-paper thresholds and the dust/cosmology assumptions that ride along with [CII] work are in
`references/parameters.md`.

## Software

From the pack's "Software named in the matched steps" aggregate (counts are matched steps, not papers):

| Software | Count | Used for |
|---|---|---|
| CASA (tclean, uvcontsub, immoments) | 40 | calibration, cubes, moment maps |
| findclumps | 10 | blind 3D line search, fidelity, completeness (2016ApJ...833...67W, 2021A&A...646A..76L) |
| CASA imfit | 5 | 2D Gaussian position/size/flux of line maps (2020ApJ...904..130V, 2024ApJ...968....9W, 2019PASJ...71..109H) |
| GILDAS (gildas 3, clic 1, mapping 1) | 5 in-scope of 6 unfiltered | uv-plane `uv_fit` line extraction and fits on ALMA data (2024A&A...685A..80Z); NOEMA [CII] spectra with flat continuum + Gaussian via clic/mapping (2017ApJ...849...91M). The sixth step (GILDAS/CLASS) is the off-topic LMC paper 2019A&A...632A.106L |
| emcee | 3 | two-Gaussian MCMC fit of a [CII] spectrum (2024A&A...682A..54T); also used for 2D Sersic morphology (2024A&A...691A.133V) |
| scipy curve_fit | 1 | chi2 fit of core + broad Gaussian to a stacked [CII] spectrum (2019A&A...630A..59B) |
| lmfit | 2 | 2D Sersic morphology of moment-0 maps (2024A&A...691A.133V), not line profiles; one other [CII] fit "with LMFIT" in the validation aggregate, paper not identified in the excerpts |
| IRAF daofind | 1 | peak finding inside findclumps (2016ApJ...833...67W) |
| Python + SpectralCube | 1 | seed-and-grow search (2020ApJ...889...98M) |
| Line Stacker | 1 | spectral stacking (2019A&A...631A..78S) |
| MAGPHYS | 3 | SEDs for counterpart redshift arguments (2016ApJ...833...67W) |

Not recommended here: PyMC3 (1 step) appears only in the off-topic LMC paper 2019A&A...632A.106L.

Downstream tools in the aggregate (CLOUDY 6, PDR Toolbox 3+, GalPak3D 3, 3DBarolo 2) belong to other skills.

## Pitfalls

- Single-line redshifts. "Single lines cannot give definitive redshifts" (2020A&A...642A.155Z); without
  continuum or optical/NIR counterparts, low-z CO interlopers cannot be ruled out (2020ApJ...889...98M).
  Require a second line or an independent spec-z before stating z.
- Non-Gaussian noise. An excess of large negative voxels points to correlated noise that produces false
  positives (2020ApJ...889...98M); a candidate "could be systematic noise" (2014ApJ...795....5O). Check the
  voxel histogram before trusting S/N.
- Low reliability near S/N 5. Blind-search reliability may be ~50% at S/N = 5 (2017A&A...605A..42C); 1-2 survey
  sources may be spurious and z > 9 detections marginal (2025ApJS..278...45F); one search seeded at SNR > 4 kept
  14 candidates, all above SNR 6.3 (2018Natur.556..469M).
- Selection-limited luminosity functions. UV-selected samples miss UV-faint [CII]-bright sources, so the LF
  is a lower limit (2020ApJ...905..147Y); a field LF can rest on one object (2021A&A...646A..76L).
- Extended emission resolved out. Emitters much larger than the beam can be missed (2015MNRAS.451.1141M);
  sparse short baselines resolve out [CII] (2018ApJ...859...12G).
- Coverage and atmosphere. Lines fall in gaps or bad atmospheric windows (2020ApJ...892..119M,
  2019PASJ...71..109H); limited bandwidth caps measurable velocities (2020ApJ...905...85S).
- Aperture dependence. Luminosities changed by a factor ~2 with aperture size (2017ApJ...851..145M).
- Astrometry. ALMA-HST offsets of 0.1-0.2" are uncertain (2019ApJ...881..124M); one paper shifted ALMA by
  0.25" to match HST, checked with foreground continuum sources (2017ApJ...851..145M).
- Settings cards flag as not stated (my sums over the pack's "not stated" list): CASA version (~21 flags),
  flux-calibration uncertainty (~21), line-free channels / continuum subtraction (~14), and the findclumps
  pre-fidelity S/N threshold (2016ApJ...833...67W). Report all of these.

## Verification checks

What papers did:
- Inverted-cube search to get fidelity (2016ApJ...833...67W, 2020ApJ...904..130V, 2021A&A...646A..76L);
  positive vs negative counts and split of visibilities into three subsets with consistent line flux
  (2015MNRAS.452...54M).
- Recover known sources: the search recovered a known companion and all emitters of an earlier survey
  (2020ApJ...889...98M).
- Injected-line completeness with the same pipeline (2016ApJ...833...67W, 2021A&A...646A..76L).
- Independent redshift agreement: [CII] z vs SINFONI within 1 sigma (2024A&A...685A..80Z); line width and z vs
  earlier SMA data (2012ApJ...752L..30W); [CII] vs [OIII] line profiles (2020MNRAS.493.4294B).
- Flux method agreement: channel-clipped flux vs Gaussian fit (2020ApJ...900..131L); f_clipped vs f_fit LFs
  (2020ApJ...905..147Y); random apertures of the same geometry for errors (2017ApJ...851..145M).
- Profile complexity: second component only if BIC or chi2 favors it (2025A&A...695A...6P, 2018PASJ...70...36I).

What a careful referee adds:
- Fidelity computed per kernel width and per region (primary-beam rings), not one global curve.
- The S/N used for the cut measured the same way in the real and inverted cubes, after the same masks.
- For each redshift, the list of alternative transitions that fit the same frequency and why they are excluded.
- The trials factor of picking a velocity window or kernel after looking at the data.

## Source cards

Full list: `references/sources.md` (132 papers). Most informative for this technique:

- 2016ApJ...833...67W: findclumps search, fidelity function, 2500-line completeness, counterpart-based z.
- 2021A&A...646A..76L: serendipitous [CII] in 118 cubes, fidelity 85% at S/N 6.30, ~50000 injected lines.
- 2020ApJ...904..130V: companion search in 56 quasar cubes, inverted cubes, abs(dv) < 2000 km/s association of detected candidates.
- 2020ApJ...889...98M: seed-and-grow search, negative-voxel excess, interloper caveat.
- 2019ApJ...882..136A: fidelity > 0.9 sample.
- 2016ApJ...833...69D: S/N > 5 line candidates at 3 mm and 1 mm.
- 2015MNRAS.451.1141M: blind [CII] search at z ~ 4.5, 6 sigma threshold.
- 2015MNRAS.452...54M: z ~ 7 [CII] with split-data reliability test and limits.
- 2017A&A...605A..42C: velocity window from Lya, reliability caveat.
- 2018Natur.556..469M: 100 km/s channels, SNR > 4 seeds.
- 2020A&A...642A.155Z: single-line redshift caveat.
- 2020ApJ...905..147Y: [CII] LF, detection at SNR_peak >= 3.5.
- 2025ApJS..278...45F: survey-level spurious-source caveat.
- 2015ApJ...807..180W: systemic z and Lya offsets.
- 2020MNRAS.493.4294B: z = 8.31 [CII] fit and window choice.
- 2024A&A...685A..80Z: uv-plane line extraction and SINFONI check.
- 2026ApJ..1002L..28Y: Gaussian + constant MCMC redshifts for a quasar pair.
- 2020ApJ...900..131L: fixed-center fits for faint lines.
- 2014ApJ...792...34O: non-detection limits with an assumed width.
- 2024A&A...690A..55S: P_chance thresholds for robust lines.
