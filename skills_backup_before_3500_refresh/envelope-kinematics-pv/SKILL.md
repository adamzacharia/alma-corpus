---
name: alma-envelope-kinematics-pv
description: "Measure infall and rotation in protostellar envelopes from ALMA line cubes with position-velocity (PV) diagrams: rotation-profile power laws and break (Keplerian) radii, infalling-rotating envelope (centrifugal barrier, Ulrich) models, streamer trajectories, redshifted-absorption infall, specific angular momentum, protostellar mass and mass infall rate. Use when a cube shows a velocity gradient across a Class 0/I source or a massive hot core and you must decide whether it is infall, rotation or both, or when you check someone else's PV analysis. Built from a 213-paper ALMA evidence pack (2012-2026); 124 of those papers carry the star-formation field tag (pack aggregate)."
---

# Envelope kinematics from PV diagrams (infall, rotation, centrifugal barrier)

Papers cut PV diagrams along the disk/envelope major axis (perpendicular to the outflow) and along the minor axis.
Under a thin, axisymmetric, flattened geometry with known near side, rotation shows up mainly along the major
axis and infall adds a velocity gradient along the minor axis. That reading is not unique: expansion, projection,
warps and foreground absorption can mimic it (2013A&A...560A.103M could not separate infall plus Keplerian from
pure Keplerian; a warped disk explained L1489 IRS in 2020ApJ...893...51S). Papers then (a) fit a power law to a
rotation profile V(R), (b) compare forward models of an infalling-rotating envelope plus disk with the PV
diagrams, or (c) look for redshifted absorption against the continuum. The mistakes that matter most: (1)
trusting low-velocity and large-radius PV points, where interferometric filtering and self-absorption distort
the profile (2014ApJ...796..131O kept only R<100 AU because about 50% of ~1000 AU-scale emission was missed), and
(2) quoting masses, break radii and infall speeds without saying how inclination (and its convention),
systemic velocity and resolution bias were handled (the mean-position method "may systematically underestimate"
the break radius at limited resolution, 2015ApJ...812...27A).

> Always report: line and an optical-depth check, PV cut PA and width, systemic velocity and whether it was fit,
> inclination with its source and convention (i = 90 deg edge-on or i = 0 edge-on), distance, emission threshold
> for data points, velocity ranges excluded, flux-scale uncertainty, and how models were spatially filtered. The
> cards flag PV cut widths and extraction details as not stated in several envelope papers (2014ApJ...796..131O,
> 2017ApJ...834..178Y, 2020A&A...634L..12D).

**Scope of the evidence.** The regex tagger pulled 213 papers; the science-field aggregate lists star formation
124, protoplanetary disks 47, nearby galaxies 37, AGN 29, evolved stars 21 (pack aggregates; papers carry several
fields). Many hits are outflow, galaxy or AGB-star PV work. Only 40 papers have full excerpts in the pack; for the
rest the pack gives one-line parameters, assumptions and limitations. This skill cites the protostellar envelope,
core and streamer papers for the recipe and the others only for generic PV practice. It does not claim which
workflow most envelope papers follow: the pack has no envelope-only denominator.

## When to use

- A Class 0/I protostar shows a velocity gradient in C18O, 13CO, CS, SO, CH3OH or HCO+ and you need the
  transition from infall to Keplerian rotation (2014ApJ...796..131O, 2015ApJ...812...27A, 2017ApJ...849...56A,
  2017ApJ...834..178Y, 2018ApJ...864L..25O).
- You want the centrifugal barrier radius and protostellar mass from an infalling-rotating envelope model
  (2015ApJ...812...59O, 2016ApJ...824...88O, 2017ApJ...837..174O, 2019ApJ...873...73Z, 2024ApJ...970...28O).
- Pseudodisk or flattened envelope with infall plus angular-momentum-conserving rotation (2014ApJ...786..114L,
  2017ApJ...843...27L, 2019ApJ...879..101L, 2019ApJ...871..100H).
- Streamers feeding a disk: trajectory fits, infall time, mass infall rate (2024A&A...683A.133G,
  2025SciA...11.4512O, 2019A&A...623A..96Y).
- Infall from redshifted (inverse P-Cygni) absorption against compact continuum (2015ApJ...814...22E,
  2012A&A...544L...7P, 2013ApJ...764L..14Z, 2018A&A...615A.141B, 2018ApJ...869..158F).
- Massive hot cores and disks with rotation plus infall (2025A&A...693A..76C, 2017A&A...603A..10B,
  2015ApJ...813L..19J, 2019ApJ...877L..25M, 2024ApJ...967...15K).

## When not to use

| Situation | Use instead |
|---|---|
| A settled, mostly Keplerian protoplanetary or Class II disk; you want M*, emission height, i, PA | `keplerian-disk-kinematics` skill (channel-map or cube fitting). Use this skill only for the envelope-to-disk transition |
| Rotation curves, dispersion and inflow/outflow in galaxies (3DBarolo, GalPak3D, kinemetry) | `galaxy-3d-kinematics` skill; `smbh-gas-dynamics` for black-hole masses. Galaxy PV papers in this pack (2021A&A...655A..25Z, 2020MNRAS.493.3744F, 2019A&A...623A..79C) follow that workflow |
| Outflow mass, momentum, energetics, rotating outflows or disk winds | `outflow-energetics` skill. Outflow PV papers here (2018A&A...618A.120L, 2020A&A...634L..12D) measure j in the flow, not the envelope |
| AGB or post-AGB expanding or rotating envelopes | `evolved-star-envelopes` skill (2018A&A...614A.113H, 2020ApJ...890L..14T are in this pack only by regex) |
| Cluster-scale or filament inflow without a central protostar's potential | Hub-filament velocity-gradient work (2024A&A...690A.185W uses region rest velocity as a proxy for core velocity); this skill's point-mass models do not apply |
| Single moment-1 map is all you need for PA | `moment-maps` skill |

## Steps

1. **Fix the geometry before cutting PV diagrams.**
   - Centre: continuum peak (general practice; 2021A&A...655A..25Z fixed the kinematic centre to the continuum
     position in a galaxy; 2024ApJ...963...72O took i = 51.1 deg from the continuum).
   - PA of the disk/envelope major axis: perpendicular to the jet or outflow (2015ApJ...812...59O assumes the
     outflow axis is perpendicular to the envelope mid-plane), or from the line emission itself;
     2018A&A...614A.113H made orthogonal PV pairs every 5 deg to find the PA (uncertainty ~5 deg).
   - Inclination: from continuum aspect ratio, i = arccos(minor/major) for a thin disk (2017ApJ...845...58Z,
     2018A&A...619A..39F), from an outflow model fit (2017ApJ...834..178Y grid in 5 deg steps, checked against
     ~50 deg from continuum aspect ratios), or fixed edge-on for L1527 (85 deg in 2017ApJ...849...56A, 90 deg in
     2014ApJ...796..131O).
   - **Pick one inclination convention and convert everything to it.** This skill uses i = 90 deg for edge-on
     (as 2014ApJ...796..131O and 2017ApJ...849...56A). 2019ApJ...873...73Z defines i = 0 as edge-on, so convert
     with i_here = 90 deg - i_paper. Record the original convention and which side is near (needed to tell
     infall from expansion on the minor axis).
   - Systemic velocity: fit it, then check. 2017ApJ...849...56A and 2017ApJ...834..178Y left Vsys free;
     2024A&A...690A..46S fixed it to 2.84 km/s after a first fit; 2018ApJ...864L..25O found 5.3 km/s fit better
     than 5.5 km/s.
2. **Choose lines by what they trace.** C18O and 13CO are candidate lower-opacity tracers for the rotation
   profile (2017ApJ...849...56A, 2015ApJ...812...27A, 2017ApJ...834..178Y), but isotopologue identity does not
   make a line optically thin: check opacity first (2015ApJ...812...27A lists optical depth among its mass
   uncertainties). CS, SO, CH3OH and HCOOH have been used to resolve the envelope and centrifugal barrier
   (2015ApJ...812...59O CS, 2014ApJ...796..131O SO, 2024ApJ...970...28O CH3OH and HCOOH). Tracer split by
   velocity: 2019ApJ...871..100H fit C18O at abs(V-Vlsr) < 1.6 km/s and CO above 1.6 km/s. Optically thick lines
   limit what you can infer (2014ApJ...796..131O: SO optically thick, so density and abundance unconstrained).
3. **Extract the PV diagrams.** Major and minor axis cuts through the centre are the standard pair
   (2015ApJ...812...27A compared models with both). Cut width: one beam (2018ApJ...863...19A) or a few tenths of
   an arcsec (0.2 arcsec in 2019A&A...621A..83S, 0.5 arcsec in 2018A&A...619A..39F). Tools named in the pack
   aggregates: CASA `impv`, `pvextractor`, GILDAS (2018ApJ...863..193V used PVExtractor along a curved
   filament path).
4. **Measure the rotation profile V(R)** (the "ridge" approach).
   - Per channel, take the intensity-weighted mean position of pixels above a clip level (5 sigma in
     2017ApJ...849...56A, 6 sigma in 2015ApJ...812...27A) or a Gaussian-fit peak (2020ApJ...893...51S fit
     positions per channel for the inner part and velocities per position for the outer part).
   - Drop low velocities where filtering and envelope confusion dominate: no mean positions at abs(dV) < 1.2 km/s
     in 2015ApJ...812...27A; low-velocity channels excluded, range not given in the pack, in 2017ApJ...834..178Y.
   - Fit V = V_b (R/R_b)^-p in log R - log V, single and double power law, chi2 (2017ApJ...849...56A,
     2015ApJ...812...27A, 2020ApJ...893...51S) or least squares (2014ApJ...796..131O). p = 0.5 means Keplerian;
     p = 1 means conserved specific angular momentum (general practice).
   - Errors: Monte Carlo resampling within error bars (2015ApJ...812...27A; 1000 repeats in
     2017ApJ...834..178Y; 10000 resamplings in 2020ApJ...893...51S).
   - Alternative: ridge and edge methods (the SLAM package implements both; SLAM is named twice in the pack's
     software aggregate, and the excerpts do not say which papers). 2025ApJ...993..120H applied ridge and edge
     with 5 sigma (12CO, C18O) and 6 sigma (13CO) thresholds, fixed p = 0.5 for the 12CO mass and took the mean of
     the ridge and edge masses.
   - Correct the apparent break radius for resolution: 67 AU apparent became ~90 AU in 2015ApJ...812...27A;
     56 AU became ~74 AU in 2017ApJ...849...56A.
5. **Convert to mass and angular momentum** (general practice; assumptions in brackets).
   - Keplerian: M* = R V_rot^2 / G with V_rot = V_obs / sin i [i = 90 deg edge-on convention; point mass, disk
     mass neglected as in 2019ApJ...873...73Z]. M* scales as 1/sin^2 i in this convention.
   - Centrifugal barrier of a ballistic infalling-rotating envelope (general practice): M = r_CB v_CB^2 / (2G)
     [zero-energy (parabolic) orbit with conserved j; v_CB is the deprojected rotation speed at the radius where
     the radial velocity vanishes]. It does not hold for infall slower than free fall or for finite-energy
     streamers. With conserved j the centrifugal (circularization) radius is r_c = l^2/(GM) and the barrier is
     r_0 = l^2/(2GM) (2017ApJ...843...27L).
   - Specific angular momentum: for flattened rotation, the axial component is j_z = R V_phi with R the
     cylindrical radius and V_phi the deprojected azimuthal speed. For a streamer on an arbitrary trajectory use
     the full vector j = r x v (TIPSY computes r0 x v0, 2024A&A...683A.133G). Example values: j = 6.1e-4 km/s pc
     in 2014ApJ...796..131O (about 126 au km/s; 1 pc = 206265 au); 791 +/- 218 au km/s for the S CrA streamer in
     2024A&A...683A.133G.
6. **Forward-model the envelope plus disk and compare with PV diagrams.** Papers do this in addition to, or
   instead of, step 4.
   - Ballistic infalling-rotating envelope (IRE, "CB model"): M, r_CB, i free in 2017ApJ...837..174O; density
     r^-1.5 (2015ApJ...812...59O, 2016ApJ...824...88O, 2017ApJ...837..174O, 2019ApJ...873...73Z); thin envelope
     (thickness 30 au in 2017ApJ...837..174O; height 20 au in 2024ApJ...970...28O; h = 0.2 r in
     2019ApJ...873...73Z); beam convolution and a fixed intrinsic line width (0.5 km/s in 2015ApJ...812...59O).
     2024ApJ...970...28O explored i 70-90 deg, M* 0.02-0.08 Msun, r_CB 2-9 au. FERIA implements IRE/Keplerian
     models (named twice in the software aggregate; the excerpts do not say which papers).
   - Infall slower than free fall, V_r = alpha V_ff: best model alpha = 0.3 in 2015ApJ...812...27A. In
     2017ApJ...849...56A alpha ~0.3 is inferred, not fit: it is what the isothermal shock condition needs to
     explain the density jump. 2025A&A...693A..76C fit an "infall ratio" A = 0.42 in a toy Keplerian plus infall
     model; the pack does not define its normalization, so do not equate it with alpha.
   - Free-fall plus conserved j, LTE line images, chi2 to PV with n0, T0, M*, j free and q fixed at -0.4
     (2017ApJ...834..178Y). 2019ApJ...871..100H fit a rotating infalling envelope with rho0, p, theta_flared,
     V_rot,0, V_infall,0 and F_C18O free.
   - Ulrich (rotating collapse) streamlines: centrifugal radius and initial polar angle as parameters
     (Rd = 700 au, theta0 = 70 deg, M = 1.1 Msun in 2020A&A...634L..12D; particle model with M* = 1.8 Msun,
     centrifugal radius 100 au and density r^-1.5 in 2019A&A...623A..96Y).
   - Full radiative transfer when temperature and abundance structure matter: RADMC-3D (2020ApJ...893...51S),
     LIME (2018A&A...614A.113H, an AGB disk). Hyperion and MOLLIE appear in the software aggregate without
     paper-level detail.
   - Run models through `simobserve` or the CASA simulator so they suffer the same spatial filtering
     (2015ApJ...812...27A, 2020ApJ...893...51S, 2014ApJ...796..131O).
   - Before calling a gradient infall, run the competing models: rotation only, rotation plus infall,
     expansion, and a warp. Papers that did parts of this: Keplerian-only vs infall in 2013A&A...560A.103M,
     warped vs coplanar disk in 2020ApJ...893...51S, spherical vs flattened envelope in 2015ApJ...812...27A.
7. **Streamers.** Fit point-mass trajectories (Mendoza et al. 2009 type) to the streamer in position and
   velocity. TIPSY grids LOS separation, plane-of-sky speed and direction and picks the trajectory that puts the
   largest fraction of points within their error bars, ties broken by chi2 (2024A&A...683A.133G). It assumes
   line intensity traces gas density, so streamer masses and rates depend on excitation and abundance (T = 25 K,
   13CO 1.45e-6, HCO+ 1e-9, optically thin) and are lower limits good to an order of magnitude. Then infall time,
   energy and Mdot = M_streamer / T_inf (2024A&A...683A.133G).
8. **Infall from absorption.** Look for redshifted absorption against compact continuum
   (2015ApJ...814...22E, 2012A&A...544L...7P, 2013ApJ...764L..14Z). Report the observed velocity offset of the
   absorption from Vsys first; it is a line-of-sight quantity, and opacity and foreground gas can move the
   absorption minimum. Turning it into a radial infall speed at a radius needs an explicit geometry and
   line-transfer model (2018A&A...615A.141B reports 5.1 km/s at 1.54 arcsec; the pack does not give its
   extraction rule). Check continuum subtraction before reading absorption (general practice; see Pitfalls).
   2018ApJ...869..158F treats infall as detected only near the compact source and an upper limit elsewhere.
9. **Infall rate.** Flattened: Mdot = 2 pi R V_r Sigma, (1.5-3.0)e-6 Msun/yr at 100-200 AU in
   2015ApJ...812...27A. Spherical shell (general practice): Mdot = Omega r^2 rho_mass v_in, with v_in the
   positive inward speed, Omega the solid angle covered by infall (4 pi for a full sphere) and
   rho_mass = mu m_H n, where n is a number density and mu the mean mass per particle of that species in units
   of m_H (2025SciA...11.4512O used mu = 2.33, 2017ApJ...849...56A 2.37 m_H). Example inputs: r ~80 AU,
   density ~2.3e9 cm-3, v_in ~7.1 km/s, disk covering ~50% (~2 pi) in 2017A&A...603A..10B (the pack does not say
   which particle the density counts; check before use). Streamer: M/T_inf (2024A&A...683A.133G); the
   dimensional estimate M v_ff / l uses v_ff = 6 km/s and l = 500 au in 2025SciA...11.4512O (pack parameters).

## Parameter defaults and ranges

Counts are my counts of bibcodes in the pack's parameter, assumption and excerpt lines, envelope and core
papers only. Longer per-paper values: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Pixel clip for mean positions in V(R) | 5 sigma | 5-6 sigma | 2 | 2017ApJ...849...56A (5), 2015ApJ...812...27A (6) |
| Ridge/edge emission threshold | 5 sigma | 5-6 sigma by line | 1 | 2025ApJ...993..120H (5 for 12CO and C18O, 6 for 13CO) |
| Channel S/N for channel-map astrometry (disk PA, i) | SNR > 5 | - | 1 | 2018ApJ...859..111H |
| Low-velocity exclusion in V(R) | drop channels near Vsys | abs(dV) < 1.2 km/s where stated | 2 | 2015ApJ...812...27A (1.2 km/s), 2017ApJ...834..178Y (range not in pack) |
| Tracer split by velocity | isotopologue at low abs(V-Vlsr), 12CO at high | 1.6 km/s boundary | 1 | 2019ApJ...871..100H |
| Inner rotation index p (double power law) | 0.5 (Keplerian) | 0.41-0.54 | 4 | 2017ApJ...849...56A (0.50), 2015ApJ...812...27A (0.54), 2020ApJ...893...51S (0.50, inner fit), 2014ApJ...796..131O (0.41) |
| Outer (envelope) index p | ~1 | 0.85-1.22 | 3 | 2017ApJ...849...56A (1.22), 2015ApJ...812...27A (0.85), 2014ApJ...796..131O (1.16) |
| Single power-law index p | source dependent | 0.57-1.0 | 1 | 2017ApJ...834..178Y (0.57 Lupus 3 MMS, 1.0 IRAS 15398) |
| Envelope-to-disk rotation break, measured | - | 53.7-67 AU | 3 | 2014ApJ...796..131O (53.7), 2017ApJ...849...56A (56), 2015ApJ...812...27A (67) |
| Same break, resolution corrected | - | ~74-90 AU | 2 | 2017ApJ...849...56A (~74), 2015ApJ...812...27A (~90) |
| Disk radius from a kinematic model fit | - | 130 +/- 70 AU | 1 | 2017ApJ...834..178Y (Lupus 3 MMS) |
| Outer-disk profile break in a warped disk (not an envelope transition) | - | 624 +/- 62 au | 1 | 2020ApJ...893...51S |
| Infall speed / free fall (alpha) | model dependent | 0.3 (fit in one paper, inferred from a shock condition in the other) | 2 | 2015ApJ...812...27A, 2017ApJ...849...56A |
| Centrifugal barrier or centrifugal radius | tens of au | 2-250 au | 5 | 2024ApJ...970...28O (2-9), 2016ApJ...824...88O (40-60), 2015ApJ...812...59O (100), 2019A&A...623A..96Y (centrifugal radius 100), 2025SciA...11.4512O (250, massive) |
| Envelope density law | r^-1.5 | r^-1.5; 2017ApJ...834..178Y tried indices -1.5, -2, -2.5 | 6 | 2015ApJ...812...59O, 2016ApJ...824...88O, 2017ApJ...837..174O, 2019ApJ...873...73Z, 2019A&A...623A..96Y, 2017ApJ...834..178Y |
| Temperature law | power law, index -0.4 | -0.4 to -0.6, or constant 25-44 K | 5 | 2017ApJ...834..178Y (q=-0.4), 2019ApJ...871..100H (70 K, r^-0.4), 2019A&A...623A..96Y (r^-0.6), 2017ApJ...849...56A (44 K), 2024A&A...683A.133G (25 K) |
| Envelope thickness | thin | 20-30 au, or h = 0.2 r | 3 | 2017ApJ...837..174O, 2024ApJ...970...28O, 2019ApJ...873...73Z |
| Model intrinsic line width | fixed 0.5 km/s | 0.5 fixed; 0.1-1.0 km/s explored | 2 | 2015ApJ...812...59O (0.5), 2013A&A...560A.103M (free 0.1-1.0) |
| C18O absolute abundance X(C18O) | ~1e-7 | 4e-8 to ~9e-7 | 4 | 2017ApJ...849...56A (4e-8), 2015ApJ...815..106H (1e-7), 2018ApJ...869...59W (4.8e-7), 2019ApJ...871..100H (X_CO 5e-4 with X_CO/X_C18O = 560, so ~8.9e-7, my arithmetic) |
| Model grid steps | 5 deg in PA and i | - | 1 | 2017ApJ...834..178Y (outflow model grid) |

## Software

Counts are from the pack aggregate "Software named in the matched steps" and cover all 213 papers, including
off-topic ones. Paper examples are given only where an excerpt or parameter line names the tool for that paper.

| Task | Tools (aggregate count) | Paper examples |
|---|---|---|
| Calibration, imaging, PV cuts, model filtering | casa 27; casa simobserve 1, casa simulator 1, casa impv 1, impv 1 | 2015ApJ...812...27A (simobserve), 2020ApJ...893...51S (simobserve), 2014ApJ...796..131O (CASA simulator) |
| PV extraction and cube handling in Python | pvextractor 6, spectral-cube 5, astropy 3 | 2018ApJ...863..193V (PVExtractor, galaxy cluster) |
| Older or alternative reduction | gildas 6, miriad 3 | 2025A&A...693A..76C (GILDAS) |
| PV rotation-curve fitting (ridge/edge) | slam 2 | no paper-level attribution in the pack |
| Infalling-rotating envelope models | feria 2 | no paper-level attribution in the pack |
| Streamer trajectories | tipsy 2 | 2024A&A...683A.133G (with scipy) |
| Radiative transfer for synthetic cubes | radmc-3d 6, hyperion 3, lime 1, mollie 1 | 2020ApJ...893...51S (RADMC-3D), 2015ApJ...811...92C (RADMC-3D, warped disk), 2018A&A...614A.113H (LIME) |
| Hydrodynamic comparison | sfumato 1 | 2014ApJ...796....1T compared with a simulation (finest cell 0.85 AU, sink 3.4 AU) |
| Samplers and fitting | emcee 4, lmfit 1, scipy 1 | 2018ApJ...861...72C (emcee on a PV cut, debris disk) |

The fitting-method aggregate (all 213 papers) lists 40 phrasings, almost all used once. About ten describe
by-eye or manual tuning ("by-eye comparison of models, no formal fit", "Manual adjustment of infall velocity; no
formal fit", "Visual comparison, no formal fit" and similar), and four name MCMC, emcee or Bayesian fits (my
count of the phrasing lines). That shows both styles occur; it does not establish which dominates.

## Pitfalls

- **Missing flux biases outer rotation.** 2014ApJ...796..131O: resolved-out large scales overestimate rotation
  at large radii, so fit only R<100 AU. 2018ApJ...859..111H had no single-dish data to check resolved-out
  12CO. Filter models with simobserve (2015ApJ...812...27A) or add ACA/TP data.
- **Resolution bias in the break radius.** Mean-position fits underestimate R_b when resolution is limited
  (2015ApJ...812...27A); correct it, or test the method on model PV diagrams (2020ApJ...893...51S).
- **Inclination is weakly constrained, degenerate and convention dependent.** 2015ApJ...812...27A could not
  constrain i from its disk model; 2020ApJ...893...51S could not measure the outer disk inclination
  independently; 2021A&A...646A...1K reports a k-i degeneracy. With i = 90 deg edge-on, M* scales as
  1/sin^2 i, so propagate it. Putting an i = 0 edge-on value (2019ApJ...873...73Z) into that formula gives a
  badly wrong mass.
- **The major/minor-axis split is not a unique diagnostic.** Expansion, projection, warps and foreground gas can
  mimic infall signatures (2013A&A...560A.103M, 2020ApJ...893...51S). You need the near side to tell inflow from
  outflow along the minor axis.
- **Self-absorption and line optical depth.** 2017ApJ...843...27L weighted its fit to the blueshifted side
  because of redshifted self-absorption; 2014ApJ...791..123W treats the absorption dip as optically thick;
  2013A&A...560A.103M could not separate infall plus Keplerian from pure Keplerian in the outer 30 AU because
  of low S/N and foreground absorption.
- **Dust opacity hides the midplane.** 2017ApJ...843...27L: the disk is optically thick in dust, so molecules
  near the midplane cannot be probed. Missing line emission there need not mean missing gas.
- **Continuum subtraction can erase or fake absorption.** 2024AJ....167...94H shows continuum subtraction
  leaving a negative image of a clump. Compare cubes with and without subtraction before reading absorption.
- **Outflow contamination.** 2025SciA...11.4512O excluded the redshifted streamer from methanol analysis for this
  reason; 2014ApJ...796....1T notes missing flux and outflow complicate lines near systemic velocity.
- **Do not assume free fall.** alpha ~0.3 in 2015ApJ...812...27A (model fit) and 2017ApJ...849...56A (inferred
  through a shock condition, so model dependent); 2025SciA...11.4512O states infall there is neither free-fall
  nor viscous.
- **Non-unique models.** 2019A&A...623A..96Y: evolutionary time and relative velocity not unique;
  2018ApJ...859..111H: genetic-algorithm solution may not be unique; 2020A&A...634L..12D: no combination of
  Rd and theta0 reproduced the wide redshifted component.
- **Fixed model structure is a systematic, not a statistical, error.** 2017ApJ...849...56A fixed a vertically
  isothermal temperature profile because the resolution could not resolve vertical structure;
  2025A&A...693A..76C calls its disk model a toy proof of concept. Quote these limits next to the fit errors.
- **Errors that are not propagated.** TIPSY does not propagate errors in fixed parameters (stellar mass,
  distance, Vsys) (2024A&A...683A.133G). By-eye fits give no formal uncertainties (2015ApJ...812...27A;
  2015ApJ...812...59O says its rms statistics are not meaningful; 2018A&A...614A.113H tuned visually).
  2024ApJ...967...15K errors exclude distance uncertainty and density gradients.
- **Masses, rates and j are limits, and the reason matters.** TIPSY streamer masses and rates assume optically
  thin emission and intensity tracing density, and are lower limits good to an order of magnitude
  (2024A&A...683A.133G). The ALMA1 mass in 2025SciA...11.4512O is stated as an upper limit under the optically
  thin approximation; that is source specific, since in general an optically thin assumption underestimates mass
  where dust is thick. Specific angular momentum can be only an upper limit (2016ApJ...832..158Z). Say what
  sets each limit.
- **Unstated settings.** Pack aggregates: CASA version not stated in 20 cards, self-calibration solution
  intervals in 16, continuum subtraction and line-free channels in 16 (plus similar phrasings 14, 10, 9), flux
  scale uncertainty in 13. Record these and the PV cut width.

## Verification checks

What the papers did:
- Compare single and double power-law fits by reduced chi2: 1.6 vs 4.0 (2017ApJ...849...56A), 1.6 vs 2.0
  (2015ApJ...812...27A); sum of squared residuals per dof (2014ApJ...796..131O).
- Leave Vsys free and confirm it (2017ApJ...849...56A recovered 5.8 km/s).
- Test the extraction method on synthetic Keplerian PV diagrams (2020ApJ...893...51S) and analyse resolution
  bias (2015ApJ...812...27A appendix).
- Try other geometries: spherical vs flattened envelope (2015ApJ...812...27A); warped vs coplanar disk
  (2020ApJ...893...51S); density indices -1.5, -2, -2.5 (2017ApJ...834..178Y). The validation aggregate also
  lists "Radial-expansion and circular-shape variants tested and found worse" and "Singular isothermal sphere
  gives indistinguishable fit" (one paper each, not named there).
- Vary the key model parameter: Rd and theta0 (2020A&A...634L..12D); a smaller 0.2 Msun mass
  (2014ApJ...796..131O); distance 2.38 vs 1.7 kpc (2024ApJ...967...15K).
- Cross-check masses with literature values (2017ApJ...834..178Y matched the 0.03 Msun of Hsieh et al. 2016).
- Measure the profile in several isotopologues with per-line thresholds and combine methods
  (2025ApJ...993..120H: 12CO, 13CO, C18O; mean of ridge and edge masses).
- Validate trajectory code against N-body two-body runs with REBOUND (2024A&A...683A.133G).

What a careful referee adds:
- Show both major and minor axis PV diagrams with the model overlaid and residuals, and state the near side.
- Fit rotation-only, rotation plus infall, expansion and warp models before claiming infall.
- Propagate inclination, distance and Vsys uncertainties into M*, r_CB, j and Mdot, and state the inclination
  convention.
- Show that the result survives a change of emission threshold and of the excluded low-velocity range.
- Check optical depth (isotopologue ratio or line modelling) before reading line shapes as kinematics.
- State whether models were filtered through the same uv coverage, and quantify missing flux.
- Quote flux-scale uncertainty and fixed-structure assumptions separately from statistical errors.

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2014ApJ...796..131O: L1527, broken power law, missing-flux limit, infall model in CASA simulator
- 2015ApJ...812...27A: TMC-1A, double power law with MC errors, alpha = 0.3, resolution bias, Mdot
- 2017ApJ...849...56A: L1527 rotation break, Vsys free, chi2 single vs double, shock-inferred alpha
- 2017ApJ...834..178Y: power-law V(R) with Vsys free, chi2 kinematic model, outflow inclination grid
- 2020ApJ...893...51S: Gaussian-fit PV method tested on model disks, RADMC-3D plus simobserve, warped disk
- 2015ApJ...812...59O: ballistic envelope (CB) model in CS, fixed line width
- 2016ApJ...824...88O: IRE plus Keplerian model in IRAS 16293 A, r_CB 40-60 AU
- 2017ApJ...837..174O: CB model with free M, r_CB, i
- 2019ApJ...873...73Z: massive envelope-disk transition; inclination defined edge-on = 0
- 2024ApJ...970...28O: IRE/Keplerian grid at a few au in B335
- 2017ApJ...843...27L: HH 212 flared envelope, r_c and r_0 from l and M, dust-thick midplane
- 2019ApJ...871..100H: envelope model with C18O and CO velocity split
- 2025ApJ...993..120H: ridge and edge methods, mean mass
- 2024A&A...683A.133G: TIPSY streamer trajectories, infall rate, lower limits
- 2025SciA...11.4512O: massive streamers, centrifugal barrier 250 au, infall rate inputs
- 2020A&A...634L..12D: Ulrich infall comparison
- 2019A&A...623A..96Y: HL Tau envelope particle model
- 2013A&A...560A.103M: infall plus Keplerian vs pure Keplerian not separable
- 2015ApJ...814...22E: inverse P-Cygni infall in B335
- 2018A&A...615A.141B: infall velocity from absorption in G31.41+0.31
- 2025A&A...693A..76C: Keplerian plus infall toy model in a massive disk
- 2017A&A...603A..10B: spherical infall inputs in a massive core
