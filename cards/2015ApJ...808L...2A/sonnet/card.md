# The 2014 ALMA Long Baseline Campaign: Observations of Asteroid 3 Juno at 60 Kilometer Resolution

`2015ApJ...808L...2A` | The Astrophysical Journal Letters 2015 | first author: ALMA Partnership | arXiv: 1503.02650 | DOI: 10.1088/2041-8205/808/1/L2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Can ALMA long-baseline 1.3 mm imaging resolve the surface of asteroid 3 Juno, giving its size, shape and brightness-temperature distribution, and test the DAMIT model and thermal properties of the regolith?  
  > "The availability of the DAMIT model provides an excellent test of ALMA’s imaging performance, while the resulting images provide new details on the surface conditions of Juno." (Introduction)
- Target **3 Juno**: coordinates 08 14 46.8474 +06 19 08.554 (J2000, image 0 centroid)  
  > "The direction of Juno was $\lambda =
124.7\ensuremath{^\circ}, \beta=-13.2\ensuremath{^\circ}$" (3.1 Viewing geometry); "which at the Earth-Juno distance of $\Delta=1.97$ AU corresponds to 60 km." (Observations); z/distance Δ = 1.97 AU (Earth-Juno); r = 2.072 AU  
  > "The direction of Juno was $\lambda =
124.7\ensuremath{^\circ}, \beta=-13.2\ensuremath{^\circ}$" (3.1 Viewing geometry); "which at the Earth-Juno distance of $\Delta=1.97$ AU corresponds to 60 km." (Observations); distance from JPL Horizons ephemeris (implied)  
  > "The direction of Juno was $\lambda =
124.7\ensuremath{^\circ}, \beta=-13.2\ensuremath{^\circ}$" (3.1 Viewing geometry); "which at the Earth-Juno distance of $\Delta=1.97$ AU corresponds to 60 km." (Observations)

## Data provenance

- ALMA projects: _none stated_
- bands: 1.3 mm (233 GHz) continuum  
  > "to observe the 1.3 mm (233 GHz) continuum emission from Juno was executed five consecutive times on 2014 Oct 19" (Observations)
- frequencies and spectral setup: 4 spectral windows, 2 GHz each, 128 channels, dual pol; centers 224, 226, 240, 242 GHz  
  > "Four spectral windows were used, each with 2 GHz bandwidth, 128 channels and dual polarization. Center frequencies were 224, 226, 240, and 242 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 0.02 to 10 Mλ (26 m to 13 km), 27-31 antennas  
  > "Data from 27 to 31 antennas were used, ranging in projected baseline length

from 0.02 to 10 M$\lambda$ (26 m to 13 km)." (Observations)
- angular resolution: beams 31.8x23.7 to 41.8x36.1 mas; smoothed to 42 mas circular  
  > "The images vary in the size of the synthesized beam from $31.8\times23.7$ mas to $41.8 \times 36.1$ mas" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~10 min per half-execution dataset (~18 min duration)  
  > "with the duration and time on source of each half being $\sim$18 min and $\sim$10 min, respectively" (Observations)
- observing dates: 2014 Oct 19, 09:15-13:38 UT, five executions of ~53 min SB  
  > "executed five consecutive times on 2014 Oct 19 starting at 09:15 UT (43 min before local sunrise) and ending at 13:38 UT" (Observations)
- pi or archival as stated: _not stated_
- Other facility **JPL Horizons**: external ephemeris for Juno  
  > "The SB included an external ephemeris with 4 min sampling obtained from Jet Propulsion Lab (JPL) Horizons" (Observations)
- Other facility **DAMIT online tool**: model sky-projected images of Juno for comparison  
  > "The model images shown in Figure [2](#juno_shifted) were obtained using the DAMIT online tool" (3.4 Comparison to DAMIT shape model)
- External data: Triaxial ellipsoid model and rotational pole of Juno  
  > "inferred from parametric blind deconvolution of near-infrared AO images (ecliptic longitude $\lambda = 118\ensuremath{^\circ}\/$ and latitude $\beta=+30\ensuremath{^\circ}\/$)" (3.1 Viewing geometry) [from (cite: Drummond08)]
- External data: Rotation period 0.300397125 days  
  > "using the rotation period of 0.300397125 days (cite: Kaas02)" (Table 1) [from (cite: Kaas02)]
- External data: Calibrator J0750+1231 flux density 0.64±0.04 Jy at 233 GHz, spectral index -0.66  
  > "yields an assumed flux density of 0.64$\pm$0.04 Jy at 233 GHz with a spectral index of $-0.66$" (Observations) [from (cite: vanKempen14)]
- Simulation/model as data: DAMIT 3D shape model (2036 faces) projected with the DAMIT online tool for comparison  
  > "A three-dimensional model with 2036 faces and 1020 vertices based on a combination of the historical optical light curves and two occultations" (Introduction)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2  
  > "Calibration and imaging was performed in CASA[^2] version 4.2.2." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231, 0.64±0.04 Jy at 233 GHz; gain calibrator J0757+0956  
  > "Bandpass and flux calibration is based on observations of the quasar J0750+1231 in each SB." (Observations)
- flux scale uncertainty: 6%  
  > "we estimate our flux scale to be accurate to 6%" (Observations)
- self calibration: Phase-only 300 s then 15 s; then amplitude 300 s; dynamic range 120 after  
  > "Phase-only self-calibration was then performed, initially with a time interval of 300 s, followed by a refinement with a time interval of 15 s." (Observations)

### Imaging

- task: _not stated_
- deconvolver: multi-scale clean, scales 0, 5, 15 pixels  
  > "The final images were constructed using multi-scale clean (cite: Rau11) with deconvolution scales of 0, 5, and 15 pixels" (Observations)
- weighting robust: robust = 0  
  > "The ten resulting datasets (epochs) were imaged individually using a robust weighting parameter of zero." (Observations)
- uv taper: _not stated_
- cell size: 5 mas  
  > "to within a fraction of the (5 mas) pixel size" (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: smoothed to circular 42.0 mas beam  
  > "we smoothed the images with a two dimensional elliptical Gaussian to obtain a circular beam of 42.0 mas" (Observations)
- final beam: 42 mas circular (60 km)  
  > "to obtain a circular beam of 42.0 mas, which at the Earth-Juno distance of $\Delta=1.97$ AU corresponds to 60 km." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Astrometric performance and campaign details  
  > "we expect our images to follow ALMA’s measured astrometric performance (cite: ALMA15a)" (Observations) [from (cite: ALMA15a)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations/thresholds and masks
- Imaging image size
- Exact self-cal reference model and antenna flagging
- Procedure to compute rotation-phase and DAMIT model settings beyond online tool
- Scheduling block UID/project code in text

## Analysis recipe

1. **Calibrate, split and image epochs with self-calibration**: Split each execution into two halves; image with robust 0 multiscale clean; phase then amplitude self-cal  
  > "the uv data from each execution was split into two halves" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Centroid before and after self-cal consistent within a fraction of pixel  
  > "the intensity-weighted centroid of the source before and after self-calibration is consistent to within a fraction of the (5 mas) pixel size" (Observations)
2. **Measure centroid, flux, peak and median brightness temperature**: Centroid of pixels >5σ; flux integrated >3σ; Planck T_B from peak and median clean-model pixel  
  > "computing the centroid of all pixels above the $5~\sigma$ level" (3.2 Images)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive size via uniform elliptical disk model**: Fit 2D Gaussian, build disk with axes +30%, convolve with 42 mas beam, iterate until Gaussian fit matches  
  > "Next we iteratively refined the disk model parameters until an elliptical Gaussian fit to the convolved disk model image matched the target parameters." (3.3 Size and shape measurement)
   - assumption: uniform brightness disk  
  > "we consider the underlying source to be an elliptical disk with uniform brightness" (3.3 Size and shape measurement)
   - fitting: _not stated_
   - validation: Compared with DAMIT, triaxial model, radar, IRAS, single-dish diameters  
  > "The mean diameter is also in reasonable agreement with the triaxial geometric mean ($250\pm5$ km)" (3.3 Size and shape measurement)
4. **Compare with DAMIT and map surface brightness variations**: DAMIT online tool predicted images; subtract uniform-brightness model from clean image  
  > "We then convolve this model with the 42 mas beam and subtract it from the clean image." (3.5 Surface features)
   - software: DAMIT online tool
   - fitting: _not stated_
   - validation: _not stated_
5. **Interpret with thermal models**: Equilibrium model and Standard Thermal Model; thermal inertia and skin depth after Lagerros96  
  > "we will proceed with $A=0.09$, which matches the result others have obtained by using the $p_{\rm V}$ values along with $q_{\rm V}=0.6$ appropriate for the Moon." (Discussion)
   - assumption: A=0.09, emissivity 1, eta=0.76  
  > "Assuming $\epsilon_\nu=1$, the equilibrium model prediction for $T_{B}$ for our Juno observations ($r=2.072$ AU) is then 188 K to 223 K, depending on $f$." (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: calibration and imaging  
  > "Calibration and imaging was performed in CASA[^2] version 4.2.2." (Observations)
- **DAMIT online tool** : model images of Juno for comparison  
  > "The model images shown in Figure [2](#juno_shifted) were obtained using the DAMIT online tool" (3.4 Comparison to DAMIT shape model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Geometric mean diameter | 259 | ±4 | km | 3 | We measure a geometric mean diameter of 259$\pm$4 km |
| Median peak brightness temperature | 215 | ±13 K | K | 2 | The median peak brightness temperature is 215$\pm$13 K |
| Median surface brightness temperature | 197 | ±15 K | K | 2 | while the median over the whole surface is $197\pm15$ K |
| Image dynamic range after self-calibration | 120 | not stated | dimensionless | 1 | The

image dynamic range after self-calibration was 120. |
| Thermal inertia (estimated) | 46 | not stated | J m^-2 s^-0.5 K^-1 | 5 | yields $\Gamma =
46$ J m$^{-2}$ s$^{-0.5}$ K$^{-1}$ |

## Qualitative findings

- Brightness temperature is highest near the subsolar point and afternoon areas, lowest beyond the evening terminator  
  > "higher values correlated to the subsolar point and afternoon areas, and lower values beyond the evening terminator" (abstract)

## Claim tuples

- H: ALMA can resolve Juno's shape and size consistent with the DAMIT model | E: Ten 1.3 mm images at 42 mas compared with DAMIT projections and a disk model | R: 259±4 km mean diameter; shapes mostly agree with DAMIT | F: ALMA size and shape confirm existing models | **supported**
- H: Surface brightness temperature varies with illumination and regolith properties | E: Subtracted uniform model from clean images | R: Warmest point at subsolar point in later images | F: Suggests lower thermal inertia at those longitudes, possibly linked to a crater | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Uniform-brightness disk is unphysical; sizes about 2-4% smaller than physical  
  > "We estimate that our method will yield sizes that are $\approx$2-4% smaller than the mean physical size." (3.3 Size and shape measurement)
- Caveat (inferred, ours): Thermal inertia interpretation is qualitative and model-dependent
- Caveat (inferred, ours): Crater link relies on unspecified AO image orientation
- Caveat (inferred, ours): No near-field correction applied

## Reproducibility

- Data public (paper): Images publicly available on ALMA Science Verification page, with calibration and imaging scripts  
  > "These images are publicly available from the ALMA Science Verification page" (Observations)
- Products in archive: _not stated_
- Code: Calibration and imaging scripts on CASA guides page  
  > "Additional details including the calibration and imaging scripts
        are available from" (footnote 4)
- Missing: Clean thresholds and masks
- Missing: Details of DAMIT rendering settings
- Data volume (inferred): ~10-50 GB
- Score (inferred): 4/5, Public SV data and scripts, clear recipe, numeric tables.
- Rediscovery candidate: yes, Data public as SV dataset, recipe fairly complete, numeric results in tables.

## Links

- Method: (cite: Rau11) (multi-scale clean)
- Companion: (cite: ALMA15a) (long baseline campaign description and astrometry)
- Related: ALMA 2014 Long Baseline Campaign
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00013.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 41,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
