# Spectral index: longer parameter tables

All entries come from the `spectral-index` evidence pack (aggregate lines "Key parameters", "Assumptions" and the
paper excerpts). Counts are my own count of those pack lines, one paper counted once per value. Papers whose "beta"
is a disk flaring index (2019A&A...622A..75L, 2019A&A...624A...7V, 2024ApJ...966...59S, 2021AJ....161..238W), a
Nuker shape parameter, or a Fermi photon index are excluded. A paper that appears only in the pack's paper list
(title only) is not used.

## 1. Adopted (fixed) dust beta when it is not measured

82 papers state a single fixed beta (my count; each bibcode below was checked against a pack line giving that
value). These are adopted assumptions, not measurements. The split follows the science field more than any
measurement.

| beta | papers | typical context | bibcodes |
|---|---|---|---|
| 0.4-0.5 | 5 | disks, with kappa about 2.3 cm2/g at 230 GHz | 2014ApJ...787...42C, 2015ApJ...798..124R, 2014ApJ...796....1T, 2019ApJ...878L...8T, 2019ApJ...878...16P |
| 1.0 | 22 | protoplanetary disks and protostars; kappa = 10 cm2/g at 1000 GHz type laws | 2014Sci...345.1584B, 2016ApJ...826...16E, 2016ApJ...828...46A, 2017ApJ...850L...2A, 2018A&A...619A.161C, 2018ApJ...861...91H, 2018ApJ...863...19A, 2018MNRAS.473..879P, 2018MNRAS.475.5322S, 2019A&A...623A.150V, 2019A&A...623L...8B, 2019A&A...628A..85V, 2019ApJ...872..112V, 2019ApJ...877L..25M, 2019ApJ...886....6T, 2019MNRAS.482..698C, 2019MNRAS.486.4114R, 2019NatAs...3..314L, 2020ApJ...898...10T, 2020MNRAS.496..394R, 2024ApJ...973...42B, 2025ApJ...993..120H |
| 1.2 | 2 | scaled single-dish data; pillars | 2014ApJ...795L..25R (chosen after scanning 1.0-2.0), 2020AJ....159...62C |
| 1.46-1.5 | 15 | high-z and nearby galaxies, some cores and disks | 2015ApJ...812...27A, 2019MNRAS.483.1624B, 2012ApJ...752L..30W, 2014ApJ...792...34O, 2015ApJ...810...91H, 2016ApJ...819...82S, 2016PASJ...68...43K, 2017ApJ...835...98U, 2017ApJ...836L...2B, 2018AJ....156..239Z, 2018ApJ...856L..12N, 2018PASJ...70...65U, 2019ApJ...871..170M, 2020ApJ...896..110L, 2025ApJ...992..103Z |
| 1.6 | 6 | z > 6 quasar hosts, always with T_dust = 47 K | 2013ApJ...770...13W, 2016ApJ...816...37V, 2017Natur.545..457D, 2018ApJ...854...97D, 2019ApJ...876...99S, 2024ApJ...968....9W |
| 1.7-1.75 | 5 | dense cores, low-metallicity galaxies | 2016ApJ...833L...6C, 2017MNRAS.468L..87C, 2019ApJ...881L..39B, 2024A&A...691A.180F, 2018ApJ...853..171G |
| 1.8-1.85 | 12 | galaxies (SMGs, z~1-3, clusters), some cores | 2014ApJ...785..111W, 2015ApJ...811L...3T, 2017ApJ...837..174O, 2017ApJ...840..101C, 2018Sci...362.1034D, 2019ApJ...880...15K, 2019MNRAS.482.3135B, 2020ApJ...892...66M, 2024ApJ...963....1O, 2024ApJ...966...51G, 2025A&A...698A.204H, 2020ApJ...896..127K |
| 1.9 | 2 | dense core, starburst nucleus | 2016ApJ...826...26T, 2021A&A...656A..46M |
| 2.0 | 13 | lensed high-z DSFGs; massive star-forming clumps and hot cores | 2013ApJ...767...88W, 2014ApJ...787..112C, 2015A&A...577A..30A, 2016ApJ...822...80S, 2016ApJ...826..112S, 2017ApJ...844..123F, 2018A&A...616L..10F, 2020A&A...635A...2S, 2020A&A...644A..84M, 2020ApJ...902...78R, 2025A&A...699A.369V, 2025ApJ...994..225N, 2026A&A...705A.100E |

Two or more values or a range instead of a single value: 1.5 and 2.0 both used (2024BSRSL..93..601H); 1.0-2.0
tested when scaling Herschel to 3 mm (2014ApJ...795L..25R, also counted above for its final 1.2); 1.2-2.0
(2017Sci...355.1285N); 1-1.8 (2020ApJ...890..129K); bounded 0-2 to constrain T_SED (2021A&A...653A.117B); MCMC over
1.3-2.5 (2024A&A...684A..56K); 1.5-2.0 varied for dust-mass systematics (2020ApJ...892...66M, also counted above for
its fiducial 1.8); beta = 2 alternative tested (pack validation aggregate, no bibcode attached).

Author guidance (my recommendation, not a pack result): if beta is not measured, adopt the value used by the
closest physical analogue above and say so. The counts above show what papers assumed, not how uncertain beta is
for your source. Choose physically justified alternative opacity laws and temperatures for that source, and
propagate their effects together (beta and T move a mass or tau estimate jointly), as 2020ApJ...892...66M did by
varying T and beta at once.

## 2. Measured alpha and beta values reported in the pack

Values copied from pack lines; sign convention as reported by each paper.

| object type | value | bands | bibcode |
|---|---|---|---|
| T Tauri disk (GM Aur), disk-averaged | alpha 2.7 ± 0.2 | 1.1 / 2.1 mm | 2020ApJ...891...48H |
| Inner vs outer disk (HD 141569) | alpha 1.81 ± 0.15 vs 2.28 (+0.43/-0.29) | three data sets, joint MCMC | 2018ApJ...859..103W |
| Debris disk HD 107146 | alpha 2.42 ± 0.16, q 3.25 ± 0.09 | mm SED | 2015ApJ...798..124R |
| Debris ring Fomalhaut | alpha_mm -2.73 ± 0.13 as printed, q 3.50 ± 0.14 | 350-6600 um | 2017MNRAS.466.4201W |
| Debris disk HD 32297 | alpha 2.4 | sub-mm | 2020ApJ...892...99C |
| Protostar in a globule (HH 900) | alpha 2.2 ± 0.5 | four bands, adjacent B6/B7 | 2020MNRAS.496..394R |
| Massive protostellar outburst (NGC6334I) | mean alpha MM1 2.9, MM2 3.2, MM4 2.4 | ALMA bands | 2017ApJ...837L..29H |
| Sgr B2 compact sources | 62 with significant alpha, 33 with alpha > 2 | 3 mm in-band | 2018ApJ...853..171G |
| Seyfert starburst ring | alpha ≥ 2-3, read as dust | 230 / 351 GHz | 2021A&A...652A..98G |
| Background galaxy | alpha about 2.5, beta about 0.5 | B6 / B7 | 2020ApJ...894...76W |
| IMBH candidate | alpha 1.18 ± 0.65 | 231 / 266 GHz | 2017NatAs...1..709O |
| Symbiotic star R Aqr centre | alpha 1.88 | 1.3 / 0.45 mm | 2024A&A...689A.317G |
| Mira A | 1.71 ± 0.05 in Band 3, 1.54 ± 0.04 B3-B6 | B3, B6 | 2015A&A...577L...4V |
| alpha Cen A / B | alpha(7,3) 1.62 / 1.61 | B3 / B7 | 2015A&A...573L...4L |
| LBV central object (ionized wind) | alpha 0.78 ± 0.05 | 9-349.5 GHz | 2017ApJ...841..130A |
| HL Tau free-free jet model | index 0.7 (175 uJy at 32.5 GHz) | VLA | 2019ApJ...883...71C |
| Radio source near HR 8799 | alpha 0.69 ± 0.03 | 3 / 340 GHz | 2024RMxAA..60..355R |
| Black hole X-ray binary | alpha 0.28 ± 0.02 | ALMA bands | 2024Ap&SS.369...18M |
| Galaxy nuclear regions | alpha -0.10 to -0.27 | 33 / 94.5 GHz | 2015ApJ...813..118M |
| Phoenix cluster radio source C1 | alpha -0.37 (ATCA+ALMA), -0.50 in-band | 18 / 92 GHz | 2020PASJ...72...62A |

Fomalhaut sign note: the 2017MNRAS.466.4201W excerpt says it fits F_nu ∝ nu^alpha yet prints alpha_mm = -2.73,
with alpha_pl = 1.84 and q = 3.50. My check: q = (alpha_mm - alpha_pl)/beta_s + 3 gives (2.73 - 1.84)/1.8 + 3 = 3.49
with +2.73, and 0.46 with -2.73. So the printed q only follows from the magnitude in the frequency convention. The
pack does not resolve the sign; normalise to S_nu ∝ nu^alpha before applying the q relation.

Reading guide (general practice, applied as a diagnostic, not a classifier): in this pack's examples, dust-dominated
sources show alpha of roughly 2-4 and ionized winds, jets and synchrotron sources show alpha below about 1. The
ranges overlap: optically thick or scattering dust, cold dust outside RJ, and mixed components can all give alpha
near or below 2. Before naming a mechanism, check temperature (non-RJ correction), optical depth, morphology, and cm
data. Sign convention matters: check whether a paper uses S ∝ nu^alpha, S ∝ nu^-alpha (2017MNRAS.469L.123O) or a
wavelength index (2019ApJ...875...55W fits brightness temperature against wavelength).

## 3. Thresholds and settings

| setting | value | bibcode |
|---|---|---|
| Pixel mask | S/N < 2.5 in either band masked | 2018A&A...616A..88V |
| Pixel mask | > 3 sigma in both maps | 2017ApJ...841..130A, 2015ApJ...813..118M |
| Pixel mask | S/N > 20 in both bands | 2018A&A...619A.161C |
| Source selection (that paper's choice) | abs(alpha) > 5 sigma(alpha) or sigma(alpha) < 0.1; completeness not quantified | 2018ApJ...853..171G |
| uv range | 40-610 klambda | 2017MNRAS.467L.120M |
| Common beam | 0.13-0.16" | 2021A&A...652A..98G |
| Common beam | 1.1 mm smoothed to the 2.1 mm resolution with `imsmooth` | 2020ApJ...891...48H |
| In-band imaging | nterms=2, robust=0 | 2018ApJ...852..122H |
| Radial bins | 1 au annuli, i = 53.21 deg, PA = 57.17 deg | 2020ApJ...891...48H |
| Flux-cal error | 10% per band | 2020ApJ...891...48H, 2018ApJ...869..158F, 2018A&A...616A..88V, 2024A&A...689A.104D, 2020ApJ...892...99C |
| Flux-cal error | 0.1 on alpha from flux calibration, 95 / 233 GHz | 2025A&A...700A.188C |
| Flux-cal error | 15% | 2020MNRAS.496..394R |
| Non-RJ correction | Delta alpha 0.06 (100 K), 0.20 (35 K) | 2019A&A...626A..36D |
| Debris planet-law index | alpha_pl = 1.84 ± 0.02 for 45 ± 5 K; beta_s = 1.8 ± 0.2 | 2017MNRAS.466.4201W, 2019AJ....158..162F |
| Grain size distribution | p = 3.5 (also 2.5, 1.5 tested), a_min 0.1 um; Td 30 K and 18 K at two rings | 2020ApJ...891...48H |
| Visibility fit prior on alpha | uniform 0-4 | 2018ApJ...859..103W |
| Free-free jet model | 175 uJy at 32.5 GHz, index about 0.7, size 22 mas | 2019ApJ...883...71C |
| Free-free index | -0.1 | 2019MNRAS.483.1624B, 2017ApJ...849...90S, 2020ApJ...895L...2N |
| Free-free index | -0.118 (3 mm extrapolated to 870 um; dust at 3 mm negligible for beta 1.7) | 2016ApJ...833L...6C |
| Non-thermal index | -0.85, tested -0.6 | 2015ApJ...813..118M |
| Thermal dust index | 3.8 fixed | 2017ApJ...849...90S |
| Thermal dust index | 3.75 (beta 1.75 on the RJ tail) | 2018ApJ...853..171G |
