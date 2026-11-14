# Parameter lists for gas-mass conversion (from the gas-mass-co-conversion pack)

Every value below is taken from the pack's "Key parameters", "Assumptions" or excerpt lines, with the paper
that used it. A bibcode marked "(card)" has no line in the rebuilt pack (it is only listed bibliographically);
its value was checked in that paper's methods card. Units: alpha in Msun (K km/s pc^2)^-1, X_CO in
cm^-2 (K km/s)^-1.

## How the counts were made

The rebuilt pack prints 700 "Key parameters" entries (340 distinct bibcodes) and 700 "Assumptions" entries
(352 distinct bibcodes); both lists end with "... N more" (186 and 616 entries omitted). Together the printed
entries cover 450 distinct bibcodes of the pack's 876. Each count below is the number of distinct bibcodes
whose printed entries match a regular expression for that value (for example `alpha_?co ... = 4.3|4.35|4.36|4.4`),
so it is a lower bound and not comparable with the counts of the earlier 360-paper pack. The 3.6, 6.5, r41,
X_CI = 3e-5 and alpha_850 counts were also read by hand; the others were not filtered further.

## Summary table

| Parameter | Common choice | Range seen | Distinct bibcodes (count) | Examples |
|---|---|---|---|---|
| alpha_CO, Galactic (incl. He) | 4.3-4.4 | 4.3, 4.35, 4.36, 4.4 used interchangeably; 4.3 +/- 1.3 with an error | 46 | 2017ApJ...835..278S, 2021A&A...656A..60A, 2021A&A...654A..69S, 2023A&A...673A..46B (4.3 +/- 1.3) |
| alpha_CO 4.6 (older Galactic / disk value) | 4.6 | | 3 | 2018Sci...362.1034D, 2017MNRAS.470.3775V (0.8 for mergers); SMGs: 2014ApJ...783...84S |
| X_CO, Galactic (no He) | 2e20 | 1.8e20 to 4.7e20 | 39 at 2e20 | 2014ApJ...784...78R, 2018ApJ...865...13T, 2024ApJ...963....1O, 2022MNRAS.510.4485R (+/- 0.4 dex); 3e20: 2020MNRAS.496.4061D; 4.7e20: 2017ApJ...846...73T (card) |
| alpha_CO, ULIRG / merger / SMG / QSO host | 0.8 | 0.6 to 1.5; 1 for SMGs in some papers | 46 quote 0.8 (some as one of two values) | 2017ApJ...843...18V, 2019ApJ...887...74F, 2024ApJ...977..198L, 2020MNRAS.496..598C; 1.0: 2018Natur.553...51M (card), 2025ApJ...987..158F; 1.1: 2019ApJ...881...43K, 2015ApJ...812L..23S (average of its two dynamical values, applied to unresolved sources) |
| alpha_CO, high-z star-forming galaxies | 3.6 | 3.6 to 10.8 when scaled with stellar mass | 10 (complete list below) | see the 3.6 row of the environment table |
| alpha_CO, Scoville convention | 6.5 (from X_CO = 3e20 with He) | | 2 | 2016ApJ...820...83S, 2017ApJ...837..150S |
| alpha_CO, low metallicity | scale with Z | 8 to 110 (CO 2-1 at 110) | not counted | 4.35 Z'^-1.6 (2021A&A...650A.134P); 15 at 12+log(O/H)=8.1 (2021ApJ...915...46C); 17 at 8.3 (2025A&A...700A.165B (card)); 110 +/- 30 (2017ApJ...835..278S) |
| alpha_CO, outflows | 0.8, optically thin 0.3-0.34 as lower bound | 0.13 to 3.4 | not counted | 2015A&A...580A...1M, 2018ApJ...863..143C (2.1 +/- 1.2), 2019MNRAS.489.1927S (2.1, range 0.8-3.4), 2018A&A...612A..29B (0.13-0.8), 2018ApJ...867..111Z (thin 0.34), 2025A&A...699A..83A (0.8 +/- 0.5) |
| alpha_CO, non-LTE (RADEX, x_CO = 3e-4) | about 1.1 | 0.9 to 1.5 | 2 | 2024ApJ...971..176H, 2014ApJ...796L..15S |
| r21 = T_b(2-1)/T_b(1-0) | 0.7-0.8 | ordinary disks and galaxies 0.4 to 1.2; nuclei and outflows 1.12 to 1.4; optically thin warm gas about 3-4; 2.2-2.5 adopted for the NGC 1068 CND and torus | 70 state a 2-1/1-0 ratio | 0.65: 2021A&A...650A.134P, 2022A&A...659A..46B, 2025ApJ...985...14L; 0.7-0.8: 2018ApJ...860..172S (card), 2017MNRAS.466.2825B, 2020ApJ...902..109B; 1: 2017ApJ...835..278S; observed 0.4-1.2 across AGN samples: 2020MNRAS.498.1560J; 1.4: 2018ApJ...863..143C; thin 3-4: 2018ApJ...867..111Z; 2.2-2.5: 2019A&A...632A..61G (card), 2024A&A...689A.347G |
| r31 = T_b(3-2)/T_b(1-0) | 0.5-0.8 | 0.27 to 1.0 in galaxies; 2.0 to 2.9 adopted for AGN tori (stated as brightness-temperature ratios) | 38 | 0.5: 2021A&A...654A..69S, 2025ApJ...993L..40S; 0.8: 2019ApJ...887...74F, 2024ApJ...963....1O; 0.31: 2022A&A...659A..46B; 0.97: 2024ApJ...964...95S; 0.55 and 1.0: 2022MNRAS.514.2346K; 0.27: 2021A&A...656A..60A; 2.0-2.9: 2021A&A...652A..98G, 2019A&A...632A..61G (card) |
| r41 = T_b(4-3)/T_b(1-0) | 0.4-0.6 | 0.22 (measured, CGM tail) to 1 (QSO); values above 1 are inverse or flux-type ratios, check | 15 | 0.22 +/- 0.11 tail, 0.67 BCG: 2024A&A...689A..67G; 0.33: 2023A&A...678A.183N; 0.41: 2018Natur.556..469M (card); 0.61: 2025A&A...693A..17D; 0.87 (QSO): 2024ApJ...977..198L; 1 (QSO): 2020MNRAS.493.3744F; L'(1-0)/L'(4-3) = 1: 2025A&A...694A.218B |
| r43 = T_b(4-3)/T_b(3-2) | 0.6-0.91 | 0.46 to 0.91 | (see examples) | 0.91 and 0.46 tested: 2019MNRAS.487.4305S (card); 0.6: 2017A&A...604A.117C (card) |
| r51, r54 (5-4 over 4-3) | SLED of a comparison population | r54 0.28; r51 0.23 (MS) to 0.6 (clumps, from simulations) | (see examples) | 2018MNRAS.477.4380S (card), 2017MNRAS.469.4683C (card), 2023MNRAS.521.5508H (r51 0.37) |
| r61, r71 | SLED of a comparison population | comparison SLEDs in 2020A&A...636A..37D (card): r61 0.34 (SMG) and 0.64 (QSO), r71 0.16 (SMG) and 0.48 (QSO). Adopted elsewhere: r61 0.92, r71 0.65 (2025A&A...695A..23S); r71 0.60 standard and 0.1 conservative (2026ApJ...997..218A) | (see examples) | 2020A&A...636A..37D (card), 2025A&A...695A..23S, 2026ApJ...997..218A, 2020NatAs...4..670A (card) (r71 0.24) |
| X_CI = [CI]/H2 | 3e-5 | 1e-5 to 8.4e-5 | 10 at 3e-5; 39 state an X_CI | 2017MNRAS.466.2825B, 2018ApJ...863..143C, 2021A&A...645A.120F, 2024A&A...689A..67G, 2025ApJ...993L..40S; 1.6e-5: 2021ApJ...909..181L, 2021A&A...654L...8C; 8.4e-5: 2024ApJ...977..198L |
| Tex for [CI] | 30 K | 25 to 31.8 K where stated | (see examples) | 30 K: 2017MNRAS.466.2825B, 2018ApJ...863..143C, 2025ApJ...987..158F; 29.1 K: 2024ApJ...977..198L; 31.8 K: 2025A&A...696A..83A; 25 K: 2025ApJ...993L..40S; 26 K adopted from literature averages with [CI](2-1)/[CI](1-0) = 0.47, not measured: 2021A&A...654L...8C |
| Q10 | 0.46-0.48 | 0.35 to 0.6 | (see examples) | 0.48: 2021A&A...645A.120F, 2023MNRAS.525.5831K, 2022PASJ...74..407U; 0.46: 2025ApJ...987..158F; 0.6: 2017MNRAS.466.2825B, 2024A&A...687A.288G; 0.35: 2021ApJ...909..181L |
| Q21, A21 for [CI](2-1) | Q21 0.5-0.57, A21 2.68e-7 s^-1 | Q21 0.03 to 0.4 (tested or LVG-derived) | 4 | 2016A&A...591A..73G, 2019A&A...624A..81M (0.5), 2024A&A...685A.138V (card), 2024A&A...689A..67G |
| alpha_[CI] | 7.3-17 for [CI](1-0); depends on X_CI and helium | 34 for [CI](2-1) (0.4 dex) | 5 | 2020ApJ...897L..19M (7.3), 2018ApJ...863..143C (9.43), 2025A&A...694A.218B (16.2), 2023MNRAS.521.5508H (17.0, with helium); (2-1): 2026ApJ...997..218A |
| CO/H2 abundance (Galactic sources, disks) | 1e-4 | 1.6e-5 (LMC) to 7e-4 in clouds and disks; 1e-3 in carbon-rich merger ejecta | 23 at 1e-4 | 2021A&A...648A..41V, 2017ApJ...846L..26W, 2024ApJ...969L...6Z; 2e-4: 2021A&A...646A...1K; 1.6e-5: 2019PASJ...71...44H; 7e-4: 2025ApJ...984L..19Y; 1e-3: 2018MNRAS.481.4931E |
| Helium factor on H2 mass | x1.36 | | 32 mention 1.36 or helium | 2018ApJ...853..149S (card), 2021ApJ...909..181L, 2024ApJ...971..176H |
| Mean molecular weight | mu_H2 = 2.76-2.8 (mass per H2 molecule); mu_p = 2.37 (mass per free particle, for number densities and pressure) | | (see examples) | mu 2.8 per H2: 2024ApJ...961..228S, 2018ApJ...865..131L; 2.37: 2017ApJ...846L..26W |
| alpha_850 (dust RJ) | 6.7e19 erg/s/Hz/Msun | 0.79e20 to 1.0e20 in the original calibration; 2.2e20 to 2.4e20 for SMGs cross-calibrated with alpha_CO = 1 | 5 | 2017ApJ...837..150S, 2017ApJ...844..123F (L850/Mgas = 6.7e19), 2022ApJ...929..100K; 1e20: 2023MNRAS.524..923Z; 7.3e19 (7.3e12 W/Hz/Msun): 2025A&A...694A.218B; original calibration: 2014ApJ...783...84S; SMGs: 2025ApJ...987..158F |
| Line-detection threshold | 3 sigma | 3 to 5 sigma | (see examples) | 2020ApJ...902..109B, 2024ApJ...977..198L, 2021ApJ...909..181L; 5 sigma: 2019PASJ...71...40T (card) |

## alpha_CO / X_CO by environment

| Environment | Values used | Papers |
|---|---|---|
| Milky Way, with helium | 4.3 | 2016ApJ...820L..39N (card), 2017ApJ...851...18L, 2018ApJ...854...83T, 2019BAAA...61..134V, 2025A&A...701A.113M (card) |
| | 4.35 / 4.36 | 2013ApJ...769L..12L, 2017ApJ...835..278S, 2018ApJ...861L..18U (card), 2021A&A...656A..60A, 2025ApJ...990..221M (card), 2026A&A...705A.163H (card) |
| | 4.4 | 2018ApJ...860..103S, 2020MNRAS.494.2131F (card), 2020MNRAS.495.3840M (card), 2021ApJ...908...54W (card) |
| Milky Way / disks, older value | 4.6 | 2018MNRAS.478.3120A (card), 2019MNRAS.485.1595P (card), 2021AN....342.1160P, 2018Sci...362.1034D, 2019MNRAS.482.1499M (disk), 2020MNRAS.497.2771M (card) (disks, z~0.03-0.2), 2015A&A...580A...1M (regular gas), 2016A&A...595L...7D (card) (thick gas), 2019A&A...632A..66O (tails) |
| SMGs (one paper) | 4.6 | 2014ApJ...783...84S |
| Milky Way, X_CO form | 2e20 | 2014ApJ...784...78R, 2018ApJ...865...13T, 2021A&A...652A..98G, 2024ApJ...963....1O (30% uncertainty), 2025ApJ...992..211N (card) |
| | 1.8e20 to 2.8e20 | 2016ApJ...823...26E (card), 2016ApJ...831..161K (card), 2017ApJ...841...43E (card), 2016NatSR...626896A (card), 2019ApJ...870...39V (card) |
| | 3e20 to 4.7e20 | 2012A&A...538L...9H, 2020MNRAS.496.4061D, 2017ApJ...843..136E, 2017ApJ...846...73T (card) (4.7e20) |
| Scoville convention (X_CO 3e20 with He) | 6.5 | 2016ApJ...820...83S, 2017ApJ...837..150S, 2018ApJ...860..111D (card), 2019ApJ...880...15K (card), 2020ApJ...901...79A (card) |
| High-z star-forming galaxies, 3.6 (complete list of printed pack entries) | 3.6 | 2016NatAs...1E...3P, 2017MNRAS.468.4205K, 2020ApJ...902..109B, 2020ApJ...902..113I (3.6/7.2/10.8 by M*), 2020MNRAS.495.1760O (no helium), 2022A&A...665A..48M, 2023ApJ...953...75H, 2024A&A...691A.178B, 2025ApJ...988..182N, 2025ApJ...989..115T (1.0 for SMGs) |
| | 3.6, further examples outside the printed entries | 2016ApJ...833...69D, 2019ApJ...882..136A, 2019ApJ...882..137P (card), 2019ApJ...882..138D (card), 2020ApJ...902..110D (card), 2020ApJ...901...79A (card), 2020ApJ...901..141K (card) |
| Early-type / lenticular disks, r21 0.7 | 3.1 | 2016ApJ...823...51B (card), 2017ApJ...845..170B (card), 2024ApJ...975..179C (card) |
| Quasar hosts, r21 0.62 | 3.1 (0.3 dex) | 2021ApJ...908..231M |
| ULIRG, merger, SMG, QSO host | 0.8 | 2014ApJ...787...48X (card), 2017ApJ...843...18V, 2018Natur.556..469M (card), 2019ApJ...881...63N, 2020MNRAS.493.3744F |
| | 0.86 (0.5 dex error) | 2014ApJ...790..160S |
| | 1.0 to 1.5 | 2018Natur.553...51M (card), 2018ApJ...861...43P (card), 2020ApJ...898...61I (1.3, 0.4 dex), 2019ApJS..241...19I (card) (1.5 for CO 2-1) |
| | 1.1 | 2019ApJ...881...43K (X_CO 0.5e20), 2015ApJ...812L..23S |
| Starburst X_CO | 0.4e20 to 0.8e20 | 2015ApJ...801...63M (0.5e20, factor 2), 2017ApJ...836..130R, 2018ApJ...856...97S, 2024ApJ...964..166K |
| Galaxy centres / nuclei | about 1/4 Galactic | 2014A&A...567A.125G (1/(4 +6 -1)), 2019A&A...632A..33A |
| Outflows | 0.8; thin 0.25 to 0.34 | 2015A&A...580A...1M, 2016ApJ...832..142Z (card), 2017A&A...608A..38O, 2018ApJ...867..111Z (thin 0.34; 1-2 for the outflow) |
| | measured 2.1 +/- 1.2 ([CI]) | 2018ApJ...863..143C; 2.1 (0.8-3.4) in 2019MNRAS.489.1927S |
| Low metallicity, prescriptions | 4.35 Z'^-1.6 | 2021A&A...650A.134P, 2025A&A...698A.296R (card); metallicity-dependent (form not given in the card): 2021A&A...656A.133Q (card) |
| | 4.35 (Z/Zsun)^-1 | 2019Natur.569..519K |
| | f_metal x 4.36 | 2019PASJ...71...40T (card) (f_metal 1.1 at logM 11, 1.4 at 10.5) |
| | Genzel 2015, Accurso 2017, Tacconi 2018, Bolatto 2013 eq. 31 | 2024A&A...692A.215C (card), 2020ApJ...897L..30M (card), 2025ApJ...985..194P, 2024ApJ...976...88L (card) |
| Low metallicity, values | 8.4 | 2025A&A...699A.369V |
| | about 10 at 0.5 Zsun | 2017MNRAS.468.3468G (card) |
| | 17 at 12+log(O/H)=8.3 | 2025A&A...700A.165B (card) |
| | about 18 at 0.3 Zsun | 2019ApJ...882....1L (card) |
| | 85 to 110 (CO 2-1, dust-based) | 2017ApJ...835..278S |
| Diffuse / CO-dark gas | X_CO 14e20 | 2020ApJ...889L...4L (card) |
| Per transition | (2-1) 6.2 to 6.7 | 2018ApJ...868L..38G, 2024PASA...41...76Z (card) |
| | (3-2) 17.4 (Galactic, r31 0.25) | 2018ApJ...860..172S (card) |
| | (3-2) 0.3-0.7 (LVG); 0.8 to 1 | 2026ApJ..1003..231W (card), 2024A&A...682A.182G (card), 2025ApJ...995..219F (card) |

## Measured alpha_CO in the pack

| Method | Value | Paper |
|---|---|---|
| Dust (resolved, 37 galaxies) | (1-0) 4.2 +1.9/-2.0; (2-1) 9.3 +4.6/-5.4; slope -0.50 with Sigma_star for 2-1 | 2024ApJ...964...18C |
| Dust, dwarf galaxy | 85 to 110 for CO(2-1) | 2017ApJ...835..278S |
| Dust, AGN nucleus | about 1/4 Galactic | 2014A&A...567A.125G |
| [CI](1-0) | 2.0 +/- 1.0 at z~4 | 2017MNRAS.466.2825B |
| [CI](1-0), merger | 2.1 +/- 1.2 (outflow), 3.2 +/- 1.8 (systemic) | 2018ApJ...863..143C |
| Dynamics | 0.6 +/- 0.3 and 1.6 +/- 0.6 at z~1.6 | 2015ApJ...812L..23S |
| 13CO LTE | 2.26 (X_CO 1.04e20) | 2017ApJ...848..101V |
| LVG | (3-2) 0.3-0.7 | 2026ApJ..1003..231W (card) |
| Known mass, Galactic centre CND | 4.5 +/- 2.5 | 2025ApJ...995L..51G |
| Statistical scatter | 0.165 dex | 2025A&A...700A.165B (card) |

## Excitation ratios (brightness-temperature ratios unless noted)

| Ratio | Values and populations | Papers |
|---|---|---|
| r21 | 0.65 to 0.8 for nearby disks | 0.65: 2021A&A...656A.133Q (card), 2025ApJ...988..263Z (card); 0.7: 2018ApJ...857...19F, 2019A&A...623A..66B; 0.77-0.8: 2017ApJ...842L..21N (card), 2024ApJ...969..122Y (card), 2020MNRAS.494.2131F (card) |
| | 0.4 to 1.2 observed across AGN samples (0.8 adopted) | 2020MNRAS.498.1560J |
| | 0.9 to 1 (LIRG, thermalised) | 2019MNRAS.482L..65K (card), 2016A&A...594A..81P (card), 2019A&A...621A..83S (card), 2024ApJ...977...36B (card) |
| | 1.12 to 1.4 (nuclei, outflows) | 2021A&A...656A..60A, 2018ApJ...863..143C |
| | about 1 if thick, up to about 3-4 if optically thin (warm LTE gas) | 2018ApJ...867..111Z |
| | 2.2 (CND), 2.5 (torus), stated as brightness-temperature ratios | 2019A&A...632A..61G (card) |
| | flux-density ratios about 3 to 4 (not r21) | 2018ApJ...853..149S (card), 2016A&A...595L...7D (card) |
| r31 = T_b(3-2)/T_b(1-0) | 0.5 to 0.8 | 2024ApJ...963....1O, 2019ApJ...887...74F, 2016NatAs...1E...3P, 2018MNRAS.479.2126F (card), 2025ApJ...995L..63L (card) |
| | 0.27 to 0.42 | 2021A&A...656A..60A, 2019ApJ...882..136A, 2021A&A...646A.127H (card) |
| | 0.55 and 1.0 | 2022MNRAS.514.2346K |
| | 2.0 to 2.9 (AGN tori, stated as brightness-temperature ratios) | 2021A&A...652A..98G, 2019A&A...632A..61G (card) |
| r41 = T_b(4-3)/T_b(1-0) | 0.22 +/- 0.11 (CGM tail) and 0.67 +/- 0.07 (BCG), measured | 2024A&A...689A..67G |
| | 0.31 to 0.63 (SMG, MS and lensed galaxies) | 2019ApJ...882..136A, 2023A&A...678A.183N, 2018Natur.556..469M (card), 2024ApJ...977..251H (card), 2024ApJ...970...30M, 2025A&A...693A..17D |
| | 0.85-0.87 (QSO and companions), 1 (QSO) | 2024ApJ...977..198L, 2020MNRAS.493.3744F |
| | above 1 (2.4, 3.0): check direction and definition before use | 2025ApJ...988..182N, 2024A&A...687A.288G |
| r43 = T_b(4-3)/T_b(3-2) | 0.6, 0.91 (0.46 tested) | 2017A&A...604A.117C (card), 2019MNRAS.487.4305S (card) |
| r51 (5-4 over 1-0), r54 (5-4 over 4-3) | r51 0.23 (MS), 0.6 (clumps, from simulations); r54 0.28 +/- 0.05; r51 0.39 | 2017MNRAS.469.4683C (card), 2018MNRAS.477.4380S (card), 2016ApJ...827...34O (card) |
| r61, r71 (over 1-0) | comparison SLEDs r61 0.34/0.64 and r71 0.16/0.48 (SMG/QSO) | 2020A&A...636A..37D (card) |
| | adopted r61 0.92, r71 0.65 | 2025A&A...695A..23S |
| | r71 0.60 (standard quasar) and 0.1 (conservative) | 2026ApJ...997..218A |
| | r71 0.24 | 2020NatAs...4..670A (card) |
| AGN vs non-AGN sets | AGN r21 0.68, r31 0.59, r41 0.37; control r21 0.6, r31 0.5 | 2024A&A...691A.178B |

## [CI] parameters

| Parameter | Values | Papers |
|---|---|---|
| X_CI | 3e-5 | 2016A&A...591A..73G, 2017MNRAS.466.2825B, 2018ApJ...866L..12G (card), 2019MNRAS.482.3135B (card), 2020A&A...641A.155V (card), 2025ApJ...993L..40S |
| | 1.5e-5; 1e-5 (CGM region); 8.4e-5 (QSO) | 2021ApJ...908..163M (card), 2021A&A...645A.120F, 2024ApJ...977..198L |
| | scaled linearly with metallicity | 2024A&A...685A.138V (card) |
| Tex | 30 K; 29.1 K; 31.8 K; 25 K | 2017MNRAS.466.2825B, 2018ApJ...863..143C, 2019ApJ...887..144J (card); 2024ApJ...977..198L; 2025A&A...696A..83A; 2025ApJ...993L..40S |
| Tex adopted, not measured | 26 K with [CI](2-1)/[CI](1-0) = 0.47, both from literature averages | 2021A&A...654L...8C |
| (not a [CI] Tex) | 2021A&A...645A.120F adopts a median Q10 = 0.48 and uses Tdust = 40 K for its continuum cross-check | 2021A&A...645A.120F |
| Q10 | 0.35, 0.457, 0.48, 0.5, 0.6 | 2019MNRAS.482.3135B (card), 2024ApJ...977..198L, 2021A&A...645A.120F, 2021ApJ...908..163M (card), 2017MNRAS.466.2825B |
| A10 | 7.93e-8 s^-1 | 2017MNRAS.466.2825B, 2018ApJ...856...72O, 2021A&A...645A.120F |
| [CI](2-1) | Q21 0.57, A21 2.68e-7 s^-1; Q21 0.05-0.4 tested | 2016A&A...591A..73G, 2024A&A...685A.138V (card) |
| Measured [CI]/H2 | 1.9e-5 +/- 0.4e-5 (CO-based), 2.2e-5 +/- 0.3e-5 (dust-based) | 2020ApJ...902..109B |

## CO abundance and isotopologue ratios (Galactic sources, disks, ejecta)

| Quantity | Values | Papers |
|---|---|---|
| CO/H2 | 1e-4 | 2017A&A...600A..62P, 2018A&A...618A.120L, 2021A&A...648A..41V, 2024ApJ...963...72O, 2021A&A...654L...8C |
| | 2e-4; 1.6e-5 (LMC); 5e-5 to 7e-4 (disks) | 2021A&A...646A...1K, 2019PASJ...71...44H, 2025ApJ...994...98F, 2025ApJ...984L..19Y |
| | 1e-3 (carbon-rich merger ejecta; evolved-star case, not for galaxies) | 2018MNRAS.481.4931E |
| 12CO/13CO | 50 to 77 | 2017ApJ...848..101V (50), 2016ApJ...828...46A (70), 2015ApJ...798...85P (76) |
| CO/C18O | 550 or 1650; 557; 570 +/- 130 | 2016ApJ...828...46A, 2025ApJ...994...98F, 2020MNRAS.496..394R |
| H2/13CO | 1.4e6 to 5e6 | 2024ApJ...964..166K, 2020ApJ...903...94M (card), 2024ApJ...966...51G (card) (3e6), 2016ApJ...831...32N |
| mu_p, mean mass per free particle (number densities, pressure) | 2.37 | 2017ApJ...846L..26W |
| mu_H2, mass per H2 molecule (M = mu_H2 m_H N(H2) A) | 2.76 to 2.8 | 2021A&A...648A..41V, 2024ApJ...961..228S |

## Other gas tracers

| Tracer | Conversion | Papers |
|---|---|---|
| HCN | alpha_HCN about 10 (6 to 40) | 2015ApJ...803...60S, 2018ApJ...858...90G, 2019ApJS..241...19I (card), 2018ApJ...868...95M |
| HCO+ | alpha_HCO+ about 10 | 2015ApJ...813..118M |
| [CII] | alpha_[CII] about 30 Msun/Lsun, 0.3 dex | 2020ApJ...905..147Y (card) |
| Dust RJ | alpha_850 6.7e19 (Td 25 K, beta 1.8); 1.0e20 +/- 0.23e20 (local), 0.79e20 (Planck) | 2016ApJ...820...83S, 2017A&A...606A..17M (card) (Td 25 K, beta 1.8), 2014ApJ...783...84S |
| Dust with gas-to-dust | 100; stellar-mass dependent; 200 | 2021A&A...652A..98G, 2018ApJ...856..118H, 2016ApJ...833...68A (card) |

## Per-pixel RADEX alpha_CO: validation steps (2024ApJ...971..176H)

- Model a fiducial N_CO per 15 km/s, then rescale to the real column with Delta v = 2.35 sigma_v from the
  CO(1-0) dispersion map, and rescale the modelled intensity by measured linewidth over 15 km/s.
- Grid-based Bayesian likelihood over the five integrated intensities; divide the summed posterior for each
  alpha_CO by the alpha_CO prior probability of the sampling space (the grid itself imposes a prior).
- Drop pixels with median alpha_CO < 0.1, chi2 > 10, best-fit values at the grid edge (X12/13 <= 30,
  log n >= 4.9, log N_CO(15 km/s) <= 16.1, log Tkin < 1.1) or very poorly constrained alpha_CO.
- The modelling is limited to regions with both 13CO(1-0) and 13CO(2-1) detections (mostly the nuclei and
  overlap region), so a cloud-scale average is biased; x_CO = 3e-4 is assumed and unconstrained.

## Software

From the rebuilt pack's software aggregate (software named in matched steps of all 876 papers; names
lower-cased there, only the top 40 names printed). Aliases merged by hand are noted. Tools from the earlier
version below the printed top 40 (lmfit, galmod, tirific, despotic, molpop-cep) are named without counts.

| Tool | Papers | What it is used for |
|---|---|---|
| casa (+ tclean, uvcontsub, casa imfit, casa immoments) | 79 (+10, 4, 4, 3) | imaging, continuum subtraction, moment maps, flux extraction (imfit 2D Gaussians in 2021ApJ...909..181L) |
| radex (+ myradex; multiline-bayesian-modeling code) | 26 (+3; 3) | non-LTE excitation; per-pixel alpha_CO (2024ApJ...971..176H); LVG Q21 (2024A&A...689A..67G); CMB effect on CO and [CI] (2025ApJ...987..158F) |
| emcee | 23 | MCMC for line-ratio, disk and regression fits (2024A&A...691A.178B) |
| cprops (+ cpropstoo), astrodendro, clumpfind | 15 (+5), 7, 3 | cloud decomposition before per-cloud luminous masses (2017ApJ...835..278S) |
| linmix | 11 | censored Bayesian regression with upper limits (2025ApJ...987..158F; linmix_err.pro in 2018ApJ...863..143C) |
| 3dbarolo (+ 3d-barolo), kinms (+ kinmspy_mcmc), kinemetry, mgefit | 8 (+3), 6 (+2), 3, 4 | dynamical masses compared with gas masses (2018MNRAS.479.5440L, 2021MNRAS.504.4123N) |
| radmc-3d, dali | 7, 7 | disk models where a gas mass is a model parameter (2018ApJ...854..130W) |
| magphys, cigale | 6, 6 | stellar masses, SFRs and L_IR for f_gas and t_dep (2025ApJ...987..158F) |
| PDR Toolbox (pdrtoolbox 4, pdr toolbox 4), cloudy | 8 entries, 8 | [CI]/CO/[CII] ratios to density and UV field (2020ApJ...902..109B, 2025ApJ...987..158F) |
| 3d-pdr | below the top 40 | 1D PDR grids for [CII]/[CI] and CO ratios (2017MNRAS.466.2825B) |
| gildas, miriad | 8, 4 | calibration and imaging outside CASA (e.g. 2021A&A...652A..98G) |
| imfit, pyspeckit, mpfit | 5, 3, 3 | Gaussian line and source fits (pyspeckit in 2018ApJ...865...13T and 2024ApJ...963....1O, card) |
