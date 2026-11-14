# Disk-integrated Thermal Properties of Ceres Measured at Millimeter Wavelengths

`2020AJ....159..215L` | The Astronomical Journal 2020 | first author: Li, Jian-Yang | arXiv: 2003.11045 | DOI: 10.3847/1538-3881/ab8305

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the disk-integrated brightness temperature, rotational lightcurve and subsurface thermal/dielectric properties of Ceres at ~1.1 mm, and is HCN present around Ceres?  
  > "to map the temperatures of Ceres over a full rotation at each epoch. We also used 2017 October ACA observations to search for HCN." (abstract)
- Target **Ceres**: coordinates _not stated_; z/distance heliocentric distance 2.540-3.092 au (Table 1)  
  > "Ceres had apparent angular diameter of 0.43” to 0.48” in our data." (2.1. Observations); distance from observing geometry (Table 1)  
  > "Ceres had apparent angular diameter of 0.43” to 0.48” in our data." (2.1. Observations)

## Data provenance

- ALMA projects: 2015.1.01384.S, 2016.1.00748.S
- bands: Band 6 (~265 GHz, ~1.1 mm)  
  > "All 12-m array observations were performed in Band 6 with a spectral setup optimized for continuum measurement sensitivity" (2.1. Observations)
- frequencies and spectral setup: 12-m: four 2 GHz SPWs at 256, 258, 272, 274 GHz; ACA: one SPW on HCN J=3-2 (244 kHz resolution) plus 3 continuum SPWs at 252.5, 254.5, 269.5 GHz  
  > "using four 2 GHz-wide spectral windows tuned to 256, 258, 272, and 274 GHz for a total of 7.5 GHz of effective bandwidth." (2.1. Observations); "three 2 GHz-wide spectral windows tuned at 252.5, 254.5, 269.5 GHz were dedicated to continuum integration." (2.1. Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array (Cycles 3, 4, 5) and ACA (Cycle 5)  
  > "In Cycle 5, we also used the Atacama Compact Array (ACA) in addition to the 12-m array." (2.1. Observations)
- configurations: _not stated_
- baselines: longest baselines up to 15 km, at least 40 antennas  
  > "the longest baselines reaching up to 15 km with 40 antennas at a minimum" (2.1. Observations)
- angular resolution: ACA ~5 arcsec; 12-m resolves Ceres in 10-20 beams  
  > "ACA observations, with a spatial resolution of 5”, did not spatially resolve Ceres." (2.1. Observations)
- max recoverable scale: _not stated_
- sensitivity: image RMS 0.07-0.6 mJy/beam, dominated by imaging dynamics; S/N >120  
  > "which ranges from 0.07 to 0.6 mJy per beam, dominating over the thermal noise." (3.1. Rotational lightcurve)
- time on source: _not stated_
- observing dates: 2015 Nov, 2017 Sep/Oct (Table 1)  
  > "three epochs in 2015 November and 2017 September and October" (abstract)
- pi or archival as stated: _not stated_
- Line: HCN J=3-2 (265.886 GHz)
- External data: Historical brightness temperature/flux measurements of Ceres near 265 GHz (Table 2)  
  > "Historical measurements of the total flux and brightness temperature at frequencies close to our data (265 GHz) in the literature, including those from ALMA archive." (Table 2) [from Moullet et al. 2010; Redman et al. 1998; Altenhoff et al. 1994, 1996; Ulich et al. 1984; Webster et al. 1988]
- External data: Triaxial shape model of Ceres  
  > "Triaxial ellipsoidal shape 482.64 ´ 480.64 ´ 445.57 km Russell et al., (2016)" (Table A1) [from Russell et al. 2016]
- External data: Bolometric Bond albedo 0.037  
  > "Bolometric Bond albedo 0.037 Li et al. (2019)" (Table A1) [from Li et al. 2019]
- External data: Emissivity 0.95  
  > "Emissivity 0.95 Keihm et al. (2013)" (Table A1) [from Keihm et al. 2013]

## Processing

### Calibration

- pipeline or manual: ALMA automated science pipeline in CASA  
  > "All data was calibrated using ALMA’s automated science pipeline package, CASA (McMullin et al., 2007)." (2.2. Data reduction and flux calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Flux scale refined with quasar J1924-2914 (Cycle 3) and J0854+2006 (Cycles 4, 5)  
  > "quasar J19242914 was selected as the most reliable calibrator for all observations, and for our data from Cycles 4 and 5 (both 12-m and ACA) in 2017, quasar J0854+2006 was the best available calibrator." (2.2. Data reduction and flux calibration)
- flux scale uncertainty: 5%  
  > "We estimate a 5% absolute calibration uncertainty corresponding to the uncertainty on the quasar" (2.2. Data reduction and flux calibration)
- self calibration: phase self-calibration based on imaging results applied to 12-m data  
  > "phase self-calibration based on imaging results was also applied successfully to improve corrections of short-term phase gain variations." (2.2. Data reduction and flux calibration)

### Imaging

- task: _not stated_
- deconvolver: Subtract uniform disk model, clean residuals, add model back  
  > "the best results were obtained by subtracting a uniform disk model, cleaning the residuals, and then adding the initial model to the cleaned components." (2.2. Data reduction and flux calibration)
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Standard thermal model for expected brightness temperature  
  > "standard thermal model (STM, Lebofsky et al. 1986) with no infrared beaming parameter" (3.2. Brightness temperature variations) [from Lebofsky et al. 1986]
- HCN rotational temperature relation Trot = 60/rh  
  > "we used the empirical relationship _T_ rot = 60/ _r_ h derived from observations of cometary comae" (3.3. Search for HCN) [from Villanueva et al. 2018]

### Not stated but needed to reproduce (our reading)

- CASA and pipeline versions
- tclean parameters (weighting, cell, image size, masks, iterations)
- self-calibration solution intervals
- exact uniform disk model parameters
- how flux density was converted to Tb (beam/disk size used)
- Cycle 3/4/5 pipeline calibrator choices per execution
- KRC run parameters (layer grid, time steps)
- how measured Tb 173 K was matched to model grid
- ACA spectral baseline/continuum handling
- project code 2017.1.01640.S is printed with a typo in the paper

## Analysis recipe

1. **Measure total flux density lightcurves**: Aperture photometry on 12-m images made from 5-15 min data; ACA flux from averaged visibility amplitudes; visibility fitting as cross-check  
  > "We used circular apertures with diameters of 0.6” to 0.8” centered on Ceres’s disk to make integrated photometry measurements." (3.1. Rotational lightcurve)
   - software: CASA
   - fitting: _not stated_
   - validation: Simulated disk observations to check flux recovery; compared Cycle 4 12-m with Cycle 5 ACA lightcurves  
  > "Our tests suggested no issues recovering the total flux of Ceres from our data." (3.1. Rotational lightcurve)
2. **Compute brightness temperatures**: Rayleigh-Jeans conversion of total flux; compare with STM expectation (216 K) to derive emissivity  
  > "We calculated brightness temperatures for Ceres based on total flux density measurements using the Rayleigh-Jeans approximation" (3.2. Brightness temperature variations)
   - fitting: _not stated_
   - validation: Compared with archival ACA data and historical measurements  
  > "we searched the ALMA archive for ACA data of Ceres acquired at times close to our Cycle 3 observations and found four sets of data." (3.2. Brightness temperature variations)
3. **Search for HCN and derive upper limit**: Average ACA spectra from Oct 18-20, bin to 300 kHz, model 3-sigma limit with PSG Haser model  
  > "finding the production rate that has the flux density at the peak of the J=3-2 emission line comparable to our 3-s noise level of 0.054 Jy." (3.3. Search for HCN)
   - software: Planetary Spectrum Generator
   - parameter: Trot = 23 K  
  > "set the rotational temperature of HCN molecules to _T_ rot = 23 K." (3.3. Search for HCN)
   - assumption: Globally uniform production, Haser model  
  > "The PSG assumes the Haser model (Haser 1957)" (3.3. Search for HCN)
   - fitting: _not stated_
   - validation: Varying Trot changes limit by factor 2-3  
  > "would change our resulting upper limit production rate by a factor of 2-3." (3.3. Search for HCN)
4. **Thermophysical and radiative transfer modeling**: USGS KRC thermal model with triaxial shape, then radiative transfer integral over depth; model disk-averaged 265 GHz Tb vs loss tangent for thermal inertia 10-320 tiu  
  > "surface and subsurface temperature profiles and distributions using the USGS KRC code (Kieffer 2013)." (Appendix A)
   - software: KRC
   - parameter: Refractive index 1.5; loss tangent explored 1e-4 to 1  
  > "We adopted a value of 1.5 in our modeling" (Appendix A)
   - assumption: Single-layer model, constant thermal parameters, no roughness or IR beaming  
  > "single-layer thermal model, constant thermal parameters as listed in Table A1, and constant dielectric constant" (5.2. Implications of high electrical absorption)
   - fitting: Graphical comparison of measured Tb (~173 K) with model curves; no formal fit  
  > "our brightness temperature measurement of about 173 K from our 2017 September and October observations suggests that the loss tangent is in the range of about 0.1" (4. Thermophysical modeling)
   - validation: Compared inferred loss tangent with prior modeling (Keihm 2013, Chamberlain 2009)  
  > "Therefore, we find that our inferred high loss tangent is in fact consistent with previous modeling results." (4. Thermophysical modeling)

## Software

- **CASA** : Calibration, imaging, cleaning  
  > "All data was calibrated using ALMA’s automated science pipeline package, CASA (McMullin et al., 2007)." (2.2. Data reduction and flux calibration)
- **Planetary Spectrum Generator** : HCN upper limit production rate  
  > "We estimated the upper limit production rate of HCN using the Planetary Spectrum Generator" (3.3. Search for HCN)
- **KRC** : Thermophysical modeling  
  > "using the USGS KRC code (Kieffer 2013)" (Appendix A)
- **ALMA Sensitivity Calculator** : Thermal noise estimate  
  > "estimated using the ALMA Sensitivity Calculator" (3.1. Rotational lightcurve)
- **Astropy** : Open source Python analysis  
  > "Astropy (Astropy Collaboration 2013), Matplotlib (Hunter 2007), SciPy (Jones et al. 2001)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lightcurve peak-to-peak amplitude | 4 | not stated | % | 1 | the maximum rotational variation of the observed Ceres flux density is 4% (peak-to-peak). |
| Disk-averaged brightness temperature (2017) | 170-180 | not stated | K | 2 | The disk-averaged brightness temperature of Ceres is measured to be between 170 K and 180 K during our 2017 observations. |
| Effective emissivity | 0.8 | not stated | dimensionless | 2 | the expected brightness temperature of Ceres is 216 K, resulting in an effective emissivity of 0.8 |
| HCN 3-sigma upper limit production rate | 2e24 | not stated | molecules s-1 | 3 | We estimate a 3-s upper limit production rate of HCN of 2´10 [24] molecules s [-1] |
| Loss tangent | 0.1-0.3 | not stated | dimensionless | 4 | suggests that the loss tangent is in the range of about 0.1 – 0.3 |
| Thermal inertia | 40-160 | not stated | tiu | 4 | The possible range of thermal inertia of Ceres is therefore probably between 40 and 160 tiu. |
| Seasonal Tb variation range | ~20 | not stated | K | 2 | The range of annual brightness temperature variations is about 20 K. |

## Qualitative findings

- Cycle 3 and Cycle 5 12-m lightcurves unreliable due to high phase RMS from weather  
  > "bad weather conditions rendered the lightcurves derived from Cycle 3 and Cycle 5 12-m data unreliable for further analysis." (3.1. Rotational lightcurve)

## Claim tuples

- H: Does Ceres show a rotational lightcurve at 1 mm? | E: Full-rotation 12-m Cycle 4 and ACA Cycle 5 flux photometry | R: Double-peaked, ~4% peak-to-peak | F: Lightcurve is real and consistent with earlier low-amplitude reports | **supported**
- H: Is HCN present around Ceres? | E: ACA HCN J=3-2 spectrum search | R: No detection, 3-sigma limit 2e24 molecules/s | F: Non-detection | **supported**
- H: Does Ceres's surface have higher dielectric absorption than lunar-like material at 1 mm? | E: KRC plus radiative transfer model vs measured Tb | R: Loss tangent 0.1-0.3; thermal inertia 40-160 tiu | F: High absorption, possibly related to hydrated composition and small grains | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Shape and albedo variations rejected as cause of lightcurve  
  > "Therefore, only variations in thermal properties and the physical properties that affect thermal emission at a wavelength of 1 mm can be responsible" (5.1. Lightcurve and longitudinal thermal variations)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is extremely simplified; Cycle 3 flux likely not fully recovered  
  > "Of course, this is an extremely simplified model." (5.1. Lightcurve and longitudinal thermal variations)
- Caveat (inferred, ours): No formal fit or uncertainties on loss tangent and thermal inertia
- Caveat (inferred, ours): Only one lightcurve pair used for conclusions
- Caveat (inferred, ours): Cycle 3 low flux unexplained
- Caveat (inferred, ours): Dielectric real part fixed

## Reproducibility

- Data public (paper): ALMA project data cited; archive ACA data used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01384.S," (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Disk model details
- Missing: Model grid and flux-to-Tb conversion
- Data volume (inferred): Hundreds of GB (extended 12-m array, three epochs plus ACA)
- Score (inferred): 4/5, Public data and a simple photometry plus model workflow, but imaging and modeling details are sparse.
- Rediscovery candidate: no, Calibration refinements and modeling details are insufficiently specified; model comparison is graphical.

## Links

- Method: Kieffer 2013 (KRC thermal model)
- Method: Villanueva et al. 2018 (PSG)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.01640.S"
 ],
 "codes_printed_but_missing": [
  "2017.1.0640.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
