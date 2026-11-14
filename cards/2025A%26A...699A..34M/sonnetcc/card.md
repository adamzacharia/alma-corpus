# ALMAGAL: IV. Morphological comparison of molecular and thermal dust emission using the histogram of oriented gradients method

`2025A&A...699A..34M` | Astronomy and Astrophysics 2025 | first author: Mininni, C. | arXiv: 2504.12963 | DOI: 10.1051/0004-6361/202452700

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, astrochemistry
- Question: How well do individual molecular transitions (H2CO, CH3OH, DCN, HC3N, CH3CN, CH3OCHO, SO, SiO) morphologically trace the 1.38 mm dust continuum in 1013 ALMAGAL high-mass clumps, on extended and compact scales, measured with the HOG method  
  > "looking at morphological correlations in their overall integrated molecular line emission with the cold dust" (abstract); "A total of 1013 targets have been analyzed in the present paper" (abstract)
- Target **ALMAGAL sample of high-mass clumps (1013 analysed)**: coordinates _not stated_; z/distance heliocentric distances up to 7.5 kpc  
  > "Due to the close proximity (below the FOV size) of 3 pairs of sources and the exclusion of Eta Carinae, the sample analyzed is of 1013 sources" (2.1 The sample); "located at heliocentric distances up to 7.5 kpc" (2.1 The sample); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: Band 6 (1.38 mm)  
  > "in the 1.38 mm band (ALMA Band 6)" (2.2 Molecular transitions analyzed)
- frequencies and spectral setup: four spectral windows: two 1.9 GHz wide (0.98 MHz, ~1.3 km/s resolution) at 217.8 and 220.0 GHz; two 0.47 GHz wide (0.24 MHz, ~0.3 km/s) at 218.3 and 220.6 GHz  
  > "The spectral setup of the observations covers four spectral windows in total" (Observations and data reduction); "centered at 217.8 GHz and 220.0 GHz, and two higher resolution spectral windows with 0.47 GHz bandwidth and spectral resolution of 0.24 MHz" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 7-m array (7M) plus two configurations of the main 12-m array per target  
  > "each target was observed with the 7-m array (hereafter 7M) and with two configurations of the main ALMA array." (Observations and data reduction)
- configurations: near sources (d < 4.7 kpc): C-2 and C-5; far sources (d > 4.7 kpc): C-3 and C-6  
  > "were observed in configurations C-2 and C-5 of the main array" (Observations and data reduction); "were observed in configurations C-3 and C-6" (Observations and data reduction)
- baselines: _not stated_
- angular resolution: 7m+tm2 data used here: linear resolution ~5000 au; full 7m+tm2+tm1 reaches ~1000 au  
  > "that reach a linear resolution of $\sim 5000\,$au" (Observations and data reduction); "at a spatial resolution down to 1000 au" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October 2019 to July 2022 (Cycle 7)  
  > "was observed between October 2019 and July 2022" (Observations and data reduction)
- pi or archival as stated: ALMA large program ALMAGAL, PIs Molinari, Schilke, Battersby, Ho  
  > "ALMAGAL is an ALMA large project (2019.1.00195.L, PIs: Molinari, Schilke, Battersby, Ho" (Introduction)
- Line: SiO 5-4 (217.104980 GHz)
- Line: DCN 3-2 (217.238538 GHz)
- Line: H2CO 3(0,3)-2(0,2) (218.222192 GHz)
- Line: CH3OCHO 17(3,14)-16(3,13) E (218.280900 GHz)
- Line: HCCCN 24-23 (218.324723 GHz)
- Line: CH3OH 4(2,3)-3(1,2) (218.440063 GHz)
- Line: H2CO 3(2,1)-2(2,0) (218.760066 GHz)
- Line: SO 6(5)-5(4) (219.949442 GHz)
- Line: CH3CN 12(1)-11(1) (220.743011 GHz)
- Line: CH3CN 12(0)-11(0) (220.747261 GHz)
- Other facility **CORNISH 5 GHz survey**: Radio counterparts used to flag 112 clumps with possible free-free contamination of the 1.38 mm continuum  
  > "We identified 112 matched clumps, mostly evolved clumps" (4.4 Details of the application of astroHOG)
- Other facility **Hi-GAL (Herschel)**: Parent sample selection and physical parameters (L/M) of the clumps  
  > "the majority of the sample that was selected from the Hi-GAL survey" (Table 3 notes)
- External data: Sample definition and properties of the 1017 ALMAGAL clumps (1013 analysed)  
  > "the sample analyzed is of 1013 sources (see (cite: ALMAGAL1) for further details)" (2.1 The sample) [from (cite: ALMAGAL1)]
- External data: Clump mean temperatures from SED fitting of Herschel continuum (and L/M values)  
  > "as derived by (cite: elia2017; elia2021) from the SED fitting of the" (5.1 Statistics of detections on moment-0 maps) [from (cite: elia2017; elia2021)]
- External data: Critical densities of the analysed transitions (Eq. 4 of Shirley 2015) with LAMDA collisional coefficients  
  > "The critical densities have been calculated from Eq. (4) of (cite: Shirley2015)" (Table 1 notes); "from LAMDA (Leiden Atomic and Molecular Database)" (Table 1 notes) [from (cite: Shirley2015)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline for single-array calibration, then ALMAGAL dedicated pipeline for joint deconvolution  
  > "Using the standard pipeline, we calibrated the data of the single arrays" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: included in the ALMAGAL pipeline for the most intense sources  
  > "joint deconvolution of the various configurations observed that includes self-calibration for the most intense sources" (Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: iterative procedure starting from the ALMA-pipeline findcont to define continuum channels and line-only cubes  
  > "to refine the determination of the continuum channels used to create the continuum images and the line-only cubes" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: joint deconvolution of 7m and tm2 (7m+tm2) cubes and continuum maps from the ALMAGAL pipeline  
  > "we decided to analyze the cubes and continuum maps obtained by the joint deconvolution of" (Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Joint-deconvolution pipeline, findcont-based continuum channel selection and quality assessment of final cubes/continuum maps  
  > "A detailed description of this routine, together with a quality assessment of the final products, is presented in (cite: ALMAGAL2)." (Observations and data reduction) [from (cite: ALMAGAL2)]
- CuTEx source extraction on the continuum maps follows the ALMAGAL fragmentation paper methodology  
  > "using the same methodology of (cite: ALMAGAL3)" (Appendix A Continuum masks) [from (cite: ALMAGAL3)]
- HOG method and astroHOG implementation  
  > "using the HOG method presented in (cite: soler_astroHOG)" (4.3 Morphological analysis with astroHOG) [from (cite: soler_astroHOG)]
- Mask dilation by one beam  
  > "we dilated the mask by one beam (cite: dame2011)" (Appendix A Continuum masks) [from (cite: dame2011)]
- Projected Rayleigh statistic as the test of uniformity of relative gradient orientations  
  > "using the projected Rayleigh statistic (cite: durand1958; Jow2018)" (4.3 Morphological analysis with astroHOG) [from (cite: durand1958; Jow2018)]

### Not stated but needed to reproduce (our reading)

- tclean/imaging parameters of the ALMAGAL 7m+tm2 cubes (weighting, robust, cell size, image size, deconvolver, masks, beam, rms): only in the ALMAGAL pipeline paper
- CASA / pipeline version used for the cubes and continuum maps
- Which archive or ALMAGAL release provides the 7m+tm2 cubes and continuum maps used (the joint-deconvolved products are team-made)
- Gaussian-derivative FWHM (Omega) used by astroHOG for the gradients
- Sigma-clipping parameters used to build the noise maps and the number of Monte Carlo iterations beyond the stated 100
- Systemic velocity of each clump and the exact 4 sigma / 5 sigma noise definition (cube-wide standard deviation) used in the automated moment-0 routine
- Beam size and pixel scale per source (needed for N_beam and the weight delta/Delta)
- CuTEx run parameters and the 7m+tm2 core catalogue (announced as Coletta et al. in prep.)
- Per-source distances needed to convert mask areas to pc^2

## Analysis recipe

1. **Adopt ALMAGAL 7m+tm2 cubes and continuum maps**: Use the jointly deconvolved 7m+tm2 line cubes and 1.38 mm continuum maps from the ALMAGAL pipeline  
  > "we decided to analyze the cubes and continuum maps obtained by the joint deconvolution of" (Observations and data reduction)
   - software: ALMA pipeline, findcont
   - parameter: Chosen over 7m+tm2+tm1 for better signal-to-noise on diffuse large-scale emission  
  > "because they recover with a better signal-to-noise ratio the diffuse emission on large scales compared to the" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build moment-0 maps with automated velocity limits**: Per source and line: spatially resample cube, Gaussian-fit average and brightest-pixel spectra, set limits at +/-2 FWHM_max around fitted centre, extended where wing SNR falls below 0.5; CH3CN K=0,1 lines integrated into one map; 97 sources use a fixed +/-5 km/s range  
  > "we resampled spatially the cube on the two positions axis by a factor 6, the average number of pixels in a beam size" (Appendix B); "where the signal-to-noise ratio (SNR), starting from the center of the line, goes below 0.5" (Appendix B); "The number of sources for which the automated routine gave integration extremes that encompass all the line, without line blending problems, is 916, while for the remaining 97 sources we created the maps using a fixed velocity range." (4.1 Moment maps creation and detection)
   - parameter: Fixed-range fallback centred on clump systemic velocity  
  > "around the systemic velocity of the clump for all the pixels" (4.1 Moment maps creation and detection)
   - parameter: Blended CH3CN 12(0)-11(0) and 12(1)-11(1) lines combined in one moment-0 map  
  > "we created a single moment-0 map that includes the emission of both transitions" (4.1 Moment maps creation and detection)
   - assumption: Line profile approximated by a Gaussian to set the integration limits  
  > "and we fit it with a Gaussian profile" (Appendix B)
   - fitting: Gaussian fits (single, or two Gaussians with equal FWHM for CH3CN) to spectra  
  > "we fitted two Gaussian assuming they have the same FWHM" (Appendix B)
   - validation: All maps visually inspected against spectra averaged over each CuTEx compact source  
  > "All the maps for each field and transition were then visually inspected to validate them." (4.1 Moment maps creation and detection)
3. **Create moment-0 masks and decide line detection**: Mask pixels with SNR > 3 in the moment-0 map, drop regions with no pixel above SNR 5 or fewer than 0.8 N_beam pixels, declare detection if a region exceeds N_beam pixels; then tabulate detection rates by L/M bin  
  > "In the first step of the mask creation we select all of the pixels above a SNR of 3." (Appendix A Moment-0 masks); "excluded the regions that do not have any pixel with SNR above 5" (Appendix A Moment-0 masks); "We required that at least one of the regions remaining inside the mask has a number of pixels" (4.2 Detection and mask on moment-0 maps)
   - parameter: L/M divided into 5 ranges for detection statistics  
  > "we divided them into 5 ranges, to explore also very young sources" (5.1 Statistics of detections on moment-0 maps)
   - fitting: _not stated_
   - validation: CH3OCHO detections checked by eye in core spectra; 29 false detections removed, leaving 110  
  > "leaving 110 sources with a real detection" (4.2 Detection and mask on moment-0 maps)
4. **Define extended and compact continuum masks**: mask_com from CuTEx compact sources (ellipses of 2 sigma semi-axes, peak > 5 x rms); mask_ext from continuum SNR > 3 with isolated regions < 0.8 N_beam removed, dilated by one beam, and mask_com added  
  > "individuates compact sources inside continuum maps building a curvature image by double-differentiation of the initial map in four different directions" (Appendix A Continuum masks); "we required that the background-subtracted peak flux from photometry is higher than 5 times the map rms to confirm the compact source" (Appendix A Continuum masks); "is defined as the continuum emission with a SNR higher than 3" (Appendix A Continuum masks)
   - software: CuTEx
   - parameter: Noise map built from the continuum image not corrected for the primary beam  
  > "we build a map of noise by estimating the noise level of the continuum image not corrected for the primary beam" (Appendix A Continuum masks)
   - parameter: Ellipses recover 86% of source integral  
  > "to recover the 86% of the integral of the source" (Appendix A Continuum masks)
   - parameter: Dilation of mask_ext by one beam  
  > "As third step we dilated the mask by one beam (cite: dame2011)" (Appendix A Continuum masks)
   - fitting: 2D elliptical Gaussians plus constant or inclined-plane background fitted by CuTEx  
  > "Identified peaks in curvature maps are then fitted (on the original map) with 2D elliptical Gaussians plus a background" (Appendix A Continuum masks)
   - validation: _not stated_
5. **Build intersection masks and quantify area coverage**: Restrict comparison to intersection of moment-0 mask with mask_ext, and to compact sources at least 60% covered by line emission; require minimum areas in beams  
  > "we took all the compact sources that have at least 60% of their area covered also by line emission, and checked that the pixels in the masks cover at least three times the area of the beam" (4.4 Details of the application of astroHOG); "we performed the analysis only if the intersection with the mask of moment-0 covers at least 5 times the area of the beam" (4.4 Details of the application of astroHOG)
   - parameter: For 6 sources with mask_ext < 2 x mask_com, only mask_com was used  
  > "For these 6 sources we considered only the mask" (4.4 Details of the application of astroHOG)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute HOG normalized projected Rayleigh statistic V_N**: astroHOG computes gradient orientation angles between continuum and moment-0 maps inside the masks, then the projected Rayleigh statistic V normalised by V_max to V_N in [-1,1]; V_N read as the fraction of the area with parallel gradients; errors from Monte Carlo noise realisations  
  > "uses tools from circular statistics to quantify the significance of the accordance of the orientation between the intensity gradients" (4.3 Morphological analysis with astroHOG); "we introduced a normalized projected Rayleigh statistic" (4.3 Morphological analysis with astroHOG); "thus the percentage of the maps that is morphologically similar" (4.3 Morphological analysis with astroHOG)
   - software: astroHOG
   - parameter: Constant statistical weight w = delta/Delta (pixel size over beam size) because angles within a beam are not independent  
  > "we use the statistical weights to account for the fact that different values of" (4.3 Morphological analysis with astroHOG)
   - parameter: 100 Monte Carlo realisations to derive the error on V_N  
  > "we used the MC method calculating 100 times" (4.4 Details of the application of astroHOG)
   - assumption: Monte Carlo noise images are uncorrelated below the beam, unlike real interferometric noise (real noise correlation below 3%)  
  > "The noise maps considered in the MC method are not correlated below the beam size, unlike the noise of interferometric maps." (4.4 Details of the application of astroHOG)
   - fitting: _not stated_
   - validation: V_N on 50 pairs of noise-only moment-0 maps gives MAD 0.6% and all values below 3%; V_N above 0.02 treated as significant  
  > "The median absolute deviation of the correlation of noise-only maps is 0.6%, with all the values being below 3%." (Appendix C); "deviate from the statistical correlation that can be found running astroHOG on noise maps (see Appendix C), and are considered significant" (5.3 astroHOG results)
7. **Compare HOG with Spearman and Pearson coefficients**: Compute Spearman (and Pearson) correlation between moment-0 and continuum pixel intensities on the same masks and compare with V_N  
  > "using the same masks used for the HOG method" (5.4 Comparison with Spearman correlation coefficient); "no underlying linear relation is assumed, and it is defined as" (5.4 Comparison with Spearman correlation coefficient)
   - fitting: _not stated_
   - validation: Worked examples of discordant sources (AG019.8843-0.5337, AG332.7016-0.5870)  
  > "which means that even if there is a good level of correlation in the intensity of the continuum and the molecular species, the two emissions do not have a similar morphology" (5.4 Comparison with Spearman correlation coefficient)
8. **Robustness tests on subsets**: Repeat the HOG analysis excluding sources with CORNISH counterparts, and using only the 97 sources with fixed-range moment-0 maps  
  > "we present in Appendix E the same results from the HOG analysis excluding the sources associated with a CORNISH counterparts" (4.4 Details of the application of astroHOG)
   - fitting: _not stated_
   - validation: Medians show no significant variation from the main results  
  > "shows no significant variation from the main results of Fig." (5.3 astroHOG results)

## Software

- **astroHOG** : Histogram of oriented gradients comparison of continuum and moment-0 maps, V and V_N with Monte Carlo errors  
  > "uses tools from circular statistics to quantify the significance of the accordance of the orientation between the intensity gradients" (4.3 Morphological analysis with astroHOG)
- **CuTEx** : Extraction of compact continuum sources used to build mask_com  
  > "individuates compact sources inside continuum maps building a curvature image by double-differentiation of the initial map in four different directions" (Appendix A Continuum masks)
- **findcont** : Starting point of an iterative continuum-channel determination in the ALMAGAL pipeline  
  > "to refine the determination of the continuum channels used to create the continuum images and the line-only cubes" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources analysed | 1013 | not stated | sources | 0 | A total of 1013 targets have been analyzed in the present paper |
| Detections H2CO 3(0,3)-2(0,2) | 772 (76.2%) | not stated | sources (percent of 1013) | 3 | 772 (76.2%) |
| Detections SiO 5-4 | 582 (57.5%) | not stated | sources (percent of 1013) | 3 | 582 (57.5%) |
| Detections DCN 3-2 | 423 (41.8%) | not stated | sources (percent of 1013) | 3 | 423 (41.8%) |
| Detections CH3OCHO 17(3,14)-16(3,13) E | 110 (10.9%) | not stated | sources (percent of 1013) | 3 | 110 (10.9%) |
| Detections HCCCN 24-23 | 371 (36.6%) | not stated | sources (percent of 1013) | 3 | 371 (36.6%) |
| Detections CH3OH 4(2,3)-3(1,2) | 607 (59.9%) | not stated | sources (percent of 1013) | 3 | 607 (59.9%) |
| Detections H2CO 3(2,1)-2(2,0) | 569 (56.2%) | not stated | sources (percent of 1013) | 3 | 569 (56.2%) |
| Detections SO 6(5)-5(4) | 650 (64.2%) | not stated | sources (percent of 1013) | 3 | 650 (64.2%) |
| Detections CH3CN 12-11 K=0,1 | 353 (34.9%) | not stated | sources (percent of 1013) | 3 | 353 (34.9%) |
| Sources where automated moment-0 routine succeeded / failed (fixed range used) | 916 / 97 | not stated | sources | 2 | is 916, while for the remaining 97 sources we created the maps using a fixed velocity range |
| Sources with fraction of mask_ext covered by line emission above 25% (H2CO 3(0,3), SO, CH3OH, H2CO 3(2,1)) | 66%, 40%, 38%, 27% | not stated | percent of detected sources | 5 | In particular the percentage is of 66%, 40%, 38%, and 27% for |
| Median V_N on mask_ext, H2CO (both) and CH3OH | 0.27-0.29 | not stated | dimensionless | 6 | have similar median values, 0.27-0.29 (27-29%) |
| Median V_N on mask_ext, SO | 0.24 | not stated | dimensionless | 6 | while the median morphological correlation of SO with the continuum at the diffuse scale is 0.24 (24%) |
| Median V_N on mask_ext, SiO | 0.15 | not stated | dimensionless | 6 | with a median value of 0.15 (15%) |
| Median V_N on mask_ext, CH3OCHO (17 sources) | 0.84 | not stated | dimensionless | 6 | we found a value of 0.84 (84%) |
| Median V_N on mask_com, SiO | 0.35 | not stated | dimensionless | 6 | with a median correlation of 0.35 (35%) |
| Median V_N on mask_com, H2CO, CH3OH, SO | around 40% | not stated | dimensionless (percent) | 6 | we found median correlation values of around 40% |
| Median V_N on mask_com, HCCCN, CH3CN, DCN | 62%-65% | not stated | dimensionless (percent) | 6 | the value of the normalized projected Rayleigh statistic is in the range 62%-65% |
| Median V_N on mask_com, CH3OCHO | 87% | not stated | dimensionless (percent) | 6 | has a median value of 87% |
| H2CO V_N on mask_com rising from the 3(0,3)-2(0,2) to the 3(2,1)-2(2,0) transition | 31% to 45% | not stated | dimensionless (percent) | 6 | (from 31% to 45%) is seen at the scale of the compact sources |
| V_N on noise-only map pairs: median absolute deviation | 0.6%, all values below 3% | not stated | dimensionless (percent) | 8 | The median absolute deviation of the correlation of noise-only maps is 0.6%, with all the values being below 3%. |
| CORNISH-matched clumps | 112 | not stated | clumps | 8 | We identified 112 matched clumps, mostly evolved clumps |

## Qualitative findings

- SiO emission, unlike other outflow tracers, often does not cover the extended continuum area; SiO and SO do not trace the same gas  
  > "unlike other outflow tracers, SiO in a large fraction of the sources does not cover well the area of the extended continuum emission" (abstract)
- Intensity-based Spearman coefficient can give a moderate/high correlation where gradients show little morphological similarity  
  > "which means that even if there is a good level of correlation in the intensity of the continuum and the molecular species, the two emissions do not have a similar morphology" (5.4 Comparison with Spearman correlation coefficient)
- Difference between the two molecule groups is attributed to molecular species, with some transition dependence especially on the compact mask  
  > "This leads us to conclude that the difference between the two groups of molecular transitions is related to the molecular species." (5.3 astroHOG results); "We can see that a dependence on the selected transition is present." (5.3 astroHOG results)

## Claim tuples

- H: Do H2CO, CH3OH and SO, which cover the extended continuum, trace its morphology? | E: astroHOG V_N between moment-0 maps and the 1.38 mm continuum on mask_ext | R: Median V_N about 0.24-0.29 | F: These transitions correlate only weakly with the diffuse dust emission and probably trace clump medium, outer layers or outflows | **supported**
- H: Which species trace the dense fragments? | E: astroHOG V_N on mask_com (compact CuTEx sources) | R: DCN, HC3N, CH3CN and CH3OCHO give V_N of about 62-65% (87% for CH3OCHO); H2CO, CH3OH, SO about 40%; SiO 35% | F: DCN, HC3N, CH3CN and CH3OCHO follow the dense fragments; SiO correlates worst | **supported**
- H: Do SiO and SO trace the same gas? | E: Compare area coverage of mask_ext and V_N for the two outflow tracers | R: SiO covers less of the extended continuum and has lower V_N than SO | F: SiO and SO do not trace the same gas | **supported**
- H: Does a gradient-based HOG measure compare morphology better than an intensity-based coefficient? | E: Compare V_N with Spearman and Pearson coefficients on the same masks | R: Positive trend with large scatter and some clearly contradictory sources | F: HOG is to be preferred for morphology; intensity coefficients answer whether tracers peak together | **supported**
- H: Does the morphological correlation depend on the evolutionary stage (L/M) of the clump? | E: V_N medians in three L/M bins | R: Distributions are consistent within errors except HCCCN and CH3CN at L/M < 1 in mask_ext, based on 10 or fewer sources | F: No clear dependence on clump L/M, possibly because clumps mix cores of different stages | **partially**

## Reasoning

- Why this data: 7m+tm2 products chosen over 7m+tm2+tm1 for better S/N on diffuse emission; 13CO and C18O excluded because emission fills the FOV  
  > "because they recover with a better signal-to-noise ratio the diffuse emission on large scales compared to the" (Observations and data reduction); "we excluded from the analysis these two tracers since in most cases their emission covers the entire FOV of the observations" (2.2 Molecular transitions analyzed)
- Why this method: HOG compares total morphology rather than pixel-by-pixel intensity  
  > "a more sophisticated approach that compares the total morphology of the emission and not only the intensity pixel by pixel, as usually done so far" (Introduction)
- Alternative: 13CO and C18O excluded because of FOV-filling emission and cleaning artefacts  
  > "we excluded from the analysis these two tracers since in most cases their emission covers the entire FOV of the observations" (2.2 Molecular transitions analyzed)
- Alternative: CORNISH-matched clumps (possible free-free) not excluded from the main analysis, only tested separately  
  > "We do not exclude those clumps from the main analysis presented in the paper" (4.4 Details of the application of astroHOG)
- Alternative: Sources with possibly optically thick lines not excluded  
  > "therefore we do not exclude sources due to optical depth consideration" (4.4 Details of the application of astroHOG)
- How they decided it was enough: Significance threshold for V_N set from noise-only pairs  
  > "deviate from the statistical correlation that can be found running astroHOG on noise maps (see Appendix C), and are considered significant" (5.3 astroHOG results)
- Limitation (authors): Outflow emission is not disentangled from the masks  
  > "would require a prior dedicated study on outflows to obtain the region covered by it, which is beyond the scope of this paper" (4.4 Details of the application of astroHOG)
- Limitation (authors): HOG is blind to peak position and size  
  > "since this method relies only on the relative orientation of the gradients, it is not sensitive to investigate if two tracers peak in the same position" (4.3 Morphological analysis with astroHOG)
- Limitation (authors): Continuum may contain free-free emission  
  > "is not only due to thermal dust emission, but may have a contribution from free-free emission" (4.4 Details of the application of astroHOG)
- Limitation (authors): Extended emission may be missed in faint sources  
  > "In some cases, especially for fainter sources, part of the extended emission might not be recovered due to the sensitivity limitation." (4.4 Details of the application of astroHOG)
- Limitation (authors): Monte Carlo noise is uncorrelated below the beam unlike real interferometric noise  
  > "The noise maps considered in the MC method are not correlated below the beam size, unlike the noise of interferometric maps." (4.4 Details of the application of astroHOG)
- Caveat (inferred, ours): Main inputs are team-processed ALMAGAL 7m+tm2 products, not archive products, so exact reproduction needs the ALMAGAL release
- Caveat (inferred, ours): Linear resolution ~5000 au for 7m+tm2 means 'compact sources' are clump fragments, not cores, and beam size in pc differs among sources
- Caveat (inferred, ours): Selection thresholds appear inconsistent: text gives 5 beams for the mask_ext intersection while the Table D.1 note says 10 beams for the largest region, and the 'first 40' versus 'first 37' sources
- Caveat (inferred, ours): V_N values depend on mask choice, the gradient smoothing scale Omega (not given) and noise-level handling
- Caveat (inferred, ours): Line optical depth and outflow contamination are not controlled, and fixed-range moment maps for 97 sources truncate wings
- Caveat (inferred, ours): Differing sensitivities per line shape which sources enter each statistic, so medians are over varying sub-samples

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: astroHOG code on GitHub (solerjuan/astroHOG)  
  > "code available through GitHub at" (Footnote 1)
- Code: Full V_N, Pearson and Spearman tables for all transitions on Zenodo (doi 10.5281/zenodo.15236491)  
  > "The full version of this table is available through Zenodo (https://doi.org/10.5281/zenodo.15236491)." (Appendix D)
- Missing: Public location and version of the ALMAGAL 7m+tm2 jointly deconvolved cubes and continuum maps
- Missing: ALMAGAL pipeline imaging parameters and CASA version
- Missing: astroHOG run parameters (gradient FWHM Omega, MC settings)
- Missing: 7m+tm2 CuTEx core catalogue (in prep.)
- Missing: Per-source velocity ranges used in the automated moment-0 routine and per-source distances
- Data volume (inferred): Inferred, uncertain: 1013 fields x 4 spectral windows of 7m+tm2 cubes plus continuum maps, probably hundreds of GB to a few TB
- Score (inferred): 3/5, astroHOG is public and the masks and moment-0 recipe are described in detail with Zenodo tables, but the input cubes come from an unpublished-in-this-paper team pipeline and several parameters (gradient scale, imaging settings, data release) are missing.
- Rediscovery candidate: no, The paper does not state that the 7m+tm2 team-processed products used are public, and key imaging and astroHOG parameters are missing, although results are numeric.

## Links

- Method: (cite: ALMAGAL2) (ALMAGAL data reduction pipeline, joint deconvolution and continuum channel determination)
- Method: (cite: soler_astroHOG) (Histogram of oriented gradients method and astroHOG implementation)
- Method: (cite: cutexMolinari+11) (CuTEx compact source extraction algorithm)
- Companion: (cite: ALMAGAL1) (ALMAGAL survey and sample description)
- Companion: (cite: ALMAGAL3) (Fragmentation properties and CuTEx methodology)
- Companion: (cite: molly2024) (Accretion flows traced by H2CO in a subsample of ALMAGAL sources)
- Related: ALMAGAL (2019.1.00195.L)
- Related: Hi-GAL
- Related: CORNISH

## Checks

```json
{
 "quotes": 129,
 "quotes_ok": 129,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 23,
 "numeric_problems": 0,
 "fill": {
  "facts": 105,
  "stated": 69,
  "rate": 0.657
 },
 "evidence_ok": true
}
```
