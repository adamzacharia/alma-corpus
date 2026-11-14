# Radiative transfer modelling: longer parameter tables

Values come from the evidence pack (`skills/packs/radiative-transfer-modelling.md`), which quotes verified
methods cards. Where the pack lists a paper only in its bibliography, the value was checked against that
paper's methods card and is marked "(card)". Counts are my counts of pack lines unless marked "aggregate".

## Dust opacity at the observed band

Check whether a value is per gram of dust or per gram of gas (dust value / 100 at gas-to-dust 100).

| Band | Value | Composition / notes | Bibcode |
|---|---|---|---|
| 1.3 mm | 2.2 cm2/g | 30% amorphous C / 70% astrosilicate, 0.1 um-3 mm, a^-3.5 | 2018ApJ...859..111H |
| 1.3 mm | 2.2 cm2/g (kappa_abs) | 0.1 um-3 mm, a^-3.5 | 2020ApJ...889...59P |
| 1.3 mm | 2.2 cm2/g | V883 Ori disk | 2019NatAs...3..314L |
| 1.3 mm | 2.25 cm2/g | 70% silicate / 30% graphite, 5 nm-3 mm, a^-3.5 | 2017ApJ...836..223W (card) |
| 1.3 mm | 2.3 cm2/g | 1 um-1 cm, a^-3.5 | 2019MNRAS.488.1005P |
| 1.28 mm | 2.31 cm2/g | astrosilicate, 0.1-3000 um | 2019A&A...624A..33V (card) |
| 230 GHz | 2.3 (nu/230 GHz) cm2/g | with T_dust 20 K | 2025ApJ...989....1Z (card) |
| any | 10 (nu/1000 GHz) cm2/g (2.3 at 230 GHz) | Beckwith law, with gas-to-dust 100 | 2018MNRAS.474.4347C (card) |
| 1.3 mm | 1.1 cm2/g (kappa_abs) | astrosilicate, 1.3 um-1 cm (debris) | 2016MNRAS.460.2933M |
| 1.27 mm | ~1.3 cm2/g | astrosilicate, blowout size to 1 cm (debris) | 2020MNRAS.497.2811K |
| 1.3 mm | 3.95 cm2/g | HD 163296, adopted from an earlier study | 2018ApJ...857...87L (card) |
| 1.3 mm | ~0.95 cm2/g per dust mass | Semenov composite aggregate | 2017ApJ...835L..11T |
| 0.88 mm | 3.8 cm2/g (kappa_abs) | astrosilicate/amorphous C/ice 70/15/15%, 1 um-1 cm | 2017MNRAS.465.2595M |
| 885 um | 3.72 cm2/g | astronomical silicates, 0.05 um-1 mm | 2016ApJ...819..102V |
| Band 7 | 1.9 cm2/g | 70/15/15% mix, 1 um-1 cm | 2021AJ....161..271F |
| 340 GHz | 4.3 cm2/g | "DALI standard" | 2017A&A...599A.113M |
| 0.87 mm, 9.1 mm | 1.84, 0.13 cm2/g | beta = 1 | 2020ApJ...890..130T |
| 230 GHz | kappa0 = 0.01 cm2/g (per gas, g/d 100) | constant beta | 2015ApJ...808..102K |
| 1000 GHz ref. | 10 cm2/g, beta = 1 | used with factor 100 for gas | 2019A&A...623A.150V |
| Bands 7, 6 | 0.40, 0.17 cm2/g | astrosilicates 0.01-1 um (red supergiant) | 2019A&A...627A.114K |

Dust models named: DIANA (2024A&A...688A.102T (card), 2024ApJ...975..235V (card)), DSHARP
(2020ApJ...893..125U (card), 2024ApJ...971..129C (card), 2025ApJ...984L..19Y), Birnstiel et al. 2018
(2024ApJ...966...59S (card)), porous DHS grains with void fraction 0.8 (2019MNRAS.482L..29D (card),
2019NatAs...3.1109P (card), 2020MNRAS.492.1531M (card)).

## Grain size ranges

| Setting | Values | Bibcode |
|---|---|---|
| Smallest a_min | 0.001 um, a_max 1.0 um (AGB envelope) | 2022A&A...665A..82O |
| a_min 2 nm, a_max 10 um | polarization model, MRN | 2020A&A...644A..11L (card) |
| Searched a_min | 0.5-20.5 um grid (41 values), q 2.5-4.5, a_max fixed 10 mm | 2018ApJ...869...10M |
| Fixed regional a_max | 10 cm in the inner midplane only; surface layer 0.01-1 um | 2023MNRAS.518.6092L |
| a_max 3 cm | just outside the snowline | 2018MNRAS.477..325B |
| a_max 1 um | red supergiant envelope, 0.01-1 um | 2019A&A...627A.114K |
| Typical disk | 0.005 um-3 mm; 0.03-1000 um | 2025A&A...697A..64V; 2021AJ....161..238W |

## Disk gas chemistry and isotopologues

Every abundance carries a denominator. n_H = n(H) + 2 n(H2) is the density of H nuclei (2021A&A...647A..10G),
so in fully molecular gas n_H ~ 2 n(H2) and X(CO/H2) = 2 X(CO/H) (general practice). Mass ratios are kept apart
from number ratios.

| Setting | Values seen | Bibcodes |
|---|---|---|
| CO/H2 (disk, number) | 1e-4 | 2017ApJ...835...17M (card), 2018ApJ...854..130W (card), 2018ApJ...859..111H, 2019A&A...625A.118K (card), 2025ApJ...984L..21B (card) |
| CO/H2 (disk), lower | 7e-5; 5e-5; 1e-6 (HD-based) | 2017ApJ...851...85B; 2014ApJ...791...42Z, 2025ApJ...994...98F (card); 2018ApJ...856..117F (card) |
| CO/H2 (disk), higher | 2e-4 (written as H2/CO = 5000) | 2014ApJ...792...68S |
| CO per H nuclei | 7.5e-5 (CO/H2 = 1.5e-4 if all H is in H2); 1e-4; 1.4e-4 above 20 K | 2017ApJ...851..132C (card); 2024ApJ...966..117X; 2019A&A...629A..75B (card) |
| CO by mass | 1.4e-4 "in mass"; X_CO = 1e-4 "CO mass abundance fraction" | 2019ApJ...881..108J; 2017ApJ...846L..26W (card) |
| CO/H2 (AGB, galaxies) | 2e-4 to 6.5e-4; 1e-3 for carbon stars and detached shells | 2026A&A...711A.159M (2e-4), 2016A&A...586A...5M (4.3e-4), 2020A&A...633A..13D (6.5e-4), 2017A&A...604A...2S (3e-4); 2020A&A...640A.133R, 2024A&A...687A.112M |
| Freeze-out | 17 K | 2014ApJ...792...68S |
| Freeze-out | 19 K, depletion 1e-8 | 2013ApJ...774...16R, 2015ApJ...813...99F (card) |
| Freeze-out | 20 K, factor 1000 depletion | 2018ApJ...859..111H |
| Freeze-out | 21 K, factor 1e-5 | 2025ApJ...984L..21B (card) |
| Freeze-out | 30 K, factor 0.01 (envelope) | 2018A&A...612A..72J |
| Freeze-out grid | 10-40 K | 2013A&A...557A.133D |
| Photodissociation | CO removed where the shielding H2 column is below 1e21 cm^-2 (factor 1e-5 in 2025ApJ...984L..21B (card)); the cards do not say how the column is integrated | 2017ApJ...851...85B, 2025ApJ...984L..21B (card) |
| CO/13CO, CO/C18O | 69, 557 | 2016ApJ...823L..18H (card), 2017ApJ...851..132C (card), 2025ApJ...994...98F (card) |
| CO/13CO, CO/C18O | 69, 570 | 2019ApJ...883...98Z |
| CO/13CO, CO/C18O | 62, 500 | 2024ApJ...966..117X |
| CO/C18O | 550 | 2017A&A...605A..21C |
| Ortho/para H2 | 3 | 2016A&A...587A.145B (card), 2020A&A...633A..13D |

Mean molecular weight: 2.37 per particle (H2 + He) in 2012ApJ...757..129R and 2025ApJ...994..214T; 2.3 in
2021AJ....161..238W; ~2.8 per H2 in 2024ApJ...976...29H; mu_H = 1.41 in 2026AJ....171..368M; mu = 14 adopted for
debris gas in 2019MNRAS.489.3670K, 2020MNRAS.497.2811K and 2020ApJ...892...99C (composition not stated in the
cards; general practice: pure CO is ~28, an equal-number C + O atomic mix ~14).

Background field: T_CMB = 2.73 (1 + z) K in 2019ApJ...873...50D; 19.2 K at z = 6.02 in 2022PASJ...74.1429T;
2.73 K for local sources in 2022ApJ...929..100K.

## Disk structure fiducials

Two vertical parameterizations appear. Height form: H(r) = H100 (r/100 au)^beta (H100 in au, beta about 1.1).
Aspect-ratio form: h(r) = H/r = h_c (r/r_c)^psi (dimensionless h, psi about 0.1). They agree when beta = 1 + psi
(general practice). Some papers use psi or p for the height exponent; check before converting.

| Setting | Values | Bibcode |
|---|---|---|
| Sigma tapered power law | gamma = 0.8, R_c = 150 AU, M_gas = 0.09 Msun | 2013ApJ...774...16R |
| Sigma tapered power law | gamma = 1, R_c = 320 AU, (h/r)_c = 0.18, psi = 0.1 | 2020ApJ...895L..18B (card) |
| Sigma tapered power law | R_c = 250 AU, gamma = 0.6, M_disk 0.1 Msun | 2018A&A...616A..88V (card) |
| Sigma grid | gamma 0-2 in steps of 0.1; R_c 110-140 AU | 2013A&A...557A.133D |
| Sigma grid | gamma 0.3-1.5, H100 5-10 au, beta 1.00-1.15 | 2023MNRAS.518.6092L |
| Scale height | H100 = 10 au, beta = 1.1 | 2019A&A...622A..75L |
| Scale height | H0 = 10 au, beta = 1.15 | 2016ApJ...816...25P, 2024ApJ...970..114T |
| Scale height | H0 = 10 au, beta = 1.125 | 2016ApJ...819..102V (card) |
| Scale height range | beta 1.0-1.2, H100 5-15 au (SED fits) | 2024ApJ...966...59S (card) |
| Scale height grid | H0 0.03-0.1, beta 1.0-1.21 | 2013A&A...557A.133D |
| Height exponent | p = 1.25 with T ~ r^-0.5 | 2021ApJ...908..250H |
| Scale height grid | h0 0.02-0.2, psi 1-1.3 (psi used as a height exponent) | 2019ApJ...883...98Z |
| Temperature | T = 50 K (r/50 au)^-0.3 | 2015ApJ...798...85P |
| Temperature | T ~ r^-0.2, two components | 2014ApJ...796....1T |
| Temperature | T(R) = 99.3 K (R/1 AU)^-0.68 | 2018A&A...616A..88V (card) |
| Two-layer temperature | Tmid10 = 40 K, Tatm10 = 125 K, q = 0.47 | 2018ApJ...852..122H (card) |
| Debris aspect ratio | h = 0.03 fixed, or 0.07 | 2020ApJ...898..146M, 2025A&A...693A.151M; 2016MNRAS.460.2933M |

Turbulence: disks 0 (2015ApJ...812...27A, 2024A&A...687A.311A) to a 0-0.3 km/s grid (2013A&A...557A.133D);
envelopes and winds 0.5 km/s (2024A&A...687A.112M), 1 km/s (2019A&A...629A.146V), 2 km/s
(2015MNRAS.453.4324M), 3 km/s (2024A&A...681A..17D), and a radial profile from 11 km/s inside to 1 km/s
(2020MNRAS.494.1323D). 2024ApJ...966L..13D gives non-thermal motions as FWHM; state your convention.

## Photon budgets (visible pack examples, not an exhaustive range)

| Photons | Use | Bibcode |
|---|---|---|
| 5e7 | dust MC | 2016MNRAS.461..385B |
| 1e8 | thermal MC and images; scattering | 2024ApJ...966..117X, 2026A&A...705A.203W; 2024ApJ...970...25W |
| 1.28e8 / 1.28e6 | temperature / images | 2024A&A...687A.311A |
| 2.5e8; 3e8 | thermal | 2025ApJ...984L..16G; 2021ApJ...909..212K (1e7 for SED), 2026AJ....171..368M |
| 1e9; 1.6e9 | per simulation | 2025ApJ...984L..12B; 2025ApJ...989L..43Y |
| 1e7 / 1e9 / 1e11 | continuum / ALMA polarization / NIR | 2024NatAs...8.1148U (card) |
| 1e5-1e9 | convergence test | 2019A&A...627A.114K |

## Sampler settings

| Walkers | Steps / burn-in | Notes | Bibcode |
|---|---|---|---|
| 16 | 1500, discard 100 | MCFOST SED fit, uniform priors | 2024AJ....168..142L |
| 24 | 5000, median of last 4200 | | 2025ApJ...984L..19Y |
| 30 | 4000-5000, 50% burn-in | | 2021PSJ.....2..105T |
| 40 | 1000, ~100 burn-in | visibilities averaged to 10 s, statwt weights | 2018MNRAS.475.4924K |
| 40 | 6000, first half removed | converged at >50 tau | 2025ApJ...990..145L |
| 50-180 | 300-1000 | visibilities averaged to 3 min and 2 GHz | 2017MNRAS.465.2595M |
| 50, 2 temperatures | 1000-2000, burn-in 100-250 | parallel tempering | 2021AJ....161..238W |
| 80 | 1000, first 500 burn-in | | 2017ApJ...843..150F (card) |
| ~100 | 1000, ~100 burn-in | | 2017ApJ...839...86H |
| 100 | 500 | | 2017ApJ...851L..23C (card) |
| 100 | 1000 after burn-in (dust), ~10,000 (gas) | | 2020MNRAS.497.2811K |
| 100 | 1200 after burn-in | | 2019MNRAS.489.3670K |
| 200 | 1500, first 200 discarded | | 2020ApJ...892...99C |
| 240 | 2000 | | 2020ApJ...889...59P |
| 500 | 1000 | uniform priors on Md, gamma, Rc, H100 | 2018ApJ...859..111H |
| 10 x free params | 2000 | | 2020ApJ...898..146M |

Data compression before fitting: visibilities averaged to 3 min and 2 GHz (2017MNRAS.465.2595M); 25 channels of
0.4 km/s (2017ApJ...851..132C (card)).

## Fitting-method phrasings (pack aggregate)

The aggregate lists 40 distinct phrasings with 43 occurrences ("chi2 grid search" 3, "Manual" 2, the other 38
once). Each phrasing is put in the first matching class, in this order: sampler (MCMC, emcee, nested sampling,
Nautilus, MultiNest) > retrieval (optimal estimation, "retrieve") > least squares (MPFIT, least squares) > chi2
(chi2 or chi-square, including grids) > manual (manual, by-eye, qualitative, not a fit, adjustment) > other.

| Class | Phrasings | Occurrences |
|---|---|---|
| Sampler | 10 | 10 |
| Retrieval | 3 | 3 |
| Least squares | 3 | 3 |
| chi2 / chi2 grid | 10 | 12 |
| Manual / by-eye / no fit | 6 | 7 |
| Other (noise or phase-function fits, slab comparisons without a statistic, unnamed) | 8 | 8 |

Two phrasings classed elsewhere also contain manual steps (MPFIT then manual tweaks; manual fits plus
optimal-estimation retrievals). These count phrasings, not papers.

## Software (full aggregate list, matched steps, not papers)

radmc-3d 215, casa 106, lime 83, dali 80, mcfost 77, emcee 73, casa simobserve 43, radex 29, simobserve 23,
vis_sample 20, galario 16, radmc3d 16, tclean 15, optool 14, miriad 10, hyperion 10, ratran 9, xclass 9, ipole 8,
shape 7, simalma 7, casa simanalyze 7, scipy 6, pdspy 6, casa simalma 6, spectralradex 6, cassis 6, mcmax 6,
radmc 6, phantom 6, simanalyze 6, hochunk3d 6, mpfit 5, torus 5, shapemol 5, imfit 5, radmc3dpy 5, polaris 5,
mollie 5, nemesis 4.

## Synthetic observation inputs

| Tool | Settings | Bibcode |
|---|---|---|
| simobserve | 18 min, PWV 1.8 mm, C36-6, start HA 2.4 h | 2016A&A...593L..14F (card) |
| simalma | C36-3 12m, 210 s, PWV 0.5 mm, also 12m+ACA | 2024ApJ...966..117X |
| simobserve | PWV 0.6 mm, Cycle 8 configuration 2 | 2023Natur.621..483G |
| simobserve | 100 runs at different hour angles, baselines >13 klambda | 2019ApJ...874...89C |
| simobserve | 60 s, 1 s integrations, 107 GHz | 2017ApJ...838..114K |
