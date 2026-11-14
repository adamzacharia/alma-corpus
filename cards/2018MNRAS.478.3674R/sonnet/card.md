# ALMA survey of circumstellar discs in the young stellar cluster IC 348

`2018MNRAS.478.3674R` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Ruíz-Rodríguez, D. | arXiv: 1805.07590 | DOI: 10.1093/mnras/sty1351

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How do the mm-continuum disk masses of Class II sources in IC 348 compare with those in younger and older regions, accounting for stellar mass?  
  > "We compare the disk mass distribution in IC 348 to those of younger and older regions, taking into account the dependence on stellar mass." (abstract)
- Target **IC 348 Class II sources (136)**: coordinates Individual positions in Table 1; field centered at R.A. 03h44m20.52s, Dec. +32d10m34.87s  
  > "We observed 136 Class II sources (disks that are optically thick in the infrared) at 0.8$''$ (200 au) resolution" (abstract); "We adopt a uniform distance of 310 $\pm$ 20 pc to all targets based on the ${\it Gaia}$ DR2 parallax measurements" (4.2 Target Properties); z/distance 310 ± 20 pc  
  > "We observed 136 Class II sources (disks that are optically thick in the infrared) at 0.8$''$ (200 au) resolution" (abstract); "We adopt a uniform distance of 310 $\pm$ 20 pc to all targets based on the ${\it Gaia}$ DR2 parallax measurements" (4.2 Target Properties); distance from Gaia DR2 parallaxes (Luri2018) of 35 targets  
  > "We observed 136 Class II sources (disks that are optically thick in the infrared) at 0.8$''$ (200 au) resolution" (abstract); "We adopt a uniform distance of 310 $\pm$ 20 pc to all targets based on the ${\it Gaia}$ DR2 parallax measurements" (4.2 Target Properties)

## Data provenance

- ALMA projects: 2015.1.01037.S
- bands: Band 6 (211-275 GHz), 1.3 mm  
  > "ALMA observations toward our IC 348 targets were carried out in Band 6 (211-275 GHz)" (3 ALMA Observations and Data Reduction)
- frequencies and spectral setup: Two continuum SPWs of 1.875 GHz at 218.0 and 233.0 GHz (mean 225.676 GHz); CO lines at 0.3 km/s resolution, 117.2 MHz bandwidth  
  > "The adopted setup included two spectral windows for continuum observations with effective bandwidths of 1.875 GHz centered at 218.0 and 233.0 GHz, for a mean frequency of 225.676 GHz" (3 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4  
  > "Our science goal was executed in Cycle 3 with the C40-4 array configuration" (3 ALMA Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: ~0.8 arcsec (200 au)  
  > "To reach the requested synthesized beam size of $\sim$0.8 arcsec" (3 ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 1σ ~0.15 mJy/beam; 3σ ~0.45 mJy  
  > "The typical (1$\sigma$) noise level reached is $\sim$0.15 mJy/beam." (3 ALMA Observations and Data Reduction)
- time on source: ~1 min per target over 3 execution blocks  
  > "with a total on-source integration time of $\sim$1 min per target over 3 execution blocks" (3 ALMA Observations and Data Reduction)
- observing dates: 23-27 June 2015  
  > "was observed between the 23rd and 27th June, 2015" (3 ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.535 GHz)
- Line: 13CO J=2-1 (220.395 GHz)
- Line: C18O J=2-1 (219.557 GHz)
- Other facility **Spitzer/IRAC, 2MASS, Pan-STARRS1, Gaia DR2**: Photometry for SEDs, extinctions, luminosities, and parallax distances  
  > "Considering that the most recent data releases of the ${\it Gaia}$ DR2 and Pan-STARRS-1 (PS1) are available, we seek for uniformity in these estimations." (4.2 Target Properties)
- External data: Target sample and Spitzer IRAC SED-slope classifications  
  > "Our sample was selected specifically from the work of (cite: Lada2006), whose sample was based on (cite: Luhman2003), and from (cite: Muench2007)" (2 Target selection) [from (cite: Lada2006); (cite: Muench2007)]
- External data: Comparison disk samples for Taurus, Lupus, Cha I, sigma Ori, Upper Sco  
  > "Upper limit inputs for the "comparison" samples are as reported in the literature" (5.2 Disk Evolution) [from (cite: Andrews2013; Ansdell2016; Ansdell2017; Barenfeld2016; Pascucci2016)]
- External data: Spectral types of targets  
  > "We derived the stellar properties based on the spectral types taken from (cite: Luhman2003) and (cite: Muench2007)" (4.2 Target Properties) [from (cite: Luhman2003); (cite: Muench2007)]
- Simulation/model as data: Baraffe2015 and PARSEC evolutionary tracks used for stellar masses and ages; BT-Settl spectra for SED photospheres  
  > "Masses and ages of targets with stellar masses between 0.01 and 1.4 $M_{\odot}$ were derived from models presented in (cite: Baraffe2015)" (4.2 Target Properties)

## Processing

### Calibration

- pipeline or manual: Initial calibration by ALMA science operations team during QA  
  > "Initial calibration (i.e. water vapor radiometer corrections, phase and amplitude calibrations) was performed by the ALMA science operations team during quality assurance." (3 ALMA Observations and Data Reduction)
- casa version: CASA 4.5.3  
  > "version 4.5.3 (cite: McMullin2007)" (3 ALMA Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0237+2848 (bandpass J0238+1636, J0336+3218; phase J0510+1800)  
  > "The flux calibrator was J0237+2848." (3 ALMA Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN on calibrated visibilities  
  > "we applied the CLEAN algorithm to the calibrated visibilities" (3 ALMA Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = +2  
  > "extracted the continuum images by applying a Briggs weighting with a robust parameter of +2, which is close to a natural weighting" (3 ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "Using the *uvcontsub* routine, we subtracted the continuum emission from the spectral windows" (3 ALMA Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Outflow mass/kinematics method for IRAS 03410+3152  
  > "following the process presented in (cite: RuizRodriguez2017)" (5.4 CO Emission From IRAS 03410+3152) [from (cite: RuizRodriguez2017)]
- Statistical spectral-type-based comparison methodology  
  > "here we used the statistical methodology presented in (cite: Andrews2013) based on spectral types." (5.2 Disk Evolution) [from (cite: Andrews2013)]
- Dust opacity 2.3 cm2/g at 1.33 mm  
  > "$\kappa_{\nu}$ = 2.3 $\rm cm^{2} g^{-1}$ at 1.33 mm; (cite: Andrews2005)" (4.1 Detection Criteria) [from (cite: Andrews2005)]

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, threshold, masks, cell and image size
- Line-free channels and continuum subtraction fit order
- Stacking procedure details (weighting, uv vs image plane)
- Flux scale uncertainty
- Bayesian linear regression priors and sampler settings (Kelly 2007 code used?)
- How stellar-mass-bin matching in Monte Carlo used spectral types for comparison samples
- Details of SED fitting and its output
- CASA pipeline version

## Analysis recipe

1. **Image continuum and measure fluxes**: Peak flux and rms with imstat; uvmodelfit point source (non-detections) or elliptical Gaussian (detections); detection S/N>4  
  > "A source with S/N $<$ 4 is considered a non-detection." (4.1 Detection Criteria)
   - software: CASA
   - parameter: Peak from 4" radius circle, rms from 4-7" annulus  
  > "Peak fluxes were derived from a 4$^{''}$ radius circle, and the rms from a 4-7$^{''}$ radius annulus centered on the expected source position." (4.1 Detection Criteria)
   - fitting: _not stated_
   - validation: Visual inspection of image plane for >4σ pixels to avoid contamination  
  > "we visually inspected the image plane for pixels with significant brightness ($>$4$\sigma$)" (4.1 Detection Criteria)
2. **Derive dust masses**: M_dust = F d^2 / (kappa B(T_dust))  
  > "we estimate disk masses for all detected targets and report them in Table" (4.1 Detection Criteria)
   - assumption: d=310 pc, T_dust=20 K, kappa=2.3 cm2/g at 1.33 mm, gas-to-dust 100  
  > "adopting a distance of 310 pc (Section [4.2](#sec:stellarparameter)) and making standard assumptions concerning the disc temperature (T$_{dust}$ = 20K)" (4.1 Detection Criteria)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stacking of non-detections**: Stack 96 non-detections centered on stellar positions  
  > "we stacked the 96 non-detections, after centering each field on the expected stellar position, to create an average image" (5.1 Non-Detections)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare luminosity distributions across regions**: 10^6 Monte Carlo draws by spectral-type bin, CDFs, censored Peto-Prentice tests; comparison samples scaled to 310 pc and 1.3 mm with F∝λ^-2.5  
  > "we simulate 10$^{6}$ synthetic "reference" disk ensembles that are used to construct Cumulative Distribution Functions (CDF)" (5.2 Disk Evolution)
   - assumption: Spectral type as proxy for stellar mass  
  > "This supports the use of spectral types as a proxy for stellar mass in the mass range of the stars in our IC 348 sample." (5.2 Disk Evolution)
   - fitting: _not stated_
   - validation: _not stated_
5. **Mdust-Mstar regression**: Bayesian linear regression handling upper limits (Kelly 2007)  
  > "This method accounts for measurement errors in linear regression for detected and undetected sources" (5.3 Disk mass vs. Stellar mass)
   - fitting: _not stated_
   - validation: Authors say fit is not accurate enough for meaningful comparison  
  > "a linear regression fit is not accurate enough to allow a meaningful comparison to other star-forming regions" (5.3 Disk mass vs. Stellar mass)
6. **Outflow properties of IRAS 03410+3152**: 12CO/13CO ratio parabola optical-depth correction; integrate blue/red channels above 4σ outside 3" mask  
  > "we apply the correction factor to all the channels with $^{13}$CO detection above 4$\sigma$" (5.4 CO Emission From IRAS 03410+3152)
   - assumption: Temperatures 20 and 50 K; no inclination correction  
  > "shows the estimates at temperatures of 20 and 50 K and without correcting for inclination effects" (5.4 CO Emission From IRAS 03410+3152)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Data reduction, CLEAN, uvcontsub, imstat, uvmodelfit  
  > "The ALMA data were reduced using the Common Astronomy Software Application (CASA) package, version 4.5.3" (3 ALMA Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of continuum detections | 40 of 136 | not stated | sources | 1 | we detect 40 out of the 136 IC 348 targets at $>$ 4$~\sigma$ significance |
| Stacked flux of non-detections | 0.14 | 0.02 | mJy | 3 | we find a clear signal of 0.14 $\pm$ 0.02 mJy |
| Typical dust mass of non-detections | ~0.40 | not stated | Earth masses | 3 | the average dust mass of the disks that were not individually detected is only $\sim$0.40 M$_{\oplus}$ |
| Linear regression slope (IC 348) | 0.90 | 0.21 | dimensionless | 5 | $\beta =$ 0.90 $\pm$ 0.21 and $\alpha =$ 0.37 $\pm$ 0.18 |
| Intrinsic scatter (IC 348) | 0.81 | 0.15 | dex | 5 | The fitted linear regression for IC 348 provides a large intrinsic scatter of $\delta =$ 0.81 $\pm$ 0.15. |
| Outflow kinematic age of IRAS 03410+3152 | 1800 | not stated | yr | 6 | we estimated a kinematic age of 1800 yr |
| Median p (IC 348 vs Taurus) | 2.3e-12 | not stated | dimensionless | 4 | medians of $p_{\phi}=$ 2.3 x 10$^{-12}$ and 5.5 x 10$^{-9}$ for Taurus and Upper Sco |

## Qualitative findings

- Disk masses in IC 348 are lower than Taurus and Lupus, similar to Cha I and sigma Ori, higher than Upper Sco  
  > "The disk masses in IC 348 are significantly lower than those in Taurus (1-3 Myr) and Lupus (1-3 Myr)" (abstract)

## Claim tuples

- H: Disk dust masses evolve with age between 1 and 10 Myr | E: Monte Carlo spectral-type-matched censored comparison of IC 348 with other regions | R: IC 348 fainter than Taurus/Lupus, similar to Cha I/sigma Ori, brighter than Upper Sco | F: Clear evolution of disk masses from 1 to 5-10 Myr | **supported**
- H: Undetected disks hold little dust | E: Stack 96 non-detections | R: 0.14 ± 0.02 mJy | F: Typical dust mass ≲0.4 Earth masses | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low detection fraction makes the Mdust-Mstar linear regression unreliable  
  > "the detection fraction is low ($\sim$30 $\%$) and is a strong function of stellar mass" (5.3 Disk mass vs. Stellar mass)
- Limitation (authors): Results depend on adopted distance and spectral types; membership not vetted  
  > "the foregoing comparisons of disc luminosity functions are highly dependent on the adopted distance and spectral types" (5.2.3 Distance Uncertainty)
- Caveat (inferred, ours): Single 310 pc distance despite a wide dispersion
- Caveat (inferred, ours): Constant 20 K dust temperature regardless of stellar luminosity
- Caveat (inferred, ours): Spectral type as mass proxy
- Caveat (inferred, ours): Short ~1 min integrations limit sensitivity for late M types

## Reproducibility

- Data public (paper): Project code given and ALMA data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA No. 2015.1.01037.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust=2
- Missing: Stacking details
- Missing: Monte Carlo and regression code settings
- Data volume (inferred): ~50-100 GB raw (3 EBs, 136 fields)
- Score (inferred): 3/5, Data are identifiable and the main steps are given, but imaging and stacking details are sparse.
- Rediscovery candidate: yes, Data are likely public, the recipe is mostly stated, and the main results are numeric (detections, stacked flux, dust masses).

## Links

- Method: (cite: Andrews2013) (Statistical methodology comparing luminosity distributions by spectral type)
- Method: (cite: Kelly2007) (Bayesian linear regression with upper limits)
- Companion: (cite: Cieza2015) (Earlier SCUBA-2 survey of IC 348)
- Companion: (cite: RuizRodriguez2017) (Outflow analysis method)
- Related: Lupus ALMA survey
- Related: Cha I
- Related: sigma Ori
- Related: Upper Sco
- Related: Taurus SMA survey

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 42,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
