# Parameter choices by subfield (dust-continuum-mass)

All values are copied from the evidence pack (`skills/packs/dust-continuum-mass.md`), "Key parameters" and
"Assumptions" lists. Those lists are truncated in the pack, so this is a sample, not a census.
Unit note (general): 1 m2/kg = 10 cm2/g. "per gas" means the opacity already includes a gas-to-dust ratio.

## Opacity normalisations

| Subfield | kappa_0 | nu_0 or lambda | beta | Per | Papers |
|---|---|---|---|---|---|
| Protoplanetary disks | 10 cm2/g | 1000 GHz | 1 | dust | 2016ApJ...828...46A, 2019A&A...623A.150V, 2019A&A...628A..85V, 2020A&A...640A..27V, 2018A&A...619A.161C, 2017AJ....153..240A, 2024A&A...684A.134R |
| Protoplanetary disks | 2.3 cm2/g | 230 GHz | 0.4 | dust | 2014ApJ...787...42C, 2017ApJ...846...70P, 2018ApJ...859...32P, 2018ApJ...869...17L, 2017ApJ...841L..11B, 2017A&A...597A..32V |
| Protoplanetary disks | 2.7 cm2/g | 885 um | 0.4 | dust | 2016ApJ...819..102V |
| Protoplanetary disks | 2 cm2/g | 890 um | n/a | dust | 2020A&A...633A.114S |
| Protoplanetary disks | 3.4 cm2/g | 880 um | n/a | dust | 2015ApJ...805L..17B, 2017ApJ...835...17M |
| Protoplanetary disks | 0.02 cm2/g | 0.89 to 1.3 mm | n/a | gas | 2014ApJ...791...20R, 2014Natur.514..600D |
| Disks, grain-size dependent | 0.42 / 1.9 cm2/g | 1.3 mm | n/a | dust (100 um / 1 mm grains) | 2024ApJ...974..102S |
| Debris disks | 2.3 cm2/g | 1.3 mm | n/a | dust | 2017ApJ...842....8M, 2018ApJ...869...75M |
| Debris disks | 0.23 m2/kg | 1.33 mm (from 1 m2/kg at 1000 GHz, linear) | 1 | dust | 2025A&A...693A.151M |
| Debris disks | 2.7 cm2/g | 1.3 mm | n/a | dust | 2013ApJ...762L..21M |
| White-dwarf debris | 1.7 cm2/g | 870 um | n/a | dust | 2014MNRAS.444.1821F |
| Dense cores (OH94) | 0.899 cm2/g | 1.3 mm | n/a | dust | 2020ApJ...894L..14L, 2018ApJ...853..160C, 2017ApJ...849...68S, 2018ApJ...869...59W |
| Dense cores (OH94) | 1.11 cm2/g | 230 GHz | n/a | dust | 2017A&A...604A...6S, 2019A&A...621A.122B |
| Dense cores | 0.9 cm2/g at 1.3 mm; pack quotes "(lambda/1.3 mm)^beta", which inverts the usual kappa proportional to nu^beta. Verify in the paper; for a positive beta use (1.3 mm/lambda)^beta | 1.3 mm | 1.5 | dust | 2016ApJ...833..209O |
| Cores / clumps (Hildebrand) | 0.1 cm2/g | 1000 GHz | 0.5 to 1.8 | gas | 2016A&A...596A..88L, 2017A&A...600A.141K, 2018MNRAS.475..448T, 2021A&A...648A..41V |
| Cores / clumps | 0.01 cm2/g | 230 GHz | n/a | gas | 2019ApJ...884...48C, 2015ApJ...808..102K, 2014ApJ...789L...4T |
| Cores / clumps | 0.00899 cm2/g | 1.3 mm | n/a | gas | 2018ApJ...855...24P, 2019NatAs...3..517Z |
| Galactic Centre clouds | 0.04 cm2/g (nu/505 GHz)^1.75 | 505 GHz | 1.75 | gas | 2015MNRAS.449..715W, 2016MNRAS.457.4536W |
| Galaxies (Li and Draine type) | 0.0431 m2/kg | 352.6 GHz | 1.8 | dust | 2020ApJ...892...66M |
| Galaxies | 0.0484 m2/kg | 850 um | 1.8 | dust | 2018Sci...362.1034D |
| Galaxies | 0.15 m2/kg | 870 um | n/a | dust | 2014MNRAS.438.1267S |
| Galaxies | 0.051 m2/kg | 500 um | 1.8 | dust | 2024ApJ...963....1O |
| Galaxies | 0.0865 m2/kg | 351 GHz | n/a | dust | 2021A&A...652A..98G |
| Galaxies | 2.64 m2/kg | 125 um | 1.5 | dust | 2015ApJ...810...91H, 2019ApJ...881...63N |
| Dwarf galaxies | 1.6 m2/kg | 160 um | 1.7 | dust | 2017MNRAS.468L..87C |
| AGB / RSG envelopes | 7 cm2/g | mm | n/a | dust | 2018A&A...615A..28D, 2018A&A...616A..34H |
| AGB envelope (OH94 coated) | 1.8 cm2/g | mm | n/a | dust | 2020ApJ...890L..14T |
| Comet coma | 0.17 to 0.467 m2/kg | 233 GHz | n/a | dust | 2025ApJ...986L..22R |

## Temperature prescriptions

| Prescription | Papers |
|---|---|
| Fixed 20 K for all disks, not scaled with L* | 2016ApJ...828...46A |
| T = 25 K (L*/Lsun)^0.25 | 2016ApJ...819..102V, 2021A&A...653A..46V (20 K when L* unknown) |
| T = 25 K (L*/Lsun)^0.17 | 2017ApJ...846...70P |
| RT-calibrated: flaring angle 0.02, R_subl = 0.07 sqrt(L*) | 2020ApJ...892..111F, 2024A&A...684A.134R |
| T_d = [zeta L / (4 pi sigma r^2)]^(1/4), zeta = 0.02 at the source radius | 2024ApJ...974..102S |
| T_d = 38 K (r/100 au)^-0.4 (L_int/Lsun)^0.2 for protostellar disks | 2020A&A...644A..11L |
| T(R) = 278.3 L*^0.25 R^-0.5 (blackbody grains) for debris belts | 2025A&A...693A.151M |
| 20 K (no counterpart), 50 K (IR or radio counterpart), 100 K (hot core) | 2020A&A...635A...2S |
| 35 K with IR counterpart, 15 K without | 2018A&A...615A...9P |
| T by L/M: 20 K (L/M < 1), 35 K (1 to 10), max(21.1 (L/M)^0.22, 35 K) above 10 | 2024A&A...690A.185W |
| T_d = 43 (L/Lsun)^0.25 K | 2024A&A...690A..46S |
| T_d = gas temperature from NH3 or line rotational temperature | 2014ApJ...797...27F, 2016ApJ...828..100F, 2020ApJ...890...76N |
| Clump SED fit for T_d and beta (22 K / 2.1 prestellar, 28 K / 1.6 protostellar) | 2020ApJ...890...76N |
| High-z: 47 K, beta 1.6 (quasar hosts) | 2016ApJ...816...37V, 2017Natur.545..457D, 2024ApJ...968....9W |
| High-z: mass-weighted 25 K | 2020ApJ...892...66M |
| High-z: assumed 25 K (not described as mass-weighted) | 2024ApJ...963....1O |
| High-z: 35 K, beta 1.5 | 2017ApJ...851..145M |

## Gas-to-dust variants

| Value | Context | Papers |
|---|---|---|
| 100 | default for disks, cores, many galaxies | 2016ApJ...828...46A, 2020ApJ...894L..14L, 2019A&A...628A..27B |
| 141 | Draine-type value for cores and clouds | 2013ApJ...779...96T, 2017MNRAS.464L..31H, 2018ApJ...853..160C |
| 150 to 154 | massive star formation, hot cores | 2017A&A...603A..10B, 2019A&A...621A.122B, 2015ApJ...813L..19J, 2019ApJ...871..170M |
| 90 +/- 25 | SMGs | 2014MNRAS.438.1267S, 2017ApJ...839...58S, 2018ApJ...859...12G |
| about 120 from 12+log(O/H) = 8.53 | metallicity-scaled galaxies | 2017MNRAS.469.4683C |
| 100 at solar metallicity, scaled with mass-metallicity relation | ASPECS stacks | 2020ApJ...892...66M |
| about 370 (dust-to-gas 0.0027 = Galactic 0.008 scaled by Z = 1/3) | LMC hot core, continuum N(H2) | 2020ApJ...891..164S |
| 300 | LMC, the same paper's gas-grain chemical model (a separate prescription) | 2020ApJ...891..164S |
| 300 / 167 | C-rich / O-rich AGB envelopes | 2024A&A...686A.274V |
| 40 | AGB wind model | 2017A&A...597A..99W |
| 4594 +/- 2848 | extremely metal-poor dwarf DDO 70 | 2020ApJ...892..147S |
| 75 to 100, tuned to HD | TW Hya disk | 2015ApJ...799..204C |
