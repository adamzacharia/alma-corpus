# Parameter choices by subfield (dust-continuum-mass)

All values are copied from the evidence pack (`skills/packs/dust-continuum-mass.md`, 915 papers), "Key
parameters" and "Assumptions" lists. Those lists are truncated in the pack (515 of 915 papers appear), so
this is a sample, not a census. Rows added in the 3,500-paper refresh cite papers new to the pack.
Values marked "(card)" come verbatim from that paper's methods card, not the pack.
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
| Disks, grain-size dependent | 0.4 / 1.9 / 1.0 cm2/g for a_max 0.1 / 1 / 10 mm | mm | n/a | dust | 2025ApJ...988..106H |
| Disks, DSHARP via optool (RT grid) | grains 0.05 um to 3 mm, full scattering | mm | n/a | dust | 2025A&A...696A.232G |
| Disks, two models side by side | DSHARP (s_max 0.1 mm) and 2.3 (nu/230 GHz)^0.4 | 230 GHz | 0.4 | dust | 2021ApJ...923..121Y |
| Disks | 2.7 cm2/g | 345 GHz | n/a | dust | 2025ApJ...994..214T |
| Disks (low end) | 1.1 cm2/g | 1.3 mm | 0.4 | dust | 2017ApJ...845...10F |
| Disks in binaries (low end) | 1.15 cm2/g (also stated as 2 cm2/g in another section) | mm | n/a | dust | 2021MNRAS.501.4317P |
| Debris disks | 2.3 cm2/g | 1.3 mm | n/a | dust | 2017ApJ...842....8M, 2018ApJ...869...75M |
| Debris disks | 0.23 m2/kg | 1.33 mm (from 1 m2/kg at 1000 GHz, linear) | 1 | dust | 2025A&A...693A.151M |
| Debris disks | 2.7 cm2/g | 1.3 mm | n/a | dust | 2013ApJ...762L..21M |
| White-dwarf debris | 1.7 cm2/g | 870 um | n/a | dust | 2014MNRAS.444.1821F |
| Dense cores (OH94) | 0.899 cm2/g | 1.3 mm | n/a | dust | 2020ApJ...894L..14L, 2018ApJ...853..160C, 2017ApJ...849...68S, 2018ApJ...869...59W |
| Dense cores (OH94) | 1.11 cm2/g | 230 GHz | n/a | dust | 2017A&A...604A...6S, 2019A&A...621A.122B |
| Dense cores | 0.9 cm2/g at 1.3 mm; pack quotes "(lambda/1.3 mm)^beta", which inverts the usual kappa proportional to nu^beta. Verify in the paper; for a positive beta use (1.3 mm/lambda)^beta | 1.3 mm | 1.5 | dust | 2016ApJ...833..209O |
| Cores (OH94 thin ice, 870 um) | 1.89 cm2/g | 870 um | n/a | dust | 2024ApJS..270....9X, 2024ApJ...962...13C, 2026ApJ...999..194I, 2026ApJ...998..277M |
| Cores (OH5, 3 mm) | 0.18 to 0.2 cm2/g | about 3 mm | n/a | dust | 2024ApJ...961L..35M, 2025ApJ...988...95D |
| Cores / clumps (Hildebrand) | 0.1 cm2/g | 1000 GHz | 0.5 to 1.8 | gas | 2016A&A...596A..88L, 2017A&A...600A.141K, 2018MNRAS.475..448T, 2021A&A...648A..41V |
| Cores / clumps | 0.01 cm2/g | 230 GHz | n/a | gas | 2019ApJ...884...48C, 2015ApJ...808..102K, 2014ApJ...789L...4T |
| Cores / clumps | 0.00899 cm2/g | 1.3 mm | n/a | gas | 2018ApJ...855...24P, 2019NatAs...3..517Z |
| Clumps by L/M class | 0.005 (printed as g cm^-2; includes gas-to-dust 100) | 1.3 mm | n/a | gas | 2025A&A...701A.219N |
| Cores / clumps (multi-temperature MBB fits) | 0.1 cm2/g per gas+dust | 300 um | 1.8 | gas | 2024A&A...687A.217D, 2024A&A...686A.122A |
| Galactic Centre clouds | 0.04 cm2/g (nu/505 GHz)^1.75 | 505 GHz | 1.75 | gas | 2015MNRAS.449..715W, 2016MNRAS.457.4536W |
| Galaxies (Li and Draine type) | 0.0431 m2/kg | 352.6 GHz | 1.8 | dust | 2020ApJ...892...66M |
| Galaxies | 0.0484 m2/kg | 850 um | 1.8 | dust | 2018Sci...362.1034D |
| Galaxies | 0.15 m2/kg | 870 um | n/a | dust | 2014MNRAS.438.1267S |
| Galaxies | 0.051 m2/kg | 500 um | 1.8 | dust | 2024ApJ...963....1O |
| Galaxies | 0.0865 m2/kg | 351 GHz | n/a | dust | 2021A&A...652A..98G |
| Galaxies | 0.0431 m2/kg | 352.6 GHz | 1.8 | dust | 2025A&A...693A.190J |
| Galaxies | 0.077 m2/kg | 850 um | n/a | dust | 2025A&A...701A.120P, 2022MNRAS.512.2426M, 2019MNRAS.482.3135B |
| Galaxies | 2.64 m2/kg | 2.4 THz (125 um) | 2.0 in 2025ApJ...993L..40S | dust | 2025ApJ...993L..40S, 2024A&A...684A..33K |
| Galaxies (RJ-tail calibration) | alpha_850 = 6.2e19 / 6.7e19 / 1e20 erg s^-1 Hz^-1 Msun^-1 per gas mass (T 25 K in the first two) | 850 um | 1.8 to 2 | gas | 2024A&A...691A.248L, 2022A&A...664A..63X, 2023MNRAS.524..923Z |
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
| Debris belts, fixed: 100 K (warm inner belt) or 40 K (cold outer belt) | 2021AJ....162..235Y |
| 20 K (no counterpart), 50 K (IR or radio counterpart), 100 K (hot core) | 2020A&A...635A...2S |
| 35 K with IR counterpart, 15 K without | 2018A&A...615A...9P |
| T by L/M: 20 K (L/M < 1), 35 K (1 to 10), max(21.1 (L/M)^0.22, 35 K) above 10 | 2024A&A...690A.185W |
| T_d = 43 (L/Lsun)^0.25 K | 2024A&A...690A..46S |
| T_f = 20 K (10-40) for L/M < 1, 30 K (10-50) for 1-10, 40 K (20-60) above 10; 1000 Monte Carlo runs | 2025A&A...701A.219N |
| T_d = CH3OH excitation / rotational temperature | 2025ApJ...991...59B, 2026ApJ..1003..219W |
| T_d = average COM rotational temperature (99 to 137 K) | 2022MNRAS.512.4419P |
| T_d = NH3 kinetic temperature (14.2, 22.6 K) | 2024ApJ...961L..35M |
| 30 K single temperature, argued because mass is dominated by the outer-radius temperature | 2026A&A...706A.214V |
| Disk T_d = T_b in the optically thick inner region | 2021ApJ...923..121Y |
| T_d = gas temperature from NH3 or line rotational temperature | 2014ApJ...797...27F, 2016ApJ...828..100F, 2020ApJ...890...76N |
| Clump SED fit for T_d and beta (22 K / 2.1 prestellar, 28 K / 1.6 protostellar) | 2020ApJ...890...76N |
| High-z: 47 K, beta 1.6 (quasar hosts) | 2016ApJ...816...37V, 2017Natur.545..457D, 2024ApJ...968....9W |
| High-z: mass-weighted 25 K | 2020ApJ...892...66M |
| High-z: assumed 25 K (not described as mass-weighted) | 2024ApJ...963....1O |
| High-z: 35 K, beta 1.5 | 2017ApJ...851..145M |
| High-z: mass-weighted 25 K | 2025ApJ...993L..40S, 2025A&A...693A.190J, 2019ApJ...880...15K |
| High-z: 47 K prior (sigma 5 K), 35 K for companions | 2021A&A...652A..66P |
| High-z: lower T bound set by T_CMB(z) | 2025A&A...695L..15F |

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
| 200 | RSG envelopes; hot DOG at about 0.5 Z_sun | 2024A&A...681A..17D, 2025A&A...695L..15F |
| proportional to Z^-0.85, 100 at solar | metallicity-scaled galaxies | 2021A&A...655A..42S |
| "100 x 10^(Z-Zsun)" as printed; Z is not defined in the pack, and if Z is a log metallicity this falls at low Z, opposite to the usual trend. Verify before use | metallicity-scaled galaxies | 2020MNRAS.498.4109J |
| dust-to-gas 0.0024 / 0.0016 / 0.002 (Z-scaled) | LMC / SMC hot cores | 2026ApJ...999..194I, 2023ApJ...946L..41S, 2021ApJ...922..206S |
| 316 | LMC protostars, same ratio applied to comparison sources | 2025ApJ...991...59B |
| 30 | disks (typical value quoted) | 2023MNRAS.518.6092L |
| 4594 +/- 2848 (card: "final GDR (4594$\pm$2848)") | extremely metal-poor dwarf DDO 70 | 2020ApJ...892..147S (card) |
| 75 to 100, tuned to HD | TW Hya disk | 2015ApJ...799..204C |

## Count membership (for the SKILL.md parameter table)

Regex matches on the pack's "Key parameters" and "Assumptions" lines (515 of 915 papers), hand-checked.
Dropped as false hits: for 20 K, CO freeze-out or abundance thresholds, T_CMB, T_CO and range-only mentions
(2017ApJ...851...85B, 2021A&A...652A.128J, 2016ApJ...827..142B, 2015A&A...575L...5H, 2020ApJ...904L...6A,
2015ApJ...805...21C, 2018A&A...615A..83V, 2018ApJ...862..102S, 2026ApJ...998..277M, 2026A&A...709A.173M,
2015ApJ...798L..23K, 2023MNRAS.522.2384M, 2025ApJ...993L..40S); for 0.9 cm2/g, values at 3 mm, 870 um,
600 um or 340 GHz and unrelated 0.90 fractions; for L^0.25, the two debris-belt blackbody laws.

- Gas-to-dust 100 (or dust-to-gas 0.01) (166): 2012ApJ...761L..20R, 2013A&A...552L..10S, 2013A&A...557A.133D, 2013ApJ...774...39A, 2013PASJ...65L..14F, 2014A&A...569A..11S, 2014ApJ...783L..13P, 2014ApJ...784...82M, 2014ApJ...785...44M, 2014ApJ...787...42C, 2014ApJ...791...20R, 2014ApJ...791...42Z, 2014ApJ...791L...6W, 2014ApJ...795L..25R, 2014ApJ...796....1T, 2014Natur.514..600D, 2015A&A...575L...5H, 2015A&A...583A..66H, 2015ApJ...799..204C, 2015ApJ...801...82H, 2015ApJ...802..125R, 2015ApJ...805...21C, 2015ApJ...805L..17B, 2015ApJ...812..134H, 2015ApJ...814...22E, 2015MNRAS.447.1826Z, 2015MNRAS.449..715W, 2016ApJ...816...37V, 2016ApJ...827..142B, 2016ApJ...831..101B, 2016ApJ...832..110C, 2017A&A...601A...5H, 2017A&A...601L...3P, 2017A&A...602A..19L, 2017A&A...603A..92V, 2017A&A...604A..60B, 2017A&A...606A.121L, 2017A&A...608A..22A, 2017ApJ...835...17M, 2017ApJ...835..213P, 2017ApJ...836....8T, 2017ApJ...838..114K, 2017ApJ...849...25L, 2017ApJ...851...85B, 2017ApJ...851L..23C, 2017MNRAS.468..685Q, 2017MNRAS.469.2230M, 2018A&A...614A.113H, 2018A&A...615A..83V, 2018A&A...617A..89C, 2018A&A...618A.164S, 2018ApJ...854..177V, 2018ApJ...859..111H, 2018ApJ...863...19A, 2018ApJ...869..115S, 2018ApJ...869..126L, 2018ApJ...869L..22W, 2018MNRAS.475..448T, 2018MNRAS.480.4991G, 2018Sci...362.1034D, 2019A&A...622A..75L, 2019A&A...623A..77S, 2019A&A...624A...7V, 2019A&A...626A..93V, 2019A&A...628A..27B, 2019A&A...628A..85V, 2019A&A...629A..29J, 2019A&A...629A.136S, 2019ApJ...871....5T, 2019ApJ...871..185L, 2019ApJ...871..251P, 2019ApJ...872...70T, 2019ApJ...880..157D, 2019ApJ...881L..42C, 2019ApJ...884...48C, 2019ApJ...886..102S, 2019ApJ...887...79H, 2019MNRAS.483..806R, 2019MNRAS.488.1005P, 2020A&A...633A.114S, 2020A&A...636A..26H, 2020A&A...644A..84M, 2020ApJ...890...76N, 2020ApJ...890L..14T, 2020ApJ...892..152H, 2020ApJ...894L..14L, 2020ApJ...895L..18B, 2020ApJ...896...43W, 2020ApJ...903...50E, 2020ApJ...904...37W, 2020ApJ...904...77G, 2020ApJ...904...78S, 2020ApJ...904..181L, 2020ApJ...904L...6A, 2020ApJ...905...25G, 2020ApJS..251...14H, 2020MNRAS.491..758A, 2020MNRAS.492.4847L, 2020MNRAS.496..394R, 2020MNRAS.498.4109J, 2020NatAs...4..142L, 2021A&A...645A..49G, 2021A&A...646A...3L, 2021A&A...647A.118L, 2021A&A...648A..33M, 2021A&A...650A..37D, 2021A&A...650A.142M, 2021A&A...650A.202R, 2021A&A...652A..66P, 2021A&A...652A..98G, 2021ApJ...907...94C, 2021ApJ...908..250H, 2021ApJ...910...75L, 2021ApJ...918...76C, 2021ApJ...921...97J, 2021MNRAS.503...77W, 2021MNRAS.506.4175M, 2021MNRAS.507.1886F, 2022A&A...661A..53V, 2022A&A...662A...8M, 2022A&A...665L...7S, 2022MNRAS.510.4485R, 2022MNRAS.512.4419P, 2022MNRAS.515.5730K, 2023Ap&SS.368...33M, 2023MNRAS.522.2384M, 2023MNRAS.525.2229M, 2023MNRAS.525.6146W, 2024A&A...682A..61C, 2024A&A...684A.200G, 2024A&A...684L..12S, 2024A&A...687A.217D, 2024A&A...687A.299L, 2024AJ....167...75H, 2024AJ....168..151J, 2024ApJ...961L..35M, 2024ApJ...962...13C, 2024ApJ...967..133S, 2024ApJ...968...10F, 2024ApJ...968L..11G, 2024ApJ...971L..23L, 2024ApJ...972..115C, 2024ApJ...973..135H, 2024ApJ...974..257Z, 2024ApJ...976..241Y, 2024ApJS..270....9X, 2024MNRAS.532.1752R, 2024RAA....24f5011X, 2024Sci...383..988B, 2025A&A...693A.286S, 2025A&A...694A..86Y, 2025A&A...694A.295P, 2025A&A...698A.165A, 2025A&A...698L..16S, 2025A&A...701A.219N, 2025ApJ...984L..16G, 2025ApJ...988...95D, 2025ApJ...995L..75C, 2025NatAs...9.1176R, 2026A&A...705A..96M, 2026A&A...706A.214V, 2026A&A...709A.173M, 2026A&A...710A.238D, 2026AJ....171..368M, 2026ApJ..1003..219W, 2026ApJ..1004L...6D
- Fixed T_d = 20 K for at least some sources (47; refresh recount added 2017ApJ...849...25L "20 K for starless candidates" and 2022ApJ...930L...3W "T_mean = 20 K for SR 12 AB"): 2017ApJ...849...25L, 2022ApJ...930L...3W, 2014ApJ...784...82M, 2015ApJ...801...82H, 2015ApJ...805L..17B, 2015ApJ...806...35J, 2015ApJ...807L...4F, 2016ApJ...828...46A, 2016ApJ...831..125P, 2016ApJ...833L...6C, 2016PASJ...68L...7T, 2017ApJ...843...45K, 2018ApJ...863...19A, 2019A&A...626A..11C, 2019A&A...628A..85V, 2019A&A...632A..83S, 2019ApJ...872...92F, 2020A&A...633A.114S, 2020A&A...642A.164V, 2020ApJ...892..152H, 2020ApJ...894L..14L, 2020MNRAS.492.4847L, 2021A&A...648A..33M, 2021A&A...649A.122P, 2021A&A...650A..37D, 2021A&A...653L...9V, 2021A&A...656A.150P, 2021ApJ...922..206S, 2021MNRAS.501.2934C, 2021MNRAS.501.4317P, 2022A&A...661A..53V, 2022A&A...662A...8M, 2023A&A...674A..66Z, 2024A&A...682A..61C, 2024A&A...692A.155K, 2024ApJ...968L..11G, 2024ApJ...971..176H, 2024Sci...383..988B, 2025A&A...694A..86Y, 2025A&A...696A.232G, 2025A&A...698A.165A, 2025A&A...701A.219N, 2025ApJ...994..214T, 2025ApJ...995...16Z, 2025ApJS..280...33Y, 2025NatAs...9.1176R, 2026A&A...706A.214V
- kappa = 10 cm2/g at 1000 GHz (12): 2016ApJ...828...46A, 2018A&A...619A.161C, 2019A&A...628A..85V, 2020ApJ...892..111F, 2020MNRAS.492.4847L, 2021A&A...648A..33M, 2023A&A...675A.131T, 2025A&A...693A..49S, 2025A&A...693A.286S, 2025A&A...694A.295P, 2026A&A...706A...4R, 2026A&A...706A.214V
- kappa = 2.3 cm2/g (at 230 GHz / 1.3 mm unless noted) (27): 2014ApJ...787...42C, 2015ApJ...798L..23K, 2016ApJ...827..142B, 2016ApJ...831..125P, 2016Natur.538..483T, 2017ApJ...842....8M, 2017ApJ...849..123M, 2018ApJ...869...75M, 2019A&A...626A..11C, 2019ApJ...872...92F, 2019ApJ...875...87D, 2019ApJ...883..180H, 2019MNRAS.488.1005P, 2020A&A...640A..19T, 2020AJ....159..288M, 2021A&A...656A.150P, 2021AJ....162..235Y, 2021ApJ...923..121Y, 2021MNRAS.501.2934C, 2022A&A...661A..53V, 2023A&A...674A..66Z, 2024A&A...686A.206Y, 2024A&A...688A.149D, 2024ApJ...966...32E, 2025A&A...696A.232G, 2025A&A...703A..15M, 2025NatAs...9.1176R
- kappa about 0.9 cm2/g near 1.3 mm (OH94-type) (25): 2015ApJ...806...35J, 2016Natur.538..483T, 2018ApJ...867...43T, 2018ApJ...869...59W, 2019A&A...623A..77S, 2019ApJ...886..102S, 2019ApJ...887...79H, 2020ApJ...894L..14L, 2020ApJ...904...78S, 2020ApJS..251...14H, 2021ApJ...910..148M, 2021MNRAS.503...77W, 2022MNRAS.512.4419P, 2023Ap&SS.368...33M, 2023MNRAS.525.2229M, 2024A&A...684L..12S, 2024ApJ...971..176H, 2024ApJ...972..115C, 2024ApJ...976..241Y, 2024RAA....24f5011X, 2025A&A...694A..86Y, 2025A&A...698L..16S, 2025ApJS..280...33Y, 2026A&A...709A.173M, 2026AJ....171..368M
- kappa 1.85 to 1.89 cm2/g near 870 um (7): 2020ApJ...890...76N, 2024ApJ...962...13C, 2024ApJS..270....9X, 2025A&A...696A...7L, 2025ApJ...991...59B, 2026ApJ...998..277M, 2026ApJ...999..194I
- T_d scaled as L^0.25 (7): 2016ApJ...819..102V, 2016ApJ...827..142B, 2016ApJ...831..125P, 2020ApJ...904...78S, 2025A&A...693A.286S, 2025A&A...694A.295P, 2025ApJ...994..214T
- T_d = 47 K (high z) (16): 2016ApJ...816...37V, 2017ApJ...836....8T, 2017MNRAS.465.4390B, 2018ApJ...866..159V, 2018MNRAS.479.1154B, 2018PASJ...70...36I, 2019ApJ...881...63N, 2020ApJ...895...74N, 2020ApJ...903...34A, 2021A&A...652A..66P, 2021ApJ...908..235I, 2022MNRAS.510.4976A, 2024ApJ...977..190X, 2024ApJ...977L..46B, 2025A&A...694A.171M, 2025A&A...700A.277C
- T_d = 25 K called mass-weighted (4): 2019ApJ...880...15K, 2024A&A...686A..64M, 2025A&A...693A.190J, 2025ApJ...993L..40S
- beta = 1 (21): 2013ApJ...774...39A, 2014ApJ...789L...4T, 2014ApJ...793....1Y, 2016ApJ...828...46A, 2017ApJ...843...45K, 2018A&A...615A...9P, 2018A&A...619A.161C, 2018ApJ...863...19A, 2019A&A...628A..85V, 2020ApJ...892..111F, 2020MNRAS.492.4847L, 2020MNRAS.496..394R, 2021A&A...648A..33M, 2022A&A...661A..53V, 2023A&A...675A.131T, 2025A&A...693A..49S, 2025A&A...693A.286S, 2025A&A...694A.295P, 2025ApJ...995...16Z, 2026A&A...706A...4R, 2026A&A...706A.214V
- beta 1.5 to 1.9 (69): 2014ApJ...785..111W, 2014ApJ...792...34O, 2014ApJ...796...84R, 2015A&A...574A..19S, 2015ApJ...800...70S, 2015ApJ...810...91H, 2015MNRAS.452...54M, 2015Natur.519..327W, 2016ApJ...816...37V, 2016ApJ...819...82S, 2016ApJ...833L...6C, 2016PASJ...68..103F, 2017A&A...602A..19L, 2017ApJ...836....8T, 2017ApJ...849...14S, 2017ApJ...849...25L, 2017ApJ...851..145M, 2017MNRAS.465.4390B, 2017MNRAS.468L..87C, 2018ApJ...866..159V, 2018MNRAS.479.1154B, 2018NatAs...2...56Z, 2018PASJ...70...36I, 2018Sci...362.1034D, 2019ApJ...871..170M, 2019ApJ...874...27T, 2019ApJ...880...15K, 2019ApJ...880..157D, 2019MNRAS.482.3135B, 2020ApJ...892...66M, 2020ApJ...895...74N, 2020ApJ...896...93H, 2020ApJ...903...34A, 2020ApJ...904...77G, 2020ApJ...904...78S, 2020ApJ...904..181L, 2020ApJS..251...14H, 2020MNRAS.499.5241C, 2021A&A...648A..41V, 2021A&A...650A.153D, 2021A&A...650A.202R, 2021A&A...652A.128J, 2021A&A...654A..90L, 2021A&A...655A..42S, 2021ApJ...908...15S, 2021ApJ...908..235I, 2021MNRAS.503...77W, 2022A&A...662A...8M, 2022A&A...664A..63X, 2022MNRAS.510.4976A, 2022MNRAS.515.1751W, 2023Ap&SS.368...33M, 2023MNRAS.524..923Z, 2023MNRAS.525.2229M, 2024A&A...686A.122A, 2024A&A...687A.217D, 2024A&A...691A.248L, 2024ApJ...963....1O, 2024ApJ...964..146F, 2024ApJ...970...30M, 2024ApJ...977..190X, 2024ApJ...977L..46B, 2025A&A...693A.190J, 2025A&A...694A..86Y, 2025A&A...694A.171M, 2025A&A...695L..18M, 2025A&A...696A..33P, 2025ApJ...995..150K, 2026A&A...709A.173M
- mu = 2.8 to 2.86 (23; exactly 2.8 or 2.80 in 20, 2.81 in 2024ApJS..270....9X and 2024RAA....24f5011X, 2.86 in 2022MNRAS.515.5730K): 2017A&A...604A..60B, 2018ApJ...869..115S, 2019A&A...628A..27B, 2019ApJ...886..102S, 2019MNRAS.483..806R, 2020ApJ...890...76N, 2020ApJ...892..152H, 2020ApJ...904..181L, 2020ApJS..251...14H, 2021A&A...650A.202R, 2022MNRAS.512.4419P, 2022MNRAS.515.5730K, 2023MNRAS.525.6146W, 2024ApJ...961L..35M, 2024ApJ...962...13C, 2024ApJ...968...10F, 2024ApJ...972..115C, 2024ApJ...976..241Y, 2024ApJS..270....9X, 2024RAA....24f5011X, 2025A&A...694A..86Y, 2025ApJ...988...95D, 2026ApJ..1004L...6D
-   of which explicitly identify the H2 convention (13; 11 at 2.8, 2 at 2.81): 2017A&A...604A..60B, 2019A&A...628A..27B, 2019ApJ...886..102S, 2020ApJ...890...76N, 2020ApJ...904..181L, 2020ApJS..251...14H, 2021A&A...650A.202R, 2022MNRAS.512.4419P, 2023MNRAS.525.6146W, 2024ApJ...961L..35M, 2024ApJS..270....9X, 2024RAA....24f5011X, 2025A&A...694A..86Y
- mu = 2.3 to 2.37 (12): 2014A&A...569A..11S, 2016ApJ...823..160D, 2016PASJ...68L...7T, 2017A&A...606A.121L, 2017ApJ...849...25L, 2019A&A...628A...2B, 2019ApJ...884...48C, 2020A&A...644A..84M, 2021ApJ...907...94C, 2023MNRAS.518.6092L, 2024RAA....24f5011X, 2026A&A...705A.203W
- mu_H = 1.41 (per H) (4): 2023Ap&SS.368...33M, 2023MNRAS.525.2229M, 2026AJ....171..368M, 2026ApJ...998..277M

Refresh recount (2026-11-01): the same regex over the 3,500-paper pack's Key parameters and Assumptions lines
(lines 154 to 1559, 515 distinct bibcodes) gave 60 bibcodes with "20 K"; 13 were dropped as above (CO freeze-out or
abundance thresholds, T_CMB, T_CO, ranges such as 10-20 K, the 25 to 20 K variation test in 2025ApJ...993L..40S)
leaving 47. The mu regex ("mu", "molecular weight" or "mass per" within 40 characters of 2.8x) gave 23.

## Opacity uncertainty examples (moved from SKILL.md Pitfalls)

About 25% (2021A&A...655A..98A, not propagated); 30% kappa giving 33% in mass (2021A&A...650A.202R); factor 2
(2018ApJ...855...24P, 2015ApJ...808..102K, 2020ApJ...903...34A at least); factor 2-3 (2016A&A...593L..14F); factor 3
between Hildebrand and OH94 (2014ApJ...796....1T); about 4 vs OH94 (2020ApJ...896...35J); factor 3-5 for a debris
belt (2018ApJ...869...10M).

## Settings cards flag as unstated (pack section counts, several wordings each)

CASA version (46, plus 40 under other wordings); self-calibration intervals (32 + 21 + 12 and smaller variants);
line-free channels (21 + 18 + 15 + 15 + 12 and more); flux-scale uncertainty (14 + 9 + 8 + 7); PB correction (12 + 8).

## Software (pack aggregates, all 915 papers)

Two labels for one tool are listed separately; their sum may overcount, overlap not checked.

| Tool | Papers | What it is used for |
|---|---|---|
| CASA | 37 (+5 casa imfit, +4 imfit, +3 tclean) | continuum imaging, `imfit` Gaussian fluxes, `uvmodelfit`, simulated observations of models |
| RADMC-3D / radmc3d | 34 + 3 | dust RT; flux limit to disk mass limit (2019MNRAS.488.1005P, 2020MNRAS.498.1319M) |
| DALI | 23 | thermochemical disk models giving gas masses (2025A&A...693A.286S) |
| MCFOST | 22 | disk RT and SED fitting |
| emcee | 21 | MCMC for SED and visibility fits; upper limits as a likelihood penalty in 2021A&A...652A..66P |
| MAGPHYS | 15 | galaxy SED fits giving dust mass (fixed beta is a bias source per 2024MNRAS.535..729P) |
| CIGALE | 13 | galaxy SED fits incl. dust mass (2025ApJ...995L..63L, 2021A&A...654A..90L) |
| LIME | 9 | non-LTE line RT for envelopes and disks |
| lifelines, ASURV, linmix / linmix_err | 7, 4, 5 + 3 | censored statistics on dust-mass samples |
| GILDAS, MIRIAD; astrodendro, Clumpfind | 7, 5; 5, 3 | imaging outside CASA; core extraction |
| SciPy | 6 | clump modified-blackbody least squares (2020ApJ...890...76N (card)); `curve_fit` of an adapted P23 disk SED model (2025A&A...694A.295P); plain KS test (2025A&A...693A.286S) |
| optool, dsharp_opac, OpacityTool | 4, 4, 3 | grain-size-dependent opacities (2025A&A...696A.232G) |
| MCMax / mcmax3d, DUSTY, ProDiMo | 5 + 3, 4, 2 | disk and envelope RT or thermochemistry |
