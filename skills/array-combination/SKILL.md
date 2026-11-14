---
name: alma-array-combination
description: "Combine ALMA 12-m, 7-m (ACA) and Total Power data, or ALMA with another single dish, to recover extended emission: visibility concatenation and joint deconvolution, feathering, model-assisted clean plus feather (MACF), sdintimaging, TP2VIS and pseudo-visibilities, plus multi-configuration and multi-cycle 12-m merging. Use when a source is larger than the 12-m maximum recoverable scale, when the user asks about missing flux, short spacings, feather, ACA or TP weights, or when combining compact and extended configurations or several cycles. Built from 714 ALMA papers (2013-2026)."
---

# Combining 12m, 7m and Total Power data

An interferometer filters out emission on scales larger than its shortest baselines allow. Papers fill that gap
by adding the 7-m array (ACA) in the visibility plane and Total Power (TP) or another single dish, most often by
feathering in the image plane. Two things matter most. First, a 12m+7m image without TP can still miss a large
share of the extended flux (individual cases are under Pitfalls). Second, datasets must match before they are
merged: weights, flux scales, phase centres, spectral frames, primary-beam convention, units, epoch and, for
continuum single-dish maps, observing frequency. Every combined product needs a flux-recovery check against
single-dish data over the area and velocity range the single dish actually covers.

Counts come from the evidence pack (`skills/packs/array-combination.md`, 714 papers). "My count" means a regex
or hand count over the pack's 413 `array_combination` key-parameter lines (one per paper); how each was made is
in `references/parameters.md`. "(card)" marks a detail that the pack lists only by title or in a cut line, and
that I checked verbatim in that paper's methods card.

## When to use

- The target is extended relative to the 12-m maximum recoverable scale (MRS): molecular clouds, filaments,
  nearby galaxy discs, circumstellar envelopes, the Sun. Authors who skipped short spacings name it as a
  limitation: map accuracy "limited primarily by missing flux" from the lack of short-spacing data
  (2016PASJ...68...88K, card); ALMA continuum lacks single-dish data so flux is underestimated
  (2018MNRAS.475..448T); only relative brightness temperatures (2020ApJ...888L..28S, card); lack of short
  baselines leaves SZ pressure-model parameters degenerate (2024A&A...689A..41V).
- You need total fluxes, column densities, masses, sizes or line ratios over extended regions (R21 maps from
  12m+7m+TP, 2025ApJ...988..162D; GMC lifecycle maps, 2019Natur.569..519K; cloud catalogues from ACA+IRAM 30m,
  2023ApJ...953..164M).
- The archive holds 12-m, 7-m and TP MOUSs of the same Science Goal. The ALMA pipeline does not combine 12 m,
  7 m and TP (2023PASP..135g4501H), so archive products are per array.
- You are merging compact + extended 12-m configurations or data from several cycles of the same target.
- You want a non-ALMA single dish (IRAM 30m, APEX, Mopra, JCMT, Nobeyama 45m, Herschel, BGPS) as short spacings.
  My count: 29 lines name one, 18 of them with feathering.

## When not to use

- **Compact sources well inside the MRS.** Missing short-spacing flux negligible (2015A&A...576L...2S); ACA left
  out because differences were <~10% (2017ApJ...850..139W); no significant missing flux in 13CO, C18O and
  continuum (2020ApJ...896...36T). Check this per line, not per project.
- **Compact-source extraction or core catalogues.** Some papers use the extended data alone for source finding
  (2018A&A...618L...5N; 2018ApJ...855...24P). Use `core-extraction-cmf` or `source-extraction-counts`.
- **The array ratio is the measurement.** 2023ApJ...944...49F kept 12 m and ACA separate: 12 m flux traces the
  disk, ACA flux the disk plus inner envelope.
- **Visibility model fitting** is a separate analysis choice, not a replacement for a combined image. Examples:
  RADMC-3D + emcee (2021AJ....161..271F), galario + dynesty (2019A&A...628A.100D), SZ fits
  (2024A&A...689A..41V; 2024A&A...682A.186L). 2018A&A...617A..23B did both: it imaged 12m+ACA+TP data and
  separately fitted the main-array + ACA visibilities with uvmultifit. Use `uv-plane-fitting`. Joint fits do not
  measure the unsampled zero-spacing flux; 2020ApJ...898..146M calls its total belt flux model-dependent.
- **Combining bands** (Band 3 + Band 7, 2017A&A...604A.115V) is a spectral-index problem. Match uv ranges instead
  (2026A&A...705A..96M; 2015ApJ...812..126C). Use `spectral-index`.
- **Solar data** follow their own TP calibration and feathering chain (2020A&A...635A..71W; 2018A&A...619L...6N;
  2017SoPh..292...87S). Cross-normalising datasets cannot replace an absolute calibration (2022A&A...661L...4A).

## Steps

1. **Inventory and decide.** Goal: know what arrays exist and what each product will use.
   - Read the MOUS list (12-m TM1/TM2, 7-m, TP) and the 12-m MRS. Papers often make several products: TP+7m and
     TP+7m+12m sets (2020ApJ...894...87C); 7m+TP for one source, 12m+7m+TP for others (2021A&A...648A..41V);
     feather for some lines, concat for CO (2021ApJ...910..148M).
   - Array selection can differ per product (2021A&A...656A..60A; 2018A&A...611A..99K; 2024PASJ...76..437Y).
     Some dropped 7 m and TP because they added noise and artifacts (2022A&A...662A...8M). State your reasons.
   - Check single-dish coverage and sensitivity first. 2024ApJ...968..131T reports incomplete TP coverage and
     non-uniform sensitivity; 2021A&A...653A..53A assumes TP covers the full CO(2-1) extent. Mark regions without
     short-spacing support and restrict recovery claims to the common footprint.
2. **Calibrate each dataset separately, then check flux scales.** Goal: datasets agree before merging.
   - "Calibrated separately, then combined" is the normal order (2014A&A...570L..14R; 2022MNRAS.510.3734D).
     Re-run the pipeline when needed (2018MNRAS.480.4974H).
   - Compare fluxes on overlapping uv scales before combining: 12-m and ACA consistent within 10%, the
     calibration uncertainty (2020ApJ...889....9M, card), or within the 15% Band 8 uncertainty
     (2018ApJ...863..143C, card). Fix mismatches explicitly: rescale visibilities in the overlap range
     (2023A&A...676A...4C), match flux on baselines of similar length (2025MNRAS.536..684D), rescale to a common
     reference (2024A&A...687A.311A), or convert TP to the ACA flux scale (2020MNRAS.491..178K).
3. **Align phase centres, spectral frames and epochs.** Goal: identical sky and frequency grids, and data that
   describe the same source state. Details and tools (`fixvis`, `fixplanets`, `phaseshift`, VisAlign, `cvel`,
   `concat` `freqtol`/`dirtol`) are in `references/parameters.md`.
   - Check dates against variability: HDO and H2O about 2 weeks apart (2025NatAs...9.1476C, card); solar data not
     strictly simultaneous (2017ApJ...845L..19B, card); Sgr A* flux scaled between epochs (2017MNRAS.470.4209Y,
     card); all epochs given the first-epoch position (2017ApJ...850L...6A).
4. **Self-calibrate (12-m multi-configuration).** Goal: consistent gains. Each pattern cites only papers that
   state it:
   - Short-baseline self-cal, then concatenation and joint self-cal: 2018ApJ...869L..41A; 2025ApJ...989...30Z;
     2024ApJ...964..190L ("SB data were self-calibrated first, and then concatenated to the LB data before
     running a new self-calibration", card); 2025ApJ...993..120H (card). 2026A&A...710A.238D self-calibrated
     the short baselines separately only when flux varied by >10%.
   - Joint self-cal of the combined data, earlier stage not stated: 2025ApJ...986L..11S (card);
     2024AJ....167...66Y (card); after VisAlign and `statwt`, 2022MNRAS.513.5790C.
   - Self-calibrated SB data combined with LB data, joint stage not stated: 2025NatAs...9.1672Y.
   - Each configuration self-calibrated individually, then combined: 2019ApJ...873...73Z (card);
     2019ApJ...883...98Z. The pack does not show which pattern is most common.
5. **Continuum subtraction: before or after concatenation.** Goal: line-only visibilities.
   - Before: 2020ApJ...889....9M; 2018A&A...616A..34H; 2021ApJ...908....8C. After: `concat` then `uvcontsub`
     (2021ApJ...908..231M); combine, self-calibrate on the continuum, then subtract (2014A&A...570L..14R).
   - Either way (general practice): choose line-free ranges in each dataset's own frequency frame, since the
     same channel index can be a different frequency in another dataset or spw; separately fitted datasets may
     legitimately use different line-free selections. Self-calibrate on continuum-bearing data, apply the gains,
     then subtract. Record fit order and ranges, and inspect residual continuum in line-free channels of the
     combined cube. TP continuum was subtracted with an order-one polynomial (2024MNRAS.530..597B).
6. **Set relative visibility weights.** Goal: each array contributes by its real sensitivity.
   - ACA/12-m examples: 7m weight 0.116 against 1 (2024A&A...688A..30B, simulated); ACA multipliers 0.3
     (2014A&A...570L..14R), 0.25 (2017A&A...605A.126R), 0.41 (2025ApJ...990..150A), x2.4
     (2021A&A...650A.202R); resulting ratios 0.18 (2020A&A...633A..13D) and ACA:TM1:TM2 ~1:5:6
     (2018A&A...616A..34H); noise-based weights (2019Natur.569..519K); `statwt` (2016ApJ...832..158Z).
   - Configuration and cycle weights: multipliers 0.2 (2023MNRAS.522.4078C; 2020A&A...642A..93H), 1/10
     (2016ApJ...829L..10I), `visweightscale` 0.6 and 0.2 (2026ApJ..1005...94N); ratios 1:4 or 1:1 by product
     (2022A&A...664A..63X); `statwt` after merging (11 papers, my count).
   - These are different quantities (multipliers vs resulting ratios). Work out what yours are normalised to
     before reusing any. General background: with equal Tsys, bandwidth and time, a 7m-7m baseline carries
     (7/12)^4 = 0.116 of a 12m-12m weight; data whose weights already reflect sensitivity need no extra factor.
     Inspect weight vs uv distance per array with `plotms` before and after.
7. **Combine 12-m and 7-m interferometric data.** Goal: one deconvolution over all baselines.
   - My count: about 137 lines name both 12-m and 7-m/ACA data. Most `concat` (2021ApJ...908..231M), pass both
     to one `tclean` with the mosaic gridder (2025A&A...701A.219N), image jointly, or do not say how. Use
     `copypointing=False` in `concat` when not mosaicking (2018MNRAS.481.4931E).
   - Less common: clean separately and feather (2019ApJ...871..170M; 2020ApJ...896...36T, who found a
     visibility-domain combination similar); union-mask hybrid (2019ApJ...885...50W); ACA image as
     `modelimage` for the 12-m clean, then feather (2018ApJ...863..143C).
8. **Add Total Power or another single dish.** Goal: restore the zero and shortest spacings. My count: 79 lines
   combine ALMA TP. 55 say they feathered (3 of those first used the single dish as a clean model), 4 use
   TP2VIS, 4 pseudo-visibilities or SD2VIS, 1 the TP cube as `tclean` model (2021A&A...645A..97Q), 1 "Fourier
   space" (2019Natur.569..519K), 1 MIRIAD `immerge` (2026ApJ..1001...33L), 13 do not say.
   - **Units first, by method.** `feather` takes images in Jy/beam with correct beam metadata. MACF needs the
     single-dish image in Jy/pixel as `startmodel` (2023PASP..135c4501P), so divide Jy/beam by the beam area in
     pixels. Stated K-to-Jy factors: APEX Tmb x39 to Jy/beam (2013ApJ...774...73I); Mopra 16.2 Jy/K and IRAM
     6.15 Jy/K (2017ApJ...835..265W); TP 41 Jy/K from Ta* in Band 3 (2019ApJ...887...88E, card).
     2021MNRAS.500.5500B prints "~41.5 K/Jy", so its direction is unclear. Factors depend on telescope,
     frequency and temperature scale (Ta* vs Tmb); never transfer one without those.
   - **Feathering.** `imregrid` the single dish to the interferometer grid, then `feather`; `sdfactor` 1.0 is the
     stated value (2018ApJ...867..111Z; 2024A&A...688A..30B). The PHANGS-ALMA pipeline images, PB-corrects and
     feathers with TP (2025ApJ...988..162D; 2021ApJS..257...43L). Staged: ACA with TP, then with 12 m
     (2024A&A...691A..70N).
   - **Primary-beam convention.** Pick one branch (general practice). (a) Apparent sky: feather the
     non-PB-corrected interferometer image with a single dish multiplied by the interferometer PB, then
     PB-correct once. Seen in 2019A&A...623A..96Y (IRAM 30m x mosaic PB) and 2025ApJ...985..166K ("the combined
     map was divided by the ALMA primary beam pattern", card). (b) PB-corrected: feather a PB-corrected image
     with the unattenuated single dish and mask to the footprint. Never mix the branches or PB-correct twice.
     2020ApJ...894...72S says TP was divided by the 7m PB before feathering and PB-corrected after; that fits
     neither branch, so check such a recipe before copying it.
   - **Single dish as clean model.** TP as clean model, then feather (2017A&A...605A..28D); MACF
     (2023PASP..135c4501P; 2024A&A...688A..30B); feathered cube as model for a new clean (2013ApJ...774...73I);
     TP-model clean, feather positive components, clean again (2018MNRAS.475..448T).
   - **Joint deconvolution.** `sdintimaging` (2023PASP..135c4501P); with APEX as single-dish input
     (2026ApJ..1003...68Y, card).
   - **Single dish to visibilities.** TP2VIS (2018ApJ...867..166S; 2021A&A...653A..53A; 2023ApJ...949..108K).
     GILDAS pseudo-visibilities: TP to ACA 0-5 m then 12 m 0-12 m (2025A&A...696A.100G); IRAM 30m map
     deconvolved, multiplied by the 7m PB, sampled 0-7 m (2026A&A...707A.120H). State how the single-dish beam
     is removed before sampling; without that step the pseudo-visibilities carry the single-dish beam taper.
   - **Cross-frequency continuum maps** need a spectral conversion first (2014ApJ...795L..25R; graybody,
     2016ApJ...832..143F; alpha_nu = 3.75, 2022MNRAS.514..578W; SED extrapolation with J-comb,
     2026A&A...708A.251X). Propagate the temperature and spectral-index uncertainty.
9. **Image and restore.** Settings are in `references/parameters.md`; most are single-paper examples, so set
   thresholds from your own rms. Multi-configuration dirty beams are not Gaussian; papers apply the JvM residual
   rescaling (2023A&A...669A..53B; 2023ApJ...949..108K). Too few iterations lost TP2VIS flux
   (2021A&A...653A..53A). Report beam, rms and the arrays in each product.
10. **Verify flux recovery** (Verification checks) before any mass or column density.

## Parameter defaults and ranges

Short version; the full table, count methods and paper lists are in `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| TP method (authors' wording) | feather | SD as clean model, TP2VIS, pseudo-vis, immerge | 55 feather of 79 TP lines (my count) | 2024MNRAS.530..597B, 2021A&A...653A..53A |
| 12m+7m method | concat or joint `tclean` | separate clean + feather; ACA as model | most of ~137 lines (my count) | 2021ApJ...908..231M, 2019ApJ...871..170M |
| ACA/12-m weight | not stated by most | multipliers 0.116-0.41, x2.4; ratios 0.18, 1:5:6 | 1 each | 2024A&A...688A..30B, 2020A&A...633A..13D |
| Per-configuration weight | unscaled | multipliers 0.2, 0.6, 1/10; ratios 1:4, 1:1 | 5 | 2026ApJ..1005...94N, 2022A&A...664A..63X |
| Weighting, line cubes | Briggs robust 0.5 | natural; robust 1, 2 | r0.5 15, natural 4 of 20 (my count) | 2021ApJ...908..231M, 2020ApJ...889....9M |
| Weighting, continuum | Briggs robust 0.5 | natural; robust 0 | r0.5 5 of 7 (my count) | 2025A&A...701A.219N, 2022A&A...662A...8M |
| Feather `sdfactor` | 1.0 or "default" | rarely stated | 2 explicit | 2018ApJ...867..111Z, 2024A&A...688A..30B |
| Deconvolver | multiscale | Hogbom | 16; 7 (my count) | 2024ApJ...968..131T, 2021A&A...645A..97Q |

Recommendations that follow: use visibility-domain 12m+7m combination with checked weights, then feather with TP
under one primary-beam convention, because that is the most common route in the pack. The one quantitative
method comparison (2023PASP..135c4501P) found SDINT and MACF raised simulated total-flux recovery above ~92%, and
Feather and MACF had the narrowest M100 A-par distributions, but it used standard `sdfactor`/`sdgain` values,
assumed aligned flux scales, and says ~10% differences on M100 are hard to interpret. 2024A&A...688A..30B took a
12m + IRAM-30m MACF map as its reference, which is an assumption, not a test. So run feather and MACF yourself
and compare them against the single dish.

## Software

Mentions in the pack's software aggregate (matched steps only), version and "casa" prefix variants merged.

| Software | Mentions | Used for | Examples |
|---|---|---|---|
| CASA (incl. "casa 5.4.1", "casa 5.6") | 190 | calibration, `concat`, `statwt`, `tclean`, `feather` | 2021ApJ...908..231M |
| `tclean` (incl. "casa tclean") | 53 | joint deconvolution, MACF | 2020ApJ...889....9M |
| `feather` (incl. "casa feather") | 27 | image-plane combination | 2024ApJ...968..131T |
| GILDAS (MAPPING), CLASS | 11; 4 | pseudo-visibilities, single-dish reduction | 2025A&A...696A.100G |
| Miriad | 9 | `immerge`, TP2VIS joint deconvolution | 2026ApJ..1001...33L, 2023ApJ...949..108K |
| PHANGS-ALMA pipeline | 9 | 12m+7m+TP imaging chain | 2025ApJ...988..162D |
| `uvcontsub`; `concat` | 9; 5 | continuum subtraction, merging | 2021ApJ...908..231M |
| TP2VIS; uvcombine; almica | 3; 2; 2 | TP to visibilities; feathering; uv-domain combination | 2018ApJ...867..166S, 2025ApJ...992L..15L |

More rows (simobserve, SoAP, uvmultifit, galario) are in `references/parameters.md`.

## Pitfalls

- **12m+7m without TP still misses flux.** Individual cases, measured differently: "even with the ACA only 50%
  of the extended flux is recovered" (2014A&A...570L..14R); ACA-only 12CO(2-1) missed 60-70% of the IRAM 30m flux
  in M33 (2023ApJ...953..164M); 7m+TP feather with interferometric flux 70% of single-dish (2024A&A...689A.122B);
  ALMA-ACA recovered 8.4 of ~29 Msun (2018ApJ...856..147O, card); ACA recovered 41% and 21% of SCUBA-2 flux with
  assumed beta = 1.8 (2020ApJ...895..119T, card); [CI] flux 34±15% below Herschel (2018ApJ...863..143C, card).
  Treat masses from such maps as lower limits, as 2021A&A...648A..41V did for outflows (card); spatial filtering
  "severely limits" masses near the cloud velocity (2017ApJ...837...60B, card).
- **Filtering changes shapes and peaks.** ACA profile slope p=4.0 vs Herschel p=1.6, and the ACA density profile
  cannot be discussed (2018ApJ...856..147O, card); ACA-only envelope sizes underestimated by a factor of two
  against TP (2021A&A...653A..53A); simulated interferometer-only peak down ~40% (2023PASP..135c4501P).
- **Missing flux depends on channel and line.** Up to 30-40% in central channels (2015ApJ...814..143A, card);
  interferometer ~0.15 and feathered ~0.8 of NRO45 flux (2019ApJ...872..121U, card). ACA CO(1-0) that resolves
  out extended emission could inflate r21 (2024MNRAS.527.4420M).
- **Deconvolution does not conserve flux** in combined data (2026ApJ..1001..184M).
- **Single-dish flux scale.** Solar TP rescaled by 0.979 (2020A&A...635A..71W). In a Herschel + SCUBA feather (no
  ALMA data) SCUBA was scaled by 3 and 0.5-10x was tested (2018ApJ...853..171G). Feathering passes any
  single-dish calibration error into the large-scale flux.
- **Units and PB.** A Jy/beam image used as a Jy/pixel model, a K-to-Jy factor reused at another frequency, or a
  mixed PB branch all give flux errors; PB errors grow toward the mosaic edge. A CASA mosaic issue overestimated
  fluxes by 10% (2019A&A...623A..96Y, card); 2023ApJ...953..164M dropped edge clouds.
- **Incomplete single-dish coverage** (2024ApJ...968..131T): outside the TP footprint the "combined" map is
  interferometer-only.
- **Unchecked weights.** Cycle data can carry weights that do not reflect sensitivity; fix with `statwt` or
  noise-based rescaling (2017A&A...605A..42C; 2019ApJ...887...40W).
- **Correlated pixels** in combined maps: 2017ApJ...845L..19B did not correct for beam-scale correlation in a
  pixel-by-pixel comparison (card). Bin to at least a beam before regressions.
- **Settings the cards flag as not stated:** feathering parameters (3 cards), TP method (2020A&A...633A..13D),
  12-m/ACA weighting (2018ApJ...856..147O; 2021ApJ...908..231M); generally CASA version (30), line-free channels
  (15), flux-scale uncertainty (13), self-cal intervals (11), PB correction details (9). Counts per phrasing,
  from the not-stated aggregate.

## Verification checks

What the papers did:

- **Total flux vs single dish, with matched apertures.** Combined maps recovered ~90% of APEX flux
  (2017A&A...605A..28D, card; 2020A&A...633A..13D, card); ACA+TP feather 99.7% (2021MNRAS.500.5500B); ~50%
  missing on the southern side vs IRAM 30m (2020ApJ...903...94M, card); global CO luminosity of ACA, IRAM 30m and
  ACA+IRAM compared (2023ApJ...953..164M). Use the same aperture, velocity range and mask for both: thresholded
  extraction lost on average 60% (range 25-89%) against a 30" aperture, and curves of growth flattened beyond 30"
  (2024MNRAS.527.4420M). Check curves of growth before blaming spatial filtering.
- **Spectra at matched resolution.** Feathered vs IRAM 30-m profile (2018ApJ...858...90G); 7M+TP vs TP
  (2019PASJ...71...85M); feathered vs JCMT spectrum over the ALMA field (2025ApJ...985..166K, card).
- **Morphology.** Combined vs TP images to show 7m filaments are not edge artifacts (2024ApJ...968..131T).
- **Gain from short spacings.** 12m+ACA recovered 9-24% extra CO over ACA alone in four of six sources
  (2021ApJ...908..231M, card); TP2VIS raised flux by at least 30% (2021A&A...653A..53A).
- **Sensitivity to choices.** ACA weight changes did not affect results (2014A&A...570L..14R); varying APEX/ALMA
  relative calibration changed clump properties <10% in 12CO (2013ApJ...774...73I); visibility vs image domain
  gave similar results (2020ApJ...896...36T); direct Fourier-plane feather gave no clear improvement
  (2018MNRAS.475..448T).
- **Simulation.** `simobserve` a sky model per array and score every method (2023PASP..135c4501P).

What a careful referee adds (general practice):

- Smooth to the single-dish beam and compare channel by channel inside the common footprint.
- Compare radial uv amplitudes of TP, 7m and 12m in their overlap annulus.
- State the arrays and MRS for every product, the PB branch, the unit conversions, and recovery per line.
- Record unknown settings as unknown; do not copy a value from the parameter table.

## Source cards

Full list: `references/sources.md` (714 papers). Most informative:

- 2023PASP..135c4501P: feather, SDINT, MACF, FSSC compared on a simulated sky and M100
- 2024A&A...688A..30B: 7m weight 0.116, feather sdfactor 1.0, MACF
- 2021A&A...653A..53A: per-antenna TP imaging, TP2VIS, ACA-only vs TP sizes
- 2023ApJ...949..108K: TP2VIS weights, MIRIAD joint deconvolution, JvM
- 2018ApJ...867..166S: TP2VIS, TP weight from map rms
- 2014A&A...570L..14R: ACA weight 0.3, 50% recovery even with ACA
- 2018A&A...616A..34H: ACA:TM1:TM2 weights from sensitivity
- 2019Natur.569..519K: noise-based 12m/7m weights, TP in Fourier space
- 2025ApJ...988..162D: PHANGS-ALMA feathering
- 2024MNRAS.530..597B: two 12-m configurations + ACA, TP feathered
- 2019A&A...623A..96Y: IRAM 30m multiplied by mosaic PB, feathered
- 2013ApJ...774...73I: APEX K-to-Jy, feathered cube as clean model
- 2018MNRAS.475..448T: TP-model clean and feather
- 2025A&A...696A.100G: GILDAS pseudo-visibilities TP to ACA to 12 m
- 2026A&A...707A.120H: deconvolved IRAM 30m to 7m pseudo-visibilities
- 2023ApJ...953..164M: ACA + IRAM 30m feather, 60-70% ACA-only missing flux
- 2024MNRAS.527.4420M: matched apertures and curves of growth
- 2024ApJ...968..131T: incomplete TP coverage, feather, morphology check
- 2021ApJ...908..231M: concat then uvcontsub
- 2023A&A...676A...4C: visibilities rescaled on overlapping uv ranges
- 2026A&A...708A.251X: J-comb with an SED-extrapolated single-dish map
