# Refresh notes: uv-plane-fitting (3,500-paper corpus, 2026-10-30)

Pack 278 -> 638 papers. Bibcodes cited: SKILL.md 68 -> 100 (with parameters.md 96 -> 133). SKILL.md 296 -> 334
lines (over the ~300 target). All SR-01..SR-23 fixes kept. Claims whose support the rebuilt pack no longer shows line-for-line (26,600
injections in 2017ApJ...850...83F, 600 klambda minimum in 2018ApJ...865...37M, 500 frank runs and AIC/BIC in
2025ApJ...986L..11S, 290 klambda null in 2014ApJ...791L...6W, Delta chi2 6.63 in 2025ApJ...986L..22R, joint
fit of close secondaries in 2025A&A...700A.188C, per-scan fits in 2020ApJ...894...76W) were checked against
their cards and kept; all cited bibcodes are in the new pack.

## Counts recomputed (pack aggregates unless noted)
- Software: CASA 105 -> 283, emcee 74 -> 136, uvmodelfit 39 -> 94 (56 + 38), uvmultifit 39 -> 86, galario
  33 -> 81, GILDAS 24 -> 77, RADMC-3D 26 -> 49, vis_sample 21 -> 37, MIRIAD 12 -> 21, LIME 7 -> 13, dynesty
  3 -> 9, frank 2 -> 14 (frank 7 + frankenstein 7). New rows: MultiNest 5, PyAutoLens 8, pdspy 7, pyralysis 4,
  imfit/GALFIT as cross-checks; AIPS, diskfit, lmfit, MPFIT, uvplot in one line. uvsim fell out of the top 40.
- Walkers (my count): 68 papers; 100 in 17, 200 in 12, 120 in 7; range 32-1024 -> 24-1024. Walkers per
  parameter 4 -> 7 papers (range 2-10). Chain settings ~40 -> ~90 papers. Priors: 29 papers.
- Weights: 6 -> 10 papers; factor range 0.25-0.4 -> 0.1-0.6 (2024PASJ...76..437Y 0.1-0.3, 2026ApJ..1005...94N
  0.2/0.6 per track). The summary now says "multiplied by 0.1 to 0.6" instead of "down by 2.5 to 4".
- uv cuts 6 -> ~19; uv bins 4 -> ~12 (range 5-150 klambda); time averaging 4 -> 8; model image 5 -> ~10
  (256-4096 px); frank settings 2 -> 7 (alpha up to 1.4, 2025ApJ...990L..70L); S/N cut 2 -> 4 (S/N >= 8-10).
- Not-stated settings re-summed: CASA/pipeline version 79, line-free channels 78, self-cal 55, image/cell 34,
  flux calibrator/scale 27, refant 12, contsub method 11, uvmodelfit start 11, coordinates 7, PB 5.

## New practice added
- Recentre via uvmodelfit + fixvis, check by imaginary-image RMS (2021ApJ...909..212K); Airy PB left ~5%
  residuals, fixed by a joint 4-field fit (2026A&A...707A.255C); per-pointing PB (2026A&A...705A.197Z).
- Astrometric systematic 5% of beam (2025Natur.642..905L); resolved-vs-point rule (2020MNRAS.492.3194S).
- Convergence checks from the pack: autocorrelation ~1000 steps (2019ApJ...874..136S), >= 1e5 post-convergence
  samples and dropping walkers 5 sigma low (2026A&A...705A.197Z), acceptance 0.2-0.5 (2020MNRAS.492..572A).
- Verification: size-recovery simulations and uvmodelfit vs imfit/GALFIT offsets (2020ApJ...888...44C),
  stacked-residual halo test (2025A&A...693A.237I), pixel-halving test (2024A&A...692A.155K), sideband
  agreement for flares (2022ApJ...939L...6B), multi-epoch fits with per-epoch centre and flux scale.
- Pitfalls: model choice and strict uv/velocity cuts (2024A&A...687A.308S); mixed-component models
  (2019MNRAS.487.4037D); warped belts (2026A&A...705A.197Z); missing flux in ACA sizes (2021A&A...653A..53A).
- Exponential disk: 2025A&A...693A.237I's R_e,major = 1.21 FWHM matches the general FWHM = 0.826 R_e.

## Source cards: out 2014ApJ...797...27F, 2023PSJ.....4..142C, 2014ApJ...792L...2C, 2015ApJ...811..124S,
2016ApJ...829L..23B, 2018A&A...617A..23B, 2020ApJ...894...76W, 2024A&A...689A.104D; in 693A.237I, 888...44C,
939L...6B, 909..212K, 705A.197Z, 687A.308S, 707A.255C (23 listed). No recommendation reversed.
