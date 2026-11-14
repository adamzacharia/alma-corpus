# Ethyl Cyanide On Titan: Spectroscopic Detection and Mapping Using Alma

`2015ApJ...800L..14C` | The Astrophysical Journal Letters 2015 | first author: Cordiner, M. A. | arXiv: 1410.5325 | DOI: 10.1088/2041-8205/800/1/L14

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system, astrochemistry
- Question: Is gas-phase ethyl cyanide (C2H5CN) present in Titan's atmosphere, and what are its vertical and spatial distributions compared with HC3N, CH3CN and CH3CCH?  
  > "we employ millimeter-wave data obtained from the Atacama Large Millimeter/submillimeter Array (ALMA) Science Archive to search for and map rotational emission lines from C$_2$H$_5$CN in Titan’s atmosphere" (Introduction)
- Target **Titan**: coordinates not stated (tracked ephemeris position)  
  > "Titan’s geocentric distance of 9.51 AU at the time of observation" (Observations); z/distance 9.51 AU geocentric  
  > "Titan’s geocentric distance of 9.51 AU at the time of observation" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00319.S
- bands: Band 6  
  > "Two 4 minute integrations were obtained using the dual-sideband Band 6 receiver" (Observations)
- frequencies and spectral setup: 4 basebands: 221.48-223.35, 223.48-225.35 GHz (LSB), 236.48-238.36, 239.48-241.36 GHz (USB); 3840 channels each; 488 kHz spacing, 976 kHz resolution  
  > "with frequencies 221.48-223.35 GHz and 223.48-225.35 GHz in the lower sideband, and 236.48-238.36 GHz and 239.48-241.36 GHz in the upper sideband, with 3840 channels per spectral window." (Observations)
- continuum bandwidth: _not stated_
- arrays: twenty 12-m antennae  
  > "with twenty 12-m antennae in the telescope array, providing baselines in the range 21-402 m" (Observations)
- configurations: _not stated_
- baselines: 21-402 m  
  > "providing baselines in the range 21-402 m" (Observations)
- angular resolution: 0.85'' x 0.67'' at 223.5 GHz  
  > "was $0.85''\times0.67''$ (long axis $57.3^{\circ}$ clockwise from celestial north)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: two 4 minute integrations  
  > "Two 4 minute integrations were obtained" (Observations)
- observing dates: 2012-07-03 23:22:14 to 2012-07-04 01:06:18 UT  
  > "between UT 2012-07-03 23:22:14 and 2012-07-04 01:06:18" (Observations)
- pi or archival as stated: archival; flux calibration observations  
  > "using ALMA archival spectra recorded in July 2012" (Summary)
- Line: C2H5CN many, e.g. 25(10,15)-24(10,14) (222.918-240.429 GHz)
- Line: HC3N J=26-25 (236.513 GHz)
- Line: CH3CCH 13_K-12_K (222.014-222.167 GHz)
- Other facility **Cassini CIRS and HASI**: atmospheric temperature profile  
  > "The atmospheric temperature profile was generated from a combination of Cassini CIRS and HASI measurements" (Results)
- External data: Titan temperature profile from Cassini CIRS and HASI  
  > "The atmospheric temperature profile was generated from a combination of Cassini CIRS and HASI measurements" (Results) [from (cite: fla05; ful05)]
- External data: Line parameters and partition functions from JPL catalog  
  > "Spectral line parameters and partition functions were taken from the JPL catalog." (Results) [from JPL catalog]
- External data: Butler-JPL-Horizons 2010 Titan flux model  
  > "scaled to match the Butler-JPL-Horizons 2010 Titan flux model (see ALMA Memo #594)" (Observations) [from ALMA Memo #594]

## Processing

### Calibration

- pipeline or manual: archive data processed with standard JAO scripts (flagging, bandpass, gain)  
  > "already processed using the standard scripts and protocols provided by the Joint ALMA Observatory. This included routine flagging, bandpass calibration and complex gain calibration." (Observations)
- casa version: CASA 4.2.1  
  > "NRAO CASA software (version 4.2.1)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Butler-JPL-Horizons 2010 Titan model; 3C 279 bandpass  
  > "The bright quasar 3C 279 was observed for bandpass calibration." (Observations)
- flux scale uncertainty: within 15%  
  > "which is expected to be accurate to within 15%" (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "imaging was carried out using the `clean` task" (Observations)
- deconvolver: Hogbom, threshold twice expected RMS  
  > "using the Hogbom algorithm, with natural visibility weighting and a threshold flux level of twice the expected RMS noise" (Observations)
- weighting robust: natural  
  > "with natural visibility weighting" (Observations)
- uv taper: _not stated_
- cell size: 0.1'' x 0.1''  
  > "The image pixel sizes were set to $0.1''\times0.1''$." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "Continuum-subtraction of the visibility amplitudes was performed using the `uvcontsub` task" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.85'' x 0.67''  
  > "was $0.85''\times0.67''$ (long axis $57.3^{\circ}$ clockwise from celestial north)" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Radiative transfer modelling strategy  
  > "Adopting a similar strategy to (cite: cor14), the spatially-integrated C$_2$H$_5$CN emission lines in the range 223.9-224.2 GHz were modeled" (Results) [from (cite: cor14)]
- Isotopologue and aerosol abundances  
  > "the abundances of nitrogen and methane isotopologues and aerosols were the same as used by (cite: tea13)" (Results) [from (cite: tea13)]

### Not stated but needed to reproduce (our reading)

- uvcontsub line-free channels and fit order
- clean mask and iterations
- Titan-frame velocity handling details
- Specific aerosol and isotopologue abundance values
- Noise estimation for fit uncertainties and the 3 sigma line detection
- Exact lines summed for the C2H5CN map
- Fitting algorithm details within NEMESIS

## Analysis recipe

1. **calibrate, subtract continuum and image**: Archive-calibrated data flux-scaled to Titan model, uvcontsub, clean per channel, Doppler-shift to Titan rest frame  
  > "The images were transformed from equatorial coordinates to (projected) linear distances with respect to the center of Titan" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **extract disk-integrated spectra and identify lines**: Integrate cubes in circular region radius 1.1''; assign with Splatalogue, CDMS, JPL  
  > "integrating the reduced ALMA data cubes within a circular region of radius $1.1''$ from the center of Titan" (Results)
   - software: Splatalogue
   - fitting: _not stated_
   - validation: Features detected at >3 sigma; spectra uncrowded  
  > "The spectra are sufficiently uncrowded that unambiguous assignments were possible for all detected lines." (Results)
3. **make integrated-line emission maps**: Sum strongest lines per species (six C2H5CN lines 223.9-224.1 GHz) and overlay on continuum  
  > "the strongest six lines in the range 223.9-224.1 GHz (shown in Fig. 3(b)) were summed to improve the signal-to-noise ratio of the map" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **retrieve C2H5CN vertical profile**: Line-by-line radiative transfer least-squares fits of step and gradient abundance profiles to 223.9-224.2 GHz lines  
  > "least-squares fits to the observed spectra were performed using C$_2$H$_5$CN abundance profiles with constant mixing ratio above a specified cutoff altitude $z_c$ and zero abundance below." (Results)
   - software: NEMESIS
   - parameter: step z_c 100-400 km; gradient model reference altitude 292 km, slope as fraction of scale height  
  > "The free parameters in this model were the abundance at a reference altitude $z_r = 292$ km" (Results)
   - assumption: Profiles do not vary with latitude/longitude; Lorentzian half-width 0.075 cm-1 atm-1 at 296 K, exponent 0.50; model atmosphere to 1000 km  
  > "The Lorentzian broadening half-width at 296 K was assumed to be 0.075 cm$^{-1}$ atm$^{-1}$, with a temperature-dependence exponent of 0.50." (Results)
   - fitting: least-squares, reduced chi^2  
  > "Initially, least-squares fits to the observed spectra were performed using C$_2$H$_5$CN abundance profiles with constant mixing ratio above a specified cutoff altitude $z_c$ and zero abundance below." (Results)
   - validation: Reduced chi^2 values; fit quality of 300 and 400 km models  
  > "The quality of these fits confirms that our C$_2$H$_5$CN line assignments are secure." (Results)

## Software

- **CASA** 4.2.1: uvcontsub and clean imaging  
  > "NRAO CASA software (version 4.2.1)" (Observations)
- **NEMESIS** : line-by-line radiative transfer retrieval  
  > "line-by-line radiative transfer module of the NEMESIS atmospheric retrieval code" (Results)
- **Splatalogue** : line assignment  
  > "Spectral peaks were assigned using the Splatalogue database for astronomical spectroscopy" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C2H5CN abundance at 292 km (gradient model) | 1.3 | 0.4 | ppb | 4 | The best-fitting abundance at $z_r$ was found to be $1.3 \pm 0.4$ ppb |
| fractional scale height f_H | 4.6 | 1.1 | dimensionless | 4 | with a retrieved fractional scale height of $f_H = 4.6 \pm 1.1$ |
| Vertical column density, gradient model | 3.6e14 | not stated | cm^-2 | 4 | Gradient      /      1.30       /      292       /   0.97   / $3.6\times10^{14}$ |
| Column density range for good-fit models | (1-5)e14 | not stated | cm^-2 | 4 | The models that fit the data well have values in the range $(1-5)\times10^{14}$ cm$^{-2}$. |
| Peak S/N of maps C2H5CN, HC3N, CH3CN, CH3CCH | 15, 40, 17, 29 | not stated | dimensionless | 3 | C$_2$H$_5$CN: 15, HC$_3$N: 40, CH$_3$CN: 17, CH$_3$CCH: 29. |

## Qualitative findings

- C2H5CN emission is concentrated in the southern hemisphere whereas other species peak in the north  
  > "the emission from C$_2$H$_5$CN is found to be concentrated in the southern (autumn) hemisphere" (abstract)

## Claim tuples

- H: Gas-phase C2H5CN is present in Titan's atmosphere | E: Search archival ALMA Band 6 spectra | R: 27 lines in 19 features detected at >3 sigma | F: First spectroscopic detection of C2H5CN | **supported**
- H: C2H5CN is located at high altitude | E: Radiative transfer fits with step and gradient profiles | R: Good fits for z_c 300/400 km and gradient; poor for 100 km | F: Mostly at altitudes >~200 km | **supported**
- H: C2H5CN spatial distribution differs from other nitriles | E: Integrated line maps | R: 7 sigma southern enhancement | F: Suggests short chemical lifetime | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Temperature variation as the cause of asymmetry judged unlikely  
  > "so spatial variations in the gas temperature are an unlikely explanation for the observed asymmetries" (Molecular Emission Maps)
- How they decided it was enough: _not stated_
- Limitation (authors): No temperature information for the epoch; further work needed  
  > "temperature information for the epoch of our observations is lacking, so further work will be needed to firmly establish the relative distributions of these species" (Molecular Emission Maps)
- Caveat (inferred, ours): Spatial resolution comparable to Titan's disk, so north-south structure is poorly resolved
- Caveat (inferred, ours): Retrieval assumes latitude-independent profiles while claiming latitudinal asymmetry
- Caveat (inferred, ours): Uncertainties on step models and degeneracy of altitude with abundance not given

## Reproducibility

- Data public (paper): data from ALMA Science Archive  
  > "obtained from the Atacama Large Millimeter/submillimeter Array (ALMA) Science Archive" (Introduction)
- Products in archive: _not stated_
- Missing: Atmospheric abundance profiles for aerosols/isotopologues
- Missing: uvcontsub channel selection
- Missing: NEMESIS configuration details
- Data volume (inferred): ~ a few GB
- Score (inferred): 3/5, Public archival data and a clear description of imaging, but retrieval inputs and several settings are not given.
- Rediscovery candidate: yes, Public data, a mostly specified recipe and numeric results (column densities and abundances).

## Links

- Method: (cite: irw08) (NEMESIS retrieval code)
- Method: (cite: mcm07) (CASA)
- Companion: (cite: cor14) (earlier ALMA Titan study with a similar modelling strategy)

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
  "facts": 69,
  "stated": 43,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
