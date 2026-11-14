---
name: alma-solar-observations
description: "Reduce, calibrate and analyse solar ALMA data: total-power (TP) full-disk maps and their absolute brightness-temperature scale, interferometric 1-20 s snapshot time series of the chromosphere, TP plus interferometer combination, Jy/beam to Tb, coalignment with SDO/IRIS, and the analyses solar papers run (center-to-limb curves, radius and limb brightening, oscillations, transient brightenings, flares and plasmoids, sunspots, plage, spicules, prominences, inversions). Use when working with solar-mode ALMA data or SV/archive solar products, checking a solar Tb value, or designing a chromospheric time-series analysis. Built from 35 ALMA papers (2015-2025)."
---

# Solar ALMA observations (chromospheric brightness temperature and time series)

ALMA sees the Sun in thermal free-free (plus H-minus) continuum from the chromosphere, read out as a
brightness temperature Tb that, being optically thick, tracks electron temperature near tau = 1
(2022A&A...661L...4A, 2020A&A...638A..62N, 2020ApJ...891L...8M). Two mistakes matter most: (1) treating the
interferometric image as absolute, when it carries no zero level until an offset or feather from the TP map is
added, and the TP scale itself is the least certain number in the chain (2020A&A...635A..71W,
2022A&A...661L...4A); (2) quoting amplitudes, sizes and event counts as intrinsic, when the beam, the
detrending and the sparse uv coverage bias them (2021A&A...656A..68E, 2020A&A...644A.152E, 2020A&A...634A..86P).

## Agent checklist

1. First establish what you have: TP full-disk maps (beam ~58-60 arcsec at 100 GHz, 25 arcsec at 230 GHz,
   21 arcsec in Band 7; 2022FrASS...9.1118D, 2017A&A...605A..78A, 2022A&A...661L...4A), interferometric
   visibilities, or delivered snapshot cubes (SoAP-processed or SV products). Fetch only the band, date and
   scans you need.
2. Decide the absolute scale before any science. If TP exists, feather or add the TP offset (6 excerpt papers
   feather, 3 add a constant; my count). If the paper is silent, normalise disk-centre quiet Sun to 7300 K at
   Band 3 (2020A&A...635A..71W, 2019ApJ...881...99M) and about 5900-6350 K at Band 6 (2020A&A...634A..56D,
   2020A&A...640A..57A); say you did.
3. Make snapshots at the cadence the science needs: 2 s is the norm (10 excerpt papers, my count, e.g.
   2017ApJ...841L...5S, 2020A&A...644A.152E), 1 s in 2021A&A...652A..92N, 20 s for faint limb work
   (2018ApJ...863...96Y). Use all four spectral windows per snapshot (2020A&A...635A..71W, 2019ApJ...877L..26L).
4. Self-calibrate the phases against a long time-averaged model and check that image jitter is gone in a
   movie (2017ApJ...841L...5S, 2018A&A...619L...6N). Record the solution interval; cards flag it as unstated
   (3 card entries, pack aggregates).
5. Coalign with SDO by cross-correlating time-averaged ALMA images with AIA 1600 A (2018A&A...619L...6N,
   2021A&A...652A..92N) after convolving AIA to the ALMA beam; target residuals below 1 arcsec
   (2019ApJ...877L..26L) or at least below the synthesized beam (2017SoPh..292...87S).
6. Measure noise from the XX minus YY image difference (2017SoPh..292...87S: 3.7 K Band 3, 9.8 K Band 6) or
   from the time series; expect 10-21 K per snapshot (2021A&A...652A..92N, 2017ApJ...841L...5S).
7. For oscillations: linear detrend, Tukey taper (0.1), Morlet wavelet, keep only power above 95% confidence
   and outside the cone of influence (2023A&A...671A..69G, 2025A&A...693A..19S). For events: at least 4
   consecutive points above 2.5 sigma over a beam-size patch (2020A&A...638A..62N, 2021A&A...652A..92N).
8. Before stating a result: rerun with a changed threshold, detrending or mask, and say whether amplitudes are
   lower or upper limits for resolution and detrending reasons (2020A&A...634A..86P, 2021A&A...652A..92N).
9. Write down: band and sub-bands, cadence, TP reference value and region, feather or offset, self-cal
   interval, coalignment method and residual, noise, and the flux-scale uncertainty used (5% at 3 sigma in
   2019ApJ...875..163R).

## When to use

- Full-disk TP maps: quiet-Sun Tb, center-to-limb variation (CLV), Te(tau) inversion, radius, limb or polar
  brightening, structure contrasts (2017A&A...605A..78A, 2022A&A...661L...4A, 2019ApJ...871...45S,
  2018A&A...613A..17B, 2021ApJ...910...77M).
- Interferometric time series of quiet Sun, plage, sunspots, the limb: oscillations, transients, waves,
  feature tracking (2020A&A...634A..86P, 2020A&A...644A.152E, 2023A&A...671A..69G, 2025A&A...693A..19S).
- Thermal diagnostics of events: plasmoids, bright points, EUV kernels, spicules (2017ApJ...841L...5S,
  2019ApJ...875..163R, 2020A&A...643A..41D, 2020ApJ...888L..28S).
- Joint ALMA plus IRIS, H-alpha or SDO correlation and inversions (2017ApJ...845L..19B, 2019ApJ...881...99M,
  2020A&A...634A..56D, 2021ApJ...906...83C).

## When not to use

| Situation | Use instead |
|---|---|
| Stars other than the Sun (Sun-as-a-star SEDs, alpha Cen) | Point-source flux fitting and Tb from Omega = pi R*^2/D^2 (2021A&A...655A.113M, 2015A&A...573L...4L); the `variability-time-domain` skill for stellar flares |
| Generic TP plus interferometer combination theory | The `array-combination` skill; this one covers solar specifics only |
| Forecasting a future single-dish instrument | Scan simulations with maria (2025OJAp....8E.129K) |
| Reading Tb as gas temperature in an optically thin feature (blob, plasmoid, off-limb) | Free-free optical-depth modelling with an assumed depth and filling factor (2017ApJ...841L...5S, 2018ApJ...863...96Y, 2020ApJ...888L..28S) |

## Steps

1. **Calibrate (solar mode).** On the Sun the antenna temperature exceeds Tsys, so both Tant and Tsys are
   measured (hot, cold, sky, off, sun and zero power readings) to scale the visibilities; attenuator changes
   were checked on 3C279 to move the phase by only 0.3 deg (IF Switch) and 0.6 deg (IF Processor)
   (2017SoPh..292...87S). Many papers start from the SV or JAO reference scripts (2019ApJ...875..163R,
   2022A&A...661L...4A). Calibration breaks of about 2 min recur every few minutes (four breaks of
   1.75-2.25 min in 2025A&A...693A..19S; about 7.5 min of data before a calibration pause in
   2020A&A...634A..56D).
2. **Make TP full-disk maps.** Double-circle scans, one full disk in 3 min in Band 7; use the antenna with the
   best Tsys and run CASA `sdgaincal` before mapping to suppress arc-like opacity modulations, using the
   repeated disk-centre position (2022A&A...661L...4A, following White et al. 2017). Band 6 two-load
   calibration used an efficiency factor C = 1.16 (2018A&A...613A..17B). Drop unstable maps: total flux was
   stable to 0.2% RMS across four 100 GHz maps and one 3.3% brighter map was discarded (2017A&A...605A..78A).
3. **Fix the absolute TP scale.** Measure quiet Sun at disk centre in a defined region (120 x 120 arcsec box,
   2019ApJ...871...45S; 240 arcsec radius, 2020A&A...635A..71W; 7.5 arcmin radius median, 2022MNRAS.511..877M)
   and compare with the values in the parameter table. Multi-day sets were cross-normalised to the December
   2015 Band 3 commissioning data with its factor fixed at 1 (2020A&A...640A..57A, 2022A&A...661L...4A);
   these authors state that cross-normalisation does not replace a true absolute calibration and that jumps
   exist between datasets (2022A&A...661L...4A).
4. **Handle the limb.** Correct diffuse light by fitting a Voigt to the CLV derivative, deconvolving with it
   and reconvolving with its Gaussian core (2017A&A...605A..78A). Stay inside the reliable range: r up to
   about 960 arcsec (2017A&A...605A..78A), limb exclusion 70, 35, 30 arcsec in Bands 3, 6, 7
   (2022A&A...661L...4A), plane-parallel inversion valid to mu ~ 0.15 (2020A&A...640A..57A). Mask bright and
   dark features before azimuthal CLV averaging (2017A&A...605A..78A).
5. **Image interferometric snapshots.** Multi-scale multi-frequency CLEAN of each 2 s snapshot with all four
   sub-bands (2020A&A...635A..71W, SoAP); mosaics used robust 1.0, which removed stripe artefacts
   (2017SoPh..292...87S). Cells 0.3 arcsec for beams of 1.2-1.6 arcsec in Band 3 (2020A&A...643A..41D,
   2019ApJ...877L..26L). Self-calibrate: against the whole-period image (2017ApJ...841L...5S), four phase
   rounds then amplitude (2018A&A...619L...6N, AIPS), or phase-only with residual jitter removed by
   autocorrelation shifts (2020ApJ...888L..28S). Correct for the primary beam (2020A&A...643A..41D,
   2020A&A...635A..71W).
6. **Combine with TP and convert to Tb.** Feather each snapshot with the simultaneous TP map
   (2017SoPh..292...87S, 2020A&A...644A.152E, 2019ApJ...881...99M) or add the TP-derived offset
   (+7700 K in 2020A&A...643A..41D; 7236 K in 2019ApJ...877L..26L). Rescale the TP map first if needed
   (7454 K to 7300 K in 2020A&A...635A..71W; full disk to 7250 K in 2018A&A...619L...6N). Without TP, work in
   relative Tb and say so (2020ApJ...888L..28S). Conversion is Rayleigh-Jeans (2020A&A...644A.152E,
   2021A&A...656A..68E). General practice: Tb [K] = 1.222e6 S [Jy/beam] / (nu[GHz]^2 bmaj bmin [arcsec^2]);
   use Planck intensity when fitting jointly with UV lines (2020A&A...634A..56D).
7. **Coalign and derotate.** Convert RA/Dec to heliocentric (2017ApJ...841L...5S: better than 2 arcsec vs
   AIA, up to 5 arcsec vs XRT), then refine by cross-correlation with AIA 1600 A (2018A&A...619L...6N), 304 A
   structures (2020A&A...643A..41D) or 45-min SDO averages (2019ApJ...877L..26L). 2021A&A...652A..92N checked
   that its pointing offset matched the general-relativistic radial offset. Derotate by cross-correlating
   with a reference frame (2020A&A...635A..71W); correct AIA for differential rotation and convolve it to the
   ALMA beam (2020A&A...638A..62N, 2020A&A...634A..86P). Rotate maps to solar north (2017ApJ...845L..19B,
   2021ApJ...910...77M).
8. **Analyse.** Pick the branch:
   - CLV and Te(tau): fit Tb against ln mu (linear, rms ~20 K, 2020A&A...640A..57A; cubic, rms 13 K,
     2022A&A...661L...4A), after reducing frequencies to 100 GHz with mu scaled by (f/f_ref)^2, which assumes
     f^-2 opacity (2020A&A...640A..57A); invert analytically (2017A&A...605A..78A).
   - Radius and limb brightening: inflection points of scan derivatives, 815-1100 arcsec filter, iterative
     circle fits rejecting points over 10 arcsec off (2021ApJ...910...77M, 2022MNRAS.511..877M), or a
     0.5 T_qS contour (2019ApJ...871...45S); forward-model beam convolution (2022MNRAS.511..877M).
   - Fourier oscillations: subtract a 3rd-degree polynomial per pixel, average PSDs, fit a linear background
     plus log-normal peak (2020A&A...634A..86P); with gaps, zero-fill and apply gap corrections of 0.6 (Band 6)
     and 0.7 (Band 3) (2021A&A...652A..92N).
   - Wavelets: see checklist line 7; remove periods over 1000 s and drop +/-180 deg phases from phase speeds
     (2025A&A...693A..19S). Torrence and Compo software at 99% against white noise (2020A&A...643A..41D).
   - Transients: remove p-modes by harmonic fitting (power down 12-17x), then apply the 2.5 sigma, 4-point,
     beam-patch, +/-2 min rule (2020A&A...638A..62N); or 14 s boxcar, amplitude >= 400 K, k-means within
     15 arcsec (2020A&A...644A.152E). Energy E = 3 N_e k V (Te,max - Te,0) with FAL C density
     (2020A&A...638A..62N).
   - Features: DoG filter, flood fill, overlap tracking and DBSCAN with scikit-image/scikit-learn
     (2023A&A...671A..69G).
   - Events and structures: background-subtracted enhancement plus free-free optical-depth modelling
     (2017ApJ...841L...5S, 2020ApJ...888L..28S); spectral slope across sub-bands with emcee
     (2019ApJ...875..163R); region masks from HMI (sunspot 0.65/0.90 of continuum, 2017ApJ...850...35L; plage
     Tb >= 6500 K, 2021ApJ...906...83C); cell/network by a 2nd-degree polynomial surface
     (2018A&A...619L...6N, 2020A&A...634A..86P).
9. **Compare with models.** Degrade synthetic Bifrost/ART maps with the actual clean beam
   (2020A&A...635A..71W, 2021A&A...656A..68E), or invert with STiC jointly with IRIS (2020A&A...634A..56D).

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Band 3 disk-centre QS Tb | 7300 K | 7114-7400 K | 9 (my count) | 7300 (2020A&A...635A..71W, 2019ApJ...875..163R), 7250 (2017A&A...605A..78A, 2018A&A...619L...6N), 7220 +/- 200 (2019ApJ...871...45S), 7347 (2022A&A...661L...4A), 7400 (2017ApJ...850...35L), 7114 (2024AN....34530149M) |
| Band 6 disk-centre QS Tb | ~6000-6350 K | 5900-6347 K | 7 (my count) | 5900 (2020A&A...634A..56D), 6000 (2017ApJ...850...35L), 6040 +/- 70 (2018A&A...613A..17B), 6180 (2017A&A...605A..78A), 6280 (2019ApJ...871...45S), 6343 (2020A&A...640A..57A), 6347 (2022A&A...661L...4A) |
| Band 5 / Band 7 disk-centre Tb | 6532 K / 6085 K | one paper | 1 | 2022A&A...661L...4A (Band 7 10.6% above the extrapolated recommended value) |
| TP beam FWHM | 58-60 / 25 / 21 arcsec | Bands 3 / 6 / 7 | 3 | 2022FrASS...9.1118D, 2017A&A...605A..78A, 2022A&A...661L...4A |
| Limb exclusion | > beam | 70 / 35 / 30 arcsec | 1 | 2022A&A...661L...4A |
| Snapshot cadence | 2 s | 1-20 s | 10 at 2 s (my count) | 2020A&A...644A.152E, 2021A&A...652A..92N (1 s), 2018ApJ...863...96Y (20 s) |
| Interferometric beam / cell (Band 3) | 1.2-1.6 / 0.3 arcsec | 4.9 x 2.2 arcsec early mosaic | 3 | 2020A&A...643A..41D, 2019ApJ...877L..26L, 2017SoPh..292...87S |
| Snapshot noise | ~10-11 K (Band 3) | 3.7-21.2 K | 3 | 2017SoPh..292...87S, 2021A&A...652A..92N, 2017ApJ...841L...5S |
| Flux-scale uncertainty | 5% (3 sigma) | 20% systematic for AIA DEM | 2 | 2019ApJ...875..163R, 2020A&A...643A..41D |
| Feather vs TP check | combined 5-10% above TP | factor 1.066 | 2 | 2017SoPh..292...87S, 2020A&A...640A..57A |
| Wavelet settings | linear detrend, Tukey 0.1, Morlet, 95%, outside COI | 99% vs white noise | 3 | 2023A&A...671A..69G, 2025A&A...693A..19S, 2020A&A...643A..41D |
| Event threshold | 2.5 sigma, >= 4 points, beam patch 12-19 px | 2.1-2.3 sigma tests; 400 K amplitude | 3 | 2020A&A...638A..62N, 2021A&A...652A..92N, 2020A&A...644A.152E |
| Coalignment residual | < 1-2 arcsec vs AIA | ~5 arcsec for full-disk overlays or XRT | 3 | 2019ApJ...877L..26L, 2017ApJ...841L...5S, 2018A&A...613A..17B |
| Limb brightening | ~10% | 5-19% (100 GHz), 6-18% (230 GHz) | 3 | 2018A&A...613A..17B, 2019ApJ...871...45S, 2022MNRAS.511..877M |

Reference results for sanity checks: p-mode peak 4.2 +/- 1.7 mHz with 55-75 K rms at 3 mm
(2020A&A...634A..86P); p-mode rms 152 K (Band 3) and 175 K (Band 6) (2021A&A...652A..92N); network
+305 K and intranetwork -285 K about the mean (2018A&A...619L...6N); quiet-Sun radius 968 arcsec at
100 GHz and 963.7 arcsec at 230 GHz (2021ApJ...910...77M).

## Software

| Job | Package (pack count) | Note |
|---|---|---|
| Calibration, imaging, feather, TP mapping | CASA (16) with `sdgaincal` (1) | robust 1.0 mosaics (2017SoPh..292...87S); `simobserve` beams (2021A&A...656A..68E) |
| Solar snapshot pipeline | SoAP (3, plus SoAP2 1) | 2020A&A...635A..71W, 2020A&A...644A.152E, 2020A&A...634A..56D |
| Solar analysis helpers | SALAT (1) | 2023A&A...671A..69G |
| Alternative imaging | AIPS (1), CLEAN (1) | 2018A&A...619L...6N, 2021A&A...652A..92N |
| Coalignment, SDO prep | SunPy (1), SolarSoftWare (1), Enhance (1), IDL (4) | 2020A&A...643A..41D, 2019ApJ...871...45S |
| Inversions and forward models | STiC (5), RH / RH 1.5D (2), RADYN (1) | 2020A&A...634A..56D, 2020ApJ...891L...8M, 2020A&A...644A.152E |
| Simulations and synthesis | Bifrost (4), ART (4) | 2021A&A...656A..68E, 2023A&A...671A..69G |
| Timing, events, fits | Torrence and Compo wavelets (1), scikit-image / scikit-learn (1 each), emcee (1), EBDETECT, DEMREG, CHIANTI v9 (1 each), MPFIT (1), Pikaia (1) | 2020A&A...643A..41D, 2019ApJ...875..163R, 2017ApJ...845L..19B, 2022FrASS...9.1118D |

Use these instead of writing new wavelet, inversion or radiative-transfer code. Check installation details
before use; the pack gives no install commands.

## Pitfalls

- **Absolute scale.** The TP scale "remains less certain" (2020A&A...635A..71W); Band 6 and 7 jump against
  commissioning data (2022A&A...661L...4A). State the reference value and treat it as the leading systematic;
  2019ApJ...875..163R names flux-scale accuracy its largest uncertainty.
- **No TP, no absolute Tb.** Without the single-dish map only relative Tb is valid (2020ApJ...888L..28S,
  2018ApJ...863...96Y).
- **Sidelobes and beam smoothing.** Polar brightening is a lower limit (2019ApJ...871...45S); single-dish
  umbral depression at 1.3 mm an upper limit (2017ApJ...850...35L); a 25 arcsec umbra is washed out at
  100 GHz (2022FrASS...9.1118D); 100 GHz CLV points 30-55 arcsec from the limb are suspect
  (2017A&A...605A..78A).
- **Resolution bias on amplitudes.** A shock signature can shrink to ~0.18 of its true excess at Band 3
  (2020A&A...644A.152E); event counts are lower limits (2020A&A...644A.152E); event energies are upper
  limits (2020A&A...638A..62N). The degraded-to-original correction of 2021A&A...656A..68E is statistical,
  not for single events.
- **Detrending and series length.** 10-min series give 1.7 mHz resolution and rms values that are upper
  limits after polynomial detrending (2020A&A...634A..86P); coarse correlated pixels make p-mode rms a lower
  limit (2021A&A...652A..92N).
- **Limb and uv artefacts.** Stripes beyond the limb from incomplete uv sampling with ~30 antennas
  (2017SoPh..292...87S); unexplained off-limb emission up to 1000 K (2018A&A...619L...6N); poor S/N beyond
  10 arcsec off the limb (2018ApJ...863...96Y).
- **Beam-sized features.** Widths at the beam scale are upper limits and need a filling-factor correction
  (0.25 in 2020ApJ...888L..28S); tracking underestimates sizes by ~20% (2023A&A...671A..69G).
- **Statistics.** Pixels are correlated on the beam scale (2017ApJ...845L..19B); bands observed on
  different days cannot measure propagation (2023A&A...671A..69G).
- **Simulation degradation.** Gaussian-beam convolution assumes perfect uv sampling (2023A&A...671A..69G).
- **Unstated settings** (pack aggregates): CASA version (4 cards), self-cal intervals (2 + 1), feathering
  parameters (2), imaging weighting and deconvolver, image registration. Record all of them.

## Verification checks

- TP: total-flux stability between maps (0.2% RMS, 2017A&A...605A..78A); disk-centre QS against the table;
  CLV fit residuals of tens of K (2020A&A...640A..57A, 2022A&A...661L...4A); radius near 963-968 arcsec
  (2021ApJ...910...77M).
- Combined maps: feathered Tb a few percent above TP at the same place (2017SoPh..292...87S,
  2020A&A...640A..57A); check the assumed background against the TP image (2019ApJ...875..163R).
- Snapshots: jitter gone in the movie after self-cal (2017ApJ...841L...5S, 2018A&A...619L...6N); noise
  replicated independently (2019ApJ...875..163R reproduced 11 K).
- Coalignment: residual quoted in arcsec and below the beam (2017SoPh..292...87S, 2019ApJ...877L..26L).
- Time series: wavelet power only above 95% and outside COI; PSD fit residuals within ~15-20%
  (2020A&A...634A..86P, 2021A&A...652A..92N); p-mode suppression factor reported before event detection
  (2020A&A...638A..62N); results stable under spatial averaging (5 x 5 px, 2020A&A...643A..41D) and a changed
  start frame (2023A&A...671A..69G).
- Events: threshold and patch-size sensitivity (2020A&A...638A..62N); chance coincidence with AIA pairing
  within 15 s; a toy-model injection test of the detector (2023A&A...671A..69G).
- Features must be larger than the beam axes (2023A&A...671A..69G).
- A referee also asks: which TP value set the zero level, whether bands were simultaneous, and whether the
  quoted amplitude is beam-diluted. Report each result as value, uncertainty (noise plus flux scale) and the
  check behind it.

## Source cards

Full list: `references/sources.md`. Most informative here: 2017SoPh..292...87S (calibration, imaging, noise),
2022A&A...661L...4A (TP Band 7, CLV, normalisation), 2017A&A...605A..78A (CLV, diffuse light),
2020A&A...640A..57A (cross-normalisation, cell/network), 2020A&A...635A..71W (SoAP snapshots, feathering,
TP scale), 2020A&A...644A.152E (events, resolution factor), 2021A&A...656A..68E (resolution effects),
2020A&A...638A..62N and 2021A&A...652A..92N (transients, p-modes), 2020A&A...634A..86P (PSDs, time lags),
2023A&A...671A..69G and 2025A&A...693A..19S (wavelets, waves), 2017ApJ...841L...5S and 2019ApJ...875..163R
(plasmoid, spectral slope), 2020A&A...643A..41D (active-region heating), 2019ApJ...877L..26L (coalignment),
2019ApJ...871...45S and 2022MNRAS.511..877M and 2021ApJ...910...77M (radius, limb brightening),
2018A&A...613A..17B (full-disc structures), 2017ApJ...850...35L (sunspots), 2020ApJ...888L..28S (spicule),
2020A&A...634A..56D (STiC inversions).
