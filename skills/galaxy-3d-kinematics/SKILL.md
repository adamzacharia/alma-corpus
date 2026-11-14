---
name: alma-galaxy-3d-kinematics
description: "Model the gas kinematics of galaxies in ALMA line cubes (CO, [CII], [CI], HCN, HI comparisons): 3D tilted-ring and parametric disk fits to the cube (3DBarolo, KinMS, GalPak3D, qubefit, TiRiFiC), 2D velocity-field fits (kinemetry, GIPSY rotcur, DiskFit, arctan models), rotation curves, velocity dispersion, v/sigma, asymmetric drift, non-circular, bar-driven and radial motions, and dynamical masses, including the simple FWHM and virial estimators used for barely resolved high-z sources. Use when deriving a rotation curve, inclination, PA, intrinsic dispersion or dynamical mass of a galaxy or circumnuclear disk, classifying a source as rotation- or dispersion-dominated, or checking someone else's kinematic fit for beam smearing and inclination problems. Built from 341 ALMA papers (2013-2026)."
---

# 3D kinematic modelling of galaxies (tilted rings, disks)

Fits a model of rotating (and possibly inflowing, outflowing or warped) gas to a galaxy line cube to recover V(R),
sigma(R), geometry (centre, PA, inclination, V_sys) and a dynamical mass. The two mistakes that matter most:
(1) **beam smearing** of the inner rotation curve into the line width, which biases sigma high and Vrot low
(2019MNRAS.482.1499M) unless the model forward-models the beam and spectral response and is shown to recover known
inputs on mock data (2017ApJ...850..180J; 2025NatAs...9.1553F, card); (2) the **inclination-velocity degeneracy**:
at marginal resolution i and peak velocity "cannot be independently determined" (2016ApJ...816...37V,
2017ApJ...850..180J), and M_dyn scales as 1/sin^2 i. "(card)" marks a claim taken verbatim from the paper's card
because the pack lists that paper only bibliographically.

> Always report: tracer and cube (weighting, channel spacing and effective spectral resolution, pixel size, mask),
> which parameters were free or fixed (and from what data), ring width, normalisation and weighting, likelihood and
> noise treatment, how errors were derived, and the radius at which M_dyn is quoted. Report the velocity frame,
> velocity definition, rest frequency and V_sys zero point (the NGC 1068 cards give V_sys = 1120 +/- 3 km/s LSR,
> 2019A&A...632A..61G, and 1127 +/- 3 km/s heliocentric, 2014A&A...567A.125G, for the same disk). Report the near
> side and the PA and V_rad sign conventions. Report primary-beam correction (and the noise map used), flux-scale
> uncertainty, clean threshold and mask, and the clipping rule behind moment maps; the cards flag these as missing
> (see Pitfalls). For 3DBarolo also give MASK (SNRCUT, GROWTHCUT, MINCHANNELS), NORM, WFUNC, FTYPE, LTYPE and z0,
> as 2023A&A...672A.106L, 2025A&A...693A..91L and 2024ApJ...977..161V do.

## When to use

- Line emission resolved by at least a few beams along the major axis, and you need V(R), sigma(R), PA, i or
  V_sys: nearby spirals and Seyferts (2024A&A...690A.169L, 2021A&A...656A..60A, 2019A&A...632A..61G), high-z
  [CII] disks (2020Natur.581..269N, 2017ApJ...850..180J, 2018ApJ...864L..11X), cosmic-noon CO and [CI] disks with
  mass models (2023A&A...672A.106L, 2025A&A...693A..91L).
- Deciding whether a high-z source is a disk or a merger (2025MNRAS.536.3757A, card: 12 of 20 DSFGs with SNR > 8
  disk-like; 2024ApJ...968....9W, card: 10 of 23 quasar hosts rotation-dominated; 2024ApJ...977..161V tests five
  literature criteria).
- Bar-driven flows and non-circular motions (2024MNRAS.528.6768H, 2014A&A...567A.125G, 2021A&A...652A..98G);
  dynamical masses for gas fractions, alpha_CO or M_BH/M_host (2015ApJ...812L..23S, 2017ApJ...845..138S).
- Separating a disk from residual outflow emission (2021A&A...655A..25Z builds the outflow from the 3DBarolo
  residual cube), with the lower-limit caveat in Pitfalls.

## When not to use

| Situation | Use instead |
|---|---|
| Protoplanetary or circumstellar Keplerian disks | `keplerian-disk-kinematics` skill |
| Black hole mass from a circumnuclear disk (MGE, M/L, point mass) | `smbh-gas-dynamics`; this skill covers only the shared disk-fitting part (2020ApJ...892...68N, 2025ApJ...992..211N) |
| Protostellar envelopes (infall plus rotation in PV diagrams) | `envelope-kinematics-pv` skill |
| Source unresolved or resolved by about one beam | No tilted-ring fit; use a line-width estimator with a stated inclination (Step 6b) and call it order-of-magnitude (2015Natur.522..455C: "very uncertain"; 2017ApJ...850..180J: ~1 dex systematic in mock tests) |
| Lensed source | Either reconstruct the source plane and fit there (2025NatAs...9.1553F, card) or forward-model lens and disk together in the visibilities (2020Natur.584..201R); carry the lens-model uncertainty either way (`lens-modelling`) |
| Only maps of velocity and line width | `moment-maps` skill |
| Outflow mass, rate and energetics | `outflow-energetics`, after removing the disk model |
| Disk stability (Toomre Q) | `toomre-stability`, fed with V(R) and sigma(R) from here |

## Steps

1. **Prepare the cube.**
   - Goal: a continuum-subtracted cube whose beam, channel spacing, spectral resolution and noise are known,
     because the model is convolved with that response and compared voxel by voxel.
   - Weighting: natural for faint or high-resolution fits (2019ApJ...883..193N; 2021A&A...654A..37D, robust 2);
     Briggs 0.5 in 2022MNRAS.516.4066L and for re-imaged survey cubes (2024ApJ...968....9W, card). Test it:
     2020MNRAS.493.3744F refit cubes imaged at robust 0.5 and -1.0.
   - Rebin or smooth if S/N is low (2025PASJ...77..432U: 40 km/s bins). Smoothing coarsens the resolution, not
     only the spacing: 2023A&A...672A.106L tested cubes with 5 km/s channels and 10 km/s resolution.
   - Check line coverage before fitting widths, dispersion, V_sys or line-width masses. In 2021A&A...654A..37D the
     line of W0410-0913 falls partly outside the SPW (only its blue wing is sampled); in 2021MNRAS.503.5583B the
     blue CO(7-6) wing of G1234S is contaminated by the adjacent [CI](2-1) line.
   - Build the fitting mask in 3D: 3DBarolo SEARCH or SMOOTH&SEARCH, SNRCUT 3-7 and GROWTHCUT 2-4.5 in the pack
     (2023A&A...672A.106L: FACTOR 1.5, SNRCUT 4, GROWTHCUT 3, MINCHANNELS 3; 2025A&A...693A..91L;
     2025PASJ...77..432U; 2025MNRAS.538.3001T). Full list with memberships in `references/parameters.md`.
   - Check imaging does not drive the answer (2022MNRAS.516.4066L: tclean vs GIPSY cubes; Gaussian rms map).

2. **First guesses for the geometry; decide what to fix.** Memberships for every count are in
   `references/parameters.md`.
   - Centre: 17 papers in the pack fix it to the continuum or AGN position (my count of parameter, assumption and
     excerpt lines; a count of examples, not a majority, since the pack gives no denominator). Alternatives: line
     peak (2019MNRAS.482.1499M), moment-0 Gaussian fit (2026A&A...707A.252K), imfit or Sersic centre
     (2025MNRAS.538.3001T, 2021ApJ...908..231M), a 1" Gaussian prior (2025MNRAS.536.3757A), or free in a first
     stage (2025PASJ...77..432U).
   - Inclination: say whether an external value is fixed (2021A&A...655A..25Z: 44 deg from GALEX UV), a prior
     (2020MNRAS.496.4061D: 37 +/- 3 deg) or only a start (2021A&A...654A..37D: 45 deg, allowed 10-80 deg).
     2023A&A...672A.106L found some best-fit values depend on the initial guesses: rerun from other starts.
   - Axis-ratio inclination (general practice): cos^2 i = (q^2 - q0^2)/(1 - q0^2); q0 from 0.1 to 0.25 in the pack,
     0.2 in 4 of 10 papers (my count). Plain i = arccos(b/a) assumes a thin disk (2024ApJ...968....9W);
     2024ApJ...977..161V notes its thin-disc fit may overestimate i by about 7 deg.
   - PA from the velocity field (kinemetry: 2014A&A...567A.125G) or the steepest-gradient PV cut.
   - Near side: fix it from independent data before reading V_rad as inflow or outflow. 2022MNRAS.516.4066L took the
     western side as near from HST dust lanes, which makes its radial motions an inflow.

3. **Choose the modelling approach.**
   - 3D cube fitting when beam smearing matters: 3DBarolo for non-parametric tilted rings; KinMS, GalPak3D or
     qubefit for parametric disks with a sampler.
   - 2D velocity-field fitting (kinemetry, rotcur, DiskFit) suits well-resolved nearby disks and harmonic analysis.
     An unconvolved model fitted to moment 1 is vulnerable to beam smearing of the inner rise; a 2D fit handles it
     only if model observables pass through the same beam and moment process as the data.
   - Whatever the dimensionality, trust comes from a forward model of the response plus a recovery test on mocks
     with the same beam and noise (2017ApJ...850..180J; 2025MNRAS.536.3757A, card: true inputs recovered within
     3 sigma); a beam-convolved 3D fit can still be degenerate.
   - uv-plane fitting for faint sources: 2025MNRAS.536.3757A (card) transforms GalPak3D models per channel with
     pyNUFFT and samples with PyMultinest; 2020Natur.584..201R fits lens and 3D disk together in the visibilities.
   - Non-axisymmetric motions need their own model compared with pure rotation (2021A&A...654A..24B: DiskFit
     harmonic models judged by chi2 and residuals; 2024MNRAS.528.6768H: KinMS bar flow kept only if the BIC drops).

4. **Set up the model.** Per-paper settings are in `references/parameters.md`.
   - Ring width: tie it to the beam. 20 papers in the pack state a beam-based rule (my count; papers with
     stage-specific widths sit in more than one group): 9 use about half a beam at some stage (sqrt(a b)/2 in
     2023A&A...672A.106L and 2024ApJ...977..161V; half the beam in 2025A&A...693A..91L and 2025PASJ...77..432U), 5
     use beam/2.5 or 0.4 beam along one axis (minor axis in 2021A&A...654A..37D; major axis in 2026A&A...707A.252K),
     7 use about one beam at some stage (2022MNRAS.516.4066L: sqrt(a b), "fully independent"; 2022ApJ...934..173S:
     one unit, then half in its second stage). Rings narrower than about half a beam are not independent: count
     independent points per beam (2024ApJ...977..161V keeps at least three beyond the beam).
   - Rotation curve (parametric): arctan recurs (at least 15 pack papers, my count, e.g. 2020MNRAS.493.3744F,
     2025PASJ...77..432U); flat (2016ApJ...820L..39N) and isothermal (2025MNRAS.536.3757A, card) also occur. No
     denominator compares the forms, so this is a recurring example, not a measured majority.
   - Surface brightness: exponential disk examples (2020Natur.581..269N, 2019ApJ...882...10N); KinMS SkySampler
     uses the observed distribution (2025ApJ...992..211N). Recommendation: start exponential for a few-beam source.
   - Thickness: thin-disk assumptions recur (2022ApJ...934..173S, 2021A&A...654A..37D, 2025MNRAS.537..520Z with
     z0 = 0); no denominator, so these are examples. Stated gas scale heights: about 100 pc in 6 papers and 300 pc
     in 4 (my count; list in parameters.md), plus 0.1 R_1/2 (2024ApJ...977..161V) and 0.15 R_1/2
     (2025MNRAS.536.3757A, card). Do not borrow a stellar height for the gas: 2019A&A...632A..33A's h_z = 317 pc goes
     with its stellar M/L, not its 3DBarolo gas disk.
   - Dispersion: radially constant in parametric examples (2020MNRAS.496.4061D, 2019MNRAS.485.4359S), free per
     ring in 3DBarolo, or one SPACEPAR value (2023A&A...672A.106L, 2025A&A...693A..91L). Starting guesses span
     10-300 km/s (2021A&A...647A.194F) and 30-150 km/s (2024ApJ...977..161V).
   - Non-circular terms: v_rad per ring, vertical velocity scanned at fixed values (2019A&A...632A..61G).
   - 3DBarolo: NORM=AZIM assumes an axisymmetric disk (2023A&A...672A.106L); LOCAL or pixel-by-pixel follows
     clumps and arms (2025MNRAS.537.1163A, 2022ApJ...934..173S). WFUNC=0 for geometry, then |cos theta|^2 (WFUNC=2)
     for V_rot (2023A&A...672A.106L, 2025A&A...693A..91L). FTYPE=2 |M - D| is the default.

5. **Fit in stages, then fix the geometry.** The most consistent pattern in the pack.
   - First fit with the poorly known geometry free, then fix or regularise PA and i and refit only the kinematics.
     Parameters fixed from independent data in Step 2 stay fixed. Regularisation differs: Bezier (REGTYPE bezier,
     2024ApJ...977..161V; 2019A&A...632A..61G), ring mean ("twostage=true" and "polyn=0" in 2022MNRAS.516.4066L;
     ring averages in 2021A&A...654A..37D), median over rings and lines (2023A&A...672A.106L). Per-paper sequences
     are in `references/parameters.md`.
   - Accept rings by explicit criteria (v_c > 3 dv_c, di and dPA < 50 deg: 2017ApJ...850..180J; drop points inside
     the beam: 2024ApJ...977..161V, 2022ApJ...934..173S). For parametric fits, 2024MNRAS.528.6768H rejects any
     parameter whose 16th-84th percentile width exceeds half its prior range.
   - Samplers: emcee (34 matched-step mentions, not distinct papers; one is a CO SLED fit, 2020ApJ...889..162L,
     card), KinMS Gibbs MCMC (2019MNRAS.485.4359S), AdaMet (2025ApJ...992..211N), MultiNest (2020Natur.584..201R).
   - Convergence: chain lengths and burn-in in the pack are examples, not defaults, and walkers x steps differ from
     single-chain iterations. Document a check: five starting points (2016ApJ...820L..39N, card), acceptance
     fraction and corner plots (2023A&A...672A.106L).
   - Noise: neighbouring pixels are correlated, so pixel chi2 is not a true chi2 (2019ApJ...883..193N). Some
     papers inflate the rms empirically: (2N)^(1/4) with N = fitted pixels (2025ApJ...992..211N,
     2020MNRAS.496.4061D) or (2N_dof)^(1/4) (2019ApJ...883..193N). State which N you used.
   - 3DBarolo errors are the change that raises the residual by 5% (2022ApJ...934..173S, 2023A&A...672A.106L);
     2024ApJ...977..161V says its MCMC errors are not statistical errors. Do not treat them as Gaussian 1 sigma
     without a mock or bootstrap test (2019MNRAS.485.4359S bootstrapped 16 half-cube subsets).

6. **Derive physical quantities.**
   - a. Resolved disk: V(R), sigma(R), v/sigma (2025NatAs...9.1553F, card: Vmax/sigma_0 = 3.58 +/- 0.74).
     M_dyn(<R) = V^2 R / G = 2.32e5 V^2 R (km/s, kpc) for a spherical mass (2020Natur.581..269N keeps the nominal
     mass and includes a 30% uncertainty for the spherical assumption; 2017ApJ...850..180J at the largest ring).
   - Dispersion near the instrumental limit: whether sigma is a measurement or an upper limit depends on the
     modelled spectral response (channel spacing and any smoothing), S/N and recovery tests, not on channel spacing
     alone. 2023A&A...672A.106L built mocks with known V_rot and sigma, retested with 5 km/s channels at 10 km/s
     resolution, and then adopted its 15 km/s channel width as a conservative, source-specific upper limit.
   - Pressure support: distinct, model-dependent estimators (list in parameters.md), skipped at large V/sigma
     (2023A&A...672A.106L, V_rot/sigma_CO >~ 17-22). The asymmetric-drift correction V_c = sqrt(V_rot^2 + V_A^2)
     assumes isotropic dispersion and constant scale height (2022ApJ...934..173S, errors not propagated).
   - b. Barely resolved or unresolved (line-width estimators). Keep the size case explicit:
     - Marginally resolved: M_dyn = 1.16e5 v_circ^2 D (Msun, km/s, kpc), v_circ = 0.75 FWHM / sin i
       (2019ApJ...882...10N, 2018PASJ...70...36I), D = 1.5 x deconvolved major-axis FWHM (2016ApJ...816...37V;
       2024ApJ...968....9W). Propagate the size error and compare with a disk model when one exists.
     - Unresolved: do not take a size from the beam. Use an independent size, a size limit, or an assumed radius
       labelled as such and bracketed (2017MNRAS.465.4390B: R = 4 kpc; 2016ApJ...816...37V: 3 +/- 1 kpc).
       2025A&A...696A..88W treats such masses as upper limits (dispersion) or lower limits (rotation).
     - Virial forms are separate estimators; see the table below. Name the coefficient and its source.
     - Unknown i: <sin i> = pi/4 (2024ApJ...961..120C), 1/<sin^2 i> = 3/2 (2026ApJ...997..218A) or fixed 55 deg
       (2019ApJ...882...10N) are different averages. Two common M_dyn equations differ by ~2.3 (2024ApJ...968....9W,
       card): quote yours.
   - c. Rotation vs dispersion: v_proj / 2 sigma_int > 0.4 (2024ApJ...968....9W, card); V/sigma > 3 plus four more
     criteria (2024ApJ...977..161V); PVsplit (2025NatAs...9.1553F, card). The thresholds differ; quote yours.
   - d. Mass budget: subtract stars and dark matter inside the same radius as M_dyn (2015ApJ...812L..23S, card:
     half the stellar mass and M_DM = 0.25 M_dyn within r_1/2). With a resolved curve, fit a mass model (ROTMOD and
     emcee, 2023A&A...672A.106L; vcdisk, 2025A&A...693A..91L) and expect a disk-halo degeneracy.
   - e. Radial flows: a separate V_rad run with the other parameters fixed and sin^2 phi weighting, then Mdot_HI = 2
     pi R Sigma_HI V_rad x 1.33 for helium on an HI-only Sigma, for optically thin HI (2024A&A...690A.169L, card;
     its authors say uncertainties preclude definitive conclusions). Report radial motion without calling it inflow
     or outflow unless the near side and sign conventions are stated (Step 2). In 2022MNRAS.516.4066L, M_gas V_rad /
     R is an upper limit, and V_rad differs by ~5 between 3DBarolo (~75 km/s) and KinMS (~15 km/s) because it
     trades off against sigma.

7. **Validate (see Verification checks)** and report systematics apart from statistical errors.

## Parameter defaults and ranges

Counts are my own counts of distinct papers in the pack lines; memberships and longer tables are in
`references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Kinematic centre | continuum / AGN position (examples, no denominator) | line peak, moment-0 fit, Sersic centre, prior, free | 17 | 2021A&A...655A..25Z, 2020ApJ...898...75I, 2024A&A...686A..46E |
| Inclination from external data | fixed, prior or start (say which) | fixed 44-76 deg; prior (37, 3 deg); start 45 deg within 10-80 deg | fixed 2, prior 2, start 3 | 2019A&A...622A..89V, 2020MNRAS.496.4061D, 2021A&A...654A..37D |
| q0 for axis-ratio i | 0.2 (4 of 10) | 0.1-0.25 | 10 | 2019MNRAS.482.1499M, 2024ApJ...977..161V |
| Ring width | half a beam (sqrt(a b)/2) | beam/2.5 to 1 beam; 0.0138" to 2" in CO cubes | 20 state a beam rule | 2023A&A...672A.106L, 2026A&A...707A.252K, 2023A&A...673A..46B |
| 3DBarolo mask | SEARCH or SMOOTH&SEARCH | SNRCUT 3-7; GROWTHCUT 2-4.5; MINCHANNELS 2-5 | 14 | 2023A&A...672A.106L, 2025MNRAS.538.3001T |
| NORM / WFUNC | AZIM; WFUNC 0, then 2 | LOCAL / pixel-by-pixel; cos theta | 9 | 2025A&A...693A..91L, 2025MNRAS.537.1163A |
| Gas scale height | thin; 100 pc (6) or 300 pc (4) when stated | z0 = 0 to 300 pc; 0.1-0.15 R_1/2 | 13 | 2022MNRAS.516.4066L, 2025A&A...693A..91L |
| Dispersion | constant, per ring, or one SPACEPAR value | starts 10-300 km/s; SPACEPAR grids 1-60 to 1-200 km/s | examples | 2021A&A...647A.194F, 2024ApJ...977..161V |
| Rotation-dominated | v_proj / 2 sigma > 0.4, or V/sigma > 3 | | 2 | 2024ApJ...968....9W (card), 2024ApJ...977..161V |

Dynamical-mass estimators (not interchangeable; keep each row's support assumption and radius):

| Estimator | Support and radius | Paper |
|---|---|---|
| V^2 R / G = 2.32e5 V^2 R | rotation, spherical; R = 3 exponential scale lengths; 30% geometry uncertainty | 2020Natur.581..269N |
| 1.16e5 (0.75 FWHM / sin i)^2 D | rotation, thin disk; D = 1.5 x deconvolved major-axis FWHM | 2016ApJ...816...37V, 2018PASJ...70...36I |
| 5 sigma^2 r_1/2 / G | spherical; within r_1/2; applied to two resolved sources | 2015ApJ...812L..23S (card) |
| C r_1/2 sigma^2 / G, C = 3.4 | rotation-dominated; r_1/2 = deconvolved major axis; C uncertain by up to x2, not in the error | 2020MNRAS.493.4294B (card) |
| alpha sigma_v^2 r / G, alpha = 3.4 | dispersion-supported; r = radius of the outermost 3DBarolo ring | 2021A&A...654A..37D |
| K(n) K(q) sigma^2 r / G | virialized, dispersion-dominated; q = 1 and n = 1 give an upper limit | 2025ApJ...987L..37W |

## Software

Counts are mentions in matched analysis steps from the pack software aggregate (not distinct papers). I merged
spellings: 3DBarolo = 3dbarolo 89 + 3d-barolo 22 + 3d barolo 5 + "3dbarolo (version 1.6)" 4 + bbarolo 3; KinMS =
kinms 54 + kinms_mcmc 13 + kinms_fitter 9 + kinmspy_mcmc 5. Off-topic tags (RADEX, CIGALE, MAGPHYS) are left out.

| Tool | Pack count | Used for | Examples |
|---|---|---|---|
| 3DBarolo | 123 (89 + 22 + 5 + 4 + 3) | Non-parametric 3D tilted rings; SEARCH masks; SPACEPAR; residual cubes | 2023A&A...672A.106L, 2024ApJ...977..161V |
| KinMS family | 81 (54 + 13 + 9 + 5) | Parametric 3D forward models with MCMC; MGE potentials | 2020ApJ...892...68N, 2021MNRAS.504.4123N |
| emcee | 34 | Sampler for cube fits and rotation-curve mass models | 2022MNRAS.516.4066L, 2021Sci...371..713L |
| CASA (+ tclean 4, immoments 4, simobserve 2) | 26 | Imaging, moments, mock observations | 2022MNRAS.516.4066L |
| kinemetry | 21 | Harmonic decomposition of 2D velocity fields | 2014A&A...567A.125G, 2021A&A...652A..98G |
| GalPak3D | 17 | Parametric 3D disk, Bayesian; also uv plane | 2020MNRAS.493.3744F, 2025MNRAS.536.3757A |
| SkySampler | 13 | Observed gas distribution as KinMS input | 2025ApJ...992..211N |
| GasTimator 8; JAMPy 6, JAM 3, MgeFit 3 | as listed | KinMS sampler; stellar potential from MGE | 2020ApJ...892...68N |
| GIPSY rotcur (+ gipsy 4) | 6 | 2D tilted rings on velocity fields | 2017ApJ...850..180J, 2017ApJ...845..138S |
| TiRiFiC 5; DiskFit, MultiNest, CANNUBI, DUCHAMP 4 each | as listed | Warped rings; harmonic models; nested sampling; geometry; source finding | 2021A&A...654A..24B, 2020Natur.584..201R, 2025A&A...701A.120P |
| qubefit, AdaMet, PyMultinest | 3 each | Disk MCMC; KinMS sampler; nested sampling | 2020Natur.581..269N, 2025ApJ...992..211N |

Recommendation: 3DBarolo for a non-parametric V(R) and sigma(R) over several beams; KinMS or GalPak3D with a
sampler for a few-beam source with few parameters. Cross-check one against the other (2020Natur.581..269N:
qubefit vs 3DBarolo; 2022MNRAS.516.4066L: 3DBarolo vs KinMS).

## Pitfalls

- **Beam smearing.** Biases sigma and r_1/2 high and V_rot low (2019MNRAS.482.1499M); map-based rotation-support
  estimates can be biased by it (2021A&A...654A..37D). Forward-model the response and test on mocks, or exclude
  the central beam (2022ApJ...934..173S).
- **Inclination.** Degenerate with V_rot at marginal resolution (2017ApJ...850..180J); from only two rings the real
  uncertainty "may be much larger" (2017ApJ...845..138S). Show results at the bracket of plausible i.
- **Spectral response and line coverage.** Channel spacing is not resolution, and truncated or blended lines bias
  widths and V_sys (Step 1; 2023A&A...672A.106L, 2021A&A...654A..37D, 2021MNRAS.503.5583B).
- **Tracer mismatch.** Matching velocity conventions does not make tracers equivalent: ionized-gas dispersions can
  be 10-15 km/s higher than molecular ones (2020Natur.584..201R), and in low-EW(Halpha) galaxies eDIG contaminates
  the dispersion and breaks the thin-disk, constant-height ADC assumptions (2022ApJ...934..173S). Compare tracers
  at matched spatial and spectral response and check each tracer's support separately.
- **Disk subtraction absorbs the residual component.** 2025A&A...693A..91L says its residual (non-circular) fluxes
  are lower limits because the axisymmetric model averages all emission in a ring and low-S/N tail pixels are
  excluded. Test normalisation and masks, and report residual flux as a lower limit where this applies.
- **Inflow vs outflow.** A significant V_rad sign does not settle direction; it needs the near side
  (2022MNRAS.516.4066L) and stated sign conventions. 2024MNRAS.528.6768H notes its bisymmetric model cannot tell
  inflow from outflow.
- **Mergers that look like disks.** Modest resolution can misclassify mergers as disks (2025MNRAS.536.3757A, card);
  2024ApJ...977..161V cannot cleanly separate discs from compact mergers. A smooth gradient alone is not a disk.
- **Underestimated errors.** ROTCUR errors are underestimated; use the per-ring floor max(fit error, channel width,
  V |sin i - sin(i +/- di)|) (2017ApJ...850..180J). Pixels are correlated (2019ApJ...883..193N).
- **Non-circular motions** can bias masses either way; 2013ApJ...770L..27F (card) judged its own uncorrected masses
  likely lower limits, which is specific to that case. Model them or bracket the mass.
- **Missing flux.** Without short spacings extended emission is lost (2014A&A...565A..97C: up to a factor ~2;
  2024A&A...691A.118K), truncating the outer curve. **Lensing:** magnification uncertainty up to ~25%
  (2025NatAs...9.1553F, card).
- **Unreported settings.** Pack "not stated" aggregate, exact labels: "casa version" 19, "line-free channels used for
  continuum" 13, "line-free channels used for continuum subtraction" 12, "line-free channel ranges for continuum
  subtraction" 9, "flux calibrator and flux scale uncertainty" 6, "self-calibration solution intervals" 6,
  "moment-map clipping thresholds" 4, "primary beam correction details" 3, "primary-beam correction details" 2,
  "primary beam correction" 2. The phrasings overlap, so do not sum them. Cards also often lack 3DBarolo parameter
  files and MCMC priors, walkers and convergence.

## Verification checks

What papers did:
- Residual cube or velocity map after subtracting the convolved model (2025ApJ...992..211N; 2021A&A...655A..25Z
  used moment-0 residuals to choose between runs; 2025PASJ...77..432U inspected residual velocities).
- PV diagrams of data and model along major and minor axes (2022MNRAS.516.4066L, 2025PASJ...77..432U).
- An independent second method: 3DBarolo vs qubefit (2020Natur.581..269N); 3DBarolo vs KinMS
  (2022MNRAS.516.4066L); 2D vs 3D geometry (2021A&A...656A..60A).
- Mock cubes with the same beam and noise: Vmax/sigma_0 overestimated by 4 +/- 2% (2025NatAs...9.1553F, card);
  inputs recovered within 3 sigma (2025MNRAS.536.3757A, card); ~1 dex on M_dyn (2017ApJ...850..180J); known
  V_rot and sigma for dispersion limits (2023A&A...672A.106L).
- Set-up sensitivity: spectral resolution degraded to MaNGA and CALIFA values and refit (2022ApJ...934..173S); a
  20 km/s-bin cube for sigma (2025PASJ...77..432U); weighting (2020MNRAS.493.3744F); five MCMC starts
  (2016ApJ...820L..39N, card); bootstrap of half-cube subsets (2019MNRAS.485.4359S).

What a careful referee adds:
- Is the disk resolved by >= 2-3 beams along the major axis? If not, why a tilted-ring fit?
- Are fixed parameters (centre, i, PA, near side) independently justified, and how do V(R) and M_dyn move?
- Is sigma from a forward model of the beam and spectral response, checked on mocks, not moment 2?
- Is the line fully covered and unblended, and are tracers compared at one convention and matched resolution?
- Is MCMC convergence documented, and is M_dyn quoted at a sampled radius with its estimator and geometry?
- Were residuals inspected for a second component, and is its flux treated as a lower limit?

## Source cards

Full list: `references/sources.md`. Most informative for this technique:

- 2017ApJ...850..180J: rotcur on z~4-6 [CII], ring acceptance, mock systematics.
- 2023A&A...672A.106L: staged 3DBarolo, SPACEPAR, mock-tested dispersion limits, mass models.
- 2025A&A...693A..91L: 3DBarolo on [CI], SPACEPAR by side, residual lower limits, vcdisk mass models.
- 2024ApJ...977..161V: 3DBarolo parameter file, Bezier regularisation, rotator-vs-merger criteria.
- 2022MNRAS.516.4066L: twostage mean geometry, near side from dust lanes, 3DBarolo vs KinMS V_rad.
- 2022ApJ...934..173S: CO vs Halpha curves, ADC, eDIG caveat, spectral-resolution tests.
- 2021A&A...654A..37D: beam/2.5 rings, outermost-ring masses, partial line coverage.
- 2019A&A...632A..61G: v_rad and v_vert, Bezier geometry, kinemetry benchmark.
- 2020Natur.581..269N: qubefit, M_dyn formula, 3DBarolo cross-check.
- 2020Natur.584..201R: joint lens-kinematic visibility fit, tracer dispersion caveat.
- 2025ApJ...992..211N: KinMS + AdaMet, noise rescaling.
- 2024MNRAS.528.6768H: bar-flow model, BIC and prior-width acceptance.
- 2024ApJ...968....9W: v/sigma classification, unresolved M_dyn equations.
- 2016ApJ...816...37V: unresolved M_dyn and the inclination degeneracy.
