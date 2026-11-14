# The solar chromosphere at millimetre and ultraviolet wavelengths. I. Radiation temperatures and a detailed comparison

`2019A&A...622A.150J` | Astronomy and Astrophysics 2019 | first author: Jafarzadeh, S. | arXiv: 1901.05763 | DOI: 10.1051/0004-6361/201834205

Card schema 1.0 | model claude-opus-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How do radiation temperature distributions at various chromospheric heights from ALMA Band 6 (1.3 mm) compare with IRIS near- and far-UV diagnostics in solar regions with different magnetic field levels, statistically and pixel-to-pixel?  
  > "The present work provides distributions of the radiation temperature at various chromospheric heights sampled by the ALMA 1.3 mm passband and the IRIS observations at near- and far-UV wavelengths" (Introduction); "The comparison between the different distributions are performed for various solar regions with different amounts of underlying magnetic fields." (Introduction)
- Target **Solar active region AR 12470**: coordinates close to solar disc-center (cosine of heliocentric angle ≈0.97)  
  > "The field of view (FOV) includes the leading sunspot of the active region AR 12470 surrounded by plages and quasi-quiet areas, close to the solar disc-center" (Observations with ALMA); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 6 (centred at 239 GHz; 1.25 mm); SW0 at 1.3 mm used for analysis  
  > "was obtained in ALMA band 6 (centred at 239 GHz; 1.25 mm) on 18 December 2015 between 19:39:25–20:02:34 UT" (Observations with ALMA); "Among the four sub-bands, we use, in the following, the brightness temperature at 1.3 mm which supposedly corresponds to the highest sampled layer in the solar atmosphere." (Observations with ALMA)
- frequencies and spectral setup: Four spectral windows of 2 GHz each, 128 channels each, TDM; sub-bands SW3, SW2, SW1, SW0 at 248, 246, 232, 230 GHz (1.209, 1.219, 1.292, 1.303 mm)  
  > "Four spectral windows (sub bands), with a bandwidth of 2 GHz each, were recorded. Each spectral window (SW) includes 128 channels (with time domain mode (TDM) as the spectral setup)." (Observations with ALMA); "These correspond to frequencies 248, 246, 232, and 230 GHz, respectively." (Observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: Heterogeneous array of twenty-one 12 m and nine 7 m antennas, plus total power array (fast-scanning full-disc maps)  
  > "The data was taken using a heterogeneous array configuration consisting of twenty-one 12 m and nine 7 m antennas." (Observations with ALMA); "full-disc total power maps were simultaneously obtained through single dish observations (i.e. with the total power (TP)-array in fast-scanning mode)." (Observations with ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 149-point mosaic, 6.048 s integration per point, pointing separation 11.2 arcsec (Nyquist)  
  > "The mosaic observations were performed with a pointing separation of 11.2 arcsec (corresponding to Nyquist sampling) and an integration time of 6.048 s for each point." (Observations with ALMA)
- observing dates: 18 December 2015, 19:39:25–20:02:34 UT  
  > "was obtained in ALMA band 6 (centred at 239 GHz; 1.25 mm) on 18 December 2015 between 19:39:25–20:02:34 UT" (Observations with ALMA)
- pi or archival as stated: Solar commissioning science verification campaign data  
  > "in the 6th solar commissioning science verification campaign" (Observations with ALMA)
- Line: Mg II k (k2v, k3, k2r) (279.6 nm)
- Line: Mg II h (h2v, h3, h2r) (280.4 nm)
- Line: C II line core (133.4 nm)
- Line: Si IV line core (139.4 nm)
- Line: O I line core (135.6 nm)
- Other facility **IRIS**: Very large dense 320-step rasters (2 s exposure), three scans 19:33:14–20:24:20 UT; UV spectra of Mg II, C II, Si IV, O I  
  > "The ALMA observations were supported by the IRIS spacecraft in the “very large dense 320-step raster” mode with 2 s exposure time per step." (IRIS observations); "Three full IRIS scans were recorded between 19:33:14–20:24:20 UT" (IRIS observations)
- Other facility **SDO/AIA**: AIA 170 nm and 30.4 nm images for co-alignment with ALMA  
  > "We use a combination of the AIA 170 nm and 30.4 nm images to perform a precise spatial alignment with the ALMA scan." (SDO images)
- Other facility **SDO/HMI**: Continuum for alignment verification and Milne-Eddington inversion (VFISV) magnetic field strength for region masks  
  > "We also use the results of the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011) to obtain the photospheric magnetic field strength." (SDO images)
- External data: Simulation result that C II source function gives T_gas = 2 T_rad, used to interpret C II–ALMA agreement  
  > "However, a $T_{gas}=2T_{rad}$ relationship was found by (cite: Rathore2015a) from a numerical simulation." (Agreements between temperature distributions) [from (cite: Rathore2015a)]
- External data: Linear correlation coefficients for umbra, plage and quiet regions from earlier ALMA–IRIS Mg II h comparison  
  > "The linear correlation coefficients reported by (cite: Bastian2017; Bastian2018) for three different regions of umbra, plage and quiet regions are, respectively, higher by a factor of 8.5, 1.04, and 1.03 compared to those found here." (Summary and conclusions) [from (cite: Bastian2017; Bastian2018)]
- Simulation/model as data: 3D radiation MHD Bifrost simulations inspected for pixel-to-pixel gas temperature relationships between chromospheric layers  
  > "By inspecting the 3D radiation MHD simulations from the Bifrost code (cite: Gudiksen2011; Carlsson2016), we found a similar behaviour in the solar chromosphere (in quiet and enhanced network regions)." (Relationships between ALMA and IRIS)

## Processing

### Calibration

- pipeline or manual: Standard CASA calibrations, imaging and feathering, with an optimised Solar ALMA Pipeline (SoAP) separating sub-bands and channels  
  > "Extraction of the four different spectral windows (i.e. with ALMA identity numbers 5,7,9, and 11) included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (Observations with ALMA); "We have optimised the standard reduction pipeline by tuning various parameters, also separating the sub-bands and the spectral channels (instead of a spectral integration, which is done by default in the standard pipeline)." (Observations with ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Pipeline (official ALMA pipeline and SoAP) brightness temperature output used with no further processing  
  > "The calibrated ALMA data product as output of the pipeline (both, the official ALMA pipeline and SoAP) is the brightness temperature (with an uncertainty in the order of 5%). Thus, it directly enters our analysis with no further processing." (Analysis and results)
- flux calibrator: _not stated_
- flux scale uncertainty: approximately 5% in brightness temperature  
  > "The shaded areas around the histograms indicate the approximate 5% uncertainty in measurements of the brightness temperatures." (Observations with ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: ≈0.15 arcsec/pixel  
  > "with a sampling resolution of ≈0.15 arcsec/pixel" (Observations with ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Interferometric mosaic feathered with total power maps for absolute brightness temperatures  
  > "The TP maps are used to derive absolute brightness temperatures for the interferometric data (cite: Shimojo2017; White2017)." (Observations with ALMA)
- smoothing: _not stated_
- final beam: ALMA PSF equivalent to a 2.2''×0.7'' Gaussian; beam varies by about 7% from SW0 to SW3  
  > "convolved with the PSF of the ALMA map (i.e. equivalent to a 2.2''×0.7'' Gaussian kernel)" (Relationships between ALMA and IRIS); "the beam size, which represents the spatial resolution, slightly varies between the four sub-bands, by about 7% from Sw0 to Sw3" (Observations with ALMA)
- final rms: _not stated_

### Inherited from earlier work

- CASA calibration, imaging and feathering steps  
  > "included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)." (Observations with ALMA) [from (cite: Shimojo2017)]
- Use of TP maps for absolute brightness temperature calibration  
  > "The TP maps are used to derive absolute brightness temperatures for the interferometric data (cite: Shimojo2017; White2017)." (Observations with ALMA) [from (cite: Shimojo2017; White2017)]
- Solar ALMA Pipeline (SoAP) described in forthcoming publication  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication (cite: Szydlarski2018)." (Observations with ALMA) [from (cite: Szydlarski2018)]
- IRIS line-feature extraction with the MOSiC analysis tool  
  > "are computed with the MOSiC analysis tool (cite: Rezaei2017)." (IRIS observations) [from (cite: Rezaei2017)]
- HMI Milne-Eddington inversion with VFISV  
  > "We also use the results of the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011)" (SDO images) [from (cite: Borrero2011)]

### Not stated but needed to reproduce (our reading)

- The SoAP parameters that were 'tuned' relative to the standard pipeline (SoAP is unpublished, in prep.)
- CASA version and imaging parameters (deconvolver, weighting/robust, masking, niter, image size) for each sub-band
- Self-calibration usage and solution intervals, if any
- Feathering parameters and TP absolute calibration details
- Exact SDO/HMI and AIA image times and HMI inversion product used
- Co-alignment procedure details (re-scaling factors, rotation angle, cross-correlation implementation)
- Gaussian-fit thresholds and reduced chi-square cutoffs in MOSiC for accepting line features
- Median filter size used to fill bad pixels and fiducial marks
- IRIS OBS ID / data levels and orbital-velocity correction details
- Treatment of pixels with 0.1 kG ≤ B < 0.2 kG (excluded from all masks)

## Analysis recipe

1. **Produce per-sub-band ALMA brightness temperature maps**: Calibration, imaging and feathering with TP per spectral window, separating sub-bands instead of averaging; select SW0 (1.3 mm)  
  > "Thus, brightness temperature maps of the four sub bands (i.e. SW3, SW2, SW1, and SW0), corresponding to wavelengths 1.209, 1.219, 1.292, and 1.303 mm, respectively, were obtained." (Observations with ALMA)
   - software: CASA, SoAP
   - parameter: four 2 GHz spectral windows, 128 channels, TDM  
  > "Each spectral window (SW) includes 128 channels (with time domain mode (TDM) as the spectral setup)." (Observations with ALMA)
   - assumption: mm emission in Rayleigh-Jeans limit and LTE, so brightness temperature represents gas temperature  
  > "With the millimetre wavelengths being in the Rayleigh-Jeans limit, the temperature can be simply measured under the assumption of local thermodynamic equilibrium (LTE)" (Introduction)
   - fitting: _not stated_
   - validation: Histograms of four sub-bands compared; differences within 5% measurement error  
  > "The small differences of the histograms lie within the measurement error of the brightness temperature by ALMA, thus no detailed comparison of the sub bands is provided." (Observations with ALMA)
2. **Extract IRIS line features**: Per-pixel Gaussian fits of increasing complexity (single then multiple Gaussians) after orbital-velocity correction; only clear single/double peaked profiles kept  
  > "the various line features are determined at each pixel using a Gaussian fit, for which the degree of freedom gradually increases." (IRIS observations); "Only pixels with clear single and double peaked profiles are included in further analysis (i.e. complicated profiles are excluded)." (IRIS observations)
   - software: MOSiC
   - parameter: single-peaked profiles interpreted as line core  
  > "In the former case, the emission peak represents the line core, in the latter, the central reversal (i.e. k3 and h3 features)." (IRIS observations)
   - fitting: Goodness of fit by reduced chi-square; each fit initial guess for next  
  > "The goodness of the fits at each step is evaluated by means of reduced chi-square statistics (cite: Bevington1992)." (IRIS observations)
   - validation: _not stated_
3. **Convert IRIS intensities to radiation temperature**: Radiometric conversion of data numbers to intensity and inversion of the Planck function; not done for optically thin O I and Si IV  
  > "We calculate the near- and far-UV radiation temperature $T_{rad}$ in the solar chromosphere at a given wavelength $\lambda$ by solving the Planck function as" (Analysis and results); "Hence, their radiation temperatures are not calculated here." (Analysis and results)
   - software: IRIS radiometric calibration-routine (version 4)
   - parameter: IRIS radiometric calibration version 4, ~15% uncertainty; T_rad uncertainty 2%  
  > "These parameters were obtained using the latest version (version 4) of the IRIS radiometric calibration-routine (with an uncertainty of about 15%)." (Analysis and results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Co-align ALMA, IRIS and SDO**: Re-scale to ALMA, shift/rotate via cross-correlation of common features (Mg II k2v vs ALMA; AIA 170+30.4 nm vs ALMA; verified with HMI continuum vs IRIS 283.2 nm)  
  > "The IRIS raster images were spatially co-aligned with the ALMA scan by cross correlating the Mg ii k2v and ALMA 1.3 mm images." (IRIS observations); "the IRIS and SDO images are first re-scaled to the ALMA images, then they are transformed (spatially shifted and/or rotated) based on cross-correlation of common features" (Observations)
   - fitting: _not stated_
   - validation: Alignment verified with SDO/HMI continuum vs IRIS Mg II 283.2 nm raster  
  > "In addition, we verified the alignments by means of a cross correlation of common features between the SDO/HMI continuum (which was separately co-aligned with ALMA) and the IRIS Mg ii raster image at 283.2 nm" (IRIS observations)
5. **Compute observing-time difference maps**: Per-pixel sampling times for ALMA and the first two IRIS scans; combine scans to build regions with max Δt of 5, 2 and 0.5 min  
  > "The sampling time of each pixel was extracted for both ALMA and IRIS maps, thus, their observing-time difference could be determined." (Observing-time difference); "Such combined regions for various areas where the maximum time difference is 5 min (white area), 2 min (blue hatched area), and 0.5 min (red hatched area) are depicted" (Observing-time difference)
   - fitting: _not stated_
   - validation: _not stated_
6. **Define magnetic regions**: Threshold HMI field strength map: umbra B≥2 kG; sunspot & pores B≥0.8 kG; penumbra & pores 2>B≥0.8 kG; plage 0.8>B≥0.2 kG; quasi-quiet B<0.1 kG  
  > "Five areas are chosen: $B\geq2$ kG comprising only the umbra, $B\geq0.8$ kG including the whole sunspot and the small pores" (Definition of regions)
   - software: VFISV
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare T_rad distributions per region**: Histograms, means, standard deviations and ranges of ALMA 1.3 mm and IRIS T_rad using second IRIS scan at original resolution resampled to ALMA pixel scale  
  > "Hence, the IRIS radiation temperatures correspond to those computed from the second scan of the IRIS raster with its original spatial resolution." (Radiation temperature distributions)
   - fitting: _not stated_
   - validation: _not stated_
8. **Pixel-to-pixel ALMA–IRIS relationships**: IRIS maps convolved with ALMA PSF and resampled; pixels with Δt ≤ 2 min (and 0.5 min) selected; Pearson r, linear slope m and Spearman ρ computed  
  > "we only include pixels, from either of the first two IRIS scans, which have a maximum observing-time difference of two minutes with their corresponding pixels in the ALMA map" (Relationships between ALMA and IRIS); "Hence, we also calculate the Spearman’s rank correlation coefficient $\rho$, which better models non-linear relationships and is not sensitive to outliers." (Relationships between ALMA and IRIS)
   - parameter: Δt ≤ 2 min (28% of FOV) and Δt ≤ 0.5 min (about 8% of FOV)  
  > "Although this selection limits us to only 28% of the entire FOV, the one-to-one comparison is free from temperature changes happening on time scales longer than 2 min." (Relationships between ALMA and IRIS)
   - fitting: Linear regression slope m  
  > "Furthermore, the linear regression coefficient of the linear fit $m$, which measures the steepness of a linear relationship, is calculated." (Relationships between ALMA and IRIS)
   - validation: Repeated with stricter 0.5 min time difference  
  > "To investigate the effect of rapid solar evolution in time scales shorter than 2 min, we also repeated the analyses with a maximum time difference of 0.5 min." (Relationships between ALMA and IRIS)
9. **Test agreement of distributions**: Kolmogorov–Smirnov test on CDFs of T_rad for pixels within 2 min  
  > "we also employ the Kolmogorov–Smirnov (K-S) test." (Agreements between temperature distributions)
   - fitting: _not stated_
   - validation: Similar K-S results for individual regions  
  > "A very similar result was obtained for the individual regions of interests studied in Section" (Agreements between temperature distributions)

## Software

- **CASA** : Standard calibration, imaging and feathering of ALMA data  
  > "included standard CASA calibrations, imaging, and feathering steps" (Observations with ALMA)
- **Solar ALMA Pipeline (SoAP)** first version: Optimised reduction separating sub-bands and channels  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication (cite: Szydlarski2018)." (Observations with ALMA)
- **MOSiC** : IRIS line-feature determination via Gaussian fitting  
  > "are computed with the MOSiC analysis tool (cite: Rezaei2017)." (IRIS observations)
- **VFISV** : Milne-Eddington inversion of HMI Stokes data for magnetic field strength  
  > "We also use the results of the Milne-Eddington Stokes inversion of the HMI data with the VFISV code" (SDO images)
- **IRIS radiometric calibration-routine** version 4: Parameters for converting IRIS data numbers to intensity  
  > "These parameters were obtained using the latest version (version 4) of the IRIS radiometric calibration-routine" (Analysis and results)
- **Bifrost** : 3D radiation MHD simulations inspected for comparison  
  > "By inspecting the 3D radiation MHD simulations from the Bifrost code (cite: Gudiksen2011; Carlsson2016)" (Relationships between ALMA and IRIS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3 mm brightness temperature, entire FOV mean | 6.6 | standard deviation 0.5 | kK | 7 | The brightness temperature at 1.3 mm varies between 4.6–8.1 kK in the entire FOV with an average and standard variation of 6.6 kK and 0.5 kK, respectively. |
| ALMA 1.3 mm brightness temperature range, entire FOV | 4.6–8.1 | not stated | kK | 7 | The brightness temperature at 1.3 mm varies between 4.6–8.1 kK in the entire FOV |
| ALMA Band 6 mean brightness temperature in umbra | 5.6 | ±0.4 (standard deviation) | kK | 7 | The ALMA Band 6 represents a mean brightness temperature of 5.6±0.4 kK in the umbra |
| ALMA Band 6 mean brightness temperature in quasi-quiet regions | 6.5 | ±0.4 (standard deviation) | kK | 7 | That is 6.5±0.4 kK in the quasi-quiet regions in the immediate vicinity of the sunspot. |
| ALMA Band 6 mean brightness temperature in plage | 7.0 | ±0.4 (standard deviation) | kK | 7 | The ALMA’s band 6 poses its highest brightness temperature in plage areas (with a mean value of 7.0±0.4 kK). |
| Mean radiation temperature range of IRIS Mg II lines across regions | 4.2–5.7 | not stated | kK | 7 | We found that in all solar regions the IRIS magnesium lines represent the lowest mean radiation temperature in the order of 4.2–5.7 kK within the lines under study |
| Excess of C II line-core T_rad over ALMA 1.3 mm in umbra | 1 | not stated | kK | 7 | with an exception in the umbra, where the latter is, on average, hotter by 1 kK. |
| Pearson correlation range for most T_rad–T_rad scatter plots (excluding umbra) | 0.5 < r < 0.9 | not stated | dimensionless | 8 | The majority of the $T_{rad}$-$T_{rad}$ scatter plots (for all solar regions, except the umbra) show a moderate-to-good positive linear correlation (i.e. $0.5 < r < 0.9$). |
| Fraction of FOV with Δt ≤ 2 min | 28 | not stated | % | 5 | Although this selection limits us to only 28% of the entire FOV |
| Fraction of FOV with Δt ≤ 0.5 min | about 8 | not stated | % | 5 | about 8% of the entire FOV |
| Uncertainty of IRIS radiation temperatures | 2 | not stated | % | 3 | We note that, however, the radiation temperatures are estimated with an uncertainty of 2% (due to the exponential of the Planck function). |
| Ratio of Bastian et al. correlation coefficients to this work (umbra, plage, quiet) | 8.5, 1.04, 1.03 | not stated | dimensionless | 8 | for three different regions of umbra, plage and quiet regions are, respectively, higher by a factor of 8.5, 1.04, and 1.03 compared to those found here. |

## Qualitative findings

- ALMA 1.3 mm T_rad distributions are about twice as wide as C II ones (except plage), suggesting contributions from a wider height range  
  > "This may suggest that the ALMA 1.3 mm sub-band includes contributions from a wider range of chromospheric heights than the C ii line." (Radiation temperature distributions)
- Relationships between far-UV channels and ALMA 1.3 mm are non-linear  
  > "The relationships between the far-UV channels and the ALMA 1.3 mm were found to be non-linear." (Summary and conclusions)
- K-S test: only C II T_rad distribution agrees to some extent with ALMA 1.3 mm  
  > "It is evident that only $T_{rad}$ distribution of the C ii line has, to some extent, agreement with that of the ALMA 1.3 mm." (Agreements between temperature distributions)

## Claim tuples

- H: Separating ALMA Band 6 sub-bands rather than averaging improves resolution of small-scale structure | E: Imaged four sub-bands separately with SoAP and compared appearance with earlier reductions | R: Finer structures resolved; sub-band histograms differ within 5% error | F: Spectral splitting gives slightly higher spatial resolution; averaging smears structures and biases distributions | **supported**
- H: Chromospheric brightness temperature depends on underlying photospheric magnetic field | E: Compared ALMA 1.3 mm Tb distributions in HMI-defined magnetic masks | R: Mean 5.6 kK in umbra, 6.5 kK quasi-quiet, 7.0 kK plage | F: Lowest temperatures in umbra, highest in plage for all channels | **supported**
- H: ALMA 1.3 mm temperatures agree with IRIS UV radiation temperatures | E: Compared distributions and K-S test of ALMA vs C II and Mg II T_rad | R: C II compatible on average except umbra (hotter by 1 kK); Mg II lower | F: ALMA agrees best with C II line core; Mg II T_rad lower, likely non-LTE | **partially**
- H: Spatial variations of UV T_rad and ALMA Tb are correlated pixel-to-pixel | E: Scatter plots of PSF-matched maps for pixels within 2 and 0.5 min observing-time difference; Pearson, Spearman, slopes | R: Moderate-to-good positive correlations (0.5<r<0.9) except umbra; offsets from y=x except C II | F: Good overall correlations; offsets likely from non-LTE formation of UV lines | **supported**
- H: Observing-time differences affect one-to-one comparisons | E: Repeated correlations with Δt ≤ 0.5 min vs ≤ 2 min | R: Larger Pearson r in most cases but smaller slopes; offsets insignificantly affected | F: Accounting for time differences is important for one-to-one comparisons | **supported**

## Reasoning

- Why this data: mm wavelengths are in the Rayleigh-Jeans limit and LTE, complementing non-LTE UV diagnostics; SW0 chosen as highest sampled layer  
  > "Observations at millimetre wavelengths are complementary to the UV diagnostics in the sense that the source function varies linearly with temperature." (Introduction)
- Why this method: Spearman correlation used because some relationships appear non-linear; time-difference selection because chromosphere varies on short time-scales  
  > "However, in several cases, the relationships between radiation temperatures of the pair lines appear to be nonlinear." (Relationships between ALMA and IRIS); "Hence, the time differences must be taken into account when one-to-one comparison between the two observations is performed." (Observing-time difference)
- Alternative: Averaging sub-bands (standard approach) rejected because it loses height information and smears structure  
  > "averaging these sub-bands (as has been commonly done), results in losing the height information and can lead to spatial smearing (i.e. reduced spatial resolution)." (Observations with ALMA)
- Alternative: Radiation temperatures of optically thin O I and Si IV not computed; intensities used instead  
  > "We remind the reader that radiation temperature of the optically thin lines (i.e. O i and Si iv) are meaningless" (Analysis and results)
- How they decided it was enough: _not stated_
- Limitation (authors): 5% ALMA Tb uncertainty is an initial estimate; detailed error discussion deferred  
  > "A detailed discussion on the error of the temperature measurements by ALMA and of the calibrations (and to what degree the initial 5% estimation is realistic) are subject of a forthcoming paper." (Observations with ALMA)
- Limitation (authors): Histogram comparisons may have substantial time differences in part of the FOV  
  > "one should also keep in mind that there can be a substantial time differences between observations at UV and mm wavelengths in part of the FOV." (Radiation temperature distributions)
- Limitation (authors): Very few umbral data points make umbral correlations uncertain  
  > "The very small correlation coefficients we found in the umbra could partly be due to a large uncertainty introduced by the very few data points entering the analysis" (Summary and conclusions)
- Limitation (authors): UV T_rad not equal to gas temperature; comparison with ALMA requires caution  
  > "thus the comparison of their $T_{rad}$ with ALMA should be done with great caution" (Radiation temperature distributions)
- Caveat (inferred, ours): Correlation coefficients and slopes per region are only in figures (not tabulated), limiting quantitative checks
- Caveat (inferred, ours): Formation heights of ALMA 1.3 mm vs UV lines are not quantified; interpretation of offsets relies on literature simulations
- Caveat (inferred, ours): Sub-band beam differences (~7%) could partly explain structural differences attributed to height
- Caveat (inferred, ours): Single 23-min mosaic; ALMA mosaic itself not instantaneous, so internal temporal smearing is not addressed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: SoAP pipeline code and its tuned parameters (in prep.)
- Missing: Full CASA imaging/feathering settings
- Missing: IRIS dataset identifiers and MOSiC fit settings
- Missing: HMI inversion product identifiers and exact alignment transformations
- Missing: Region-wise r, m, ρ values in tabular form
- Data volume (inferred): ALMA SV mosaic visibilities plus TP maps of order tens of GB; IRIS rasters and SDO images a few GB
- Score (inferred): 2/5, ALMA reduction relies on an unpublished, tuned pipeline with no imaging parameters given; IRIS fitting and alignment details are sparse, though the statistical analysis is simple.
- Rediscovery candidate: no, The paper does not state the data are public, and the ALMA reduction (SoAP) is not described sufficiently to redo; results are numeric but the recipe is incomplete.

## Links

- Method: (cite: Shimojo2017) (Standard CASA calibration, imaging and feathering of solar ALMA data)
- Method: (cite: White2017) (Total power absolute brightness temperature calibration)
- Method: (cite: Szydlarski2018) (Solar ALMA Pipeline (SoAP))
- Method: (cite: Rezaei2017) (MOSiC IRIS spectral analysis tool)
- Method: (cite: Borrero2011) (VFISV Milne-Eddington inversion code for HMI)
- Companion: (cite: Bastian2017; Bastian2018) (Earlier ALMA Band 6 vs IRIS Mg II h comparison of the same data)
- Companion: (cite: Loukitcheva2017) (Same data reported earlier in the literature)
- Related: ALMA solar commissioning science verification campaign
- Related: IRIS
- Related: SDO (AIA, HMI)

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
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
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 62,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
