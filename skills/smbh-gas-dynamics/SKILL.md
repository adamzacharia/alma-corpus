---
name: alma-smbh-gas-dynamics
description: "Measure supermassive (and intermediate-mass) black hole masses from ALMA circumnuclear molecular gas kinematics: forward-model a CO line cube as a thin disk orbiting a point mass plus an MGE stellar potential (KinMS, KinMS_MCMC/GAStimator, emcee, AdaMet, dynesty, downhill simplex), with systematic-error budgets for distance, stellar M/L, gas mass, warps and turbulence. Also covers the quick alternatives seen in ALMA papers (CO line-width relation, CNN estimators, lens central-image limits) and the high-z M_BH/M_dyn comparison. Use when planning or checking a CO-dynamical M_BH measurement, judging whether the sphere of influence is resolved, choosing priors, noise rescaling and error budget, or reviewing someone else's M_BH fit. Built from 35 ALMA papers (2013-2025), about 25 on-topic."
---

# Supermassive black hole masses from molecular gas dynamics

Fits a model of a thin, rotating molecular gas disk in the combined potential of a central point mass and the
host's stars (and sometimes the gas itself) directly to an ALMA CO cube, and reads M_BH off the Keplerian rise
in the innermost velocities. The mistakes that matter most: (1) **not resolving the sphere of influence**, which
increases the degeneracy between M_BH and the stellar mass model (Gamma or M/L) and makes the result model
dependent (2020MNRAS.496.4061D, 2018MNRAS.473.3818D); it does not by itself make the result prior-dominated
(2020MNRAS.496.4061D still rejects both no-BH and >~1e6 Msun models), so test prior sensitivity before calling
it an upper limit; (2) **treating chi^2 as if pixels were independent**, which understates the uncertainties
unless the correlation is handled, either by modelling the covariance or by an empirical noise inflation
(2019ApJ...883..193N, 2024ApJ...975..179C, 2018MNRAS.473.3818D); (3) **forgetting that M_BH scales linearly
with the adopted distance**, which in several papers is the largest single error term (2025ApJ...992..211N,
2019ApJ...881...10B).

> Always report: tracer, beam and channel width, the radius where the BH dominates compared with the beam, the
> stellar mass model (band, MGE, dust correction), which parameters were free and their priors, the likelihood
> and how pixel correlation was handled, sampler and chain length, the fit region (shape and size), and a
> separate systematic error budget (distance, mass model, gas mass, turbulence model, warp). The cards often
> cannot recover these (see Pitfalls).

Counts below marked "pack count" are my own count of the paper excerpts in the evidence pack after dropping
off-topic papers; counts marked "aggregate" are the pack's software and settings aggregates. Values marked
"(card)" come from that paper's single methods card, not from the pack text; "card count" means I counted
across the nine full-fit cards listed under When to use.

## When to use

- A nearby early-type or spiral galaxy with a regular, dusty circumnuclear CO disk and an HST image for the
  stellar mass model: the core use case. Nine papers in the pack do a full cube fit for M_BH (pack count):
  2016ApJ...823...51B, 2018MNRAS.473.3818D, 2019ApJ...881...10B, 2019ApJ...883..193N, 2020ApJ...892...68N,
  2020MNRAS.496.4061D, 2024ApJ...975..179C, 2025ApJ...992..211N, 2025MNRAS.541.2540Z.
- Low-mass and intermediate-mass BHs in dwarfs when sub-parsec resolution is available (2020MNRAS.496.4061D:
  5.5e5 Msun in NGC 404 from a 0.051" x 0.026" beam (card)).
- Revisiting an earlier intermediate-resolution M_BH with longer baselines (2025MNRAS.541.2540Z,
  2025ApJ...992..211N, 2019ApJ...881...10B compares with its Cycle 2 fits).
- Feasibility and target selection: compute R_SoI = G M_BH / sigma_*^2 and the angular radius
  theta_SoI = R_SoI / D, with D the galaxy distance (radians when R_SoI and D share a length unit; multiply by
  206265 for arcsec), and keep targets with theta_SoI > 0.01" (2024MNRAS.527.9343L). Then estimate the time for
  S/N = 5 per beam in 10 km/s channels with the ALMA Observing Tool. That calculation (2024MNRAS.527.9343L,
  step 7) takes the central peak pixel, assumes homogeneous molecular gas within the central beam and a target
  beam about equal to theta_SoI; it gave about 70 days, 80 days and 100 years for three maser galaxies. Before
  relying on such a number, estimate the central surface brightness at the proposed resolution: clumpy gas or a
  central hole breaks the homogeneity assumption.
- Fixing M_BH from a prior measurement and fitting inflow or radial motions around it
  (2025A&A...700A.285W fixes log M_BH = 6.65 and fits radial velocities in 20 bins).

## When not to use

| Situation | Use instead |
|---|---|
| Galaxy-scale rotation curves, inclination, PA, dispersion or M_dyn of the whole disk | the `galaxy-3d-kinematics` skill (3DBarolo, tilted rings, M_dyn estimators) |
| High-z quasar hosts at kpc resolution: you only get M_dyn, not M_BH. Papers use M_dyn = 1.16e5 v_circ^2 d Msun (v_circ in km/s, d the physical disk diameter in kpc), v_circ = 0.75 FWHM / sin i (2016ApJ...816...37V, d = 1.5 x deconvolved size; 2018PASJ...70...36I, d = 1.5 a_maj; 2018ApJ...854...97D, i = 55 deg; 2017ApJ...845..138S from a rotation curve). The M_BH they compare with differs by paper: Mg II virial masses from the literature in 2016ApJ...816...37V (card) and 2017ApJ...845..138S; Mg II virial masses for two quasars and Eddington-limited masses for two others in 2018PASJ...70...36I (Eddington from the pack, Mg II from the card); minimum masses from the Eddington luminosity, i.e. lower limits, in 2018ApJ...854...97D | `galaxy-3d-kinematics` for M_dyn; quote M_BH from the optical/NIR paper and say whether it is virial, Eddington-based or a lower limit |
| Gas only marginally resolved, no Keplerian rise | expect strong M_BH-mass-model degeneracy; check the posterior against the prior and whether no-BH models are rejected before reporting a measurement, a prior-dominated value or an upper limit (2020MNRAS.496.4061D); 2013ApJ...770...13W only predicts M_BH from a line-width sigma via M-sigma |
| A quick number from an unresolved CO profile | the W50-inclination relation with Monte Carlo errors (2024ApJ...977..238B: log M_BH = 7.66 +0.21/-0.15); label it a scaling-relation estimate, not a dynamical mass |
| A strongly lensed source behind a massive elliptical | central-image non-detection in a lens model can give a lower limit, but only under an assumed central mass profile: 2015PASJ...67...72T gets M_BH > 3e8 Msun with r_core fixed to 150 mas and says BH mass and core radius are degenerate; 2015ApJ...811..115W prefers log M_BH >~ 8.5 for its R_core = 0.15" model. 2017ApJ...843L..35W models SDP.9 with Glee (core-radius and log M_BH priors) but finds no meaningful SMBH constraint from the non-detection (card). The bound is not model-independent; state the core model with it |
| Many galaxies, need a fast estimate | CNNs trained on simulated PVDs or moment-1 maps (2025A&A...693A.311P), but the authors trained one network per galaxy, so this is not a ready-made estimator for arbitrary galaxies: each new galaxy needs its own simulations and training. They also say the scatter is not a physical uncertainty and the simulations lack bars, clumps and misalignments |
| Water masers at sub-pc | VLBI maser disks; ALMA 321 GHz maser papers in the pack use M_BH as an input, not an output (2013ApJ...768L..38H, 2024PASJ...76..340K) |

Off-topic papers in the pack (regex matched "M_BH" but no gas-dynamical measurement): 2017ApJ...849...91M,
2020ApJ...897L..14Y, 2018A&A...617A..82B (single-epoch virial masses), 2019A&A...621A..83S (stellar M-sigma),
2019ApJ...879..117K, 2019ApJ...887...74F, 2020ApJ...891...64F, 2016ApJ...827...81I, 2019ApJ...872...69P,
2020ApJ...898...75I, 2020A&AT...31..423B. They are not used for recommendations below.

## Steps

1. **Check that the sphere of influence is resolvable.** Goal: know before fitting whether the data can
   measure M_BH. Method: R_SoI = G M_BH / sigma_*^2 from a prior M_BH (M-sigma) and the literature sigma_*;
   also R_eq, the radius where enclosed stellar mass equals M_BH (`mge_radial_mass` in JAM). 2025MNRAS.541.2540Z
   reports R_eq / R_beam of about 1.6 and calls its data the first to resolve the SoI of NGC 1574 (card);
   2024ApJ...975..179C quotes r_SOI = 0.12" (pack) with a 0.30" x 0.16" beam (card). If the beam is several
   times larger than R_SoI, expect M_BH to be degenerate with the stellar mass model and check prior sensitivity
   (2020MNRAS.496.4061D, 2016ApJ...823...51B).
2. **Calibrate and image the CO cube.** Goal: a cube with the finest beam that still has S/N per channel.
   Method (from cards): CASA `uvcontsub` on line-free channels (2018MNRAS.473.3818D); 2020ApJ...892...68N fits
   the continuum with a power law over the line-free bandwidth and subtracts it with `uvcontsub` from CASA 5.1.1
   (card; the same card says the CASA version used for imaging is not stated); 2025ApJ...992..211N applies its
   continuum self-calibration to the line SPW (card); `tclean` with Briggs robust 0.5 in 6 of the 8 full-fit
   cards that state a weighting (card count, see table). 2025MNRAS.541.2540Z chose robust 1.0 "after some
   trials" so the SoI stays resolved while keeping S/N (card). Combine long and short baseline tracks so that
   the extended disk is not resolved out (2020MNRAS.496.4061D images the long-baseline tracks and all tracks
   separately). Software: CASA. Self-calibration and continuum-fitting choices are dataset-specific: verify them
   on your own data.
3. **Build the stellar mass model.** Goal: the extended-mass circular velocity. Method: Multi-Gaussian Expansion
   (MGE) of an HST image, deprojected, scaled by a free M/L, circular velocity from `mge_vcirc` /
   `mge_circular_velocity` (2020ApJ...892...68N, 2025MNRAS.541.2540Z, 2025ApJ...992..211N,
   2019ApJ...883..193N). Correct for dust: 2019ApJ...881...10B builds dust-corrected MGEs and its M_BH spans
   (2.059-2.276)e9 Msun across models D1-D4; 2025MNRAS.541.2540Z uses `mge_fit_sectors_regularized` with a
   TinyTim PSF. Software: mgefit, JAM/JamPy, TinyTim.
4. **Model the gas surface brightness.** Goal: the flux weighting of the model cube. Method: an exponential disk
   (2019ApJ...883..193N, 2025MNRAS.541.2540Z; 2018MNRAS.473.3818D adds truncations and a plateau), or the
   observed moment-0 map deconvolved with 10 iterations of Richardson-Lucy (2019ApJ...881...10B,
   2024ApJ...975..179C), or SkySampler clouds drawn from the image (2020MNRAS.496.4061D, 2025ApJ...992..211N,
   which also tries two Gaussians: 2.34e9 vs 2.50e9 Msun).
5. **Forward-model the cube.** Goal: a model cube on the data grid. Method: thin disk, circular orbits,
   v_c^2(r) = G M_BH / r + v_*^2(r) (+ v_gas^2 if the gas mass matters), Gaussian line profiles with a turbulent
   sigma, convolved with the synthesized beam on an oversampled grid, then rebinned. Free parameters, typically
   9 to 13: M_BH, M/L (or Gamma), x_c, y_c, i, PA, v_sys, sigma_turb, flux normalisation, plus disk shape or
   warp terms (2019ApJ...881...10B, 2016ApJ...823...51B, 2025ApJ...992..211N nine; 2025MNRAS.541.2540Z eleven;
   2020ApJ...892...68N thirteen). Software: KinMS / KinMSpy, or a custom code (2019ApJ...881...10B,
   2024ApJ...975..179C; their code is not released).
6. **Fit.** Goal: posteriors for M_BH and M/L. Method: chi^2 likelihood over a stated fit region around the
   nucleus, an explicit treatment of correlated pixels (see Pitfalls), log-uniform prior on M_BH, an MCMC or
   nested sampler (table below). Two-step fits are common: a wide preliminary region first, then a small
   central region for the final fit (2018MNRAS.473.3818D 160x160 then 64x64 pixels; 2020ApJ...892...68N 4"x4"
   then 1"x1").
7. **Compare with no-BH and too-large-BH models and inspect residuals.** See Verification checks.
8. **Build a systematic error budget.** Goal: separate statistical and systematic errors. Method: refit with
   all free parameters while changing one assumption at a time (oversampling, block averaging, fit region,
   central gas hole, radial flow, turbulence profile, distance, gas mass) and add positive and negative shifts
   in quadrature (2019ApJ...881...10B: +-2.7e8 Msun, about 12%). For gas mass, test a range of plausible gas
   masses and CO-to-H2 conversions rather than a single alternative value: 2024ApJ...975..179C treats the gas
   as negligible, tests it, and still says its gas-mass systematic is likely underestimated. Report statistical
   and systematic separately, as 2024ApJ...975..179C (7.26 +0.43/-0.48 stat +0.55/-1.00 sys e8 Msun) and
   2025ApJ...992..211N (2.50 +-0.37 stat +-0.8 sys e9 Msun) do.
9. **Place on scaling relations.** Compare with M-sigma, M-M_bulge or M-M_* (2024ApJ...975..179C runs a
   10,000-iteration Monte Carlo offset test for six relic galaxies; 2025MNRAS.541.2540Z).

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| CO line | CO(2-1) | CO(2-1), CO(3-2) | 9 full-fit papers (pack count) | CO(3-2) in 2018MNRAS.473.3818D; CO(2-1) in 2019ApJ...881...10B, 2025MNRAS.541.2540Z |
| Imaging weight (line cube) | Briggs robust 0.5 | natural to robust 1.0 | robust 0.5 in 6 of the 8 full-fit cards that state a weighting (card count); 2020ApJ...892...68N does not state it | 0.5 in 2019ApJ...881...10B, 2024ApJ...975..179C, 2018MNRAS.473.3818D, 2016ApJ...823...51B, 2025ApJ...992..211N, 2020MNRAS.496.4061D (long-baseline cube; robust 0.1 for all tracks); robust 1.0 in 2025MNRAS.541.2540Z; natural and 0.5 in 2019ApJ...883..193N, which fits the natural cube (all card) |
| Channel width | about 10-20 km/s | 2 to 20.1 km/s | 8 cards state it (card count) | 2 km/s (2020MNRAS.496.4061D), 10 km/s (2018MNRAS.473.3818D, 2025ApJ...992..211N), 10.2 km/s (2019ApJ...881...10B), 19.9 km/s (2024ApJ...975..179C), 20 km/s (2025MNRAS.541.2540Z, 2019ApJ...883..193N), 20.1 km/s (2016ApJ...823...51B) (all card) |
| Beam | 0.1"-0.3" | 0.042" x 0.030" to 0.32" x 0.23" | 9 cards (card count) | 0.042" x 0.030" (2020ApJ...892...68N combined), 0.051" x 0.026" (2020MNRAS.496.4061D), 0.078" x 0.070" (2025MNRAS.541.2540Z), 0.12" x 0.09" (2019ApJ...881...10B), 0.30" x 0.16" (2024ApJ...975..179C), 0.319" x 0.233" (2016ApJ...823...51B) (all card) |
| Oversampling of model grid | s >= 4 | 4-6 | 2 | M_BH stable for s >= 4 (2019ApJ...881...10B); s = 6 (2024ApJ...975..179C) |
| Block averaging before chi^2 | 4x4 or 5x5 pixels | none to 5x5 | 3 | 2019ApJ...881...10B, 2024ApJ...975..179C, 2016ApJ...823...51B |
| Final fit region | central ~1" | see examples; give shape and whether the size is a radius, semi-axis or full width | 6 | radius r_fit = 1" (2019ApJ...881...10B); ellipse with semi-major axis 1.5", axis ratio 0.54 (2024ApJ...975..179C); radius 0.25" (2020MNRAS.496.4061D); 1.55" x 1.55" box, full width (2019ApJ...883..193N); 1" x 1" box (2020ApJ...892...68N); central 64x64 pixels (2018MNRAS.473.3818D) |
| Preliminary fit region | whole disk | 160x160 pixels, 4" x 4" box | 2 | 2018MNRAS.473.3818D, 2020ApJ...892...68N |
| M_BH prior | uniform in log M_BH | log 4.0-6.9 (dwarf) to 4.8-9.8 | 5 | 2018MNRAS.473.3818D, 2020MNRAS.496.4061D, 2020ApJ...892...68N, 2024ApJ...975..179C, 2025ApJ...992..211N |
| M/L or Gamma prior | flat; Gaussian when stellar kinematics constrain it | Gamma ~ N(0.61, 0.11) | 1 | 2020MNRAS.496.4061D |
| Inclination prior | flat over MGE-allowed range, or Gaussian | N(37, 3) deg | 3 | 2020ApJ...892...68N, 2020MNRAS.496.4061D; 2018MNRAS.473.3818D cross-checks flat in sin i |
| sigma_turb | free, constant | fixed 2.2 to 24.7 km/s | 5 | 12.9 (2020MNRAS.496.4061D), 11.3 (2025MNRAS.541.2540Z), fixed 2.2 (2018MNRAS.473.3818D), 24.7 (2016ApJ...823...51B); sigma_turb / v_c = 0.030 (2019ApJ...881...10B) |
| Correlated-pixel treatment | empirical inflation: multiply rms by (2N)^(1/4) (same as dividing chi^2 by sqrt(2N)) | N = 12,112 to 76,014 | 4 | N is counted differently: N_dof in 2019ApJ...883..193N; N = 36,376 pixels with detected emission in 2025MNRAS.541.2540Z, although it fits the full unmasked cube; N = 12,112 (factor 12.47) in 2020MNRAS.496.4061D, whose card says the pixel selection is not stated; N = 76,014 in 2025ApJ...992..211N. Alternative: analytic covariance in the central fit (2018MNRAS.473.3818D) |
| Chain length | 1e5-3e5 steps, 10-20% burn-in | 3e4 to 3e6 | 5 | 1e5 / 10% (2018MNRAS.473.3818D), 3e5 / 10% (2020MNRAS.496.4061D), 2e5 / 1e4 (2025MNRAS.541.2540Z), 1e5 / 20% (2025ApJ...992..211N), 3e6 / 20% (2020ApJ...892...68N) |
| Quoted interval | 68% plus a wide interval; state which | 68/99%, 68/99.7%, 16/84 + 0.2/99.8 (called 3 sigma), Delta chi^2 < 9 | 5 | 68/99% credible (2018MNRAS.473.3818D, 2020MNRAS.496.4061D); 68/99.7% (2024ApJ...975..179C); 16/84 and 0.2/99.8 percentiles (2020ApJ...892...68N); residual < chi^2_min + 9 (2019ApJ...883..193N). Do not relabel a 99% interval as 3 sigma |
| Gas mass in potential | include, or test over a plausible range | negligible to 4e8 Msun | 3 | included (2020MNRAS.496.4061D); tested, systematic likely underestimated (2024ApJ...975..179C); two gas masses (2019ApJ...883..193N) |

## Software

From the pack aggregates (counts are matched analysis steps, not papers):

- **KinMS** (aggregate 6; plus KinMS_MCMC 2, KinMS_fitter 1, KinMSpy_MCMC 1): forward-models the cube from a
  surface brightness profile and circular velocity curve (2018MNRAS.473.3818D, 2019ApJ...883..193N,
  2020MNRAS.496.4061D, 2020ApJ...892...68N, 2025A&A...700A.285W, 2025ApJ...992..211N, 2025MNRAS.541.2540Z).
  This is the WISDOM and MBHBM* project toolchain.
- **SkySampler** (aggregate 3): samples gas clouds from the observed intensity map (2020MNRAS.496.4061D,
  2025A&A...700A.285W, 2025ApJ...992..211N).
- **Samplers**: GAStimator Gibbs MCMC with adaptive stepping (aggregate 1; 2025MNRAS.541.2540Z; same method in
  2018MNRAS.473.3818D, 2020MNRAS.496.4061D), emcee (aggregate 1; 2020ApJ...892...68N), AdaMet (aggregate 1;
  2025ApJ...992..211N), dynesty nested sampling (aggregate 1; 2024ApJ...975..179C), mpfit then a grid
  (aggregate 1; 2019ApJ...883..193N), downhill simplex (IDL amoeba in 2016ApJ...823...51B; custom in
  2019ApJ...881...10B).
- **Stellar mass model**: MGE (`mge_fit_sectors_regularized` and TinyTim for the HST PSF in
  2025MNRAS.541.2540Z), JAM `mge_vcirc` (aggregate 2; 2020ApJ...892...68N, 2025MNRAS.541.2540Z), JamPy
  (2025ApJ...992..211N), MGE for an enclosed stellar mass (2020ApJ...898...75I uses it to subtract M_* and M_BH
  from M_dyn, an off-topic use).
- **Richardson-Lucy deconvolution** of the CO intensity map: IRAF STSDAS `lucy` (2019ApJ...881...10B),
  scikit-image (2024ApJ...975..179C).
- **Lens route**: Glee (aggregate 3) and glafic (2015ApJ...811..115W, 2017ApJ...843L..35W, 2015PASJ...67...72T).
- **ML route**: Keras CNNs (aggregate 2; 2025A&A...693A.311P).
- **Planning**: ALMA Observing Tool (2024MNRAS.527.9343L).

## Pitfalls

- **Unresolved Keplerian rise.** 2020MNRAS.496.4061D says it does not resolve the Keplerian increase, so the
  result depends on the stellar mass model and Gamma, and it advises caution on its low Gamma; it still rejects
  no-BH and >~1e6 Msun models. So poor resolution raises degeneracy and model dependence; whether the result is
  prior-dominated has to be checked (posterior vs prior, prior-sensitivity refits), not assumed.
  2016ApJ...816...37V: inclination and peak velocity cannot be separated at its resolution.
- **Central gas hole.** If CO is missing inside R_SoI, M_BH becomes sensitive to stellar mass modelling
  (2018MNRAS.473.3818D).
- **Correlated pixels.** The residual "is not equivalent to" chi^2 (2019ApJ...883..193N); chi^2_nu is
  underestimated after down-sampling (2024ApJ...975..179C); beam correlations neglected (2020MNRAS.496.4061D);
  2025MNRAS.541.2540Z assumes a diagonal covariance. Two distinct remedies appear: modelling the covariance
  (2018MNRAS.473.3818D uses an analytic covariance in its central fit; 2016ApJ...823...51B tried a covariance
  matrix and it failed) and empirical inflation of the noise by (2N)^(1/4) (see table). Inflation rescales the
  error bars but does not reconstruct the covariance, and its result depends on how N is counted, so state N
  and the mask that defines it. Use one approach, not both, and say which.
- **Distance.** M_BH is proportional to the angular size distance (2019ApJ...881...10B,
  2024MNRAS.527.9343L). 2025ApJ...992..211N: 69.3 vs 46.4 Mpc gives about 30% in M_BH, its dominant error;
  2019ApJ...881...10B: other distances put M_BH at (2.0-3.8)e9 Msun; 2025MNRAS.541.2540Z leaves its 10%
  distance error out of the budget. State the distance and scale M_BH if it changes.
- **Gas mass.** A single included or tested gas mass is not a full uncertainty budget: 2024ApJ...975..179C says
  its gas-mass systematic is likely underestimated, and 2019ApJ...883..193N notes its gas masses are lower
  limits because short baselines are missing.
- **Poor fits still return a best value.** 2016ApJ...823...51B had chi^2_nu = 4.4 and could not derive
  meaningful confidence limits (only "about (4-8)e8 Msun"); 2019ApJ...881...10B notes chi^2_nu = 1.179 is not
  formally acceptable. Inadequate warp, turbulence or surface brightness models are the usual causes.
- **Turbulence model.** In 2016ApJ...823...51B M_BH moved from 6.02e8 (free flat sigma_turb = 24.7 km/s) to
  8.0e8 Msun (sigma_turb = 10 km/s).
- **Warps and non-circular motion.** Most fits assume circular orbits in a thin disk (2019ApJ...883..193N,
  2020ApJ...892...68N, 2025MNRAS.541.2540Z, 2025ApJ...992..211N). Model warps explicitly when the PA or i
  twists (2024ApJ...975..179C tilted ring and linear twist, 2025MNRAS.541.2540Z linear PA warp).
- **Missing flux.** Without short baselines, gas masses are lower limits (2019ApJ...883..193N); combine
  configurations (2020MNRAS.496.4061D).
- **Dust and M/L gradients.** A spatially uniform M/L is usually assumed (2019ApJ...881...10B,
  2025MNRAS.541.2540Z); 2018MNRAS.473.3818D fits separate inner and outer M/L.
- **Lens limits are model-conditional.** Central-image bounds depend on the adopted core radius
  (2015PASJ...67...72T: BH mass and core radius degenerate, r_core fixed to 150 mas; 2015ApJ...811..115W:
  bound quoted for R_core = 0.15").
- **Unreported settings.** The cards often lack line-free channel ranges for `uvcontsub` (listed 9 times in the
  pack's not-stated aggregate), clean masks and thresholds, sampler settings (dynesty live points in
  2024ApJ...975..179C; mpfit grid spacing in 2019ApJ...883..193N), and some modelling codes are unpublished
  (2019ApJ...881...10B, 2024ApJ...975..179C). Record all of these for your own fit.
- **High-z M_BH/M_dyn.** Not gas-dynamical BH masses. Inclination is the dominant unknown and is often left out
  of the error (2016ApJ...816...37V); M_BH systematics up to about 0.4 dex (2020A&A...637A..84P); low
  resolution may overestimate M_dyn (2018ApJ...854...97D); mixing virial, Eddington-based and lower-limit M_BH
  in one comparison mixes different quantities.

## Verification checks

What papers did:

- **No-BH and too-large-BH models.** Show PVDs for the best fit, M_BH = 0 and a too-large M_BH
  (2020MNRAS.496.4061D: no BH and >~1e6 Msun both fail; 2020ApJ...892...68N).
- **Residual maps.** Velocity-field and moment residuals, plus major- and minor-axis PVDs
  (2025ApJ...992..211N: |V_residual| <~ 15 km/s across the disk; 2025MNRAS.541.2540Z).
- **Model comparison by BIC.** Flat disk vs tilted ring vs linear twist, excluding Delta BIC >= +10
  (2024ApJ...975..179C); one- vs two-component warp (2025MNRAS.541.2540Z).
- **Reduced chi^2.** Values in the pack: 0.867 (2025ApJ...992..211N), 1.159 (2024ApJ...975..179C), 1.16
  (2020ApJ...892...68N), 1.179 (2019ApJ...881...10B), 2.14 (2025MNRAS.541.2540Z, improved from 2.37).
- **Numerical convergence.** Oversampling until M_BH stops changing (2019ApJ...881...10B); full-resolution vs
  block-averaged fits agree (2016ApJ...823...51B).
- **Fit-region and sampler cross-checks.** Refit within 1", rerun with emcee, flat priors in sin i and cos PA
  (2018MNRAS.473.3818D: same M_BH, errors about 1.5 times larger); inner and outer cubes give consistent
  parameters (2025A&A...700A.285W).
- **Mass-model tests.** Vary M/L (2019ApJ...883..193N tried 0.05, 0.5 and 5.0 with negligible change), gas
  mass, dust correction (2019ApJ...881...10B), surface brightness model (2025ApJ...992..211N).
- **Scaling relations.** Compare with M-sigma and M-M_* (2024ApJ...975..179C, 2025MNRAS.541.2540Z).

What a careful referee adds:

- Ask for R_SoI or R_eq in beams and the smallest radius probed by the PVD (2025MNRAS.541.2540Z gives
  R_min / R_eq = 0.37 (card)). If R_SoI is below the beam, the M_BH posterior should be shown against its
  prior and refit with a different prior range.
- Check that the correlated-pixel treatment is stated (covariance model or inflation, and how N was counted),
  and that statistical and systematic errors are quoted separately at stated probability levels.
- Check the distance used and whether its error is in the budget.
- Check that the gas-mass systematic covers a range of gas masses and conversion factors.
- Check that the gas fit region excludes outflows or absorption (2019ApJ...883..193N has both in NGC 1275).

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2019ApJ...881...10B: precision M_BH in NGC 3258, full systematic error budget, oversampling test.
- 2024ApJ...975..179C: warped disk, dynesty, BIC model selection, stat vs sys split.
- 2025MNRAS.541.2540Z: WISDOM, SoI resolved, GAStimator, noise rescaling, warp.
- 2025ApJ...992..211N: KinMS + SkySampler + AdaMet, distance as dominant systematic.
- 2020MNRAS.496.4061D: intermediate-mass BH, sub-pc beam, priors, unresolved Keplerian rise caveat.
- 2018MNRAS.473.3818D: KinMS_MCMC two-step fit, central hole, analytic covariance, emcee cross-check.
- 2020ApJ...892...68N: emcee, 13 parameters, systematics tests, PVD checks.
- 2019ApJ...883..193N: mpfit plus grid, Delta chi^2 < 9 errors, M/L insensitivity.
- 2016ApJ...823...51B: failure case, poor fits and turbulence dependence.
- 2024MNRAS.527.9343L: SoI target selection and observing time.
- 2025A&A...700A.285W: inner/outer KinMS fits with M_BH fixed.
- 2025A&A...693A.311P: CNN M_BH estimates, one network per galaxy.
- 2024ApJ...977..238B: W50-inclination relation.
- 2015ApJ...811..115W, 2015PASJ...67...72T: lens central-image limits under fixed core models.
- 2020A&A...637A..84P, 2017ApJ...845..138S: high-z M_BH-M_dyn comparisons.
