# Smoke on the water: CO and H<SUB>2</SUB>O in a circumnuclear disc around a quasar at redshift 2.64

`2020MNRAS.493.5290S` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Stacey, H. R. | arXiv: 2002.07186 | DOI: 10.1093/mnras/staa494

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Where does the 380 GHz H2O (4_14-3_21) line emission in the lensed quasar MG J0414+0534 originate (disc, jet or offset component), and what is the structure of the circumnuclear molecular gas disc and radio jets?  
  > "We localise the 380 GHz H$_2$O emission relative to the CO and radio jet components, from which we derive a model for the emission from the system." (1 Introduction); "We confirm the previously reported detection of the 380 GHz water line and that the flux density ratio between the two merging lensed images is reversed with respect to the radio/mm continuum." (abstract)
- Target **MG J0414+0534**: coordinates _not stated_; z/distance z = 2.64 (2.639 in the conclusion); 1 arcsec = 8.2 kpc  
  > "For this cosmology, 1 arcsec corresponds to 8.2 kpc at the source redshift of 2.64." (1 Introduction); "MG J0414+0534, a gravitationally lensed dusty star-forming galaxy that hosts a type 1 quasar." (abstract); distance from redshift origin not stated in text; angular scale from Planck 2016 flat LCDM, H0 = 67.8 km/s/Mpc, Omega_M = 0.31  
  > "For this cosmology, 1 arcsec corresponds to 8.2 kpc at the source redshift of 2.64." (1 Introduction); "MG J0414+0534, a gravitationally lensed dusty star-forming galaxy that hosts a type 1 quasar." (abstract)

## Data provenance

- ALMA projects: 2017.1.00316.S, 2013.1.01110.S
- bands: Band 3 (100 GHz, H2O); Band 7 (340 GHz, CO (11-10))  
  > "The first, taken at 100 GHz, targeted H$_2$O, whereas the second, taken at 340 GHz, targeted high-excitation CO." (2.2 ALMA observations); "MG J0414+0534 was observed with ALMA in Band 3 under project code 2017.1.00316.S (PI: Kuo)." (2.2.1 100 GHz data)
- frequencies and spectral setup: Band 3: four SPWs at 92, 94, 104, 106 GHz; 94 and 104 GHz SPWs (1920 channels, 0.94 GHz bandwidth each) cover the two H2O lines; other SPWs 128 channels, 2 GHz bandwidth; 3 s integration  
  > "The data were correlated with a visibility integration time of 3 s, in four spectral windows of central frequency 92, 94, 104 and 106 GHz, respectively." (2.2.1 100 GHz data); "These spectral windows were each correlated with 1920 channels and 0.94 GHz bandwidth; the remaining spectral windows had 128 channels and 2 GHz bandwidth." (2.2.1 100 GHz data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest baseline 2400 m (Band 3)  
  > "in an antenna configuration with a longest baseline of 2400 m." (2.2.1 100 GHz data)
- angular resolution: H2O observations about a factor of 2 coarser than CO (11-10); absolute beam size not stated  
  > "While the angular resolution of the 380 GHz H$_2$O line observations are around a factor of 2 lower than those of the CO (11–10)" (3.1 Velocity structure)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 160 min total on target (about 40 min per epoch), Band 3  
  > "The total time on-target was 160 min, with approximately 40 min per epoch." (2.2.1 100 GHz data)
- observing dates: Band 3: 2017 December 13, 15 (two observations) and 18  
  > "The data were taken in four epochs on 2017 December 13, 15 (two observations) and 18" (2.2.1 100 GHz data)
- pi or archival as stated: Band 3: PI Kuo; Band 7: PI Inoue (data reused; not the authors' own proposals)  
  > "under project code 2017.1.00316.S (PI: Kuo)." (2.2.1 100 GHz data); "under project code 2013.1.01110.S (PI: Inoue)." (2.2.2 340 GHz data)
- Line: H2O 4_14-3_21 (380.197 GHz)
- Line: H2O 5_23-6_16 (not detected) (336.228 GHz)
- Line: CO 11-10 (1267.014 GHz)
- Other facility **Global VLBI (EVN + VLBA), project GW019A**: 1.6 GHz radio continuum imaging of the lensed images (VLBI sub-components used for the lens model and jet structure)  
  > "MG J0414+0534 was observed with the global VLBI array on 2008 June 7, under project code GW019A (PI: Wucknitz)." (2.1 1.6 GHz VLBI observations); "The 1.6 GHz VLBI positions, having the highest precision and largest number of image components, were used to optimise for the best lens model parameters." (3.3 Source-plane structure)
- External data: ALMA Band 7 (2013.1.01110.S) CO (11-10) observations, data reduction, imaging, line profile, and continuum/line image flux ratios  
  > "Details of the observations, data reduction and imaging are reported by" (2.2.2 340 GHz data); "We then fix the flux density of images A2, B and C using the flux ratios reported by" (3.3 Source-plane structure) [from (cite: Stacey:2018b)]
- External data: 22 GHz H2O megamaser components used for comparison with the 380 GHz line peaks  
  > "the peaks in the 380 GHz H$_{2}$O line profile are consistent with the blue and redshifted components of the 22 GHz H$_2$O megamaser system reported by" (3.1 Velocity structure) [from (cite: Castangia:2011)]
- External data: Black hole mass from microlensing analysis of the X-ray emission, compared with the dynamical mass  
  > "which is only three times larger than the black hole mass determined by" (3.4 Size and structure of the molecular gas disc) [from (cite: Pooley:2007)]
- External data: Flat LCDM cosmology used for distances and angular scale  
  > "We assume the (cite: Planck:2016) model of flat" (1 Introduction) [from (cite: Planck:2016)]
- Simulation/model as data: Grid of mock sources on the source plane lensed with the authors' gravlens model to find viable positions of the anomalous H2O component  
  > "we place a grid of mock sources on the source plane and compute the positions predicted by our lens model." (3.3 Source-plane structure)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline within CASA (Band 3); VLBI calibrated manually in AIPS  
  > "The data were calibrated using the ALMA pipeline within CASA." (2.2.1 100 GHz data); "The data were manually flagged to remove radio frequency interference and off-source integrations." (2.1 1.6 GHz VLBI observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (absolute flux and bandpass), Band 3  
  > "J0423$-$0120 was used as the absolute flux and spectral bandpass calibrator." (2.2.1 100 GHz data)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on the continuum SPWs to align the four epochs and correct residual phase and amplitude errors; solution intervals not stated for ALMA  
  > "Self-calibration was performed using the continuum spectral windows to spatially align the four epochs and correct for any residual time-dependent phase and amplitude errors." (2.2.1 100 GHz data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Model fit to line-free channels, subtracted in the visibility plane  
  > "The continuum subtraction was performed by fitting a model to the continuum in the line-free spectral channels and subtracting it from the data in the visibility plane." (2.2.1 100 GHz data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Frequency averaging by a factor of 16, giving 22.6 km/s per channel  
  > "the data were averaged in frequency by a factor of 16 to increase the signal-to-noise ratio per channel and the computational speed during imaging." (2.2.1 100 GHz data); "This resulted in a spectral resolution of 22.6 km s$^{-1}$ channel$^{-1}$." (2.2.1 100 GHz data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Band 7 (2013.1.01110.S) CO (11-10) observation details, data reduction and imaging are not repeated  
  > "Details of the observations, data reduction and imaging are reported by" (2.2.2 340 GHz data) [from (cite: Stacey:2018b)]
- Lensed-image flux ratios used to fix A2, B and C in the Gaussian fits to the H2O moment 0 map  
  > "We then fix the flux density of images A2, B and C using the flux ratios reported by" (3.1 Velocity structure) [from (cite: Stacey:2018b)]
- Radio component positions referenced to the brightest component in image B  
  > "The radio components are measured relative to the brightest component in image B, for consistency with previous studies" (2.1 1.6 GHz VLBI observations) [from (e.g. (cite: Macleod:2013))]

### Not stated but needed to reproduce (our reading)

- CASA version used for the ALMA pipeline and for IMFIT/imaging
- tclean (or other imaging) parameters for the Band 3 cubes: weighting/robust, cell size, image size, deconvolver, masks and cleaning threshold
- Which channels were treated as line-free for continuum subtraction (the paper notes the broad line makes this hard)
- Self-calibration solution intervals, reference model and number of iterations for the ALMA data
- Synthesised beam and rms noise of the Band 3 cubes and moment maps
- Spatial apertures and velocity ranges used for the line profiles, integrated intensities and position-velocity slices
- Initial guesses and fitting method for the double-Gaussian line profile and the four-Gaussian image-plane fit
- The lens parameter table and VLBI component table are referenced but their contents are not in the paper text; gravlens setup (optimisation details) not given
- Grid spacing and extent of the mock source positions; how magnifications of 40 and 330 were computed
- Which epochs were combined and flux-scale handling for the variability comparison
- VLBI Briggs robust value and AIPS imaging parameters

## Analysis recipe

1. **Calibrate and image the 1.6 GHz VLBI data and fit components**: Manual flagging, calibration and self-calibration in AIPS; Briggs-weighted imaging; 2-D Gaussians fitted to sub-components of the four lensed images with IMFIT  
  > "The data were edited, calibrated and imaged using the Astronomical Image Processing Software (AIPS)." (2.1 1.6 GHz VLBI observations); "The target was imaged and deconvolved in AIPS using a Briggs weighting of the visibilities" (2.1 1.6 GHz VLBI observations)
   - software: AIPS, CASA (IMFIT)
   - parameter: Self-calibration on line-free SPWs down to a 60 s solution interval  
  > "Several iterations of self-calibration of the target were performed using the line-free spectral windows, down to a solution interval of 60 s, to correct for residual phase and amplitude errors." (2.1 1.6 GHz VLBI observations)
   - assumption: Brightest radio sub-component (I) is at or near the radio core, matching the optical quasar position  
  > "so this is likely emission from (or very close to) the radio core." (2.1 1.6 GHz VLBI observations)
   - fitting: 2-D Gaussian fits in the image plane  
  > "was used to fit 2-dimensional Gaussians to the sub-components of the four lensed images (in the image plane) to extract their positions and uncertainties" (2.1 1.6 GHz VLBI observations)
   - validation: VLBI components compared with earlier 8.4 GHz imaging and previous imaging of the same data  
  > "The VLBI components appear structurally similar to those reported by" (2.1 1.6 GHz VLBI observations)
2. **Calibrate and prepare the 100 GHz ALMA data**: ALMA pipeline in CASA, frequency averaging by 16, self-calibration on continuum SPWs to align epochs, visibility-plane continuum subtraction  
  > "The data were calibrated using the ALMA pipeline within CASA." (2.2.1 100 GHz data); "The continuum subtraction was performed by fitting a model to the continuum in the line-free spectral channels and subtracting it from the data in the visibility plane." (2.2.1 100 GHz data)
   - software: CASA
   - parameter: Frequency averaging by a factor of 16 giving 22.6 km/s channels  
  > "This resulted in a spectral resolution of 22.6 km s$^{-1}$ channel$^{-1}$." (2.2.1 100 GHz data)
   - fitting: _not stated_
   - validation: Calibration and imaging of target and calibrators independently verified  
  > "We independently verified the calibration and imaging (of both the target and the calibrators)" (4.1 Origin of the H2O emission)
3. **Detect the 380 GHz H2O line and measure line intensity, luminosity and moment maps**: Line imaging of the Band 3 data, line intensity and luminosity (uncorrected for lensing magnification), moment maps of images A1 and A2 above a 3 sigma cut  
  > "We confirm the detection of the 4$_{14}$–3$_{21}$ H$_2$O line; the line intensity and line luminosity (uncorrected for lensing magnification)" (2.2.1 100 GHz data); "Moment maps of the line emission from lensed images A1 and A2, using a signal-to-noise ratio cut of 3$\sigma$, are shown in Fig." (2.2.1 100 GHz data)
   - software: CASA
   - parameter: 3 sigma signal-to-noise cut for moment maps  
  > "using a signal-to-noise ratio cut of 3$\sigma$" (2.2.1 100 GHz data)
   - fitting: _not stated_
   - validation: Detection consistent with the previous tentative detection; the 5_23-6_16 line is not detected, as in the earlier analysis  
  > "We do not detect the 5$_{23}$–6$_{16}$ H$_2$O line, consistent with the results of" (2.2.1 100 GHz data)
4. **Extract red and blue CO (11-10) component positions**: Images from selected channels on either side of the systemic velocity, 2-D Gaussian fits with IMFIT  
  > "The positions of the redshifted and blueshifted components of the line emission were extracted by creating images from selected channels on either side of the systemic velocity." (2.2.2 340 GHz data)
   - software: CASA (IMFIT)
   - fitting: 2-D Gaussian fits  
  > "The positions of these components were extracted by fitting 2-dimensional Gaussians using the task IMFIT within CASA." (2.2.2 340 GHz data)
   - validation: _not stated_
5. **Extract H2O and CO line profiles and fit the double-horn profile**: Line profile from an aperture including images A1 and A2 and from image A1 only; two Gaussian components fitted to the double-horn profile of A1; systemic velocity correction inferred from the double peak  
  > "using an aperture including lensed images A1 and A2, and also from only lensed image A1 in the case of the former." (3.1 Velocity structure); "We fit two Gaussian components to the double-horn profile isolated from image A1" (3.1 Velocity structure)
   - software: not stated
   - assumption: Emission from image A1 comes from a disc (double-horn profile)  
  > "under the assumption that the emission is from a disc" (3.1 Velocity structure)
   - fitting: Two-Gaussian fit; fitting method not stated  
  > "We fit two Gaussian components to the double-horn profile isolated from image A1" (3.1 Velocity structure)
   - validation: Compared with the CO (11-10) line profile and the 22 GHz megamaser components  
  > "compared the line profile and position-velocity diagram with those from the CO (11–10) and the 22 GHz H$_2$O megamaser" (4.1 Origin of the H2O emission)
6. **Test whether the H2O emission is resolved with Gaussian fits to the four images**: Fit four Gaussians fixed to the synthesised beam size and position angle at the mm-continuum centroids; A1 flux free, A2, B, C fixed by CO/continuum flux ratios; inspect residuals  
  > "we fix four Gaussian components to the size and position angle of the synthesised beam, and fix the component positions to the centroids of the mm-continuum emission." (3.1 Velocity structure); "We then fix the flux density of images A2, B and C using the flux ratios reported by" (3.1 Velocity structure)
   - software: not stated
   - assumption: H2O emission coincident with the quasar images is unresolved with the mm-continuum flux ratios  
  > "Assuming the 380 GHz H$_2$O line emission that is coincident with the quasar images is unresolved and has image flux ratios consistent with the mm-continuum" (3.1 Velocity structure)
   - fitting: Gaussian fit with A1 flux optimised; optimiser not stated  
  > "We initially allow the flux density of these components to optimise." (3.1 Velocity structure)
   - validation: Residuals show 4 sigma surface-brightness features around image A2  
  > "the residuals of this model fit have surface brightness features at the 4$\sigma$ level" (3.1 Velocity structure)
7. **Test for short-timescale variability across epochs**: Compare integrated line flux and position-velocity diagrams between epoch subsets (Dec 15 epochs vs combined Dec 13 and 18 epochs)  
  > "we examine the individual observations to look for short time-scale variability." (3.2 Variability); "We find tentative evidence for variability when comparing the integrated flux from combining the two 2017 December 15 epochs with the combined preceding and succeeding epochs on 2017 December 13 and 18" (3.2 Variability)
   - software: not stated
   - fitting: _not stated_
   - validation: Continuum is checked for variability; amplitude-scaling differences would not change line signal-to-noise  
  > "We note that, although differences in amplitude scaling could mimic source variability, this would not affect the signal-to-noise ratio of the line emission." (3.2 Variability)
8. **Build a gravitational lens model**: Parametric gravlens model: SIE plus external shear for the primary lens G1 and an SIS for the satellite G2, optimised on 1.6 GHz VLBI image positions; ALMA data aligned to the VLBI frame on the compact core  
  > "We assume a simple model of a singular isothermal ellipsoid with external shear" (3.3 Source-plane structure); "we align them using the compact core emission that is associated with synchrotron emission from the quasar." (3.3 Source-plane structure)
   - software: gravlens
   - parameter: Component flux densities not used in the fit  
  > "The flux densities of the components were not used in the modelling, as these are known to deviate from a smooth lens model" (3.3 Source-plane structure)
   - assumption: Smooth mass distribution; more complex models would not change the interpretation  
  > "this will not significantly change our interpretation here." (3.3 Source-plane structure)
   - fitting: Best-fit parameters optimised to VLBI positions; optimiser and priors not stated  
  > "were used to optimise for the best lens model parameters." (3.3 Source-plane structure)
   - validation: Agreement with previous lens models  
  > "are found to be in good agreement with previous modelling of the system" (3.3 Source-plane structure)
9. **Reconstruct the source plane and locate the anomalous H2O component**: Reconstruct VLBI and CO components in the source plane; place a grid of mock sources, lens them, and exclude positions that do not reproduce the observed image region; infer magnification and isotropic luminosity assuming half the line emission is in each component  
  > "we place a grid of mock sources on the source plane and compute the positions predicted by our lens model." (3.3 Source-plane structure); "we exclude all source positions that produce an image below the midpoint between image A1 and A2." (3.3 Source-plane structure)
   - software: gravlens
   - assumption: Half of the detected 380 GHz H2O emission originates in the disc; the radio-core magnification represents the H2O disc  
  > "Assuming just half of the 380 GHz H$_2$O emission we detect originates in a disc" (3.3 Source-plane structure)
   - assumption: Half of the H2O emission originates in the anomalous feature  
  > "Assuming that half of the 380 GHz H$_2$O emission originates in the anomalous feature" (3.3 Source-plane structure)
   - fitting: _not stated_
   - validation: Candidate source regions checked against the position of the anomalous feature north of A2 in position-velocity diagrams and Gaussian fits  
  > "only the green and blue source regions are in agreement with the observations." (3.3 Source-plane structure)
10. **Estimate dynamical mass and disc sizes**: Enclosed mass from R V_max^2 / G for the CO disc (R = 30 pc, V_obs = 550 km/s corrected for 45 deg inclination); same formula applied to half the H2O line-peak separation to infer the H2O disc size  
  > "where $R$ is the 30 pc radius (60 pc diameter)" (3.4 Size and structure of the molecular gas disc); "Here, we assume the maximum rotational velocity is half the separation of the line peaks identified in Section" (3.4 Size and structure of the molecular gas disc)
   - software: not stated
   - parameter: V_obs = 550 km/s, inclination 45 deg  
  > "We assume the rotational velocity is the line velocity at the FWHM ($V_{\rm obs}=550$  km s$^{-1}$), corrected with an inclination angle of 45 deg" (3.4 Size and structure of the molecular gas disc)
   - assumption: Keplerian rotation with enclosed mass dominated by the black hole for the water-emitting disc; 45 deg inclination  
  > "Assuming the molecular gas disc also contains water emitting regions with a Keplerian rotation and whose enclosed mass is dominated by the black hole" (3.4 Size and structure of the molecular gas disc)
   - fitting: _not stated_
   - validation: Dynamical mass compared with the black hole mass from microlensing  
  > "which is only three times larger than the black hole mass determined by" (3.4 Size and structure of the molecular gas disc)

## Software

- **CASA** : ALMA pipeline calibration, imaging, and IMFIT Gaussian fitting  
  > "The data were calibrated using the ALMA pipeline within CASA." (2.2.1 100 GHz data); "The task IMFIT within the Common Astronomy Software Applications (CASA) package" (2.1 1.6 GHz VLBI observations)
- **AIPS** : Editing, calibration and imaging of the 1.6 GHz VLBI data  
  > "The data were edited, calibrated and imaged using the Astronomical Image Processing Software (AIPS)." (2.1 1.6 GHz VLBI observations)
- **gravlens** : Parametric lens modelling  
  > "This was performed using the parametric lens modelling software gravlens" (3.3 Source-plane structure)
- **Astropy** : Named in the acknowledgements as used in the research; specific use not stated  
  > "This research made use of Astropy and Matplotlib packages for Python" (Acknowledgements)
- **Matplotlib** : Named in the acknowledgements as used in the research; specific use not stated  
  > "This research made use of Astropy and Matplotlib packages for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 380 GHz H2O (4_14-3_21) integrated line intensity | 1.0 | 0.1 | Jy km/s | 3 | $1.0\pm0.1$ |
| 380 GHz H2O line luminosity (uncorrected for lensing magnification) | 5.3e7 | 0.6e7 | Lsun | 3 | $(5.3\pm0.6)\times10^{7}$ |
| 380 GHz H2O line luminosity L' | 3.0e10 | 0.4e10 | K km/s pc^2 | 3 | $(3.0\pm0.4)\times10^{10}$ |
| Spectral resolution after averaging | 22.6 | not stated | km/s per channel | 2 | This resulted in a spectral resolution of 22.6 km s$^{-1}$ channel$^{-1}$. |
| Blue Gaussian component centre (image A1 double-horn profile) | -210 | 20 | km/s | 5 | which are centred on $-210\pm20$  km s$^{-1}$ and $490\pm20$  km s$^{-1}$ |
| Red Gaussian component centre (image A1 double-horn profile) | 490 | 20 | km/s | 5 | which are centred on $-210\pm20$  km s$^{-1}$ and $490\pm20$  km s$^{-1}$ |
| FWHM of blue and red Gaussian components | 630 and 420 | 50 and 40 | km/s | 5 | with full width at half maximum (FWHM) of $630\pm50$  km s$^{-1}$ and $420\pm40$  km s$^{-1}$, respectively. |
| Overall FWHM of the 380 GHz H2O line profile | ~1000 | not stated | km/s | 5 | The overall FWHM of the 380 GHz H$_{2}$O line profile is $\sim1000$  km s$^{-1}$ |
| CO (11-10) line FWHM (Gaussian fit) | 1100 | 100 | km/s | 5 | $1100\pm100$  km s$^{-1}$, based on a Gaussian fit |
| Correction to systemic velocity from double-peaked H2O profile | +140 | 10 | km/s | 5 | suggests a correction to the systemic velocity of $+140\pm10$  km s$^{-1}$ |
| Peak H2O velocity dispersion | ~400 | not stated | km/s | 3 | the velocity dispersion of the 380 GHz H$_2$O emission peaks at around $400$  km s$^{-1}$ |
| A2/A1 H2O line flux ratio | ~2 | not stated | dimensionless | 6 | the H$_2$O line emission from image A2 appears around twice as bright as A1 |
| Increase in A1+A2 emission between 13 and 15 December | 1.7 | 0.8 | dimensionless (factor) | 7 | appears to increase by a factor $1.7\pm0.8$ between the observations taken on 2017 December 13 and 15 |
| Variability significance, total (A1+A2) integrated emission | 2 | not stated | sigma | 7 | The significance of this variability is at the $2\sigma$ level when we consider the total integrated emission |
| Variability significance, image A1 only | 3 | not stated | sigma | 7 | the significance rises to $3\sigma$ when we only consider the integrated flux from image A1 |
| Time delay between merging images (lens model) | 0.4 | not stated | days | 8 | The time delay between the merging images of the quasar is expected to be 0.4 days, based on our lens model |
| Radio jet extent (East-West, in projection) | ~200 | not stated | pc | 9 | extended in an East–West direction by around 200 pc in projection. |
| CO (11-10) molecular gas disc size | 60 | not stated | pc (diameter) | 9 | a molecular gas disc with a size that is 60 pc in projection around the quasar. |
| Total magnification of the radio core | ~40 | not stated | dimensionless | 9 | ($\mu_{\rm tot} \simeq 40$) |
| Isotropic H2O disc line luminosity (intrinsic) | ~7e5 | not stated | Lsun | 9 | we estimate the isotropic line luminosity is $\sim7\times10^{5}$ L$_{\odot}$. |
| Highest combined magnification of merging images from mock sources | ~330 | not stated | dimensionless | 9 | we take the highest combined magnification of the merging images produced by the mock sources (about 330) |
| Minimum intrinsic isotropic luminosity of the anomalous H2O component | 8e4 | not stated | Lsun | 9 | to infer a minimum intrinsic isotropic line luminosity of $8\times10^{4}$ L$_{\odot}$. |
| Offset of the anomalous H2O component from the quasar | >600 | not stated | pc | 9 | originates $>600$ pc East of the quasar and perpendicular to the molecular gas disc. |
| Enclosed dynamical mass within 30 pc | ~3e9 | not stated | Msun | 10 | We find a dynamical mass of $M_{\rm dyn}(<30~{\rm pc}) \sim3\times10^{9}$ M$_{\odot}$ |
| Size (diameter) of the water-emitting disc | ~35 | not stated | pc | 10 | This implies the size (diameter) of the water emitting disc is around 35 pc |

## Qualitative findings

- The 380 GHz H2O line detection is robust and the A2/A1 flux ratio is reversed relative to the radio/mm continuum and CO (11-10)  
  > "we find strong evidence that the 380 GHz H$_2$O line detection is robust." (4.1 Origin of the H2O emission); "the flux density ratio between the two merging lensed images is reversed with respect to the radio/mm continuum." (abstract)
- Tentative evidence of variability of the integrated line intensity on timescales of days  
  > "We further find tentative evidence of variability in the integrated line intensity on timescales of days." (abstract)
- The line has a disc component and an anomalous component offset from the disc near the lensing caustic  
  > "another component of emission that is offset" (abstract)
- No clear evidence that the 380 GHz H2O line comes from masers; the high luminosity is more consistent with thermal emission  
  > "we find no clear evidence that the 380 GHz H$_2$O line observed here originates from a population of masers" (4.2 Structure of the circumnuclear gas disc)

## Claim tuples

- H: Is the 380 GHz H2O line detection in MG J0414+0534 robust, and is the A2/A1 flux ratio really reversed? | E: Independent re-calibration and imaging of the Band 3 data and comparison of the line profile and position-velocity diagram with CO (11-10) and 22 GHz maser | R: Line detected with 1.0 +/- 0.1 Jy km/s; A2 about twice as bright as A1; line width and dispersion similar to CO | F: The detection is robust and the flux ratio is reversed relative to continuum and CO | **supported**
- H: Does part of the 380 GHz H2O emission arise in a circumnuclear disc like the CO (11-10)? | E: Double-horn profile fit and position-velocity diagrams of H2O compared with CO; disc size from Keplerian assumption | R: Double-peaked profile and PV structure within the CO disc extent; disc diameter about 35 pc | F: H2O emission includes a compact rotating disc about 35 pc across, smaller than the 60 pc CO disc | **partially**
- H: Where does the anomalous velocity component not belonging to the disc originate? | E: Position-velocity analysis, Gaussian fits and a grid of mock sources through the gravlens model | R: Viable source positions lie near the caustic more than 600 pc East of the quasar with magnification about 330 | F: A second H2O component is offset about 600 pc perpendicular to the disc and highly magnified | **supported**
- H: Is the 380 GHz H2O line variable on timescales of days? | E: Compare integrated flux and PV diagrams between epoch subsets over 6 days | R: 2 sigma for total emission, 3 sigma for image A1 only; no continuum variability | F: Tentative evidence for variability; needs short-cadence monitoring | **partially**
- H: What is the size of the CO (11-10) disc and how does the enclosed mass compare with the black hole? | E: Lens model source-plane reconstruction and dynamical mass M = R V^2 / G | R: 60 pc disc diameter; enclosed mass about 3e9 Msun, three times the microlensing black hole mass | F: CO kinematics are driven by the central supermassive black hole | **supported**

## Reasoning

- Why this data: Earlier ALMA analysis gave only a tentative detection and an unexpected reversed flux ratio, motivating a re-analysis combined with archival VLBI and CO imaging  
  > "Surprisingly, this tentative detection finds the flux ratio between the two merging lensed images (A1 and A2) to be reversed relative to the radio/mm continuum" (1 Introduction)
- Why this method: VLBI positions used for the lens model because they have the highest precision and the most image components  
  > "The 1.6 GHz VLBI positions, having the highest precision and largest number of image components, were used to optimise for the best lens model parameters." (3.3 Source-plane structure)
- Alternative: More complex lens models (e.g. ellipsoidal power-law mass distribution) not used because they would not change the interpretation  
  > "While an improved fit to the image positions may also be obtained with more complex parametric models" (3.3 Source-plane structure)
- Alternative: Doubly imaged source positions several kpc from the quasar (as proposed by Kuo et al.) judged not feasible  
  > "which we do not consider to be feasible." (3.3 Source-plane structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Variability evidence is only tentative (2-3 sigma)  
  > "We find tentative evidence for variability in the 380 GHz H$_2$O disc at the 3$\sigma$ level on timescales of hours to days." (4.2 Structure of the circumnuclear gas disc)
- Limitation (authors): Beam smearing prevents detailed disc dynamics; deferred to future higher-resolution CO imaging  
  > "Therefore, we defer a more comprehensive investigation of the disc dynamics to a future work that will use higher resolution imaging of the CO (11–10) line." (3.4 Size and structure of the molecular gas disc)
- Limitation (authors): Low surface brightness and chance lensing configuration make spatial resolution of the H2O emission difficult  
  > "However, the low surface brightness of this 380 GHz H$_2$O line emission and the chance lensing configuration we propose suggest that spatially resolving the source emission may be difficult." (4.3 Discussion)
- Caveat (inferred, ours): Disc interpretation rests on a double-horn profile from one lensed image at low angular resolution; alternative (outflow, jet, multiple clumps) not excluded
- Caveat (inferred, ours): Dynamical mass and disc size assume a fixed 45 deg inclination and a Keplerian black-hole-dominated disc with no uncertainty propagated
- Caveat (inferred, ours): Half-and-half luminosity split between disc and anomalous component is an assumption
- Caveat (inferred, ours): Variability significance (2-3 sigma) could be affected by flux-scale differences between epochs and continuum subtraction of a very broad line
- Caveat (inferred, ours): Lens model uses a simple SIE+shear+SIS; microlensing and substructure could affect flux ratios and magnifications

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and tclean/imaging parameters for the Band 3 cubes
- Missing: Line-free channel selection and self-calibration settings
- Missing: Apertures and velocity windows for profiles, PV slices and variability
- Missing: Lens model and VLBI component tables not present in the paper text; gravlens run details
- Missing: Mock-source grid details and the magnification calculation
- Data volume (inferred): Band 3 (2017.1.00316.S, 4 epochs, 160 min, 1920-channel SPWs) probably tens to a few hundred GB raw; plus Band 7 data 2013.1.01110.S (not reprocessed here) and VLBI GW019A
- Score (inferred): 2/5, Data come from named ALMA projects and a VLBI project, but imaging parameters, CASA version, apertures and lens model details are missing and key results depend on interpretive assumptions
- Rediscovery candidate: no, Recipe is not complete enough to redo the imaging, fits and lens modelling without the missing parameters, and several conclusions are qualitative or assumption-driven

## Links

- Method: (cite: Stacey:2018b) (Observation, reduction and imaging of the Band 7 CO (11-10) data and the line/continuum flux ratios used here)
- Method: (cite: Kuo:2019) (Earlier analysis of the same Band 3 data with the tentative detection of the 380 GHz H2O line)
- Method: (cite: Keeton:2001a; Keeton:2001b) (gravlens lens modelling software)
- Companion: (cite: Castangia:2011) (22 GHz H2O megamaser detection and monitoring of MG J0414+0534, compared with the 380 GHz line peaks)
- Companion: (cite: Impellizzeri:2008) (Original 22 GHz megamaser detection in MG J0414+0534)
- Companion: (cite: Volino:2010) (Previous imaging of the same global VLBI data)
- Related: GW019A (global VLBI, PI Wucknitz)
- Related: 2013.1.01110.S (ALMA Band 7, PI Inoue)
- Related: 2017.1.00316.S (ALMA Band 3, PI Kuo)

## Checks

```json
{
 "quotes": 139,
 "quotes_ok": 139,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 25,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 76,
  "rate": 0.704
 },
 "evidence_ok": true
}
```
