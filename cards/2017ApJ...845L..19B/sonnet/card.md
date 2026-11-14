# A First Comparison of Millimeter Continuum and Mg II Ultraviolet Line Emission from the Solar Chromosphere

`2017ApJ...845L..19B` | The Astrophysical Journal Letters 2017 | first author: Bastian, T. S. | arXiv: 1706.04532 | DOI: 10.3847/2041-8213/aa844c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How do ALMA 1.25 mm continuum brightness temperature and IRIS Mg II h2v radiation temperature compare in a solar active region, and why do slope and offset differ?  
  > "In this Letter we present a first comparison of solar observations of the chromosphere in a solar active region made by ALMA in the 1.25 mm band (239 GHz)" (Introduction)
- Target **NOAA active region 12470**: coordinates approximately N15E05 (heliographic)  
  > "band 6 observations of NOAA active region number 12470 on 18 December 2015 from 19:11:41 - 20:09:59 UT when the active region was at approximately N15E05" (2.1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 6 (239 GHz, 1.25 mm)  
  > "The mean frequency was 239 GHz, or a wavelength of 1.25 mm." (2.1)
- frequencies and spectral setup: 4 spectral windows, each 2 GHz wide, centered on 230, 232, 246, 248 GHz  
  > "The band 6 observations were acquired in 4 spectral windows, each 2 GHz in bandwidth, centered on 230, 232, 246, and 248 GHz." (2.1)
- continuum bandwidth: _not stated_
- arrays: 12m array plus total power antennas (feathered)  
  > "The interferometric and TP mapping data were combined using “feathering" techniques as described by Shimojo et al. (2017)." (2.1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.4" x 0.9" (PA -76.7 deg)  
  > "has an angular resolution of $2.4"\times 0.9"$ (position angle -76.7$^\circ$)" (2.1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 149 pointings, 6.048 s each  
  > "formed from a mosaic of 149 pointings (Nyquist sampled), each pointing of duration 6.048s" (2.1)
- observing dates: 2015 December 18, 19:11:41-20:09:59 UT  
  > "on 18 December 2015 from 19:11:41 - 20:09:59 UT" (2.1)
- pi or archival as stated: _not stated_
- Line: Mg II h (IRIS) h doublet line (2803.5 Å)
- Other facility **IRIS**: Mg II h line raster maps, converted to radiation temperature  
  > "They are comprised of three dense ($0.35"$) 320-step very large raster scans" (2.2)
- Other facility **SDO/AIA**: differential emission measure for coronal contribution estimate  
  > "We estimated $\phi(T)$ using measurements by the Solar Dynamics Observatory Atmospheric Imaging Assembly" (3)
- External data: Model Mg II h2v formation heights 600-2000 km, peak 1400 km  
  > "forms in the middle chromosphere over a range of heights from 600 to 2,000 km with a peak around 1,400 km (Leenaarts et al., 2013b)" (3) [from Leenaarts et al. 2013b]
- External data: Synthetic 1.3 mm formation height peak 1150 km  
  > "suggest that the radiation mostly originates at similar heights, with a peak at 1150 km (Loukitcheva et al., 2017)" (3) [from Loukitcheva et al. 2017]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quiet Sun disk center scaled to 5900 K at 1.25 mm  
  > "the brightness temperature of the quiet Sun at the center of the solar disk is scaled to 5900 K (1.25 mm)" (2.1)
- flux scale uncertainty: ALMA ≈5% (total power); IRIS ~15%  
  > "These are expected to be calibrated in absolute terms to $\approx 5\%$ (see White et al. 2017)." (2.1); "absolute calibration of order 15%" (2.2)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Feathering of interferometric and total power maps  
  > "The interferometric and TP mapping data were combined using “feathering" techniques as described by Shimojo et al. (2017)." (2.1)
- smoothing: IRIS T_rad map convolved with Gaussian to ALMA resolution  
  > "was then convolved with a Gaussian kernel so that it had the same angular resolution as the corresponding ALMA map" (3)
- final beam: 2.4" x 0.9"  
  > "has an angular resolution of $2.4"\times 0.9"$ (position angle -76.7$^\circ$)" (2.1)
- final rms: _not stated_

### Inherited from earlier work

- Solar observing calibration procedures and TP calibration  
  > "Calibration of the TP measurements is described by White et al. (2017)" (2.1) [from White et al. 2017]
- Feathering technique  
  > "combined using “feathering" techniques as described by Shimojo et al. (2017)" (2.1) [from Shimojo et al. (2017)]
- Double-Gaussian line model  
  > "We used a nine-parameter double-Gaussian model (Schmit et al. 2015)" (2.2) [from Schmit et al. 2015]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (deferred to Shimojo/White)
- Feathering parameters
- Pixel masks for sunspot, quiet, plage regions
- Alignment offsets and how they were determined
- Formula for converting intensity to radiation temperature
- Linear fit method (regression type)

## Analysis recipe

1. **Fit IRIS Mg II h profiles**: Nine-parameter double-Gaussian fit; record h2r/h2v peak intensity and wavelength  
  > "We stored the model fits in separate arrays for the intensities and wavelengths for both the red and blue Mg II h2 peaks." (2.2)
   - software: MPFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Radiometric calibration to T_rad**: Convert DN/s to physical intensity (calibration version 004), then radiation temperature  
  > "We used the latest calibration values to date for this purpose (i.e. version “004”)." (2.2)
   - fitting: _not stated_
   - validation: _not stated_
3. **Co-register and match resolution**: Rotate ALMA map by solar position angle; median-fill failed IRIS pixels; interpolate to 0.4" grid; convolve to ALMA beam; correct offsets  
  > "the IRIS raster data were interpolated onto a uniform grid ($0.4"\times 0.4"$ pixels)" (3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Pixel-by-pixel correlation and linear fits**: Scatter plots of T_B vs T_rad, Pearson coefficient and linear slopes for all pixels and for sunspot/quiet/plage masks  
  > "A linear fit to the data yields a slope of $m=0.57$." (3)
   - fitting: linear fit  
  > "The solid line in Fig. 2 shows a linear fit to sunspot pixels (slope $m=0.4$); the dashed line shows the same for “quiet” regions pixels ($m=0.56$)" (Results and Discussion)
   - validation: Checked calibration, non-simultaneity and coronal contribution (<=2%)  
  > "found that $\Delta T_B$(1.25 mm) was no more than 2%" (3)

## Software

- **MPFIT** : Double-Gaussian fit of Mg II h profiles  
  > "based on MPFIT (Markwardt 2009) to model the line profile" (2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pearson correlation, all pixels | 0.78 | not stated | dimensionless | 4 | The Pearson correlation coefficient for all pixels is 0.78. |
| Slope, all pixels | 0.57 | not stated | dimensionless | 4 | A linear fit to the data yields a slope of $m=0.57$. |
| Slopes sunspot/quiet/plage | 0.4 / 0.56 / 0.66 | not stated | dimensionless | 4 | is 0.4 (sunspot), 0.56 (quiet regions), and 0.66 (plage regions) |
| Mean T_B (1.25 mm) | 7380 (range 5200-8700) | not stated | K | 4 | approximately 7380 K and 5200-8700 K, respectively |
| Mean T_rad (Mg II h2v) | 5470 (range 4500-6500) | not stated | K | 4 | approximately 5470 K and 4500-6500 K, respectively |

## Qualitative findings


## Claim tuples

- H: Do ALMA T_B and IRIS Mg II T_rad correlate? | E: Pixelwise comparison of matched-resolution maps | R: r=0.78, slope 0.57, T_B mean ~35% higher | F: Clear correlation with slope <1 and significant offset | **supported**
- H: Does the correlation vary by region? | E: Separate fits for sunspot, quiet, plage masks | R: Slopes 0.4, 0.56, 0.66 | F: Slope increases with hotter denser gas, possibly due to formation heights or source function coupling | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Time variability and coronal contribution cannot explain offsets and slopes  
  > "While time variability likely increases the scatter in the correlation between the two datasets, it cannot account for the offsets and slopes of the scatter plots." (3)
- How they decided it was enough: _not stated_
- Limitation (authors): Pixels are correlated on ALMA beam scale and not corrected for  
  > "we have not corrected for the fact that pixels are correlated on the scale of ALMA’s resolution" (3)
- Limitation (authors): Datasets not strictly simultaneous  
  > "the two data sets not obtained strictly simultaneously" (3)
- Caveat (inferred, ours): Fit uncertainties and correlated pixels not accounted for
- Caveat (inferred, ours): Region masks subjective
- Caveat (inferred, ours): Single active region, single epoch

## Reproducibility

- Data public (paper): ALMA science verification data cited by project code  
  > "ADS/JAO.ALMA #2011.0.00020.SV" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Feathering and calibration details (in Shimojo et al. 2017, White et al. 2017)
- Missing: Region masks
- Missing: Alignment procedure
- Missing: Fit method
- Data volume (inferred): tens of GB (solar SV mosaic plus TP)
- Score (inferred): 3/5, Public SV data and simple analysis, but processing details deferred to other papers and masks unspecified.
- Rediscovery candidate: no, Recipe depends on external papers for calibrated map and IRIS processing; masks unstated.

## Links

- Method: Shimojo et al. 2017 (Solar ALMA observing, feathering)
- Method: White et al. 2017 (TP calibration and solar commissioning)
- Method: Schmit et al. 2015 (Double-Gaussian line fitting)
- Related: ALMA solar science verification
- Related: IRIS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```
