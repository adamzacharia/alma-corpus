# Azimuthal asymmetries in the debris disk around HD 61005. A massive collision of planetesimals?

`2016A&A...591A.108O` | Astronomy and Astrophysics 2016 | first author: Olofsson, J. | arXiv: 1601.07861 | DOI: 10.1051/0004-6361/201628196

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: What are the radial and azimuthal dust distributions of the HD 61005 debris disk from SPHERE, ALMA and SED modeling, and what explains its morphology?  
  > "Thanks to the new observations, we propose a solution for both the radial and azimuthal distribution of the dust grains in the debris disk." (abstract)
- Target **HD 61005**: coordinates _not stated_; z/distance 35.4±1.1 pc  
  > "located at a distance of $35.4\pm1.1$ pc ((cite: 2007))" (1 Introduction); distance from van Leeuwen 2007  
  > "located at a distance of $35.4\pm1.1$ pc ((cite: 2007))" (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00437.S
- bands: Band 6  
  > "HD 61005 was observed with ALMA in Band 6 (PI: David Rodriguez, program 2012.1.00437.S)" (2.2 ALMA observations)
- frequencies and spectral setup: three continuum SPWs (31250 kHz resolution), one SPW 230.05-230.99 GHz (488.28 kHz) for CO  
  > "the last one was used to search for CO gas emission ($230.05-230.99$ GHz, with a $488.28$ kHz resolution), which was not detected" (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 11.8 to 334.9 m  
  > "with minimum and maximum baselines of 11.8 and 334.9 m, respectively" (2.2 ALMA observations)
- angular resolution: 1.36" x 0.73" (48 au x 26 au), PA -86.5 deg  
  > "The beam size is $1.36^{\prime\prime} \times 0.73^{\prime\prime}$ (48 au$\times$26 au) with a position angle of $-86.5^{\circ}$." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 0.09 mJy/beam  
  > "(sensitivity of $0.09$ mJy/beam)" (2.2 ALMA observations)
- time on source: integration 120.96 s  
  > "2014-03-20       | 2012.1.00437.S | Continuum       | 31250.00      | $211.91-228.97$     | 0.79     | 120.96" (Table 1)
- observing dates: 2014-03-20  
  > "We only kept the observations performed on the 20 of March 2014 for which the water vapor was minimum." (2.2 ALMA observations)
- pi or archival as stated: PI David Rodriguez, program 2012.1.00437.S  
  > "HD 61005 was observed with ALMA in Band 6 (PI: David Rodriguez, program 2012.1.00437.S)" (2.2 ALMA observations)
- Line: CO 2-1 (~230.5 GHz)
- Other facility **VLT/SPHERE**: IRDIS ADI H and K, IRDIS DPI H-band images  
  > "The observations were obtained in different instrumental set-ups in February, March, and May 2015" (2.1)
- Other facility **Herschel PACS/SPIRE**: far-IR photometry for SED  
  > "The star HD 61005 was observed by *Herschel* ((cite: Pilbratt2010)) with the Photodetector Array Camera and Spectrometer instrument" (2.3 SED)
- Other facility **Spitzer/IRS**: mid-IR spectrum from CASSIS  
  > "we downloaded the *Spitzer*/IRS spectrum from the Cornell Atlas of Spitzer/IRS Sources database" (2.3 SED)
- External data: SMA 1.3 mm flux 7.2±0.3 mJy (compared)  
  > "(cite: Ricarte2013) obtained a total flux of $7.2\pm0.3$ mJy at $1.3$ mm with their SMA observations" (3.2 Results) [from Ricarte2013]
- External data: Heliocentric radial velocity 22.5 km/s  
  > "From the heliocentric radial velocity of $22.5$ km.s$^{-1}$ ((cite: Desidera2011))" (6.2 Gas mass upper limits) [from Desidera2011]
- External data: Teff = 5500 K  
  > "with an effective temperature of $T_{\star} = 5500$ K ((cite: Casagrande2011))" (2.4 Stellar parameters) [from Casagrande2011]

## Processing

### Calibration

- pipeline or manual: CASA standard scripts provided by the observatory  
  > "Data processing was performed within CASA using the standard scripts provided by the observatory." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, briggs weighting  
  > "The reconstructed image (with so-called briggs weighting and pixel size of $0.13^{\prime\prime}$)" (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.13"  
  > "The reconstructed image (with so-called briggs weighting and pixel size of $0.13^{\prime\prime}$)" (2.2 ALMA observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.36" x 0.73", PA -86.5 deg  
  > "The beam size is $1.36^{\prime\prime} \times 0.73^{\prime\prime}$ (48 au$\times$26 au) with a position angle of $-86.5^{\circ}$." (2.2 ALMA observations)
- final rms: 0.09 mJy/beam  
  > "(sensitivity of $0.09$ mJy/beam)" (2.2 ALMA observations)

### Inherited from earlier work

- Herschel data processing in HIPE as in earlier work  
  > "the very same way as described in (cite: Olofsson2013)" (2.3 SED) [from Olofsson2013]
- SED weighting of photometry vs IRS points  
  > "We therefore opt for a similar strategy to the one described in (cite: Ballering2013)." (5.1) [from Ballering2013]
- CO gas mass upper-limit procedure  
  > "we follow a similar procedure to that of (cite: Matra2015) and (cite: Moor2015b)" (6.2) [from Matra2015; Moor2015b]

### Not stated but needed to reproduce (our reading)

- briggs robust value, clean threshold and image size
- ALMA flux calibrator and flux scale uncertainty
- CASA version
- line-free handling/spectral window selection details beyond SPW choice
- number of channels/velocity binning for the CO spectrum
- DDiT code availability

## Analysis recipe

1. **Fit ALMA visibilities with a ring model**: Fourier-space fit of the model image to channel-averaged complex visibilities, with emcee MCMC  
  > "The modeling of the ALMA observations is performed in the Fourier space, attempting to reproduce both the real and imaginary parts of the complex visibilities" (3.1 Modeling strategy)
   - software: emcee, CASA
   - parameter: 200 walkers, 500 burn-in, 2000 iterations; alpha_in = 5 fixed  
  > "using $200$ walkers, a burn-in phase of $500$ iterations and a total length of the chains of $2000$ iterations after the burn-in phase" (3.1 Modeling strategy)
   - assumption: circular disk  
  > "We first model the ALMA data (Section [3](#sec:alma)) assuming a circular disk" (2.5)
   - fitting: emcee, uniform priors, chi2 with CASA weights  
  > "The goodness of fit is the sum of the weights (estimated in CASA) times the squared difference between the observed and modeled complex visibilities" (3.1 Modeling strategy)
   - validation: mean acceptance fraction 0.48, max autocorrelation time 60; best model imaged with CASA ft/clean and residuals inspected  
  > "we find that the mean acceptance fraction (the mean fraction of steps accepted for each walker within the chain) is of $0.48$" (3.1 Modeling strategy)
2. **Upper limit on CO gas mass**: LTE optically thin M_CO from rms-based integrated flux over 15 km/s at 20 K  
  > "Assuming optically thin gas, this leads to an upper limit of $6.9\times 10^{-7}$ M$_{\oplus}$." (6.2)
   - software: CASA
   - parameter: T = 20 K, width 15 km/s, v_LSR 3.68 km/s  
  > "we obtain a $v_{\mathrm{LSR}}$ of $3.68$ km.s$^{-1}$" (6.2)
   - assumption: LTE, optically thin  
  > "The fractional level was calculated assuming local thermal equilibrium" (6.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Combine with SPHERE/SED modeling and compare eccentric model to ALMA**: Eccentric and azimuthally damped models built from SPHERE fits were generated with ALMA best-fit parameters and compared with the ALMA data  
  > "we generated models including eccentricity and azimuthal variations." (6.4)
   - software: CASA
   - parameter: e=0.093, Phi_e=127, w=52, Phi_eta=138, eta=0.47 and 0.6  
  > "and two values for $\eta$ ($0.47$ and $0.6$)" (6.4)
   - fitting: _not stated_
   - validation: residuals compared to 2 sigma level  
  > "the residuals barely reach the $2\sigma$ level" (6.4)

## Software

- **CASA** : ALMA data processing, ft and clean of models, weights  
  > "Data processing was performed within CASA using the standard scripts provided by the observatory." (2.2 ALMA observations)
- **emcee** : MCMC fits of ALMA, SPHERE and SED  
  > "we use an affine invariant ensemble sampler Monte-Carlo Markov Chain, implemented in the `emcee` package" (3.1 Modeling strategy)
- **triangle** v0.1.1: posterior plots  
  > "(using the `triangle` Python package, (cite: ForemanMackey2014))" (3.2 Results)
- **scikit-learn** : PCA for ADI  
  > "using the implementation of the `scikit-learn` Python package" (2.1.1)
- **HIPE** build 12.0.2083: Herschel data processing  
  > "The data were processed using the HIPE software (build 12.0.2083" (2.3 SED)
- **PynPoint** : planet detection limits  
  > "preliminary tests using the `PynPoint` package ((cite: Amara2012))" (6.5)
- **DDiT** : disk SED and image model code  
  > "The DDiT code is mostly based on the code already described in (cite: Olofsson2012; Olofsson2013)." (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA r0 | 66.4 | +6.1/-8.7 | au | 1 | $r_0$ \[au\] / $[40, 80]$ / $0.2$ / $66.4_{-8.7}^{+6.1}$ |
| ALMA 1.3 mm flux | 4.6 | +0.7/-0.6 | mJy | 1 | $f_{1300}$ \[mJy\] / $[1, 20]$ / $0.1$ / $4.6_{-0.6}^{+0.7}$ |
| ALMA inclination | 84.5 | +2.9/-2.5 | deg | 1 | $i$ \[$^{\circ}$\] / $[79, 89]$ / $0.1$ / $84.5_{-2.5}^{+2.9}$ |
| ALMA position angle | 70.7 | +1.9/-2.3 | deg | 1 | $\phi$ \[$^{\circ}$\] / $[55, 85]$ / $0.1$ / $70.7_{-2.3}^{+1.9}$ |
| CO gas mass upper limit | 6.9e-7 | not stated | Earth masses | 2 | this leads to an upper limit of $6.9\times 10^{-7}$ M$_{\oplus}$ |
| SPHERE eccentricity | 0.093 | +0.018/-0.014 | dimensionless | 3 | $e$ / $[0, 0.6]$ / $0.0025$ / $0.093_{-0.014}^{+0.018}$ |
| SED dust mass | 0.37 | +0.04/-0.01 | Earth masses | 3 | $3.7_{-0.1}^{+0.4}$ |

## Qualitative findings

- Wings not detected in ALMA data; no CO detected; ALMA cannot confirm or rule out azimuthal asymmetry  
  > "The sensitivity of the ALMA observations cannot confirm nor rule out an asymmetric disk for large mm-sized dust grains." (Conclusion)

## Claim tuples

- H: The mm-grain parent belt is narrow and consistent with SPHERE geometry | E: Visibility fit of ALMA Band 6 continuum | R: r0 ~66 au, i ~84.5, flux 4.6 mJy; outer slope poorly constrained | F: Parent planetesimals form a narrow belt near 61 au | **supported**
- H: The ALMA data show the SPHERE azimuthal asymmetry | E: Compared eccentric/damped models with ALMA data | R: residuals below ~2 sigma for eta=0.47 and 0.6 | F: Cannot exclude asymmetry; eta ~0.5 excluded at 2 sigma only | **partially**
- H: Significant CO gas is present | E: CO 2-1 non-detection upper limit | R: M_CO < 6.9e-7 Mearth | F: Gas-to-dust ratio cannot be concluded | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimeter observations trace larger grains following the parent planetesimals, so modeled independently of SPHERE  
  > "the millimeter observations most likely trace a population of larger grains that more closely follow the parent planetesimals’ belt" (3)
- How they decided it was enough: _not stated_
- Limitation (authors): Large ALMA beam leaves outer slope poorly constrained; uncertainties should be treated carefully  
  > "We note that not all the distributions reach zero on each side of their maximum (especially for $\alpha_{\mathrm{out}}$ and $i$)" (3.2 Results)
- Caveat (inferred, ours): Only one ALMA execution used; discarded others without justification
- Caveat (inferred, ours): ALMA flux lower than SMA values, offered no firm explanation
- Caveat (inferred, ours): Flux calibration uncertainty not propagated

## Reproducibility

- Data public (paper): ALMA program cited in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2012.1.00437.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Briggs robust value, clean parameters
- Missing: CASA version
- Missing: DDiT code not released
- Data volume (inferred): ~5 GB (single ALMA Band 6 execution)
- Score (inferred): 3/5, ALMA data are archival and the model is described in detail, but imaging parameters are missing and the code is not released.
- Rediscovery candidate: no, ALMA part is minor and the custom DDiT code is not available; imaging details are missing.

## Links

- Method: Olofsson2012; Olofsson2013 (Origin of the DDiT disk/SED code)
- Companion: Ricarte2013 (SMA 1.3 mm observations of HD 61005)
- Related: SPHERE GTO

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 75,
  "stated": 47,
  "rate": 0.627
 },
 "evidence_ok": true
}
```
