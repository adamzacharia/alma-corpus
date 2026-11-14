# Per-paper settings for blind extraction, fidelity, completeness and counts

All values are from the evidence pack `packs/source-extraction-counts.md` (verified quotes in the cards).
"Not stated" means the card flags it as missing.

## Detection setups

| Bibcode | Finder | Detection image | Thresholds | Notes |
|---|---|---|---|---|
| 2014ApJ...795....5O | SExtractor | maps before PB correction | 6 contiguous pixels > 1.8 sigma; peak S/N > 4.0 | spurious count from negative map |
| 2016ApJ...833...68A | SExtractor | non-PB-corrected 1.2 mm map | min area 5 pixels (1.5''); extract to 2.5 sigma local; main sample > 3.5 sigma, counts extended to 3 sigma | 2D Gaussian fluxes, peak for unresolved |
| 2015ApJ...807..128S | SExtractor + CASA imfit | 0.8'' "detection" maps, non-PB-corrected | > 3 sigma peaks; 4 sigma cut gives 52 SMGs | 0.8'' radius aperture, 4% correction |
| 2025ApJS..278...45F | SExtractor 2.5.0 | natural and tapered, Wide and Deep | Wide 5.0 / 4.4; Deep 4.8 / 4.2 (natural / tapered); to 20% relative sensitivity | thresholds where positives exceed negatives |
| 2018A&A...620A.152F | BLOBCAT | S/N map of 0.60'' mosaic | sigma_p = 4.8, sigma_f = 2.7 (scan 4-6, 2.5-4) | purity >= 0.8 required |
| 2020ApJ...897...91G | LineSeeker (DBSCAN) | natural and tapered 1.2 mm | pixels S/N >= 2 grouped; fidelity 50% at 4.3 (natural), 3.3 (tapered) | DBSCAN eps/min samples not stated |
| 2013MNRAS.432....2K | IDL code, MH-MCMC Gaussian fits | 88 ALMA maps | peaks > 2.5 sigma; catalog > 3.5 sigma | point-source peak flux adopted |
| 2015A&A...584A..78C | 2D Gaussian fitting (tool not named) | 18 continuum maps | S/N > 3.5, size within 1.5x beam | 50 sources |
| 2018ApJ...869...71Z | CASA, iterative masking | S/N maps, uncorrected PB | 5 sigma; "radius 1.3 x primary beam FWHM" as written | noise = "68th percentile of the distribution of pixel values" (signed or absolute not stated; for signed Gaussian pixels this is ~0.47 sigma) |
| 2018ApJ...860..161S | not stated in pack | 870 um maps | S/N >= 4.3 gives 98% purity | recovery within 0.6'' |
| 2015ApJ...806L..25S | not stated in pack | quasar fields | 3.75 sigma; 5.25 sigma high-confidence in low-rms fields | high spurious fraction in low-rms fields |
| 2018MNRAS.479.3879W | not stated in pack | SMG fields | 5.5 sigma blind; 5.0 sigma at IRAC 3.6 um positions (15% contamination) | |
| 2020A&A...643A..53F | BLOBCAT + GALFIT | 0.60'' tapered image | 3.5-4.8 sigma with IRAC < 0.3'' or < 0.7'' plus radio | purity 48% within 0.7'' of IRAC |
| 2020A&A...640A..27V | blind peak search | disk survey map | > 4.8 sigma, 0.6 expected false positives from independent beams | |
| 2019ApJ...871..109P | not stated in pack | serendipitous fields | 3.9 sigma; 176 sources | no completeness or counts |
| 2018ApJ...867..153C | not stated in pack | quasar fields | two or more adjacent pixels above 5 sigma | |
| 2016A&A...586A..70L | SExtractor | wavelet-filtered Band 3+6+7 | 4.5 sigma, min 5 pixels | background counts vs Hatsukade et al. 2013 |
| 2019A&A...632A..38A | SEAC flood fill | ATCA radio maps (earlier ALMA data used only for comparison) | seed 5 sigma, flood 3 sigma, local rms | Galactic cluster; non-ALMA methodological example |

## Injection-recovery setups

Sources per realization, realizations, and total injections are kept in separate columns. Totals are
as quoted in the pack or computed from the two previous columns (marked "computed"); blank = not stated
in the pack.

| Bibcode | Sources per realization | Realizations | Total injections | Flux / S/N range | Sizes | Recovered if |
|---|---|---|---|---|---|---|
| 2018ApJ...869...71Z | not stated (random positions) | 100 per S/N bin | | S/N 3.0-7.0, step 0.1 | not stated | within one synthesized beam |
| 2020ApJ...897...91G | point sources into a uv jackknife noise image | | 20,000 | not stated for completeness (0.03-2 mJy is the separate P(D) forward-model range) | point | |
| 2015ApJ...807..128S | not stated | 2 x 10^4 simulated maps | | power law index -2 | 0-0.5'' | |
| 2018A&A...620A.152F | 300 per run | 100 runs per flux value | 30,000 per flux value (computed); number of flux values not stated | 0.5-2.4 mJy | 0.2-0.9'' FWHM (ALMA 1.4x smaller than HST H) | |
| 2015A&A...584A..78C | 4-8 per simulation | 1000 per map (completeness); 10^4 per map (boosting) | 4,000-8,000 per map for completeness (computed) | 0.05-1 mJy; S/N 3-8 (boosting) | | S/N >= 3.5 |
| 2016ApJ...833...68A | 10 point sources | 10 | 100 | 10-300 uJy | point | within 1'' |
| 2013MNRAS.432....2K | 5 per source-removed map | 16 per map | 7,400 (as quoted) | | | |
| 2014ApJ...795....5O | flux-scaled synthesized beams | | not stated (card flags it) | S/N 2-9 | beam | |
| 2019MNRAS.487.4648S | | | | power law index -2 | uniform 0-0.9'' FWHM | within 0.6'' |
| 2018ApJ...860..161S | | | | | | within 0.6'' |
| 2018PASJ...70...65U | | | | | | > 4 sigma and within 1.0'' |
| 2018ApJ...867..153C | unresolved, unclustered | | | Fujimoto 2016 Schechter counts | point | |
| 2020ApJS..251...14H | 10 point sources, CASA simobserve + tclean | | | | point | inside a pruned leaf |
| 2019MNRAS.483.1624B | 600 beam-sized Gaussians per mass bin | | | | beam | ClumpFind rerun; logistic fit |

## Fidelity and completeness parameterizations

- Error function vs S/N for fidelity and completeness: fidelity A = log10(42), B = 1/4; completeness
  A' = log10(35), B' = 0.45; both 50% at 3 sigma (2016ApJ...833...68A).
- Line-search fidelity (same idea): C_3mm = 5.1, C_1mm = 5.0, sigma_3mm = 0.4, sigma_1mm = 0.8; 60/80/95%
  fidelity at S/N 5.17/5.34/5.57 (3 mm) (2016ApJ...833...67W).
- Gaussian noise tails plus a power-law signal, fitted to negative then positive peak distributions
  (2020ApJ...902..110D).
- Per-source weight p = 2 - f_recovered - f_spurious, with f vs S/N parametrizations not stated
  (2013MNRAS.432....2K).

## Count fits reported

Conventions differ (differential vs cumulative, N0 in mJy^-1 deg^-2 vs deg^-2). Do not move parameters
between rows; integrate a differential model to get cumulative counts.

| Bibcode | Band | Model and fitter | Parameters |
|---|---|---|---|
| 2020ApJ...897...91G | 1.2 mm | differential DPL; direct counts and P(D) (Cash statistic grid; injected fluxes 0.03-2 mJy) | S0 = 0.10 +/- 0.02 mJy, N0 = (4.4 +/- 0.6) x 10^4 mJy^-1 deg^-2; P(D) grid N0 1-100 x 10^3 mJy^-1 deg^-2, S0 0.05-1.0 mJy, alpha 1.5-5, beta -2 to 2 |
| 2015ApJ...807..128S | 870 um, S > 7.5 mJy | DPL (written form not in pack), fit method not stated | S0 = 8.4 +/- 0.6 mJy, N0 = 390 (+110/-80) deg^-2, alpha = 1.9 +/- 0.2, beta = 10.5 (+3.0/-3.2) |
| 2017ApJ...835...98U, 2018PASJ...70...65U | 1.1 mm (literature counts scaled) | written N(>S) = N'/S' [(S/S')^alpha + (S/S')^beta]^-1, N' in deg^-2 (card); fit method not stated | prefactor N'/S' has units of a differential normalization; check the paper before using as cumulative |
| 2018ApJ...869...71Z | 3 mm | cumulative DPL, chi-square Levenberg-Marquardt; Schechter rejected | alpha = 1.4 +/- 0.5, beta = 3.4 +/- 0.5, S0 = 0.11 (+0.22/-0.03) mJy |
| 2018A&A...620A.152F | 1.1 mm | DPL and Schechter, least squares (Trust Region Reflective) | completeness 94% at 1.2 mJy for point sources |
| 2013MNRAS.432....2K | 870 um | cumulative counts with 1000 flux resamples | N(> 4.2 mJy) = 167.3 (28.6) deg^-2 |
| 2014ApJ...795....5O | 1.2 mm | differential, dlogS = 0.2, Poisson errors | log n = 4.83 (+0.37/-0.45) at 0.13 mJy |

## Count errors

- Absolute flux-scale uncertainty: 20% stated but not included in the analysis (2017ApJ...835...98U);
  propagate it or quantify it separately.
- Poisson (Gehrels) dominates in small fields (2015A&A...584A..78C); cosmic variance from the Moster et al.
  2011 tool with z = 3.5, dz = 3, M* = 10^10.5 Msun (2015A&A...584A..78C).
- 1000 Gaussian flux resamplings, scatter per bin added (2020ApJ...897...91G, 2013MNRAS.432....2K).
- Cosmic variance omitted (2018A&A...620A.152F); counts likely biased low by cosmic variance
  (2018ApJ...869...71Z); 42-58% for a pencil-beam survey (2020ApJ...892...66M).
