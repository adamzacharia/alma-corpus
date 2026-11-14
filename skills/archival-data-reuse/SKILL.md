---
name: alma-archival-data-reuse
description: "Choose, fetch and combine ALMA archive data for a science goal: which projects and MOUSes to use, whether delivered products (FITS images, cubes, calibrated visibilities, survey releases) are usable as delivered or need recalibration, re-imaging or self-calibration, how to fetch only the products needed instead of whole projects, what to check before combining projects, cycles, configurations or arrays (flux scale, weights, frequencies, uv coverage, beams, astrometry and proper motion, epochs and variability), and what provenance to record. Use when a task names a target and a goal but not the data, when an analysis needs more than one dataset, when archive products look noisier or different from a paper, or when combining data from different projects. Built from 1764 ALMA papers (2012-2026)."
---

# Reusing ALMA archive data: choose, fetch, recalibrate or not, combine

Most ALMA papers use more than one dataset: 1346 of 1764 member papers list two or more project codes, and 92 list
ten or more (pack aggregate). Archive products are often good enough as delivered, and many papers use them that
way, but early-cycle data, bad calibrator models, under-cleaned images and multi-project combinations are where
papers recalibrate. The two mistakes that matter most: downloading whole projects when a few products would do,
and merging datasets whose flux scales, weights, frequencies or positions were never checked against each other.

How to query the archive (TAP/ObsCore, DataLink, MOUS/EB structure, package layout, restoring an MS) is covered
by the companion skill `working-with-alma-data` (Quasar repo: `third_party/alma-data-skill/SKILL.md`, see its
`references/archive-query.md` and `references/products-and-qa.md`). This skill covers what to choose and what to
do with it. The per-check detail for combining is in `references/combination-checks.md`.

Counts: "pack aggregate" means a count printed in the evidence pack (`skills/packs/archival-data-reuse.md`);
"my count" means my regex count over the listed rows of a pack aggregate (301 listed rows each for "used as
delivered" and "how combined"). Data volumes in the pack are the card author's estimates, marked (card).

## Agent checklist

1. Write down the measurement first (quantity, resolution, MRS, line or continuum, epoch needs). Then list every
   MOUS that covers the target, not just the first project (76% of this pack's papers use 2+ project codes, but
   the pack was selected for archival or multi-project work; across the whole corpus about 38% of papers list
   2+ codes, 1,346 of 3,537, my count over all cards).
2. Start from the highest-level product that answers the question: published table or survey release, then
   archive FITS, then calibrated visibilities, then raw data. Fetch per MOUS and per product, never a whole
   project by code. Estimate size before downloading (single tracks ~10-50 GB raw, multi-project sets hundreds
   of GB to TB, images <1 GB; card estimates, e.g. 2014ApJ...792...94D, 2016ApJS..222....1F, 2015ApJ...806L..15K).
3. Default to delivered calibration. About 46 of 301 listed "used as delivered" rows say the authors
   recalibrated or reprocessed (my count); the rest used observatory calibration, often after inspection
   (2015ApJ...810..112O, 2020MNRAS.492.3194S). What "delivered" means depends on the cycle (general practice,
   check the README of the delivery): Cycle 0-1 and much of Cycle 2 data were calibrated by observatory staff with
   manual scripts (scriptForPI/QA2 scripts, no pipeline weblog), and image products, when present, are QA2
   reference images rather than science-ready cubes; pipeline calibration with a weblog is the norm from about
   Cycle 3, and pipeline imaging products from about Cycle 4-5. For early cycles, plan on restoring the MS with
   the delivered scripts in the CASA version they name and imaging it yourself.
3b. Never measure from an archive image before checking it (general practice): primary-beam corrected or not
   (`.pbcor` vs flat noise), units and beam, cleaning depth and mask (negative bowls around extended emission
   mean flux was lost), continuum ranges used for line cubes (automatic ranges can include your line), velocity
   frame and rest frequency, channel width, and whether the spw covers the full line.
4. Recalibrate only for a named reason: a bad or outdated flux-calibrator model (2018A&A...616A.127R,
   2024A&A...684A...4U), a variable flux calibrator (2020ApJ...904...78S), artefacts in the pipeline product
   (2024NatAs...8..256O), lines flagged as RFI or atmosphere (2016ApJ...821L...8S, 2024ApJ...969..102N), or a
   weighting or imaging choice the products do not offer (2018ApJ...854...83T, 2020MNRAS.496.1834L).
5. Before combining anything, check flux scales on overlapping uv ranges, recompute weights (`statwt`), put all
   data on one frequency frame and common bandwidth, align positions (proper motion), and ask whether the source
   varies between epochs. Details in `references/combination-checks.md`.
6. Adopt a flux-scale uncertainty per band when the data are silent: 5% for Bands 3-6 and 10% for Band 7
   (2021A&A...648A..33M), 10% for Bands 6/7 (2025ApJ...989...83B). 10% is by far the most common stated value
   (about 86 of 155 listed values, my count). Use a larger value (15-20%) for combined early-cycle data
   (2023A&A...674A.125B, 2014ApJ...796L..15S). The observatory's stated accuracy (general practice, ALMA
   technical handbook) is about 5% in Bands 3-5, 10% in Bands 6-7 and 20% in Bands 8-10; use these when nothing
   else is known. The term applies to absolute fluxes and anything scaling with them (masses, luminosities). It
   largely cancels only for ratios measured in the same execution and spectral setup; ratios between bands,
   projects or epochs (spectral indices, line ratios from different data) carry both datasets' terms. Positions,
   velocities and sizes do not get it.
6b. Before planning a new study on archive data, check whether the question was already answered, including
   with other datasets: search ADS for the target or sample plus the measurement (team lesson: in CosmicCoder
   runs, unpublished data were taken as proof of a novel question). State what is new (sample, resolution,
   method) before fetching anything.
7. Minimum validation before reporting: image a calibrator or a known source and compare with the calibrator
   catalogue or an earlier measurement (2015MNRAS.451.1141M, 2015ApJ...810..112O); compare fluxes of each
   dataset before and after combination; confirm noise near the expected value (2018ApJ...866..141K).
8. Record provenance for every dataset: project code, MOUS UID, product type and version, calibration route,
   CASA and pipeline version, flux calibrator, adopted flux uncertainty, self-cal settings, weights, alignment
   shifts, and the download date. These are the items the cards most often flag as not stated (CASA version 67,
   self-cal intervals 43, flux calibrator and uncertainty 21, pack aggregate).

## When to use

- A task gives a target and a science goal and the agent must pick the data (top-down work), or a paper's data
  must be refetched for a reproduction (see the `paper-reproduction` skill for the answer key and tolerances).
- More than one dataset is needed: deeper sensitivity (cycle 1+2, 2+3, 1+3+7 combinations, 2023ApJ...945...69R;
  2017ApJ...842L..24A), more uv coverage (compact + extended, 2018A&A...619A.161C), more bands for a spectral
  index or SED (2019ApJ...881..159M), more epochs for astrometry or variability (2026MNRAS.551g1411H).
- Archive data were taken for another purpose: calibrator scans used as science (13 Cycle 0 projects in which a
  blazar was the calibrator, 2016A&A...586A..70L; Titan flux-calibration scans, 2016ApJ...821L...8S; absorption
  toward a calibrator in 33 projects, 2024ApJ...969..102N), or blind searches across many fields
  (2015MNRAS.451.1141M; 2016ApJS..222....1F; 2018ApJ...869...71Z).
- A survey team has released processed products (PHANGS-ALMA v4.0 cubes and moment maps, 2021A&A...656A.133Q,
  2024A&A...691A.351R; MAPS, 2023A&A...674A.113I; DSHARP, 2021A&A...654A..35B; ALPINE DR1, 2021A&A...653A.111R;
  ARI-L re-imaged products, 2021MNRAS.507.3998P).

## When not to use

- **A published table or catalogue answers the question.** Papers adopt A3COSMOS fluxes directly
  (2022A&A...665A...3J) or ALMA calibrator-catalogue flux densities (2022MNRAS.513.6013M, 2024A&A...692A.203K).
  The card estimates such inputs at MB, against tens of GB to TB of visibilities (2017A&A...606A..17M;
  2026MNRAS.551g1411H, card). Use the table and cite it.
- **The job is the combination itself** (12m + 7m + TP weights, feather, MACF): use `array-combination`.
- **The job is self-calibration of one dataset**: use `self-calibration`. For imaging choices (weighting,
  masks, JvM): `imaging-choices`. For fitting visibilities: `uv-plane-fitting`.
- **Time variability is the measurement**: keep epochs separate and use `variability-time-domain`;
  combining hides the signal (2015A&A...577L...4V treated epochs separately; 2024A&A...692A..86H kept epochs
  apart because of variability).
- **Solar data**: they use their own pipeline and archive (SoAP, 2020A&A...635A..71W; SALSA time series,
  2023A&A...671A..69G), not the standard route below.

## Steps

1. **Define what the data must deliver.** Goal: a written requirement that selects datasets.
   - Quantity, band and line, angular resolution, largest scale needed, sensitivity, epoch constraints.
   - Papers set requirements and admit archival data only if they meet them: 6 archival discs met "the
     sensitivity and resolution requirements of the programme" (2026A&A...705A.196H). Check: requirement written.
2. **Inventory every dataset on the target.** Goal: a table of all MOUSes, not one project.
   - Query by position and frequency (companion skill), aggregate by MOUS, list band, array, configuration,
     beam, MRS, sensitivity, dates, release status. Example scope: all public data as of December 2019
     (2021A&A...645A..33B); all public data through 31 December 2020 (2021A&A...655A.113M); 37 ALMA and VLA
     datasets over 11 years for proper motions (2026MNRAS.551g1411H).
   - Include calibrator-intent data and data taken for other targets in the field. Check other facilities too
     (SMA with ALMA, 2025ApJ...985...84L; VLA with ALMA, 2026MNRAS.551g1411H).
   - Write the table to a file and summarise it; do not print raw query results into context (in CosmicCoder
     agent runs, printing huge raw tables cost millions of input tokens). Check: table file exists.
3. **Choose which datasets to use, and say why.** Goal: a selection with reasons per MOUS.
   - Drop data that add noise or artefacts: 7m and TP not combined "due to increased noise and artifacts"
     (2022A&A...662A...8M); a combination with "no gain in sensitivity or image quality" not used
     (2022A&A...665A.107T); combined cubes kept "for reference only, not for measurements" (2024A&A...691A.197K).
   - Some papers never combine projects for the same source (2019ApJS..244...40L) or keep Cycle 0 separate
     (2016ApJ...833..103H). Different products may need different subsets: Cycle 3 only for the inner jet,
     Cycle 1+3 for outer knots (2017NatAs...1E.152L); main results from one cycle, the combination only in an
     appendix (2020ApJ...902...99I).
   - Check: each MOUS marked used / not used with a reason.
4. **Pick the lowest product level that works.** Goal: avoid processing you do not need.
   - Image products as delivered: pipeline continuum images for transient fluxes (2025ApJ...993L...6N),
     JVO first-look images for Gaussian fluxes (2021A&A...655A.113M), archive FITS for counterpart IDs
     (2022MNRAS.511.1408G), archive cubes for line work (2023MNRAS.524.1211M).
   - Triage on products, reprocess only what matters: archive continuum maps for a blind search, maps with
     detections re-reduced (2018ApJ...869...71Z); delivered images for a preliminary check, final images from
     calibrated visibilities (2021A&A...653A.166C); QA2 data used, raw data reprocessed only to check artefacts
     (2021A&A...653A..77P).
   - Go to visibilities when you need custom imaging, self-cal, uv fitting, stacking or combination. Delivered
     FITS can omit targets, SPWs or channels (companion skill, guardrail 7).
   - Check: product level chosen per MOUS, with the reason.
5. **Decide: delivered calibration or recalibration.** Goal: a defensible calibration route per MOUS.
   - Default: delivered calibration after inspecting the calibration plots or weblog. "The calibration plots
     were inspected, deemed adequate, and no changes to the delivered calibration were made"
     (2015ApJ...810..112O). Recalibration "gave no significant improvement" (2016ApJ...830L..16B).
   - Recalibrate when a reason in the checklist (item 4) applies. Other cases in the pack: 7-10% flux correction
     for flux-calibrator polarisation (2023Natur.617..696V); calibrator flux renormalised (2019A&A...626A..81V);
     manual flux fix for one galaxy (2026ApJ..1001...33L); per-spw flux rescaling up to 2% (2025ApJ...989...83B);
     revised JAO scripts after a calibration problem was found (2021ApJ...907L..27A).
   - Routes to calibrated visibilities: run the delivered scripts (`scriptForPI.py`) in the required CASA
     version (2019ApJS..244...40L; 2021ApJ...918...76C; 2024ApJ...969...56M), or ask an ARC for calibrated MSs
     (EU ARC, 2024A&A...689A.283L, 2024A&A...691A.178B; EA ARC, 2023ApJ...945...69R; recalibration of early-cycle
     data via the Helpdesk, 2023PASJ...75..925F), or use NRAO SRDP (2024ApJ...969L...6Z).
   - If CASA cannot run in your environment, say so and stay with image products; do not fake a recalibration
     (in CosmicCoder agent runs, tclean was not installable on one HPC system).
   - Check: route recorded; if recalibrated, the new flux compared with the delivered flux
     (2013A&A...560A.103M: recalibrated, "consistent with delivered continuum flux").
6. **Fetch only what is needed, then shrink it.** Goal: data volume proportional to the question.
   - Download per MOUS and per product class (FITS, caltables plus raw EBs, or ARC-calibrated MS). After
     calibration, split out the target and SPWs you need and average: 10-30 GB reduced to 1-2 GB with 10 s time
     and 4-channel averaging (2021MNRAS.506.1978L, card); calibrated on-source data split off
     (2024ApJ...969...56M); calibrator fields only, "much smaller" (2024ApJ...969..102N, card).
   - Check smearing limits before averaging (general practice: bandwidth and time smearing grow with distance from
     phase centre and baseline length). Check: disk use logged; nothing fetched that is not in the selection.
7. **Prepare each dataset alone.** Goal: each dataset is good before it meets the others.
   - Self-calibrate each dataset first when bright enough, then combine (2016A&A...586A..70L); short-baseline
     data self-calibrated first, then concatenated with long baselines and self-calibrated together
     (2018ApJ...869L..41A; 2024ApJ...964..190L). Use `self-calibration` for settings.
   - Image each dataset separately and measure flux, position and noise. These numbers feed step 8.
8. **Run the pre-combination checks.** Goal: datasets agree on flux, weights, frequency, position and source
   state. Full table in `references/combination-checks.md`; the short version:
   - Flux: compare on overlapping uv ranges and rescale to a common reference if needed (2023A&A...676A...4C;
     2024A&A...687A.311A; 2023Natur.623..705S with `gencal`).
   - Weights: `statwt` before or after `concat` (2016ApJS..222....1F; 2017ApJ...850...83F; 2019ApJ...871...37H),
     or rescale to match noise variance (2017A&A...605A..42C).
   - Frequency: common channel width and bandwidth (Cycle 1 binned by 4 to match Cycle 3, Cycle 3 trimmed to the
     Cycle 1 bandwidth, 2019A&A...629A..29J); common frame (LSRK, 2021A&A...645A..49G).
   - Position: proper motion and phase centre (`fixvis`, `fixplanets`, `phaseshift`): realigned to Gaia DR2
     (2021MNRAS.506.1978L); offsets larger than one third of the extended-configuration beam corrected
     (2021A&A...648A..33M); Cycle 2 reference frame relabelled to ICRS (2023ApJ...954..197I).
   - Source state: is it variable between the dates? A blazar core was subtracted before combining cycles
     (2017ApJ...849...95B); lines taken eight years apart may see a changed background source
     (2024A&A...683A..62M).
   - uv coverage: match it when comparing bands or epochs (`uvsim` to common coverage, 2015ApJ...812..126C;
     baseline cuts, 2020ApJ...902...99I, 2021ApJ...907L..27A).
9. **Combine.** Goal: one dataset or one product, with a documented method.
   - `concat` in the uv plane is the most common route (56 of 301 listed "how combined" rows name concat;
     feather 43, `statwt` 10; my count). Joint `tclean` of several MSs is the other common route
     (2022MNRAS.515.1751W). The ALMA pipeline does not combine 12 m, 7 m and TP (2023PASP..135g4501H), so
     combination is your step. For TP and ACA use `array-combination`.
   - Image-plane combination when uv combination is not sensible: inverse-variance mean of separate continuum
     images (2019MNRAS.482.3135B); noise-weighted linear mosaicking of separate parts (2021ApJS..257...43L).
10. **Validate and record.** Goal: evidence that the combination helped and did not bias the result (see
    Verification checks), plus a provenance table (template in `references/combination-checks.md`).

## Parameter defaults and ranges

| Setting | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Absolute flux-scale uncertainty | 10% | 5% to 20% | ~86 of 155 listed values say 10% (my count) | 2016ApJS..222....1F, 2021A&A...648A..41V |
| Band 3-4 flux uncertainty | 5% | 5% | 3 excerpts | 2021A&A...648A..33M, 2018A&A...619A.161C, 2025ApJ...989...83B |
| Band 6 flux uncertainty | 5-10% | 5% to 10% | 3 excerpts | 2021ApJS..257...43L, 2025ApJ...989...83B |
| Band 7 flux uncertainty | 10% | 10% | 3 excerpts | 2021A&A...648A..33M, 2018A&A...619A.161C |
| Combined multi-configuration or early-cycle data | 15% | 15% to 20% | 2 excerpts | 2023A&A...674A.125B, 2014ApJ...796L..15S |
| Flux agreement to accept a dataset | within the stated uncertainty | ~10% vs SMA; within 10% | few | 2014ApJ...796L..15S, 2021A&A...648A..41V |
| Position offset to correct | > 1/3 of the extended beam | Gaia-based shifts; mas pointing offsets | few | 2021A&A...648A..33M, 2019MNRAS.482L..29D |
| Frequency tolerance in `concat` | default | `freqtol` 10 MHz | 1 | 2020A&A...641A..97V, 2025A&A...699A..80H |
| Relative weights | `statwt` recompute | manual rescale to noise; inverse variance | 10 statwt rows (my count) | 2017A&A...605A..42C, 2020ApJ...892L..18I |
| Calibration route | delivered pipeline calibration | revised scripts; ARC MS; full manual | ~120 pipeline vs 3 "manual" listed rows (my count) | 2018ApJ...869..126L, 2017ApJ...849...14S |
| CASA version for imaging | one modern version for all datasets | per-project versions for calibration | 4.7.2 (26), 5.4.1 (19), pack aggregate | 2025ApJ...985...84L, 2025A&A...699A..80H |
| Data volume, image products | <1 GB to a few GB | 1-10 GB for a dozen targets | card estimates | 2016PASJ...68..103F, 2021A&A...655A.113M |
| Data volume, one track (raw) | ~10-50 GB | few GB to 100 GB | card estimates | 2014ApJ...792...94D, 2012A&A...548A..69N |
| Data volume, multi-project | hundreds of GB to ~1 TB | up to several TB | card estimates | 2016ApJS..222....1F, 2021ApJS..257...43L |

Notes. The pack's proposal-cycle aggregate is dominated by 2015 (1074), 2016 (891) and 2013 (848) codes; 2011-2013
codes are 1789 of 5942 project-code entries (30%, my sum), so early-cycle calibration issues are common in
practice. The "2001" entry is an artefact. Per-band numbers above are from excerpts, not a corpus-wide count.

## Software

| Job | Tool | Evidence |
|---|---|---|
| Querying the archive, packages, restore | companion skill `working-with-alma-data`; astroquery | general practice |
| Restoring calibrated visibilities | `scriptForPI.py` in the delivered CASA version | 2019ApJS..244...40L, 2024MNRAS.529L...1J |
| Calibrated MS without restoring | EU/EA ARC service; NRAO SRDP | 2024A&A...691A.178B, 2023ApJ...945...69R, 2024ApJ...969L...6Z |
| Image products for many targets | JVO portal (15 pack lines, my grep) | 2017MNRAS.468.1769F, 2019ApJ...875...94H |
| Re-imaged archive products | ARI-L | 2024ApJ...976...29H, 2024ApJ...977..238B |
| Flux model and rescaling | `setjy` (Perley-Butler 2017, Butler-JPL-Horizons 2012), `gencal` | 2022JApA...43...83M, 2016ApJS..222....1F, 2023Natur.623..705S |
| Weights | `statwt` (and `oldstatwt` for older data) | 2017ApJ...835..174S, 2021Sci...371..713L |
| Alignment | `fixvis`, `fixplanets`, `phaseshift`, VisAlign | 2021MNRAS.506.1978L, 2024A&A...687A.311A, 2022MNRAS.513.5790C |
| Frequency matching | `cvel`, `mstransform`, `split` over common range | 2016ApJ...821L...8S, 2018ApJ...852..122H, 2023MNRAS.521.1045R |
| Combination | `concat` (56 rows), `tclean` joint imaging, `feather` (43 rows) | 2021A&A...646A..72H, 2023ApJ...948L...2Y |
| Flux measurement on products | `imfit` | 2024ApJ...974..279D |
| Moments from archive cubes | 3D-Barolo | 2024MNRAS.535..729P |

CASA is the default for everything above. Use the CASA version the package requires for restoring and a single
version for all later steps, as papers do (CASA 6.3.0 for all analysis after per-project pipeline calibration,
2025ApJ...985...84L; per-program pipeline versions 5.6.1 and 6.5.2, then 6.5.2 for concatenation,
2025A&A...699A..80H). PHANGS-ALMA found "little influence of the adopted CASA version" on its final results
(2021ApJS..257...43L).

## Pitfalls

- **Whole-project downloads.** In CosmicCoder agent runs an agent tried to fetch about 4 TB by project code when
  specific products were enough. Survey-scale projects are several TB (2021ApJS..257...43L, card; 75 EBs,
  2017A&A...605A.121M, card).
- **Old flux-calibrator models.** A poorly defined Ceres model was replaced by quasar calibrators
  (2024A&A...684A...4U); reprocessing with new flux model libraries gave more reliable flux calibration
  (2018A&A...616A.127R); a variable flux-calibrator quasar forced manual reduction (2020ApJ...904...78S). Check
  which calibrator and model each early-cycle MOUS used.
- **Science lines flagged in calibrator data.** When the calibrator is the science target, pipeline flags remove
  the lines: emission lines were unflagged for Titan (2016ApJ...821L...8S); absorption channels re-flagged and
  recalibrated (2024ApJ...969..102N).
- **Products that are not final science images.** Delivered images were under-cleaned and re-imaged
  (2020MNRAS.496.1834L); a pipeline cube had strong artefacts and the bandpass was redone (2024NatAs...8..256O);
  a published map was not primary-beam corrected (2016A&A...589A..20V). JVO first-look fluxes are pipeline-based,
  and per-star published fluxes were preferred where they existed (2021A&A...655A.113M).
- **Unequal weights across cycles.** Older data can carry weights that do not reflect noise: Cycle 1 weights
  adjusted with `statwt` before combination (2023ApJ...945...69R); `oldstatwt` reweighting (2021Sci...371..713L);
  survey visibilities needed per-spw weight rescaling (2023PASP..135f4503Z).
- **Inherited processing.** Reused survey or earlier-paper products carry choices you cannot see: calibration
  deferred to an earlier paper (2019A&A...623A..68T; 2016ApJ...832..178V); data used "as published by" another
  team (2019A&A...621L...5K). Read that paper's methods before comparing noise or flux.
- **Moving sources and epochs.** Proper motion smears or doubles a source if not corrected (2016ApJ...820L..40A;
  2019A&A...625A.118K). Variable sources should not be merged blindly (2024A&A...692A..86H; 2015A&A...577L...4V).
- **Missing short spacings in old or long-baseline data.** Flux of a line from long baselines only is a lower
  limit (2025ApJ...985...84L); filtering affects extended species without TP (2024A&A...684A...4U).
- **Settings the cards flag as not stated** (pack aggregate, phrasing variants not merged): CASA version 67,
  CASA and pipeline version 27, self-cal solution intervals 43 (+22 with iterations), flux calibrator and
  uncertainty 21, flux-scale uncertainty 20. When reusing such a paper's data, record these as unknown.

## Verification checks

What the papers did:

- **Calibrator sanity.** Phase calibrators imaged and fluxes compared with the ALMA calibrator database, point
  source confirmed (2015MNRAS.451.1141M); calibrator amplitudes flat in channel and time and phases near zero
  (2026ApJ..1001...33L).
- **Delivered versus reprocessed.** Recalibrated flux consistent with delivered flux (2013A&A...560A.103M);
  ALMA and ARI-L cubes gave compatible results (2024ApJ...977..238B); own imaging showed delivered data already
  optimal (2015MNRAS.452.2258D); self-cal tested and rejected when S/N did not improve (2021A&A...648A..41V).
- **Flux against earlier measurements.** Continuum flux compared with earlier SMA values (2015ApJ...810..112O);
  ALMA and SMA scales differ ~10%, within the adopted 20% (2014ApJ...796L..15S); inter-spw continuum mismatches of
  1-3% compared with expected relative calibration errors (2025ApJ...989...83B).
- **Noise and image quality.** rms close to thermal (2018ApJ...866..141K); S/N gain from self-cal reported per
  program (2025ApJ...985...84L); flux of the science source consistent with and without self-cal
  (2023ApJ...945L...3M).
- **uv-coverage effects.** A hot-spot flux 5% lower when Band 3 is imaged with Band 7 uv coverage
  (2016A&A...586A..70L).
- **Astrometry.** Point-source offset compared with Gaia DR2 accuracy, and background sources checked for
  smearing along the proper-motion direction (2021MNRAS.506.1978L).
- **Contaminated sources.** Beam shape differing from the synthesised beam flags confusion (2021A&A...655A.113M).

What an evaluator or referee adds (general practice):

- Each dataset's flux, position and noise measured alone, then the combined values; combined flux within the
  quadrature sum of the flux-scale uncertainties.
- A table of every MOUS considered, used or rejected, with reasons and the product level used.
- The adopted flux-scale uncertainty propagated into every flux, ratio and spectral index.
- Stop when the selected data meet the step-1 requirement and the checks pass. If a needed check cannot be run
  (no overlap in uv range, CASA not available), state the result as provisional and record the open item rather
  than adding more data indefinitely.

## Source cards

Full list: `references/sources.md` (1764 papers). Most informative for this workflow:

- 2016ApJS..222....1F: 66 archive maps from 18 projects, `statwt` then `concat`, 10% flux error
- 2025ApJ...985...84L: eight projects plus SMA, per-program self-cal, one CASA version for analysis
- 2025A&A...699A..80H: new plus archival data, per-program pipeline versions, `concat` defaults
- 2026MNRAS.551g1411H: 37 archival ALMA and VLA datasets, independent calibration, epochs for astrometry
- 2026ApJ..1001...33L: raw archival data recalibrated with observatory scripts, calibrator-amplitude check
- 2021ApJS..257...43L: survey combining many projects, CASA-version insensitivity, noise-weighted mosaics
- 2021A&A...648A..33M: align, rescale, correct offsets > 1/3 beam, per-band flux errors
- 2017ApJ...849...14S: raw data recalibrated with revised flux model and extra flagging
- 2024A&A...684A...4U: Ceres model replaced, archival configuration added with `concat`
- 2016A&A...586A..70L: calibrator scans from 13 Cycle 0 projects, self-cal before combining
- 2016ApJ...821L...8S: Titan calibration scans, unflagged lines, `fixplanets` and `cvel`
- 2024ApJ...969..102N: calibrator data from 33 projects, re-flagging for absorption lines
- 2015MNRAS.451.1141M: archive calibration used as delivered, calibrator flux check
- 2015ApJ...810..112O: delivered calibration inspected and kept
- 2021A&A...655A.113M: JVO first-look images for a mm SED sample, beam-shape check
- 2021MNRAS.506.1978L: Gaia realignment, `fixvis` and `fixplanets`, averaging to shrink data
- 2025ApJ...989...83B: archival survey across 14 projects, per-spw flux rescaling, per-band flux errors
- 2019A&A...629A..29J: channel binning and bandwidth trimming to match cycles
- 2023ApJ...945...69R: ARC-calibrated MSs, Cycle 1 weights fixed with `statwt`
- 2018ApJ...869...71Z: blind search on archive maps, re-reduction only where detected
- 2021A&A...653A..77P: QA2 products used, raw data reprocessed only to test artefacts
- 2023A&A...674A.125B: multi-configuration combination aligned on the stellar peak, 15% flux error
- 2020ApJ...904...78S: manual reduction for a variable flux calibrator
- 2024NatAs...8..256O: bandpass redone after pipeline-cube artefacts
- 2023PASP..135g4501H: pipeline does not combine 12 m, 7 m and TP
