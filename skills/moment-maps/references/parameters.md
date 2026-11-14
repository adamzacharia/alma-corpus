# Moment maps: per-paper parameter lists

Longer lists behind the counts in `SKILL.md`. Values come from the rebuilt evidence pack (1087 papers): its
key-parameter lines (360 papers listed, 369 truncated, so counts are lower bounds) and its excerpts. Papers the
rebuilt pack lists only bibliographically were checked against their own card and are marked "(card)". A
threshold given without its meaning is marked "unstated".

## Velocity-map (moment 1 / 2) thresholds, 35 papers

How counted: unique bibcodes whose key-parameter line (or excerpt, for 2021ApJ...914...36I) gives a clip or
S/N cut for moments 1 and 2, or for "moment maps" in general, plus five card-checked papers. Each paper is
counted once, in the row of its threshold.

| Threshold | Applied to | Papers (n) |
|---|---|---|
| 5 sigma | clip in immoments / S/N >= 5 | 2018A&A...615A.155H, 2021ApJ...914...36I, 2020ApJ...894...72S (3) |
| 4.5 sigma | emission above threshold, chosen to suppress SO2 absorption | 2020ApJ...904...77G (1) |
| 4 sigma | per-pixel clip or unstated | 2016A&A...590A..73A (card), 2020A&A...640A.104A (card), 2020ApJ...903..145L (card), 2022A&A...662A.121R (quadratic maps), 2023MNRAS.519.2030H, 2015MNRAS.452...88K (pixel S/N >= 4), 2025ApJ...988..106H, 2024MNRAS.533..771R, 2020MNRAS.496..138B ("SNR > 4 pixel cut for moment maps"), 2024ApJ...977...37N (4 sigma pixel cut plus 5 sigma on moment 0) (10) |
| 3-5 sigma | by galaxy morphology; pixels below set to null | 2024A&A...686A.156D (1) |
| 3-4 sigma | by line or band | 2024NatAs...8..587F (4 at 183 GHz, 3 at 325 GHz, per channel, card), 2025A&A...696A..18C (3 for CH3OH, 4 for smaller molecules), 2020ApJ...905...25G (7 mJy, ~3-4 sigma) (3) |
| 3.5 sigma | spectral peak (2026A&A...705A.198M); "clip S/N < 3.5 sigma" (2024ApJ...963....1O) | 2026A&A...705A.198M, 2024ApJ...963....1O (2) |
| 3 sigma | moment-0 rms (2021A&A...653A.111R); moment-0 mask (2023MNRAS.518.3183L); voxels > 3 rms plus moment 0 > 0.4 Jy/beam km/s (2014ApJ...788L..34P); peak velocity (2026MNRAS.552g1700S); emission above 3 sigma (2025ApJ...985..166K); integrated-intensity S/N > 3 and dispersion S/N > 2 (2023ApJ...945...42B); unstated (2026A&A...707A.252K, 2020MNRAS.493.5290S, 2024A&A...687A.311A) | as listed (9) |
| 2.5 sigma | unstated | 2020MNRAS.493L.108B (card) (1) |
| 2 sigma | unstated (2018Natur.560..613T); all moment maps (2024A&A...688L..22P); per channel (2024PASJ...76..960S) | as listed (3) |
| 1.5x local rms | pixel threshold | 2025Natur.641.1137B (1) |
| integrated S/N > 10 | integrated flux | 2021ApJ...917...99Y (1) |

Related but not counted: 2026A&A...705A.201B integrates only pixels whose peak emission exceeds 4 sigma (a
peak-based pixel selection for integration, not a velocity-map clip).

## Moment 0 clipping, 16 papers

| Clip | Papers |
|---|---|
| none / no sigma clip | 2020ApJ...903..145L (card), 2023A&A...677A..76P; masked without a flux threshold: 2024ApJ...964..190L |
| negatives only | 2024A&A...692A.155K ("clipped at 0 sigma with no mask"), 2025ApJ...988..106H, 2024MNRAS.533..771R (`includepix` [0,100] where absorption overlaps) |
| 1 sigma | 2021A&A...646A..59R, 2026MNRAS.552g1700S |
| 2 sigma | 2024A&A...688L..22P, 2024PASJ...76..960S (per channel), 2025ApJ...985..226W (mask smoothed over one beam) |
| 3 sigma | 2016A&A...590A..73A (card), 2025A&A...699A..83A (all moments), 2020MNRAS.496.2362P, 2022MNRAS.511.3618L |
| 5 sigma | 2026MNRAS.551g1645K |

## Smoothed-cube masks, 11 papers

| Smoothing | Threshold | Paper |
|---|---|---|
| beam FWHM spatial, spectral width unstated | 1.5 sigma | 2018ApJ...865...13T |
| beam FWHM spatial, then Hanning in velocity | not given here | 2019MNRAS.484.4239R (card) |
| spatial 1.5, spectral factor 4 | 3 sigma | 2021MNRAS.500.3802H |
| 1.5x beam Gaussian, 4-channel boxcar | > 3x rms | 2022MNRAS.512.1522D |
| 1.5x beam, Hanning | 0.9 sigma | 2026MNRAS.546f2269R |
| smoothing factor alpha = 3 | beta = 0.5 sigma | 2021MNRAS.504.4123N |
| alpha = 3, varied to check signal coherence | beta = 0.75 sigma | 2022MNRAS.509.2920N |
| spectral sigma 100 km/s, spatial sigma 10 px | 2x rms in signal-free regions | 2025A&A...699A..80H |
| smoothed cube | 1.5x rms of the smoothed cube | 2023MNRAS.522.4078C |
| smoothed cube | 0.5 sigma of the unsmoothed cube = 8 sigma of the smoothed cube | 2026ApJ..1005...94N |
| smoothed cube, channels by visual inspection | 3 sigma | 2017ApJ...848L...7C |
| 3x beam, Hanning over 5 channels | 1 sigma | 2025MNRAS.541.2540Z (card) |

(The 2019MNRAS.484.4239R row is kept for its kernel only and not counted in the 11.)

## Weighting examples

How counted: key-parameter lines matching robust 0.5 (14 papers) and robust 2 / natural (18 papers). The
corpus-wide median robust is 0.5 in nearly every field (`skills/stats/README.md`, 3498 cards).

- robust 0.5: 2014ApJ...783L..13P, 2024ApJ...975...72B, 2021ApJ...921...97J, 2024PASJ...76..960S, among others.
- robust 2 or natural: 2018A&A...617A..23B, 2025ApJ...988...72S, 2018Sci...362.1034D, 2022ApJ...929..100K,
  2021A&A...654A..37D, 2022PASJ...74.1429T, 2026A&A...706A.236M, among others.
- Per line: robust 1.0 for 12CO and 2.0 for 13CO and C18O (2020ApJ...889L..24P, card).
- Per product: moment 0 at robust 0.0 and moments 1-2 at robust +2.0 (2018A&A...615A.155H).
- Both ends: robust -2 and 2 (2019A&A...621A..83S, card).

## Velocity windows tied to a line fit

| Window | Paper |
|---|---|
| +/-2 sigma_V around V_sys | 2023MNRAS.519.2030H |
| -0.85 to +0.85 FWHM | 2021A&A...655A..42S |
| peak +/-1.4 sigma (~83% of the flux), flux corrected by ~1.20 | 2025A&A...694A.171M |
| 2x FWHM | 2025ApJ...985..259J |
| 3x [CII] FWHM (700 km/s) | 2020ApJ...903...34A |
| 2-sigma line width from 1D Gaussian fits | 2026ApJ..1004..194F |
| CO(2-1) width equal to [CII] FWHM, range holding 84% of the emission | 2024A&A...684A..33K |
| consecutive channels above 1 sigma of the spectrum | 2020MNRAS.496..875R |
| default +/-10 km/s for faint or non-detected sources | 2024ApJS..274...15G |

Other windows: +/-12 km/s around systemic (2014ApJ...791L...6W); 300 km/s per lens component
(2018ApJ...867..140L); blends from -5 km/s of the lowest to +5 km/s of the highest line (2018ApJ...857...35S);
-140 to +140 km/s picked for highest S/N and checked by eye (2020MNRAS.493.4294B); >3 sigma channels summed
(2019MNRAS.485..739M, card); about 35 km/s for complex-molecule maps with a narrower check
(2024A&A...687A.163B, card); outflow lobes blue -400 to -120 and red +120 to 300 km/s (2019A&A...632A..33A).

## Channel width examples

Protoplanetary disks 0.114-0.163 km/s (2024ApJ...972...88L), 0.20-0.43 km/s (2024ApJ...964..190L); debris
disk 0.4 km/s for 12CO and 1.6 km/s for 13CO and C18O (2025A&A...703A..15M); nearby galaxies 3.8 km/s
(2025ApJ...988...72S) and ~10.2 km/s (2019ApJ...881...10B, card); Galactic Center CND 5 km/s
(2018PASJ...70...85T); high-z 35 km/s at z = 8.31 (2020MNRAS.493.4294B, card), 50 km/s at z = 7.5
(2019ApJ...881...63N), 100 km/s (2021ApJ...921...97J, 2022PASJ...74.1429T).

## Keplerian mask line-width laws

- 2020ApJ...890..142P: r0 = 100 AU, q = -0.3, v0 = 0.3 km/s (0.6 or 0.15 for some lines and disks) (card).
- 2021ApJ...911..150P: V0 = 0.22-0.25 km/s, R0 = 100 AU, q = 0.3.
Check how each paper writes the law and the sign of q before reusing either.

## Sampler settings and ring widths

| Paper | Settings |
|---|---|
| 2020ApJ...891...48H | eddy + emcee: 48 walkers, 3500 steps total, first 500 discarded |
| 2024ApJ...974..102S | 64 walkers, 3000 burn-in steps then another 3000 kept |
| 2022A&A...662A.121R | about 200 walkers, 1000-2000 steps, last 800-1000 sampled |
| 2026A&A...705A.201B | 32 walkers, 1500 steps, 500 burn-in |

3DBarolo ring widths: beam minor-axis FWHM (2022NatCo..13.4574G), minor-axis FWHM / 2.5
(2021A&A...654A..37D), major-axis FWHM / 2.5 (2026A&A...707A.252K).

## Software (pack aggregates, mentions in matched steps)

| Tool | Count | Used for |
|---|---|---|
| CASA (tclean, immoments, imfit, uvcontsub) | 467 (immoments 37 + 27 = 64, imfit 27 + 24 = 51, tclean 40 + 6 = 46, uvcontsub 15) | imaging, moments, Gaussian fits |
| bettermoments | 65 | quadratic peak velocity, clipped moments, peak intensity (2026A&A...705A.198M) |
| GILDAS / MIRIAD / AIPS | 27 / 17 / 9 | imaging and spectra, SMA moments (2018ApJ...853..147M) |
| astropy / spectral-cube | 23 / 17 | Python cube handling |
| GoFish | 20 | azimuthally averaged spectra and profiles |
| 3DBarolo / kinemetry | 19 (14 + 5) / 5 | tilted-ring fits and SEARCH masks (2025A&A...693A..91L) |
| emcee / eddy | 17 / 12 | disk rotation fits (2020ApJ...891...48H, 2018ApJ...868..113T) |
| CARTA | 14 | viewing, 2D Gaussian fits in a mask (2023A&A...674A.125B) |
| PHANGS-ALMA pipeline / SoFiA | 6 / 6 | masks and moment products (2024ApJ...971..176H), source finding (2019PASJ...71...85M) |
| keplerian_mask, pvextractor, astrodendro | 5 / 5 / 9 | disk masks, PV cuts, dendrograms |

## Paper-specific upper-limit recipes (not portable defaults)

- 2017AJ....153..240A: 3x image rms, integrated over +/-1 km/s of the known stellar velocity (card).
- 2018ApJ...853..147M: spectra shifted by the CO moment-1 velocity and summed over the CO spatial mask; the
  3 sigma limit is the filtered spectrum's rms times the number of independent channels across the CO line
  width. This assumes every molecule shares CO's spectro-spatial distribution. They checked the filter on the
  detected CO and also gave unfiltered limits within +/-5 km/s.
- 2024A&A...682A.166F: integrated luminosity of a Gaussian with assumed FWHM 600 km/s and a peak equal to
  1 sigma. The 1 sigma is the assumed peak amplitude, not the confidence level of the integrated limit.
  Non-detections were rechecked with other apertures and channel binning.
- 2024A&A...691A.178B: a detection threshold only (non-detection if S/N < 3).

## Integrated upper limits at 3 sigma, 9 papers

| Recipe | Paper |
|---|---|
| 3x image rms over +/-1 km/s of the stellar velocity | 2017AJ....153..240A (card) |
| CO-shifted, CO-masked spectrum; rms x independent channels (assumes CO-like distribution) | 2018ApJ...853..147M |
| 3 sigma flux limit 90.84 mJy km/s for 13CO and C18O | 2026MNRAS.545f2150S |
| 16 random background apertures for the noise | 2022MNRAS.510.1148S |
| over 320 km/s | 2017MNRAS.468.4205K |
| 3 sigma limits; weak lines smoothed to 6 or 8 km/s | 2022MNRAS.515..543C |
| point source, fixed 200 km/s range at best redshift | 2021A&A...655A..42S |
| assumed FWHM 100 km/s | 2025Natur.641.1137B |
| assumed 300 km/s line width | 2024ApJ...964...95S |
