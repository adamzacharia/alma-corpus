# ALMA Thermal Observations of a Proposed Plume Source Region on Europa

`2017AJ....154..148T` | The Astronomical Journal 2017 | first author: Trumbo, Samantha K. | arXiv: 1708.07922 | DOI: 10.3847/1538-3881/aa8769

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Is the Galileo PPR nighttime thermal excess near Pwyll Crater caused by excess endogenic heat flow (plume source) or by a local thermal inertia variation?  
  > "evaluate whether the anomaly is best explained by variation in the thermal inertia or whether it is truly indicative of an endogenic hot spot." (Introduction)
- Target **Europa (region northwest of Pwyll Crater)**: coordinates 276 deg W, 16.8 deg S (anomaly location)  
  > "centered on 276$\degree$ W and 16.8$\degree$ S, which is coincident with the Galileo thermal anomaly in the potential plume source region" (Fits to ALMA and Galileo PPR Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01302.S
- bands: Band 6 (~230 GHz), continuum TDM mode  
  > "The observation described in this paper was taken in Band 6, near 230 GHz, in the “continuum” (or “TDM”) mode, with the standard frequency tuning." (2 ALMA Observations and Data Reduction)
- frequencies and spectral setup: four SPWs: 224–226, 226–228, 240–242, 242–244 GHz; effective frequency 233 GHz  
  > "224–226 GHz; 226–228 GHz; 240–242 GHz; and 242–244 GHz." (2 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "The observations described herein were undertaken with the 12-m array" (2 ALMA Observations and Data Reduction)
- configurations: C36-7, 50 antennas, max useable spacing ~5 km  
  > "ALMA had 50 available antennas in its C36-7 configuration, with a maximum useable antenna spacing of $\sim$ 5 km." (2 ALMA Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: 0.05" effective resolution  
  > "deconvolved Europa image with the 0.05" effective resolution of the interferometer" (2 ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 Nov 27, 10:00–10:40 UTC  
  > "We observed Europa with ALMA on November 27 of 2015 from 10:00 to 10:40 UTC." (2 ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **Galileo PPR**: Nighttime thermal brightness temperature map of Pwyll region (data provided by J. Spencer)  
  > "The authors thank John R. Spencer for kindly providing the Galileo PPR data used within this paper." (Acknowledgments)
- Other facility **Voyager/Galileo USGS basemap**: Greyscale basemap used to build albedo map  
  > "USGS Voyager/Galileo greyscale basemap of Europa (at 2 pixel/degree resolution)" (3 Thermal Modeling)
- External data: Voyager normal albedo points in green, blue, violet, UV filters  
  > "We take the normal albedo points of (cite: McEwen1986) in the Voyager green, blue, violet, and ultraviolet filters" (3 Thermal Modeling) [from (cite: McEwen1986)]
- External data: Europa phase integral 1.01  
  > "As the phase integral of Europa is 1.01 (cite: Grundy2007)" (3 Thermal Modeling) [from (cite: Grundy2007)]
- External data: Regolith density 500 kg/m^3  
  > "We assume a snow-like constant regolith density of 500 $kg/m^3$ (cite: Spencer1999)" (3 Thermal Modeling) [from (cite: Spencer1999)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Fully calibrated visibilities provided by ALMA  
  > "Fully calibrated visibility data were provided by ALMA." (2 ALMA Observations and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: several iterations of self-calibration  
  > "We performed several iterations of self-calibration (cite: Taylor1999) on the visibility data" (2 ALMA Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: pixel sampling of 10 times the full spatial resolution  
  > "Figure [1](#fig:alma) shows this image with a pixel sampling of 10 times the full spatial resolution." (2 ALMA Observations and Data Reduction)
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

- Thermal model approach and roughness implementation similar to earlier work  
  > "similar to those developed in the past for several solar system bodies (cite: Spencer1989; Spencer1990; Hayne2015)" (3 Thermal Modeling) [from (cite: Spencer1989; Spencer1990; Hayne2015)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (flux calibrator, flux scale uncertainty)
- Self-calibration solution intervals and number of iterations
- Imaging task, weighting, deconvolver, masking, beam size and rms
- Absolute brightness-temperature scale and how Europa disk model was used for selfcal
- Galileo PPR data values (provided privately)
- Gridding range of thermal inertia and emissivity
- Fitting region and uncertainties on fitted parameters

## Analysis recipe

1. **Image Europa**: Self-calibrate calibrated visibilities and deconvolve, averaging all SPWs  
  > "We performed several iterations of self-calibration (cite: Taylor1999) on the visibility data to create a deconvolved Europa image" (2 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build albedo map**: Linear correlation between USGS basemap greyscale and Voyager normal albedos  
  > "The greyscale values and approximate normal albedos correlate linearly with an $R^2$ of .92 and a standard deviation of .03" (3 Thermal Modeling)
   - assumption: Normal albedos taken as hemispherical (phase integral 1.01)  
  > "we take these normal albedos as approximate hemispherical albedos" (3 Thermal Modeling)
   - fitting: linear fit  
  > "We then find the greyscale value of each corresponding point in the USGS basemap and use the resulting linear correlation to get an approximate wavelength-integrated normal albedo for each point in the USGS map." (Thermal Modeling)
   - validation: _not stated_
3. **Global thermal model and global fit**: 1D heat diffusion, grid over thermal inertia and emissivity, minimizing sum of squared residuals over region covered by both ALMA and PPR; model smoothed to beam / 140 km  
  > "we run our model for each observation over a wide grid of thermal inertias and emissivities and minimize the sum of the squares of the residuals" (4 Fits to ALMA and Galileo PPR Observations)
   - parameter: heat flux 20 mW/m^2 lower boundary; 5 skin depths; top layer d/30, growth 1.2; timestep <=1/500 Europa day  
  > "We define the thickness of the top layer to be $d/30$, with the thickness of each subsequent layer increasing by a factor of 1.2." (3 Thermal Modeling)
   - assumption: density 500 kg/m^3, cp 900 J/(K kg), emissivity equal at ALMA and PPR wavelengths, homogeneous disk  
  > "We treat the emissivities of the surface at the ALMA and PPR wavelengths as equal." (3 Thermal Modeling)
   - fitting: grid search chi-square minimization  
  > "we run our model for each observation over a wide grid of thermal inertias and emissivities and minimize the sum of the squares of the residuals for the region covered by both datasets." (Fits to ALMA and Galileo PPR Observations)
   - validation: Tested roughness (rms slopes to 20 deg), subsurface sensing and sunlight penetration variants  
  > "We tested a roughness model with rms slopes up to 20$\degree$" (3 Thermal Modeling)
4. **Test endogenic heat vs thermal inertia at anomaly**: Model 156 km radius area over diurnal cycle, fit ALMA (95.6 K) and PPR (95.1 K) points by varying heat flux or thermal inertia and albedo  
  > "We define the best fits by minimizing the sum of the squares of the differences between the models and the two data points." (4 Fits to ALMA and Galileo PPR Observations)
   - fitting: least squares on two data points  
  > "We define the best fits by minimizing the sum of the squares of the differences between the models and the two data points." (Fits to ALMA and Galileo PPR Observations)
   - validation: albedo change compared to albedo uncertainty (4 sigma)  
  > "a 4$\sigma$ deviation from our albedo model" (4 Fits to ALMA and Galileo PPR Observations)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit global emissivity | 0.8 | not stated | dimensionless | 3 | an emissivity of 0.8 and a thermal inertia of 95 $J/(m^2 \cdot K \cdot s^{1/2})$ provide the best result |
| Best-fit global thermal inertia | 95 | not stated | J m^-2 K^-1 s^-1/2 | 3 | an emissivity of 0.8 and a thermal inertia of 95 $J/(m^2 \cdot K \cdot s^{1/2})$ provide the best result |
| Local thermal inertia needed at anomaly | 140 (47% increase), albedo 0.56 to 0.59 | not stated | J m^-2 K^-1 s^-1/2 | 4 | increasing the thermal inertia by 47$\%$ from 95 to 140 |
| Heat flux to match PPR night only | 0.66 (from 0.02) | not stated | W m^-2 | 4 | requires raising the subsurface heat flux from 0.02 $W/m^2$ to 0.66 $W/m^2$ |
| Heat flux matching both with albedo 0.69 | 1.6 | not stated | W m^-2 | 4 | A local heat flux of 1.6 $W/m^2$ can account for both the ALMA and Galileo PPR brightness temperatures |
| ALMA brightness temperature at anomaly | 95.6 | not stated | K | 4 | the ALMA data point is taken to be 95.6 K |

## Qualitative findings

- Pwyll region is warm at night and cold by day relative to model, indicating thermal inertia variation  
  > "shows up as anomalously hot at night and cold during the day. This pattern is suggestive of a variation in the local thermal inertia." (4 Fits to ALMA and Galileo PPR Observations)

## Claim tuples

- H: The nighttime thermal anomaly is due to endogenic heat flow | E: Fit ALMA day and PPR night brightness temperatures with a heat-flux increase | R: Matching night gives daytime temperature far too high; only works with 23% albedo increase (4 sigma) | F: Endogenic heating alone cannot explain the anomaly | **supported**
- H: A local thermal inertia increase explains the anomaly | E: Fit both data points raising thermal inertia and albedo | R: Inertia 95 to 140 with albedo 0.56 to 0.59 matches both | F: Anomaly most likely a thermal inertia variation, perhaps from Pwyll ejecta | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Anomaly was endogenic at Galileo time (1998) but cooled by 2015; cannot be ruled out  
  > "We cannot rule out the possibility that the region associated with the thermal anomaly was anomalously warm due to endogenic heat at the time of the Galileo observation in 1998, but has since cooled." (4 Fits to ALMA and Galileo PPR Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple homogeneous model; emissivities at ALMA and PPR wavelengths unknown  
  > "However, the relevant emissivities for Europa-like conditions and compositions are not known." (3 Thermal Modeling)
- Caveat (inferred, ours): Only two data points constrain the local fit, with no stated uncertainties
- Caveat (inferred, ours): Equal emissivity at 1.3 mm and 27.5 micron is assumed and strongly affects brightness temperatures
- Caveat (inferred, ours): Absolute ALMA flux calibration for a resolved moving target not discussed

## Reproducibility

- Data public (paper): ALMA project code cited; Galileo PPR data provided privately by J. Spencer  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01302.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Thermal model code
- Missing: Galileo PPR data
- Missing: Imaging parameters and self-cal settings
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, ALMA data are archival-accessible and model is described in detail, but imaging details and PPR data are missing.
- Rediscovery candidate: no, Imaging details are missing and PPR data are not public.

## Links

- Method: (cite: Hayne2015) (Thermal model and roughness implementation)
- Companion: (cite: Spencer1999) (Galileo PPR nighttime observation of Pwyll)
- Companion: (cite: Sparks2017) (Potential plume detection near Pwyll)
- Related: Galileo PPR
- Related: HST Europa plume observations

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 33,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
