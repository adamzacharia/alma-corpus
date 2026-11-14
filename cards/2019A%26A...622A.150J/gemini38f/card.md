# The solar chromosphere at millimetre and ultraviolet wavelengths. I. Radiation temperatures and a detailed comparison

`2019A&A...622A.150J` | Astronomy and Astrophysics 2019 | first author: Jafarzadeh, S. | arXiv: 1901.05763 | DOI: 10.1051/0004-6361/201834205

Card schema 1.0 | model gemini-3.8-flash | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How do radiation temperature distributions and small-scale features across different solar magnetic regions compare between ALMA 1.3 mm observations and IRIS near/far-UV diagnostics in the solar chromosphere?  
  > "The present work provides distributions of the radiation temperature at various chromospheric heights sampled by the ALMA 1.3 mm passband and the IRIS observations at near- and far-UV wavelengths" (1 Introduction)
- Target **AR 12470**: coordinates close to the solar disc-center (with cosine of heliocentric angle ≈0.97)  
  > "This study is primarily based on observations of the solar active region AR 12470 by ALMA on 18 December 2015." (2 Observations); "The field of view (FOV) includes the leading sunspot of the active region AR 12470 surrounded by plages and quasi-quiet areas, close to the solar disc-center (with cosine of heliocentric angle \approx0.97)." (2.1 Observations with ALMA); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 6 (centred at 239 GHz; 1.25 mm)  
  > "A mosaic image with 149 points, covering an area of (\approx140\times140) arcsec^2 on the Sun (with a sampling resolution of \approx0.15 arcsec/pixel), was obtained in ALMA band 6 (centred at 239 GHz; 1.25 mm)" (2.1 Observations with ALMA)
- frequencies and spectral setup: Four spectral windows: 248 GHz (1.209 mm), 246 GHz (1.219 mm), 232 GHz (1.292 mm), and 230 GHz (1.303 mm); 128 channels each in TDM  
  > "Four spectral windows (sub bands), with a bandwidth of 2 GHz each, were recorded. Each spectral window (SW) includes 128 channels (with time domain mode (TDM) as the spectral setup)." (2.1 Observations with ALMA); "Thus, brightness temperature maps of the four sub bands (i.e. SW3, SW2, SW1, and SW0), corresponding to wavelengths 1.209, 1.219, 1.292, and 1.303 mm, respectively, were obtained. These correspond to frequencies 248, 246, 232, and 230 GHz, respectively." (2.1 Observations with ALMA)
- continuum bandwidth: 2 GHz per spectral window (4 spectral windows)  
  > "Four spectral windows (sub bands), with a bandwidth of 2 GHz each, were recorded." (2.1 Observations with ALMA)
- arrays: Heterogeneous array of 12 m and 7 m antennas, plus Total Power (TP) array  
  > "The data was taken using a heterogeneous array configuration consisting of twenty-one 12 m and nine 7 m antennas." (2.1 Observations with ALMA); "In addition, full-disc total power maps were simultaneously obtained through single dish observations (i.e. with the total power (TP)-array in fast-scanning mode)." (2.1 Observations with ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 6.048 s per point for 149 mosaic points  
  > "The mosaic observations were performed with a pointing separation of 11.2 arcsec (corresponding to Nyquist sampling) and an integration time of 6.048 s for each point." (2.1 Observations with ALMA)
- observing dates: 18 December 2015 between 19:39:25–20:02:34 UT  
  > "obtained in ALMA band 6 (centred at 239 GHz; 1.25 mm) on 18 December 2015 between 19:39:25–20:02:34 UT (in the 6th solar commissioning science verification campaign)." (2.1 Observations with ALMA)
- pi or archival as stated: Science verification  
  > "on 18 December 2015 between 19:39:25–20:02:34 UT (in the 6th solar commissioning science verification campaign)." (2.1 Observations with ALMA)
- Other facility **IRIS**: Near- and far-UV slit-jaw/raster spectroscopy targeting Mg II h & k, C II 133.4 nm, O I 135.6 nm, and Si IV 139.4/140.3 nm  
  > "The ALMA observations were supported by the IRIS spacecraft in the “very large dense 320-step raster” mode with 2 s exposure time per step." (2.2 IRIS observations); "The IRIS spectrograph covers a wide wavelength range in the UV, which particularly includes the C ii 133.4 nm doublet, O i 135.6 nm, the Si iv doublet (at 139.4 nm and 140.3 nm), Mg ii k 279.6 nm, and Mg ii h 280.4 nm." (2.2 IRIS observations)
- Other facility **SDO**: AIA 170 nm and 30.4 nm imaging for co-alignment; HMI continuum and full Stokes Milne-Eddington inversions (VFISV) for photospheric magnetic field strength  
  > "Images from SDO/AIA (cite: Lemen2012) and SDO/HMI (cite: Schou2012), corresponding to the ALMA scan, were also collected." (2.4 SDO images); "We use a combination of the AIA 170 nm and 30.4 nm images to perform a precise spatial alignment with the ALMA scan." (2.4 SDO images); "We also use the results of the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011) to obtain the photospheric magnetic field strength." (2.4 SDO images)
- Simulation/model as data: 3D radiation MHD simulations from the Bifrost code inspected to interpret height differences and scatter in temperature relations  
  > "By inspecting the 3D radiation MHD simulations from the Bifrost code (cite: Gudiksen2011; Carlsson2016), we found a similar behaviour in the solar chromosphere (in quiet and enhanced network regions)." (3.2 Relationships between ALMA and IRIS)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: approximate 5%  
  > "The shaded areas around the histograms indicate the approximate 5% uncertainty in measurements of the brightness temperatures." (2.1 Observations with ALMA); "The calibrated ALMA data product as output of the pipeline (both, the official ALMA pipeline and SoAP) is the brightness temperature (with an uncertainty in the order of 5%)." (3 Analysis and results)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: ≈0.15 arcsec/pixel  
  > "covering an area of (\approx140\times140) arcsec^2 on the Sun (with a sampling resolution of \approx0.15 arcsec/pixel)" (2.1 Observations with ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Feathering interferometric (12 m + 7 m) maps with single-dish Total Power maps  
  > "The TP maps are used to derive absolute brightness temperatures for the interferometric data (cite: Shimojo2017; White2017)." (2.1 Observations with ALMA); "Extraction of the four different spectral windows (i.e. with ALMA identity numbers 5,7,9, and 11) included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (2.1 Observations with ALMA)
- smoothing: _not stated_
- final beam: 2.2'' × 0.7''  
  > "Prior to the comparison, the IRIS images are (1) convolved with the PSF of the ALMA map (i.e. equivalent to a 2.2''\times0.7'' Gaussian kernel)" (3.2 Relationships between ALMA and IRIS)
- final rms: _not stated_

### Inherited from earlier work

- CASA calibrations, imaging, and feathering steps  
  > "Extraction of the four different spectral windows (i.e. with ALMA identity numbers 5,7,9, and 11) included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (2.1 Observations with ALMA) [from (cite: Shimojo2017)]
- Stokes inversion of HMI data using the VFISV code  
  > "We also use the results of the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011) to obtain the photospheric magnetic field strength." (2.4 SDO images) [from (cite: Borrero2011)]
- Fitting IRIS spectral line features using MOSiC  
  > "are computed with the MOSiC analysis tool (cite: Rezaei2017)." (2.2 IRIS observations) [from (cite: Rezaei2017)]

### Not stated but needed to reproduce (our reading)

- CASA tclean/imaging weighting scheme and robust parameter
- feather task parameters (sdfactor, effdishdiam)
- Exact SoAP pipeline parameter tuning details
- Absolute coordinates/pointing center of the ALMA mosaic

## Analysis recipe

1. **Calibrate, image, separate sub-bands, and feather ALMA Band 6 data**: Process ALMA Band 6 interferometric and fast-scanning TP data with CASA and Solar ALMA Pipeline (SoAP), separating the four individual 2 GHz spectral windows and feathering with TP data to create absolute brightness temperature maps.  
  > "We have optimised the standard reduction pipeline by tuning various parameters, also separating the sub-bands and the spectral channels (instead of a spectral integration, which is done by default in the standard pipeline)." (2.1 Observations with ALMA); "Extraction of the four different spectral windows (i.e. with ALMA identity numbers 5,7,9, and 11) included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (2.1 Observations with ALMA)
   - software: CASA, SoAP
   - parameter: 4 sub-bands: SW3 (248 GHz, 1.209 mm), SW2 (246 GHz, 1.219 mm), SW1 (232 GHz, 1.292 mm), SW0 (230 GHz, 1.303 mm)  
  > "Thus, brightness temperature maps of the four sub bands (i.e. SW3, SW2, SW1, and SW0), corresponding to wavelengths 1.209, 1.219, 1.292, and 1.303 mm, respectively, were obtained." (2.1 Observations with ALMA)
   - assumption: ALMA 1.3 mm brightness temperature is formed in LTE, representing local gas temperature around tau=1.  
  > "With the millimetre wavelengths being in the Rayleigh-Jeans limit, the temperature can be simply measured under the assumption of local thermodynamic equilibrium (LTE)" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared small-scale structural appearance across sub-bands with beam sizes to ensure differences reflect formation height rather than calibration artifacts.  
  > "We therefore argue that the different appearances of the small-scale structures are mostly due to the slightly different formation heights for the sub bands although the small differences in the spatial resolution of the four sub-bands may contribute to some extent" (2.1 Observations with ALMA)
2. **Extract IRIS line parameters and calculate radiation temperatures**: Fit IRIS spectra with Gaussian models using MOSiC, extract peak and core intensities, convert data numbers to physical intensity using IRIS radiometric calibration routine v4, and invert the Planck function to calculate Trad.  
  > "the various line features are determined at each pixel using a Gaussian fit, for which the degree of freedom gradually increases." (2.2 IRIS observations); "We calculate the near- and far-UV radiation temperature T_rad in the solar chromosphere at a given wavelength \lambda by solving the Planck function" (3 Analysis and results); "These parameters were obtained using the latest version (version 4) of the IRIS radiometric calibration-routine (with an uncertainty of about 15%)." (3 Analysis and results)
   - software: MOSiC
   - parameter: Mg II k2v, k3, k2r; Mg II h2v, h3, h2r; C II 133.4 nm line core  
  > "The line features, namely, the blue and red emission peaks and core of the magnesium k line (i.e. Mg ii k2v, Mg ii k2r, and Mg ii k3, respectively) and of the magnesium h line (i.e. Mg ii h2v, Mg ii h2r, and Mg ii h3) as well as the line cores of O i 135.6 nm, C ii 133.4 nm and Si iv 139.4 nm, are computed with the MOSiC analysis tool" (2.2 IRIS observations)
   - assumption: UV diagnostics are formed under non-LTE conditions; Trad gives information on source function around optical depth unity for optically thick lines.  
  > "For an optically thick line, the radiation temperature gives information on the source function around optical depth unity. In LTE, this translates directly to the gas temperature while in non-LTE the source function is typically more or less decoupled and typically lower than the Planck function." (1 Introduction)
   - fitting: Sequential Gaussian fitting with increasing degrees of freedom evaluated by reduced chi-square.  
  > "It begins with a single Gaussian fit, then a higher level of multiple Gaussian (with a larger number of free parameters), if the previous one fails. Each fit provides an initial guess for the next one. The goodness of the fits at each step is evaluated by means of reduced chi-square statistics" (2.2 IRIS observations)
   - validation: Excluded complicated profiles and required clear single or double-peaked profiles; removed fiducial marks and filled bad pixels with median filters.  
  > "Only pixels with clear single and double peaked profiles are included in further analysis (i.e. complicated profiles are excluded)." (2.2 IRIS observations); "A few “bad” pixels in the C ii and Si iv line-core images were filled using a median filter." (3 Analysis and results)
3. **Spatial and temporal co-alignment and region partitioning**: Co-align IRIS, SDO, and ALMA images using 2D cross-correlation; segment the FOV into 5 magnetic regions based on SDO/HMI VFISV magnetic field strength; calculate pixel-by-pixel observing time differences.  
  > "All images from IRIS and SDO are precisely co-aligned with that from ALMA (i.e. the IRIS and SDO images are first re-scaled to the ALMA images, then they are transformed (spatially shifted and/or rotated) based on cross-correlation of common features)." (2 Observations); "The sampling time of each pixel was extracted for both ALMA and IRIS maps, thus, their observing-time difference could be determined." (2.3 Observing-time difference); "We define different regions based on the level of magnetic field strength, B, deduced from inversions of full Stokes SDO/HMI observations (of the magnetically sensitive line Fe i 617.3 nm)." (2.5 Definition of regions)
   - software: VFISV
   - parameter: Regions: B >= 2 kG (umbra), B >= 0.8 kG (sunspot and pores), 0.8 <= B < 2 kG (penumbra and pores), 0.2 <= B < 0.8 kG (plage), B < 0.1 kG (quasi-quiet); time-lag thresholds: 2 min and 0.5 min  
  > "Five areas are chosen: B\geq2 kG comprising only the umbra, B\geq0.8 kG including the whole sunspot and the small pores, 2 kG>B\geq0.8 kG that is similar to the previous region except the umbra and thus comprises the penumbra and pores, 0.8 kG>B\geq0.2 kG defining the plage areas, and B<0.1 kG to represent the quasi-quiet regions." (2.5 Definition of regions); "More importantly, we only include pixels, from either of the first two IRIS scans, which have a maximum observing-time difference of two minutes with their corresponding pixels in the ALMA map" (3.2 Relationships between ALMA and IRIS)
   - assumption: Photospheric magnetic field structure defines chromospheric magnetic regions.  
  > "This is used for partitioning the entire FOV into areas with different amoutns of (photospheric) magnetic fields, underlying their chromospheric (and transition region) counterparts sampled with ALMA and IRIS." (2.4 SDO images)
   - fitting: _not stated_
   - validation: Verified spatial co-alignment by cross-correlating SDO/HMI continuum with IRIS Mg II 283.2 nm raster.  
  > "In addition, we verified the alignments by means of a cross correlation of common features between the SDO/HMI continuum (which was separately co-aligned with ALMA) and the IRIS Mg ii raster image at 283.2 nm" (2.2 IRIS observations)
4. **Statistical distribution comparison and pixel-to-pixel correlation analysis**: Compute Trad histograms for ALMA and IRIS lines across magnetic regions. For one-to-one comparison, convolve IRIS maps to the ALMA PSF (2.2'' x 0.7''), resample to ALMA pixel grid, restrict to delta_t <= 2 min (and 0.5 min), and calculate Pearson r, linear regression slope m, Spearman rho, and Kolmogorov-Smirnov test statistic d.  
  > "Distributions of the radiation temperature measured at 1.3 mm by ALMA and at the multiple line features of the UV spectra by IRIS are plotted in Figures 6 and 7." (3.1 Radiation temperature distributions); "Prior to the comparison, the IRIS images are (1) convolved with the PSF of the ALMA map (i.e. equivalent to a 2.2''\times0.7'' Gaussian kernel), and (2) re-sampled to the same pixel size as in the ALMA map." (3.2 Relationships between ALMA and IRIS); "In order to test for a potential linear relationship between the radiation temperature (or intensity) values of the UV diagnostics and that of the ALMA, the Pearson correlation coefficient r is calculated for each pair." (3.2 Relationships between ALMA and IRIS); "To investigate how the distributions of the radiation temperatures, compared in the scatter plots in Section 3.2 (i.e. from the similar spatial-resolution data; sampled within two minutes in time), are compared, we also employ the Kolmogorov–Smirnov (K-S) test." (3.2.1 Agreements between temperature distributions)
   - parameter: ALMA PSF convolution: 2.2'' x 0.7'' Gaussian kernel; delta_t <= 2 min and delta_t <= 0.5 min  
  > "Prior to the comparison, the IRIS images are (1) convolved with the PSF of the ALMA map (i.e. equivalent to a 2.2''\times0.7'' Gaussian kernel), and (2) re-sampled to the same pixel size as in the ALMA map." (3.2 Relationships between ALMA and IRIS)
   - assumption: Limiting time difference to <= 2 min (or 0.5 min) mitigates distortion of correlation metrics by chromospheric dynamic evolution.  
  > "Although this selection limits us to only 28% of the entire FOV, the one-to-one comparison is free from temperature changes happening on time scales longer than 2 min." (3.2 Relationships between ALMA and IRIS)
   - fitting: Linear regression for slope m, Pearson r, and Spearman rank correlation rho.  
  > "Furthermore, the linear regression coefficient of the linear fit m, which measures the steepness of a linear relationship, is calculated. However, in several cases, the relationships between radiation temperatures of the pair lines appear to be nonlinear. Hence, we also calculate the Spearman’s rank correlation coefficient \rho" (3.2 Relationships between ALMA and IRIS)
   - validation: Repeated correlations with delta_t <= 0.5 min to confirm that residual time lags did not dominate results.  
  > "To investigate the effect of rapid solar evolution in time scales shorter than 2 min, we also repeated the analyses with a maximum time difference of 0.5 min." (3.2 Relationships between ALMA and IRIS)

## Software

- **CASA** : Standard calibrations, imaging, and feathering steps of ALMA data  
  > "Extraction of the four different spectral windows (i.e. with ALMA identity numbers 5,7,9, and 11) included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (2.1 Observations with ALMA)
- **SoAP** first version: Solar ALMA Pipeline: tuning reduction parameters, separating sub-bands and spectral channels  
  > "We have optimised the standard reduction pipeline by tuning various parameters, also separating the sub-bands and the spectral channels (instead of a spectral integration, which is done by default in the standard pipeline). The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication" (2.1 Observations with ALMA)
- **MOSiC** : Extracting line features (blue and red emission peaks and line cores) from IRIS spectra via sequential Gaussian fitting  
  > "are computed with the MOSiC analysis tool (cite: Rezaei2017)." (2.2 IRIS observations)
- **VFISV** : Milne-Eddington Stokes inversion of SDO/HMI Fe I 617.3 nm data to obtain photospheric magnetic field strength  
  > "We also use the results of the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011) to obtain the photospheric magnetic field strength." (2.4 SDO images)
- **Bifrost** : 3D radiation MHD simulations inspected to interpret temperature correlation vs formation height difference  
  > "By inspecting the 3D radiation MHD simulations from the Bifrost code (cite: Gudiksen2011; Carlsson2016), we found a similar behaviour in the solar chromosphere (in quiet and enhanced network regions)." (3.2 Relationships between ALMA and IRIS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3 mm mean brightness temperature (entire FOV) | 6.6 | 0.5 | kK | 4 | The brightness temperature at 1.3 mm varies between 4.6–8.1 kK in the entire FOV with an average and standard variation of 6.6 kK and 0.5 kK, respectively.; FOV / mean / 6.6 / 6.6 / 5.6 / 5.3 / 5.6 / 5.5 / 5.2 / 5.4 |
| ALMA 1.3 mm mean brightness temperature (umbra) | 5.6 | 0.4 | kK | 4 | Its mean value is the smallest in the umbra (5.6\pm0.4 kK; where the uncertainty is the standard deviation of the distribution) |
| ALMA 1.3 mm mean brightness temperature (plage) | 7.0 | 0.4 | kK | 4 | and is the largest in the plage region (7.0\pm0.4 kK). |
| ALMA 1.3 mm mean brightness temperature (quasi-quiet regions) | 6.5 | 0.4 | kK | 4 | Regions / mean / 6.5 / 6.5 / 5.3 / 5.1 / 5.3 / 5.2 / 5.0 / 5.2; That is 6.5\pm0.4 kK in the quasi-quiet regions in the immediate vicinity of the sunspot. |
| ALMA 1.3 mm brightness temperature range (entire FOV) | 4.6–8.1 | not stated | kK | 4 | The brightness temperature at 1.3 mm varies between 4.6–8.1 kK in the entire FOV with an average and standard variation of 6.6 kK and 0.5 kK, respectively. |
| C II 133.4 nm mean radiation temperature (entire FOV) | 6.6 | 0.3 | kK | 4 | FOV / mean / 6.6 / 6.6 / 5.6 / 5.3 / 5.6 / 5.5 / 5.2 / 5.4; FOV / \sigma / 0.5 / 0.3 / 0.4 / 0.3 / 0.4 / 0.4 / 0.3 / 0.4 |

## Qualitative findings

- Splitting ALMA Band 6 into its four sub-bands resolves finer structures and slightly increases spatial resolution compared to spectral averaging, avoiding spatial smearing.  
  > "However, it is clear that separating the sub bands (along with other improvement in the data reduction procedures) has resulted in resolving finer structures, compared to the same data reported earlier in the literature" (2.1 Observations with ALMA); "It was revealed that spectral splitting of the ALMA observations in a particular Band (here, in Band 6) results in a slightly higher spatial resolution. Otherwise, the standard spectral averaging smears out small-scale structures" (4 Summary and conclusions)
- Radiation temperature distribution of C II 133.4 nm line core has the closest overlap and agreement with ALMA 1.3 mm across all regions except the umbra, whereas Mg II lines systematically display lower radiation temperatures (4.2-5.7 kK).  
  > "In comparison with the UV radiation temperatures, the ALMA distribution has the best overlap with that from the C ii in all regions except in the umbra where the far-UV line poses higher T_rad compared to that from the mm band." (3.1 Radiation temperature distributions); "The brightness temperature measured with the ALMA observations at band 6 (i.e. at 1.3 mm) is, on average, compatible with that retrieved from the line core of the C ii, with an exception in the umbra, where the latter is, on average, hotter by 1 kK." (4 Summary and conclusions)
- Moderate-to-good positive correlations exist between ALMA 1.3 mm brightness temperatures and UV radiation temperatures for pixels with small observing-time differences (<= 2 min), but persistent offsets from the 1:1 line reflect non-LTE effects in UV lines.  
  > "The majority of the T_rad-T_rad scatter plots (for all solar regions, except the umbra) show a moderate-to-good positive linear correlation (i.e. 0.5 < r < 0.9)." (3.2 Relationships between ALMA and IRIS); "Despite the (good) degree of correlations between the radiation temperatures of the ALMA Band 6 and the UV diagnostics, there is always an offset between the T_rad-T_rad trend of the scatter points and the y=x line" (4 Summary and conclusions)

## Claim tuples

- H: Separating ALMA Band 6 sub-bands rather than averaging across the band preserves formation height information and avoids spatial smearing. | E: Reconstructed individual brightness temperature maps for the four sub-bands (SW0 to SW3) using CASA and SoAP, and compared small-scale features against the synthesized beam sizes. | R: Distinct appearance of small structures larger than the synthesized beam was identified between the sub-bands, varying across the 7% beam size change. | F: Spectral splitting preserves small-scale structures and slight formation height variations across the band pass. | **supported**
- H: Chromospheric radiation temperatures probed by ALMA 1.3 mm correlate on a pixel-by-pixel basis with IRIS UV radiation temperatures once matched in spatial resolution and restricted to small observing time differences. | E: Convolved IRIS rasters to ALMA's PSF (2.2'' x 0.7''), restricted pixels to delta_t <= 2 min (and <= 0.5 min), and computed Pearson r and Spearman rho across 5 magnetic regions. | R: Moderate-to-good positive correlations (0.5 < r < 0.9) were found across all regions except the umbra; restricting to delta_t <= 0.5 min increased r further. | F: ALMA 1.3 mm and IRIS UV diagnostics track similar chromospheric thermal structures, but offsets from y=x remain due to non-LTE source function decoupling in UV diagnostics. | **supported**
- H: ALMA 1.3 mm brightness temperatures and IRIS UV radiation temperatures vary systematically across solar magnetic environments. | E: Partitioned the field into umbra, penumbra/pores, plage, and quasi-quiet Sun based on SDO/HMI photospheric magnetic field inversions and generated statistical distributions. | R: ALMA mean brightness temperature was lowest in the umbra (5.6 +/- 0.4 kK), intermediate in quasi-quiet regions (6.5 +/- 0.4 kK), and highest in plage (7.0 +/- 0.4 kK); Mg II and C II lines showed analogous regional variation. | F: Both millimetre and UV diagnostics reflect cooler chromospheric conditions in strong sunspot fields (likely via Wilson depression and reduced heating) and elevated heating in plage magnetic flux. | **supported**

## Reasoning

- Why this data: ALMA Band 6 provides LTE linear gas temperature diagnostics in the Rayleigh-Jeans regime to contrast with non-LTE IRIS UV diagnostics over the same active region.  
  > "With the millimetre wavelengths being in the Rayleigh-Jeans limit, the temperature can be simply measured under the assumption of local thermodynamic equilibrium (LTE), in contrast to UV diagnostics for which deviations from LTE cannot be neglected" (1 Introduction)
- Why this method: Separating individual 2 GHz sub-bands avoids spatial smearing and captures distinct formation heights; spatial PSF convolution and temporal masking isolate physical relationships from instrumental and solar-evolution biases.  
  > "However, they represent slightly different heights of formation, thus, averaging these sub-bands (as has been commonly done), results in losing the height information and can lead to spatial smearing" (2.1 Observations with ALMA); "Although this selection limits us to only 28% of the entire FOV, the one-to-one comparison is free from temperature changes happening on time scales longer than 2 min." (3.2 Relationships between ALMA and IRIS)
- Alternative: Spectral averaging across all four Band 6 sub-bands was rejected because it reduces spatial resolution and loses height-of-formation stratification.  
  > "However, they represent slightly different heights of formation, thus, averaging these sub-bands (as has been commonly done), results in losing the height information and can lead to spatial smearing (i.e. reduced spatial resolution)." (2.1 Observations with ALMA)
- Alternative: Radiation temperatures were rejected for optically thin lines (O I and Si IV) because their emergent intensity integrates over a wide line of sight rather than reflecting a local source function.  
  > "We remind the reader that radiation temperature of the optically thin lines (i.e. O i and Si iv) are meaningless, as they are results of integration of the contribution function across a wide range of heights along the line of sight. Hence, their radiation temperatures are not calculated here." (3 Analysis and results)
- How they decided it was enough: Checked whether restricting time differences further from 2 min to 0.5 min changed the core conclusions; found higher r but similar overall distributions and offsets.  
  > "The correlation coefficients r as well as slopes of the scatter plots m for pixels with a maximum time difference of 0.5 min have somewhat small differences compared to those with larger time lags of up to 2 min." (3.2 Relationships between ALMA and IRIS)
- Limitation (authors): Comparing IRIS Trad with ALMA brightness temperature is subject to UV non-LTE decoupling (Trad != Tgas) and formation height differences.  
  > "We remind the reader that the T_rad of the Mg ii lines (and of the C ii line) is not equal to their actual gas temperature (cite: Leenaarts2013b; Rathore2015a), thus the comparison of their T_rad with ALMA should be done with great caution" (3.1 Radiation temperature distributions)
- Limitation (authors): Strict time-lag cuts (<= 2 min or 0.5 min) severely reduced the usable FOV area (to 28% and 8% respectively), leaving very few umbral data points.  
  > "Although this selection limits us to only 28% of the entire FOV, the one-to-one comparison is free from temperature changes happening on time scales longer than 2 min." (3.2 Relationships between ALMA and IRIS); "The very small correlation coefficients we found in the umbra could partly be due to a large uncertainty introduced by the very few data points entering the analysis" (4 Summary and conclusions)
- Caveat (inferred, ours): Differences between sub-bands could be influenced by residual calibration errors or the 7% variation in beam size rather than pure formation height stratification.
- Caveat (inferred, ours): Non-LTE radiation temperature is an imperfect proxy for gas temperature, preventing a direct 1-to-1 thermodynamic comparison without detailed forward modeling.

## Reproducibility

- Data public (paper): Public ALMA science verification data ADS/JAO.ALMA#2011.0.00020.SV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00020.SV." (Acknowledgements)
- Products in archive: _not stated_
- Code: SoAP pipeline described as forthcoming in Szydlarski et al. (2018); MOSiC and VFISV cited from literature.  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication (cite: Szydlarski2018)." (2.1 Observations with ALMA)
- Missing: Exact parameter configuration scripts for SoAP used to produce the sub-band images
- Missing: Precise feathering weights/scaling factors applied between TP maps and interferometric mosaic
- Data volume (inferred): 50-200 GB (ALMA 149-pointing mosaic raw TDM visibilities and TP maps plus IRIS 320-step rasters and SDO AIA/HMI maps)
- Score (inferred): 7/5, The science verification ALMA data, IRIS rasters, and SDO data are fully public and clearly identified. The core analysis steps (converting DN to Trad, masking magnetic regions, matching PSF, and cross-correlation) are well explained. However, the custom SoAP pipeline scripts and exact CASA feather parameters are not provided in the paper text.
- Rediscovery candidate: yes, All raw data are public in standard archives (ALMA SV, IRIS, SDO), the observational and calibration steps follow established procedures, and the quantitative findings (temperatures across magnetic regions and correlation statistics) provide clear benchmarks for replication.

## Links

- Method: (cite: Shimojo2017) (Standard CASA calibrations, imaging, and feathering procedures for ALMA solar commissioning data)
- Method: (cite: White2017) (Total Power calibration and absolute brightness temperature scaling for ALMA solar observations)
- Method: (cite: Rezaei2017) (MOSiC analysis tool for multi-Gaussian fitting of IRIS UV spectral lines)
- Method: (cite: Borrero2011) (VFISV Milne-Eddington inversion of SDO/HMI Stokes profiles)
- Companion: (cite: Szydlarski2018) (Describes the Solar ALMA Pipeline (SoAP) used to optimize reduction and separate sub-bands)
- Related: ALMA Solar Commissioning Science Verification Campaign 6

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 90,
 "quote_pass_rate": 0.957,
 "quotes_too_long": 12,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 54,
  "rate": 0.659
 },
 "evidence_ok": false
}
```
