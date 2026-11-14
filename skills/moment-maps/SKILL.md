---
name: alma-moment-maps
description: "Make and interpret moment maps from ALMA line cubes: integrated intensity (moment 0), intensity-weighted or fitted velocity (moment 1, quadratic peak velocity), dispersion (moment 2) or effective width, peak intensity (moment 8) and peak brightness temperature, with the masking, clipping, velocity windows and uncertainty handling that published ALMA papers use. Use when collapsing a cube into maps, measuring integrated line fluxes or upper limits, building velocity fields for kinematic fits (eddy, 3DBarolo, kinemetry), or checking someone else's moment maps. Built from 1087 ALMA papers (2012-2026)."
---

# Moment maps and line imaging products

Collapses a line cube into 2D maps: moment 0 (integrated intensity, Jy/beam km/s), moment 1 (velocity),
moment 2 (intensity-weighted velocity dispersion, sigma not FWHM), moment 8 or peak brightness temperature.
Every map depends on three choices: the **velocity window**, the **mask or clip** and the **velocity
estimator**. The two mistakes that matter most: (1) clipping moment 0 with a hard per-pixel sigma cut and then
quoting it as a total flux, which drops faint extended emission (2013ApJ...769L..12L; some papers leave moment
0 unclipped or only signal-masked and clip only moments 1 and 2: 2020ApJ...903..145L, 2023A&A...677A..76P,
2024ApJ...964..190L), and (2) reading moment 2 as intrinsic turbulence when it also holds beam-smeared
rotation, thermal and bulk-motion broadening, unresolved hyperfine structure and multiple components
(2019MNRAS.487..444R, 2024ApJ...977...37N, 2026A&A...709A.173M).

> Always report: velocity window (or mask recipe), clip threshold for each moment and what it is applied to
> (voxel, peak or integrated S/N), channel width, rms per channel and how it was measured, weighting,
> whether maps are primary-beam corrected, rest frequency, velocity frame and Doppler convention, the
> systemic velocity adopted, and the absolute flux-scale uncertainty. The cards flag moment-map clipping
> thresholds as not stated in 18 card entries (10 + 8 across two phrasings) and primary-beam correction
> details in 23 (16 + 7), pack aggregates; writing these down already beats a good share of the literature.

## When to use

- A detected line needs a morphology map, total flux, sizes or radial profile (2016A&A...592A..76D,
  2020A&A...644A..84M, 2021A&A...655A..80D, 2025A&A...703A..15M).
- A velocity field for a rotation or Keplerian fit, dynamical mass, PA or inclination (2020ApJ...891...48H,
  2018ApJ...868..113T, 2025ApJ...988...72S, 2020ApJ...890..167T, 2022A&A...662A.121R).
- Weak disk lines where a Keplerian mask raises S/N (2017A&A...606A.125S, 2018A&A...614A.106C, 2021ApJ...911..150P).
- Outflow lobe maps (2021A&A...648A..41V, 2019A&A...632A..33A); line-ratio maps on a common beam, grid and
  mask (2024ApJ...971..176H, 2022ApJ...929..100K, 2024ApJ...977...37N).
- Integrated-flux upper limits (2017AJ....153..240A, 2018ApJ...853..147M, 2024A&A...682A.166F), and input
  maps for lens models or source extraction (2018ApJ...867..140L, 2014A&A...568A..92M, 2024A&A...687A.163B).

## When not to use

| Situation | Use instead |
|---|---|
| Several velocity components, self-absorption or broad wings along the same sightline | Per-pixel multi-Gaussian fits (1-3 Gaussians with BIC selection in 2021ApJ...908..231M; iterative Gaussian adding in 2018ApJ...865...13T), or channel maps and PV diagrams (2015ApJ...815..106H) |
| Intrinsic dispersion or rotation curve of a beam-smeared galaxy | Model the cube in 3D instead of reading moment 2 (3DBarolo named 19 times, 14 + 5 spellings, pack aggregates). 2021ApJ...908...19B fits the cube with a beam-convolved thin-disk model whose intrinsic flux map comes from Richardson-Lucy deconvolution of moment 0. 2021A&A...654A..37D found map-based velocities about a factor of 2 below its modelled values. What one paper actually did: 2025ApJ...988...72S ran 3DBarolo on the moment-1 map with stellar PA, inclination, centre and vsys fixed, fitted a tanh curve and subtracted the model from moment 1 |
| Disk kinematics needing emission height, planet kinks or pressure bumps | Fitted peak velocity (bettermoments quadratic) plus eddy / disksurf fits (2024ApJ...974..102S, 2020ApJ...891...48H, 2024ApJ...964..190L) |
| Line flux of an unresolved or barely resolved source | An aperture spectrum with a Gaussian fit (2026A&A...705A..81K, 2024A&A...682A.166F) or a uv-plane fit are alternatives to integrating moment 0. Check aperture, window, noise and recovered flux (2024A&A...682A.166F: 0.7 arcsec aperture said to hold 99% of the flux; non-detections rechecked with other apertures and binning) |
| Clumpy or irregular sources | Aperture photometry on moment 0 rather than a 2D Gaussian, which fits these poorly (2024A&A...686A.156D) |
| Infall versus rotation in envelopes | PV diagrams along chosen PAs (2018PASJ...70...85T, 2015ApJ...815..106H) |
| Many weak transitions of one species, or a weak line with a detected partner | Stack transitions or spectra (inverse-variance stacking of moment-8 maps in 2019ApJ...871..112X; Keplerian-shifted stacking in 2016ApJ...832..204Y), or a matched filter from the detected line (HCO+ as the N2H+ template in 2024ApJ...972...88L) |

## Steps

1. **Prepare the cube.**
   - Continuum: most moment maps use a continuum-subtracted cube. Line-free channels or method are the most
     common unstated setting (227 card entries, 13 phrasings, pack aggregates); record ranges and fit order.
     Archival pipeline cubes pick continuum channels from a joint moment 0 / moment 8 mask (above 5 and 4
     MAD) assuming about 19% line-free channels (2023PASP..135g4501H); check them against your line.
   - **Thermometry branch.** For peak-brightness temperatures also keep the unsubtracted cube:
     2024ApJ...964..190L took temperatures from the non-continuum-subtracted cubes so as not to underestimate
     line intensity toward strong continuum (its step 7).
   - Weighting: the corpus-wide median Briggs robust is 0.5 in nearly every field (stats README, 3498 cards).
     In this pack's listed key-parameter lines (360 papers listed, 369 truncated) robust 0.5 appears in 14
     and robust 2 or natural in 18 (my count): subset counts, not a ranking (`references/parameters.md`).
   - Channel width, set by science (selected examples): protoplanetary disks 0.11-0.43 km/s
     (2024ApJ...972...88L, 2024ApJ...964..190L); debris-disk CO 0.4-1.6 km/s (2025A&A...703A..15M); nearby
     galaxies 3.8-10.2 km/s (2025ApJ...988...72S, 2019ApJ...881...10B); Galactic Center CND 5 km/s
     (2018PASJ...70...85T); high-z 35-100 km/s (2020MNRAS.493.4294B, 2019ApJ...881...63N, 2021ApJ...921...97J,
     2022PASJ...74.1429T at 100 km/s).
   - JvM correction: 2024ApJ...974..102S applied it and found results do not depend on it;
     2024ApJ...964..190L warns it "can underestimate effective rms". General practice: apply it only when
     restoring-beam and residual normalizations differ, and measure the rms on the corrected cube.
2. **Measure the noise and record velocity metadata.** Use line-free channels or emission-free regions:
   regions matching the extraction aperture (2026A&A...705A..81K), 16-20 random off-source apertures
   (2022MNRAS.510.1148S, 2025A&A...703A..15M), 100 random background annuli (2022A&A...662A.121R), or images
   without the Keplerian mask (2024ApJ...975...72B). Make the mask on a flat-noise map and measure flux on the
   primary-beam-corrected map (2018ApJ...867..140L). Record rest frequency, frame (LSR usual, e.g.
   2018ApJ...869...59W; barycentric in 2020ApJ...892...99C), Doppler convention (radio in 2018ApJ...866..117C)
   and the systemic velocity. Check imported geometry conventions: 2019ApJ...873...73Z defines inclination
   with edge-on = 0.
3. **Check spectral coverage, then choose the velocity window.**
   - Confirm the cube covers the line and its wings before integrating or fitting. In 2021A&A...654A..37D one
     source's [CII] fell entirely outside the band and another was sampled only on its blue wing; in
     2026A&A...710A.390O part of 13CO(3-2) fell outside the spectral window for seven objects. Flag truncated
     fluxes and widths as lower limits or drop them.
   - Fixed (+/-7 km/s in 2018ApJ...853..147M) or fit-based: +/-2 sigma_V (2023MNRAS.519.2030H) to 3x FWHM
     (2020ApJ...903...34A); peak +/-1.4 sigma kept ~83% and needed a ~1.20 correction (2025A&A...694A.171M).
     S/N-maximising (2024A&A...686A.156D, 2020MNRAS.493.4294B) or significant channels only ("contiguous
     channels above 2 sigma, peak above 3 sigma", 2025NatAs...9.1476C). More in `references/parameters.md`.
   - Broad window then a narrower check (2024A&A...687A.163B: consistent sizes and positions). Narrow it to
     avoid a neighbouring line (2024A&A...688A.130H) or outflow wings (2020MNRAS.496.2790L). Outflow lobes:
     separate blue and red ranges excluding cloud velocities (2021A&A...648A..41V, 2019A&A...632A..33A).
4. **Build the mask.** Pick one recipe and state its parameters, including whose rms the threshold uses
   (2026ApJ..1005...94N quotes 0.5 sigma of the unsmoothed cube as 8 sigma of the smoothed one).

   | Recipe | Parameters seen | Papers |
   |---|---|---|
   | Per-pixel sigma clip (`includepix` in immoments, `-clip` in bettermoments) | set per paper | 3 sigma on moment 0 and 4 sigma on moments 1-2 after two-channel smoothing (2016A&A...590A..73A, 2020A&A...640A.104A, card); 3 sigma for all moments (2025A&A...699A..83A) |
   | Smooth-and-mask (mask from smoothed cube, moments on unsmoothed cube) | spatial 1-3 beams, often 1.5x beam; threshold 0.5-3 sigma | 2018ApJ...865...13T, 2021MNRAS.500.3802H, 2022MNRAS.512.1522D, 2026MNRAS.546f2269R, 2025MNRAS.541.2540Z (kernels per paper in `references/parameters.md`) |
   | Seed and grow (PHANGS style) | seed 3.5-5 sigma in 2-3 channels, grow to 1.5-3 sigma | 2024ApJ...971..176H (5 to 2), 2023A&A...671A...3J (3.5 to 2), 2019ApJ...876..141I (5 to 1.5), 2025ApJ...988..162D (4 to 2, +10 km/s, card), 2023ApJ...945...42B (5 to 3) |
   | Contiguous-channel mask (MASKMOMENT) | >3 sigma in 2 contiguous channels | 2025ApJ...988...72S |
   | 3DBarolo SEARCH | SNRCUT 3.5-4.5, GROWTHCUT 2-4.5, MINCHANNELS 2-3 | 2025A&A...693A..91L, 2025PASJ...77..432U, 2022NatCo..13.4574G |
   | Source finder (SoFiA, 6 in aggregates) | 4 sigma on smoothed cubes; integrated S/N > 3 | 2019PASJ...71...85M |
   | MAD-based per-spaxel channel selection | per spaxel, channels with S/N above ~5 MAD | 2021A&A...654A..24B |
   | Morphological cleanup | fill holes < 2 beams; drop islands < 1 beam | 2024MNRAS.527.9343L |
   | Keplerian mask (disks; keplerian_mask named 5 times) | M*, PA, i, centre from literature; vsys and line width tuned | 2017A&A...606A.125S, 2018A&A...614A.106C, 2020ApJ...890..142P, 2021ApJ...911..150P, 2024ApJ...964..190L |

   - A MAD threshold on the integrated map is a detection rule, not a channel mask: 2026A&A...706A.236M
     requires a moment-0 detection above 5 MAD and then extracts within the detected region.
   - Keplerian masks: pad them for flared layers (2019ApJ...876...72L) or enlarge the outer radius (1.5x in
     2025ApJ...989....3D), and check they cover all emission (2018ApJ...868..113T). 2017A&A...606A.125S
     reports an S/N gain of about 2. Published line-width laws differ in sign convention; see
     `references/parameters.md` before reusing one. Velocity-matched extraction does the same for a ring
     (2015MNRAS.447.3936M).
   - **Line ratios.** Matching masks and windows is not enough. Put every line on a common beam and grid with
     comparable spatial filtering: 2022ApJ...929..100K convolved to a 2.0 arcsec beam with a 10 klambda uv
     cutoff for ratios; 2024ApJ...971..176H uses one combined "combo" mask; 2024ApJ...977...37N used the same
     velocity range for all maps and judged a factor-of-four beam difference too large for a quantitative
     comparison.
5. **Compute the moments.**
   - Moment 0: sum over masked channels times channel width (CASA `immoments`, 64 mentions, 37 + 27
     spellings, pack aggregates). For flux, prefer an unclipped or signal-masked map over a hard per-pixel
     clip (2020ApJ...903..145L, 2023A&A...677A..76P, 2024ApJ...964..190L). Clipping only negatives
     (`includepix` from 0) biases a noisy sum high (general practice); papers do it where absorption overlaps
     (2024MNRAS.533..771R) or without saying why (2025ApJ...988..106H, 2024A&A...692A.155K), so say so if you do.
   - Velocity: intensity-weighted moment 1 is the default. The quadratic fit to the peak channel and its two
     neighbours (bettermoments) appears in the protoplanetary-disk examples (2020ApJ...891...48H,
     2018ApJ...868..113T, 2024ApJ...974..102S, 2022A&A...662A.121R), debris disks (2026A&A...705A.198M) and a
     cool-core cluster (2024ApJ...963....1O). bettermoments is named in 65 matched steps (pack aggregates), a
     software count, not a method frequency. Per-pixel Gaussian fits are the other option
     (2018ApJ...853..147M; 2021ApJ...908..231M with initial width 20 km/s, maximum 500 km/s and an S/N >= 3
     mask, and 300 Monte Carlo iterations for errors (card)). 2024ApJ...974..102S compared all three.
   - Velocity-map thresholds (35 papers enumerated in `references/parameters.md`): 4 sigma in 10, 3 sigma in
     9, 5 sigma in 3, others from 1.5x local rms (2025Natur.641.1137B) to integrated S/N > 10
     (2021ApJ...917...99Y). The meaning is often not stated. Three kinds appear: a per-voxel clip before
     collapsing (2014ApJ...788L..34P), a blank on the pixel's spectral peak (2026A&A...705A.198M at 3.5
     sigma, 2026MNRAS.552g1700S at 3 sigma) and a blank on moment-0 S/N (2021A&A...653A.111R,
     2023MNRAS.518.3183L, 2024ApJ...977...37N at 5 sigma). Say which.
   - Moment 8: 2019ApJ...871..112X made peak maps only from transitions it selected as uncontaminated and
     still could not fix the AcA morphology because of spatial contamination; confirm the velocity interval
     is clean or decompose the spectrum first. Peak brightness temperature through the full Planck function
     from bettermoments quadratic peaks: 2026A&A...705A.198M, 2024ApJ...964..190L.
   - Moment 2: intensity-weighted dispersion (sigma). For a Gaussian FWHM = 2.355 sigma; keep them apart
     (2018ApJ...865...13T quotes FWHM 342 km/s and sigma 145 km/s for one component). Channel width broadens
     it; the cards rarely state a correction (2014ApJ...794L..10Y corrected narrow widths for its 0.60 km/s
     resolution). A noise-robust alternative is the effective width sigma_v = I / (sqrt(2 pi) T_peak), equal
     to moment 2 for a Gaussian (2024ApJ...971..176H). Use matching units: I in K km/s with T_peak in K, or
     integrated and peak intensity from the same Jy/beam cube (general practice).
6. **Attach uncertainties and limits.**
   - Per beam, moment 0 over N channels of width dv with per-channel rms sigma: sigma_mom0 = sigma dv sqrt(N),
     N all channels in the window (2024ApJ...977...37N). With correlated channels use dv sqrt(sum_ij C_ij),
     C the channel covariance (general practice).
   - Aperture flux (general practice): summing a Jy/beam km/s map over N_pix pixels gives Jy km/s only after
     multiplying by Omega_pix / Omega_beam, and the noise scales with the number of beams, about
     sigma_mom0 sqrt(N_pix Omega_pix / Omega_beam). Papers use sqrt of the beams in the region
     (2024A&A...690A.255D, 2020MNRAS.499.5136C) or blank apertures of the same size and window
     (2026A&A...705A..81K, 2025A&A...703A..15M).
   - Calibration: report statistical and absolute flux-scale errors separately (2014ApJ...790..160S
     +/-0.07 (rms) +/-0.07 (calibration) mJy; 15% in 2018PASJ...70...85T; 5% Band 3 and 10% Band 6 in
     2022ApJ...929..100K). 2021A&A...656A..46M and 2020ApJ...892...99C say their fit errors exclude it; cards
     flag it as not stated in about 50 entries (18 + 16 + 9 + 7, pack aggregates).
   - Upper limits: k dv sqrt(sum_ij C_ij) over the assumed width, with k stated (3 in 9 papers in my count;
     galaxy examples assume 100-320 km/s). State k, width, region and noise method. Paper recipes are not
     portable defaults (caveats for 2017AJ....153..240A, 2018ApJ...853..147M, 2024A&A...682A.166F and
     2024A&A...691A.178B in `references/parameters.md`).
   - Position uncertainty: about beam / (S/N) (2016A&A...592A..76D, 2023MNRAS.519.2030H).
7. **Measure derived quantities.**
   - Sizes and PAs from 2D Gaussian fits (2D Gaussian 11 plus variants, pack aggregates): CASA `imfit` on
     averaged, normalised moment-0 maps (2020A&A...644A..84M); a 2D Gaussian fit for the PA in
     2014ApJ...784...78R. `imfit` is named 51 times (27 + 24, pack aggregates). Alternatives: curve-of-growth
     photometry in elliptical annuli (2022A&A...662A.121R, 2025A&A...703A..15M), or the half-peak area size
     theta_50 = 2 sqrt(A / pi), deconvolved as theta_S = sqrt(theta_50^2 - theta_beam^2) (2024MNRAS.533.1143M).
   - **Is it resolved?** Propagate size errors and compare with the beam. 2024MNRAS.533.1143M states that
     unresolved emission prevents morphological conclusions; 2021ApJ...914...36I found an extent only 1.7
     sigma from zero and adopted a 3 sigma upper limit. Report unresolved or insignificant extents as limits.
   - Radial profiles from azimuthal averaging (gofish, 20 mentions; 1/4-beam bins and a 30 deg wedge in
     2021ApJS..257....6G). 2021A&A...655A..80D measured extents from 2 sigma moment-0 contours, with at least
     10 samples per bin over angular ranges >= 60 deg. Velocity gradients from a plane fit to moment 1
     (2024ApJ...977...37N). Gas masses go to the gas-mass skill.
8. **Fit the velocity field (optional).** eddy (12 mentions) for disks, 3DBarolo (19) and kinemetry (5) for
   galaxies, emcee (17), pack aggregates. Free parameters are usually centre, PA, inclination, vsys
   (2018ApJ...864..133T, 2018ApJ...869L..50P, 2022A&A...662A.121R); fix PA and inclination from continuum
   when the line is noisier (2020ApJ...891...48H, 2024ApJ...974..102S). Start fit radii at 1.5x the beam
   major axis (2024ApJ...974..102S). Repeat at M* +/- 1 sigma (2022A&A...662A.121R). Sampler settings and
   3DBarolo ring widths per paper: `references/parameters.md`. A second fitter is a cheap check (DISCFIT
   against 3DBarolo in 2024A&A...691A.118K, which notes axisymmetric orbits miss a one-armed spiral and bias
   the inclination).

## Parameter defaults and ranges

Counts marked "my count" come from the pack's listed key-parameter lines (360 papers listed, 369 truncated),
plus cards where marked, so they are lower bounds. Per-paper lists: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Weighting for cubes | Briggs 0.5 (corpus median) | -2 to 2, natural | 14 robust 0.5; 18 robust 2 or natural (my count, subset) | 2014ApJ...783L..13P, 2019A&A...621A..83S (-2 and 2), 2018Sci...362.1034D (2) |
| Moment 0 clip | none, a signal mask, or 3 sigma | 0 (negatives only) to 5 sigma | 16 (my count) | 2016A&A...590A..73A (3), 2026MNRAS.551g1645K (5), 2026MNRAS.552g1700S (1), 2023A&A...677A..76P (none) |
| Moment 1/2 threshold | 4 sigma (10), 3 sigma (9) | 1.5x local rms to 5 sigma; integrated S/N up to 10 | 35 (my count) | 2022A&A...662A.121R (4), 2021A&A...653A.111R (3 on moment-0 rms), 2026A&A...705A.198M (3.5 peak) |
| Mask threshold on smoothed cube | 1.5-3 sigma | 0.5-3 sigma (say which cube's rms) | 11 | 2018ApJ...865...13T (1.5), 2017ApJ...848L...7C (3), 2022MNRAS.509.2920N (0.75) |
| Seed / grow thresholds | 5 then 2 sigma | seed 3.5-5, grow 1.5-3 | 5 | 2024ApJ...971..176H, 2023A&A...671A...3J, 2019ApJ...876..141I |
| Velocity estimator | moment 1; quadratic peak in the disk examples | moment 1, quadratic, per-pixel Gaussian | software count only | 2024ApJ...974..102S, 2020ApJ...891...48H, 2018ApJ...853..147M |
| Channel width | per science | 0.11 km/s (disks) to 100 km/s (high-z) | selected examples | 2024ApJ...972...88L, 2025A&A...703A..15M, 2022PASJ...74.1429T |
| Detection rule | >=3 sigma in moment 0 and in the spectrum or channels | 2.5-5 sigma; 5 MAD on moment 0 | examples | 2021ApJ...911..150P, 2020ApJ...889...98M, 2026A&A...706A.236M |
| Upper-limit significance (integrated) | 3 sigma | 3 sigma in 9 | 9 (my count) | 2017AJ....153..240A, 2018ApJ...853..147M, 2022MNRAS.510.1148S |

## Software

Mentions in matched steps (pack aggregates), not method frequencies; per-tool uses in `references/parameters.md`.
CASA 467 (immoments 37 + 27, imfit 27 + 24, tclean 40 + 6, uvcontsub 15); bettermoments 65 (quadratic
velocity, peak intensity); GILDAS 27, MIRIAD 17, AIPS 9; astropy 23, spectral-cube 17; GoFish 20; CARTA 14;
3DBarolo 19 (14 + 5), kinemetry 5, emcee 17, eddy 12; PHANGS-ALMA pipeline 6, SoFiA 6; keplerian_mask 5,
pvextractor 5, astrodendro 9. MASKMOMENT in 2025ApJ...988...72S; disksurf in 2024ApJ...974..102S.

## Pitfalls

- **Clipping bias.** A hard per-pixel clip biases moment 0 low and moment 1 toward bright gas; masking
  "removes faint diffuse emission" (2013ApJ...769L..12L). Use a smoothed or seed-and-grow mask and compare
  with an unclipped sum. Clipping negatives only biases high.
- **Missing flux.** Interferometer-only moment 0 underestimates extended emission: >6 arcsec structures in
  2013AJ....146...47I, >9.1 arcsec in 2014AJ....147..141H, lower-limit masses in 2016MNRAS.460..627K and
  2021A&A...648A..41V. Feathered data gave a 20-50% higher streamer mass in 2025ApJ...985..166K; dropping
  baselines under 60 m lost 9% of the flux in 2025A&A...703A..15M. Compare with single-dish flux where you
  can (2019PASJ...71...85M, 2017A&A...608A.134Y).
- **Foreground absorption.** Cloud absorption removed about 30% of 12CO on one side of AS 209
  (2018ApJ...868..113T) and affects 12CO in almost all the Taurus multiple-system discs (2022A&A...662A.121R).
  2024NatAs...8..587F doubled the blue side to correct red-shifted absorption (an assumption).
- **Moment 1 on multi-component lines.** A single centroid averages components; papers switch to
  multi-Gaussian fits (2013AJ....146...47I, 2018ApJ...865...13T, 2015ApJ...803...97S).
- **Moment 2 is not turbulence.** Before deriving turbulent dispersion, remove or bound: beam smearing and
  rotation (2019MNRAS.487..444R, 2025A&A...699A..83A, 2021A&A...654A..37D); thermal width and bulk
  velocity-gradient width, both subtracted in 2024ApJ...977...37N step 5; unresolved hyperfine structure
  (2026A&A...709A.173M treats widths as upper limits because hyperfine splitting was neglected); channel
  width. Compare dispersions only at matched resolution (2025A&A...699A..83A).
- **Brightness temperature is not automatically gas temperature.** 2024ApJ...964..190L equates them only
  under stated assumptions: optically thick lines in LTE that fill the beam. It warns that inner lines may
  become optically thin, and C18O gives only a lower limit. Check optical depth, excitation and beam filling
  first.
- **Optically thin conversions on thick lines.** Masses from an optically thin conversion applied to opaque
  emission are lower limits (2026A&A...705A.198M; 2014ApJ...783L..13P for continuum vortex masses).
  Empirical alpha_CO / X_CO factors are a different case: the factor is uncertain and may overestimate the
  mass (2025ApJ...988...72S, 2024ApJ...963....1O, 2018ApJ...865...13T).
- **Imaging artefacts.** A central [CII] dip was a cleaning artefact (2024A&A...686A.156D); 12-m-only data
  may hold artefacts at low velocities (2025ApJ...985..166K); JvM-corrected maps can understate the rms
  (2024ApJ...964..190L). Continuum-subtraction errors leak into moment 0 near bright continuum and band
  edges (2017A&A...606A.125S).
- **Blends.** Severe blends block a spatial analysis (2018A&A...615A.155H); map only unblended transitions
  (2024MNRAS.533.1143M) or split shared flux by assumption (halved in 2021A&A...651L...5V).
- **Keplerian mask circularity.** Masks from assumed M*, i, PA bias weak-line maps toward the model;
  2016ApJ...832..204Y notes the gain depends on accurate Keplerian velocities and is lower inside the beam.
- **Unstated settings.** Cards flag clipping thresholds (18), primary-beam correction (23), CASA version (54,
  or 104 with combined phrasings) and line-free channels (227) as not stated (pack aggregates). Do not infer
  them; ask or say so.

## Verification checks

What the papers did:
- Vary the velocity window and confirm sizes and positions hold (2024A&A...687A.163B); vary mask smoothing
  and check coherence of what survives (2022MNRAS.509.2920N).
- Compare total flux with single-dish or other instruments (2019PASJ...71...85M, 2014A&A...568A..92M,
  2018ApJ...853..147M); apply the same aperture to different array combinations (2024A&A...686A.156D).
- For fitted line maps, check recovered flux against the channel sum (about 97% in the worst cases in
  2021ApJ...908..231M (card)).
- Re-run without the JvM correction and compare moment 1, Gaussian and quadratic maps (2024ApJ...974..102S).
- Check PA or morphology across lines (2014ApJ...784...78R across CO(1-0) and CO(3-2); 2016A&A...592A..76D
  positions within 8 mas); compare line-map PA and inclination with the continuum (2025A&A...703A..15M,
  2022A&A...662A.121R).
- Compare the model velocity field with moment 1 (2020ApJ...890..167T); for a Keplerian fit to channel maps,
  inspect residual channel maps (2018ApJ...869...59W); vary the inner fit radius (2024MNRAS.534.2904C).
- Apply the same mask and velocity range to model cubes as to the data (2024A&A...687A.311A, 2024ApJ...972...88L).
- Confirm a moment-1 gradient in a PV diagram before calling it rotation (not confirmed for DC8187(W) in
  2024A&A...686A.156D); cross-check surface temperatures against peak-intensity profiles (2024ApJ...964..190L).
- Compare fitted sizes with the synthesized beam and call lines unresolved or marginally resolved when they
  are (validation aggregate; 2024MNRAS.533.1143M, 2021ApJ...914...36I).

What a careful referee adds:
- Overlay the mask on channel maps and show that no emission falls outside it.
- Report moment 0 flux with and without clipping, and the rms map, not only a single rms value.
- State whether maps and fluxes are primary-beam corrected and give the beam for every map.
- For velocity fields, show the S/N cut, what it is applied to, and how many pixels survive.
- For ratios, show the common beam, uv range and grid.

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2017A&A...606A.125S (Keplerian masking, S/N gain)
- 2018ApJ...865...13T (smooth-and-mask moments, multi-Gaussian fits)
- 2019PASJ...71...85M (SoFiA masks, moment-0 error, single-dish check)
- 2024ApJ...974..102S (JvM, bettermoments, eddy and disksurf)
- 2024ApJ...964..190L (Keplerian-masked moment 0, unsubtracted cubes for temperatures, peak Tb assumptions)
- 2020ApJ...891...48H (quadratic velocity map, eddy with emcee)
- 2022A&A...662A.121R (4 sigma quadratic maps, eddy at M* +/- 1 sigma, curve of growth, absorption)
- 2026A&A...705A.198M (bettermoments clipping, peak Tb)
- 2024ApJ...971..176H (PHANGS seed-and-grow combo mask, effective width)
- 2024ApJ...977...37N (moment-0 noise, thermal and bulk width subtraction, beam-size caveat)
- 2025ApJ...988...72S (MASKMOMENT, 3DBarolo on moment 1)
- 2021ApJ...908..231M (per-pixel Gaussian fits, flux recovery)
- 2024A&A...686A.156D (S/N-maximising window, aperture photometry, PV check)
- 2024MNRAS.533.1143M (half-peak size, unresolved emission caveat)
- 2021ApJ...911..150P (Keplerian masks and detection rule across a disk survey)
- 2025A&A...703A..15M (random-aperture noise, curve of growth, baseline-cut flux test)
- 2019ApJ...871..112X (moment 8, inverse-variance stacking)

Off-topic papers in the pack (tagged by regex, ignored here): 2014ApJ...787..112C (Herschel HIFI survey),
2025ApJ...989..138S, 2026A&A...705A..97K and 2026ApJ..1003...65O (JWST-led studies).
