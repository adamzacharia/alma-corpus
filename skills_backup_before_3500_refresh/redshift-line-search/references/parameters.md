# Per-paper settings for redshift and line searches (from the evidence pack)

Every entry is taken from `packs/redshift-line-search.md` (key parameters, assumptions, excerpts). "Not stated"
means the card flags it as missing. A blank cell means the pack does not give that setting for that paper; do
not fill it from another row.

## Blind and serendipitous searches

| Paper | Search method | Seed / cut | Fidelity / reliability | Completeness | Region |
|---|---|---|---|---|---|
| 2016ApJ...833...67W | findclumps, 3/5/7/9-channel averages on 7.8 MHz (3 mm) and 31.2 MHz (1 mm) cubes, daofind | seed not stated; >2 sigma in consecutive channels | 1 - N_neg/N_pos, error-function fit (C_3mm 5.1, sigma 0.4; C_1mm 5.0, sigma 0.8); keep >= 60%; 60/80/95% at S/N 5.17/5.34/5.57 (3 mm) and 5.15/5.50/5.97 (1 mm) | 2500 injected lines, 50-500 km/s, peaks 0.22-1.00 mJy (3 mm) and 0.5-2.0 mJy (1 mm) | radius: sqrt(2) x PB radius at 3 mm (53" at 84 GHz, 39" at 115 GHz), 30.9" at 1 mm |
| 2016ApJ...833...69D | not given in the pack (same ASPECS field as 2016ApJ...833...67W by title; its search settings are not transferred here) | S/N > 5; 21 candidates (10 at 3 mm, 11 at 1 mm) | | | |
| 2019ApJ...882..136A | not given in the pack (ASPECS by title) | | fidelity > 0.9 gives 16 candidates | | |
| 2021A&A...646A..76L | findclumps on 118 cubes, kernels ~90-550 km/s | S/N 3 seed | > 85% (S/N >= 6.30), plus two ~50% lines with counterparts; 14 lines final | ~50000 injected lines, four PB rings | |
| 2020ApJ...904..130V | per-channel S/N > 3, Gaussian smoothing in frequency up to 400 MHz, 56 cubes | S/N 3 | >= 0.8 from inverted cubes; visual vetting | not stated | |
| 2020ApJ...889...98M | > 3 sigma in one 15 MHz channel, four neighbours > 2 sigma (~50 km/s), moment 0 over FWHM | S/N > 5 | visual inspection; negative-voxel excess noted | recovers known emitters | within the PB FWHM (half-power contour); target masked |
| 2015MNRAS.451.1141M | blind [CII] search at z ~ 4.5 | 6 sigma | | | |
| 2018Natur.556..469M | 100 km/s channels | SNR > 4 peaks; 14 candidates all SNR > 6.3 | | | |
| 2025ApJ...995..219F | per-channel | S/N > 2.5 across >= 3 contiguous channels | | | |
| 2024A&A...690A..55S | | robust lines sigma > 7, p_chance < 0.001; P_chance < 5% for masking lines | | | |
| 2017A&A...605A..42C | targeted window | abs(v) < 500 km/s of Lya | reliability may be ~50% at S/N = 5 | | PB FWHM 16" (diameter); 2" excluded around a serendipitous source |
| 2025ApJS..278...45F | survey LF | 5 sigma and FWHM = 200 km/s assumed for LF | 1-2 sources may be spurious | no completeness correction for IR LF | |

## Targeted detection thresholds and widths

| Paper | Setting |
|---|---|
| 2020ApJ...905..147Y | detection SNR_peak >= 3.5 (75 detections, 43 non-detections) |
| 2020A&A...643A...1L | detection S/N > 3.5 |
| 2014ApJ...792...34O | 3 sigma limit, assumed width 40 km/s, 40 km/s channels |
| 2015MNRAS.452...54M | 3 sigma limits in 100 km/s bins; 7 sigma offset clump |
| 2019ApJ...881..124M | conservative limit assumes 200 km/s width and ~0.7" beam |
| 2020A&A...641A.155V | 3 sigma, Delta v = 400 km/s when only optical z available |
| 2019ApJ...887..107F | single Gaussian FWHM 270 km/s used to correct a 100 km/s window |
| 2019ApJ...887..144J | acceptable line widths 100 to 1000 km/s |

## Line fitting and redshift

| Paper | Setting |
|---|---|
| 2020ApJ...904..130V | single Gaussian + constant; aperture radii 0.4-1.5" with residual scaling |
| 2026ApJ..1002L..28Y | Gaussian + constant by MCMC; 0.8" diameter apertures |
| 2017ApJ...849...91M | flat continuum + Gaussian, GILDAS |
| 2018PASJ...70...36I | single Gaussian, 1.5" diameter; double Gaussian tested by reduced chi2 (1.05 vs 1.24) |
| 2025A&A...695A...6P | two components only if DeltaBIC > 5 and both S/N > 3 |
| 2020ApJ...900..131L | center fixed to [CII] redshift; 0.8" radius aperture |
| 2019ApJ...881...63N | same FWHM as [CII] for all lines |
| 2020MNRAS.492.1778M | Gaussian prior on z_sys (6.5285, 0.001) from [CII] |
| 2020ApJ...905...85S | systemic z from [CII] or S/N-weighted stacked CO lines |
| 2017ApJ...851..145M | L/Lsun = 1.04e-3 x S dv x nu_obs x D_L^2 |

## Assumptions that travel with [CII] redshift papers

Dust for L_FIR when the continuum is also measured: T_dust = 47 K, beta = 1.6 in many quasar papers
(2020ApJ...904..130V, 2026ApJ..1002L..28Y, 2019ApJ...887...40W, 2018ApJ...854...97D, 2020ApJ...897L..14Y);
alternatives 30 K (2015ApJ...807..180W), 35 K (2017ApJ...851..145M), 45 K (2025ApJS..278...45F). These belong
to the `dust-continuum-mass` and `sed-fitting` skills; state them, do not tune them here.
