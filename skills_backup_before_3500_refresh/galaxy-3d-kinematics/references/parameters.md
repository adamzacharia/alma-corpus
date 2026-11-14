# Parameter settings by paper (galaxy-3d-kinematics)

Every row is a setting quoted in the evidence pack for this technique. Use it to pick defaults that match a
paper with similar data (resolution, tracer, redshift) and to cite them.

## Geometry

| Setting | Value | Paper |
|---|---|---|
| Centre | fixed to 1.2 mm continuum; PV slit 0.45" wide | 2021A&A...655A..25Z |
| Centre | AGN position; final PA = 289 +/- 5, i = 41 +/- 2 deg | 2014A&A...567A.125G |
| Centre | AGN; PA = 120, i = 41 deg fixed in Barolo | 2019A&A...632A..33A |
| Centre | AGN; V_sys fixed 4920 km/s; initial i = 45, PA = 128 | 2020ApJ...898...75I |
| Centre | continuum peak; 60 rings of 0.15" (~19 pc) | 2024A&A...686A..46E |
| Centre | continuum centroid; PA = 330, i = 30 deg fixed; 8 rings 1.5" apart; free v_circ, V_sys, dispersion | 2020A&A...641A.151S |
| Centre | AGN position and V_sys fixed; v_rot, v_rad, sigma, PA, i, H free, then PA/i Bezier-fixed | 2019A&A...632A..61G |
| Centre | AGN position of the unresolved 1.3 mm component | 2019A&A...628A..65A |
| Centre | dynamical centres assumed at the AGN positions (kinemetry) | 2021A&A...652A..98G |
| Centre | CO intensity peak; Delta chi2_nu = 1 confidence limit | 2019MNRAS.482.1499M |
| Centre | [CII] Gaussian peak; V_sys = 0; radius 0.35" | 2019ApJ...887...40W |
| Centre and axis ratio | fixed from Sersic fit; ring width half beam; 75% pixel sampling | 2021ApJ...908..231M |
| Centre prior | Gaussian, sigma 1"; uniform Vmax 0-600, sigma 0-200 km/s, r_e 0-2", r_t 0-1" | 2025MNRAS.536.3757A |
| Inclination | 44 deg from GALEX UV | 2021A&A...655A..25Z |
| Inclination | 76.3 deg from dust-lane models | 2019A&A...622A..89V |
| Inclination | 22 deg from literature, fixed (Halpha ring model, not ALMA) | 2024A&A...684A..24P |
| Inclination | i = arccos(q), q = 0.53 from F150W, 57.9 deg; i then left free in 3DBarolo | 2025NatAs...9.1553F |
| Inclination | K-band b/a, q0 = 0.14, 10% error, 3 sigma range; i a free parameter | 2019MNRAS.482.1499M |
| Inclination | 59 +/- 14 deg from axis ratio | 2019ApJ...887...74F |
| Inclination | i = arccos(b/a); D = 1.5 x FWHM major axis | 2024ApJ...968....9W |
| Inclination | Gaussian prior (37, 3 deg) | 2020MNRAS.496.4061D |
| Inclination | free over MGE-allowed range | 2020ApJ...892...68N |
| Inclination | 65 deg chosen (monotonic RC); 53 deg gives same conclusions | 2020ApJ...895..135K |
| Inclination | 32, 37, 27 deg assumed for three AGN hosts | 2020A&A...636A..37D |
| Inclination | 60-90 deg range from residual maps | 2018MNRAS.476.3956T |
| Intrinsic thickness q0 | 0.13 | 2017ApJ...851..126V |
| Intrinsic thickness q0 | 0.14 | 2019MNRAS.482.1499M |
| Intrinsic thickness q0 | 0.2 | 2019A&A...624A.138Y, 2025A&A...700A.165B |
| PA | fixed at 352.3 deg (rotcur) | 2017MNRAS.465.4390B |
| PA | fixed at 28 deg; 20 shells for CO(2-1) | 2025A&A...701A.113M |
| PA | -74.35 deg from 2MASS K_s imfit | 2020ApJ...901..151S |
| PA / i | PA = 314, i = 57 deg fixed in final 3DBarolo run; delta r = 0.3" | 2021A&A...656A..60A |

## Rings and radial grid

| Setting | Value | Paper |
|---|---|---|
| Ring width | beam, then half beam; R_t limited to 0-25 kpc; v_exp = 0 | 2019ApJ...871...85L |
| Ring width | (0.5-1.0) x PSF FWHM; AZIM normalisation; free V, sigma, PA, i | 2025NatAs...9.1553F |
| Ring width | 0.25"; local normalisation | 2024ApJ...969..122Y |
| Ring width | 0.1" (0.84 kpc) | 2018ApJ...864L..11X |
| Ring width | five rings of 0.1" centred 0.15"-0.55" | 2017ApJ...845..138S |
| Ring width | 50 rings, dr = 0.05" from 0.10" | 2020ApJ...898...75I |
| Ring width | 15" (HI); weighting abs(cos theta)^2 for rotation fits, sin^2 phi for the V_rad fit | 2024A&A...690A.169L |
| Ellipses | 28 ellipses 0.5"-24" (kinemetry) | 2014A&A...567A.125G |
| Ellipses | 32 ellipses 0.25"-8.25", step 0.25" (kinemetry) | 2021A&A...652A..98G |
| Ellipses | 1.2" ring width (kinemetry); other widths similar | 2017ApJ...843..136E |
| Ellipses | COVER = 0.50; 100 ellipses initially; spacing set by beam | 2019MNRAS.487..444R |
| Radii | 103 radii, 2-210 pc (3DBarolo); 20 radii 10-210 pc (kinemetry) | 2019A&A...632A..61G |
| Shells | shell width = PSF FWHM; thin disc below PSF | 2025A&A...701A.113M |

## Disk structure

| Setting | Value | Paper |
|---|---|---|
| Scale height | 0.2 x max radius; sigma_v grid 5-145 km/s | 2017ApJ...850..180J |
| Scale height | thin disk z0 = 100 pc for CO | 2024A&A...690A.169L |
| Scale height | h_z = 150 pc fixed | 2016ApJ...823...68S |
| Scale height | h_z = 317 pc; pixel 0.06" = 5 pc | 2019A&A...632A..33A |
| Scale height | exponential, h = 0.04" ~ 300 pc | 2018MNRAS.479.5440L |
| Scale height | h_z = 0.15 R_1/2 (thick disk) | 2025MNRAS.536.3757A |
| Scale height | Gaussian z_h < 1.3 pc (1 sigma) | 2020MNRAS.496.4061D |
| Dispersion | initial 10-40 km/s tested; data binned to 40 km/s | 2019ApJ...870...39V |
| Dispersion | first guess 50 km/s, v_rot 80 km/s (nuclear disc) | 2021A&A...655A..25Z |
| Dispersion | fixed at 2.2 km/s | 2018MNRAS.473.3818D |
| Dispersion | inclination 65, PA 210 deg, dispersion 15 km/s, scale height 4" | 2016ApJ...832..142Z |
| Rotation curve | Bertola A = 200 km/s, p = 1.5 | 2019A&A...621A..83S |
| Rotation curve | Bertola, 1 <= p <= 3/2 | 2021A&A...656A..60A |
| Rotation curve | Vmax = 165 km/s from Tully-Fisher; r_t free (2.4 kpc) | 2025ApJ...988...72S |
| Rotation curve | linear rise to 150 km/s at 0.1", then flat | 2016ApJ...816...37V |
| Free parameters | I0, R_D, i, PA, centre (3), v_max | 2016ApJ...820L..39N |
| Free parameters | 9 or 10 | 2020Natur.581..269N |
| Free parameters | 10 | 2019ApJ...876...91H, 2025MNRAS.536.3757A |
| Free parameters | 11 | 2025MNRAS.541.2540Z |
| Vertical velocity | scanned at 0, 25, 50, 100, 150 km/s | 2019A&A...632A..61G |
| Bar | PA 0 deg, ellipticity 0.42; Omega = 120 km/s/kpc, lambda = 0.2 | 2019A&A...621A..83S |

## Sampling and noise

Chain lengths and burn-in fractions are what individual papers ran, not defaults. Ensemble steps x walkers,
single-chain iterations and retained samples are different units. Pair any chain with a stated convergence
check. The rms inflation factors are empirical treatments of correlated pixels, and N is counted differently:
fitted pixels (2025ApJ...992..211N, 2020MNRAS.496.4061D) versus degrees of freedom (2019ApJ...883..193N).

| Setting | Value | Paper |
|---|---|---|
| Chain | 3e6 iterations, 20% burn-in (after a 1e5-iteration wide fit) | 2020ApJ...892...68N |
| Chain | 1e5 iterations, 20% burn-in; log MBH; rms x (2N)^0.25, N = 76,014 | 2025ApJ...992..211N |
| Chain | 300,000 steps, 10% burn-in; rms x 12.47 for N = 12,112 | 2020MNRAS.496.4061D |
| Chain | 2e5 steps, first 1e4 discarded | 2025MNRAS.541.2540Z |
| Chain | 50 walkers, 1000 steps | 2020A&A...637A..84P |
| Chain | 30,000 samples, uniform priors | 2025A&A...700A.285W |
| Chain | 1e5 realisations | 2014A&A...565A..59D |
| Chain | Metropolis-Hastings, first 40% discarded; five starting points | 2016ApJ...820L..39N |
| Errors | residual < 9 + chi2_min after rms x (2N_dof)^(1/4) | 2019ApJ...883..193N |
| Errors | max of rotcur error, channel width, V abs(sin i - sin(i +/- di)) | 2017ApJ...850..180J |
| Errors | weighted standard deviation over rings | 2017ApJ...845..138S |
| Pixels fitted | S/N >~ 3 | 2019MNRAS.489.1927S |
| Channels fitted | 1900-2800 km/s above 5 sigma | 2020ApJ...895..135K |

## Dynamical mass conversions

| Estimator | Value / assumption | Paper |
|---|---|---|
| M_dyn = 2.32e5 V^2 R | R = 3 exponential scale lengths; spherical; nominal mass kept, 30% uncertainty included for the spherical assumption | 2020Natur.581..269N |
| M_dyn = 1.16e5 v_circ^2 D | v_circ = 0.75 FWHM / sin i, i = 55 deg | 2019ApJ...882...10N |
| M_dyn = 1.16e5 v_circ^2 D | v_circ = 0.75 FWHM / sin i; D = 1.5 a_maj | 2018PASJ...70...36I |
| M_dyn = 1.16e5 V_cir^2 D | V_cir = 1.763 sigma / sin i; sin i = 0.45-1 | 2015Natur.522..455C |
| M_dyn(<r_1/2) = 5 sigma^2 r_1/2 / G | spherical; two resolved sources; M_DM = 0.25 M_dyn; gas = M_dyn - half M_star - M_DM within r_1/2 | 2015ApJ...812L..23S |
| M_dyn = C r_1/2 sigma^2 / G | C = 3.4 for a rotation-dominated system; r_1/2 = deconvolved major axis; C uncertainty (up to x2) not in the error | 2020MNRAS.493.4294B |
| Assumed size | R = 4 kpc for unresolved quasars (assumption, not a measurement) | 2017MNRAS.465.4390B |
| M_dyn (sin i)^2 = 1.94e5 v_FWHM^2 r_1/2 | not inclination-corrected | 2017ApJ...851..145M |
| M_dyn = 230 r v^2 (sin i)^-2 | r in pc; i = 45 deg, FWHM ~200 km/s | 2015ApJ...811...39I |
| M = R(k1^2 + 3 sigma^2)/G | k1 = first (rotation) harmonic coefficient; HCN sigma assumed from symmetric macroscopic motions | 2015ApJ...806L..34F |
| V_circ at 2 r_e, asymmetric drift | M_dyn within 10 kpc | 2025MNRAS.536.3757A |
| v_rot and sigma in quadrature | rotation (not dispersion) corrected for i = 50 deg for the upper value | 2015ApJ...806...17R |
| v_c,proj = 0.75 delta v | thin uniform disk | 2020A&A...636A..37D |
| <v_rot> = (pi/2) v_obs | inclination average | 2018ApJ...867..140L |
| <sin i> = pi/4 | random orientation | 2024ApJ...961..120C |
| Rotation-dominated | v_proj / 2 sigma_int > 0.4 | 2024ApJ...968....9W |
| Radial mass flow | Mdot = 2 pi R Sigma_HI V_rad x 1.33 (helium, HI-only Sigma); optically thin HI; V_rad fit with other parameters fixed, sin^2 phi weighting | 2024A&A...690A.169L |
