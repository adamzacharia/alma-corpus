# ALMA detection of hydrogen cyanide in the atmosphere of Saturn

`2024JApA...45...31M` | Journal of Astrophysics and Astronomy 2024 | first author: Manna, Arijit | arXiv: 2104.10474 | DOI: 10.1007/s12036-024-10024-w

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: solar_system, astrochemistry
- Question: Detect HCN rotational emission in Saturn's atmosphere with ALMA, and derive its abundance, vertical distribution and likely formation mechanism  
  > "In this letter, we present the detection of the rotational emission line of HCN in the atmosphere of Saturn using ALMA." (Introduction); "the authors did not focus on studying the mixing ratio, vertical distribution, and formation pathways of HCN in the atmosphere of Saturn." (Observation and data reductions)
- Target **Saturn**: coordinates phase centre (J2000) 18:37:56.412, –22:15:52.617  
  > "18:37:56.412, –22:15:52.617" (Observation and data reductions); "the geocentric distance was 9.21 AU" (Observation and data reductions); z/distance geocentric distance 9.21 AU  
  > "18:37:56.412, –22:15:52.617" (Observation and data reductions); "the geocentric distance was 9.21 AU" (Observation and data reductions); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00636.S
- bands: Band 7  
  > "the high-resolution Atacama Large Millimeter/Submillimeter Array (ALMA) band 7 with a 12 m array (PI: Fouchet, Thierry)" (Observation and data reductions)
- frequencies and spectral setup: 340.98–342.96, 342.98–344.96, 354.42–354.54 and 354.98–356.96 GHz; spectral resolutions 1128.91, 70.56, 282.23 and 1128.91 kHz respectively  
  > "The observed frequency ranges were 340.98–342.96 GHz, 342.98–344.96 GHz, 354.42–354.54 GHz, and 354.98–356.96 GHz, with spectral resolutions of 1128.91 kHz, 70.56 kHz, 282.23 kHz, and 1128.91 kHz, respectively." (Observation and data reductions)
- continuum bandwidth: _not stated_
- arrays: 12 m array; 44 antennas  
  > "a total of forty-four antennas were used, with an on-source integration time of 476.40 sec." (Observation and data reductions)
- configurations: _not stated_
- baselines: 15.0 m to 313.7 m  
  > "The minimum and maximum baselines during the observation were 15.0 m and 313.7 m." (Observation and data reductions)
- angular resolution: 0.70, 0.78, 0.82 and 0.85 arcsec for the four frequency ranges respectively  
  > "the angular resolution was 0.70$^{\prime\prime}$, 0.78$^{\prime\prime}$, 0.82$^{\prime\prime}$, and 0.85$^{\prime\prime}$ for the corresponding frequency ranges" (Observation and data reductions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 476.40 sec  
  > "a total of forty-four antennas were used, with an on-source integration time of 476.40 sec." (Observation and data reductions)
- observing dates: May 25, 2018  
  > "Saturn was observed on May 25, 2018" (Observation and data reductions)
- pi or archival as stated: Archival data; PI Fouchet, Thierry  
  > "We used the archival data of the solar gas planet Saturn" (Observation and data reductions); "band 7 with a 12 m array (PI: Fouchet, Thierry)" (Observation and data reductions)
- Line: HCN J = 4–3 (354.505 GHz)
- Line: CO J = 3–2 (345 GHz (as stated, approximate))
- Other facility **TGSS, NVSS and Spitzer sky surveys**: Checked at Saturn's coordinates for sources near the limb; none seen  
  > "We also checked the TGSS, NVSS, and Spitzer sky survey data using the coordinates of Saturn, but we did not observe any source close to the limb." (Line emission towards Saturn)
- External data: Disk-averaged retrieved temperature profile of Saturn, used in the PSG forward model and retrieval  
  > "For the temperature profile, we used the disk-averaged retrieved result from (cite: lel84)." (Determination of the abundance of HCN) [from Lellouch, Encrenaz & Combes 1984, A&A, 135, 371 (cite: lel84)]
- External data: Atmospheric layers (60 layers) and default vertical abundance profiles of CH4, C2H6, C2H2, NH3, NH4SH in PSG  
  > "The atmospheric layers are taken from (cite: mos05)." (Determination of the abundance of HCN); "we use default values available in PSG (cite: mos05)" (Retrieval profile of HCN) [from Moses 2005, JGRE, 110, E08001 (cite: mos05)]
- External data: HITRAN molecular database for HCN spectroscopic parameters  
  > "We used the HITRAN molecular database for spectroscopic parameters to obtain the abundance of HCN from the western and eastern limbs of Saturn." (Determination of the abundance of HCN) [from HITRAN (no citation given in the paper)]
- External data: Perley-Butler 2017 flux calibrator model used with SETJY  
  > "we used the Perley-Butler 2017 flux calibrator model to match the continuum flux density of the flux calibrator with 5% accuracy" (Observation and data reductions) [from Perley & Butler 2017, ApJ, 230, 1538 (cite: pal17)]
- External data: Earlier modelled HCN VMR in Saturn's atmosphere of 3.58 ppb, used for comparison  
  > "Earlier, (cite: lel84) simulated the VMR in the atmosphere of Saturn to be 3.58 ppb" (Determination of the abundance of HCN) [from Lellouch, Encrenaz & Combes 1984 (cite: lel84)]
- External data: Earlier model-derived limb line shifts of -9.2 km/s (east) and 7.7 km/s (west), used for comparison  
  > "(cite: ca10) also showed the millimeter-wavelength spectral line of Saturn is shifted –9.2 km s$^{-1}$ for the eastern limb line-of-sight and 7.7 km s$^{-1}$ for the western limb line-of-sight" (Line emission towards Saturn) [from Cavalié et al. 2010, A&A, 510, A88 (cite: ca10)]
- Simulation/model as data: PSG radiative-transfer model spectra of HCN (line-by-line and correlated-k) fitted to the observed limb spectra  
  > "During the computation of the simulated spectra, we used the line-by-line and correlated-k approaches for better spectral resolution." (Determination of the abundance of HCN)

## Processing

### Calibration

- pipeline or manual: ALMA standard pipeline in CASA, plus pipeline flagging tasks hifa_bandpassflag and hifa_flagdata and manual flagging of telluric channels  
  > "with a standard data reduction pipeline delivered by the ALMA observatory for data analysis and imaging" (Observation and data reductions); "We applied the CASA pipeline tasks `hifa_bandpassflag` and `hifa_flagdata` to remove the bad antenna data." (Observation and data reductions)
- casa version: CASA 5.4.1  
  > "Common Astronomy Software Application (`CASA 5.4.1`)" (Observation and data reductions)
- pipeline version: _not stated_
- archive products used as is: No: raw archival data were downloaded and reduced by the authors  
  > "After downloading the archival raw data of Saturn from the ALMA archive" (Observation and data reductions)
- flux calibrator: J1750+0939 (flux and bandpass); Perley-Butler 2017 model via SETJY; phase calibrator J1832–2039  
  > "the flux and bandpass calibrators were taken as J1750+0939, and the phase calibrator was taken as J1832–2039" (Observation and data reductions); "we used the Perley-Butler 2017 flux calibrator model to match the continuum flux density of the flux calibrator with 5% accuracy using the task `SETJY` in CASA" (Observation and data reductions)
- flux scale uncertainty: 5% accuracy (flux calibrator model match)  
  > "we used the Perley-Butler 2017 flux calibrator model to match the continuum flux density of the flux calibrator with 5% accuracy" (Observation and data reductions)
- self calibration: _not stated_

### Imaging

- task: MSTRANSFORM to split target; TCLEAN (continuum, then specmode=cube per rest frequency); IMPBCOR; IMMOMENTS  
  > "we separated the target dataset into another dataset using the task `MSTRANSFORM` with all available rest frequencies." (Observation and data reductions); "we used the task `TCLEAN` with the `SPECMODE = CUBE` parameter for each rest frequency to create the spectral data cubes of Saturn." (Observation and data reductions)
- deconvolver: Hogbom (continuum image)  
  > "we used task `TCLEAN` with the `HOGBOM` algorithm to create the continuum image of Saturn." (Observation and data reductions)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB  
  > "we used the CASA task `UVCONTSUB` for continuum subtraction because continuum subtraction is essential for studying the spectral line." (Observation and data reductions)
- line free channels: Line-free channels used for the continuum images (ranges not given)  
  > "We used the line-free channels during the production of the continuum emission images." (Observation and data reductions)
- primary beam correction: IMPBCOR  
  > "To correct the primary beam pattern in the synthesized image, we applied the `IMPBCOR` task in the CASA." (Observation and data reductions)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.78 x 0.61 arcsec (continuum image)  
  > "The synthesized beam size of the continuum image was 0.78$^{\prime\prime}\times$0.61$^{\prime\prime}$." (Continuum emission towards Saturn)
- final rms: _not stated_

### Inherited from earlier work

- Least-squares fitting of the PSG model spectrum to the observed spectrum follows the method described in Iino et al. 2020  
  > "we used the least-squares method, which is well described in (cite: ii20)" (Determination of the abundance of HCN) [from Iino et al. 2020, ApJL, 903, L1 (cite: ii20)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: cell size, image size, weighting/robust, masking, threshold, niter, channel width and velocity resolution of the cubes
- Line-free channel ranges used for the continuum image and the UVCONTSUB fit
- Which flagged data and spectral windows were used for the 354.5 GHz cube, and how the 355.01 GHz ozone line was handled in the HCN window
- Velocity range used for the IMMOMENTS integrated map
- PSG configuration: instrument beam/resolution settings, observing geometry inputs, line-width treatment, pressure-grid definition, and the exact HCN input profile shape (constant VMR or scaled profile) used for the fit
- Uncertainty model of the least-squares fit and the optimal-estimation retrieval (a priori profile, covariance, noise), and how the limb aperture geometry enters the model
- Whether the PSG forward model accounts for the interferometric filtering of the disk flux
- Detection significance (SNR) and per-channel rms of the HCN spectra
- Why the eastern shift is quoted as -9.2 km/s in the text and fixed at -9.26 km/s in the fit

## Analysis recipe

1. **Calibrate raw ALMA data**: Import the raw ASDM into CASA 5.4.1, set the flux scale with SETJY, flag bad antennas with pipeline tasks, flag telluric channels during bandpass calibration, then apply flux, bandpass and gain calibration  
  > "We applied the CASA pipeline tasks `hifa_bandpassflag` and `hifa_flagdata` to remove the bad antenna data." (Observation and data reductions); "During the bandpass calibration, we carefully removed the telluric effect from the data by flagging the channels where the telluric absorption lines were observed." (Observation and data reductions)
   - software: CASA 5.4.1, importasdm, setjy, hifa_bandpassflag, hifa_flagdata
   - parameter: Flux model: Perley-Butler 2017, matched to the calibrator continuum flux to 5% accuracy  
  > "we used the Perley-Butler 2017 flux calibrator model to match the continuum flux density of the flux calibrator with 5% accuracy" (Observation and data reductions)
   - parameter: Strong telluric ozone line at 355.01 GHz removed  
  > "at a frequency of 355.01 GHz, and we removed that line during the data analysis" (Observation and data reductions)
   - fitting: _not stated_
   - validation: No telluric lines near the CO and HCN lines  
  > "We do not observe any telluric lines near the lines of CO and HCN." (Observation and data reductions)
2. **Make continuum image and line cubes**: Split target with MSTRANSFORM; TCLEAN (Hogbom) continuum image from line-free channels; UVCONTSUB; TCLEAN specmode=cube per rest frequency; IMPBCOR primary-beam correction  
  > "After the flux, bandpass, and gain calibration, we separated the target dataset into another dataset using the task `MSTRANSFORM` with all available rest frequencies." (Observation and data reductions); "After continuum subtraction, we used the task `TCLEAN` with the `SPECMODE = CUBE` parameter for each rest frequency to create the spectral data cubes of Saturn." (Observation and data reductions)
   - software: CASA 5.4.1, mstransform, tclean, uvcontsub, impbcor
   - parameter: Continuum image: tclean with hogbom deconvolver using line-free channels  
  > "we used task `TCLEAN` with the `HOGBOM` algorithm to create the continuum image of Saturn." (Observation and data reductions)
   - assumption: Disk flux filtered out by lack of short spacings; only limb emission preserved  
  > "As a result of the lack of short spacing with the interferometer, the disk flux of Saturn is filtered out, and only the emission from the limbs is preserved." (Observation and data reductions)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure the disk continuum flux density**: Disk-average flux density (excluding rings) from a 16 arcsec circle over the planet disk; ring flux not estimated  
  > "We estimate the flux density by drawing a 16$^{\prime\prime}$ circle over the disk part of planet." (Continuum emission towards Saturn); "We do not estimate the flux densities of rings because it is very difficult due to their complex structure." (Continuum emission towards Saturn)
   - software: CASA 5.4.1
   - parameter: Continuum image at 856.19 um (350.14 GHz)  
  > "(350.14 GHz) wavelength continuum emission image of the gas planet Saturn" (Continuum emission towards Saturn)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract limb spectra and measure HCN line shifts**: Extract HCN J=4-3 spectra from 2.7 arcsec diameter circular regions on the eastern and western limbs of the cubes and read off the peak velocity shift from the theoretical line centre  
  > "We extract the molecular emission spectra from the eastern and western limbs of the spectral data cubes of Saturn." (Line emission towards Saturn); "diameter circular region in the eastern limb of Saturn centred at RA" (Line emission towards Saturn)
   - software: CASA 5.4.1
   - parameter: Eastern limb aperture centred at RA 18h35m51.873s, Dec -22d19m27.982s (J2000); western limb at RA 18h33m53.128s, Dec -22d19m29.406s  
  > "= (18$^{h}$35$^{m}$51.873$^{s}$), Dec (J2000) = (–22$^\circ$19$^{\prime}$27$^{\prime\prime}$.982)" (Line emission towards Saturn)
   - parameter: Zero velocity is the theoretical HCN peak at 354.505 GHz  
  > "the center position (i.e., 0 km s$^{-1}$) is the theoretical peak position of the HCN (354.505 GHz)" (Line emission towards Saturn)
   - assumption: Line shifts attributed to strong stratospheric winds between the east and west limbs  
  > "This spectral shift could have been caused by strong stratospheric winds between the eastern and western limbs of Saturn." (Line emission towards Saturn)
   - fitting: _not stated_
   - validation: Shifts compared with Cavalié et al. 2010 model results  
  > "Our estimated shift in the HCN emission line for both the eastern and western limbs is similar to that of (cite: ca10)." (Line emission towards Saturn)
5. **Fit HCN abundance with PSG forward model**: Fit PSG model spectra (line-by-line and correlated-k) to the observed limb spectra, with the line velocity fixed per limb, to derive the HCN vertical mixing ratio  
  > "PSG is also able to fit the modelled spectra of the detected molecules over the observed spectra to determine the abundance of those molecules" (Determination of the abundance of HCN); "During the spectral fitting, the velocity of the western limb spectra is fixed at 8.36 km s$^{-1}$." (Determination of the abundance of HCN)
   - software: Planetary Spectrum Generator (PSG)
   - parameter: Pressure levels of the vertical structure 10 to 100 (ubar as printed), 60 atmospheric layers  
  > "the pressure levels of the vertical atmospheric structure ranged from 10 to 100" (Determination of the abundance of HCN); "with 60 atmospheric layers" (Determination of the abundance of HCN)
   - parameter: Velocity fixed at 8.36 km/s (west) and -9.26 km/s (east)  
  > "Similarly, the velocity of the eastern limb spectra is fixed at –9.26 kms$^{-1}$." (Determination of the abundance of HCN)
   - assumption: Disk-averaged temperature profile from Lellouch et al. 1984; layers from Moses 2005; HITRAN line parameters  
  > "For the temperature profile, we used the disk-averaged retrieved result from (cite: lel84)." (Determination of the abundance of HCN); "We used the HITRAN molecular database for spectroscopic parameters" (Determination of the abundance of HCN)
   - fitting: Least-squares fit of model to observed spectrum, method as in Iino et al. 2020; priors and likelihood not stated  
  > "we used the least-squares method, which is well described in (cite: ii20)" (Determination of the abundance of HCN)
   - validation: Compared with the earlier simulated VMR of 3.58 ppb  
  > "which is nearly similar to our observed abundance of HCN in the atmosphere of Saturn" (Determination of the abundance of HCN)
6. **Retrieve vertical HCN and temperature profiles**: Optimal-estimation retrieval with PSG over 10 bar to 100 ubar, 60 layers, using the fitted limb abundances as input; default PSG profiles for other species  
  > "We used the optimal estimation method to compute the retrieval model of HCN using the PSG." (Retrieval profile of HCN); "To compute the retrieval profile, we used the abundance of HCN at 6.19 ppb (western limb) and 2.90 ppb (eastern limb) in the PSG." (Retrieval profile of HCN)
   - software: Planetary Spectrum Generator (PSG)
   - parameter: Temperature profile from Lellouch et al. 1984; spectroscopy from HITRAN; 60 layers  
  > "The temperature profile derived from the disk-averaged result was obtained from (cite: lel84)." (Retrieval profile of HCN); "we used 60 atmospheric layers in the PSG (cite: mos05)" (Retrieval profile of HCN)
   - assumption: Default PSG vertical profiles for CH4, C2H6, C2H2, NH3 and NH4SH  
  > "we use default values available in PSG (cite: mos05)" (Retrieval profile of HCN)
   - fitting: Optimal estimation (a priori and covariance not stated)  
  > "We used the optimal estimation method to compute the retrieval model of HCN using the PSG." (Retrieval profile of HCN)
   - validation: _not stated_
7. **Map the spatial distribution of HCN**: Integrate the line cubes with IMMOMENTS over the velocity range where HCN is detected and overplot on the continuum map  
  > "We create an integrated emission map of the HCN in Saturn using the task `IMMOMENTS` in CASA." (Spatial distribution of HCN in Saturn); "We overplot the integrated emission map of HCN over the 856.19" (Spatial distribution of HCN in Saturn)
   - software: CASA 5.4.1, immoments
   - fitting: _not stated_
   - validation: _not stated_
8. **Compare abundance with Jupiter and infer formation pathway**: Compare the derived Saturn HCN mixing ratio range with Jupiter's value from Tokunaga et al. 1981 and with the laboratory result of Raulin et al. 1979  
  > "we calculated the mixing ratio of HCN in Saturn’s atmosphere to be (2.90–6.19) ppb." (Possible formation mechanism of HCN in the atmosphere of Saturn); "This implies that the laboratory experiment of (cite: rau79) is valid in the atmosphere of Saturn" (Possible formation mechanism of HCN in the atmosphere of Saturn)
   - assumption: Saturn has a much lower NH3 abundance than Jupiter, so a lower HCN abundance supports photolysis of CH4 and NH3  
  > "the abundance of HCN in Saturn is lower than that in Jupiter because Saturn’s atmosphere contains a much lower abundance of NH$_{3}$" (Possible formation mechanism of HCN in the atmosphere of Saturn)
   - fitting: _not stated_
   - validation: The authors say further photochemical modelling is needed  
  > "Further photochemical modelling is needed to establish the most efficient pathways for the production of HCN in the atmosphere of Saturn." (Possible formation mechanism of HCN in the atmosphere of Saturn)

## Software

- **CASA** 5.4.1: Data reduction with the ALMA standard pipeline, imaging and analysis  
  > "Common Astronomy Software Application (`CASA 5.4.1`) with a standard data reduction pipeline delivered by the ALMA observatory for data analysis and imaging" (Observation and data reductions)
- **importasdm** : Import ALMA data into CASA  
  > "We imported the ALMA data into CASA using task `IMPORTASDM`." (Observation and data reductions)
- **setjy** : Flux calibrator model (Perley-Butler 2017)  
  > "with 5% accuracy using the task `SETJY` in CASA" (Observation and data reductions)
- **hifa_bandpassflag, hifa_flagdata** : Remove bad antenna data  
  > "We applied the CASA pipeline tasks `hifa_bandpassflag` and `hifa_flagdata` to remove the bad antenna data." (Observation and data reductions)
- **mstransform** : Split the target data with all available rest frequencies  
  > "we separated the target dataset into another dataset using the task `MSTRANSFORM` with all available rest frequencies." (Observation and data reductions)
- **tclean** : Continuum image (hogbom) and spectral cubes  
  > "we used task `TCLEAN` with the `HOGBOM` algorithm to create the continuum image of Saturn." (Observation and data reductions)
- **uvcontsub** : Continuum subtraction  
  > "we used the CASA task `UVCONTSUB` for continuum subtraction" (Observation and data reductions)
- **impbcor** : Primary beam correction  
  > "we applied the `IMPBCOR` task in the CASA" (Observation and data reductions)
- **immoments** : Integrated emission (moment) map of HCN  
  > "using the task `IMMOMENTS` in CASA" (Spatial distribution of HCN in Saturn)
- **Planetary Spectrum Generator (PSG)** : Radiative-transfer modelling, abundance fitting and optimal-estimation retrieval of HCN and temperature profiles  
  > "PSG is a radiative transfer suite for spectrum simulation of the solar planets, exoplanets, comets, and other minor objects in our solar system." (Determination of the abundance of HCN); "we computed the VMR retrieval profile of HCN using the PSG" (Retrieval profile of HCN)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum frequency of the Saturn continuum image | 350.14 GHz (856.19 um) | not stated | GHz | 2 | (350.14 GHz) wavelength continuum emission image of the gas planet Saturn |
| Continuum synthesized beam | 0.78 x 0.61 | not stated | arcsec | 2 | The synthesized beam size of the continuum image was 0.78$^{\prime\prime}\times$0.61$^{\prime\prime}$. |
| Disk-average continuum flux density of Saturn (excluding rings) | 1.60 | 0.35 | Jy/beam | 3 | The disk average (except ring) continuum flux density of Saturn is 1.60$\pm$0.35 Jy beam$^{-1}$. |
| HCN J=4-3 line shift, eastern limb | -9.2 (354.516 GHz) | not stated | km/s | 4 | we find that the HCN spectra in the eastern limb (red line) is shifted –9.2 km s$^{-1}$ (354.516 GHz) from the center |
| HCN J=4-3 line shift, western limb | 8.36 (354.494 GHz) | not stated | km/s | 4 | for the western limb (black line), the peak of the HCN is shifted to 8.36 km s$^{-1}$ (354.494 GHz) |
| HCN vertical mixing ratio, western limb | 6.19 | not stated | ppb | 5 | After spectral fitting, the derived vertical mixing ratios (VMR) of HCN towards the western and eastern limbs of Saturn are 6.19 ppb and 2.90 ppb, respectively. |
| HCN vertical mixing ratio, eastern limb | 2.90 | not stated | ppb | 5 | After spectral fitting, the derived vertical mixing ratios (VMR) of HCN towards the western and eastern limbs of Saturn are 6.19 ppb and 2.90 ppb, respectively. |
| Pressure level where the HCN VMR profile saturates | 0.001 | not stated | bar | 6 | we find that the VMR of HCN is saturated at a pressure level of 0.001 bar |
| Maximum altitude of HCN in the stratosphere | 475 | not stated | km | 6 | This means that the HCN molecule is distributed up to 475 km in the stratosphere of Saturn. |
| Retrieved temperature range within the HCN-containing pressure range | 100 to 250 | not stated | K | 6 | within this pressure level, the temperature varies between 100 and 250 K |

## Qualitative findings

- HCN J=4-3 emission arises from the eastern and western limbs; no line emission from the equatorial region  
  > "originates from both the eastern and western limbs of Saturn. We do not detect any line emissions from the equatorial region of Saturn." (Line emission towards Saturn)
- Channel maps indicate HCN circulating from east to west limb via the north pole  
  > "The channel maps clearly indicates the HCN molecule circulating from the eastern limb to the western limbs of Saturn via the north pole." (Line emission towards Saturn)
- The HCN integrated map is resolved  
  > "We observe that the integrated map of HCN is resolved because the line emitting region is larger than the synthesized beam of the integrated emission map." (Spatial distribution of HCN in Saturn)
- No CH2NH or other complex species chemically linked to HCN observed  
  > "We did not observe any other complex molecules that are chemically connected to HCN, such as CH$_{2}$NH." (Line emission towards Saturn)

## Claim tuples

- H: Is HCN detectable in Saturn's atmosphere at submillimetre wavelengths with ALMA? | E: Reduced archival ALMA Band 7 data and extracted spectra from the east and west limbs | R: HCN J=4-3 emission at 354.505 GHz seen on both limbs, Doppler shifted by -9.2 and 8.36 km/s | F: First detection of the HCN rotational emission line in Saturn's atmosphere | **supported**
- H: What is the HCN abundance on the two limbs? | E: Least-squares fit of PSG model spectra to the limb spectra | R: 6.19 ppb (west) and 2.90 ppb (east) | F: Abundances are similar to the 3.58 ppb earlier model value | **supported**
- H: How is HCN distributed vertically and what is the temperature structure? | E: PSG optimal-estimation retrieval of VMR and TP profiles | R: VMR saturates at 0.001 bar, about 475 km; temperature 100-250 K within that range | F: HCN extends up to 475 km in the stratosphere | **supported**
- H: Do the opposite limb line shifts trace stratospheric winds? | E: Measured the peak velocity of HCN on each limb and compared with a published model | R: -9.2 km/s east and 8.36 km/s west, similar to Cavalié et al. 2010 | F: Shifts could be due to strong stratospheric winds | **partially**
- H: How does HCN form in Saturn's atmosphere? | E: Compared the derived mixing ratio (2.90-6.19 ppb) with Jupiter's HCN abundance and a laboratory experiment | R: Saturn HCN abundance slightly lower than Jupiter's | F: Photolysis of CH4 and NH3 is claimed to produce the HCN | **partially**

## Reasoning

- Why this data: Archival data originally taken to measure Saturn's stratospheric winds with HCN and CO lines; earlier users did not study HCN abundance, vertical distribution or formation  
  > "The objective of this observation was to directly measure Saturn’s stratospheric winds using the emission lines of hydrogen cyanide (HCN)" (Observation and data reductions); "also used this data, but the authors did not focus on studying the mixing ratio, vertical distribution, and formation pathways of HCN" (Observation and data reductions)
- Why this method: Submillimetre heterodyne observations are considered the best way to search for HCN in Saturn  
  > "the submillimeter spectral range is the best for searching for evidence of HCN in Saturn’s atmosphere" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of short spacings filters out the disk flux, so only limb emission is preserved  
  > "As a result of the lack of short spacing with the interferometer, the disk flux of Saturn is filtered out, and only the emission from the limbs is preserved." (Observation and data reductions)
- Limitation (authors): Ring continuum flux not estimated because of complex structure  
  > "We do not estimate the flux densities of rings because it is very difficult due to their complex structure." (Continuum emission towards Saturn)
- Limitation (authors): Formation pathways need further photochemical modelling  
  > "Further photochemical modelling is needed to establish the most efficient pathways for the production of HCN in the atmosphere of Saturn." (Possible formation mechanism of HCN in the atmosphere of Saturn)
- Caveat (inferred, ours): No uncertainties are given on the line shifts, VMRs, altitude or temperature range, and no detection significance or rms is quoted.
- Caveat (inferred, ours): Eastern line shift is given as -9.2 km/s in one place and fixed at -9.26 km/s in the fit.
- Caveat (inferred, ours): Disk flux filtering by the interferometer is not shown to be included in the forward model, so the retrieved VMR and profile may be biased.
- Caveat (inferred, ours): The temperature profile is a 1984 disk-averaged one, not limb-specific, and the retrieved 'temperature of HCN' is just the assumed atmospheric profile.
- Caveat (inferred, ours): Only 476 s on source and a single HCN line, so the vertical profile is weakly constrained and the 475 km extent may reflect priors.
- Caveat (inferred, ours): The formation-pathway claim rests on a qualitative Saturn versus Jupiter abundance comparison, not on chemical modelling.
- Caveat (inferred, ours): The ozone line removal at 355.01 GHz sits close to the HCN window and its effect on the HCN baseline is not discussed.

## Reproducibility

- Data public (paper): Archival ALMA data downloaded from the ALMA archive (project 2017.1.00636.S)  
  > "After downloading the archival raw data of Saturn from the ALMA archive" (Observation and data reductions); "ADS /JAO.ALMA#2017.1.00636.S" (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: tclean imaging parameters (cell, size, weighting, masks, thresholds, channel widths)
- Missing: Line-free channel selection for continuum and UVCONTSUB
- Missing: PSG input configuration, fit parameters, retrieval prior and error treatment
- Missing: Velocity range for the moment map
- Missing: Uncertainty estimates for all derived numbers
- Data volume (inferred): One short Band 7 execution block with 44 antennas and four spectral windows; raw data likely a few to tens of GB (estimate).
- Score (inferred): 3/5, Public archival data, named CASA tasks and a fully numeric headline result, but imaging parameters, PSG setup and retrieval priors are missing and no uncertainties are given.
- Rediscovery candidate: yes, Data are public, the aperture positions and line frequency are given, PSG is public, and the main results (VMR, shifts, altitude, temperature range) are numeric; exact numbers would need the missing PSG settings.

## Links

- Method: McMullin et al. 2007, ASP Conf. Ser. 376, 127 (cite: m07) (CASA reference)
- Method: Villanueva et al. 2018, JQSRT, 217, 86 (cite: vil18) (Planetary Spectrum Generator)
- Method: Iino et al. 2020, ApJL, 903, L1 (cite: ii20) (Least-squares spectral fitting method and ALMA HCN in Neptune)
- Companion: Benmahi et al. 2022, A&A, 666, A117 (cite: ben22) (Earlier paper using the same ALMA Saturn data (stratospheric winds))
- Companion: Lellouch, Encrenaz & Combes 1984 (cite: lel84) (Temperature profile and simulated HCN VMR in Saturn)
- Companion: Cavalié et al. 2010, A&A, 510, A88 (cite: ca10) (Model line shifts for east and west limbs used for comparison)
- Related: ALMA project 2017.1.00636.S (PI Fouchet)

## Checks

```json
{
 "quotes": 122,
 "quotes_ok": 122,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 79,
  "rate": 0.738
 },
 "evidence_ok": true
}
```
