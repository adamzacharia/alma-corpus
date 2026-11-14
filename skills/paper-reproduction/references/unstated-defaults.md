# Unstated and inherited settings: inventory template and corpus examples

Companion to `../SKILL.md`. The physical conventions below are the ones papers most often adopt from earlier work
(pack "Conventions inherited" and "Data or numbers taken from the literature" lists). There is no single corpus
default for most of them: the right value is the one the paper (or the paper it cites) used. When the paper
is silent, pick the example closest to its field, flag it, and test how much the answer key moves.

## Inventory template (one row per setting)

| Setting | Stated value | Where stated (section, table, caption) | Inherited from (bibcode or reference) | Default assumed | Basis | Effect tested? |
|---|---|---|---|---|---|---|

Fill it before processing. Rows commonly needed: calibration route and CASA version, flux calibrator and
flux-scale uncertainty, flagging, self-calibration (applied? rounds, intervals, reference antenna), line-free
channels and fit order, weighting/robust and taper, cell and image size, deconvolver, mask, threshold,
primary-beam correction, channel width and smoothing, rest frequency and velocity frame, phase centre,
apertures and regions, completeness or flux-boosting corrections, distance, inclination and PA, systemic
velocity, physical constants (below), fit priors and sampler settings, code and version.

## Calibration and imaging conventions

| Convention | Corpus examples |
|---|---|
| Calibration follows a CASA guide or SV team scripts | 2012ApJ...760L..25E (CASA guide for Antennae SV data), 2013Sci...341..630Q (self-calibration from the TW Hya SV CASA guide), 2013ApJ...765L..14Q and 2013ApJ...774...16R (SV team scripts) |
| Standard Cycle 0 reduction script | 2014ApJ...793....1Y, 2014ApJ...795..156W |
| Calibrator flux models | Butler-JPL-Horizons 2012 / ALMA Memo 594 (2015A&A...576L..15O); Titan model from ALMA Memo 594 (2014ApJ...795L..30C) |
| Hanning smoothing to mimic the pipeline | 2013ApJ...774...16R |
| Online Hanning smoothing in the data | 2020ApJ...904..181L (0.488 MHz, 0.42 km/s) |
| Short-spacing combination by feathering from an earlier paper | 2013ApJ...777..126S, 2017ApJ...850...35L |
| Self-calibrated visibilities used directly rather than CLEAN images | 2015A&A...581L...3V |
| Positional accuracy rule of thumb (beam / (2 x S/N)) and ~10% of beam for Cycle 0 | 2013ApJ...768L..38H |
| Uncertainties of elliptical Gaussian fits in correlated noise (Condon 1997) | 2013ApJ...768...91H, 2013MNRAS.432....2K, 2014ApJ...796...84R |

## Physical constants papers adopt from earlier work

| Quantity | Examples (value, paper) |
|---|---|
| Dust opacity | kappa = 0.1 (lambda/0.3 mm)^-beta cm2/g with beta = 2 (2013A&A...555A.112P); 0.1 (0.3 mm/lambda)^beta with beta = 1 (2014ApJ...793....1Y); 0.77 (850 um/lambda)^beta (2014ApJ...792...34O, Dunne et al. 2000); 2.3 cm2/g at 1.3 mm with gas-to-dust 0.01 (2014ApJ...784...62A); 0.034 cm2/g at 856 um (2014ApJ...784...82M); 0.1 cm2/g at 220 GHz, beta = 0 (2014ApJ...796..131O); 0.01 cm2/g at 231 GHz, beta = 1 (2014ApJ...789L...4T); 0.5 cm2/g at 1.3 mm (2015A&A...576L..15O); 1.9 cm2/g at 0.89 mm and 1.3 cm2/g at 1.3 mm (2026A&A...705A.197Z) |
| Dust temperature | 20 K "for comparison with earlier surveys" (2014ApJ...784...82M); Td = 25 (L/Lsun)^0.25 K (2014ApJ...784...62A); 30 K (2014A&A...566A..74L); 150 K for a hot core (2026ApJ..1004L...6D) |
| Greybody for high-z FIR | beta = 2, exclude rest wavelengths < 50 um (2013ApJ...767...88W); the same exclusion in 2014ApJ...785..149S; beta = 1.5, T = 35 K (2013ApJ...769L..27H) |
| Mean molecular weight | 2.8 per H2 (2013A&A...555A..73K, 2026ApJ..1004L...6D) |
| CO abundance or H2/CO | CO/H2 = 1e-4 (2013A&A...555A..73K); H2/CO = 1e4 (2016ApJ...829....6W) |
| X_CO or alpha_CO | 3e20 (2012A&A...538L...9H, 2012ApJ...760L..25E); Galactic 2e20 (2014ApJ...792...94D); alpha_CO 4.8 for L_FIR < 1e11 and 0.8 for U/LIRGs (2014ApJS..214....1U); ULIRG 0.4e20 with 0.5 dex error (2014ApJ...790..160S) |
| CO line ratios | I(2-1)/I(1-0) = 1.0 (2012ApJ...760L..25E); 1-0/2-1 = 0.7 (2013ApJ...774...73I); R21 = 0.5 (2020ApJS..247...15S, for time estimates); r31 = 0.57 (2015A&A...576L...2S) |
| Isotopic ratios | 12C/13C = 75 (2013A&A...557A.132M); 16O/18O = 560 (2013A&A...549L...3P); 12CO/13CO = 69 and 12CO/C18O = 557 (2013ApJ...774...16R) |
| Line luminosity definition | Solomon & Vanden Bout 2005 (2012ApJ...752L..30W, 2013PASJ...65..100I, 2020ApJS..247...15S, 2025A&A...699L..11V) |
| SFR calibrations | SFR = 1.7e-10 L_IR (2012ApJ...761L..32W, Kennicutt 1998); Kennicutt 1998 with Salpeter IMF (2013ApJ...770...13W) |
| Cosmology | Omega_m = 0.308, Omega_Lambda = 0.692, H0 = 67.8 (2020ApJS..247...15S) |
| Disk structure exponents | p = -1.5, q = -0.4 initial values (2014ApJ...793....1Y); gamma = 1 for comparison with prior work (2014ApJ...791...42Z) |
| Virial and size conventions | alpha_g = 5/3 (2012ApJ...760L..25E); clump radius r = 1.91 sigma_x (2013ApJ...774...73I); 1/r density law (2025A&A...699L..11V) |
| Solar and planetary definitions | radius at 50% of quiet-Sun Tb, quiet Sun from a 120 x 120 arcsec disc-centre box (2019ApJ...871...45S); Titan disk split into 35 annuli to 1200 km (2025PSJ.....6..107N) |

## Geometry and literature numbers

| Input | Examples |
|---|---|
| Distance, with rescaling | GAIA distance adopted and literature scales adjusted (2017ApJ...848L..11K); 1.78 kpc (2020ApJ...904..181L); results kept in [D/1 kpc]^2 form (2019A&A...623A.153O) |
| Inclination, PA, systemic velocity fixed from earlier work | 2015A&A...584A..16P (fixed in MCMC), 2014Natur.511..567J (from scattered light), 2021A&A...645A..21G (i = 35 deg, PA 320 deg, vsys 1994 km/s) |
| Stellar or galaxy models | MGE light model (2019MNRAS.485.4359S); stellar mass fixed from the literature (2012ApJ...757..129R, 2013ApJ...774...16R) |
| Molecular data | LAMDA collision rates (2012ApJ...757..129R, 2014A&A...563A.113V); CDMS and JPL (2014A&A...568L...5C) |
| Single-dish flux for recovered-flux checks | 2012A&A...538L...9H, 2014A&A...570L..14R, 2015A&A...576L..15O (850 Jy km/s) |
| Catalogue values the analysis takes as fixed | redshifts and magnifications (2024ApJ...965..108U); deboosted single-dish fluxes and counterparts (2013ApJ...768...91H) |

## Statistical corrections inherited in survey series

| Correction | Examples |
|---|---|
| Completeness, flux boosting, spurious fraction for counts | 2014ApJ...795....5O (from an earlier count paper), 2013ApJ...768...91H, 2015A&A...584A..78C (alternative boosting correction) |
| Completeness by S/N from simulations | 2021ApJ...908..192S (47% at S/N 4.0, 80% at 5.0) |
| Redshift-uncertainty reliability from line-search simulations | 2018MNRAS.481.1976Z |
| Good-map selection rule (rms < 0.6 mJy/beam, axis ratio < 2) from the survey paper | 2014ApJ...780..115D |

If a series paper quotes corrected numbers, rebuild the correction from the earlier paper (often by artificial
source insertion and recovery) before comparing raw counts or fluxes; otherwise compare uncorrected to
uncorrected and say so.
