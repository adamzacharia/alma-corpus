# Is this an early stage merger? A case study on molecular gas and star formation properties of Arp 240

`2020MNRAS.496.5243H` | Monthly Notices of the Royal Astronomical Society 2020 | first author: He, Hao | arXiv: 2006.12523 | DOI: 10.1093/mnras/staa1826

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Is Arp 240 (NGC 5257/5258) really an early-stage merger? Measure its resolved CO gas properties, CO-to-H2 conversion factor and star formation efficiency to constrain the merger stage and the SFE per free-fall time.  
  > "however, we find that this system has a lower global gas fraction but a higher star formation efficiency compared to typical close galaxy pairs, which suggests that this system may already be in an advanced merger stage." (abstract)
- Target **NGC 5257**: coordinates RA = 13h39m52.91s, Dec = +00'24.5'' (as printed in Table 1; HyperLEDA)  
  > "Coordinates (J2000) $^a$ | RA$=13^h39^m52.91^s$ | RA$=13^h39^m57.70^s$" (Table 1); "Redshift $^b$ | 0.022676 | 0.022539" (Table 1); "Luminosity Distance (Mpc) | 98.0 | 97.4 | 1" (Table 1); z/distance z = 0.022676; luminosity distance 98.0 Mpc  
  > "Coordinates (J2000) $^a$ | RA$=13^h39^m52.91^s$ | RA$=13^h39^m57.70^s$" (Table 1); "Redshift $^b$ | 0.022676 | 0.022539" (Table 1); "Luminosity Distance (Mpc) | 98.0 | 97.4 | 1" (Table 1); distance from Table 1 reference (1) = Mould_2000  
  > "Coordinates (J2000) $^a$ | RA$=13^h39^m52.91^s$ | RA$=13^h39^m57.70^s$" (Table 1); "Redshift $^b$ | 0.022676 | 0.022539" (Table 1); "Luminosity Distance (Mpc) | 98.0 | 97.4 | 1" (Table 1)
- Target **NGC 5258**: coordinates RA = 13h39m57.70s, Dec = +00'51.1'' (as printed in Table 1; HyperLEDA)  
  > "Coordinates (J2000) $^a$ | RA$=13^h39^m52.91^s$ | RA$=13^h39^m57.70^s$" (Table 1); "Redshift $^b$ | 0.022676 | 0.022539" (Table 1); "Luminosity Distance (Mpc) | 98.0 | 97.4 | 1" (Table 1); z/distance z = 0.022539; luminosity distance 97.4 Mpc  
  > "Coordinates (J2000) $^a$ | RA$=13^h39^m52.91^s$ | RA$=13^h39^m57.70^s$" (Table 1); "Redshift $^b$ | 0.022676 | 0.022539" (Table 1); "Luminosity Distance (Mpc) | 98.0 | 97.4 | 1" (Table 1); distance from Table 1 reference (1) = Mould_2000  
  > "Coordinates (J2000) $^a$ | RA$=13^h39^m52.91^s$ | RA$=13^h39^m57.70^s$" (Table 1); "Redshift $^b$ | 0.022676 | 0.022539" (Table 1); "Luminosity Distance (Mpc) | 98.0 | 97.4 | 1" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00804.S
- bands: Band 3 (12CO 1-0 at 112 GHz, 13CO 1-0 at 108 GHz) and Band 6 (12CO 2-1 at 223 GHz); single pointings in Band 3, Band 6 mosaics of 4 pointings (NGC 5257) and 9 pointings (NGC 5258)  
  > "Band 3 covers $^{12}$CO $J$=1-0 (112 GHz) and $^{13}$CO $J$=1-0 (108 GHz) and Band 6 covers $^{12}$CO $J$=2-1 (223 GHz)." (2.1 ALMA Data); "Single pointings were used for the Band 3 data. For the Band 6 data, four pointings were used for NGC 5257 while 9 pointings were used for NGC 5258." (2.1 ALMA Data)
- frequencies and spectral setup: Usable bandwidth per spectral window 1875 MHz (12m) and 2000 MHz (7m); channel width 1.953 MHz; CN 1-0 (111 GHz) and CS 2-1 (95.8 GHz) also detected in Band 3  
  > "The total usable bandwidth for each of the spectral windows was 1875 MHz for the 12m array and 2000 MHz for the 7m array. The width of a single channel is 1.953 MHz." (2.1 ALMA Data); "We also detected CN $J$=1-0 (111 GHz) and CS $J$=2-1 (95.8 GHz) in Band 3." (2.1 ALMA Data)
- continuum bandwidth: _not stated_
- arrays: 12m+7m for 12CO 1-0 and 12CO 2-1; 12m only for 13CO 1-0  
  > "$1.6$ | 2.0 $\times$ 1.6 | 12m+7m array | 10 | 112.73" (Table 1); "$3.0$ | 1.0 $\times$ 0.5 | 12m+7m array | 10 | 225.46" (Table 1); "$0.64$ | 2.1 $\times$ 1.6 | 12m array | 20 | 107.78" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 about 2 arcsec (1 kpc); Band 6 about 1 arcsec (0.5 kpc); native beams 2.0x1.6 (12CO 1-0), 1.0x0.5 (12CO 2-1), 2.1x1.6 (13CO 1-0) arcsec  
  > "The resolution of Band 3 is about 2 arcsec (1 kpc) while the resolution of Band 6 is about 1 arcsec (0.5 kpc)." (2.1 ALMA Data)
- max recoverable scale: largest angular scale about 32 arcsec after the 6 klambda inner uv cut  
  > "After cutting the uvrange, the largest angular scale (LAS) is about 32 arcsec." (2.1 ALMA Data)
- sensitivity: RMS noise 1.6 (12CO 1-0), 3.0 (12CO 2-1), 0.64 (13CO 1-0) mJy/beam at 10, 10, 20 km/s channels  
  > "$1.6$ | 2.0 $\times$ 1.6 | 12m+7m array | 10 | 112.73" (Table 1); "$3.0$ | 1.0 $\times$ 0.5 | 12m+7m array | 10 | 225.46" (Table 1); "$0.64$ | 2.1 $\times$ 1.6 | 12m array | 20 | 107.78" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: project 2015.1.00804.S, PI Kazimierz Sliwa (data used as obtained by another PI)  
  > "The data for Arp 240 was acquired from project 2015.1.00804.S (PI: Kazimierz Sliwa)." (2.1 ALMA Data)
- Line: 12CO J=1-0 (112 GHz (as stated for the band; rest frequency not given))
- Line: 13CO J=1-0 (108 GHz (as stated for the band; rest frequency not given))
- Line: 12CO J=2-1 (223 GHz (as stated for the band; rest frequency not given))
- Line: CN J=1-0 (111 GHz)
- Line: CS J=2-1 (95.8 GHz)
- Line: 12CO J=3-2 (SMA, not ALMA) (not stated)
- Other facility **SMA**: 12CO J=3-2 map (beam 3.79 x 2.8 arcsec), compact configuration, used with ALMA lines for RADEX  
  > "The $^{12}$CO $J$=3-2 map has a beam size of 3.79$''$ $\times$ 2.8$''$." (2.2 SMA Data); "The data processing is described in (cite: Wilson_2008)." (2.2 SMA Data)
- Other facility **VLA**: 33 GHz continuum (about 0.5 arcsec resolution) used as the SFR tracer  
  > "Arp 240 was observed with the VLA in 33 GHz continuum." (2.5 Radio Continuum); "The resolution of the data is about 0.5 arcsec" (2.5 Radio Continuum)
- Other facility **Spitzer**: 3.6 and 4.5 micron images (project 70038, PI Sanders) for stellar mass; 24 micron map for SFR/L_TIR  
  > "3.6 μm and 4.5 μm data is from project 70038 (PI:Sanders) with a resolution of roughly 2 arcsec." (2.3 Infrared Data); "the 33 GHz continuum map from the Very Large Array (VLA) to trace the SFR." (2 Observations and Data Reduction)
- Other facility **Herschel**: 70 micron map, used with Spitzer 24 micron for L_TIR / SFR tracing  
  > "Space Telescope, the 70 μm map from the" (2 Observations and Data Reduction)
- External data: 33 GHz VLA continuum data of Arp 240  
  > "The detailed description of the data is in (cite: Linden_2019)." (2.5 Radio Continuum) [from (cite: Linden_2019)]
- External data: SMA 12CO J=3-2 and 2-1 observations and their processing  
  > "The data processing is described in (cite: Wilson_2008)." (2.2 SMA Data) [from (cite: Wilson_2008)]
- External data: Young massive cluster catalogue (age < 10 Myr, mass > 1e6 Msun) used for YMC identification  
  > "We selected these young star clusters from (cite: Linden_2017) with age smaller than 10 Myr and mass greater than" (3.3 Star Formation Rates) [from (cite: Linden_2017)]
- External data: Petrosian radii 17.53 and 24.86 arcsec for NGC 5257 and NGC 5258  
  > "from the SDSS DR12 catalog[^4]" (3.1 Gas Mass) [from SDSS DR12 catalog]
- External data: Isophotal radius R25 = 53.3 arcsec for NGC 5257  
  > "which is 53.3 arcsec for NGC 5257 (cite: Fuentes-Carrera_2019)" (3.1 Gas Mass) [from (cite: Fuentes-Carrera_2019)]
- External data: Parametric rotation curve and stellar disk scale lengths 4.2 kpc (NGC 5257) and 5.8 kpc (NGC 5258)  
  > "We use the parametric fitted rotation curve from (cite: Fuentes-Carrera_2019)." (5.2 Toomre Stability); "which is 4.2 kpc and 5.8 kpc for NGC 5257 and NGC 5258 respectively (cite: Fuentes-Carrera_2019)" (5.1 SFE per free-fall time) [from (cite: Fuentes-Carrera_2019)]
- External data: Resolved ULIRG comparison points for the Kennicutt-Schmidt and eps_ff plots  
  > "We also add in resolved points from other ULIRGs (cite: Wilson_2019) for comparison." (5 Gas Properties and SFR) [from (cite: Wilson_2019)]
- External data: Main-sequence sSFR relation used to compute the starburst probability  
  > "we adopted the equation from (cite: Catinella_2018)" (3.1 Gas Mass) [from (cite: Catinella_2018)]
- External data: Stellar mass relation from 3.6 and 4.5 micron fluxes  
  > "The relevant equation is given in (cite: Eskew_2012)" (2.3 Infrared Data) [from (cite: Eskew_2012)]
- External data: 12CO/13CO and 12CO/H2 abundance ratios used as model assumptions  
  > "For the Milky Way, this ratio varies from $\sim$ 30 in the center to $\sim$ 100 in the outermost disk (cite: Milam_2005)." (4.1 RADEX Modeling) [from (cite: Milam_2005); (cite: Cormier_2018)]
- Simulation/model as data: Merger simulation of Arp 240 (Privon et al.) used to set the merger stage (just past first passage)  
  > "Simulations (cite: Privon_2013) show the two galaxies are in the early stage of the merging process and have just been through first passage." (1 Introduction)

## Processing

### Calibration

- pipeline or manual: original (archive) reduction scripts used to calibrate the raw data  
  > "The original reduction scripts were used to calibrate the raw data using CASA version 4.5.0, which is the version of CASA when the data was taken." (2.1 ALMA Data)
- casa version: CASA 4.5.0 (calibration); CASA 5.1.1 (line-free channel selection and uvcontsub); CASA 5.4.0 (all imaging)  
  > "The original reduction scripts were used to calibrate the raw data using CASA version 4.5.0, which is the version of CASA when the data was taken." (2.1 ALMA Data); "We use CASA 5.1.1 to select line free channels and subtract the continuum from the line cubes using" (2.1 ALMA Data); "All imaging steps were carried out in CASA 5.4.0." (2.1 ALMA Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (CASA 5.4.0); threshold 2 x RMS; channel width 10 km/s (12CO) and 20 km/s (13CO); total velocity range 500 km/s  
  > "All imaging steps were carried out in CASA 5.4.0." (2.1 ALMA Data); "The total velocity range is set to be 500 km s$^{-1}$. For cleaning, we set the threshold to be 2 times the RMS noise." (2.1 ALMA Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 12CO 2-1 uvtapered with a Gaussian of 1.65 x 1.44 arcsec in image space; 12CO 1-0 and 13CO 1-0 inner uvrange cut at 6 klambda  
  > "with a Gaussian beam with size of 1.65$''$ $\times$ 1.44$''$ in image space to match the small scale." (2.1 ALMA Data); "We cut the inner uvrange of the $^{12}$CO $J$=1-0 and $^{13}$CO $J$=1-0 data at 6 k$\lambda$ to match the large scale." (2.1 ALMA Data)
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh in tclean; defaults except sidelobethreshold = 4.0 (default 3.0) for 12CO 2-1 of NGC 5257  
  > "to identify clean regions automatically." (2.1 ALMA Data); "We found strong sidelobes at the edges of the $^{12}$CO $J$=2-1 map for NGC 5257 and therefore we set the sidelobethreshold to be 4.0 instead of the default 3.0." (2.1 ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA 5.1.1 after selecting line-free channels (channels not listed)  
  > "We use CASA 5.1.1 to select line free channels and subtract the continuum from the line cubes using" (2.1 ALMA Data)
- line free channels: _not stated_
- primary beam correction: applied to both moment 0 maps before the ratio map  
  > "The final step is to do primary beam correction for both moment 0 maps and calculate the ratio map." (3.2 Line Ratio)
- array combination: _not stated_
- smoothing: all cubes smoothed to 2.186 x 1.896 arcsec for the ratio maps; to 3.8 x 2.99 arcsec for RADEX  
  > "we smoothed all the image cubes to have a beam size of 2.186$''$ $\times$ 1.896$''$." (2.1 ALMA Data); "Therefore we smooth all the line images to the largest beam size of 3.8$''$ $\times$ 2.99$''$ and measure the average intensity." (4.1 RADEX Modeling)
- final beam: native beams 2.0x1.6 (12CO 1-0), 1.0x0.5 (12CO 2-1), 2.1x1.6 (13CO 1-0) arcsec  
  > "$1.6$ | 2.0 $\times$ 1.6 | 12m+7m array | 10 | 112.73" (Table 1); "$3.0$ | 1.0 $\times$ 0.5 | 12m+7m array | 10 | 225.46" (Table 1); "$0.64$ | 2.1 $\times$ 1.6 | 12m array | 20 | 107.78" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Moment 1 and 2 maps made with a consecutive-channel (>2 channels) masking algorithm  
  > "following the procedure used by (cite: Sun_2018)" (2.1 ALMA Data); "A more detailed description of their algorithm can be found in their Section 3.2." (2.1 ALMA Data) [from (cite: Sun_2018)]
- SMA 12CO 3-2 data processing  
  > "The data processing is described in (cite: Wilson_2008)." (2.2 SMA Data) [from (cite: Wilson_2008)]
- VLA 33 GHz data reduction  
  > "The detailed description of the data is in (cite: Linden_2019)." (2.5 Radio Continuum) [from (cite: Linden_2019)]
- alpha_CO prescription (starburst probability f_SB mixing of main-sequence and starburst values)  
  > "we adopt the recipe in (cite: Violino_2018)." (3.1 Gas Mass) [from (cite: Violino_2018)]
- Composite 33 GHz SFR calibration  
  > "The relation between the radio continuum and the SFR has been calibrated (cite: Murphy_2011) as" (2.5 Radio Continuum) [from (cite: Murphy_2011)]
- Bayesian likelihood RADEX grid code with beam filling factor  
  > "we use a Baysian likelihood code (cite: Kamenetzky_2016) to create probability distributions for the various parameters above." (4.1 RADEX Modeling) [from (cite: Kamenetzky_2016)]
- Gas scale height and epsilon_ff formalism  
  > "Therefore the SFE per free-fall time can be calculated as (cite: Wilson_2019)" (5.1 SFE per free-fall time) [from (cite: Wilson_2019)]
- Stellar scale height and velocity dispersion estimates  
  > "we use the empirical equation from (cite: Leroy_2008) to estimate the scale height for the stars" (5.1 SFE per free-fall time); "We use the theoretical equation (cite: Leroy_2008) based on the assumption of disk hydrostatic equilibrium to calculate the stellar velocity dispersion," (5.2 Toomre Stability) [from (cite: Leroy_2008)]
- Original archive calibration scripts  
  > "The original reduction scripts were used to calibrate the raw data using CASA version 4.5.0" (2.1 ALMA Data) [from ALMA archive reduction scripts for 2015.1.00804.S]

### Not stated but needed to reproduce (our reading)

- Which channels were treated as line-free for uvcontsub, and the continuum fit order
- tclean weighting scheme and robust value, cell size, image size and deconvolver for each cube
- Number of clean iterations and the exact auto-multithresh values other than sidelobethreshold (the 'defaults' depend on CASA 5.4.0)
- The calibration flux scale uncertainty and whether any extra flagging or self-calibration was done beyond the archive scripts
- Rest frequencies and velocity frame used for the cubes
- Exact moment-0 velocity ranges and the masks used for the Sun et al. moment 1/2 maps
- The aperture shapes (polygons drawn by eye) used for line ratios, RADEX regions and the depletion-time regions
- RADEX grid ranges, step sizes and priors for temperature, density, column density and beam filling factor (only the optical depth prior is given)
- The 33 GHz VLA image and the SMA 12CO 3-2 cube (not in the ALMA archive; from Linden et al. and Wilson et al.)
- How the 12CO 2-1 velocity dispersion map sigma_v was computed
- Beam-correction and flux-ratio treatment when matching SMA and ALMA beams

## Analysis recipe

1. **Calibrate, continuum-subtract and image the CO cubes**: Archive reduction scripts in CASA 4.5.0; line-free selection and uvcontsub in CASA 5.1.1; tclean in CASA 5.4.0 with auto-multithresh at 2 x RMS threshold  
  > "The original reduction scripts were used to calibrate the raw data using CASA version 4.5.0, which is the version of CASA when the data was taken." (2.1 ALMA Data); "All imaging steps were carried out in CASA 5.4.0." (2.1 ALMA Data)
   - software: CASA, tclean, uvcontsub
   - parameter: Channel width 10 km/s for 12CO 1-0 and 2-1, 20 km/s for 13CO 1-0  
  > "set the channel width to be 10 km s$^{-1}$ for $^{12}$CO $J$=1-0 and $^{12}$CO $J$=2-1 and 20 km s$^{-1}$ for $^{13}$CO $J$=1-0 to achieve better sensitivity." (2.1 ALMA Data)
   - parameter: Total velocity range 500 km/s; clean threshold 2 x RMS  
  > "The total velocity range is set to be 500 km s$^{-1}$. For cleaning, we set the threshold to be 2 times the RMS noise." (2.1 ALMA Data)
   - parameter: sidelobethreshold = 4.0 for 12CO 2-1 NGC 5257, other parameters default  
  > "We found strong sidelobes at the edges of the $^{12}$CO $J$=2-1 map for NGC 5257 and therefore we set the sidelobethreshold to be 4.0 instead of the default 3.0." (2.1 ALMA Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps**: Moment 0 with immoments at 2 RMS; moment 1 and 2 with the Sun et al. (2018) algorithm that keeps only signal spanning more than 2 consecutive channels  
  > "with threshold of 2 RMS for each image cube." (2.1 ALMA Data); "it will only pick out signals spanning more than 2 consecutive velocity channels, which excludes noisy pixels with inaccurate velocity measurements." (2.1 ALMA Data)
   - software: CASA immoments, Sun et al. 2018 Python script
   - fitting: _not stated_
   - validation: _not stated_
3. **Match resolution and uv coverage; build line-ratio maps**: Cut inner uv at 6 klambda for 12CO 1-0 and 13CO 1-0, taper 12CO 2-1, re-image, smooth to a common beam; use matched-threshold moment 0 maps and primary-beam corrected ratios  
  > "We cut the inner uvrange of the $^{12}$CO $J$=1-0 and $^{13}$CO $J$=1-0 data at 6 k$\lambda$ to match the large scale." (2.1 ALMA Data); "we smoothed all the image cubes to have a beam size of 2.186$''$ $\times$ 1.896$''$." (2.1 ALMA Data)
   - software: CASA
   - parameter: Ratio-map threshold: 2 x flux ratio x 13CO RMS cut on the 12CO cube; S/N cut of 5 on 12CO 1-0 for the 2-1/1-0 map  
  > "We then applied a 2 $\times$ the flux ratio $\times$ $^{13}$CO $J$=1-0 RMS cut to the $^{12}$CO $J$=1-0 cube to make the moment 0 map." (3.2 Line Ratio); "we adopt a S/N cut of 5 instead of 2 for the $^{12}$CO $J$=1-0 cube." (3.2 Line Ratio)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive global gas masses, concentration and gas fractions**: M_mol = alpha_CO x L_CO(1-0) within a Petrosian-radius aperture; alpha_CO chosen via the Violino et al. starburst probability, which gives f_SB about 1 so the ULIRG value is adopted; gas concentration from the central 500 pc vs the R25 surface density  
  > "We adopted a circular aperture with radius equal to the Petrosian radius $R_p$ to measure the global gas mass." (3.1 Gas Mass); "This analysis suggests that we should adopt the ULIRG conversion factor for both galaxies." (3.1 Gas Mass)
   - parameter: Blank pixels within R25 set to zero or to the noise to bracket the concentration degree  
  > "The first is to assume all the blank pixels have an intensity equal to zero. The second is to assume all the blank pixels have an intensity equal to the noise, which defines the lower limit of the ratio." (3.1 Gas Mass)
   - assumption: ULIRG conversion factor 1.1 Msun (K km/s pc^2)^-1  
  > "From the $^{12}$CO $J$=1-0 ALMA observations assuming a ULIRG conversion factor of 1.1" (Table 1)
   - fitting: _not stated_
   - validation: Compared the gas concentration with barred and unbarred galaxies of Sakamoto et al.  
  > "This clearly suggests that NGC 5257 is fairly gas concentrated in the center." (3.1 Gas Mass)
5. **Measure SFR surface density from 33 GHz continuum**: Murphy et al. composite free-free plus synchrotron relation applied to the 33 GHz image; polygon apertures drawn by eye around star-forming regions  
  > "The relation between the radio continuum and the SFR has been calibrated (cite: Murphy_2011) as" (2.5 Radio Continuum); "These polygon regions drawn by eye roughly correspond to regions with signal-to-noise (S/N) value greater than 4.0." (3.3 Star Formation Rates)
   - parameter: VLA resolution about 0.5 arcsec, sensitivity about 9.8e-6 Jy/beam  
  > "the sensitivity is about $9.8 \times 10^{-6}$ Jy beam$^{-1}$." (2.5 Radio Continuum)
   - assumption: alpha_NT = 0.85 and T_e = 1e4 K  
  > "We assume $\alpha^{NT}=0.85$ (cite: Murphy_2012) and $T_e=10^4\ \si{K}$." (2.5 Radio Continuum)
   - fitting: _not stated_
   - validation: _not stated_
6. **Model CO line ratios with RADEX**: Grid of one-component RADEX models fit to the 12CO 1-0, 2-1, 3-2 and 13CO 1-0 intensities in three regions, with a Bayesian likelihood code that adds a beam filling factor; 1D and 4D maximum-likelihood solutions  
  > "We use a grid of models across the parameter space to fit the observed line intensities." (4.1 RADEX Modeling); "This code gives two types of solutions, 1D Max and 4D max." (4.1 RADEX Modeling)
   - software: RADEX, Kamenetzky et al. 2016 Bayesian likelihood code
   - parameter: All lines smoothed to 3.8 x 2.99 arcsec and average intensity measured (peak intensity at the center of NGC 5257)  
  > "Therefore we smooth all the line images to the largest beam size of 3.8$''$ $\times$ 2.99$''$ and measure the average intensity." (4.1 RADEX Modeling); "Therefore, we use the peak intensity instead of the average intensity for the center of NGC 5257." (4.1 RADEX Modeling)
   - parameter: Median FWHM linewidths 135, 116 and 87 km/s for NGC 5257 center, NGC 5257 south-west and NGC 5258 south arm  
  > "which are 135, 116 and 87 km s$^{-1}$ for the center and south-west region of NGC 5257 and the south arm of NGC 5258 respectively." (4.1 RADEX Modeling)
   - parameter: 12CO/13CO abundance ratio fixed to 50 (fiducial), 30 and 100 (extremes)  
  > "and the lower and upper extreme values to be 30 and 100." (4.1 RADEX Modeling)
   - assumption: 12CO/H2 abundance 1e-4 with helium correction 1.4  
  > "We assume the \[$^{12}$CO\]/\[H$_2$\] abundance ratio to be $10^{-4}$ (cite: Cormier_2018) with a helium correction to be 1.4." (4.1 RADEX Modeling)
   - assumption: Optical depth prior 0 to 100; one-component model  
  > "The lower limit is set due to the fact that CO should not be a maser. The upper limit is recommended by the RADEX documentation." (4.1 RADEX Modeling); "Because we only model the lower J CO lines, we use a one-component model." (4.1 RADEX Modeling)
   - fitting: Grid plus Bayesian likelihood (Kamenetzky et al. code); 1D and 4D maximum-likelihood solutions; free parameters temperature, H2 density, column density, beam filling factor  
  > "we use a Baysian likelihood code (cite: Kamenetzky_2016) to create probability distributions for the various parameters above." (4.1 RADEX Modeling)
   - validation: Modeled CO SLEDs compared with measured ones; 1D and 4D solutions differ by at most 0.5 dex  
  > "From these figures, we can see the modeling generally reproduces the measured CO SLEDs." (4.1 RADEX Modeling)
7. **Derive alpha_CO from RADEX and from an LTE analysis**: RADEX: N_H2 = N_12CO,beam-averaged / [12CO/H2], compared with the 12CO 1-0 intensity; LTE: optically thick 12CO plus optically thin 13CO gives tau_13 = 1/R, excitation temperature from 12CO peak T_B, per-pixel alpha_CO averaged weighted by N_12CO  
  > "We can compare these results directly with the $^{12}$CO $J$=1-0 intensity to calculate the conversion factor." (4.2 CO-to-H2 Conversion Factor); "We use a local thermal equilibrium (LTE) analysis for the $^{12}$CO/$^{13}$CO $J$=1-0 ratio to try to understand what causes the change in the ratio." (4.3 Comparison with LTE Analysis)
   - software: RADEX
   - parameter: LTE: pixels binned to 1.5 x 1.5 arcsec; 12CO/13CO = 50; beam filling factor 0.1 and 1.0  
  > "We then binned the pixels to be 1.5$''$ $\times$ 1.5$''$." (4.3 Comparison with LTE Analysis); "We assume the abundance ratio of \[$^{12}$CO\]/\[$^{13}$CO\] to be 50." (4.3 Comparison with LTE Analysis)
   - assumption: 12CO/H2 = 1e-4, same as the RADEX input  
  > "which is the same as our input into the RADEX model." (4.3 Comparison with LTE Analysis)
   - fitting: _not stated_
   - validation: LTE alpha_CO consistent with the RADEX results; alpha_CO acknowledged as strongly dependent on the assumed abundance ratios  
  > "which is consistent with our RADEX modeling results." (4.3 Comparison with LTE Analysis)
8. **Compute depletion times and SFE per free-fall time**: t_dep = Sigma_mol/Sigma_SFR from 12CO 2-1 (ratio 0.8, ULIRG alpha_CO) and 33 GHz; eps_ff = t_ff/t_dep with scale height from gas self-gravity (Wilson et al.), then corrected for the stellar component using midplane gas fraction  
  > "The molecular mass is calculated based on the $^{12}$CO $J$=2-1 intensity. We assume the conversion factor to be a ULIRG conversion factor." (5 Gas Properties and SFR); "Assuming the gas disk is in equilibrium and that vertical gravity is dominated by gas self-gravity, then we can calculate the scale height as (cite: Wilson_2019)" (5.1 SFE per free-fall time)
   - parameter: Pixel analysis: S/N = 4 cut on the 33 GHz image; pixels binned to 1.0 x 1.0 arcsec  
  > "For pixel selection, we applied a S/N=4 cut to the 33 GHz image." (5 Gas Properties and SFR); "We then binned the pixels to 1.0$''$ $\times$ 1.0$''$ to get independent measurements." (5 Gas Properties and SFR)
   - assumption: 12CO 2-1/1-0 ratio 0.8; ULIRG alpha_CO  
  > "We also assume the $^{12}$CO $J$=2-1/1-0 ratio is 0.8, which is the flux ratio measurement from section 3.2." (5 Gas Properties and SFR)
   - fitting: _not stated_
   - validation: Tested the effect of the stellar potential, the 2-1/1-0 ratio and alpha_CO on eps_ff  
  > "We can see that the efficiency per free-fall time including the stellar component is slightly smaller." (5.1 SFE per free-fall time)
9. **Toomre stability analysis**: Q for a gas disk and the composite Q_tot of Wang and Silk including stars; stellar surface density from Spitzer images; kappa from the parametric rotation curve  
  > "Therefore, we can apply a Toomre stability analysis (cite: Toomre1977)" (5.2 Toomre Stability); "We use the parametric fitted rotation curve from (cite: Fuentes-Carrera_2019)." (5.2 Toomre Stability)
   - assumption: Stellar velocity dispersion from the hydrostatic equilibrium relation (no measured sigma_star)  
  > "We do not have data for" (5.2 Toomre Stability)
   - fitting: _not stated_
   - validation: Q_tot correlated against t_dep and eps_ff for star-forming pixels; found no clear trend  
  > "We see there is no clear trend in both plots." (5.2 Toomre Stability)

## Software

- **CASA** 4.5.0 (calibration); 5.1.1 (uvcontsub); 5.4.0 (imaging): Calibration, continuum subtraction, imaging and moment maps  
  > "All imaging steps were carried out in CASA 5.4.0." (2.1 ALMA Data); "We use CASA 5.1.1 to select line free channels and subtract the continuum from the line cubes using" (2.1 ALMA Data)
- **tclean** CASA 5.4.0: Imaging with auto-multithresh masking and uv taper  
  > "We found strong sidelobes at the edges of the $^{12}$CO $J$=2-1 map for NGC 5257 and therefore we set the sidelobethreshold to be 4.0 instead of the default 3.0." (2.1 ALMA Data)
- **uvcontsub** CASA 5.1.1: Continuum subtraction of line cubes  
  > "We use CASA 5.1.1 to select line free channels and subtract the continuum from the line cubes using" (2.1 ALMA Data)
- **immoments** : Moment 0 maps of ALMA and SMA cubes  
  > "we remake the moment 0 map (Fig. [3](#fig:SMA)) using the CASA" (2.2 SMA Data)
- **RADEX** : Radiative transfer modeling of the CO lines  
  > "we use the radiative transfer code RADEX (cite: vandertak_2007)." (4.1 RADEX Modeling)
- **Bayesian likelihood code (Kamenetzky et al. 2016)** : Probability distributions of RADEX parameters including beam filling factor  
  > "we use a Baysian likelihood code (cite: Kamenetzky_2016) to create probability distributions for the various parameters above." (4.1 RADEX Modeling)
- **Sun et al. 2018 moment-map Python script** : Moment 1 and moment 2 maps with consecutive-channel masking  
  > "This algorithm was implemented in a Python script" (2.1 ALMA Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Global molecular gas mass NGC 5257 (ULIRG alpha_CO) | 4.6e9 | not stated | Msun | 4 | The gas mass is about $4.6 \times 10^{9} |
| Global molecular gas mass NGC 5258 (ULIRG alpha_CO) | 7.2e9 | not stated | Msun | 4 | and $7.2 \times 10^{9} |
| sSFR ratio to main sequence, NGC 5257 and NGC 5258 | 9.37 and 7.8 | not stated | dimensionless | 4 | The ratio is 9.37 for NGC 5257 and 7.8 for NGC 5258. |
| Gas concentration degree NGC 5257 | 72 to 95 | range from the two blank-pixel treatments | dimensionless | 4 | We calculated the concentration degree of NGC 5257 to be $72 \sim 95$. |
| Gas concentration degree NGC 5258 (central 500 pc) | 11 to 13 | range from the two blank-pixel treatments | dimensionless | 4 | which is about $11 \sim 13$. |
| Global gas fraction NGC 5257 and NGC 5258 | 0.05 and 0.07 | not stated | dimensionless | 4 | The global gas fraction is 0.05 for NGC 5257 and 0.07 for NGC 5258. |
| Global 12CO/13CO J=1-0 and 12CO 2-1/1-0 ratio, NGC 5257 | 13.1 and 0.80 | 0.06 on the 2-1/1-0 ratio; 1.0 on 12/13 | dimensionless | 3 | Global / $13.1 \pm 1.0$ / $0.80 \pm 0.06$ |
| Global 12CO/13CO J=1-0 and 12CO 2-1/1-0 ratio, NGC 5258 | 10.9 and 0.85 | 0.8 on 12/13; 0.06 on 2-1/1-0 | dimensionless | 3 | Global / $10.9 \pm 0.8$ / $0.85 \pm 0.06$ |
| Central 12CO/13CO J=1-0 ratio in NGC 5258 | 5.6 | 0.5 | dimensionless | 3 | Center / $5.6 \pm 0.5$ / $0.80 \pm 0.07$ |
| alpha_CO from RADEX, NGC 5257 center (12CO/13CO = 100, 50, 30) | 1.9, 0.9, 0.5 | +0.5/-0.4, +0.2/-0.2, +0.1/-0.1 | Msun pc^-2 (K km/s)^-1 | 7 | Center / $1.9_{-0.4}^{+0.5}$ / $0.9_{-0.2}^{+0.2}$ / $0.5_{-0.1}^{+0.1}$ |
| alpha_CO from RADEX, NGC 5257 south-west (12CO/13CO = 100, 50, 30) | 0.9, 0.4, 0.23 | +0.4/-0.3, +0.1/-0.1, +0.04/-0.03 | Msun pc^-2 (K km/s)^-1 | 7 | South West / $0.9_{-0.3}^{+0.4}$ / $0.4_{-0.1}^{+0.1}$ / $0.23_{-0.03}^{+0.04}$ |
| alpha_CO from RADEX, NGC 5258 south arm (12CO/13CO = 100, 50, 30) | 3.4, 1.5, 0.5 | +4.7/-2.0, +1.9/-0.8, +0.3/-0.2 | Msun pc^-2 (K km/s)^-1 | 7 | South Arm / $3.4_{-2.0}^{+4.7}$ / $1.5_{-0.8}^{+1.9}$ / $0.5_{-0.2}^{+0.3}$ |
| LTE mean alpha_CO NGC 5257 (beam filling 1.0 and 0.1) | 0.50 and 0.94 | not stated | Msun pc^-2 (K km/s)^-1 | 7 | NGC 5257 / 0.50 / 0.94 |
| LTE mean alpha_CO NGC 5258 (beam filling 1.0 and 0.1) | 0.59 and 1.27 | not stated | Msun pc^-2 (K km/s)^-1 | 7 | NGC 5258 / 0.59 / 1.27 |
| Depletion time, NGC 5257 center (Sigma_SFR 2.5, Sigma_mol 550) | 2.16e8 | not stated | yr | 8 | NGC5257 / center / 2.5 / 550 / 2.16 |
| Depletion time, NGC 5257 arm (Sigma_SFR 1.1, Sigma_mol 86) | 0.77e8 | not stated | yr | 8 | arm / 1.1 / 86 / 0.77 |
| Depletion time, NGC 5257 west (Sigma_SFR 1.1, Sigma_mol 45) | 0.42e8 | not stated | yr | 8 | west / 1.1 / 45 / 0.42 |
| Depletion time, NGC 5257 south (Sigma_SFR 3.0, Sigma_mol 79) | 0.27e8 | not stated | yr | 8 | south / 3.0 / 79 / 0.27 |
| Depletion time, NGC 5258 south arm (Sigma_SFR 2.4, Sigma_mol 338) | 1.5e8 | not stated | yr | 8 | NGC5258 / south arm / 2.4 / 338 / 1.5 |
| Fraction of NGC 5257 global SFR in its center | 7% | not stated | percent | 5 | The SFR enclosed in the center of NGC5257 makes up only 7% of the global SFR of NGC 5257 |
| Fraction of NGC 5258 global SFR in its only radio-detected region | about 30% | not stated | percent | 5 | For NGC 5258, the only radio detected SF region contains about 30% of the global SFR of this galaxy. |
| Offset between YMC position and 33 GHz peak (south source, NGC 5257) | 1.1 | not stated | arcsec | 5 | The offset for that particular source is 1.1 arcsec. |
| Q_tot in the center of NGC 5258 | about 3 | not stated | dimensionless | 9 | In the center of NGC 5258, the Q value is about 3 |

## Qualitative findings

- Molecular gas is concentrated in the center of NGC 5257 but in the south spiral arm of NGC 5258  
  > "For NGC 5257, the gas is clearly concentrated in the center." (3.1 Gas Mass); "For NGC 5258, the gas is concentrated in the south spiral arm instead of the center." (3.1 Gas Mass)
- The off-center NGC 5257 star-forming regions with short depletion times are associated with young massive clusters  
  > "We note that these regions with short depletion times are generally associated with the existence of young massive star clusters" (3.3 Star Formation Rates)
- Star-forming regions outside the NGC 5257 center have Toomre factor below 0.5 (highly unstable); gas Q exceeds Q_tot by a factor 2.5 to 10  
  > "Except for that region, all the star forming regions have a Toomre factor below 0.5, which is highly unstable to gravitational collapse." (5.2 Toomre Stability)

## Claim tuples

- H: Is Arp 240 in an early merger stage as simulations suggest? | E: Global gas fraction and SFE from ALMA 12CO 1-0 gas masses, Spitzer stellar masses and radio SFR, compared with other close pairs | R: Lower global gas fraction but higher SFE than typical close pairs; global depletion time about 1e8 yr | F: Arp 240 may already be in an advanced merger stage despite having just passed first passage in simulations | **partially**
- H: What is the CO-to-H2 conversion factor in Arp 240 regions? | E: RADEX modeling of 12CO 1-0, 2-1, 3-2 and 13CO 1-0 in three regions, plus a pixel-by-pixel LTE analysis | R: RADEX alpha_CO for 12CO/13CO = 50 is 0.9, 0.4 and 1.5; LTE mean values are 0.50 to 1.27 | F: alpha_CO is close to or smaller than the ULIRG value, though dependent on the assumed 12CO/13CO and 12CO/H2 abundances | **partially**
- H: Do star-forming regions in Arp 240 have short molecular gas depletion times? | E: 33 GHz SFR and 12CO 2-1 gas surface density in apertures and in individual pixels | R: Aperture depletion times 0.27e8 to 2.16e8 yr, shortest in the off-center NGC 5257 sources | F: Most star-forming regions have depletion times under 100 Myr, comparable to ULIRGs for off-center sources | **supported**
- H: Why does the SFE per free-fall time exceed 100% in some regions? | E: Computed eps_ff with and without the stellar potential, tested Toomre Q, the 2-1/1-0 ratio and alpha_CO as alternative causes | R: eps_ff near or above 1 in off-center NGC 5257 regions with YMCs; stellar potential, Q and alpha_CO do not remove it | F: The 33 GHz emission is likely dominated by YMCs, causing an overestimate of eps_ff; needs pc-resolution data to confirm | **partially**
- H: Does disk instability (Toomre Q) set depletion time or eps_ff? | E: Q_tot maps with stars and gas, compared with t_dep and eps_ff pixel by pixel | R: All major star-forming regions have Q_tot below 1 but no trend with t_dep or eps_ff | F: Q_tot only sets the criterion for collapse, not its speed, as in Leroy et al. | **supported**

## Reasoning

- Why this data: Few resolved CO studies of early-stage mergers exist; a still earlier merger than Arp 55 can test the alpha_CO transition  
  > "A study of an even earlier merger will help us to explore this problem." (1 Introduction)
- Why this method: RADEX with multiple CO lines constrains gas properties and alpha_CO in resolved regions  
  > "One of the tools to constrain the molecular gas properties as well as the conversion factor is RADEX modeling (cite: vandertak_2007)." (1 Introduction)
- Alternative: Stellar potential, Toomre instability and the 2-1/1-0 ratio were examined as causes of high eps_ff and found insufficient (the ratio helps only for the south region)  
  > "However, changing the $^{12}$CO $J$=2-1/1-0 ratio does not help for the other two off-center star forming regions in NGC 5257." (5.3 Causes to the high eps_ff); "We further excluded the factor of Toomre instability in Section 5.2" (5.3 Causes to the high eps_ff)
- How they decided it was enough: _not stated_
- Limitation (authors): SMA 12CO 3-2 missing flux at the NGC 5257 center  
  > "Possibly due to the missing flux problem of the SMA data (cite: Wilson_2008), the center of NGC 5257 has an extremely low" (4.1 RADEX Modeling)
- Limitation (authors): Only one 13CO line, so the 12CO/13CO abundance ratio must be fixed and alpha_CO depends on it  
  > "To constrain all the parameters, we would still need an additional" (4.1 RADEX Modeling)
- Limitation (authors): Limited ALMA sensitivity: no CO detection out to the isophotal radius  
  > "Due to the limited sensitivity, we do not detect molecular gas out to the isophotal radius" (3.1 Gas Mass)
- Limitation (authors): Toomre analysis assumes a thin disk with no external force, not ideal for mergers  
  > "Finally, we note that the Toomre instability analysis assumes the galaxy disk to be infinitely thin without any external force." (5.2 Toomre Stability)
- Caveat (inferred, ours): alpha_CO conclusions rest on a fixed 12CO/13CO ratio and a fixed 12CO/H2 abundance, so the 'close to ULIRG' result is largely an assumption-driven range
- Caveat (inferred, ours): RADEX results come from only three regions with beam-matched SMA data and a missing-flux problem; density is unconstrained by 2 dex
- Caveat (inferred, ours): The ULIRG alpha_CO is assumed in the gas masses used for the main depletion time and eps_ff results, so the SFE conclusions inherit that assumption
- Caveat (inferred, ours): The YMC-dominated radio emission explanation is not tested with data of pc resolution
- Caveat (inferred, ours): Regions are drawn by eye, so region-based numbers are hard to reproduce exactly

## Reproducibility

- Data public (paper): Paper states the data are public in the references and available from the authors on request  
  > "This research is based on public data available in the references. The whole dataset can be obtained from the authors by request." (Data Availability)
- Products in archive: _not stated_
- Code: Moment-map Python script of Sun et al. is public on GitHub; no code released by the authors themselves  
  > "https://github.com/astrojysun/Sun_Astro_Tools/blob/master/sun_astro_tools/spectralcube.py" (footnote 2)
- Missing: Weighting, robust, cell and image sizes, and line-free channels for the CO cubes
- Missing: Aperture and region definitions (drawn by eye) for ratios, RADEX regions and depletion times
- Missing: RADEX grid ranges and priors beyond optical depth
- Missing: The 33 GHz VLA image (Linden et al.) and the SMA 12CO 3-2 data (Wilson et al.)
- Missing: The sigma_v map definition used in eps_ff and Toomre Q
- Data volume (inferred): Band 3 and Band 6 12m+7m mosaics with several spectral windows; likely tens to a few hundred GB of raw/calibrated data (estimate)
- Score (inferred): 3/5, ALMA data and archive scripts are public and the imaging/moment/ratio recipe is largely given with CASA versions, but imaging weights, masks, regions and RADEX priors are missing and the SMA and VLA inputs come from other papers.
- Rediscovery candidate: no, Key results need the SMA 3-2 and VLA 33 GHz data and hand-drawn regions, and several imaging settings are not stated.

## Links

- Method: (cite: Sun_2018) (Moment 1 and 2 map algorithm)
- Method: (cite: vandertak_2007) (RADEX radiative transfer code)
- Method: (cite: Kamenetzky_2016) (Bayesian likelihood code for RADEX grids)
- Method: (cite: Violino_2018) (alpha_CO prescription from starburst probability)
- Method: (cite: Murphy_2011) (33 GHz SFR calibration)
- Method: (cite: Wilson_2019) (Gas scale height and eps_ff formalism)
- Companion: (cite: Sliwa_2017) (Arp 55 CO study used for comparison of alpha_CO and abundance ratios)
- Companion: (cite: Wilson_2008) (SMA 12CO 3-2 data for Arp 240)
- Companion: (cite: Linden_2019) (VLA 33 GHz data of Arp 240)
- Companion: (cite: Linden_2017) (Young massive cluster catalogue for the system)
- Companion: (cite: Privon_2013) (Merger simulation placing Arp 240 just past first passage)
- Related: ALMA project 2015.1.00804.S (PI Sliwa)
- Related: Spitzer project 70038 (PI Sanders)

## Checks

```json
{
 "quotes": 187,
 "quotes_ok": 187,
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
  "facts": 131,
  "stated": 99,
  "rate": 0.756
 },
 "evidence_ok": true
}
```
