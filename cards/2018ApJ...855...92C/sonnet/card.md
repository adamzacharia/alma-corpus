# ALMA’s Polarized View of 10 Protostars in the Perseus Molecular Cloud

`2018ApJ...855...92C` | The Astrophysical Journal 2018 | first author: Cox, Erin G. | arXiv: 1802.00449 | DOI: 10.3847/1538-4357/aaacd2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the origin of dust polarization (scattering, magnetically aligned grains, radiative alignment) on disk and envelope scales in Class 0/I protostars?  
  > "Our principle survey goal was to examine the polarization structure of a set of young protostars to see whether we could explain it in the context of models that predict polarization due to different mechanisms" (Discussion)
- Target **10 Perseus protostars (Per-emb-2, 5, 11, 14, 18, 26, 29, 41, 50 and one other)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01503.S
- bands: Band 7 (870 um)  
  > "The data were taken using ALMA Band 7 on 2016, July 17 in configuration C40-4" (2.2 Observations and Data Reduction)
- frequencies and spectral setup: 4 continuum spectral windows centered on 337.5, 339.4, 347.5, 349.5 GHz; full polarization  
  > "The 4 spectral windows were centered on 337.5, 339.4, 347.5, and 349.5 GHz." (2.2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4  
  > "in configuration C40-4" (2.2 Observations and Data Reduction)
- baselines: 15 to 704 m  
  > "Baselines for the C40-4 configuration ranged from 15 to 704 meters" (2.2 Observations and Data Reduction)
- angular resolution: ~0.35 arcsec; typical 0.38 x 0.31 arcsec  
  > "The typical resolution for our observations was 0.38$\ensuremath{''}$ by 0.31$\ensuremath{''}$." (2.2 Observations and Data Reduction)
- max recoverable scale: ~7.2 arcsec  
  > "corresponding to a maximum recoverable scale of $\sim 7.2 \ensuremath{''}$" (2.2 Observations and Data Reduction)
- sensitivity: _not stated_
- time on source: 2.6 hours total, ~8 min per source  
  > "The observations took a total of 2.6 hours, with $\sim$8 minutes spent per source." (2.2 Observations and Data Reduction)
- observing dates: 2016 July 17  
  > "The data were taken using ALMA Band 7 on 2016, July 17" (2.2 Observations and Data Reduction)
- pi or archival as stated: PI Erin Cox  
  > "project code 2015.1.01503.S; P.I. Erin Cox" (2.2 Observations and Data Reduction)
- Other facility **VLA VANDAM survey**: Sample selection and disk-candidate classification from 8 mm data  
  > "Our target selection was constructed from our Very Large Array Nascent Disk and Multiplicity (VANDAM) survey" (2.1 Sample Selection)
- Other facility **SMA MASSES**: 220 GHz brightness for sample selection  
  > "then chose the brightest 25 at 220 GHz from the Submillimeter Array (SMA) Mass Assembly of Stellar Systems and their Evolution (MASSES) survey" (2.1 Sample Selection)
- External data: Outflow position angles  
  > "We also present the polarization properties and outflow angles (taken from (cite: st17), and references therein)." (3 Results) [from (cite: st17)]
- External data: Disk-candidate classification and disk inclinations (45-65 deg)  
  > "these disks’ inclinations range from $\sim 45-65^\circ$ (cite: se16)" (Discussion) [from (cite: se16); (cite: se17)]

## Processing

### Calibration

- pipeline or manual: Manual reduction by NRAO analysts  
  > "These observations were reduced manually by data analysts at the National Radio Astronomy Observatory (NRAO)" (2.2 Observations and Data Reduction)
- casa version: CASA 4.7.0  
  > "version 4.7.0" (2.2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 (flux); J0336+3218 phase; J0237+2848 bandpass; J0510+1800 polarization  
  > "The sources J0336+3218, J0238+1636, J0237+2848, and J0510+1800 were used to calibrate the phase, flux, bandpass, and polarization, respectively." (2.2 Observations and Data Reduction)
- flux scale uncertainty: 10% (not included in reported errors)  
  > "The overall amplitude calibration uncertainty at Band 7 for ALMA is 10%" (2.2 Observations and Data Reduction)
- self calibration: One iteration of phase-only self-cal over integration time; Per-emb-41 over 6 s  
  > "Per-emb-41, however, was bright enough to self-calibrate over a 6 second interval." (2.2 Observations and Data Reduction)

### Imaging

- task: CASA CLEAN  
  > "We used the CASA task `CLEAN`, with natural weighting, to produce the final, full Stokes images for all sources." (2.2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting" (2.2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.38 x 0.31 arcsec typical  
  > "The typical resolution for our observations was 0.38$\ensuremath{''}$ by 0.31$\ensuremath{''}$." (2.2 Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Disk-candidate classification via 8 mm visibility profile fitting  
  > "indicates a source identified as a disk-candidate on the basis of fitting the 8 mm visibility profile (cite: se16)" (Table notes) [from (cite: se16); (cite: se17)]

### Not stated but needed to reproduce (our reading)

- Clean thresholds, iterations, masks, cell and image size
- Stokes I rms and polarization noise values per source
- Per-emb source coordinates and adopted distance to Perseus
- Self-calibration solution interval for the other sources
- Exact sampling grid for the Kaplan-Meier and angle-offset analysis
- Outflow position angles per source
- Which source is the tenth (not named)

## Analysis recipe

1. **Make polarization maps**: Form polarized intensity sqrt(Q^2+U^2), angle 0.5 arctan(U/Q), debias with mean Q/U noise, mask below 5 sigma, fraction = P/I  
  > "The polarization intensity maps were debiased using the average noise value determined from the Q and U maps. Each map was masked below 5$\sigma$." (2.2 Observations and Data Reduction)
   - software: CASA immath
   - parameter: 5 sigma mask  
  > "Each map was masked below 5$\sigma$." (2.2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes and mean polarization angle**: Gaussian fits with imfit; polarized-intensity-weighted mean angle within 115 au (0.5 arcsec) radius of polarized peak  
  > "The sum is taken within a circle of radius 115 au (= 0.5 arcsecond) centered at the peak of the polarized continuum." (3 Results)
   - software: CASA imfit
   - fitting: Elliptical Gaussian  
  > "Integrated and peak flux densities are estimated from elliptical Gaussian fits using the CASA task `imfit`." (3 Results)
   - validation: _not stated_
3. **Compare inner vs outer polarization fraction distributions**: Kaplan-Meier estimator including upper limits, sampled at ~half-beam spacing; inner (~100-150 au) vs outer; log-rank test  
  > "we sample the polarization fraction (or its upper limit) at spacings of $\sim 1/2$ beam-width (to ensure a degree of statistical independence)." (3 Results)
   - software: lifelines
   - fitting: _not stated_
   - validation: Checked detection threshold in outer regions; typical detection ~2x minimum threshold  
  > "the typical detection is at a level $\sim$ 2 times the minimum detection threshold." (3 Results)
4. **Test polarization offset from outflow axis**: KS and AD tests against uniform distribution on 0-90 deg; disk-candidates vs non-disk-candidates  
  > "We performed both the Kolmogorov-Smirnov (KS) and Anderson-Darling (AD) tests to compare the distribution of $\Delta \theta$ to that of a uniform distribution." (3 Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: Calibration, CLEAN imaging, immath, imfit  
  > "using the Common Astronomy Software Applications (CASA) package (cite: mc07), version 4.7.0" (2.2 Observations and Data Reduction)
- **lifelines** v0.11.1: Kaplan-Meier estimator  
  > "we used the `lifelines` Python package (cite: dp17)[^1] to compute the Kaplan-Meier product limit estimator" (3 Results)
- **Matplotlib** : Plotting  
  > "Matplotlib (http://dx.doi.org/10.1109/MCSE.2007.55)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Log-rank test p-value inner vs outer polarization fraction | ≲1e-4 | not stated | dimensionless | 3 | The p-value for the log-rank test between the two classes is $p \lesssim 10^{-4}$. |
| KS/AD p-value, disk-candidate offsets vs uniform | ~0.02-0.06 | not stated | dimensionless | 4 | We find suggestive evidence ($p \sim 0.02-0.06$) that the angular offset differs from a uniform random variable |
| KS/AD p-value, non-disk-candidates vs uniform | ≳0.3 | not stated | dimensionless | 4 | We find no evidence ($p\gtrsim 0.3$) that the offset distribution for the non-disk-candidate sources is different from a random uniform distribution. |

## Qualitative findings

- All sources polarized; 9/10 show extended polarized emission  
  > "all of our sources show some degree of polarization, with most (9/10) showing significantly extended emission in the polarized continuum" (abstract)

## Claim tuples

- H: Inner (disk-scale) and envelope-scale polarization fractions are intrinsically different | E: Kaplan-Meier CDFs with upper limits, log-rank test | R: Outer regions more likely to show polarization above a few %; p≲1e-4 | F: Different polarization mechanisms inner vs envelope | **supported**
- H: Disk-candidate polarization is consistent with dust scattering | E: Compare polarization angle to outflow axis/disk minor axis; KS and AD tests | R: Disk-candidate vectors roughly along minor axis; offsets differ from uniform (p~0.02-0.06) | F: Consistent with self-scattering, though toroidal-field alignment is not excluded | **partially**

## Reasoning

- Why this data: Previous polarization surveys had poor resolution (>2.5 arcsec), causing disk/envelope confusion  
  > "previous observations have not been able to disentangle them due to comparatively poor resolution" (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot definitively state the cause of the polarization hole  
  > "Though we cannot definitively state the cause of this hole, there are a few possibilities." (Discussion)
- Caveat (inferred, ours): Small sample (3 disk-candidates) limits the statistics
- Caveat (inferred, ours): Disk-candidate classification relies on an unpublished thesis
- Caveat (inferred, ours): Marginal p-values
- Caveat (inferred, ours): Scattering vs toroidal-field alignment not distinguished
- Caveat (inferred, ours): Single-band data cannot constrain grain sizes

## Reproducibility

- Data public (paper): ALMA project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01503.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters
- Missing: Outflow angles per source
- Missing: Noise levels
- Missing: Details of Kaplan-Meier sampling
- Data volume (inferred): ~10-30 GB raw single-execution Band 7 polarization dataset
- Score (inferred): 3/5, Data identified and the main steps described, but the imaging parameters and angle inputs are missing.
- Rediscovery candidate: no, Key imaging settings and outflow angles are not given, and the results are mostly qualitative or p-values.

## Links

- Method: (cite: dp17) (lifelines Kaplan-Meier)
- Companion: (cite: se16) (Disk-candidate 8 mm fitting)
- Companion: (cite: st17) (Outflow angles)
- Related: VANDAM
- Related: MASSES

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 37,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
