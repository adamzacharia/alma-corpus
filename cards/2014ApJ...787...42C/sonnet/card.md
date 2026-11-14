# An ALMA Continuum Survey of Circumstellar Disks in the Upper Scorpius OB Association

`2014ApJ...787...42C` | The Astrophysical Journal 2014 | first author: Carpenter, John M. | arXiv: 1404.0387 | DOI: 10.1088/0004-637X/787/1/42

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How much dust do disks around K and M stars in Upper Sco (5-11 Myr) contain, how does it depend on stellar mass, and how does it compare with younger Taurus disks?  
  > "We use these data to investigate any dependence of the disk properties with stellar mass, and compare these observations with existing submillimeter continuum measurements of stars in the younger Taurus region to investigate the evolution of dust masses." (Introduction)
- Target **20 K and M-type disk-bearing stars in Upper Sco**: coordinates phase centers listed in Table 1 (e.g. 15:56:24.774 -22:25:55.26)  
  > "we adopt $d=145$ pc, which is the mean distance of the OB stars in the Upper Sco association (cite: deZeeuw99)" (3 ALMA Observations); z/distance 145 pc  
  > "we adopt $d=145$ pc, which is the mean distance of the OB stars in the Upper Sco association (cite: deZeeuw99)" (3 ALMA Observations); distance from mean distance of Upper Sco OB stars (de Zeeuw et al. 1999)  
  > "we adopt $d=145$ pc, which is the mean distance of the OB stars in the Upper Sco association (cite: deZeeuw99)" (3 ALMA Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (880 um, mean 340.7 GHz)  
  > "All observations were obtained in Band 7 with a full-width-at-half-maximum (FWHM) primary beam size of 18.5$''$." (3 ALMA Observations)
- frequencies and spectral setup: 4 spectral windows at 333.8, 335.7, 345.8, 347.7 GHz, 1.875 GHz bandwidth each, 0.488 MHz channels; one window on 12CO J=3-2  
  > "spectral windows centered on 333.8, 335.7, 345.8, and 347.7 GHz for a mean frequency of 340.7 GHz (880 $\mu$m)" (3 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, 17-25 per night  
  > "| 2012 Aug 24 | 25       | 17–375         | 0.77   | Neptune | J1924$-$292 | J1751$-$0939 | J1625$-$2527 |" (Table 3)
- configurations: _not stated_
- baselines: 12-402 m  
  > "| 2012 Dec 16 | 17       | 16–402         | 1.16   | Titan   | J1924$-$292 | …            | J1625$-$2527 |" (Table 3)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 1 sigma 0.19, 0.16, 0.52 mJy/beam for Aug 24, Aug 28, Dec 16  
  > "The 1$\sigma$ point source sensitivity near the phase center is typically 0.19, 0.16, and 0.52 mJy beam$^{-1}$" (3 ALMA Observations)
- time on source: _not stated_
- observing dates: 2012 Aug 24, Aug 28, Dec 16  
  > "The ALMA Early Science Cycle 0 observations were obtained on 2012 Aug 24 UT (7 sources), 2012 Aug 28 (6 sources), and 2012 Dec 16 (5 sources)." (3 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.79599 GHz)
- Other facility **2MASS and DENIS**: optical/near-IR photometry for extinction and luminosity  
  > "Observed optical and near-infrared photometry were drawn from the 2MASS (cite: Skrutskie06; Cutri03) and DENIS (cite: DENIS) photometric catalogs." (2 The Upper Sco Sample)
- External data: Taurus Class II submillimeter flux densities, extrapolated to 880 um  
  > "The submillimeter flux densities for this sample are presented in (cite: Andrews13)" (6.2 Relative dust masses) [from Andrews et al. 2013 (cite: Andrews13)]
- External data: Sample selection of 24 K/M stars with IR excess  
  > "identified with an infrared excess between 3.6 $\mu$m and 16 $\mu$m by (cite: Carpenter06)" (2 The Upper Sco Sample) [from Carpenter et al. 2006 (cite: Carpenter06)]
- External data: Taurus Class II membership list  
  > "The comparison sample in Taurus consists of Class II sources compiled by (cite: Luhman10)." (6.2 Relative dust masses) [from Luhman et al. 2010 (cite: Luhman10)]
- Simulation/model as data: Siess et al. 2000 pre-main-sequence tracks (Z=0.02, no overshoot) for stellar masses  
  > "using the (cite: Siess00) pre-main-sequence evolutionary tracks with a metallicity of Z=0.02 and no convective overshoot" (2 The Upper Sco Sample)

## Processing

### Calibration

- pipeline or manual: CASA scripts from C. Brogan, adapted for bandpass, flux, gain  
  > "We adapted the initial calibration scripts to perform bandpass, flux, and gain calibration using CASA 4.1." (3 ALMA Observations)
- casa version: CASA 4.1  
  > "We adapted the initial calibration scripts to perform bandpass, flux, and gain calibration using CASA 4.1." (3 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune or Titan, Butler-JPL-Horizons 2012 models  
  > "Flux calibration was established by observing either Neptune or Titan, and adopting the Butler-JPL-Horizon 2012 models." (3 ALMA Observations)
- flux scale uncertainty: 10% (1 sigma)  
  > "We adopt a 1$\sigma$ calibration uncertainty of 10%." (3 ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: CASA 4.1 imaging  
  > "Images were created from the calibrated visibilities using CASA 4.1 using a Briggs robust weighting parameter of 2." (3 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 2  
  > "Images were created from the calibrated visibilities using CASA 4.1 using a Briggs robust weighting parameter of 2." (3 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: all channels except those around 12CO J=3-2  
  > "A continuum map was produced by averaging all of the channels except those around the $^{12}$CO J=$3-2$ line." (3 ALMA Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.13-0.62 mJy/beam per source (Table 4)  
  > "RMS noise in an image created with robust=2 and measured in an annulus between 4$''$ and 5$''$ centered on the stellar position" (Table 4)

### Inherited from earlier work

- Dust mass formalism: isothermal optically thin, kappa=2.3 cm2/g at 230 GHz, beta=0.4, Tdust=25 K (L*/Lsun)^0.25  
  > "The dust temperature is estimated as $T_\mathrm{dust} = 25\,\mathrm{K} \times(L_*/L_\odot)^{0.25}$ (cite: Andrews13)." (5.1 Dust Masses) [from Andrews et al. 2013 (cite: Andrews13)]
- Effective temperature scale  
  > "the temperature scale described in (cite: Andrews13) and references therein was adopted." (2 The Upper Sco Sample) [from Andrews et al. 2013 (cite: Andrews13)]
- Initial CASA calibration scripts  
  > "The initial reduction scripts were kindly provided by Crystal Brogan (NRAO)" (3 ALMA Observations) [from C. Brogan (NRAO), private communication]

### Not stated but needed to reproduce (our reading)

- ALMA project code is not printed in the text (only SSB code in acknowledgments)
- Image size, cell size and clean threshold/mask
- Exact channels excluded around 12CO
- Precise handling of the 16% flux offset between nights
- Taurus stellar masses/fluxes tables (from Andrews13) needed for comparison
- ASURV test settings and Kelly (2007) priors

## Analysis recipe

1. **Derive stellar parameters**: Teff from spectral type, L* from J-band photometry and extinction, masses from Siess tracks marginalized over age  
  > "The stellar mass distribution was then inferred by marginalizing over the stellar ages." (2 The Upper Sco Sample)
   - parameter: distance 145 pc with 15% uncertainty  
  > "which is assumed to be 15% of the mean distance of 145 pc (cite: deZeeuw99)" (2 The Upper Sco Sample)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux densities**: uvmodelfit elliptical gaussian (6 params), point source if FWHM/error<2; aperture photometry (1.5") for the ring; upper limit = max(0,S)+3 rms  
  > "Flux densities were measured by fitting an elliptical gaussian to the visibility data using *uvmodelfit* in CASA." (4 ALMA Results)
   - software: CASA
   - fitting: uncertainties scaled to reduced chi-squared of unity  
  > "The uncertainty on the model parameters were scaled by the factor needed to produce a reduced chi-squared of unity." (4 ALMA Results)
   - validation: offsets of centroids compared with stellar positions  
  > "Within the 3$\sigma$ uncertainties, the centroid of the continuum emission is consistent with the stellar position" (4 ALMA Results)
3. **Compute dust masses**: optically thin isothermal formula from flux, distance, opacity, Planck function  
  > "Assuming the dust emission is isothermal and optically thin, the dust mass is given by" (5.1 Dust Masses)
   - parameter: kappa=2.3 cm2/g at 230 GHz, beta=0.4, d=145 pc  
  > "we adopt $\kappa_\nu$=2.3 cm$^2$ g$^{-1}$ at 230 GHz, and assume $\kappa_\nu$ scales with frequency as $\nu^\beta$, where $\beta=0.4$." (5.1 Dust Masses)
   - assumption: dust-to-gas ratio 0.01  
  > "assuming a dust-to-gas ratio of 0.01 by mass" (5.2 Dust Mass vs. Stellar Mass in Upper Sco)
   - fitting: _not stated_
   - validation: _not stated_
4. **Mdust-M* relation in Upper Sco**: censored-data correlation tests (ASURV) and Bayesian linear regression with upper limits (Kelly 2007)  
  > "the slope of the power-law was derived using the Bayesian method described in (cite: Kelly07)" (5.2 Dust Mass vs. Stellar Mass in Upper Sco)
   - software: ASURV
   - fitting: Kelly (2007) Bayesian method with measurement errors, upper limits, intrinsic scatter  
  > "takes into account the measurement uncertainties, upper limits, and intrinsic scatter in the relationship" (5.2 Dust Mass vs. Stellar Mass in Upper Sco)
   - validation: compared with Taurus slope and dispersion from Andrews13  
  > "The slope and spread for Upper Sco are consistent with that for disks in Taurus" (5.2 Dust Mass vs. Stellar Mass in Upper Sco)
5. **Compare Upper Sco with Taurus**: Kaplan-Meier means and ASURV two-sample tests in two stellar-mass bins (0.097-0.26 and 0.49-1.6 Msun); Taurus fluxes scaled to 880 um with nu^2.4  
  > "We used the two-sample tests in the ASURV package to compare the Upper Sco and Taurus samples." (6.2 Relative dust masses)
   - software: ASURV
   - assumption: Taurus flux extrapolated with nu^2.4  
  > "by assuming the dust emission varies with frequency as $\nu^{2.4}$" (6.2 Relative dust masses)
   - fitting: _not stated_
   - validation: stellar mass distributions tested to be consistent between samples  
  > "Thus there is no evidence for differences in the stellar mass distribution of Class II sources Taurus and Upper Sco for the two stellar mass ranges." (6.2 Relative dust masses)

## Software

- **CASA** 4.1: calibration, imaging, uvmodelfit  
  > "The ALMA data were calibrated using the CASA package." (3 ALMA Observations)
- **uvmodelfit** : fitting flux densities to visibilities  
  > "Flux densities were measured by fitting an elliptical gaussian to the visibility data using *uvmodelfit* in CASA." (4 ALMA Results)
- **ASURV** : censored-data correlation and two-sample tests  
  > "as implemented in the ASURV software package (cite: Lavalley92)" (5.2 Dust Mass vs. Stellar Mass in Upper Sco)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of detections (>=3 sigma) | 13 of 20 | not stated | sources | 2 | Thirteen sources were detected in the 880 $\mu$m continuum with a signal-to-noise ratio of 3 or greater. |
| Dust mass range of detections | 0.3-52 | not stated | Earth masses | 3 | inferred dust masses between 0.3 and 52 M$_\oplus$ |
| Mdust-M* intercept | 0.68 | 0.30 | log Mearth | 4 | (0.68\pm0.30) +
(1.01\pm0.60)\, \mathrm{log} (M_*/\mathrm{M_\odot})$ |
| Mdust-M* slope | 1.01 | 0.60 | dimensionless | 4 | (0.68\pm0.30) +
(1.01\pm0.60)\, \mathrm{log} (M_*/\mathrm{M_\odot})$ |
| Scatter in relation | 0.76 | 0.24 | dex | 4 | with a spread of $0.76\pm0.24$ dex |
| Delta log Mdust (Taurus to Upper Sco), 0.49-1.6 Msun | 0.44 | 0.26 | dex | 5 | $\Delta\mathrm{log\,M_{dust}} = 0.44\pm0.26$ |
| Mean log Mdust Upper Sco, high-mass bin | 0.57 | 0.25 | log Mearth | 5 | $<\mathrm{log (M_{dust}/M_\oplus)}> = 0.57 \pm 0.25$ for Upper Sco |

## Qualitative findings

- Four brightest disks (>40 mJy) are resolved; J160421.7-213028 shows a ring  
  > "The dust emission around J160421.7-213028 is resolved into a ring" (4 ALMA Results)

## Claim tuples

- H: Dust mass depends on stellar mass in Upper Sco | E: ASURV correlation tests and Kelly regression | R: p of no correlation 0.017-0.044; slope 1.01±0.60 | F: marginal evidence dust mass rises with stellar mass | **partially**
- H: Dust masses are lower in Upper Sco than Taurus | E: Kaplan-Meier and ASURV two-sample tests | R: Delta log Mdust=0.44±0.26; probabilities 0.03-0.21 (high mass), 0.064-0.086 (low mass) | F: lower on average but not significant at 3 sigma | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: simplified dust-mass approach usable for all sources including Taurus ones lacking interferometry  
  > "Therefore, we adopt a simplified approach to estimating dust masses that can be applied to all sources" (5.1 Dust Masses)
- Alternative: Grain growth (max size 1 mm to 1 cm) could explain the flux decrease without a mass change  
  > "Thus we cannot exclude the possibility that the size distribution of particles is changing between Upper Sco and Taurus but the overall mass of solids has remained the same." (7 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass errors exclude opacity uncertainty; upper limits treated inconsistently between samples; multiplicity unknown for most stars  
  > "The dust mass uncertainties do not include errors in the assumed dust opacity." (5.1 Dust Masses)
- Caveat (inferred, ours): Small sample and many upper limits give poor statistics
- Caveat (inferred, ours): Taurus comparison relies on heterogeneous literature fluxes
- Caveat (inferred, ours): Assumed single dust temperature law and opacity drive absolute masses

## Reproducibility

- Data public (paper): ALMA Cycle 0 data acknowledged with ADS/JAO.ALMA#2011.0.00966.SSB  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00966.SSB." (Acknowledgments)
- Products in archive: _not stated_
- Missing: image/cell size and clean parameters
- Missing: Taurus data tables in the cited paper
- Missing: calibration scripts
- Data volume (inferred): ~10-50 GB (3 Cycle 0 datasets, 18 fields)
- Score (inferred): 4/5, Simple, well-described analysis with public Cycle 0 data; some imaging details and external Taurus data needed.
- Rediscovery candidate: yes, Data are archival, flux measurement and dust-mass recipe are clear, results are numeric.

## Links

- Method: Andrews et al. 2013 (cite: Andrews13) (dust-mass formalism and Taurus data)
- Method: Kelly 2007 (cite: Kelly07) (Bayesian regression with censored data)
- Companion: Zhang et al. 2014, in preparation (detailed analysis of J160421.7-213028)
- Related: Mathews et al. 2012 SMA Upper Sco survey
- Related: Spitzer survey of Carpenter et al. 2006

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00526.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00966.SSB"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 48,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
