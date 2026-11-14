---
name: alma-keplerian-disk-kinematics
description: "Fit Keplerian rotation of disks in ALMA line data to measure central (stellar or protostellar) dynamical masses, disk inclination, position angle, systemic velocity, emission height and Keplerian radius, and to find deviations from Keplerian rotation. Covers velocity-map fits (bettermoments + eddy), forward modelling of channel maps or visibilities (RADMC-3D/LIME + emcee), velocity-aligned stacking for faint disks, and PV-diagram rotation curves for embedded protostars. Use when a paper or task needs a dynamical mass from disk rotation, a Keplerian mask, Keplerian-shifted stacking, or checks on someone else's Keplerian fit. Built from 188 ALMA papers (2012-2026)."
---

# Keplerian disk kinematics and dynamical masses

Measures the central mass and disk geometry from the line-of-sight velocity pattern of a rotating disk,
v_los = sqrt(G M / r) cos(phi) sin(i) + v_sys for a thin disk (general practice). The two mistakes that matter
most: (1) **reporting M* without facing the mass-inclination and mass-distance degeneracies**: the
line of sight only constrains roughly M sin^2 i, and M scales linearly with the adopted distance
(2015ApJ...812...27A reports M* sin^2 i = 0.56 Msun; 2020ApJ...894...74B: "dynamical mass scales linearly
with distance"); and (2) **quoting the MCMC posterior width as the error**: in CQ Tau the formal error was
+-0.002 Msun while different model runs gave 1.47-1.65 Msun (2021A&A...648A..19W), and in DM Tau / MWC 480
systematics dominate over statistics (2020ApJ...895..109F).

> Always report: tracer and transition, rest frequency, velocity frame and convention, channel width and any
> spectral smoothing, distance (and its source), whether i, PA and centre are fixed (from what) or free,
> emission-surface assumption (thin, conical, flared), fitted radial range, noise model, sampler settings and
> priors, and an error budget that includes distance and model systematics.

Counts below come from the evidence pack aggregates (188 papers; 128 protoplanetary-disk, 77 star-formation,
14 debris-disk, 7 evolved-star tags, papers can carry several) or from my own count of pack lines, as stated
at each count. A few details come from single methods cards and are marked "(card)"; each matches a verbatim
quote in that card. About a dozen pack papers are off-topic for disk Keplerian fits and are ignored here
(listed at the end).

## When to use

- Dynamical stellar mass of a Class II star from a resolved CO/13CO/C18O disk, for comparison with
  evolutionary tracks (2017ApJ...844..158S, 2021ApJ...908...46B, 2017ApJ...846L..26W, 2025ApJ...986L..11S).
- Protostellar mass and Keplerian disk radius in embedded (Class 0/I) sources from PV diagrams
  (2017ApJ...849...56A, 2024A&A...690A..46S, 2018ApJ...864L..25O, 2015ApJ...812...27A).
- Disk geometry (i, PA, v_sys, centre) and emission height from velocity maps: 12CO with a conical surface
  (2018ApJ...868..113T), HCO+ with a flared surface (2020ApJ...891...48H), CS first-moment maps for geometry
  only, with M* fixed at 0.65 Msun (2018ApJ...864..133T).
- Rotation curves and deviations from Keplerian (pressure bumps, spirals, warps, planets)
  (2018ApJ...868..113T, 2021A&A...648A..19W, 2012ApJ...757..129R, 2024MNRAS.534.2904C).
- Low-S/N survey disks where a mass is only reachable by velocity-aligned stacking (2018A&A...616A.100Y,
  2021ApJ...908...46B).
- Building a Keplerian CLEAN mask or Keplerian-shifted spectral stack for weak lines (2013ApJ...774...16R,
  2024ApJ...965..147B, 2021ApJ...908..141H, 2026A&A...705A.198M).
- Gas in debris belts or disks around evolved stars (2016ApJ...829....6W, 2013ApJ...776...77K,
  2018A&A...614A..58B, 2017A&A...597L...5B).
- Massive (proto)star disks, keeping in mind the disk mass is not negligible (2025NatAs...9.1833L,
  2019A&A...622A.206M, 2018ApJ...860..119G).

## When not to use

| Situation | Use instead |
|---|---|
| Rotation in an infalling envelope, centrifugal barrier, infall-rotation transition, streamers | `envelope-kinematics-pv` skill. The pack shows these models (centrifugal barrier M = r_CB v_CB^2 / 2G in 2019ApJ...873...73Z; IRE/FERIA and streamline models in 2025SciA...11.4512O) but they are not Keplerian disk fits |
| Galaxy rotation curves, circumnuclear disks, AGN gas dynamics | `galaxy-3d-kinematics` skill (3D tilted-ring or kinemetry); the galaxy papers tagged here (2015ApJ...811...39I) are out of scope |
| Unresolved disk, single spectrum only | A Keplerian double-peak line profile fit gives at most M sin^2 i with an assumed radius; say so, or treat the mass as a limit (2020ApJ...896..127K: "lower limit because inclination is unknown") |
| Ionized disk plus wind traced by radio recombination lines | A dedicated non-LTE disk-plus-wind model, not a plain Keplerian fit: 2020ApJ...897L..33J needed MORELI with a Keplerian ionized disk and an expanding wind (see step 1) |
| Only the dust disk geometry is needed | Continuum visibility fitting (`uv-plane-fitting` skill), which several papers use to fix i and PA before the kinematic fit (2020ApJ...891...48H, 2024ApJ...974..102S) |
| Gas mass or temperature is the goal | `radiative-transfer-modelling` / `gas-mass-co-conversion`; Keplerian fits mostly fix those as nuisance parameters |

## Steps

1. **Pick the regime and tracer.**
   - Class II disks: 12CO for geometry and emission height (optically thick, elevated surface), 13CO/C18O
     or CN closer to the midplane for masses (2018A&A...616A.100Y stacks 13CO and C18O 3-2, card;
     2021ApJ...908...46B stacks 13CO, C18O and CN, card, assuming "different molecules follow same Keplerian
     rotation").
   - Embedded protostars: C18O, SO, HCO+ along the disk major axis (2015ApJ...812...27A C18O;
     2018ApJ...864L..25O SO; 2014ApJ...786..114L HCO+). Avoid lines dominated by envelope or outflow.
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
     aggregates, 2) and 2017A&A...597L...5B gives no velocity reference (card note in the pack).
     2019ApJ...883...22C binned all line windows to matching 334 m/s LSRK channels (card).
   - Channels: about 0.1 km/s for disks (2016ApJ...823L..18H, 2025ApJ...989....1Z, 2025ApJ...989....3D);
     160 m/s in 2018ApJ...868..113T. Record any spectral smoothing, since it correlates channels:
     2013ApJ...776...77K applies 2-channel Hanning smoothing in its models.
   - Weighting: Briggs robust 0.5 in 3 of the 4 pack lines that give a robust value (2018ApJ...864..133T,
     2024RAA....24g5017M, 2026A&A...705A.198M); 0.6 in 2021A&A...648A..19W; natural for sensitivity
     (2018ApJ...868..113T, 2013ApJ...774...16R).
   - CLEAN with a Keplerian mask: the `keplerian_mask` script is named in 5 matched steps (pack aggregates),
     typically seeded with literature M*, PA, i (2020A&A...638A..38T tunes v_sys and line width to maximise
     S/N; 2018A&A...614A.106C uses M = 1.65 Msun). 2018ApJ...868..113T first fits a moment map, then re-cleans
     with a mask built from that fit and checks it "encompass[es] the whole emission".
3. **Fix the geometry you can measure independently.** Many papers fix i, PA and centre from continuum
   visibility fits and leave M* and v_sys free (2020ApJ...891...48H; 2024ApJ...974..102S; 2025ApJ...986L..11S
   fixes i = 49.9 deg; 2019ApJ...880...69Y fixes PA 138 deg, i 47 deg). Centre on the continuum peak
   (2018ApJ...869...59W, 2018A&A...616A.100Y). Fixing i transfers any inclination error straight into M*.
4. **Choose the kinematic method.**

| Method | When | How papers do it |
|---|---|---|
| A. Velocity map + `eddy` | Resolved, bright disk (12CO/13CO/HCO+) | `bettermoments` quadratic (peak) velocity map, then `eddy` Keplerian model with emcee; flat or conical surface z = r tan psi (2018ApJ...868..113T), or flared z = z0 (r/1")^psi with psi an exponent (2020ApJ...891...48H); also 2021A&A...648A..19W, 2024ApJ...974..102S |
| B1. Forward model, M* free (dynamical mass) | Best dynamical masses; moderate S/N | Parametric flared, vertically isothermal LTE disk, ray-traced with RADMC-3D, Fourier-sampled at the data uv points, MCMC; M* free with disk structure as nuisance (2017ApJ...846L..26W, 2017ApJ...835...17M, 2016ApJ...818..156C, 2019ApJ...883...22C with DiskJockey, card) |
| B2. Forward model, M* fixed (structure, temperature, turbulence) | Gas structure is the goal | Same machinery with a prescribed mass: M* = 2.3 Msun fixed in 2015ApJ...813...99F, M* = 1.7 Msun in 2018ApJ...854..130W, masses fixed in 2020ApJ...895..109F. These are not dynamical-mass measurements |
| C. Velocity-aligned stacking | Faint survey disks | Shift each pixel by -v_kep cos(phi) sin(i), stack, grid-search M*, PA, i, v_sys for maximum S/N of the stacked line (2018A&A...616A.100Y); 2021ApJ...908...46B maximises S/N over M* and v_sys with i, PA, position and distance fixed (card) |
| D. PV rotation curve | Embedded, near edge-on protostars | Mean positions or ridge/edge per channel along the major axis, single or double power law in log R-log V; Keplerian if index ~0.5; `SLAM` MCMC (2017ApJ...849...56A uses only pixels above 5 sigma for the mean positions; 2024A&A...690A..46S, 2015ApJ...812...27A) |
| E. Tilted rings | Massive protostellar disks | `3DBarolo` on the cube, power-law fit of v_rot(r), Keplerian enclosed mass (2025NatAs...9.1833L); see step 8 for converting enclosed mass to M* |
| F. Visual model comparison | Complex systems, illustrative only | Grid or hand-tuned models vs channel maps and PV (2019ApJ...873...73Z, 2018A&A...614A.113H, 2018A&A...614A..58B). Authors themselves say this gives no fit quality |

5. **Set up the fit.**
   - Preserve each paper's fixed/free split rather than a generic list. M* free: 2017ApJ...846L..26W (Mdisk,
     Rdisk, gamma, T0, q, xi, M*, v_sys, i, PA, offsets) and 2017ApJ...835...17M (M*, i, PA, r_c, T10, q, Mgas,
     xi, v_sys, offsets). M* fixed: 2018ApJ...854..130W (free Mdisk, r_c, gamma, T0, q, xi, v_sys, i, PA with
     M* = 1.7 Msun) and 2015ApJ...813...99F.
   - Fixed values seen: X_CO = 1e-4, mu = 2.37, inner radius 0.1 au (2017ApJ...846L..26W, 2018ApJ...854..130W);
     gamma = 1 fixed in 2016ApJ...823L..18H, 2015ApJ...798...85P, 2019ApJ...883...22C, 2020ApJ...895..109F,
     but fitted in 2017ApJ...846L..26W and 2018ApJ...854..130W; turbulent broadening xi = 0.01 km/s
     (2016ApJ...823L..18H), v_turb 0.01 km/s (2017NatAs...1E.130Z).
   - Restrict the radial range: fit 0.2-2" (2020ApJ...891...48H), 0.33-1.4" (2024ApJ...974..102S), or exclude
     the inner ~5 beams "to mitigate the spatial resolution bias" (2025ApJ...994...98F). Vary r_min to see if
     results move (2024MNRAS.534.2904C).
   - Handle contaminated channels and sides. 2019ApJ...883...22C masks all channels with 4.0-7.5 km/s LSRK
     after checking FCRAO cloud maps (card); 2016ApJ...818..156C excludes 23 contaminated channels (card);
     2017ApJ...843...27L weights the fit to the blueshifted side because of redshifted self-absorption.
     Separately, in AS 209 the foreground cloud absorbs about 30% of the 12CO emission on the western side
     (2018ApJ...868..113T); that is an absorption measurement, not a channel-exclusion fraction.
   - Velocity-map S/N cut before fitting: 5 sigma (2017ApJ...840...60B, 2024MNRAS.534.2904C) or 2.5 sigma
     (2020MNRAS.493L.108B). This is an intensity threshold on which pixels enter the map; keep it distinct from
     the per-pixel velocity uncertainties used in the likelihood.
   - Use a noise model that matches the data. 2016MNRAS.460.2933M writes the likelihood "taking into account
     the number of independent beams in the image and the correlation between adjacent channels"; neighbouring
     annuli are correlated within a beam (2018ApJ...864..133T). Either model the spatial and spectral
     correlation or count effective independent samples, and match the model's spectral response (channel
     width, Hanning smoothing as in 2013ApJ...776...77K) to the data. Pixel-by-pixel chi2 on an oversampled map
     without this shrinks the posterior (recommendation following these papers).
6. **Sample.** emcee is the sampler named most often in the matched steps (18, pack aggregates); that is a
   count of mentions, not a validated default. Others in the pack: Metropolis-Hastings with Gibbs sampling,
   3 chains (2016ApJ...829....6W), a Julia ensemble sampler in DiskJockey (2019ApJ...883...22C, card), chi2
   grids (2013ApJ...776...77K, 2015ApJ...812...27A). Reported settings in the parameter table below. Report
   16th-84th percentiles (2021A&A...648A..19W) but treat them as a floor.
7. **Inspect residuals and rotation curves.** Subtract the best Keplerian model from the velocity map
   (2024MNRAS.534.2904C, 2021A&A...648A..19W); for v_phi(r) bin deprojected spectra into annuli of about a
   quarter beam and fit each annulus (2018ApJ...868..113T with eddy + celerite GP; 2019A&A...625A.118K).
   exoALMA made residual maps by "subtracting the model disk obtained from spectral fitting using DISCMINER"
   (2026ApJ..1000L..15F, card). Before naming a cause for a residual, report that "velocity residuals are model
   dependent, and the appearance of a Doppler-flip is therefore also model dependent" (2024MNRAS.534.2904C;
   it varied r_min to test this) and the resolution limit: unresolved velocity features "will underestimate
   the true depth" (2018ApJ...868..113T). Residual morphology alone does not identify a planet, spiral or warp.
8. **Build the error budget and the reported mass.** Add distance uncertainty in quadrature
   (2017ApJ...846L..26W adds 20 pc at 140 pc), compare runs with different surfaces, masks and radial ranges,
   and report the spread. A rotation curve measures the enclosed mass. Where the disk and surrounding gas are
   massive, report enclosed mass and stellar mass separately and say which gravity model was used:
   2025NatAs...9.1833L finds M_cl = 7.6 +- 1.4 Msun enclosed, then M* = M_cl - M_disk - sum(M_gas) = 4.89 Msun.

## Parameter defaults and ranges

"Typical value" is the value most often reported in the pack lines, not an independently validated default.
"Supporting pack entries" is my count of distinct bibcodes in the pack's parameter, assumption and excerpt
lines that state the setting (not a paper-level prevalence).

| Parameter | Typical value (reported settings) | Range seen | Supporting pack entries | Examples |
|---|---|---|---|---|
| Channel width | 0.1 km/s | 0.1-0.4 km/s | 6 | 2016ApJ...823L..18H, 2019A&A...624A...7V (0.11), 2018ApJ...868..113T (0.16), 2017ApJ...851..132C (0.4) |
| Briggs robust | 0.5 | 0.5-2, natural | 4 robust + 3 natural | 2018ApJ...864..133T, 2021A&A...648A..19W (0.6), 2026A&A...705A.198M (0.5 or 2); natural 2018ApJ...868..113T, 2013ApJ...774...16R, 2016MNRAS.460.2933M |
| Inclination | fixed from continuum or literature | free in forward models and some eddy fits | 12 fixed, 10 free | fixed 2020ApJ...891...48H, 2025ApJ...986L..11S, 2019A&A...625A.118K (51.7 deg); free 2016ApJ...829....6W, 2017ApJ...846L..26W, 2018ApJ...864..133T |
| Distance | Gaia DR2 where stated | 59 pc to 2.38 kpc | 15+ | 2018ApJ...862L...2F (59 pc), 2019A&A...632L..12H (59.5 pc), 2021A&A...648A..19W (162 pc), 2017ApJ...844..158S (131/119/140 pc), 2024ApJ...967...15K (2.38 and 1.7 kpc, spectrophotometric, card); Gaia DR2 in 2020ApJ...895..109F |
| Emission surface, 12CO conical | psi ~13-15 deg (z/r = tan psi ~0.23-0.27) | 13.1-15 deg | 2 | 2018ApJ...868..113T (psi 13.1 deg), 2013ApJ...774...16R (~15 deg) |
| Emission surface, HCO+ flared | z = z0 (r/1")^psi | z0 0.127", exponent psi 0.81 (z/r = 0.127 at r = 1") | 1 | 2020ApJ...891...48H |
| Emission surface, assumed ratio | z/r = 0.13 | n/a | 1 | 2023PASJ...75..424O (assumed height ratio; tracer not given in the pack line) |
| Emission surface (13CO, C18O, PV fits) | geometrically thin | n/a | 5 | 2018A&A...616A.100Y, 2019ApJ...880...69Y, 2016ApJ...832..204Y |
| Annulus width (rotation curve, stacking) | 1/4 beam | 1/4 beam, 4 au, 0.05" | 5 | 2018ApJ...868..113T, 2024ApJ...965..147B, 2018ApJ...864..133T (4 au), 2024ApJ...970..153A (0.05") |
| Sampler walkers / steps / burn-in | see examples | walkers 32-200, steps 1000-15,000 | 7 | 2020ApJ...891...48H (48/3500/500), 2021A&A...648A..19W (200/5000 burn + 5000), 2025ApJ...994...98F (32/1000/300 for M*), 2018A&A...619A.171B (80/1000), 2026ApJ..1003...64Y (100/15,000/2000), 2025ApJ...984L..21B (2000 burn + 4000) |
| M* prior | broad uniform | U(0,5) Msun; 5-15 Msun massive | 2 | 2025ApJ...994...98F, 2019A&A...622A.206M |
| Inclination and distance priors | geometric on i, Gaussian on d | d ~ N(145, 20) pc | 1 | 2016ApJ...818..156C (sin(i)/2 prior on i and Gaussian distance prior, card) |
| Stacking grid | M* step 0.1 Msun, i step 5 deg | M* 0.1-3, PA 0-355, i 5-85, v_sys step 0.1 km/s | 1 | 2018A&A...616A.100Y |
| Model grid (debris CO) | 5 parameters | M* 0.9-3.0 step 0.3, i 25-39 step 2 | 1 | 2013ApJ...776...77K |
| Turbulent broadening xi / v_turb | 0.01 km/s | n/a | 2 | 2016ApJ...823L..18H (xi), 2017NatAs...1E.130Z (v_turb) |
| Other line-width parameters (not interchangeable) | as defined per paper | see examples | 4 | 2013ApJ...776...77K (intrinsic line width 0.1 km/s), 2015ApJ...798...85P (b = 50 m/s), 2018A&A...616A..34H (micro-turbulence ~0.5 km/s), 2018A&A...614A.113H (turbulence 1 km/s, AGB) |
| Velocity-map S/N cut | 5 sigma | 2.5-5 sigma | 3 | 2017ApJ...840...60B, 2024MNRAS.534.2904C, 2020MNRAS.493L.108B (2.5) |
| PV mean-position intensity threshold | 5 sigma | n/a | 1 | 2017ApJ...849...56A |
| Keplerian mask smoothing | Gaussian kernel | sigma 0.7" | 1 | 2013ApJ...774...16R |
| PV inner power-law index | 0.5 (Keplerian) | fitted 0.50-0.53; outer ~1.2 | 3 | 2017ApJ...849...56A (0.50, outer 1.22), 2015ApJ...812...27A (0.53), 2024A&A...690A..46S (fixed 0.5) |
| Gas structure (forward models) | X_CO 1e-4, mu 2.37 | gamma fixed at 1 or fitted | 7 | X_CO/mu: 2017ApJ...846L..26W, 2018ApJ...854..130W, 2015ApJ...813...99F; gamma = 1 fixed: 2019ApJ...883...22C, 2015ApJ...798...85P, 2016ApJ...823L..18H, 2020ApJ...895..109F; gamma fitted: 2017ApJ...846L..26W, 2018ApJ...854..130W |

Line widths: the pack mixes turbulent xi, intrinsic line width, Doppler b and "turbulence" without a common
convention. Before comparing values, check whether each is a sigma, a Doppler b (sqrt(2) sigma) or a FWHM and
whether thermal broadening is included (general practice).

## Software

Counts are matched steps naming the tool (pack aggregates). They show how often a tool is named, not how often
a method is used.

| Tool | Count | Used for |
|---|---|---|
| CASA (`tclean`, `simobserve`) | 45 (+ 3 version-tagged, tclean 2) | calibration, Keplerian-masked imaging, synthetic observations of models (2020ApJ...893...51S, 2018A&A...614A.113H) |
| emcee | 18 | sampling Keplerian and disk-model posteriors (2020ApJ...891...48H, 2025ApJ...994...98F, 2018ApJ...868..113T) |
| eddy | 16 | Keplerian fits to velocity maps, emission surfaces, rotation curves (2018ApJ...868..113T, 2021A&A...648A..19W, 2025ApJ...986L..11S) |
| RADMC-3D (+ radmc3dpy 2) | 14 | ray-traced line cubes for forward models (2016ApJ...818..156C, 2017ApJ...846L..26W, 2020ApJ...893...51S) |
| bettermoments | 13 | quadratic / peak velocity maps feeding eddy (2020ApJ...891...48H, 2024MNRAS.534.2904C) |
| GoFish | 10 | Keplerian-shifted stacking for weak lines (2024ApJ...965..147B, 2026A&A...705A.198M); Kepler-correcting Stokes I and V for Zeeman fits (2021ApJ...908..141H, see Pitfalls) |
| LIME | 7 | non-LTE line radiative transfer (2012ApJ...757..129R, 2013ApJ...774...16R, 2018A&A...614A.113H) |
| keplerian_mask (+ kepmask 1) | 5 | Keplerian CLEAN and moment masks (2021A&A...648A..19W, 2026A&A...705A.198M) |
| vis_sample (+ vissample 1), DiskJockey | 3, 3 | sample model images at data uv points (2016ApJ...823L..18H); Julia MCMC for disk dynamical masses (2019ApJ...883...22C, card) |
| Miriad, GILDAS | 3, 3 | older imaging and PV work (2020ApJ...898...10T, 2019A&A...632L..12H) |
| FERIA, SLAM, 3DBarolo, pvextractor, disksurf, celerite, MORELI | 2, 1, 1, 1, 1, 1, 1 | IRE models, PV rotation curves, tilted rings, PV cuts, surface extraction, GP rotation curves, non-LTE RRL disk-plus-wind models (2025SciA...11.4512O, 2024A&A...690A..46S, 2025NatAs...9.1833L, 2018ApJ...868..113T, 2020ApJ...897L..33J) |
| DISCMINER | not in aggregates | channel-map Keplerian models and residual maps for exoALMA (2026ApJ..1000L..15F, card) |

## Pitfalls

- **Mass-inclination degeneracy.** "The inclination and the stellar mass are degenerate" (2013ApJ...776...77K
  took i from the best-fit mass); inclination poorly constrained by the disk model (2015ApJ...812...27A,
  2017A&A...597L...5B, 2018A&A...616A.100Y); edge-on assumed to get a minimum mass (2017NatAs...1E.172L,
  2020ApJ...896..127K). If i comes from the continuum, say so and propagate its error.
- **Distance.** M is proportional to the adopted distance (2020ApJ...894...74B); several papers state the
  error excludes distance (2024ApJ...967...15K). Check that distances are Gaia-era for older papers.
- **Underestimated errors.** Posterior widths far below run-to-run scatter (2021A&A...648A..19W);
  systematics from midplane temperature and flux calibration dominate (2020ApJ...895..109F); calibration
  uncertainty left out of the MCMC (2020ApJ...892...99C); correlated pixels and channels treated as
  independent (see step 5).
- **Spectral axis.** A wrong sky-frequency transformation (2013ApJ...774...16R) or an unstated rest frequency
  or frame shifts v_sys and misaligns stacks. Check it before fitting.
- **Pressure and self-gravity.** A rotation curve cannot separate large-scale pressure support from M*
  (2018ApJ...868..113T). Disk mass is usually neglected (2019ApJ...873...73Z, 2019A&A...622A.206M), which fails
  for massive disks (disk-to-star 0.2-0.6 in 2025NatAs...9.1833L, where enclosed mass 7.6 Msun becomes
  M* = 4.89 Msun after subtracting disk and gas); 2024ApJ...970..153A fits stellar, pressure and self-gravity
  terms together.
- **Beam smearing.** Not corrected in the inner 90-100 au in 2018ApJ...864..133T. In 2025ApJ...994...98F the
  resolution bias on intensity/temperature "can extend up to 8 times the size of the beam" with intensity
  underestimated by up to 50%; for the mass fit the same paper excludes the inner ~5 beams. In
  2025ApJ...986L..11S EDDY on the moment-1 map gave 0.043 Msun while the 12CO visibility fit gave 0.092 Msun,
  and the authors note EDDY "does not take the beam convolution into account, which may result in smaller
  stellar mass" (card). 2024ApJ...970..153A corrects v_phi with mock-cube factors. Neighbouring annuli are
  correlated within a beam (2018ApJ...864..133T).
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
  (2015ApJ...812...27A).
- **Missing flux and cloud contamination.** Missing large scales bias rotation at large radii
  (2014ApJ...796..131O; ~25% filtered in 2017A&A...597L...5B); foreground cloud absorption (2018ApJ...868..113T,
  2020ApJ...894...74B, 2024ApJ...969..165D).
- **Low S/N stacking.** Stellar mass can be overestimated for fluxes below about 400 mJy km/s
  (2018A&A...616A.100Y).
- **Stacking for polarisation.** Stacking red and mirrored blue sides "would destroy any Stokes V signal from a
  vertical magnetic field" (2021ApJ...908..141H). Keep red and blue sides separate when polarity matters, and
  fit only unblended parts of hyperfine lines: that paper used only the low-frequency part of line 5 and the
  high-frequency part of line 7.
- **RRL disks.** Keplerian-only models miss the wind; maser variability and large high-velocity centroid errors
  limit the mass (2020ApJ...897L..33J).
- **Binaries and circumbinary disks.** The fit gives the total enclosed mass (2020ApJ...898...10T assumed
  equal masses totalling 0.5 Msun); circumbinary disks leave non-Keplerian residuals (2024MNRAS.534.2904C).
  Combine with RV orbits for component masses (2016ApJ...818..156C).
- **Conventions.** Inclination and PA conventions differ (2019ApJ...873...73Z defines edge-on as i = 0;
  2018A&A...614A.113H quotes i = 110 deg). Convert before comparing.
- **Hand-tuned models.** Many models are "not unique nor optimized" (2012ApJ...757..129R,
  2013ApJ...774...16R) or chosen by eye (2019ApJ...873...73Z, 2018A&A...614A.113H). Do not quote them as fits.
- **Unstated settings.** Cards flag CASA version (16), self-calibration intervals (15), image and cell size
  (11), line-free channels (more than 50 across phrasings) and rest frequencies (2) as not stated (pack
  aggregates). Write them down.

## Verification checks

What papers did:
- Recover a known mass from synthetic data: 0.99 +- 0.02 Msun for a 1 Msun model (2025ApJ...994...98F);
  tests on 30 blank-field synthetic images and 24 model disks for the stacking method (2018A&A...616A.100Y,
  card).
- Refit with different surface assumptions (flared, thin, no continuum subtraction): the three radial v_rot
  profiles are "consistent within 3 sigma of one another" (2018ApJ...868..113T). This validates the rotation
  curve, not the mass.
- Refit with and without beam convolution and with velocity errors x10 (2021A&A...648A..19W).
- Compare image-plane and visibility-plane masses: 0.043 vs 0.092 Msun in 2025ApJ...986L..11S (card), so the
  check can fail; compare masses from different lines: "80% of the measurements from different line data agree
  on a level better than 1 sigma" (2021ApJ...908...46B, card).
- Vary a fixed structure parameter: the dynamical mass "remained the same" for floating q, q = 0.50 and
  q = 0.75 (2019ApJ...883...22C, card).
- Test competing velocity laws: single vs double power law, reduced chi2 1.6 vs 4.0 (2017ApJ...849...56A);
  infalling-rotating envelope rejected (2018ApJ...864L..25O); pure Keplerian rejected (2019ApJ...873...73Z);
  no-wind model rejected for an RRL disk (2020ApJ...897L..33J).
- Overlay isovelocity contours or model PV curves on channels (2020ApJ...891...48H, 2020ApJ...898...10T).
- Convergence: multiple chains agree, model matches data to ~10% (2016ApJ...829....6W); reduced chi2 0.72
  (2015ApJ...812...27A).
- Independent masses: SED fit (2019ApJ...873...73Z), earlier lower-resolution data (2025NatAs...9.1833L).
- Mask covers all emission (2018ApJ...868..113T).

What a careful referee adds:
- Is the quoted error dominated by distance and inclination, and are those propagated?
- Does M* change when r_min, r_max, surface height or tracer change (2024MNRAS.534.2904C varies r_min)?
- Does the likelihood account for correlated pixels and channels (2016MNRAS.460.2933M), and does the model
  match the data's channelisation and smoothing?
- Were rest frequency, velocity frame and convention checked and reported?
- Were absorbed or cloud-contaminated channels excluded, and is the fit symmetric between red and blue sides?
- For embedded sources, is the fitted region inside the Keplerian radius and free of envelope/outflow?
- For massive disks, is the reported number the enclosed mass or the stellar mass?
- Is i from the gas consistent with i from the continuum (2025ApJ...986L..11S reports "consistent solutions of
  inclination and position angle to those from the continuum", card)?
- Are residual features shown to survive changes to the subtracted model?

## Source cards

Full list: `references/sources.md` (generated). Most informative for this technique:

- 2018ApJ...868..113T (eddy, conical surface, GP rotation curve, surface tests)
- 2020ApJ...891...48H (bettermoments + eddy on HCO+, fixed geometry, emcee settings)
- 2021A&A...648A..19W (eddy runs, underestimated errors, beam tests)
- 2025ApJ...986L..11S (image vs visibility masses for a brown dwarf)
- 2017ApJ...846L..26W (RADMC-3D + emcee visibility fit, M* free, distance in quadrature)
- 2016ApJ...818..156C (disk mass combined with binary RV orbit)
- 2019ApJ...883...22C (DiskJockey dynamical mass, cloud channels)
- 2017ApJ...844..158S (dynamical masses vs evolutionary tracks)
- 2021ApJ...908...46B (stacked survey masses, thin-disk bias)
- 2018A&A...616A.100Y (velocity-aligned stacking grid, low-flux bias)
- 2025ApJ...994...98F (recovery test, beam-bias correction)
- 2024ApJ...970..153A (pressure and self-gravity in v_phi)
- 2017ApJ...849...56A (PV double power law, Keplerian radius)
- 2024A&A...690A..46S (SLAM ridge and edge fits)
- 2015ApJ...812...27A (C18O disk model, M sin^2 i)
- 2018ApJ...864L..25O (very low-mass protostar from SO PV)
- 2013ApJ...776...77K (debris CO grid, M-i degeneracy)
- 2016ApJ...829....6W (MCMC on moment 1, debris disk)
- 2016MNRAS.460.2933M (likelihood with independent beams and channel correlation)
- 2024MNRAS.534.2904C (residuals, r_min dependence, circumbinary)
- 2025NatAs...9.1833L (3DBarolo for a massive disk, enclosed vs stellar mass)
- 2020ApJ...897L..33J (RRL disk plus wind with MORELI)
- 2021ApJ...908..141H (GoFish Kepler correction for Zeeman, stacking caveat)
- 2018ApJ...864..133T (CS moment-1 geometry fit with fixed M*, beam smear)
- 2020ApJ...895..109F (systematics dominate)

Off-topic papers in the pack (regex-tagged, ignored here): 2013ApJ...768L..38H and 2015ApJ...811...39I
(galaxy nuclei), 2017ApJ...837...93Y and 2017ApJ...842...94T (orbits around Sgr A*), 2019NatAs...3..408D
(OH/IR binary), 2023PASJ...75..225M (HII region ring), 2024A&A...689A..85G (JWST-led),
2024ApJ...966..117X (synthetic disk winds), 2015ApJ...808..102K (CARMA, Toomre Q), 2014A&A...569A..11S and
2016ApJ...830L..37I (core and hot-corino studies without disk fits).
