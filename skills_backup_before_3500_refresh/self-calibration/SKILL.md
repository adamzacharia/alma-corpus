---
name: alma-self-calibration
description: "Plan, run and report phase and amplitude self-calibration of ALMA visibilities: what to calibrate on, the solution-interval ladder, minsnr/minblperant/refant, when to add an amplitude round, when to stop, and how to transfer solutions to line data. Use when an ALMA image is dynamic-range or phase-noise limited, when a bright continuum, line or maser is available as a model, when combining epochs or arrays, or when judging whether a paper's self-calibration was sound. Built from 419 ALMA papers (2012-2026)."
---

# Self-calibration of ALMA visibilities

Self-calibration uses the target's own emission as the gain model and solves for residual antenna phase (and
sometimes amplitude) errors left after phase referencing. In the corpus it is mostly done in CASA, phase-only
rounds come first, solution intervals usually shrink each round, and continuum solutions are often (not always)
transferred to the line data. The mistakes that matter most: (1) amplitude self-calibration on a weak, variable or
poorly modelled source, which changes the flux scale or imprints the model; (2) not stating the solution
intervals, rounds and reference antenna. "Self-calibration solution intervals" is the most frequent self-cal
category in the pack's "not stated" aggregate (63 cards); related categories (intervals and number of iterations
36, intervals and reference antenna 13, intervals and number of rounds 12) are listed separately and may overlap,
so do not add them.

> **Phase first, amplitude last (if at all). Shrink solint until S/N stops improving. Measure rms, peak and beam
> before and after every round. Decide per science product whether solutions go to the line data, and state the
> order of self-cal and continuum subtraction.**

## When to use

- The phase-referenced image is dynamic-range limited (stripes, sidelobes around a bright source). Examples:
  3C138 sidelobe/peak ratio fell from 17% to 0.6% at 241 GHz (2015ApJ...808L...1A); Sgr B2 reached dynamic
  range 18000 after 3 phase + 2 amplitude rounds (2018ApJ...853..171G).
- A bright compact continuum source is in the field: a disk, a stellar photosphere, an AGN core, a quasar
  (2016ApJ...820L..39N, 2017Sci...355.1285N), a planet or moon (2014ApJ...795L..30C, 2023PSJ.....4..142C).
- Continuum is weak but a strong line or maser is present: self-calibrate on the brightest channel or line
  (2012A&A...548A..69N, 2016ApJ...817..168H, 2017A&A...603A..92V, 2019A&A...628A..10B).
- Several epochs, tracks or configurations will be combined: self-calibrate each dataset first
  (2016A&A...586A..70L, 2020ApJ...892L..18I, 2020ApJ...898..146M).
- Solar snapshot imaging with pointing jitter: self-calibrate against the image from the whole observing period
  (2017ApJ...841L...5S).
- VLBI with ALMA, where station gains come from self-calibration to a model (2019ApJ...871...30I,
  2024MNRAS.534.3237M).

## When not to use

| Situation | What papers did instead |
|---|---|
| Target too faint for good gain solutions | Skipped it: "CIDA 12 too low S/N" (2024ApJ...966...59S); "SM1N too faint" (2014ApJ...797...27F). Selection rules use different quantities: image detection significance >=10 sigma (2017ApJ...851...83C), source flux density brighter than ~3 mJy (2016ApJ...823..160D), estimated S/N_selfcal > 3 (2025A&A...696A.150S) |
| Self-cal tested and gave no gain | Kept the pipeline data (2017A&A...603A..10B, tested at solint 30 s and shorter) |
| Source intrinsically variable within the track | Phase-only, no amplitude self-cal (2024MNRAS.534.3237M, Sgr A*); check light curve first (2024ApJ...966...59S) |
| Too little signal at high frequency | Some Band 9 datasets were not self-calibrated (2019ApJ...871...73H, 2014ApJ...796...82Z; the former validated by splitting data in time and uv range instead), while others were: on the strongest peak (2014A&A...567A.125G), antenna-based phase (2015ApJ...812..126C), separately per spw (2016ApJ...823...91S), phase-only on a combined continuum image (2024PSJ.....5..125T). Decide on signal and solution quality, not band |
| Lensed source modelled in the uv plane | Fit antenna phase offsets jointly with the lens model (2013ApJ...767..132H, 2016ApJ...826..112S) |
| Polarization of a faint point source | Use long solints; 2020ApJ...895...64L derived a minimum usable solint of about 35 s and attributed the earlier claimed polarization to instrumental systematics |
| Data missing flux (no short spacings) | 2015ApJ...804...37L did no amplitude self-cal because of the missing flux, and its two phase rounds were performed but not applied to the 12m data |

Self-calibration does not replace good phase referencing or flagging. If a round fails, keep the last calibration
state that passed your checks: 2020ApJ...898...10T kept its first 120 s phase round (~20% noise reduction) after a
second 30 s round and an amplitude+phase round did not help, and independently checked that the pipeline
calibration was fine. Fall back to the pipeline data only if no round improves the image (2017A&A...603A..10B).

## Steps

1. **Start from checked, aligned data.** Goal: a clean starting point. Method: pipeline-calibrated MS
   (2024Ap&SS.369...18M: pipeline, setjy, extra flagging, mstransform split); check the pipeline calibration
   (2020ApJ...898...10T). For multi-epoch data of a moving star, shift to a common phase centre with `fixvis`
   and `fixplanets` before self-cal (2018ApJ...852..122H, 2020ApJ...891...48H). Self-calibrate each execution
   or dataset separately, then combine (2016A&A...586A..70L, 2020ApJ...898..146M). Software: CASA.
2. **Build the self-cal dataset.** Goal: maximise S/N per solution. Method: line-free continuum channels from
   all spws (2018A&A...615A..28D, 2017A&A...601A...5H), averaged in frequency (128 to 8 channels per spw in
   2015A&A...577L...4V; 125 MHz channels in 2024ApJ...966...59S); combine spws in the solve (2020ApJ...898..146M,
   all 4 SPWs; 2020ApJ...892L..18I, spws combined). Line-rich sources: correct for continuum spectral index
   (2020MNRAS.498L..87B) and remember `findcont` can be conservative in line-rich fields (2025A&A...696A.150S).
   No usable continuum: use a strong line or maser channel (see When to use). Some papers time-bin
   first (60 s in 2018A&A...610A..24F). Record the exact channel ranges used for the self-cal model.
3. **Make the first model.** Goal: a model that contains only emission you trust. Method: shallow clean with a
   tight mask or small clean box on the bright emission (2015ApJ...806...17R, natural weighting and a small clean
   box; 2014ApJ...791L...6W, mask on the strong component only; 2017A&A...604A...6S, components >500 mJy only).
   Simple sources: a point source (2020ApJ...898..146M, the star; 2024MNRAS.534.3237M) or a disk at the
   expected brightness temperature for planets and moons (2023PSJ.....4..142C, 2024PSJ.....5..125T). Extended
   emission around a compact source: restrict the solve to long baselines (>150 klambda in 2015A&A...576A..41B;
   >50 klambda in 2015ApJ...802...69B; >150 m in 2016ApJ...827...68P; >250 klambda in 2017ApJ...843...83W).
   Software: `tclean` with `savemodel='modelcolumn'` (general practice) or `startmodel`.
4. **Phase-only rounds with a shrinking solint.** Goal: remove residual atmospheric phase. Method: `gaincal`
   `calmode='p'`, start long and shorten each round down to a few tens of seconds or the integration time;
   re-image deeper between rounds. Phase-only ladders stated as such: 600, 300, 150 s, then scan time
   (2016ApJ...818..158A); 5, 2, 1 min (2017Icar..286..289L); scan length, 30.25 s, integration
   (2017ApJ...850L..30Y); `inf` then `int` (2024A&A...686A.274V); full integration (>121 s) down to 2 s
   (2023PSJ.....4..142C). Ladders whose solution type the card does not state: whole observation, 350 s, 60 s
   (2019AJ....157..251T, type listed as not stated); 600 to 90 s in Band 4 and 1200 to 240 s in Band 6
   (2016ApJ...829L..35T). Not every first round is long: 2015ApJ...808...36M started phase-only at the record
   length (~6 s Band 3, ~3 s Band 6) and ALMAGAL uses `solint='int'` on every iteration while cleaning to 4x, 3x,
   then 2x rms (2025A&A...696A.150S). More ladders in `references/parameters.md`.
   **Scan length versus whole observation (general CASA practice):** `solint='inf'` with the default `combine=''`
   gives one solution per scan, not one per track; a whole-observation solution needs `combine='scan'` (and
   `'field'` for mosaics). The corpus documents both strategies (scan length in 2016ApJ...818..158A and
   2017ApJ...850L..30Y; whole observation in 2019AJ....157..251T; `inf` in 2024A&A...686A.274V without stating
   `combine`). Record the actual time span per solution and the number of solutions per antenna (2020ApJ...895...64L
   reports 14 solutions per polarization per antenna for its 20 min amplitude round).
5. **Optional amplitude round.** Goal: remove residual amplitude errors on very bright sources. Method: usually
   `calmode='ap'` after the phase rounds, previous phase table applied on the fly (2020ApJ...895...64L). A
   conservative starting point (my recommendation, not a literature rule) is one trial round with a solint
   longer than the last phase round, as in 60 s with gains normalised after ~3-6 s phase (2015ApJ...808...36M),
   scan length ~5 min after 30 s phase (2017ApJ...840...60B), 7 min after 6 s (2017ApJ...851..132C), 20 min with
   `gaintype='T'` after 2 min (2020ApJ...895...64L), 3600 s after 60 s (2015ApJ...814...22E). Documented
   alternatives: the same solint as the last phase round (30 s, 2017A&A...605A..21C; integration time,
   2017ApJ...850L..30Y; 2.048 s, 2020ApJ...894L..14L) and two amplitude+phase rounds (2018ApJ...853..171G).
   Some papers reserve it for the brightest sources (2019MNRAS.484.4239R) or selected targets
   (2017ApJ...845..170B) or drop it because it did not help (2020ApJ...891...48H, 2017ApJ...847...66O,
   2018ApJ...859..165S).
6. **Decide when to stop.** Rules seen: stop when image S/N stops improving (2023PSJ.....4..142C, down to 2 s);
   keep an iteration only if rms improves by >7.5% and the beam grows by <15% (2025A&A...696A.150S); stop after
   a round that brings no improvement (2012A&A...548A..69N, 2020ApJ...898...10T, 2016MNRAS.458L..29C).
   2024PSJ.....5..125T stopped once the "continuum phase distribution was on order +-10%"; the paper does not
   define that percentage for a phase, so it is not an executable threshold. If you use a phase-scatter rule,
   define it yourself (for example rms of gain phases per antenna in degrees at the final solint) and report it.
7. **Apply and transfer.** Goal: calibrate each science product with solutions that were validated for it.
   Method: write down the calibration chain before `applycal`: which input column or data state the solutions
   were derived on (pipeline-calibrated, time-binned, frequency-averaged), whether each table is incremental (solved
   with earlier tables applied on the fly) or a replacement, the `spwmap` from the solved (often averaged or
   combined) spws to the target spws, and what happens to data whose solutions were flagged (`applymode`, for
   example flag versus calonly; general CASA practice). Mapping matters: 2017A&A...600A..72F derived solutions
   on a TDM window and applied them to FDM windows; 2018A&A...616A..34H applied solutions from one configuration
   to all. Then branch by product:
   - **Continuum-derived solutions to line data.** Common: by my regex count over the pack's 391
     `self_calibration` key-parameter lines (lines containing "appl" or "transfer" and "line", "spw", "cube",
     "CO" or "channels", excluding "not applied/used"), 69 transfer solutions beyond the self-cal data, mostly to
     line windows or cubes, a few to other spws or "all data" (2013Sci...341..630Q, 2017A&A...597A..32V,
     2018ApJ...859..111H, 2024PSJ.....5..125T).
   - **Line data kept off self-cal.** 5 of the 391 lines (regex "not applied/used/transferred to line/cube/CO",
     "none for cubes", "continuum only"): explicit in 2013Natur.493..191C, 2016ApJ...833...41Z,
     2018ApJ...853..171G and 2024ApJ...966...59S (not applied to CO); 2020ApJ...893...51S says only "continuum
     only". Separately, 2017A&A...604A...6S did not use its self-calibrated images for continuum analysis.
   - **Order of continuum subtraction.** Either: apply solutions, then `uvcontsub` and image lines
     (2018ApJ...852..122H, 2018ApJ...865...13T); or apply to continuum-subtracted data (2018ApJ...863L..35M,
     2019A&A...623L...6P, 2020A&A...644A.119P); or, for line-based self-cal, subtract continuum first and
     self-calibrate on the strongest line feature (2012A&A...548A..69N). State which.

## Parameter defaults and ranges

Counts below are my counts over the pack's key-parameter section unless marked as pack aggregates. That section
has 391 `processing.calibration.self_calibration = ...` lines, one per paper (counted with grep). Rows marked
"examples" are not exhaustive counts. Where a card does not state phase-only versus amplitude+phase, the row says
"type not stated" rather than guessing. A requested `solint` and the integration duration are different things: a
requested solint shorter than the dump time still yields one solution per integration (general CASA practice).

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Mode sequence | phase-only rounds, then optionally amplitude+phase | phase-only only to 3 phase + 2 amp+phase | "phase-only"/"phase only" in 141 of 391 lines; an amplitude term ("amp", "amplitude", "ap") in 128 (my regex counts; overlapping, and the amplitude count includes "amplitude did not help") | 2015ApJ...806...17R, 2017A&A...602L..10O, 2018ApJ...853..171G |
| Phase rounds | 1-3 | 1 to 6 | examples | 1: 2015ApJ...798L..23K, 2018MNRAS.475.4924K; 4: 2017ApJ...836..223W, 2017ApJ...842L...9H; 6: 2024MNRAS.534.3237M |
| First phase solint | scan length, `inf`, or several minutes | record length (~3-6 s, 2015ApJ...808...36M) or `int` (2025A&A...696A.150S) up to whole observation (2019AJ....157..251T, type not stated) | examples | phase-only: 2016ApJ...818..158A (600 s), 2015ApJ...814...22E (600 s), 2017A&A...600A..72F (300 s), 2020ApJ...898...10T (120 s); type not stated: 2016ApJ...829L..35T (1200 s B6) |
| Final phase solint | integration time or 6-60 s | phase-only: 2 s (2023PSJ.....4..142C) to 2 min (2020ApJ...895...64L); type not stated: up to 240 s (2016ApJ...829L..35T, B6) | examples | 2020ApJ...894L..14L (2.048 s, the shortest integration), 2018A&A...609A..47P (6 s), 2017A&A...602L..10O (15 s), 2016A&A...586A..99H (60 s, type not stated); MIRIAD 0.01 min requested interval, type not stated (2016A&A...593A..44L) |
| Amplitude solint | longer than the last phase round, but not always | integration time (2017ApJ...850L..30Y; 2.048 s in 2020ApJ...894L..14L) to 3600 s (2015ApJ...814...22E) | examples | 2015ApJ...808...36M (60 s), 2017A&A...605A..21C (30 s), 2020ApJ...898..146M ("amplitude round", ~370 s), 2020ApJ...895...64L (20 min) |
| `minsnr` (per gain solution) | 2-3 | 2 to 3 | 4 | 2016ApJ...818..158A (2), 2017A&A...605A..21C (2), 2025A&A...696A.150S (2.5), 2020ApJ...892L..18I (3; 2 for 3-antenna solutions) |
| `minblperant` | 4 | 4 | 2 | 2016ApJ...818..158A, 2017A&A...605A..21C |
| `refant` | a named central antenna | DA41, DA59, DV11; `refantmode='strict'` | 4 | 2018A&A...610A..24F, 2017A&A...600A..72F, 2017A&A...605A..21C, 2020ApJ...895...64L |
| Amp `gaintype` | `T` | `T` | 2 | 2020ApJ...895...64L, 2016A&A...593A..61M |
| Gate: ALMAGAL's estimated self-cal S/N (the pack does not give its formula) | S/N_selfcal > 3 | | 1 | 2025A&A...696A.150S |
| Gate: image detection significance (peak / image rms) | >= 10 sigma | | 1 | 2017ApJ...851...83C |
| Gate: source flux density | brighter than ~3 mJy | | 1 | 2016ApJ...823..160D |
| Accept rule | rms down >7.5%, beam up <15% | | 1 | 2025A&A...696A.150S |
| uv cut for the solve | long baselines only when extended emission is unmodelled | >150 m to >250 klambda | 4 | 2015A&A...576A..41B, 2015ApJ...802...69B, 2016ApJ...827...68P, 2017ApJ...843...83W |

The cards rarely state `combine`, `solnorm` or `refant`; treat any value you choose for those as your own
decision and report it.

### What self-calibration bought (reported improvements)

| Gain reported | Paper |
|---|---|
| rms 36 to 16 mJy/beam (line-free), 100 to 18 mJy/beam (line channels) | 2015ApJ...806...17R |
| continuum rms down ~40x | 2017ApJ...851..132C |
| rms down ~10x (3C138) | 2015ApJ...808L...1A |
| peak S/N 150 to 1320 at 346 GHz | 2014ApJ...791L...6W |
| SNR 340 to 547 | 2016Sci...353.1519P |
| dynamic range ~120 to ~250 | 2020ApJ...892L..18I |
| SNR x1.8; peak S/N 28 to 37 | 2018ApJ...859..111H; 2018MNRAS.475.4924K |
| rms ~20%, 14%, ~25%, <=10% | 2020ApJ...898...10T; 2018ApJ...865...13T; 2017Sci...355.1285N; 2017ApJ...838..114K |
| CO(1-0) S/N x1.2; not possible at CO(3-2) | 2016ApJ...832..148V |
| ALMAGAL: 81% (7M), 66% (TM2), 45% (TM1) of eligible fields improved | 2025A&A...696A.150S |

These are individual case results with different metrics (image rms, peak S/N, dynamic range), not a validated
prediction by source brightness or morphology; compare like with like. The one survey-scale result is that the
ALMAGAL success rate falls as the array gets more extended (2025A&A...696A.150S).

## Software

Pack aggregates over matched steps: CASA 281, tclean 24, AIPS 13, GILDAS 7, MIRIAD 7, gaincal 6, eht-imaging 2,
applycal 2, uvcontsub 2, DIFMAP/difmap 2, Obit/obit 2.

| Tool | Used for | Examples |
|---|---|---|
| CASA `tclean` (or the older `clean`) + `gaincal` + `applycal` | the standard loop | `tclean`/`gaincal`/`applycal`: 2023PSJ.....4..142C; `clean`/`gaincal`/`applycal`: 2017ApJ...850L...2A; CASA pipeline then self-cal: 2024Ap&SS.369...18M |
| CASA `fixvis`, `fixplanets` | common phase centre before self-cal and combination | 2018ApJ...852..122H, 2020ApJ...891...48H |
| CASA scripted automatic loop | survey-scale self-cal with accept/reject rules | 2025A&A...696A.150S |
| MIRIAD `selfcal` | mosaics (`options=mosaic`) and point sources | 2016A&A...593A..44L, 2018A&A...614A..42M, 2019A&A...632A..66O |
| GILDAS | phase self-cal on compact sources (IRAM-style reduction) | 2017A&A...597L...5B, 2018A&A...614A..58B |
| AIPS, Obit | VLBI hybrid mapping; JVLA companion data; long-baseline tests | 2024MNRAS.534.3237M, 2016PASJ...68L...7T, 2015ApJ...808...36M, 2015ApJ...808L...1A |
| DIFMAP | iterative self-cal of compact radio sources | 2016A&A...593L..19M |
| eht-imaging | VLBI amplitude self-cal to a Gaussian or closure image | 2019ApJ...871...30I |
| custom MCMC lens code | antenna phases fit jointly with a lens model | 2013ApJ...767..132H |

The CASA version is flagged as not stated in 51 cards (pack aggregates). Record it; `gaincal` defaults changed
across versions (general practice).

## Pitfalls

- **Unreported settings.** In the pack's "not stated" aggregate the self-cal categories are, with their exact
  labels: "self-calibration solution intervals" 63; "... solution intervals and number of iterations" 36; "...
  solution intervals and reference antenna" 13; "... solution intervals and number of rounds" 12; "...
  solution interval" 8. These are category counts that may overlap, not unique cards. Line-free channel
  selection and continuum subtraction details, and image size, cell size, masks and clean thresholds, also recur
  across many separately worded categories (for example "line-free channels and continuum subtraction method"
  17, "line-free channels and uvcontsub fit order" 4, "image size and cell size" 21). Report, per round: mode,
  solint and the actual time span per solution, `combine`, `gaintype`, `minsnr`, `minblperant`, `refant`, uv
  range, `solnorm`/normalisation, and the model (mask, clean threshold, deconvolver). Report once: the channel
  ranges used for the self-cal data, the continuum-subtraction channels and fit order, and the calibration
  chain used in `applycal` (Step 7).
- **Amplitude self-cal changes the flux scale.** Measure it: 2015ApJ...808...36M normalised gains and found <0.7%
  (ALMA) and <0.5% (JVLA) amplitude change. If the source is variable or the model is incomplete, skip it
  (2024MNRAS.534.3237M, 2015ApJ...804...37L).
- **Model imprinting.** Self-calibrating to a model can create the model's structure. 2024MNRAS.534.3237M
  self-calibrated noise and point-source data with ring models and recovered rings, showing how a ring can be
  an artifact. 2013ApJ...767..132H used simulations to show that fitting the lens model and antenna phases
  together recovers the input antenna phases without bias; the pack does not show a test of bias in the lens
  parameters themselves. Start from a conservative mask and let the model grow round by round.
- **Too-short solint on faint data.** Noise-driven phase solutions raise the apparent peak and can fake
  polarization; 2020ApJ...895...64L required solint of at least ~35 s. Watch the fraction of flagged solutions
  at `minsnr` (ALMAGAL notes data that fail `minsnr=2.5`, 2025A&A...696A.150S).
- **Beam and astrometry change.** ALMAGAL rejects a round if the beam grows >15% (2025A&A...696A.150S).
  Phase-only self-cal ties positions to the starting model (general practice): 2017A&A...608A..38O corrected
  ~0.1 arcsec offsets with the continuum; 2020ApJ...898..146M re-centred on the fitted star. Check astrometry
  against phase-referenced data or an external position (2018A&A...615A..28D adopted 17 mas from check
  sources).
- **Line contamination in the self-cal data.** Continuum channels must be line-free. ALMAGAL reports that
  `findcont` is conservative in line-rich sources and lists the absence of manual continuum ranges as a
  limitation (2025A&A...696A.150S); 2020MNRAS.498L..87B corrected for the continuum spectral index. My
  recommendation, beyond what those papers did: inspect the spectra and set explicit line-free ranges in
  line-rich fields, and report them.
- **High frequency and long baselines.** Feasibility depends on the signal and the quality of the solutions,
  not on the band alone. Band 9 cases go both ways: no self-cal in 2019ApJ...871...73H and 2014ApJ...796...82Z;
  self-cal on the strongest peak (2014A&A...567A.125G), antenna-based phase (2015ApJ...812..126C), separate
  per-spw solutions (2016ApJ...823...91S) and phase-only on a combined continuum image (2024PSJ.....5..125T). On
  15 km baselines self-cal was "limited" for HL Tau and absent for SDP.81 (2015ApJ...808L...1A).
- **Polarization.** Short solints can create spurious polarization (2020ApJ...895...64L, minimum ~35 s); the
  same paper solved amplitude gains per polarization with `gaintype='T'` and kept the cross-hand phase fixed, and
  left the origin of time-varying systematics such as XY phase uninvestigated. Check that self-cal does not
  change the XX/YY (or parallel-hand) ratio and keep cross-hand phase and leakage calibration separate from
  self-cal (general practice). Self-cal cannot remove polarization-fraction bias from spatial filtering:
  2024A&A...686A.274V notes that resolved-out CO flux can overestimate polarization fractions by a factor 2-3.
- **Self-calibrated image used for the wrong product.** 2017A&A...604A...6S self-calibrated only on bright
  components and did not use the self-calibrated images for continuum analysis; decide per science product.
- **Missing flux is not fixed by self-cal.** Interferometric filtering limits remain (2016ApJ...832..148V
  recovered 43% of single-dish flux); amplitude self-cal against an incomplete model can make it worse.

## Verification checks

What papers used:

- rms, peak and beam before and after each round (2025A&A...696A.150S); dynamic range before/after
  (2020ApJ...892L..18I, 2023PSJ.....4..142C, ~580 final).
- Flux-scale stability: amplitude change from self-cal <0.7% (2015ApJ...808...36M); self-calibrated fluxes
  within 5% across datasets in a band (2018ApJ...852..122H); visibility amplitudes within 5% on overlapping
  spatial frequencies (2020ApJ...891...48H); amplitude agreement <~10% between cycles (2020ApJ...892L..18I).
- External flux comparison: Herschel SPIRE (2015ApJ...806...17R), SCUBA-2 (2018MNRAS.475.4924K), SMA
  (2015ApJ...810..112O), IRAM 30m (2018ApJ...865...13T).
- Extra rounds tried and shown not to help (2012A&A...548A..69N, 2020ApJ...898...10T).
- Split data in time, uv range and polarization to test calibration (2019ApJ...871...73H, Band 9 within 6%).
- Simulations: recovery of input antenna phases under joint lens fitting (2013ApJ...767..132H); ring
  imprinting from self-cal on noise and point-source data (2024MNRAS.534.3237M).
- Independent image comparison: ALMA vs VLA images of 3C138 agree to a few percent (2015ApJ...808L...1A).

What a careful referee adds:

- Ask for the full solint ladder, mode per round, `minsnr`, `refant`, and the fraction of flagged solutions.
- Plot the gain phases per antenna: smooth, time-correlated phases mean real atmosphere; random scatter at the
  shortest solint means you are fitting noise.
- Compare peak and integrated flux before and after: phase-only self-cal should raise the peak modestly and
  leave the integrated flux of a well-modelled source nearly unchanged (general practice).
- For claims of faint structure, image with and without self-cal and with a different starting model.
- Check that line results do not depend on whether continuum solutions were transferred.

## Source cards

Full list: `references/sources.md` (419 papers). Most informative for this technique:

- 2025A&A...696A.150S: automatic phase-only loop, S/N gate, rms/beam accept rule, success rates by array.
- 2016ApJ...818..158A: 4-step phase ladder 600/300/150 s/scan, minblperant=4, minsnr=2.
- 2017A&A...605A..21C: 2 phase + 1 amp, solints 500/30/30 s, refant, minsnr.
- 2020ApJ...895...64L: phase 10 and 2 min, amp 20 min `T`, minimum solint for polarization.
- 2015ApJ...808...36M: record-length phase then 60 s amp, normalised gains, amplitude scale check.
- 2015ApJ...806...17R: 2 phase + 1 amp with quantified noise drop in line and line-free channels.
- 2017ApJ...851..132C: 30 s, 6 s phase then 7 min amp; ~40x rms drop.
- 2020ApJ...898..146M: per-execution point-source model self-cal on Vega, all 4 spws, 3 phase rounds then an
  amplitude round.
- 2023PSJ.....4..142C: disk start model, solint down to 2 s, stop on S/N.
- 2024PSJ.....5..125T: Band 9 phase-only self-cal on a disk model, loosely defined phase-scatter stop, transfer
  to line data.
- 2019AJ....157..251T: whole-observation, 350 s, 60 s ladder on Neptune (solution type not stated).
- 2020ApJ...898...10T: one 120 s round; further rounds and amplitude did not help.
- 2024MNRAS.534.3237M: phase-only hybrid mapping, model-imprinting simulation.
- 2013ApJ...767..132H: antenna phases fit jointly with a lens model; simulations recover input phases.
- 2018ApJ...853..171G: 3 phase + 2 amp, continuum only, dynamic range 18000.
- 2017A&A...600A..72F: TDM-derived solutions applied to FDM windows.
- 2018ApJ...852..122H: fixvis/fixplanets alignment, flux consistency check.
- 2024ApJ...966...59S: self-cal only where it helped, skipped for low-S/N sources.
- 2017A&A...603A..92V: self-cal on an SiO maser channel applied to all spws.
