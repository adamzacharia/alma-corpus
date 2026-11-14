# Galaxies at redshifts 5 to 6 with systematically low dust content and high [C II] emission

`2015Natur.522..455C` | Nature 2015 | first author: Capak, P. L. | arXiv: 1503.07596 | DOI: 10.1038/nature14500

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do typical z~5-6 star-forming galaxies show lower dust content and enhanced [CII] relative to FIR compared with z<3 systems?  
  > "We find these galaxies have >12x less thermal emission compared with similar systems" (abstract)
- Target **HZ1-HZ10 (COSMOS LBGs at z~5-6), plus HZ5a and HZ8W**: coordinates RA/Dec per source in Extended Data Table 1 (e.g. HZ1 149.971869, 2.118175)  
  > "HZ1 149.971869 2.118175 5.690 LAE/I-LBG 5.6885±2e-4" (Extended Data Table 1); z/distance z=5.15-5.69 ([CII] redshifts)  
  > "HZ1 149.971869 2.118175 5.690 LAE/I-LBG 5.6885±2e-4" (Extended Data Table 1); distance from [CII] redshift, consistent with Keck/DEIMOS optical spectroscopy redshifts  
  > "HZ1 149.971869 2.118175 5.690 LAE/I-LBG 5.6885±2e-4" (Extended Data Table 1)

## Data provenance

- ALMA projects: 2012.1.00523.S
- bands: Band 7  
  > "These data were taken with an early 20antenna version of Atacama Large Millimeter Array (ALMA) in band 7" (main text)
- frequencies and spectral setup: four side bands; one centered on [CII] 158 um, other three for continuum  
  > "One of the four side bands was always centered on the 158μm [CII] line" (main text)
- continuum bandwidth: 7.5 GHz  
  > "continuum mode with 7.5GHz of bandwidth" (main text)
- arrays: early 20-antenna ALMA, compact configuration  
  > "an early 20antenna version of Atacama Large Millimeter Array (ALMA)" (main text)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.6 arcsec  
  > "the compact array yielding a resolution of ~0.6 arc seconds" (main text)
- max recoverable scale: larger than 5-7 arcsec (29-43 kpc) resolved out  
  > "The baseline configuration used will resolve out spatial scales larger than 5-7” (29-43 kpc)" (Method 2)
- sensitivity: _not stated_
- time on source: ~20 minutes  
  > "~20 minutes of integration" (main text)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Other facility **Keck-II DEIMOS**: spectroscopic absorption-line redshifts  
  > "have spectroscopically determined absorption line redshifts from the Deep Extragalactic Imaging Multi-Object Spectrograph (DEIMOS)" (main text)
- Other facility **HST ACS F814W**: UV morphologies/sizes  
  > "UV morphologies are measured from the Hubble-Space-Telescope (HST) Advanced Camera For Surveys (ACS) F814W" (main text)
- Other facility **Spitzer SPLASH**: 3-5 um photometry for stellar masses  
  > "new 3-5μm photometry from the Spitzer-SPLASH survey" (main text)
- External data: COSMOS photometric redshift catalog optical/NIR photometry  
  > "Optical and near infrared data were obtained from the COSMOS photometric redshift catalog" (Method 3) [from Ilbert et al. (cite: 32)]
- External data: HST-ACS weak lensing catalog sizes  
  > "Sizes were taken from the COSMOS Hubble Space Telescope Advanced Camera for Surveys (HST-ACS) weak lensing catalog" (Method 3) [from Leauthaud et al. (cite: 15)]
- External data: Grey body FIR SED parameter ranges from z~2-5 objects  
  > "total infrared (3-1100μm) luminosity was derived using the range of grey body models covering the full range of objects observed at z~2-5" (Method 4) [from Casey 2012 (cite: 18)]

## Processing

### Calibration

- pipeline or manual: ALMA staff initial calibration, then re-analysed with extra flagging  
  > "The ALMA observatory staff, as part of standard data processing and delivery, performed initial data calibration." (Method 2)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, Robust = 1  
  > "The data were re-imaged using the CASA Briggs flexible weighting of the u-v visibility data with Robust = 1" (Method 2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: [CII] line contribution subtracted from measured continuum fluxes  
  > "The [CII] line contribution was subtracted from the measured continuum fluxes." (Method 2)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dynamical mass estimator  
  > "We used the method outlined in Wang et al. [37] to estimate the dynamical masses." (Method 4) [from Wang et al. (cite: 37)]
- Stellar mass SED fitting  
  > "Stellar masses were derived using data from the Spitzer Large Area Survey with Hyper-Suprime-Cam (SPLASH) in the same way described in previous work" (Method 4) [from Ilbert et al. (cite: 32)]
- Completeness analysis  
  > "We also performed a completeness analysis following Casey et al. [38]" (Method 5) [from Casey et al. (cite: 38)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum imaging bandwidth used
- Image size, cell size, cleaning threshold, masks
- Flagging details and which channels/times were flagged
- Flux calibrator and ALMA flux scale uncertainty
- Channel width of cubes and moment-0 velocity range
- Fit box sizes for CASA Gaussian fits
- CASA version
- Stacking procedure details
- Details of the SED fitting (templates, extinction laws)

## Analysis recipe

1. **Re-reduce and image ALMA data**: Additional flagging, re-imaging with Briggs weighting to make continuum, moment zero and channel maps  
  > "The calibrated visibility data was then re-analyzed, performing additional flagging of bad time periods in the data and bad channels." (Method 2)
   - software: CASA
   - parameter: Robust = 1  
  > "with Robust = 1 to create continuum, moment zero, and channel maps" (Method 2)
   - fitting: _not stated_
   - validation: Independent blind check of data reduction by a coauthor  
  > "carried out an independent blind check of the ALMA data reduction" (Author Contributions)
2. **Fit [CII] lines and continuum, derive redshift, FWHM, flux, sizes**: Gaussian fitting of spectra and image components; centroid compared to [CII] rest frequency  
  > "Gaussian fitting of the spectral and spatial data was performed using the CASA viewer and CASA fit tool." (Method 2)
   - software: CASA viewer, CASA imfit
   - fitting: CASA Gaussian fitting, not constrained by beam size  
  > "The fits were not constrained by the beam size, and so they can be slightly smaller due to the data errors." (Method 2)
   - validation: [CII] redshifts identical within precision to optical spectroscopic redshifts  
  > "Since these measures were identical, within our precision" (Method 2)
3. **Derive infrared luminosity from the single 158um point**: Scale grey body models to observed rest-frame 158 um flux  
  > "The range of allowed infrared luminosities was determined by scaling these grey bodies to the observed rest frame 158μm flux." (Method 4)
   - parameter: alpha=1.5-2.5, beta=1.2-2.0, T=25-45 K  
  > "ranged between α=1.5-2.5, β=1.2-2.0 and T=25-45 K" (Method 4)
   - assumption: FIR SEDs follow z~2-5 grey body range  
  > "using the range of grey body models covering the full range of objects observed at z~2-5" (Method 4)
   - fitting: _not stated_
   - validation: Blind test of FIR luminosity by a coauthor  
  > "She also conducted a blind test of the FIR luminosity," (Author Contributions)
4. **Measure UV slope beta and UV luminosity**: Power-law fit to rest-frame 0.13-0.3 um photometry; alternate fit 0.15-0.3 um to estimate systematic  
  > "The rest frame ultraviolet properties were determined by fitting a powerlaw to the rest frame 0.13-0.3μm photometry" (Method 4)
   - fitting: _not stated_
   - validation: Additional ±0.3 systematic from simulations of blending and S/N  
  > "an additional ±0.3 systematic error should be included" (Method 4)
5. **Compare to IRX-beta relations and test robustness; stack non-detections**: Compare IRX vs beta with Meurer and SMC relations; predicted vs measured mean flux of undetected sources  
  > "If we assume a Meurer et al. like IRX-β relation and the mean of our grey body models" (Method 5)
   - assumption: Meurer relation typical of z<3; SMC-like dust model  
  > "The Meurer [28] relation, consistent with typical galaxies at z<3, is shown as a black solid line" (Figure 2)
   - fitting: _not stated_
   - validation: Extreme dust-temperature models tested; completeness analysis  
  > "find the low dust emission is unlikely due to selection effects in our UV sample" (Method 5)
6. **Estimate dynamical masses**: Mdyn = 1.16e5 Vcir^2 D with Vcir = 1.763 sigma/sin(i), i from axis ratio  
  > "V cir = 1.763 σ [CII] /sin(i), and i, the disk inclination angle is approximated by the axis ratio of the object" (Method 4)
   - parameter: sin(i)=0.45-1 assumed for errors  
  > "assumes sin(i)=0.45-1" (Method 4)
   - fitting: _not stated_
   - validation: Compared to stellar masses and z~1-3 Halpha dynamical masses  
  > "We find the dynamical masses are typically a factor of ~3 greater than the stellar masses" (Method 4)

## Software

- **CASA** : imaging, moment maps, Gaussian fitting  
  > "The data were re-imaged using the CASA Briggs flexible weighting" (Method 2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked mean continuum of 6 non-detections | 35 | 13 | uJy | 5 | yields a continuum detection of 35±13μJy |
| [CII] velocity dispersions | 63-163 | not stated | km/s | 2 | [CII] velocity dispersions of σ=63-163 km/s |
| Systematic uncertainty in LIR | 0.3 | not stated | dex | 3 | This range of parameters resulted in a systematic uncertainty of 0.3 dex in the derived luminosity. |
| HZ10 continuum flux | 1261 | 44 | uJy | 2 | HZ10 150.247098 1.555426 5.659 LAE/I-LBG 5.6566±2e-4 1261±44 1.57±0.09 127±8 |
| Effect on z~6 star formation density | 30-40% less | not stated | percent | 5 | result in ~30-40% less StarFormation at z~6 than previously thought |

## Qualitative findings

- All 9 targeted galaxies detected in [CII] at >3 sigma; only 4 of 9 in continuum  
  > "we find >3σ detections of the [CII] line in all 9 normal galaxies" (main text)

## Claim tuples

- H: z~5-6 galaxies are less dust obscured than z<3 systems | E: ALMA band 7 continuum and IRX-beta comparison | R: Continuum detected in 4 of 9; stack of the rest is 35±13 uJy, >12x below expectation | F: Galaxies are significantly less dust obscured, consistent with SMC-like or lower | **supported**
- H: [CII] is enhanced relative to FIR at z~5-6 | E: [CII]/FIR compared with lower-z samples | R: Clear excess of [CII] relative to FIR | F: Consistent with lower dust-to-gas ratio, like local low-metallicity systems | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Changes in dust properties and geometry considered less likely than a lower dust-to-gas ratio, but geometry cannot be fully excluded  
  > "we cannot fully exclude this possibility since it would explain the observed IRX properties" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Dynamical masses very uncertain due to low spatial resolution  
  > "This method yields an approximate answer but is very uncertain" (Method 4)
- Caveat (inferred, ours): Single FIR point makes LIR depend on assumed SED
- Caveat (inferred, ours): Short integrations and low resolution limit sizes and dynamics
- Caveat (inferred, ours): Mean-stacked non-detections depend on source positions and weighting

## Reproducibility

- Data public (paper): ALMA data cited as ADS/JAO.ALMA#2012.1.00523.S  
  > "This paper makes use of ALMA data: ADS/JAO.ALMA#2012.1.00523.S." (Author Information)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust=1
- Missing: CASA version
- Missing: Fit box sizes
- Missing: Stacking details
- Data volume (inferred): ~tens of GB
- Score (inferred): 3/5, Public data and numeric tables, but imaging and fit details are sparse.
- Rediscovery candidate: yes, Public data with numeric tables of fluxes, though processing details are incomplete.

## Links

- Method: Wang et al. (cite: 37) (dynamical mass method)
- Method: Casey 2012 (cite: 18) (FIR SED models)
- Related: COSMOS
- Related: SPLASH

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 46,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
