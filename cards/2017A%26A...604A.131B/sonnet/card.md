# Exploring the volatile composition of comets C/2012 F6 (Lemmon) and C/2012 S1 (ISON) with ALMA

`2017A&A...604A.131B` | Astronomy and Astrophysics 2017 | first author: Bøgelund, Eva G. | arXiv: 1705.02812 | DOI: 10.1051/0004-6361/201629197

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system, astrochemistry
- Question: What are the production rates and parent scale lengths of volatile species in comets Lemmon and ISON, and how can line ratios constrain uncertainties from unknown collision rates and kinetic temperatures?  
  > "We derive production rates for a number of volatile coma species and explore how molecular line ratios can help constrain the uncertainties of these rates." (abstract)
- Target **C/2012 F6 (Lemmon)**: coordinates _not stated_; z/distance Delta = 1.705-1.748 AU; r_H 1.165-1.475 AU  
  > "The comet was discovered on 2012 March 23 and reached perihelion one year later on 2013 March 24 at a distance of 0.73 AU" (2 Observations); distance from JPL Horizons ephemerides  
  > "The comet was discovered on 2012 March 23 and reached perihelion one year later on 2013 March 24 at a distance of 0.73 AU" (2 Observations)
- Target **C/2012 S1 (ISON)**: coordinates _not stated_; z/distance Delta = 0.875-0.887 AU; r_H 0.557-0.589 AU  
  > "The comet reached perihelion on 2013 November 28 at a distance of merely 0.013 AU" (2 Observations); distance from JPL Horizons ephemerides  
  > "The comet reached perihelion on 2013 November 28 at a distance of merely 0.013 AU" (2 Observations)

## Data provenance

- ALMA projects: 2012.A.00020.S, 2012.A.00033.S, 2011.0.00012.SV
- bands: Band 7 (Cycle 1) for both comets; Band 6 SV for Lemmon  
  > "using the ALMA Band 7 receivers (covering the frequency range 275-373 GHz)." (2 Observations); "These observations were carried out using the Band 6 receivers (covering the frequency range 211-275 GHz)" (2 Observations)
- frequencies and spectral setup: Band 7 windows: 937500 kHz, 3840 channels, 244 kHz (~0.20 km/s); Band 6 SV: 234375 kHz, 61 kHz (0.07 km/s)  
  > "All spectral windows have a total bandwidth of 937500 kHz with 3840 equally spaced channels providing a spectral resolution of 244 kHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-2733 m (Lemmon B7), 15-1175 m (SV), 12-1284 m (ISON); baselines >~500 m excluded in imaging  
  > "no signal was detected on baselines longer than $\sim$500 m so we excluded these during imaging" (2 Observations)
- angular resolution: Restored beams 0.79x0.50 to 0.55x0.37 arcsec; CS beam 0.59x0.39 arcsec  
  > "The images were restored with a Gaussian beam between 0$\overset{\second}{.}$79$\times$0$\overset{\second}{.}$50 and 0$\overset{\second}{.}$55$\times$0$\overset{\second}{.}$37" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 15.8-91.7 min per setting  
  > "2013 Nov 16 - 2013 Nov 17 & 91.7" (Table 1)
- observing dates: Lemmon 30 May-2 June 2013 (B7), 11 May 2013 (B6 SV); ISON 16-17 Nov 2013  
  > "between 30 May and 2 June 2013 and 16 and 17 November 2013 for comets Lemmon and ISON respectively" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCN 4-3 and 3-2 (354.50547 / 265.88640 GHz)
- Line: CS 7-6 (342.88286 GHz)
- Line: HNC 4-3 (362.63030 GHz)
- Line: H2CO 5(1,5)-4(1,4) (351.76864 GHz)
- Line: CH3OH several (266.83812-350.90507 GHz)
- Line: HCO+ 3-2 and 4-3 (undetected) (267.55753 / 356.73424 GHz)
- Other facility **SOHO**: Water production rates  
  > "are deduced by (cite: Combi2014a; Combi2014) using the SOHO satellite." (4 Model)
- Other facility **JPL Horizons**: Ephemerides  
  > "The cometary positions were traced using JPL Horizons ephemerides" (2 Observations)
- External data: Water production rates of Lemmon and ISON  
  > "are deduced by (cite: Combi2014a; Combi2014) using the SOHO satellite." (4 Model) [from Combi2014a; Combi2014]
- External data: Photodestruction rates for HCN, CH3OH, H2CO  
  > "Photodestruction rates for HCN, CH$_3$OH and H$_2$CO are adopted from (cite: Crovisier1994)" (4 Model) [from Crovisier1994]
- External data: Collisional rates  
  > "molecular collision rates which we adopt from the Leiden Atomic and Molecular Database (cite: Schoier2005)" (4 Model) [from Schoier2005]
- External data: Kinetic temperatures 55 K (Lemmon), 90 K (ISON)  
  > "kinetic gas temperatures of 55 K for comet Lemmon and 90 K for comet ISON (cite: Cordiner2014)" (4 Model) [from Cordiner2014]

## Processing

### Calibration

- pipeline or manual: Optimised standard data delivery reduction scripts  
  > "We optimise the standard data delivery reduction scripts for each target and use these to flag and calibrate the data." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (Lemmon); Ceres and Titan (ISON); SV: J2232+117, J0006-0623, J0238+166  
  > "flux scale calibrations were done for Lemmon using Pallas and for ISON using Ceres and Titan." (2 Observations)
- flux scale uncertainty: 10% adopted  
  > "We adopt a conservative 10$\%$ error on the absolute flux calibration" (4.4)
- self calibration: _not stated_

### Imaging

- task: CASA 4.2.2 CLEAN  
  > "Deconvolution is done in CASA 4.2.2 using the CLEAN algorithm with natural visibility weighting." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "CLEAN algorithm with natural visibility weighting" (2 Observations)
- uv taper: _not stated_
- cell size: 0.1 arcsec  
  > "The image pixel size was set to 0$\overset{\second}{.}$1$\times$0$\overset{\second}{.}$1." (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied because comet offset from pointing centre  
  > "To account for the offset of the pointing centre with respect to the position of the cometary nucleus, images were primary beam corrected." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Exclusion of baselines >~500 m  
  > "As noted by (cite: Cordiner2014), no signal was detected on baselines longer than $\sim$500 m so we excluded these during imaging" (2 Observations) [from Cordiner2014]
- Kinetic temperatures  
  > "kinetic gas temperatures of 55 K for comet Lemmon and 90 K for comet ISON (cite: Cordiner2014)" (4 Model) [from Cordiner2014]

### Not stated but needed to reproduce (our reading)

- CLEAN iterations, threshold and masks
- Frequency/velocity range for line integration and continuum channels
- Aperture size for flux integration
- Which execution blocks/MS used
- Model grid spacing in Q and Lp
- Simobserve noise/atmosphere parameters
- Photodestruction rate values used
- Nucleus coordinates

## Analysis recipe

1. **Calibrate and image continuum and lines**: Standard scripts, CLEAN natural weighting, baselines <500 m, primary beam corrected, shifted to rest frequency  
  > "Deconvolution is done in CASA 4.2.2 using the CLEAN algorithm with natural visibility weighting." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with Cordiner et al. results  
  > "check the consistency of our new analysis by comparison to these papers" (Introduction)
2. **Model coma emission with Haser profile**: LIME non-LTE radiative transfer, spherical constant-velocity Haser model, collisions with H2O only (H2 rates scaled by 9.0), outer cut-off 5e3 km  
  > "This is done using LIME (cite: Brinch2010), a code for non-LTE line excitation and radiative transfer." (4 Model)
   - software: LIME
   - parameter: v_exp 0.7 km/s (Lemmon), 1.0 km/s (ISON)  
  > "We adopt expansion velocities of 0.7 km s$^{-1}$ for comet Lemmon and 1.0 km s$^{-1}$ for comet ISON" (4 Model)
   - assumption: T_kin 55 K Lemmon, 90 K ISON  
  > "kinetic gas temperatures of 55 K for comet Lemmon and 90 K for comet ISON" (4 Model)
   - fitting: _not stated_
   - validation: _not stated_
3. **Simulate ALMA observation of models**: Simobserve with antenna configuration, noise and atmosphere, then clean identically  
  > "After running Simobserve on all model outputs these are cleaned and imaged using the same parameters and routines as the observations." (4 Model)
   - software: CASA simobserve
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive production rates and parent scale lengths**: Grid of Q and Lp; chi2 minimisation on peak intensity and integrated flux in aperture  
  > "We then select the model that best reproduces the velocity integrated peak intensity and the specially integrated line flux in an aperture centred on each of the comets by minimising the $\chi^2$ values" (4.1)
   - software: LIME
   - fitting: chi2 grid search  
  > "we create a grid of models spanning a large range of molecular production rates and parent scale lengths." (Molecular production rates and parent scale lengths)
   - validation: Compared to DiSanti2016, Agundez2014, Cordiner2014  
  > "Within errors, we derive production rates in agreement with those presented by (cite: Cordiner2014) for HCN and HNC in both comets." (4.1)
5. **Constrain temperature and collision scaling with HCN(4-3)/(3-2)**: Model grid in T_kin (5-150 K) and Q_HCN/Q_H2O (1e-4 to 1) and collision scaling (1-20); test extreme cases on other species  
  > "We vary the temperature between 5 and 150 K and the Q$_{\rm HCN}$/Q$_{\rm H_2O}$ ratio between 10$^{-4}$ and 1." (4.4)
   - software: LIME
   - assumption: Constant coma temperature, collision scaling and HCN/H2O across dates  
  > "firstly, that the coma temperature and collision rate scaling are the same on both dates" (4.4)
   - fitting: reduced chi2 contours 1 and 3  
  > "the solid black lines show the reduced $\chi^2$ contours equal to 1 and 3." (HCN(4-3)/(3-2) line ratio)
   - validation: _not stated_

## Software

- **CASA** 4.2.2: Calibration, CLEAN imaging, Simobserve  
  > "Deconvolution is done in CASA 4.2.2" (2 Observations)
- **LIME** : Non-LTE 3D radiative transfer modelling  
  > "This is done using LIME (cite: Brinch2010)" (4 Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS parent scale length (ISON) | 200 | ±50 | km | 4 | CS & 7-6 & 65.83 & 6.7 |
| Q_CS (ISON) | 6.7e26 | +0.8/-0.7 | s^-1 | 4 | We derive production rates of 6.7$\times10^{26}$ s$^{-1}$ for CS in comet ISON |
| Q_CS/Q_H2O (ISON) | 0.19 | +0.023/-0.020 | % | 4 | derive a Q$_{\rm CS}$/Q$_{\rm H_2O}$ production rate ratio of 0.19$\%$ |
| HCN(4-3)/(3-2) line ratio (Lemmon) | 2.40 | ±0.34 | dimensionless | 5 | we derive a line ratio for HCN(4-3)/(3-2) of 2.40$\pm$0.34 |
| Q_H2CO (Lemmon, ISON) | 1.8e26, 8.0e26 | ±0.3e26, ±1.0e26 | s^-1 | 4 | we derive production rates of 1.8$\times$10$^{26}$ s$^{-1}$ and 8.0$\times$10$^{26}$ s$^{-1}$ for Lemmon and ISON respectively |
| Q_CH3OH (ISON) | 17.0e26 | ±5.0e26 | s^-1 | 4 | consistent with our value of (17.0$\pm$5.0)$\times10^{26}$ s$^{-1}$ |
| HNC/HCN ratio (ISON) | 0.45 | not stated | dimensionless | 4 | For comet ISON, we derive a HNC/HCN ratio of 0.45 |

## Qualitative findings

- HCN and CH3OH centrally peaked (parents); HNC and H2CO distributed  
  > "find centrally peaked, symmetric distributions for HCN and CH$_3$OH, indicative of parent species" (Conclusion)

## Claim tuples

- H: Is CS a parent or daughter species in comet ISON? | E: Fit Haser model to ALMA CS(7-6) map | R: Lp = 200±50 km, similar to the beam | F: CS tentatively a daughter species | **partially**
- H: Do collision scaling and temperature affect production rates? | E: Model grids of HCN(4-3)/(3-2) | R: Insensitive to collision scaling >5; T>30 K needed; T<110 K at 1σ | F: Line ratios mitigate uncertainties; temperature matters more | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CH3OH rejected as H2CO precursor  
  > "makes CH$_3$OH an unlikely predecessor of H$_2$CO" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Single outflow velocity and time-averaged production rate; H2CO is a lower limit (ortho only)  
  > "This is not surprising since we use a single parameter to express the outflow velocity of molecules." (4.3)
- Caveat (inferred, ours): Only one temperature and velocity per comet; HCN scale-length behaviour unexplained
- Caveat (inferred, ours): Time variability averaged over
- Caveat (inferred, ours): Resolution barely resolves CS Lp
- Caveat (inferred, ours): No MCMC; uncertainties from grid

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "In this paper we analyse archival observations obtained with the Atacama Large Millimeter/Submillimeter Array (ALMA) of two comets." (Introduction)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: aperture definitions
- Missing: model grid details
- Missing: Simobserve settings
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 3/5, Public data and clear model framework, but many imaging and fitting settings missing.
- Rediscovery candidate: no, Key imaging and grid-fit settings are unstated and require LIME modelling.

## Links

- Method: Brinch2010 (LIME code)
- Method: Haser1957 (Haser model)
- Companion: Cordiner2014 (Earlier analysis of same data)
- Companion: Cordiner2017b (Time variability of ISON emission)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 44,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
