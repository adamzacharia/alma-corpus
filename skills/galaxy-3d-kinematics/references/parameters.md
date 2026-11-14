# Parameter settings by paper (galaxy-3d-kinematics)

Every row is a setting quoted in the evidence pack for this technique, unless marked "(card)": those come verbatim
from the paper's card because the pack lists the paper only bibliographically. Use the tables to pick defaults that
match a paper with similar data (resolution, tracer, redshift) and to cite them. Counts are my own counts of
distinct papers in the pack's key-parameter, assumption and excerpt lines; the membership is listed with each count.

## Geometry

Centre fixed to the continuum or AGN position, 17 papers: 2021A&A...655A..25Z, 2014A&A...567A.125G,
2019A&A...632A..33A, 2020ApJ...898...75I, 2024A&A...686A..46E, 2021A&A...652A..98G, 2019A&A...628A..65A,
2020A&A...641A.151S, 2019A&A...632A..61G (step 6), 2025A&A...699A..83A, 2025A&A...693A.174E, 2017ApJ...845L...5I,
2021ApJ...914...36I, 2022A&A...665A.107T, 2022MNRAS.512.2371H, 2018ApJ...863L..16M, 2018ApJ...859..144A. The pack
gives no denominator, so this is a count of examples.

Inclination from external data (SKILL.md counts):
- Fixed (2): 2021A&A...655A..25Z (44 deg from GALEX UV, second run), 2019A&A...622A..89V (76.3 deg from dust lanes).
- Prior or bounded range with i free (2): 2020MNRAS.496.4061D (Gaussian 37, 3 deg), 2019MNRAS.482.1499M (K-band
  b/a, q0 = 0.14, 10% error, 3 sigma range).
- Start only (3): 2025NatAs...9.1553F (i = arccos(q) = 57.9 deg, then i free in 3DBarolo), 2021A&A...654A..37D
  (45 deg, allowed 10-80 deg), 2021MNRAS.503.5583B (45 deg, allowed 10-80 deg).

| Setting | Value | Paper |
|---|---|---|
| Centre | AGN; PA = 120, i = 41 deg fixed in Barolo | 2019A&A...632A..33A |
| Centre | AGN; V_sys fixed 4920 km/s; initial i = 45, PA = 128 | 2020ApJ...898...75I |
| Centre | continuum peak; 60 rings of 0.15" (~19 pc) | 2024A&A...686A..46E |
| Centre | continuum centroid; PA = 330, i = 30 deg fixed; 8 rings 1.5" apart; free v_circ, V_sys, dispersion | 2020A&A...641A.151S |
| Centre | continuum peak; SEARCH 5 sigma / 3 sigma; v_rad = 0 | 2022MNRAS.512.2371H |
| Centre | CO intensity peak; Delta chi2_nu = 1 confidence limit | 2019MNRAS.482.1499M |
| Centre | 2D Gaussian fit to moment 0 (NGC 4845); flux-weighted centroid (NGC 4968) | 2021A&A...654A..24B |
| Centre | 2D Gaussian fit to moment 0; Smooth & Search 3 sigma | 2026A&A...707A.252K |
| Centre, PA | imfit; VROT, VDISP, INC, Z0 free | 2025MNRAS.538.3001T |
| Centre and axis ratio | fixed from Sersic fit; ring width half beam; 75% pixel sampling | 2021ApJ...908..231M |
| Centre prior | Gaussian, sigma 1"; uniform Vmax 0-600, sigma 0-200 km/s, r_e 0-2", r_t 0-1" | 2025MNRAS.536.3757A |
| Centre etc. free | kinematic centre, PA, i, V_sys, V_rot, sigma free in the 0.2" cube | 2025PASJ...77..432U |
| Initial guesses | x0, y0, V_rot, V_sys from SEARCH; i from b/a; sigma 30-150 km/s | 2024ApJ...977..161V |
| Initial guesses | vrot 330, vdisp 37 km/s, inc 47, pa 115 deg | 2025MNRAS.537.1163A |
| Inclination | i = arccos(b/a); D = 1.5 x FWHM major axis | 2024ApJ...968....9W |
| Inclination | 65-68 deg from 3DBarolo (MCG-06-30-15); 60 deg from outer-ring ellipse (NGC 4968) | 2021A&A...654A..24B |
| Inclination / PA | fixed 40 +/- 10, 170 +/- 10 deg (AzTEC/C159); 75 +/- 10, 145 +/- 5 deg (J1000+0234) | 2021A&A...647A.194F |
| Inclination / PA | initial values from the literature | 2024ApJ...976..201F, 2025A&A...699A..83A |
| Inclination / PA | fixed or free ring by ring, both presented | 2024ApJ...968...87K |
| PA | fixed at 352.3 deg (rotcur) | 2017MNRAS.465.4390B |
| PA / i / V_sys | fixed after the first run (PA = 320, i = 35 deg, V_sys = 1194 km/s) | 2018ApJ...859..144A |

Intrinsic thickness q0 for axis-ratio inclinations, 10 papers: 0.1 (2018ApJ...863...56C), 0.13
(2017ApJ...851..126V), 0.14 (2019MNRAS.482.1499M, 2020A&A...643A..78M), 0.15 (2018Natur.560..613T), 0.2
(2019A&A...624A.138Y, 2025A&A...700A.165B, 2024ApJ...977..161V, 2025MNRAS.538.3001T), 0.25 (2025ApJ...988..182N).

## Rings and radial grid

Beam-based ring-width rules, 20 papers. A paper with stage-specific widths is listed in each group it uses, so the
group sizes add to more than 20.
- About half a beam at some stage (9): 2023A&A...672A.106L (sqrt(a b)/2), 2024ApJ...977..161V (RADSEP =
  sqrt(theta_x theta_y)/2, near-Nyquist), 2021ApJ...908..231M (half beam FWHM), 2025A&A...696A..88W (half the beam
  major axis), 2022MNRAS.512.1012C (half-beam increments), 2025A&A...693A..91L (0.09", half the beam),
  2025PASJ...77..432U (0.097", half the resolution element, 0.2" cube; 0.35", 40% of it, 0.9" cube),
  2019ApJ...871...85L (second stage), 2022ApJ...934..173S (second stage).
- Beam/2.5 or 0.4 beam along one axis (5): minor axis in 2021A&A...654A..37D (ring width), 2021MNRAS.503.5583B
  (minimum width), 2022MNRAS.510.3734D (0.4 x minor axis, minimum width), 2024ApJ...970...30M (minimum ring radius);
  major axis in 2026A&A...707A.252K (0.0138" = theta_maj / 2.5).
- About one beam at some stage (7): 2022MNRAS.516.4066L (0.186" = sqrt(a b), "fully independent"),
  2022NatCo..13.4574G (minor-axis FWHM), 2025A&A...701A.113M (shell = PSF FWHM), 2024ApJ...976..201F (beam FWHM, for
  optical IFU data), 2025NatAs...9.1553F (0.5-1.0 x PSF FWHM), 2019ApJ...871...85L (first stage),
  2022ApJ...934..173S (first stage).
- Spacing set by the beam without a stated factor (1): 2019MNRAS.487..444R (kinemetry).

| Setting | Value | Paper |
|---|---|---|
| Ring width | 0.0138" (CO, source plane) | 2026A&A...707A.252K |
| Ring width | 0.025" | 2025MNRAS.537.1163A |
| Ring width | 0.06", 20 rings to 1.2" | 2025MNRAS.537..520Z |
| Ring width | 0.06", 9 rings | 2021Sci...371..713L |
| Ring width | 0.1" (0.84 kpc) | 2018ApJ...864L..11X |
| Ring width | 0.1", 6 rings | 2021ApJ...914...36I |
| Ring width | 0.12" and 0.55" (two galaxies) | 2021A&A...654A..24B |
| Ring width | 0.2" and 0.23" | 2021A&A...647A.194F |
| Ring width | 0.25"; local normalisation | 2024ApJ...969..122Y |
| Ring width | 0.3"-0.4" | 2022MNRAS.512.2371H |
| Ring width | 1.5" | 2020A&A...641A.151S |
| Ring width | 2" (CO(1-0), 5-7 rings) | 2023A&A...673A..46B |
| Ring width | 15" (HI); weighting abs(cos theta)^2 | 2024A&A...690A.169L |
| Ring width | 28.8" (HI) | 2025ApJ...980..126K |
| Radii | 50 rings, dr = 0.05" from 0.10" | 2020ApJ...898...75I |
| Max radius | 1.0 x deconvolved major-axis FWHM | 2021MNRAS.503.5583B |
| Max radius | morphological major-axis FWHM | 2021A&A...654A..37D |
| Max radius | 0.8 x CO FWHM major axis | 2024ApJ...970...30M |
| Max radius | 2 x major-axis FWHM | 2022NatCo..13.4574G |
| Ellipses | COVER = 0.50; 100 ellipses initially; spacing set by beam | 2019MNRAS.487..444R |

## 3DBarolo masks

14 papers state SEARCH / SMOOTH&SEARCH settings for a disk fit (2025NatAs...9..406L also does, for H2 surface
densities of clouds, and is left out).

| Mask | SNRCUT / primary | GROWTHCUT / secondary | Other | Paper |
|---|---|---|---|---|
| SMOOTH&SEARCH | 4 | 3 | FACTOR 1.5, MINCHANNELS 3 | 2023A&A...672A.106L |
| SMOOTH&SEARCH | 4 | 3 | FACTOR 1.8, MINCHANNELS 2 | 2025A&A...693A..91L |
| SEARCH | 4.5 | 4.5 | MINCHANNELS 3, 40 km/s bins | 2025PASJ...77..432U |
| SEARCH | 5 sigma clip | grown to 2.1 sigma | absolute THRESHOLD, MINCHANNELS 5, MINPIX 1 | 2024ApJ...977..161V |
| SEARCH | 3.5 | 3.0 | | 2021MNRAS.503.5583B |
| SEARCH | 3.0-3.5 | 2.0-3.0 | per source | 2023MNRAS.521.1045R |
| SMOOTH&SEARCH | 3 | 2 | FACTOR 1.5 | 2025A&A...701A.120P |
| SEARCH | 4.5 | 3.5 | >= 30 pixels, >= 2 channels | 2024ApJ...970...30M |
| SEARCH | 7 | 4 | MINCHANNELS 4 | 2025MNRAS.538.3001T |
| SMOOTH&SEARCH | 3 | | | 2026A&A...707A.252K |
| SEARCH | 3 | | | 2025A&A...693A.174E |
| SEARCH | 3.5 | 2.0 | | 2022NatCo..13.4574G |
| SEARCH | 3.5 | 2.0 | | 2022MNRAS.510.3734D |
| SEARCH | 5 | 3 | | 2022MNRAS.512.2371H |

## Normalisation, weighting and residual

9 papers: 2023A&A...672A.106L (NORM AZIM; WFUNC 0, then 2), 2025A&A...693A..91L (AZIM; WFUNC 2; FUNC 2),
2025MNRAS.537.1163A (local; wfunc 2; ftype 2), 2024A&A...690A.169L (|cos theta|^2), 2022ApJ...934..173S
(pixel-by-pixel; |cos theta|^2; |M - D|), 2025PASJ...77..432U (flux renormalised per pixel), 2025NatAs...9.1553F
(AZIM), 2024ApJ...977..161V (azimuthal), 2022MNRAS.516.4066L (cos theta). 2024A&A...690A.169L (card) switches to
sin^2 phi weighting for its separate V_rad run.

## Staged fits

| Paper | Sequence |
|---|---|
| 2023A&A...672A.106L | all seven ring parameters free, WFUNC=0; geometry fixed to the median over rings and lines; SPACEPAR V_rot-sigma grid (sigma 1-60 km/s); final run with only V_rot free, sigma fixed, WFUNC=2 |
| 2025A&A...693A..91L | centre fixed on the minor axis; 3DFIT for median V_sys, PA, i over 5 rings; SPACEPAR (V_rot 200-450, sigma 1-200 km/s) on approaching, receding and both sides; final 3DFIT with sigma = 47 km/s |
| 2024ApJ...977..161V | TWOSTAGE true, REGTYPE bezier; FREE vrot vdisp pa inc |
| 2019A&A...632A..61G | AGN position and V_sys fixed; v_rot, v_rad, sigma, PA, i, H free, then PA and i fixed to a Bezier interpolation |
| 2022MNRAS.516.4066L | "twostage=true" and "polyn=0": all seven parameters free, then centre, V_sys, PA, i fixed to the mean over rings; second fit with V_rot, V_rad, sigma |
| 2021A&A...654A..37D | centre fixed; V_rot, sigma, V_sys, i, PA free; then V_sys, i, PA fixed to ring averages |
| 2022ApJ...934..173S | one resolution unit, geometry plus V_rot and sigma; then geometry fixed, half-unit rings |
| 2025PASJ...77..432U | 0.2" cube with geometry free; 0.9" cube with parameters fixed to the high-resolution medians; SPACEPAR for sigma |
| 2024ApJ...976..201F | centre, V_sys, V_rot, sigma, PA, i free; then only V_rot and sigma |
| 2025MNRAS.537.1163A | twostage = true, regtype = 1 |
| 2025MNRAS.537..520Z | TWOSTAGE = true, z0 = 0 |
| 2018ApJ...859..144A | PA, i, V_sys fixed after the first run |
| 2024A&A...690A.169L (card) | HI fit first; CO fit starts from the HI result with centre and V_sys fixed; i, PA, V_rot, sigma free, then geometry fixed; V_rad in a separate run with other parameters fixed |
| 2021A&A...655A..25Z | centre fixed; first run i and PA free; second run i fixed to 44 deg |

Ring acceptance: v_c > 3 dv_c, di < 50 deg, dPA < 50 deg (2017ApJ...850..180J); only rings above 3 sigma
(2017ApJ...845..138S); V_rot errors > 30 km/s dropped (2024A&A...690A.169L); points inside the beam dropped
(2024ApJ...977..161V, < 1.55 kpc; 2022ApJ...934..173S, central resolution element); radii beyond 3 beams only
(2020A&A...643A..78M); innermost and outermost points dropped (2024ApJ...976..201F).

## Disk structure

Gas scale heights stated for the fitted gas disk, 13 papers:
- About 100 pc (6): 2023A&A...672A.106L (LTYPE 3, z0 = 100 pc), 2022MNRAS.516.4066L (100 pc, 0.25"),
  2025MNRAS.537.1163A (0.0138" = 100 pc), 2022ApJ...934..173S (100 pc), 2021MNRAS.503.5583B (0.01" ~ 100 pc),
  2024A&A...690A.169L (card: thin disk z0 = 100 pc for CO).
- 300 pc (4): 2025A&A...693A..91L, 2025PASJ...77..432U, 2021Sci...371..713L, 2018MNRAS.479.5440L (0.04" ~ 300 pc).
- Other (3): 2024ApJ...977..161V (0.1 R_1/2), 2025MNRAS.536.3757A (card: h_z = 0.15 R_1/2), 2025MNRAS.537..520Z
  (z0 = 0).

| Setting | Value | Paper |
|---|---|---|
| Scale height | 0.2 x max radius; sigma_v grid 5-145 km/s | 2017ApJ...850..180J |
| Scale height | h_z = 150 pc fixed | 2016ApJ...823...68S |
| Scale height | 150 pc, weighting abs(cos theta) | 2017PASJ...69...83M |
| Scale height | 0.01" (thin disk) | 2022NatCo..13.4574G, 2021A&A...654A..37D |
| Scale height | Gaussian z_h < 1.3 pc (1 sigma) | 2020MNRAS.496.4061D |
| Stellar scale height (not the gas disk) | h_z = 317 pc with stellar M/L = 0.5 (I band); pixel 0.06" = 5 pc | 2019A&A...632A..33A |
| Dispersion | initial guesses 10-300 km/s; channels 10.3 km/s | 2021A&A...647A.194F |
| Dispersion | initial 30-150 km/s ("arbitrarily set") | 2024ApJ...977..161V |
| Dispersion | initial = moment-2 maximum | 2021A&A...654A..37D |
| Dispersion | SPACEPAR sigma 1-100 km/s, steps 2 km/s; adopted 60 km/s | 2025PASJ...77..432U |
| Dispersion | constant 50 km/s (assumption) | 2023MNRAS.521.1045R |
| Dispersion | fixed 8 km/s, scale height 0 | 2024ApJ...968...87K |
| Dispersion | inclination 65, PA 210 deg, dispersion 15 km/s, scale height 4" | 2016ApJ...832..142Z |
| Rotation curve | arctan v(r) = (2/pi) v_inf arctan(r/r_t); v_inf = 540 km/s, r_t = 0.52 kpc | 2025PASJ...77..432U |
| Rotation curve | Vrot = Vmax (2/pi) arctan(R/Rt); centre, PA, i from CANNUBI | 2025A&A...701A.120P |
| Rotation curve | exponential disk, arctan, GalPak3D defaults | 2020MNRAS.493.3744F |
| Rotation curve | linear rise to 150 km/s at 0.1", then flat | 2016ApJ...816...37V |
| Rotation curve | flat, zero intrinsic dispersion | 2016ApJ...820L..39N |
| Free parameters | I0, R_D, i, PA, centre (3), v_max | 2016ApJ...820L..39N |
| Free parameters | 9 or 10 | 2020Natur.581..269N |
| Free parameters | 10 (card) | 2025MNRAS.536.3757A |
| Vertical velocity | scanned at 0, 25, 50, 100, 150 km/s | 2019A&A...632A..61G |

## Sampling and noise

Chain lengths and burn-in fractions are what individual papers ran, not defaults. Ensemble steps x walkers,
single-chain iterations and retained samples are different units. Pair any chain with a stated convergence check.
The rms inflation factors are empirical treatments of correlated pixels, and N is counted differently: fitted pixels
(2025ApJ...992..211N, 2020MNRAS.496.4061D) versus degrees of freedom (2019ApJ...883..193N).

| Setting | Value | Paper |
|---|---|---|
| Chain | 3e6 iterations, 20% burn-in (after a 1e5-iteration wide fit) | 2020ApJ...892...68N |
| Chain | 1e5 iterations, 20% burn-in; log MBH; rms x (2N)^0.25, N = 76,014 | 2025ApJ...992..211N |
| Chain | 300,000 steps, 10% burn-in; rms x 12.47 for N = 12,112 | 2020MNRAS.496.4061D |
| Chain | 3e5 steps, first 10% burn-in | 2019MNRAS.485.4359S |
| Chain | 200 walkers, 1000 burn-in, 2000 sampling iterations, a = 2 (mass model) | 2022MNRAS.516.4066L, 2021Sci...371..713L |
| Chain | 2e5 steps, first 1e4 discarded | 2025MNRAS.541.2540Z |
| Chain | 30,000 samples, uniform priors | 2025A&A...700A.285W |
| Chain | five starting points and runs for convergence (card) | 2016ApJ...820L..39N |
| Chain | acceptance fractions > 50% and corner plots checked | 2023A&A...672A.106L |
| Errors | residual < 9 + chi2_min after rms x (2N_dof)^(1/4) | 2019ApJ...883..193N |
| Errors | max of rotcur error, channel width, V abs(sin i - sin(i +/- di)) | 2017ApJ...850..180J |
| Errors | 3DBarolo 5% residual change; symmetric sqrt(delta_+ delta_-) | 2023A&A...672A.106L |
| Errors | residual < 1.05 of the minimum | 2022ApJ...934..173S |
| Errors | weighted standard deviation over rings | 2017ApJ...845..138S |
| Errors | bootstrap of 16 half-cube subsets with MPFIT | 2019MNRAS.485.4359S |

## Pressure support

Distinct, model-dependent estimators:
- Asymmetric-drift correction, V_c = sqrt(V_rot^2 + V_A^2), polynomial (degree <= 3) sigma profile, isotropic
  dispersion, constant scale height; ADC errors not propagated; eDIG makes it less accurate for low-EW(Halpha)
  galaxies (2022ApJ...934..173S). Isotropic dispersion also assumed in 2024ApJ...976..201F.
- V_circ corrected for asymmetric drift at 2 r_e, M_dyn within 10 kpc (2025MNRAS.536.3757A, card).
- M = R(k1^2 + 3 sigma^2)/G, k1 the first (rotation) harmonic; HCN sigma attributed to symmetric macroscopic motions
  (2015ApJ...806L..34F). Say whether k1 is deprojected.
- Rotation and dispersion in quadrature, rotation corrected for i = 50 deg for the upper value, dispersion not
  corrected (2015ApJ...806...17R).
- Not needed at V_rot/sigma_CO >~ 17-22 (2023A&A...672A.106L).

## Dynamical mass conversions

| Estimator | Value / assumption | Paper |
|---|---|---|
| M_dyn = 2.32e5 V^2 R | R = 3 exponential scale lengths = 4.2 kpc; spherical; nominal mass kept, 30% uncertainty for the spherical assumption | 2020Natur.581..269N |
| M_dyn = 1.16e5 v_circ^2 D | v_circ = 0.75 FWHM / sin i, i = 55 deg | 2019ApJ...882...10N |
| M_dyn = 1.16e5 v_circ^2 D | v_circ = 0.75 FWHM / sin i; D = 1.5 a_maj | 2018PASJ...70...36I |
| D = 1.5 x deconvolved size | i = 25, 50 deg; 55 deg and 3 +/- 1 kpc for J2348-3054 | 2016ApJ...816...37V |
| M_dyn(<r_1/2) = 5 sigma^2 r_1/2 / G | spherical; two resolved sources; M_DM = 0.25 M_dyn; gas = M_dyn - half M_star - M_DM within r_1/2 | 2015ApJ...812L..23S (card) |
| M_dyn = C r_1/2 sigma^2 / G, C = 3.4 | rotation-dominated system; r_1/2 = deconvolved major axis, 1.15 +/- 0.35 kpc; C uncertainty (up to x2) not in the error | 2020MNRAS.493.4294B (card for C) |
| M_dyn^disp = alpha sigma_v^2 r / G, alpha = 3.4 | dispersion-dominated systems; r and v of the outermost 3DBarolo ring; M_dyn^rot = v^2 r / G also computed | 2021A&A...654A..37D |
| K(n) K(q) virial estimator | K(n) = 8.87 - 0.831n + 0.0241n^2, K(q) = [0.87 + 0.38 exp(-3.71(1-q))]^2; q = 1, n = 1 gives an upper limit; virialized, dispersion-dominated | 2025ApJ...987L..37W |
| Unresolved sizes | masses are upper limits (dispersion) or lower limits (rotation) | 2025A&A...696A..88W |
| Assumed size | R = 4 kpc for unresolved quasars (assumption, not a measurement) | 2017MNRAS.465.4390B |
| R = 0.75 x CO FWHM major axis | thin disk, i = arccos(amin/amaj) | 2019ApJ...887...24T |
| <sin i> = pi/4 | random orientation | 2024ApJ...961..120C |
| factor 3/2 | reciprocal of the expectation of sin^2 i | 2026ApJ...997..218A |
| Rotation-dominated | v_proj / 2 sigma_int > 0.4 (card) | 2024ApJ...968....9W |
| Rotation support | V/sigma > 3 | 2024ApJ...977..161V |
| Radial mass flow | Mdot_HI = 2 pi R Sigma_HI V_rad x 1.33 (helium, HI-only Sigma); optically thin HI; V_rad fit with other parameters fixed, sin^2 phi weighting (card) | 2024A&A...690A.169L |
| Radial mass flow | Mdot = M_gas(R) V_rad(R) / R, an upper limit | 2022MNRAS.516.4066L |
