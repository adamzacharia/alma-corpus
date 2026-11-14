# The solar chromosphere at millimetre and ultraviolet wavelengths. I. Radiation temperatures and a detailed comparison

`2019A&A...622A.150J` | Astronomy and Astrophysics 2019 | first author: Jafarzadeh, S. | arXiv: 1901.05763 | DOI: 10.1051/0004-6361/201834205

Card schema 1.0 | model claude-haiku-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How do radiation temperatures from ALMA band 6 (1.3 mm) compare with IRIS near- and far-UV chromospheric radiation temperatures across solar regions with different magnetic field strengths?  
  > "The present work provides distributions of the radiation temperature at various chromospheric heights sampled by the ALMA 1.3 mm passband and the IRIS observations at near- and far-UV wavelengths" (Introduction)
- Target **AR 12470 (solar active region, with surrounding plage and quasi-quiet areas)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: ALMA band 6 (centred at 239 GHz; 1.25 mm); the 1.3 mm sub-band is used for comparison  
  > "obtained in ALMA band 6 (centred at 239 GHz; 1.25 mm) on 18 December 2015" (Observations with ALMA)
- frequencies and spectral setup: Four spectral windows (SW0-SW3) of 2 GHz each, 128 channels per window, time domain mode; sub-band frequencies 248, 246, 232 and 230 GHz  
  > "Four spectral windows (sub bands), with a bandwidth of 2 GHz each, were recorded." (Observations with ALMA); "These correspond to frequencies 248, 246, 232, and 230 GHz, respectively." (Observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: Heterogeneous array of twenty-one 12 m and nine 7 m antennas, plus total power (TP) array in fast-scanning mode  
  > "The data was taken using a heterogeneous array configuration consisting of twenty-one 12 m and nine 7 m antennas." (Observations with ALMA); "full-disc total power maps were simultaneously obtained through single dish observations" (Observations with ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beam varies by about 7% between sub-bands; PSF used for IRIS convolution equivalent to a 2.2'' x 0.7'' Gaussian kernel  
  > "(1) convolved with the PSF of the ALMA map (i.e. equivalent to a $2.2\ensuremath{''}\times0.7\ensuremath{''}$ Gaussian kernel)" (Relationships between ALMA and IRIS)
- max recoverable scale: _not stated_
- sensitivity: Approximate 5% uncertainty in brightness temperature  
  > "The shaded areas around the histograms indicate the approximate 5% uncertainty in measurements of the brightness temperatures." (Observations with ALMA)
- time on source: Mosaic of 149 pointings, integration time 6.048 s per point, pointing separation 11.2 arcsec  
  > "The mosaic observations were performed with a pointing separation of 11.2 arcsec (corresponding to Nyquist sampling) and an integration time of 6.048 s for each point." (Observations with ALMA)
- observing dates: 18 December 2015, 19:39:25-20:02:34 UT (ALMA); IRIS scans 19:33:14-20:24:20 UT  
  > "on 18 December 2015 between 19:39:25–20:02:34 UT" (Observations with ALMA); "Three full IRIS scans were recorded between 19:33:14–20:24:20 UT" (IRIS observations)
- pi or archival as stated: Taken during the 6th solar commissioning science verification campaign  
  > "(in the 6th solar commissioning science verification campaign)" (Observations with ALMA)
- Line: Mg II k line (k2v, k2r, k3) (not stated)
- Line: Mg II h line (h2v, h2r, h3) (not stated)
- Line: C II 133.4 nm doublet, line core (not stated)
- Line: O I 135.6 nm, line core (optically thin; intensity only) (not stated)
- Line: Si IV 139.4 nm, line core (optically thin; intensity only) (not stated)
- Other facility **IRIS (Interface Region Imaging Spectrograph)**: UV spectra in 'very large dense 320-step raster' mode, 2 s exposure per step, FOV 105x175 arcsec  
  > "The ALMA observations were supported by the IRIS spacecraft in the “very large dense 320-step raster” mode with 2 s exposure time per step." (IRIS observations)
- Other facility **SDO (AIA, HMI)**: AIA 170 nm and 30.4 nm images for co-alignment; HMI continuum and magnetograms for magnetic-field masks  
  > "We use a combination of the AIA 170 nm and 30.4 nm images to perform a precise spatial alignment with the ALMA scan." (SDO images)
- External data: Comparison of ALMA band 6 at 1.25 mm brightness temperature with IRIS Mg ii h average of emission peaks; linear correlation coefficients from that study  
  > "who compared the brightness temperature of the ALMA’s band 6 at 1.25 mm and the radiation temperature of the average of the emission peaks of the IRIS Mg ii h." (Introduction) [from (cite: Bastian2017; Bastian2018)]
- External data: T_gas = 2 T_rad relationship for C II 133.4 nm from radiation MHD simulations  
  > "For a far-UV spectral line (i.e. C ii 133.4 nm), (cite: Rathore2015a) found a $T_{gas}=2\,T_{rad}$ relationship (from radiation MHD simulations)." (Introduction) [from (cite: Rathore2015a)]
- Simulation/model as data: 3D radiation MHD simulations from the Bifrost code, quiet and enhanced network regions, used to compare pixel-to-pixel gas temperature scatter  
  > "By inspecting the 3D radiation MHD simulations from the Bifrost code (cite: Gudiksen2011; Carlsson2016), we found a similar behaviour" (Relationships between ALMA and IRIS)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline optimised by the authors (separating sub-bands and spectral channels); Solar ALMA Pipeline (SoAP) output used  
  > "We have optimised the standard reduction pipeline by tuning various parameters, also separating the sub-bands and the spectral channels" (Observations with ALMA)
- casa version: not stated (standard CASA calibration, imaging and feathering steps)  
  > "included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (Observations with ALMA)
- pipeline version: SoAP first version, described in a forthcoming publication  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication" (Observations with ALMA)
- archive products used as is: _not stated_
- flux calibrator: Absolute brightness temperature scale set by TP (total power) maps  
  > "The TP maps are used to derive absolute brightness temperatures for the interferometric data" (Observations with ALMA)
- flux scale uncertainty: Approximately 5% (initial estimate; detailed error analysis deferred)  
  > "The calibrated ALMA data product as output of the pipeline (both, the official ALMA pipeline and SoAP) is the brightness temperature (with an uncertainty in the order of 5%)." (Analysis and results)
- self calibration: _not stated_

### Imaging

- task: not stated (CASA imaging with feathering of interferometric and TP data)  
  > "included standard CASA calibrations, imaging, and feathering steps" (Observations with ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: approximately 0.15 arcsec/pixel  
  > "with a sampling resolution of $\approx0.15$ arcsec/pixel" (Observations with ALMA)
- image size: approximately 140 x 140 arcsec mosaic  
  > "covering an area of ($\approx140\times140$) arcsec$^2$ on the Sun" (Observations with ALMA)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Feathering of 12 m and 7 m interferometric data with total power maps  
  > "The TP maps are used to derive absolute brightness temperatures for the interferometric data" (Observations with ALMA)
- smoothing: _not stated_
- final beam: Sub-band beam sizes vary by about 7%; PSF used in comparison 2.2'' x 0.7''  
  > "the beam size, which represents the spatial resolution, slightly varies between the four sub-bands, by about 7% from Sw0 to Sw3" (Observations with ALMA)
- final rms: _not stated_

### Inherited from earlier work

- Standard CASA calibration, imaging and feathering steps for the four sub-band brightness temperature maps  
  > "included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (Observations with ALMA) [from (cite: Shimojo2017)]
- Solar ALMA Pipeline (SoAP) reduction, first version not yet published  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication" (Observations with ALMA) [from (cite: Szydlarski2018)]
- Gaussian line-feature extraction of IRIS spectra with MOSiC  
  > "are computed with the MOSiC analysis tool (cite: Rezaei2017)." (IRIS observations) [from (cite: Rezaei2017)]
- Milne-Eddington Stokes inversion of HMI data with the VFISV code, for photospheric magnetic field strength  
  > "the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011)" (SDO images) [from (cite: Borrero2011)]
- IRIS radiometric calibration (version 4) for converting data numbers to intensity  
  > "These parameters were obtained using the latest version (version 4) of the IRIS radiometric calibration-routine" (Analysis and results) [from not stated]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and the imaging parameters (weighting, robust value, deconvolver, masking, cleaning threshold) used to make the sub-band maps and feathered TP combination
- Details of the SoAP reduction (tuning parameters, channel handling) which are deferred to an unpublished paper
- Calibration and processing of the IRIS raster, including the spatial/spectral binning details and the IRIS line-fit initial guesses and thresholds for accepting single vs double Gaussian fits
- Quantitative definition of the single-peak versus double-peak classification and the reduced chi-square threshold
- Exact coordinates and pointing of the mosaic, and the exact time-matching algorithm between ALMA and IRIS pixels
- Mapping from HMI Fe I magnetic strength to masks at the level of the 0.02-3.6 kG map resampling
- How the 2.2'' x 0.7'' PSF convolution was implemented and the resampling method

## Analysis recipe

1. **Obtain ALMA band 6 brightness temperature maps per sub-band**: Standard reduction with optimised pipeline separating sub-bands and channels, followed by CASA calibration, imaging and feathering with total power maps; 1.3 mm sub-band used for comparison  
  > "Extraction of the four different spectral windows (i.e. with ALMA identity numbers 5,7,9, and 11) included standard CASA calibrations, imaging, and feathering steps" (Observations with ALMA)
   - software: CASA, SoAP
   - parameter: Four sub-bands SW0-SW3 at 230, 232, 246, 248 GHz; 1.3 mm sub-band used  
  > "Among the four sub-bands, we use, in the following, the brightness temperature at 1.3 mm" (Observations with ALMA)
   - assumption: Brightness temperature taken as representative of gas temperature at the formation heights (LTE in Rayleigh-Jeans regime)  
  > "(ALMA’s $T_{rad}$ is a good representative of the gas temperature at the heights sampled by the mm line;" (Analysis and results)
   - fitting: _not stated_
   - validation: Sub-band differences judged within the 5% brightness temperature uncertainty  
  > "The small differences of the histograms lie within the measurement error of the brightness temperature by ALMA" (Observations with ALMA)
2. **Co-align IRIS and SDO images to ALMA**: Cross-correlation of common features; IRIS re-scaled and shifted/rotated; IRIS Mg ii k2v used against ALMA 1.3 mm; AIA 170 nm and 30.4 nm combined for SDO-ALMA alignment  
  > "they are transformed (spatially shifted and/or rotated) based on cross-correlation of common features" (Observations); "The IRIS raster images were spatially co-aligned with the ALMA scan by cross correlating the Mg ii k2v and ALMA 1.3 mm images." (IRIS observations)
   - fitting: _not stated_
   - validation: Cross-check of IRIS Mg ii 283.2 nm raster against SDO/HMI continuum  
  > "we verified the alignments by means of a cross correlation of common features between the SDO/HMI continuum" (IRIS observations)
3. **Extract line features from IRIS spectra**: Per-pixel Gaussian fits of increasing complexity (single then multiple Gaussians), each fit seeding the next; pixels without clear single or double peaks excluded  
  > "the various line features are determined at each pixel using a Gaussian fit, for which the degree of freedom gradually increases." (IRIS observations)
   - software: MOSiC
   - parameter: Goodness of fit by reduced chi-square  
  > "The goodness of the fits at each step is evaluated by means of reduced chi-square statistics (cite: Bevington1992)." (IRIS observations)
   - fitting: Gaussian fits per pixel, multiple Gaussians if single fit fails; reduced chi-square  
  > "It begins with a single Gaussian fit, then a higher level of multiple Gaussian (with a larger number of free parameters), if the previous one fails." (IRIS observations)
   - validation: Only clear single or double peaked profiles retained  
  > "Only pixels with clear single and double peaked profiles are included in further analysis" (IRIS observations)
4. **Convert IRIS intensities to radiation temperatures**: Intensity from data numbers using photon count per DN, effective area, pixel sizes, exposure time and slit width; radiation temperature from inverting the Planck function  
  > "We calculate the near- and far-UV radiation temperature $T_{rad}$ in the solar chromosphere at a given wavelength $\lambda$ by solving the Planck function" (Analysis and results)
   - software: IRIS radiometric calibration routine (version 4)
   - parameter: Intensity calibration uncertainty about 15%; radiation temperature uncertainty 2%  
  > "We note that, however, the radiation temperatures are estimated with an uncertainty of 2% (due to the exponential of the Planck function)." (Analysis and results)
   - assumption: Radiation temperature of optically thin lines (O i, Si iv) not computed as not meaningful  
  > "We remind the reader that radiation temperature of the optically thin lines (i.e. O i and Si iv) are meaningless" (Analysis and results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Define magnetic-field regions**: Partition FOV by HMI-derived B-map thresholds into umbra, penumbra and pores, plage, quasi-quiet, and sunspot and pores  
  > "Five areas are chosen: $B\geq2$ kG comprising only the umbra" (Definition of regions)
   - software: VFISV
   - parameter: B thresholds 2 kG, 0.8 kG, 0.2 kG, 0.1 kG  
  > "0.8 kG$>B\geq0.2$ kG defining the plage areas, and $B<0.1$ kG to represent the quasi-quiet regions." (Definition of regions)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare radiation temperature distributions per region**: Histograms, means, standard deviations and ranges of T_rad per region and line feature  
  > "The ranges, means, and standard deviations of the radiation temperature distributions of the different lines, and for the various areas, are summarised in Table" (Radiation temperature distributions)
   - fitting: _not stated_
   - validation: _not stated_
7. **Pixel-to-pixel comparison of ALMA and IRIS**: IRIS convolved with ALMA PSF and resampled to ALMA pixels; only pixels within a maximum observing-time difference kept (2 min and 0.5 min); scatter plots with density colouring and y=x line  
  > "which have a maximum observing-time difference of two minutes with their corresponding pixels in the ALMA map" (Relationships between ALMA and IRIS)
   - parameter: Time-difference masks 2 min (28% of FOV) and 0.5 min (about 8% of FOV)  
  > "Although this selection limits us to only 28% of the entire FOV" (Relationships between ALMA and IRIS)
   - assumption: Temperature changes on time scales longer than 2 min are negligible for the comparison  
  > "the one-to-one comparison is free from temperature changes happening on time scales longer than 2 min." (Relationships between ALMA and IRIS)
   - fitting: Linear regression slope m; Pearson r; Spearman rho  
  > "Furthermore, the linear regression coefficient of the linear fit $m$, which measures the steepness of a linear relationship, is calculated." (Relationships between ALMA and IRIS)
   - validation: Spearman rank correlation as check for non-linear relationships  
  > "we also calculate the Spearman’s rank correlation coefficient $\rho$, which better models non-linear relationships and is not sensitive to outliers." (Relationships between ALMA and IRIS)
8. **Test distribution agreement**: Kolmogorov-Smirnov test on cumulative distribution functions of T_rad  
  > "we also employ the Kolmogorov–Smirnov (K-S) test." (Agreements between temperature distributions)
   - parameter: d = maximum CDF difference, between 0 and 1  
  > "The $d$ parameter varies between 0 and 1, the former indicates the best match and the latter means no agreement at all." (Agreements between temperature distributions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Standard calibration, imaging and feathering of ALMA sub-band maps  
  > "included standard CASA calibrations, imaging, and feathering steps" (Observations with ALMA)
- **SoAP (Solar ALMA Pipeline)** first version (not stated): Solar reduction of ALMA data with sub-band and channel separation  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication" (Observations with ALMA)
- **MOSiC** : Gaussian line-feature extraction of IRIS spectra and determination of radiation temperatures  
  > "are computed with the MOSiC analysis tool (cite: Rezaei2017)." (IRIS observations)
- **VFISV** : Milne-Eddington Stokes inversion of HMI data for magnetic field strength  
  > "the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011)" (SDO images)
- **IRIS radiometric calibration routine** version 4: Parameters for converting IRIS data numbers to intensity  
  > "These parameters were obtained using the latest version (version 4) of the IRIS radiometric calibration-routine" (Analysis and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3 mm brightness temperature mean over full FOV | 6.6 | 0.5 (standard deviation) | kK | 6 | with an average and standard variation of 6.6 kK and 0.5 kK, respectively. |
| ALMA 1.3 mm brightness temperature range over full FOV | 4.6-8.1 | not stated | kK | 6 | The brightness temperature at 1.3 mm varies between 4.6–8.1 kK in the entire FOV |
| ALMA 1.3 mm mean brightness temperature in umbra | 5.6 | 0.4 (standard deviation of distribution) | kK | 6 | The ALMA Band 6 represents a mean brightness temperature of $5.6\pm0.4$ kK in the umbra |
| ALMA 1.3 mm mean brightness temperature in quasi-quiet regions | 6.5 | 0.4 (standard deviation of distribution) | kK | 6 | That is $6.5\pm0.4$ kK in the quasi-quiet regions in the immediate vicinity of the sunspot. |
| ALMA 1.3 mm mean brightness temperature in plage | 7.0 | 0.4 (standard deviation of distribution) | kK | 6 | The ALMA’s band 6 poses its highest brightness temperature in plage areas (with a mean value of $7.0\pm0.4$ kK). |
| IRIS Mg II line feature mean radiation temperatures (all regions) | 4.2-5.7 range of lowest mean T_rad among lines | not stated | kK | 6 | the IRIS magnesium lines represent the lowest mean radiation temperature in the order of 4.2–5.7 kK |
| Difference in umbral mean T_rad: C II line core minus ALMA 1.3 mm | 1 | not stated | kK | 6 | with an exception in the umbra, where the latter is, on average, hotter by 1 kK. |
| Pearson r for majority of T_rad-T_rad scatter plots (excluding umbra) | 0.5 < r < 0.9 | not stated | dimensionless | 7 | show a moderate-to-good positive linear correlation (i.e. $0.5 < r < 0.9$). |
| Fraction of FOV retained for 2 min time-difference comparison | 28 | not stated | percent | 7 | Although this selection limits us to only 28% of the entire FOV |
| Radiation temperature uncertainty from Planck inversion | 2 | not stated | percent | 4 | We note that, however, the radiation temperatures are estimated with an uncertainty of 2% (due to the exponential of the Planck function). |

## Qualitative findings

- Spectral splitting of the ALMA band 6 data into sub-bands gives slightly higher spatial resolution than standard spectral averaging  
  > "It was revealed that spectral splitting of the ALMA observations in a particular Band (here, in Band 6) results in a slightly higher spatial resolution." (Summary and conclusions)
- Plage has the highest and umbra the lowest radiation temperatures in all channels  
  > "In plage areas, we found the highest radiation temperatures in all spectral channels." (Summary and conclusions)
- Only the C II line core agrees with ALMA in distribution (K-S test)  
  > "It is evident that only $T_{rad}$ distribution of the C ii line has, to some extent, agreement with that of the ALMA 1.3 mm." (Agreements between temperature distributions)

## Claim tuples

- H: Radiation temperatures from ALMA 1.3 mm correlate with those from IRIS UV line features across solar regions | E: Pixel-to-pixel scatter plots of IRIS radiation temperatures (convolved to ALMA PSF) against ALMA brightness temperature, time-matched within 2 min, for six regions | R: Moderate-to-good positive linear correlation (0.5 < r < 0.9) for most regions except the umbra; Spearman coefficients also provided | F: Spatial variation of UV radiation temperatures is similar to that of ALMA 1.3 mm in most regions | **supported**
- H: ALMA and IRIS radiation temperatures agree in value (offset from y=x) | E: Scatter plots and CDF comparison with K-S test for all pixels and per region | R: Offsets from the y=x line for most pairs; C II line core is the exception and only C II matches ALMA in distribution | F: Non-LTE source function decoupling and different formation heights cause offsets, so UV radiation temperatures do not equal gas temperatures | **partially**
- H: Observing-time differences affect the ALMA-IRIS comparison | E: Repeated the analysis with maximum 0.5 min time difference and compared with 2 min results | R: Larger Pearson correlations in most cases but smaller slopes; offsets not significantly changed | F: Accounting for time differences is important for one-to-one comparisons | **supported**
- H: Radiation temperatures vary with underlying magnetic field strength | E: Histograms and means of ALMA and IRIS T_rad for umbra, penumbra and pores, plage, quasi-quiet and combined regions | R: ALMA mean 5.6 kK in umbra, 7.0 kK in plage, 6.5 kK in quasi-quiet regions | F: Umbra has the lowest and plage the highest radiation temperatures, attributed to Wilson depression and reduced heating | **supported**

## Reasoning

- Why this data: ALMA band 6 is complementary to UV diagnostics because the source function varies linearly with temperature in the Rayleigh-Jeans limit under LTE  
  > "Observations at millimetre wavelengths are complementary to the UV diagnostics in the sense that the source function varies linearly with temperature." (Introduction)
- Why this method: Partitioning the FOV into regions by magnetic field strength is the conventional approach to study magnetic dependence  
  > "The conventional approach to study such dependency is to partition the FOV into regions with distinct amounts of magnetic fields." (Definition of regions)
- Alternative: Averaging ALMA sub-bands (as commonly done) rejected because it loses height information and smears structures  
  > "averaging these sub-bands (as has been commonly done), results in losing the height information and can lead to spatial smearing" (Observations with ALMA)
- Alternative: Radiation temperature of optically thin O I and Si IV lines not computed  
  > "Hence, their radiation temperatures are not calculated here." (Analysis and results)
- How they decided it was enough: Time-difference thresholds of 2 min and 0.5 min were applied, retaining 28% and about 8% of FOV respectively  
  > "we also investigate the relationships for pixels with a more conservative time difference of maximum 0.5 min" (Relationships between ALMA and IRIS)
- Limitation (authors): Absolute ALMA temperature error and calibration deferred to a forthcoming paper; 5% initial estimate  
  > "A detailed discussion on the error of the temperature measurements by ALMA and of the calibrations (and to what degree the initial 5% estimation is realistic) are subject of a forthcoming paper." (Observations with ALMA)
- Limitation (authors): Non-linear relationships cannot be completely ruled out for individual pixels  
  > "We note that we cannot completely rule out non-linear relationships between the radiation temperatures" (Relationships between ALMA and IRIS)
- Limitation (authors): Umbra comparison based on very few data points after time-difference selection  
  > "The very small correlation coefficients we found in the umbra could partly be due to a large uncertainty introduced by the very few data points" (Summary and conclusions)
- Caveat (inferred, ours): The SoAP reduction underlying the ALMA maps is not described in this paper, so the ALMA brightness temperatures cannot be independently regenerated from the text.
- Caveat (inferred, ours): Mg II and C II radiation temperatures are non-LTE and differ from gas temperatures, so the comparison with LTE ALMA values is interpretive.
- Caveat (inferred, ours): Time-matched subsets are small (28% and about 8% of FOV) and the umbra subset is tiny, weakening the correlation statistics there.
- Caveat (inferred, ours): Formation height differences between sub-bands and lines are invoked but not quantified.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA data linked via project 2011.0.00020.SV; the archive manifest lists no linked projects  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00020.SV." (Acknowledgements)
- Code: _not stated_
- Missing: SoAP reduction parameters and the unpublished SoAP description
- Missing: CASA version and full imaging parameters for the sub-band maps and TP feathering
- Missing: IRIS MOSiC fitting configuration and pixel-selection thresholds
- Missing: Exact time-matching procedure and co-alignment transforms
- Missing: Region mask generation details from HMI B-maps
- Data volume (inferred): Order of a few GB (ALMA mosaic of 149 pointings with 4 spectral windows of 128 channels, plus IRIS 320-step rasters and SDO images); inferred, not stated.
- Score (inferred): 3/5, Data are archival-style ALMA plus IRIS and SDO, but the key ALMA reduction (SoAP) is unpublished and imaging parameters are missing, so a reproduction would be partial.
- Rediscovery candidate: no, Data public status is not stated, the ALMA reduction recipe is incomplete (SoAP unpublished, CASA version and imaging parameters missing), so the main numbers cannot be reliably redone from the text.

## Links

- Method: (cite: Shimojo2017) (Standard CASA calibration, imaging and feathering of the ALMA solar maps)
- Method: (cite: Rezaei2017) (MOSiC tool for IRIS line-feature extraction)
- Method: (cite: Borrero2011) (VFISV inversion of HMI data)
- Companion: (cite: Szydlarski2018) (Forthcoming description of the SoAP reduction used for the ALMA data)
- Companion: (cite: Bastian2017) (Earlier ALMA and IRIS comparison of the same data set)
- Companion: (cite: Bastian2018) (Follow-up ALMA and IRIS comparison of Mg ii h brightness temperatures)
- Related: ALMA solar commissioning science verification campaign
- Related: IRIS spacecraft observations
- Related: SDO (AIA and HMI)

## Checks

```json
{
 "quotes": 95,
 "quotes_ok": 95,
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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 100,
  "stated": 69,
  "rate": 0.69
 },
 "evidence_ok": true
}
```

## Figures

- **Figure 1** (channel_maps, 4 panel(s), data): ALMA band 6 brightness temperature (radiation temperature) maps of the solar field in four sub-bands at 1.209, 1.219, 1.292 and 1.303 mm, with circles marking structures with different temperature distributions.
  - axes: x: arcsec position [arcsec]; y: arcsec position [arcsec]; colour: T_rad radiation temperature [kK]
  - supports step 1
  - read off the plot: approx. colour scale 4.5 to 8 kK; approx. field of view about 143 by 139 arcsec; approx. sub-band wavelengths 1.209, 1.219, 1.292, 1.303 mm
- **Figure 2** (histogram, 1 panel(s), data): Normalized histograms of brightness temperature over the entire field of view for the four ALMA sub-band images shown in Figure 1, with shaded 5% uncertainty areas.
  - axes: x: brightness temperature [not labelled]; y: normalized occurrence frequency [normalized to maximum]
  - supports step 1
  - validation: Shows that the four sub-band distributions are similar in shape and offset, with uncertainty shading.
  - read off the plot: approx. peak normalized occurrence at 1.0 for all four sub-bands; approx. distributions span about 4.5 to 7.5 kK in x-axis ticks
- **Figure 3** (moment_map, 9 panel(s), data): Radiation temperature maps of the ALMA 1.3 mm continuum (panel a) and of IRIS line features: C II 133.4 nm line core (c), Mg II k blue peak, line core and red peak (d-f), and Mg II h blue peak, line core and red peak (g-i); panel b shows Si IV line core, with blue pixels where line features could not be determined.
  - axes: x: position [arcsec]; y: position [arcsec]; colour: T_rad radiation temperature [kK]
  - supports step 2
  - read off the plot: approx. Mg II k and h radiation temperature colour scales about 4.5 to 6.5 kK; approx. field of view about 97 by 129 arcsec
- **Figure 6** (histogram, 6 panel(s), data): Distributions of ALMA 1.3 mm radiation temperature (filled grey) and of IRIS Mg II k blue peak, line core and red peak, for the entire field of view and for sunspot and pores, umbra, penumbra and pores, plage and quiet regions.
  - axes: x: radiation temperature T_rad [kK]; y: normalized frequency [normalized to maximum]
  - supports step 6
  - validation: Compares radiation temperature distributions of ALMA and IRIS Mg II k per magnetic-field region.
  - read off the plot: approx. entire FOV ALMA peak near 6.8 kK; approx. entire FOV IRIS Mg II k3 peak near 5.2 kK; approx. umbra ALMA distribution around 5 to 6.5 kK; approx. quiet regions ALMA peak near 6.6 kK; approx. plage ALMA peak near 7.0 kK
  - reproduction target
- **Figure 7** (histogram, 6 panel(s), data): Same as Figure 6 but for the IRIS Mg II h line features (h2v, h3, h2r) and the IRIS C II 133.4 nm line core, compared with ALMA 1.3 mm, per magnetic-field region.
  - axes: x: radiation temperature T_rad [kK]; y: normalized frequency [normalized to maximum]
  - supports step 6
  - validation: Compares radiation temperature distributions of ALMA and IRIS Mg II h and C II per magnetic-field region.
  - read off the plot: approx. entire FOV C II core peak near 6.5 kK; approx. entire FOV ALMA peak near 6.8 kK; approx. umbra C II core peak near 6.5 kK; approx. quiet regions Mg II h3 peak near 4.8 kK
  - reproduction target
- **Figure 8** (scatter_or_relation, 6 panel(s), data): Mean radiation temperatures (red dots) retrieved from ALMA 1.3 mm and from IRIS Mg II k, Mg II h and C II core features, for each magnetic-field region, with standard deviation error bars.
  - axes: y: mean radiation temperature [kK]; x: diagnostic (1.3 mm, C II core, Mg II k2/k3/k2, Mg II h2/h3/h2) [not labelled]
  - supports step 6
  - validation: Compares mean radiation temperatures across ALMA and IRIS diagnostics per region with standard deviation error bars.
  - read off the plot: approx. entire FOV ALMA mean 6.6 kK; approx. entire FOV C II core mean 6.6 kK; approx. entire FOV Mg II k3 mean 5.3 kK; approx. umbra ALMA mean 5.6 kK; approx. plage ALMA mean 7.0 kK
  - reproduction target
- **Figure 10** (scatter_or_relation, 9 panel(s), data): Pixel-to-pixel density scatter plots of IRIS radiation temperatures (Mg II k3, h3, k2r, h2r, and Si IV and O I core intensities) against ALMA 1.3 mm radiation temperature for pixels in the sunspot and small pores, with slope m, Pearson r and Spearman rho.
  - axes: x: ALMA 1.3 mm T_rad [kK]; y: IRIS T_rad or line-core intensity [kK; erg s-1 cm-3 sr-1]; colour: pixel density [not labelled]
  - supports step 7
  - validation: Pixel-to-pixel correlation between ALMA and IRIS diagnostics within sunspot and pores.
  - read off the plot: approx. Mg II k2v slope m 0.49 with r 0.81; approx. Mg II k3 slope m 0.27 with r 0.77; approx. C II core slope m 0.23 with r 0.70 in sunspot and pores
- **Figure 11** (scatter_or_relation, 5 panel(s), data): Pixel-to-pixel scatter plots of IRIS Mg II k3, h3, C II core and O I core against ALMA 1.3 mm radiation temperature for pixels in the umbral region, with fitted slope, r and rho.
  - axes: x: ALMA 1.3 mm T_rad [kK]; y: IRIS T_rad or line-core intensity [kK; erg s-1 cm-3 sr-1]; colour: pixel density [not labelled]
  - supports step 7
  - validation: Pixel-to-pixel correlation between ALMA and IRIS diagnostics in the umbra, showing weak correlation.
  - read off the plot: approx. C II core T_rad about 6.4 to 6.5 kK across ALMA 4.8 to 5.9 kK; approx. Mg II k3 T_rad about 4.6 to 5.3 kK
- **Figure 12** (scatter_or_relation, 9 panel(s), data): Pixel-to-pixel density scatter plots of IRIS Mg II k3, h3, k2r, h2r and Si IV and O I core intensities against ALMA 1.3 mm radiation temperature for pixels in the penumbra and small pores.
  - axes: x: ALMA 1.3 mm T_rad [kK]; y: IRIS T_rad or line-core intensity [kK; erg s-1 cm-3 sr-1]; colour: pixel density [not labelled]
  - supports step 7
  - validation: Pixel-to-pixel correlation between ALMA and IRIS diagnostics in penumbra and pores.
  - read off the plot: approx. Mg II k2r slope m 0.47 with r 0.83; approx. C II core slope m 0.54 with r 0.89
- **Figure 13** (scatter_or_relation, 9 panel(s), data): Pixel-to-pixel density scatter plots of IRIS Mg II k3, h3, k2r, h2r and Si IV and O I core intensities against ALMA 1.3 mm radiation temperature for plage pixels.
  - axes: x: ALMA 1.3 mm T_rad [kK]; y: IRIS T_rad or line-core intensity [kK; erg s-1 cm-3 sr-1]; colour: pixel density [not labelled]
  - supports step 7
  - validation: Pixel-to-pixel correlation between ALMA and IRIS diagnostics in plage areas.
  - read off the plot: approx. C II core slope m 0.58 with r 0.83 in plage; approx. Mg II k2r slope m 0.53 with r 0.80 in plage
- **Figure 14** (scatter_or_relation, 9 panel(s), data): Pixel-to-pixel density scatter plots of IRIS Mg II k3, h3, k2r, h2r and Si IV and O I core intensities against ALMA 1.3 mm radiation temperature for quasi-quiet region pixels.
  - axes: x: ALMA 1.3 mm T_rad [kK]; y: IRIS T_rad or line-core intensity [kK; erg s-1 cm-3 sr-1]; colour: pixel density [not labelled]
  - supports step 7
  - validation: Pixel-to-pixel correlation between ALMA and IRIS diagnostics in quasi-quiet regions, with weaker slopes and uncertainties.
  - read off the plot: approx. C II core slope m 0.38 with r 0.71 in quasi-quiet regions; approx. Mg II k2r slope m 0.51 with r 0.69
- **Figure 15** (scatter_or_relation, 6 panel(s), data): Pearson correlation coefficients r (red, left axis) and regression slopes m (blue, right axis) between UV radiation temperatures and ALMA 1.3 mm per solar region, for pixel sets with maximum time differences of 2 and 0.5 min.
  - axes: y: Pearson correlation coefficient r [dimensionless]; y: regression slope m [dimensionless]; x: UV diagnostic (C II, Mg II k and h features) [not labelled]
  - supports step 7
  - validation: Checks sensitivity of pixel-to-pixel correlation to the maximum observing time difference between ALMA and IRIS.
  - read off the plot: approx. entire FOV C II r about 0.74; approx. sunspot and pores Mg II k r about 0.93; approx. umbra r about 0.55 for first diagnostic; approx. plage r about 0.83 for first diagnostic
- **Figure 16** (model_vs_data, 1 panel(s), data): Cumulative distribution functions of radiation temperature for the entire field of view for ALMA 1.3 mm and each IRIS UV diagnostic, with Kolmogorov-Smirnov statistics d for each channel against ALMA.
  - axes: x: radiation temperature T_rad [kK]; y: cumulative distribution [dimensionless]
  - supports step 8
  - validation: Tests distribution agreement between ALMA and each IRIS diagnostic via Kolmogorov-Smirnov statistic d.
  - read off the plot: approx. ALMA CDF median near 6.9 kK; approx. Mg II k3 KS d 0.92; approx. C II core KS d 0.26
  - reproduction target
