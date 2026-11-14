---
name: alma-imaging-choices
description: "Choose tclean imaging parameters for ALMA data the way published papers do: weighting and Briggs robust, deconvolver (hogbom, clark, multiscale, mtmfs), uv taper and uv-range cuts, multiscale scales, masks, clean thresholds, cell size, and the checks that show the image can be trusted. Use when imaging ALMA continuum or line visibilities, picking a robust value or taper for a science goal, matching resolutions across bands or tracers, or judging whether a published image's settings are reasonable. Built from 2488 ALMA papers (2012-2026)."
---

# ALMA imaging choices (tclean)

Imaging parameters trade resolution against surface-brightness sensitivity and decide how much extended flux
survives. Briggs `robust=0.5` is the choice in about 63% of stated robust values and at least 59% in every period
from 2012 to 2026; natural or `robust=2` (now the second most common value, 16% in 2022-2026) is chosen for
detection and faint or extended emission, robust 0 or lower (or uniform) to resolve structure. The two mistakes
that matter most: quoting a total flux or size from an image whose uv coverage or weighting filtered out extended
emission, and treating sub-beam clumps or large-scale CLEAN flux as real without a simulated-observation or
alternative-imaging check (2019ApJ...874...89C, 2023ApJ...954..197I).

**How counts were made.** (1) Robust values: corpus statistics `stats/settings_long.csv` (3498 non-held-out
cards, all techniques, 2012-2026). Each row is one numeric robust value x one science field, so a paper with two
robust values or two fields gives several rows; "natural" and "uniform" are not in this file. (2) Weighting type,
deconvolver and taper: my count of the pack's key-parameter list, which shows 160 of the 2488 papers spread over
2012-2026 (it ends "... 4826 more" lines), one count per paper, all of a paper's lines read together. (3) Unstated
rates: `stats/README.md` (all 3498 cards). (4) Software: pack aggregates, copied exactly. Everything else is an
example list, not a frequency. Off-topic regex hits are not cited.

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
- Fitting sizes, fluxes or disk models to visibilities: use `uv-plane-fitting`; papers do this because
  image-plane values depend on weighting and deconvolution (uvmodelfit next to imfit, 2020ApJ...904..131N;
  uvmultifit per channel, 2021A&A...653A..53A; frank profiles, 2026A&A...705A.196H).
- Moment maps from a finished cube: use `moment-maps`. 12m+7m+TP combination in depth: use `array-combination`.
- Archive discovery, restore and MS structure: use the working-with-ALMA-data skill.

## Steps

1. **State the goal of each image first.** Papers often make several images of one dataset: robust 0 for
   morphology and moment 0, robust +2 for moments 1 and 2, PV plots and tilted-ring fits (2018A&A...615A.155H);
   robust 0.5 for the main high-resolution cube and robust 2 for warp analysis (2025MNRAS.537..520Z); continuum
   0.5, high-resolution cube 0.8, low-resolution cube 2.0 with a 600 klambda taper (2026MNRAS.548ag546D); robust
   0.5, 2, and 2 with a taper to about twice the resolution (2021A&A...654A..37D); robust 0.5 by default, natural
   for faint targets and non-detections (2025A&A...703A..15M).
2. **Pick weighting from the goal.** Corpus robust rows: 0.5 in 1669 of 2630 (63%), 2 in 327 (12%), 0 in 268
   (10%), 1 in 150 (6%), negative in 137 (5%), other values 79 (stats). Field medians are 0.5 except cosmology
   (median 1, n=7) and solar system (median 0, n=9) (stats README).
   - Detection, faint lines, limits, extended emission: natural or `robust=2`. Stated reasons: "to maximize
     sensitivity to an extended signal" (2016PASJ...68...88K), "to maximise the sensitivity" (2019A&A...630A..59B),
     robust 2 "to maximize sensitivity" with robust 0.5 peak fluxes within about 15% (2025MNRAS.538.3001T),
     natural "to maximize the surface brightness sensitivity per beam" (2025A&A...701A.120P). An archive-mining
     survey used robust 2 for all continuum images and re-imaged the under 10% with obvious artifacts by flagging
     baselines and/or using robust 0.5 (2019ApJS..244...40L). High-z galaxy rows use robust 2 more often (56 of 255 rows, 22%) than star-formation
     rows (64 of 621, 10%) (my count of stats).
   - General purpose: `robust=0.5` (2018ApJ...866..117C, 2021A&A...653A..53A, 2024PASJ...76..437Y,
     2025ApJ...988..106H). Robust 0 is described as "approximately half way between natural and uniform"
     (2018A&A...615A.155H).
   - Resolving structure: robust 0 to -2, uniform or superuniform. Examples: robust -2 (uniform) "to achieve the
     highest resolution" (2026ApJ...999...32W); uniform "to decrease side lobes and optimize angular resolution"
     (2014ApJ...797...27F); superuniform with `npixels=3` for high resolution (2021AJ....162...99F); robust -1 to fit
     lensed-image positions (2023ApJ...954..197I); uniform with spacings >1 km for astrometry (2015ApJ...808L...1A);
     uniform to check for a single point source (2025A&A...694L..15H). Per-band values were tuned for
     resolution and sensitivity: Band 7 -0.2, Band 6 0.0, Band 4 -0.6, Band 3 0.5 (2021A&A...648A..33M).
   - Scans: robust -2 to 2 in steps of 0.5 to see what structure survives (2025ApJ...992L..31C); -2 to 2 with
     similar results (2018ApJ...865...13T); candidates 0, 0.5, 1, 2 (2023PASP..135g4501H).
   - Continuum and lines from the same data are often weighted differently. Examples: continuum 0.5, CO cube
     natural (2018MNRAS.475.4924K); continuum natural, line cube 0.5 (2019ApJ...881...10B); continuum robust 0,
     line cubes 0.5 (2015ApJ...808L...3A); continuum uniform and natural, CO cubes natural (2026ApJ...999...32W);
     one transition 0.5 and the others 2.0 (2021ApJ...906..111T). The pack has no denominator for which split is
     more common.
3. **Add a taper or uv cut only when the goal needs a different beam.** 41 of the 160 listed papers mention a
   taper (my count, including tested-not-adopted and one uv-range cut filed as a taper); `imaging.uv_taper` is
   unstated in 88% of cards (stats).
   - Detection: 0.7" taper on weak lines "to increase the significance" (2021AJ....162...99F); ten cubes per
     undetected target tapered 0.2" to 2" in 0.2" steps (2020MNRAS.499.5136C); natural with a 1" taper for the
     initial detection image (2025A&A...699A..80H); 1" or 2" tapers tested for non-detections
     (2025A&A...703A..15M); `uvtaper=[0.5 arcsec]` to find a faint continuum emitter (2022A&A...665A.107T).
   - Low-surface-brightness emission: robust 0.5 with a 0.3" taper "to improve the signal-to-noise ratio of the
     fainter, larger-scale emission" (2025ApJ...988..106H); `outertaper=0.4"` for extended CO (2018ApJ...866..117C);
     2" taper on a natural continuum image (2026ApJ...999...32W); 2" Gaussian taper with robust 2
     (2015ApJ...798..124R). Residual maps are often tapered to show faint misfit: 0.8" (2018MNRAS.479.5423M), 10"
     (2019MNRAS.490.5134B), 0.02" (2025ApJ...988..106H). A taper reweights baselines that were observed; it cannot
     restore spacings shorter than the shortest baseline (missing large-scale flux without TP, 2016PASJ...68...88K;
     12m-only cubes with negative bowls, 2023A&A...678A.194C).
   - Matching another beam: 12CS tapered to the isotopologue beams, reducing flux about 25% (2019ApJ...876...72L);
     elliptical tapers per transition for common-resolution radial profiles (2021ApJ...906..111T); Band 4 tapers to
     circularize an elongated beam (2021A&A...648A..33M); robust and taper explored to match two bands' beams
     (2026A&A...705A..96M); 1.2" common-resolution stack test (2019A&A...630A..59B); ALMA tapered to an SMA-like
     5.9"x3.0" beam (2015ApJ...814..143A).
   - Inner uv cuts and baseline selection: `uvrange` >138 klambda (2023MNRAS.522...56V); baselines <60 m omitted
     for some targets (2025A&A...703A..15M); baselines >25 m or >50 m for affected sources (2022A&A...665A..82O);
     spacings >1 km for astrometry (2015ApJ...808L...1A).
   - Syntax (general practice): `clean(outertaper=...)` became `tclean(uvtaper=...)`; valid forms are
     `uvtaper=['0.5arcsec']` or `['0.3arcsec','0.2arcsec','45deg']`, and tapers in klambda (50 and 100 klambda,
     2013ApJ...777...92S; 600 klambda, 2026MNRAS.548ag546D). The taper value is not the achieved beam: a 0.5"
     taper gave a 0.65"x0.62" beam (2022A&A...665A.107T); read the restoring beam from the image header.
     Image-plane smoothing (`imsmooth`, 16 papers in the pack aggregates) is a different operation from a uvtaper.
4. **Pick the deconvolver.** In the 160 listed papers (my count): multiscale 38, Hogbom 31, mtmfs or `nterms=2`
   11, Clark 4, Cotton-Schwab 2, maximum entropy 1, SDI 1. `imaging.deconvolver` is unstated in 87% of cards
   (stats), so these are small numbers.
   - Compact or point-like emission and many line cubes: `deconvolver='hogbom'` (2023Ap&SS.368...33M,
     2024ApJS..270....9X, 2025MNRAS.537..520Z, 2021A&A...645A..97Q). Clark is a separate point-component CLEAN
     algorithm, still selected in recent work (2025PSJ.....6..183C, 2020NatAs...4..861C, 2020ApJ...888L..28S).
     Cotton-Schwab for disks without substructure, multiscale for disks with substructure (2024PASJ...76..437Y).
   - Extended emission: `deconvolver='multiscale'`. A survey that tested Hogbom and multiscale with three masking
     methods found multiscale with a primary-beam mask "the most stable and optimal" (2023A&A...678A.194C).
     Split by data: Hogbom for ACA-only, multiscale for TP+ACA (2021A&A...653A..53A); Hogbom per source,
     multiscale for uv-stacks (2020ApJ...904..131N); multiscale for lines, Hogbom for continuum
     (2019A&A...631A..64B).
   - Wide-band or multi-band continuum, spectral index: `deconvolver='mtmfs'`, `nterms=2` (2018ApJ...852..122H,
     2021A&A...648A..33M, 2015ApJ...808L...3A). Rules seen: `nterms=2` where fractional bandwidth exceeds 10% and
     for all-band combinations (2025A&A...702A.276P); Hogbom per SPW but mtmfs `nterms=2` for all four SPWs, 30-40%
     better sensitivity (2025A&A...699A.265G); `nterms=1` when a flat spectrum is assumed (2026A&A...707A.255C).
   - Non-CLEAN methods are rare: maximum entropy with gpu-uvmem, truncated at ten iterations "to avoid excessive
     clumping" (2026A&A...707A.255C; uvmem 9 papers in aggregates); SDI in GILDAS (2018A&A...614A..58B).
   - Dirty images first: a dirty cube (`niter=0`) inspected before cleaning only the detected sources
     (2025A&A...701A.120P); a 0-iteration cube for a Keplerian-masked line search (2021MNRAS.506.1978L).
5. **Set multiscale scales from the beam.** Recipe seen: 0 (point), about 1x and 3x the beam, sometimes 5x to 10x
   ([0,1,3] x CLEAN beam, 2024PASJ...76..437Y; [0,1,3,5] beams, 2021A&A...648A..33M; [0,1,3,5,10] beams,
   2020ApJ...904..131N; [0,5,15,25] pixels, about 1, 3 and 5 beams, 2025A&A...703A..15M). A geometric series from
   0 increasing by about x2 the beam-minor-axis/cell ratio up to about 5.5" was used for a whole survey
   (2023A&A...678A.194C). In pixels: [0,5,15] (2015ApJ...808L...3A, plus 45 for CO; 2024RAA....24f5011X),
   [0,5,15,50,150] (2026A&A...709A..93D, 2020ApJ...894L..14L). Keep the largest scale below the largest
   recoverable scale; 2016PASJ...68...88K converged for a largest scale of 40-50" with 7m+12m. Self-calibration
   models of data poorer than about 1" used `scales=[0]` (2021A&A...648A..33M). CASA `scales` are in pixels
   (general practice): `scale_pixels = scale_arcsec / cell_arcsec`; beam 0.10" and cell 0.02" turn [0,1,3] beams
   into `scales=[0,5,15]`. Convert arcsec or beam values from papers before reuse. Full list in
   `references/parameters.md`.
6. **Mask.** Options seen: a primary-beam mask (`pbmask` at 10% response), chosen over an in-house auto-mask and
   `auto-multithresh` (2023A&A...678A.194C); `auto-multithresh` (9 papers in aggregates; 2025ApJ...988..106H,
   2026ApJ...999...32W) with stated settings `noisethreshold` 5 and `sidelobethreshold` 1.25 (2024RAA....24f5011X)
   or thresholds 2, 4.5, 2, 0.0 with `nsigma=1` (2025A&A...699A..80H); a single-dish-based mask (>0.3 x SD
   maximum) plus `auto-multithresh` (2023PASP..135c4501P); interactive per-channel masks for sources brighter than
   20 Jy (2021A&A...653A..53A); fixed circular masks (10" diameter, 2026ApJ...999L..32R; 2" radius,
   2020ApJ...904..131N; 1.3" on Titan, 2020ApJ...904L..12C); an elliptical mask (2021AJ....162...99F); polygon
   mask (2014ApJ...785...44M); no mask with `niter` 500-1000 (2019A&A...630A..59B). Keplerian masks for disk lines
   (`keplerian_mask` 15 papers, pack aggregate) need stellar mass, inclination, PA and outer radius
   (2021AJ....162...99F, 2026MNRAS.545f2150S); the ARKS gas analysis assumes gas co-located with the dust and
   near-Keplerian (2026A&A...705A.198M). Compare with a broader mask and inspect excluded emission before reading
   non-detections or odd velocities from such a cube. `imaging.masking` is unstated in 81% of cards (stats).
7. **Set the stopping threshold.** Of 22 papers in the key-parameter list and excerpts that give a clean threshold
   in rms units (my count), 10 use about 2x rms (2014ApJ...792L...2C, 2015ApJ...800L..14C, 2017ApJ...838..147C,
   2018Sci...362.1034D, 2020ApJ...904..131N, 2020ApJ...904L..12C, 2020NatAs...4..861C, 2021A&A...645A..97Q,
   2021A&A...654A..37D, 2026ApJ...999L..32R); 1.5x and 3x rms are next (4 each). Range seen 0.5 sigma
   (2021A&A...654A..37D for two faint targets) to 5 sigma (2023A&A...678A.194C, which found a "relatively shallow"
   5 sigma most stable against divergence and stippling across 15 fields; one field only to 10 sigma).
   `gain=0.1` (2025A&A...699A.265G); 0.05 for diffuse emission (2016PASJ...68...88K, 2020PASJ...72...33K). Set
   `niter` high enough that the threshold, not the iteration cap, stops the run: flux was lost with too few
   iterations and 10 000-100 000 were tested (2021A&A...653A..53A). Read the stop reason per channel (general
   practice); divergent channels were masked and left uncleaned in one survey (2023A&A...678A.194C).
8. **Cell and image size.** About 5 pixels per beam (2019ApJS..244...40L); pixel 10% of the beam minor axis
   (2025A&A...702A.276P); 0.01" pixels "sampling the synthesised beams properly" (2025MNRAS.537..520Z).
   Absolute cells range from 0.005" (2023ApJ...954..197I, 2021AJ....162...14A) to 1" (2024RAA....24f5011X,
   2026A&A...707A.255C). `imaging.cell_size` is unstated in 84% of cards (stats). For mosaics use
   `gridder='mosaic'` (2024A&A...687A.112M; joint mosaic with 12m+7m, 2020PASJ...72...33K). `pblimit=0.2` is
   common (2024RAA....24f5011X, 2023MNRAS.522...56V, 2024ApJS..270....9X); below 0.3 primary-beam attenuation
   the Gaussian beam approximation adds systematics (2019ApJS..244...40L).
9. **Primary-beam correct** before any flux or size measurement (`impbcor`, 17 papers in aggregates, or
   `pbcor=True`; 2018ApJ...852..122H, 2025ApJ...988..106H, 2019ApJ...882..107R). Unstated in 80% of cards (stats).
   Visibility-profile tools may ignore the primary beam and bias large disks (frank, 2026A&A...705A.196H).
10. **Run the Verification checks**, then record weighting, robust, taper, deconvolver, scales, threshold, mask,
    cell, final beam, rms and CASA version.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Briggs robust (numeric) | 0.5 | -2 to 2 (4 rows report 3) | 1669 of 2630 rows (stats) | 2018ApJ...866..117C, 2024PASJ...76..437Y |
| robust 2 | sensitivity, faint lines | 1.5-2 | 327 (+30 at 1.5) of 2630 rows | 2025MNRAS.538.3001T, 2019ApJS..244...40L |
| robust 0 | resolution-leaning | 0 | 268 of 2630 rows | 2018A&A...615A.155H, 2025PSJ.....6..183C |
| robust 1 | mixed continuum/lines | 0.6-1.0 | 150 (+11 at 0.6-0.8) of 2630 rows | 2015ApJ...808L...4A, 2020ApJ...894...72S |
| negative robust | high-resolution maps | -2 to -0.2 | 137 of 2630 rows | 2026ApJ...999...32W, 2019A&A...631A..25J |
| natural weighting named | detection, extended | n/a | 63 of 141 weighting papers in list | 2016PASJ...68...88K, 2025A&A...701A.120P |
| uniform / superuniform | resolution, astrometry | n/a | 8 / 1 of 141 in list | 2014ApJ...797...27F, 2021AJ....162...99F |
| Weighting unstated | | | 40% of 3498 cards (stats) | |
| uv taper | none unless detection or matching | 0.02" to 10"; 50 to 1000 klambda | 41 of 160 in list | 2025ApJ...988..106H, 2019MNRAS.490.5134B, 2013ApJ...777...92S, 2015ApJ...808L...4A |
| Deconvolver | hogbom compact/lines; multiscale extended | hogbom, clark, Cotton-Schwab, multiscale, mtmfs, MEM, SDI | 31 / 4 / 2 / 38 / 11 / 1 / 1 of 160 in list | 2023A&A...678A.194C, 2025MNRAS.537..520Z |
| `nterms` | 2 for wide band | 1-2 | 11 mtmfs or nterms=2 in list | 2025A&A...702A.276P, 2025A&A...699A.265G |
| Multiscale scales | [0, 1x, 3x beam] | up to about 10x beam; up to 608 pixels | see parameters.md | 2024PASJ...76..437Y, 2020ApJ...904..131N |
| Threshold | 2x rms | 0.5 to 5 sigma (10 sigma one field) | 10 of 22 at 2x rms | 2020ApJ...904..131N, 2023A&A...678A.194C |
| Loop gain | 0.1 | 0.05-0.1 | 4 state it (my count) | 2025A&A...699A.265G, 2016PASJ...68...88K |
| Cell | 5 pixels per beam | 0.005" to 1" | unstated in 84% | 2019ApJS..244...40L, 2025A&A...702A.276P |
| `niter` | high, threshold-limited | 500-1000 to 100 000 | few state it | 2019A&A...630A..59B, 2021A&A...653A..53A |

Robust by period (stats rows; share at 0.5 / 0 / 2 / negative): 2012-2015 n=136: 63% / 22% / 4% / 2%;
2016-2018 n=628: 66% / 10% / 11% / 6%; 2019-2021 n=855: 66% / 10% / 11% / 5%; 2022-2026 n=1011: 59% / 9% / 16% / 5%.
In the pack list, natural is named by 28 of 52 weighting papers from 2012-2018 and 35 of 89 from 2019-2026;
Briggs/robust by 33 of 52 and 75 of 89 (my count; a paper can name both). CASA documents robust from -2 to 2
(general practice), so a reported robust 3 should be checked against the paper before reuse.

## Software

Pack aggregates over all 2488 papers (labels overlap: "casa tclean" and "tclean" may be the same paper):

| Tool (pack label: count) | Used for |
|---|---|
| casa: 1809; tclean: 515; casa tclean: 60; clean: 30; casa clean: 14 | imaging and deconvolution |
| alma pipeline: 20 | pipeline imaging products |
| gildas: 66 | Hogbom/SDI cleaning (2018A&A...614A..58B) |
| miriad: 54; aips: 36; difmap: 10 | imaging in some papers; the cards rarely say why |
| uvcontsub: 121 | continuum subtraction before cube imaging |
| imfit: 56; casa imfit: 26 | Gaussian sizes and fluxes on the cleaned image |
| feather: 19 | single-dish combination (custom feather of clean components, 2018MNRAS.475..448T; feather, MACF and SDINT compared, 2023PASP..135c4501P) |
| impbcor: 17; imsmooth: 16 | primary-beam correction; image-plane smoothing |
| keplerian_mask: 15; auto-multithresh: 9 | disk line masks; automatic masks |
| fixvis: 12; fixplanets: 12 | common phase centre for moving or high-proper-motion targets |
| bettermoments: 12; uvmodelfit: 11; uvmultifit: 10 | moment maps; uv-plane checks (2020ApJ...904..131N) |
| casa simobserve: 10; simobserve: 9 | artifact and recovery tests (2019ApJ...874...89C, 2020MNRAS.493.5045M, 2020PASJ...72...33K) |
| uvmem: 9 | maximum-entropy imaging (gpu-uvmem, 2026A&A...707A.255C) |

## Pitfalls

- **Missing flux.** 11 of the 120 author-limitation lines in the pack mention resolved-out, filtered or missing
  extended flux or absent short spacings (my count). Examples: ALMA recovered 54 +/- 5% of the Nobeyama 45-m flux
  (2020MNRAS.493.5045M); only about 15% of single-dish flux in NGC 6240 (2015ApJ...800...70S); about 30% recovered
  over a 12m Band 1 mosaic (2026A&A...707A.255C); 12m-only cubes show negative bowls and one window was withheld
  (2023A&A...678A.194C); structures larger than the 0.4" maximum recoverable scale resolved out
  (2022PASJ...74..738T); missing flux despite 7m+12m multiscale imaging (2016PASJ...68...88K); adding TP raised
  flux by at least 30% (2021A&A...653A..53A). A taper or more natural weighting reveals only sampled
  low-surface-brightness emission; for total flux add short-spacing data or give a model-based estimate with its
  assumptions.
- **CLEAN changes extended amplitudes.** In mock tests CLEAN boosted intensities on scales >=0.7" by about 60%
  (2023ApJ...954..197I). A smooth model observed with simobserve produced substructure like the observed one
  (2019ApJ...874...89C); subtle azimuthal features may reflect uv-coverage differences (2015ApJ...808L...3A);
  structure within about a beam of the centre can be distorted (2025ApJ...988..106H).
- **Sizes near the beam.** Separate observed, deconvolved and unresolved widths. Only 154 of 233 GMCs were
  resolved and radii near the beam are highly uncertain (2020MNRAS.493.5045M); missing flux and noise make
  Gaussian sizes "first approximations" (2021A&A...653A..53A); one survey kept the non-deconvolved size when the
  deconvolved size fell below half of it (2023A&A...678A.194C). Give uncertainties and a model or injection test
  for marginally resolved sizes.
- **Mismatched resolution.** Spectral indices and line ratios need a common final beam and comparable uv
  sampling; tapering to match can change flux (about 25% in 2019ApJ...876...72L).
- **Spectral index noise.** 2018ApJ...852..122H computed alpha only above 5x rms and noted an absolute alpha
  uncertainty of about 0.4 from 10% flux calibration per band; the same 0.4 systematic appears in
  2025A&A...694L..15H (alpha = +1.26 +/- 0.44). Entropy-regularized images biased a recovered spectral index
  (-0.26 for a flat input; 2026A&A...707A.255C). Non-simultaneous bands mix spectral index with variability
  (2022PASJ...74..738T).
- **Clean-beam vs dirty-beam units.** Restored components are in clean-beam units and residuals in dirty-beam
  units, which biases fluxes when the dirty beam has broad wings (general practice). Papers applied the JvM
  correction F = C + eps R with eps = C/(D-R) in the aperture (2020ApJ...904..131N); report eps 0.62 +/- 0.17
  across a survey, with the dirty beam integrated to its first null and noise scaled by 1/eps
  (2023A&A...678A.194C); eps 0.24 checked with deeper cleans to 1 and 0.7 sigma and a single-dish flux
  (2025MNRAS.537..520Z); eps about 0.37 (Briggs) and 0.31 (natural) (2024A&A...689A.145S). One paper skipped it
  after deep cleaning (2025A&A...699A..80H).
- **Correlated pixels.** Pixels within a beam are not independent: aperture errors as rms x sqrt(N beams)
  (2020ApJ...904..131N); profile errors with independent points set by arc length over the beam major axis
  (2026A&A...705A.196H); the full pixel covariance was ignored as intractable (2025MNRAS.537..520Z).
- **Sidelobes and variability.** Faint patches near Sgr A* were judged residual sidelobes, and its flaring
  violates the non-variability assumption of synthesis imaging, giving circular artifacts (2022PASJ...74..738T);
  an annulus started at twice the resolution to avoid PSF sidelobes (2025A&A...702A.276P). Solar data gave
  stripes at robust 0 and were imaged at robust 1 (2017SoPh..292...87S).
- **Startmodels.** A continuum startmodel overestimated at hot cores with line forests left negative residuals
  (2023A&A...678A.194C).
- **Underreporting.** Cards flag as not stated (pack aggregate): CASA version 166; image and cell size 61 (plus 19
  and 17 for variant phrasings); primary-beam correction details 33 (plus 17); clean threshold, masks, cell and
  image size 15 (plus 13, 13 and 12). Briggs is sometimes named with no robust value (2013ApJ...777...92S,
  2020ApJ...888L..28S, 2020MNRAS.491..427B).
- **Moving targets.** Shift to a common phase centre before combining epochs (`fixvis`/`fixplanets`,
  2018ApJ...852..122H); image solar-system bodies in their rest frame (2020ApJ...904L..12C, 2019AJ....158...76C).
- **Spectral gridding.** Forcing a channel centre onto the systemic velocity samples wings symmetrically
  (2012ApJ...757..129R); channels degraded to 0.43 km/s to raise S/N (2018A&A...614A..58B); catalogued velocity
  dispersions may be overestimated by about 1.5 when lines are narrow compared with the channel width
  (2020MNRAS.493.5045M).

## Verification checks

What papers did:

- **Flux against single-dish or lower-resolution data:** SEST 15-m (2018A&A...615A.155H); IRAM 30-m
  (2025MNRAS.537..520Z); Nobeyama 45-m (2020MNRAS.493.5045M); APEX, under 20% filtered (2018A&A...614A..58B);
  SCUBA (2015ApJ...800...70S).
- **Re-image with a taper or other weighting:** taper tried to test for resolved-out flux (2017ApJ...846..108C);
  tapered check map (2018Sci...362.1034D); 0.5" taper for tentative lines and common resolution
  (2021A&A...654A..37D); tapers at three beams to estimate Band 6 flux (2021A&A...651A..35O); robust 0.5 vs 2 peak
  fluxes (2025MNRAS.538.3001T); natural weighting dropped one feature below 3 sigma (2023ApJ...954..197I).
- **Simulated observations** of a model with `simobserve` + `tclean`: 100 hour-angle realizations
  (2019ApJ...874...89C); mock GMCs through the full pipeline (2020MNRAS.493.5045M); mock visibilities matched to
  each execution block (2020PASJ...72...33K); same hour angle, duration and configuration (2020NatAs...4..861C);
  uv-coverage simulations on an infrared template (2026A&A...707A.255C).
- **Alternative settings agree:** deconvolvers, masks and thresholds tested (2023A&A...678A.194C); robust -2 to 2
  (2018ApJ...865...13T, 2025ApJ...992L..31C); natural and Briggs agree after residual scaling, and delta-function
  CLEAN, uv-plane fits and subsamples give consistent profiles (2020ApJ...904..131N); structure persists across
  cleaning runs (2013ApJ...777...92S); gpu-uvmem vs tclean (2026A&A...707A.255C); a Fourier-plane feather gave no
  clear improvement (2018MNRAS.475..448T).
- **Multiscale scales** chosen by minimal residuals and maximal recovered flux; insensitive to small-scale bias
  below 0.8 (2016PASJ...68...88K).
- **Residuals and iterations:** residuals inspected (validation aggregate: 2 papers); flux lost with too few
  iterations (2021A&A...653A..53A); no fragments in residuals (2019ApJ...874...89C); binned visibilities and dirty
  residual maps (2018MNRAS.479.5423M).
- **Noise and dynamic range against expectation:** achieved vs theoretical noise at matched resolution
  (2023A&A...678A.194C); rms vs archive QA2 images (2019ApJS..244...40L); noise from half-split difference maps
  (2020PASJ...72...33K); dynamic range >= 200 000 (2022PASJ...74..738T); fluxes within 5% across datasets
  (2018ApJ...852..122H).

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
- Channels or images that stopped on `niter` rather than threshold, or were left uncleaned, listed.
- For non-detections: limits from a natural or tapered image, aperture stated.

## Source cards

Full list: `references/sources.md` (2488 papers). Parameter lists: `references/parameters.md`.

- 2023A&A...678A.194C: ALMA-IMF cubes; deconvolver, mask and threshold tests; pbmask; 5 sigma; JvM with noise scaling.
- 2020ApJ...904..131N: Hogbom vs multiscale, JvM aperture fluxes, sqrt(N beams) errors, uv vs image checks.
- 2019ApJ...874...89C: ACA+12m multiscale, robust 0.5 with 1.5" taper, simobserve artifact test.
- 2025MNRAS.537..520Z: robust 0.5 vs 2 by goal, Hogbom at 1.5 sigma, JvM checked by deeper cleans and single dish.
- 2021A&A...653A..53A: ACA Hogbom vs TP+ACA multiscale, niter tests, interactive masks, flux gain from TP.
- 2026A&A...707A.255C: gpu-uvmem vs tclean, robust 2, scales in pixels, 70% missing flux, spectral-index bias.
- 2016PASJ...68...88K: multiscale scale search, gain 0.05, small-scale bias test, 7m+12m missing flux.
- 2018ApJ...852..122H: per-tracer robust, multiscale in arcsec, mtmfs spectral index with S/N mask.
- 2023ApJ...954..197I: robust 0, 0.5, -1 and natural by purpose; CLEAN boosts extended flux in mocks.
- 2021AJ....162...99F: Keplerian masks, superuniform, 0.7" taper on weak lines, per-line weighting.
- 2025ApJ...988..106H: robust 0.5 with 0.3" taper, auto-multithresh, tapered residual image.
- 2019ApJS..244...40L: archive-scale robust 2, 5 pixels per beam, artifact re-imaging, QA2 noise check.
- 2018A&A...615A.155H: robust 0 vs +2 by analysis product, SEST missing-flux check.
- 2021A&A...654A..37D: robust 0.5, 2 and tapered 2; thresholds 2 and 0.5 sigma.
- 2025A&A...703A..15M: robust 0.5 default, natural and 1-2" tapers for non-detections, scales in beams.
- 2021A&A...648A..33M: per-band robust tuning, tapers to circularize, mtmfs, scales by beam.
- 2025A&A...702A.276P: mtmfs rule by fractional bandwidth, pixel 10% of beam, sidelobe-safe annulus.
- 2022PASJ...74..738T: variability artifacts, residual sidelobes, resolved-out structure, dynamic range.
- 2020MNRAS.493.5045M: mock-GMC simobserve tests, 54% recovery vs Nobeyama, beam-size limits.
- 2019ApJ...876...72L: taper to match isotopologue beams, flux change.
- 2021ApJ...906..111T: per-transition robust and elliptical tapers for common resolution.
- 2018MNRAS.475..448T: 12m+7m+TP custom feather combination.
