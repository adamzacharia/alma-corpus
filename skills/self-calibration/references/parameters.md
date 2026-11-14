# Self-calibration ladders seen in the corpus

Each row is one paper's self-calibration sequence as its card records it (pack key-parameter lines and
excerpts; the 26 rows added in the 2026-10 refresh come from the 896-paper pack). "p" = phase-only round, "ap" = amplitude+phase round, "amp" = amplitude round whose exact mode the card
does not give, "type not stated" = the card does not say phase-only or amplitude+phase. Blank cells mean the card
does not state it. A requested solint shorter than the integration time still gives one solution per integration.
"(card)" = the pack lists the paper only bibliographically; the row was checked against its card.

| Paper | Model / data used | Sequence (solint) | Notes |
|---|---|---|---|
| 2012ApJ...752L..30W | line-free emission | ap (3 min) | 7 min calibration cycle |
| 2013Natur.493..191C | continuum | p (5 min), then ap | not applied to line channels |
| 2014A&A...566A.112M | two-point-source model | p (30 s) | S/N up ~2 |
| 2014ApJ...795..156W | CO averaged over 500 km/s into one plane | type not stated (10 min) | |
| 2014ApJ...796...82Z | continuum per band | ap (2 min) in B3; p in B6, B7; none in B9 | |
| 2015ApJ...806...17R | bright central region, natural weighting | p, p, ap | noise 36 to 16 mJy/beam |
| 2015ApJ...808...36M | Mira AB continuum | p (record length, ~6 s B3, ~3 s B6), ap (60 s) | gains normalised; amplitude change <0.7% |
| 2015ApJ...814...22E | smoothed line-free channels | p (600 s), p (60 s), amp (3600 s) | applied to unsmoothed data |
| 2016A&A...593A..44L | 7 central mosaic fields, demos model | MIRIAD selfcal options=mosaic, requested interval 0.01 min, type not stated | |
| 2016A&A...593A..61M | target | p, p, amp (T gain) | |
| 2016ApJ...817..168H (card) | peak maser channel | p (5 s), ap (30/72 s) | applied to all channels and spws |
| 2016ApJ...818..158A (card) | continuum | p (600 s), p (300 s), p (150 s), p (scan) | minblperant=4, minsnr=2 |
| 2016ApJ...824..132N | CLEAN models of I, Q, U | p, ap (30 s) | |
| 2016ApJ...827...68P | line (Circinus); continuum >150 m (NGC 4945) | p (1 min); p (30 s) | |
| 2016ApJ...829L..35T | continuum | iterative ladder 600 to 90 s (B4); 1200 to 240 s (B6), type not stated | |
| 2017A&A...600A..72F (card) | TDM continuum window | p (300 s), p, amp | refant DA59; applied to FDM windows |
| 2017A&A...602L..10O | continuum | p x3 (15 s), ap | |
| 2017A&A...605A..21C (card) | continuum | p (500 s), p (30 s), amp (30 s) | refant DV11; min 4 baselines, SNR>2 |
| 2017ApJ...840...60B (card) | continuum | p (30 s), ap (scan length ~5 min) | peak S/N up ~4x |
| 2017ApJ...850L..30Y | continuum | p (scan length), p (30.25 s), p (int), ap (int) | transferred to line spws |
| 2017ApJ...851..132C (card) | continuum | p (30 s), p (6 s), ap (7 min) | continuum rms down ~40x |
| 2017Icar..286..289L | continuum window (Pluto) | p (5 min), p (2 min), p (1 min) | applied to line windows |
| 2018A&A...609A..47P (card) | continuum | p x3 (last at 6 s), ap | applied to CO |
| 2018A&A...616A..88V (card) | continuum | p, down to 6 s (B6) or 15 s (B7) | |
| 2018A&A...619L...6N | continuum | p (20 min), p (1 min), p (2 s), p (2 s), amp (2 s) | |
| 2018ApJ...853..171G | joint 7m+12m continuum | p x3, ap x2 | none for cubes |
| 2018ApJ...867...43T | continuum | p (scan length), p (12.1 or 6.05 s), amp with normalisation | 16 of 17 fields; applied to line bands |
| 2018ApJ...869...17L | continuum | S/N >~100: p x3 + amp; S/N <100: p + amp; S/N <30: none | stopped when no S/N improvement |
| 2018ApJ...869L..41A | compact data, then combined | compact: p (60, 30, 18, 6 s), amp (scan); combined: p (900, 360, 180, 60, 30 s), amp | spws combined; applymode='calonly' for SNR <= 1.5 |
| 2018MNRAS.481L..40S | lensed quasar continuum | p, several timescales from scan length down to 240 s | applied to line channels |
| 2019AJ....157..251T | Neptune | whole observation, 350 s, 60 s | type not stated |
| 2019PASJ...71..124S | continuum | p (scan length 2-7 min), p (240 s), p (120 s), p (60 s), amp (scan length) | |
| 2020ApJ...888L..28S | continuum | p x5, 10 min down to 2 s | |
| 2020ApJ...890..130T | continuum, peak S/N >10 | up to 3 p (scan length, 12.08 s, 3.02 s); long baselines unfolded with cuts 800-8000 klambda | applymode='calonly' |
| 2020ApJ...894L..14L | continuum | p x2 (Sgr B1-off); p x2 + ap (Sgr C), 2.048 s | |
| 2020ApJ...895...64L | point source, per sideband | p (10 min), p (2 min), ap (20 min, gain mode T: one polarization-independent gain per antenna in CASA) | refant strict; min solint ~35 s |
| 2020ApJ...898...10T | continuum | p (120 s) | 30 s round and ap did not help |
| 2020ApJ...898..146M | stellar point source, all 4 spws | p (~370 s), p (132 s), p (99 s), amp (~370 s) | per execution; peak SNR up 40-50% |
| 2020ApJ...905...85S | continuum | 1-2 p (scan length or half scan) | rms down up to 2x |
| 2021ApJ...911...29C | line-free continuum | p (30 s), polarizations averaged, spws independent | min SNR 3, min 6 baselines per antenna |
| 2021ApJ...923..121Y | continuum | p (98 s), p (49 s, integration), ap (98 s) | SNR up 3.8x |
| 2021PSJ.....2....3M | continuum | p (20, 10, 5, 1 min) | |
| 2022MNRAS.513.5790C | each dataset, then concatenated | OOselfcal; scan length (~50 s), halved each iteration | uvmem imaging in the loop |
| 2022PASJ...74..738T | Sgr A* field | p (inf) x2, then int, then ap; 7-8 iterations | flaring breaks the static-sky model |
| 2023A&A...676A...4C | continuum | p (inf, combine scans, G), p (60 s, combine spws, T), p (10 s, T) | |
| 2023PSJ.....4..142C | Lambertian disk start model | p from full integration (>121 s) down to 2 s | stop when SNR stops improving |
| 2023PSJ.....4..206R | continuum, automated | p (inf over EB), p (per-scan inf), shorter where possible, amp (inf) where phase succeeded | combine='scan,spw' fallback |
| 2024A&A...686A.274V | continuum | p (inf), p (int) | |
| 2024A&A...687A.308S | continuum | p (3 min, 60.6 s, 30.3 s), ap (3 min, 90.9 s) | clean depth lowered each round |
| 2024A&A...688A.110S | per epoch | several rounds; shortest solint giving S/N >3 on >90% of antennas | ap for SPT lenses, p only for SDP 81 |
| 2024ApJ...961....4B | continuum | p (inf), p (int), ap (inf); extra 15 s ap for Sgr B2 N B6 | |
| 2024ApJ...963L..31H | Stokes I | p (600 s), p (30 s), p (10 s) | 12CO flagged before self-cal |
| 2024ApJ...973..138H | user-masked continuum, auto_selfcal | p, solint halved from inf to int | keep if S/N up and beam area change <5%; fallback combines scans and spws |
| 2024MNRAS.534.3237M | point-source start (EHT) | p x6 (0.15 min) | SNR cutoff 3, refant ALMA; no amp |
| 2024PASJ...76..437Y | continuum, initial S/N >100 | p (inf), p (OST/5), ap (OST/5); S/N <100: p (inf), ap (OST/5) | OST = on-source time; best-S/N image kept |
| 2025A&A...696A.150S (card) | continuum, automatic | p (int) per iteration, clean 4x/3x/2x rms | S/N_selfcal>3, minsnr=2.5; keep if rms >7.5% better and beam <15% larger |
| 2025A&A...698A.115R | Band 7 SB, then SB+LB | p per EB; SB p (EB, 360, 120, 60, 20 s); combined p (EB, 360, 120, 60, 30, 18 s); ap x2 (EB, scan) | lines flagged +-30 km/s |
| 2025ApJ...989...30Z | pseudo-continuum, lines flagged +-15 km/s | p per EB (inf), EB alignment, p down to 20 s / 18 s, ap (inf) | reject antennas <3 baselines or SNR <4; flag amp SNR <5 or gains >20% |
| 2026A&A...705A..96M | extended data, then combined with FAUST | p x7 (inf combine=scan to int, shortest ~30 s); amp (inf); combined p x6 (inf, 60 to 9 s), amp (inf) | solnorm True then False |
| 2026A&A...708A.146P | background quasar >=4 mJy | p (30 s to 4 min); amp if quasar >20 mJy | |
| 2026A&A...712A.244H | continuum | "two iterations of one round of phase-only (int) followed by one round of phase and amplitude" (10 s B4/B6, 30 s B7) | ordering ambiguous: either (p, ap) twice or p, p, ap |
| 2026MNRAS.552g1700S | SB, then SB+LB | SB p (inf, 360 s), executable form combine='scan,spw' (card spelling "spws, scans"); SB+LB p (one round) | applymode='calonly' |

## What self-calibration bought (reported improvements)

| Gain reported | Paper |
|---|---|
| rms 36 to 16 mJy/beam (line-free), 100 to 18 mJy/beam (line); continuum rms ~40x; ~10x (3C138); 3.5-4x with line rms up to 30% | 2015ApJ...806...17R; 2017ApJ...851..132C (card); 2015ApJ...808L...1A; 2026A&A...711A.159M |
| dynamic range x11.4, x31.9, x57.7 to 11200 after phase, amp, amp+phase; ~380 to ~2860; ~120 to ~250 | 2017A&A...603A..68M; 2017NatAs...1..848V; 2020ApJ...892L..18I (card) |
| peak S/N 150 to 1320; SNR x3.8; x1.8; 28 to 37 | 2014ApJ...791L...6W; 2021ApJ...923..121Y; 2018ApJ...859..111H (card); 2018MNRAS.475.4924K |
| line S/N +50% CO(1-0), +30% CO(3-2); x1.2 CO(1-0), none at CO(3-2); line self-cal x1.1-1.5 | 2018ApJ...863..193V; 2016ApJ...832..148V; 2019A&A...622A.206M |
| rms ~20%, 14%, ~25%, <=10%; S/N ~10% for peak S/N>20 targets | 2020ApJ...898...10T; 2018ApJ...865...13T; 2017Sci...355.1285N; 2017ApJ...838..114K (card); 2015ApJ...812...43B |
| ALMAGAL: 81% (7M), 66% (TM2), 45% (TM1) of eligible fields improved; Taurus disks: SNR x~1.5 at ~10 Mlambda max baseline, several times at ~2 Mlambda | 2025A&A...696A.150S (card); 2024PASJ...76..437Y (card) |

These are individual case results with different metrics (image rms, peak S/N, dynamic range), not a validated
prediction by source brightness or morphology; compare like with like. Two sample-level results point the same
way: gains are smaller for more extended arrays (ALMAGAL success rate by array, 2025A&A...696A.150S; Taurus disk
SNR gain by maximum baseline, 2024PASJ...76..437Y).

Independent image comparison: ALMA vs VLA images of 3C138 agree to a few percent (2015ApJ...808L...1A).

## Software used in self-calibration loops

| Tool | Used for | Examples |
|---|---|---|
| CASA `tclean` (or the older `clean`) + `gaincal` + `applycal` | the standard loop | `tclean`/`gaincal`/`applycal`: 2023PSJ.....4..142C, 2022PASJ...74..738T; `clean`/`gaincal`/`applycal`: 2017ApJ...850L...2A; CASA pipeline then self-cal: 2024Ap&SS.369...18M |
| CASA `fixvis`, `fixplanets`, `phaseshift` | common phase centre before self-cal and combination | 2018ApJ...852..122H, 2020ApJ...891...48H, 2024A&A...687A.311A |
| `auto_selfcal` and other scripted loops | survey-scale self-cal with accept/reject rules and fallbacks | 2024ApJ...973..138H (modified, user masks), 2025A&A...696A.150S, 2023PSJ.....4..206R |
| snow (gpuvmem), OOselfcal (uvmem) | self-cal loops with RML/MEM imaging in place of `tclean` | 2025A&A...702A..18D, 2026A&A...710L..10C, 2022MNRAS.513.5790C |
| gaincalR | antenna-based gain solver inside the loop | 2024ApJ...971L..33K, 2022MNRAS.514.2346K |
| MIRIAD `selfcal` | mosaics (`options=mosaic`) and point sources | 2016A&A...593A..44L, 2018A&A...614A..42M, 2019A&A...632A..66O |
| GILDAS | phase self-cal on compact sources (IRAM-style reduction) | 2017A&A...597L...5B, 2018A&A...614A..58B, 2024A&A...689A.317G |
| AIPS, Obit | VLBI hybrid mapping; JVLA companion data; long-baseline tests | 2024MNRAS.534.3237M, 2016PASJ...68L...7T, 2015ApJ...808...36M, 2015ApJ...808L...1A |
| DIFMAP | iterative self-cal of compact radio sources | 2016A&A...593L..19M, 2024PASJ...76..340K |
| eht-imaging | VLBI amplitude self-cal to a Gaussian or closure image | 2019ApJ...871...30I, 2020A&A...636A...5R |
