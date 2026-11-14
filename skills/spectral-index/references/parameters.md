# Spectral index: longer parameter tables

Every entry comes from the rebuilt `spectral-index` evidence pack (aggregate lines "Key parameters", "Assumptions",
"Settings cards flag as needed but not stated", "Software", and the paper excerpts). An entry marked "(card)" is a
paper the pack only lists by title; its value was checked verbatim against that paper's methods card. Papers whose
"beta" is a disk flaring index, Nuker shape, wind exponent, grain size index, spectral curvature, chemical rate
coefficient or X-ray/UV slope are excluded throughout.

## 1. Adopted (fixed) dust beta when it is not measured

**196 papers state one fixed dust beta** (my count). How it was made: a script pulled every Key-parameters or
Assumptions line containing "beta" or "β" (275 papers), parsed "beta = x" style values, then I removed by hand the
non-dust betas (2019A&A...622A..75L, 2019A&A...624A...7V, 2023A&A...677A..76P, 2024AJ....167...77D,
2024ApJ...970..114T, 2023MNRAS.518.6092L and 2016PASJ...68...43K are flaring or disk-model parameters;
2021ApJ...908...19B Nuker; 2022A&A...659L...1L size index; 2023ApJ...945...40C curvature; 2024A&A...681A..17D wind;
2022RAA....22f5021G chemistry; 2025A&A...701A..41D corona model), measured or fitted values (2024A&A...683A.141R,
2025A&A...694A.218B, 2020ApJ...904...78S) and multi-value or range entries (listed below), and added five lines the
parser missed (2021ApJ...918...76C, 2025ApJ...995..150K, 2024A&A...686A..64M, 2022MNRAS.514.2346K,
2021MNRAS.501.4317P). One paper is counted once. These are adopted assumptions, not measurements.

| beta | papers | bibcodes (value in brackets when the bin spans more than one value) |
|---|---|---|
| 0 | 1 | 2021A&A...655A..98A |
| 0.4-0.5 | 5 | 2014ApJ...787...42C (0.4), 2014ApJ...796....1T (0.5), 2015ApJ...798..124R (0.4), 2017ApJ...845...10F (0.4), 2019ApJ...878L...8T (0.5) |
| 0.7-0.93 | 3 | 2019ApJ...872...70T (0.93), 2023A&A...669A..90C (0.76), 2025Natur.641.1137B (0.7) |
| 1.0 | 26 | 2014ApJ...793....1Y, 2014Sci...345.1584B, 2016ApJ...826...16E, 2016ApJ...828...46A, 2018A&A...619A.161C, 2018ApJ...863...19A, 2018ApJ...863...94L, 2018MNRAS.473..879P, 2018MNRAS.475.5322S, 2019A&A...623A.150V, 2019A&A...623L...8B, 2019A&A...628A..85V, 2019ApJ...877L..25M, 2019ApJ...886....6T, 2019MNRAS.482..698C, 2019MNRAS.486.4114R, 2019NatAs...3..314L, 2020ApJ...898...10T, 2020MNRAS.496..394R, 2023A&A...675A.131T, 2024ApJ...973...42B, 2025A&A...693A..49S, 2025A&A...693A.286S, 2025A&A...694A.295P, 2025ApJ...993..120H, 2026A&A...706A.214V |
| 1.2-1.3 | 5 | 2014ApJ...795L..25R (1.2), 2017A&A...604A..60B (1.2), 2018ApJ...865..131L (1.3), 2020AJ....159...62C (1.2), 2023MNRAS.519.5807D (1.2) |
| 1.4 | 2 | 2020A&A...641A..97V, 2024ApJ...971L..23L |
| 1.46-1.55 | 36 | 2012ApJ...752L..30W (1.5), 2014ApJ...792...34O (1.5), 2014ApJ...796...84R (1.5), 2015ApJ...804..141Z (1.5), 2015ApJ...810...91H (1.5), 2015ApJ...812...27A (1.46), 2016ApJ...819...82S (1.5), 2016MNRAS.455.2745K (1.5), 2017ApJ...835...98U (1.5), 2017ApJ...836L...2B (1.5), 2017ApJ...849...25L (1.5), 2018AJ....156..239Z (1.5), 2018ApJ...856L..12N (1.5), 2018PASJ...70...65U (1.5), 2019A&A...622A..99L (1.5), 2019ApJ...871..170M (1.5), 2019MNRAS.483.1624B (1.49), 2020ApJ...895..142L (1.5), 2020ApJ...896..110L (1.5), 2020ApJ...905L..23M (1.55), 2021A&A...646A..25Z (1.5), 2021A&A...650A.202R (1.5), 2021A&A...652A.128J (1.5), 2022MNRAS.511.1408G (1.5), 2022MNRAS.514.5004L (1.5), 2023A&A...674A..76P (1.5), 2023A&A...675A..85M (1.5), 2024A&A...686A..64M (1.5), 2024A&A...686A.146Z (1.5), 2024A&A...691A.248L (1.5), 2024AJ....167...72D (1.5), 2024ApJ...966..120L (1.5), 2025A&A...702A.183H (1.5), 2025ApJ...992..103Z (1.5), 2025ApJ...993..200C (1.5), 2025ApJ...995..150K (1.5) |
| 1.6 | 25 | 2013ApJ...770...13W, 2013ApJ...773...44W, 2016ApJ...816...37V, 2017ApJ...836....8T, 2017ApJ...850..108W, 2017Natur.545..457D, 2018ApJ...854...97D, 2018ApJ...866..159V, 2018MNRAS.479.1154B, 2019ApJ...876...99S, 2019ApJ...880..157D, 2020ApJ...902..112B, 2020ApJ...903...34A, 2021A&A...645A..33B, 2021ApJ...908..235I, 2022MNRAS.510.4976A, 2024A&A...688A..30B, 2024ApJ...968....9W, 2024ApJ...972..116I, 2024ApJ...977L..46B, 2024RAA....24f5008M, 2025A&A...694A.171M, 2025A&A...695A..23S, 2025SciA...11.6953M, 2026MNRAS.546ag167S |
| 1.7-1.75 | 14 | 2016ApJ...833L...6C (1.7), 2017MNRAS.468L..87C (1.7), 2018ApJ...853..171G (1.75), 2018ApJ...861...14C (1.7), 2021MNRAS.501.4317P (1.7), 2021MNRAS.503...77W (1.75), 2022ApJ...927..218H (1.7), 2022MNRAS.514..578W (1.75), 2023MNRAS.525.2229M (1.7), 2023MNRAS.526.2077A (1.7), 2024A&A...691A.180F (1.7), 2024ApJ...976...29H (1.7), 2025A&A...701A..85K (1.7), 2026A&A...709A.173M (1.7) |
| 1.8-1.85 | 41 | 2014ApJ...785..111W (1.8), 2014ApJ...789L..36W (1.8), 2015ApJ...800...70S (1.8), 2015ApJ...811L...3T (1.8), 2017ApJ...835..213P (1.8), 2017ApJ...837..174O (1.8), 2017ApJ...840..101C (1.8), 2017MNRAS.468.4675D (1.8), 2018NatAs...2...56Z (1.8), 2018Sci...362.1034D (1.8), 2019ApJ...880...15K (1.8), 2019MNRAS.482.3135B (1.8), 2020ApJ...892...66M (1.8), 2020ApJ...896..127K (1.85), 2020MNRAS.496.4358I (1.8), 2020MNRAS.499.5241C (1.8), 2021A&A...654A..90L (1.8), 2021A&A...655A..42S (1.8), 2021ApJ...918...69U (1.8), 2021ApJ...919...30D (1.8), 2021MNRAS.505.1509S (1.8), 2022ApJ...930...32C (1.8), 2022MNRAS.514.2346K (1.8), 2023ApJ...944...49F (1.8), 2023MNRAS.524..923Z (1.8), 2024A&A...682L...5G (1.8), 2024A&A...686A.122A (1.8), 2024A&A...687A.217D (1.8), 2024ApJ...961...71F (1.8), 2024ApJ...963....1O (1.8), 2024ApJ...966...51G (1.8), 2024ApJ...970...30M (1.8), 2024MNRAS.533.2966Q (1.8), 2025A&A...693A.190J (1.8), 2025A&A...695L..18M (1.8), 2025A&A...696A..33P (1.8), 2025A&A...698A.204H (1.8), 2025A&A...704A.158C (1.8), 2025ApJ...987...77J (1.8), 2026A&A...706A.227G (1.85), 2026ApJ...997..218A (1.8) |
| 1.9-1.95 | 3 | 2016ApJ...826...26T (1.9), 2019ApJ...887...55C (1.95), 2021A&A...656A..46M (1.9) |
| 2.0 | 35 | 2013ApJ...767...88W, 2014ApJ...787..112C, 2016ApJ...822...80S, 2016ApJ...823L..12G, 2016ApJ...826..112S, 2017A&A...605A.105C, 2017ApJ...845L...5I, 2018A&A...616L..10F, 2019PASJ...71...73T, 2020A&A...635A...2S, 2020A&A...644A..84M, 2020ApJ...889..172K, 2020ApJ...891..113R, 2020ApJ...902...78R, 2021ApJ...918...76C, 2021Galax...9..115D, 2021MNRAS.500.3667S, 2021MNRAS.505.4838L, 2022A&A...664A..60B, 2022MNRAS.512.2426M, 2022MNRAS.515.3126I, 2022MNRAS.515.5730K, 2023MNRAS.521.2962F, 2023MNRAS.521.5508H, 2024A&A...692A..22Z, 2025A&A...696A..83A, 2025A&A...699A.369V, 2025ApJ...985..222H, 2025ApJ...985L...8U, 2025ApJ...989...83B, 2025ApJ...990L..61C, 2025ApJ...994..225N, 2026A&A...708A.251X, 2026A&A...713A.167D, 2026MNRAS.546ag049F |

Most common single values: 1.8 (39 of the 41 in the 1.8-1.85 bin), 1.5 (33 of 36 in 1.46-1.55), 2.0 (35), 1.0 (26),
1.6 (25). In the 1.6 group, 15 of 25 lines pair it with T_dust = 47 K. The 1.0 group is mostly disks and
protostars; the 1.8 and 2.0 groups are mostly galaxies, clumps and hot cores (my reading of the same lines).

Not counted above (several values, a range, or a prior):
- Two or more fixed values: 1.5 and 2.0 (2024BSRSL..93..601H); 1.5 warm and 2 cold (2021ApJ...908...15S); 1.5 and
  1.7, plus 1.6 (2020ApJ...895...74N); 1.5 for one index, 1.8 for the cloud (2022A&A...662A...8M); 2.0 fixed with
  1.8 inside a gas-to-dust calibration (2022MNRAS.510.3734D); 1.8 as an alternative model (2020A&A...643A...5D);
  beta 0 and 1 (alpha 2 and 3) as two cases (2025ApJ...979..142N); bounds 0.5-4 with beta 2 for detection limits
  (2024MNRAS.530.4887W).
- Ranges: 1.2-2.0 (2017Sci...355.1285N); 1-1.8 (2020ApJ...890..129K); 0-2 to bound T_SED (2021A&A...653A.117B);
  0-2 (gamma 2-4) in a dust + free-free model (2023A&A...680A.110C); MCMC over 1.3-2.5 (2024A&A...684A..56K, card).
- Priors on a fitted beta: Gaussian 1.7 ± 0.5 (2019ApJ...882..168P); Gaussian 1.8, sigma 0.25 (2026A&A...706A.174A);
  uniform 1.0-2.0 (2019MNRAS.489.3939C); uniform 1.0-3.0 (2021ApJ...919...30D, which also uses a fixed-1.8 model and
  is counted above); box 1-2.5 (2021A&A...652A..66P); 1-3 (2025A&A...695L..15F); uniform 0-0.5 in a 1000-draw
  bootstrap (2025NatAs...9.1176R); prior 2.0 (2015A&A...577A..30A).
- 2024A&A...686A.122A (counted at 1.8) explored ± 0.2; 2018NatAs...2...56Z (counted at 1.8) gives 1.5 as an
  alternative; 2014ApJ...795L..25R (counted at 1.2) chose 1.2 ± 0.1.

Author guidance (my recommendation, not a pack result): if beta is not measured, adopt the value used by the closest
physical analogue above and say so. The counts show what papers assumed, not how uncertain beta is for your source.
Choose physically justified alternative opacity laws and temperatures for that source and propagate them together,
because beta and T move a mass or tau estimate jointly.

## 2. Measured alpha and beta values

Values copied from pack result lines or (card) lines; sign convention as each paper reports it. Model assumptions are
kept out of this table (for example the HD 107146 model scales flux as nu^(2+beta) with beta = 0.4 fixed,
2015ApJ...798..124R, and NGC 3627 assumes a nonthermal index of -0.85, 2015ApJ...813..118M).

| object | value | bands | bibcode |
|---|---|---|---|
| GM Aur disk, disk-averaged | alpha 2.7 ± 0.2 | 1.1 / 2.1 mm | 2020ApJ...891...48H (card) |
| HD 141569 inner vs outer disk | alpha 1.81 ± 0.15 vs 2.28 (+0.43/-0.29) | joint MCMC visibility fit | 2018ApJ...859..103W |
| HD 107146 debris disk | alpha 2.42 ± 0.16, q 3.25 ± 0.09 | mm | 2015ApJ...798..124R (card) |
| HD 107146 debris disk | beta 0.3 ± 0.2, q 3.17 ± 0.11 | B6 + B7, beta_s 1.8 | 2026A&A...705A.196H |
| Fomalhaut debris ring | alpha_mm -2.73 ± 0.13 as printed, q 3.50 ± 0.14 | 350-6600 um | 2017MNRAS.466.4201W |
| HD 32297 debris disk | sub-mm alpha 2.4 | sub-mm | 2020ApJ...892...99C (card) |
| HH 900 protostar | alpha 2.2 ± 0.5 | four-band fit | 2020MNRAS.496..394R (card) |
| NGC6334I outburst | mean alpha MM1 2.9, MM2 3.2, MM4 2.4 | ALMA bands | 2017ApJ...837L..29H |
| Sgr B2 compact sources | 62 with alpha measured, 33 with alpha > 2 | 3 mm | 2018ApJ...853..171G |
| AB Aur disk | beta 0.2 ± 0.1 (thin, T = 39 K assumed) | four bands | 2024A&A...683A.141R |
| Seyfert starburst rings | alpha ≥ 2-3, read as dust | 230 / 351 GHz | 2021A&A...652A..98G (card) |
| Background galaxy | alpha about 2.5, beta about 0.5 | B6 / B7 | 2020ApJ...894...76W (card) |
| IMBH candidate CO-0.40-0.22* | alpha 1.18 ± 0.65 | 231 / 266 GHz | 2017NatAs...1..709O (card) |
| R Aqr compact centre | alpha 1.88 | 1.3 / 0.45 mm | 2024A&A...689A.317G (card) |
| Mira A | 1.71 ± 0.05 within B3, 1.54 ± 0.04 B3 to B6 | B3, B6 | 2015A&A...577L...4V (card) |
| RMC 127 LBV central object | alpha 0.78 ± 0.05 | 9-349.5 GHz | 2017ApJ...841..130A |
| Radio source projected near HR 8799 | alpha 0.69 ± 0.03 | 3 / 340 GHz | 2024RMxAA..60..355R (card) |
| MAXI J1348-630 (X-ray binary) | alpha 0.28 ± 0.02 | ALMA bands | 2024Ap&SS.369...18M (card) |
| NGC 3627 nucleus and two regions | mean alpha -0.10, -0.15, -0.27 | 33 / 94.5 GHz | 2015ApJ...813..118M (card) |
| Phoenix cluster source C1 | alpha -0.37 (ATCA + ALMA), -0.50 in-band | cm to 3 mm | 2020PASJ...72...62A (card) |
| rho Oph W filament, diffuse EME | alpha -0.78 ± 0.05 (fields range -0.16 to -1.06) | Band 1 | 2026A&A...707A.255C |

Fomalhaut sign note: the 2017MNRAS.466.4201W excerpt says it fits F_nu ∝ nu^alpha yet prints alpha_mm = -2.73,
with alpha_pl = 1.84 and q = 3.50. My check: q = (alpha_mm - alpha_pl)/beta_s + 3 gives (2.73 - 1.84)/1.8 + 3 = 3.49
with +2.73, and 0.46 with -2.73. The printed q only follows from the magnitude in the frequency convention. The pack
does not resolve the sign; normalise to S_nu ∝ nu^alpha before applying the q relation.

Reading guide (general practice, a diagnostic, not a classifier): in these examples dust-dominated sources show alpha
of roughly 2-4 and ionized winds, jets and synchrotron sources show alpha below about 1. The ranges overlap:
optically thick or scattering dust, cold dust outside RJ and mixed components can all give alpha near or below 2, and
a negative index at cm wavelengths can be EME/AME rather than synchrotron (2026A&A...707A.255C). Check temperature,
optical depth, morphology and cm data before naming a mechanism. Sign convention matters: S ∝ nu^-alpha in
2017MNRAS.469L.123O; a brightness-temperature index in wavelength in 2019ApJ...875...55W.

## 3. Thresholds and settings

How counts were made: my count of Key-parameters and Assumptions lines that state the setting for an alpha map,
alpha fit or index-derived quantity, one paper once, plus (card) entries.

S/N cuts for alpha maps or fits (12: 11 pack + 1 card; 3 sigma in 6):

| cut | bibcode |
|---|---|
| 2 sigma across all four spws | 2025A&A...703A..82S |
| S/N < 2.5 in either band masked | 2018A&A...616A..88V |
| > 3 in both bands | 2025A&A...698L..16S |
| s/n < 3 in any band masked | 2024A&A...683A.141R |
| I > 3 rms in each spw, 10% calibration in quadrature, fit accepted if chi^2 < 18.307 | 2026A&A...712A.244H |
| 3 sigma at 3 mm before applying its alpha scheme | 2024A&A...686A.122A |
| > 3 sigma pixels, 5.5 / 9 GHz index map | 2017ApJ...841..130A |
| > 3 sigma pixels, 33 / 94.5 GHz | 2015ApJ...813..118M (card) |
| > 4 sigma | 2023ApJ...948..110Y |
| 5 sigma across all four bands | 2023A&A...680A.110C |
| 5 sigma lens-plane mask, S/N > 3.5 at 33 GHz source-plane | 2023MNRAS.524.3671Z |
| S/N > 20 in both bands | 2018A&A...619A.161C |

Source selection by alpha significance (that paper's choice): |alpha| > 5 sigma(alpha) or sigma(alpha) < 0.1,
completeness not quantified (2018ApJ...853..171G).

Matched uv range (3): 20-1500 klambda, smoothed to 2" (2018ApJ...859...86T); 40-610 klambda (2017MNRAS.467L.120M);
50-1000 klambda with a taper so beam areas agree within a few percent (2025ApJ...985..148L).

Common beam (9 pack + 3 card): Band 6 convolved to the Band 3 beam (2024ApJ...961....4B); [0.13", 0.09"]
(2023MNRAS.518.6092L); single-spw images smoothed with `imsmooth` (2026A&A...712A.244H); 0.3" circular, which
super-resolves the 5 GHz map (2021ApJ...918...76C); 35 mas for profiles (2025MNRAS.538.2358S); Band 7 cleaned with a
uv-taper, then smoothed to Band 6 (2025A&A...699A.373F); 0.25" uniform restoring beam (2023MNRAS.524.3671Z);
2.7" x 2.6" on a regridded 0.3" pixel grid (2024MNRAS.527.1444A); 2" (2018ApJ...859...86T); 1.1 mm smoothed to the
2.1 mm resolution with CASA `imsmooth` (2020ApJ...891...48H, card); 94.5 GHz convolved to the 33 GHz beam and
regridded (2015ApJ...813..118M, card); 0.13-0.16" (2021A&A...652A..98G, card).

Briggs robust for imaging that fed an alpha map (3): 0 with nterms=2 (2018ApJ...852..122H); 0.0 for the combined
B6+B7 nterms=2 image (2015ApJ...808L...3A); 0.5, 0 and -0.5 tested (2025A&A...698A.165A).

MTMFS spectral-index imaging (4 used, 1 judged too noisy): within one band, 3 mm maps (2018ApJ...853..171G, nterms
not given); combined bands, B6+B7 (2015ApJ...808L...3A) and all 12 m data across bands as a cross-check
(2025A&A...702A.276P, alpha 0.57 ± 0.23 vs 0.56 ± 0.11 from per-band fits); band not stated, nterms=2, robust 0
(2018ApJ...852..122H). In-band tclean alpha maps too noisy to use (2024ApJ...961....4B).

| setting | value | bibcode |
|---|---|---|
| Dust T (10 papers, my count) | midplane 30 K and 18 K at two rings | 2020ApJ...891...48H |
| Dust T | about 15 K at 50 au | 2020ApJ...898...36L |
| Dust T | T(r) = 38 K (L/Lsun)^0.2 (r/100 au)^-0.4, 21 to 8 K over 600-4000 au | 2023A&A...676A...4C, 2024A&A...682A..61C |
| Dust T | T_d(r) = 360 (r/1 au)^-0.5 K | 2021ApJ...923..121Y |
| Dust T | 20 K with a 2.5 K Gaussian in a bootstrap | 2025NatAs...9.1176R |
| Dust T | 45 ± 5 K debris ring; 39 K; 35 and 100 K | 2017MNRAS.466.4201W; 2024A&A...683A.141R; 2019A&A...626A..36D |
| Dust T | 20, 14.7 and about 30 K tried for tau | 2021A&A...649A.122P |
| Radial bins | 1 au, i = 53.21 deg, PA = 57.17 deg | 2020ApJ...891...48H |
| Radial bins | 32 bins of 2.5 au | 2023MNRAS.518.6092L |
| Non-RJ correction | Delta alpha 0.06 (100 K), 0.20 (35 K) | 2019A&A...626A..36D |
| Debris planet-law index | alpha_pl = 1.84 ± 0.02 for 45 ± 5 K; beta_s = 1.8 ± 0.2 | 2017MNRAS.466.4201W, 2019AJ....158..162F |
| Grain size distribution | p = 3.5 (2.5, 1.5 tested), a_min 0.1 um; Td 30 K and 18 K at two rings | 2020ApJ...891...48H |
| Grain grid | a_max 10 um-1 cm, Sigma_d 0.001-10 g/cm2, 1000 log bins each | 2023ApJ...948..110Y |
| Visibility-fit prior on alpha | uniform 0-4 | 2018ApJ...859..103W |
| Free-free jet model | 175 uJy at 32.5 GHz, index about 0.7, size 22 mas | 2019ApJ...883...71C |
| Free-free index | -0.118 (3 mm extrapolated to 870 um; dust at 3 mm negligible for beta 1.7) | 2016ApJ...833L...6C |
| Thermal dust index | 3.8 fixed | 2017ApJ...849...90S |
| Thermal dust index | 3.75 (beta 1.75 on the RJ tail) | 2018ApJ...853..171G |

## 4. Per-band flux-calibration errors

How counted: my count of Key-parameters, Assumptions and excerpt lines giving a per-band calibration percentage, one
paper once, plus one (card) entry.

- 10% in every band (17): 2016A&A...588A.112G, 2018A&A...616A..88V, 2018ApJ...867...43T, 2018ApJ...869..158F,
  2020ApJ...891...48H, 2021AJ....162...99F, 2021ApJ...915...99I, 2023MNRAS.518.6092L, 2024A&A...682A..61C,
  2024A&A...689A.104D, 2025A&A...694L..15H, 2025A&A...695A..23S, 2025A&A...700A..22O, 2025ApJ...988..106H,
  2026A&A...706A.214V, 2026A&A...712A.244H, 2020ApJ...892...99C (card).
- 5% or 10% by band (5): 2023A&A...676A...4C and 2024MNRAS.527.9668H (10% B7, 5% B3-B6); 2024ApJ...974L..25D (5% B3,
  10% B7); 2025A&A...698L..16S (5% B3, 10% B6); 2019A&A...626A..81V (10%, 5% for one Band 4 set).
- 10% for ALMA, other values for other instruments (4): 2021ApJ...918...76C (VLA 5% / 15%), 2022MNRAS.509..748W
  (VLA 5%, SMA 15%), 2025A&A...693A..49S (NOEMA 20%), 2015A&A...584A..16P (20% and 10%).
- 5% (3): 2022MNRAS.511.1408G, 2025A&A...703A.110S, 2026MNRAS.550g1193B. 15% (1): 2020MNRAS.496..394R.
  5-20% by band, instruments not split in the pack (1): 2020ApJ...905...89Y.

## 5. Fixed non-dust indices

How counted: my count of Key-parameters and Assumptions lines that fix the index, one paper once.

- Free-free -0.1 (11): 2016ApJ...828...50K, 2017ApJ...849...90S, 2018MNRAS.479.1154B, 2019MNRAS.483.1624B,
  2020ApJ...895L...2N, 2024A&A...686A.122A, 2024A&A...692A.181Z (above about 22 GHz), 2024ApJ...963..103G,
  2024ApJS..274...15G, 2025A&A...702A..27P, 2026A&A...713A.167D (above 5 GHz).
- Ionised jets: 0.6 (2017ApJ...840...32T, 2023A&A...677A..97F, 2025A&A...702A..27P); 0.4 thick or -0.1 thin
  (2025A&A...702A..18D).
- Synchrotron or nonthermal, one fiducial value (20): -0.68 median for sources with few radio points
  (2021MNRAS.508.5259M); -0.7 (7: 2018ApJ...867...48I, 2020MNRAS.495.1760O with ± 0.3, 2021MNRAS.503.1174K,
  2022MNRAS.511.1408G, 2023PASJ...75..311K, 2025ApJ...990..166D, 2026A&A...706A.206H); -0.75 (2: 2024ApJ...967..133S,
  2025ApJ...991L..31B); -0.8 (6: 2017ApJ...850..178A, 2017MNRAS.468.4675D, 2020A&A...642A.155Z, 2024ApJ...961..120C,
  2024ApJ...974..243N, 2025A&A...701A.234Z); -0.83 (2020ApJ...905L..23M); -0.85 (2: 2015ApJ...813..118M,
  2025ApJ...979..217S); -0.9 (2017ApJ...849...90S).
- Explored or alternative values (not defaults): -0.6 tested against -0.85 (2015ApJ...813..118M, card); -0.6 to -0.8
  (2021A&A...654A..24B); -0.9 and -1.0 (2018ApJ...866L...3B); a jet index measured at -1.04 ± 0.03 with -0.7 to -1.5
  explored (2021MNRAS.503.1174K).
- Dust 3.5-4 for subtraction or classification: 3.8 (2017ApJ...849...90S), 3.75 (2018ApJ...853..171G), 4 with 3.8
  tested (2024ApJ...974..243N), 4 in a tested multi-component model (2024ApJ...963..103G).

## 6. Software census

Counts are the pack's software aggregate (mentions in matched steps, not unique papers). Merge map: CASA = `casa` 94
+ `tclean` 16 + `casa imfit` 5 + `imsmooth` 3 + `immoments` 2 = 120; SciPy = `scipy` 10 + `scipy curve_fit` 4 +
`scipy.optimize` 3 = 17; Frankenstein = `frankenstein` 6 + `frank` 3 = 9; MultiNest = `pymultinest` 3 +
`multinest` 2 = 5. Left out: `imfit` 4 (not clearly CASA), `astropy` 7, `python` 4, `python 3` 2, `matplotlib` 2
(generic), `madcuba` 2 and `ppmap` 2 (not tied to an alpha step). Bibcodes are only those the pack ties to the tool.

| Tool | Pack count | Used for |
|---|---|---|
| CASA (incl. tclean, imfit, imsmooth) | 120 | mtmfs alpha maps (2018ApJ...853..171G); per-spw `imsmooth` (2026A&A...712A.244H); `imfit` check of inner-disk flux (2025MNRAS.538.2358S); 3 mm / 1 mm indices (2024ApJ...961....4B) |
| emcee | 27 | two-greybody SED fits with free beta (2023MNRAS.523.4654T); radio-mm SED with AME (2020ApJ...905L..23M) |
| SciPy | 17 | power-law fits (2025A&A...702A.276P, 2019ApJ...875...55W); ring profile fits (2025MNRAS.538.2358S) |
| CIGALE, MAGPHYS, EAZY, BAGPIPES | 13, 6, 3, 3 | galaxy SED fits; see `sed-fitting` |
| RADMC-3D, mcfost, DustPy | 11, 5, 4 | a_max(R) fit to alpha_mm(R) (RADMC-3D, 2023MNRAS.518.6092L); dust evolution plus synthetic images (DustPy + RADMC-3D, 2025MNRAS.538.2358S) |
| Frankenstein (`frank`) | 9 | 1D visibility profiles (2025MNRAS.538.2358S, 2026A&A...705A.196H); its `alpha`/`w_smooth` are hyperparameters, not spectral indices |
| GILDAS, AIPS, MIRIAD | 7, 5, 4 | calibration and imaging outside CASA (not tied to an alpha step) |
| MultiNest | 5 | synchrotron + free-free + greybody fits (2018MNRAS.479.1154B) |
| astrodendro | 4 | core extraction before 3 mm / 1 mm indices (2024ApJ...961....4B) |
| uvmultifit, uvplot | 3, 3 | per-spw point-source fluxes (2026A&A...712A.244H); visibility plots (2025MNRAS.538.2358S) |
| galario, dynesty | 3, 3 | visibility forward modelling, nested sampling (2019A&A...628A.100D, an SZ model) |
| linmix, lmfit | 3, 3 | censored regression (2021MNRAS.507.2531Z); least squares |
| dsharp_opac | 3 | DSHARP opacities (not tied to a paper) |
| eht-imaging, NFFT | 2, 2 | RML multi-frequency alpha map from visibilities (2023ApJ...945...40C) |

## 7. Settings the cards flag as not stated

Pack aggregate, my sums over phrasings: line-free channels 66 (12 phrasings); CASA version 28, plus 33 in nine other
CASA-version phrasings (27 of those also ask for the pipeline version or pipeline/manual choice; the other 6 are
"casa version used for calibration and imaging" 3 and "casa version and calibration procedure" 3); flux calibrator
and flux-scale uncertainty 23 (4 phrasings); self-cal solution intervals 17, plus 20 with iterations or rounds; image
and cell size 13; primary-beam correction 12; CLEAN threshold/mask/niter 9; uvmodelfit starting parameters 3;
continuum bandwidth 3.
