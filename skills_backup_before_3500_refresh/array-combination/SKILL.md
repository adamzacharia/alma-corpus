---
name: alma-array-combination
description: "Combine ALMA 12-m, 7-m (ACA) and Total Power data, or ALMA with another single dish, to recover extended emission: visibility concatenation and joint deconvolution, feathering, single-dish model images, TP2VIS/sdintimaging/pseudo-visibilities, plus multi-configuration 12-m merging. Use when a source is larger than the 12-m maximum recoverable scale, when the user asks about missing flux, short spacings, feather, ACA weights or TP, or when combining compact and extended configurations or several cycles. Built from 262 ALMA papers (2014-2026)."
---

# Combining 12m, 7m and Total Power data

An interferometer filters out emission on scales larger than its shortest baselines allow. Papers fill that gap
by adding the 7-m array (ACA) in the visibility plane and Total Power (TP) or another single dish, most often by
feathering in the image plane. Two things matter most. First, a 12m+7m image without TP can still miss a large
share of the extended flux (individual cases, measured in different ways, are under Pitfalls). Second, datasets
must match before they are merged: weights, flux scales, phase centres, spectral frames, primary-beam
convention, observing epoch and, for continuum single-dish maps, observing frequency. Every combined product
needs a flux-recovery check against single-dish data.

Counts below are from the evidence pack (`skills/packs/array-combination.md`). Where a count is my own tally of
the pack's 240 `array_combination` lines (one per paper), it says so; I left out lines that are off-topic for
this technique (band-to-band images such as 2014MNRAS.444.1821F and 2017A&A...604A.115V, spectral-window
stacking such as 2024A&A...690A..55S, single-array mosaics such as 2014ApJ...784...62A).

## When to use

- The target is extended relative to the 12-m maximum recoverable scale (MRS): molecular clouds, filaments,
  nearby galaxy discs, circumstellar envelopes, the Sun. Authors who skipped short spacings name it as a
  limitation: "Missing flux on large scales due to no Total Power Array" (2016PASJ...68...88K); ALMA continuum
  without single-dish data underestimates the flux (2018MNRAS.475..448T); only relative brightness temperatures
  because single-dish data were not combined (2020ApJ...888L..28S); missing flux for some lines
  (2015ApJ...803...60S).
- You need total fluxes, column densities, masses or line ratios over extended regions (e.g. R21 maps from
  12m+7m+TP, 2025ApJ...988..162D; GMC lifecycle maps from 12m+7m+TP, 2019Natur.569..519K).
- The archive holds 12-m, 7-m and TP MOUSs of the same Science Goal, or you are merging compact + extended
  12-m configurations or data from several cycles of the same target.
- You want to add a non-ALMA single dish (IRAM 30m, APEX, Nobeyama 45m, Herschel, BGPS, SIMBA) as short
  spacings. My tally: 23 papers do this.

## When not to use

- **Compact sources well inside the MRS.** 2015A&A...576L...2S argued missing short-spacing flux was negligible
  and used 12-m data only; 2017ApJ...835..108S used only 12-m data because the 7-m total flux differed by <10%.
- **Compact-source extraction or core catalogues.** Some papers use the extended data alone for source finding:
  12 m only for core extraction but 12m+7m for lines (2018A&A...618L...5N); an extended-only image for compact
  sources (2018ApJ...855...24P). Use the `core-extraction-cmf` or `source-extraction-counts` skill.
- **Fitting models to visibilities.** Fit the 12-m and ACA visibilities jointly instead of combining images
  (2021AJ....161..271F with RADMC-3D and emcee; 2019A&A...628A.100D with galario and dynesty; 2018A&A...617A..23B
  with uvmultifit on main array + ACA only). Use `uv-plane-fitting`. Joint fitting does not measure the
  unsampled zero-spacing flux: the total flux comes from the model's extrapolation. 2020ApJ...898..146M calls its
  total belt flux model-dependent for this reason, and 2021AJ....161..271F notes its model-dependent ALMA flux is
  about half the SCUBA-2 flux.
- **Combining bands** (Band 3 + Band 7, 2017A&A...604A.115V) is a spectral-index problem, not short-spacing
  correction. Use `spectral-index`.
- **Solar data** follow their own TP calibration and feathering chain (2020A&A...635A..71W with SoAP;
  2017ApJ...845L..19B). Treat solar TP absolute temperature as a separate calibration problem.

## Steps

1. **Inventory and decide.** Goal: know what arrays exist and what each product will use.
   - Read the MOUS list (12-m TM1/TM2, 7-m, TP) and the 12-m MRS. Several papers make more than one product:
     TP+7m and TP+7m+12m image sets (2020ApJ...894...87C); 7m+TP for one criterion, 12m+7m+TP for others
     (2021A&A...656A.133Q); ACA-only cubes at 15" next to 12m+7m cubes (2021A&A...656A..46M).
   - Array selection can differ per product: all configurations concatenated but TM1 left out of the line
     cubes (2021A&A...656A..60A); C43-1 + C43-4 combined, with C43-4 restricted to baselines >250 m for one
     analysis (2025ApJ...992..103Z). The pack does not give the reasons; state yours.
2. **Calibrate each dataset separately, then check flux scales.** Goal: datasets agree before merging.
   - "calibrated separately, then combined" is the normal order (2014A&A...570L..14R; 2019ApJ...879...25K;
     2020A&A...633A..13D). Re-run the pipeline with QA flag files and flux.csv when needed (2018MNRAS.480.4974H).
   - Compare fluxes on overlapping uv scales: 12-m vs ACA within 10% (2020ApJ...889....9M) or 15%
     (2018ApJ...863..143C); check flux consistency of configurations before combining (2017ApJ...851...83C).
3. **Align phase centres, positions, spectral frames and epochs.** Goal: identical sky and frequency grids, and
   data that describe the same source state.
   - Fix positional offsets between short- and long-baseline data (2020ApJ...889L..24P; 20 and 40 mas offsets in
     2019AJ....158...15P). Correct proper motion (2019A&A...625A.118K; 2016ApJ...820L..40A) or assign all epochs
     the first-epoch position (2017ApJ...850L...6A).
   - CASA tasks seen: `fixvis` (2018ApJ...868L...5K), `fixvis` + `fixplanets` (2019ApJ...883...98Z),
     `phaseshift`/`fixplanets` (2025ApJ...990..183U), `fixplanets` + `cvel` for a moving target
     (2016ApJ...821L...8S).
   - Convert to a common frame (LSRK) before combining (2016A&A...587A..44P; 2016A&A...594A..81P) and regrid
     channels (`mstransform` to 0.25 km/s, 2018ApJ...852..122H; `cvel`, 2025SciA...11.4512O).
   - Check observing dates against source variability before merging epochs or reading differences between
     datasets as missing flux. The pack has cases where timing mattered: comet HDO and H2O observed about two
     weeks apart (2025NatAs...9.1476C); solar datasets not strictly simultaneous (2017ApJ...845L..19B); blazar
     datasets combined per band while the authors note sparse time sampling of a variable source
     (2016A&A...586A..70L).
4. **Self-calibrate (12-m multi-configuration).** Goal: consistent gains across configurations. Patterns the
   pack shows, each attributed only to papers that state it:
   - Self-calibrate the short-baseline data, concatenate with long-baseline data, then self-calibrate jointly
     (2018ApJ...869L..41A; 2025ApJ...989....3D).
   - Joint self-calibration of the concatenated data, earlier stages not stated in the pack (C43-8 + C43-5 in
     2025ApJ...986L..11S; extended configurations concatenated and self-calibrated together in
     2024AJ....167...66Y).
   - Self-calibrated short-baseline data combined with long-baseline data, any joint stage not stated
     (2025ApJ...993..120H; 2025NatAs...9.1833L).
   - Each configuration calibrated and self-calibrated individually, then combined (2019ApJ...873...73Z); two
     programs combined after self-cal (2019ApJ...883...98Z).
   - The pack does not show which pattern is most common.
5. **Continuum subtraction: before or after concatenation.** Goal: line-only visibilities without losing the
   continuum you need for self-calibration.
   - Before concatenation: 2020ApJ...889....9M; 2018A&A...616A..34H; 2021ApJ...908....8C.
   - After concatenation: `concat` then `uvcontsub` (2021ApJ...908..231M); combine, self-calibrate on the
     continuum, then subtract it (2014A&A...570L..14R).
   - Either order works if the line-free channels are the same in every dataset. Self-calibrate on data that
     still contain the continuum, apply the gain tables to the line data, then subtract (the 2014A&A...570L..14R
     order). Record line-free channels and fit order; the cards often omit them (see Pitfalls).
6. **Set relative visibility weights.** Goal: each array contributes according to its real sensitivity.
   - Check the weights before trusting `concat`. ACA/12-m examples: recomputed with `statwt`
     (2016ApJ...832..158Z; 2017ApJ...835..174S); empirical noise-based 12m/7m weights (2019Natur.569..519K);
     ACA weights multiplied by 0.3 (2014A&A...570L..14R); ACA/12-m weight ratio set to 0.18
     (2020A&A...633A..13D); ACA:TM1:TM2 weighted by intrinsic sensitivity, about 1:5:6 (2018A&A...616A..34H);
     `visweightscale` in `concat` (2019ApJ...870...39V); default weights kept after checking that average
     weights were similar across three configurations (2020A&A...634L..12D).
   - Other multi-dataset reweighting, not ACA/12-m specific: `statwt` after concatenating HUDF projects
     (2017ApJ...850...83F) and for joint imaging (2017A&A...600A.141K); Cycle 0/1 weights corrected
     (2019ApJ...887...40W); weights rescaled to match the noise variance (2017A&A...605A..42C).
   - 0.3 (a multiplier) and 0.18 (a resulting ratio) are different quantities. Work out what your weights are
     normalised to before reusing either number.
   - General practice: inspect weights per array with `plotms` (weight vs uv distance) before and after.
7. **Combine 12-m and 7-m interferometric data.** Goal: one deconvolution over all baselines.
   - The most common method is visibility-domain: `concat` the MSs (2015Natur.527...70P; 2021ApJ...908..231M) or
     pass both to one `tclean` call (2018ApJ...853..160C; 2020MNRAS.497.3504T; joint imaging in
     2015ApJ...804...37L). Use `copypointing=False` in `concat` when not mosaicking (2018MNRAS.481.4931E).
   - Less common: clean 12-m and 7-m separately and feather the images (2019ApJ...871..170M;
     2016ApJ...826...26T), or use the ACA-only image as `startmodel`/`modelimage` for the 12-m clean, then feather
     (2018ApJ...863..143C; 2020A&A...635A...2S).
8. **Add Total Power or another single dish.** Goal: restore the zero and shortest spacings. Categories below
   follow the authors' own wording. My tally: of 40 papers that combine ALMA TP, 23 say they feathered
   (e.g. 2017ApJ...841..110S; 2018ApJ...862....8T; 2020ApJ...904L..24S; 2020ApJ...902...53S), 1 says the cubes were
   combined "in Fourier space" (2019Natur.569..519K), 4 describe a uv-domain or visibility combination, and 12
   cards do not state the method.
   - **Image combination (feathering).** Feathering is itself a weighted sum of the two images in the Fourier
     domain, so "combined in Fourier space" (2019Natur.569..519K; "feathering in Fourier space",
     2016ApJ...826...26T) belongs here. In CASA: `imregrid` the single dish to the interferometer grid, then
     `feather(imagename, highres, lowres)`. The PHANGS-ALMA pipeline does channel regridding, continuum
     subtraction, `tclean`, primary-beam correction, feather with TP and convolution to a round beam
     (2025ApJ...988..162D).
   - **Primary-beam convention for feathering.** Pick one branch and keep it (general practice):
     (a) apparent-sky branch: feather the interferometer image that is not PB-corrected with a single-dish map
     multiplied by the interferometer (mosaic) PB response, then PB-correct the result once with `impbcor`. The
     pack shows the single-dish x PB step (2019A&A...623A..96Y; PB weighting inside the 2018MNRAS.475..448T
     procedure; 7m PB applied before pseudo-visibilities in 2026A&A...707A.120H).
     (b) PB-corrected branch: PB-correct the interferometer image first, feather with the unattenuated
     single-dish map, and mask the result to the PB footprint; the PHANGS order lists PB correction before
     feathering (2025ApJ...988..162D).
     Never feed a PB-corrected interferometer image together with a PB-multiplied single-dish map, and never
     PB-correct twice. Both errors give position-dependent flux errors that grow toward the mosaic edge.
   - **Single dish as a clean model.** TP regridded and used as the clean model, then feather
     (2017A&A...605A..28D); 12m+7m cleaned with the TP image as model, positive clean components smoothed with
     `imsmooth` and feathered with TP, then cleaned again (2018MNRAS.475..448T); Model-Assisted Cleaning plus
     Feather (MACF) with IRAM 30m (2024A&A...690A.375S).
   - **Joint deconvolution with a single-dish image.** 12-m and 7-m combined in visibility space, then joint
     deconvolution with APEX using `sdintimaging` (2026ApJ..1003...68Y). The card does not say how the APEX cube
     was regridded or scaled.
   - **Single dish converted to visibilities.** TP2VIS with TP weight set from the TP map rms
     (2018ApJ...867..166S); 12m, 7m and TP concatenated with TP converted at 41 Jy/K (2019ApJ...887...88E);
     12m, ACA and TP combined "in uv domain" with almica (2025ApJ...992L..15L); pseudo-visibilities in
     GILDAS/MAPPING, TP to ACA over 0-5 m and then to 12 m over 0-12 m (2025A&A...696A.100G), or IRAM 30m to 7m
     over 0-7 m after multiplying by the 7m primary beam (2026A&A...707A.120H); MIRIAD with Nobeyama 45m
     pseudo-visibilities and a tuned relative weight (2018PASJ...70...73H); NRO45 map converted to uv data
     (2018ApJ...854...90E).
   - **Continuum single-dish maps at another wavelength need a spectral conversion first.** Herschel 500 um was
     scaled to 3 mm before combination (2014ApJ...795L..25R); a beta = 1.8 spectral index was assumed to compare
     ACA 1.2 mm flux with SCUBA-2 850 um (2020ApJ...895..119T). 2018ApJ...856..147O feathered Herschel 250 um
     with CASA `feather`; the pack does not show its conversion. Regridding alone does not make the maps
     compatible: scale with a stated spectral index or SED fit, propagate the temperature and spectral-index
     uncertainty, and put both maps in the same brightness unit with correct beam metadata before feathering or
     comparing recovered flux.
9. **Image and restore.** Goal: a deconvolved cube with a known beam and flux scale.
   - Settings seen are in the parameter table; most of them are single-paper examples, so set thresholds from
     your own rms. Report beam, rms, and which arrays went into each product.
10. **Verify flux recovery.** See Verification checks. Do this before any mass or column density.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| TP combination method (authors' wording) | feather | feather, "Fourier space", model image, TP2VIS, sdintimaging, pseudo-visibilities | 23 feather of 40 TP papers (my tally) | 2017ApJ...849...90S, 2019ApJ...872..121U, 2018ApJ...867..166S |
| 12m+7m method | visibility concat or joint `tclean` | separate clean + feather; ACA image as model | most of 94 lines naming 7m/ACA (my tally) | 2021ApJ...908..231M, 2018ApJ...853..160C, 2019ApJ...871..170M |
| ACA/12-m weights, recomputed | `statwt` | noise-based empirical weights | 2 ACA/12-m `statwt`; 1 noise-based | 2016ApJ...832..158Z, 2017ApJ...835..174S, 2019Natur.569..519K |
| ACA weight multiplier | not stated by most cards | 0.3 applied to ACA weights | 1 | 2014A&A...570L..14R |
| Resulting ACA/12-m weight ratio | not stated by most cards | 0.18; ACA:TM1:TM2 about 1:5:6 | 2 | 2020A&A...633A..13D, 2018A&A...616A..34H |
| Compact-config weight for continuum | unscaled | 0.2; 1/10 | 2 | 2020ApJ...889..141T, 2016ApJ...829L..10I |
| ALMA TP flux scale factor | rarely stated | TP x0.979 (solar) | 1 | 2020A&A...635A..71W |
| TP K to Jy conversion | rarely stated | 41 Jy/K | 1 | 2019ApJ...887...88E |
| Pseudo-visibility uv range | 0 up to about the next array's dish diameter | 0-5 m, 0-7 m, 0-12 m | 2 | 2025A&A...696A.100G, 2026A&A...707A.120H |
| Weighting, combined line cubes | Briggs robust 0.5 | natural; robust 2 for faint lines | robust 0.5: 7; natural: 4 (my count, see note) | 2021ApJ...908..231M, 2016ApJ...832..142Z, 2018MNRAS.475..448T, 2018A&A...617A..23B |
| Weighting, combined continuum | Briggs robust 0.5 | robust 0 | robust 0.5: 6 (my count) | 2020ApJ...901..151S, 2019ApJ...874...89C, 2015ApJ...804...37L |
| uv taper | not stated by most cards | 0.6" to 3" | 4 | 2020ApJ...894...87C, 2018ApJ...863..143C, 2019ApJ...874...89C, 2018ApJ...858...90G |
| Multiscale scales | 0 (point) plus 2-4 larger scales | [0,1,5,10,15] px at 0.2"; 0,2",5",10"; 0,2,6,18"; 7-m 0,14.6",43.9" | 4 | 2018MNRAS.475..448T, 2019A&A...623A..96Y, 2019ApJ...874...89C, 2020ApJ...902...53S |
| Clean depth | no common choice; single-paper recipes | multiscale to ~4 sigma then single-scale to ~1 sigma (PHANGS); 6 sigma mask, clean to 4 sigma; threshold ~0.5x dirty rms; TP2VIS gain 0.05, 4e6 iterations | 1 each | 2025ApJ...988..162D, 2016ApJ...832..142Z, 2026ApJ..1001L...1T, 2018ApJ...867..166S |
| Deconvolver | multiscale for extended emission | Hogbom | multiscale 4 (row above); Hogbom 2 | 2021ApJ...907L..15S, 2026ApJ..1003...68Y |
| Masking | auto-multithresh | "automask"/"auto-masking" with the algorithm not named | auto-multithresh 2; unnamed 2 | 2019PASJ...71...85M, 2021ApJ...908..231M, 2021ApJ...907L..15S, 2026ApJ..1003...68Y |
| Overlap-scale flux agreement accepted | within calibration error | 10-15% | 2 | 2020ApJ...889....9M, 2018ApJ...863..143C |

Note on the weighting counts: I took the pack's key-parameter list, kept only papers that also have an
`array_combination` line, and counted unique papers by product. Line cubes with robust 0.5: 2021ApJ...908..231M,
2020ApJ...890..167T, 2018ApJ...863..143C, 2019ApJ...885L..20H, 2018ApJ...860L..14K, 2021A&A...648A..41V (12CO),
2016ApJ...832..142Z. Line cubes with natural weighting: 2020ApJ...889....9M, 2018A&A...617A..23B,
2018MNRAS.475..448T, 2020ApJ...901..151S. Continuum with robust 0.5: 2019ApJ...875...96N, 2020ApJ...889....9M,
2020ApJ...901..151S, 2021A&A...648A..41V, 2019ApJ...874...89C, 2020A&A...635A...2S. Robust 0.5 with the product
not stated: 2021ApJ...907L..15S, 2019ApJ...872..121U, 2019PASJ...71...85M, 2020ApJ...894...87C,
2018ApJ...862....8T. Natural with the product not stated: 2019A&A...623A..96Y, 2018ApJ...867..166S,
2019ApJ...885...82L. Robust 0 continuum and robust 2 lines in 2015ApJ...804...37L.

Recommendations that follow from this: use visibility-domain 12m+7m combination with checked weights, then
feather with TP under one consistent primary-beam convention (Step 8), because that is the most common route in
the pack and several of the single-dish comparisons under Verification were made on feathered data
(2018ApJ...858...90G; 2019ApJ...872..121U; 2020ApJ...903...94M). Use TP2VIS, `sdintimaging` or pseudo-visibilities
when you need one joint deconvolution; 2018MNRAS.475..448T found no clear improvement from direct Fourier-plane
feathering over their model-based route, so the choice is not settled by the pack.

## Software

Counts are mentions in the pack's software aggregate (matched steps only), with version variants merged.

| Software | Mentions | Used for | Examples |
|---|---|---|---|
| CASA (incl. "casa 5.1", "5.6.0", "6.2.0") | 67 | calibration, `concat`, `statwt`, `tclean`, `feather` | 2021ApJ...908..231M, 2018MNRAS.480.4974H |
| `tclean` | 8 | joint deconvolution of 12m+7m | 2020ApJ...889....9M, 2025ApJ...988..162D |
| `feather` | 6 | image-plane TP/single-dish combination | 2016ApJ...832..142Z, 2017A&A...605A..28D |
| uvcombine | 2 | feathering: Herschel with SCUBA/SHARC (no ALMA data in that step); BGPS 1.1 mm with ALMA | 2018ApJ...853..171G, 2024ApJ...962...48J |
| Miriad | 2 | joint FT and CLEAN with 45m pseudo-visibilities | 2018PASJ...70...73H |
| TP2VIS | 1 | TP to visibilities, joint deconvolution | 2018ApJ...867..166S |
| sdintimaging | 1 | joint deconvolution of a single-dish image with interferometer data | 2026ApJ..1003...68Y |
| almica | 1 | 12m+ACA+TP combination described as uv domain | 2025ApJ...992L..15L |
| GILDAS (MAPPING) | 1 | single-dish pseudo-visibilities | 2025A&A...696A.100G, 2026A&A...707A.120H |
| PHANGS-ALMA pipeline | 1 | full 12m+7m+TP imaging chain | 2025ApJ...988..162D |
| SoAP | 1 | solar imaging with TP feathering | 2020A&A...635A..71W |
| simalma, CASA simobserve | 1 each | simulating combined observations | named in the aggregate |
| uvmultifit; galario; dynesty | 1; 2; 1 | fitting 12m+ACA visibilities instead of combining images | 2018A&A...617A..23B, 2019A&A...628A.100D |

## Pitfalls

- **12m+7m without TP still misses flux.** The pack has individual cases, measured in different ways, not a
  typical fraction: "even with the ACA only 50% of the extended flux is recovered" (2014A&A...570L..14R, 12m+ACA);
  ALMA-ACA recovered 8.4 of ~29 Msun (2018ApJ...856..147O, a mass comparison); ACA alone recovered 41% and 21% of
  SCUBA-2 flux in two cores (2020ApJ...895..119T, ACA-only, with an assumed beta); [CI] flux 34±15% lower than
  Herschel (2018ApJ...863..143C); about 4 of 8.2 Jy in APEX CO 3-2 resolved out (2017ApJ...841..110S). Treat
  masses from such maps as lower limits, as 2017ApJ...837...60B and 2021A&A...648A..41V (outflow masses) did.
- **Filtering changes shapes, not only totals.** 2018ApJ...856..147O fitted a Plummer-like slope p=4.0 to the
  ALMA-ACA profile against p=1.6 from Herschel and concluded the ALMA-ACA density profile cannot be discussed; a
  smooth model underestimated the peak flux because extended structure was filtered (2019ApJ...874...89C). Do
  not fit profile slopes, widths or morphology on maps that lack the relevant spacings.
- **Missing flux is channel dependent.** Negligible at line edges but 30-40% in central channels
  (2015ApJ...814..143A); the interferometer alone held ~0.15 of the NRO45 flux, the feathered map ~0.8
  (2019ApJ...872..121U). Line ratios between a combined and an uncombined line are biased.
- **Single-dish flux scale.** 2020A&A...635A..71W rescaled a solar TP map by 0.979 and still calls the absolute
  TP scale "less certain". In a Herschel + SCUBA feather (no ALMA data in that step), 2018ApJ...853..171G had to
  scale SCUBA up by ~3 and tested factors of 0.5-10x, which shows how far single-dish scales can disagree.
  Feathering puts any single-dish calibration error directly into the large-scale flux.
- **Cross-frequency continuum maps.** A Herschel, SCUBA or BGPS map is not at the ALMA frequency. Without an
  explicit spectral conversion (Step 8; 2014ApJ...795L..25R, 2020ApJ...895..119T) the short spacings or the
  recovery fraction carry an unknown temperature and spectral-index error.
- **Primary beam and mosaic response.** Mixing the two branches in Step 8 (PB-corrected interferometer image
  with a PB-multiplied single dish, or a second PB correction) gives position-dependent flux errors.
  2019A&A...623A..96Y also notes a CASA mosaic imaging issue that overestimated fluxes by 10%.
- **Unchecked weights.** Data from different cycles can carry weights that do not reflect sensitivity; papers fixed
  this with `statwt` or manual rescaling to match noise variance (2017A&A...605A..42C; 2019ApJ...887...40W).
- **Positional, frame and epoch mismatches** between configurations, epochs or cycles blur structure or mix
  source states (see Step 3). Moving targets need `fixplanets` (2016ApJ...821L...8S).
- **Pixels in feathered or combined maps are correlated on the beam scale**; 2017ApJ...845L..19B did not
  correct for this in a pixel-by-pixel comparison. Bin to at least a beam before regressions.
- **Using combined data where it hurts.** Large-scale emission raises the background for compact-source
  finding; see When not to use.
- **Settings the cards flag as not stated.** Specific to combination: feathering parameters (2020ApJ...890..167T;
  2017ApJ...845L..19B), the TP combination method (2020A&A...633A..13D), relative weighting of 12-m and ACA
  (2018ApJ...856..147O; 2019ApJ...875...96N; 2017ApJ...850L...6A; 2021ApJ...908..231M), and how APEX data were
  regridded and scaled for `sdintimaging` (2026ApJ..1003...68Y). The cards rarely state `sdfactor`,
  `effdishdiam` or `sdgain`. General settings that the pack's not-stated aggregate lists most often (counts are
  per phrasing, so related phrasings are listed separately there): CASA version (15) and CASA plus pipeline
  version (8); line-free channels and continuum-subtraction method (13, plus several variant phrasings, two of
  which ask for the fit order); flux-scale uncertainty (10, plus 6 with the flux calibrator); image and cell size
  (7); self-calibration solution intervals and iterations (6, plus 3 and 3 in variants); primary-beam correction
  details (5 and 4).

## Verification checks

What the papers did:

- **Total flux vs single dish.** Combined maps recovered ~90% of APEX flux (2017A&A...605A..28D;
  2020A&A...633A..13D); ALMA total flux consistent with Nobeyama 45-m (2020ApJ...901..151S); missing flux vs IRAM
  30m <~30% north, ~50% south (2020ApJ...903...94M).
- **Spectra vs single dish at matched resolution.** Feathered cube profile vs IRAM 30-m at 30"
  (2018ApJ...858...90G); 7M+TP spectrum matched the TP profile (2019PASJ...71...85M); ACA profile vs APEX
  (2016RAA....16..106H); feathering, interferometer-only and NRO45 spectra side by side (2019ApJ...872..121U).
- **Flux-scale agreement on overlapping uv scales**: 10% (2020ApJ...889....9M), 15% (2018ApJ...863..143C).
- **Gain from adding short spacings.** 12m+ACA concatenation recovered 9-24% extra CO over ACA alone in four
  of six sources (2021ApJ...908..231M).
- **Sensitivity to choices.** ACA weight changes did not affect results (2014A&A...570L..14R); direct
  Fourier-plane feather tested with no clear improvement (2018MNRAS.475..448T); compared with APEX spectra and
  Hogbom-cleaned individual datasets (2019A&A...631A..64B); residual scaling for flux consistency with the TP map
  (2018ApJ...867..166S). The 0.5x-10x scale test in 2018ApJ...853..171G was on a Herschel + SCUBA feather, but the
  same test applies to an ALMA + single-dish feather.
- **External instruments.** Morphology checked against SMA, SHARC2 and VLA; not significantly biased by missing
  flux on scales <~30" (2015ApJ...804...37L).

What a careful referee adds (general practice, not from the pack):

- Smooth the combined cube to the single-dish beam and compare channel by channel, not only the integrated flux.
- Compare the power spectra or radial uv amplitudes of TP, 7m and 12m in their overlap annulus.
- State which arrays went into every product and the MRS of each, and give flux-recovery fractions per line.
- State the primary-beam branch used for feathering and check the flux of a source near the mosaic edge.
- Check the clean-residual flux scaling (dirty-beam vs clean-beam area) when the combined beam is non-Gaussian.
- Report the provenance settings listed at the end of Pitfalls (CASA and pipeline versions, line-free channels
  and fit order, flux-scale uncertainty, image and cell size, masks, self-calibration intervals, combination
  weights and feather parameters). Record a value you cannot find as unknown; do not copy a value from the
  parameter table.

## Source cards

Full list: `references/sources.md` (262 papers). Most informative for this technique:

- 2014A&A...570L..14R: ACA weight multiplier 0.3, weight test, 50% recovery even with ACA
- 2014ApJ...795L..25R: Herschel 500 um scaled to 3 mm before combination
- 2016ApJ...832..158Z: 12m+7m with `statwt`, then feather with TP
- 2017A&A...605A..28D: TP as clean model, feather, ~90% of APEX flux
- 2018A&A...616A..34H: ACA:TM1:TM2 weights from sensitivity
- 2018A&A...617A..23B: antenna-specific weighting, TP feathered, uvmultifit
- 2018ApJ...853..171G: uvcombine feathering of Herschel with SCUBA, scale-factor tests
- 2018ApJ...856..147O: ACA missing mass, filtered density profile
- 2018ApJ...863..143C: ACA as model image, flux-scale check, missing [CI] flux
- 2018ApJ...867..166S: TP2VIS joint deconvolution
- 2018MNRAS.475..448T: custom TP-model clean and feather procedure
- 2018PASJ...70...73H: Nobeyama 45m pseudo-visibilities in MIRIAD
- 2019A&A...623A..96Y: IRAM 30m regridded, multiplied by mosaic PB, feathered
- 2019ApJ...870...39V: `visweightscale` and overlap-based weighting
- 2019ApJ...872..121U: interferometer vs feathered flux ratio to NRO45
- 2019Natur.569..519K: noise-based 12m/7m weights, TP combined in Fourier space
- 2020A&A...633A..13D: ACA/12-m weight ratio 0.18, ~90% APEX recovery
- 2020A&A...635A..71W: solar TP scaling and feathering
- 2020ApJ...889....9M: 12m vs ACA flux-scale check, concat after uvcontsub
- 2020ApJ...895..119T: ACA recovery of SCUBA-2 flux with an assumed beta
- 2021ApJ...908..231M: concat 12m+ACA, then uvcontsub, measured flux gain
- 2024A&A...690A.375S: Model-Assisted Cleaning plus Feather with IRAM 30m
- 2025A&A...696A.100G: GILDAS pseudo-visibilities TP to ACA to 12 m
- 2025ApJ...988..162D: PHANGS-ALMA pipeline feathering
- 2026ApJ..1003...68Y: 12m+7m in visibility space, `sdintimaging` with APEX
