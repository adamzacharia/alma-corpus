---
name: alma-hydro-simulation-comparison
description: "Compare ALMA continuum and line data with hydrodynamic simulations (planet-disk interaction, circumbinary and misaligned disks, disk instabilities, AGB binary winds, cloud collisions): choose a code and setup, run a model grid, post-process it into synthetic ALMA images, and judge the match. Use when a task asks for a planet mass from gaps, rings, spirals or velocity kinks, for a companion orbit that explains disk morphology, for SPH or grid models of an observed source, or for checking whether a simulated feature would survive ALMA uv coverage and noise. Built from 52 on-topic ALMA papers (2012-2026)."
---

# Comparing ALMA data to hydrodynamic simulations

A hydro comparison runs a physical simulation (gas, often plus dust and sink particles), turns a snapshot into
synthetic ALMA images, and asks which setup reproduces the data. The result is usually a planet mass, a
companion orbit or a mechanism. Two mistakes matter most: (1) presenting a by-eye match from a handful of runs
as a measurement, when the authors themselves say the degeneracy between planet mass, viscosity, aspect ratio
and dust properties was not quantified (2019A&A...622A..75L, 2018MNRAS.475.5296D, 2018ApJ...857...87L); and
(2) comparing a simulation that is locally isothermal with a radiative transfer step that uses a different
temperature, which biases kinematic amplitudes (2023PASJ...75.1105K, 2019A&A...625A.118K, 2025ApJ...984L..15P).

Evidence base: the `hydro-simulation-comparison` pack (53 regex-tagged papers). I drop 2018MNRAS.474.5105B
(a SPHERE/ZIMPOL paper whose only pack entry is "data not flux calibrated"), leaving 52. Counts marked "pack"
are the pack's software aggregate (per matched analysis step, all 53 papers). Counts marked "pack lines" are my
own count of the pack's excerpt, key-parameter and assumption lines. Several papers do not run a simulation but
apply a scaling relation derived from earlier ones (2017ApJ...851L..23C, 2019ApJ...880...69Y,
2024ApJ...976..132H); those are covered here only as the quick route. 2016PASJ...68...43K does both: it runs
its own 2D FARGO grid over Mp, h/R and alpha to calibrate a gap-width formula, then applies the formula to the
HL Tau gaps.

Related skills: post-processing a density field into images is `alma-radiative-transfer-modelling`; measuring
the radial profile, gap width and depth you will compare against is `alma-disk-substructure-profiles`;
Keplerian masks, rotation curves and velocity residual extraction are `alma-keplerian-disk-kinematics`.

## When to use

- Infer planet mass and location from dust gaps and rings by running planet-disk models
  (2019A&A...622A..75L, 2018MNRAS.475.5296D, 2019AJ....158...15P, 2020ApJ...888L...4T, 2018ApJ...866L...6C).
- Explain localized velocity kinks or deviations in CO channel maps with an embedded planet
  (2019NatAs...3.1109P, 2025ApJ...984L..15P, 2023MNRAS.526L..41P, 2023PASJ...75.1105K).
- Constrain a stellar companion's orbit from spirals, cavities or disk misalignment in binaries and triples
  (2020MNRAS.499.3837G, 2020MNRAS.499.3857N, 2024A&A...688A.102T, 2020ApJ...895L..18B, 2024MNRAS.534.2904C).
- Test a mechanism: gravitational instability vs companions for spirals (2017ApJ...839L..24M), VSI/MRI/GI
  turbulence signatures (2025ApJ...984L..21B), gas gaps and turbulence levels (2018ApJ...857...87L,
  2019ApJ...871..107F).
- Protostellar circumbinary disks with infall (2014ApJ...796....1T, 2020ApJ...898...10T).
- AGB binary or triple wind morphology (2012Natur.490..232M, 2020A&A...633A..13D, 2024A&A...691A..57M) and
  galactic cloud-cloud collisions (2020MNRAS.494.2131F).
- Building a model grid that maps observables to planet mass for a survey (2018ApJ...869L..47Z,
  2015ApJ...809...93D, 2026ApJ..1003..215F, 2016PASJ...68...43K).

## When not to use

| Situation | Use instead |
|---|---|
| Static parametric disk/envelope model fitted to data, no dynamics | `alma-radiative-transfer-modelling` |
| Only need gap location, width, depth or ring contrast | `alma-disk-substructure-profiles` |
| Planet mass from a published gap-width or gap-depth scaling, no new run | the quick route in Step 1 below, profile measurement in `alma-disk-substructure-profiles` |
| Rotation curves, dynamical stellar mass, Keplerian residual maps | `alma-keplerian-disk-kinematics` |
| Galaxy-scale gas dynamics around SMBHs, tilted rings | `alma-smbh-gas-dynamics`, `alma-galaxy-3d-kinematics` |
| Cloud virial analysis without simulations | `alma-gmc-decomposition-virial` |

## Steps

1. **Decide whether a simulation is needed.** Goal: avoid running hydro for something a scaling relation
   answers. Quick routes (no new run), each with its own inputs and conditions:

   | Route | Inputs the papers state | Conditions stated |
   |---|---|---|
   | Gap width = k R_Hill, r_Hill = a (m_p/3M*)^(1/3), k = 4-8 (2017ApJ...851L..23C, 2025ApJ...986L..11S); k = 5 (2016A&A...586A..99H) | measured gap width, orbital radius, M*, k | gaps fully evacuated, M* 1.0 Msun (2017ApJ...851L..23C); alpha < 0.01, one planet per gap (2025ApJ...986L..11S) |
   | Gap radius = 4 R_Hill (2018ApJ...869...17L) | gap radius (not full width), orbital radius, M* | the paper measures gap width as full width at half depth elsewhere; keep its "gap radius" convention |
   | Kanagawa gap-width formula (2016PASJ...68...43K) | width with edges where tau crosses tau_unp/2, Rp = (Rin+Rout)/2, alpha, dust opacity index beta, M* | alpha 1e-3, beta 1.5, M* 1 Msun, gas and dust gap widths similar (weak filtration) |
   | Kanagawa gap depth (2019ApJ...880...69Y) | gap depth (4-8), M* 2.1 Msun, T 60 K, alpha 1e-3 | vertically isothermal disk |
   | Zhang et al. 2018 relations (2024ApJ...976..132H) | kappa_abs 0.43 cm^2/g, amax 0.1 mm, n(a) ~ a^-3.5, alpha 1e-3 | one planet per gap, DSHARP dust; temperature uncertainty dominates |
   | Chaotic / crossing zone (2015ApJ...798..124R) | gap width and location in a debris disk | gas-poor debris regime; no alpha or h/r; data could not separate a gap from a double power law |

   Do not mix width conventions: a gap radius read as a full width (or the reverse) is a factor of 2 in
   size and, since m_p scales as the cube of the Hill radius, a factor of 8 in mass (general relation). Each
   route inherits the assumptions of the simulations it was calibrated on. Run a simulation when the claim is
   morphological (spirals, kinks, misalignment, vortices) or when several gaps, migration or gas and dust must
   be matched together.
2. **Pick the code by physics.** Goal: a code that represents the features you will compare.
   - 3D SPH with sink particles for planets, binaries, misalignment and wind injection: PHANTOM
     (2019NatAs...3.1109P, 2019A&A...622A..75L, 2024A&A...688A.102T, 2024A&A...691A..57M); one-fluid
     dust or multigrain dust (11 bins in 2019NatAs...3.1109P, 2023MNRAS.526L..41P).
   - 2D grid two-fluid or Lagrangian dust for gap and ring profiles and survey grids: FARGO, Dusty FARGO-ADSG,
     FARGO3D, LA-COMPASS, PEnGUIn (2015ApJ...809...93D, 2018ApJ...869L..47Z, 2026ApJ..1003..215F,
     2018ApJ...857...87L, 2019ApJ...879L...2M).
   - 3D grid for vertical kinematics or inclined planets: Athena++ (2023PASJ...75.1105K), FARGO3D 3D
     (2019A&A...625A.118K), PLUTO (2021A&A...654A..35B).
   - AMR for protostellar binaries with infall: SFUMATO (2014ApJ...796....1T, 2020ApJ...898...10T); galaxy
     scale: ENZO (2020MNRAS.494.2131F). AGB winds: GADGET-2 variants (2012Natur.490..232M,
     2020A&A...633A..13D).
3. **Set up the disk from the data.** Goal: initial conditions tied to the source, not defaults. Fix stellar
   mass, distance, disk extent and inclination/PA from observations (2019NatAs...3.1109P uses 2.4 Msun and
   185 pc; 2024MNRAS.534.2904C rescales a model to 1.8 Msun, i = 27 deg, PA = -20 deg). Choose Sigma(R) slope
   (p = 1 in 2024MNRAS.534.2904C, 2020MNRAS.499.3837G, 2016ApJ...819..134B), aspect ratio, viscosity, disk
   mass, dust-to-gas ratio and grain size (table below). Planets: fixed circular orbits (2015ApJ...809...93D,
   2026ApJ..1003..215F) or free to migrate and accrete (2018MNRAS.475.5296D, 2020ApJ...888L...4T,
   2019ApJ...879L...2M). For multiple-star systems check orbital stability first (Mardling and Aarseth
   criterion plus REBOUND over 1000 outer periods, 2024A&A...691A..57M).
4. **Run long enough and pick the snapshot deliberately.** Goal: a quasi-steady or source-age-appropriate
   state. Run lengths range from about 20 orbits (2025ApJ...984L..15P, 2014ApJ...796....1T) and 100 orbits
   (2023MNRAS.526L..41P, 2016ApJ...819..134B) to 1000 orbits (2018ApJ...869L..47Z, 2019A&A...625A.118K,
   2018ApJ...857...87L, 2019ApJ...871..107F) and beyond (1500 in 2026ApJ..1003..215F; up to 3000 in
   2024A&A...688A.102T). State which snapshot was compared and why; 2026ApJ..1003..215F checked ring steady
   state over the last 600 orbits, while 2018MNRAS.475.5296D chose the snapshot by eye.
5. **Post-process into observables.** Goal: same quantity, units and resolution as the data. Compute
   temperatures and images with MCFOST (Voronoi cells on SPH particles, Tgas = Tdust, LTE CO;
   2019NatAs...3.1109P, 2025ApJ...984L..15P) or RADMC-3D (2017ApJ...839L..24M, 2019A&A...625A.118K,
   2025ApJ...984L..21B, via fargo2radmc3d in the last); LIME for AGB envelopes (2012Natur.490..232M,
   2020A&A...633A..13D). The RT setup itself (opacities, abundances, freeze-out) belongs to
   `alma-radiative-transfer-modelling`; keep it consistent with the hydro temperature.
6. **Make synthetic ALMA data.** Goal: compare like with like. Best practice in the pack: CASA simobserve with
   the same antenna configuration, then the same imaging (2020ApJ...898...10T, 2019A&A...625A.118K,
   2021A&A...654A..35B); CASA ft plus CLEAN (2018ApJ...866L...6C); simdata (2012Natur.490..232M). At minimum,
   compute channels finer than the data, bin to the observed channel width, Hanning smooth if the data are,
   and convolve with the CLEAN beam (2019NatAs...3.1109P). 2024A&A...691A..57M admits no ALMA simulator was
   applied. 2017ApJ...839L..24M did run simobserve and clean, but with a generic configuration (alma.out13,
   card) and admits the uv coverage differs from the data; match the real configuration, not just "an" array.
7. **Compare and choose.** Goal: a defensible best model and bracket. Typical comparisons: azimuthally
   averaged radial profiles (2018MNRAS.475.5296D, 2019A&A...622A..75L), ring locations and fluxes
   (2019AJ....158...15P), inner-edge radius at 10% of peak surface density against the observed range
   (2020MNRAS.499.3857N), rotation-curve deviation delta v_rot (2019A&A...625A.118K), kink shape and amplitude
   in channel maps (2019NatAs...3.1109P, 2025ApJ...984L..15P), velocity residuals (2024MNRAS.534.2904C),
   flattening ratio of AGB arcs (2024A&A...691A..57M). Visual or qualitative comparison is frequent in the
   excerpted sample (my count of pack lines: 17 of the 40 excerpts); that sample cannot give the share across
   all 52 papers. Report the range of models that are acceptable and the ones ruled out, for example moment-2
   line broadening ruling out the upper planet masses (2019NatAs...3.1109P). Geometry-dependent cases:
   - Velocity residuals and Doppler flips depend on the Keplerian background subtracted (2024MNRAS.534.2904C).
     Document the background model and test plausible alternatives before reading a residual as a companion.
   - Kink classification is subjective and inclination-biased (2025ApJ...984L..15P). Do not compare
     detection rates or class frequencies across disks at different inclinations, or treat a non-detection
     at an unfavorable inclination as absence.
   - Dust alone cannot fix mutual inclinations between disk rings and orbits, because the orbital direction is
     unknown (2020ApJ...895L..18B). Use gas kinematics or orbital-direction constraints before claiming a
     unique misalignment angle.
8. **Rescale and report.** Scale-free runs are rescaled by stellar mass (2018ApJ...869...17L,
   2019ApJ...880...69Y) or length (2024MNRAS.534.2904C). Report code, resolution, alpha, h/r, EOS, dust
   treatment, run length, snapshot, RT inputs and synthetic-observation settings. The pack's "not stated"
   list names these gaps, so report each explicitly:
   - spectral reference: rest frequency and systemic velocity adopted; channel width and binning of the
     synthetic cube (2025ApJ...984L..21B leaves the synthetic channel width and noise seed unstated);
   - geometry: disk inclination and PA used in the models, emission-surface parameters, planet-wake
     projection;
   - extraction: how kink location and amplitude were measured, eddy initial values, bettermoments clipping and
     masks;
   - imaging: robust, taper, cell, image size, CLEAN mask and threshold, applied identically to data and model;
   - noise: simobserve weather (PWV), integration time, noise realization, beam and rms of the shown cubes;
   - RT: MCFOST photon number and grid, abundance denominator, depletion factors.

## Parameter defaults and ranges

Counts are distinct bibcodes, from my count of pack lines (excerpts, key parameters, assumptions; a paper
repeated across those lines counts once) unless marked otherwise. "Common choice" is the most frequent value
reported, not a recommended default; set your own from the source.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Equation of state | locally or vertically isothermal | isothermal; flux-limited diffusion; polytropic gamma 1.2 with H I cooling; ENZO cooling/heating | 16 isothermal | 2019NatAs...3.1109P, 2024A&A...688A.102T, 2017ApJ...839L..24M, 2024A&A...691A..57M |
| Viscosity alpha (grid codes and scaling relations) | 1e-3 | 0 to 0.014 | 1e-3 in 10 | 1e-3 in: 2015ApJ...809...93D, 2016PASJ...68...43K, 2016ApJ...829L..35T, 2018ApJ...869L..47Z (preferred of 1e-4/1e-3/1e-2), 2018A&A...619A.161C, 2019A&A...625A.118K, 2019ApJ...879L...2M, 2019ApJ...880...69Y, 2023PASJ...75.1105K, 2024ApJ...976..132H; other values: 2019ApJ...871..107F (0), 2019AJ....158...15P (1e-5), 2018ApJ...866L...6C (0.014) |
| SPH alpha_AV (gives alpha_SS) | 0.1-0.2 | 0.1-0.31; alpha_SPH 0.1-1.0 | 5 | 2018MNRAS.475.5296D (0.1 to 0.003), 2019A&A...622A..75L (0.15 to 5e-3), 2025ApJ...984L..15P (0.2), 2020ApJ...895L..18B (0.31), 2017ApJ...839L..24M |
| alpha_SS in SPH disks | 5e-3 | ~1e-3 to 5e-3 | 8 (5e-3 in 6) | 5e-3: 2020ApJ...888L...4T, 2020MNRAS.499.3837G, 2024A&A...688A.102T, 2020MNRAS.499.3857N, 2019A&A...624A..33V, 2019A&A...622A..75L (~5e-3); 2018MNRAS.475.5296D (~3e-3); 2019NatAs...3.1109P (~1e-3) |
| Aspect ratio h/r | 0.05 | 0.033-0.14 | 0.05 in 7 | 2020ApJ...895L..18B, 2018ApJ...869L..47Z (0.05, 0.07, 0.1), 2019AJ....158...15P (0.033), 2017ApJ...846...70P (0.14) |
| SPH particles (initial) | 1e6 | 2.5e5 to 5e6 initial; 1.3e7 after splitting | 1e6 in 6 | 1e6: 2020ApJ...888L...4T, 2023MNRAS.526L..41P, 2024A&A...688A.102T, 2020ApJ...895L..18B, 2018MNRAS.475.5296D, 2025ApJ...984L..15P (then each particle split into 13 for the last 2 orbits); 2017ApJ...839L..24M (2.5e5), 2019NatAs...3.1109P (2e6), 2024MNRAS.534.2904C (5e6) |
| 2D grid (r x phi) | ~1000 x 1000-2000 | 256x256 to 1766x4096 | 9 | 2015ApJ...809...93D, 2016PASJ...68...43K (1024x2048), 2019ApJ...879L...2M (20 cells per H), 2019ApJ...871..107F |
| Disk gas mass | 3e-3 to 1e-2 Msun | 3e-3 to 0.12 Msun | 9 | 2019NatAs...3.1109P, 2025ApJ...984L..15P (5e-3), 2019A&A...625A.118K (3e-3), 2024A&A...688A.102T (0.12) |
| Dust-to-gas ratio | 0.01 | 0.009-0.2 | 0.01 in 9 | 2018ApJ...869L..47Z, 2026ApJ..1003..215F, 2018MNRAS.475.5296D (0.1), 2019A&A...622A..75L (0.01-0.2) |
| Dust grain size | 1 mm single size | 0.15 mm; 11 bins 1 um-1.6 mm; Stokes 0.002-0.2 | 1 mm in 6 | 2020ApJ...888L...4T, 2018ApJ...857...87L, 2019NatAs...3.1109P, 2026ApJ..1003..215F |
| Run length | 1000 orbits (grid) | 20 to 3000 orbits; 1e4-1e5 orbits for gap-width fits | 1000 in 4 | 2018ApJ...869L..47Z, 2025ApJ...984L..15P (20), 2024A&A...688A.102T, 2016PASJ...68...43K |
| Planet accretion radius | no shared default | 0.125 Hill radius (one paper) | 1 | 2025ApJ...984L..15P |
| Stellar accretion / sink radius | no shared default | 1 au tested with no significant change; 3.4 AU sink in AMR | 2 | 2020ApJ...888L...4T, 2014ApJ...796....1T |
| Schmidt number | Sc = 1 | - | 2 | 2015ApJ...809...93D, 2018ApJ...869L..47Z |
| CO abundance (RT) | 12CO 1e-4, but the denominator differs | 12CO/H2 1e-4; 12CO 1e-4 relative to H (= 2e-4 per H2 in fully molecular gas, general conversion; check the denominator your RT code expects); 13CO 7e-7 and X(C18O) 5.1e-7 (denominator not given in the pack) | 5 | per H2: 2019A&A...625A.118K, 2025ApJ...984L..21B; per H: 2025ApJ...984L..15P; 2019NatAs...3.1109P (13CO), 2020ApJ...898...10T (C18O) |
| CO freeze-out | deplete below 20-21 K | factor 1e-5 or free | 2 | 2025ApJ...984L..21B, 2025ApJ...984L..15P |
| Microturbulence (RT) | 0 | 0-50 m/s | 4 | 2023MNRAS.526L..41P, 2019A&A...625A.118K (30 m/s), 2019NatAs...3.1109P (50 m/s) |
| Synthetic channel width | finer than data, then binned | 26-50 m/s | 2 | 2019NatAs...3.1109P, 2025ApJ...984L..21B |

Longer setups per paper (stellar mass, disk extent, temperature laws, binary parameters) are in
`references/parameters.md`.

## Software

Pack aggregate counts (per matched analysis step, all 53 papers):

| Purpose | Software (pack count) | Notes |
|---|---|---|
| 3D SPH gas+dust, sinks | PHANTOM (15), generic "sph code" (1), GADGET-2 (2 as gadget-2/gadget2) | PHANTOM dominates disk and AGB work |
| 2D/3D grid planet-disk | FARGO (4), FARGO3D (4) + FARGO-3D (2), Dusty FARGO-ADSG (2), FARGO-ADSG (1), FARGO2D (1), Athena++ (1), PLUTO (1), LA-COMPASS (1), PEnGUIn (1) | FARGO family is the default for 2D gap grids |
| AMR / galaxy | SFUMATO (2), ENZO (1) | protostellar binaries; barred galaxy clouds |
| N-body stability | REBOUND (2) | triple-star orbits (2024A&A...691A..57M) |
| RT post-processing | MCFOST (6) + pymcfost (1), RADMC-3D (5) + radmc3d (1), LIME (2), fargo2radmc3d (1), HOCHUNK3D (1), optool (1), Synthesizer (1) | MCFOST pairs with PHANTOM; RADMC-3D with grid codes |
| Synthetic observations | CASA (3), simobserve (2), simdata (1), simanalyze (1) | simulator use is rarer than RT use |
| Kinematics extraction | eddy (1), bettermoments (1) | on observed and synthetic cubes alike (2024MNRAS.534.2904C) |
| Visualization | SPLASH (1) | SPH rendering |

The phantom+mcfost pipeline was benchmarked in the exoALMA papers (2025ApJ...984L..15P).

## Pitfalls

- **Isothermal hydro vs RT temperature.** Locally isothermal hydro with a different RT temperature is
  inconsistent (2023PASJ...75.1105K, 2014ApJ...796....1T); the vertically isothermal assumption is called a
  major limitation (2025ApJ...984L..15P) and may underestimate delta v_rot (2019A&A...625A.118K). A
  radiative-equilibrium rerun changed velocities by only ~0.1 and 0.05 km/s in one case (2019NatAs...3.1109P);
  run that test rather than assume it.
- **By-eye fits hide degeneracy.** Planet mass, alpha, h/r, dust-to-gas and grain size trade off; several
  papers say they cannot quantify it (2019A&A...622A..75L, 2018MNRAS.475.5296D, 2018ApJ...857...87L,
  2020A&A...633A..13D). 2020MNRAS.499.3837G tested only seven candidate orbital configurations of the
  companion (not seven orbits of run time) and calls the comparison subjective.
- **Different tracers give different masses.** In PDS 70 the continuum gap matched 5 MJup but the kinematic
  depth matched 10 MJup (2019A&A...625A.118K). Report both, not the convenient one.
- **Snapshot and run length.** Gap profiles fitted at a fixed 1000 orbits (2018ApJ...869L..47Z); single
  snapshots with particular parameters (2025ApJ...984L..21B). Features evolve; a match at one time is not a
  unique solution.
- **Numerical artefacts.** Inner boundaries can make a central 12CO peak much stronger than observed
  (2019ApJ...879L...2M) or produce tails (2023PASJ...75.1105K). Instant accretion at the sink radius may
  overestimate planet accretion (2020ApJ...888L...4T).
- **Missing physics.** No dust feedback (2018ApJ...869L..47Z, 2015ApJ...809...93D); no growth, fragmentation
  or back-reaction (2019AJ....158...15P); 2D only (2016ApJ...819..134B); no magnetic field
  (2020ApJ...898...10T); MRI models without the Hall effect or ambipolar diffusion, and no embedded planets
  (2025ApJ...984L..21B); migration and inclination damping ignored
  (2023PASJ...75.1105K); no stellar pulsations in AGB winds (2024A&A...691A..57M).
- **No uv-plane simulation, or the wrong one.** 2024A&A...691A..57M admits no ALMA simulator was applied;
  2017ApJ...839L..24M simulated with a uv coverage different from the data and aims only at morphological
  similarity. On the observed side, eddy ignores beam
  convolution (2025ApJ...986L..11S) and beam smearing complicates rotation curves (2019A&A...625A.118K).
- **Gaps may not be planets.** Planet-based occurrence rates are upper limits (2018ApJ...869L..47Z); MHD and
  instabilities remain possible (2017ApJ...851L..23C); several simulations could not reproduce all features
  (2021A&A...654A..35B, 2018ApJ...869...17L, 2024A&A...688A.102T).
- **Scaling-relation inputs dominate.** Gap-width masses depend on beta and dust filtration
  (2016PASJ...68...43K); temperature uncertainty dominates trap and mass estimates (2024ApJ...976..132H);
  partially resolved gaps make width and depth degenerate (2017ApJ...851L..23C).
- **Geometry and background dependence.** Residuals and Doppler flips are model dependent through the assumed
  Keplerian background (2024MNRAS.534.2904C); kink classification is inclination-biased
  (2025ApJ...984L..15P); mutual inclinations cannot be fixed from dust alone (2020ApJ...895L..18B).
- **Contaminated channels.** Cloud absorption can hide the channels where a kink is expected, so no kinematic
  mass is possible (2023MNRAS.526L..41P).
- **What cards flag as not stated.** MCFOST photon and grid settings, the quantitative criterion for the
  best planet mass, disk i and PA adopted in models, simobserve weather and noise inputs, snapshot choice, and
  code availability (pack "not stated" list; 2019NatAs...3.1109P, 2025ApJ...984L..15P, 2020ApJ...898...10T).

## Verification checks

What papers did:
- Run the synthetic data through the ALMA simulator and confirm the feature survives uv sampling and noise
  (2019NatAs...3.1109P).
- Numerical convergence: double resolution (2016ApJ...819..134B), +-50% resolution moving the planet position
  less than 8% (2019ApJ...879L...2M), smoothing length (2016PASJ...68...43K), solver and CFL changes
  (2023PASJ...75.1105K), accretion radius (2020ApJ...888L...4T), temperature 13.5 vs 25 K
  (2014ApJ...796....1T).
- Steady state of rings over the final orbits (2026ApJ..1003..215F); orbit stability for multiples
  (2024A&A...691A..57M).
- Benchmark against earlier simulations in the overlapping parameter space (2024A&A...688A.102T,
  2025ApJ...984L..15P).
- Independent observables: moment-2 broadening and a SPHERE non-detection to rule out high masses
  (2019NatAs...3.1109P); gap-depth vs gap-width masses (2016PASJ...68...43K); disk mass, kinematics,
  asymmetry and depth consistency (2018ApJ...869L..47Z); accretion rate and spectral index
  (2018ApJ...866L...6C); dust settling H_d/H_g against the RT value (2019A&A...622A..75L); final disk
  orientation (2020MNRAS.499.3837G); comparison with DSHARP planet masses (2024ApJ...976..132H).

What a careful referee adds:
- A stated goodness-of-fit metric on the compared quantity (profile residuals, kink amplitude) instead of
  "by eye", and the bracketing models that fail.
- The radiative-equilibrium or vertically stratified temperature test whenever kinematic amplitudes are
  quoted.
- Identical imaging (weighting, channel width, beam) for data and model; run the same extraction tools on
  both.
- At least two independent observables (continuum and gas, or gap and kink) before claiming a planet mass.
- For residual-based claims, the same residual signature under at least one alternative background model
  (different emission surface or rotation curve).

## Source cards

Full list: `references/sources.md`. Most informative for this technique:

- 2019NatAs...3.1109P: phantom+mcfost kink detection; simulator test, channel binning, moment-2 check.
- 2025ApJ...984L..15P: exoALMA channel-map kinks; phantom setup, CO depletion, benchmarked pipeline.
- 2019A&A...625A.118K: FARGO3D + RADMC3D + simobserve for PDS 70; continuum vs kinematic masses.
- 2018ApJ...869L..47Z: DSHARP Dusty FARGO-ADSG grid; gap width to planet mass relations.
- 2019A&A...622A..75L: PHANTOM dust gap fit; by-eye admitted; settling check.
- 2018MNRAS.475.5296D: Elias 24 migrating, accreting planet; radial profile comparison.
- 2018ApJ...857...87L: LA-COMPASS, >100 runs, radially varying alpha.
- 2019ApJ...879L...2M: PEnGUIn PDS 70; resolution tests, inner boundary artefact.
- 2023PASJ...75.1105K: Athena++ inclined planet; numerical checks, temperature inconsistency.
- 2016PASJ...68...43K: own FARGO grid calibrates a gap-width mass formula, then applied to HL Tau.
- 2026ApJ..1003..215F: FARGO3D ring properties vs pebble isolation mass.
- 2024MNRAS.534.2904C: circumbinary velocity residuals; rescaling to HD 142527.
- 2020MNRAS.499.3837G: HD 100453 binary orbit; seven candidate orbits; rewind runs.
- 2024A&A...688A.102T: GG Tau A coplanar vs misaligned; benchmarking.
- 2020ApJ...898...10T: SFUMATO L1551 IRS 5 with simobserve and LTE RT.
- 2025ApJ...984L..21B: VSI/MRI/GI turbulence signatures; RADMC-3D setup.
- 2018ApJ...866L...6C: CI Tau FARGO3D with dust; CASA ft plus CLEAN.
- 2019AJ....158...15P: mini-Neptune in a ring; Dusty FARGO-ADSG with Lagrangian dust.
- 2024A&A...691A..57M: AGB triple winds; REBOUND stability; no simulator admitted.
- 2017ApJ...839L..24M: Elias 2-27 spirals, SPH with flux-limited diffusion, RADMC-3D.
