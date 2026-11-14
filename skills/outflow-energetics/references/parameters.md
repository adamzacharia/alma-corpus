# Outflow energetics: per-paper parameters

Values are copied from the evidence pack (`skills/packs/outflow-energetics.md`) key-parameter, assumption and
excerpt lines. "-" means the pack does not give it. The tables are selected examples, not complete lists;
counts in SKILL.md come from the pack's key-parameter and assumption lines, and population counts from the
classification at the end of this file.

## Protostellar outflows

| Paper | Tracer | Tex | Abundance / mu | Opacity | Inclination | Rate / time method |
|---|---|---|---|---|---|---|
| 2016ApJ...832..158Z | 12CO + isotopologues | 15 and 50 K | CO/H2 1e-4; "2.34e-24 g per H2" as quoted (equals 1.4 m_H, a mass per H nucleus: source inconsistency) | highest column among isotopologues per pixel | 40 deg | mass spectra power laws (slope sign inconsistent in the paper, see SKILL.md) |
| 2021A&A...648A..41V | 12CO 2-1 | 25 and 100 K | X_CO 1e-4; mu 2.76; Tbg 2.7 K | none (lower limits) | sizes deprojected; outflow perpendicular to disk | opening angle at 1000 au |
| 2024ApJ...966..117X | synthetic 12CO 2-1 | 10-50 K | mu 1.4 | thin | 60-70 deg tested | half-length / mass-weighted LOS velocity; corrections 10 (Mdot), 200 (Pdot) |
| 2015ApJ...811L...4Z | 12CO 1-0 | 10 K | H2/CO 1e4; mu 2.8 | thin | 30 deg | size/velocity x tan(theta) |
| 2017MNRAS.465..834Z | 12CO, 13CO | 50 K | 12CO/H2 1e-4; 12CO/13CO 62 | not applied (lower limits) | face-on, age uncertain | Perez et al. 2015 per-channel |
| 2017MNRAS.468.3266R | 12CO, 13CO, C18O | 20 and 50 K | - | corrected, "with caution" | not corrected | v_flow = P/M; age lower limit |
| 2018MNRAS.473..879P | 12CO, 13CO | 50 K | 12CO/H2 1e-4; 12CO/13CO 62 | - | - | - |
| 2020A&A...634L..12D | 12CO 2-1, 13CO | 50 K | 12CO/13CO 65 | 12CO opacity corrected with 13CO | - | steady-flow mass flux in 0.7" slices |
| 2020MNRAS.496..394R | 12CO 2-1 | 100 K (50 K gives ~40% less) | H2/CO 1e4 | thin wings | i <= 62.5 deg, not applied | wings |v-v0| > 3.5 km/s, Margulis 1985 correction |
| 2016A&A...587A.145B | 12CO 2-1 | 100 K | CO/H2 1e-4 | thin | 20 deg (from plane of sky) | t_dyn 400-500 yr |
| 2020A&A...633A.126B | 12CO, 13CO | 30 K | CO/H2 8.3e-5; K = 5.07e-10 Msun s K^-1 km^-1 | 13CO-based; 12CO alone low by 1.1-5 | uncertain | vmax method (lower limit) |
| 2019A&A...632A.101T | CO, SiO, others | 250, 300, 700 K tested | H2/CO 1.2e4; mu 2.8 | - | not corrected | M7 force printed as Mdot v_max / R_lobe (not a force dimensionally; check before reuse) |
| 2019ApJ...873...73Z | 12CO 2-1 | - | 12CO/H2 1e-4; "2.34e-24 g per H2" as quoted (see above) | correction factors 10 / 8 | 20 deg | t_dyn from 15" length |
| 2024ApJ...963...72O | CO | 40 K | X_CO 1e-4; mu 2.8; d 405.7 pc | thin (lower limits) | - | - |
| 2016ApJ...821L...3T | CO | 17 K (minimizes mass) | - | - | 60 deg | lower limits |
| 2025A&A...695A.236L | H2CO | 30-70 K | H2CO 1e-10 | - | not corrected | - |
| 2025A&A...699A.382M | C18O | 50-100 K | CO 1e-4; mu_g 2.3; 16O/18O 560 | thin LTE | 40 +/- 10 deg | t_dyn = R / v_exp; compared with PFT |
| 2025ApJ...987..197H | HC3N 11-10 | - | HC3N/H2 5e-9; mu 2.8 | thin | 53.7 deg | 5 sigma lobe masks |
| 2013ApJ...775L..31S | SiO (CS check) | - | - | - | 45 deg | R = Robs/sin i, V = Vmax/cos i |
| 2015Natur.527...70P | CO knots | - | - | - | unknown | tau_dyn = D/V (cos i/sin i) |
| 2023ApJ...956L..35Z | CO | 30 K | H2/CO 1e4 | thick, lower limit | - | explosive outflow, 120 km/s range |
| 2020ApJ...899L..10F | 12CO | 20 K | 12CO/H2 1e-4 | LTE | 30 and 70 deg | - |
| 2017ApJ...847...92H | CO | 20 K | - | thin | not corrected | d = 436 pc |
| 2019ApJ...886...15T | CO | - | X_CO 7e20; CO(2-1)/(1-0) 1.0 | - | 30-70 deg | - |
| 2024ApJ...961..228S | CO | - | X_CO 2.0e20; mu 2.8 | - | i_out = i_ring | area where intensity > 0.5 K km/s |
| 2016ApJ...828..100F | SiO 2-1 | >= 15 K | - | thin | - | wind 300 km/s; mass loading 0.1-0.3 |
| 2020ApJ...904..158L | 28SiO, 29SiO | same Tex | 28SiO abundance uncertain by up to 100 | v=1 thick | - | - |
| 2019ApJ...886L...4Z | H30alpha | - | all H ionized; mass 1.4 x H | - | weakly constrained | photoionized outflow |
| 2026ApJ..1003...26O | [O I], [O III] | Te 1e4 K | X_O 3e-4; fV 1/3 | - | - | atomic outflow |

## Galaxy and AGN outflows

| Paper | Tracer | Conversion | Velocity | Radius | Geometry / formula |
|---|---|---|---|---|---|
| 2018ApJ...859...35G | CO | alpha_CO 0.8 | mass-weighted mean of red and blue wings, no inclination | half the red-blue peak separation | Mdot = M v / R |
| 2014A&A...567A.125G | CO 3-2 | X_CO ~1/4 MW | V_out ~100 km/s | R_out ~100 pc | 3 V M / R tan(alpha), coplanar tan(alpha) = 1/tan(i) |
| 2024A&A...686A..46E | CO 3-2 | r31 0.7; X_CO 2e20 (upper limits: possible bar) | 25.6 +/- 9.4 km/s | 0.4"-5" | shell, M v / R |
| 2017ApJ...843...18V | CO 1-0 | alpha_CO 0.8 | 1000 km/s | 7 kpc (conservative) | M V / R |
| 2019A&A...628A.118B | CO 3-2 | alpha_CO 0.8; r31 from systemic | v98 | clump distance | M v / R |
| 2019A&A...630A..59B | [CII] stack | X_C+ ~1e-4, T 200 K, PDR fraction 0.7 | abs(Delta v) + FWHM/2 | ~3.5 kpc | M v / R |
| 2025ApJ...990L..31B | [CII] | Hailey-Dunsheath 2010, T 200 K | abs(v_mom1) + 2 sigma | beam radius at centre | Omega M v f / r, Omega ~1/2 |
| 2024ApJ...970....9B | [CII], BAL | X_C+ 1.4e-4, T 200 K; BAL: mu 1.4, global covering Omega 0.2 | - | max extent or bulk | shell ([CII]); thin shell (BAL) |
| 2013ApJ...763..120C | [CII] wing +220 to +500 km/s | [CII]/H 1.4e-4 | - | 1.5" (10 kpc) | conical |
| 2019A&A...631A..78S | [CII] stack | X_C+ 1.4e-4, T 200 K | 493 km/s | 11.5 kpc | constant velocity |
| 2026ApJ..1000..312Z | [CII] | X_C+ 1e-4; mu 1.4 | - | 3.0 kpc | - |
| 2025A&A...695A...6P | Halpha, [OIII], [CII] | n_e 200, Z 0.5 Zsun; [CII] at T 1e4 K, n_H 1e4 (lower limit) | abs(Delta v) + 2 sigma | 2 kpc / 1.3 kpc | M v / R; eta = Mdot/SFR |
| 2024ApJ...962....1S | OH 119 um | OH/H2 5e-7; Tex 50 K | 669 km/s | 2 kpc | thin shell, f 0.3 |
| 2018Sci...361.1016S | OH 119 um | OH/H2 5e-6; Tex = Tdust 100 K; mu 1.36 | 440 km/s | ~600 pc | thin shell, f_cov 0.8 |
| 2019A&A...632L...7J | H2O absorption | chi_H2O ~1e-6 | fitted v0 | R_IN 0.07 kpc | spherical shell, MultiNest |
| 2020ApJ...901..151S | CO | X_CO 0.5e20 | - | h_z 1 kpc | cylinder (conservative) |
| 2020A&A...641A.151S | CO 2-1 residuals | alpha_CO 1.1 | v_max | - | 3 v_max M / R |
| 2014ApJ...790..160S | CO 3-2 | - | 500 km/s | 0.3 kpc | 3 M v / r (volume filling); momentum boost vs L_bol/c |
| 2014ApJ...797...90S | CO 1-0 | X20 = 1 | deprojected with disk inclination | extent | M / (extent / v) |
| 2018ApJ...868...95M | HCN, HCO+, CO | alpha_HCN 0.24-10; alpha_CO 0.8-4.6 | 1600 km/s | 400 pc | age = l / V, i 80 deg |
| 2020A&A...633A.127F | CO | - | 160 km/s projected | ~100 pc | M V / d, L_kin = 1/2 M V^3 / d |
| 2024A&A...684L..11G | CO | - | 217 km/s projected, 515 deprojected | 52 pc | turbulence neglected |
| 2016ApJ...832..142Z | CO | alpha_CO 0.34-0.8 | 150-180 km/s | - | cone perpendicular to disk, i 65 deg |
| 2017A&A...608A..38O | CO lines | alpha_CO 0.25 at Tex 29 K | 300 km/s | 0.5 kpc | spherical |
| 2019A&A...632A..33A | CO 3-2 | r31 0.82; Galactic 4.36 or 1/4 | 300 km/s | 23 pc | - |
| 2019A&A...628A..65A | CO 2-1 | X 2e20; CO(1-0)/(2-1) 1 | 100 km/s | 35 pc | - |
| 2018MNRAS.475L..52S | CO 2-1 | alpha_CO 0.8; ratio 1 | - | - | i 45 deg |
| 2019MNRAS.489.1927S | CO | alpha_CO 2.1 (0.8-3.4) | - | - | cone axis 45 deg to line of sight |
| 2018ApJ...863..143C | [CI], CO | alpha_CO 2.1 +/- 1.2 where [CI] undetected | - | 0.5 kpc | - |
| 2021A&A...655A..25Z | CO | alpha_CO 0.3 (thin), 0.8 (thick) | - | - | - |
| 2021AN....342.1160P | CO residuals | alpha_CO 0.8 | - | - | - |
| 2015A&A...580A...1M | CO (one line) | X_CO uncertain | 200 km/s | 0.3 kpc | tau_dyn ~1.5e6 yr |
| 2017ApJ...851..126V | CO | - | 400 km/s | 1.6 kpc | M 3.3e9 Msun |
| 2024A&A...682A..54T | [CII] | PDR L[CII]-to-mass | 560 km/s | 2.4-5.5 kpc | - |

## Classification of the 97 pack papers (basis for the population counts in SKILL.md)

My classification of every paper in the pack's "All papers" list, by title and, where present, excerpt.

**Protostellar outflows (34):** 2013ApJ...774L...7M, 2013ApJ...775L..31S, 2015ApJ...811L...4Z,
2015ApJ...812...59O, 2015ApJ...815..106H, 2015Natur.527...70P, 2016A&A...587A.145B, 2016ApJ...821L...3T,
2016ApJ...828..100F, 2016ApJ...832..158Z, 2017ApJ...847...92H, 2017MNRAS.465..834Z, 2017MNRAS.468.3266R,
2018MNRAS.473..879P, 2019A&A...632A.101T, 2019ApJ...873...73Z, 2019ApJ...886...15T, 2019ApJ...886L...4Z,
2020A&A...633A.126B, 2020A&A...634L..12D, 2020ApJ...889...43Z, 2020ApJ...899L..10F, 2020ApJ...904..158L,
2020MNRAS.496..394R, 2021A&A...648A..41V, 2021A&A...649A.139I, 2023ApJ...956L..35Z, 2024ApJ...961..228S,
2024ApJ...963...72O, 2024ApJ...966..117X, 2025A&A...695A.236L, 2025A&A...699A.382M, 2025ApJ...987..197H,
2026ApJ..1003...26O.

**Galaxy/AGN outflows (49, a few only mention an outflow):** 2013ApJ...763..120C, 2014A&A...567A.125G,
2014ApJ...784...78R, 2014ApJ...790..160S, 2014ApJ...797...90S, 2015A&A...580A...1M, 2016ApJ...823...68S,
2016ApJ...832..142Z, 2017A&A...608A..38O, 2017ApJ...834..135T, 2017ApJ...843...18V, 2017ApJ...851..126V,
2018ApJ...859...35G, 2018ApJ...863..143C, 2018ApJ...867..165B, 2018ApJ...868...95M, 2018MNRAS.473.1909G,
2018MNRAS.475L..52S, 2018PASJ...70L...1M, 2018Sci...361.1016S, 2019A&A...628A..65A, 2019A&A...628A.118B,
2019A&A...630A..59B, 2019A&A...631A..78S, 2019A&A...632A..33A, 2019A&A...632A..61G, 2019A&A...632A..66O,
2019A&A...632L...7J, 2019MNRAS.489.1927S, 2019MNRAS.490.5860S, 2020A&A...633A.127F, 2020A&A...633L...4H,
2020A&A...640A.104A, 2020A&A...641A.151S, 2020ApJ...890...29F, 2020ApJ...901..151S, 2021A&A...655A..25Z,
2021A&A...656A..45M, 2021AN....342.1160P, 2024A&A...682A..54T, 2024A&A...684L..11G, 2024A&A...686A..46E,
2024ApJ...962....1S, 2024ApJ...970....9B, 2024ApJ...974..195Z, 2025A&A...695A...6P, 2025ApJ...990L..31B,
2025ApJ...992L...7S, 2026ApJ..1000..312Z.

**Evolved stars and stellar winds (6, out of scope):** 2016A&A...593A..92B, 2017A&A...605A..28D,
2017ApJ...841..110S, 2017ApJ...841..130A, 2017MNRAS.464L..75F, 2018A&A...614A..58B.

**Other Galactic papers, off-topic for outflow energetics (8):** 2014ApJ...789L...4T, 2016ApJ...827...72S,
2018A&A...615A.141B, 2018ApJ...866..141K, 2019ApJ...872....2R, 2019ApJ...886...14F, 2019ApJ...887..209A,
2020ApJ...890..129K.
