# Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies

`2025ApJ...985..194P` | The Astrophysical Journal 2025 | first author: Pigarelli, Alex | arXiv: 2504.15381 | DOI: 10.3847/1538-4357/adc99e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Do z~1.6 cluster galaxies, including those at low mass and well below the star-forming main sequence, have molecular gas fractions that differ from coeval field galaxies, as measured with stacked CO(2-1)?  
  > "we address this problem by probing CO emission to fainter luminosities through stacking analyses with 54 galaxy cluster members in three $z\sim1.6$ galaxy clusters" (Introduction)
- Target **SpARCS J022416-032330 (J0224)**: coordinates _not stated_; z/distance z~1.6  
  > "SpARCS J022416-032330 (“J0224”), SpARCS J022546-035517 (“J0225”), and SpARCS J033056-284300 (“J0330”)." (SpARCS Clusters); distance from _not stated_
- Target **SpARCS J022546-035517 (J0225)**: coordinates _not stated_; z/distance z~1.6  
  > "we explore the CO content of galaxies within three massive ($M_{*} \gtrsim 10^{14} M_{\odot}$) galaxy clusters at z$\sim$1.6" (Observations, SpARCS Clusters); distance from _not stated_
- Target **SpARCS J033056-284300 (J0330)**: coordinates _not stated_; z/distance z~1.6  
  > "we explore the CO content of galaxies within three massive ($M_{*} \gtrsim 10^{14} M_{\odot}$) galaxy clusters at z$\sim$1.6" (Observations, SpARCS Clusters); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00974.S, 2017.1.01228.S, 2021.1.01002.S, 2021.1.01257.S
- bands: Band 3 (CO(2-1)); Band 7 dust continuum  
  > "We also use ALMA Band 7 dust continuum observations" (ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 beams ~0.5''x0.4'' (~4.2x3.4 kpc); Band 7 median 0.45''x0.37''  
  > "The measurement sets have synthesized beams of approximately 0.5$''$$\times$0.4$''$ ($\sim 4.2\times3.4$ kpc)" (ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 3 rms in 50 km/s channels 0.05, 0.04, 0.07 mJy/beam (J0224, J0225, J0330); Band 7 central rms 0.02 mJy/beam  
  > "The central rms in 50 km s$^{-1}$ channels are 0.05 mJy beam$^{-1}$, 0.04 mJy beam$^{-1}$, and 0.07 mJy beam$^{-1}$ for J0224, J0225, and J0330, respectively." (Band 3 CO(2-1) Reduction and Spectral Extraction)
- time on source: 2.91 and 3.33 h (J0224, two pointings), 11.65 h (J0225), 3.94 h (J0330); Band 7 ~35-40 min per pointing  
  > "2.91 and 3.33 hours for two separate pointings in J0224, 11.65 hours combined in a single pointing for J0225, and 3.94 hours in a single pointing for J0330" (ALMA Observations)
- observing dates: _not stated_
- pi or archival as stated: PI: Noble  
  > "(Project code: 2018.1.00974.S, PI: Noble)" (ALMA Observations)
- Line: CO J=2-1 (230.54 GHz)
- Other facility **Herschel (PACS/SPIRE, HerMES)**: Deblended FIR catalogs 100-500 um used for SED fitting  
  > "which have publicly available, deblended FIR catalogs (100/160/250/350/500 $\mu$m)" (SpARCS Clusters)
- Other facility **HST and Spitzer and ground-based imaging**: 18-band UV-FIR photometry for SED fitting  
  > "have been imaged in 18 photometric bands spanning UV-FIR" (SpARCS Clusters)
- External data: Field molecular gas scaling relation (T18) used for comparison  
  > "Work by (cite: 2018ApJ...853..179T) found an empirically-derived “field scaling relation” (hereafter T18" (Introduction) [from (cite: 2018ApJ...853..179T)]
- External data: Star-forming main sequence (S14) for DeltaMS  
  > "offsets from the SFMS ((cite: 2014ApJS..214...15S), hereafter S14)" (Stellar Masses and Star Formation Rates) [from (cite: 2014ApJS..214...15S)]
- External data: Spectroscopic cluster membership and Halpha redshifts  
  > "Currently, 113 cluster members have been identified over all 3 clusters, primarily from their H$\alpha$ emission (cite: 2016A&A...592A.161N)." (SpARCS Clusters) [from (cite: 2016A&A...592A.161N)]

## Processing

### Calibration

- pipeline or manual: CASA ALMA Science Pipeline  
  > "We reduce the ALMA measurement sets using the CASA ALMA Science Pipeline version 6.5.4.9" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- casa version: _not stated_
- pipeline version: 6.5.4.9  
  > "CASA ALMA Science Pipeline version 6.5.4.9" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "cleaned using `tclean` with natural weighting, a stopping threshold of 2.5$\sigma$, manual masking" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- deconvolver: _not stated_
- weighting robust: natural  
  > "cleaned using `tclean` with natural weighting" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- uv taper: _not stated_
- cell size: 8 pixels across beam minor axis (Band 3); 0.037'' (Band 7)  
  > "Each image is created with a cell size chosen such that there are 8 pixels across the minor axis of each of the clean beams." (Band 3 CO(2-1) Reduction and Spectral Extraction)
- image size: _not stated_
- masking: manual masking; stopping threshold 2.5 sigma  
  > "a stopping threshold of 2.5$\sigma$, manual masking" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- multiscale scales: _not stated_
- continuum subtraction: uv-continuum subtraction  
  > "the measurement sets of each cluster are uv-continuum subtracted" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- line free channels: _not stated_
- primary beam correction: enabled, primary beam response 20%  
  > "primary beam response set to 20%, and primary beam correction enabled" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- array combination: two J0225 measurement sets concatenated  
  > "the two J0225 measurement sets are first concatenated" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- smoothing: _not stated_
- final beam: 0.45x0.35'' (J0224), 0.52x0.41'' (J0225), 0.48x0.39'' (J0330)  
  > "The synthesized beams for the images are 0.45$''$$\times$0.35$''$ for J0224, 0.52$''$$\times$0.41$''$ for J0225, and 0.48$''$$\times$0.39$''$ for J0330." (Band 3 CO(2-1) Reduction and Spectral Extraction)
- final rms: 0.05, 0.04, 0.07 mJy/beam in 50 km/s channels  
  > "The central rms in 50 km s$^{-1}$ channels are 0.05 mJy beam$^{-1}$, 0.04 mJy beam$^{-1}$, and 0.07 mJy beam$^{-1}$" (Band 3 CO(2-1) Reduction and Spectral Extraction)

### Inherited from earlier work

- 50 km/s channel binning to be consistent with previously published work on these measurement sets  
  > "to be consistent with previously published work on these measurement sets (see (cite: 2019ApJ...870...56N; 2023ApJ...944..213C))" (Spectral Bootstrapping) [from (cite: 2019ApJ...870...56N; 2023ApJ...944..213C)]
- Spectroscopic redshifts and membership  
  > "H${\alpha}$ spectroscopic redshift (cite: 2016A&A...592A.161N)" (Spectral Stacking) [from (cite: 2016A&A...592A.161N)]
- Luminosity to gas mass conversion method  
  > "We follow the (cite: 2005ARA&A..43..677S) method of calculating the CO line luminosity" (Gas Masses) [from (cite: 2005ARA&A..43..677S)]

### Not stated but needed to reproduce (our reading)

- Stellar mass-metallicity relation and alpha_CO prescription details used (T18 form)
- CIGALE module parameters (tau, age grids, etc.)
- Line-free channel ranges for continuum subtraction
- Per-galaxy stellar masses, SFRs, DeltaMS, redshifts
- Cube image sizes and clean mask definitions
- Spectral extraction aperture sizes per galaxy and exact aperture formula
- Numeric flux scale uncertainty
- Metallicity values (Nantais et al. in prep)

## Analysis recipe

1. **Image Band 3 cubes**: Pipeline reduction, concatenate J0225 sets, uv-continuum subtraction, tclean at 50 km/s  
  > "cleaned using `tclean` with natural weighting, a stopping threshold of 2.5$\sigma$, manual masking" (Band 3 CO(2-1) Reduction and Spectral Extraction)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra**: imfit on moment 0 maps for sizes; elliptical apertures at 4*HWHM/2.355 for detections; 0.8'' circular aperture for undetected from curve of growth  
  > "We use this size aperture for spectral extraction of the CO-undetected galaxies." (Band 3 CO(2-1) Reduction and Spectral Extraction)
   - software: CASA imfit
   - parameter: 0.8'' aperture radius for undetected  
  > "find the total flux from a Gaussian fit flattened beyond a circular aperture radius of 0.8$''$" (Band 3 CO(2-1) Reduction and Spectral Extraction)
   - fitting: 2D Gaussian (imfit)  
  > "We measure the size of each CO-detected cluster member with the `imfit` task in CASA, which fits a 2D Gaussian profile" (Data, Band 3 CO(2-1) Reduction and Spectral Extraction)
   - validation: curve of growth on averaged undetected spectra  
  > "We additionally average the spectra of CO-undetected cluster members shifted to the rest frame to perform a curve of growth analysis" (Data, Band 3 CO(2-1) Reduction and Spectral Extraction)
3. **Derive stellar masses and SFRs**: CIGALE SED fitting with exponentially declining SFH, BC03, Chabrier IMF, Calzetti attenuation; Band 7 and HerMES constraints  
  > "We assume an exponentially declining star formation history with BC03 simple stellar populations" (Stellar Masses and Star Formation Rates)
   - software: CIGALE
   - assumption: Chabrier IMF, Calzetti dust attenuation, SFR averaged over 100 Myr  
  > "star formation rates span $0.1 - 279$ $M_{\odot}$ yr$^{-1}$ averaged over the last 100 Myr" (Stellar Masses and Star Formation Rates)
   - fitting: _not stated_
   - validation: _not stated_
4. **Group and stack spectra**: Shift to rest frame, interpolate to 50 km/s, inverse-variance weighted stacks in LM, HM-aMS, HM-bMS groups and CO-detected/undetected subsets  
  > "stack the spectra in each grouping with inverse-variance weighting according to their line-free channel-to-channel rms" (Spectral Stacking)
   - parameter: LM: logM<10; HM-aMS: logM>10, DeltaMS>-0.3; HM-bMS: logM>10, DeltaMS<-0.3  
  > "The remaining galaxies that are above log($M_{*}/M_{\odot}) > 10.0$ and more than 0.3 dex below the SFMS are considered part of the High Mass-below SFMS grouping" (Spectral Stacking)
   - assumption: SFMS scatter 0.3 dex  
  > "we adopt a scatter of 0.3 dex on the SFMS" (Spectral Stacking)
   - fitting: _not stated_
   - validation: results insensitive to using DeltaMS<0 as the bMS cut  
  > "our results are insensitive to adjusting the below Main Sequence classification to any measurement below the Main Sequence ($<$0 dex offset)" (Spectral Stacking)
5. **Bootstrap uncertainties**: 1,000 resamplings with replacement within each grouping; per-channel std gives uncertainty  
  > "This bootstrapping is performed with 1,000 realizations per grouping and the standard deviation in each channel across all realizations gives the uncertainty" (Spectral Bootstrapping)
   - assumption: Channel-to-channel correlated noise minimal  
  > "We assume that any channel-to-channel correlated noise is minimal and does not impact the spectra." (Spectral Bootstrapping)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit Gaussian line to stacks**: Nested sampling Gaussian fit with bootstrap channel errors; non-parametric SNR  
  > "We model a Gaussian emission line using the `dynesty` package (cite: 2020MNRAS.493.3132S) to perform nested sampling fits" (Bayesian Fitting of Stacked Spectra)
   - software: dynesty
   - parameter: Priors: centroid in (-300,300) km/s, amplitude in (0,1.5) mJy, FWHM in (0.01,500) km/s  
  > "velocity centroid $\in$ (-300,300) km s$^{-1}$; centroid amplitude $\in$ (0.00, 1.50) mJy; FWHM $\in$ (0.01,500) km s$^{-1}$" (Bayesian Fitting of Stacked Spectra)
   - fitting: Uniform prior on amplitude, Gaussian priors on centroid (sigma=63.7 km/s at 0) and FWHM (300±31 LM, 365±21 HM-aMS, 407±61 HM-bMS km/s)  
  > "We assign a uniform prior to the amplitude parameter, and Gaussian priors to the centroid and FWHM parameters." (Bayesian Fitting of Stacked Spectra)
   - validation: _not stated_
7. **Compute gas masses**: L'CO from Solomon & Vanden Bout; M_gas = alpha_CO L'CO / r21  
  > "The line luminosity can be converted into a gas mass through:" (Gas Masses)
   - parameter: r21 = 0.77  
  > "we adopt an excitation factor correction, $r_{21}$, of 0.77" (Gas Masses)
   - assumption: alpha_CO from stellar mass-metallicity correction (T18), weighted average 4.4-6.9  
  > "We find the weighted average $\alpha_{CO}$ for our stacks of spectra to be between 4.4 and 6.9" (Gas Masses)
   - fitting: _not stated_
   - validation: alpha_CO variation checked in discussion  
  > "Nevertheless, we consider what values of $\alpha_{\textrm{CO}}$ would be required for our measured CO luminosities to be in line with the T18 field scaling relation." (Discussion, Variance of alpha_CO)
8. **Determine detection limits**: Inject Gaussian lines into simulated noisy flat spectra, recover with same Bayesian fitter, find flux where 90% have 3sigma detection  
  > "find the lower limit on the injected flux where 90% of the stacked spectra have a 3$\sigma$ detection" (Gas Detection Limits)
   - software: dynesty
   - fitting: same Bayesian fit  
  > "finally attempting to recover the injected flux through the same Bayesian parameter estimation as Section [\ref{subsec:bayesian}]" (Analysis, Gas Detection Limits)
   - validation: _not stated_
9. **Forward model field gas fractions**: Redraw stellar masses and DeltaMS within errors 10,000 times, resample, feed to T18 at z=1.6, add 0.1 dex scatter, compare to measurements  
  > "We Gaussian scatter the quantity log($\mu$) for each realization of “field galaxy groupings” assuming the inherent 0.1 dex scatter on the T18 relation" (Forward Modeling)
   - assumption: average redshift z=1.6  
  > "Using the average redshift of the groupings ($z=1.6$)" (Forward Modeling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9 (pipeline): Calibration, tclean imaging, imfit  
  > "CASA ALMA Science Pipeline version 6.5.4.9" (Band 3 CO(2-1) Reduction and Spectral Extraction)
- **CIGALE** : SED fitting for stellar masses and SFRs  
  > "We use the SED fitting code `CIGALE`" (Stellar Masses and Star Formation Rates)
- **dynesty** : Nested sampling Gaussian fits to stacked spectra  
  > "We model a Gaussian emission line using the `dynesty` package" (Bayesian Fitting of Stacked Spectra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gas mass LM grouping | 1.3 | 0.4 | 1e10 Msun | 7 | we detect average gas masses of 1.3$\pm$0.4 $\times$10$^{10}$ M$_{\odot}$, 5.6$\pm$0.6 $\times$10$^{10}$ M$_{\odot}$, and 3.1$\pm$0.4 $\times$10$^{10}$ M$_{\odot}$ |
| Gas mass HM-aMS | 5.6 | 0.6 | 1e10 Msun | 7 | 5.6$\pm$0.6 $\times$10$^{10}$ M$_{\odot}$ |
| Gas mass HM-bMS | 3.1 | 0.4 | 1e10 Msun | 7 | 3.1$\pm$0.4 $\times$10$^{10}$ M$_{\odot}$ for the LM, HM-aMS, and HM-bMS groupings |
| Gas fractions LM, HM-aMS, HM-bMS | 75%, 65%, 32% | 11%, 8%, 6% | percent | 7 | gas fractions ($f_{gas} = M_{gas}/(M_{gas}+M_{*})$) of 75$\pm$11%, 65$\pm$8%, and 32$\pm$6% respectively |
| 3sigma completeness limit, HM-aMS CO-undetected | 36 | not stated | mJy km/s | 8 | For the HM-aMS CO-undetected grouping, this completeness limit occurs at 36 mJy km s$^{-1}$. |
| alpha_CO needed for HM-bMS CO-detected / undetected to match T18 | 1.74 / 8.81 | not stated | Msun (K km/s pc^2)^-1 | 0 | the HM-bMS CO-detected grouping would require an $\alpha_{\textrm{CO}}$ value of 1.74, and the HM-bMS CO-undetected grouping would need an $\alpha_{\textrm{CO}}$ value of 8.81 |

## Qualitative findings

- Ensemble cluster populations are consistent with field gas fractions; CO-detected and undetected splits below the SFMS deviate in opposite directions  
  > "There is significant variance from the molecular gas field scaling relation in both the gas-rich and gas-deficient directions for the CO-detected and CO-undetected stacks, respectively." (Conclusion)

## Claim tuples

- H: Cluster galaxies as a population differ in gas content from coeval field galaxies | E: Stacked CO(2-1) in three mass/DeltaMS groupings compared to forward-modeled T18 | R: All three 'all' groupings lie within 1 sigma of field-like contours | F: No systematic gas deficiency or enhancement on average | **supported**
- H: Galaxies below the SFMS show environmental gas differences | E: Split HM-bMS into CO-detected and undetected stacks | R: +3 sigma gas-rich and -2 sigma gas-deficient respectively | F: Likely environmental processes, though T18 is not calibrated below the SFMS | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Stacking probes fainter CO luminosities than individual detections  
  > "we address this problem by probing CO emission to fainter luminosities through stacking analyses" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): T18 is not calibrated below the SFMS; limited metallicity info; 6 of 10 HM-bMS CO-undetected galaxies have SFRs constrained only by HerMES upper limits  
  > "the T18 field scaling relation is primarily calibrated for galaxies on or above the SFMS at this redshift" (Comparison of CO-detected to CO-undetected in the bMS Bins)
- Caveat (inferred, ours): SFRs for galaxies without Band 7 coverage rely on upper limits and may bias bMS classification
- Caveat (inferred, ours): alpha_CO from mass-metallicity relation rather than measured
- Caveat (inferred, ours): Stacking mixes detected and undetected members with different aperture choices

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Member catalog with stellar masses, SFRs, redshifts
- Missing: CIGALE configuration
- Missing: Mask definitions and aperture parameters
- Data volume (inferred): ~100-300 GB for four projects (Bands 3 and 7)
- Score (inferred): 3/5, Data and general recipe are given with project codes, but the member catalog, CIGALE settings and alpha_CO details are missing.
- Rediscovery candidate: no, Requires the unpublished member catalog and SED-derived properties.

## Links

- Method: (cite: 2018ApJ...853..179T) (Field scaling relation and alpha_CO metallicity correction)
- Method: (cite: 2022MNRAS.514.4205S) (Non-parametric emission significance)
- Companion: (cite: 2019ApJ...870...56N) (Earlier CO study of the same clusters)
- Companion: (cite: 2023ApJ...944..213C) (CO kinematics of the same clusters)
- Related: SpARCS
- Related: HerMES
- Related: See Change

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 58,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
