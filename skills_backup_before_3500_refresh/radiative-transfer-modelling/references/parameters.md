# Radiative transfer modelling: longer parameter tables

Every value below is copied from the evidence pack (`skills/packs/radiative-transfer-modelling.md`), which
quotes verified methods cards. Counts are my counts of pack lines unless marked "aggregate".

## Dust opacity at the observed band

Check whether a value is per gram of dust or per gram of gas (dust value / 100 at gas-to-dust 100).

| Band | Value | Composition / notes | Bibcode |
|---|---|---|---|
| 1.3 mm | 2.2 cm2/g | 30% amorphous C / 70% astrosilicate, 0.1 um-3 mm, a^-3.5 | 2018ApJ...859..111H |
| 1.3 mm | 2.2 cm2/g (kappa_abs) | a_max 3 mm, a^-3.5 | 2018MNRAS.474.4347C |
| 1.3 mm | 2.2 cm2/g (kappa_abs) | 0.1 um-3 mm, a^-3.5 | 2020ApJ...889...59P |
| 1.3 mm | 2.2 cm2/g | V883 Ori disk | 2019NatAs...3..314L |
| 1.3 mm | 2.25 cm2/g | 70% silicate / 30% graphite, 5 nm-3 mm | 2017ApJ...836..223W |
| 1.3 mm | 2.3 cm2/g | 1 um-1 cm, a^-3.5 | 2019MNRAS.488.1005P |
| 1.28 mm | 2.31 cm2/g | astrosilicate, 0.1-3000 um | 2019A&A...624A..33V |
| 230 GHz | 2.3 (nu/230 GHz) cm2/g | with T_dust 20 K | 2025ApJ...989....1Z |
| 1.3 mm | 1.1 cm2/g (kappa_abs) | astrosilicate, 1.3 um-1 cm (debris) | 2016MNRAS.460.2933M |
| 1.27 mm | ~1.3 cm2/g | astrosilicate, blowout size to 1 cm (debris) | 2020MNRAS.497.2811K |
| 1.3 mm | 3.95 cm2/g | HD 163296 | 2018ApJ...857...87L |
| 1.3 mm | ~0.95 cm2/g per dust mass | Semenov composite aggregate | 2017ApJ...835L..11T |
| 0.88 mm | 3.8 cm2/g (kappa_abs) | astrosilicate/amorphous C/ice 70/15/15%, 1 um-1 cm | 2017MNRAS.465.2595M |
| 885 um | 3.72 cm2/g | astronomical silicates, 0.05 um-1 mm | 2016ApJ...819..102V |
| Band 7 | 1.9 cm2/g | 70/15/15% mix, 1 um-1 cm | 2021AJ....161..271F |
| 340 GHz | 4.3 cm2/g | "DALI standard" | 2017A&A...599A.113M |
| 0.87 mm, 9.1 mm | 1.84, 0.13 cm2/g | beta = 1 | 2020ApJ...890..130T |
| 230 GHz | kappa0 = 0.01 cm2/g (per gas, g/d 100) | constant beta | 2015ApJ...808..102K |
| 1000 GHz ref. | 10 cm2/g, beta = 1 | used with factor 100 for gas | 2019A&A...623A.150V |
| Bands 7, 6 | 0.40, 0.17 cm2/g | astrosilicates 0.01-1 um (red supergiant) | 2019A&A...627A.114K |

Dust models named: DIANA (2024A&A...688A.102T, 2024ApJ...975..235V), DSHARP (2020ApJ...893..125U,
2024ApJ...971..129C, 2025ApJ...984L..19Y), Birnstiel et al. 2018 (2024ApJ...966...59S), porous DHS grains
with void fraction 0.8 (2019MNRAS.482L..29D, 2019NatAs...3.1109P, 2020MNRAS.492.1531M).

## Disk gas chemistry and isotopologues

Every abundance must carry its denominator. In fully molecular gas n(H) = 2 n(H2), so X(CO/H2) = 2 X(CO/H)
(general practice). The rows below keep per-H2 and per-H values apart.

| Setting | Values seen | Bibcodes |
|---|---|---|
| CO/H2 (disk) | 1e-4 | 2017ApJ...835...17M, 2017ApJ...846L..26W, 2018ApJ...854..130W, 2018ApJ...859..111H, 2019A&A...625A.118K, 2025ApJ...984L..21B |
| CO/H2 (disk), lower | 7e-5; 5e-5; 1e-6 | 2017ApJ...851...85B; 2025ApJ...994...98F; 2018ApJ...856..117F |
| CO per H nuclei | 7.5e-5 (with H/H2 = 2, i.e. CO/H2 = 1.5e-4); 1e-4 (CO/H2 = 2e-4 if all H is in H2); 1.4e-4 | 2017ApJ...851..132C; 2024ApJ...966..117X; 2019A&A...629A..75B, 2019ApJ...883...98Z |
| CO/H2 (AGB, galaxies) | 3e-4 to 6.5e-4 | 2016A&A...586A...5M (4.3e-4), 2018A&A...620A..75K (4e-4), 2020A&A...633A..13D (6.5e-4), 2017A&A...604A...2S (3e-4) |
| Freeze-out | 19 K, depletion 1e-8 | 2013ApJ...774...16R, 2015ApJ...813...99F |
| Freeze-out | 20 K, factor 1000 depletion | 2018ApJ...859..111H |
| Freeze-out | 21 K, factor 1e-5 | 2025ApJ...984L..21B |
| Freeze-out | 30 K, factor 0.01 (envelope) | 2018A&A...612A..72J |
| Photodissociation | CO removed where the shielding H2 column is below 1e21 cm^-2 (factor 1e-5 in 2025ApJ...984L..21B); the cards do not say how the column is integrated | 2017ApJ...851...85B, 2025ApJ...984L..21B |
| CO/13CO, CO/C18O | 69, 557 | 2016ApJ...823L..18H, 2017ApJ...851..132C, 2025ApJ...994...98F |
| CO/13CO, CO/C18O | 69, 570 | 2019ApJ...883...98Z |
| CO/13CO, CO/C18O | 77, 560 | 2017ApJ...836..201D |
| CO/13CO, CO/C18O | 62, 500 | 2024ApJ...966..117X |
| CO/C18O | 550 | 2017A&A...605A..21C |
| Ortho/para H2 | 3 | 2016A&A...587A.145B, 2020A&A...633A..13D |

## Disk structure fiducials

Two vertical parameterizations appear. Height form: H(r) = H100 (r/100 au)^beta (H0, H100 in au, beta about
1.1). Aspect-ratio form: h(r) = H/r = h_c (r/r_c)^psi (dimensionless h, psi about 0.1). They agree when
beta = 1 + psi (general practice). The 2019ApJ...883...98Z grid pairs a dimensionless h0 with psi 1-1.3, which
looks like a height exponent; check the paper before converting.

| Setting | Values | Bibcode |
|---|---|---|
| Sigma tapered power law | gamma = 0.8, R_c = 150 AU, M_gas = 0.09 Msun | 2013ApJ...774...16R |
| Sigma tapered power law | gamma = 1, R_c = 320 AU, (h/r)_c = 0.18, psi = 0.1 | 2020ApJ...895L..18B |
| Sigma tapered power law | R_c = 250 AU, gamma = 0.6, M_disk 0.1 Msun | 2018A&A...616A..88V |
| Scale height | H100 = 10 au, beta = 1.1 | 2019A&A...622A..75L |
| Scale height | H0 = 10 au, beta = 1.125 | 2016ApJ...819..102V |
| Scale height | beta 1.0-1.2, H100 5-15 au | 2024ApJ...966...59S |
| Scale height grid | h0 0.02-0.2, psi 1-1.3 | 2019ApJ...883...98Z |
| Temperature | T = 50 K (r/50 au)^-0.3 | 2015ApJ...798...85P |
| Two-layer temperature | Tmid10 = 40 K, Tatm10 = 125 K, q = 0.47 | 2018ApJ...852..122H |
| Debris aspect ratio | h = 0.03 fixed, or 0.07 | 2020ApJ...898..146M, 2025A&A...693A.151M; 2016MNRAS.460.2933M |

## Sampler settings

| Walkers | Steps / burn-in | Notes | Bibcode |
|---|---|---|---|
| ~100 | 1000, ~100 burn-in | | 2017ApJ...839...86H |
| 80 | 1000, first 500 burn-in | | 2017ApJ...843..150F |
| 100 | 500 | | 2017ApJ...851L..23C |
| 50-180 | 300-1000 | visibilities averaged to 3 min and 2 GHz | 2017MNRAS.465.2595M |
| 500 | 1000 | uniform priors on Md, gamma, Rc, H100 | 2018ApJ...859..111H |
| 40 | 1000, ~100 burn-in | visibilities averaged to 10 s, statwt weights | 2018MNRAS.475.4924K |
| 240 | 2000 | | 2020ApJ...889...59P |
| 200 | 1500, first 200 discarded | | 2020ApJ...892...99C |
| 10 x free params | 2000 | | 2020ApJ...898..146M |
| 100 | 1000 after burn-in (dust), ~10,000 (gas) | | 2020MNRAS.497.2811K |
| 50, 2 temperatures | 1000-2000, burn-in 100-250 | parallel tempering | 2021AJ....161..238W |
| 24 | 5000, median of last 4200 | | 2025ApJ...984L..19Y |
| 40 | 6000, first half removed | converged at >50 tau | 2025ApJ...990..145L |

Data compression before fitting: visibilities averaged to 3 min and 2 GHz (2017MNRAS.465.2595M); 25
channels of 0.4 km/s (2017ApJ...851..132C).

## Synthetic observation inputs

| Tool | Settings | Bibcode |
|---|---|---|
| simobserve | 18 min, PWV 1.8 mm, C36-6, start HA 2.4 h | 2016A&A...593L..14F |
| simalma | C36-3 12m, 210 s, PWV 0.5 mm, also 12m+ACA | 2024ApJ...966..117X |
| simobserve | PWV 0.6 mm, Cycle 8 configuration 2 | 2023Natur.621..483G |
| simobserve | 100 runs at different hour angles, baselines >13 klambda | 2019ApJ...874...89C |
| simobserve | 60 s, 1 s integrations, 107 GHz | 2017ApJ...838..114K |
