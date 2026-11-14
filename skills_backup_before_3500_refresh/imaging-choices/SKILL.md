---
name: alma-imaging-choices
description: "Choose tclean imaging parameters for ALMA data the way published papers do: weighting and Briggs robust, deconvolver (hogbom, clark, multiscale, mtmfs), uv taper and uv-range cuts, multiscale scales, masks, clean thresholds, cell size, and the checks that show the image can be trusted. Use when imaging ALMA continuum or line visibilities, picking a robust value or taper for a science goal, matching resolutions across bands or tracers, or judging whether a published image's settings are reasonable. Built from 1121 ALMA papers (2012-2026)."
---

# ALMA imaging choices (tclean)

Imaging parameters trade resolution against surface-brightness sensitivity and decide how much extended flux
survives. Briggs `robust=0.5` is the default in about two thirds of stated robust values in every period from 2012
to 2026; natural or `robust=2` is chosen for detection and faint or extended emission, robust 0 or lower (or
uniform) to resolve structure. The two mistakes that matter most: quoting a total flux or size from an image whose
uv coverage or weighting filtered out extended emission, and treating sub-beam clumps in a cleaned image as real
without a simulated-observation or alternative-imaging check.

**How counts were made.** (1) Robust values: corpus statistics `stats/settings_long.csv` (1591 non-held-out
cards, all techniques, 2012-2026; no 2022 rows). Each row is one numeric robust value x one science field, so a
paper with two robust values or two fields gives several rows; "natural" and "uniform" are not in this file.
(2) Weighting type and deconvolver: my count of the pack's key-parameter list, which shows 290 of the 1121 papers
spread over 2012-2026 (it ends "... 1236 more" lines), one count per paper, all of a paper's lines read together.
(3) Unstated rates: `stats/unstated_rates.csv` (all 1591 cards). (4) Software: pack aggregates, copied exactly.
Everything else is an example list, not a frequency. Off-topic regex hits are not cited.

## When to use

- Imaging calibrated ALMA visibilities in CASA `tclean` (or GILDAS) for continuum (`specmode='mfs'`) or line
  cubes (`specmode='cube'`).
- Picking `weighting`/`robust`, `uvtaper`, `uvrange`, `deconvolver`, `scales`, `nterms`, `threshold`, mask and
  `cell` for a stated goal (detection, size, morphology, kinematics, flux, spectral index).
- Making matched-resolution images across bands, tracers or arrays.
- Reviewing whether a paper's or pipeline product's imaging setup supports the claim made from it.

## When not to use

- Self-calibration solution intervals: use `self-calibration`.
- Line-free channel selection and `uvcontsub`: use `continuum-subtraction`.
- Fitting sizes, fluxes or disk models to visibilities: use `uv-plane-fitting`; papers often do this because
  image-plane values depend on weighting (2017ApJ...846..108C, 2018MNRAS.475.4924K).
- Moment maps from a finished cube: use `moment-maps`. 12m+7m+TP combination in depth: use `array-combination`.
- Archive discovery, restore and MS structure: use the working-with-ALMA-data skill.

## Steps

1. **State the goal of each image first.** Papers often make several images of one dataset: robust 0.5, -1 and
   a tapered robust 2 image (2018ApJ...853..171G); robust 0.5 with robust 2 for non-detections and 0 and -0.5 also
   made (2020ApJ...890..130T); two cubes at robust 0.5 and 0.1 (2020MNRAS.496.4061D); robust 0.5 or 2 chosen per
   disk orientation (2026A&A...705A.198M).
2. **Pick weighting from the goal.** Corpus robust rows: 0.5 in 700 of 1061 (66%), 0 in 125 (12%), 2 in 117
   (11%), 1 in 49 (5%), negative in 44 (4%), other values 26 (stats). Field medians are all 0.5 (stats README).
   - Detection, faint lines, limits, extended emission: natural or `robust=2`. Stated reasons: "to maximize the
     point-source flux significance" (2020MNRAS.493.4294B), "to maximise the sensitivity" (2019A&A...630A..59B),
     "to maximize sensitivity to an extended signal" (2016PASJ...68...88K). High-z galaxy rows use robust 2 more
     often (23 of 97 rows, 24%) than star-formation rows (20 of 241, 8%) (my count of stats).
   - General purpose: `robust=0.5` (2018ApJ...866..117C, 2025ApJ...993...85Y, 2020A&A...634A...9M, 2024ApJ...968L..19F).
   - Resolving structure: robust 0 to -2, uniform or superuniform. Examples: robust -2 (uniform) for a
     long-baseline map (2018A&A...616L...3B); robust -2 for a high-resolution image (2018ApJ...861...91H); robust
     -1.0 and 1.0 (2021A&A...654A..35B); uniform "to decrease side lobes and optimize angular resolution"
     (2014ApJ...797...27F); robust 0 with -1 and uniform tested (2017A&A...602L..10O).
   - Continuum and lines from the same data are often weighted differently. Examples with lines on the natural
     side: continuum 0.5, lines natural (2018ApJ...859..111H, 2018MNRAS.475.4924K); continuum 0.5, cube 2.0
     (2024ApJ...972..111L, 2025SciA...11.4512O); continuum uniform, lines natural (2020ApJ...898...10T,
     2024PASJ...76..340K). Examples the other way: continuum natural, masers or line cube robust 0.5
     (2014A&A...572L...9R, 2019ApJ...881...10B). The pack has no denominator for which split is more common.
3. **Add a taper or uv cut only when the goal needs a different beam.** 65 of the 290 listed papers mention a
   taper (my count, including tested-not-adopted); `imaging.uv_taper` is unstated in 88% of cards (stats).
   - Detection: 0.7" after testing 0.4-0.8" (2017ApJ...851..145M); natural plus 0.6" taper for detection maps
     (2015ApJ...807..128S); 0.45" taper with natural weighting for non-detections (2020A&A...636A..37D); 100-200
     klambda tested, 150 klambda adopted (2021ApJ...907L..15S). 2020MNRAS.493.4294B smoothed natural maps in the
     image plane with a 0.27" Gaussian chosen by S/N over 0.01-0.50"; that is image convolution, not a `uvtaper`.
   - Low-surface-brightness emission: `outertaper=0.4"` gave 841 Jy km/s total CO(6-5) against 512 Jy km/s in four
     regions of the untapered image (2018ApJ...866..117C); 0.3" taper as a flux-recovery test (2019ApJ...876..130H).
     A taper reweights baselines that were observed; it cannot restore spacings shorter than the shortest baseline.
   - Matching another beam: 12CS tapered to the isotopologue beams, reducing flux about 25% (2019ApJ...876...72L);
     Band 3 tapered to Band 7 resolution (2024A&A...684A..56K); second epoch tapered to the first beam
     (2020PASJ...72L...9F); superuniform Band 3 restored to the 1.3 mm beam (2024ApJ...963..164R); ALMA tapered to an
     SMA-like 5.9"x3.0" beam (2015ApJ...814..143A).
   - Inner uv cut for compact sources: >100 klambda (2015ApJ...801...82H, 2020ApJ...891...80M), >80 klambda with
     uniform (2014ApJ...796....1T), a 100 klambda cut chosen as the best rms over 0-300 klambda (2018ApJ...860...77E),
     baselines >2.5 km only (2018A&A...616L...3B).
   - Syntax (general practice): `clean(outertaper=...)` became `tclean(uvtaper=...)`; a valid form is
     `uvtaper=['0.5arcsec']` or `['0.010arcsec','0.010arcsec','10deg']` (2021A&A...654A..35B). The taper value is
     not the achieved beam; read the restoring beam from the image header.
4. **Pick the deconvolver.** In the 290 listed papers (my count): Hogbom 39, multiscale 40, mtmfs/`nterms=2` 9,
   Clark 3, SDI 2, MEM 2. `imaging.deconvolver` is unstated in 90% of cards (stats), so these are small numbers.
   - Compact or point-like emission and many line cubes: `deconvolver='hogbom'` (2025MNRAS.541.2540Z,
     2024A&A...682A.166F, 2025ApJ...986L..22R, 2019A&A...630A..59B). Clark is a separate point-component CLEAN
     algorithm, still selected in modern `tclean` work (2023PSJ.....4..142C, 2020ApJ...888L..28S, 2019AJ....158...76C).
   - Extended emission: `deconvolver='multiscale'` (2020ApJ...899...10T "to recover the extended emission",
     2020ApJ...898..146M, 2018ApJ...852..122H). Split by component: multiscale for lines and Hogbom for continuum
     (2019A&A...631A..64B, 2025SciA...11.4512O); multiscale adopted over Hogbom (2018ApJ...860...77E).
   - Wide-band or multi-band continuum, spectral index: `deconvolver='mtmfs'`, `nterms=2` (2018ApJ...852..122H,
     2018ApJ...853..171G, 2024ApJ...963..164R, 2015ApJ...813..118M, 2024ApJ...972..111L).
   - Non-CLEAN methods are rare: maximum entropy (2014ApJ...796...82Z; uvmem in 2015ApJ...811...92C), sparse
     modeling (2020ApJ...895...84Y), SDI in GILDAS (2018A&A...614A..58B, 2019A&A...629A.146V).
   - Leaving an image dirty happens for weak sources (2012ApJ...761L..32W left one target dirty).
5. **Set multiscale scales from the beam.** Recipe seen: 0 (point), about 1x and 3x the beam, sometimes 9x or more
   (2017A&A...602L..10O [0,1,3] beams; 2025ApJ...993...85Y [0,1,3] clean beam; 2020ApJ...898..146M [0,1,3,9];
   2020MNRAS.496.4061D point plus 3, 6, 9 beams). In pixels: [0,5,10] (2026A&A...705A.198M), [0,6,18]
   (2020ApJ...899...10T), [0,5,20] (2024ApJ...963..164R). Keep the largest scale below the largest recoverable
   scale; 2016PASJ...68...88K found convergence for a largest scale of 40-50" with 7m+12m. CASA `scales` are in
   pixels (general practice): `scale_pixels = scale_arcsec / cell_arcsec`; beam 0.10" and cell 0.02" turn
   [0,1,3] beams into `scales=[0,5,15]`. Convert arcsec or beam values from papers before reuse. Full list in
   `references/parameters.md`.
6. **Mask.** Options seen: polygon mask on all channels (2012ApJ...757..129R); interactive per-channel masks
   (2019A&A...628A.118B); `auto-multithresh` checked against a conservative user mask (2024ApJ...963..164R; also
   2024ApJ...968L..19F, 2021ApJ...907L..15S); boxes around >5 sigma sources (2015ApJ...807..128S); fixed circular
   mask (2025ApJ...986L..22R 10" diameter; 2024A&A...682A.166F 1.25"); no mask with `niter` 500-1000
   (2019A&A...630A..59B). Keplerian masks for disk lines (2026A&A...705A.198M; `keplerian_mask` named in 4 papers,
   pack aggregate) assume gas co-located with the dust and near-Keplerian (2026A&A...705A.198M); compare with a
   broader mask and inspect excluded emission before reading non-detections or odd velocities from such a cube.
   `imaging.masking` is unstated in 82% of cards (stats).
7. **Set the stopping threshold.** Of 29 papers in the key-parameter list and excerpts that give a threshold in
   rms units (my count), 11 use about 2x rms (2014ApJ...792L...2C, 2014ApJ...795L..30C, 2016ApJ...821L...8S,
   2017ApJ...846..108C, 2018Sci...362.1034D, 2018Icar..307..380T, 2020MNRAS.496.4061D, 2024ApJ...962....1S,
   2024A&A...682A.166F, 2025ApJ...986L..22R, 2025ApJ...990L..31B) and 6 use 3x. Range seen 0.5 sigma
   (2016ApJ...829....6W, 2020ApJ...890...29F) to about 5 sigma (2025A&A...697A..64V). `gain=0.1`
   (2015ApJ...811...39I, 2018ApJ...857...19F); 0.05 for diffuse emission (2016PASJ...68...88K). Set `niter` high
   enough that the threshold, not the iteration cap, stops the run; read the stop reason (general practice), since
   some combined 12CO channels were not cleaned to threshold (2019A&A...631A..64B).
8. **Cell and image size.** Pixel about 1/5 of the beam (2026A&A...705A.198M); otherwise an absolute cell, from
   0.0037" (2024ApJ...961..228S continuum) to 1" (2020ApJ...899...10T ACA cores). `imaging.cell_size` is unstated
   in 85% of cards (stats). For mosaics use `gridder='mosaic'` (2020A&A...634A...9M). A bright source outside the
   target can be removed by imaging both fields as a mosaic (2020A&A...642A..96P: noise 11.8 to 7.3 uJy).
9. **Primary-beam correct** before any flux or size measurement (`impbcor` or `pbcor=True`; 2018ApJ...852..122H,
   2024ApJ...968L..19F; 2020ApJ...899...10T fit after correction). Unstated in 83% of cards (stats).
10. **Run the Verification checks**, then record weighting, robust, taper, deconvolver, scales, threshold, mask,
    cell, final beam, rms and CASA version.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Briggs robust (numeric) | 0.5 | -2 to 2 | 700 of 1061 rows (stats) | 2018ApJ...866..117C, 2025ApJ...993...85Y |
| robust 0 | resolution-leaning | 0 | 125 of 1061 rows | 2013Natur.493..191C, 2023PSJ.....4..142C |
| robust 2 | sensitivity, faint lines | 1.5-2 | 117 (+8 at 1.5) of 1061 rows | 2024A&A...682A.166F, 2015ApJ...798..124R |
| robust 1 | mixed continuum/lines | 0.6-1.0 | 49 (+4 at 0.6-0.8) of 1061 rows | 2015Natur.522..455C, 2025MNRAS.541.2540Z |
| negative robust | high-resolution maps | -2 to -0.2 | 44 of 1061 rows | 2018ApJ...861...91H, 2019A&A...631A..25J |
| natural weighting named | detection, extended | n/a | 130 of 268 weighting papers in list | 2017ApJ...846..108C, 2020ApJ...899...10T |
| uniform / superuniform | resolution, beam matching | n/a | 13 / 2 of 268 in list | 2014ApJ...797...27F, 2024Natur.633..323V |
| Weighting unstated | | | 39% of 1591 cards (stats) | |
| uv taper | none unless detection or matching | 0.010" to 10"; 18.75 klambda to 1.5 Mlambda | 65 of 290 in list | 2021A&A...654A..35B, 2020ApJ...898..146M, 2024ApJ...977..198L, 2023PASJ...75..424O |
| Deconvolver | hogbom compact/lines; multiscale extended | hogbom, clark, multiscale, mtmfs, MEM, SDI | 39 / 3 / 40 / 9 / 2 / 2 of 290 in list | 2020ApJ...898..146M, 2025MNRAS.541.2540Z |
| `nterms` | 2 | 1-2 | 9 with nterms=2 in list | 2018ApJ...853..171G, 2015ApJ...813..118M |
| Multiscale scales | [0, 1x, 3x beam] | up to 15x beam; up to 608 pixels | see parameters.md | 2017A&A...602L..10O, 2018ApJ...857...19F |
| Threshold | 2x rms | 0.5 to about 5 sigma | 11 of 29 at 2x rms | 2020MNRAS.496.4061D, 2025A&A...697A..64V |
| Loop gain | 0.1 | 0.05-0.1 | 5 state it (my count) | 2015ApJ...811...39I, 2016PASJ...68...88K |
| Cell | about 1/5 beam | 0.0037" to 1" | unstated in 85% | 2026A&A...705A.198M, 2024ApJ...961..228S |
| `niter` | high, threshold-limited | 500-1000 to 4 million | few state it | 2019A&A...630A..59B, 2018ApJ...867..166S |

Robust by period (stats rows; share at 0.5 / 0 / 2 / negative): 2012-2015 n=81: 63% / 25% / 6% / 1%;
2016-2018 n=390: 67% / 9% / 13% / 5%; 2019-2021 n=383: 68% / 12% / 8% / 4%; 2023-2026 n=207: 61% / 11% / 16% / 3%.
In the pack list, natural is named by 59 of 108 weighting papers from 2012-2018 and 71 of 160 from 2019-2026;
Briggs/robust by 63 of 108 and 111 of 160 (my count; a paper can name both).

## Software

Pack aggregates over all 1121 papers (labels overlap: "casa tclean" and "tclean" may be the same paper):

| Tool (pack label: count) | Used for |
|---|---|
| casa: 813; tclean: 71; casa tclean: 14; casa clean: 8; clean: 7 | imaging and deconvolution |
| miriad: 27 | imaging in some papers; the cards rarely say why |
| gildas: 23; gildas/mapping: 3 | Hogbom/SDI cleaning (2018A&A...614A..58B, 2015ApJ...814..143A, 2020MNRAS.495..943H) |
| aips: 19; aips jmfit: 3 | imaging and source fits |
| uvcontsub: 11 | continuum subtraction before cube imaging |
| casa imfit: 8; imfit: 6 | Gaussian sizes and fluxes on the cleaned image |
| casa simobserve: 7 | artifact and completeness tests (2019ApJ...874...89C, 2020ApJ...899...10T, 2020ApJS..251...14H) |
| feather: 5 | single-dish combination (2018MNRAS.475..448T used a custom feather of clean components) |
| keplerian_mask: 4; uvmem: 4; imsmooth: 4 | disk line masks; maximum-entropy imaging (2015ApJ...811...92C); smoothing |
| bettermoments: 3; uvmodelfit: 3 | moment maps; uv-plane checks (2017ApJ...846..108C) |

## Pitfalls

- **Missing flux.** 11 of the 120 author-limitation lines in the pack mention resolved-out, filtered or missing
  extended flux or absent short spacings (my count). Examples: the high-resolution dataset resolves out 74% of
  the CO (2020MNRAS.496.4061D); more than 80% missing against single dish (2020ApJ...899...10T); robust 0.5 missed
  extended [C II] that robust 2 recovered (2024A&A...682A.166F); missing flux despite 7m+12m multiscale imaging
  (2016PASJ...68...88K); total belt flux model-dependent through extrapolation to zero uv distance
  (2020ApJ...898..146M). A taper or more natural weighting reveals only sampled low-surface-brightness emission;
  for total flux add short-spacing data or give a model-based estimate with its assumptions.
- **Fake substructure.** A smooth flat-center profile observed with simobserve produces substructure like the
  observed one (2019ApJ...874...89C); low-contrast continuum substructure cannot be told from artifacts
  (2020ApJ...899...10T).
- **Sizes near the beam.** Separate observed, deconvolved and unresolved widths. A width comparable to the beam
  "may be narrower" (2020ApJ...888L..28S); sub-beam vertical structure was claimed cautiously
  (2018MNRAS.475.4924K). Give uncertainties and a model or injection test for marginally resolved sizes.
- **Mismatched resolution.** Spectral indices and line ratios need a common final beam and comparable uv
  sampling; tapering to match can change flux (about 25% in 2019ApJ...876...72L).
- **Spectral index noise.** 2018ApJ...852..122H computed alpha only above 5x rms and noted an absolute alpha
  uncertainty of about 0.4 from 10% flux calibration per band; 2018ApJ...853..171G kept alpha only where
  |alpha| > 5 sigma(alpha) or sigma(alpha) < 0.1.
- **Clean-beam vs dirty-beam units.** Restored components are in clean-beam units and residuals in dirty-beam
  units, which biases fluxes when the dirty beam has broad wings (general practice). Papers applied the Jorsater
  and van Moorsel residual scaling (2018ApJ...867..166S) or report JvM epsilon 0.31-0.71 (2024ApJ...974..102S).
- **Correlated pixels.** Pixels within a beam are not independent: beam correlations were neglected
  (2020MNRAS.496.4061D), correlated noise noted (2019ApJ...881...10B), and a cost function assumed independent
  points (2023PSJ.....4..142C).
- **Sidelobes from bright off-target sources** raise the noise (2020A&A...642A..96P).
- **Non-CLEAN residuals.** Sparse-modeling images self-calibrated with MS-CLEAN models had larger asymmetric
  residuals (2020ApJ...895...84Y).
- **Underreporting.** Cards flag as not stated (pack aggregate): CASA version 118; image and cell size 43 (plus 13
  and 11 for variant phrasings); primary-beam correction details 22; clean threshold, masks, cell and image size
  10. Briggs is sometimes named with no robust value (2018A&A...614A..58B, 2020ApJ...888L..28S, 2024A&A...689A.317G).
- **Moving targets.** Shift to a common phase center before combining epochs (`fixvis`/`fixplanets`,
  2018ApJ...852..122H; Titan regridded to its rest frame, 2019AJ....158...76C).
- **Spectral gridding.** Forcing a channel center onto the systemic velocity samples wings symmetrically
  (2012ApJ...757..129R); channels degraded to 0.43 km/s to raise S/N (2018A&A...614A..58B).

## Verification checks

What papers did:

- **Flux against single-dish or lower-resolution data:** ACA vs combined cube 174 vs 161 Jy km/s
  (2020MNRAS.496.4061D); SCUBA-2 plus a 180-degree rotation subtraction (2018MNRAS.475.4924K); APEX, under 20%
  filtered (2018A&A...614A..58B); CARMA (2015ApJ...798..124R); Herschel total CO(6-5) (2018ApJ...866..117C).
- **Re-image with a taper or more natural weighting:** 2017ApJ...846..108C, 2024A&A...682A.166F,
  2019ApJ...876..130H, 2017A&A...597A..41G (1.5" outertaper check images), 2018Sci...362.1034D (tapered check map).
- **Simulated observations** of a smooth model with `simobserve` + `tclean` (2019ApJ...874...89C, 100
  hour-angle realizations; 2020ApJ...899...10T).
- **Alternative settings agree:** codes, masks and weightings in four test regions (2020MNRAS.495..943H);
  auto-mask vs a user mask (2024ApJ...963..164R); robust -2 to 2 tried with similar results (2018ApJ...865...13T);
  superuniform compared with robust 0.5 (2024Natur.633..323V); weighting chosen after trials (2025MNRAS.541.2540Z).
- **Multiscale scales** chosen by minimal residuals and maximal recovered flux; insensitive to small-scale bias
  below 0.8 (2016PASJ...68...88K).
- **Image-plane vs uv-plane values agree** (uvmodelfit vs imfit and sextractor, 2017ApJ...846..108C).
- **Residuals and overcleaning:** residuals inspected (2026A&A...705A.198M); no overcleaned regions
  (2024A&A...689A.317G); dirty-beam sidelobes under 10% (2015ApJ...814..143A).
- **Noise and dynamic range against expectation:** rms vs expected (2020A&A...642A..96P); dynamic range about
  580 (2023PSJ.....4..142C); fluxes within 5% across datasets (2018ApJ...852..122H).

What a careful referee adds:

- The largest recoverable scale against source size, and a missing-flux estimate when they are close.
- Every robust value, taper, threshold, mask method, cell, final beam, rms and CASA version stated.
- For clumps: a simulated observation, or persistence across two weightings or deconvolvers.
- For spectral indices and line ratios: a common final beam, comparable uv sampling and recoverable scales,
  matched spectral resolution for channel ratios, an S/N mask, and the inter-band flux-scale error propagated
  separately from image noise.
- For fluxes: residual flux inside the aperture and whether a JvM-type correction was needed and applied.
- Aperture errors from rms x sqrt(aperture area / beam area) for apertures larger than the beam, and
  image-plane likelihoods that account for pixel correlation (general practice).
- Channels or images that stopped on `niter` rather than threshold listed.
- For non-detections: limits from a natural or tapered image, aperture stated.

## Source cards

Full list: `references/sources.md` (1121 papers). Parameter lists: `references/parameters.md`.

- 2016PASJ...68...88K: multiscale scale search, gain 0.05, small-scale bias test, 7m+12m missing flux.
- 2019ApJ...874...89C: ACA+12m multiscale, robust 0.5 with 1.5" taper, simobserve artifact test.
- 2020ApJ...899...10T: natural multiscale for cores, simobserve check, >80% missing flux.
- 2024A&A...682A.166F: robust 2 vs 0.5 and taper test for extended [C II].
- 2020MNRAS.493.4294B: natural weighting, image-plane smoothing chosen by S/N for a z=8.31 detection.
- 2020MNRAS.496.4061D: two cubes at robust 0.5 and 0.1, multiscale in beam units, 74% resolved out.
- 2025MNRAS.541.2540Z: robust chosen after trials; Hogbom cube to 1.5 sigma.
- 2018ApJ...852..122H: per-tracer robust, multiscale in arcsec, mtmfs spectral index with S/N mask.
- 2024ApJ...963..164R: mtmfs with auto-multithresh checked by a user mask; superuniform to match beams.
- 2026A&A...705A.198M: three-stage tclean, Keplerian masks, robust by disk orientation, pixel 1/5 beam.
- 2018ApJ...866..117C: outertaper and extended CO flux.
- 2019ApJ...876...72L: taper to match isotopologue beams, flux change.
- 2020ApJ...895...84Y: sparse modeling vs MS-CLEAN fidelity.
- 2018MNRAS.475..448T: 12m+7m+TP custom feather combination.
- 2020A&A...642A..96P: mosaic imaging to remove an off-field source's sidelobes.
- 2017ApJ...846..108C: natural weighting, taper test, uv vs image fits.
- 2020MNRAS.495..943H: GILDAS vs CASA, masks and weightings compared.
- 2018ApJ...867..166S: 4 million iterations, gain 0.05, JvM residual scaling.
- 2024ApJ...974..102S: per-tracer robust and JvM epsilon values.
- 2019A&A...631A..64B: multiscale lines vs Hogbom continuum; channels not cleaned to threshold.
