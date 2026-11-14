# The Disk Orientations of Perseus Protostellar Multiples at ∼8 au Resolution

`2024ApJ...963..164R` | The Astrophysical Journal 2024 | first author: Reynolds, Nickalas K. | arXiv: 2312.13570 | DOI: 10.3847/1538-4357/ad151d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are circumstellar disks in Perseus protostellar multiples preferentially aligned or randomly oriented, as a test of disk vs turbulent fragmentation  
  > "We performed a statistical analysis on the relative alignment of disk pairs to determine whether the disks are preferentially aligned or randomly distributed." (abstract)
- Target **12 Perseus protostellar multiple systems (e.g. L1448 IRS3B, Per-emb-2, SVS13A)**: coordinates per-source RA/Dec in Table 1 (e.g. L1448 IRS1 03:25:09.45 +30:46:21.84)  
  > "toward 12 protostellar systems in the Perseus molecular cloud (d$\sim$300 pc)" (2.1 Band 6 (1.3 mm) Observations); "L1448 IRS1 | ... | 3:25:9.45 | 30:46:21.84" (Table 1); z/distance ~300 pc  
  > "toward 12 protostellar systems in the Perseus molecular cloud (d$\sim$300 pc)" (2.1 Band 6 (1.3 mm) Observations); "L1448 IRS1 | ... | 3:25:9.45 | 30:46:21.84" (Table 1); distance from average distance to Perseus cloud  
  > "toward 12 protostellar systems in the Perseus molecular cloud (d$\sim$300 pc)" (2.1 Band 6 (1.3 mm) Observations); "L1448 IRS1 | ... | 3:25:9.45 | 30:46:21.84" (Table 1)

## Data provenance

- ALMA projects: 2019.1.01425.S, 2016.1.00337.S
- bands: Band 6 (1.3 mm) primary; Band 3 (3 mm) for three targets  
  > "primarily using Band 6 (1.3 mm) with some supplementary observations in Band 3 (3 mm)" (2 Observations and Data Analysis)
- frequencies and spectral setup: 3 continuum SPWs of 1.875 GHz, 3840 channels; 4 line SPWs of 117.19 MHz  
  > "3 spectral windows setup for 1.875 GHz bandwidth and 3840 channels and four spectral windows used 117.19 MHz bandwidth" (2.1 Band 6 (1.3 mm) Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 6: C-9/10; Band 3: C40-6 and C40-9  
  > "The observations were carried out in the most extended configuration C-9/10 (baselines 150 m$\sim$14.9 km)" (2.1 Band 6 (1.3 mm) Observations); "Data were taken in two ALMA configurations, C40-6 (2017 Aug 1) and C40-9 (2017 September 27)" (2.2 Band 3 (3 mm) Observations)
- baselines: Band 3 combined: 16 m to 14,500 m  
  > "The baselines sampled in the combined dataset ranged from 16 m to 14,500 m." (2.2 Band 3 (3 mm) Observations)
- angular resolution: Band 6 beams 42x23 to 66x29 mas  
  > "effective angular resolution of 42 mas$\times$23 masto 66 mas$\times$29 mas" (2.1 Band 6 (1.3 mm) Observations)
- max recoverable scale: _not stated_
- sensitivity: 13-76 uJy/beam continuum (Briggs robust 1)  
  > "with a continuum sensitivity of 13-76 $\mu$Jy beam$^{-1}$" (2.1 Band 6 (1.3 mm) Observations)
- time on source: ~9 min (5 sources) or ~14 min (7 sources) per source  
  > "with the average time-on-source $\sim$14 minutes for the 3 EBs combined" (2.1 Band 6 (1.3 mm) Observations)
- observing dates: 2019 September 11-18 (Band 6); 2017 Aug 1 and Sep 27 (Band 3)  
  > "between 2019 September 11-18 at Band 6 (1.3 mm)" (2.1 Band 6 (1.3 mm) Observations)
- pi or archival as stated: _not stated_
- Line: 13CO J=2-1 (not stated)
- External data: Multiplicity distribution of Perseus protostellar multiples used to sample model system multiplicity (20-10,000 au)  
  > "following the distribution of Perseus protostellar multiples of (cite: 2022tobinoffnerkratter)" (4.3 Models of Companion Orientations) [from (cite: 2022tobinoffnerkratter)]
- External data: Class, Tbol, Lbol of sources  
  > "Class, T$_{bol}$, and L$_{bol}$are given in (cite: 2018tobinlooneyli; 2008connelley)." (Table 1) [from (cite: 2018tobinlooneyli; 2008connelley)]
- Simulation/model as data: 10,000 model systems per alignment fraction (aligned with 30 deg FWHM normal vs random), compared with observed dot-product distributions  
  > "we generated 10,000 model systems (each system will have at least two sources) for each of the different fractions of systems with fractional orientations" (4.3 Models of Companion Orientations)

## Processing

### Calibration

- pipeline or manual: ARC pipeline calibration; phase-only self-calibration  
  > "The raw visibility data were calibrated by the North American ARC staff using Common Astronomy Software Applications (CASA) version 6.2.1 automated pipeline." (2.1 Band 6 (1.3 mm) Observations)
- casa version: 6.2.1 pipeline (Band 6); 6.5.0-15 imaging; 4.7.2 (Band 3)  
  > "The data were pipeline processed by the observatory using the pipeline included in CASA 4.7.2 (r39732)." (2.2 Band 3 (3 mm) Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0341+3352 and J0338+3106 (Band 6); J0238+1636 (Band 3)  
  > "J0336$+$3218 | J0237$+$2848 | J0341$+$3352" (Table 2)
- flux scale uncertainty: ~10%  
  > "While the absolute flux density scale is expected to be accurate to $\sim$10%" (2.1 Band 6 (1.3 mm) Observations)
- self calibration: 4-5 rounds phase-only, solints from EB length down to single integration (Per-emb-2 excluded)  
  > "We performed 4 to 5 rounds of phase-only self calibration, with the first round of intervals starting at the full length of the EB" (2.1 Band 6 (1.3 mm) Observations)

### Imaging

- task: tclean (Band 6, CASA 6.5.0-15); clean (Band 3)  
  > "The data were imaged using CASA version 6.5.0-15 with the task *tclean*" (2.1 Band 6 (1.3 mm) Observations)
- deconvolver: MTMFS, 2 Taylor terms  
  > "we used the Multi-(Taylor-)term Multi-Frequency Synthesis (MTMFS) with scale sizes of 0, 5, and 20 pixels and 2 Taylor terms" (2.1 Band 6 (1.3 mm) Observations)
- weighting robust: Briggs robust 1.0 (Band 6); superuniform (Band 3)  
  > "restoring the images with super-uniform weighting scheme to closely match the beamsize of the 1.3 mm observations" (2.2 Band 3 (3 mm) Observations)
- uv taper: _not stated_
- cell size: 4 mas (Band 6); 5 mas (Band 3)  
  > "image sizes of 9000$\times$9000and 4 mas per pixel" (2.1 Band 6 (1.3 mm) Observations)
- image size: 9000x9000 (Band 6); 2048x2048 (Band 3)  
  > "image sizes of 2048$\times$2048 pixels and 5 mas pixels" (2.2 Band 3 (3 mm) Observations)
- masking: auto-multithresh with sidelobethreshold 2.0, checked against user mask (Band 6); hand-drawn masks (Band 3)  
  > "defining the sidelobe threshold sub-parameter to be 2.0" (2.1 Band 6 (1.3 mm) Observations)
- multiscale scales: 0, 5, 20 pixels  
  > "scale sizes of 0, 5, and 20 pixels" (2.1 Band 6 (1.3 mm) Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C40-6 and C40-9 imaged together (Band 3)  
  > "The final self-calibrated data were imaged together using the CASA task *clean*" (2.2 Band 3 (3 mm) Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Band 6 RMS 13-76 uJy/beam per source; common 20 uJy/beam display level  
  > "RMS is specified as the root-mean-squared of the Briggs robust 1 weighted image with the upper 95%of emission clipped." (Table 1)

### Inherited from earlier work

- 30 deg FWHM for preferentially aligned distribution and 30 deg alignment definition  
  > "normal distribution described by a full-width-half-maximum value of 30$^{\circ}$ (cite: 2019leeoffner)" (4.3 Models of Companion Orientations) [from (cite: 2019leeoffner)]
- Companion-finding algorithm similar to prior work  
  > "We made use of a method similar to the one implemented by (cite: 2022tobinoffnerkratter)" (4.1 Companion Finding) [from (cite: 2022tobinoffnerkratter)]
- Direct visibility fitting technique  
  > "Similar techniques were applied to protoplanetary disks (cite: 2022jenningsdhsarp; 2022jenningstaurus)" (2.3 Gaussian Fitting the uv-visibilities) [from (cite: 2022jenningsdhsarp; 2022jenningstaurus)]

### Not stated but needed to reproduce (our reading)

- Number of walkers, live points, priors and convergence criteria for uv Gaussian fits (emcee/dynesty/pdspy)
- uv-fit prior ranges for sizes, flux and angles
- Line-free channels / continuum channel selection for Band 6
- Self-cal reference model and exact solint per source
- Which flux calibrator per EB and flux-scale handling
- Random seeds and exact sampling of sources chosen for pairs
- Exact Gaussian vs ECDF construction of model pair distributions and scipy function settings
- Per-source clean thresholds

## Analysis recipe

1. **Calibrate and self-calibrate**: ARC pipeline calibration then 4-5 rounds phase-only self-calibration  
  > "We performed 4 to 5 rounds of phase-only self calibration" (2.1 Band 6 (1.3 mm) Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum**: tclean MTMFS with auto-multithresh, Briggs robust 1  
  > "The final images were checked by simultaneously cleaning the data with a conservative user-defined mask." (2.1 Band 6 (1.3 mm) Observations)
   - software: CASA tclean
   - parameter: scales 0,5,20 pix; 4 mas pixels; sidelobethreshold 2.0  
  > "scale sizes of 0, 5, and 20 pixels and 2 Taylor terms" (2.1 Band 6 (1.3 mm) Observations)
   - fitting: _not stated_
   - validation: Cleaned with conservative user mask as check  
  > "The final images were checked by simultaneously cleaning the data with a conservative user-defined mask." (2.1 Band 6 (1.3 mm) Observations)
3. **Fit disk geometry (PA, inclination) per source**: Multi-component 2-D Gaussians fit to visibilities (uv>400 kλ) with Bayesian inference; image-plane imfit as cross-check  
  > "We constrained the sources using Bayesian inference, fitting multi-component 2-D Gaussians to the visibilities of each individual source" (2.3 Gaussian Fitting the uv-visibilities)
   - software: emcee, dynesty, pdspy, CASA imfit
   - parameter: uv-distance > 400 kλ; phase center within 0.5" of published positions  
  > "by restricting the *uv*-distance $>$400 k$\lambda$" (2.3 Gaussian Fitting the uv-visibilities)
   - assumption: Disks axisymmetric and geometrically thin; i = arccos(sigma_minor/sigma_major); distance 300 pc  
  > "We assumed that the disks are axisymmetric and geometrically thin" (4.2 Geometric Orientations)
   - fitting: Errors are 1 sigma from median of posterior  
  > "The errors reported are derived as the 1 $\sigma$uncertainty from the median of the sampled posterior." (2.3 Gaussian Fitting the uv-visibilities)
   - validation: uv and image-plane results consistent within 3 sigma  
  > "find the results between the *uv*-visibility and image plane analysis are consistent within 3 $\sigma$" (2.3 Gaussian Fitting the uv-visibilities)
4. **Build model populations**: 10,000 model systems per aligned/random fraction; aligned drawn with 30 deg FWHM normal, random from uniform in cos i; same projection bias applied  
  > "Randomly aligned systems are constructed by drawing the position angle and inclination from a uniform distribution of inverse cosine from 0 to 1." (4.3 Models of Companion Orientations)
   - assumption: Stellar and disk angular momentum axes aligned; no separation-dependent weighting  
  > "under the assumption the stellar angular momentum axis and disk angular momentum axis are aligned" (4.3 Models of Companion Orientations)
   - fitting: _not stated_
   - validation: Results insensitive to ±5 deg change of 30 deg  
  > "the results presented are not significantly changed if moderate deviations ($\pm$5$^{\circ}$) from 30$^{\circ}$is chosen" (4.3 Models of Companion Orientations)
5. **Statistical comparison of dot-product distributions**: Resample observations 10,000 times with Gaussian errors; 2-sample KS, AD, Epps-Singleton tests vs each model fraction; reject at 0.3%  
  > "We set a null-hypothesis rejection threshold of 0.3% (3 $\sigma$)" (4.4 Statistical Tests)
   - software: scipy
   - parameter: Subsamples <100 au, >500 au, <10,000 au; Method A pairing (N_s-1 pairs per system)  
  > "This gives us N$_{s} - 1$number of pairs per system" (4.4 Statistical Tests)
   - fitting: _not stated_
   - validation: Image-plane analysis gives consistent results; Methods B and C do not change results significantly  
  > "We chose Method A for our analysis, but the results presented in this work do not change significantly for any of the methods." (Comparison of Orientation Vectors)

## Software

- **CASA** 6.2.1 (pipeline), 6.5.0-15 (imaging), 4.7.2 (Band 3): Calibration, tclean/clean imaging, self-calibration, imfit  
  > "The data were imaged using CASA version 6.5.0-15 with the task *tclean*" (2.1 Band 6 (1.3 mm) Observations)
- **emcee** : Bayesian uv-visibility fitting  
  > "using (cite: emcee; 2020dynesty; 2022pdspy)" (2.3 Gaussian Fitting the uv-visibilities)
- **dynesty** : Nested sampling of uv fits  
  > "using (cite: emcee; 2020dynesty; 2022pdspy)" (2.3 Gaussian Fitting the uv-visibilities)
- **pdspy** : uv-visibility modeling framework  
  > "using (cite: emcee; 2020dynesty; 2022pdspy)" (2.3 Gaussian Fitting the uv-visibilities)
- **scipy** : KS, AD and ES tests  
  > "we apply all three tests, KS, AD, and ES test (as implemented in *scipy*)" (Statistical Tests (appendix))

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of sources detected | 32 | not stated | sources | 3 | resolving and detecting 32 sources within the field of view of the targeted sources |
| Number of pairs, <100 au / >500 au / <10,000 au | 7 / 15 / 21 | not stated | pairs | 5 | with separations $<$100 au (N$_{pairs}$=7) |
| Median relative orientation angle, Class 0 sources | 24 | not stated | deg | 5 | we found the median relative orientation angle between the sources in each system is 24$^{\circ}$for the Class 0 sources |
| Per-emb-2-A/B binary separation | 24 | not stated | au | 3 | previously reported compact ($a=$24 au) binary Per-emb-2-A/-B |
| Allowed aligned fraction, full sample (<10,000 au) | 40%-80% | not stated | fraction aligned | 5 | with the underlying distribution described as 40%-80%preferentially aligned systems |

## Qualitative findings

- Per-emb-5 resolved as a single ringed disk with a one-armed spiral, not a close binary  
  > "Per-emb-5 is now resolved and appears as a ringed disk with a single spiral arm extending to the west." (7 Conclusions)
- Additional faint compact source at geometric center of L1448 IRS3B inner ring  
  > "we confidently detected an additional continuum source at the geometric center of the inner disk ring" (7 Conclusions)

## Claim tuples

- H: Compact (<100 au) multiples have preferentially aligned disks | E: Compare observed dot-product ECDF with mixture models | R: Underlying distribution at least 40% preferentially aligned; random-dominated ruled out | F: Consistent with disk fragmentation for compact pairs | **supported**
- H: Wide (>500 au) pairs are more randomly aligned | E: Same tests on >500 au subsample | R: 40%-80% aligned equally likely | F: Cannot conclusively determine fraction; statistically different from compact sample per abstract | **partially**
- H: Full sample is purely aligned or purely random | E: Tests on <10,000 au sample | R: Both pure cases ruled out | F: Hybrid of gravitational instability and turbulent fragmentation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv fitting avoids CLEAN and beam biases for compact sources  
  > "we desired an alternate fitting method to measure the source parameters independent of the images produced with the CLEAN algorithm" (2.3 Gaussian Fitting the uv-visibilities)
- Alternative: Pairing Methods B (all permutations) and C (reference source) considered; Method A chosen  
  > "We chose Method A for our analysis, but the results presented in this work do not change significantly for any of the methods." (Comparison of Orientation Vectors)
- How they decided it was enough: _not stated_
- Limitation (authors): Low number of pairs prevents determining exact aligned fraction  
  > "With the relatively low number of statistics (at most 21 pairs of sources), we were not able to determine the exact underlying fractional alignment ratio" (5.1 Formation Pathways)
- Limitation (authors): Continuum only: cannot distinguish aligned from anti-aligned disks  
  > "we were unable to differentiate between aligned and anti-aligned disks" (4.2 Geometric Orientations)
- Caveat (inferred, ours): Gaussian-derived inclination assumes thin axisymmetric disks; optically thick or ringed disks bias i
- Caveat (inferred, ours): Excluding 100-500 au pairs and small N limit statistical power
- Caveat (inferred, ours): Marginally resolved sources have poorly constrained PA
- Caveat (inferred, ours): Mixture model is simple and ignores separation dependence

## Reproducibility

- Data public (paper): Data cited by ALMA project codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01425.S and 2017.1.00337.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Sampler settings and priors for uv fits
- Missing: Custom model-generation and statistics code not released
- Missing: Self-calibration details per source
- Data volume (inferred): ~100-500 GB raw for C-9/10 Band 6 plus Band 3 datasets
- Score (inferred): 3/5, Public data and clear workflow, but sampler priors, code and some settings missing.
- Rediscovery candidate: no, Recipe lacks fit priors and code; results hinge on custom statistics.

## Links

- Method: (cite: 2022jenningsdhsarp) (Direct visibility fitting approach)
- Method: (cite: 2022tobinoffnerkratter) (Companion-finding method and multiplicity distribution)
- Companion: (cite: 2018tobinlooneyli) (Earlier ALMA VANDAM follow-up of the same multiples)
- Companion: (cite: 2021reynoldstran) (Prior ALMA study of L1448 IRS3B)
- Related: VANDAM Survey

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.1.00337.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 59,
  "rate": 0.747
 },
 "evidence_ok": true
}
```
