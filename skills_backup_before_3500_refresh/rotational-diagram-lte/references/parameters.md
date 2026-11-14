# LTE and rotation-diagram parameters (from the `rotational-diagram-lte` pack)

Every value is copied from the pack's key-parameter, assumption, limitation or excerpt lines. Papers in the
pack that are off-topic for LTE line excitation (solar free-free, pure disk kinematics, dust-only work) are
left out. Non-LTE grids (RADEX, LVG) belong to the non-lte-excitation skill and appear here only as
cross-checks.

## 1. Full-spectrum LTE fits: fixed and free parameters

| Paper | Code | Free | Fixed / bounds |
|---|---|---|---|
| 2016A&A...587A..91B | Weeds | five model parameters (size, N, T, v offset, FWHM); "the other four parameters were optimized by eye" | deuterated species share main-isotopologue parameters |
| 2019A&A...628A..10B | Weeds | by eye | size 2" for all species; urea Trot 160 K, FWHM 5.0 km/s |
| 2014Sci...345.1584B | Weeds | 5 parameters per species | size 1.0", Trot 153 K, linewidth 5 km/s |
| 2020A&A...636A..67A | XCLASS | Tex, N, FWHM, vLSR | Tex 50-300 K (HNCO, NH2CHO), 70-400 K (H2CO); vLSR within +/-0.5 km/s |
| 2025ApJS..276...49J | XCLASS + MAGIX | N only | v_width 3 km/s, Trot 120 K, eta 0.384; lines with tau < 0.7 and width < 4 km/s |
| 2019ApJ...885...82L | XCLASS / MAGIX | per species | genetic, Levenberg-Marquardt, errorestim-ins; other species' Trot tied to SO2 |
| 2024A&A...682A..74F | MADCUBA AUTOFIT | V, FWHM, Tex, N | emission fills beam; 34SO Tex fixed at 58 K in one region |
| 2020MNRAS.492.1180R | MADCUBA AUTOFIT | N, v, FWHM | Tex 5 K (PN, PO), 34 K (SO) |
| 2021A&A...656A..46M | MADCUBA | N, Tex when constrained | size 5" (10" for 12CO), vLSR 230 km/s, FWHM 150 km/s, Tex 15 K when unconstrained |
| 2024A&A...686A..59N | LTE fit | N, Tex only with >= 2 lines spanning Eup | FWHM ~1.8 +/- 0.5 km/s from unblended lines; Tex 100 K (300 K for t-HCOOH, NH2CHO); Vlsr 2.7 km/s |
| 2018A&A...616A..90C | LTE grid | Tex 90-300 K, N 1e13-1e17 cm-2 | FWHM 1.8-2.4 (A), 0.8-1.2 (B) km/s; size 0.5"; tau < 0.2 |
| 2018A&A...619A..28L | LTE | N, Tex | CH2NH N 1e14-5e15, Tex 25-300 K; NO, N2O N 1e15-1e17, Tex 25-400 K; FWHM 1 km/s; Tbg 21 K |
| 2019A&A...624A..82B | LTE grid | Tex, N | Tex 10-500 K in 10 K steps; N in 20 log steps; channels within +/-2 FWHM; size = synthesised beam |
| 2020A&A...635A..48M | LTE | Trot, N | filling factor 0.5; FWHM 2.2-2.4 km/s; tau < 0.1; weight 3 where model exceeds data |
| 2017A&A...597A..53L | LTE | N | FWHM 1.0 km/s, size 0.5", tau <= 0.1, common Tex 125 K |
| 2015ApJ...813L..19J | LTE | Tex, vLSR, FWHM, N | initial Tex 50-350 K, FWHM 0.5-10 km/s, N 1e14-1e17 cm-2, size 0.53" |
| 2020ApJ...898...54T | LTE | FWHM 1-10 km/s | size 0.3" (Core A), 0.5" (B, C); filling factor 1 |
| 2019A&A...623A..68T | MCWeeds (absorption) | N, FWHM, v0 per component | dips > 4 sigma; velocity prior uniform +/-3 km/s; FWHM max 30 km/s; log N normal width 2 |
| 2024A&A...689A..65R | emcee | Tex, Nt | uniform Tex 0-50 K, Nt 1e11-1e14 cm-2 (disk-averaged); Tex 0-100 K, Nt 1e11-1e16 (radial) |
| 2024A&A...687A.220I | emcee | joint fit | beam and source size 0.5", FWHM 1 km/s, vLSR 2.7 km/s; 300 walkers, 1500 steps |
| 2016A&A...595L...4L | MCMC | | 100000 iterations, burn-in 20000, thinning 50; size 0.2" |
| 2019A&A...622A.206M | LTE | Ncol, Tex, VLSR, FWHM | transitions with tau < 0.5 |

## 2. Rotation (population) diagrams

| Paper | Species / source | Settings | Result quoted |
|---|---|---|---|
| 2020ApJ...890..142P | H2CO, 15 disks | iterative C_tau, converge at 0.001% (5000 iterations max); 10% flux error in quadrature; >= 3 lines | Tex 11 +/- 0.39 K (DM Tau) to 37 +/- 3.6 K (J1604-2130) |
| 2018ApJ...864..170G | o-H2CO, HD 163296 | 3 ortho lines; flux error from 500 signal-free apertures | 24 +/- 14 K |
| 2016A&A...587A..91B | COMs, Sgr B2(N2) | opacity from Weeds, contamination removed | CH2DCN 136 (14) K; C2H5CN 137.3 (1.6) K |
| 2019A&A...628A..10B | urea, formamide, Sgr B2(N1S) | opacity and contamination corrected | urea 350 +/- 190 K (unreliable); formamide 159 +/- 5 K |
| 2014Sci...345.1584B | i-, n-PrCN, Sgr B2(N2) | contaminants subtracted, thin verified | n-PrCN 153 +/- 12 K; i-PrCN 154 +/- 99 K |
| 2018A&A...620A..75K | TiO2, Mira | unblended lines | 580 +/- 65 K, N 2.7e16 cm-2 |
| 2019ApJ...870L..26C | CH3OH, comet ISON | 3 lines | 139 +/- 29 K |
| 2024A&A...689A..64B | OCS, SO2, NGC 253 | 1-3 components, reduced chi2, 15% calibration error, no beam correction | OCS 10-65 K and 124-312 K; SO2 55-79 K and 115-298 K |
| 2025A&A...696A.100G | C2H, Orion Bar | beam coupling from IRAM 30m and ALMA maps | 22 +/- 2 K and 59 +/- 7 K |
| 2019ApJ...872..200H | | card wording: "a conservative error of 20% for the ln(E_u/g_u) values" (anomalous: the ordinate is ln(N_u/g_u); propagate intensity errors instead, see SKILL.md step 3); 80% confidence intervals | |
| 2025A&A...693A..76C | CH3CN K ladder, per pixel | K = 2,3,4,5,7,8 and v8=1; >= 3 lines per pixel; show relative errors < 60% | |
| 2020ApJ...890...76N | K ladders | cores with >= 3 K lines above 3 sigma; Q(T) from Araya 2005 | |
| 2017ApJ...834....6S | | Trot 7.4 K adopted where 2_K-1_K not detected; A and E same N | |
| 2019ApJ...872..196S | | Trot 200 K where no diagram fit; Aij >= 1e-5 | |

## 3. Tex assumed for single lines and limits

| Paper | Tex | Sensitivity reported |
|---|---|---|
| 2020MNRAS.492.1180R | 5 K (PN, PO), 34 K (SO) | N changes by 2.5 (PN), 2.1 (PO) over 5-50 K |
| 2024A&A...682A..74F | PN over the 26-75 K (region 1) and 12-30 K (region 2) range of other tracers | |
| 2016ApJ...825...79S | | +/- 20 K changes N by 40% |
| 2024ApJ...963...72O | 40 K | N within 20% for 20-50 K |
| 2020MNRAS.496..394R | 20 K | higher or variable Tex changes results by < ~2 |
| 2020MNRAS.493L.108B | 25 K at 90-110 au | 20-80 K gives N within errors |
| 2015ApJ...798..124R | 50 K (CO mass limit) | |
| 2018A&A...619A..28L | 100 K for quoted 3 sigma limits | |
| 2016ApJ...830L..37I | 100 K, close to the 111 K dust temperature | |
| 2021A&A...656A..46M | 15 K when unconstrained; 300 K for vibrational display | |
| 2019A&A...624A.125M | 15 K | |
| 2017ApJ...848..101V | 15 K from CO(3-2)/(1-0) | |
| 2018A&A...620A.119D | lower limit = CMB at z (10.1 K), 20 and 30 K tried | |
| 2015A&A...582L...4M | Tex = CMB at z = 0.89 (5.14 K) | |

## 4. Optical depth handling

| Paper | Approach |
|---|---|
| 2016A&A...587A..91B | Goldsmith-Langer correction with Weeds opacities |
| 2020ApJ...890..142P | iterative C_tau from a thin start |
| 2019NatAs...3..314L | CH3OH = 13CH3OH x 60 |
| 2024A&A...682A..74F | 28SiO/29SiO ~ 8 and ~ 20, 32SO/34SO ratios vs MADCUBA tau |
| 2015ApJ...798...85P | 12CO/13CO brightness ratio R = 2.0 +/- 0.2 (so 13CO/12CO ~ 0.5) gives tau_12CO ~ 56, tau_13CO ~ 0.7, assuming both lines share Tex, the CMB is neglected and the abundance ratio 12CO/13CO = 76 |
| 2026A&A...705A.198M | Tex = peak Tb of 12CO; tau_12CO = 77 from ISM 12C/13C |
| 2020ApJ...898...97B | tau_blend(C2H) = 1.1 +/- 0.2, tau(HCN) = 5.8 +/- 1.8 |
| 2015ApJ...803...97S | thin after excluding thick lines; tau ~ 2 at S mu^2 ~ 35 at 150 K |
| 2018A&A...615L..10M | optical depth ratio 77 with same Tex |

## 5. Partition function and spectroscopy

| Paper | Item |
|---|---|
| 2014Sci...345.1584B | vibrational Q factors at 150 K: 1.64 (i-PrCN), 2.09 (g-n-PrCN), 2.36 (a-n-PrCN) |
| 2019ApJ...880..130M | CH3OCHO corrected by a factor 2.1 for torsional states |
| 2016A&A...587A..92M | Q corrections for conformers and vibrational states |
| 2016A&A...587A..91B | statistical 2:1 split for out-of-plane / in-plane conformers |
| 2019A&A...632A..19T | two CH3OD partition functions; CH3OD Trot fixed to CH2DOH |
| 2020MNRAS.497.5454I | Qrot = 1.23 Trot^1.5 |
| 2024AJ....167...66Y | Aul >= 1e-8 s-1, Eu <= 1000 K; CH2DOH spectroscopy uncertain by ~3 |
| 2019A&A...624A..70C | Aij >= 1e-3 s-1, Eup <= 500 K |
| 2025A&A...693A.101T | Eup <= 300 K, A >= 1e-6 s-1, < 1000 GHz |

## 6. Spin and isotopic ratios adopted

| Paper | Ratio |
|---|---|
| 2024A&A...689A..65R | o/p 3:1 |
| 2019ApJ...876...72L | H2CS o/p 3 |
| 2024ApJ...968L..19F | o/p 1 |
| 2021A&A...645A.145G | H2CO o/p 1.8-2.8; H2CS 3.0; CH3OH A/E = 1 |
| 2026A&A...707A.120H | E/A = 1 (CH3OH, CH3CHO); OPR 3 (H2CO, CH2CO) |
| 2024ApJ...969..143I | para-H2CO only, no OPR needed |
| 2019NatAs...3..314L, 2015ApJ...813L..19J, 2020MNRAS.498L..87B | 12C/13C = 60 |
| 2019A&A...632A..19T, 2024A&A...686A.201N | 12C/13C = 70 |
| 2017MNRAS.466...49J, 2014A&A...569A..11S | 12C/13C = 50 |
| 2015ApJ...798...85P | 12CO/13CO = 76 (abundance, used for the LTE 13CO mass) |
| 2017A&A...608A..38O | 12CO/13CO = 100 |
| 2016ApJ...832..158Z | X12,13 = 62 |
| 2021A&A...656A..46M | measured 12C/13C = 22 +/- 2 in NGC 253 |

## 7. LTE justification by density

| Paper | Density quoted |
|---|---|
| 2018ApJ...864..170G | > 1e6 cm-3, emission thermalized |
| 2017ApJ...839...43O | > 1e6 cm-3 |
| 2018A&A...614A.123P | n_crit ~ 1e6 cm-3 vs 4e7-5e8 cm-3 |
| 2018MNRAS.478.2505I | n_crit ~ 1e7 cm-3 |
| 2020A&A...635A.189F | n(H2) > 1e7 cm-3 |
| 2025A&A...693A..76C | > 1e7 cm-3 |
| 2024IJAsB..23...14M | 7e7 cm-3 |
| 2020A&A...644A..84M, 2024ESC.....8..665M | ~ 1e8 cm-3 |
| 2019ApJ...871..112X | > 1e9 cm-3 |
| 2018A&A...620A.170J | >~ 1e10 cm-3 |
| 2016ApJ...833...41Z | LTE assumed and found not to hold |

## 8. Abundance normalisation

| Paper | N(H2) route |
|---|---|
| 2020A&A...636A..67A | dust continuum, Tdust 100 K, kappa 1.0 cm2/g, gas-to-dust 100 |
| 2025ApJS..276...49J | continuum fit, N_H2 = 1.24e25 cm-2 (2%), kappa 2.2 cm2/g at 230 GHz, beta 1 |
| 2021A&A...656A..46M | C18O with 16O/18O = 100 (the pack's step line prints "18O/16O = 100", inverted; the paper's Oxygen result is 16O/18O = 100 +/- 20) and CO/H2 ~ 8e-5: N(H2) = 100 N(C18O) / 8e-5 = 3.1e23 cm-2, factor 2 uncertainty |
| 2018A&A...615A.141B | dust temperature = CH3OCHO Tex; N_H2 a lower limit for thick dust |
| 2024IJAsB..23...14M | N(H2) = 1.30e23 cm-2 |
| 2015A&A...581A..85P | X_SO = X_CO N_SO / N_CO with X_CO = 1e-4 |

## 9. Filling factors and column-to-mass conversion

| Paper | Item |
|---|---|
| 2017ApJ...848..101V | filling factor 0.1 assumed (same for CO 1-0 and 3-2); M_mol = 1.36 m_H2 N_H2 A_source; 12CO/13CO = 50, 12CO/H2 = 1e-4 |
| 2020A&A...635A..48M | filling factor 0.5 assumed |
| 2025ApJS..276...49J | eta = 0.384 fitted to the continuum, then fixed in the line fits |
| 2024ApJ...969..143I | filling factor restricted to < 1 in the fit |
| 2015A&A...581A..85P | M_disk ~ 1.4 m_H2 (N_C17O / X_C17O) A_beam, blue + red lobes; C17O/CO = 1/1792, X_CO = 1e-4; beam dilution factor ~8 |
| 2021ApJ...908..163M | [CI] H2 mass limit with Q10 = 0.5, X[CI] = 1.5e-5, Delta v = 300 km/s, helium factor 1.36 |

Assumed unity filling: 24 bibcodes by the count rule in SKILL.md (Parameter defaults section).
