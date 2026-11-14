# Per-paper parameters for `evolved-star-envelopes`

Every value below is from the `evolved-star-envelopes` evidence pack (aggregates or excerpts), or from the
verified methods card of the same paper where marked "(card)". Values are what each paper adopted or found, not
recommendations. Off-topic paper 2020ApJ...892...52L is left out.

## Cool winds: AGB, RSG, yellow hypergiant

| Paper | Star | Method | Adopted inputs | Result |
|---|---|---|---|---|
| 2016A&A...586A...5M | R Scl (C-rich AGB, detached shell) | 1D Monte Carlo RT (Schoier & Olofsson 2001), shell grid + chi2; SD residual by hand | a = 2.5; T_kin power law beta = -0.85; R0 = 3 R*; v from 3 to 14.3 km/s; blackbody Teff 2300 K, L 5200 Lsun; f(12CO) = 4.3e-4 (card); shell radius 19.5" and width 2" from dust-scattered light, 20% assumed obs uncertainty in the shell chi2 (card, section 3.2) | post-pulse Mdot 1.6e-5 Msun/yr (half-abundance radius 7.2"); recent Mdot 3.5e-6 Msun/yr |
| 2017A&A...597A..99W | IRAS 17163-3907 (YHG) | Monte Carlo CSE RT grid, chi2 on CO spectrum excluding ISM and spur | CO/H2 = 1e-4; turbulence 1 km/s; gas-to-dust 40; d = 4 kpc; CO levels to J = 40, v = 0 and 1 | v_exp 100 ± 10 km/s; Mdot (8 ± 1.5) × 10^-5 Msun/yr; wind gas mass at least 0.04 Msun |
| 2019A&A...629A.146V | IRC+10216 (C-rich AGB) | LVG + ray tracing, 100 log shells, abundance profiles adjusted by hand | d = 123 pc; R* = 4e13 cm; T* = 2330 K; Mdot = 2.7e-5 Msun/yr (input); v_exp 5/11/14.5 km/s; turbulence 1 km/s; gas-to-dust 300; H2-only collisions | SiO about 1e-7; CS about 1e-6 falling to 5e-7 at 100-300 R*; SiS 1-2e-6 to 70-100 R*; disappearance radii SiS 600, SiO 700-800, CS 1000 R* |
| 2019MNRAS.484.1865H | EP Aqr (O-rich AGB) | de-projection of temperature-corrected cubes, dM/dOmega | Veq = 1.9 km/s; Vpole = 10.3 (blue) / 10.7 (red) km/s; CO/H about 2.5e-4 | Mdot 0.9e-7 Msun/yr (no absorption) |
| 2020A&A...633A..13D | pi1 Gru (S-type AGB) | optically thin CO 3-2 mass formula (Olofsson & Nyman), intensity over high-velocity range x 2 | D = 160 pc; f = 6.5e-4; aperture efficiency 0.76; Tex = 15 K | eruption mass 4.3e-5 Msun; Mdot 3.3e-6 Msun/yr (lower limit) |
| 2017A&A...605A..28D | pi1 Gru | integrate fitted 3D density (SHAPE + SHAPEMOL, card) | mean particle mass 3e-24 g | torus-phase Mdot 7.7e-7 Msun/yr; outflow mass 7.3e-4 Msun; momentum 9.6e37 g cm/s; ages 730 yr (torus), 160 yr (outflow) |
| 2020ApJ...899..152H | R Leo (O-rich AGB; CARMA) | power-law T, beta-law v, continuity ODE (SciPy) | R* = 1.4 AU; T* = 1800 K; Rc = 10.7 AU; v_inf = 8.5 km/s; Mdot = 1.1e-7 Msun/yr; beta = 0-5; alpha = 0.6 | density range consistent with literature CO models |
| 2018A&A...612L..11S | omi Cet (O-rich AGB) | chemistry model then Monte Carlo non-LTE RT (mcp); CO lines only as a check | Mdot 2.5e-7 Msun/yr (adopted, not fitted); v_exp 2.5 km/s; 12CO/H2 = 5e-4; 13CO/H2 = 5e-5; ISRF only external UV | peak CI abundance 2.4e-5 |
| 2024A&A...686A.274V | CW Leo, R Leo | LIME 1.9.5 + PORTAL polarised RT | turbulence 1 km/s; mean particle mass 2.35 amu; gas-to-dust 300 (CW Leo), 167 (R Leo); amorphous carbon or silicate opacity; CW Leo dipole inclined 45 deg, PA 125 deg | polarisation morphology qualitatively matched |
| 2024A&A...691A..57M | R Aql (triple-system models) | PHANTOM SPH, REBOUND stability | M1 = 1.6, M2 = 0.4 Msun; ai = 5 au; ao = 35 au; Mdot = 1.1e-6 Msun/yr; T1 = 2800 K; v_ini 8 or 15 km/s; M3 = 0.1/0.6/1.2 Msun; gamma = 1.2; mu = 2.38 | flattening ratio about 0.5 for v08 triples; inner period 7.91 yr |
| 2015MNRAS.453.4324M | 47 Tuc AGB stars | expected Mdot from Reimers/SC05 + MESA budget; 3D Monte Carlo cluster ISRF | 0.53 Msun final WD mass; one star at RGB tip per 80000 yr | expected Mdot 1.2-3.5e-7 Msun/yr; CO non-detection explained by dissociation |
| 2018A&A...615A..28D | IK Tau, R Dor (AGB) | optically thin dust after subtracting a stellar point source | kappa about 7 cm^2/g; T_d 200-650 K (IK Tau), 400-1530 K (R Dor); drift velocity below 20 km/s | dust mass 3.7e-7 and 2e-8 Msun; dust Mdot about 1e-8 and 5e-9 Msun/yr; factor 5 uncertainty |
| 2015A&A...573L...1O | VY CMa (RSG) | dust mass of resolved-out emission over 8" shell / timescale | V_d about 60 km/s; T = 200 K | dust Mdot 5e-6 (V_d/60 km/s) Msun/yr |
| 2018A&A...616L...3B | R Aqr (symbiotic) | uniform disk fitted in uv plane; line centroids | | 15 mas disk; position ±3 mas, Gaia-consistent |

## Post-AGB and pre-planetary nebulae

| Paper | Object | Method | Adopted inputs | Result |
|---|---|---|---|---|
| 2016A&A...593A..92B | Red Rectangle | fitted disk + outflow model, parameters varied to incompatibility | outflow gas comes from disk; constant Mdot | disk 1.3e-2 Msun (about 50%); outflow 1.2e-3 Msun; lifetime about 8000 yr |
| 2017A&A...597L...5B | IW Car | fitted model, kinematic time and Mdot | | outflow age about 1000 yr; disk lifetime about 8000 yr |
| 2017ApJ...835L..13S | IRAS 16342-3814 | 12CO/13CO in 26 deg wedges, optical depth, Tex | 13CO photodissociated beyond R_out | Mdot above 3.5e-4 (V_AGB/23 km/s) Msun/yr; age 455 yr |
| 2017ApJ...841..110S | Boomerang Nebula | analytic tau(1-0) with Mdot proportional to V^a, V linear in r | V0 = 164 km/s; R0 = 80"; r_in = 6"; f_CO = 1.3e-3; D = 1.5 kpc | Mdot at least 2.1e-3 Msun/yr at 80" (a = 0); cold mass at least 3.3 Msun; a 0.9-2.2 |

## Hot massive-star ionized winds

| Paper | Object | Method | Adopted inputs | Result |
|---|---|---|---|---|
| 2018A&A...617A.137F | Westerlund 1 (WR, OB, BHG) | Wright & Barlow with Gaunt factor, f_cl = 1 | Te = 0.5 Teff; d = 5 kpc; mu = 1.4, Z = 1, gamma = 1 (OB); mu = 4.0 (WN6 or earlier), 2.0 (later WN), 4.7 (WC8/9); mu = 1.6, gamma = 0.8, Z = 0.9 (BHG) | mean WR Mdot (3.6 ± 0.4) × 10^-5 Msun/yr excluding WR S and Wd1-13; WC mean (4.2 ± 0.7) × 10^-5 Msun/yr; LBV log Mdot about -4.6 |
| 2019A&A...632A..38A | Westerlund 1 (ATCA vs ALMA) | Wright & Barlow; clumping from radio/ALMA ratio | d = 5 kpc; Te = 0.5 Teff (hot), 10,000 K (cool); mu 1.4/2.0/4/4.7 | mean WR Mdot 4.61e-5 Msun/yr; WR S Mdot f_cl^0.5 (6.3 ± 1.2) × 10^-6 Msun/yr; clumping ratios assume constant Mdot |
| 2017MNRAS.464L..75F | Wd1-9 (sgB[e]) | line-width velocity with mm and radio fluxes, Dougherty et al. model | v about 100 km/s; d = 5 kpc; spherical | Mdot about 6.4e-5 (d/5 kpc)^1.5 Msun/yr |
| 2017ApJ...841..130A | RMC 127 (LBV) | Reynolds 1986 collimated wind; Panagia & Felli spherical for comparison | D = 48.5 kpc; T = 6420 K; v = 148 km/s; varphi = 75 deg; x0 = 1; mu = 1; theta0 = 0.5 rad; nu_max = 1e13 Hz | epsilon 1.34 (model 1); spherical Mdot (2.1 ± 0.4) × 10^-5 Msun/yr; collimated a factor 2 or more lower |
| 2014ApJ...791...95A | eta Car | Weaver et al. wind-blown shell then snow-plow | t2 = 71 yr; ambient density 1e5 and 1e6 cm^-3 | predicted v2 = 19 km/s matches shell expansion |
