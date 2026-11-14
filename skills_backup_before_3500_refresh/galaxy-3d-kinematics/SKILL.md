---
name: alma-galaxy-3d-kinematics
description: "Model the gas kinematics of galaxies in ALMA line cubes (CO, [CII], HCN, HI comparisons): 3D tilted-ring and parametric disk fits to the cube (3DBarolo, KinMS, GalPak3D, qubefit, TiRiFiC), 2D velocity-field fits (kinemetry, GIPSY rotcur, DiskFit, arctan models), rotation curves, velocity dispersion, v/sigma, non-circular and radial motions, and dynamical masses, including the simple FWHM and virial estimators used for barely resolved high-z sources. Use when deriving a rotation curve, inclination, PA, intrinsic dispersion or dynamical mass of a galaxy or circumnuclear disk, classifying a source as rotation- or dispersion-dominated, or checking someone else's kinematic fit for beam smearing and inclination problems. Built from 145 ALMA papers (2013-2026)."
---

# 3D kinematic modelling of galaxies (tilted rings, disks)

Fits a model of rotating (and possibly inflowing, outflowing or warped) gas to a galaxy line cube to recover the
rotation curve V(R), intrinsic dispersion sigma(R), geometry (centre, PA, inclination, systemic velocity) and a
dynamical mass. The two mistakes that matter most: (1) **beam smearing** of the inner rotation curve into the
line width, which biases sigma high and Vrot low in low-resolution data (2019MNRAS.482.1499M) unless the model
forward-models the instrumental response (beam and channels) and that model is shown to recover known inputs
on mock data; convolution alone does not remove degeneracies (2017ApJ...850..180J, 2025NatAs...9.1553F mock
tests); (2) the **inclination-velocity degeneracy**: at marginal resolution
inclination and peak rotation velocity "cannot be independently determined" (2016ApJ...816...37V;
2017ApJ...850..180J), and M_dyn scales as 1/sin^2 i, so a free, poorly constrained inclination silently
dominates the error budget.

> Always report: tracer and cube (weighting, channel width, pixel size, mask), which parameters were free and
> which fixed (and from what data), ring width or radial grid, normalisation and weighting, the likelihood and
> noise treatment, how errors were derived, and the radius at which M_dyn is quoted. Also report the velocity
> frame (LSR, heliocentric or barycentric), velocity definition (radio, optical or relativistic), rest frequency
> and V_sys zero point, and convert every dataset to one convention before combining tracers or comparing
> systemic velocities: the NGC 1068 cards quote V_sys = 1120 +/- 3 km/s (LSR, 2019A&A...632A..61G) and
> 1127 +/- 3 km/s (heliocentric, 2014A&A...567A.125G) for the same disk. Report primary-beam correction (and its
> effect on the noise map used in the fit), flux-scale uncertainty, clean threshold and mask, and the clipping or
> S/N rule that selects pixels for moment maps and fitted velocity fields; the cards flag these as missing
> (pack "not stated" aggregates). The cards often cannot recover 3DBarolo parameter files, MCMC priors or chain
> settings (see Pitfalls).

## When to use

- The line emission is resolved by at least a few beams along the major axis and you need V(R), sigma(R),
  PA, i or V_sys: nearby spirals and Seyferts (2024A&A...690A.169L, 2021A&A...656A..60A, 2021A&A...655A..25Z,
  2019A&A...632A..61G), high-z [CII] disks (2020Natur.581..269N, 2025NatAs...9.1553F, 2017ApJ...850..180J,
  2018ApJ...864L..11X).
- Deciding whether a high-z source is a rotating disk or a merger (2025MNRAS.536.3757A: 12 of 20 DSFGs with
  SNR > 8 disk-like; 2024ApJ...968....9W: 10 of 23 quasar hosts rotation-dominated; 2019ApJ...871...85L).
- Quantifying non-circular motions, radial inflow/outflow or bar streaming in circumnuclear disks
  (2014A&A...567A.125G, 2019A&A...621A..83S, 2021A&A...652A..98G, 2024A&A...690A.169L).
- Dynamical masses for gas fractions, alpha_CO calibration or M_BH/M_host ratios (2015ApJ...812L..23S,
  2017ApJ...845..138S, 2020A&A...637A..84P).
- Separating a disk model from residual outflow emission (2021A&A...655A..25Z builds the outflow from the
  3DBarolo residual cube; 2021AN....342.1160P explains high dispersion by projection of non-coplanar rings).

## When not to use

| Situation | Use instead |
|---|---|
| Protoplanetary or circumstellar Keplerian disks (stellar mass, emission surfaces, planet kinks) | `keplerian-disk-kinematics` skill |
| Measuring a supermassive black hole mass from a circumnuclear gas disk (MGE stellar model, M/L, BH point mass) | `smbh-gas-dynamics` skill; this skill only covers the generic disk-fitting part that KinMS-based M_BH work shares (2020ApJ...892...68N, 2025ApJ...992..211N, 2020MNRAS.496.4061D) |
| Protostellar envelopes: infall plus rotation from PV diagrams, centrifugal barrier | `envelope-kinematics-pv` skill |
| Source unresolved or resolved by about one beam | Do not run a tilted-ring fit; use a line-width estimator with an explicit inclination assumption (Step 6b) and say it is order-of-magnitude (2015Natur.522..455C: "very uncertain"; 2017ApJ...850..180J mock tests: ~1 dex systematic) |
| Lensed source in the image plane | Reconstruct the source-plane cube first (see `lens-modelling`), then fit (2025NatAs...9.1553F fits source-plane cubes) |
| Only need maps of velocity and line width | `moment-maps` skill |
| Outflow mass, rate and energetics | `outflow-energetics` skill, after removing the disk model |
| Disk stability (Toomre Q) | `toomre-stability` skill, fed with V(R) and sigma(R) from here |

## Steps

1. **Prepare the cube.**
   - Goal: a continuum-subtracted cube whose beam, channel width and noise are known exactly, because the model
     is convolved with that beam and compared pixel by pixel.
   - Weighting is set by S/N and resolution: natural-weighted cubes for faint or high-resolution fits
     (2019ApJ...883..193N, 2019ApJ...876..112R with 25 mas pixels); Briggs robust 0.5 for re-imaged survey cubes
     (2024ApJ...968....9W) and for a high-resolution CND cube (2019ApJ...881...10B: robust 0.5, 10.2 km/s
     channels, 0.015" pixels).
   - Rebin channels if S/N is low (2019ApJ...870...39V binned to 40 km/s). Test robustness to weighting:
     2020MNRAS.493.3744F refit cubes imaged at robust 0.5 and -1.0.
   - Cut out a fitting region (2019ApJ...883..193N: 1.55" x 1.55", 4687-5580 km/s, 129x129x47 pixels;
     2025A&A...700A.285W: separate outer cube and 1.1" x 1.1" inner cutout at 40 mas).
   - Software: CASA tclean / immoments (CASA named in 6 matched steps, pack aggregates).

2. **Get first guesses for the geometry and decide what to fix.**
   - Centre: 9 pack papers fix it to the continuum or AGN position (my count of the pack parameter, assumption
     and excerpt lines: 2021A&A...655A..25Z, 2014A&A...567A.125G, 2019A&A...632A..33A, 2020ApJ...898...75I,
     2024A&A...686A..46E, 2021A&A...652A..98G, 2019A&A...628A..65A, 2020A&A...641A.151S, 2019A&A...632A..61G
     step 6). The pack gives no denominator, so this is a count of examples, not a majority. Other choices: the
     line intensity peak (2019MNRAS.482.1499M CO peak, 2019ApJ...887...40W [CII] peak), a Sersic centre
     (2021ApJ...908..231M), the HI best-fit centre carried into the CO fit (2024A&A...690A.169L), a Gaussian
     prior of 1" width (2025MNRAS.536.3757A), or free (2016ApJ...820L..39N, 2018MNRAS.476..122V).
   - Inclination: decide whether an external estimate is a fixed value, a prior, or only a starting guess, and
     say which. Fixed: 44 deg from GALEX UV (2021A&A...655A..25Z, second run), 76.3 deg from dust-lane models
     (2019A&A...622A..89V), 22 deg from the literature (2024A&A...684A..24P, for an Halpha ring model, not an
     ALMA cube). Prior or bounded range: K-band b/a with q0 = 0.14, 10% error and a 3 sigma range while i stays
     a free parameter (2019MNRAS.482.1499M); Gaussian prior (37, 3 deg) (2020MNRAS.496.4061D). Starting value
     only: HST/JWST axis ratio i = arccos(q) = 57.9 deg (2025NatAs...9.1553F, which then lists inclination among
     the free 3DBarolo parameters); HI geometry as the start of the CO fit, with i free in the first CO stage
     (2024A&A...690A.169L).
   - Axis-ratio inclination (general practice): cos^2 i = (q^2 - q0^2)/(1 - q0^2); q0 values used: 0.13
     (2017ApJ...851..126V), 0.14 (2019MNRAS.482.1499M), 0.2 (2019A&A...624A.138Y, 2025A&A...700A.165B).
     Plain i = arccos(b/a) assumes an infinitely thin disk (2024ApJ...968....9W, 2017ApJ...845...58Z).
   - PA: from the velocity field (kinemetry, PaFit: 2025A&A...701A.113M checks against PaFit) or the
     steepest-gradient PV cut (2020MNRAS.493.3744F).

3. **Choose the modelling approach.**
   - 3D cube fitting (preferred when beam smearing matters): 3DBarolo for non-parametric tilted rings; KinMS,
     GalPak3D or qubefit for parametric disks with MCMC (see Software for counts).
   - 2D velocity-field fitting (kinemetry, GIPSY rotcur, DiskFit, arctan models) is fine for well-resolved
     nearby disks and for harmonic analysis of non-circular motions. A plain fit of an unconvolved model to a
     moment-1 map is vulnerable to beam smearing of the inner rise; a 2D fit can account for it only if the
     model observables are built through the same beam and moment process as the data (2019ApJ...871...85L
     subtracts a beam-convolved model to check residuals).
   - Whatever the dimensionality, what earns trust is a forward model of the observed response plus a recovery
     test on mock data with the same beam and noise (2025NatAs...9.1553F, 2025MNRAS.536.3757A,
     2017ApJ...850..180J); a beam-convolved 3D fit can still be degenerate (inclination vs V_rot) or biased.
   - For many faint sources consider fitting in the uv plane: 2025MNRAS.536.3757A transforms GalPak3D models per
     channel with pyNUFFT and samples the visibility likelihood with PyMultinest.

4. **Set up the model.**
   - Ring/shell width: tie it to the beam. Choices seen: one beam, then half a beam (2019ApJ...871...85L);
     half the beam FWHM (2021ApJ...908..231M); 0.5-1.0 x PSF FWHM (2025NatAs...9.1553F); shell width = PSF FWHM
     (2025A&A...701A.113M); "ring spacing set by beam size" (2019MNRAS.487..444R). Rings narrower than about
     half a beam are not independent.
   - Rotation curve form for parametric fits: arctan (2020MNRAS.493.3744F GalPak3D default, 2019MNRAS.482.1499M,
     2025A&A...700A.285W), flat (2016ApJ...820L..39N), constant or arctan (2020Natur.581..269N), isothermal
     profile (2025MNRAS.536.3757A).
   - Surface brightness: pack examples with an exponential disk are 2020Natur.581..269N, 2019ApJ...883..193N,
     2019ApJ...882...10N and 2025MNRAS.536.3757A; exponential plus arctan are the GalPak3D defaults that
     2020MNRAS.493.3744F kept because its resolution could not separate models. KinMS SkySampler uses the observed
     distribution directly (2025ApJ...992..211N, 2020MNRAS.496.4061D, 2025A&A...700A.285W). Recommendation (not
     a measured frequency): start from an exponential disk for a few-beam source and test a non-parametric or
     observed distribution where the data allow (2024A&A...684A..24P preferred non-parametric rings by BIC, for
     Halpha).
   - Thickness: thin disk is the usual assumption (2019ApJ...871...85L, 2020A&A...641A.151S,
     2019MNRAS.489.1927S); explicit values: scale height 0.2 x max radius (2017ApJ...850..180J), z0 = 100 pc for
     CO (2024A&A...690A.169L), h_z = 150 pc (2016ApJ...823...68S), 317 pc (2019A&A...632A..33A), 0.04" ~ 300 pc
     (2018MNRAS.479.5440L), h_z = 0.15 R_1/2 (2025MNRAS.536.3757A). 2020Natur.581..269N tested a thick disk
     against the thin default.
   - Dispersion: constant with radius in most parametric fits (2019ApJ...883..193N, 2020ApJ...892...68N,
     2025MNRAS.536.3757A, 2018ApJ...864L..11X); free per ring in 3DBarolo (2024A&A...690A.169L,
     2025NatAs...9.1553F).
   - Non-circular terms: radial velocity v_rad per ring (2019A&A...632A..61G, 2021A&A...656A..60A,
     2024A&A...690A.169L), vertical velocity scanned at fixed values (2019A&A...632A..61G: 0, 25, 50, 100,
     150 km/s), radial motions in 20 bins (2025A&A...700A.285W).
   - 3DBarolo options seen: AZIM normalisation (2025NatAs...9.1553F), local normalisation (2024ApJ...969..122Y),
     |cos theta|^2 weighting for the rotation fits and sin^2 phi weighting for the separate radial-velocity fit
     (2024A&A...690A.169L). GIPSY rotcur: UNIFORM weighting with 0 deg exclusion angle (2017ApJ...845..138S).

5. **Fit in stages, then fix the geometry.** This staged recipe is the most consistent pattern in the pack.
   - General shape: first fit with the poorly known geometry free, then fix or regularise PA and i (median,
     mean or Bezier/polynomial) and refit only the kinematics. Parameters that were fixed from independent data
     before the fit (step 2) stay fixed; do not free them in stage 1 just to follow the recipe. What each cited
     implementation actually releases:
     - 2024A&A...690A.169L (3DBarolo): HI fit free, then centre and V_sys fixed, geometry regularised, then
       V_rot and sigma; CO fit starts from the HI result with centre and V_sys fixed, i, PA, V_rot, sigma free,
       then i and PA fixed; v_rad fitted in a separate run (see 6e).
     - 2019A&A...632A..61G (3DBarolo): AGN position and V_sys fixed throughout; v_rot, v_rad, sigma, PA, i and
       H free, then PA and i fixed to a Bezier interpolation of the first run.
     - 2021A&A...655A..25Z (3DBarolo): centre fixed to the continuum throughout; first run i and PA free,
       second run i fixed to 44 deg (chosen by lower residuals).
     - 2021A&A...656A..60A (3DBarolo): final run with PA = 314 and i = 57 deg fixed.
     - kinemetry: free PA and i, then fixed i, then fixed PA and i (2014A&A...567A.125G, 2021A&A...652A..98G);
       fixed to medians (2019A&A...621A..83S).
     - rotcur: fix centre, then V_sys, then PA and i, finally only v_c (2017ApJ...850..180J);
       2017ApJ...845..138S.
   - Accept rings by explicit criteria: v_c > 3 dv_c, di < 50 deg and dPA < 50 deg (2017ApJ...850..180J);
     only rings above 3 sigma (2017ApJ...845..138S); error on i < 20 deg (2017MNRAS.465.4390B); drop rings with
     V_rot errors > 30 km/s (2024A&A...690A.169L).
   - Samplers for parametric fits: emcee (9 matched-step mentions in the pack software aggregate, not 9
     distinct kinematic papers; one is a CO SLED fit, 2020ApJ...889..162L; kinematic examples
     2020ApJ...892...68N, 2021AN....342.1160P, 2024A&A...684A..24P), KinMS MCMC / AdaMet (2020MNRAS.496.4061D,
     2025ApJ...992..211N), nested sampling (2025MNRAS.536.3757A), Metropolis-Hastings (2016ApJ...820L..39N).
   - Convergence: chain lengths and burn-in fractions in the parameter table are examples, not defaults, and
     ensemble "steps x walkers" are not the same unit as single-chain iterations or retained samples. Document
     a convergence check (independent starts, as 2016ApJ...820L..39N did with five starting points; trace and
     autocorrelation or effective sample size checks are general practice). The cards often do not state
     priors, walkers or convergence (2020Natur.581..269N, 2021AN....342.1160P).
   - Noise: neighbouring pixels are correlated, so the pixel chi2 is not a true chi2 (2019ApJ...883..193N).
     Some papers inflate the rms as an empirical uncertainty treatment, and the counting convention differs:
     (2N)^(1/4) with N = number of fitted pixels (2025ApJ...992..211N, N = 76,014; 2020MNRAS.496.4061D, factor
     12.47 for N = 12,112); (2N_dof)^(1/4) with N_dof the degrees of freedom, then errors from residual
     < 9 + chi2_min (2019ApJ...883..193N). State which N you used; neither is a formal correlated-noise
     likelihood.

6. **Derive physical quantities.**
   - a. Resolved disk: rotation curve and dispersion profile from the fit; v/sigma or Vmax/sigma_0
     (2020Natur.581..269N: 3.4; 2025NatAs...9.1553F: 3.58 +/- 0.74; 2019ApJ...871...85L: 7 +/- 3). Dynamical
     mass M_dyn(<R) = V^2 R / G = 2.32e5 V^2 R (V in km/s, R in kpc) for a spherical mass distribution
     (2020Natur.581..269N, which keeps the nominal mass and includes a 30% uncertainty for the spherical
     assumption; 2017ApJ...850..180J at the largest ring).
   - Pressure support: if sigma is a large fraction of V, the published corrections are distinct,
     model-dependent estimators, not interchangeable fixes. Pick the one whose dispersion model fits your
     source and state it:
     - asymmetric-drift correction to V_circ at 2 r_e (2025MNRAS.536.3757A);
     - turbulent thick-disk model following Burkert et al. (2019MNRAS.482.1499M);
     - M = R(k1^2 + 3 sigma^2)/G with k1 the first harmonic (rotation) term of a harmonic decomposition, under
       the stated assumption that the HCN dispersion comes from symmetric macroscopic motions
       (2015ApJ...806L..34F); say whether k1 is deprojected;
     - rotation and dispersion added in quadrature, with only the rotation velocity corrected for inclination
       (i = 50 deg for the upper value) and the dispersion left uncorrected (2015ApJ...806...17R).
   - b. Barely resolved or unresolved source (line-width estimators). Keep the size case explicit:
     - Marginally resolved, deconvolved size measured: M_dyn = 1.16e5 v_circ^2 D (Msun, km/s, kpc),
       v_circ = 0.75 FWHM / sin i (2019ApJ...882...10N, 2018PASJ...70...36I), D = 1.5 x the deconvolved
       major-axis FWHM (2016ApJ...816...37V, 2018PASJ...70...36I, 2024ApJ...968....9W). Sizes close to the beam
       are uncertain (2017MNRAS.465.4390B), so propagate the size error.
     - Unresolved, no reliable deconvolved size: do not invent one from the beam. Either use an independent
       size measurement, quote M_dyn as a limit from a size limit, or assume a radius and label the mass as
       assumption-driven, bracketing the radius (2017MNRAS.465.4390B assumed R = 4 kpc for its unresolved
       quasars; 2016ApJ...816...37V used 3 +/- 1 kpc for J2348-3054).
     - v_circ = 1.763 sigma / sin i with sin i = 0.45-1 for the error (2015Natur.522..455C).
     - Virial forms are separate estimators with their own geometry and radius: M_dyn(<r_1/2) = 5 sigma^2
       r_1/2 / G assumes spherical symmetry and was applied to two resolved sources (2015ApJ...812L..23S);
       C r_1/2 sigma^2 / G with C = 3.4 assumes a rotation-dominated system and takes the deconvolved major
       axis as r_1/2 (2020MNRAS.493.4294B, who note the uncertainty in C, up to a factor of two, is not in their
       error). Do not treat C = 3.4-5 as a tuning range or as a default for unresolved sources.
     - Inclination when unknown: <sin i> = pi/4 (2024ApJ...961..120C) or a fixed value such as 55 deg
       (2019ApJ...882...10N, 2018ApJ...854...97D).
     - 2024ApJ...968....9W finds two common M_dyn equations differ by a factor ~2.3 for the same sources: quote
       which one you used.
   - c. Rotation- vs dispersion-dominated: v_proj / 2 sigma_int > 0.4 means rotation-dominated
     (2024ApJ...968....9W); PVsplit classification (2025NatAs...9.1553F).
   - d. Mass budget: gas from the dynamical mass after subtracting stars and dark matter, with every component
     measured inside the same radius. 2015ApJ...812L..23S takes M_dyn(<r_1/2) and subtracts half the stellar
     mass and the dark matter to get the gas within r_1/2; subtracting the total stellar mass from an enclosed
     M_dyn underestimates the enclosed gas. Say whether the result is enclosed gas or an extrapolation to total
     gas. Dark matter is either neglected (2025NatAs...9.1553F, 2020MNRAS.496.4061D) or set to 25% of M_dyn
     (2015ApJ...812L..23S, 2015ApJ...811..124S); 2017MNRAS.469.4683C brackets 0-0.25 M_dyn.
   - e. Radial mass flow (2024A&A...690A.169L, 3DBarolo, HI): a separate run fits V_rad with all other
     parameters fixed and sin^2 phi weighting; Mdot_HI = 2 pi R Sigma_HI V_rad, assuming optically thin HI, then
     x 1.33 for helium. Apply the 1.33 only to an HI-only (or H2-only) surface density; omit it if Sigma already
     includes helium. The authors say their uncertainties preclude definitive conclusions on radial flows, so
     test the significance of V_rad (sign and size against its error, and against the PA/i uncertainty) before
     calling it inflow or outflow.

7. **Validate (see Verification checks) and report systematics separately from statistical errors**
   (2025ApJ...992..211N reports MBH and M/L as stat +/- sys).

## Parameter defaults and ranges

Counts are my own count of distinct papers in the pack lines quoted below; the longer table is in
`references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Kinematic centre | Fixed to continuum / AGN position (most frequent in the examples; no denominator) | line peak, Sersic centre, HI centre, Gaussian prior, free | 9 fix to continuum/AGN (listed in Step 2) | 2021A&A...655A..25Z, 2014A&A...567A.125G, 2020ApJ...898...75I, 2024A&A...686A..46E, 2020A&A...641A.151S, 2019A&A...632A..61G |
| Inclination from external data | Used as a fixed value, a prior, or a starting guess (say which) | fixed 22-76 deg; prior (37, 3 deg); b/a range with i free; start only | fixed 3, prior/range 2, start only 2 (my count, Step 2) | fixed: 2021A&A...655A..25Z, 2019A&A...622A..89V; prior: 2020MNRAS.496.4061D, 2019MNRAS.482.1499M; start: 2025NatAs...9.1553F |
| Intrinsic thickness q0 for axis-ratio i | 0.13-0.2 | 0.13, 0.14, 0.2 | 4 | 2017ApJ...851..126V, 2019MNRAS.482.1499M, 2019A&A...624A.138Y, 2025A&A...700A.165B |
| Ring width | 0.5-1 beam | 0.05"-1.5" (CO); 15" (HI) | 15 | 2019ApJ...871...85L, 2021ApJ...908..231M, 2025NatAs...9.1553F, 2024A&A...686A..46E, 2020ApJ...898...75I |
| Rotation curve (parametric) | arctan | flat, constant, isothermal, Bertola | 9 | 2020MNRAS.493.3744F, 2019MNRAS.482.1499M, 2016ApJ...820L..39N, 2025MNRAS.536.3757A |
| Scale height | thin disk | 1.3 pc limit to 317 pc; 0.2 R_max; 0.15 R_1/2 | 8 | 2017ApJ...850..180J, 2024A&A...690A.169L, 2019A&A...632A..33A, 2020MNRAS.496.4061D |
| Dispersion | constant (parametric, 8 papers) or free per ring (3DBarolo) | initial guesses 10-50 km/s | 10 | 2019ApJ...870...39V, 2021A&A...655A..25Z, 2025MNRAS.536.3757A |
| MCMC burn-in (examples, not a default) | 20% in 2 papers | 5-40% | 5 | 2020ApJ...892...68N, 2025ApJ...992..211N, 2020MNRAS.496.4061D, 2016ApJ...820L..39N, 2025MNRAS.541.2540Z |
| Chain length (examples; units differ) | no common value; require a documented convergence check | 50 walkers x 1000 steps (ensemble) to 3e6 iterations (single chain); 30,000 samples | 7 | 2020A&A...637A..84P, 2025ApJ...992..211N, 2020MNRAS.496.4061D, 2020ApJ...892...68N |
| Noise rescaling (empirical) | rms x (2N)^(1/4), N = fitted pixels; or (2N_dof)^(1/4) | none stated in most | 3 | 2025ApJ...992..211N, 2020MNRAS.496.4061D (pixels); 2019ApJ...883..193N (N_dof) |
| Ring acceptance | > 3 sigma | v_c > 3 dv_c; di < 20-50 deg; dV < 30 km/s | 4 | 2017ApJ...850..180J, 2017ApJ...845..138S, 2017MNRAS.465.4390B, 2024A&A...690A.169L |
| Barely resolved estimator | 1.16e5 (0.75 FWHM / sin i)^2 D, D = 1.5 x deconvolved major-axis FWHM | unresolved: assumed R = 4 kpc or 3 +/- 1 kpc, labelled as assumed | 4 + 2 | 2016ApJ...816...37V, 2018PASJ...70...36I, 2019ApJ...882...10N, 2024ApJ...968....9W; assumed size: 2017MNRAS.465.4390B |
| Virial estimators (not interchangeable) | 5 sigma^2 r_1/2 / G (spherical, within r_1/2); C = 3.4 (rotation-dominated, r_1/2 = deconvolved major axis) | C uncertain by up to x2 | 2 | 2015ApJ...812L..23S, 2020MNRAS.493.4294B |
| Rotation-dominated threshold | v_proj / 2 sigma > 0.4 | | 1 | 2024ApJ...968....9W |

## Software

Counts are mentions in matched analysis steps from the pack aggregates (not distinct papers; spellings merged
where obvious). Off-topic entries from regex mis-tags (RADEX, MOLPOP-CEP, MAGPHYS, ISHAPE, dendrogram) are
left out.

| Tool | Pack count | Used for | Examples |
|---|---|---|---|
| 3DBarolo | 30 (+2 "3D Barolo", +1 ELLPROF) | Non-parametric 3D tilted rings on the cube; V_rot, sigma, v_rad, PA, i per ring; residual cubes | 2024A&A...690A.169L, 2019A&A...632A..61G, 2021A&A...655A..25Z, 2025NatAs...9.1553F, 2021A&A...656A..60A |
| KinMS family (KinMS, KinMS_MCMC, KinMS_fitter, KinMSpy_MCMC, KinMS_fit) | 15 + 4 + 1 + 1 + 1 | Parametric 3D forward models with MCMC, gas self-gravity (gasGrav), MGE potentials | 2020ApJ...892...68N, 2025A&A...700A.285W, 2020MNRAS.496.4061D, 2014A&A...565A..59D |
| kinemetry | 12 | Harmonic decomposition of 2D velocity fields; PA, i, non-circular terms | 2014A&A...567A.125G, 2021A&A...652A..98G, 2017ApJ...843..136E, 2019A&A...621A..83S |
| emcee | 9 (one is a CO SLED fit, 2020ApJ...889..162L) | Sampler behind custom and KinMS fits | 2021AN....342.1160P, 2024A&A...684A..24P, 2020A&A...637A..84P |
| GalPak3D | 7 | Parametric 3D disk (exponential, arctan), Bayesian; also in uv plane | 2020MNRAS.493.3744F, 2025MNRAS.536.3757A |
| GIPSY rotcur (+ velfi, galmod) | 5 (+1 velfi, +1 galmod) | 2D tilted rings on velocity fields; model velocity fields; model cubes | 2017ApJ...850..180J, 2017ApJ...845..138S, 2019ApJ...871...85L, 2017MNRAS.465.4390B |
| SkySampler | 3 | Observed gas distribution as KinMS input | 2025ApJ...992..211N, 2020MNRAS.496.4061D |
| TiRiFiC | 3 | 3D tilted rings (warps) | aggregate only |
| DiskFit | 2 | Bar (m = 2) perturbation fits | 2019A&A...621A..83S |
| JAM / mge_vcirc | 2-3 | Stellar circular velocity from MGE | 2020ApJ...892...68N, 2019ApJ...883..193N |
| AdaMet, PyMultinest | 2 each | Samplers | 2025ApJ...992..211N, 2025MNRAS.536.3757A |
| qubefit, MOKA3D, pyNUFFT | 1 each | Custom MCMC disk fit; multi-shell disk; uv-plane transform | 2020Natur.581..269N, 2025A&A...701A.113M, 2025MNRAS.536.3757A |
| CASA (immoments, simobserve) | 6 + 1 + 1 | Moment maps, mock observations | 2024ApJ...968....9W, 2017ApJ...850..180J |

Recommendation: 3DBarolo when you want a non-parametric rotation curve and dispersion profile and the disk spans
several beams; KinMS or GalPak3D with an MCMC when the source is only a few beams across and you need posterior
uncertainties on a small number of parameters. Cross-check one against the other when possible
(2020Natur.581..269N: qubefit vs 3DBarolo, 279 km/s, consistent; 2020ApJ...892...68N: KinMS vs tilted-ring).

## Pitfalls

- **Beam smearing.** Low resolution biases sigma_v and r_1/2 high and V_rot low (2019MNRAS.482.1499M); the
  turnover radius may be affected (2019ApJ...870...39V); the velocity map can be "very uncertain" at low S/N
  (2018MNRAS.479.5440L). Fit a forward model that includes the beam and channel response and check it on mock
  cubes, or exclude the central beam from quantities derived from unconvolved maps (2021A&A...655A..25Z
  excluded the central 0.3").
- **Inclination.** Degenerate with V_rot at marginal resolution (2017ApJ...850..180J, 2016ApJ...816...37V);
  derived from only two successful rings, the real uncertainty "may be much larger" (2017ApJ...845..138S);
  unreliable for strong bars and solid-body velocity fields (2020ApJ...897..122L). 2020ApJ...895..135K picked
  i = 65 deg because it gave a monotonic rotation curve and checked that 53 deg gives the same conclusions:
  always show the result at the bracket of plausible inclinations (2017ApJ...845..138S: 26 and 48 deg).
- **Mergers that look like disks.** Modest resolution can misclassify mergers as disks (2025MNRAS.536.3757A);
  limited depth and resolution prevent distinguishing disk, merger and outflow (2019ApJ...887...74F). A smooth
  velocity gradient alone is not a disk.
- **Underestimated errors.** ROTCUR errors are underestimated (2017ApJ...850..180J); tilted-ring confidence
  intervals with uniform velocity errors are too small (2020ApJ...892...68N); 3DBarolo was used without error
  estimates in 2019ApJ...870...39V; correlated pixels make chi2 not a true chi2 (2019ApJ...883..193N,
  2019ApJ...881...10B with chi2_nu = 1.179 still not formally acceptable). Use the per-ring error floor of
  2017ApJ...850..180J: max of fit error, channel width, and V |sin i - sin(i +/- di)|.
- **Non-circular motions.** Bars and outflows break the circular-orbit assumption: outflow quantities can be
  upper limits because bar elliptical motions are possible (2024A&A...686A..46E); non-circular motions in barred
  galaxies were not modelled in 2019A&A...623A..79C; 2013ApJ...770L..27F judged its own masses, not corrected
  for them, to be likely lower limits. That direction is specific to that case: non-circular motions can bias a
  mass either way, so model them for your source or bracket the mass. Axisymmetric models gave large chi2
  (>= 4) in 2019A&A...632A..61G.
- **Missing flux.** Without short spacings, extended emission is lost (~50% in 2017ApJ...843..136E, 40-50% in
  2021A&A...656A..60A, MRS 6.2" in 2020A&A...641A.151S), which truncates the outer rotation curve and biases
  surface-brightness-weighted models.
- **Distance and mass-model systematics.** Distance can dominate (~30% in M_BH, 2025ApJ...992..211N; 10% not
  included in 2025MNRAS.541.2540Z); mass-model parameters are degenerate (2021A&A...656A..60A); dark-matter
  density and scale length cannot both be constrained from ~5 kpc coverage (2025A&A...701A.113M).
- **Lensing.** Source-plane kinematics inherit magnification systematics (up to ~25% in 2025NatAs...9.1553F).
- **Unreported settings.** The cards rarely state 3DBarolo parameter files (ring widths, mask, normalisation:
  2019A&A...632A..61G, 2021A&A...655A..25Z, 2024A&A...690A.169L, 2025NatAs...9.1553F) or MCMC priors, walkers
  and convergence (2020Natur.581..269N, 2014A&A...565A..59D, 2024A&A...684A..24P, 2021AN....342.1160P). Across
  the pack, CASA version (13), line-free channels for continuum (7) and self-calibration intervals (6) top the
  "not stated" list (pack aggregates); the same list also flags flux calibrator and flux-scale uncertainty (6),
  moment-map clipping thresholds (4), clean thresholds and masks, and primary-beam correction (2), and the cards
  for 2025A&A...700A.285W and 2017MNRAS.465.4390B do not state the rest frequency or the rotcur set-up. Write
  them down, along with the velocity frame and definition.

## Verification checks

What papers did:
- Residual cube or velocity map after subtracting the beam-convolved model: residuals below 3 sigma
  (2020Natur.581..269N); |V_residual| < 15 km/s (2025ApJ...992..211N); < 30 km/s (2017ApJ...845..138S,
  2021A&A...656A..60A); mean <data - model> = 17 +/- 9 km/s (2019MNRAS.482.1499M); moment-0 residual 2% vs 5%
  used to choose between runs (2021A&A...655A..25Z).
- PV diagrams of data and model along the major and minor axes (2019A&A...632A..61G, 2021A&A...655A..25Z,
  2025ApJ...992..211N).
- A second, independent method: 2D vs 3D geometry agreement (2021A&A...656A..60A); 3DBarolo vs qubefit
  (2020Natur.581..269N); envelope tracing vs arctan fit (2019ApJ...871...85L); line-width estimate vs disk fit
  (2020Natur.581..269N, 300 +/- 50 vs 272 km/s); velocity model vs axis ratio (2017ApJ...851..126V).
- Mock cubes with the same beam and noise: Vmax/sigma_0 overestimated by 4 +/- 2% (2025NatAs...9.1553F);
  parameters recovered within 3 sigma (2025MNRAS.536.3757A); ~1 dex systematic on M_dyn at low resolution
  (2017ApJ...850..180J).
- Sensitivity to set-up: other ring widths (2017ApJ...843..136E), other weighting (2020MNRAS.493.3744F),
  inclination bracket (2017ApJ...845..138S), inner vs outer cube consistency (2025A&A...700A.285W), five
  starting points for MCMC convergence (2016ApJ...820L..39N), model comparison by BIC (2024A&A...684A..24P:
  delta BIC > 100 for non-parametric rings over an exponential disk, for its JWST Halpha velocity map, not the
  ALMA data).
- External consistency: PA and i against literature (2014A&A...567A.125G), PA against PaFit
  (2025A&A...701A.113M), M_dyn against gas + stellar mass (2025NatAs...9.1553F, 2015ApJ...806...17R).

What a careful referee adds:
- Is the disk resolved by >= 2-3 beams along the major axis? If not, why a tilted-ring fit at all?
- Are the fixed parameters (centre, i, PA) independently justified, and how do V(R) and M_dyn move over their
  uncertainty?
- Is sigma from a forward model that includes the beam, not moment 2, and was that model checked on mocks?
- For MCMC fits: is convergence documented (several starts, chain diagnostics), not only a chain length?
- Are all datasets on one velocity frame, definition and rest frequency before V_sys or tracers are compared?
- Is the quoted M_dyn at a radius actually sampled by the data, with the formula and geometry stated?
- Were residuals inspected for a second component (outflow, bar, merger companion) before calling it a disk?

## Source cards

Full list: `references/sources.md`. Most informative for this technique:

- 2017ApJ...850..180J: rotcur on z~4-6 [CII], ring acceptance rules, GALMOD dispersion grid, mock systematics.
- 2024A&A...690A.169L: staged 3DBarolo HI then CO fits, ring rejection, radial mass flows.
- 2019A&A...632A..61G: 3DBarolo with v_rad and v_vert, Bezier-regularised geometry, kinemetry benchmark.
- 2014A&A...567A.125G: kinemetry three-step geometry fit, harmonic order 3.
- 2021A&A...652A..98G: kinemetry on GATOS Seyferts, 32 ellipses.
- 2021A&A...655A..25Z: 3DBarolo with fixed inclination, residual-cube outflows.
- 2021A&A...656A..60A: 2D vs 3D tilted rings, radial motions, mass model.
- 2020Natur.581..269N: qubefit thin-disk MCMC, M_dyn formula, cross-check with 3DBarolo.
- 2025NatAs...9.1553F: 3DBarolo on source-plane cubes, mock-cube bias test.
- 2025MNRAS.536.3757A: GalPak3D in the uv plane, priors, simulation recovery.
- 2020ApJ...892...68N: KinMS + emcee, chain settings, tilted-ring cross-check.
- 2025ApJ...992..211N: KinMS + AdaMet, noise rescaling, systematic tests.
- 2020MNRAS.496.4061D: KinMS_MCMC priors, disk thickness limit.
- 2019ApJ...883..193N: KinMS + mpfit, correlated-pixel caveat.
- 2017ApJ...845..138S: rotcur on a z = 6.13 quasar host, inclination bracket.
- 2019ApJ...871...85L: rotcur, envelope tracing, arctan fit.
- 2019MNRAS.482.1499M: arctan disk fit with axis-ratio inclination, beam-smearing caveat.
- 2024ApJ...968....9W: v/sigma classification and unresolved M_dyn equations.
- 2016ApJ...816...37V: unresolved M_dyn estimator and inclination degeneracy.
- 2019A&A...621A..83S: kinemetry, Bertola model and DiskFit bar perturbations.
