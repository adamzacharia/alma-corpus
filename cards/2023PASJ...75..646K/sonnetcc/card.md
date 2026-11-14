# Investigating physical states of molecular gas in the overlapping region of interacting galaxies NGC 4567/4568 using ALMA

`2023PASJ...75..646K` | Publications of the Astronomical Society of Japan 2023 | first author: Kaneko, Hiroyuki | arXiv: 2303.17638 | DOI: 10.1093/pasj/psad025

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Do molecular clouds in the filament and overlapping region of the early-stage interacting pair NGC 4567/4568 show higher virial parameters and a higher CO(3-2)/CO(1-0) ratio (denser gas) than disc clouds, as simulations of collisional compression predict?  
  > "In this study, we investigate the physical states of a filamentary molecular structure at the overlapping region, which was previously reported." (abstract); "This result contradicts the predictions of previous numerical simulations, which suggested that the molecular gas on the collision front of galaxies is compressed and becomes denser." (abstract)
- Target **NGC 4567/4568**: coordinates _not stated_; z/distance 16 Mpc  
  > "the close proximity (16 Mpc: (cite: Mei07))" (Introduction); "relatively large projected nuclear separation (5.6 kpc)" (Introduction); distance from Mei et al. 2007 (cite: Mei07)  
  > "the close proximity (16 Mpc: (cite: Mei07))" (Introduction); "relatively large projected nuclear separation (5.6 kpc)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01161.S, 2012.1.00759.S
- bands: Band 3 (CO 1-0), Band 7 (CO 3-2)  
  > "Forty-nine 12-m array and nine Atacama Compact Array (ACA) 7-m array antennas were used for CO($J$ = 1–0) observations with the Band 3 receiver" (Observations and data reduction); "thirty-seven 12-m antennas and eight ACA 7-m antennas were used for CO($J$ = 3–2) observations with the Band 7 receiver" (Observations and data reduction)
- frequencies and spectral setup: CO(1-0) rest frequency 115.271 GHz; CO(3-2) rest frequency 345.796 GHz; velocity resolution 5 km/s for both cubes; CO(1-0) single field, CO(3-2) mosaic of three fields  
  > "at 115.271 GHz (the rest frequency of CO($J$ = 1–0)) are 50.5 and 86.6 arcsec, respectively, and those at 345.796 GHz (the rest frequency of CO($J$ = 3–2))" (Observations and data reduction); "The CO($J$ = 1–0) data were obtained in a single field of view, whereas the CO($J$ = 3–2) data were obtained in a mosaic of three fields of view" (Observations and data reduction); "and a velocity resolution of 5 km s$^{-1}$" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array and ACA 7-m array (49 + 9 antennas in Band 3; 37 + 8 antennas in Band 7)  
  > "Forty-nine 12-m array and nine Atacama Compact Array (ACA) 7-m array antennas were used for CO($J$ = 1–0) observations with the Band 3 receiver" (Observations and data reduction); "thirty-seven 12-m antennas and eight ACA 7-m antennas were used for CO($J$ = 3–2) observations with the Band 7 receiver" (Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(1-0): 126 pc x 99 pc at 16 Mpc (combined cube); CO(3-2): 43 pc x 36 pc at 16 Mpc (arcsec beam values not legible in the text)  
  > "(126 pc$\times$99 pc at 16 Mpc)" (Observations and data reduction); "(43 pc $\times$ 36 pc at 16 Mpc)" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 1.5 mJy/beam in both CO(1-0) and CO(3-2) cubes (CO(1-0): 0.067 mK); CO(1-0) disc region 4.0 mJy/beam  
  > "the root mean square (rms) noise of 1.5 mJy beam$^{-1}$ (0.067 mK) was obtained" (Observations and data reduction); "The rms noise for CO($J$ = 3–2) is 1.5 mJy beam$^{-1}$." (Observations and data reduction)
- time on source: CO(1-0): 3.71 hours total observation time; CO(3-2): 0.52 hours total observation time  
  > "CO($J$ = 1–0) observations were conducted in January, May and June 2016 with a total observation time of 3.71 hours" (Observations and data reduction); "the CO($J$ = 3–2) observations were carried out in May–July 2016 with a total observation time of 0.52 hours" (Observations and data reduction)
- observing dates: CO(1-0): January, May and June 2016; CO(3-2): May-July 2016  
  > "CO($J$ = 1–0) observations were conducted in January, May and June 2016 with a total observation time of 3.71 hours" (Observations and data reduction); "the CO($J$ = 3–2) observations were carried out in May–July 2016 with a total observation time of 0.52 hours" (Observations and data reduction)
- pi or archival as stated: Own Cycle 3 program (PI: Hiroyuki Kaneko); a Cycle 1 ALMA program (2012.1.00759.S per acknowledgements) is also used  
  > "We observed NGC 4567/4568 using ALMA as a Cycle 3 program (ID: 2015.1.01161.S, PI: Hiroyuki Kaneko)." (Observations and data reduction); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01161.S and ADS/JAO.ALMA#2012.1.00759.S." (Acknowledgements)
- Line: CO J = 1-0 (115.271 GHz)
- Line: CO J = 3-2 (345.796 GHz)
- Other facility **Nobeyama 45-m telescope**: Single-dish CO(1-0) data used to estimate the missing flux of the ALMA Cycle 3 CO(1-0) data (63%) and for galaxy-scale CO contours overlaid on the HI image  
  > "we estimated the missing flux for CO($J$ = 1–0) in Cycle 3 using data obtained with the Nobeyama 45-m telescope (cite: Kaneko13)" (Observations and data reduction); "overlaid with CO($J$ = 1–0) contours obtained by the Nobeyama 45-m telescope (cite: Kaneko13)" (Discussion)
- External data: Distance to the galaxy pair, 16 Mpc  
  > "the close proximity (16 Mpc: (cite: Mei07))" (Introduction) [from Mei et al. 2007 (cite: Mei07)]
- External data: CO-to-H2 conversion factor XCO = 2.0 x 10^20 cm^-2 (K km/s)^-1  
  > "Adopting $X_{\rm CO}$ = 2.0 $\times$ 10$^{20}$" (3.1 CO(J = 1-0)) [from Bolatto et al. 2013 (cite: Bolatto13)]
- External data: Earlier ALMA Cycle 1 CO(1-0) data and filament cloud properties (four clouds, alpha_vir 0.18 +/- 0.10, radius 30.8 +/- 5.8 pc, sigma 3.3 +/- 2.0 km/s) used for comparison and for 3D-BAROLO modelling  
  > "their radius and velocity dispersion are 30.8 $\pm$ 5.8 pc and 3.3 $\pm$ 2.0 km s$^{-1}$, respectively" (4.2 Physical properties of molecular clouds); "compare them with the observed data of each galaxy pair obtained in the ALMA Cycle 1 program" (4.4 Evolutionary and collisional stages) [from Kaneko et al. 2018 (cite: Kaneko18)]
- External data: Total molecular gas mass of the pair and Nobeyama 45-m CO(1-0) data  
  > "Since the total amount of molecular gas of the NGC 4567/4568 pair is" (3.1 CO(J = 1-0)) [from Kaneko et al. 2013 (cite: Kaneko13)]
- External data: HI image of the pair  
  > "image (cite: Iono05) overlaid with CO($J$ = 1–0) contours obtained by the Nobeyama 45-m telescope" (4.3 Formation process of the filamentary molecular structure) [from Iono et al. 2005 (cite: Iono05)]
- External data: HI deficiency of NGC 4567 (0.13 +/- 0.12) and NGC 4568 (0.38 +/- 0.12)  
  > "(cite: Chung09) estimated that NGC 4567 and NGC 4568 have H deficiency of 0.13 $\pm$ 0.12 and 0.38 $\pm$ 0.12, respectively." (4.3 Formation process of the filamentary molecular structure) [from Chung et al. 2009 (cite: Chung09)]
- External data: H-alpha image used as star formation tracer  
  > "a star formation tracer, H$\alpha$ (cite: Xu00)" (4.2 Physical properties of molecular clouds) [from Xu et al. 2000 (cite: Xu00)]
- Simulation/model as data: 3D-BAROLO circular-motion kinematic models of each galaxy compared with the ALMA Cycle 1 data  
  > "we create kinematic models using 3D-BAROLO (cite: DiTeodoro15), assuming a circular motion" (4.4 Evolutionary and collisional stages)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: about 5% (Band 3) and 10% (Band 7), both sidebands  
  > "The systematic error on the absolute flux is estimated to be approximately 5 and 10% for both sidebands in Band 3 and Band 7, respectively." (Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: CASA tclean, interactive  
  > "The imaging process was conducted interactively using the *tclean* task with Briggs weighting (using a robustness parameter of 0.5)." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The imaging process was conducted interactively using the *tclean* task with Briggs weighting (using a robustness parameter of 0.5)." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: CO(1-0): 256 x 256 pixels; CO(3-2): 500 x 500 pixels (grid sizes not legible in the text)  
  > "The final data of CO($J$ = 1–0) were imaged on a 256 $\times$ 256 pixel with a grid size of" (Observations and data reduction); "CO($J$ = 3–2) were imaged on a 500 $\times$ 500 pixel with a grid size of" (Observations and data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "To image the CO lines, we performed continuum subtraction using the *uvcontsub* task and subsequently corrected for primary beam attenuation." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: applied after imaging (primary beam attenuation corrected)  
  > "To image the CO lines, we performed continuum subtraction using the *uvcontsub* task and subsequently corrected for primary beam attenuation." (Observations and data reduction)
- array combination: 12-m and ACA 7-m data combined for CO(1-0); combined cube also for CO(3-2)  
  > "The 12-m array data and the ACA 7-m array data for CO($J$ = 1–0) were combined together." (Observations and data reduction); "The resulting combined data cube has an angular resolution of" (Observations and data reduction)
- smoothing: CO(3-2) convolved and re-gridded to the lower-resolution CO(1-0) image for the overlay comparison  
  > "after convolving and re-gridding the CO($J$ = 3–2) data to match the lower resolution CO($J$ = 1–0) image" (3.2 CO(J = 3-2))
- final beam: _not stated_
- final rms: 1.5 mJy/beam (CO 1-0 and CO 3-2)  
  > "the root mean square (rms) noise of 1.5 mJy beam$^{-1}$ (0.067 mK) was obtained" (Observations and data reduction); "The rms noise for CO($J$ = 3–2) is 1.5 mJy beam$^{-1}$." (Observations and data reduction)

### Inherited from earlier work

- Luminosity mass of the observed region from the CO(1-0) flux  
  > "We derived the luminosity mass of the observed region from the CO($J$ = 1–0) flux using the following equation (cite: Kenney98)" (3.1 CO(J = 1-0)) [from (cite: Kenney98)]
- Virial parameter definition alpha_vir = 5 sigma^2 R / (G M_CO)  
  > "We calculated the virial parameter $\alpha_{\rm vir}$ for the clouds using the following equation (cite: Bertoldi92)" (4.2 Physical properties of molecular clouds) [from (cite: Bertoldi92)]
- Bound-cloud criterion alpha_vir less than about 1  
  > "the cloud is considered to be gravitationally bound (cite: Kauffmann13)" (4.2 Physical properties of molecular clouds) [from (cite: Kauffmann13)]
- Cloud identification with the CLUMPFIND algorithm  
  > "The CLUMPFIND algorithm (cite: Williams94) is employed for this purpose" (4.1 Molecular cloud identification) [from (cite: Williams94)]
- Missing flux of CO(1-0) estimated against Nobeyama 45-m data  
  > "we estimated the missing flux for CO($J$ = 1–0) in Cycle 3 using data obtained with the Nobeyama 45-m telescope (cite: Kaneko13)" (Observations and data reduction) [from (cite: Kaneko13)]
- Filament discovered earlier and used as the object of study  
  > "the filamentary molecular structure, which was discovered by (cite: Kaneko18), is visible" (Results) [from (cite: Kaneko18)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the standard pipeline or manual scripts were used
- Flux calibrator and any flux-scale corrections
- Whether self-calibration was applied
- Line-free channels and fit order used in uvcontsub
- tclean deconvolver, cell size, interactive mask choices, stopping threshold, and primary-beam cutoff for the CO(3-2) mosaic
- Beam sizes in arcsec and position angles (not legible in the provided text)
- How the 12-m and ACA visibilities were weighted or combined, and the CO(3-2) mosaic setup
- CLUMPFIND implementation and version, and exact deconvolution of radius and velocity dispersion
- How cloud pixels were matched between the CO(1-0) and CO(3-2) cubes for R3-2/1-0 (beam matching, masks) and how its uncertainty was derived
- Reduction details of the Cycle 1 data (2012.1.00759.S) used for comparison and 3D-BAROLO input
- 3D-BAROLO parameters (rings, inclination, position angle, systemic velocity) and the HI image source data

## Analysis recipe

1. **calibrate and image the CO(1-0) and CO(3-2) cubes**: Calibration and imaging in CASA; continuum undetected; continuum subtraction with uvcontsub; primary beam correction; tclean with Briggs weighting; 12-m and ACA combined  
  > "Data reduction, including calibration and imaging, was executed with the Common Astronomy Software Applications (CASA) package (cite: CASA22)." (Observations and data reduction); "Initially, the 3-mm and 1-mm continuum emission were scrutinized and found to be undetected." (Observations and data reduction)
   - software: CASA, tclean, uvcontsub
   - parameter: Briggs robust = 0.5  
  > "using the *tclean* task with Briggs weighting (using a robustness parameter of 0.5)" (Observations and data reduction)
   - parameter: velocity resolution 5 km/s  
  > "and a velocity resolution of 5 km s$^{-1}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **make moment maps and measure integrated intensities and luminosity mass**: Moment maps clipped at 3 sigma (CO 3-2 integrated intensity) and 5 sigma (velocity field and dispersion); luminosity mass from CO(1-0) flux with the Kenney and Young relation  
  > "The integrated intensity map was clipped at 3 $\sigma$, whereas the velocity field and the velocity dispersion map were clipped at 5 $\sigma$" (3.2 CO(J = 3-2)); "We derived the luminosity mass of the observed region from the CO($J$ = 1–0) flux using the following equation (cite: Kenney98)" (3.1 CO(J = 1-0))
   - parameter: clip level 5 sigma on CO(1-0) velocity field and dispersion maps (1 sigma = 1.5 mJy/beam)  
  > "The velocity field and velocity dispersion maps were clipped at 5 $\sigma$ (1 $\sigma$ = 1.5 mJy beam$^{-1}$)." (3.1 CO(J = 1-0))
   - assumption: XCO = 2.0 x 10^20 cm^-2 (K km/s)^-1; distance 16 Mpc  
  > "Adopting $X_{\rm CO}$ = 2.0 $\times$ 10$^{20}$" (3.1 CO(J = 1-0)); "the close proximity (16 Mpc: (cite: Mei07))" (Introduction)
   - fitting: _not stated_
   - validation: Missing flux estimated with Nobeyama 45-m data; mass treated as a lower limit  
  > "found that the missing flux accounts for 63% of the total flux" (Observations and data reduction); "Note that the derived mass is the lower limit due to missing flux." (3.1 CO(J = 1-0))
3. **build position-velocity diagrams across the filament**: P-V diagrams perpendicular to the filament from the CO(1-0) cube  
  > "we created position-velocity (P–V) diagrams that are perpendicular to the filament using CO($J$ = 1–0) data" (3.3 Position-Velocity Diagram)
   - fitting: _not stated_
   - validation: _not stated_
4. **identify molecular clouds in the CO(1-0) cube and assign them to regions**: CLUMPFIND in 3D with contour levels starting at 3 sigma and spaced by 2 sigma; separate noise levels for overlapping and disc regions; filament membership from position and P-V velocity criteria  
  > "We set the minimum level of contour lines at 3 $\sigma$ and the interval of contour lines at 2 $\sigma$." (4.1 Molecular cloud identification); "The rms noise of 1 $\sigma$ = 1.5 mJy beam$^{-1}$ is used for the overlapping region, and 1 $\sigma$ = 4.0 mJy beam$^{-1}$ is used for the disc region." (4.1 Molecular cloud identification)
   - software: CLUMPFIND
   - parameter: cloud must exceed beam size (~100 pc) and the 5 km/s velocity resolution; clouds truncated at the field edge excluded  
  > "A molecular cloud is defined as having a size larger than the beam size ($\sim$100 pc) and a velocity width larger than the velocity resolution (5 km s$^{-1}$)." (4.1 Molecular cloud identification); "we exclude those truncated at the edge of the field of view" (4.1 Molecular cloud identification)
   - parameter: filament defined as integrated intensity > 0.5 Jy km/s in the white box and emission above 4.5 mJy/beam (3 sigma) in the P-V diagram  
  > "The filament is defined as the area with CO($J$ = 1–0) integrated intensity of $>$ 0.5 Jy km s$^{-1}$ in the white box of figure" (4.1 Molecular cloud identification)
   - fitting: _not stated_
   - validation: Compared the number of filament clouds with the earlier Cycle 1 study (four clouds)  
  > "who identified a total of four molecular clouds in the same region" (4.1 Molecular cloud identification)
5. **derive cloud physical properties and virial parameters**: Radius and velocity dispersion from CLUMPFIND after deconvolution; luminosity mass from CO(1-0) integrated intensity, projected area and XCO; surface density = mass / area for a spherical cloud; alpha_vir = 5 sigma^2 R / (G M_CO)  
  > "Radius and velocity dispersion were calculated after deconvolution during CLUMPFIND." (4.2 Physical properties of molecular clouds); "We calculated the virial parameter $\alpha_{\rm vir}$ for the clouds using the following equation (cite: Bertoldi92)" (4.2 Physical properties of molecular clouds)
   - software: CLUMPFIND
   - parameter: XCO = 2.0 x 10^20 cm^-2 (K km/s)^-1  
  > "We adopt $X_{\rm CO}$ = 2.0 $\times$ 10$^{20}$" (4.2 Physical properties of molecular clouds)
   - assumption: cloud treated as a sphere for mass surface density; alpha_vir below about 1 means gravitationally bound  
  > "assuming that the molecular cloud is a sphere" (4.2 Physical properties of molecular clouds); "the cloud is considered to be gravitationally bound (cite: Kauffmann13)" (4.2 Physical properties of molecular clouds)
   - fitting: _not stated_
   - validation: Typical uncertainty about 10% in luminosity mass and virial parameter, from the flux uncertainty  
  > "The typical uncertainties in the luminosity mass and the virial parameter are estimated to be $\sim$10%, mainly due to the flux uncertainty." (4.2 Physical properties of molecular clouds)
6. **compare cloud populations between disc and overlapping regions**: Two-sample Kolmogorov-Smirnov test on each cloud property at the 1% significance level  
  > "The Kolmogorov–Smirnov (K–S) test is used to determine whether the population of the distribution of each physical quantity" (4.2 Physical properties of molecular clouds); "(the significance level is 1%)" (4.2 Physical properties of molecular clouds)
   - fitting: _not stated_
   - validation: _not stated_
7. **measure CO(3-2)/CO(1-0) intensity ratio per cloud**: R3-2/1-0 = I(CO 3-2)/I(CO 1-0) from pixel values inside the clouds identified in the CO(1-0) cube; clouds in the disc region not plotted  
  > "we calculate the integrated intensity ratios using the pixel values in the molecular cloud identified using the CO($J$ = 1–0) cube data." (4.2 Physical properties of molecular clouds); "The clouds in the disc region are not plotted in figure" (4.2 Physical properties of molecular clouds)
   - fitting: _not stated_
   - validation: Compared with R3-2/1-0 from LIRGs, VV 114, M 33, the Milky Way and NGC 613 in the literature  
  > "Furthermore, $R_{3-2/1-0}$ in the overlapping region is comparable to the ratio of 0.10 found in the inter-arm region of NGC 613 (cite: Muraoka16)." (4.2 Physical properties of molecular clouds)
8. **test cluster stripping and compare CO with HI and H-alpha**: Compare galaxy-scale HI and CO distributions; split NGC 4568 into northern and southern discs using an ellipse fit to the HI 3 sigma level; compare HI mass in the two halves; overlay R3-2/1-0 with H-alpha  
  > "we divided NGC 4568 into two regions: the northern disc and the southern disc." (4.3 Formation process of the filamentary molecular structure); "Figure [10](#fig:R32-Ha) shows the $R_{3-2/1-0}$ image overlaid with H$\alpha$." (4.2 Physical properties of molecular clouds)
   - assumption: optically thin HI emission  
  > "Assuming the optically thin emission" (4.3 Formation process of the filamentary molecular structure)
   - fitting: ellipse fit to the HI image of NGC 4568 to reproduce the 3 sigma level  
  > "to reproduce the 3$\sigma$ level" (4.3 Formation process of the filamentary molecular structure)
   - validation: _not stated_
9. **model the disc kinematics and look for departures from circular motion**: 3D-BAROLO kinematic models assuming circular motion compared with the Cycle 1 CO(1-0) data of each galaxy  
  > "we create kinematic models using 3D-BAROLO (cite: DiTeodoro15), assuming a circular motion, and compare them with the observed data of each galaxy pair obtained in the ALMA Cycle 1 program" (4.4 Evolutionary and collisional stages)
   - software: 3D-BAROLO
   - assumption: circular motion  
  > "assuming a circular motion" (4.4 Evolutionary and collisional stages)
   - fitting: _not stated_
   - validation: Residuals checked for deviations from circular motion  
  > "Except for this distortion, there is no significant deviation from the circular motion, including the overlapping region" (4.4 Evolutionary and collisional stages)

## Software

- **CASA** : calibration and imaging of the ALMA data  
  > "Data reduction, including calibration and imaging, was executed with the Common Astronomy Software Applications (CASA) package (cite: CASA22)." (Observations and data reduction)
- **tclean** : interactive imaging with Briggs weighting, robust 0.5  
  > "The imaging process was conducted interactively using the *tclean* task with Briggs weighting (using a robustness parameter of 0.5)." (Observations and data reduction)
- **uvcontsub** : continuum subtraction before imaging the CO lines  
  > "we performed continuum subtraction using the *uvcontsub* task" (Observations and data reduction)
- **CLUMPFIND** : 3D molecular cloud identification in the CO(1-0) cube  
  > "The CLUMPFIND algorithm (cite: Williams94) is employed for this purpose" (4.1 Molecular cloud identification)
- **3D-BAROLO** : kinematic models assuming circular motion  
  > "we create kinematic models using 3D-BAROLO (cite: DiTeodoro15), assuming a circular motion" (4.4 Evolutionary and collisional stages)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(1-0) integrated intensity in the field of view | 205 | 3 | Jy km/s | 2 | The CO($J$ = 1–0) integrated intensity in the field of view is 205 $\pm$ 3 Jy km s$^{-1}$. |
| CO(1-0) luminosity mass of observed region | 4.1e8 | 0.1e8 | Msun | 2 | the luminosity mass is (4.1 $\pm$ 0.1) $\times$ 10$^{8}$ $M_\odot$ |
| Fraction of the pair's molecular gas in the observed region | 9% | not stated | percent | 2 | this corresponds to 9% of molecular gas of this pair |
| CO(1-0) missing flux fraction | 63% | not stated | percent | 2 | found that the missing flux accounts for 63% of the total flux |
| CO(3-2) integrated intensity | 7.4 | 1.0 | Jy km/s | 2 | The CO($J$ = 3–2) integrated intensity is 7.4 $\pm$ 1.0 Jy km s$^{-1}$. |
| CO(1-0) integrated intensity within the CO(3-2) field of view | 30 | 1 | Jy km/s | 2 | Within the CO($J$ = 3–2) field of view, the CO($J$ = 1–0) integrated intensity is 30$\pm$1 Jy km s$^{-1}$. |
| Global CO(3-2)/CO(1-0) intensity ratio | 0.25 | 0.03 | dimensionless | 2 | Therefore, the global CO($J$ = 3–2)/CO($J$ = 1–0) intensity ratio is 0.25 $\pm$ 0.03. |
| 3 sigma continuum upper limit, 3 mm | 1.7e-1 | not stated | mJy/beam | 1 | 1.7 $\times$ 10$^{-1}$ mJy beam$^{-1}$ |
| 3 sigma continuum upper limit, 1 mm | 2.4e-1 | not stated | mJy/beam | 1 | 2.4 $\times$ 10$^{-1}$ mJy beam$^{-1}$ |
| Molecular clouds identified (total) | 114 | not stated | clouds | 4 | We identified 114 molecular clouds using CO($J$ = 1–0) data. |
| Clouds per region: disc / overlapping (excl. filament) / filament | 62 / 44 / 8 | not stated | clouds | 4 | As a result, 62 molecular clouds are identified in the disc region, 44 molecular clouds in the overlapping region (excluding those in the filament), and eight molecular clouds associated with the filament. |
| Mean virial parameter, filament clouds | 0.56 | 0.14 | dimensionless | 5 | a factor of two higher an average virial parameter (0.56 $\pm$ 0.14) than that in the overlapping region (0.28 $\pm$ 0.12) and in the disc region (0.26 $\pm$ 0.16) |
| Mean virial parameter, overlapping-region clouds | 0.28 | 0.12 | dimensionless | 5 | a factor of two higher an average virial parameter (0.56 $\pm$ 0.14) than that in the overlapping region (0.28 $\pm$ 0.12) and in the disc region (0.26 $\pm$ 0.16) |
| Mean virial parameter, disc-region clouds | 0.26 | 0.16 | dimensionless | 5 | a factor of two higher an average virial parameter (0.56 $\pm$ 0.14) than that in the overlapping region (0.28 $\pm$ 0.12) and in the disc region (0.26 $\pm$ 0.16) |
| K-S p-values, radius and virial parameter (overlapping vs disc) | 0.23 and 0.67 | not stated | dimensionless | 6 | The *p*-values of the K–S test for the radius and virial parameters above 1%, specifically 0.23 and 0.67, respectively. |
| K-S p-values, velocity dispersion, luminosity mass, mass surface density | 1.9e-3, 3.1e-6, 2.8e-5 | not stated | dimensionless | 6 | precisely 1.9 $\times$ 10$^{-3}$, 3.1 $\times$ 10$^{-6}$, and 2.8 $\times$ 10$^{-5}$, respectively |
| Average R3-2/1-0 of clouds in the overlapping region | 0.05 | 0.04 | dimensionless | 7 | The average $R_{3-2/1-0}$ for each molecular cloud in the overlapping region is 0.05 $\pm$ 0.04. |
| Maximum R3-2/1-0 over all clouds | 0.17 | 0.04 | dimensionless | 7 | the maximum value of $R_{3-2/1-0}$ for all molecular clouds, including the overlapping region, is 0.17 $\pm$ 0.04 |
| R3-2/1-0 of filament clouds | less than 0.1 | not stated | dimensionless | 7 | All molecular clouds in the filaments have an $R_{3-2/1-0}$ of less than 0.1 |
| Correlation coefficient between CO(1-0) and CO(3-2) cloud integrated intensities | 0.84 | not stated | dimensionless | 7 | The correlation coefficient between CO($J$ = 1–0) and CO($J$ = 3–2) integrated intensity of each molecular cloud is 0.84 |

## Qualitative findings

- Velocity dispersion is higher along the filament, consistent with molecular gas collision there  
  > "shows that the velocity dispersion is higher in the filament, suggesting that molecular gas collision occurs there" (3.1 CO(J = 1-0))
- CO(3-2) peaks around, not at, the filament, suggesting a deficiency of warm and dense gas in the filament  
  > "although the CO($J$ = 3–2) intensity does not peak at the filament but around it" (3.2 CO(J = 3-2))
- No significant deviation from circular motion except a slight distortion, so the interaction is at a very early stage  
  > "there is no significant deviation from the circular motion, including the overlapping region" (4.4 Evolutionary and collisional stages)
- No sign of strong ICM stripping of HI in the overlapping region  
  > "The environmental effect may not be the main driver for making the filament." (4.3 Formation process of the filamentary molecular structure)

## Claim tuples

- H: Filament clouds are still gravitationally bound despite collision-induced turbulence | E: CLUMPFIND clouds in CO(1-0), virial parameters from radius, velocity dispersion and luminosity mass | R: Filament mean alpha_vir 0.56 +/- 0.14 vs 0.28 +/- 0.12 (overlapping) and 0.26 +/- 0.16 (disc); all below 1 | F: Filament clouds have a factor of two higher virial parameter and larger velocity dispersion but are all gravitationally bound | **supported**
- H: Gas on the collision front is compressed and denser, giving high CO(3-2)/CO(1-0) as simulations predict | E: R3-2/1-0 computed for each cloud from ALMA CO(3-2) and CO(1-0) | R: Maximum R3-2/1-0 0.17 +/- 0.04; mean 0.05 +/- 0.04 in the overlapping region; filament clouds below 0.1 | F: Filament clouds have lower R3-2/1-0 than the surroundings, contradicting simulation predictions; the pair is probably too early in the interaction | **supported**
- H: Cloud properties in the overlapping region differ from those in the disc | E: K-S tests of cloud radius, velocity dispersion, luminosity mass, surface density and virial parameter between the two regions | R: p = 0.23 (radius), 0.67 (alpha_vir); 1.9e-3, 3.1e-6, 2.8e-5 for dispersion, mass, surface density | F: Disc clouds have larger velocity dispersion, luminosity mass and surface density than overlapping-region clouds | **supported**
- H: The pair is in a very early stage of interaction | E: 3D-BAROLO circular-motion models and inspection of velocity field and P-V diagrams | R: Only a slight distortion in part of NGC 4568; velocity field not significantly disturbed | F: The pair is at a very early stage with a quiet collision, so clouds have not yet become dense enough to trigger star formation | **supported**
- H: The filament formed by compression of HI gas at the collision front | E: Comparison of CO and HI distributions and HI deficiency, HI mass in two halves of NGC 4568 | R: Filament lies around the HI peak; HI masses comparable north and south; no clear stripping signs | F: Filament might have been formed by HI compression; high-resolution HI data needed to verify | **partially**

## Reasoning

- Why this data: CO(3-2) traces warmer and denser gas than CO(1-0), so comparing the two probes dense gas formation  
  > "CO($J$ = 3–2) traces warmer and denser molecular gas than CO($J$ = 1–0)" (Introduction); "we can investigate the dense gas formation process by comparing the spatial distribution of CO($J$ = 3–2) with that of CO($J$ = 1–0)" (Introduction)
- Why this method: Cloud-scale R3-2/1-0 is used to test whether clouds are dense enough to trigger star formation  
  > "of each molecular cloud to investigate whether the clouds are dense enough to trigger star formation" (Introduction)
- Alternative: HCN(1-0) not used since strong HCN is not expected before a starburst  
  > "Therefore, strong HCN emission is not expected for this galaxy pair, as the starburst has not been triggered yet." (Introduction)
- Alternative: CO(3-2) may not be the ideal tracer for the filament formation process  
  > "moderately dense gas tracers such as CO($J$ = 3–2) may not be the ideal choice to probe the formation process" (4.3 Formation process of the filamentary molecular structure)
- How they decided it was enough: _not stated_
- Limitation (authors): 63% of CO(1-0) flux is missing and the derived mass is a lower limit  
  > "found that the missing flux accounts for 63% of the total flux" (Observations and data reduction); "Note that the derived mass is the lower limit due to missing flux." (3.1 CO(J = 1-0))
- Limitation (authors): CO(3-2) missing flux could not be estimated  
  > "As no single-dish data was available, the missing flux of CO($J$ = 3–2) could not be estimated." (Observations and data reduction)
- Limitation (authors): Primary beam correction enhances noise at the edge of the CO(3-2) field  
  > "Note that the primary beam correction caused noise enhancement at the edge of the field of view." (3.2 CO(J = 3-2))
- Limitation (authors): Map-based R3-2/1-0 values cannot be directly compared with cloud values because of unrelated emission  
  > "Therefore, the values presented in figure [10](#fig:R32-Ha) cannot be directly compared with those in figure" (4.2 Physical properties of molecular clouds)
- Caveat (inferred, ours): Cloud properties depend on CLUMPFIND settings and on 63% missing CO(1-0) flux; comparison with the earlier Cycle 1 cloud list shows the results are sensitive to sensitivity and resolution
- Caveat (inferred, ours): R3-2/1-0 uses the CO(1-0) cloud masks with a 12-m plus ACA CO(1-0) cube and a CO(3-2) cube with different missing-flux levels and resolution, so ratios are likely biased low and the matching of beams and uv ranges is not described
- Caveat (inferred, ours): Single XCO value is applied to filament, overlap and disc clouds
- Caveat (inferred, ours): Virial parameters ignore external pressure and magnetic fields and depend on deconvolved sizes

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version, calibrators, tclean mask and cell settings, and line-free channels
- Missing: Beam sizes and position angles for the final cubes
- Missing: CLUMPFIND implementation and cloud catalogue
- Missing: Cycle 1 reduction and 3D-BAROLO parameters
- Missing: Nobeyama 45-m data and the HI and H-alpha images
- Data volume (inferred): Two Cycle 3 projects (Band 3 12-m plus ACA, 3.7 h; Band 7 12-m plus ACA, 0.5 h) and one Cycle 1 project; likely tens of GB of raw data, with products a few GB
- Score (inferred): 3/5, ALMA project codes and the main analysis recipe (tclean Briggs 0.5, uvcontsub, CLUMPFIND 3 sigma/2 sigma, formulae) are given with numeric results, but CASA version, masks, cell sizes, beam sizes and several external datasets are missing.
- Rediscovery candidate: yes, Project codes are given and the cloud identification and ratio analysis are simple and numeric, so a rough reproduction of cloud counts, virial parameters and R3-2/1-0 is plausible, although exact numbers need unstated settings.

## Links

- Method: Kaneko et al. 2018 (cite: Kaneko18) (Earlier Cycle 1 ALMA CO(1-0) observations that discovered the filament and gave a first cloud list for comparison)
- Method: Williams et al. 1994 (cite: Williams94) (CLUMPFIND cloud identification)
- Method: Di Teodoro and Fraternali 2015 (cite: DiTeodoro15) (3D-BAROLO kinematic modelling)
- Method: Bertoldi and McKee 1992 (cite: Bertoldi92) (Virial parameter definition)
- Companion: Kaneko et al. 2013 (cite: Kaneko13) (Nobeyama 45-m CO(1-0) data, total molecular gas mass, and early-stage collision interpretation)
- Companion: Kaneko et al. 2017 (cite: Kaneko17) (Higher molecular gas fraction in the overlapping region)
- Companion: Kaneko et al. 2018 (cite: Kaneko18) (Discovery of the filamentary molecular structure with ALMA Cycle 1)
- Related: ALMA Cycle 1 program of the same pair (2012.1.00759.S per acknowledgements)

## Checks

```json
{
 "quotes": 137,
 "quotes_ok": 137,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 77,
  "rate": 0.7
 },
 "evidence_ok": true
}
```
