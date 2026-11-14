# Imaging parameters seen in the pack (imaging-choices)

Every row is copied from a line of the current evidence pack (2488 papers): the key-parameter list (160 papers,
2012-2026, truncated after the listed lines) or the 40 detailed excerpts. Papers that appear in the pack only by
title are not used. These are example lists, not frequencies, except where a count is given. Check the card
before reusing a value. CASA `tclean` `scales` are in pixels: convert arcsec or beam multiples with
`scale_pixels = scale_arcsec / cell_arcsec`.

## Multiscale scales

| Scales | Units | Paper | Context |
|---|---|---|---|
| 0, 1, 3 | x CLEAN beam | 2024PASJ...76..437Y | disks with substructure; Cotton-Schwab otherwise |
| 0, 1, 3, 5 | x beam | 2021A&A...648A..33M | mtmfs; `scales=0` for self-cal of data poorer than ~1" |
| about 1 and 3 | x beam FWHM | 2015ApJ...813..118M | galaxy continuum, nterms=2 |
| 0, 1, 3, 5, 10 | x synthesized beam | 2020ApJ...904..131N | uv-stacks (Hogbom per source) |
| 1, 2, 5 | x beam | 2020MNRAS.493.5045M | GMC mosaic, robust 0.5 |
| 0, 5, 10 | x beam | 2018ApJ...869..158F | robust 0.5 |
| geometric series from 0, about x2 the beam-minor/cell ratio, up to ~5.5" | pixels | 2023A&A...678A.194C | survey line cubes, pbmask |
| 0, 5, 15, 25 (about 1, 3, 5 beams) | pixels | 2025A&A...703A..15M | debris disks, robust 0.5 |
| 0, 5, 15 (plus 45 for CO) | pixels | 2015ApJ...808L...3A | robust 0, long baselines |
| 0, 5, 15 (0, 5, 15, 45 in Band 4) | pixels | 2015ApJ...808L...4A | robust 1 |
| 0, 5, 15 | pixels | 2015ApJ...808L...2A | robust 0 |
| 0, 5, 15 | pixels (1" cell) | 2024RAA....24f5011X | line cubes, auto-multithresh |
| 0, 5, 15, 50, 150 / 0, 5, 15, 50 | pixels | 2026A&A...709A..93D | mtmfs continuum / line cubes |
| 0, 5, 15, 50, 150 | pixels (0.04") | 2020ApJ...894L..14L | robust 0.5 |
| 0, 7, 42, 126 | pixels | 2025ApJ...995L..51G | robust 0.5 |
| 0, 15, 38, 70 | pixels (1") | 2026A&A...707A.255C | mtmfs nterms=1, gain 0.05, tclean comparison |
| 0, 8, 23, 68, 203, 608 | pixels | 2019A&A...631A..64B | line emission |
| 0, 1, 5, 10, 15 | x pixel (0.2") | 2018MNRAS.475..448T | 12m+7m+TP, natural |
| 0, 3, 9, 27 | not stated | 2020ApJS..251...14H | CMZ continuum, robust 0.5 |
| 0, 3 | not stated | 2020ApJ...894...72S | robust 1 |
| 3 or 4 scales | not stated | 2026A&A...705A..96M | depends on source |
| 0, 0.06, 0.15, 0.3, 0.6 | arcsec | 2018ApJ...852..122H | Band 6 continuum, robust 0.5 |
| 0, 0.2, 0.4, 0.8, 1.6, 3.2 | arcsec | 2018ApJ...852..122H | 12CO cube, robust 1.0 |
| 0, 0.12, 0.36 | arcsec | 2019ApJ...871....5T | robust 0, 0.14" beam |
| 0, 0.5, 1.0, 2.5, 5.0 | arcsec | 2021ApJ...906..111T | disk lines |
| 0, 2, 6, 18 | arcsec | 2019ApJ...874...89C | ACA+12m, taper 1.5" |
| 0, 5, 8, 13, 20, 30, 45 | arcsec | 2016PASJ...68...88K | SZ, small-scale bias 0.4, gain 0.05 |
| 0, 4, 8, 16, 32, 64 | arcsec FWHM | 2020PASJ...72...33K, 2023PASJ...75..311K | SZ, natural, joint mosaic |

## Clean thresholds and stopping

22 papers give a clean threshold in rms units (my count over the key-parameter list and excerpts; absolute mJy
thresholds without an rms and detection thresholds are left out). 2026MNRAS.548ag546D appears in two rows.

| Threshold | Papers | Notes |
|---|---|---|
| 0.5 sigma | 2021A&A...654A..37D | lowered from 2 sigma for two faint targets |
| 1 sigma | 2021AJ....162...99F, 2024A&A...689A.145S, 2025A&A...699A..80H | 162F continuum; 699H `nsigma=1` with auto-multithresh |
| 1.5 sigma | 2025MNRAS.537..520Z, 2026ApJ..1005...94N, 2025A&A...701A.120P, 2026MNRAS.548ag546D | 701P in two 0.6" circular masks; 548D high-resolution cube |
| about 2x rms | 2014ApJ...792L...2C, 2015ApJ...800L..14C, 2017ApJ...838..147C, 2018Sci...362.1034D, 2020ApJ...904..131N, 2020ApJ...904L..12C, 2020NatAs...4..861C, 2021A&A...645A..97Q, 2021A&A...654A..37D, 2026ApJ...999L..32R | 10 papers; mostly Hogbom or Clark |
| 2.5 sigma | 2016PASJ...68...88K | multiscale, gain 0.05 |
| 3x rms | 2019A&A...630A..59B, 2019ApJ...876...72L, 2021ApJ...906..111T, 2026MNRAS.548ag546D | 630B no mask, niter 500-1000; 548D continuum |
| 5 sigma (10 sigma one field) | 2023A&A...678A.194C | chosen as most stable against divergence and stippling |
| model to 5 sigma during self-cal | 2021AJ....162...99F | self-calibration model only |
| divergent channels left uncleaned | 2023A&A...678A.194C | listed in the survey's imaging parameter file |
| 10 000 vs 100 000 iterations | 2021A&A...653A..53A | flux lost with too few iterations |

## Tapers and uv cuts

41 of the 160 listed papers mention a taper (my count, including tested-not-adopted and one uv-range cut filed as
a taper). Examples:

| Setting | Paper | Purpose |
|---|---|---|
| 0.02" | 2025ApJ...988..106H | residual-visibility continuum image |
| 0.3" with robust 0.5 | 2025ApJ...988..106H | fainter, larger-scale CO emission |
| 0.4" outertaper | 2018ApJ...866..117C | extended CO, 0.4" beam |
| `uvtaper=[0.5 arcsec]` (beam 0.65"x0.62") | 2022A&A...665A.107T | faint continuum emitter |
| 0.5" with robust 1.0 | 2021MNRAS.506.1978L | Band 7 analysis and residual maps |
| 0.7" on weak lines | 2021AJ....162...99F | raise detection significance |
| 0.8" outer taper | 2018MNRAS.479.5423M | Band 7 residual dirty maps |
| 0.9" (0.88 mm) and 0.4" (1.3 mm) | 2020MNRAS.498.1319M | main images, robust 2 |
| 0.2" to 2" in 0.2" steps | 2020MNRAS.499.5136C | ten cubes per undetected target |
| 1" with natural | 2025A&A...699A..80H | initial detection image |
| 1" or 2" tested | 2025A&A...703A..15M | non-detections |
| 1" | 2014A&A...569A..11S | weaker lines |
| 1.2" | 2019A&A...630A..59B | common-resolution stack test |
| 1.3" | 2014ApJ...797...27F | H2D+ cube |
| 1.5" with robust 0.5 | 2019ApJ...874...89C | ACA+12m core |
| about twice the robust-2 resolution; extra 0.5" | 2021A&A...654A..37D | extended emission; tentative-line checks |
| 2" Gaussian, robust 2 | 2015ApJ...798..124R | debris disk |
| 2" on natural continuum | 2026ApJ...999...32W | faint extended dust |
| 5" FWHM | 2021A&A...650A.117N | robust 0 to 2 |
| 10" | 2019MNRAS.490.5134B | tapered residual map |
| 50 klambda (CO 1-0), 100 klambda (CO 2-1) | 2013ApJ...777...92S | natural / Briggs |
| 100 klambda Gaussian radius | 2017ApJ...841..110S | 12m+ACA, natural |
| 200 and 1000 klambda | 2015ApJ...808L...4A | H2O and CO lines |
| 600 klambda, robust 2 | 2026MNRAS.548ag546D | low-resolution CO cube |
| beyond 900 klambda | 2021A&A...645A..33B | one high-resolution [C II] source |
| elliptical, per transition | 2021ApJ...906..111T | common-resolution radial profiles |
| Band 4 tapers to circularize the beam | 2021A&A...648A..33M | multi-band matching |
| robust and taper explored | 2026A&A...705A..96M | match two bands' beams |
| match isotopologue beams (flux about 25% lower) | 2019ApJ...876...72L | line ratios |
| SMA-like 5.9" x 3.0" | 2015ApJ...814..143A | facility comparison |
| beams of about 0.025, 0.083 and 0.15" | 2021A&A...651A..35O | Band 6 flux at several resolutions |
| tried, parameters not stated | 2017ApJ...846..108C | resolved-out flux test |
| `uvrange` > 138 klambda | 2023MNRAS.522...56V | compact sources |
| baselines < 60 m omitted | 2025A&A...703A..15M | some 12CO cubes |
| baselines > 25 m or > 50 m | 2022A&A...665A..82O | affected sources |
| spacings > 1 km, uniform | 2015ApJ...808L...1A | astrometry |
