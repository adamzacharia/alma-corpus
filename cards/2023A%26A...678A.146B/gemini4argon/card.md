# Tracing snowlines and C/O ratio in a planet-hosting disk. ALMA molecular line observations towards the HD 169142 disk

`2023A&A...678A.146B` | Astronomy and Astrophysics 2023 | first author: Booth, Alice S. | arXiv: 2308.07910 | DOI: 10.1051/0004-6361/202346974

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry, exoplanets
- Question: What are the elemental make-up (specifically the C/O ratio) of the gas and the locations of the CO and H2O snowlines in the planet-hosting HD 169142 disk in relation to its forming planets?  
  > "In this paper, we present Atacama Large Millimeter/submillimeter Array (ALMA) observations of the HD 169142 disk where we detect 13 different species. Using these data, we infer the elemental make-up of the gas and location of both the CO and snowlines in relation to these forming planets." (Introduction)
- Target **HD 169142**: coordinates _not stated_; z/distance 114.0 pc  
  > "HD 169142 is a nearby (114.0 pc) F1 star hosting an almost face on (inclination of 13$^{\circ}$, position angle of 5$^{\circ}$) protoplanetary disk (cite: 2006AJ....131.2290R; 2017A&A...600A..72F; 2018A&A...616A...1G; 2018A&A...620A.128V)." (Introduction); distance from (cite: 2006AJ....131.2290R; 2017A&A...600A..72F; 2018A&A...616A...1G; 2018A&A...620A.128V)  
  > "HD 169142 is a nearby (114.0 pc) F1 star hosting an almost face on (inclination of 13$^{\circ}$, position angle of 5$^{\circ}$) protoplanetary disk (cite: 2006AJ....131.2290R; 2017A&A...600A..72F; 2018A&A...616A...1G; 2018A&A...620A.128V)." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00799.S, 2015.1.00806.S, 2016.1.00344.S, 2016.1.00346.S, 2018.1.01237.S
- bands: Bands 6, 7 and 8  
  > "We have compiled ALMA observations towards the HD 169142 disk over Bands 6, 7 and 8." (Observations)
- frequencies and spectral setup: 2016.1.00344.S: 5 spws (3 for CO J=2-1 lines, continuum windows at 218.004 GHz and 232.004 GHz); 2016.1.00346.S: 4 spws at 478.651, 480.568, 489.785, 492.195 GHz (~0.15 km/s resolution); 2018.1.01237: 4 spws at 279.515 GHz (~0.15 km/s), 277.990 GHz (~1.2 km/s), 288.147 GHz (~0.29 km/s), 289.990 GHz (~17 km/s)  
  > "These observations consist of 5 spectral windows with 3 dedicated to the CO lines (, , $J=2-1$) and two continuum windows centred at 218.004 GHz and 232.004 GHz." (Observations); "The dataset contains four spectral windows, which are centred at 478.651 GHz, 480.568 GHz, 489.785 GHz and 492.195 GHz with the latter two the line spectral windows at $\sim0.15$ km s$^{-1}$ spectral resolution." (Observations); "Four spectral windows were used, centred at 279.515 GHz (resolution of $\sim0.15$ km s$^{-1}$), 277.990 GHz ($\sim1.2$ km s$^{-1}$), 288.147 GHz ($\sim0.29$ km s$^{-1}$) and 289.990 GHz ($\sim17$ km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–1574 m, 35–1574 m (2012.1.00799.S); 19–7716 m (2015.1.00806.S); 19-3144 m, 21-2647 m (2016.1.00344.S); 15-279 m (2016.1.00346.S); 15-500 m (2018.1.01237.S)  
  > "| 2012.1.00799.S | Honda, M. | 7 | 2015-07-26 | 41 | 15–1574 | 41.4 | 1.3 |" (ALMA Observations); "| 2015.1.00806.S | Pineda, J. | 7 | 2015-12-06 | 32 | 19–7716 | 25.3 | 0.4 |" (ALMA Observations); "| 2018.1.01237.S | Macías, E. | 7 | 2019-04-10 | 43 | 15-500 | 81.0 | 5.7 |" (ALMA Observations)
- angular resolution: ~0.03" to ~1.0" across projects (synthesized beams from 0.19"x0.14" to 1.07"x0.51")  
  > "Project 2015.1.00806.S (PI: Pineda, J.) are Band 7 observations at $\approx$0.03" and in these data, we detect $J=6-5$." (Observations); "Project 2016.1.00346.S (PI: Tsukagoshi, T.) are Band 8 observations at $\approx$1.0" and we detect $J=10-9$ and [CI] $^{3}P_1-^{3}P_0$." (Observations); "| | $^{3}P_1-^3P_0$ | 492.160651 | 24 | 7.994$\times10^{-4}$ | 3 | 2.0 | 1.07"$\times$0.51" (81) | 0.15 | 71.9 | (7.4$\pm$0.7)$\times10^{3}$ |" (Table 1)
- max recoverable scale: 0.4" to 8.5" across executions  
  > "| 2015.1.00806.S | Pineda, J. | 7 | 2015-12-06 | 32 | 19–7716 | 25.3 | 0.4 |" (ALMA Observations); "| 2016.1.00344.S | Pérez, S. | 6 | 2016-10-04 | 40 | 19-3144 | 33.3 | 8.5 |" (ALMA Observations)
- sensitivity: 0.23 to 130.7 mJy beam^-1 per channel (depending on line and channel width)  
  > "| | $J=10-9$ | 489.750921 | 129 | 2.489$\times10^{-3}$ | 21 | 0.5 | 0.94"x0.40" (83) | 0.15 | 130.7 | (4.3$\pm$0.4)$\times10^{3}$ |" (Table 1); "| | $J=6-5$ | 289.209066 | 38 | 4.812$\times10^{-4}$ | 13 | 0.5 | 0.73"$\times$0.46" (89) | 16.2 | 0.23 | 261.0$\pm$30 |" (Table 1)
- time on source: 2.92 to 81.0 min per execution (41.4, 21.2, 41.4, 25.3, 33.3, 33.2, 2.92, 81.0 min)  
  > "| 2016.1.00346.S | Tsukagoshi, T. | 8 | 2017-04-05 | 40 | 15-279 | 2.92 | 5.9 |" (ALMA Observations); "| 2018.1.01237.S | Macías, E. | 7 | 2019-04-10 | 43 | 15-500 | 81.0 | 5.7 |" (ALMA Observations)
- observing dates: 2015-07-26, 2015-07-27, 2015-08-08, 2015-12-06, 2016-10-04, 2017-07-05, 2017-04-05, 2019-04-10  
  > "| 2012.1.00799.S | Honda, M. | 7 | 2015-07-26 | 41 | 15–1574 | 41.4 | 1.3 |" (ALMA Observations); "| 2016.1.00344.S | Pérez, S. | 6 | 2016-10-04 | 40 | 19-3144 | 33.3 | 8.5 |" (ALMA Observations); "| 2018.1.01237.S | Macías, E. | 7 | 2019-04-10 | 43 | 15-500 | 81.0 | 5.7 |" (ALMA Observations)
- pi or archival as stated: Archival compilation (PIs: Honda, M.; Pineda, J.; Perez, S.; Tsukagoshi, T.; Macías, E.)  
  > "We obtained the calibrated measurement sets from the ALMA archive and performed one round of phase-only self-calibration (interval 60 seconds) on the data after flagging the line containing channels." (Observations); "Many of the line detections presented in this work are serendipitous detections in continuum spectral windows in archival ALMA data." (Conclusion)
- Line: [CI] ^3P_1-^3P_0 (492.160651 GHz)
- Line: not stated J=4-3 (288.143858 GHz)
- Line: DCN J=3-2 (217.238539 GHz)
- Line: DCN J=4-3 (289.644917 GHz)
- Line: not stated J=3-2 (279.511701 GHz)
- Line: CS J=7-6 (342.882850 GHz)
- Line: CS J=10-9 (489.750921 GHz)
- Line: not stated J=6-5 (289.209066 GHz)
- Line: not stated J=6-5 (277.455405 GHz)
- Line: SO J=8_8-7_7 (344.310612 GHz)
- Line: not stated J=8_(1,7)-7_(1,6) (278.887661 GHz)
- Line: not stated J=3_0,3-2_0,2 (218.222192 GHz)
- Line: not stated J=3_2,2-3_2,1 (218.475632 GHz)
- Line: not stated J=4_0,4-3_0,3 (290.623405 GHz)
- Line: not stated J=4_2,2-3_1,2 (218.440050 GHz)
- Line: not stated J=9_(-1,9)-8_(0,8) (278.304510 GHz)
- Line: not stated J=6-5 blend (strongest J=6_(-3,4)-5_(-3,3)) (290.209700 GHz)
- Line: not stated J=11_(1,10)-11_(0,11) (331.502370 GHz)
- Line: not stated J=24-23 (218.324723 GHz)
- Line: not stated J=6_(0,6)-5_(1,5) and J=6_(1,6)-5_(0,5) blend (217.822148 GHz)
- External data: Molecular spectroscopic data (frequencies, upper state energies, Einstein A coefficients, degeneracies)  
  > "All of the molecular data are taken from the Cologne Database for Molecular Spectroscopy (cite: 2005JMoSt.742..215M)." (Observations) [from Cologne Database for Molecular Spectroscopy (cite: 2005JMoSt.742..215M)]
- External data: C18O J=2-1 disk-integrated flux of 3.9 +/- 0.5 Jy km s^-1  
  > "For reference, the $J=2-1$ disk integrated flux from (cite: 2017A&A...600A..72F) is 3.9$\pm$0.5 Jy km s$^{-1}$." (Observations); "We take the HD169142 $J=2-1$ line flux of 3.9 Jy km s$^{-1}$ from (cite: 2017A&A...600A..72F)." (Organic content) [from (cite: 2017A&A...600A..72F)]
- External data: 0.9 mm continuum image, 12CO map, and SO column density of (2.1 +/- 0.3) x 10^13 cm^-2 at 100 K  
  > "For comparison, we also include the 0.9 mm continuum image and map from (cite: Law2023)." (Results); "| | \- | \- | (2.1$\pm$0.3)$\times10^{13*}$ |" (Table 2); "$^{*}$ taken from (cite: Law2023)." (Results) [from (cite: Law2023)]
- External data: Fiducial disk dust temperature model of HD 169142  
  > "The dust temperature in the fiducial model of this disk from (cite: 2018A&A...614A.106C) only reaches the freeze-out temperature of CO ($\approx$20 K) in the midplane of the very outer disk at $\approx$150 au" (Locating the CO and snowlines); "This is also consistent with the model from (cite: 2018A&A...614A.106C) which places the midplane snowline at $\approx$20 au, which is at the edge of the inner dust ring (shown in Figure E1)." (Locating the CO and snowlines) [from (cite: 2018A&A...614A.106C)]
- External data: ISM sulfur isotope ratios (32S/34S = 22, 12C/13C = 69)  
  > "This is done for SO, CS (using the optically thinner and assuming = 22, e.g.; (cite: 1999RPPh...62..143W))," (Results); "compared to the ISM isotope ratios ( = 22, /=69, e.g.; (cite: 1999RPPh...62..143W))" (Volatile sulphur and C/O) [from (cite: 1999RPPh...62..143W)]
- Simulation/model as data: Fiducial HD 169142 disk dust temperature model from Carney et al. (2018)  
  > "The dust temperature in the fiducial model of this disk from (cite: 2018A&A...614A.106C) only reaches the freeze-out temperature of CO ($\approx$20 K) in the midplane of the very outer disk at $\approx$150 au" (Locating the CO and snowlines); "This is also consistent with the model from (cite: 2018A&A...614A.106C) which places the midplane snowline at $\approx$20 au, which is at the edge of the inner dust ring (shown in Figure E1)." (Locating the CO and snowlines)

## Processing

### Calibration

- pipeline or manual: Calibrated by ALMA staff, followed by manual self-calibration  
  > "All data sets were first calibrated by the ALMA staff and the subsequent data reduction, representative angular resolution and the molecules detected in each data set are summarised below:" (Observations); "We obtained the calibrated measurement sets from the ALMA archive and performed one round of phase-only self-calibration (interval 60 seconds) on the data after flagging the line containing channels." (Observations)
- casa version: CASA 6.2  
  > "We performed all of the imaging in CASA version 6.2 (cite: 2007ASPC..376..127M)" (Observations)
- pipeline version: _not stated_
- archive products used as is: No; calibrated measurement sets from archive were further self-calibrated, continuum-subtracted, and imaged  
  > "We obtained the calibrated measurement sets from the ALMA archive and performed one round of phase-only self-calibration (interval 60 seconds) on the data after flagging the line containing channels." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "Since we are comparing molecular lines from a variety of different sets of observations we take the errors on the integrated fluxes to be the 10% absolute flux calibration uncertainty of ALMA." (Observations); "We take the errors on these fluxes to be $\pm$10% due to the uncertainty on the absolute flux calibration of ALMA." (Results)
- self calibration: Phase-only self-calibration: 2016.1.00344.S (1 round, 60s, +20% continuum SNR); 2016.1.00346.S (3 rounds, 60, 20, 6s, +40% continuum SNR); 2018.1.01237 (3 rounds, inf down to 30s, continuum SNR ~900 to ~1600)  
  > "We obtained the calibrated measurement sets from the ALMA archive and performed one round of phase-only self-calibration (interval 60 seconds) on the data after flagging the line containing channels." (Observations); "This consisted of three rounds of phase-only calibration using solution lengths (60, 20 and 6 seconds)." (Observations); "Three rounds of phase-only self-calibration were applied, with solution intervals going down from inf (i.e., the scan duration) to 30 s." (Observations)

### Imaging

- task: tCLEAN  
  > "We performed all of the imaging in CASA version 6.2 (cite: 2007ASPC..376..127M) and used Keplerian masks for the tCLEAN mask (generates with the code from (cite: rich_teague_2020_4321137)) for lines at a spectral resolution $<$2 km s$^{-1}$" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 or 2.0 (line dependent)  
  > "| | $^{3}P_1-^3P_0$ | 492.160651 | 24 | 7.994$\times10^{-4}$ | 3 | 2.0 | 1.07"$\times$0.51" (81) | 0.15 | 71.9 | (7.4$\pm$0.7)$\times10^{3}$ |" (Table 1); "| | $J=4-3$ | 288.143858 | 35 | 5.858$\times10^{-3}$ | 9 | 0.5 | 0.72"$\times$0.46" (89) | 0.26 | 2.64 | 970$\pm$100 |" (Table 1)
- uv taper: 0.4" beam taper for all lines in 2016.1.00344.S except HC3N; Gaussian uv-taper of 0.25" for CS J=7-6  
  > "All lines in the 2016.1.00344.S data aside from were tapered to a 0.4" beam to increase signal-to-noise." (Observations); "$\dagger$ The CS $J=7-6$ image was generated with a Gaussian uv-taper of 0.25" and then further smoothed in the image plane with the CASA `imsmooth` task using a Gaussian kernel of 0.2"." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks (for spectral resolution < 2 km s^-1) and hand-drawn elliptical masks (for coarser spectral resolution)  
  > "used Keplerian masks for the tCLEAN mask (generates with the code from (cite: rich_teague_2020_4321137)) for lines at a spectral resolution $<$2 km s$^{-1}$ and hand-drawn elliptical tCLEAN masks for other lines that were observed at a coarser spectral resolution" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub with fit order 1 after excluding line-containing channels  
  > "The continuum was subtracted using uvcontsub with a fit order of 1 after excluding the line containing channels." (Observations)
- line free channels: Identified iteratively by subtracting continuum assuming no lines, making a dirty image, extracting spectra to identify lines, and re-running uvcontsub with those channels flagged  
  > "The line containing channels of the continuum spectral windows were identified in an iterative process. First, the continuum was subtracted assuming no lines were present, we made a dirty image of the line, extracted spectra, identified any lines and then made a new continuum subtracted measurement set flagging these channels." (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CASA imsmooth with 0.2" Gaussian kernel for CS J=7-6; SO and CH3OH convolved to 0.7" resolution to match C34S and H2CO for radial column density ratios  
  > "$\dagger$ The CS $J=7-6$ image was generated with a Gaussian uv-taper of 0.25" and then further smoothed in the image plane with the CASA `imsmooth` task using a Gaussian kernel of 0.2"." (Observations); "Figure 3 shows the radial column densities at the native angular resolution for each of the four molecules alongside a version where the and images are convolved to the same angular resolution of the and data using CASA tool imsmooth." (Results); "Since the SO data are convolved to a lower spatial resolution (0.7") the minimum N(CS)/N(SO) is likely lower than 1.0" (Volatile sulphur and C/O)
- final beam: Ranges from 0.19"x0.14" (PA 84 deg) to 1.07"x0.51" (PA 81 deg); see Table 1 for each transition  
  > "| | $^{3}P_1-^3P_0$ | 492.160651 | 24 | 7.994$\times10^{-4}$ | 3 | 2.0 | 1.07"$\times$0.51" (81) | 0.15 | 71.9 | (7.4$\pm$0.7)$\times10^{3}$ |" (Table 1); "| | $J=8_8-7_7$ | 344.310612 | 88 | 5.186$\times10^{-4}$ | 17 | 2.0 | 0.19"$\times$0.14" (84) | 0.46 | 1.50 | 120$\pm$10 |" (Table 1)
- final rms: 0.23 to 130.7 mJy beam^-1 per channel; see Table 1 for each transition  
  > "| | $J=10-9$ | 489.750921 | 129 | 2.489$\times10^{-3}$ | 21 | 0.5 | 0.94"x0.40" (83) | 0.15 | 130.7 | (4.3$\pm$0.4)$\times10^{3}$ |" (Table 1); "| | $J=6-5$ | 289.209066 | 38 | 4.812$\times10^{-4}$ | 13 | 0.5 | 0.73"$\times$0.46" (89) | 16.2 | 0.23 | 261.0$\pm$30 |" (Table 1)

### Inherited from earlier work

- Data reduction for ALMA Projects 2012.1.00799.S and 2015.1.00806.S  
  > "For further details about the data reduction, please refer to (cite: Law2023)." (Observations); "For further details on the data reduction, please refer to (cite: Law2023)." (Observations) [from (cite: Law2023)]
- Matched filtering method to confirm weak line detection  
  > "A weak detection of in the images was confirmed via both matched filtering and spectral stacking with GoFish (cite: 2018AJ....155..182L; GoFish)." (Observations) [from (cite: 2018AJ....155..182L)]
- Keplerian mask generation code for tCLEAN  
  > "used Keplerian masks for the tCLEAN mask (generates with the code from (cite: rich_teague_2020_4321137)) for lines at a spectral resolution $<$2 km s$^{-1}$" (Observations) [from (cite: rich_teague_2020_4321137)]
- Standard LTE optically thin column density calculation methods  
  > "We estimate disk-averaged column densities for all the molecules detected using these disk-integrated fluxes following the now standard methods (cite: 2018ApJ...859..131L)." (Results) [from (cite: 2018ApJ...859..131L)]

### Not stated but needed to reproduce (our reading)

- Deconvolver algorithm (e.g., hogbom, multiscale) and stopping threshold/niter used in CASA tCLEAN
- Pixel cell size and image dimensions used during tCLEAN imaging
- Exact parameters used to generate the Keplerian masks (stellar mass, systemic velocity, spatial/velocity buffer widths) and dimensions of the hand-drawn elliptical masks
- Specific channel ranges flagged for line emission prior to self-calibration and continuum subtraction

## Analysis recipe

1. **Self-calibration, iterative continuum subtraction, and line imaging**: Phase-only self-calibration on continuum after flagging lines; iterative line identification in continuum windows followed by uvcontsub (fit order 1); imaging with tCLEAN using Keplerian masks (<2 km/s resolution) or hand-drawn elliptical masks, applying uv-tapers and imsmooth where needed.  
  > "The continuum was subtracted using uvcontsub with a fit order of 1 after excluding the line containing channels." (Observations); "We performed all of the imaging in CASA version 6.2 (cite: 2007ASPC..376..127M) and used Keplerian masks for the tCLEAN mask (generates with the code from (cite: rich_teague_2020_4321137)) for lines at a spectral resolution $<$2 km s$^{-1}$ and hand-drawn elliptical tCLEAN masks for other lines" (Observations)
   - software: CASA, tCLEAN, uvcontsub, imsmooth, keplerian_mask
   - parameter: uvcontsub fit order = 1; Briggs robust = 0.5 or 2.0; 0.4" uv-taper for 2016.1.00344.S lines (except HC3N); 0.25" uv-taper and 0.2" imsmooth kernel for CS J=7-6  
  > "The continuum was subtracted using uvcontsub with a fit order of 1 after excluding the line containing channels." (Observations); "All lines in the 2016.1.00344.S data aside from were tapered to a 0.4" beam to increase signal-to-noise." (Observations); "$\dagger$ The CS $J=7-6$ image was generated with a Gaussian uv-taper of 0.25" and then further smoothed in the image plane with the CASA `imsmooth` task using a Gaussian kernel of 0.2"." (Observations)
   - fitting: _not stated_
   - validation: Assessed continuum SNR improvement after self-calibration (20% for 2016.1.00344.S, 40% for 2016.1.00346.S, ~900 to ~1600 for 2018.1.01237)  
  > "This resulted in only a 20% improvement in the continuum signal-to-nose ratio." (Observations); "The self-calibration yielded a signal-to-noise improvement of 40% for the continuum." (Observations); "Overall, the SNR of the continuum improved from $\sim900$ to $\sim1600$." (Observations)
2. **Confirm weak N2H+ line detection**: Matched filtering and spectral stacking using GoFish  
  > "A weak detection of in the images was confirmed via both matched filtering and spectral stacking with GoFish (cite: 2018AJ....155..182L; GoFish)." (Observations)
   - software: GoFish
   - fitting: _not stated_
   - validation: Compared matched filter response and GoFish stacked spectrum (Figure B1)  
  > "A weak detection of in the images was confirmed via both matched filtering and spectral stacking with GoFish (cite: 2018AJ....155..182L; GoFish)." (Observations); "Comparisons of matched filter and GoFish detections of" (Comparisons of matched filter and GoFish detections of)
3. **Generate integrated intensity maps, radial profiles, and disk-integrated fluxes**: Generated moment 0 maps using the same Keplerian or elliptical masks as imaging with no flux clipping; extracted azimuthally-averaged radial profiles and measured disk-integrated fluxes.  
  > "All integrated intensity maps were generated with the same Keplerian or elliptical masks used in the imaging with no flux clipping to ensure accurate fluxes." (Results); "Figure 2 shows the azimuthally-averaged radial profiles for the same lines as presented in Figure 1." (Results); "Table [\[tab:1\]](#tab:1) lists the disk-integrated fluxes for all of the detected lines." (Results)
   - parameter: No flux clipping; 10% absolute flux calibration uncertainty adopted for flux errors  
  > "All integrated intensity maps were generated with the same Keplerian or elliptical masks used in the imaging with no flux clipping to ensure accurate fluxes." (Results); "We take the errors on these fluxes to be $\pm$10% due to the uncertainty on the absolute flux calibration of ALMA." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute disk-averaged and radial column densities and abundance ratios**: Calculated disk-averaged column densities from integrated fluxes and radial column density profiles from azimuthally-averaged emission profiles using standard optically thin LTE methods; convolved SO and CH3OH images with imsmooth to match C34S and H2CO resolution for radial ratios.  
  > "We estimate disk-averaged column densities for all the molecules detected using these disk-integrated fluxes following the now standard methods (cite: 2018ApJ...859..131L). This assumes the gas is in local thermodynamic equilibrium and that the line emission is optically thin." (Results); "We also compute radial column densities from the emission profiles presented in Figure 2." (Results); "Figure 3 shows the radial column densities at the native angular resolution for each of the four molecules alongside a version where the and images are convolved to the same angular resolution of the and data using CASA tool imsmooth." (Results)
   - software: CASA, imsmooth
   - parameter: Circular emitting area of 2" for disk-averaged column densities (0.3" for CH3OH and SO); T_ex = 30 K and 60 K for cooler gas species, 100 K for SO and CH3OH; fixed T_ex = 60 K for radial column densities  
  > "Disk-averaged column densities assuming a circular emitting area of 2" for all species aside from and SO where we use 0.3"." (Results); "For most species, we only detect one transition therefore we calculate all of the column densities at 30 and 60 K for the molecules we expect to be tracing cooler gas and 100 K for the SO and which are emitting from the warmer inner disk." (Results); "Since we do not have any excitation information we assume a fixed temperature of 60 K." (Results)
   - assumption: Local thermodynamic equilibrium (LTE), optically thin emission, and ISM isotope ratios (32S/34S = 22, 12C/13C = 69)  
  > "This assumes the gas is in local thermodynamic equilibrium and that the line emission is optically thin." (Results); "This is done for SO, CS (using the optically thinner and assuming = 22, e.g.; (cite: 1999RPPh...62..143W))," (Results); "compared to the ISM isotope ratios ( = 22, /=69, e.g.; (cite: 1999RPPh...62..143W))" (Volatile sulphur and C/O)
   - fitting: _not stated_
   - validation: Excluded low-SNR H2CO J=3_(2,2)-3_(2,1) and CH3OH J=4_(2,2)-3_(1,2) lines; assessed optical depth of CS by comparing 12CS/13CS and CS/C34S column density ratios to ISM values  
  > "We exclude the $J=3_{(2,2)}-3_{(2,1)}$ and $J=4_{(2,2)}-_{(1,2)}$ lines from this analysis as they are low signal-to-noise detections in the spectra (see Figure C1)." (Results); "Using the ratios between the different isotopologues we can assess if the main isotopologue is optically thick." (Volatile sulphur and C/O)

## Software

- **CASA** 6.2: Self-calibration, continuum subtraction (uvcontsub), line imaging (tCLEAN), and image-plane Gaussian smoothing (imsmooth)  
  > "We performed all of the imaging in CASA version 6.2 (cite: 2007ASPC..376..127M)" (Observations); "The continuum was subtracted using uvcontsub with a fit order of 1 after excluding the line containing channels." (Observations); "convolved to the same angular resolution of the and data using CASA tool imsmooth." (Results)
- **GoFish** : Spectral stacking to confirm weak N2H+ line detection  
  > "A weak detection of in the images was confirmed via both matched filtering and spectral stacking with GoFish (cite: 2018AJ....155..182L; GoFish)." (Observations)
- **keplerian_mask** : Generating Keplerian masks for tCLEAN imaging of lines with spectral resolution < 2 km s^-1  
  > "used Keplerian masks for the tCLEAN mask (generates with the code from (cite: rich_teague_2020_4321137)) for lines at a spectral resolution $<$2 km s$^{-1}$" (Observations)
- **Astropy** : General analysis (listed in Acknowledgements)  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy)." (Acknowledgements)
- **IPython** : General analysis (listed in Acknowledgements)  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy)." (Acknowledgements)
- **Jupyter** : General analysis (listed in Acknowledgements)  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy)." (Acknowledgements)
- **Matplotlib** : Plotting (listed in Acknowledgements)  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy)." (Acknowledgements)
- **NumPy** : Numerical analysis (listed in Acknowledgements)  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CI] 3P1-3P0 disk-integrated flux | 7.4e3 | 0.7e3 | mJy km s^-1 | 3 | / / $^{3}P_1-^3P_0$ / 492.160651 / 24 / 7.994$\times10^{-4}$ / 3 / 2.0 / 1.07"$\times$0.51" (81) / 0.15 / 71.9 / (7.4$\pm$0.7)$\times10^{3}$ / |
| DCO+ J=4-3 (288.143858 GHz) disk-integrated flux | 970 | 100 | mJy km s^-1 | 3 | / / $J=4-3$ / 288.143858 / 35 / 5.858$\times10^{-3}$ / 9 / 0.5 / 0.72"$\times$0.46" (89) / 0.26 / 2.64 / 970$\pm$100 / |
| DCN J=3-2 (217.238539 GHz) disk-integrated flux | 93.0 | 10 | mJy km s^-1 | 3 | / / $J=3-2$ / 217.238539 / 21 / 4.575$\times10^{-4}$ / 21 / 2.0, taper / 0.41"$\times$0.37" (86) / 2.7 / 0.67 / 93.0.0$\pm$10 / |
| DCN J=4-3 (289.644917 GHz) disk-integrated flux | 240.0 | 20 | mJy km s^-1 | 3 | / / $J=4-3$ / 289.644917 / 35 / 1.124$\times10^{-3}$ / 27 / 0.5 / 0.73"$\times$0.46" (89) / 16.2 / 0.24 / 240.0$\pm$20 / |
| N2H+ J=3-2 (279.511701 GHz) disk-integrated flux | 55.0 | 6 | mJy km s^-1 | 3 | / / $J=3-2$ / 279.511701 / 27 / 1.259$\times10^{-3}$ / 63 / 2.0 / 0.91"$\times$0.58" (85) / 0.14 / 2.95 / 55.0$\pm$6 / |
| CS J=7-6 (342.882850 GHz) disk-integrated flux | >=7e3 | not stated | mJy km s^-1 | 3 | / $\dagger$ / $J=7-6$ / 342.882850 / 66 / 8.368$\times10^{-4}$ / 15 / 0.5 / 0.29"$\times$0.26"(37) / 0.85 / 11.7 / ${\gtrsim}$7$\times10^{3}$ / |
| CS J=10-9 (489.750921 GHz) disk-integrated flux | 4.3e3 | 0.4e3 | mJy km s^-1 | 3 | / / $J=10-9$ / 489.750921 / 129 / 2.489$\times10^{-3}$ / 21 / 0.5 / 0.94"x0.40" (83) / 0.15 / 130.7 / (4.3$\pm$0.4)$\times10^{3}$ / |
| C34S J=6-5 (289.209066 GHz) disk-integrated flux | 261.0 | 30 | mJy km s^-1 | 3 | / / $J=6-5$ / 289.209066 / 38 / 4.812$\times10^{-4}$ / 13 / 0.5 / 0.73"$\times$0.46" (89) / 16.2 / 0.23 / 261.0$\pm$30 / |
| 13CS J=6-5 (277.455405 GHz) disk-integrated flux | 51 | 5 | mJy km s^-1 | 3 | / / $J=6-5$ / 277.455405 / 47 / 4.399$\times10^{-4}$ / 26 / 0.5 / 0.73"$\times$0.46" (89) / 1.10 / 1.1 / 51$\pm$5 / |
| SO J=8_8-7_7 (344.310612 GHz) disk-integrated flux | 120 | 10 | mJy km s^-1 | 3 | / / $J=8_8-7_7$ / 344.310612 / 88 / 5.186$\times10^{-4}$ / 17 / 2.0 / 0.19"$\times$0.14" (84) / 0.46 / 1.50 / 120$\pm$10 / |
| H2CS J=8_(1,7)-7_(1,6) (278.887661 GHz) disk-integrated flux | 140 | 10 | mJy km s^-1 | 3 | / / $J=8_{(1,7)}-7_{1,6}$ / 278.887661 / 73 / 3.181$\times10^{-4}$ / 51 / 0.5 / 0.73"$\times$0.46" (89) / 1.10 / 1.07 / 140$\pm$10 / |
| H2CO J=3_0,3-2_0,2 (218.222192 GHz) disk-integrated flux | 480 | 50 | mJy km s^-1 | 3 | / / $J=3_{0,3}-2_{0,2}$ / 218.222192 / 21 / 2.818$\times10^{-4}$ / 7 / 2.0, taper / 0.41"$\times$0.37" (86) / 2.7 / 0.52 / 480$\pm$50 / |
| H2CO J=3_2,2-3_2,1 (218.475632 GHz) disk-integrated flux | 55 | 6 | mJy km s^-1 | 3 | / / $J=3_{2,2}-3_{2,1}$ / 218.475632 / 68 / 1.571$\times10^{-4}$ / 7 / 2.0, taper / 0.41"$\times$0.37" (86) / 2.7 / 0.51 / 55$\pm$6 / |
| H2CO J=4_0,4-3_0,3 (290.623405 GHz) disk-integrated flux | 900 | 90 | mJy km s^-1 | 3 | / / $J=4_{0,4}-3_{0,3}$ / 290.623405 / 35 / 6.902$\times10^{-4}$ / 9 / 0.5 / 0.73"$\times$0.46" (89) / 16.2 / 0.26 / 900$\pm$90 / |
| CH3OH J=4_2,2-3_1,2 (218.440050 GHz) disk-integrated flux | 65 | 7 | mJy km s^-1 | 3 | / / $J=4_{2,2}-3_{1,2}$ / 218.440050 / 45 / 4.687$\times10^{-5}$ / 36 / 2.0 / 0.20"$\times$0.15" (88) / 0.46 / 1.44 / 65$\pm$7 / |
| CH3OH J=9_(-1,9)-8_(0,8) (278.304510 GHz) disk-integrated flux | 13 | 1 | mJy km s^-1 | 3 | / / $J=9_{(-1,9)}-8_{(0,8)}$ / 278.304510 / 110 / 7.685$\times10^{-5}$ / 76 / 0.5 / 0.73"$\times$0.46" (89) / 1.10 / 1.05 / 13$\pm$1 / |
| CH3OH J=6-5 blend (290.209700 GHz) disk-integrated flux | 104 | 10 | mJy km s^-1 | 3 | / / blend$^*$ / 290.209700 / 112 / 7.994$\times10^{-5}$ / 52 / 0.5 / 0.73"$\times$0.46" (89) / 16.2 / 0.24 / 104$\pm$10 / |
| CH3OH J=11_(1,10)-11_(0,11) (331.502370 GHz) disk-integrated flux | 44 | 10 | mJy km s^-1 | 3 | / / $J=11_{(1,10)}-11_{(0,11)}$ / 331.502370 / 169 / 3.929$\times10^{-4}$ / 92 / 2.0 / 0.20"$\times$0.15" (88) / 0.46 / 1.44 / 44$\pm$10 / |
| HC3N J=24-23 (218.324723 GHz) disk-integrated flux | 171 | 20 | mJy km s^-1 | 3 | / / $J=24-23$ / 218.324723 / 131 / 8.261$\times10^{-4}$ / 49 / 2.0 / 0.26"$\times$0.21" (74) / 2.7 / 0.45 / 171$\pm$20 / |
| c-C3H2 J=6_(0,6)-5_(1,5) and J=6_(1,6)-5_(0,5) blended (217.822148 GHz) disk-integrated flux | 59 | 6 | mJy km s^-1 | 3 | / / $J=6_{(0,6)}-5_{(1,5)}$ / 217.822148 / 39 / 5.934$\times10^{-4}$ / 13 / 2.0, taper / 0.41"$\times$0.37" (86) / 2.7 / 0.59 / 59$\pm$6$\dagger$$\dagger$ / |
| [CI] disk-averaged column density (T_ex = 60 K) | 5.0e16 | 0.5e16 | cm^-2 | 4 | / / (5.1$\pm$0.5)$\times10^{16}$ / (5.0$\pm$0.5)$\times10^{16}$ / \- / |
| CH3OH disk-averaged column density (T_ex = 100 K) | 3.3e14 | 0.3e14 | cm^-2 | 4 | / / \- / \- / (3.3$\pm$0.3)$\times10^{14}$ / |
| CS / C34S column density ratio (T_ex = 30 K) | 44 | 10 | dimensionless | 4 | The inferred column density ratios of / (44$\pm$10 at 30 K, 10$\pm$5 at 60 K) and / (150$\pm$30 at 30 K, 36$\pm$8 at 60 K) |
| CS / C34S column density ratio (T_ex = 60 K) | 10 | 5 | dimensionless | 4 | The inferred column density ratios of / (44$\pm$10 at 30 K, 10$\pm$5 at 60 K) and / (150$\pm$30 at 30 K, 36$\pm$8 at 60 K) |
| CS / 13CS column density ratio (T_ex = 30 K) | 150 | 30 | dimensionless | 4 | The inferred column density ratios of / (44$\pm$10 at 30 K, 10$\pm$5 at 60 K) and / (150$\pm$30 at 30 K, 36$\pm$8 at 60 K) |
| CS / 13CS column density ratio (T_ex = 60 K) | 36 | 8 | dimensionless | 4 | The inferred column density ratios of / (44$\pm$10 at 30 K, 10$\pm$5 at 60 K) and / (150$\pm$30 at 30 K, 36$\pm$8 at 60 K) |
| H2CS / CS column density ratio (T_ex = 30 K) | 0.22 | 0.04 | dimensionless | 4 | The CS is ringed and the follows this same spatial distribution with a / ratio of 0.22$\pm$0.04 at 30 K and 0.18$\pm$0.04 at 60 K |
| H2CS / CS column density ratio (T_ex = 60 K) | 0.18 | 0.04 | dimensionless | 4 | The CS is ringed and the follows this same spatial distribution with a / ratio of 0.22$\pm$0.04 at 30 K and 0.18$\pm$0.04 at 60 K |
| N(CS)/N(SO) radial column density ratio at 10 au | 1.0 | 0.2 | dimensionless | 4 | From Figure 3 the N(CS)/N(SO) ratio is $1.0\pm$0.2 at 10 au and then increases radially to $>10$ by 100 au. |
| N(CS)/N(SO) radial column density ratio at 100 au | >10 | not stated | dimensionless | 4 | From Figure 3 the N(CS)/N(SO) ratio is $1.0\pm$0.2 at 10 au and then increases radially to $>10$ by 100 au. |
| N(CS)/N(SO) radial column density ratio at 37 au (location of HD 169142 b) | 2.0 | 0.4 | dimensionless | 4 | From Figure 3 the N(CS)/N(SO) ratio at the location of HD 169142 b is 2.0$\pm$0.4. |
| N(CH3OH)/N(H2CO) radial column density ratio at 10 au | 140 | 40 | dimensionless | 4 | Within the snowline line at 10 au this ratio is 140$\pm$40 which decreases sharply to $<$3 beyond $\approx$60 au. |
| N(CH3OH)/N(H2CO) radial column density ratio beyond ~60 au | <3 | not stated | dimensionless | 4 | Within the snowline line at 10 au this ratio is 140$\pm$40 which decreases sharply to $<$3 beyond $\approx$60 au. |

## Qualitative findings

- First detections of DCN, N2H+, [CI], CS, C34S, 13CS, H2CS, H2CO, CH3OH, HC3N, and c-C3H2 in the HD 169142 disk (13 species total including DCO+ and SO).  
  > "In this paper, we present Atacama Large Millimeter/submillimeter Array (ALMA) observations of the HD 169142 disk where we detect 13 different species." (Introduction); "We present the first detections of , , [CI], , , , , , , and in the HD 169142 disk." (Conclusion)
- All newly reported molecules show varying ring-like morphologies, with SO and CH3OH being the most compact and showing a clear radial anti-correlation between SO and CS.  
  > "All of the newly reported molecules show varying ring-like morphologies with the SO and being the most compact." (Results); "These profiles highlight a clear anti-correlation between SO and CS." (Results)
- Low N2H+ line flux relative to 13CO indicates minimal CO freeze-out in the HD 169142 disk; any CO snowline lies beyond the mm-dust disk edge (~100 au) at ~150 au.  
  > "This comparison and the temperature structure in the disk model from (cite: 2018A&A...614A.106C) indicates the lack of CO freeze-out in the HD 169142 disk but, if there is a CO freeze-out in this disk it is likely beyond the mm-dust disk edge ($\approx$100 au) and out at $\approx$150 au." (Conclusion)
- Compact CH3OH and SO emission in the inner disk traces thermal ice sublimation at the H2O snowline located at the edge of the inner mm-dust ring (~20 au), supporting the inheritance of complex ices.  
  > "The detection of and from the inner disk can be explained by the sublimation of ices putting the snowline at the edge of the inner mm-dust $\approx$20 au." (Conclusion); "Since needs to form in the cold phase, this further supports the hypothesis that complex ices can survive the disk formation process." (Conclusion)
- The giant planet HD 169142 b (at 37 au) is located between the H2O (and likely CO2) snowline and the CO snowline, where the gas-phase C/O ratio is ~1.0, while any companion inside the central cavity (<20 au) accretes gas with C/O < 1.  
  > "We estimate that the giant planet HD 169142 b is forming between the and snowlines and given the temperature structure of the disks likely between the and snowlines. This is a region of the disk where C/O$\approx$1.0." (Conclusion); "If there is another giant planet in the central cavity $<$20 au this is within the snowline and therefore the planet will be accreting gas with C/O$<$1." (Conclusion)

## Claim tuples

- H: N2H+ emission traces the location of the CO snowline and the degree of CO freeze-out in the HD 169142 disk. | E: Detected N2H+ J=3-2 via imaging, matched filtering, and GoFish spectral stacking, and compared its distance-scaled flux and N2H+/C18O ratio with chemical models and other protoplanetary disks (TW Hya, MWC 480, HD 163296). | R: N2H+ J=3-2 flux is 55.0 +/- 6 mJy km s^-1 (~10x weaker than in TW Hya, MWC 480, and HD 163296, and ~5x weaker relative to C18O J=2-1 than in the Herbig disks), consistent with a gas-phase CO/H2 abundance of ~10^-4. | F: There is minimal CO freeze-out in the warm HD 169142 disk; weak N2H+ likely traces upper disk atmosphere chemistry, and any midplane CO snowline lies beyond the mm-dust rings at ~150 au. | **supported**
- H: Compact CH3OH and SO emission in the inner disk traces thermal desorption of ices at the H2O snowline and indicates inheritance of pre-stellar ices. | E: Imaged multiple CH3OH transitions, SO, and H2CO, and computed the radial column density ratio N(CH3OH)/N(H2CO) across the disk. | R: CH3OH and SO emission are compact inside the inner dust ring, and N(CH3OH)/N(H2CO) is 140 +/- 40 at 10 au, dropping sharply to < 3 beyond ~60 au. | F: The H2O snowline is located at the edge of the inner mm-dust ring (~20 au) where T > 100 K; because HD 169142 is warm (T_dust > 20 K) with limited CO freeze-out, the CH3OH ice must be inherited from the cold pre-stellar phase rather than formed in-situ. | **supported**
- H: Radial variations in volatile sulfur carriers (CS and SO) and hydrocarbons/nitriles trace changes in the gas-phase C/O ratio across the H2O snowline and at the orbit of the giant planet HD 169142 b (37 au). | E: Derived radial column density profiles of CS (from C34S) and SO at matched 0.7" resolution and mapped ring morphologies of c-C3H2 and HC3N relative to the planet locations. | R: SO lies interior to the CS ring; N(CS)/N(SO) increases from 1.0 +/- 0.2 at 10 au to 2.0 +/- 0.4 at 37 au (HD 169142 b) and > 10 at 100 au, while c-C3H2 and HC3N peak in rings at the outer edge of the mm-dust disk. | F: Gas-phase C/O increases across the H2O snowline (~20 au); any planet in the central cavity (<20 au) accretes gas with C/O < 1, whereas HD 169142 b at 37 au forms between the H2O/CO2 and CO snowlines and accretes gas with C/O ~ 1.0 (unless locally lowered by planetary shock heating). | **supported**

## Reasoning

- Why this data: Shorter baseline data from 2016.1.00344.S were selected because they are optimal for searching for weak extended molecular line emission.  
  > "This project also has higher angular resolution data ($\approx$0.02") associated with it (cite: 2019AJ....158...15P) but as we are searching for weak lines emission we only make use of the shorter baseline data, which are optimal for our science goals." (Observations)
- Why this method: Keplerian masks were used for high spectral resolution lines (<2 km/s) while hand-drawn elliptical masks were used for coarse resolution lines because the total line width across the nearly face-on disk is only a few km/s; optically thinner C34S was used to trace CS radial column density; a fixed intermediate T_ex = 60 K was assumed for radial profiles due to lack of multi-line excitation constraints.  
  > "used Keplerian masks for the tCLEAN mask (generates with the code from (cite: rich_teague_2020_4321137)) for lines at a spectral resolution $<$2 km s$^{-1}$ and hand-drawn elliptical tCLEAN masks for other lines that were observed at a coarser spectral resolution as total line width is only a few km s$^{-1}$ across the disk." (Observations); "This is done for SO, CS (using the optically thinner and assuming = 22, e.g.; (cite: 1999RPPh...62..143W))," (Results); "Since we do not have any excitation information we assume a fixed temperature of 60 K. The SO and are likely warmer than this and the CS and may be cooler but given the data in hand this intermediate temperature is the simplest assumption to make." (Results)
- Alternative: Rejected using the ~0.02" long-baseline execution of Project 2016.1.00344.S, keeping only the shorter baseline (~0.2") data which are optimal for weak line emission.  
  > "This project also has higher angular resolution data ($\approx$0.02") associated with it (cite: 2019AJ....158...15P) but as we are searching for weak lines emission we only make use of the shorter baseline data, which are optimal for our science goals." (Observations)
- Alternative: Excluded H2CO J=3_(2,2)-3_(2,1) and CH3OH J=4_(2,2)-3_(1,2) from the column density calculations due to low signal-to-noise and differing emission morphology.  
  > "We exclude the $J=3_{(2,2)}-3_{(2,1)}$ and $J=4_{(2,2)}-_{(1,2)}$ lines from this analysis as they are low signal-to-noise detections in the spectra (see Figure C1). Additionally, the $J=3_{(2,2)}$-$3_{(2,1)}$ line does not share the same emission morphology as the other two strongly detected lines (see Figure D1)." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): CS J=7-6 integrated flux is only a lower limit due to the lack of short-baseline data in Project 2015.1.00806.S.  
  > "Due to the lack of short-baseline data we consider this flux a lower limit." (Observations)
- Limitation (authors): Lack of multi-line excitation information requires assuming fixed excitation temperatures (30, 60, or 100 K), introducing degeneracy between optical depth, isotope ratios, and emitting layer temperatures for CS isotopologues.  
  > "Since we do not have any excitation information we assume a fixed temperature of 60 K." (Results); "If the gas is cooler (30 K) then the isotopes appear to be less abundant than in the ISM, but they may emit from different layers of the disk and therefore at different temperatures. Observation of CS $J=6-5$ rather than $J=10-9$ to match the and lines, respectively, will help break this degeneracy." (Volatile sulphur and C/O)
- Limitation (authors): Convolving SO to 0.7" resolution to match C34S means the minimum N(CS)/N(SO) ratio in the inner disk is likely an upper limit (lower than 1.0 at native resolution).  
  > "Since the SO data are convolved to a lower spatial resolution (0.7") the minimum N(CS)/N(SO) is likely lower than 1.0 since the emission is more compact at 0.2" and the CS already shows a gas cavity in the 0.7" data." (Volatile sulphur and C/O)
- Limitation (authors): The CH3OH observations are not sensitive enough to detect a non-thermally desorbed outer-disk reservoir at N(CH3OH)/N(H2CO) ~ 1-2 as seen in HD 100546 and TW Hya.  
  > "In the colder outer disk, the data are not sensitive enough to detect the same non-thermally desorbed reservoir of as seen for HD 100546 and TW Hya where N()/N()$\approx$1-2 (cite: 2019A&A...623A.124C; 2021NatAs...5..684B)." (Organic content)
- Limitation (authors): Higher angular resolution observations are needed to resolve the spatial relationship between dust and the large organics (HC3N, c-C3H2, H2CO) and to characterize the local gas composition near HD 169142 b.  
  > "Higher angular resolution observations are required to properly determine the relationship between the dust, and the large organics , and ." (Organic content); "Future higher angular resolution observations will be able to further characterise the gas composition in the vicinity of this planet." (Conclusion)
- Caveat (inferred, ours): Several lines are detected in coarse continuum spectral windows (16.2 km/s and 2.7 km/s channels), which severely under-resolves the narrow line profiles (~few km/s) of this nearly face-on disk (i = 13 deg) and complicates continuum subtraction.
- Caveat (inferred, ours): Assuming a uniform circular emitting area of 2" (or 0.3" for SO and CH3OH) for disk-averaged column densities is a rough approximation given that the species exhibit distinct ring morphologies at different radii.
- Caveat (inferred, ours): Comparing CS J=10-9 (E_up = 129 K) in Band 8 with C34S J=6-5 (E_up = 38 K) and 13CS J=6-5 (E_up = 47 K) in Band 7 under a single isothermal assumption mixes transitions that likely probe different vertical/radial temperature layers.

## Reproducibility

- Data public (paper): Calibrated measurement sets were obtained from the public ALMA archive for projects 2012.1.00799.S, 2015.1.00806.S, 2016.1.00344.S, 2016.1.00346.S, and 2018.1.01237.S  
  > "We obtained the calibrated measurement sets from the ALMA archive and performed one round of phase-only self-calibration (interval 60 seconds) on the data after flagging the line containing channels." (Observations); "This work makes use of the following ALMA data: 2012.1.00799.S, 2015.1.00806.S, 2016.1.00344.S, 2016.1.00346.S, 2018.1.01237." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Exact tCLEAN stopping criteria (threshold, niter) and deconvolver choice
- Missing: Exact Keplerian mask parameters (stellar mass, systemic velocity, target radius, line width parameters) and hand-drawn elliptical mask regions
- Missing: Specific channel ranges flagged during iterative continuum subtraction in the continuum spectral windows
- Missing: Image pixel cell size and grid dimensions
- Data volume (inferred): ~50-150 GB across the 5 ALMA archival projects (8 execution blocks total, excluding the unused 0.02" long-baseline execution of 2016.1.00344.S)
- Score (inferred): 8/5, All five ALMA project codes and execution dates are explicitly tabulated, self-calibration solution intervals and SNR improvements are given per project, uvcontsub order is stated, and Table 1 provides exact rest frequencies, spectroscopic constants, robust parameters, tapers, synthesized beams, channel widths, rms values, and integrated fluxes, along with clear LTE column density assumptions (emitting areas and excitation temperatures). Only minor imaging and mask parameters (tCLEAN threshold, cell size, Keplerian mask inputs) are omitted.
- Rediscovery candidate: yes, All archival ALMA datasets are public, the imaging and optically thin LTE column density recipes are straightforward and well-specified, and the main results (integrated line fluxes, disk-averaged column densities, and radial column density ratios) are explicitly tabulated numeric values.

## Links

- Method: (cite: 2018AJ....155..182L) (Matched filtering technique used to confirm weak N2H+ emission)
- Method: (cite: GoFish) (GoFish spectral stacking software used to confirm N2H+ detection)
- Method: (cite: rich_teague_2020_4321137) (Code used to generate Keplerian masks for tCLEAN imaging)
- Method: (cite: 2018ApJ...859..131L) (Standard optically thin LTE column density calculation method)
- Companion: (cite: Law2023) (Presents the 12CO, 13CO, C18O, SiS, and SO data reduction and analysis from projects 2012.1.00799.S and 2015.1.00806.S, and provides the SO column density and 0.9 mm continuum/12CO comparison maps used in this work)

## Checks

```json
{
 "quotes": 207,
 "quotes_ok": 207,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 9,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 33,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 70,
  "rate": 0.787
 },
 "evidence_ok": true
}
```
