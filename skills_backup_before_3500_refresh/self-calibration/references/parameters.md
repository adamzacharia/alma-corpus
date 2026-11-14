# Self-calibration ladders seen in the corpus

Each row is one paper's self-calibration sequence as its card records it (pack key-parameter lines and
excerpts). "p" = phase-only round, "ap" = amplitude+phase round, "amp" = amplitude round whose exact mode the card
does not give, "type not stated" = the card does not say phase-only or amplitude+phase. Blank cells mean the card
does not state it. A requested solint shorter than the integration time still gives one solution per integration.

| Paper | Model / data used | Sequence (solint) | Notes |
|---|---|---|---|
| 2012ApJ...752L..30W | line-free emission | ap (3 min) | 7 min calibration cycle |
| 2013Natur.493..191C | continuum | p (5 min), then ap | not applied to line channels |
| 2014A&A...566A.112M | two-point-source model | p (30 s) | S/N up ~2 |
| 2014ApJ...795..156W | CO averaged over 500 km/s into one plane | type not stated (10 min) | |
| 2014ApJ...796...82Z | continuum per band | ap (2 min) in B3; p in B6, B7; none in B9 | |
| 2015ApJ...806...17R | bright central region, natural weighting | p, p, ap | noise 36 to 16 mJy/beam |
| 2015ApJ...808...36M | Mira AB continuum | p (record length, ~6 s B3, ~3 s B6), ap (60 s) | gains normalised; amplitude change <0.7% |
| 2015ApJ...814...22E | smoothed line-free channels | p (600 s), p (60 s), ap (3600 s) | applied to unsmoothed data |
| 2016A&A...593A..44L | 7 central mosaic fields, demos model | MIRIAD selfcal options=mosaic, requested interval 0.01 min, type not stated | |
| 2016A&A...593A..61M | target | p, p, ap (T gain) | |
| 2016ApJ...817..168H | peak maser channel | p (5 s), ap (30/72 s) | applied to all channels and spws |
| 2016ApJ...818..158A | continuum | p (600 s), p (300 s), p (150 s), p (scan) | minblperant=4, minsnr=2 |
| 2016ApJ...824..132N | CLEAN models of I, Q, U | p, ap (30 s) | |
| 2016ApJ...827...68P | line (Circinus); continuum >150 m (NGC 4945) | p (1 min); p (30 s) | |
| 2016ApJ...829L..35T | continuum | iterative ladder 600 to 90 s (B4); 1200 to 240 s (B6), type not stated | |
| 2017A&A...600A..72F | TDM continuum window | p (300 s), p, ap | refant DA59; applied to FDM windows |
| 2017A&A...602L..10O | continuum | p x3 (15 s), ap | |
| 2017A&A...605A..21C | continuum | p (500 s), p (30 s), ap (30 s) | refant DV11; min 4 baselines, SNR>2 |
| 2017ApJ...840...60B | continuum | p (30 s), ap (scan length ~5 min) | peak S/N up ~4x |
| 2017ApJ...850L..30Y | continuum | p (scan length), p (30.25 s), p (int), ap (int) | transferred to line spws |
| 2017ApJ...851..132C | continuum | p (30 s), p (6 s), ap (7 min) | continuum rms down ~40x |
| 2017Icar..286..289L | continuum window (Pluto) | p (5 min), p (2 min), p (1 min) | applied to line windows |
| 2018A&A...609A..47P | continuum | p x3 (last at 6 s), ap | applied to CO |
| 2018A&A...616A..88V | continuum | p, down to 6 s (B6) or 15 s (B7) | |
| 2018ApJ...853..171G | joint 7m+12m continuum | p x3, ap x2 | none for cubes |
| 2019AJ....157..251T | Neptune | whole observation, 350 s, 60 s | type not stated |
| 2020ApJ...894L..14L | continuum | p x2 (Sgr B1-off); p x2 + ap (Sgr C), 2.048 s | |
| 2020ApJ...895...64L | point source, per sideband | p (10 min), p (2 min), ap (20 min, gaintype T) | refant strict; min solint ~35 s |
| 2020ApJ...898...10T | continuum | p (120 s) | 30 s round and ap did not help |
| 2020ApJ...898..146M | stellar point source, all 4 spws | p (~370 s), p (132 s), p (99 s), amp (~370 s) | per execution; peak SNR up 40-50% |
| 2020ApJ...905...85S | continuum | 1-2 p (scan length or half scan) | rms down up to 2x |
| 2023PSJ.....4..142C | Lambertian disk start model | p from full integration (>121 s) down to 2 s | stop when SNR stops improving |
| 2024A&A...686A.274V | continuum | p (inf), p (int) | |
| 2024MNRAS.534.3237M | point-source start (EHT) | p x6 (0.15 min) | SNR cutoff 3, refant ALMA; no amp |
| 2025A&A...696A.150S | continuum, automatic | p (int) per iteration, clean 4x/3x/2x rms | S/N_selfcal>3, minsnr=2.5; keep if rms >7.5% better and beam <15% larger |
