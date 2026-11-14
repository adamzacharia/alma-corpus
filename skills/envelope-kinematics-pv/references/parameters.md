# Envelope kinematics: per-paper settings and results

All values are from the rebuilt `envelope-kinematics-pv` evidence pack (493 papers; verified quotes in the methods
cards). Only envelope, core and streamer papers are listed. "n.s." = not stated in the pack (it may be in the
paper). Inclinations are as the paper states them: 2019ApJ...873...73Z uses i = 0 for edge-on, 2020ApJ...904..181L
and 2025SciA...11.6953M use i = 0 for face-on, 2024ApJ...966..192S measures i from the outflow axis; the others
quote edge-on near 90 deg.

## Rotation-profile (PV data point) fits

| Paper | Source | Points / settings | Fit | Result |
|---|---|---|---|---|
| 2017ApJ...849...56A | L1527 IRS | mean positions of pixels >5 sigma; Vsys 5.8 km/s; d 140 pc; i 85 deg | chi2 double vs single power law in log R - log V | p_in 0.50 +/- 0.05, p_out 1.22 +/- 0.04, R_b 56 +/- 2 AU (corrected ~74 AU), M* ~0.45 Msun; reduced chi2 1.6 vs 4.0 |
| 2015ApJ...812...27A | TMC-1A | mean positions >6 sigma on PA 73 deg cut; no points at abs(dV) < 1.2 km/s; Vsys 6.4 km/s | chi2, Gaussian errors in log R, rectangular in log V, MC dispersal | p_in 0.54 +/- 0.14, p_out 0.85 +/- 0.04, R_b 67 AU apparent (~90 AU corrected), M* 0.68 Msun; reduced chi2 1.6 vs 2.0 |
| 2023ApJ...958...98F | Oph IRS 63 | 13CO, C18O, SO; cut 5 pixels (~0.5 arcsec), PA 149 deg; >5 sigma; filtered channels excluded; d 132 pc; i 47 deg | SLAM ridge and edge, MCMC, averaged | M* 0.5 +/- 0.2 Msun; R_b 265 +/- 9 au (13CO); p_in ~0.6 +/- 0.04; 13CO p_in+dp 1.2 +/- 0.4 (edge 1.6, ridge 0.9); SO edge p_in 0.48, R_b 97 au |
| 2026ApJ..1003..219W | Sgr C O-type protostar | major-axis PV (PA 42 deg); 16 sigma and 9 sigma extraction; R0 1300 au; i 50 deg | power law by ODR, inverse-square error weights | 16 sigma: p 0.49 +/- 0.04, 42.95 Msun; 9 sigma: p 0.81 +/- 0.06, 40.73 Msun |
| 2025ApJ...993..120H | IRAS 04169+2702 | ridge and edge on 12CO, 13CO, C18O; Vsys 6.9 km/s; i 43 deg; 5 sigma (12CO, C18O), 6 sigma (13CO) | power law; p fixed 0.5 for 12CO mass | mass = mean of ridge and edge |
| 2025ApJ...992...18P | eDisk Class 0 | ridge 6 sigma (13CO), 3 sigma (C18O); edge threshold n.s. | ridge/edge | n.s. beyond these |
| 2024ApJ...966...32E | eDisk protobinary | PV along Gaussian-fit PA, width ~1 beam; A to 2 arcsec, B to 1.5 arcsec; opposite side of each disk only | ridge and edge | p ~0.5 Keplerian; ridge and edge bracket the Keplerian mass |
| 2014ApJ...796..131O | L1527 IRS | radii <100 AU (resolved-out scales overestimate rotation); Vsys 5.9 km/s; edge-on 90 deg | n.s. in pack | disk 54 AU, 0.3 Msun; j 6.1e-4 km/s pc |
| 2020ApJ...893...51S | L1489 IRS (warped disk) | inner fit r < 100 au; inner 0.1-200 au PA 69 deg, outer 300-600 au PA 54 deg; i 73 deg | n.s. in pack | M* 1.6 Msun, Mdisk 0.0071 Msun |
| 2017ApJ...834..178Y | Class 0/I protostars | R0 = 1 arcsec; low-velocity channels excluded (range n.s.); PA and i in 5 deg steps | n.s. in pack | n.s. in pack |
| 2022A&A...664A.171V | [BHB2007] 11 | cut PA 140 deg, width 0.5 arcsec; centroids with peak > 5x fit error and SNR > 10; accuracy Theta/(2 SNR) | centroid positions | n.s. in pack |
| 2024A&A...690A..46S | eDisk Class 0 | Vsys 2.84 km/s fixed after first fit | Keplerian inside break radius | n.s. beyond these |
| 2018ApJ...859..111H | EX Lup | channels with SNR > 5 for astrometry (not PV mean positions); M* 0.5 Msun | n.s. in pack | n.s. in pack |
| 2013A&A...560A.103M | VLA1623A | M* 0.2 Msun, PA 35 deg, vlsr 4.0 km/s fixed (vlsr range 3.4-4.0 seen); d 120 pc | free vwidth 0.1-1.0 km/s, i 0-90 deg, Rout 100-200 AU | n.s. in pack |

## Infalling-rotating envelope, CB and Ulrich models

| Paper | Model | Fixed / assumed | Free or explored | Fit and checks |
|---|---|---|---|---|
| 2015ApJ...812...59O | ballistic envelope plus outflow (L1527, CS) | density r^-1.5, outer radius 1000 AU, line width 0.5 km/s, beam 0.5 arcsec, optically thin, Gaussian profile; outflow perpendicular to mid-plane | M = 0.18 Msun, r_CB = 100 AU; R0 = z0 = 1 arcsec | n.s. |
| 2014ApJ...795..152O | IRE (IRAS 15398) | flared 20 deg, outer 240 AU, r^-1.5, line width 0.5 km/s, beam 0.6 arcsec; optically thin; no disk inside CB | infall and rotation 1 km/s | n.s. |
| 2016ApJ...820L..34S | IRE (IRAS 04365+2535) | r^-1.5, constant abundance, optically thin, extension angle 30 deg; outer 350 AU; 0.5 km/s width | n(H2) 3e6-3e8 cm-3, T 30-120 K | n.s. |
| 2016ApJ...824...88O | IRE plus Keplerian (IRAS 16293 A) | r^-1.5, constant abundance, optically thin, i 60 deg | r_CB 40-60 AU, M 0.75 Msun, outer radius 180 AU | n.s. |
| 2017ApJ...837..174O | IRE (L483) | envelope thickness 30 au, r^-1.5; i 80 deg, PA 15 deg | M, r_CB, i | n.s. |
| 2018ApJ...854...96O | envelope model (IRAS 16293 B) | thickness 50 au, outer 300 au, i 5 deg, line width 0.5 km/s, Vsys 2.9 km/s; emissivity ~ density, no RT | n.s. | n.s. |
| 2020ApJ...904..185O | IRE vs Keplerian (IRAS 16293 A) | flared 30 deg, intrinsic FWHM 1 km/s, PA 50 deg; optically thin, no RT | r_CB 50 au; r_CB 5, 10, 20 au vs Keplerian | n.s. |
| 2019ApJ...873...73Z | IRE plus Keplerian (G339.88-1.26) | h(r) = 0.2 r; envelope r^-1.5; disk r^-2.5; r_out/d = 0.8 arcsec; optically thin; disk mass neglected; i = 0 is edge-on | n.s. | n.s. |
| 2024ApJ...970...28O | IRE/Keplerian (B335, CH3OH, HCOOH) | height 20 au, R_out 24 au (CH3OH), 10 au (HCOOH), PA 5 deg | i 70-90 deg, M* 0.02-0.08 Msun, r_CB 2-9 au | n.s. |
| 2025A&A...701A.141L | ballistic envelope plus SO ring | CB 65 au (SO ring); parabolic orbit; negligible flare; v_phi ~ r^-1, free fall scaled down ~1.5; M 0.5 Msun in the model (central mass 0.35 Msun also stated) | velocity ratio adjusted | n.s. |
| 2017ApJ...843...27L | flared envelope with parabolic boundaries (HH 212) | Vsys 1.7 km/s; boundaries a = 0.05, b = 0.45 and a = -0.05, b = -0.6 | l and M; r_c = l^2/GM, r_0 = l^2/2GM | fit weighted to blueshifted side (redshifted self-absorption) |
| 2014ApJ...786..114L | pseudodisk plus disk (HH 212, HCO+) | disk outer 0.3 arcsec (120 AU), half thickness 0.1 arcsec; envelope outer 5 arcsec; LTE; Beckwith opacity beta = 1; free fall, constant j | T0, n0, vr0, vphi0, m, q, x(HCO+) (7 free) | n.s. |
| 2019ApJ...871..100H | rotating infalling envelope (IRAS 16253) | X_CO 5e-4, X_CO/X_C18O 560 (so X_C18O ~8.9e-7), T0 70 K, T ~ r^-0.4 | rho0, p, theta_flared, V_rot,0, V_infall,0, F_C18O | C18O fit at abs(V-Vlsr) < 1.6 km/s, CO above (tracer split) |
| 2017ApJ...834..178Y | free fall plus conserved j, LTE | q fixed -0.4; zero density within 80 deg of polar axis | n.s. in pack | n.s. in pack |
| 2018A&A...615A..58Y | infall plus rotation (B335) | i 87 deg, d 100 pc, T 38 K (r/100 au)^-0.4, polar cavity within 60 deg empty; R0 100 au, outer 700 au; 7.7-8.9 km/s excluded | n(R0), p, Vin(R0); j fixed 3e-5 km/s pc or 0 | n.s. |
| 2015ApJ...812...27A | flattened envelope (to 900 AU) plus disk, V_r = alpha V_ff | surface density beyond 200 AU reduced by 2 | v_out, R_kep, alpha, i: best (0.85, 100 AU, 0.3, 65 deg) | by eye; spherical envelope models worse; simobserve filtering |
| 2017ApJ...849...56A | disk plus envelope, C18O radiative transfer | T 44 K, mu 2.37 m_H, vertically isothermal; C18O 4e-8 (alternative 5e-7 at 80-88 AU, 2.8e-8 elsewhere) | alpha ~0.3 inferred from isothermal shock condition, not fit | moment-0 residuals (9 sigma left for constant abundance) |
| 2020ApJ...904..181L | M1-M4 SPARX models (S255IR SMA1, CH3CN) | Sigma ~ r^-1.1; T 430 K inside 214 au, then r^-0.7; CH3CN 2e-8 to 900 au; turbulence 2 km/s; LTE; no interferometric filtering | M1 20 Msun at 25 deg; M2 4.76 Msun at 60 deg; M3 M2 plus 2.5 km/s infall; M4 Ulrich, r_CB 90 au (arbitrary) | qualitative PV comparison of the central "waist" |
| 2026ApJ..1003..219W | Keplerian disk (h = 0.2 r) plus Ulrich envelope, PPV fit | thermal Gaussian line profile; model and data peak-normalised | priors: M* 20-50 Msun, Rin 80-400, Rc 400-1600, Rout 1600-2500 au, i 30-90 deg | emcee, chi2 likelihood; M* 40 Msun, Rc 1300 au, i 50 deg; pure disk and pure Ulrich both fail |
| 2020A&A...634L..12D | Ulrich-type infall (DG Tau B) | i 63 deg | Rd 700 au, theta0 70 deg, M 1.1 Msun | n.s. |
| 2019A&A...623A..96Y | collisionless particle envelope (HL Tau) | M* 1.8 Msun, centrifugal radius 100 au, i 47 deg, PA 138 deg, envelope 3000 au, r^-1.5, 1e4 yr; T = 15 (r/1000 au)^-0.6 K; self-gravity ignored | n.s. | n.s. |
| 2025SciA...11.6953M | point mass plus rotating plane (massive core) | PV cut along steepest gradient; centre at long-baseline continuum peak | M 20-70 Msun, i 0-20 deg (0 = face-on), r_CB 0-200 au, r_out 800-1200 au | 45 Msun best fit judged too massive; spectral type gives i 20-30 deg |

## Streamers and infall rates

| Paper | Method | Settings | Result |
|---|---|---|---|
| 2024A&A...683A.133G | TIPSY trajectories | point-mass gravity only; M*, d, Vsys fixed; line intensity traces density; T 25 K; 13CO 1.45e-6, HCO+ 1e-9, optically thin | n.s. in pack |
| 2023ApJ...958...98F | Mendoza 2009 streamers, manual tuning | M* 0.5 Msun; i 47 deg; near side 59 deg E of N; R_cloud 5300 au; h_0 = sqrt(R_disk G M*); LTE, T_ex 21 K, X(C18O) 3e-7 | envelope 0.04 Msun (lower limit); Mdot ~4e-6 Msun/yr (order of magnitude); not unique |
| 2025ApJ...985..166K | streamer trajectories | i_s 107 deg, r_d 55 au, M* 0.14 Msun fixed; theta_0, phi_0 free; edges at 3 sigma; t_ff = sqrt(R^3/2GM*); C18O 15 K LTE thin | mass uncertainty from X(C18O) (1-2)e-7 and T_ex 10-30 K |
| 2024A&A...682A..61C | dusty streamer | M 0.15 Msun; Vsys 2.9-3.9 km/s explored; PV path width = beam (1.6 arcsec); only central gravity | rate is an upper estimate (whole streamer assumed to fall in) |
| 2026ApJ..1003..219W | trajectory families plus Ulrich Mdot | M* 40 Msun, PA 42 deg, i 50 deg; r_cb 1100-1200 au; theta0 families | Mdot = M_env / I = 7e-3 Msun/yr (order of magnitude; mass supply, not accretion) |
| 2014ApJ...793....1Y | infalling flows (L1489 IRS) | 1.6 Msun, conserved j, zero energy; theta0, phi0 +/- 3 deg; flows 5000 au (red), 2000 au (blue); X(C18O) 3e-7 | n.s. in pack |
| 2015ApJ...812...27A | Mdot = 2 pi R V_r Sigma | R 100-200 AU | (1.5-3.0)e-6 Msun/yr |
| 2020ApJ...904..181L | flattened envelope | Sigma 0.71 g cm^-2 at 900 au, V_r 2.5 km/s (M4: 2.99 km/s) | 2.3e-4 Msun/yr |
| 2017A&A...603A..10B | spherical infall | r ~80 AU, density ~2.3e9 cm-3 (particle species n.s.), v_in ~7.1 km/s; disk covers ~50% (~2 pi) | n.s. in pack |
| 2025SciA...11.4512O | massive streamers | i 65 deg, disk PA -55 deg; CB 250 au; T 100 K, kappa 1 cm2/g at 1.3 mm, dust-to-gas 0.01, mu 2.33, d 3.1 kpc; v_ff 6 km/s, l 500 au | n.s. in pack |
| 2018A&A...615A.141B | absorption toward the hot core | radius 1.54 arcsec | infall velocity 5.1 km/s (extraction rule n.s.) |
| 2018ApJ...861...14C | Hill5 fits to asymmetric profiles | initial tau 0.1-30, v_in 0.1-4 km/s, sigma 0.3-0.9 km/s | Hill5 may underestimate v_in, so the rate is a lower limit |
| 2015ApJ...814...22E | infall from absorption in B335 | T_dust 111 K (mass weighted); opacity 1.48e-2 cm2/g; gas-to-dust 100; constant infall rate | n.s. in pack |
| 2019ApJ...885...98S | 1D spherical collapse (IRAS 4A) | n = 3.05e9 (r/33.5 au)^-1.8 cm-3; v 1.1 km/s at 1000 au; turbulence 0.4 km/s | n.s. in pack |
| 2015ApJ...813L..19J | disk plus infall model (AFGL 4176) | disk 2000 AU, 12 Msun gas, Sigma ~ r^-1.5, i 30 deg, 25 Msun star; Draine dust R_V 5.5 | infall 4.6e-4 Msun/yr |
| 2024ApJ...967...15K | infall in a hot core | distance 2.38 kpc, 1.7 kpc also tested | n.s. in pack |
