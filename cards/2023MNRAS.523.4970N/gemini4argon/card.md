# Resolving the binary components of the outbursting protostar HBC 494 with ALMA

`2023MNRAS.523.4970N` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Nogueira, Pedro Henrique | arXiv: 2305.15647 | DOI: 10.1093/mnras/stad1614

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Resolve the substructure/asymmetry in the disk of the outbursting protostar HBC 494 to determine its nature and examine the surrounding gas kinematics at small and large scales.  
  > "ALMA Cycle-2 observations in the millimeter continuum (∼0′′.25 angular resolution) show that the disk is elongated with an apparent asymmetry (Cieza et al. 2018), indicating the presence of an unresolved structure or a secondary disk." (1 INTRODUCTION); "In this work, we present ALMA Cycle 4 observations at ∼0′′.03 angular resolution that reveal the binary nature of the HBC 494 system." (1 INTRODUCTION)
- Target **HBC 494**: coordinates J2000 05h40m27.448s -07d27m29.65s  
  > "We started our analysis by fixing the visibilities’ phase center on J2000 05h40m27.448s -07d27m29.65s" (2.1 Continuum imaging); "We started our analysis by fixing the visibilities’ phase center on J2000 05h40m27.448s -07d27m29.65s." (2.1 Continuum imaging); z/distance 414±7 pc  
  > "HBC 494 is a Class I protostar, located in the Orion molecular cloud at a distance of 414±7 pc (Menten et al. 2007)" (1 Introduction); "We started our analysis by fixing the visibilities’ phase center on J2000 05h40m27.448s -07d27m29.65s." (2.1 Continuum imaging); distance from Menten et al. 2007  
  > "HBC 494 is a Class I protostar, located in the Orion molecular cloud at a distance of 414±7 pc (Menten et al. 2007)" (1 Introduction); "We started our analysis by fixing the visibilities’ phase center on J2000 05h40m27.448s -07d27m29.65s." (2.1 Continuum imaging)

## Data provenance

- ALMA projects: 2016.1.00630.S
- bands: Band 6 (1.3 mm)  
  > "HBC 494 has been observed during the ALMA Cycle-4 in band 6 (program 2016.1.00630.S: PI Zurlo) for two nights" (2 OBSERVATIONS AND DATA REDUCTION); "The image synthesis of the 1.3 mm continuum emission was performed with the tclean task of CASA." (2.1 Continuum imaging)
- frequencies and spectral setup: Central frequencies: 230.543 (12CO J=2-1), 233.010 (continuum), 220.403 (13CO J=2-1), 219.565 (C18O J=2-1), and 218.010 (continuum) GHz; min spectral resolution: 15.259 kHz (~0.02 km/s) for 12CO, 30.518 kHz (~0.04 km/s) for 13CO and C18O  
  > "230.543 (to cover the transition [12] CO J=2-1), 233.010 (continuum), 220.403 ( [13] CO J=2-1), 219.565 (C [18] O J=2-1), and 218.010 (continuum)" (2 Observations and data reduction); "The minimum spectral resolution achieved (second night) for 12CO was 15.259 kHz (∼ 0.02 km/s), while for 13CO and C18CO, it was 30.518 kHz (∼ 0.04 km/s)." (2 OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: 2 GHz per continuum band (two bands)  
  > "Both continuum bands presented 2 GHz bandwidths." (2 OBSERVATIONS AND DATA REDUCTION)
- arrays: 40 12-m antennas (both nights)  
  > "The ALMA configuration of antennas was composed of 40 12-m antennas with a baseline from 19 to 3144 m." (2 OBSERVATIONS AND DATA REDUCTION); "The ALMA configuration consisted of 40 12-m antennas with a baseline from 42 m to 14851 m." (2 OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: 19 m to 3144 m (first night); 42 m to 14851 m (second night)  
  > "The ALMA configuration of antennas was composed of 40 12-m antennas with a baseline from 19 to 3144 m." (2 OBSERVATIONS AND DATA REDUCTION); "The ALMA configuration consisted of 40 12-m antennas with a baseline from 42 m to 14851 m." (2 OBSERVATIONS AND DATA REDUCTION)
- angular resolution: 0.142 arcsec (first night); 0.027 arcsec (second night); 41.2 x 29.8 mas (combined continuum)  
  > "Zurlo 2016.1.00630.S 0′′.142 09/10/2016 8.39 min" (Table 1); "Zurlo 2016.1.00630.S 0′′.027 26/09/2017 25.55 min" (Table 1); "For the high-resolution data, we used the Briggs weighting scheme with a robust parameter of 0.5, resulting in a synthesized beam size of 41.2 × 29.8 mas, and a position angle of 40.6." (2.1 Continuum imaging)
- max recoverable scale: _not stated_
- sensitivity: ~0.034 mJy/beam (continuum); 1.9, 3.6, and 2.6 mJy/beam for 12CO, 13CO, and C18O respectively  
  > "The rms is ∼0.034 mJy/beam, as observed in a circular region with a radius of 225 mas without emission." (3.1 Continuum analysis); "The rms values, obtained for the channel without a clear signal on the channel maps (4 km/s), were 1.9, 3.6, and 2.6 mJy/beam for 12CO, 13CO and C18O, respectively." (2.2 Line imaging)
- time on source: 8.39 min (first night); 25.55 min (second night)  
  > "The total integration on the target was 8.39 min." (2 OBSERVATIONS AND DATA REDUCTION); "The total integration on the target was 25.55 min." (2 OBSERVATIONS AND DATA REDUCTION)
- observing dates: 09/10/2016 and 26/09/2017  
  > "HBC 494 has been observed during the ALMA Cycle-4 in band 6 (program 2016.1.00630.S: PI Zurlo) for two nights, one on the 9th October 2016 and the other on the 26th September 2017 (see table 1)." (2 OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: PI Zurlo  
  > "HBC 494 has been observed during the ALMA Cycle-4 in band 6 (program 2016.1.00630.S: PI Zurlo)" (2 OBSERVATIONS AND DATA REDUCTION)
- Line: 12CO J=2-1 (230.543 GHz (central frequency of spw))
- Line: 13CO J=2-1 (220.403 GHz (central frequency of spw))
- Line: C18O J=2-1 (219.565 GHz (central frequency of spw))
- External data: Distance to HBC 494 of 414±7 pc  
  > "HBC 494 is a Class I protostar, located in the Orion molecular cloud at a distance of 414±7 pc (Menten et al. 2007)" (1 Introduction) [from Menten et al. 2007]
- External data: Sample of 14 resolved FUors and EXors and Class 0/I systems for dust mass vs radius comparison  
  > "The dust mass vs radius comparison between HBC 494 N and HBC 494 S, a sample of 14 resolved FUors and EXors (extracted from Hales et al. 2020) and Class 0/I systems (Tobin et al. 2020), can be seen in figure 8." (4.2 Disk sizes and masses); "To generate this plot, we obtained data from Kóspál et al. (2017); Hales et al. (2018); Cieza et al. (2018); Takami et al. (2019); Cruz-Sáenz de Miera et al. (2019); Pérez et al. (2020); Hales et al. (2020)." (Figure 8 caption) [from Kóspál et al. (2017); Hales et al. (2018); Cieza et al. (2018); Takami et al. (2019); Cruz-Sáenz de Miera et al. (2019); Pérez et al. (2020); Hales et al. (2020); Tobin et al. (2020)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v.5.5  
  > "The data were calibrated with the Common Astronomy Software Applications package (CASA v.5.5, McMullin et al. 2007), and the python modules from CASA API, casatasks and casatools (CASA Team et al. 2022)." (2 OBSERVATIONS AND DATA REDUCTION)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (first night); J0423-0120 (second night)  
  > "The flux calibrator and bandpass calibrator were both J0522-3627, and the phase calibrator was J0607-0834." (2 OBSERVATIONS AND DATA REDUCTION); "The flux calibrator was J0423-0120, the bandpass calibrator was J0510+1800, and the phase calibrator was J0541-0541." (2 OBSERVATIONS AND DATA REDUCTION)
- flux scale uncertainty: _not stated_
- self calibration: One iteration step of self-calibration applied to both observations (SNR improvement ~6 for first night, ~1.6 for second night)  
  > "One iteration step of self-calibration was applied to both observations. For the first night (low-resolution image: 142 mas), it resulted in an improvement of ∼6 SNR. For the second night (high-resolution image: 27 mas), it resulted in an SNR improvement of ∼ 1.6." (2.1 Continuum imaging)

### Imaging

- task: tclean  
  > "The image synthesis of the 1.3 mm continuum emission was performed with the tclean task of CASA." (2.1 Continuum imaging); "Next, we performed the tclean process using Briggs weighting with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale of 6 mas." (2.2 Line imaging)
- deconvolver: Hogbom (for line imaging)  
  > "Next, we performed the tclean process using Briggs weighting with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale of 6 mas." (2.2 Line imaging)
- weighting robust: Briggs weighting, robust = 0.5 (both continuum and line)  
  > "For the high-resolution data, we used the Briggs weighting scheme with a robust parameter of 0.5, resulting in a synthesized beam size of 41.2 × 29.8 mas, and a position angle of 40.6." (2.1 Continuum imaging); "Next, we performed the tclean process using Briggs weighting with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale of 6 mas." (2.2 Line imaging)
- uv taper: _not stated_
- cell size: 1.5 mas (continuum); 6 mas (line)  
  > "The pixel scale of the image was set to 1.5 mas." (2.1 Continuum imaging); "Next, we performed the tclean process using Briggs weighting with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale of 6 mas." (2.2 Line imaging)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "Therefore, we proceeded to remove the visibility’s continuum contributions by using the CASA task uvcontsub." (2.2 Line imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Concatenated short and long baseline visibilities using CASA concat task  
  > "Our final continuum image was produced from a concatenated measurement set combining both, the short and the long baseline visibilities, using the concat task of CASA." (2.1 Continuum imaging)
- smoothing: _not stated_
- final beam: 41.2 x 29.8 mas, PA 40.6 deg (combined continuum)  
  > "For the high-resolution data, we used the Briggs weighting scheme with a robust parameter of 0.5, resulting in a synthesized beam size of 41.2 × 29.8 mas, and a position angle of 40.6." (2.1 Continuum imaging)
- final rms: ~0.034 mJy/beam (34.0 uJy/beam) for continuum; 1.9, 3.6, and 2.6 mJy/beam for 12CO, 13CO, and C18O cubes  
  > "The rms is ∼0.034 mJy/beam, as observed in a circular region with a radius of 225 mas without emission." (3.1 Continuum analysis); "The rms values, obtained for the channel without a clear signal on the channel maps (4 km/s), were 1.9, 3.6, and 2.6 mJy/beam for 12CO, 13CO and C18O, respectively." (2.2 Line imaging)

### Inherited from earlier work

- Formula and dust opacity law for dust mass estimation from millimeter continuum flux  
  > "Thus, assuming standard disks, we can use the observed fluxes to estimate the dust masses of HBC 494 N and S. For that, we use the following formula (as in Beckwith et al. 1990; Andrews & Williams 2005; Cieza et al. 2018):" (3.1 Continuum analysis); "Adopting the distance of 414 pc, isothermal dust temperature (𝑇dust = 20 K) and dust opacity assuming a 𝑀gas/𝑀dust fraction of 100, (𝜅𝜈 = 10 (𝜈/ 1012 Hz) cm2 g−1; Beckwith et al. 1990)" (3.1 Continuum analysis) [from Beckwith et al. 1990; Andrews & Williams 2005; Cieza et al. 2018]
- Methodology for disk size calculation using deconvolved Gaussian FWHM/2 radius from 2D Gaussian fits  
  > "The disk sizes were calculated using the deconvolved Gaussian FWHM/2 radius obtained from 2D Gaussian fits. This methodology was also used for other ALMA datasets (e.g., Hales et al. 2020; Tobin et al. 2020)." (4.2 Disk sizes and masses) [from Hales et al. 2020; Tobin et al. 2020]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution interval (solint), whether phase-only or amplitude+phase, and clean masking details.
- Exact line-free channels and polynomial order used in uvcontsub.
- Deconvolver, image size, and stopping threshold/niter used for continuum tclean.
- Beam sizes for the spectral line cubes (both large-scale and small-scale).
- Whether the line imaging used the concatenated dataset or individual baseline configurations for the large-scale (8000 au) vs small-scale (150 au) analyses.

## Analysis recipe

1. **Calibrate, self-calibrate, concatenate, and image 1.3 mm continuum visibilities**: Fix visibilities phase center, perform 1 iteration of self-calibration on each night's dataset, concatenate short and long baseline measurement sets using concat, and synthesize final continuum image with tclean.  
  > "We started our analysis by fixing the visibilities’ phase center on J2000 05h40m27.448s -07d27m29.65s. The image synthesis of the 1.3 mm continuum emission was performed with the tclean task of CASA." (2.1 Continuum imaging); "One iteration step of self-calibration was applied to both observations." (2.1 Continuum imaging); "Our final continuum image was produced from a concatenated measurement set combining both, the short and the long baseline visibilities, using the concat task of CASA." (2.1 Continuum imaging)
   - software: CASA, casatasks, casatools, tclean, concat
   - parameter: Phase center: J2000 05h40m27.448s -07d27m29.65s; Briggs robust = 0.5; pixel scale = 1.5 mas  
  > "We started our analysis by fixing the visibilities’ phase center on J2000 05h40m27.448s -07d27m29.65s." (2.1 Continuum imaging); "For the high-resolution data, we used the Briggs weighting scheme with a robust parameter of 0.5, resulting in a synthesized beam size of 41.2 × 29.8 mas, and a position angle of 40.6. The pixel scale of the image was set to 1.5 mas." (2.1 Continuum imaging)
   - fitting: _not stated_
   - validation: SNR improvement of ~6 for the first night and ~1.6 for the second night after self-calibration  
  > "For the first night (low-resolution image: 142 mas), it resulted in an improvement of ∼6 SNR. For the second night (high-resolution image: 27 mas), it resulted in an SNR improvement of ∼ 1.6." (2.1 Continuum imaging)
2. **Characterize continuum disk properties (fluxes, sizes, position angles, inclinations) and radial profiles**: Fit 2D Gaussians to the resolved binary components in the continuum image using CASA imfit, derive disk inclinations from the deconvolved aspect ratios, and extract radial brightness profiles in elliptical apertures.  
  > "We performed a 2D Gaussian fitting with the imfit tool of CASA in order to characterize the newly resolved components." (3.1 Continuum analysis); "The inclinations are calculated using the aspect ratios of the disks. These are assumed as projected circular disks when face-on, thus elliptical when inclined:" (3.1 Continuum analysis); "The surface brightness (dots), measured in apertures ranging from the beam’s major axis to 3 times the semi-major axis FWHM of each continuum disk, were normalized to the peak fluxes." (Figure 3 caption)
   - software: CASA, imfit
   - parameter: RMS measured in a circular region with a radius of 225 mas without emission  
  > "The rms is ∼0.034 mJy/beam, as observed in a circular region with a radius of 225 mas without emission." (3.1 Continuum analysis)
   - assumption: Disks are circular when face-on and elliptical when inclined  
  > "These are assumed as projected circular disks when face-on, thus elliptical when inclined" (3.1 Continuum analysis)
   - fitting: 2D Gaussian fitting with CASA imfit  
  > "We performed a 2D Gaussian fitting with the imfit tool of CASA in order to characterize the newly resolved components." (3.1 Continuum analysis)
   - validation: _not stated_
3. **Estimate dust and gas masses of the two circumstellar disks**: Compute dust mass from integrated 1.3 mm continuum flux density using the optically thin isothermal dust emission formula, and multiply by gas-to-dust ratio for gas mass.  
  > "Thus, assuming standard disks, we can use the observed fluxes to estimate the dust masses of HBC 494 N and S." (3.1 Continuum analysis); "Following the standard gas-to-dust mass ratio of 100, we report disk gas masses estimations of 143.46 𝑀Jup for HBC 494 N, and 28.68 𝑀Jup for HBC 494 S." (3.1 Continuum analysis)
   - assumption: Optically thin dust emission, distance d = 414 pc, isothermal dust temperature T_dust = 20 K, gas-to-dust mass ratio M_gas/M_dust = 100, dust opacity kappa_nu = 10 (nu / 10^12 Hz) cm^2 g^-1  
  > "A large fraction of the mm-sized grains in protoplanetary disks resides in the midplane. They are usually optically thin to their own radiation." (3.1 Continuum analysis); "Adopting the distance of 414 pc, isothermal dust temperature (𝑇dust = 20 K) and dust opacity assuming a 𝑀gas/𝑀dust fraction of 100, (𝜅𝜈 = 10 (𝜈/ 1012 Hz) cm2 g−1; Beckwith et al. 1990) we get dust masses of 1.43 𝑀Jup (HBC 494 N) and 0.29 𝑀Jup (HBC 494 S)." (3.1 Continuum analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Continuum subtraction, spectral line imaging, and moment/channel map analysis at large (8000 au) and small (150 au) scales**: Fix phase center, subtract continuum in uv-plane with uvcontsub, image 12CO, 13CO, and C18O cubes with tclean, and generate channel maps, moment 0 and moment 1 maps, spectral profiles, and spatial cuts before and after continuum subtraction.  
  > "Therefore, we proceeded to remove the visibility’s continuum contributions by using the CASA task uvcontsub. Next, we performed the tclean process using Briggs weighting with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale of 6 mas." (2.2 Line imaging); "The next two subsections describe the large and small-scale structure analyses. The large scale, using the extent of 8000 au, shows the results of outflows and envelopes." (3.2 Line analysis); "To evaluate the effects of continuum over-subtraction, we generated spatial profiles for each disk using 12CO moment 0 maps at small scales before and after continuum subtraction." (APPENDIX A: EFFECTS OF CONTINUUM OVER-SUBTRACTION)
   - software: CASA, uvcontsub, tclean, imstat
   - parameter: Briggs robust = 0.5; Hogbom deconvolver; pixel scale = 6 mas; spectral widths: 1 km/s (12CO) and 0.3 km/s (13CO, C18O); velocity ranges: -6 to 18 km/s (total / 12CO, excluding 1 to 5 km/s for cloud contamination), 0 to 11 km/s (13CO, C18O)  
  > "Next, we performed the tclean process using Briggs weighting with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale of 6 mas. The total velocity ranged between -6 km/s to 18 km/s, although a smaller range (0 km/s to 11 km/s) was used to create the 13CO and C18O moment maps. We used spectral resolution widths of 1 km/s for 12CO and of 0.3 km/s for 13CO and C18O." (2.2 Line imaging); "We considered velocities in the range of -6 km/s to 1 km/s, and from 5 km/s to 18 km/s, as similarly done for the different large-scale arcs described in the previous subsection." (3.2.2 Small scale structures (150 au resolution))
   - fitting: _not stated_
   - validation: Compared moment 0 maps and spatial profiles along disk semi-major axes before and after continuum subtraction to evaluate continuum over-subtraction.  
  > "To evaluate the effects of continuum over-subtraction, we generated spatial profiles for each disk using 12CO moment 0 maps at small scales before and after continuum subtraction. We created cuts that crossed the semi-major axis of each disk (see red lines in Figure A1, top panels) for this purpose." (APPENDIX A: EFFECTS OF CONTINUUM OVER-SUBTRACTION)

## Software

- **CASA** v.5.5: Data calibration, self-calibration, concatenation, continuum subtraction, continuum and spectral line imaging, 2D Gaussian fitting, and channel rms statistics  
  > "The data were calibrated with the Common Astronomy Software Applications package (CASA v.5.5, McMullin et al. 2007), and the python modules from CASA API, casatasks and casatools (CASA Team et al. 2022)." (2 OBSERVATIONS AND DATA REDUCTION); "The image synthesis of the 1.3 mm continuum emission was performed with the tclean task of CASA." (2.1 Continuum imaging); "We performed a 2D Gaussian fitting with the imfit tool of CASA in order to characterize the newly resolved components." (3.1 Continuum analysis)
- **casatasks** : Calibration and data reduction via CASA Python API  
  > "The data were calibrated with the Common Astronomy Software Applications package (CASA v.5.5, McMullin et al. 2007), and the python modules from CASA API, casatasks and casatools (CASA Team et al. 2022)." (2 OBSERVATIONS AND DATA REDUCTION)
- **casatools** : Calibration and data reduction via CASA Python API  
  > "The data were calibrated with the Common Astronomy Software Applications package (CASA v.5.5, McMullin et al. 2007), and the python modules from CASA API, casatasks and casatools (CASA Team et al. 2022)." (2 OBSERVATIONS AND DATA REDUCTION)
- **tclean** : Image synthesis of 1.3 mm continuum and CO isotopologue spectral lines  
  > "The image synthesis of the 1.3 mm continuum emission was performed with the tclean task of CASA." (2.1 Continuum imaging); "Next, we performed the tclean process using Briggs weighting with a robust parameter of 0.5, Hogbom deconvolver, and pixel scale of 6 mas." (2.2 Line imaging)
- **concat** : Combining short and long baseline visibilities into a concatenated measurement set  
  > "Our final continuum image was produced from a concatenated measurement set combining both, the short and the long baseline visibilities, using the concat task of CASA." (2.1 Continuum imaging)
- **uvcontsub** : Removing continuum contribution from spectral line visibilities  
  > "Therefore, we proceeded to remove the visibility’s continuum contributions by using the CASA task uvcontsub." (2.2 Line imaging)
- **imfit** : 2D Gaussian fitting of the continuum disks HBC 494 N and HBC 494 S  
  > "We performed a 2D Gaussian fitting with the imfit tool of CASA in order to characterize the newly resolved components." (3.1 Continuum analysis)
- **imstat** : Calculating rms values in each channel of the spectral line cubes  
  > "The rms values were calculated using all data in each channel, through the CASA task imstat." (Figure B1 caption)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Projected separation between HBC 494 N and HBC 494 S | 0.18 (75) | not stated | arcsec (au) | 2 | The projected separation between the two sources is 0′′.18 (75 au). |
| Unprojected separation between HBC 494 N and HBC 494 S (assuming quasi-coplanar) | 0.24 (99) | not stated | arcsec (au) | 2 | Assuming they are quasi-coplanar, with the same PA, the unprojected separation would be ∼0′′.24 (99 au). |
| HBC 494 N continuum integrated flux density | 105.17 (105.2 in Table 2) | ± 1.89 (± 1.9 in Table 2) | mJy | 2 | The integrated fluxes for “N” and “S” are 105.17 ± 1.89 mJy and 21.06 ± 0.63 mJy, respectively.; Flux density (mJy) 105.2 ± 1.9 21.1 ± 0.6 |
| HBC 494 S continuum integrated flux density | 21.06 (21.1 in Table 2) | ± 0.63 (± 0.6 in Table 2) | mJy | 2 | The integrated fluxes for “N” and “S” are 105.17 ± 1.89 mJy and 21.06 ± 0.63 mJy, respectively.; Flux density (mJy) 105.2 ± 1.9 21.1 ± 0.6 |
| HBC 494 N continuum peak flux | 22.96 (23.0 in Table 2) | ± 0.35 (± 0.4 in Table 2) | mJy/beam | 2 | The peak fluxes are 22.96 ± 0.35 mJy/beam and 8.71 ± 0.21 mJy/beam for the primary and secondary sources, respectively.; Peak flux (mJy / beam) 23.0 ± 0.4 8.7 ± 0.2 |
| HBC 494 S continuum peak flux | 8.71 (8.7 in Table 2) | ± 0.21 (± 0.2 in Table 2) | mJy/beam | 2 | The peak fluxes are 22.96 ± 0.35 mJy/beam and 8.71 ± 0.21 mJy/beam for the primary and secondary sources, respectively.; Peak flux (mJy / beam) 23.0 ± 0.4 8.7 ± 0.2 |
| HBC 494 N deconvolved major axis FWHM | 84.00 (84.0 in Table 2) | ± 1.82 (± 1.8 in Table 2) | mas | 2 | For the primary component, we find a major axis FWHM of 84.00 ± 1.82 mas and a minor axis of 66.94 ± 1.50 mas (34.8 ± 0.7 × 27.8 ± 0.6 au), with a position angle of 70.01 ± 4.46 deg (values deconvolved from the beam).; Major axis (mas) 84.0 ± 1.8 64.6 ± 2.5 |
| HBC 494 N deconvolved minor axis FWHM | 66.94 (66.9 in Table 2) | ± 1.50 (± 1.5 in Table 2) | mas | 2 | For the primary component, we find a major axis FWHM of 84.00 ± 1.82 mas and a minor axis of 66.94 ± 1.50 mas (34.8 ± 0.7 × 27.8 ± 0.6 au), with a position angle of 70.01 ± 4.46 deg (values deconvolved from the beam).; Minor axis (mas) 66.9 ± 1.5 46.0 ± 1.9 |
| HBC 494 N deconvolved major axis FWHM (physical) | 34.8 | ± 0.7 | au | 2 | Major axis (au) 34.8 ± 0.7 26.7 ± 1.0 |
| HBC 494 N deconvolved minor axis FWHM (physical) | 27.8 | ± 0.6 | au | 2 | Minor axis (au) 27.8 ± 0.6 19.9 ± 0.8 |
| HBC 494 N position angle | 70.01 (70.0 in Table 2) | ± 4.46 (± 4.5 in Table 2) | deg | 2 | with a position angle of 70.01 ± 4.46 deg (values deconvolved from the beam).; Position angle (deg) 70.0 ± 4.5 65.4 ± 5.3 |
| HBC 494 S deconvolved major axis FWHM | 64.60 (64.6 in Table 2) | ± 2.49 (± 2.5 in Table 2) | mas | 2 | For the secondary, the major axis FWHM is 64.60 ± 2.49 mas and the minor axis FWHM is 45.96 ± 1.89 mas (26.7 ± 1.0 × 19.9 ± 0.8 au), and the position angle is 65.38 ± 5.32 deg.; Major axis (mas) 84.0 ± 1.8 64.6 ± 2.5 |
| HBC 494 S deconvolved minor axis FWHM | 45.96 (46.0 in Table 2) | ± 1.89 (± 1.9 in Table 2) | mas | 2 | For the secondary, the major axis FWHM is 64.60 ± 2.49 mas and the minor axis FWHM is 45.96 ± 1.89 mas (26.7 ± 1.0 × 19.9 ± 0.8 au), and the position angle is 65.38 ± 5.32 deg.; Minor axis (mas) 66.9 ± 1.5 46.0 ± 1.9 |
| HBC 494 S deconvolved major axis FWHM (physical) | 26.7 | ± 1.0 | au | 2 | Major axis (au) 34.8 ± 0.7 26.7 ± 1.0 |
| HBC 494 S deconvolved minor axis FWHM (physical) | 19.9 | ± 0.8 | au | 2 | Minor axis (au) 27.8 ± 0.6 19.9 ± 0.8 |
| HBC 494 S position angle | 65.38 (65.4 in Table 2) | ± 5.32 (± 5.3 in Table 2) | deg | 2 | and the position angle is 65.38 ± 5.32 deg.; Position angle (deg) 70.0 ± 4.5 65.4 ± 5.3 |
| HBC 494 N inclination | 37.16 (37.2 in Table 2) | ± 2.36 (± 2.4 in Table 2) | deg | 2 | It resulted in 37.16 ± 2.36 degrees inclination for HBC 494 N; Inclination (deg) 37.2±2.4 44.7±3.3 |
| HBC 494 S inclination | 44.65 (44.7 in Table 2) | ± 3.27 (± 3.3 in Table 2) | deg | 2 | 44.65 ± 3.27 for HBC 494 S; Inclination (deg) 37.2±2.4 44.7±3.3 |
| HBC 494 N dust mass | 1.43 (1.4 in Table 2) | not stated | M_Jup | 3 | we get dust masses of 1.43 𝑀Jup (HBC 494 N) and 0.29 𝑀Jup (HBC 494 S).; Dust mass (𝑀Jup ) 1.4 0.3 |
| HBC 494 S dust mass | 0.29 (0.3 in Table 2) | not stated | M_Jup | 3 | we get dust masses of 1.43 𝑀Jup (HBC 494 N) and 0.29 𝑀Jup (HBC 494 S).; Dust mass (𝑀Jup ) 1.4 0.3 |
| HBC 494 N gas mass | 143.46 (143.5 in Table 2) | not stated | M_Jup | 3 | Following the standard gas-to-dust mass ratio of 100, we report disk gas masses estimations of 143.46 𝑀Jup for HBC 494 N, and 28.68 𝑀Jup for HBC 494 S.; Gas mass (𝑀Jup ) 143.5 28.7 |
| HBC 494 S gas mass | 28.68 (28.7 in Table 2) | not stated | M_Jup | 3 | Following the standard gas-to-dust mass ratio of 100, we report disk gas masses estimations of 143.46 𝑀Jup for HBC 494 N, and 28.68 𝑀Jup for HBC 494 S.; Gas mass (𝑀Jup ) 143.5 28.7 |
| Inclination difference (Delta i) between HBC 494 N and S | 7.5 | ± 4.1 | deg | 2 | The HBC 494 disks have similar inclinations (Δ𝑖 = 7.5 ± 4.1 degrees) and similar PAs (Δ𝑃𝐴 = 4.6 ± 7.0 degrees). |
| Position angle difference (Delta PA) between HBC 494 N and S | 4.6 | ± 7.0 | deg | 2 | The HBC 494 disks have similar inclinations (Δ𝑖 = 7.5 ± 4.1 degrees) and similar PAs (Δ𝑃𝐴 = 4.6 ± 7.0 degrees). |

## Qualitative findings

- HBC 494 is resolved into a binary system (HBC 494 N and HBC 494 S) with two individual circumstellar disks and no detected circumbinary disk or internal disk substructures at 30 mas resolution.  
  > "Here, we present follow-up observations at ∼0′′.03, resolving the system into two components: HBC 494 N (primary) and HBC 494 S (secondary). No circumbinary disk was detected." (ABSTRACT); "At 30 mas resolution, no substructures were detected (see the radial profiles in Figure 3)." (3.1 Continuum analysis)
- At large scales (8000 au), 12CO traces wide-angle (~150 deg) bipolar outflow arcs while 13CO and C18O trace a rotating, infalling, and expanding envelope with a rotation axis nearly perpendicular to the outflow.  
  > "show southern and northern 12 CO wide-angle arcs (∼ 150 ◦ ) and no clear signal of large structures" (3.2.1 Large-scale structures (8000 au)); "The 13CO emission traces the rotating, infalling, and expanding envelope surrounding the system, showing a small deviation from the 12CO outflowing arcs’ rotation axis." (3.2.1 Large-scale structures (8000 au)); "It is noticeable that the 13CO emission has a rotation axis almost perpendicular to the 12CO outflows axis, ensuring that the physical processes behind the two are different." (3.2.1 Large-scale structures (8000 au))
- At small scales (150 au), continuum-subtracted 12CO and 13CO moment 0 maps show cavities/holes at the continuum disk positions and no clear rotational signatures.  
  > "However, by looking at the molecular lines in this scale (see the moment maps in Figure 7, left and middle columns), we could not clearly detect the presence of the disks or their rotational signatures." (3.2.2 Small scale structures (150 au resolution)); "Additionally, the area within the continuum disks highlights regions similar to cavities or “holes" (Figure 7, left column, upper and middle row)." (3.2.2 Small scale structures (150 au resolution))

## Claim tuples

- H: The elongation and asymmetry previously observed in the millimeter continuum of HBC 494 at ~0.25 arcsec resolution is caused by an unresolved structure or a secondary disk. | E: Observed HBC 494 with ALMA Band 6 at ~0.03 arcsec resolution combining short and long baseline configurations and fitted 2D Gaussians with CASA imfit. | R: Resolved two continuum disks, HBC 494 N (105.2 mJy, 84.0 x 66.9 mas) and HBC 494 S (21.1 mJy, 64.6 x 46.0 mas), separated by 0.18 arcsec (75 au), with no detected substructures or circumbinary disk. | F: HBC 494 is a binary system where the primary disk is ~5 times brighter/more massive and ~2 times bigger than the secondary disk. | **supported**
- H: Eruptive YSO disks (FUors/EXors) are more massive than typical Class 0/I disks, and disks in multiple systems are smaller than those in single systems due to dynamical interactions. | E: Calculated dust masses (assuming T=20 K and optically thin emission) and deconvolved FWHM/2 radii for HBC 494 N and S and compared them against literature samples of resolved FUors, EXors, and Class 0/I disks. | R: HBC 494 N has M_dust = 1.43 M_Jup (comparable to FUors) and HBC 494 S has M_dust = 0.29 M_Jup (comparable to EXors); both disks are smaller than single eruptive YSO disks. | F: HBC 494 disks preserve high masses typical of eruptive systems while their sizes are smaller than single eruptive YSOs, consistent with tidal truncation and dynamical evolution in multiple systems. | **supported**
- H: Close-separation binary systems like HBC 494 form via rotational disk fragmentation, which produces spin-aligned and coplanar disks, rather than direct/turbulent core fragmentation. | E: Derived the inclinations and position angles of HBC 494 N and HBC 494 S from 2D Gaussian fits to the continuum emission and compared their relative orientations. | R: The disks have very similar inclinations (Delta i = 7.5 ± 4.1 deg) and position angles (Delta PA = 4.6 ± 7.0 deg). | F: The HBC 494 disks are in a quasi-coplanar, spin-aligned configuration, tentatively suggesting formation by rotational disk fragmentation, though small-scale gas kinematics and astrometry are needed to confirm. | **partially**
- H: Cavities observed in the small-scale continuum-subtracted 12CO and 13CO moment 0 maps within the continuum disk areas trace either physical gas removal/chemical destruction by jets/radiation or an artifact of continuum over-subtraction due to optically thick lines. | E: Produced small-scale CO moment 0 maps and spatial profiles along the disk semi-major axes before and after uvcontsub continuum subtraction. | R: Spatial profiles show that continuum overestimation due to foreground optically thick line absorption propagated through uvcontsub, creating cavities at the continuum peak positions. | F: The cavities in the small-scale 12CO and 13CO moment 0 maps may be caused by slow-moving outflows/chemical destruction or by optical depth effects and continuum over-subtraction; optically thinner lines are required to recover the true disk gas signal. | **partially**

## Reasoning

- Why this data: Earlier ALMA Cycle 2 observations at ~0.25 arcsec resolution showed an elongated, asymmetric disk around HBC 494, requiring follow-up at ~0.03 arcsec resolution to resolve the substructure or secondary disk.  
  > "ALMA Cycle-2 observations in the millimeter continuum (∼0′′.25 angular resolution) show that the disk is elongated with an apparent asymmetry (Cieza et al. 2018), indicating the presence of an unresolved structure or a secondary disk. In this work, we present ALMA Cycle 4 observations at ∼0′′.03 angular resolution that reveal the binary nature of the HBC 494 system." (1 INTRODUCTION)
- Why this method: Used uvcontsub because unsubtracted line dirty images mimicked gaseous envelopes around the disks without revealing gas dynamic signatures; used deconvolved Gaussian FWHM/2 radii and standard isothermal 20 K optically thin dust mass formula to allow consistent comparison with other ALMA disk surveys.  
  > "After producing a dirty image from the visibilities, we noticed that the emission mimicked the presence of gaseous envelopes around the disks (moment 0 maps, see Figure 1, left column) but no gas dynamic signatures were revealed (moment 1 map, see Figure 1, right column). Therefore, we proceeded to remove the visibility’s continuum contributions by using the CASA task uvcontsub." (2.2 Line imaging); "The disk sizes were calculated using the deconvolved Gaussian FWHM/2 radius obtained from 2D Gaussian fits. This methodology was also used for other ALMA datasets (e.g., Hales et al. 2020; Tobin et al. 2020). Therefore, it allows a consistent comparison with other disks." (4.2 Disk sizes and masses)
- Alternative: Gravitational instability (GI), infall, or stellar flybys as outburst triggering mechanisms were not supported because no spiral, clumpy, or perturbation features were detected in the dust or gas maps.  
  > "For each HBC 494 disk, no clue of trigger mechanisms was found, since the gas and continuum data did not reveal clear spiral or clumpy features indicating a case of infall or GI (see e.g., Zhu et al. 2012; Kratter & Lodato 2016)." (4.1 Multiplicity and triggering mechanisms); "Looking at the dust continuum (Figure 2), CO isotopologues moment maps (Figure 7), and the scattered 12CO emission (Figure 12 of Ruíz-Rodríguez et al. 2017), the hypothesis of stellar flybys is also not encouraged since no trace of perturbation was detected (Cuello et al. 2020, 2023)." (4.1 Multiplicity and triggering mechanisms)
- Alternative: Manually adding back lost line signal to correct for continuum over-subtraction was rejected because it would only create fake signal at the noise level.  
  > "The "holes" or cavities seen in the top-right panel could potentially be diminished by manually adding back some of the lost line signal, but this would only create a fake signal at the level of noise." (APPENDIX A: EFFECTS OF CONTINUUM OVER-SUBTRACTION)
- How they decided it was enough: _not stated_
- Limitation (authors): Optically thin dust approximation does not account for optically thick inner disk regions, which can underestimate dust masses, while assuming a fixed 20 K dust temperature can overestimate masses if the dust is warmer.  
  > "However, it is worth mentioning that the optically thin analysis can not take into account the innermost regions of the disk (optically thick). This may lead to an underestimation of the dust masses. Also, an underlying miscalculated dust grain temperature can alter the results, overestimating the masses if the dust is warmer than expected." (4.2 Disk sizes and masses)
- Limitation (authors): Cloud contamination and optical depth effects mask small-scale disk rotational kinematics, prevent detection of a circumbinary gas disk, and cause continuum over-subtraction in uvcontsub.  
  > "However, no HBC 494 circumbinary gas disk was observed due to cloud contamination and optical depth effects." (4.1 Multiplicity and triggering mechanisms); "The dynamics of both disks in such scales were masked principally by cloud contamination." (5 CONCLUSIONS)
- Limitation (authors): Using only the 12-m main array data filters out extended emission on large scales, which requires combining with ALMA single-dish/ACA data to fully recover.  
  > "It also shows some significant contours on both horizontal extremes, which can be tracers of the filtered signals using only the main array data. The data partially trace features that, due to their large extension, require a combination of the ALMA main and single dish arrays to recover extended flux emission." (APPENDIX B: 12CO, 13CO AND C18O CHANNEL MAPS WITH CONTOURS AND THE EFFECT OF CLOUD CONTAMINATION)
- Caveat (inferred, ours): In Table 2, the rows labeled 'Major axis (au)' (34.8 and 26.7 au) and 'Minor axis (au)' (27.8 and 19.9 au) actually list the FWHM in au, and the row labeled 'FWHM Radius (au)' repeats 34.8 and 26.7 au, whereas at 414 pc an FWHM of 84.0 mas corresponds to 34.8 au diameter (so FWHM/2 radius R_c is ~17.4 au and ~13.4 au, as plotted in Figure 8).
- Caveat (inferred, ours): Assuming T_dust = 20 K for an outbursting FUor object (~250 L_sun) likely overestimates the dust mass significantly compared to radiative transfer models of heated disks.

## Reproducibility

- Data public (paper): Public and downloadable from the official ALMA archive (ADS/JAO.ALMA 2016.1.00630.S)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2016.1.00630.S. The data are downloadable from the official ALMA archive and public." (DATA AVAILABILITY)
- Products in archive: _not stated_
- Missing: Self-calibration parameters (solution interval, calibration mode, reference antenna, clean threshold/masking).
- Missing: Exact channel ranges used for continuum fitting in uvcontsub.
- Missing: Whether the large-scale (8000 au) line cubes were imaged from the short-baseline dataset alone or the concatenated dataset, and their synthesized beam sizes.
- Data volume (inferred): ~20-50 GB (two Band 6 12-m array execution blocks, one compact and one long-baseline at 0.027 arcsec resolution with high spectral resolution CO windows).
- Score (inferred): 78/5, Raw data are public, CASA version and core imaging/fitting tasks (tclean, concat, uvcontsub, imfit) and key parameters (robust=0.5, pixel scales, velocity ranges, dust mass formula and constants) are explicitly stated; slight deductions for missing self-calibration solint and uvcontsub channel selection details.
- Rediscovery candidate: yes, Public ALMA data (2016.1.00630.S) with a straightforward imaging + CASA imfit + analytical dust mass recipe yielding clear, high-SNR numeric results for the binary separation, disk fluxes, deconvolved sizes, inclinations, and masses.

## Links

- Method: Beckwith et al. 1990 (Dust opacity law and optically thin isothermal dust mass formula)
- Method: Andrews & Williams 2005 (Optically thin dust mass estimation from millimeter continuum)
- Method: Cieza et al. 2018 (Dust mass estimation formula and Cycle 2 observations of HBC 494)
- Method: Hales et al. 2020 (Disk characteristic radius (deconvolved Gaussian FWHM/2) methodology and comparison sample)
- Method: Tobin et al. 2020 (Disk size methodology and Orion Class 0/I comparison sample)
- Companion: Cieza et al. 2018 (Earlier ALMA Cycle 2 continuum observations (~0.25 arcsec) of HBC 494 that showed the disk asymmetry)
- Companion: Ruíz-Rodríguez et al. 2017 (Earlier ALMA Cycle 2 molecular line observations of the large-scale outflows and envelope in HBC 494)

## Checks

```json
{
 "quotes": 155,
 "quotes_ok": 155,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 17,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 60,
  "rate": 0.75
 },
 "evidence_ok": true
}
```
