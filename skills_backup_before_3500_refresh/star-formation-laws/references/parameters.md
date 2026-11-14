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
| L_IR | Kennicutt 1998, rescaled to Chabrier | Chabrier | 2019ApJ...876..130H, 2019ApJ...881...63N, 2025ApJ...994....4A |
| L_IR | Kennicutt 1998 | Salpeter | 2017A&A...599A.134S, 2018ApJ...856...72O, 2019ApJ...876...99S |
| L_IR | Kennicutt and Evans 2012 | not stated in pack line | 2017A&A...605A..42C, 2020A&A...635A.119C |
| TIR | Murphy et al. 2011 TIR-to-SFR | not stated in pack line | 2015ApJ...815..103B |
| H-alpha | SFR [Msun/yr] = 5.53e-42 L_Halpha (Hao+11; L units not in pack) | not stated in pack line | 2024ApJ...976...88L |
| H-alpha | SFR [Msun/yr] = 4.5e-42 L_Halpha [erg/s] (Kennicutt 1998); f = 0.44 gives likely upper-limit L_Halpha | not stated in pack line | 2020ApJS..247...61F |
| H-alpha | Murphy et al. 2011, 20% uncertainty | Kroupa | 2019Natur.569..519K |
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

IMF conversions used: Salpeter to Chabrier SFR /1.8 (2017A&A...604A.117C), /1.6 (2024ApJ...976...70L);
Salpeter to Kroupa /1.5 (2019A&A...621A..27F); stellar mass Chabrier = Salpeter/1.7 (2018A&A...616A.110E).

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
| alpha_HCN | 10 | 2015ApJ...815..103B, 2018ApJ...858...90G, 2018ApJ...863..129S, 2019AJ....157..131B |
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
| correlation | Kendall tau | 2020ApJ...903..145L |

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
