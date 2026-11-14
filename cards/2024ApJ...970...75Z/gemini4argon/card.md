# The Resolved Star Formation Law in NGC 7469 from JWST, ALMA, and VLA

`2024ApJ...970...75Z` | The Astrophysical Journal 2024 | first author: Zanchettin, Maria Vittoria | arXiv: 2406.07901 | DOI: 10.3847/1538-4357/ad57bd

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars, star_formation
- Question: Investigate the spatially resolved star formation process and correlations between PAHs, star formation rate surface density, and cold molecular gas mass surface density within the central 3.3 kpc region of NGC 7469.  
  > "We investigate the star formation process within the central 3.3 kpc region of the nearby luminous infrared Seyfert NGC 7469, probing scales ranging from 88 to 330 pc." (abstract); "We further investigate the correlations between the PAHs, the star formation rate and the cold molecular gas." (abstract); "We derive the correlation between the star formation rate and the cold molecular gas mass surface densities, the Kennicutt-Schmidt star formation law." (abstract)
- Target **NGC 7469**: coordinates 23:03:15.617 +08:52:26.00 J2000  
  > "In this paper, we study the SF process in the inner (∼ 3 kpc) region of NGC 7469, a nearby (z = 0.01627) luminous infrared galaxy" (1. INTRODUCTION); "The adopted luminosity distance of the galaxy is 72.1 Mpc and the corresponding scale is 0.338 kpc/arcsec." (1. INTRODUCTION); "We used the task os.system to model a point source at the AGN position (23:03:15.617 +08:52:26.00 J2000, Izumi et al. 2020)" (3. ANALYSIS); z/distance z = 0.01627; D_L = 72.1 Mpc (0.338 kpc/arcsec)  
  > "In this paper, we study the SF process in the inner (∼ 3 kpc) region of NGC 7469, a nearby (z = 0.01627) luminous infrared galaxy" (1. INTRODUCTION); "The adopted luminosity distance of the galaxy is 72.1 Mpc and the corresponding scale is 0.338 kpc/arcsec." (1. INTRODUCTION); "We used the task os.system to model a point source at the AGN position (23:03:15.617 +08:52:26.00 J2000, Izumi et al. 2020)" (3. ANALYSIS); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00078.S
- bands: Band 6 (1.3 mm)  
  > "We combine JWST/MIRI imaging with the F770W filter, with CO(2-1) and the underlying 1.3 mm dust continuum data from ALMA" (abstract); "We analyzed band 6 ALMA 12 m observations (program ID 2017.1.00078.S, PI Izumi Takuma) of NGC 7469 of the CO(2-1) line (observed frequency 226.85 GHz) and the underlying continuum (224.2-243.7 GHz)." (2. OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: CO(2-1) observed frequency 226.85 GHz, underlying continuum 224.2-243.7 GHz across 4 spectral windows, channel width 5 km s^-1  
  > "We analyzed band 6 ALMA 12 m observations (program ID 2017.1.00078.S, PI Izumi Takuma) of NGC 7469 of the CO(2-1) line (observed frequency 226.85 GHz) and the underlying continuum (224.2-243.7 GHz)." (2. OBSERVATIONS AND DATA REDUCTION); "The CO(2-1) data cube has a beam size of 0.508 arcsec × 0.374 arcsec and a rms noise of 0.518 mJy/beam for a channel width of 5 km s^-1." (2. OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: 12 m array (44 antennas)  
  > "NGC 7469 was observed in September 2018 by using the 12m array for a total integration time of 1.48 h in the configuration C43-4 with 44 antennas" (2. OBSERVATIONS AND DATA REDUCTION)
- configurations: C43-4  
  > "NGC 7469 was observed in September 2018 by using the 12m array for a total integration time of 1.48 h in the configuration C43-4 with 44 antennas" (2. OBSERVATIONS AND DATA REDUCTION)
- baselines: _not stated_
- angular resolution: ~0.4 arcsec (0.492 arcsec x 0.360 arcsec for continuum; 0.508 arcsec x 0.374 arcsec for CO(2-1))  
  > "proving an angular resolution of about 0.4 arcsec and a largest angular scale of 4.8 arcsec." (2. OBSERVATIONS AND DATA REDUCTION); "The resulting synthesized beam for the continuum map is 0.492 arcsec × 0.360 arcsec (corresponding to 164 pc × 120 pc), with an rms of 0.0121 mJy/beam." (2. OBSERVATIONS AND DATA REDUCTION); "The CO(2-1) data cube has a beam size of 0.508 arcsec × 0.374 arcsec and a rms noise of 0.518 mJy/beam for a channel width of 5 km s^-1." (2. OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: 4.8 arcsec  
  > "proving an angular resolution of about 0.4 arcsec and a largest angular scale of 4.8 arcsec." (2. OBSERVATIONS AND DATA REDUCTION)
- sensitivity: 0.0121 mJy/beam (1.3 mm continuum); 0.518 mJy/beam per 5 km s^-1 channel (CO(2-1) cube, or 7.8 M_sun/beam); 0.56 Jy/beam.km/s (CO(2-1) moment-0)  
  > "The resulting synthesized beam for the continuum map is 0.492 arcsec × 0.360 arcsec (corresponding to 164 pc × 120 pc), with an rms of 0.0121 mJy/beam." (2. OBSERVATIONS AND DATA REDUCTION); "The CO(2-1) data cube has a beam size of 0.508 arcsec × 0.374 arcsec and a rms noise of 0.518 mJy/beam for a channel width of 5 km s^-1." (2. OBSERVATIONS AND DATA REDUCTION); "Right panel: velocity integrated CO(2-1) (moment-0) map. White contours are drawn at (3, 5, 10, 15, 20, 30) σ, σ = 0.56 Jy/beam.km/s." (Figure 1 caption)
- time on source: 1.48 h (total integration time)  
  > "NGC 7469 was observed in September 2018 by using the 12m array for a total integration time of 1.48 h in the configuration C43-4 with 44 antennas" (2. OBSERVATIONS AND DATA REDUCTION)
- observing dates: September 2018  
  > "NGC 7469 was observed in September 2018 by using the 12m array for a total integration time of 1.48 h in the configuration C43-4 with 44 antennas" (2. OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: Archival (PI Izumi Takuma)  
  > "We analyzed band 6 ALMA 12 m observations (program ID 2017.1.00078.S, PI Izumi Takuma) of NGC 7469 of the CO(2-1) line (observed frequency 226.85 GHz) and the underlying continuum (224.2-243.7 GHz)." (2. OBSERVATIONS AND DATA REDUCTION)
- Line: CO 2-1 (not stated (observed frequency 226.85 GHz))
- Other facility **VLA**: Archival K-band (18-26 GHz, centered at 22 GHz) radio continuum observations (project code 20A-158, PI Krista L. Smith), observed April 2020 for 58.9 h, beam 1.029 arcsec x 0.967 arcsec, rms 23.2 uJy/beam.  
  > "We analysed archival VLA observations of NGC 7469 in band K (project code 20A-158, PI Krista L. Smith). The observations were carried out in April 2020 for a total integration time of 58.9 h in the frequency range 18-26 GHz." (2. OBSERVATIONS AND DATA REDUCTION); "The final continuum map has an rms of 23.2 µJy/beam and a clean beam of 1.029 arcsec × 0.967 arcsec (i.e. 342 pc × 322 pc)." (2. OBSERVATIONS AND DATA REDUCTION)
- Other facility **JWST/MIRI**: F770W (7.7 um) SUB128 subarray imaging (program ID 1328, PI Armus Lee, MAST DOI 10.17909/3x02-0q74), observed 2022 July 2 with 48 s exposure, FoV 14.8 arcsec x 16.4 arcsec, pixel size 0.11 arcsec, sensitivity 12 MJy sr^-1 pixel^-1.  
  > "JWST/MIRI (Bouchet et al. 2015; Rieke et al. 2015) imaging of NGC 7469 was obtained with the F770W (7.7 µm) filter with both the BRIGHTSKY and SUB128 subarray modes (program ID 1328, PI Armus Lee)." (2. OBSERVATIONS AND DATA REDUCTION); "In this paper we focus the analysis on the SUB128 subarray data, where the nucleus remained unsaturated, taken on 2022 July 2 with an exposure time of 48 s." (2. OBSERVATIONS AND DATA REDUCTION); "The field of view of 14.8 arcsec × 16.4 arcsec and the pixel size is 0.11 arcsec. The calibrated JWST/MIRI 7.7 µm map has a sensitivity of 12 MJy sr^-1 pixel^-1." (2. OBSERVATIONS AND DATA REDUCTION)
- Other facility **NED**: Integrated radio fluxes used to fit the radio SED and obtain the average radio spectral index alpha = -0.85.  
  > "by fitting the radio Spectral Energy Distribution (SED) using the integrated radio fluxes reported by NED" (3. ANALYSIS)
- External data: AGN position (23:03:15.617 +08:52:26.00 J2000) and naming of continuum clumps A to D.  
  > "We used the task os.system to model a point source at the AGN position (23:03:15.617 +08:52:26.00 J2000, Izumi et al. 2020) with a flux of 5.037 mJy at 22 GHz" (3. ANALYSIS); "Clumps from A to D are named as in Izumi et al. (2020), who first identified the clumps using the ALMA 860 µm continuum map." (4.1. Morphology of the SB ring) [from Izumi et al. 2020]
- External data: Galaxy inclination angle i = 45 deg.  
  > "The cos i factor is the correction for galaxy inclination, which we assume i =45 deg (Davies et al. 2004)." (3. ANALYSIS) [from Davies et al. 2004]
- External data: Stellar mass log(M_*/M_sun) = 10.5.  
  > "for a stellar mass of log(M∗/M⊙) = 10.5" (3. ANALYSIS) [from Díaz-Santos et al. 2007]
- External data: CO ladder correction factor R_21 = 0.7 and K-S relation for local AGN host galaxies: log Sigma_SFR = (1.14 +- 0.01) log Sigma_H2 + (-3.41 +- 0.02).  
  > "We adopt a CO ladder correction factor of R_21 = 0.7 equal to the mean value found by Casasola et al. (2015)" (3. ANALYSIS); "The purple shaded area shows the range of values found by Casasola et al. (2015) for local AGN host galaxies: logΣ_SFR = (1.14 ± 0.01)logΣ_H2 + (−3.41 ± 0.02)." (Figure 4 caption) [from Casasola et al. 2015]
- External data: Outer starburst ring radius r_SB ~ 900 pc.  
  > "where r_SB ∼ 900pc is the outer SB ring radius (Song et al. 2021)." (Figure 3 caption); "To quantify this steepening, we divided the data into two subsamples: an inner region within the SB ring (r < r_SB) and an outer region with r > r_SB, where r_SB = 900 pc. This value has been measured by (Song et al. 2021)" (4.2. PAH emission) [from Song et al. 2021]
- External data: Spatially resolved star formation law measurements for NGC 2992 on ~200 pc scales.  
  > "Triangles show the derived quantities for NGC 2992 (Zanchettin et al. 2023)." (Figure 4 caption); "The plot also includes NGC 2992 measurements obtained with a similar method on ∼ 200 pc scales (Zanchettin et al. 2023)" (4.3. The star formation law) [from Zanchettin et al. 2023]
- External data: Best-fit K-S correlation for dusty starbursts and U/LIRGs: log Sigma_SFR = (0.98 +- 0.07) log Sigma_H2 + (-2.27 +- 0.21) with 0.33 dex scatter.  
  > "The yellow shaded area shows the best-fit correlation with 0.33 dex scatter found using global measurements for (Kennicutt & De Los Reyes 2021): logΣ_SFR = (0.98 ± 0.07)logΣ_H2 + (−2.27 ± 0.21)." (Figure 4 caption) [from Kennicutt & De Los Reyes 2021]
- Simulation/model as data: Simulated point-spread function (PSF) of the JWST/MIRI F770W filter image generated with WebbPSF version 1.2.1 with a pixel size of 0.027 arcsec.  
  > "tool version 1.2.1 (Perrin et al. 2014) to simulate the point-spread function (PSF) of the JWST/MIRI F770W filter image, with a pixel size of 0.027 arcsec" (3. ANALYSIS)

## Processing

### Calibration

- pipeline or manual: Standard pipeline by NRAO Observatory with default calibrators  
  > "Visibilities were calibrated by the NRAO Observatory, using the standard pipeline and default calibrators." (2. OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Imaging was performed with task tclean using the hogbom algorithm, a threshold of three times the root mean square (rms) noise" (2. OBSERVATIONS AND DATA REDUCTION)
- deconvolver: hogbom  
  > "Imaging was performed with task tclean using the hogbom algorithm, a threshold of three times the root mean square (rms) noise" (2. OBSERVATIONS AND DATA REDUCTION)
- weighting robust: Briggs weighting with robust b = 0.5 for 1.3 mm continuum (and VLA 22 GHz continuum); natural weighting for CO(2-1) data cube  
  > "a briggs weighting scheme with robust parameter b = 0.5 for the continuum map and a natural weighting scheme for the CO(2-1) data cube in order to increase the map sensitivity." (2. OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: First-order polynomial fit and subtraction in uv-plane from the spw covering CO(2-1); for continuum map, averaged visibilities in the four spws excluding the CO(2-1) spectral range  
  > "We created a continuum map by averaging the visibilities in the four spectral windows (spws), excluding the spectral range covered by the CO(2-1) emission line." (2. OBSERVATIONS AND DATA REDUCTION); "We produced continuum-subtracted datacubes by fitting and subtracting a first-order polynomial from the visibilities of the spw covering CO(2-1)." (2. OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All maps regridded to the VLA spatial resolution (1 arcsec squared cells) for common grid extraction  
  > "First, we regridded all the maps at the VLA spatial resolution, i.e. the coarser resolution of our data. The grid is centered at the AGN position and has 1 arcsec wide (i.e. 0.330 kpc) squared cells, equal to regridded maps resolution, and a total size of 10 arcsec × 10 arcsec (i.e. 3.3 kpc × 3.3 kpc)." (3. ANALYSIS)
- final beam: 0.492 arcsec x 0.360 arcsec, PA = 46 deg (1.3 mm continuum); 0.508 arcsec x 0.374 arcsec, PA = 45 deg (CO(2-1) cube); 1.029 arcsec x 0.967 arcsec, PA = -13 deg (VLA 22 GHz)  
  > "The resulting synthesized beam for the continuum map is 0.492 arcsec × 0.360 arcsec (corresponding to 164 pc × 120 pc), with an rms of 0.0121 mJy/beam." (2. OBSERVATIONS AND DATA REDUCTION); "The CO(2-1) data cube has a beam size of 0.508 arcsec × 0.374 arcsec and a rms noise of 0.518 mJy/beam for a channel width of 5 km s^-1." (2. OBSERVATIONS AND DATA REDUCTION); "The clean beam (0.492 arcsec × 0.360 arcsec, PA=46 deg) is indicated by the gray ellipse." (Figure 1 caption); "The clean beam (0.508 × 0.374 arcsec, PA=45 deg) is indicated by the gray ellipse." (Figure 1 caption)
- final rms: 0.0121 mJy/beam (1.3 mm continuum); 0.518 mJy/beam per 5 km s^-1 channel (CO(2-1) cube); 0.56 Jy/beam.km/s (CO(2-1) moment-0); 23.2 uJy/beam (VLA 22 GHz)  
  > "The resulting synthesized beam for the continuum map is 0.492 arcsec × 0.360 arcsec (corresponding to 164 pc × 120 pc), with an rms of 0.0121 mJy/beam." (2. OBSERVATIONS AND DATA REDUCTION); "The CO(2-1) data cube has a beam size of 0.508 arcsec × 0.374 arcsec and a rms noise of 0.518 mJy/beam for a channel width of 5 km s^-1." (2. OBSERVATIONS AND DATA REDUCTION); "Right panel: velocity integrated CO(2-1) (moment-0) map. White contours are drawn at (3, 5, 10, 15, 20, 30) σ, σ = 0.56 Jy/beam.km/s." (Figure 1 caption)

### Inherited from earlier work

- Conversion factor F_21 from CO flux density to line luminosity L' in K km s^-1 pc^2.  
  > "where F_21 is the conversion factor from the flux density to the line luminosity L' in K km s^-1 pc^2 (see Solomon & Vanden Bout 2005)" (3. ANALYSIS) [from Solomon & Vanden Bout 2005]
- CO-to-H2 conversion factor alpha_CO = 4.2 (+1.961/-1.341) M_sun (K km s^-1 pc^2)^-1 derived from equation 25.  
  > "equation 25 in Accurso et al. (2017), for a stellar mass of" (3. ANALYSIS) [from Accurso et al. 2017]
- Radio 1.4 GHz luminosity to SFR calibration.  
  > "SFR adopting the correlation reported by Shao et al. (2018) in section 3.2" (3. ANALYSIS); "We estimate the global SFR integrated over the central 3.3 kpc × 3.3 kpc into SFR = 11.5 ± 0.3 M_⊙ yr^-1, following the prescription of Shao et al. (2018), see Section 3." (4.1. Morphology of the SB ring) [from Shao et al. 2018]
- Assumption that 90% of the JWST/MIRI F770W filter flux is attributed to PAH emission (10% hot dust continuum contamination).  
  > "Whitcomb et al. (2023) showed that the Spitzer/IRS spectra of the star-forming regions in 75 nearby galaxies (SINGS sample) may have up to 10% continuum contamination in the F770W filter. Therefore, in a conservative approach, we assumed that 90% of the flux is attributed to PAH (Chastenet et al. 2023)." (3. ANALYSIS) [from Whitcomb et al. 2023; Chastenet et al. 2023]

### Not stated but needed to reproduce (our reading)

- Cell size (arcsec/pixel) and image size (pixels) used in CASA tclean for ALMA 1.3 mm continuum, ALMA CO(2-1) cube, and VLA 22 GHz continuum.
- Exact velocity/frequency range excluded for the CO(2-1) emission line during continuum averaging and uv-plane continuum subtraction, and the velocity range integrated to create the CO(2-1) moment-0 map.
- Whether primary beam correction was applied to the ALMA and VLA maps.
- Whether the ALMA CO(2-1) and JWST/MIRI F770W maps were convolved to match the VLA 1.03 x 0.97 arcsec PSF before regridding onto the 1 arcsec x 1 arcsec grid, or simply rebinned/regridded.
- Exact CASA task/tool used to create the point-source visibility model for VLA AGN subtraction (paper prints 'task os.system', which is a Python module call rather than a CASA modeling task such as cl.addcomponent or ft).
- Exact metallicity / [O/H] value input into Equation 25 of Accurso et al. (2017) to obtain alpha_CO = 4.2.
- Units and definition of SB_PAH in Figure 3 and Table 1 (e.g., whether in MJy/sr, erg s^-1 cm^-2, or W kpc^-2, as the y-axis label is truncated/missing units in Figure 3).

## Analysis recipe

1. **Image ALMA Band 6 continuum and CO(2-1) data cube and generate Moment 0 map**: Average visibilities across 4 spectral windows excluding CO(2-1) line to image 1.3 mm continuum; subtract 1st-order polynomial from CO(2-1) spw visibilities and image cube with tclean; integrate in velocity to produce CO(2-1) moment-0 map blanked below 1 sigma.  
  > "We created a continuum map by averaging the visibilities in the four spectral windows (spws), excluding the spectral range covered by the CO(2-1) emission line. We produced continuum-subtracted datacubes by fitting and subtracting a first-order polynomial from the visibilities of the spw covering CO(2-1)." (2. OBSERVATIONS AND DATA REDUCTION); "Imaging was performed with task tclean using the hogbom algorithm, a threshold of three times the root mean square (rms) noise, a briggs weighting scheme with robust parameter b = 0.5 for the continuum map and a natural weighting scheme for the CO(2-1) data cube in order to increase the map sensitivity." (2. OBSERVATIONS AND DATA REDUCTION); "Right panel: velocity integrated CO(2-1) (moment-0) map. White contours are drawn at (3, 5, 10, 15, 20, 30) σ, σ = 0.56 Jy/beam.km/s. The clean beam (0.508 × 0.374 arcsec, PA=45 deg) is indicated by the gray ellipse. Regions with emission below 1σ are blanked out." (Figure 1 caption)
   - software: CASA, tclean
   - parameter: deconvolver = hogbom, threshold = 3 rms, Briggs robust b = 0.5 (continuum), natural weighting (CO(2-1) cube), channel width = 5 km s^-1  
  > "Imaging was performed with task tclean using the hogbom algorithm, a threshold of three times the root mean square (rms) noise, a briggs weighting scheme with robust parameter b = 0.5 for the continuum map and a natural weighting scheme for the CO(2-1) data cube in order to increase the map sensitivity." (2. OBSERVATIONS AND DATA REDUCTION); "The CO(2-1) data cube has a beam size of 0.508 arcsec × 0.374 arcsec and a rms noise of 0.518 mJy/beam for a channel width of 5 km s^-1." (2. OBSERVATIONS AND DATA REDUCTION)
   - fitting: First-order polynomial fit in uv-plane for continuum subtraction.  
  > "We produced continuum-subtracted datacubes by fitting and subtracting a first-order polynomial from the visibilities of the spw covering CO(2-1)." (2. OBSERVATIONS AND DATA REDUCTION)
   - validation: Measured synthesized beam and rms sensitivity of resulting continuum and CO(2-1) maps.  
  > "The resulting synthesized beam for the continuum map is 0.492 arcsec × 0.360 arcsec (corresponding to 164 pc × 120 pc), with an rms of 0.0121 mJy/beam." (2. OBSERVATIONS AND DATA REDUCTION)
2. **Model and subtract central AGN point source from VLA 22 GHz visibilities and image continuum**: Average 62 spws of calibrated VLA K-band visibilities; model a central point source at the AGN position with flux 5.037 mJy (90% of central beam flux), subtract it from visibilities using uvsub, and clean with tclean.  
  > "We averaged the 62 spw and we produced a clean map using the tclean task and a briggs weighting scheme with robust parameter b = 0.5. We used the hogbom cleaning algorithm with a detection threshold of 3 times the rms sensitivity." (2. OBSERVATIONS AND DATA REDUCTION); "We used the task os.system to model a point source at the AGN position (23:03:15.617 +08:52:26.00 J2000, Izumi et al. 2020) with a flux of 5.037 mJy at 22 GHz, corresponding to 90% of the central beam flux." (3. ANALYSIS); "We used the uvsub task to subtract the point source model from the visibility data, so obtaining the final visibilities." (3. ANALYSIS)
   - software: CASA, tclean, uvsub
   - parameter: AGN position = 23:03:15.617 +08:52:26.00 J2000, point source flux = 5.037 mJy (90% of central beam flux), circumnuclear flux correction = 15%, Briggs robust b = 0.5, hogbom, threshold = 3 rms  
  > "We used the task os.system to model a point source at the AGN position (23:03:15.617 +08:52:26.00 J2000, Izumi et al. 2020) with a flux of 5.037 mJy at 22 GHz, corresponding to 90% of the central beam flux." (3. ANALYSIS); "The final circumnuclear region flux is corrected by 15 % and its value is consistent with the central beam flux after point source subtraction." (3. ANALYSIS)
   - assumption: 90% of the central beam flux at 22 GHz is due to the central AGN point source.  
  > "with a flux of 5.037 mJy at 22 GHz, corresponding to 90% of the central beam flux." (3. ANALYSIS)
   - fitting: _not stated_
   - validation: Tested different point source flux normalizations to verify avoidance of artificial over-subtracted regions.  
  > "We performed several tests with different point source flux normalization, and checked that with the assumed fraction we avoid artificial over-subtracted regions." (3. ANALYSIS)
3. **Model and subtract radial PSF contribution from JWST/MIRI F770W map**: Simulate the JWST/MIRI F770W PSF using WebbPSF (pixel size 0.027 arcsec), model the radial PSF contribution in circular sectors with radius equal to the grid cell size (1 arcsec), and apply radial correction to extracted F770W fluxes and errors.  
  > "circular sectors with a radius equal to the grid cells size, see Section 3, and we derived the radial correction for the F770W filter map" (3. ANALYSIS); "We modeled the radial PSF contribution by using circular sectors with a radius equal to the grid cells size, see Section 3, and we derived the radial correction for the F770W filter map." (3. ANALYSIS); "We corrected both the F770W filter fluxes extracted with the grid and their associated errors for the PSF contribution according to their distance from the center, by following standard error propagation (i.e., convolving the square of the error map with the square of the PSF error)." (3. ANALYSIS)
   - software: WebbPSF
   - parameter: Simulated PSF pixel size = 0.027 arcsec, circular sector radius = 1 arcsec, central 1 arcsec (~330 pc) excluded  
  > "We excluded from the analysis the central 1 arcsec" (3. ANALYSIS); "We excluded from the analysis the central 1 arcsec (∼ 330 pc) region where the PSF contribution is dominant." (3. ANALYSIS)
   - assumption: 90% of the F770W filter flux is attributed to the 7.7 um PAH feature (10% hot dust continuum contamination).  
  > "Therefore, in a conservative approach, we assumed that 90% of the flux is attributed to PAH (Chastenet et al. 2023)." (3. ANALYSIS)
   - fitting: _not stated_
   - validation: Excluded the central 1 arcsec region where PSF contribution and AGN heating dominate.  
  > "We excluded from the analysis the central 1 arcsec (∼ 330 pc) region where the PSF contribution is dominant." (3. ANALYSIS)
4. **Regrid maps to common resolution, extract grid fluxes, and compute physical surface densities (Sigma_H2, Sigma_SFR, SB_PAH)**: Regrid ALMA CO(2-1), VLA 22 GHz, and JWST F770W maps to the VLA spatial resolution; apply a 10 arcsec x 10 arcsec grid of 1 arcsec x 1 arcsec (0.330 kpc) cells centered on the AGN; exclude the central AGN cell and cells with mean flux < 3 rms/pixel; convert extracted fluxes to Sigma_H2 (Eq. 1), Sigma_SFR (via 1.4 GHz extrapolation and Shao et al. 2018), and SB_PAH, plus integrated M(H2), SFR, and depletion time tau_dep = M(H2)/SFR.  
  > "First, we regridded all the maps at the VLA spatial resolution, i.e. the coarser resolution of our data. The grid is centered at the AGN position and has 1 arcsec wide (i.e. 0.330 kpc) squared cells, equal to regridded maps resolution, and a total size of 10 arcsec × 10 arcsec (i.e. 3.3 kpc × 3.3 kpc)." (3. ANALYSIS); "Fluxes are extracted from each cell. If the mean flux in the cell is below 3rms per pixel, we consider it as an upper limit." (3. ANALYSIS); "The grid is centered at the AGN position and has 1 arcsec wide (i.e. 0.330 kpc) squared cells, equal to regridded maps resolution" (3. ANALYSIS)
   - software: astropy
   - parameter: Grid size = 10 arcsec x 10 arcsec (3.3 kpc x 3.3 kpc), cell size = 1 arcsec x 1 arcsec (0.330 kpc), detection threshold = 3 rms per pixel, number of valid data points = 82 (31 at r < r_SB, 51 at r > r_SB)  
  > "The grid is centered at the AGN position and has 1 arcsec wide (i.e. 0.330 kpc) squared cells, equal to regridded maps resolution, and a total size of 10 arcsec × 10 arcsec (i.e. 3.3 kpc × 3.3 kpc)." (3. ANALYSIS); "Fluxes are extracted from each cell. If the mean flux in the cell is below 3rms per pixel, we consider it as an upper limit." (3. ANALYSIS)
   - assumption: D_L = 72.1 Mpc (0.338 kpc/arcsec); inclination i = 45 deg; R_21 = 0.7; alpha_CO = 4.2 (+1.961/-1.341) M_sun (K km s^-1 pc^2)^-1 for log(M_*/M_sun) = 10.5; radio spectral index alpha = -0.85 between 1.4 and 22 GHz; 90% of F770W flux from PAH.  
  > "The adopted luminosity distance of the galaxy is 72.1 Mpc and the corresponding scale is 0.338 kpc/arcsec." (1. INTRODUCTION); "which we assume i =45 deg (Davies et al. 2004)" (3. ANALYSIS); "First, we derived the radio luminosity at 1.4 GHz by assuming an average radio spectrum steepness α = −0.85 for the entire galaxy." (3. ANALYSIS)
   - fitting: Radio SED fitted using integrated radio fluxes from NED to obtain spectral index alpha = -0.85.  
  > "by fitting the radio Spectral Energy Distribution (SED) using the integrated radio fluxes reported by NED" (3. ANALYSIS)
   - validation: Compared global SFR and M(H2) with literature values from Song et al. (2021), Lai et al. (2022), Davies et al. (2004), Izumi et al. (2020), Nguyen et al. (2021), and Zhang & Ho (2023); checked impact of spectral index variations (-0.7 to -0.9, up to 10% on SFR).  
  > "Song et al. (2021) derived the spectral index measured from 15 to 33 GHz, finding values in between ∼-0.7 and ∼-0.9 in the NGC 7469 nuclear ring. These variations translate into corrections to the SFR up to 10% which will be taken into account further in the discussion." (3. ANALYSIS); "Our SFR estimate is consistent with the SFR = 21 ± 2.1 M_⊙ yr^-1 by Song et al. (2021) from the 3-to-33 GHz radio continuum, and with the range of SFR = 10-30 M_⊙ yr^-1 reported by Lai et al. (2022)" (4.1. Morphology of the SB ring)
5. **Quantify correlations and fit linear scaling relations between SB_PAH, Sigma_SFR, and Sigma_H2**: Compute Pearson rho and Kendall tau rank correlation coefficients; fit linear relations y = n x + k in log-log space using MCMC (emcee) for the full sample (r > 0), inner SB ring (r < r_SB = 900 pc), and outer region (r > r_SB) for SB_PAH vs Sigma_SFR, SB_PAH vs Sigma_H2, and the Kennicutt-Schmidt law (log Sigma_SFR vs log Sigma_H2).  
  > "We derived the Pearson ρ and the Kendall τ rank correlation coefficients (Table 1), finding a higher correlation of SB_PAH with Σ_SFR than with Σ_H2, both for the SB ring and for external regions." (4.2. PAH emission); "We fit a linear relation y = nx + k to each subsample using Python package emcee (Foreman-Mackey et al. 2013), and assuming a constant error on Σ_H2 and Σ_SFR, equal to the rms noise of each regridded map." (4.2. PAH emission); "We adopted the same fitting method as described above, taking into account the uncertainties both on Σ_SFR and on Σ_H2, and the best fit linear relation for all data points is logΣ_SFR = (1.02 ± 0.07)logΣ_H2 + (−2.85 ± 0.02) (green solid line in Figure 4)." (4.3. The star formation law)
   - software: emcee
   - parameter: r_SB = 900 pc; N = 82 total points (31 for r < r_SB, 51 for r > r_SB)  
  > "To quantify this steepening, we divided the data into two subsamples: an inner region within the SB ring (r < r_SB) and an outer region with r > r_SB, where r_SB = 900 pc." (4.2. PAH emission); "NGC 7469 is known to host a prominent starburst (SB) ring with an outer radius of 900 pc" (1. INTRODUCTION)
   - assumption: Constant error on Sigma_H2 and Sigma_SFR equal to the rms noise of each regridded map; error on SB_PAH obtained by convolving rms noise of regridded MIRI map with PSF uncertainty.  
  > "equal to the rms noise of each regridded map. The uncertainty associated to SB PAH is obtained by convolving the rms noise of the regridded MIRI map with the uncertainty" (4.2. PAH emission)
   - fitting: MCMC linear fit y = n x + k using Python emcee library, accounting for uncertainties in both coordinates.  
  > "We fit a linear relation y = nx + k to each subsample using Python package emcee (Foreman-Mackey et al. 2013)" (4.2. PAH emission); "We adopted the same fitting method as described above, taking into account the uncertainties both on Σ_SFR and on Σ_H2" (4.3. The star formation law)
   - validation: Tested effect of excitation- and metallicity-dependent alpha_CO prescription of Narayanan et al. (2012) on the slope change between SB ring and outer disk.  
  > "Considering a CO-to-H2 conversion factor accounting for both solar-like metallicity and gas excitation, as prescribed by Narayanan et al. (2012), we found that the change in slope between SB ring and outer disk remains appreciable." (4.2. PAH emission)

## Software

- **CASA** 5.1.1-5: Imaging ALMA Band 6 continuum and CO(2-1) data cube, continuum subtraction, modeling and subtracting central AGN point source in VLA K-band visibilities (uvsub), and imaging VLA 22 GHz continuum (tclean).  
  > "Imaging was performed with the Common Astronomy Software Applications (CASA; McMullin et al. 2007), version 5.1.1-5." (2. OBSERVATIONS AND DATA REDUCTION); "Imaging was performed with the Common Astronomy Software Applications (CASA; McMullin et al. 2007), version 5.1.1-5." (2. OBSERVATIONS AND DATA REDUCTION); "Within CASA, we modeled and subtracted the central point source emission in the VLA map to remove its contribution from the circumnuclear region." (3. ANALYSIS)
- **tclean** : Deconvolving and imaging ALMA 1.3 mm continuum, ALMA CO(2-1) cube, and VLA 22 GHz continuum.  
  > "Imaging was performed with task tclean using the hogbom algorithm, a threshold of three times the root mean square (rms) noise" (2. OBSERVATIONS AND DATA REDUCTION); "We averaged the 62 spw and we produced a clean map using the tclean task and a briggs weighting scheme with robust parameter b = 0.5." (2. OBSERVATIONS AND DATA REDUCTION)
- **uvsub** : Subtracting the central AGN point source model from VLA 22 GHz visibility data.  
  > "We used the uvsub task to subtract the point source model from the visibility data, so obtaining the final visibilities." (3. ANALYSIS)
- **WebbPSF** 1.2.1: Simulating the point-spread function (PSF) of the JWST/MIRI F770W filter image.  
  > "to simulate the point-spread function (PSF) of the JWST/MIRI F770W filter image" (3. ANALYSIS)
- **emcee** : MCMC linear fitting of scaling relations between SB_PAH, Sigma_SFR, and Sigma_H2.  
  > "The dashed green lines are the linear fit to the data logΣ_SFR = (1.02 ± 0.07)logΣ_H2 + (−2.85 ± 0.02), derived by using the python emcee library (Foreman-Mackey et al. 2013)." (Figure 4 caption); "We fit a linear relation y = nx + k to each subsample using Python package emcee (Foreman-Mackey et al. 2013)" (4.2. PAH emission)
- **astropy** : General astronomical data analysis (listed in Software section).  
  > "Software: astropy (Astropy Collaboration et al. 2013, 2018), emcee (Foreman-Mackey et al. 2013), CASA (McMullin et al. 2007), WebbPSF (Perrin et al. 2014)" (5. ACKNOWLEDGMENTS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum map rms sensitivity | 0.0121 | not stated | mJy/beam | 1 | The resulting synthesized beam for the continuum map is 0.492 arcsec × 0.360 arcsec (corresponding to 164 pc × 120 pc), with an rms of 0.0121 mJy/beam. |
| CO(2-1) cube rms noise (per 5 km s^-1 channel) | 0.518 | not stated | mJy/beam | 1 | The CO(2-1) data cube has a beam size of 0.508 arcsec × 0.374 arcsec and a rms noise of 0.518 mJy/beam for a channel width of 5 km s^-1. |
| CO(2-1) mass surface density sensitivity (per 5 km s^-1 channel) | 7.8 | not stated | M_sun/beam | 1 | This translates into a mass surface density sensitivity of 7.8 M_⊙/beam for a channel width of 5 km s^-1, computed using equation 1. |
| CO(2-1) moment-0 map rms noise | 0.56 | not stated | Jy/beam.km/s | 1 | Right panel: velocity integrated CO(2-1) (moment-0) map. White contours are drawn at (3, 5, 10, 15, 20, 30) σ, σ = 0.56 Jy/beam.km/s. |
| VLA 22 GHz continuum map rms noise | 23.2 | not stated | uJy/beam | 2 | The final continuum map has an rms of 23.2 µJy/beam and a clean beam of 1.029 arcsec × 0.967 arcsec (i.e. 342 pc × 322 pc). |
| Modeled AGN point source flux at 22 GHz | 5.037 | not stated | mJy | 2 | We used the task os.system to model a point source at the AGN position (23:03:15.617 +08:52:26.00 J2000, Izumi et al. 2020) with a flux of 5.037 mJy at 22 GHz, corresponding to 90% of the central beam flux. |
| Average galaxy radio spectral index (alpha) | -0.85 | not stated | dimensionless | 4 | First, we derived the radio luminosity at 1.4 GHz by assuming an average radio spectrum steepness α = −0.85 for the entire galaxy. |
| Global SFR (central 3.3 kpc x 3.3 kpc, excluding central cell) | 11.5 | ± 0.3 | M_sun yr^-1 | 4 | We estimate a global star formation rate SFR ∼ 11.5 M_⊙ yr^-1 from the radio at 22 GHz; We estimate the global SFR integrated over the central 3.3 kpc × 3.3 kpc into SFR = 11.5 ± 0.3 M_⊙ yr^-1, following the prescription of Shao et al. (2018), see Section 3. |
| Cold molecular gas mass M(H2) (central 3.3 kpc x 3.3 kpc) | 6.4e9 | ± 2.0e9 | M_sun | 4 | and a cold molecular gas mass M(H2) ∼ 6.4 × 10^9 M_⊙ from the CO(2-1) emission.; We computed the molecular gas mass over the central 3.3 kpc × 3.3 kpc M(H2) = (6.4 ± 2.0) × 10^9 M_⊙, where the error is dominated by the uncertainty on α_CO (0.165 dex, Accurso et al. 2017). |
| Cold molecular gas mass in the starburst ring M(H2)_SB | 3.3e9 | ± 1.0e9 | M_sun | 4 | We computed that ∼ 50% of the total cold molecular gas mass is contained in the SB ring, M(H2)_SB = (3.3 ± 1.0) × 10^9 M_⊙. |
| Gas depletion timescale tau_dep (central 3.3 kpc x 3.3 kpc) | 0.56 | ± 0.18 | Gyr | 4 | We obtained τ_dep = (0.56 ± 0.18) Gyr for the central 3.3 kpc × 3.3 kpc region, and a shorter τ_dep = (0.47 ± 0.15) Gyr for the SB ring. |
| Gas depletion timescale tau_dep (starburst ring) | 0.47 | ± 0.15 | Gyr | 4 | We obtained τ_dep = (0.56 ± 0.18) Gyr for the central 3.3 kpc × 3.3 kpc region, and a shorter τ_dep = (0.47 ± 0.15) Gyr for the SB ring. |
| Mean gas depletion timescale across grid cells (tau_dep,mean) | 0.66 | ± 0.02 | Gyr | 4 | In Figure 4, we report the characteristic gas depletion timescales: NGC 7469 data points show an average τ_dep,mean = (0.66 ± 0.02) Gyr, where the uncertainty is the standard error of the mean. |
| Sigma_SFR - SB_PAH correlation slope n (all points, r > 0) | 1.77 | ± 0.08 | dimensionless | 5 | r > 0 82 0.91 0.75 1.77 ± 0.08 -2.56 ± 0.03 |
| Sigma_SFR - SB_PAH correlation zero-point k (all points, r > 0) | -2.56 | ± 0.03 | dimensionless | 5 | r > 0 82 0.91 0.75 1.77 ± 0.08 -2.56 ± 0.03 |
| Sigma_SFR - SB_PAH correlation slope n (SB ring, r < r_SB) | 2.16 | ± 0.20 | dimensionless | 5 | r < r_SB 31 0.76 0.56 2.16 ± 0.20 -2.78 ± 0.02; In particular, the slope at the SB ring is n = (2.16 ± 0.20) whereas at r > r_SB is n = (0.83 ± 0.10). |
| Sigma_SFR - SB_PAH correlation zero-point k (SB ring, r < r_SB) | -2.78 | ± 0.02 | dimensionless | 5 | r < r_SB 31 0.76 0.56 2.16 ± 0.20 -2.78 ± 0.02 |
| Sigma_SFR - SB_PAH correlation slope n (outer region, r > r_SB) | 0.83 | ± 0.10 | dimensionless | 5 | r > r_SB 51 0.77 0.56 0.83 ± 0.10 -2.36 ± 0.03; In particular, the slope at the SB ring is n = (2.16 ± 0.20) whereas at r > r_SB is n = (0.83 ± 0.10). |
| Sigma_SFR - SB_PAH correlation zero-point k (outer region, r > r_SB) | -2.36 | ± 0.03 | dimensionless | 5 | r > r_SB 51 0.77 0.56 0.83 ± 0.10 -2.36 ± 0.03 |
| Sigma_H2 - SB_PAH correlation slope n (all points, r > 0) | 2.17 | ± 0.11 | dimensionless | 5 | 0.84 0.68 2.17 ± 0.11 -15.48 ± 0.36 |
| Sigma_H2 - SB_PAH correlation zero-point k (all points, r > 0) | -15.48 | ± 0.36 | dimensionless | 5 | 0.84 0.68 2.17 ± 0.11 -15.48 ± 0.36 |
| Sigma_H2 - SB_PAH correlation slope n (SB ring, r < r_SB) | 2.61 | ± 0.25 | dimensionless | 5 | 0.71 0.52 2.61 ± 0.25 -10.25 ± 0.03 |
| Sigma_H2 - SB_PAH correlation zero-point k (SB ring, r < r_SB) | -10.25 | ± 0.03 | dimensionless | 5 | 0.71 0.52 2.61 ± 0.25 -10.25 ± 0.03 |
| Sigma_H2 - SB_PAH correlation slope n (outer region, r > r_SB) | 0.72 | ± 0.09 | dimensionless | 5 | 0.66 0.47 0.72 ± 0.09 -4.39 ± 0.03 |
| Sigma_H2 - SB_PAH correlation zero-point k (outer region, r > r_SB) | -4.39 | ± 0.03 | dimensionless | 5 | 0.66 0.47 0.72 ± 0.09 -4.39 ± 0.03 |
| Kennicutt-Schmidt law slope n (log Sigma_SFR vs log Sigma_H2, all points) | 1.02 | ± 0.07 | dimensionless | 5 | The dashed green lines are the linear fit to the data logΣ_SFR = (1.02 ± 0.07)logΣ_H2 + (−2.85 ± 0.02), derived by using the python emcee library (Foreman-Mackey et al. 2013).; the best fit linear relation for all data points is logΣ_SFR = (1.02 ± 0.07)logΣ_H2 + (−2.85 ± 0.02) (green solid line in Figure 4). |
| Kennicutt-Schmidt law zero-point k (log Sigma_SFR vs log Sigma_H2, all points) | -2.85 | ± 0.02 | dimensionless | 5 | The dashed green lines are the linear fit to the data logΣ_SFR = (1.02 ± 0.07)logΣ_H2 + (−2.85 ± 0.02), derived by using the python emcee library (Foreman-Mackey et al. 2013). |
| Kennicutt-Schmidt law slope n (outer region, r > r_SB) | 0.5 | ± 0.1 | dimensionless | 5 | The slope of this relation is consistent with that obtained by fitting the SB ring alone, while we find a flatter slope for the fit of the outer region (n = 0.5 ± 0.1). |

## Qualitative findings

- The ALMA 1.3 mm dust continuum morphology closely matches the VLA 22 GHz radio continuum and JWST/MIRI 7.7 um PAH emission across the starburst ring, with clumps B, C, and D detected with similar morphology and size in all tracers.  
  > "We find that the 1.3 mm map shows a morphology remarkably similar to those traced by the 22 GHz and the 7.7 µm polycyclic aromatic hydrocarbon (PAH) emission observed with JWST. The three tracers reproduce the morphology of the starburst ring with good agreement." (abstract); "In particular, clumps B, C, and D are detected with similar morphology and size in the dust continuum, CO(2-1), 22 GHz, and the PAH emission." (4.1. Morphology of the SB ring)
- A fifth 1.3 mm continuum clump E (23:03:15.60 +08:52:24.56 J2000) is detected at ~18 sigma with a CO(2-1) counterpart, no mid-IR counterpart, and a 15 sigma 22 GHz radio peak offset by ~0.5 arcsec to the northeast.  
  > "In addition, we identify clump E (23:03:15.60 +08:52:24.56, J2000) where we detect 1.3 mm emission with a statistical significance of ∼ 18σ." (4.1. Morphology of the SB ring); "the dusty clump E exhibits no evident counterpart in the radio or mid-IR maps" (4.1. Morphology of the SB ring)
- The inner bar structure connecting the SB ring to the CND is detected at 12 sigma in CO(2-1), but is undetected down to 3 sigma in both 22 GHz radio continuum and 7.7 um PAH emission.  
  > "Although the bar structure is detected at a significance level of 12σ in the CO(2-1) map, it remains undetected down to 3σ in the radio continuum and in the 7.7 µm maps, despite the high angular resolution of JWST/MIRI." (4.1. Morphology of the SB ring)
- Approximately 60% of the star formation and ~50% of the cold molecular gas mass within the central 3.3 kpc x 3.3 kpc occur in the starburst ring.  
  > "We found that the majority, approximately 60%, of the SF occurs in the SB ring, consistent with Song et al. (2021)." (4.1. Morphology of the SB ring); "We computed that ∼ 50% of the total cold molecular gas mass is contained in the SB ring, M(H2)_SB = (3.3 ± 1.0) × 10^9 M_⊙." (4.1. Morphology of the SB ring)

## Claim tuples

- H: Does the 1.3 mm dust continuum trace the same starburst ring morphology as the 22 GHz radio continuum and 7.7 um PAH emission in NGC 7469? | E: Compare high-resolution ALMA 1.3 mm continuum and CO(2-1) maps with VLA 22 GHz continuum and JWST/MIRI F770W 7.7 um images across the central 3.3 kpc. | R: Clumps B, C, and D in the SB ring are detected with remarkably similar morphology and size in 1.3 mm, CO(2-1), 22 GHz, and 7.7 um emission; clump E is detected at 18 sigma in 1.3 mm and CO(2-1) with a 0.5 arcsec offset 15 sigma radio peak, while the inner bar is detected at 12 sigma in CO(2-1) but < 3 sigma in radio and 7.7 um. | F: The 1.3 mm, 22 GHz, and 7.7 um PAH tracers reproduce the morphology of the starburst ring in good agreement, indicating that 1.3 mm emission mainly traces thermal dust heated by young stars in the SB ring. | **supported**
- H: How does 7.7 um PAH surface brightness correlate with star formation rate surface density (Sigma_SFR) and cold molecular gas surface density (Sigma_H2), and does the correlation vary between the starburst ring and the outer disk? | E: Extract fluxes in 82 1-arcsec (330 pc) grid cells across the central 3.3 kpc x 3.3 kpc, compute Pearson rho and Kendall tau correlation coefficients, and fit linear log-log relations using emcee for the inner SB ring (r < 900 pc) and outer region (r > 900 pc). | R: SB_PAH correlates more strongly with Sigma_SFR (rho = 0.91, tau = 0.75) than with Sigma_H2 (rho = 0.84, tau = 0.68), and the slopes are significantly steeper inside the SB ring (n = 2.16 +- 0.20 for Sigma_SFR; n = 2.61 +- 0.25 for Sigma_H2) than in the outer region (n = 0.83 +- 0.10 for Sigma_SFR; n = 0.72 +- 0.09 for Sigma_H2). | F: PAH emission correlates more tightly with SFR than with CO likely due to the ionizing radiation field of young stars, and the steepening in the SB ring reflects enhanced recent star formation activity (though radial variations in alpha_CO, PAH properties, and radio spectral index may also contribute). | **supported**
- H: Where does the spatially resolved Kennicutt-Schmidt star formation law of NGC 7469 lie relative to local AGN host galaxies and dusty starbursts (U/LIRGs)? | E: Fit the spatially resolved log Sigma_SFR vs log Sigma_H2 relation on 330 pc scales across NGC 7469 using emcee and compare with the NUGA local AGN relation (Casasola et al. 2015) and the U/LIRG starburst relation (Kennicutt & De Los Reyes 2021). | R: The best-fit K-S relation is log Sigma_SFR = (1.02 +- 0.07) log Sigma_H2 + (-2.85 +- 0.02) with a mean depletion time of 0.66 +- 0.02 Gyr, offset by ~0.6 dex above local NUGA AGNs and ~0.6 dex below U/LIRGs. | F: NGC 7469 exhibits an intermediate star formation regime between local AGN host galaxies and U/LIRGs. | **supported**

## Reasoning

- Why this data: Combining interferometric mm (ALMA CO(2-1) and 1.3 mm continuum), cm (VLA 22 GHz), and JWST/MIRI F770W data resolves hundred-parsec scales (88 to 330 pc) to trace cold molecular gas, dust extinction-free SFR, and 7.7 um PAH emission across the starburst ring and outer disk.  
  > "Taking advantage of interferometric mm and cm, and JWST data of nearby galaxies, it is possible to perform spatially resolved studies of the SF process in galaxies, down to hundred-parsec scales and to investigate the correlations between the PAHs, the SFR surface density (Σ_SFR) and the mass surface density of molecular gas (Σ_H2), which is the direct fuel of the formation of stars." (1. INTRODUCTION); "In this paper we focus the analysis on the SUB128 subarray data, where the nucleus remained unsaturated, taken on 2022 July 2 with an exposure time of 48 s." (2. OBSERVATIONS AND DATA REDUCTION)
- Why this method: Natural weighting was used for the CO(2-1) cube to increase map sensitivity; maps were regridded to the coarsest (VLA 1 arcsec) resolution for uniform grid comparison; the central 1 arcsec cell was excluded and radial PSF / point-source subtraction applied because of strong AGN torus/PSF and core-jet contamination.  
  > "and a natural weighting scheme for the CO(2-1) data cube in order to increase the map sensitivity." (2. OBSERVATIONS AND DATA REDUCTION); "First, we regridded all the maps at the VLA spatial resolution, i.e. the coarser resolution of our data." (3. ANALYSIS); "The central cell (i.e. the one that contains the AGN) is not used, since it is not possible to determine and disentangle the AGN contribution to the measured flux with good accuracy." (3. ANALYSIS)
- Alternative: JWST/MIRI BRIGHTSKY subarray mode was available in program 1328, but analysis focused on the SUB128 subarray data where the nucleus remained unsaturated.  
  > "JWST/MIRI (Bouchet et al. 2015; Rieke et al. 2015) imaging of NGC 7469 was obtained with the F770W (7.7 µm) filter with both the BRIGHTSKY and SUB128 subarray modes (program ID 1328, PI Armus Lee). In this paper we focus the analysis on the SUB128 subarray data, where the nucleus remained unsaturated" (2. OBSERVATIONS AND DATA REDUCTION)
- Alternative: Excitation- and metallicity-dependent CO-to-H2 conversion factor prescription of Narayanan et al. (2012) was tested as an alternative to the constant Accurso et al. (2017) alpha_CO, finding that the slope change between the SB ring and outer disk remains appreciable.  
  > "Considering a CO-to-H2 conversion factor accounting for both solar-like metallicity and gas excitation, as prescribed by Narayanan et al. (2012), we found that the change in slope between SB ring and outer disk remains appreciable." (4.2. PAH emission)
- Alternative: Separate K-S linear fit to the outer region (r > r_SB) yielding slope n = 0.5 +- 0.1 was rejected in favor of the global fit because the outer fit is dominated by low-SNR data points.  
  > "The slope of this relation is consistent with that obtained by fitting the SB ring alone, while we find a flatter slope for the fit of the outer region (n = 0.5 ± 0.1). As the latter fit is dominated by data points with low SNR, we consider the global logΣ_SFR − logΣ_H2 relation as best-fit for NGC 7469." (4.3. The star formation law)
- How they decided it was enough: _not stated_
- Limitation (authors): Current theoretical models for the JWST PSF lack a robust method for removing PSF spikes, requiring a conservative radial sector subtraction and exclusion of the central 1 arcsec (~330 pc) region.  
  > "Due to the limitations in the current theoretical model for the JWST PSF, we do not have a robust method for removing the PSF spikes (see Williams et al. 2024, and references therein). Therefore we applied this conservative method to subtract and model the PSF contribution. We excluded from the analysis the central 1 arcsec (∼ 330 pc) region where the PSF contribution is dominant." (3. ANALYSIS)
- Limitation (authors): The central 1 arcsec x 1 arcsec cell containing the AGN and CND is excluded because AGN dust-reprocessed torus emission in MIRI and core-jet radio emission in VLA cannot be disentangled with good accuracy.  
  > "The central cell (i.e. the one that contains the AGN) is not used, since it is not possible to determine and disentangle the AGN contribution to the measured flux with good accuracy." (3. ANALYSIS)
- Limitation (authors): Local variations in the radio spectral index (between -0.7 and -0.9 in the nuclear ring, or radial steepening) cannot be excluded and can affect derived SFR values by up to 10% and contribute to the slope change in log SB_PAH vs log Sigma_SFR.  
  > "However, we cannot exclude local variations in the steepness of the radio spectrum that can affect the final SFR values. Song et al. (2021) derived the spectral index measured from 15 to 33 GHz, finding values in between ∼-0.7 and ∼-0.9 in the NGC 7469 nuclear ring. These variations translate into corrections to the SFR up to 10%" (3. ANALYSIS); "We therefore cannot exclude that the superposition of these effects could cause the observed slope change in the logSB_PAH − logΣ_SFR relation." (4.2. PAH emission)
- Limitation (authors): Local variations in gas properties (metallicity, turbulence, excitation) and PAH properties (grain size distribution, ionization fraction, temperature) can affect alpha_CO and PAH luminosity, and probing PAH grain properties requires ratios of multiple MIR PAH features rather than F770W alone.  
  > "Still local variations in gas properties, including composition, turbulence, and metallicity, significantly influence the CO-to-H2 conversion factor" (4.2. PAH emission); "Additionally, several factors, including grain size distribution, temperature, ionization field, metallicity, and dust amount can affect PAH luminosity (e.g. Chastenet et al. 2023; Whitcomb et al. 2024)." (4.2. PAH emission); "However, investigating PAH properties such as grain size distribution and ionization fraction involves examining the ratios between various MIR PAH features (Lai et al. 2023; Bohn et al. 2023)." (4.2. PAH emission)
- Caveat (inferred, ours): Adopting a single galactic-scale alpha_CO = 4.2 M_sun (K km s^-1 pc^2)^-1 and a fixed R_21 = 0.7 across both the intense starburst ring and the outer disk may systematically overestimate M(H2) in the starburst ring where ULIRG-like alpha_CO (~0.8-1.5) and higher CO excitation often apply.
- Caveat (inferred, ours): Extrapolating from 22 GHz to 1.4 GHz using a single spectral index alpha = -0.85 neglects the rising thermal free-free fraction at 22 GHz in young starburst clumps.
- Caveat (inferred, ours): It is not explicitly stated whether the ALMA (0.5 arcsec) and JWST/MIRI (0.25 arcsec) images were convolved to the VLA PSF (1.03 x 0.97 arcsec) prior to regridding onto 1 arcsec pixels.
- Caveat (inferred, ours): The y-axis label of Figure 3 ('log SB_PAH') omits physical units, making the zero-points k in Table 1 ambiguous without knowing the exact unit convention adopted for SB_PAH.

## Reproducibility

- Data public (paper): Public archival data from ALMA (2017.1.00078.S), VLA data archive (20A-158), and JWST MAST archive (program 1328, DOI: 10.17909/3x02-0q74).  
  > "We used the standard calibrated visibilites provided by the VLA data archive l" (2. OBSERVATIONS AND DATA REDUCTION); "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (5. ACKNOWLEDGMENTS); "The JWST data used in this paper can be found in MAST: 10.17909/3x02-0q74. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00078.S" (5. ACKNOWLEDGMENTS)
- Products in archive: Calibrated JWST/MIRI images from MAST and standard calibrated visibilities from the VLA archive and NRAO ALMA pipeline.  
  > "Visibilities were calibrated by the NRAO Observatory, using the standard pipeline and default calibrators." (2. OBSERVATIONS AND DATA REDUCTION); "We used the standard calibrated visibilites provided by the VLA data archive l" (2. OBSERVATIONS AND DATA REDUCTION); "Visibilities were calibrated by the NRAO Observatory, using the standard pipeline and default calibrators." (2. OBSERVATIONS AND DATA REDUCTION)
- Missing: Exact frequency/velocity channel ranges for ALMA continuum averaging, uv-plane continuum subtraction, and CO(2-1) moment-0 velocity integration.
- Missing: Image pixel sizes and dimensions in CASA tclean for ALMA and VLA imaging.
- Missing: Exact implementation of the radial WebbPSF sector subtraction on the JWST/MIRI F770W map.
- Missing: Exact physical units of SB_PAH used in the linear regressions in Table 1 and Figure 3.
- Missing: Details of whether PSF matching (convolution to VLA beam) was performed prior to regridding onto the 1 arcsec x 1 arcsec grid.
- Data volume (inferred): Moderate (~50-200 GB total: ~1.5 h ALMA Band 6 12m data is ~10-30 GB, 58.9 h VLA K-band continuum visibilities is ~30-150 GB, and JWST/MIRI SUB128 calibrated products are <100 MB).
- Score (inferred): 72/5, All three datasets (ALMA, VLA, JWST) are publicly available in archives with explicit project codes/DOIs, software versions (CASA 5.1.1-5, WebbPSF 1.2.1) and main tclean parameters (hogbom, robust=0.5/natural, 3rms threshold) as well as physical conversion formulas and assumptions are clearly stated; however, minor imaging parameters (pixel/image sizes, velocity integration windows), PSF-matching details prior to regridding, and the exact units of SB_PAH in Table 1/Figure 3 are omitted.
- Rediscovery candidate: yes, All raw/calibrated data are public in the ALMA, VLA, and MAST archives, the data reduction and 1-arcsec grid analysis recipe are straightforward, and the paper reports clear numeric benchmarks (rms noises, global SFR and M(H2), depletion timescales, and MCMC correlation slopes).

## Links

- Method: Solomon & Vanden Bout 2005 (Conversion factor F_21 from CO flux density to line luminosity L'.)
- Method: Accurso et al. 2017 (Equation 25 used to derive the metallicity/mass-dependent CO-to-H2 conversion factor alpha_CO.)
- Method: Shao et al. 2018 (Section 3.2 correlation used to convert 1.4 GHz radio luminosity to SFR.)
- Method: Whitcomb et al. 2023; Chastenet et al. 2023 (Justification for attributing 90% of the JWST/MIRI F770W filter flux to the 7.7 um PAH feature.)
- Method: Perrin et al. 2014 (WebbPSF tool used to simulate the JWST/MIRI F770W PSF.)
- Companion: Zanchettin et al. 2023 (Prior paper by the same lead author applying a similar spatially resolved star formation law methodology to NGC 2992, directly compared in Figure 4.)
- Related: NUGA (NUclei of GAlaxies)
- Related: DustPedia
- Related: SINGS

## Checks

```json
{
 "quotes": 187,
 "quotes_ok": 187,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 21,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 28,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 79,
  "rate": 0.798
 },
 "evidence_ok": true
}
```
