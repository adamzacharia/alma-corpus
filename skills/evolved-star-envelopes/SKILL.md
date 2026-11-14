---
name: alma-evolved-star-envelopes
description: "Measure circumstellar envelopes of evolved stars with ALMA: gas and dust mass-loss rates, expansion velocities, shells, spirals, tori and bipolar outflows around AGB stars, red supergiants, yellow hypergiants and post-AGB nebulae, plus free-free mass-loss rates of hot massive-star winds (WR, LBV, B[e], OB supergiants). Use when asked for a mass-loss rate, an envelope or shell mass, a kinematic age, a 1D or 3D envelope model (Monte Carlo or LVG radiative transfer, SHAPE, LIME), or how much ALMA flux is resolved out in an extended CSE. Built from 24 ALMA papers (2014-2024)."
---

# Circumstellar envelopes of evolved stars and mass-loss rates

Turns resolved CO (and SiO, SiS, CS, CI) line cubes, mm dust continuum, or mm/cm free-free flux into mass-loss
rates, envelope masses, velocity fields and timescales. The two mistakes that matter most: (1) treating an
interferometric map of an envelope that spans tens of arcsec as complete: IW Car lost about 25% of its 12CO 3-2
flux (2017A&A...597L...5B), other papers report lost extended flux without a number (2016A&A...586A...5M,
2017A&A...597A..99W), and in IW Car and the Red Rectangle the models then overpredict the faint extended emission
(2017A&A...597L...5B, 2016A&A...593A..92B); and (2) quoting a mass-loss rate as measured when it is degenerate with
abundance, temperature and velocity profiles, or is a lower limit set by optical depth (2016A&A...586A...5M,
2019A&A...629A.146V, 2020A&A...633A..13D).

**Evidence base.** All counts below are my own count of the `evolved-star-envelopes` pack lines unless I say
"pack aggregate". The pack has 24 papers; I treat 2020ApJ...892...52L (infrared colour classification of C- vs
O-rich AGB stars from SiO maser detections) as off-topic for envelope modelling and leave it out of counts, which
leaves 23. They fall into three groups, and the methods do not transfer between them:

| Group | Papers (my count) | Main tracer |
|---|---|---|
| AGB, RSG and yellow hypergiant envelopes | 14 | CO lines, SiO/SiS/CS, dust continuum |
| Post-AGB and pre-planetary nebulae (disk + outflow, jets, ultra-cold outflow) | 4 | CO, 13CO |
| Hot massive-star ionized winds (WR, LBV, B[e], OB/BHG, eta Car) | 5 | mm/cm free-free continuum, RRLs |

This is a small pack. Most methods are seen in one to three papers, so the defaults below are "what the few
papers that did this used", not a consensus. Imaging settings are rarely stated: the pack aggregate lists CASA
version (3), line-free channels (2), image and cell size (2) and self-cal intervals (2) as the most often missing.

## When to use

- Mass-loss rate of an AGB or RSG star from CO line profiles and maps (2017A&A...597A..99W, 2016A&A...586A...5M,
  2019MNRAS.484.1865H, 2020A&A...633A..13D).
- Detached shells, spirals, arcs and episodic mass loss: shell mass and temperature, shell-to-shell spacing,
  kinematic ages (2016A&A...586A...5M, 2019A&A...629A.146V, 2020A&A...633A..13D).
- Radial abundance profiles and photodissociation radii of parent molecules (SiO, SiS, CS, CO, CI)
  (2019A&A...629A.146V, 2018A&A...612L..11S, 2015MNRAS.453.4324M).
- 3D morpho-kinematic models of tori, bipolar outflows and binary-shaped winds (2017A&A...605A..28D,
  2019MNRAS.484.1865H, 2018A&A...616L...3B, 2024A&A...691A..57M).
- Post-AGB nebulae with a rotating disk plus an expanding outflow: masses, angular momentum, disk lifetime
  (2016A&A...593A..92B, 2017A&A...597L...5B), and pre-planetary nebula jets and tori (2017ApJ...835L..13S,
  2017ApJ...841..110S).
- Dust mass and dust mass-loss rate from mm continuum around AGB stars or RSGs (2018A&A...615A..28D,
  2015A&A...573L...1O).
- Free-free mass-loss rates of hot, massive evolved stars from ALMA continuum alone or with ATCA
  (2018A&A...617A.137F, 2019A&A...632A..38A, 2017MNRAS.464L..75F, 2017ApJ...841..130A).
- Magnetic field morphology from line polarisation (Goldreich-Kylafis) in CSEs (2024A&A...686A.274V,
  2020ApJ...899..152H). Linear polarisation only: circular polarisation of extended lines is dominated by beam
  effects (2024A&A...686A.274V).

## When not to use

| Situation | Use instead |
|---|---|
| Line identification in a CSE line survey | `line-identification` (2018A&A...615A..28D is a survey, but this skill only covers its dust and wind physics) |
| Full non-LTE excitation theory, collisional rates, LVG grids in general | `non-lte-excitation` |
| Chemical network modelling of the envelope beyond parent abundance profiles | `chemical-modelling` |
| Free-free versus dust decomposition of the continuum in general | `free-free-synchrotron` |
| Combining 12 m, ACA and Total Power (feather, UVSHORT) in detail | `array-combination` |
| Linear polarisation calibration and debiasing in general | `polarization-magnetic-fields` |
| Young-star outflows (protostellar jets, momentum, force) | `outflow-energetics` |
| Keplerian disk mass and inclination around young stars | `keplerian-disk-kinematics` |
| Classifying AGB populations from IR colours or maser surveys | not covered here (2020ApJ...892...52L is the only such pack paper) |

## Steps

1. **Recover the extended flux before modelling anything.**
   - Goal: know how much emission the interferometer filtered out.
   - Method seen: smooth ALMA cubes to each single-dish beam with CASA `imsmooth` and compare spectra with the
     single-dish spectra (2016A&A...586A...5M, card section "Interferometer vs. single-dish"). Combine ACA with
     Total Power via `feather`, using the TP map as the model for initial cleaning (2017A&A...605A..28D, card); the
     feather scaling is not stated (pack). Merge ALMA with IRAM 30 m pseudo-visibilities with GILDAS UVSHORT after
     continuum subtraction (2019A&A...629A.146V, card); the continuum-subtraction method and the UVSHORT scaling are
     not stated (pack).
   - Evidence of scale: about 25% of 12CO 3-2 flux filtered out (2017A&A...597L...5B); negative artefacts from
     filtering of emission larger than 30 arcsec (2017A&A...597A..99W); Cycle 0 without ACA could not constrain
     the mass-loss history (2016A&A...586A...5M); filtered CO flux inflated polarisation fractions by a factor 2-3
     (2024A&A...686A.274V).
   - If you cannot recover the flux, model the single-dish spectra for the integrated quantities and use ALMA only
     for morphology, as 2016A&A...586A...5M did for the post-pulse wind.

2. **Image lines and continuum.**
   - Weighting seen (each from that paper's card, imaging section, quoted verbatim there; the pack itself only
     lists weighting as often unstated): natural (2016A&A...586A...5M, 2017A&A...597A..99W, 2017A&A...605A..28D
     for 13CO); Briggs robust 0.5 (2018A&A...615A..28D, 2024A&A...686A.274V); both a natural and a robust 0.5 cube
     (2019A&A...629A.146V).
   - Deconvolution (cards): masks built in an iterative procedure with decreasing CLEAN thresholds
     (2016A&A...586A...5M); re-imaging with an iteratively decreasing threshold, masks not stated
     (2017A&A...605A..28D); Steer-Dewdney-Ito CLEAN because Hogbom CLEAN can add artificial clumpiness to extended
     emission (2019A&A...629A.146V).
   - Continuum (cards): `uvcontsub` with a first-order polynomial to line-free channels (2017A&A...597A..99W,
     section 2.1), or `uvcontsub` with the fit order not stated (2024A&A...686A.274V). Self-calibrate on line-free
     continuum and apply to all data (2018A&A...615A..28D); two rounds of phase-only self-cal with solution
     intervals "inf" and "int" (2024A&A...686A.274V, section 2), although its spw and channel selection is not
     stated (pack).
   - If you need defaults the papers do not give, treat them as general practice, not literature evidence.
   - Record what you used: cell, image size, threshold and line-free ranges are the settings the cards most often
     flag as missing (pack aggregate).

3. **Fix the star: position, systemic velocity, terminal velocity.**
   - Locate the star from the continuum peak, a uniform-disk fit in the uv plane, and centroids of high-excitation
     lines; check against Gaia (2018A&A...616L...3B: 15 mas disk, ±3 mas absolute).
   - Expansion velocity from the line half-width: values used in the pack run from 2.5 km/s
     (2018A&A...612L..11S) through 8.5 (2020ApJ...899..152H) and 14.3 (2016A&A...586A...5M) to 100 ± 10 km/s for a
     yellow hypergiant (2017A&A...597A..99W).
   - For aspherical winds, separate components: EP Aqr used Veq = 1.9 km/s and Vpole = 10.3/10.7 km/s with
     V = Veq + (Vpole - Veq) sin^2(alpha) (2019MNRAS.484.1865H).

4. **Choose the mass-loss method for the data you have** (table below), then derive Mdot.

   | Method | Papers (my count) | Gives | Key assumptions |
   |---|---|---|---|
   | 1D Monte Carlo non-LTE RT on CO, grid + chi2 or manual fit | 2: 2017A&A...597A..99W (chi2 grid), 2016A&A...586A...5M (manual fit to SD spectra) | Mdot, v_exp, T(r) | constant isotropic Mdot, 1/r^2 density, CO/H2 |
   | Chemistry model gives atomic C profiles, fed to Monte Carlo non-LTE RT (mcp) at an adopted Mdot; CO lines only as a check | 1: 2018A&A...612L..11S | CI abundance and emission, not Mdot | adopted Mdot 2.5e-7 Msun/yr, spherical uniform expansion, ISRF only external UV |
   | LVG + ray tracing, abundance profiles fitted at fixed Mdot | 1: 2019A&A...629A.146V | X(r), photodissociation radii | spherical, H2-only collisions |
   | Integrate a fitted 3D density model (SHAPE/SHAPEMOL or own code) | 3: 2017A&A...605A..28D, 2016A&A...593A..92B, 2017A&A...597L...5B | mass, momentum, average Mdot over the kinematic age | LVG, mean particle mass |
   | De-projection of temperature-corrected cubes into dM/dOmega | 1: 2019MNRAS.484.1865H | Mdot by direction | velocity law, CO/H |
   | Optically thin CO mass formula over a velocity range | 1: 2020A&A...633A..13D | mass and Mdot of an eruption | thin, thermalised, Tex |
   | Analytic optical depth (12CO/13CO ratio or absorption) | 2: 2017ApJ...835L..13S, 2017ApJ...841..110S | lower limits on Mdot | velocity law, abundance |
   | Optically thin dust continuum | 2: 2018A&A...615A..28D, 2015A&A...573L...1O | dust mass, dust Mdot | kappa, T_d, drift or dust velocity |
   | Free-free flux, Wright & Barlow | 2: 2018A&A...617A.137F, 2019A&A...632A..38A | ionized Mdot (really Mdot f_cl^0.5) | Te, mu, Z, gamma, v_inf, smooth wind |
   | Free-free flux with the Dougherty et al. emission model, line-width velocity | 1: 2017MNRAS.464L..75F (Wd1-9) | ionized Mdot | spherical, d = 5 kpc, stellar parameters from Dougherty et al. 2010 |
   | Spherical Panagia & Felli wind, used as the comparison case | 1: 2017ApJ...841..130A | spherical-wind Mdot | spherical, constant velocity |
   | Collimated ionized wind (Reynolds 1986) | 1: 2017ApJ...841..130A | Mdot for a jet-like wind | epsilon from spectral index, inclination |

   - Constant-Mdot density (general practice): n_H2(r) = Mdot / (4 pi r^2 v(r) mu_H2 m_H), where mu_H2 m_H is the
     gas mass per H2 molecule including helium (about 2.8 m_H for a solar He fraction; use 2 m_H only for a pure-H2
     convention, and state which). It is a strict 1/r^2 law only where v(r) is constant. Papers assumed constant
     Mdot with a 1/r^2 density (2016A&A...586A...5M, 2017A&A...597A..99W) or constant expansion velocity
     (2018A&A...612L..11S, 2019A&A...629A.146V, 2024A&A...686A.274V); R Scl's model accelerates from 3 to
     14.3 km/s (2016A&A...586A...5M), so its density falls faster than 1/r^2 in the inner wind.
   - Free-free (general practice, Wright & Barlow form): Mdot [Msun/yr] = 0.095 mu v_inf S_nu^(3/4) d^(3/2) /
     (Z gamma^(1/2) g_ff^(1/2) nu^(1/2)), with v_inf in km/s, S_nu in Jy, d in kpc, nu in Hz; it assumes a
     spherical, isothermal, fully ionized wind at constant v_inf. Westerlund 1 papers used Te = 0.5 Teff and a
     smooth wind (f_cl = 1) (2018A&A...617A.137F, 2019A&A...632A..38A), so the result is really Mdot f_cl^(1/2).
   - Dust (general practice): M_d = S_nu d^2 / (kappa_nu B_nu(T_d)), where S_nu is the dust-only flux (stellar
     photosphere removed, as 2018A&A...615A..28D did by subtracting a beam-convolved point source), kappa_nu is the
     opacity per unit dust mass, and T_d is one effective temperature. It needs optically thin emission AND a
     stated temperature assumption: a single T_d stands in for a temperature distribution, so either give the
     range (2018A&A...615A..28D used 200-650 K for IK Tau and 400-1530 K for R Dor) or integrate over T_d(r). Then dust
     Mdot = M_d / t_cross, with t_cross from the shell size over the dust velocity (2015A&A...573L...1O, 8 arcsec,
     V_d about 60 km/s) or from a momentum-equation solution with drift velocity capped at 20 km/s
     (2018A&A...615A..28D).

5. **Model shells, arcs and episodic mass loss.**
   - Detached shell. Pack: convolve the best-fit shell model with the single-dish beams, subtract it from the
     single-dish spectra, and model the residual with a constant-Mdot RT model, which stayed degenerate
     (2016A&A...586A...5M). Card details for the shell fit itself (2016A&A...586A...5M card, section 3.2, verbatim
     quotes): shell emission extracted from a ring of ±3 arcsec centred on the shell, assuming a shell radius of
     19.5 arcsec and 14.3 km/s, from images smoothed to 4 arcsec and 1.5 km/s; a 1D Monte Carlo RT grid over shell
     masses 2.5e-3 to 4.75e-3 Msun in steps of 0.25e-3 and temperatures 10-290 K in steps of 20 K, best fit by
     minimising chi2 with an assumed 20% observational uncertainty; shell width 2 arcsec taken from dust-scattered
     light images.
   - Azimuthal averages of SiO, SiS and CS show shells in IRC+10216; the card quotes a kinematical age of about
     365 yr for a shell at about 420 R* (2019A&A...629A.146V, card numeric results). The pack itself gives only the
     abundance profiles and disappearance radii for this paper.
   - Kinematic age t = r / v_exp, for example 455 yr at R_out for 23 km/s (2017ApJ...835L..13S); 730 yr torus and
     160 yr outflow (2017A&A...605A..28D); about 1000 yr for the IW Car outflow (2017A&A...597L...5B). Use
     deprojected radii and velocities: the IRAS 16342-3814 blob ages are uncertain because a uniform radial velocity
     was assumed (2017ApJ...835L..13S), and IW Car's inclination is poorly determined (2017A&A...597L...5B). r/v is
     a ballistic age; for an accelerating wind integrate dr/v(r) instead, and carry the inclination and distance
     uncertainty into the age.
   - Spirals and companions: compare with hydrodynamic models (PHANTOM SPH, orbits checked with REBOUND over 1000
     outer periods; 2024A&A...691A..57M) or with a 3D model passed through an ALMA simulator. 2017A&A...605A..28D
     used the CASA SIMOBSERVE task to simulate visibilities of the observation from the model brightness
     distribution (card, section 4.3); 2020A&A...633A..13D used SIMALMA, settings not stated (pack). Passing the
     model through the simulator with your own uv coverage is our recommendation.

6. **Derive masses, momenta and lifetimes.**
   - Integrate the fitted density with a mean particle mass: 3e-24 g (2017A&A...605A..28D), 2.35 amu
     (2024A&A...686A.274V), mu = 2.38 (2024A&A...691A..57M).
   - Post-AGB disks: disk lifetime = disk mass / outflow Mdot, about 8000 yr in both pack cases
     (2016A&A...593A..92B, 2017A&A...597L...5B).
   - Compare the outflow momentum with the radiation momentum: 2017A&A...605A..28D compares to L/c. Since P (g cm/s)
     and L/c (g cm/s^2) differ in units, do it as P versus L t/c over the kinematic age t, or as the force P/t versus
     L/c, or as the driving time P c / L (general practice).

7. **State uncertainties honestly** (see Pitfalls and Verification). Report Mdot with its distance, abundance and
   velocity scalings written out, as 2017MNRAS.464L..75F ((d/5 kpc)^1.5), 2015A&A...573L...1O ((V_d/60 km/s)) and
   2017ApJ...835L..13S ((V_AGB/23 km/s)) do.

## Parameter defaults and ranges

All from the pack; counts are my own count of pack lines. Longer table: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Density law | 1/r^2 (constant Mdot) | constant or from fitted 3D model | 5 | 2016A&A...586A...5M, 2017A&A...597A..99W, 2019A&A...629A.146V |
| Turbulent velocity | 1 km/s | 1 km/s | 3 | 2017A&A...597A..99W, 2019A&A...629A.146V, 2024A&A...686A.274V |
| CO/H2 (12CO) | no single default | 1e-4 to 5e-4 (CO/H 2.5e-4) | 4 | 1e-4 2017A&A...597A..99W; 4.3e-4 2016A&A...586A...5M (card); 5e-4 2018A&A...612L..11S; CO/H 2.5e-4 2019MNRAS.484.1865H |
| Gas-to-dust | 300 for C-rich | 40 to 300 | 3 | 300 2019A&A...629A.146V, 2024A&A...686A.274V (CW Leo); 167 R Leo 2024A&A...686A.274V; 40 YHG 2017A&A...597A..99W |
| Dust opacity type | amorphous carbon (C-rich), silicate (O-rich) | kappa about 7 cm^2/g at 345 GHz | 2 | 2024A&A...686A.274V, 2018A&A...615A..28D |
| Gas temperature law | power law in r | exponent -0.6 to -0.85 | 2 | alpha 0.6 2020ApJ...899..152H; beta -0.85 2016A&A...586A...5M |
| Velocity law | constant v_exp | beta law, or 3 to 14.3 km/s acceleration | 5 | constant 2019A&A...629A.146V, 2018A&A...612L..11S; beta law 2020ApJ...899..152H; gradual 2016A&A...586A...5M |
| CO energy levels in RT | J up to 40, v=0 and v=1 | | 1 | 2017A&A...597A..99W |
| RT radial grid | 100 log-spaced shells | | 1 | 2019A&A...629A.146V |
| Dust temperature | one assumed T (VY CMa) or a stated range (AGB) | 200 K to 1530 K | 2 | single 200 K 2015A&A...573L...1O; ranges 200-650 K (IK Tau) and 400-1530 K (R Dor) 2018A&A...615A..28D |
| Free-free Te | 0.5 Teff | 10,000 K for cool stars | 2 | 2018A&A...617A.137F, 2019A&A...632A..38A |
| Free-free mu | 1.4 OB | 1.4 to 4.7 by type | 2 | 2018A&A...617A.137F, 2019A&A...632A..38A |
| Clumping f_cl | 1 (smooth) | | 2 | 2018A&A...617A.137F, 2019A&A...632A..38A |
| Gas Mdot derived or adopted for observed AGB/RSG/YHG winds | | 0.9e-7 to 8e-5 Msun/yr | 8 | derived: 0.9e-7 2019MNRAS.484.1865H, 7.7e-7 2017A&A...605A..28D, 3.3e-6 (lower limit) 2020A&A...633A..13D, 3.5e-6 and 1.6e-5 2016A&A...586A...5M, (8 ± 1.5) × 10^-5 2017A&A...597A..99W; adopted as model input: 1.1e-7 2020ApJ...899..152H, 2.5e-7 2018A&A...612L..11S, 2.7e-5 2019A&A...629A.146V |
| Gas Mdot used outside observed-wind fits | | 1.2e-7 to 1.1e-6 Msun/yr | 2 | 1.1e-6 SPH input 2024A&A...691A..57M; expected 1.2-3.5e-7 from evolution 2015MNRAS.453.4324M (not counted in the row above) |
| Ionized Mdot (hot massive stars), smooth wind, d = 5 kpc for Wd1 | | (6.3 ± 1.2) × 10^-6 to 6.4e-5 Msun/yr | 4 | WR S Mdot f_cl^0.5 (6.3 ± 1.2) × 10^-6 2019A&A...632A..38A; RMC 127 spherical (2.1 ± 0.4) × 10^-5 2017ApJ...841..130A; Wd1 WR mean (3.6 ± 0.4) × 10^-5 excluding WR S and Wd1-13, WC mean (4.2 ± 0.7) × 10^-5 2018A&A...617A.137F; WR mean 4.61e-5 2019A&A...632A..38A; Wd1-9 6.4e-5 (d/5 kpc)^1.5 2017MNRAS.464L..75F |

## Software

Pack aggregate: each distinct software string is counted once. Two of those strings ("monte carlo radiative
transfer code (schöier & olofsson 2001)" and "monte carlo cse code (bernes 1979; schoier & olofsson 2001)") name
the same code family, used by 2 papers (2016A&A...586A...5M, 2017A&A...597A..99W); every other package appears in
one paper. So no code is a standard here. Card details add a few more.

| Purpose | Software | Papers |
|---|---|---|
| 1D non-LTE CO radiative transfer | Monte Carlo code of Schoier & Olofsson 2001 (Bernes 1979) | 2 papers: 2016A&A...586A...5M, 2017A&A...597A..99W (two aggregate strings, one each) |
| 1D non-LTE RT with chemistry input | mcp, plus a UCL_CHEM-type CSE chemical model | 2018A&A...612L..11S |
| LVG + ray tracing for SiO/SiS/CS | code of Agundez et al. 2012 | 2019A&A...629A.146V |
| 3D morpho-kinematic + non-LTE RT | SHAPE + SHAPEMOL (the card quotes SHAPEMOL as "publicly available"; SHAPE model files not released) | 2017A&A...605A..28D (card, sections 1 and 4.3) |
| 3D RT and line polarisation | LIME 1.9.5 + PORTAL | 2024A&A...686A.274V |
| Envelope ODE (density from continuity) | SciPy `odeint` | 2020ApJ...899..152H |
| Binary/triple wind hydrodynamics | PHANTOM (SPH), REBOUND (orbit stability) | 2024A&A...691A..57M |
| Expected Mdot from stellar evolution | MESA | 2015MNRAS.453.4324M |
| ALMA + single-dish merging | GILDAS UVSHORT; CASA `feather`; CASA `imsmooth` for comparison | 2019A&A...629A.146V, 2017A&A...605A..28D, 2016A&A...586A...5M (cards) |
| Calibration, imaging, continuum subtraction | CASA (version given as 5.7.2 in 2024A&A...686A.274V and 4.1 in 2016A&A...586A...5M, per their cards; unstated in 3 papers per the pack aggregate) | 2024A&A...686A.274V, 2018A&A...615A..28D, 2017A&A...597A..99W, 2016A&A...586A...5M (cards) |

Several model codes were not released or not named (2016A&A...593A..92B, 2017A&A...597L...5B, 2017ApJ...835L..13S).

## Pitfalls

- **Resolved-out flux biases everything downstream** (step 1). Models fitted to filtered maps overpredict extended
  emission (2016A&A...593A..92B, 2017A&A...597L...5B); dust masses from filtered maps are low
  (2015A&A...573L...1O, 2018A&A...615A..28D); polarisation fractions go up by 2-3x (2024A&A...686A.274V).
- **Degeneracy.** Mdot, half-abundance radius, temperature and velocity profiles trade off
  (2016A&A...586A...5M); density versus abundance with only one or two lines per molecule (2019A&A...629A.146V);
  de-projection is under-determined (2019MNRAS.484.1865H); triple-system SPH parameter space is degenerate
  (2024A&A...691A..57M). Fit several transitions at once where you can.
- **Fits by eye.** Several models were not formally fit (2020A&A...633A..13D; 2017A&A...597L...5B per its card;
  2019A&A...629A.146V matched azimuthal averages "on average"). Treat their numbers as indicative.
- **Optical depth.** The thin-CO mass is a lower limit when tau is near 1 (2020A&A...633A..13D); dust in the
  brightest clump may be thick (2015A&A...573L...1O); CO in absorption gives only a lower-limit size
  (2017ApJ...841..110S).
- **Spherical, constant-Mdot templates on non-spherical winds.** The AGB wind model applied to a yellow
  hypergiant gives only an order-of-magnitude Mdot (2017A&A...597A..99W); LVG may not apply in a torus
  (2017A&A...605A..28D); non-spherical shells make recombination-line fits degenerate (2014ApJ...791...95A).
- **Distance.** The distance dependence depends on the estimator, so refit at the new distance or write the
  scaling for the estimator you used (general practice): an optically thin mass scales as d^2, but if the age
  comes from a measured angular size (t proportional to d) the age-averaged Mdot scales as d; a full CO RT fit has
  no simple power law. Free-free Mdot scales as d^1.5 (2017MNRAS.464L..75F). R Scl distance was "very uncertain" (2016A&A...586A...5M). Carry the scaling explicitly.
- **Contamination.** ISM CO along the line of sight must be masked out of the fitted spectrum
  (2017A&A...597A..99W); diffuse cluster emission can be misattributed to stars (2019A&A...632A..38A);
  non-thermal sources must be excluded before free-free Mdot (2018A&A...617A.137F).
- **External UV.** The interstellar or cluster radiation field sets the CO and 13CO photodissociation radius and
  can make CO undetectable (2015MNRAS.453.4324M, 2017ApJ...835L..13S, 2018A&A...612L..11S).
- **Comparing models to data without the instrument.** 2024A&A...691A..57M did not apply an ALMA simulator;
  2017A&A...605A..28D did (SIMOBSERVE, card), which is the safer route.
- **Line polarisation.** Resolved-out CO flux inflates polarisation fractions by 2-3x, and circular polarisation
  of extended lines is dominated by beam effects, so it cannot test anisotropic resonant scattering
  (2024A&A...686A.274V). Check instrumental and beam effects before interpreting Stokes V.
- **Free-free Mdot assumptions.** Radio-to-ALMA clumping ratios assume a constant Mdot between the epochs and
  frequencies compared (2019A&A...632A..38A); fluxes need matching beams and no nebular contamination (RMC 127:
  differing beams and nebular contamination, 2017ApJ...841..130A); the Westerlund 1 census assumes the mm flux is
  not affected by binarity (2018A&A...617A.137F).
- **Not stated in cards** (pack aggregate): CASA version, line-free channels, image and cell size, self-cal
  intervals, TP combination method, model grids. If you reuse a paper's numbers, you cannot rebuild their images.

## Verification checks

What the papers did:
- Compare the integrated model with single-dish spectra of several transitions: IRAM 30 m (2019A&A...629A.146V);
  JCMT CO 2-1, 3-2, 4-3 (2018A&A...612L..11S); emitting sizes against ALMA and single-dish limits
  (2016A&A...586A...5M).
- Compare Mdot with independent literature values or methods: free-free versus non-LTE models, within a factor
  of about 2 (2018A&A...617A.137F); radio versus ALMA flux for clumping, valid only under constant Mdot and with
  comparable beams and no diffuse or nebular contamination (2019A&A...632A..38A, 2017ApJ...841..130A); CO model densities
  against other CO Mdot models (2020ApJ...899..152H); collimated versus spherical wind, which differ by a factor
  of 2 or more (2017ApJ...841..130A).
- Vary parameters until the model is incompatible with data: about 50% on density and abundance, 30% on
  temperature (2016A&A...593A..92B).
- Quote chi2 errors from the 1 sigma ellipse (2017A&A...597A..99W).
- Check a dynamical prediction against the measured expansion velocity (2014ApJ...791...95A: 19 km/s).
- Test sensitivity to a velocity-law choice (2019MNRAS.484.1865H: Veq versus escape velocity, "very small"
  difference) and to IR pumping (2019A&A...629A.146V).
- Check astrometry against Gaia (2018A&A...616L...3B) and orbital stability with N-body integration
  (2024A&A...691A..57M).

What a careful referee adds:
- A missing-flux number for every map used in a fit (ALMA smoothed to the single-dish beam versus single-dish).
- Model images passed through `simobserve`/`tclean` with the real uv coverage before comparing to data.
- Mdot quoted with explicit scalings for d, v_exp, CO/H2 (or Te, mu, f_cl for free-free), and an optical-depth
  statement saying whether it is a lower limit.
- At least two transitions (or a 12CO/13CO pair) before claiming a temperature or Mdot, given the degeneracies
  above.

## Source cards

Full list with titles: `references/sources.md`. Most informative for methods:

- 2016A&A...586A...5M: detached shell RT grid, single-dish shell subtraction, missing-flux comparison
- 2017A&A...597A..99W: Monte Carlo CO RT grid with chi2 errors, ISM masking, YHG caveat
- 2019A&A...629A.146V: UVSHORT merge, LVG abundance profiles, shells in azimuthal averages
- 2017A&A...605A..28D: ACA + TP feather, SHAPEMOL 3D model, simobserve, outflow mass and momentum
- 2020A&A...633A..13D: optically thin CO eruption mass, lower-limit reasoning
- 2019MNRAS.484.1865H: de-projection of an aspherical wind into dM/dOmega
- 2018A&A...615A..28D: dust mass and dust Mdot from 345 GHz continuum
- 2015A&A...573L...1O: RSG dust mass-loss from resolved-out flux
- 2018A&A...612L..11S: chemistry plus non-LTE RT for CI
- 2016A&A...593A..92B: post-AGB disk and outflow, parameter-variation uncertainties
- 2017A&A...597L...5B: post-AGB disk lifetime, filtered flux
- 2017ApJ...835L..13S: 12CO/13CO Mdot lower limit, kinematic ages
- 2017ApJ...841..110S: analytic optical-depth Mdot with radial dependence
- 2024A&A...686A.274V: line polarisation in CSEs, LIME + PORTAL
- 2024A&A...691A..57M: SPH triple-system wind shaping
- 2018A&A...617A.137F: free-free Mdot census with Te, mu, Z, gamma choices
- 2019A&A...632A..38A: radio versus ALMA free-free, clumping
- 2017ApJ...841..130A: collimated versus spherical ionized wind Mdot
