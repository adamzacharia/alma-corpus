# Imaging parameters seen in the pack (imaging-choices)

Every row is copied from a line of the current evidence pack: the key-parameter list (290 of the 1121 papers,
2012-2026, truncated after the listed lines) or the 40 detailed excerpts. Papers that appear in the pack only by
title are not used. These are example lists, not frequencies, except where a count is given. Check the card
before reusing a value. CASA `tclean` `scales` are in pixels: convert arcsec or beam multiples with
`scale_pixels = scale_arcsec / cell_arcsec`.

## Multiscale scales

| Scales | Units | Paper | Context |
|---|---|---|---|
| 0, 1, 3 | x synthesized beam | 2017A&A...602L..10O | nterms=2, robust 0 |
| 0, 1, 3 | x CLEAN beam | 2025ApJ...993...85Y | disk continuum, robust 0.5 |
| about 1 and 3 | x beam FWHM | 2015ApJ...813..118M | galaxy continuum, nterms=2 |
| 0, 1, 3, 9 | x expected beam | 2020ApJ...898..146M | debris belt, 12m+ACA, natural |
| point, 3, 6, 9 | x beam | 2020MNRAS.496.4061D | CO(2-1) cube, threshold 2x rms |
| point, 0.5, 1, 2, 3 | x beam FWHM | 2024ApJ...974..102S | disk lines |
| 0, 1, 2, 3, 4, 5 | x beam | 2023PASJ...75..424O | disk lines |
| 0, 5, 10 | x beam | 2018ApJ...869..158F | robust 0.5 |
| 1, 2, 5, 10, 15 | x beam | 2018ApJ...857...19F | GMC cube, gain 0.1, 100 iterations per cycle |
| 0, 5, 10 | pixels (pixel = beam/5) | 2026A&A...705A.198M | debris CO, third tclean pass |
| 0, 6, 18 | pixels (1") | 2020ApJ...899...10T | prestellar cores, natural |
| 0, 5, 20 | pixels (4 mas) | 2024ApJ...963..164R | mtmfs, robust 1 |
| 0, 10, 25 | pixels (0.25") | 2017PASJ...69...18T | line cubes, robust 0.1-0.4 |
| 0, 7, 21 / 0, 5, 15 | pixels (6 mas) | 2017ApJ...842L..24A | CO and SiO lines |
| 0, 4, 20 / 0, 5, 25 | pixels | 2020ApJ...898...10T | continuum / lines |
| 0, 5, 15, 25 | pixels | 2025SciA...11.4512O | line cubes, robust 2 |
| 0, 5, 15, 50, 150 | pixels (0.04") | 2020ApJ...894L..14L | robust 0.5 |
| 0, 3, 9, 27 | pixels | 2020ApJS..251...14H | CMZ continuum, simulated observations |
| 0, 4, 12, 24, 48 / 0, 4 | pixels | 2025ApJ...989....1Z | Band 6 / Band 7 |
| 0, 5, 11, 21 | pixels (0.5") | 2024ApJ...969..143I | continuum |
| 0, 8, 23, 68, 203, 608 | pixels | 2019A&A...631A..64B | line emission |
| [0,30,60]; [0,6,18,30]; [0,6,18,30,60] | pixels | 2025A&A...696A.150S | 7m; 12m; combined |
| 0, 1, 5, 10, 15 | x pixel (0.2") | 2018MNRAS.475..448T | 12m+7m+TP, natural |
| 0, 0.06, 0.15, 0.3, 0.6 | arcsec | 2018ApJ...852..122H | Band 6 continuum, robust 0.5 |
| 0, 0.2, 0.4, 0.8, 1.6, 3.2 | arcsec | 2018ApJ...852..122H | 12CO cube, robust 1.0 |
| 0, 0.3, 0.9 | arcsec | 2020ApJ...895...84Y | MS-CLEAN reference for sparse modeling |
| 0, 0.12, 0.36 | arcsec | 2019ApJ...871....5T | robust 0, 0.14" beam |
| 0, 0.1, 0.3 | arcsec | 2018ApJ...860...77E | adopted over Hogbom |
| 0, 0.048, 0.08, 0.24 | arcsec | 2018ApJ...866L...6C | |
| 0, 0.5, 1.25 | arcsec | 2020ApJ...905..152D | clean to 3 sigma |
| 0, 100, 300 / 0, 50, 150 | mas | 2016ApJ...829L..35T | Band 4 / Band 6 |
| 0, 2, 6, 18 | arcsec | 2019ApJ...874...89C | ACA+12m, taper 1.5" |
| 0, 5, 8, 13, 20, 30, 45 | arcsec | 2016PASJ...68...88K | SZ, small-scale bias 0.4, gain 0.05 |

## Clean thresholds and stopping

29 papers give a threshold in rms units (my count over the key-parameter list and excerpts; absolute mJy
thresholds without an rms are left out).

| Threshold | Papers | Notes |
|---|---|---|
| 0.5 sigma or residual max sigma/2 | 2016ApJ...829....6W, 2020ApJ...890...29F, 2024A&A...689A.317G | deep clean; 689G GILDAS Hogbom, about 4000-5000 components |
| 1 sigma | 2024ApJ...971..129C | robust 0.8 |
| 1.25 sigma | 2025SciA...11.4512O | continuum |
| 1.5 sigma | 2025MNRAS.541.2540Z; 2015ApJ...807..128S in boxes around >5 sigma sources | |
| 2x rms | 2014ApJ...792L...2C, 2014ApJ...795L..30C, 2016ApJ...821L...8S, 2017ApJ...846..108C, 2018Sci...362.1034D, 2018Icar..307..380T, 2020MNRAS.496.4061D, 2024ApJ...962....1S, 2024A&A...682A.166F, 2025ApJ...986L..22R, 2025ApJ...990L..31B | 11 papers; mostly Hogbom |
| 2.5 sigma | 2016PASJ...68...88K, 2025A&A...696A.150S | multiscale; 150S also stops when model flux grows <1% |
| 3x rms | 2015ApJ...807..128S, 2017ApJ...839...43O, 2019A&A...630A..59B, 2019ApJ...876...72L, 2020ApJ...905..152D, 2021A&A...655A..25Z | 839O Hogbom with Briggs 0.5; 630B no mask, niter 500-1000 |
| 4x rms | 2017A&A...597A..41G, 2020ApJ...893..101L, 2026A&A...705A.198M | 597G niter 1000; 198M Keplerian mask |
| about 5 sigma | 2025A&A...697A..64V | multiscale |
| not reached in some channels | 2019A&A...631A..64B | combined 12CO image |

## Tapers and uv cuts

65 of the 290 listed papers mention a taper (my count). Examples:

| Setting | Paper | Purpose |
|---|---|---|
| `['0.010arcsec','0.010arcsec','10deg']` | 2021A&A...654A..35B | high-resolution taper, robust -1 and 1 |
| 0.04" FWHM | 2024A&A...691A..57M | combining three configurations |
| 0.27" Gaussian image-plane convolution of natural maps (scanned 0.01-0.50") | 2020MNRAS.493.4294B | maximize [C II] S/N; not a uvtaper |
| 0.3" | 2019ApJ...876..130H | flux recovery test |
| 0.4" outertaper | 2018ApJ...866..117C | extended CO flux |
| 0.45" with natural | 2020A&A...636A..37D | non-detections |
| 0.6" with natural | 2015ApJ...807..128S | detection maps |
| 0.7" (tested 0.4-0.8") | 2017ApJ...851..145M | detection |
| 150 klambda (100-200 tested) | 2021ApJ...907L..15S | about 0.8" |
| 1.2" | 2019A&A...630A..59B | common-resolution stack test |
| 1.5" with robust 0.5 | 2019ApJ...874...89C | ACA+12m core |
| 1.5" outertaper | 2017A&A...597A..41G | check images |
| 2" Gaussian, robust 2 | 2015ApJ...798..124R | debris disk flux |
| 10" | 2020ApJ...898..146M | large-scale belt image |
| 18.75 klambda (Gaussian FWHM 4.8") | 2024ApJ...977..198L | natural, large scales |
| 1.5 Mlambda (12CO), 0.3 Mlambda (13CO, C18O) | 2023PASJ...75..424O | disk lines |
| 0.3" tested, not adopted | 2024A&A...682A.166F | no extra emission recovered |
| match isotopologue beams (flux about 25% lower) | 2019ApJ...876...72L | line ratios |
| Band 3 to Band 7 resolution | 2024A&A...684A..56K | multi-band matching |
| second epoch to first beam | 2020PASJ...72L...9F | epoch comparison |
| SMA-like 5.9" x 3.0" | 2015ApJ...814..143A | facility comparison |
| uv > 100 klambda | 2015ApJ...801...82H, 2020ApJ...891...80M | compact sources |
| uv > 80 klambda, uniform | 2014ApJ...796....1T | highest-resolution continuum |
| uv cut 100 klambda (best rms over 0-300) | 2018ApJ...860...77E | continuum |
| baselines > 2.5 km only | 2018A&A...616L...3B | long-baseline map |
