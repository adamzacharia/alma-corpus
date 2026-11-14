# Per-paper parameters: polarization and magnetic fields

All values are from the evidence pack (`skills/packs/polarization-magnetic-fields.md`), key-parameter, assumption
and excerpt lines. Entries marked "card" come from the paper's methods card.

## Calibration and imaging

| Paper | Setting |
|---|---|
| 2016ApJ...824..132N | `gaincal` KCROSS and XYf+QU, `qufromgain`, `polcal` D-terms on J1337-1257; repeat with 3C 279 agrees within 0.5% (typically 0.1-0.3%); absolute EVPA accuracy 0.4 deg (derived for this dataset from a 2 deg misalignment over 29 antennas) |
| 2020ApJ...895...64L | Tsys/WVR, bandpass, `qufromgain`, XYf+QU, `xyamb`, `polcal`; reference antenna DV06 then DA64; cross-hand delay from the strongest-polarization scan; robust 0.0; residual calibrator polarization ~0.1%; extra 1-sigma systematic ~0.09% of Stokes I |
| 2019ApJ...878L..26L | leakage calibrator with ~90 deg parallactic coverage; D-terms ~1%; XX/YY gain ratio within ~2% of unity; Q/U fitted with Stokes I position and beam fixed; 1e5 Monte Carlo draws for P |
| 2024ApJ...975..103P | `polcal` D-terms; `tclean` nterms=2, cell 0.2", robust 1; `immath` POLI/POLA; `imfit` elliptical Gaussians; `rmfit` with 6 mJy/beam (3 x rms) threshold, no systematics included |
| 2024A&A...686A.274V | ALMA polarization scripts after re-normalisation fix; CASA 5.7.2; phase self-cal solint 'inf' then 'int'; robust 0.5; >5 sigma_P detections |
| 2023Natur.621..483G | pipeline plus polarization script; clean threshold 10 uJy; P/sigma_P >= 3; 0.1% MDP added in quadrature |
| 2020ApJ...893...33L | natural weighting; MDP 0.1%, systematic 0.03%; vectors at P/sigma_P >= 3 |
| 2018A&A...616A..56A | common uv range 27-1310 klambda for Bands 3, 6, 7; vectors at PI S/N = 5 |
| 2018ApJ...864...81O | robust 0.5; sigma_PI = 2.9e-5 Jy/beam; fraction only above 3 sigma_PI; mean angle error ~2.5 deg |
| 2016ApJ...831L..12K | robust 0.5; multiscale at angular scales 0, 0.3, 0.9" (convert to pixels for CASA `scales`); Stokes V rms 25.2 uJy near thermal; sigma_PI = 42.8 uJy/beam |
| 2018ApJ...859..165S | PB-corrected I, Q, U, V; PI/sigma > 4; sigma_PI ~ sigma_Q ~ sigma_U; 0.1% 1-sigma fraction uncertainty |
| 2020ApJ...893...54Y | robust +0.5; 0.1" pixels; I and PI S/N > 3; orientation errors <~9 deg |
| 2025ApJ...992..103Z | robust 0.5; 3 sigma cutoff on Stokes Q and U (not on PI); sigma_PA = 28.65 deg sigma_p/I_p, I_p = polarized intensity |
| 2019A&A...626A..36D | S/N > 4; inner third of primary beam; sigma_psi from circular-mean variance |
| 2020A&A...640A.111A | robust 0.5, Hogbom; inner third of primary beam; 52 cores, 29 with polarization |
| 2020A&A...644A..11L | robust 1; four phase-only self-cal rounds; 4 pixels per beam; S with n = 8 neighbours and lag ~half a beam; no PB correction for statistics |
| 2019ApJ...884...48C | robust 0.5; final self-cal solint 90 s |
| 2020ApJ...892..152H | robust 2.0, 0.5, -0.5; 4 self-cal rounds |
| 2018ApJ...861...91H | robust -2 for the high-resolution VLA 1623 image; sources outside inner third of PB flagged unreliable |
| 2017A&A...603A..92V | lines robust 0.5, continuum robust -0.5; Monte Carlo of 1000 random D-term sets for Stokes V |
| 2019ApJ...884L..58U | per-SPW Stokes maps; phase-calibrator polarization stable to <0.02%; angle by atan2 |
| 2020ApJ...899..152H (CARMA) | MIRIAD `xyauto` for R-L phase, `gpcal options=qusolve` for leakage, `impol` debiasing |

## Mechanism and grain-size modelling

| Paper | Setting |
|---|---|
| 2018A&A...616A..56A | beta = alpha - 2 (thin, Rayleigh-Jeans); radiative alignment fit i = 48 deg, PA = 138 deg (+-15); DustPol at 343 GHz, i = 55 deg, k grid, best k = 3, mean residual 23.4 deg (sigma 7.5) |
| 2018ApJ...864...81O | 0.87 mm field as proxy for 140 um radiation; i = 27 deg, PA = 341 deg; pixels above 10 sigma |
| 2016ApJ...831L..12K | RADMC-3D, compact spherical grains, slope -3.5, a_max ~150 um (reported constraint ~40-300 um), T 36 K, i 27 deg |
| 2018ApJ...860...82H | MRN a^-3.5, a_min 0.25 um, ice/organics/silicates 62/30/8%; a_max 61 um best, 50 and 70 um tested |
| 2024ApJ...963..134Y | a_max 140 um, a_min 0.1 um; 1.6e8 photons; only self-scattering |
| 2019MNRAS.482L..29D | natural weighting; scattering only, multiple scattering included; a_max ~100 um |
| 2019MNRAS.483.2371Y | radiative alignment test in Band 3; p0 = 2%, i = 46.72 deg; thin disk, radial radiation flux |
| 2020A&A...634L..15G | perfect alignment of compact astrosilicate grains; b/a = 1.1 or 0.9 |
| 2025ApJ...990..183U | scattering polarization roughly C P90 omega_eff (effective albedo) with C ~ 0.02, used only as an MCMC prior (emcee); composition preference within 40 au partly prior- and optical-depth-driven; constant filling factor, smooth gas disk |
| 2024NatAs...8.1148U | 1e9 photon packages for ALMA polarization models |
| 2020ApJ...893...54Y | optical-depth check: peak T_b 30 K vs T_dust 67 K; models scored by segments within 30 deg |

## Field strength

| Paper | Inputs and result |
|---|---|
| 2020ApJ...896..157H | DCF on SiO v=0 J=2-1 angles: I, Q, U convolved with a 0.5" Gaussian, low-resolution angle map subtracted from the 0.1" map; delta phi = 4 deg, Delta V ~ 10 km/s (width convention not stated in pack), n = 1e6 cm^-3 adopted to satisfy the maser-pumping model, correction 0.5; B_pos 23 mG, total ~30 mG via the statistical 4B/pi factor |
| 2020ApJ...893...33L | B0 ~ sqrt(8 pi rho) sigma_v / alpha; sigma_v = 10 km/s, alpha = 5 +- 2 deg, rho = 1.4e-22 g cm^-3; B = 0.67 mG (upper limit); B_t/B_0 = 0.062 +- 0.025 |
| 2024A&A...686A.274V | structure function (Koch et al. 2010) within ~2"; delta ~300 au, Delta' ~500 au, W1 ~40 au, N ~1.2; B_t/B_0 = 0.061 +- 0.001; ~19 mG at 250 au; lower limit if field not frozen in |
| 2019ApJ...884...48C | DCF and two variants; EVPA standard deviation; >= 10 independent Nyquist points per region; sigma_v from H13CO+ with Kolmogorov extrapolation (n = 0.36) |
| 2019A&A...626A..36D | DCF and structure function; order-of-magnitude only; xi = 0.5 and n = 1e6 cm^-3 for MM4 and MM8 (card, section 4.5.1) |
| 2019ApJ...879...25K | DCF called very rough; F = 91 mJy, D = 300 pc, kappa = 0.01 cm^2/g, T_d = 30 K; trans-sonic sigma assumed; background field from Q, U smoothed with a beam 3x larger along both axes, dispersion 10 deg (card) |
| 2018NatCo...9.4636L | Delta v_los ~15 km/s; Delta phi ~30 +- 20 deg; n_H2 >~ 2e6 cm^-3 |
| 2018MNRAS.477.2760M | sigma_theta ~0.38 rad; v_turb 0.1-1 km/s |
| 2017ApJ...847...92H | sigma_v ~0.8 km/s from 13CS |
| 2020ApJ...899...55A | sigma_phi ~ sigma_psi, M_A ~ sigma_psi |

## Zeeman and line polarization

| Paper | Inputs and result |
|---|---|
| 2021ApJ...908..141H | CN 2-1, robust 0.5, 0.25 km/s channels; `gofish` Kepler shift (i = 35.3 deg, 126 pc, 1.25 Msun); joint fit V_j = C1 I_j + C2 dI_j/dnu + 0.5 B Z_j dI_j/dnu over unblended hyperfine parts j; B = B_LOS; 3-sigma limits 5.0 and 4.2 mG |
| 2019A&A...624L...7V | CN in TW Hya; robust 0.5; low inclination so sensitive mainly to B_z |
| 2017A&A...603A..92V | SiO masers: z ~ 1500 s^-1 G^-1; B cos(theta) ~2.4 G; grain-alignment lower limit B > 13 mG |
| 2020ApJ...896..157H | V = b dI/dnu with g Omega/2pi = 230 Hz/G; implied ~10 G judged implausible, opposite signs in J=1-0 and 2-1: Zeeman interpretation rejected |
| 2024A&A...686A.274V | PORTAL on LIME; turbulent velocity 1 km/s; extended-line Stokes V dominated by beam effects |
| 2020ApJ...899..152H | G-K model, uniform field and velocity gradient slab; predicted m_l ~3% matches CO in R Crt |

## Compact synchrotron sources

| Paper | Inputs and result |
|---|---|
| 2024ApJ...975..103P | RM from linear EVPA vs lambda^2 over four SPWs (single screen, same opacity assumed; n-pi handling not stated; no systematics in `rmfit`); core RM (4.5 +- 0.4)e4 rad m^-2; core fraction 0.88 +- 0.08% |
| 2019MNRAS.489..470G | 2D Gaussian fits on natural-weighted maps; 3 sigma detections; log-normal fraction A = 0.86, mu = 2.05, sigma = 0.97; median 2.2 +- 0.6% at 97.5 GHz |
| 2016A&A...593A..44L | XX/YY ratio vs parallactic angle, Q offset fitted; Sgr A* ~14 +- 1.2% at PA 158 +- 3 deg (Stokes U undetermined) |
| 2016A&A...593A..61M | dual differential polarimetry; differential RM can be biased by up to ~30% |
| 2018ApJ...868..101B | baselines < 50 klambda rejected; largest RMs suspect from phase wraps |
| 2019A&A...621A..18M | poor parallactic coverage in Bands 7/8 limits RM; EVPA variability can mimic RM |
