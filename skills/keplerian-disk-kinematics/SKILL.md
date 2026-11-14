---
name: alma-keplerian-disk-kinematics
description: "Fit Keplerian rotation of disks in ALMA line data to measure central (stellar or protostellar) dynamical masses, disk inclination, position angle, systemic velocity, emission height and Keplerian radius, and to find deviations from Keplerian rotation. Covers velocity-map fits (bettermoments + eddy), forward modelling of channel maps or visibilities (RADMC-3D/LIME, pdspy, csalt, DISCMINER + emcee/dynesty), velocity-aligned stacking for faint disks, and PV-diagram rotation curves for embedded protostars. Use when a paper or task needs a dynamical mass from disk rotation, a Keplerian mask, Keplerian-shifted stacking, or checks on someone else's Keplerian fit. Built from 447 ALMA papers (2012-2026)."
---

# Keplerian disk kinematics and dynamical masses

Measures the central mass and disk geometry from the line-of-sight velocity pattern of a rotating disk,
v_los = sqrt(G M / r) cos(phi) sin(i) + v_sys for a thin disk (general practice). The two mistakes that matter
most: (1) **reporting M* without facing the mass-inclination and mass-distance degeneracies**: the
line of sight only constrains roughly M sin^2 i, and M scales linearly with the adopted distance
(2015ApJ...812...27A reports M* sin^2 i = 0.56 Msun; 2020ApJ...894...74B: "dynamical mass scales linearly
with distance"); and (2) **quoting the MCMC posterior width as the error**: in CQ Tau the formal error was
+-0.002 Msun while different model runs gave 1.47-1.65 Msun (2021A&A...648A..19W); in HD 142527 the mass moved
from 2.29 to 2.53 Msun with the fitted radial range (2021A&A...650A..59B); eddy errors "below 1%" were "likely
underestimated" because pixel correlation was ignored (2026A&A...705A.202M); and in DM Tau / MWC 480
systematics dominate over statistics (2020ApJ...895..109F).

> Always report: tracer and transition, rest frequency, velocity frame and convention, channel width and any
> spectral smoothing, distance (and its source), whether i, PA and centre are fixed (from what) or free,
> emission-surface assumption (thin, conical, flared), fitted radial range, noise model, sampler settings,
> convergence rule and priors, and an error budget that includes distance and model systematics.

Counts come from the pack aggregates (447 papers; 295 protoplanetary-disk, 189 star-formation, 158 astrochemistry,
33 debris-disk, 20 evolved-star tags, papers can carry several) or my own grep of pack lines, as stated. Many
tagged papers only use a Keplerian mask or Keplerian-shifted stacking for chemistry, so software counts overstate
how often masses are measured. "(card)" marks details from a single methods card, each matching a verbatim quote.
About 20 off-topic papers are ignored (listed at the end). Full parameter table: `references/parameters.md`.

## When to use

- Dynamical stellar mass of a Class II star from a resolved CO/13CO/C18O disk, for comparison with
  evolutionary tracks (2017ApJ...844..158S, 2021ApJ...908...46B, 2017ApJ...846L..26W, 2025ApJ...986L..11S).
  For 23 Upper Sco K/M stars, five track sets "consistently underestimate stellar mass by >~25%"
  (2025ApJ...994..214T, card).
- Protostellar mass and Keplerian disk radius in embedded (Class 0/I) sources from PV diagrams or uv-plane
  disk models (2017ApJ...849...56A, 2024A&A...690A..46S, 2018ApJ...864L..25O, 2015ApJ...812...27A;
  separate disks in the VLA 1623 multiple, 2024A&A...687A.308S).
- Disk geometry (i, PA, v_sys, centre) and emission height from velocity maps: 12CO with a conical surface
  (2018ApJ...868..113T), 12CO with a two-power-law surface (2019Natur.574..378T), HCO+ with a flared surface
  (2020ApJ...891...48H), CS first-moment maps for geometry only, with M* fixed at 0.65 Msun (2018ApJ...864..133T).
- Rotation curves and deviations from Keplerian (pressure bumps, spirals, vortices, warps, planets, meridional
  flows) (2018ApJ...868..113T, 2019Natur.574..378T, 2021A&A...650A..59B, 2021A&A...648A..19W,
  2012ApJ...757..129R, 2024MNRAS.534.2904C).
- Low-S/N survey disks where a mass is only reachable by velocity-aligned stacking (2018A&A...616A.100Y,
  2021ApJ...908...46B).
- Building a Keplerian CLEAN mask or Keplerian-shifted spectral stack for weak lines (2013ApJ...774...16R,
  2024ApJ...965..147B, 2021ApJ...908..141H, 2026A&A...705A.198M, 2024ApJ...976..258K).
- Gas in debris belts or disks around evolved stars (2016ApJ...829....6W, 2013ApJ...776...77K,
  2026A&A...705A.201B, 2026A&A...705A.202M, 2016A&A...596A..92K, 2017A&A...597L...5B).
- Massive (proto)star disks, keeping in mind the disk mass is not negligible (2025NatAs...9.1833L,
  2019A&A...622A.206M, 2018ApJ...860..119G).

## When not to use

| Situation | Use instead |
|---|---|
| Rotation in an infalling envelope, centrifugal barrier, infall-rotation transition, streamers | `envelope-kinematics-pv` skill. The pack shows these models (centrifugal barrier M = r_CB v_CB^2 / 2G in 2019ApJ...873...73Z; IRE/FERIA and streamline models in 2025SciA...11.4512O, 2025ApJ...985..166K) but they are not Keplerian disk fits; 2025SciA...11.6953M notes its IRE model "is insensitive to the central mass" |
| Galaxy rotation curves, circumnuclear disks, AGN gas, orbits around Sgr A* | `galaxy-3d-kinematics` skill (3D tilted-ring or kinemetry); the galaxy and Galactic Centre papers tagged here (2015ApJ...811...39I, 2020ApJ...902...99I, 2024ApJ...970...74P) are out of scope |
| Unresolved disk, single spectrum only | A Keplerian double-peak line profile fit gives at most M sin^2 i with an assumed radius; say so, or treat the mass as a limit (2020ApJ...896..127K: "lower limit because inclination is unknown") |
| Ionized disk plus wind traced by radio recombination lines | A dedicated non-LTE disk-plus-wind model, not a plain Keplerian fit: 2020ApJ...897L..33J needed MORELI with a Keplerian ionized disk and an expanding wind (see step 1) |
| Only the dust disk geometry is needed | Continuum visibility fitting (`uv-plane-fitting` skill), which several papers use to fix i and PA before the kinematic fit (2020ApJ...891...48H, 2024ApJ...974..102S, 2024A&A...692A.155K) |
| Gas mass or temperature is the goal | `radiative-transfer-modelling` / `gas-mass-co-conversion`; Keplerian fits mostly fix those as nuisance parameters |

## Steps

1. **Pick the regime and tracer.**
   - Class II disks: 12CO for geometry and emission height (optically thick, elevated surface), 13CO/C18O
     or CN closer to the midplane for masses (2018A&A...616A.100Y stacks 13CO and C18O 3-2, card;
     2021ApJ...908...46B stacks 13CO, C18O and CN, card, assuming "different molecules follow same Keplerian
     rotation"). 13CO and C18O gave velocities within 20-30 m/s of each other in HD 142527 (2021A&A...650A..59B).
   - Embedded protostars: C18O, SO, HCO+, C17O along the disk major axis (2015ApJ...812...27A C18O;
     2018ApJ...864L..25O SO; 2014ApJ...786..114L HCO+; 2024A&A...687A.308S C17O, assumed to trace only the
     rotationally supported disks). Avoid lines dominated by envelope or outflow.
   - Massive protostars: hot-core lines such as CH3CN (2025NatAs...9.1833L). RRLs need more than a Keplerian
     fit: 2020ApJ...897L..33J modelled H21alpha with the non-LTE code MORELI as a Keplerian ionized disk plus
     an expanding wind; the same model without a wind "does not reproduce" the high-velocity centroid
     deviations, some centroid positional errors are large at high velocities, and the RRL masers are
     variable. Carry those caveats into any RRL mass (central mass 15 Msun there).
2. **Calibrate, self-calibrate, subtract continuum, image the cube** (see `self-calibration`,
   `continuum-subtraction`, `imaging-choices`).
   - Verify the spectral axis before fitting or stacking: rest frequency, velocity frame (LSRK) and
     convention. 2013ApJ...774...16R found that "the transformation to the absolute sky frequency in the Band 7
     measurement set" from the SV team was incorrect; cards flag rest frequencies as not stated (pack
     aggregates, 3) and 2017A&A...597L...5B gives no velocity reference (card note in the pack).
     2019ApJ...883...22C binned all line windows to matching 334 m/s LSRK channels (card).
   - Channels: about 0.1 km/s for 12CO disk cubes (2016ApJ...823L..18H, 2025ApJ...989....1Z); 160 m/s in
     2018ApJ...868..113T. State spacing and resolution separately (2024ApJ...966...63Y uses a spacing of half the
     resolution) and any smoothing, which correlates channels (2-channel Hanning in 2013ApJ...776...77K).
   - Weighting: Briggs robust 0.5 in 16 of the 23 pack bibcodes that state a robust value (my grep; e.g.
     2018ApJ...864..133T, 2026A&A...705A.202M); 1.0 in 2024ApJ...976..258K and 2026A&A...705A..49Z, 0.6 in
     2021A&A...648A..19W; natural for sensitivity (2018ApJ...868..113T, 2013ApJ...774...16R).
   - CLEAN with a Keplerian mask: the `keplerian_mask` script is named in 20 matched steps (+3 as "keplerian
     mask", pack aggregates), typically seeded with literature M*, PA, i (2020A&A...638A..38T tunes v_sys and
     line width to maximise S/N; 2024ApJ...976..258K rescales literature geometry to the adopted distance).
     2018ApJ...868..113T first fits a moment map, then re-cleans with a mask built from that fit and checks it
     "encompass[es] the whole emission".
3. **Fix the geometry you can measure independently.** Many papers fix i, PA and centre from continuum
   visibility fits and leave M* and v_sys free (2020ApJ...891...48H; 2024ApJ...974..102S; 2024A&A...692A.155K;
   2025ApJ...986L..11S fixes i = 49.9 deg; 2019ApJ...880...69Y fixes PA 138 deg, i 47 deg); 17 pack bibcodes
   state a fixed inclination (my grep). 2019Natur.574..378T instead puts a tight Gaussian prior on i (46.7 +-
   0.1 deg). Centre on the continuum peak (2018ApJ...869...59W, 2018A&A...616A.100Y). Fixing i transfers any
   inclination error straight into M*; near face-on, compact disks make literature M*, i and PA uncertain
   (2024ApJ...973..135H).
4. **Choose the kinematic method.**

| Method | When | How papers do it |
|---|---|---|
| A. Velocity map + `eddy` | Resolved, bright disk (12CO/13CO/HCO+) | `bettermoments` quadratic or Gaussian velocity map, then `eddy` Keplerian model with emcee; flat or conical surface z = r tan psi (2018ApJ...868..113T), flared z = z0 (r/1")^psi with psi an exponent (2020ApJ...891...48H), two-power-law surface with 10 free parameters (2019Natur.574..378T); also 2021A&A...648A..19W, 2024ApJ...974..102S, 2026A&A...705A.201B, 2026A&A...705A.202M |
| B1. Forward model, M* free (dynamical mass) | Best dynamical masses; moderate S/N | Parametric flared, vertically isothermal LTE disk, ray-traced with RADMC-3D, Fourier-sampled at the data uv points, MCMC; M* free with disk structure as nuisance (2017ApJ...846L..26W, 2017ApJ...835...17M, 2016ApJ...818..156C, 2019ApJ...883...22C with DiskJockey, card). `pdspy` (RADMC-3D + galario) with emcee, 15 free parameters (2025ApJ...994..214T, card) or with dynesty nested sampling (2024A&A...687A.308S, card). `csalt` models visibility spectra in LSRK per timestamp, convolves with the correlator spectral response and uses a spectral-covariance likelihood (2026A&A...705A..49Z, card) |
| B2. Forward model, M* fixed (structure, temperature, turbulence) | Gas structure is the goal | Same machinery with a prescribed mass: M* = 2.3 Msun fixed in 2015ApJ...813...99F, M* = 1.7 Msun in 2018ApJ...854..130W, masses fixed in 2020ApJ...895..109F; DISKFIT least squares on visibilities in 2024ApJ...976..258K. These are not dynamical-mass measurements |
| B3. Channel-map model (DISCMINER) | Kinematic substructure, residual maps | Orientation, M*, v_sys, upper and lower surfaces, intensity, line width and line slope fitted to channel maps (2023A&A...674A.113I); exoALMA residual maps from DISCMINER models (2026ApJ..1000L..15F, card). Its uncertainty is purely statistical (2025ApJ...984L..13H) |
| C. Velocity-aligned stacking | Faint survey disks | Shift each pixel by -v_kep cos(phi) sin(i), stack, grid-search M*, PA, i, v_sys for maximum S/N of the stacked line (2018A&A...616A.100Y); 2021ApJ...908...46B maximises S/N over M* and v_sys with i, PA, position and distance fixed (card) |
| D. PV rotation curve | Embedded, near edge-on protostars | Mean positions or ridge/edge per channel along the major axis, single or double power law in log R-log V; Keplerian if index ~0.5; `SLAM` MCMC (2017ApJ...849...56A uses only pixels above 5 sigma for the mean positions; 2024A&A...690A..46S, 2015ApJ...812...27A). Ridge and edge fits bracket the mass (2024ApJ...966...32E, 2025ApJ...992...18P) |
| E. Tilted rings | Massive protostellar disks | `3DBarolo` on the cube, power-law fit of v_rot(r), Keplerian enclosed mass (2025NatAs...9.1833L, card); see step 8 for converting enclosed mass to M* |
| F. Visual model comparison | Complex systems, illustrative only | Grid or hand-tuned models vs channel maps and PV (2019ApJ...873...73Z, 2018A&A...614A.113H, 2018ApJ...865..131L compares 0.05-0.4 Msun curves by eye). Authors themselves say this gives no fit quality |

5. **Set up the fit.**
   - Preserve each paper's fixed/free split rather than a generic list. M* free: 2017ApJ...846L..26W (Mdisk,
     Rdisk, gamma, T0, q, xi, M*, v_sys, i, PA, offsets), 2017ApJ...835...17M (M*, i, PA, r_c, T10, q, Mgas,
     xi, v_sys, offsets) and 2024A&A...687A.308S (M*, M_disk, R_disk, gamma, T0, q, a_turb, i, PA, v_sys,
     x0, y0). M* fixed: 2018ApJ...854..130W (free Mdisk, r_c, gamma, T0, q, xi, v_sys, i, PA with
     M* = 1.7 Msun) and 2015ApJ...813...99F.
   - Fixed values seen: X_CO = 1e-4, mu = 2.37 (2017ApJ...846L..26W, 2018ApJ...854..130W, 2025ApJ...994..214T);
     gamma = 1 fixed in 2016ApJ...823L..18H, 2019ApJ...883...22C, 2020ApJ...895..109F, but fitted in
     2017ApJ...846L..26W and 2018ApJ...854..130W; xi = 0.01 km/s (2016ApJ...823L..18H, 2017NatAs...1E.130Z).
     Widen a prior when walkers pile at its edge (2025ApJ...994..214T widened q from [0,1] to [0,2]).
   - Restrict the radial range: fit 0.2-2" (2020ApJ...891...48H), 0.33-1.4" (2024ApJ...974..102S), or exclude
     the inner ~5 beams "to mitigate the spatial resolution bias" (2025ApJ...994...98F) or the inner 100 au
     (2021A&A...650A..59B). Vary r_min and r_max to see if results move (2024MNRAS.534.2904C,
     2021A&A...650A..59B).
   - Handle contaminated channels and sides: mask 4.0-7.5 km/s LSRK after checking cloud maps
     (2019ApJ...883...22C, card); exclude 23 contaminated channels (2016ApJ...818..156C, card) or drop
     cloud-absorbed ranges from the likelihood (2026A&A...705A..49Z, card); cut envelope velocities and
     uv < 100-200 klambda (2024A&A...687A.308S); model the absorption as a 3-parameter Gaussian
     (2024A&A...687A.188K); weight to the blueshifted side under redshifted self-absorption (2017ApJ...843...27L).
     The ~30% 12CO absorption on AS 209's western side (2018ApJ...868..113T) is an absorption measurement, not a
     channel-exclusion fraction.
   - Velocity-map S/N cut before fitting: 5 sigma (2017ApJ...840...60B, 2024MNRAS.534.2904C,
     2026A&A...705A.201B) or 2.5 sigma (2020MNRAS.493L.108B). This is an intensity threshold on which pixels
     enter the map; keep it distinct from the per-pixel velocity uncertainties used in the likelihood.
   - Use a noise model that matches the data. 2016MNRAS.460.2933M writes the likelihood "taking into account
     the number of independent beams in the image and the correlation between adjacent channels";
     2019Natur.574..378T uses "only spatially independent pixels, those at least a beam FWHM apart"; csalt
     treats the spectral covariance explicitly (2026A&A...705A..49Z, card); neighbouring annuli are correlated
     within a beam (2018ApJ...864..133T). Model the correlation or count effective independent samples, and
     match the model's channelisation and smoothing to the data. Pixel-by-pixel chi2 on an oversampled map
     shrinks the posterior (recommendation following these papers; 2026A&A...705A.202M gives it as the reason
     its eddy errors are underestimated).
6. **Sample.** emcee is the sampler named most often in the matched steps (35, pack aggregates), a count of
   mentions, not a validated default. Others: dynesty (2024A&A...687A.308S, card), Metropolis-Hastings with
   Gibbs sampling, 3 chains (2016ApJ...829....6W), DiskJockey's Julia sampler (2019ApJ...883...22C, card),
   Levenberg-Marquardt (2024ApJ...976..258K), chi2 grids (2013ApJ...776...77K). State a convergence rule:
   median change < 5% over the last 500 steps (2026A&A...705A..49Z), slope of log M* < 1% over the last 1000
   (2025ApJ...994..214T, card), autocorrelation ~1000 steps (2019ApJ...874..136S). Report 16th-84th
   percentiles (2021A&A...648A..19W) but treat them as a floor.
7. **Inspect residuals and rotation curves.** Subtract the best Keplerian model from the velocity map
   (2024MNRAS.534.2904C, 2021A&A...648A..19W, 2021A&A...650A..59B) or image residual visibilities as channel
   maps and look for 3 and 5 sigma features (2026A&A...705A..49Z, 2024A&A...687A.308S, cards). For v_phi(r)
   fit deprojected spectra in annuli of about a quarter beam (2018ApJ...868..113T with eddy + celerite GP;
   2019Natur.574..378T for v_phi, v_R and v_Z); 2026A&A...705A.202M re-ran eddy ten times with the orientation
   drawn from the Keplerian-fit posterior. exoALMA residual maps came from DISCMINER models
   (2026ApJ..1000L..15F, card). Before naming a cause, report that "velocity residuals are model dependent, and
   the appearance of a Doppler-flip is therefore also model dependent" (2024MNRAS.534.2904C, which varied r_min)
   and that unresolved features "will underestimate the true depth" (2018ApJ...868..113T). Beam smearing alone
   gives 20-80 m/s deviations in a pure Keplerian model at 0.3" (2021A&A...650A..59B). Residual morphology
   alone does not identify a planet, spiral, vortex or warp.
8. **Build the error budget and the reported mass.** Add distance uncertainty in quadrature
   (2017ApJ...846L..26W adds 20 pc at 140 pc) or fit it with a Gaia-parallax prior (2025ApJ...994..214T, card),
   compare runs with different surfaces, masks, tracers and radial ranges, and report the spread.
   2025ApJ...994..214T reports Delta chi2 intervals because standard-deviation errors were 2-3x smaller (card);
   2019Natur.574..378T found systematics 2-3 times the statistical errors on its velocities. A rotation curve
   measures the enclosed mass. Where the disk and surrounding gas are massive, report enclosed mass and stellar
   mass separately and say which gravity model was used: 2025NatAs...9.1833L finds M_cl = 7.6 +- 1.4 Msun
   enclosed, then M* = M_cl - M_disk - sum(M_gas) = 4.89 Msun (card).

## Parameter defaults and ranges

"Typical value" is the value most often reported in the pack lines, not an independently validated default.
"Supporting pack entries" is my count (grep) of distinct bibcodes in the pack's parameter, assumption and
excerpt lines that state the setting, not a paper-level prevalence. More rows (masks, priors, grids, PV
thresholds, gas structure, line widths) and full example lists: `references/parameters.md`.

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Channel width | 0.1 km/s (12CO disks) | 26 m/s to 1.7 km/s | 28 | 2016ApJ...823L..18H, 2018ApJ...868..113T (0.16), 2017ApJ...851..132C (0.4), 2026A&A...705A.201B (26 m/s) |
| Briggs robust | 0.5 | -1 to 2, natural | 23 robust + 3 natural | 2018ApJ...864..133T, 2021A&A...648A..19W (0.6), 2024ApJ...976..258K (1.0), 2026A&A...705A.198M (0.5 or 2) |
| Inclination | fixed from continuum or literature | prior or free | 17 fixed | 2020ApJ...891...48H, 2019A&A...625A.118K (51.7 deg); prior 2019Natur.574..378T; free 2017ApJ...846L..26W |
| Distance | Gaia (DR2, then DR3) | 59 pc to 6.7 kpc | 6 Gaia | 2018ApJ...862L...2F (59 pc), 2020ApJ...895..109F (DR2), 2026A&A...705A..49Z (DR3), 2021A&A...650A.142M (6.7 kpc) |
| Emission surface, 12CO conical | psi ~13-15 deg (z/r = tan psi ~0.23-0.27) | 13.1-15 deg | 2 | 2018ApJ...868..113T, 2013ApJ...774...16R |
| Emission surface, flared | z = z0 (r/1")^psi, psi an exponent | HCO+ z0 0.127", psi 0.81; 12CO/HCO+ z0 0.33", psi 0.76 | 3 | 2020ApJ...891...48H, 2021AJ....162...99F, 2019Natur.574..378T |
| Annulus width | 1/4 beam | 1/5 beam to 2x beam minor axis | 13 | 2018ApJ...868..113T, 2019Natur.574..378T, 2026A&A...705A.202M (20% beam) |
| Walkers / steps / burn-in | see examples | walkers 16-1000, steps 300-40,000 | 17 | 2020ApJ...891...48H (48/3500/500), 2021A&A...648A..19W (200/5000+5000), 2025ApJ...994..214T (200, burn >= 1000) |
| M* prior | broad uniform | U(0,5) Msun; 5-15 Msun massive | 5 | 2025ApJ...994...98F, 2019ApJ...884L..56T (0.1-2), 2019A&A...622A.206M |
| Turbulent broadening xi / v_turb | 0.01 km/s | n/a | 2 | 2016ApJ...823L..18H, 2017NatAs...1E.130Z |

Line widths (xi, intrinsic width, Doppler b, "turbulence") are not interchangeable: check sigma vs b
(sqrt(2) sigma) vs FWHM and whether thermal broadening is included before comparing (general practice).

## Software

Counts are matched steps naming the tool (pack aggregates). They show how often a tool is named, not how often
a method is used.

| Tool | Count | Used for |
|---|---|---|
| CASA (`tclean`, `uvcontsub`, `imfit`, `simobserve`) | 101 (+ tclean 24, casa tclean 7, uvcontsub 13, casa imfit 4) | calibration, Keplerian-masked imaging, synthetic observations of models (2020ApJ...893...51S, 2026A&A...705A.202M) |
| eddy | 39 | Keplerian fits to velocity maps, emission surfaces, rotation curves (2018ApJ...868..113T, 2019Natur.574..378T, 2021A&A...650A..59B) |
| emcee | 35 | sampling Keplerian and disk-model posteriors (2020ApJ...891...48H, 2025ApJ...994...98F, 2026A&A...705A.201B) |
| GoFish | 32 | Keplerian-shifted stacking and radial profiles for weak lines (2024ApJ...965..147B, 2024ApJ...976..258K); Kepler-correcting Stokes I and V for Zeeman fits (2021ApJ...908..141H, see Pitfalls) |
| RADMC-3D (+ radmc3dpy) | 29 | ray-traced line cubes for forward models and beam-smearing tests (2016ApJ...818..156C, 2017ApJ...846L..26W, 2021A&A...650A..59B) |
| bettermoments | 26 | quadratic or Gaussian velocity maps feeding eddy (2020ApJ...891...48H, 2026A&A...705A.202M) |
| keplerian_mask (+ "keplerian mask" 3) | 20 | Keplerian CLEAN and moment masks (2021A&A...648A..19W, 2026A&A...705A.198M) |
| LIME, RATRAN, MCFOST | 11, 3, 5 | line radiative transfer (LIME: 2012ApJ...757..129R, 2013ApJ...774...16R, 2018A&A...614A.113H) |
| VISIBLE | 9 | matched-filter detection of weak lines with Keplerian-mask templates (2024ApJ...976..258K); not a mass method |
| DISCMINER | 7 | channel-map Keplerian models and residual maps (2023A&A...674A.113I, 2025ApJ...984L..13H, 2026ApJ..1000L..15F card) |
| pdspy, galario, csalt, DISKFIT, vis_sample (+ vissample 2), DiskJockey | 5, 4, 3, 5, 4, 3 | uv-plane disk fits (pdspy: 2025ApJ...994..214T, 2024A&A...687A.308S, cards; csalt: 2026A&A...705A..49Z, card; DISKFIT: 2024ApJ...976..258K; vis_sample: 2016ApJ...823L..18H; DiskJockey: 2019ApJ...883...22C, card) |
| Miriad, GILDAS (+ iram-gildas 2) | 5, 5 | older imaging and PV work (2020ApJ...898...10T, 2019A&A...632L..12H) |
| FERIA, SLAM, pvextractor, celerite, MORELI, 3DBarolo, disksurf | 3, 3, 4, 2, 2, not in aggregates, not in aggregates | IRE models, PV rotation curves, PV cuts, GP rotation curves, non-LTE RRL disk-plus-wind models, tilted rings, surface extraction (2025SciA...11.4512O, 2024A&A...690A..46S, 2018ApJ...868..113T, 2020ApJ...897L..33J, 2025NatAs...9.1833L card, 2025ApJ...984L..10G) |

## Pitfalls

- **Mass-inclination degeneracy.** "The inclination and the stellar mass are degenerate" (2013ApJ...776...77K
  took i from the best-fit mass); inclination poorly constrained by the disk model (2015ApJ...812...27A,
  2017A&A...597L...5B, 2018A&A...616A.100Y); edge-on assumed to get a minimum mass (2017NatAs...1E.172L,
  2020ApJ...896..127K). Some masses are quoted without an inclination correction (2025A&A...694A..92B,
  2021A&A...650A.142M) or as M = 0.82 Msun / sin^2 i (2019ApJ...881..112O). If i comes from the continuum, say
  so and propagate its error.
- **Distance.** M is proportional to the adopted distance (2020ApJ...894...74B); several papers state the
  error excludes distance (2024ApJ...967...15K). Check that distances are Gaia-era for older papers.
- **Underestimated errors.** Posterior widths far below run-to-run scatter (2021A&A...648A..19W); eddy errors
  "below 1%" but "likely underestimated" because pixel correlation was ignored (2026A&A...705A.202M; also
  2026A&A...705A.201B); for a 0.99 Msun kinematic mass "the true uncertainties are closer to ~10%, due to
  systematics" (2025ApJ...991..176W, card); DISCMINER uncertainty is purely statistical (2025ApJ...984L..13H,
  pack assumption line); DISKFIT errors
  unreliable where parameters are strongly coupled (2024ApJ...976..258K); systematics from midplane
  temperature and flux calibration dominate (2020ApJ...895..109F); calibration uncertainty left out of the
  MCMC (2020ApJ...892...99C).
- **Radial range.** The fitted mass depends on which radii enter: 2.53 +- 0.04 (100-200 au), 2.29 +- 0.07
  (> 200 au) and 2.36 +- 0.07 Msun (adopted, 100-400 au) for the HD 142527 binary (2021A&A...650A..59B).
- **Spectral axis.** A wrong sky-frequency transformation (2013ApJ...774...16R) or an unstated rest frequency
  or frame shifts v_sys and misaligns stacks. Check it before fitting.
- **Pressure and self-gravity.** A rotation curve cannot separate large-scale pressure support from M*
  (2018ApJ...868..113T). In simulated ARKS observations with input 1.91 Msun, fits returned 1.93 Msun for the
  Keplerian and one pressure-supported model and 1.80 Msun for the other (2026A&A...705A.202M). Disk mass is
  usually neglected (2019ApJ...873...73Z, 2019A&A...622A.206M), which fails for massive disks (disk-to-star
  0.2-0.6 in 2025NatAs...9.1833L, card, where enclosed mass 7.6 Msun becomes M* = 4.89 Msun after subtracting
  disk and gas); 2024ApJ...970..153A fits stellar, pressure and self-gravity terms together.
- **Beam smearing.** Not corrected in the inner 90-100 au in 2018ApJ...864..133T. In 2025ApJ...994...98F the
  resolution bias on intensity/temperature "can extend up to 8 times the size of the beam" with intensity
  underestimated by up to 50%; for the mass fit the same paper excludes the inner ~5 beams. In
  2025ApJ...986L..11S EDDY on the moment-1 map gave 0.043 Msun while the 12CO visibility fit gave 0.092 Msun,
  and the authors note EDDY "does not take the beam convolution into account, which may result in smaller
  stellar mass" (card). Beam smearing plus pressure gradients could not be told apart from a vortex in HD 142527
  (2021A&A...650A..59B), and it flattens extracted v_phi, so the true profile "is likely steeper than the
  extracted one" and deviations are probably underestimated (2026A&A...705A.202M). 2024ApJ...970..153A corrects v_phi with mock-cube factors.
- **Emission height.** 2024MNRAS.534.2904C assumed elevated emission surfaces for four MAPS disks (GM Aur,
  HD 163296, IM Lupi, MWC 480) and flat Keplerian disks for the rest; it did not measure a mass or PA bias from
  that choice. As general modelling guidance, fitting an elevated tracer such as 12CO with a thin disk can
  shift the fitted geometry, so test a surface model. Thin-disk stacking can overestimate the mass: "the stellar
  mass could be overestimated by 20% to 30% with our method, when a disk is highly inclined (i = 80 deg)"
  (2021ApJ...908...46B, card, synthetic disks); the pack line for the same paper calls the scale-height effect
  small (<3%) under its adopted assumptions.
- **Residuals are model dependent.** Doppler-flips and other residual features depend on the subtracted model
  (2024MNRAS.534.2904C), and unresolved features are shallower than they really are (2018ApJ...868..113T).
- **Envelope, infall, jets.** Cannot distinguish infall+Keplerian from pure Keplerian at low S/N
  (2013A&A...560A.103M); embedded masses may be upper limits (2018ApJ...864L..25O) or confused by the jet
  (2024ApJ...961..228S); PV mean-position methods underestimate the break radius at low resolution
  (2015ApJ...812...27A); ridge fitting underestimates and edge fitting overestimates the mass
  (2025ApJ...992...18P); a proto-brown-dwarf candidate stayed "tentative" with 0.27-0.30 Msun from PV curves
  (2018ApJ...865..131L).
- **Missing flux and cloud contamination.** Missing large scales bias rotation at large radii
  (2014ApJ...796..131O; ~25% filtered in 2017A&A...597L...5B); foreground cloud absorption (2018ApJ...868..113T,
  2020ApJ...894...74B, 2024ApJ...969..165D, 2020ApJ...904L...6A), negligible in the central CO of a highly
  inclined disk (2021ApJ...908..250H).
- **Low S/N stacking.** Stellar mass can be overestimated for fluxes below about 400 mJy km/s
  (2018A&A...616A.100Y).
- **Stacking for polarisation.** Stacking red and mirrored blue sides "would destroy any Stokes V signal from a
  vertical magnetic field" (2021ApJ...908..141H). Keep red and blue sides separate when polarity matters, and
  fit only unblended parts of hyperfine lines: that paper used only the low-frequency part of line 5 and the
  high-frequency part of line 7.
- **Maser and RRL disks.** Keplerian-only models miss the wind; maser variability and large high-velocity
  centroid errors limit the mass (2020ApJ...897L..33J); 2D Gaussian centroids underestimate the maser disk size,
  giving a lower enclosed mass (2023ApJ...953L...6P).
- **Binaries and circumbinary disks.** The fit gives the total enclosed mass (2020ApJ...898...10T assumed
  equal masses totalling 0.5 Msun; the fitted Mstar in 2020ApJ...905...89Y is the total binary mass);
  circumbinary disks leave non-Keplerian residuals (2024MNRAS.534.2904C, 2020ApJ...905...89Y). Combine with RV
  orbits for component masses (2016ApJ...818..156C).
- **Conventions.** Inclination and PA conventions differ (2019ApJ...873...73Z defines edge-on as i = 0;
  2018A&A...614A.113H quotes i = 110 deg; 2024A&A...687A.311A measures PA to the blueshifted semi-major axis).
  Convert before comparing.
- **Hand-tuned models.** Many models are "not unique nor optimized" (2012ApJ...757..129R,
  2013ApJ...774...16R) or chosen by eye (2019ApJ...873...73Z, 2018A&A...614A.113H, 2018ApJ...865..131L). Do not
  quote them as fits.
- **Unstated settings.** Cards flag self-calibration intervals (24, plus variants), CASA version (23, plus
  variants), image and cell size (13), flux-scale uncertainty (7), line-free channels (more than 100 across
  phrasings) and rest frequencies (3) as not stated (pack aggregates). Write them down.

## Verification checks

What papers did:
- Recover a known mass from synthetic data: 0.99 +- 0.02 Msun for a 1 Msun model (2025ApJ...994...98F);
  1.93 Msun for a 1.91 Msun input after simobserve and tclean, processed like the data (2026A&A...705A.202M);
  tests on 30 blank-field synthetic images and 24 model disks for the stacking method (2018A&A...616A.100Y,
  card).
- Refit with different surface assumptions (flared, thin, no continuum subtraction): the three radial v_rot
  profiles are "consistent within 3 sigma of one another" (2018ApJ...868..113T). This validates the rotation
  curve, not the mass. 2019Natur.574..378T compared a parametric with a non-parametric surface and with Z1 = 0,
  and refit with v_R fixed to 0 ("no change" in v_phi).
- Refit with and without beam convolution and with velocity errors x10 (2021A&A...648A..19W).
- Compare radial ranges and fitting procedures: features "present independently of the exact fitting
  procedure" while the mass moved with radius (2021A&A...650A..59B).
- Compare image-plane and visibility-plane masses: 0.043 vs 0.092 Msun in 2025ApJ...986L..11S (card), so the
  check can fail; compare masses from different lines: "80% of the measurements from different line data agree
  on a level better than 1 sigma" (2021ApJ...908...46B, card); 12CO, 13CO and joint fits "all agree within
  uncertainties" (2025ApJ...994..214T, card); 13CO and C18O PV curves gave 0.27 and 0.30 Msun
  (2018ApJ...865..131L).
- Vary a fixed structure parameter: the dynamical mass "remained the same" for floating q, q = 0.50 and
  q = 0.75 (2019ApJ...883...22C, card); run the fit at the adopted M* and +-1 sigma (2022A&A...662A.121R).
- Test competing velocity laws: single vs double power law, reduced chi2 1.6 vs 4.0 (2017ApJ...849...56A);
  infalling-rotating envelope rejected (2018ApJ...864L..25O); pure Keplerian rejected (2019ApJ...873...73Z,
  and for the ARKS gas ring, 2026A&A...705A.202M); no-wind model rejected for an RRL disk (2020ApJ...897L..33J).
- Residual channel maps from residual visibilities, checked at 3 and 5 sigma (2026A&A...705A..49Z,
  2024A&A...687A.308S, cards); overlay isovelocity contours or model PV curves on channels
  (2020ApJ...891...48H, 2020ApJ...898...10T).
- Convergence: multiple chains agree, model matches data to ~10% (2016ApJ...829....6W); reduced chi2 0.72
  (2015ApJ...812...27A); explicit stopping rules (2026A&A...705A..49Z, 2025ApJ...994..214T card).
- Gas geometry vs continuum geometry: PA, i and offsets "consistent with those measured for the continuum"
  (2026A&A...705A.201B; also 2026A&A...705A.202M).
- Independent masses: SED fit (2019ApJ...873...73Z), earlier lower-resolution data (2025NatAs...9.1833L),
  stellar-model mass (2026A&A...705A.201B).
- Mask covers all emission (2018ApJ...868..113T); radial profiles also made without the Keplerian mask
  (2024ApJ...976..258K).

What a careful referee adds:
- Is the quoted error dominated by distance and inclination, and are those propagated?
- Does M* change when r_min, r_max, surface height or tracer change (2024MNRAS.534.2904C varies r_min;
  2021A&A...650A..59B shows it can)?
- Does the likelihood account for correlated pixels and channels (2016MNRAS.460.2933M, 2019Natur.574..378T),
  and does the model match the data's channelisation and smoothing?
- Were rest frequency, velocity frame and convention checked and reported?
- Were absorbed or cloud-contaminated channels excluded or modelled, and is the fit symmetric between red and
  blue sides?
- For embedded sources, is the fitted region inside the Keplerian radius and free of envelope/outflow, and
  was the mass from ridge or edge points?
- For massive disks, is the reported number the enclosed mass or the stellar mass?
- Is i from the gas consistent with i from the continuum (2025ApJ...986L..11S reports "consistent solutions of
  inclination and position angle to those from the continuum", card)?
- Was a convergence rule stated, and are residual features shown to survive changes to the subtracted model?

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2018ApJ...868..113T (eddy, conical surface, GP rotation curve, surface tests)
- 2019Natur.574..378T (eddy surface fit, independent pixels, 3D velocities, systematics vs statistics)
- 2020ApJ...891...48H (bettermoments + eddy on HCO+, fixed geometry, emcee settings)
- 2021A&A...648A..19W (eddy runs, underestimated errors, beam tests)
- 2021A&A...650A..59B (radial-range dependence of mass, beam smearing vs vortex)
- 2026A&A...705A.202M (eddy on a debris gas ring, recovery test, underestimated errors)
- 2025ApJ...986L..11S (image vs visibility masses for a brown dwarf)
- 2025ApJ...994..214T (pdspy uv fits for 23 stars, convergence rule, tracks vs dynamical masses)
- 2026A&A...705A..49Z (csalt with spectral covariance, cloud ranges excluded, stopping rule)
- 2024A&A...687A.308S (pdspy + dynesty for a protostellar multiple, channel and uv cuts)
- 2017ApJ...846L..26W (RADMC-3D + emcee visibility fit, M* free, distance in quadrature)
- 2016ApJ...818..156C (disk mass combined with binary RV orbit)
- 2019ApJ...883...22C (DiskJockey dynamical mass, cloud channels)
- 2021ApJ...908...46B (stacked survey masses, thin-disk bias)
- 2018A&A...616A.100Y (velocity-aligned stacking grid, low-flux bias)
- 2025ApJ...994...98F (recovery test, beam-bias correction)
- 2024ApJ...970..153A (pressure and self-gravity in v_phi)
- 2017ApJ...849...56A (PV double power law, Keplerian radius)
- 2024A&A...690A..46S (SLAM ridge and edge fits)
- 2015ApJ...812...27A (C18O disk model, M sin^2 i)
- 2016MNRAS.460.2933M (likelihood with independent beams and channel correlation)
- 2024MNRAS.534.2904C (residuals, r_min dependence, circumbinary)
- 2025NatAs...9.1833L (3DBarolo for a massive disk, enclosed vs stellar mass)
- 2021ApJ...908..141H (GoFish Kepler correction for Zeeman, stacking caveat)
- 2020ApJ...895..109F (systematics dominate)

Off-topic papers in the pack (regex-tagged, ignored here): 2013ApJ...768L..38H, 2015ApJ...811...39I,
2013PASJ...65..100I, 2020ApJ...902...99I and 2017MNRAS.468.1769F (galaxy nuclei and clouds);
2017ApJ...837...93Y, 2017ApJ...842...94T, 2017ApJ...850L...5T, 2019ApJ...871L...1T, 2020PASJ...72L...5T,
2024ApJ...970...74P and 2025A&A...704A...7P (Galactic Centre orbits and black holes); 2021AJ....162...14A
(stellar astrometry); 2019NatAs...3..408D (OH/IR binary); 2023PASJ...75..225M (HII region ring);
2024A&A...689A..85G (JWST-led); 2024ApJ...966..117X (synthetic disk winds); 2015ApJ...808..102K (CARMA,
Toomre Q); 2014A&A...569A..11S and 2016ApJ...830L..37I (core and hot-corino studies without disk fits).
