# Pre-combination checks and provenance template (`archival-data-reuse`)

Run every row before merging data from different projects, cycles, configurations, arrays or epochs. Each row
gives what to compare, how papers fixed a mismatch, and what to record. Citations are from the evidence pack
(`skills/packs/archival-data-reuse.md`). For 12m + 7m + TP specifics (weights, feather, MACF) use
`array-combination`.

## Checks

| Check | How to test | How papers fixed a mismatch | Record | Examples |
|---|---|---|---|---|
| Flux scale | Image each dataset alone; compare flux of a compact feature, or amplitudes on overlapping uv ranges | Rescale visibilities in the overlap range; rescale to a common reference; `gencal` amplitude factor; renormalise a calibrator flux | factor applied per dataset, reference dataset | 2023A&A...676A...4C, 2024A&A...687A.311A, 2023Natur.623..705S, 2019A&A...626A..81V |
| Flux calibrator model | Read calibrator name and model per MOUS (weblog, scripts) | Replace a poor solar-system model with quasar fluxes; reprocess with newer flux libraries; manual reduction for a variable calibrator | calibrator, model, date | 2024A&A...684A...4U, 2018A&A...616A.127R, 2020ApJ...904...78S |
| Weights | Compare weight vs measured visibility scatter per dataset (`plotms`) | `statwt` per dataset or after `concat`; manual rescale to noise variance; inverse-variance weights; check that average weights are similar before keeping defaults | statwt settings or factors | 2016ApJS..222....1F, 2017A&A...605A..42C, 2023ApJ...954..197I, 2020A&A...634L..12D |
| Relative configuration weight | Decide whether short or long baselines should dominate | Fixed multipliers (compact 0.2 for continuum, unscaled for cubes; 1/10 for low resolution; 0.2 and 1.0 by configuration) | multiplier and why | 2020ApJ...889..141T, 2016ApJ...829L..10I, 2023MNRAS.522.4078C |
| Spectral frame and channels | Check frame (TOPO vs LSRK), channel width, bandwidth per SPW | Bin to the coarser channel and trim to the common bandwidth; regrid with `mstransform` or `cvel`; `split` the common frequency range; combine in LSRK | frame, channel width, common range | 2019A&A...629A..29J, 2018ApJ...852..122H, 2023MNRAS.521.1045R, 2021A&A...645A..49G |
| Concat tolerances | Check whether fields and SPWs should merge | Defaults keep separate fields and SPWs; `freqtol` 10 MHz used once | freqtol, dirtol | 2025A&A...699A..80H, 2020A&A...641A..97V |
| Phase centre and astrometry | Fit position of a compact feature in each dataset; compare with the expected position | `fixvis`, `fixplanets`, `phaseshift`; Gaussian-fit alignment to a common position; offsets larger than one third of the extended beam corrected; pointing offset corrected in mas | shift per dataset, reference position | 2024A&A...686A.298G, 2024A&A...682A..55M, 2021A&A...648A..33M, 2019MNRAS.482L..29D |
| Proper motion | Compute the source motion between the dates | Shift visibilities for proper motion; realign to Gaia DR2; shift all epochs to one date | proper motion used, epoch | 2016ApJ...820L..40A, 2021MNRAS.506.1978L, 2023ApJ...948..110Y |
| Reference frame | Check coordinate frame per dataset | Cycle 2 reference frame relabelled to ICRS before `concat` | frame change | 2023ApJ...954..197I |
| Self-calibration order | Is each dataset bright enough alone? | Self-cal each, then combine; short baselines first, then joint self-cal; self-cal short baselines and concat with flux-calibrated long baselines | per-stage solint | 2016A&A...586A..70L, 2018ApJ...869L..41A, 2024A&A...684A.174P |
| Bad execution blocks | Amplitude vs uv distance per EB | Flag an EB with deviant amplitude-vs-uv | EB flagged | 2024ApJ...966...63Y |
| Source variability | Date span vs expected variability; flux of compact core per epoch | Subtract the variable core before combining; keep epochs separate | epochs used, reason | 2017ApJ...849...95B, 2024A&A...692A..86H |
| Moving or extended structure | Does a secondary or feature move between epochs? | Recentre epochs on the moving component before line imaging | recentring | 2020ApJ...902L..33G |
| uv coverage and MRS | Compare uv ranges and MRS per dataset | Common uv coverage with `uvsim`; uv cuts (compact uv > 180 klambda plus all extended); exclude baselines in a range; drop baselines < 33 m; restrict to uv < 65 klambda | uv range per product | 2015ApJ...812..126C, 2020ApJ...901...74T, 2020ApJ...902...99I, 2021ApJ...907L..27A, 2024A&A...682A.186L |
| Beam for comparisons | Beams of each product | Smooth to a common beam before ratios (2.5 arcsec common beam for line ratios); adjust a reused cube's beam | target beam | 2026ApJ..1001...33L, 2020ApJ...905..122H |
| Did combining help? | Compare noise, beam, fidelity with and without each dataset | Drop the combination if there is no gain; keep combined cubes as reference only | decision | 2022A&A...665A.107T, 2024A&A...691A.197K |

## Provenance template (one row per dataset, written to a file)

| Field | Example of what papers state |
|---|---|
| Project code, PI, PI or archival | archival, PI named (2017ApJ...849...14S) |
| MOUS UID(s), EBs used and dropped | per member OUS in a table (2025ApJ...989...83B) |
| Band, SPWs, array, configuration, beam, MRS, rms | per dataset tables (2024ApJ...969..102N, 2024A&A...684A...4U) |
| Observing dates | per EB (2025ApJ...989...83B) |
| Product used and version | PHANGS-ALMA v4.0 (2021A&A...656A.133Q); MAPS release (2023A&A...674A.113I); pipeline image (2025ApJ...993L...6N) |
| Calibration route | delivered, restored with scripts, ARC MS, or recalibrated (2021ApJ...918...76C, 2024A&A...691A.178B) |
| CASA and pipeline version, calibration and analysis separately | pipeline 5.6.1 and 6.5.2, analysis 6.5.2 (2025A&A...699A..80H) |
| Flux calibrator, model, adopted uncertainty | J1550+0527 power law, ~5% (2017ApJ...849...14S) |
| Self-calibration (rounds, solint, mode) | phase rounds 900 s and 360 s, then inf (2025ApJ...985...84L) |
| Weights, rescale factors, alignment shifts | statwt, shifts in arcsec (2019A&A...625A.118K) |
| Data release cut-off and download date | public by 2015 June (2016ApJS..222....1F); downloaded March 2014 (2018MNRAS.477.2926W) |
| Open items | anything not verifiable with the data in hand |
