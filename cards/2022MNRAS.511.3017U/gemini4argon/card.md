# The bright extragalactic ALMA redshift survey (BEARS) I: redshifts of bright gravitationally lensed galaxies from the Herschel ATLAS

`2022MNRAS.511.3017U` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Urquhart, S. A. | arXiv: 2201.07815 | DOI: 10.1093/mnras/stac150

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Measure spectroscopic redshifts, CO line widths, CO luminosities, and magnification factors for bright gravitationally lensed submillimeter galaxies selected from the Herschel ATLAS South Galactic Pole field.  
  > "We present spectroscopic measurements for 71 galaxies associated with 62 of the brightest high-redshift submillimeter sources from the Southern fields of the Herschel Astrophysical Terahertz Large Area Survey (H-ATLAS), while targeting 85 sources which resolved into 142." (Abstract); "Here, we present robust spectroscopic redshift measurements from the 12-m Array obtained in ALMA Cycle 7 and from the ACA (Atacama Compact Array) in ALMA Cycles 4 and 6 for 71 galaxies: Bright Extragalactic ALMA Redshift Survey (BEARS)." (Introduction)
- Target **85 Herschel-ATLAS SGP sources (71 galaxies with robust spectroscopic redshifts)**: coordinates See Table 1 (e.g., HerBS-11 at 01:24:07.50, -28:14:34.7)  
  > "We present spectroscopic measurements for 71 galaxies associated with 62 of the brightest high-redshift submillimeter sources from the Southern fields of the Herschel Astrophysical Terahertz Large Area Survey (H-ATLAS), while targeting 85 sources which resolved into 142." (Abstract); "The spectroscopic redshifts span a range $1.41<z<4.53$ with a mean value of 2.75" (Abstract); "| J012407.4$-$281434 | 11 | 1 | | 01:24:07.50 | $-$28:14:34.7 | 2.631 | |" (Table 1); z/distance 1.41 < z < 4.53 (mean 2.75)  
  > "We present spectroscopic measurements for 71 galaxies associated with 62 of the brightest high-redshift submillimeter sources from the Southern fields of the Herschel Astrophysical Terahertz Large Area Survey (H-ATLAS), while targeting 85 sources which resolved into 142." (Abstract); "The spectroscopic redshifts span a range $1.41<z<4.53$ with a mean value of 2.75" (Abstract); "| J012407.4$-$281434 | 11 | 1 | | 01:24:07.50 | $-$28:14:34.7 | 2.631 | |" (Table 1); distance from ALMA spectroscopic redshifts obtained in this work  
  > "We present spectroscopic measurements for 71 galaxies associated with 62 of the brightest high-redshift submillimeter sources from the Southern fields of the Herschel Astrophysical Terahertz Large Area Survey (H-ATLAS), while targeting 85 sources which resolved into 142." (Abstract); "The spectroscopic redshifts span a range $1.41<z<4.53$ with a mean value of 2.75" (Abstract); "| J012407.4$-$281434 | 11 | 1 | | 01:24:07.50 | $-$28:14:34.7 | 2.631 | |" (Table 1)

## Data provenance

- ALMA projects: 2016.2.00133.S, 2018.1.00804.S, 2019.1.01477.S
- bands: Band 3 and Band 4  
  > "This led to observations with the ALMA 12 m Array that covered all 85 fields in Band 4 as well as Band 3 (in programme 2019.1.01477.S) where emission lines were not already obvious." (Sample selection)
- frequencies and spectral setup: ACA Band 3: 5 tunings covering 86.6-115.7 GHz (29.1 GHz bandwidth, 101 GHz central, 7.813 MHz / 20-25 km/s resolution); 12-m Band 3 & 4: 6 tunings (3 per band) covering 89.6-112.6 GHz and 139-162 GHz (23.25 GHz bandwidth each, centred at 101 and 151 GHz)  
  > "The observations of each target consisted of single pointings with a series of 5 spectral tunings set up to cover the sky frequency range between 86.6 and 115.7 GHz (2.59 - 3.46 mm; Fig. 2 top panel)." (ACA observations); "The spectral resolution was set to 7.813 MHz, which is equivalent to a velocity bin of $20-25$ km s$^{-1}$." (ACA observations); "These observations produce near-continuous coverage of 23.25 GHz bandwidth centred at 101 and 151 GHz (89.6$-$112.6 and 139$-$162 GHz)." (12-m Array observations)
- continuum bandwidth: _not stated_
- arrays: ACA (Morita Array) and 12-m Array  
  > "Data were acquired with the ACA (also called the Morita Array) during ALMA Cycles 4 and 6 in programmes 2016.2.00133.S and 2018.1.00804.S (P.I.: S. Serjeant)." (ACA observations); "Data were acquired with the ALMA 12-m Array during ALMA Cycle 7 in programme 2019.1.01477.S (P.I.: S. Urquhart)." (12-m Array observations)
- configurations: C43-1, C43-2, or C43-3 (for 12-m Array)  
  > "Each field was observed in Bands 3 (if it had not been observed with the ACA in this band) and 4 using a single pointing with the 12-m Array in either the C43-1, C43-2, or C43-3 configurations." (12-m Array observations)
- baselines: _not stated_
- angular resolution: ACA Band 3: 17 x 10 arcsec; 12-m Band 3: 3.6 x 2.7 arcsec (~3 arcsec); 12-m Band 4: 2.2 x 1.8 arcsec (~2 arcsec)  
  > "These configuration yielded beams with full width at half-maxima (FWHM) of approximately 3 arcsec in Band 3 and 2 arcsec in Band 4." (12-m Array observations); "| ACA | 3 | 101 | 29.1 | 17 $\times$ 10 | 2.0 | 100 $\times$ 100 | 200 $\times$ 200 |" (Data processing); "| 12-m Array | 3 | 101 | 23.25 | 3.6 $\times$ 2.7 | 0.5 | 240 $\times$ 240 | 120 $\times$ 120 |" (Data processing)
- max recoverable scale: _not stated_
- sensitivity: ACA: 3 mJy per 308 km/s; 12-m Array: 0.8 mJy per 300 km/s  
  > "The sensitivity goals were set to 3 mJy, as measured within a velocity width of 308 km s$^{-1}$, since this was the expected line width of the data; this was typically matched by our observations." (ACA observations); "Based on the results of the ACA campaign described above, we required an RMS of 0.8 mJy for a 300 km s$^{-1}$ line; this was typically matched by our observations." (12-m Array observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI programmes (ACA P.I.: S. Serjeant; 12-m Array P.I.: S. Urquhart)  
  > "Data were acquired with the ACA (also called the Morita Array) during ALMA Cycles 4 and 6 in programmes 2016.2.00133.S and 2018.1.00804.S (P.I.: S. Serjeant)." (ACA observations); "Data were acquired with the ALMA 12-m Array during ALMA Cycle 7 in programme 2019.1.01477.S (P.I.: S. Urquhart)." (12-m Array observations)
- Line: CO (2-1), (3-2), (4-3), (5-4), (6-5), (7-6) (not stated)
- Line: [CI] (3P1-3P0) (492 GHz)
- Line: [CI] (3P2-3P1) (809 GHz)
- Line: H2O 2_11 - 2_02 (not stated)
- Other facility **Herschel Space Observatory (H-ATLAS / SPIRE)**: Target selection catalogue and 250, 350, and 500 um flux densities from H-ATLAS SGP Data Release 2 Catalogue version 1.4  
  > "Our targets are taken from the Herschel Astrophysical Terahertz Large Area Survey (cite: eales2010)." (Sample selection); "For the SGP field, data were taken from H-ATLAS SGP Data Release 2 Catalogue version 1.4 (cite: smith2017; maddox2018; furlanetto2018)." (Redshift determination)
- Other facility **VISTA (VIKING survey)**: Foreground lensing galaxy photometric redshifts derived from VIKING zYJHKs data  
  > "For sources where the data currently exist, we compare our spectroscopic lensed redshift values with those of proposed foreground lensing galaxies taken from (cite: bakx2020), derived from the VISTA Kilo-degree Infrared Galaxy (VIKING) survey (cite: edge2013), a survey in zYJHK$_{\rm S}$ to sub-arcsecond resolution." (Comparison to foreground lens redshifts)
- External data: HerBS sample selection and photometric redshifts  
  > "Our sample selection for this paper is based on the criteria set out in (cite: bakx18):" (Sample selection); "Fig. 4 presents a comparison of the photometric redshifts from previous catalogues in (cite: Bakx2020Erratum) which use an SED fit and the method described in (cite: ivison16) to the spectroscopic measurements presented here" (Spectroscopic versus photometric redshifts) [from (cite: bakx18; Bakx2020Erratum; ivison16)]
- External data: H-ATLAS SGP Data Release 2 Catalogue version 1.4  
  > "For the SGP field, data were taken from H-ATLAS SGP Data Release 2 Catalogue version 1.4 (cite: smith2017; maddox2018; furlanetto2018)." (Redshift determination) [from (cite: smith2017; maddox2018; furlanetto2018)]
- External data: VIKING-derived foreground lens redshifts  
  > "(8) VIKING derived lens redshift from (cite: bakx2020)." (Table 1) [from (cite: bakx2020)]
- External data: Lensed, unlensed, and ULIRG comparison samples of CO redshifts, line widths, and luminosities  
  > "The lensed sample is compiled from (cite: neri2019), (cite: harris2012), (cite: yang2017), (cite: aravena2016) and some well known individual sources." (Redshift and CO line width distributions); "The unlensed sample comes from (cite: bothwell2013), (cite: harris2010) and several well known individual unlensed sources from literature." (Redshift and CO line width distributions); "We use the previously defined “lensed" and “unlensed" samples (Section 4.1) and create an additional sample of ULIRGS. This is composed of data from (cite: solomon1997), (cite: combes2011) and (cite: combes2013)." (The $L^{\prime}_{\rm CO}$ and $\Delta V$ relation) [from (cite: neri2019; harris2012; yang2017; aravena2016; bothwell2013; harris2010; solomon1997; combes2011; combes2013)]
- External data: Median brightness temperature ratios for SMGs used for CO excitation correction  
  > "a correction for excitation was applied using the median brightness temperature ratios for SMGs in Table 4 of (cite: bothwell2013), and accounting for errors." (The $L^{\prime}_{\rm CO}$ and $\Delta V$ relation) [from (cite: bothwell2013)]
- External data: Submillimetre number counts model and angular size data for LensPop simulations  
  > "A mock submillimetre catalogue was created, based on the study by (cite: Cai2013) that allows for an estimate of number counts as a function of the (unlensed) flux at 500 $\upmu\mathrm{m}$ and redshift." (Magnification distribution); "The LensPop model also requires the source galaxy angular size, which we have estimated using data from (cite: Ikarashi2015)." (Magnification distribution) [from (cite: Cai2013; Ikarashi2015)]
- Simulation/model as data: Monte-Carlo simulations of 1000 fake redshift catalogues of 1000 redshifts to optimize ALMA Band 3 and 4 tuning configurations  
  > "We derive this optimised solution using a Monte-Carlo approach, where we generated 1000 fake redshift catalogues of 1000 redshifts, drawn from the previously-mentioned redshift distribution assuming a standard error of $\Delta z/(1+z)=0.13$ (e.g., (cite: pearson13; ivison16))." (12-m Array observations)
- Simulation/model as data: Differential magnification simulations of a z=2.3 background galaxy lensed by a z=0.9 foreground lens with 4 or 100 star-forming clumps/GMCs  
  > "We have repeated the methodology of (cite: serjeant2012) (to which the reader is referred for more details) to run a simulation of a $z=2.3$ background galaxy with a foreground gravitational lens at $z=0.9$." (The effects of differential magnification on luminosities); "In order to quantify the effect of more smoothly distributing the star formation, we performed a new set of simulations with star formation contained in 100 giant molecular clouds, rather than four, again following the methodology of (cite: serjeant2012)." (The effects of differential magnification on luminosities)
- Simulation/model as data: LensPop strong gravitational lensing population simulations adapted for submillimetre galaxies over 10% of the sky  
  > "The model used as the basis for the work presented in this section was described in (cite: COLLETT2015) with its source code available as open source software, and was originally designed to predict strong gravitational lensing of optical galaxies." (Magnification distribution); "A total of 10 per cent of the sky was simulated, to avoid Poisson errors in the models dominating the comparison with the data." (Magnification distribution)

## Processing

### Calibration

- pipeline or manual: 12-m Array data were pipeline-calibrated; ACA data were manually calibrated  
  > "The 12-m Array data were pipeline-calibrated with the Common Astronomy Software Applications (CASA) package version 5.6.1 (cite: mcmullin2007), while the ACA data were manually calibrated with the same version of CASA." (Data processing)
- casa version: 5.6.1  
  > "The 12-m Array data were pipeline-calibrated with the Common Astronomy Software Applications (CASA) package version 5.6.1 (cite: mcmullin2007), while the ACA data were manually calibrated with the same version of CASA." (Data processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars and Solar System objects  
  > "The calibrators were typically quasars, although Solar System objects were used for flux calibration in some observations." (ACA observations)
- flux scale uncertainty: 5 per cent  
  > "The uncertainty in the flux calibration is 5 per cent (cite: remijan2019)." (Data processing)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA version 5.6.1  
  > "Imaging was done with the tclean command within CASA version 5.6.1." (Data processing)
- deconvolver: Hogbom  
  > "All images were created using natural weighting, the standard gridder, and the Hogbom deconvolver." (Data processing)
- weighting robust: natural weighting  
  > "All images were created using natural weighting, the standard gridder, and the Hogbom deconvolver." (Data processing)
- uv taper: _not stated_
- cell size: ACA Band 3: 2.0 arcsec; 12-m Band 3: 0.5 arcsec; 12-m Band 4: 0.3 arcsec  
  > "| ACA | 3 | 101 | 29.1 | 17 $\times$ 10 | 2.0 | 100 $\times$ 100 | 200 $\times$ 200 |" (Data processing); "| 12-m Array | 3 | 101 | 23.25 | 3.6 $\times$ 2.7 | 0.5 | 240 $\times$ 240 | 120 $\times$ 120 |" (Data processing); "| 12-m Array | 4 | 151 | 23.25 | 2.2 $\times$ 1.8 | 0.3 | 240 $\times$ 240 | 72 $\times$ 72 |" (Data processing)
- image size: ACA Band 3: 100 x 100 pixels (200 x 200 arcsec); 12-m Band 3: 240 x 240 pixels (120 x 120 arcsec); 12-m Band 4: 240 x 240 pixels (72 x 72 arcsec)  
  > "| ACA | 3 | 101 | 29.1 | 17 $\times$ 10 | 2.0 | 100 $\times$ 100 | 200 $\times$ 200 |" (Data processing); "| 12-m Array | 3 | 101 | 23.25 | 3.6 $\times$ 2.7 | 0.5 | 240 $\times$ 240 | 120 $\times$ 120 |" (Data processing); "| 12-m Array | 4 | 151 | 23.25 | 2.2 $\times$ 1.8 | 0.3 | 240 $\times$ 240 | 72 $\times$ 72 |" (Data processing)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Lines initially identified in image cube without continuum subtraction; once found, continuum was subtracted from visibility data and re-imaged  
  > "Spectral lines were initially identified in the image cube without continuum subtraction. Once spectral lines were found, the continuum was subtracted from the visibility data, and the data were re-imaged" (Data processing)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ACA Band 3: 17 x 10 arcsec; 12-m Band 3: 3.6 x 2.7 arcsec; 12-m Band 4: 2.2 x 1.8 arcsec  
  > "| ACA | 3 | 101 | 29.1 | 17 $\times$ 10 | 2.0 | 100 $\times$ 100 | 200 $\times$ 200 |" (Data processing); "| 12-m Array | 3 | 101 | 23.25 | 3.6 $\times$ 2.7 | 0.5 | 240 $\times$ 240 | 120 $\times$ 120 |" (Data processing); "| 12-m Array | 4 | 151 | 23.25 | 2.2 $\times$ 1.8 | 0.3 | 240 $\times$ 240 | 72 $\times$ 72 |" (Data processing)
- final rms: _not stated_

### Inherited from earlier work

- Sample selection criteria (500 um flux >= 80 mJy, z_phot >= 2, SGP field, lens selection)  
  > "Our sample selection for this paper is based on the criteria set out in (cite: bakx18):" (Sample selection) [from (cite: bakx18)]
- Gravitational lens selection technique (lack of cross-identification with known blazars or bright local galaxies)  
  > "Lack of cross-identification with known blazars or bright local galaxies (following the gravitational lens selection technique of (cite: negrello2010));" (Sample selection) [from (cite: negrello2010)]
- ALMA spectral tuning optimization and robust single/multi-line redshift determination method  
  > "We based the precise tunings in Bands 3 and 4 on the method detailed in (cite: Bakx2020IRAM), where we optimised the expected number of sources with robust redshifts" (12-m Array observations); "With the precise frequencies of the spectral lines in hand, we calculate all potential redshift solutions for each line, and use the method described in (cite: Bakx2020IRAM) to provide only robust redshifts." (Redshift determination) [from (cite: Bakx2020IRAM)]
- Continuum measurements and individual galaxy source counts in the ALMA fields  
  > "As reported by Bendo et al. in prep, we find 142 individual galaxies in the ALMA images, and here we report the 71 galaxies with spectroscopic redshifts." (Sample selection) [from Bendo et al. in prep.]
- Differential magnification simulation methodology  
  > "We have repeated the methodology of (cite: serjeant2012) (to which the reader is referred for more details) to run a simulation of a $z=2.3$ background galaxy with a foreground gravitational lens at $z=0.9$." (The effects of differential magnification on luminosities) [from (cite: serjeant2012)]
- Strong gravitational lensing population model (LensPop)  
  > "The model used as the basis for the work presented in this section was described in (cite: COLLETT2015) with its source code available as open source software, and was originally designed to predict strong gravitational lensing of optical galaxies." (Magnification distribution) [from (cite: COLLETT2015)]

### Not stated but needed to reproduce (our reading)

- Exact circular aperture radii used for each source during line extraction
- Exact frequency channel ranges selected for continuum subtraction and line flux integration per source
- Final re-imaged channel widths per cube after manual adjustment
- Stopping criteria / threshold and masking settings in CASA tclean
- Exact parameters (slope and intercept) of the linear fit to the unlensed L'_CO vs FWHM relation used to compute the magnification factors in Table 2

## Analysis recipe

1. **Calibrate and image ALMA visibilities, subtract continuum, and re-image cubes**: Pipeline/manual calibration in CASA 5.6.1, initial imaging with tclean using natural weighting and Hogbom deconvolver, visual identification of spectral lines, visibility continuum subtraction, and re-imaging with manually adjusted channel widths.  
  > "The 12-m Array data were pipeline-calibrated with the Common Astronomy Software Applications (CASA) package version 5.6.1 (cite: mcmullin2007), while the ACA data were manually calibrated with the same version of CASA." (Data processing); "All images were created using natural weighting, the standard gridder, and the Hogbom deconvolver." (Data processing); "Once spectral lines were found, the continuum was subtracted from the visibility data, and the data were re-imaged with manual adjustments made to the channel width in the final image cubes" (Data processing)
   - software: CASA, tclean
   - parameter: natural weighting, standard gridder, Hogbom deconvolver, pixel scale 2.0/0.5/0.3 arcsec, image size 100x100/240x240 pixels  
  > "All images were created using natural weighting, the standard gridder, and the Hogbom deconvolver." (Data processing)
   - assumption: 5 per cent flux calibration uncertainty  
  > "The uncertainty in the flux calibration is 5 per cent (cite: remijan2019)." (Data processing)
   - fitting: _not stated_
   - validation: Visual inspection of data and optimizing SNR in both image slices and extracted spectrum  
  > "the data were re-imaged with manual adjustments made to the channel width in the final image cubes to optimize the balance between the sampling of the spectral line emission and the signal-to-noise ratio" (Data processing)
2. **Extract spectral line fluxes and line widths**: Aperture photometry within the image cubes using circular apertures centered on continuum peaks, with manually adjusted aperture radii and frequency channels to maximize flux while keeping detection above 5 sigma.  
  > "Line measurements were made using aperture photometry within the image cubes." (Line extraction); "Circular apertures were centered on the peaks of the corresponding continuum emission, and the radii of the apertures were manually adjusted for each source in each image to include as much line emission as possible while still measuring that emission at higher than the 5$\sigma$ level." (Line extraction); "Similarly, we manually selected frequency channels that measured as much of the line flux as possible without diluting the signal with background noise so much that the measurements fall below 5$\sigma$." (Line extraction)
   - parameter: Detection threshold > 5 sigma  
  > "include as much line emission as possible while still measuring that emission at higher than the 5$\sigma$ level." (Line extraction)
   - fitting: _not stated_
   - validation: Lines were first identified by visual inspection independently by several authors  
  > "Lines were first identified by visual inspection of the data independently by several of the authors, and then confirmed through the following process." (Line extraction)
3. **Determine spectroscopic redshifts**: Calculate all potential redshift solutions from detected line frequencies and use multi-line detections (59 sources) or single-line exclusion of alternative solutions where other lines would have been detected (13 sources) following Bakx et al. (2020).  
  > "With the precise frequencies of the spectral lines in hand, we calculate all potential redshift solutions for each line, and use the method described in (cite: Bakx2020IRAM) to provide only robust redshifts." (Redshift determination); "In total, we find redshifts for 59 sources using multiple spectral lines that point to an unambiguous redshift solution." (Redshift determination); "For thirteen sources, we find bright emission from only a single line. In these specific cases (HerBS-22, -39, -40, -60, -73, -80B, -81A, -103, -122A, -146B, -155 and -207, -208B), we are able to exclude all other redshift solutions." (Redshift determination)
   - parameter: Spectroscopic redshift uncertainty < 0.001  
  > "We note that the uncertainty of the spectroscopic redshifts is less than 0.001, however for clarity, we show only three trailing digits in Table 1." (Redshift determination)
   - assumption: Adjacent CO spectral lines typically have similar integrated line fluxes, allowing exclusion of redshift solutions for strong single-line detections  
  > "Since adjacent CO spectral lines typically have similar integrated line fluxes, we can only exclude redshift solutions for galaxies with strong line detections in CO lines." (Redshift determination)
   - fitting: _not stated_
   - validation: Comparison against submm photometric redshifts and foreground VIKING lens redshifts  
  > "Fig. 4 presents a comparison of the photometric redshifts from previous catalogues in (cite: Bakx2020Erratum) which use an SED fit and the method described in (cite: ivison16) to the spectroscopic measurements presented here" (Spectroscopic versus photometric redshifts); "Table 1 gives the probable lens redshifts applicable here and, as expected, they all have lower photometric redshifts than the sources we present." (Comparison to foreground lens redshifts)
4. **Derive apparent CO(1-0) luminosities and lensing magnification factors**: Calculate apparent CO luminosities from the lowest available CO transition using Equation 3 of Solomon & Vanden Bout (2005), convert to CO(1-0) using median SMG brightness temperature ratios from Bothwell et al. (2013), and infer magnification factors from the vertical offset relative to a fit to the unlensed L'_CO(1-0) vs FWHM relation.  
  > "We derived CO brightness estimates via equation 3 of (cite: solomon2005):" (Redshift and CO line width distributions); "a correction for excitation was applied using the median brightness temperature ratios for SMGs in Table 4 of (cite: bothwell2013), and accounting for errors. We calculate the CO(1$-$0) luminosity from the lowest CO transition available." (The $L^{\prime}_{\rm CO}$ and $\Delta V$ relation); "The magnifications from the offset from our fit to the unlensed samples are listed in Table 2." (Magnification distribution)
   - assumption: Spatially flat LambdaCDM cosmology with H0 = 67.4 km s^-1 Mpc^-1 and Omega_M = 0.315  
  > "We adopt a spatially flat $\Lambda$CDM cosmology throughout this paper with $H_{0}=67.4$ km s$^{-1}$ Mpc$^{-1}$ and $\Omega_{\rm M}=0.315$ (cite: Planck2018parameters)." (Introduction)
   - assumption: Median SMG brightness temperature ratios from Table 4 of Bothwell et al. (2013) apply for excitation correction  
  > "a correction for excitation was applied using the median brightness temperature ratios for SMGs in Table 4 of (cite: bothwell2013), and accounting for errors." (The $L^{\prime}_{\rm CO}$ and $\Delta V$ relation)
   - assumption: Gravitational magnification depends only on lensing geometry and is independent of velocity width  
  > "The vertical offset of lensed sources in Fig. 6 is due to gravitational magnification, which in turn depends only on the lensing geometry and is therefore formally independent of velocity width $\Delta V$." (Magnification distribution)
   - fitting: Fit to unlensed samples in the L'_CO vs Delta V plane  
  > "The magnifications from the offset from our fit to the unlensed samples are listed in Table 2." (Magnification distribution)
   - validation: Differential magnification simulations following Serjeant (2012) show negligible (+/- 3.5% to +/- 20%) effect on CO luminosities  
  > "In order to quantify the effect of more smoothly distributing the star formation, we performed a new set of simulations with star formation contained in 100 giant molecular clouds, rather than four, again following the methodology of (cite: serjeant2012). This is shown as the red curve in Fig. 7, and is a $\pm3.5\%$ effect." (The effects of differential magnification on luminosities)
5. **Compare inferred magnification distribution with galaxy-galaxy strong lensing population models**: Adapt the LensPop code (Collett 2015) with a mock submillimetre source catalogue based on Cai et al. (2013) and source sizes from Ikarashi et al. (2015), simulate 10% of the sky for S_500 > 80 mJy and z_source > 2, and compare the cumulative magnification distribution against the CO-inferred magnifications.  
  > "The model used as the basis for the work presented in this section was described in (cite: COLLETT2015) with its source code available as open source software" (Magnification distribution); "A mock submillimetre catalogue was created, based on the study by (cite: Cai2013) that allows for an estimate of number counts as a function of the (unlensed) flux at 500 $\upmu\mathrm{m}$ and redshift." (Magnification distribution); "A further simulation of $10\%$ of the sky was undertaken, from which a HERBS-like subset of source redshift $z_{\mathrm{source}}>2$ was selected." (Magnification distribution)
   - software: LensPop
   - parameter: Source density 0.011 arcsec^-2, z > 1 (and z_source > 2 subset), S_500 > 80 mJy and 100 mJy, 10% sky area  
  > "The source density parameter was calculated from the data in (cite: Cai2013) to be 0.011 arcsec$^{-2}$." (Magnification distribution); "A total of 10 per cent of the sky was simulated, to avoid Poisson errors in the models dominating the comparison with the data." (Magnification distribution)
   - assumption: Strong lensing by elliptical galaxies modelled as singular isothermal ellipsoids (SIEs) with source lying within the Einstein radius  
  > "The model assumes strong lensing by elliptical galaxies, modelled as singular isothermal ellipsoids (SIEs)." (Magnification distribution); "For simplicity, we have used only submillimetre galaxies at $z > 1$, and require that the background source lies within the Einstein radius in order for strong lensing to be possible." (Magnification distribution)
   - fitting: _not stated_
   - validation: Tested robustness by including a 100 mJy flux limit prediction and comparing against Bussmann et al. (2013) and Reuter et al. (2020) samples  
  > "The flux density limit of $80$ mJy applies to the targets in this paper, but we have included a $100$ mJy prediction to demonstrate robustness to the precise choice of flux limit." (Magnification distribution)

## Software

- **CASA** 5.6.1: Pipeline calibration of 12-m Array data, manual calibration of ACA data, and imaging with tclean  
  > "The 12-m Array data were pipeline-calibrated with the Common Astronomy Software Applications (CASA) package version 5.6.1 (cite: mcmullin2007), while the ACA data were manually calibrated with the same version of CASA." (Data processing); "Imaging was done with the tclean command within CASA version 5.6.1." (Data processing)
- **tclean** 5.6.1: Imaging ACA and 12-m Array visibility data  
  > "Imaging was done with the tclean command within CASA version 5.6.1." (Data processing)
- **LensPop** : Simulating the strong gravitational lensing magnification distribution of submillimetre galaxies  
  > "The model used as the basis for the work presented in this section was described in (cite: COLLETT2015) with its source code available as open source software" (Magnification distribution); "The LensPop model also requires the source galaxy angular size, which we have estimated using data from (cite: Ikarashi2015)." (Magnification distribution)
- **Astropy** : General astronomy calculations in Python  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy2013; astropy2018)." (Acknowledgements)
- **Numpy** : Data analysis  
  > "Data analysis made use of the Python package Numpy (cite: harris2020array)." (Acknowledgements)
- **Matplotlib** : Making figures  
  > "Some figures were made with the Python package Matplotlib (cite: Hunter:2007)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of galaxies with robust spectroscopic redshifts | 71 | not stated | dimensionless | 3 | We present spectroscopic measurements for 71 galaxies associated with 62 of the brightest high-redshift submillimeter sources from the Southern fields of the Herschel Astrophysical Terahertz Large Area Survey (H-ATLAS), while targeting 85 sources which resolved into 142. |
| Number of Herschel fields with robust redshifts | 62 | not stated | dimensionless | 3 | We find spectroscopic redshifts for one or multiple sources in 62 of the 85 Herschel fields. |
| Redshift identification success rate (overall) | 73 | not stated | per cent | 3 | We have obtained robust redshift measurements for all sources using the 12-m Array and an efficient tuning of ALMA to optimise its use as a redshift hunter, with 73 per cent of the sources having a robust redshift identification. |
| Spectroscopic redshift range | 1.41 to 4.53 | < 0.001 | dimensionless | 3 | The spectroscopic redshifts span a range $1.41<z<4.53$ with a mean value of 2.75; We note that the uncertainty of the spectroscopic redshifts is less than 0.001, however for clarity, we show only three trailing digits in Table 1. |
| Mean spectroscopic redshift | 2.75 | not stated | dimensionless | 3 | The redshift distribution of our sample has a mean redshift of 2.75 and median redshift of 2.61, with all sources lying within the redshift range $1.41< z< 4.52$. |
| Median spectroscopic redshift | 2.61 | not stated | dimensionless | 3 | The redshift distribution of our sample has a mean redshift of 2.75 and median redshift of 2.61, with all sources lying within the redshift range $1.41< z< 4.52$. |
| CO emission line FWHM range | 110 to 1290 | not stated | km s^-1 | 2 | the CO emission line full-width at half-maxima range between $\rm 110\,km\,s^{-1} < FWHM < 1290\,km\,s^{-1}$ with a mean value of $\sim$500 km s$^{-1}$, in line with other high-$z$ samples. |
| Mean CO line width (FWHM) | 494 | not stated | km s^-1 | 2 | We find a median width of 475 km s$^{-1}$ and a mean of 494 km s$^{-1}$, which lies below both the values of the lensed and unlensed samples reported |
| Median CO line width (FWHM) | 475 | not stated | km s^-1 | 2 | We find a median width of 475 km s$^{-1}$ and a mean of 494 km s$^{-1}$, which lies below both the values of the lensed and unlensed samples reported |
| Photometric redshift standard deviation sigma(Delta z_Bakx / (1 + z_spec)) | 0.14 | not stated | dimensionless | 3 | The standard deviations are $\sigma(\Delta z_{\rm Bakx} / (1+z_{\rm spec}))=0.14$ and $\sigma(\Delta z_{\rm Ivison} / (1+z_{\rm spec}))=0.13$. |
| Photometric redshift standard deviation sigma(Delta z_Ivison / (1 + z_spec)) | 0.13 | not stated | dimensionless | 3 | The standard deviations are $\sigma(\Delta z_{\rm Bakx} / (1+z_{\rm spec}))=0.14$ and $\sigma(\Delta z_{\rm Ivison} / (1+z_{\rm spec}))=0.13$. |
| Simulated differential magnification spread (100 GMCs model) | 3.5 | not stated | per cent | 4 | This is shown as the red curve in Fig. 7, and is a $\pm3.5\%$ effect. |
| HerBS-11 spectroscopic redshift | 2.631 | < 0.001 | dimensionless | 3 | / J012407.4$-$281434 / 11 / 1 / / 01:24:07.50 / $-$28:14:34.7 / 2.631 / / |
| HerBS-11 apparent CO(1-0) luminosity (mu L'_CO(1-0)) | 78.1 | 8.8 | 10^10 K km s^-1 pc^2 | 4 | / J012407.4$-$281434 / 11 / 410 $\pm$ 80 / 78.1 $\pm$ 8.8 / 18.4 $\pm$ 2.1 / |
| HerBS-11 magnification factor (mu) | 18.4 | 2.1 | dimensionless | 4 | / J012407.4$-$281434 / 11 / 410 $\pm$ 80 / 78.1 $\pm$ 8.8 / 18.4 $\pm$ 2.1 / |

## Qualitative findings

- All sources with available foreground VIKING lens redshifts lie at higher spectroscopic redshifts than their proposed foreground lenses.  
  > "Table 1 gives the probable lens redshifts applicable here and, as expected, they all have lower photometric redshifts than the sources we present." (Comparison to foreground lens redshifts)
- Differential magnification effects on CO line luminosities are negligible (+/- 3.5% for 100 GMCs, or +/- 20% in the pessimistic 4-clump model) compared to random errors.  
  > "In summary, the worst case is that the differential magnification effects are comparable to or smaller than the random errors, while in more realistic up-to-date models the effects in this case are negligible." (The effects of differential magnification on luminosities)
- The inferred magnification distribution agrees well with galaxy-galaxy strong lensing models (LensPop) for mu < 10, with hints of an excess at higher magnifications potentially due to group/cluster lensing, Eddington-like bias, or differential magnification of line widths.  
  > "The observed magnification distribution is consistent with galaxy-galaxy strong lensing models at magnifications $<10$, but there are hints of an excess at higher magnifications." (Conclusions)

## Claim tuples

- H: Optimised stacked ALMA tunings in Bands 3 and 4 can efficiently measure robust spectroscopic redshifts for bright Herschel-selected submillimetre galaxies. | E: Observed 85 H-ATLAS SGP fields with ALMA 12-m Array in Bands 3 and 4 (3 tunings per band) and ACA in Band 3, and applied multi-line identification and single-line exclusion. | R: Obtained robust spectroscopic redshifts for 71 galaxies across 62 of the 85 Herschel fields (73 per cent overall; 75 per cent for sources with 12-m Band 3 and 4 coverage), spanning 1.41 < z < 4.53. | F: The ALMA Band 3+4 tuning strategy is a highly efficient redshift hunter, though the 75% success rate is slightly below the 90% predicted by Monte Carlo simulations due to source multiplicity and faint lines. | **supported**
- H: The bright H-ATLAS sources selected with S_500 >= 80 mJy and z_phot >= 2 are strongly gravitationally lensed. | E: Derived apparent CO(1-0) luminosities from the lowest detected CO transition and compared them against CO line FWHM alongside lensed and unlensed comparison samples. | R: The derived CO(1-0) luminosities are significantly elevated relative to the unlensed line-width to CO(1-0) luminosity scaling relation, and all sources with VIKING lens candidates lie behind the foreground lens redshifts. | F: The sample is predominantly strongly gravitationally lensed, clearly separated from unlensed SMGs in the L'_CO(1-0) vs FWHM diagram. | **supported**
- H: Differential magnification across resolved background sources does not significantly bias the integrated CO line luminosities. | E: Simulated a z=2.3 background galaxy lensed by a z=0.9 foreground lens following Serjeant (2012) using both a 4-clump model and a smoother 100-GMC model. | R: The 1-sigma spread in differential magnification is +/- 20% for the pessimistic 4-clump model and +/- 3.5% for the 100-GMC model. | F: Differential magnification effects on CO luminosities are comparable to or much smaller than the random errors and can be neglected. | **supported**
- H: The distribution of magnification factors inferred from the L'_CO vs FWHM relation matches predictions from galaxy-galaxy strong lensing models. | E: Compared magnification factors estimated from the vertical offset in the L'_CO(1-0) vs FWHM plane with mock submm lensing catalogues generated using the LensPop SIE galaxy-galaxy lensing code. | R: The observed magnification distribution agrees well with the HERBS-like LensPop model up to mu ~ 10, but shows a hint of an excess at higher magnifications. | F: Galaxy-galaxy strong lensing accounts for the magnification distribution up to mu ~ 10, while the high-magnification excess may arise from group/cluster lensing, Eddington-like bias from magnification uncertainties, or differential magnification of line widths. | **partially**

## Reasoning

- Why this data: Submillimetre CO spectroscopy is unobscured by dust extinction, and combining 3 stacked tunings each in ALMA Bands 3 and 4 maximizes continuous frequency coverage, shrinks the z~2 redshift desert, and increases expected robust redshift detections from 12% to 90% for only 20% extra observing time.  
  > "However, redshifted carbon monoxide (CO) emission lines are observable with sub-millimetre and millimetre-wave spectroscopy. These emission lines are unobscured by dust exinction and are directly attributable to the sub/mm sources." (Introduction); "In total, this statistical exercise raised the probability for detecting robust redshifts (both by multiple spectral line, and by inference) from 12 per cent to 90 per cent while only requiring 20 per cent extra observation time for the additional band 4 tuning." (12-m Array observations)
- Why this method: Manual aperture adjustments per source maximize line flux above 5 sigma without adding noisy pixels from larger continuum apertures; single-line redshift exclusion leverages the continuous Band 3+4 coverage to rule out alternative redshifts that would have produced a second detected line.  
  > "If we matched the apertures used to measure the continuum and line emission, we would either need to choose large apertures that included all of the detectable continuum emission but also included extra noisy pixels for the line emission or small apertures that optimize the line detections but do not include all of the continuum emission." (Line extraction); "In other words, if we would have detected two spectral lines within our covered bandwidth for every redshift solution except one, we can identify the redshift robustly from a single bright detected spectral line." (12-m Array observations)
- Alternative: 5-tuning Band 3-only spectral scan (as used in Weiss et al. 2013 and initial ACA observations) was replaced by 3 tunings in Band 3 + 3 tunings in Band 4 because Band 3-only had inefficient sideband overlap and only yielded ~12% multi-line detections (for z > 3.5).  
  > "The typical ALMA tuning used in studies such as (cite: weiss2013) and our earlier ACA data — to essentially fully cover Band 3, as in the top panel of Figure 2 — was found to be particularly good at detecting at least one spectral line (an expected 87 per cent across our sample). However, this approach is rather inefficient given the large overlap between the upper sidebands of the lower-frequency tunings and lower sidebands of the higher-frequency tunings." (12-m Array observations)
- Alternative: Matched continuum and line apertures were rejected because continuum is detected at higher S/N and matching apertures would either add noise to the line measurement or miss continuum flux.  
  > "If we matched the apertures used to measure the continuum and line emission, we would either need to choose large apertures that included all of the detectable continuum emission but also included extra noisy pixels for the line emission or small apertures that optimize the line detections but do not include all of the continuum emission." (Line extraction)
- How they decided it was enough: Required > 5 sigma line detections for robust redshifts; stopped requesting Cycle 6 ACA tunings once line emission was detected in Cycle 4; simulated 10% of the sky in LensPop so Poisson errors would not dominate.  
  > "For some targets, however, line emission was detected using the limited Cycle 4 data that were acquired. For these sources, we did not request any additional Cycle 6 observations to complete the coverage of the 86.6 to 115.7 GHz range." (ACA observations); "the radii of the apertures were manually adjusted for each source in each image to include as much line emission as possible while still measuring that emission at higher than the 5$\sigma$ level." (Line extraction); "A total of 10 per cent of the sky was simulated, to avoid Poisson errors in the models dominating the comparison with the data." (Magnification distribution)
- Limitation (authors): At 2-3 arcsec resolution, most detected targets are unresolved point sources and multiple images in galaxy-galaxy lensing systems cannot be resolved.  
  > "however, most of the detected targets will be unresolved point sources." (12-m Array observations); "Multiple images in galaxy-galaxy gravitational lensing systems would not be resolved in our ALMA data, since for source redshifts $\gg$ lens redshifts, the critical radius in a Singular Isothermal Sphere lens asymptotes to $\sim1.5^{\prime\prime}\times(\sigma_{\rm v}/230$ km s$^{-1})^2$ where $\sigma_{\rm v}$ is the lens velocity dispersion." (Redshift determination)
- Limitation (authors): Some individually resolved components could be multiple lensed images of the same galaxy system lensed by foreground clusters rather than separate galaxies.  
  > "However, it is possible that a small fraction are multiple images of the same galaxy system lensed by foreground cluster lenses." (Redshift determination)
- Limitation (authors): 23 Herschel sources lack robust redshifts due to no lines (5), single lines too faint for exclusion (7), sub-5-sigma secondary lines (9), or ambiguous single lines (7).  
  > "We were unable to identify the redshifts for 23 Herschel sources with the ALMA 12m-Array data." (Sources without robust redshifts)
- Limitation (authors): Magnification estimates from the L'_CO vs FWHM relation have large uncertainties, do not account for inclination or dynamical state, and only propagate luminosity uncertainties in Table 2.  
  > "One possibility is that uncertainties in the magnification cause an Eddington-like bias in the magnification distribution in Fig. 8, and indeed (cite: aravena2016) find that these magnification estimates can have large uncertainties" (Magnification distribution); "Magnification uncertainties are calculated using only the uncertainties in luminosity." (Table 2)
- Limitation (authors): The LensPop model only considers galaxy-galaxy lensing by SIEs and does not include galaxy group/cluster lensing or internal CO velocity and luminosity distributions.  
  > "This model only considers galaxy-galaxy lensing, and has no contribution from strong lensing by galaxy clusters." (Magnification distribution); "The statistical effects on the population discussed above are incorporated in our LensPop simulations, though we consider only galaxy-galaxy lensing and do not consider the CO velocity and luminosity distributions within galaxies." (Magnification distribution)
- Caveat (inferred, ours): Manual adjustment of circular aperture radii and frequency channel ranges to stay above 5 sigma can introduce selection/confirmation bias in measured line fluxes and widths.
- Caveat (inferred, ours): Magnification uncertainties in Table 2 neglect the large scatter in the unlensed L'_CO vs FWHM scaling relation, line width measurement errors, inclination angle effects, and CO excitation ratio scatter.
- Caveat (inferred, ours): Single-line redshift identifications (13 sources) rely on assumed CO SLED excitation ratios to rule out uninhibited second lines, which could fail for galaxies with anomalous CO excitation.

## Reproducibility

- Data public (paper): Herschel SPIRE data available at https://www.h-atlas.org; reduced and calibrated science-ready ALMA data available on the ALMA Science Archive at https://almascience.eso.org/asax/ under 2016.2.00133.S, 2018.1.00804.S, and 2019.1.01477.S.  
  > "The Herschel SPIRE data can be downloaded at https://www.h-atlas.org , while reduced and calibrated science-ready ALMA data is available on the ALMA Science Archive at https://almascience.eso.org/asax/ . This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.2.00133.S, 2018.1.00804.S, and 2019.1.01477.S." (Data Availability)
- Products in archive: Reduced and calibrated science-ready ALMA data available on the ALMA Science Archive  
  > "while reduced and calibrated science-ready ALMA data is available on the ALMA Science Archive at https://almascience.eso.org/asax/ ." (Data Availability)
- Code: LensPop open-source software available at https://github.com/tcollett/LensPop (from Collett 2015)  
  > "The model used as the basis for the work presented in this section was described in (cite: COLLETT2015) with its source code available as open source software" (Magnification distribution)
- Missing: Per-source aperture radii and frequency channel intervals used to extract line fluxes
- Missing: Final channel widths of the continuum-subtracted image cubes for each source
- Missing: Exact fitted equation for the unlensed L'_CO(1-0) vs FWHM relation used to compute the magnification factor mu in Table 2
- Missing: Modified LensPop script/catalogue files implementing the Cai et al. (2013) submm source counts
- Data volume (inferred): Moderate (~100-500 GB): 85 fields observed in short integrations across 5-6 spectral tunings in Bands 3 and 4 with compact 12-m configurations (240x240 pixel cubes) and ACA (100x100 pixel cubes).
- Score (inferred): 78/5, ALMA project codes, CASA version, imaging grid/beam/pixel parameters, and full per-source result tables (coordinates, redshifts, line fluxes, FWHMs, luminosities, magnifications) are clearly provided, and data are public; however, manual per-source aperture sizes, channel ranges, and the exact unlensed scaling relation fit coefficients are not explicitly tabulated.
- Rediscovery candidate: yes, Public archival ALMA data for a well-defined sample of 85 fields with complete answer keys (Table 1, Table A1, Table 2) for spectroscopic redshifts, line fluxes, FWHMs, and CO luminosities.

## Links

- Method: (cite: Bakx2020IRAM) (Method for optimizing ALMA spectral tunings and determining robust redshifts from multiple or single spectral lines)
- Method: (cite: solomon2005) (Standard equation (Eq. 3) used to calculate CO line luminosities L'_CO)
- Method: (cite: bothwell2013) (Median SMG CO brightness temperature ratios (Table 4) used for excitation correction to CO(1-0))
- Method: (cite: serjeant2012) (Simulation methodology for quantifying differential magnification effects)
- Method: (cite: COLLETT2015) (LensPop strong gravitational lensing population code adapted for submm magnification distribution modelling)
- Companion: Bendo et al. in prep. (BEARS Paper II presenting continuum measurements, source multiplicities, and spectral energy distribution analyses)
- Companion: Hagimoto et al. in prep. (BEARS Paper III presenting line upper limits, inferences from the CO ladder, and the composite spectrum)
- Companion: Bakx et al. in prep. (Dedicated discussion of the statistical single/multi-line redshift identification method)
- Related: BEARS (Bright Extragalactic ALMA Redshift Survey)
- Related: H-ATLAS (Herschel Astrophysical Terahertz Large Area Survey)
- Related: HerBS (Herschel Bright Sources)
- Related: VIKING (VISTA Kilo-degree Infrared Galaxy survey)
- Related: z-GAL

## Checks

```json
{
 "quotes": 170,
 "quotes_ok": 170,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 10,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 82,
  "rate": 0.804
 },
 "evidence_ok": true
}
```
