# H<SUB>2</SUB>CO Ortho-to-para Ratio in the Protoplanetary Disk HD 163296

`2018ApJ...864..170G` | The Astrophysical Journal 2018 | first author: Guzmán, V. V. | arXiv: 1809.01705 | DOI: 10.3847/1538-4357/aad778

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the disk-averaged H2CO ortho-to-para ratio in the HD 163296 disk, and what does it say about H2CO formation (gas-phase vs grain surface)?  
  > "We present the first measurement of the $\mathrm{H_2CO}$ o/p ratio in a protoplanetary disk" (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc adopted (Gaia: 101.5±1.2 pc)  
  > "it is located $101.5\pm1.2$ pc away (cite: gaia2018). For consistency with previous analysis, we use the old distance of 122 pc (cite: vandenAncker1998) throughout the paper." (Introduction); distance from van den Ancker et al. 1998 (adopted); Gaia 2018  
  > "it is located $101.5\pm1.2$ pc away (cite: gaia2018). For consistency with previous analysis, we use the old distance of 122 pc (cite: vandenAncker1998) throughout the paper." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00681.S
- bands: ALMA Band 7  
  > "The Band 7 observations have baselines lengths spanning between 27 and 650 m, and a total on-source time of 45.5 min." (2.1 ALMA)
- frequencies and spectral setup: ALMA: four spectral windows; H2CO window 58 MHz bandwidth, 15 kHz channels  
  > "The $\mathrm{H_2CO}$ line was covered with a spectral window of 58 MHz bandwidth and 15 kHz channel width." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: ALMA 32 antennas; SMA 7 antennas sub-compact  
  > "observed in March 2014 with 7 antennas in the sub-compact (SUB) array configuration" (2.2 SMA)
- configurations: _not stated_
- baselines: 27-650 m (ALMA)  
  > "The Band 7 observations have baselines lengths spanning between 27 and 650 m" (2.1 ALMA)
- angular resolution: ALMA beam 1.00x0.90 arcsec; SMA beams ~2-8 arcsec  
  > "$1.00\times 0.90$ | -72.80 | 7.22 | 15.90" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 45.5 min (ALMA)  
  > "a total on-source time of 45.5 min" (2.1 ALMA)
- observing dates: ALMA May 2014 (Cycle 1); SMA March 2014  
  > "We observed the $\mathrm{H_2CO}$ $4_{04}-3_{03}$ line at 290.623 GHz with ALMA in May 2014 during Cycle 1" (2.1 ALMA)
- pi or archival as stated: ALMA project PI C. Qi  
  > "(project ADS/JAO.ALMA#2012.1.00681; PI: C. Qi.)" (2.1 ALMA)
- Line: p-H2CO 3_03-2_02 (218.222 GHz)
- Line: o-H2CO 3_13-2_12 (225.698 GHz)
- Line: o-H2CO 4_14-3_13 (281.527 GHz)
- Line: p-H2CO 4_04-3_03 (290.623 GHz)
- Line: o-H2CO 4_13-3_12 (300.837 GHz)
- Other facility **SMA**: Five H2CO lines (3 ortho, 2 para) giving disk-integrated fluxes; two lines from Qi et al. 2013  
  > "We observed five $\mathrm{H_2CO}$ lines with the SMA." (2.2 SMA)
- External data: Disk physical structure (gas density and temperature) of HD 163296  
  > "we use the disk physical structure of (cite: qi2011), that was constrained by fitting the spectral energy distribution, the millimeter dust continuum, and multiple CO and CO isotopologue lines." (4 Line modeling) [from (cite: qi2011)]
- External data: Disk inclination 48.5 deg and position angle 132 deg  
  > "is inclined by $48.5\ensuremath{^\circ}$ (as measured by CO and dust continuum emission), and the position angle (defined from North to West) is 132$\ensuremath{^\circ}$ (cite: isella2007)" (Introduction) [from (cite: isella2007)]
- External data: H2CO inner-disk radii R1 and R2 from chemical models of this disk  
  > "The values for $R_1$ and $R_2$ are chosen based on predictions from chemical models of this disk (Cleeves et al., private communication)." (4.1) [from Cleeves et al., private communication]
- External data: SMA 225.698 and 281.527 GHz o-H2CO data  
  > "which have been presented in (cite: qi2013)" (2.2 SMA) [from (cite: qi2013)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA staff calibration; SMA calibrated with MIR  
  > "We used the standard calibration performed by the ALMA staff, and further self-calibrated the data in phase and amplitude" (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: SMA: Titan and Mars  
  > "Titan and Mars were used as flux calibrators." (2.2 SMA)
- flux scale uncertainty: 10-20%  
  > "absolute flux calibration uncertainites of 10-20%" (4.2)
- self calibration: Phase and amplitude self-calibration of ALMA data  
  > "further self-calibrated the data in phase and amplitude to improve the signal-to-noise ratio" (2.1 ALMA)

### Imaging

- task: CLEAN in CASA 4.7  
  > "The continuum subtracted visibilities were cleaned in `CASA` 4.7, using the `CLEAN` algorithm with Briggs weighting of 2." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 2  
  > "Briggs weighting of 2" (2.1 ALMA)
- uv taper: Gaussian taper of 1 arcsec (ALMA)  
  > "We applied a Gaussian taper of $1''$ to improve the signal-to-noise." (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: ALMA: per-channel mask following Keplerian rotation; SMA: circular masks per line  
  > "we created a mask to help the cleaning process, by selecting regions in each channel with line emission that is consistent with the expected Keplerian rotation of the disk." (2.1 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Regridded to 0.6 km/s channels  
  > "The data were regridded to a spectral resolution of 0.6$\mathrm{\,km\,s^{-1}}$." (2.1 ALMA)
- final beam: 1.00x0.90 arcsec, PA -72.8 deg (ALMA)  
  > "$1.00\times 0.90$ | -72.80" (Table 1)
- final rms: ALMA channel rms 7.22 mJy/beam  
  > "7.22 | 15.90" (Table 1)

### Inherited from earlier work

- Detailed ALMA observation description  
  > "A detailed description of the observations and the results of the N$_2$H$^+$ $J=3-2$ and DCO$^+$ $J=4-3$ lines are given in (cite: qi2015)." (2.1 ALMA) [from (cite: qi2015)]
- SMA description of 281 and 225 GHz observations  
  > "A detailed description of the observations can be found in (cite: qi2013)." (2.2 SMA) [from (cite: qi2013)]
- Disk physical structure  
  > "we use the disk physical structure of (cite: qi2011)" (4 Line modeling) [from (cite: qi2011)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction details
- Self-calibration solution intervals and reference
- Cleaning threshold, image size and cell size
- MCMC priors, walkers and steps
- Source coordinates
- Gas-to-dust ratio, collisional rates and line broadening used in RADMC-3D
- SMA calibration flux values and MIR steps
- Dust/gas structure parameters from Qi et al. 2011 in detail

## Analysis recipe

1. **Image ALMA and SMA lines**: Calibrate (ALMA standard + self-cal; SMA with MIR), then clean in CASA with 0.6 km/s channels and masks  
  > "The calibrated data were then exported to `CASA` and cleaned in the same way as the ALMA line." (2.2 SMA)
   - software: CASA, MIR
   - parameter: Briggs robust 2; 1 arcsec taper for ALMA  
  > "Briggs weighting of 2" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure disk-integrated fluxes and rotational temperature**: Circular 6 arcsec mask fluxes; rotational diagram of three ortho lines  
  > "Using the three ortho lines we constructed a rotational diagram" (3.2)
   - parameter: Flux error: std of 500 simulated flux measurements at random signal-free positions  
  > "The uncertainty in the flux was estimated by taking the standard deviation of 500 simulated flux measurements from regions free of signal" (3.2)
   - assumption: Emission thermalized (LTE) given densities >1e6 cm-3  
  > "we expect the bulk of the emission to be thermalized" (3.2)
   - fitting: _not stated_
   - validation: Compared with 24 K from Carney et al. 2017  
  > "This temperature is consistent with the temperature of 24 K derived by (cite: carney2017)" (3.2)
3. **Fit H2CO abundance structure to ALMA visibilities**: Two-component parametric abundance (X1, X2, alpha free), RADMC-3D LTE models, vis-sample, MCMC, for three (z/r)_l  
  > "We use a Bayesian approach to find the best fit of the model to the ALMA visibilities." (4.1)
   - software: RADMC-3D, vis-sample, emcee
   - parameter: Fixed R1=1 au, R2=80 au, Rout=600 au, (z/r)_u=0.5; (z/r)_l=0.15, 0.20, 0.25  
  > "$R_1$ | 1 au" (Table 3)
   - assumption: LTE; uniform o/p of 3 for total abundance  
  > "are computed assuming a uniform o/p ratio of 3" (4.1)
   - fitting: emcee MCMC; likelihood from weighted real and imaginary visibility differences  
  > "We then compute the weighted difference between model and observations, for the real and imaginary parts of the complex visibility, which gives the likelihood of the model." (4.1)
   - validation: Channel maps of data, model and residuals; third-component test  
  > "Fig. [5] shows channel maps of the $\mathrm{H_2CO}$ line observed with ALMA (top row), together with the best fit model (middle row), and the residuals (bottom row)." (4.1)
4. **Fit o/p ratio to SMA data**: Fix abundance structure, fit uniform o/p and flux scale factor to five SMA lines  
  > "we keep the $\mathrm{H_2CO}$ abundance structure fixed, and vary only the o/p ratio." (4.2)
   - software: RADMC-3D, vis-sample, emcee
   - parameter: Free: o/p and scale  
  > "we introduce a *scale* factor for the total $\mathrm{H_2CO}$ abundance in the disk" (4.2)
   - assumption: Uniform o/p across disk  
  > "We assume a uniform o/p ratio across the disk." (4.2)
   - fitting: MCMC as for ALMA; posteriors in Fig. 6  
  > "Fig. [6] shows the posterior probability distribution for the $\mathrm{H_2CO}$ disk-averaged o/p ratio." (4.2)
   - validation: Compared model and observed ortho-line fluxes in rotational diagram; spin vs rotational temperature  
  > "This is the only model resulting in consistent spin and rotational temperatures." (4.2)

## Software

- **CASA** 4.7: Cleaning ALMA and SMA visibilities  
  > "cleaned in `CASA` 4.7" (2.1 ALMA)
- **MIR** : SMA calibration  
  > "The SMA data were first calibrated with the `MIR` software package" (2.2 SMA)
- **RADMC-3D** : Synthetic line emission, LTE level populations  
  > "using the `RADMC-3D` package (cite: dullemond2012) to compute the level populations" (4.1)
- **vis-sample** : Sampling model at observed uv points  
  > "using the `vis-sample` Python package" (4.1)
- **emcee** : MCMC posterior sampling  
  > "MCMC method implemented in the `emcee` package" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rotational temperature from three ortho lines | 24 | ±14 | K | 2 | We obtain a rotational temperature of $24\pm14$ K. |
| Best-fit o/p ratio, (z/r)_l=0.15 | 2.50 | +0.31/-0.27 | dimensionless | 4 | which gives an o/p ratio of $2.50^{+0.31}_{-0.27}$ |
| Spin temperature, best fit | 17 | +6/-3 | K | 4 | $\ensuremath{T_\ensuremath{\mathrm{spin}}}=17^{+6}_{-3}$ K |
| Range of o/p across models (1 sigma) | 1.8-2.8 | not stated | dimensionless | 4 | The possible values for the $\mathrm{H_2CO}$ o/p ratio are $1.8-2.8$ (within 1$\sigma$), corresponding to spin temperatures of $11-22$ K. |
| ALMA 290 GHz p-H2CO flux | 1.22 | 0.05 | Jy km/s | 2 | $1.22\pm 0.05$ |

## Qualitative findings

- H2CO emission is ring-like with central depletion, peak near 100 au and a weaker second peak/plateau near 400 au  
  > "The emission presents a ring-like spatial distribution, with a depletion of $\mathrm{H_2CO}$ emission at the disk center" (3.1)

## Claim tuples

- H: The disk-averaged H2CO o/p ratio is below the high-temperature value of 3, indicating low-temperature formation | E: Joint modeling of ALMA and SMA H2CO visibilities with RADMC-3D and MCMC | R: o/p = 1.8-2.8, Tspin 11-22 K | F: Consistent with low-temperature formation, likely grain surface chemistry | **supported**
- H: Rotational temperature from ortho lines traces cold H2CO | E: Rotational diagram of three ortho lines | R: 24±14 K | F: Emission at large scales arises from cold layers near the CO freeze-out temperature | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Abundance structure fixed from high-resolution ALMA line since SMA resolution is low  
  > "Given the lower angular resolution of the SMA observations, we keep the $\mathrm{H_2CO}$ abundance structure fixed, and vary only the o/p ratio." (4.2)
- Alternative: Third cold component near midplane tested; small contribution  
  > "suggesting that the contribution of such a third cold component to the overall $\mathrm{H_2CO}$ emission is small" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): o/p is a disk-averaged value; vertical distributions cannot be distinguished by SMA data  
  > "However, we cannot rule out any of the vertical distribution choices based on the SMA data." (4.2)
- Caveat (inferred, ours): Depends on a single ALMA line to set abundance structure
- Caveat (inferred, ours): Scale factor of 1.2-1.8 between SMA and ALMA is large compared to quoted flux uncertainties
- Caveat (inferred, ours): Low-S/N SMA fluxes give large o/p uncertainties
- Caveat (inferred, ours): Spin temperature interpretation is uncertain given lab results

## Reproducibility

- Data public (paper): ALMA project 2012.1.00681.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00681.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Priors, walker counts and convergence for emcee
- Missing: Self-calibration parameters
- Missing: SMA raw data and calibration details
- Missing: Cleaning thresholds and image sizes
- Data volume (inferred): ~10-50 GB for ALMA Cycle 1 Band 7 project; SMA data separate
- Score (inferred): 3/5, ALMA data public and software named, but MCMC and calibration details missing, and SMA data and a private-communication model input are needed.
- Rediscovery candidate: no, Needs SMA data and private-communication chemical-model inputs; fitting recipe incomplete.

## Links

- Method: (cite: qi2015) (Description of ALMA observations)
- Method: (cite: qi2011) (Disk physical structure)
- Companion: (cite: carney2017) (Higher-resolution 3-2 H2CO observations and rotational temperature)
- Companion: (cite: qi2013) (Earlier SMA H2CO observations)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
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
  "facts": 78,
  "stated": 56,
  "rate": 0.718
 },
 "evidence_ok": true
}
```
