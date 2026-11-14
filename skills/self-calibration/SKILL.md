---
name: alma-self-calibration
description: "Plan, run and report phase and amplitude self-calibration of ALMA visibilities: what to calibrate on, the solution-interval ladder, minsnr/minblperant/refant/combine/applymode, when to add an amplitude round, when to stop, and how to transfer solutions to line data. Use when an ALMA image is dynamic-range or phase-noise limited, when a bright continuum, line or maser is available as a model, when combining epochs or arrays, or when judging whether a paper's self-calibration was sound. Built from 896 ALMA papers (2012-2026)."
---

# Self-calibration of ALMA visibilities

Self-calibration uses the target's own emission as the gain model and solves for residual antenna phase (and
sometimes amplitude) errors left after phase referencing. In the corpus it is mostly done in CASA, phase-only
rounds come first, solution intervals usually shrink each round, and continuum solutions are often (not always)
transferred to the line data. The mistakes that matter most: (1) amplitude self-calibration on a weak, variable or
poorly modelled source, which changes the flux scale or imprints the model; (2) not stating the solution
intervals, rounds and reference antenna, the most frequent self-cal gap in the pack's "not stated" aggregate
(category counts in Pitfalls).

> **Phase first, amplitude last (if at all). Shrink solint until S/N stops improving. Measure rms, peak and beam
> before and after every round. Decide per science product whether solutions go to the line data, and state the
> order of self-cal and continuum subtraction. Phase-only self-cal gives up absolute astrometry.**

## When to use

- The phase-referenced image is dynamic-range limited (stripes, sidelobes around a bright source). Examples:
  3C138 sidelobe/peak ratio fell from 17% to 0.6% at 241 GHz (2015ApJ...808L...1A, card); Sgr B2 reached dynamic
  range 18000 after 3 phase + 2 amplitude rounds (2018ApJ...853..171G).
- A bright compact continuum source is in the field: a disk, a stellar photosphere, an AGN core, a quasar
  (2016ApJ...820L..39N, 2017Sci...355.1285N; 2024ApJ...971L..33K pointed at a mm-bright QSO to allow it), a
  planet or moon (2014ApJ...795L..30C, 2023PSJ.....4..142C).
- Continuum is weak but a strong line or maser is present: self-calibrate on the brightest channel or line
  (2012A&A...548A..69N, 2016ApJ...817..168H, 2017A&A...603A..92V, 2023ApJ...948..134P, 3 maser channels, 60 s).
- Several epochs, tracks or configurations will be combined: self-calibrate each dataset first, then the
  combination (2016A&A...586A..70L, 2020ApJ...898..146M, 2018ApJ...869L..41A, 2024A&A...689A.145S).
- Solar snapshot imaging with pointing jitter: self-calibrate against the image from the whole observing period
  (2017ApJ...841L...5S), then per-slot 20 s images as models (2018ApJ...863...96Y).
- VLBI with ALMA, where station gains come from self-calibration to a model (2019ApJ...871...30I,
  2024MNRAS.534.3237M).

## When not to use

| Situation | What papers did instead |
|---|---|
| Target too faint for good gain solutions | Skipped it: "CIDA 12 too low S/N" (2024ApJ...966...59S); "SM1N too faint" (2014ApJ...797...27F); attempted and not adopted for lack of S/N (2025A&A...694L..15H, 2021ApJ...910...53V, 2021ApJ...909...98Y, 2026A&A...707A.255C). Gates use different quantities; see the gate rows in the parameter table |
| Self-cal tested and gave no gain | Kept the pipeline data (2017A&A...603A..10B, card, tested at solint 30 s and shorter) |
| Complex structure the model cannot capture | 2024PASJ...76...54L skipped self-cal because it expected artifacts from the complicated Sgr B2(N) substructure |
| Source intrinsically variable within the track | Phase-only, no amplitude self-cal (2024MNRAS.534.3237M, Sgr A*); check light curve first (2024ApJ...966...59S); or model the variable point source separately (see Pitfalls) |
| Too little signal at high frequency | Some Band 9 datasets were not self-calibrated (2019ApJ...871...73H, 2014ApJ...796...82Z; the former validated by splitting data in time and uv range instead), while others were: on the strongest peak (2014A&A...567A.125G), antenna-based phase (2015ApJ...812..126C), separately per spw (2016ApJ...823...91S), phase-only on a combined continuum image (2024PSJ.....5..125T), on the CO(6-5) peak (2024A&A...682L...5G). Decide on signal and solution quality, not band |
| Lensed source modelled in the uv plane | Fit antenna phase offsets jointly with the lens model (2013ApJ...767..132H, 2016ApJ...826..112S) |
| Polarization of a faint point source | Use long solints; 2020ApJ...895...64L derived a minimum usable solint of about 35 s and attributed the earlier claimed polarization to instrumental systematics |
| Data missing flux (no short spacings) | 2015ApJ...804...37L (card) did no amplitude self-cal because of the missing flux, and its two phase rounds were performed but not applied to the 12m data |
| Absolute positions are the science | 2021AJ....162...14A used phase self-cal only for the A-B separation, not for absolute positions |

Self-calibration does not replace good phase referencing or flagging. If a round fails, keep the last calibration
state that passed your checks: 2020ApJ...898...10T kept its first 120 s phase round (~20% noise reduction) after
a 30 s round and an amplitude+phase round did not help, and checked the pipeline calibration independently. Fall
back to the pipeline data only if no round improves the image (2017A&A...603A..10B).

## Steps

1. **Start from checked, aligned data.** Goal: a clean starting point. Method: pipeline-calibrated MS
   (2024Ap&SS.369...18M: pipeline, setjy, extra flagging, mstransform split); check the pipeline calibration
   (2020ApJ...898...10T). For multi-epoch data of a moving star, shift to a common phase centre with `fixvis`
   and `fixplanets` (2018ApJ...852..122H, 2020ApJ...891...48H; `phaseshift` in 2024A&A...687A.311A).
   Self-calibrate each execution or dataset separately, then combine (2016A&A...586A..70L, 2020ApJ...898..146M).
   Multi-configuration data are staged: compact first, then the combination continues the ladder
   (2018ApJ...869L..41A, 2021A&A...649A.122P, 2025A&A...698A.115R; per-EB round and EB alignment first in
   2025ApJ...989...30Z). Software: CASA.
2. **Build the self-cal dataset.** Goal: maximise S/N per solution. Method: line-free continuum channels from
   all spws (2018A&A...615A..28D), averaged in frequency (128 to 8 channels per spw in 2015A&A...577L...4V;
   125 MHz in 2024ApJ...966...59S; 250 MHz in 2025A&A...698A.115R). Disk papers first flag a window around each
   line: +-15 km/s (2025ApJ...989...30Z), +-20 (2021AJ....162...99F), +-25 (2021A&A...649A.122P), +-30
   (2025A&A...698A.115R). Combine spws (and often scans and polarizations) in the solve when S/N is short
   (2020ApJ...898..146M, 2020ApJ...892L..18I, 2024A&A...687A.311A first round). Line-rich sources: correct for
   continuum spectral index (2020MNRAS.498L..87B) and remember `findcont` can be conservative in line-rich fields
   (2025A&A...696A.150S, card). No usable continuum: use a strong line or maser channel (see When to use). Record the
   exact channel ranges used for the self-cal model.
3. **Make the first model.** Goal: a model that contains only emission you trust. Method: shallow clean with a
   tight mask or small clean box on the bright emission (2015ApJ...806...17R; 2014ApJ...791L...6W, mask on the
   strong component only; 2017A&A...604A...6S (card), components >500 mJy only; 2016ApJ...833..219P, CLEAN components
   >3 sigma). CAMPOS found user-drawn masks gave better S/N and a cleaner noise pattern than automasking
   (2024ApJ...973..138H). Simple sources: a point source (2020ApJ...898..146M, the star; 2024MNRAS.534.3237M) or a
   disk at the expected brightness temperature for planets and moons (2023PSJ.....4..142C, 2024PSJ.....5..125T,
   2025PSJ.....6..183C). Extended emission around a compact source: restrict the solve to long baselines (>150
   klambda in 2015A&A...576A..41B; >50 klambda in 2015ApJ...802...69B; >150 m in 2016ApJ...827...68P). Weighting:
   CAMPOS self-calibrated once per final weighting because matching them gave the best S/N (2024ApJ...973..138H);
   others self-calibrated at one robust and imaged at another (2025A&A...702A..18D, 2024ApJ...971L..33K).
   Software: a starting image can be given to `tclean` as `startmodel` (Callisto as a Lambertian disk,
   2025PSJ.....6..183C). Separately, the solver needs model visibilities: save them (`tclean`
   `savemodel='modelcolumn'`, or `ft` of the model image) and check their flux against the model image before
   `gaincal` (general CASA practice).
4. **Phase-only rounds with a shrinking solint.** Goal: remove residual atmospheric phase. Method: `gaincal`
   `calmode='p'`, start long and shorten each round down to a few tens of seconds or the integration time;
   re-image deeper between rounds. Ladders: `inf` then `int` (2024A&A...686A.274V, 2022PASJ...74..738T); halve the
   solint each round from `inf` or scan length to `int` (2024ApJ...973..138H, 2022MNRAS.513.5790C,
   2025A&A...702A..18D); fixed lists such as 600, 300, 150 s, scan (2016ApJ...818..158A) or 60, 30, 18, 6 s
   (2018ApJ...869L..41A). Not every first round is long: record length (2015ApJ...808...36M); ALMAGAL uses `int`
   every iteration while cleaning to 4x, 3x, then 2x rms (2025A&A...696A.150S, card). A data-driven floor: the shortest
   solint giving S/N > 3 on >90% of antennas (2024A&A...688A.110S). More ladders, including those of unstated
   type, in `references/parameters.md`.
   **Scan length versus whole observation (general CASA practice):** `solint='inf'` with the default `combine=''`
   gives one solution per scan, not one per track; a whole-observation solution needs `combine='scan'`. In a
   mosaic, add `'field'` only if one model covers all pointings and shared gains are justified; per-pointing
   solves are the alternative (2020PASP..132i4501H, one phase round on every pointing). Both appear: scan length (2016ApJ...818..158A, 2026MNRAS.549g1100P); whole
   observation (2019AJ....157..251T); `inf` with `combine='scan'` (2023A&A...676A...4C, 2026A&A...705A..96M);
   `combine='scan,spw'` as fallback when per-scan `inf` fails (2023PSJ.....4..206R, 2024ApJ...973..138H). Record
   the time span per solution and solutions per antenna (2020ApJ...895...64L reports 14 per polarization per
   antenna for its 20 min amplitude round).
5. **Optional amplitude round.** Goal: remove residual amplitude errors on very bright sources. Method: usually
   `calmode='ap'` after the phase rounds, previous phase table applied on the fly (2020ApJ...895...64L). A
   conservative starting point (my recommendation, not a literature rule) is one trial round with a solint
   longer than the last phase round: 60 s with gains normalised after ~3-6 s (2015ApJ...808...36M), 7 min after
   6 s (2017ApJ...851..132C), 20 min gain mode `T` after 2 min (2020ApJ...895...64L), `inf` after `int` (2024ApJ...961....4B,
   2026A&A...705A..96M). Documented
   alternatives: the same solint as the last phase round (30 s, 2017A&A...605A..21C, card; integration time,
   2017ApJ...850L..30Y; 2.048 s, 2020ApJ...894L..14L) and two amplitude+phase rounds (2018ApJ...853..171G,
   2025A&A...698A.115R). Guards seen: flag amplitude solutions with S/N < 5 and amplitude gains off by >20%
   (2025ApJ...989...30Z); `solnorm=True` first, then `False` (2026A&A...705A..96M). Some papers reserve
   amplitude for bright sources (2019MNRAS.484.4239R; quasars >20 mJy in 2026A&A...708A.146P) or drop it because
   it did not help or lowered the dynamic range (2020ApJ...891...48H, 2017ApJ...847...66O, both card; 2025ApJ...989...83B).
6. **Decide when to stop.** Rules seen: stop when image S/N (or image and visibility residuals) stop improving
   (2023PSJ.....4..142C, down to 2 s; 2018ApJ...869...17L; 2024ApJ...971L..33K; 2012A&A...548A..69N); keep the
   best-S/N image among the rounds (2024PASJ...76..437Y); keep an iteration only if rms improves by >7.5% and the
   beam grows by <15% (2025A&A...696A.150S, card), or if S/N rises and the beam area changes by <5%
   (2024ApJ...973..138H). 2024PSJ.....5..125T stopped once the "continuum phase distribution was on order +-10%";
   the paper does not define that percentage for a phase, so it is not an executable threshold. If you use a
   phase-scatter rule, define it yourself (for example rms of gain phases per antenna in degrees) and report it.
7. **Apply and transfer.** Goal: calibrate each science product with solutions that were validated for it.
   Method: write down the calibration chain before `applycal`: which input column or data state the solutions
   were derived on (pipeline-calibrated, time-binned, frequency-averaged), whether each table is incremental (solved
   with earlier tables applied on the fly) or a replacement, the `spwmap` from the solved (often averaged or
   combined) spws to the target spws, and what happens to data whose solutions were flagged (`applymode='calonly'`
   in 2018ApJ...869L..41A, 2020ApJ...890..130T, 2026MNRAS.552g1700S). Mapping matters: 2017A&A...600A..72F
   applied TDM-derived solutions to FDM windows; 2018A&A...616A..34H applied one configuration's solutions to all.
   Then branch by product:
   - **Continuum-derived solutions to line data.** Common: 50 of the 330 shown `self_calibration` lines transfer
     solutions beyond the self-cal data, mostly to line windows or cubes (my regex: "appl" or "transfer" plus
     "line", "spw", "cube", "CO" or "channels", excluding "not applied/used"; 2013Sci...341..630Q,
     2017A&A...597A..32V, 2021ApJ...917...99Y, 2026A&A...709A..93D, 2024PSJ.....5..125T).
   - **Line data kept off self-cal.** 3 of the 330 lines (regex "not applied/used/transferred to line/cube/CO",
     "none for cubes", "continuum only"): 2013Natur.493..191C, 2015ApJ...808L...3A and 2018ApJ...853..171G.
     Outside the shown lines: 2016ApJ...833...41Z and 2024ApJ...966...59S (not applied to CO).
   - **Order of continuum subtraction.** Either: apply solutions, then `uvcontsub` and image lines
     (2018ApJ...852..122H, 2024ApJ...971L..33K); or apply to continuum-subtracted data (2018ApJ...863L..35M,
     2020ApJ...904...77G, 2023A&A...678A.137C); or, for line-based self-cal, subtract continuum first and
     self-calibrate on the strongest line feature (2012A&A...548A..69N). State which.

## Parameter defaults and ranges

Counts are my grep counts over the pack's key-parameter section unless marked as pack aggregates. That section
is truncated (700 lines shown, "751 more" not shown) and has 330 `processing.calibration.self_calibration = ...`
lines, so counts cover a subset of the 896 papers. "Examples" rows are not exhaustive. "(card)" = the pack only
lists that paper bibliographically and the value was checked in its card. `minsnr`/`minblperant` rows: lines in
that section naming a per-solution S/N or baselines-per-antenna cutoff, plus card examples. "Type not stated" = the
card does not say phase-only or amplitude+phase. A requested `solint` shorter than the dump time still yields one
solution per integration (general CASA practice).

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Mode sequence | phase-only rounds, then optionally amplitude | illustrative, not bounds: p only (4 p, 2016ApJ...818..158A, card); p, p, ap (2015ApJ...806...17R); 3 p + 2 ap (2018ApJ...853..171G, 2024A&A...687A.308S); 7 p then amp trials (2026A&A...705A..96M) | "phase-only"/"phase only" in 106 of 330 lines; `amp` or a whole-word `ap` (case-insensitive) in 101 (my regex counts; overlapping, and the amplitude count includes negatives such as "no amplitude self-cal") | 2017A&A...602L..10O |
| Phase rounds | 1-3 | 1 to 7 | examples | 1: 2015ApJ...798L..23K, 2026ApJ...999..194I; 4: 2017ApJ...836..223W, 2018A&A...619L...6N; 6: 2024MNRAS.534.3237M; 7: 2026A&A...705A..96M |
| Rounds by initial S/N | more rounds for brighter sources | | 2 | peak S/N >~100: 3 phase + 1 amp, <100: 1 phase + 1 amp, <30: none (2018ApJ...869...17L); initial S/N >100: 2 phase + 1 ap, <100: 1 phase + 1 ap (2024PASJ...76..437Y) |
| First phase solint | scan length, `inf`, or several minutes | record length (~3-6 s, 2015ApJ...808...36M) or `int` (2025A&A...696A.150S) up to whole observation (2019AJ....157..251T, type not stated) | examples | 2016ApJ...818..158A (600 s), 2020ApJ...898...10T (120 s), 2024PASJ...76..437Y (`inf`), 2021PSJ.....2....3M (20 min) |
| Final phase solint | integration time or 6-60 s | phase-only: 2 s (2023PSJ.....4..142C, 2020ApJ...888L..28S) to 240 s (2018MNRAS.481L..40S, scan length down to 240 s); 2 min (2020ApJ...895...64L); 90 s for an Orion-KL mosaic (2021ApJ...907...94C); type not stated: 240 s (2016ApJ...829L..35T, B6) | examples | 2020ApJ...894L..14L (2.048 s), 2018A&A...609A..47P (6 s), 2017A&A...602L..10O (15 s); typically shortest successful 30 s on extended data (2026A&A...705A..96M); type not stated: 2016A&A...586A..99H (60 s), MIRIAD 0.01 min requested interval (2016A&A...593A..44L) |
| Amplitude solint | longer than the last phase round, but not always | integration time (2017ApJ...850L..30Y; 2.048 s in 2020ApJ...894L..14L) to 3600 s (2015ApJ...814...22E) | examples | 2015ApJ...808...36M (60 s), 2017A&A...605A..21C (30 s), 2024PASJ...76..437Y (on-source time/5), 2020ApJ...895...64L (20 min), 2025A&A...704A..18O (whole EB, ~45 min) |
| `minsnr` (per gain solution) | 2-3 | 2 to 5 | 8 examples: 4 pack lines + 4 cards | pack: 2021ApJ...906..111T (3), 2021ApJ...911...29C (3), 2024MNRAS.534.3237M (SNR cutoff 3), 2025ApJ...989...30Z (4 phase, 5 amplitude); cards: 2016ApJ...818..158A (2), 2017A&A...605A..21C (2), 2025A&A...696A.150S (2.5), 2020ApJ...892L..18I (3) |
| `minblperant` | 4 or 6 | 3 to 6 | 5 examples: 3 pack lines + 2 cards | pack: 2021ApJ...906..111T (6), 2021ApJ...911...29C (6), 2025ApJ...989...30Z (antennas with <3 baselines rejected); cards: 2016ApJ...818..158A (4), 2017A&A...605A..21C (4) |
| `refant` | a named central antenna | DA41, DA47, DA59, DV11; `refantmode='strict'`; ALMA as VLBI reference | 6 examples | 2018A&A...610A..24F (card), 2024ApJS..270....9X, 2017A&A...600A..72F (card), 2017A&A...605A..21C (card), 2020ApJ...895...64L, 2024MNRAS.534.3237M |
| `gaintype` | CASA `T` = one polarization-independent gain per antenna; `G` = separate per-polarization gains | `G`, `T` | 3 | 2023A&A...676A...4C (`G` at `inf`, `T` at 60 and 10 s), 2020ApJ...895...64L (amp+phase, gain mode `T`), 2016A&A...593A..61M (amplitude round, `T` gain) |
| `combine` | `'scan'` or `'scan,spw'` for long or low-S/N solves (CASA tokens are singular: `scan`, `spw`, `field`) | | examples | 2023A&A...676A...4C, 2023PSJ.....4..206R (`'scan,spw'`), 2024A&A...692A.155K, 2026MNRAS.552g1700S (card quotes "spws, scans") |
| `applymode` | `'calonly'` | | 3 | 2018ApJ...869L..41A (for antenna pairs with SNR <= 1.5), 2020ApJ...890..130T, 2026MNRAS.552g1700S |
| Gate: peak S/N of the initial image | >10 to >40 | | 5 | >10 (2020ApJ...890..130T), >20 (2019ApJS..245....2S, 2015ApJ...812...43B), >=30 (2018ApJ...869...17L), >40 (2018AJ....155...54W) |
| Gate: image detection significance (peak / image rms) | >= 10 sigma | | 1 | 2017ApJ...851...83C (card) |
| Gate: source flux density | a few mJy for phase | ~3 mJy to 100 mJy | 3 | ~3 mJy (2016ApJ...823..160D, card); >=4 mJy phase, >20 mJy amplitude (2026A&A...708A.146P); >=100 mJy quasars (2022MNRAS.516.5618P) |
| Gate: ALMAGAL's estimated self-cal S/N (the card does not give its formula) | S/N_selfcal > 3 | | 1 | 2025A&A...696A.150S (card) |
| Accept rule | rms or S/N better, beam nearly unchanged | beam growth <5% to <15% | 3 | rms down >7.5%, beam up <15% (2025A&A...696A.150S, card); S/N up, beam area change <5% (2024ApJ...973..138H); amplitude dropped if dynamic range falls (2025ApJ...989...83B) |
| uv cut for the solve | long baselines only when extended emission is unmodelled | >150 m to >250 klambda; or short baselines only (<1000 m) when long ones are faint | 5 | 2015A&A...576A..41B, 2015ApJ...802...69B, 2016ApJ...827...68P, 2017ApJ...843...83W (card, >250 klambda), 2021ApJ...909...11J |

`solnorm` and the version-dependent `gaincal` defaults are still rarely stated; treat any value you choose as
your own decision and report it.

Reported improvements (rms, peak S/N, dynamic range, line S/N, survey success rates) are tabulated in
`references/parameters.md`. They are individual case results with different metrics, not a prediction by
source brightness; two sample-level results show smaller gains on more extended arrays (2025A&A...696A.150S,
card; 2024PASJ...76..437Y).

## Software

Pack aggregates over matched steps (896 papers): CASA 590, tclean 122, uvcontsub 34, gaincal 27, AIPS 26, MIRIAD
19, applycal 17, GILDAS 13, fixplanets 10, fixvis 9, DIFMAP/difmap 9, ALMA pipeline 9, clean 7, eht-imaging 6,
Obit 5, phaseshift 5, auto_selfcal 4, snow 3, uvmem 3, OOselfcal 2, gpuvmem 2.

Tool-by-tool examples (MIRIAD, GILDAS, AIPS/Obit, DIFMAP, eht-imaging, RML loops) are in `references/parameters.md`.

The CASA version is flagged as not stated in 74 cards (pack aggregates). Record it; `gaincal` defaults changed
across versions (general practice).

## Pitfalls

- **Unreported settings.** In the pack's "not stated" aggregate the self-cal categories are, with their exact
  labels: "self-calibration solution intervals" 92; "... solution intervals and number of iterations" 58; "...
  solution intervals and number of rounds" 19; "... solution intervals and reference antenna" 18; "... solution
  interval" 12. These are category counts that may overlap, not unique cards. Line-free channels, continuum
  subtraction, image size, cell size, masks and thresholds recur in many separately worded categories (for
  example "line-free channels and continuum subtraction method" 26, "image size and cell size" 28). Report, per round:
  mode, solint and the actual time span per solution, `combine`, `gaintype`, `minsnr`, `minblperant`, `refant`,
  uv range, `solnorm`/normalisation, `applymode`, and the model (mask, weighting, clean threshold, deconvolver).
  Report once: the channel ranges used for the self-cal data, the continuum-subtraction channels and fit order,
  and the calibration chain used in `applycal` (Step 7).
- **Amplitude self-cal changes the flux scale.** Measure it: 2015ApJ...808...36M normalised gains and found <0.7%
  (ALMA) and <0.5% (JVLA) amplitude change. Multi-epoch papers rescale afterwards: amplitudes of one day rescaled
  to the other's total planet flux (2026A&A...707A.240C); per-execution flux rescaling of 10% and 19%
  (2021A&A...649A.122P). If the source is variable or the model is incomplete, skip it (2024MNRAS.534.3237M,
  2015ApJ...804...37L).
- **Model imprinting.** Self-calibrating to a model can create the model's structure. 2024MNRAS.534.3237M
  self-calibrated noise and point-source data with ring models and recovered rings, showing how a ring can be
  an artifact. 2013ApJ...767..132H used simulations to show that fitting the lens model and antenna phases
  together recovers the input antenna phases without bias; the pack does not show a test of bias in the lens
  parameters themselves. Start from a conservative mask and let the model grow round by round.
- **Variable sources violate the static-sky model.** Sgr A* flaring produced concentric circular artifacts,
  lowered S/N and could shift positions (2022PASJ...74..738T). Fixes seen: two-component (variable point source
  + constant mini-spiral) self-cal at 4 s (2022A&A...666A..39M); self-cal on the extended structure, then extract
  the point-source light curve (2024A&A...682A..97W); a uv-plane light-curve fit used in self-cal (2025ApJ...995L..51G).
- **Too-short solint on faint data.** Noise-driven phase solutions raise the apparent peak and can fake
  polarization; 2020ApJ...895...64L required solint of at least ~35 s. Watch the fraction of flagged solutions
  at `minsnr` (ALMAGAL notes data that fail `minsnr=2.5`, 2025A&A...696A.150S, card) and use a data-driven floor (Step 4).
- **Absolute astrometry is lost; beam can change.** Phase-only self-cal ties positions to the starting model:
  2026MNRAS.549g1100P says absolute astrometry was not preserved (+0.9 arcsec RA, -0.5 arcsec Dec offset from
  earlier work, relative positions intact); 2017A&A...608A..38O corrected ~0.1 arcsec offsets with the continuum;
  2020ApJ...898..146M re-centred on the fitted star. Measure positions on the phase-referenced data or check
  sources (2018A&A...615A..28D, 17 mas). Accept rules also cap beam change (Step 6).
- **Line contamination in the self-cal data.** ALMAGAL reports `findcont` is conservative in line-rich sources
  and lists the absence of manual continuum ranges as a limitation (2025A&A...696A.150S, card); disk papers flag fixed
  velocity windows around known lines (Step 2). My recommendation, beyond what ALMAGAL did: inspect the spectra
  and set explicit line-free ranges in line-rich fields, and report them.
- **High frequency and long baselines.** Feasibility depends on the signal and the quality of the solutions,
  not on the band alone (Band 9 cases go both ways; see When not to use). On 15 km baselines self-cal was
  "limited" for HL Tau and absent for SDP.81 (2015ApJ...808L...1A). Long-baseline options seen: stage compact
  data first (Step 1), unfold the solve in cuts of 800 to 8000 klambda (2020ApJ...890..130T), or solve and apply
  only within uv < 1000 m because long baselines had S/N < 3 (2021ApJ...909...11J).
- **Polarization.** Short solints can create spurious polarization (2020ApJ...895...64L, minimum ~35 s); the
  same paper ran its amp+phase round in gain mode `T`, kept the cross-hand phase fixed, and reported 14
  solutions per polarization per antenna (its own accounting). In CASA, `gaintype='T'` solves one
  polarization-independent gain per antenna; use `'G'` if you need separate per-polarization gains. The paper
  left time-varying systematics such as XY phase uninvestigated. 2021AJ....162...99F used a first scan-length
  round for polarization offsets. Check the parallel-hand ratio is unchanged and keep cross-hand phase and leakage
  calibration separate (general practice). Self-cal cannot remove filtering bias: resolved-out CO flux can
  overestimate polarization fractions by a factor 2-3 (2024A&A...686A.274V).
- **Self-calibrated image used for the wrong product.** 2017A&A...604A...6S (card) self-calibrated only on bright
  components and did not use the self-calibrated images for continuum analysis; decide per science product.
- **Missing flux is not fixed by self-cal.** Interferometric filtering limits remain (2016ApJ...832..148V
  recovered 43% of single-dish flux); amplitude self-cal against an incomplete model can make it worse.

## Verification checks

What papers used:

- rms, peak and beam before and after each round (2025A&A...696A.150S, 2024ApJ...973..138H); dynamic range
  before/after (2020ApJ...892L..18I, card, 2023PSJ.....4..142C, ~580 final; 2025ApJ...989...83B, per product); extra
  rounds tried and shown not to help (2012A&A...548A..69N, 2020ApJ...898...10T).
- Flux-scale stability: amplitude change from self-cal <0.7% (2015ApJ...808...36M); fluxes within 5% across
  datasets in a band (2018ApJ...852..122H); visibility amplitudes within 5% on overlapping spatial frequencies
  (2020ApJ...891...48H, card); <~10% between cycles (2020ApJ...892L..18I card, 2023ApJ...954..197I); inter-spw continuum
  mismatches of 1-3% checked against the relative flux calibration error (2025ApJ...989...83B).
- Gain tables: incremental gains close to unity (2022A&A...666A..39M); residual scatter ~5 deg phase, 10%
  amplitude (2015A&A...574A...5D); two calibration models giving comparable gains (2019ApJ...871...30I).
- External flux comparison: Herschel SPIRE (2015ApJ...806...17R), SCUBA-2 (2018MNRAS.475.4924K), SMA
  (2015ApJ...810..112O), IRAM 30m (2018ApJ...865...13T); published images of the same disk (2021ApJ...923..121Y).
- Robustness of structure: different clean masks on self-calibrated and non-self-calibrated images gave the same
  structure (2013Sci...340.1199V); 20 images split by spw and observing block gave consistent fluxes
  (2026MNRAS.549g1100P).
- Split data in time, uv range and polarization to test calibration (2019ApJ...871...73H, Band 9 within 6%).
- Simulations: recovery of input antenna phases under joint lens fitting (2013ApJ...767..132H); ring
  imprinting from self-cal on noise and point-source data (2024MNRAS.534.3237M); an injected synthetic transient
  recovered after two-component self-cal (2022A&A...666A..39M), which also warns that its snapshot residuals
  are dynamic-range limited and non-Gaussian, so a Gaussian false-positive rate does not hold. For transient
  searches, measure the residual noise distribution or false-positive rate empirically.

What a careful referee adds:

- Ask for the solint ladder, mode per round, `minsnr`, `refant`, `combine`, and the fraction of flagged solutions.
- Plot the gain phases per antenna: smooth, time-correlated phases mean real atmosphere; random scatter at the
  shortest solint means you are fitting noise.
- Compare peak and integrated flux before and after: the integrated flux of a well-modelled source should stay
  nearly unchanged under phase-only self-cal. Do not judge success by the size of the peak gain (150 to 1320 in
  2014ApJ...791L...6W); judge it by flux consistency, gain quality and matched imaging and noise measurements.
- For claims of faint structure, image with and without self-cal and with a different starting model.
- Check that line results do not depend on whether continuum solutions were transferred.
- If positions matter, compare them with the phase-referenced image before self-cal.

## Source cards

Full list: `references/sources.md` (896 papers). Most informative for this technique:

- 2025A&A...696A.150S (card): automatic phase-only loop, S/N gate, rms/beam accept rule, success rates by array.
- 2024ApJ...973..138H: auto_selfcal with user masks, inf-to-int halving, beam-area rule, combine fallback.
- 2018ApJ...869L..41A: staged compact then combined ladders, applymode='calonly'.
- 2025ApJ...989...30Z: per-EB round and alignment, baseline/S/N rejection, amplitude S/N and 20% gain flags.
- 2026A&A...705A..96M: combine='scan' ladder to 30 s, amplitude trials, solnorm True then False.
- 2016ApJ...818..158A (card): 4-step phase ladder 600/300/150 s/scan, minblperant=4, minsnr=2.
- 2020ApJ...895...64L: phase 10 and 2 min, amp+phase 20 min in gain mode `T`, minimum solint for polarization.
- 2024MNRAS.534.3237M: phase-only hybrid mapping, model-imprinting simulation.
- 2022A&A...666A..39M: two-component self-cal for a variable source, gain and injection checks.
