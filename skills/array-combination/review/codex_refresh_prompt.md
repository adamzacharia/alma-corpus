# Review task: a REFRESHED ALMA agent skill against its rebuilt evidence pack

The skill below was first written from a ~1,600-paper corpus, reviewed, and fixed (the fix record is the
RECONCILIATION section). The corpus then grew to ~3,500 papers, the evidence pack was rebuilt, and a writer began
updating the skill to the new pack. The writer may have been cut off before finishing, so expect a mix: some
counts and ranges updated to the new pack, others still at the old values, and possibly a half-edited section.

Apply every check from the standard review (attribution, unsupported practice, scientific correctness, omissions,
usability: see below), and also these refresh checks:

A. **Stale or mixed numbers.** Paper counts, "used in N papers", common choices and ranges that do not match the
   NEW pack aggregates (the old corpus was about half the size, so old counts are usually roughly half). The
   description line's "Built from N ALMA papers" must match the pack.
B. **Lost fixes.** Any item the RECONCILIATION marks FIXED that the current skill has undone or reintroduced.
C. **Broken edits.** Duplicated sections, contradictory statements left from an unfinished rewrite, tables whose
   rows disagree with the text, dangling references.
D. **Length.** Over ~300 lines is a low-severity usability finding; say what could move to references/parameters.md.

Standard checks, in this order:
1. Attribution: every number, range, default, software attribution and "papers do X" claim that cites bibcodes is
   supported by the pack for those bibcodes; counts match the pack aggregates.
2. Unsupported practice presented as literature practice.
3. Scientific correctness: formulas, units, CASA task/parameter names and semantics, unsafe advice.
4. Omissions: important pitfalls, assumptions or validation checks clearly present in the pack but missing.
5. Usability: anything an agent would misread or could not act on.

You have no file access: everything you need is in this message.

Output format (Markdown, nothing else):

```
# Codex refresh review: <slug>
VERDICT: CLEAN | FIX
REFRESH: COMPLETE | PARTIAL   (PARTIAL if any section still carries old-pack numbers or an unfinished edit)
## Findings
- RR-01 | high|medium|low | <stale|lost-fix|broken-edit|length|attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- RR-02 | ...
## Notes
<at most 5 lines>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (array-combination) ===
---
name: alma-array-combination
description: "Combine ALMA 12-m, 7-m (ACA) and Total Power data, or ALMA with another single dish, to recover extended emission: visibility concatenation and joint deconvolution, feathering, model-assisted clean plus feather (MACF), sdintimaging, TP2VIS and pseudo-visibilities, plus multi-configuration and multi-cycle 12-m merging. Use when a source is larger than the 12-m maximum recoverable scale, when the user asks about missing flux, short spacings, feather, ACA or TP weights, or when combining compact and extended configurations or several cycles. Built from 714 ALMA papers (2013-2026)."
---

# Combining 12m, 7m and Total Power data

An interferometer filters out emission on scales larger than its shortest baselines allow. Papers fill that gap
by adding the 7-m array (ACA) in the visibility plane and Total Power (TP) or another single dish, most often by
feathering in the image plane. Two things matter most. First, a 12m+7m image without TP can still miss a large
share of the extended flux (individual cases, measured in different ways, are under Pitfalls). Second, datasets
must match before they are merged: weights, flux scales, phase centres, spectral frames, primary-beam
convention, observing epoch and, for continuum single-dish maps, observing frequency. Every combined product
needs a flux-recovery check against single-dish data.

Counts below are from the evidence pack (`skills/packs/array-combination.md`, 714 papers). Where a count is my own
tally of the pack's 413 `array_combination` lines (one per paper), it says so; I left out lines that are
off-topic for this technique (band-to-band images such as 2014MNRAS.444.1821F and 2017A&A...604A.115V,
spectral-window stacking such as 2024A&A...690A..55S, single-array mosaics such as 2014ApJ...784...62A).

## When to use

- The target is extended relative to the 12-m maximum recoverable scale (MRS): molecular clouds, filaments,
  nearby galaxy discs, circumstellar envelopes, the Sun. Authors who skipped short spacings name it as a
  limitation: "Missing flux on large scales due to no Total Power Array" (2016PASJ...68...88K); ALMA continuum
  without single-dish data underestimates the flux (2018MNRAS.475..448T); only relative brightness temperatures
  because single-dish data were not combined (2020ApJ...888L..28S); missing flux for some lines
  (2015ApJ...803...60S); lack of short baselines leaves SZ pressure-model parameters degenerate (2024A&A...689A..41V).
- You need total fluxes, column densities, masses, sizes or line ratios over extended regions (R21 maps from
  12m+7m+TP, 2025ApJ...988..162D; GMC lifecycle maps, 2019Natur.569..519K; cloud catalogues from ACA+IRAM 30m,
  2023ApJ...953..164M).
- The archive holds 12-m, 7-m and TP MOUSs of the same Science Goal. The ALMA pipeline does not combine 12 m,
  7 m and TP for you (2023PASP..135g4501H), so archive products are per array.
- You are merging compact + extended 12-m configurations or data from several cycles of the same target.
- You want to add a non-ALMA single dish (IRAM 30m, APEX, Mopra, SEST, JCMT, Herschel, BGPS, MALT90) as short
  spacings. My tally: 28 lines name one, 18 of them with feathering.

## When not to use

- **Compact sources well inside the MRS.** 2015A&A...576L...2S argued missing short-spacing flux was negligible;
  2017ApJ...850..139W left out the ACA because differences were <~10%; compact C18O and C17O had negligible
  missing flux at the peak in ACA-only data (2025ApJ...994..158G). Check this per line, not per project.
- **Compact-source extraction or core catalogues.** Some papers use the extended data alone for source finding:
  12 m only for core extraction but 12m+7m for lines (2018A&A...618L...5N); an extended-only image for compact
  sources (2018ApJ...855...24P). Use the `core-extraction-cmf` or `source-extraction-counts` skill.
- **The array ratio is the measurement.** 2023ApJ...944...49F kept 12 m and ACA images separate because 12 m flux
  traces the disk and ACA flux the disk plus inner envelope, and used their ratio as an evolutionary indicator.
- **Fitting models to visibilities.** Fit the 12-m and ACA visibilities jointly instead of combining images
  (2021AJ....161..271F with RADMC-3D and emcee; 2019A&A...628A.100D with galario and dynesty; 2018A&A...617A..23B
  with uvmultifit; 2024A&A...689A..41V and 2024A&A...682A.186L for SZ). Use `uv-plane-fitting`. Joint fitting
  does not measure the unsampled zero-spacing flux: the total comes from the model's extrapolation.
  2020ApJ...898..146M calls its total belt flux model-dependent for this reason, and 2021AJ....161..271F notes its
  model-dependent ALMA flux is about half the SCUBA-2 flux.
- **Combining bands** (Band 3 + Band 7, 2017A&A...604A.115V) is a spectral-index problem, not short-spacing
  correction. Match uv ranges instead (2026A&A...705A..96M; common uv coverage via uvsim, 2015ApJ...812..126C).
  Use `spectral-index`.
- **Solar data** follow their own TP calibration and feathering chain (2020A&A...635A..71W with SoAP;
  2018A&A...619L...6N; 2017SoPh..292...87S). 2022A&A...661L...4A notes that cross-normalising datasets cannot
  replace a true absolute calibration. Treat solar TP absolute temperature as a separate problem.

## Steps

1. **Inventory and decide.** Goal: know what arrays exist and what each product will use.
   - Read the MOUS list (12-m TM1/TM2, 7-m, TP) and the 12-m MRS. Several papers make more than one product:
     TP+7m and TP+7m+12m image sets (2020ApJ...894...87C); 7m+TP for one source and 12m+7m+TP for others
     (2021A&A...648A..41V); 12m+7m for continuum and large-scale C18O but 12 m only for small-scale C18O
     (2023MNRAS.522.2384M); feather for some lines, concat for CO, nothing for SiO (2021ApJ...910..148M).
   - Array selection can differ per product: TM1 left out of the line cubes (2021A&A...656A..60A); ACA needed for
     continuum but not for H29alpha (2018A&A...611A..99K); compact data added only when the MRS was smaller than
     the ring radii (2024PASJ...76..437Y). Some authors dropped 7 m and TP because they added noise and artifacts
     (2022A&A...662A...8M) or gave no gain (2022A&A...665A.107T). State your reasons.
2. **Calibrate each dataset separately, then check flux scales.** Goal: datasets agree before merging.
   - "calibrated separately, then combined" is the normal order (2014A&A...570L..14R; 2025A&A...693A.174E;
     2022MNRAS.510.3734D). Re-run the pipeline with QA flag files and flux.csv when needed (2018MNRAS.480.4974H).
   - Compare fluxes on overlapping uv scales: 12-m vs ACA within 10% (2020ApJ...889....9M) or 15%
     (2018ApJ...863..143C); check before combining (2017ApJ...851...83C). Fix mismatches explicitly: rescale
     visibilities in the overlapping uv range (2023A&A...676A...4C), match continuum flux on baselines of similar
     length (2025MNRAS.536..684D), flux-rescale to a common reference (2024A&A...687A.311A; 2026MNRAS.552g1700S),
     or convert TP to the ACA flux scale before feathering (2020MNRAS.491..178K).
3. **Align phase centres, positions, spectral frames and epochs.** Goal: identical sky and frequency grids, and
   data that describe the same source state.
   - Fix positional offsets between short- and long-baseline data (2020ApJ...889L..24P; 20 and 40 mas offsets in
     2019AJ....158...15P). Correct proper motion (2019A&A...625A.118K; 2016ApJ...820L..40A) or assign all epochs
     the first-epoch position (2017ApJ...850L...6A).
   - Tools seen: `fixvis` (2018ApJ...868L...5K), `fixvis` + `fixplanets` to Gaia positions (2021MNRAS.506.1978L),
     `phaseshift` (2024A&A...687A.311A), VisAlign (2022MNRAS.513.5790C; 2025A&A...702A..18D), `fixplanets` + `cvel`
     for a moving target (2016ApJ...821L...8S), relabelling an old frame to ICRS (2023ApJ...954..197I).
   - Convert to a common frame (LSRK) before combining (2016A&A...587A..44P; 2021A&A...645A..49G) and regrid
     channels (`mstransform` to 0.25 km/s, 2018ApJ...852..122H). In `concat`, default `freqtol`/`dirtol` keep
     fields and spws separate (2025A&A...699A..80H); papers set freqtol 10 MHz (2020A&A...641A..97V) or 30 MHz
     (2026A&A...712A.227E).
   - Check observing dates against source variability before merging epochs or reading differences as missing
     flux: comet HDO and H2O about two weeks apart (2025NatAs...9.1476C); solar datasets not simultaneous
     (2017ApJ...845L..19B); epochs combined after scaling the variable Sgr A* flux (2017MNRAS.470.4209Y).
4. **Self-calibrate (12-m multi-configuration).** Goal: consistent gains across configurations. Patterns the
   pack shows, each attributed only to papers that state it:
   - Self-calibrate the short-baseline data, concatenate with long-baseline data, then self-calibrate jointly
     (2018ApJ...869L..41A; 2025ApJ...989...30Z; 2024ApJ...964..190L). 2026A&A...710A.238D self-calibrated the
     short baselines separately only when flux varied by >10%.
   - Joint self-calibration of the concatenated data, earlier stages not stated (2025ApJ...986L..11S;
     2024AJ....167...66Y; after VisAlign and statwt, 2022MNRAS.513.5790C).
   - Self-calibrated short-baseline data combined with long-baseline data, any joint stage not stated
     (2025ApJ...993..120H; 2025NatAs...9.1672Y).
   - Each configuration calibrated and self-calibrated individually, then combined (2019ApJ...873...73Z;
     2019ApJ...883...98Z).
   - The pack does not show which pattern is most common.
5. **Continuum subtraction: before or after concatenation.** Goal: line-only visibilities without losing the
   continuum you need for self-calibration.
   - Before concatenation: 2020ApJ...889....9M; 2018A&A...616A..34H; 2021ApJ...908....8C; 2019ApJ...881L..42C.
   - After concatenation: `concat` then `uvcontsub` (2021ApJ...908..231M); combine, self-calibrate on the
     continuum, then subtract it (2014A&A...570L..14R).
   - Either order works if the line-free channels are the same in every dataset. Self-calibrate on data that
     still contain the continuum, apply the gain tables to the line data, then subtract. Record line-free
     channels and fit order; the cards often omit them (see Pitfalls). Subtract TP continuum too (order-one
     polynomial, 2024MNRAS.530..597B).
6. **Set relative visibility weights.** Goal: each array contributes according to its real sensitivity.
   - Check the weights before trusting `concat`. ACA/12-m examples: 7m weight 0.116 against 1 for 12 m
     (2024A&A...688A..30B, simulated data); ACA weights x0.3 (2014A&A...570L..14R) or 0.25 (2017A&A...605A.126R);
     ACA downweighted by 0.41 (2025ApJ...990..150A) or weighted x2.4 (2021A&A...650A.202R); ACA/12-m ratio 0.18
     (2020A&A...633A..13D); ACA:TM1:TM2 about 1:5:6 from sensitivity (2018A&A...616A..34H); empirical noise-based
     weights (2019Natur.569..519K); equal weights for 7 m and 12 m (2025ApJ...979..217S); default weights kept
     after checking they matched (2020A&A...634L..12D); `statwt` (2016ApJ...832..158Z; 2017ApJ...835..174S).
   - These numbers are different quantities (multipliers, resulting ratios, per-array factors), and 0.41 and 2.4
     are reciprocal choices. Work out what your weights are normalised to before reusing any of them. General
     background: with equal Tsys, bandwidth and time, a 7m-7m baseline carries (7/12)^4 = 0.116 of a 12m-12m
     baseline's weight. Data whose weights already reflect sensitivity need no extra factor; adding one
     double-counts.
   - Configuration and cycle reweighting: one dataset weighted 0.2 (C40-3, 2023MNRAS.522.4078C; TM0,
     2020A&A...642A..93H) or lower-resolution data 1/10 (2016ApJ...829L..10I); `visweightscale` factors 0.6 and 0.2
     (2026ApJ..1005...94N); 1:4 for a high-resolution product and 1:1 for a total-flux product
     (2022A&A...664A..63X); inverse error variance (2023ApJ...954..197I; 2020ApJ...892L..18I); cycle data
     reweighted with `statwt` (Cycle 1, 2023ApJ...945...69R; 2019ApJ...871...37H; oldstatwt, 2021Sci...371..713L). My count:
     11 papers name `statwt` in their combination settings.
   - General practice: inspect weights per array with `plotms` (weight vs uv distance) before and after.
7. **Combine 12-m and 7-m interferometric data.** Goal: one deconvolution over all baselines.
   - My tally: 150 `array_combination` lines name both 12-m and 7-m/ACA data. Most concatenate (`concat`,
     2015Natur.527...70P; 2021ApJ...908..231M), pass both to one `tclean` with the mosaic gridder
     (2023A&A...678A.160E; 2025A&A...701A.219N), image jointly, or do not say how. Use `copypointing=False` in
     `concat` when not mosaicking (2018MNRAS.481.4931E).
   - Less common: clean 12-m and 7-m separately and feather the images (2019ApJ...871..170M; 2016ApJ...826...26T;
     2020ApJ...896...36T, who found a visibility-domain combination gave similar results); a hybrid of separate
     deconvolution then joint imaging with a union mask (2019ApJ...885...50W); or the ACA image as
     `startmodel`/`modelimage` for the 12-m clean, then feather (2018ApJ...863..143C; 2020A&A...635A...2S).
8. **Add Total Power or another single dish.** Goal: restore the zero and shortest spacings. Categories follow
   the authors' own wording. My tally: 85 lines combine ALMA TP (including solar full-disk TP maps). 56 say they
   feathered (e.g. 2024MNRAS.530..597B; 2017ApJ...841..110S; 2021PASJ...73..205T; 2025A&A...702A.133K), 3 use the
   single dish as a clean model and then feather, 1 uses the TP cube only as the `tclean` model
   (2021A&A...645A..97Q), 1 says "Fourier space" (2019Natur.569..519K), 4 use TP2VIS, 4 make pseudo-visibilities,
   1 uses MIRIAD `immerge` (2026ApJ..1001...33L), and 15 do not state the method.
   - **Image combination (feathering).** Feathering is itself a weighted sum of the two images in the Fourier
     domain, so "combined in Fourier space" (2019Natur.569..519K; 2016ApJ...826...26T) belongs here. In CASA:
     `imregrid` the single dish to the interferometer grid, then `feather(imagename, highres, lowres)`;
     `sdfactor` 1.0 is the stated value (2018ApJ...867..111Z; 2024A&A...688A..30B), and several papers say
     "default parameters" (2017SoPh..292...87S; 2021MNRAS.503.4320F; 2019MNRAS.486..283B). The PHANGS-ALMA pipeline
     does channel regridding, continuum subtraction, `tclean`, primary-beam correction, feather with TP and
     convolution to a round beam (2025ApJ...988..162D; 2021ApJS..257...43L). Staged feathering also appears: ACA
     with TP first, then the result with the 12-m cube (2024A&A...691A..70N).
   - **Primary-beam convention for feathering.** Pick one branch and keep it (general practice):
     (a) apparent-sky branch: feather the interferometer image that is not PB-corrected with a single-dish map
     multiplied by the interferometer (mosaic) PB response, then PB-correct the result once. The pack shows the
     single-dish x PB step (2019A&A...623A..96Y; 7m PB applied before pseudo-visibilities, 2026A&A...707A.120H),
     PB correction after feathering (2020ApJ...894...72S), and the whole chain: JCMT `imregrid`, x ALMA PB,
     `feather`, then divided by the PB (2025ApJ...985..166K; the last step is in its card, the pack line is cut).
     (b) PB-corrected branch: PB-correct the interferometer image first, feather with the unattenuated
     single-dish map, and mask the result to the PB footprint; the PHANGS order lists PB correction before
     feathering (2025ApJ...988..162D).
     Never feed a PB-corrected interferometer image together with a PB-multiplied single-dish map, and never
     PB-correct twice. Both errors give position-dependent flux errors that grow toward the mosaic edge.
   - **Single dish as a clean model (MACF and relatives).** TP regridded and used as the clean model, then
     feather (2017A&A...605A..28D); Model-Assisted Cleaning plus Feather, the single-dish image in Jy/pixel as
     `tclean` startmodel then feathered (2023PASP..135c4501P; 2024A&A...688A..30B); feathered ALMA+APEX or
     ALMA+Mopra cube used as the model for a new clean (2013ApJ...774...73I; 2013Natur.499..450B); 12m+7m cleaned
     with the TP image as model, positive clean components feathered with TP, then cleaned again
     (2018MNRAS.475..448T).
   - **Joint deconvolution with a single-dish image.** `sdintimaging` (SDINT), compared with other methods in
     2023PASP..135c4501P; 12m+7m combined in visibility space, then joint deconvolution with APEX
     (2026ApJ..1003...68Y; the card does not say how the APEX cube was regridded or scaled).
   - **Single dish converted to visibilities.** TP2VIS with TP weight from the TP map rms (2018ApJ...867..166S);
     per-antenna `sdimaging`, reframed to the ACA channels, weighted TP image, TP2VIS, joint `tclean` with ACA
     (2021A&A...653A..53A); TP2VIS with 7m and TP weights scaled by 5 and 20, jointly deconvolved in MIRIAD
     (2023ApJ...949..108K); `tp2vistweak` (2026A&A...707A.252K). Pseudo-visibilities in GILDAS/MAPPING
     (2017A&A...601L...9G; 2018A&A...618A..35G), TP to ACA over 0-5 m and then to 12 m over 0-12 m
     (2025A&A...696A.100G), IRAM 30m to 7m over 0-7 m after multiplying by the 7m primary beam
     (2026A&A...707A.120H); SD2VIS after main array + ACA (2017A&A...605A.126R).
   - **Unit conversion first.** Put the single dish in Jy/beam with a stated factor: APEX Tmb x39
     (2013ApJ...774...73I); Mopra 16.2 Jy/K and IRAM 6.15 Jy/K (2017ApJ...835..265W); ALMA TP 41 Jy/K
     (2019ApJ...887...88E) or about 41.5 (as printed in 2021MNRAS.500.5500B).
   - **Continuum single-dish maps at another wavelength need a spectral conversion first.** Herschel 500 um
     scaled to 3 mm (2014ApJ...795L..25R; graybody beta = 1.2, Tdust = 20 K, 2016ApJ...832..143F); BGPS-combined
     continuum scaled by ~0.6 with alpha_nu = 3.75 (2022MNRAS.514..578W); an 18" 1.3 mm map extrapolated from a
     Herschel + APEX/ArTeMiS SED, merged with ACA by the J-comb uv-domain algorithm (2026A&A...708A.251X); beta =
     1.8 assumed to compare ACA 1.2 mm with SCUBA-2 850 um (2020ApJ...895..119T). 2018ApJ...856..147O feathered
     Herschel 250 um without a conversion shown in the pack. Scale with a stated spectral index or SED fit,
     propagate the temperature and spectral-index uncertainty, and use the same brightness unit and correct
     beam metadata before feathering or comparing recovered flux.
9. **Image and restore.** Goal: a deconvolved cube with a known beam and flux scale.
   - Settings seen are in the parameter table; most are single-paper examples, so set thresholds from your own
     rms. With multi-configuration data the dirty beam is not Gaussian; papers apply the JvM (Jorsater & van
     Moorsel) residual rescaling (2023A&A...669A..53B; 2024A&A...689A.145S; 2021ApJS..257....6G;
     2023ApJ...949..108K) or correct CLEAN-beam versus dirty-beam scaling (2021ApJ...906..111T). TP2VIS imaging
     lost flux with too few iterations (2021A&A...653A..53A). Report beam, rms, and which arrays went into each
     product.
10. **Verify flux recovery.** See Verification checks. Do this before any mass or column density.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| TP combination method (authors' wording) | feather | SD as clean model, MACF, TP2VIS, pseudo-visibilities, sdintimaging, immerge | 56 feather of 85 ALMA TP lines (my tally) | 2024MNRAS.530..597B, 2021A&A...653A..53A, 2025A&A...696A.100G |
| 12m+7m method | visibility concat or joint `tclean` | separate clean + feather; ACA image as model; hybrid | most of 150 lines naming 12 m and 7 m (my tally) | 2021ApJ...908..231M, 2025A&A...701A.219N, 2019ApJ...871..170M |
| ACA/12-m weight factor | not stated by most cards | 0.116, 0.25, 0.3, 0.41, x2.4 (different normalisations) | 1 each | 2024A&A...688A..30B, 2017A&A...605A.126R, 2014A&A...570L..14R, 2025ApJ...990..150A, 2021A&A...650A.202R |
| Resulting ACA/12-m weight ratio | not stated by most cards | 0.18; ACA:TM1:TM2 about 1:5:6 | 2 | 2020A&A...633A..13D, 2018A&A...616A..34H |
| Per-configuration weight | unscaled | 0.2; 1/10; 1:4 for high-res products | 4 | 2023MNRAS.522.4078C, 2020A&A...642A..93H, 2016ApJ...829L..10I, 2022A&A...664A..63X |
| `statwt` reweighting after merging | named in 11 papers (my count) | `oldstatwt` for old data | 11 | 2017ApJ...850...83F, 2023A&A...679A.119R, 2021Sci...371..713L |
| TP2VIS weights | TP weight from TP map rms | 7m x5, TP x20 (MIRIAD) | 2 | 2018ApJ...867..166S, 2023ApJ...949..108K |
| Feather `sdfactor` | 1.0 or "default" | rarely stated (feather parameters flagged not stated in 3 cards) | 2 explicit | 2018ApJ...867..111Z, 2024A&A...688A..30B |
| Single-dish flux scale factor | rarely stated | TP x0.979 (solar); interferometer scaled down 14% to the full-disk map | 2 | 2020A&A...635A..71W, 2018A&A...619L...6N |
| Single-dish K to Jy | rarely stated | APEX 39; Mopra 16.2; IRAM 6.15; ALMA TP ~41 | 4 | 2013ApJ...774...73I, 2017ApJ...835..265W, 2019ApJ...887...88E, 2021MNRAS.500.5500B |
| Pseudo-visibility uv range | 0 up to about the next array's dish diameter | 0-5 m, 0-7 m, 0-12 m | 2 | 2025A&A...696A.100G, 2026A&A...707A.120H |
| Weighting (product not separated) | Briggs robust 0.5 | natural; robust 1, 2, 0, -0.2 | robust 0.5: 42; natural: 11; robust 2: 4; robust 1: 3 (my count) | 2021ApJ...908..231M, 2023ApJ...953..164M, 2025ApJ...990..150A, 2023ApJ...949..108K |
| uv taper | not stated by most cards | 0.6" to 3" | 7 (my count) | 2020ApJ...894...87C, 2018ApJ...863..143C, 2019ApJ...874...89C, 2018ApJ...858...90G |
| Multiscale scales | 0 (point) plus 2-4 larger scales | [0,1,5,10,15] px at 0.2"; 0,2",5",10"; [0,7,21] px; point to 10" | 13 papers name multiscale (my count) | 2018MNRAS.475..448T, 2019A&A...623A..96Y, 2025A&A...701A.219N, 2024MNRAS.530..597B |
| Clean depth | no common choice; single-paper recipes | multiscale to ~4 sigma then single-scale to ~1 sigma (PHANGS); 2-2.5x rms; 5 sigma; ~1 sigma with auto-multithresh | 1 each | 2025ApJ...988..162D, 2025ApJ...990..150A, 2018ApJ...853..111J, 2023A&A...678A.194C, 2023ApJ...953..164M |
| Deconvolver | multiscale for extended emission | Hogbom | multiscale 13; Hogbom 7 (my count) | 2024ApJ...968..131T, 2021A&A...645A..97Q |
| Masking | auto-multithresh | "automask" with the algorithm not named; pbmask 10% | auto-multithresh 5 (my count) | 2024ApJ...968..131T, 2025ApJ...994..158G, 2021ApJ...907L..15S, 2023A&A...678A.194C |
| Overlap-scale flux agreement accepted | within calibration error | 10-15% | 2 | 2020ApJ...889....9M, 2018ApJ...863..143C |

My counts of weighting, deconvolver, masking, taper and `statwt` are unique papers with an `array_combination`
line whose key-parameter lines in the pack mention the setting. The product is not separated: several papers
use natural weighting for lines and robust 0.5 for continuum (2020ApJ...889....9M; 2020ApJ...901..151S) or
different weighting per array (2020ApJ...896...36T; 2025ApJ...990..150A).

Recommendations that follow from this: use visibility-domain 12m+7m combination with checked weights, then
feather with TP under one consistent primary-beam convention (Step 8), because that is the most common route in
the pack. The two systematic comparisons in the pack favour adding the model step: on a simulated sky model
SDINT and MACF raised total-flux recovery above ~92% of the true flux, and on M100 Feather and MACF had the
narrowest A-par distributions (2023PASP..135c4501P); 2024A&A...688A..30B took its 12m + IRAM-30m MACF map as the
reference. So run feather and MACF and compare them. Use TP2VIS, `sdintimaging` or pseudo-visibilities when you
need one joint deconvolution; 2018MNRAS.475..448T found no clear improvement from direct Fourier-plane
feathering over their model-based route. Both comparisons used standard `sdfactor`/`sdgain` values and assumed
aligned flux scales, so tune and check these yourself.

## Software

Counts are mentions in the pack's software aggregate (matched steps only), with version and "casa" prefix
variants merged.

| Software | Mentions | Used for | Examples |
|---|---|---|---|
| CASA (incl. "casa 5.4.1", "casa 5.6") | 190 | calibration, `concat`, `statwt`, `tclean`, `feather` | 2021ApJ...908..231M, 2018MNRAS.480.4974H |
| `tclean` (incl. "casa tclean") | 53 | joint deconvolution of 12m+7m, MACF | 2020ApJ...889....9M, 2025ApJ...988..162D |
| `feather` (incl. "casa feather") | 27 | image-plane TP/single-dish combination | 2016ApJ...832..142Z, 2024ApJ...968..131T |
| GILDAS (MAPPING), CLASS | 11; 4 | single-dish pseudo-visibilities, single-dish reduction | 2025A&A...696A.100G, 2018A&A...618A..35G |
| Miriad | 9 | `immerge`, joint deconvolution with TP2VIS visibilities | 2026ApJ..1001...33L, 2023ApJ...949..108K |
| PHANGS-ALMA pipeline | 9 | full 12m+7m+TP imaging chain | 2025ApJ...988..162D, 2021ApJS..257...43L |
| `uvcontsub`; `imcontsub`; `concat`; `mstransform` | 9; 3; 5; 2 | continuum subtraction, merging, regridding | 2021ApJ...908..231M, 2018ApJ...852..122H |
| TP2VIS | 3 | TP to visibilities, joint deconvolution | 2018ApJ...867..166S, 2021A&A...653A..53A |
| `simobserve`; DC_script | 3; 2 | simulated combinations; comparing combination methods | 2023PASP..135c4501P |
| uvcombine | 2 | feathering: Herschel with SCUBA (no ALMA data in that step); BGPS with ALMA | 2018ApJ...853..171G, 2024ApJ...962...48J |
| almica | 2 | 12m+ACA+TP combination described as uv domain | 2025ApJ...992L..15L |
| SoAP | 2 | solar imaging with TP feathering | 2020A&A...635A..71W |
| sdintimaging; J-comb; FSSC | below the aggregate cut-off | joint deconvolution; uv-domain linear combination; feather-like | 2023PASP..135c4501P, 2026A&A...708A.251X |
| uvmultifit; galario; dynesty | 3; 3; 3 | fitting 12m+ACA visibilities instead of combining images | 2018A&A...617A..23B, 2019A&A...628A.100D |

## Pitfalls

- **12m+7m without TP still misses flux.** The pack has individual cases, measured in different ways, not a
  typical fraction: "even with the ACA only 50% of the extended flux is recovered" (2014A&A...570L..14R, 12m+ACA);
  ACA-only 12CO(2-1) missed 60-70% of the global IRAM 30m flux in M33 (2023ApJ...953..164M); interferometric
  flux 70% of single-dish flux (2024A&A...689A.122B); ALMA-ACA recovered 8.4 of ~29 Msun (2018ApJ...856..147O, a
  mass comparison); ACA alone recovered 41% and 21% of SCUBA-2 flux in two cores (2020ApJ...895..119T, with an
  assumed beta); [CI] flux 34±15% lower than Herschel (2018ApJ...863..143C). Treat masses from such maps as
  lower limits, as 2017ApJ...837...60B and 2021A&A...648A..41V (outflow masses) did.
- **Filtering changes shapes and peaks, not only totals.** 2018ApJ...856..147O fitted p=4.0 to the ALMA-ACA
  profile against p=1.6 from Herschel and said the ALMA-ACA density profile cannot be discussed; ACA-only CO
  envelope sizes were underestimated by a factor of two against TP (2021A&A...653A..53A); in simulation the
  interferometer-only peak of the brightest compact source fell by ~40% (2023PASP..135c4501P); a smooth model
  underestimated the peak flux (2019ApJ...874...89C). Do not fit profile slopes, widths, sizes or morphology on
  maps that lack the relevant spacings.
- **Missing flux is channel and line dependent.** Negligible at line edges but 30-40% in central channels
  (2015ApJ...814..143A); interferometer alone ~0.15 of the NRO45 flux, feathered map ~0.8 (2019ApJ...872..121U).
  Line ratios between a combined and an uncombined line are biased: ACA CO(1-0) that resolves out extended
  emission could inflate r21 (2024MNRAS.527.4420M). 2024MNRAS.527.1444A dropped an ALMA flux from a radio
  spectral fit because of missing short spacings.
- **Deconvolution does not conserve flux** in combined data (2026ApJ..1001..184M), and too few iterations lose
  flux (2021A&A...653A..53A). Check residuals and the JvM factor (Step 9).
- **Single-dish flux scale.** 2020A&A...635A..71W rescaled a solar TP map by 0.979 and still calls the absolute
  TP scale "less certain". In a Herschel + SCUBA feather (no ALMA data in that step), 2018ApJ...853..171G had to
  scale SCUBA up by ~3 and tested factors of 0.5-10x, which shows how far single-dish scales can disagree.
  Feathering puts any single-dish calibration error directly into the large-scale flux.
- **Cross-frequency continuum maps.** A Herschel, SCUBA, ATLASGAL or BGPS map is not at the ALMA frequency.
  Without an explicit spectral conversion (Step 8) the short spacings or the recovery fraction carry an unknown
  temperature and spectral-index error.
- **Primary beam and mosaic edges.** Mixing the two branches in Step 8 gives position-dependent flux errors.
  2019A&A...623A..96Y notes a CASA mosaic imaging issue that overestimated fluxes by 10%; 2023ApJ...953..164M
  dropped clouds at the field edge where PB correction is uncertain; 2023PASP..135c4501P tested only emission
  inside the well-characterised PB; 2024A&A...691A..70N weighted mosaics to limit edge noise.
- **Unchecked weights.** Data from different cycles can carry weights that do not reflect sensitivity; papers fixed
  this with `statwt` or manual rescaling to match noise variance (2017A&A...605A..42C; 2019ApJ...887...40W).
  Adding a dish-size factor to weights that already reflect sensitivity double-counts (Step 6).
- **Adding arrays can hurt.** 7 m and TP added noise and artifacts (2022A&A...662A...8M); a combination gave no
  gain (2022A&A...665A.107T). Large-scale emission also raises the background for compact-source finding.
- **Positional, frame and epoch mismatches** between configurations, epochs or cycles blur structure or mix
  source states (Step 3). Moving targets need `fixplanets` (2016ApJ...821L...8S; 2023ApJ...948..110Y).
- **Pixels in feathered or combined maps are correlated on the beam scale**; 2017ApJ...845L..19B did not
  correct for this in a pixel-by-pixel comparison. Bin to at least a beam before regressions.
- **Settings the cards flag as not stated.** Specific to combination: feathering parameters (3 cards in the
  aggregate; 2017ApJ...845L..19B; 2013ApJ...774...73I), the TP combination method (2020A&A...633A..13D), relative
  weighting of 12-m and ACA (2018ApJ...856..147O; 2019ApJ...875...96N; 2017ApJ...850L...6A; 2021ApJ...908..231M),
  and the regridding and scaling of APEX data for `sdintimaging` (2026ApJ..1003...68Y). The cards rarely state
  `sdfactor`, `effdishdiam` or `sdgain`, and 2023PASP..135c4501P used "standard values". General settings the
  pack's not-stated aggregate lists most often (counts are per phrasing, so related phrasings are listed
  separately there): CASA version (30) and CASA plus pipeline version (9); line-free channels and continuum
  subtraction (15 and 15, plus many variant phrasings); flux-scale uncertainty (13, plus 6, 5 and 5 with the flux
  calibrator); self-calibration solution intervals (11, plus 8 and 4 with iterations or rounds); image and cell
  size (11 and 5); primary-beam correction details (9 and 4).

## Verification checks

What the papers did:

- **Total flux vs single dish.** Combined maps recovered ~90% of APEX flux (2017A&A...605A..28D;
  2020A&A...633A..13D); ACA+TP feather recovered 99.7% of single-dish flux (2021MNRAS.500.5500B); ALMA total flux
  consistent with Nobeyama 45-m (2020ApJ...901..151S); missing flux vs IRAM 30m <~30% north, ~50% south
  (2020ApJ...903...94M); global CO luminosity of ACA, IRAM 30m and ACA+IRAM compared (2023ApJ...953..164M).
- **Spectra vs single dish at matched resolution.** Feathered cube profile vs IRAM 30-m at 30"
  (2018ApJ...858...90G); 7M+TP spectrum matched the TP profile (2019PASJ...71...85M); feathering,
  interferometer-only and NRO45 spectra side by side (2019ApJ...872..121U).
- **Combined vs single-dish morphology.** Combined and TP images compared to show that 7m filaments are not edge
  artifacts (2024ApJ...968..131T); ACA-only sizes compared with TP sizes (2021A&A...653A..53A).
- **Flux-scale agreement on overlapping uv scales**: 10% (2020ApJ...889....9M), 15% (2018ApJ...863..143C).
- **Gain from adding short spacings.** 12m+ACA recovered 9-24% extra CO over ACA alone in four of six sources
  (2021ApJ...908..231M); TP2VIS combination raised flux by at least 30% (2021A&A...653A..53A).
- **Sensitivity to choices.** ACA weight changes did not affect results (2014A&A...570L..14R); varying the
  relative APEX/ALMA flux calibration changed clump properties by <10% in 12CO and <5% in 13CO
  (2013ApJ...774...73I); visibility- and image-domain 12m+7m combinations gave similar results
  (2020ApJ...896...36T); 10 000 to 100 000 iterations tested with residuals inspected (2021A&A...653A..53A);
  direct Fourier-plane feather tested with no clear improvement (2018MNRAS.475..448T); residual scaling for
  flux consistency with the TP map (2018ApJ...867..166S). The 0.5x-10x scale test in 2018ApJ...853..171G was on a
  Herschel + SCUBA feather, but the same test applies to an ALMA + single-dish feather.
- **Simulation.** Observe a sky model with `simobserve` for each array and run every combination method on it,
  scoring flux recovery, A-par and power spectra against the truth (2023PASP..135c4501P; 2024A&A...688A..30B).
- **External instruments.** Morphology checked against SMA, SHARC2 and VLA; not significantly biased by missing
  flux on scales <~30" (2015ApJ...804...37L).

What a careful referee adds (general practice, not from the pack):

- Smooth the combined cube to the single-dish beam and compare channel by channel, not only the integrated flux.
- Compare the power spectra or radial uv amplitudes of TP, 7m and 12m in their overlap annulus.
- State which arrays went into every product and the MRS of each, and give flux-recovery fractions per line.
- State the primary-beam branch used for feathering and check the flux of a source near the mosaic edge.
- Report the provenance settings listed at the end of Pitfalls (CASA and pipeline versions, line-free channels
  and fit order, flux-scale uncertainty, image and cell size, masks, self-calibration intervals, combination
  weights, feather parameters and JvM factor). Record a value you cannot find as unknown; do not copy a value
  from the parameter table.

## Source cards

Full list: `references/sources.md` (714 papers). Most informative for this technique:

- 2023PASP..135c4501P: comparison of feather, SDINT, MACF and FSSC on a simulated sky and M100
- 2024A&A...688A..30B: simulated filtering bias; 7m weight 0.116, feather sdfactor 1.0, MACF
- 2021A&A...653A..53A: per-antenna TP imaging, TP2VIS, joint tclean; ACA-only sizes vs TP
- 2023ApJ...949..108K: TP2VIS weights, MIRIAD joint deconvolution, JvM correction
- 2018ApJ...867..166S: TP2VIS joint deconvolution, TP weight from map rms
- 2014A&A...570L..14R: ACA weight multiplier 0.3, weight test, 50% recovery even with ACA
- 2018A&A...616A..34H: ACA:TM1:TM2 weights from sensitivity
- 2020A&A...633A..13D: ACA/12-m weight ratio 0.18, ~90% APEX recovery
- 2019Natur.569..519K: noise-based 12m/7m weights, TP combined in Fourier space
- 2025ApJ...988..162D: PHANGS-ALMA pipeline feathering
- 2024MNRAS.530..597B: two 12-m configurations + ACA cleaned together, TP feathered, TP continuum subtraction
- 2019A&A...623A..96Y: IRAM 30m regridded, multiplied by mosaic PB, feathered
- 2013ApJ...774...73I: APEX K-to-Jy factor, feathered cube as clean model, flux-calibration test
- 2017A&A...605A..28D: TP as clean model, feather, ~90% of APEX flux
- 2018MNRAS.475..448T: custom TP-model clean and feather procedure
- 2025A&A...696A.100G: GILDAS pseudo-visibilities TP to ACA to 12 m
- 2023ApJ...953..164M: ACA + IRAM 30m feather, 60-70% ACA-only missing flux
- 2018ApJ...856..147O: ACA missing mass, filtered density profile
- 2018ApJ...863..143C: ACA as model image, flux-scale check, missing [CI] flux
- 2019ApJ...872..121U: interferometer vs feathered flux ratio to NRO45
- 2021ApJ...908..231M: concat 12m+ACA, then uvcontsub, measured flux gain
- 2023A&A...669A..53B: multi-configuration merge with JvM correction
- 2023A&A...676A...4C: visibilities rescaled on overlapping uv ranges before concat
- 2016ApJ...832..143F: Herschel 500 um scaled to 3 mm with a stated graybody
- 2026A&A...708A.251X: J-comb uv combination with an SED-extrapolated single-dish map

=== RECONCILIATION (first review, fixes to keep) ===
# Reconciliation: array-combination
- SR-01 | FIXED | Dropped all four numbers. Pack has no MRS/flux values for 2017MNRAS.468.3266R, 2017ApJ...835..174S, 2017MNRAS.464L..31H or 2020ApJ...893...13M (only their combination or title lines). The 2017ApJ...835..174S card shows that 4.6" came from deliberate uv-clipping, so it was also misused. Replaced with pack-backed limitations (2016PASJ...68...88K, 2018MNRAS.475..448T, 2020ApJ...888L..28S, 2015ApJ...803...60S).
- SR-02 | FIXED | Pack l.594-598: the uvcombine feather and the SCUBA x3 / 0.5-10x test combine Herschel with SCUBA. Removed the row from the ALMA single-dish scale-factor table and relabelled it as a non-ALMA example in Software, Pitfalls and Verification. The ALMA TP scale row keeps only 2020A&A...635A..71W.
- SR-03 | FIXED | Split weighting examples. ACA/12-m `statwt`: 2016ApJ...832..158Z, 2017ApJ...835..174S (pack l.382, 373). General multi-dataset reweighting: 2017ApJ...850...83F (HUDF, l.310), 2017A&A...600A.141K, 2019ApJ...887...40W, 2017A&A...605A..42C.
- SR-04 | FIXED | Recounted unique papers from the key-parameter list that also have an array_combination line, split by product. Line cubes: robust 0.5 in 7, natural in 4. Continuum: robust 0.5 in 6. Unspecified product: robust 0.5 in 5, natural in 3. Every paper is listed in a note under the table; 2020ApJ...889....9M and 2020ApJ...901..151S are counted as natural lines plus robust 0.5 continuum.
- SR-05 | FIXED | Step 4 now ties each stage only to the papers that state it: SB self-cal then joint (2018ApJ...869L..41A, 2025ApJ...989....3D); joint only (2025ApJ...986L..11S, 2024AJ....167...66Y); SB self-cal then combined, no joint stage stated (2025ApJ...993..120H, 2025NatAs...9.1833L); per-configuration (2019ApJ...873...73Z, 2019ApJ...883...98Z). Removed the "most common" ranking.
- SR-06 | FIXED | Moved 2021A&A...656A..60A (TM1 left out of the line cubes) and 2025ApJ...992..103Z (>250 m baselines for one analysis, not source finding either) into a product-specific array-selection bullet in Step 1. The skill now says the pack gives no reason for either choice.
- SR-07 | FIXED | Removed "often holds 20-60%" and "Two mistakes dominate". The summary now names two things to watch without claiming how often they happen. Pitfalls says the cases are individual and labels each one (12m+ACA, mass comparison, ACA-only with assumed beta).
- SR-08 | FIXED | Clean depth is now labelled as single-paper recipes. Deconvolver and masking are separate rows. auto-multithresh is attributed only to 2019PASJ...71...85M and 2021ApJ...908..231M (pack l.229, 767), and "automask" is listed as algorithm not named. TP2VIS gain/iterations sit under clean depth as a 2018ApJ...867..166S example. The skill tells users to set thresholds from their own rms.
- SR-09 | FIXED | Replaced the unconditional recipe with two matched PB branches. (a) Apparent-sky interferometer image plus PB-multiplied single dish, then one impbcor (2019A&A...623A..96Y, 2018MNRAS.475..448T, 2026A&A...707A.120H). (b) PB-corrected inputs with footprint masking (PHANGS order, 2025ApJ...988..162D). Added explicit warnings against mixing the branches or double-correcting. The recommendation, Pitfalls and Verification were updated to match.
- SR-10 | FIXED | 0.3 is now a separate row as an ACA weight multiplier (2014A&A...570L..14R), and 0.18 and 1:5:6 are resulting ratios (2020A&A...633A..13D, 2018A&A...616A..34H). Step 6 warns that the normalisation must be established before either number is reused.
- SR-11 | FIXED | 2026ApJ..1003...68Y now reads: 12m+7m combined in visibility space, then sdintimaging joint deconvolution with APEX (pack l.114, 620-622). Step 8 groups methods as image combination/feathering (with "Fourier space" placed under it), single dish as clean model, joint deconvolution with an SD image, and SD converted to visibilities. The tally is described as the authors' wording.
- SR-12 | FIXED | New Step 5 presents both orders: subtraction before concat (2020ApJ...889....9M, 2018A&A...616A..34H, 2021ApJ...908....8C) and after concat (2021ApJ...908..231M, 2014A&A...570L..14R). It says to self-calibrate on continuum-bearing data, apply the gains, then subtract.
- SR-13 | FIXED | Step 8 and Pitfalls now require a spectral/SED conversion for cross-frequency continuum maps, with propagated T and beta uncertainty and matched units and beam metadata. Cites 2014ApJ...795L..25R (Herschel 500 um scaled to 3 mm, l.158), 2020ApJ...895..119T (beta=1.8, l.645) and 2018ApJ...856..147O (Herschel 250 um feathered, conversion not shown).
- SR-14 | FIXED | Added a "Filtering changes shapes" pitfall (2018ApJ...856..147O p=4.0 vs 1.6, density profile cannot be discussed; 2019ApJ...874...89C peak underestimated). The visibility-fitting bullet now says joint fits do not measure zero-spacing flux (2020ApJ...898..146M, 2021AJ....161..271F).
- SR-15 | FIXED | Added provenance settings to Pitfalls, counted from the pack's not-stated aggregate per phrasing: CASA/pipeline version, line-free channels and fit order, flux-scale uncertainty, image/cell size, self-cal intervals, PB correction. Added a referee check that unknown values be recorded as unknown, not copied from the table.
- SR-16 | FIXED | Step 3 now includes an epoch/variability check (2025NatAs...9.1476C two weeks apart; 2017ApJ...845L..19B not simultaneous; 2016A&A...586A..70L blazar combined per band with sparse time sampling). The Pitfalls bullet was extended to cover it.

Also changed (not raised by Codex): the lower-limit mass example now also cites 2021A&A...648A..41V, which is in the pack (2017ApJ...837...60B is supported only by its card). 2020ApJ...893...13M was removed from Verification.

=== EVIDENCE PACK (array-combination, rebuilt) ===
# Evidence pack: Combining 12m, 7m and Total Power data (`array-combination`)

Scope: recovering extended emission: feathering, joint deconvolution, short-spacing correction

Built from 714 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2013-2026.
Matcher (regex over analysis steps): `feather|joint deconvolution|tp2vis|total[- ]power|\baca\b|7[- ]?m array|combin\w* (?:the )?(?:12|7)[- ]?m|short[- ]spacing`; processing fields: imaging.array_combination
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- star_formation: 350
- nearby_galaxies: 179
- milky_way_ism: 165
- astrochemistry: 163
- protoplanetary_disks: 121
- high_z_galaxies: 98
- agn_and_quasars: 86
- evolved_stars: 45
- galaxy_clusters_and_sz: 24
- debris_disks: 22
- exoplanets: 21
- stellar_physics: 19
- sun: 14
- solar_system: 10
- instrumentation: 6

### Software named in the matched steps
- casa: 183
- tclean: 50
- feather: 21
- gildas: 11
- uvcontsub: 9
- miriad: 9
- astropy: 6
- casa feather: 6
- phangs-alma pipeline: 6
- concat: 5
- class: 4
- emcee: 4
- casa 5.4.1: 4
- astrodendro: 4
- imsmooth: 4
- phangs-alma imaging pipeline: 3
- alma pipeline: 3
- tp2vis: 3
- uvmultifit: 3
- casa tclean: 3
- radmc-3d: 3
- galario: 3
- dynesty: 3
- simobserve: 3
- casa 5.6: 3
- imcontsub: 3
- uvcombine: 2
- photutils: 2
- scipy: 2
- cigale: 2
- uvmodelfit: 2
- almica: 2
- dc_script: 2
- auto-multithresh: 2
- soap: 2
- radio-beam: 2
- mstransform: 2
- casa imregrid: 2
- statcont: 2
- alma-imf data pipeline: 2

### Fitting methods (most common phrasings)
- Gaussian fit to the intensity profile perpendicular to the ridge, implemented in FilFinder: 1
- 2D quadratic polynomial fit (centroid_quadratic) or 2D Gaussian fit (centroid_2dg) for centroiding: 1
- Linear fit to log median points of disk flux vs. envelope flux: 1
- 4th-degree polynomial fit to log10(M_dot) medians and power-law fit to N_proto(<R) via scipy.optimize.curve_fit: 1
- Bootstrapping with 10,000 trials per cloud, using median absolute deviation scaled by square root of oversampling rate …: 1
- Truncated power-law fit to cumulative mass distribution treating N_0 as an independent free parameter; Spearman's rank …: 1
- Order-one polynomial (linear) fits for TP continuum subtraction: 1
- Non-linear least squares Gaussian fits; single, double and triple Gaussians compared with corrected AIC and BIC: 1
- MAGPHYS Bayesian fit returning posterior samples; medians and 68% intervals reported: 1
- Gaussian visibility-plane fitting with CASA uvmodelfit: 1
- Gaussian model; UVMULTIFIT for ACA-only visibilities; TP diameters from deconvolved image-plane major axes.: 1
- Gaussian radial emission distributions.: 1
- chi2 minimisation; uncertainties from post-fit covariance matrix: 1
- Standard radial velocity, abundance and temperature distributions give good fits; fitting algorithm and statistic not s…: 1
- Gaussian fits, no sampler or priors stated: 1
- MCMC; uniform priors except Gaussian priors on i (26.8+/-2.3 deg) and PA (68.25+/-5.55 deg): 1
- Bayesian; uniform centroid prior across ACA field; wide uninformative mass/slope and point-source priors; split-normal …: 1
- Reconstruct dust mass and temperature posterior distributions: 1
- Single-Gaussian fit to each line profile; software not stated: 1
- Least-squares; 1 sigma errors from the diagonal of the covariance matrix: 1
- Affine-invariant ensemble MCMC (emcee), medians and 68% intervals: 1
- least squares minimization of residuals: 1
- Linear regression in log space using LTS_LINEFIT and LTS_PLANEFIT routines of Cappellari et al. (2013): 1
- Static nested sampling with dynesty; significance from Bayes factor against null model: 1
- Gaussian fitting programme for spectral line profiles: 1
- CASA uvmodelfit per integration: 1
- Monte Carlo propagation of uncertainties, 1 sigma intervals: 1
- linear regression with Spearman coefficient and p value (method details not stated): 1
- Plummer-like profile with slope p; Herschel p=1.6, ALMA-ACA p=4.0; priors/likelihood not stated: 1
- Chi-square minimization over the 200,000-model R06 grid in SED Fitter, selecting top 5 best-fit models per source: 1
- Linear proportional function fitting to column density correlations: 1
- Constant flux density and power-law models independently fit to continuum across all four spectral windows.: 1
- Gaussian fit in image plane with imfit to locate emission peak in each execution block: 1
- Elliptical fit to the ring lobes: 1
- Qualitative visual comparison of channel maps and integrated intensity maps (no formal fitting): 1
- Spectral-index fit with errors including rms and absolute flux scaling uncertainties: 1
- MCMC as for stellar fits: 1
- Bessel function fit to uv amplitudes: 1
- Nested sampling with dynesty; priors and likelihood details not stated: 1
- 2D Gaussian fits (ACA); Gaussian fits to spectra giving Vlsr ~4 km/s and width ~5 km/s for H13CO+: 1

### Validation checks used
- Combined and TP images compared to check that 7m sub-structures are not edge artifacts: 1
- Feathers found in 7m data lie inside the extended TP structures, not on edges, so not artifacts; width bias from the ad…: 1
- Median line masses much below critical; statistics of YSO association used as a consistency check: 1
- Limited by 1.6 km/s velocity resolution: 1
- Qualitative visual match of peak widths ~0.01 pc on ~0.1 pc structures and similar column densities: 1
- feathering experiments with SCUBA scaling 0.5x-10x: 1
- Boundary value of 2.4 determined from visual inspection of the sources: 1
- Inspected curves of growth to verify the convolved aperture recovers target flux without large-scale spatial filtering …: 1
- Repeated K-S and A-D statistical tests excluding outliers with R > 1 to confirm conclusions are unchanged: 1
- Compared simple isothermal 870 μm ACA envelope mass estimates with full radiative transfer SED model envelope masses fr…: 1
- Extinction checked with MUSE Balmer decrement; 24 um compared to check embedded SF: 1
- Compared global 12CO(J=2-1) luminosity between ACA, IRAM 30 m, and ACA+IRAM data over the observed region; checked C18O…: 1
- Tuned low significance mask threshold from default 2 sigma to 3 sigma to reject fake emission at cloud edges; compared …: 1
- Compared derived R - sigma_v coefficients and mass function slopes with earlier M33 catalogs (Rosolowsky et al. 2007; C…: 1
- Subtracted diffuse 8 um emission using HIIphot and confirmed the CDF trend does not change.: 1
- Visual inspection of observatory weblog diagnostic plots for calibration issues and visual inspection of cleaned cubes …: 1
- Stop criterion is peak S/N no longer improving between rounds: 1
- Visual inspection to remove data with irregular amplitude or phase values: 1
- Integration range recovers ~99.5% of the flux while keeping S/N >~ 3 per channel; AICc/BIC favour single Gaussian (no b…: 1
- CIGALE comparison and MAGPHYS re-runs without IRAC bands; offsets within the posterior uncertainties: 1
- Compared elliptical and Keplerian masked spectra; used elliptically-masked spectrum to avoid removing real non-Kepleria…: 1
- Repeated uvmodelfit with a range of initial peak location guesses (converging within ∼8%); checked archival high-resolu…: 1
- Tested direct Fourier-plane feather combination; no clear improvement: 1
- Visual noise checks during interactive cleaning; average signal increase of 10 percent after self-calibration.: 1
- Tested 10 000–100 000 iterations; inspected artefacts and residual flux; combination increased flux by at least 30 perc…: 1
- Inspect velocity-dependent fits for spikes, negative regions, missing flux, and poor Gaussian descriptions.: 1
- ACA-only versus TP comparison exposes underestimated or unreliable interferometric sizes.: 1
- Residual images imaged and checked as Gaussian noise; Monte Carlo exploration of chi2 PDFs: 1
- Independent ACA comparison and variation of LTE reference parameters within reasonable limits.: 1
- Upper limit is consistent with the ALMA detection of Circosta+21: 1
- Compared ACA and ALMA spectra from different apertures; flux curve plateaus beyond r_ap ~ 25 arcsec: 1
- Size consistent with the curve-of-growth estimate; zero-baseline flux consistent with the spectral flux within its larg…: 1
- Authors caution that the ACA beam dilutes kinematic signatures and the features cannot be studied in detail: 1
- Peak vanishes progressively for deviating parameters; detection stated as marginal: 1
- Residual systematic intensity errors <~1% stated to be negligible compared with thermal noise: 1
- curves of growth of ACA CO(1-0) for sources with integrated S/N > 5: 1
- Varied relative flux calibration; <10% uncertainty in 12CO clump properties, <5% in 13CO: 1
- SDSS coordinates checked against GAIA and UKIDSS: 1
- Degraded HXMM01 still showed residual at S_res/S_tot=0.05: 1
- Suppression of large-scale arc-like brightness modulations in Band 7 images: 1

### Key parameters and settings (bibcode: value)
- 2024ApJ...968..131T: natural weighting, multi-scale deconvolver, auto-multithresh mask, 1'' x 1'' pixels
- 2024ApJ...968..131T: detection limit 3 sigma = 0.075 K; minimum structure size 600 pixels (1 pixel = 1'' x 1'')
- 2024ApJ...968..131T: skeleton ridge longer than 5 beam sizes; branches shorter than 3 beam sizes discarded
- 2024ApJ...968..131T: adapt_threth = 0.006 pc
- 2024ApJ...968..131T: smooth_size = 0.003 pc
- 2024ApJ...968..131T: SO: assumed density equal to critical density 2e6 cm^-3 and width 1500 AU
- 2024ApJ...968..131T: processing.imaging.array_combination = TP images for C18O and SO regridded to the 7m pixel scale and combined with the 7m image using CASA feather
- 2018ApJ...853..171G: constant T=20 and 50 K maps plus SED-temperature maps; SCUBA scaled by 3x
- 2018ApJ...853..171G: processing.imaging.array_combination = 7m+12m (and TP) combined into single dataset
- 2023ApJ...944...49F: Area ratio < 1.3: unresolved; 1.3 to 2.4: compact; > 2.4: extended; shared continuous half-max contour: multiple; 12 m disk outside half-max contour: offset
- 2023ApJ...944...49F: 6" (~2500 au) aperture radius convolved with beam FWHM; 5-sigma detection threshold
- 2023ApJ...944...49F: R = 0.5 threshold separating envelope-dominated (R < 0.5) from disk-dominated (R > 0.5) sources
- 2023ApJ...944...49F: R bin width = 0.0055 for median infall rate fit
- 2019Natur.569..519K: A_Halpha = 0.5 mag extinction correction
- 2019Natur.569..519K: processing.imaging.array_combination = 12-m + 7-m with empirical noise-based weighting; total power combined in Fourier space
- 2023ApJ...953..164M: natural weighting
- 2023ApJ...953..164M: threshold ~ 1 sigma noise level
- 2023ApJ...953..164M: Convolved circular beam = 7.5'' (30 pc)
- 2023ApJ...953..164M: High significance mask > 4 sigma in 3 continuous velocity channels; low significance mask > 3 sigma in 3 continuous velocity channels over 7.5'' beam
- 2023ApJ...953..164M: Local maxima merge threshold: T_max - T_merge >= 2 sigma; minimum spatial separation = 7.5''; minimum spectral separation = 7 km/s
- 2023ApJ...953..164M: Radius conversion coefficient = 1.91; channel width Delta V_chan = 0.7 km/s
- 2023ApJ...953..164M: Completeness limits: 5 x 10^4 M_sun (ACA+IRAM catalog) and 8.4 x 10^4 M_sun (Corbelli et al. 2017 catalog)
- 2023ApJ...953..164M: Strong 8 um emission threshold > 2 MJy sr^-1; cloud mass threshold = 10^5 M_sun
- 2023ApJ...953..164M: processing.imaging.array_combination = Combined ACA 7 m-array 12CO(J=2-1) data with IRAM 30 m data using feather task
- 2024MNRAS.530..597B: Multi-scale clean scales: point sources, 0.5, 1, 2.5, 5, and 10 arcsec
- 2024MNRAS.530..597B: Circular synthesized beam FWHMs: 55, 80, 90, 120, and 150 pc
- 2024MNRAS.530..597B: TP continuum subtraction: order-one polynomial (linear)
- 2024MNRAS.530..597B: processing.imaging.array_combination = Two 12 m-array configurations and 7 m ACA imaged and cleaned together; combined with TP cubes using CASA feather task
- 2025A&A...693A.286S: 1 to 3 rounds in most cases, solution interval starting at inf and decreasing by factors of two; S/N gain factor 1.7 on average; applied for 12 targets
- 2026A&A...706A.174A: Cube mask 16″ x 10″ elliptical; velocity binning about 100 km/s
- 2021A&A...655A..42S: pixel size 1/5 of the beam minor axis
- 2021A&A...655A..42S: Sunburst B4 continuum: channels within 250 km/s of CO(4-3) and [CI] excluded
- 2021A&A...655A..42S: integration range -0.85 to +0.85 times best-fit Gaussian FWHM
- 2021A&A...655A..42S: upper limits: 3 sigma point source, fixed 200 km/s range at best available redshift
- 2021A&A...655A..42S: CIGALE test: same stellar templates and attenuation law as MAGPHYS, delayed exponential SFH, nebular emission, Dale 2014 dust templates with alpha_SF 0-4 and f…
- 2023NatAs...7..684K: cell size = 0.5", image region = 20"x20", velocity integration range = -14.5 to 25.5 km s-1, elliptical aperture radius = 5.0"
- 2023NatAs...7..684K: uvmodelfit channels = ±10 km s-1 from source velocity, 20 iterations (converging after ∼8)
- 2016ApJ...832...37G: threshold 70 µJy, 1000 iterations, taper 1 arcsec
- 2016ApJ...832...37G: processing.imaging.array_combination = Feathered with SCUBA-2 map
- 2019ApJ...875...96N: robust = 0.5
- 2019ApJ...875...96N: processing.imaging.array_combination = Band 7 ACA data combined with 12m data for continuum imaging after phase shift
- 2018MNRAS.475..448T: natural weighting, 0.2 arcsec pixel, multiscale [0,1,5,10,15]
- 2018MNRAS.475..448T: processing.imaging.array_combination = 12 m + 7 m cleaned jointly with TP image as model, feathering of positive clean components with TP, then clean again
- 2021A&A...653A..53A: Two peak-emission channels for self-calibration.
- 2021A&A...653A..53A: Högbom; Briggs robust = 0.5; 10 000 iterations.
- 2021A&A...653A..53A: Interactive channel masks for sources brighter than 20 Jy.
- 2021A&A...653A..53A: AI Vol, AFGL 3068, R Dor, IRC-30398; CO(2–1).
- 2021A&A...653A..53A: Multiscale; 100 000 iterations.
- 2021A&A...653A..53A: Position, flux, major axis, minor-to-major axis ratio, and position angle.
- 2021A&A...653A..53A: Central-channel Gaussian major axes and axis ratios.
- 2021A&A...653A..53A: Error: average error from the two channels on each side of the central velocity channel.
- 2021A&A...653A..53A: processing.imaging.array_combination = Per-antenna sdimaging; reframe to ACA frequencies/channels; weighted TP image; tp2vis; joint tclean with ACA.
- 2018A&A...617A..23B: natural weighting; 1 or 2 km/s channels
- 2018A&A...617A..23B: Gaussian position, flux density, FWHM; delta component at same position
- 2018A&A...617A..23B: processing.imaging.array_combination = Main array + ACA combined in visibility plane with antenna-specific weighting; TP feathered in image plane
- 2024A&A...692A..86H: ACA covers the whole emission; NOEMA comparison uses R<1.5 arcsec.
- 2024A&A...692A..86H: Reference model, as printed: mass-loss rate 2.4 M⊙ yr−1; terminal velocity 8 km s−1; SiO/H=10−5.
- 2024A&A...692A..86H: SiO density 1.5 SiO/cm3 at 165 au, multiplied by a Gaussian with e-folding radius 215 au.
- 2024A&A...692A..86H: Radial velocity: 2 km s−1 at 17 au, increasing to 2+6(1−0.1/r)^0.8.
- 2024A&A...692A..86H: T(K)=100(210/r[au])^0.78.
- 2021A&A...654L...8C: native channel width 5.45 km/s
- 2021A&A...654L...8C: Briggs weighting, robust = 0.5
- 2021A&A...654L...8C: 3 sigma upper limit S_106GHz < 0.5 mJy/beam
- 2021A&A...654L...8C: ACA spectra rebinned to 160 km/s; single broad Gaussian per aperture; ALMA-t fluxes from elliptical apertures (a=15, b=10 arcsec and a=20, b=15 arcsec)
- 2021A&A...654L...8C: Gaussian FWHM = 300+-80 kpc
- 2021A&A...654L...8C: v in [-300, 300] km/s; threshold 0.04 Jy/beam km/s
- 2017ApJ...850L...6A: best PA ~140 deg, i ~45 deg, peak at ~23''
- 2017ApJ...850L...6A: processing.imaging.array_combination = ACA and 12-m data combined in images; ACA epochs assigned the first-epoch position before combining
- 2026ApJ..1001..184M: robust = 1.0
- 2026ApJ..1001..184M: relative VLA/GBT weights set manually by resetting system temperature columns
- 2026ApJ..1001..184M: processing.imaging.array_combination = 12m + 7m jointly imaged in CASA, then feathered with total power (2013.1.00857.S)
- 2024MNRAS.527.4420M: bin widths 100 km/s for non-detections, 50 km/s if S/N high enough
- 2024MNRAS.527.4420M: aperture ~30 arcsec diameter (~80 kpc at median z)
- 2013ApJ...774...73I: APEX conversion Tmb to Jy/beam multiply by 39
- 2013ApJ...774...73I: processing.imaging.array_combination = APEX + ALMA with CASA feather
- 2022A&A...661L...4A: Band 7 beam FWHM = 21 arcsec; scan duration = 3 min
- 2021AJ....161..271F: 22 free parameters (Model 1), 24 (Models 2, 3)
- 2021AJ....161..271F: Surface density zero inside 70 au and beyond 600 au for Models 2 and 3
- 2018A&A...619L...6N: processing.imaging.array_combination = feather with full-disk TP image, interferometric flux scaled down for 14% excess
- 2021A&A...650A.153D: Free SZ centroid, mass parameter, and inner slope
- 2021A&A...650A.153D: Unresolved sources: point models with power-law spectra
- 2021A&A...650A.153D: Herschel upper limits: average fluxes in BCG-centered apertures with sizes equal to the respective beams
- 2021A&A...650A.153D: processing.imaging.array_combination = Band 3 and Band 4 ACA observations combined in Compton y units for display only
- 2025ApJ...994..158G: Hogbom deconvolver, Briggs robust 0.5
- 2025ApJ...994..158G: AUTO-MULTITHRESH masking, parameters as Kepley et al. 2020 Table 2
- 2025ApJ...994..158G: pixel size 1.1 arcsec, primary beam correction applied
- 2025ApJ...994..158G: common circular beam 7.5 arcsec
- 2025ApJ...994..158G: Integration velocity range 105-145 km/s for 12CO and 122-129 km/s for the other three lines
- 2025ApJ...994..158G: processing.imaging.array_combination = ACA and TP combined with CASA feather (12CO and 13CO only)
- 2016A&A...595A.117J: processing.imaging.array_combination = 12 m and ACA combined before final imaging
- 2024PSJ.....5..221C: pixel size 0.5''; 30''-diameter circular mask; threshold 2 x RMS
- 2024PSJ.....5..221C: RMS noise multiplied by 1.29 for adjacent-channel correlation
- 2019MNRAS.487.4037D: Free: Pei, rs (uniform priors), point-source position, flux, spectral index; kappa Gaussian, eta exponential hyperparameters
- 2017AJ....154..206L: 35 impact parameters up to 1000 km; Lorentz width 0.075 cm-1/bar, alpha 0.5 (HC3N 0.1, 0.75)
- 2025A&A...703A..15M: processing.imaging.array_combination = Multi-epoch 12-m observations concatenated with CONCAT and reweighted with STATWT
- 2018A&A...617A.129K: processing.imaging.array_combination = The three V4332 Sgr datasets were combined
- 2015ApJ...808..102K: processing.imaging.array_combination = tracks combined in the invert-Fourier transform step
- 2023PASP..135c4501P: 12m (7m): 52 (17) fields, each visited 30 (90) times per session, 10 s integration per field
- 2023PASP..135c4501P: Skymodel 4096^2 pixels of 0.05'' (204.8'' per side)
- 2023PASP..135c4501P: Standard (default-like) values for briggs, sdfactor (Feather, MACF) and sdgain (SDINT); numbers not given
- 2023PASP..135c4501P: MACF: SD image (Jy per pixel) used as tclean startmodel, then feathered with the SD image
- 2026MNRAS.546ag037E: 230 GHz (ACA, Cygnus X-1 archival, GX 339-4 archival); 104 GHz (GRS 1915+105 archival)
- 2014A&A...570L..14R: ACA weight factor 0.3
- 2014A&A...570L..14R: processing.imaging.array_combination = Main array and ACA combined, ACA weighted down by factor 0.3
- 2013Natur.499..450B: Briggs robust 0.5
- 2013Natur.499..450B: processing.imaging.array_combination = CLEANed ALMA feathered with Mopra; combined cube used as prior for a new CLEAN deconvolution
- 2024A&A...689A..41V: Mostly flat priors; Gaussian priors on calibration and redshift
- 2024A&A...689A..41V: Evidence convergence threshold Δln B = 0.01
- 2024A&A...689A..41V: A = 1177.0 km/s, alpha = 0.364
- 2024A&A...689A..41V: processing.imaging.array_combination = Modeling in uv-plane with each pointing modeled individually, combined at likelihood level; joint ALMA+ACA imaged map for display
- 2020AJ....159..215L: Trot = 23 K
- 2020ApJ...890..167T: robust = 0.5; 2 km/s velocity resolution
- 2020ApJ...890..167T: processing.imaging.array_combination = interferometric and TP images combined with feathering
- 2015A&A...576L...2S: µ = 49 ± 5
- 2021A&A...650A.117N: processing.imaging.array_combination = combined C40-6 and C40-3 12m runs in tclean
- 2021A&A...647A..10G: η_mb = 0.74 at ∼ 168 GHz (IRAM 30m); η_mb = 0.71 (SOFIA/GREAT)
- 2021A&A...647A..10G: 5'' aperture toward (+10'', -10'') for ALMA SH+ line profiles
- 2021A&A...647A..10G: Beam coupling factors for Herschel/HIFI SH+: f_b ≃ 0.4 at ∼ 526 GHz and f_b ≃ 0.6 at ∼ 683 GHz
- 2021A&A...647A..10G: processing.imaging.array_combination = 12 m array combined with Total-Power (TP) single-dish maps (at 19'' resolution) as zero- and short-spacings; image synthesis steps described in Goicoechea et a…
- 2022ApJ...939L...6B: integration time = 6 sec (ALMA 12-m) and 10 sec (ACA)
- 2022ApJ...939L...6B: detection threshold > 3 sigma
- 2022ApJ...939L...6B: sideband flux agreement within 20%
- 2014A&A...569L...5M: v_LSR = 10.50 km/s from HCO+ J=4-3
- 2026MNRAS.548ag325W: processing.imaging.array_combination = High angular resolution (2015.1.00631.S) and lower angular resolution (2013.1.00280.S) data combined in Epoch 1; 2017.1.00789.S and 2018.1.00717.S in Epoch 2
- 2019MNRAS.488.1005P: processing.imaging.array_combination = All spectral windows combined in imaging; multiple observing blocks concatenated with proper motions accounted for
- 2014ApJ...795L..25R: processing.imaging.array_combination = ALMA combined with Herschel 500 um scaled to 3 mm via CLEAN in CASA
- 2017A&A...604A.115V: processing.imaging.array_combination = Band 3 and Band 7 maps combined with CASA Feather into M3
- 2014MNRAS.444.1821F: processing.imaging.array_combination = Band 6 and 7 combined image made with CASA
- 2024RAA....24f5011X: uvcontsub linear fit (order 1); line channels flagged using model spectrum widened to 50 km/s
- 2024RAA....24f5011X: briggs robust 0.5; noisethreshold 5 sigma; sidelobethreshold 1.25 sigma; line cubes multiscale [0,5,15]; pblimit 0.2; image 108x108 pix, 1 arcsec cell
- 2024RAA....24f5011X: edge channels (~2x128 per SPW) flagged in the first data release; no self-calibration
- 2024RAA....24f5011X: gas-to-dust ratio 100
- 2024RAA....24f5011X: kappa = 1 cm2/g at ~230 GHz (Ossenkopf & Henning 1994, thin ice mantles)
- 2024RAA....24f5011X: eta = 2.4 for deconvolved size
- 2024RAA....24f5011X: mu_H2 = 2.81; mu_p = 2.37; channel width 1.34 km/s; m_H2CO = 30 m_H
- 2024RAA....24f5011X: 30 sources with line width > 7 km/s (outflow wings) assigned an averaged observed velocity dispersion of 1.66 km/s
- 2024RAA....24f5011X: ASHES continuum images cropped to the QUARKS field size
- 2024RAA....24f5011X: linear regression on combined sample in log(DGF) vs log(L/M)
- 2018ApJ...856..147O: Filament PA=146.3 deg from 2D Gaussian fit on Herschel
- 2018ApJ...856..147O: processing.imaging.array_combination = 12-m and ACA combined in the uv plane; Herschel 250 um feathered with CASA feather
- 2022ApJ...927..218H: Foreground extinction A_V range [0, 250] mag
- 2022ApJ...927..218H: Fixed distances D = 398 pc (Orion A), 404 pc (Orion B), 404 pc (lambda Orionis)
- 2022ApJ...927..218H: Disk outer radius constraint < 140 au (except G192)
- 2022ApJ...927..218H: Outflow cavity effective opening angle constraint |Theta_400^Fitter - Theta_400^obs| < 1 deg
- 2022ApJ...927..218H: Magnetospheric truncation radius R_trunc = 5 R_* and hot spot fractional area f_spot = 0.007
- 2022ApJ...927..218H: PEACHES-matched criteria: L_bol > 1 L_sun and 3 sigma methanol detection
- 2022ApJ...927..218H: processing.imaging.array_combination = TM1 + TM2 + ACA combined
- 2019ApJ...881...43K: 2.5 km/s channels; clean to 2.5 x RMS; masked at 5 sigma
- 2019ApJ...881...43K: processing.imaging.array_combination = 12 m interferometric images feathered with TP; ACA excluded
- 2023ApJ...949..108K: 7m weight scale = 5, TP weight scale = 20, Briggs robust = -0.2, cell size = 0.25''
- 2023ApJ...949..108K: Channel widths = 5, 2, and 1 km/s; conversion T_b [K] = 25.4 S_nu [Jy]
- 2023ApJ...949..108K: processing.imaging.array_combination = TP cube converted to visibilities with TP2VIS; 7m and TP weights scaled by 5 and 20; jointly deconvolved with 12m+7m+TP in MIRIAD with Jorsater & van Moorsel (…
- 2024ApJ...962...88V: Briggs robust = 0.5
- 2024ApJ...962...88V: channel width 5.08 km/s, LSR, radio definition
- 2024ApJ...962...88V: multi-scale clean scales 0, 5, 10 arcsec, S/N ~ 4 threshold
- 2024ApJ...962...88V: APEX main beam efficiency 0.80 (PI230)
- 2024A&A...682A..55M: processing.imaging.array_combination = Phase centres aligned via Gaussian fit, shifted to common J2000 15h39m27.750s -34d46m17.692s, and concatenated (4 datasets for continuum; 2018.1.00271 + 2015.1…
- 2025A&A...699A..80H: processing.imaging.array_combination = concat calibrated datasets into one ms; default freqtol and dirtol retain separate fields and SPWs; tclean handles combination.
- 2021MNRAS.508.5259M: Spatial Gaussian kernels: 3, 6, 9''; spectral kernels: 60, 120, 180, 240, 300, 360 km/s; moment 0 detection threshold = 5 (median absolute deviation noise); mi…
- 2023A&A...676A...4C: Five final frequencies: 88, 100, 141, 249, and 348 GHz
- 2023A&A...676A...4C: Shortest common baseline cut: 9.8 klambda
- 2023A&A...676A...4C: Self-calibration solution intervals: inf (gaintype='G'), 60s (gaintype='T'), 10s (gaintype='T')
- 2023A&A...676A...4C: processing.imaging.array_combination = Visibilities rescaled in overlapping uv-distance ranges and combined in uv-plane using CASA concat task
- 2019ApJS..244...40L: processing.imaging.array_combination = data from different projects for the same source are not combined
- 2018ApJ...869L..41A: processing.imaging.array_combination = Compact self-calibrated first, then combined with extended data and self-calibrated jointly
- 2019ApJ...872..121U: robust = 0.5
- 2019ApJ...872..121U: processing.imaging.array_combination = interferometer and TP maps combined by feathering
- 2021MNRAS.500.5500B: K-to-Jy factor ~41.5 K/Jy for TP; channel width ~1.3 km s^-1
- 2021MNRAS.500.5500B: Velocity integration range (+29, +36) km s^-1; systemic velocity = 32.5 km s^-1; ring reference width = 7 arcsec (ACA beam)
- 2021MNRAS.500.5500B: Inner radius = 0.3 pc, half opening angle = 10 deg, inclination = 70 deg, PA = 135 deg; v_phi = 1 km s^-1, v_exp = 3.5 km s^-1, v_turb = 0.25 km s^-1
- 2021MNRAS.500.5500B: processing.imaging.array_combination = CASA feather task combining ACA and ALMA TP cubes (recovering 99.7% of single-dish flux)
- 2017A&A...605A..28D: processing.imaging.array_combination = TP regridded, used as clean model, then ACA and TP combined with FEATHER
- 2026A&A...709A.216U: Circular Gaussian beam FWHMs starting from original synthesised beam major-axis up to total emission extent
- 2026A&A...709A.216U: processing.imaging.array_combination = ALMA 12m, ACA, and total power combined for IRC+10216 archival SiS J=5-4; ALMA + IRAM 30m OTF combined cubes used from literature
- 2021ApJ...908..231M: robust 0.5, 11 km/s channels
- 2021ApJ...908..231M: processing.imaging.array_combination = 12-m + ACA concatenated with CONCAT
- 2017MNRAS.464.1415M: processing.imaging.array_combination = ACA and 12-m concatenated
- 2024PASJ...76..960S: Briggs robust 0.5, velocity resolution 2.0 km/s
- 2024PASJ...76..960S: 2 sigma detection threshold per channel for moment maps
- 2024PASJ...76..960S: processing.imaging.array_combination = 12 m and 7 m visibilities concatenated, then combined with Total Power by feather
- 2025ApJ...989...83B: Intrinsic alpha = -0.6 for the mock light curves; Band 6 light curve 2 yr with one-day cadence
- 2015ApJ...804...37L: processing.imaging.array_combination = 12m+ACA joint imaging
- 2019ApJ...887...24T: processing.imaging.array_combination = two configurations combined for IRAS F23411+0228
- 2020A&A...635A..71W: TP SB2 mean in central 240'' radius scaled from 7454 K to 7300 K
- 2020A&A...635A..71W: processing.imaging.array_combination = Feathering of interferometric data with TP map (SB2 TP scaled to 7300 K, factor 0.979)
- 2020ApJ...898..146M: aspect ratio h fixed to 0.03; walkers = 10 x free parameters; 2000 steps
- 2020ApJ...898..146M: processing.imaging.array_combination = 12m+ACA visibilities concatenated and imaged jointly
- 2017SoPh..292...87S: processing.imaging.array_combination = CASA feather with default parameters, combining with full-Sun TP map
- 2020ApJ...894...72S: 10 km/s channels, robust 1
- 2020ApJ...894...72S: processing.imaging.array_combination = TP regridded, divided by 7m PB, feather, then PB-corrected
- 2025ApJ...981...49S: processing.imaging.array_combination = 12 m array and ACA data combined within tclean
- 2026ApJ...999L..32R: 10'' diameter mask, threshold = 2 x rms noise, natural weighting
- 2026ApJ...999L..32R: ACA primary beam FWHM = 29.3'' at 338 GHz and 27.9'' at 354 GHz
- 2019A&A...629A.104G: uv>30 m for flux measurement (50 m tested)
- 2019A&A...629A.104G: processing.imaging.array_combination = ALMA and ACA visibilities merged in uv; maps merged for display
- 2024A&A...686A.206Y: processing.imaging.array_combination = visibilities of both observation blocks combined for the main image
- 2018MNRAS.481.4931E: processing.imaging.array_combination = concat of the two uv datasets, copypointing=False
- 2014ApJ...792...68S: processing.imaging.array_combination = two dates' measurement sets combined
- 2025A&A...702A.276P: processing.imaging.array_combination = 7 m ACA test observations not combined (excluded due to non-detection); all 12 m array MOUSs across Bands 1-8 combined, and Bands 7+8 combined
- 2013ApJ...777...92S: processing.imaging.array_combination = ALMA CO(1-0) cube at 8 km/s feathered with SEST
- 2014ApJ...797...90S: processing.imaging.array_combination = CSV and Cycle 0 Band 3 combined as a mosaic
- 2024A&A...682A.186L: uv upper threshold 65 klambda
- 2024A&A...682A.186L: SZ centroid fixed to X-ray centroid so that only the mass term (M500) is free per pressure model
- 2024A&A...682A.186L: processing.imaging.array_combination = ACA and ALMA Band 3 and Band 4 visibilities modelled jointly in the uv plane (no imaging); only uv < 65 klambda used
- 2023PSJ.....4..206R: Apertures capture all emission at >=3 sigma
- 2023PSJ.....4..206R: processing.imaging.array_combination = 12 m and ACA imaged separately (no combination stated)
- 2020ApJS..251...14H: processing.imaging.array_combination = SMA-only data used for catalogs (no single-dish feathering)
- 2015ApJ...811..124S: processing.imaging.array_combination = H75/H214, 1.5 km and 6 km configurations combined
- 2020A&A...633A..68D: processing.imaging.array_combination = pipeline cube combining all five executions
- 2024A&A...688A..30B: CASA v.6.5.2
- 2024A&A...688A..30B: thermalnoise = tsys-atm for the noisy runs, PWV = 1.8 mm
- 2024A&A...688A..30B: concat weights 1 (12m) and 0.116 (7m)
- 2024A&A...688A..30B: feather sdfactor = 1.0
- 2024A&A...688A..30B: 23 small-scale filaments (fibers) in OMC-3
- 2024A&A...688A..30B: processing.imaging.array_combination = 12m+7m: concat with weights 1 and 0.116 then joint tclean; with TP: feather (sdfactor 1.0) and MACF (SD image as tclean startmodel)
- 2019ApJ...874...89C: robust 0.5, taper 1.5", scales [0,2,6,18]"
- 2019ApJ...874...89C: processing.imaging.array_combination = joint deconvolution of ACA+12m visibilities
- 2020MNRAS.496.2790L: velocity interval 1.5 to 6.5 km/s, chosen from the H13CO+ line width to avoid outflow contamination
- 2020MNRAS.496.2790L: processing.imaging.array_combination = ACA and 12-m calibrated and imaged separately, not combined for the science case study; a feather test (HCO+, H13CO+) was shown in Figure 4
- 2018ApJ...863..143C: robust = 0.5; 6 km/s binning; taper 1.4''
- 2018ApJ...863..143C: processing.imaging.array_combination = ACA cleaned cube used as modelimage for ALMA clean, then feather of ALMA and ACA images
- 2021ApJS..257...43L: Multiscale clean threshold: 4 sigma; Hogbom clean threshold: 1 sigma; strict mask: S/N > 4 in 2 channels expanded to S/N > 2 in 2 channels; moment 1 prior tole…
- 2021ApJS..257...43L: processing.imaging.array_combination = 12-m and 7-m imaged together (12-m+7-m), multi-part mosaics linearly combined (noise-weighted), then combined with TP via feather algorithm
- 2024MNRAS.527.1444A: 5-sigma pixel brightness threshold; regridded to 0.3 x 0.3 arcsec^2 pixel size and smoothed to 2.7 x 2.6 arcsec^2 resolution for spectral index map
- 2024MNRAS.527.1444A: processing.imaging.array_combination = 7-m ACA and 12-m total power combined as described in Tokuda et al. (2021) for 12CO (J=2-1)
- 2026A&A...705A..96M: processing.imaging.array_combination = Self-calibrated extended and FAUST compact continuum datasets combined; matched uv-wavelength ranges for spectral-index imaging
- 2025A&A...695A.163B: processing.imaging.array_combination = Concatenate uv observations; re-calibrate weights with CASA statwt.
- 2020MNRAS.494.4090C: Test elliptical apertures of 1× and 1.5× the beam size against single-pixel extraction.
- 2021A&A...648A..33M: processing.imaging.array_combination = Align positions, rescale fluxes, correct offsets, combine short/long baselines and projects, then self-calibrate together.
- 2018ApJ...863...56C: processing.imaging.array_combination = Cycle 2 and Cycle 4 data concatenated for ALESS49.1
- 2018ApJ...852..122H: processing.imaging.array_combination = Extended and compact datasets imaged together jointly; mstransform regrid to 0.25 km/s channels
- 2016A&A...593A.107L: processing.imaging.array_combination = 12m antennas omitted from ACA data before measuring Stokes I
- 2021MNRAS.504.2687N: Case 1: 1 Jy/pixel for R < 0.04 arcsec; Case 2: 0.1 Jy/pixel for 0.04 < R < 0.3 arcsec; Case 3: Case 1 + Case 2
- 2017A&A...605A.116K: Briggs robust = 0.5; 1 km/s velocity binning
- 2017A&A...605A.116K: processing.imaging.array_combination = MA and ACA combined in the uv-plane; TP added via feathering
- 2024A&A...684A...4U: processing.imaging.array_combination = CASA task concat (version 6.3.0-48) combining 2013.1.00070.S with extended and compact configurations of 2015.1.01271.S
- 2023ApJ...954..197I: processing.imaging.array_combination = Cycle 2 and Cycle 4 visibilities concatenated with weights inversely proportional to error variance after relabeling Cycle 2 reference frame to ICRS
- 2019AJ....157..135M: processing.imaging.array_combination = all configurations and ACA combined with per-dataset visibility weight rescaling
- 2024ApJ...977...37N: pixel size 2.935 arcsec, channel width 0.332 km/s
- 2025ApJ...995..108J: processing.imaging.array_combination = TM1 and TM2 combined with CASA concat for Cycles 8/10.
- 2015Natur.527...70P: processing.imaging.array_combination = concat of 12m and 7m uv-data
- 2017ApJ...845L...5I: processing.imaging.array_combination = cycle 3 and cycle 1 visibilities combined
- 2020A&A...644A.152E: processing.imaging.array_combination = interferometric maps feathered with single-dish total power
- 2020MNRAS.492.6067M: inclination 45 deg, azimuthal averaging
- 2020MNRAS.492.6067M: processing.imaging.array_combination = Proxima Cen: ACA alone and 12m + ACA combined limits shown
- 2019ApJ...881...99M: processing.imaging.array_combination = feathering with full-disk single-dish image in CASA
- 2020PASJ...72...33K: processing.imaging.array_combination = 12-m and 7-m visibilities imaged jointly as a mosaic
- 2026A&A...707A.120H: processing.imaging.array_combination = IRAM 30m map deconvolved, multiplied by ALMA 7m primary beam, pseudo-visibilities sampled 0-7 m merged with 7m data
- 2017A&A...597A..53L: processing.imaging.array_combination = 12 m and ACA data combined before final cleaning and imaging
- 2024JApA...45...31M: Continuum image: tclean with hogbom deconvolver using line-free channels
- 2019A&A...628A.100D: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05)
- 2016ApJ...821L...8S: processing.imaging.array_combination = C18O and C17O data combined per transition with fixplanets and cvel
- 2026A&A...706A...4R: processing.imaging.array_combination = Higher and lower spectral setups imaged jointly
- 2017ApJ...842L..24A: processing.imaging.array_combination = cycle 2 and cycle 3 data combined
- 2015ApJ...812..126C: processing.imaging.array_combination = ATCA 6 km data from several configurations concatenated; ALMA datasets brought to common uv coverage using uvsim
- 2023PASP..135g4501H: processing.imaging.array_combination = Not supported: 12 m, 7 m and total power combinations are not yet done by the pipeline
- 2025A&A...694L..15H: processing.imaging.array_combination = Setup 1, Setup 2 and Setup 1+2 continuum images combined; combination procedure not described
- 2015ApJ...814..143A: processing.imaging.array_combination = ALMA combined with IRAM 30m short spacings
- 2015ApJ...803...60S: processing.imaging.array_combination = Compact+extended combined for 340 GHz low-res continuum
- 2026A&A...708A.251X: 36.3'' coarse resolution with 14.0'' pixel size; 18'' medium resolution; 6.2'' high resolution
- 2026A&A...708A.251X: uv overlap between 18.2'' and 28.0''
- 2026A&A...708A.251X: astrodendro min_value = 3 sigma, min_delta = 1 sigma, min_npix = pixels in half a synthesized beam
- 2026A&A...708A.251X: processing.imaging.array_combination = J-comb linear combination algorithm in the uv domain combining ACA 7m continuum (6'') with extrapolated 18'' 1.3 mm map (from Herschel + APEX/ArTéMiS SED)
- 2017ApJ...843...45K: robust = 0.5
- 2017ApJ...843...45K: processing.imaging.array_combination = 7 m and 12 m concatenated in uv; Total Power feathered in image space
- 2022MNRAS.514..578W: robust = 0.5, continuum threshold = 15 microJy, 10^5 iterations; line threshold = 0.06 mJy; Gaussian smoothing kernel = 0.34 arcsec
- 2022MNRAS.514..578W: min_value (threshold) = 3 sigma (and 5 sigma for comparison), min_delta (increment) = 1 sigma (sigma = 15 microJy), min_npix = 77
- 2022MNRAS.514..578W: processing.imaging.array_combination = Continuum feathered with Barnes et al. (2019) ALMA 12m+7m+BGPS data using CASA feather task after scaling flux by ~0.6 (using alpha_nu = 3.75 from 259 GHz to 2…
- 2018ApJ...858...90G: taper 2-3"; 8" final beam; 10 km/s channels
- 2018ApJ...858...90G: processing.imaging.array_combination = CASA feather with IRAM 30-m (not for CS)
- 2021A&A...645A..97Q: Hogbom deconvolution, natural weighting, 2 mJy/beam threshold, 2.5 km/s channels
- 2021A&A...645A..97Q: Total power baseline: order-1 polynomial in line-free windows 755-855 and 1500-1600 km/s
- 2021A&A...645A..97Q: Pixel 0.082 arcsec, image 1344 x 1440 pixels
- 2021A&A...645A..97Q: processing.imaging.array_combination = 12 m and 7 m visibilities concatenated and imaged together, with total power cube as model in tclean
- 2024ApJ...971..176H: Briggs robust = 0.5; 1st-order continuum fit on line-free channels
- 2024ApJ...971..176H: Clean threshold 2 x RMS, RMS ~0.18 mJy/beam
- 2024ApJ...971..176H: processing.imaging.array_combination = 12m and 7m measurement sets combined before imaging; cleaned image feathered with TP data
- 2026MNRAS.552g1700S: processing.imaging.array_combination = concatenated 3 short-baseline (C43-3) and 4 long-baseline (C43-6) executions after astrometric alignment and flux scaling
- 2025ApJ...987...61R: processing.imaging.array_combination = Combined two 12-m array execution blocks
- 2023ApJ...948L...2Y: processing.imaging.array_combination = Combined six execution blocks in two configurations (C43-6 and C43-7)
- 2019ApJ...876..130H: processing.imaging.array_combination = Concatenated with earlier 0.16" data
- 2019A&A...625A.118K: processing.imaging.array_combination = Cycle 3 and Cycle 5 data combined after proper-motion phase-center correction and shift by (0.509'', 0.490'')
- 2019ApJ...885L..20H: robust 0.5; 2 km/s channels; smoothed to 1.3''
- 2019ApJ...885L..20H: processing.imaging.array_combination = 12 m + 7 m + single-dish; four mosaics processed separately then combined
- 2020A&A...633A..13D: ACA/12-m weight ratio 0.18
- 2020A&A...633A..13D: processing.imaging.array_combination = ACA and 12-m calibrated and combined, then combined with TP; ACA/12-m weight ratio scaled to 0.18
- 2017A&A...605A.126R: processing.imaging.array_combination = main array + ACA (ACA weight 0.25) combined, then with TP via SD2VIS
- 2024RAA....24c5009N: processing.imaging.array_combination = June 5 and June 14, 2019 TM0 observations merged with equal weights; combined data from Homan et al. (2020a) merged 2016 and 2019 observations giving TM0 a wei…
- 2020ApJ...902...99I: processing.imaging.array_combination = Main results use Cycle 6 data only; Appendix A combines Cycle 6 with Cycle 5 HCN data after excluding Cycle 5 baselines of 44–83 m
- 2019AJ....158..162F: cell 0.08", 800x800 pixels
- 2024ApJ...968L..11G: processing.imaging.array_combination = ACES data are combined 12m + 7m + TP; the 2012 data are 12m and the 2017 data 7m only
- 2026MNRAS.546ag167S: processing.imaging.array_combination = High and low resolution visibilities coadded in uv-space using CASA task 'concat'
- 2015ApJ...802..125R: processing.imaging.array_combination = Single-dish data used as model during CLEAN in Fourier domain (not feathering)
- 2019A&A...629A..30F: processing.imaging.array_combination = Calibration-intended 4C12.50 data merged; archival CO(1-0), CO(3-2) concatenated with concat to make deep cubes
- 2023A&A...671A..69G: processing.imaging.array_combination = Interferometric images combined with full-disk Total Power (TP) single-dish maps for absolute brightness temperatures
- 2020ApJ...905..122H: 49 Ceti: ~6 arcsec, corresponding to 340 au
- 2020ApJ...905..122H: HD 21997: 4.0×4.0 arcsec, P.A.=0.0 degrees; 4 arcsec corresponds to 280 au
- 2017ApJ...845L..19B: processing.imaging.array_combination = Feathering of interferometric and total power maps
- 2023PASJ...75..311K: processing.imaging.array_combination = 12-m and 7-m data imaged together (joint mosaic imaging)
- 2026A&A...711A.118A: processing.imaging.array_combination = 7M + TM1 + TM2 combined
- 2018ApJ...853L..19S: processing.imaging.array_combination = 7m and 12m data simultaneously imaged and deconvolved interactively
- 2025NatAs...9.1476C: processing.imaging.array_combination = 9 Band 6 sessions time-averaged and concatenated into one measurement set
- 2016PASJ...68...88K: processing.imaging.array_combination = 7-m and 12-m visibilities imaged jointly
- 2018AJ....156..270S: processing.imaging.array_combination = three observations combined, spectrally averaged and stacked into one visibility set
- 2025Natur.642..905L: processing.imaging.array_combination = Combined compact and extended configuration visibility datasets in tclean mosaic mode.
- 2014ApJ...784...62A: processing.imaging.array_combination = FV Tau and HBC 387 pointings combined in a mosaic
- 2025ApJ...985..166K: Feathered cube beam 0.30''x0.22'', rms 1.46 mJy/beam (0.56 K)
- 2025ApJ...985..166K: Radial range 1-9000 au, distance 151 pc, stellar mass 0.14 Msun, disk radius 55 au, disk mass 1.0e-2 Msun, envelope mass 0.52 Msun, C18O abundance 1.7e-7
- 2025ApJ...985..166K: Disk P.A. 45 deg and inclination 73 deg
- 2025ApJ...985..166K: processing.imaging.array_combination = 12-m and 7-m (and all projects) imaged together in one tclean; JCMT feathered with the ALMA cube using CASA feather after imregrid and multiplication by the AL…
- 2019A&A...631A..64B: thresholds 0.05 mJy/beam continuum, 3 mJy/beam lines
- 2019A&A...631A..64B: processing.imaging.array_combination = concatenation of three projects after astrometric alignment and weight normalisation
- 2021A&A...646A..25Z: cell = 0.3" (combined) and 1" (7 m); robust = 0.5; clean threshold = 0.4 mJy Beam^-1 (combined) and 4 mJy Beam^-1 (7 m); field down to 20% primary beam power p…
- 2021A&A...646A..25Z: Combined images: min_value = 3 rms, min_delta (step) = 1 rms, min_npix = half of synthesized beam
- 2021A&A...646A..25Z: 7 m ACA images: min_value = 2.5 rms, min_delta (step) = 1 rms, min_npix = half of 7 m ACA synthesized beam
- 2021A&A...646A..25Z: processing.imaging.array_combination = 12 m main array and 7 m ACA combined in visibility space using CASA task CONCAT
- 2018ApJ...864..120M: robust=0.5, 1.5 km/s channels, 0.05 arcsec pixel
- 2018ApJ...864..120M: processing.imaging.array_combination = 12m+7m mosaic feathered with TP image
- 2020ApJ...896...36T: Briggs robust 0.5 (12 m), natural (7 m)
- 2020ApJ...896...36T: processing.imaging.array_combination = 12 m and 7 m imaged separately then feathered; IRAM 30 m feathered too; alternative visibility-domain combination gave similar results
- 2025PASJ...77..616I: Briggs robust = 0.5
- 2025PASJ...77..616I: pixel 0.''13, ~5.1 km/s channels
- 2025PASJ...77..616I: processing.imaging.array_combination = 12 m and 7 m concatenated in the visibility plane, then TP cube feathered in
- 2025MNRAS.538.2358S: processing.imaging.array_combination = Concatenated 1 SB (C43-4), 2 re-scaled MB (C43-7), and 4 LB (C43-10) 12m executions
- 2024ApJ...965..108U: processing.imaging.array_combination = Existing 2013.1.00999S and 2015.1.01425.S data combined for five Hubble Frontier Fields
- 2020MNRAS.495.3409S: processing.imaging.array_combination = observations of each target combined into one measurement set with CASA concat
- 2021ApJ...906..111T: processing.imaging.array_combination = Several transitions combine different ALMA configurations; flux-density and noise corrections address CLEAN-beam versus dirty-beam scaling.
- 2017ApJ...835..286I: processing.imaging.array_combination = Cycle 1 and Cycle 2 visibilities combined
- 2018A&A...619A.161C: processing.imaging.array_combination = Extended and compact configurations observed to recover short spacings (combined data)
- 2017A&A...601L...9G: processing.imaging.array_combination = Total-power 12 m single-dish maps used to create short-spacing visibilities with GILDAS/MAPPING and merged with ACA
- 2020A&A...640A.133R: 10000 clean iterations; 20000 for >20 Jy sources
- 2020A&A...640A.133R: 32×32 pixels of 0.8″ (CO 2-1) and 0.7″ (CO 3-2)
- 2017ApJ...841..110S: processing.imaging.array_combination = 12m and ACA combined in visibility plane; TP combined with CASA feather
- 2026A&A...711A.159M: processing.imaging.array_combination = Extended configuration used for main analysis; combined with compact configurations (C-4, C-2) to test flux filtering
- 2023ApJ...942L..24K: processing.imaging.array_combination = Combined C-5 and C-8 12 m configurations
- 2019ApJ...881...84S: processing.imaging.array_combination = Three datasets frequency-averaged then concatenated
- 2025NatAs...9..406L: processing.imaging.array_combination = SMC: 12 m + 7 m interferometry cubes combined with product TP cubes using feather
- 2024ApJ...976..201F: processing.imaging.array_combination = ALMA data combined with previous ACA observations; combination method not stated
- 2015ApJ...801...82H: processing.imaging.array_combination = SV band 6 (230-232 GHz) concatenated with cycle 0; band 7 continuum and line-mode data concatenated
- 2019ApJ...880..157D: processing.imaging.array_combination = low- and high-resolution datasets concatenated
- 2020A&A...634A..56D: processing.imaging.array_combination = interferometric combined with TP data
- 2021MNRAS.506.1978L: processing.imaging.array_combination = 2016 and 2018 Band 7 measurement sets realigned to Gaia DR2 stellar positions with fixvis and fixplanets, then combined with CASA concat
- 2017ApJ...850...35L: processing.imaging.array_combination = Feathering of single-dish and interferometric maps
- 2020A&A...638A..70D: 5% flux uncertainty
- 2025A&A...700A.141H: processing.imaging.array_combination = 12 m array + ACA visibilities combined
- 2018A&A...610A..54P: processing.imaging.array_combination = ACA included to fill short baselines
- 2026ApJ...997...16H: robust = 2.0
- 2026ApJ...997...16H: threshold = 1.2 mJy (continuum), 100 mJy (spectral channels)
- 2026ApJ...997...16H: Circular region radius/aperture = 25'' (10,000 au), velocity range = v_LSR +/- 3 km s^-1, SNR threshold = 5
- 2026ApJ...997...16H: Convolved circular beam FWHM = 36''; Yebes extraction window = 5 MHz; modeled T_rot = 5 K and 10 K (and evaluated at 7.5 K)
- 2019A&A...623A..96Y: natural weighting; scales 0, 2", 5", 10"
- 2019A&A...623A..96Y: processing.imaging.array_combination = ACA+ALMA jointly cleaned, then feathered with IRAM 30m (regridded and multiplied by mosaic primary beam response) using feather/casafeather
- 2021PASJ...73..205T: Aperture radii: 6''.5 (341-GHz_ACA, background annulus 6''.5 to 9''.8), 0''.5 (233-GHz), and 12'' diameter (233-GHz vs ACA flux comparison)
- 2021PASJ...73..205T: kappa_341GHz = 1.8 cm^2 g^-1; kappa_233GHz = 0.899 cm^2 g^-1; R_g/d = 100
- 2021PASJ...73..205T: processing.imaging.array_combination = 12-m and 7-m combined in visibility space; 12-m + 7-m merged with TP using CASA feathering task for C18O_all
- 2018ApJ...853..111J: Briggs robust 0.5, clean to ~2.5×RMS
- 2018ApJ...853..111J: processing.imaging.array_combination = ACA + TP feather
- 2022MNRAS.514.5035L: channel width = 2 km s^-1 (and 15 km s^-1 for kinematics)
- 2022MNRAS.514.5035L: Briggs robust = 2.0, uv-taper = 0.7'', final circular beam FWHM = 1.1''
- 2022MNRAS.514.5035L: processing.imaging.array_combination = concat in CASA (combining 12-m C36-4 and 7-m observations)
- 2024A&A...691A.121N: ~8 mK noise per 5 km/s channel
- 2024A&A...691A.121N: Channel width 5 km/s used in the analysis
- 2024A&A...691A.121N: processing.imaging.array_combination = 12-m interferometric + 7-m ACA + 12-m total power data combined
- 2024A&A...683A.141R: processing.imaging.array_combination = Band 4 compact and extended configurations combined in tclean; VLA C, B and A executions aligned for proper motion and combined
- 2026A&A...707A.252K: processing.imaging.array_combination = Combined 2018.1.01710.S and 2015.1.01320.S re-gridded to common spectral resolution 15.625 MHz, using tp2vistweak from Total Power to Visibilities tool
- 2023MNRAS.524.3671Z: processing.imaging.array_combination = Combined all calibrated on-source visibility data from projects 2012.1.00175.S and 2017.1.00963.S
- 2021MNRAS.501.2934C: processing.imaging.array_combination = long-baseline processed alone for all targets; also combined with 0.2'' Cycle-4 data (2016.1.00545.S), used in analysis only for WSB 82
- 2016ApJ...833..103H: processing.imaging.array_combination = Cycle 0 data not combined
- 2016ApJ...829L..35T: processing.imaging.array_combination = Band 6 combined with archival short-baseline Band 6 after phase shift; B4 long baselines only
- 2016ApJ...832..143F: processing.imaging.array_combination = ALMA combined with Herschel (500 micron scaled to 3 mm, graybody beta=1.2, Tdust=20 K)
- 2023A&A...674A.125B: processing.imaging.array_combination = Extended, mid, and (where available) compact configurations combined and aligned on the stellar peak of the first epoch
- 2019A&A...621A..50B: processing.imaging.array_combination = MA and ACA not combined; analysed separately
- 2024NatAs...8..308D: processing.imaging.array_combination = three array configurations combined in CASA to maximise sensitivity
- 2022MNRAS.514.6215Y: processing.imaging.array_combination = Calibrated ALMA data from extended and compact configurations were concatenated
- 2018MNRAS.479.5423M: processing.imaging.array_combination = Band 7 12m+ACA combined
- 2024A&A...691A..70N: processing.imaging.array_combination = Feather ACA + total power cubes, then feather to 12 m cube; four mosaics combined with weighting to mitigate edge noise; 3 mm continuum 12 m image feathered to…
- 2024ApJ...969...56M: processing.imaging.array_combination = 12m array only (7m not used)
- 2014ApJ...795..152O: processing.imaging.array_combination = CCH data combined with project 2011.0.00628.S (15-16 antennas)
- 2016A&A...586A..70L: processing.imaging.array_combination = Self-calibrated datasets combined per band, then all into band 3+6+7 superset
- 2021A&A...652A..92N: processing.imaging.array_combination = 1 s snapshot images combined with full-disk ALMA images to recover large scales and absolute Tb
- 2021MNRAS.502.5390P: processing.imaging.array_combination = concatenated multiple 12 m datasets at similar frequencies
- 2017ApJ...841L..20I: processing.imaging.array_combination = Single dish and interferometric data combined in the U-V plane (feathering), default parameters
- 2026AJ....172..108L: min_value = 5 sigma, min_delta = 1 sigma, min_npix = 1 synthesized beam, major-to-minor axis ratio < 2
- 2026AJ....172..108L: M = 0.95 M_sun, R = 2400 au
- 2026AJ....172..108L: processing.imaging.array_combination = ACA alone, combined ACA+TM2, and combined ACA+TM2+TM1
- 2018ApJ...862....8T: briggs robust 0.5 before tapering
- 2018ApJ...862....8T: processing.imaging.array_combination = feathering of 12 m + 7 m + TP in CASA
- 2021MNRAS.503.4320F: feather default parameter set (effective dish size, single-dish scaling, low-pass filtering)
- 2021MNRAS.503.4320F: Spectral smoothing to ~0.4 km s^-1; Total power HPBW ~ 70"
- 2021MNRAS.503.4320F: processing.imaging.array_combination = 12m, 7m, and total power combined using feather in CASA 4.7.0 with default parameter set
- 2019PASJ...71...85M: Briggs robust 0.5, auto-multithresh, niter 10000
- 2019PASJ...71...85M: processing.imaging.array_combination = 7M and TP feathered on image plane
- 2020ApJ...889....9M: natural weighting for lines; 20 km/s channels; continuum robust 0.5
- 2020ApJ...889....9M: processing.imaging.array_combination = 12m and ACA visibilities concatenated before deconvolution
- 2024A&A...689A.122B: final circular beam 22 arcsec, channel width 10 km/s
- 2024A&A...689A.122B: processing.imaging.array_combination = 7m + TP combined with CASA feather; interferometric flux is 70% of single-dish flux
- 2025ApJ...984L..16G: processing.imaging.array_combination = Cycle 6 and exoALMA combined for sensitivity, short spacings and high angular resolution
- 2025ApJ...995..150K: processing.imaging.array_combination = Himiko Cycle 0 and Cycle 1 data concatenated (6.4 h)
- 2021Sci...371..713L: processing.imaging.array_combination = 2012, 2015, and 2018 ALMA datasets combined for continuum; 2012 and 2018 datasets combined for [C II] cube after reweighting with oldstatwt
- 2021A&A...649A.122P: processing.imaging.array_combination = All available Band 7 observations (compact and extended, from three projects) combined; Band 4 compact and extended combined after separate compact self-calibr…
- 2019ApJ...887...40W: processing.imaging.array_combination = Cycle 1 combined with Cycle 0 data, weights corrected
- 2016Natur.535..258C: processing.imaging.array_combination = All three Cycle-2 epochs combined for a single C18O cube
- 2018A&A...618A..35G: processing.imaging.array_combination = Zero-spacing pseudo-visibilities from TP map created with GILDAS/MAPPING and merged in the uv plane
- 2021A&A...651A..35O: processing.imaging.array_combination = Band 6: three configurations combined
- 2016RAA....16..106H: V_x* = 3.2 km/s mean velocity of selected sample
- 2025MNRAS.536..684D: processing.imaging.array_combination = Band 6 extended and compact configurations combined with equal weight after matching continuum flux densities on baselines of similar length
- 2021A&A...652A..98G: processing.imaging.array_combination = Extended and compact configurations combined
- 2019MNRAS.484.1257M: processing.imaging.array_combination = 12m+ACA combined image
- 2025PASJ...77L..55S: processing.imaging.array_combination = 12m + 7m + TP (Total Power) combined cube
- 2024A&A...682L...5G: processing.imaging.array_combination = Combined two Band 7 datasets using extended and compact 12m array configurations
- 2013A&A...555A.112P: processing.imaging.array_combination = Mopra single-dish data combined with ALMA using GILDAS; combined cube rms 0.14 Jy/beam (~0.8 K)
- 2017ApJ...849...95B: processing.imaging.array_combination = For 2209+080, cycle 4 and cycle 3 data combined after core subtraction
- 2020ApJ...888L..28S: processing.imaging.array_combination = not combined with single-dish full-sun images
- 2025ApJ...990..150A: Briggs robust 1 (12m), robust 2 (12m+ACA mosaic); 600x600 px at 0.05 arcsec; clean threshold 2x rms
- 2025ApJ...990..150A: Fixed T = 20 K; N bounded between 1e13 and 1e16 cm^-2
- 2025ApJ...990..150A: processing.imaging.array_combination = 12m + ACA imaged together with mosaic gridding; ACA visibilities downweighted by factor 0.41 (effective 12m:ACA time ratio 1:2.4)
- 2018ApJ...861...14C: multiscale 0,3,10,30 pixels; pixel 0.16"
- 2018ApJ...861...14C: processing.imaging.array_combination = 12+7 m concatenated; TP feathered for lines
- 2023A&A...678A.194C: pbmask = 10% of primary beam response
- 2023A&A...678A.194C: Cleaning threshold = 5 sigma (10 sigma for G351.77)
- 2023A&A...678A.194C: Multi-scale scales = geometric series from 0 increasing by ~x2 minor beam/cell size up to ~5.5''
- 2023A&A...678A.194C: processing.imaging.array_combination = Combination of the two ALMA 12m-array configurations (7m and TP not combined in DR1)
- 2019ApJ...887..143S: robust = 0.5, Hogbom, mosaic gridder
- 2019ApJ...887..143S: processing.imaging.array_combination = [C I] band 8 12m+ACA feathered with TP using feather
- 2020ApJ...901..151S: natural weighting, 10.16 km/s channels (CO); Briggs robust 0.5, mfs (continuum)
- 2020ApJ...901..151S: processing.imaging.array_combination = TM and ACA jointly deconvolved; no total power
- 2025ApJ...990..209C: Final beams 0.270'' (CO 2-1), 0.331'' (CO 3-2), 0.276'' ([CI] 1-0)
- 2025ApJ...990..209C: Highest resolution data used, not matched
- 2025ApJ...990..209C: processing.imaging.array_combination = 12m and ACA data imaged together through the PHANGS-ALMA pipeline
- 2025A&A...702A..18D: processing.imaging.array_combination = Aligned with VisAlign and concatenated: Band 3 (two TM1 configs), Band 4 (TM1 + TM2), Band 9 (TM1 uv-clipped > 0.4 Mlambda and scaled by 1/0.78 + shifted TM2);…
- 2024MNRAS.528.5019H: processing.imaging.array_combination = All programmes combined in the uv plane and imaged together in MFS mode at one reference frequency; no spectral-index correction applied
- 2023MNRAS.521.1045R: processing.imaging.array_combination = SGP38326 combined from two datasets (2018.1.00001.S and 2015.1.00330.S) using CASA split and concat over common frequency range
- 2023A&A...669A..53B: processing.imaging.array_combination = Combined short baseline (43C-2) and long baseline (43C-5) data; JvM correction applied (epsilon ~ 0.50 for robust +0.5 lines, 0.26-0.83 across robust grid for …
- 2019PASJ...71...71H: processing.imaging.array_combination = Cycle 4 and 5 Band 8 data combined with concat
- 2017ApJ...851...83C: processing.imaging.array_combination = two configurations' datasets combined after checking flux consistency
- 2016A&A...593A..44L: processing.imaging.array_combination = 12m and ACA treated separately
- 2020MNRAS.495.4297S: processing.imaging.array_combination = the two executions combined before imaging
- 2019A&A...623A.153O: processing.imaging.array_combination = three configurations combined for 12CO(2-1)
- 2024A&A...687A.112M: processing.imaging.array_combination = concat with visibility weights adjusted for uniformity; U Ant TP feathered with ACA and TM.
- 2020ApJ...895...73K: processing.imaging.array_combination = two executions combined each for a_07 and b_07 after calibration
- 2016MNRAS.460.2933M: processing.imaging.array_combination = cycle 1 and cycle 2 datasets combined
- 2024A&A...690A.372L: processing.imaging.array_combination = 12-m and 7-m data combined with CASA 6.4.1 (UCH II sight lines)
- 2025A&A...700A.285W: processing.imaging.array_combination = two datasets jointly imaged; 30 km/s channels
- 2013ApJ...779L..22J: processing.imaging.array_combination = 2011.0.00777.S combined for CH3OH and continuum
- 2017ApJ...835L..35M: processing.imaging.array_combination = all available visibilities per band combined
- 2020A&A...640A..57A: processing.imaging.array_combination = HR interferometric data feathered with FD images
- 2024AJ....167...72D: 3sigma contour threshold for fitting
- 2024AJ....167...72D: processing.imaging.array_combination = Combined TM1, TM2, and ACA configurations for line cubes
- 2018A&A...610A..77H: robust = 0.5; final beam 4.5"
- 2018A&A...610A..77H: processing.imaging.array_combination = feathering of IRAM 30m and ALMA maps
- 2023A&A...678A.160E: 4-sigma contour of HDCO 259 GHz map used as extraction polygon
- 2023A&A...678A.160E: Velocity integration ranges for H2CO components: -5 to 0 km s^-1, 1 to 8 km s^-1, 8 to 15 km s^-1; extended structure: 0 to 6 km s^-1
- 2023A&A...678A.160E: Continuum offset of 10.3 K added to H2CO spectrum to model absorption; baseline offset of 0.1 K corrected in HDCO 259 GHz spectrum
- 2023A&A...678A.160E: processing.imaging.array_combination = 12 m (C43-4, C43-1) and 7 m (ACA) combined using the 'mosaic' gridder in tclean after self-calibration alignment
- 2018ApJ...867..166S: 4 million iterations, gain 0.05, natural weighting
- 2018ApJ...867..166S: processing.imaging.array_combination = TP converted to visibilities with TP2VIS, joint deconvolution with 12m+7m; TP weight from TP map rms
- 2020A&A...641A..97V: APEX main beam efficiency 0.72
- 2020A&A...641A..97V: processing.imaging.array_combination = concat with freqtol 10 MHz, statwt weights; feather with APEX
- 2025ApJ...988..162D: multi-scale clean to ~4σ, then single-scale to ~1σ
- 2025ApJ...988..162D: processing.imaging.array_combination = 7m+TP feathered; CO(2-1) 12m+7m+TP
- 2024ApJ...976..258K: processing.imaging.array_combination = Two executions with identical spectral setups combined with concat (no multi-array combination stated)
- 2025PASJ...77..432U: processing.imaging.array_combination = All 29 min of C43-2 data from 2021.1.00041.S and 2021.1.01406.S combined for the low-resolution [CII] cube
- 2022A&A...665A.107T: processing.imaging.array_combination = Combination of Dataset I and Dataset II was performed, but not used in the analysis due to no gain in sensitivity or image quality
- 2023MNRAS.522.2384M: processing.imaging.array_combination = 12-m + 7-m combined for continuum and large-scale C18O datacube (2); 12-m only (C43-4 + C43-1) combined for small-scale C18O datacube (1)
- 2019ApJ...882...10N: processing.imaging.array_combination = Combined with previous compact-array data (2015.1.01115.S)
- 2019MNRAS.482..698C: processing.imaging.array_combination = Three nights concatenated and processed together
- 2019MNRAS.485.2457H: processing.imaging.array_combination = ALMA combined with MALT90 single-dish data (as in Rathborne et al.)
- 2020A&A...644A..59K: processing.imaging.array_combination = Visibility data overlapping in frequency combined; SMA configurations combined
- 2018MNRAS.480.4991G: processing.imaging.array_combination = sessions combined into one measurement set per band
- 2025A&A...699A.316S: natural weighting, clean beam 4.84 x 2.79 arcsec
- 2020ApJ...892L..18I: processing.imaging.array_combination = Cycle 2 and 4 combined with weights inversely proportional to error variance
- 2019MNRAS.486.5552B: processing.imaging.array_combination = compact and extended configurations combined
- 2025A&A...696A.100G: processing.imaging.array_combination = TP + ACA 7m merged via GILDAS/MAPPING pseudo-visibilities (0-5 m), then merged with 12 m (0-12 m)
- 2025ApJ...979..142N: uv > 5 klambda
- 2025ApJ...979..142N: Baseband pairings: LSB-O with Band 4-Low, LSB-I with Band 4-High, USB-I with Band 5-Low, USB-O with Band 5-High
- 2025ApJ...979..142N: 32 walkers, uniform prior -5.0 < alpha < 5.0, 5000 Monte Carlo samples with Gaussian(mean=1, std=0.1) for ALMA calibration error
- 2018A&A...611A..99K: processing.imaging.array_combination = Concatenate ACA and 12 m configurations; ACA needed for continuum (80% flux in 12 m only for G302.02), not for H29α
- 2022A&A...662A...8M: robust = 0; spectral index α = 3.5; central frequencies ν_B6 = 228.965 GHz, ν_B3 = 100.713 GHz; FOV down to 15% primary beam sensitivity
- 2022A&A...662A...8M: processing.imaging.array_combination = Different 12 m array configurations combined; 7 m array and Total Power not combined for the present analysis due to increased noise and artifacts
- 2019ApJ...871..170M: phase-only self-cal, 60 s averaging, one iteration
- 2019ApJ...871..170M: processing.imaging.array_combination = CASA feather of 12m and ACA cubes
- 2023PASJ...75..646K: Briggs robust = 0.5
- 2023PASJ...75..646K: velocity resolution 5 km/s
- 2023PASJ...75..646K: processing.imaging.array_combination = 12-m and ACA 7-m data combined for CO(1-0); combined cube also for CO(3-2)
- 2025A&A...700A.165B: Low-res: +-30 km/s (three channels each side); high-res: 10 km/s width
- 2025ApJ...989...30Z: processing.imaging.array_combination = EBs concatenated; self-cal on short-baseline data, then on combined short+long baseline data
- 2025ApJ...988..172H: processing.imaging.array_combination = concat of the different tunings' measurement sets
- 2021A&A...646A..26B: processing.imaging.array_combination = Execution blocks from different cycles combined before imaging
- 2021A&A...646A..72H: processing.imaging.array_combination = Three ALMA projects concatenated into one measurement set with CONCAT
- 2018MNRAS.475..492K: processing.imaging.array_combination = concatenate the two datasets in each band
- 2019ApJ...881..159M: processing.imaging.array_combination = All datasets per band combined; Band 6+7 imaged together for spectral index
- 2017ApJ...842...94T: processing.imaging.array_combination = 12-m and ACA mosaic data combined
- 2019A&A...627A.114K: processing.imaging.array_combination = ALMA B7 combined with SMA data, weights recalculated in CASA
- 2025A&A...700L..11S: processing.imaging.array_combination = Visibilities from different configurations combined in the uv-plane with antenna-specific weighting
- 2026ApJ..1004..207M: Briggs robust 0.5; multiscale scales 0, 5, 15, 25, 50 x pixel; pixel 0.2''
- 2026ApJ..1004..207M: auto-multithresh: sidelobethreshold 1.75, noisethreshold 2, lownoisethreshold 1.5, negativethreshold 0, minbeamfrac 0.3
- 2026ApJ..1004..207M: processing.imaging.array_combination = 12 m + 7 m cleaned together, then TP combined with feather
- 2018ApJ...866..141K: processing.imaging.array_combination = 12-m and 7-m data combined for the 226 GHz mosaic
- 2021MNRAS.508.4639Z: Averaging aperture size = 36''; 12m+7m moment 1 velocity range = [-23, -16.5] km s^-1; ACA 7m blue/red integration ranges = [-60, -19.8] km s^-1 and [-19.8, 20…
- 2021MNRAS.508.4639Z: processing.imaging.array_combination = ACA 7m and ALMA 12m visibility data combined and jointly cleaned in tclean
- 2017PASJ...69...83M: Briggs robust 0.5, 0.05'' pixels, 1500x1500
- 2017PASJ...69...83M: processing.imaging.array_combination = TP combined with 12-m+ACA using Feather in CASA
- 2020MNRAS.494.2131F: alpha_CO = 4.4, R21 = 0.8
- 2020MNRAS.494.2131F: processing.imaging.array_combination = feathered with total power image
- 2026ApJ..1001...33L: processing.imaging.array_combination = 12m and 07m imaged jointly; combined with TP cube using MIRIAD immerge on commonly covered channels
- 2025ApJ...988..106H: processing.imaging.array_combination = short-baseline 2016.1.01042.S EBs self-calibrated, then long-baseline 2022.1.01365.S data aligned and combined
- 2026ApJ...999...47L: processing.imaging.array_combination = Measurement sets for individual SBs concatenated using CASA concat command and imaged collectively as a mosaic
- 2022MNRAS.515.1751W: processing.imaging.array_combination = Co-adding high-resolution and low-resolution [C II] visibilities in tclean using all available data sets combined
- 2023ApJ...948..110Y: processing.imaging.array_combination = Joint imaging of C43-6 and C43-9 after shifting target coordinates to June 23, 2019 using CASA fixplanets
- 2019MNRAS.482.3135B: processing.imaging.array_combination = ID 9: Cycle 4 and 5 continuum images made separately, combined with inverse-variance weighted mean
- 2019ApJ...883...98Z: processing.imaging.array_combination = IM Lup two programs combined after self-cal using fixvis and fixplanets
- 2018PASJ...70...85T: processing.imaging.array_combination = 12-m and 7-m mosaics both observed; combination method not stated
- 2020A&A...642A..93H: processing.imaging.array_combination = TM0 weight 0.2 relative to combined 2016 data; continuum equal weight per dataset
- 2018A&A...616A..34H: processing.imaging.array_combination = Continuum-subtracted data of ACA, TM1, TM2 combined with weights from intrinsic sensitivities, ratio ~1:5:6
- 2025A&A...702A.133K: deconvolver = 'multiscale' with 4 to 5 scales in geometric progression
- 2025A&A...702A.133K: threshold = 3 sigma, cyclefactor = 3 or 4, pixel size = 1/3 to 1/5 of clean beam minor axis
- 2025A&A...702A.133K: fitorder = 0 in imcontsub; kernel = 'commonbeam' in imsmooth
- 2025A&A...702A.133K: processing.imaging.array_combination = 7M+12M imaged together in tclean, then combined with TP using CASA task feathering
- 2019MNRAS.486..283B: processing.imaging.array_combination = feather of ALMA 12m+7m with BGPS, default parameters
- 2021ApJ...910...11O: robust = 0.5
- 2021ApJ...910...11O: processing.imaging.array_combination = 12-m (two configurations) and ACA 7-m visibilities combined in the uv plane
- 2017ApJ...850..139W: processing.imaging.array_combination = 12m + TP via CASA feather; ACA excluded (differences <~10%)
- 2023MNRAS.522.4078C: Briggs robust = 0.5, pixel size = 0.05'', channel width = 2 km s^-1, C40-3 weight = 0.2, C40-6 weight = 1.0
- 2023MNRAS.522.4078C: processing.imaging.array_combination = Manual weighting of 0.2 to C40-3 and 1.0 to C40-6, then combined with ACA using CASA task concat with default weighting
- 2026ApJ..1005...94N: processing.imaging.array_combination = CASA concat with visweightscale factors: 0.6 for uid_A002_Xea90c0_X334e (2019.1.00036.S) and 0.2 for each of uid_A002_Xe03886_X7606 and uid_A002_Xe03886_Xd75e …
- 2025NatAs...9.1672Y: processing.imaging.array_combination = 2024: self-calibrated short-baseline data combined with long-baseline data; all spectral windows used after flagging lines (setup 2)
- 2024A&A...686A.156D: processing.imaging.array_combination = CASA concat: HR+MR and HR+MR+LR visibility concatenations for each source.
- 2022A&A...664A..63X: processing.imaging.array_combination = Combined C40-4 and C40-7 in UV table with visibility weights 1:4 (high-res cube and high-res continuum) and 1:1 (total flux cube and low-res continuum)
- 2022MNRAS.513.5790C: processing.imaging.array_combination = Aligned in uv-plane using VisAlign, concatenated directly, visibility weights replaced via CASA statwt, followed by joint self-calibration and imaging with OOs…
- 2017ApJ...835...98U: processing.imaging.array_combination = uv data of all pointings/SBs combined into a single uv dataset
- 2019AJ....158...15P: processing.imaging.array_combination = concat of short and long baseline datasets after 20,40 mas offset correction
- 2019PASJ...71..128T: processing.imaging.array_combination = FEATHER with Total Power data for molecular lines
- 2022A&A...659A.109K: 30 km s^-1 spectral bin, natural weighting for SMA, 0.5'' aperture diameter for V5668 Sgr
- 2018A&A...609A..67K: processing.imaging.array_combination = TE, TC and combined cubes made
- 2025A&A...701A.219N: Central frequency 231.1 GHz; 7m: 5 blocks x ~470 s, 10-12 antennas; 12m: 1 block x ~360 s, 47 antennas; PWV ~1.8 and ~2.9 mm; elevation ~45 to ~72 deg
- 2025A&A...701A.219N: tclean: Mfs, mosaic gridding, Multiscale scales=[0, 7, 21], Briggs robust=0.5, Auto-multithresh, cell size=0.2", beam=1.29"x1.51"
- 2025A&A...701A.219N: processing.imaging.array_combination = joint deconvolution of 12 m and 7 m arrays with mosaic gridding in tclean
- 2017MNRAS.464L..31H: processing.imaging.array_combination = 12 m + 7 m visibilities combined
- 2021A&A...650A.202R: ACA visibility weight factor 2.4
- 2021A&A...650A.202R: processing.imaging.array_combination = ACA and 12m visibilities concatenated (ACA weight x2.4) before imaging
- 2018ApJ...867..111Z: robust 0.5; SD factor 1; 5 km/s channels
- 2018ApJ...867..111Z: processing.imaging.array_combination = FEATHER with SD factor 1
- 2023ApJ...958...53S: Velocity resolution 0.4 km s^-1; PB threshold 0.2 for 12CO(2-1) and 0.5 for 12CO(3-2) and 13CO(2-1); smoothed beam 3.5'' x 3.5''
- 2023ApJ...958...53S: processing.imaging.array_combination = feather task used to combine cleaned 7 m and calibrated TP data for CO(J=3-2), and cleaned 12 m and 7 m data for CO(J=2-1)
- 2025MNRAS.537..520Z: processing.imaging.array_combination = CASA task concat combining two C43-10 tracks, one C36-4 track, and one C40-7 track (excluding first C43-10 track uid_A002_Xf031e1_X16fe)
- 2025ApJ...985...84L: processing.imaging.array_combination = CS 3-2: SB and LB execution blocks concatenated before a further phase-only self-cal round
- 2024A&A...689A.145S: processing.imaging.array_combination = Multi-configuration data combined; JvM correction measured and applied per channel range with similar beam properties, following Czekala et al. 2021; mean fact…
- 2021ApJ...907...62R: processing.imaging.array_combination = CO(10-9): compact (C43-2/3) and extended (C43-5) configurations combined (Table 1 lists C43-2/3+5)
- 2021A&A...656A.150P: processing.imaging.array_combination = SB and LB combined after shifting all phase centres to the LB phase centre
- 2016ApJS..222....1F: processing.imaging.array_combination = cluster: statwt reweighting then concat of the datasets
- 2018ApJ...864...81O: processing.imaging.array_combination = Cycle 3 and Cycle 4 data combined in uv plane during tclean
- 2019ApJ...881L..42C: processing.imaging.array_combination = concat of the two continuum-subtracted datasets (12m+ACA)
- 2020A&A...644A..61H: processing.imaging.array_combination = all configurations combined with equal weight
- 2019MNRAS.484.1865H: processing.imaging.array_combination = IRAM pseudo-visibilities merged with ALMA 12-m data (CO 1-0 only); ACA/zero spacing absent for CO 2-1
- 2026A&A...706A.248T: natural weighting, MFS, hogbom, no mask
- 2026A&A...706A.248T: multiscale scales 0, 5, 10, 20 pixels; 0.5 km/s channels
- 2026A&A...706A.248T: processing.imaging.array_combination = ACA and 12m visibilities combined before imaging
- 2019PASJ...71...73T: processing.imaging.array_combination = feathering of 7 m and IRAM 30 m data per CASA instruction
- 2022MNRAS.512.4419P: processing.imaging.array_combination = 12-m and ACA combined for continuum and SiO (2-1), HCO+ (1-0), and CS (2-1) spectral lines
- 2019ApJ...883..145J: robust 2.0 for final maps
- 2019ApJ...883..145J: processing.imaging.array_combination = 12m and ACA cubes concatenated with CASA concatenate after checking weights
- 2020ApJ...890..149T: processing.imaging.array_combination = feathering on a per-channel basis; long-baseline execution Xc5148b/X127e only, combined with compact and intermediate
- 2026MNRAS.548ag546D: processing.imaging.array_combination = Concatenated (u,v) components from all four tracks (three 12-m tracks and one 7-m ACA track) imaged jointly in tclean
- 2026A&A...710A.238D: processing.imaging.array_combination = short-baseline self-calibrated independently before combination if flux variation > 10%, then combined and self-calibrated again; observations separated by < 2…
- 2025ApJ...985..243B: processing.imaging.array_combination = ALPINE compact-configuration data combined with new extended-configuration CRISTAL data
- 2023A&A...679A.119R: processing.imaging.array_combination = concatenated visibilities from multiple configurations and recalculated noise using statwt
- 2023MNRAS.523.4970N: processing.imaging.array_combination = Concatenated short and long baseline visibilities using CASA concat task
- 2018ApJ...865..106C: processing.imaging.array_combination = cycle3+cycle4 visibilities concatenated
- 2018ApJ...868L...5K: processing.imaging.array_combination = Long baseline combined with archival short-baseline data; phase centers aligned with fixvis
- 2018ApJ...859...86T: processing.imaging.array_combination = 12+7 m combined for 230 and 265 GHz
- 2021A&A...655A..80D: processing.imaging.array_combination = compact, mid, extended datasets combined
- 2026A&A...711A.239S: fitorder = 0 in channels 12 to 20 km s^-1 for imcontsub
- 2026A&A...711A.239S: S/N threshold = 12 for N2H+(1-0); 5 for DCN(3-2), C18O(2-1), SiO(5-4); 7 for H41alpha
- 2026A&A...711A.239S: processing.imaging.array_combination = feather task combining 7m, 12m, and Total Power (TP) data
- 2019ApJ...875...24C: processing.imaging.array_combination = 12-m + ACA + TP combined
- 2020MNRAS.491..178K: processing.imaging.array_combination = Feather of ACA 7m and TP; TP converted to the flux scale of the ACA data before feathering
- 2016ApJ...832..142Z: robust = 0.5; 6 sigma mask, clean to 4 sigma for CO(1-0)
- 2016ApJ...832..142Z: processing.imaging.array_combination = cubes combined with Total Power using FEATHER
- 2020A&A...634A.121H: processing.imaging.array_combination = 12m+7m joint imaging, feathered with Total Power
- 2026MNRAS.549ag781K: processing.imaging.array_combination = Combined TM1 and TM2 MSs jointly in tclean
- 2024PASJ...76..437Y: processing.imaging.array_combination = Compact-configuration data combined with long-baseline data when MRS < radii of known gap/ring features; phase centers aligned with fixvis and fixplanets
- 2024MNRAS.529L...1J: processing.imaging.array_combination = Eight accepted 3 hr JVLA executions concatenated (one excluded for calibration problems)
- 2021ApJ...909..130R: processing.imaging.array_combination = visibilities from both ALMA programmes (C43-1, C43-2, and C43-6 with baselines <= 1000 klambda) concatenated
- 2020ApJ...902L..33G: processing.imaging.array_combination = 12CO line imaging combined the 0.02'', 0.2'' and 1.1'' resolution datasets after recentring the 2019 and 2017 epochs on the secondary disk position
- 2017ApJ...845..138S: processing.imaging.array_combination = Cycle 1 combined with Cycle 0 data
- 2018ApJ...868L...3M: processing.imaging.array_combination = compact and extended concatenated
- 2017MNRAS.470.4209Y: processing.imaging.array_combination = Two epochs combined after scaling variable Sgr A* flux
- 2024ApJ...966..171M: Detection S/N >3; smooth marginal ~3 sigma spectra over two native channels before fitting
- 2024ApJ...966..171M: Generally adopt DCO+ when both lines are detected; use either detected line otherwise
- 2024ApJ...966..171M: processing.imaging.array_combination = 12 m + 7 m concat and joint cleaning; separate 7 m-only continuum images; TP C18O for clump velocity dispersion
- 2019ApJ...871..185L: Briggs robust=0; 0.01" pixels; 6000 pixels
- 2020ApJ...895..119T: Tkin = 16 K, Tex = 15 K
- 2017ApJ...835..265W: processing.imaging.array_combination = Mopra via Miriad immerge (16.2 Jy/K); IRAM via CASA feather (6.15 Jy/K); feathered cubes used as clean models via setjy
- 2020ApJ...903...94M: processing.imaging.array_combination = 12m+7m feathering; then ALMA combined with IRAM 30m by feathering
- 2026A&A...712A.227E: processing.imaging.array_combination = concat of compact (C-1) and extended (C-4 or C-3) MS files with 30 MHz frequency tolerance
- 2024A&A...687A.311A: processing.imaging.array_combination = OLD, SB and LB combined in the visibility plane; datasets centred with phaseshift on the cavity centre and flux-rescaled to a common reference
- 2024A&A...690A..55S: processing.imaging.array_combination = All ALMA spectral windows combined into a single 1D spectrum per source
- 2020ApJ...904..131N: processing.imaging.array_combination = All sources, cycles (and, in the full sample, 7 m data) imaged together in the uv-stack
- 2020ApJ...905...89Y: processing.imaging.array_combination = Calibrated visibilities of the same line or the continuum in the same band (from different projects) were combined for imaging
- 2016ApJ...826..112S: processing.imaging.array_combination = tracks of both configurations combined and imaged together
- 2016ApJ...831..101B: processing.imaging.array_combination = Compact and extended data combined; TW Hya phase centres aligned on continuum peak
- 2025ApJS..280...33Y: model spectrum width 50 km/s, shifted by field Vlsr
- 2025ApJS..280...33Y: uvcontsub linear fit, fitorder=1
- 2025ApJS..280...33Y: processing.imaging.array_combination = ACA and TM2 raw visibilities concatenated (concat) and imaged jointly; two-pointing clumps mosaicked except I12572-6316 and I17269-3312
- 2018A&A...617A..89C: processing.imaging.array_combination = 12 m + 7 m joint deconvolution for continuum and CO(3-2)
- 2023MNRAS.522.3719L: intensity threshold = 2.5 sigma, step = 1.0 sigma, minimum pixels = 1 synthesized beam, integrated flux cut >= 4 sigma
- 2023MNRAS.522.3719L: processing.imaging.array_combination = combined 12m+7m continuum data
- 2019A&A...627A...6S: K/Jy 19.17; velocity ranges -360<v<-260 and -260<v<-160 km/s
- 2019A&A...627A...6S: processing.imaging.array_combination = uv-plane combination of 12m and ACA within CASA
- 2020ApJ...893..135M: processing.imaging.array_combination = 12-m and ACA combined; NGC 3627 feathered with total power
- 2024MNRAS.531.4045C: processing.imaging.array_combination = C43-6 and C43-8 configurations combined
- 2025A&A...700L...5G: processing.imaging.array_combination = Different configurations combined after astrometric and flux corrections; older data rescaled before merging.
- 2024MNRAS.533.2966Q: processing.imaging.array_combination = all available MS files of a field combined into one map
- 2022MNRAS.510.3734D: processing.imaging.array_combination = Band 3: two 12m measurement sets independently calibrated and combined into one MS using CASA
- 2020NatAs...4..142L: processing.imaging.array_combination = Cycle 5 (C43-8) combined with Cycle 3 observations
- 2017ApJ...850...83F: processing.imaging.array_combination = HUDF projects combined with concat; weights recomputed with statwt
- 2019MNRAS.482L..29D: processing.imaging.array_combination = Band 6 + Band 7 combined with multi-frequency synthesis; pointing offset -11,-73 mas corrected
- 2025A&A...696A.202S: pblimit increased from 0.05 to 0.2 for the 7M12M product
- 2025A&A...696A.202S: Final cube: 0.23 km/s resolution, beam 2.3'' x 2.1'', BPA 89 deg
- 2025A&A...696A.202S: processing.imaging.array_combination = 12m + 7m combined in tclean (7M12M); 7M12M continuum-subtracted data feathered with TP (7M12M = high resolution, TP = low resolution)
- 2016ApJ...833..209O: processing.imaging.array_combination = 12-m and ACA combined in the uv plane in CASA
- 2020ApJ...888...56I: 0.4 km/s channels, robust=0.5, scales 0,5,9 pixels
- 2020ApJ...888...56I: processing.imaging.array_combination = Visibilities from both projects jointly deconvolved; 12CO feathered with APEX
- 2018ApJ...860L..14K: Briggs robust 0.5, 0.5" pixels, 5 km/s channels
- 2018ApJ...860L..14K: processing.imaging.array_combination = 12-m and ACA 7-m combined
- 2023A&A...673A..46B: processing.imaging.array_combination = Two execution blocks combined with CASA concat after split
- 2024ApJ...963..103G: processing.imaging.array_combination = Concatenated projects 2011.0.00348.S, 2015.1.01569.S, 2016.1.00027.S, and 2019.1.01641.S for Band 3 continuum (split at 110 GHz)
- 2025A&A...698A.115R: processing.imaging.array_combination = self-calibrated SB EB concatenated with the three LB EBs
- 2025PASP..137l4501T: processing.imaging.array_combination = Rest-framed MSs concatenated into one MS with CASA concat
- 2023ApJ...945..121U: processing.imaging.array_combination = Combined 2018.1.00035.L with existing ALMA data from 2013.1.00999.S and 2015.1.01425.S for five Hubble Frontier Fields
- 2021ApJS..257....6G: processing.imaging.array_combination = combined data from two different array configurations with CLEAN residual map scaling (Jorsater & van Moorsel correction)
- 2016ApJ...829L..10I: processing.imaging.array_combination = AzTEC1: 0.3'' data combined with high-resolution data, down-weighted by 1/10; multiscale CLEAN
- 2016ApJ...820L..40A: processing.imaging.array_combination = Visibilities shifted for proper motion and combined after excising line channels
- 2025A&A...693A.199C: Circular aperture ~30 arcsec
- 2025A&A...693A.199C: Smoothed velocity resolution 0.2 km s^-1
- 2025A&A...693A.199C: processing.imaging.array_combination = 12m + 7m ACA + Total Power images combined with feather in casa
- 2016ApJ...826...26T: processing.imaging.array_combination = 12 m and 7 m cleaned separately, then combined with single-dish map by feathering in Fourier space
- 2021ApJ...907L..15S: robust 0.5, hogbom, automask
- 2021ApJ...907L..15S: processing.imaging.array_combination = configurations imaged jointly
- 2018PASJ...70L...1M: processing.imaging.array_combination = TP combined with 12-m+ACA using Feather in CASA (Band 8)
- 2022MNRAS.512.1012C: processing.imaging.array_combination = ALMA and CARMA combined with Miriad immerge as a test; final analysis uses ALMA data only
- 2024MNRAS.535..729P: processing.imaging.array_combination = 12m+7m+TP for PHANGS galaxies; 12m and ACA 7m for NGC 625, NGC 1705, NGC 5253; 7m for NGC 6822; 12m for NGC 7793
- 2024AJ....167...66Y: processing.imaging.array_combination = compact and extended data concatenated
- 2025ApJS..278...45F: processing.imaging.array_combination = CASA concat of DUALZ with ALMA-HFF and ALCS data within 20 arcsec radius, weights by data depth
- 2020MNRAS.495.3124H: processing.imaging.array_combination = uv data of Cycle 5 and Cycle 6 observations combined (core [CII]; CO(4-3) around the entire structure)
- 2020ApJ...889L..24P: processing.imaging.array_combination = Short and long baseline datasets concatenated after correcting positional offset
- 2017A&A...605A..42C: processing.imaging.array_combination = Cycle 1 and Cycle 2 Band 6 visibilities combined, weights manually rescaled to match noise variance
- 2016ApJ...823L..10W: processing.imaging.array_combination = Three B7 datasets concatenated and stacked in uv domain after velocity regridding
- 2024MNRAS.535.1364Z: Pixel size 0.4 arcsec
- 2024MNRAS.535.1364Z: Imaged field to 20% power point, radius 44 arcsec
- 2024MNRAS.535.1364Z: processing.imaging.array_combination = main array + 7 m array combined before cleaning
- 2017ApJ...837...60B: processing.imaging.array_combination = 12-m and 7-m visibilities combined in uv-plane
- 2021A&A...648A..41V: Briggs robust=0.5 (continuum, 12CO), robust=2 (faint lines)
- 2021A&A...648A..41V: processing.imaging.array_combination = 7m+12m concatenated and cleaned; then feathered with TP (IRAS 15398, IRAS 16059); 7m+TP for J160115
- 2016A&A...594A..70K: processing.imaging.array_combination = Visibilities combined by weighting data sets in the uv plane for continuous amplitude vs uv-distance
- 2022MNRAS.516.4066L: processing.imaging.array_combination = Combined dataset of C43-5 and C43-8 configurations
- 2026A&A...707A..77H: processing.imaging.array_combination = five observations combined into one measurement set with concat
- 2024ApJ...964..190L: processing.imaging.array_combination = SB data concatenated to LB data before further self-calibration
- 2025A&A...693A.237I: processing.imaging.array_combination = Combined compact (C43-1/2/3), extended (C43-4/5/6), and archival ALPINE/CRISTAL+ visibilities (excluding ALPINE for CRISTAL-06, 07c, 08, 23c)
- 2020MNRAS.499.5136C: processing.imaging.array_combination = BDF-3299 new and old datasets combined
- 2020ApJ...895..109F: processing.imaging.array_combination = short and long baseline visibilities combined
- 2019ApJ...871...37H: processing.imaging.array_combination = Cycle 2 and 3 visibilities combined, weights rescaled with STATWT
- 2017MNRAS.465..834Z: processing.imaging.array_combination = Concatenated lower and higher resolution data from three epochs
- 2025SciA...11.6953M: Pixel size 0.4 arcsec (Band 3), 0.05 arcsec (Band 6)
- 2025SciA...11.6953M: Three rounds of phase-only self-calibration, shortest solution interval 12 s (Band 6)
- 2025SciA...11.6953M: processing.imaging.array_combination = ACA and 12 m data combined and imaged together in CASA (Band 3)
- 2019ApJ...886...36S: processing.imaging.array_combination = joint imaging of 12 m + 7 m
- 2021ApJ...910..148M: Cube velocity widths 0.1 (C18O, N2D+), 0.5 (DCN), 1.0 (CO, SiO) km/s
- 2021ApJ...910..148M: processing.imaging.array_combination = Image-plane combination with feather for 1.3 mm continuum, C18O, N2D+, DCN; uv-plane combination with concat for CO; no combination for SiO (ALMA low resolutio…
- 2019A&A...632A..33A: processing.imaging.array_combination = all configurations (TC, TE, TM2, TM1) concatenated
- 2022A&A...664A..60B: processing.imaging.array_combination = combination of extended and compact configurations
- 2025MNRAS.541.2540Z: processing.imaging.array_combination = concat of all tracks then joint tclean
- 2024ApJ...967...68H: processing.imaging.array_combination = Short (ACA) and long baseline measurement sets aligned to a common phase center and combined
- 2024ApJ...972..147C: processing.imaging.array_combination = 12m and 7m combined; Total Power excluded
- 2023ApJ...945...69R: processing.imaging.array_combination = Combined multi-cycle MSs using CASA concat (Cycles 2+3 for [O III]; Cycles 1+3 and Cycles 1+3+7 for [C II]) after adjusting Cycle 1 weights with statwt
- 2021ApJ...908....8C: processing.imaging.array_combination = concat of continuum-subtracted long and short baselines
- 2019MNRAS.487.4856M: processing.imaging.array_combination = Cycle 1, 3 and 5 data combined
- 2026A&A...706A.328L: robust = 0.5
- 2026A&A...706A.328L: processing.imaging.array_combination = ACA and 12-m data combined with concat; IRAM 30m added only for CH3OH
- 2017A&A...600A.141K: processing.imaging.array_combination = Joint imaging with weights adjusted by statwt
- 2020A&A...635A...2S: robust = 0.5; 1.0" circular super-resolution beam
- 2020A&A...635A...2S: processing.imaging.array_combination = ACA-only image as model in 12m clean, then FEATHER
- 2019A&A...623A..79C: processing.imaging.array_combination = all calibrated baselines combined into UV tables
- 2021A&A...645A..49G: processing.imaging.array_combination = Extended and compact data combined in the uv plane within the LRSK frequency reference frame
- 2025A&A...693A.174E: processing.imaging.array_combination = TE and TC concatenated with CONCAT after separate calibration
- 2024ApJ...974L..25D: processing.imaging.array_combination = All four Band 3 configuration EBs combined and imaged together
- 2026A&A...706A.285C: natural weighting; MFS; 3 sigma threshold
- 2020PASJ...72...69Y: processing.imaging.array_combination = ASAGAO data combined with archival 2015.1.00543.S and 2012.1.00173.S into one combined map
- 2020ApJ...893..101L: processing.imaging.array_combination = Executions of the same setting concatenated before imaging
- 2018ApJ...856...72O: processing.imaging.array_combination = 2 mm: two-pointing mosaic, concatenated visibilities
- 2026A&A...705L..16C: Beam 0.4 x 0.34 arcsec, rms 2.0 mJy/beam
- 2026A&A...705L..16C: processing.imaging.array_combination = C18O: 12m and 7m data combined
- 2019A&A...632A.101T: processing.imaging.array_combination = C43-1 and C43-4 combined for Band 6
- 2020ApJ...894...87C: Briggs robust 0.5; 0.6 arcsec uvtaper for combined
- 2020ApJ...894...87C: processing.imaging.array_combination = Two image sets: TP+7m, and TP+7m+12m; feathered with TP
- 2019ApJ...885...50W: processing.imaging.array_combination = Hybrid: separate 12m and 7m deconvolution, then joint imaging with union mask
- 2023MNRAS.521.3348N: processing.imaging.array_combination = ALMOND: 7-m + TP combined; PHANGS-ALMA: 12-m + 7-m + TP combined
- 2025ApJ...979..217S: processing.imaging.array_combination = CASA concat with equal weighting for ALMA 7m and 12m; CASA concat with 4:1 (A:C) weighting for VLA
- 2024ApJ...966...63Y: processing.imaging.array_combination = 12CN N=2-1: short-baseline continuum imaged and self-calibrated first, then combined with longer-baseline EBs; one EB with deviant amplitude-vs-uv flagged
- 2025A&A...699A.256P: processing.imaging.array_combination = concat of all programs into a single ms
- ... 259 more

### Assumptions (bibcode: value)
- 2024ApJ...968..131T: Peak T maps used instead of moment 0 to avoid velocity-range ambiguity; overlap of more than two velocity components along the line of sight judged not promine…
- 2024ApJ...968..131T: Critical line mass evaluated at 15 K; large 0.1 pc filament taken as width 0.1 pc with N ~1.5e22 cm^-2
- 2024ApJ...968..131T: Initial sheet 4000 cm^-3, 0.1 pc thick, 50 uG in-plane field, +-1 km/s inflow, isothermal, ambipolar diffusion
- 2018ApJ...853..171G: foreground column 5e21-5e22 cm-2
- 2023ApJ...944...49F: Average distance to Orion of 400 pc (6" corresponds to ~2500 au)
- 2023ApJ...944...49F: 12 m flux traces the disk while ACA flux traces combined disk plus inner envelope
- 2023ApJ...944...49F: Distance D = 400 pc, dust temperature T = 15 K, dust opacity = 2.57 cm^2 g^-1 at 700 μm scaled to 870 μm with beta = 1.8, dust-to-gas ratio = 0.01
- 2023ApJ...944...49F: Spherically symmetric freefall with total mass M = 0.25 M_sun, outer envelope radius r_outer = 2500 au, constant star formation rate, and protostellar lifetime…
- 2019Natur.569..519K: alpha_CO = 4.35 (Z/Zsun)^-1 Msun/(K km/s pc^2), 50% uncertainty
- 2023ApJ...953..164M: Distance D = 840 kpc (1'' = 4 pc)
- 2023ApJ...953..164M: R_21 = 0.6 applied to recalculate Corbelli et al. (2017) GMC masses
- 2023ApJ...953..164M: 8 um emission traces high-mass star-forming regions
- 2024MNRAS.530..597B: Distance to NGC 4038/9 = 22 Mpc
- 2021A&A...655A..42S: flux calibration accuracy 10%; astrometry accurate to 0.6 arcsec
- 2021A&A...655A..42S: sources unresolved by the ACA Band 4 beam
- 2021A&A...655A..42S: Bruzual and Charlot stellar emission, da Cunha 2008 dust emission, Charlot and Fall attenuation law, energy balance
- 2023NatAs...7..684K: V_LSRK = 5.7 km s-1; M_* = 2.4 M_sun for Keplerian mask
- 2023NatAs...7..684K: Continuum and C18O 3-2 emission peaks trace the central star location within the central 0.5" pixel
- 2021A&A...653A..53A: Gaussian emission distribution gives an initial envelope-size estimate.
- 2021A&A...653A..53A: TP observations cover the full extent of CO(2–1) emission.
- 2018A&A...617A..23B: Gaussian intensity distribution; uncertainties assume reduced chi2 of 1
- 2024A&A...692A..86H: Initial LTE ratio calculation neglects differential opacity and assumes LTE level populations.
- 2021A&A...654L...8C: The additional component at v~1500 km/s is too faint to fit and is excluded from the single-Gaussian fits
- 2021A&A...654L...8C: Unresolved ISM represented by a point source
- 2017ApJ...850L...6A: Star unresolved; non-thermal emission negligible
- 2017ApJ...850L...6A: Circular belt tilted; T_d ~10 K with same temperature law
- 2024MNRAS.527.4420M: 30 arcsec aperture captures total flux; extraction at 3 sigma level would lose on average 60% of flux
- 2022A&A...661L...4A: Arc-like modulations are associated with opacity variations and can be corrected by adjusting gains relative to the central field position in double-circle sca…
- 2021AJ....161..271F: Dust: 70% astrosilicate, 15% amorphous carbon, 15% water ice; size power law -3.5, 1 um to 1 cm; Band 7 opacity 1.9 cm2/g
- 2021AJ....161..271F: Band 6 emission scaled from Band 7 via free alpha_mm
- 2021AJ....161..271F: Toy model inclination 33 deg, stellar mass 1.56 Msun
- 2018A&A...619L...6N: FD disk-center Tb scaled to 7250 K
- 2021A&A...650A.153D: Isothermal ICM; thermal SZ relativistic correction from Itoh2004
- 2021A&A...650A.153D: Flat Λ Cold Dark Matter: ΩM=0.30, ΩΛ=0.70, H0=70.0 km s−1 Mpc−1
- 2021A&A...650A.153D: Do not model the extended radio source; extrapolate it with α=−1 to check contamination
- 2021A&A...650A.153D: Exclude EMU compact flux because extended radio emission may contaminate it
- 2021A&A...650A.153D: Dust opacity power law; β=1.5
- 2021A&A...650A.153D: ν0=c/350 μm; κ0=0.192 m² kg−1
- 2025ApJ...994..158G: C18O and C17O ACA-only spectra have negligible missing flux at the peak position because they are compact
- 2025ApJ...994..158G: 12CO and 13CO from ACA+TP; C18O and C17O from ACA-only
- 2024PSJ.....5..221C: Q(H2O) from cubic spline interpolation of SOHO Ly-alpha measurements, taken as applicable at the ACA spatial resolution
- 2019MNRAS.487.4037D: Diagonal noise covariance; CMB and confusion negligible
- 2019MNRAS.487.4037D: Te fixed at 7 keV
- 2017AJ....154..206L: temperature profile from HASI+CIRS feathered 60-100 km; CO abundance 5.06e-5
- 2023PASP..135c4501P: Flux scales of the interferometer and SD data are aligned; astrometry aligned; images corrected for PB response
- 2024A&A...689A..41V: Cosmology Planck2014_XIII, H0=67.7, Om=0.307; non-relativistic SZ (relativistic corrections neglected)
- 2024A&A...689A..41V: ACT and ALMA+ACA likelihoods independent
- 2024A&A...689A..41V: Local scaling relations of Arnaud2010 used for Y to M500
- 2020AJ....159..215L: Globally uniform production, Haser model
- 2015A&A...576L...2S: Missing short-spacing flux negligible
- 2021A&A...647A..10G: T_ex = 10-30 K and extended emission for H3S+ upper limit
- 2022ApJ...939L...6B: Point source model for the star
- 2024RAA....24f5011X: dust temperature of each ACA source equals the H2CO kinetic temperature
- 2024RAA....24f5011X: distance uncertainty 20% and flux calibration uncertainty 10% included in mass errors
- 2024RAA....24f5011X: L/M indicates evolutionary stage
- 2018ApJ...856..147O: Mean molecular weight 2.33
- 2022ApJ...927..218H: 2D axisymmetric YSO geometry (central star, accretion disk, envelope, bipolar cavity) with solar metallicity PHOENIX stellar atmospheres
- 2022ApJ...927..218H: Cavity wall polynomial index b = 1.5
- 2022ApJ...927..218H: 12C/13C = 50 in the Orion cloud to rescale 13CH3OH column density to main CH3OH
- 2023ApJ...949..108K: Single average T_sys per EB
- 2021MNRAS.508.5259M: Point-like continuum source at continuum map centroid; negative features in inverted cubes are purely spurious.
- 2021MNRAS.500.5500B: Axisymmetric ring geometry at distance d = 6 kpc, constant expansion velocity with no velocity dispersion across the ring
- 2021MNRAS.500.5500B: Axisymmetric ring at d = 6 kpc with r^-2 power-law density and temperature profiles anchored to RADEX outputs
- 2020ApJ...898..146M: Optically thin; r^-0.5 temperature profile; constant dust opacity
- 2026ApJ...999L..32R: Gaussian ACA primary beam response; origin at peak gas flux (<0.75'' offset from phasecenter)
- 2019A&A...629A.104G: Sources are point-like given the large beams
- 2019AJ....157..251T: 5% absolute flux error from calibrators
- 2023PASP..135b5002C: Grid Sources are unresolved on ALMA baselines
- 2024A&A...682A.186L: Eight literature gNFW pressure profiles considered (A10 UP/MD, M14 UP/NCC, L15 REF/8.0/8.5, G17 EXT)
- 2024A&A...688A..30B: integration time ratio C43-1 : ACA-7m = 1 : 7 to match sensitivities
- 2024A&A...688A..30B: 12m + IRAM-30m MACF map taken as the true emission distribution
- 2020MNRAS.496.2790L: Total core mass ~400 Msun from earlier work at average dust temperature 35 K; distance 5.2 kpc
- 2021ApJS..257...43L: Spatial and spectral variations of the noise in each cube are separable; conversion to molecular gas mass assumes Milky Way alpha_CO^(1-0) = 4.35 M_sun pc^-2 (…
- 2024MNRAS.527.1444A: Pure power-law radio spectrum S_nu propto nu^alpha; flux density errors < 10%; ALMA 108 GHz flux excluded from fit due to missing short spacings
- 2020MNRAS.494.4090C: ACA observations are unresolved, even for the largest sources.
- 2016A&A...593A.107L: Source spatially compact so missing short spacings not a concern
- 2021MNRAS.504.2687N: Isotropic sky brightness distributions
- 2020A&A...644A.152E: Rayleigh-Jeans law and LTE
- 2020MNRAS.492.6067M: same assumptions as for TRAPPIST-1
- 2024JApA...45...31M: Disk flux filtered out by lack of short spacings; only limb emission preserved
- 2019A&A...628A.100D: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected
- 2026A&A...708A.251X: Single-component graybody emission; Hildebrand (1983) dust opacity kappa_0 = 0.1 cm^2 g^-1 at 300 um (gas+dust), spectral index beta = 2.0, mean molecular weig…
- 2026A&A...708A.251X: Dust temperature changes slowly and 1.3 mm emission is purely thermal dust emission
- 2026A&A...708A.251X: Distance d = 2.8 kpc, deconvolution factor eta = 2.4, leaf dust temperature taken from mean of 18'' temperature map within leaf mask
- 2022MNRAS.514..578W: Spectral index alpha_nu = 3.75 between 225 GHz and 259 GHz resulting in a flux scaling factor of ~0.6
- 2022MNRAS.514..578W: Distance d = 8.1 kpc, dust temperature T = 20 K, spectral index beta = 1.75, dust opacity kappa_nu = 0.04 cm^2 g^-1 * (225 GHz / 505 GHz)^1.75, gas-to-dust rat…
- 2021MNRAS.503.1174K: Jet spectral index \alpha = -1.04 \pm 0.03 (explored range -0.7 to -1.5, and -1.2); cavity energy E_cav = 4pV; Lorentz factor 10^3 - 10^5 and photon index 2 fo…
- 2025ApJ...985..166K: Isothermal 15 K, LTE, optically thin C18O; dust opacity table of Semenov et al. 2003
- 2021A&A...646A..25Z: Dust emissivity spectral index beta ~ 1.5 for extrapolating ATLASGAL 870 um flux to 1.3 mm
- 2021A&A...646A..25Z: Leaves in the dendrogram have no substructures and correspond to dense cores; prolonged 7 m leaves (major-to-minor ratio > 2.5) with multiple contour subpeaks …
- 2020ApJ...896...36T: 13CO, C18O and continuum have no significant missing flux
- 2026ApJ...997...16H: Distance of ~400 pc for converting 25'' to 10,000 au
- 2026ApJ...997...16H: Optically thin emission and LTE across rotational temperatures (5 K, 7.5 K, 10 K)
- 2021PASJ...73..205T: Optically thin dust emission; D = 1.7 kpc; T_dust = 20-40 K for 341-GHz_ACA; T_dust = 100 K for 233-GHz; spherical geometry for n_H2
- 2026AJ....172..108L: Optically thin dust continuum emission; gas-to-dust ratio R_gd = 100; dust opacity kappa_nu = 0.9, 1.5, and 3.9 cm^2 g^-1 for 1.3 mm, 850 um, and 500 um; dust …
- 2026AJ....172..108L: r^-2 density profile with p/q = 0.22 (also compared with uniform density profile which increases beta by a factor of three)
- 2021MNRAS.503.4320F: Eq. 1 is valid for non-spherical sources using equivalent circle angular diameter Theta
- 2025ApJ...990..150A: Gaussian hyperfine line profiles, one common T_r, LTE
- 2025ApJ...990..150A: Background temperature 2.73 K (CMB)
- 2025ApJ...990..150A: 20 K adopted at the low end of 10-50 K because outflow cavities assumed cooler than outflowing gas
- 2023A&A...678A.194C: Dirty beam volume is integrated up to its first null to compute JvM epsilon factor
- 2024AJ....167...72D: Optically thin 1.3 mm dust continuum emission
- 2024AJ....167...72D: Dust mass opacity kappa_nu ~ 0.00899(nu/231 GHz)^beta cm^2 g^-1, gas-to-dust mass ratio = 100, dust opacity spectral index beta ~ 1.5
- 2024AJ....167...72D: Dust temperature T_dust ~ 15 K, distances D = 389 +/- 3 pc (Orion A), 404 +/- 5 pc (Orion B), 404 +/- 4 pc (lambda-Ori)
- 2025ApJ...979..142N: Rayleigh-Jeans approximation: alpha = 2 + beta, with power-law dust opacity kappa_nu propto nu^beta
- 2022A&A...662A...8M: Spectral index α = 3.5 corresponding to optically thin dust emission with emissivity index β = 1.5
- 2025A&A...700A.165B: Galaxy unresolved at ACA resolution; GMCs co-spatial with star clusters and unresolved
- 2025A&A...701A.219N: Synthetic clumps placed at heliocentric distance of 5.2 kpc matching HG24
- 2024ApJ...966..171M: Both lines trace the same physical location: dense gas
- 2020ApJ...895..119T: beta = 1.8 for flux scaling
- 2026A&A...705L..16C: C18O(2-1) emission expected to be optically thin at ~50 au
- 2024ApJ...966..117X: distance 2 kpc
- 2024A&A...692A.215C: Chabrier IMF; flat LCDM Om=0.3, OL=0.7
- 2024ApJ...964...34L: Extended CO snowline set by a past accretion burst of HOPS 373SW


### Limitations the authors admit
- 2024ApJ...968..131T: Velocity resolution of 1.6 km/s misses small velocity dispersion structures and cannot separate overlapping velocity components
- 2024ApJ...968..131T: TP coverage incomplete and non-uniform sensitivity
- 2024ApJ...968..131T: N(H2) is a lower limit because of CO freeze-out and the assumed uniform abundance
- 2024ApJ...968..131T: Widths only marginally resolved and biased by the FilFinder adapt_thresh input
- 2018ApJ...853..171G: Catalog potentially incomplete; completeness cannot be quantified
- 2018ApJ...853..171G: Column density maps not very accurate; SFR strongly dependent on assumed timescale
- 2023ApJ...944...49F: 30 of the 330 HOPS sources were excluded because they were very faint or noisy in the ACA data and presented imaging challenges.
- 2023ApJ...944...49F: Envelope mass and infall rate estimates assume a constant representative total mass (0.25 M_sun), isothermal 15 K dust, uniform opacity, and only count material within 2500 au, ignoring infalling gas…
- 2023ApJ...944...49F: The 12 m/ACA flux ratio can be affected by variations in initial core conditions, angular momentum, magnetic fields, multiplicity, dust temperature/opacity dependencies on luminosity, and short-times…
- 2019Natur.569..519K: Extinction correction might underestimate attenuation toward GMC density peaks
- 2019Natur.569..519K: eps_sf and eta_fb depend on CO-to-H2 and Halpha-to-SFR conversion factors
- 2023ApJ...953..164M: Beam smearing at 30 pc resolution makes compact C18O(J=2-1) emission undetectable in the ACA map.
- 2023ApJ...953..164M: Small clouds with minor axis dispersion smaller than the beam (sigma_min < sigma_beam) have undefined deconvolved radii and are excluded, as are clouds at the edge of the ACA FOV where primary beam c…
- 2023ApJ...953..164M: Assuming a constant R_21 = 0.60 across the M33 disk introduces an error of about 30% in M_CO because R_21 varies spatially from 0.4 to 0.8.
- 2023ApJ...953..164M: The catalog includes 147 clouds with peak S/N < 10, whereas CPROPS requires S/N >= 10 for stable recovery of cloud properties.
- 2023ApJ...953..164M: Distributions of cloud radius and velocity dispersion depend on the spatial and velocity resolutions of the input data cube due to the hierarchical structure of the ISM.
- 2024MNRAS.530..597B: Using a fixed 1 kpc radius to define central regions across PHANGS-ALMA galaxies means low stellar mass (smaller) galaxies have a larger fraction of contaminating disc pixels in their central 1 kpc, …
- 2024MNRAS.530..597B: Sensitivity limits truncate the detection of low surface density regions with large velocity dispersions, preventing determination of whether the velocity dispersion-surface density relation in merge…
- 2024MNRAS.530..597B: Virial parameter estimates do not account for external pressure confinement (e.g., from stellar surface density or cloud-cloud collisions) that could help bind the gas.
- 2024MNRAS.530..597B: Assuming a single Milky Way CO-to-H2 conversion factor across all of NGC 4038/9 is likely an oversimplification given expected spatial and temporal variations in mergers.
- 2025A&A...693A.286S: Upper limits on IMTT CO fluxes do not constrain gas masses; most limits reach the grid maximum
- 2025A&A...693A.286S: Resolved-structure fraction lower than Herbig, attributed to lower spatial resolution; lack of deep observations
- 2025A&A...693A.286S: Sample biased towards high accretors and brightest disks
- 2025A&A...693A.286S: Dust masses may be underestimated (optical depth, opacity), seen as high gas-to-dust ratios
- 2026A&A...706A.174A: Stellar mass and other SED-derived properties highly uncertain because of Lupus-I extinction
- 2026A&A...706A.174A: Lens redshift not confirmed; MUSE and FORS2 data too poor
- 2026A&A...706A.174A: Dust mass strongly depends on the assumed kappa and optical depth
- 2026A&A...706A.174A: Unresolved data and fixed GDMR and [CO]/[H2] prevent tight gas-mass constraints
- 2026A&A...706A.174A: A minor AGN contribution cannot be ruled out
- 2021A&A...655A..42S: Cannot quantify the differential-lensing bias in magnification
- 2021A&A...655A..42S: Lens-model uncertainties possibly dominated by systematics
- 2021A&A...655A..42S: Small sample and large calibration dispersion at low metallicity make the hypothesis hard to falsify
- 2023NatAs...7..684K: The ACA CS 7-6 observation is essentially unresolved because the 4.78" beam is nearly equal to the radial extent of the gas disk.
- 2023NatAs...7..684K: The DALI model lacks a smooth transition between the inner cavity and dust ring (having a sharp boundary instead) and does not include the outer dust gap between r ∼ 40 - 150 au in ∆_g/d.
- 2023NatAs...7..684K: Wedge splicing angles are measured in the image cube plane rather than projected onto the inclined 3D disk plane.
- 2023NatAs...7..684K: Grain-surface conversion of CO to CO2 ice (reactions 14-16) is not included in the DALI chemical network and is approximated by manually depleting initial H2O, O, and CO abundances; reverse timescale…
- 2016ApJ...832...37G: Missing flux relative to SCUBA-2 and a lack of more compact array data.
- 2019ApJ...875...96N: Observation time was ~20% of the requested time, insufficient to test the model
- 2018MNRAS.475..448T: Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density
- 2018MNRAS.475..448T: ALMA continuum lacks single-dish data so flux is underestimated
- 2021A&A...653A..53A: Missing flux and high noise can significantly alter Gaussian fits; sizes are first approximations.
- 2021A&A...653A..53A: Gaussian-size reliability decreases with increasing MLR.
- 2021A&A...653A..53A: Distance uncertainties affect linear sizes and model comparisons.
- 2021A&A...653A..53A: DY Gem's derived size likely does not represent its true CO(2–1)-emitting size.
- 2021A&A...653A..53A: RZ Sgr and FU Mon sizes are relatively unreliable because of aspherical structures.
- 2021A&A...653A..53A: Weak sources have low S/N and cannot be properly Gaussian-fitted.
- 2021A&A...653A..53A: Intrinsic asymmetric structures require additional observations and modelling.
- 2021A&A...653A..53A: Further molecular detections may require optimized analysis; no additional molecular-emission analysis was attempted.
- 2018A&A...617A..23B: Spherical symmetry assumed despite asymmetric emission
- 2018A&A...617A..23B: Weak lines too low S/N for uv fitting
- 2024A&A...692A..86H: ACA and NOEMA cover different spatial extents.
- 2024A&A...692A..86H: The north-western mass-ejection interpretation is limited by sensitivity and angular resolution.
- 2024A&A...692A..86H: The angular resolution cannot reliably map individual SiO maser spots.
- 2024A&A...692A..86H: High-velocity wings cannot be established confidently because of absorption and mass ejection.
- 2021A&A...654L...8C: Spectral analysis limited by low S/N
- 2021A&A...654L...8C: The ALMA dataset has poor coverage of the redshifted side of the CO line
- 2021A&A...654L...8C: ACA beam is too large to analyse kinematics in detail
- 2021A&A...654L...8C: Mass estimates are highly uncertain, with no constraint on the gas physical conditions
- 2017ApJ...850L...6A: Data insufficient for proper modeling; secondary source could be a noise peak
- 2026ApJ..1001..184M: Deconvolution does not conserve integrated flux, leading to underestimates of extended emission in the NH3 combination
- 2026ApJ..1001..184M: CO absorption cannot set how far in front the clouds are
- 2026ApJ..1001..184M: Exact line-of-sight distances remain hard to determine
- 2024MNRAS.527.4420M: ACA CO(1-0) may resolve out extended emission, which could inflate r21
- 2024MNRAS.527.4420M: J1430+1339 ACA CO(3-2) may be over-resolved and miss flux
- 2024MNRAS.527.4420M: Small number of sources with the required data limits conclusions about correlations
- 2024MNRAS.527.4420M: Low S/N limits the interpretation of multiple CO components
- 2013ApJ...774...73I: Clumps are approximately beam-sized; higher resolution will break them up
- 2018MNRAS.480.4974H: Coarse ACA resolution cannot resolve pairs closer than 2-3"; physical association unproven
- 2022A&A...661L...4A: Low spatial resolution (21 arcsec) of the single-dish Band 7 images prevents a detailed study of the association between ALMA and H-alpha features.
- 2022A&A...661L...4A: Absolute calibration jumps exist between datasets, and cross-normalization cannot replace true absolute calibration (e.g., using the Moon).
- 2022A&A...661L...4A: The Band 7 results rely on observations from a single day and require verification with additional data.
- 2021AJ....161..271F: Model-dependent total flux; ALMA flux about half of SCUBA-2 flux
- 2018A&A...619L...6N: Unexplained excess emission beyond the limb up to 1000 K; segregation method not unique
- 2021A&A...650A.153D: Chandra source counts do not constrain the ICM temperature distribution.
- 2021A&A...650A.153D: Most X-ray hardness structures have low significance.
- 2021A&A...650A.153D: Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map.
- 2021A&A...650A.153D: SZ masses may be biased by nonhydrostatic gas and mass–inner-slope degeneracy.
- 2021A&A...650A.153D: Limited spectral coverage leaves thermal and kinetic SZ strongly degenerate.
- 2021A&A...650A.153D: Interferometric filtering favors compact, low-mass pressure models and limits extrapolation to large scales.
- 2021A&A...650A.153D: Weak-lensing positional precision limits confidence in the southern gas–mass offset.
- 2021A&A...650A.153D: Dust mass and temperature require better high-frequency observations.
- 2025ApJ...994..158G: Single sightline/cloud; representativeness for the whole SMC unknown
- 2025ApJ...994..158G: 12CO shows moderate missing flux in ACA-only data
- 2025ApJ...994..158G: Single Gaussian component assumed for simplicity; 12CO optical depth leads only to lower limits on 16O/18O and 16O/17O
- 2016A&A...595A.117J: Abundances relative to H2 highly uncertain as continuum is optically thick
- 2024PSJ.....5..221C: Raw statistical significance of the HC15N and H13CN detections is low
- 2024PSJ.....5..221C: HCN and isotopologues were observed on different dates, so variations in Q(H2O) and HCN/H2O enter the uncertainty
- 2024PSJ.....5..221C: CN may have an additional source beyond HCN photolysis, so CN/C15N need not equal HCN/HC15N
- 2019MNRAS.487.4037D: Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations
- 2017AJ....154..206L: C3H8 lines blended so abundance uncertain; south pole partly hidden
- 2025A&A...703A..15M: Dust mass uncertainties are formal only and do not include systematic uncertainties in dust opacity (which can reach a factor of several) or non-single dust temperatures.
- 2025A&A...703A..15M: CO mass estimates assume LTE at 20 K and ISM isotopic ratios; non-LTE/subthermal excitation, different kinetic temperatures, isotope-selective photodissociation, or fractionation can alter true CO ma…
- 2025A&A...703A..15M: Predicted collisional mass loss rates (M_dot_Dmin) have large uncertainties (40-60% formal, potentially much larger systematically) because smallest grain sizes may deviate from the blowout size in h…
- 2025A&A...703A..15M: Secular planet stirring calculations assume a massless disk and neglect disk self-gravity, which would require a more massive planet if the disk mass exceeds the planet mass.
- 2018A&A...617A.129K: Masses are lower limits, accurate to about a factor of ~2 at best owing to the CO/H2 conversion; line saturation uncertain
- 2018A&A...617A.129K: Velocity field and density degenerate in the Shape model
- 2015ApJ...808..102K: Inner radii unreliable due to resolution and decoherence; constant beta assumed; kappa0 uncertain by factor two
- 2023PASP..135c4501P: Test cases exclude bright emission extending beyond the well-characterised primary beam
- 2023PASP..135c4501P: At SD resolution the M100 comparison has few voxels per channel, making ~10% differences hard to interpret
- 2023PASP..135c4501P: Standard values were assumed for reduction parameters (briggs, sdfactor, sdgain) for simplicity
- 2026MNRAS.546ag037E: Scaling archival mm fluxes from 98, 104, and 350 GHz to 230 GHz assuming a flat spectral index (alpha = 0) introduces uncertainties of ~6% to 14%.
- 2026MNRAS.546ag037E: Non-simultaneous mm and X-ray observations (especially for A0620-00 where Chandra data is from 2013 and F_var = 0.83, and GRS 1915+105 with a 9-month gap) mean temporal variability can significantly …
- 2026MNRAS.546ag037E: Potential contribution from the donor star wind to the mm emission of Cygnus X-1 is not modeled.
- 2026MNRAS.546ag037E: Large uncertainties in the free parameters describing plasma physics in both ADAF and compact jet models (kept fixed to default values calibrated only for SMBHs) prevent strong conclusions about the …
- 2014A&A...570L..14R: Only ~50% of extended flux recovered even with ACA; dynamic range limited to ~50
- 2013Natur.499..450B: Outflow rate is uncertain due to alpha_CO and geometry
- 2024A&A...689A..41V: Lack of short baselines makes beta–P0 degeneracy and template discrimination weak; gNFW poorly suited for filaments
- 2020AJ....159..215L: Model is extremely simplified; Cycle 3 flux likely not fully recovered
- 2020ApJ...890..167T: A single source of ~1e4 Msun cannot explain T2 and T3 kinematics; diffuse mass distribution possible
- 2015A&A...576L...2S: Delivered data did not meet requested sensitivity; ~25% flux calibration uncertainty
- 2021A&A...650A.117N: Scheduled ALMA Band 9 observations could not be performed due to weather constraints.
- 2021A&A...650A.117N: The faint ATCA 5.5 GHz extended emission near the GRB site is at the ~5 sigma level, so there is no guarantee that it is real and it is too faint to split in time or frequency.
- 2021A&A...650A.117N: Small angular sizes (< 0.2''), faintness, and strong host foreground emission prevent MUSE from clarifying the nature of individual clumps C-G and K-M.
- 2021A&A...650A.117N: Low S/N in the outskirts of the galaxy prevents measuring E(B-V)_host, EW(Halpha), or a secure SFR at the GRB explosion site.
- 2021A&A...650A.117N: Apparent lower metallicity in region B and high velocity dispersions (~60 km s^-1) in the outskirts could be affected by low-number statistics or low S/N.
- 2021A&A...647A..10G: Bad weather limited SOFIA/GREAT observations to ~70 min on a single flight, so the achieved rms (50 mK) is insufficient for an unambiguous detection of SH, providing only upper limits.
- 2021A&A...647A..10G: Specific inelastic collision rate coefficients for SH with H and H2 are not available, requiring mass-scaling from SH-He rates without hyperfine resolution.
- 2021A&A...647A..10G: Gas-grain models do not include formation of more complex S-bearing ices (s-OCS, s-H2S2, s-S_n, s-SO2, s-HSO) or gas-phase reactions of S+ with desorbed organic molecules like H2CO, and assume steady…
- 2021A&A...647A..10G: Low-temperature (< 1000 K) radiative and dielectronic recombination rates of S+ used in PDR models may not be sufficiently accurate.
- 2022ApJ...939L...6B: Shorter integration times imply higher rms noise, so fainter flares will not be detected.

### Settings cards flag as needed but not stated
- casa version: 30
- line-free channels and continuum subtraction method: 15
- line-free channels used for continuum: 15
- flux scale uncertainty: 13
- self-calibration solution intervals: 11
- image size and cell size: 11
- line-free channels for continuum subtraction: 11
- line-free channels used for continuum subtraction: 10
- continuum subtraction and line-free channels: 10
- casa version and pipeline version: 9
- primary beam correction details: 9
- continuum subtraction method and line-free channels: 8
- self-calibration solution intervals and number of iterations: 8
- line-free channel ranges for continuum subtraction: 7
- line-free channels and continuum subtraction: 7
- line-free channel ranges for continuum: 7
- flux calibrator and flux scale uncertainty: 6
- line-free channels used for uvcontsub: 6
- line-free channels for uvcontsub: 5
- flux calibrator and flux-scale uncertainty: 5
- flux calibrators and flux scale uncertainty: 5
- cell and image size: 5
- casa version and calibration procedure: 5
- casa version and whether the pipeline or manual calibration was used: 4
- self-calibration status: 4
- line-free channel selection: 4
- self-calibration solution intervals and number of rounds: 4
- continuum-subtraction and line-free channels: 4
- line-free channel ranges used for continuum: 4
- primary-beam correction details: 4
- casa version used for calibration and imaging: 3
- pipeline version: 3
- feathering parameters: 3
- line-free channels / continuum subtraction: 3
- line-free channels for continuum: 3
- exact casa version and pipeline version used for calibration and imaging: 3
- clean threshold, masks, cell and image size: 3
- line-free channel ranges used for uvcontsub: 3
- line-free channel ranges for uvcontsub: 3
- flux calibration uncertainty: 3

## Paper excerpts (40 of 714, chosen for detail and spread over fields/years)

### 2024ApJ...968..131T: Internal 1000 au Scale Structures of the R CrA Cluster-forming Cloud. I. Filamentary Structures (2024; star_formation, milky_way_ism; observational_alma_primary)
- question: What filamentary sub-structures exist inside the dense, cluster-forming R CrA clump, what are their physical properties (widths, column density, line mass, velocity), are they gravitationally unstable and star-forming, and how do they form
- processing.imaging.array_combination: TP images for C18O and SO regridded to the 7m pixel scale and combined with the 7m image using CASA feather [Data reduction: "The TP array data for C$^{18}$O and SO were regridded at the same pixel scale as the 7m-array image and combined by the `feather` task."]
- step 1: Image the 7m data and combine with TP
  - method: Concatenate all calibrated 7m and TP measurement sets, image with tclean (multi-scale, natural weighting, auto-multithresh), then feather TP with the 7m image [Data reduction: "we concatenated all of the visibility files and imaged them together"] [Data reduction: "The TP array data for C$^{18}$O and SO were regridded at the same pixel scale as the 7m-array image and combined by the `feather` task."]
  - software: CASA, tclean, feather
  - parameter: natural weighting, multi-scale deconvolver, auto-multithresh mask, 1'' x 1'' pixels [Data reduction: "We applied the natural weighting"] [Data reduction: "the CLEAN mask was automatically created using the `auto-multithresh` procedure"]
  - validation: Combined and TP images compared to check that 7m sub-structures are not edge artifacts [Overall properties of the cloud: "This can be confirmed by comparing the combined image with the TP array image."]
- step 2: Identify filamentary structures (feathers) and measure widths
  - method: FilFinder run on 7m-only peak antenna temperature maps; skeletons split at junctions into branches; Gaussian fit across the ridge for width [Properties of the filamentary substruct…: "For the C$^{18}$O and SO images reported here in detail, an algorithm for filament identification, FilFinder, was used (cite: koch15)"] [Properties of the filamentary substruct…: "They were obtained by fitting the intensity distribution perpendicular to the ridge, assuming the Gaussian distributions."]
  - software: FilFinder
  - parameter: detection limit 3 sigma = 0.075 K; minimum structure size 600 pixels (1 pixel = 1'' x 1'') [Properties of the filamentary substruct…: "we set $3\sigma = 0.075$ K as the detection limit and the minimum size of the structure as 600 pixels"]
  - parameter: skeleton ridge longer than 5 beam sizes; branches shorter than 3 beam sizes discarded [Properties of the filamentary substruct…: "if the ridge has a length longer than 5 times the beam size"] [Properties of the filamentary substruct…: "After discarding short branches less than 3 times the beam size"]
  - parameter: adapt_threth = 0.006 pc [Properties of the filamentary substruct…: "FilFinder provides an input parameter, `adapt_threth` (0.006 pc in this case), which is an estimate of the filament width to be identified"]
  - parameter: smooth_size = 0.003 pc [Properties of the filamentary substruct…: "the `smooth_size` (0.003 pc in this case) were set to eliminate small noise fluctuations when creating the mask."]
  - assumption: Peak T maps used instead of moment 0 to avoid velocity-range ambiguity; overlap of more than two velocity components along the line of sight judged not prominent [Properties of the filamentary substruct…: "Technically, the use of the Peak $T$ maps, not the moment 0 maps, is advantageous as it allows us to exclude ambiguity related to velocity-range selection."]
  - fitting: Gaussian fit to the intensity profile perpendicular to the ridge, implemented in FilFinder [Properties of the filamentary substruct…: "They were obtained by fitting the intensity distribution perpendicular to the ridge, assuming the Gaussian distributions."]
  - validation: Feathers found in 7m data lie inside the extended TP structures, not on edges, so not artifacts; width bias from the adapt_thresh input admitted [Overall properties of the cloud: "show that all the filamentary sub-structures found in the 7m array are embedded inside of the extended structures, rather than located at the edges"] [Properties of the filamentary substruct…: "so there remains a bias in the extracted filamentary structure width"]
- step 4: Line mass and stability of feathers
  - method: Line mass from average column density and branch width for 7m-only and 7m+TP N(H2); compared with critical line mass 2Cs^2/G [Column density distributions and embedd…: "we estimated the mass per unit length (line mass, $M_{\rm line}$) from the average column density and the filament width obtained above."] [Column density distributions and embedd…: "The critical line mass for gas with temperature of 15 K is $24\ M_{\ensuremath{\odot}}\,{\rm pc}^{-1}$"]
  - parameter: SO: assumed density equal to critical density 2e6 cm^-3 and width 1500 AU [Column density distributions and embedd…: "we assume the average density same as the critical density of $2 \times 10^6$ cm$^{-3}$ for the SO emission lines"]
  - assumption: Critical line mass evaluated at 15 K; large 0.1 pc filament taken as width 0.1 pc with N ~1.5e22 cm^-2 [Column density distributions and embedd…: "assuming that the extended structure with a column density of $\sim 1.5\times 10^{22}$ cm$^{-2}$ at the center is a filament with the width of 0.1 pc"]
  - validation: Median line masses much below critical; statistics of YSO association used as a consistency check [Line mass and dynamical stability of th…: "From these facts, it seems that the feather structures cannot be unstable with self-gravity alone and do not fragment and collapse."]
- step 5: Associate feathers with YSOs and continuum sources
  - method: Compare feather positions with catalogued Class 0/I YSOs; match 1.3 mm continuum peaks to IR coordinates within 2 arcsec [Overall properties of the cloud: "6 sources are clearly detected in the 1.3 mm continuum as the counterparts with the separations less than 2 arcsec between the 1.3 mm peak positions and the catalogued IR coordinates"]
- step 6: Inspect velocity field of feathers
  - method: C18O moment 1 map of the 7m data compared across feathers [Velocity fields: "In spite of the poor velocity resolution, the moment 1 map exhibits noticeable velocity change among feathers."]
  - validation: Limited by 1.6 km/s velocity resolution [Velocity fields: "In the present spectral setup, the velocity resolution of C$^{18}$O is 1.6 km s$^{-1}$, which is not sufficient to discuss small changes in the velocity field and spectral shapes."]
- step 7: Compare with MHD colliding-flow simulation
  - method: Qualitative comparison of simulated column density map and horizontal cut at 1.3 Myr with the observed feathers and column density cuts [Comparison with MHD simulations: "A horizontal cut of this column density distribution is shown in Fig. [11](#fig:MHDsim) bottom."] [Comparison with MHD simulations: "These visual characteristics reproduce the observation well."]
  - assumption: Initial sheet 4000 cm^-3, 0.1 pc thick, 50 uG in-plane field, +-1 km/s inflow, isothermal, ambipolar diffusion [Comparison with MHD simulations: "Gas flow with a velocity of $\pm 1$ km s$^{-1}$ is given from both sides in the $x$ direction, and the gas is converged at the center."]
  - validation: Qualitative visual match of peak widths ~0.01 pc on ~0.1 pc structures and similar column densities [Comparison with MHD simulations: "Sharp density peaks with widths of about 0.01 pc are seen on top of the structure that extends about 0.1 pc."]
- result: Number of C18O filamentary branches (feathers) = 101 ± not stated dimensionless [abstract: "We identify 101 and 37 filamentary structures with a few thousand AU widths in C$^{18}$O and SO, respectively"]
- result: Number of SO filamentary branches (feathers) = 37 ± not stated dimensionless [abstract: "We identify 101 and 37 filamentary structures with a few thousand AU widths in C$^{18}$O and SO, respectively"]
- result: Branches with successful width estimates (C18O, SO) = 95 and 37 ± not stated dimensionless [Properties of the filamentary substruct…: "we obtained successful estimations of widths for 95 and 37 branches of C$^{18}$O and SO, respectively"]
- result: Median feather width (C18O, SO) = 0.0064 pc (1300 AU) and 0.0055 pc (1100 AU) ± not stated pc [Properties of the filamentary substruct…: "with medians of 0.0064 pc (1300 AU) and 0.0055 pc (1100 AU), respectively"]
- result: Maximum feather width = 0.01 ± not stated pc [Properties of the filamentary substruct…: "The maximum width is 0.01 pc"]
- result: C18O feathers overlapping SO structures = 19 of 110 C18O (as printed) and 16 of 37 SO ± not stated dimensionless [Properties of the filamentary substruct…: "19 out of the 110 C$^{18}$O structures overlap with the SO structures, while conversely 16 out of the 37 SO structures do"]
- result: Line mass range and median, 7m only = 0.1 - 4.8, median 0.5 ± not stated Msun/pc [Column density distributions and embedd…: "They were distributed in the range of 0.1 – 4.8 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$ with a median value of 0.5 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$"]
- result: Line mass range and median, 7m+TP = 0.3 - 9.3, median 1.4 ± not stated Msun/pc [Column density distributions and embedd…: "and 0.3 – 9.3 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$ with a median value of 1.4 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$, respectively"]
- result: Critical line mass at 15 K = 24 ± not stated Msun/pc [Column density distributions and embedd…: "The critical line mass for gas with temperature of 15 K is $24\ M_{\ensuremath{\odot}}\,{\rm pc}^{-1}$"]
- result: Line mass of the 0.1 pc extended structure = approximately 30 ± not stated Msun/pc [Column density distributions and embedd…: "the line mass is approximately $30\ M_{\ensuremath{\odot}}\,{\rm pc}^{-1}$"]
- result: Median and highest feather volume density = 2.1e5 (median), 1.2e6 (highest) ± not stated cm^-3 [Line mass and dynamical stability of th…: "The median density of the feather is $2.1 \times 10^5$ cm$^{-3}$, and the highest one is $1.2 \times 10^6$ cm$^{-3}$."]
- result: Feathers associated with YSOs (C18O, SO) = 11 of 101 and 6 of 37 ± not stated dimensionless [Properties of the filamentary substruct…: "Overall, only 11 and 6 out of the 101 C$^{18}$O and 37 SO filamentary structures, respectively, are associated with YSOs."]
- result: Class 0/I sources detected in 1.3 mm continuum = 6 of 11 ± not stated dimensionless [Overall properties of the cloud: "6 sources are clearly detected in the 1.3 mm continuum as the counterparts with the separations less than 2 arcsec between the 1.3 mm peak positions and the catalogued IR coordinates"]
- result: Velocity dispersion among feathers = ~1 ± not stated km/s [Velocity fields: "The velocity dispersion among feathers is about $\sim 1$ km s$^{-1}$."]
- limitation (authors): Velocity resolution of 1.6 km/s misses small velocity dispersion structures and cannot separate overlapping velocity components [Properties of the filamentary substruct…: "Also, structures with different radial velocities that may overlap on the line-of-sight are not separated."]
- limitation (authors): TP coverage incomplete and non-uniform sensitivity [ALMA ACA observations: "the achieved sensitivity is different for each of them, because the executions of the project timed out in the cycle"]
- limitation (authors): N(H2) is a lower limit because of CO freeze-out and the assumed uniform abundance [Distribution of the feather structures: "However, such region is limited and a uniform abundance distribution is assumed in this paper."]
- not stated (card): multi-scale scales list, niter, threshold, gain and the auto-multithresh parameters in tclean; image size, phase centres and mosaic gridding per field, and primary-beam correction; spectral window and channels used for the continuum and whether continuum was subtracted from the lines; how the TP data were calibrated and imaged, and feather parameters (SDfactor, uv ranges); conversion of Jy/beam t…

### 2018ApJ...853..171G: Distributed Star Formation throughout the Galactic Center Cloud Sgr B2 (2018; star_formation, milky_way_ism; observational_alma_primary)
- question: Is there extended, distributed star formation across the Sgr B2 cloud beyond the N, M, S protoclusters, and how do star formation thresholds and surface density relations compare with local clouds?
- processing.imaging.array_combination: 7m+12m (and TP) combined into single dataset [2.1 ALMA data: "The ALMA QA2 calibrated measurement sets were combined to make a single high-resolution, high-dynamic range data set."]
- step 5: Column density maps and thresholds
  - method: Herschel SED fits at 25", combined with SHARC/SCUBA via feathering; column densities at source positions; compare with Lada+2010 and Krumholz+2008 thresholds [2.2 Other data: "we created several column density maps using different assumptions about the dust temperature."]
  - software: uvcombine
  - parameter: constant T=20 and 50 K maps plus SED-temperature maps; SCUBA scaled by 3x [2.2 Other data: "We had to scale the SCUBA data up by a factor $\approx3$"]
  - assumption: foreground column 5e21-5e22 cm-2 [2.2 Other data: "This material may have column densities as low as 5$\times 10^{21}$ $\textrm{cm}^{-2}$ or as high as 5$\times 10^{22}$ $\textrm{cm}^{-2}$"]
  - validation: feathering experiments with SCUBA scaling 0.5x-10x [Appendix Single Dish Combination: "we show the images and resulting histograms when we combine the Herschel data with the SCUBA data scaled by a range of factors from $0.5\times$ to $10\times$"]
- limitation (authors): Catalog potentially incomplete; completeness cannot be quantified [3.1: "Our selection criteria result in a reliable but potentially incomplete catalog"]
- limitation (authors): Column density maps not very accurate; SFR strongly dependent on assumed timescale [4.1.1: "our estimate of the star formation rate remains strongly dependent on the assumed star formation timescale"]
- not stated (card): tclean image size, cell size, multiscale scales and primary-beam mask details; self-calibration solution intervals and per-iteration imaging parameters (only in script); exact by-eye source selection and per-source peak/photometry procedure; Herschel SED-fitting details (Battersby et al. in prep) and dust opacity for column density maps; uvcombine/feather weighting parameters; cluster radius defi…

### 2023ApJ...944...49F: 300: An ACA 870 μm Continuum Survey of Orion Protostars and Their Evolution (2023; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Characterize the evolution of protostellar envelopes and test whether the ALMA 12 m to ACA 870 μm continuum flux ratio serves as an evolutionary indicator that avoids inclination and foreground extinction degeneracies affecting SED-based c…
- step 2: Determine source centroids and classify ACA envelope morphologies
  - method: Find emission centroid using photutils centroid_quadratic (fallback to centroid_2dg, then manual selection). Compare the area of the half-maximum contour of the central 9x9 pixels to the restoring beam area, and check if the 12 m disk posi… [3.2. Observed Morphologies: "To classify envelopes by their morphology, we first compare the ratio of the area of the half-maximum contour to the area of the restoring beam."] [3.3. Flux Measurements: "To measure flux, we first calculate the centroid of the ACA emission using the centroid_quadratic function of the publicly available photutils Python package from astropy (Bradley et al. 2020)."]
  - software: astropy, photutils
  - parameter: Area ratio < 1.3: unresolved; 1.3 to 2.4: compact; > 2.4: extended; shared continuous half-max contour: multiple; 12 m disk outside half-max contour: offset [3.2. Observed Morphologies: "For sources where the area of the half-maximum contour is less than 1.3 times the area of the restoring beam, these can be considered to be unresolved or marginally resolved."] [3.2. Observed Morphologies: "Sources where the ratio of half-max contour to beam area is between 1.3 and 2.4 we designate as “compact,” with the flux concentrated within the center region."]
  - fitting: 2D quadratic polynomial fit (centroid_quadratic) or 2D Gaussian fit (centroid_2dg) for centroiding [3.3. Flux Measurements: "That function attempts to calculate a centroid by fitting a 2D quadratic polynomial to a narrow region of the data."] [3.3. Flux Measurements: "If centroid_quadratic fails to return a position, we attempt to calculate the centroid with centroid_2dg, which attempts to fit a 2D Gaussian to the data."]
  - validation: Boundary value of 2.4 determined from visual inspection of the sources [3.2. Observed Morphologies: "The boundary value of 2.4 was determined from visual inspection of the sources."]
- step 3: Measure ACA 870 μm continuum flux densities
  - method: Measure flux in three ways: beam flux at peak pixel in central 9x9 pixels, beam flux at 12 m disk position, and integrated flux using photutils aperture_photometry within a 6" radius circle convolved with the beam FWHM. Adopt convolved ape… [3.3. Flux Measurements: "To address these complications, we measure flux in three ways: by taking the beam flux at the peak pixel in the central 9 × 9 pixels, taking the beam flux at the position of the disk as seen in the 12 m data, and by measuring the integrated flux within an aperture."] [3.3. Flux Measurements: "Since this radius is close to the angular resolution of the ACA data, we use the integrated flux measured within a 6″ radius circle convolved with the beam FWHM, which accounts for emission spread outside of the 6″ radius circular aperture."]
  - software: astropy, photutils
  - parameter: 6" (~2500 au) aperture radius convolved with beam FWHM; 5-sigma detection threshold [3.3. Flux Measurements: "If the integrated aperture flux is less than five times the integrated F ν rms level (in millijanskys), we adopt the 5σ uncertainty as an upper limit for the flux."]
  - assumption: Average distance to Orion of 400 pc (6" corresponds to ~2500 au) [3.3. Flux Measurements: "Fischer et al. (2017) used fits to SEDs to examine the masses of the inner ∼2500 au (6 ″ at the average distance for Orion) of the best-fit model envelopes."]
  - validation: Inspected curves of growth to verify the convolved aperture recovers target flux without large-scale spatial filtering fluctuations; compared ACA fluxes of bright isolated sources (HOPS-287, HOPS-376, HOPS-404) against single-dish APEX/LAB… [3.3. Flux Measurements: "By comparing the radii of the apertures to the curves of growth, we determine that our convolved aperture is appropriate for the majority of sources, recovering the flux of the target source without being sensitive to fluctuations at larger scales."] [Appendix A Comparison to Single-dish Fl…: "We pick out the bright, isolated sources HOPS-287, HOPS-376, and HOPS-404, to test if we are recovering the correct flux with our improved angular resolution."]
- step 4: Calculate 12 m/ACA flux ratios (R), envelope fluxes, and statistical comparisons across SED classes
  - method: Calculate R = F_nu(12 m) / F_nu(ACA) and envelope flux = F_nu(ACA) - F_nu(12 m), summing 12 m disk fluxes when multiple 12 m sources fall within the ACA half-max contour. Perform Kolmogorov-Smirnov (K-S), Anderson-Darling (A-D), Spearman r… [4.2. The 12 m to ACA Flux Ratio: "For this work, in the case of multiple 12 m sources within an ACA source, we combine the disk flux for all sources within the half-maximum contour of the ACA data to calculate the flux ratio."] [4.3. The Evolution of Envelope Flux: "The envelope flux can be  calculated from the ACA-12 mthe disk flux from the combined flux difference, i.e., subtractingdisk(s) and envelope flux."]
  - parameter: R = 0.5 threshold separating envelope-dominated (R < 0.5) from disk-dominated (R > 0.5) sources [4.2. The 12 m to ACA Flux Ratio: "We define R = 0.5 to be the transition from envelope to disk-dominated."]
  - assumption: 12 m flux traces the disk while ACA flux traces combined disk plus inner envelope [4.2. The 12 m to ACA Flux Ratio: "The high angular resolution 12 m data is dominated by emission from the disk, while the ACA data traces the combined emission from the disk and envelope within 8000 au."]
  - fitting: Linear fit to log median points of disk flux vs. envelope flux [4.4. The Evolution of the Disk Flux: "The black line shows a linear fit to the log median points."]
  - validation: Repeated K-S and A-D statistical tests excluding outliers with R > 1 to confirm conclusions are unchanged [4.2. The 12 m to ACA Flux Ratio: "To test for bias due to the small number of sources with ratio >1, in Table 6 we show the same statistical tests between SED classes excluding these sources."]
- step 5: Estimate envelope masses, mass infall rates, and fraction of stellar mass accreted as a function of R
  - method: Convert envelope flux (ACA - 12 m difference) to envelope mass M_ACA using Eq. (2), compute freefall time t_ff via Eq. (3), and estimate infall rate M_dot = M_env / t_ff. Fit a 4th-degree polynomial to log10(M_dot) vs. R and a power law to… [4.3. The Evolution of Envelope Flux: "We use the same equation as Tobin et al. (2020) to estimate envelope mass from the submillimeter envelope flux:"] [5.2. The Evolution of Envelope Infall: "A fourth-degree polynomial was fit to the log of the medians using scipy.optimize.curve_fit."]
  - software: scipy
  - parameter: R bin width = 0.0055 for median infall rate fit [5.2. The Evolution of Envelope Infall: "We also show the median estimated values plotted from R = 0 to 1 at increments of 0.0055 in R."]
  - assumption: Distance D = 400 pc, dust temperature T = 15 K, dust opacity = 2.57 cm^2 g^-1 at 700 μm scaled to 870 μm with beta = 1.8, dust-to-gas ratio = 0.01 [4.3. The Evolution of Envelope Flux: "We assume a distance of 400 pc and a temperature of 15 K."] [4.3. The Evolution of Envelope Flux: "We adopt a dust opacity of 2.57 cm2 g−1 at 700 μm, for a Mathis, Rumpl & Nordsieck (MRN; Mathis et al. 1977) distribution of dust grains with thin ice mantles at a density of 106 cm−3 from Ossenkopf & Henning (1994)."]
  - assumption: Spherically symmetric freefall with total mass M = 0.25 M_sun, outer envelope radius r_outer = 2500 au, constant star formation rate, and protostellar lifetime of 500,000 yr [4.3. The Evolution of Envelope Flux: "We adopt a total mass of 0.25 M e and an envelope radius of 2500 au."] [5.2. The Evolution of Envelope Infall: "where α = 1/SFR = 500,000 yr/N proto (i.e., dt/dN proto )."]
  - fitting: 4th-degree polynomial fit to log10(M_dot) medians and power-law fit to N_proto(<R) via scipy.optimize.curve_fit [5.2. The Evolution of Envelope Infall: "A fourth-degree polynomial was fit to the log of the medians using scipy.optimize.curve_fit."] [5.2. The Evolution of Envelope Infall: "We fit a power law to the curve (middle left, Figure 16)."]
  - validation: Compared simple isothermal 870 μm ACA envelope mass estimates with full radiative transfer SED model envelope masses from Furlan et al. (2016) using Spearman rank correlation (r = 0.66, p = 1.73e-29). [Appendix A Comparison to Single-dish Fl…: "In the right panel of Figure 20 we compare their mass with our envelope mass estimated from the 870 μm ACA flux."] [Appendix A Comparison to Single-dish Fl…: "These results indicate that our simple estimate of envelope masses from dust emission assuming an opacity and a constant temperature of 15 K is consistent with model envelope masses created using full radiative transfer modeling."]
- result: ACA 870 μm 5-sigma detection rate (total sample) = 82 (247/300) ± not stated % [3.1. Detection Rates: "A total of 247 sources out of 300 (82%) are detected by the ACA at the 5σ level, where the peak flux in the central region is greater than five times the mean I ν rms level for the image."]
- result: ACA 870 μm 5-sigma detection rate for Class 0 protostars = 90 (80/89) ± not stated % [3.1. Detection Rates: "Using the SED classes from Furlan et al. (2016), we detected 80/89 Class 0 protostars (90%), 94/114 Class I protostars (83%), 67/89 FS protostars (75%), and 6/8 Class II objects (75%)."]
- result: ACA 870 μm 5-sigma detection rate for Class I protostars = 83 (94/114) ± not stated % [3.1. Detection Rates: "Using the SED classes from Furlan et al. (2016), we detected 80/89 Class 0 protostars (90%), 94/114 Class I protostars (83%), 67/89 FS protostars (75%), and 6/8 Class II objects (75%)."]
- result: ACA 870 μm 5-sigma detection rate for Flat Spectrum protostars = 75 (67/89) ± not stated % [3.1. Detection Rates: "Using the SED classes from Furlan et al. (2016), we detected 80/89 Class 0 protostars (90%), 94/114 Class I protostars (83%), 67/89 FS protostars (75%), and 6/8 Class II objects (75%)."]
- result: Fraction of unresolved ACA sources = 36 (108/300) ± not stated % [3.2. Observed Morphologies: "A total of 108/300 (36%) sources are unresolved; this is the most common morphology."]
- result: Fraction of compact ACA sources = 24.3 (73/300) ± not stated % [3.2. Observed Morphologies: "In comparison, a total of 73/300 (24.3%) of the sources have compact morphologies."]
- result: Fraction of extended ACA sources = 21 (63/300) ± not stated % [3.2. Observed Morphologies: "Extended sources make up 63/300 (21%) of the sample."]
- result: Fraction of multiple morphology ACA sources = 5.3 (16/300) ± not stated % [3.2. Observed Morphologies: "Only 5.3% (16 objects) of the entire sample show a multiple morphology."]
- result: Fraction of offset morphology ACA sources = 13.3 (40/300) ± not stated % [3.2. Observed Morphologies: "A total of 40/300 (13.3%) of our sources exhibit an offset morphology."]
- result: Median 12 m/ACA flux ratio for Class 0 protostars = 0.25 ± not stated dimensionless [4.2. The 12 m to ACA Flux Ratio: "The flux ratio distribution for Class 0 has a median of 0.25, demonstrating that they are indeed deeply embedded sources with their envelopes dominating the submillimeter flux."]
- result: Fraction of envelope-dominated protostars (R < 0.5) in total sample = 60 (180/300) ± not stated % [6. Conclusions: "In total, 60% (180/300) of the protostars are envelope-dominated, with flux ratios less than 0.5, while the remainder are disk-dominated."]
- result: Fraction of Class 0 protostars that are envelope-dominated (R < 0.5) = 81 (72/89) ± not stated % [4.2. The 12 m to ACA Flux Ratio: "In summary, we find that Class 0 protostars are envelope-dominated, with 72/89 (81%) having R < 0.5."]
- result: Fraction of Flat Spectrum protostars that are disk-dominated (R > 0.5) = 61 (54/89) ± not stated % [4.2. The 12 m to ACA Flux Ratio: "In contrast, FS protostars are disk-dominated, with 54/89 (61%) having R > 0.5; however, that means 39% of FS protostars appear to be envelope-dominated."]
- result: Power-law slope of log(disk flux) vs. log(envelope flux) = 0.68 ± not stated dimensionless [4.4. The Evolution of the Disk Flux: "We find that disk flux increases with increasing flux difference, with the log of the disk flux scaling as 0.68 times the log of the envelope flux."]
- result: Spearman rank correlation between disk flux and envelope flux = 0.58 ± p-value = 1.8e-13 dimensionless [4.4. The Evolution of the Disk Flux: "The test returned a correlation rank of 0.58 on a scale from −1 to 1 and a p-value of 1.8 × 10−13, indicating that there is indeed a correlation between the variables."]
- result: Fraction of stellar mass accreted during the envelope-dominated phase = 80 ± not stated % [abstract: "We estimate that 80% of the mass is accreted during the envelope-dominated phase."]
- result: Kendall's Tau correlation between 12 m/ACA flux ratio R and T_bol = 0.33 ± p-value = 1.9e-13 dimensionless [5.4. Flux Ratio as an Evolutionary Diag…: "For the ratio R versus T bol, the test returns τ = 0.33 with a p-value of 1.9 × 10−13 ."]
- result: Kendall's Tau correlation between envelope flux and T_bol = -0.48 ± p-value = 2.5e-26 dimensionless [5.4. Flux Ratio as an Evolutionary Diag…: "For the envelope flux versus T bol, the test returns τ = −0.48 with a p-value of 2.5 × 10−26 ."]
- limitation (authors): 30 of the 330 HOPS sources were excluded because they were very faint or noisy in the ACA data and presented imaging challenges. [3. The 300: ACA Sample Characteristics …: "The remaining 30 sources out of the 330 from HOPS were very faint or noisy in the ACA data, presenting challenges for imaging, and were excluded from the present work."]
- limitation (authors): Envelope mass and infall rate estimates assume a constant representative total mass (0.25 M_sun), isothermal 15 K dust, uniform opacity, and only count material within 2500 au, ignoring infalling gas outside 2500 au, outflow mass loss, and… [4.3. The Evolution of Envelope Flux: "It should further be noted that there is likely infalling material outside the 2500 au radius."]
- limitation (authors): The 12 m/ACA flux ratio can be affected by variations in initial core conditions, angular momentum, magnetic fields, multiplicity, dust temperature/opacity dependencies on luminosity, and short-timescale luminosity/accretion outbursts betw… [5.4.1. Class 0 Protostars: "For these sources, the high 12 m to ACA ratio is due to the compact nature of their envelopes, as opposed to having less-massive envelopes."]
- not stated (card): tclean stopping threshold, niter, deconvolver type, and automasking parameters; Whether primary beam correction was applied before aperture photometry on the 7-pointing mosaics; Exact coordinates of the three off-source 6" apertures used for I_nu rms calculation for each target; Radius of the ring around the image center used to place the sixteen 6" apertures for F_nu rms calculation; Which speci…

### 2019Natur.569..519K: Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback (2019; nearby_galaxies, star_formation, milky_way_ism; observational_alma_primary)
- question: Why does the gas depletion time exceed the GMC dynamical time by two orders of magnitude: slow, efficient star formation over many dynamical times, or fast, inefficient star formation with rapid GMC dispersal?
- processing.imaging.array_combination: 12-m + 7-m with empirical noise-based weighting; total power combined in Fourier space [Methods: "We combine the 12-m and 7-m array data using an empirical noise-based weighting"] [Methods: "We combine the interferometric and total power data cubes in Fourier space"]
- step 1: Image CO(1-0) and Halpha maps
  - method: Combine 12-m, 7-m and total power CO data; reduce Halpha WFI data; correct Halpha for [NII] contamination and extinction [Methods: "We remove the contribution of from our H$\alpha$ map scaling it by $5/6$."]
  - software: CASA
  - parameter: A_Halpha = 0.5 mag extinction correction [Methods: "We further correct for internal extinction of H$\alpha$ by $A_{\rm H\alpha}=0.5$ mag"]
  - assumption: alpha_CO = 4.35 (Z/Zsun)^-1 Msun/(K km/s pc^2), 50% uncertainty [Methods: "Throughout the analysis, we adopt an uncertainty on $\alpha_{\rm CO}$ of 50%."]
  - validation: Extinction checked with MUSE Balmer decrement; 24 um compared to check embedded SF [Methods: "resulting in $A_{\rm H\alpha}=0.37\pm0.24$ mag (median $\pm$ standard deviation)"]
- result: Total SFR from Halpha = 0.092 ± not stated Msun/yr [Methods: "we measure a total SFR of $0.092~{\rm M}_\odot~{\rm yr}^{-1}$ in NGC300"]
- result: CO 5-sigma point-source sensitivity = 5600 ± not stated Msun [Methods: "point source sensitivity of $5600~{\rm M}_\odot$ when integrated over $10~{\rm km~s}^{-1}$"]
- limitation (authors): Extinction correction might underestimate attenuation toward GMC density peaks [Methods: "It might underestimate the attenuation towards the GMC density peaks, where the surface density is $>20~{\rm M}_\odot~{\rm pc}^{-2}$."]
- limitation (authors): eps_sf and eta_fb depend on CO-to-H2 and Halpha-to-SFR conversion factors [Methods: "Due to their dependence on $t_{\rm dep}$, the quantities $\epsilon_{\rm sf}$ and $\eta_{\rm fb}$ are sensitive to absolute scaling factors"]
- not stated (card): Which ALMA execution blocks/MOUS were used and the pipeline version used; CASA clean parameters: cell size, image size, masking, niter; Details of the modified total power pipeline and how feathering was done; Image-cube moment/masking used to make the CO map fed to Heisenberg; Heisenberg code is not public (available on request); Exact reference parameters in Kruijssen 2018 Tables 1-2 not reprod…

### 2023ApJ...953..164M: ACA CO(J = 2-1) Mapping of the Nearest Spiral Galaxy M33. I. Initial Results and Identification of Molecular Clouds (2023; nearby_galaxies, star_formation; observational_alma_primary)
- question: To obtain the spatial distribution in CO(J=2-1) emission with higher sensitivity and angular resolution in M33, and to identify and investigate low-mass (< 10^5 M_sun) and high-mass (>= 10^5 M_sun) molecular clouds to understand hierarchic…
- processing.imaging.array_combination: Combined ACA 7 m-array 12CO(J=2-1) data with IRAM 30 m data using feather task [Observations and Data Reduction: "To compensate for such diffuse components, we combined the ACA 7 m-array $^{12}$CO($J=2-1$) data with the IRAM 30 m data using the `feather` task."]
- step 1: Calibrate, concatenate, image ACA visibilities, and feather with IRAM 30 m data
  - method: Apply standard ALMA calibration, concatenate visibilities from 36 science goals across projects, image with tclean using multi-scale deconvolver, natural weighting, and auto-multithresh down to ~1 sigma, then combine 12CO(J=2-1) ACA data w… [Observations and Data Reduction: "Prior to the imaging process, we concatenated all visibilities obtained in each science goal with a total number of 36."] [Observations and Data Reduction: "We used the `tclean` task with `multi-scale` deconvolver (cite: kepley2020) to recover extended emission as much as possible. In `tclean` task, we applied the natural weighting and used the `auto-multithresh` procedure to identify automatically regions containing emission in the dirty and residual images."]
  - software: CASA, tclean, feather
  - parameter: natural weighting [Observations and Data Reduction: "In `tclean` task, we applied the natural weighting and used the `auto-multithresh` procedure to identify automatically regions containing emission in the dirty and residual images."]
  - parameter: threshold ~ 1 sigma noise level [Observations and Data Reduction: "We continued the deconvolution process until the intensity of the residual image attains the $\sim$1 $\sigma$ noise level."]
  - validation: Compared global 12CO(J=2-1) luminosity between ACA, IRAM 30 m, and ACA+IRAM data over the observed region; checked C18O upper limit against convolved archival 12 m data (2017.1.00461.S) in NGC 604. [Observations and Data Reduction: "To evaluate the missing flux of the ACA observations, we measured the global $^{12}$CO($J=2-1$) luminosities over the M33 disk obtained by the ACA 7 m antennas and by the IRAM 30 m telescope (cite: druard2014)."] [CO Maps: "To check the validity of the upper limit, we retrieved the ALMA archival data (project code 2017.1.00461.S) and examined the C$^{18}$O($J=2-1$) emission in a GMC associated with NGC 604."]
- step 3: Decompose molecular clouds and measure basic cloud properties
  - method: Convolve ACA+IRAM 12CO(J=2-1) cube to 7.5'' circular beam, mask emission using cprops_mask, identify local maxima and assign emission via watershed algorithm in PYCPROPS, deconvolve beam and channel width to obtain intrinsic radius R and v… [Cloud Decomposition: "Firstly, we convolved the ACA+IRAM $^{12}$CO($J=2-1$) cube data to 7.5$''$ in order to identify molecular clouds by a circular beam. Then, we made masked cube data using `cprops_mask` provided by (cite: rosolowsky2021)."] [Cloud Decomposition: "To do this, we use a watershed algorithm, which associates all the cube pixels in the emission-masked data with a local maximum."]
  - software: PYCPROPS, cprops_mask
  - parameter: Convolved circular beam = 7.5'' (30 pc) [Cloud Decomposition: "Firstly, we convolved the ACA+IRAM $^{12}$CO($J=2-1$) cube data to 7.5$''$ in order to identify molecular clouds by a circular beam."]
  - parameter: High significance mask > 4 sigma in 3 continuous velocity channels; low significance mask > 3 sigma in 3 continuous velocity channels over 7.5'' beam [Cloud Decomposition: "The criteria of the emission mask are that high significance emission is required to be more than 4 $\sigma$ in continuous three velocity channels and low significance emission which is adjacent to high significance emission is required to be more than 3 $\sigma$ in continuous three velocity channels at least over the…"]
  - parameter: Local maxima merge threshold: T_max - T_merge >= 2 sigma; minimum spatial separation = 7.5''; minimum spectral separation = 7 km/s [Cloud Decomposition: "The neighbor is rejected if $T_{\rm max} - T_{\rm merge}$ is less than 2 $\sigma$, which means that such a local maximum is likely a noise fluctuation."] [Cloud Decomposition: "We adopted the beam size (7.5$''$) as a minimum spatial separation and also adopted 7 km s$^{-1}$ as a minimum spectral separation,"]
  - parameter: Radius conversion coefficient = 1.91; channel width Delta V_chan = 0.7 km/s [Cloud Decomposition: "The coefficient 1.91 converts the rms size to the effective spherical radius of the cloud (cite: solomon1987; rosolowsky2006)."] [Cloud Decomposition: "where $\sigma_{v, {\rm chan}}$ is the velocity resolution element, which is related to the velocity channel width ($\Delta V_{\rm chan}$ = 0.7 km s$^{-1}$) as $\sigma_{v, {\rm chan}} = \Delta V_{\rm chan}/(2 \sqrt{2\,{\rm ln}\,2})$."]
  - assumption: Distance D = 840 kpc (1'' = 4 pc) [Cloud Decomposition: "Here, $\sigma_{\rm beam}$ is calculated as $7.5\ensuremath{''} \times 4$ = 30, where the factor of 4 is the spatial size in parsec of 1$\ensuremath{''}$ at the distance of M33 (840 kpc)."]
  - fitting: Bootstrapping with 10,000 trials per cloud, using median absolute deviation scaled by square root of oversampling rate for uncertainties. [Catalog Description: "We repeated the resampling and remeasuring 10,000 times for each cloud, and evaluated the uncertainties. The final uncertainty in each property is the median absolute deviation of the bootstrapped values scaled up by the square root of the over-sampling rate, which corresponds to the number of pixels per beam size."]
  - validation: Tuned low significance mask threshold from default 2 sigma to 3 sigma to reject fake emission at cloud edges; compared extrapolated to observed values; separated low-S/N (<10) and high-S/N (>=10) clouds in subsequent analyses. [Cloud Decomposition: "In particular, the low significance mask does not reject fake emission (i.e., noise) at the cloud edge. Thus, we carefully tuned the rms thresholds, and finally we adopted 3 $\sigma$ for low significance masks."] [Catalog Description: "Since our catalog includes 147 molecular clouds whose S/N ratio is lower than 10, we examine the properties of such low-S/N clouds in the following analyses."]
- step 6: Analyze scaling relations, cumulative mass functions, and velocity dispersion decomposition against IRAM GMCs
  - method: Compute size-linewidth coefficient sigma_v R^-0.5; fit truncated power-law functions to cumulative mass distributions above completeness limits for ACA+IRAM clouds and 362 IRAM GMCs within ACA FOV; for 77 IRAM GMCs resolved into >=3 ACA+IR… [Size–Line-width Relation: "This trend can be evaluated more quantitatively by deriving the coefficient of the $R-\sigma_v$ relation, $\sigma_v R^{0.5}$."] [Mass Function: "Figure 12 shows the cumulative cloud mass functions fitted by the truncated power-law functions."]
  - parameter: Completeness limits: 5 x 10^4 M_sun (ACA+IRAM catalog) and 8.4 x 10^4 M_sun (Corbelli et al. 2017 catalog) [Mass Function: "If we apply such a linear scaling between the two masses to our molecular cloud catalog, the completeness limit is estimated to be $5 \times 10^4\,M_{\odot}$ because the lowest mass cloud is $7 \times 10^3\,M_{\odot}$ (see subsection 4.1)."] [Mass Function: "Note that we recalculated the GMC masses in the (cite: corbelli2017) catalog by assuming $R_{21} = 0.6$ and adopted $8.4 \times 10^4\,M_{\odot}$ as the completeness limit."]
  - assumption: R_21 = 0.6 applied to recalculate Corbelli et al. (2017) GMC masses [Mass Function: "Note that we recalculated the GMC masses in the (cite: corbelli2017) catalog by assuming $R_{21} = 0.6$ and adopted $8.4 \times 10^4\,M_{\odot}$ as the completeness limit."]
  - fitting: Truncated power-law fit to cumulative mass distribution treating N_0 as an independent free parameter; Spearman's rank correlation coefficient r_s for velocity dispersion comparisons. [Mass Function: "Note that we treated $N_0$ as a free parameter (i.e., independent of $\gamma$) in this study to achieve the best fitting."] [Origin of Velocity Dispersion in IRAM G…: "A clear correlation between $v_{\rm diff}$ and the velocity dispersion of the IRAM GMC, with the Spearman’s rank correlation coefficient $r_{\rm s}$ of 0.59, can be seen,"]
  - validation: Compared derived R - sigma_v coefficients and mass function slopes with earlier M33 catalogs (Rosolowsky et al. 2007; Corbelli et al. 2017; Braine et al. 2018). [Size–Line-width Relation: "To explain the origin of such a smaller velocity dispersion, we examine the $R-\sigma_v$ relations based on the two earlier GMC catalogs in M33 (cite: rosolowsky2007; corbelli2017)."] [Mass Function: "Considering that (cite: braine2018) obtained $\gamma = -1.65$ for all 566 GMCs in the (cite: corbelli2017) catalog, the cloud population of the ACA+IRAM cloud catalog is similar to that of the (cite: corbelli2017) catalog."]
- step 7: Evaluate association between molecular clouds and Spitzer/IRAC 8 um emission
  - method: Regrid IRAC 8 um map to match ACA+IRAM 12CO(J=2-1) map, average pixel values within each cloud, and construct cumulative distribution functions (CDFs) for 423 high-mass (>= 10^5 M_sun) and 425 low-mass (< 10^5 M_sun) clouds. [Properties of Molecular Clouds and High…: "To do this, we regridded the IRAC 8 $\mu$m map (cite: dale2009) to match the ACA+IRAM $^{12}$CO($J=2-1$) map and obtained mean $8\,\mu$m flux by averaging the pixel values included within each molecular cloud."] [Properties of Molecular Clouds and High…: "Then, we constructed the cumulative distribution functions (CDFs) both for 423 high-mass clouds and 425 low-mass clouds."]
  - software: HIIphot
  - parameter: Strong 8 um emission threshold > 2 MJy sr^-1; cloud mass threshold = 10^5 M_sun [Luminosities and Masses: "In the spiral arm region, many high-mass clouds are associated with the strong (typically $> 2$ MJy sr$^{-1}$) 8 $\mu$m emission, which likely traces high-mass star-forming regions (cite: calzetti2005; wu2005; calzetti2007; crocker2013)."] [Properties of Molecular Clouds and High…: "the strong ($> 2$ MJy sr$^{-1}$) $8\,\mu$m emission is found in 72% of high-mass clouds, but only in 36% of low-mass clouds, respectively."]
  - assumption: 8 um emission traces high-mass star-forming regions [Luminosities and Masses: "In the spiral arm region, many high-mass clouds are associated with the strong (typically $> 2$ MJy sr$^{-1}$) 8 $\mu$m emission, which likely traces high-mass star-forming regions (cite: calzetti2005; wu2005; calzetti2007; crocker2013)."]
  - validation: Subtracted diffuse 8 um emission using HIIphot and confirmed the CDF trend does not change. [Diffuse Emission Subtraction for IRAC 8…: "To extract the compact 8 $\mu$m emission which directly reflects the star formation from the diffuse components, we applied $HIIphot$, an IDL software developed by (cite: thilker2000)."] [Diffuse Emission Subtraction for IRAC 8…: "The general trend found in Figure 15 does not change; the $8\,\mu$m-bright sources are closely associated with high-mass clouds rather than low-mass clouds."]
- result: Global 12CO(J=2-1) luminosity with stand-alone ACA 7 m antennas = 7.6e6 ± not stated K km s^-1 pc^2 [Observations and Data Reduction: "We found the global $^{12}$CO($J=2-1$) luminosity with ACA 7 m antennas $L_{\rm CO}^{\rm ACA} = 7.6 \times 10^6$ K km s$^{-1}$ pc$^2$ over the observed region, and that with the IRAM 30 m telescope $L_{\rm CO}^{\rm IRAM} = 2.1 \times 10^7$ K km s$^{-1}$ pc$^2$ for the same area."]
- result: Global missing flux of 12CO(J=2-1) emission in stand-alone ACA observations = 60-70 ± not stated % [Observations and Data Reduction: "This indicates the global missing flux of $^{12}$CO($J=2-1$) emission of $60-70$%, which mainly corresponds to diffuse components of molecular gas."]
- result: C18O(J=2-1) 3 sigma upper limit in ACA map = 66 ± not stated mK [CO Maps: "The rms noise level of 22 mK yields a 3 $\sigma$ upper limit of 66 mK."]
- result: Total number of molecular clouds cataloged in M33 = 848 ± not stated dimensionless [Abstract: "Based on the ACA+IRAM $^{12}$CO($J=2-1$) cube data, we cataloged 848 molecular clouds with a mass range from $10^3$ $M_{\odot}$ to $10^6$ $M_{\odot}$."]
- result: Cloud radius R range and median = 6.8 to 72 (median 34) ± not stated pc [Basic Properties of Cataloged Molecular…: "$R$ ranges from 6.8 to 72 pc, and $\sigma_v$ ranges from 1.0 to 6.1 km s$^{-1}$. Their medians are 34 pc and 2.8 km s$^{-1}$, respectively."]
- result: Cloud velocity dispersion sigma_v range and median = 1.0 to 6.1 (median 2.8) ± not stated km s^-1 [Basic Properties of Cataloged Molecular…: "$R$ ranges from 6.8 to 72 pc, and $\sigma_v$ ranges from 1.0 to 6.1 km s$^{-1}$. Their medians are 34 pc and 2.8 km s$^{-1}$, respectively."]
- result: Average size-linewidth coefficient sigma_v R^-0.5 for 848 clouds = 0.48 ± 0.13 km s^-1 pc^-0.5 [Size–Line-width Relation: "The average $\sigma_v R^{0.5}$ for 848 clouds is $0.48 \pm 0.13$, which is significantly smaller than the Galactic $\sigma_v R^{0.5}$, 0.72."]
- result: Cumulative mass distribution slope gamma for ACA+IRAM cloud catalog = -1.60 ± not stated dimensionless [Mass Function: "We obtained $\gamma = -1.60$ for the ACA+IRAM cloud catalog and $\gamma = -1.48$ for the (cite: corbelli2017) catalog, respectively."]
- result: Spearman's rank correlation coefficient r_s between IRAM GMC velocity dispersion and inter-cloud velocity difference v_… = 0.59 ± not stated dimensionless [Origin of Velocity Dispersion in IRAM G…: "A clear correlation between $v_{\rm diff}$ and the velocity dispersion of the IRAM GMC, with the Spearman’s rank correlation coefficient $r_{\rm s}$ of 0.59, can be seen, while $\sigma_{v, {\rm mean}}$ seems nearly constant (2 – 4 km s$^{-1}$) and its correlation with the velocity dispersion of the IRAM GMC is weak ($…"]
- result: Fraction of high-mass (>= 10^5 M_sun) clouds with strong (> 2 MJy sr^-1) 8 um emission = 72 ± not stated % [Properties of Molecular Clouds and High…: "the strong ($> 2$ MJy sr$^{-1}$) $8\,\mu$m emission is found in 72% of high-mass clouds, but only in 36% of low-mass clouds, respectively."]
- result: Fraction of low-mass (< 10^5 M_sun) clouds with strong (> 2 MJy sr^-1) 8 um emission = 36 ± not stated % [Properties of Molecular Clouds and High…: "the strong ($> 2$ MJy sr$^{-1}$) $8\,\mu$m emission is found in 72% of high-mass clouds, but only in 36% of low-mass clouds, respectively."]
- limitation (authors): Beam smearing at 30 pc resolution makes compact C18O(J=2-1) emission undetectable in the ACA map. [CO Maps: "Thus, we consider that the beam smearing effect makes C$^{18}$O($J=2-1$) emission undetectable in the ACA 30 pc-resolution map."]
- limitation (authors): Small clouds with minor axis dispersion smaller than the beam (sigma_min < sigma_beam) have undefined deconvolved radii and are excluded, as are clouds at the edge of the ACA FOV where primary beam correction causes larger uncertainties. [Cloud Decomposition: "Note that if $\sigma_{\rm min}$ is smaller than $\sigma_{\rm beam}$, the resultant $R$ is not properly defined. We do not consider such small clouds further in this paper."]
- limitation (authors): Assuming a constant R_21 = 0.60 across the M33 disk introduces an error of about 30% in M_CO because R_21 varies spatially from 0.4 to 0.8. [Luminosities and Masses: "Note that, as pointed out by (cite: yajima2021), $R_{21}$ varies within an individual galaxy; in fact, $R_{21}$ in M33 varies from position to position, typically ranging from 0.4 to 0.8. Therefore we consider that the assumption of a constant $R_{2-1/1-0}$ over the M33 disk yields an error of about 30%."]
- not stated (card): Exact multi-scale scales used in CASA tclean; Cell size (pixel scale) and image dimensions (in pixels) used in tclean; Auto-multithresh sub-parameters in tclean (sidelobethreshold, noisethreshold, lownoisethreshold, minbeamfrac); Whether continuum subtraction (e.g., uvcontsub) was performed prior to line imaging; Exact definition of the ACA FOV boundary used to reject edge clouds; Specific parame…

### 2024MNRAS.530..597B: Cloud-scale molecular gas properties of the ANTENNAE merger: a comparative study with PHANGS-ALMA galaxies and NGC 3256 (2024; nearby_galaxies, star_formation; observational_alma_primary)
- question: How do the cloud-scale molecular gas properties of the Antennae merger (NGC 4038/9) compare to those in nearby spiral galaxies from PHANGS-ALMA and the late-stage merger NGC 3256, and how do they depend on merger stage?
- processing.imaging.array_combination: Two 12 m-array configurations and 7 m ACA imaged and cleaned together; combined with TP cubes using CASA feather task [2.2 Calibration and imaging: "The observations from the two 12 m-array configurations and the ACA were all imaged and cleaned together."] [2.2 Calibration and imaging: "Using the feather task in casa, the TP cubes were combined with both main array configurations plus the ACA."]
- step 1: Calibrate and image interferometric and Total Power CO (2-1) data and combine across spatial scales
  - method: Reapply ALMA observatory pipeline calibration to 12 m and 7 m data, subtract continuum, jointly image and clean both 12 m configurations and 7 m ACA using modified PHANGS-ALMA pipeline (multi-scale then single-scale tclean), calibrate/imag… [2.2 Calibration and imaging: "The observations from the two 12 m-array configurations and the ACA were all imaged and cleaned together."] [2.2 Calibration and imaging: "Using the feather task in casa, the TP cubes were combined with both main array configurations plus the ACA."]
  - software: CASA, PHANGS-ALMA imaging pipeline, PHANGS-ALMA TP calibration and imaging pipeline
  - parameter: Multi-scale clean scales: point sources, 0.5, 1, 2.5, 5, and 10 arcsec [2.2 Calibration and imaging: "These modifications include implementation of different angular sizes of the model components during multi-scale cleaning, for which we use point sources, 0.5, 1, 2.5, 5, and 10 arcsec."]
  - parameter: Circular synthesized beam FWHMs: 55, 80, 90, 120, and 150 pc [2.2 Calibration and imaging: "Several versions of the interferometric cube were made when the synthesized beam was made circular, with FWHM physical sizes of 55, 80, 90, 120, and 150 pc."]
  - parameter: TP continuum subtraction: order-one polynomial (linear) [2.2 Calibration and imaging: "all continuum subtraction was carried out using order-one polynomial (linear) fits to the continuum levels."]
  - assumption: Distance to NGC 4038/9 = 22 Mpc [1 INTRODUCTION: "At a distance of 22 Mpc (Schweizer et al. 2008), NGC 4038/9 is the nearest gas-rich major merger"]
  - fitting: Order-one polynomial (linear) fits for TP continuum subtraction [2.2 Calibration and imaging: "all continuum subtraction was carried out using order-one polynomial (linear) fits to the continuum levels."]
  - validation: Visual inspection of observatory weblog diagnostic plots for calibration issues and visual inspection of cleaned cubes for artefacts before feathering [2.2 Calibration and imaging: "We inspected the diagnostic plots in the observatory weblogs to search for problematic data that were not properly calibrated or left unflagged by the ALMA pipeline."] [2.2 Calibration and imaging: "Cleaned cubes were also visually inspected for artefacts related to calibration and cleaning errors before combining with the TP data."]
- result: Native synthesized beam size of 12CO (2-1) cube = 0.51 ± not stated arcsec [2.1 Observations: "The native beam size is 0.51′′ (55 pc) and the rms noise at this resolution is 0.24 K."]
- result: RMS noise at native 0.51 arcsec (55 pc) resolution = 0.24 ± not stated K [2.1 Observations: "The native beam size is 0.51′′ (55 pc) and the rms noise at this resolution is 0.24 K."]
- result: RMS noise of feathered 55 pc resolution cube = 0.25 ± not stated K [2.2 Calibration and imaging: "The cube with 55 pc resolution (0.51 arcsec) has an rms noise of approximately 0.25 K."]
- limitation (authors): Using a fixed 1 kpc radius to define central regions across PHANGS-ALMA galaxies means low stellar mass (smaller) galaxies have a larger fraction of contaminating disc pixels in their central 1 kpc, likely underestimating their central per… [4.1 Distribution of cloud-scale molecul…: "However, given the size-stellar mass relation of galaxies, the fraction of a galaxy included in the central region will increase as stellar mass decreases."]
- limitation (authors): Sensitivity limits truncate the detection of low surface density regions with large velocity dispersions, preventing determination of whether the velocity dispersion-surface density relation in mergers is broader at all surface densities o… [4.2 Correlations between velocity dispe…: "However, the sensitivity limit in this parameter space roughly follows the upper-left edge of the contours (see Figure 1 from Sun et al. 2020), so that we do not have enough sensitivity to detect low surface density regions with large velocity dispersions."]
- limitation (authors): Virial parameter estimates do not account for external pressure confinement (e.g., from stellar surface density or cloud-cloud collisions) that could help bind the gas. [5.1 Comparison of the two mergers: "We must also caution that the virial parameters shown in Figures 3 through 5 do not account for pressure confinement contributing to binding the observed molecular gas."]
- not stated (card): Exact tclean weighting parameter (robust value) used during imaging; Exact cell size and image dimensions (in pixels and arcsec) used in tclean prior to post-feathering regridding; Exact user-defined spectral line centre and width parameters used for automated continuum subtraction; Signal-to-noise thresholds and masking criteria used to generate moment maps and define significant pixels; Exact c…

### 2025A&A...693A.286S: Intermediate mass T Tauri disk masses and a comparison to their Herbig disk descendants (2025; protoplanetary_disks, exoplanets; archival_reuse)
- question: Do disks around intermediate mass T Tauri (IMTT) stars, the precursors of Herbig stars, differ from Herbig disks in dust mass, gas mass, gas-to-dust ratio and radii, and what does this imply for planet formation around intermediate mass st…
- step 1: Calibrate and self-calibrate the 12-m data
  - method: Phase self-calibration on continuum, rounds repeated until peak S/N stops improving, then applied to line spectral windows; single amplitude round only for SU Aur; no self-cal for ACA [Data selection and reduction: "The 12-m array data were phase self-calibrated based on the continuum data for multiple rounds up until the peak signal-to-noise did not improve compared to the previous round."] [Data selection and reduction: "The resulting calibration table was applied to the line spectral windows by using the `applycal` task."]
  - software: CASA
  - parameter: 1 to 3 rounds in most cases, solution interval starting at inf and decreasing by factors of two; S/N gain factor 1.7 on average; applied for 12 targets [Data selection and reduction: "In most cases one to three rounds were done"] [Data selection and reduction: "then decreasing by factors of two, which increases the signal-to-noise ratio by a factor of 1.7 on average"]
  - validation: Stop criterion is peak S/N no longer improving between rounds [Data selection and reduction: "up until the peak signal-to-noise did not improve compared to the previous round"]
- result: Self-calibration S/N improvement (average factor) = 1.7 ± not stated dimensionless [Data selection and reduction: "which increases the signal-to-noise ratio by a factor of 1.7 on average"]
- limitation (authors): Upper limits on IMTT CO fluxes do not constrain gas masses; most limits reach the grid maximum [Gas masses and radii: "the upper limits obtained for the IMTT disks are not"]
- limitation (authors): Resolved-structure fraction lower than Herbig, attributed to lower spatial resolution; lack of deep observations [Continuum images: "which is likely due to the lower spatial resolution of the data available in our work"]
- limitation (authors): Sample biased towards high accretors and brightest disks [Introduction: "the IMTT disks are likely biased towards the high accretors and brightest disks"]
- not stated (card): CASA version and whether archive pipeline products or manual calibration were used for the non-mosaic data; tclean parameters: robust/weighting, cell size, image size, niter, threshold, masks, uv taper, and the exact channel width per line; Line-free channels and fit order used in uvcontsub for each dataset; Self-calibration solution intervals actually used per target, spw combination, and S/N ac…

### 2026A&A...706A.174A: Hiding behind a curtain of dust: Gas and dust properties of an ultra-luminous strongly-lensed z = 3.75 galaxy behind the Milky Way disc (2026; high_z_galaxies; observational_alma_primary)
- question: Confirm the spectroscopic redshift of the strongly lensed submm galaxy J154506 behind the Milky Way (Lupus-I cloud) and make an initial characterisation of its dust and molecular gas properties
- step 1: Reduce and image the ACA Cycle 10 spectral scans
  - method: CASA pipeline calibration; interactive tclean with natural weighting; cubes with fixed elliptical mask, binned to about 100 km/s; no-continuum-subtracted cubes first, then continuum measured from line-free channels [3.2 ALMA Cycle 10 Atacama Compact Array…: "We created continuum images using the interactive TCLEAN task within CASA with natural weighting."] [3.2 ALMA Cycle 10 Atacama Compact Array…: "We subsequently measured the continuum and extracted it from line-free regions adjacent to detected emission lines."]
  - software: CASA, tclean
  - parameter: Cube mask 16″ x 10″ elliptical; velocity binning about 100 km/s [3.2 ALMA Cycle 10 Atacama Compact Array…: "Each spectral cube was imaged separately and cleaned using a fixed elliptical mask of"] [3.2 ALMA Cycle 10 Atacama Compact Array…: "During the data reduction steps, the cubes were further binned to velocity resolutions of"]
  - validation: Visual inspection to remove data with irregular amplitude or phase values [3.2 ALMA Cycle 10 Atacama Compact Array…: "including visual inspections to identify and remove data with irregular amplitude or phase values"]
- limitation (authors): Stellar mass and other SED-derived properties highly uncertain because of Lupus-I extinction [4 Spectroscopic redshift confirmation: "makes SED-derived properties, such as the stellar mass, highly uncertain."]
- limitation (authors): Lens redshift not confirmed; MUSE and FORS2 data too poor [3.5 MUSE and FORS2 observations: "The low quality of this dataset precluded spectroscopic confirmation of the lens and prevented further detailed analysis."]
- limitation (authors): Dust mass strongly depends on the assumed kappa and optical depth [6.1 Dust emission and FIR-derived prope…: "Dust mass estimates are highly dependent on the assumed"]
- not stated (card): Imaging parameters for ACA tclean (cell size, image size, deconvolver, threshold, niter) and the clean mask for continuum; Line-free channel ranges used for continuum estimation in the ACA cubes; Exact velocity range used to integrate each ACA line and how line fluxes and uncertainties were computed; Flux calibrator and flux-scale uncertainty for the ACA and archival data; Primary-beam correction…

### 2021A&A...655A..42S: Molecular gas budget and characterization of intermediate-mass star-forming galaxies at z ≈ 2-3 (2021; high_z_galaxies; observational_alma_primary)
- question: Constrain the molecular gas content (CO, [CI], dust) of four cluster-lensed, UV-selected intermediate-mass star-forming galaxies at z~2-3 with ACA and compare gas fraction and depletion time with high-z scaling relations
- step 1: calibrate and image ACA continuum and line data
  - method: CASA pipeline calibration, then tclean with natural weighting; Band 7 continuum as dirty MFS images followed by masked cleaning; Band 4 cubes at native 3.9 MHz channels [2.2 Atacama Compact Array data: "All subsequent imaging was done with CASA task `tclean` and using natural weights to maximize signal-to-noise ratio."] [2.2.1 The Sunburst Arc: "We then synthesized data-cubes keeping the native channel resolution (3.9 MHz)."]
  - software: CASA, tclean, uvcontsub
  - parameter: pixel size 1/5 of the beam minor axis [2.2 Atacama Compact Array data: "The resulting cubes and images are sampled at pixel size equal to 1/5 of beam minor axis"]
  - parameter: Sunburst B4 continuum: channels within 250 km/s of CO(4-3) and [CI] excluded [2.2.1 The Sunburst Arc: "We then repeated the imaging process excluding channels within 250 km s^−1^ to each side of the expected central frequency"]
  - assumption: flux calibration accuracy 10%; astrometry accurate to 0.6 arcsec [2.2 Atacama Compact Array data: "We assumed a flux calibration accuracy of 10% throughout."] [2.2 Atacama Compact Array data: "the astrometry is expected to be accurate to 0.6″"]
- step 3: fit line profiles and measure line fluxes and luminosities
  - method: 1D Gaussian fits to CO spectra; zeroth-moment maps integrated over +/-0.85 FWHM; 2D Gaussian imfit on moment maps; 3 sigma upper limits for non-detections [3.1 Emission lines in the SGASJ0033 sys…: "we fit one dimensional Gaussian profiles to the CO spectra of SGASJ0033-A and SGASJ0033-SMG using non linear least squares minimization"] [3.1 Emission lines in the SGASJ0033 sys…: "The resulting moment maps were then fit with a 2D Gaussian profile using CASA task `imfit`"]
  - software: CASA imfit
  - parameter: integration range -0.85 to +0.85 times best-fit Gaussian FWHM [3.1 Emission lines in the SGASJ0033 sys…: "we used symmetric integration ranges spanning from $-0.85$ to $+0.85$ times the best-fit Gaussian FWHM"]
  - parameter: upper limits: 3 sigma point source, fixed 200 km/s range at best available redshift [3.1 Emission lines in the SGASJ0033 sys…: "we report $3\sigma$ point source upper limits assuming a fixed integration range width of 200 km s^−1^ around the best spectroscopic redshift available"]
  - assumption: sources unresolved by the ACA Band 4 beam [3.1 Emission lines in the SGASJ0033 sys…: "The results of the fits are consistent with the sources being unresolved by the ACA Band 4 beam."]
  - fitting: Non-linear least squares Gaussian fits; single, double and triple Gaussians compared with corrected AIC and BIC [3.1 Emission lines in the SGASJ0033 sys…: "We fit single, double and triple Gaussian models, but only the single Gaussian achieved optimal corrected Akaike Information criterion (cite: Cavanaugh1997CorrectedAkaikeCriterion) and Bayesian Information criterion (cite: Wit2012StatsModelUncertainty) scores."]
  - validation: Integration range recovers ~99.5% of the flux while keeping S/N >~ 3 per channel; AICc/BIC favour single Gaussian (no broad component) [3.1 Emission lines in the SGASJ0033 sys…: "In this way we recover $\sim 99.5\%$ of the flux while keeping S/N$\gtrsim 3$ per channel."]
- step 7: fit SEDs for stellar mass and SFR
  - method: High-z MAGPHYS on HST, ACA submillimetre and IRAC photometry (when available), with CIGALE as a cross-check; results corrected by magnification [3.3 SED fitting: "We combined image plane optical HST photometry (four bands), ACA submillimeter continuum photometry (two bands) and IRAC near infrared photometry (two bands) when available"] [3.3 SED fitting: "we used the high-$z$ version of the Multi-wavelength Analysis of Galaxy Physical Properties package (cite: daCunha2015HighZMagphysALESS)"]
  - software: MAGPHYS (high-z), CIGALE
  - parameter: CIGALE test: same stellar templates and attenuation law as MAGPHYS, delayed exponential SFH, nebular emission, Dale 2014 dust templates with alpha_SF 0-4 and f_AGN = 0 [3.3 SED fitting: "we used the same stellar templates and attenuation law as MAGPHYS, but assumed a delayed exponential SFH and a nebular emission component"] [3.3 SED fitting: "Here we have chosen to fix $f_\text{AGN}=0$ and vary $\alpha_\text{SF}$ between 0 and 4."]
  - assumption: Bruzual and Charlot stellar emission, da Cunha 2008 dust emission, Charlot and Fall attenuation law, energy balance [3.3 SED fitting: "MAGPHYS uses precomputed grids of stellar emission (cite: Bruzual&Charlot2003SSP) and dust emission models (cite: daCunha2008MagphysPaper)"] [Introduction: "Star formation rates and stellar masses are derived assuming a (cite: Chabrier2003IMF) initial mass function (IMF)."]
  - fitting: MAGPHYS Bayesian fit returning posterior samples; medians and 68% intervals reported [3.3 SED fitting: "The results are given as samples of the posterior probability distribution of the parameters of the models."]
  - validation: CIGALE comparison and MAGPHYS re-runs without IRAC bands; offsets within the posterior uncertainties [3.3 SED fitting: "we also ran CIGALE (cite: Boquien2019CIGALEpaper), another SED fitting code, and then compare with our MAGPHYS results"] [2.3.2 Spitzer: "we ran MAGPHYS on SGASJ1226-A and SGASJ1226-B again but turning off the fitting for the IRAC bands"]
- result: CO(4-3) central frequency, SGASJ0033-A.1+A.2 = 136.004 ± 0.001 GHz [Table 2 (line fluxes): "$136.004 \pm 0.001$"]
- result: CO(4-3) redshift, SGASJ0033-A.1+A.2 = 2.3899 ± 0.000025 dimensionless [Table 2 (line fluxes): "2.3899 ± 0.000025"]
- result: CO(4-3) FWHM, SGASJ0033-A.1+A.2 = 85 ± 7 km/s [Table 2 (line fluxes): "$85 \pm 7$"]
- result: CO(4-3) integrated flux mu*Delta v*S_nu, A.1+A.2 (table prints the unit column as km/s; Jy prefix lost in the text) = 1.96 ± 0.15 Jy km/s (unit as printed is garbled) [Table 2 (line fluxes): "$1.96 \pm 0.15$"]
- result: CO(4-3) line luminosity mu*L'_line, A.1+A.2 = 3.30 ± 0.25 1e10 K km/s pc^2 [Table 2 (line fluxes): "$3.30 \pm 0.25$"]
- result: [CI](1-0) line luminosity mu*L'_line, A.1+A.2 = 0.53 ± 0.19 1e10 K km/s pc^2 [Table 2 (line fluxes): "$0.53 \pm 0.19$"]
- result: CO(4-3) line luminosity mu*L'_line, A.3 = 1.1 ± 0.4 1e10 K km/s pc^2 [Table 2 (line fluxes): "$1.1 \pm 0.4$"]
- result: CO(4-3) FWHM, SGASJ0033-SMG = 430 ± 87 km/s [Table 2 (line fluxes): "$430 \pm 87$"]
- result: CO(4-3) central frequency, SGASJ0033-SMG = 135.643 ± 0.017 GHz [Table 2 (line fluxes): "$135.643 \pm 0.017$"]
- result: CO(4-3) detection significance, SGASJ0033 arc = 10 ± not stated sigma [2.2.3 SGASJ0033: "Preliminary analysis revealed a $10\sigma$ detection of the CO line"]
- result: log M_stars, Sunburst Arc (magnification-corrected) = 9.44 ± +0.17/-0.11 log(M_sun) [SED results table: "$9.44_{-0.11}^{+0.17}$"]
- result: log M_stars, SGASJ1226-A = 9.38 ± +0.11/-0.11 log(M_sun) [SED results table: "$9.38_{-0.11}^{+0.11}$"]
- result: log M_stars, SGASJ1226-B = 9.73 ± +0.17/-0.16 log(M_sun) [SED results table: "$9.73_{-0.16}^{+0.17}$"]
- result: log M_stars, SGASJ0033-A = 10.10 ± +0.16/-0.17 log(M_sun) [SED results table: "$10.10_{-0.17}^{+0.16}$"]
- result: log SFR100, Sunburst Arc = 1.20 ± +0.07/-0.13 log(M_sun per yr) [SED results table: "$1.20_{-0.13}^{+0.07}$"]
- result: log SFR100, SGASJ1226-A = 0.65 ± +0.11/-0.05 log(M_sun per yr) [SED results table: "$0.65_{-0.05}^{+0.11}$"]
- result: log SFR100, SGASJ1226-B = 1.12 ± +0.21/-0.08 log(M_sun per yr) [SED results table: "$1.12_{-0.08}^{+0.21}$"]
- result: log SFR100, SGASJ0033-A = 1.12 ± +0.22/-0.19 log(M_sun per yr) [SED results table: "$1.12_{-0.19}^{+0.22}$"]
- result: CIGALE minus MAGPHYS offsets in SFR and M_stars = ~0.15 dex (SFR), ~0.3 dex (M_stars) ± not stated dex [3.3 SED fitting: "the former produces on average $\sim 0.15$ dex and $\sim 0.3$ dex higher estimates of SFR and $M_\text{stars}$ respectively than MAGPHYS"]
- limitation (authors): Cannot quantify the differential-lensing bias in magnification [4.2 The molecular gas deficit cannot be…: "Unfortunately, we cannot currently provide a quantitative estimation of the bias in the magnification."]
- limitation (authors): Lens-model uncertainties possibly dominated by systematics [2.3.3 Lens models and source plane reco…: "We note, however, that the uncertainties are possibly dominated by systematics"]
- limitation (authors): Small sample and large calibration dispersion at low metallicity make the hypothesis hard to falsify [4.3 Low metallicity as the driver of th…: "Given the large dispersion in tracer-to-gas calibrations in the subsolar metallicity regime and the small size of our sample, it remains difficult to falsify the hypothesis proposed above."]
- not stated (card): tclean niter, threshold, gridder, imsize and phase-centre settings for each image and cube; which channels were used for the Band 7 and Band 4 continuum and exact line-free ranges for each source; uvcontsub fit channel ranges for SGASJ0033; CASA pipeline version label per execution block and which archive MOUS or scheduling blocks were used; flux, bandpass and phase calibrators and the flux scale…

### 2023NatAs...7..684K: Azimuthal C/O variations in a planet-forming disk (2023; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: How does the gas-phase elemental C/O ratio vary azimuthally in the protoplanetary disk around HD 100546, and what explains the spatial and kinematic asymmetries in CS and SO emission?
- step 1: Calibrate, image, and extract spectra and upper limits from ACA Band 7 observations
  - method: Calibrate ACA visibilities with the ALMA pipeline, subtract continuum with uvcontsub, image with tCLEAN using natural weighting, generate moment 0 maps between -14.5 and 25.5 km s-1, extract spectra using 5.0" elliptical and Keplerian mask… [3.1 Data reduction: "Continuum and line imaging were performed with the tCLEAN algorithm using natural weighting in order to maximize the S/N ratio of the data."] [3.1 Data reduction: "The total disk-integrated flux was extracted using the CASA task specflux, and determined to be 0.62 Jy km s–1 for the Keplerian-masked cube, where the mask was cut at ± 4 km s–1 either side of the source velocity in order to remove noisy channels."]
  - software: CASA, ALMA Pipeline, tCLEAN, uvcontsub, specflux, Keplerian mask (Teague, 2020), VISIBLE / matched filter (Loomis et al., 2018)
  - parameter: cell size = 0.5", image region = 20"x20", velocity integration range = -14.5 to 25.5 km s-1, elliptical aperture radius = 5.0" [3.1 Data reduction: "We used a cell size of 0.5" to ensure that the beam is well sampled."] [3.1 Data reduction: "The CS 7-6 integrated intensity map (Figure 2, top right) was generated from a 20"x20" region centred on the source, where the integrated intensity is determined between -14.5 to 25.5 km s–1"]
  - assumption: V_LSRK = 5.7 km s-1; M_* = 2.4 M_sun for Keplerian mask [3.1 Data reduction: "The mask identifies which pixels in the image cubes have Doppler shifted line velocities that match the Keplerian velocity, based on the velocity profile of a disk rotating around a star of mass M ⋆ = 2.4 M ⊙ ."] [3.1 Data reduction: "corresponding to channels expected to contain significant emission ( ∼± 20 km s–1 from the source velocity V LSRK = 5.7 km s–1 )."]
  - validation: Compared elliptical and Keplerian masked spectra; used elliptically-masked spectrum to avoid removing real non-Keplerian/asymmetric emission. [3.1 Data reduction: "Due to the peculiar nature of the CS line profile, our analysis utilises only the elliptically-masked spectrum, in order to not mistakenly remove any real emission."]
- step 2: Measure and validate the spatial offset of CS 7-6 emission from the host star
  - method: Fit a Gaussian to the CS image and deproject using disk inclination and PA; compare CS peak position against ACA continuum and C18O 3-2 reference positions; calculate beam centroid uncertainty; fit a Gaussian directly to continuum-subtract… [1.1 Data & observational findings: "Fitting a Gaussian, we find the peak of the CS emission to be significantly offset from the host star by ∼ 1"."] [Supplementary Information 1: "Next, we assess the offset in the visibility plane, using the CASA task uvmodelfit to fit a model directly to the UV-data."]
  - software: CASA, uvmodelfit
  - parameter: uvmodelfit channels = ±10 km s-1 from source velocity, 20 iterations (converging after ∼8) [Supplementary Information 1: "We first split out the spectral windows containing the CS 7-6 emission from continuum-subtracted measurement set, using only the channels centered ± 10 km s–1 from the source velocity."] [Supplementary Information 1: "We run 20 iterations, with the model converging after ∼ 8."]
  - assumption: Continuum and C18O 3-2 emission peaks trace the central star location within the central 0.5" pixel [Supplementary Information 1: "It is therefore reasonable to utilise the continuum and C 18 O emission peaks as reference locations for the host star."]
  - fitting: Gaussian visibility-plane fitting with CASA uvmodelfit [Supplementary Information 1: "We then fit a Gaussian to the data, where the initial guess for shape is based on the synthesized beam properties, and the initial guess for the emission peak is the image centre (ie. location of the star)."]
  - validation: Repeated uvmodelfit with a range of initial peak location guesses (converging within ∼8%); checked archival high-resolution C2H data (2017.1.00845.S) which also shows redshifted enhancement. [Supplementary Information 1: "Since uvmodelfit can be sensitive to the initial conditions, we repeat the fitting using a range of initial guesses for the location of the emission peak. In all cases the models converge to close to the same result, deviating by a maximum of ∼ 8 % from the value reported here."] [Supplementary Information 1: "The total flux on the red-shifted side of the disk is a factor of ∼ 1.5 greater that that on the shifted side, which may be indicative of an elevated C/O ratio."]
- result: CS 7-6 integrated intensity peak flux = 0.90 ± 0.10 Jy beam-1 km s-1 [1.1 Data & observational findings: "CS is detected at 9 σ confidence (0.90 ± 0.10 Jy beam–1 km s–1 at emission peak, as measured from the integrated intensity map), using the Atacama Compact Array (ACA) in Cycle 4 (Figure 2, top right)."]
- result: CS 7-6 channel map peak flux density = 0.21 ± 0.024 Jy beam-1 [3.1 Data reduction: "Channel maps are presented in Supplementary Information 6, from which we measure a peak flux density of 0.21 Jy beam–1 and rms of 0.024 Jy beam–1 ."]
- result: CS 7-6 disk-integrated flux (elliptical mask) = 1.02 ± not stated Jy km s-1 [3.1 Data reduction: "The disk-integrated flux extracted from the elliptically masked cube was 1.02 Jy km s–1 ."]
- result: CS 7-6 disk-integrated flux (Keplerian mask) = 0.62 ± not stated Jy km s-1 [3.1 Data reduction: "The total disk-integrated flux was extracted using the CASA task specflux, and determined to be 0.62 Jy km s–1 for the Keplerian-masked cube, where the mask was cut at ± 4 km s–1 either side of the source velocity in order to remove noisy channels."]
- result: CS 7-6 disk-integrated flux (energy units) = 1.167e-20 ± not stated W m-2 [Table 3: "CS 7-6 1.167 × 10–20 This work"]
- result: CS 7-6 emission peak spatial offset (image plane) = 1 ± 0.27 arcsec [Supplementary Information 1: "We therefore find the CS 7-6 emission peak to be offset by ∼ 1 ± 0.27"."]
- result: CS 7-6 emission peak radial offset (deprojected) = 100 ± not stated au [1.1 Data & observational findings: "We determine the radial separation between the peak of the emission and the host star by exploiting the known inclination and position angle of the disk to deproject the image, finding the emission peak to be radially offset ∼ 100 au from the source."]
- result: CS 7-6 emission peak offset in visibility plane (total absolute) = 1.11 ± 0.33 arcsec [Supplementary Information 1: "The offset in the emission peak is found to be 0.88 ± 0.23" west and 0.68 ± 0.25" south, corresponding to a total absolute offset of 1.11 ± 0.33"."]
- result: CS 7-6 emission peak offset in visibility plane (west) = 0.88 ± 0.23 arcsec [Supplementary Information 1: "The offset in the emission peak is found to be 0.88 ± 0.23" west and 0.68 ± 0.25" south, corresponding to a total absolute offset of 1.11 ± 0.33"."]
- result: CS 7-6 emission peak offset in visibility plane (south) = 0.68 ± 0.25 arcsec [Supplementary Information 1: "The offset in the emission peak is found to be 0.88 ± 0.23" west and 0.68 ± 0.25" south, corresponding to a total absolute offset of 1.11 ± 0.33"."]
- result: C18O 3-2 integrated intensity peak flux = 7.2 ± 0.3 Jy beam-1 km s-1 [3.1 Data reduction: "The detection is made at a ∼ 24 σ confidence level, with a peak flux of 7.2 ± 0.3 Jy beam–1 km s–1, as measured from the integrated intensity map."]
- result: C18O 3-2 disk-integrated flux (Keplerian mask) = 5.41 ± not stated Jy km s-1 [3.1 Data reduction: "The disk integrated flux is measured using the procedure outlined above, determined to be 5.41 Jy km s–1 using a Keplerian mask, and 8.22 Jy km s–1 using an elliptical mask."]
- result: C18O 3-2 disk-integrated flux (elliptical mask) = 8.22 ± not stated Jy km s-1 [3.1 Data reduction: "The disk integrated flux is measured using the procedure outlined above, determined to be 5.41 Jy km s–1 using a Keplerian mask, and 8.22 Jy km s–1 using an elliptical mask."]
- result: C18O 3-2 disk-integrated flux (energy units) = 9.03e-20 ± not stated W m-2 [Table 3: "C 18 O 3-2 9.03 × 10–20 This work"]
- result: SO 2_1-1_0 3sigma upper limit = < 0.66 ± not stated Jy km s-1 [Table 2: "SO 2 1 - 1 0 329.385 0.250 15.8 1.423 × 10–5 4.83 ” × 4.08 ” 0.14 < 0.66"]
- result: SO2 4_3,1-3_2,2 3sigma upper limit = < 0.48 ± not stated Jy km s-1 [Table 2: "SO 2 4 3,1 - 3 2,2 332.505 0.250 31.3 3.290 × 10–4 4.84 ” × 4.07 ” 0.10 < 0.48"]
- result: C36S 7-6 3sigma upper limit = < 0.46 ± not stated Jy km s-1 [Table 2: "C 36 S 7 – 6 332.510 0.250 63.9 6.951 × 10–4 4.78 ” × 4.07 ” 0.10 < 0.46"]
- result: HCS+ 8-7 3sigma upper limit = < 0.71 ± not stated Jy km s-1 [Table 2: "HCS + 8 – 7 341.339 0.250 73.7 8.352 × 10–4 4.62 ” × 4.03 ” 0.14 < 0.71"]
- result: H2CS 10_0,10-9_0,9 3sigma upper limit = < 1.50 ± not stated Jy km s-1 [Table 2: "H 2 CS 10 0,10 - 9 0,9 342.946 0.250 90.6 6.080 × 10–4 4.73 ” × 3.90 ” 0.31 < 1.50"]
- result: 34SO 2_3-2_1 3sigma upper limit = < 1.60 ± not stated Jy km s-1 [Table 2: "34 SO 2 3 - 2 1 343.851 0.250 20.9 1.382 × 10–7 4.63 ” × 3.89 ” 0.31 < 1.60"]
- result: SO 8_8-7_7 3sigma upper limit = < 1.50 ± not stated Jy km s-1 [Table 2: "SO 8 8 - 7 7 344.310 0.250 87.5 5.188 × 10–4 4.62 ” × 3.89 ” 0.30 < 1.50"]
- limitation (authors): The ACA CS 7-6 observation is essentially unresolved because the 4.78" beam is nearly equal to the radial extent of the gas disk. [1.1 Data & observational findings: "The emission is essentially unresolved, since the beam size (4.78") is almost equal to the radial extent of the gas disk, as traced by CO (Walsh et al., 2017)."]
- limitation (authors): The DALI model lacks a smooth transition between the inner cavity and dust ring (having a sharp boundary instead) and does not include the outer dust gap between r ∼ 40 - 150 au in ∆_g/d. [1.2 Modelling: "One possible explanation is that our model lacks a smooth transition between the cavity and dust ring, instead having a sharp boundary."]
- limitation (authors): Wedge splicing angles are measured in the image cube plane rather than projected onto the inclined 3D disk plane. [3.3.5 Modelling azimuthal asymmetries: "Angles are measured in the plane of the cube i.e. they are not projected on to the disk, and as such do not directly correlate to angles measured in the disk plane."]
- not stated (card): Exact disk inclination and position angle values adopted for image deprojection, Keplerian masking, and DALI raytracing; Specific line-free channel ranges used in uvcontsub for each ACA spectral window; tCLEAN stopping threshold and masking strategy during deconvolution of the ACA cubes; Exact CASA simobserve and simanalyze configuration files and noise/thermal parameters used to simulate the obs…

### 2016ApJ...832...37G: ALMA Observations of Lyα Blob 1: Halo Substructure Illuminated from Within (2016; high_z_galaxies; observational_alma_primary)
- question: Do the submillimetre sources at the centre of SSA22-LAB01 and their surrounding halo substructure explain the extended Lyα emission of the blob?
- processing.imaging.array_combination: Feathered with SCUBA-2 map [2.1 ALMA: "To both maps we ‘feather’ the single dish SCUBA-2 (regridded) map"]
- step 1: Image ALMA continuum
  - method: Concatenate two projects, clean with masks, multi-scale, natural weighting, full-res and 1 arcsec taper, feather with SCUBA-2 [2.1 ALMA: "We use a natural weighting of the visibilities and clean down to a threshold of 70 _µ_ Jy within 1000 iterations."]
  - software: CASA
  - parameter: threshold 70 µJy, 1000 iterations, taper 1 arcsec [2.1 ALMA: "clean down to a threshold of 70 _µ_ Jy within 1000 iterations"]
- result: Total ALMA 850 µm flux density (tapered, >3σ) = 1.68 ± 0.06 mJy [3.1: "_S_ 850 = 1 _._ 68 _±_ 0 _._ 06 mJy"]
- result: S850 of a+b = 0.95 ± 0.04 mJy [Table 1: "0 _._ 95 _±_ 0 _._ 04"]
- result: S850 of c = 0.73 ± 0.05 mJy [Table 1: "0 _._ 73 _±_ 0 _._ 05"]
- result: Flux discrepancy with SCUBA-2 = 2.9 ± 1.1 mJy [2.1 ALMA: "∆ _S_ 850 = 2 _._ 9 _±_ 1 _._ 1 mJy"]
- limitation (authors): Missing flux relative to SCUBA-2 and a lack of more compact array data. [2.1 ALMA: "Deeper observations with a slightly more compact array configuration would be beneficial to address this."]
- not stated (card): Number of SBs/execution blocks and observing dates for the ALMA data; Flux calibrator and absolute flux uncertainty; Whether archive-delivered or manually produced calibration was used, and CASA version; Feathering parameters and SCUBA-2 map scaling; SimALMA parameter values; Simulation initial conditions and code configuration; Molecular gas mass conversion details; SED template normalization de…

### 2019ApJ...875...96N: Dust Continuum Emission and the Upper Limit Fluxes of Submillimeter Water Lines of the Protoplanetary Disk around HD 163296 Observed by ALMA (2019; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Can sub-millimeter water line upper limits toward HD 163296 constrain the mm dust opacity and the extent of the hot water vapor region / H2O snowline position?
- processing.imaging.array_combination: Band 7 ACA data combined with 12m data for continuum imaging after phase shift [2.1 Observational setup and data reduct…: "we have combined Band 7 archival ACA (Atacama Compact Array) data (2016.1.00884.S, PI: V. Guzman) with our Band 7 data in our dust continuum imaging"]
- step 1: Calibrate and image Band 7 data
  - method: CASA calibration, Briggs CLEAN robust 0.5, continuum self-cal applied to lines; ACA combined for continuum [2.1 Observational setup and data reduct…: "In addition to the usual CLEAN imaging, we performed self-calibration of the continuum emission to improve the sensitivity and image quality."]
  - software: CASA
  - parameter: robust = 0.5 [2.1 Observational setup and data reduct…: "briggs weighting with a robust parameter of 0.5"]
- limitation (authors): Observation time was ~20% of the requested time, insufficient to test the model [3.1 Upper limit of the water line fluxes: "the observation time executed (20% of our proposed time in our Cycle 3 proposal) was not enough to test our model."]
- not stated (card): Self-calibration solution intervals, number of iterations and references; Line-free channels / continuum subtraction method for spectral cubes; Cell size, image size, masks, clean threshold; Number of ACA execution blocks and relative weighting in combination; Source position, PA used for the Keplerian filter and aperture center; How rms of peak flux density was measured for 3 sigma limits; Spect…

### 2018MNRAS.475..448T: Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study (2018; milky_way_ism, star_formation; observational_alma_primary)
- question: Is IRAS 19132+1035 a site of interaction between the GRS 1915+105 jet and the ISM, and what do the molecular lines say about ISM conditions and jet power?
- processing.imaging.array_combination: 12 m + 7 m cleaned jointly with TP image as model, feathering of positive clean components with TP, then clean again [3.1 Spectral line imaging: "we take the positive-only interferometer components from the CLEAN model, smooth them to the synthesized beam using the `imsmooth` task, and combine the smoothed interferometer component image with the re-gridded single dish image, using the `feather` task."]
- step 1: Combine 12 m, 7 m and TP data into line cubes
  - method: Custom CASA procedure: clean 12m+7m, regrid TP, primary-beam weight, feather clean components with TP, final clean with feathered model [3.1 Spectral line imaging: "We use a custom procedure, which combines the 12 m, 7 m, and total power array data, to image all of our spectral lines."]
  - software: CASA
  - parameter: natural weighting, 0.2 arcsec pixel, multiscale [0,1,5,10,15] [3.1 Spectral line imaging: "All imaging is done with natural weighting to maximize sensitivity, a pixel size of 0.2 arcsec"]
  - validation: Tested direct Fourier-plane feather combination; no clear improvement [3.1 Spectral line imaging: "did not find any clear improvements in image quality"]
- limitation (authors): Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density [5.4 Constraints on jet properties: "We have also assumed a constant external density."]
- limitation (authors): ALMA continuum lacks single-dish data so flux is underestimated [4.1 Continuum Emission: "we do not recover all the flux from the region in these ALMA continuum observations"]
- not stated (card): Line-free channels and continuum velocity ranges for each line; Channel width/velocity resolution and cube spectral regridding used in final imaging; Clean thresholds, mask, and number of iterations; Final synthesized beams and rms noise per cube; Gaussian fit and MCMC setup (priors, sampler, walkers) for SED and line fits; Regions A-D coordinates and extraction apertures; Manual calibration deta…

### 2021A&A...653A..53A: DEATHSTAR: nearby AGB stars with the Atacama Compact Array. II. CO envelope sizes and asymmetries: the S-type stars (2021; evolved_stars, astrochemistry; observational_alma_primary)
- question: Constrain CO circumstellar envelope sizes and deviations from spherical symmetry.
- processing.imaging.array_combination: Per-antenna sdimaging; reframe to ACA frequencies/channels; weighted TP image; tp2vis; joint tclean with ACA. [Observation with total power and data c…: "The calibrated data were exported into CASA images using the CASA task *sdimaging* and reframed to match the rest frequencies and channel numbers of the ACA data."] [Observation with total power and data c…: "The images were then combined into one single weighted image for each source."]
- step 1: Prepare ACA line images
  - method: Self-calibrate on peak 12CO channels and re-image with tclean. [Observation with the Atacama Compact Ar…: "All spectral windows in both bands were self-calibrated using two channels across the peak $^{12}$CO emission for all sources to improve the signal-to-noise ratio (S/N)."] [Observation with the Atacama Compact Ar…: "The data were re-imaged with the CASA task $tclean$ using the *Högbom* algorithm, a Briggs weighting (robust parameter = $0.5$), and $10\,000$ iterations."]
  - software: CASA, tclean
  - parameter: Two peak-emission channels for self-calibration. [Observation with the Atacama Compact Ar…: "All spectral windows in both bands were self-calibrated using two channels across the peak $^{12}$CO emission for all sources"]
  - parameter: Högbom; Briggs robust = 0.5; 10 000 iterations. [Observation with the Atacama Compact Ar…: "The data were re-imaged with the CASA task $tclean$ using the *Högbom* algorithm, a Briggs weighting (robust parameter = $0.5$), and $10\,000$ iterations."]
  - parameter: Interactive channel masks for sources brighter than 20 Jy. [Observation with the Atacama Compact Ar…: "Sources brighter than $20$ Jy were cleaned interactively by visually checking the noise level and manually selecting the shape of the masks applied on the emission regions in each channel map before each cleaning cycle."]
  - validation: Visual noise checks during interactive cleaning; average signal increase of 10 percent after self-calibration. [Observation with the Atacama Compact Ar…: "This increased the strength of the signal by 10 percent on average."] [Observation with the Atacama Compact Ar…: "Sources brighter than $20$ Jy were cleaned interactively by visually checking the noise level"]
- step 2: Recover extended emission with TP
  - method: Image TP antennas separately, align spectral grids, combine weighted images, generate tp2vis visibilities, and jointly image with ACA. [Observation with total power and data c…: "The calibrated data were exported into CASA images using the CASA task *sdimaging* and reframed to match the rest frequencies and channel numbers of the ACA data."] [Observation with total power and data c…: "The images were then combined into one single weighted image for each source."]
  - software: CASA, sdimaging, tp2vis, tclean
  - parameter: AI Vol, AFGL 3068, R Dor, IRC-30398; CO(2–1). [Observation with total power and data c…: "AI Vol, AFGL 3068, R Dor, and IRC-30398"] [Observation with total power and data c…: "All four sources were scanned to map the CO(2–1) emission using four 12-m TP antennas"]
  - parameter: Multiscale; 100 000 iterations. [Observation with total power and data c…: "Therefore, we run $tclean$ with the $multiscale$ algorithm and $100\,000$ iterations for all four sources."]
  - validation: Tested 10 000–100 000 iterations; inspected artefacts and residual flux; combination increased flux by at least 30 percent. [Observation with total power and data c…: "In addition, we tried several sets of iterations (from 10 000 to 100 000) and did not see any signs of artefacts introduced in the images."] [Observation with total power and data c…: "By checking the residual images, however, we noticed that flux was lost when applying too few iterations."]
- step 4: Estimate envelope sizes and axis ratios
  - method: Per-channel Gaussian fits to ACA-only visibilities; image-plane Gaussian fits to TP-only CO(2–1) for four sources. [Fitting the emission distribution: "We fit a Gaussian emission distribution model to the data visibilities in CO(2–1) and CO(3–2) in each velocity channel for the sources observed with ACA-only using the UVMULTIFIT library implemented in CASA (cite: uvmultifit)."] [Fitting the emission distribution: "The emission distributions of AI$\,\,$Vol, AFGL$\,\,$3068, R$\,\,$Dor, and IRC-30398 were fitted by a Gaussian model in the image plane on the CO(2–1) TP-only data."]
  - software: CASA, UVMULTIFIT
  - parameter: Position, flux, major axis, minor-to-major axis ratio, and position angle. [Fitting the emission distribution: "For each run, UVMULTIFIT gives the position, flux, major axis, ratio between minor and major axes, and the position angle of the fitted Gaussian."]
  - parameter: Central-channel Gaussian major axes and axis ratios. [Gaussian distribution fitting: "The measured major axes and ratio of the minor to major axis of the best-fitting Gaussian at the central channel"]
  - parameter: Error: average error from the two channels on each side of the central velocity channel. [Gaussian distribution fitting: "We take the error as the average error from the two channels on each side of the central velocity channel."]
  - assumption: Gaussian emission distribution gives an initial envelope-size estimate. [Fitting the emission distribution: "Such fitting of the emission distribution permits initial estimates of the sizes of the CO envelopes and will reveal signs of deviation from spherical symmetry."]
  - fitting: Gaussian model; UVMULTIFIT for ACA-only visibilities; TP diameters from deconvolved image-plane major axes. [Fitting the emission distribution: "We fit a Gaussian emission distribution model to the data visibilities in CO(2–1) and CO(3–2) in each velocity channel for the sources observed with ACA-only using the UVMULTIFIT library implemented in CASA (cite: uvmultifit)."] [Fitting the emission distribution: "The resulting deconvolved major axes give an estimate of the diameters of the CO envelopes."]
  - validation: Inspect velocity-dependent fits for spikes, negative regions, missing flux, and poor Gaussian descriptions. [Gaussian distribution fitting: "Negative regions emerge, which is due to the flux being resolved out."] [Gaussian distribution fitting: "As a consequence, the emission cannot be properly fitted by a Gaussian distribution, leading to fluctuating spikes."]
- step 7: Check TP radial profiles and flux losses
  - method: Run CASAIRING on four TP-only CO(2–1) cubes; compare radial brightness distributions, deconvolved Gaussian sizes, photodissociation radii, and ACA-only sizes. [Image fitting: "obtained by running the CASA task CASAIRING on the TP-only image cubes of the four stars AFGL$\,$3068, AI$\,$Vol, IRC-30398, and R$\,$Dor."] [Image fitting: "Using observations with the ACA only, the CO(2–1) sizes of the CSEs of AFGL$\,$3068 and AI$\,$Vol obtained by measuring the CO(2–1) FWHM from the visibility fitting are underestimated by a factor of two compared to using the TP data."]
  - software: CASA, CASAIRING
  - assumption: TP observations cover the full extent of CO(2–1) emission. [Image fitting: "As our TP observations cover the full extent of the CO(2–1) emission"]
  - fitting: Gaussian radial emission distributions. [Image fitting: "For all four stars, the resulting emission distribution follows a Gaussian distribution"]
  - validation: ACA-only versus TP comparison exposes underestimated or unreliable interferometric sizes. [Image fitting: "Further, the effects of resolved-out flux on the ACA-only visibility fits of IRC-30398 and R$\,$Dor do not permit a reliable size measurement for these sources."]
- result: T Cet CO(2–1) Gaussian major axis = 4.58 ± ±0.34 arcsec [Table 2: "T Cet | 10.8 | 4.58$\pm$0.34 | 0.79$\pm$0.06"]
- result: Z Ant CO(2–1) Gaussian major axis = 3.24 ± ±0.17 arcsec [Table 2: "Z Ant | 6.2 | 3.24$\pm$0.17 | 0.84$\pm$0.06"]
- result: UY Cen CO(2–1) Gaussian major axis = 1.49 ± ±0.71 arcsec [Table 2: "UY Cen | 5.0 | 1.49$\pm$0.71 | 0.52$\pm$0.23"]
- result: AM Cen CO(2–1) Gaussian major axis = 5.59 ± ±0.27 arcsec [Table 2: "AM Cen | 6.8 | 5.59$\pm$0.27 | 0.90$\pm$0.06"]
- result: ST Sco CO(2–1) Gaussian major axis = 4.32 ± ±0.10 arcsec [Table 2: "ST Sco | 10.6 | 4.32$\pm$0.10 | 1.00$\pm$0.02"]
- result: FU Mon CO(2–1) Gaussian major axis = 8.29 ± ±0.17 arcsec [Table 2: "FU Mon | 10.2 | 8.29$\pm$0.17 | 0.84$\pm$0.03"]
- result: NSV 24833 CO(2–1) Gaussian major axis = 3.76 ± ±0.21 arcsec [Table 2: "NSV 24833 | 8.2 | 3.76$\pm$0.21 | 0.96$\pm$0.06"]
- result: DY Gem CO(2–1) Gaussian major axis = 4.50 ± ±0.15 arcsec [Table 2: "DY Gem | 12.7 | 4.50$\pm$0.15 | 0.51$\pm$0.04"]
- result: RZ Sgr CO(2–1) Gaussian major axis = 9.00 ± ±0.09 arcsec [Table 2: "RZ Sgr | 27.6 | 9.00$\pm$0.09 | 0.99$\pm$0.01"]
- result: TT Cen CO(2–1) Gaussian major axis = 6.26 ± ±0.31 arcsec [Table 2: "TT Cen | 14.2 | 6.26$\pm$0.31 | 1.00$\pm$0.07"]
- result: GI Lup CO(2–1) Gaussian major axis = 3.81 ± ±0.14 arcsec [Table 2: "GI Lup | 9.8 | 3.81$\pm$0.14 | 0.95$\pm$0.06"]
- result: RT Sco CO(2–1) Gaussian major axis = 6.99 ± ±0.07 arcsec [Table 2: "RT Sco | 21.6 | 6.99$\pm$0.07 | 1.00$\pm$0.01"]
- result: IRC-10401 CO(2–1) Gaussian major axis = 5.43 ± ±0.42 arcsec [Table 2: "IRC -10401 | 10.6 | 5.43$\pm$0.42 | 0.85$\pm$0.06"]
- result: ST Sgr CO(2–1) Gaussian major axis = 1.52 ± ±0.17 arcsec [Table 2: "ST Sgr | 8.5 | 1.52$\pm$0.17 | 0.98$\pm$0.05"]
- result: T Sgr CO(2–1) Gaussian major axis = 3.55 ± ±0.40 arcsec [Table 2: "T Sgr | 5.8 | 3.55$\pm$0.40 | 0.99$\pm$0.10"]
- result: W Aql CO(3–2) Gaussian major axis = 4.62 ± ±0.05 arcsec [Table 2: "4.62$\pm$0.05 | 1.00$\pm$0.02"]
- result: θ Aps CO(2–1) Gaussian major axis = 4.90 ± ±0.06 arcsec [Table 2: "$\theta$ Aps | 10.1 | 4.90$\pm$0.06 | 0.97$\pm$0.01"]
- result: R Dor TP-only CO(2–1) deconvolved major axis = 14.69 ± ±0.27 arcsec [Table 2: "R Dor$^*$ | 42.7 | 14.69$\pm$0.27 | 0.92$\pm$0.03"]
- result: U Men CO(2–1) Gaussian major axis = 7.15 ± ±0.20 arcsec [Table 2: "U Men | 7.0 | 7.15$\pm$0.20 | 0.88$\pm$0.03"]
- result: IRC-30398 TP-only CO(2–1) deconvolved major axis = 12.24 ± ±0.41 arcsec [Table 2: "IRC-30398$^*$ | 27.5 | 12.24$\pm$0.41 | 0.82$\pm$0.06"]
- result: V1302 Cen CO(2–1) Gaussian major axis = 1.94 ± ±0.28 arcsec [Table 2: "V1302 Cen | 6.3 | 1.94$\pm$0.28 | 1.00$\pm$0.11"]
- result: V996 Cen CO(2–1) Gaussian major axis = 4.58 ± ±0.27 arcsec [Table 2: "V996 Cen | 7.4 | 4.58$\pm$0.27 | 0.85$\pm$0.06"]
- result: X TrA CO(2–1) Gaussian major axis = 6.19 ± ±0.06 arcsec [Table 2: "X TrA | 10.7 | 6.19$\pm$0.06 | 0.99$\pm$0.01"]
- result: AQ Sgr CO(3–2) Gaussian major axis = 0.93 ± ±0.36 arcsec [Table 2: "0.93$\pm$0.36 | 0.90$\pm$0.04"]
- result: V821 Her CO(2–1) Gaussian major axis = 6.53 ± ±0.04 arcsec [Table 2: "V821 Her | 31.5 | 6.53$\pm$0.04 | 0.98$\pm$0.01"]
- result: AI Vol TP-only CO(2–1) deconvolved major axis = 14.56 ± ±0.60 arcsec [Table 2: "AI Vol$^*$ | 37.6 | 14.56$\pm$0.60 | 0.94$\pm$0.06"]
- result: AFGL 3068 TP-only CO(2–1) deconvolved major axis = 17.14 ± ±0.73 arcsec [Table 2: "AFGL 3068$^*$ | 40.3 | 17.14$\pm$0.73 | 0.86$\pm$0.06"]
- result: T Cet CO(2–1) minor-to-major axis ratio = 0.79 ± ±0.06 dimensionless [Table 2: "T Cet | 10.8 | 4.58$\pm$0.34 | 0.79$\pm$0.06"]
- result: UY Cen CO(2–1) minor-to-major axis ratio = 0.52 ± ±0.23 dimensionless [Table 2: "UY Cen | 5.0 | 1.49$\pm$0.71 | 0.52$\pm$0.23"]
- result: FU Mon CO(2–1) minor-to-major axis ratio = 0.84 ± ±0.03 dimensionless [Table 2: "FU Mon | 10.2 | 8.29$\pm$0.17 | 0.84$\pm$0.03"]
- result: DY Gem CO(2–1) minor-to-major axis ratio = 0.51 ± ±0.04 dimensionless [Table 2: "DY Gem | 12.7 | 4.50$\pm$0.15 | 0.51$\pm$0.04"]
- result: RZ Sgr CO(2–1) minor-to-major axis ratio = 0.99 ± ±0.01 dimensionless [Table 2: "RZ Sgr | 27.6 | 9.00$\pm$0.09 | 0.99$\pm$0.01"]
- result: AFGL 3068 and AI Vol ACA-only size underestimate relative to TP = two ± not stated dimensionless [Image fitting: "Using observations with the ACA only, the CO(2–1) sizes of the CSEs of AFGL$\,$3068 and AI$\,$Vol obtained by measuring the CO(2–1) FWHM from the visibility fitting are underestimated by a factor of two compared to using the TP data."]
- result: Flux increase after TP+ACA combination = at least 30 ± not stated percent [Observation with total power and data c…: "After data combination, the flux of the four observed sources increased by at least $30$ percent."]
- limitation (authors): Missing flux and high noise can significantly alter Gaussian fits; sizes are first approximations. [Discussion and summary: "A number of the observations presented in this paper are subject to missing or resolved-out flux, or high noise levels that can significantly alter the Gaussian fits."]
- limitation (authors): Gaussian-size reliability decreases with increasing MLR. [Discussion and summary: "The reliability of the Gaussian fit estimates decreases with increasing MLR which will affect the larger sources in particular (cite: deathstar)."]
- limitation (authors): Distance uncertainties affect linear sizes and model comparisons. [Discussion and summary: "The measured sizes are also affected by the large uncertainties in the distances."]
- not stated (card): CASA, pipeline, UVMULTIFIT, and tp2vis versions.; Per-source execution blocks, observing dates, configurations, and baseline ranges.; Self-calibration channel indices, solution intervals, solution type, reference antenna, and iteration sequence.; Image cell sizes, image dimensions, cleaning thresholds, and masks for sources at or below 20 Jy.; Multiscale scale sizes and TP-to-ACA visibility weigh…

### 2018A&A...617A..23B: Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN (2018; evolved_stars, astrochemistry; observational_alma_primary)
- question: What are the spatial distribution, abundances and radial extent of CS, SiS, 29SiO and H13CN in the circumstellar envelope of the S-type AGB star W Aql, resolved with ALMA?
- processing.imaging.array_combination: Main array + ACA combined in visibility plane with antenna-specific weighting; TP feathered in image plane [3 Observations and data reduction: "The combination of the main array and ACA data is conducted in the visibility plane with antenna-specific weighting, whereas the TP data is combined with the rest of the data via feathering in the image plane."]
- step 1: Image and extract line properties
  - method: CLEAN imaging of combined 12m+ACA+TP data, moment maps and spectra extracted with apertures [3 Observations and data reduction: "Imaging of all spectral lines was carried out with CASA using the CLEAN algorithm with natural weighting"]
  - software: CASA
  - parameter: natural weighting; 1 or 2 km/s channels [3 Observations and data reduction: "The spectral channels were binned to a velocity resolution of 1 km s$^{-1}$ and 2 km s$^{-1}$ for strong and weak spectral lines, respectively."]
- step 2: Fit emission size in uv plane
  - method: Fit circular Gaussian, then Gaussian plus delta function, to visibilities per channel (main array + ACA only) [4.3 uv fitting: "we use the CASA tool *uvmultifit* (cite: Marti-Vidal2014), to fit geometric flux models to the bright emission regions of all spectral lines."]
  - software: uvmultifit, CASA
  - parameter: Gaussian position, flux density, FWHM; delta component at same position [4.3 uv fitting: "described by its position (relative to the current stellar position of RA 19:15:23.379 and DEC –07:02:50.38 J2000.0 (cite: Ramstedt2017)), flux density, and FWHM size"]
  - assumption: Gaussian intensity distribution; uncertainties assume reduced chi2 of 1 [Appendix uv-fitting: "meaning that the reduced $\chi^2$ can be assumed to be similar to its expected value of unity"]
  - fitting: chi2 minimisation; uncertainties from post-fit covariance matrix [Appendix uv-fitting: "estimates the uncertainties of the fitted parameters from the curvature of the $\chi^2$ distribution at its minimum via the diagonal elements of the post-fit covariance matrix"]
  - validation: Residual images imaged and checked as Gaussian noise; Monte Carlo exploration of chi2 PDFs [Appendix uv-fitting: "we have performed a Monte Carlo analysis of our Gaussian source model plus additional delta component across the full parameter space"]
- limitation (authors): Spherical symmetry assumed despite asymmetric emission [6.2 Limitations of radiative transfer m…: "The most obvious limitation of the radiative transfer models is that they assume spherical symmetry"]
- limitation (authors): Weak lines too low S/N for uv fitting [4.3 uv fitting: "the signal-to-noise ratio (S/N) for all weak lines is too low for confident fitting"]
- not stated (card): CASA version used for calibration and imaging; CLEAN threshold, mask criteria, cell size and image size; Line-free channels and continuum subtraction method; Flux calibration uncertainty and whether archive products were used as is; uvmultifit settings (initial guesses, channel handling); Exact ALI model grid, fitting criterion and how best fit was judged beyond by-eye; Wind velocity profile para…

### 2024A&A...692A..86H: Millimetre observations of the S-type AGB star χ Cygni: Variability of the emission of the inner envelope (2024; evolved_stars, astrochemistry; multi_facility_alma_minor)
- question: Variability and morpho-kinematics of χ Cygni's inner CSE; an independent ALMA/ACA check of the SiO(5-4)/SiO(6-5) emission ratio.
- step 4: Check the SiO ratio with ACA and LTE modelling
  - method: Compare archived ACA and NOEMA SiO spectra; calculate LTE ratios and integrate radiative transfer through a spherical CSE. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "In order to get an independent evaluation of the emission ratio, we analysed archived ALMA/ACA observations of the SiO(5-4) and SiO(6-5) line emissions of $\chi$ Cygni from Project 2021.2.00147.S (PI M. Saberi)."] [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "producing a simple LTE model of the morpho-kinematics and integrating the radiative transfer equation over a spherical CSE."]
  - parameter: ACA covers the whole emission; NOEMA comparison uses R<1.5 arcsec. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "The ACA measurement covers the whole emission while the NOEMA measurement is over $R$\<1.5 arcsec only."]
  - parameter: Reference model, as printed: mass-loss rate 2.4 M⊙ yr−1; terminal velocity 8 km s−1; SiO/H=10−5. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "a mass-loss rate of 2.4 M$_\odot$ yr$^{-1}$, a terminal velocity of 8 km s$^{-1}$, an SiO/H abundance ratio of 10$^{-5}$"]
  - parameter: SiO density 1.5 SiO/cm3 at 165 au, multiplied by a Gaussian with e-folding radius 215 au. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "meaning a density of 1.5 SiO/cm$^3$ at a distance of 165 au from the centre of the star, multiplied by a Gaussian having a $e$-folding radius of 215 au"]
  - parameter: Radial velocity: 2 km s−1 at 17 au, increasing to 2+6(1−0.1/r)^0.8. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "a radial velocity increasing from 2 km s$^{-1}$ at 17 au to 2+6(1$-$0.1/$r$)$^{0.8}$ at a distance $r$"]
  - parameter: T(K)=100(210/r[au])^0.78. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "a radial dependence of the temperature of the form $T$(K)=100(210/$r$\[au\])$^{0.78}$."]
  - assumption: Initial LTE ratio calculation neglects differential opacity and assumes LTE level populations. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "when neglecting opacity (more precisely when neglecting the difference between the effects of opacity on each of the two line emissions) and assuming level populations predicted by LTE"]
  - fitting: Standard radial velocity, abundance and temperature distributions give good fits; fitting algorithm and statistic not stated. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "We find that standard radial distributions of the velocity, molecular abundance and temperature give good fits to the data."]
  - validation: Independent ACA comparison and variation of LTE reference parameters within reasonable limits. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "Indeed, it is $\sim$0.7 instead of 0.86, probably consistent within uncertainties."] [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "when varying these within reasonable limits, we find that the emission ratio SiO(5-4)/SiO(6-5) remains between 0.5 and 0.6"]
- result: 2023 A-configuration Si16O(5-4)/Si16O(6-5) mean ratios, S1 and S2 = 0.86 in S1 and 0.92 in S2 ± not stated dimensionless [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "using 2023 A-configuration data, give mean emission ratios of 0.86 in S$_1$ and 0.92 in S$_2$, corresponding to temperatures of 19 and 21 K."]
- result: LTE temperatures corresponding to 2023 A-configuration SiO ratios, S1 and S2 = 19 and 21 ± not stated K [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "using 2023 A-configuration data, give mean emission ratios of 0.86 in S$_1$ and 0.92 in S$_2$, corresponding to temperatures of 19 and 21 K."]
- result: Merged A+B SiO mean ratios, S1 and S2 = 0.76 in S1 and 0.68 in S2 ± not stated dimensionless [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "Using instead A+B-configuration data, which however mixes 2023 and 2024 observations, these values become 0.76 in S$_1$ and 0.68 in S$_2$, corresponding to temperatures of 27 and 36 K."]
- result: NOEMA/ACA SiO ratio comparison, retained in the paper's wording = ∼0.7 instead of 0.86 ± not stated dimensionless [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "Indeed, it is $\sim$0.7 instead of 0.86, probably consistent within uncertainties."]
- result: SiO(5-4)/SiO(6-5) ratio from varied spherical LTE models = between 0.5 and 0.6 ± not stated dimensionless [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "when varying these within reasonable limits, we find that the emission ratio SiO(5-4)/SiO(6-5) remains between 0.5 and 0.6"]
- limitation (authors): ACA and NOEMA cover different spatial extents. [Si$^{16}$O(5-4)/Si$^{16}$O(6-5) emissio…: "The ACA measurement covers the whole emission while the NOEMA measurement is over $R$\<1.5 arcsec only."]
- limitation (authors): The north-western mass-ejection interpretation is limited by sensitivity and angular resolution. [The red-shifted north-western octant: e…: "the situation is not as clear as it was in the case of EP Aqr because the data are of lesser sensitivity and lower angular resolution."]
- limitation (authors): The angular resolution cannot reliably map individual SiO maser spots. [Si$^{16}$O($\nu$=1,$J$=6-5) maser: "the angular resolution is insufficient to map reliably the maser emission and possibly reveal multiple emitting spots simultaneously present in the close neighbourhood of the star"]
- not stated (card): ACA execution blocks, observing dates, spectral setup and exact downloaded products.; ACA calibration software, version, flux calibration and any additional flagging.; ACA imaging or spectral-extraction procedure, aperture, velocity integration limits and uncertainty calculation.; NOEMA line-free channels and continuum-subtraction implementation.; NOEMA self-calibration solution intervals, refere…

### 2021A&A...654L...8C: SUPER. VI. A giant molecular halo around a z∼2 quasar (2021; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Is there extended molecular (CO(3-2)) gas in the circumgalactic medium of the z~2 quasar cid_346 beyond its ISM, how far does it extend, and how much molecular gas could it hold?
- step 1: Reduce and image the ACA CO(3-2) data
  - method: Calibrated MS from the standard pipeline scriptForPI; cubes cleaned with tclean using interactive masks, no continuum subtraction; spectra from primary-beam corrected cubes [2 Observations: "We obtained the calibrated measurement set by running the standard pipeline through the"] [2 Observations: "Deconvolution and cleaning were executed using the task"]
  - software: CASA v.5.6, tclean
  - parameter: native channel width 5.45 km/s [2 Observations: "The data were imaged at their native spectral resolution of $\Delta v_{\rm channel} =5.45$ km s$^{-1}$"]
  - parameter: Briggs weighting, robust = 0.5 [2 Observations: "We applied Briggs weighting and set the robust parameter equal to 0.5."]
- step 3: Check for ACA continuum
  - method: Collapsed line-free spw17 map to place an upper limit on the continuum [Appendix A.1: "We verified this by using a line-free spectral window (spw17) adjacent to the one containing the CO(3-2) line"]
  - software: CASA
  - parameter: 3 sigma upper limit S_106GHz < 0.5 mJy/beam [Appendix A.1: "Using this map, we can place an ACA $3\sigma$ upper limit on the continuum level of $\rm S_{106~GHz}<0.5~mJy~beam^{-1}$"]
  - validation: Upper limit is consistent with the ALMA detection of Circosta+21 [Appendix A.1: "which is consistent with the detection by (cite: Circosta+21)"]
- step 4: Extract spectra in apertures, fit Gaussians, build the curve of growth
  - method: CO(3-2) spectra extracted from several apertures of ALMA (r = 0.6-10 arcsec) and ACA (r > 10 arcsec) cubes, fitted with Gaussians; fluxes plotted against aperture radius [Appendix A.3: "For small apertures probed by the ALMA data ($r_{aperture}=0.6\ensuremath{''}-5\ensuremath{''}$), the CO(3-2) spectrum exhibits a single component"] [Appendix A.3: "Apertures with $r>10\ensuremath{''}$ are only reliably probed by the ACA data."]
  - software: CASA
  - parameter: ACA spectra rebinned to 160 km/s; single broad Gaussian per aperture; ALMA-t fluxes from elliptical apertures (a=15, b=10 arcsec and a=20, b=15 arcsec) [Appendix A.3: "The ACA spectra were rebinned to $\Delta v_{channel}=160$ km s$^{-1}$ in order to maximise the S/N."] [Appendix A.3: "All spectra were fitted using a single broad Gaussian component"]
  - assumption: The additional component at v~1500 km/s is too faint to fit and is excluded from the single-Gaussian fits [Appendix A.3: "None of these single-Gaussian fits include the additional component centred at $v\sim1500$ km s$^{-1}$"]
  - fitting: Gaussian fits, no sampler or priors stated [Results: "A Gaussian fit returns a total flux of $8.7\pm2.6$ Jy km s$^{-1}$"]
  - validation: Compared ACA and ALMA spectra from different apertures; flux curve plateaus beyond r_ap ~ 25 arcsec [Results: "by comparing ACA and ALMA spectra extracted from different apertures"] [Results: "and it plateaus for larger apertures"]
- step 5: Model the ACA uv visibilities
  - method: uv visibilities modelled as a circular Gaussian plus a point source [Results: "the data are modelled using a circular Gaussian function with $\rm FWHM=300\pm80$ kpc, in addition to a point source (the unresolved ISM) which contributes very little to the total flux"]
  - parameter: Gaussian FWHM = 300+-80 kpc [Results: "the data are modelled using a circular Gaussian function with $\rm FWHM=300\pm80$ kpc, in addition to a point source"]
  - assumption: Unresolved ISM represented by a point source [Results: "in addition to a point source (the unresolved ISM)"]
  - validation: Size consistent with the curve-of-growth estimate; zero-baseline flux consistent with the spectral flux within its large error [Results: "This size estimate is consistent with the analysis of the"] [Discussion and conclusions: "which is consistent, within its (large) error, with the CGM flux measured from the spectrum"]
- step 8: Make moment maps of the ACA cube
  - method: CASA immoments with a velocity window and flux threshold [Appendix A.5: "by selecting the velocity range $v\in[-300, 300]$ km s$^{-1}$and masking pixels below a flux threshold of 0.04 Jy beam$^{-1}$ km s$^{-1}$"]
  - software: CASA
  - parameter: v in [-300, 300] km/s; threshold 0.04 Jy/beam km/s [Appendix A.5: "by selecting the velocity range $v\in[-300, 300]$ km s$^{-1}$and masking pixels below a flux threshold of 0.04 Jy beam$^{-1}$ km s$^{-1}$"]
  - validation: Authors caution that the ACA beam dilutes kinematic signatures and the features cannot be studied in detail [Appendix A.5: "since the very large beam of ACA would dilute any kinematic signature of kiloparsec-scale outflows"]
- result: ACA total CO(3-2) flux (CGM, r<~200 kpc) = 8.7 ± +-2.6 Jy km/s [Results: "A Gaussian fit returns a total flux of $8.7\pm2.6$ Jy km s$^{-1}$"]
- result: ACA flux relative to the ISM component of Circosta+21 = 14 ± +-5 dimensionless [Results: "which is a factor of $14\pm5$ higher than estimated by (cite: Circosta+21) for the ISM component"]
- result: Halo extent from the curve of growth = ~200 ± not stated kpc [Results: "we infer that the CO halo extends up to $r\sim200$ kpc"]
- result: uv-fit Gaussian FWHM = 300 ± +-80 kpc [Results: "the data are modelled using a circular Gaussian function with $\rm FWHM=300\pm80$ kpc"]
- result: uv-fit zero-baseline CO(3-2) flux = 16 ± +-11 Jy km/s [Table 3: "FWHM=$300\pm80$ kpc | $16\pm11$ | $40\pm30$"]
- result: uv-fit L'CO(3-2) = 40 ± +-30 1e10 K km/s pc^2 [Table 3: "FWHM=$300\pm80$ kpc | $16\pm11$ | $40\pm30$"]
- result: Flux within r_ap = 15 arcsec = 4.2 ± +-1.9 Jy km/s [Appendix A.3: "contains half of our fiducial CGM CO(3-2) flux ($4.2\pm1.9$ Jy km s$^{-1}$"]
- result: Best-fit FWHM of the broad ACA CO(3-2) line = ~1000 ± not stated km/s [Appendix A.3: "The best-fit FWHM value is $\sim1000$ km s$^{-1}$ for all ACA spectral fits."]
- result: ACA 3 sigma continuum upper limit at 106 GHz = <0.5 ± not stated mJy/beam [Appendix A.1: "we can place an ACA $3\sigma$ upper limit on the continuum level of $\rm S_{106~GHz}<0.5~mJy~beam^{-1}$"]
- limitation (authors): Spectral analysis limited by low S/N [Results: "Although our spectral analysis is limited by the low signal-to-noise (S/N) of the data"]
- limitation (authors): The ALMA dataset has poor coverage of the redshifted side of the CO line [2 Observations: "it does not provide good coverage of the redshifted side of the CO line"]
- limitation (authors): ACA beam is too large to analyse kinematics in detail [Appendix A.5: "Due to the poor resolution and low S/N of the data, none of these features can be studied in detail."]
- not stated (card): tclean parameters for the ACA cubes: cell size, image size, niter, threshold, deconvolver, and the interactively drawn masks; How the ACA data were combined or not with the ALMA 12 m data (ACA and ALMA are treated as separate datasets); Details of the scriptForPI calibration (flagging, calibrators) and the ACA spectral windows used for the CO cube; Aperture centre and exact extraction method for …

### 2017ApJ...850L...6A: ALMA Discovery of Dust Belts around Proxima Centauri (2017; debris_disks, exoplanets; observational_alma_primary)
- question: Does Proxima Centauri host circumstellar dust belts (a Kuiper belt analog), and what are their location, temperature and mass?
- processing.imaging.array_combination: ACA and 12-m data combined in images; ACA epochs assigned the first-epoch position before combining [Observations: "all data were assigned the formal position of the first epoch of observation, prior to combination of all epochs."]
- step 2: Separate stellar from dust emission
  - method: Compare ALMA 12-m peak and photospheric model prediction with ACA flux [3.1 The Emission from the Star: "indicates that $\sim$70-80% of the flux density detected by ACA ($340\pm60\,\mu$Jy; Fig. [1](#fig:aca)) does not arise from the star"]
  - assumption: Star unresolved; non-thermal emission negligible [3.1 The Emission from the Star: "is negligible ($\ll$1 $\mu$Jy)"]
- step 4: Search for outer belt in ACA data
  - method: Azimuthal averaging over elliptical annuli with a grid of PA and eccentricity [3.3 A Possible Outer Belt at 30 au: "We analyzed a grid of different position angles and eccentricities of the ellipses."]
  - parameter: best PA ~140 deg, i ~45 deg, peak at ~23'' [3.3 A Possible Outer Belt at 30 au: "ellipse PA $\simeq140\ensuremath{^\circ}$ (major axis) and an eccentricity corresponding to an inclination angle $i\simeq45\ensuremath{^\circ}$"]
  - assumption: Circular belt tilted; T_d ~10 K with same temperature law [3.3 A Possible Outer Belt at 30 au: "It would be extremely cold (with $T_d\simeq10$ K, if the same temperature law is assumed)"]
  - validation: Peak vanishes progressively for deviating parameters; detection stated as marginal [3.3 A Possible Outer Belt at 30 au: "Deviations from this combination of parameters produce a progressive vanishing of the feature."]
- result: Outer belt total flux density = ~1.7 ± not stated mJy [3.3 A Possible Outer Belt at 30 au: "we estimate a total flux density of $\sim$ 1.7 mJy"]
- result: Outer belt total mass = 0.33 ± not stated Earth masses [3.3 A Possible Outer Belt at 30 au: "corresponding to a total mass (including large bodies) of $0.33~M_\ensuremath{\oplus}$"]
- limitation (authors): Data insufficient for proper modeling; secondary source could be a noise peak [3.2 Dust Around Proxima Centauri: "While our data are insufficient for a proper modeling"]
- not stated (card): Cell size, image size, number of iterations and clean threshold/masks; Exact elliptical annulus binning and noise estimation for the 30 au profile; Which ACA+12m combination weighting was used for combined images; Detailed derivation of the total flux of 1.7 mJy for the outer belt; Calculation excluding substellar companion via RV

### 2026ApJ..1001..184M: Reconciling 3D Models for the Central 10 pc of the Milky Way (2026; milky_way_ism, astrochemistry; multi_facility_alma_minor)
- question: Where along the line of sight do the 50 and 20 km/s clouds, Sgr A East and the CND lie relative to Sgr A*; build a 3D model of the central 10 pc consistent with radio observations and CMZ orbital kinematics
- processing.imaging.array_combination: 12m + 7m jointly imaged in CASA, then feathered with total power (2013.1.00857.S) [3.2.2 Band 3 and 6 CND Mosaic: "The 7m and 12m data were then jointly imaged using CASA, and the images were then feathered with the total power data."]
- step 1: Calibrate and image ALMA data
  - method: ALMA pipeline calibration (2019.1.01240.S) and manual calibration (2013.1.00857.S); tclean imaging with robust 1.0; 7m+12m joint imaging feathered with total power for 2013.1.00857.S [3.2.1 Band 3 CO pointing toward Sgr A*: "The imaging of both line and continuum emission was performed in CASA, using the `tclean` task, with a robust weighting of 1.0"] [3.2.2 Band 3 and 6 CND Mosaic: "The 7m and 12m data were then jointly imaged using CASA, and the images were then feathered with the total power data."]
  - software: CASA, tclean, ALMA pipeline
  - parameter: robust = 1.0 [3.2.1 Band 3 CO pointing toward Sgr A*: "with a robust weighting of 1.0"]
- step 2: Combine VLA and GBT NH3 data
  - method: Miriad-based combination: GBT cubes smoothed and regridded, deconvolved, converted to visibilities and jointly imaged with VLA; final linear combination of joint and GBT cubes with immerge [3.1.2 GBT observations: "We then jointly imaged the GBT and VLA visibilities using the Miriad-`invert` and `mossdi` tasks."] [3.1.2 GBT observations: "we used the Miriad-`immerge` task to linearly combine the GBT+VLA joint image cubes we produced and the spectrally smoothed and regridded GBT image cubes"]
  - software: Miriad, ALMICA, CASA feather
  - parameter: relative VLA/GBT weights set manually by resetting system temperature columns [3.1.2 GBT observations: "the relative weights between the GBT and VLA visibilities were manually optimized by artificially resetting the system temperature columns"]
  - validation: Residual systematic intensity errors <~1% stated to be negligible compared with thermal noise [3.1.2 GBT observations: "which is negligible as compared to the thermal noises in our present study"]
- result: 12CO cube per-channel noise (ALMA Band 3) = 13.3 mJy/beam (0.395 K) ± not stated mJy/beam [3.2.1 Band 3 CO pointing toward Sgr A*: "The per-channel noise in this cube is 13.3 mJy/beam (0.395 K)."]
- result: 12CO cube maximum recoverable scale = 21'' (0.84 pc) ± not stated arcsec [3.2.1 Band 3 CO pointing toward Sgr A*: "It is sensitive to emission on size scales up to 21$''$ (0.84 pc)."]
- result: NH3 (3,3) per-channel noise (VLA+GBT) = 1.3 mJy/beam (0.26 K) ± not stated mJy/beam [3.1.2 GBT observations: "a per-channel noise of 1.3 mJy/beam (0.26 K)"]
- limitation (authors): Deconvolution does not conserve integrated flux, leading to underestimates of extended emission in the NH3 combination [3.1.2 GBT observations: "The deconvolution algorithms used throughout this procedure do not conserve integrated flux densities."]
- limitation (authors): CO absorption cannot set how far in front the clouds are [5 Discussion: "While our absorption measurements alone cannot determine how far in front the 20 and 50 km/s clouds lie"]
- limitation (authors): Exact line-of-sight distances remain hard to determine [6 Conclusions: "their exact distance along the line of sight still remains difficult to determine"]
- not stated (card): ALMA flux calibrator and flux-scale uncertainty for either project; ALMA pipeline version and whether archive products were used as is; pipeline vs manual for each execution block; Whether any self-calibration was done; tclean parameters other than robust = 1.0: deconvolver, niter/threshold, masks, image size, uv-taper, and the spectral channelization of the 12CO cube (stated only as 141 kHz nati…

### 2024MNRAS.527.4420M: The Quasar Feedback Survey: characterizing CO excitation in quasar host galaxies (2024; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: Do AGN feedback (ionised outflows, radio jets) in 17 Type 2 quasars at z<0.2 impact the global molecular gas content and CO excitation (low-J and J_up=6,7 SLEDs)?
- step 1: image ACA CO(1-0) cubes
  - method: tclean in CASA with natural weighting and Hogbom deconvolver; velocity bins of 50 or 100 km/s [3.1 CO(1-0) observations: "We image the CO(1-0) emission using the TCLEAN function in CASA and apply natural weighting with the Högbom deconvolver."]
  - software: CASA tclean
  - parameter: bin widths 100 km/s for non-detections, 50 km/s if S/N high enough [3.1 CO(1-0) observations: "Bin widths of 100 km $\rm s^{-1}$ were used for non-detections and 50 km $\rm s^{-1}$ bins were used if the S/N was high enough"]
- step 2: extract spectra in a common 30 arcsec aperture
  - method: spectra extracted from the ACA cubes in an aperture matched to the APEX CO(2-1) beam (~30 arcsec diameter); curves of growth show flux flattens beyond 30 arcsec [3.1 CO(1-0) observations: "we take an aperture equivalent to the APEX beam size when observing CO(2-1), which is $\sim$ 30 arcsec diameter"] [3.1 CO(1-0) observations: "Beyond 30 arcsec the flux density flattens off in almost all cases"]
  - parameter: aperture ~30 arcsec diameter (~80 kpc at median z) [3.1 CO(1-0) observations: "we extract spectra with an aperture diameter of $\sim$ 80 kpc at the median redshift"]
  - assumption: 30 arcsec aperture captures total flux; extraction at 3 sigma level would lose on average 60% of flux [3.1 CO(1-0) observations: "we would measure on average 60% less flux when compared to the extraction at 30 arcsec"]
  - validation: curves of growth of ACA CO(1-0) for sources with integrated S/N > 5 [3.1 CO(1-0) observations: "we plot the curves of growth of the ACA CO(1-0)"]
- result: flux lost if CO(1-0) extracted with a 3 sigma minimum level instead of the 30 arcsec aperture = 60% on average (range 25-89%) ± not stated percent [3.1 CO(1-0) observations: "we would measure on average 60% less flux when compared to the extraction at 30 arcsec"]
- limitation (authors): ACA CO(1-0) may resolve out extended emission, which could inflate r21 [5.1.2 Optical depth effects: "some of the CO(1-0) emission may be resolved out given the ACA spatial resolution"]
- limitation (authors): J1430+1339 ACA CO(3-2) may be over-resolved and miss flux [3.3 CO(3-2) Observations: "there is a possibility it is slightly over resolved and perhaps missing flux"]
- limitation (authors): Small number of sources with the required data limits conclusions about correlations [5.2 A localised impact on CO?: "it is hard to take strong conclusions from these investigations"]
- not stated (card): CASA version and whether archive-delivered or re-run calibration products were used for the ACA data; tclean parameters beyond natural weighting and Hogbom: cell size, image size, mask, threshold, niter; line-free channels / continuum subtraction (if any) for ACA CO(1-0) and the J1430+1339 CO(3-2) cube; exact spectral setup (rest frequencies, spectral windows, channelisation) of the ACA observati…

### 2013ApJ...774...73I: ALMA Resolves 30 Doradus: Sub-parsec Molecular Cloud Structure near the Closest Super Star Cluster (2013; star_formation, milky_way_ism, nearby_galaxies; observational_alma_primary)
- question: How do dense molecular clump properties and CO/dust abundances in 30Dor-10, near the super star cluster R136, compare with Galactic clumps and with distance from R136?
- processing.imaging.array_combination: APEX + ALMA with CASA feather [2.2 APEX: "The APEX image cube was combined with a cleaned ALMA cube using the CASA task `feather`"]
- step 1: Combine ALMA and APEX CO cubes
  - method: Feather APEX with cleaned ALMA cube, then use as clean model [2.2 APEX: "To mitigate these effects we used the feathered image as a model in clean deconvolution"]
  - software: CASA, CLASS
  - parameter: APEX conversion Tmb to Jy/beam multiply by 39 [2.2 APEX: "The APEX data was converted from main beam temperature to Jy$\;$bm$^{-1}$ by multiplying by 39 (cite: apex)"]
  - validation: Varied relative flux calibration; <10% uncertainty in 12CO clump properties, <5% in 13CO [2.2 APEX: "the image combination process results in less than 10% uncertainty of $^{12}$CO clump properties and less than 5% uncertainty of $^{13}$CO clump properties."]
- limitation (authors): Clumps are approximately beam-sized; higher resolution will break them up [6: "Higher resolution will likely break these clumps up into smaller substructures"]
- not stated (card): CASA version and calibration procedure (manual vs pipeline), flagging; tclean/clean parameters: weighting, robust, cell, image size, masks, threshold; Continuum channel selection and continuum subtraction method; Feather parameters and relative flux scaling applied; Exact hybrid clump decomposition parameters (contrast, S/N, floor levels); Dust temperature = Tex assumption details and mass-map re…

### 2018MNRAS.480.4974H: On the multiplicity of ALMA Compact Array counterparts of far-infrared bright quasars (2018; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Are the Herschel/SPIRE far-infrared fluxes of FIR-bright z=2-4 SDSS quasars from single sub-mm sources or from multiple counterparts, and what does this imply for major mergers as triggers?
- step 1: Recalibrate and image ACA data
  - method: Re-ran ALMA pipeline with QA flag files, antenna position corrections and flux.csv; primary-beam corrected [3 The ACA data: "using the flagging files, antenna position corrections and flux files (flux.csv) provided by the ALMA observatory quality assurance process"]
  - software: CASA 5.1
- step 2: Identify ACA counterparts within SPIRE beam
  - method: Search within 11" of SPIRE coordinates; primary = unique or closest counterpart; compare with SDSS/SPIRE positions [4 Results: "we look for counterparts within (18$\\ \\ ^{\prime\prime}$/2)+2$\\ \\ ^{\prime\prime}$= 11$\\ \\ ^{\prime\prime}$ from the SPIRE coordinates"]
  - validation: SDSS coordinates checked against GAIA and UKIDSS [4.1 Astrometry: "we checked the SDSS coordinates against GAIA and UKIDSS"]
- step 3: Test detectability of hidden companions
  - method: Simulate point-source pairs, smooth to ACA beam, fit beam to primary and inspect residuals; apply same to real maps and to degraded Bussmann maps [4.3: "We then fit with the ACA beam to the primary (brightest and centred) component on each image and look for residuals at the position of the secondary (fainter) component."]
  - software: CASA imsmooth
  - validation: Degraded HXMM01 still showed residual at S_res/S_tot=0.05 [4.3: "albeit with S$_{\rm res}$/S$_{\rm tot}$=0.05"]
- result: Quasars with unique ACA counterpart within 11" = 19 of 28 ± not stated sources [4 Results: "Of the 28 SDSS quasars, 19 have unique ALMA counterparts, while six and three sources have a second and third counterparts within 11"]
- result: Lowest detection significance (J233456) = 3.5 ± not stated sigma [4 Results: "Source J233456, the source with the lowest ACA detection level, is detected at 3.5$\sigma$."]
- result: J233600 hidden-companion residual fraction = 0.27 ± not stated dimensionless [4.3: "S$_{\rm res}$/S$_{\rm tot}$=0.27 at a distance of 2$.\!\!^{\prime\prime}$5"]
- result: Mean ACA offsets for six objects from SDSS and SPIRE = 3.59 and 1.62 ± not stated arcsec [5.2: "mean offsets for those six objects of 3$.\!\!^{\prime\prime}$59 and 1$.\!\!^{\prime\prime}$62"]
- limitation (authors): Coarse ACA resolution cannot resolve pairs closer than 2-3"; physical association unproven [5.4: "Sub-arcsec resolution observations are absolutely essential"]
- not stated (card): imaging parameters (tclean weighting, robust, cell, size, deconvolution); source extraction method for fluxes and positions (fitting vs peak); how rms/detection significance was computed; how beam-subtraction residual fitting was implemented; self-calibration or flux scale uncertainty; SFR/flux conversion used

### 2022A&A...661L...4A: A first look at the submillimeter Sun with ALMA (2022; sun; observational_alma_primary)
- question: What are the disk structures, center-to-limb brightness temperature variations, and chromospheric electron temperature profiles of the quiet Sun in the first full-disk ALMA Band 7 (0.86 mm; 347 GHz) solar images, combined with Bands 3 and …
- step 1: Acquire, select, and map full-disk Total Power images
  - method: Process 12-m TP double-circle scan observations using JAO CASA scripts and the methodology of White et al. (2017), selecting antennas with better T_sys (PM03 for Band 3, PM04 for Band 6, PM02 for Band 7) and applying CASA sdgaincal before … [Observations and data reduction: "In Bands 3 and 6, we only used the images that were provided by antennas PM03 and PM04, respectively, because of their better system temperature, $T_{sys}$."] [Observations and data reduction: "The TP data were acquired and processed using the methodology described by (cite: 2017SoPh..292...88W)."]
  - software: CASA, sdgaincal
  - parameter: Band 7 beam FWHM = 21 arcsec; scan duration = 3 min [Observations and data reduction: "The full width at half maximum (FWHM) of the Band 7 single dish beam was 21$''$ and each TP antenna scanned the full solar disk in 3 min."]
  - assumption: Arc-like modulations are associated with opacity variations and can be corrected by adjusting gains relative to the central field position in double-circle scans [Observations and data reduction: "It is possible that these modulations are associated with opacity variations during observations."] [Observations and data reduction: "This task takes advantage of the fact that the double-circle mode observes the same position in the center of the field of view and adjusts the gains throughout the whole dataset relative to the measured intensity at the center."]
  - validation: Suppression of large-scale arc-like brightness modulations in Band 7 images [Observations and data reduction: "We were able to largely suppress them by invoking CASA’s task sdgaincal before mapping."]
- limitation (authors): Low spatial resolution (21 arcsec) of the single-dish Band 7 images prevents a detailed study of the association between ALMA and H-alpha features. [abstract: "In spite of the low spatial resolution (21$''$), several interesting results were obtained."]
- limitation (authors): Absolute calibration jumps exist between datasets, and cross-normalization cannot replace true absolute calibration (e.g., using the Moon). [Center-to-limb variation and modeling: "As noted in Paper II, there is a jump in $T_b$ between the commissioning and the current Band 6 data set, attributed to absolute calibration issues, and so is the case with Band 7."]
- not stated (card): Exact CASA version used to process the Total Power data and run sdgaincal; Specific parameters passed to CASA task sdgaincal (e.g., radius, calmode); Quantitative parameters and kernel used for the diffuse light correction inherited from Paper I; Best-fit polynomial coefficients A_0, A_1, A_2, A_3 of T_b(mu) and the derived dataset normalization factors; Exact single-dish beam FWHMs for Bands 3 a…

### 2021AJ....161..271F: A Detailed Characterization of HR 8799's Debris Disk with ALMA in Band 7 (2021; debris_disks, exoplanets; observational_alma_primary)
- question: Where is the inner edge of HR 8799's cold debris disk and what is its radial profile shape (sharp vs smooth), and is an extra planet implied?
- step 3: Fit radial profile models in visibility space
  - method: RADMC-3D model images x primary beam, sampled at uv points, chi2 summed over Band 7 12m, ACA, Band 6 12m; three surface-density models; extra Gaussian source for bright background source; central point source [3.1 Model Description: "the radiative transfer code is used to produce model images which are multiplied by the primary beam"]
  - software: RADMC-3D, emcee
  - parameter: 22 free parameters (Model 1), 24 (Models 2, 3) [3.1 Model Description: "This gives us a total of 22 free parameters for Model 1, and 24 for Models 2 and 3."]
  - parameter: Surface density zero inside 70 au and beyond 600 au for Models 2 and 3 [3.1 Model Description: "we set the surface density to zero interior to 70 au for both Model 2 and Model 3"]
  - assumption: Dust: 70% astrosilicate, 15% amorphous carbon, 15% water ice; size power law -3.5, 1 um to 1 cm; Band 7 opacity 1.9 cm2/g [3.1 Model Description: "with a size distribution following a power law of index $-$3.5 over sizes from 1 micron to 1 centimeter"]
  - assumption: Band 6 emission scaled from Band 7 via free alpha_mm [3.1 Model Description: "it is scaled to band 6 via a spectral index, $(\alpha_\mathrm{mm})$, which is left as free parameter"]
  - fitting: MCMC; uniform priors except Gaussian priors on i (26.8+/-2.3 deg) and PA (68.25+/-5.55 deg) [3.1 Model Description: "We assume uniform priors except for the disk inclination and position angle"]
  - validation: Likelihood ratio exp(-dchi2/2) between models, BIC, residual maps; rerun with unconstrained orientation [3.2 Best-Fit Model Results: "Even after considering the lower number of free parameters of Model 1, e.g. through the Bayesian Information Criterion"]
- step 5: Map CO 3-2 in ACA data
  - method: tclean cube, natural weights, compared to Keplerian toy model [7 The gas content: "we map the CO $J$=3-2 line emission, using the TCLEAN algorithm to create a full-spectral-resolution cube"]
  - software: CASA
  - assumption: Toy model inclination 33 deg, stellar mass 1.56 Msun [7 The gas content: "assumed inclination = 33$^{\circ}$, stellar mass = 1.56 $M_{\odot}$"]
- result: Model 1 inner edge radius = 135 ± 4 au [Table 3: "$r_{\min}$ | Inner Radius (au) | $135 \pm 4$"]
- result: Model 3 inner-edge Gaussian peak radius r1 = 172 ± +26/-40 au [Table 3: "Peak Radius Inner Edge (au) | $172_{-40}^{+26}$"]
- result: Model 3 inner edge sigma = 37 ± +14/-21 au [Table 3: "Standard Deviation Inner edge (au) | $37_{-21}^{+14}$"]
- result: Spectral index alpha_mm (Model 3) = 2.5 ± 0.2 dimensionless [3.2 Best-Fit Model Results: "which in our preferred model (Model 3) was found to be $2.5\pm0.2$"]
- result: Disk flux Band 7 (Model 3) = 8.1 ± 1.0 mJy [3.2 Best-Fit Model Results: "$3.1 \pm 0.5\,$mJy and $8.1\pm 1.0\,$mJy in Band 6 and Band 7, respectively"]
- result: Disk dust mass (Model 3) = 1.3e-1 ± 0.1e-1 Earth masses [Table 4: "$(1.3 \pm 0.1)\times10^{-1}$"]
- result: Bright source flux Band 7 (Model 3) = 316 ± +20/-19 uJy [3.2 Best-Fit Model Results: "Its total flux is found to be $316^{+20}_{-19}$ $\mu\mathrm{Jy}$ at 880 microns"]
- result: Disk inclination with unconstrained prior = 30.8 ± +2.8/-3.2 deg [4.2 The disk orientation: "we recover a disk inclination of $30.8^{\circ\,+2.8}_{-3.2}$"]
- limitation (authors): Model-dependent total flux; ALMA flux about half of SCUBA-2 flux [4.3 The disk flux: "On the other hand, one factor that could cause the ALMA flux to be too low is that it is model dependent."]
- not stated (card): MCMC settings (walkers, steps, burn-in, convergence); Uniform prior bounds for free parameters; Image size, cell size and clean threshold/masking for continuum; uv-range and weights used in the visibility fit; Pipeline version; Exact CO channels excluded; Disk scale height/aspect ratio and stellar parameters for RADMC-3D

### 2018A&A...619L...6N: First high-resolution look at the quiet Sun with ALMA at 3mm (2018; sun; observational_alma_primary)
- question: What do high-resolution ALMA 3 mm images show of the quiet Sun chromosphere: network/intranetwork brightness, center-to-limb variation, and spicules?
- processing.imaging.array_combination: feather with full-disk TP image, interferometric flux scaled down for 14% excess [Observations and data reduction: "The combination was done using CASA’s task `feather` and correcting for the fact that the flux of the derived images was higher than that of the FD image by 14%"]
- step 2: Fix pointing and combine with full-disk image
  - method: Cross-correlate with AIA 1600 Å; feather with processed FD image; primary beam correction [Observations and data reduction: "Therefore the actual pointing was computed by cross-correlation of the ALMA with the AIA 1600 Å images."]
  - software: CASA
  - assumption: FD disk-center Tb scaled to 7250 K [Full-disk images: "we scaled the FD image to match the quiet Sun brightness temperature at disk center reported in Paper I which was 7250 K."]
  - validation: Compared to AIA 1600/304 and IRIS [Results: "There is also a very strong similarity between the ALMA images and the Interface Region Imaging Spectrograph (IRIS) slit-jaw images in three bands"]
- limitation (authors): Unexplained excess emission beyond the limb up to 1000 K; segregation method not unique [Summary and discussion: "we got emission beyond the limb of up to 1000 K (14% of the disk center value), the origin of which we could not identify."]
- not stated (card): AIPS CLEAN parameters (weighting, robust, cell, image size, iterations); Self-calibration reference model and calibrator details; Details of single-dish processing (Appendix A mostly not given); Exact alignment/cross-correlation procedure for pointing; Polynomial fit and masking details beyond second degree; Azimuthal averaging bin widths

### 2021A&A...650A.153D: Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger at z ≃ 1.13 (2021; galaxy_clusters_and_sz, agn_and_quasars; archival_reuse)
- question: Reconstruct the intracluster pressure distribution and investigate the merger and diffuse radio emission in SPT-CL J2106-5844.
- processing.imaging.array_combination: Band 3 and Band 4 ACA observations combined in Compton y units for display only [Multicomponent model: "obtained by combining the Band 3 and Band 4 ACA observations naïvely converted to Compton $\vary$ units"] [Multicomponent model: "The ACA maps are presented only for display purposes and not used for any quantitative study."]
- step 5: Search for SZ pressure peaks and compact contamination
  - method: Jointly forward-model Band 3/4 ALMA+ACA visibilities; project a gNFW pressure model and sample its Fourier transform at measured uv coordinates; search for point sources. [SZ modeling: "the reconstruction method is devised to sample the Fourier transform of a map of the SZ effect from a model galaxy cluster to the $u\varv$-plane coordinates of the sampled visibilities."] [Free modeling run: "is obtained by numerical integration of a generalized Navarro-Frenk-White (cite: Nagai2007) pressure profile along the line-of-sight direction"]
  - parameter: Free SZ centroid, mass parameter, and inner slope [Free modeling run: "We perform a first modeling run assuming the universal parametrization by (cite: Arnaud2010) but allow the model centroid, mass parameter, and slope at small radii to vary."]
  - parameter: Unresolved sources: point models with power-law spectra [Free modeling run: "we use point source models to describe the contamination from unresolved compact sources with flux characterized by a simple power-law spectral dependence."]
  - assumption: Isothermal ICM; thermal SZ relativistic correction from Itoh2004 [SZ modeling: "We compute the average relativistic corrections to the thermal SZ spectrum by means of the approximation by (cite: Itoh2004)."] [SZ modeling: "Given the large uncertainties on the temperature distribution, we assume this to be described by an isothermal model"]
  - assumption: Flat Λ Cold Dark Matter: ΩM=0.30, ΩΛ=0.70, H0=70.0 km s−1 Mpc−1 [Introduction: "Throughout this work, we assume a spatially flat $\Lambda$ Cold Dark Matter cosmological model, with $\Omega_{\mathrm{M}}=0.30$, $\Omega_{\Lambda}=0.70$, and $H_0=70.0~\mathrm{km\,s^{-1}\,Mpc^{-1}}$."]
  - assumption: Do not model the extended radio source; extrapolate it with α=−1 to check contamination [Free modeling run: "We do not consider any model component to describe the extended radio source, which should not significantly contaminate the measured SZ signal."] [Free modeling run: "by assuming a power law spectrum with average spectral index $\alpha=-1$"]
  - fitting: Bayesian; uniform centroid prior across ACA field; wide uninformative mass/slope and point-source priors; split-normal temperature prior from the X-ray estimate. [Free modeling run: "The centroid coordinates are assumed to have a uniform prior extending over the field of view of ACA, while we consider wide uninformative priors for both the mass and slope parameters."] [Free modeling run: "Uninformative priors are assumed for the position, amplitude, and spectral index."]
  - validation: Test alternate gNFW/point-source priors and observation subsets; both SZ components remain identified. [Free modeling run: "checked that the two SZ components are identified independent of any prior assumptions on the gNFW parameters or point-like component, or of the specific subsets of observations employed in the modeling."]
- step 7: Constrain the central source spectrum and dust
  - method: Add ATCA compact-source fluxes to ALMA+ACA fits; fit spectral curvature, then add Herschel upper limits and fit power law plus modified blackbody. [Unresolved source: "we repeat the fit by including the flux measurements from the ATCA data at 2.1, 5.5, and 9 GHz."] [Unresolved source: "we extend the spectral model of the unresolved source to a modified power law, hence to fit for any potential spectral curvature at high frequency."]
  - parameter: Herschel upper limits: average fluxes in BCG-centered apertures with sizes equal to the respective beams [Unresolved source: "upper limits based on the average fluxes measured in each of the three *Herschel* bands within apertures centered on the BCG position and with size equal to the respective beams."]
  - assumption: Exclude EMU compact flux because extended radio emission may contaminate it [Unresolved source: "We do not consider here any information from the EMU observations as, at the EMU frequency, the extended radio structure may significantly contaminate the flux measured for the central source."]
  - assumption: Dust opacity power law; β=1.5 [Unresolved source: "For the dust opacity function, we consider a power-law form, $k_{\nu_{\textsc{rf}}}=k_{0}[(1+z)\nu/\nu_{0}]^{\beta}$"] [Unresolved source: "where the dust emission efficiency index is fixed to $\beta=1.5$ (cite: PlanckXLIII2016; Erler2018)."]
  - assumption: ν0=c/350 μm; κ0=0.192 m² kg−1 [Unresolved source: "We set the reference frequency to $\nu_0=c/350~\mathrm{\mu m}$"] [Unresolved source: "the typical value for the mass absorption coefficient at $350~\mathrm{\mu m}$ of $\kappa_{0}=0.192~\mathrm{m^{2}~kg^{-1}}$ (cite: Draine2003)."]
  - fitting: Reconstruct dust mass and temperature posterior distributions [Unresolved source: "the heavy degeneracy affecting the posterior probability distribution of the reconstructed mass and temperature."]
  - validation: Compare modified power-law and dust-model spectra; note disagreement in Band 3 and heavy mass–temperature degeneracy. [Unresolved source: "We observe a general agreement with the modified power law model, except for a discrepancy over ALMA’s Band 3 spectral window."] [Unresolved source: "the heavy degeneracy affecting the posterior probability distribution of the reconstructed mass and temperature."]
- result: BCG dust mass = 3.5 × 10^8 ± +2.3/-1.9 × 10^8 M⊙ [Unresolved source: "we measure values for the dust mass and temperature of $3.5\substack{+2.3\\-1.9}\cdot10^8~\mathrm{M_{\odot}}$ and $19.8\substack{+7.0\\-6.6}~\mathrm{K}$, respectively"]
- result: BCG dust temperature = 19.8 ± +7.0/-6.6 K [Unresolved source: "we measure values for the dust mass and temperature of $3.5\substack{+2.3\\-1.9}\cdot10^8~\mathrm{M_{\odot}}$ and $19.8\substack{+7.0\\-6.6}~\mathrm{K}$, respectively"]
- limitation (authors): Chandra source counts do not constrain the ICM temperature distribution. [Chandra: "The low number of source counts in the available *Chandra* data did not allow for deriving significant constraints on the temperature distribution of the ICM within SPT-CL J2106-5844."]
- limitation (authors): Most X-ray hardness structures have low significance. [Chandra: "aside from the bright core region, it is not possible to identify any structure with a significance higher than $2\sigma$."]
- limitation (authors): Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map. [Diffuse emission: "the different angular resolutions of the available radio data, combined with the severe sparsity and low significance of the observations at high frequencies, do not allow for building a detailed map of the spectral index distribution"]
- not stated (card): ALMA/ACA calibrated measurement-set release identifiers, calibration CASA/pipeline versions, and any additional flagging or averaging.; Exact visibility likelihood, visibility-weight treatment, and implementation of the 5% flux-calibration uncertainty.; Forward-model map grid, line-of-sight integration limits, primary-beam model, and frequency integration across spectral windows.; Numerical fixed…

### 2025ApJ...994..158G: Oxygen Isotopes Reveal Low-mass Star Dominance in the Small Magellanic Cloud (2025; astrochemistry, nearby_galaxies, star_formation; observational_alma_primary)
- question: Can the oxygen isotope ratios (especially 18O/17O) of molecular gas in the low-metallicity SMC be measured via C18O and C17O J=2-1 and what do they say about stellar enrichment and the galaxy-wide IMF
- processing.imaging.array_combination: ACA and TP combined with CASA feather (12CO and 13CO only) [Observations and data reduction: "The combination of the single-dish and ACA datasets was performed using the"]
- step 1: Calibrate and image the ACA data
  - method: ALMA pipeline calibration in CASA, then manual tclean imaging [Observations and data reduction: "The raw data were calibrated using the ALMA pipeline of the Common Astronomy Software Applications (CASA) package (cite: 2022PASP..134k4501C)."]
  - software: CASA 6.5.4, tclean
  - parameter: Hogbom deconvolver, Briggs robust 0.5 [Observations and data reduction: "Briggs weighting with a robust parameter of 0.5"]
  - parameter: AUTO-MULTITHRESH masking, parameters as Kepley et al. 2020 Table 2 [Observations and data reduction: "The automated masking algorithm"]
  - parameter: pixel size 1.1 arcsec, primary beam correction applied [Observations and data reduction: "A primary beam correction was applied to all cleaned data."]
  - validation: Flux calibration accuracy estimated to be better than 10% from the calibrators [Observations and data reduction: "the flux calibration accuracy is estimated to be better than 10%"]
- step 2: Add short spacings and match resolution
  - method: Feather TP 12CO and 13CO data with the ACA data, then convolve all lines to a common 7.5 arcsec beam; C18O and C17O stay ACA-only [Observations and data reduction: "The combination of the single-dish and ACA datasets was performed using the"] [Observations and data reduction: "all data were convolved to a common circular beam of 7$''$5 for subsequent analysis"]
  - software: CASA feather
  - parameter: common circular beam 7.5 arcsec [Observations and data reduction: "all data were convolved to a common circular beam of 7$''$5 for subsequent analysis"]
  - assumption: C18O and C17O ACA-only spectra have negligible missing flux at the peak position because they are compact [Short spacing: "we conclude that the missing flux in the ACA-only data is negligible for the C$^{18}$O $J=2 \to 1$ and C$^{17}$O $J=2 \to 1$ spectra at the peak position"]
  - validation: ACA-only vs ACA+TP flux comparison: ACA-only recovers 70% (12CO) and 82% (13CO) of total flux, 83% and 97% at the peak position [Short spacing: "the ACA-only data account for only 70% and 82% of the total flux densities in the ACA+TP combined data"]
- step 3: Extract peak spectra and fit Gaussians
  - method: Extract spectra at the emission peak (13CO peak) and fit a Gaussian to each to get velocity, peak Tb, FWHM and integrated intensity [Results: "we extracted spectra at the emission peak and used them to derive the isotopic ratios."] [Results: "We performed a Gaussian fitting to each spectrum"]
  - parameter: Integration velocity range 105-145 km/s for 12CO and 122-129 km/s for the other three lines [Table 2: "The values are obtained by integrating the velocity range of 105–145 km s$^{-1}$ for"]
  - assumption: 12CO and 13CO from ACA+TP; C18O and C17O from ACA-only [Table 2: "whereas those of C$^{18}$O ($2 \to 1$) and C$^{17}$O ($2 \to 1$) are derived from the ACA-only datasets"]
  - fitting: Single-Gaussian fit to each line profile; software not stated [Results: "We performed a Gaussian fitting to each spectrum"]
  - validation: Velocity centroids of the four lines agree within the uncertainties and with earlier studies [Results: "The velocity centroids of the four transitions are consistent within the uncertainties"]
- result: 13CO/C18O integrated intensity ratio = 90 ± +/-5 dimensionless [Results: "The integrated intensity ratio of $^{13}$CO/C$^{18}$O is 90$\pm$5"]
- result: C18O J=2-1 integrated intensity = 0.099 ± +/-0.005 K km/s [Table 2: "0.099$\pm$0.005"]
- result: C17O J=2-1 integrated intensity = 0.114 ± +/-0.002 K km/s [Table 2: "0.114$\pm$0.002"]
- result: C17O J=2-1 detection significance = >10 ± not stated dimensionless (S/N) [Results: "the C$^{17}$O $J=2\to1$ transition is detected with a signal-to-noise ratio of $>$10"]
- limitation (authors): Single sightline/cloud; representativeness for the whole SMC unknown [Discussion: "but establishing whether it is representative on a global scale will require future studies with larger samples."]
- limitation (authors): 12CO shows moderate missing flux in ACA-only data [Short spacing: "emphasizing the need for total power data to accurately determine its brightness temperatures"]
- limitation (authors): Single Gaussian component assumed for simplicity; 12CO optical depth leads only to lower limits on 16O/18O and 16O/17O [Local thermodynamic equilibrium: "we assume a single Gaussian component for all molecules for simplicity"]
- not stated (card): Image size / field of view and tclean threshold, niter, mask parameter values (only given by reference to Kepley et al. 2020); Whether and how continuum was subtracted, and which channels were line-free; CASA version and pipeline version used for calibration (only the imaging version is given); Feather settings (sdfactor, TP scaling, units conversion from Jy/beam to K) and TP imaging/gridding det…

### 2016A&A...595A.117J: The ALMA Protostellar Interferometric Line Survey (PILS). First results from an unbiased submillimeter wavelength line survey of the Class 0 protostellar binar… (2016; astrochemistry, star_formation; observational_alma_primary)
- question: What is the chemical complexity of the Class 0 protostellar binary IRAS 16293-2422 on solar-system scales, and how are glycolaldehyde, its isomers and isotopologues formed?
- processing.imaging.array_combination: 12 m and ACA combined before final imaging [3.1 Data, calibration and imaging: "before combining the 12 m array and ACA datasets and performing the final imaging"]
- limitation (authors): Abundances relative to H2 highly uncertain as continuum is optically thick [5.1 Excitation analysis: "even as a limit the abundance with respect to H$_2$ is highly uncertain"]
- not stated (card): CASA version and exact calibration scripts; tclean weighting/robust, cell and image size, deconvolver, masks; Reference continuum-subtraction code details; Synthetic-spectrum code and fitting procedure, uncertainties on column densities; Details of line width/LSR velocity fixed values used; Rotation diagram fit details

### 2024PSJ.....5..221C: Evidence for Surprising Heavy Nitrogen Isotopic Enrichment in Comet 46P/Wirtanen's Hydrogen Cyanide (2024; solar_system, astrochemistry; observational_alma_primary)
- question: Derive the 12C/13C and 14N/15N ratios in HCN in the coma of Jupiter-family comet 46P/Wirtanen from ACA observations of HCN, H13CN and HC15N, using non-LTE radiative transfer modeling
- step 1: Image ACA cubes of the targeted lines
  - method: CASA tclean (Hogbom) with natural weighting after flagging, calibration and continuum subtraction as in Cordiner et al. 2023 [Observations: "Imaging was performed using the CASA `tclean` (Högbom) algorithm with natural weighting and a pixel size of $0.5''$."] [Observations: "Data flagging, calibration and continuum subtraction were performed as described by (cite: cor23)."]
  - software: CASA tclean
  - parameter: pixel size 0.5''; 30''-diameter circular mask; threshold 2 x RMS [Observations: "Deconvolution was carried out within a $30''$-diameter circular mask centered on the comet, with a flux threshold of twice the RMS noise level ($\sigma$)."]
- step 6: Fit production rates and abundances of HCN, HC15N and H13CN
  - method: Least-squares fit of SUBLIME 1D model spectra to the flux-loss-corrected spectra; abundances relative to H2O using Q(H2O) from SOHO Ly-alpha [Results: "Best fitting production rates and abundances (relative to H$_2$O) for the three HCN isotopologues are given in Table [\[tab:results\]](#tab:results)."] [Results: "Formal ($1\sigma$) uncertainties were derived from the diagonal elements of the covariance matrix of the least-squares fit."]
  - software: SUBLIME
  - parameter: RMS noise multiplied by 1.29 for adjacent-channel correlation [Results: "the RMS noise measurement on each spectrum was multiplied by a factor of 1.29, following (cite: nix20)"]
  - assumption: Q(H2O) from cubic spline interpolation of SOHO Ly-alpha measurements, taken as applicable at the ACA spatial resolution [Results: "implies that the SOHO water production rates should be applicable at the spatial resolution of our ACA data"]
  - fitting: Least-squares; 1 sigma errors from the diagonal of the covariance matrix [Results: "Formal ($1\sigma$) uncertainties were derived from the diagonal elements of the covariance matrix of the least-squares fit."]
  - validation: Q(H2O) cross-checked against SOFIA (8e27 s-1) and IRTF (7e27 s-1) values from other dates [Results: "These $Q({\rm H_2O})$ values are consistent with the average water production rate of $8\times10^{27}$ s$^{-1}$ measured by (cite: lis19) using the SOFIA telescope"]
- result: HCN production rate (2018-12-02) = 5.20e24 ± +-0.09e24 s-1 [Table 2: "$(5.20\pm0.09)\times10^{24}$"]
- result: HC15N production rate (2018-12-07) = 1.03e23 ± +-0.25e23 s-1 [Table 2: "$(1.03\pm0.25)\times10^{23}$"]
- result: H13CN production rate (2018-12-07) = 7.70e22 ± +-2.49e22 s-1 [Table 2: "$(7.70\pm2.49)\times10^{22}$"]
- result: HCN abundance relative to H2O = 9.17e-4 ± +-0.16e-4 dimensionless [Table 2: "$(9.17\pm0.16)\times10^{-4}$"]
- result: HC15N abundance relative to H2O = 1.36e-5 ± +-0.33e-5 dimensionless [Table 2: "$(1.36\pm0.33)\times10^{-5}$"]
- result: H13CN abundance relative to H2O = 1.03e-5 ± +-0.32e-5 dimensionless [Table 2: "$(1.03\pm0.32)\times10^{-5}$"]
- limitation (authors): Raw statistical significance of the HC15N and H13CN detections is low [Results: "The raw statistical significance of our HC$^{15}$N and H$^{13}$CN detections is less than optimal"]
- limitation (authors): HCN and isotopologues were observed on different dates, so variations in Q(H2O) and HCN/H2O enter the uncertainty [Discussion: "Because HCN and its minor isotopologues were observed in comet 46P on different dates (almost 6 days apart)"]
- limitation (authors): CN may have an additional source beyond HCN photolysis, so CN/C15N need not equal HCN/HC15N [Discussion: "it should be noted that CN in cometary comae often has an additional source that cannot be explained by HCN photolysis alone"]
- not stated (card): Flux, bandpass and phase calibrators and the calibration route (manual or pipeline) and CASA version: all deferred to Cordiner et al. 2023; How the comet ephemeris tracking and the continuum subtraction (line-free channels, order) were done; tclean details: number of iterations, absolute threshold in mJy, channel width and velocity regridding of the cubes, execution blocks combined; SUBLIME input…

### 2019MNRAS.487.4037D: A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145 (2019; galaxy_clusters_and_sz; observational_alma_primary)
- question: Can joint forward-modelling of ALMA/ACA visibilities with Bolocam and Planck images constrain the pressure distribution of RX J1347.5-1145, and does the south-eastern SZ excess indicate a strong overpressure or reflect model geometry?
- step 1: Prepare ALMA/ACA visibilities
  - method: Manual calibration, spectral-window averaging and uv binning of visibilities per field [3.1: "we consider spectral window-averaged visibilities for each of the fields"]
  - software: CASA
  - assumption: Diagonal noise covariance; CMB and confusion negligible [3.1: "we then assume the ACA+ALMA block of the noise covariance matrix to be diagonal"]
- step 2: Joint Bayesian fit of spherical cool-core gNFW plus point source
  - method: Joint likelihood product of ACA+ALMA visibilities, Bolocam and Planck images; gNFW centred on X-ray peak with fixed Arnaud slopes, Te=7 keV, point source power law [5.1.1: "we fit a spherically symmetric gNW pressure profile whose centroid is set at the position of the peak in the observed X-ray brightness distribution"]
  - software: emcee, GALARIO, FFTW, astropy
  - parameter: Free: Pei, rs (uniform priors), point-source position, flux, spectral index; kappa Gaussian, eta exponential hyperparameters [Table 1: "$\mathcal{E}[1.00]$ is instead the exponential distribution with unitary expectation value"]
  - assumption: Te fixed at 7 keV [5.1.1: "we fix the electron temperature to $T_{\mathrm{e}}=7~\mathrm{keV}$"]
  - fitting: Affine-invariant ensemble MCMC (emcee), medians and 68% intervals [4.3: "we make use of the specific implementation of the affine-invariant ensemble sampling technique"]
  - validation: Data-free prior-only run and mock tests [5.1.1: "This has been performed by sampling the posterior distribution obtained in the case of a constant likelihood"]
- result: Spherical gNFW r_s = 3.10 ± 16th 2.97, 84th 3.24 arcmin [Table 2: "$r_{\mathrm{s}}$ | arcmin | $3.10$ | $2.97$ | $3.24$"]
- result: Spherical gNFW P_ei = 5.39e-2 ± 16th 5.16, 84th 5.65 (1e-2) keV cm^-3 [Table 2: "$5.39$ | $5.16$ | $5.65$"]
- result: Point-source flux at 90 GHz = 4.208 ± 16th 4.199, 84th 4.217 mJy [Table 2: "$4.208$ | $4.199$ | $4.217$"]
- result: Point-source spectral index = -0.431 ± 16th -0.462, 84th -0.399 dimensionless [Table 2: "$-0.431$ | $-0.462$ | $-0.399$"]
- result: Planck/ALMA+ACA scaling ratio = 0.993 ± 0.038 dimensionless [5.1.4: "with ratio equal to $0.993\pm 0.038$"]
- limitation (authors): Models differ in components so statistical comparison is misleading; overfitting may hide overpressure; X-ray arithmetic limited to linear perturbations [5.2: "a direct comparison based on statistical considerations would provide misleading results"]
- not stated (card): Exact binning parameters and number of averaged visibilities; Planck MILCA implementation details and Y_cyl Gaussian prior; MCMC walkers, steps, burn-in and convergence; Fitting code is not public/versioned; Chandra reduction details and X-ray arithmetic smooth models; Source of 12.5 keV vs 7 keV temperature choices beyond brief description

### 2017AJ....154..206L: Mapping Vinyl Cyanide and Other Nitriles in Titan's Atmosphere Using ALMA (2017; solar_system, astrochemistry; archival_reuse)
- question: Can C2H3CN be detected at submillimeter frequencies in Titan's atmosphere and spatially mapped, along with other nitriles, to constrain abundances and photochemistry/circulation?
- step 3: retrieve vertical abundance profiles
  - method: NEMESIS line-by-line radiative transfer with step (300 km) models for C2H3CN/C2H5CN and fractional scale-height gradient models for HC3N/CH3CN; spectra scaled to model in line-free regions [Results: "The abundances and fractional scale-height parameters $f_H$ were optimized by minimizing the sum of squares of the spectroscopic residuals"]
  - software: NEMESIS
  - parameter: 35 impact parameters up to 1000 km; Lorentz width 0.075 cm-1/bar, alpha 0.5 (HC3N 0.1, 0.75) [Results: "across 35 impact parameters between the center of Titan’s disk and the top of the model atmosphere at 1000 km"]
  - assumption: temperature profile from HASI+CIRS feathered 60-100 km; CO abundance 5.06e-5 [Results: "by feathering the profiles together in the range 60-100 km using a linearly graded (weighted) average."]
  - fitting: least squares minimization of residuals [Results: "optimized by minimizing the sum of squares of the spectroscopic residuals"]
  - validation: reduced chi-squared; step heights >200 km acceptable [Results: "we find that models with a step height of $>$200 km provide a reasonable fit to our C$_2$H$_3$CN and C$_2$H$_5$CN observations"]
- result: C2H3CN abundance (300 km step) = 3.03 ± 0.29 ppb [Table 1: "| C$_2$H$_3$CN | 3.03 (0.29) |"]
- result: C2H5CN abundance (300 km step) = 7.37 ± 0.32 ppb [Table 1: "| C$_2$H$_5$CN | 7.37 (0.32) |"]
- result: C2H5CN/C2H3CN ratio = 2.43 ± 0.26 dimensionless [Discussion: "The C$_2$H$_5$CN/C$_2$H$_3$CN abundance ratio of $2.43\pm0.26$"]
- result: HC3N fractional scale-height = 2.05 ± 0.16 dimensionless [Table 1: "$2.05\pm0.16$ and $1.63\pm0.02$, respectively."]
- result: CH3CN fractional scale-height = 1.63 ± 0.02 dimensionless [Table 1: "$2.05\pm0.16$ and $1.63\pm0.02$, respectively."]
- result: C3H8 mixing ratio = 8.5e-7 ± 0.6e-7 mixing ratio [Results: "best-fitting C$_3$H$_8$ mixing ratio of $(8.5\pm0.6)\times10^{-7}$"]
- limitation (authors): C3H8 lines blended so abundance uncertain; south pole partly hidden [Results: "our fitted value should be treated with extreme caution due to the fact that the two propane lines are both blended"]
- not stated (card): Line-free channels used for continuum subtraction; Velocity integration ranges for moment maps; Contour factor n and per-map RMS values; Exact CIRS temperature profile data; Initial values and optimizer settings for NEMESIS fits; Number of iterations/clean mask; Spectral windows and calibrators other than flux scale

### 2025A&A...703A..15M: Discovery of carbon monoxide emission from five debris disks around young A-type stars (2025; debris_disks, protoplanetary_disks; observational_alma_primary)
- question: Expand the sample of known CO-bearing debris disks around young intermediate-mass stars and explore the environmental conditions and origin (primordial vs. secondary) of their gas.
- processing.imaging.array_combination: Multi-epoch 12-m observations concatenated with CONCAT and reweighted with STATWT [Observations and data reduction: "For objects that were observed at more than one epoch (Table [1](#tab:obslog)), the resulting measurement sets were concatenated using the CONCAT task. To ensure the relative weights between the different data sets are correct we recalculated the data weights with the `CASA` STATWT task."]
- limitation (authors): Dust mass uncertainties are formal only and do not include systematic uncertainties in dust opacity (which can reach a factor of several) or non-single dust temperatures. [Dust masses: "We caution that the uncertainties given are formal errors only, taking into account the errors in the measured flux density, the distance of the system, and the derived dust temperature, but do not consider the possible systematic uncertainties associated with the value of the dust opacity, which can reach a factor of…"]
- limitation (authors): CO mass estimates assume LTE at 20 K and ISM isotopic ratios; non-LTE/subthermal excitation, different kinetic temperatures, isotope-selective photodissociation, or fractionation can alter true CO masses by a factor of several. [CO mass estimates: "For our adopted excitation temperature of 20 K and LTE, the $J=2$ rotational level is very efficiently populated, but a significantly different temperature and/or non-LTE environment may result in a lower fractional population than assumed and, accordingly, a higher CO mass."]
- limitation (authors): Predicted collisional mass loss rates (M_dot_Dmin) have large uncertainties (40-60% formal, potentially much larger systematically) because smallest grain sizes may deviate from the blowout size in high-f_d or gas-bearing disks. [Second generation gas produced in a ste…: "First, the typical formal uncertainty of the $\dot{M}_\mathrm{D_{min}}$ estimate is 40–60%, and the real uncertainty could be even substantially higher as there are a number of simplifying assumptions behind Eq. [\[eq:mdustprod\]](#eq:mdustprod)."]
- not stated (card): Exact pixel size (cell size) and image dimensions (imsize) used in TCLEAN for continuum and line cubes; Stopping criteria / threshold and masking strategy in TCLEAN; Whether primary beam correction was applied to continuum images and line cubes before flux extraction; Exact velocity intervals integrated to construct the moment 0 maps for HD 9985, HD 145101, HD 152989, and HD 155853; Exact apertur…

### 2018A&A...617A.129K: Submillimeter-wave emission of three Galactic red novae: cool molecular outflows produced by stellar mergers (2018; stellar_physics, astrochemistry, evolved_stars; observational_alma_primary)
- question: What are the physical, kinematic and chemical properties of the cool molecular remnants of three Galactic red novae (V4332 Sgr, V1309 Sco, V838 Mon), and how do they compare with post-AGB/pre-PN objects?
- processing.imaging.array_combination: The three V4332 Sgr datasets were combined [3.1 ALMA observations: "The three datasets were combined."]
- limitation (authors): Masses are lower limits, accurate to about a factor of ~2 at best owing to the CO/H2 conversion; line saturation uncertain [6.2 Masses dispersed in the merger even…: "The minimum masses we derive are accurate to within a factor of about $\sim$2, at best, owing to uncertain conversion factor"]
- limitation (authors): Velocity field and density degenerate in the Shape model [3.6 A 3-dimensional model of the CO emi…: "There is strong degeneracy between the velocity field and the density distribution which could not be broken with the current observations."]
- not stated (card): Cell size, image size, masks and clean thresholds for all ALMA imaging; Continuum subtraction method and line-free channels; Exact Gaussian-fit procedure (task/region) for sizes and positions; CASSIS fit setup: priors, line widths per species, source sizes for each component; Shape model parameters (density profile, velocity law details) and how best model chosen; SMA reduction details (MIR flagg…

### 2015ApJ...808..102K: Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA (2015; protoplanetary_disks; observational_alma_primary)
- question: What are the physical properties of six Taurus protoplanetary disks from CARMA 1.3 and 2.7 mm visibilities, and does a flared power-law or flared viscous accretion disk model fit better?
- processing.imaging.array_combination: tracks combined in the invert-Fourier transform step [3 Observations and Data: "Individual tracks have been calibrated and verified separately then combined in the invert-Fourier transform step to make maps."]
- limitation (authors): Inner radii unreliable due to resolution and decoherence; constant beta assumed; kappa0 uncertain by factor two [4.3 Model Parameters: "fitted values can be model-dependent and are likely unreliable due to systematic uncertainties in the observation, primarily the resolution."]
- not stated (card): Fitting code is not named or released; MCMC proposal widths, number of steps, burn-in and annealing schedule not given; Prior ranges for the free parameters; Stellar luminosities and masses adopted in RADMC-3D and photon numbers; Exact flux calibrator fluxes and which tracks were combined per target; Opacity law at infrared wavelengths used in RADMC-3D; Details of how inner radius and center offs…

### 2023PASP..135c4501P: Data Combination: Interferometry and Single-dish Imaging in Radio Astronomy (2023; instrumentation, nearby_galaxies; technical_calibration_or_instrument)
- question: Which interferometer plus single-dish data combination methods recover the true sky flux best, and how can their performance be quantitatively assessed (new A-par, fidelity, power-spectrum and spectrogram diagnostics)
- step 1: Simulate ALMA observations of the skymodel
  - method: Run simobserve on the synthetic skymodel for 12m (two configurations), ACA 7m and SD, with multiple fields and days [4.1 Simulated continuum observations: "we ran the `simobserve` task in CASA version 5.6.1 to create simulated observational data in MeasurementSet format (MSs)"]
  - software: CASA simobserve 5.6.1
  - parameter: 12m (7m): 52 (17) fields, each visited 30 (90) times per session, 10 s integration per field [4.1 Simulated continuum observations: "For 12m (7m) array, there are 52 (17) fields to cover the simulated image and each field is set to be visited 30 (90) times per observing session on different days with the integration time of 10 seconds per field."]
  - parameter: Skymodel 4096^2 pixels of 0.05'' (204.8'' per side) [4.1 Simulated continuum observations: "The model has $4,096^2$ pixels with a size of 0.05$''$ each, resulting in an image size of 204.8$''$ each side"]
- step 4: Combine SD and interferometric data with each method
  - method: Feather, SDINT (sdintimaging), MACF (tclean with SD image as startmodel, then feather) and FSSC applied to skymodel and M100; TP2VIS implemented in the script but not evaluated [3 Combination Methods: "The methods we present for evaluation are: Feather"] [3.4 TP2VIS: "we decided not to include it in the evaluation section of this paper"]
  - software: CASA 6.1 feather, CASA 6.1 sdintimaging, CASA 6.1 tclean, FSSC Python code, DC_script
  - parameter: Standard (default-like) values for briggs, sdfactor (Feather, MACF) and sdgain (SDINT); numbers not given [6.4 Single-dish flux recovery: "For simplicity, our data combinations assumed standard values for reduction parameters such as"]
  - parameter: MACF: SD image (Jy per pixel) used as tclean startmodel, then feathered with the SD image [3.3 Model-assisted CLEAN plus Feather m…: "providing the SD image (in units of Janskys per pixel) as the starting model image"]
  - assumption: Flux scales of the interferometer and SD data are aligned; astrometry aligned; images corrected for PB response [3 Combination Methods: "We assume that flux scales are aligned, but further fine-tuning can be done for specific use cases."]
  - validation: Results compared against the true skymodel (simulation) or the SD cube (M100) [5 Assessment metrics: "In real observations the emission of any interferometric or data combination map can be compared against its SD counterpart"]
- step 6: Compare combination methods
  - method: Compare A-par distributions, flux recovery per signal bin, intensity and A-par power spectra, and M100 spectrograms for int-CLEAN, Feather, SDINT, MACF (FSSC nearly identical to Feather) [6.3 Comparison between data combination…: "We quantitatively investigate the performance of the different data combination techniques"] [6.3 Comparison between data combination…: "The FSSC method is not shown but produced results nearly identical to Feather in this test."]
  - software: DC_script
- result: Skymodel total flux recovery by SDINT and MACF = above ~92% ± not stated % of reference flux [6.3 Comparison between data combination…: "The total flux recovery is improved by the SDINT and MACF methods with total flux values above $\sim$ 92% with respect to the true sky emission."]
- result: Skymodel SDINT A-par dispersion = 0.13 ± not stated dimensionless [6.3 Comparison between data combination…: "While SDINT shows a smaller dispersion of the A-par values ($\sigma($A-par$)=0.13$"]
- result: Skymodel MACF mean A-par = -0.08 ± not stated dimensionless [6.3 Comparison between data combination…: "MACF shows a better mean A-par value (A-par = -0.08"]
- result: Peak flux loss of brightest compact skymodel source in int-CLEAN = ~40% ± not stated % of true peak [6.1 The indispensable short-spacing inf…: "the peak flux of this source in the interferometric-alone int-CLEAN observations is reduced by a factor of $\sim$ 40% compared to the true emission in our skymodel"]
- result: M100 SDINT A-par and dispersion at SD resolution = |A-par| = -0.11 (as written) ± sigma(A-par) = 0.06 dimensionless [6.4 Single-dish flux recovery: "while SDINT shows slightly larger differences with respect to the SD flux ($|$A-par$|=-0.11$ and $\sigma($ A-par$)=0.06$)"]
- result: M100 Feather and MACF A-par dispersion = 0.04 ± not stated dimensionless [6.4 Single-dish flux recovery: "both showing narrow A-par distributions ($\sigma($ A-par$)=0.04$)"]
- limitation (authors): Test cases exclude bright emission extending beyond the well-characterised primary beam [3 Combination Methods: "Finally, we use test cases without bright emission that extends or emerges beyond the area of the well-characterised PB-response."]
- limitation (authors): At SD resolution the M100 comparison has few voxels per channel, making ~10% differences hard to interpret [6.4 Single-dish flux recovery: "Comparisons within these 10% variations are however difficult to interpret given the low number statistics available"]
- limitation (authors): Standard values were assumed for reduction parameters (briggs, sdfactor, sdgain) for simplicity [6.4 Single-dish flux recovery: "For simplicity, our data combinations assumed standard values for reduction parameters such as"]
- not stated (card): Calibration of the M100 Science Verification data (manual vs pipeline, CASA version, flux scale) and which calibrated products/MS were used; Actual sdfactor / effdishdiam values for Feather and MACF, sdgain and dishdia for SDINT (paper only says 'standard values'); sdintimaging deconvolver, scales, thresholds, cell size and image size; tclean cell/imsize and stopping threshold; Power-law index an…

### 2026MNRAS.546ag037E: Stellar-mass black holes on the millimetre Fundamental Plane of black hole accretion (2026; stellar_physics, agn_and_quasars; observational_alma_primary)
- question: Whether the newly-discovered millimetre fundamental plane of black hole accretion holds for accreting stellar-mass black holes (X-ray binaries), and whether ADAF or compact jet models can explain the correlation for these sources.
- step 1: Calibrate and image new ACA and archival ALMA continuum observations
  - method: Reduce data using the CASA pipeline following Davis et al. (2022) and Ruffa et al. (2024), and image the four continuum spectral windows together using CASA TCLEAN in multi-frequency synthesis mode. [New ACA observations: "The data were reduced using the COMMON ASTRONOMY SOFTWARE APPLICATIONS (CASA) pipeline (cite: McMullin07), adopting a version appropriate for each dataset and a standard calibration strategy."] [New ACA observations: "The continuum images were produced by combining the four continuum spectral windows using the CASA task TCLEAN in multi-frequency synthesis mode."]
  - software: CASA, TCLEAN
  - parameter: 230 GHz (ACA, Cygnus X-1 archival, GX 339-4 archival); 104 GHz (GRS 1915+105 archival) [Archival Observations: "The mm luminosity of Cygnus X-1, GRS 1915+105 and GX 339-4 was thus also estimated from archival ALMA continuum observations at $230$ GHz for Cygnus X-1 (Proposal ID: 2016.1.00496.S) and GX 339-4 (Proposal ID: 2019.1.01324.T) and at $104$ GHz for GRS 1915+105 (Proposal ID: 2017.1.00051.S)"]
- step 4: Fit the M_BH - L_nu,mm relation and the mm Fundamental Plane (mmFP)
  - method: Fit the combined SMBH + XRB sample (including new ACA data for Cygnus X-1 and archival 230 GHz data for GX 339-4) using LTS_LINEFIT and LTS_PLANEFIT, and evaluate Spearman rank correlation coefficients. [Results: "Following (cite: Ruffa24), we fitted the $M_{\rm BH}$ – $L_{\rm \nu,mm}$ and mmFP data, including the XRBs, using the LTS_LINEFIT and LTS_PLANEFIT routines of (cite: Cappellari2013), respectively."] [Results: "When performing these fits we only included the new ACA data for Cygnus X-1 and the archival data for GX 339-4 (due to its substantial flux variability in the ACA observations)."]
  - software: LTS_LINEFIT, LTS_PLANEFIT
  - fitting: Linear regression in log space using LTS_LINEFIT and LTS_PLANEFIT routines of Cappellari et al. (2013) [Results: "Following (cite: Ruffa24), we fitted the $M_{\rm BH}$ – $L_{\rm \nu,mm}$ and mmFP data, including the XRBs, using the LTS_LINEFIT and LTS_PLANEFIT routines of (cite: Cappellari2013), respectively."]
  - validation: Spearman rank correlation analysis (rho and p-values) and comparison of best-fitting coefficients and scatters with SMBH-only fits of Ruffa et al. (2024). [Results: "In both cases, the best-fitting coefficients agree well with those derived when fitting only the SMBHs (cite: Ruffa24), and both relations have similar or improved scatters compared to the SMBH-only fits."] [Results: "We also performed Spearman rank analyses to quantify the statistical significance of the correlations, and show the resulting correlation coefficients $\rho$ and $p$-values in the top-left corner of each panel of Figure 1 which are similar or better then the correlation coefficients in (cite: Ruffa24)."]
- result: M_BH - L_nu,mm power-law slope = 0.89 ± 0.04 dimensionless [Results: "\log_{10}\left(\frac{M_{\rm BH}}{\rm M_{\odot}}\right)=(0.89\pm0.04)\left[\log_{10}\left(\frac{L_{\rm \nu,mm}}{\mathrm{erg\,s}^{-1}}\right)-39\right] + (8.26\pm0.08)\,,"]
- result: M_BH - L_nu,mm power-law intercept = 8.26 ± 0.08 dex [Results: "\log_{10}\left(\frac{M_{\rm BH}}{\rm M_{\odot}}\right)=(0.89\pm0.04)\left[\log_{10}\left(\frac{L_{\rm \nu,mm}}{\mathrm{erg\,s}^{-1}}\right)-39\right] + (8.26\pm0.08)\,,"]
- result: M_BH - L_nu,mm observed scatter sigma_obs = 0.49 ± not stated dex [Results: "with an observed scatter ($\sigma_{\rm obs}$) of $0.49$ dex and an estimated intrinsic scatter ($\sigma_{\rm int}$) of $0.44\pm0.15$ dex."]
- result: M_BH - L_nu,mm intrinsic scatter sigma_int = 0.44 ± 0.15 dex [Results: "with an observed scatter ($\sigma_{\rm obs}$) of $0.49$ dex and an estimated intrinsic scatter ($\sigma_{\rm int}$) of $0.44\pm0.15$ dex."]
- result: mmFP L_X,2-10 slope coefficient = -0.22 ± 0.05 dimensionless [Results: "\nonumber \log_{10}\left(\frac{M_{\rm BH}}{\rm M_{\odot}}\right) = (-0.22\pm0.05)\left[\log_{10}\left(\frac{L_{\rm X,2-10}}{\mathrm{erg\,s}^{-1}}\right)-40\right] \\+ (0.97\pm0.05)\left[\log_{10}\left(\frac{L_{\nu,\rm mm}}{\mathrm{erg\,s}^{-1}}\right)-39\right] + (8.32\pm0.08)\,,"]
- result: mmFP L_nu,mm slope coefficient = 0.97 ± 0.05 dimensionless [Results: "\nonumber \log_{10}\left(\frac{M_{\rm BH}}{\rm M_{\odot}}\right) = (-0.22\pm0.05)\left[\log_{10}\left(\frac{L_{\rm X,2-10}}{\mathrm{erg\,s}^{-1}}\right)-40\right] \\+ (0.97\pm0.05)\left[\log_{10}\left(\frac{L_{\nu,\rm mm}}{\mathrm{erg\,s}^{-1}}\right)-39\right] + (8.32\pm0.08)\,,"]
- result: mmFP intercept coefficient = 8.32 ± 0.08 dex [Results: "\nonumber \log_{10}\left(\frac{M_{\rm BH}}{\rm M_{\odot}}\right) = (-0.22\pm0.05)\left[\log_{10}\left(\frac{L_{\rm X,2-10}}{\mathrm{erg\,s}^{-1}}\right)-40\right] \\+ (0.97\pm0.05)\left[\log_{10}\left(\frac{L_{\nu,\rm mm}}{\mathrm{erg\,s}^{-1}}\right)-39\right] + (8.32\pm0.08)\,,"]
- result: mmFP observed scatter sigma_obs = 0.42 ± not stated dex [Results: "with $\sigma_{\rm obs}=0.42$ dex and $\sigma_{\rm int}=0.36\pm0.07$ dex."]
- result: mmFP intrinsic scatter sigma_int = 0.36 ± 0.07 dex [Results: "with $\sigma_{\rm obs}=0.42$ dex and $\sigma_{\rm int}=0.36\pm0.07$ dex."]
- limitation (authors): Scaling archival mm fluxes from 98, 104, and 350 GHz to 230 GHz assuming a flat spectral index (alpha = 0) introduces uncertainties of ~6% to 14%. [Archival Observations: "Archival mm fluxes at frequencies other than $230$ GHz were scaled to that band assuming a flat spectral index ($\alpha=0$). This unavoidably introduces uncertainties in our comparisons."]
- limitation (authors): Non-simultaneous mm and X-ray observations (especially for A0620-00 where Chandra data is from 2013 and F_var = 0.83, and GRS 1915+105 with a 9-month gap) mean temporal variability can significantly impact source positions and increase sca… [Archival Observations: "This data was taken in 2013 meaning that A0620-00 is a source where variability can have an significant impact."]
- limitation (authors): Potential contribution from the donor star wind to the mm emission of Cygnus X-1 is not modeled. [Physical Drivers: "For Cygnus X-1 in the soft state and potentially in the hard state there might be some contribution to the mm emission from the donor star wind. This contribution should be investigated further."]
- not stated (card): Specific CASA versions used for each dataset; TCLEAN weighting scheme (e.g., Briggs robust parameter), cell size, image size, and stopping threshold; Exact method used to measure continuum flux densities (e.g., peak pixel vs Gaussian fit vs aperture integration) and upper limit threshold (e.g., 3-sigma) inherited from Ruffa et al. (2024); Assumed flux scale uncertainty when computing errors on L_…

### 2014A&A...570L..14R: The wonderful complexity of the Mira AB system (2014; evolved_stars; observational_alma_primary)
- question: What is the morphology of the circumstellar CO(3-2) gas around the Mira AB binary, and how has it been shaped by the binary interaction?
- processing.imaging.array_combination: Main array and ACA combined, ACA weighted down by factor 0.3 [2 Observations: "The data were subsequently combined, weighing the ACA data down by a factor of $0.3$ to account for the lower sensitivity of the 7m antennas."]
- step 1: Combine and image data
  - method: Calibrate separately, combine 12m and ACA with ACA weight 0.3, self-calibrate on continuum, subtract continuum, image line [2 Observations: "After applying the self-calibration, final imaging was done after subtracting the continuum, and averaging over 2 channels to $\sim$0.85 km s$^{-1}$ spectral resolution."]
  - software: CASA
  - parameter: ACA weight factor 0.3 [2 Observations: "weighing the ACA data down by a factor of $0.3$"]
  - validation: Tests indicate the exact ACA weight does not affect results [2 Observations: "Tests indicate that the exact weight does not affect our results."]
- limitation (authors): Only ~50% of extended flux recovered even with ACA; dynamic range limited to ~50 [3.2 Circumstellar morphology: "even with the ACA only 50% of the extended flux is recovered."]
- not stated (card): tclean parameters: weighting/robust, deconvolver, cell and image size, masks; CASA version; Line-free channels used for continuum; Self-calibration solution intervals; Flux scale uncertainty; How the uv fit was performed (model, software); How the position-velocity cut was extracted; Spectral setup details beyond window centres

### 2013Natur.499..450B: Suppression of star formation in the galaxy NGC 253 by a starburst-driven molecular wind (2013; nearby_galaxies; observational_alma_primary)
- question: How much molecular gas is carried out by the starburst-driven wind of NGC 253, and what is the mass loading relative to the star formation rate?
- processing.imaging.array_combination: CLEANed ALMA feathered with Mopra; combined cube used as prior for a new CLEAN deconvolution [Supplementary Information: "We then used the combined cube as the prior for a deconvolution of the ALMA observations using CLEAN."]
- step 1: Reduce and image CO(1-0) cube
  - method: Calibrate, self-calibrate, CLEAN, feather with Mopra, re-CLEAN [Supplementary Information: "We reduced the data using the CASA and Miriad software packages."]
  - software: CASA, Miriad
  - parameter: Briggs robust 0.5 [Supplementary Information: "using robust weighing with Briggs parameter 0.5"]
- limitation (authors): Outflow rate is uncertain due to alpha_CO and geometry [main text: "with considerable uncertainty due to α CO and the geometrical corrections."]
- not stated (card): CASA version and calibrators; Mopra map details and feathering parameters; cell size, image size, masks, CLEAN thresholds; self-cal solution intervals; continuum subtraction and line-free channels; method for defining outflow components and measuring LCO, vw, rw; shell radii and velocity measurement procedure

### 2024A&A...689A..41V: XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster (2024; galaxy_clusters_and_sz; observational_alma_primary)
- question: What are the dynamical state and morphology of the ICM of the z=1.98 cluster XLSSC 122, as traced by resolved SZ observations?
- processing.imaging.array_combination: Modeling in uv-plane with each pointing modeled individually, combined at likelihood level; joint ALMA+ACA imaged map for display [3.2 Visibility-based modeling of the ICM: "we model each pointing individually and correct for the primary beam attenuation per field. The fields are combined at the likelihood level"]
- step 2: Single-component ICM forward modeling
  - method: gNFW (theoretical) and A10/M14 template (empirical) pressure models integrated to Compton y, converted to SZ brightness per band, Fourier transformed, sampled at data uv-points with primary beam; Gaussian likelihood on unbinned visibilitie… [3 Methodology: "We then apply the ALMA and ACA transfer function to the model to account for the missing baselines and compute the likelihood of the resulting model on the unbinned visibilities"]
  - software: dynesty
  - parameter: Mostly flat priors; Gaussian priors on calibration and redshift [3.3 Joint likelihood modeling: "we mainly use flat priors except for the calibration and redshift uncertainty parameters which we marginalize over."]
  - parameter: Evidence convergence threshold Δln B = 0.01 [3.3 Joint likelihood modeling: "set to $\Delta\ln\mathcal{B}=0.01$"]
  - assumption: Cosmology Planck2014_XIII, H0=67.7, Om=0.307; non-relativistic SZ (relativistic corrections neglected) [1 Introduction: "$H_0=67.7$ kms$^{-1}$Mpc$^{-1}$ and $\Omega_{\rm m} = 0.307$"]
  - assumption: ACT and ALMA+ACA likelihoods independent [3.3 Joint likelihood modeling: "Hence, we assume no covariance between the ACA+ALMA observations and the ACT maps."]
  - fitting: Static nested sampling with dynesty; significance from Bayes factor against null model [3.2 Visibility-based modeling of the ICM: "The implementation uses the static nested sampling method implemented in the `dynesty` package"]
  - validation: Residual maps in uv plane; Bayes factor comparisons [5.1.1 The theoretical formalism: "The residuals in Figure [1] are obtained by subtracting the model in the visibility plane from the data."]
- step 5: Derive SZ and dynamical masses
  - method: Evidence-weighted average of empirical-formalism masses (ALMA+ACA+ACT); velocity dispersion biweight of 32 members with Munari scaling, converted to M500 with colossus [7 Mass estimates: "Our SZ mass is calculated by taking the evidence-weighted average of the mass estimates from the empirical formalism runs"]
  - software: colossus
  - parameter: A = 1177.0 km/s, alpha = 0.364 [7 Mass estimates: "with $A = 1177.0$ km s$^{-1}$ and $\alpha = 0.364$"]
  - assumption: Local scaling relations of Arnaud2010 used for Y to M500 [7 Mass estimates: "we make use of local scaling relations from (cite: Arnaud2010) to convert $Y_{\rm 500,c}$ to an SZ-derived halo mass"]
  - validation: Compared with X-ray, CARMA, ACT catalog masses [Mass estimates: "We also quote the derived cluster mass of XLSSC 122 as reported in the ACT cluster catalog (cite: Hilton2021)."]
- result: SZ detection significance, ALMA+ACA = ~10.9–11.2 ± not stated sigma [5.1 ALMA+ACA modeling: "we detect the SZ effect at $\sim10.9-11.2\sigma$ in the ACA+ALMA data"]
- result: SZ detection significance, ALMA+ACA+ACT = 15 ± not stated sigma [9 Conclusions: "which increases to $15\sigma$ when ACT observations are included"]
- result: M500,c (SZ) = 1.66e14 ± +0.23/-0.20 e14 Msun [7 Mass estimates: "$M_{500,\mathrm{c}} = 1.66^{+0.23}_{-0.20} \times 10^{14}~\rm M_\odot$"]
- result: Eccentricity (ALMA+ACA+ACT) = 0.46 ± +0.12/-0.16 dimensionless [5.2 ALMA+ACA+ACT joint likelihood model…: "likelihood-weighted average of $e=0.46^{+0.12}_{-0.16}$"]
- result: Velocity dispersion sigma200,c = 1014 ± 169 km/s [7 Mass estimates: "We found a $\sigma_{200,\mathrm{c}} = 1014~\pm169$ km s$^{-1}$"]
- result: log10 M500,c dynamical = 14.69 ± +0.13/-0.18 log Msun [7 Mass estimates: "$\log_{10} M_{500,\mathrm{c}}^{\mathrm{dyn}} = 14.69^{+0.13}_{-0.18}~\rm M_\odot$"]
- result: Y(<r500,c) A10-MD = 2.0e-5 ± +0.6/-0.4 e-5 Mpc^2 [8.3 Time scales: "we find $Y(<r_{500,\mathrm{c}}) = 2.0^{+0.6}_{-0.4} \times 10^{-5}~\textnormal{Mpc}^2$"]
- result: SZ peak offset from BCG/X-ray peak = 10'' (80 kpc) ± 1'' (7 kpc) arcsec [8.1 Morphological implications: "offset from the BCG and the peak of the X-ray emission by $10\ensuremath{''}\pm 1\ensuremath{''}$ ($80\pm7$ kpc)"]
- limitation (authors): Lack of short baselines makes beta–P0 degeneracy and template discrimination weak; gNFW poorly suited for filaments [5.1.2 The empirical formalism: "the lack of short baselines in the ALMA+ACA observations explains why the mass estimates vary between models"]
- not stated (card): Exact ALMA/ACA uv-selection, channel binning and weights used in the visibility fits; dynesty settings (live points, bounding, sampling); Exact ACT DR6 map products, beams, transfer functions and cutout size; Tapering and tclean parameters for display images; How evidence-weighted mass average across models is computed; Y-to-M500 conversion implementation details; Band 4 point-source model detail…

### 2020AJ....159..215L: Disk-integrated Thermal Properties of Ceres Measured at Millimeter Wavelengths (2020; solar_system; observational_alma_primary)
- question: What are the disk-integrated brightness temperature, rotational lightcurve and subsurface thermal/dielectric properties of Ceres at ~1.1 mm, and is HCN present around Ceres?
- step 1: Measure total flux density lightcurves
  - method: Aperture photometry on 12-m images made from 5-15 min data; ACA flux from averaged visibility amplitudes; visibility fitting as cross-check [3.1. Rotational lightcurve: "We used circular apertures with diameters of 0.6” to 0.8” centered on Ceres’s disk to make integrated photometry measurements."]
  - software: CASA
  - validation: Simulated disk observations to check flux recovery; compared Cycle 4 12-m with Cycle 5 ACA lightcurves [3.1. Rotational lightcurve: "Our tests suggested no issues recovering the total flux of Ceres from our data."]
- step 3: Search for HCN and derive upper limit
  - method: Average ACA spectra from Oct 18-20, bin to 300 kHz, model 3-sigma limit with PSG Haser model [3.3. Search for HCN: "finding the production rate that has the flux density at the peak of the J=3-2 emission line comparable to our 3-s noise level of 0.054 Jy."]
  - software: Planetary Spectrum Generator
  - parameter: Trot = 23 K [3.3. Search for HCN: "set the rotational temperature of HCN molecules to _T_ rot = 23 K."]
  - assumption: Globally uniform production, Haser model [3.3. Search for HCN: "The PSG assumes the Haser model (Haser 1957)"]
  - validation: Varying Trot changes limit by factor 2-3 [3.3. Search for HCN: "would change our resulting upper limit production rate by a factor of 2-3."]
- result: Lightcurve peak-to-peak amplitude = 4 ± not stated % [3.1. Rotational lightcurve: "the maximum rotational variation of the observed Ceres flux density is 4% (peak-to-peak)."]
- result: HCN 3-sigma upper limit production rate = 2e24 ± not stated molecules s-1 [3.3. Search for HCN: "We estimate a 3-s upper limit production rate of HCN of 2´10 [24] molecules s [-1]"]
- limitation (authors): Model is extremely simplified; Cycle 3 flux likely not fully recovered [5.1. Lightcurve and longitudinal therma…: "Of course, this is an extremely simplified model."]
- not stated (card): CASA and pipeline versions; tclean parameters (weighting, cell, image size, masks, iterations); self-calibration solution intervals; exact uniform disk model parameters; how flux density was converted to Tb (beam/disk size used); Cycle 3/4/5 pipeline calibrator choices per execution; KRC run parameters (layer grid, time steps); how measured Tb 173 K was matched to model grid; ACA spectral baselin…

## All papers in this technique

- 2013A&A...555A.112P (2013): Global collapse of molecular clouds as a formation mechanism for the most massive stars
- 2013ApJ...774...73I (2013): ALMA Resolves 30 Doradus: Sub-parsec Molecular Cloud Structure near the Closest Super Star Cluster
- 2013ApJ...777...92S (2013): ALMA Observations of the Coldest Place in the Universe: The Boomerang Nebula
- 2013ApJ...779L..22J (2013): A Recent Accretion Burst in the Low-mass Protostar IRAS 15398-3359: ALMA Imaging of Its Related Chemistry
- 2013Natur.499..450B (2013): Suppression of star formation in the galaxy NGC 253 by a starburst-driven molecular wind
- 2014A&A...569L...5M (2014): Revised spectroscopic parameters of SH<SUP>+</SUP> from ALMA and IRAM 30 m observations
- 2014A&A...570L..14R (2014): The wonderful complexity of the Mira AB system
- 2014ApJ...784...62A (2014): Circumstellar Disks around Binary Stars in Taurus
- 2014ApJ...792...68S (2014): ALMA Observations of the T Tauri Binary System AS 205: Evidence for Molecular Winds and/or Binary Interactions
- 2014ApJ...795..152O (2014): A Substellar-mass Protostar and its Outflow of IRAS 15398-3359 Revealed by Subarcsecond-resolution Observations of H<SUB>2</SUB>CO and CCH
- 2014ApJ...795L..25R (2014): Turbulence Sets the Initial Conditions for Star Formation in High-pressure Environments
- 2014ApJ...797...90S (2014): An Infrared-luminous Merger with Two Bipolar Molecular Outflows: ALMA and SMA Observations of NGC 3256
- 2014MNRAS.444.1821F (2014): ALMA and Herschel observations of the prototype dusty and polluted white dwarf G29-38
- 2015A&A...576L...2S (2015): ALMA detection of [C ii] 158 μm emission from a strongly lensed z = 2.013 star-forming galaxy
- 2015ApJ...801...82H (2015): ALMA Imaging of Millimeter/Submillimeter Continuum Emission in Orion KL
- 2015ApJ...802..125R (2015): A Cluster in the Making: ALMA Reveals the Initial Conditions for High-mass Cluster Formation
- 2015ApJ...803...60S (2015): ALMA Multi-line Observations of the IR-bright Merger VV 114
- 2015ApJ...804...37L (2015): ALMA Resolves the Spiraling Accretion Flow in the Luminous OB Cluster-forming Region G33.92+0.11
- 2015ApJ...808..102K (2015): Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA
- 2015ApJ...811..124S (2015): Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies
- 2015ApJ...812..126C (2015): A Compact Concentration of Large Grains in the HD 142527 Protoplanetary Dust Trap
- 2015ApJ...814..143A (2015): The Peculiar Distribution of CH3CN in IRC +10216 Seen by ALMA
- 2015Natur.527...70P (2015): Episodic molecular outflow in the very young protostellar cluster Serpens South
- 2016A&A...586A..70L (2016): Anatomy of a blazar in the (sub-)millimeter: ALMA observations of PKS 0521-365
- 2016A&A...587A..44P (2016): Sub-kpc star formation law in the local luminous infrared galaxy IC 4687 as seen by ALMA
- 2016A&A...587A..91B (2016): Exploring molecular complexity with ALMA (EMoCA): Deuterated complex organic molecules in Sagittarius B2(N2)
- 2016A&A...593A..44L (2016): The 492 GHz emission of Sgr A* constrained by ALMA
- 2016A&A...593A.107L (2016): Linearly polarized millimeter and submillimeter continuum emission of Sgr A* constrained by ALMA
- 2016A&A...594A..70K (2016): Deep ALMA imaging of the merger NGC 1614. Is CO tracing a massive inflow of non-starforming gas?
- 2016A&A...594A..81P (2016): High-velocity extended molecular outflow in the star-formation dominated luminous infrared galaxy ESO 320-G030
- 2016A&A...595A.117J (2016): The ALMA Protostellar Interferometric Line Survey (PILS). First results from an unbiased submillimeter wavelength line survey of the Class …
- 2016ApJ...820L..40A (2016): Ringed Substructure and a Gap at 1 au in the Nearest Protoplanetary Disk
- 2016ApJ...821L...8S (2016): Isotopic Ratios of Carbon and Oxygen in Titan’s CO using ALMA
- 2016ApJ...823L..10W (2016): First Detection of Gas-phase Methanol in a Protoplanetary Disk
- 2016ApJ...826...26T (2016): Revealing a Detailed Mass Distribution of a High-density Core MC27/L1521F in Taurus with ALMA
- 2016ApJ...826..112S (2016): ALMA Imaging and Gravitational Lens Models of South Pole Telescope—Selected Dusty, Star-Forming Galaxies at High Redshifts
- 2016ApJ...826..213L (2016): Angular Momentum Loss in the Envelope-Disk Transition Region of the HH 111 Protostellar System: Evidence for Magnetic Braking?
- 2016ApJ...827..133L (2016): Star Formation and Feedback: A Molecular Outflow-Prestellar Core Interaction in L1689N
- 2016ApJ...829L..10I (2016): Clumpy and Extended Starbursts in the Brightest Unlensed Submillimeter Galaxies
- 2016ApJ...829L..35T (2016): A Gap with a Deficit of Large Grains in the Protoplanetary Disk around TW Hya
- 2016ApJ...831...32N (2016): A Study of the Relation between Star Formation and Molecular Clumps on Subparsec Scales in 30 Doradus
- 2016ApJ...831..101B (2016): Hydrocarbon Emission Rings in Protoplanetary Disks Induced by Dust Evolution
- 2016ApJ...832...37G (2016): ALMA Observations of Lyα Blob 1: Halo Substructure Illuminated from Within
- 2016ApJ...832..142Z (2016): The Molecular Wind in the Nearest Seyfert Galaxy Circinus Revealed by ALMA
- 2016ApJ...832..143F (2016): The Link between Turbulence, Magnetic Fields, Filaments, and Star Formation in the Central Molecular Zone Cloud G0.253+0.016
- 2016ApJ...832..158Z (2016): ALMA Cycle 1 Observations of the HH46/47 Molecular Outflow: Structure, Entrainment, and Core Impact
- 2016ApJ...833..103H (2016): Kiloparsec-scale Dust Disks in High-redshift Luminous Submillimeter Galaxies
- 2016ApJ...833..209O (2016): Dense Core Properties in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA
- 2016ApJ...833..219P (2016): ALMA Observations of Orion Source I at 350 and 660 GHz
- 2016ApJS..222....1F (2016): ALMA Census of Faint 1.2 mm Sources Down to ~ 0.02 mJy: Extragalactic Background Light and Dust-poor, High-z Galaxies
- 2016MNRAS.460.2933M (2016): Exocometary gas in the HD 181327 debris ring
- 2016NatSR...626896A (2016): Kennicutt-Schmidt Law in the Central Region of NGC 4321 as Seen by ALMA
- 2016Natur.535..258C (2016): Imaging the water snow-line during a protostellar outburst
- 2016Natur.537..207G (2016): Compression and ablation of the photo-irradiated molecular cloud the Orion Bar
- 2016PASJ...68...88K (2016): The Sunyaev-Zel'dovich effect at 5″: RX J1347.5-1145 imaged by ALMA
- 2016RAA....16..106H (2016): Morphology and kinematics of the gas envelope of the Mira binary W Aquilae
- 2017A&A...597A..53L (2017): The ALMA-PILS survey: First detections of ethylene oxide, acetone and propanal toward the low-mass protostar IRAS 16293-2422
- 2017A&A...600A.141K (2017): Resolving the fragmentation of high line-mass filaments with ALMA: the integral shaped filament in Orion A
- 2017A&A...601L...9G (2017): Spatially resolved images of reactive ions in the Orion Bar
- 2017A&A...604A.115V (2017): The correct estimate of the probability of false detection of the matched filter in weak-signal detection problems . II. Further results wi…
- 2017A&A...605A..28D (2017): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. I. Large-scale kinematic structure…
- 2017A&A...605A..42C (2017): Extended ionised and clumpy gas in a normal galaxy at z = 7.1 revealed by ALMA
- 2017A&A...605A.116K (2017): Rings and filaments: The remarkable detached CO shell of U Antliae
- 2017A&A...605A.126R (2017): The circumstellar envelope around the S-type AGB star W Aql. Effects of an eccentric binary orbit
- 2017AJ....154..206L (2017): Mapping Vinyl Cyanide and Other Nitriles in Titan's Atmosphere Using ALMA
- 2017ApJ...834....6S (2017): Merger-induced Shocks in the Nearby LIRG VV 114 through Methanol Observations with ALMA
- 2017ApJ...835...98U (2017): ALMA Deep Field in SSA22: Source Catalog and Number Counts
- 2017ApJ...835..108S (2017): Kinematic Structure of Molecular Gas around High-mass YSO, Papillon Nebula, in N159 East in the Large Magellanic Cloud: A New Perspective w…
- 2017ApJ...835..174S (2017): Spatially resolved CO SLED of the Luminous Merger Remnant NGC 1614 with ALMA
- 2017ApJ...835..265W (2017): Dense Molecular Gas Tracers in the Outflow of the Starburst Galaxy NGC 253
- 2017ApJ...835..286I (2017): Extremely Red Submillimeter Galaxies: New z ≳ 4-6 Candidates Discovered using ALMA and Jansky VLA
- 2017ApJ...835L..35M (2017): New ALMA and Fermi/LAT Observations of the Large-scale Jet of PKS 0637-752 Strengthen the Case Against the IC/CMB Model
- 2017ApJ...836L..29J (2017): <SUP>13</SUP>CO/C<SUP>18</SUP>O Gradients across the Disks of Nearby Spiral Galaxies
- 2017ApJ...837...60B (2017): The ALMA View of the OMC1 Explosion in Orion
- 2017ApJ...839..133P (2017): Variation in GMC Association Properties across the Bars, Spiral Arms, Inter-arms, and Circumnuclear Region of M100 (NGC 4321) Extracted fro…
- 2017ApJ...840...82D (2017): Morphological Properties of the Crab Nebula: A Detailed Multiwavelength Study Based on New VLA, HST, Chandra, and XMM-Newton Images
- 2017ApJ...841..110S (2017): The Coldest Place in the Universe: Probing the Ultra-cold Outflow and Dusty Disk in the Boomerang Nebula
- 2017ApJ...841L..20I (2017): ALMA Discovery of Solar Umbral Brightness Enhancement at λ = 3 mm
- 2017ApJ...842...92G (2017): Thermal Feedback in the High-mass Star- and Cluster-forming Region W51
- 2017ApJ...842...94T (2017): ALMA View of the Galactic Center Minispiral: Ionized Gas Flows around Sagittarius A<SUP>∗</SUP>
- 2017ApJ...842L..24A (2017): Very Deep inside the SN 1987A Core Ejecta: Molecular Structures Seen in 3D
- 2017ApJ...843...27L (2017): Formation and Atmosphere of Complex Organic Molecules of the HH 212 Protostellar Disk
- 2017ApJ...843...45K (2017): Mass Transport from the Envelope to the Disk of V346 Nor: A Case Study for the Luminosity Problem in an FUor-type Young Eruptive Star
- 2017ApJ...844...98M (2017): ALMA Observations of N83C in the Early Stage of Star Formation in the Small Magellanic Cloud
- 2017ApJ...845...58Z (2017): ALMA Maps of Dust and Warm Dense Gas Emission in the Starburst Galaxy IC 5179
- 2017ApJ...845..138S (2017): Gas Dynamics of a Luminous z = 6.13 Quasar ULAS J1319+0950 Revealed by ALMA High-resolution Observations
- 2017ApJ...845L...5I (2017): On the Disappearance of a Cold Molecular Torus around the Low-luminosity Active Galactic Nucleus of NGC 1097
- 2017ApJ...845L..19B (2017): A First Comparison of Millimeter Continuum and Mg II Ultraviolet Line Emission from the Solar Chromosphere
- 2017ApJ...849...14S (2017): Resolved Structure of the Arp 220 Nuclei at λ ≈ 3 mm
- 2017ApJ...849...25L (2017): ALMA Reveals Sequential High-mass Star Formation in the G9.62+0.19 Complex
- 2017ApJ...849...68S (2017): Very Large Array Ammonia Observations of the HH 111/HH 121 Protostellar System: A Detection of a New Source with a Peculiar Chemistry
- 2017ApJ...849...90S (2017): Evolution of Molecular Clouds in the Superwind Galaxy NGC 1808 Probed by ALMA Observations
- 2017ApJ...849...95B (2017): Fermi Non-detections of Four X-Ray Jet Sources and Implications for the IC/CMB Mechanism
- 2017ApJ...850...35L (2017): Solar ALMA Observations: Constraining the Chromosphere above Sunspots
- 2017ApJ...850...83F (2017): Demonstrating a New Census of Infrared Galaxies with ALMA (DANCING-ALMA). I. FIR Size and Luminosity Relation at z = 0-6 Revealed with 1034…
- 2017ApJ...850..139W (2017): ALMA Observations of a Quiescent Molecular Cloud in the Large Magellanic Cloud
- 2017ApJ...850L...6A (2017): ALMA Discovery of Dust Belts around Proxima Centauri
- 2017ApJ...851...83C (2017): Protoplanetary Disks in ρ Ophiuchus as Seen from ALMA
- 2017MNRAS.464.1415M (2017): Exocometary gas structure, origin and physical properties around β Pictoris through ALMA CO multitransition observations
- 2017MNRAS.464L..31H (2017): Unveiling the early-stage anatomy of a protocluster hub with ALMA
- 2017MNRAS.465..834Z (2017): The ALMA early science view of FUor/EXor objects - I. Through the looking-glass of V2775 Ori
- 2017MNRAS.466.3519R (2017): The ALMA early science view of FUor/EXor objects - II. The very wide outflow driven by HBC 494
- 2017MNRAS.468.3266R (2017): The ALMA early science view of FUor/EXor objects - III. The slow and wide outflow of V883 Ori
- 2017MNRAS.470.4209Y (2017): ALMA and VLA observations of emission from the environment of Sgr A*
- 2017MNRAS.472.1239B (2017): Tests of star formation metrics in the low-metallicity galaxy NGC 5253 using ALMA observations of H30α line emission
- 2017PASJ...69...83M (2017): ALMA multiline observations toward the central region of NGC 613
- 2017SoPh..292...87S (2017): Observing the Sun with the Atacama Large Millimeter/submillimeter Array (ALMA): High-Resolution Interferometric Imaging
- 2018A&A...609A..67K (2018): The close circumstellar environment of Betelgeuse. V. Rotation velocity and molecular envelope properties from ALMA
- 2018A&A...610A..54P (2018): The ALMA-PILS Survey: Formaldehyde deuteration in warm gas on small scales toward IRAS 16293-2422 B
- 2018A&A...610A..77H (2018): An ALMA study of the Orion Integral Filament. I. Evidence for narrow fibers in a massive cloud
- 2018A&A...611A..99K (2018): The evolution of young HII regions. I. Continuum emission and internal dynamics
- 2018A&A...614A..64B (2018): Magnetic fields at the onset of high-mass star formation
- 2018A&A...615A...9P (2018): Distribution of Serpens South protostars revealed with ALMA
- 2018A&A...616A..34H (2018): An unusual face-on spiral in the wind of the M-type AGB star EP Aquarii
- 2018A&A...617A..23B (2018): Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN
- 2018A&A...617A..89C (2018): Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). I. Indication for a centrifugal barrier in the enviro…
- 2018A&A...617A.120M (2018): Tracing the cold and warm physico-chemical structure of deeply embedded protostars: IRAS 16293-2422 vs. VLA 1623-2417
- 2018A&A...617A.129K (2018): Submillimeter-wave emission of three Galactic red novae: cool molecular outflows produced by stellar mergers
- 2018A&A...618A..35G (2018): High-speed molecular cloudlets around the Galactic center's supermassive black hole
- 2018A&A...618L...5N (2018): Detection of a high-mass prestellar core candidate in W43-MM1
- 2018A&A...619A..40M (2018): The radio jets of SS 433 at millimetre wavelengths
- 2018A&A...619A.161C (2018): Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk
- 2018A&A...619L...6N (2018): First high-resolution look at the quiet Sun with ALMA at 3mm
- 2018A&A...620A..31M (2018): Chasing discs around O-type (proto)stars. ALMA evidence for an SiO disc and disc wind from G17.64+0.16
- 2018AJ....156..270S (2018): The Albedos, Sizes, Colors, and Satellites of Dwarf Planets Compared with Newly Measured Dwarf Planet 2013 FY27
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853..111J (2018): First Results from the Herschel and ALMA Spectroscopic Surveys of the SMC: The Relationship between [C II]-bright Gas and CO-bright Gas at …
- 2018ApJ...853..160C (2018): The Core Mass Function in the Massive Protocluster G286.21+0.17 Revealed by ALMA
- 2018ApJ...853..171G (2018): Distributed Star Formation throughout the Galactic Center Cloud Sgr B2
- 2018ApJ...853L..19S (2018): The Detection of Hot Cores and Complex Organic Molecules in the Large Magellanic Cloud
- 2018ApJ...854...90E (2018): Molecular Gas Properties in M83 from CO PDFs
- 2018ApJ...855...24P (2018): Thermal Jeans Fragmentation within ∼1000 au in OMC-1S
- 2018ApJ...855L...2M (2018): Detection of a Millimeter Flare from Proxima Centauri
- 2018ApJ...856...72O (2018): An Extreme Protocluster of Luminous Dusty Starbursts in the Early Universe
- 2018ApJ...856...97S (2018): Dense Molecular Gas in the Starburst Nucleus of NGC 1808
- 2018ApJ...856..147O (2018): Gravitationally Unstable Condensations Revealed by ALMA in the TUKH122 Prestellar Core in the Orion A Cloud
- 2018ApJ...858...90G (2018): Dense Gas, Dynamical Equilibrium Pressure, and Star Formation in Nearby Star-forming Galaxies
- 2018ApJ...859...86T (2018): ALMA Images of the Host Cloud of the Intermediate-mass Black Hole Candidate CO-0.40-0.22*: No Evidence for Cloud-Black Hole Interaction, bu…
- 2018ApJ...860..119G (2018): A Keplerian Disk around Orion SrCI, a ∼ 15 M <SUB>☉</SUB> YSO
- 2018ApJ...860..172S (2018): Cloud-scale Molecular Gas Properties in 15 Nearby Galaxies
- 2018ApJ...860L..14K (2018): Discovery of a Molecular Collision Front in Interacting Galaxies NGC 4567/4568 with ALMA
- 2018ApJ...861...14C (2018): Infall Signatures in a Prestellar Core Embedded in the High-mass 70 μm Dark IRDC G331.372-00.116
- 2018ApJ...862....8T (2018): Warm CO Gas Generated by Possible Turbulent Shocks in a Low-mass Star-forming Dense Core in Taurus
- 2018ApJ...863...56C (2018): Resolving the ISM at the Peak of Cosmic Star Formation with ALMA: The Distribution of CO and Dust Continuum in z ∼ 2.5 Submillimeter Galaxi…
- 2018ApJ...863..143C (2018): ALMA [C I]<SUP>3</SUP> P <SUB>1</SUB>-<SUP>3</SUP> P <SUB>0</SUB> Observations of NGC 6240: A Puzzling Molecular Outflow, and the Role of O…
- 2018ApJ...864...81O (2018): Two Different Grain Size Distributions within the Protoplanetary Disk around HD 142527 Revealed by ALMA Polarization Observation
- 2018ApJ...864..120M (2018): ALMA Observations toward the Starburst Dwarf Galaxy NGC 5253. I. Molecular Cloud Properties and Scaling Relations
- 2018ApJ...864L...1G (2018): Violent Quenching: Molecular Gas Blown to 1000 km s<SUP>-1</SUP> during a Major Merger
- 2018ApJ...865..106C (2018): A Submillimeter Perspective on the GOODS Fields (SUPER GOODS). III. A Large Sample of ALMA Sources in the GOODS-S
- 2018ApJ...865..131L (2018): High-resolution ALMA Study of the Proto-brown-dwarf Candidate L328-IRS
- 2018ApJ...866..141K (2018): Extremely Dense Cores Associated with Chandra Sources in Ophiuchus A: Forming Brown Dwarfs Unveiled?
- 2018ApJ...867..111Z (2018): Spatially Resolved <SUP>12</SUP>CO(2-1)/<SUP>12</SUP>CO(1-0) in the Starburst Galaxy NGC 253: Assessing Optical Depth to Constrain the Mole…
- 2018ApJ...867..166S (2018): Internal Structures of Molecular Clouds in the LMC Revealed by ALMA
- 2018ApJ...868...95M (2018): ALMA Observations of HCN and HCO<SUP>+</SUP> Outflows in the Merging Galaxy NGC 3256
- 2018ApJ...868L...3M (2018): ALMA Reveals a Misaligned Inner Gas Disk inside the Large Cavity of a Transitional Disk
- 2018ApJ...868L...5K (2018): A Spatially Resolved au-scale Inner Disk around DM Tau
- 2018ApJ...868L..38G (2018): Do Spectroscopic Dense Gas Fractions Track Molecular Cloud Surface Densities?
- 2018ApJ...869..126L (2018): Forming Super Star Clusters in the Central Starburst of NGC 253
- 2018ApJ...869L..41A (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). I. Motivation, Sample, Calibration, and Overview
- 2018MNRAS.475..448T (2018): Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study
- 2018MNRAS.475..492K (2018): ALMACAL - III. A combined ALMA and MUSE survey for neutral, molecular, and ionized gas in an H I-absorption-selected system
- 2018MNRAS.476.5417S (2018): Unveiling the inner morphology and gas kinematics of NGC 5135 with ALMA
- 2018MNRAS.479.5423M (2018): A gap in the planetesimal disc around HD 107146 and asymmetric warm dust emission revealed by ALMA
- 2018MNRAS.480.4974H (2018): On the multiplicity of ALMA Compact Array counterparts of far-infrared bright quasars
- 2018MNRAS.480.4991G (2018): ALMA imaging of the nascent planetary nebula IRAS 15103-5754
- 2018MNRAS.481.4931E (2018): ALMA reveals the aftermath of a white dwarf-brown dwarf merger in CK Vulpeculae
- 2018NatAs...2..478M (2018): The unexpectedly large proportion of high-mass star-forming cores in a Galactic mini-starburst
- 2018PASJ...70...73H (2018): ALMA <SUP>12</SUP>CO (J = 1-0) imaging of the nearby galaxy M 83: Variations in the efficiency of star formation in giant molecular clouds
- 2018PASJ...70...85T (2018): ALMA view of the circumnuclear disk of the Galactic Center: tidally disrupted molecular clouds falling to the Galactic Center
- 2018PASJ...70L...1M (2018): ALMA [C I] observations toward the central region of Seyfert galaxy NGC 613
- 2019A&A...621A..50B (2019): ALMA observations of the "fresh" carbon-rich AGB star TX Piscium. The discovery of an elliptical detached shell
- 2019A&A...623A..79C (2019): ALMA observations of molecular tori around massive black holes
- 2019A&A...623A..96Y (2019): Signs of outflow feedback from a nearby young stellar object on the protostellar envelope around HL Tauri
- 2019A&A...623A.153O (2019): HD 101584: circumstellar characteristics and evolutionary status
- 2019A&A...625A.118K (2019): Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA
- 2019A&A...626A..93V (2019): The ALMA-PILS survey: gas dynamics in IRAS 16293-2422 and the connection between its two protostars
- 2019A&A...627A...6S (2019): Physical conditions in Centaurus A's northern filaments. I. APEX mid-J CO observations of CO-bright regions
- 2019A&A...627A.114K (2019): Massive dust clumps in the envelope of the red supergiant VY Canis Majoris
- 2019A&A...628A.100D (2019): An ALMA+ACA measurement of the shock in the Bullet Cluster
- 2019A&A...629A..29J (2019): Organic chemistry in the innermost, infalling envelope of the Class 0 protostar L483
- 2019A&A...629A..30F (2019): Complex molecular gas kinematics in the inner 5 kpc of 4C12.50 as seen by ALMA
- 2019A&A...629A.104G (2019): Sunyaev-Zel'dovich detection of the galaxy cluster Cl J1449+0856 at z = 1.99: The pressure profile in uv space
- 2019A&A...631A..64B (2019): Kinematics around the B335 protostar down to au scales
- 2019A&A...632A..33A (2019): ALMA captures feeding and feedback from the active galactic nucleus in NGC 613
- 2019A&A...632A..57C (2019): Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II. Complex organic molecules and heavy water in shoc…
- 2019A&A...632A..83S (2019): Probing fragmentation and velocity sub-structure in the massive NGC 6334 filament with ALMA
- 2019A&A...632A.101T (2019): Chemical and kinematic structure of extremely high-velocity molecular jets in the Serpens Main star-forming region
- 2019A&A...632A.106L (2019): Physical conditions in the gas phases of the giant H II region LMC-N 11. II. Origin of [C II] and fraction of CO-dark gas
- 2019AJ....157..135M (2019): Kuiper Belt-like Hot and Cold Populations of Planetesimal Inclinations in the β Pictoris Belt Revealed by ALMA
- 2019AJ....157..251T (2019): Neptune's Latitudinal Variations as Viewed with ALMA
- 2019AJ....158...15P (2019): Dust Unveils the Formation of a Mini-Neptune Planet in a Protoplanetary Ring
- 2019AJ....158..162F (2019): From Scattered-light to Millimeter Emission: A Comprehensive View of the Gigayear-old System of HD 202628 and its Eccentric Debris Ring
- 2019ApJ...870...39V (2019): ALMA Observations of the Molecular Gas in the Elliptical Galaxy NGC 3557
- 2019ApJ...870...81T (2019): The Formation Conditions of the Wide Binary Class 0 Protostars within BHR 71
- 2019ApJ...871...37H (2019): Molecular and Ionized Gas Phases of an AGN-driven Outflow in a Typical Massive Galaxy at z ≈ 2
- 2019ApJ...871..100H (2019): ALMA Observations of the Protostellar Disk around the VeLLO IRAS 16253-2429
- 2019ApJ...871..112X (2019): ALMA Observations of the Spatial Distribution of Three C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> Isomers toward Sgr B2(N)
- 2019ApJ...871..170M (2019): Fire in the Heart: A Characterization of the High Kinetic Temperatures and Heating Sources in the Nucleus of NGC 253
- 2019ApJ...871..185L (2019): Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA
- 2019ApJ...871..221M (2019): A Very Compact Extremely High Velocity Flow toward MMS 5/OMC-3 Revealed with ALMA
- 2019ApJ...872...70T (2019): ALMA High Angular Resolution Polarization Study: An Extremely Young Class 0 Source, OMC-3/MMS 6
- 2019ApJ...872..121U (2019): Molecular Cloud Cores in the Galactic Center 50 km s<SUP>-1</SUP> Molecular Cloud
- 2019ApJ...873...73Z (2019): An Ordered Envelope-Disk Transition in the Massive Protostellar Source G339.88-1.26
- 2019ApJ...874...89C (2019): The Central 1000 au of a Pre-stellar Core Revealed with ALMA. I. 1.3 mm Continuum Observations
- 2019ApJ...874..104K (2019): Widespread Molecular Outflows in the Infrared Dark Cloud G28.37+0.07: Indications of Orthogonal Outflow-filament Alignment
- 2019ApJ...875...24C (2019): Filamentary Accretion Flows in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA
- 2019ApJ...875...62Y (2019): ALMA Observations of Layered Structures due to CO Selective Dissociation in the ρ Ophiuchi A Plane-parallel PDR
- 2019ApJ...875...96N (2019): Dust Continuum Emission and the Upper Limit Fluxes of Submillimeter Water Lines of the Protoplanetary Disk around HD 163296 Observed by ALMA
- 2019ApJ...876..130H (2019): ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies
- 2019ApJ...879...25K (2019): Highly Ordered and Pinched Magnetic Fields in the Class 0 Protobinary System L1448 IRS 2
- 2019ApJ...880..157D (2019): ALMA and HST Kiloparsec-scale Imaging of a Quasar-galaxy Merger at Z ≈ 6.2
- 2019ApJ...881...43K (2019): The Molecular Outflow in NGC 253 at a Resolution of Two Parsecs
- 2019ApJ...881...84S (2019): The REASONS Survey: Resolved Millimeter Observations of a Large Debris Disk around the Nearby F Star HD 170773
- 2019ApJ...881...99M (2019): Solar Chromospheric Temperature Diagnostics: A Joint ALMA-Hα Analysis
- 2019ApJ...881..159M (2019): Characterization of Ring Substructures in the Protoplanetary Disk of HD 169142 from Multiwavelength Atacama Large Millimeter/submillimeter …
- 2019ApJ...881L..42C (2019): Interstellar Plunging Waves: ALMA Resolves the Physical Structure of Nonstationary MHD Shocks
- 2019ApJ...882...10N (2019): Resolved [C II] Emission from z &gt; 6 Quasar Host-Companion Galaxy Pairs
- 2019ApJ...882..168P (2019): Low Star Formation Efficiency in Typical Galaxies at z = 5-6
- 2019ApJ...882L...4C (2019): Resolved ALMA Continuum Image of the Circumbinary Ring and Circumstellar Disks in the L1551 IRS 5 System
- 2019ApJ...883...98Z (2019): Systematic Variations of CO Gas Abundance with Radius in Gas-rich Protoplanetary Disks
- 2019ApJ...883..145J (2019): ALMA Unveils Widespread Molecular Gas Clumps in the Ram Pressure Stripped Tail of the Norma Jellyfish Galaxy
- 2019ApJ...884..146T (2019): An ALMA Study of the FU Ori-type Object V900 Mon: Implications for the Progenitor
- 2019ApJ...885...50W (2019): Relations between Molecular Cloud Structure Sizes and Line Widths in the Large Magellanic Cloud
- 2019ApJ...885...82L (2019): Sulfur-bearing Molecules in Orion KL
- 2019ApJ...885..106L (2019): Characterizing Magnetic Field Morphologies in Three Serpens Protostellar Cores with ALMA
- 2019ApJ...885L..20H (2019): The Nuclear Filaments inside the Circumnuclear Disk in the Central 0.5 pc of the Galactic Center
- 2019ApJ...886...36S (2019): ALMA Observations of Fragmentation, Substructure, and Protostars in High-mass Starless Clump Candidates
- 2019ApJ...886..102S (2019): The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). I. Pilot Survey: Clump Fragmentation
- 2019ApJ...886L...4Z (2019): Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05
- 2019ApJ...887...24T (2019): Resolving the Interstellar Medium in Ultraluminous Infrared QSO Hosts with ALMA
- 2019ApJ...887...40W (2019): Resolving the Interstellar Medium in the Nuclear Region of Two z = 5.78 Quasar Host Galaxies with ALMA
- 2019ApJ...887...49S (2019): The Gas-Star Formation Cycle in Nearby Star-forming Galaxies. I. Assessment of Multi-scale Variations
- 2019ApJ...887...88E (2019): Star Formation Efficiencies at Giant Molecular Cloud Scales in the Molecular Disk of the Elliptical Galaxy NGC 5128 (Centaurus A)
- 2019ApJ...887..143S (2019): ALMA Observations of Atomic Carbon [C I] ( <SUP> 3 </SUP> P <SUB> 1 </SUB> → <SUP> 3 </SUP> P <SUB> 0 </SUB>) and Low-J CO Lines in the Sta…
- 2019ApJS..244...40L (2019): Automated Mining of the ALMA Archive in the COSMOS Field (A<SUP>3</SUP>COSMOS). I. Robust ALMA Continuum Photometry Catalogs and Stellar Ma…
- 2019MNRAS.482..698C (2019): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution
- 2019MNRAS.482.3135B (2019): The relationship between dust and [C I] at z = 1 and beyond
- 2019MNRAS.482L..29D (2019): Submillimetre dust polarization and opacity in the HD163296 protoplanetary ring system
- 2019MNRAS.484.1257M (2019): A gap in HD 92945's broad planetesimal disc revealed by ALMA
- 2019MNRAS.484.1865H (2019): The morpho-kinematics of the circumstellar envelope around the AGB star EP Aqr
- 2019MNRAS.485.2457H (2019): `The Brick' is not a brick: a comprehensive study of the structure and dynamics of the central molecular zone cloud G0.253+0.016
- 2019MNRAS.485.4359S (2019): WISDOM project - IV. A molecular gas dynamical measurement of the supermassive black hole mass in NGC 524
- 2019MNRAS.486..283B (2019): Young massive star cluster formation in the Galactic Centre is driven by global gravitational collapse of high-mass molecular clouds
- 2019MNRAS.486.5552B (2019): Sub-millimetre non-contaminated detection of the disc around TWA 7 by ALMA
- 2019MNRAS.487.4037D (2019): A joint ALMA-Bolocam-Planck SZ study of the pressure distribution in RX J1347.5-1145
- 2019MNRAS.487.4856M (2019): The kiloparsec-scale gas kinematics in two star-forming galaxies at z ∼ 1.47 seen with ALMA and VLT-SINFONI
- 2019MNRAS.488.1005P (2019): Upper limits on protolunar disc masses using ALMA observations of directly imaged exoplanets
- 2019NatAs...3..517Z (2019): Dynamics of a massive binary at birth
- 2019Natur.569..519K (2019): Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback
- 2019PASJ...71...44H (2019): Formation of high-mass stars in an isolated environment in the Large Magellanic Cloud
- 2019PASJ...71...71H (2019): Big Three Dragons: A z = 7.15 Lyman-break galaxy detected in [O III] 88 μm, [C II] 158 μm, and dust continuum with ALMA
- 2019PASJ...71...73T (2019): A centrally concentrated sub-solar-mass starless core in the Taurus L1495 filamentary complex
- 2019PASJ...71...85M (2019): Complex distribution and velocity field of molecular gas in NGC 1316 as revealed by the Morita Array of ALMA
- 2019PASJ...71..128T (2019): G-0.02-0.07, the compact H II region complex nearest to the galactic center with ALMA
- 2020A&A...633A..13D (2020): The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. II. The spiral-outflow observed at…
- 2020A&A...633A..68D (2020): GRB 190114C in the nuclear region of an interacting galaxy. A detailed host analysis using ALMA, the HST, and the VLT
- 2020A&A...634A..56D (2020): The multi-thermal chromosphere. Inversions of ALMA and IRIS data
- 2020A&A...634A.121H (2020): The headlight cloud in NGC 628: An extreme giant molecular cloud in a typical galaxy disk
- 2020A&A...634L..12D (2020): ALMA reveals a large structured disk and nested rotating outflows in DG Tauri B
- 2020A&A...635A...2S (2020): Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA
- 2020A&A...635A..71W (2020): The Sun at millimeter wavelengths. I. Introduction to ALMA Band 3 observations
- 2020A&A...636A..38N (2020): Episodic accretion constrained by a rich cluster of outflows
- 2020A&A...638A..70D (2020): The Massive and Distant Clusters of WISE Survey. SZ effect of Verification with the Atacama Compact Array - Localization and Cluster Analys…
- 2020A&A...640A..57A (2020): Modeling the quiet Sun cell and network emission with ALMA
- 2020A&A...640A.133R (2020): DEATHSTAR: Nearby AGB stars with the Atacama Compact Array. I. CO envelope sizes and asymmetries: A new hope for accurate mass-loss-rate es…
- 2020A&A...641A..97V (2020): ALMA resolves molecular clouds in metal-poor Magellanic Bridge A
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A..93H (2020): A detailed view on the circumstellar environment of the M-type AGB star EP Aquarii. I. High-resolution ALMA and SPHERE observations
- 2020A&A...642A.164V (2020): Observations of edge-on protoplanetary disks with ALMA. I. Results from continuum data
- 2020A&A...644A..59K (2020): Molecular remnant of Nova 1670 (CK Vulpeculae). I. Properties and enigmatic origin of the gas
- 2020A&A...644A..61H (2020): ATOMIUM: A high-resolution view on the highly asymmetric wind of the AGB star π<SUP>1</SUP>Gruis. I. First detection of a new companion and…
- 2020A&A...644A.152E (2020): The Sun at millimeter wavelengths. II. Small-scale dynamic events in ALMA Band 3
- 2020AJ....159..171F (2020): A Ringed Pole-on Outflow from DO Tauri Revealed by ALMA
- 2020AJ....159..180K (2020): Outflow from Outer-arm Starburst in a Grazing Collision between Galaxies
- 2020AJ....159..215L (2020): Disk-integrated Thermal Properties of Ceres Measured at Millimeter Wavelengths
- 2020ApJ...888...56I (2020): Structural and Dynamical Analysis of 0.1 pc Cores and Filaments in the 30 Doradus-10 Giant Molecular Cloud
- 2020ApJ...888L..28S (2020): Estimating the Temperature and Density of a Spicule from 100 GHz Data Obtained with ALMA
- 2020ApJ...889....9M (2020): GASP. XXII. The Molecular Gas Content of the JW100 Jellyfish Galaxy at z ∼ 0.05: Does Ram Pressure Promote Molecular Gas Formation?
- 2020ApJ...889..141T (2020): A Noncorotating Gas Component in an Extreme Starburst at z = 4.3
- 2020ApJ...889L..24P (2020): Long Baseline Observations of the HD 100546 Protoplanetary Disk with ALMA
- 2020ApJ...890...76N (2020): ALMA Observations of Two Massive and Dense MALT90 Clumps
- 2020ApJ...890..149T (2020): The Molecular Gas in the NGC 6240 Merging Galaxy System at the Highest Spatial Resolution
- 2020ApJ...890..167T (2020): The Fifth Candidate for an Intermediate-mass Black Hole in the Galactic Center
- 2020ApJ...890L..10K (2020): Systematic Variations of CO J = 2-1/1-0 Ratio and Their Implications in The Nearby Barred Spiral Galaxy M83
- 2020ApJ...891..113R (2020): Effect of Feedback of Massive Stars in the Fragmentation, Distribution, and Kinematics of the Gas in Two Star-forming Regions in the Carina…
- 2020ApJ...892...68N (2020): The MBHBM<SUB>⋆</SUB> Project. I. Measurement of the Central Black Hole Mass in Spiral Galaxy NGC 3504 Using Molecular Gas Kinematics
- 2020ApJ...892..111F (2020): Dust-depleted Inner Disks in a Large Sample of Transition Disks through Long-baseline ALMA Observations
- 2020ApJ...892..147S (2020): Oversized Gas Clumps in an Extremely Metal-poor Molecular Cloud Revealed by ALMA's Parsec-scale Maps
- 2020ApJ...892L..18I (2020): ALMA 50-parsec-resolution Imaging of Jet-ISM Interaction in the Lensed Quasar MG J0414+0534
- 2020ApJ...893...13M (2020): Confirmation of Enhanced Long-wavelength Dust Emission in OMC 2/3
- 2020ApJ...893...63T (2020): Physical Conditions and Kinematics of the Filamentary Structure in Orion Molecular Cloud 1
- 2020ApJ...893..101L (2020): An Unbiased ALMA Spectral Survey of the LkCa 15 and MWC 480 Protoplanetary Disks
- 2020ApJ...893..135M (2020): Mass Functions of Giant Molecular Clouds and Young Star Clusters in Six Nearby Galaxies
- 2020ApJ...894...23H (2020): Determining the Physical Conditions of an Extremely Young Class 0 Circumbinary Disk around VLA 1623A
- 2020ApJ...894...72S (2020): Atacama Compact Array Measurements of the Molecular Mass in the NGC 5044 Cooling-flow Group
- 2020ApJ...894...87C (2020): Gas Kinematics of the Massive Protocluster G286.21+0.17 Revealed by ALMA
- 2020ApJ...894L..20X (2020): Independent Core Rotation in Massive Filaments in Orion
- 2020ApJ...895...73K (2020): A Massive Molecular Torus inside a Gas-poor Circumnuclear Disk in the Radio Galaxy NGC 1052 Discovered with ALMA
- 2020ApJ...895..101H (2020): Efficient Methanol Production on the Dark Side of a Prestellar Core
- 2020ApJ...895..109F (2020): Measuring Turbulent Motion in Planet-forming Disks with ALMA: A Detection around DM Tau and Nondetections around MWC 480 and V4046 Sgr
- 2020ApJ...895..119T (2020): ALMA ACA and Nobeyama Observations of Two Orion Cores in Deuterated Molecular Lines
- 2020ApJ...896...35J (2020): A Detailed View of the Circumstellar Environment and Disk of the Forming O-star AFGL 4176
- 2020ApJ...896...36T (2020): ALMA Observations of Giant Molecular Clouds in M33. I. Resolving Star Formation Activities in the Giant Molecular Filaments Possibly Formed…
- 2020ApJ...897..122L (2020): PHANGS CO Kinematics: Disk Orientations and Rotation Curves at 150 pc Resolution
- 2020ApJ...898...75I (2020): ALMA Observations of Multiple CO and C Lines toward the Active Galactic Nucleus of NGC 7469: An X-Ray-dominated Region Caught in the Act
- 2020ApJ...898..146M (2020): Dust Populations in the Iconic Vega Planetary System Resolved by ALMA
- 2020ApJ...899...10T (2020): FRagmentation and Evolution of Dense Cores Judged by ALMA (FREJA). I. Overview: Inner ∼1000 au Structures of Prestellar/Protostellar Cores …
- 2020ApJ...899...37K (2020): A Comparison of the Stellar, CO, and Dust-continuum Emission from Three Star-forming HUDF Galaxies at z ∼ 2
- 2020ApJ...899L..10F (2020): A Low-velocity Bipolar Outflow from a Deeply Embedded Object in Taurus Revealed by the Atacama Compact Array
- 2020ApJ...901..151S (2020): Molecular Gas Outflow in the Starburst Galaxy NGC 1482
- 2020ApJ...901L...8S (2020): Molecular Gas Properties on Cloud Scales across the Local Star-forming Galaxy Population
- 2020ApJ...902...53S (2020): ALMA CO Observations of Gamma-Ray Supernova Remnant N132D in the Large Magellanic Cloud: Possible Evidence for Shocked Molecular Clouds Ill…
- 2020ApJ...902...99I (2020): ALMA 0"02 Resolution Observations Reveal HCN-abundance-enhanced Counter-rotating and Outflowing Dense Molecular Gas at the NGC 1068 Nucleus
- 2020ApJ...902L..33G (2020): A Tale of Two Transition Disks: ALMA Long-baseline Observations of ISO-Oph 2 Reveal Two Closely Packed Nonaxisymmetric Rings and a ∼2 au Ca…
- 2020ApJ...903...94M (2020): ALMA Observations of Giant Molecular Clouds in M33. II. Triggered High-mass Star Formation by Multiple Gas Colliding Events at the NGC 604 …
- 2020ApJ...903..119L (2020): The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). II. Molecular Outflows in the Extreme Early Stages of Protocluster …
- 2020ApJ...904..131N (2020): No Evidence for [C II] Halos or High-velocity Outflows in z ≳ 6 Quasar Host Galaxies
- 2020ApJ...904L..24S (2020): ALMA CO Observations of the Gamma-Ray Supernova Remnant RX J1713.7-3946: Discovery of Shocked Molecular Cloudlets and Filaments at 0.01 pc …
- 2020ApJ...905...85S (2020): Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc …
- 2020ApJ...905...89Y (2020): Kinematical Signs of Dust Trapping and Feedback in a Local Pressure Bump in the Protoplanetary Disk around HD 142527 Revealed with ALMA
- 2020ApJ...905..122H (2020): Physical Conditions of Gas Components in Debris Disks of 49 Ceti and HD 21997
- 2020ApJS..251...14H (2020): CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone
- 2020MNRAS.491..178K (2020): Carina's pillars of destruction: the view from ALMA
- 2020MNRAS.492.6067M (2020): Searching for a dusty cometary belt around TRAPPIST-1 with ALMA
- 2020MNRAS.493.2872C (2020): The lifecycle of molecular clouds in nearby star-forming disc galaxies
- 2020MNRAS.493.5045M (2020): Properties of giant molecular clouds in the strongly barred galaxy NGC 1300
- 2020MNRAS.494.2131F (2020): Fast cloud-cloud collisions in a strongly barred galaxy: suppression of massive star formation
- 2020MNRAS.494.4090C (2020): The [C II]/[N II] ratio in 3 &lt; z &lt; 6 sub-millimetre galaxies from the South Pole Telescope survey
- 2020MNRAS.495.3124H (2020): Megaparsec-scale structure around the protocluster core SPT2349-56 at z = 4.3
- 2020MNRAS.495.3409S (2020): An ALMA survey of the brightest sub-millimetre sources in the SCUBA-2-COSMOS field
- 2020MNRAS.495.3840M (2020): A large amount of diffuse molecular gases in the bar of the strongly barred galaxy NGC 1300: cause of the low star formation efficiency
- 2020MNRAS.495.4297S (2020): ALMA reveals the coherence of the magnetic field geometry in OH 231.8+4.2
- 2020MNRAS.496..394R (2020): Illuminating a tadpole's metamorphosis II: observing the ongoing transformation with ALMA
- 2020MNRAS.496.1834L (2020): Atacama Compact Array observations of the pulsar-wind nebula of SNR 0540-69.3
- 2020MNRAS.496.2790L (2020): ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions - I. Survey description and a first look at G9.62+0.19
- 2020MNRAS.496.4061D (2020): Revealing the intermediate-mass black hole at the heart of the dwarf galaxy NGC 404 with sub-parsec resolution ALMA observations
- 2020MNRAS.496L..38D (2020): Weak CS emission in an extremely metal-poor galaxy DDO 70
- 2020MNRAS.497.3504T (2020): Jet-ISM interactions near the microquasars GRS 1758-258 and 1E 1740.7-2942
- 2020MNRAS.499.5136C (2020): Missing [C II] emission from early galaxies
- 2020NatAs...4..142L (2020): Spiral structures in an embedded protostellar disk driven by envelope accretion
- 2020PASJ...72...33K (2020): Deeply cooled core of the Phoenix galaxy cluster imaged by ALMA with the Sunyaev-Zel'dovich effect
- 2020PASJ...72...69Y (2020): ALMA twenty-six arcmin<SUP>2</SUP> survey of GOODS-S at one millimeter (ASAGAO): Millimeter properties of stellar mass selected galaxies
- 2021A&A...645A..49G (2021): A proto-pseudobulge in ESO 320-G030 fed by a massive molecular inflow driven by a nuclear bar
- 2021A&A...645A..97Q (2021): ALMA resolves giant molecular clouds in a tidal dwarf galaxy
- 2021A&A...645A.142A (2021): Continuity of accretion from clumps to Class 0 high-mass protostars in SDC335
- 2021A&A...646A..25Z (2021): H II regions and high-mass starless clump candidates. II. Fragmentation and induced star formation at 0.025 pc scale: an ALMA continuum stu…
- 2021A&A...646A..26B (2021): A puzzling non-detection of [O III] and [C II] from a z ≈ 7.7 galaxy observed with ALMA
- 2021A&A...646A..72H (2021): Resolved molecular line observations reveal an inherited molecular layer in the young disk around TMC1A
- 2021A&A...647A..10G (2021): Bottlenecks to interstellar sulfur chemistry. Sulfur-bearing hydrides in UV-illuminated gas and grains
- 2021A&A...648A..33M (2021): Characterizing the dust content of disk substructures in TW Hydrae
- 2021A&A...648A..41V (2021): Outflows, envelopes, and disks as evolutionary indicators in Lupus young stellar objects
- 2021A&A...649A.122P (2021): A bright inner disk and structures in the transition disk around the very low-mass star CIDA 1
- 2021A&A...650A.117N (2021): The host galaxy of the short GRB 050709
- 2021A&A...650A.134P (2021): Star formation scaling relations at ∼100 pc from PHANGS: Impact of completeness and spatial scale
- 2021A&A...650A.153D (2021): Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger a…
- 2021A&A...650A.202R (2021): Identification of pre-stellar cores in high-mass star forming clumps via H<SUB>2</SUB>D<SUP>+</SUP> observations with ALMA
- 2021A&A...651A..35O (2021): Heavy-element Rydberg transition line emission from the post-giant-evolution star HD 101584
- 2021A&A...652A..92N (2021): ALMA observations of the variability of the quiet Sun at millimeter wavelengths
- 2021A&A...652A..98G (2021): The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies
- 2021A&A...653A..53A (2021): DEATHSTAR: nearby AGB stars with the Atacama Compact Array. II. CO envelope sizes and asymmetries: the S-type stars
- 2021A&A...653A.166C (2021): Structured velocity field in the inner envelope of B335: ALMA observations of rare CO isotopologues
- 2021A&A...654A..18V (2021): Maser emission from the CO envelope of the asymptotic giant branch star W Hydrae
- 2021A&A...654L...8C (2021): SUPER. VI. A giant molecular halo around a z∼2 quasar
- 2021A&A...655A..42S (2021): Molecular gas budget and characterization of intermediate-mass star-forming galaxies at z ≈ 2-3
- 2021A&A...655A..80D (2021): ATOMIUM: halide molecules around the S-type AGB star W Aquilae
- 2021A&A...656A..46M (2021): ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array
- 2021A&A...656A..60A (2021): Black hole feeding and star formation in NGC 1808
- 2021A&A...656A.133Q (2021): Stellar structures, molecular gas, and star formation across the PHANGS sample of nearby galaxies
- 2021A&A...656A.150P (2021): Constraining the properties of the potential embedded planets in the disk around HD 100546
- 2021AJ....161..185W (2021): Applying the Tremaine-Weinberg Method to Nearby Galaxies: Stellar-mass-based Pattern Speeds and Comparisons with ISM Kinematics
- 2021AJ....161..271F (2021): A Detailed Characterization of HR 8799's Debris Disk with ALMA in Band 7
- 2021ApJ...906..111T (2021): The TW Hya Rosetta Stone Project. II. Spatially Resolved Emission of Formaldehyde Hints at Low-temperature Gas-phase Formation
- 2021ApJ...907...62R (2021): Rise of the Titans: Gas Excitation and Feedback in a Binary Hyperluminous Dusty Starburst Galaxy at z ∼ 6
- 2021ApJ...907L..15S (2021): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Detection of Extremely High-density Compact Structure of Prestellar Cores and M…
- 2021ApJ...908....8C (2021): The TW Hya Rosetta Stone Project. III. Resolving the Gaseous Thermal Profile of the Disk
- 2021ApJ...908...92H (2021): Rotating Filament in Orion B: Do Cores Inherit Their Angular Momentum from Their Parent Filament?
- 2021ApJ...908..231M (2021): Compact Molecular Gas Distribution in Quasar Host Galaxies
- 2021ApJ...909...11J (2021): 25 au Angular Resolution Observations of HH 211 with ALMA: Jet Properties and Shock Structures in SiO, CO, and SO
- 2021ApJ...909..130R (2021): Ultrafaint [C II] Emission in a Redshift = 2 Gravitationally Lensed Metal-poor Dwarf Galaxy
- 2021ApJ...910...11O (2021): FAUST. II. Discovery of a Secondary Outflow in IRAS 15398-3359: Variability in Outflow Direction during the Earliest Stage of Star Formatio…
- 2021ApJ...910...89B (2021): The Physical Drivers of the Luminosity-weighted Dust Temperatures in High-redshift Galaxies
- 2021ApJ...910..148M (2021): Revealing a Centrally Condensed Structure in OMC-3/MMS 3 with ALMA High-resolution Observations
- 2021ApJS..257....6G (2021): Molecules with ALMA at Planet-forming Scales (MAPS). VI. Distribution of the Small Organics HCN, C<SUB>2</SUB>H, and H<SUB>2</SUB>CO
- 2021ApJS..257...43L (2021): PHANGS-ALMA: Arcsecond CO(2-1) Imaging of Nearby Star-forming Galaxies
- 2021MNRAS.500.5500B (2021): A warm molecular ring in AG Car: composing the mass-loss puzzle
- 2021MNRAS.501.2934C (2021): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - III. The evolution of substructures in massive discs at 3-5 au resolution
- 2021MNRAS.502.5390P (2021): A ∼75 per cent occurrence rate of debris discs around F stars in the β Pic moving group
- 2021MNRAS.503...77W (2021): Star formation in 'the Brick': ALMA reveals an active protocluster in the Galactic centre cloud G0.253+0.016
- 2021MNRAS.503.1174K (2021): Feedback factory: multiple faint radio jets detected in a cluster at z = 2
- 2021MNRAS.503.4320F (2021): ALMA-IRDC - II. First high-angular resolution measurements of the <SUP>14</SUP>N/<SUP>15</SUP>N ratio in a large sample of infrared-dark cl…
- 2021MNRAS.504.2687N (2021): Morpho-kinematics of the circumstellar envelope of the AGB star R Dor: a global view
- 2021MNRAS.506.1978L (2021): High-resolution ALMA and HST images of q<SUP>1</SUP> Eri: an asymmetric debris disc with an eccentric Jupiter
- 2021MNRAS.506.4175M (2021): Massive protocluster of a periodic maser source G188.95+0.89
- 2021MNRAS.508.4639Z (2021): ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions-VI. On the formation of the 'L' type filament in G286.21+0.17
- 2021MNRAS.508.5259M (2021): An ACA 1 mm survey of HzRGs in the ELAIS-S1: survey description and first results
- 2021PASJ...73..205T (2021): ALMA view of the Galactic super star cluster RCW 38 at 270 au resolution
- 2021PASJ...73S..35T (2021): The formation of young massive clusters triggered by cloud-cloud collisions in the Antennae galaxies NGC 4038/NGC 4039
- 2021RAA....21...26Y (2021): Collapsing index: a new method to identify star-forming cores based on ALMA images
- 2021Sci...371..713L (2021): A massive stellar bulge in a regularly rotating galaxy 1.2 billion years after the Big Bang
- 2022A&A...659A.109K (2022): A search for cool molecular gas in GK Persei and other classical novae
- 2022A&A...660L...6C (2022): The ALMA-PILS survey: First tentative detection of 3-hydroxypropenal (HOCHCHCHO) in the interstellar medium and chemical modeling of the C<…
- 2022A&A...661L...4A (2022): A first look at the submillimeter Sun with ALMA
- 2022A&A...662A...8M (2022): ALMA-IMF. I. Investigating the origin of stellar masses: Introduction to the Large Program and first results
- 2022A&A...663A..61P (2022): Variations in the Σ<SUB>SFR</SUB> ‒ Σ<SUB>mol</SUB> ‒ Σ<SUB>⋆</SUB> plane across galactic environments in PHANGS galaxies
- 2022A&A...664A..60B (2022): Compact molecular gas emission in local LIRGs among low- and high-z galaxies
- 2022A&A...664A..63X (2022): Starbursts with suppressed velocity dispersion revealed in a forming cluster at z = 2.51
- 2022A&A...664A.171V (2022): FAUST. V. Hot methanol in the [BHB2007] 11 protobinary system; hot corino versus shock origin
- 2022A&A...665A.107T (2022): Black hole and host galaxy growth in an isolated z ∼ 6 QSO observed with ALMA
- 2022AJ....164...43S (2022): Molecular Cloud Populations in the Context of Their Host Galaxy Environments: A Multiwavelength Perspective
- 2022ApJ...927..218H (2022): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): A Hot Corino Survey toward Protostellar Cores in the Orion Cloud
- 2022ApJ...931L...5J (2022): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Deriving Inclination Angle and Velocity of the Protostellar Jets from Their SiO…
- 2022ApJ...939L...6B (2022): First Millimeter Flares Detected from ϵ Eridani with the Atacama Large Millimeter/submillimeter Array
- 2022MNRAS.510.3734D (2022): A high-resolution investigation of the multiphase ISM in a galaxy during the first two billion years
- 2022MNRAS.512.1012C (2022): Cuspy dark matter density profiles in massive dwarf galaxies
- 2022MNRAS.512.1522D (2022): WISDOM Project - X. The morphology of the molecular ISM in galaxy centres and its dependence on galaxy structure
- 2022MNRAS.512.4419P (2022): ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions - X. Chemical differentiation among the massive cores in G9.62+0.…
- 2022MNRAS.513.5790C (2022): Variable structure in the PDS 70 disc and uncertainties in radio-interferometric image restoration
- 2022MNRAS.514..578W (2022): The initial conditions for young massive cluster formation in the Galactic Centre: convergence of large-scale gas flows
- 2022MNRAS.514.5035L (2022): WISDOM project - XI. Star formation efficiency in the bulge of the AGN-host Galaxy NGC 3169 with SITELLE and ALMA
- 2022MNRAS.514.6215Y (2022): Is there a sub-parsec-scale jet base in the nearby dwarf galaxy NGC 4395?
- 2022MNRAS.515.1751W (2022): Dual constraints with ALMA: new [O III] 88-μm and dust-continuum observations reveal the ISM conditions of luminous LBGs at z 7
- 2022MNRAS.515.3126I (2022): The ALMA REBELS Survey: dust continuum detections at z &gt; 6.5
- 2022MNRAS.516.4066L (2022): WISDOM Project - XIII. Feeding molecular gas to the supermassive black hole in the starburst AGN-host galaxy Fairall 49
- 2023A&A...669A..53B (2023): Sulphur monoxide emission tracing an embedded planet in the HD 100546 protoplanetary disk
- 2023A&A...669A..90C (2023): Magnetically regulated collapse in the B335 protostar?. II. Observational constraints on gas ionization and magnetic field coupling
- 2023A&A...671A..69G (2023): The Sun at millimeter wavelengths. IV. Magnetohydrodynamic waves in small-scale bright features
- 2023A&A...673A..46B (2023): Another X-ray UFO without a momentum-boosted molecular outflow. ALMA CO(1-0) observations of the galaxy pair IRAS 05054+1718
- 2023A&A...674A..75N (2023): ALMA-IMF. V. Prestellar and protostellar core populations in the W43 cloud complex
- 2023A&A...674A.125B (2023): ATOMIUM: Probing the inner wind of evolved O-rich stars with new, highly excited H<SUB>2</SUB>O and OH lines
- 2023A&A...676A...4C (2023): FAUST. IX. Multiband, multiscale dust study of L1527 IRS. Evidence for variations in dust properties within the envelope of a class 0/I you…
- 2023A&A...676A..67W (2023): Quantifying the energetics of molecular superbubbles in PHANGS galaxies
- 2023A&A...677A..80W (2023): ALMA and VLBA views on the outflow associated with an O-type protostar in G26.50+0.28
- 2023A&A...677A..97F (2023): A high-resolution radio study of the L1551 IRS 5 and L1551 NE jets
- 2023A&A...678A.160E (2023): FAUST. X. Formaldehyde in the protobinary system [BHB2007] 11: Small-scale deuteration
- 2023A&A...678A.194C (2023): ALMA-IMF. VII. First release of the full spectral line cubes: Core kinematics traced by DCN J = (3‒2)
- 2023A&A...679A.119R (2023): PRUSSIC. II. ALMA imaging of dense-gas tracers in SDP.81: Evidence for low mechanical heating and a sub-solar metallicity in a z = 3.04 dus…
- 2023ApJ...942L..24K (2023): UGC 4211: A Confirmed Dual Active Galactic Nucleus in the Local Universe at 230 pc Nuclear Separation
- 2023ApJ...944...49F (2023): 300: An ACA 870 μm Continuum Survey of Orion Protostars and Their Evolution
- 2023ApJ...944L..18M (2023): PHANGS-JWST First Results: Interstellar Medium Structure on the Turbulent Jeans Scale in Four Disk Galaxies Observed by JWST and the Atacam…
- 2023ApJ...945...69R (2023): Updated Measurements of [O III] 88 μm, [C II] 158 μm, and Dust Continuum Emission from a z = 7.2 Galaxy
- 2023ApJ...945..121U (2023): ALMA Lensing Cluster Survey: Properties of Millimeter Galaxies Hosting X-Ray-detected Active Galactic Nuclei
- 2023ApJ...948..110Y (2023): Multiple Rings and Asymmetric Structures in the Disk of SR 21
- 2023ApJ...948..127O (2023): FAUST. VII. Detection of a Hot Corino in the Prototypical Warm Carbon-chain Chemistry Source IRAS 15398-3359
- 2023ApJ...948L...2Y (2023): Eccentric Dust Ring in the IRS 48 Transition Disk
- 2023ApJ...949..108K (2023): Diverse Molecular Structures across the Whole Star-forming Disk of M83: High-fidelity Imaging at 40 pc Resolution
- 2023ApJ...953..164M (2023): ACA CO(J = 2-1) Mapping of the Nearest Spiral Galaxy M33. I. Initial Results and Identification of Molecular Clouds
- 2023ApJ...954..197I (2023): ALMA Measurement of 10 kpc Scale Lensing-power Spectra toward the Lensed Quasar MG J0414+0534
- 2023ApJ...958...53S (2023): ALMA Observations of Supernova Remnant N49 in the Large Magellanic Cloud. II. Non-LTE Analysis of Shock-heated Molecular Clouds
- 2023MNRAS.518.3183L (2023): An extended [C II] halo around a massive star-forming galaxy at z = 5.3
- 2023MNRAS.520.3245Z (2023): ATOMS: ALMA three-millimetre observations of massive star-forming regions - XIV. Properties of resolved ultra-compact H II regions
- 2023MNRAS.521.1045R (2023): Regular rotation and low turbulence in a diverse sample of z ∼ 4.5 galaxies observed with ALMA
- 2023MNRAS.521.3348N (2023): The ALMOND survey: molecular cloud properties and gas density tracers across 25 nearby spiral galaxies with ALMA
- 2023MNRAS.522.2384M (2023): FAUST - VIII. The protostellar disc of VLA 1623-2417W and its streamers imaged by ALMA
- 2023MNRAS.522.3719L (2023): Evidence of high-mass star formation through multiscale mass accretion in hub-filament-system clouds
- 2023MNRAS.522.4078C (2023): WISDOM Project - XV. Giant molecular clouds in the central region of the barred spiral galaxy NGC 5806
- 2023MNRAS.523.1140L (2023): NGC 1436: the making of a lenticular galaxy in the Fornax Cluster
- 2023MNRAS.523.4970N (2023): Resolving the binary components of the outbursting protostar HBC 494 with ALMA
- 2023MNRAS.524.3671Z (2023): Discovery of a radio jet in the Cloverleaf quasar at z = 2.56
- 2023NatAs...7..684K (2023): Azimuthal C/O variations in a planet-forming disk
- 2023PASJ...75..311K (2023): Galaxy clusters at z ∼ 1 imaged by ALMA with the Sunyaev-Zel'dovich effect
- 2023PASJ...75..424O (2023): ALMA Band 6 high-resolution observations of the transitional disk around SY Chamaeleontis
- 2023PASJ...75..646K (2023): Investigating physical states of molecular gas in the overlapping region of interacting galaxies NGC 4567/4568 using ALMA
- 2023PASP..135b5002C (2023): A Characterization of the ALMA Phasing System at 345 GHz
- 2023PASP..135c4501P (2023): Data Combination: Interferometry and Single-dish Imaging in Radio Astronomy
- 2023PASP..135g4501H (2023): The ALMA Interferometric Pipeline Heuristics
- 2023PSJ.....4..206R (2023): ALMA Observations of the DART Impact: Characterizing the Ejecta at Submillimeter Wavelengths
- 2024A&A...681A.117P (2024): The CO-to-H<SUB>2</SUB> conversion factor of molecular outflows. Rovibrational CO emission in NGC 3256-S resolved by JWST/NIRSpec
- 2024A&A...682A..55M (2024): High-resolution ALMA observations of compact discs in the wide-binary system Sz 65 and Sz 66
- 2024A&A...682A..78V (2024): JOYS+: Mid-infrared detection of gas-phase SO<SUB>2</SUB> emission in a low-mass protostar. The case of NGC 1333 IRAS 2A: Hot core or accre…
- 2024A&A...682A.186L (2024): Feeding and feedback processes in the Spiderweb proto-intracluster medium
- 2024A&A...682L...5G (2024): Structures Of Dust and gAs (SODA): Constraining the innermost dust properties of II Zw96 with JWST observations of H<SUB>2</SUB>O and CO
- 2024A&A...683A.141R (2024): AB Aur, a Rosetta stone for studies of planet formation. III. Continuum observations at 2 and 7 mm
- 2024A&A...684A...4U (2024): Charting circumstellar chemistry of carbon-rich asymptotic giant branch stars. I. ALMA 3 mm spectral surveys
- 2024A&A...684A.174P (2024): High turbulence in the IM Lup protoplanetary disk. Direct observational constraints from CN and C<SUB>2</SUB>H emission
- 2024A&A...684L..12S (2024): FAUST. XIII. Dusty cavity and molecular shock driven by IRS7B in the Corona Australis cluster
- 2024A&A...685A.138V (2024): The cold interstellar medium of a normal sub-L<SUP>⋆</SUP> galaxy at the end of reionization
- 2024A&A...686A..31B (2024): Molecular isotopologue measurements toward super star clusters and the relation to their ages in NGC 253 with ALCHEMI
- 2024A&A...686A.156D (2024): ALMA-ALPINE [CII] survey: The sub-kpc morphology of three main sequence galaxy systems at z ∼ 4.5 revealed by ALMA
- 2024A&A...686A.201N (2024): ALMA view of the L1448-mm protostellar system on disk scales: CH<SUB>3</SUB>OH and H<SUP>13</SUP>CN as new disk wind tracers
- 2024A&A...686A.206Y (2024): First ALMA observations of the HD 105211 debris disc: A warm dust component close to a gigayear-old star
- 2024A&A...686A.298G (2024): Into the thick of it: ALMA 0.45 mm observations of HL Tau at a resolution of 2 au
- 2024A&A...686L..13D (2024): FAUST. XV. A disc wind mapped by CH<SUB>3</SUB>OH and SiO in the inner 300 au of the NGC 1333 IRAS 4A2 protostar
- 2024A&A...687A.112M (2024): Probing the dynamical and kinematical structures of detached shells around AGB stars
- 2024A&A...687A.311A (2024): V892 Tau: A tidally perturbed circumbinary disc in a triple stellar system
- 2024A&A...688A..30B (2024): Emergence of high-mass stars in complex fiber networks (EMERGE). II. The need for data combination in ALMA observations
- 2024A&A...688L..22P (2024): FAUST. XVII. Super deuteration in the planet-forming system IRS 63 where the streamer strikes the disk
- 2024A&A...689A..41V (2024): XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster
- 2024A&A...689A..65R (2024): ALMA high-resolution observations unveil planet formation shaping molecular emission in the PDS 70 disk
- 2024A&A...689A.122B (2024): The properties and kinematics of HCN emission across the closest starburst galaxy NGC 253 observed with ALMA
- 2024A&A...689A.145S (2024): The ALMA-CRISTAL survey: Discovery of a 15 kpc-long gas plume in a z = 4.54 Lyman-α blob
- 2024A&A...689A.273R (2024): The ALMA-ALPAKA survey: II. Evolution of turbulence in galaxy disks across cosmic time: Difference between cold and warm gas
- 2024A&A...689L...5M (2024): FAUST: XVIII. Evidence of annular substructure in a very young Class 0 disk
- 2024A&A...690A..46S (2024): Early Planet Formation in Embedded Disks (eDisk): XVI. Asymmetric dust disk driving a multicomponent molecular outflow in the young Class 0…
- 2024A&A...690A..55S (2024): NOEMA formIng Cluster survEy (NICE): Characterizing eight massive galaxy groups at 1.5 &lt; z &lt; 4 in the COSMOS field
- 2024A&A...690A.185W (2024): Dynamical accretion flows: ALMAGAL: Flows along filamentary structures in high-mass star-forming clusters
- 2024A&A...690A.197M (2024): The ALMA-CRISTAL survey: Widespread dust-obscured star formation in typical star-forming galaxies at z = 4─6
- 2024A&A...690A.258B (2024): ALMACAL: XII. Data characterisation and products
- 2024A&A...690A.372L (2024): A new measurement of the Galactic <SUP>12</SUP>C/<SUP>13</SUP>C gradient from sensitive HCO<SUP>+</SUP> absorption observations
- 2024A&A...690A.375S (2024): Emergence of high-mass stars in complex fiber networks (EMERGE): III. Fiber networks in Orion
- 2024A&A...691A..70N (2024): Disruption of a massive molecular cloud by a supernova in the Galactic Centre: Initial results from the ACES project
- 2024A&A...691A.121N (2024): A 260 pc resolution ALMA map of HCN(1─0) in the galaxy NGC 4321
- 2024A&A...691A.197K (2024): Compact and high excitation molecular clumps in the extended ultraviolet disk of M83
- 2024A&A...692A..86H (2024): Millimetre observations of the S-type AGB star χ Cygni: Variability of the emission of the inner envelope
- 2024A&A...692A.215C (2024): Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon
- 2024AJ....167...66Y (2024): Chemistry of Complex Organic Molecules in the V883 Ori Disk Revealed by ALMA Band 3 Observations
- 2024AJ....167...72D (2024): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Molecular Jets and Episodic Accretion in Protostars
- 2024AJ....167...77D (2024): JWST Imaging of Edge-on Protoplanetary Disks. I. Fully Vertically Mixed 10 μm Grains in the Outer Regions of a 1000 au Disk
- 2024ApJ...961..120C (2024): Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus
- 2024ApJ...961L..35M (2024): The ALMA-QUARKS Survey: Detection of Two Extremely Dense Substructures in a Massive Prestellar Core
- 2024ApJ...962...48J (2024): Thermal Properties of the Hot Core Population in Sagittarius B2 Deep South.
- 2024ApJ...962...88V (2024): The EDGE-CALIFA Survey: Molecular Gas and Star Formation Activity across the Green Valley
- 2024ApJ...963..103G (2024): The ALMA View of Positive Black Hole Feedback in the Dwarf Galaxy Henize 2─10
- 2024ApJ...963..163I (2024): The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). X. Hot Gas Reveals Deeply Embedded Star Formation
- 2024ApJ...964...34L (2024): Multiple Jets in the Bursting Protostar HOPS 373SW
- 2024ApJ...964..190L (2024): Mapping the Vertical Gas Structure of the Planet-hosting PDS 70 Disk
- 2024ApJ...965..108U (2024): ALMA Lensing Cluster Survey: Full Spectral Energy Distribution Analysis of z ∼ 0.5─6 Lensed Galaxies Detected with millimeter Observations
- 2024ApJ...966...32E (2024): Early Planet Formation in Embedded Disks (eDisk). XIII. Aligned Disks with Nonsettled Dust around the Newly Resolved Class 0 Protobinary R …
- 2024ApJ...966...63Y (2024): The First Spatially Resolved Detection of <SUP>13</SUP>CN in a Protoplanetary Disk and Evidence for Complex Carbon Isotope Fractionation
- 2024ApJ...966..117X (2024): Disk Wind Feedback from High-mass Protostars. III. Synthetic CO Line Emission
- 2024ApJ...966..120L (2024): Dark Dragon Breaks Magnetic Chain: Dynamical Substructures of IRDC G28.34 Form in Supported Environments
- 2024ApJ...966..130R (2024): Investigating the Drivers of Electron Temperature Variations in H II Regions with Keck-KCWI and VLT-MUSE
- 2024ApJ...966..171M (2024): The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). XI. Statistical Study of Early Fragmentation
- 2024ApJ...966..192S (2024): Multiple Outflows around a Single Protostar IRAS 15398−3359
- 2024ApJ...967...68H (2024): Radial and Vertical Constraints on the Icy Origin of H<SUB>2</SUB>CO in the HD 163296 Protoplanetary Disk
- 2024ApJ...967..133S (2024): Hidden Gems on a Ring: Infant Massive Clusters and Their Formation Timeline Unveiled by ALMA, HST, and JWST in NGC 3351
- 2024ApJ...968...34W (2024): The Galaxies Missed by Hubble and ALMA: The Contribution of Extremely Red Galaxies to the Cosmic Census at 3 &lt; z &lt; 8
- 2024ApJ...968..131T (2024): Internal 1000 au Scale Structures of the R CrA Cluster-forming Cloud. I. Filamentary Structures
- 2024ApJ...968L..11G (2024): A Broad Line-width, Compact, Millimeter-bright Molecular Emission Line Source near the Galactic Center
- 2024ApJ...969...56M (2024): Observational Constraints on Sunyaev─Zeldovich Effect Halos around High-z Quasars
- 2024ApJ...969..143I (2024): A Radial Decrease in Kinetic Temperature Measured with H<SUB>2</SUB>CO in 30 Doradus
- 2024ApJ...970L..40S (2024): Direct Observational Evidence of Multi-epoch Massive Star Formation in G24.47+0.49
- 2024ApJ...971..176H (2024): Unraveling the Mystery of the Low CO-to-H<SUB>2</SUB> Conversion Factor in Starburst Galaxies: RADEX Modeling of the Antennae
- 2024ApJ...971..187A (2024): High-resolution Study of the Outflow Activity and Chemical Environment of Chamaeleon-MMS1
- 2024ApJ...971L..23L (2024): Polarization Substructure in the Spiral-dominated HH 111 Disk: Evidence for Grain Growth
- 2024ApJ...972..147C (2024): Comparisons between Resolved Star Formation Rate and Gas Tracers in the Strongly Lensed Galaxy SDSS J0901+1814 at Cosmic Noon
- 2024ApJ...974L..25D (2024): Asymmetric Dust Accumulation of the PDS 70 Disk Revealed by ALMA Band 3 Observations
- 2024ApJ...976...29H (2024): ALMASOP. The Localized and Chemically Rich Features near the Bases of the Protostellar Jet in HOPS 87
- 2024ApJ...976..132H (2024): High-resolution ALMA Observations of Richly Structured Protoplanetary Disks in σ Orionis
- 2024ApJ...976..198H (2024): Whole-disk Sampling of Molecular Clouds in M83
- 2024ApJ...976..201F (2024): Constraining Quasar Feedback from Analysis of the Hydrostatic Equilibrium of the Molecular Gas in Their Host Galaxies
- 2024ApJ...976..241Y (2024): The ALMA-QUARKS Survey: Fibers' Role in Star Formation Unveiled in an Intermediate-mass Protocluster Region of the Vela D Cloud
- 2024ApJ...976..258K (2024): Chemistry in the GG Tau A Disk: Constraints from H<SUB>2</SUB>D<SUP>+</SUP>, N<SUB>2</SUB>H<SUP>+</SUP>, and DCO<SUP>+</SUP> High Angular R…
- 2024ApJ...977...37N (2024): Turbulent Pressure Heats Gas and Suppresses Star Formation in Galactic Bar Molecular Clouds
- 2024ApJ...977..198L (2024): The SUPERCOLD-CGM Survey. II. [C I](1─0) Emission and the Physical Conditions of Cold Gas in Enormous Lyα Nebulae at z ∼ 2
- 2024JApA...45...31M (2024): ALMA detection of hydrogen cyanide in the atmosphere of Saturn
- 2024MNRAS.527.1444A (2024): ATCA study of Small Magellanic Cloud supernova remnant 1E 0102.2-7219
- 2024MNRAS.527.4420M (2024): The Quasar Feedback Survey: characterizing CO excitation in quasar host galaxies
- 2024MNRAS.527.9343L (2024): WISDOM project - XVIII. Molecular gas distributions and kinematics of three megamaser galaxies
- 2024MNRAS.527.9668H (2024): Surviving the heat: multiwavelength analysis of V883 Ori reveals that dust aggregates survive the sublimation of their ice mantles
- 2024MNRAS.528.5019H (2024): An optimal ALMA image of the Hubble Ultra Deep Field in the era of JWST: obscured star formation and the cosmic far-infrared background
- 2024MNRAS.529L...1J (2024): New constraints on the molecular gas content of a z 8 galaxy from JVLA CO(J = 2-1) observations
- 2024MNRAS.530..597B (2024): Cloud-scale molecular gas properties of the ANTENNAE merger: a comparative study with PHANGS-ALMA galaxies and NGC 3256
- 2024MNRAS.531.2653C (2024): Multiple chemical tracers finally unveil the intricate NGC 1333 IRAS 4A outflow system. FAUST XVI
- 2024MNRAS.531.4045C (2024): WISDOM Project - XXI. Giant molecular clouds in the central region of the barred spiral galaxy NGC 613: a steep size-linewidth relation
- 2024MNRAS.533.2966Q (2024): ALMA follow-up of 3000 red-Herschel galaxies: the nature of extreme submillimetre galaxies
- 2024MNRAS.534..683Z (2024): Molecular clouds as hubs in spiral galaxies: gas inflow and evolutionary sequence
- 2024MNRAS.535..729P (2024): The spatially resolved relation between dust, gas, and metal abundance with the TYPHOON survey
- 2024MNRAS.535.1364Z (2024): ATOMS: ALMA three-millimeter observations of massive star-forming regions - XVIII. On the origin and evolution of dense gas fragments in mo…
- 2024NatAs...8..308D (2024): Chemical tracers of a highly eccentric AGB-main-sequence star binary
- 2024NatAs...8..587F (2024): Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk
- 2024PASJ...76..437Y (2024): ALMA 2D super-resolution imaging of Taurus-Auriga protoplanetary disks: Probing statistical properties of disk substructures
- 2024PASJ...76..960S (2024): Spiral magnetic fields and their role on accretion dynamics in the circumnuclear disk of Sagittarius A*: Insight from λ = 850 μm polarizati…
- 2024PSJ.....5..221C (2024): Evidence for Surprising Heavy Nitrogen Isotopic Enrichment in Comet 46P/Wirtanen's Hydrogen Cyanide
- 2024RAA....24c5009N (2024): EP Aquarii: A New Picture of the Circumstellar Envelope
- 2024RAA....24f5008M (2024): Study of Complex Nitrogen and Oxygen-bearing Molecules toward the High-mass Protostar IRAS 18089─1732
- 2024RAA....24f5011X (2024): The ALMA-QUARKS Survey. II. The ACA 1.3 mm Continuum Source Catalog and the Assembly of Dense Gas in Massive Star-Forming Clumps
- 2025A&A...693A..49S (2025): A complete Herbig disk mass survey in Orion
- 2025A&A...693A.174E (2025): Molecular gas stratification and disturbed kinematics in the Seyfert galaxy MCG-05-23-16 revealed by JWST and ALMA
- 2025A&A...693A.190J (2025): ALMA Lensing Cluster Survey: Dust mass measurements as a function of redshift, stellar mass, and star formation rate from z = 1 to z = 5
- 2025A&A...693A.199C (2025): Interaction between the supernova remnant W44 and the infrared dark cloud G034.77-00.55: Shock induced star formation
- 2025A&A...693A.237I (2025): The ALMA-CRISTAL Survey: Spatial extent of [CII] line emission in star-forming galaxies at z = 4−6
- 2025A&A...693A.286S (2025): Intermediate mass T Tauri disk masses and a comparison to their Herbig disk descendants
- 2025A&A...694L..15H (2025): Discovery of ionized circumstellar gas emission around the long-period Cepheid ℓ Carinae with ALMA
- 2025A&A...695A..51B (2025): Hierarchical accretion flow from the G351 infrared dark filament to its central cores
- 2025A&A...695A.163B (2025): ALMACAL: XIII. Evolution of the CO luminosity function and the molecular gas mass density out to z ∼ 6
- 2025A&A...695A.278H (2025): FAUST: XXIII. SiO outflow in the protobinary system L483
- 2025A&A...696A..18C (2025): The hot corino-like chemistry of four FUor-like protostars
- 2025A&A...696A..31G (2025): Shock-induced HCNH<SUP>+</SUP> abundance enhancement in the heart of the starburst galaxy NGC 253 unveiled by ALCHEMI
- 2025A&A...696A.100G (2025): PDRs4All: XII. Far-ultraviolet-driven formation of simple hydrocarbon radicals and their relation with polycyclic aromatic hydrocarbons
- 2025A&A...696A.149M (2025): ALMAGAL: I. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy: Presentation of the survey and early results
- 2025A&A...696A.150S (2025): ALMAGAL: II. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy: ALMA data processing and pipeline
- 2025A&A...696A.151C (2025): ALMAGAL: III. Compact source catalog: Fragmentation statistics and physical evolution of the core population
- 2025A&A...696A.202S (2025): ALMA-IMF: XVIII. The assembly of a star cluster: Dense N<SUB>2</SUB>H<SUP>+</SUP> (1─0) kinematics in the massive G351.77 protocluster
- 2025A&A...698A.115R (2025): Radial variations in the nitrogen, carbon, and hydrogen fractionation in the PDS 70 planet-hosting disk
- 2025A&A...698A.165A (2025): Confirmation of a ring structure in the disk around MP Mus (PDS 66) with ALMA Band 7 observations
- 2025A&A...698A.296R (2025): The impact of spiral arms on the star formation life cycle
- 2025A&A...698L..16S (2025): FAUST: XXIV. Large dust grains in the protostellar outflow cavity walls of the Class I binary L1551 IRS5
- 2025A&A...699A..34M (2025): ALMAGAL: IV. Morphological comparison of molecular and thermal dust emission using the histogram of oriented gradients method
- 2025A&A...699A..70H (2025): Investigating the chemical link between H<SUB>2</SUB>CO and CH<SUB>3</SUB>OH within the central molecular zone of NGC 253
- 2025A&A...699A..80H (2025): The ALMA-CRISTAL survey: Gas, dust, and stars in star-forming galaxies when the Universe was ∼1 Gyr old: I. Survey overview and case studies
- 2025A&A...699A.256P (2025): The ALMA-CRISTAL survey: Extended [CII] emission in an interacting galaxy system at z ∼ 5.5
- 2025A&A...699A.316S (2025): OGLE-2002-BLG-360: A dusty anomaly among red nova remnants
- 2025A&A...699A.373F (2025): Inner disc and circumplanetary material in the PDS 70 system: Insights from multi-epoch, multi-frequency ALMA observations
- 2025A&A...700A.141H (2025): Statistical nuclear spin ratios of deuterated ammonia in the pre-stellar core L1544
- 2025A&A...700A.165B (2025): GAMA 526784: The progenitor of a globular cluster-rich ultra-diffuse galaxy?: II. Molecular gas, neutral gas, and environment
- 2025A&A...700A.285W (2025): Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593
- 2025A&A...700L...5G (2025): Edge-On Disk Study (EODS): I. Thermal structure of the Flying Saucer disk
- 2025A&A...700L..11S (2025): Stephenson 2 DFK 52: Discovery of an exotic red supergiant in the massive stellar cluster RSGC2
- 2025A&A...701A.113M (2025): MIRACLE: I. Unveiling the multi-phase, multi-scale physical properties of the active galaxy NGC 424 with MIRI, MUSE, and ALMA
- 2025A&A...701A.141L (2025): Sulfur oxides tracing streamers and shocks at low-mass protostellar disk─envelope interfaces
- 2025A&A...701A.219N (2025): The Rosetta Stone project: III. ALMA synthetic observations of fragmentation in high-mass star-forming clumps
- 2025A&A...702A..18D (2025): Multi-frequency observations of PDS70c: Radio emission mechanisms in the circumplanetary environment
- 2025A&A...702A..35D (2025): The ALMA-QUARKS survey: Extensive detection of acetamide in multiple high-mass star-forming regions
- 2025A&A...702A.133K (2025): ALMA-IMF: XIX. C<SUP>18</SUP>O (J = 2─1): Measurements of turbulence in 15 massive protoclusters
- 2025A&A...702A.276P (2025): The pre-eruption state of T CrB as observed with ALMA in 2024
- 2025A&A...703A..15M (2025): Discovery of carbon monoxide emission from five debris disks around young A-type stars
- 2025A&A...704A.133S (2025): Early Planet Formation in Embedded Disks (eDisk): XX. Constraining the chemical tracers of young protostellar sources
- 2025ApJ...979..142N (2025): Peculiar Dust Emission within the Orion Molecular Cloud
- 2025ApJ...979..217S (2025): The Arp 240 Galaxy Merger: A Detailed Look at the Molecular Kennicutt─Schmidt Star Formation Law on Subkiloparsec Scales
- 2025ApJ...981...49S (2025): ALMA Observations of Peculiar Embedded Icy Objects
- 2025ApJ...984L..16G (2025): exoALMA. XI. ALMA Observations and Hydrodynamic Models of LkCa 15: Implications for Planetary Mass Companions in the Dust Continuum Cavity
- 2025ApJ...985...84L (2025): A Multiline Analysis of the Distribution and Excitation of CS and H<SUB>2</SUB>CS in the HD 163296 Disk
- 2025ApJ...985..166K (2025): Early Planet Formation in Embedded Disks (eDisk). XXI. Limited Role of Streamers in Mass Supply to the Disk in the Class 0 Protostar IRAS 1…
- 2025ApJ...985..194P (2025): Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies
- 2025ApJ...985..226W (2025): A Multiwavelength Study of the Dynamic Environment Surrounding the FUor V960 Mon
- 2025ApJ...985..243B (2025): The ALMA-CRISTAL Survey: Weak Evidence for Star-formation-driven Outflows in z ∼ 5 Main-sequence Galaxies
- 2025ApJ...986L..11S (2025): Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint
- 2025ApJ...987...61R (2025): Resolved ALMA [C II] 158 μm Observations at Cosmic Noon: Interstellar Medium Structure and Dynamics of the Starbursting QSO SDSS J1000
- 2025ApJ...988...72S (2025): ALMA-JELLY. I. High Resolution CO(2─1) Observations of Ongoing Ram Pressure Stripping in NGC 4858 Reveal Asymmetrical Gas Tail Formation an…
- 2025ApJ...988..106H (2025): Grand Design Spiral Arms in the Compact, Embedded Protoplanetary Disk of Haro 6-13
- 2025ApJ...988..162D (2025): Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations
- 2025ApJ...988..172H (2025): The Centre of Attention: A Powerful Radio Galaxy Pinpoints a Near-infrared-dark Protocluster at z ∼ 3.9
- 2025ApJ...989....3D (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). III. Dust and Gas Disk Properties in the Lupus Star-forming Region
- 2025ApJ...989...30Z (2025): SO Emission in the Dynamically Perturbed Protoplanetary Disks around CQ Tau and MWC 758
- 2025ApJ...989...56H (2025): ALMASOP. A Rotating Feature Rich in Complex Organic Molecules in a Protostellar Core
- 2025ApJ...989...83B (2025): CO Emission and Absorption-line Survey of the M87 Nucleus Using Archival ALMA Imaging
- 2025ApJ...989..138S (2025): A First Look at Spatially Resolved Infrared Supernova Remnants in M33 with JWST
- 2025ApJ...990..150A (2025): PEACHES. IV. Tracing the Formation and Evolution of C<SUB>2</SUB>H in Perseus Low-mass Protostars
- 2025ApJ...990..173C (2025): LZ-STAR Survey: Low-metallicity Star Formation Survey of Sh2-284. I. Ordered Massive Star Formation in the Outer Galaxy
- 2025ApJ...990..183U (2025): Multiwavelength Dust Characterization of the HL Tau Disk and Implications for Planet Formation
- 2025ApJ...990..209C (2025): The Resolved Structure of a Low-metallicity Photodissociation Region
- 2025ApJ...990L..31B (2025): ALMA Reveals Bright Circumgalactic Emission and a Biconical Outflow in z ∼ 6.4 Quasar PSOJ183+05
- 2025ApJ...990L..70L (2025): Discovery of Hα Emission from a Protoplanet Candidate around the Young Star 2MASS J16120668─3010270 with MagAO-X
- 2025ApJ...992...18P (2025): Early Planet Formation in Embedded Disks (eDisk). XXII. Keplerian Disk, Disk Structures, and Jets/Outflows in the Class 0 Protostar IRAS 04…
- 2025ApJ...992...44D (2025): Revisiting the Gas Dynamics of Henize 2─10: Possible Drivers of the Starburst
- 2025ApJ...992...55T (2025): Extended and Compact Ortho-H<SUB>2</SUB>D<SUP>+</SUP> Structures Close to the Moment of Star Formation: Evidence from ALMA-ACA Observations…
- 2025ApJ...992..103Z (2025): Impact of Gravity on Changing Magnetic Field Orientations in a Sample of Massive Protostellar Clusters Observed with ALMA
- 2025ApJ...992L..15L (2025): A Dense Molecular Ringlike Structure in Gaseous CO Depletion Region G34.74−0.12
- 2025ApJ...993..120H (2025): Early Planet Formation in Embedded Disks (eDisk). XVII. A Compact but Structured Keplerian Disk and Large-scale Streamers Revealed in the C…
- 2025ApJ...994..158G (2025): Oxygen Isotopes Reveal Low-mass Star Dominance in the Small Magellanic Cloud
- 2025ApJ...995..108J (2025): Molecular Gas in Major Mergers Hosting Dual and Single AGNs at &lt;10 kpc Nuclear Separations
- 2025ApJ...995..111Z (2025): The ALMA-ATOMS-QUARKS Survey: Resolving a Chemically Rich Massive Protostellar Outflow
- 2025ApJ...995..150K (2025): Comprehensive JWST+ALMA Study on the Extended Lyα Emitters, Himiko, and CR7 at z ∼ 7: Blue Major Merger Systems in Stark Contrast to Submil…
- 2025ApJ...995..193Y (2025): The ALMA-QUARKS Survey: Evidence of a Candidate High-mass Prestellar Core Aside a Bright-rimmed Cloud IRAS 18290-0924
- 2025ApJ...995L...7L (2025): The Rotation Dip in the Envelope─Disk Transition of HH 111: Evidence for Magnetic Braking
- 2025ApJS..278...45F (2025): DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey
- 2025ApJS..280...33Y (2025): The ALMA-QUARKS Survey. III. Clump-to-core Fragmentation and Searches for High-mass Starless Cores
- 2025MNRAS.536..684D (2025): The salty emission of the intermediate-mass AGB star OH 30.1-0.7
- 2025MNRAS.537..520Z (2025): WISDOM Project - XXII. A 5 per cent precision CO-dynamical supermassive black hole mass measurement in the galaxy NGC 383
- 2025MNRAS.537.2232Z (2025): An examination of large-scale galactic effects on molecular cloud properties in NGC 628: the significant impact of tidal effects from neigh…
- 2025MNRAS.538....1Z (2025): ATOMS: ALMA Three-millimeter Observations of massive Star-forming regions - XX. Probability distribution function of integrated intensity f…
- 2025MNRAS.538.2358S (2025): High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15
- 2025MNRAS.540.2396S (2025): MeerKAT discovery of an infalling cold gas tail on to the nearby barred spiral galaxy, NGC 5643
- 2025MNRAS.540.2623P (2025): Exploring the potential for kinematically colder H I component as a tracer for star-forming gas in nearby galaxies
- 2025MNRAS.541.1276Z (2025): The most massive star clusters in molecular clouds: insights from the integrated cloud-wide initial mass function (ICIMF) theory
- 2025MNRAS.541.2540Z (2025): WISDOM Project─XXV. Improving the CO-dynamical supermassive black hole mass measurement in the galaxy NGC 1574 using high spatial resolutio…
- 2025MNRAS.544.4014Z (2025): Connecting star formation in the Milky Way and nearby galaxies ─ I. Comparability of molecular cloud physical properties
- 2025NatAs...9..406L (2025): Inadequate turbulent support in low-metallicity molecular clouds
- 2025NatAs...9.1476C (2025): A D/H ratio consistent with Earth's water in Halley-type comet 12P from ALMA HDO mapping
- 2025NatAs...9.1672Y (2025): Winding motion of spirals in a gravitationally unstable protoplanetary disk
- 2025NatAs...9.1833L (2025): Detection of a septuple stellar system in formation via disk fragmentation
- 2025Natur.642..905L (2025): Evidence for a sub-Jovian planet in the young TWA 7 disk
- 2025PASJ...77..432U (2025): ADF22-WEB: A giant barred spiral starburst galaxy in the z = 3.1 SSA22 protocluster core
- 2025PASJ...77..616I (2025): Cloud-cloud collisions in the Antennae galaxies: Does high-speed collision suppress star formation?
- 2025PASJ...77..834O (2025): Detailed analysis of multiline molecular distributions in the Seyfert galaxy NGC 1068: Possible effect of the active galactic nucleus outfl…
- 2025PASJ...77L..55S (2025): Circumnuclear eccentric gas flow in the Galactic Center revealed by ALMA CMZ Exploration Survey (ACES)
- 2025PASP..137l4501T (2025): The ViSta Method for Stacking in the Fourier Domain and its Application to the Dusty Star-forming Galaxies in the ALMA Science Archive
- 2025SciA...11.4512O (2025): Massive extended streamers feed high-mass young stars
- 2025SciA...11.6953M (2025): A misaligned protostellar disk fed by gas streamers in a barred spiral-like massive dense core
- 2026A&A...705A..96M (2026): FAUST: XXVIII. High-resolution ALMA observations of Class 0/I disks: Structure, optical depths, and temperatures
- 2026A&A...705A.100E (2026): ALMAGAL: V. Relations between the core populations and the parent clump physical properties
- 2026A&A...705L..16C (2026): FAUST: XXX. Dust enhancement in the young binary L1551 IRS 5
- 2026A&A...706A...4R (2026): Resolving the terrestrial planet-forming region of HD 172555 with ALMA: I. Post-impact dust distribution
- 2026A&A...706A.174A (2026): Hiding behind a curtain of dust: Gas and dust properties of an ultra-luminous strongly-lensed z = 3.75 galaxy behind the Milky Way disc
- 2026A&A...706A.186R (2026): Duration and properties of the embedded phase of star formation in 37 nearby galaxies from PHANGS-JWST
- 2026A&A...706A.248T (2026): Interaction of the central jet with the surrounding gas in the protostellar outflow from IRAS 04166+2706
- 2026A&A...706A.285C (2026): Infrared emission from z ∼ 6.5 quasar host galaxies: a direct estimate of dust physical properties
- 2026A&A...706A.292S (2026): Dissecting the dust distribution and polarization around two B213 young stellar objects with ALMA
- 2026A&A...706A.328L (2026): Silicon monoxide in the filamentary infrared dark cloud G035.39-00.33: An ALMA view
- 2026A&A...707A..77H (2026): Massive dusty multiphase outflow in local merger shows no sign of slowing on kiloparsec scales
- 2026A&A...707A.120H (2026): Spatial distribution of organics in the Horsehead nebula: Signposts of chemistry driven by atomic carbon
- 2026A&A...707A.121G (2026): Molecular gas and star formation in central rings across nearby galaxies
- 2026A&A...707A.221S (2026): ALMAGAL: VI. The spatial distribution of dense cores during the evolution of cluster-forming massive clumps
- 2026A&A...707A.252K (2026): Detailed lens modeling and kinematics of the submillimeter galaxy G09v1.97: An analysis of CO, H<SUB>2</SUB>O, H<SUB>2</SUB>O<SUP>+</SUP>, …
- 2026A&A...708A.251X (2026): Linear filament and nested cluster evolution tomography (LANCET): I. Capture the evolution of dense gas in 14-parsec filament G316.8
- 2026A&A...709A.173M (2026): ALMAGAL: VIII. Early phases of triggered star formation in source AG286.0716─1.8229
- 2026A&A...709A.216U (2026): Charting circumstellar chemistry of carbon-rich asymptotic giant branch stars: III. SiO and SiS abundances
- 2026A&A...710A.238D (2026): Dust characterization of halos: The extended emission in protoplanetary disks
- 2026A&A...711A.118A (2026): ALMAGAL: IX. The chemical complexity of AG318.9477−00.1960: A line-identification template for ALMAGAL
- 2026A&A...711A.159M (2026): The formation radius of HCN in O-rich asymptotic giant branch stars
- 2026A&A...711A.239S (2026): ALMA-IMF: XXI. N<SUB>2</SUB>H<SUP>+</SUP> kinematics in the G012.80 protocluster: Evidence of filament rotation and evolution
- 2026A&A...712A.227E (2026): ALMA CO-CAVITY: I. Resolved molecular gas in void galaxies
- 2026AJ....172..108L (2026): Formation of a Protostellar Multiple System via Rotational Fragmentation
- 2026ApJ...997...16H (2026): Ubiquity of Methanol and Its Related Chemical Segregation in Orion Starless Cores: The ALMASOP Sample
- 2026ApJ...997..155M (2026): The ALMA Survey of 70 µm Dark High-mass Clumps in Early Stages (ASHES). XIII. Core Mass Function, Lifetime, and Growth of Prestellar Cores
- 2026ApJ...999...47L (2026): The Extended Mapping Obscuration to Reionization with ALMA (Ex-MORA) Survey: 5σ Source Catalog and Redshift Distribution
- 2026ApJ...999L..32R (2026): CH<SUB>3</SUB>OH and HCN in Interstellar Comet 3I/ATLAS Mapped with the ALMA Atacama Compact Array: Distinct Outgassing Behaviors and a Rem…
- 2026ApJ..1000..308W (2026): The ALPINE-CRISTAL-JWST Survey: Chemical Abundance Comparison between the ISM and CGM of Main-sequence Galaxies at z = 4─6
- 2026ApJ..1001...33L (2026): ALMA FACTS. III. High-resolution CO(2─1)/CO(1─0) Maps of Twelve Nearby Galaxies
- 2026ApJ..1001..161H (2026): The ALMA-QUARKS Survey: Evidence of an Explosive Molecular Outflow in IRAS 15520─5234
- 2026ApJ..1001..184M (2026): Reconciling 3D Models for the Central 10 pc of the Milky Way
- 2026ApJ..1001L...1T (2026): ALMA Band 9 CO(6─5) Reveals a Warm Ring Structure Associated with the Embedded Protostar in the Cold Dense Core MC 27/L1521F
- 2026ApJ..1003...26O (2026): The SOMA Atomic Outflow Survey. I. An Atomic O I and Highly Ionized O III Outflow from Massive Protostar G11.94-00.62
- 2026ApJ..1003...68Y (2026): A Multiscale Molecular and Atomic Gas View on the H II Region N113 in the Large Magellanic Cloud: Evidence for High-mass Star Formation Tri…
- 2026ApJ..1003..231W (2026): Multiscale Gas Structure and Dynamics in an Extragalactic Central Molecular Zone
- 2026ApJ..1004..207M (2026): Global and Local Infall in the ASHES Sample (GLASHES). II. Asymmetric Line Profiles Around Dense Cores in 70 μm Dark Massive Clumps
- 2026ApJ..1005...94N (2026): Dynamical Evidence for a Billion Solar-mass Black Hole in Galaxy NGC 4061 from ALMA <SUP>12</SUP>CO(2─1) Kinematics
- 2026MNRAS.546ag037E (2026): Stellar-mass black holes on the millimetre Fundamental Plane of black hole accretion
- 2026MNRAS.546ag167S (2026): Under the glare of a luminous quasar, the FIR continuum is still an excellent tracer of the ISM down to the central kiloparsec
- 2026MNRAS.548ag325W (2026): 3D insights into SN 1987A: ALMA observations compared to hydrodynamical explosion simulations
- 2026MNRAS.548ag546D (2026): WISDOM project - XXVIII. Molecular gas measurement of the supermassive black hole mass of the galaxy NGC 1387
- 2026MNRAS.549ag781K (2026): GOALS-JWST: resolved multiphase molecular gas in IRAS 20551-4250 using JWST and ALMA
- 2026MNRAS.551g1645K (2026): A high-velocity SiO jet from S255N SMA3
- 2026MNRAS.552g1700S (2026): Dust substructures and line perturbations driven by a forming planet in J16120
