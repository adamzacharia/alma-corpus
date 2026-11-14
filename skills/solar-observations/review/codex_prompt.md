# Review task: an ALMA agent skill against its evidence pack

You are reviewing a skill file (SKILL.md, plus an optional parameters table) that another model wrote from the
EVIDENCE PACK below. The pack is built from methods cards of published ALMA papers; every quote in it was
mechanically verified against the paper text. The skill will be given to research agents that analyse ALMA data,
so wrong defaults or misattributed practice cause real errors. You have no file access: everything you need is in
this message.

Check, in this order:

1. **Attribution.** Every number, range, default, software attribution and "papers do X" claim that cites
   bibcodes: does the pack support it for those bibcodes? Flag claims the pack contradicts, claims cited to a paper
   whose pack entry says something else, and counts that do not match the pack aggregates.
2. **Unsupported practice.** Statements presented as literature practice with no support in the pack. (General
   background marked as general practice is fine if it is correct.)
3. **Scientific correctness.** Wrong formulas, wrong units, wrong CASA task/parameter names or semantics, unsafe
   advice, or a recommendation that contradicts the evidence.
4. **Omissions.** Important pitfalls, assumptions or validation checks that are clearly present in the pack (for
   example in "Limitations the authors admit" or "Settings cards flag as needed but not stated") but missing from
   the skill.
5. **Usability.** Anything an agent would misread or could not act on.
6. **Contamination and team lessons.** If a WRITER CONTEXT section is present: flag any mention of, or hint at,
   the held-out evaluation targets it names (objects, papers, or their numbers). Team lessons may appear only as
   labelled team experience in general form; flag any that is presented as literature practice or carries
   numbers not in the context.

Some skills are *workflow* skills (paper reproduction, claim verification, archival reuse, software map). Their
packs aggregate card fields such as inherited conventions, missing-for-reproduction items, validation checks and
software used. Lines marked "(card)" in the pack are the card author's inference; the skill should say so when it
leans on one. Review them with the same rules.

Output format (Markdown, nothing else):

```
# Codex review: <slug>
VERDICT: CLEAN | FIX
## Findings
- SR-01 | high|medium|low | <attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- SR-02 | ...
## Notes
<at most 5 lines: overall quality, anything the writer should know>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (solar-observations) ===
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

=== WRITER CONTEXT (readers, team lessons, contamination rule; not a literature source) ===
# Who reads these skills, and what went wrong in their runs (CosmicCoder meeting notes, Oct-Nov 2026)

Distilled from the CosmicCoder agent meeting notes (all pages) for skill writers. This file is for YOU, the writer.
Do not quote it as a literature source. Lessons below may appear in a skill only as clearly labelled team experience
("in CosmicCoder agent runs ...") and only in general form.

## The readers

The skills are read by research agents working on ALMA data: single Claude Code agents, research frameworks
(Denario, AutoResearch) and teams of agents (questioner, worker, reviewer/validator, editor) that post findings to a
shared forum and are graded against published papers or by astronomers. Tasks come in two shapes:

- **Bottom-up / reproduction**: given an ALMA dataset (and maybe a literature summary), find what the paper found.
- **Top-down / novel**: given a research question, pick the method and the data, then answer it.

Evaluation decomposes a paper into (hypothesis, experiment, result, finding) tuples and asks: are the individual
experiments correct, are the final conclusions correct, are the findings significant, are they novel. Experts want
each experiment traceable to code.

## Lessons from the runs (write skills that prevent these)

1. **Agents reimplemented a naive version of a standard package** (a cube kinematics fitter) and got a worse
   measurement than the paper. Agents need to know which established tool does the job and reach for it.
2. **One dataset is rarely enough.** Good projects needed several datasets to clear up inconsistencies and to check
   earlier literature claims, plus tables and numbers from other papers. One framework gave up when a table from
   another paper was needed.
3. **Downloading whole projects is a trap.** An agent tried to fetch about 4 TB of raw data by project code; the
   analysis needed only specific products, which astroquery could fetch. Older-cycle data that needed
   reprocessing could not be processed in that environment (CASA/tclean was not installable on one HPC system).
   Archive image products were often usable as delivered.
4. **Unstated and inherited conventions break reproductions.** A paper in a series reused corrections (for
   example flux and number recovery from artificial source insertion) and design choices from its earlier
   papers without restating them. Reproduced images were noisier than the paper's and nobody could tell what
   extra preprocessing the authors had done.
5. **"Done" must mean executed and checked.** A framework's judge approved tasks when code had been written but
   not run. Stricter gates (the file ran, outputs exist and look sane) fixed it.
6. **Context flooding.** Agents printed huge raw tables into their context, costing millions of input tokens.
   Summarise; write tables to files.
7. **Overconfident conclusions.** One system's conclusions were "more confident than its evidence supports".
   Single agents stopped after minutes having characterised the obvious bright component and missed the faint
   compact signal that was the real finding.
8. **No stopping criterion.** Open-ended runs became a money pit, agents going back and forth verifying claims
   they could only speculate about given the data. Agents need a rule for when the evidence is enough and when a
   question cannot be settled with the data in hand (and should be written down as open).
9. **Verifiers and editors help.** Adding a verifier/editor that asked "what is the most important question?"
   raised scores; teams with worker and validate roles beat strict pipelines; adaptive iterative loops beat
   heavy fixed pipelines. Staged work (each stage with tests and an answer key, stop or retry by stage) worked for
   model reproductions; open items needing expert confirmation were recorded rather than forced.
10. **Novelty is easy to fake.** Ideation agents treated unpublished data as proof of a novel question without
    checking whether the same question had been answered with other datasets, and repackaged an observing
    proposal into analysis tasks instead of distinct hypotheses.
11. **Results need tolerances.** Reproductions reported agreement to stated precision (for example within 0.3% or
    "within reading precision" of a figure) and explained each remaining mismatch (smoothing of a published
    figure, a possible table typo) instead of declaring success or failure overall.

## Contamination rule (critical)

The team's evaluation tasks are held out of the corpus. Never name, describe or hint at their targets or results
in a skill: no L1521F / L1521F-IRS, no "CMF across Galactic environments" protocluster series, no z~6 quasar-host
[CII] kinematics sample results, no SZ quasar-feedback detection in HE 0515-4414, no specific numbers from those
papers. Write general practice from the pack. If a lesson above came from one of those tasks, state it only in
general form (as it is phrased above).

=== EVIDENCE PACK (solar-observations) ===
# Evidence pack: Solar ALMA observations (chromosphere brightness temperature, time series) (`solar-observations`)

Scope: solar-mode ALMA: total-power full-disk maps, interferometric time series, brightness-temperature calibration, feathering, oscillations and flares in the chromosphere

Built from 35 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2015-2025.
Matcher (regex over analysis steps): `.`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- sun: 35
- stellar_physics: 3
- instrumentation: 2
- solar_system: 1

### Software named in the matched steps
- casa: 16
- stic: 5
- bifrost: 4
- art: 4
- idl: 4
- maria: 3
- soap: 3
- jvo: 1
- simbad: 1
- alma science archive: 1
- vizier: 1
- python: 1
- cds sed service (vizier): 1
- phoenix: 1
- scikit-image: 1
- scikit-learn: 1
- salat: 1
- pikaia: 1
- sdgaincal: 1
- emcee: 1
- solarsoftware: 1
- enhance: 1
- sunpy: 1
- ebdetect: 1
- demreg: 1
- chianti v9: 1
- python wavelet software (torrence & compo): 1
- rh: 1
- aips: 1
- clean: 1
- soap2: 1
- rh 1.5d: 1
- radyn: 1
- mpfit: 1

### Fitting methods (most common phrasings)
- Successive circle fits, discarding points outside R̄ ±10 arcsec after each fit: 1
- Least-square exponential fit; not a physical model: 1
- Gaussian fitting of slit brightness-temperature profiles: 1
- Linear fit for detrending: 1
- two-dimensional Gaussian function fit to each image: 1
- DBSCAN clustering on feature light curves: 1
- Log-normal fits to size and horizontal velocity distributions: 1
- Linear fit for detrending time series prior to CWT: 1
- Gaussian fit to difference distribution: 1
- Standard chi2 minimisation over (f_n, f_T); 1 sigma uncertainties from Delta chi2 = 1 above the minimum; sampler and pr…: 1
- Pikaia genetic algorithm with chi-squared minimization; full-generation replacement over 10 generations with 100 childr…: 1
- Voigt function fit to derivative of CLV: 1
- Least squares on logarithmic form; residual RMS ~60 K: 1
- Power-law (log-log) fits: 1
- Least-squares fit to third-degree polynomial in ln(mu): 1
- Analytical algebraic inversion from fitted polynomial coefficients A_i to a_i: 1
- Normal likelihood in log space; uniform non-informative priors on gradient and intercept; 90% percentile intervals: 1
- 2D Gaussian FWHM for kernel sizes: 1
- Qualitative comparison, no formal fit: 1
- Gaussian function fit to 1-D beam profiles: 1
- Iterative least-squares circle fit to extracted limb coordinates: 1
- Two linear fits to the lowest and highest valid LB values as a function of R_synth: 1
- second-order polynomial to line core for minimum: 1
- Least-squares harmonic fit (Roerink et al. 2000) with iterative outlier removal: 1
- Linear fit in log axes with Poisson-weighted bins: 1
- Power-law fit to energy distribution above 2.4e24 erg: 1
- second-degree polynomial: 1
- chi^2 minimization of PSD model a0+a1 ln nu+a2 exp(...): 1
- Power-law fit with Poisson bin errors: 1
- Linear fit to binned medians and ±1σ: 1
- chi2 minimization with regularization penalties and ad hoc ALMA weighting: 1
- linear fit: 1
- Linear fit (quadratic made no difference): 1
- Linear regression of Tb vs log mu100, inverted to Te(tau100): 1
- Double Gaussian for Mg II features: 1

### Validation checks used
- Limb-point filtering intended to reject active-region, instrumental-error, and high-opacity contamination: 1
- Compare SST 212-GHz and ALMA 230-GHz radius determinations: 1
- Simulations show increased radius uncertainty perpendicular to azimuth-elevation scans: 1
- SST and ALMA radii appear consistent within uncertainties with the radius-frequency trend: 1
- 212-, 230-, and 405-GHz radii are close to model radii; 100-GHz radii are about 4 arcsec larger: 1
- Compare six-month SST 212-GHz and ALMA 230-GHz equatorial and polar radius series: 1
- Compare behavior across frequencies, latitude regions, and both solar proxies: 1
- jitter removal checked in 2-s movie: 1
- precision better than 2" ALMA vs AIA; up to 5" vs XRT: 1
- 304 Å excluded due to resonance scattering: 1
- XRT non-detection constrains T<1 MK: 1
- compared with polar jets (Sako13) and active-region jets (Liu16): 1
- Selected fibril persists throughout the observed period.: 1
- Contaminated sources identified by beam shape differing from the synthesised beam: 1
- Published VLA stellar fluxes compared with the pipeline values: 1
- Model compared with observed SEDs at IR-UV frequencies, e.g. Delta S/S_mod near 0 at high frequencies for the Sun: 1
- Results compared with earlier T_B analyses of alpha Cen A/B and Sirius: 1
- Tested a different starting snapshot for time series matching and confirmed it did not change final results: 1
- Toy model control experiment with synthetic 2D Gaussian features placed via Poisson Disk Sampling with 5% noise and con…: 1
- Verified that feature sizes exceed the median minor and major axes of the ALMA beam: 1
- Restricted dominant period and phase extraction to wavelet regions with >= 95% confidence level and outside the cone of…: 1
- Uncertainties derived from error propagation analysis; compared observational energy fluxes against both original and d…: 1
- Phase variation from attenuator changes checked with 3C279; std 0.3 deg (IF Switch), 0.6 deg (IF Proc): 1
- Stripe artifacts disappear with robust 1.0: 1
- Combined Tb 5-10% above single-dish map at same position: 1
- Co-alignment better than synthesized beam by comparing umbra edge: 1
- Procedures a and b used to test whether small changes in the measurements change the output profile: 1
- Checked that |B|_min = 200 G avoided simulated ARs appearing much larger than observed ARs, and compared extrapolated f…: 1
- Monitored stabilization of chi-squared across generations and evaluated optical depth and contribution functions across…: 1
- Compared synthetic vs. observed average T_b values (normalized to T_qS) within uncertainties across AR regions in Table…: 1
- Total flux RMS of 0.2% across four 100 GHz images: 1
- Compared with high-resolution images near east limb (100 GHz) and south pole (239 GHz); reliable up to r~960'': 1
- Adding a quadratic term did not change results; power series unstable; compared with Eddington-Barbier and models: 1
- Visual comparison with ALMA TP maps convolved to TP beam: 1
- Suppression of large-scale arc-like brightness modulations in Band 7 images: 1
- Comparison with December 2015 commissioning observations: 1
- Comparison of rms deviation of third-degree fit (~13 K) against linear (26.6 K) and quadratic (16.0 K) fits, and compar…: 1
- Comparison with Paper II curve and FAL93 models A, C, and F: 1
- Replicated Shimojo et al. noise level of 11 K: 1
- Single-dish images checked to support the assumed background value: 1

### Key parameters and settings (bibcode: value)
- 2021ApJ...910...77M: Accept center-to-limb distances between 815 arcsec (0.85 Rθ) and 1100 arcsec (1.15 Rθ)
- 2021ApJ...910...77M: Equatorial: 30° N to 30° S; polar: above 60° N and below 60° S
- 2021ApJ...910...77M: Retain at least 35% of limb points, usually 6 out of 16; otherwise discard the map
- 2021ApJ...910...77M: Store radii between 800 and 1300 arcsec with standard deviation below 20 arcsec
- 2021ApJ...910...77M: SST running mean: 300 points; clipping: ±2.5σ
- 2021ApJ...910...77M: Used 29 088 SST maps: 24 186 at 212 GHz and 4902 at 405 GHz
- 2021ApJ...910...77M: Used 196 ALMA maps: 125 at 100 GHz and 71 at 230 GHz
- 2021ApJ...910...77M: 100, 212, 230, and 405 GHz
- 2021ApJ...910...77M: Radius smoothing: 100 days; proxy running mean: 396 days (13 months); averages every 6 months
- 2021ApJ...910...77M: Solar activity proxies: 10.7-centimeter solar flux F10.7 and mean photospheric magnetic field intensity |B|
- 2021ApJ...910...77M: SST correlations: 212 and 405 GHz, 2007–2019; ALMA qualitative comparison: 100 and 230 GHz, 2015–2018
- 2017ApJ...841L...5S: enhancements 145 K, 68.1, 49.8, 20.2 DN/s/pixel
- 2025A&A...693A..19S: 2 s image cadence
- 2025A&A...693A..19S: 1568 s lifetime
- 2025A&A...693A..19S: Seven slits perpendicular to fibril axis; spacing 5 pixels = 510 km
- 2025A&A...693A..19S: Slits in the portion visible throughout the time series
- 2025A&A...693A..19S: Remove periods >1000 s, frequencies <1 mHz
- 2025A&A...693A..19S: Remove Cone of Influence
- 2025A&A...693A..19S: In-phase φ=0° and anti-phase φ=180° indicate standing waves
- 2025A&A...693A..19S: 95% confidence; outside CoI; power weighting
- 2025A&A...693A..19S: Exclude ±180° phase angles
- 2025A&A...693A..19S: 95% confidence; outside CoI; phase differences weighted by power
- 2021A&A...655A.113M: Detection: flux beyond 3x the RMS of the background sky
- 2021A&A...655A.113M: Science categories: Debris disks, Exoplanets, Disks around low-mass stars, Disks around high-mass stars, Main-sequence stars
- 2021A&A...655A.113M: Default CDS search radius of 5 arcsec
- 2021A&A...655A.113M: For gamma Vir A&B, both stars assumed to contribute to measured fluxes between 10^3 and 5x10^5 GHz; separate fluxes by Teff ratio
- 2021A&A...655A.113M: PHOENIX version 18.05
- 2021A&A...655A.113M: Synthetic spectrum covers 0.01 nm to 3.0 cm; Rayleigh-Jeans tail at low frequencies
- 2021A&A...655A.113M: T_B conversion uses solid angle Omega_s = pi R*^2 / D^2 (stellar radius and distance)
- 2021A&A...655A.113M: Band 6 (240 GHz), all antennas, 1 hour integration gives 3 sigma threshold of about 50 microJy
- 2023A&A...671A..69G: Band 3 simulation snapshots: [700-1288, 1428-2022, 2172-2764]; Band 6 simulation snapshots: [700-1182, 1294-1770, 1913-2389, 2499-2981, 3120-3354]
- 2023A&A...671A..69G: Degraded pixel sizes: 0.34 arcsec (Band 3) and 0.14 arcsec (Band 6)
- 2023A&A...671A..69G: DoG filter Gaussian widths: 0.5 and 2.0 times the median major axis of the ALMA beam; local maxima minimum separation: 1.5 times the median major beam
- 2023A&A...671A..69G: Flood fill tolerance: ~2.4 standard deviations (FWHM halfway between seed peak temperature and FoV median temperature); max border distance filter: 4 times med…
- 2023A&A...671A..69G: FFT velocity amplitude threshold: > 2 standard deviations above the average
- 2023A&A...671A..69G: Linear detrending; Tukey window length = 0.1; CWT significance threshold >= 95% confidence level outside the cone of influence
- 2023A&A...671A..69G: Observing frequencies: nu = 100 GHz (Band 3) and 240 GHz (Band 6); External mass density rho_e = 2.5e-8 kg m^-3 (Band 3) and 4.0e-7 kg m^-3 (Band 6)
- 2023A&A...671A..69G: Degraded simulation median formation heights: 1563 km (Band 3) and 1260 km (Band 6)
- 2017SoPh..292...87S: robust = 1.0
- 2024AN....34530149M: Band 3 pixel size 6 arcsec; QS radius ~15 pixels; CH radius 10 pixels
- 2024AN....34530149M: AR modified from 400 km to the model top; CH from 2 km to the model top; QS over the entire model height range
- 2024AN....34530149M: Range over which f_n and f_T are varied is set so the model matches observations in the height range
- 2022FrASS...9.1118D: Longitudinal rotation: -0.01 deg (230 GHz), -2.85 deg (100 GHz), 7.31 deg (17 GHz)
- 2022FrASS...9.1118D: Grid size: 256x256 pixels (~2" per pixel)
- 2022FrASS...9.1118D: Force-free parameter alpha = -0.005
- 2022FrASS...9.1118D: Minimum photospheric magnetic field |B|_min = 200 G
- 2022FrASS...9.1118D: Vertical voxel height resolution h_z = 50 km
- 2022FrASS...9.1118D: Umbra: |B| >= 1500 G (~200 pixels); Penumbra: 1000 <= |B_0| < 1500 G (~230 pixels); Plages: 200 <= |B_0| < 1000 G (~27200 pixels); Quiet Sun: |B| <= 200 G (~38…
- 2022FrASS...9.1118D: 5 free parameters: chromospheric temperature gradient, chromospheric electron density gradient, coronal temperature factor N_T, coronal electron density factor…
- 2022FrASS...9.1118D: GA settings: full-generation replacement, 10 generations, 100 children per generation, crossover probability = 0.85, variable mutation mode, initial mutation r…
- 2022FrASS...9.1118D: Gyroresonance harmonics s <= 5 with 10% uncertainty in |B| (3rd harmonic at 2000±200 G, 4th at 1500±150 G, 5th at 1200±120 G)
- 2022FrASS...9.1118D: 2D Gaussian beam FWHM: 25" (230 GHz), 58" (100 GHz), 10" (17 GHz)
- 2017A&A...605A..78A: ALMA data used up to theta~70 deg
- 2022A&A...661L...4A: Band 7 beam FWHM = 21 arcsec; scan duration = 3 min
- 2022A&A...661L...4A: Central region size = 500'' by 500''; smoothed to 21'' ALMA resolution
- 2022A&A...661L...4A: f_ref = 100 GHz; limb exclusion cutoffs = 70'' (Band 3), 35'' (Band 6), 30'' (Band 7)
- 2022A&A...661L...4A: Band 3 commissioning normalization factor = 1; polynomial degree = 3
- 2022A&A...661L...4A: C_1 = -0.5772157, C_2 = 1.978112, C_3 = -5.444874
- 2019ApJ...875..163R: 100 chains, 1000 steps including tuning
- 2020A&A...643A..41D: cell 0.3 arcsec, beam 1.2 arcsec, +7700 K
- 2020A&A...643A..41D: 9 sigma cores, 5 sigma halos
- 2020A&A...643A..41D: 4x4 px averaged intensities; 20% systematic uncertainty
- 2017ApJ...850...35L: 0.65 and 0.90 of surrounding white-light intensity
- 2022MNRAS.511..877M: 2′ band width centered on 2-D profile peak for SST 1-D beam extraction
- 2022MNRAS.511..877M: Quiet-Sun region radius: 7.5′
- 2022MNRAS.511..877M: Initial limb point distance filter: 815″ (0.85 R_theta) to 1100″ (1.15 R_theta)
- 2022MNRAS.511..877M: Iterative outlier rejection threshold: |r - R_bar| >= 10″; minimum 10 points (out of usual 34); maximum standard deviation 20″
- 2022MNRAS.511..877M: LB_synth grid: 0% to 40% in 5% steps; R_synth grid: 960″ to 976″ in 1″ steps (153 profiles)
- 2020A&A...638A..62N: Maximum error ≲ 5 K, or fewer than five points left
- 2020A&A...638A..62N: 2.5σ threshold; 12 pixels (targets 2-6) or 19 pixels (target 7)
- 2020A&A...638A..62N: Fit range: widest range with mean error bars <10%; Poisson uncertainties
- 2021A&A...652A..92N: Fit range lower 2-4 mHz, upper 30-50 mHz chosen by minimum chi^2
- 2020A&A...634A..86P: frequency resolution 1.7 mHz
- 2018A&A...613A..17B: C = 1.16
- 2018A&A...613A..17B: QS circle radius 5 pixels at disc centre, 30 pixels elsewhere
- 2021A&A...656A..68E: Ten equidistant frequencies per receiver band, averaged
- 2021A&A...656A..68E: Position angle fixed at 80 degrees
- 2021A&A...656A..68E: Analysis time range t=1000-2000 s for Tb and formation heights; 1550-1750 s for spatial power
- 2021A&A...656A..68E: Bins 0.02-0.2, 0.2-0.4, ..., 1.5-2.0 kK then 0.5 kK width
- 2018ApJ...863...96Y: T = 1e4–4e5 K; Tb=135 K; L≈1.5''
- 2020A&A...634A..56D: 19 temperature nodes, 9 vturb nodes, 7 vLOS nodes
- 2020A&A...634A..56D: IRIS instrumental profile Gaussian FWHM 53 mÅ
- 2019ApJ...877L..26L: 4 spws combined, 1.6'' beam, 0.3'' cells, 1090 images
- 2020A&A...644A.152E: amplitude threshold 400 K
- 2020A&A...644A.152E: radius 15''
- 2020A&A...644A.152E: initial amplitude 0.005-0.05 v0, period 90-210 s
- 2020A&A...640A..57A: Reduction to f_ref = 100 GHz via Tb((f/fref)^2 mu, fref)=Tb(mu,f)
- 2020A&A...635A..71W: TP SB2 mean in central 240'' radius scaled from 7454 K to 7300 K


### Assumptions (bibcode: value)
- 2021ApJ...910...77M: Circle representation of the solar limb within each selected latitude region
- 2021ApJ...910...77M: Optical reference radius Rθ = 959.63 arcsec, corresponding to R⊙ = 6.9599×10^8 m
- 2021ApJ...910...77M: Uniform solar-disk temperature
- 2021ApJ...910...77M: Different observing times distribute the SST scan-direction uncertainty uniformly across the data set
- 2021ApJ...910...77M: 2-D solar atmospheric SSC model developed by (cite: selhorst05)
- 2017ApJ...841L...5S: line-of-sight depth 4" (~3000 km), filling factor unity
- 2017ApJ...841L...5S: filling factor unity
- 2025A&A...693A..19S: Long periods likely represent slow magnetic-structure evolution.
- 2025A&A...693A..19S: ±180° standing-wave phase lag is not a propagation-time measurement.
- 2025A&A...693A..19S: Some standing patterns may be superpositions of oppositely propagating waves.
- 2021A&A...655A.113M: Rounded literature values for stellar parameters
- 2021A&A...655A.113M: Mm-cm emission originates from optically thick layers so T_B traces atmospheric temperature stratification
- 2021A&A...655A.113M: Sample chosen without companion or disk contamination, so excess is attributed to the star's own atmosphere
- 2021A&A...655A.113M: Solar T_B of 5900 K in band 6
- 2015A&A...573L...4L: Chromospheric height ~0.1% of stellar radius, as in the Sun
- 2023A&A...671A..69G: LTE radiative transfer using non-equilibrium electron densities from Bifrost; perfect spatial Fourier space sampling approximated by Gaussian beam convolution
- 2023A&A...671A..69G: Merged features terminate the lifespan of the individual merging features at the previous frame
- 2023A&A...671A..69G: 1 arcsec ~ 727 km; features are approximately circular (blob-like) so diameter of a circle of equal area represents feature size
- 2023A&A...671A..69G: External mass densities rho_e for ALMA observations are taken from the Bifrost simulation (within circles of 3x feature radius outside the feature); ALMA brigh…
- 2017SoPh..292...87S: Linear polarization negligible; XX and YY should be equal
- 2024AN....34530149M: Limb brightening correction applied to measured brightness temperatures before the modelling
- 2024AN....34530149M: Thermal bremsstrahlung is the dominant emission mechanism; Rayleigh-Jeans approximation; solar abundances; magnetic field neglected
- 2024AN....34530149M: For CH, f_T range is wide in case 1, restricted near 1 in case 2 and fixed to 1 in case 3; coronal temperature changes do not affect optically thin coronal emi…
- 2022FrASS...9.1118D: |B| is 7.5% greater than observed B_z due to heliographic position (17.40°N, 17.68°E)
- 2022FrASS...9.1118D: Linear force-free field approximation (current density parallel to magnetic field at any point in space)
- 2022FrASS...9.1118D: Pixels with |B| <= 200 G have quiet Sun brightness temperature T_B = T_qS
- 2022FrASS...9.1118D: Effective ion charge Z = 1.178, only electron-proton collisions considered, densities grouped as (n_e * n_i)^(1/2), plasma fully ionized above 1000 km in SSC m…
- 2017A&A...605A..78A: LTE thermal free-free and H- absorption proportional to f^-2
- 2022A&A...661L...4A: Arc-like modulations are associated with opacity variations and can be corrected by adjusting gains relative to the central field position in double-circle sca…
- 2022A&A...661L...4A: Both free-free and H^- absorption coefficients are proportional to f^-2
- 2022A&A...661L...4A: Absolute calibration of the December 2015 Band 3 commissioning observations is accurate
- 2022A&A...661L...4A: Thermal bremsstrahlung and H^- emission in local thermodynamic equilibrium; plane-parallel formal solution of radiative transfer equation
- 2019ApJ...875..163R: Flux scale error normal with 3σ = 5%
- 2019ApJ...875..163R: Isothermal plasma; C7 model background; purely hydrogen plasma; background Tb 7300±100 K
- 2020A&A...643A..41D: 1700 A continuum as EB proxy in absence of H-alpha
- 2020A&A...643A..41D: n_e ~1e9 cm^-3 or sqrt(EM/w) with filling factor 1; depth equals width
- 2020A&A...643A..41D: fully ionized hydrogen plasma
- 2017ApJ...850...35L: Disk-center QS ~6000 K (1.3 mm) and ~7400 K (3 mm)
- 2017ApJ...850...35L: Thermal free-free emission in LTE
- 2022MNRAS.511..877M: Derivatives of solar equator brightness temperature profiles are good approximations for the ALMA single-dish beam due to high spatial resolution and averaging…
- 2022MNRAS.511..877M: Synthetic profiles follow scaled SSC atmospheric model shapes.
- 2019ApJ...881...99M: 1D hydrostatic semi-empirical atmospheres; mm radiation in Rayleigh-Jeans approximation
- 2020A&A...638A..62N: Optically thick (tau 10-16), so excess Tb equals excess Te; filling factor 1; constant Ne; V_ap = A^(3/2)
- 2018A&A...619L...6N: FD disk-center Tb scaled to 7250 K
- 2021A&A...652A..92N: gamma=5/3; rho from FAL C model
- 2021A&A...652A..92N: height equals horizontal size; filling factor unity
- 2019ApJ...871...45S: R_sun = 696 Mm (959.64")
- 2020A&A...634A..86P: linear (white-noise) background
- 2020A&A...634A..86P: Upward sound waves at about 12 km/s (7000 K)
- 2021A&A...656A..68E: LTE in radiation formation
- 2021A&A...656A..68E: Best case: perfectly sampled observation, no noise or atmosphere
- 2021A&A...656A..68E: Base temperature is hottest of local pre/post minima (conservative)
- 2018ApJ...863...96Y: disk brightness 7000 K
- 2018ApJ...863...96Y: 100% filling factor, small optical thickness
- 2020A&A...634A..56D: 1D plane-parallel hydrostatic atmosphere; instantaneous NLTE electron densities; cyclotron and synchrotron neglected
- 2020A&A...644A.152E: Rayleigh-Jeans law and LTE
- 2020A&A...640A..57A: Commissioning calibration correct; opacity proportional to f^-2
- 2020A&A...640A..57A: Plane-parallel atmosphere, valid to mu~0.15
- 2021ApJ...906...83C: Vertical LOS, simulation degraded to IRIS and Band6 resolution
- 2020ApJ...888L..28S: spicule width 0.5''
- 2020ApJ...888L..28S: negligible background, T<10,000 K, thermal LTE electron-proton free-free emission
- 2020ApJ...891L...8M: Free-free hydrogen absorption main opacity source


### Limitations the authors admit
- 2021ApJ...910...77M: Large scatter remains in SST radius values despite strict selection.
- 2021ApJ...910...77M: Azimuth-elevation scanning increases radius uncertainty perpendicular to the scan direction.
- 2021ApJ...910...77M: SST radius time series are not strongly correlated with solar proxies.
- 2021ApJ...910...77M: ALMA observations cover a shorter period; longer observations are needed to establish trends.
- 2021ApJ...910...77M: Different radius definitions, methods, and instrumental bandwidths complicate comparisons between studies.
- 2021ApJ...910...77M: The exponential radius-frequency trend is descriptive rather than a physical model.
- 2017ApJ...841L...5S: ALMA-XRT alignment uncertain by up to 5"
- 2017ApJ...841L...5S: Three-dimensional path unknown
- 2025A&A...693A..19S: Only one long-lived fibril identified; other extended dark structures may contain unresolved fibrils.
- 2025A&A...693A..19S: Abrupt phase-angle changes may be noise or spurious signals.
- 2025A&A...693A..19S: Superposed wave modes complicate interpretation of cross-observable phase relationships.
- 2025A&A...693A..19S: Waveguide asymmetry and cross-sectional density structure require future detailed modeling.
- 2021A&A...655A.113M: Stellar radius, Teff and distance uncertainties cause notable flux uncertainty in the model comparison (gamma Vir)
- 2021A&A...655A.113M: Remaining calibration issues in the alpha Cen 230 GHz C2 data point
- 2021A&A...655A.113M: A single T_B point (GJ 2006 A) cannot support robust conclusions
- 2021A&A...655A.113M: Sample is small and an initial version
- 2015A&A...573L...4L: Sparse spectral sampling prevents a conclusive statement on changing opacities
- 2023A&A...671A..69G: Degrading the simulation by Gaussian beam convolution assumes perfect spatial Fourier space sampling rather than ALMA's true sparse uv coverage.
- 2023A&A...671A..69G: The feature tracking algorithm has a ~60% detection success rate when features overlap and systematically underestimates feature sizes by ~20%, which can affect radial velocity and energy flux estima…
- 2023A&A...671A..69G: ALMA Band 3 and Band 6 observations were not simultaneous and lack direct wave propagation measurements between the two bands.
- 2023A&A...671A..69G: Non-unity filling factors can over- or under-estimate energy flux, and external mass densities cannot be measured from ALMA data so simulation densities had to be used.
- 2023A&A...671A..69G: Standard photospheric cylinder models used to infer sausage wave modes from phase relations assume density and structural uniformity that may not hold in the chromosphere.
- 2017SoPh..292...87S: Robust value not fully optimized
- 2017SoPh..292...87S: Limb artifacts from incomplete uv sampling; only ~30 antennas
- 2024AN....34530149M: Only three observed wavelengths for AR and CH
- 2024AN....34530149M: Single-dish beams may average in surrounding regions and lead to incorrect conclusions
- 2024AN....34530149M: One-dimensional models give only mean brightness temperature of a structure
- 2024AN....34530149M: Models are hydrostatic while AR and CH profiles appear not to follow that trend
- 2022FrASS...9.1118D: The genetic algorithm is purely a mathematical solution and does not verify whether the atmospheric plasma is in local thermodynamic equilibrium (LTE).
- 2022FrASS...9.1118D: Low spatial resolution of ALMA single-dish observations (25" at 230 GHz, 58" at 100 GHz) smooths the dark umbra (25" diameter) with surrounding bright areas, masking the umbra at 100 GHz and reducing…
- 2022FrASS...9.1118D: The modeled atmospheric profiles that fit 230 and 100 GHz well cannot reach the high brightness temperatures observed at 17 GHz in non-polarized regions (reaching at most 1.2 T_qS vs. 2.8 T_qS observ…
- 2022FrASS...9.1118D: The modeled 17 GHz polarized gyroresonance source is smaller and rounder than the observed elliptical source.
- 2017A&A...605A..78A: 100 GHz results 30-55'' from the limb may be affected by the 60'' beam
- 2025OJAp....8E.129K: Input map is UV-based, not true millimetre; one map used for all frequencies; time-evolving atmosphere not studied
- 2022A&A...661L...4A: Low spatial resolution (21 arcsec) of the single-dish Band 7 images prevents a detailed study of the association between ALMA and H-alpha features.
- 2022A&A...661L...4A: Absolute calibration jumps exist between datasets, and cross-normalization cannot replace true absolute calibration (e.g., using the Moon).
- 2022A&A...661L...4A: The Band 7 results rely on observations from a single day and require verification with additional data.
- 2019ApJ...875..163R: Flux scale accuracy is the largest uncertainty; background gradient uncertainty not included; isothermal assumption
- 2020A&A...643A..41D: Simulation magnetic topology not comparable to the observed region; no IRIS data; DEM coronal estimates are lower limits
- 2017ApJ...850...35L: Side lobes may affect 1.3 mm umbral brightness, which should be treated as an upper limit
- 2022MNRAS.511..877M: SST antenna beams are wide (3.6′ and 3.3′), asymmetric, and have high secondary lobes, preventing direct measurement of limb brightening in SST maps and causing asymmetric convolved profiles.
- 2022MNRAS.511..877M: Solar atmospheric models such as SSC represent average approximations and do not always reproduce observations, particularly at millimeter wavelengths where chromospheric features like spicules near …
- 2019ApJ...881...99M: 1D hydrostatic models and 1D radiative transfer for H-alpha
- 2020A&A...638A..62N: Energies are upper limits owing to assumptions; poor resolution; optically thick emission samples only a thin layer; residual oscillation power may affect detection of weak events
- 2018A&A...619L...6N: Unexplained excess emission beyond the limb up to 1000 K; segregation method not unique
- 2021A&A...652A..92N: Observed p-mode rms is a lower limit since resolution is coarse and pixels are correlated
- 2019ApJ...871...45S: Sidelobes not removed so polar brightening is a lower limit; poor resolution
- 2020A&A...634A..86P: 10-min series limit frequency resolution to 1.7 mHz and prevent detecting longer-period oscillations; rms values are upper limits due to detrending
- 2018A&A...613A..17B: Selection criteria for AR and sunspot are crude and arbitrary; prominence result depends on ~5 arcsec overlay precision
- 2021A&A...656A..68E: Best-case scenario without noise, atmosphere, imaging artifacts; static slightly eccentric beam; correction factors not for one-to-one correction
- 2018ApJ...863...96Y: Absolute brightness temperature is hard to determine; S/N poor beyond 10'' off limb; resolution comparable to blob size
- 2018ApJ...863...96Y: Could not confirm jet generation models
- 2020A&A...634A..56D: STiC cannot treat time-dependent hydrogen ionization; 1D plane-parallel assumption; resolution difference between IRIS and ALMA
- 2020A&A...644A.152E: Resolution limits detection; 552 events is a lower limit
- 2017ApJ...845L..19B: Pixels are correlated on ALMA beam scale and not corrected for
- 2017ApJ...845L..19B: Datasets not strictly simultaneous
- 2020A&A...640A..57A: Poor statistics of HR data and reliance on commissioning calibration
- 2017ApJ...841L..20I: Single snapshot, limited resolution, cannot distinguish scenarios
- 2021ApJ...906...83C: Model should not be taken as perfect; modeled Band6 Tb is 2,000 K lower than observed
- 2020A&A...635A..71W: Absolute Tb scale from TP remains uncertain
- 2020ApJ...888L..28S: Width comparable to beam, so the actual width may be narrower
- 2020ApJ...888L..28S: Only relative brightness temperatures because single-dish data not combined
- 2020ApJ...891L...8M: Model is 2D and may limit LOS superposition

### Settings cards flag as needed but not stated
- casa version: 4
- self-calibration solution intervals: 2
- feathering parameters: 2
- exact alma map identifiers, campaign dates, and selection within each listed project.: 1
- alma and sst calibration procedures and the processing state of the input maps.: 1
- alma map pixel scale and the interpolation method used for sst maps.: 1
- numerical differentiation scheme, any profile smoothing, and treatment of multiple derivative extre…: 1
- solar rotation and earth-orbit correction formulae, ephemerides, and normalization epoch or distanc…: 1
- circle-fit objective, solver, weighting, initial center, and unambiguous convergence criterion.: 1
- definition of quoted radius uncertainties and conversion of angular radii to physical radii.: 1
- running-mean boundary handling, sigma-clipping iteration policy, and weighting across maps and rece…: 1
- sst beam matrices and numerical implementation of the uniform-disk convolution simulations.: 1
- ssc model inputs and the radius-extraction procedure applied to its profiles.: 1
- exact proxy files, daily and six-month averaging rules, handling of missing dates, and correlation …: 1
- casa version and imaging parameters (weighting, deconvolver, cell/image size): 1
- details of the shimojo17 calibration and noise-estimation procedures: 1
- self-calibration solution interval: 1
- exact time windows for signal and background averaging: 1
- gaunt factor formula used: 1
- exact aia response values and dem/response tool used: 1
- alma project/dataset identifier for retrieval beyond the sv acknowledgement: 1
- exact analyzed scan ids, timestamps and frame selection resolving the observing-span, scan-duration…: 1
- soap version, reduction configuration, calibration tables, flagging and brightness-temperature cali…: 1
- imaging task, weighting/robust value, deconvolution settings, masks, image dimensions and any prima…: 1
- exact fibril and slit coordinates, slit lengths and whether slit positions change between frames.: 1
- unsharp-mask kernel and adaptive histogram equalization settings.: 1
- gaussian model including background treatment, initial values, fit bounds, weighting and failed-fit…: 1
- tukey-window taper parameter and detailed wavelet-filter implementation.: 1
- morlet parameters, scale grid and significance-test noise model.: 1
- power weighting, histogram binning and sample aggregation rules.: 1
- treatment of zero and near-zero phase lags in phase-speed calculations.: 1
- image registration and sdo co-alignment procedures.: 1
- exact alma flux density values and uncertainties adopted for each star and band (the table of fluxe…: 1
- stellar parameters actually fed to phoenix (teff, log g, radius, metallicity, distance) per star: 1
- jvo product identifiers / member ous ids used for each star and band: 1
- details of the 2d gaussian fits (region, fixed or free parameters, error treatment) and any flux-sc…: 1
- casa version and imaging parameters of the vla pipeline (weighting, cell, deconvolver, self-calibra…: 1
- how uncertainties and error bars on s_obs, s_mod and delta s/s_mod were propagated: 1
- exact catalogues/data points retained from cds and the outlier-rejection criteria: 1
- procedure used to split gamma vir a/b fluxes (explicit formula) and to correct fluxes between 10^3 …: 1

## Paper excerpts (35 of 35, chosen for detail and spread over fields/years)

### 2021ApJ...910...77M: The Subterahertz Solar Cycle: Polar and Equatorial Radii Derived from SST and ALMA (2021; sun; observational_alma_primary)
- question: Measure equatorial and polar subterahertz solar radii and investigate their relationship with the solar activity cycle.
- step 1: Orient maps and extract limb points
  - method: Rotate solar North upwards, correct coordinates for Earth's orbital eccentricity, and identify scan-derivative maxima and minima as solar limb coordinates. [Radius Determination: "The first step is to extract the solar limb coordinates from each map which are defined as the maximum and minimum points of the numerical differentiation"] [Radius Determination: "All solar maps are rotated so that the position of the solar North points upwards, and the coordinates are corrected according to the eccentricity of the Earth’s orbit"]
  - parameter: Accept center-to-limb distances between 815 arcsec (0.85 Rθ) and 1100 arcsec (1.15 Rθ) [Radius Determination: "With this radius determination filter, only points with a center–to–limb distance between ${815}^{\prime\prime}$ ($0.85 R_{\theta}$) and ${1100}^{\prime\prime}$ ($1.15 R_{\theta}$) are considered."]
  - validation: Limb-point filtering intended to reject active-region, instrumental-error, and high-opacity contamination [Radius Determination: "During the limb points extraction, some criteria are adopted to avoid extracting limb points associated with active regions, instrumental errors or high atmospheric opacity"]
- step 2: Fit equatorial and polar radii for each map
  - method: Fit circles to latitude-selected limb coordinates; calculate radius as the average center-to-limb distance; apply the same method to SST and ALMA. [Radius Determination: "The solar limb coordinates are fit by a circle and the radius is calculated as the average of the center-to-limb distances."] [Radius Determination: "The same method is applied to both telescopes, so that a comparison between the 212 GHz radius of SST and the 230 GHz radius of ALMA could be made."]
  - parameter: Equatorial: 30° N to 30° S; polar: above 60° N and below 60° S [Radius Determination: "First, the radius of each map is determined using only the equatorial latitudes of the solar disk – points between ${30}^{\circ}$ N and ${30}^{\circ}$ S."] [Radius Determination: "Then, the polar radius is determined considering only points above ${60}^{\circ}$ N and below ${60}^{\circ}$ S."]
  - parameter: Retain at least 35% of limb points, usually 6 out of 16; otherwise discard the map [Radius Determination: "This process is repeated until there are at least 35% of the points, usually 6 out of 16 depending on the map and the latitude region – polar or equatorial."] [Radius Determination: "If there are fewer points remaining, the entire map is discarded; otherwise, the radius is calculated."]
  - parameter: Store radii between 800 and 1300 arcsec with standard deviation below 20 arcsec [Radius Determination: "If the radius value is between ${800}^{\prime\prime}$ and ${1300}^{\prime\prime}$ and the standard deviation is below ${20}^{\prime\prime}$, then the calculated radius is stored and the next map is submitted to this process."]
  - assumption: Circle representation of the solar limb within each selected latitude region [Radius Determination: "The solar limb coordinates are fit by a circle"] [Radius Determination: "First, the radius of each map is determined using only the equatorial latitudes of the solar disk"]
  - fitting: Successive circle fits, discarding points outside R̄ ±10 arcsec after each fit [Radius Determination: "For each fit, the points with center-to-limb distance (obtained from the fitting) outside the interval ($\bar{R}-$${10}^{\prime\prime}$, $\bar{R}+$${10}^{\prime\prime}$) are discarded, and then a new circle fit is performed with the remaining points."]
  - validation: Compare SST 212-GHz and ALMA 230-GHz radius determinations [Radius Determination: "The same method is applied to both telescopes, so that a comparison between the 212 GHz radius of SST and the 230 GHz radius of ALMA could be made."]
- step 3: Reject SST outliers and calculate average radii
  - method: Sigma-clip the SST radius distribution after subtracting a running mean; obtain average radii from the remaining values. [Radius Determination: "Thus, we applied a sigma clipping on the distribution, subtracting from the distribution a running mean of 300 points, and then discarding values that are outside the $\pm 2.5\sigma$ range."] [Radius Determination: "From the remaining values, we obtain the average radii."]
  - parameter: SST running mean: 300 points; clipping: ±2.5σ [Radius Determination: "Thus, we applied a sigma clipping on the distribution, subtracting from the distribution a running mean of 300 points, and then discarding values that are outside the $\pm 2.5\sigma$ range."]
  - parameter: Used 29 088 SST maps: 24 186 at 212 GHz and 4902 at 405 GHz [RESULTS: "We used 29 088 SST maps (from a total of 36 034 maps) to calculate the radii at 212 GHz (24 186 maps) and 405 GHz (4902 maps)"]
  - parameter: Used 196 ALMA maps: 125 at 100 GHz and 71 at 230 GHz [RESULTS: "196 ALMA maps to calculate the radii at 100 GHz (125 maps) and 230 GHz (71) maps"]
- step 4: Derive emission altitudes
  - method: Subtract the visible solar radius from mean subterahertz radii to determine emission altitudes above the photosphere. [Radius Determination: "Finally, the visible solar radius is subtracted from the the mean subterahertz radii to determine the altitudes in the atmosphere at which the 100, 212, 230, and 405 GHz emissions are predominantly produced."]
  - assumption: Optical reference radius Rθ = 959.63 arcsec, corresponding to R⊙ = 6.9599×10^8 m [INTRODUCTION: "At optical wavelengths the canonical value of the mean apparent solar radius is $R_\theta=$${959.63}^{\prime\prime}$ corresponding to $R_\odot=6.9599\times 10^8$ m."] [INTRODUCTION: "This value has been widely used in the literature, hence we adopt it as the reference value."]
- step 5: Assess beam-induced radius uncertainty
  - method: Convolve 2-D antenna beam matrices with a uniform-temperature solar disk. [Radius Determination: "To assess the quality of the radius determinations, here we carry out a series of simulations convolving 2-D antenna beam matrix representations with a solar disk with uniform temperature."]
  - assumption: Uniform solar-disk temperature [Radius Determination: "a solar disk with uniform temperature."]
  - assumption: Different observing times distribute the SST scan-direction uncertainty uniformly across the data set [Radius Determination: "Since SST has an altazimuthal mount and maps are obtained at different times of the day, the uncertainty is uniformly distributed in the data set."]
  - validation: Simulations show increased radius uncertainty perpendicular to azimuth-elevation scans [Radius Determination: "The results show that azimuth-elevation maps increase the uncertainty of radius determination in the direction perpendicular to scans."]
- step 6: Compare radii with the literature frequency trend
  - method: Plot measured radii alongside Table 1 literature values and overplot a least-square exponential trend. [Subterahertz Radii: "Our results are plotted with those from other authors"] [Subterahertz Radii: "To guide the eye, an exponential curve (dashed line) is over plotted to show the trend of the radius as a function of the observing frequency or wavelength"]
  - fitting: Least-square exponential fit; not a physical model [Subterahertz Radii: "Note that the trend curve is just a least-square exponential fit, not a physical model."]
  - validation: SST and ALMA radii appear consistent within uncertainties with the radius-frequency trend [Subterahertz Radii: "SST and ALMA radii seem to agree within uncertainties with the trend"]
- step 7: Compare measured radii with the SSC model
  - method: Generate SSC brightness-temperature profiles at the four observing frequencies and compare their radii with measurements. [Subterahertz Radii: "Next, we used a 2-D solar atmospheric model developed by (cite: selhorst05) (hereafter referred to as the SSC model) to generate profiles of temperature brightness, $T_B$, at 100, 212, 230, and 405 GHz"]
  - parameter: 100, 212, 230, and 405 GHz [Subterahertz Radii: "to generate profiles of temperature brightness, $T_B$, at 100, 212, 230, and 405 GHz"]
  - assumption: 2-D solar atmospheric SSC model developed by (cite: selhorst05) [Subterahertz Radii: "a 2-D solar atmospheric model developed by (cite: selhorst05) (hereafter referred to as the SSC model)"]
  - validation: 212-, 230-, and 405-GHz radii are close to model radii; 100-GHz radii are about 4 arcsec larger [Subterahertz Radii: "Our results at 212, 230 and 405 GHz are very close to the radii derived from the model, whereas the 100-GHz radii are about ${4}^{\prime\prime}$ bigger, not agreeing with the model."]
- step 8: Construct radius and solar-proxy time series
  - method: Use daily radius averages smoothed over 100 days, solar proxies smoothed over 396 days, and six-month averages. [Observational Time Series: "To analyze the radius variation over the solar activity cycle, we use the average taken every 6 months from the solar radii and solar proxies."] [Observational Time Series: "We use radius daily averages, smoothed over a 100-day period to build time series at radio frequencies."]
  - parameter: Radius smoothing: 100 days; proxy running mean: 396 days (13 months); averages every 6 months [Observational Time Series: "we use the average taken every 6 months from the solar radii and solar proxies."] [Observational Time Series: "We use radius daily averages, smoothed over a 100-day period to build time series at radio frequencies."]
  - parameter: Solar activity proxies: 10.7-centimeter solar flux F10.7 and mean photospheric magnetic field intensity |B| [Observational Time Series: "As solar activity proxies, we used the 10.7-centimeter solar flux, $F_{10.7}$, and the intensity of the mean photospheric magnetic field, $|B|$"]
  - validation: Compare six-month SST 212-GHz and ALMA 230-GHz equatorial and polar radius series [Correlation with Solar Activity: "We compared the equatorial and polar radius time series at 212 GHz (SST) with the time series of the equatorial and polar radii at 230 GHz (ALMA), with 6-month averages."]
- step 9: Assess relationships with solar activity
  - method: Calculate linear correlation coefficients between SST radii and solar proxies; qualitatively analyze ALMA radius variations. [Table 3: "Linear correlation coefficients, $\rho$, between solar radii and solar proxies."] [INTRODUCTION: "We analyze the equatorial and polar radius behavior over time, with qualitative analysis for 100 and 230 GHz (ALMA) from 2015 to 2018."]
  - parameter: SST correlations: 212 and 405 GHz, 2007–2019; ALMA qualitative comparison: 100 and 230 GHz, 2015–2018 [INTRODUCTION: "We analyze the equatorial and polar radius behavior over time, with qualitative analysis for 100 and 230 GHz (ALMA) from 2015 to 2018."] [INTRODUCTION: "Also, we determine the correlation coefficient between the solar activity proxies and equatorial and polar radii time series at 212 and 405 GHz (SST), from 2007 to 2019."]
  - validation: Compare behavior across frequencies, latitude regions, and both solar proxies [Correlation with Solar Activity: "the calculated correlation coefficients, $\rho$, are organized by frequency, solar latitude regions and solar proxies."] [Correlation with Solar Activity: "The radii derived from SST’s maps are found to have both average values and behavior over time very close to ALMA’s"]
- result: 100-GHz equatorial angular radius = 968 ± ±3 arcsec [Table 2: "| 100 | Equatorial | 968$\pm$3 | 702.1$\pm$2.2 | 6.1$\pm$2.2 | 964.2 | |"]
- result: 100-GHz polar angular radius = 968.4 ± ±2.3 arcsec [Table 2: "| | Polar | 968.4$\pm$2.3 | 702.4$\pm$1.7 | 6.4$\pm$1.7 | | |"]
- result: 212-GHz equatorial angular radius = 963 ± ±4 arcsec [Table 2: "| 212 | Equatorial | 963$\pm$4 | 699$\pm$3 | 3$\pm$3 | 963.8 | |"]
- result: 212-GHz polar angular radius = 963 ± ±4 arcsec [Table 2: "| | Polar | 963$\pm$4 | 698$\pm$3 | 2$\pm$3 | | |"]
- result: 230-GHz equatorial angular radius = 963.7 ± ±1.8 arcsec [Table 2: "| 230 | Equatorial | 963.7$\pm$1.8 | 698.9$\pm$1.3 | 3.0$\pm$1.3 | 963.2 | |"]
- result: 230-GHz polar angular radius = 963.7 ± ±1.6 arcsec [Table 2: "| | Polar | 963.7$\pm$1.6 | 698.9$\pm$1.2 | 3.0$\pm$1.2 | | |"]
- result: 405-GHz equatorial angular radius = 963 ± ±5 arcsec [Table 2: "| 405 | Equatorial | 963$\pm$5 | 699$\pm$4 | 3$\pm$4 | 962.8 | |"]
- result: 405-GHz polar angular radius = 963 ± ±6 arcsec [Table 2: "| | Polar | 963$\pm$6 | 698$\pm$4 | 2$\pm$4 | | |"]
- result: 100-GHz equatorial physical radius = 702.1 ± ±2.2 10^3 km [Table 2: "| 100 | Equatorial | 968$\pm$3 | 702.1$\pm$2.2 | 6.1$\pm$2.2 | 964.2 | |"]
- result: 100-GHz polar physical radius = 702.4 ± ±1.7 10^3 km [Table 2: "| | Polar | 968.4$\pm$2.3 | 702.4$\pm$1.7 | 6.4$\pm$1.7 | | |"]
- result: 212-GHz equatorial physical radius = 699 ± ±3 10^3 km [Table 2: "| 212 | Equatorial | 963$\pm$4 | 699$\pm$3 | 3$\pm$3 | 963.8 | |"]
- result: 212-GHz polar physical radius = 698 ± ±3 10^3 km [Table 2: "| | Polar | 963$\pm$4 | 698$\pm$3 | 2$\pm$3 | | |"]
- result: 230-GHz equatorial physical radius = 698.9 ± ±1.3 10^3 km [Table 2: "| 230 | Equatorial | 963.7$\pm$1.8 | 698.9$\pm$1.3 | 3.0$\pm$1.3 | 963.2 | |"]
- result: 230-GHz polar physical radius = 698.9 ± ±1.2 10^3 km [Table 2: "| | Polar | 963.7$\pm$1.6 | 698.9$\pm$1.2 | 3.0$\pm$1.2 | | |"]
- result: 405-GHz equatorial physical radius = 699 ± ±4 10^3 km [Table 2: "| 405 | Equatorial | 963$\pm$5 | 699$\pm$4 | 3$\pm$4 | 962.8 | |"]
- result: 405-GHz polar physical radius = 698 ± ±4 10^3 km [Table 2: "| | Polar | 963$\pm$6 | 698$\pm$4 | 2$\pm$4 | | |"]
- result: 100-GHz equatorial emission altitude = 6.1 ± ±2.2 10^3 km [Table 2: "| 100 | Equatorial | 968$\pm$3 | 702.1$\pm$2.2 | 6.1$\pm$2.2 | 964.2 | |"]
- result: 100-GHz polar emission altitude = 6.4 ± ±1.7 10^3 km [Table 2: "| | Polar | 968.4$\pm$2.3 | 702.4$\pm$1.7 | 6.4$\pm$1.7 | | |"]
- result: 212-GHz equatorial emission altitude = 3 ± ±3 10^3 km [Table 2: "| 212 | Equatorial | 963$\pm$4 | 699$\pm$3 | 3$\pm$3 | 963.8 | |"]
- result: 212-GHz polar emission altitude = 2 ± ±3 10^3 km [Table 2: "| | Polar | 963$\pm$4 | 698$\pm$3 | 2$\pm$3 | | |"]
- result: 230-GHz equatorial emission altitude = 3.0 ± ±1.3 10^3 km [Table 2: "| 230 | Equatorial | 963.7$\pm$1.8 | 698.9$\pm$1.3 | 3.0$\pm$1.3 | 963.2 | |"]
- result: 230-GHz polar emission altitude = 3.0 ± ±1.2 10^3 km [Table 2: "| | Polar | 963.7$\pm$1.6 | 698.9$\pm$1.2 | 3.0$\pm$1.2 | | |"]
- result: 405-GHz equatorial emission altitude = 3 ± ±4 10^3 km [Table 2: "| 405 | Equatorial | 963$\pm$5 | 699$\pm$4 | 3$\pm$4 | 962.8 | |"]
- result: 405-GHz polar emission altitude = 2 ± ±4 10^3 km [Table 2: "| | Polar | 963$\pm$6 | 698$\pm$4 | 2$\pm$4 | | |"]
- result: 100-GHz SSC model radius = 964.2 ± not stated arcsec [Table 2: "| 100 | Equatorial | 968$\pm$3 | 702.1$\pm$2.2 | 6.1$\pm$2.2 | 964.2 | |"]
- result: 212-GHz SSC model radius = 963.8 ± not stated arcsec [Table 2: "| 212 | Equatorial | 963$\pm$4 | 699$\pm$3 | 3$\pm$3 | 963.8 | |"]
- result: 230-GHz SSC model radius = 963.2 ± not stated arcsec [Table 2: "| 230 | Equatorial | 963.7$\pm$1.8 | 698.9$\pm$1.3 | 3.0$\pm$1.3 | 963.2 | |"]
- result: 405-GHz SSC model radius = 962.8 ± not stated arcsec [Table 2: "| 405 | Equatorial | 963$\pm$5 | 699$\pm$4 | 3$\pm$4 | 962.8 | |"]
- result: 212-GHz equatorial radius correlation with F10.7 = 0.05 ± not stated dimensionless [Table 3: "| 212 GHz | Equatorial | 0.05 | 0.16 |"]
- result: 212-GHz equatorial radius correlation with |B| = 0.16 ± not stated dimensionless [Table 3: "| 212 GHz | Equatorial | 0.05 | 0.16 |"]
- result: 212-GHz polar radius correlation with F10.7 = -0.36 ± not stated dimensionless [Table 3: "| 212 GHz | Polar | -0.36 | -0.23 |"]
- result: 212-GHz polar radius correlation with |B| = -0.23 ± not stated dimensionless [Table 3: "| 212 GHz | Polar | -0.36 | -0.23 |"]
- result: 405-GHz equatorial radius correlation with F10.7 = 0.64 ± not stated dimensionless [Table 3: "| 405 GHz | Equatorial | 0.64 | 0.50 |"]
- result: 405-GHz equatorial radius correlation with |B| = 0.50 ± not stated dimensionless [Table 3: "| 405 GHz | Equatorial | 0.64 | 0.50 |"]
- result: 405-GHz polar radius correlation with F10.7 = -0.39 ± not stated dimensionless [Table 3: "| 405 GHz | Polar | -0.39 | -0.23 |"]
- result: 405-GHz polar radius correlation with |B| = -0.23 ± not stated dimensionless [Table 3: "| 405 GHz | Polar | -0.39 | -0.23 |"]
- limitation (authors): Large scatter remains in SST radius values despite strict selection. [Radius Determination: "Even with the strict criteria adopted in the mean radius determination, there is still a large scattering in the distribution of SST radius values."]
- limitation (authors): Azimuth-elevation scanning increases radius uncertainty perpendicular to the scan direction. [Radius Determination: "The results show that azimuth-elevation maps increase the uncertainty of radius determination in the direction perpendicular to scans."]
- limitation (authors): SST radius time series are not strongly correlated with solar proxies. [DISCUSSION AND CONCLUSIONS: "The radii time series are not strongly correlated with the solar proxies"]
- not stated (card): Exact ALMA map identifiers, campaign dates, and selection within each listed project.; ALMA and SST calibration procedures and the processing state of the input maps.; ALMA map pixel scale and the interpolation method used for SST maps.; Numerical differentiation scheme, any profile smoothing, and treatment of multiple derivative extrema.; Solar rotation and Earth-orbit correction formulae, ephem…

### 2017ApJ...841L...5S: The First ALMA Observation of a Solar Plasmoid Ejection from an X-Ray Bright Point (2017; sun; observational_alma_primary)
- question: What are the thermal structure and physical parameters (temperature, density, mass, energy) of a plasmoid ejected from an X-ray bright point, from combined 100 GHz ALMA, AIA EUV and XRT data?
- step 1: calibrate and image ALMA data
  - method: Calibrate per Shimojo17, 2-s imaging, self-calibration against full-period image, scale with single-dish background [Observation: "we carried out self-calibration using the image synthesized from the entire observing period as a reference, and this successfully removed the artificial motion."]
  - validation: jitter removal checked in 2-s movie [Observation: "this successfully removed the artificial motion"]
- step 2: co-align ALMA, AIA and XRT
  - method: convert ALMA RA/DEC to heliocentric; visual inspection for XRT [Observation: "The co-alignment between the ALMA images and the other wavelengths is achieved by the conversion of the a priori coordinate system of the ALMA images from RA/DEC to heliocentric."]
  - validation: precision better than 2" ALMA vs AIA; up to 5" vs XRT [Observation: "the precision of the co-alignment is better than 2$^{\prime\prime}$ for ALMA with respect to AIA"]
- step 3: measure plasmoid enhancements
  - method: time-averaged intensities during a window minus background from another window, in 100 GHz and AIA 171/193/211 [Thermal structure of the plasmoid: "The intensity enhancement corresponding to the plasmoid is derived from the time-averaged intensities during the period indicated by the dotted lines"]
  - parameter: enhancements 145 K, 68.1, 49.8, 20.2 DN/s/pixel [Thermal structure of the plasmoid: "The averaged enhancements that should be explained by the hypotheses are 145 K, 68.1 DN/sec/pixel, 49.8 DN/sec/pixel, and 20.2 DN/sec/pixel"]
  - assumption: line-of-sight depth 4" (~3000 km), filling factor unity [Thermal structure of the plasmoid: "we assume that the line-of-sight depth of the plasmoid is 4$^{\prime\prime}$ ($\sim$3000 km)"]
  - validation: 304 Å excluded due to resonance scattering [Thermal structure of the plasmoid: "we cannot obtain reliable quantitative results from 304 Å for the reasons given earlier"]
- step 4: test isothermal/multithermal hypotheses
  - method: compute density required vs temperature for each band using AIA responses and free-free emission (Lang80); find where curves intersect [Thermal structure of the plasmoid: "we use the standard formula for thermal free-free emission (cite: Lang80)"]
  - assumption: filling factor unity [Thermal structure of the plasmoid: "we assume that the filling factor of the plasma is unity"]
  - validation: XRT non-detection constrains T<1 MK [Plasmoid ejection observed with ALMA, A…: "we conclude that the plasmoid does not include significant coronal plasma at temperatures $>$1 MK"]
- step 5: derive mass and energies
  - method: from optically thin parameters: T=1e5 K, volume 3e25 cm3, n=3e9 cm-3 [Thermal structure of the plasmoid: "the mass of the plasmoid is of order 2$\times$10$^{11}$ g and the thermal and kinetic energies are 5$\times$10$^{24}$ ergs and 2$\times$10$^{24}$ ergs"]
  - validation: compared with polar jets (Sako13) and active-region jets (Liu16) [Thermal structure of the plasmoid: "These values are an order of magnitude smaller than, for example, the averaged thermal energy of polar X-ray jets"]
- result: 100 GHz enhancement = 145 ± not stated K [Thermal structure of the plasmoid: "145 K, 68.1 DN/sec/pixel, 49.8 DN/sec/pixel, and 20.2 DN/sec/pixel"]
- result: isothermal optically thin temperature range = 8.0e4 to 1.4e5 ± not stated K [Hypothesis 2): Isothermal plasma that i…: "around a temperature of 8.0$\times10^{4}\sim$1.4$\times$10$^{5}$ K and density of 3.5$\sim$3.9$\times$10$^{9}$ cm$^{-3}$"]
- result: isothermal optically thin density = 3.5-3.9e9 ± not stated cm^-3 [Hypothesis 2): Isothermal plasma that i…: "density of 3.5$\sim$3.9$\times$10$^{9}$ cm$^{-3}$"]
- result: plasmoid mass = 2e11 ± order of magnitude g [Thermal structure of the plasmoid: "the mass of the plasmoid is of order 2$\times$10$^{11}$ g"]
- result: thermal energy = 5e24 ± not stated erg [Thermal structure of the plasmoid: "the thermal and kinetic energies are 5$\times$10$^{24}$ ergs and 2$\times$10$^{24}$ ergs"]
- result: kinetic energy = 2e24 ± not stated erg [Thermal structure of the plasmoid: "the thermal and kinetic energies are 5$\times$10$^{24}$ ergs and 2$\times$10$^{24}$ ergs"]
- limitation (authors): ALMA-XRT alignment uncertain by up to 5" [Observation: "the positional uncertainty between ALMA and XRT might be as poor as 5$^{\prime\prime}$"]
- limitation (authors): Three-dimensional path unknown [Plasmoid ejection observed with ALMA, A…: "although we have no way of determining the exact path in three dimensions"]
- not stated (card): CASA version and imaging parameters (weighting, deconvolver, cell/image size); Details of the Shimojo17 calibration and noise-estimation procedures; Self-calibration solution interval; Exact time windows for signal and background averaging; Gaunt factor formula used; Exact AIA response values and DEM/response tool used; ALMA project/dataset identifier for retrieval beyond the SV acknowledgement

### 2025A&A...693A..19S: The Sun at millimeter wavelengths: V. Magnetohydrodynamic waves in a fibrillar structure (2025; sun; archival_reuse)
- question: Determine oscillation periods and phase speeds along a dark fibril to identify MHD wave modes.
- step 1: Fill calibration gaps
  - method: Linearly interpolate the four calibration breaks before wave analysis. [Observations: "four breaks (each 1.75 $-$ 2.25 minutes) for calibration, which were linearly interpolated before our wave analysis."]
  - parameter: 2 s image cadence [Observations: "This resulted in a time series of images with a high temporal resolution of 2 s"]
- step 2: Identify and track the fibril
  - method: Unsharp mask and adaptive histogram equalization for detection; track the dark structure through all frames. [Identification of oscillatory signals: "This method uses an unsharp mask algorithm and an adaptive histogram equalization procedure to enhance the intensity contrast between neighboring pixels and within the image (only for detection purposes)."] [Identification of oscillatory signals: "Using this method, we identified the long-lived fibril that persisted throughout the observed period."]
  - parameter: 1568 s lifetime [Identification of oscillatory signals: "To study waves and oscillations in the observed long-lived fibril, we track the dark elongated structure present in all frames, corresponding to a lifetime of 1568 s."]
  - validation: Selected fibril persists throughout the observed period. [Identification of oscillatory signals: "Using this method, we identified the long-lived fibril that persisted throughout the observed period."]
- step 3: Extract three oscillation observables
  - method: Measure slit brightness-temperature profiles; use Gaussian centroid, centroid brightness temperature and FWHM for position, intensity and width. [Identification of oscillatory signals: "We measured the brightness temperature in all pixels along each slit and determined the fibril’s position at each location by finding the centroid of the slit using Gaussian fitting."] [Identification of oscillatory signals: "Additionally, we calculated the brightness temperature at the centroid (representing the fibril’s intensity) and the full width at half maximum (FWHM) of the Gaussian fit (representing the fibril’s width) at each slit location."]
  - parameter: Seven slits perpendicular to fibril axis; spacing 5 pixels = 510 km [Identification of oscillatory signals: "To quantify oscillatory signals along the fibril, we placed seven artificial slits perpendicular to the fibril axis, spaced 5 pixels apart (corresponding to 510 km on the solar disc)."]
  - parameter: Slits in the portion visible throughout the time series [Identification of oscillatory signals: "The slits were positioned in the part of the fibril visible throughout the time series, as the fibril’s length varied over time."]
  - fitting: Gaussian fitting of slit brightness-temperature profiles [Identification of oscillatory signals: "We measured the brightness temperature in all pixels along each slit and determined the fibril’s position at each location by finding the centroid of the slit using Gaussian fitting."]
- step 4: Prepare oscillation time series
  - method: Linear detrending, Tukey apodisation and wavelet filtering to remove periods larger than 1000 s. [Wavelet analysis: "We note that all signals (corresponding to brightness temperature, width, and position) were detrended by using a linear fit and then apodised using a Tukey window prior to the wavelet analyses."] [Wavelet analysis: "Furthermore, periods larger than 1000 s (i.e., smaller than 1 mHz) were subtracted from all signals by means of wavelet filtering."]
  - parameter: Remove periods >1000 s, frequencies <1 mHz [Wavelet analysis: "Furthermore, periods larger than 1000 s (i.e., smaller than 1 mHz) were subtracted from all signals by means of wavelet filtering."]
  - assumption: Long periods likely represent slow magnetic-structure evolution. [Wavelet analysis: "Such long periods are likely related to slow evolution of the magnetic structure, rather than wave signatures."]
  - fitting: Linear fit for detrending [Wavelet analysis: "were detrended by using a linear fit and then apodised using a Tukey window prior to the wavelet analyses."]
- step 5: Measure wavelet power and phase relationships
  - method: Morlet power spectra for all three observables and seven slits; cross-power between consecutive slits and between observable pairs within each slit. [Wavelet analysis: "We calculated the wavelet power spectra of oscillations in all three parameters across the seven slits along the fibril using a Morlet function."] [Wavelet analysis: "Additionally, we calculated the wavelet cross-power spectra between consecutive slits for each parameter"]
  - parameter: Remove Cone of Influence [Wavelet analysis: "We identified and removed the Cone of Influence (CoI), the unreliable areas in the time-frequency space subject to edge effects, from further analyses."]
  - parameter: In-phase φ=0° and anti-phase φ=180° indicate standing waves [Wavelet analysis: "In-phase and anti-phase relationships are indicative of standing waves."] [Wavelet analysis: "Arrows pointing to the right represent in-phase oscillations ($\phi=0^\circ$), arrows pointing to the left represent anti-phase oscillations ($\phi=180^\circ$)"]
- step 6: Summarize oscillation periods
  - method: Construct power-weighted period distributions within 95% confidence and outside CoI; normalize each distribution by its maximum; calculate range, mean, median and standard deviation. [Wave periods: "These distributions are constructed by considering all power-weighted periods within the $95\%$ confidence levels and outside the CoI of the wavelet cross-power spectra calculated for each slit."] [Wave periods: "The final distribution is then normalized by its maximum value to facilitate comparison."]
  - parameter: 95% confidence; outside CoI; power weighting [Wave periods: "These distributions are constructed by considering all power-weighted periods within the $95\%$ confidence levels and outside the CoI of the wavelet cross-power spectra calculated for each slit."]
- step 7: Derive propagation speeds
  - method: Calculate τ=φP/(2π) between consecutive slits; derive phase speed from 510 km separation and time lag; summarize signed and absolute speeds and propagation directions. [Phase speeds: "\tau = \frac{\phi P}{2\pi},"] [Phase speeds: "Knowing the fixed distance between slits (510 km) and the calculated time lags, we determine the phase speed (or propagation speed) for brightness temperature, width, and position oscillations."]
  - parameter: Exclude ±180° phase angles [Phase speeds: "where $\phi$ is the phase angle (excluding $\pm180^\circ$) and $P$ is the wave period, both obtained from the wavelet analysis."]
  - parameter: 95% confidence; outside CoI; phase differences weighted by power [Phase speeds: "In this calculation, we also consider only phase differences that fall within the $95\%$ confidence levels and outside the CoI of the wavelet cross-power spectra."] [Phase speeds: "These phase differences are further weighted by power, emphasizing the significance of correlation strengths in the time-frequency domain."]
  - assumption: ±180° standing-wave phase lag is not a propagation-time measurement. [Phase speeds: "In a standing wave, a $\pm180^\circ$ phase-lag signifies a special relationship of persistent anti-phase oscillation, rather than a measure of propagation."]
- step 8: Interpret wave modes
  - method: Associate transverse oscillations with likely kink modes and width oscillations with likely sausage modes; interpret phase distributions as mixed standing and propagating waves. [Discussion and Conclusions: "The transverse oscillations likely represent the presence of MHD kink modes (cite: 1982SoPh...75....3S), while the size fluctuations (width oscillations) likely indicate sausage modes (cite: 1981SoPh...69...39R; 2013A&A...555A..75M)."] [Wavelet analysis: "The normalized phase-lag distributions"]
  - assumption: Some standing patterns may be superpositions of oppositely propagating waves. [Phase speeds: "The co-existence of these oppositely propagating waves in the same structure may suggest that at least some of the observed standing wave patterns (those with $0^\circ$ phase lags) may result from their superposition."]
- result: Tracked fibril lifetime = 1568 ± not stated s [Identification of oscillatory signals: "To study waves and oscillations in the observed long-lived fibril, we track the dark elongated structure present in all frames, corresponding to a lifetime of 1568 s."]
- result: Brightness-temperature period range = 21-692 ± not stated s [Table 1: "| Brightness temperature | 21-692 | 264 | 241 | 114 |"]
- result: Brightness-temperature mean period = 264 ± not stated s [Table 1: "| Brightness temperature | 21-692 | 264 | 241 | 114 |"]
- result: Brightness-temperature median period, Table 1 = 241 ± 114 (standard deviation of distribution) s [Table 1: "| Brightness temperature | 21-692 | 264 | 241 | 114 |"]
- result: Horizontal-displacement period range = 11-692 ± not stated s [Table 1: "| Horizontal displacement | 11-692 | 233 | 224 | 102 |"]
- result: Horizontal-displacement mean period = 233 ± not stated s [Table 1: "| Horizontal displacement | 11-692 | 233 | 224 | 102 |"]
- result: Horizontal-displacement median period, Table 1 = 224 ± 102 (standard deviation of distribution) s [Table 1: "| Horizontal displacement | 11-692 | 233 | 224 | 102 |"]
- result: Width period range = 13-692 ± not stated s [Table 1: "| Width | 13-692 | 260 | 272 | 118 |"]
- result: Width mean period = 260 ± not stated s [Table 1: "| Width | 13-692 | 260 | 272 | 118 |"]
- result: Width median period = 272 ± 118 (standard deviation of distribution) s [Table 1: "| Width | 13-692 | 260 | 272 | 118 |"]
- result: Brightness-temperature median period, abstract = 240 ± 114 (standard deviation of distribution) s [abstract: "We detected oscillations in brightness temperature, horizontal displacement, and width at multiple locations along the fibril, with median periods and standard deviations of $240\pm114$ s, $225\pm102$ s, and $272\pm118$ s, respectively."]
- result: Horizontal-displacement median period, abstract = 225 ± 102 (standard deviation of distribution) s [abstract: "We detected oscillations in brightness temperature, horizontal displacement, and width at multiple locations along the fibril, with median periods and standard deviations of $240\pm114$ s, $225\pm102$ s, and $272\pm118$ s, respectively."]
- result: Brightness-temperature signed mean phase speed = -29 ± not stated km/s [Table 2: "| Brightness temperature | -29 | -44 | 250 | 28$\%$ | 72$\%$ |"]
- result: Brightness-temperature signed median phase speed = -44 ± 250 (standard deviation of distribution) km/s [Table 2: "| Brightness temperature | -29 | -44 | 250 | 28$\%$ | 72$\%$ |"]
- result: Brightness-temperature mean absolute phase speed = 148 ± not stated km/s [Table 2: "| Brightness temperature | -29 | -44 | 250 | 28$\%$ | 72$\%$ | | absolute values | 148 | 74 | 204 | | |"]
- result: Brightness-temperature median absolute phase speed = 74 ± 204 (standard deviation of distribution) km/s [abstract: "oppositely propagating waves exhibit phase speeds (median and standard deviation of distributions) of $74\pm204$ km/s, $52\pm197$ km/s, and $28\pm254$ km/s for the three observables, respectively."]
- result: Brightness-temperature rightward / leftward propagation occurrence = 28 / 72 ± not stated % [Table 2: "| Brightness temperature | -29 | -44 | 250 | 28$\%$ | 72$\%$ |"]
- result: Horizontal-displacement signed mean phase speed = -12 ± not stated km/s [Table 2: "| Horizontal displacement | -12 | -27 | 222 | 32$\%$ | 68$\%$ |"]
- result: Horizontal-displacement signed median phase speed = -27 ± 222 (standard deviation of distribution) km/s [Table 2: "| Horizontal displacement | -12 | -27 | 222 | 32$\%$ | 68$\%$ |"]
- result: Horizontal-displacement mean absolute phase speed = 103 ± not stated km/s [Table 2: "| Horizontal displacement | -12 | -27 | 222 | 32$\%$ | 68$\%$ | | absolute values | 103 | 52 | 197 | | |"]
- result: Horizontal-displacement median absolute phase speed = 52 ± 197 (standard deviation of distribution) km/s [abstract: "oppositely propagating waves exhibit phase speeds (median and standard deviation of distributions) of $74\pm204$ km/s, $52\pm197$ km/s, and $28\pm254$ km/s for the three observables, respectively."]
- result: Horizontal-displacement rightward / leftward propagation occurrence = 32 / 68 ± not stated % [Table 2: "| Horizontal displacement | -12 | -27 | 222 | 32$\%$ | 68$\%$ |"]
- result: Width signed mean phase speed = -3 ± not stated km/s [Table 2: "| Width | -3 | -6 | 268 | 46$\%$ | 54$\%$ |"]
- result: Width signed median phase speed = -6 ± 268 (standard deviation of distribution) km/s [Table 2: "| Width | -3 | -6 | 268 | 46$\%$ | 54$\%$ |"]
- result: Width mean absolute phase speed = 86 ± not stated km/s [Table 2: "| Width | -3 | -6 | 268 | 46$\%$ | 54$\%$ | | absolute values | 86 | 28 | 254 | | |"]
- result: Width median absolute phase speed = 28 ± 254 (standard deviation of distribution) km/s [abstract: "oppositely propagating waves exhibit phase speeds (median and standard deviation of distributions) of $74\pm204$ km/s, $52\pm197$ km/s, and $28\pm254$ km/s for the three observables, respectively."]
- result: Width rightward / leftward propagation occurrence = 46 / 54 ± not stated % [Table 2: "| Width | -3 | -6 | 268 | 46$\%$ | 54$\%$ |"]
- limitation (authors): Only one long-lived fibril identified; other extended dark structures may contain unresolved fibrils. [Analysis and results: "Instead, we find a few extended dark structures, likely due to unresolved individual fibrils."]
- limitation (authors): Abrupt phase-angle changes may be noise or spurious signals. [Wavelet analysis: "We note that some of the abrupt changes in phase angles could be due to noise or spurious signals."]
- limitation (authors): Superposed wave modes complicate interpretation of cross-observable phase relationships. [Wavelet analysis: "However, interpreting such relationships is complex due to the potential superposition of multiple MHD wave modes, which current theoretical models are not yet sophisticated enough to fully disentangle"]
- not stated (card): Exact analyzed scan IDs, timestamps and frame selection resolving the observing-span, scan-duration and 1568 s lifetime discrepancy.; SoAP version, reduction configuration, calibration tables, flagging and brightness-temperature calibration procedure.; Imaging task, weighting/robust value, deconvolution settings, masks, image dimensions and any primary-beam correction or total-power combination.;…

### 2021A&A...655A.113M: EMISSA (Exploring Millimeter Indicators of Solar-Stellar Activity). I. The initial millimeter-centimeter main-sequence star sample (2021; stellar_physics, sun; archival_reuse)
- question: What is the atmospheric stratification (chromosphere/corona presence) of main-sequence stars as a function of stellar type, probed by mm-cm SEDs compared with a photospheric model
- step 1: Select ALMA main-sequence star sample from the archive
  - method: Search ALMA archive science categories for main-sequence stars, remove unknown types and spectroscopic binaries, then keep stars with clean significant detections in JVO first-look images [2.1.1 Archival data in the mm-cm band: "In total, publicly available data sets for 104 main sequence stars were identified."] [2.1.1 Archival data in the mm-cm band: "From these, 8 stars with unknown spectral type or luminosity class and 4 stars in spectroscopic binaries were removed."]
  - software: Python, VizieR, SIMBAD, ALMA Science Archive, JVO
  - parameter: Detection: flux beyond 3x the RMS of the background sky [2.1.1 Archival data in the mm-cm band: "the flux density of the target star was beyond at least three times the root mean square (RMS) flux of the background sky in the image"]
  - parameter: Science categories: Debris disks, Exoplanets, Disks around low-mass stars, Disks around high-mass stars, Main-sequence stars [2.1.1 Archival data in the mm-cm band: "‘Debris disks’, ‘Exoplanets’, ‘Disks around low-mass stars’, ‘Disks around high-mass stars’, and ‘Main-sequence stars’"]
  - validation: Contaminated sources identified by beam shape differing from the synthesised beam [2.1.1 Archival data in the mm-cm band: "data for many were found to have contamination from nearby sources, which was visible from the shape of the stars, which was significantly different from that of the synthesised beam."]
- step 2: Measure mm-cm flux densities
  - method: 2D Gaussian fit to each JVO ALMA image; VLA archive data imaged with an automated CASA-based pipeline; published ALMA fluxes preferred where available [2.1.1 Archival data in the mm-cm band: "The flux densities of different ALMA bands for each star were determined by fitting a two-dimensional Gaussian function to each image downloaded from the JVO."] [2.1.1 Archival data in the mm-cm band: "ALMA flux values from publications were preferred over values derived from JVO images"]
  - software: CASA
  - fitting: two-dimensional Gaussian function fit to each image [2.1.1 Archival data in the mm-cm band: "fitting a two-dimensional Gaussian function to each image downloaded from the JVO"]
  - validation: Published VLA stellar fluxes compared with the pipeline values [2.1.1 Archival data in the mm-cm band: "However, the published fluxes from stellar observations with the VLA match our pipeline values quite well."]
- step 3: Compile IR-EUV SED from catalogues
  - method: Query the CDS SED service by RA/DEC and search radius; for gamma Vir A&B use a smaller radius and split combined fluxes by Teff ratio [2.1.2 Archival data at higher frequenci…: "When provided the RA and DEC of a target source and a search radius, the CDS server looks for sources detected within the radius across the different astronomical catalogues and reports their fluxes as a function of frequency."]
  - software: CDS SED service (VizieR)
  - parameter: Default CDS search radius of 5 arcsec [2.1.2 Archival data at higher frequenci…: "CDS by default sets a radius of 5"]
  - parameter: For gamma Vir A&B, both stars assumed to contribute to measured fluxes between 10^3 and 5x10^5 GHz; separate fluxes by Teff ratio [2.1.2 Archival data at higher frequenci…: "For this frequency range, it is assumed that both stars contribute to the measured fluxes."]
- step 4: Compute photospheric model SED
  - method: PHOENIX 1D LTE model atmosphere and synthetic spectrum per star using the Husser et al. grid as starting point and rounded literature stellar parameters [2.2 PHOENIX model atmospheres: "A one-dimensional local thermal equilibrium (LTE) model atmosphere and the corresponding synthetic spectrum were calculated for each star in the sample using the PHOENIX code"]
  - software: PHOENIX
  - parameter: PHOENIX version 18.05 [2.2 PHOENIX model atmospheres: "using the current production version of PHOENIX (version 18.05)."]
  - parameter: Synthetic spectrum covers 0.01 nm to 3.0 cm; Rayleigh-Jeans tail at low frequencies [2.2 PHOENIX model atmospheres: "The synthetic spectrum covers a wavelength range from 0.01 nm to 3.0 cm"]
  - assumption: Rounded literature values for stellar parameters [2.2 PHOENIX model atmospheres: "For the stellar parameters, rounded literature values were used"]
  - validation: Model compared with observed SEDs at IR-UV frequencies, e.g. Delta S/S_mod near 0 at high frequencies for the Sun [3.1 Sun as a star: "while it remains relatively close to 0 at high frequencies between 10$^3$ GHz and 10$^6$ GHz, where the emission primarily originates from the photosphere."]
- step 5: Quantify excess and brightness temperature
  - method: Define spectral flux excess Delta S/S_mod = (S_obs - S_mod)/S_mod; convert S_nu to T_B with the Rayleigh-Jeans approximation; compute spectral index beta assuming S_obs proportional to nu^beta [Conclusions and outlook: "as the ratio of the difference between the observed and the PHOENIX model spectral flux density to the respective model values."] [Introduction: "Using the Rayleigh-Jeans approximation, the spectral flux density,"]
  - parameter: T_B conversion uses solid angle Omega_s = pi R*^2 / D^2 (stellar radius and distance) [Introduction: "The latter is given as $\Omega_s = \pi R_*^2/D^2$"]
  - assumption: Mm-cm emission originates from optically thick layers so T_B traces atmospheric temperature stratification [Introduction: "Because the emission primarily originates from optically thick layers in the mm range"]
  - validation: Results compared with earlier T_B analyses of alpha Cen A/B and Sirius [3.2 Stellar sample: "confirm the results of"]
- step 6: Compare excess across spectral types
  - method: Examine Delta S/S_mod spectra and Delta S/S_mod versus Teff in ALMA bands 6 and 7 for the sample [4.2 Dependence on spectral type: "for the stars in the sample for ALMA bands 7 and 6."]
  - assumption: Sample chosen without companion or disk contamination, so excess is attributed to the star's own atmosphere [4.2 Dependence on spectral type: "Because the stellar sample was chosen to have no contamination from any companion or disk in the mm–cm band range, the excess flux can be attributed to the excess thermal and/or non-thermal energy content that is connected to the presence of a stellar chromosphere."]
- step 7: Estimate ALMA detection distance for Sun-like stars
  - method: Scale the solar band 6 brightness temperature to a 3 sigma ALMA sensitivity threshold to find the maximum detection distance [4.3 Possible extension of the sample si…: "with the aforementioned detection threshold ALMA will detect a Sun-like star located within $10$ pc."]
  - parameter: Band 6 (240 GHz), all antennas, 1 hour integration gives 3 sigma threshold of about 50 microJy [4.3 Possible extension of the sample si…: "An observation in this band using all available antennas of ALMA with full spectral averaging and an integration time of 1 hour can provide a $3 \sigma$ source detection threshold of around $50\,\mu$Jy."]
  - assumption: Solar T_B of 5900 K in band 6 [4.3 Possible extension of the sample si…: "Assuming a typical temperature of $5900$ K for the Sun in band 6"]
- result: Final sample size of main-sequence stars with significant ALMA detection = 12 ± not stated stars [2.1.1 Archival data in the mm-cm band: "The final sample of stars with a significant detection in at least one ALMA band consists of 12 sources."]
- result: Reduced candidate sample after removing unknown-type stars and spectroscopic binaries = 92 ± not stated stars [2.1.1 Archival data in the mm-cm band: "This led to a reduced sample of 92 stars."]
- result: Brightness temperature of GJ 2006 A at 341 GHz = 1.6e5 ± not stated K [3.2 Stellar sample: "The ALMA flux corresponds to a brightness temperature of $1.6 \times 10^5$ K"]
- result: Brightness temperatures of gamma Vir A and B at ALMA bands 6 and 7 (lower limits) = >8000 (gamma Vir A); >7000 (gamma Vir B) ± not stated K [3.2 Stellar sample: "The corresponding brightness temperatures exceed 8000 K for $\gamma$ Vir A and 7000 K for $\gamma$ Vir B"]
- result: Delta S/S_mod of GJ 2006 A in band 7 (Discussion value) = 12000 ± not stated % [4.2 Dependence on spectral type: "has a significantly higher value (12000%) in its atmospheric layer probed by band 7"]
- result: Delta S/S_mod of GJ 2006 A in band 7 (Conclusions value, inconsistent with Discussion) = ~1100 ± not stated % [Conclusions and outlook: "In band 7, GJ 2006 A showed a flux excess of $\sim$ 1100%."]
- result: Delta S/S_mod of FGK stars in band 7 = ~0 to 1 ± not stated dimensionless [4.2 Dependence on spectral type: "we find that all the FGK stars show a $\Delta S/S_{mod}$ $\sim$ 0 – 1"]
- result: Maximum distance at which ALMA band 6 detects a Sun-like star (3 sigma, 1 hr) = 10 ± not stated pc [4.3 Possible extension of the sample si…: "ALMA will detect a Sun-like star located within $10$ pc."]
- limitation (authors): Stellar radius, Teff and distance uncertainties cause notable flux uncertainty in the model comparison (gamma Vir) [3.2 Stellar sample: "uncertainties for the stellar radii, effective temperatures, and to a lesser extent, for their distance, result in a notable flux uncertainty"]
- limitation (authors): Remaining calibration issues in the alpha Cen 230 GHz C2 data point [3.2 Stellar sample: "The C2 data point at 230 GHz seems to still have some calibration issues"]
- limitation (authors): A single T_B point (GJ 2006 A) cannot support robust conclusions [4.2 Dependence on spectral type: "it is hard to draw any robust conclusion."]
- not stated (card): Exact ALMA flux density values and uncertainties adopted for each star and band (the table of fluxes is not in the text), and which came from the paper's JVO fits versus publications; Stellar parameters actually fed to PHOENIX (Teff, log g, radius, metallicity, distance) per star; JVO product identifiers / member OUS IDs used for each star and band; Details of the 2D Gaussian fits (region, fixed …

### 2015A&A...573L...4L: ALMA observations of α Centauri. First detection of main-sequence stars at 3 mm wavelength (2015; stellar_physics, sun; observational_alma_primary)
- question: Can ALMA resolve the alpha Cen A and B components at mm/submm wavelengths, give their flux ratios, and extend the SED to 3 mm to probe the chromospheric temperature minimum and free-free emission?
- step 1: calibrate and image
  - method: CASA calibration with Ceres/Titan flux scales, quasar gain and bandpass calibrators; imaging with Briggs/natural weighting; B9 self-cal; primary beam correction [Observations and data reduction: "using, for all data sets, the quasar J$1617-5848$ as complex gain calibrator"]
  - software: CASA
- step 2: measure flux densities, ratios and spectral indices
  - method: Fluxes of A and B in each band; B/A ratios; spectral index alpha between bands [Results: "The measured flux densities are reported in Table [\[data\]](#data) and also displayed graphically in Fig. [2](#freq)."]
- step 3: compute brightness temperatures and compare with photospheres
  - method: Convert flux to T_B with stellar radius plus chromospheric height and compare to photospheric levels [Results: "In Fig. [3](#alma_ab), the SEDs are presented for both stars in terms of brightness temperature[^3] versus wavelength."]
  - assumption: Chromospheric height ~0.1% of stellar radius, as in the Sun [Discussion: "In the Sun, the height of the chromosphere $\int\!dh$ corresponds to about 0.1% of its radius."]
- result: alpha Cen A flux density Band 3 (3075 um) = 3.373 ± 0.011 mJy [Table 1: "$3.373\pm 0.011$ \[307\]"]
- result: alpha Cen B flux density Band 3 = 1.585 ± 0.016 mJy [Table 1: "$1.585\pm 0.016$ \[99\]"]
- result: alpha Cen A flux density Band 7 = 26.06 ± 0.19 mJy [Table 1: "$26.06\pm 0.19$ \[137\]"]
- result: alpha Cen B flux density Band 7 = 12.04 ± 0.23 mJy [Table 1: "$12.04\pm 0.23$ \[52\]"]
- result: alpha Cen A flux density Band 9 = 107.2 ± 1.5 mJy [Table 1: "$107.2\pm 1.5$ \[71\]"]
- result: alpha Cen B flux density Band 9 = 57.6 ± 4.5 mJy [Table 1: "$57.6\pm 4.5$ \[13\]"]
- result: flux ratio B/A at 3.1 mm = 0.47 ± 0.006 dimensionless [Results: "$=0.47\pm0.006$ at 3.1 mm"]
- result: flux ratio B/A at 870 um = 0.46 ± 0.01 dimensionless [Results: "$=0.46\pm0.01$ at 870 $\mu$m"]
- result: flux ratio B/A at 440 um = 0.54 ± 0.04 dimensionless [Results: "$S_{\!\nu}^{\rm B}/S_{\!\nu}^{\rm A}=0.54\pm0.04$ at 440 $\mu$m"]
- result: spectral index alpha(7,3) A / B = 1.62 / 1.61 ± not stated dimensionless [Table 1: "| 2.08 | 1.62 |"]
- limitation (authors): Sparse spectral sampling prevents a conclusive statement on changing opacities [Discussion: "a more conclusive statement would require a tighter spectral sampling, including the intermediate ALMA bands."]
- not stated (card): CASA version; Briggs robust value; Method of flux extraction (aperture vs Gaussian fit) and uncertainties; Phase/pointing offsets and details of self-cal solint; Distance to alpha Cen used

### 2023A&A...671A..69G: The Sun at millimeter wavelengths. IV. Magnetohydrodynamic waves in small-scale bright features (2023; sun; observational_alma_primary)
- question: Identify and study magnetohydrodynamic (MHD) waves and their energy flux in bright small-scale magnetic features in the solar chromosphere using ALMA Band 3 and Band 6 observations alongside Bifrost simulations.
- step 1: Synthesize and degrade simulation continuum brightness temperature maps to match ALMA observations
  - method: Solve radiative transfer with ART on Bifrost simulation snapshots to get Band 3 and Band 6 brightness temperatures, subsample frames to 2 s cadence with scan gaps matching ALMA, convolve with the median ALMA synthetic elliptical beam, and … [Simulation: "We used the Advanced Radiative Transfer code (cite: 2021_art) which solves the radiative transfer equation under the assumption of Local Thermodynamics Equilibrium (LTE)."] [Simulation: "For this, we have arbitrary chosen the snapshot corresponding to 700 s as starting point and so on removed every other frame, constructing a new time series wit the frames 700, 702, 704 and etc, until eventually we matched both ALMA observations time stamps."]
  - software: Bifrost, ART
  - parameter: Band 3 simulation snapshots: [700-1288, 1428-2022, 2172-2764]; Band 6 simulation snapshots: [700-1182, 1294-1770, 1913-2389, 2499-2981, 3120-3354] [Simulation: "In the case of Band 3, the 3 scans are composed of the snapshots [700-1288, 1428-2022, 2172-2764]. For the case of Band 6, the 5 scans correspond to the snapshots [700-1182, 1294-1770, 1913-2389, 2499-2981, 3120-3354]."]
  - parameter: Degraded pixel sizes: 0.34 arcsec (Band 3) and 0.14 arcsec (Band 6) [Simulation: "Subsequently, the pixel size of the simulation was changed from 0.066 arcsec to the respective 0.34 arcsec in Band 3 and 0.14 arcsec in Band 6."]
  - assumption: LTE radiative transfer using non-equilibrium electron densities from Bifrost; perfect spatial Fourier space sampling approximated by Gaussian beam convolution [Simulation: "We used the Advanced Radiative Transfer code (cite: 2021_art) which solves the radiative transfer equation under the assumption of Local Thermodynamics Equilibrium (LTE). In this work, ART uses the non-equilibrium electron densities provided by the Bifrost simulations"] [Simulation: "Please note that this approach assumes a perfect sampling of the spatial Fourier space while, in reality, ALMA's Fourier space coverage is sparse."]
  - validation: Tested a different starting snapshot for time series matching and confirmed it did not change final results [Simulation: "As a side note, we also did a test with a different starting snapshot and it did not change the final results"]
- step 2: Automatically identify, segment, track, and classify oscillating small-scale bright features
  - method: Apply a Difference of Gaussians (DoG) filter to each frame, find local maxima, segment features via Flood fill on normalized inverted images, filter out elongated/large masks, track overlapping masks frame-to-frame, and cluster extracted p… [Feature Identification and Tracking: "we applied to each frame a Difference of Gaussians (DoG) filter with Gaussian widths of half and double the median major axis of the ALMA beam."] [Feature Identification and Tracking: "Then, for each frame, we saved the position of all local maxima separated by at least 1.5 times the median major beam. Subsequently, we used the positions of the local maxima as seed points in the Flood fill method implemented in the Python Scikit-image library (cite: scikit-image)."]
  - software: SALAT, Scikit-image, Scikit-learn
  - parameter: DoG filter Gaussian widths: 0.5 and 2.0 times the median major axis of the ALMA beam; local maxima minimum separation: 1.5 times the median major beam [Feature Identification and Tracking: "we applied to each frame a Difference of Gaussians (DoG) filter with Gaussian widths of half and double the median major axis of the ALMA beam."] [Feature Identification and Tracking: "Then, for each frame, we saved the position of all local maxima separated by at least 1.5 times the median major beam."]
  - parameter: Flood fill tolerance: ~2.4 standard deviations (FWHM halfway between seed peak temperature and FoV median temperature); max border distance filter: 4 times median beam major axis; frame-to-frame overlap: >= 2 pixels [Feature Identification and Tracking: "This range was chosen such that for each seed point the method would flood all surrounding pixels within $\sim2.4$ standard deviations, corresponding to the full width at half maximum understood as all the pixels where the temperature is halfway between the pixel seed position (local maximum) temperature and the media…"] [Feature Identification and Tracking: "all the features with distances between any two points on their borders larger than 4 times the median beam major axis were discarded."]
  - assumption: Merged features terminate the lifespan of the individual merging features at the previous frame [Feature Identification and Tracking: "In the case that two or more masks merge in the following frame, each individual feature is considered alive until the previous frame."]
  - fitting: DBSCAN clustering on feature light curves [Feature Identification and Tracking: "These light curves are classified by means of the Density-Based Spatial Clustering of Applications with Noise (DBSCAN) algorithm which is part of the Python Machine Learning Scikit-learn package (cite: scikit-learn)."]
  - validation: Toy model control experiment with synthetic 2D Gaussian features placed via Poisson Disk Sampling with 5% noise and convolved with the ALMA beam: yielded ~60% detection success rate and showed systematic ~20% size underestimation. [Discussion and Conclusions: "However, the method systematically underestimates the true size of the detected features by $\sim$20% for most common sizes in Band 3 and 6."] [On the feature tracking method: "Therefore, the intention of this appendix is to asses the limitation of the algorithm with regard to the definition of the features borders. To this end, we designed a control experiment consisting of a toy model image filled with Gaussian-like fake features."]
- step 3: Extract physical properties, sizes, and horizontal velocities of tracked features
  - method: For each feature and frame, extract peak brightness temperature, compute equivalent circular diameter from mask area, track intensity-weighted centre of gravity to compute instantaneous horizontal velocities, and take the FFT of horizontal… [Occurrence and general properties: "For each individual feature, the algorithm returns its shape, area, value of the brightest pixel, average pixel value within the feature, initial and final time, and the position of the centre of gravity (of intensity) as computed from the pixel values within the feature's border as weights. For the purpose of this pa…"] [Location, lifetimes, size and horizonta…: "Each displacement of the centre of gravity in $x$ and $y$ directions between 2 consecutive frames was used to calculate the instantaneous horizontal velocities $v_x$ and $v_y$ and the corresponding instantaneous horizontal velocity $v_t = \sqrt{v_x^2 + v_y^2}$ for each feature."]
  - parameter: FFT velocity amplitude threshold: > 2 standard deviations above the average [Location, lifetimes, size and horizonta…: "The velocity amplitudes are computed by taking the fast Fourier transform of each horizontal velocity oscillation and subsequently choosing those amplitude values greater than two standard deviations over the average."]
  - assumption: 1 arcsec ~ 727 km; features are approximately circular (blob-like) so diameter of a circle of equal area represents feature size [Observations: "($1600$ km $\times$ $1235$ km assuming that $1$ arcsec $\approx$ 727 km)"] [Location, lifetimes, size and horizonta…: "Although the shape of the feature changes with time, it remains close to a blob-like shape, making the diameter of a circle of equal area an excellent proxy for its size and its corresponding evolution."]
  - fitting: Log-normal fits to size and horizontal velocity distributions [Location, lifetimes, size and horizonta…: "The blue and black thick lines shows a log-norm fit in each case."] [Location, lifetimes, size and horizonta…: "Again, the grey distributions correspond to results from simulations, the blue distributions to results from observations and the blue and black thick lines correspond to log-norm fits."]
  - validation: Verified that feature sizes exceed the median minor and major axes of the ALMA beam [Location, lifetimes, size and horizonta…: "In both panels, the vertical maroon dashed lines are the median minor and major axes of the ALMA beam in each corresponding band, showing that the features found by the method were completely resolved by ALMA."]
- step 4: Determine oscillation periods and temperature-size phase differences via wavelet analysis
  - method: Detrend temperature, size, and horizontal velocity time series with a linear fit, apodize with a Tukey window, and compute Continuous Wavelet Transforms (CWT) and cross-wavelet transforms between temperature and size. [Wavelet analysis and periods: "In order to determine the oscillation periods, we performed a continuous wavelet analysis (CWT) for temperature, size and velocity for each individual feature."] [Wavelet analysis and periods: "To proceed with the analysis of these oscillations, all time series corresponding to temperature, size and horizontal velocity were detrended (using a linear fit) and apodised (using a Tukey window with a length of 0.1)."]
  - parameter: Linear detrending; Tukey window length = 0.1; CWT significance threshold >= 95% confidence level outside the cone of influence [Wavelet analysis and periods: "To proceed with the analysis of these oscillations, all time series corresponding to temperature, size and horizontal velocity were detrended (using a linear fit) and apodised (using a Tukey window with a length of 0.1)."] [Wavelet analysis and periods: "The wavelet analysis described above is applied to each individual feature, resulting in the dominant oscillation periods (i.e., all periods corresponding to wavelet areas with a confidence level of 95% or larger and outside the cone of influence) as well as the phase differences between temperature and sizes."]
  - fitting: Linear fit for detrending time series prior to CWT [Wavelet analysis and periods: "all time series corresponding to temperature, size and horizontal velocity were detrended (using a linear fit)"]
  - validation: Restricted dominant period and phase extraction to wavelet regions with >= 95% confidence level and outside the cone of influence [Wavelet analysis and periods: "resulting in the dominant oscillation periods (i.e., all periods corresponding to wavelet areas with a confidence level of 95% or larger and outside the cone of influence)"]
- step 5: Estimate wave energy flux of sausage modes
  - method: Compute filling factor f, radial velocity perturbation v_r from radius amplitude and size period, phase speed v_ph from temperature and area fractional perturbations, and combine with external mass density rho_e from the Bifrost simulation… [Energy flux estimation: "The time averaged flux of energy $\langle F \rangle$ carried by a wave through a surface perpendicular to a magnetic flux tube can be estimated using the following equation originally provided by (cite: 2015A&A...578A..60M):"] [Energy flux estimation: "For the energy flux estimate presented here, we set $\delta r$ to the averaged amplitude of the radius oscillation across all features and $P$ to the averaged mean periods of size oscillations across all features."]
  - parameter: Observing frequencies: nu = 100 GHz (Band 3) and 240 GHz (Band 6); External mass density rho_e = 2.5e-8 kg m^-3 (Band 3) and 4.0e-7 kg m^-3 (Band 6) [Energy flux estimation: "The densities are taken directly from the simulation as the average of the mean values within circles of 3 times the radii of each feature excluding the densities inside the feature, being $\approx 2.5\times 10^{-8}$ kg m$^{-3}$ for Band 3 and $\approx 4.0\times 10^{-7}$ kg m$^{-3}$ for Band 6."] [Energy flux estimation: "$\nu$ is the frequency of observation ($100$ GHz for Band 3 and $240$ GHz for Band 6)"]
  - parameter: Degraded simulation median formation heights: 1563 km (Band 3) and 1260 km (Band 6) [Energy flux estimation: "of 1563 km for Band 3 and 1260 km for Band 6, the slope of the energy fluxes between the two heights in the observation is 12"]
  - assumption: External mass densities rho_e for ALMA observations are taken from the Bifrost simulation (within circles of 3x feature radius outside the feature); ALMA brightness temperature in Rayleigh-Jeans limit is a proxy for emission intensity [Energy flux estimation: "The densities are taken directly from the simulation as the average of the mean values within circles of 3 times the radii of each feature excluding the densities inside the feature, being $\approx 2.5\times 10^{-8}$ kg m$^{-3}$ for Band 3 and $\approx 4.0\times 10^{-7}$ kg m$^{-3}$ for Band 6."] [Energy flux estimation: "Given that brightness temperature measured from ALMA lies within the Rayleigh-Jeans limit, it can be applied as a proxy for emission intensity."]
  - validation: Uncertainties derived from error propagation analysis; compared observational energy fluxes against both original and degraded Bifrost simulations [Energy flux estimation: "Each value is shown with its respective uncertainty from the error propagation analysis."]
- result: Number of identified oscillating bright features (ALMA Band 3) = 193 ± not stated dimensionless [abstract: "We found 193 and 293 features in the Bands 3 and 6 observations, respectively."]
- result: Number of identified oscillating bright features (ALMA Band 6) = 293 ± not stated dimensionless [abstract: "We found 193 and 293 features in the Bands 3 and 6 observations, respectively."]
- result: Number of identified oscillating bright features (Degraded simulation Band 3) = 24 ± not stated dimensionless [abstract: "In the degraded simulation, the total number of features were 24 for Band 3 and 204 for Band 6."]
- result: Number of identified oscillating bright features (Degraded simulation Band 6) = 204 ± not stated dimensionless [abstract: "In the degraded simulation, the total number of features were 24 for Band 3 and 204 for Band 6."]
- result: Number of identified oscillating bright features (Original simulation Band 3) = 36 ± not stated dimensionless [abstract: "In the original simulation, the total number of features were 36 for Band 3 and 392 for Band 6."]
- result: Number of identified oscillating bright features (Original simulation Band 6) = 392 ± not stated dimensionless [abstract: "In the original simulation, the total number of features were 36 for Band 3 and 392 for Band 6."]
- result: Mean temperature oscillation period (ALMA Band 3) = 72 ± 29 s [Occurrence and general properties: "| **ALMA B3** | 72 | 66 | 29 | 68 | 62 | 28 | 61 | 52 | 27 |"]
- result: Mean size oscillation period (ALMA Band 3) = 68 ± 28 s [Occurrence and general properties: "| **ALMA B3** | 72 | 66 | 29 | 68 | 62 | 28 | 61 | 52 | 27 |"]
- result: Mean horizontal velocity oscillation period (ALMA Band 3) = 61 ± 27 s [Occurrence and general properties: "| **ALMA B3** | 72 | 66 | 29 | 68 | 62 | 28 | 61 | 52 | 27 |"]
- result: Mean temperature oscillation period (ALMA Band 6) = 52 ± 17 s [Occurrence and general properties: "| **ALMA B6** | 52 | 50 | 17 | 50 | 50 | 16 | 48 | 44 | 15 |"]
- result: Mean size oscillation period (ALMA Band 6) = 50 ± 16 s [Occurrence and general properties: "| **ALMA B6** | 52 | 50 | 17 | 50 | 50 | 16 | 48 | 44 | 15 |"]
- result: Mean horizontal velocity oscillation period (ALMA Band 6) = 48 ± 15 s [Occurrence and general properties: "| **ALMA B6** | 52 | 50 | 17 | 50 | 50 | 16 | 48 | 44 | 15 |"]
- result: Average horizontal velocity amplitude range = 2.1-5.0 ± not stated km s^-1 [abstract: "There are indications for the possible presence of transverse (kink) waves with average amplitude velocities of 2.1-5.0 km s$^{-1}$."]
- result: Filling factor (ALMA Band 3) = 3.7 ± 0.8 % [Wavelet analysis and periods: "| Filling factor [\%] | 3.7 $\pm$ 0.8 | 1.6 $\pm$ 1.0 | 1.3 $\pm$ 0.8 | 2.7 $\pm$ 0.7 | 1.2 $\pm$ 0.5 | 1.9 $\pm$ 0.5 |"]
- result: Filling factor (ALMA Band 6) = 2.7 ± 0.7 % [Wavelet analysis and periods: "| Filling factor [\%] | 3.7 $\pm$ 0.8 | 1.6 $\pm$ 1.0 | 1.3 $\pm$ 0.8 | 2.7 $\pm$ 0.7 | 1.2 $\pm$ 0.5 | 1.9 $\pm$ 0.5 |"]
- result: Phase speed v_ph (ALMA Band 3) = 14.7 ± 0.9 km s^-1 [Wavelet analysis and periods: "| Phase speed $\mathrm{v_{ph}}$ [ km s$^{-1}$] | 14.7 $\pm$ 0.9 | 13.0 $\pm$ 1.0 | 13.0 $\pm$ 1.4 | 13.2$\pm$ 0.9 | 11.6 $\pm$ 1.0 | 11.6 $\pm$ 1.3 |"]
- result: Phase speed v_ph (ALMA Band 6) = 13.2 ± 0.9 km s^-1 [Wavelet analysis and periods: "| Phase speed $\mathrm{v_{ph}}$ [ km s$^{-1}$] | 14.7 $\pm$ 0.9 | 13.0 $\pm$ 1.0 | 13.0 $\pm$ 1.4 | 13.2$\pm$ 0.9 | 11.6 $\pm$ 1.0 | 11.6 $\pm$ 1.3 |"]
- result: Time-averaged radial velocity <v_r> (ALMA Band 3) = 11.3 ± 0.3 km s^-1 [Wavelet analysis and periods: "| Radial velocity $\langle\mathrm{v_r}\rangle$ [ km s$^{-1}$] | 11.3 $\pm$ 0.3 | 9.8 $\pm$ 0.9 | 8.1 $\pm$ 0.5 | 5.6 $\pm$ 0.1 | 6.8 $\pm$ 0.1 | 7.2 $\pm$ 0.1 |"]
- result: Time-averaged radial velocity <v_r> (ALMA Band 6) = 5.6 ± 0.1 km s^-1 [Wavelet analysis and periods: "| Radial velocity $\langle\mathrm{v_r}\rangle$ [ km s$^{-1}$] | 11.3 $\pm$ 0.3 | 9.8 $\pm$ 0.9 | 8.1 $\pm$ 0.5 | 5.6 $\pm$ 0.1 | 6.8 $\pm$ 0.1 | 7.2 $\pm$ 0.1 |"]
- result: Fast-sausage wave energy flux (ALMA Band 3) = 1838 ± 429 W m^-2 [Wavelet analysis and periods: "| Energy flux [ W m$^{-2}$] | 1838 $\pm$ 429 | 621$\pm$ 407 | 453$\pm$ 289 | 5341 $\pm$ 1448 | 3640 $\pm$ 1557 | 5485 $\pm$ 1587 |"]
- result: Fast-sausage wave energy flux (ALMA Band 6) = 5341 ± 1448 W m^-2 [Wavelet analysis and periods: "| Energy flux [ W m$^{-2}$] | 1838 $\pm$ 429 | 621$\pm$ 407 | 453$\pm$ 289 | 5341 $\pm$ 1448 | 3640 $\pm$ 1557 | 5485 $\pm$ 1587 |"]
- result: Fast-sausage wave energy flux (Degraded simulation Band 3) = 621 ± 407 W m^-2 [Wavelet analysis and periods: "| Energy flux [ W m$^{-2}$] | 1838 $\pm$ 429 | 621$\pm$ 407 | 453$\pm$ 289 | 5341 $\pm$ 1448 | 3640 $\pm$ 1557 | 5485 $\pm$ 1587 |"]
- result: Fast-sausage wave energy flux (Degraded simulation Band 6) = 3640 ± 1557 W m^-2 [Wavelet analysis and periods: "| Energy flux [ W m$^{-2}$] | 1838 $\pm$ 429 | 621$\pm$ 407 | 453$\pm$ 289 | 5341 $\pm$ 1448 | 3640 $\pm$ 1557 | 5485 $\pm$ 1587 |"]
- result: Fast-sausage wave energy flux (Original simulation Band 3) = 453 ± 289 W m^-2 [Wavelet analysis and periods: "| Energy flux [ W m$^{-2}$] | 1838 $\pm$ 429 | 621$\pm$ 407 | 453$\pm$ 289 | 5341 $\pm$ 1448 | 3640 $\pm$ 1557 | 5485 $\pm$ 1587 |"]
- result: Fast-sausage wave energy flux (Original simulation Band 6) = 5485 ± 1587 W m^-2 [Wavelet analysis and periods: "| Energy flux [ W m$^{-2}$] | 1838 $\pm$ 429 | 621$\pm$ 407 | 453$\pm$ 289 | 5341 $\pm$ 1448 | 3640 $\pm$ 1557 | 5485 $\pm$ 1587 |"]
- result: Slope of observational wave energy flux between Band 6 and Band 3 formation heights = 12 ± 5 W m^-2 km^-1 [Energy flux estimation: "of 1563 km for Band 3 and 1260 km for Band 6, the slope of the energy fluxes between the two heights in the observation is 12"]
- limitation (authors): Degrading the simulation by Gaussian beam convolution assumes perfect spatial Fourier space sampling rather than ALMA's true sparse uv coverage. [Simulation: "Please note that this approach assumes a perfect sampling of the spatial Fourier space while, in reality, ALMA's Fourier space coverage is sparse."]
- limitation (authors): The feature tracking algorithm has a ~60% detection success rate when features overlap and systematically underestimates feature sizes by ~20%, which can affect radial velocity and energy flux estimates by a factor of sqrt(2). [Discussion and Conclusions: "20% for most common sizes in Band 3 and 6. We note that it does not affect the derived oscillation periods, or the measured temperatures and horizontal velocities."]
- limitation (authors): ALMA Band 3 and Band 6 observations were not simultaneous and lack direct wave propagation measurements between the two bands. [Discussion and Conclusions: "the fact that the ALMA data for Band 3 and Band 6 used here were not obtained simultaneous prevents drawing any strong conclusion regarding the differences in the found oscillations period distributions and its implications for any related decrease in the energy flux."]
- not stated (card): Hyperparameters (eps, min_samples, distance metric, and feature vector representation of light curves) used in the scikit-learn DBSCAN clustering to classify oscillating light curves; Mother wavelet function (e.g., Morlet) and wavenumber parameter used in the continuous wavelet transform (CWT); Value of the adiabatic index gamma and mean molecular weight assumed when computing the sound speed c_s…

### 2017SoPh..292...87S: Observing the Sun with the Atacama Large Millimeter/submillimeter Array (ALMA): High-Resolution Interferometric Imaging (2017; sun, instrumentation; technical_calibration_or_instrument)
- question: How can ALMA be commissioned and calibrated for continuum interferometric imaging of the Sun in Bands 3 and 6, and what do the resulting science-verification images show?
- step 1: Calibrate solar visibilities
  - method: Standard ALMA calibration with solar-specific amplitude calibration using Tant from hot/cold/sky/off/sun/zero power measurements and Tsys [3.2 Flux Calibration: "when observing the Sun $T_{\rm ant}>T_{\rm sys}$, and it is therefore necessary to measure both $T_{\rm sys}$ and $T_{\rm ant}$ in order to correctly scale the visibility measurements."]
  - software: CASA
  - validation: Phase variation from attenuator changes checked with 3C279; std 0.3 deg (IF Switch), 0.6 deg (IF Proc) [3.1 Gain Calibration: "its standard deviation across the spectral window is 0.3 degrees for the attenuator in the IF Switch, and 0.6 degrees in the IF Processor."]
- step 2: Synthesize mosaic images
  - method: clean mosaic with all four SPWs, 149 pointings, robust 1.0 [4.1 Data and Image Synthesis: "we include the data from all four SPWs for synthesizing one solar image in this article."]
  - software: CASA
  - parameter: robust = 1.0 [4.1 Data and Image Synthesis: "Hence, in this article, we always set the robust parameter to 1.0."]
  - validation: Stripe artifacts disappear with robust 1.0 [4.1 Data and Image Synthesis: "When this is done, the artificial stripes disappear in the image"]
- step 3: Combine with single-dish map
  - method: feather with full-Sun TP map [4.1 Data and Image Synthesis: "Figure 7e is the result of combining the synthesized image and the full-Sun map constructed from the simultaneous single-dish mapping data."]
  - software: CASA
  - validation: Combined Tb 5-10% above single-dish map at same position [4.1 Data and Image Synthesis: "the averaged brightness temperature of the combined image is always larger (5$\ --\ $10%) than the temperature brightness at the same position in the single-dish map"]
- step 4: Estimate noise
  - method: Difference of XX and YY images; Gaussian fit width of difference distribution [4.2 Estimating the Noise Level: "the difference between the two polarizations can therefore be used as a proxy for the noise level in the final images"]
  - software: CASA
  - assumption: Linear polarization negligible; XX and YY should be equal [4.2 Estimating the Noise Level: "the difference between the solar images synthesized from XX- and YY- data should be zero in principle"]
  - fitting: Gaussian fit to difference distribution [4.2 Estimating the Noise Level of Solar…: "From the width of the Gaussian function fitted to the distribution of the differential (Figure 9e), the noise level of the Band 3 synthesized image of the sunspot (Figure 7b) is 3.7 K"]
- step 5: Co-align with SDO/AIA and IRIS
  - method: Coordinate conversion only for AIA; visual inspection for IRIS [4.4 Co-alignment between ALMA and other…: "the co-alignment is done only by the visual inspection."]
  - validation: Co-alignment better than synthesized beam by comparing umbra edge [4.4 Co-alignment between ALMA and other…: "the precision of the co-alignment appears to be better than the size of the synthesized beam"]
- result: Noise level Band 3 sunspot image = 3.7 ± not stated K [4.2 Estimating the Noise Level: "is 3.7 K when the integration time is six seconds and the integration bandwidth is 8 GHz"]
- result: Noise level Band 6 sunspot image = 9.8 ± not stated K [4.2 Estimating the Noise Level: "estimate the noise level to be 9.8 K"]
- result: Synthesized beam Band 3 = 4.9 x 2.2 ± not stated arcsec [4.1 Data and Image Synthesis: "4.9$^{\prime\prime}$$\times$2.2$^{\prime\prime}$"]
- limitation (authors): Robust value not fully optimized [4.1 Data and Image Synthesis: "The value is not fully optimized, and the most suitable value might depends on the target and array configuration."]
- limitation (authors): Limb artifacts from incomplete uv sampling; only ~30 antennas [4.3 Imaging Artifacts Above the Solar L…: "The stripes are non-physical artifacts due to incomplete sampling"]
- not stated (card): Cell size, image size, niter, threshold and deconvolver for clean; Mask and cleaning details; CASA version; Exact feather parameters and how TP map and the correction factor were applied; Procedure for RA/Dec to heliocentric conversion; Which SV execution blocks and scripts map to each dataset beyond EB IDs

### 2024AN....34530149M: Calculated brightness temperatures of solar structures compared with ALMA and Metsähovi measurements (2024; sun; theory_or_simulation_compared_to_alma)
- question: Which semiempirical atmosphere model (AL or ATLCW) better reproduces ALMA and Metsähovi mm brightness temperatures of the quiet Sun, and what density and temperature scaling of the ATLCW model fits the quiet Sun, an active region and a cor…
- step 1: measure Band 3 brightness temperatures of QS, AR and CH
  - method: Average pixels in the Band 3 full-disc map: QS within ~15 pixel radius at disc centre; CH within 10 pixel radius away from the limb; AR from all pixels above a brightness threshold so sunspots are excluded; non-QS structures compared with … [Observational results / ALMA data: "by averaging the values of all pixels within a radius of about 15 pixels."] [Observational results / ALMA data: "The brightness temperature is then averaged over all pixels brighter than this threshold."]
  - parameter: Band 3 pixel size 6 arcsec; QS radius ~15 pixels; CH radius 10 pixels [Observational results / ALMA data: "The size of a single pixel of the Band 3 full-disc map is 6 arcsec on the Sun."] [Observational results / ALMA data: "within an area of a radius of 10 pixels within the visible CH structure"]
  - assumption: Limb brightening correction applied to measured brightness temperatures before the modelling [Observational results / ALMA data: "we applied the limb brightening correction to the measured brightness temperatures before the modeling was done."]
- step 2: assemble multi-wavelength brightness temperature table
  - method: Combine the new Band 3 values with Band 6 values from Brajša et al. (2018b), Band 5 and 7 QS values from Alissandrakis et al. (2023) and Metsähovi values at 3.40, 3.90 and 8.10 mm [Observational results / Metsähovi data: "The Metsähovi results for the brightness temperature were obtained using a similar procedure as described for ALMA, but with the limb brightening effect already accounted for"] [Observational results / ALMA data: "The results for Band 5 and 7, available only for QS"]
- step 3: compute model brightness temperature versus wavelength
  - method: Integrate thermal bremsstrahlung radiative transfer through the ATLCW QS model (Tb = integral of Te exp(-tau) dtau) over the structure's height range, per wavelength; Gaunt factor from van Hoof et al. interpolation; model density and tempe… [Models / Obtaining theoretical models: "These contributions are integrated over all heights defined for a given solar structure, yielding the total brightness temperature for a given wavelength"] [Models: "the Gaunt factor for the observed frequency is calculated using the accurate interpolation method recently developed by van Hoof et al."]
  - parameter: AR modified from 400 km to the model top; CH from 2 km to the model top; QS over the entire model height range [Models / Obtaining theoretical models: "For ARs, we assumed a minimum height of 400 km and a maximum of 57 km (maximum height value available in the ATLCW QS model)."] [Models / Obtaining theoretical models: "For QS on the other hand, the entire height range from the photosphere to the maximum available height in the ATLCW QS model was considered."]
  - assumption: Thermal bremsstrahlung is the dominant emission mechanism; Rayleigh-Jeans approximation; solar abundances; magnetic field neglected [Introduction: "Then the radiation mechanism is chosen, in this case thermal bremsstrahlung, and the radiative transfer equation is numerically solved for each input model."] [Models: "neglecting the magnetic field is given by (e.g., Benz"]
- step 4: fit density and temperature scaling factors by chi-squared minimisation
  - method: Vary f_n and f_T, recompute the profile for each pair, and take the global chi2 minimum over all observed wavelengths; AR and CH fitted with two measurement procedures (a: Delta Tb added to measured central QS; b: Delta Tb added to origina… [Models / Fitting theoretical models: "for each pair of the two multiplicative factors the brightness temperature calculation is repeated until the global minimum of Equation"] [Modeling results / Active region: "In the first procedure, which corresponds to the actual measurement, the brightness temperature of AR is determined by adding the difference"]
  - parameter: Range over which f_n and f_T are varied is set so the model matches observations in the height range [Models / Fitting theoretical models: "The range of values within which the two multiplicative factors are varied"]
  - assumption: For CH, f_T range is wide in case 1, restricted near 1 in case 2 and fixed to 1 in case 3; coronal temperature changes do not affect optically thin coronal emission [Modeling results / Coronal hole: "As the coronal radiation is optically thin, a change in coronal temperature would not result in a significant change in brightness temperature."]
  - fitting: Standard chi2 minimisation over (f_n, f_T); 1 sigma uncertainties from Delta chi2 = 1 above the minimum; sampler and priors not stated [Models / Fitting theoretical models: "The best-fitting brightness temperature profile minimizes the above sum."] [Models / Fitting theoretical models: "where the $\chi^2$ value reaches $\Delta\chi^2=1$ above the minimum"]
  - validation: Procedures a and b used to test whether small changes in the measurements change the output profile [Modeling results / Active region: "This approach was chosen to investigate whether a small change in the measurements would lead to a significant change in the output brightness temperature profile."]
- step 5: compare fitted structures with earlier results
  - method: Compare best-fit AR and CH densities and temperatures with earlier model/observational studies and the earlier FAL-based modelling [Discussion and conclusions: "Furthermore, we compare the current modeling results based on the modified ATLCW model presented in this work with earlier efforts by Brajša et al."]
- result: Band 3 (2.80 mm) brightness temperature of central QS = 7114 ± not stated K [Table 1: "ALMA | 2015-12-17 | 2.80/107 | 58 | 7114 | 7114 | $0$"]
- result: Band 3 (2.80 mm) brightness temperature of AR and difference from QS = 7928 (Delta Tb +625) ± not stated K [Table 1: "2015-12-17 | 2.80/107 | 58 | 7303 | 7928 | $+625$"]
- result: Band 3 (2.80 mm) brightness temperature of CH and difference from QS = 7398 (Delta Tb -145) ± not stated K [Table 1: "2015-12-17 | 2.80/107 | 58 | 7543 | 7398 | $-145$"]
- result: Metsähovi 8.10 mm brightness temperature of AR and difference from QS = 8580 (Delta Tb +480) ± not stated K [Table 1: "2015-12-19 | 8.10/37 | 144 | 8100 | 8580 | $+480$"]
- result: Metsähovi 8.10 mm brightness temperature of CH and difference from QS = 8020 (Delta Tb -80) ± not stated K [Table 1: "2015-12-19 | 8.10/37 | 144 | 8100 | 8020 | $-80$"]
- result: QS best-fit density factor f_n (QS_best) = 1.13 ± +0.14/-0.13 dimensionless [Table 3: "$1.13^{+0.14}_{-0.13}$"]
- result: QS best-fit temperature factor f_T (QS_best) = 0.99 ± +0.02/-0.02 dimensionless [Table 3: "$0.99^{+0.02}_{-0.02}$"]
- result: QS chi2_min = 1.19 ± not stated dimensionless [Table 3: "$1.19$"]
- result: AR best-fit density factor f_n, procedure a (AR_best) = 1.09 ± +0.18/-0.16 dimensionless [Table 3: "$1.09^{+0.18}_{-0.16}$"]
- result: AR best-fit temperature factor f_T, procedure a (AR_best) = 1.10 ± +0.04/-0.03 dimensionless [Table 3: "$1.10^{+0.04}_{-0.03}$"]
- result: AR best-fit density factor f_n, procedure b = 1.13 ± +0.17/-0.16 dimensionless [Table 3: "$1.13^{+0.17}_{-0.16}$"]
- result: AR best-fit temperature factor f_T, procedure b = 1.09 ± +0.03/-0.04 dimensionless [Table 3: "$1.09^{+0.03}_{-0.04}$"]
- result: AR density and temperature relative to QS (procedures a, b) = density 9%-13% higher; temperature 9%-10% higher ± not stated percent [Modeling results / Active region: "the density of the AR is 9%$-$13% higher than the QS level"]
- result: CH1_best density factor f_n, procedure a = 1/1.34 ± +1.34/-0.33 on the 1.34 dimensionless [Table 3: "$1/\left(1.34^{+1.34}_{-0.33}\right)$"]
- result: CH1_best density factor f_n, procedure b = 1/1.67 ± +3.84/-0.75 on the 1.67 dimensionless [Table 3: "$1/\left(1.67^{+3.84}_{-0.75}\right)$"]
- result: CH density relative to QS across the three CH cases = 1-1.7 times lower ± not stated dimensionless [Discussion and conclusions: "give a CH density 1$-$1.7 times lower than the QS value"]
- limitation (authors): Only three observed wavelengths for AR and CH [Discussion and conclusions: "It should be noted that for structures other than QS we had only three observed wavelengths on which to base our analysis and conclusions."]
- limitation (authors): Single-dish beams may average in surrounding regions and lead to incorrect conclusions [Discussion and conclusions: "single-dish measurements could potentially lead to incorrect conclusions about the solar structure depending on how much of the surrounding region is included in the average brightness temperature measurement."]
- limitation (authors): One-dimensional models give only mean brightness temperature of a structure [Discussion and conclusions: "the one-dimensional approach has a significant disadvantage compared to multidimensional models."]
- not stated (card): Which ALMA SV data product (file, execution block, calibration/reduction version) the Band 3 full-disc map of 2015-12-17 is, and how it was reduced and flux calibrated; Pixel positions of the QS, AR and CH regions used for averaging in the Band 3 map; The numerical brightness temperature threshold that defines the AR; The per-point brightness temperature uncertainties actually used in chi2 (the p…

### 2022FrASS...9.1118D: A Genetic Algorithm to Model Solar Radio Active Regions From 3D Magnetic Field Extrapolations (2022; sun; archival_reuse)
- question: Determine the plasma temperature and electron density height profiles in the solar atmosphere of active region NOAA 12470 to reproduce observed radio brightness temperature maps at 17, 100, and 230 GHz.
- step 1: Prepare, deproject, and co-align magnetogram and radio maps
  - method: Rotate AR in HMI LOS magnetogram to solar disk center, remove solar spherical curvature, correct magnetic field intensities for projection effects, longitudinally rotate radio maps to match magnetogram time, resize radio maps to match magn… [Magnetogram: "To correct for this, the AR has been rotated to solar disk center, solar spherical curvature has been removed, and the magnetic field intensities have been corrected for projection."] [Radio maps: "The nominal time of the 230 GHz map is 14:52 UT, i.e., only 1 minute difference from the nominal time of the HMI observation, requiring just $-0.01^\circ$ of longitudinal rotation. The nominal time of the 100 GHz map was 19:35 UT, requiring a longitudinal rotation of $-2.85^\circ$."]
  - software: IDL
  - parameter: Longitudinal rotation: -0.01 deg (230 GHz), -2.85 deg (100 GHz), 7.31 deg (17 GHz) [Radio maps: "The nominal time of the 230 GHz map is 14:52 UT, i.e., only 1 minute difference from the nominal time of the HMI observation, requiring just $-0.01^\circ$ of longitudinal rotation. The nominal time of the 100 GHz map was 19:35 UT, requiring a longitudinal rotation of $-2.85^\circ$."] [Radio maps: "We used a 17 GHz map observed at 02:44 UT and available in $512\times512$ pixels$^2$ format (4.91” resolution), rotated longitudinally by $7.31^\circ$ with respect to the HMI magnetogram."]
  - parameter: Grid size: 256x256 pixels (~2" per pixel) [Results: "To speed up the computational process, the datacubes and images were resized from $1024\times1024$ pixels$^2$ to $256\times256$ pixels$^2$, corresponding to a spatial resolution $\sim2''$ per pixel."]
  - assumption: |B| is 7.5% greater than observed B_z due to heliographic position (17.40°N, 17.68°E) [Gyroresonance contribution: "Due to the heliographic position of AR 12740 (17.40$^\circ$N, 17.68$^\circ$E), it is estimated that $|\vec{B}|$ is 7.5% greater than the observed $B_z$."]
- step 2: Extrapolate 3D coronal and chromospheric magnetic field from photospheric magnetogram
  - method: Perform linear force-free field (LFF) extrapolation above the photosphere starting from the line-of-sight magnetic field component to generate 3D cubes of Bx, By, Bz and field line positions, and interpolate voxel height resolution to 50 k… [Magnetic field extrapolation: "Photospheric magnetograms are used as the boundary condition for an extrapolation of the field above the photosphere using the linear force-free field approximation."] [Magnetic field extrapolation: "The result is three cubes of intensities, one for each component of the magnetic field vector ($B_x$, $B_y$, and $B_z$) and another data cube for the positions of the magnetic field lines."]
  - software: IDL
  - parameter: Force-free parameter alpha = -0.005 [Results: "A low value for the $\alpha$ parameter in (1) does not significantly affect the extrapolated magnetic field configuration at low heights in the atmosphere: here $\alpha=-0.005$ was chosen for the LFF extrapolation since it generated a greater number of closed magnetic field lines in the selected region than did the po…"]
  - parameter: Minimum photospheric magnetic field |B|_min = 200 G [Magnetic field extrapolation: "In this work, the extrapolated field lines were calculated only above positions with $|\vec{B}|_{min}=200$ G at the photosphere."]
  - parameter: Vertical voxel height resolution h_z = 50 km [Results: "However, the radiative transfer calculations require better resolution in the height of the voxels ($h_z$) due to the relatively narrow width of the chromosphere, and they were re-scaled via interpolation from the resolution of the magnetogram to 50 km, similar to the resolution of the SSC model."]
  - assumption: Linear force-free field approximation (current density parallel to magnetic field at any point in space) [Magnetic field extrapolation: "The fundamental equation that describes a force-free field (assuming that the current density is parallel to the magnetic field at any point in space) is"]
  - validation: Checked that |B|_min = 200 G avoided simulated ARs appearing much larger than observed ARs, and compared extrapolated field lines against SDO/AIA 193 Å image. [Magnetic field extrapolation: "A different minimum value could be chosen by the user, but we found that the inclusion of magnetic fields below this limit resulted in the simulated ARs appearing much larger than the observed ARs."] [Results: "Figure [3](#fig:AIA) shows some of the magnetic field lines obtained in the extrapolation with $\alpha=-0.005$ and $|\vec{B}|_{min}=200$ G."]
- step 3: Classify pixels by photospheric magnetic field strength
  - method: Classify each pixel in the magnetogram into four classes based on photospheric magnetic field intensity |B|_0: umbra, penumbra, plage, and quiet Sun. [Results: "The resulting atmospheric profiles were grouped into four different classes corresponding to different atmospheric features: umbrae, penumbrae, plage and quiet Sun."] [Results: "Each pixel in the magnetogram was classified as umbra, penumbra, or plage according to its intensity ($|\vec{B}|$), as follows: umbra, $|\vec{B}|\geq1500$ G ($\sim200$ pixels); penumbra, $1000\leq |\vec{B}_0|<1500$ G ($\sim$230 pixels); plages, $200\leq|\vec{B}_0|<1000$ G ($\sim$27200 pixels). All pixels with $|\vec{B…"]
  - parameter: Umbra: |B| >= 1500 G (~200 pixels); Penumbra: 1000 <= |B_0| < 1500 G (~230 pixels); Plages: 200 <= |B_0| < 1000 G (~27200 pixels); Quiet Sun: |B| <= 200 G (~38000 pixels) [Results: "Each pixel in the magnetogram was classified as umbra, penumbra, or plage according to its intensity ($|\vec{B}|$), as follows: umbra, $|\vec{B}|\geq1500$ G ($\sim200$ pixels); penumbra, $1000\leq |\vec{B}_0|<1500$ G ($\sim$230 pixels); plages, $200\leq|\vec{B}_0|<1000$ G ($\sim$27200 pixels). All pixels with $|\vec{B…"]
  - assumption: Pixels with |B| <= 200 G have quiet Sun brightness temperature T_B = T_qS [Results: "All pixels with $|\vec{B}|\leq200$ G were classified as quiet Sun ($\sim$38000 pixels) and were assumed to have $T_B=T_{qS}$."]
- step 4: Fit 1D atmospheric temperature and density profiles per pixel via genetic algorithm and radiative transfer
  - method: Run Pikaia genetic algorithm independently for each vertical column (pixel) to modify the seed SSC quiet Sun model via 5 free parameters, compute thermal bremsstrahlung and gyroresonance absorption coefficients and 1D radiative transfer to… [Atmospheric modelling via genetic algor…: "An initial 1D atmospheric model is used as a seed for the GA: at each step, $T_\mathrm{b}$ is obtained via the calculation of radiative transfer incorporating opacity from both the thermal bremsstrahlung and gyroresonance emission mechanisms."] [Atmospheric modelling via genetic algor…: "The GA iteratively updates the atmospheric plasma trapped by magnetic field lines until a best model is found via $\chi^2$ minimization of the calculated and observed $T_\mathrm{b}$ values."]
  - software: Pikaia
  - parameter: 5 free parameters: chromospheric temperature gradient, chromospheric electron density gradient, coronal temperature factor N_T, coronal electron density factor N_n_e, and TR position shift Delta h [Genetic Algorithm Features: "Five free parameters are supplied to the GA representing the atmospheric model."]
  - parameter: GA settings: full-generation replacement, 10 generations, 100 children per generation, crossover probability = 0.85, variable mutation mode, initial mutation rate = 0.005, mutation rate range = 0.0005 to 0.25 [Genetic Algorithm Features: "The method used here was full-generation replacement using ten generations with one hundred children each. The crossover probability was 0.85 and the mutation mode was variable. The initial mutation rate, that is, the initial probability that any gene locus will mutate in any generation, was 0.005. Finally, the mutati…"]
  - parameter: Gyroresonance harmonics s <= 5 with 10% uncertainty in |B| (3rd harmonic at 2000±200 G, 4th at 1500±150 G, 5th at 1200±120 G) [Emission mechanisms: "Since the contribution of higher harmonics to the radio emission is very small (cite: Shibasaki1994), the gyroresonance emission was only calculated for harmonics smaller than 5 ($s\leq 5$)."] [Gyroresonance contribution: "To investigate the gyroresonance contribution, $\kappa_g$ was calculated for harmonics $s\leq 5$, allowing for an uncertainty of $10\%$ in the $|\vec{B}|$ values."]
  - assumption: Effective ion charge Z = 1.178, only electron-proton collisions considered, densities grouped as (n_e * n_i)^(1/2), plasma fully ionized above 1000 km in SSC model [Emission mechanisms: "Only the contributions of collisions with protons was considered, since its density is much larger than that of other ion species ($n_i$)."] [Emission mechanisms: "Following (cite: Zirin1988), it was assumed $Z=1.178$, if a fully hydrogen atmosphere was considered, i.e. $Z=1$, the resulting $T_\mathrm{b}$ should be only $\sim 3\%$ smaller for all frequencies simulated here."]
  - fitting: Pikaia genetic algorithm with chi-squared minimization; full-generation replacement over 10 generations with 100 children each; stabilizes by ~7th generation. [Genetic Algorithm Features: "A generation of child atmospheric models is created by the algorithm based on the parent models with the lowest $\chi^2$ values, using the genetic algorithm described in (cite: Charbonneau1995)."] [Genetic Algorithm Features: "In our runs the $\chi^2$ measure typically stabilizes to a minimum value by about the seventh generation."]
  - validation: Monitored stabilization of chi-squared across generations and evaluated optical depth and contribution functions across atmospheric layers. [Genetic Algorithm Features: "In our runs the $\chi^2$ measure typically stabilizes to a minimum value by about the seventh generation."] [Free-free contribution: "In Figure [5](#fig:tau_cf) we show, for each atmospheric class, the optical depth ($\tau$, top row) and the contribution function (CF, bottom row), that represents the emission variation with the atmosphere height."]
- step 5: Convolve synthetic radio maps with instrumental beams and compare with observations
  - method: Convolve the 2" resolution GA model brightness temperature maps with 2D Gaussian beams matching observational resolutions (25" at 230 GHz, 58" at 100 GHz, 10" at 17 GHz) and compare average brightness temperatures across umbra, penumbra, p… [Comparison of the synthetic and observe…: "To compare the simulations with the observations, the model results were convolved with a 2D Gaussian beam that matches the resolution of the ALMA single-dish observations, i.e., 25” and 58” at 230 and 100 GHz, respectively."] [Comparison of the synthetic and observe…: "As summarized in Table [1](#Table:TB17_pol), when gyroresonance is taken into account the $T_\mathrm{b}$ values obtained for the highly polarized region are in agreement with those observed."]
  - parameter: 2D Gaussian beam FWHM: 25" (230 GHz), 58" (100 GHz), 10" (17 GHz) [Comparison of the synthetic and observe…: "To compare the simulations with the observations, the model results were convolved with a 2D Gaussian beam that matches the resolution of the ALMA single-dish observations, i.e., 25” and 58” at 230 and 100 GHz, respectively."] [Comparison of the synthetic and observe…: "If only free-free emission is considered, at 17 GHz the umbra appears darker in the model than the surrounding area, with a brightness temperature of $1.06\pm0.02\times T_{qS}$ at 10” resolution."]
  - validation: Compared synthetic vs. observed average T_b values (normalized to T_qS) within uncertainties across AR regions in Tables. [Comparison of the synthetic and observe…: "All the simulated areas are consistent with the observations to within the uncertainties."]
- result: Transition region (TR) height for umbrae = 1080 ± 20 km [Abstract: "for umbrae the TR is located at $1080\pm20$ km above the solar surface;"]
- result: Transition region (TR) height for penumbrae = 1800 ± 50 km [Abstract: "for penumbrae, the TR is located at $1800\pm50$ km;"]
- result: Transition region (TR) height for plages (bright regions outside sunspots) = 2000 ± 100 km [Abstract: "and for bright regions outside sunspots, the TR is located at $2000\pm100$ km."]
- result: Quiet Sun brightness temperature at 17 GHz = 10050 ± 120 K [Radio maps: "At 17 GHz, $T_{qS}=10050\pm 120$ K, and AR 12470 has brightness temperatures varying from $5.3\times10^4$ to $6.8\times10^4$ K in the areas with $|\vec{B}|>1500$ G."]
- result: Observed AR 12470 brightness temperature range at 230 GHz (where |B| > 1500 G) = 5800 to 6600 ± not stated K [Radio maps: "While the quiet Sun brightness temperature ( $T_\mathrm{b,QS}$) at 230 GHz is $6210\pm110$ K (cite: Selhorst2019), the AR 12470 brightness temperature ($T_\mathrm{b}$) varies from 5800 to 6600 K across locations with magnetic field intensities greater than 1500 G"]
- result: Observed AR 12470 brightness temperature range at 100 GHz (where |B| > 1500 G) = 7200 to 7650 ± not stated K [Radio maps: "At 100 GHz, $T_{qS}=7110\pm90$ K (cite: Selhorst2019) and AR 12470 showed $T_\mathrm{b}$ varying from 7200 to 7650 K where $|\vec{B}|>1500$ G."]
- result: Observed AR 12470 brightness temperature range at 17 GHz (where |B| > 1500 G) = 5.3e4 to 6.8e4 ± not stated K [Radio maps: "At 17 GHz, $T_{qS}=10050\pm 120$ K, and AR 12470 has brightness temperatures varying from $5.3\times10^4$ to $6.8\times10^4$ K in the areas with $|\vec{B}|>1500$ G."]
- result: Observed Umbra averaged brightness temperature at 230 GHz = 0.99 ± 0.04 T_qS [Comparison of the synthetic and observe…: "| Umbra | $0.99\pm0.04$ | $0.98\pm0.01$ | $1.00 \pm0.01$ | $1.03\pm0.01$ | $1.02\pm0.01$ | $1.06\pm0.01$ |"]
- result: Modeled Umbra averaged brightness temperature at 230 GHz (2" resolution) = 0.98 ± 0.01 T_qS [Comparison of the synthetic and observe…: "| Umbra | $0.99\pm0.04$ | $0.98\pm0.01$ | $1.00 \pm0.01$ | $1.03\pm0.01$ | $1.02\pm0.01$ | $1.06\pm0.01$ |"]
- result: Modeled Umbra averaged brightness temperature at 230 GHz (25" resolution) = 1.00 ± 0.01 T_qS [Comparison of the synthetic and observe…: "| Umbra | $0.99\pm0.04$ | $0.98\pm0.01$ | $1.00 \pm0.01$ | $1.03\pm0.01$ | $1.02\pm0.01$ | $1.06\pm0.01$ |"]
- result: Observed Umbra averaged brightness temperature at 100 GHz = 1.03 ± 0.01 T_qS [Comparison of the synthetic and observe…: "| Umbra | $0.99\pm0.04$ | $0.98\pm0.01$ | $1.00 \pm0.01$ | $1.03\pm0.01$ | $1.02\pm0.01$ | $1.06\pm0.01$ |"]
- result: Modeled Umbra averaged brightness temperature at 100 GHz (2" resolution) = 1.02 ± 0.01 T_qS [Comparison of the synthetic and observe…: "| Umbra | $0.99\pm0.04$ | $0.98\pm0.01$ | $1.00 \pm0.01$ | $1.03\pm0.01$ | $1.02\pm0.01$ | $1.06\pm0.01$ |"]
- result: Modeled Umbra averaged brightness temperature at 100 GHz (58" resolution) = 1.06 ± 0.01 T_qS [Comparison of the synthetic and observe…: "| Umbra | $0.99\pm0.04$ | $0.98\pm0.01$ | $1.00 \pm0.01$ | $1.03\pm0.01$ | $1.02\pm0.01$ | $1.06\pm0.01$ |"]
- result: Observed Penumbra averaged brightness temperature at 230 GHz = 1.05 ± 0.05 T_qS [Comparison of the synthetic and observe…: "| Penumbra | $1.05\pm0.05$ | $1.04\pm0.01$ | $1.02 \pm~0.02$ | $1.05\pm0.02$ | $1.07\pm0.01$ | $1.07\pm0.02$ |"]
- result: Modeled Penumbra averaged brightness temperature at 230 GHz (25" resolution) = 1.02 ± 0.02 T_qS [Comparison of the synthetic and observe…: "| Penumbra | $1.05\pm0.05$ | $1.04\pm0.01$ | $1.02 \pm~0.02$ | $1.05\pm0.02$ | $1.07\pm0.01$ | $1.07\pm0.02$ |"]
- result: Observed Penumbra averaged brightness temperature at 100 GHz = 1.05 ± 0.02 T_qS [Comparison of the synthetic and observe…: "| Penumbra | $1.05\pm0.05$ | $1.04\pm0.01$ | $1.02 \pm~0.02$ | $1.05\pm0.02$ | $1.07\pm0.01$ | $1.07\pm0.02$ |"]
- result: Modeled Penumbra averaged brightness temperature at 100 GHz (58" resolution) = 1.07 ± 0.02 T_qS [Comparison of the synthetic and observe…: "| Penumbra | $1.05\pm0.05$ | $1.04\pm0.01$ | $1.02 \pm~0.02$ | $1.05\pm0.02$ | $1.07\pm0.01$ | $1.07\pm0.02$ |"]
- result: Observed Plages averaged brightness temperature at 230 GHz = 1.07 ± 0.07 T_qS [Comparison of the synthetic and observe…: "| Plages | $1.07\pm0.07$ | $1.08\pm0.05$ | $1.04 \pm0.04$ | $1.06\pm0.04$ | $1.10\pm0.04$ | $1.06\pm0.03$ |"]
- result: Modeled Plages averaged brightness temperature at 230 GHz (25" resolution) = 1.04 ± 0.04 T_qS [Comparison of the synthetic and observe…: "| Plages | $1.07\pm0.07$ | $1.08\pm0.05$ | $1.04 \pm0.04$ | $1.06\pm0.04$ | $1.10\pm0.04$ | $1.06\pm0.03$ |"]
- result: Observed Plages averaged brightness temperature at 100 GHz = 1.06 ± 0.04 T_qS [Comparison of the synthetic and observe…: "| Plages | $1.07\pm0.07$ | $1.08\pm0.05$ | $1.04 \pm0.04$ | $1.06\pm0.04$ | $1.10\pm0.04$ | $1.06\pm0.03$ |"]
- result: Modeled Plages averaged brightness temperature at 100 GHz (58" resolution) = 1.06 ± 0.03 T_qS [Comparison of the synthetic and observe…: "| Plages | $1.07\pm0.07$ | $1.08\pm0.05$ | $1.04 \pm0.04$ | $1.06\pm0.04$ | $1.10\pm0.04$ | $1.06\pm0.03$ |"]
- result: Observed Polarized region averaged brightness temperature at 17 GHz = 3.69 ± 1.35 T_qS [Comparison of the synthetic and observe…: "| Polarized | $3.69\pm 1.35$ | $1.06\pm 0.03$ | $1.06\pm 0.02$ | $9.41\pm 3.51$ | $4.08\pm1.19$ |"]
- result: Modeled Polarized region averaged brightness temperature at 17 GHz with free-free + gyroresonance (10" resolution) = 4.08 ± 1.19 T_qS [Comparison of the synthetic and observe…: "| Polarized | $3.69\pm 1.35$ | $1.06\pm 0.03$ | $1.06\pm 0.02$ | $9.41\pm 3.51$ | $4.08\pm1.19$ |"]
- result: Observed Non-polarized region averaged brightness temperature at 17 GHz = 1.58 ± 0.32 T_qS [Comparison of the synthetic and observe…: "| Non-polarized | $1.58\pm 0.32$ | $1.04\pm 0.06$ | $1.04\pm 0.06$ | $1.04\pm 0.06$ | $1.04\pm 0.05$ |"]
- result: Modeled Non-polarized region averaged brightness temperature at 17 GHz with free-free + gyroresonance (10" resolution) = 1.04 ± 0.05 T_qS [Comparison of the synthetic and observe…: "| Non-polarized | $1.58\pm 0.32$ | $1.04\pm 0.06$ | $1.04\pm 0.06$ | $1.04\pm 0.06$ | $1.04\pm 0.05$ |"]
- limitation (authors): The genetic algorithm is purely a mathematical solution and does not verify whether the atmospheric plasma is in local thermodynamic equilibrium (LTE). [Genetic Algorithm Features: "Nevertheless, the GA used here is a mathematical solution and it does not verify if the atmospheric plasma is in local thermodynamic equilibrium (LTE) or not."]
- limitation (authors): Low spatial resolution of ALMA single-dish observations (25" at 230 GHz, 58" at 100 GHz) smooths the dark umbra (25" diameter) with surrounding bright areas, masking the umbra at 100 GHz and reducing its contrast at 230 GHz. [Comparison of the synthetic and observe…: "The resulting low contrast of the dark umbra with respect to the quiet Sun in the model is due to the low resolution of the ALMA single-dish observations. Since the umbral size is almost equal to the ALMA 230 GHz beam, the umbral $T_\mathrm{b}$ is smoothed with the bright surrounding areas."]
- limitation (authors): The modeled atmospheric profiles that fit 230 and 100 GHz well cannot reach the high brightness temperatures observed at 17 GHz in non-polarized regions (reaching at most 1.2 T_qS vs. 2.8 T_qS observed). [Comparison of the synthetic and observe…: "However, the modeled atmospheric profiles that achieved good agreement with the $T_\mathrm{b}$ observations at 230 and 100 GHz were not able to reach the high $T_\mathrm{b}$ values observed at 17 GHz. While these regions showed observational values as high as $2.8\times T_{qS}$, the model was only able to reach a maxi…"]
- not stated (card): Prior bounds (minimum and maximum values) chosen for each of the five GA free parameters (chromospheric temperature gradient, chromospheric electron density gradient, coronal temperature factor, coronal electron density factor, and TR position shift); Exact functional mathematical equations for how the five GA free parameters modify the SSC temperature and density height profiles; Details of the …

### 2017A&A...605A..78A: Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models (2017; sun; archival_reuse)
- question: To derive information on the temperature structure of the solar chromosphere and compare it with existing models.
- step 1: Select stable full-disk images
  - method: Compared repeated 100 GHz images and dropped the first Dec 16 image, which was 3.3% brighter [Observations: "the first image of the same day was 3.3% brighter and we preferred to ignore it in our analysis"]
  - validation: Total flux RMS of 0.2% across four 100 GHz images [Observations: "The total flux of the sun was remarkably stable, with an RMS of 0.2%."]
- step 2: Measure center-to-limb Tb curves
  - method: Tb as function of distance from disk center after masking bright and dark features; disk ellipticity taken into account [Results: "we calculated the brightness temperature, $T_b$, as a function of distance from the disk center, $r$"]
  - validation: Compared with high-resolution images near east limb (100 GHz) and south pole (239 GHz); reliable up to r~960'' [Results: "we are safe in using measurements up to $r\simeq960$$''$"]
- step 3: Correct for diffuse light
  - method: Fit Voigt function to CLV derivative near limb; deconvolve with Voigt, reconvolve with Gaussian core [Results: "we deconvolved with the Voigt function and reconvolved with the Gaussian core"]
  - fitting: Voigt function fit to derivative of CLV [Results: "this was better fitted with a Voigt function rather than with a Gaussian"]
- step 4: Invert CLV to Te(tau)
  - method: Assumed Te = a1 + a2 ln tau; Tb(mu)=a1+a2(ln mu - gamma); least-squares fit; data reduced to common reference frequency using f^-2 absorption [Inversion of the center-to-limb curve: "The coefficients $a_1$ and $a_2$ can be determined by least square fit of the observations."]
  - parameter: ALMA data used up to theta~70 deg [Inversion of the center-to-limb curve: "we used ALMA measurements up to $\theta\simeq70$$^\circ$"]
  - assumption: LTE thermal free-free and H- absorption proportional to f^-2 [Inversion of the center-to-limb curve: "both the free-free and the H$^-$ absorption coefficients are proportional to $f^{-2}$"]
  - fitting: Least squares on logarithmic form; residual RMS ~60 K [Inversion of the center-to-limb curve: "The fit was very good, with an RMS of residuals of $\sim60$ K"]
  - validation: Adding a quadratic term did not change results; power series unstable; compared with Eddington-Barbier and models [Inversion of the center-to-limb curve: "the addition of a quadratic term in ([\[logform\]](#logform)) did not change appreciably either the data fit or the inversion results"]
- result: Central Tb at 239 GHz = 6180 ± dispersion 100 K K [abstract: "The brightness temperature at the center of the disk is 6180 and 7250 K at 239 and 100 GHz respectively"]
- result: Central Tb at 100 GHz = 7250 ± dispersion 170 K K [abstract: "with dispersions of 100 and 170 K"]
- result: Solar radius at 239 GHz (1 AU) = 961.1 ± 2.5 arcsec [abstract: "$961.1\pm2.5$$''$ and $964.1\pm4.5$$''$ at 239 and 100 GHz"]
- result: Solar radius at 100 GHz (1 AU) = 964.1 ± 4.5 arcsec [abstract: "$961.1\pm2.5$$''$ and $964.1\pm4.5$$''$ at 239 and 100 GHz"]
- result: 239/100 GHz intensity ratio mean = 0.87 ± dispersion 0.01 dimensionless [Results: "The average value of the ratio is 0.87, with a dispersion of 0.01."]
- result: Global inversion slope a2 = -608 ± not stated K [Inversion of the center-to-limb curve: "The global inversion gave a slope of $a_2=-608$ K."]
- result: Slopes per band (100, 239, 343 GHz) = -608, -519, -818 ± not stated K [Inversion of the center-to-limb curve: "with slopes of $-608$, $-519$ and $-818$ K at 100, 239 and 343 GHz respectively"]
- result: Tb beyond the limb at r=1200'' = 100 (239 GHz), 93 (100 GHz) ± not stated K [Results: "it has a value of 100 K at 239 and 93 K at 100 GHz"]
- limitation (authors): 100 GHz results 30-55'' from the limb may be affected by the 60'' beam [Summary and conclusions: "which may have been affected by the 60$''$ antenna beam"]
- not stated (card): Calibration and image reconstruction details of the Science Verification full-disk images (CASA version, procedure); Absolute flux scale/uncertainty; Pixel size and how limb irregularities and the ellipticity were corrected; Voigt fit parameters for diffuse-light correction; Exact mask thresholds; Details of the Fig 4 CLV binning and elliptical radius fitting; Handling of 230 vs 239 GHz naming an…

### 2025OJAp....8E.129K: Observing the Sun with the Atacama Large Aperture Submillimeter Telescope (AtLAST): Forecasting Full-disk Observations (2025; sun, instrumentation; theory_or_simulation_compared_to_alma)
- question: What FOVs, detector counts and scan strategies let AtLAST scan the full solar disk in under 1 minute, enabling regular observations of dynamic phenomena such as flares?
- step 1: Construct millimetre full-disk input map
  - method: Combine AIA 304 (quiet Sun) with scaled AIA 1600 (active regions) via intensity mask, scale to ALMA TP brightness temperature distribution [3.2 Realistic high-resolution input maps: "We therefore construct the required millimetre full-disk maps by taking AIA 304 map, keeping the QS regions, but replacing the active regions with those in AIA 1600 Å multiplied with a scaling factor."]
  - validation: Visual comparison with ALMA TP maps convolved to TP beam [3.2 Realistic high-resolution input maps: "The threshold of which had to be adjusted slightly at different epochs to achieve the visually best reference map."]
- step 2: Simulate AtLAST scans for Cases A-C
  - method: maria simulations of circular detector arrays with double-circle or single-circle scans in four bands (100, 250, 670, 950 GHz) [4.2: "Three different instrumental setups with different scan strategies are discussed in detail."]
  - software: maria
- step 3: Derive scan time vs FOV and pixel count relations
  - method: Compute minor circles needed and scan time under AtLAST limits; fit power laws [4.3 Cadence of observations: "A wide range of instrument FOVs were then set-up, and the required number of minor circles per pattern computed"]
  - software: maria
  - fitting: Power-law (log-log) fits [Results, Cadence of observations: "To make this easier, the area between first-order log-log fits to the two different sampling lengths has been shaded to the appropriate colour associated with the pixel spacing."]
- step 4: Quantify map quality with power spectra with and without atmosphere
  - method: Compare spatial power spectra of synthetic maps to input map; rerun with 2D maria atmosphere [5.4: "we utilise spatial power spectra, as comparing these spectra to that of the input map will give insight"]
  - software: maria
- result: Case A scan time (1000 pixels, 36 minor circles) = 89 ± not stated s [4.2.1: "It was found that the required time needed to complete such a scan was $~89$ seconds."]
- result: Case B scan time = 11.4 ± not stated s [4.2.2: "the shortest time AtLAST could complete such a scan is $\sim 11.4$ seconds"]
- result: Case C scan time = 2.7 ± not stated s [4.2.3: "which it completes in about 2.7 seconds"]
- result: Pixels for 1-min cadence at 950 GHz, 1.0 fλ spacing = 24,464 ± not stated pixels [Table 1: "| 1.0 f$\lambda$ | 280 | 1708 | 12,165 | 24,464 |"]
- limitation (authors): Input map is UV-based, not true millimetre; one map used for all frequencies; time-evolving atmosphere not studied [3.2 Realistic high-resolution input maps: "full-disk maps in the ultraviolet are not perfect representations of the millimetre Sun, as slightly different heights in the atmosphere are probed."]
- not stated (card): maria version and configuration files (site, weather, sampling rate, beam model); AIA map dates, intensity mask threshold and 1600 Å scaling factor; Exact brightness temperature scaling applied per frequency; Atmosphere model parameters (PWV, seed); Power spectrum computation details; Calibrated ALMA TP map processing

### 2022A&A...661L...4A: A first look at the submillimeter Sun with ALMA (2022; sun; observational_alma_primary)
- question: What are the disk structures, center-to-limb brightness temperature variations, and chromospheric electron temperature profiles of the quiet Sun in the first full-disk ALMA Band 7 (0.86 mm; 347 GHz) solar images, combined with Bands 3 and …
- step 1: Acquire, select, and map full-disk Total Power images
  - method: Process 12-m TP double-circle scan observations using JAO CASA scripts and the methodology of White et al. (2017), selecting antennas with better T_sys (PM03 for Band 3, PM04 for Band 6, PM02 for Band 7) and applying CASA sdgaincal before … [Observations and data reduction: "In Bands 3 and 6, we only used the images that were provided by antennas PM03 and PM04, respectively, because of their better system temperature, $T_{sys}$."] [Observations and data reduction: "The TP data were acquired and processed using the methodology described by (cite: 2017SoPh..292...88W)."]
  - software: CASA, sdgaincal
  - parameter: Band 7 beam FWHM = 21 arcsec; scan duration = 3 min [Observations and data reduction: "The full width at half maximum (FWHM) of the Band 7 single dish beam was 21$''$ and each TP antenna scanned the full solar disk in 3 min."]
  - assumption: Arc-like modulations are associated with opacity variations and can be corrected by adjusting gains relative to the central field position in double-circle scans [Observations and data reduction: "It is possible that these modulations are associated with opacity variations during observations."] [Observations and data reduction: "This task takes advantage of the fact that the double-circle mode observes the same position in the center of the field of view and adjusts the gains throughout the whole dataset relative to the measured intensity at the center."]
  - validation: Suppression of large-scale arc-like brightness modulations in Band 7 images [Observations and data reduction: "We were able to largely suppress them by invoking CASA’s task sdgaincal before mapping."]
- step 2: Compare full-disk and central-region solar structures across wavelengths
  - method: Compare ALMA Band 7 full-disk and central 500'' x 500'' images against AIA 1700 Å, 1600 Å, and 304 Å images and GONG H-alpha (and negative H-alpha) images smoothed to the ALMA resolution. [abstract: "Quiet Sun structures on the disk are similar to those in Atmospheric Imaging Assembly (AIA) images at 1600 Å and 304 Å, after the latter are smoothed to the ALMA resolution"] [Structures on the solar disk: "A full-disk Band 7 image is shown in Fig. 1; AIA images in the 1700 Å and 304 Å bands, as well as a GONG H$\alpha$ image are also displayed for comparison."]
  - parameter: Central region size = 500'' by 500''; smoothed to 21'' ALMA resolution [Structures on the solar disk: "Enlarged images of a 500$''$ by 500$''$ region at the center of the disk are shown in Fig. 2, where the negative of the H$\alpha$ image is given."]
- step 3: Extract, correct, and frequency-remap center-to-limb brightness temperature variations
  - method: Measure T_b(mu) across the disk in Bands 3, 6, and 7, apply diffuse light correction as in Paper I, exclude limb regions within 70'', 35'', and 30'' in Bands 3, 6, and 7 respectively, and remap all measurements to a common reference freque… [Center-to-limb variation and modeling: "The measurements were corrected for diffuse light as described in Paper I."] [Center-to-limb variation and modeling: "We avoided measurements close to the limb, going up to 70, 35, and 30$''$ from the limb in Bands 3, 6, and 7, respectively, which is more than the corresponding beam sizes."]
  - parameter: f_ref = 100 GHz; limb exclusion cutoffs = 70'' (Band 3), 35'' (Band 6), 30'' (Band 7) [abstract: "we combined them to a unique curve of $T_b(\log\mu_{100})$, where $\mu_{100}$ is the cosine of the heliocentric angle reduced to 100 GHz."] [Center-to-limb variation and modeling: "We avoided measurements close to the limb, going up to 70, 35, and 30$''$ from the limb in Bands 3, 6, and 7, respectively, which is more than the corresponding beam sizes."]
  - assumption: Both free-free and H^- absorption coefficients are proportional to f^-2 [Center-to-limb variation and modeling: "taking advantage of the fact that both the free-free (cite: 1970resp.book.....Z) and the H$^-$ (cite: 1974ApJ...187..179S) absorption coefficients are proportional to $f^{-2}$."]
  - validation: Comparison with December 2015 commissioning observations [Center-to-limb variation and modeling: "The results are shown in the top panel of Fig. 3, where we have included, for comparison, data from the commissioning observations of December 2015, which were also used in Papers I and II."]
- step 4: Cross-normalize datasets and fit combined CLV curve to derive disk-center brightness temperatures
  - method: Normalize Band 6 and Band 7 datasets (and current Band 3 dataset) relative to December 2015 Band 3 commissioning data (normalization factor fixed to 1) via a simultaneous least-squares fit of all sets to a third-degree polynomial in ln(mu)… [Center-to-limb variation and modeling: "Working as in Paper II, we normalized Band 6 and 7 measurements through a least-squares fit of all sets to the same polynomial function of $T_b(\log \mu)$."] [Center-to-limb variation and modeling: "Considering that Band 3 is more reliable (cite: 2017SoPh..292...88W), we set the normalization factor of the commissioning data for that at unity, leaving the factors for the other data sets to be determined by the fit."]
  - parameter: Band 3 commissioning normalization factor = 1; polynomial degree = 3 [Center-to-limb variation and modeling: "Considering that Band 3 is more reliable (cite: 2017SoPh..292...88W), we set the normalization factor of the commissioning data for that at unity, leaving the factors for the other data sets to be determined by the fit."]
  - assumption: Absolute calibration of the December 2015 Band 3 commissioning observations is accurate [abstract: "Assuming that the absolute calibration of the Band 3 commissioning observations is accurate, we deduced a brightness temperature at the center of the disk of 6085 K for Band 7"]
  - fitting: Least-squares fit to third-degree polynomial in ln(mu) [Center-to-limb variation and modeling: "Working as in Paper II, we normalized Band 6 and 7 measurements through a least-squares fit of all sets to the same polynomial function of $T_b(\log \mu)$."]
  - validation: Comparison of rms deviation of third-degree fit (~13 K) against linear (26.6 K) and quadratic (16.0 K) fits, and comparison of derived T_b with Paper II [Center-to-limb variation and modeling: "The root mean square (rms) deviation was about 13 K, whereas linear and quadratic fits gave rms deviations of 26.6 K and 16.0 K, respectively."]
- step 5: Invert radiative transfer equation to derive electron temperature profile T_e(tau_100)
  - method: Analytically invert the radiative transfer formal solution for a third-degree polynomial in ln(tau), T_e(tau) = a_0 + a_1 ln(tau) + a_2 ln^2(tau) + a_3 ln^3(tau), using Euler constant and Riemann zeta integrals to obtain coefficients a_0, … [Appendix: Inversion of the transfer equ…: "where $\gamma$ is the Euler constant and $\zeta$ is the Riemann zeta function."] [Center-to-limb variation and modeling: "The resulting $T_e( au)$ is plotted in the bottom panel of Fig. 3, together with the corresponding curves from models A (cell interior), C (average quiet Sun), and F (network) of (cite: 1993ApJ...406..319F) and our results from Paper II."]
  - parameter: C_1 = -0.5772157, C_2 = 1.978112, C_3 = -5.444874 [Appendix: Inversion of the transfer equ…: "\int_0^\infty \ln x\,e^{-x}\,dx&=&-\gamma=-0.5772157=C_1"]
  - assumption: Thermal bremsstrahlung and H^- emission in local thermodynamic equilibrium; plane-parallel formal solution of radiative transfer equation [Introduction: "Such observations provide simpler diagnostics because the quiet Sun emission originates from thermal bremsstrahlung in local thermodynamic equilibrium (cite: 2016SSRv..200....1W)."] [Inversion of the transfer equation for …: "and substituting into the formal solution of the transfer equation, $$egin{equation} T_b(\mu)=\int_0^\infty T_e( au)\, e^{- au/\mu}\,d au/\mu \label{transf} , \end{equation}$$"]
  - fitting: Analytical algebraic inversion from fitted polynomial coefficients A_i to a_i [Appendix: Inversion of the transfer equ…: "we obtain the coefficients of $T_e(\tau)$:"]
  - validation: Comparison with Paper II curve and FAL93 models A, C, and F [Center-to-limb variation and modeling: "The resulting $T_e( au)$ is plotted in the bottom panel of Fig. 3, together with the corresponding curves from models A (cell interior), C (average quiet Sun), and F (network) of (cite: 1993ApJ...406..319F) and our results from Paper II."]
- result: Brightness temperature enhancement of small active/plage regions over surroundings in Band 7 = 900 ± not stated K [Structures on the solar disk: "As expected, these appear brighter than their surroundings in Band 7 by about 900 K."]
- result: RMS deviation of third-degree polynomial CLV fit = 13 ± not stated K [Center-to-limb variation and modeling: "The root mean square (rms) deviation was about 13 K, whereas linear and quadratic fits gave rms deviations of 26.6 K and 16.0 K, respectively."]
- result: RMS deviation of linear CLV fit = 26.6 ± not stated K [Center-to-limb variation and modeling: "The root mean square (rms) deviation was about 13 K, whereas linear and quadratic fits gave rms deviations of 26.6 K and 16.0 K, respectively."]
- result: RMS deviation of quadratic CLV fit = 16.0 ± not stated K [Center-to-limb variation and modeling: "The root mean square (rms) deviation was about 13 K, whereas linear and quadratic fits gave rms deviations of 26.6 K and 16.0 K, respectively."]
- result: Disk center brightness temperature (Band 3 Average, 100 GHz) = 7347 ± not stated K [Table 1: "| **Band 3 Aver** | **100** | **7300** | **7324** | **0.3** | **7347** | ** 0.6** |"]
- result: Disk center brightness temperature (Band 3 SW1, 93 GHz) = 7431 ± not stated K [Table 1: "| Band 3 SW1 | 93 | | 7406 | | 7431 | |"]
- result: Disk center brightness temperature (Band 3 SW2, 95 GHz) = 7406 ± not stated K [Table 1: "| Band 3 SW2 | 95 | | 7382 | | 7406 | |"]
- result: Disk center brightness temperature (Band 3 SW3, 105 GHz) = 7289 ± not stated K [Table 1: "| Band 3 SW3 | 105 | | 7269 | | 7289 | |"]
- result: Disk center brightness temperature (Band 3 SW4, 107 GHz) = 7266 ± not stated K [Table 1: "| Band 3 SW4 | 107 | | 7248 | | 7266 | |"]
- result: Disk center brightness temperature estimate (Band 5 Average, 198 GHz) = 6532 ± not stated K [Table 1: "| **Band 5 Aver** | **198** | **–** | **–** | | **6532** | |"]
- result: Disk center brightness temperature estimate (Band 5 SW1, 191 GHz) = 6571 ± not stated K [Table 1: "| Band 5 SW1 | 191 | | – | | 6571 | |"]
- result: Disk center brightness temperature estimate (Band 5 SW2, 193 GHz) = 6560 ± not stated K [Table 1: "| Band 5 SW2 | 193 | | – | | 6560 | |"]
- result: Disk center brightness temperature estimate (Band 5 SW3, 203 GHz) = 6506 ± not stated K [Table 1: "| Band 5 SW3 | 203 | | – | | 6506 | |"]
- result: Disk center brightness temperature estimate (Band 5 SW4, 205 GHz) = 6495 ± not stated K [Table 1: "| Band 5 SW4 | 205 | | – | | 6495 | |"]
- result: Disk center brightness temperature (Band 6 Average, 239 GHz) = 6347 ± not stated K [Table 1: "| **Band 6 Aver** | **239** | **5900** | **6343** | **7.5** | **6347** | ** 7.6** |"]
- result: Disk center brightness temperature (Band 6 SW1, 230 GHz) = 6382 ± not stated K [Table 1: "| Band 6 SW1 | 230 | | 6386 | | 6382 | |"]
- result: Disk center brightness temperature (Band 6 SW2, 232 GHz) = 6374 ± not stated K [Table 1: "| Band 6 SW2 | 232 | | 6376 | | 6374 | |"]
- result: Disk center brightness temperature (Band 6 SW3, 246 GHz) = 6322 ± not stated K [Table 1: "| Band 6 SW3 | 246 | | 6310 | | 6322 | |"]
- result: Disk center brightness temperature (Band 6 SW4, 248 GHz) = 6315 ± not stated K [Table 1: "| Band 6 SW4 | 248 | | 6301 | | 6315 | |"]
- result: Disk center brightness temperature (Band 7 Average, 347 GHz) = 6085 ± not stated K [abstract: "Assuming that the absolute calibration of the Band 3 commissioning observations is accurate, we deduced a brightness temperature at the center of the disk of 6085 K for Band 7, instead of the value of 5500 K"]
- result: Percentage difference of Band 7 disk center T_b above extrapolated recommended value = 10.6 ± not stated % [Center-to-limb variation and modeling: "while the disk temperature for Band 7 is 6085 K, or 10.6% above the extrapolated recommended value of 5500 K."]
- result: Disk center brightness temperature (Band 7 SW1, 341 GHz) = 6095 ± not stated K [Table 1: "| Band 7 SW1 | 341 | | – | | 6095 | |"]
- result: Disk center brightness temperature (Band 7 SW2, 343 GHz) = 6092 ± not stated K [Table 1: "| Band 7 SW2 | 343 | | – | | 6092 | |"]
- result: Disk center brightness temperature (Band 7 SW3, 351 GHz) = 6077 ± not stated K [Table 1: "| Band 7 SW3 | 351 | | – | | 6077 | |"]
- result: Disk center brightness temperature (Band 7 SW4, 353 GHz) = 6074 ± not stated K [Table 1: "| Band 7 SW4 | 353 | | – | | 6074 | |"]
- result: Atmospheric inversion parameter a_0 = 6964 ± not stated K [Table 2: "| $a_0$ | 6999 | 6964 |"]
- result: Atmospheric inversion parameter a_1 = -680 ± not stated K [Table 2: "| $a_1$ | $-563$ | $-680$ |"]
- result: Atmospheric inversion parameter a_2 = 30 ± not stated K [Table 2: "| $a_2$ | – | 30 |"]
- result: Atmospheric inversion parameter a_3 = 19 ± not stated K [Table 2: "| $a_3$ | – | 19 |"]
- limitation (authors): Low spatial resolution (21 arcsec) of the single-dish Band 7 images prevents a detailed study of the association between ALMA and H-alpha features. [abstract: "In spite of the low spatial resolution (21$''$), several interesting results were obtained."]
- limitation (authors): Absolute calibration jumps exist between datasets, and cross-normalization cannot replace true absolute calibration (e.g., using the Moon). [Center-to-limb variation and modeling: "As noted in Paper II, there is a jump in $T_b$ between the commissioning and the current Band 6 data set, attributed to absolute calibration issues, and so is the case with Band 7."]
- not stated (card): Exact CASA version used to process the Total Power data and run sdgaincal; Specific parameters passed to CASA task sdgaincal (e.g., radius, calmode); Quantitative parameters and kernel used for the diffuse light correction inherited from Paper I; Best-fit polynomial coefficients A_0, A_1, A_2, A_3 of T_b(mu) and the derived dataset normalization factors; Exact single-dish beam FWHMs for Bands 3 a…

### 2019ApJ...875..163R: First Spectral Analysis of a Solar Plasma Eruption Using ALMA (2019; sun; archival_reuse)
- question: Can the logarithmic millimetre continuum gradient across ALMA Band 3 sub-bands be used to estimate optical thickness (and hence temperature/emission measure) of a solar plasmoid and an X-ray bright point enhancement?
- step 1: Calibrate and image
  - method: Calibrate with SV reference scripts; synthesise images at 2 s cadence for full band and each of four spectral windows [3 Observation: "synthesise each image using the full bandwidth of Band 3 at a cadence of 2 s"]
  - validation: Replicated Shimojo et al. noise level of 11 K [3.1 Noise level calculation: "We replicate the 11 K noise level value presented by (cite: 2017ApJ...841L...5S)"]
- step 2: Brightness temperature enhancement and errors
  - method: Mean Tb in two boxes per time step; enhancement = enhanced minus background phase (N=29 steps each); noise from XX-YY, plus 5% flux-scale error [3.1 Noise level calculation: "As the number of timesteps in both the background and enhanced phases were kept equal at $N=29$"]
  - assumption: Flux scale error normal with 3σ = 5% [3.2 Flux scale accuracy: "we have assumed a normally-distributed random uncertainty where the mean is zero and $3\sigma$ is equal to the 5% limit."]
- step 3: Fit spectral gradient
  - method: Bayesian linear regression of log E vs log nu with emcee [4.1: "we sampled it using a python implementation of the affine-invariant ensemble sampler for Markov-chain Monte-Carlo (MCMC) method (EMCEE)"]
  - software: emcee
  - parameter: 100 chains, 1000 steps including tuning [4.1: "We sampled using 100 chains, each with 1000 steps including tuning."]
  - fitting: Normal likelihood in log space; uniform non-informative priors on gradient and intercept; 90% percentile intervals [4.1: "The prior distributions for the two desired fitting parameters, i.e spectral gradient and y-intercept, have been set as non-informative uniform distributions."]
- step 4: Derive optical thickness and plasma parameters
  - method: Intersect gradient confidence interval with diagnostic curve using alpha (1.04–1.09) and beta bounds; then derive T, EM, density [4.1: "Through plotting this curve and the confidence intervals of the fitted enhancement gradient it is possible to estimate the optical thickness/optical thickness regime"]
  - assumption: Isothermal plasma; C7 model background; purely hydrogen plasma; background Tb 7300±100 K [4.1: "We assume a purely hydrogen plasma and a solely thermal bremsstrahlung emission mechanism."]
  - validation: Single-dish images checked to support the assumed background value [4.1: "This assumption was checked by viewing the ALMA single-dish images during the observation"]
- result: Optical thickness, box 1 (90%) = 0.02–2.78 ± 90% confidence dimensionless [4.1: "0.02 $\leq \tau_{90\%\,\mathrm{confidence}} \leq$ 2.78"]
- result: Optical thickness, box 2 (90%) = 0.11–2.78 ± 90% confidence dimensionless [4.2 Box 2: Moving enhancement from plas…: "the optical thickness of the plasmoid ranges from 0.11 – 2.78"]
- result: Spectral gradient box 1 = -1.6 to -0.4 ± 90% interval dimensionless [4.1: "the spectral gradient ranges between -1.6 and -0.4"]
- result: Electron temperature box 1 = 7370–15300 ± not stated K [4.1: "between $\approx$ 7370 – 15300 K"]
- result: Electron temperature box 2 = 7440–9660 ± not stated K [4.2 Box 2: Moving enhancement from plas…: "electron temperature of the plasmoid of $\sim$7440 – 9660 K"]
- result: Full-band enhancement box 2 = 221 ± 9.4 K [Table: "| Full Band – 100 GHz | 159 $\pm$ 6.8 | 221 $\pm$ 9.4 |"]
- result: Plasmoid electron density = 0.7–3e10 ± not stated cm^-3 [4.2 Box 2: Moving enhancement from plas…: "the electron density of the plasma would be in the range $\approx$ 0.7 – 3$\times 10^{10} \,\mathrm{cm^{-3}}$"]
- limitation (authors): Flux scale accuracy is the largest uncertainty; background gradient uncertainty not included; isothermal assumption [5 Discussion: "The largest source of uncertainty in the data is due to the accuracy of the flux scale determination."]
- not stated (card): Exact box 1 and box 2 pixel/coordinate extents; Exact time ranges of background and enhanced phases; Synthesis (tclean) parameters: weighting, cell, imaging software and CASA version; MCMC burn-in and exact prior widths; Exact SV scan/execution block used

### 2020A&A...643A..41D: ALMA observations of transient heating in a solar active region (2020; sun; observational_alma_primary)
- question: Are Ellerman bombs, UV bursts and flaring active-region fibrils visible in the ALMA 3 mm continuum, and what temperatures and formation heights do they have?
- step 1: Image ALMA Band 3 and set absolute temperature scale
  - method: Phase self-calibrated mapping of all four sidebands, primary beam correction, conversion to Tb, offset by single-dish comparison [2.1 Data reduction and calibration: "The maps are converted from flux to brightness temperature."]
  - parameter: cell 0.3 arcsec, beam 1.2 arcsec, +7700 K [2.1 Data reduction and calibration: "This resulted in the addition of 7700 K to the interferometer maps."]
- step 2: Prepare and co-align SDO data
  - method: AIA respiking, SunPy alignment, HMI deconvolution with Enhance, degradation and stray-light correction, rebin to 0.3 arcsec; refine alignment with 304 A structures [2.1 Data reduction and calibration: "the co-alignment was refined by taking advantage of the good correspondence between the mm and EUV bright structures"]
  - software: SolarSoftWare, SunPy, Enhance
  - validation: visual verification with other events [2.1 Data reduction and calibration: "The accuracy was visually verified by the spatial coincidence of other events at different times."]
- step 3: Search for EBs and compare to Band 3
  - method: EBDETECT on AIA 1700 A, 9 sigma events, measure Tb and light-curve correlations [3.1 Ellerman bombs as sub-canopy events: "Here, we only consider $9\sigma$ events"]
  - software: EBDETECT
  - parameter: 9 sigma cores, 5 sigma halos [3.1 Ellerman bombs as sub-canopy events: "the EBs (both the $9\sigma$ cores and $5\sigma$ extended halos) are undetected in the ALMA Band 3 maps."]
  - assumption: 1700 A continuum as EB proxy in absence of H-alpha [3.1 Ellerman bombs as sub-canopy events: "In the absence of H$\alpha$ observations, the 1700 Å continuum can be used as a proxy for EBs"]
- step 4: DEM and thermal energy of EUV kernels
  - method: Regularized DEM inversion with six AIA filters; E_th ~ 3 n_e k T V [3.4 Differential emission measure analy…: "We estimated an order of magnitude for the thermal energy of the EUV kernels (Sect. [3.2](#section:DEM)) as $E_{\rm th}$$\sim$3$n_{\rm e}k_{\rm B}TV,$"]
  - software: DEMREG, CHIANTI v9
  - parameter: 4x4 px averaged intensities; 20% systematic uncertainty [3.4 Differential emission measure analy…: "we include a systematic uncertainty factor of 20% to account for uncertainties in atomic data"]
  - assumption: n_e ~1e9 cm^-3 or sqrt(EM/w) with filling factor 1; depth equals width [3.4 Differential emission measure analy…: "and a filling factor of one is assumed"]
  - fitting: 2D Gaussian FWHM for kernel sizes [3.4 Differential emission measure analy…: "The dimensions are estimated by fitting a 2D Gaussian to the kernels"]
- step 5: Coronal contribution to 3 mm Tb
  - method: Integrate free-free opacity times DEM over 5.5<=logT<=7.3 in Rayleigh-Jeans limit [3.4 Differential emission measure analy…: "We computed the DEM in each pixel of the FOV, and the integration was carried between 5.5$\leq\log T\leq$7.3"]
  - assumption: fully ionized hydrogen plasma [3.4 Differential emission measure analy…: "assuming a fully ionized hydrogen plasma"]
- step 6: Synthetic 3 mm continuum from Bifrost
  - method: NLTE computation with STIC (six-level hydrogen), AIA EUV synthesized with response functions; smear to 1.2 arcsec [4 Synthetic millimeter continuum: "computed in nonlocal thermodynamic equilibrium (NLTE) using the STockholm Inversion Code"]
  - software: Bifrost, STIC
  - validation: compared with observed Tb at kernels [4 Synthetic millimeter continuum: "which agrees with the typical values that we observe at the bright kernels"]
- step 7: Wavelet periodicity analysis
  - method: Wavelet transform without detrending, 99% confidence assuming white noise [7 Millimeter brightness oscillations: "We find evidence for periodicities in the $\approx$50-150 s range in NF1 and NF3 at a 99% confidence level assuming white noise."]
  - software: Python wavelet software (Torrence & Compo)
  - validation: 5x5 px averaging to test jitter [7 Millimeter brightness oscillations: "This has no significant effect on their power spectra."]
- result: Max Tb in NF kernels = 14300 ± not stated K [3.2 The millimeter counterparts of EUV …: "The highest brightness temperature at 3 mm that we observe in the EUV kernels is $T_{\rm b}$$\approx$14 300 K."]
- result: Mean Tb of EBs in Band 3 = 7900 ± ±300 K [3.1 Ellerman bombs as sub-canopy events: "the mean and standard deviation of the brightness of the EBs in Band 3 are $T_{\rm b}$$\sim$7900$(\pm 300)\rm \,K$."]
- result: Number of EBs in ALMA FOV = 20 ± not stated count [3.1 Ellerman bombs as sub-canopy events: "We identified a total of 20 EBs within the ALMA FOV throughout the time span of the observations."]
- result: Thermal energy NF1 (n_e from EM) = 4e25 ± ±1e25 erg [3.4 Differential emission measure analy…: "$E_{\rm th}$$\approx$$4(\pm1)\times10^{25}$ erg (NF1)"]
- result: Coronal contribution to Tb in NF1/NF2/NF3 = 3% / 4% / 7% ± not stated percent [3.4 Differential emission measure analy…: "We find a relative contribution of $\sim$3% in NF1, 4% in NF2, and 7% in NF3."]
- result: Wavelet periodicities = 50-150 ± not stated s [7 Millimeter brightness oscillations: "We find evidence for periodicities in the $\approx$50-150 s range in NF1 and NF3"]
- result: Correlation of simulated Tb(3mm) with gas T at tau=1 = 0.92 ± not stated dimensionless [4 Synthetic millimeter continuum: "are well-correlated ($r=0.92$)"]
- limitation (authors): Simulation magnetic topology not comparable to the observed region; no IRIS data; DEM coronal estimates are lower limits [4 Synthetic millimeter continuum: "Furthermore, the magnetic topology is not directly comparable to the observed active region"]
- not stated (card): ALMA reduction software (CASA?) and version, and imaging task/parameters (weighting, deconvolver); self-calibration solution intervals; how the calibrated single-dish image was obtained; exact co-alignment offsets and angle between ALMA and SDO; EBDETECT parameters beyond threshold, and 1700 A reference level; absolute coordinates of the pointing; time cadence of ALMA maps and how they were made

### 2017ApJ...850...35L: Solar ALMA Observations: Constraining the Chromosphere above Sunspots (2017; sun; archival_reuse)
- question: What do ALMA 1.3 mm and 3 mm brightness temperatures of a sunspot umbra and penumbra imply for semi-empirical sunspot chromosphere models?
- step 1: Define sunspot regions
  - method: Umbral and penumbral boundaries from HMI continuum; inner/outer regions chosen by eye with ellipses [2.2: "red and green ellipses outlining inner and outer umbral boundaries (chosen by eye as described below)"]
  - parameter: 0.65 and 0.90 of surrounding white-light intensity [2.1: "0.65 and 0.90 of the surrounding photospheric white-light intensity"]
  - validation: Compared with magnetogram histograms [2.2: "The inner umbral ellipse, depicted in red, corresponds to the region of the strongest LOS magnetic field"]
- step 2: Measure brightness temperature statistics
  - method: Mean and RMS of pixel brightness temperatures per region, with maps normalized to single-dish QS values [2.1: "we determined typical brightness temperature values as the average of the corresponding set and its root-mean-square (RMS) variation"]
  - assumption: Disk-center QS ~6000 K (1.3 mm) and ~7400 K (3 mm) [2.1: "around 6000 K and 7400 K, at 1.3 mm and 3 mm, respectively"]
- step 3: Compute model mm brightness spectra
  - method: Thermal free-free emission with H-zero and H-minus opacities at 32 wavelengths, 0.1-20 mm; effective formation heights from contribution function centroids [3.3: "We have calculated the expected submm/mm brightness temperatures at 32 selected wavelengths in the range 0.1–20 mm for sunspot umbral models"]
  - assumption: Thermal free-free emission in LTE [3.3: "assuming that the thermal free-free mechanism is responsible for the emission at mm wavelengths"]
- step 4: Compare observations with models
  - method: Compare model-minus-QS difference spectra with observed brightness minus disk-center QS, including earlier observations [3.3: "we plot the difference spectra between the umbral brightness and the QS brightness from the corresponding reference atmospheric models"]
  - fitting: Qualitative comparison, no formal fit [Millimeter-wavelength brightness spectr…: "None of the depicted model curves provides an outstanding fit to the observations at these longer wavelengths. However, the umbral model of (cite: 1994ASIC..433..169S), depicted in Fig. 12 by a red curve, shows the best agreement"]
- result: Inner umbra mean Tb, 1.3 mm = 5330 ± RMS 260 K K [Table 1: "| inner umbra | 5330 | 260 | 7960 | 270 |"]
- result: Inner umbra mean Tb, 3 mm = 7960 ± RMS 270 K K [Table 1: "| inner umbra | 5330 | 260 | 7960 | 270 |"]
- result: Penumbra mean Tb, 1.3 mm = 6990 ± RMS 440 K K [Table 1: "| penumbra | 6990 | 440 | 7380 | 450 |"]
- result: Effective formation height, Severino 1994 model, 1.3 mm / 3 mm = 1090 / 1540 ± not stated km [Table 2: "| Severino et al. 1994 | 1090 | 1540 |"]
- limitation (authors): Side lobes may affect 1.3 mm umbral brightness, which should be treated as an upper limit [4 Discussion and Conclusions: "the derived umbral brightness depression in the single-dish map at 1.3 mm should be considered as an upper limit"]
- not stated (card): Calibration pipeline/CASA version and feathering parameters; Exact ellipse parameters for inner/outer umbra and penumbra; Code for the free-free brightness computation; Image sizes and pixel scales; Details of how model QS references were subtracted per model

### 2022MNRAS.511..877M: Subterahertz radius and limb brightening of the Sun derived from SST and ALMA (2022; sun; archival_reuse)
- question: Determine the average radius and limb brightening of the Sun at 100, 212, 230, and 405 GHz using SST and ALMA single-dish observations, and investigate how antenna beam size and limb brightening level affect radius measurements from the ha…
- step 1: Reconstruct 1-D antenna beam profiles and measure reference HPBWs
  - method: For ALMA, reconstruct 1-D beams by averaging the derivatives of solar equator brightness temperature profiles extracted from all solar maps; for SST, determine 2-D beams via solar scan tomography and average a 2′ band centered on the peak;… [Antenna beam: "ALMA beams were reconstructed using the derivatives of the solar equator $T\!_B$ profiles extracted from all the solar maps, such as those of Fig. [1](#fig:maps)."] [Antenna beam: "The SST 1-D beam profiles were obtained by averaging a band of 2′ width centered on the 2-D profile peak, and are shown in panels *d* and *f* of Fig. [2](#fig:beams) for 212 and 405 GHz, respectively."]
  - parameter: 2′ band width centered on 2-D profile peak for SST 1-D beam extraction [Antenna beam: "The SST 1-D beam profiles were obtained by averaging a band of 2′ width centered on the 2-D profile peak, and are shown in panels *d* and *f* of Fig. [2](#fig:beams) for 212 and 405 GHz, respectively."]
  - assumption: Derivatives of solar equator brightness temperature profiles are good approximations for the ALMA single-dish beam due to high spatial resolution and averaging over many maps. [Antenna beam: "Limb brightening/darkening affects the derivative, however due to the number of maps (the derivatives are superimposed), and to the high spatial resolution of ALMA single-dish, $T\!_B$ profiles derivatives are good approximations for the beam."]
  - fitting: Gaussian function fit to 1-D beam profiles [Antenna beam: "These four 1-D beams at 100, 212, 230, and 415 GHz are shown in panels (a), (b), (d), and (f) of Fig. [2](#fig:beams), respectively, were then fit by a Gaussian function to estimate the real HPBW."]
  - validation: Compared 2-D convolutions of asymmetric SST beams with 1-D convolutions using synthetic TB profiles (LB of 10%, 20%, 30%, 40% and R_synth of 960″ and 970″), finding differences < 0.5″ in radius and < 1% in LB. [Antenna beam: "To analyze that, we performed 2-D convolutions of SST beams and synthetic $T\!_B$ profiles, with $L\!B$ of 10%, 20%, 30% and 40%, and *R*~synth~ of 960″ and 970″."] [Antenna beam: "The radii and $L\!B$ derived from the 2-D convolutions are very close to the 1-D convolutions (differences less than 0.5″ in radius and less than 1% in $L\!B$)."]
- step 2: Extract solar limb coordinates and determine average solar radii from maps
  - method: Correct maps for Earth's orbital eccentricity. Extract limb coordinates per scan using (1) inflection-point method (maxima and minima of numerical derivative) and (2) half-power method (mean TB between background mode outside disk and quie… [Radius Determination: "All solar maps were corrected accordingly for the eccentricity of the Earth’s orbit that makes the apparent solar radii vary over the course of a year."] [Radius Determination: "For the inflection-point method, the limb coordinates (black $\times$ in panels *c* and *d* of Fig. [3](#fig:method)) are defined as the maximum and minimum points of the numerical derivative (red curve in panel *c*, Fig. [3](#fig:method)) of each scan across the solar disk."]
  - parameter: Quiet-Sun region radius: 7.5′ [Radius Determination: "The background level is defined as the most common $T\!_B$ value, or mode, outside the solar disk (solid blue lines in panels *a* and *b* of Fig. [3](#fig:method)) and the $T\!_{qS}$value is the $T\!_B$ median value in the center of the solar disk (green dashed lines in panels *a* and *b* of Fig. [3](#fig:method)) con…"]
  - parameter: Initial limb point distance filter: 815″ (0.85 R_theta) to 1100″ (1.15 R_theta) [Radius Determination: "For the limb point extraction, only those with a center-to-limb distance between 815″ ($0.85$ $R_\theta$) and 1100″ ($1.15$ $R_\theta$) are considered."]
  - parameter: Iterative outlier rejection threshold: |r - R_bar| >= 10″; minimum 10 points (out of usual 34); maximum standard deviation 20″ [Radius Determination: "For each fit, the points with center-to-limb distance, $r$, outside the interval $\bar{R}-\ang{;;10}<r<\bar{R}+\ang{;;10}$ are discarded, and then a new circle fit is performed with the remaining points."] [Radius Determination: "If there are less than 10 points (out of the usual 34) remaining, the entire map is discarded; otherwise, the radius is calculated."]
  - fitting: Iterative least-squares circle fit to extracted limb coordinates [Radius Determination: "These extracted limb points are then fit by a circle (red dashed line in panel *d* of Fig. [3](#fig:method)) using a least-squares method to determine the center coordinates."]
  - validation: Compared measured radii against SSC model predictions and literature values. [Radius Determination: "Also, the inflection-point method radii are closer to the radius measurements reported in the literature (cite: selhor19b; alissan20; menezes21)."]
- step 3: Forward model 1-D solar scan convolutions and estimate limb brightening ranges
  - method: Generate 153 synthetic TB profiles by scaling SSC profiles across LB_synth (0% to 40%, step 5%) and R_synth (960″ to 976″, step 1″). Convolve in 1-D with reconstructed antenna beams. Measure R_conv (both methods) and LB_conv. Select the fo… [Simulated TB profiles: "The synthetic profiles are generated by scaling SSC profiles with limb brightening levels above quiet-Sun level, $L\!B$~synth~, from 0 to 40% (in 5% steps), and radius, *R*~synth~, from 960″ to 976″ (varying by 1″), resulting in a total of 153 $T\!_B$ profiles."] [Simulated TB profiles: "First, for each *R*~synth~, we select the four *R*~conv~ closest to $\bar{R}$. From these four values, only those in the range $\bar{R}$$-\sigma\leq\textit{R}\textsubscript{conv}\leq$$\bar{R}$$+\sigma$ are considered, where $\sigma$ is the standard deviation of $\bar{R}$ for each frequency."]
  - parameter: LB_synth grid: 0% to 40% in 5% steps; R_synth grid: 960″ to 976″ in 1″ steps (153 profiles) [Simulated TB profiles: "The synthetic profiles are generated by scaling SSC profiles with limb brightening levels above quiet-Sun level, $L\!B$~synth~, from 0 to 40% (in 5% steps), and radius, *R*~synth~, from 960″ to 976″ (varying by 1″), resulting in a total of 153 $T\!_B$ profiles."]
  - assumption: Synthetic profiles follow scaled SSC atmospheric model shapes. [Simulated TB profiles: "The synthetic profiles are generated by scaling SSC profiles with limb brightening levels above quiet-Sun level, $L\!B$~synth~, from 0 to 40% (in 5% steps), and radius, *R*~synth~, from 960″ to 976″ (varying by 1″), resulting in a total of 153 $T\!_B$ profiles."]
  - fitting: Two linear fits to the lowest and highest valid LB values as a function of R_synth [Simulated TB profiles: "Moreover, two linear fits are performed: one with the lowest $L\!B$ of each *R*~synth~, and another onefor the highest $L\!B$ of each *R*~synth~, resulting in a $L\!B$ band that ranges from 0% to 40%, as a function of *R*~synth~."]
  - validation: Compared derived LB ranges against previous measurements at 100 and 230 GHz from Selhorst et al. (2019) and convolved SSC model predictions. [Limb brightening estimate: "The $L\!B$ ranges at 100 and 230 GHz agree with the values reported by (cite: selhor19)."]
- result: Gaussian-fitted antenna HPBW at 100 GHz (ALMA) = 1.1 ± not stated arcmin [Antenna beam: "These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively."]
- result: Gaussian-fitted antenna HPBW at 212 GHz (SST) = 3.6 ± not stated arcmin [Antenna beam: "These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively."]
- result: Gaussian-fitted antenna HPBW at 230 GHz (ALMA) = 0.44 ± not stated arcmin [Antenna beam: "These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively."]
- result: Gaussian-fitted antenna HPBW at 405 GHz (SST) = 3.3 ± not stated arcmin [Antenna beam: "These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively."]
- result: Average solar radius at 100 GHz (inflection-point method) = 968 ± 3 arcsec [Abstract: "$\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz)."]
- result: Average solar radius at 212 GHz (inflection-point method) = 963 ± 3 arcsec [Abstract: "$\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz)."]
- result: Average solar radius at 230 GHz (inflection-point method) = 963 ± 2 arcsec [Abstract: "$\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz)."]
- result: Average solar radius at 405 GHz (inflection-point method) = 963 ± 5 arcsec [Abstract: "$\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz)."]
- result: Average solar radius at 100 GHz (half-power method) = 969 ± 2 arcsec [Table 1: "| 100 (ALMA) | $969\pm2$ | $968\pm3$ | 964.2 | 966.4 |"]
- result: Average solar radius at 212 GHz (half-power method) = 967 ± 3 arcsec [Table 1: "| 212 (SST) | $967\pm3$ | $963\pm3$ | 963.6 | 969.0 |"]
- result: Average solar radius at 230 GHz (half-power method) = 964.1 ± 1.7 arcsec [Table 1: "| 230 (ALMA) | $964.1\pm1.7$ | $963\pm2$ | 963.5 | 965.0 |"]
- result: Average solar radius at 405 GHz (half-power method) = 965 ± 5 arcsec [Table 1: "| 405 (SST) | $965\pm5$ | $963\pm5$ | 962.9 | 967.4 |"]
- result: Convolved SSC model solar radius R_ssc^conv at 100 GHz = 966.4 ± not stated arcsec [Table 1: "| 100 (ALMA) | $969\pm2$ | $968\pm3$ | 964.2 | 966.4 |"]
- result: Convolved SSC model solar radius R_ssc^conv at 212 GHz = 969.0 ± not stated arcsec [Table 1: "| 212 (SST) | $967\pm3$ | $963\pm3$ | 963.6 | 969.0 |"]
- result: Convolved SSC model solar radius R_ssc^conv at 230 GHz = 965.0 ± not stated arcsec [Table 1: "| 230 (ALMA) | $964.1\pm1.7$ | $963\pm2$ | 963.5 | 965.0 |"]
- result: Convolved SSC model solar radius R_ssc^conv at 405 GHz = 967.4 ± not stated arcsec [Table 1: "| 405 (SST) | $965\pm5$ | $963\pm5$ | 962.9 | 967.4 |"]
- result: Limb brightening range at 100 GHz = 5.0 - 18.7 ± not stated % [Table 2: "| 100 (ALMA) | | 5.0 - 18.7 | | 33.6 | 8.9 |"]
- result: Limb brightening range at 212 GHz = 1.6 - 12.0 ± not stated % [Table 2: "| 212 (SST) | | 1.6 - 12.0 | | 36.5 | 4.2 |"]
- result: Limb brightening range at 230 GHz = 6.4 - 17.6 ± not stated % [Table 2: "| 230 (ALMA) | | 6.4 - 17.6 | | 37.4 | 16.3 |"]
- result: Limb brightening range at 405 GHz = 3.3 - 17.0 ± not stated % [Table 2: "| 405 (SST) | | 3.3 - 17.0 | | 39.3 | 3.2 |"]
- result: Convolved SSC model limb brightening LB_conv at 100 GHz = 8.9 ± not stated % [Table 2: "| 100 (ALMA) | | 5.0 - 18.7 | | 33.6 | 8.9 |"]
- result: Convolved SSC model limb brightening LB_conv at 212 GHz = 4.2 ± not stated % [Table 2: "| 212 (SST) | | 1.6 - 12.0 | | 36.5 | 4.2 |"]
- result: Convolved SSC model limb brightening LB_conv at 230 GHz = 16.3 ± not stated % [Table 2: "| 230 (ALMA) | | 6.4 - 17.6 | | 37.4 | 16.3 |"]
- result: Convolved SSC model limb brightening LB_conv at 405 GHz = 3.2 ± not stated % [Table 2: "| 405 (SST) | | 3.3 - 17.0 | | 39.3 | 3.2 |"]
- limitation (authors): SST antenna beams are wide (3.6′ and 3.3′), asymmetric, and have high secondary lobes, preventing direct measurement of limb brightening in SST maps and causing asymmetric convolved profiles. [Limb brightening estimate: "In the case of the $T\!_B$ profiles at 212 and 405 GHz, $L\!B$~conv~ is very low and the convolved profiles are asymmetric, which are a result of wider beams with high secondary lobes."]
- limitation (authors): Solar atmospheric models such as SSC represent average approximations and do not always reproduce observations, particularly at millimeter wavelengths where chromospheric features like spicules near the limb cause discrepancies. [Conclusions: "Those discrepancies could be due to the presence of chromospheric features such as spicules located close to the limb or, in the case of SST maps, probably due to the large beam width and deformations. In fact, the model represents average approximations, which do not always reproduce the observations."]
- not stated (card): Exact list of the 125 Band 3 and 71 Band 6 FITS files used from the 17 listed ALMA project codes; Software environment and libraries used for map interpolation, numerical differentiation, circle fitting, and 1-D convolution; Exact functional form or parameterization used to scale the SSC brightness temperature profiles to arbitrary LB_synth and R_synth values; How the 34 scan directions or chords…

### 2019ApJ...881...99M: Solar Chromospheric Temperature Diagnostics: A Joint ALMA-Hα Analysis (2019; sun; observational_alma_primary)
- question: How does the ALMA Band 3 brightness temperature relate to the H-alpha core width as a chromospheric temperature diagnostic, and what physical mechanism explains the relation?
- step 1: Calibrate and self-calibrate ALMA data, feather with full-disk
  - method: Standard CASA calibration, per-interval self-calibration, feathering with single-dish, normalised to 7300 K [2.2 ALMA Observations and Processing: "we apply a self-calibration technique."]
  - software: CASA
- step 2: Measure H-alpha core width
  - method: Width of line profile at half line depth, with depth defined relative to intensity at ±1.0 Å [3.1 IBIS Line Widths: "we measure the separation of the line profile wings at half of the line depth, defined as the difference between the line minimum and the intensity at $\pm$ 1.0 Å from the core position"]
  - fitting: second-order polynomial to line core for minimum [3.1 IBIS Line Widths: "were determined through fitting of a second-order polynomial to the line core"]
  - validation: width errors about 0.005 Å [3.1 IBIS Line Widths: "the errors in the line width were determined to be about 0.005 Å"]
- step 3: Match resolution, align and correlate
  - method: Convolve IBIS with elliptical Gaussian 1.95'' x 2.03'', bin ALMA in time by 8 maps, align, 2D histogram, Pearson r and orthogonal distance regression [3.3 Comparison: "Because of the scatter present in both measurements, we perform an orthogonal distance regression (cite: 1990ApJ...364..104I) to find the best linear fit between the two parameters."]
- step 4: Forward model with RH
  - method: Synthesize H-alpha and 3 mm intensity from SRPM and VAL C models with 4-level hydrogen with PRD for Ly-alpha, Ly-beta, H-alpha; compare to observed correlation [4 Synthetic Spectral Diagnostics with RH: "The RH calculations were done using a 4-level (including continuum) hydrogen atom with the Ly-alpha, Ly-beta and Balmer-alpha transitions treated under partial redistribution (PRD)"]
  - software: RH
  - assumption: 1D hydrostatic semi-empirical atmospheres; mm radiation in Rayleigh-Jeans approximation [4 Synthetic Spectral Diagnostics with RH: "The emergent millimetric radiation was calculated from the synthetic intensity under the Rayleigh-Jeans approximation"]
  - validation: model points compared with observed correlation [4 Synthetic Spectral Diagnostics with RH: "coincide well with the observational data for models B to P"]
- result: Pearson correlation between T_B and H-alpha width = 0.84 ± not stated dimensionless [3.3 Comparison: "with a Pearson correlation coefficient of 0.84"]
- result: ODR fit: H-alpha width vs T = 0.533 + 6.12e-5 T ± not stated Å (T in K) [3.3 Comparison: "The best fit equation is $0.533 + 6.12\times10^{-5}\;T$"]
- result: Mean T_B of FOV = ~8600 ± not stated K [3.2 ALMA Band 3 Intensity: "The overall average $T_B$ for our field is $\sim$ 8600 K"]
- result: Thermal broadening for 6000 to 12000 K = 0.025 ± not stated Å [3.3 Comparison: "would only be expected to increase the line width by 0.025 Å"]
- limitation (authors): 1D hydrostatic models and 1D radiative transfer for H-alpha [4 Synthetic Spectral Diagnostics with RH: "The SRPM models have shortcomings as they are 1D, hydro-static, semi-empirical models"]
- not stated (card): tclean/CLEAN parameters (weighting, robust, cell, niter) for ALMA images; Self-calibration solution intervals and reference model details; Feather parameters and single-dish image scaling details; IBIS calibration and HMI destretch parameters; RH setup details beyond a 4-level hydrogen atom; Alignment procedure between ALMA and IBIS; CASA version

### 2020A&A...638A..62N: Transient brightenings in the quiet Sun detected by ALMA at 3 mm (2020; sun; archival_reuse)
- question: Are there weak transient brightenings in the quiet Sun at 3 mm with ALMA, what are their properties and energies, and can they account for chromospheric heating?
- step 1: Prepare ALMA and AIA data
  - method: Use ALMA snapshot images from Nindos et al. (2018); correct AIA for differential rotation, convolve with ALMA beam, co-align by cross-correlating time-averaged images [Observations and data analysis: "The analysis of the AIA data involved the correction for differential rotation, their convolution with the appropriate ALMA beam, and their co-alignment with the ALMA images"]
- step 2: Detrend and remove p-mode oscillations
  - method: Subtract running average (10 min kernel) over a beam-size macropixel; iterative least-squares harmonic fit and subtraction [Observations and data analysis: "Each light curve was detrended by subtracting the running average of the time profile of a macropixel with size equal to the ALMA beam"]
  - parameter: Maximum error ≲ 5 K, or fewer than five points left [Observations and data analysis: "until an acceptable maximum error ($\lesssim 5$ K) is reached or their number becomes less than five"]
  - fitting: Least-squares harmonic fit (Roerink et al. 2000) with iterative outlier removal [Observations and data analysis: "we applied a least-squares curve fitting procedure (see Roerink et al. 2000)"]
  - validation: Power spectra show p-mode power suppressed by factors of 12 to 17 [Observations and data analysis: "panel (f) indicates that our algorithm can significantly suppress the power of p-mode oscillations (by factors of 12 to 17)"]
- step 3: Detect transient brightenings
  - method: Event if at least 4 consecutive points above 2.5σ, beam-size cluster of adjacent pixels also exceed, and peaks synchronous within ±2 min; AIA requires one point [Observations and data analysis: "the intensity of at least four consecutive points of the light curve was above some user-defined threshold above the average intensity of the curve"]
  - parameter: 2.5σ threshold; 12 pixels (targets 2-6) or 19 pixels (target 7) [Observations and data analysis: "a multiplication factor of 2.5$\sigma$ above average intensity for the light curves"]
  - validation: Threshold and Nmin sensitivity tests (Fig. 2); chance-coincidence estimate for pairing [Statistics and properties of transient …: "the lack of appreciable changes for $N_{min} \leq 12$ justifies our selection of using $N_{min} = 12$ in the subsequent analysis"]
- step 4: Characterize events and pair with AIA
  - method: Measure areas (divided by mu), FWHM durations, network fraction; pair events sharing a pixel with maxima within 15 s; power-law fits in log-log [Statistics and properties of transient …: "we requested that the two events (ALMA and AIA) have at least one common pixel and that their light curves show maxima within 15 s"]
  - parameter: Fit range: widest range with mean error bars <10%; Poisson uncertainties [Statistics and properties of transient …: "The fitting range was determined automatically as the widest range of values that yielded mean error bars less than 10%."]
  - fitting: Linear fit in log axes with Poisson-weighted bins [Statistics and properties of transient …: "In each case, a linear fit in logarithmic axes was performed that gave the power-law function parameters."]
  - validation: Exponential fits compared via chi-squared [Statistics and properties of transient …: "the values of $\chi^2$ for the exponential fits are about 10% smaller than those of the power-law fits"]
- step 5: Derive thermal energies and heating power
  - method: E = 3 N_e k V_ap (T_e,max - T_e,0) with FAL C densities at h1 and h2; power per unit area from total energy, duration and area [Implications for chromospheric heating: "$$\begin{equation} E = 3N_e k V_{ap} (T_{e,max}-T_{e,0}) . \end{equation}$$"]
  - assumption: Optically thick (tau 10-16), so excess Tb equals excess Te; filling factor 1; constant Ne; V_ap = A^(3/2) [Implications for chromospheric heating: "we assume that the volume, $V_{ap}$, can be estimated from the area, $A$, of the event through the equation $V_{ap} = A^{3/2}$"]
  - fitting: Power-law fit to energy distribution above 2.4e24 erg [Implications for chromospheric heating: "For energies higher than 2.4 $\times 10^{24}$ erg"]
  - validation: Repeated with relaxed criteria (2.3σ, 2.1σ, >=1 pixel) [Implications for chromospheric heating: "we estimated the energy content of the ALMA events detected by using both a 2.3$\sigma$ and a 2.1$\sigma$ threshold"]
- result: Number of ALMA events = 184 ± not stated events [Summary and conclusions: "we were able to able to detect 184 events in the six $87\ensuremath{''} \times 87\ensuremath{''}$ targets"]
- result: Mean event duration (3 mm) = 51.1 ± 6.5 s [Table 2: "Mean duration$^{d}$ (s) (all) | $51.1 \pm 6.5$"]
- result: Mean maximum area (3 mm) = 12.3 ± 3.4 Mm^2 [Table 2: "Mean area (Mm$^2$) (all) | $12.3 \pm 3.4$"]
- result: Power-law index of area distribution (3 mm) = 2.73 ± 0.02 dimensionless [Table 2: "Power-law index of distribution (all) | $2.73 \pm 0.02$"]
- result: Power-law index of duration distribution (3 mm) = 2.35 ± 0.02 dimensionless [Table 2: "Power-law index of distribution (all) | $2.35 \pm 0.02$"]
- result: Thermal energy range = 1.5e24 to 9.9e25 ± ±0.1e24 and ±2.0e25 at ends erg [Implications for chromospheric heating: "Our computations (see Table 3) yielded thermal energies ranging from $(1.5 \pm 0.1) \times 10^{24}$ to $(9.9 \pm 2.0) \times 10^{25}$ erg."]
- result: Energy distribution power-law index = 1.67 ± 0.05 dimensionless [Implications for chromospheric heating: "can be fitted with a power-law function with index of $1.67 \pm 0.05$"]
- result: Power per unit area = 1.9e4 ± 0.2e4 erg cm^-2 s^-1 [Table 3: "All events (2.5$\sigma$, pixels $\geq$ beam size) | $15.0 \pm 1.0$ | $1.0 \pm 0.2$ | $1.67 \pm 0.05$ | $1.9 \pm 0.2$"]
- result: Events with 304 Å / 1600 Å counterparts = 18 / 14 ± not stated events [Summary and conclusions: "Only a small fraction of ALMA events had 304 Å and 1600 Å counterparts (18 and 14), respectively."]
- limitation (authors): Energies are upper limits owing to assumptions; poor resolution; optically thick emission samples only a thin layer; residual oscillation power may affect detection of weak events [Implications for chromospheric heating: "imply that the derived energies represent upper limits"]
- not stated (card): CASA version, calibration and imaging parameters (all in Nindos et al. 2018); How sigma of the light curves is defined and computed; Number of adjacent-pixel clusters 'user-defined' beyond beam-size patch details; Harmonic frequencies and fitting details for the oscillation removal; AIA data processing details and alignment specifics; Histogram binning used for the frequency distributions; Softwa…

### 2018A&A...619L...6N: First high-resolution look at the quiet Sun with ALMA at 3mm (2018; sun; observational_alma_primary)
- question: What do high-resolution ALMA 3 mm images show of the quiet Sun chromosphere: network/intranetwork brightness, center-to-limb variation, and spicules?
- step 1: Re-image with self-calibration
  - method: AIPS CLEAN of average and 2 s snapshot images after phase and amplitude self-calibration [Observations and data reduction: "Both our average and snapshot CLEAN images were produced after four rounds of phase self-calibration"]
  - software: AIPS
  - validation: Self-cal removed jitter in snapshot movies [Observations and data reduction: "removed the jitter that was apparent in the movies of snapshot images"]
- step 2: Fix pointing and combine with full-disk image
  - method: Cross-correlate with AIA 1600 Å; feather with processed FD image; primary beam correction [Observations and data reduction: "Therefore the actual pointing was computed by cross-correlation of the ALMA with the AIA 1600 Å images."]
  - software: CASA
  - assumption: FD disk-center Tb scaled to 7250 K [Full-disk images: "we scaled the FD image to match the quiet Sun brightness temperature at disk center reported in Paper I which was 7250 K."]
  - validation: Compared to AIA 1600/304 and IRIS [Results: "There is also a very strong similarity between the ALMA images and the Interface Region Imaging Spectrograph (IRIS) slit-jaw images in three bands"]
- step 3: Measure CLV and network/intranetwork Tb
  - method: Fit Tb(x,y) in 80" FOV with second-degree polynomial; mean above fit = network, below = intranetwork; azimuthal averaging for CLV [Results: "We next fitted $T_b(x,y)$ with a second-degree polynomial to avoid large-scale structure and we considered the average of the values above the fit as representative of the network and the others as representative of the intranetwork."]
  - fitting: second-degree polynomial [Results: "We next fitted $T_b(x,y)$ with a second-degree polynomial to avoid large-scale structure"]
  - validation: Convolved AIA 1600 Å with ALMA beam for Target 5: 3.3% cell increase, 3.7% network drop [Results: "a check using AIA 1600 Å data for Target 5 gave a 3.3% increase of the cell intensity and a 3.7% drop of the network intensity"]
- result: Network excess over average Tb = 305 ± 35 K [Results: "On average, the network is $305 \pm 35$ K above the average $T_b$ and the intranetwork $285 \pm 30$ K below."]
- result: Intranetwork deficit below average Tb = 285 ± 30 K [Results: "On average, the network is $305 \pm 35$ K above the average $T_b$ and the intranetwork $285 \pm 30$ K below."]
- result: Network/cell ratio = 1.08 ± not stated dimensionless [Results: "The network/cell ratio has an average value of 1.08 and decreases slightly towards the limb."]
- result: Spicule Tb at 8.5" above limb = 2560 (1800 above background) ± not stated K [Results: "is most prominent at 8.5$''$, with $T_b=2560$ K, 1800 K above the local background and a width of 4$''$."]
- limitation (authors): Unexplained excess emission beyond the limb up to 1000 K; segregation method not unique [Summary and discussion: "we got emission beyond the limb of up to 1000 K (14% of the disk center value), the origin of which we could not identify."]
- not stated (card): AIPS CLEAN parameters (weighting, robust, cell, image size, iterations); Self-calibration reference model and calibrator details; Details of single-dish processing (Appendix A mostly not given); Exact alignment/cross-correlation procedure for pointing; Polynomial fit and masking details beyond second degree; Azimuthal averaging bin widths

### 2021A&A...652A..92N: ALMA observations of the variability of the quiet Sun at millimeter wavelengths (2021; sun; observational_alma_primary)
- question: Variability of the quiet solar chromosphere at 1.26 mm and 3 mm: spatially resolved p-mode oscillations and transient brightenings
- step 1: Correct pointing and re-image
  - method: Cross-correlate ALMA images with AIA 1600 A; re-compute average and 1 s snapshot CLEAN images with self-calibration; combine with full-disk images [2 Data reduction: "We computed the actual pointing by cross-correlating the ALMA images with the 1600 Å images"]
  - software: CLEAN
  - validation: Offset consistent with general-relativistic radial offset [2 Data reduction: "verified that the position offset we established was consistent with the general-relativistic radial offset"]
- step 2: Power spectra of oscillations
  - method: Per-pixel light curves in blocks (scans 1-4, 5-8; 1-3, 4-6), zero-filled gaps, FT to PSD, averaged over 120x120 pixel FoV and blocks; fit log-normal plus linear in ln(nu) [3 Analysis of Oscillations: "zeroes were added to fill the blanks in the concatenated light curves."]
  - parameter: Fit range lower 2-4 mHz, upper 30-50 mHz chosen by minimum chi^2 [3 Analysis of Oscillations: "The lower and upper frequency employed in our analysis was the one leading to the smallest ${\chi}^{2}$."]
  - fitting: chi^2 minimization of PSD model a0+a1 ln nu+a2 exp(...) [3 Analysis of Oscillations: "for each combination of lower and upper frequency that could be drawn from these intervals, we performed the PSD fitting and calculated the corresponding ${\chi}^{2}$."]
  - validation: Residuals not exceeding ~20%; errors from difference between two blocks; gap correction factors 0.6 (Band 6), 0.7 (Band 3) [3 Analysis of Oscillations: "relatively small absolute residuals (blue solid lines) not exceeding $\approx 20 \%$."]
- step 3: p-mode energy density
  - method: epsilon = rho dv^2 with linear sound wave relation [3 Analysis of Oscillations: "For linear sound waves it is:"]
  - assumption: gamma=5/3; rho from FAL C model [3 Analysis of Oscillations: "$\gamma=5/3$"]
- step 4: Detect transient brightenings
  - method: Remove oscillations, then require >=4 consecutive points above 2.5 sigma, shared by a beam-size patch of 18 pixels, peaking within +-2 min; same on AIA 304/1600 with 1 point [4.1 Detection: "at least four consecutive points in each “corrected” time profile should have intensity exceeding a 2.5$\sigma$ threshold above the mean intensity of the light curve"]
  - validation: Oscillatory power suppressed by factors 11-16; pairing with AIA within 15 s [4.1 Detection: "by factors of 13 to 16 in Band 3, and by factors of 11 to 15 in Band 6"]
- step 5: Event energies and power-law fits
  - method: Thermal free-free energy from excess Tb, FAL C electron density, and volume from area; power-law fits to frequency distributions [4.3 Energy budgets: "we assume that they emit thermal free-free radiation, the electron density and apparent volume do not change significantly in the course of the events, and that the filling factor is unity"]
  - assumption: height equals horizontal size; filling factor unity [4.3 Energy budgets: "assuming their height is equal to their horizontal size"]
  - fitting: Power-law fit with Poisson bin errors [4.2 Properties: "derived from the propagation of errors associated with the histogram bins assuming Poisson statistics"]
- result: p-mode rms, Band 6 original = 175 ± 1 K [Table 2: "1.26 mm Band 6 original | $175\pm~1$"]
- result: p-mode rms, Band 3 original = 152 ± 1 K [Table 2: "3.00 mm Band 3 original | $152\pm1$"]
- result: p-mode energy density at 1.26 mm = 3e-2 ± not stated erg cm^-3 [3 Analysis of Oscillations: "an energy density of $\approx 3 \times {10}^{-2} \mathrm{erg\,{cm}^{-3}}$"]
- result: Number of transient brightenings 1.26 mm / 3 mm = 77 / 115 ± not stated events [abstract: "We detected 77 transient brightenings at 1.26 mm and 115 at 3 mm."]
- result: Energy power-law index 1.26 mm / 3 mm = 1.64 / 1.73 ± 0.04 / 0.06 dimensionless [4.3 Energy budgets: "indices of $1.64 \pm 0.04$ and $1.73 \pm 0.06$ for the 1.26 mm and 3 mm events"]
- result: Noise levels Band 3 / Band 6 = 10.5 / 21.2 ± not stated K [4.2 Properties: "We measured noise levels of 10.5 K and 21.2 K in Bands 3 and 6, respectively."]
- limitation (authors): Observed p-mode rms is a lower limit since resolution is coarse and pixels are correlated [5 Conclusions: "as a lower limit of the actual value"]
- not stated (card): CASA version and imaging parameters (weighting, deconvolver, self-cal solints); Exact pointing offset values from the general-relativity correction; Method to remove oscillations from light curves in detail (in Paper II); Treatment of the 2.5 sigma threshold sigma definition and network/intra-network segmentation thresholds; Energy distribution binning and fit ranges; Whether calibrated visibilit…

### 2019ApJ...871...45S: Solar Polar Brightening and Radius at 100 and 230 GHz Observed by ALMA (2019; sun; archival_reuse)
- question: Is polar brightening present in ALMA single-dish solar maps at 100 and 230 GHz, how large is it, and how does it (and the solar radius) compare with the FAL-C and SSC atmospheric models?
- step 1: Degrade Band 6 maps
  - method: Convolve with Gaussian of 54" from theta100^2=theta230^2+theta_x^2 [Data analysis and results: "determined by the relation $\theta_{100}^2=\theta_{230}^2+\theta_x^2$, assuming that the ALMA observational beams are gaussian."]
- step 2: Quiet Sun temperature
  - method: Mean Tb in 120"x120" disc-centre box [Data analysis and results: "the $T_{qS}$ of each map was assumed to be the mean brightness temperature of a small area at disc center ($120''\times120''$"]
  - validation: Compared with White 2017 and Alissandrakis 2017 [Data analysis and results: "that is in agreement with the values suggested by (cite: White2017) ($7280\pm250$ K)"]
- step 3: Polar brightening
  - method: Average of 61 radial profiles every 1 deg at PA 60-120 (South) and 240-300 (North); peak relative to T_qS [Data analysis and results: "average of 61 radial profiles through the disc center, that were taken every 1$^\circ$ between 60 and 120$^\circ$, and between 240 and 300$^\circ$ position angles"]
- step 4: Solar radius
  - method: Contour at 0.5 T_qS, 1440 points, circle fit [Data analysis and results: "solar limb position determined by `contour` procedure of IDL at the level equal to half of $T_{qS}$; c) 1440 points determined over the curve resulting from step b; d) a circumference fit adjusted to the points."]
  - software: IDL
- step 5: Model limb brightening
  - method: Compute Tb from FAL-C and SSC with H and H- free-free opacities, 2D expansion with R=696 Mm, Gaussian convolution to 25" and 58" [Atmospheric Models: "the brightness temperature was computed every 100 km in the center-to-limb direction, and these results convolved with a Gaussian function with the same resolutions of the observed maps"]
  - assumption: R_sun = 696 Mm (959.64") [Atmospheric Models: "$R_\Sun=696$ Mm or $959''.64$"]
  - validation: Compared model and observed profiles [Atmospheric Models: "the shape of the simulated center-to-limb profiles generally agrees with the observations when the uncertainties are considered."]
- result: Mean polar brightening 100 GHz South = 6.1 ± 2.8 % [Data analysis and results: "$T_B/T_{qS} = 6.1\%\pm 2.8$ and $5.1\%\pm2.7$, respectively for the South and North poles"]
- result: Mean polar brightening 100 GHz North = 5.1 ± 2.7 % [Data analysis and results: "$T_B/T_{qS} = 6.1\%\pm 2.8$ and $5.1\%\pm2.7$, respectively for the South and North poles"]
- result: Mean polar brightening 230 GHz South = 9.2 ± 4.7 % [Data analysis and results: "$T_B/T_{qS} = 9.2\% \pm 4.7$ for the South and $8.7\% \pm 4.4$ for the North pole intensities"]
- result: Mean polar brightening 230 GHz North = 8.7 ± 4.4 % [Data analysis and results: "$T_B/T_{qS} = 9.2\% \pm 4.7$ for the South and $8.7\% \pm 4.4$ for the North pole intensities"]
- result: Solar radius 100 GHz = 965.9 ± 3.2 arcsec [Data analysis and results: "mean values of $965''.9\pm3''.2$ at 100 GHz and $961''.6\pm2''.1$ at 230 GHz"]
- result: Solar radius 230 GHz = 961.6 ± 2.1 arcsec [Data analysis and results: "mean values of $965''.9\pm3''.2$ at 100 GHz and $961''.6\pm2''.1$ at 230 GHz"]
- result: Mean T_qS 100 GHz = 7220 ± 200 K [Data analysis and results: "The average $T_{qS}$ obtained for the six 100 GHz maps was $7220\pm 200$ K"]
- result: Mean T_qS 230 GHz = 6280 ± 200 K [Data analysis and results: "the mean $T_{qS}$ obtained for the three maps was $6280\pm200$ K"]
- result: SSC limb brightening 100 GHz (58" beam) = 10.5 ± not stated % [Atmospheric Models: "The convolution with a $58''$ Gaussian-beam resulted in limb intensities of 10.5% at 100 GHz and 13.3% at 230 GHz."]
- limitation (authors): Sidelobes not removed so polar brightening is a lower limit; poor resolution [Discussion and conclusions: "there should be non-zero sidelobes in a radio telescope beam. Therefore, the derived polar brightening should be a lower limit."]
- not stated (card): Location/format of the SV single-dish maps and calibration details (brightness scale, pointing); Pixel size of maps; How uncertainty on polar brightening was exactly propagated; Details of polynomial fit to radius vs frequency data; Exact radius values from literature used in Fig 6

### 2020A&A...634A..86P: Observations of solar chromospheric oscillations at 3 mm with ALMA (2020; sun; archival_reuse)
- question: Characterize spatially-resolved chromospheric oscillations of the quiet Sun at 3 mm, their center-to-limb variation, and their lag relative to AIA 1600 Å
- step 1: Prepare ALMA and AIA data
  - method: Extract central 80"x80" region of each target; degrade AIA to ALMA resolution; correct differential rotation; co-align by cross-correlating time-averaged images [2 Observations and data analysis: "We extracted a 80$''$$\times$80$''$ region from the original 120$''$ diameter FoV at the center of each target"]
- step 2: Cell/network segregation
  - method: Pixels below (above) a second-degree 2D polynomial fit of the average image are cell (network) [2.1 Cell-Network Segregation: "Pixels with values smaller (larger) than these of the mask are tagged as cell (network) pixels."]
  - validation: visual inspection of masks [2.1 Cell-Network Segregation: "it though leads to satisfactory results as judged by visual inspection of the resulting masks and the actual average images."]
- step 3: Compute PSDs
  - method: Subtract 3rd-degree polynomial from each pixel light curve, Fourier transform, average PSDs over FoV, cell and network [2.2 Calculation of Power Spectral Densi…: "We then calculated the PSDs for every pixel in the FoV and averaged over the entire FoV, as well as the cell and network using the masks described above."]
  - parameter: frequency resolution 1.7 mHz [2 Observations and data analysis: "The frequency resolution of all three data sets, determined by the duration of the time series, is 1.7 mHz."]
  - validation: Compared with subtraction of mean only; polynomial degrees 1-4 tested [3.1 ALMA 3 mm: "experimentation with different degree polynomials (i.e., 1-4) showed that the higher the degree of the polynomial, the smaller the amplitude of the peak around the p-mode domain."]
- step 4: Fit PSD peaks
  - method: Fit linear background plus log-normal peak; derive peak frequency a3 and rms from integral [2.3 Fitting of spatially averaged power…: "The fittings were performed in the frequency range of $\approx$ \[0.008, 13.3\] mHz"]
  - assumption: linear (white-noise) background [2.3 Fitting of spatially averaged power…: "a linear background is deemed as a reasonable choice."]
  - validation: Residuals not exceeding about 15% (ALMA) and 10% (AIA) [3.1 ALMA 3 mm: "with residuals (blue lines) not exceeding $\approx 15 \%$."]
- step 5: Spatial coherence
  - method: Pixel-to-pixel cross-correlation with region growing, clusters with coefficient above 0.7 [2 Observations and data analysis: "we determined clusters of pixels with cross-correlation coefficient above 0.7 and counted the number of pixels per cluster."]
- step 6: ALMA-AIA time lag and formation height difference
  - method: Cross-correlate light curves averaged over 3"x3" macropixels, keep max coefficient >= 0.7, parabolic fit of peak for lag; height from lag times sound speed [3.3 Time-lag analysis: "The optimal temporal lag was calculated from a parabolic fitting of the cross-correlation function around its peak."]
  - assumption: Upward sound waves at about 12 km/s (7000 K) [3.3 Time-lag analysis: "traveling at a speed of $\approx$ 12 $\mathrm{km{s}^{-1}}$ (i.e., corresponding to a temperature of 7000 K)"]
  - validation: Argued lag is real despite differing peak frequencies [3.3 Time-lag analysis: "We may thus safely conclude that the time lag is real."]
- result: ALMA 3 mm oscillation frequency = 4.2 ± 1.7 mHz [abstract: "with frequencies of $4.2 \pm 1.7$ mHz are observed in the quiet Sun"]
- result: ALMA spatially averaged rms = 55-75 ± not stated K [abstract: "yield rms in the range $\approx$ 55-75 K"]
- result: AIA 1600 Å oscillation frequency = 3.7 ± 1.7 mHz [abstract: "For AIA 1600 Å the oscillation frequency is $3.7\pm1.7$ mHz."]
- result: ALMA lag behind AIA 1600 Å = about 100 ± not stated s [abstract: "ALMA 3 mm time-series lag AIA 1600 Å by $\approx$ 100 s"]
- result: Formation height difference = about 1200 ± not stated km [abstract: "a formation-height difference of $\approx$ 1200 km"]
- limitation (authors): 10-min series limit frequency resolution to 1.7 mHz and prevent detecting longer-period oscillations; rms values are upper limits due to detrending [3.1 ALMA 3 mm: "the derived p-mode rms amplitudes from the use of a 3rd degree polynomial fitting of the original light-curves could be seen as upper limits."]
- not stated (card): Calibration and imaging details (CASA version, self-calibration, weighting) only in Nindos et al. 2018; Exact AIA data series/level and download specification; Exact parameters of the AIA-ALMA cross-correlation co-alignment; Fit initial guesses and fitting method for the PSD function; How uncertainties of the lag and error bars are computed

### 2018A&A...613A..17B: First analysis of solar structures in 1.21 mm full-disc ALMA image of the Sun (2018; sun; observational_alma_primary)
- question: Can different solar structures (quiet Sun, active regions, prominences, inversion lines, coronal holes, coronal bright points) be identified in a 1.21 mm full-disc ALMA image, and what are their brightness temperatures relative to the quie…
- step 1: calibrate full-disc map
  - method: Two-load calibration with efficiency factor, data reduction in CASA [2 Measurements and data reduction: "Data reduction was performed using the Common Astronomy Software Applications (CASA) package"]
  - software: CASA
  - parameter: C = 1.16 [2 Measurements and data reduction: "$C = 1.16$ for Band 6"]
- step 2: measure brightness temperatures of regions of interest
  - method: Mean of all pixels in regions of interest; compared with quiet Sun at same radius along the equator east; AR threshold Tb>6900 K, sunspot Tb<6400 K [3 An analysis of the ALMA image and com…: "Brightness temperatures of various structures are calculated as the mean values of all pixels within regions of interest denoted in Fig. 1a."]
  - parameter: QS circle radius 5 pixels at disc centre, 30 pixels elsewhere [3 An analysis of the ALMA image and com…: "At the solar disc center radius of the circle is 5 pixels, while for all other quiet Sun measurements it is 30 pixels."]
  - validation: Selection criteria acknowledged as crude and arbitrary [3 An analysis of the ALMA image and com…: "We note that this selection criteria (for AR1 and SS) are crude and to some extent arbitrary."]
- step 3: identify coronal bright points across wavelengths
  - method: 56 CBPs identified in AIA 19.3 nm marked with boxes and overlaid on He I 1083 nm and ALMA maps; visual comparison [3.5 Coronal bright points: "56 coronal bright points (only point-like structures and small loops) are identified and denoted with blue boxes."]
  - validation: Correspondence of CBPs used to test overlay/orientation precision at about 5 arcsec [3.5 Coronal bright points: "this spatial precision is in the order of 5 arc sec."]
- result: Central quiet Sun brightness temperature = 6040 ± 70 K [Table 1: "| QS | 0 | $6040 \pm 70$ | 78 | $6040 \pm 70$ | 78 | $0$ |"]
- result: Active region AR1 excess over QS = +1010 ± not stated K [Table 1: "$7250 \pm 210$ | 3048 | $+1010$"]
- result: Sunspot deficit = -90 ± not stated K [Table 1: "$6080 \pm 210$ | 136 | $-90$"]
- result: Magnetic inversion line deficit = -170 ± not stated K [4 Summary, discussion and conclusions: "The average brightness temperature of the measured part of the inversion line has a brightness temperature 170 K below the quiet Sun level."]
- result: Prominence (FIL1) deficit = -110 ± not stated K [Table 1: "$6350 \pm 110$ | 154 | $-110$"]
- result: Coronal hole CH1 deficit = -50 ± not stated K [Table 1: "$6540 \pm 130$ | 2804 | $-50$"]
- result: CBPs corresponding to ALMA bright points = 82 ± not stated % [3.5 Coronal bright points: "the great majority (82 %) of all coronal bright points from the EUV image corresponds to the ALMA 1.21 mm bright points"]
- result: CBPs corresponding to He I 1083 nm dark points = 75 ± not stated % [3.5 Coronal bright points: "the great majority (75 %) of all coronal bright points from the EUV image corresponds to He I 1083 nm dark points"]
- result: Limb brightening at 1.21 mm = about 10 ± not stated % [3.1 Quiet Sun: "The amount of this limb brightening is in the order of 10 % in agreement with recent results of (cite: Alissandrakis2017)."]
- limitation (authors): Selection criteria for AR and sunspot are crude and arbitrary; prominence result depends on ~5 arcsec overlay precision [3.3 Prominences on the solar disc: "The reliability of this result depends on the overlying precision (in the order of 5 arc sec)"]
- not stated (card): Calibrated ALMA map file/version and exact CASA version; Coordinates and pixel positions of the regions of interest; Alignment procedure of ALMA map with SDO/Halpha images; Selection of the 56 coronal bright points; How the prominence region was extracted from Halpha

### 2021A&A...656A..68E: The Sun at millimeter wavelengths. III. Impact of the spatial resolution on solar ALMA observations (2021; sun, stellar_physics; theory_or_simulation_compared_to_alma)
- question: How does limited spatial resolution (ALMA array configurations C1-C7, bands 3-10) affect the observability of small-scale dynamics in synthetic solar mm observables from a Bifrost model?
- step 1: Compute synthetic mm brightness temperature maps
  - method: Column-wise LTE radiative transfer with ART on Bifrost; ten frequencies per band averaged; Rayleigh-Jeans conversion to Tb [2.2 Brightness temperature maps at mm w…: "The intensities at mm wavelenghts are obtained by solving the radiative transfer equation column-wise throughout the FOV, using the advanced radiative transfer (ART) code"]
  - software: ART
  - parameter: Ten equidistant frequencies per receiver band, averaged [2.2 Brightness temperature maps at mm w…: "with ten frequencies equidistantly distributed across the spectral range of each receiver band"]
  - assumption: LTE in radiation formation [2.2 Brightness temperature maps at mm w…: "LTE conditions in the formation of the radiation are assumed"]
- step 2: Derive clean beams for configurations C1-C7
  - method: Synthetic observations with simobserve, Sun placed near zenith, beam extracted [2.3 Spatial resolution of ALMA observat…: "As a first approximation, we placed the Sun at an angle close to zenith, which resulted in a slightly eccentric clean beam."]
  - software: CASA
  - parameter: Position angle fixed at 80 degrees [4.3 Eccentricity of clean beams: "the position angle was set to a constant value (of 80 degrees"]
  - assumption: Best case: perfectly sampled observation, no noise or atmosphere [2.3 Spatial resolution of ALMA observat…: "corresponds to a perfectly sampled observation."]
- step 3: Degrade maps and analyze formation heights, Tb distributions, spatial and temporal power
  - method: 2D convolution with clean beams; tau=1 heights; radially averaged FFT power spectra; temporal power with linear detrend and tapered cosine window [3.4 Spatial power distributions: "The power spectra were calculated using radially averaged 2D fast Fourier transform (FFT) on the detrended (linear) brightness temperature maps over the entire FOV"]
  - parameter: Analysis time range t=1000-2000 s for Tb and formation heights; 1550-1750 s for spatial power [3.3 Brightness temperature distributions: "for the time range $t=1000$ – $2000$ s"]
- step 4: Derive ΔTb conversion between degraded and original resolution
  - method: Detect brightening peaks (ΔTb>20 K) at all locations in QS/FS/FP; bin degraded ΔTb; median and ±1σ fitted linearly: ΔTb,org = κ ΔTb,deg + μ [3.5 Degradation of Tb excess signatures…: "All instances of transient brightening events with $\Delta$T$_\mathrm{b} > 20$ K are considered, well below what is reported for observed brightening events so far."]
  - parameter: Bins 0.02-0.2, 0.2-0.4, ..., 1.5-2.0 kK then 0.5 kK width [3.5 Degradation of Tb excess signatures…: "the median and standard deviation values were calculated in the bins at degraded resolution of $\{0.02$ – $0.2$, $0.2$ – $0.4$, $0.4$ – $0.6$"]
  - assumption: Base temperature is hottest of local pre/post minima (conservative) [3.5 Degradation of Tb excess signatures…: "the base temperature of the specific event was defined as the hottest of the local pre- and post-minima."]
  - fitting: Linear fit to binned medians and ±1σ [3.5 Degradation of Tb excess signatures…: "the median values and the plus/minus one standard deviation values can be reasonably well estimated by a linear fit"]
  - validation: Applied to observed band 3 C3 event distributions of Eklund et al. 2020 [4.4 Comparison with observations: "The peak of the resulting distribution of corrected $\Delta T_\mathrm{b}$ is shifted by about $1000$ K from around $650$ K to $1750$ K for the INW events"]
- result: Band 3 QS mean Tb at original resolution = 6346 ± not stated K [3.3 Brightness temperature distributions: "The average value of the $T_\mathrm{b}$ distribution at the original resolution of band 3 is $6346$ K in the QS region"]
- result: Band 6 QS mean Tb at original resolution = 5254 ± not stated K [3.3 Brightness temperature distributions: "$5254$ K in the QS region, $6845$ K in the FS region, and $7417$ K in the FP region"]
- result: Example event ΔTb at original vs C3 resolution (band 3 QS) = over 3200 K original; ~290 K at C3; 240 K at C1 ± not stated K [3.5 Degradation of Tb excess signatures…: "only approximately $290$ K at the resolution of array configuration C3 and $240$ K at C1."]
- result: Corrected original ΔTb for 1.2 kK event, band 3 QS C3 = 2.78 ± +1.51/-1.92 kK [3.5 Degradation of Tb excess signatures…: "a resulting estimated temperature of $T_\mathrm{b,ori}=2.78^{+1.51}_{-1.92}$ kK"]
- result: Mean QS formation height band 10 / 6 / 3 = 0.6 / 0.9 / 1.3 ± not stated Mm [5 Conclusion: "The average formation height increases with wavelength from $0.6$ Mm at band $10$, to $0.9$ Mm at band $6$ to $1.3$ Mm at band $3$ in the simulated QS region."]
- result: Shift of peak of corrected ΔTb distribution of observed INW events = 650 to 1750 ± not stated K [4.4 Comparison with observations: "from around $650$ K to $1750$ K for the INW events and about $400$ K from around $550$ K to $950$ K for the NW events"]
- limitation (authors): Best-case scenario without noise, atmosphere, imaging artifacts; static slightly eccentric beam; correction factors not for one-to-one correction [3.5 Degradation of Tb excess signatures…: "the distributions are not intended for performing one-to-one corrections of specific events in observational data."]
- not stated (card): simobserve parameters (CASA version, hour angle/declination, integration, input model setup) used to derive clean beams; Exact pixel coordinates of the QS, FS and FP regions; Whether the beam kernel is Gaussian or the actual PSF main lobe and how it was fit; Bifrost snapshot file identifiers and ART version/settings; Detection algorithm for peaks and minima beyond the ΔTb>20 K threshold; Fit meth…

### 2018ApJ...863...96Y: ALMA Observations of the Solar Chromosphere on the Polar Limb (2018; sun; observational_alma_primary)
- question: What dynamic structures (jets, blobs) does the solar polar-limb chromosphere show at 100 GHz in ALMA, and how do they correspond to IRIS and AIA features?
- step 1: Calibrate and self-calibrate, make 20 s images
  - method: Solar nominal calibration, two-step phase self-cal, 20 s synthesized images; scale set by 7000 K disk [Observations: "we synthesize each image with an integration time of 20 s after performing a following two-step self-calibration for the antenna’s phases."]
  - assumption: disk brightness 7000 K [Observations: "we assume that the brightness of the solar disk is 7000 K ((cite: avrett2008ApJS..175..229A))."]
- step 2: Relative brightness movie and comparison with IRIS/AIA
  - method: Relative brightness normalized by time-averaged Tb; compare limbs and jets with AIA 171 and IRIS Mg II [Results: "is a temporally averaged brightness over the entire observed period ($\Delta t \approx 1 \ \mathrm{h}$)."]
- step 3: Estimate electron density of blob
  - method: Thermal free-free optical depth with Gaunt factor, tau ≈ Tb/T, EM≈n^2 L [Discussion: "assuming a small optical thickness, 100% filling factor, and $L \approx 1.5\ensuremath{''}$ approximated with the width of the observed blob, and $\tau \approx T_b/T$"]
  - parameter: T = 1e4–4e5 K; Tb=135 K; L≈1.5'' [Discussion: "we obtain $n=(4.6-8.4) \times 10^{9}\ \mathrm{cm}^{-3}$ in the range of $T=(10^4- 4\times 10^5)\ \mathrm{K}$."]
  - assumption: 100% filling factor, small optical thickness [Discussion: "assuming a small optical thickness, 100% filling factor"]
  - validation: Compared with spicule densities from IRIS spectra (Alissandrakis 2018): about an order of magnitude lower [Discussion: "This number is a factor of one order of magnitude smaller than those for spicules obtained through the analysis of the IRIS spectrum data"]
- result: Blob brightness enhancement = 135 ± not stated K [Results: "The brightness enhancement in ALMA images is by 135 K beyond the background"]
- result: Blob proper motion speed = 40 ± not stated km/s [Results: "The blob shows a systematic proper motion at a speed of 40 km/s"]
- result: ALMA jet elongation speed = 30–40 ± not stated km/s [Results: "The speed of the elongation is 30–40 $\mathrm{km}\ \mathrm{s}^{-1}$."]
- result: Blob electron density = (4.6-8.4)e9 ± not stated cm^-3 [Discussion: "we obtain $n=(4.6-8.4) \times 10^{9}\ \mathrm{cm}^{-3}$"]
- limitation (authors): Absolute brightness temperature is hard to determine; S/N poor beyond 10'' off limb; resolution comparable to blob size [Observations: "it is still difficult to determine the absolute brightness temperature in the ALMA data"]
- limitation (authors): Could not confirm jet generation models [Discussion: "Using the available data in the present observations, we could not confirm the proposed model."]
- not stated (card): CASA version and imaging task/parameters (weighting, cell, size, deconvolution); Self-calibration solution intervals and software; Array configuration and baselines; Number of antennas and spectral window setup; IRIS/AIA data processing and alignment with ALMA; Method for measuring jet length and blob proper motion

### 2020A&A...634A..56D: The multi-thermal chromosphere. Inversions of ALMA and IRIS data (2020; sun; observational_alma_primary)
- question: How do temperature and microturbulence stratification in plage and quiet Sun change when ALMA 1.25 mm continuum is added to NLTE inversions of IRIS NUV spectra, and what do cool holes and hot transient brightenings imply?
- step 1: Reduce and align ALMA and IRIS data
  - method: Process ALMA with SoAP2, rescale TP to 5900 K, combine up to 14 ALMA images per IRIS raster, interpolate to common grid, convert Tb to intensity via Planck function [2.1 Data reduction and alignment: "Up to 14 ALMA images were then combined to replicate the IRIS rasters"]
  - software: CASA, SoAP2
- step 2: NLTE inversions of IRIS vs IRIS+ALMA
  - method: STiC regularized Levenberg-Marquardt inversion of Mg II h&k, UV triplet, Ni I, NUV continuum with and without the 1.25 mm point; NLTE hydrogen ionization, free-free mm opacity [3.1 Inversion setup: "which is a regularized Levenberg-Marquardt code for multi-atom NLTE inversions of multiple spectral lines and continua including partial frequency redistribution (PRD) effects"]
  - software: STiC
  - parameter: 19 temperature nodes, 9 vturb nodes, 7 vLOS nodes [3.1 Inversion setup: "We used nine and seven equidistant nodes for $v_{\rm turb}$ and $v_{\rm LOS}$, respectively."]
  - parameter: IRIS instrumental profile Gaussian FWHM 53 mÅ [3.1 Inversion setup: "Gaussian function with a fullwidth at half maximum of 53 mÅ"]
  - assumption: 1D plane-parallel hydrostatic atmosphere; instantaneous NLTE electron densities; cyclotron and synchrotron neglected [6.1 Limitations of the inversions: "STiC code which assumes a 1D, plane-parallel atmosphere in hydrostatic equilibrium"]
  - fitting: chi2 minimization with regularization penalties and ad hoc ALMA weighting [3.1 Inversion setup: "we introduced an *ad hoc* weighting function that ensures that the ALMA data are well fitted"]
  - validation: Monte Carlo tests for overfitting; node-count tests [3.1 Inversion setup: "we ran a set of Monte Carlo simulations as explained in Section"]
- step 3: Response functions and uncertainties
  - method: Numerical temperature response functions; up to 100 Monte Carlo inversions per pixel with random starting atmospheres [3.3 Uncertainties: "we ran sets of up to $n=100$ Monte Carlo simulations per pixel of synthetic IRIS and ALMA data generated from the best-fit models"]
  - software: STiC
  - validation: 68% confidence intervals accurate to <0.5% [3.3 Uncertainties: "accurate (to <0.5%) 68% confidence intervals on the parameters"]
- step 4: Synthesize CO lines in cool holes
  - method: LTE vibration-rotation CO lines near 4.67 micron computed from inverted models [4.3 Chromospheric holes: "We computed a few vibration-rotation CO lines in the commonly observed near-infrared (NIR) range around 4.67 $\rm \mu m$ assuming LTE."]
- step 5: Time evolution of plage subfield
  - method: Invert 18 time steps (~7.5 min) with IRIS and IRIS+ALMA; compare temperature, vturb, vLOS and Mg II wavelength-time diagrams [4.5 Time evolution of the plage region: "We inverted 18 time steps, which is about $\sim7.5$ min (before ALMA pauses for calibration)"]
  - software: STiC
- result: Mean plage Tb at 1.25 mm = 8500 ± not stated K [2.2 Overview: "The average value for the center of the plage region is $\sim8500$ K"]
- result: Median vturb at logtau=-5, IRIS vs IRIS+ALMA (full FoV) = ~4 and ~2 ± not stated km/s [4.4 Microturbulence: full raster: "The median values for the entire FoV are approximately $\sim4\,\rm km\,s^{-1}$ and $\sim2\,\rm km\,s^{-1}$ for the IRIS and IRIS+ALMA inversions respectively"]
- result: Median depth-averaged vturb in plage over time, IRIS vs IRIS+ALMA = 5.5 and 4.8 ± 16-84%: 4.4-6.6 and 3.9-5.9 km/s [4.5 Time evolution of the plage region: "$5.5^{6.6}_{4.4}\rm\,km\,s^{-1}$ and $4.8^{5.9}_{3.9}\rm\,km\,s^{-1}$ in the IRIS and IRIS+ALMA inversions"]
- result: Std of 1.25 mm residuals = 3 ± not stated % [4.2 Temperature maps: full raster: "The standard deviation of the distribution of the residuals at 1.25 mm is 3%."]
- result: Coolest region Tb: mean and minimum = ~4050 and ~3100 ± not stated K [2.2 Overview: "has an average $T_{\rm b}\sim4050$ K and a minimum $T_{\rm b}\sim3100$ K"]
- result: Shock periodicity in Mg II peaks = 3.5-4 ± not stated min [4.5 Time evolution of the plage region: "we find a shock wave signature in the Mg II peak intensities with periods between 3.5 and 4 min"]
- limitation (authors): STiC cannot treat time-dependent hydrogen ionization; 1D plane-parallel assumption; resolution difference between IRIS and ALMA [3.1 Inversion setup: "It is not possible to take these effects into account with STiC or with any other current inversion code to our knowledge."]
- not stated (card): SoAP2 parameters (CLEAN scales, self-cal solints, imaging weights, cell size) and CASA version; Form and values of the ad hoc ALMA weighting function in chi2; Regularization weights alpha and node positions; Initial model atmospheres and data weights sigma; Exact alignment procedure and ALMA PSF treatment; Selection of pixels for Monte Carlo tests

### 2019ApJ...877L..26L: ALMA Detection of Dark Chromospheric Holes in the Quiet Sun (2019; sun; observational_alma_primary)
- question: Does ALMA Band 3 reveal quiet-Sun chromospheric structure, in particular dark/cool regions, that is not seen in UV, visible or magnetogram data?
- step 1: Make ALMA brightness temperature cube
  - method: Per-2s images mapped, self-calibrated, converted to Tb, single-dish offset added [Data Collection and Reduction: "the interferometric images were converted from flux to brightness temperature, and then 7236 K"]
  - software: CASA
  - parameter: 4 spws combined, 1.6'' beam, 0.3'' cells, 1090 images [Data Collection and Reduction: "The final data cube $T_b(x,y,t)$ contains 1090 images."]
- step 2: Co-align multiwavelength data
  - method: Cross-correlation of 45-min averaged images against SDO full-disk reference [Data Collection and Reduction: "all other images were coaligned by cross-correlating images averaged over 45 minutes"]
  - validation: Remaining displacements below 1'' [Data Collection and Reduction: "The remaining image displacements are less than 1$''$"]
- step 3: Compare time-averaged images and histograms for ChAH, network and internetwork regions
  - method: Time-averaged maps and brightness/DN histograms for four equal-size rectangles [Results: "we complemented it with three other regions of the same size in the FOV"]
  - validation: Stability checked via histograms of full time sequence [Results: "To confirm the ChAH’s stability over the duration of the observations"]
- result: Minimum ALMA Band 3 Tb in ChAH = 4370 ± not stated K [Results: "in the ChAH data cube it drops as low as 4370 K, which is about 60% of the quiet-Sun brightness temperature"]
- result: ChAH size = approx. 20'' x 20'' ± not stated arcsec [Results: "With horizontal dimensions of approx. 20$''$ x 20$''$"]
- result: Fraction of frames with Tb<5000 K in ChAH rectangle = 57 ± not stated % [Results: "In 57% of the 2s frames there are regions within the blue ChAH rectangle where the brightness temperature is below 5000 K."]
- result: Time-averaged ChAH Tb range = 5600-7500 ± not stated K [Results: "The brightness temperature ranges from 5600 K to 7500 K in the Band 3 image"]
- not stated (card): CASA version and solar-specific scripts; Imaging task, deconvolver, weighting/robust, and cleaning details; Self-calibration solution intervals; How the 7236 K offset was derived from total-power maps; Co-alignment and mask details for the ROI rectangles

### 2020A&A...644A.152E: The Sun at millimeter wavelengths. II. Small-scale dynamic events in ALMA Band 3 (2020; sun; observational_alma_primary)
- question: How often do small-scale dynamic brightness-temperature events occur in the quiet Sun in ALMA Band 3, what are their properties, and are they consistent with propagating shock waves?
- step 1: Produce Tb time series
  - method: SoAP imaging of all sub-bands combined, feathering, Rayleigh-Jeans conversion to Tb, 2 s cadence, 1200 steps [2.1 Observational data: "The final dataset has a cadence of 2 s, with a total of 1200 time steps."]
  - software: SoAP
  - assumption: Rayleigh-Jeans law and LTE [2.1 Observational data: "under the assumption of the Rayleigh-Jeans law and formation in local thermodynamic equilibrium"]
- step 2: Detect Tb peaks per pixel
  - method: Box-car smoothing over 7 time steps (14 s); find rise-then-fall peaks with amplitude >= 400 K relative to nearest significant local minimum; lifetime = FWHM [2.2 Event definition and selection: "the data is box-car averaged in time with a size of $7$ time steps $(14\,s)$."]
  - parameter: amplitude threshold 400 K [2.2 Event definition and selection: "with an amplitude of at least $400$ K"]
  - validation: conservative criteria to minimize false detections [2.2 Event definition and selection: "the criteria are defined more conservatively for this initial study in order to minimize the number of false detection."]
- step 3: Group pixels into events
  - method: k-means clustering in space and time within 15'' radius; events fully in one time scan; number of clusters via elbow and silhouette methods [2.2 Event definition and selection: "The pixels showing such a temporary rise in brightness temperature are grouped together using the k-means clustering method"]
  - parameter: radius 15'' [2.2 Event definition and selection: "the k-means clustering is only applied to the innermost parts within a radius of $15\ensuremath{''}$."]
  - validation: elbow and silhouette methods [2.2 Event definition and selection: "This method is commonly referred to as the "silhouette method"."]
- step 4: Event statistics and magnetic field comparison
  - method: Size, lifetime, amplitude, base Tb, apparent motion, repetitiveness, HMI LOS field at event location; NW/IN mask [3.3 Statistical study: "the apparent motion is estimated for each event."]
- step 5: Compare with shock simulations
  - method: RADYN 1D piston-driven waves + RH 1.5D, Band 3 mean of four sub-bands; Bifrost+ART degraded with clean beam to derive reduction factor [4.2 Shock wave propagation in a 3D envi…: "The limited spatial resolution of the ALMA band 3 observations thus results in an observable signature of this shock wave example, $\sim 0.18$ times the original $\Delta T_\text{b}$ magnitude."]
  - software: RADYN, RH 1.5D, Bifrost, ART
  - parameter: initial amplitude 0.005-0.05 v0, period 90-210 s [4.1 1D numerical simulations: "Distinct shock waves are excited with an initial amplitude between $0.005 v_0 - 0.05 v_0$ and wave periodicity between $P \approx 90 - 210$ s."]
- result: Number of events = 552 ± not stated dimensionless [3.1 Events with peaks: "A total number of $552$ events are found within the inner parts of the FOV with a radius of $15$$''$"]
- result: Typical Tb excess (50% of events) = ~450-750 ± not stated K [3.3 Statistical study: "with values between $\sim450$ – $750$ K and $\sim 55$ – $125$ s for $50~\%$ of the distribution."]
- result: Event lifetime range (FWHM) = ~43-360 ± not stated s [3.1 Events with peaks: "The lifetimes ranging between $\sim43$ – $360$ s"]
- result: Resolution reduction factor of Tb excess (Bifrost example) = ~0.18 ± not stated dimensionless [4.2 Shock wave propagation in a 3D envi…: "$\sim 0.18$ times the original $\Delta T_\text{b}$ magnitude"]
- result: 1D simulated Tb excess for P=90-210 s = ~2000-4450 ± not stated K [4.1 1D numerical simulations: "values of the brightness temperature excess between $\sim 2000$ K to $4450$ K are seen"]
- result: Mean Tb of area = 7402 ± not stated K [3.3 Statistical study: "$<T_\text{b}>_{x,y,t} = 7402$ K and $7336$ K"]
- limitation (authors): Resolution limits detection; 552 events is a lower limit [4.3 Detection of events: "the $552$ detected dynamical events in this dataset (within $15"$ radius) must therefore be considered to be a lower limit only."]
- not stated (card): SoAP software and version (not public per text), CLEAN parameters, scales, thresholds; Number of clusters k chosen and clustering settings; Definition of 'significant local minima' for peak detection; Co-alignment procedure details; ART code is in prep. and RADYN/RH run details (grids) incomplete; Time-averaged noise/uncertainty of Tb

### 2017ApJ...845L..19B: A First Comparison of Millimeter Continuum and Mg II Ultraviolet Line Emission from the Solar Chromosphere (2017; sun; observational_alma_primary)
- question: How do ALMA 1.25 mm continuum brightness temperature and IRIS Mg II h2v radiation temperature compare in a solar active region, and why do slope and offset differ?
- step 1: Fit IRIS Mg II h profiles
  - method: Nine-parameter double-Gaussian fit; record h2r/h2v peak intensity and wavelength [2.2: "We stored the model fits in separate arrays for the intensities and wavelengths for both the red and blue Mg II h2 peaks."]
  - software: MPFIT
- step 2: Radiometric calibration to T_rad
  - method: Convert DN/s to physical intensity (calibration version 004), then radiation temperature [2.2: "We used the latest calibration values to date for this purpose (i.e. version “004”)."]
- step 3: Co-register and match resolution
  - method: Rotate ALMA map by solar position angle; median-fill failed IRIS pixels; interpolate to 0.4" grid; convolve to ALMA beam; correct offsets [3: "the IRIS raster data were interpolated onto a uniform grid ($0.4"\times 0.4"$ pixels)"]
- step 4: Pixel-by-pixel correlation and linear fits
  - method: Scatter plots of T_B vs T_rad, Pearson coefficient and linear slopes for all pixels and for sunspot/quiet/plage masks [3: "A linear fit to the data yields a slope of $m=0.57$."]
  - fitting: linear fit [Results and Discussion: "The solid line in Fig. 2 shows a linear fit to sunspot pixels (slope $m=0.4$); the dashed line shows the same for “quiet” regions pixels ($m=0.56$)"]
  - validation: Checked calibration, non-simultaneity and coronal contribution (<=2%) [3: "found that $\Delta T_B$(1.25 mm) was no more than 2%"]
- result: Pearson correlation, all pixels = 0.78 ± not stated dimensionless [3: "The Pearson correlation coefficient for all pixels is 0.78."]
- result: Slope, all pixels = 0.57 ± not stated dimensionless [3: "A linear fit to the data yields a slope of $m=0.57$."]
- result: Slopes sunspot/quiet/plage = 0.4 / 0.56 / 0.66 ± not stated dimensionless [abstract: "is 0.4 (sunspot), 0.56 (quiet regions), and 0.66 (plage regions)"]
- result: Mean T_B (1.25 mm) = 7380 (range 5200-8700) ± not stated K [3: "approximately 7380 K and 5200-8700 K, respectively"]
- result: Mean T_rad (Mg II h2v) = 5470 (range 4500-6500) ± not stated K [3: "approximately 5470 K and 4500-6500 K, respectively"]
- limitation (authors): Pixels are correlated on ALMA beam scale and not corrected for [3: "we have not corrected for the fact that pixels are correlated on the scale of ALMA’s resolution"]
- limitation (authors): Datasets not strictly simultaneous [3: "the two data sets not obtained strictly simultaneously"]
- not stated (card): CASA version and calibration/imaging details (deferred to Shimojo/White); Feathering parameters; Pixel masks for sunspot, quiet, plage regions; Alignment offsets and how they were determined; Formula for converting intensity to radiation temperature; Linear fit method (regression type)

### 2020A&A...640A..57A: Modeling the quiet Sun cell and network emission with ALMA (2020; sun; observational_alma_primary)
- question: What are the electron temperature structures of the average quiet Sun, cell interior and network from ALMA Band 3 and 6 images, and how well is the ALMA full-disk absolute calibration known?
- step 1: Normalize FD images
  - method: Least-square fit of all FD sets to a common linear function of log mu at 100 GHz; Band 3 factor set to unity [2.1: "we set the normalization factor for that at unity, leaving the factors for the other data sets to be determined by the fit."]
  - parameter: Reduction to f_ref = 100 GHz via Tb((f/fref)^2 mu, fref)=Tb(mu,f) [2.1: "we had reduced all data to a common reference frequency, $f_{ref}$"]
  - assumption: Commissioning calibration correct; opacity proportional to f^-2 [4 Summary: "assuming that the commissioning calibration was correct"]
  - fitting: Linear fit (quadratic made no difference) [2.1: "Here a linear fit function was used, as a quadratic fit made no difference."]
  - validation: rms deviation about 20 K; feathered/FD comparison factor 1.066 [2.1: "with a root mean square (rms) deviation of about 20 K for the ALMA data"]
- step 2: Invert average QS Te(tau)
  - method: Tb(mu)=a1+a2(ln mu - gamma) giving Te=a1+a2 ln tau [2.1: "T_b(\mu)=a_1+a_2(\ln\mu-\gamma)"]
  - assumption: Plane-parallel atmosphere, valid to mu~0.15 [2.2: "is valid up to $\mu\simeq0.15$ ($\sim10$$''$ from the limb)"]
  - validation: Scatter of single-day inversions gives error estimates [2.2: "which gives $\delta a_1=14$ K and $\delta a_2=15$ K."]
- step 3: Measure cell and network Tb
  - method: Pixel segregation: set 1 equal split; set 2 lowest 8% cell, top 4% network; HR values corrected to match global inversion [3.2 Processing and results: "attributing the lowest 8% of the pixels to cell interior and the top 4% to the network"]
  - fitting: Linear regression of Tb vs log mu100, inverted to Te(tau100) [3.2 Processing and results: "together with the corresponding linear regression lines and FAL93 models"]
- result: a1 (average QS) = 6999 ± 14 K K [Table 2: "| $a_1 (K)$ | 6999 | 6887 |"]
- result: a2 (average QS) = -563 ± 15 K K [Table 2: "| $a_2 (K)$ | $-$563 | $-$608 |"]
- result: Band 6 disk-centre Tb = 6343 ± not stated K [2.2: "the Band 6 average value (6343 K) is 443 K or 7.5% above the recommended (5900 K)"]
- result: Network-cell Te difference at tau100=1 (set 1 / set 2) = 657 / 1554 ± not stated K [Table 7: "| set 1 | 657 | 1.10 |"]
- result: Network/cell Te ratio (set 1 / set 2) = 1.10 / 1.24 ± not stated dimensionless [Table 7: "| set 2 | 1554 | 1.24 |"]
- limitation (authors): Poor statistics of HR data and reliance on commissioning calibration [4 Summary: "In spite of the poor statistics"]
- not stated (card): Imaging, feathering and self-calibration parameters for HR data; CASA version and calibration details; Exact commissioning mosaic dataset identifiers; Details of the inversion procedure from Tb(mu) to Te(tau) beyond log fit; Details of how network/cell pixel selection thresholds were applied across regions; Data of April 12 2018 observations not given a project code

### 2017ApJ...841L..20I: ALMA Discovery of Solar Umbral Brightness Enhancement at λ = 3 mm (2017; sun; observational_alma_primary)
- question: What is the 3 mm brightness structure of a large sunspot umbra at high resolution, and how does it compare with UV/EUV/visible images?
- step 1: Compare 3 mm brightness with multiwavelength images
  - method: Overlay ALMA brightness temperature contours on AIA, HMI and IRIS images and compare [Figure 2: "The overlaid contours indicate the radio brightness temperature at λ=3 mm observed by ALMA"]
- step 2: Histogram regional statistics
  - method: Histograms of brightness temperature, continuum and field in inner and outer umbra regions [Figure 5: "Histograms from the images of (b) brightness temperature at λ=3 mm"]
- result: Umbral brightness enhancement average temperature = about 8000 K ± not stated K [3. Data Analysis and Results: "The average temperature of this “umbral brightness enhancement” is about 8000 K"]
- result: Inner penumbra temperature = 7200 ± not stated K [3. Data Analysis and Results: "The inner penumbra (7200 K) and the outer part of the umbra (7300 K)"]
- result: Plage temperature = about 7800 ± not stated K [3. Data Analysis and Results: "The plage region neighboring the sunspot is about 7800 K at 3 mm."]
- limitation (authors): Single snapshot, limited resolution, cannot distinguish scenarios [4.3 Origin of the umbral brightness enh…: "so that additional millimeter observations"]
- not stated (card): Calibration and imaging software and versions; Feathering parameters; Method for aligning ALMA with IRIS/AIA/HMI; Definition of inner/outer umbra ellipses; Tool used for the analysis

### 2021ApJ...906...83C: ALMA and IRIS Observations of the Solar Chromosphere. II. Structure and Dynamics of Chromospheric Plages (2021; sun, solar_system; observational_alma_primary)
- question: How do ALMA Band 6 brightness temperatures in chromospheric plage relate to IRIS Mg II, C II and Si IV diagnostics, where does the 1.25 mm emission form, and does it show shock heating?
- step 1: Define plage and periphery masks
  - method: Magnetogram threshold ±0.1 kG as guide; pore removed with Band6 Tb≥6,500 K mask [3: "we employ the *ALMA*/Band6 maps segmented at a low threshold $T_b\ge6,500$ K."]
  - validation: Results change only 3-5% with thresholded magnetogram masks [4.1.1.1: "if we impose thresholded magnetogram masks for the plage areas the results do not change beyond 3-5%"]
- step 2: Build matched IRIS rasters and radiative temperatures
  - method: Match Band6 2 s frames to slit times within ±1 s; Mg II Trad via Planck inversion; Si IV and C II integrated; hot pixels >10 DN/s interpolated [4.1.1: "we match our *ALMA*/Band6 2 s-cadence series by composing “rasters” that match the time of each slit sampling position to within $\pm$1 s."]
  - fitting: Double Gaussian for Mg II features [4.1.1: "we perform double gaussian fitting (cite: Schmit_etal_2015) for the Mg II raster data"]
  - validation: Mid-raster frame matching changes results ~1% [4.1.1: "but found no significant change in our results (i.e., of order $\sim$ 1%)"]
- step 3: Correlate observables
  - method: Pearson C.C. in plage, periphery and full FOV (time-averaged), and per correlation bin per time step [4.1.1.1: "We proceed by calculating the linear correlation coefficent (Pearson r, hereafter “C.C.”) between each of the four observables"]
  - validation: Same analysis on Bifrost synthetic observables [4.1.2: "we perform this analysis on the synthetic observables produced from our model."]
- step 4: Explain formation heights with Bifrost
  - method: Inspect emissivity and tau=1 heights of synthetic Si IV, Mg II k, Band6 in spicule and fibril regions [4.1.3: "we explore the time evolution in the emission and formation height of the synthetic observables for the region with spicules and plage"]
  - assumption: Vertical LOS, simulation degraded to IRIS and Band6 resolution [2.2: "The viewing geometry chosen was for an “observer” looking from above down on the domain"]
- step 5: Shock heating in plage
  - method: Autocorrelation map to select 1"×1" region; λ-t plots with unsharp mask and time derivatives; overplot ALMA Tb [4.2: "we filter them with an unsharp-mask image processing operation with a 5-pixel radius."]
- result: C.C. ALMA Tb vs Mg II k Trad, plage = 0.56 ± not stated dimensionless [5: "While the C.C. for *ALMA*/Band6 $T_b$ with Mg II k $T_{\rm rad}$ is 0.56 for plage and 0.57 for the periphery"]
- result: C.C. ALMA vs Mg II k, full FOV = 0.74 ± not stated dimensionless [5: "the calculation for the full FOV increases the value dramatically, to a C.C. of 0.74"]
- result: C.C. with Mg II h2v/h2r average Trad method = 0.52 ± not stated dimensionless [5: "we found that the C.C. in that case was even lower, i.e., C.C. = 0.52"]
- result: Plage pixels = 650 (578 after pore exclusion); periphery 480 ± not stated pixels [5: "The total number of pixels in the plage mask is 650 which finally becomes 578 pixels after excluding the pore region"]
- result: Baseline Tb above plage = ≈7,500 K (max 8,500 K) ± not stated K [4.2: "The jumps in T$_b$ are of order 10%-20% increase from a baseline value of $\approx$ 7,500 K (maximum jump at 8,500 K)."]
- result: Shock decay time = 60-120 ± not stated s [4.2: "The observed decay time down to the baseline value is of order $\approx$60-120 s."]
- limitation (authors): Model should not be taken as perfect; modeled Band6 Tb is 2,000 K lower than observed [6 Summary & Conclusions: "the distribution of modeled brightness temperatures of *ALMA*/Band6 is lower by 2,000 K as compared to the observations."]
- not stated (card): ALMA calibration, CASA version, imaging parameters (all in Paper I); IRIS/ALMA co-alignment procedure; Bifrost output snapshots; Fitting details for double Gaussian; Autocorrelation lifetime definition; Pore mask construction details

### 2020A&A...635A..71W: The Sun at millimeter wavelengths. I. Introduction to ALMA Band 3 observations (2020; sun; observational_alma_primary)
- question: What is the diagnostic potential of ALMA Band 3 brightness temperatures for a Quiet Sun region, and how do they compare with simultaneous SDO observations?
- step 1: Reconstruct 2 s snapshot images
  - method: Multi-scale multi-frequency CLEAN per snapshot using all four sub-bands to produce full-band maps [2.2 Interferometric data processing: "Here, all interferometric information from the four sub-bands is used to produce one continuum image (referred to as “full-band map”) for each time step"]
  - software: SoAP, CASA
- step 2: Primary beam correction, TP feathering, alignment and derotation
  - method: Divide by Gaussian beam, feather with TP map, co-align with SDO, correct solar rotation by cross-correlating with first frame [2.2 Interferometric data processing: "The apparent drift of snapshot images in time due to solar rotation was then corrected by cross-correlating consecutive 2 s images with a reference image"]
  - software: SoAP, CASA
  - parameter: TP SB2 mean in central 240'' radius scaled from 7454 K to 7300 K [2.5 Absolute temperatures based on Tota…: "The average value in the original SB2 map is 7454 K and thus only 154 K higher than the recommended value"]
- step 3: Brightness temperature statistics, network/internetwork
  - method: Mask built from time-averaged AIA 1700/1600, saturated HMI magnetograms and ALMA maps; statistics in inner r<=22'' [2.7 Data mask: "a data mask is constructed based on a combination of time-averaged maps in SDO/AIA 1700 and SDO/AIA 1600 and saturated SDO/HMI magnetograms and the band-averaged ALMA maps."]
- step 4: Cross-correlate ALMA with SDO channels
  - method: Convolve SDO maps with representative ALMA beam and compute cross-correlation per time step, excluding the compact-loop region [3.4 Correlation of ALMA and SDO maps: "For each time step, the SDO maps are first convolved with the representative ALMA Band 3 beam before calculating the cross-correlation"]
- step 5: Test angular resolution effect with simulation
  - method: Convolve Bifrost/ART band-averaged maps with ALMA, BIMA beams (also rotated 90 deg) and compare statistics [4.2 Dependence on angular resolution: "additional degraded maps are calculated with the beam rotated by $90\,\deg$."]
  - software: ART, Bifrost
  - validation: Compared simulated rms with observed [4.2 Dependence on angular resolution: "The simulated standard deviation, however, is roughly a factor two higher than the corresponding observational value."]
- result: Mean Tb, inner region (all) = 7400 ± 453 (rms) K [3.2 Brightness temperature distribution: "The corresponding average and standard deviation is $(7500 \pm 514)$ K for the whole FOV and $(7400 \pm 453)$ K for the inner region."]
- result: Mean Tb network / internetwork = 7588 / 7228 ± not stated K [Table 1: "| avg. | 7400 | 7588 | 7228 |"]
- result: Histogram FWHM network / internetwork = 782 / 702 ± not stated K [Table 1: "| histogram, FWHM | 752 | 782 | 702 |"]
- result: Cross-correlation ALMA with AIA 304 and 131 = 0.38 ± not stated dimensionless [3.4 Correlation of ALMA and SDO maps: "both reaching a moderate correlation of $\langle\mathcal{C}\rangle_t=0.38$"]
- result: Cross-correlation ALMA with AIA 171 = 0.33 ± not stated dimensionless [3.4 Correlation of ALMA and SDO maps: "followed by SDO/AIA 17.1 nm with $\langle\mathcal{C}\rangle_t = 0.33$."]
- result: Simulated Tb rms with representative beam = 1033 (original 1549) ± not stated K [4.2 Dependence on angular resolution: "Using the representative beam from the ALMA observations presented here results in a standard deviation of 1033 K"]
- result: Compact loop top Tb range = 8500 to 9650 ± not stated K [3.5 Compact loops: "ALMA maps the hot loop tops at brightness temperatures between 8500 K and a maximum of 9650 K."]
- limitation (authors): Absolute Tb scale from TP remains uncertain [abstract: "The absolute brightness temperature scale as set by Total Power measurements remains less certain and must be improved in the future."]
- not stated (card): SoAP code and its parameters (CLEAN scales, niter, weighting, cell/image size, masks); CASA version; Data selection/flagging and reference calibrators; Method details for SDO-ALMA co-alignment; Thresholds used for the network/internetwork mask; ART code settings and Bifrost snapshot identity

### 2020ApJ...888L..28S: Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA (2020; sun; observational_alma_primary)
- question: What are the temperature and density of a spicule seen at 100 GHz with ALMA, and how does it relate to spicules seen in IRIS Mg II and AIA 304 A?
- step 1: Image synthesis and self-calibration
  - method: Per-2 s images with CLEAN after phase-only self-calibration; jitter removed by shifting images using auto-correlation offsets [2 Observations: "To remove jitter motion caused by the remaining phase error, we spatially shift the images based on the offsets estimated by the auto-correlation of the images."]
  - software: CASA
- step 2: Brightness temperature enhancement of spicule
  - method: Subtract pre-event brightness from event brightness pixel by pixel; correct by filling factor 0.25 (assumed width 0.5'' vs apparent 2'') [3 The spicules observed with ALMA, IRIS…: "Thus, we use 960 K (= 240 K/0.25) as the brightness temperature of the 100GHz spicule."]
  - assumption: spicule width 0.5'' [3 The spicules observed with ALMA, IRIS…: "we assume that the width of the 100GHz spicule is 0$''$.5"]
- step 3: Optical depth vs temperature, observed and modeled
  - method: Observed tau = -ln(1-Tb/T); model free-free optical depth for assumed T and density with 0.5'' line-of-sight depth; intersection gives T and n [3 The spicules observed with ALMA, IRIS…: "The black line estimates from the observations and the colored line of the model cross when we assume the kinetic temperature of the plasma and the number density of ionized hydrogens"]
  - assumption: negligible background, T<10,000 K, thermal LTE electron-proton free-free emission [3 The spicules observed with ALMA, IRIS…: "2) the temperature range of the 100GHz spicule is lower than 10,000K, 3) the emission from the spicule is the thermal free-free emission"]
  - validation: Consistency with 193 A absorption and Rutten (2017) temperature range [3 The spicules observed with ALMA, IRIS…: "The temperature range is consistent with the temperature derived above, and thus, justifies our estimation."]
- result: Peak brightness temperature enhancement = 240 ± not stated K [3 The spicules observed with ALMA, IRIS…: "the peak enhancement of the brightness temperature caused by the spicule is about 240 K."]
- result: Kinetic temperature = ~6800 ± not stated K [abstract: "the kinetic temperature of the plasma and the number density of ionized hydrogens in the 100GHz spicule are $\sim$6800 K"]
- result: Ionized hydrogen number density = 2.2e10 ± not stated cm^-3 [abstract: "$\rm 2.2\times10^{10} \ cm^{-3}$"]
- limitation (authors): Width comparable to beam, so the actual width may be narrower [3 The spicules observed with ALMA, IRIS…: "the actual width can be narrower than the value because the width is comparable to the size of the synthesized beam."]
- limitation (authors): Only relative brightness temperatures because single-dish data not combined [2 Observations: "in this study, we only deal with relative brightness temperatures."]
- not stated (card): Briggs robust value, cell size, image size, clean iterations; Pre-event reference time for background subtraction; Details of the free-free opacity formula and constants used; Number of antennas and array configuration; Which sources were used as calibrators

### 2020ApJ...891L...8M: The Formation Height of Millimeter-wavelength Emission in the Solar Chromosphere (2020; sun; theory_or_simulation_compared_to_alma)
- question: Where in the solar atmosphere do ALMA band 3 and band 6 emission form in rMHD models with ambipolar diffusion and non-equilibrium ionization, and how well does brightness temperature trace gas temperature?
- step 1: Synthesize ALMA intensities
  - method: LTE module of STiC computes continuum opacity and emergent intensity at 1.2 and 3 mm from simulation electron density and gas pressure [Synthesis of ALMA observations: "STiC utilizes the electron densities and gas pressure stratifications from the simulations to compute the partial densities of all species that are involved in the calculations."]
  - software: STiC
  - assumption: Free-free hydrogen absorption main opacity source [Synthesis of ALMA observations: "which include the main opacity source at mm wavelengths (free-free hydrogen absorption"]
- step 2: Compute tau=1 formation heights and compare Tb with gas temperature
  - method: Optical depth at 1.2 and 3 mm, tau=1 heights averaged over 12 minutes, JPDFs of Tb vs T, contribution and source functions, comparison with VAL-C [Formation height of ALMA observations: "we computed the optical depth ($\tau$) at 1.2 and 3mm wavelengths (ALMA bands 6 and 3, respectively)."]
  - software: IDL
  - validation: Compared with VAL-C atmosphere [Formation height of ALMA observations: "For comparison we add, for both ALMA wavelengths, the height at which the optical depth is unity for a VAL-C (cite: Vernazza:1981yq) atmosphere"]
- result: Mean formation height 1.2 mm, LTE = 0.9 ± std 0.7 Mm Mm [Formation height of ALMA observations: "the average formation height at wavelengths of 1.2mm is 0.9 Mm (with a standard deviation of 0.7 Mm)"]
- result: Mean formation height 3 mm, LTE = 1.8 ± std 1 Mm Mm [Formation height of ALMA observations: "the average formation height at 3mm is 1.8 Mm (standard deviation of 1 Mm)"]
- result: Mean formation height 1.2 mm, NEI = 2.67 ± ±1.08 Mm [Formation height of ALMA observations: "n average the 1.2mm emission is formed at a height of $2.67\pm1.08$ Mm"]
- result: Mean formation height 3 mm, NEI = 2.78 ± ±1.09 Mm [Formation height of ALMA observations: "the 3mm emission is formed at a mean height of $2.78\pm1.09$ Mm"]
- result: Mean Tb difference 3 mm vs 1.2 mm, NEI = 1280 ± not stated K [Relationship between ALMA brightness te…: "The mean brightness temperature difference between the two wavelengths is $1280$ K."]
- limitation (authors): Model is 2D and may limit LOS superposition [Conclusions and discussion: "We note that our model is limited to two dimensions, and it is crucial to expand this model into 3D."]
- not stated (card): Simulation snapshot data and Bifrost output access; STiC version and exact frequency/opacity settings; Definition of the formation height and tau=1 computation details; ALMA calibration and imaging details for the observation; Snapshot selection and time sampling for statistics

## All papers in this technique

- 2015A&A...573L...4L (2015): ALMA observations of α Centauri. First detection of main-sequence stars at 3 mm wavelength
- 2017A&A...605A..78A (2017): Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models
- 2017ApJ...841L...5S (2017): The First ALMA Observation of a Solar Plasmoid Ejection from an X-Ray Bright Point
- 2017ApJ...841L..20I (2017): ALMA Discovery of Solar Umbral Brightness Enhancement at λ = 3 mm
- 2017ApJ...845L..19B (2017): A First Comparison of Millimeter Continuum and Mg II Ultraviolet Line Emission from the Solar Chromosphere
- 2017ApJ...850...35L (2017): Solar ALMA Observations: Constraining the Chromosphere above Sunspots
- 2017SoPh..292...87S (2017): Observing the Sun with the Atacama Large Millimeter/submillimeter Array (ALMA): High-Resolution Interferometric Imaging
- 2018A&A...613A..17B (2018): First analysis of solar structures in 1.21 mm full-disc ALMA image of the Sun
- 2018A&A...619L...6N (2018): First high-resolution look at the quiet Sun with ALMA at 3mm
- 2018ApJ...863...96Y (2018): ALMA Observations of the Solar Chromosphere on the Polar Limb
- 2019ApJ...871...45S (2019): Solar Polar Brightening and Radius at 100 and 230 GHz Observed by ALMA
- 2019ApJ...875..163R (2019): First Spectral Analysis of a Solar Plasma Eruption Using ALMA
- 2019ApJ...877L..26L (2019): ALMA Detection of Dark Chromospheric Holes in the Quiet Sun
- 2019ApJ...881...99M (2019): Solar Chromospheric Temperature Diagnostics: A Joint ALMA-Hα Analysis
- 2020A&A...634A..56D (2020): The multi-thermal chromosphere. Inversions of ALMA and IRIS data
- 2020A&A...634A..86P (2020): Observations of solar chromospheric oscillations at 3 mm with ALMA
- 2020A&A...635A..71W (2020): The Sun at millimeter wavelengths. I. Introduction to ALMA Band 3 observations
- 2020A&A...638A..62N (2020): Transient brightenings in the quiet Sun detected by ALMA at 3 mm
- 2020A&A...640A..57A (2020): Modeling the quiet Sun cell and network emission with ALMA
- 2020A&A...643A..41D (2020): ALMA observations of transient heating in a solar active region
- 2020A&A...644A.152E (2020): The Sun at millimeter wavelengths. II. Small-scale dynamic events in ALMA Band 3
- 2020ApJ...888L..28S (2020): Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA
- 2020ApJ...891L...8M (2020): The Formation Height of Millimeter-wavelength Emission in the Solar Chromosphere
- 2021A&A...652A..92N (2021): ALMA observations of the variability of the quiet Sun at millimeter wavelengths
- 2021A&A...655A.113M (2021): EMISSA (Exploring Millimeter Indicators of Solar-Stellar Activity). I. The initial millimeter-centimeter main-sequence star sample
- 2021A&A...656A..68E (2021): The Sun at millimeter wavelengths. III. Impact of the spatial resolution on solar ALMA observations
- 2021ApJ...906...83C (2021): ALMA and IRIS Observations of the Solar Chromosphere. II. Structure and Dynamics of Chromospheric Plages
- 2021ApJ...910...77M (2021): The Subterahertz Solar Cycle: Polar and Equatorial Radii Derived from SST and ALMA
- 2022A&A...661L...4A (2022): A first look at the submillimeter Sun with ALMA
- 2022FrASS...9.1118D (2022): A Genetic Algorithm to Model Solar Radio Active Regions From 3D Magnetic Field Extrapolations
- 2022MNRAS.511..877M (2022): Subterahertz radius and limb brightening of the Sun derived from SST and ALMA
- 2023A&A...671A..69G (2023): The Sun at millimeter wavelengths. IV. Magnetohydrodynamic waves in small-scale bright features
- 2024AN....34530149M (2024): Calculated brightness temperatures of solar structures compared with ALMA and Metsähovi measurements
- 2025A&A...693A..19S (2025): The Sun at millimeter wavelengths: V. Magnetohydrodynamic waves in a fibrillar structure
- 2025OJAp....8E.129K (2025): Observing the Sun with the Atacama Large Aperture Submillimeter Telescope (AtLAST): Forecasting Full-disk Observations
