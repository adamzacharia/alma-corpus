# Envelope kinematics: per-paper settings and results

All values are from the `envelope-kinematics-pv` evidence pack (verified quotes in the methods cards). Only
envelope, core and streamer papers are listed. "n.s." = not stated in the pack (it may be in the paper).
Inclinations are as the paper states them; 2019ApJ...873...73Z uses i = 0 for edge-on, the others i = 90 deg.

## Rotation-profile (PV data point) fits

| Paper | Source | Line(s) / points | Fit | Result |
|---|---|---|---|---|
| 2017ApJ...849...56A | L1527 IRS | mean positions of pixels >5 sigma; Vsys 5.8 km/s; d 140 pc; i 85 deg | chi2 double vs single power law in log R - log V | p_in 0.50 +/- 0.05, p_out 1.22 +/- 0.04, R_b 56 +/- 2 AU (corrected ~74 AU), M* ~0.45 Msun; reduced chi2 1.6 vs 4.0 |
| 2015ApJ...812...27A | TMC-1A | mean positions >6 sigma on PA 73 deg cut; no points at abs(dV) < 1.2 km/s; Vsys 6.4 km/s | chi2, Gaussian errors in log R, rectangular in log V, MC dispersal | p_in 0.54 +/- 0.14, p_out 0.85 +/- 0.04, R_b 67 AU apparent (~90 AU corrected), M* 0.68 Msun; reduced chi2 1.6 vs 2.0 |
| 2014ApJ...796..131O | L1527 IRS | C18O points within 100 AU; Vsys 5.9 km/s | least squares, single and broken power law | break 53.7 +/- 0.4 AU, inner -0.41 +/- 0.24, outer -1.16 +/- 0.13, M ~0.3 Msun |
| 2020ApJ...893...51S | L1489 IRS | Gaussian fits per channel (inner, r<100 au) and per position (outer) | chi2, 10000 resamplings, 3 sigma errors | inner p 0.50 +/- 0.11, M* 1.64 +/- 0.12 Msun; outer-disk break 624 +/- 62 au, p_in 0.47, p_out 1.07 (warped-disk system) |
| 2017ApJ...834..178Y | Lupus 3 MMS, IRAS 15398, IRAS 16253 | C18O peak positions per channel; R0 = 1 arcsec; low-velocity channels excluded (range n.s.); Vsys free | power law, 1000 Monte Carlo repeats | Lupus 3 MMS index -0.57 +/- 0.03; IRAS 15398 index -1.0 +/- 0.06 |
| 2025ApJ...993..120H | IRAS 04169+2702 | ridge and edge on 12CO, 13CO, C18O; Vsys 6.9 km/s; i 43 deg; 5 sigma (12CO, C18O), 6 sigma (13CO) | single power law; p fixed 0.5 for 12CO mass | mass = mean of ridge and edge |
| 2024A&A...690A..46S | eDisk Class 0 | Vsys 2.84 km/s fixed after first fit | Keplerian inside break radius | n.s. beyond these |
| 2018ApJ...859..111H | EX Lup | channel-map astrometry with channels SNR > 5 (not PV mean positions); PV along PA 78 deg | chi2 Keplerian fit to red-side centroids, M* 0.5 Msun assumed | i 38 +/- 4 deg |
| 2013A&A...560A.103M | VLA1623A | M* 0.2 Msun, PA 35 deg, vlsr 4.0 km/s fixed; d 120 pc | free vwidth 0.1-1.0 km/s, i 0-90 deg, Rout 100-200 AU | cannot separate infall plus Keplerian from pure Keplerian in outer 30 AU |

## Infalling-rotating envelope, CB and Ulrich models

| Paper | Model | Fixed / assumed | Free or explored | Fit and checks |
|---|---|---|---|---|
| 2015ApJ...812...59O | ballistic envelope plus outflow (L1527, CS) | density r^-1.5, outer radius 1000 AU, line width 0.5 km/s, beam 0.5 arcsec, optically thin, Gaussian profile | M = 0.18 Msun, r_CB = 100 AU; R0 = z0 = 1 arcsec | simple model; rms statistics not meaningful (authors) |
| 2016ApJ...824...88O | IRE plus Keplerian (IRAS 16293 A) | density r^-1.5, constant abundance, optically thin, i 60 deg | r_CB 40-60 AU, M 0.75 Msun, outer radius 180 AU | n.s. |
| 2017ApJ...837..174O | IRE (L483) | envelope thickness 30 au, density r^-1.5; i 80 deg, PA 15 deg | M, r_CB, i | n.s. |
| 2019ApJ...873...73Z | IRE plus Keplerian (G339.88-1.26) | h(r) = 0.2 r; envelope r^-1.5; disk r^-2.5; r_out/d = 0.8 arcsec; optically thin; disk mass neglected; i = 0 is edge-on | n.s. | n.s. |
| 2024ApJ...970...28O | IRE/Keplerian (B335, CH3OH, HCOOH) | height 20 au, R_out 24 au (CH3OH), 10 au (HCOOH), PA 5 deg | i 70-90 deg, M* 0.02-0.08 Msun, r_CB 2-9 au | n.s. |
| 2017ApJ...843...27L | flared envelope with parabolic boundaries (HH 212) | Vsys 1.7 km/s; boundaries a = 0.05, b = 0.45 and a = -0.05, b = -0.6 | l and M; r_c = l^2/GM, r_0 = l^2/2GM | fit weighted to blueshifted side (redshifted self-absorption); dust-thick midplane |
| 2014ApJ...786..114L | pseudodisk plus disk (HH 212, HCO+) | disk outer radius 0.3 arcsec (120 AU), half thickness 0.1 arcsec; envelope outer radius 5 arcsec; LTE; Beckwith opacity beta = 1 | T0, n0, vr0, vphi0, m, q, x(HCO+) (7 free) | n.s. |
| 2019ApJ...871..100H | rotating infalling envelope (IRAS 16253) | X_CO 5e-4, X_CO/X_C18O 560 (so X_C18O ~8.9e-7), T0 70 K, T ~ r^-0.4 | rho0, p, theta_flared, V_rot,0, V_infall,0, F_C18O | C18O fit at abs(V-Vlsr) < 1.6 km/s, CO above (tracer split, not an exclusion) |
| 2017ApJ...834..178Y | free fall plus conserved j plus Keplerian disk, LTE C18O | q fixed -0.4; zero density within 80 deg of polar axis | n0, T0, M*, j; density index in {-1.5, -2, -2.5} | chi2; errors from reduced chi2 min + 1 |
| 2015ApJ...812...27A | flattened envelope (to 900 AU) plus disk, V_r = alpha V_ff | surface density beyond 200 AU reduced by 2 | v_out, R_kep, alpha, i: best (0.85, 100 AU, 0.3, 65 deg) | by eye; spherical envelope models worse; simobserve filtering |
| 2017ApJ...849...56A | disk plus envelope, C18O radiative transfer | T 44 K, mu 2.37 m_H, vertically isothermal; C18O 4e-8 (alternative 5e-7 at 80-88 AU, 2.8e-8 elsewhere) | alpha ~0.3 inferred from isothermal shock condition, not fit | moment-0 residuals |
| 2014ApJ...796..131O | envelope plus SO ring plus Keplerian disk | edge-on; SO ring 70-120 AU, 32 K, abundance 9e-7; disk 54 AU, 0.3 Msun; j = 6.1e-4 km/s pc | infall velocity (free fall vs reduced) | manual; CASA simulator; robust to 0.2 Msun |
| 2020A&A...634L..12D | Ulrich rotating infall shell (DG Tau B) | M 1.1 Msun | Rd 700 au, theta0 70 deg; Rd and theta0 varied | no combination reproduces the wide redshifted component |
| 2019A&A...623A..96Y | collisionless particle envelope (HL Tau) | M* 1.8 Msun, centrifugal radius 100 au, i 47 deg, PA 138 deg, envelope 3000 au, r^-1.5, 1e4 yr; T = 15 (r/1000 au)^-0.6 K | evolution time, relative velocity | not unique |
| 2025A&A...693A..76C | Keplerian plus infall toy model fit to CH3CN peak velocities (IRAS 20126+4104) | PA_d 48 deg; Rd 0.3 arcsec = 490 au; kappa_d 0.01 cm2/g | M 12 Msun, i 59 deg, infall ratio A 0.42 (normalization n.s.), Vsys -4.3 km/s | least squares on velocities; C-shape matched qualitatively; proof of concept (authors) |

## Streamers and infall rates

| Paper | Method | Settings | Result |
|---|---|---|---|
| 2024A&A...683A.133G | TIPSY, Mendoza 2009 trajectories, grid over LOS separation, POS speed, POS direction | point-mass gravity only; M*, d, Vsys fixed; line intensity traces density; T 25 K; 13CO 1.45e-6, HCO+ 1e-9, optically thin | S CrA j 791 +/- 218 au km/s, infall time 8301 +/- 1358 yr, Mdot >= 2.5e-8 Msun/yr; HL Tau Mdot >= 4.5e-9 Msun/yr (lower limits, order of magnitude) |
| 2025SciA...11.4512O | massive streamers | i 65 deg, disk PA -55 deg; CB 250 au; T 100 K, kappa 1 cm2/g at 1.3 mm, dust-to-gas 0.01, mu 2.33, d 3.1 kpc; v_ff 6 km/s, l 500 au, alpha 0.1-1 | ALMA1 mass an upper limit under the optically thin approximation (authors); infall neither free-fall nor viscous |
| 2015ApJ...812...27A | Mdot = 2 pi R V_r Sigma | R 100-200 AU | (1.5-3.0)e-6 Msun/yr |
| 2017A&A...603A..10B | spherical infall | r ~80 AU, density ~2.3e9 cm-3 (particle species n.s.), v_in ~7.1 km/s; disk covers ~50% (~2 pi) | n.s. in pack |
| 2018A&A...615A.141B | absorption toward the hot core | radius 1.54 arcsec | infall velocity 5.1 km/s (extraction rule n.s.) |
| 2015ApJ...814...22E | infall from absorption in B335 | T_dust 111 K (mass weighted); opacity 1.48e-2 cm2/g; gas-to-dust 100; constant infall rate, wind mass loss neglected | n.s. in pack |
| 2015ApJ...813L..19J | disk plus infall model (AFGL 4176) | disk 2000 AU, 12 Msun gas, Sigma ~ r^-1.5, i 30 deg, 25 Msun star; Draine dust R_V 5.5 | infall 4.6e-4 Msun/yr |
| 2024ApJ...967...15K | infall in a hot core | distance 2.38 kpc, 1.7 kpc also tested | errors exclude distance uncertainty and density gradients |
