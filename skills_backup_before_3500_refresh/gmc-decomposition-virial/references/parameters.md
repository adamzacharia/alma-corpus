# Parameters: cloud decomposition and virial analysis

All values are from the evidence pack `C:\Users\adama\alma-corpus\skills\packs\gmc-decomposition-virial.md`.

## Virial mass coefficients (general practice, then what papers used)

General practice: for a sphere with rho ~ r^-k, M_vir = 3 (5 - 2k)/(3 - k) sigma^2 R / G, with sigma the 1D
Gaussian dispersion. With R in pc and sigma in km/s, G = 1/232 pc (km/s)^2 / Msun, so:

| Profile | M_vir with sigma | M_vir with FWHM dV (dV = 2.355 sigma) | Used by |
|---|---|---|---|
| uniform (k = 0) | 1160 R sigma^2 | 210 R dV^2 | 2018ApJ...856..147O, 2019ApJ...872..121U |
| r^-1 (k = 1) | about 1040 R sigma^2 | about 189-190 R dV^2 | 2020ApJ...892..147S, 2015Natur.525..218R (1044), 2018ApJ...857...19F (189), 2025A&A...699A.369V (190) |
| r^-1.8 | k-factor 1.16 in alpha = 3 k sigma^2 R / (G M) (an alpha_E-type form: 3k = 3.48 vs 5/a = 3.5, my arithmetic) | - | 2014ApJ...795L..25R |
| r^-1.5 | a = 5/4; alpha kept as 5 sigma^2 R/(G M) = 2a E_K/|E_G|, unbound above alpha_cr = 2a | - | 2020ApJ...894...87C |
| r^-1 (fixed scale) | alpha = 5 sigma^2 R/(f G M), f = 10/9 (alpha_E-type) | - | 2018ApJ...860..172S |

Normalization (general practice): a = (1 - k/3)/(1 - 2k/5); alpha_5 = 5 sigma^2 R/(G M) = a alpha_E with
alpha_E = 2E_K/|E_G|. Thresholds: alpha_E equilibrium 1, bound below 2; alpha_5 equilibrium a, bound below 2a.
Do not mix a profile-corrected alpha with the 2a threshold.

A r^-2 profile gives about 30% less mass than r^-1 (2017ApJ...846...73T).

## Segmentation settings by paper

| Paper | Code | Settings |
|---|---|---|
| 2025A&A...699A.369V | CPROPS ECLUMP | THRESH 3 sigma, EDGE 1.5 sigma, MINAREA 0.5 beams, MINPEAK 3 sigma, MINVCHAN 3, BOOTSTRAP 1000, /NONUNIFORM |
| 2018ApJ...857...19F | modified CPROPS | 4 sigma seeds, 2 sigma edge, local maxima in 15 pc x 15 pc x 2 km/s, SIGDISCONT 5, > 1 beam, peak > 1 K above merge |
| 2020MNRAS.499.2534K | CPROPS ECLUMP | mask > 4 sigma, edge 2.0-1.5 sigma |
| 2018ApJ...867..165B | cprops/cpropstoo | X_CO 4.35e20, brightness temperature ratio 0.82 |
| 2018PASJ...70...73H | astrodendro | peak S/N > 3, 3 sigma above merge, min pixels 3 beam areas, cube smoothed to 46 pc |
| 2017MNRAS.464L..31H | astrodendro | min_value 3 sigma, min_delta 1 sigma, min_npix 60 |
| 2017PASJ...69...18T | CLUMPFIND | threshold 8 sigma, increment 4 sigma, drop diameter < 1.4 arcsec |
| 2020ApJ...890...76N | CLUMPFIND | radius = geometric mean of semi-axes |
| 2018ApJ...860..172S | fixed scale | R = r_beam, line-of-sight depth about 2 r_beam, f = 10/9 |
| 2018ApJ...861L..18U | fixed scale | H = 100 pc; hydrostatic (median 122 pc) and virial cloud alpha_vir ~ 2 (median 116 pc) alternatives |
| 2020ApJ...892..147S | CASA imfit | 2D Gaussian on moment 0, R from geometric-mean sigma |

## Mass conversions by paper

| Paper | Conversion |
|---|---|
| 2018ApJ...857...19F | alpha_CO,MW 4.35, R21 0.7, R_H2/R_CO 1.2, metallicity from radial gradient |
| 2018PASJ...70...73H | X 2.0e20 with helium 1.36 (M = 4.4 L_CO) |
| 2012ApJ...760L..25E | X 3.0e20, no helium, I(2-1)/I(1-0) = 1.0 |
| 2025A&A...699A.369V | alpha_CO 8.4 applied to L_CO(1-0), R32/10 about 2 |
| 2024ApJ...966...51G | X(1-0) 2.4, X(2-1) 3 (unit scale not given in pack or card; verify before use), R21 0.8; N(H2)/N(13CO) = 3e6 for LTE |
| 2017ApJ...835..278S | alpha_CO 4.35, R21 = 1 |
| 2017PASJ...69...18T | [H2]/[13CO] 5.0e5, Tex 8.5 K |
| 2019ApJ...872..121U | X(H13CO+) 6e-11, X(C34S) 4.87e-10, Tex from RADEX |
| 2015MNRAS.449..715W | dust mass, gas 70 K, mu = 2.8 mH (per H2 convention) |
| 2020ApJ...894...87C | dust mass at 20 K, mu_p = 2.33 (per free particle) |
| 2020ApJ...890...76N | mu_H2 = 2.8 (per H2 molecule), Rgd = 100, k100GHz = 0.21 cm2/g |
| 2020MNRAS.499.2534K | result, not an input: X_CO = 5.5e20 +/- 4.6e20 from virial masses |
| 2015Natur.525..218R | result, not an input: alpha_CO about 28 +/- 28 from virial masses |
