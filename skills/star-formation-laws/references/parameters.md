# Star formation laws: longer parameter table

All values are from the evidence pack (`skills/packs/star-formation-laws.md`); a few marked "card" come from
the paper's methods card. They are what papers adopted, not recommendations. Gas-side conversion factors
(alpha_CO, r_J1, X_CI, gas-to-dust) are treated in `../gas-mass-co-conversion/` and listed here only where
they set a star formation law result.

## SFR calibrations

| tracer | calibration as quoted | IMF | paper |
|---|---|---|---|
| L_IR (8-1000 um) | SFR = 1.72e-10 L_IR, then /1.5 to Kroupa (units not in pack) | Salpeter -> Kroupa | 2019A&A...621A..27F |
| L_IR | SFR = 1.40e-10 L_IR (units not in pack) | Chabrier | 2025A&A...698A.204H |
| L_IR | SFR [Msun/yr] = 1.7e-10 L_IR/Lsun (Kennicutt 1998) | not stated in pack line | 2021ApJ...915...46C |
| L_IR | SFR = L_IR/(5.8e9 Lsun) (Kennicutt 1998) | Salpeter | 2021MNRAS.500.3667S, 2024A&A...691A.248L |
| L_IR | 1.73e-10 Msun/yr/Lsun | Salpeter 1-100 Msun | 2024MNRAS.535.1533B |
| L_IR | SFR_IR [Msun/yr] = 1.49e-10 L_IR/Lsun | Chabrier | 2022MNRAS.510.4976A |
| L_IR | 1.49e-10 L_IR (units not in pack) | not stated in pack line | 2020ApJ...905...86S |
| L_IR | 1.48e-10 Msun/(yr Lsun) | Kroupa | 2020Natur.584..201R, 2024MNRAS.533.2966Q (units not in its line) |
| L_IR | SFR [Msun/yr] = 1.0e-10 L_IR/Lsun (Kennicutt 1998) | Chabrier | 2015ApJ...815L...8U, 2016ApJ...832..114M |
| L_IR | SFR = 9.5e-11 L_IR (units not in pack) | Chabrier | 2019A&A...625A..96K |
| L_IR | log SFR [Msun/yr] = log L_IR [erg/s] - 43.41 | not stated in pack line | 2025ApJ...993..111W |
| L_FIR | SFR = 1.73e-10 L_FIR/Lsun Msun/yr | Salpeter | 2013A&A...559A..29C |
| L_IR | Kennicutt 1998, rescaled to Chabrier | Chabrier | 2019ApJ...876..130H, 2019ApJ...881...63N, 2025ApJ...994....4A |
| L_IR | Kennicutt 1998 | Salpeter | 2017A&A...599A.134S, 2018ApJ...856...72O, 2019ApJ...876...99S |
| L_IR | Kennicutt and Evans 2012 | not stated in pack line | 2017A&A...605A..42C, 2020A&A...635A.119C |
| TIR | Murphy et al. 2011 TIR-to-SFR | not stated in pack line | 2015ApJ...815..103B |
| H-alpha | SFR [Msun/yr] = 5.53e-42 L_Halpha (Hao+11; L units not in pack) | not stated in pack line | 2024ApJ...976...88L |
| H-alpha | SFR [Msun/yr] = 4.5e-42 L_Halpha [erg/s] (Kennicutt 1998); f = 0.44 gives likely upper-limit L_Halpha | not stated in pack line | 2020ApJS..247...61F |
| H-alpha | Murphy et al. 2011, 20% uncertainty | Kroupa | 2019Natur.569..519K |
| H-alpha | SFR = 7.9e-42 L[Halpha_cor,mask] (units not in pack) | Chabrier stated for the paper | 2021MNRAS.500.3802H |
| H-alpha | log SFR = log L_Halpha - 41.27 (Kennicutt and Evans 2012; L units not in pack line) | not stated in pack line | 2022MNRAS.514.5035L |
| H-alpha + 1.4 GHz | L_corr = L_obs + 0.39e13 L(1.4GHz); SFR = L_corr/10^41.27 (units not in pack) | not stated | 2022ApJ...929..100K |
| H-alpha + WISE 22 um | default; FUV + 22 um where H-alpha missing; matches MUSE maps to about 0.1 dex | not stated | 2025ApJ...985...14L |
| H-alpha (MaNGA, Pipe3D) | Kennicutt 1998, Balmer decrement, R_V = 3.1; non-SF spaxels from D4000 | Salpeter | 2024ApJ...964..120P, 2020MNRAS.492.6027E |
| Pa-alpha | SFR = 4.0e-41 L_Paa; intrinsic Halpha/Paa 0.116 (units not in pack) | not stated | 2020A&A...643A..78M |
| Pa-alpha | Halpha/Paa = 8.6, Kennicutt 2012 | Kroupa | 2026A&A...707A.144S |
| 3 GHz radio | Murphy 2012, T_e = 1e4 K, alpha_NT = -0.85, SFR/beam area 0.26 kpc^2 | Kroupa | 2025ApJ...979..217S |
| 93 GHz free-free | T_e = 1e4 K, alpha_NT = 0.84, 10% dust correction, 30% SFR uncertainty | not stated | 2023ApJ...945...42B |
| 8.4 GHz | thermal/non-thermal via Murphy 2012, alpha_nth = 1.2 | not stated | 2015ApJ...799...11X |
| H40alpha | SFR [Msun/Myr] = 3.008e-3 L(H40alpha) [Jy km/s kpc^2] | Kroupa and Weidner 2003 | 2022MNRAS.510.4998Z |
| 21 um (JWST) | Sigma_SFR [Msun/yr/kpc^2] = 3.8e-3 I_21um [MJy/sr] | not stated | 2025MNRAS.544.4014Z |
| CO(5-4) | L'_CO(5-4) to L_TIR (Daddi 2015), then Kennicutt and Evans 2012 | Chabrier | 2026MNRAS.546ag167S |
| Pa-alpha | with Calzetti extinction | not stated | 2021A&A...656A..60A |
| FUV + 24 um | Sigma_SFR = 3.2e-3 I24 + 8.1e-2 I_FUV; A_FUV = 8.24 E(B-V) (map and output units not in pack) | not stated | 2012ApJ...760L..25E |
| FUV / NUV / 12 um / 24 um | K = 1.04e-1, 1.04e-1, 3.77e-3, 2.97e-3 (units not in pack) | not stated | 2018ApJ...861L..18U |
| UV (HST) | Salim07, SFR uncertainty factor 2; region SFR = share of UV counts x global SFR | Chabrier | 2018ApJ...863..193V |
| 8 um PAH | log Sigma_SFR = 0.844 log Sigma_L8 - 30.923 (intercept is unit-dependent; units not in pack, take them from the paper) | not stated | 2019ApJ...887...88E |
| 33 GHz free-free | mean thermal fraction 79% | not stated | 2015ApJ...813..118M |
| 110 GHz | possible 25% synchrotron contamination | not stated | 2018ApJ...863..129S |
| 160 um | linear mapping, no AGN contribution | universal IMF | 2019ApJ...876..112R |
| WISE 22 um | same conversion as Spitzer 24 um | not stated | 2017MNRAS.472.1239B |
| [CII] | 0.5 dex scatter on SFR_CII | not stated | 2019ApJ...882...10N |

IMF conversions used: Salpeter to Chabrier SFR /1.8 (2017A&A...604A.117C), /1.77 (2022MNRAS.511.1303V),
/1.7 (2020MNRAS.496..875R, 2021NatAs...5..319P), -0.23 dex (2021A&A...654A..90L), x0.61 (2024MNRAS.52710201E),
/1.6 (2024ApJ...976...70L); an "IMF difference" factor of 1.5 citing Kennicutt 2012 (2024ApJ...976..201F);
Salpeter to Kroupa /1.5 (2019A&A...621A..27F); stellar mass Chabrier = Salpeter/1.7 (2018A&A...616A.110E).
IMF high-mass shape as a 30% systematic on SFR (2020MNRAS.499.4940Z).

## Dust temperature and emissivity for single-band IR SFRs

| T_dust, beta | paper |
|---|---|
| 47 K, 1.6 | 2013ApJ...770...13W |
| 47 K | 2018ApJ...854...97D, 2019ApJ...881...63N |
| 40 K (all galaxies) | 2017A&A...599A.134S |
| 41 K, 1.5, bolometric factor 1.91 | 2018ApJ...867..140L |
| average of (47 K, 1.6) and (41 K, 1.95) | 2017MNRAS.465.4390B |
| 45 K, 1.5 | 2019ApJ...881..124M |
| 35 K, 1.5 | 2017ApJ...851..145M |
| 30 K, 1.5 | 2018MNRAS.478.1170C |
| 30-50 K, 1.2-2.0 | 2019ApJ...882...10N |
| 25-45 K | 2017A&A...605A..42C |
| 25 K (20-30 K for errors) | 2016ApJ...833...12R |
| 50 K, 2.0 | 2017A&A...604A.117C |
| 50 K, 2.5 (to set upper limits) | 2019A&A...621A..27F |
| 30, 50, 90, 120 K, 1.5 (2 at 50 K) | 2015ApJ...813...45L |
| free T, beta = 1.8 | 2025A&A...698A.204H |
| 47 K, 1.6 | 2026MNRAS.546ag167S, 2019MNRAS.488.1180S (30-50 K for errors), 2024ApJ...977L..46B, 2025A&A...694A.171M |
| 40 K, 1.5 | 2020MNRAS.499.5136C |
| 30 K, 2.0 | 2025A&A...696A..83A |
| 65 K (SMG), 50 K (QSO), beta 1.5 | 2013A&A...559A..29C |
| thin 40 K, 1.85; thick 58 K, 1.93 | 2025A&A...694A.218B |
| 35 K, 1.8 from the global SED; resolved tests at 60 and 80 K | 2020MNRAS.494.5542R |
| T_d = 34.6 + 3.94(z-2) K, or fixed 35 or 50 K | 2020ApJ...902..112B |

## Gas side, as it enters the law

| quantity | value | paper |
|---|---|---|
| alpha_CO (Galactic, incl. He) | 4.35 | 2020ApJ...903..145L, 2025ApJ...995..151Y |
| alpha_CO | radially varying (Bolatto 2013 / Sun 2022) for the analysis; constant 4.35 only for a sensitivity estimate | 2025ApJ...988..162D |
| alpha_CO | 4.36, r31 = 0.27, inclination 57 deg, 45% missing flux | 2021A&A...656A..60A |
| alpha_CO | 4.36 x f_metal (1.1 at log M* = 11, 1.4 at 10.5) | 2019PASJ...71...40T |
| alpha_CO | 4.4 incl. He, R21 = 0.7 | 2020MNRAS.499..193K |
| alpha_CO | 4.6 | 2019MNRAS.485.1595P |
| alpha_CO | 4.6 disks, 0.8 mergers | 2020MNRAS.497.2771M |
| alpha_CO | variable, Bolatto+13 eq. 31, iterated to < 0.1% change | 2024ApJ...976...88L |
| alpha_CO | metallicity-dependent, Genzel 2015 | 2024A&A...692A.215C |
| alpha_CO | 0.8 | 2017A&A...604A.117C, 2017ApJ...846..108C, 2019MNRAS.489..427I |
| alpha_CO | 0.86, 0.5 dex error | 2014ApJ...790..160S |
| alpha_CO | 1.1, with a CO(2-1)/CO(1-0) **flux** ratio f_CO(2-1)/f_CO(1-0) = S21dv/S10dv = 3 (not the L' or brightness-temperature ratio R21; the corresponding L'21/L'10 is 3/4 = 0.75, since L' scales as S dv / nu_obs^2) | 2020A&A...641A.151S |
| alpha_CO MS vs SB | 4.87 with R51 = 0.23 vs 1 with R51 = 0.6 | 2017MNRAS.469.4683C |
| X_CO | 2e20 cm^-2 (K km/s)^-1, Sigma_H2 = 4.2 I_1-0, R21 = 0.7; the pack line reads "with helium", but X_CO itself converts CO intensity to H2 column and has no helium: helium enters only the mass coefficient (here the 4.2) | 2019A&A...623A..66B |
| X_CO -> alpha_CO | X_CO = 2e20 corresponds to alpha_CO = 4.35 including the 1.36 helium factor | 2025ApJ...995..151Y |
| alpha_CO | 4.3 constant; robustness test with a factor-two lower value in starburst centres | 2020MNRAS.493L..39E, 2020MNRAS.492.6027E |
| alpha_CO | 4.35 (Z/Zsun)^-1.5 (max(Sigma_star,100)/100)^-0.25; R21 = 0.65 (Sigma_SFR/0.018)^0.125, 0.35-1.0 | 2025ApJ...985...14L, 2025A&A...693L..13N, 2026MNRAS.552g1615S |
| alpha_CO | Bolatto 2013 eq. 31 iterated to a 0.1 convergence threshold; Sigma_HI = 5 assumed | 2021ApJ...909...12G |
| alpha_CO | Accurso 2017 with PP04 metallicity (12+log O/H capped at 8.8; 1.36 included) | 2021MNRAS.500.3802H, 2026A&A...712A.227E |
| alpha_CO | 4.2 (centre) to 20 (outskirts) | 2024A&A...689A.122B |
| alpha_CO | 1.1 with CO(2-1)/CO(1-0) = 0.85 (LIRG merger) | 2025ApJ...979..217S |
| alpha_CO | 1.0 with R31 = 0.78 (lensed z = 3 DSFG) | 2020MNRAS.494.5542R |
| alpha_CO | 0.8 (x1.36 for helium) and 3.8, compared with dust and [CI] estimates | 2025A&A...694A.218B |
| alpha_CO | 0.8 ULIRGs, 1.2 LIRGs, 4.4 others | 2019MNRAS.483.4586F |
| alpha_HCN | 10 | 2015ApJ...815..103B, 2018ApJ...858...90G, 2018ApJ...863..129S, 2019AJ....157..131B, 2024A&A...689A.122B |
| alpha_HCN | 14; 15 | 2023MNRAS.521.3348N; 2025A&A...693L..13N |
| HI | Sigma_atom = 2.0e-2 I_HI cos i (Msun/pc^2, I_HI in K km/s), includes 1.36 | 2024A&A...687A.293Q |
| alpha_HCO+ | about 10 | 2015ApJ...813..118M |
| gas from dust | log delta_GDR = 10.54 - 0.99 (12+log O/H); starbursts delta_GDR about 30 | 2020A&A...641A.155V |
| gas from 850 um | alpha_nu = 6.7e19 erg/s/Hz/Msun at 25 K, T correction 0.77-1.06 | 2026ApJ..1001..131C |

Helium: X_CO is an H2 column conversion without helium (general practice); alpha_CO or the Sigma coefficient
is where the 1.36 factor goes. Check whether a quoted alpha_CO already includes it and apply 1.36 exactly once.

## Sampling, cuts and fits

| setting | value | paper |
|---|---|---|
| pixel grid | 6'' resolution, 3'' pixels; SFR 3 sigma = 0.018 Msun/yr | 2012ApJ...760L..25E |
| pixel grid | 2.4'' = 43 pc; Sigma_mol complete to about 4 Msun/pc^2 | 2019ApJ...887...88E |
| aperture grid | beam-sized, second grid offset by 0.5 FWHM | 2024ApJ...976...88L |
| aperture | 0.75'' = 34 pc radius | 2021A&A...656A..60A |
| hexagons | 1 kpc spacing, 1.5 kpc resolution | 2021A&A...656A.133Q |
| spiral apertures | 200 pc wide on a 100 pc grid; robust 100-400 pc | 2025A&A...700A.285W |
| aperture photometry | 3'' apertures (11 regions) | 2018ApJ...863..129S |
| spaxel cut | CO S/N > 2; Sigma_* > 1e7 Msun/kpc^2 | 2019ApJ...884L..33L |
| spaxel cut | CO S/N > 2; AGN bulge excluded | 2017ApJ...851...18L |
| resampling | 10,000 resamplings; 2 sigma gas cut | 2024ApJ...972..147C |
| regression | Kelly 2007 linmix, log space | 2018ApJ...863..193V |
| regression | LINMIX_ERR with censored points; L_IR >= 10^8.5 Lsun | 2020A&A...641A.155V |
| regression | ODR | 2024ApJ...976...88L, 2019ApJ...887...88E |
| regression | least squares per galaxy | 2025ApJ...995..151Y |
| regression | least squares on binned data, also slope fixed to 1 for SFE (card) | 2017A&A...602L...9M |
| regression | double power law with free break, 10,000 bootstraps (card) | 2019ApJ...882....5W |
| correlation | Kendall tau | 2020ApJ...903..145L, 2020MNRAS.496.2155Z |
| hexagons | 500 pc, beam area 0.26 kpc^2, 3 km/s channels | 2025ApJ...979..217S |
| regression | linmix (10^4 MCMC, with and without limits), ODR, ASURV; GMM by AIC/BIC | 2025ApJ...979..217S |
| correlation | Spearman, significant if rho > 0.30 and p < 0.03 | 2025ApJ...979..217S |
| pixel grid | 150 pc fiducial; 200, 300, 500 pc, 1 kpc tests; > 60% detected per Sigma_* bin | 2022A&A...663A..61P |
| regression | hierarchical Bayesian, NUTS, 4 chains x (2000 + 2000); centred at log Sigma_* 8.11, Sigma_mol 7.25, Sigma_SFR -2.48 | 2022A&A...663A..61P |
| beam binning | grid moved one pixel at a time over all origins; rms + 10% calibration error | 2020MNRAS.496.2155Z |
| beam binning | 25 grid offsets (5 x 5, 0-0.8 bin size) to scale spaxels to the PSF | 2021MNRAS.500.3802H |
| sub-beam pixels | 0.5'' pixels, non-independence handled after Zabel 2020 | 2024MNRAS.535.2538Z |
| pixel cut | > 3 sigma in CO or dust and > 1 sigma in the other | 2024MNRAS.535.1533B |
| radial annuli | 200 pc wide, 100 pc step; S/N > 3 in H-alpha and CO | 2022MNRAS.514.5035L |
| hexagons | 1.5 kpc; keep f_comp > 0.5 and Sigma_mol > 20 Msun/pc^2 (841 regions in 67 galaxies) | 2025A&A...700A.123M |
| lensed boxes | 200 pc to 6.4 kpc boxes and apertures | 2023A&A...678A.183N |
| SFE bootstrap | 10,000 realisations within error bars; 500 pc radial bins | 2024A&A...687A.293Q |
| control spaxels | matched within 0.1 dex in Sigma_H2 or Sigma_*, M_*, O/H and 0.1 R/R_e; b/a > 0.34 | 2020MNRAS.492.6027E, 2020MNRAS.493L..39E |
| driver bands | Delta f_gas - Delta SFE within +-0.15 counts as both | 2024ApJ...964..120P |
| global area | two-sided disk 2 pi R_FWHM^2; unresolved CO radius = optical Petrosian / 1.6 | 2017MNRAS.470.3775V |
| global area | Sigma_SFR = SFR/(2 pi R_e^2), R_e = FWHM/2 | 2022A&A...665A...3J |
| global area | (0.5 SFR_IR)/(pi R_e^2), R_e = mean deconvolved FWHM/2 | 2022MNRAS.510.4976A |
| survival fit | survdiff; AGN fits with slope fixed to the MS value and limits as detections (upper limits only) | 2017MNRAS.468.4205K |

## Efficiency per free-fall time and life-cycle parameters

| quantity | value | paper |
|---|---|---|
| eps_ff (IRDC, turbulent core model) | 0.11; eps_core = 0.5 | 2018ApJ...855L..25K |
| eps_ff in models | KDM 0.015; SFK 0.0045, b = 0.4 | 2019MNRAS.487.4305S |
| dense-gas model | n_dense = 2.8e5 cm^-3, eps_SF = 0.28% | 2018ApJ...863..129S |
| feedback model | P*/m* = 3000 km/s | 2024ApJ...976...88L |
| life-cycle fit | t_gas = 35 Myr, t_over = 5 Myr, t_star = 10 Myr, lambda = 400 pc | 2017ApJ...835..278S |
| (U)LIRG disk model | alpha+beta about 0.3, Sigma_gas/Sigma_total about 0.5 | 2019ApJ...882....5W |
| star formation timescale | 5 Myr | 2017ApJ...850...54C |
| eps_ff (500 pc, H = 100 pc, filling factor 1) | medians 25% and 42% | 2025ApJ...979..217S |
| eps_ff model | eps_0 = 1%, b = 0.4, fixed half depth R = 100 pc; eps_ff definition-sensitive | 2023ApJ...945...42B |
| cloud density | h = 100 pc, rho_cloud = Sigma_cloud/2h | 2025A&A...700A.123M |
| dense-gas free-fall time | 0.8 Myr for n_H2 about 3e3 cm^-3 | 2025A&A...693L..13N |
| eps_ff in models | 0.015 | 2024MNRAS.52710201E |

## Results to sanity-check against (not targets)

Resolved molecular KS slopes: 0.63 overall and 0.28 in a CND (2019ApJ...887...88E); 0.64 to 1.18
(2018ApJ...863..193V); 0.62 to 1.08 with mean 0.81 in dwarfs (2025ApJ...995..151Y); 0.90 or 1.23 depending on
alpha_CO (2024ApJ...976...88L); 0.52+-0.17 for Arp 240, 0.52 and 0.75 for its two galaxies, 0.15 to 0.98 by
component (2025ApJ...979..217S). Global slope 1.26+-0.02 for dusty z < 0.35 galaxies (2017MNRAS.470.3775V).

Depletion times: median 0.8 Gyr in z~0.1 analogues (2024ApJ...976...88L); 1.5 Gyr in Cen A
(2019ApJ...887...88E); 3.9 Gyr along a Seyfert spiral (2025A&A...700A.285W); < 2 Gyr in arms vs 3-4 Gyr between
arms, and >= 10x longer in a ram-pressure tail (2020MNRAS.496.2155Z); 0.10-0.14 Gyr in a LIRG merger
(2025ApJ...979..217S); log SFE -9.5 to -9.0 per yr in main-sequence MaNGA galaxies (2024ApJ...964..120P);
0.7 Gyr in protocluster galaxies (2025A&A...698A.204H); 0.4 Gyr in a LLAGN centre (2020A&A...641A.151S);
67-85 Myr in a z = 1.52 merger pair (2018ApJ...868...75S); 23-140 Myr for one z = 4.3 galaxy depending on the gas
estimator (2025A&A...694A.218B); 50+-40 Myr in a z~2 quasar host (2021MNRAS.500.3667S); 1-20 Myr across a lensed
z = 3 DSFG (2020MNRAS.494.5542R); 12-28 Myr in a hyperluminous quasar (2019ApJ...887...74F). SFE_H2 of 0.9-4.1
per Gyr in dwarfs (2025ApJ...995..151Y).

Extreme Sigma_SFR: about 4200 (2013ApJ...767..132H), 4500 (2021MNRAS.500.3667S) and 2e3 Msun/yr/kpc^2
(2017ApJ...842L..16L), compared in 2019ApJ...876..130H with its model-dependent Eddington-limited lower limit of
about 650 Msun/yr/kpc^2, which assumes optically thick emission, a gas fraction of unity, dust-to-gas 1/90 and
one global dust temperature (2022MNRAS.510.4976A uses the same bound with f_gas = 1 and f_dg = 1/90).
eps_ff = 0.11 in an IRDC (2018ApJ...855L..25K).
