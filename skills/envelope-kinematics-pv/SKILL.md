---
name: alma-envelope-kinematics-pv
description: "Measure infall and rotation in protostellar envelopes from ALMA line cubes with position-velocity (PV) diagrams: rotation-profile power laws and break (Keplerian) radii, infalling-rotating envelope (centrifugal barrier, Ulrich) models, streamer trajectories, redshifted-absorption infall, specific angular momentum, protostellar mass and mass infall rate. Use when a cube shows a velocity gradient across a Class 0/I source or a massive hot core and you must decide whether it is infall, rotation or both, or when you check someone else's PV analysis. Built from a 493-paper ALMA evidence pack (2012-2026); 303 of those papers carry the star-formation field tag (pack aggregate)."
---

# Envelope kinematics from PV diagrams (infall, rotation, centrifugal barrier)

Papers cut PV diagrams along the disk/envelope major axis (perpendicular to the outflow) and along the minor axis.
Under a thin, axisymmetric, flattened geometry with known near side, rotation shows up mainly along the major
axis and infall adds a velocity gradient along the minor axis. That reading is not unique: expansion, projection,
warps and foreground gas can mimic it (L1489 IRS turned out to be a warped-disk system, 2020ApJ...893...51S; a
PV gradient alone cannot tell inflow behind a source from outflow in front of it, 2014ApJ...784...78R). Papers
then (a) fit a power law to a rotation profile V(R), (b) fit or compare forward models of an infalling-rotating
envelope plus disk, or (c) look for redshifted absorption against the continuum. The mistakes that matter most:
(1) trusting low-velocity and large-radius PV points, where interferometric filtering, cloud contamination and
self-absorption distort the profile (2014ApJ...796..131O kept only R<100 AU because resolved-out large scales
overestimate rotation; 2023ApJ...958...98F excluded filtered-out channels), and (2) quoting masses, break radii and
infall speeds without saying how inclination (and its convention), systemic velocity, emission threshold and
resolution bias were handled (the mean-position method "may systematically underestimate" the break radius at
limited resolution, 2015ApJ...812...27A; the fitted index moved from 0.49 to 0.81 when the extraction threshold
dropped from 16 to 9 sigma in 2026ApJ..1003..219W).

> Always report: line and an optical-depth check, PV cut PA and width, systemic velocity and whether it was fit,
> inclination with its source and convention (i = 90 deg edge-on or i = 0 edge-on), near side, distance, emission
> threshold for data points, velocity ranges excluded, flux-scale uncertainty, and whether models were spatially
> filtered. Cards flag PV extraction widths as not stated (2018ApJ...863...72O, 2014ApJ...784...78R).

**Scope of the evidence.** The regex tagger pulled 493 papers; the science-field aggregate lists star formation
303, astrochemistry 132, protoplanetary disks 107, nearby galaxies 90, Milky Way ISM 76, AGN 65, evolved stars 52
(pack aggregates; papers carry several fields). Many hits are outflow, galaxy or AGB-star PV work, and most of the
40 full excerpts are off-topic. This skill cites the protostellar envelope, core and streamer papers for the recipe
and the others only for generic PV practice. It does not claim which workflow most envelope papers follow: the
pack has no envelope-only denominator.

## When to use

- A Class 0/I protostar shows a velocity gradient in C18O, 13CO, CS, SO, CH3OH or HCO+ and you need the
  transition from infall to Keplerian rotation (2015ApJ...812...27A, 2017ApJ...849...56A, 2023ApJ...958...98F,
  2025ApJ...993..120H, 2024ApJ...966...32E).
- You want the centrifugal barrier radius and protostellar mass from an infalling-rotating envelope model
  (2015ApJ...812...59O, 2016ApJ...824...88O, 2017ApJ...837..174O, 2020ApJ...904..185O, 2024ApJ...970...28O,
  2025A&A...701A.141L).
- Pseudodisk or flattened envelope with infall plus angular-momentum-conserving rotation (2014ApJ...786..114L,
  2017ApJ...843...27L, 2019ApJ...879..101L, 2019ApJ...871..100H, 2018A&A...615A..58Y).
- Streamers feeding a disk: trajectory fits, infall time, mass infall rate (2024A&A...683A.133G,
  2023ApJ...958...98F, 2025ApJ...985..166K, 2024A&A...682A..61C, 2014ApJ...793....1Y, 2025SciA...11.4512O).
- Infall from redshifted (inverse P-Cygni) absorption or asymmetric profiles (2015ApJ...814...22E,
  2012A&A...544L...7P, 2013ApJ...764L..14Z, 2018A&A...615A.141B, 2018ApJ...861...14C).
- Massive hot cores and disks with rotation plus infall (2020ApJ...904..181L, 2026ApJ..1003..219W,
  2025SciA...11.6953M, 2017A&A...603A..10B, 2015ApJ...813L..19J, 2019ApJ...877L..25M, 2024ApJ...967...15K).

## When not to use

| Situation | Use instead |
|---|---|
| A settled, mostly Keplerian protoplanetary or Class II disk; you want M*, emission height, i, PA | `keplerian-disk-kinematics` skill. PV-curve masses of edge-on Class II disks (2026A&A...710A.140M) belong there; use this skill only for the envelope-to-disk transition |
| Rotation curves, dispersion and inflow/outflow in galaxies (3DBarolo, GalPak3D, kinemetry) | `galaxy-3d-kinematics` skill; `smbh-gas-dynamics` for black-hole masses. Galaxy PV papers here (2021A&A...655A..25Z, 2020MNRAS.493.3744F, 2019A&A...623A..79C) follow that workflow |
| Outflow mass, momentum, rotating outflows or disk winds | `outflow-energetics` skill. Outflow PV papers here (2018A&A...618A.120L, 2018ApJ...863...72O, 2020A&A...634L..12D) measure the flow, not the envelope |
| AGB or post-AGB expanding or rotating envelopes | `evolved-star-envelopes` skill (2018A&A...614A.113H, 2020ApJ...890L..14T are in this pack only by regex) |
| Cluster-scale or filament inflow without a central protostar's potential | Hub-filament velocity-gradient work (2024A&A...690A.185W uses region rest velocity as a proxy for core velocity); this skill's point-mass models do not apply |
| Single moment-1 map is all you need for PA | `moment-maps` skill |

## Steps

1. **Fix the geometry before cutting PV diagrams.**
   - Centre: continuum peak (2026ApJ..1003..219W centred its priors on the dust peak; 2025SciA...11.6953M used
     the long-baseline 1.3 mm peak; 2021A&A...655A..25Z did the same in a galaxy).
   - PA of the disk/envelope major axis: perpendicular to the jet or outflow (2015ApJ...812...59O assumes the
     outflow axis is perpendicular to the envelope mid-plane), the steepest velocity gradient (2025SciA...11.6953M)
     or a Gaussian-fit PA of the emission (2024ApJ...966...32E). Check the gradient is perpendicular to the outflow
     before calling it rotation (2020ApJ...904..181L). Warped systems have different inner and outer PAs (69 and
     54 deg in 2020ApJ...893...51S); 2026ApJ..1003..219W fit separate envelope and disk PAs (18 and 43 deg).
   - Inclination: continuum aspect ratio, i = arccos(minor/major) for a thin disk (2017ApJ...845...58Z,
     2018A&A...619A..39F; 74 deg for VLA1623 B in 2022MNRAS.515..543C); an axis ratio near 0.5 gave only i >= 60 deg
     in 2020ApJ...904..181L. A thick-disk version, cos^2 i = ((b/a)^2 - q^2)/(1 - q^2) with q = 0.2, is used for
     galaxies (2024ApJ...977..161V). Other routes: an outflow model fit (75-90 deg allowed in 2018ApJ...863...72O),
     a model grid in 5 deg steps of PA and i (2017ApJ...834..178Y), a free parameter in a cube fit (50 +/- 4 deg in
     2026ApJ..1003..219W), or fixed edge-on for L1527 (85 deg in 2017ApJ...849...56A, 90 deg in 2014ApJ...796..131O).
   - **Pick one inclination convention and convert everything to it.** This skill uses i = 90 deg for edge-on (as
     2014ApJ...796..131O, 2017ApJ...849...56A and 2020ApJ...904..181L, which states i = 0 is face-on).
     2019ApJ...873...73Z defines i = 0 as edge-on, so convert with i_here = 90 deg - i_paper; 2024ApJ...966..192S
     measures i between the line of sight and the outflow axis. Record the original convention and the near side
     (2023ApJ...958...98F: near side 59 deg E of N), which you need to tell infall from expansion.
   - Systemic velocity: fit it, then check. 2017ApJ...849...56A left it free and recovered 5.8 km/s;
     2024A&A...690A..46S fixed 2.84 km/s after a first fit; 2018ApJ...864L..25O found 5.3 km/s fit better than
     5.5 km/s; 2019ApJ...879..101L refined it to 9.10 km/s; 2024A&A...682A..61C explored 2.9-3.9 km/s. The PV fit
     Vsys moved from -51.27 to -52.10 km/s between thresholds in 2026ApJ..1003..219W.
2. **Choose lines by what they trace.** C18O and 13CO are candidate lower-opacity tracers for the rotation
   profile (2017ApJ...849...56A, 2015ApJ...812...27A, 2023ApJ...958...98F), but isotopologue identity does not
   make a line optically thin: check opacity first (2015ApJ...812...27A lists optical depth among its mass
   uncertainties). 2023ApJ...958...98F found peak 13CO/C18O brightness ratios of 2-3, so C18O thin and 13CO thick
   (ratio < 4). CS, SO, CH3OH and HCOOH resolve the envelope and centrifugal barrier (2015ApJ...812...59O CS,
   2014ApJ...796..131O SO ring at 70-120 AU, 2024ApJ...970...28O CH3OH and HCOOH, 2025A&A...701A.141L SO ring
   taken as the barrier at 65 au). For massive cores, CH3CN K ladders get more compact with steeper gradients at
   higher K (2020ApJ...904..181L); 2026ApJ..1003..219W stacked CH3OCHO lines weighted by integrated flux.
   Tracer split by velocity: 2019ApJ...871..100H fit C18O at abs(V-Vlsr) < 1.6 km/s and CO above.
3. **Extract the PV diagrams.** Major and minor axis cuts through the centre are the standard pair
   (2015ApJ...812...27A compared models with both). Cut width (my count, 9 envelope and core papers): about one
   beam (2018ApJ...863...19A, 2024ApJ...966...32E, 1.6 arcsec in 2024A&A...682A..61C) or 0.1-0.5 arcsec (0.5 in
   2023ApJ...958...98F, 2022A&A...664A.171V and 2024A&A...684A.189V, 0.2 in 2019A&A...621A..83S, 0.1 in
   2024A&A...686L..13D; 5 pixels in 2020ApJ...897...59M). Tools: CASA `impv` (2020ApJ...904..181L ran it on observed and model cubes),
   `pvextractor` (2018ApJ...863..193V along a curved filament path), SLAM (2023ApJ...958...98F).
4. **Measure the rotation profile V(R)** (the "ridge" approach).
   - Per channel, take the intensity-weighted mean position of pixels above a clip level (5 sigma in
     2017ApJ...849...56A, 6 sigma in 2015ApJ...812...27A) or a Gaussian-fit centroid (2022A&A...664A.171V kept
     centroids with peak > 5x the fit error and SNR > 10; positional accuracy Theta/(2 SNR)).
   - Drop low velocities where filtering and envelope confusion dominate: abs(dV) < 1.2 km/s in
     2015ApJ...812...27A; 7.7-8.9 km/s in 2018A&A...615A..58Y; filtered-out channels in 2023ApJ...958...98F;
     range not given in the pack for 2017ApJ...834..178Y. Limit radii too (r < 100 au inner fit in
     2020ApJ...893...51S, R < 100 AU in 2014ApJ...796..131O).
   - Fit V = V_b (R/R_b)^-p in log R - log V, single and double power law, by chi2 (2017ApJ...849...56A,
     2015ApJ...812...27A) or orthogonal distance regression with errors on both axes and inverse-square weights
     (2026ApJ..1003..219W). p = 0.5 means Keplerian; p = 1 means rotation plus infall conserving angular momentum
     (general practice; stated in 2024ApJ...966...32E).
   - Errors: Monte Carlo dispersal of points within the error bars, Gaussian in log R and rectangular in log V
     (2015ApJ...812...27A).
   - Ridge and edge methods (SLAM, 4 in the software aggregate): MCMC fits in both modes, final values averaged
     (2023ApJ...958...98F; mean of ridge and edge masses in 2025ApJ...993..120H, with 5 sigma for 12CO and C18O and
     6 sigma for 13CO, p fixed 0.5 for the 12CO mass). Ridge and edge bracket the Keplerian mass
     (2024ApJ...966...32E). 2024ApJ...966...32E fit only the opposite side of each disk to limit contamination.
   - Test the threshold: 16 sigma traced the inner Keplerian part (p = 0.49 +/- 0.04) and 9 sigma the extended
     transition (p = 0.81 +/- 0.06) in 2026ApJ..1003..219W.
   - Correct the apparent break radius for resolution: 67 AU apparent became ~90 AU in 2015ApJ...812...27A;
     56 AU became ~74 AU in 2017ApJ...849...56A.
5. **Convert to mass and angular momentum** (general practice; assumptions in brackets).
   - Keplerian: M* = R V_rot^2 / G with V_rot = V_obs / sin i [i = 90 deg edge-on convention; point mass, disk
     mass neglected as in 2019ApJ...873...73Z]. M* scales as 1/sin^2 i; 2020ApJ...904..181L quotes masses as
     M/sin^2 i, which is the safe way to report them when i is poor.
   - Centrifugal barrier of a ballistic infalling-rotating envelope (general practice): M = r_CB v_CB^2 / (2G)
     [zero-energy (parabolic) orbit with conserved j, as assumed in 2025A&A...701A.141L; v_CB is the deprojected
     rotation speed where the radial velocity vanishes]. It does not hold for infall slower than free fall or
     finite-energy streamers. The centrifugal radius is r_c = l^2/(GM) and the barrier r_0 = l^2/(2GM)
     (2017ApJ...843...27L).
   - Specific angular momentum: for flattened rotation the axial part is j_z = R V_phi (cylindrical R,
     deprojected V_phi); for a streamer on an arbitrary path use the full vector j = r x v (general practice).
     Examples: j = 6.1e-4 km/s pc (about 126 au km/s) in L1527 (2014ApJ...796..131O); j_IRE = 7.9e-4 km/s pc in
     L483 (2018ApJ...863...72O); an upper limit ~3.6e2 au km/s from an assumed 20 Msun and r_CB < 125 au, against
     ~1e4 au km/s "apparent" j from larger-scale gradients (2020ApJ...904..181L).
6. **Forward-model the envelope plus disk and compare with PV diagrams or the cube.**
   - Ballistic infalling-rotating envelope (IRE, "CB model"; FERIA, 3 in the software aggregate, no paper-level
     attribution): M, r_CB, i free in 2017ApJ...837..174O; density r^-1.5 (2015ApJ...812...59O,
     2016ApJ...824...88O, 2017ApJ...837..174O, 2019ApJ...873...73Z, 2016ApJ...820L..34S); thin envelope (30 au in
     2017ApJ...837..174O, 20 au in 2024ApJ...970...28O, h = 0.2 r in 2019ApJ...873...73Z) or flared 20-30 deg
     (2014ApJ...795..152O, 2020ApJ...904..185O); optically thin, no radiative transfer (2020ApJ...904..185O,
     2018ApJ...854...96O). 2024ApJ...970...28O explored i 70-90 deg, M* 0.02-0.08 Msun, r_CB 2-9 au;
     2020ApJ...904..185O compared Keplerian with IRE at r_CB = 5, 10, 20 au.
   - Infall slower than free fall, V_r = alpha V_ff: alpha = 0.3 fit in 2015ApJ...812...27A; ~0.3 inferred, not
     fit, from an isothermal shock condition in 2017ApJ...849...56A; free-fall speeds scaled down by ~1.5 in
     2025A&A...701A.141L. 2020ApJ...904..181L compared Keplerian plus constant 2.5 km/s infall with an Ulrich flow.
   - Parametric infall plus rotation fit to PV: free-fall, conserved j, LTE, q = -0.4, polar region within 80 deg
     empty (2017ApJ...834..178Y); n(R0), p, Vin(R0) free with j fixed at 3e-5 km/s pc or 0 and a 60 deg polar
     cavity (2018A&A...615A..58Y); rho0, p, theta_flared, V_rot,0, V_infall,0, F_C18O free (2019ApJ...871..100H);
     seven free parameters including vr0, vphi0 (2014ApJ...786..114L).
   - Ulrich (rotating collapse) envelopes: 2020A&A...634L..12D (Rd 700 au, theta0 70 deg, 1.1 Msun);
     2019A&A...623A..96Y (particle model, 1.8 Msun, centrifugal radius 100 au, r^-1.5). 2026ApJ..1003..219W fit
     a Keplerian disk plus Ulrich envelope to the whole PPV cube with emcee (chi2 likelihood, model and data
     normalised to their peaks, bounded priors on M*, Rin, Rc, Rout, i, PAs, mass ratio).
   - Full radiative transfer when temperature and abundance matter: RADMC-3D (2015ApJ...811...92C, warped disk),
     SPARX (2020ApJ...904..181L, LTE CH3CN cubes smoothed with `imsmooth`, PV with `impv`), LIME
     (2020ApJ...891...61Y). 2020ApJ...901..166V added a 3000 au rotating infalling envelope when a disk alone could
     not reproduce the short-uv visibilities.
   - Filter models through the same uv coverage (`simobserve`, 2015ApJ...812...27A). 2020ApJ...904..181L states it
     applied no interferometric filtering to its model cubes; treat such comparisons as weaker.
   - Before calling a gradient infall, run the competing models: pure Keplerian, Keplerian plus infall, pure
     envelope, expansion and a warp. Papers that did parts of this: four models M1-M4 in 2020ApJ...904..181L; pure
     disk and pure Ulrich both failed in 2026ApJ..1003..219W; spherical vs flattened envelope in
     2015ApJ...812...27A.
7. **Streamers.** Fit point-mass trajectories (Mendoza et al. 2009 type) in position and velocity.
   - Manual tuning of initial polar and azimuthal angles and cloud radius, with j set so the centrifugal radius
     equals the disk radius (2023ApJ...958...98F; same assumption in 2025ApJ...985..166K). The authors say the
     values may not be best or unique (2023ApJ...958...98F). Families of trajectories with varying theta0
     (2026ApJ..1003..219W); initial angles to +/- 3 deg (2014ApJ...793....1Y).
   - TIPSY (2024A&A...683A.133G): point-mass gravity only, M*, distance and Vsys fixed, line intensity assumed
     to trace density, T = 25 K, 13CO 1.45e-6 and HCO+ 1e-9, optically thin. Masses and rates inherit all of
     these.
   - Streamer edges at 3 sigma in moment 0 and t_ff = sqrt(R^3 / 2GM*) (2025ApJ...985..166K); then
     Mdot = M_streamer / t_ff (general practice). PV path width equal to the beam along the streamer (2024A&A...682A..61C).
   - Mass from C18O in LTE with T_ex from peak 13CO, X(C18O) = 3e-7 (2023ApJ...958...98F); abundance (1-2)e-7
     and T_ex 10-30 K set the mass uncertainty in 2025ApJ...985..166K.
8. **Infall from absorption.** Look for redshifted absorption against compact continuum
   (2015ApJ...814...22E, 2012A&A...544L...7P, 2013ApJ...764L..14Z). Report the observed velocity offset of the
   absorption from Vsys first; it is a line-of-sight quantity, and opacity and foreground gas can move the
   absorption minimum. Turning it into a radial infall speed at a radius needs an explicit geometry and
   line-transfer model (2018A&A...615A.141B reports 5.1 km/s at 1.54 arcsec; the pack does not give its
   extraction rule; 2019ApJ...885...98S used a 1D spherical collapse model with n ~ r^-1.8). Hill5-type fits to
   asymmetric profiles: initial guesses tau 0.1-30, v_in 0.1-4 km/s (2018ApJ...861...14C), which may underestimate
   v_in, so the rate is a lower limit. 2018ApJ...869..158F treats infall as detected only near the compact source
   and an upper limit elsewhere.
9. **Infall rate.** Flattened: Mdot = 2 pi R V_r Sigma, (1.5-3.0)e-6 Msun/yr at 100-200 AU in
   2015ApJ...812...27A; 2.3e-4 Msun/yr from Sigma = 0.71 g cm^-2 and 2.5 km/s at 900 au in 2020ApJ...904..181L
   (consistent with 2 pi R V_r Sigma, my arithmetic). Ulrich envelope: Mdot = M_env / I, with I the streamline
   integral of normalised density, 7e-3 Msun/yr as an order-of-magnitude value (2026ApJ..1003..219W). Spherical
   shell (general practice): Mdot = Omega r^2 rho_mass v_in, with v_in the positive inward speed, Omega the solid
   angle covered by infall (4 pi for a full sphere) and rho_mass = mu m_H n, n a number density and mu the mean
   mass per particle of that species in units of m_H (2.33 in 2025SciA...11.4512O, 2.37 in 2017ApJ...849...56A,
   2.3 in 2012A&A...544L...7P). Example inputs: r ~80 AU, density ~2.3e9 cm-3, v_in ~7.1 km/s, ~50% (~2 pi)
   covered (2017A&A...603A..10B; the pack does not say which particle the density counts). Envelope infall is a
   mass supply, not instantaneous accretion onto the star (2026ApJ..1003..219W).

## Parameter defaults and ranges

Counts are my counts of bibcodes in the pack's parameter, assumption, limitation and excerpt lines, envelope, core
and streamer papers only. Longer per-paper values: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Pixel clip for mean positions in V(R) | 5 sigma | 5-6 sigma | 2 | 2017ApJ...849...56A (5), 2015ApJ...812...27A (6) |
| Ridge/edge or PV-point threshold | 5 sigma | 3-6 sigma by line; 9 and 16 sigma in a massive disk | 4 | 2025ApJ...993..120H (5, 6), 2025ApJ...992...18P (ridge 6 for 13CO, 3 for C18O), 2023ApJ...958...98F (>5), 2026ApJ..1003..219W (9, 16) |
| Centroid acceptance | SNR > 10 | SNR > 5 to > 10 | 2 | 2022A&A...664A.171V (>10), 2018ApJ...859..111H (>5, channel-map astrometry) |
| PV cut width | ~1 beam or 0.5 arcsec | 0.1-1.6 arcsec | 9 | see Step 3 |
| Low-velocity exclusion in V(R) | drop channels near Vsys | abs(dV) < 1.2 km/s where stated | 4 | 2015ApJ...812...27A, 2018A&A...615A..58Y (7.7-8.9 km/s), 2023ApJ...958...98F (filtered channels), 2017ApJ...834..178Y (range not in pack) |
| Tracer split by velocity | isotopologue at low abs(V-Vlsr), 12CO at high | 1.6 km/s boundary | 1 | 2019ApJ...871..100H |
| Inner rotation index p | 0.5 (Keplerian) | 0.48-0.61 | 4 | 2017ApJ...849...56A (0.50), 2015ApJ...812...27A (0.54), 2023ApJ...958...98F (~0.6 CO, 0.48 SO edge), 2026ApJ..1003..219W (0.49, single law at 16 sigma) |
| Outer (envelope) index p | ~1 | 0.81-1.22 (1.6 in one edge fit) | 4 | 2017ApJ...849...56A (1.22), 2015ApJ...812...27A (0.85), 2023ApJ...958...98F (1.2 +/- 0.4; edge 1.6, ridge 0.9), 2026ApJ..1003..219W (0.81, 9 sigma single law) |
| Envelope-to-disk break, measured | - | 56-265 au | 3 | 2017ApJ...849...56A (56), 2015ApJ...812...27A (67), 2023ApJ...958...98F (265 +/- 9 in 13CO; SO 97 edge, 120 ridge) |
| Same break, resolution corrected | - | ~74-90 AU | 2 | 2017ApJ...849...56A (~74), 2015ApJ...812...27A (~90) |
| Infall speed / free fall (alpha) | model dependent | 0.3 to ~0.67 | 3 | 2015ApJ...812...27A (0.3 fit), 2017ApJ...849...56A (~0.3 inferred), 2025A&A...701A.141L (V_ff / ~1.5) |
| Centrifugal barrier or radius, low mass | tens of au | 2-100 au | 6 | 2024ApJ...970...28O (2-9), 2016ApJ...824...88O (40-60), 2020ApJ...904..185O (50), 2025A&A...701A.141L (65), 2015ApJ...812...59O (100), 2019A&A...623A..96Y (100) |
| Centrifugal barrier or radius, massive | hundreds of au | < 125 to ~1300 au | 4 | 2020ApJ...904..181L (< 125), 2025SciA...11.4512O (250), 2025SciA...11.6953M (grid 0-200), 2026ApJ..1003..219W (1300; streamers 1100-1200) |
| Envelope density law | r^-1.5 | r^-1.5; r^-1.8 in a 1D collapse model | 9 | 2015ApJ...812...59O, 2016ApJ...824...88O, 2017ApJ...837..174O, 2019ApJ...873...73Z, 2019A&A...623A..96Y, 2014ApJ...795..152O, 2016ApJ...820L..34S, 2018ApJ...854...96O; 2019ApJ...885...98S (r^-1.8) |
| Temperature law | power law, index -0.4 | -0.3 to -0.7, or constant 15-44 K | 9 | 2017ApJ...834..178Y (-0.4), 2018A&A...615A..58Y (38 K, -0.4), 2019ApJ...871..100H (70 K, -0.4), 2014ApJ...793....1Y (44 K, -0.3), 2019A&A...623A..96Y (-0.6), 2020ApJ...904..181L (-0.7 beyond 214 au), 2017ApJ...849...56A (44 K), 2024A&A...683A.133G (25 K), 2025ApJ...985..166K (15 K) |
| Envelope thickness | thin | 20-50 au, h = 0.2 r, or flared 20-30 deg | 6 | 2017ApJ...837..174O (30), 2024ApJ...970...28O (20), 2018ApJ...854...96O (50), 2019ApJ...873...73Z (0.2 r), 2014ApJ...795..152O (20 deg), 2020ApJ...904..185O (30 deg) |
| Model intrinsic line width | 0.5 km/s | 0.5-1 km/s fixed; 0.1-1.0 explored | 6 | 2015ApJ...812...59O, 2014ApJ...795..152O, 2016ApJ...820L..34S, 2018ApJ...854...96O (0.5); 2020ApJ...904..185O (1 FWHM); 2013A&A...560A.103M (free 0.1-1.0) |
| C18O abundance X(C18O) | ~1-3e-7 | 4e-8 to ~9e-7 | 8 | 2017ApJ...849...56A (4e-8), 2015ApJ...815..106H (1e-7), 2017ApJ...837...86T and 2025ApJ...985..166K (1.7e-7), 2014ApJ...793....1Y and 2023ApJ...958...98F (3e-7), 2018ApJ...869...59W (4.8e-7), 2019ApJ...871..100H (~8.9e-7 from X_CO 5e-4 and ratio 560, my arithmetic) |
| Model grid steps | 5 deg in PA and i | - | 1 | 2017ApJ...834..178Y |

## Software

Counts are from the pack aggregate "Software named in the matched steps" and cover all 493 papers, including
off-topic ones. Paper examples are given only where an excerpt, parameter line or title names the tool.

| Task | Tools (aggregate count) | Paper examples |
|---|---|---|
| Calibration, imaging, PV cuts | casa 60, impv 5, casa imfit 3, carta 5, casa viewer 2 | 2020ApJ...904..181L (imsmooth, impv) |
| Model filtering | casa simobserve 4, casa simulator 2 | 2015ApJ...812...27A (simobserve) |
| PV extraction and cubes in Python | pvextractor 12, spectral-cube 9, astropy 6 | 2018ApJ...863..193V (PVExtractor and LMFIT, galaxy cluster) |
| Older or alternative reduction | gildas 16, miriad 6, karma 3 | 2022MNRAS.515..543C (IRAM-GILDAS) |
| PV rotation-curve fitting | slam 4, keplerfit 2 | 2023ApJ...958...98F (SLAM ridge and edge, MCMC) |
| Infalling-rotating envelope models | feria 3 | no paper-level attribution in the pack |
| Streamer trajectories | tipsy 3 | 2024A&A...683A.133G (TIPSY paper) |
| Radiative transfer for synthetic cubes | radmc-3d 17, lime 4, hyperion 4, sparx 3, radex 3, ratran 2, hochunk 2, pdspy 2 | 2015ApJ...811...92C (RADMC-3D), 2020ApJ...904..181L (SPARX), 2020ApJ...891...61Y (LIME grid) |
| Samplers and fitting | emcee 7, scipy 5, matlab 3, lmfit 2, mpfit 2 | 2026ApJ..1003..219W (emcee on the PPV cube) |
| Galaxy kinematics (off-topic here) | 3dbarolo 9, galpak3d 3, kinemetry 2 | use the galaxy skill |

The fitting-method aggregate (all 493 papers) lists 40 phrasings, almost all used once. By my count 14 describe
manual, visual or qualitative tuning ("by-eye comparison of models, no formal fit", "Manual visual adjustment of
theta, phi, and R_cloud" and similar), 2 name MCMC (emcee, SLAM) and about 5 name chi2 fits. Both styles occur;
this does not establish which dominates.

## Pitfalls

- **Missing flux and cloud contamination bias low velocities and outer radii.** 2014ApJ...796..131O: resolved-out
  scales overestimate rotation at large radii, so fit only R<100 AU. 2023ApJ...958...98F: cloud contamination and
  filtering near Vsys make the C18O envelope mass a lower limit. 2024ApJ...966..192S: no emission near Vsys
  because optically thick foreground CO is resolved out. 2020ApJ...904..181L: missing flux beyond 2 arcsec can
  flatten the density profile. Filter models with simobserve (2015ApJ...812...27A) or add ACA/TP data.
- **Resolution and threshold bias.** Mean-position fits underestimate R_b at limited resolution
  (2015ApJ...812...27A); correct it. The extraction threshold selects which regime you fit (p 0.49 at 16 sigma
  vs 0.81 at 9 sigma, 2026ApJ..1003..219W): report it and test another.
- **Inclination is weakly constrained, degenerate and convention dependent.** 2015ApJ...812...27A could not
  constrain i from its disk model; 2020ApJ...904..181L says i is not well constrained. Near face-on, M scales
  steeply: 2025SciA...11.6953M fit i 0-20 deg and got 45 Msun, judged too massive for an early protostar; its
  spectral-type mass of 8-16 Msun implies i 20-30 deg instead. Some papers quote masses uncorrected for i (2015MNRAS.447.1826Z). Putting an i = 0 edge-on
  value (2019ApJ...873...73Z) into the 1/sin^2 i formula gives a badly wrong mass.
- **PV-curve masses are ill-defined at modest SNR.** 2026A&A...710A.140M: SNR per spaxel, cloud contamination and
  asymmetries preclude a robust statistical approach, masses scale linearly with distance, and its masses came out
  30-50% above literature values.
- **The major/minor-axis split is not a unique diagnostic.** Expansion, projection, warps and foreground gas can
  mimic infall (2020ApJ...893...51S warped disk; 2014ApJ...784...78R inflow behind vs outflow in front). You need
  the near side. 2025A&A...701A.141L assumes negligible flare so infall does not project onto the major axis;
  state that assumption when you use it.
- **Self-absorption and line optical depth.** 2017ApJ...843...27L weighted its fit to the blueshifted side because
  of redshifted self-absorption; 2014ApJ...791..123W treats the absorption dip as optically thick.
- **Dust opacity hides the midplane and biases masses low.** Sub-mm dust opacity may hide line emission in an
  optically thick disk midplane (2022MNRAS.515..543C); thick inner dust makes continuum masses lower limits
  (2023ApJ...958...98F, 2026ApJ..1003..219W). Missing line emission there need not mean missing gas.
- **Continuum subtraction can fake absorption.** 2023ApJ...958...98F: continuum over-subtraction made negative
  artifacts at the disk centre in optically thick lines. Interferometric filtering can also mimic absorption
  (2021A&A...653A..77P). Compare cubes with and without subtraction before reading absorption.
- **Outflow and companion contamination.** 2025SciA...11.6953M dropped a velocity cluster as outflow-related;
  2024ApJ...966...32E fit only the opposite side of each disk in a protobinary.
- **Do not assume free fall.** alpha ~0.3 in 2015ApJ...812...27A (fit) and 2017ApJ...849...56A (inferred through
  a shock condition, so model dependent); ~1/1.5 in 2025A&A...701A.141L. 2023ApJ...958...98F lists the free-fall
  assumption as a reason its infall rate is only an order of magnitude.
- **Non-unique and idealised models.** Streamer parameters tuned by hand "might not be the best or even unique"
  (2023ApJ...958...98F); alternative origins of spirals remain possible (2026ApJ..1003..219W); a parametric warp
  model is not dynamically consistent and had no systematic parameter search (2015ApJ...811...92C); an
  axisymmetric PPV model leaves spiral residuals (2026ApJ..1003..219W).
- **Fixed model structure is a systematic, not a statistical, error.** 2017ApJ...849...56A fixed a vertically
  isothermal temperature profile because the resolution could not resolve vertical structure. Quote such limits
  next to the fit errors.
- **Errors that are not propagated.** Parameters held fixed (M*, distance, Vsys in TIPSY, 2024A&A...683A.133G)
  carry no uncertainty into the fit unless you vary them. By-eye fits give no formal uncertainties
  (2015ApJ...812...27A; 2018ApJ...863...72O). Calibration uncertainty can sit outside an MCMC fit
  (2020ApJ...892...99C).
- **Masses, rates and j are limits, and the reason matters.** Lower limits: C18O envelope mass under filtering
  (2023ApJ...958...98F), Hill5 infall rate (2018ApJ...861...14C). Upper estimates: a streamer rate that assumes the
  whole streamer falls in (2024A&A...682A..61C), j from an upper-limit r_CB (2020ApJ...904..181L). An optically thin
  assumption generally underestimates mass where dust is thick. Say what sets each limit.
- **Unstated settings.** Pack aggregates: CASA version not stated in 31 cards, self-calibration solution intervals
  in 23 (21 more with iterations), flux scale uncertainty in 20, line-free channels and continuum subtraction in
  20 (plus similar phrasings 18, 17, 13), image and cell size in 11. Record these and the PV cut width.

## Verification checks

What the papers did:
- Compare single and double power-law fits by reduced chi2: 1.6 vs 4.0 (2017ApJ...849...56A), 1.6 vs 2.0
  (2015ApJ...812...27A).
- Leave Vsys free and confirm it (2017ApJ...849...56A recovered 5.8 km/s); analyse resolution bias
  (2015ApJ...812...27A appendix).
- Cross-check PV masses with the cube model: 40.7 vs 40 Msun in 2026ApJ..1003..219W; compare the kinematic break
  radius with the moment-1 transition (2023ApJ...958...98F).
- Run ridge and edge and average them (2023ApJ...958...98F, 2025ApJ...993..120H); they bracket the mass
  (2024ApJ...966...32E).
- Try other geometries: spherical vs flattened envelope (2015ApJ...812...27A); pure disk vs pure Ulrich vs both
  (2026ApJ..1003..219W); four kinematic models across all CH3CN K components (2020ApJ...904..181L). The validation
  aggregate also lists "Singular isothermal sphere gives indistinguishable fit" and "Rejected a bicone-projection
  alternative by comparing with PV shapes" (one paper each, not named there).
- Scan one parameter and show where the model breaks: inclination outside 75-90 deg fails in 2018ApJ...863...72O;
  j = 0, 1, 2, 4 times j_IRE overlaid, 4x overestimates rotation (2018ApJ...863...72O); distance 2.38 vs 1.7 kpc
  (2024ApJ...967...15K).
- Check opacity with an isotopologue ratio (13CO/C18O 2-3, 2023ApJ...958...98F).
- Compare with literature after rescaling for distance and inclination (2023ApJ...958...98F: 0.5 vs 0.4 Msun;
  envelope 0.04 vs 0.07 Msun).

What a careful referee adds:
- Show both major and minor axis PV diagrams with the model overlaid and residuals, and state the near side.
- Fit rotation-only, rotation plus infall, expansion and warp models before claiming infall.
- Propagate inclination, distance and Vsys uncertainties into M*, r_CB, j and Mdot, and state the convention.
- Show the result survives a change of emission threshold and of the excluded low-velocity range.
- State whether models were filtered through the same uv coverage, and quantify missing flux.
- Quote flux-scale uncertainty and fixed-structure assumptions separately from statistical errors.

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2015ApJ...812...27A: TMC-1A, double power law with MC errors, alpha = 0.3, resolution bias, simobserve, Mdot
- 2017ApJ...849...56A: L1527 rotation break, Vsys free, chi2 single vs double, shock-inferred alpha
- 2023ApJ...958...98F: eDisk IRS 63, SLAM ridge/edge, Mendoza streamers, 13CO/C18O opacity check, limits
- 2026ApJ..1003..219W: massive disk plus Ulrich envelope fit to the PPV cube with emcee, PV thresholds, ODR
- 2020ApJ...904..181L: S255IR SMA1, four SPARX models, M/sin^2 i, infall rate and j upper limit
- 2025ApJ...993..120H: ridge and edge per line, mean mass
- 2024ApJ...966...32E: ridge and edge bracket the Keplerian mass, one-sided fits
- 2014ApJ...796..131O: L1527, R<100 AU because of missing flux, SO ring, j
- 2015ApJ...812...59O: ballistic envelope (CB) model in CS, fixed line width
- 2016ApJ...824...88O: IRE plus Keplerian model in IRAS 16293 A, r_CB 40-60 AU
- 2020ApJ...904..185O: IRE vs Keplerian at several r_CB on a 10 au scale
- 2024ApJ...970...28O: IRE/Keplerian grid at a few au in B335
- 2025A&A...701A.141L: SO ring as centrifugal barrier, slowed free fall
- 2019ApJ...873...73Z: massive envelope-disk transition; inclination defined edge-on = 0
- 2018A&A...615A..58Y: B335 infall model, low-velocity exclusion, polar cavity
- 2017ApJ...834..178Y: infall plus conserved-j model, 5 deg grid
- 2019ApJ...871..100H: envelope model with C18O and CO velocity split
- 2024A&A...683A.133G: TIPSY streamer trajectories and their assumptions
- 2025ApJ...985..166K: eDisk streamers, t_ff, mass uncertainty from abundance and T_ex
- 2024A&A...682A..61C: streamer PV path, rate as upper estimate
- 2018ApJ...863...72O: outflow inclination and j scans on PV (useful test design)
- 2015ApJ...814...22E: infall detected in B335
- 2018ApJ...861...14C: Hill5 infall fits, lower-limit rate
- 2018A&A...615A.141B: infall velocity toward a hot core
