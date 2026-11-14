# Identifying Variability in Deeply Embedded Protostars with ALMA and CARMA

`2019ApJ...871..149F` | The Astrophysical Journal 2019 | first author: Francis, Logan | arXiv: 1902.00588 | DOI: 10.3847/1538-4357/aaf972

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Can brightness variability of deeply embedded protostars in Serpens Main be detected by comparing 2007 CARMA and 2016 ALMA 1.3 mm interferometric observations, and what sensitivity to variability do ALMA-only comparisons imply?  
  > "The goal of this work is thus to develop and apply methods for comparing interferometric data in a variability study of deeply embedded protostars." (Introduction)
- Target **Serpens Main Class 0/I protostars (Ser-emb 1-9, 11, 15, 17)**: coordinates Pointing centers listed per source, e.g. Ser-emb 1 18:29:09.09 +00:31:30.9  
  > "The Serpens Main star forming region is located $436.0 \pm 9.2$ pc away (cite: ortiz-leon2017) and contains 34 Class 0 and I protostars (cite: dunham2015)." (2 Observations and Standard Calibrations); "Ser-emb 1 | 18:29:09.09 +00.31.30.9 | 0 | Y" (Table 1); z/distance 436.0 ± 9.2 pc  
  > "The Serpens Main star forming region is located $436.0 \pm 9.2$ pc away (cite: ortiz-leon2017) and contains 34 Class 0 and I protostars (cite: dunham2015)." (2 Observations and Standard Calibrations); "The Serpens Main star forming region is located $436.0 \pm 9.2$ pc away" (Observations and Standard Calibrations); distance from Ortiz-León et al. 2017 (cite: ortiz-leon2017)  
  > "The Serpens Main star forming region is located $436.0 \pm 9.2$ pc away (cite: ortiz-leon2017) and contains 34 Class 0 and I protostars (cite: dunham2015)." (2 Observations and Standard Calibrations); "located $436.0 \pm 9.2$ pc away (cite: ortiz-leon2017)" (Observations and Standard Calibrations)

## Data provenance

- ALMA projects: 2015.1.00310.S, 2018.1.00917.S
- bands: Band 6 (1.3 mm, 233 GHz)  
  > "$233$ GHz ($1.3$ mm) Band 6 continuum observations of the Serpens sources" (2.1 ALMA Observations and Calibration)
- frequencies and spectral setup: SPW centers 224, 226, 240, 242 GHz; 128 channels of 15.625 MHz  
  > "Spectral Window Center Freqs. (GHz)            | 224, 226, 240, 242" (Table 2)
- continuum bandwidth: 8 GHz total; 7 GHz after flagging edge channels  
  > "Excluding the flagged edge channels, the bandwidth is 7 GHz." (Table 2)
- arrays: _not stated_
- configurations: C36-6, 39 antennas  
  > "Configuration                                  | C36-6" (Table 2)
- baselines: 10-808 kλ  
  > "Proj. baseline range (k$\lambda$)              | 10-808" (Table 2)
- angular resolution: 0.3 arcsec  
  > "Resolution ($''$)                              | 0.3" (Table 2)
- max recoverable scale: 3.0 arcsec  
  > "Maximum Recoverable Scale$^{b}$ ($''$)         | 3.0" (Table 2)
- sensitivity: requested continuum RMS 0.1 mJy  
  > "Our 2016 ALMA observations were requested to reach a continuum RMS noise level of 0.1 mJy" (4.1 Continuum RMS Noise of Observations)
- time on source: ~2 minutes per source (1.75 min in table)  
  > "totalling $\sim2$ minutes on source" (2.1 ALMA Observations and Calibration)
- observing dates: 21 July 2016  
  > "Observation date(s)                            | 21 July 2016" (Table 2)
- pi or archival as stated: _not stated_
- Other facility **CARMA**: 2007 230 GHz C-configuration archival tracks (project cx190) as first epoch  
  > "Project code | cx190" (Table 3)
- Other facility **JCMT Transient Survey**: Context: 850 um monitoring showing SMM1 rising ~5%/yr  
  > "SMM1, a bright intermediate mass Class 0 protostar, is rising in brightness by $\sim5 \%$yr$^{-1}$" (1 Introduction)
- External data: Source sample and Class from Bolocam/Spitzer comparison  
  > "previously identified in comparisons of Bolocam and Spitzer maps (cite: enoch2009)" (2 Observations and Standard Calibrations) [from (cite: enoch2009)]
- External data: CARMA 230 GHz maps and ~20% absolute flux accuracy  
  > "$\sim$20% for the CARMA observations (cite: enoch2011)" (5.4 Relative Flux Calibration Factors and Variability of Sources) [from (cite: enoch2011)]
- External data: Spitzer c2d/GB YSO properties  
  > "This table adapted from table 2 of (cite: dunham2015)." (Table 14) [from (cite: dunham2015)]
- External data: SMM1 rising ~5%/yr  
  > "which is rising by $\sim5\%/yr$ in the Transient Survey (cite: johnstone2018)" (6 Discussion & Conclusion) [from (cite: johnstone2018)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline for ALMA; manual MIRIAD calibration for CARMA  
  > "were applied to the raw visibility data using the ALMA pipeline in version 4.5.3 of the Common Astronomy Software Applications (CASA) package" (2.1 ALMA Observations and Calibration); "The archived raw data were obtained and manually calibrated using the MIRIAD data reduction package" (2.2 CARMA Observations and Calibration)
- casa version: CASA 4.5.3 (pipeline); CASA 4.7.2 (imaging)  
  > "produced using the `clean` task in CASA 4.7.2" (3 Reduced ALMA Maps and Source Identification)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939 (ALMA)  
  > "Flux calibrator                                | J1751+0939" (Table 2)
- flux scale uncertainty: ~10% Band 6 ALMA  
  > "nominal Band 6 flux calibration accuracy of $\sim$10% (cite: almatechcycle3)" (4.2 Comparison of First and Second ALMA Scans)
- self calibration: Phase-only with gaincal, 2-3 iterations with decreasing solint from scan length to integration time  
  > "Phase-only self-calibration using the CASA `gaincal` task was attempted for every science target in the full data set and each single scan subset." (2.1 ALMA Observations and Calibration)

### Imaging

- task: CASA clean, multi-frequency synthesis  
  > "The `clean` task was then run in multi-frequency synthesis mode to a threshold of 3$\sigma$" (3 Reduced ALMA Maps and Source Identification)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.25  
  > "using Briggs weighting with robust=0.25 and a pixel size of 0.06$''$ to produce 60x60$''$ maps" (3 Reduced ALMA Maps and Source Identification)
- uv taper: Gaussian taper with FWHM equal to the matched CARMA beam major axis  
  > "The taper used is equivalent to smoothing by a circular Gaussian kernel with FWHM equal to the major axis of the corresponding matched CARMA beam" (5.2)
- cell size: 0.06 arcsec  
  > "using Briggs weighting with robust=0.25 and a pixel size of 0.06$''$ to produce 60x60$''$ maps" (3 Reduced ALMA Maps and Source Identification)
- image size: 60x60 arcsec  
  > "a pixel size of 0.06$''$ to produce 60x60$''$ maps" (3 Reduced ALMA Maps and Source Identification)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: to limiting response 0.1 (40 arcsec diameter)  
  > "All maps were primary beam corrected to a limiting response level of 0.1, corresponding to an image diameter of $40\ensuremath{''}$." (3 Reduced ALMA Maps and Source Identification)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CARMA data reduction/targets and 230 GHz maps from earlier survey  
  > "(cite: enoch2011) observed nine of the deeply embedded protostars in Serpens" (2.2) [from (cite: enoch2011)]
- Relative flux calibration strategy  
  > "we turn to relative flux calibration methods similar to those used in the JCMT Transient Survey (cite: mairs2017a)" (4.2) [from (cite: mairs2017a)]
- Simulated re-observation approach  
  > "A similar approach was successfully used by (cite: hunter2017) for detecting variability between SMA and ALMA observations" (5.3) [from (cite: hunter2017)]

### Not stated but needed to reproduce (our reading)

- Clean mask definitions and iteration limits
- CARMA calibration details (flagging, flux calibrator models) in MIRIAD
- Exact self-calibration solution intervals and which sources succeeded
- Box regions per source for the Box Method
- Exact CARMA imaging parameters and the uv-cut applied per track
- Clean threshold values in mJy per field

## Analysis recipe

1. **Calibrate and self-calibrate ALMA data**: ALMA pipeline then phase-only self-calibration with gaincal, full data and single-scan subsets  
  > "Where successful, self-calibration was repeated 2-3 times with successively smaller solution intervals ranging from the scan duration to the integration time" (2.1)
   - software: CASA
   - fitting: _not stated_
   - validation: SNR improved up to 30% for bright targets  
  > "self-calibration provided an improvement of up to $30~$% in SNR" (2.1)
2. **Image ALMA continuum and measure source fluxes**: clean MFS, Briggs robust 0.25; Gaussian fits  
  > "After correction, the flux of point-like sources was measured by Gaussian fitting." (3)
   - software: CASA clean
   - fitting: _not stated_
   - validation: _not stated_
3. **ALMA-only first vs second scan variability limits via rFCFs**: Image each scan separately, measure Box and Gaussian peak/integrated fluxes, fit weighted average of flux ratios (σ^-2) for bright (>10 mJy) and dim sources  
  > "each point is weighted by $\sigma^{-2}$, where $\sigma$ is the uncertainty in the ratio" (4.2)
   - software: CASA imfit
   - fitting: weighted average of ratios; uncertainty is weighted standard deviation  
  > "The overall uncertainty in the rFCF is given by the standard deviation of the ratios" (4.2)
   - validation: random antenna dropping tests (2,4,8 of 39)  
  > "These tests were done removing 2, 4, or 8 of the 39 antennas from each scan" (4.2)
4. **Match ALMA and CARMA beams by uv-plane matching**: Keep visibilities whose nearest-neighbour distance as fraction of CARMA uv-distance < f_cut=0.25; apply uv-taper to ALMA  
  > "we use $f_\text{cut}=0.25$ in every comparison" (5.2)
   - software: CASA
   - fitting: _not stated_
   - validation: compared matched beam shapes  
  > "improves the agreement in beam shapes to within $\sim0.1\ensuremath{''}$ or better for both axes" (5.2)
5. **Simulated CARMA re-observation of ALMA maps**: simobserve with CARMA antenna positions, schedule, flagging; no noise; uv cut >30 m; taper  
  > "only including visibilities more than 30m from the $uv$-plane origin" (5.3)
   - software: CASA simobserve
   - fitting: _not stated_
   - validation: compare simulated and matched beam shapes  
  > "The simulated and $uv$-plane matched beam shapes are compared against each other in table" (Simulated Re-observations of ALMA sources with CARMA)
6. **Derive CARMA-to-ALMA rFCFs and test for variability**: Fit average of ALMA/CARMA Box peak flux ratios per track; compute percent difference and detection sigma  
  > "We therefore calculate rFCFs by fitting an average to the ratio of ALMA to CARMA Box peak fluxes" (5.4)
   - fitting: weighted average  
  > "When fitting the average to determine the rFCF, each point is weighted by $\sigma^{-2}$, where $\sigma$ is the uncertainty in the ratio" (Comparison of First and Second ALMA Scans)
   - validation: consistency of two beam-comparison methods  
  > "differences in the flux calibration factors across beam comparison methods are consistent with each other" (5.4)

## Software

- **CASA** 4.5.3 (pipeline), 4.7.2 (imaging): calibration, self-calibration, clean, imfit, simobserve, importmiriad  
  > "further processing and imaging of the data were carried out in CASA" (2.2)
- **MIRIAD** : manual calibration of archival CARMA data  
  > "manually calibrated using the MIRIAD data reduction package" (2.2)
- **CASA analysisUtils** : listed as software used  
  > "CASA analysisUtils[^6], Python version 2.7, astropy" (Acknowledgements)
- **astropy, aplpy, matplotlib** Python 2.7: analysis and plotting  
  > "astropy (cite: astropy2013), aplpy (cite: aplpy2012), and matplotlib (cite: matplotlib2007)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA dynamic range limit | ~400 | not stated | dimensionless | 2 | We find through a fit to the expected noise behaviour for our observations after self-calibration (blue curve in figure [4](#fig:brt_pk_contam).) that the dynamic range limit is $\sim400$. |
| rFCF Box peak flux, bright sources (ALMA scan1/scan2) | 0.998 | 0.007 | dimensionless | 3 | Box Peak Flux           / 1.006 (0.033) / 0.998 (0.007) / |
| rFCF Box peak flux, dim sources | 1.006 | 0.033 | dimensionless | 3 | Box Peak Flux           / 1.006 (0.033) / 0.998 (0.007) / |
| ALMA-only variability sensitivity, dim source (3 mJy) | ~16 | not stated | % | 3 | we are thus sensitive to variability at the $\sim16\%$ level for representative dim sources (3 mJy; 3% flux error) |
| ALMA-only variability sensitivity, bright source (10 mJy) | ~4.8 | not stated | % | 3 | at the $\sim4.8\%$ level for bright sources (10 mJy; 1% flux error) |
| CARMA rFCF scatter σ_rFCF | ~40 | not stated | % | 6 | We find $\sigma_\text{rFCF}$ to be $\sim40\%$ for either beam comparison method |
| 3σ variability detection limit, tracks C1.2/C1.5 | ~24-60 | not stated | % | 6 | is $\sim24-60\%$ for tracks C1.2 and C1.5 and $\sim75-180\%$ for track C2.3 |
| 3σ variability detection limit, track C2.3 | ~75-180 | not stated | % | 6 | is $\sim24-60\%$ for tracks C1.2 and C1.5 and $\sim75-180\%$ for track C2.3 |
| SMM1-a (ID 10) flux change CARMA C1.2 vs ALMA (beam matching) | -3.29 | 7.44 | % | 6 | / 10 / 876.38 (67.20)        / 847.56 (5.47)        / -3.29 (7.44)       / 0.44               / |

## Qualitative findings

- No source varies above ~1σ in either beam-matching or simulated re-observation comparisons  
  > "No source is seen to vary above $\gtrsim 1 \sigma$ by either the beam matching or simulated observation analysis." (5.4)
- ALMA found sources in every field, including three that CARMA did not detect  
  > "our observations find sources in every field owing to ALMA’s higher sensitivity" (3)

## Claim tuples

- H: Deeply embedded protostars in Serpens varied detectably between 2007 CARMA and 2016 ALMA | E: uv-matched and simulated-reobservation flux comparison with rFCFs | R: No variation above ~1σ; detection limits ~24-180% | F: No variability detected above limits due to low CARMA SNR and few common sources | **supported**
- H: Repeated ALMA observations can detect low-level variability | E: Compare first and second scans with rFCFs | R: ~4.8% sensitivity for 10 mJy sources, ~16% for 3 mJy sources | F: A second ALMA epoch could detect few-percent variability for bright sources | **supported**
- H: uv-matching and simulated re-observation both permit cross-array comparison | E: Both methods applied to the same tracks | R: Similar rFCF precision and beam matching | F: Methods similarly effective; matching simpler | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Relative flux calibration avoids the ~10% absolute flux accuracy limit  
  > "To sidestep this problem, we turn to relative flux calibration methods similar to those used in the JCMT Transient Survey" (4.2)
- Alternative: Comparing CARMA D/E with ALMA by discarding long baselines was rejected due to a factor 2-3 SNR drop  
  > "this would result in at least a factor of 2-3 drop in the ALMA SNR, and thus we do not attempt to do so" (2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Low CARMA SNR and few common sources hinder robust rFCFs  
  > "The greatest limitations in our comparisons are imposed by the relatively low signal to noise of the CARMA data" (6)
- Caveat (inferred, ours): Only 3 usable CARMA tracks so σ_rFCF poorly constrained
- Caveat (inferred, ours): Frequency difference 230 vs 233 GHz and spectral-index effects not corrected
- Caveat (inferred, ours): Matched beams still differ by ~0.1-0.3 arcsec

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; CARMA data from the archive  
  > "The archived raw data were obtained and manually calibrated using the MIRIAD data reduction package" (2.2)
- Products in archive: _not stated_
- Missing: Custom beam-matching and rFCF code not released
- Missing: Box regions and clean masks not given
- Data volume (inferred): ~10-50 GB (ALMA 12 fields snapshot plus CARMA archive tracks)
- Score (inferred): 5/5, Data public and method described with many parameters, but no code and several settings missing.
- Rediscovery candidate: no, Requires CARMA archival reduction and custom code; results are mostly upper limits.

## Links

- Method: (cite: mairs2017a) (relative flux calibration strategy)
- Method: (cite: hunter2017) (simulated re-observation variability approach)
- Companion: (cite: enoch2011) (CARMA survey of the same sources)
- Companion: (cite: johnstone2018) (JCMT Transient Survey variability results)
- Related: JCMT Transient Survey
- Related: CARMA Serpens survey
- Related: Spitzer c2d/Gould Belt

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 57,
  "rate": 0.731
 },
 "evidence_ok": true
}
```
