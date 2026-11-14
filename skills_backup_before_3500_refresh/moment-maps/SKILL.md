---
name: alma-moment-maps
description: "Make and interpret moment maps from ALMA line cubes: integrated intensity (moment 0), intensity-weighted or fitted velocity (moment 1, quadratic peak velocity), dispersion (moment 2), peak intensity (moment 8) and peak brightness temperature, with the masking, clipping, velocity windows and uncertainty handling that published ALMA papers use. Use when collapsing a cube into maps, measuring integrated line fluxes or upper limits, building velocity fields for kinematic fits (eddy, 3DBarolo, kinemetry), or checking someone else's moment maps. Built from 413 ALMA papers (2012-2026)."
---

# Moment maps and line imaging products

Collapses a continuum-subtracted line cube into 2D maps: moment 0 (integrated intensity, Jy/beam km/s),
moment 1 (velocity), moment 2 (intensity-weighted velocity dispersion, sigma not FWHM), moment 8 or peak
brightness temperature. Every map depends on
three choices: the **velocity window**, the **mask or clip** and the **velocity estimator**. The two mistakes
that matter most: (1) clipping moment 0 with a hard per-pixel sigma cut and then quoting it as a total flux,
which drops faint extended emission (2013ApJ...769L..12L; several papers leave moment 0 unclipped and clip only
moments 1 and 2: 2020ApJ...903..145L), and (2) reading moment 2 as intrinsic turbulence when it also contains
beam smearing of rotation and multiple velocity components (2019MNRAS.487..444R treats M2 only as an upper
limit on intrinsic dispersion).

> Always report: velocity window (or mask recipe), clip threshold for each moment, channel width, rms per
> channel and how it was measured, weighting, whether maps are primary-beam corrected, rest frequency,
> velocity frame and Doppler convention, the systemic velocity adopted, and the absolute flux-scale
> uncertainty. The cards flag "moment-map clipping thresholds" as not stated in 10 card entries (6 + 4 across
> two phrasings, pack aggregates), so writing these down is already better than a good share of the literature.

## When to use

- You have a detected line in a cube and need a morphology map, total flux, sizes or radial profile
  (2016A&A...592A..76D, 2020A&A...644A..84M, 2021A&A...655A..80D).
- You need a velocity field for a rotation or Keplerian fit, a dynamical mass, PA or inclination
  (2020ApJ...891...48H, 2018ApJ...868..113T, 2025ApJ...988...72S, 2020ApJ...890..167T).
- Weak lines in disks where a Keplerian mask raises S/N (2017A&A...606A.125S, 2018A&A...614A.106C,
  2020A&A...638A..38T).
- Outflows split into red and blue lobe maps (2021A&A...648A..41V, 2019A&A...632A..33A).
- Non-detections that need an integrated-flux upper limit (2017AJ....153..240A, 2018ApJ...853..147M,
  2024A&A...682A.166F).
- Input maps for lens models or source extraction (2018ApJ...867..140L, 2014A&A...568A..92M, 2024A&A...687A.163B).

## When not to use

| Situation | Use instead |
|---|---|
| Line has several velocity components, self-absorption or broad wings along the same sightline | Per-pixel multi-Gaussian fits (1-3 Gaussians with BIC selection in 2021ApJ...908..231M; iterative Gaussian adding in 2018ApJ...865...13T), or channel maps and PV diagrams (2015ApJ...815..106H) |
| Intrinsic velocity dispersion or rotation curve of a beam-smeared galaxy | Model the cube in 3D instead of reading moment 2 (general recommendation; 3DBarolo is named in 2 matched steps, pack aggregates). Note what one paper actually did: 2025ApJ...988...72S ran 3DBarolo on the moment-1 map with stellar PA, inclination, centre and vsys fixed, fitted a tanh rotation curve to its points and subtracted the model from moment 1 |
| Disk kinematics needing emission height, planet kinks or pressure bumps | Fitted peak velocity (bettermoments quadratic) plus eddy / disksurf fits (2024ApJ...974..102S, 2020ApJ...891...48H) |
| Line flux of an unresolved or barely resolved source | An aperture spectrum with a Gaussian fit (2026A&A...705A..81K, 2024A&A...682A.166F) or a uv-plane fit are alternatives to integrating moment 0. Whichever you use, state and check the aperture, velocity window, noise estimate and recovered flux (2024A&A...682A.166F used a 0.7 arcsec aperture said to hold 99% of the flux and rechecked non-detections with other apertures and channel binning) |
| Infall versus rotation in envelopes | PV diagrams along chosen PAs (2018PASJ...70...85T, 2015ApJ...815..106H) |
| Many weak transitions of one species | Stack transitions or spectra (inverse-variance stacking of moment maps in 2019ApJ...871..112X; Keplerian-shifted stacking in 2016ApJ...832..204Y) |

## Steps

1. **Start from a clean, continuum-subtracted cube.**
   - Continuum subtraction is the most common unstated setting: the pack aggregates list line-free channels or
     continuum subtraction as not stated in well over 100 card entries. Record the line-free ranges and fit order.
     STATCONT is one alternative (2 papers in aggregates) but is "not optimal for spectral lines close to the
     noise level" per 2021A&A...656A..46M.
   - Weighting: Briggs robust 0.5 is the most common stated choice for line cubes (12 papers in my count of pack
     parameter lines, e.g. 2014ApJ...783L..13P, 2016ApJ...828...46A, 2019ApJ...881...10B, 2025ApJ...984L..19Y).
     Natural weighting is used for faint lines (2018A&A...617A..23B, 2020MNRAS.493.4294B, 2025NatAs...9.1476C);
     robust 1-2 for the faint isotopologues (2020ApJ...889L..24P: robust 1.0 for 12CO, 2.0 for 13CO and C18O).
   - Channel width: set by science. Disks: 0.16-0.25 km/s (2018ApJ...868..113T, 2017MNRAS.465..834Z,
     2025ApJ...984L..19Y). Nearby galaxies: a few to ~10 km/s (3.8 km/s in 2025ApJ...988...72S; 10.2 km/s in
     2019ApJ...881...10B for the NGC 3258 circumnuclear disk). Galactic Center circumnuclear disk: 5 km/s
     (2018PASJ...70...85T). High-z: 35-50 km/s (2020MNRAS.493.4294B 35 km/s at z = 8.31,
     2019ApJ...881...63N 50 km/s at z = 7.5).
   - JvM correction: 2024ApJ...974..102S applied it to its line maps (epsilon 0.71, 0.47, 0.33, 0.31 for 12CO,
     13CO, C18O, H2CO) and confirmed the results do not depend on it. That is one paper, not a rule tied to
     the number of configurations. General practice: apply it only when the restoring-beam and dirty-beam
     (residual) flux normalizations differ, derive epsilon for your own image product, and remember it
     rescales the residual noise, so measure the rms on the corrected cube and say which product you used.
   - Software: CASA `tclean` (CASA named in 180 matched steps, pack aggregates); GILDAS/MAPPING (7) and MIRIAD
     (12, names lower-cased in the aggregates) also appear.
2. **Measure the noise per channel.** Use line-free channels or emission-free regions. 2026A&A...705A..81K
   samples several emission-free regions per channel with the same size as the extraction aperture. Make the
   mask on a flat-noise map and measure flux on the primary-beam-corrected map (2018ApJ...867..140L).
   Record the velocity metadata at the same time: rest frequency, frame (LSR velocities are the usual
   choice, e.g. 2018ApJ...869...59W; barycentric in 2020ApJ...892...99C), Doppler convention (radio,
   nu_obs = nu_rest (1 - V/c), in 2018ApJ...866..117C) and the systemic velocity reference. When you import
   mask or model geometry from another paper, check its conventions: 2019ApJ...873...73Z defines inclination
   with edge-on = 0, the opposite of the usual face-on = 0.
3. **Choose the velocity window.** Patterns in the pack:
   - Fixed window around systemic velocity: +/-7 km/s (2018ApJ...853..147M), +/-12 km/s (2014ApJ...791L...6W),
     -140 to +140 km/s chosen because it gave the highest S/N and matched by-eye inspection (2020MNRAS.493.4294B),
     300 km/s windows per lens component (2018ApJ...867..140L).
   - Channels with significant signal only: "contiguous channels above 2 sigma, peak above 3 sigma"
     (2025NatAs...9.1476C); channels with >3 sigma summed (2019MNRAS.485..739M).
   - Broad window for complex-molecule maps, then a narrower one as a check (about 35 km/s in
     2024A&A...687A.163B; narrower gave consistent sizes and positions).
   - Blended lines: from -5 km/s of the lowest to +5 km/s of the highest velocity line (2018ApJ...857...35S).
   - Outflow lobes: separate blue and red ranges, excluding cloud-velocity channels (2021A&A...648A..41V;
     blue -400 to -120 and red +120 to 300 km/s in 2019A&A...632A..33A).
4. **Build the mask.** Pick one of the recipes below and state its parameters.

   | Recipe | Parameters seen | Papers |
   |---|---|---|
   | Per-pixel sigma clip (`includepix` in immoments, `-clip` in bettermoments) | moment 0: 3 sigma; moments 1-2: 4 sigma | 2016A&A...590A..73A, 2020A&A...640A.104A |
   | Smooth-and-mask (mask from smoothed cube, moments on unsmoothed cube) | beam-FWHM spatial + spectral smoothing (spectral kernel width not stated), 1.5 sigma | 2018ApJ...865...13T |
   | Same, heavier smoothing | 3x beam, Hanning over 5 channels, 1 sigma | 2025MNRAS.541.2540Z |
   | Same, Gaussian then Hanning | beam FWHM, then Hanning in velocity | 2019MNRAS.484.4239R |
   | Two-threshold (seed and grow) mask | 4 sigma seed, 2 sigma expansion, +10 km/s along velocity | 2025ApJ...988..162D |
   | Contiguous-channel mask (MASKMOMENT, PHANGS style) | >3 sigma in 2 contiguous channels | 2025ApJ...988...72S |
   | Source finder (SoFiA, 5 papers in aggregates) | 4 sigma on several smoothed cubes; merge 2 px / 3 chan; integrated S/N > 3 | 2019PASJ...71...85M |
   | Morphological cleanup | fill holes < 2 beams; drop islands < 1 beam | 2024MNRAS.527.9343L |
   | Keplerian mask (disks) | stellar mass, PA, i, centre from literature; vsys and line width tuned for S/N | 2017A&A...606A.125S, 2018A&A...614A.106C, 2020A&A...638A..38T, 2020ApJ...890..142P |

   - Keplerian masks: pad them for flared emitting layers (2019ApJ...876...72L) or enlarge the outer radius
     (1.5x in 2025ApJ...989....3D), and check the mask covers all the emission (2018ApJ...868..113T).
     2017A&A...606A.125S reports an S/N gain of about 2 from the mask. Local line width parameters
     r0 = 100 au, q = -0.3, v0 = 0.3 km/s are one published set (2020ApJ...890..142P).
   - Velocity-matched extraction is the same idea for a ring: per pixel, sum only the channels at the
     expected Keplerian velocity (2015MNRAS.447.3936M).
5. **Compute the moments.**
   - Moment 0: sum over masked channels times channel width. CASA `immoments` (12 mentions in pack aggregates
     across spellings, e.g. 2020MNRAS.493.4294B, 2026A&A...707A.120H). For flux, prefer an unclipped or
     signal-masked map over a hard per-pixel clip (2020ApJ...903..145L leaves moment 0 unclipped).
   - Velocity: intensity-weighted moment 1 is the default. The quadratic fit to the peak channel and its two
     neighbours (bettermoments) is used in the protoplanetary-disk examples here (2020ApJ...891...48H,
     2018ApJ...868..113T, 2024ApJ...974..102S), in debris disks (2026A&A...705A.198M) and also outside disks
     (2024ApJ...963....1O, a cool-core cluster). bettermoments is named in 31 matched steps (pack aggregates);
     that is a software count, not a count of papers using the quadratic estimator, so it does not show a
     majority. Gaussian fits per pixel are the other option (2018ApJ...853..147M; 2021ApJ...908..231M with 300
     Monte Carlo iterations for errors). 2024ApJ...974..102S compared moment 1, Gaussian and quadratic maps.
   - Velocity-map thresholds (7 papers, my count of pack parameter lines): 4 sigma (2016A&A...590A..73A,
     2020A&A...640A.104A, 2020ApJ...903..145L), 3-4 sigma by line (2024NatAs...8..587F), 3.5 sigma
     (2024ApJ...963....1O, 2026A&A...705A.198M), 2.5 sigma (2020MNRAS.493L.108B). The meaning differs and is
     often not stated: only 2026A&A...705A.198M says the cut blanks pixels whose spectral peak is below
     3.5 sigma; 2024ApJ...963....1O clips "all pixels with S/N < 3.5 sigma"; the others give a number without
     saying whether it is a per-voxel clip before collapsing or a per-pixel blank on peak S/N. Say which you use.
   - Moment 8 (peak intensity) maps per transition: 2019ApJ...871..112X made them only from transitions it
     selected as uncontaminated, stacked them, and still could not fix the AcA morphology because of spatial
     contamination. Before assigning a peak map to a species, confirm its velocity interval is free of other
     lines or decompose the spectrum. Peak brightness temperature through the full Planck function is used for
     debris disks in 2026A&A...705A.198M.
   - Moment 2: the intensity-weighted velocity dispersion (sigma). For a Gaussian, FWHM = 2.355 sigma; keep the
     two apart when comparing with fitted widths (2018ApJ...865...13T quotes FWHM 342 km/s and sigma 145 km/s
     for one component). Channel width and the spectral response also broaden it (general practice; the cards
     rarely state a correction for this, so say whether you made one). Treat it as an upper limit on intrinsic
     dispersion where rotation is unresolved (2019MNRAS.487..444R).
6. **Attach uncertainties and limits.**
   - General practice, per beam: for a moment 0 (Jy/beam km/s) summed over N independent channels of width
     dv with per-channel rms sigma, sigma_mom0 = sigma * dv * sqrt(N). With correlated channels (Hanning
     smoothing, oversampled channels) use dv * sqrt(sum_ij C_ij), where C is the channel covariance; the
     sqrt(N) form then underestimates the noise.
   - General practice, aperture flux: summing a Jy/beam km/s map over N_pix pixels gives Jy km/s only after
     multiplying by Omega_pix / Omega_beam. Pixels within a beam are correlated, so the noise of that sum is
     about sigma_mom0 * sqrt(N_pix * Omega_pix / Omega_beam) (the number of beams in the aperture), not
     sigma_mom0 * sqrt(N_pix). Better, measure it directly with blank apertures of the same size and window,
     as 2026A&A...705A..81K does per channel. The expression sigma_rms sqrt(npts) (pixel scale)^2 in
     2019PASJ...71...85M is for the error of their molecular-mass noise map, not a recipe for Jy/beam maps.
   - Calibration: report the statistical error and the absolute flux-scale uncertainty separately
     (2014ApJ...790..160S quotes +/-0.07 (rms) +/-0.07 (calibration) mJy; 2018PASJ...70...85T adopts 15%).
     2021A&A...656A..46M and 2020ApJ...892...99C note that their fit uncertainties exclude the calibration
     error. Cards flag flux-scale uncertainty as not stated in about 37 entries (14 + 11 + 5 + 4 + 3 across
     phrasings, pack aggregates). Add continuum-subtraction and fixed-parameter systematics where they matter.
   - Upper limits, as the papers did them (paper-specific, not portable defaults):
     - 2017AJ....153..240A: 3x image rms, integrated over +/-1 km/s of the known stellar velocity.
     - 2018ApJ...853..147M: spectra shifted by the CO moment-1 velocity and summed over the CO spatial mask;
       3 sigma limit reported as the filtered spectrum's rms times the number of independent channels across
       the CO line width. This assumes every molecule shares CO's spectro-spatial distribution; they checked
       the filter on the detected CO and also gave agnostic, unfiltered limits over the continuum region
       within +/-5 km/s. Adopt the recipe only with those assumptions and checks.
     - 2024A&A...682A.166F: integrated luminosity of a Gaussian with assumed FWHM 600 km/s and a peak equal to
       1 sigma. The 1 sigma is the assumed peak amplitude, not the confidence level of the integrated limit.
       Non-detections were rechecked with other apertures and channel binning.
     - 2024A&A...691A.178B gives a detection threshold only (non-detection if S/N < 3).
   - Upper limits, general form: k * dv * sqrt(sum_ij C_ij) over the assumed line width, with k the stated
     significance (3 is the usual choice in the examples above). State k, the assumed width, the extraction
     region and how the noise was measured.
   - Position uncertainty: about beam / (S/N) (2016A&A...592A..76D).
7. **Measure derived quantities.** Sizes and PAs from 2D Gaussian fits: CASA `imfit` on averaged, normalised
   moment-0 maps in 2020A&A...644A..84M; a 2D Gaussian fit to the moment-0 map for the PA in
   2014ApJ...784...78R (software not named). `imfit` is named 13 times (casa imfit 10 + imfit 3, pack
   aggregates). Radial profiles from azimuthal averaging (gofish, 8 mentions, pack aggregates).
   2021A&A...655A..80D made azimuthally averaged radial profiles and, separately, measured extents from the
   2 sigma moment-0 contours, binning the contour values with at least 10 samples per bin (angular ranges of
   at least 60 deg).
   Line luminosity and gas mass from moment 0 go to the gas-mass skill; examples here use alpha_CO 4.3 with
   R21 0.8 (2025ApJ...988...72S) and X_CO 2e20 (2019PASJ...71...85M).
8. **Fit the velocity field (optional).** eddy (6 mentions) for disks, 3DBarolo (2) and kinemetry (2) for
   galaxies (pack aggregates). Free parameters are usually centre, PA, inclination, vsys (2018ApJ...864..133T,
   2018ApJ...869L..50P); fix PA and inclination from continuum when the line is noisier (2020ApJ...891...48H,
   2024ApJ...974..102S). Exclude the inner beam: fit radii start at 1.5x beam major axis in
   2024ApJ...974..102S.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Weighting for cubes | Briggs 0.5 | -2 to 2, natural | 12 robust 0.5 (my count of pack lines) | 2014ApJ...783L..13P, 2019A&A...621A..83S (-2 and 2), 2018Sci...362.1034D (2) |
| Moment 0 clip | 3 sigma, or none with a signal mask | 1.5-5 sigma | ~8 (my count) | 2016A&A...590A..73A (3), 2017ApJ...840...60B (5), 2016ApJ...833L...6C (1.5, 2.5) |
| Moment 1/2 threshold | 4 sigma (higher than moment 0) | 2.5-4 sigma; voxel clip vs peak-S/N blank usually unstated | 7 (my count) | 2020A&A...640A.104A, 2020MNRAS.493L.108B, 2024NatAs...8..587F (3-4); peak-based only in 2026A&A...705A.198M (3.5) |
| Smoothing for mask | beam-FWHM spatial | 1-3 beams; spectral: Hanning (2 papers), 2-channel smoothing, or unstated | 4 (kernels as stated: beam FWHM + spectral, width unstated; beam FWHM then Hanning; 3 beams + Hanning over 5 channels; two-channel smoothing, kernel not named) | 2018ApJ...865...13T, 2019MNRAS.484.4239R, 2025MNRAS.541.2540Z, 2020A&A...640A.104A |
| Mask threshold on smoothed cube | 1.5-3 sigma | 1-4 sigma | 5 | 2018ApJ...865...13T (1.5), 2017ApJ...848L...7C (3), 2019ApJ...882...31A (~2x rms) |
| Velocity estimator | moment 1; quadratic peak in the disk examples | moment 1, quadratic, per-pixel Gaussian | bettermoments named in 31 matched steps (software count, not method frequency) | 2024ApJ...974..102S, 2020ApJ...891...48H, 2018ApJ...853..147M (Gaussian) |
| Keplerian mask M* | literature value | 1.65-2.3 Msun in examples | 4 | 2017A&A...606A.125S (2.3), 2018A&A...614A.106C (1.65) |
| Channel width | per science | 0.16 km/s (disks) to 50 km/s (high-z) | many | 2018ApJ...868..113T, 2019ApJ...881...63N |
| Detection rule | >=3 sigma in moment 0 and spectrum | 2.5-5 sigma | ~6 | 2020ApJ...898...97B, 2020ApJ...889...98M (3 sigma peak, 4 channels > 2 sigma, S/N > 5) |
| Upper-limit significance (integrated) | 3 sigma | 3 sigma stated in 2 | 2 (my count) | 2017AJ....153..240A, 2018ApJ...853..147M; not comparable: 2024A&A...682A.166F assumes a 1 sigma Gaussian peak, 2024A&A...691A.178B gives only an S/N < 3 non-detection threshold |
| eddy/emcee sampling | see examples | 48-64 walkers | 2 | 2020ApJ...891...48H: 48 walkers, 3500 steps total, first 500 discarded (3000 kept); 2024ApJ...974..102S: 64 walkers, 3000 burn-in steps then another 3000 kept |

Counts marked "my count" are from the pack's key-parameter lines, not the aggregates; most papers do not
state these settings, so they are lower bounds.

## Software

From the pack aggregates (mentions in matched analysis steps; names are lower-cased in the rebuilt pack, and
sub-task spellings are summed where noted). These count software mentions, not how often a method is used.

| Tool | Count | Used for |
|---|---|---|
| CASA (tclean, immoments, imfit, viewer) | 180 (immoments 10 + 2 = 12, imfit 10 + 3 = 13, tclean 4) | imaging, moments, Gaussian fits |
| bettermoments | 31 | quadratic peak velocity, clipped moments, peak intensity (2026A&A...705A.198M) |
| MIRIAD | 12 | moments for SMA and older data (2018ApJ...853..147M) |
| emcee | 10 | velocity-field and Keplerian fits (2018ApJ...868..113T) |
| GoFish | 8 | azimuthally averaged spectra and profiles |
| GILDAS | 7 | imaging and spectra (2019A&A...631A..78S) |
| AIPS | 6 | older reductions |
| eddy | 6 | disk rotation fits on velocity maps (2020ApJ...891...48H) |
| SoFiA | 5 | source finding and masks (2019PASJ...71...85M) |
| 3DBarolo, kinemetry, disksurf, CPROPS, spectral-cube, CARTA | 2 each | galaxy kinematics, emission surfaces, clouds, Python cube handling, viewing |

MASKMOMENT appears in 2025ApJ...988...72S for PHANGS-style masks; makeplots (Python) in 2018ApJ...865...13T.

## Pitfalls

- **Clipping bias.** A hard per-pixel clip removes faint emission and biases moment 0 low and moment 1 toward
  bright gas. Masking "removes faint diffuse emission" (2013ApJ...769L..12L). Use a smoothed or
  seed-and-grow mask, and compare total flux with an unclipped sum.
- **Missing flux.** Interferometer-only moment 0 underestimates extended emission: >6 arcsec structures in
  2013AJ....146...47I, >9.1 arcsec in 2014AJ....147..141H, lower-limit masses in 2016MNRAS.460..627K and
  2021A&A...648A..41V. Compare with single-dish flux where you can (2019PASJ...71...85M).
- **Foreground absorption.** Cloud absorption removed about 30% of 12CO on one side of AS 209
  (2018ApJ...868..113T); 2024NatAs...8..587F doubled the blue side to correct red-shifted absorption (an
  assumption, not a measurement). Mask or flag cloud-velocity channels (2021A&A...648A..41V).
- **Moment 1 on multi-component lines.** A single centroid averages components; papers switch to two- or
  multi-Gaussian fits (2013AJ....146...47I, 2018ApJ...865...13T, 2015ApJ...803...97S).
- **Moment 2 is not turbulence.** Beam smearing and rotation inflate it (2019MNRAS.487..444R); resolution
  limits velocity-shear modelling (2016NatAs...1E...3P).
- **Continuum subtraction errors** leak into moment 0 near bright continuum and at band edges
  (2017A&A...606A.125S: N2D+ "on the edge of a strong atmospheric feature").
- **Keplerian mask circularity.** Masks built from assumed M*, i, PA bias weak-line maps toward the model;
  2016ApJ...832..204Y notes the gain depends on an accurate Keplerian velocity and drops inside the beam.
- **Unstated settings.** Cards flag clipping thresholds (10), primary beam correction (19 across phrasings),
  CASA version (35) and line-free channels as not stated (pack aggregates). Do not infer them; ask or say so.
- **Optical depth.** Thick lines (12CO) trace temperature and surface, not column (2021A&A...648A..19W).
  Masses from an optically thin conversion applied to opaque emission are lower limits (2026A&A...705A.198M
  for CO in debris disks; 2014ApJ...783L..13P makes the same point for continuum vortex masses). Empirical
  alpha_CO / X_CO conversions are a different case: the factor itself is uncertain and may overestimate the
  mass (2025ApJ...988...72S, 2024ApJ...963....1O, 2018ApJ...865...13T), so quote that uncertainty separately.

## Verification checks

What the papers did:
- Vary the velocity window and confirm sizes and positions hold (2024A&A...687A.163B), or pick the window that
  maximises S/N and confirm by eye (2020MNRAS.493.4294B).
- Compare total flux with single-dish or other interferometers (2019PASJ...71...85M, 2014A&A...568A..92M,
  2018ApJ...853..147M).
- For fitted line maps, check recovered flux against the channel sum (about 97% in the worst cases in
  2021ApJ...908..231M).
- Re-run without the JvM correction (2024ApJ...974..102S) and compare velocity maps from different estimators
  (moment 1, Gaussian, quadratic: same paper).
- Check the PA or morphology across lines or transitions (2014ApJ...784...78R across CO(1-0) and CO(3-2);
  2019ApJ...871..112X across upper-level energies; 2016A&A...592A..76D positions within 8 mas across lines).
- Compare the modelled velocity field with the observed moment 1 (2020ApJ...890..167T); for a Keplerian fit
  to high-velocity channel maps, inspect residual channel maps and compare the fitted PA and inclination with
  the continuum (2018ApJ...869...59W); vary the inner fit radius to test residuals (2024MNRAS.534.2904C).

What a careful referee adds:
- Overlay the mask on channel maps and show that no emission falls outside it.
- Report moment 0 flux with and without clipping, and the rms map, not only a single rms value.
- State whether the moment maps and fluxes are primary-beam corrected and give the beam for every map.
- For velocity fields, show the S/N cut and how many pixels survive.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2017A&A...606A.125S (Keplerian masking, S/N gain)
- 2018ApJ...865...13T (smooth-and-mask moments, multi-Gaussian fits)
- 2019PASJ...71...85M (SoFiA masks, moment-0 error, single-dish check)
- 2024ApJ...974..102S (JvM, bettermoments, eddy and disksurf)
- 2020ApJ...891...48H (quadratic velocity map, eddy with emcee)
- 2018ApJ...868..113T (Keplerian mask, conical surface fit, absorption)
- 2026A&A...705A.198M (bettermoments clipping, peak Tb)
- 2025ApJ...988...72S (MASKMOMENT, 3DBarolo on moment 1)
- 2025ApJ...988..162D (two-threshold mask)
- 2020ApJ...903..145L (unclipped moment 0, 4 sigma for moments 1-2)
- 2020A&A...640A.104A (3 and 4 sigma clips, channel smoothing)
- 2021ApJ...908..231M (per-pixel Gaussian fits, flux recovery)
- 2020MNRAS.493.4294B (window chosen by S/N, immoments)
- 2024A&A...687A.163B (moment 0 for COM sources, window test)
- 2018ApJ...853..147M (velocity-shifted upper limits)
- 2020ApJ...890..142P (Keplerian masks across a disk survey)
- 2019MNRAS.487..444R (moment 2 as upper limit)
- 2021A&A...648A..41V (outflow lobe maps, cloud channels)
- 2019ApJ...871..112X (moment 8, inverse-variance stacking)
- 2025MNRAS.541.2540Z (heavily smoothed mask)

Off-topic papers in the pack (tagged by regex, ignored here): 2014ApJ...787..112C (Herschel HIFI survey),
2025ApJ...989..138S, 2026A&A...705A..97K and 2026ApJ..1003...65O (JWST-led studies).
