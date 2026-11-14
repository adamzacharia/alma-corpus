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

=== SKILL.md (imaging-choices) ===
---
name: alma-imaging-choices
description: "Choose tclean imaging parameters for ALMA data the way published papers do: weighting and Briggs robust, deconvolver (hogbom, multiscale, mtmfs), uv taper and uv-range cuts, multiscale scales, masks, clean thresholds, cell size, and the checks that show the image can be trusted. Use when imaging ALMA continuum or line visibilities, picking a robust value or taper for a science goal, matching resolutions across bands or tracers, deciding whether to clean at all, or judging whether a published image's settings are reasonable. Built from 1121 ALMA papers (2012-2026)."
---

# ALMA imaging choices (tclean)

Imaging parameters trade resolution against surface-brightness sensitivity and decide how much extended flux
survives. Papers pick them per science goal: natural or robust 2 for detection and faint lines, robust 0.5 as
the general compromise, robust 0 or lower (or uniform) to resolve structure. The two mistakes that matter most:
reporting a total flux or size from an image whose weighting or uv coverage resolved out extended emission, and
treating sub-beam clumps in a cleaned image as real without a simulated-observation or alternative-imaging check.

Counts below are my own counts of the pack lines unless marked "pack aggregate". The pack's key-parameter list
is truncated after mid-2018 (432 papers listed), so weighting and deconvolver counts describe 2012-2018 practice;
the 40 detailed excerpts cover 2012-2026. Regex tagging pulled in a few off-topic papers (non-ALMA facilities,
non-imaging values); those are excluded from counts and citations.

## When to use

- Imaging calibrated ALMA visibilities in CASA `tclean` (or GILDAS/MAPPING) for continuum (`specmode='mfs'`)
  or line cubes (`specmode='cube'`).
- Picking `weighting`/`robust`, `uvtaper`, `uvrange`, `deconvolver`, `scales`, `nterms`, `threshold`, mask and
  `cell` for a stated science goal (detection, size, morphology, kinematics, flux, spectral index).
- Making matched-resolution images across bands, tracers or arrays (spectral index, line ratios, multi-wavelength
  comparison).
- Reviewing whether a paper's or a pipeline product's imaging setup supports the claim made from it.

## When not to use

- Calibration and self-calibration solution intervals: use the `self-calibration` skill.
- Line-free channel selection and `uvcontsub`: use the `continuum-subtraction` skill.
- Fitting sizes, fluxes or disk models directly to visibilities: use `uv-plane-fitting`; papers often do this
  precisely because image-plane values depend on weighting (2017ApJ...846..108C, 2018MNRAS.475.4924K).
- Moment maps from a finished cube: use `moment-maps`.
- Joint 12m+7m+TP combination strategy in depth: use `array-combination`.
- Raw archive discovery, restore and MS structure: use the working-with-ALMA-data skill.

## Steps

1. **State the goal of each image before choosing anything.** Papers routinely make more than one image of the
   same data: a high-resolution and a high-sensitivity version (2016ApJ...823...68S robust 0.5 and robust 2;
   2018ApJ...853..171G robust 0.5, -1, and tapered robust 2), or a detection map plus a resolved map
   (2016MNRAS.457L.122H natural plus taper for detection, robust 0.5 for high resolution).
2. **Pick weighting from the goal.**
   - Detection, faint lines, upper limits, extended emission: natural or `robust=2`. Stated reasons: "to maximize
     the point-source flux significance" (2020MNRAS.493.4294B), "to maximise the sensitivity" (2019A&A...630A..59B),
     "to maximize sensitivity to an extended signal" (2016PASJ...68...88K).
   - General purpose continuum or lines: Briggs `robust=0.5` (2018ApJ...866..117C, 2025ApJ...993...85Y,
     2020A&A...634A...9M, 2024ApJ...968L..19F).
   - Resolving structure: `robust=0` to `-1`, uniform or superuniform (2016ApJ...828...46A robust -1.0 for resolved
     sources; 2014ApJ...797...27F uniform "to decrease side lobes and optimize angular resolution";
     2018A&A...616L...3B uniform for the long-baseline map).
   - Continuum and lines from the same data usually get different weighting, with lines on the more natural side:
     continuum robust 0.5 and lines natural (2016Natur.540..406B, 2017A&A...600A..72F, 2018ApJ...859..111H,
     2018MNRAS.475.4924K); continuum robust 0.5 and cube robust 2.0 (2024ApJ...972..111L); continuum robust 0 and
     CO robust 2 (2016ApJ...823L..27H); continuum -2 and lines 0.5 (2017ApJ...840...60B). The reverse split exists
     but is rare in the pack (2017MNRAS.472.1239B, 2014A&A...572L...9R).
3. **Add a taper or uv cut when the goal needs a different beam than the weighting gives.**
   - Taper for detection or to recover extended flux: 0.27" chosen by maximizing [C II] S/N over 0.01-0.50"
     (2020MNRAS.493.4294B); 0.7" after testing 0.4-0.8" (2017ApJ...851..145M); several tapers, highest S/N adopted
     (2016ApJ...833...12R); `outertaper=0.4"` recovered 841 vs 512 Jy km/s in untapered regions (2018ApJ...866..117C).
   - Taper to match another dataset's beam: Band 4 tapered to the Band 7 beam for a spectral index map
     (2018A&A...619A.161C); ALMA tapered to an SMA-like 5.9"x3.0" beam (2015ApJ...814..143A); all data to a common
     4.2"x2.1" (2016ApJ...821..112K); common uv range 27-1310 klambda for all bands (2018A&A...616A..56A).
   - Inner uv cut to isolate compact sources: uv>100 klambda (2015ApJ...801...82H), >80 klambda
     (2014ApJ...796....1T), >160 klambda with superuniform (2017A&A...597A..32V); a 40 klambda inner cutoff chosen to
     minimize rms (2018AJ....155...47A).
4. **Pick the deconvolver.**
   - Compact or point-like emission, most line cubes: `deconvolver='hogbom'` (2025MNRAS.541.2540Z line cube,
     2024A&A...682A.166F, 2025ApJ...986L..22R, 2019A&A...630A..59B). Clark is the older equivalent
     (2023PSJ.....4..142C, 2019AJ....158...76C, 2015ApJ...814...22E).
   - Extended emission (disks, envelopes, cores, SZ, galaxies): `deconvolver='multiscale'` (2020ApJ...899...10T
     "to recover the extended emission", 2020ApJ...898..146M, 2018ApJ...852..122H). 2017ApJ...851...83C used
     standard CLEAN for compact sources and multiscale for extended and transition disks.
   - Wide fractional bandwidth or multi-band continuum, spectral index: `deconvolver='mtmfs'`, `nterms=2`
     (2018ApJ...852..122H, 2018ApJ...853..171G, 2024ApJ...963..164R, 2015ApJ...813..118M).
   - Non-CLEAN alternatives exist but are rare: maximum entropy (2014ApJ...796...82Z; uvmem in 2015ApJ...811...92C),
     sparse modeling (2020ApJ...895...84Y), SDI in GILDAS (2018A&A...614A..58B).
   - Some papers do not clean at all, for weak or unresolved signals: line cubes imaged dirty
     (2016ApJ...823L..10W), no ALMA deconvolution (2016ApJ...833...12R), zero iterations (2016ApJ...819...82S).
5. **Set multiscale scales from the beam, not by habit.** Common recipe: 0 (point), then about 1x and 3x the
   synthesized beam, sometimes 9x or more (2017A&A...602L..10O [0,1,3] beams; 2025ApJ...993...85Y [0,1,3] clean beam;
   2020ApJ...898..146M [0,1,3,9] beams; 2020MNRAS.496.4061D point plus 3, 6, 9 beams). In pixels, [0,5,10]
   (2026A&A...705A.198M), [0,6,18] (2020ApJ...899...10T), [0,5,20] (2024ApJ...963..164R). Largest scale should stay
   below the largest recoverable scale; 2016PASJ...68...88K found convergence for a largest scale of 40-50" with
   7m+12m data. See `references/parameters.md` for the full list.
6. **Mask.** Options seen: a polygon mask applied to all channels (2012ApJ...757..129R); Keplerian masks for disk
   lines (2018A&A...614A.106C, 2026A&A...705A.198M; `keplerian_mask` is named in 4 papers, pack aggregate);
   `usemask='auto-multithresh'` checked against a conservative user mask (2024ApJ...963..164R; also
   2024ApJ...968L..19F); boxes around sources above 5 sigma (2015ApJ...807..128S, 2016MNRAS.461.2944A); a fixed
   circular mask on the target (2025ApJ...986L..22R 10" diameter; 2024A&A...682A.166F 1.25"); no mask with
   `niter` 500-1000 (2019A&A...630A..59B).
7. **Set the stopping threshold.** The most common stated value in the pack is about 2x the rms (2014ApJ...792L...2C,
   2014ApJ...795L..30C, 2016ApJ...821L...8S, 2020MNRAS.496.4061D, 2024A&A...682A.166F, 2025ApJ...986L..22R;
   my count: 7 papers). Range seen 0.5 sigma (2016ApJ...829....6W, 2018A&A...619A..39F) to 4 sigma
   (2017A&A...597A..41G, 2026A&A...705A.198M). Use `gain=0.1` (2015ApJ...811...39I, 2017ApJ...844..123F); 0.05 for
   diffuse emission (2016PASJ...68...88K).
8. **Cell and image size.** Pixel about 1/5 of the beam (2026A&A...705A.198M states it); otherwise papers give an
   absolute cell (0.02" in 2025MNRAS.541.2540Z, 0.05" in 2019A&A...630A..59B, 0.1" in 2024ApJ...972..111L, 4 mas in
   2024ApJ...963..164R). Image size and cell are among the settings cards most often flag as not stated (43 cards
   for "image size and cell size", plus variants; pack aggregate). For mosaics use `gridder='mosaic'`
   (2020A&A...634A...9M). Bright sources outside the target field can be removed by imaging them jointly as a
   mosaic (2020A&A...642A..96P: noise fell from 11.8 to 7.3 uJy).
9. **Primary-beam correct** before any flux or size measurement (`impbcor` or `pbcor=True`; 2018ApJ...852..122H,
   2024ApJ...968L..19F, 2020ApJ...899...10T fits after primary-beam correction).
10. **Run the checks in Verification checks**, then record every setting (weighting, robust, taper, deconvolver,
    scales, threshold, mask, cell, CASA version) in the methods.

## Parameter defaults and ranges

Weighting counts: my count over the 390 papers with a weighting line in the pack key-parameter list (2012-2018);
a paper can appear in several rows.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Weighting, any natural mention | natural or `robust=2` | natural, robust 1.5-2 | 216 of 390 | 2017ApJ...846..108C, 2020ApJ...899...10T |
| Briggs robust (when a value is given) | 0.5 | -2 to 2 | 149 of 390 at 0.5 | 2018ApJ...866..117C, 2025ApJ...993...85Y |
| robust 0 | resolution-leaning | 0 | 46 of 390 | 2013Natur.493..191C, 2023PSJ.....4..142C |
| robust 1 | line cubes, sensitivity-leaning | 1.0 | 10 of 390 | 2015Natur.522..455C, 2025MNRAS.541.2540Z |
| Negative robust / uniform / superuniform | high-resolution maps | -2 to -0.5; uniform; superuniform `npixels=2` | 8 / 29 / 9 of 390 | 2017A&A...603A..10B, 2018ApJ...854..177V, 2017ApJ...849...56A |
| Robust value not given | (Briggs stated, no number) | n/a | 20 of 390 | 2015ApJ...798...85P, 2016A&A...596A..75S |
| uv taper | none unless detection or matching | 0.03" to 10"; 50-1000 klambda | taper mentioned in about 70 of 432 | 2020MNRAS.493.4294B, 2018A&A...619A.161C |
| Deconvolver | hogbom for compact/lines; multiscale for extended | hogbom, clark, multiscale, mtmfs, MEM, SDI | key-param list: multiscale 21, hogbom 12, mtmfs 6, clark 3, MEM 2, SDI 1 | 2020ApJ...898..146M, 2025MNRAS.541.2540Z |
| `nterms` | 2 | 2 | 6 in key-param list | 2018ApJ...853..171G, 2015ApJ...813..118M |
| Multiscale scales | [0, 1x, 3x beam] | up to 9-15x beam | 9 with explicit scales in key-param list, more in excerpts | 2017A&A...602L..10O, 2018ApJ...857...19F |
| Threshold | 2x rms | 0.5 to 4 sigma | 7 at about 2x rms (my count, whole pack) | 2020MNRAS.496.4061D, 2024A&A...682A.166F |
| Loop gain | 0.1 | 0.05-0.1 | 5 state it | 2015ApJ...811...39I, 2016PASJ...68...88K |
| Cell | about 1/5 beam | 4 mas to 0.4" | rarely stated | 2026A&A...705A.198M, 2020A&A...642A..96P |
| `niter` | until threshold | 500-1000 (no mask); 1000 with 4x rms | few state it | 2019A&A...630A..59B, 2017A&A...597A..41G |

## Software

Pack aggregates over all 1121 papers (software named in the matched steps):

| Tool | Count | Used for |
|---|---|---|
| CASA | 813 | calibration and imaging; `tclean` named 70 times, "CASA tclean" 14, older `clean` 6 |
| GILDAS (+ GILDAS/MAPPING 3) | 23 | Hogbom/Clark/SDI cleaning, mostly European groups (2018A&A...614A..58B, 2024A&A...689A.317G, 2020MNRAS.495..943H) |
| MIRIAD (+ "Miriad" 7) | 20 | older or SMA-combined imaging |
| AIPS | 19 | VLA companion data and JMFIT source fits |
| uvcontsub | 10 | continuum subtraction before cube imaging |
| CASA simobserve | 7 | artifact and missing-flux tests (2019ApJ...874...89C, 2020ApJ...899...10T, 2019AJ....158...76C) |
| imfit / CASA imfit | 5 / 7 | Gaussian sizes and fluxes on the cleaned image |
| feather | 4 | single-dish combination (2018MNRAS.475..448T used a custom feather of clean components) |
| keplerian_mask | 4 | disk line masks |
| uvmem | 4 | maximum-entropy imaging (2015ApJ...811...92C) |
| bettermoments | 3 | moment maps after imaging |

## Pitfalls

- **Missing flux.** The most frequent imaging limitation authors admit (14 of the 120 limitation lines in the pack
  mention resolved-out or missing flux, my count). Examples: high-resolution data resolve out 74% of the CO
  (2020MNRAS.496.4061D); more than 80% missing relative to single dish (2020ApJ...899...10T); robust 0.5 missed
  extended [C II] that robust 2 recovered (2024A&A...682A.166F); continuum flux underestimated without single-dish
  data (2018MNRAS.475..448T). Do not quote total flux from a high-resolution or low-robust image without a check.
- **Fake substructure.** Clean on a smooth source can produce clumps. 2019ApJ...874...89C showed that a flat-center
  profile observed with simobserve produces substructure like the observed one; 2020ApJ...899...10T state that
  low-contrast continuum substructure cannot be distinguished from artifacts.
- **Image-plane sizes depend on weighting and beam.** Widths comparable to the beam are upper limits
  (2020ApJ...888L..28S); vertical structure smaller than the beam was treated with caution (2018MNRAS.475.4924K).
- **Mismatched beams across bands or tracers.** Spectral indices and line ratios need matched uv coverage or a
  common taper (2018A&A...619A.161C, 2018A&A...616A..56A).
- **Sidelobes from bright off-target sources** raise the noise above the expected value (2020A&A...642A..96P).
- **Non-CLEAN imaging residuals.** Sparse-modeling images self-calibrated with MS-CLEAN models had larger,
  asymmetric residuals (2020ApJ...895...84Y).
- **Underreporting.** Settings cards flag as not stated (pack aggregate): CASA version 118, image and cell size 43
  (plus 13 and 11 for variant phrasings), primary-beam correction details 22, clean threshold/masks/cell/image size
  10. Robust value missing in 20 of 390 weighting lines (my count), and some cards note "robust value not given"
  (2018A&A...614A..58B, 2024A&A...689A.317G, 2020ApJ...888L..28S).
- **Moving targets.** Shift to a common phase center before combining epochs (`fixvis`/`fixplanets` for TW Hya
  proper motion, 2018ApJ...852..122H; Titan regridded to its rest frame, 2019AJ....158...76C).
- **Spectral gridding.** 2012ApJ...757..129R forced a channel center onto the systemic velocity so line wings are
  sampled symmetrically; channel width choices affect sensitivity as much as weighting (2018A&A...614A..58B degraded
  channels to 0.43 km/s to raise S/N).

## Verification checks

What papers did (cite the one you follow):

- **Compare flux with single-dish or lower-resolution data.** ACA vs combined cube 174 vs 161 Jy km/s
  (2020MNRAS.496.4061D); SCUBA-2 vs ALMA plus a 180-degree rotation subtraction (2018MNRAS.475.4924K); APEX
  profiles, under 20% filtered (2018A&A...614A..58B); CARMA flux (2015ApJ...798..124R); Herschel total CO(6-5)
  (2018ApJ...866..117C).
- **Re-image with a taper or more natural weighting** and see whether flux or a source appears
  (2017ApJ...846..108C, 2024A&A...682A.166F, 2018ApJ...856..118H taper for flux check).
- **Simulated observations** with `simobserve` + `tclean` of a smooth model to test whether substructure is an
  artifact (2019ApJ...874...89C 100 hour-angle realizations; 2020ApJ...899...10T).
- **Alternative imaging settings agree:** codes, masks and weightings compared in four test regions
  (2020MNRAS.495..943H); auto-mask checked with a conservative user mask (2024ApJ...963..164R); other weightings
  tested (2017A&A...602L..10O robust -1 and uniform; 2018A&A...610A..24F chose uniform after trying schemes;
  2017MNRAS.465.4390B robust 0.5 as a size check).
- **Multiscale scale choice** by minimal residuals and maximal recovered flux, and insensitivity to small-scale bias
  below 0.8 (2016PASJ...68...88K).
- **Image-plane vs uv-plane values agree** (uvmodelfit vs imfit and sextractor, 2017ApJ...846..108C).
- **Residuals and overcleaning:** residuals inspected (2026A&A...705A.198M); no overcleaned regions
  (2024A&A...689A.317G); dirty-beam sidelobes under 10% (2015ApJ...814..143A).
- **Noise and dynamic range against expectation:** measured rms vs expected sensitivity (2020A&A...642A..96P);
  dynamic range about 580 after self-calibration (2023PSJ.....4..142C); self-calibrated fluxes within 5% across
  datasets (2018ApJ...852..122H).
- **Measurement sensitivity to clipping:** moving a clip from 2 to 1.3 sigma changed flux by -15% to +10%
  (2017ApJ...851...18L).

What a careful referee adds:

- Ask for the largest recoverable scale against the source size, and a missing-flux estimate when they are close.
- Ask that every robust value, taper, threshold, mask method, cell and CASA version be stated.
- For claimed substructure or clumps, ask for either a simulated observation or the feature's persistence across two
  weightings or two deconvolvers.
- For spectral indices and line ratios, ask that both images share uv range or a common restoring beam.
- For non-detections, ask that the limit come from a natural or tapered image, with the aperture stated.

## Source cards

Full list: `references/sources.md` (1121 papers). Longer parameter lists: `references/parameters.md`.
Most informative for imaging choices:

- 2016PASJ...68...88K: multiscale scale search, gain 0.05, small-scale bias test, SZ with 7m+12m.
- 2019ApJ...874...89C: ACA+12m joint multiscale, robust 0.5 with 1.5" taper, simobserve artifact test.
- 2020ApJ...899...10T: natural multiscale for cores, simobserve check, >80% missing flux.
- 2024A&A...682A.166F: robust 2 vs 0.5 and taper test for extended [C II].
- 2020MNRAS.493.4294B: natural weighting and taper chosen by S/N maximization for a z=8.31 detection.
- 2020MNRAS.496.4061D: two cubes at robust 0.5 and 0.1, multiscale in beam units, 74% resolved out.
- 2025MNRAS.541.2540Z: robust chosen after trials to resolve the sphere of influence; Hogbom cube.
- 2018ApJ...852..122H: per-tracer robust, multiscale in arcsec, mtmfs spectral index, fixvis for proper motion.
- 2024ApJ...963..164R: mtmfs with auto-multithresh checked by a user mask; superuniform to match beams.
- 2026A&A...705A.198M: three-stage tclean, Keplerian masks, robust by disk orientation, pixel 1/5 beam.
- 2018ApJ...866..117C: outertaper recovering extended CO flux.
- 2018A&A...619A.161C: taper to match beams for a spectral index map.
- 2020ApJ...895...84Y: sparse modeling vs MS-CLEAN fidelity.
- 2018MNRAS.475..448T: 12m+7m+TP custom feather combination.
- 2020A&A...642A..96P: mosaic imaging to remove an off-field source's sidelobes.
- 2017ApJ...846..108C: natural weighting, taper test, uv vs image fits.
- 2020MNRAS.495..943H: GILDAS vs CASA, masks and weightings compared.
- 2018MNRAS.475.4924K: robust 0.5 continuum, natural CO, single-dish flux check.
- 2016ApJ...828...46A: robust chosen by whether the source is resolved.
- 2017ApJ...851...83C: deconvolver chosen by source extent.

=== references/parameters.md ===
# Imaging parameters seen in the pack (imaging-choices)

Values copied from the evidence pack (key-parameter list, 2012-2018, plus the 40 detailed excerpts). One line per
paper; check the card before reusing a value.

## Multiscale scales

| Scales | Units | Paper | Context |
|---|---|---|---|
| 0, 1, 3 | x synthesized beam | 2017A&A...602L..10O | mtmfs nterms=2, robust 0 |
| 0, 1, 3 | x CLEAN beam | 2025ApJ...993...85Y | disk continuum, robust 0.5 |
| about 1 and 3 | x beam FWHM | 2015ApJ...813..118M | nearby galaxy continuum, nterms=2 |
| 0, 1, 3, 9 | x expected beam | 2020ApJ...898..146M | debris belt, 12m+ACA, natural |
| point, 3, 6, 9 | x beam | 2020MNRAS.496.4061D | CO(2-1) cube, threshold 2x rms |
| 1, 2, 4, 8 (plus point) | x beam | 2017ApJ...836..223W | MSMFS, natural |
| 1, 2, 5, 10, 15 | x beam | 2018ApJ...857...19F | GMC cube, gain 0.1, 100 iterations per cycle |
| 0, 5, 10 | pixels (pixel = beam/5) | 2026A&A...705A.198M | debris CO, third tclean pass |
| 0, 6, 18 | pixels | 2020ApJ...899...10T | prestellar cores, natural |
| 0, 6, 18 | pixels | 2017ApJ...840...60B | continuum robust -2 |
| 0, 5, 15 | pixels | 2017ApJ...837L..29H | continuum |
| 0, 5, 20 | pixels (4 mas) | 2024ApJ...963..164R | mtmfs, robust 1 |
| 0, 10, 25 | pixels (0.25") | 2017PASJ...69...18T | line cubes, robust 0.1-0.4 |
| 0, 7, 21 / 0, 5, 15 | pixels (6 mas) | 2017ApJ...842L..24A | CO and SiO lines |
| 0, 0.06, 0.15, 0.3, 0.6 | arcsec | 2018ApJ...852..122H | Band 6 continuum, robust 0.5 |
| 0, 0.2, 0.4, 0.8, 1.6, 3.2 | arcsec | 2018ApJ...852..122H | 12CO cube, robust 1.0 |
| 0, 0.3, 0.9 | arcsec | 2016ApJ...831L..12K | disk continuum, robust 0.5 |
| 0, 0.3, 0.9 | arcsec | 2020ApJ...895...84Y | MS-CLEAN reference for sparse modeling |
| 0, 100, 300 / 0, 50, 150 | mas | 2016ApJ...829L..35T | Band 4 / Band 6 |
| 0, 2, 6, 18 | arcsec | 2019ApJ...874...89C | ACA+12m, taper 1.5" |
| 0, 5, 8, 13, 20, 30, 45 | arcsec | 2016PASJ...68...88K | SZ, small-scale bias 0.4, gain 0.05 |
| 0, 1, 5, 10, 15 | x pixel (0.2") | 2018MNRAS.475..448T | 12m+7m+TP, natural |

## Clean thresholds and stopping

| Threshold | Paper | Notes |
|---|---|---|
| 2x rms | 2014ApJ...792L...2C, 2014ApJ...795L..30C | Hogbom, per channel |
| 2x expected rms | 2016ApJ...821L...8S | Hogbom |
| 2x dirty-channel rms | 2020MNRAS.496.4061D | multiscale cube |
| 2x rms of each cube | 2024A&A...682A.166F | Hogbom, 1.25" mask |
| 2x rms | 2025ApJ...986L..22R | Hogbom, 10" mask, natural |
| about 2 sigma (0.5 mJy) | 2015ApJ...814...22E | Clark, continuum |
| 2.5 sigma | 2016PASJ...68...88K | multiscale, diffuse |
| 3x rms | 2017ApJ...839...43O, 2018A&A...620A.115B | Hogbom; natural |
| 3 sigma, Niter 500-1000, no mask | 2019A&A...630A..59B | archival [C II] cubes |
| 3 sigma in boxes around peaks | 2017ApJ...850...83F | continuum survey |
| 4x rms, niter 1000 | 2017A&A...597A..41G | natural |
| 6 sigma mask, clean to 4 sigma | 2016ApJ...832..142Z | CO(1-0) |
| 4 rms | 2026A&A...705A.198M | Keplerian mask |
| 1.5 sigma | 2017ApJ...835...98U, 2017ApJ...843L..35W, 2025MNRAS.541.2540Z | deep cleaning |
| 1.5 sigma in boxes around >5 sigma sources | 2015ApJ...807..128S, 2016MNRAS.461.2944A | survey continuum |
| 0.5 sigma | 2016ApJ...829....6W, 2018A&A...619A..39F | GILDAS-style deep clean |
| residual max sigma/2, about 4000-5000 components | 2024A&A...689A.317G | GILDAS Hogbom |

## Tapers and uv cuts

| Setting | Paper | Purpose |
|---|---|---|
| Gaussian 0.27" (scanned 0.01-0.50") | 2020MNRAS.493.4294B | maximize [C II] S/N |
| 0.7" (tested 0.4-0.8") | 2017ApJ...851..145M | detection |
| several tapers, highest S/N adopted | 2016ApJ...833...12R | size measurement |
| `outertaper=0.4"` | 2018ApJ...866..117C | extended CO flux |
| 1.5" with robust 0.5 | 2019ApJ...874...89C | ACA+12m core |
| 2" Gaussian, robust 2 | 2015ApJ...798..124R | debris disk flux |
| 10" | 2020ApJ...898..146M | large-scale belt image |
| 1.2" for common-resolution stack | 2019A&A...630A..59B | stacking test |
| 0.3" tested, not adopted | 2024A&A...682A.166F | no extra emission recovered |
| Band 4 to Band 7 beam | 2018A&A...619A.161C | spectral index |
| common 27-1310 klambda | 2018A&A...616A..56A | multi-band matching |
| uv > 100 klambda | 2015ApJ...801...82H, 2014PASJ...66..106H | compact sources |
| baselines < 40 klambda excluded (minimizes rms) | 2018AJ....155...47A | continuum |
| baselines > 2.5 km only, uniform | 2018A&A...616L...3B | long-baseline map |
| uv distances < 50 m excluded, superuniform | 2018ApJ...854...56L | high resolution |

=== EVIDENCE PACK (imaging-choices) ===
# Evidence pack: Interferometric imaging parameter choices (tclean) (`imaging-choices`)

Scope: weighting, robust, deconvolver, taper, masking and thresholds by science case

Built from 1121 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `tclean|\bclean\b|briggs|robust|deconvol|multiscale|mtmfs|uv[- ]?taper|weighting`; processing fields: imaging.weighting_robust, imaging.deconvolver, imaging.uv_taper, imaging.multiscale_scales
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- star_formation: 360
- protoplanetary_disks: 279
- high_z_galaxies: 271
- astrochemistry: 211
- nearby_galaxies: 210
- agn_and_quasars: 202
- milky_way_ism: 113
- evolved_stars: 51
- stellar_physics: 46
- debris_disks: 45
- galaxy_clusters_and_sz: 31
- solar_system: 21
- exoplanets: 21
- transients: 13
- cosmology: 13

### Software named in the matched steps
- casa: 813
- tclean: 71
- miriad: 27
- gildas: 23
- aips: 19
- casa tclean: 14
- uvcontsub: 11
- casa clean: 8
- casa imfit: 8
- casa simobserve: 7
- clean: 7
- imfit: 6
- emcee: 6
- radmc-3d: 6
- statcont: 6
- gaincal: 5
- mcfost: 5
- feather: 5
- keplerian_mask: 4
- uvmem: 4
- vis_sample: 4
- imsmooth: 4
- casa immoments: 3
- gildas/mapping: 3
- cprops: 3
- galfit: 3
- difmap: 3
- bettermoments: 3
- aips jmfit: 3
- phangs-alma pipeline: 3
- lime: 3
- uvmodelfit: 3
- casa uvmodelfit: 2
- sextractor: 2
- clumpfind: 2
- mpfit: 2
- applycal: 2
- uvmultifit: 2
- frankenstein: 2
- scipy: 2

### Fitting methods (most common phrasings)
- 2D Gaussian: 4
- Gaussian fit: 3
- single Gaussian: 2
- Gaussian profile, chi-square fit in uv plane: 1
- Gaussian fit; errors from fit and Monte Carlo injection of model profiles in random cube regions: 1
- chi2 minimisation; peak flux fixed: 1
- 2D Gaussian in image plane: 1
- emcee, uniform priors, median and 16/84 percentiles: 1
- Manual exploration of many configurations; best-fit model chosen by comparison with data and previous results, no forma…: 1
- emcee ensemble sampler; chi2 likelihood; priors not stated: 1
- 2D Gaussian fit: 1
- imfit single-component Gaussian: 1
- Gaussian line profile; Monte Carlo for uncertainties: 1
- Nonlinear least squares with MPFIT; 1σ errors from covariance matrix: 1
- chi2 minimization; errors from inverse Hessian plus rms propagation (1 sigma): 1
- least squares, linear in visibility space: 1
- Point source fit with position fixed to Stokes I: 1
- Point source model with imfit: 1
- Voigt function fit to derivative of CLV: 1
- Least-squares Gaussian fit to radial profiles: 1
- chi^2 downhill simplex; at least nine free parameters (M_BH, Upsilon_H, x_c, y_c, i, Gamma, v_sys, sigma_turb, f_0); un…: 1
- grid search minimizing Cash statistic C=-2lnL with Poisson likelihood: 1
- Hyperparameter and geometry priors (Table 2) sampled in 5000 fits; 16-84th percentile as 1 sigma: 1
- Gaussian fit to CO spectrum: 1
- Iterative Tukey biweight robust least squares of f_F658N vs f_F555W: 1
- uvmodelfit chi^2 minimization, single uniform disk: 1
- MGE fit: 1
- Gaussian linewidths corrected for instrumental broadening: 1
- emcee affine-invariant ensemble sampler, Gaussian likelihood exp(-chi2/2) with pixel-correlation reweighting by l_pix^2…: 1
- emcee sampling of likelihood in visibilities; 1 sigma range of posterior: 1
- straight-line fit: 1
- Gaussian per slice: 1
- Iterative multiplicative correction of surface density (no sampler): 1
- Gaussian least-squares fit: 1
- Non-linear least squares, b free or fixed 0.5: 1
- Free parameters: amplitudes and widths: 1
- Elliptical Gaussian least-squares (details not stated): 1
- GALFIT least squares, sky fixed to zero, clean Gaussian beam as PSF: 1
- Ellipse fit to ring peaks; Gaussian fit for FWHM without beam deconvolution: 1
- 2D Nuker profile convolved with clean beam (AGE-PRO XI): 1

### Validation checks used
- Visual inspection of residuals: 2
- Continuum fluxes of self-calibrated images agree within 5% within each band; compared with published images: 1
- Compared with 190 GHz spectral index of Tsukagoshi et al.: 1
- Imaged without continuum subtraction; integration limits changed flux <0.1%: 1
- Consistent with imfit and sextractor on cleaned image: 1
- Fit errors consistent with Monte Carlo errors: 1
- Residuals show no significant fragments; simulated images reproduce similar substructure: 1
- Compared with Herschel total flux: 1
- Dust-derived M_mol consistent with CO-derived: 1
- Two continuum bands compared for MC1 and MC35: 1
- MC31 real vs synthetic residual comparison: 1
- velocity range gives highest S/N and agrees with by-eye inspection: 1
- uncertainty in C not included, could vary by factor of two: 1
- Cleaned with conservative user mask as check: 1
- Results insensitive to ±5 deg change of 30 deg: 1
- SNR improvement of 1.2 over non-self-calibrated image: 1
- inclination compared with CO kinematic value of Hales et al.: 1
- disk-averaged T compared with T Tauri scaling (~20 K): 1
- Total fluxes from visibility amplitude 3.3 Jy vs 3.2 Jy: 1
- Ideal NRMSE curve from convolved reference image: 1
- Checked cube without uvcontsub; substructure persists: 1
- First-order polynomial continuum did not significantly affect results: 1
- Repeated with cubes tapered to 1.2 arcsec: 1
- Flux compared with APEX profiles; <20% flux lost: 1
- Comparison of predicted channel maps and PV diagrams with data; similarity to Red Rectangle, IW Car: 1
- Independent blind check of data reduction by a coauthor: 1
- Extreme dust-temperature models tested; completeness analysis: 1
- Tested atmospheric CO, flat Tsys re-calibration, and continuum subtraction variations; wings persist: 1
- Compared combined-cube flux with ACA total flux (174±17 vs 161±16 Jy km/s): 1
- MGE-based potential gives same results: 1
- Compared with SCUBA-2 flux; 180-degree rotation subtraction consistent with noise: 1
- Delta chi2 and BIC model comparison; residual images: 1
- weighting chosen after trials to resolve SoI while retaining S/N: 1
- Alternative robust=0.5 and taper tested on [CII]: 1
- Tested direct Fourier-plane feather combination; no clear improvement: 1
- Contribution functions for altitude sensitivity; comparison with CIRS retrievals: 1
- Converged for largest scale 40-50"; insensitive to bias <0.8: 1
- Dirty beam sidelobes <10 % of main beam: 1
- Compared with ground-state results of El-Abd et al. (Tex 135 K, N 1.24e17): 1
- error is rms far from the source: 1

### Key parameters and settings (bibcode: value)
- 2018ApJ...852..122H: robust=0.5; scales 0, 0.06, 0.15, 0.3, 0.6 arcsec
- 2018ApJ...852..122H: nterms=2, robust=0, i=5 deg, PA=152 deg
- 2018ApJ...852..122H: integration -1.91 to 7.59 km/s; 3 sigma clip
- 2018ApJ...852..122H: processing.imaging.weighting_robust = Band 6 image robust=0.5; combined spectral index image robust=0; 12CO robust=1.0; 13CO robust=0
- 2018ApJ...852..122H: processing.imaging.deconvolver = multi-scale CLEAN
- 2018ApJ...852..122H: processing.imaging.multiscale_scales = 12CO: 0, 0.2, 0.4, 0.8, 1.6, 3.2 arcsec; Band 6: 0, 0.06, 0.15, 0.3, 0.6 arcsec
- 2017ApJ...846..108C: line flux contained within 2'' circular radius
- 2017ApJ...846..108C: processing.imaging.weighting_robust = natural weighting (both bands)
- 2017ApJ...846..108C: processing.imaging.uv_taper = tapering tried to test for resolved-out ALESS67.2; parameters not stated
- 2019ApJ...874...89C: robust 0.5, taper 1.5", scales [0,2,6,18]"
- 2019ApJ...874...89C: 100 models, Cycle 1 configuration 2, baselines >13 klambda
- 2019ApJ...874...89C: processing.imaging.weighting_robust = robust 0.5
- 2019ApJ...874...89C: processing.imaging.deconvolver = multi-scale clean
- 2019ApJ...874...89C: processing.imaging.uv_taper = 1.5"
- 2019ApJ...874...89C: processing.imaging.multiscale_scales = [0, 2, 6, 18] arcsec
- 2018ApJ...866..117C: robust = 0.5; outertaper = 0.4"
- 2018ApJ...866..117C: dV deconvolved with 13.5 km/s channel; 10 km/s rotation removed; flux x1.731 for total
- 2018ApJ...866..117C: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2018ApJ...866..117C: processing.imaging.uv_taper = outertaper = 0.4" for 0.4" x 0.4" beam
- 2020ApJ...899...10T: scales 0,6,18 pix; 1'' pixels; natural weighting; 3 sigma detection threshold
- 2020ApJ...899...10T: p=2; R_flat 8000,2500,1500,900,300 au; aspect ratios 1.0 and 1.8; kappa=0.005, Td=10 K
- 2020ApJ...899...10T: processing.imaging.weighting_robust = Natural
- 2020ApJ...899...10T: processing.imaging.deconvolver = multiscale
- 2020ApJ...899...10T: processing.imaging.multiscale_scales = 0, 6, 18 pixels
- 2020MNRAS.493.4294B: moment 0 integrated over -140 to +140 km/s
- 2020MNRAS.493.4294B: r_1/2 = deconvolved major axis, 1.15 ± 0.35 kpc
- 2020MNRAS.493.4294B: processing.imaging.weighting_robust = natural weighting
- 2020MNRAS.493.4294B: processing.imaging.uv_taper = Gaussian 0.27" FWHM (convolution of natural maps), chosen by maximizing S/N over 0.01-0.50"
- 2024ApJ...963..164R: scales 0,5,20 pix; 4 mas pixels; sidelobethreshold 2.0
- 2024ApJ...963..164R: processing.imaging.weighting_robust = Briggs robust 1.0 (Band 6); superuniform (Band 3)
- 2024ApJ...963..164R: processing.imaging.deconvolver = MTMFS, 2 Taylor terms
- 2024ApJ...963..164R: processing.imaging.multiscale_scales = 0, 5, 20 pixels
- 2025ApJ...993...85Y: solint=inf, robust 0.5
- 2025ApJ...993...85Y: 100 walkers, 500 steps, 250 burn-in
- 2025ApJ...993...85Y: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2025ApJ...993...85Y: processing.imaging.deconvolver = multi-frequency synthesis with multi-scale, scales [0,1,3] x theta_cl
- 2020ApJ...895...84Y: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2020ApJ...895...84Y: processing.imaging.multiscale_scales = [0, 0.3, 0.9] asec
- 2014ApJ...797...27F: processing.imaging.weighting_robust = SM1 uniform; SM1N natural
- 2014ApJ...797...27F: processing.imaging.deconvolver = SM1: multi-frequency synthesis; SM1N: multi-scale multi-frequency synthesis
- 2014ApJ...797...27F: processing.imaging.uv_taper = H2D+ tapered to 1.3 arcsec
- 2024ApJ...972..111L: robust=0.5, cell 0.1"
- 2024ApJ...972..111L: ~0.8" aperture and peak pixel 0.1"
- 2024ApJ...972..111L: processing.imaging.weighting_robust = continuum robust=0.5; cube robust=2.0
- 2024ApJ...972..111L: processing.imaging.deconvolver = continuum: mtmfs; cube: hogbom
- 2019A&A...630A..59B: Niter 500-1000, threshold 3 sigma
- 2019A&A...630A..59B: processing.imaging.weighting_robust = natural weighting
- 2019A&A...630A..59B: processing.imaging.deconvolver = Hogbom
- 2019A&A...630A..59B: processing.imaging.uv_taper = tapering to 1.2 arcsec for common-resolution stack test; sources <0.6'' not used
- 2018A&A...614A..58B: Channels degraded to 0.43 km/s
- 2018A&A...614A..58B: Inclination 70 deg to plane of sky axis, PA -15 deg, X(13CO)=1.5e-5, X(12CO)=1.5e-4
- 2018A&A...614A..58B: processing.imaging.weighting_robust = Natural (adopted) and robust (value not given)
- 2018A&A...614A..58B: processing.imaging.deconvolver = Hogbom and SDI tried; SDI used for final data
- 2015Natur.522..455C: Robust = 1
- 2015Natur.522..455C: processing.imaging.weighting_robust = Briggs, Robust = 1
- 2012ApJ...757..129R: systemic LSR velocity +2.87 km/s forced onto a channel center
- 2012ApJ...757..129R: processing.imaging.weighting_robust = natural weighting
- 2012ApJ...757..129R: processing.imaging.deconvolver = CLEAN
- 2020MNRAS.496.4061D: robust 0.5 / 0.1; 2 km/s channels; 0.015" pixels; clean threshold 2x RMS
- 2020MNRAS.496.4061D: processing.imaging.weighting_robust = Briggs robust 0.5 (three long-baseline tracks); robust 0.1 (all tracks)
- 2020MNRAS.496.4061D: processing.imaging.deconvolver = multi-scale clean, scales for point sources and 3, 6, 9 times the beam; threshold 2x dirty-channel RMS
- 2020MNRAS.496.4061D: processing.imaging.uv_taper = continuum tapered, beam 0.67"x0.46"
- 2018MNRAS.475.4924K: 40 walkers, 1000 steps, ~100 burn-in; data averaged to 10 s and four channels per SPW; weights recomputed with statwt; reweighting 1/2.5
- 2018MNRAS.475.4924K: processing.imaging.weighting_robust = Briggs robust = 0.5 (continuum); natural weighting for CO cube
- 2025MNRAS.541.2540Z: pixel 0.02", 200x200 pixels, robust 1.0
- 2025MNRAS.541.2540Z: processing.imaging.weighting_robust = Briggs robust 1.0 (line); robust 0.5 (continuum)
- 2025MNRAS.541.2540Z: processing.imaging.deconvolver = Högbom
- 2015ApJ...813..118M: robust=0.5, nterms=2
- 2015ApJ...813..118M: processing.imaging.weighting_robust = Briggs robust=0.5
- 2015ApJ...813..118M: processing.imaging.multiscale_scales = scales ≈1 and 3 times synthesized beam FWHM
- 2024A&A...682A.166F: robust 2.0, 0.05'' pixels, threshold 2 rms, 1.25'' mask
- 2024A&A...682A.166F: processing.imaging.weighting_robust = Briggs, robust = 2.0
- 2024A&A...682A.166F: processing.imaging.deconvolver = Hogbom, threshold 2x rms of each cube
- 2024A&A...682A.166F: processing.imaging.uv_taper = 0.3'' taper tested in appendix; not adopted
- 2018MNRAS.475..448T: natural weighting, 0.2 arcsec pixel, multiscale [0,1,5,10,15]
- 2018MNRAS.475..448T: processing.imaging.weighting_robust = natural weighting
- 2018MNRAS.475..448T: processing.imaging.deconvolver = multi-scale clean, scales [0,1,5,10,15] x pixel size
- 2019AJ....158...76C: pixel 0.025'', mask 1.3''
- 2019AJ....158...76C: Wedges phi=45-135 and 225-315 deg
- 2019AJ....158...76C: processing.imaging.weighting_robust = Natural for maps; Briggs robust = 0 for limb profiles
- 2016PASJ...68...88K: loop gain 0.05, threshold 0.03 mJy
- 2016PASJ...68...88K: processing.imaging.weighting_robust = natural
- 2016PASJ...68...88K: processing.imaging.deconvolver = Multi-Scale CLEAN, scales [0,5,8,13,20,30,45]", small-scale bias 0.4, gain 0.05, threshold 0.03 mJy (2.5σ)
- 2020A&A...634A...9M: robust 0.5, hogbom, gridder mosaic
- 2020A&A...634A...9M: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2020A&A...634A...9M: processing.imaging.deconvolver = hogbom
- 2015ApJ...814..143A: processing.imaging.deconvolver = Högbom clean, no support
- 2015ApJ...814..143A: processing.imaging.uv_taper = Taper to simulate 5.9" x 3.0" beam (SMA comparison)
- 2019ApJ...882..118X: Briggs robust 0.5 (B4, B6), 0.0 (B7)
- 2019ApJ...882..118X: dV = 2.72 km/s, Vlsr = -6.90 km/s fixed
- 2019ApJ...882..118X: processing.imaging.weighting_robust = Briggs, robust 0.5 (Bands 4 and 6), 0.0 (Band 7)
- 2017A&A...600A...8D: uniform weighting; 301.99 GHz; self-cal 1 h
- 2017A&A...600A...8D: processing.imaging.weighting_robust = uniform weighting, central frequency 301.99 GHz
- 2020MNRAS.495..943H: 20,000 clean iterations in illustrated GILDAS channel; brightness cut 0.08 Jy/beam
- 2020MNRAS.495..943H: processing.imaging.weighting_robust = Natural weighting adopted (robust 1.0 also tested)
- 2020ApJ...898..146M: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...898..146M: processing.imaging.deconvolver = multiscale
- 2020ApJ...898..146M: processing.imaging.uv_taper = 10'' taper for large-scale image
- 2020ApJ...898..146M: processing.imaging.multiscale_scales = 0, 1, 3, 9 times synthesized beam size
- 2026A&A...705A.198M: robust 0.5 or 2; scales [0,5,10]; pixel 1/5 beam
- 2026A&A...705A.198M: processing.imaging.weighting_robust = Briggs robust 0.5 for gas-bearing non-edge-on; robust 2 for edge-on HD 32297, HD 131488 and gas-free
- 2026A&A...705A.198M: processing.imaging.deconvolver = multiscale in third iteration
- 2026A&A...705A.198M: processing.imaging.multiscale_scales = [0,5,10] pixels
- 2020A&A...642A..96P: pixel 0.4"; RMS 11.8 uJy vs expected 8 uJy
- 2020A&A...642A..96P: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...888L..28S: processing.imaging.weighting_robust = Briggs weighting (robust not stated)
- 2020ApJ...888L..28S: processing.imaging.deconvolver = CLEAN with Clark algorithm
- 2019ApJ...876L..10E: robust 0.5, 2400 pixels at 0.03 arcsec
- 2019ApJ...876L..10E: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2020ApJS..251...14H: kernel sigma = 14 pixels (~7'')
- 2020ApJS..251...14H: min value = 3x global noise (3 MJy/sr); min pixels ~ half average beam; min significance = global low noise
- 2020ApJS..251...14H: masses from flux assuming Td = 20 K
- 2020ApJS..251...14H: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2020ApJS..251...14H: processing.imaging.multiscale_scales = [0, 3, 9, 27]
- 2025ApJ...986L..22R: 10'' mask, threshold 2x rms
- 2025ApJ...986L..22R: processing.imaging.weighting_robust = natural weighting
- 2025ApJ...986L..22R: processing.imaging.deconvolver = Högbom
- 2025ApJ...986L..22R: processing.imaging.uv_taper = 2'' Gaussian taper for March 17 CO image
- 2024A&A...689A.317G: processing.imaging.weighting_robust = robust weighting (value not given); natural weighting for SPW 27 and 29 in Band 6 and low-res maps
- 2024A&A...689A.317G: processing.imaging.deconvolver = Hogbom; ~4000 components first pass, 5000 final; stop at sigma_p/2
- 2015ApJ...798..124R: processing.imaging.weighting_robust = natural weighting, Briggs robust = 2
- 2015ApJ...798..124R: processing.imaging.uv_taper = Gaussian uv-taper, on-sky FWHM 2 arcsec
- 2024ApJ...968L..19F: Briggs robust 0.5
- 2024ApJ...968L..19F: processing.imaging.weighting_robust = Briggs, robust 0.5
- 2023PSJ.....4..142C: Briggs robust 0.0, Clark deconvolver, solint down to 2 s
- 2023PSJ.....4..142C: processing.imaging.weighting_robust = Briggs, robust = 0.0
- 2023PSJ.....4..142C: processing.imaging.deconvolver = Clark
- 2015ApJ...803...97S: processing.imaging.weighting_robust = natural weighting
- 2015ApJ...803...97S: processing.imaging.deconvolver = Hogbom
- 2016A&A...593A..61M: processing.imaging.weighting_robust = natural weighting (simulations)
- 2025A&A...696A.100G: processing.imaging.deconvolver = Högbom CLEAN
- 2020MNRAS.498L..87B: processing.imaging.weighting_robust = Briggs robust = 0.4
- 2020ApJ...895...64L: robust 0.0
- 2020ApJ...895...64L: amp solint 20 min, 14 solutions per pol per antenna, cross-hand phase fixed
- 2020ApJ...895...64L: processing.imaging.weighting_robust = robust = 0.0
- 2024ApJ...970...56P: Briggs 0 weighting
- 2024ApJ...970...56P: processing.imaging.weighting_robust = Briggs 0 (L band -0.5)
- 2014ApJ...792L...2C: processing.imaging.weighting_robust = natural
- 2014ApJ...792L...2C: processing.imaging.deconvolver = Högbom, flux threshold of 2x RMS
- 2014ApJ...795L..25R: beta = 1.2 ± 0.1 chosen
- 2015A&A...573L...4L: processing.imaging.weighting_robust = Briggs in Band 7; natural in Bands 3 and 9 (robust value not given)
- 2015ApJ...808L...1A: processing.imaging.weighting_robust = Astrometry: uniform weighting, spacings >1 km; 3C138 high-res image natural weight
- 2024ApJ...963....1O: natural weighting, 20 km/s channels, no taper
- 2024ApJ...963....1O: processing.imaging.weighting_robust = natural weighting adopted (Briggs tested, robust value not given)
- 2019MNRAS.488.1005P: natural weights, CASA v.5.2
- 2019MNRAS.488.1005P: processing.imaging.weighting_robust = natural
- 2014ApJ...784...78R: processing.imaging.weighting_robust = Briggs, robust 0.5
- 2017A&A...604A.115V: processing.imaging.weighting_robust = robust = 1.5 (Band 3), 2 (Band 7)
- 2014ApJ...790..160S: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2019ApJ...871....5T: robust = 0; scales [0, 0.12, 0.36] arcsec; 0.14'' restoring beam
- 2019ApJ...871....5T: r_pk=95 au, sigma_r=10 au, Sigma_d,0=1.84e-2 g cm^-2, h_d=9.8 au, a_max=1 mm, gas Sigma ~ r^-1 for 8-320 au, h_g=13.2 au (r/95 au)^1.25, gas-to-dust 100
- 2019ApJ...871....5T: processing.imaging.weighting_robust = Briggs robust = 0
- 2019ApJ...871....5T: processing.imaging.multiscale_scales = [0, 0.12, 0.36] arcsec
- 2019ApJ...876..130H: R = +0.5 gives 0.08"x0.06", rms 23 uJy/beam
- 2019ApJ...876..130H: processing.imaging.weighting_robust = Briggs, R = +0.5 (reference)
- 2019ApJ...876..130H: processing.imaging.deconvolver = multi-scale clean, geometric progression of scales
- 2019ApJ...876..130H: processing.imaging.uv_taper = 0.3" taper for flux recovery test
- 2019A&A...631A..64B: robust = 0.5
- 2019A&A...631A..64B: thresholds 0.05 mJy/beam continuum, 3 mJy/beam lines
- 2019A&A...631A..64B: processing.imaging.weighting_robust = Briggs, robust 0.5
- 2019A&A...631A..64B: processing.imaging.deconvolver = multiscale for line emission; Högbom for continuum of individual sets
- 2019A&A...631A..64B: processing.imaging.multiscale_scales = 0, 8, 23, 68, 203, 608 pixels
- 2019ApJ...881...10B: Briggs r=0.5, 10.2 km/s channels, 0.015'' pixels
- 2019ApJ...881...10B: CO surface brightness map from 10 iterations of Richardson-Lucy deconvolution
- 2019ApJ...881...10B: fit region 415 spatial pixels x 94 channels = 39010 data points; spectral range 2310-3273 km/s
- 2019ApJ...881...10B: processing.imaging.weighting_robust = Briggs r=0.5 for the line cube; natural for continuum (Cycle 2+4)
- 2019ApJ...881...10B: processing.imaging.deconvolver = multiscale deconvolution on combined Cycle 2+4
- 2020ApJ...890..130T: self-cal only when peak S/N>10; applymode=calonly
- 2020ApJ...890..130T: sources with unreliable sizes (fixed to beam) excluded from radius analysis
- 2020ApJ...890..130T: processing.imaging.weighting_robust = Briggs robust=0.5 (robust=2 for non-detections; also 0 and -0.5 made); VLA Natural, nterms=2
- 2020ApJ...890..130T: processing.imaging.uv_taper = Continuum uv>25 kλ; line data natural weighting >50 kλ with 500 kλ outer taper
- 2020ApJ...897...91G: clean threshold 20 uJy/beam
- 2020ApJ...897...91G: N0=1-100e3 mJy^-1 deg^-2, S0=0.05-1.0 mJy, alpha=1.5-5, beta -2 to 2; fluxes 0.03-2 mJy; histogram bins 4.3 uJy/beam
- 2020ApJ...897...91G: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...897...91G: processing.imaging.uv_taper = tapered image to 2.37"x2.05" beam, rms 11.3 uJy/beam
- 2025A&A...696A.150S: robust +0.5; 6th iteration removes remaining emission channels
- 2025A&A...696A.150S: stop when model flux increases <1% or residual <2.5x theoretical noise
- 2025A&A...696A.150S: processing.imaging.weighting_robust = Briggs robust = +0.5
- 2025A&A...696A.150S: processing.imaging.deconvolver = multiscale
- 2025A&A...696A.150S: processing.imaging.multiscale_scales = 7M [0,30,60]; TM2/TM1 [0,6,18,30]; 7MTM2 and 7MTM2TM1 [0,6,18,30,60]
- 2024ApJ...971..129C: robust=0.8, 1 sigma threshold
- 2024ApJ...971..129C: Rmax=2.1", N=300, p0=1e-15 Jy^2, alpha=1.3, wsmooth=0.1
- 2024ApJ...971..129C: w_max = 17.1 au, w_min = h_p = 5.15 au
- 2024ApJ...971..129C: processing.imaging.weighting_robust = robust = 0.8 (also 0.0 for profiles)
- 2020ApJ...891...48H: Band 4 robust 0, Band 6 robust 0.5
- 2020ApJ...891...48H: processing.imaging.weighting_robust = Band 4 robust = 0; Band 6 robust = 0.5; HCO+ robust 1.0
- 2020ApJ...891...48H: processing.imaging.uv_taper = Gaussian outer taper for HCO+; 0.06 arcsec taper for low-res continuum
- 2020ApJ...891...48H: processing.imaging.multiscale_scales = Compact: [0,0.15,0.3,0.6,0.9] arcsec; combined: [0,0.075,0.15,0.3,0.525] arcsec; HCO+: [0,0.2,0.5,0.75,1.5] arcsec
- 2014A&A...569A..11S: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2014A&A...569A..11S: processing.imaging.uv_taper = 1 arcsec taper for C17O, C34S, H13CO+, SiO
- 2024ApJ...968....9W: aperture diameter 1.5''; robust 2.0
- 2024ApJ...968....9W: D=1.5×FWHM major axis; i=arccos(b/a)
- 2024ApJ...968....9W: processing.imaging.weighting_robust = robust = 2.0 (natural) for main analysis; robust = 0.5 for kinematics
- 2018Sci...362.1034D: briggs robust=2, hogbom, 1″ mask, 2σ clean depth
- 2018Sci...362.1034D: processing.imaging.weighting_robust = briggs, robust = 2
- 2018Sci...362.1034D: processing.imaging.deconvolver = hogbom
- 2018Sci...362.1034D: processing.imaging.uv_taper = taper giving FWHM ~1″ (check map)
- 2017ApJ...841..110S: Deconvolved half-power size ~2.3" at 3.3 mm (radius ~2.6e16 cm)
- 2017ApJ...841..110S: processing.imaging.weighting_robust = natural weighting (Band 3 12m+ACA)
- 2017ApJ...841..110S: processing.imaging.uv_taper = Gaussian taper radius of 100 klambda
- 2015ApJ...807..128S: clean to 3 sigma; 1.5 sigma with boxes around >5 sigma sources
- 2015ApJ...807..128S: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2015ApJ...807..128S: processing.imaging.uv_taper = natural weighting plus 0.6'' Gaussian taper for detection maps
- 2015ApJ...811...92C: processing.imaging.weighting_robust = natural weights for flux and noise; Briggs restoration beam
- 2015ApJ...811...92C: processing.imaging.deconvolver = uvmem maximum-entropy (MEM) non-parametric visibility fit
- 2020MNRAS.495.3840M: robust = 0.5; 5 km/s channels
- 2020MNRAS.495.3840M: Av = 1.0 mag; C_NII = 0.79; alpha 5.3e-42 conversion
- 2020MNRAS.495.3840M: processing.imaging.weighting_robust = Briggs robust = 0.5 (both CO 1-0 and CO 2-1)
- 2020MNRAS.495.3840M: processing.imaging.deconvolver = multiscale CLEAN
- 2016ApJ...829....6W: natural weighting; threshold 1/2 sigma_RMS
- 2016ApJ...829....6W: processing.imaging.weighting_robust = natural weighting
- 2025ApJ...992..211N: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2025ApJ...992..211N: processing.imaging.deconvolver = Högbom
- 2015Natur.525..218R: processing.imaging.weighting_robust = natural weighting
- 2024ApJ...975..103P: nterms=2, cell 0.2", robust=1
- 2024ApJ...975..103P: processing.imaging.weighting_robust = Briggs, robust = 1
- 2024ApJ...975..103P: processing.imaging.deconvolver = nterms=2
- 2024ApJ...975..103P: processing.imaging.uv_taper = SPWs 1-3 tapered/restored to SPW0 beam 2.9"x2.3" at PA -4.5 deg for RM
- 2019ApJS..244...25S: Spectral regions above 8x initial rms removed before robust rms
- 2019ApJS..244...25S: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2019ApJS..244...25S: processing.imaging.deconvolver = Högbom
- 2016ApJ...821L...8S: clean threshold 2x expected RMS
- 2016ApJ...821L...8S: processing.imaging.weighting_robust = natural weighting
- 2016ApJ...821L...8S: processing.imaging.deconvolver = Högbom clean
- 2018ApJ...865...13T: natural weighting; 40 km/s channels (binned to 5, 10, 40 km/s as needed)
- 2018ApJ...865...13T: processing.imaging.weighting_robust = natural; Briggs robust -2 to 2 tried, results similar
- 2018ApJ...865...13T: processing.imaging.uv_taper = Gaussian taper for some images, beam 0.944x0.764 arcsec PA 86
- 2021ApJ...908..231M: robust 0.5, 11 km/s channels
- 2021ApJ...908..231M: processing.imaging.weighting_robust = robust = 0.5
- 2015A&A...577L...4V: Briggs 0.5
- 2015A&A...577L...4V: processing.imaging.weighting_robust = Briggs 0.5
- 2015A&A...577L...4V: processing.imaging.deconvolver = Band 3: multi-frequency synthesis with two Taylor coefficients
- 2019A&A...628A..10B: Briggs robust 0.5
- 2019A&A...628A..10B: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2019A&A...628A..10B: processing.imaging.deconvolver = csclean imager mode
- 2018MNRAS.481.4931E: robust=2
- 2018MNRAS.481.4931E: processing.imaging.weighting_robust = Briggs robust=2
- 2020A&A...644A..59K: robust = 0.5
- 2020A&A...644A..59K: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2020AJ....159..288M: Briggs robust 0.5
- 2020AJ....159..288M: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2025ApJ...990..145L: 9 free parameters: M_disk, a0, w_r, e_f0, omega_f, n_pow, i, PA, h; 40 walkers, 6000 steps, first half removed
- 2025ApJ...990..145L: processing.imaging.weighting_robust = Briggs, robust 0.5
- 2020ApJ...891...80M: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...891...80M: processing.imaging.uv_taper = only baselines >100 kλ used to isolate stellar emission
- 2021A&A...656A..68E: Position angle fixed at 80 degrees
- 2021A&A...656A..68E: Analysis time range t=1000-2000 s for Tb and formation heights; 1550-1750 s for spatial power
- 2019ApJ...884L..58U: processing.imaging.deconvolver = iterative CLEAN, up to 15000 iterations, threshold 0.02 mJy
- 2020ApJ...894L..14L: robust 0.5; scales [0,5,15,50,150]; 0.04" pixel
- 2020ApJ...894L..14L: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2020ApJ...894L..14L: processing.imaging.deconvolver = multiscale, scales [0, 5, 15, 50, 150]
- 2024PSJ.....5..125T: Hogbom, natural weighting, 0.01 arcsec pixels
- 2024PSJ.....5..125T: processing.imaging.weighting_robust = natural weighting
- 2024PSJ.....5..125T: processing.imaging.deconvolver = Högbom
- 2024A&A...686A.274V: detection threshold >5 sigma_P
- 2024A&A...686A.274V: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2013ApJ...762L..21M: processing.imaging.weighting_robust = natural weighting
- 2024IJAsB..23...14M: processing.imaging.weighting_robust = Briggs robust 0.5
- 2023PSJ.....4..193B: processing.imaging.weighting_robust = robust = 0
- 2026ApJ..1003L..17Y: processing.imaging.deconvolver = CLEAN (Högbom)
- 2020A&A...644A..84M: processing.imaging.weighting_robust = Briggs robust = 0
- 2024Ap&SS.369...18M: robust = 0.5, Stokes I
- 2024Ap&SS.369...18M: processing.imaging.weighting_robust = robust = 0.5
- 2014ApJ...795L..30C: processing.imaging.weighting_robust = natural
- 2014ApJ...795L..30C: processing.imaging.deconvolver = Hogbom, per channel, threshold 2x RMS
- 2014A&A...563A.136M: processing.imaging.weighting_robust = Briggs, robustness 0.5 (simulated data)
- 2019ApJ...876...72L: robust = 0.5 (0 for V4046 Sgr)
- 2019ApJ...876...72L: processing.imaging.weighting_robust = Briggs robust = 0.5; robust = 0 for V4046 Sgr CS 6-5
- 2019ApJ...876...72L: processing.imaging.deconvolver = CLEAN (Högbom) with 3 sigma threshold
- 2019ApJ...876...72L: processing.imaging.uv_taper = uv-taper on 12CS visibilities to match isotopologue beams (LkCa 15), reduces flux ~25%
- 2017A&A...597A..41G: niter=1000, threshold 4x rms, 0.1'' pixels
- 2017A&A...597A..41G: 10,000-240,000 iterations, 5,000 burn-in
- 2017A&A...597A..41G: processing.imaging.weighting_robust = natural weighting
- 2017A&A...597A..41G: processing.imaging.uv_taper = outertaper 1.5'' for check images
- 2018ApJ...869..158F: robust 0.5; scales 0,5,10 beams
- 2018ApJ...869..158F: processing.imaging.weighting_robust = robust = 0.5
- 2018ApJ...869..158F: processing.imaging.deconvolver = multiscale clean
- 2018ApJ...869..158F: processing.imaging.uv_taper = Tapered for several sources, beam ~1.5 arcsec (205 au); taper parameters not given
- 2018ApJ...869..158F: processing.imaging.multiscale_scales = 0, 5, 10 times synthesized beam
- 2018ApJ...857...19F: scales 1,2,5,10,15 x beam; 0.15 arcsec pixels; 100 iterations per cycle; gain 0.1
- 2018ApJ...857...19F: D=1.93 Mpc; R21=0.7; alpha_CO,MW=4.35; Sigma100_GMC=0.69
- 2018ApJ...857...19F: processing.imaging.weighting_robust = natural weighting
- 2018ApJ...857...19F: processing.imaging.deconvolver = multiscale CLEAN, scales 1, 2, 5, 10, 15 x synthesized beam
- 2020ApJ...898...10T: multiscale [0,4,20] continuum, [0,5,25] lines; cell 0.02''
- 2020ApJ...898...10T: processing.imaging.weighting_robust = uniform for continuum; natural for lines
- 2020ApJ...898...10T: processing.imaging.multiscale_scales = continuum [0,4,20]; lines [0,5,25]
- 2020ApJ...905..152D: clean to 3 sigma; scales 0, 0.5, 1.25 arcsec
- 2020ApJ...905..152D: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...905..152D: processing.imaging.deconvolver = multi-scale clean at scales 0, 0.5, 1.25 arcsec
- 2020ApJ...905..152D: processing.imaging.uv_taper = 0.6 arcsec
- 2026ApJ..1000..184N: S/N > 7 sigma; inner 1'' masked
- 2026ApJ..1000..184N: processing.imaging.weighting_robust = robust 0 (continuum); 0.5 (12CO)
- 2025A&A...697A..64V: mfs, nterms=1, multiscale, robust -0.5 to 0.5, clean to ~5σ
- 2025A&A...697A..64V: 30° wedge on major axis; 4 settling levels alpha_z,MCFOST 2e-4 to 0.2
- 2025A&A...697A..64V: processing.imaging.weighting_robust = Briggs, robust between -0.5 and 0.5 (per disk in table)
- 2025A&A...697A..64V: processing.imaging.deconvolver = multi-scale, cleaned to ~5σ
- 2020ApJ...894...74B: robust 0.5; 0.02" pixels; 0.5 km/s channels
- 2020ApJ...894...74B: processing.imaging.weighting_robust = robust = 0.5
- 2020ApJ...894...74B: processing.imaging.uv_taper = uv cut: none and 100 kλ tested
- 2014ApJ...796...82Z: robust = 0.5; 8 mas pixels
- 2014ApJ...796...82Z: processing.imaging.weighting_robust = robust = 0.5 in all bands
- 2014ApJ...796...82Z: processing.imaging.deconvolver = MEM in B3, B6, B7; CLEAN for I44-subtracted residuals
- 2026A&A...705A..81K: natural weighting, ~70 km/s channels
- 2026A&A...705A..81K: processing.imaging.weighting_robust = natural weighting
- 2026A&A...705A..81K: processing.imaging.deconvolver = Hogbom
- 2019A&A...628A.118B: natural weighting, 0.04 arcsec pixel, 30 km/s channels
- 2019A&A...628A.118B: processing.imaging.weighting_robust = natural weighting; briggs robust b=-0.5 for high-resolution cube
- 2019A&A...628A.118B: processing.imaging.deconvolver = Hogbom with interactive per-channel masks
- 2017A&A...602L..10O: robust 0, nterms=2, scales 0,1,3 beams, solint 15 s
- 2017A&A...602L..10O: processing.imaging.weighting_robust = Briggs robust 0 (also robust -1 and uniform tested)
- 2017A&A...602L..10O: processing.imaging.deconvolver = Multi-frequency synthesis CLEAN, nterms=2, multiscale
- 2017A&A...602L..10O: processing.imaging.multiscale_scales = 0, 1, 3 x synthesized beam
- 2014ApJ...792...34O: 40 km/s channels; 7.5 GHz continuum bandwidth
- 2014ApJ...792...34O: processing.imaging.weighting_robust = natural weighting
- 2014ApJ...792...34O: processing.imaging.uv_taper = 100 kλ taper giving 1.5"x1.2" beam
- 2013ApJ...774...16R: mask smoothing sigma = 0.7 arcsec
- 2013ApJ...774...16R: processing.imaging.weighting_robust = natural weighting
- 2021A&A...656A..46M: Binning 3, 5, 6, 8, 10 MHz for Bands 3-7; robust 0.5 mostly
- 2021A&A...656A..46M: processing.imaging.weighting_robust = Briggs robust 0.5 for most; some tunings use 0.4, 0.25, 0.0, -2.0 with uvrange cuts
- 2021A&A...656A..46M: processing.imaging.deconvolver = hogbom
- 2019ApJ...881...84S: Gaussian u-v taper 2", Briggs 0.5
- 2019ApJ...881...84S: processing.imaging.weighting_robust = Briggs 0.5
- 2019ApJ...881...84S: processing.imaging.uv_taper = Gaussian 2"
- 2024ApJ...964..166K: eta=1.91; channel width 5 km/s
- 2015ApJ...806...17R: 10 km/s channels; beam 0.39"x0.22"
- 2015ApJ...806...17R: processing.imaging.weighting_robust = uniform and natural weighting cubes
- 2024ApJ...962....1S: robust=0.5; 2σ threshold
- 2024ApJ...962....1S: processing.imaging.weighting_robust = briggs, robust = 0.5
- 2024ApJ...962....1S: processing.imaging.deconvolver = hogbom, mtmfs-style multi-frequency synthesis for continuum
- 2019Natur.570...83M: Robust = 0.5; residual slope <30 mJy
- 2019Natur.570...83M: processing.imaging.weighting_robust = Robust = 0.5
- 2018Icar..307..380T: pixel 0.03'', threshold 2x RMS
- 2018Icar..307..380T: processing.imaging.weighting_robust = natural
- 2018Icar..307..380T: processing.imaging.deconvolver = Högbom
- 2018ApJ...863..193V: robust = 0.5; velocity bins 20 and 10 km/s
- 2018ApJ...863..193V: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2018ApJ...863..193V: processing.imaging.uv_taper = uv taper on CO(3-2) to smooth scales below 0.1 arcsec
- 2021A&A...652A..98G: robust 1 (MSR), 0.1 (HSR); 10 km/s channels
- 2021A&A...652A..98G: processing.imaging.weighting_robust = robust = 1 (MSR) and 0.1 (HSR)
- 2015ApJ...808...36M: processing.imaging.weighting_robust = Briggs robust = 0
- 2019A&A...631A..25J: robust = -0.5
- 2019A&A...631A..25J: processing.imaging.weighting_robust = robust = -0.5
- 2017ApJ...842L..24A: scales [0,7,21] or [0,5,15]; 6 mas pixel
- 2017ApJ...842L..24A: processing.imaging.multiscale_scales = [0,7,21] for CO 2-1 and SiO 5-4; [0,5,15] for SiO 6-5
- 2020ApJ...890L..14T: robust = 0; ~1.3 km/s channels
- 2020ApJ...890L..14T: processing.imaging.weighting_robust = Briggs, robust = 0
- 2021AJ....161..271F: processing.imaging.weighting_robust = natural weighting
- 2025A&A...693A.151M: processing.imaging.weighting_robust = Different weighting and u-v tapers per target; natural weighting for CO
- 2025A&A...693A.151M: processing.imaging.deconvolver = multiscale CLEAN
- 2020PASJ...72L...9F: processing.imaging.uv_taper = uv-taper applied to second Band 7 observation to match the first beam
- 2018A&A...620A.119D: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...890..167T: robust = 0.5; 2 km/s velocity resolution
- 2020ApJ...890..167T: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2025NatAs...9.1476C: processing.imaging.weighting_robust = natural weighting
- 2025NatAs...9.1476C: processing.imaging.deconvolver = Högbom
- 2024Natur.633..323V: processing.imaging.weighting_robust = superuniform weighting (compared with Briggs robust 0.5)
- 2013ApJ...777L..25M: PACS aperture 20 arcsec, sky annulus 40-50 arcsec
- 2024ESC.....8..665M: processing.imaging.deconvolver = hogbom (continuum)
- 2015A&A...582L...1T: processing.imaging.deconvolver = Hogbom
- 2017A&A...605A.121M: processing.imaging.weighting_robust = Bandpass: natural weighting; science targets: briggs as in SV scripts (robust value not stated)
- 2020ApJ...891..164S: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2018ApJ...860...77E: robust 0.5, cell 0.02"
- 2018ApJ...860...77E: processing.imaging.weighting_robust = robust = 0.5
- 2018ApJ...860...77E: processing.imaging.deconvolver = Multiscale clean (0, 0.1", 0.3" scales) adopted over Hogbom
- 2018ApJ...860...77E: processing.imaging.uv_taper = uv cut at 100 klambda (optimal rms among 0-300 klambda)
- 2017ApJ...851..145M: taper FWHM 0.7''
- 2017ApJ...851..145M: M_dyn/Msun (sin i)^2 = 1.94e5 v_FWHM^2 r_1/2
- 2017ApJ...851..145M: processing.imaging.weighting_robust = natural weighting
- 2017ApJ...851..145M: processing.imaging.uv_taper = Gaussian FWHM=0.7''; tested 0.4-0.8''
- 2018ApJ...853..171G: robust 0.5, -1, and tapered robust 2 images
- 2018ApJ...853..171G: alpha kept if |alpha|>5 sigma(alpha) or sigma(alpha)<0.1
- 2018ApJ...853..171G: processing.imaging.weighting_robust = Briggs robust 0.5 (main); -1; taper with robust 2
- 2018ApJ...853..171G: processing.imaging.deconvolver = multi-scale multi-frequency synthesis, 2 Taylor terms (mtmfs, nterms=2)
- 2019A&A...632A..61G: 20 km/s channels
- 2019A&A...632A..61G: Full size defined at ~3 sigma level of the Gaussian
- 2019A&A...632A..61G: processing.imaging.weighting_robust = robust = 1 (MSR) and 0.1 (HSR)
- 2020ApJ...894...87C: Briggs robust 0.5; 0.6 arcsec uvtaper for combined
- 2020ApJ...894...87C: Deconvolved analysis excludes cores with area <1.5 x A_beam (34 of 76)
- 2020ApJ...894...87C: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2020ApJ...894...87C: processing.imaging.uv_taper = 0.6 arcsec uvtaper for combined data
- 2020ApJ...889..141T: processing.imaging.weighting_robust = robust=+2.0 with uvtaper 0.05'' (continuum); robust=+2.0, uvtaper 0.1'' (low-res cube)
- 2020ApJ...889..141T: processing.imaging.deconvolver = Multi-Scale Clean
- 2024ApJ...961..228S: robust 0.5; cell 0.0037'' (cont), 0.140'' (lines); 0.1 km/s channels
- 2024ApJ...961..228S: processing.imaging.weighting_robust = Briggs, robust = 0.5 (both datasets)
- 2025ApJ...989....1Z: 0.1 km/s channels for 12CO, 0.2 km/s others
- 2025ApJ...989....1Z: processing.imaging.weighting_robust = robust 0.5 for 12CO; 1 for other lines
- 2025ApJ...989....1Z: processing.imaging.uv_taper = uvtaper to circularize beam for Band 6 lines; uvrange >50 klambda for 12CO of Lupus/Upper Sco
- 2025ApJ...989....1Z: processing.imaging.multiscale_scales = [0,4,12,24,48] pixels Band 6; [0,4] Band 7
- 2020ApJ...893..101L: solints 100s, 30s, 10s phase; one amplitude; robust -0.5
- 2020ApJ...893..101L: clean threshold 4σ
- 2020ApJ...893..101L: bootstrap 10000 draws on emission-free channels
- 2020ApJ...893..101L: processing.imaging.weighting_robust = Natural for survey cubes; continuum robust −0.5; strong lines (>20σ) Briggs robust 0.5
- 2015ApJ...801...82H: processing.imaging.weighting_robust = uniform weighting
- 2015ApJ...801...82H: processing.imaging.uv_taper = uv>100 klambda cut for compact source identification
- 2026A&A...705A..39P: 30 km/s channel width
- 2026A&A...705A..39P: processing.imaging.weighting_robust = natural
- 2026A&A...705A..39P: processing.imaging.deconvolver = hogbom
- 2019A&A...632A..66O: processing.imaging.weighting_robust = Natural weighting for low-noise cube; uniform for 100 GHz continuum
- 2019A&A...632A..66O: processing.imaging.uv_taper = Tapering to 0.167x0.126 arcsec (large-scale cube) and to match CO(3-2) beam; taper values not stated
- 2018A&A...616L...3B: processing.imaging.weighting_robust = Briggs robust = 1; robust -2 (uniform) for long-baseline map
- 2018A&A...616L...3B: processing.imaging.deconvolver = Hogbom
- 2018A&A...616L...3B: processing.imaging.uv_taper = baselines >2.5 km only
- 2012ApJ...761L..32W: natural weighting
- 2012ApJ...761L..32W: processing.imaging.weighting_robust = Natural weighting
- 2012ApJ...761L..32W: processing.imaging.deconvolver = GRB 021004 left dirty; GRB 080607 CLEANed
- 2015ApJ...810..112O: robust 0.5 continuum, 1.0 lines; 0.2 km/s channels
- 2015ApJ...810..112O: processing.imaging.weighting_robust = Briggs, robust = 0.5 continuum, 1.0 lines
- 2020ApJ...901..151S: natural weighting, 10.16 km/s channels (CO); Briggs robust 0.5, mfs (continuum)
- 2020ApJ...901..151S: processing.imaging.weighting_robust = CO: natural; continuum: Briggs robust 0.5
- 2020ApJ...901..151S: processing.imaging.uv_taper = Gaussian FWHM 4" for tapered cube (beam 4.902x4.219", rms 4.1 mJy/beam)
- 2019AJ....157..117M: processing.imaging.weighting_robust = natural weighting
- 2019AJ....157..117M: processing.imaging.deconvolver = multiscale
- 2019AJ....157..117M: processing.imaging.uv_taper = 2 arcsec
- 2024MNRAS.527.9343L: robust = 2.0, 10 km/s channels
- 2024MNRAS.527.9343L: processing.imaging.weighting_robust = Briggs robust = 2.0, 10 km/s channels (cube and continuum)
- 2024MNRAS.527.9343L: processing.imaging.deconvolver = MultiScale
- 2015ApJ...811...39I: gain 0.1, threshold 1.0 mJy
- 2015ApJ...811...39I: processing.imaging.weighting_robust = natural
- 2024PASJ...76..340K: processing.imaging.weighting_robust = natural (line); uniform (continuum)
- 2019ApJ...872..121U: robust = 0.5
- 2019ApJ...872..121U: processing.imaging.weighting_robust = briggs, robust = 0.5
- 2018ApJ...859L..15C: pixel 0.025'', flux threshold 8 mJy
- 2018ApJ...859L..15C: processing.imaging.weighting_robust = natural
- 2018ApJ...859L..15C: processing.imaging.deconvolver = Clark clean
- 2016MNRAS.458.3134R: robust 0.5 (Band 3), 2 (Band 7); 10 km/s channels
- 2016MNRAS.458.3134R: processing.imaging.weighting_robust = robust 0.5 for CO(1-0); robust 2 for CO(3-2)
- 2016MNRAS.458.3134R: processing.imaging.deconvolver = CLEAN with Briggs weighting
- 2020ApJ...891...64F: processing.imaging.weighting_robust = natural (LR); Briggs robust 0.5 (MR); robust 0.2 (HR)
- 2013A&A...556L...1V: processing.imaging.weighting_robust = natural weighting
- 2016ApJ...825...79S: CLEAN threshold 72 mJy
- 2016ApJ...825...79S: processing.imaging.weighting_robust = equal weighting of uv
- 2018ApJ...855L...2M: processing.imaging.weighting_robust = natural weighting
- 2023RAA....23a5004N: processing.imaging.weighting_robust = robust weighting (weight=1)
- 2020PASP..132h4401T: processing.imaging.weighting_robust = natural weighting
- 2025A&A...698A.183D: processing.imaging.weighting_robust = natural weighting; robust -2 to 2 tested, gave noisy images
- 2025A&A...698A.183D: processing.imaging.deconvolver = Hogbom
- 2020ApJ...894...76W: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...889L...4L: processing.imaging.weighting_robust = Briggs weighting, Clean algorithm (robust not given)
- 2024PSJ.....5..230D: processing.imaging.weighting_robust = robust = 1.0 (VLA images only)
- 2024A&A...691A..57M: processing.imaging.uv_taper = FWHM 0.04 arcsec, combining three configurations
- 2018ApJ...869L..41A: Combined data: SPWs combined; applymode='calonly' for antenna pairs with SNR ≤ 1.5
- 2018ApJ...869L..41A: processing.imaging.weighting_robust = Briggs robust = 0.5 during self-calibration; fiducial images tailored per target (Table 4)
- 2018ApJ...869L..41A: processing.imaging.deconvolver = Multi-scale, multi-frequency synthesis (flat spectrum); scales target-dependent: point, ~θb, 2–3θb, further scales up to mask radius
- 2018ApJ...869L..41A: processing.imaging.uv_taper = Target-dependent tapers in fiducial images (Table 4); CO tapers in Table 5
- 2019ApJ...876..112R: 5 mas pixels, 1024x1024, auto-mask SNR 2
- 2019ApJ...876..112R: 25 mas pixel cubes, natural weighting
- 2019ApJ...876..112R: processing.imaging.weighting_robust = natural weighting
- 2019ApJ...887..209A: processing.imaging.weighting_robust = Briggs robust = 0.0
- 2019ApJ...887..209A: processing.imaging.deconvolver = Multi-scale CLEAN, point sources or Gaussians of FWHM ~1.5''
- 2019MNRAS.484.4239R: nterms=1, natural weighting
- 2019MNRAS.484.4239R: Gaussian smoothing with beam FWHM, then Hanning smoothing in velocity
- 2019MNRAS.484.4239R: processing.imaging.weighting_robust = natural weighting for continuum and line
- 2021ApJ...907L..15S: robust 0.5, hogbom, automask
- 2021ApJ...907L..15S: processing.imaging.weighting_robust = robust = 0.5
- 2021ApJ...907L..15S: processing.imaging.deconvolver = hogbom
- 2021ApJ...907L..15S: processing.imaging.uv_taper = 100-200 kλ tested; 150 kλ (~0.8") adopted
- 2020ApJ...889..162L: robust = 2; first-order polynomial continuum
- 2020ApJ...889..162L: processing.imaging.weighting_robust = Briggs robust = 2 (natural)
- 2025SciA...11.4512O: continuum robust 0.5, threshold 1.25 sigma; lines robust 2, multiscale 0,5,15,25
- 2025SciA...11.4512O: processing.imaging.weighting_robust = continuum robust 0.5; lines robust 2
- 2025SciA...11.4512O: processing.imaging.deconvolver = continuum Hogbom; lines multi-scale
- 2025SciA...11.4512O: processing.imaging.multiscale_scales = 0, 5, 15, 25
- 2025ApJ...993...90S: robust=0.5; final peak SNR 62.3
- 2025ApJ...993...90S: 1000 iterations, 32 walkers, init from SpM cos i and PA
- 2025ApJ...993...90S: processing.imaging.weighting_robust = Briggs robust=0.5 (continuum and line)
- 2025ApJ...993...90S: processing.imaging.deconvolver = multi-scale for line
- 2023PASJ...75..424O: emitting surface height ratio 0.13
- 2023PASJ...75..424O: processing.imaging.weighting_robust = natural weighting for continuum; line maps density weight (file names indicate robust 0.5)
- 2023PASJ...75..424O: processing.imaging.uv_taper = Gaussian taper 1.5 Mlambda on 12CO; 0.3 Mlambda on 13CO and C18O
- 2023PASJ...75..424O: processing.imaging.multiscale_scales = [0, 1,2,3,4,5 x beam size]
- 2015ApJ...811L...4Z: robust 0.5; taper ~1.0''
- 2015ApJ...811L...4Z: processing.imaging.weighting_robust = robust = 0.5
- 2015ApJ...811L...4Z: processing.imaging.uv_taper = tapered to ~1.0'' resolution
- 2025ApJS..278...45F: pixel 0.1 arcsec, natural weighting, taper 1.5 arcsec, automask
- 2025ApJS..278...45F: processing.imaging.weighting_robust = natural weighting
- 2025ApJS..278...45F: processing.imaging.uv_taper = 1.5x1.5 arcsec
- 2017ApJ...851..126V: robust 0.5, 0.05'' pixel
- 2017ApJ...851..126V: processing.imaging.weighting_robust = Continuum: Briggs robust 0.5; line cubes: natural
- 2017ApJ...851..126V: processing.imaging.uv_taper = Cycle 2 band 4: taper to 0.98''x0.8'' (robust 0.5)
- 2017A&A...603A..92V: line robust 0.5; continuum robust -0.5
- 2017A&A...603A..92V: processing.imaging.weighting_robust = lines: Briggs robust 0.5; continuum: robust -0.5
- 2015A&A...576L...2S: processing.imaging.weighting_robust = natural weighting
- 2015A&A...576L...2S: processing.imaging.uv_taper = tapered to 0.5'' resolution for Fig. 1
- 2014ApJ...791L...6W: CO integrated between -12 and +12 km/s of source velocity 5.7 km/s
- 2014ApJ...791L...6W: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2020ApJ...898...75I: robust 0.0 (Bands 6-8); robust 0.5 with outertaper 0.2'' (Band 3); dV = 10 km/s (20 for 13CO)
- 2020ApJ...898...75I: processing.imaging.weighting_robust = robust = 0.0 for Bands 6,7,8; robust = +0.5 for Band 3
- 2020ApJ...898...75I: processing.imaging.uv_taper = outertaper = 0.2 arcsec (Band 3)
- 2017MNRAS.465.2595M: processing.imaging.weighting_robust = natural weights
- 2017MNRAS.465.2595M: processing.imaging.uv_taper = Gaussian taper FWHM 1.2" giving 1.5"x1.3" beam
- 2025ApJ...995L..63L: natural weighting, untapered
- 2025ApJ...995L..63L: processing.imaging.weighting_robust = natural weighting
- 2025ApJ...995L..63L: processing.imaging.uv_taper = untapered; heavy 2 arcsec taper tested
- 2014ApJ...797...90S: Briggs robust = 0, natural, tapered
- 2014ApJ...797...90S: processing.imaging.weighting_robust = Briggs robust = 0, natural, or tapered depending on dataset
- 2026ApJ..1002L..28Y: aperture diameter 0.8''
- 2026ApJ..1002L..28Y: processing.imaging.weighting_robust = natural weighting
- 2017ApJ...842...94T: fitorder=1; natural and Briggs R=0.5 weighting
- 2017ApJ...842...94T: processing.imaging.weighting_robust = natural and Briggs R=0.5
- 2019AJ....157..251T: 512x512 pixels, 0.02" cell, 1000-2000 iterations until in-disk noise equals sky noise
- 2019AJ....157..251T: processing.imaging.weighting_robust = natural weighting
- 2017ApJ...848..101V: processing.imaging.weighting_robust = Briggs, robust = 2
- 2017ApJ...848..101V: processing.imaging.uv_taper = uv taper smoothing CO(3-2) and 13CO(3-2) on scales below 0.1 arcsec
- 2020ApJ...898...61I: df = 62.5 MHz (quasars), 31.25 MHz (galaxies)
- 2020ApJ...898...61I: processing.imaging.weighting_robust = natural weighting
- 2014A&A...572L...9R: processing.imaging.weighting_robust = Continuum natural; masers Briggs robust=0.5
- 2019A&A...629A.128W: 4 Gaussians for MA0.89 SW; 1 Gaussian for MA0.89 NE and MA0.68
- 2017MNRAS.464L..75F: processing.imaging.weighting_robust = natural and Briggs robust 0
- 2020A&A...633A..13D: ACA/12-m weight ratio 0.18
- 2020ApJ...892...99C: processing.imaging.weighting_robust = natural weighting
- 2024RMxAA..60..355R: ALMA robust 0.5; VLA robust 2
- 2024RMxAA..60..355R: processing.imaging.weighting_robust = ALMA robust = 0.5; VLA robust = 2
- 2020A&A...638A..17O: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2016ApJ...829L..35T: robust 0.5/1.0; scales [0,100,300]/[0,50,150] mas
- 2016ApJ...829L..35T: processing.imaging.weighting_robust = Briggs robust 0.5 (B4), 1.0 (B6), 0.0 (MFS)
- 2016ApJ...829L..35T: processing.imaging.uv_taper = Band 6 visibilities with uv >3000 klambda flagged
- 2016ApJ...829L..35T: processing.imaging.multiscale_scales = [0,100,300] mas (B4), [0,50,150] mas (B6), [0,60,180] mas (MFS)
- 2019ApJ...881..124M: 2-channel averaging, ~18 km/s
- 2019ApJ...881..124M: processing.imaging.weighting_robust = natural weighting for initial; Briggs robust 0.5 for high-res
- 2019ApJ...881..124M: processing.imaging.uv_taper = 650 kλ (0.3'' FWHM)
- 2017ApJ...838..114K: kappa=0.23 cm2/g at 107 GHz; T=15 K; d=140 pc; gas-to-dust 100
- 2017PASJ...69...18T: robust 0.4/0.4/0.2/0.1; multiscale [0,10,25]; cell 0.25 arcsec; 1.5 km/s channels
- 2017PASJ...69...18T: processing.imaging.weighting_robust = Briggs; robust = 0.4 (13CO, C18O), 0.2 (CS), 0.1 (CH3OH)
- 2017PASJ...69...18T: processing.imaging.deconvolver = multi-scale CLEAN
- 2017PASJ...69...18T: processing.imaging.multiscale_scales = [0, 10, 25] pixels
- 2020AJ....159...62C: processing.imaging.weighting_robust = natural for main images; robust = 0.5 for Gaussian fits
- 2020A&A...636A..37D: channel width 40/120/40 km/s for XID 42/539/666
- 2020A&A...636A..37D: processing.imaging.weighting_robust = Line: robust 0.5, 1, 1 for XID 42, 539, 666; continuum robust 1
- 2020A&A...636A..37D: processing.imaging.uv_taper = 0.45" taper with natural weighting for non-detections
- 2024ApJ...969..143I: processing.imaging.weighting_robust = Briggs robust=2 for high-res combination
- 2024ApJ...969..143I: processing.imaging.uv_taper = Gaussian taper 0.37''
- 2024ApJ...969..143I: processing.imaging.multiscale_scales = continuum: 0, 5, 11, 21 x 0.5'' pixel
- 2024ApJ...974..102S: JvM epsilon = 0.71, 0.47, 0.33, 0.31 for 12CO, 13CO, C18O, H2CO
- 2024ApJ...974..102S: zeta = 0.02, L* = 0.25 Lsun, T_d=[zeta L/(4 pi sigma r^2)]^(1/4)
- 2024ApJ...974..102S: processing.imaging.weighting_robust = Briggs robust 0.0 (continuum, 12CO), 0.5 (13CO), 1.0 (C18O, H2CO)
- 2024ApJ...974..102S: processing.imaging.multiscale_scales = point sources and 0.5, 1, 2, 3 times beam FWHM
- 2021AJ....161...38O: Sigma(20au)=35 g cm-2, gamma=-1.3, H(20au)=2 au, p=0.3, mean molecular weight 2.37, T_atm=125 K at 10 au
- 2021AJ....161...38O: processing.imaging.weighting_robust = Briggs 0.5
- 2014ApJ...796....1T: robust=+0.5; uv>80 klambda for highest-resolution continuum
- 2014ApJ...796....1T: processing.imaging.weighting_robust = Briggs robust=+0.5 for lines; continuum: Natural, robust=+0.5, and Uniform with uv>80 klambda
- 2025ApJ...990L..31B: channels |v|>1000 km/s for fit; hogbom; natural weighting
- 2025ApJ...990L..31B: processing.imaging.weighting_robust = natural weighting
- 2025ApJ...990L..31B: processing.imaging.deconvolver = hogbom, non-interactive, threshold 2x rms
- 2019A&A...631A..78S: 3-D spectra extracted over 2" region
- 2019A&A...631A..78S: processing.imaging.weighting_robust = natural weighting
- 2019A&A...627A.114K: robust = 0.5
- 2019A&A...627A.114K: processing.imaging.weighting_robust = Briggs robust = 0.5 unless otherwise stated
- 2019A&A...627A.114K: processing.imaging.uv_taper = UV taper equivalent to a 450 mas Gaussian beam
- 2015ApJ...807..180W: robust = 1; 15.625 MHz channels
- 2015ApJ...807..180W: processing.imaging.weighting_robust = Briggs, Robust = 1
- 2015ApJ...808..102K: robust = 0
- 2015ApJ...808..102K: processing.imaging.weighting_robust = robust = 0
- 2021A&A...655A..25Z: pixel 0.05 arcsec, 10.6 km/s channels
- 2021A&A...655A..25Z: processing.imaging.weighting_robust = natural
- 2021A&A...655A..25Z: processing.imaging.deconvolver = hogbom, threshold 3x rms
- 2019MNRAS.484.1257M: processing.imaging.weighting_robust = natural weights
- 2019MNRAS.484.1257M: processing.imaging.uv_taper = Gaussian taper 0.7''
- 2025A&A...701A..48D: robust 0 / 2 / 0.5; uv-taper 0.5'' for Mrk 915
- 2025A&A...701A..48D: processing.imaging.weighting_robust = robust = 0 (NGC 6860), 2 (Mrk 915), 0.5 (MCG -01-24-012)
- 2025A&A...701A..48D: processing.imaging.uv_taper = Gaussian 0.5 arcsec for Mrk 915 only
- 2015MNRAS.450L..80B: natural weighting, 0.1 arcsec pixels, 3.9 MHz channels
- 2015MNRAS.450L..80B: processing.imaging.weighting_robust = natural weighting
- 2024ApJ...970....9B: processing.imaging.weighting_robust = natural
- 2024ApJ...970....9B: processing.imaging.deconvolver = hogbom
- 2019ApJ...872....2R: 3 km/s channels, robust 0.5, PB cutoff 20%
- 2019ApJ...872....2R: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2018AJ....156..164B: Eris visibility fit: slightly limb-darkened disk, radius 1163 km; others point sources
- 2018AJ....156..164B: processing.imaging.weighting_robust = natural weighting
- 2018ApJ...853..195W: processing.imaging.weighting_robust = natural weighting
- 2020MNRAS.493.3744F: processing.imaging.weighting_robust = Natural weighting (Briggs robust 0.5 and -1.0 only for GalPak tests)
- 2013ApJ...778L..25C: processing.imaging.weighting_robust = robust = 0.5
- 2019ApJ...871..112X: robust 0.5, cell 0.3 arcsec
- 2019ApJ...871..112X: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2019ApJ...875...55W: processing.imaging.weighting_robust = VLA natural weighting
- 2020ApJ...899..152H: processing.imaging.weighting_robust = natural weighting
- 2020MNRAS.497.2811K: processing.imaging.weighting_robust = natural weighting
- 2018ApJ...866L...6C: robust 0.5
- 2018ApJ...866L...6C: alpha=0.014, disc mass 20 MJ within 200 au, 350x512 cells, 5.6-378 au
- 2018ApJ...866L...6C: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2018ApJ...866L...6C: processing.imaging.deconvolver = multi-scale CLEAN, scales 0", 0.048", 0.08", 0.24"
- 2016ApJ...816...37V: robust=0.5
- 2016ApJ...816...37V: D=1.5x deconvolved size; i=25, 50 deg; 55 deg and 3±1 kpc for J2348–3054
- 2016ApJ...816...37V: processing.imaging.weighting_robust = robust = 0.5
- 2018ApJ...861...91H: robust = -2 for high-resolution VLA 1623 image
- 2018ApJ...861...91H: processing.imaging.weighting_robust = Natural (both); Briggs robust = -2 for VLA 1623
- 2018ApJ...861...91H: processing.imaging.deconvolver = multiscale clean
- 2018ApJ...861...91H: processing.imaging.uv_taper = 100 klambda Gaussian taper for CB disk flux fit
- 2016ApJ...822L..10I: gain 0.1, threshold 0.8 mJy, 40 channels binned, 0.03 arcsec pixel
- 2016ApJ...822L..10I: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...904L..24S: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...904L..24S: processing.imaging.deconvolver = multi-scale
- 2020ApJ...904L..24S: processing.imaging.uv_taper = uvtaper applied (value not given)
- 2020ApJ...892...66M: Offset dRA=+0.076", dDec=-0.279"; PB coverage >75% (2.27 arcmin^2)
- 2020ApJ...892...66M: Redshift bins 0.3-0.6, 0.6-1.0, 1.0-1.6, 1.6-2.3, 2.3-3.2; mass thresholds from 1e11 down in 0.5 dex steps
- 2020ApJ...892...66M: processing.imaging.weighting_robust = natural weighting
- 2024ApJ...963...72O: robust −1, 0.5, 2.0
- 2024ApJ...963...72O: processing.imaging.weighting_robust = briggs; robust −1, 0.5, 2.0 depending on dataset/line
- 2024ApJ...963...72O: processing.imaging.deconvolver = högbom
- 2024ApJ...963...72O: processing.imaging.uv_taper = baselines >30 kλ, uvtaper 300 kλ (for one line)
- 2024ApJ...969..165D: 7 phase-only + 1 amplitude iteration; robust +0.5
- 2024ApJ...969..165D: 253-1536B mask: inclination 45 deg, PA -90 deg
- 2024ApJ...969..165D: processing.imaging.weighting_robust = Briggs robust +0.5
- 2024ApJ...969..165D: processing.imaging.uv_taper = uvtaper = 0.5 arcsec for lines
- 2021A&A...654A..35B: processing.imaging.weighting_robust = robust -1.0 and 1.0
- 2021A&A...654A..35B: processing.imaging.uv_taper = ['0.010arcsec','0.010arcsec','10deg']
- 2012A&A...548A..69N: robust=1, 0.3" pixels, 30" image
- 2012A&A...548A..69N: processing.imaging.weighting_robust = Briggs, robustness 1
- 2024ApJ...977..198L: taper 18.75 kλ
- 2024ApJ...977..198L: processing.imaging.weighting_robust = natural weighting
- 2024ApJ...977..198L: processing.imaging.uv_taper = downweight baselines longer than 18.75 kλ (Gaussian FWHM 4.8'')
- 2017ApJ...843..136E: robust = 0.5
- 2017ApJ...843..136E: processing.imaging.weighting_robust = Briggs, robust = 0.5 (continuum and lines)
- 2019A&A...629A.146V: processing.imaging.weighting_robust = Natural weighting cube and robust = 0.5 cube
- 2019A&A...629A.146V: processing.imaging.deconvolver = Steer-Dewdney-Ito algorithm (not Hogbom)
- 2015A&A...584A..32M: fit restricted to pixels >=2.5 sigma; resolved if FWHM > half beam
- 2015A&A...584A..32M: processing.imaging.weighting_robust = robust = 0.5
- 2013Natur.493..191C: self-cal solint 5 min
- 2013Natur.493..191C: processing.imaging.weighting_robust = Briggs, robustness 0
- 2020MNRAS.497.2771M: processing.imaging.weighting_robust = natural weighting
- 2019ApJ...872...92F: processing.imaging.weighting_robust = natural weighting
- 2024A&A...690A.169L: ring width 15 arcsec; weighting |cos θ|^2; rings with Vrot errors >±30 km/s dropped
- 2015A&A...580A...1M: robust = 0; 20 km/s channels
- 2015A&A...580A...1M: processing.imaging.weighting_robust = Briggs robust = 0 for line cubes; uniform weighting for continuum
- 2025A&A...700A.285W: robust = 0.5, 30 km/s channels
- 2025A&A...700A.285W: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2016A&A...593A..44L: processing.imaging.weighting_robust = natural weighting
- 2016A&A...593A..44L: processing.imaging.uv_taper = Gaussian taper FWHM = 1.5" for CI line on 12m data
- 2019AJ....157..219T: pixel 0.1 arcsec, threshold 10 mJy
- 2019AJ....157..219T: processing.imaging.deconvolver = Högbom clean
- 2017ApJ...836..130R: processing.imaging.weighting_robust = natural weighting
- 2020ApJ...893...33L: processing.imaging.weighting_robust = natural
- 2015A&A...576L..15O: processing.imaging.weighting_robust = natural weighting
- 2019ESC.....3.2088S: robust = 0.5
- 2019ESC.....3.2088S: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2019MNRAS.488..191G: processing.imaging.weighting_robust = natural weighting
- 2021A&A...655A..80D: processing.imaging.uv_taper = 0.2" taper for AlF measurement
- 2018ApJ...859..111H: Continuum Briggs robust 0.5; lines natural weighting
- 2018ApJ...859..111H: 100 models per generation, 50 generations; Rc fixed 75 au, Rout 150 au
- 2018ApJ...859..111H: processing.imaging.weighting_robust = Continuum: Briggs robust 0.5; CO cubes natural weighting (extra 12CO cube robust 0.5)
- 2017A&A...602L...9M: robust = 0.5
- 2017A&A...602L...9M: fit restricted to pixels >= 2.5 sigma
- 2017A&A...602L...9M: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2018AJ....156..239Z: robust = 0; 140 klambda taper for line
- 2018AJ....156..239Z: kappa = 0.015 cm2/g, beta = 1.5, Td = 25 K
- 2018AJ....156..239Z: processing.imaging.weighting_robust = robust = 0
- 2018AJ....156..239Z: processing.imaging.uv_taper = outer taper 140 klambda (line image)
- 2018ApJ...867..166S: 4 million iterations, gain 0.05, natural weighting
- 2018ApJ...867..166S: processing.imaging.weighting_robust = natural weighting
- 2018ApJ...867..166S: processing.imaging.deconvolver = 4 million iterations, gain 0.05; residual scaling of Jorsater & van Moorsel
- 2020A&A...635A...2S: robust = 0.5; 1.0" circular super-resolution beam
- 2020A&A...635A...2S: processing.imaging.weighting_robust = Briggs robust = 0.5
- 2020A&A...635A...2S: processing.imaging.deconvolver = multi-scale
- 2021A&A...645A..45C: processing.imaging.weighting_robust = Briggs robust=1.0
- 2021A&A...645A..45C: processing.imaging.uv_taper = tapered HR cube, beam 0.21"x0.16"
- 2024A&A...686A.201N: processing.imaging.weighting_robust = briggs robust 0.5 (H13CO+: 2.0)
- 2024A&A...686A.201N: processing.imaging.deconvolver = multiscale
- 2024ApJ...966...59S: robust 0.5/1/2 per source
- 2024ApJ...966...59S: processing.imaging.weighting_robust = robust 0.5 (2M0434, 2M0436, 2M0450, 2M0508), 1 (2M0412), 2 (CIDA 12)
- 2024ApJ...966...59S: processing.imaging.deconvolver = multiscale
- 2024ApJ...966...59S: processing.imaging.uv_taper = Continuum: tapered for circular beams (values not stated); lines tapered to 0.2'' (2M0412, 2M0434) and 0.1'' (others)
- 2020ApJ...889L..24P: robust 1.0 (12CO), 2.0 (13CO, C18O)
- 2020ApJ...889L..24P: processing.imaging.weighting_robust = Continuum natural; 12CO robust 1.0; 13CO and C18O robust 2.0
- 2013ApJ...774L...7M: robust=0.5, cell 0.14"
- 2013ApJ...774L...7M: processing.imaging.weighting_robust = briggs, robust=0.5
- 2024A&A...688A..55M: SED template of Bethermin et al. 2017; gencal and applycal; three mass bins
- 2024A&A...688A..55M: processing.imaging.weighting_robust = natural weighting
- 2018ApJ...869..114I: processing.imaging.weighting_robust = natural weighting
- 2018A&A...615A..28D: robust 0.5
- 2018A&A...615A..28D: processing.imaging.weighting_robust = robust 0.5
- 2013ApJ...768...91H: processing.imaging.weighting_robust = natural weighting
- 2015ApJ...798L..23K: processing.imaging.weighting_robust = natural weighting
- 2015ApJ...798L..23K: processing.imaging.deconvolver = CLEAN
- 2020ApJ...890...29F: clean threshold 0.5 times rms
- 2020ApJ...890...29F: processing.imaging.weighting_robust = natural weighting; Robust weighting for high-res cube (value not given)
- 2020ApJ...890...29F: processing.imaging.deconvolver = mx; MRC (Wakker & Schwarz 1988) check; threshold 0.5 rms
- 2019ApJ...877L..32M: robust = 0.5
- 2019ApJ...877L..32M: processing.imaging.weighting_robust = robust = 0.5
- 2025ApJ...992...44D: 3 km/s channels; 0.69x0.55 arcsec beam
- 2025ApJ...992...44D: processing.imaging.weighting_robust = Briggs robust = 1.5
- 2014ApJ...795..156W: robust 0.5; 0.08'' pixels; 5 km/s channels; 10 min solint
- 2014ApJ...795..156W: processing.imaging.weighting_robust = Briggs, robust = 0.5
- 2024A&A...684A..56K: processing.imaging.weighting_robust = Briggs robust 0.5; band 3 cubes natural
- 2024A&A...684A..56K: processing.imaging.uv_taper = band 3 tapered to match band 7 resolution
- 2019PASJ...71..105T: uvcontsub fitorder=1; natural weighting
- 2019PASJ...71..105T: processing.imaging.weighting_robust = natural weighting
- 2017ApJ...839L..15G: processing.imaging.weighting_robust = natural
- 2018MNRAS.475.3004S: robust = 0
- 2018MNRAS.475.3004S: processing.imaging.weighting_robust = Briggs, robust = 0
- 2020ApJ...900..131L: processing.imaging.weighting_robust = natural weighting
- 2015MNRAS.453.4324M: processing.imaging.uv_taper = outertaper 1.5 arcsec
- 2019A&A...632A..19T: processing.imaging.weighting_robust = natural weighting (PdBI)
- 2016MNRAS.459.4518H: processing.imaging.weighting_robust = natural weighting
- 2017ApJ...839...43O: Briggs 0.5, 0.25 km/s channels, 3 rms threshold
- 2017ApJ...839...43O: inclination 7 degrees
- 2017ApJ...839...43O: processing.imaging.weighting_robust = Briggs parameter 0.5
- 2017ApJ...839...43O: processing.imaging.deconvolver = Hogbom CLEAN to 3x rms
- 2017ApJ...845..138S: 62.5 MHz channels, robust = 0.5
- 2017ApJ...845..138S: UNIFORM weighting, exclusion angle 0 deg; only rings >3 sigma used
- 2017ApJ...845..138S: processing.imaging.weighting_robust = robust = 0.5
- 2018ApJ...859..165S: processing.imaging.multiscale_scales = multi-scale used for Stokes I (scales not stated)
- ... 1236 more

### Assumptions (bibcode: value)
- 2018ApJ...852..122H: M* = 0.88 Msun, distance 59.5 pc
- 2018ApJ...866..117C: Radio velocity convention nu_obs = nu_rest(1 - V/c)
- 2018ApJ...866..117C: T_d = 25 K
- 2018ApJ...866..117C: alpha_CO = 0.8; CO(6-5)/CO(1-0) ~ 2
- 2020ApJ...899...10T: Td = 10 K, kappa = 0.005 cm2/g
- 2020MNRAS.493.4294B: rotation-dominated system
- 2024ApJ...963..164R: Stellar and disk angular momentum axes aligned; no separation-dependent weighting
- 2025ApJ...993...85Y: deprojected outer ring is circular; Gaussian ring and beam
- 2025ApJ...993...85Y: mu=2.3, M*=0.5 Msun, L*=0.43 Lsun, stellar heating dominant
- 2020ApJ...895...84Y: Data 2 MS-CLEAN at nominal resolution is trusted reference
- 2018A&A...614A..58B: LTE level populations, constant abundances, axial symmetry, D = 1100 pc
- 2015Natur.522..455C: Meurer relation typical of z<3; SMC-like dust model
- 2020MNRAS.496.4061D: thin disc; each cloudlet equal mass fraction
- 2018MNRAS.475.4924K: Dust size 10 um to 1 cm, q=11/6; 880 um opacity 0.17 m2/kg
- 2019AJ....158...76C: Optically thin emission; density from Krasnopolsky 2009; temperature from CIRS CH4 limb at -27 deg
- 2019ApJ...882..118X: Partition function approximated by sixth-order polynomial
- 2026A&A...705A.198M: Gas co-located with dust and near-Keplerian
- 2020ApJS..251...14H: Point-source-like emission model
- 2024A&A...689A.317G: Continuum constant within each spectral window (spectral index 2, <1% variation)
- 2014ApJ...795L..25R: T_dust = 20 ± 1 K
- 2019ApJ...871....5T: Gaussian ring emission for beam deconvolution
- 2019ApJ...871....5T: Gas-to-dust mass ratio 100; CO abundance 1e-4; HCO+ 1e-9; turbulence 120 m/s; LTE
- 2019ApJ...881...10B: spatially uniform M/L; gas disk mass not included; thin, cold disk with no asymmetric drift
- 2020ApJ...890..130T: Gaussian 2σ approximates disk radius (~95% of flux)
- 2020ApJ...897...91G: double power-law number counts
- 2024ApJ...971..129C: Axisymmetric emission; i=29 deg, PA=45.7 deg
- 2024ApJ...971..129C: Passive flared disk Td, phi=0.02, L*=6 Lsun, scaled by 0.5, mu=2.33, Sc=1, Gaussian rings
- 2024ApJ...968....9W: [C II] from thin rotating disk
- 2017ApJ...841..110S: Outer waist expanding; lobe inclination 75-90 deg
- 2017ApJ...841..110S: Optically thin dust; 10% of stellar flux reddened to 900 K for disk case
- 2020MNRAS.495.3840M: H2/(HI+H2) = 0.7 for old-star 22 micron correction
- 2016ApJ...829....6W: Flux uncertainty dominated by 10% absolute flux scale
- 2025ApJ...992..211N: constant M/L, no dark matter in the center
- 2020AJ....159..288M: Gaussian radial profile, FWHM = 0.2R
- 2025ApJ...990..145L: Dust sizes 0.9 um–1 cm, -3.5 power law, 3.5 g/cm3, optically thin, Kurucz stellar spectrum
- 2021A&A...656A..68E: Best case: perfectly sampled observation, no noise or atmosphere
- 2024PSJ.....5..125T: Flat or limb-darkened disk starting model at Titan's Band 9 brightness temperature
- 2019ApJ...876...72L: 12C/13C = 68±15 and 32S/34S = 24.4±5.0; same Tex and emitting volume
- 2018ApJ...857...19F: Metallicity from radial gradient, CO(2-1)/CO(1-0)=0.7, R_H2/R_CO=1.2, truncated power-law density with beta=1
- 2020ApJ...898...10T: Disk PA 160 deg, inclination 60 deg, coplanar CBD and CSDs
- 2026ApJ..1000..184N: PA disk 113 deg
- 2026ApJ..1000..184N: distance 140 pc
- 2025A&A...697A..64V: Gas scale height 10 au at 100 au with exponent 1.1; grain sizes 0.005 µm-3 mm, n(a)∝a^-3.5, 100 bins; gas-to-dust 100; Sc=1.5; initial kappa=13.27 cm2/g, T=20(…
- 2025A&A...697A..64V: Stellar radius artificially increased for GO Tau, GW Lup, HL Tau, Oph163131 to warm models
- 2020ApJ...894...74B: distance 400 pc
- 2019A&A...628A.118B: intrinsic QSO continuum variation across spw0/spw1 less than 1%
- 2024ApJ...964..166K: Galactic X_CO=2e20 for normal, 0.5e20 for starbursts and centers
- 2021AJ....161..271F: Toy model inclination 33 deg, stellar mass 1.56 Msun
- 2017ApJ...851..145M: Not corrected for inclination
- 2020ApJ...894...87C: T=20 K masses; k_rho=1.5, a=5/4; alpha_cr = 2a
- 2019A&A...632A..66O: z = 0.1525 for de-redshifting
- 2019ApJ...876..112R: exponential disc (Sersic n=1)
- 2019ApJ...887..209A: Systemic velocities from C18O Gaussian fits; S68Nb1 assumed same as S68Nc1
- 2019A&A...629A.128W: Covering factor f_c = 1, optically thin; OPR = 3
- 2017ApJ...838..114K: T=15 K (10 K gives 2x higher masses; 25 K gives ~2x lower)
- 2020AJ....159...62C: kappa=0.015 cm2/g, beta=1.2, Td=50 K (30 K for source B), dust-to-gas 100, D=2.3 kpc
- 2024ApJ...974..102S: optically thin emission; p = 2.5 or 3.5
- 2018ApJ...866L...6C: fragmentation velocity 10 m/s; dust-to-gas 0.01; a^-3 size distribution of compact silicate grains
- 2016ApJ...816...37V: Thin inclined disk; gas-to-dust ratio ~100
- 2016ApJ...822L..10I: HCN thermalized to J=3 and optically thick; conversion factor 10 Msun/(K km/s pc^2)
- 2024A&A...690A.169L: Optically thin H I
- 2025A&A...700A.285W: alpha_CO = 1/10 of MW value 4.35 (conservative); 1/2 as optimistic
- 2018ApJ...859..111H: LTE with Tgas=Tdust; CO/H2 = 1e-4; freeze-out below 20 K with depletion factor 1000
- 2018AJ....156..239Z: Distance 200 pc, dust-to-gas 100, optically thin emission (so masses are lower limits)
- 2024A&A...686A.201N: geometrically thin disk for inclination lower limit
- 2019ApJ...877L..32M: CO mass upper limit assumes LTE
- 2017ApJ...845..138S: Pure circular rotation; shared centre, Vsys, phi, i across rings
- 2018ApJ...859..165S: inclination from cos i = b/a
- 2020ApJ...892..119M: Cosmology Om=0.3, OL=0.7, H0=70
- 2024A&A...690A..55S: Modified blackbody with beta~1.7
- 2017A&A...600A..72F: Teff 8400 K blackbody, L=10 Lsun, d=117 pc, i=13 deg, PA=5 deg, chi=f_large=0.2, [C]/[H]=2.4e-4
- 2019A&A...632L...7J: flat continuum despite 1-2% change over sideband
- 2019A&A...632L...7J: mu = 5.6±0.1; SFR = 3.6e3 Msun/yr
- 2018A&A...619A..40M: continuous jet flow
- 2015ApJ...812...27A: dust kappa(1 THz)=10 cm2/g, beta=1.46, Tc=28 K, gas/dust=100, d=140 pc
- 2017A&A...602A..19L: distance 353 pc
- 2017A&A...602A..19L: gas-to-dust ratio 100
- 2020A&A...635A.119C: Constant dust temperature and opacity; same attenuation across radial bins
- 2024AJ....167...66Y: common emitting size, Tex and line width under LTE
- 2020ApJ...897..122L: Thin circular disk, constant phi and i with radius; q_min=0.25 for photometric inclination
- 2019A&A...624A.125M: All isotopologues share distribution and velocity profile; column density ratios equal atomic isotopic ratios
- 2019NatAs...3.1109P: Dust mix 60% silicate, 15% amorphous carbon, hollow spheres (max void 0.8), dn/da ~ a^-3.5, dust-to-gas 1/100
- 2025A&A...694A..82S: Terminal metallicity 12+log(O/H)~9.0; primordial inflow
- 2015ApJ...806L..34F: inclination 45 deg, distance 68 Mpc
- 2018A&A...615A.141B: Distance 7.9 kpc
- 2024ApJ...966..117X: distance 2 kpc
- 2018PASJ...70...73H: CO-to-H2 factor 2.0e20 cm-2 (K km/s)-1 with helium factor 1.36
- 2017A&A...605A..21C: All three H2CO lines are co-spatial; fluxes are lower limits
- 2025MNRAS.541.4031D: 13CO optically thin, [12C/13C]=70, temperature effects minor
- 2017A&A...607L...6T: Fixed i=87 deg, M*=0.2 Msun, optically thin, 0.6 km/s dispersion, power-law emissivity
- 2019MNRAS.488.5029H: LFIR integrated over rest-frame 40-120 um
- 2025A&A...695A.149K: 3C84 unpolarized for leakage; 3C286 PA 33 deg
- 2020ApJ...895..119T: Constant density sphere
- 2020ApJ...892...68N: constant M/L, justified by uniform J-H colour
- 2018A&A...616L..10F: gas-to-dust ratio 100; kappa_300um=10 cm2/g with beta=2; T_dust = host core temperature; D=1.3 kpc
- 2018A&A...616L..10F: core scale 0.1 pc where not deconvolvable (upper limit on M_Jeans)
- 2020ApJS..247...61F: Calzetti and SMC attenuation equally weighted
- 2020MNRAS.499.2534K: Virial mass for spherical cloud with 1/r density profile; distance 59 kpc
- 2019ApJ...887...37U: Cosmology Omega_M=0.7, Omega_Lambda=0.3, h=0.70; target z_cen=1.315 for CO(2-1)
- 2018ApJ...868..113T: i = 35.3 deg fixed
- 2018ApJ...862L...2F: LTE, gas-to-dust ratio 100, star mass 0.7 Msun
- 2026A&A...705A.100E: Clump kappa300=10 cm2/g, beta=2, gas-to-dust 100; non-deconvolved sizes for surface density
- 2018A&A...609A..47P: Initial temperature power-law exponent -0.5
- 2017ApJ...850...83F: [CII] contamination by chance negligible (~1-2% of sources, <=10% of continuum)
- 2019ApJ...878...16P: distance 114.4 pc
- 2019ApJ...874L..30V: L_FIR from dust SED with T=47 K, beta=1.6, 42.5-122.5 um
- 2017A&A...607A..55V: Midplane emission constant over the 8 month period
- 2019MNRAS.486..560S: All sources are point-like
- 2016ApJ...827..133L: distance 120 pc
- 2019PASJ...71L...3F: Pulsed component negligible at ALMA bands
- 2018ApJ...869L..46D: Gas temperature equals dust temperature


### Limitations the authors admit
- 2018ApJ...852..122H: Models are not optimal; dust modeling and multi-line fitting deferred; perturbed temperature model not physically self-consistent
- 2018ApJ...852..122H: Absolute alpha uncertain by ~0.4 from flux calibration
- 2017ApJ...846..108C: CO detection is only ~3 sigma peak SNR so 2D CO kinematics and central detail are limited
- 2017ApJ...846..108C: ALESS67.2 nature inconclusive
- 2019ApJ...874...89C: Mass uncertainty ~50% due to distance and opacity
- 2019ApJ...874...89C: Smooth model underestimates peak flux because extended structure is filtered
- 2018ApJ...866..117C: AGN continuum non-detection may reflect lack of sensitivity
- 2020ApJ...899...10T: Continuum-only substructure cannot be distinguished from artifacts at low contrast
- 2020ApJ...899...10T: Mass uncertainty dominated by assumed dust opacity
- 2020MNRAS.493.4294B: Uncertainty in C not included in M_dyn; CMB attenuation of [C II] not corrected; resolution does not resolve outflow regions
- 2024ApJ...963..164R: Low number of pairs prevents determining exact aligned fraction
- 2024ApJ...963..164R: Continuum only: cannot distinguish aligned from anti-aligned disks
- 2025ApJ...993...85Y: Ring clumps only 3-5 sigma; higher SNR needed to confirm the SW clump
- 2025ApJ...993...85Y: Low spectral index evidence tentative
- 2020ApJ...895...84Y: SpM images have larger asymmetric residuals due to self-calibration with MS-CLEAN; degree of super-resolution for Data 2 not established
- 2014ApJ...797...27F: Masses uncertain to factors of a few
- 2024ApJ...972..111L: Only projected distances and radial velocities known; spatial offset of redshifted [C II] smaller than beam
- 2019A&A...630A..59B: Interferometric data may miss extended diffuse emission; stacking dilutes orientations
- 2018A&A...614A..58B: Inner disk and width poorly constrained; mass depends on CO abundance and distance; LTE assumption; temperature uncertain
- 2015Natur.522..455C: Dynamical masses very uncertain due to low spatial resolution
- 2012ApJ...757..129R: Model parameters are not unique nor optimized; limited resolution
- 2020MNRAS.496.4061D: Keplerian rise not resolved; result depends on stellar mass model and Gamma
- 2020MNRAS.496.4061D: Low Gamma should be treated with caution; beam correlations neglected
- 2018MNRAS.475.4924K: Vertical extent is smaller than the beam, so the vertical resolution conclusion is cautious; tests not exhaustive.
- 2018MNRAS.475.4924K: Dust mass has large systematic uncertainty from arbitrary opacity.
- 2025MNRAS.541.2540Z: Circular-orbit assumption with mild non-circular motions; distance uncertainty (10%) not included in budget
- 2015ApJ...813..118M: Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2
- 2024A&A...682A.166F: Simple geometry and single homogeneous cloud; continuum and CO SLED not modeled
- 2018MNRAS.475..448T: Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density
- 2018MNRAS.475..448T: ALMA continuum lacks single-dish data so flux is underestimated
- 2019AJ....158...76C: Limb retrievals are approximate due to coarse resolution and simplified polygonal parameterization
- 2019AJ....158...76C: Lifetime derivation relies on gross assumptions
- 2016PASJ...68...88K: Missing flux on large scales due to no Total Power Array
- 2020A&A...634A...9M: Core result holds only if thermal contamination of 108 GHz flux is below ~80%, which is poorly constrained
- 2015ApJ...814..143A: Smooth spherical shell model does not reproduce fine structure; infrared pumping only partly included
- 2019ApJ...882..118X: Uncertainties may be underestimated since continuum subtraction systematics not included
- 2017A&A...600A...8D: Observations not strictly simultaneous; 4U 1728-34 in transitional state
- 2020MNRAS.495..943H: CO recoverable scale ~4 arcsec means much extended flux missing; CO deconvolution leaves negative regions; arbitrariness of fragment definition
- 2020ApJ...898..146M: Total belt flux is model-dependent due to extrapolation to zero uv distance; position angle and inclination unconstrained
- 2020ApJ...898..146M: Low target elevation and antenna shadowing
- 2026A&A...705A.198M: Optically thick masses are lower limits; inner radii are upper limits; degeneracy thick/thin needs radiative transfer
- 2020A&A...642A..96P: Limits are less constraining than the 4-8 GHz limits given the expected spectral index; only a single few-hour epoch.
- 2020ApJ...888L..28S: Width comparable to beam, so the actual width may be narrower
- 2020ApJ...888L..28S: Only relative brightness temperatures because single-dish data not combined
- 2019ApJ...876L..10E: ALMA 100 GHz limit is too shallow to constrain a star formation origin
- 2020ApJS..251...14H: Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2
- 2025ApJ...986L..22R: Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower
- 2024A&A...689A.317G: In-falling component size is not conclusive
- 2015ApJ...798..124R: Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density
- 2024ApJ...968L..19F: Collisional rate coefficients for PH3-H2 unavailable; extended continuum emission resolved out may explain lower N(H2)
- 2023PSJ.....4..142C: cost function formally limited to independent data points
- 2023PSJ.....4..142C: single observation of leading hemisphere only
- 2015ApJ...803...97S: Many lines blended; Hot Core v_t=2 T_rot not determinable
- 2016A&A...593A..61M: Differential RM imaging with polarized fiducial element can be biased by up to ~30%.
- 2025A&A...696A.100G: Exact chemical pathways and relative contributions of bottom-up and top-down processes remain unquantified; models omit PAH chemistry
- 2020MNRAS.498L..87B: Emission unresolved; cannot distinguish envelope from disk; S hot corino needs higher resolution
- 2020ApJ...895...64L: Origin of time-varying systematics (e.g. XY phase) not investigated; second-order corrections beyond scope
- 2024ApJ...970...56P: VLA bands observed sequentially, not simultaneously, so no instantaneous spectrum.
- 2014ApJ...792L...2C: Lack of short baselines prevents ruling out additional H2CO sources with sizes >= 5 arcsec
- 2014ApJ...795L..25R: Core unresolved so density is a lower limit; deviation may be from temperature
- 2015A&A...573L...4L: Sparse spectral sampling prevents a conclusive statement on changing opacities
- 2015ApJ...808L...1A: Only one weather station available, degrading astrometry relative to predicted 0.18 mas
- 2024ApJ...963....1O: X_CO uncertainty may overestimate molecular mass by a factor of a few
- 2024ApJ...963....1O: Chandra data too shallow to resolve cavity
- 2019MNRAS.488.1005P: System ages uncertain by ~50%
- 2019MNRAS.488.1005P: Gas (CO) not analysed
- 2014ApJ...784...78R: Cannot tell whether gas lies in front of or behind the BCG
- 2017A&A...604A.115V: Flux measurements of 1b+3b are highly uncertain because of source shape
- 2014ApJ...790..160S: Outflow quantities order-of-magnitude; XCO and line ratio uncertain
- 2017A&A...605A..78A: 100 GHz results 30-55'' from the limb may be affected by the 60'' beam
- 2019ApJ...871....5T: The ring width is comparable to the beam, so the estimates are tentative; the model is not a full fit and the HCO+ pattern is not reproduced.
- 2019ApJ...876..130H: Single dust temperature assumed across sources, affecting Sigma_SFR maps
- 2019ApJ...876..130H: Interpretations require kinematic confirmation; small sample
- 2019A&A...631A..64B: Some channels not cleaned to threshold in combined 12CO image
- 2019ApJ...881...10B: Model not a formally acceptable fit (chi^2_nu=1.179); correlated noise; local irregularities in velocity/dispersion fields
- 2019ApJ...881...10B: Distance disagreements among estimates imply M_BH may lie in (2.0-3.8)e9 Msun
- 2020ApJ...890..130T: Optically thick emission yields mass underestimates; envelope contamination possible; Gaussian radius biases
- 2020ApJ...897...91G: Three sources lack NIR counterparts and are likely false detections
- 2025A&A...696A.150S: findcont conservative in line-rich sources; no manual continuum ranges
- 2025A&A...696A.150S: TM1-only line cubes not produced in first release
- 2024ApJ...971..129C: Only two bands constrain four parameters; priors needed; porosity unconstrained
- 2020ApJ...891...48H: Temperature, flux calibration and degeneracies prevent precise grain size measurements
- 2014A&A...569A..11S: Extended emission resolved out; H13CO+ linewidths are lower limits; missing flux affects abundances.
- 2024ApJ...968....9W: Marginal resolution, assumed T_dust, and uncertain inclination give large uncertainties in M_dyn and SFR
- 2018Sci...362.1034D: U1 may be at a different redshift; stellar mass and SFR uncertain by factor of 2
- 2017ApJ...841..110S: Envelope size only a lower limit because CO is in absorption
- 2015ApJ...807..128S: Small number statistics at both ends of the counts
- 2015ApJ...811...92C: Model is parametric, not dynamically consistent, no systematic parameter search
- 2015ApJ...811...92C: MEM resolution varies with image
- 2020MNRAS.495.3840M: alpha_CO may be a factor of a few lower in the bar, so Sigma_mol could be overestimated
- 2020MNRAS.495.3840M: SFR below 1e-3 Msun/yr/kpc2 should be considered upper limits
- 2016ApJ...829....6W: CO mass assumes optically thin LTE and could be larger by a factor of a few or more
- 2016ApJ...829....6W: Debris mass depends strongly on assumed size distribution, density, albedo
- 2025ApJ...992..211N: Distance uncertainty (69.3 vs 46.4 Mpc) gives ~30% systematic in MBH, dominant error
- 2015Natur.525..218R: NW ALMA flux is lower than APEX; may reflect different line ratio, weak emission or resolved-out extended emission
- 2024ApJ...975..103P: 1.3 mm and 3.5 mm emission may not arise from same location; limited resolution hinders HST-1 vs inner jet attribution
- 2019ApJS..244...25S: Spectra assume source at phase center; positional errors can cause non-detections; SiO variability makes brightness only indicative
- 2016ApJ...821L...8S: Unquantified systematic errors (disc-averaged temperature, Voigt profile, line-broadening coefficients)
- 2018ApJ...865...13T: X_CO uncertainty may overestimate mass by a factor of a few
- 2018ApJ...865...13T: Projection effects: motions in plane of sky unknown
- 2021ApJ...908..231M: Small and possibly biased sample
- 2021ApJ...908..231M: Surface density depends on alpha_CO choice
- 2015A&A...577L...4V: Band 3 resolution too poor to confirm the hotspot there; 25 Oct Band 3 epoch affected by resolved calibrator
- 2019A&A...628A..10B: Line-continuum splitting is preliminary with unexplained baseline artifacts
- 2018MNRAS.481.4931E: Velocity resolution is modest and dynamical modelling is deferred.
- 2020A&A...644A..59K: Errors underestimated; isothermal assumption fails in center; SO2 fits unsatisfactory
- 2020A&A...644A..59K: Beam filling factors set to 1; no collisions with e- and H
- 2020AJ....159..288M: Coarse resolution; disk width fixed; contamination by faint background sources cannot be ruled out
- 2020AJ....159..288M: Dust opacity systematics not in error budget
- 2025ApJ...990..145L: Massless-disk N-body ignores self-gravity; noise non-Gaussian near minor axis; residuals suggest width at apocenter not quite right
- 2021A&A...656A..68E: Best-case scenario without noise, atmosphere, imaging artifacts; static slightly eccentric beam; correction factors not for one-to-one correction
- 2019ApJ...884L..58U: Non-simultaneous multi-wavelength polarimetry limits conclusions
- 2020ApJ...894L..14L: Dust temperature at 2000 AU unknown, strongly affects masses
- 2020ApJ...894L..14L: Cannot tell whether cores are prestellar or protostellar
- 2024PSJ.....5..125T: Low S/N of CH3D prevents vertical profile; CH4 inference relies on prior D/H; beam smooths latitudinal structure
- 2024A&A...686A.274V: Spatial filtering resolves out much CO flux, overestimating polarisation fractions by factor 2-3.
- 2024A&A...686A.274V: Circular polarisation of extended lines dominated by beam effects; no test of anisotropic resonant scattering.
- 2013ApJ...762L..21M: Spectral index of central peak poorly constrained; inner belt interpretation needs higher resolution
- 2024IJAsB..23...14M: Hyperfine lines unresolved and source not spatially resolved
- 2023PSJ.....4..193B: Two Orcus epochs have much larger errors due to poor conditions and compact configuration

### Settings cards flag as needed but not stated
- casa version: 118
- self-calibration solution intervals: 54
- image size and cell size: 43
- line-free channels and continuum subtraction method: 38
- continuum subtraction and line-free channels: 38
- self-calibration solution intervals and number of iterations: 36
- flux scale uncertainty: 34
- flux calibrator and flux scale uncertainty: 31
- line-free channels used for continuum: 29
- casa version and pipeline version: 28
- line-free channels for continuum subtraction: 25
- line-free channels used for continuum subtraction: 23
- primary beam correction details: 22
- line-free channel ranges: 20
- line-free channels used for uvcontsub: 16
- self-calibration solution intervals and reference antenna: 15
- self-calibration solution intervals and number of rounds: 14
- source coordinates: 13
- cell size and image size: 13
- line-free channels for uvcontsub: 12
- line-free channel ranges for continuum subtraction: 12
- pipeline version: 11
- line-free channel ranges for uvcontsub: 11
- cell and image size: 11
- line-free channel ranges for continuum: 11
- flux calibrators and flux scale uncertainty: 11
- casa/pipeline version: 11
- flux calibration uncertainty: 10
- primary-beam correction details: 10
- clean threshold, masks, cell and image size: 10
- self-calibration, if any: 9
- casa version and calibration procedure: 9
- primary beam correction: 9
- uvmodelfit starting parameters: 8
- line-free channel selection: 8
- casa version and whether the pipeline or manual calibration was used: 8
- image size, cell size, clean threshold and masks: 8
- continuum subtraction method and line-free channels: 8
- line-free channels and continuum subtraction details: 8
- casa version and whether pipeline or manual calibration: 8

## Paper excerpts (40 of 1121, chosen for detail and spread over fields/years)

### 2018ApJ...852..122H: CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations (2018; protoplanetary_disks, astrochemistry; archival_reuse)
- question: What are the CO and dust properties (CO column density structure, spectral index/grain sizes) in the TW Hya disk at high angular resolution?
- processing.imaging.weighting_robust: Band 6 image robust=0.5; combined spectral index image robust=0; 12CO robust=1.0; 13CO robust=0 [$^{12}$CO $J=3-2$ Data Reduction: "Briggs weighting (robust = 1.0)"] [Continuum Reduction: "Briggs weighting (robust $=0.5$)"]
- processing.imaging.deconvolver: multi-scale CLEAN [$^{12}$CO $J=3-2$ Data Reduction: "The $^{12}$CO datasets were then imaged together with the multi-scale CLEAN algorithm (as implemented in the `tclean` task in `CASA 5.0`)"]
- processing.imaging.multiscale_scales: 12CO: 0, 0.2, 0.4, 0.8, 1.6, 3.2 arcsec; Band 6: 0, 0.06, 0.15, 0.3, 0.6 arcsec [$^{12}$CO $J=3-2$ Data Reduction: "using scales of 0$''$, 0$\ensuremath{''}$2, 0$\ensuremath{''}$4, 0$\ensuremath{''}$8, 1$\ensuremath{''}$6, and 3$\ensuremath{''}$2"]
- step 1: Reduce and combine archival continuum data
  - method: Calibrate, flag line channels, average line-free channels, phase self-calibrate, align phase centers with fixvis/fixplanets, image Band 6 with MS-MFS [Continuum Reduction: "Because of the relatively large proper motion of TW Hya, the `fixvis` and `fixplanets` tasks in `CASA` were used to shift the datasets to a common phasecenter."]
  - software: CASA
  - parameter: robust=0.5; scales 0, 0.06, 0.15, 0.3, 0.6 arcsec [Continuum Reduction: "Briggs weighting (robust $=0.5$) and scales of $0''$, 0$\ensuremath{''}$06, 0$\ensuremath{''}$15, 0$\ensuremath{''}$3, and 0$\ensuremath{''}$6 were used."]
  - validation: Continuum fluxes of self-calibrated images agree within 5% within each band; compared with published images [Continuum Reduction: "The continuum fluxes from the self-calibrated images were within 5% of one another within each band"]
- step 2: Make 290 GHz spectral index map
  - method: Joint imaging of Band 6+7 with multi-term MFS (nterms=2), spectral index computed where intensity exceeds 5 sigma [Continuum Reduction: "The spectral index is computed only for pixels where the intensity image exceeds 0.1 mJy beam$^{-1}$ (5 $\times$ the rms noise)."]
  - software: CASA
  - parameter: nterms=2, robust=0, i=5 deg, PA=152 deg [The Spectral Index Between 1.3 mm and 8…: "The adopted position angle and inclination are 152 and 5 degrees, respectively"]
  - assumption: M* = 0.88 Msun, distance 59.5 pc [The Spectral Index Between 1.3 mm and 8…: "We favor the higher stellar mass value of 0.88 $M_\odot$"]
  - validation: Compared with 190 GHz spectral index of Tsukagoshi et al. [Observational results, The Spectral Ind…: "Our 290 GHz spectral index map, which has an angular resolution about a factor of two higher than the map from (cite: 2016ApJ...829L..35T), now confirms the presence of the latter two peaks."]
- step 3: Image 12CO J=3-2 cube and derive moment/peak Tb maps
  - method: Self-calibrate, uvcontsub, mstransform to 0.25 km/s, multi-scale tclean, impbcor; integrated intensity above 3 sigma; peak Tb via Planck law, median of three offset cubes [12CO J=3-2 Peak Brightness Temperatures: "A peak brightness map is computed by taking the maximum value along the frequency axis for each pixel in the image cube and then converting to a brightness temperature using Planck’s law"]
  - software: CASA
  - parameter: integration -1.91 to 7.59 km/s; 3 sigma clip [$^{12}$CO $J=3-2$ Data Reduction: "An integrated intensity map was produced by summing emission above the $3\sigma$ level in the velocity range from $-1.91$ to 7.59 km s$^{-1}$."]
  - validation: Imaged without continuum subtraction; integration limits changed flux <0.1% [$^{12}$CO $J=3-2$ Data Reduction: "truncating or extending the integration range by a few channels changed the integrated flux by less than $0.1\%$"]
- result: 12CO integrated flux (r<4 arcsec) = 42.7 ± 0.2 Jy km/s [12CO J=3-2 Emission Morphology: "The integrated flux, measured inside a circular mask with a radius of $4''$, is 42.7$\pm0.2$ Jy km s$^{-1}$."]
- result: 12CO emission extent (3 sigma) = 3.6 arcsec (215 AU) ± not stated arcsec [12CO J=3-2 Emission Morphology: "$^{12}$CO emission exceeding the $3\sigma$ level extends to a radius of $\approx 3.6\ensuremath{''}$ (215 AU)"]
- result: 12CO/13CO flux ratio in outer annulus (101-214 AU) = ~20 ± not stated dimensionless [Comparison to other CO isotopologues: "Inside this annulus, the $^{12}$CO/$^{13}$CO flux ratio is $\approx20$"]
- result: Spectral index in rings = 1.7-2.2 ± scatter dimensionless [The Spectral Index Between 1.3 mm and 8…: "$\alpha$ values range from 1.7 to 2.2, taking the scatter into account"]
- result: Spectral index peaks at gaps (25, 41, 47 AU) = ~2.6-2.7 ± not stated dimensionless [The Spectral Index Between 1.3 mm and 8…: "$\alpha$ peaking at $\sim2.6-2.7$ near the locations of the continuum emission gaps at 25, 41, and 47 AU"]
- result: Peak 12CO brightness temperature 25-90 AU = ~70 to 35 ± not stated K [12CO J= 3-2 Peak Brightness Temperatures: "The peak brightness temperatures between radii of 25 and 90 AU range from $\sim$70 to 35 K"]
- limitation (authors): Models are not optimal; dust modeling and multi-line fitting deferred; perturbed temperature model not physically self-consistent [A “Perturbed Temperature" Model: "this model is not physically self-consistent"]
- limitation (authors): Absolute alpha uncertain by ~0.4 from flux calibration [The Spectral Index Between 1.3 mm and 8…: "A $\sim10\%$ flux uncertainty in each band would correspond to an uncertainty in the overall offset of $\Delta \alpha\sim0.4$"]
- not stated (card): Self-calibration solution intervals and number of iterations; Line-free channel ranges for continuum and uvcontsub; Image size and cell size for clean/tclean; clean thresholds and number of iterations; Exact spectral windows used per program; Procedure for how model parameters were chosen beyond 'some experimentation' (no fit/goodness metric); Radial bin and deprojection details for profiles

### 2017ApJ...846..108C: A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1 (2017; high_z_galaxies; observational_alma_primary)
- question: How do the sizes, spatial distributions and kinematics of dust, CO gas, H II regions and stars compare in the z=2.12 SMG ALESS67.1, and what does this imply for alpha_CO, IRX-beta and the Schmidt-Kennicutt relation?
- processing.imaging.weighting_robust: natural weighting (both bands) [2.1 ALMA 870 μm continuum: "The *uv*–data were inverse Fourier–transformed using natural weighting to produce the dirty continuum image"]
- processing.imaging.uv_taper: tapering tried to test for resolved-out ALESS67.2; parameters not stated [3.1 ALMA 870 μm continuum: "We have tried tapering the map to lower spatial resolution in order to test the possibility that the lack of detection is due to extended structures"]
- step 1: Image Band 7 continuum and measure flux and size
  - method: Natural-weight dirty image, clean a 1'' circle to 2 sigma; uvmodelfit Gaussian fit to the uv data, cross-checked with imfit and sextractor [3.1 ALMA 870 μm continuum: "we first use the uvmodelfit algorithm to model the *uv*–data. We find that the best bit (reduced $\chi^2$=0.5) Gaussian profile has an intensity of 3.7$\pm$0.2 mJy"]
  - software: CASA uvmodelfit, imfit, sextractor
  - fitting: Gaussian profile, chi-square fit in uv plane [3.1 ALMA 870 μm continuum: "the best bit (reduced $\chi^2$=0.5) Gaussian profile"]
  - validation: Consistent with imfit and sextractor on cleaned image [3.1 ALMA 870 μm continuum: "We obtain consistent results if we instead using the imfit algorithm or sextractor on the cleaned image."]
- step 2: Extract CO(3-2) spectrum and line properties
  - method: Iterative procedure: weight-averaged map over best-guess width, curve-of-growth aperture, clean to 2 sigma, Gaussian fit, update FWHM until convergence [3.2 ALMA 12CO J=3–2: "Next the extracted spectrum is fitted with a Gaussian profile and the frequency width used for obtaining the averaged map is updated to be the FWHM of the spectral fit."]
  - software: CASA
  - parameter: line flux contained within 2'' circular radius [3.2 ALMA 12CO J=3–2: "all the line flux is contained within a circular radius of 2$''$"]
  - fitting: Gaussian fit; errors from fit and Monte Carlo injection of model profiles in random cube regions [3.2 ALMA 12CO J=3–2: "We create fake spectra by injecting model profile into spectra extracted from randomly selected regions of the data cube"]
  - validation: Fit errors consistent with Monte Carlo errors [3.2 ALMA 12CO J=3–2: "The errors are estimates from the fit, and they are consistent with the errors derived from a Monte Carlo simulation."]
- result: 870 um Gaussian flux density = 3.7 ± 0.2 mJy [3.1 ALMA 870 μm continuum: "has an intensity of 3.7$\pm$0.2 mJy"]
- result: 870 um continuum half-light radius (circularized) = 1.2 ± 0.1 kpc [5 Summary: "finding 1.2$\pm$0.1 kpc (circularized) for 870 $\mu$m (rest-frame 280 $\mu$m) continuum"]
- result: CO(3-2) redshift = 2.1196 ± 0.0009 dimensionless [3.2 ALMA 12CO J=3–2: "$z=2.1196\pm0.0009$"]
- result: CO(3-2) line flux = 4.2 ± 1.2 Jy km/s [3.2 ALMA 12CO J=3–2: "we derive a total line flux of 4.2$\pm$1.2 Jy km s$^{-1}$"]
- result: CO(3-2) line FWHM = 862 ± 195 km/s [3.2 ALMA 12CO J=3–2: "with a velocity FWHM of 862$\pm$195 km s$^{-1}$"]
- limitation (authors): CO detection is only ~3 sigma peak SNR so 2D CO kinematics and central detail are limited [4.1 Kinematics – CO and Halpha: "Our $^{12}$CO(J=3-2) detection does not have high enough SNR to produce 2D kinematic maps like H$\alpha$"]
- limitation (authors): ALESS67.2 nature inconclusive [3.1 ALMA 870 μm continuum: "so the nature of ALESS67.2 remains inconclusive"]
- not stated (card): CLEAN threshold, iterations and any robust/taper values for Band 7 and Band 3 imaging; Calibration details for Band 7 (pipeline/manual, CASA version); Line-free channels and continuum subtraction for CO cube; frequency width of averaged CO map; SINFONI reduced cubes (custom routines not released); MCMC priors, walkers and chain length for the rotating disk fit; uvmodelfit starting parameters; Inc…

### 2019ApJ...874...89C: The Central 1000 au of a Pre-stellar Core Revealed with ALMA. I. 1.3 mm Continuum Observations (2019; star_formation; observational_alma_primary)
- question: What is the structure of the central ~1000 au of the pre-stellar core L1544 in 1.3 mm dust continuum, and is there real fragmentation or are substructures interferometric artefacts?
- processing.imaging.weighting_robust: robust 0.5 [2 Observations: "a robust weighting of 0.5, and a taper of 1.5$^{\prime\prime}$"]
- processing.imaging.deconvolver: multi-scale clean [2 Observations: "we use the multi-scale clean technique"]
- processing.imaging.uv_taper: 1.5" [2 Observations: "a robust weighting of 0.5, and a taper of 1.5$^{\prime\prime}$"]
- processing.imaging.multiscale_scales: [0, 2, 6, 18] arcsec [2 Observations: "with the multi-scale parameter of \[0, 2, 6, 18\] arcsec"]
- step 1: Calibrate and jointly image ACA+12m continuum
  - method: Calibrate in CASA, reweight with statwt, joint multi-scale mfs clean [2 Observations: "We perform a joint de-convolution of both datasets (ACA and 12-m array) in CASA (version 4.4.0) using multifrequency synthesis (*mfs*)"]
  - software: CASA
  - parameter: robust 0.5, taper 1.5", scales [0,2,6,18]" [2 Observations: "a robust weighting of 0.5, and a taper of 1.5$^{\prime\prime}$"]
- step 5: Fit smooth elongated model and test substructure
  - method: Fit F(r)=F0/(1+(r/Rflat)^alpha) with elliptical radius by chi2 minimisation over 50% PB region; simulate observations, residuals; 100 simulations with different hour angles using baselines >13 klambda, natural weighting [4.2 The smooth elongated structure deri…: "The best-fit model is calculated by minimising the $\chi^2$ of the flux difference between the model (after applying the primary beam correction) and the combined ACA+Main Array data"]
  - software: CASA simobserve
  - parameter: 100 models, Cycle 1 configuration 2, baselines >13 klambda [4.2.1: "We run 100 models with different starting hour-angles to generate different $uv$-coverage."]
  - fitting: chi2 minimisation; peak flux fixed [4.2 The smooth elongated structure deri…: "The peak value is fixed and the minimisation is carried out over the region with primary beam response higher than 50%."]
  - validation: Residuals show no significant fragments; simulated images reproduce similar substructure [4.2.1: "small substructures similar to those identified in the ALMA data of L1544 can be produced when a radial emission profile with a flat central section is used as input image"]
- result: Best-fit smooth model Rflat = 10.84 (1463 au) ± not stated arcsec (au) [4.2: "$R_{\rm flat}$=10.84$^{\prime\prime}$ (equivalent to 1463 au), $\alpha$=2.32, $AR$=1.83"]
- result: Best-fit smooth model alpha = 2.32 ± not stated dimensionless [4.2: "$\alpha$=2.32, $AR$=1.83, position angle PA=166$^{\circ}$"]
- result: Best-fit model F0 = 0.772 ± not stated mJy/beam [4.2: "$F_0$=0.772 mJy beam$^{-1}$"]
- limitation (authors): Mass uncertainty ~50% due to distance and opacity [Footnote 1: "effectively increase this error to about 50 $\%$ of the measured value"]
- limitation (authors): Smooth model underestimates peak flux because extended structure is filtered [4.3: "the peak flux of the simulated combined image was underestimated because the model was constructed from the ALMA data"]
- not stated (card): Image size and cell size; Clean threshold, masks and iteration count; Whether continuum channels were selected/line-free; no continuum subtraction details; Pointing/phase centre coordinates; Simulation inputs: simobserve integration times, precipitable water vapour, thermal noise settings; How the 5-sigma contour area was converted to a radius (elliptical vs circular); Details of the MHD/HD simul…

### 2018ApJ...866..117C: ALMA Observation of NGC 5135: The Circumnuclear CO (6-5) and Dust Continuum Emission at 45 pc Resolution (2018; nearby_galaxies, agn_and_quasars, star_formation; observational_alma_primary)
- question: What are the properties of the circumnuclear CO (6-5) and 435 um dust emission in NGC 5135, what is the AGN contribution, and what heats the CO (6-5) gas?
- processing.imaging.weighting_robust: Briggs, robust = 0.5 [2 Observation: "The calibrated images were cleaned using the Briggs weighting (with the parameter “robust” set to 0.5)."]
- processing.imaging.uv_taper: outertaper = 0.4" for 0.4" x 0.4" beam [3.1 CO (6-5) Line Emission: "by applying an uv-taper (with the parameter “outertaper” = 0.4$''$) to our uv data before imaging"]
- step 1: Image line cube and continuum
  - method: Clean with Briggs weighting; line from one SPW, continuum from the other three; uv-taper version also made [2 Observation: "The CO (6-5) line data cube was generated using the data in the SPW covering the sky frequency range of 680.975 to 682.975 GHz."]
  - software: CASA
  - parameter: robust = 0.5; outertaper = 0.4" [2 Observation: "Briggs weighting (with the parameter “robust” set to 0.5)"]
- step 2: Moment maps and total fluxes
  - method: Moment 0 integrated 3971-4157 km/s; moments 1 and 2 with 4 sigma_ch threshold on uv-tapered image [3.1 CO (6-5) Line Emission: "We set the threshold at 4-$\sigma_{\rm ch}$, where $\sigma_{\rm ch}$ is the r.m.s noise per frequency channel,"]
  - software: CASA
  - assumption: Radio velocity convention nu_obs = nu_rest(1 - V/c) [3.1 CO (6-5) Line Emission: "$\nu_{\rm obs} = \nu_{\rm rest}\,(1 - V/c)$"]
  - validation: Compared with Herschel total flux [3.1 CO (6-5) Line Emission: "Therefore the clump regions in Fig. 1a together account for $\sim$32% of the total CO (6-5) flux of the galaxy."]
- step 4: Clump parameters
  - method: 2D Gaussian fit to clump maps; CLUMPFIND variant for blends; deconvolve beam; extract spectra in elliptical apertures [4.2 Properties of Molecular Gas Clumps: "These were derived from a 2d Gaussian fit to the clump intensity map."]
  - software: CASA, CLUMPFIND
  - fitting: 2D Gaussian [4.2 Properties of Molecular Gas Clumps: "These were derived from a 2d Gaussian fit to the clump intensity map."]
- step 5: Virial and molecular gas masses
  - method: M_vir = 5 dV^2 R / G; M_mol from 435 um flux via Scoville et al. 2016 and from CO flux with alpha_CO [4.2 Properties of Molecular Gas Clumps: "the Virial mass ($M_{vir}$) is estimated as"]
  - parameter: dV deconvolved with 13.5 km/s channel; 10 km/s rotation removed; flux x1.731 for total [4.2 Properties of Molecular Gas Clumps: "Thus, we multiply the flux density by 1.731 to estimate the total flux."]
  - assumption: T_d = 25 K [4.2 Properties of Molecular Gas Clumps: "assuming a dust temperature of the 25 K"]
  - assumption: alpha_CO = 0.8; CO(6-5)/CO(1-0) ~ 2 [4.2 Properties of Molecular Gas Clumps: "The ${\mathrm{CO}}\,(6\text{--}5)$ /${\mathrm{CO}}\,(1\text{--}0)$ is about 2"]
  - validation: Dust-derived M_mol consistent with CO-derived [4.2 Properties of Molecular Gas Clumps: "The molecular gas mass derived this way is consistent with the one derived from the dust continuum as shown in Column (12) of Table 2."]
- result: Total CO(6-5) flux of four regions = 512 ± 24 Jy km/s [3.1 CO (6-5) Line Emission: "The total CO (6-5) flux from the combined four regions in Fig. 1a is 512 $\pm$ 24 Jy km s$^{-1}$."]
- result: Total CO(6-5) flux in 0.4" tapered image = 841 ± 45 Jy km/s [3.1 CO (6-5) Line Emission: "is 841 $\pm$ 45 Jy km s$^{-1}$"]
- result: 435 um continuum flux of four regions = 181 ± 25 mJy [3.2 Dust Continuum Emission: "we derived a total flux of 181 $\pm$ 25 mJy for the 435$\,\mu{\rm m}$ continuum emission"]
- result: Fraction of Herschel CO(6-5) flux in ALMA regions = ~32 ± not stated percent [3.1 CO (6-5) Line Emission: "account for $\sim$32% of the total CO (6-5) flux of the galaxy"]
- result: Clump radii range = 45-180 ± not stated pc [4.2 Properties of Molecular Gas Clumps: "the radii range from 45 to 180 pc for the clumps"]
- result: Clump line widths = 60-88 ± not stated km/s [4.2 Properties of Molecular Gas Clumps: "The resulting $\Delta V_{\rm FWHM}$ ranges from 60 to 88 km s$^{-1}$."]
- result: Virial masses = ~7 to 60 x 10^7 ± not stated Msun [4.2 Properties of Molecular Gas Clumps: "rage from $\sim$7 to 60 $\times 10^7\,M_{\odot}$"]
- result: Molecular gas masses (dust) = ~1 to 10 x 10^8 ± not stated Msun [4.2 Properties of Molecular Gas Clumps: "ranges from $\sim$1 to 10 $\times 10^8\,M_{\odot}$"]
- limitation (authors): AGN continuum non-detection may reflect lack of sensitivity [5 Summary: "the non-detection in continuum emission may simply reflect the lack of sensitivity in our observation."]
- not stated (card): Calibrator names other than the phase calibrator (bandpass, flux) and flux scale; Whether the pipeline or manual calibration was used; Self-calibration, if any; Line-free channel selection and continuum subtraction method; Clean threshold, mask, niter, image size, cell size, deconvolver; Exact aperture definitions for clump spectra and total flux regions; CO(6-5)/CO(1-0) ratio basis and derivatio…

### 2020ApJ...899...10T: FRagmentation and Evolution of Dense Cores Judged by ALMA (FREJA). I. Overview: Inner ∼1000 au Structures of Prestellar/Protostellar Cores in Taurus (2020; star_formation; large_program_or_survey)
- question: What are the inner ~1000 au structures of prestellar/protostellar cores in Taurus, and how long do high-density prestellar cores last before protostar formation?
- processing.imaging.weighting_robust: Natural [2.2 Observations: "The weighting scheme was $``$Natural.$"$"]
- processing.imaging.deconvolver: multiscale [2.2 Observations: "we used the `tclean` task with the `multi-scale` deconvolver (cite: Kepley20) to recover the extended emission."]
- processing.imaging.multiscale_scales: 0, 6, 18 pixels [2.2 Observations: "the scales of the `multi-scale` clean are 0, 6, and 18 pixels."]
- step 1: Image continuum and measure source properties
  - method: tclean multiscale natural-weighted continuum imaging, then 2D Gaussian fits after primary beam correction; rms from emission-free pixels [2.2 Observations: "We manually selected emission-free pixels from each continuum image to estimate their rms noise levels."]
  - software: CASA
  - parameter: scales 0,6,18 pix; 1'' pixels; natural weighting; 3 sigma detection threshold [3.1 Prestellar Cores: "We could not detect significant ($>$3$\sigma$) emission in 20 prestellar cores"]
  - fitting: 2D Gaussian in image plane [3.1 Prestellar Cores: "We performed 2D Gaussian fittings to the observed continuum distributions in the image plane"]
  - validation: Two continuum bands compared for MC1 and MC35 [7.1: "Figure [8](#fig:cont1-2) shows that the two frequency images reproduce almost the same result."]
- step 3: Test whether substructures are interferometric artifacts
  - method: simobserve and tclean of smooth Plummer-like cores compared with observations; plus C18O and N2D+ line distributions [4.1: "In the CASA simulator, we used the `simobserve` task to generate simulated visibilities at a central frequency of 225 GHz"]
  - software: CASA simobserve, tclean
  - parameter: p=2; R_flat 8000,2500,1500,900,300 au; aspect ratios 1.0 and 1.8; kappa=0.005, Td=10 K [4.1: "We adapted two aspect ratios of 1.0 and 1.8."]
  - assumption: Td = 10 K, kappa = 0.005 cm2/g [4.1: "we assumed $\kappa_{\rm 1.3\,mm}$ = 0.005 cm$^{2}$ g$^{-1}$ and $T_{\rm d}$ = 10 K"]
  - validation: MC31 real vs synthetic residual comparison [7.3: "The residual image does not show large differences between the real and synthetic observations."]
- result: Prestellar cores with continuum detection = 12 of 32 (about one-third) ± not stated cores [3.1 Prestellar Cores: "we confirmed continuum detection toward 12 prestellar cores"]
- result: Prestellar peak flux range = 2-5 ± not stated mJy/beam [3.1 Prestellar Cores: "are 2–5 mJy beam$^{-1}$ and 5–63 mJy, respectively"]
- result: Prestellar total flux range = 5-63 ± not stated mJy [3.1 Prestellar Cores: "are 2–5 mJy beam$^{-1}$ and 5–63 mJy, respectively"]
- result: Protostellar total flux range = 62-225 ± not stated mJy [3.2 Protostellar Cores: "The observed total and peak fluxes are 62–225 mJy and $\sim$14–202 mJy beam$^{-1}$"]
- result: Disk contribution fraction = 35-90% except MC27 ± not stated percent [3.2 Protostellar Cores: "most of the flux is dominated by $F_{\rm disk}$ with a range of 35–90% except for MC27"]
- result: Detection limit of central density = ~4e5 ± not stated cm-3 [4.1: "gives us a detection limit of the central density, $\sim$4 $\times$ 10$^{5}$ cm$^{-3}$"]
- result: Missing flux relative to single dish = >80% ± not stated percent [3.1 Prestellar Cores: "there is a large amount of missing flux, more than 80%"]
- limitation (authors): Continuum-only substructure cannot be distinguished from artifacts at low contrast [4.1: "Therefore, we cannot merely claim that the observed substructure is a substantial piece of evidence of fragmentation of prestellar cores."]
- limitation (authors): Mass uncertainty dominated by assumed dust opacity [3.1 Prestellar Cores: "The uncertainty of the mass estimation mainly arises from the assumption of $\kappa_{\rm 1.3\,mm}$"]
- not stated (card): Rest frequencies and line windows per target; Phase calibrator selection per execution block and QA/flagging details; How the 7 m ms was calibrated (pipeline vs manual, pipeline version); Mask definitions per target and exact rms measurement regions; How Table 3 category I/II/III counts for unobserved cores were assigned; Simulation integration time and noise treatment

### 2020MNRAS.493.4294B: ALMA uncovers the [C II] emission and warm dust continuum in a z = 8.31 Lyman break galaxy (2020; high_z_galaxies; observational_alma_primary)
- question: Is [C II] detected in the z=8.31 LBG MACS0416_Y1, and what does the 1.5 mm continuum non-detection imply for its dust temperature and emissivity index?
- processing.imaging.weighting_robust: natural weighting [2.2 ALMA observations: "We used the natural weighting on the `tclean` task to maximize the point-source flux significance."]
- processing.imaging.uv_taper: Gaussian 0.27" FWHM (convolution of natural maps), chosen by maximizing S/N over 0.01-0.50" [3.1 Detection: "We find this FWHM size by maximizing the signal-to-noise of the [C ii] emission for all tapering sizes between 0.01$''$ and 0.50$''$"]
- step 1: Image cube and continuum
  - method: tclean with natural weighting, all configurations combined; cube at 35 km/s; continuum excludes [C II] channels [2.2 ALMA observations: "A CASA task `tclean` was used to combine all visibilities into an image, both for the continuum and the [C ii] emission"]
  - software: CASA
  - parameter: moment 0 integrated over -140 to +140 km/s [2.2 ALMA observations: "We integrate the data cube between $-140$ and +140 km/s around the [C ii] frequency to generate the [C ii]-integrated map"]
  - validation: velocity range gives highest S/N and agrees with by-eye inspection [2.2 ALMA observations: "This $-140$ and $+$140 km/s velocity range was chosen because it resulted in the highest signal-to-noise ratio for the [C ii] emission"]
- step 6: Dynamical mass from kinematics
  - method: Virial M_dyn = C r_1/2 sigma^2 / G with C = 3.4; velocity field via immoments [4.2.2: "we take $C$ to be 3.4 from (cite: Erb2006)"]
  - software: CASA immoments
  - parameter: r_1/2 = deconvolved major axis, 1.15 ± 0.35 kpc [4.2.2: "we take the deconvolved major axis as the half-light radius, equalling 1.15 $\pm$ 0.35 kpc"]
  - assumption: rotation-dominated system [Discussion, Velocity profile: "Given that MACS0416_Y1 is rotationally-dominated, we take $C$ to be 3.4 from (cite: Erb2006)"]
  - validation: uncertainty in C not included, could vary by factor of two [4.2.2: "although we note that the uncertainty in $C$ is not accounted for, and could vary by a factor of two"]
- result: 1.5 mm continuum upper limit = <18 ± 3 sigma uJy [3.2: "We find a 3$\sigma$ upper limit of 18 $\mu$Jy at 1.5 mm"]
- result: Dynamical mass = 1.2e10 ± 0.4e10 Msun [4.2.2: "We find a dynamical mass of (1.2 $\pm$ 0.4) $\times$ 10$^{10}$ M$_{\odot}$"]
- limitation (authors): Uncertainty in C not included in M_dyn; CMB attenuation of [C II] not corrected; resolution does not resolve outflow regions [4.2.2: "Our current beam-width does not allow us to resolve the individual outflowing regions"]
- not stated (card): Imaging cell size, image size, masking and clean threshold; Which spectral windows/channels define the continuum and exact aggregate continuum bandwidth; Aperture/method for 2D Gaussian fit and tapered spectrum extraction; Exact measurement of 1.5 mm limit (reference frequency, position used); Flux calibrator and flux scale uncertainty; Whether archive products or re-calibrated data were used; De…

### 2024ApJ...963..164R: The Disk Orientations of Perseus Protostellar Multiples at ∼8 au Resolution (2024; star_formation; observational_alma_primary)
- question: Are circumstellar disks in Perseus protostellar multiples preferentially aligned or randomly oriented, as a test of disk vs turbulent fragmentation
- processing.imaging.weighting_robust: Briggs robust 1.0 (Band 6); superuniform (Band 3) [2.2 Band 3 (3 mm) Observations: "restoring the images with super-uniform weighting scheme to closely match the beamsize of the 1.3 mm observations"]
- processing.imaging.deconvolver: MTMFS, 2 Taylor terms [2.1 Band 6 (1.3 mm) Observations: "we used the Multi-(Taylor-)term Multi-Frequency Synthesis (MTMFS) with scale sizes of 0, 5, and 20 pixels and 2 Taylor terms"]
- processing.imaging.multiscale_scales: 0, 5, 20 pixels [2.1 Band 6 (1.3 mm) Observations: "scale sizes of 0, 5, and 20 pixels"]
- step 2: Image continuum
  - method: tclean MTMFS with auto-multithresh, Briggs robust 1 [2.1 Band 6 (1.3 mm) Observations: "The final images were checked by simultaneously cleaning the data with a conservative user-defined mask."]
  - software: CASA tclean
  - parameter: scales 0,5,20 pix; 4 mas pixels; sidelobethreshold 2.0 [2.1 Band 6 (1.3 mm) Observations: "scale sizes of 0, 5, and 20 pixels and 2 Taylor terms"]
  - validation: Cleaned with conservative user mask as check [2.1 Band 6 (1.3 mm) Observations: "The final images were checked by simultaneously cleaning the data with a conservative user-defined mask."]
- step 4: Build model populations
  - method: 10,000 model systems per aligned/random fraction; aligned drawn with 30 deg FWHM normal, random from uniform in cos i; same projection bias applied [4.3 Models of Companion Orientations: "Randomly aligned systems are constructed by drawing the position angle and inclination from a uniform distribution of inverse cosine from 0 to 1."]
  - assumption: Stellar and disk angular momentum axes aligned; no separation-dependent weighting [4.3 Models of Companion Orientations: "under the assumption the stellar angular momentum axis and disk angular momentum axis are aligned"]
  - validation: Results insensitive to ±5 deg change of 30 deg [4.3 Models of Companion Orientations: "the results presented are not significantly changed if moderate deviations ($\pm$5$^{\circ}$) from 30$^{\circ}$is chosen"]
- limitation (authors): Low number of pairs prevents determining exact aligned fraction [5.1 Formation Pathways: "With the relatively low number of statistics (at most 21 pairs of sources), we were not able to determine the exact underlying fractional alignment ratio"]
- limitation (authors): Continuum only: cannot distinguish aligned from anti-aligned disks [4.2 Geometric Orientations: "we were unable to differentiate between aligned and anti-aligned disks"]
- not stated (card): Number of walkers, live points, priors and convergence criteria for uv Gaussian fits (emcee/dynesty/pdspy); uv-fit prior ranges for sizes, flux and angles; Line-free channels / continuum channel selection for Band 6; Self-cal reference model and exact solint per source; Which flux calibrator per EB and flux-scale handling; Random seeds and exact sampling of sources chosen for pairs; Exact Gaussia…

### 2025ApJ...993...85Y: Peculiar Disk Substructures Associated with the Young Eruptive Star EX Lupi (2025; protoplanetary_disks, star_formation; observational_alma_primary)
- question: Does the disk of the EXor EX Lupi host resolved substructures, and how do they relate to the disk surface/thermal structure and to episodic accretion?
- processing.imaging.weighting_robust: Briggs robust = 0.5 [2.2 Self-calibration and CLEAN Imaging: "we employed a Briggs robustness parameter of 0.5 for the imaging"]
- processing.imaging.deconvolver: multi-frequency synthesis with multi-scale, scales [0,1,3] x theta_cl [2.2 Self-calibration and CLEAN Imaging: "with scale parameters of $[0, 1, 3] \times \theta_{\rm cl}$ (where $\theta_{\rm cl}$ is the CLEAN beam size)"]
- step 1: Calibrate, align and self-calibrate
  - method: CASA pipeline calibration, phase-center shifting with fixvis/fixplanets, phase-only self-cal with CLEAN model [2.2 Self-calibration and CLEAN Imaging: "we apply a phase-only self-calibration ($\tt calmode = p$) with a CLEAN model as a reference calibrator for each dataset."]
  - software: CASA
  - parameter: solint=inf, robust 0.5 [2.2 Self-calibration and CLEAN Imaging: "CASA task $\tt gaincal$ to average whole scans ($\tt solint = inf$)"]
  - validation: SNR improvement of 1.2 over non-self-calibrated image [2.2 Self-calibration and CLEAN Imaging: "which reached slight improvements of 1.2 in SNR compared with a non-self-calibrated CLEAN image"]
- step 3: Fit outer ring geometry and width
  - method: ellipse fit for PA/inclination; Gaussian fit to deprojected radial profile with emcee; deconvolve beam [3.1.1 Detailed Geometry: "we employed a Markov Chain Monte Carlo (MCMC) fitting procedure using the `emcee` sampler"]
  - software: emcee
  - parameter: 100 walkers, 500 steps, 250 burn-in [3.1.1 Detailed Geometry: "ran 100 walkers for 500 steps, discarding the initial 250 steps as burn-in"]
  - assumption: deprojected outer ring is circular; Gaussian ring and beam [3.1.1 Detailed Geometry: "Assuming that the deprojected outer ring is circular"]
  - fitting: emcee, uniform priors, median and 16/84 percentiles [3.1.1 Detailed Geometry: "We adopted uniform (flat) priors"]
  - validation: inclination compared with CO kinematic value of Hales et al. [3.1.1 Detailed Geometry: "in reasonable agreement with the $38^{\circ} \pm 4^{\circ}$ derived from a Keplerian model rotation"]
- step 6: Temperature profile, scale height, trapping ratio
  - method: passively irradiated flared disk energy balance gives T_d(r); h_p=c_s/Omega; ratio of deconvolved width to h_p [5.1 Thermal Structure of the Disk: "The temperature at each radius $r$ is determined by balancing the stellar irradiation"]
  - assumption: mu=2.3, M*=0.5 Msun, L*=0.43 Lsun, stellar heating dominant [3.1.2 Dust Trapping: "The mean molecular weight is assumed to be $\mu = 2.3$ in atomic units"]
  - validation: disk-averaged T compared with T Tauri scaling (~20 K) [5.1 Thermal Structure of the Disk: "consistent with the disk$-$averaged temperature ($\langle T_{\mathrm{d}} \rangle \approx 20$ K)"]
- result: Outer ring inclination = 42.6 ± 2.4 deg [3.1.1 Detailed Geometry: "an inclination of $42^{\circ}.6 \pm 2^{\circ}.4$"]
- result: Outer ring position angle = 51.7 ± 2.2 deg [3.1.1 Detailed Geometry: "yielding a PA of $51^{\circ}.7 \pm 2^{\circ}.2$"]
- result: Ring radius = 28.59 ± 0.04 au [3.1.1 Detailed Geometry: "$r_{\rm ring} = 28.59\pm 0.04 ~\rm au$"]
- result: Deconvolved ring width = 1.62 ± 0.04 au [3.1.1 Detailed Geometry: "deconvolved ring width of $\hat{w}_{d} = 1.62\pm 0.04$ au"]
- result: Ring width / pressure scale height = 0.95 ± 0.04 dimensionless [3.1.2 Dust Trapping: "$\hat{w}_{\rm d}/h_{\rm p}(r_{\rm ring}) = 0.95 \pm 0.04$"]
- result: Disk-averaged temperature = 18 ± 1 K [5.1 Thermal Structure of the Disk: "The resulting average disk temperatures yields $18\pm1$ K"]
- result: Ring-star center offset = ~5 ± not stated au [3.1.1 Detailed Geometry: "The center of the ellipse has an offset of $\sim 5$ au"]
- limitation (authors): Ring clumps only 3-5 sigma; higher SNR needed to confirm the SW clump [3 Peculiar Disk Structures: "observations with higher SNR are required to confirm or reject the presence of this clump"]
- limitation (authors): Low spectral index evidence tentative [6.1 Origin of the Inner Arc: "though the evidence remains tentative"]
- not stated (card): PRIISM pixel size, image size and PRIISM version; Exact CLEAN cell size, image size, masks, threshold and iterations; Self-calibration spectral/time details and number of rounds; Flux calibration scale uncertainty; Whether the SPHERE image reduction products are public/how to obtain them; Radial bin width and aperture settings for curve of growth; Exact pixel region and weighting for the inner-ar…

### 2020ApJ...895...84Y: Super-resolution Imaging of the Protoplanetary Disk HD 142527 Using Sparse Modeling (2020; protoplanetary_disks, instrumentation; archival_reuse)
- question: Can sparse modeling (l1+TSV) imaging applied to ALMA data reproduce super-resolution structure (finer than the beam) of the HD 142527 disk with higher fidelity than MS-CLEAN?
- processing.imaging.weighting_robust: Briggs robust = 0.5 [2.2 Data Reduction and Imaging with MS-…: "by adopting Briggs weighting of robust parameter 0.5"]
- processing.imaging.multiscale_scales: [0, 0.3, 0.9] asec [2.2 Data Reduction and Imaging with MS-…: "MS-CLEAN performed with scale parameters of \[0, 0.3, 0.9\] asec"]
- step 1: Calibrate and self-calibrate visibilities
  - method: ALMA pipeline then iterative phase-only self-calibration using MS-CLEAN models [2.2 Data Reduction and Imaging with MS-…: "we performed iterative self-calibration of the visibility phase (calmode = p)."]
  - software: CASA
  - validation: Total fluxes from visibility amplitude 3.3 Jy vs 3.2 Jy [2.2 Data Reduction and Imaging with MS-…: "The resultant total fluxes of Data 1 and 2 are derived to be 3.3 Jy and 3.2 Jy, respectively"]
- step 2: MS-CLEAN imaging
  - method: MS-CLEAN with Briggs robust 0.5 and scales [0,0.3,0.9] asec [2.2 Data Reduction and Imaging with MS-…: "The corrected data were imaged using MS-CLEAN performed with scale parameters of \[0, 0.3, 0.9\] asec"]
  - software: CASA
- step 4: Fidelity versus resolution (NRMSE)
  - method: Convolve images with beams of fraction R of Data 1 nominal beam; compute NRMSE in image and gradient (Prewitt) domains against Data 2 MS-CLEAN reference; optimal resolution is minimum, worse of two domains [3.2 Fidelity at Multi-resolution: "The beam size providing the minimum NRMSE may be considered as an optimal resolution"]
  - assumption: Data 2 MS-CLEAN at nominal resolution is trusted reference [3.2 Fidelity at Multi-resolution: "The Data 2 MS-CLEAN at its nominal resolution is therefore the best choice as the reference image."]
  - validation: Ideal NRMSE curve from convolved reference image [3.2 Fidelity at Multi-resolution: "The solid green line shows the ideal NRMSE curves between the non-convolved and the convolved reference images"]
- result: Optimal resolution Data 1 SpM, image domain = 23 x 16 (41%) ± not stated mas [Table 1: "23 $\times$ 16 (41 $\%$)"]
- result: Optimal resolution Data 1 MS-CLEAN, gradient domain = 34 x 24 (60%) ± not stated mas [Table 1: "34 $\times$ 24 (60 $\%$)"]
- result: Total flux Data 1 / Data 2 = 3.3 / 3.2 ± not stated Jy [2.2 Data Reduction and Imaging with MS-…: "The resultant total fluxes of Data 1 and 2 are derived to be 3.3 Jy and 3.2 Jy, respectively"]
- result: Data 1 SpM NRMSE plateau at R<=41% = 5-10% image domain, 10-15% gradient domain ± not stated percent [3.2 Fidelity at Multi-resolution: "with typical ranges of $5-10~\%$ in the image domain and $10-15~\%$ in the gradient domain"]
- limitation (authors): SpM images have larger asymmetric residuals due to self-calibration with MS-CLEAN; degree of super-resolution for Data 2 not established [5 Conclusion: "SpM images have more asymmetric and larger residuals, while MS-CLEAN images have nearly symmetric residuals distributions."]
- not stated (card): SpM code/implementation used (not named or released); Selected optimal (Lambda_l, Lambda_t) per spectral window; Clean masks, thresholds, iteration counts, cell/image size for MS-CLEAN; Number of self-cal iterations and exact steps; Calibrator for Data 1 flux scale; Frequency ordering/weighting when averaging four SPW images; Reference position of the star for radial profiles

### 2014ApJ...797...27F: Revealing H<SUB>2</SUB>D<SUP>+</SUP> Depletion and Compact Structure in Starless and Protostellar Cores with ALMA (2014; star_formation, astrochemistry; observational_alma_primary)
- question: What small-scale structure and H2D+ distribution exist in the Oph A SM1 and SM1N cores, and are they starless or protostellar?
- processing.imaging.weighting_robust: SM1 uniform; SM1N natural [2.1 ALMA: "The final image was created with uniform weighting of the $uv$-data to decrease side lobes and optimize angular resolution"]
- processing.imaging.deconvolver: SM1: multi-frequency synthesis; SM1N: multi-scale multi-frequency synthesis [2.1 ALMA: "using multi-scale, multi-frequency synthesis deconvolution to recover better the observed larger-scale structure of the source"]
- processing.imaging.uv_taper: H2D+ tapered to 1.3 arcsec [2.1 ALMA: "the H$_2$D$^+$ data were tapered in the $uv$-plane to a final angular resolution of 1$''$.3"]
- step 1: Image continuum
  - method: MFS imaging of all four spws; uniform weighting for SM1 after self-cal, natural multiscale for SM1N [2.1 ALMA: "To image the SM1 condensation, we performed a multi-frequency synthesis deconvolution over all spectral windows and self-calibrated on the initial source model."]
  - software: CASA
- limitation (authors): Masses uncertain to factors of a few [3.2: "While the uncertainty in the derived masses is thus uncertain to factors of a few"]
- not stated (card): Self-calibration solint and number of iterations for SM1; Cell size, image size, clean masks and thresholds; Multiscale scales for SM1N; Taper parameters for the H2D+ cube; Line-free channels used for continuum subtraction; uvmodelfit starting parameters; Phase centre / reference positions used for uv-averaging bins; ATCA NH3 data and SMA data are unpublished (in preparation)

### 2024ApJ...972..111L: Ongoing and Fossil Large-scale Outflows Detected in a High-redshift Radio Galaxy: [C II] Observations of TN J0924-2201 at z = 5.174 (2024; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the kinematics of the [C II] gas in the z=5.17 radio galaxy TN J0924-2201, and are the three CO(1-0) companions outflows from the host or unrelated dwarf galaxies?
- processing.imaging.weighting_robust: continuum robust=0.5; cube robust=2.0 [2 ALMA Observations: "we applied `tclean` with deconvolver `hogbom` and Briggs weighting `robust=2.0`."]
- processing.imaging.deconvolver: continuum: mtmfs; cube: hogbom [2 ALMA Observations: "we applied `tclean` with deconvolver `hogbom` and Briggs weighting `robust=2.0`."]
- step 1: Continuum imaging and flux measurement
  - method: tclean mtmfs on line-free channels; peak and integrated flux [2 ALMA Observations: "We applied `tclean` with deconvolver `mtmfs` and Briggs weighting `robust=0.5`."]
  - software: CASA
  - parameter: robust=0.5, cell 0.1" [2 ALMA Observations: "The pixel scale is set to $0''.1$."]
- step 3: Build [C II] cube and fit line
  - method: uvcontsub, tclean hogbom; spectra; single and double 1-D Gaussian fits [3.2 [C II] line emission: "We applied double-component 1-D Gaussian fit on the spectrum and found a redshifted substructure"]
  - software: CASA
  - parameter: ~0.8" aperture and peak pixel 0.1" [3.2 [C II] line emission: "The upper left panel shows the spectrum extracted with aperture $\sim0''.8$, which covers the whole galaxy"]
  - fitting: Gaussian fit [3.2 [C II] line emission: "We applied double-component 1-D Gaussian fit on the spectrum and found a redshifted substructure, which is shown in red dashed line, with a velocity offset of $702\pm17\,\rm km\,s^{-1}$, relative to the main component."]
  - validation: Checked cube without uvcontsub; substructure persists [3.2 [C II] line emission: "It is clear that the redshifted substructure does still appear."]
- result: Continuum integrated flux of TN J0924-2201 = 829 ± 57 uJy [3.1 1-mm continuum emission: "The peak flux of TN J0924$-$2201 is $392\pm19\,\mu$Jy and the integrated flux is $829\pm57\,\mu$Jy."]
- result: [C II] systemic redshift = 5.1736 ± 0.0002 dimensionless [abstract: "$z_{\rm [C\,{\sc II}]}=5.1736\pm0.0002$"]
- result: Ly-alpha velocity offset from [C II] = 1035 ± 10 km/s [abstract: "redshifted by a velocity of $1035\pm10$ km s$^{-1}$"]
- result: Redshifted [C II] component velocity = 702 ± 17 km/s [Table 1: "Mean (km$\,$s$^{-1}$) | $\pm6$$\ensuremath{^{a}}$ | $702\pm17$"]
- result: C IV velocity offset = 500 ± 10 km/s [abstract: "C iv line with a velocity of $500\pm10$ km s$^{-1}$"]
- result: Main component velocity dispersion = 270 ± 6 km/s [Table 1: "Velocity dispersion (km$\,$s$^{-1}$) | $270\pm6$ | $47\pm16$"]
- result: Continuum 3-sigma upper limit at companions = 57 ± not stated uJy/beam [3.1 1-mm continuum emission: "The $3\sigma$ upper limit of non-detection is $57\,\mu$Jy with beam $\sim0''.4$."]
- limitation (authors): Only projected distances and radial velocities known; spatial offset of redshifted [C II] smaller than beam [4.2 Outflowing molecular clouds: "Although we only have the information of the projected distances and the radial velocities instead of the actual distances and velocities"]
- not stated (card): Continuum-fit channel selection for uvcontsub exactly; Clean mask, threshold and iteration settings; Image size and spectral-line fitting method details; Aperture centre for the ~0.8" spectrum and how the deconvolved sizes were measured; Spectral cube channel start/frequency and rest frequency used; Gray-body fitting method, priors/fitter and photometry used; Inputs to PDR model and L_IR scaling;…

### 2019A&A...630A..59B: Widespread QSO-driven outflows in the early Universe (2019; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Do high-z QSOs show faint broad [CII] wings tracing cold outflows, detectable by stacking archival ALMA [CII] data?
- processing.imaging.weighting_robust: natural weighting [Sample and data reduction: "We chose a natural weighting to maximise the sensitivity of the individual observations"]
- processing.imaging.deconvolver: Hogbom [Sample and data reduction: "Hogbom algorithm with no cleaning mask and a number of iterations $N_{\rm iter}=500-1000$"]
- processing.imaging.uv_taper: tapering to 1.2 arcsec for common-resolution stack test; sources <0.6'' not used [4.4 Stacked Cube: "We produced ALMA cubes at the worse angular resolution in our sample by tapering the visibilities to 1.2 arcsec."]
- step 1: Image archival data and subtract continuum
  - method: CASA clean cubes (Hogbom, natural, 0.05'' pixels, 30 km/s channels); zeroth-order uv-plane continuum fit to |v|>1500 km/s channels [Sample and data reduction: "We chose a natural weighting to maximise the sensitivity of the individual observations, a common pixel size of 0.05$''$ and a common spectral bin of 30 km s$^{-1}$."]
  - software: CASA
  - parameter: Niter 500-1000, threshold 3 sigma [Sample and data reduction: "a number of iterations $N_{\rm iter}=500-1000$ according to the significance of the detection"]
  - validation: First-order polynomial continuum did not significantly affect results [Sample and data reduction: "We verified that modelling the continuum emission with a first order polynomial did not significantly affect our results"]
- step 5: Size of outflow from stacked cube
  - method: Beam-deconvolved half-light radius of |v|>400 km/s map [4.4 Stacked Cube: "We derived a beam-deconvolved half light radius $R_{\rm out} = \sqrt{(R_{\rm 50\%}^2 - R_{\rm beam}^2})\sim 0.60$ arcsec"]
  - validation: Repeated with cubes tapered to 1.2 arcsec [4.4 Stacked Cube: "we derived a beam-corrected half light radius $R_{\rm out}^{\rm taper} \sim 4.6$ kpc"]
- result: Outflow radius R_out = ~3.5 ± not stated kpc [4.4 Stacked Cube: "$R_{\rm out}$ corresponds to $\sim3.5$ kpc at $\langle z_{\rm stack}\rangle$."]
- limitation (authors): Interferometric data may miss extended diffuse emission; stacking dilutes orientations [Conclusions: "we cannot exclude that additional, more extended emission is present but missed by the interferometric data used for the stacking."]
- not stated (card): List of the 48 QSOs with per-source flux scaling/calibration corrections (table not in text); Exact clean threshold and iteration count per source; Which sources were calibrated manually vs pipeline; Exact aperture definition/centering and handling of channels with partial coverage; Initial guesses for the Gaussian fits; How the 100 empty positions were chosen; Fruchter&Hook-based cube regridding…

### 2018A&A...614A..58B: High-resolution observations of IRAS 08544-4431. Detection of a disk orbiting a post-AGB star and of a slow disk wind (2018; evolved_stars, stellar_physics; observational_alma_primary)
- question: Does the post-AGB binary IRAS 08544-4431 host a rotating Keplerian disk plus a slow outflow, and what are their structure, mass, dynamics and angular momentum?
- processing.imaging.weighting_robust: Natural (adopted) and robust (value not given) [Observations: "Image deconvolution was carried out with natural and also robust weighting"]
- processing.imaging.deconvolver: Hogbom and SDI tried; SDI used for final data [Observations: "The data here presented were obtained with natural weighting and SDI method."]
- step 1: Calibrate and image data
  - method: CASA calibration, GILDAS phase self-cal, SDI CLEAN with natural weighting, continuum subtraction [Observations: "The data here presented were obtained with natural weighting and SDI method."]
  - software: CASA, GILDAS
  - parameter: Channels degraded to 0.43 km/s [Observations: "the resolution was degraded to about 0.43 km s$^{-1}$ to improve the S/N at high velocities."]
  - validation: Flux compared with APEX profiles; <20% flux lost [Observations: "a small fraction of the flux, $<$ 20%, was filtered out in the maps of $^{12}$CO $J$=3$-$2."]
- step 2: Model nebula with LTE radiative transfer
  - method: Axisymmetric disk (inner Keplerian, outer sub-Keplerian + expansion) plus outflow; LTE radiative transfer on ~10^6 cells and 10^4-10^5 rays, convolved with clean beam, compared with maps and PV diagrams [3 Modeling of our ALMA maps: "Typically, we solve the transfer equations following 10$^4$ to 10$^5$ rays, which traverse the cells in which the nebula has been divided."]
  - parameter: Inclination 70 deg to plane of sky axis, PA -15 deg, X(13CO)=1.5e-5, X(12CO)=1.5e-4 [Table 1: "| Axis inclination with respect to the plane of the sky | | 70$^\circ$ | from IR and CO data |"]
  - assumption: LTE level populations, constant abundances, axial symmetry, D = 1100 pc [3 Modeling of our ALMA maps: "We assume local-thermal-equilibrium (LTE) populations for the involved rotational levels."]
  - fitting: Manual exploration of many configurations; best-fit model chosen by comparison with data and previous results, no formal sampler [3 Modeling of our ALMA maps: "In any case, a high number of different configurations were analyzed."]
  - validation: Comparison of predicted channel maps and PV diagrams with data; similarity to Red Rectangle, IW Car [3.1 Description of the best-fit model: "comparing the predictions with the observational data and other previous results; see predicted maps per velocity channel and position-velocity diagram in Figs. 3 and 5."]
- result: Total central mass (D=1100 pc) = 1.8 ± ~40% Msun [abstract: "The disk rotation indicates a total central mass of about 1.8 $M_{\mbox{\ensuremath{\odot}}}$, for a distance of 1100 pc."]
- result: Continuum flux = ~320 ± 1 mJy [Observations: "yielded a total flux of $\sim$ 320 $\pm$ 1 mJy"]
- limitation (authors): Inner disk and width poorly constrained; mass depends on CO abundance and distance; LTE assumption; temperature uncertain [3.2 Uncertainties: "Some disk properties are not well determined from the observations, mainly because of the relatively low angular resolution"]
- not stated (card): Robust weighting parameter value; SDI clean parameters, masks, and number of iterations; CASA version and calibration script; Spectral window rest frequencies; Fitting procedure and merit function for model comparison (apparently by eye); Code for the radiative transfer model not released; Which calibrator served which role; Self-calibration solution intervals

### 2015Natur.522..455C: Galaxies at redshifts 5 to 6 with systematically low dust content and high [C II] emission (2015; high_z_galaxies; observational_alma_primary)
- question: Do typical z~5-6 star-forming galaxies show lower dust content and enhanced [CII] relative to FIR compared with z<3 systems?
- processing.imaging.weighting_robust: Briggs, Robust = 1 [Method 2: "The data were re-imaged using the CASA Briggs flexible weighting of the u-v visibility data with Robust = 1"]
- step 1: Re-reduce and image ALMA data
  - method: Additional flagging, re-imaging with Briggs weighting to make continuum, moment zero and channel maps [Method 2: "The calibrated visibility data was then re-analyzed, performing additional flagging of bad time periods in the data and bad channels."]
  - software: CASA
  - parameter: Robust = 1 [Method 2: "with Robust = 1 to create continuum, moment zero, and channel maps"]
  - validation: Independent blind check of data reduction by a coauthor [Author Contributions: "carried out an independent blind check of the ALMA data reduction"]
- step 5: Compare to IRX-beta relations and test robustness; stack non-detections
  - method: Compare IRX vs beta with Meurer and SMC relations; predicted vs measured mean flux of undetected sources [Method 5: "If we assume a Meurer et al. like IRX-β relation and the mean of our grey body models"]
  - assumption: Meurer relation typical of z<3; SMC-like dust model [Figure 2: "The Meurer [28] relation, consistent with typical galaxies at z<3, is shown as a black solid line"]
  - validation: Extreme dust-temperature models tested; completeness analysis [Method 5: "find the low dust emission is unlikely due to selection effects in our UV sample"]
- result: Stacked mean continuum of 6 non-detections = 35 ± 13 uJy [main text: "yields a continuum detection of 35±13μJy"]
- result: Effect on z~6 star formation density = 30-40% less ± not stated percent [Method 8: "result in ~30-40% less StarFormation at z~6 than previously thought"]
- limitation (authors): Dynamical masses very uncertain due to low spatial resolution [Method 4: "This method yields an approximate answer but is very uncertain"]
- not stated (card): Line-free channels and continuum imaging bandwidth used; Image size, cell size, cleaning threshold, masks; Flagging details and which channels/times were flagged; Flux calibrator and ALMA flux scale uncertainty; Channel width of cubes and moment-0 velocity range; Fit box sizes for CASA Gaussian fits; CASA version; Stacking procedure details; Details of the SED fitting (templates, extinction laws)

### 2012ApJ...757..129R: Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk (2012; protoplanetary_disks; archival_reuse)
- question: What do the spatially and spectrally resolved 12CO J=2-1 and J=3-2 line wings from the TW Hya disk reveal about the temperature and kinematic structure of the inner disk?
- processing.imaging.weighting_robust: natural weighting [2 Data and Calibration: "Fourier inverted (assuming natural weighting) with modest spectral averaging"]
- processing.imaging.deconvolver: CLEAN [2 Data and Calibration: "deconvolved with the `CLEAN` algorithm using a simple polygon mask applied to all channels"]
- step 1: Calibrate and image CO cubes
  - method: Calibrate SV data in CASA, continuum-subtract, invert with natural weighting, CLEAN with polygon mask; native and binned channels [2 Data and Calibration: "We utilized two different channel spacings: (1) “native", meaning 0.20 and 0.12 km s$^{-1}$ for $J$=2$-$1 and $J$=3$-$2"]
  - software: CASA
  - parameter: systemic LSR velocity +2.87 km/s forced onto a channel center [2 Data and Calibration: "we elected to force the reduced spectral datasets to have a channel precisely centered on the known systemic LSR velocity of TW Hya, $+$2.87 km s$^{-1}$."]
  - validation: Tested atmospheric CO, flat Tsys re-calibration, and continuum subtraction variations; wings persist [2 Data and Calibration: "we re-calibrated the data instead with a spectrally flat, band-averaged $T_{\rm sys}$ correction. This had no discernable effect on the results"]
- result: Projected line-wing velocity extent = 2.1 ± not stated km/s [2 Data and Calibration: "significant ($>$5 $\sigma$) emission in the wings of both CO transitions out to projected velocities at least $\pm$2.1 km s$^{-1}$"]
- result: CO 2-1 integrated flux (5"x5" box, 0.20 km/s) = 17.5 ± 1.8 Jy km/s [Table 1: "$7.8\pm0.8$ | $17.5\pm1.8$"]
- result: CO 3-2 integrated flux (0.12 km/s) = 37.2 ± 3.7 Jy km/s [Table 1: "$9.7\pm1.0$ | $37.2\pm3.7$"]
- limitation (authors): Model parameters are not unique nor optimized; limited resolution [3.3.3 A Disk Warp: "the warp model parameters we determine or even the formulation we adopt are not unique, nor optimized"]
- not stated (card): CLEAN threshold, polygon mask geometry, cell and image size; Exact line-free channels and polynomial order for continuum subtraction; LIME settings (number of grid points, photons) and CO abundance X_co value; Gas-to-dust ratio and dust properties details for RADMC-3D model; Exact MPFIT setup, initial values and how manual adjustments were made; Distance to TW Hya adopted

### 2020MNRAS.496.4061D: Revealing the intermediate-mass black hole at the heart of the dwarf galaxy NGC 404 with sub-parsec resolution ALMA observations (2020; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: What is the mass of the intermediate-mass black hole in NGC 404 once the molecular gas contribution to the potential is included, using sub-parsec ALMA CO(2-1) kinematics plus stellar kinematics?
- processing.imaging.weighting_robust: Briggs robust 0.5 (three long-baseline tracks); robust 0.1 (all tracks) [2 ALMA data: "imaged using Briggs weighting (robust parameter 0.5)"] [2 ALMA data: "imaged using Briggs weighting (robust parameter 0.1)"]
- processing.imaging.deconvolver: multi-scale clean, scales for point sources and 3, 6, 9 times the beam; threshold 2x dirty-channel RMS [2 ALMA data: "cleaning scales optimised for point sources, and emission with a characteristic scale 3, 6 and 9 times the synthesised beam"] [2 ALMA data: "to a threshold equal to twice the root-mean square (RMS) noise of the dirty channels"]
- processing.imaging.uv_taper: continuum tapered, beam 0.67"x0.46" [2.2 Continuum emission: "additionally tapered the data in the $uv$-plane (yielding a synthesised beam of 0$.\!\!^{\prime\prime}$67 $\times$ 0$.\!\!^{\prime\prime}$46"]
- step 1: Calibrate, combine and image CO(2-1) and continuum
  - method: Manual CASA calibration, uvcontsub, multiscale clean of combined tracks, primary-beam correction; two cubes (robust 0.5 long baselines; robust 0.1 all tracks) [2 ALMA data: "In this work we make use of two different sets of CO(2-1) data products."]
  - software: CASA
  - parameter: robust 0.5 / 0.1; 2 km/s channels; 0.015" pixels; clean threshold 2x RMS [2 ALMA data: "Both datasets use a channel width of 2 km s$^{-1}$ and pixels of 0$.\!\!^{\prime\prime}$015$\times$0$.\!\!^{\prime\prime}$015."]
  - validation: Compared combined-cube flux with ACA total flux (174±17 vs 161±16 Jy km/s) [2.1 Line emission: "We derive a total CO(2-1) flux of $174\pm17$ Jy km s$^{-1}$ from these data, in agreement with the estimate from our combined dataset."]
- step 4: Build gas distribution and potential for gas kinematic model
  - method: SKYSAMPLER samples clean components with 1e6 point sources; potential via IDL POTENTIAL_NEWTON from symmetrised cloudlets in thin warped disc [4.1 Gas distribution: "that samples the observed clean components with an arbitrary number of point sources ($10^6$ in this case)"]
  - software: SKYSAMPLER, IDL POTENTIAL_NEWTON
  - assumption: thin disc; each cloudlet equal mass fraction [4.2 Mass model: "assuming each cloudlet has an equal fraction of the total gas mass"]
  - validation: MGE-based potential gives same results [4.2 Mass model: "our results would not have changed"]
- result: CO(2-1) integrated flux (inner 8"x8", combined) = 161 ± 16 Jy km/s [2.1 Line emission: "we find an integrated line flux of $161\pm16$ Jy km s$^{-1}$ within the inner 8$^{\prime \prime}$$\,\times$ 8$^{\prime \prime}$"]
- result: CO(2-1) flux from ACA = 174 ± 17 Jy km/s [2.1 Line emission: "We derive a total CO(2-1) flux of $174\pm17$ Jy km s$^{-1}$ from these data"]
- result: Flux resolved out in high-res dataset = 74 ± not stated percent [2.1 Line emission: "The high-resolution dataset resolves out 74% of this emission"]
- result: Gas mass within 0.25" (3.7 pc) = 2.5e5 ± 0.3e5 Msun [4.2 Mass model: "the total molecular gas mass is (2.5$\pm$0.3)$\times$10$^5$ M$_{\odot}$"]
- limitation (authors): Keplerian rise not resolved; result depends on stellar mass model and Gamma [4.5 Uncertainties: "given that we do not resolve the Keplerian increase of the circular velocity around the BH"]
- limitation (authors): Low Gamma should be treated with caution; beam correlations neglected [5.4 Stellar mass normalisation: "We therefore suggest that the low $\Gamma$ value should be treated with caution."]
- not stated (card): Line-free channels used for uvcontsub and continuum imaging; Image size and cube velocity range/imaging details, mask definition, CASA version; Which tracks form the 'three long baseline tracks' and their execution blocks/uv-tapering parameters; Moment mask threshold; Exact MCMC step sizes, convergence criterion and KinMS settings; Exact pixel selection for N=12,112 and radial range of fit; Inter…

### 2018MNRAS.475.4924K: ALMA observations of the narrow HR 4796A debris ring (2018; debris_disks; observational_alma_primary)
- question: What are the radial and vertical structure of the HR 4796A debris ring at 880 um, is CO gas present, and what do these imply for dynamics and an interior planet?
- processing.imaging.weighting_robust: Briggs robust = 0.5 (continuum); natural weighting for CO cube [2 Observations: "then imaged the visibilities with natural weighting to cover the spectral region"]
- step 1: Image continuum and measure flux
  - method: CLEAN imaging, phase self-cal, elliptical mask photometry [2.1 Basic continuum analysis: "Using an elliptical mask with a semi-major axis of 1.75$''$ and semi-minor axis 0.4$''$ (the ratio derived for the dust ring below), we measure a total disk flux of $14.8 \pm 1.5$ mJy"]
  - software: CASA
  - validation: Compared with SCUBA-2 flux; 180-degree rotation subtraction consistent with noise [2.1 Basic continuum analysis: "This agreement suggests that the ALMA observations have not resolved out significant flux on scales larger than seen in Figure"]
- step 3: Fit disk models to visibilities
  - method: radmc-3d optically thin torus models, FT to uv points, chi2 minimisation with MCMC; Gaussian, box, power-law, eccentric variants [3 Continuum image Models: "we use the ensemble Markov-Chain Monte-Carlo (MCMC) method proposed by (cite: gw2010), as implemented by the `emcee` package"]
  - software: radmc-3d, emcee, CASA
  - parameter: 40 walkers, 1000 steps, ~100 burn-in; data averaged to 10 s and four channels per SPW; weights recomputed with statwt; reweighting 1/2.5 [3 Continuum image Models: "For most fitting runs we use 40 walkers and chains with 1000 steps"]
  - assumption: Dust size 10 um to 1 cm, q=11/6; 880 um opacity 0.17 m2/kg [3 Continuum image Models: "such that the 880$\mu$m opacity is 0.17 m$^2$ kg$^{-1}$ (45 au$^2$ $M_\oplus^{-1}$)"]
  - fitting: emcee ensemble sampler; chi2 likelihood; priors not stated [3 Continuum image Models: "The difference between the model and the data is then quantified by computing the $\chi^2$ goodness-of-fit metric over all visibility samples."]
  - validation: Delta chi2 and BIC model comparison; residual images [3.5 Summary of modelling: "$BIC = \chi^2 + N_{\rm param} \ln(N_{\rm vis})$"]
- result: Total disk flux at 880 um = 14.8 ± 1.5 mJy [2.1 Basic continuum analysis: "we measure a total disk flux of $14.8 \pm 1.5$ mJy"]
- result: Gaussian torus FWHM_r = 10 ± 1 au [Table 1: "FWHM$_r$ (au) | 10 | 1"]
- result: Gaussian torus FWHM_h = 7 ± 1 au [Table 1: "FWHM$_h$ (au) | 7 | 1"]
- result: Dust mass = 0.35 ± 0.04 Earth masses [Table 1: "$M_{\rm dust}$ ($M_\oplus$) | 0.35 | 0.04"]
- result: Ring radius r0 (Gaussian) = 78.6 ± 0.2 au [Table 1: "$r_0$ (au) | 78.6 | 0.2"]
- result: Position angle = 26.7 ± 0.1 deg [Table 1: "$\Omega$ ($^\circ$) | 26.7 | 0.1"]
- result: Inclination = 76.6 ± 0.2 deg [Table 1: "$I$ ($^\circ$) | 76.6 | 0.2"]
- result: Power-law index p = 24 ± 2 dimensionless [3.3 Power-law torus: "is $p = 24 \pm 2$, which corresponds to a FWHM of only 5au"]
- limitation (authors): Vertical extent is smaller than the beam, so the vertical resolution conclusion is cautious; tests not exhaustive. [5 Summary and Conclusions: "We remain cautious about the claim of vertically resolved structure because it is smaller than the beam size"]
- limitation (authors): Dust mass has large systematic uncertainty from arbitrary opacity. [3 Continuum image Models: "the mass is given largely for comparative purposes (i.e. it has a considerable systematic uncertainty)"]
- not stated (card): Line-free channels used in uvcontsub; Image size, cell size, and clean threshold/mask; Self-calibration solution interval; Priors and bounds on MCMC parameters; Model grid/radmc-3d settings (photon number, image resolution); Details of CO NLTE code (not public; Matra et al. submitted); Mass-loss rate calculation inputs (stellar luminosity, f) not fully listed

### 2025MNRAS.541.2540Z: WISDOM Project─XXV. Improving the CO-dynamical supermassive black hole mass measurement in the galaxy NGC 1574 using high spatial resolution ALMA observations (2025; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: What is the SMBH mass of NGC 1574 when high-resolution ALMA CO(2-1) data that spatially resolve the sphere of influence are forward-modelled, and how does it compare with the earlier intermediate-resolution measurement?
- processing.imaging.weighting_robust: Briggs robust 1.0 (line); robust 0.5 (continuum) [2.3.1 Imaging: "using Briggs weighting with a robust parameter of $1.0$"] [2.4 Continuum emission: "Briggs weighting with a robust parameter of $0.5$"]
- processing.imaging.deconvolver: Högbom [2.2 Observations and data reduction: "using the `tclean` task with a Högbom deconvolver"]
- step 2: Continuum subtraction and line cube imaging
  - method: uvcontsub then tclean cube, Briggs robust 1.0, 20 km/s channels, clean to 1.5 sigma [2.3.1 Imaging: "We adopted a channel width of $20$ km s$^{-1}$"]
  - software: CASA
  - parameter: pixel 0.02", 200x200 pixels, robust 1.0 [2.2 Observations and data reduction: "we chose a pixel size of $0.02\ensuremath{''}$"]
  - validation: weighting chosen after trials to resolve SoI while retaining S/N [2.3.1 Imaging: "After some trials, we chose this weighting to ensure that the SMBH SoI is sufficiently spatially resolved"]
- step 4: Continuum measurement
  - method: mfs tclean, robust 0.5, imfit 2D Gaussian [2.4 Continuum emission: "We fit a two-dimensional (2D) Gaussian to the source with the CASA task `imfit`"]
  - software: CASA
  - fitting: 2D Gaussian fit [Continuum emission: "We fit a two-dimensional (2D) Gaussian to the source with the CASA task `imfit`, revealing a marginally-resolved source with a deconvolved FWHM size of"]
- result: Continuum flux density at 231 GHz = 2.37 ± ±0.03 ±0.24 (syst) mJy [2.4 Continuum emission: "an integrated flux density of $2.37\pm0.03\pm0.24$ mJy"]
- limitation (authors): Circular-orbit assumption with mild non-circular motions; distance uncertainty (10%) not included in budget [4.1 Main uncertainties: "we choose not to include in the SMBH mass uncertainty budget the $10\%$ uncertainty introduced by the distance"]
- not stated (card): Prior distributions beyond the uniform search ranges, and the Gibbs sampler settings (step sizes, number of chains); Which channels were identified as line-free for uvcontsub; Clean mask definition and niter limits for tclean; Exact tclean parameters beyond weighting and threshold (e.g. gridder, PB limit, number of channels); Pipeline version used by the archive scripts; Whether primary-beam corr…

### 2015ApJ...813..118M: Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations (2015; nearby_galaxies, star_formation; observational_alma_primary)
- question: How do free-free continuum (33 and 94.5 GHz) and dense gas tracers (HCN, HCO+ J=1-0) compare on ~90 pc scales in three regions of NGC 3627, and how do dense gas fraction and star formation efficiency relate?
- processing.imaging.weighting_robust: Briggs robust=0.5 [2.4 Continuum Imaging and Photometry: "We chose to use *Briggs* weighting with robust=0.5, and set the variable nterms=2"]
- processing.imaging.multiscale_scales: scales ≈1 and 3 times synthesized beam FWHM [2.4 Continuum Imaging and Photometry: "searching for structures with scales $\approx$1 and 3 times the FWHM of the synthesized beam"]
- step 1: Image continuum and measure photometry
  - method: clean with MFS, nterms=2, multiscale, Briggs robust 0.5; imfit within 15 arcsec circular aperture [2.4 Continuum Imaging and Photometry: "we used the task imfit in CASA to fit sources within a circular aperture having a radius of 15$''$"]
  - software: CASA
  - parameter: robust=0.5, nterms=2 [2.4 Continuum Imaging and Photometry: "We chose to use *Briggs* weighting with robust=0.5, and set the variable nterms=2"]
  - fitting: imfit single-component Gaussian [2.4 Continuum Imaging and Photometry: "Clearly for the case of Enuc. 2, which is an elongated structure at the end of the bar, a single-component fit is not the most appropriate."]
- step 2: Image lines, extract spectra, fit line widths
  - method: uvcontsub, clean, moment 0 maps; spectra from circular aperture 20% larger than source major axis convolved with beam; Gaussian fits [2.5 Line Imaging and Photometry: "The spectra were extracted using a circular aperture centered on the 94.5 GHz source positions returned by imfit"]
  - software: CASA
  - fitting: Gaussian line profile; Monte Carlo for uncertainties [2.5 Line Imaging and Photometry: "uncertainties that were estimated using the errors per channel along with a Monte Carlo approach"]
- result: continuum-HCN/HCO+ peak offset at Enuc. 2 = ≈3 arcsec (≈130 pc) ± not stated arcsec [3.2 Spatial Offsets: "The continuum and molecular gas are spatially offset in the plane of the sky by $\approx$3$''$ ($\approx$130 pc at the distance of NGC 3627)."]
- result: 33 GHz integrated flux density of nucleus = 2.09 ± 0.08 mJy [Table 2: "$1.70\pm0.06$ | $2.09\pm0.08$"]
- limitation (authors): Only three regions; nuclear HCN cut off by bandpass; single-component fit poor for Enuc. 2 [2.5 Line Imaging and Photometry: "the detection of HCN towards the nucleus is cut off by the bandpass at a radial velocity of $v_\mathrm{LSRK} \approx 800\mathrm{\,km\,s^{-1}}$"]
- not stated (card): Line-free channels for uvcontsub; ALMA array configuration, baselines, and time on source; CASA version; Image size and cell size; Clean masks and thresholds; Velocity ranges for moment 0 integration; SFR calibration formula and how L33 converts to SFR; Monte Carlo details for velocity dispersion errors; Unit conversion from Jy/beam to K km/s for HCO+, HCN, CO

### 2024A&A...682A.166F: A benchmark for extreme conditions of the multiphase interstellar medium in the most luminous hot dust-obscured galaxy at z = 4.6 (2024; agn_and_quasars, high_z_galaxies, milky_way_ism; observational_alma_primary)
- question: What are the multiphase ISM conditions in the hot dust-obscured galaxy W2246-0526, as constrained by eight FIR fine-structure lines compared with CLOUDY models?
- processing.imaging.weighting_robust: Briggs, robust = 2.0 [2 Observations: "Briggs weighting mode set to a robustness = 2.0 (close to natural weighting)"]
- processing.imaging.deconvolver: Hogbom, threshold 2x rms of each cube [2 Observations: "We run the Hogbom cleaning algorithm (cite: 1974A&AS...15..417H) to a flux density threshold of two times the root mean square of each cube"]
- processing.imaging.uv_taper: 0.3'' taper tested in appendix; not adopted [ALMA data reduction: "applying a tapering of the visibilities with a value of $0.3\ensuremath{''}$ no extra emission is recovered"]
- step 1: Calibrate and image line cubes
  - method: ScriptForPI pipeline restore, tclean Hogbom cubes, uvcontsub continuum subtraction [2 Observations: "We processed the data with the `ScriptForPI.py` provided through the ALMA science archive"]
  - software: CASA, tclean, uvcontsub
  - parameter: robust 2.0, 0.05'' pixels, threshold 2 rms, 1.25'' mask [2 Observations: "Briggs weighting mode set to a robustness = 2.0 (close to natural weighting)"]
  - validation: Alternative robust=0.5 and taper tested on [CII] [ALMA data reduction: "extended emission is missed when using a robust parameter of $r=0.5$"]
- limitation (authors): Simple geometry and single homogeneous cloud; continuum and CO SLED not modeled [3.2 ISM models: "we do not attempt to fit the continuum emission"]
- not stated (card): Line-free channel ranges and spectral channel widths for each cube; Continuum uvcontsub fit order; Exact phase centre/aperture centre coordinates; Pipeline versions per cycle; Flux calibration uncertainty; How errors on fluxes were computed; Priors and grid-interpolation details of the Bayesian fit, and which ratios entered the fit; CLOUDY input files/scripts; Source coordinates

### 2018MNRAS.475..448T: Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study (2018; milky_way_ism, star_formation; observational_alma_primary)
- question: Is IRAS 19132+1035 a site of interaction between the GRS 1915+105 jet and the ISM, and what do the molecular lines say about ISM conditions and jet power?
- processing.imaging.weighting_robust: natural weighting [3.1 Spectral line imaging: "All imaging is done with natural weighting to maximize sensitivity, a pixel size of 0.2 arcsec"]
- processing.imaging.deconvolver: multi-scale clean, scales [0,1,5,10,15] x pixel size [3.1 Spectral line imaging: "the multi-scale algorithm (scales of $[0,1,5,10,15]\times$ the pixel size)"]
- step 1: Combine 12 m, 7 m and TP data into line cubes
  - method: Custom CASA procedure: clean 12m+7m, regrid TP, primary-beam weight, feather clean components with TP, final clean with feathered model [3.1 Spectral line imaging: "We use a custom procedure, which combines the 12 m, 7 m, and total power array data, to image all of our spectral lines."]
  - software: CASA
  - parameter: natural weighting, 0.2 arcsec pixel, multiscale [0,1,5,10,15] [3.1 Spectral line imaging: "All imaging is done with natural weighting to maximize sensitivity, a pixel size of 0.2 arcsec"]
  - validation: Tested direct Fourier-plane feather combination; no clear improvement [3.1 Spectral line imaging: "did not find any clear improvements in image quality"]
- limitation (authors): Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density [5.4 Constraints on jet properties: "We have also assumed a constant external density."]
- limitation (authors): ALMA continuum lacks single-dish data so flux is underestimated [4.1 Continuum Emission: "we do not recover all the flux from the region in these ALMA continuum observations"]
- not stated (card): Line-free channels and continuum velocity ranges for each line; Channel width/velocity resolution and cube spectral regridding used in final imaging; Clean thresholds, mask, and number of iterations; Final synthesized beams and rms noise per cube; Gaussian fit and MCMC setup (priors, sampler, walkers) for SED and line fits; Regions A-D coordinates and extraction apertures; Manual calibration deta…

### 2019AJ....158...76C: ALMA Spectral Imaging of Titan Contemporaneous with Cassini's Grand Finale (2019; solar_system, astrochemistry; observational_alma_primary)
- question: What are the spatial distributions, abundances and chemical/dynamical lifetimes of Titan's nitriles and propane around the 2017 solstice, as seen by ALMA alongside Cassini CIRS?
- processing.imaging.weighting_robust: Natural for maps; Briggs robust = 0 for limb profiles [4.4 ALMA Limb Abundance Retrievals: "Briggs weighting of the interferometric data was used (with a $robust$ parameter of zero)"]
- step 1: Calibrate and image data
  - method: JAO pipeline calibration; days combined after regridding and Doppler-shifting to Titan's rest frame; position offset corrected; continuum subtracted; Clark clean [2 ALMA Observations: "The data from May 8 and May 16 were combined after regridding and Doppler-shifting to Titan’s rest frame."]
  - software: CASA
  - parameter: pixel 0.025'', mask 1.3'' [2 ALMA Observations: "with a pixel size of $0.025''$"]
- step 4: Retrieve limb abundance profiles
  - method: Fit S(r) profiles with spherically symmetric model with polygonal abundance x(z), passed through ALMA simulator [4.4 ALMA Limb Abundance Retrievals: "the resulting images were passed through the ALMA simulator (using the `Simobserve` and `Clean` tasks)"]
  - software: MPFIT, CASA simobserve, CASA clean
  - parameter: Wedges phi=45-135 and 225-315 deg [4.4 ALMA Limb Abundance Retrievals: "averaged within angular regions $\phi=45$-135$^{\circ}$ and $\phi=225$-315$^{\circ}$"]
  - assumption: Optically thin emission; density from Krasnopolsky 2009; temperature from CIRS CH4 limb at -27 deg [4.4 ALMA Limb Abundance Retrievals: "under the assumption of optically thin emission"]
  - fitting: Nonlinear least squares with MPFIT; 1σ errors from covariance matrix [4.4 ALMA Limb Abundance Retrievals: "obtained through nonlinear least-squares optimization using the MPFIT routine (cite: mar12), and $1\sigma$ parameter errors were determined from the covariance matrix"]
  - validation: Contribution functions for altitude sensitivity; comparison with CIRS retrievals [4.4 ALMA Limb Abundance Retrievals: "contribution functions (total flux as a function of altitude) were calculated within an ALMA beam centered at the respective $r_p$ value"]
- result: HNC lower altitude of emission = 730 ± ±60 km [abstract: "found to be confined predominantly to altitudes above $730\pm60$ km"]
- result: HNC abundance above 1030 km = 4.3e-5 ± ±1.3e-5 dimensionless [5.1 Chemistry and dynamics: "with an abundance of $(4.3\pm1.3)\times10^{-5}$ above 1030 km"]
- result: HNC peak emission radius = 3140 ± not stated km [4.4 ALMA Limb Abundance Retrievals: "the very high HNC peak emission radius of 3140 km is particularly surprising"]
- limitation (authors): Limb retrievals are approximate due to coarse resolution and simplified polygonal parameterization [5.2.2 Comparisons with prior observatio…: "our ALMA retrievals should be considered only approximate"]
- limitation (authors): Lifetime derivation relies on gross assumptions [5.2.1 Inferred molecular lifetimes: "Additional caution is required for their interpretation due to the gross assumptions made in their derivation."]
- not stated (card): Line-free channel ranges and polynomial order for continuum subtraction; Number of clean iterations and spectral windows/channel widths used in the cubes; Integration velocity ranges for each moment-0 map; How the two days' data were weighted and combined; Flux-weighted CIRS temperature profile and exact Simobserve configuration; Initial guesses and bounds for the MPFIT fits; Titan ephemeris used…

### 2016PASJ...68...88K: The Sunyaev-Zel'dovich effect at 5″: RX J1347.5-1145 imaged by ALMA (2016; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can ALMA (7-m plus 12-m arrays, Band 3) image the thermal SZE of RX J1347.5-1145 at 5 arcsec resolution, and how should missing flux be corrected and the map compared with X-ray and earlier SZE data?
- processing.imaging.weighting_robust: natural [3 Imaging Analysis: "Natural weighting is adopted to maximize sensitivity to an extended signal."]
- processing.imaging.deconvolver: Multi-Scale CLEAN, scales [0,5,8,13,20,30,45]", small-scale bias 0.4, gain 0.05, threshold 0.03 mJy (2.5σ) [3.3: "we adopt the scales \[$0, ~5'', ~8'', ~13'', ~20'', ~30'', ~45''$\] with the small-scale bias parameter of 0.4 as our fiducial choice."]
- step 3: Deconvolve extended SZE
  - method: Multi-Scale CLEAN with scale set chosen for minimal residuals and maximal recovered flux [3.3: "Having searched for a combination of parameters that gives minimal residuals as well as the maximal recovered flux"]
  - software: CASA
  - parameter: loop gain 0.05, threshold 0.03 mJy [3.3: "We also use a loop gain of 0.05 suitable for diffuse emission and a flux threshold of 0.03 mJy ($2.5 \sigma$)"]
  - validation: Converged for largest scale 40-50"; insensitive to bias <0.8 [3.3: "the deconvolved results are insensitive to the value of the small-scale bias parameter as long as its value is less than 0.8."]
- result: SZE intensity at south-east peak = -0.286 ± ±0.017 ±0.017 mJy/beam [3.4: "$-0.286 \pm 0.017 \pm 0.017$ mJy/beam"]
- result: SZE flux within 40" of SE peak = -12.4 ± ±0.2 ±0.8 mJy [3.4: "The measured flux within a radius of $40''$ from the south-east peak is $-12.4 \pm 0.2 \pm 0.8$ mJy."]
- limitation (authors): Missing flux on large scales due to no Total Power Array [Conclusions: "The accuracy of the map is limited primarily by missing flux arising from the lack of short-spacing data in the current configuration of ALMA."]
- not stated (card): Phase center coordinates (blank in text); Exact CASA task parameters (niter, mask, spw selection) for tclean/clean; Simulation details: simobserve PWV and noise settings, exact large-scale fall-off factor shape; Contour-binning and XSPEC fit details for pseudo pressure map; Whether Band 3 7-m QA2 weights were rescaled; Number of pixels/image size

### 2020A&A...634A...9M: The flickering nuclear activity of Fornax A (2020; agn_and_quasars, nearby_galaxies; multi_facility_alma_minor)
- question: What are the timescale and duty cycle of the nuclear activity of Fornax A, from the radio spectrum of its lobes, jets and core?
- processing.imaging.weighting_robust: Briggs, robust = 0.5 [2.3 ALMA: 108 GHz: "we used the task `tclean` with `Briggs` weighting and `robust` parameter 0.5."]
- processing.imaging.deconvolver: hogbom [2.3 ALMA: 108 GHz: "We performed cleaning using the `hogbom` algorithm"]
- step 1: Image ALMA 108 GHz continuum
  - method: CASA tclean mosaic of the Morita array continuum excluding CO and CN channels [2.3 ALMA: 108 GHz: "The continuum image was generated using CASA. In particular, we used the task `tclean` with `Briggs` weighting and `robust` parameter 0.5."]
  - software: CASA
  - parameter: robust 0.5, hogbom, gridder mosaic [2.3 ALMA: 108 GHz: "We performed cleaning using the `hogbom` algorithm within a mask selected by standard `auto-threshold` and mosaicking options"]
- limitation (authors): Core result holds only if thermal contamination of 108 GHz flux is below ~80%, which is poorly constrained [5.2: "This result holds as long as the thermal contamination to the 108 GHz flux of the kpc-core, poorly constrained by currently available data, is $\lesssim 80\%$."]
- not stated (card): ALMA image size and cell size; number of clean iterations and threshold; CASA version used for tclean; how the 108 GHz continuum flux scale uncertainty was set; how the kpc-core thermal contamination at 108 GHz was handled in detail; SYNAGE++ fitting details (grid, priors, error estimation); regions used for flux extraction (coordinates); whether the fourth spectral window frequency is given (tex…

### 2015ApJ...814..143A: The Peculiar Distribution of CH3CN in IRC +10216 Seen by ALMA (2015; evolved_stars, astrochemistry; observational_alma_primary)
- question: Where is CH3CN distributed in the envelope of IRC +10216 at sub-arcsec resolution, and where is it formed?
- processing.imaging.deconvolver: Högbom clean, no support [Observations: "Image deconvolution was carried out using the Högbom clean algorithm with no support"]
- processing.imaging.uv_taper: Taper to simulate 5.9" x 3.0" beam (SMA comparison) [Results: "we have applied a tapering procedure to the ALMA data to suppress long baselines and simulate what would be seen with a synthesized beam of 5$''$9 $\times$ 3$''$0"]
- step 1: Calibrate and image CH3CN J=14-13
  - method: CASA calibration, GILDAS continuum subtraction and Högbom clean [Observations: "Calibration was done with the software CASA[^2] and further data processing was done using the package GILDAS[^3]."]
  - software: CASA, GILDAS
  - validation: Dirty beam sidelobes <10 % of main beam [Observations: "The associated dirty beam has minor contributions from sidelobes (less than 10 % of the main beam"]
- result: Synthesized beam = 0.76 x 0.61 ± not stated arcsec [Observations: "The resulting synthesized beam is $0\mbox{\rlap{.}$''$}76\times0\mbox{\rlap{.}$''$}61$"]
- result: Ring radius / inner hole = ~2 / ~1 ± not stated arcsec [Results: "the maximum of the emission appears as a ring with a radius of $\sim2''$ and that there is a hole within $\sim1''$"]
- limitation (authors): Smooth spherical shell model does not reproduce fine structure; infrared pumping only partly included [2 Excitation and radiative transfer mod…: "Our model of a smooth hollow spherical shell does not aim at reproducing these fine details"]
- not stated (card): Channel ranges used for continuum subtraction; Clean mask/iteration count, weighting, cell and image size; How 30m and ALMA data were merged in GILDAS; CASA version; Description of the LVG code and fitting procedure for the abundance profile (no goodness-of-fit); Phase center coordinates

### 2019ApJ...882..118X: ALMA Detection of Vibrationally Excited (v <SUB>t</SUB> = 1, 2) Acetic Acid toward NGC 6334I (2019; astrochemistry, star_formation; observational_alma_primary)
- question: Are vibrationally excited (vt = 1, 2) acetic acid lines present toward NGC 6334I, and what are their excitation temperature, column density and spatial distribution?
- processing.imaging.weighting_robust: Briggs, robust 0.5 (Bands 4 and 6), 0.0 (Band 7) [2 Observations: "The Briggs weighting scheme and a Robust parameter of 0.5 for the Band 4 and 6 data and 0.0 for the Band 7 data"]
- step 1: Image and continuum-subtract
  - method: UV-plane continuum subtraction, tclean imaging, smoothing to 0.26'' beam [2 Observations: "used to subtract the continuum emission in the UV-plane."]
  - software: CASA
  - parameter: Briggs robust 0.5 (B4, B6), 0.0 (B7) [2 Observations: "a Robust parameter of 0.5 for the Band 4 and 6 data and 0.0 for the Band 7 data"]
- step 3: Fit Tex and column density
  - method: chi2 fit of single-Tex model to clean features only, with dV and Vlsr fixed to medians [3.1 Line Identification: "$\chi^2$ fitting is performed to statistically optimize the model and determine $T_\mathrm{ex}$ and $N_\mathrm{T}$."]
  - parameter: dV = 2.72 km/s, Vlsr = -6.90 km/s fixed [3.1 Line Identification: "The $\Delta V$ is fixed to $2.72~\mathrm{km\,s^{-1}}$ and the $V_\mathrm{lsr}$ is fixed to $-6.90~\mathrm{km\,s^{-1}}$."]
  - assumption: Partition function approximated by sixth-order polynomial [3.1 Line Identification: "The torsional-rotational partition function $Q_\mathrm{rv}$ is approximated by fitting the total internal partition function as a function of temperature ($T$) using a sixth order polynomial"]
  - fitting: chi2 minimization; errors from inverse Hessian plus rms propagation (1 sigma) [3.1 Line Identification: "which include the fitting error derived from the inverse of the Hessian matrix and the error propagation from the rms noise of the observed spectra."]
  - validation: Compared with ground-state results of El-Abd et al. (Tex 135 K, N 1.24e17) [3.1 Line Identification: "who measure an $N_\mathrm{T}$ of $1.24 \times 10^{17}~\mathrm{cm^{-2}}$ and a $T_\mathrm{ex}$ of 135 K"]
- result: Excitation temperature = 142 ± 25 K K [abstract: "the best-fit excitation temperature and column density are obtained to be 142(25) K and $1.12(7) \times 10^{17} \mathrm{cm^{-2}}$ respectively"]
- result: Column density = 1.12e17 ± 0.07e17 cm^-2 [abstract: "$1.12(7) \times 10^{17} \mathrm{cm^{-2}}$"]
- result: Line width (fixed) = 2.72 ± not stated km/s [3.1 Line Identification: "The $\Delta V$ is fixed to $2.72~\mathrm{km\,s^{-1}}$"]
- limitation (authors): Uncertainties may be underestimated since continuum subtraction systematics not included [3.1 Line Identification: "the uncertainties listed here might be underestimated as we have not incorporated the systematic uncertainties introduced by continuum subtraction."]
- not stated (card): Actual line-free channel ranges; CASA version; Calibration/pipeline details and flux uncertainty; tclean cell size, image size, niter, threshold, masks; Details of Gaussian fits and chi2 fit implementation; How T_bg values were measured; Band 4 and Band 7 observing parameters (arrays, dates) in this paper

### 2017A&A...600A...8D: ALMA observations of 4U 1728-34 and 4U 1820-30: first detection of neutron star X-ray binaries at 300 GHz (2017; stellar_physics, milky_way_ism; observational_alma_primary)
- question: How do jet properties (radio-to-mm spectrum and the optically thick/thin break) of two atoll neutron-star X-ray binaries relate to their hard/soft states, compared with black holes?
- processing.imaging.weighting_robust: uniform weighting, central frequency 301.99 GHz [2.2 ALMA: "extracted with uniform weighting and using a central frequency of 301.99 GHz"]
- step 1: Image ALMA continuum and measure flux
  - method: Re-generate images from calibrated products, self-calibrate, primary-beam correct, fit elliptical Gaussian for peak flux [2.2 ALMA: "the reported flux density for all sources in this section corresponds to the peak flux from the elliptical Gaussian fitted to the source emission in the image plane"]
  - software: CASA
  - parameter: uniform weighting; 301.99 GHz; self-cal 1 h [2.2 ALMA: "The images were self-calibrated on a timescale of 1 hour."]
  - validation: error is rms far from the source [2.2 ALMA: "the error corresponds to the rms of the image measured far away from the source position"]
- result: 4U 1728-34 ALMA 302 GHz peak flux = 1.40 ± 0.02 mJy/beam [Table 2: "4U 1728$-$34 | 17:31:57.6757 $\pm$ 0.0003 | -33:50:01.544 $\pm$ 0.005 | 1.40 $\pm$ 0.02"]
- result: 4U 1820-30 ALMA 302 GHz peak flux = 0.40 ± 0.02 mJy/beam [Table 2: "4U 1820$-$30 | 18:23:40.5050 $\pm$ 0.0004 | -30:21:40.089 $\pm$ 0.005 | 0.40 $\pm$ 0.02"]
- limitation (authors): Observations not strictly simultaneous; 4U 1728-34 in transitional state [Results: "our observations at different frequencies are not strictly simultaneous."]
- not stated (card): CASA version used for ALMA imaging; tclean parameters: cell size, image size, deconvolver, masking, niter/threshold; Self-calibration details beyond the 1 h solint; Fitting method for spectral indices and the break (interpolation procedure); Which flux scale uncertainty was applied for ALMA; Tudor et al. model for ATCA subtraction unavailable

### 2020MNRAS.495..943H: Revealing new features of the millimetre emission of the circumbinary envelope of Mira Ceti (2020; evolved_stars; archival_reuse)
- question: What is the morpho-kinematics of the circumbinary envelope of Mira Ceti between ~100 and ~350 au in SiO(5-4) and CO(3-2), and what do its fragments imply about Mira B's influence, mass ejection and turbulence?
- processing.imaging.weighting_robust: Natural weighting adopted (robust 1.0 also tested) [2.2 De-convolution: "The data used in the subsequent sections of the article were processed by GILDAS using optimal masks and natural weighting"]
- step 1: Recalibrate and image data
  - method: SiO recalibrated with ALMA scripts in CASA 4.2.2; CO deconvolved in GILDAS with optimal channel masks, natural weighting; CASA compared [2.2 De-convolution: "The data used in the subsequent sections of the article were processed by GILDAS using optimal masks and natural weighting"]
  - software: CASA, GILDAS
  - parameter: 20,000 clean iterations in illustrated GILDAS channel; brightness cut 0.08 Jy/beam [2.2 De-convolution: "Figure [2](#fig2) displays a clean map obtained from GILDAS after 20,000 iterations."]
  - validation: Brightness in four test regions compared across codes, masks and weightings; results checked with and without cut [2.2 De-convolution: "Systematically, we made sure that all the statements made in the remaining part of the article are robust with respect to this brightness cut and to de-convolution and cleaning processes."]
- limitation (authors): CO recoverable scale ~4 arcsec means much extended flux missing; CO deconvolution leaves negative regions; arbitrariness of fragment definition [2.1 Generalities: "The value of the recoverable scale associated with the CO observations implies that a large fraction of the extended flux is missing."]
- not stated (card): CLEAN thresholds, iteration counts and the actual per-channel masks for the adopted GILDAS CO cubes; GILDAS version; Which SiO imaging parameters (weighting, robust, beam) were used in CASA; Exact selection of data/calibrators for the CO set; Line-free channels and continuum treatment for CO; Details of the radiative transfer calculation for absorption (37%) and the 12CO/13CO abundance conversion

### 2020ApJ...898..146M: Dust Populations in the Iconic Vega Planetary System Resolved by ALMA (2020; debris_disks, exoplanets; observational_alma_primary)
- question: What is the mm-wavelength structure of Vega's outer dust belt, is there warm inner dust emission, and what planetary architecture explains it?
- processing.imaging.weighting_robust: natural weighting [2 Observations: "we image the combined 12m+ACA data with natural visibility weighting"]
- processing.imaging.deconvolver: multiscale [2 Observations: "We employed multi-frequency synthesis with multiscale deconvolution to best recover emission on extended scales from the outer belt"]
- processing.imaging.uv_taper: 10'' taper for large-scale image [2 Observations: "we produce an image of the combined 12m+ACA data with natural weighting, but with a 10$\ensuremath{''}$ *u-v* taper applied"]
- processing.imaging.multiscale_scales: 0, 1, 3, 9 times synthesized beam size [2 Observations: "we used scales of 0 (point source), 1, 3, and 9 times the expected synthesized beam size of the image"]
- limitation (authors): Total belt flux is model-dependent due to extrapolation to zero uv distance; position angle and inclination unconstrained [3.3.2 Modelling results: "The best-fit total belt flux at 1.34 mm varies depending on the model employed"]
- limitation (authors): Low target elevation and antenna shadowing [2 Observations: "The high source declination means that the elevations of the Vega scans were low - in the range 21-28$^{\circ}$."]
- not stated (card): CLEAN thresholds, masks, cell and image sizes; Priors ranges and starting positions of belt MCMC; Exact line-free channel selection beyond +-50 km/s and CO imaging details; Pipeline version and ALMA flagging details; Temperature grid details for RADMC-3D; Phase-center coordinates of Vega

### 2026A&A...705A.198M: The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview (2026; debris_disks, astrochemistry; large_program_or_survey)
- question: What is the spectro-spatial distribution, optical depth and mass of CO gas in ARKS debris discs, and is CO detectable in the 13 discs without previous detections?
- processing.imaging.weighting_robust: Briggs robust 0.5 for gas-bearing non-edge-on; robust 2 for edge-on HD 32297, HD 131488 and gas-free [2 Observations: "we employed Briggs weighting, with a robust parameter of 0.5."] [2 Observations: "we employed Briggs weighting with a robust parameter of 2, which is close to Natural weighting"]
- processing.imaging.deconvolver: multiscale in third iteration [2 Observations: "In the third and final `tclean` iteration, the deconvolver parameter was set to `multiscale`"]
- processing.imaging.multiscale_scales: [0,5,10] pixels [2 Observations: "We set the scales for the tclean deconvolution to be $[0,5,10]$"]
- step 1: Image line cubes
  - method: Three-stage tclean with Keplerian masks and multiscale CLEAN to 4 RMS [2 Observations: "We developed an imaging pipeline where `tclean` is called three times."]
  - software: CASA, tclean, keplerian_mask
  - parameter: robust 0.5 or 2; scales [0,5,10]; pixel 1/5 beam [2 Observations: "We set the scales for the tclean deconvolution to be $[0,5,10]$"]
  - assumption: Gas co-located with dust and near-Keplerian [2 Observations: "we use prior knowledge of each disc’s geometry, assuming gas is co-located with the dust"]
  - validation: Visual inspection of residuals [2 Observations: "which we confirmed by visual inspection"]
- limitation (authors): Optically thick masses are lower limits; inner radii are upper limits; degeneracy thick/thin needs radiative transfer [4.2: "To break this degeneracy, radiative transfer modelling needs to be carried out"]
- not stated (card): Line-free channels / continuum subtraction approach for the line cubes; Exact nbeams and C value for each system; Clean mask thresholds and RMS estimation region; Which Measurement Sets / execution blocks per target; Gofish annulus/aperture radii used for each spectrum; Excitation temperatures per disc used in mass calculation

### 2020A&A...642A..96P: A search for millimeter emission from the coldest and closest brown dwarf with ALMA (2020; stellar_physics, exoplanets; observational_alma_primary)
- question: Does the coldest known brown dwarf W0855 emit steady or pulsed millimeter radio emission at ~93 GHz, and what does this imply for radio astrometry and its magnetic field?
- processing.imaging.weighting_robust: natural weighting [2.2 Data analysis: "a pixel size of 0.4$\ensuremath{''}$ and natural weighting"]
- step 1: Image W0855 field alone
  - method: tclean mfs, natural weighting, single field [2.2 Data analysis: "only the W0855 data were imaged as a single field with a pixel size of 0.4$\ensuremath{''}$ and natural weighting"]
  - software: CASA tclean
  - parameter: pixel 0.4"; RMS 11.8 uJy vs expected 8 uJy [2.2 Data analysis: "noise RMS in the central region of the image of 11.8 $\mu$Jy, significantly worse than the expected 8 $\mu$Jy"]
  - validation: compared to expected sensitivity [2.2 Data analysis: "significantly worse than the expected 8 $\mu$Jy"]
- step 2: Remove 3C 209 sidelobes via mosaic
  - method: Re-image combining 3C 209 field and target field as mosaic [2.2 Data analysis: "This permitted us to remove the sidelobes of 3C 209 in the deconvolution"]
  - software: CASA tclean
  - validation: noise reduced to 7.3 uJy [2.2 Data analysis: "reduced the noise RMS in the region around the nominal position of W0855 to 7.3 $\mu$Jy"]
- result: Noise RMS, steady (mosaic image) = 7.3 ± not stated uJy/beam [2.2 Data analysis: "reduced the noise RMS in the region around the nominal position of W0855 to 7.3 $\mu$Jy"]
- limitation (authors): Limits are less constraining than the 4-8 GHz limits given the expected spectral index; only a single few-hour epoch. [Summary and conclusions: "they are less constraining because the power-law spectrum measured in similar objects such as TVLM 513"]
- not stated (card): Masking/clean threshold and iteration count for tclean; Mosaic details (phase centres, weighting of the 3C 209 field, gridder); Method for measuring flux in the beam-shaped region of the 30 s images; Whether 3C 209 was imaged with same deconvolver (hogbom assumed not stated); Image size; Pipeline flagging beyond standard

### 2020ApJ...888L..28S: Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA (2020; sun; observational_alma_primary)
- question: What are the temperature and density of a spicule seen at 100 GHz with ALMA, and how does it relate to spicules seen in IRIS Mg II and AIA 304 A?
- processing.imaging.weighting_robust: Briggs weighting (robust not stated) [2 Observations: "Clark algorithm and Briggs weighting scheme on CASA 5.4.0"]
- processing.imaging.deconvolver: CLEAN with Clark algorithm [2 Observations: "The CLEAN deconvolution method is used for the image synthesis with the Clark algorithm and Briggs weighting scheme on CASA 5.4.0"]
- step 1: Image synthesis and self-calibration
  - method: Per-2 s images with CLEAN after phase-only self-calibration; jitter removed by shifting images using auto-correlation offsets [2 Observations: "To remove jitter motion caused by the remaining phase error, we spatially shift the images based on the offsets estimated by the auto-correlation of the images."]
  - software: CASA
- limitation (authors): Width comparable to beam, so the actual width may be narrower [3 The spicules observed with ALMA, IRIS…: "the actual width can be narrower than the value because the width is comparable to the size of the synthesized beam."]
- limitation (authors): Only relative brightness temperatures because single-dish data not combined [2 Observations: "in this study, we only deal with relative brightness temperatures."]
- not stated (card): Briggs robust value, cell size, image size, clean iterations; Pre-event reference time for background subtraction; Details of the free-free opacity formula and constants used; Number of antennas and array configuration; Which sources were used as calibrators

### 2019ApJ...876L..10E: A Radio Source Coincident with the Superluminous Supernova PTF10hgi: Evidence for a Central Engine and an Analog of the Repeating FRB 121102? (2019; transients, other; multi_facility_alma_minor)
- question: What is the origin of the radio source detected at the position of the superluminous supernova PTF10hgi, and does it indicate a central engine analogous to the FRB121102 persistent source?
- processing.imaging.weighting_robust: Briggs, robust = 0.5 [2.3 ALMA Observations: "Briggs weighting (cite: Briggs1995) with a robust parameter of 0.5"]
- step 1: Image ALMA Band 3 and derive upper limit
  - method: MFS Briggs imaging in CASA; non-detection at VLA position gives 3 sigma limit [2.3 ALMA Observations: "We do not detect emission at the position of the VLA source, with a $3\sigma$ limit of $F_\nu(100\,{\rm GHz})\lesssim 44 \ \rm \mu$Jy."]
  - software: CASA
  - parameter: robust 0.5, 2400 pixels at 0.03 arcsec [2.3 ALMA Observations: "The field is imaged using 2400 pixels and an image scale of 0.03 arcsec per pixel, MFS, Briggs weighting"]
- result: ALMA 100 GHz flux density limit (3 sigma) = 44 ± not stated uJy [2.3 ALMA Observations: "with a $3\sigma$ limit of $F_\nu(100\,{\rm GHz})\lesssim 44 \ \rm \mu$Jy"]
- limitation (authors): ALMA 100 GHz limit is too shallow to constrain a star formation origin [3.1 Star formation Activity: "Our ALMA non-detection at 100 GHz does not provide meaningful constraints on a star formation origin"]
- not stated (card): ALMA array configuration, baselines and resolution; CASA version and whether pipeline products were used; ALMA flux, bandpass and phase calibrators; Spectral setup and continuum bandwidth; Final synthesized beam and rms; How the 3 sigma limit was measured

### 2020ApJS..251...14H: CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone (2020; milky_way_ism, star_formation; multi_facility_alma_minor)
- question: Which compact sources (<10'', ~0.4 pc) exist in the 1.3 mm SMA CMZoom continuum maps of the Central Molecular Zone, what are their properties and completeness, and what do they imply for CMZ star formation potential?
- processing.imaging.weighting_robust: Briggs, robust = 0.5 [3.2 Source Recovery and Simulated Obser…: "Briggs weighting with a robust parameter of 0.5 was used throughout."]
- processing.imaging.multiscale_scales: [0, 3, 9, 27] [3.2 Source Recovery and Simulated Obser…: "The `tclean` task was called with multi-scale parameter set to scales \[0, 3, 9, and 27\]."]
- step 1: Build local RMS map
  - method: Spatially averaged standard deviation of clean residual images using Gaussian kernel [3.1 Pruned Dendrogram Algorithm: "where $R_{x,y}$ corresponds to the residual value at pixel coordinates $(x,y)$, and $\ast G$ denotes convolution with a Gaussian kernel with $\sigma=14$ pixels, or $\sim$ 7$''$."]
  - software: CASA
  - parameter: kernel sigma = 14 pixels (~7'') [3.1 Pruned Dendrogram Algorithm: "Gaussian kernel with $\sigma=14$ pixels, or $\sim$ 7$''$"]
  - validation: Kernel size chosen from simulated-observation false-positive parameter study [8 Catalog Parameter Studies: "We chose to use the 14 pixel kernel as this choice also has a slightly lower average completeness mass."]
- step 2: Run dendrogram and prune leaves by local noise
  - method: Dendrogram on continuum map in MJy/sr, then keep leaves with peak >6 sigma (robust) or >4 sigma (high-completeness) and mean >2 sigma of local RMS [3.1 Pruned Dendrogram Algorithm: "the former prioritizing only the most robust leaves with a peak flux at least 6$\sigma$ above the local RMS estimate and the latter prioritizing a higher catalog completeness, which includes leaves with a peak flux at least 4$\sigma$ above the local RMS estimate."]
  - software: astrodendro
  - parameter: min value = 3x global noise (3 MJy/sr); min pixels ~ half average beam; min significance = global low noise [3.1 Pruned Dendrogram Algorithm: "The minimum pixel value is chosen to be a factor of three greater than this global noise estimate."]
  - validation: Parameter study of delta and kernel in Appendix [8 Catalog Parameter Studies: "we find that the mass and radius distribution of leaf properties in the catalog is well preserved"]
- step 3: Completeness and false-positive from simulated observations
  - method: Inject 10 point sources, simobserve, tclean, make RMS map, dendrogram and prune, count recovered sources [3.2 Source Recovery and Simulated Obser…: "A given point-source is considered to be recovered if its coordinates are located anywhere within a pruned leaf."]
  - software: CASA simobserve, CASA tclean, AATM
  - parameter: masses from flux assuming Td = 20 K [3.2 Source Recovery and Simulated Obser…: "we assume a constant dust temperature of 20K"]
  - assumption: Point-source-like emission model [3.2 Source Recovery and Simulated Obser…: "can be modeled by point-source-like emission for the purposes of this simplistic completeness estimate."]
  - validation: Completeness resilient to atmospheric variation [3.2 Source Recovery and Simulated Obser…: "The completeness results for our catalogs constructed from the simulated observations is resilient to variations typical in atmospheric conditions"]
- result: Robust catalog leaves = 285 ± not stated leaves [4.1 Leaf Distribution in l-b Space: "The robust catalog contains 285 leaves"]
- result: High-completeness catalog leaves = 816 ± not stated leaves [4.5 High-Completeness Catalog: "The change produces a catalog of 816 leaves as compared to the robust catalog with its 285 leaves."]
- result: Median local RMS = 13 ± not stated MJy/sr [3.1 Pruned Dendrogram Algorithm: "We find a median RMS over all surveyed regions is 13 MJy sr$^{-1}$."]
- result: 95% completeness mass, robust = 80 ± not stated Msun [3.2 Source Recovery and Simulated Obser…: "point-sources above 80 solar masses, under the typical observational conditions for the *CMZoom* survey, are detected with more than 95% completeness"]
- result: 95% completeness mass, high-completeness = ~50 ± not stated Msun [4.5 High-Completeness Catalog: "with a 95% completeness of $\sim 50$ M$_\odot$ (assuming T$_d$=20K)"]
- limitation (authors): Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2 [3.2 Source Recovery and Simulated Obser…: "These mass completeness estimates account only for the observational biases in observing point-source-like emission"]
- not stated (card): Exact dendrogram parameter values in the appendix-referenced setup (min_value, min_npix, min_delta numeric values beyond 3 MJy/sr scaling); Access/processing of CMZoom SMA maps from Dataverse versus Paper I imaging details; Simulated observation antenna configuration, integration time and weather settings; Herschel temperature map not yet published (in prep.); Exact point-source flux values and m…

### 2025ApJ...986L..22R: The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at 16.6 au from the Sun (2025; solar_system; observational_alma_primary)
- question: What are the molecular activity drivers, CO outgassing kinematics and continuum (nucleus/dust) properties of the distant active Oort cloud comet C/2014 UN271 at 16.6 au?
- processing.imaging.weighting_robust: natural weighting [2 Observations and Data Reduction: "using natural visibility weighting"]
- processing.imaging.deconvolver: Högbom [2 Observations and Data Reduction: "We deconvolved the point-spread function with the Högbom algorithm, using natural visibility weighting"]
- processing.imaging.uv_taper: 2'' Gaussian taper for March 17 CO image [3.1: "We applied a 2$\ensuremath{''}$ Gaussian taper in the $uv$-plane to the March 17 CO image"]
- step 1: Calibrate and image CO and continuum
  - method: Standard CASA flagging/calibration, post-pipeline flux correction, Högbom clean with natural weighting, primary beam correction [2 Observations and Data Reduction: "The data were flagged, calibrated, and imaged using standard routines in Common Astronomy Software Applications (CASA) package version 6.6.1"]
  - software: CASA
  - parameter: 10'' mask, threshold 2x rms [2 Observations and Data Reduction: "a 10$\ensuremath{''}$ diameter mask centered on the peak continuum position, and a flux threshold of twice the rms noise"]
  - validation: Flux scale checked against ALMA calibrator catalog [Flux Calibration: "We compared the 233 GHz flux predicted by the ALMA Flux Estimation algorithm for each quasar on the date of observations against the nearby measured values."]
- limitation (authors): Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower [4.1.1: "Our two-component radiative transfer model is a simplification of this geometry"]
- not stated (card): Line-free channels and continuum subtraction method; Image pixel/cell size and image size; Exact spectral window frequencies and CO rest frequency; Initial guesses and bounds for lmfit fits; Choice of aperture/extraction for interferometric spectra fitted; Pipeline version; Calibrator catalog data used for polynomial fit details; Phase center coordinates

### 2024A&A...689A.317G: Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii (2024; evolved_stars, astrochemistry, stellar_physics; observational_alma_primary)
- question: What do ALMA continuum, H30alpha and molecular line maps reveal about the inner regions of the symbiotic system R Aqr, and how are weak molecules distributed there?
- processing.imaging.weighting_robust: robust weighting (value not given); natural weighting for SPW 27 and 29 in Band 6 and low-res maps [2 Observations: "we worked to reach our best angular resolution using robust weighting."]
- processing.imaging.deconvolver: Hogbom; ~4000 components first pass, 5000 final; stop at sigma_p/2 [2 Observations: "Final clean maps were obtained imposing a maximum amplitude of the absolute value of the residual map of $\sigma_{p}$/2"]
- step 2: Subtract continuum and clean maps
  - method: uv-plane continuum subtraction then Hogbom CLEAN with two-pass stopping criteria [2 Observations: "We completed a first cleaning using a maximum number of clean components of $\sim$4000."]
  - software: GILDAS
  - assumption: Continuum constant within each spectral window (spectral index 2, <1% variation) [2 Observations: "assuming a spectral index of two, differences in the intensity of the continuum emission smaller than 1 % are expected"]
  - validation: Checked line-free channels for residuals and no overcleaning [2 Observations: "We checked that the final clean maps do not show overcleaned regions."]
- limitation (authors): In-falling component size is not conclusive [5 Modeling: "Therefore, the obtained result concerning the size of the in-falling component is not conclusive."]
- not stated (card): Robust parameter values; Line-free channel ranges per spectral window; Self-calibration solution intervals and reference components; Cell and image sizes; CASA and GILDAS versions; Model code and fitting figure of merit; dust Gaussian parameters; Band 7 flux date inconsistency (November 2018 vs 2017)

### 2015ApJ...798..124R: ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146 (2015; debris_disks; observational_alma_primary)
- question: What is the radial distribution of mm-sized dust in the HD 107146 debris disk, and is there a gap or dip in the dust surface density?
- processing.imaging.weighting_robust: natural weighting, Briggs robust = 2 [3.1 Continuum Images: "obtained with natural weighting using a Briggs robust parameter of 2"]
- processing.imaging.uv_taper: Gaussian uv-taper, on-sky FWHM 2 arcsec [3.1 Continuum Images: "weighted with a Gaussian uv-taper with an on-sky FWHM of 2 arcsec"]
- step 2: image continuum and measure integrated flux
  - method: clean imaging with natural and tapered weighting; flux integrated over area above 2σ in the tapered map [3.1 Continuum Images: "This was obtained by integrating the surface brightness over the area showing emission at"]
  - software: CASA
  - validation: compared with CARMA flux of 10.4 ± 1.4 mJy [3.1 Continuum Images: "consistent at $\approx 1\sigma$ with the measurement of 10.4 $\pm$ 1.4 mJy by (cite: Corder:2009)"]
- result: Integrated flux density at 1.25 mm = 12.5 ± 1.3 mJy [3.1 Continuum Images: "The integrated flux density from the disk is 12.5 $\pm$ 1.3 mJy at 1.25 mm."]
- limitation (authors): Data cannot distinguish between gap and double power-law forms; dust opacity degenerate with surface density [5.3 Double power-law: "The ALMA data presented in this paper do not allow us to distinguish between these possible different functional forms"]
- not stated (card): Number of emcee walkers and iterations (only 'several hundreds') and burn-in; Priors and bounds on model parameters; Clean threshold, mask, cell and image size of the CLEAN images; Whether CASA clean or other tools were used for the visibility extraction and weight rescaling in detail; Which spectral windows/channels were used for continuum (line-free channels excluded CO); Exact dust opacity tab…

### 2024ApJ...968L..19F: Deep Search for Phosphine in a Prestellar Core (2024; astrochemistry, star_formation; observational_alma_primary)
- question: Can gas-phase PH3 be detected in the prestellar core L1544, and what does its abundance imply for the volatile phosphorus elemental abundance?
- processing.imaging.weighting_robust: Briggs, robust 0.5 [2 Observations: "with the Briggs weighting and a robustness parameter of 0.5"]
- step 1: Image cube and continuum
  - method: CASA tclean with auto-multithresh, uvcontsub, impbcor; continuum from continuum window plus line-free channels [2 Observations: "The aggregate continuum image is constructed by using the continuum window in addition to the line-free channels selected from the other five spectral windows."]
  - software: CASA
  - parameter: Briggs robust 0.5 [2 Observations: "with the Briggs weighting and a robustness parameter of 0.5"]
- limitation (authors): Collisional rate coefficients for PH3-H2 unavailable; extended continuum emission resolved out may explain lower N(H2) [Appendix: H2 column density: "The contribution from the largely-extended ($>$25") continuum emission that was resolved out in the ACA observations may account for the above discrepancy."]
- not stated (card): Line-free channels used for continuum and uvcontsub; Image size, cell size, clean threshold/niter; Calibrators and pipeline version; Flux scale uncertainty; Full P chemical network reaction list and rate parameters (partly in Furuya 2023 submitted); Spectral rms in K converted from Jy/beam details

### 2023PSJ.....4..142C: Thermal Properties of the Leading Hemisphere of Callisto Inferred from ALMA Observations (2023; solar_system; observational_alma_primary)
- question: What are the global thermal properties (thermal inertia, emissivity) and local thermal anomalies of Callisto's leading hemisphere at 0.87 mm?
- processing.imaging.weighting_robust: Briggs, robust = 0.0 [2.2 Data Analysis: "we adopted a Briggs weighting scheme with a robust parameter of 0.0"]
- processing.imaging.deconvolver: Clark [2.2 Data Analysis: "used the "Clark" deconvolver"]
- step 1: self-calibrate and image
  - method: iterative phase-only self-calibration with tclean and gaincal, starting from a Lambertian disk model [2.2 Data Analysis: "Our phase-only self-calibration using CASA followed as such: for the first round of imaging, a Lambertian disk scaled to the size and brightness temperature of Callisto was used as a startmodel"]
  - software: CASA, tclean, gaincal, applycal
  - parameter: Briggs robust 0.0, Clark deconvolver, solint down to 2 s [2.2 Data Analysis: "we adopted a Briggs weighting scheme with a robust parameter of 0.0, and used the "Clark" deconvolver"]
  - validation: dynamic range ~580 [2.2 Data Analysis: "A dynamic range of $\sim$580 (peak flux/rms in units of Jy/beam) was obtained for the final image."]
- limitation (authors): cost function formally limited to independent data points [3.1 Two-Component Mixtures: "we note that the cost function is formally limited to data sets with independent data points."]
- limitation (authors): single observation of leading hemisphere only [5 Conclusion: "However, such a hypothesis is difficult to confirm in the context of a single thermal observation."]
- not stated (card): tclean image size, cell size, niter, threshold and masks; startmodel Lambertian disk parameters; intermediate self-cal solints and number of iterations; CASA version; emissivity/thermal model input parameters (density, heat capacity, dielectrics, roughness); exact cost function and chi-squared cutoff implementation; thermophysical model code availability; quasar J1232-0224 role details

### 2015ApJ...803...97S: An ALMA Imaging Study of Methyl Formate (HCOOCH<SUB>3</SUB>) in Torsionally Excited States toward Orion KL (2015; astrochemistry, star_formation; archival_reuse)
- question: Do rotational and vibrational (torsional) temperatures of methyl formate differ in Orion KL Compact Ridge and Hot Core when resolved with ALMA, unlike the earlier single-dish result?
- processing.imaging.weighting_robust: natural weighting [Observations: "The natural-weighted beam size was 1.7$''$ $\times$ 1.4$''$ with the position angle of 171$^\circ$."]
- processing.imaging.deconvolver: Hogbom [Observations: "The Hogbom algorithm was used for the clean."]
- step 1: Image cubes and remove continuum
  - method: CASA imaging with Hogbom clean, natural weighting; linear continuum fit to line-free channels [Observations: "A first order fit to the line-free channels was used to estimate the continuum emission removal. The Hogbom algorithm was used for the clean."]
  - software: CASA
- limitation (authors): Many lines blended; Hot Core v_t=2 T_rot not determinable [Rotation Diagrams: "It was not possible to determine the realistic rotational temperature of HCOOCH$_{3}$ in $v_{t} =$2 for the Hot Core."]
- not stated (card): CASA version and calibration (SV data products used?) details; Line-free channel ranges and continuum fit per setting; Clean mask, image size, cell size, number of iterations/threshold; Spectrum extraction aperture (green circle size) for Compact Ridge and Hot Core; Gaussian fitting procedure and uncertainty derivation for line parameters; Rotation diagram fitting method (weights, treatment of er…

## All papers in this technique

- 2012A&A...544L...7P (2012): The first ALMA view of IRAS 16293-2422. Direct detection of infall onto source B and high-resolution kinematics of source A
- 2012A&A...548A..69N (2012): Outflow structure and velocity field of Orion source. I. ALMA imaging of SiO isotopologue maser and thermal emission
- 2012ApJ...749..162O (2012): Evidence for Multiple Pathways to Deuterium Enhancements in Protoplanetary Disks
- 2012ApJ...750L..21B (2012): Constraining the Planetary System of Fomalhaut Using High-resolution ALMA Observations
- 2012ApJ...754L..17Z (2012): ALMA Observations of the Outflow from Source I in the Orion-KL Region
- 2012ApJ...757..129R (2012): Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk
- 2012ApJ...761L..32W (2012): ALMA Submillimeter Continuum Imaging of the Host Galaxies of GRB 021004 and GRB 080607
- 2013A&A...549L...6K (2013): ALMA CO J = 6-5 observations of IRAS 16293-2422. Shocks and entrainment
- 2013A&A...554A..78P (2013): Acetone in Orion BN/KL. High-resolution maps of a special oxygen-bearing molecule
- 2013A&A...555A..73K (2013): ALMA detection of the rotating molecular disk wind from the young star HD 163296
- 2013A&A...556L...1V (2013): ALMA observations of the variable <SUP>12</SUP>CO/<SUP>13</SUP>CO ratio around the asymptotic giant branch star R Sculptoris
- 2013A&A...557L..11B (2013): ALMA observations of the Red Rectangle, a preliminary analysis
- 2013AJ....146...47I (2013): High-density Molecular Gas Properties of the Starburst Galaxy NGC 1614 Revealed with ALMA
- 2013AJ....146...91I (2013): ALMA Detection of the Vibrationally Excited HCN J = 4-3 Emission Line in the AGN-hosting Luminous Infrared Galaxy IRAS 20551-4250
- 2013ApJ...762L..21M (2013): Millimeter Emission Structure in the First ALMA Image of the AU Mic Debris Disk
- 2013ApJ...763..120C (2013): The Anatomy of an Extreme Starburst within 1.3 Gyr of the Big Bang Revealed by ALMA
- 2013ApJ...764L..14Z (2013): ALMA 690 GHz Observations of IRAS 16293-2422B: Infall in a Highly Optically Thick Disk
- 2013ApJ...765L..14Q (2013): First Detection of c-C<SUB>3</SUB>H<SUB>2</SUB> in a Circumstellar Disk
- 2013ApJ...767..132H (2013): ALMA Observations of SPT-discovered, Strongly Lensed, Dusty, Star-forming Galaxies
- 2013ApJ...768...91H (2013): An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: Source Catalog and Multiplicity
- 2013ApJ...768L..38H (2013): Submillimeter H<SUB>2</SUB>O Maser in Circinus Galaxy—a New Probe for the Circumnuclear Region of Active Galactic Nuclei
- 2013ApJ...770...13W (2013): Redshift 6.4 Host Galaxies of 10<SUP>8</SUP> Solar Mass Black Holes: Low Star Formation Rate and Dynamical Mass
- 2013ApJ...770..142N (2013): The Abundance of H<SUB>2</SUB>O and HDO in Orion Kl from Herschel/HIFI
- 2013ApJ...773L..34K (2013): Carbon Monoxide in the Cold Debris of Supernova 1987A
- 2013ApJ...774...16R (2013): A Spatially Resolved Vertical Temperature Gradient in the HD 163296 Disk
- 2013ApJ...774L...7M (2013): ALMA Observations of the Massive Molecular Outflow G331.512-0.103
- 2013ApJ...775L..31S (2013): ALMA Observations of the IRDC Clump G34.43+00.24 MM3: Hot Core and Molecular Outflows
- 2013ApJ...777...85N (2013): Deuterated Molecules in Orion KL from Herschel/HIFI
- 2013ApJ...777L..25M (2013): ALMA Continuum Observations of a 30 Myr Old Gaseous Debris Disk around HD 21997
- 2013ApJ...778L..25C (2013): Unveiling the Dust Nucleation Zone of IRC+10216 with ALMA
- 2013ApJ...779...96T (2013): The Dynamics of Massive Starless Cores with ALMA
- 2013MNRAS.430L..10L (2013): ALMA and VLA observations of the outflows in IRAS 16293-2422.
- 2013MNRAS.432....2K (2013): An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: high-resolution 870 μm source counts
- 2013Natur.493..191C (2013): Flows of gas through a protoplanetary gap
- 2013PASJ...65L...7I (2013): Active Galactic Nucleus and Extended Starbursts in a Midstage Merger VV 114
- 2014A&A...563A.136M (2014): UVMULTIFIT: A versatile tool for fitting astronomical radio interferometric data
- 2014A&A...565A..59D (2014): ALMA resolves turbulent, rotating [CII] emission in a young starburst galaxy at z = 4.8
- 2014A&A...567A.125G (2014): Molecular line emission in NGC 1068 imaged with ALMA. I. An AGN-driven outflow in the dense molecular gas
- 2014A&A...568A..92M (2014): Herschel-ATLAS and ALMA. HATLAS J142935.3-002836, a lensed major merger at redshift 1.027
- 2014A&A...569A..11S (2014): A necklace of dense cores in the high-mass star forming region G35.20-0.74 N: ALMA observations
- 2014A&A...572L...9R (2014): ALMA sub-mm maser and dust distribution of VY Canis Majoris
- 2014AJ....147..141H (2014): ALMA View of G0.253+0.016: Can Cloud-Cloud Collision form the Cloud?
- 2014ApJ...781L..39T (2014): Serendipitous ALMA Detection of a Distant CO-emitting X-Ray Bright Galaxy
- 2014ApJ...782L...2I (2014): Dust Production and Particle Acceleration in Supernova 1987A Revealed with ALMA
- 2014ApJ...783...84S (2014): The Evolution of Interstellar Medium Mass Probed by Dust Emission: ALMA Observations at z = 0.3-2
- 2014ApJ...783L..13P (2014): Large-scale Asymmetries in the Transitional Disks of SAO 206462 and SR 21
- 2014ApJ...784...62A (2014): Circumstellar Disks around Binary Stars in Taurus
- 2014ApJ...784...78R (2014): Massive Molecular Gas Flows in the A1664 Brightest Cluster Galaxy
- 2014ApJ...785L..12C (2014): Spiral Arms in the Disk of HD 142527 from CO Emission Lines with ALMA
- 2014ApJ...786..114L (2014): ALMA Results of the Pseudodisk, Rotating Disk, and Jet in the Continuum and HCO<SUP>+</SUP> in the Protostellar System HH 212
- 2014ApJ...787...42C (2014): An ALMA Continuum Survey of Circumstellar Disks in the Upper Scorpius OB Association
- 2014ApJ...787...48X (2014): ALMA Observations of Warm Molecular Gas and Cold Dust in NGC 34
- 2014ApJ...790..160S (2014): ALMA Observations of a Candidate Molecular Outflow in an Obscured Quasar
- 2014ApJ...791...20R (2014): Brown Dwarf Disks with ALMA
- 2014ApJ...791...95A (2014): η Carinae Baby Homunculus Uncovered by ALMA
- 2014ApJ...791..123W (2014): A Study of Dynamical Processes in the Orion KL Region Using ALMA—Probing Molecular Outflow and Inflow
- 2014ApJ...791L...6W (2014): ALMA Hints at the Presence of two Companions in the Disk around HD 100546
- 2014ApJ...792...34O (2014): ALMA Observation of 158 μm [C II] Line and Dust Continuum of a z = 7 Normally Star-forming Galaxy in the Epoch of Reionization
- 2014ApJ...792L...2C (2014): Mapping the Release of Volatiles in the Inner Comae of Comets C/2012 F6 (Lemmon) and C/2012 S1 (ISON) Using the Atacama Large Millimeter/Su…
- 2014ApJ...792L..25V (2014): Spatially Resolved HCN J = 4-3 and CS J = 7-6 Emission from the Disk around HD 142527
- 2014ApJ...795..156W (2014): ALMA Observations of the Antennae Galaxies. I. A New Window on a Prototypical Merger
- 2014ApJ...795L..25R (2014): Turbulence Sets the Initial Conditions for Star Formation in High-pressure Environments
- 2014ApJ...795L..30C (2014): ALMA Measurements of the HNC and HC<SUB>3</SUB>N Distributions in Titan's Atmosphere
- 2014ApJ...796....1T (2014): Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE
- 2014ApJ...796...82Z (2014): Spectral and Morphological Analysis of the Remnant of Supernova 1987A with ALMA and ATCA
- 2014ApJ...797...27F (2014): Revealing H<SUB>2</SUB>D<SUP>+</SUP> Depletion and Compact Structure in Starless and Protostellar Cores with ALMA
- 2014ApJ...797...90S (2014): An Infrared-luminous Merger with Two Bipolar Molecular Outflows: ALMA and SMA Observations of NGC 3256
- 2014ApJS..214....1U (2014): Cold Molecular Gas in Merger Remnants. I. Formation of Molecular Gas Disks
- 2014MNRAS.442..577T (2014): An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: radio properties and the far-infrared/radio correlation
- 2014PASJ...66..106H (2014): VERA and ALMA observations of the H<SUB>2</SUB>O supermaser burst in Orion KL
- 2014Sci...345.1584B (2014): Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide
- 2015A&A...573L...1O (2015): ALMA observations of anisotropic dust mass loss in the inner circumstellar environment of the red supergiant VY Canis Majoris
- 2015A&A...573L...4L (2015): ALMA observations of α Centauri. First detection of main-sequence stars at 3 mm wavelength
- 2015A&A...576L...2S (2015): ALMA detection of [C ii] 158 μm emission from a strongly lensed z = 2.013 star-forming galaxy
- 2015A&A...576L..15O (2015): ALMA view of the circumstellar environment of the post-common-envelope-evolution binary system HD 101584
- 2015A&A...577L...4V (2015): Resolving the stellar activity of the Mira AB binary with ALMA
- 2015A&A...580A...1M (2015): The fast molecular outflow in the Seyfert galaxy IC 5063 as seen by ALMA
- 2015A&A...582L...1T (2015): Searching for trans ethyl methyl ether in Orion KL⋆
- 2015A&A...583A..66H (2015): Probing the final stages of protoplanetary disk evolution with ALMA
- 2015A&A...584A..32M (2015): (Sub)millimetre interferometric imaging of a sample of COSMOS/AzTEC submillimetre galaxies. II. The spatial extent of the radio-emitting re…
- 2015A&A...584A..42A (2015): Probing highly obscured, self-absorbed galaxy nuclei with vibrationally excited HCN
- 2015A&A...584A..78C (2015): ALMA constraints on the faint millimetre source number counts and their contribution to the cosmic infrared background
- 2015A&A...584A..99E (2015): The Dragonfly Galaxy. II. ALMA unveils a triple merger and gas exchange in a hyper-luminous radio galaxy at z = 2
- 2015ApJ...798...85P (2015): CO Gas Inside the Protoplanetary Disk Cavity in HD 142527: Disk Structure from ALMA
- 2015ApJ...798..124R (2015): ALMA Observations of the Debris Disk around the Young Solar Analog HD 107146
- 2015ApJ...798L..23K (2015): An ALMA Disk Mass for the Candidate Protoplanetary Companion to FW Tau
- 2015ApJ...801...82H (2015): ALMA Imaging of Millimeter/Submillimeter Continuum Emission in Orion KL
- 2015ApJ...802...69B (2015): Radio and Millimeter Monitoring of Sgr A*: Spectrum, Variability, and Constraints on the G2 Encounter
- 2015ApJ...803...60S (2015): ALMA Multi-line Observations of the IR-bright Merger VV 114
- 2015ApJ...803...97S (2015): An ALMA Imaging Study of Methyl Formate (HCOOCH<SUB>3</SUB>) in Torsionally Excited States toward Orion KL
- 2015ApJ...804...37L (2015): ALMA Resolves the Spiraling Accretion Flow in the Luminous OB Cluster-forming Region G33.92+0.11
- 2015ApJ...805..186L (2015): Jet Motion, Internal Working Surfaces, and Nested Shells in the Protostellar System HH 212
- 2015ApJ...806...17R (2015): Morphology and Kinematics of Warm Molecular Gas in the Nuclear Region of Arp 220 as Revealed by ALMA
- 2015ApJ...806L..17S (2015): ALMA Resolves the Properties of Star-forming Regions in a Dense Gas Disk at z ∼ 3
- 2015ApJ...806L..22C (2015): On the Nature of the Tertiary Companion to FW Tau: ALMA CO Observations and SED Modeling
- 2015ApJ...806L..34F (2015): Local Instability Signatures in ALMA Observations of Dense Gas in NGC 7469
- 2015ApJ...807..128S (2015): The SCUBA-2 Cosmology Legacy Survey: ALMA Resolves the Bright-end of the Sub-millimeter Number Counts
- 2015ApJ...807..180W (2015): Star Formation and the Interstellar Medium in z &gt; 6 UV-luminous Lyman-break Galaxies
- 2015ApJ...807L...4F (2015): High-mass Star Formation Triggered by Collision between CO Filaments in N159 West in the Large Magellanic Cloud
- 2015ApJ...808...36M (2015): New Measurements of the Radio Photosphere of Mira Based on Data from the JVLA and ALMA
- 2015ApJ...808...69B (2015): ALMA Observations of the Largest Proto-Planetary Disk in the Orion Nebula, 114-426: A CO Silhouette
- 2015ApJ...808..102K (2015): Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA
- 2015ApJ...808L...1A (2015): The 2014 ALMA Long Baseline Campaign: An Overview
- 2015ApJ...810..112O (2015): Double DCO<SUP>+</SUP> Rings Reveal CO Ice Desorption in the Outer Disk Around IM Lup
- 2015ApJ...810L...7V (2015): A Concentration of Centimeter-sized Grains in the Ophiuchus IRS 48 Dust Trap
- 2015ApJ...811...39I (2015): ALMA Observations of the Submillimeter Dense Molecular Gas Tracers in the Luminous Type-1 Active Nucleus of NGC 7469
- 2015ApJ...811...92C (2015): Accretion Kinematics through the Warped Transition Disk in HD142527 from Resolved CO(6-5) Observations
- 2015ApJ...811..115W (2015): The Innermost Mass Distribution of the Gravitational Lens SDP.81 from ALMA Observations
- 2015ApJ...811..124S (2015): Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies
- 2015ApJ...811L...3T (2015): SXDF-ALMA 1.5 arcmin<SUP>2</SUP> Deep Survey: A Compact Dusty Star-forming Galaxy at z = 2.5
- 2015ApJ...811L...4Z (2015): Origin and Kinematics of the Eruptive Flow from XZ Tau Revealed by ALMA
- 2015ApJ...812...27A (2015): ALMA Observations of the Transition from Infall Motion to Keplerian Rotation around the Late-phase Protostar TMC-1A
- 2015ApJ...812...88M (2015): Stellar Masses and Star Formation Rates of Lensed, Dusty, Star-forming Galaxies from the SPT Survey
- 2015ApJ...812..126C (2015): A Compact Concentration of Large Grains in the HD 142527 Protoplanetary Dust Trap
- 2015ApJ...812..134H (2015): The Early ALMA View of the FU Ori Outburst System
- 2015ApJ...812L..23S (2015): A Higher Efficiency of Converting Gas to Stars Pushes Galaxies at z ∼ 1.6 Well Above the Star-forming Main Sequence
- 2015ApJ...813...99F (2015): Weak Turbulence in the HD 163296 Protoplanetary Disk Revealed by ALMA CO Observations
- 2015ApJ...813..118M (2015): Microwave Continuum Emission and Dense Gas Tracers in NGC 3627: Combining Jansky VLA and ALMA Observations
- 2015ApJ...813..128Q (2015): Chemical Imaging of the CO Snow Line in the HD 163296 Disk
- 2015ApJ...813L..19J (2015): A Keplerian-like Disk around the Forming O-type Star AFGL 4176
- 2015ApJ...814...22E (2015): Detection of Infall in the Protostar B335 with ALMA
- 2015ApJ...814..143A (2015): The Peculiar Distribution of CH3CN in IRC +10216 Seen by ALMA
- 2015MNRAS.450L..80B (2015): ALMA observations of 99 GHz free-free and H40α line emission from star formation in the centre of NGC 253
- 2015MNRAS.451.1141M (2015): The ALMA Patchy Deep Survey: a blind search for [C II] emitters at z ∼ 4.5
- 2015MNRAS.451L..40R (2015): ALMA imaging of SDP.81 - I. A pixelated reconstruction of the far-infrared continuum emission.
- 2015MNRAS.452...54M (2015): The assembly of `normal' galaxies at z ∼ 7 probed by ALMA
- 2015MNRAS.453.4324M (2015): ALMA reveals sunburn: CO dissociation around AGB stars in the globular cluster 47 Tucanae
- 2015Natur.522..455C (2015): Galaxies at redshifts 5 to 6 with systematically low dust content and high [C II] emission
- 2015Natur.525..218R (2015): Dense cloud cores revealed by CO in the low metallicity dwarf galaxy WLM
- 2015Natur.527...70P (2015): Episodic molecular outflow in the very young protostellar cluster Serpens South
- 2016A&A...585A..58V (2016): Resolved gas cavities in transitional disks inferred from CO isotopologs with ALMA
- 2016A&A...586A...5M (2016): A detailed view of the gas shell around R Sculptoris with ALMA
- 2016A&A...586A..69P (2016): The radio continuum spectrum of Mira A and Mira B up to submillimeter wavelengths
- 2016A&A...586A..70L (2016): Anatomy of a blazar in the (sub-)millimeter: ALMA observations of PKS 0521-365
- 2016A&A...586A..99H (2016): Steepening of the 820 μm continuum surface brightness profile signals dust evolution in TW Hydrae's disk
- 2016A&A...586L...1G (2016): The shadow of the Flying Saucer: A very low temperature for large dust grains
- 2016A&A...586L...7B (2016): An ALMA view of the interstellar medium of the z = 4.77 lensed starburst SPT-S J213242-5802.9
- 2016A&A...587A..44P (2016): Sub-kpc star formation law in the local luminous infrared galaxy IC 4687 as seen by ALMA
- 2016A&A...587A..91B (2016): Exploring molecular complexity with ALMA (EMoCA): Deuterated complex organic molecules in Sagittarius B2(N2)
- 2016A&A...589L...5M (2016): Detection of extragalactic CF<SUP>+</SUP> toward PKS 1830-211. Chemical differentiation in the absorbing gas
- 2016A&A...590A..73A (2016): A precessing molecular jet signaling an obscured, growing supermassive black hole in NGC 1377?
- 2016A&A...591A..73G (2016): ALMA finds dew drops in the dusty spider's web
- 2016A&A...592A..76D (2016): ALMA-resolved salt emission traces the chemical footprint and inner wind morphology of VY Canis Majoris
- 2016A&A...593A..44L (2016): The 492 GHz emission of Sgr A* constrained by ALMA
- 2016A&A...593A..61M (2016): Dual differential polarimetry. A technique to recover polarimetric information from dual-polarization observations
- 2016A&A...593A..92B (2016): Further ALMA observations and detailed modeling of the Red Rectangle
- 2016A&A...593L...2N (2016): Planck's Dusty GEMS. II. Extended [CII] emission and absorption in the Garnet at z = 3.4 seen with ALMA
- 2016A&A...593L..19M (2016): The MHz-peaked radio spectrum of the unusual γ-ray source PMN J1603-4904
- 2016A&A...594A..81P (2016): High-velocity extended molecular outflow in the star-formation dominated luminous infrared galaxy ESO 320-G030
- 2016A&A...595L...7D (2016): ALMA reveals optically thin, highly excited CO gas in the jet-driven winds of the galaxy IC 5063
- 2016A&A...596A..50G (2016): The ALMA detection of CO rotational line emission in AGB stars in the Large Magellanic Cloud
- 2016A&A...596A..75S (2016): Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z 3.3
- 2016A&A...596A..88L (2016): ALMA observations of the <ASTROBJ>Th 28</ASTROBJ> protostellar disk. A new example of counter-rotation between disk and optical jet
- 2016AJ....152..218I (2016): ALMA HCN and HCO+ J =3-2 Observations of Optical Seyfert and Luminous Infrared Galaxies: Confirmation of Elevated HCN-to-HCO+ Flux Ratios i…
- 2016ApJ...816...27S (2016): Resolved Millimeter-wavelength Observations of Debris Disks around Solar-type Stars
- 2016ApJ...816...37V (2016): Bright [C II] and Dust Emission in Three z &gt; 6.6 Quasar Host Galaxies Observed by ALMA
- 2016ApJ...816L...6D (2016): The Strikingly Uniform, Highly Turbulent Interstellar Medium of the Most Luminous Galaxy in the Universe
- 2016ApJ...817..168H (2016): ALMA Observation of the 658 GHz Vibrationally Excited H2O Maser in Orion KL Source I
- 2016ApJ...818..156C (2016): A Disk-based Dynamical Constraint on the Mass of the Young Binary DQ Tau
- 2016ApJ...818..158A (2016): Planetary System Formation in the Protoplanetary Disk around HL Tauri
- 2016ApJ...818L..16Z (2016): On the Commonality of 10-30 AU Sized Axisymmetric Dust Structures in Protoplanetary Disks
- 2016ApJ...819...82S (2016): Properties of the Interstellar Medium in Star-Forming Galaxies at z ~ 1.4 Revealed with ALMA
- 2016ApJ...819..102V (2016): Dust Masses of Disks around 8 Brown Dwarfs and Very Low-mass Stars in Upper Sco OB1 and Ophiuchus
- 2016ApJ...820...19T (2016): Mapping CO Gas in the GG Tauri A Triple System with 50 au Spatial Resolution
- 2016ApJ...820...83S (2016): ISM Masses and the Star formation Law at Z = 1 to 6: ALMA Observations of Dust Continuum in 145 Galaxies in the COSMOS Survey Field
- 2016ApJ...820..118Z (2016): ALMA Imaging of the CO (6-5) Line Emission in NGC 7130*
- 2016ApJ...820L..25Y (2016): Gas Gaps in the Protoplanetary Disk around the Young Protostar HL Tau
- 2016ApJ...820L..39N (2016): First Connection between Cold Gas in Emission and Absorption: CO Emission from a Galaxy-Quasar Pair
- 2016ApJ...820L..40A (2016): Ringed Substructure and a Gap at 1 au in the Nearest Protoplanetary Disk
- 2016ApJ...821..112K (2016): SMA Observations of the Extended <SUP>12</SUP>CO(J = 6-5) Emission in the Starburst Galaxy NGC 253
- 2016ApJ...821L...3T (2016): An Ordered Bipolar Outflow from a Massive Early-stage Core
- 2016ApJ...821L...8S (2016): Isotopic Ratios of Carbon and Oxygen in Titan’s CO using ALMA
- 2016ApJ...821L..16C (2016): The VLA View of the HL Tau Disk: Disk Mass, Grain Evolution, and Early Planet Formation
- 2016ApJ...822...80S (2016): The Redshift Distribution of Dusty Star-forming Galaxies from the SPT Survey
- 2016ApJ...822L..10I (2016): ALMA 0.1-0.2 arcsec Resolution Imaging of the NGC 1068 Nucleus: Compact Dense Molecular Gas Emission at the Putative AGN Location
- 2016ApJ...823...26E (2016): High Star Formation Rates in Turbulent Atomic-dominated Gas in the Interacting Galaxies IC 2163 and NGC 2207
- 2016ApJ...823...51B (2016): Toward Precision Black Hole Masses with ALMA: NGC 1332 as a Case Study in Molecular Disk Dynamics
- 2016ApJ...823...68S (2016): Gas Dynamics and Outflow in the Barred Starburst Galaxy NGC 1808 Revealed with ALMA
- 2016ApJ...823...91S (2016): The Radial Distribution of H<SUB>2</SUB> and CO in TW Hya as Revealed by Resolved ALMA Observations of CO Isotopologues
- 2016ApJ...823..160D (2016): An ALMA Search for Substructure, Fragmentation, and Hidden Protostars in Starless Cores in Chamaeleon I
- 2016ApJ...823L..10W (2016): First Detection of Gas-phase Methanol in a Protoplanetary Disk
- 2016ApJ...823L..18H (2016): Evidence for a CO Desorption Front in the Outer AS 209 Disk
- 2016ApJ...823L..27H (2016): An Extremely High Velocity Molecular Jet Surrounded by an Ionized Cavity in the Protostellar Source Serpens SMM1
- 2016ApJ...824...88O (2016): Infalling-Rotating Motion and Associated Chemical Change in the Envelope of IRAS 16293-2422 Source A Studied with ALMA
- 2016ApJ...824..132N (2016): ALMA Science Verification Data: Millimeter Continuum Polarimetry of the Bright Radio Quasar 3C 286
- 2016ApJ...825...44I (2016): ALMA Investigation of Vibrationally Excited HCN/HCO<SUP>+</SUP>/HNC Emission Lines in the AGN-Hosting Ultraluminous Infrared Galaxy IRAS 20…
- 2016ApJ...825...79S (2016): Survey Observations of a Possible Glycine Precursor, Methanimine (CH2NH)
- 2016ApJ...826...16E (2016): Protoplanetary Disks in the Orion OMC1 Region Imaged with ALMA
- 2016ApJ...826...26T (2016): Revealing a Detailed Mass Distribution of a High-density Core MC27/L1521F in Taurus with ALMA
- 2016ApJ...826..112S (2016): ALMA Imaging and Gravitational Lens Models of South Pole Telescope—Selected Dusty, Star-Forming Galaxies at High Redshifts
- 2016ApJ...827...34O (2016): Witnessing the Birth of the Red Sequence: ALMA High-resolution Imaging of [C II] and Dust in Two Interacting Ultra-red Starbursts at z = 4.…
- 2016ApJ...827...68P (2016): Submillimeter H<SUB>2</SUB>O Megamasers in NGC 4945 and the Circinus Galaxy
- 2016ApJ...827...81I (2016): Do Circumnuclear Dense Gas Disks Drive Mass Accretion onto Supermassive Black Holes?
- 2016ApJ...827..133L (2016): Star Formation and Feedback: A Molecular Outflow-Prestellar Core Interaction in L1689N
- 2016ApJ...827L..32B (2016): Sub-kiloparsec ALMA Imaging of Compact Star-forming Galaxies at z ~ 2.5: Revealing the Formation of Dense Galactic Cores in the Progenitors…
- 2016ApJ...828...25L (2016): Debris Disks in the Scorpius-Centaurus OB Association Resolved by ALMA
- 2016ApJ...828...46A (2016): ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses
- 2016ApJ...828..100F (2016): Outflow Detection in a 70 μm Dark High-Mass Core
- 2016ApJ...829....6W (2016): ALMA Observations of HD 141569’s Circumstellar Disk
- 2016ApJ...829L..10I (2016): Clumpy and Extended Starbursts in the Brightest Unlensed Submillimeter Galaxies
- 2016ApJ...829L..11P (2016): Tracing the Reionization Epoch with ALMA: [C II] Emission in z ∼ 7 Galaxies
- 2016ApJ...829L..23B (2016): ALMA-SZ Detection of a Galaxy Cluster Merger Shock at Half the Age of the Universe
- 2016ApJ...829L..35T (2016): A Gap with a Deficit of Large Grains in the Protoplanetary Disk around TW Hya
- 2016ApJ...830L..37I (2016): Discovery of a Hot Corino in the Bok Globule B335
- 2016ApJ...831..101B (2016): Hydrocarbon Emission Rings in Protoplanetary Disks Induced by Dust Evolution
- 2016ApJ...831..161K (2016): Ocular Shock Front in the Colliding Galaxy IC 2163
- 2016ApJ...831L..12K (2016): Submillimeter Polarization Observation of the Protoplanetary Disk around HD 142527
- 2016ApJ...832..142Z (2016): The Molecular Wind in the Nearest Seyfert Galaxy Circinus Revealed by ALMA
- 2016ApJ...832..148V (2016): Molecular Gas Along a Bright Hα Filament in 2A 0335+096 Revealed by ALMA
- 2016ApJ...832..158Z (2016): ALMA Cycle 1 Observations of the HH46/47 Molecular Outflow: Structure, Entrainment, and Core Impact
- 2016ApJ...832..178V (2016): Vortices and Spirals in the HD135344B Transition Disk
- 2016ApJ...832..204Y (2016): Stacking Spectra in Protoplanetary Disks: Detecting Intensity Profiles from Hidden Molecular Lines in HD 163296
- 2016ApJ...833...12R (2016): VLA and ALMA Imaging of Intense Galaxy-wide Star Formation in z ∼ 2 Galaxies
- 2016ApJ...833...41Z (2016): High-resolution Observations of Molecular Lines in Arp 220: Kinematics, Morphology, and Limits on the Applicability of the Ammonia Thermome…
- 2016ApJ...833...67W (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Survey Description
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833..112S (2016): Gas Fraction and Depletion Time of Massive Star-forming Galaxies at z ~ 3.2: No Change in Global Star Formation Process out to z &gt; 3
- 2016ApJ...833..195W (2016): The SXDF-ALMA 2-arcmin<SUP>2</SUP> Deep Survey: Stacking Rest-frame Near-infrared Selected Objects
- 2016ApJ...833..209O (2016): Dense Core Properties in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA
- 2016ApJ...833..238H (2016): ALMA Band 8 Continuum Emission from Orion Source I
- 2016MNRAS.457.2936I (2016): ALMA imprint of intergalactic dark structures in the gravitational lens SDP.81
- 2016MNRAS.457L.122H (2016): ALMA resolves extended star formation in high-z AGN host galaxies
- 2016MNRAS.458.3134R (2016): ALMA observations of cold molecular gas filaments trailing rising radio bubbles in PKS 0745-191
- 2016MNRAS.458L..29C (2016): A ring-like concentration of mm-sized particles in Sz 91
- 2016MNRAS.459.3629I (2016): ALMA observations of the submillimetre hydrogen recombination line from the type 2 active nucleus of NGC 1068
- 2016MNRAS.459.4518H (2016): The detection of dust around NN Ser
- 2016MNRAS.460..627K (2016): The winds from HL Tau
- 2016MNRAS.460.2933M (2016): Exocometary gas in the HD 181327 debris ring
- 2016MNRAS.460L..10B (2016): Resolving the planetesimal belt of HR 8799 with ALMA
- 2016MNRAS.461.2944A (2016): ALMA observations of a z ≈ 3.1 protocluster: star formation from active galactic nuclei and Lyman-alpha blobs in an overdense environment
- 2016MNRAS.462.1192L (2016): Estimating sizes of faint, distant galaxies in the submillimetre regime
- 2016MNRAS.462L.101A (2016): Dipper discs not inclined towards edge-on orbits
- 2016MNRAS.463..252B (2016): Free-free and H42α emission from the dusty starburst within NGC 4945 as observed by ALMA
- 2016NatAs...1E...3P (2016): Large molecular gas reservoirs in ancestors of Milky Way-mass galaxies nine billion years ago
- 2016Natur.535..258C (2016): Imaging the water snow-line during a protostellar outburst
- 2016Natur.540..406B (2016): Resolved images of a protostellar outflow driven by an extended disk wind
- 2016PASJ...68...88K (2016): The Sunyaev-Zel'dovich effect at 5″: RX J1347.5-1145 imaged by ALMA
- 2016Sci...353.1519P (2016): Spiral density waves in a young protoplanetary disk
- 2017A&A...597A..27S (2017): ALMA high spatial resolution observations of the dense molecular region of NGC 6302
- 2017A&A...597A..32V (2017): Cavity and other radial substructures in the disk around HD 97048
- 2017A&A...597A..41G (2017): The ALMA Frontier Fields Survey. I. 1.1 mm continuum detections in Abell 2744, MACS J0416.1-2403 and MACS J1149.5+2223
- 2017A&A...597A..99W (2017): ALMA Compact Array observations of the Fried Egg nebula. Evidence for large-scale asymmetric mass-loss from the yellow hypergiant IRAS 1716…
- 2017A&A...597L...5B (2017): A second post-AGB nebula that contains gas in rotation and in expansion: ALMA maps of IW Carinae
- 2017A&A...599A.134S (2017): The ALMA Redshift 4 Survey (AR4S). I. The massive end of the z = 4 main sequence of galaxies
- 2017A&A...600A...8D (2017): ALMA observations of 4U 1728-34 and 4U 1820-30: first detection of neutron star X-ray binaries at 300 GHz
- 2017A&A...600A..72F (2017): ALMA unveils rings and gaps in the protoplanetary system <ASTROBJ>HD 169142</ASTROBJ>: signatures of two giant protoplanets
- 2017A&A...600A.141K (2017): Resolving the fragmentation of high line-mass filaments with ALMA: the integral shaped filament in Orion A
- 2017A&A...601L...3P (2017): First detection of the 448 GHz H<SUB>2</SUB>O transition in space
- 2017A&A...602A..11P (2017): ALMA reveals starburst-like interstellar medium conditions in a compact star-forming galaxy at z 2 using [CI] and CO
- 2017A&A...602A..19L (2017): A concordant scenario to explain FU Orionis from deep centimeter and millimeter interferometric observations
- 2017A&A...602A..42K (2017): Subarcsecond imaging of the water emission in Arp 220
- 2017A&A...602A..49H (2017): VALES. II. The physical conditions of interstellar gas in normal star-forming galaxies up to z = 0.2 revealed by ALMA
- 2017A&A...602A..54M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: The extent of the radio-emitting region revealed by 3 GHz imaging with the Ve…
- 2017A&A...602A..59C (2017): Chasing discs around O-type (proto)stars: Evidence from ALMA observations
- 2017A&A...602L...9M (2017): On the Kennicutt-Schmidt scaling law of submillimetre galaxies
- 2017A&A...602L..10O (2017): The inhomogeneous submillimeter atmosphere of Betelgeuse
- 2017A&A...603A..10B (2017): Fragmentation and disk formation in high-mass star formation: The ALMA view of G351.77-0.54 at 0.06'' resolution
- 2017A&A...603A..92V (2017): Magnetically aligned dust and SiO maser polarisation in the envelope of the red supergiant VY Canis Majoris
- 2017A&A...603L...2O (2017): First detection of methanol towards a post-AGB object, HD 101584
- 2017A&A...603L...6H (2017): Direct evidence of multiple reservoirs of volatile nitrogen in a protosolar nebula analogue
- 2017A&A...604A...2S (2017): PdBI U/LIRG Survey (PULS): Dense molecular gas in Arp 220 and NGC 6240
- 2017A&A...604A...6S (2017): The physical and chemical structure of Sagittarius B2. II. Continuum millimeter emission of Sgr B2(M) and Sgr B2(N) with ALMA
- 2017A&A...604A.115V (2017): The correct estimate of the probability of false detection of the matched filter in weak-signal detection problems . II. Further results wi…
- 2017A&A...604A.117C (2017): Planck's dusty GEMS. IV. Star formation and feedback in a maximum starburst at z = 3 seen at 60-pc resolution
- 2017A&A...604L...2F (2017): The complexity of Orion: an ALMA view. II. gGg'-ethylene glycol and acetic acid
- 2017A&A...605A..21C (2017): Increased H<SUB>2</SUB>CO production in the outer disk around HD 163296
- 2017A&A...605A..28D (2017): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. I. Large-scale kinematic structure…
- 2017A&A...605A..42C (2017): Extended ionised and clumpy gas in a normal galaxy at z = 7.1 revealed by ALMA
- 2017A&A...605A..78A (2017): Center-to-limb observations of the Sun with ALMA . Implications for solar atmospheric models
- 2017A&A...605A.121M (2017): Phase correction for ALMA. Investigating water vapour radiometer scaling: The long-baseline science verification data case study
- 2017A&A...606A..17M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution …
- 2017A&A...606A.125S (2017): DCO<SUP>+</SUP>, DCN, and N<SUB>2</SUB>D<SUP>+</SUP> reveal three different deuteration regimes in the disk around the Herbig Ae star HD 16…
- 2017A&A...607A..55V (2017): An 80 au cavity in the disk around HD 34282
- 2017A&A...607L...5Q (2017): Clues to NaCN formation
- 2017A&A...607L...6T (2017): ALMA discovery of a rotating SO/SO<SUB>2</SUB> flow in HH212. A possible MHD disk wind?
- 2017A&A...608A..22A (2017): Luminous, pc-scale CO 6-5 emission in the obscured nucleus of NGC 1377
- 2017A&A...608A..38O (2017): Properties of the molecular gas in the fast outflow in the Seyfert galaxy IC 5063
- 2017AJ....153..233F (2017): ALMA Observations of Asymmetric Molecular Gas Emission from a Protoplanetary Disk in the Orion Nebula
- 2017AJ....153..240A (2017): An ALMA Survey of Protoplanetary Disks in the σ Orionis Cluster
- 2017AJ....154..225S (2017): ALMA 1.3 mm Map of the HD 95086 System
- 2017ApJ...834....6S (2017): Merger-induced Shocks in the Nearby LIRG VV 114 through Methanol Observations with ALMA
- 2017ApJ...834..135T (2017): Bulge-forming Galaxies with an Extended Rotating Disk at z ~ 2
- 2017ApJ...834..178Y (2017): Signs of Early-stage Disk Growth Revealed with ALMA
- 2017ApJ...835...17M (2017): ALMA Measurements of Circumstellar Material in the GQ Lup System
- 2017ApJ...835...98U (2017): ALMA Deep Field in SSA22: Source Catalog and Number Counts
- 2017ApJ...835..108S (2017): Kinematic Structure of Molecular Gas around High-mass YSO, Papillon Nebula, in N159 East in the Large Magellanic Cloud: A New Perspective w…
- 2017ApJ...835..174S (2017): Spatially resolved CO SLED of the Luminous Merger Remnant NGC 1614 with ALMA
- 2017ApJ...835..278S (2017): Physical Properties of Molecular Clouds at 2 pc Resolution in the Low-metallicity Dwarf Galaxy NGC 6822 and the Milky Way
- 2017ApJ...835L..11T (2017): Grand-design Spiral Arms in a Young Forming Circumstellar Disk
- 2017ApJ...835L..13S (2017): ALMA Observations of the Water Fountain Pre-planetary Nebula IRAS 16342-3814: High-velocity Bipolar Jets and an Expanding Torus
- 2017ApJ...835L..35M (2017): New ALMA and Fermi/LAT Observations of the Large-scale Jet of PKS 0637-752 Strengthen the Case Against the IC/CMB Model
- 2017ApJ...836..130R (2017): Alma Observations of Massive Molecular Gas Filaments Encasing Radio Bubbles in the Phoenix Cluster
- 2017ApJ...836..201D (2017): The Sizes and Depletions of the Dust and Gas Cavities in the Transitional Disk J160421.7-213028
- 2017ApJ...836..223W (2017): An ALMA and MagAO Study of the Substellar Companion GQ Lup B*
- 2017ApJ...836L...2B (2017): ALMA [C II] 158 μm Detection of a Redshift 7 Lensed Galaxy behind RXJ1347.1-1145
- 2017ApJ...837...60B (2017): The ALMA View of the OMC1 Explosion in Orion
- 2017ApJ...837..174O (2017): L483: Warm Carbon-chain Chemistry Source Harboring Hot Corino Activity
- 2017ApJ...837L..29H (2017): An Extraordinary Outburst in the Massive Protostellar System NGC6334I-MM1: Quadrupling of the Millimeter Continuum
- 2017ApJ...838...97M (2017): Imaging a Central Ionized Component, a Narrow Ring, and the CO Snowline in the Multigapped Disk of HD 169142
- 2017ApJ...838..114K (2017): ALMA Observations of Starless Core Substructure in Ophiuchus
- 2017ApJ...838..146L (2017): ALMA Observations of the Interaction of a Radio Jet with Molecular Gas in Minkowski's Object
- 2017ApJ...839...43O (2017): H<SUB>2</SUB>CO Distribution and Formation in the TW HYA Disk
- 2017ApJ...839...58S (2017): The SCUBA-2 Cosmology Legacy Survey: Multi-wavelength Properties of ALMA-identified Submillimeter Galaxies in UKIDSS UDS
- 2017ApJ...839...86H (2017): Radial Surface Density Profiles of Gas and Dust in the Debris Disk around 49 Ceti
- 2017ApJ...839...99P (2017): A Multi-wavelength Analysis of Dust and Gas in the SR 24S Transition Disk
- 2017ApJ...839L..15G (2017): Discovery and Physical Characterization of a Large Scattered Disk Object at 92 au
- 2017ApJ...839L..24M (2017): On the Origin of the Spiral Morphology in the Elias 2-27 Circumstellar Disk
- 2017ApJ...840....8S (2017): Luminous Infrared Galaxies with the Submillimeter Array. V. Molecular Gas in Intermediate to Late-stage Mergers
- 2017ApJ...840...23L (2017): A Multi-ringed, Modestly Inclined Protoplanetary Disk around AA Tau
- 2017ApJ...840...60B (2017): A Close-up View of the Young Circumbinary Disk HD 142527
- 2017ApJ...840..101C (2017): Near-infrared MOSFIRE Spectra of Dusty Star-forming Galaxies at 0.2 &lt; z &lt; 4
- 2017ApJ...840L..11S (2017): Extreme CO Isotopic Abundances in the ULIRG IRAS 13120-5453: An Extremely Young Starburst or Top-heavy Initial Mass Function
- 2017ApJ...840L..12S (2017): WL 17: A Young Embedded Transition Disk
- 2017ApJ...841..110S (2017): The Coldest Place in the Universe: Probing the Ultra-cold Outflow and Dusty Disk in the Boomerang Nebula
- 2017ApJ...841..130A (2017): The Luminous Blue Variable RMC 127 as Seen with ALMA and ATCA
- 2017ApJ...841L..11B (2017): First Millimeter Detection of the Disk around a Young, Isolated, Planetary-mass Object
- 2017ApJ...841L..25T (2017): Rotating Starburst Cores in Massive Galaxies at z = 2.5
- 2017ApJ...842....8M (2017): A Complete ALMA Map of the Fomalhaut Debris Disk
- 2017ApJ...842...94T (2017): ALMA View of the Galactic Center Minispiral: Ionized Gas Flows around Sagittarius A<SUP>∗</SUP>
- 2017ApJ...842L...9H (2017): Unveiling the Role of the Magnetic Field at the Smallest Scales of Star Formation
- 2017ApJ...842L..15S (2017): ISM Properties of a Massive Dusty Star-forming Galaxy Discovered at z ∼ 7
- 2017ApJ...842L..16L (2017): ALMA [N II] 205 μm Imaging Spectroscopy of the Interacting Galaxy System BRI 1202-0725 at Redshift 4.7
- 2017ApJ...842L..21N (2017): ALMA Observations of Gas-rich Galaxies in z ∼ 1.6 Galaxy Clusters: Evidence for Higher Gas Fractions in High-density Environments
- 2017ApJ...842L..24A (2017): Very Deep inside the SN 1987A Core Ejecta: Molecular Structures Seen in 3D
- 2017ApJ...843...18V (2017): Quasar Feedback in the Ultraluminous Infrared Galaxy F11119+3257: Connecting the Accretion Disk Wind with the Large-scale Molecular Outflow
- 2017ApJ...843...27L (2017): Formation and Atmosphere of Complex Organic Molecules of the HH 212 Protostellar Disk
- 2017ApJ...843...83W (2017): ALMA Images of the Orion Hot Core at 349 GHz
- 2017ApJ...843..136E (2017): Disentangling the Circumnuclear Environs of Centaurus A. III. An Inner Molecular Ring, Nuclear Shocks, and the CO to Warm H<SUB>2</SUB> Int…
- 2017ApJ...843..150F (2017): A Three-dimensional View of Turbulence: Constraints on Turbulent Motions in the HD 163296 Protoplanetary Disk Using DCO<SUP>+</SUP>
- 2017ApJ...843L..35W (2017): ALMA Observations of the Gravitational Lens SDP.9
- 2017ApJ...844...99L (2017): An ALMA Survey of CO Isotopologue Emission from Protoplanetary Disks in Chamaeleon I
- 2017ApJ...844..123F (2017): The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters …
- 2017ApJ...845...58Z (2017): ALMA Maps of Dust and Warm Dense Gas Emission in the Starburst Galaxy IC 5179
- 2017ApJ...845..138S (2017): Gas Dynamics of a Luminous z = 6.13 Quasar ULAS J1319+0950 Revealed by ALMA High-resolution Observations
- 2017ApJ...845..154V (2017): Molecular Gas in Three z ∼ 7 Quasar Host Galaxies
- 2017ApJ...845..170B (2017): ALMA Observations of Circumnuclear Disks in Early-type Galaxies: <SUP>12</SUP>CO(2-1) and Continuum Properties
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...846L..14S (2017): Massive Quenched Galaxies at z ∼ 0.7 Retain Large Molecular Gas Reservoirs
- 2017ApJ...846L..26W (2017): An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C
- 2017ApJ...847...66O (2017): ALMA Observations of the Archetypal “Hot Core” That Is Not: Orion-KL
- 2017ApJ...847...92H (2017): ALMA Observations of Dust Polarization and Molecular Line Emission from the Class 0 Protostellar Source Serpens SMM1
- 2017ApJ...847..108W (2017): Discovery of Striking Difference of Molecular-emission-line Richness in the Potential Proto-binary System NGC 2264 CMM3
- 2017ApJ...848..101V (2017): A <SUP>13</SUP>CO Detection in a Brightest Cluster Galaxy
- 2017ApJ...849...56A (2017): ALMA Observations of the Protostar L1527 IRS: Probing Details of the Disk and the Envelope Structures
- 2017ApJ...849...90S (2017): Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations
- 2017ApJ...849..154S (2017): ALMA Pinpoints a Strong Overdensity of U/LIRGs in the Massive Cluster XCS J2215 at z = 1.46
- 2017ApJ...850...83F (2017): Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034…
- 2017ApJ...850L...2A (2017): ALMA Observations of SMM11 Reveal an Extremely Young Protostar in Serpens Main Cluster
- 2017ApJ...850L...6A (2017): ALMA Discovery of Dust Belts around Proxima Centauri
- 2017ApJ...850L..21K (2017): ALMA and GMRT Constraints on the Off-axis Gamma-Ray Burst 170817A from the Binary Neutron Star Merger GW170817
- 2017ApJ...850L..30Y (2017): ALMA Detection of Bipolar Outflows: Evidence for Low-mass Star Formation within 1 pc of Sgr A*
- 2017ApJ...851...18L (2017): SDSS-IV MaNGA-resolved Star Formation and Molecular Gas Properties of Green Valley Galaxies: A First Look with ALMA and MaNGA
- 2017ApJ...851...55S (2017): ALMA Reveals Transition of Polarization Pattern with Wavelength in HL Tau’s Disk
- 2017ApJ...851...83C (2017): Protoplanetary Disks in ρ Ophiuchus as Seen from ALMA
- 2017ApJ...851...98T (2017): No Sign of Strong Molecular Gas Outflow in an Infrared-bright Dust-obscured Galaxy with Strong Ionized-gas Outflow
- 2017ApJ...851..126V (2017): Galactic-scale Feedback Observed in the 3C 298 Quasar Host Galaxy
- 2017ApJ...851..132C (2017): The Architecture of the GW Ori Young Triple-star System and Its Disk: Dynamical Masses, Mutual Inclinations, and Recurrent Eclipses
- 2017ApJ...851..145M (2017): ALMA Reveals Metals yet No Dust within Multiple Components in CR7
- 2017ApJ...851L..23C (2017): ALMA Observations of Elias 2-24: A Protoplanetary Disk with Multiple Gaps in the Ophiuchus Molecular Cloud
- 2017MNRAS.464L..31H (2017): Unveiling the early-stage anatomy of a protocluster hub with ALMA
- 2017MNRAS.464L..75F (2017): ALMA observations of the supergiant B[e] star Wd1-9
- 2017MNRAS.465..834Z (2017): The ALMA early science view of FUor/EXor objects - I. Through the looking-glass of V2775 Ori
- 2017MNRAS.465.2595M (2017): ALMA observations of the η Corvi debris disc: inward scattering of CO-rich exocomets by a chain of 3-30 M<SUB>⊕</SUB> planets?
- 2017MNRAS.465.4390B (2017): The discovery of gas-rich, dusty starbursts in luminous reddened quasars at z ∼ 2.5 with ALMA
- 2017MNRAS.466...49J (2017): Optical depth estimates and effective critical densities of dense gas tracers in the inner parts of nearby galaxy discs
- 2017MNRAS.466..138K (2017): A merger in the dusty, z = 7.5 galaxy A1689-zD1?
- 2017MNRAS.466..861D (2017): A deep ALMA image of the Hubble Ultra Deep Field
- 2017MNRAS.466.4201W (2017): 1.3-mm ALMA observations of the Fomalhaut debris system
- 2017MNRAS.467L.120M (2017): The ALMA view of W33A: a spiral filament feeding the candidate disc in MM1-Main
- 2017MNRAS.468.3266R (2017): The ALMA early science view of FUor/EXor objects - III. The slow and wide outflow of V883 Ori
- 2017MNRAS.468.3468G (2017): Molecular gas on large circumgalactic scales at z = 3.47
- 2017MNRAS.468L..87C (2017): New ALMA constraints on the star-forming interstellar medium at low metallicity: a 50 pc view of the blue compact dwarf galaxy SBS 0335-052
- 2017MNRAS.469.3347M (2017): ALMA spectral survey of Supernova 1987A - molecular inventory, chemistry, dynamics and explosive nucleosynthesis
- 2017MNRAS.469.3518M (2017): ALMA observations of the multiplanet system 61 Vir: what lies outside super-Earth systems?
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2017MNRAS.472.1239B (2017): Tests of star formation metrics in the low-metallicity galaxy NGC 5253 using ALMA observations of H30α line emission
- 2017NatAs...1..709O (2017): Millimetre-wave emission from an intermediate-mass black hole candidate in the Milky Way
- 2017NatAs...1E..60K (2017): The large-scale nebular pattern of a superwind binary in an eccentric orbit
- 2017NatAs...1E.130Z (2017): Mass inventory of the giant-planet formation zone in a solar nebula analogue
- 2017NatAs...1E.146H (2017): Disk-driven rotating bipolar outflow in Orion Source I
- 2017NatAs...1E.152L (2017): A rotating protostellar jet launched from the innermost disk of HH 212
- 2017NatAs...1E.172L (2017): Formation of wide binaries by turbulent fragmentation
- 2017Natur.545..457D (2017): Rapidly star-forming galaxies adjacent to quasars at redshifts exceeding 6
- 2017Natur.548..430F (2017): Large turbulent reservoirs of cold molecular gas around high-redshift starburst galaxies
- 2017PASJ...69...18T (2017): A statistical study of giant molecular clouds traced by <SUP>13</SUP>CO, C<SUP>18</SUP>O, CS, and CH<SUB>3</SUB>OH in the disk of NGC 1068 …
- 2017PASP..129c5004M (2017): ALMA Long Baseline Campaigns: Phase Characteristics of Atmosphere at Long Baselines in the Millimeter and Submillimeter Wavelengths
- 2017Sci...355.1285N (2017): [C II] 158-μm emission from the host galaxies of damped Lyman-alpha systems
- 2017SciA....3E2935L (2017): First detection of equatorial dark dust lane in a protostellar disk at submillimeter wavelength
- 2018A&A...609A..47P (2018): Direct mapping of the temperature and velocity gradients in discs. Imaging the vertical CO snow line around IM Lupi
- 2018A&A...609A..75F (2018): Hidden molecular outflow in the LIRG Zw 049.057
- 2018A&A...610A..24F (2018): ALMA continuum observations of the protoplanetary disk AS 209. Evidence of multiple gaps opened by a single planet
- 2018A&A...610A..53M (2018): Chandra and ALMA observations of the nuclear activity in two strongly lensed star-forming galaxies
- 2018A&A...612A.103C (2018): Radio outburst from a massive (proto)star. When accretion turns into ejection
- 2018A&A...613A..34P (2018): ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy
- 2018A&A...614A..42M (2018): ALMA observations of AGN fuelling. The case of PKS B1718-649
- 2018A&A...614A..58B (2018): High-resolution observations of IRAS 08544-4431. Detection of a disk orbiting a post-AGB star and of a slow disk wind
- 2018A&A...614A.106C (2018): Probing midplane CO abundance and gas temperature with DCO<SUP>+</SUP> in the protoplanetary disk around HD 169142
- 2018A&A...615A...9P (2018): Distribution of Serpens South protostars revealed with ALMA
- 2018A&A...615A..28D (2018): ALMA spectral line and imaging survey of a low and a high mass-loss rate AGB star between 335 and 362 GHz
- 2018A&A...615A..83V (2018): Unveiling the physical conditions of the youngest disks. A warm embedded disk in L1527
- 2018A&A...615A.141B (2018): Accelerating infall and rotational spin-up in the hot molecular core G31.41+0.31
- 2018A&A...615L..10M (2018): Unlocking the secrets of the midplane gas and dust distribution in the young hybrid disc HD 141569
- 2018A&A...615L..14M (2018): Revised SED of the triple protostellar system VLA 1623-2417
- 2018A&A...616A..23D (2018): The evolving jet spectrum of the neutron star X-ray binary Aql X-1 in transitional states during its 2016 outburst
- 2018A&A...616A..56A (2018): Magnetic field in a young circumbinary disk
- 2018A&A...616A..88V (2018): V1094 Scorpii: A rare giant multi-ringed disk around a T Tauri star
- 2018A&A...616A.100Y (2018): Stellar masses and disk properties of Lupus young stellar objects traced by velocity-aligned stacked ALMA <SUP>13</SUP>CO and C<SUP>18</SUP…
- 2018A&A...616L...3B (2018): High-resolution observations of the symbiotic system R Aqr. Direct imaging of the gravitational effects of the secondary on the stellar wind
- 2018A&A...616L..10F (2018): ALMA observations of RCW 120 Fragmentation at 0.01 pc scale&amp;star
- 2018A&A...617A..23B (2018): Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN
- 2018A&A...617A..28S (2018): Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case
- 2018A&A...617A..82B (2018): The WISSH quasars project. V. ALMA reveals the assembly of a giant galaxy around a z = 4.4 hyper-luminous QSO
- 2018A&A...617A.137F (2018): An ALMA 3 mm continuum census of Westerlund 1
- 2018A&A...618A..85S (2018): Near infrared spectroscopy and star-formation histories of 3 ≤ z ≤ 4 quiescent galaxies
- 2018A&A...618A.120L (2018): The HH30 edge-on T Tauri star. A rotating and precessing monopolar outflow scrutinized by ALMA
- 2018A&A...618L...5N (2018): Detection of a high-mass prestellar core candidate in W43-MM1
- 2018A&A...619A..39F (2018): The dense molecular gas in the z ∼ 6 QSO SDSS J231038.88+185519.7 resolved by ALMA
- 2018A&A...619A..40M (2018): The radio jets of SS 433 at millimetre wavelengths
- 2018A&A...619A.161C (2018): Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk
- 2018A&A...620A..75K (2018): High-resolution observations of gas and dust around Mira using ALMA and SPHERE/ZIMPOL
- 2018A&A...620A.115B (2018): Dense-gas tracers and carbon isotopes in five 2.5 &lt; z &lt; 4 lensed dusty star-forming galaxies from the SPT SMG sample
- 2018A&A...620A.119D (2018): X-shooter and ALMA spectroscopy of GRB 161023A. A study of metals and molecules in the line of sight towards a luminous GRB
- 2018A&A...620A.152F (2018): GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies
- 2018AJ....155...47A (2018): Optical and Radio Observations of the T Tauri Binary KH 15D (V582 Mon): Stellar Properties, Disk Mass Limit, and Discovery of a CO Outflow
- 2018AJ....156..164B (2018): Medium-sized Satellites of Large Kuiper Belt Objects
- 2018AJ....156..239Z (2018): ALMA Reveals a Collision between Protostellar Outflows in BHR 71
- 2018AJ....156..270S (2018): The Albedos, Sizes, Colors, and Satellites of Dwarf Planets Compared with Newly Measured Dwarf Planet 2013 FY27
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853...24U (2018): ALMA 26 arcmin<SUP>2</SUP> Survey of GOODS-S at One-millimeter (ASAGAO): X-Ray AGN Properties of Millimeter-selected Galaxies
- 2018ApJ...853..147M (2018): Molecular Reconnaissance of the β Pictoris Gas Disk with the SMA: A Low HCN/(CO+CO<SUB>2</SUB>) Outgassing Ratio and Predictions for Future…
- 2018ApJ...853..160C (2018): The Core Mass Function in the Massive Protocluster G286.21+0.17 Revealed by ALMA
- 2018ApJ...853..171G (2018): Distributed Star Formation throughout the Galactic Center Cloud Sgr B2
- 2018ApJ...853..195W (2018): Herschel and ALMA Observations of Massive SZE-selected Clusters
- 2018ApJ...854...56L (2018): ALMA Dust Polarization Observations of Two Young Edge-on Protostellar Disks
- 2018ApJ...854...83T (2018): Optical, Near-IR, and Sub-mm IFU Observations of the Nearby Dual Active Galactic Nuclei MRK 463
- 2018ApJ...854...97D (2018): An ALMA [C II] Survey of 27 Quasars at z &gt; 5.94
- 2018ApJ...854..130W (2018): The Orbit of the Companion to HD 100453A: Binary-driven Spiral Arms in a Protoplanetary Disk
- 2018ApJ...854..177V (2018): New Insights into the Nature of Transition Disks from a Complete Disk Survey of the Lupus Star-forming Region
- 2018ApJ...854L...4R (2018): Cospatial Star Formation and Supermassive Black Hole Growth in z ∼ 3 Galaxies: Evidence for In Situ Co-evolution
- 2018ApJ...854L...7C (2018): ALMA Detection of Extended [C II] Emission in Himiko at z = 6.6
- 2018ApJ...855...24P (2018): Thermal Jeans Fragmentation within ∼1000 au in OMC-1S
- 2018ApJ...855...92C (2018): ALMA’s Polarized View of 10 Protostars in the Perseus Molecular Cloud
- 2018ApJ...855L...2M (2018): Detection of a Millimeter Flare from Proxima Centauri
- 2018ApJ...855L..25K (2018): Core Emergence in a Massive Infrared Dark Cloud: A Comparison between Mid-IR Extinction and 1.3 mm Emission
- 2018ApJ...856...14L (2018): A 100 au Wide Bipolar Rotating Shell Emanating from the HH 212 Protostellar Disk: A Disk Wind?
- 2018ApJ...856...72O (2018): An Extreme Protocluster of Luminous Dusty Starbursts in the Early Universe
- 2018ApJ...856...97S (2018): Dense Molecular Gas in the Starburst Nucleus of NGC 1808
- 2018ApJ...856..117F (2018): Turbulence in the TW Hya Disk
- 2018ApJ...856..118H (2018): Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46
- 2018ApJ...856..147O (2018): Gravitationally Unstable Condensations Revealed by ALMA in the TUKH122 Prestellar Core in the Orion A Cloud
- 2018ApJ...856L..12N (2018): Molecular Emission from a Galaxy Associated with a z ∼ 2.2 Damped Lyα Absorber
- 2018ApJ...857...18S (2018): Multiple Gaps in the Disk of the Class I Protostar GY 91
- 2018ApJ...857...19F (2018): The ALMA View of GMCs in NGC 300: Physical Properties and Scaling Relations at 10 pc Resolution
- 2018ApJ...857...35S (2018): ALMA Observations of the IRDC Clump G34.43+00.24 MM3: Complex Organic and Deuterated Molecules
- 2018ApJ...858...90G (2018): Dense Gas, Dynamical Equilibrium Pressure, and Star Formation in Nearby Star-forming Galaxies
- 2018ApJ...859...12G (2018): The Dust and [C II] Morphologies of Redshift ∼4.5 Sub-millimeter Galaxies at ∼200 pc Resolution: The Absence of Large Clumps in the Interst…
- 2018ApJ...859...21A (2018): ALMA Survey of Lupus Protoplanetary Disks. II. Gas Disk Radii
- 2018ApJ...859...32P (2018): Homogeneous Analysis of the Dust Morphology of Transition Disks Observed with ALMA: Investigating Dust Trapping and the Origin of the Cavit…
- 2018ApJ...859...35G (2018): The Dual Role of Starbursts and Active Galactic Nuclei in Driving Extreme Molecular Outflows
- 2018ApJ...859..111H (2018): The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System
- 2018ApJ...859..131L (2018): The Distribution and Excitation of CH<SUB>3</SUB>CN in a Solar Nebula Analog
- 2018ApJ...859..165S (2018): Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. I. VLA 1623
- 2018ApJ...859L..15C (2018): Interferometric Imaging of Titan’s HC<SUB>3</SUB>N, H<SUP>13</SUP>CCCN, and HCCC<SUP>15</SUP>N
- 2018ApJ...860....7R (2018): A Cavity of Large Grains in the Disk around the Group II Herbig Ae/Be Star HD 142666
- 2018ApJ...860....9M (2018): Detection of an Optical/UV Jet/Counterjet and Multiple Spectral Components in M84
- 2018ApJ...860...77E (2018): Protoplanetary Disk Properties in the Orion Nebula Cluster: Initial Results from Deep, High-resolution ALMA Observations
- 2018ApJ...860...82H (2018): ALMA Observations of Polarization from Dust Scattering in the IM Lup Protoplanetary Disk
- 2018ApJ...860...87F (2018): The Discovery of a New Massive Molecular Gas Component Associated with the Submillimeter Galaxy SMM J02399-0136
- 2018ApJ...860..103S (2018): Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey
- 2018ApJ...860..119G (2018): A Keplerian Disk around Orion SrCI, a ∼ 15 M <SUB>☉</SUB> YSO
- 2018ApJ...860..124D (2018): The Eccentric Cavity, Triple Rings, Two-armed Spirals, and Double Clumps of the MWC 758 Disk
- 2018ApJ...860..161S (2018): An ALMA Survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS Field: Number Counts of Submillimeter Galaxies
- 2018ApJ...860L..14K (2018): Discovery of a Molecular Collision Front in Interacting Galaxies NGC 4567/4568 with ALMA
- 2018ApJ...861....7F (2018): ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exp…
- 2018ApJ...861...43P (2018): Hidden in Plain Sight: A Massive, Dusty Starburst in a Galaxy Protocluster at z = 5.7 in the COSMOS Field
- 2018ApJ...861...72C (2018): ALMA Resolves C I Emission from the β Pictoris Debris Disk
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...861..123F (2018): Why Post-starburst Galaxies Are Now Quiescent
- 2018ApJ...862....8T (2018): Warm CO Gas Generated by Possible Turbulent Shocks in a Low-mass Star-forming Dense Core in Taurus
- 2018ApJ...862L...2F (2018): First Detection of the Simplest Organic Acid in a Protoplanetary Disk
- 2018ApJ...863...19A (2018): The Distinct Evolutionary Nature of Two Class 0 Protostars in Serpens Main SMM4
- 2018ApJ...863..129S (2018): Spatially Resolved Dense Molecular Gas Excitation in the Nearby LIRG VV 114
- 2018ApJ...863..143C (2018): ALMA [C I]<SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Observations of NGC 6240: A Puzzling Molecular Outflow, and the Role of O…
- 2018ApJ...863..193V (2018): Molecular Gas Filaments and Star-forming Knots Beneath an X-Ray Cavity in RXC J1504-0248
- 2018ApJ...863L..35M (2018): First Results of an ALMA Band 10 Spectral Line Survey of NGC 6334I: Detections of Glycolaldehyde (HC(O)CH<SUB>2</SUB>OH) and a New Compact …
- 2018ApJ...864...38L (2018): CO (7-6), [C I] 370 μm, and [N II] 205 μm Line Emission of the QSO BRI 1335-0417 at Redshift 4.407
- 2018ApJ...864...81O (2018): Two Different Grain Size Distributions within the Protoplanetary Disk around HD 142527 Revealed by ALMA Polarization Observation
- 2018ApJ...864..133T (2018): Temperature, Mass, and Turbulence: A Spatially Resolved Multiband Non-LTE Analysis of CS in TW Hya
- 2018ApJ...864..170G (2018): H<SUB>2</SUB>CO Ortho-to-para Ratio in the Protoplanetary Disk HD 163296
- 2018ApJ...864..174A (2018): The 30 Year Search for the Compact Object in SN 1987A
- 2018ApJ...864L..11X (2018): Flat Rotation Curves Found in Merging Dusty Starbursts at z = 2.3 through Tilted-ring Modeling
- 2018ApJ...864L..25O (2018): The Co-evolution of Disks and Stars in Embedded Stages: The Case of the Very-low-mass Protostar IRAS 15398-3359
- 2018ApJ...865...13T (2018): A Galaxy-scale Fountain of Cold Molecular Gas Pumped by a Black Hole
- 2018ApJ...865...37M (2018): Multiple Rings in the Transitional Disk of GM Aurigae Revealed by VLA and ALMA
- 2018ApJ...866..117C (2018): ALMA Observation of NGC 5135: The Circumnuclear CO (6-5) and Dust Continuum Emission at 45 pc Resolution
- 2018ApJ...866..141K (2018): Extremely Dense Cores Associated with Chandra Sources in Ophiuchus A: Forming Brown Dwarfs Unveiled?
- 2018ApJ...866L...6C (2018): High-resolution Millimeter Imaging of the CI Tau Protoplanetary Disk: A Massive Ensemble of Protoplanets from 0.1 to 100 au
- 2018ApJ...866L..12G (2018): A Magnified View of Circumnuclear Star Formation and Feedback around an Active Galactic Nucleus at z = 2.6
- 2018ApJ...867....7S (2018): Molecular Clouds Associated with the Type Ia SNR N103B in the Large Magellanic Cloud
- 2018ApJ...867...48I (2018): Circumnuclear Multiphase Gas in the Circinus Galaxy. II. The Molecular and Atomic Obscuring Structures Revealed with ALMA
- 2018ApJ...867..140L (2018): Resolving Star Formation on Subkiloparsec Scales in the High-redshift Galaxy SDP.11 Using Gravitational Lensing
- 2018ApJ...867..153C (2018): No Evidence for Millimeter Continuum Source Overdensities in the Environments of z ≳ 6 Quasars
- 2018ApJ...867..166S (2018): Internal Structures of Molecular Clouds in the LMC Revealed by ALMA
- 2018ApJ...867L..25B (2018): SS433's Jet Trace from ALMA Imaging and Global Jet Watch Spectroscopy: Evidence for Post-launch Particle Acceleration
- 2018ApJ...868...80C (2018): The Physical and Chemical Properties of the ρ Ophiuchi A Dense Core
- 2018ApJ...868...95M (2018): ALMA Observations of HCN and HCO<SUP>+</SUP> Outflows in the Merging Galaxy NGC 3256
- 2018ApJ...868..113T (2018): Evidence for a Vertical Dependence on the Pressure Structure in AS 209
- 2018ApJ...868L...3M (2018): ALMA Reveals a Misaligned Inner Gas Disk inside the Large Cavity of a Transitional Disk
- 2018ApJ...868L...5K (2018): A Spatially Resolved au-scale Inner Disk around DM Tau
- 2018ApJ...868L..38G (2018): Do Spectroscopic Dense Gas Fractions Track Molecular Cloud Surface Densities?
- 2018ApJ...869...17L (2018): Gaps and Rings in an ALMA Survey of Disks in the Taurus Star-forming Region
- 2018ApJ...869...59W (2018): Physical and Chemical Conditions of the Protostellar Envelope and the Protoplanetary Disk in HL Tau
- 2018ApJ...869...71Z (2018): Constraining the Volume Density of Dusty Star-forming Galaxies through the First 3 mm Number Counts from ALMA
- 2018ApJ...869...75M (2018): ALMA Detection of Extended Millimeter Halos in the HD 32297 and HD 61005 Debris Disks
- 2018ApJ...869..114I (2018): Detection of Coronal Magnetic Activity in nearby Active Supermassive Black Holes
- 2018ApJ...869..126L (2018): Forming Super Star Clusters in the Central Starburst of NGC 253
- 2018ApJ...869..158F (2018): ALMA Detections of the Youngest Protostars in Ophiuchus
- 2018ApJ...869L..41A (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). I. Motivation, Sample, Calibration, and Overview
- 2018ApJ...869L..43H (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). III. Spiral Structures in the Millimeter Continuum of the Elias 27, IM …
- 2018ApJ...869L..44K (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). IV. Characterizing Substructures and Interactions in Disks around Multi…
- 2018ApJ...869L..46D (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). VI. Dust Trapping in Thin-ringed Protoplanetary Disks
- 2018ApJ...869L..48G (2018): The Disk Substructures at High Angular Resolution Program (DSHARP). VIII. The Rich Ringed Substructures in the AS 209 Disk
- 2018ApJ...869L..50P (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). X. Multiple Rings, a Misaligned Inner Disk, and a Bright Arc in the Dis…
- 2018Icar..307..380T (2018): Spatial variations in Titan's atmospheric temperature: ALMA and Cassini comparisons from 2012 to 2015
- 2018MNRAS.473.1909G (2018): ALMA suggests outflows in z ∼ 5.5 galaxies
- 2018MNRAS.473.3818D (2018): WISDOM Project - III. Molecular gas measurement of the supermassive black hole mass in the barred lenticular galaxy NGC4429
- 2018MNRAS.474.3640M (2018): CO excitation in the Seyfert galaxy NGC 34: stars, shock or AGN driven?
- 2018MNRAS.474.4039M (2018): ALMA + VLT observations of a damped Lyman-α absorbing galaxy: massive, wide CO emission, gas-rich but with very low SFR
- 2018MNRAS.474.4347C (2018): The ALMA early science view of FUor/EXor objects - V. Continuum disc masses and sizes
- 2018MNRAS.474.4988S (2018): A disrupted molecular torus around Eta Carinae as seen in <SUP>12</SUP>CO with ALMA
- 2018MNRAS.475..448T (2018): Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study
- 2018MNRAS.475.1288S (2018): Identifying the subtle signatures of feedback from distant AGN using ALMA observations and the EAGLE hydrodynamical simulations
- 2018MNRAS.475.3004S (2018): ALMA observation of the disruption of molecular gas in M87
- 2018MNRAS.475.4924K (2018): ALMA observations of the narrow HR 4796A debris ring
- 2018MNRAS.475.4939A (2018): ALMA observations of lensed Herschel sources: testing the dark matter halo paradigm
- 2018MNRAS.475.5296D (2018): Rings and gaps in the disc around Elias 24 revealed by ALMA
- 2018MNRAS.475.5322S (2018): Deuterated formaldehyde in the low-mass protostar HH212
- 2018MNRAS.475L..52S (2018): Imaging the molecular outflows of the prototypical ULIRG NGC 6240 with ALMA
- 2018MNRAS.476..122V (2018): An ALMA view of star formation efficiency suppression in early-type galaxies after gas-rich minor mergers
- 2018MNRAS.476.3956T (2018): ALMA view of a massive spheroid progenitor: a compact rotating core of molecular gas in an AGN host at z = 2.226
- 2018MNRAS.476.5417S (2018): Unveiling the inner morphology and gas kinematics of NGC 5135 with ALMA
- 2018MNRAS.477.5104C (2018): An inner warp in the DoAr 44 T Tauri transition disc
- 2018MNRAS.477L..60E (2018): Giant galaxy growing from recycled gas: ALMA maps the circumgalactic molecular medium of the Spiderweb in [C I]
- 2018MNRAS.478.1170C (2018): Kiloparsec-scale gaseous clumps and star formation at z = 5-7
- 2018MNRAS.478.2505I (2018): Radiative transfer modelling of W33A MM1: 3D structure and dynamics of a complex massive star-forming region
- 2018MNRAS.478.3721S (2018): Deep ALMA photometry of distant X-ray AGN: improvements in star formation rate constraints, and AGN identification
- 2018MNRAS.479.2126F (2018): ALMA observations of a metal-rich damped Ly α absorber at z = 2.5832: evidence for strong galactic winds in a galaxy group
- 2018MNRAS.479.3879W (2018): An ALMA survey of CO in submillimetre galaxies: companions, triggering, and the environment in blended sources
- 2018MNRAS.479.3892F (2018): The complex jet- and bar-perturbed kinematics in NGC 3393 as revealed with ALMA and GEMINI-GMOS/IFU
- 2018MNRAS.479.5440L (2018): Neutral versus ionized gas kinematics at z ≃ 2.6: the AGN-host starburst galaxy PKS 0529-549
- 2018MNRAS.480.1006L (2018): The curious case of II Lup: a complex morphology revealed with SAM/NACO and ALMA
- 2018MNRAS.481.1631B (2018): Obscured star formation in bright z ≃ 7 Lyman-break galaxies
- 2018MNRAS.481.4931E (2018): ALMA reveals the aftermath of a white dwarf-brown dwarf merger in CK Vulpeculae
- 2018MNRAS.481L..40S (2018): A flux-ratio anomaly in the CO spectral line emission from gravitationally lensed quasar MG J0414+0534
- 2018NatCo...9.4636L (2018): Unveiling a magnetized jet from a low-mass protostar
- 2018Natur.556..469M (2018): A massive core for a cluster of galaxies at a redshift of 4.3
- 2018PASJ...70...36I (2018): Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). III. Star formation properties of the host galaxies at z ≳ 6 studied with AL…
- 2018PASJ...70...65U (2018): ALMA deep field in SSA22: Survey design and source catalog of a 20 arcmin<SUP>2</SUP> survey at 1.1 mm
- 2018PASJ...70...73H (2018): ALMA <SUP>12</SUP>CO (J = 1-0) imaging of the nearby galaxy M 83: Variations in the efficiency of star formation in giant molecular clouds
- 2018PASJ...70...85T (2018): ALMA view of the circumnuclear disk of the Galactic Center: tidally disrupted molecular clouds falling to the Galactic Center
- 2018PASJ...70L...1M (2018): ALMA [C I] observations toward the central region of Seyfert galaxy NGC 613
- 2018PASJ...70L...6K (2018): A high dust emissivity index β for a CO-faint galaxy in a filamentary Lyα nebula at z = 3.1
- 2018RAA....18...93Z (2018): Disks and outflows in the S255IR area of high mass star formation from ALMA observations
- 2018Sci...361.1016S (2018): Fast molecular outflow from a dusty star-forming galaxy in the early Universe
- 2018Sci...362.1034D (2018): The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6
- 2019A&A...621A..27F (2019): Massive galaxies on the road to quenching: ALMA observations of powerful high redshift radio galaxies
- 2019A&A...621A..83S (2019): Outflows in the inner kiloparsec of NGC 1566 as revealed by molecular (ALMA) and ionized gas (Gemini-GMOS/IFU) kinematics
- 2019A&A...621A.122B (2019): High-mass star formation at sub-50 au scales
- 2019A&A...622A..75L (2019): Ring structure in the MWC 480 disk revealed by ALMA
- 2019A&A...622A.206M (2019): A 10-M<SUB>☉</SUB> YSO with a Keplerian disk and a nonthermal radio jet
- 2019A&A...622L..14F (2019): Gas infall and possible circumstellar rotation in R Leonis
- 2019A&A...623A..29F (2019): Hidden or missing outflows in highly obscured galaxy nuclei?
- 2019A&A...623A..66B (2019): ALMA CO(2-1) observations in the XUV disk of M83
- 2019A&A...623A..79C (2019): ALMA observations of molecular tori around massive black holes
- 2019A&A...623A..96Y (2019): Signs of outflow feedback from a nearby young stellar object on the protostellar envelope around HL Tauri
- 2019A&A...623A.124C (2019): Upper limits on CH<SUB>3</SUB>OH in the HD 163296 protoplanetary disk. Evidence for a low gas-phase CH<SUB>3</SUB>OH-to-H<SUB>2</SUB>CO rat…
- 2019A&A...623A.150V (2019): The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN
- 2019A&A...623L...6P (2019): Organic molecules in the protoplanetary disk of DG Tauri revealed by ALMA
- 2019A&A...623L...8B (2019): Unveiling a cluster of protostellar disks around the massive protostar GGD 27 MM1
- 2019A&A...624A...7V (2019): Spatial segregation of dust grains in transition disks. SPHERE observations of 2MASS J16083070-3828268 and RXJ1852.3-3700
- 2019A&A...624A..33V (2019): ALMA study of the HD 100453 AB system and the tidal interaction of the companion with the disk
- 2019A&A...624A.125M (2019): Spatially resolved carbon and oxygen isotopic ratios in NGC 253 using optically thin tracers
- 2019A&A...624A.138Y (2019): CO, H<SUB>2</SUB>O, H<SUB>2</SUB>O<SUP>+</SUP> line and dust emission in a z = 3.63 strongly lensed starburst merger at sub-kiloparsec scal…
- 2019A&A...624L...7V (2019): Stringent limits on the magnetic field strength in the disc of TW Hya. ALMA observations of CN polarisation
- 2019A&A...625A.118K (2019): Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA
- 2019A&A...626L...2F (2019): High gas-to-dust size ratio indicating efficient radial drift in the mm-faint CX Tauri disk
- 2019A&A...627A.114K (2019): Massive dust clumps in the envelope of the red supergiant VY Canis Majoris
- 2019A&A...627A.147A (2019): The hidden heart of the luminous infrared galaxy IC 860. I. A molecular inflow feeding opaque, extreme nuclear activity
- 2019A&A...627L...6M (2019): Substructures in the Keplerian disc around the O-type (proto-)star G17.64+0.16
- 2019A&A...628A..10B (2019): Re-exploring Molecular Complexity with ALMA (ReMoCA): interstellar detection of urea
- 2019A&A...628A..23A (2019): Imaging the molecular interstellar medium in a gravitationally lensed star-forming galaxy at z = 5.7
- 2019A&A...628A..65A (2019): Nuclear molecular outflow in the Seyfert galaxy NGC 3227
- 2019A&A...628A..85V (2019): Disk masses in the Orion Molecular Cloud-2: distinguishing time and environment
- 2019A&A...628A..95M (2019): Observational constraints on dust disk sizes in tidally truncated protoplanetary disks in multiple systems in the Taurus region
- 2019A&A...628A.100D (2019): An ALMA+ACA measurement of the shock in the Bullet Cluster
- 2019A&A...628A.118B (2019): The gentle monster PDS 456. Kiloparsec-scale molecular outflow and its implications for QSO feedback
- 2019A&A...629A..75B (2019): First detections of H<SUP>13</SUP>CO<SUP>+</SUP> and HC<SUP>15</SUP>N in the disk around HD 97048. Evidence for a cold gas reservoir in the…
- 2019A&A...629A.128W (2019): Chlorine-bearing molecules in molecular absorbers at intermediate redshifts
- 2019A&A...629A.146V (2019): IRC + 10°216 mass loss properties through the study of λ3 mm emission. Large spatial scale distribution of SiO, SiS, and CS
- 2019A&A...630A..59B (2019): Widespread QSO-driven outflows in the early Universe
- 2019A&A...631A..25J (2019): ALMA observations of water deuteration: a physical diagnostic of the formation of protostars
- 2019A&A...631A..64B (2019): Kinematics around the B335 protostar down to au scales
- 2019A&A...631A..78S (2019): A spectral stacking analysis to search for faint outflow signatures in z ∼ 6 quasars
- 2019A&A...631A..91G (2019): Towards sub-kpc scale kinematics of molecular and ionized gas of star-forming galaxies at z ∼ 1
- 2019A&A...632A..19T (2019): Interferometric observations of warm deuterated methanol in the inner regions of low-mass protostars
- 2019A&A...632A..33A (2019): ALMA captures feeding and feedback from the active galactic nucleus in NGC 613
- 2019A&A...632A..38A (2019): A radio census of the massive stellar cluster Westerlund 1
- 2019A&A...632A..61G (2019): ALMA images the many faces of the <ASTROBJ>NGC 1068</ASTROBJ> torus and its surroundings
- 2019A&A...632A..66O (2019): ALMA observations of PKS 1549-79: a case of feeding and feedback in a young radio quasar
- 2019A&A...632A.101T (2019): Chemical and kinematic structure of extremely high-velocity molecular jets in the Serpens Main star-forming region
- 2019A&A...632L...7J (2019): Detection of a high-redshift molecular outflow in a primeval hyperstarburst galaxy
- 2019AJ....157..117M (2019): On the Ubiquity and Stellar Luminosity Dependence of Exocometary CO Gas: Detection around M Dwarf TWA 7
- 2019AJ....157..131B (2019): Kiloparsec-Scale Variations in the Star Formation Efficiency of Dense Gas: The Antennae Galaxies (NGC 4038/39)
- 2019AJ....157..219T (2019): Measurement of CH<SUB>3</SUB>D on Titan at Submillimeter Wavelengths
- 2019AJ....157..237R (2019): Constraints on a Putative Planet Sculpting the V4046 Sagittarii Circumbinary Disk
- 2019AJ....157..251T (2019): Neptune's Latitudinal Variations as Viewed with ALMA
- 2019AJ....158...15P (2019): Dust Unveils the Formation of a Mini-Neptune Planet in a Protoplanetary Ring
- 2019AJ....158...47M (2019): Thermal Emission from the Uranian Ring System
- 2019AJ....158...76C (2019): ALMA Spectral Imaging of Titan Contemporaneous with Cassini's Grand Finale
- 2019AJ....158..162F (2019): From Scattered-light to Millimeter Emission: A Comprehensive View of the Gigayear-old System of HD 202628 and its Eccentric Debris Ring
- 2019ApJ...870...39V (2019): ALMA Observations of the Molecular Gas in the Elliptical Galaxy NGC 3557
- 2019ApJ...870...59S (2019): ALMA, ATCA, and Spitzer Observations of the Luminous Extragalactic Supernova SN 1978K
- 2019ApJ...870...80L (2019): Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7
- 2019ApJ...871....5T (2019): The Flared Gas Structure of the Transitional Disk around Sz 91
- 2019ApJ...871...48P (2019): High-resolution ALMA Observations of HD 100546: Asymmetric Circumstellar Ring and Circumplanetary Disk Upper Limits
- 2019ApJ...871...85L (2019): The ISM Properties and Gas Kinematics of a Redshift 3 Massive Dusty Star-forming Galaxy
- 2019ApJ...871..100H (2019): ALMA Observations of the Protostellar Disk around the VeLLO IRAS 16253-2429
- 2019ApJ...871..107F (2019): Gas Density Perturbations Induced by One or More Forming Planets in the AS 209 Protoplanetary Disk as Seen with ALMA
- 2019ApJ...871..109P (2019): Multiband Optical and Near-Infrared Properties of Faint Submillimeter Galaxies with Serendipitous ALMA Detections
- 2019ApJ...871..112X (2019): ALMA Observations of the Spatial Distribution of Three C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> Isomers toward Sgr B2(N)
- 2019ApJ...871..170M (2019): Fire in the Heart: A Characterization of the High Kinetic Temperatures and Heating Sources in the Nucleus of NGC 253
- 2019ApJ...871..185L (2019): Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA
- 2019ApJ...872....2R (2019): ALMA Detection of Extreme Blueshifted Ionized Gas within 0.2 pc of Sgr A* from -480 to -300 km s<SUP>-1</SUP>
- 2019ApJ...872...69P (2019): AGN Torus Detectability at Submillimeter Wavelengths: What to Expect from ALMA Continuum Data
- 2019ApJ...872...92F (2019): The Planet Formation Potential around a 45 Myr Old Accreting M Dwarf
- 2019ApJ...872..121U (2019): Molecular Cloud Cores in the Galactic Center 50 km s<SUP>-1</SUP> Molecular Cloud
- 2019ApJ...872..158A (2019): Resolved Young Binary Systems and Their Disks
- 2019ApJ...872..196S (2019): Implications of a Hot Atmosphere/Corino from ALMA Observations toward NGC 1333 IRAS 4A1
- 2019ApJ...872..200H (2019): ALMA Observations of the Massive Molecular Outflow G331.512-0.103. II. Physical Properties, Kinematics, and Geometry Modeling
- 2019ApJ...873...50D (2019): Source Structure and Molecular Gas Properties from High-resolution CO Imaging of SPT-selected Dusty Star-forming Galaxies
- 2019ApJ...873...73Z (2019): An Ordered Envelope-Disk Transition in the Massive Protostellar Source G339.88-1.26
- 2019ApJ...874...27T (2019): Detection of the Far-infrared [O III] and Dust Emission in a Galaxy at Redshift 8.312: Early Metal Enrichment in the Heart of the Reionizat…
- 2019ApJ...874...53B (2019): Environmental Effect on the Interstellar Medium in Galaxies across the Cosmic Web at z = 0.73
- 2019ApJ...874...89C (2019): The Central 1000 au of a Pre-stellar Core Revealed with ALMA. I. 1.3 mm Continuum Observations
- 2019ApJ...874..104K (2019): Widespread Molecular Outflows in the Infrared Dark Cloud G28.37+0.07: Indications of Orthogonal Outflow-filament Alignment
- 2019ApJ...874L..30V (2019): 400 pc Imaging of a Massive Quasar Host Galaxy at a Redshift of 6.6
- 2019ApJ...875...24C (2019): Filamentary Accretion Flows in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA
- 2019ApJ...875...55W (2019): The MESAS Project: Long-wavelength Follow-up Observations of Sirius A
- 2019ApJ...875...87D (2019): The Mass of Stirring Bodies in the AU Mic Debris Disk Inferred from Resolved Vertical Structure
- 2019ApJ...875...96N (2019): Dust Continuum Emission and the Upper Limit Fluxes of Submillimeter Water Lines of the Protoplanetary Disk around HD 163296 Observed by ALMA
- 2019ApJ...875L...8R (2019): An Accreting Supermassive Black Hole Irradiating Molecular Gas in NGC 2110
- 2019ApJ...875L...9W (2019): The Ophiuchus DIsk Survey Employing ALMA (ODISEA): Disk Dust Mass Distributions across Protostellar Evolutionary Classes
- 2019ApJ...876...72L (2019): Sulfur Chemistry in Protoplanetary Disks: CS and H<SUB>2</SUB>CS
- 2019ApJ...876...91H (2019): Molecular Gas Properties in the Host Galaxy of GRB 080207
- 2019ApJ...876...99S (2019): Star Formation and ISM Properties in the Host Galaxies of Three Far-infrared Luminous Quasars at z ∼ 6
- 2019ApJ...876..112R (2019): Strong Far-ultraviolet Fields Drive the [C II]/Far-infrared Deficit in z ∼ 3 Dusty, Star-forming Galaxies
- 2019ApJ...876..130H (2019): ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies
- 2019ApJ...876L..10E (2019): A Radio Source Coincident with the Superluminous Supernova PTF10hgi: Evidence for a Central Engine and an Analog of the Repeating FRB 12110…
- 2019ApJ...876L..13S (2019): Line Ratios Reveal N<SUB>2</SUB>H<SUP>+</SUP> Emission Originates above the Midplane in TW Hydrae
- 2019ApJ...877L..22L (2019): The Anomalously Low (Sub)Millimeter Spectral Indices of Some Protoplanetary Disks May Be Explained By Dust Self-scattering
- 2019ApJ...877L..32M (2019): Multiple Rings of Millimeter Dust Emission in the HD 15115 Debris Disk
- 2019ApJ...878...16P (2019): An Inner Disk in the Large Gap of the Transition Disk SR 24S
- 2019ApJ...878...73Y (2019): ALMA 26 arcmin<SUP>2</SUP> Survey of GOODS-S at 1 mm (ASAGAO): Near-infrared-dark Faint ALMA Sources
- 2019ApJ...878..103R (2019): Modeling the Protoplanetary Disks of Two Brown Dwarfs in the Taurus Molecular Cloud
- 2019ApJ...878L...8T (2019): Discovery of An au-scale Excess in Millimeter Emission from the Protoplanetary Disk around TW Hya
- 2019ApJ...878L..25H (2019): ALMA Polarimetry of AT2018cow
- 2019ApJ...879...25K (2019): Highly Ordered and Pinched Magnetic Fields in the Class 0 Protobinary System L1448 IRS 2
- 2019ApJ...879...54L (2019): Revealing the Stellar Mass and Dust Distributions of Submillimeter Galaxies at Redshift 2
- 2019ApJ...879...75H (2019): Jet-driven Galaxy-scale Gas Outflows in the Hyperluminous Quasar 3C 273
- 2019ApJ...879..101L (2019): A Pseudodisk Threaded with a Toroidal and Pinched Poloidal Magnetic Field Morphology in the HH 211 Protostellar System
- 2019ApJ...879L...2M (2019): PDS 70: A Transition Disk Sculpted by a Single Planet
- 2019ApJ...879L..13M (2019): ALMA Observations of Molecular Gas in the Host Galaxy of AT2018cow
- 2019ApJ...880...15K (2019): The Molecular Gas Reservoirs of z ∼ 2 Galaxies: A Comparison of CO(1-0) and Dust-based Molecular Gas Masses
- 2019ApJ...880...69Y (2019): HL Tau Disk in HCO<SUP>+</SUP> (3-2) and (1-0) with ALMA: Gas Density, Temperature, Gap, and One-arm Spiral
- 2019ApJ...880..130M (2019): A New, Rotating Hot Corino in Serpens
- 2019ApJ...880L..19K (2019): A Luminous Molecular Gas Pair beyond Redshift 7
- 2019ApJ...881...10B (2019): A Precision Measurement of the Mass of the Black Hole in NGC 3258 from High-resolution ALMA Observations of Its Circumnuclear Disk
- 2019ApJ...881...63N (2019): An ALMA Multiline Survey of the Interstellar Medium of the Redshift 7.5 Quasar Host Galaxy J1342+0928
- 2019ApJ...881...84S (2019): The REASONS Survey: Resolved Millimeter Observations of a Large Debris Disk around the Nearby F Star HD 170773
- 2019ApJ...881..124M (2019): Resolved UV and [C II] Structures of Luminous Galaxies within the Epoch of Reionization
- 2019ApJ...881..147S (2019): Positive and Negative Feedback of AGN Outflows in NGC 5728
- 2019ApJ...881L...2B (2019): ALMA Observations of the Terahertz Spectrum of Sagittarius A*
- 2019ApJ...881L..23B (2019): The z = 7.54 Quasar ULAS J1342+0928 Is Hosted by a Galaxy Merger
- 2019ApJ...881L..39B (2019): Sub-arcsecond (Sub)millimeter Imaging of the Massive Protocluster G358.93-0.03: Discovery of 14 New Methanol Maser Lines Associated with a …
- 2019ApJ...882....1L (2019): CO and Fine-structure Lines Reveal Low Metallicity in a Stellar-mass-rich Galaxy at z ∼ 1?
- 2019ApJ...882....5W (2019): The Kennicutt-Schmidt Law and Gas Scale Height in Luminous and Ultraluminous Infrared Galaxies
- 2019ApJ...882...10N (2019): Resolved [C II] Emission from z &gt; 6 Quasar Host-Companion Galaxy Pairs
- 2019ApJ...882...31A (2019): A Superluminous Supernova in High Surface Density Molecular Gas within the Bar of a Metal-rich Galaxy
- 2019ApJ...882...49L (2019): Compact Disks in a High-resolution ALMA Survey of Dust Structures in the Taurus Molecular Cloud
- 2019ApJ...882..118X (2019): ALMA Detection of Vibrationally Excited (v <SUB>t</SUB> = 1, 2) Acetic Acid toward NGC 6334I
- 2019ApJ...882..136A (2019): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Evolution of the Molecular Gas in CO-selected Galaxies
- 2019ApJ...882..138D (2019): The ALMA Spectroscopic Survey in the HUDF: CO Luminosity Functions and the Molecular Gas Content of Galaxies through Cosmic History
- 2019ApJ...882..160Q (2019): Probing CO and N<SUB>2</SUB> Snow Surfaces in Protoplanetary Disks with N<SUB>2</SUB>H<SUP>+</SUP> Emission
- 2019ApJ...882L..31B (2019): The First Detection of <SUP>13</SUP>C<SUP>17</SUP>O in a Protoplanetary Disk: A Robust Tracer of Disk Gas Mass
- 2019ApJ...883....1Z (2019): An Episodic Wide-angle Outflow in HH 46/47
- 2019ApJ...883...22C (2019): The Degree of Alignment between Circumbinary Disks and Their Binary Hosts
- 2019ApJ...883...71C (2019): The Radial Distribution of Dust Particles in the HL Tau Disk from ALMA and VLA Observations
- 2019ApJ...883...98Z (2019): Systematic Variations of CO Gas Abundance with Radius in Gas-rich Protoplanetary Disks
- 2019ApJ...883..180H (2019): First Subarcsecond Submillimeter-wave [C I] Image of 49 Ceti with ALMA
- 2019ApJ...883..193N (2019): The ALMA Discovery of the Rotating Disk and Fast Outflow of Cold Molecular Gas in NGC 1275
- 2019ApJ...883L...2M (2019): The Origin of the X-Ray Emission in Two Well-aligned Extragalactic Jets: The Case for IC/CMB
- 2019ApJ...883L..29L (2019): First [N II]122 μm Line Detection in a QSO-SMG Pair BRI 1202-0725 at z = 4.69
- 2019ApJ...884...48C (2019): The Seven Most Massive Clumps in W43-Main as Seen by ALMA: Dynamical Equilibrium and Magnetic Fields
- 2019ApJ...884...97L (2019): Diagnosing 0.1-10 au Scale Morphology of the FU Ori Disk Using ALMA and VLTI/GRAVITY
- 2019ApJ...884..112T (2019): An ALMA/HST Study of Millimeter Dust Emission and Star Clusters
- 2019ApJ...884L..28I (2019): Counter-rotation and High-velocity Outflow in the Parsec-scale Molecular Torus of NGC 1068
- 2019ApJ...884L..58U (2019): First Detection of Radio Linear Polarization in a Gamma-Ray Burst Afterglow
- 2019ApJ...885...82L (2019): Sulfur-bearing Molecules in Orion KL
- 2019ApJ...885L..20H (2019): The Nuclear Filaments inside the Circumnuclear Disk in the Central 0.5 pc of the Galactic Center
- 2019ApJ...885L..39H (2019): First Detection of Submillimeter-wave [<SUP>13</SUP>C I] <SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Emission in a Gaseous Debr…
- 2019ApJ...886....6T (2019): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. I. Identifying and Characterizing the Protostellar Content …
- 2019ApJ...886...14F (2019): An ALMA View of Molecular Filaments in the Large Magellanic Cloud. I. The Formation of High-mass Stars and Pillars in the N159E-Papillon Ne…
- 2019ApJ...886...15T (2019): An ALMA View of Molecular Filaments in the Large Magellanic Cloud. II. An Early Stage of High-mass Star Formation Embedded at Colliding Clo…
- 2019ApJ...886L...4Z (2019): Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05
- 2019ApJ...887...37U (2019): The ALMA Spectroscopic Survey in the HUDF: Constraining Cumulative CO Emission at 1 ≲ z ≲ 4 with Power Spectrum Analysis of ASPECS LP Data …
- 2019ApJ...887...40W (2019): Resolving the Interstellar Medium in the Nuclear Region of Two z = 5.78 Quasar Host Galaxies with ALMA
- 2019ApJ...887...74F (2019): ALMA Reveals a Gas-rich, Maximum Starburst in the Hyperluminous, Dust-obscured Quasar W0533-3401 at z ∼ 2.9
- 2019ApJ...887..107F (2019): First Identification of 10 kpc [C II] 158 μm Halos around Star-forming Galaxies at z = 5-7
- 2019ApJ...887..149B (2019): Origins of Molecular Clouds in Early-type Galaxies
- 2019ApJ...887..183Z (2019): On the Gas Content, Star Formation Efficiency, and Environmental Quenching of Massive Galaxies in Protoclusters at z ≈ 2.0-2.5
- 2019ApJ...887..209A (2019): Protostellar Evolution in Serpens Main: Possible Origin of Disk-size Diversity
- 2019ApJS..241...19I (2019): ALMA Spatially Resolved Dense Molecular Gas Survey of Nearby Ultraluminous Infrared Galaxies
- 2019ApJS..244...25S (2019): The Bulge Asymmetries and Dynamical Evolution (BAaDE) SiO Maser Survey at 86 GHz with ALMA
- 2019ESC.....3.2088S (2019): Complex Organic Molecules in Star-Forming Regions of the Magellanic Clouds
- 2019Icar..319..417T (2019): Abundance measurements of Titan's stratospheric HCN, HC<SUB>3</SUB>N, C<SUB>3</SUB>H<SUB>4</SUB>, and CH<SUB>3</SUB>CN from ALMA observatio…
- 2019MNRAS.482..698C (2019): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution
- 2019MNRAS.482.1499M (2019): VALES V: a kinematic analysis of the molecular gas content in H-ATLAS galaxies at z ∼ 0.03-0.35 using ALMA
- 2019MNRAS.482.3135B (2019): The relationship between dust and [C I] at z = 1 and beyond
- 2019MNRAS.482L..29D (2019): Submillimetre dust polarization and opacity in the HD163296 protoplanetary ring system
- 2019MNRAS.483.1624B (2019): An ALMA archival study of the clump mass function in the Large Magellanic Cloud
- 2019MNRAS.484.1257M (2019): A gap in HD 92945's broad planetesimal disc revealed by ALMA
- 2019MNRAS.484.4239R (2019): The AGN fuelling/feedback cycle in nearby radio galaxies I. ALMA observations and early results
- 2019MNRAS.485..739M (2019): Asymmetric mid-plane gas in ALMA images of HD 100546
- 2019MNRAS.485.1595P (2019): Multiphase circumgalactic medium probed with MUSE and ALMA
- 2019MNRAS.485.2457H (2019): `The Brick' is not a brick: a comprehensive study of the structure and dynamics of the central molecular zone cloud G0.253+0.016
- 2019MNRAS.485.5377F (2019): A compact jet at the infrared heart of the prototypical low-luminosity AGN in NGC 1052
- 2019MNRAS.486..560S (2019): Passive galaxies in the early Universe: ALMA confirmation of z ∼ 3-5 candidates in the CANDELS GOODS-South field
- 2019MNRAS.486.4114R (2019): ALMA reveals a pseudo-disc in a proto-brown dwarf
- 2019MNRAS.487..444R (2019): Nuclear kinematics in nearby AGN - I. An ALMA perspective on the morphology and kinematics of the molecular CO(2-1) emission
- 2019MNRAS.487..622T (2019): Observation of narrow polar jets in the nascent wind of oxygen-rich AGB star EP Aqr
- 2019MNRAS.487.3102G (2019): GASP XVIII: star formation quenching due to AGN feedback in the central region of a jellyfish galaxy
- 2019MNRAS.487.4648S (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: source catalogue and properties
- 2019MNRAS.488..191G (2019): ALMA observations of A0620-00: fresh clues on the nature of quiescent black hole X-ray binary jets
- 2019MNRAS.488.1005P (2019): Upper limits on protolunar disc masses using ALMA observations of directly imaged exoplanets
- 2019MNRAS.488.5029H (2019): Star-formation rates of two GRB host galaxies at z ∼ 2 and a [C II] deficit observed with ALMA
- 2019MNRAS.489..427I (2019): Hyperluminous starburst gives up its secrets
- 2019MNRAS.489..470G (2019): ALMA Band 3 polarimetric follow-up of a complete sample of faint PACO sources
- 2019MNRAS.489.1927S (2019): Testing the blast-wave AGN feedback scenario in MCG-03-58-007
- 2019MNRAS.490.4956G (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: high-resolution dust continuum morphologies and the link between su…
- 2019MNRAS.490.5860S (2019): The multiphase gas structure and kinematics in the circumnuclear region of NGC 5728
- 2019NatAs...3..278K (2019): Publisher Correction: A circumbinary protoplanetary disk in a polar configuration
- 2019NatAs...3..314L (2019): The ice composition in the disk around V883 Ori revealed by its stellar outburst
- 2019NatAs...3..517Z (2019): Dynamics of a massive binary at birth
- 2019NatAs...3.1109P (2019): Kinematic detection of a planet carving a gap in a protoplanetary disk
- 2019Natur.569..519K (2019): Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback
- 2019Natur.570...83M (2019): A cool accretion disk around the Galactic Centre black hole
- 2019PASJ...71...40T (2019): Environmental impacts on molecular gas in protocluster galaxies at z ∼ 2
- 2019PASJ...71...68K (2019): A Chandra and ALMA study of X-ray-irradiated gas in the central ∼100 pc of the Circinus galaxy
- 2019PASJ...71...71H (2019): Big Three Dragons: A z = 7.15 Lyman-break galaxy detected in [O III] 88 μm, [C II] 158 μm, and dust continuum with ALMA
- 2019PASJ...71...85M (2019): Complex distribution and velocity field of molecular gas in NGC 1316 as revealed by the Morita Array of ALMA
- 2019PASJ...71..105T (2019): Rotating ionized gas ring around the Galactic center IRS13E3
- 2019PASJ...71..109H (2019): Detections of [O III] 88 μm in two quasars in the reionization epoch
- 2019PASJ...71L...3F (2019): First detection of PSR B1259-63/LS 2883 in the millimeter and submillimeter wavelengths with ALMA
- 2020A&A...633A..13D (2020): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. II. The spiral-outflow observed at…
- 2020A&A...633A.114S (2020): Demographics of disks around young very low-mass stars and brown dwarfs in Lupus
- 2020A&A...633A.126B (2020): The dynamically young outflow of the Class 0 protostar Cha-MMS1
- 2020A&A...633A.127F (2020): A CO molecular gas wind 340 pc away from the Seyfert 2 nucleus in ESO 420-G13 probes an elusive radio jet
- 2020A&A...633A.160C (2020): The ALMA Frontier Fields Survey. V. ALMA Stacking of Lyman-Break Galaxies in Abell 2744, Abell 370, Abell S1063, MACSJ0416.1-2403 and MACSJ…
- 2020A&A...634A...9M (2020): The flickering nuclear activity of Fornax A
- 2020A&A...634L...3Y (2020): First detection of the 448 GHz ortho-H<SUB>2</SUB>O line at high redshift: probing the structure of a starburst nucleus at z = 3.63
- 2020A&A...634L..12D (2020): ALMA reveals a large structured disk and nested rotating outflows in DG Tauri B
- 2020A&A...634L..15G (2020): Polarized emission by aligned grains in the Mie regime: Application to protoplanetary disks observed by ALMA
- 2020A&A...635A...2S (2020): Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA
- 2020A&A...635A..71W (2020): The Sun at millimeter wavelengths. I. Introduction to ALMA Band 3 observations
- 2020A&A...635A.119C (2020): Extended Hα over compact far-infrared continuum in dusty submillimeter galaxies. Insights into dust distributions and star-formation rates …
- 2020A&A...635L...9P (2020): Planet-induced spirals in the circumbinary disk of GG Tauri A
- 2020A&A...636A..37D (2020): Dust and gas content of high-redshift galaxies hosting obscured AGN in the Chandra Deep Field-South
- 2020A&A...636L...4M (2020): Spirals inside the millimeter cavity of transition disk SR 21
- 2020A&A...637A..84P (2020): The ALMA view of the high-redshift relation between supermassive black holes and their host galaxies
- 2020A&A...638A..17O (2020): SiO maser astrometry of the red transient V838 Monocerotis
- 2020A&A...639A..43A (2020): Cold molecular gas and PAH emission in the nuclear and circumnuclear regions of Seyfert galaxies
- 2020A&A...640A..13S (2020): Bipolar molecular outflow of the very low-mass star Par-Lup3-4. Evidence for scaled-down low-mass star formation
- 2020A&A...640A..19T (2020): Dust masses of young disks: constraining the initial solid reservoir for planet formation
- 2020A&A...640A..27V (2020): Protoplanetary disk masses in NGC 2024: Evidence for two populations
- 2020A&A...640A.104A (2020): ALMA resolves the remarkable molecular jet and rotating wind in the extremely radio-quiet galaxy NGC 1377
- 2020A&A...640A.111A (2020): Outflows, cores, and magnetic field orientations in W43-MM1 as seen by ALMA
- 2020A&A...641A.151S (2020): Molecular gas in the central region of NGC 7213
- 2020A&A...641L...2M (2020): All good things come in threes: the third image of the lensed quasar PKS 1830-211
- 2020A&A...642A..96P (2020): A search for millimeter emission from the coldest and closest brown dwarf with ALMA
- 2020A&A...642L...7P (2020): ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). II. Vertical stratification of CO, CS, CN, H<SUB>2</SUB>CO, and CH<SUB>3…
- 2020A&A...643A...1L (2020): The ALPINE-ALMA [CII] survey. Survey strategy, observations, and sample properties of 118 star-forming galaxies at 4 &lt; z &lt; 6
- 2020A&A...643A...2B (2020): The ALPINE-ALMA [CII] survey: Data processing, catalogs, and statistical source properties
- 2020A&A...643A..41D (2020): ALMA observations of transient heating in a solar active region
- 2020A&A...643A..53F (2020): GOODS-ALMA: Using IRAC and VLA to probe fainter millimeter galaxies
- 2020A&A...643A..89P (2020): Excitation and acceleration of molecular outflows in LIRGs: The extended ESO 320-G030 outflow on 200-pc scales
- 2020A&A...644A..11L (2020): A statistical analysis of dust polarization properties in ALMA observations of Class 0 protostellar cores
- 2020A&A...644A..59K (2020): Molecular remnant of Nova 1670 (CK Vulpeculae). I. Properties and enigmatic origin of the gas
- 2020A&A...644A..84M (2020): The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB>
- 2020A&A...644A.119P (2020): ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). III. The interplay between gas and dust in the protoplanetary disk of DG…
- 2020AJ....159...62C (2020): ALMA Observations of the Extraordinary Carina Pillars: HH 901/902
- 2020AJ....159..288M (2020): The Big Sibling of AU Mic: A Cold Dust-rich Debris Disk around CP-72 2713 in the β Pic Moving Group
- 2020ApJ...888L..28S (2020): Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA
- 2020ApJ...889....9M (2020): GASP. XXII. The Molecular Gas Content of the JW100 Jellyfish Galaxy at z ∼ 0.05: Does Ram Pressure Promote Molecular Gas Formation?
- 2020ApJ...889...43Z (2020): Dense Cores, Filaments, and Outflows in the S255IR Region of High-mass Star Formation
- 2020ApJ...889...59P (2020): Resolving the FU Orionis System with ALMA: Interacting Twin Disks?
- 2020ApJ...889...98M (2020): Investigating Overdensities around z &gt; 6 Galaxies through ALMA Observations of [C II]
- 2020ApJ...889..137M (2020): Balmer Break Galaxy Candidates at z ∼ 6: A Potential View on the Star Formation Activity at z ≳ 14
- 2020ApJ...889..141T (2020): A Noncorotating Gas Component in an Extreme Starburst at z = 4.3
- 2020ApJ...889..155W (2020): Observations of the Orion Source I Disk and Outflow Interface
- 2020ApJ...889..162L (2020): Probing the Full CO Spectral Line Energy Distribution (SLED) in the Nuclear Region of a Quasar-starburst System at z = 6.003
- 2020ApJ...889L...4L (2020): Revealing the CO X-factor in Dark Molecular Gas through Sensitive ALMA Absorption Observations
- 2020ApJ...889L..24P (2020): Long Baseline Observations of the HD 100546 Protoplanetary Disk with ALMA
- 2020ApJ...890...29F (2020): Multiphase Gas Flows in the Nearby Seyfert Galaxy ESO428-G014. Paper I
- 2020ApJ...890...76N (2020): ALMA Observations of Two Massive and Dense MALT90 Clumps
- 2020ApJ...890...95I (2020): <SUP>14</SUP>N/<SUP>15</SUP>N Isotopic Ratio in CH<SUB>3</SUB>CN of Titan's Atmosphere Measured with ALMA
- 2020ApJ...890..129K (2020): Detection of Irregular, Submillimeter Opaque Structures in the Orion Molecular Clouds: Protostars within 10,000 yr of Formation?
- 2020ApJ...890..130T (2020): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. II. A Statistical Characterization of Class 0 and Class I P…
- 2020ApJ...890..142P (2020): An ALMA Survey of H<SUB>2</SUB>CO in Protoplanetary Disks
- 2020ApJ...890..167T (2020): The Fifth Candidate for an Intermediate-mass Black Hole in the Galactic Center
- 2020ApJ...890L..14T (2020): Shaping the Envelope of the Asymptotic Giant Branch Star W43A with a Collimated Fast Jet
- 2020ApJ...891...48H (2020): A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk
- 2020ApJ...891...64F (2020): Truth or Delusion? A Possible Gravitational Lensing Interpretation of the Ultraluminous Quasar SDSS J010013.02+280225.8 at z = 6.30
- 2020ApJ...891...80M (2020): Properties of M Dwarf Flares at Millimeter Wavelengths
- 2020ApJ...891...83C (2020): ALMA Reveals the Molecular Gas Properties of Five Star-forming Galaxies across the Main Sequence at 3
- 2020ApJ...891..164S (2020): Chemistry and Physics of a Low-metallicity Hot Core in the Large Magellanic Cloud
- 2020ApJ...892...66M (2020): The ALMA Spectroscopic Survey in the HUDF: The Cosmic Dust and Gas Mass Densities in Galaxies up to z ∼ 3
- 2020ApJ...892...68N (2020): The MBHBM<SUB>⋆</SUB> Project. I. Measurement of the Central Black Hole Mass in Spiral Galaxy NGC 3504 Using Molecular Gas Kinematics
- 2020ApJ...892...99C (2020): The Surprisingly Low Carbon Mass in the Debris Disk around HD 32297
- 2020ApJ...892..111F (2020): Dust-depleted Inner Disks in a Large Sample of Transition Disks through Long-baseline ALMA Observations
- 2020ApJ...892..119M (2020): Measuring the Heating and Cooling of the Interstellar Medium at High Redshift: PAH and [C II] Observations of the Same Star-forming Galaxie…
- 2020ApJ...892..147S (2020): Oversized Gas Clumps in an Extremely Metal-poor Molecular Cloud Revealed by ALMA's Parsec-scale Maps
- 2020ApJ...892..152H (2020): Understanding the Origin of the Magnetic Field Morphology in the Wide-binary Protostellar System BHR 71
- 2020ApJ...892L..18I (2020): ALMA 50-parsec-resolution Imaging of Jet-ISM Interaction in the Lensed Quasar MG J0414+0534
- 2020ApJ...893...33L (2020): ALMA Polarimetry Measures Magnetically Aligned Dust Grains in the Torus of NGC 1068
- 2020ApJ...893...51S (2020): Disk Structure around the Class I Protostar L1489 IRS Revealed by ALMA: A Warped-disk System
- 2020ApJ...893...54Y (2020): Transition from Ordered Pinched to Warped Magnetic Field on a 100 au Scale in the Class 0 Protostar B335
- 2020ApJ...893..101L (2020): An Unbiased ALMA Spectral Survey of the LkCa 15 and MWC 480 Protoplanetary Disks
- 2020ApJ...893..125U (2020): Scattering-induced Intensity Reduction: Large Mass Content with Small Grains in the Inner Region of the TW Hya disk
- 2020ApJ...894...74B (2020): Protoplanetary Disks in the Orion Nebula Cluster: Gas-disk Morphologies and Kinematics as Seen with ALMA
- 2020ApJ...894...76W (2020): The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B
- 2020ApJ...894...87C (2020): Gas Kinematics of the Massive Protocluster G286.21+0.17 Revealed by ALMA
- 2020ApJ...894L..14L (2020): ALMA Observations of Massive Clouds in the Central Molecular Zone: Jeans Fragmentation and Cluster Formation
- 2020ApJ...895...64L (2020): Radio Linear Polarization of GRB Afterglows: Instrumental Systematics in ALMA Observations of GRB 171205A
- 2020ApJ...895...84Y (2020): Super-resolution Imaging of the Protoplanetary Disk HD 142527 Using Sparse Modeling
- 2020ApJ...895..101H (2020): Efficient Methanol Production on the Dark Side of a Prestellar Core
- 2020ApJ...895..109F (2020): Measuring Turbulent Motion in Planet-forming Disks with ALMA: A Detection around DM Tau and Nondetections around MWC 480 and V4046 Sgr
- 2020ApJ...895..119T (2020): ALMA ACA and Nobeyama Observations of Two Orion Cores in Deuterated Molecular Lines
- 2020ApJ...895..135K (2020): AGN X-Ray Irradiation of CO Gas in NGC 2110 Revealed by Chandra and ALMA
- 2020ApJ...895L...2N (2020): Substructure Formation in a Protostellar Disk of L1527 IRS
- 2020ApJ...895L..18B (2020): GW Ori: Interactions between a Triple-star System and Its Circumtriple Disk in Action
- 2020ApJ...895L..46L (2020): Hints of a Population of Solar System Analog Planets from ALMA
- 2020ApJ...896...35J (2020): A Detailed View of the Circumstellar Environment and Disk of the Forming O-star AFGL 4176
- 2020ApJ...896..110L (2020): ALMA Observations of NGC 6334S. I. Forming Massive Stars and Clusters in Subsonic and Transonic Filamentary Clouds
- 2020ApJ...896..127K (2020): Multiple Outflows in the High-mass Cluster-forming Region G25.82-0.17
- 2020ApJ...897...91G (2020): The ALMA Spectroscopic Survey in the HUDF: Deep 1.2 mm Continuum Number Counts
- 2020ApJ...897..122L (2020): PHANGS CO Kinematics: Disk Orientations and Rotation Curves at 150 pc Resolution
- 2020ApJ...897L..19M (2020): Discovery of a [C I]-faint, CO-bright Galaxy: ALMA Observations of the Merging Galaxy NGC 6052
- 2020ApJ...898...10T (2020): Circumbinary Disks of the Protostellar Binary Systems in the L1551 Region
- 2020ApJ...898...36L (2020): Dual-wavelength ALMA Observations of Dust Rings in Protoplanetary Disks
- 2020ApJ...898...54T (2020): Chemical Composition in the IRAS 16562-3959 High-mass Star-forming Region
- 2020ApJ...898...61I (2020): Circumnuclear Molecular Gas in Low-redshift Quasars and Matched Star-forming Galaxies
- 2020ApJ...898...75I (2020): ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act
- 2020ApJ...898...97B (2020): An Evolutionary Study of Volatile Chemistry in Protoplanetary Disks
- 2020ApJ...898..146M (2020): Dust Populations in the Iconic Vega Planetary System Resolved by ALMA
- 2020ApJ...899...10T (2020): FRagmentation and Evolution of Dense Cores Judged by ALMA (FREJA). I. Overview: Inner ∼1000 au Structures of Prestellar/Protostellar Cores …
- 2020ApJ...899...55A (2020): Search for Alignment of Disk Orientations in Nearby Star-forming Regions: Lupus, Taurus, Upper Scorpius, ρ Ophiuchi, and Orion
- 2020ApJ...899..152H (2020): Mapping Circumstellar Magnetic Fields of Late-type Evolved Stars with the Goldreich-Kylafis Effect: CARMA Observations at λ1.3 mm of R Crt …
- 2020ApJ...900....1F (2020): The ALPINE-ALMA [C II] Survey: Size of Individual Star-forming Galaxies at z = 4-6 and Their Extended Halo Structure
- 2020ApJ...900..131L (2020): Ionized and Atomic Interstellar Medium in the z = 6.003 Quasar SDSS J2310+1855
- 2020ApJ...901...74T (2020): Structural Evolution in Massive Galaxies at z ∼ 2
- 2020ApJ...901...79A (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies
- 2020ApJ...901..141K (2020): An Intensity Mapping Detection of Aggregate CO Line Emission at 3 mm
- 2020ApJ...901..151S (2020): Molecular Gas Outflow in the Starburst Galaxy NGC 1482
- 2020ApJ...901L...5K (2020): High Molecular Gas Masses in Absorption-selected Galaxies at z ≍ 2
- 2020ApJ...902...53S (2020): ALMA CO Observations of Gamma-Ray Supernova Remnant N132D in the Large Magellanic Cloud: Possible Evidence for Shocked Molecular Clouds Ill…
- 2020ApJ...902...78R (2020): The Complete Redshift Distribution of Dusty Star-forming Galaxies from the SPT-SZ Survey
- 2020ApJ...902..109B (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Excitation and Atomic Carbon in Star-forming Galaxies at z = 1-3
- 2020ApJ...902..110D (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Multiband Constraints on Line-luminosity Functions and the Cosmic Density of …
- 2020ApJ...902..141S (2020): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. III. Substructures in Protostellar Disks
- 2020ApJ...902L..47Z (2020): Confirming the Explosive Outflow in G5.89 with ALMA
- 2020ApJ...903...94M (2020): ALMA Observations of Giant Molecular Clouds in M33. II. Triggered High-mass Star Formation by Multiple Gas Colliding Events at the NGC 604 …
- 2020ApJ...903..145L (2020): ALMaQUEST. IV. The ALMA-MaNGA QUEnching and STar Formation (ALMaQUEST) Survey
- 2020ApJ...904..130V (2020): Kiloparsec-scale ALMA Imaging of [C II] and Dust Continuum Emission of 27 Quasar Host Galaxies at z ∼ 6
- 2020ApJ...904L..24S (2020): ALMA CO Observations of the Gamma-Ray Supernova Remnant RX J1713.7-3946: Discovery of Shocked Molecular Cloudlets and Filaments at 0.01 pc …
- 2020ApJ...905...85S (2020): Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc …
- 2020ApJ...905..152D (2020): [N II] Fine-structure Emission at 122 and 205 μm in a Galaxy at z = 2.6: A Globally Dense Star-forming Interstellar Medium
- 2020ApJS..247...61F (2020): The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements
- 2020ApJS..251...14H (2020): CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone
- 2020MNRAS.491.4724F (2020): A3COSMOS: the dust attenuation of star-forming galaxies at z = 2.5-4.0 from the COSMOS-ALMA archive
- 2020MNRAS.491L..18J (2020): The ALPINE-ALMA [C II] survey: a triple merger at z ∼ 4.56
- 2020MNRAS.493.3744F (2020): SMM J04135+10277: a distant QSO-starburst system caught by ALMA
- 2020MNRAS.493.4294B (2020): ALMA uncovers the [C II] emission and warm dust continuum in a z = 8.31 Lyman break galaxy
- 2020MNRAS.493L.108B (2020): <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc
- 2020MNRAS.494.2131F (2020): Fast cloud-cloud collisions in a strongly barred galaxy: suppression of massive star formation
- 2020MNRAS.495..943H (2020): Revealing new features of the millimetre emission of the circumbinary envelope of Mira Ceti
- 2020MNRAS.495.1577I (2020): Radiative equilibrium estimates of dust temperature and mass in high-redshift galaxies
- 2020MNRAS.495.2332K (2020): ALMACAL VII: first interferometric number counts at 650 μm
- 2020MNRAS.495.3840M (2020): A large amount of diffuse molecular gases in the bar of the strongly barred galaxy NGC 1300: cause of the low star formation efficiency
- 2020MNRAS.496.1834L (2020): Atacama Compact Array observations of the pulsar-wind nebula of SNR 0540-69.3
- 2020MNRAS.496.3128R (2020): Characterizing the radio continuum nature of sources in the massive star-forming region W75N (B)
- 2020MNRAS.496.4061D (2020): Revealing the intermediate-mass black hole at the heart of the dwarf galaxy NGC 404 with sub-parsec resolution ALMA observations
- 2020MNRAS.497.2771M (2020): VALES VI: ISM enrichment in star-forming galaxies up to z ∼ 0.2 using <SUP>12</SUP>CO(1-0), <SUP>13</SUP>CO(1-0), and C<SUP>18</SUP>O(1-0) …
- 2020MNRAS.497.2811K (2020): Survey of planetesimal belts with ALMA: gas detected around the Sun-like star HD 129590
- 2020MNRAS.497.3504T (2020): Jet-ISM interactions near the microquasars GRS 1758-258 and 1E 1740.7-2942
- 2020MNRAS.498L..87B (2020): FAUST I. The hot corino at the heart of the prototypical Class I protostar L1551 IRS5
- 2020MNRAS.499.2534K (2020): Resolved star formation in the metal-poor star-forming region Magellanic Bridge C
- 2020MNRAS.499.3837G (2020): Spirals, shadows, and precession in HD 100453 - I. The orbit of the binary
- 2020Natur.581..269N (2020): A cold, massive, rotating disk galaxy 1.5 billion years after the Big Bang
- 2020PASJ...72L...9F (2020): ALMA observations of PSR B1259-63/LS 2883 in an inactive period: Variable circumstellar disk?
- 2020PASP..132h4401T (2020): Herschel Observations of Disks around Late-type Stars
- 2021A&A...645A..45C (2021): Planck's Dusty GEMS. VIII. Dense-gas reservoirs in the most active dusty starbursts at z ∼ 3
- 2021A&A...645A.120F (2021): ALMA and MUSE observations reveal a quiescent multi-phase circumgalactic medium around the z ≃ 3.6 radio galaxy 4C 19.71
- 2021A&A...645A.145G (2021): ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). V. Sample, overview, and demography of disk molecular emission
- 2021A&A...646A..76L (2021): The ALPINE-ALMA [C II] survey. Luminosity function of serendipitous [C II] line emitters at z ∼ 5
- 2021A&A...646A.127H (2021): Multiwavelength dissection of a massive heavily dust-obscured galaxy and its blue companion at z∼2
- 2021A&A...648A..19W (2021): A highly non-Keplerian protoplanetary disc. Spiral structure in the gas disc of CQ Tau
- 2021A&A...648A..41V (2021): Outflows, envelopes, and disks as evolutionary indicators in Lupus young stellar objects
- 2021A&A...649A.125W (2021): HCN (1‒0) opacity of outflowing gas in Arp 220W
- 2021A&A...651L...6B (2021): A major asymmetric ice trap in a planet-forming disk. II. Prominent SO and SO<SUB>2</SUB> pointing to C/O &lt; 1
- 2021A&A...652A..30S (2021): The emergence of passive galaxies in the early Universe
- 2021A&A...652A..92N (2021): ALMA observations of the variability of the quiet Sun at millimeter wavelengths
- 2021A&A...652A..98G (2021): The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies
- 2021A&A...653A..46V (2021): Probing protoplanetary disk evolution in the Chamaeleon II region
- 2021A&A...653A.117B (2021): ORion Alma New GEneration Survey (ORANGES). I. Dust continuum and free-free emission of OMC-2/3 filament protostars
- 2021A&A...654A..35B (2021): A multiwavelength analysis of the spiral arms in the protoplanetary disk around WaOph 6
- 2021A&A...654A.165V (2021): The effect of active galactic nuclei on the cold interstellar medium in distant star-forming galaxies
- 2021A&A...655A..25Z (2021): The IBISCO survey. I. Multiphase discs and winds in the Seyfert galaxy Markarian 509
- 2021A&A...655A..72S (2021): Physical conditions in the warped accretion disk of a massive star. 349 GHz ALMA observations of G023.01‒00.41
- 2021A&A...655A..80D (2021): ATOMIUM: halide molecules around the S-type AGB star W Aquilae
- 2021A&A...656A..46M (2021): ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array
- 2021A&A...656A..60A (2021): Black hole feeding and star formation in NGC 1808
- 2021A&A...656A..68E (2021): The Sun at millimeter wavelengths. III. Impact of the spatial resolution on solar ALMA observations
- 2021AJ....161...38O (2021): The TW Hya Rosetta Stone Project. I. Radial and Vertical Distributions of DCN and DCO<SUP>+</SUP>
- 2021AJ....161..271F (2021): A Detailed Characterization of HR 8799's Debris Disk with ALMA in Band 7
- 2021AN....342.1160P (2021): CO kinematics unveil outflows plausibly driven by a young jet in the gigahertz peaked radio core of NGC 6328
- 2021ApJ...906...16S (2021): A New Feedback Cycle in the Archetypal Cooling Flow Group NGC 5044
- 2021ApJ...907L..15S (2021): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Detection of Extremely High-density Compact Structure of Prestellar Cores and M…
- 2021ApJ...908....8C (2021): The TW Hya Rosetta Stone Project. III. Resolving the Gaseous Thermal Profile of the Disk
- 2021ApJ...908...46B (2021): Dynamical Stellar Masses of Pre-main-sequence Stars in Lupus and Taurus Obtained with ALMA Surveys in Comparison with Stellar Evolutionary …
- 2021ApJ...908...54W (2021): ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5
- 2021ApJ...908..141H (2021): ALMA CN Zeeman Observations of AS 209: Limits on Magnetic Field Strength and Magnetically Driven Accretion Rate
- 2021ApJ...908..163M (2021): Extremely Low Molecular Gas Content in the Vicinity of a Red Nugget Galaxy at z = 1.91
- 2021ApJ...908..175C (2021): The Extraordinary Outburst in the Massive Protostellar System NGC 6334 I-MM1: Spatiokinematics of Water Masers during a Contemporaneous Fla…
- 2021ApJ...908..231M (2021): Compact Molecular Gas Distribution in Quasar Host Galaxies
- 2023ApJ...956L..16T (2023): An ALMA-resolved View of 7000 au Protostellar Gas Ring around the Class I Source CrA-IRS 2 as a Possible Sign of Magnetic Flux Advection
- 2023ApJ...956L..35Z (2023): One, Two, Three ... An Explosive Outflow in IRAS 12326-6245 Revealed by ALMA
- 2023MNRAS.526L..41P (2023): Kinematic and thermal signatures of the directly imaged protoplanet candidate around Elias 2-24
- 2023NatAs...7...80U (2023): Simultaneous radio and optical polarimetry of GRB 191221B afterglow
- 2023Natur.621..483G (2023): Polarized thermal emission from dust in a galaxy at redshift 2.6
- 2023PASJ...75..225M (2023): An expanding ring of the hypercompact H II region W 49 N:A2
- 2023PASJ...75..424O (2023): ALMA Band 6 high-resolution observations of the transitional disk around SY Chamaeleontis
- 2023PSJ.....4..142C (2023): Thermal Properties of the Leading Hemisphere of Callisto Inferred from ALMA Observations
- 2023PSJ.....4..193B (2023): Masses and Densities of Dwarf Planet Satellites Measured with ALMA
- 2023RAA....23a5004N (2023): Contributions of Rotation, Expansion and Line Broadening to the Morphology and Kinematics of the Inner CSE of Oxygen-rich AGB Star R Hya
- 2024A&A...681A..19C (2024): Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): HD 34700 A unveils an inner ring
- 2024A&A...682A..54T (2024): HYPERION. Interacting companion and outflow in the most luminous z &gt; 6 quasar
- 2024A&A...682A..56Z (2024): Exploring the dust grain size and polarization mechanism in the hot and massive Class 0 disk IRAS 16293-2422 B
- 2024A&A...682A.166F (2024): A benchmark for extreme conditions of the multiphase interstellar medium in the most luminous hot dust-obscured galaxy at z = 4.6
- 2024A&A...683A.133G (2024): TIPSY: Trajectory of Infalling Particles in Streamers around Young stars. Dynamical analysis of the streamers around S CrA and HL Tau
- 2024A&A...684A..23T (2024): Fitting pseudo-Sérsic (Spergel) light profiles to galaxies in interferometric data: The excellence of the uυ-plane
- 2024A&A...684A..24P (2024): GA-NIFS: Early-stage feedback in a heavily obscured active galactic nucleus at z = 4.76
- 2024A&A...684A..56K (2024): Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O
- 2024A&A...684A.134R (2024): Correlation between accretion rate and free-free emission in protoplanetary disks. A multiwavelength analysis of central mm/cm emission in …
- 2024A&A...684L..11G (2024): A spectacular galactic scale magnetohydrodynamic powered wind in ESO 320-G030
- 2024A&A...685A..80Z (2024): Unveiling [C II] clumps in a lensed star-forming galaxy at z ∼ 3.4
- 2024A&A...685A.138V (2024): The cold interstellar medium of a normal sub-L<SUP>⋆</SUP> galaxy at the end of reionization
- 2024A&A...686A..47M (2024): A possible relation between global CO excitation and massive molecular outflows in local ULIRGs
- 2024A&A...686A.201N (2024): ALMA view of the L1448-mm protostellar system on disk scales: CH<SUB>3</SUB>OH and H<SUP>13</SUP>CN as new disk wind tracers
- 2024A&A...686A.274V (2024): Molecular line polarisation from the circumstellar envelopes of asymptotic giant branch stars
- 2024A&A...687A.163B (2024): ALMA-IMF. XI. The sample of hot core candidates: A rich population of young high-mass protostars unveiled by the emission of methyl formate
- 2024A&A...688A..55M (2024): A<SUP>3</SUP>COSMOS: Measuring the cosmic dust-attenuated star formation rate density at 4 &lt; z &lt; 5
- 2024A&A...688L..18T (2024): Detection of maser emission at 183 and 380 GHz with ALMA in the gigamaser galaxy TXS 2226-184
- 2024A&A...689A..65R (2024): ALMA high-resolution observations unveil planet formation shaping molecular emission in the PDS 70 disk
- 2024A&A...689A..85G (2024): MINDS: A multi-instrument investigation into the molecule-rich JWST-MIRI spectrum of the DF Tau binary system
- 2024A&A...689A.104D (2024): From traffic jams to roadblocks: The outer regions of TW Hya with ALMA Band 8
- 2024A&A...689A.317G (2024): Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii
- 2024A&A...690A..46S (2024): Early Planet Formation in Embedded Disks (eDisk): XVI. Asymmetric dust disk driving a multicomponent molecular outflow in the young Class 0…
- 2024A&A...690A..55S (2024): NOEMA formIng Cluster survEy (NICE): Characterizing eight massive galaxy groups at 1.5 &lt; z &lt; 4 in the COSMOS field
- 2024A&A...690A.169L (2024): Neutral atomic and molecular gas dynamics in the nearby spiral galaxies NGC 1512, NGC 4535, and NGC 7496
- 2024A&A...691A..57M (2024): SPH modelling of AGB wind morphology in hierarchical triple systems and a comparison to observation of R Aql
- 2024A&A...691A.133V (2024): The ALMA-CRISTAL survey: Dust temperature and physical conditions of the interstellar medium in a typical galaxy at z = 5.66
- 2024A&A...691A.157V (2024): Identifying the mechanisms of water maser variability during the accretion burst in NGC6334I
- 2024A&A...691A.178B (2024): KASHz+SUPER: Evidence of cold molecular gas depletion in AGN hosts at cosmic noon
- 2024A&A...691A.180F (2024): CHEMOUT: CHEMical complexity in star-forming regions of the OUTer Galaxy: IV. ALMA observations of organic species at a galactocentric radi…
- 2024A&A...692A.215C (2024): Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon
- 2024AJ....167...66Y (2024): Chemistry of Complex Organic Molecules in the V883 Ori Disk Revealed by ALMA Band 3 Observations
- 2024Ap&SS.369...18M (2024): Multi-wavelength observation of MAXI J1348─630 during the outburst in 2019
- 2024ApJ...961..108K (2024): The CO Outflow Components Ejected by a Recent Accretion Event in B335
- 2024ApJ...961..120C (2024): Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus
- 2024ApJ...961..228S (2024): Ring Gap Structure around Class I Protostar WL 17
- 2024ApJ...962....1S (2024): Molecular Outflow in the Reionization-epoch Quasar J2054-0005 Revealed by OH 119 μm Observations
- 2024ApJ...962...48J (2024): Thermal Properties of the Hot Core Population in Sagittarius B2 Deep South.
- 2024ApJ...963....1O (2024): "Beads-on-a-string" Star Formation Tied to One of the Most Powerful Active Galactic Nucleus Outbursts Observed in a Cool-core Galaxy Cluster
- 2024ApJ...963...72O (2024): Revealing Multiple Nested Molecular Outflows with Rotating Signatures in HH270mms1-A with ALMA
- 2024ApJ...963..164R (2024): The Disk Orientations of Perseus Protostellar Multiples at ∼8 au Resolution
- 2024ApJ...964...48T (2024): An Extremely Young Protostellar Core, MMS 1/OMC-3: Episodic Mass Ejection History Traced by the Micro SiO Jet
- 2024ApJ...964..166K (2024): Physical Properties of Molecular Clouds in the Overlap Region of the Merging Antennae Galaxies
- 2024ApJ...965...68M (2024): ALMA Confirmation of Millimeter Time Variability in the Gamma-Ray Detected Seyfert Galaxy GRS 1734-292
- 2024ApJ...965..147B (2024): The Carbon Isotopic Ratio and Planet Formation
- 2024ApJ...966...51G (2024): The Size─Linewidth Relation and Signatures of Feedback from Quiescent to Active Star Forming Regions in the LMC
- 2024ApJ...966...59S (2024): Small and Large Dust Cavities in Disks around Mid-M Stars in Taurus
- 2024ApJ...966...84A (2024): Molecular Gas Tracers in Young and Old Protoplanetary Disks
- 2024ApJ...966..117X (2024): Disk Wind Feedback from High-mass Protostars. III. Synthetic CO Line Emission
- 2024ApJ...966..119L (2024): ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). I. What Triggered the Current Episode of Eruption?
- 2024ApJ...967...11C (2024): TEMPLATES: Characterization of a Merger in the Dusty Lensing SPT0418─47 System
- 2024ApJ...967...15K (2024): Infall Motions in the Hot Core Associated with the Hypercompact H II Region G345.0061+01.794 B
- 2024ApJ...968....9W (2024): A Spatially Resolved [C II] Survey of 31 z ∼ 7 Massive Galaxies Hosting Luminous Quasars
- 2024ApJ...968L..19F (2024): Deep Search for Phosphine in a Prestellar Core
- 2024ApJ...969..122Y (2024): ALMA Reveals Spatially Resolved Properties of Molecular Gas in the Host Galaxy of FRB 20191001A at z = 0.2340
- 2024ApJ...969..143I (2024): A Radial Decrease in Kinetic Temperature Measured with H<SUB>2</SUB>CO in 30 Doradus
- 2024ApJ...969..165D (2024): Chemistry in Externally FUV-irradiated Disks in the Outskirts of the Orion Nebula Cluster
- 2024ApJ...970....9B (2024): Multiphase Black Hole Feedback and a Bright [C II] Halo in a LoBAL Quasar at z ∼ 6.6
- 2024ApJ...970...56P (2024): Radio Emission from the Magnetically Active M Dwarf UV Ceti from 1 to 105 GHz
- 2024ApJ...970..153A (2024): On Kinematic Measurements of Self-gravity in Protoplanetary Disks
- 2024ApJ...971..129C (2024): A Dust-trapping Ring in the Planet-hosting Disk of Elias 2-24
- 2024ApJ...972..111L (2024): Ongoing and Fossil Large-scale Outflows Detected in a High-redshift Radio Galaxy: [C II] Observations of TN J0924-2201 at z = 5.174
- 2024ApJ...972..147C (2024): Comparisons between Resolved Star Formation Rate and Gas Tracers in the Strongly Lensed Galaxy SDSS J0901+1814 at Cosmic Noon
- 2024ApJ...972..163L (2024): First JVLA Radio Observation on PDS 70
- 2024ApJ...973...42B (2024): Resolving Twin Jets and Twin Disks with JWST and ALMA: The Young WL 20 Multiple System
- 2024ApJ...974...83Y (2024): Detection of Dimethyl Ether in the Central Region of the MWC 480 Protoplanetary Disk
- 2024ApJ...974..102S (2024): Hints of Planet Formation Signatures in a Large-cavity Disk Studied in the AGE-PRO ALMA Large Program
- 2024ApJ...975..103P (2024): The Faraday Rotation Measure of the M87 Jet at 3.5 mm with ALMA
- 2024ApJ...975..179C (2024): Modeling ALMA Observations of the Warped Molecular Gas Disk in the Red Nugget Relic Galaxy NGC 384
- 2024ApJ...976...70L (2024): The ALMA-CRISTAL Survey: Spatially Resolved Star Formation Activity and Dust Content in 4 &lt; z &lt; 6 Star-forming Galaxies
- 2024ApJ...976...88L (2024): Disk Turbulence and Star Formation Regulation in High-z Main-sequence Analog Galaxies
- 2024ApJ...976..132H (2024): High-resolution ALMA Observations of Richly Structured Protoplanetary Disks in σ Orionis
- 2024ApJ...977..198L (2024): The SUPERCOLD-CGM Survey. II. [C I](1─0) Emission and the Physical Conditions of Cold Gas in Enormous Lyα Nebulae at z ∼ 2
- 2024ApJ...977..251H (2024): Molecular Gas Mass Measurements of an Active, Starburst Galaxy at z ≍ 2.6 Using ALMA Observations of the [C I], CO, and Dust Emission
- 2024ESC.....8..665M (2024): Detection and Chemical Modeling of Complex Prebiotic Molecule Cyanamide in the Hot Molecular Core G31.41 + 0.31
- 2024IJAsB..23...14M (2024): Detection and prebiotic chemistry of possible glycine precursor molecule methylenimine towards the hot molecular core G10.47+0.03
- 2024JKAS...57..163L (2024): HCN and HNC in the Disk of an Outbursting Young Star, V883 Ori
- 2024MNRAS.527.9343L (2024): WISDOM project - XVIII. Molecular gas distributions and kinematics of three megamaser galaxies
- 2024MNRAS.529.3601R (2024): Observations of spiral and streamer on a candidate proto-brown dwarf
- 2024MNRAS.532.2842K (2024): MeerKAT observations of starburst galaxies and AGNs within the core of XMMXCS J2215.9-1738 at z = 1.46
- 2024MNRAS.534.2904C (2024): Observational signatures of circumbinary discs - II. Kinematic signatures in velocity residuals
- 2024MNRAS.534.3237M (2024): An independent hybrid imaging of Sgr A* from the data in EHT 2017 observations
- 2024NatAs...8..587F (2024): Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk
- 2024Natur.633..323V (2024): One month convection timescale on the surface of a giant evolved star
- 2024PASJ...76..340K (2024): Sub-parsec-scale jet-driven water maser with possible gravitational acceleration in the radio galaxy NGC 1052
- 2024PSJ.....5..125T (2024): Observations of Titan's Stratosphere during Northern Summer: Temperatures, CH<SUB>3</SUB>CN and CH<SUB>3</SUB>D Abundances
- 2024PSJ.....5..230D (2024): Surface Properties of the Kalliope─Linus System from ALMA and VLA Data
- 2024RAA....24g5017M (2024): Investigating Sulfur Chemistry in the HD163296 Disk
- 2024RMxAA..60..355R (2024): The Radio Continuum Source Projected Near HR 8799
- 2025A&A...693A..76C (2025): Dissecting the disk and the jet of a massive (proto)star: An ALMA view of IRAS 20126+4104
- 2025A&A...693A.151M (2025): REsolved ALMA and SMA Observations of Nearby Stars (REASONS): A population of 74 resolved planetesimal belts at millimetre wavelengths
- 2025A&A...694A..82S (2025): The ALPINE-ALMA [CII] Survey: Unveiling the baryon evolution in the interstellar medium of z ∼ 5 star-forming galaxies
- 2025A&A...695A...6P (2025): GA-NIFS: Multiphase analysis of a star-forming galaxy at z ∼ 5.5
- 2025A&A...695A.149K (2025): Physical conditions around high-mass young star-forming objects via simultaneous observations of excited OH and methanol masers
- 2025A&A...695A.236L (2025): Erosion of a dense molecular core by a strong outflow from a massive protostar
- 2025A&A...696A.100G (2025): PDRs4All: XII. Far-ultraviolet-driven formation of simple hydrocarbon radicals and their relation with polycyclic aromatic hydrocarbons
- 2025A&A...696A.150S (2025): ALMAGAL: II. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy: ALMA data processing and pipeline
- 2025A&A...697A..64V (2025): Turbulence in protoplanetary disks: A systematic analysis of dust settling in 33 disks
- 2025A&A...698A.183D (2025): Dust populations from 30 to 1000 au in the debris disk of HD 120326: Panchromatic view with VLT/SPHERE, ALMA, and HST/STIS
- 2025A&A...698A.204H (2025): An ALMA spectroscopic survey of the Planck high-redshift object PLCK G073.4−57.5 confirms two protoclusters
- 2025A&A...699A..62J (2025): ALMA observation of an evolving magnetized corona in the radio-quiet changing-state active galactic nucleus NGC 1566
- 2025A&A...699A.256P (2025): The ALMA-CRISTAL survey: Extended [CII] emission in an interacting galaxy system at z ∼ 5.5
- 2025A&A...699A.369V (2025): Dense clumps survive in the vicinity of R136 in 30 Doradus
- 2025A&A...699A.382M (2025): FAUST: XXV. A potential new molecular outflow in [BHB2007] 11
- 2025A&A...700A.188C (2025): FAUST: XXVI. The dust opacity spectral indices of protostellar envelopes bridge the gap between interstellar medium and disks
- 2025A&A...700A.278R (2025): CO(1─0) imaging reveals 10-kiloparsec molecular gas reservoirs around star-forming galaxies at high redshift
- 2025A&A...700A.285W (2025): Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593
- 2025A&A...701A..48D (2025): NGC 6860, Mrk 915, and MCG -01-24-012: I. Spatial anticorrelation between cold molecular and ionized gas distributions in Seyfert galaxies
- 2025A&A...701A.113M (2025): MIRACLE: I. Unveiling the multi-phase, multi-scale physical properties of the active galaxy NGC 424 with MIRI, MUSE, and ALMA
- 2025ApJ...984L..19Y (2025): exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings
- 2025ApJ...984L..57O (2025): The Ophiuchus DIsk Survey Employing ALMA (ODISEA): A Unified Evolutionary Sequence of Planet-driven Substructures Explaining the Diversity …
- 2025ApJ...985..194P (2025): Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies
- 2025ApJ...986L..11S (2025): Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint
- 2025ApJ...986L..22R (2025): The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at …
- 2025ApJ...988...72S (2025): ALMA-JELLY. I. High Resolution CO(2─1) Observations of Ongoing Ram Pressure Stripping in NGC 4858 Reveal Asymmetrical Gas Tail Formation an…
- 2025ApJ...988..135M (2025): The Physical Properties and Morphologies of Faint Dusty Star-forming Galaxies Identified with JWST
- 2025ApJ...988..162D (2025): Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations
- 2025ApJ...989....1Z (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results
- 2025ApJ...989....3D (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). III. Dust and Gas Disk Properties in the Lupus Star-forming Region
- 2025ApJ...989..138S (2025): A First Look at Spatially Resolved Infrared Supernova Remnants in M33 with JWST
- 2025ApJ...990...66K (2025): Reexamination of the CO Absorption Line in the M87 Nucleus
- 2025ApJ...990..145L (2025): ALMA Reveals an Eccentricity Gradient in the Fomalhaut Debris Disk
- 2025ApJ...990..183U (2025): Multiwavelength Dust Characterization of the HL Tau Disk and Implications for Planet Formation
- 2025ApJ...990L..31B (2025): ALMA Reveals Bright Circumgalactic Emission and a Biconical Outflow in z ∼ 6.4 Quasar PSOJ183+05
- 2025ApJ...991...53C (2025): HerS-3: An Exceptional Einstein Cross Reveals a Massive Dark Matter Halo
- 2025ApJ...992...44D (2025): Revisiting the Gas Dynamics of Henize 2─10: Possible Drivers of the Starburst
- 2025ApJ...992...55T (2025): Extended and Compact Ortho-H<SUB>2</SUB>D<SUP>+</SUP> Structures Close to the Moment of Star Formation: Evidence from ALMA-ACA Observations…
- 2025ApJ...992..103Z (2025): Impact of Gravity on Changing Magnetic Field Orientations in a Sample of Massive Protostellar Clusters Observed with ALMA
- 2025ApJ...992..211N (2025): Revisiting the Supermassive Black Hole Mass of NGC 7052 Using High Spatial Resolution Molecular Gas Observed with ALMA
- 2025ApJ...993...85Y (2025): Peculiar Disk Substructures Associated with the Young Eruptive Star EX Lupi
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...993..120H (2025): Early Planet Formation in Embedded Disks (eDisk). XVII. A Compact but Structured Keplerian Disk and Large-scale Streamers Revealed in the C…
- 2025ApJ...994..225N (2025): Unveiling Stellar Feedback and Cloud Structure in the ρ Ophiuchi-A Region Using ALMA and JWST: Discovery of Substellar Cores, C<SUP>18</SUP…
- 2025ApJ...994..233Y (2025): ALMA-IMF. XX. Core Fragmentation in the W51 High-mass Star-forming Region
- 2025ApJ...994..256Y (2025): A Face-on Accretion Disk Geometry Revealed by Millimeter-wave Periodicity in Sgr A<SUP>∗</SUP>
- 2025ApJ...995..151Y (2025): Molecular Gas and Star Formation in Dwarf Galaxies Observed by the Atacama Large Millimeter/submillimeter Array
- 2025ApJ...995..219F (2025): PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon
- 2025ApJ...995L..63L (2025): ALMA Reveals Diverse Dust-to-gas Mass Ratios and Quenching Modes in Old Quiescent Galaxies
- 2025ApJS..278...45F (2025): DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey
- 2025MNRAS.541.2540Z (2025): WISDOM Project─XXV. Improving the CO-dynamical supermassive black hole mass measurement in the galaxy NGC 1574 using high spatial resolutio…
- 2025MNRAS.541.4031D (2025): VERTICO ─ IX. Signatures of environmental processing of the gas in Virgo cluster spiral galaxies through mapping of CO isotopologues
- 2025NatAs...9..526O (2025): Observationally derived magnetic field strength and 3D components in the HD 142527 disk
- 2025NatAs...9.1476C (2025): A D/H ratio consistent with Earth's water in Halley-type comet 12P from ALMA HDO mapping
- 2025NatAs...9.1553F (2025): Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn
- 2025NatAs...9.1833L (2025): Detection of a septuple stellar system in formation via disk fragmentation
- 2025PASJ...77..572S (2025): ALMA 2D super-resolution imaging survey of Ophiuchus Class I/flat spectrum/II disks. I. Discovery of new disk substructures
- 2025SciA...11.4512O (2025): Massive extended streamers feed high-mass young stars
- 2026A&A...705A..39P (2026): High-z [OI] emission lines: COLDSIM simulations and ALMA observations
- 2026A&A...705A..81K (2026): Resolving the molecular gas emission of the z ∼ 2.5─2.8 starburst galaxies SPT 0125-47 and SPT 2134-50
- 2026A&A...705A.100E (2026): ALMAGAL: V. Relations between the core populations and the parent clump physical properties
- 2026A&A...705A.163H (2026): CHILES: X. Molecular and atomic gas at intermediate redshift
- 2026A&A...705A.193L (2026): Zooming into the water snow line: High-resolution water observations of the HL Tau disk
- 2026A&A...705A.198M (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview
- 2026A&A...707A.120H (2026): Spatial distribution of organics in the Horsehead nebula: Signposts of chemistry driven by atomic carbon
- 2026ApJ..1000..184N (2026): Investigating the Nested Structure of the Outflow from the Low Luminosity Protostar IRAS 16253-2429 Using JWST and ALMA
- 2026ApJ..1000..308W (2026): The ALPINE-CRISTAL-JWST Survey: Chemical Abundance Comparison between the ISM and CGM of Main-sequence Galaxies at z = 4─6
- 2026ApJ..1000..312Z (2026): A Potential Link between Nuclear Winds and Cold Gas Outflows on Kiloparsec Scales in Reionization-era Quasars
- 2026ApJ..1001..124M (2026): Multiwavelength ALMA Imaging of HD 34282: Dust-trapping Signatures of a Vortex Candidate
- 2026ApJ..1001..134S (2026): Protostellar Outflows Shed Light on the Dominant Close Companion Star Formation Pathways
- 2026ApJ..1001L...1T (2026): ALMA Band 9 CO(6─5) Reveals a Warm Ring Structure Associated with the Embedded Protostar in the Cold Dense Core MC 27/L1521F
- 2026ApJ..1002L..28Y (2026): A Close Quasar Pair in a Massive Galaxy Merger at z = 5.7
- 2026ApJ..1003...52D (2026): Molecular Gas Excitation in z ∼ 0.7 Gas-rich Poststarburst Galaxies from SQuIGG<inline-formula> <mml:math><mml:mover><mml:mrow><mml:mi>L</m…
- 2026ApJ..1003...64Y (2026): Compact Hydrogen Sulfide Emission Indicates Sulfur-bearing Ice Sublimation in the Inner Disk of HD 163296
- 2026ApJ..1003...65O (2026): A Study of HH 270 with the James Webb Space Telescope
- 2026ApJ..1003...68Y (2026): A Multiscale Molecular and Atomic Gas View on the H II Region N113 in the Large Magellanic Cloud: Evidence for High-mass Star Formation Tri…
- 2026ApJ..1003L..17Y (2026): Evidence for Multiple Orbiting Hotspots in the 340 GHz Variability of Sgr A*
- 2026ApJ..1004..126K (2026): An Active Galactic Nucleus in the Antennae Galaxies?
