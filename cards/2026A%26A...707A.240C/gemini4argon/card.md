# Observations of the temporal evolution of Saturn's stratosphere following the Great Storm of 2010─2011: II. Latitudinal distribution of CO and stratospheric winds

`2026A&A...707A.240C` | Astronomy and Astrophysics 2026 | first author: Cavalié, T. | arXiv: 2601.20359 | DOI: 10.1051/0004-6361/202557032

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Assess whether Saturn's 2010-2011 stratospheric beacon perturbed the CO distribution and measure how the vortex perturbed the stratospheric wind regime.  
  > "We aim to assess whether the beacon induced any perturbation in another oxygen species, namely CO. A second goal is to measure how the vortex perturbed the stratospheric wind regime." (Abstract)
- Target **Saturn**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00808.S
- bands: _not stated_
- frequencies and spectral setup: 230.538 GHz, spectral resolution 244 kHz  
  > "We observed the CO (J=2-1) line at 230.538 GHz emanating from Saturn as part of project 2011.0.00808.S" (January 2012 ALMA observations); "All spectra were recorded with a spectral resolution of 244 kHz." (January 2012 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 17, 16, and 18 antennas  
  > "on January 9, 14, and 22, 2012, with 17, 16, and 18 antennas, respectively, in the Cycle 0 compact configuration." (January 2012 ALMA observations)
- configurations: Cycle 0 compact configuration  
  > "on January 9, 14, and 22, 2012, with 17, 16, and 18 antennas, respectively, in the Cycle 0 compact configuration." (January 2012 ALMA observations)
- baselines: 18 m to 268 m  
  > "The baselines extended from 18 m to 268 m." (January 2012 ALMA observations)
- angular resolution: 2.04" x 1.34" (PA -9.9 deg)  
  > "The compact configuration used for these observations resulted in a synthetic beam of 2.04” $\times$ 1.34” with a position angle of -9.9$^\circ$." (January 2012 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 6.5 mJy/beam per 244 kHz channel  
  > "The final spectral noise is 6.5 mJy/beam per spectral channel." (January 2012 ALMA observations)
- time on source: ~55 minutes  
  > "The total on-source time was $\sim$55 minutes." (January 2012 ALMA observations)
- observing dates: January 9, 14, and 22, 2012 (Jan 9 discarded from final coadd)  
  > "We observed the CO (J=2-1) line at 230.538 GHz emanating from Saturn as part of project 2011.0.00808.S on January 9, 14, and 22, 2012" (January 2012 ALMA observations); "The lack of additional bandpass calibrator observations on January 9 significantly reduces the final line sensitivity in these observations, and we choose to discard them from the final coadd." (January 2012 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: CO J=3-2 (345.796 GHz)
- Other facility **Submillimeter Array (SMA)**: CO (J=3-2) line observations at 345.796 GHz on March 13, 2010 (project 2009B-S037)  
  > "We targeted the emission of the CO (J=3-2) line at 345.796 GHz from Saturn’s atmosphere with the Submillimeter Array, as part of project 2009B-S037 in a single track on March 13, 2010." (March 2010 SMA observations)
- Other facility **JPL Horizons**: Ephemerides for observatory-planet relative velocity correction  
  > "requires final correction by the observatory-planet relative velocity, which we obtain from JPL Horizons ephemerides." (March 2010 SMA observations)
- Other facility **JPL Spectroscopy database**: Spectroscopic constants of NH3, PH3, and CO lines  
  > "The spectroscopic constants of the NH$_3$, PH$_3$, and CO lines modeled in this paper have been extracted from the JPL Spectroscopy database." (Radiative transfer model)
- External data: Seasonal altitude-latitude thermal field retrieved from Cassini/CIRS measurements  
  > "For the SMA data from March 2010, we use the seasonal altitude-latitude thermal field retrieved from Cassini/CIRS measurements presented in (cite: Fletcher2018b)." (Thermal fields) [from (cite: Fletcher2018b)]
- External data: Temperatures retrieved from beacon-specific observations on January 27, 2012, and beacon western drift  
  > "(ii) temperatures retrieved as a function of altitude, latitude, and longitude from beacon-specific observations carried out on January 27, 2012, by (cite: Fletcher2012b)." (Thermal fields) [from (cite: Fletcher2012b)]
- External data: Physical vertical profile of CO from a ~220-year-old comet impact  
  > "we choose to adopt the physical profile of (cite: Cavalie2010) derived from atmospheric transport following a comet impact occurring $\sim$220 years before the observations" (Background composition and CO distribution model) [from (cite: Cavalie2010)]
- External data: Line broadening parameters for NH3, PH3, and CO  
  > "We have computed the line broadening parameters following (cite: Fletcher2007) for NH$_3$, (cite: Levy1993; Levy1994) for PH$_3$, and (cite: Dick2009) for CO." (Radiative transfer model) [from (cite: Fletcher2007), (cite: Levy1993; Levy1994), (cite: Dick2009)]
- External data: 2018 ALMA stratospheric wind measurements of Saturn  
  > "The measurements confirm the presence of the broad prograde equatorial jet initially detected by (cite: Benmahi2022; Benmahi2025) in the stratosphere." (Stratospheric winds during the storm) [from (cite: Benmahi2022; Benmahi2025)]

## Processing

### Calibration

- pipeline or manual: manual in CASA 4.7.2  
  > "We reduced the data with the Common Astronomy Software Applications (CASA) version 4.7.2." (January 2012 ALMA observations)
- casa version: 4.7.2  
  > "We reduced the data with the Common Astronomy Software Applications (CASA) version 4.7.2." (January 2012 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: performed on continuum and spectral data; Jan 22 amplitudes rescaled to match Jan 14 total planet flux (978 Jy vs 951 Jy) after self-calibration  
  > "There is a small difference remaining on total planet flux between the two dates: 978$\pm$14 Jy on January 14 versus 951$\pm$12 Jy on January 22, both after selfcalibration." (January 2012 ALMA observations); "We further processed the data to produce selfcalibrated continuum and continuum-subtracted spectral images." (January 2012 ALMA observations)

### Imaging

- task: clean  
  > "We used the multiscale algorithm in the clean process, with scales relevant to the features expected in the Saturn image" (January 2012 ALMA observations)
- deconvolver: multiscale and Clark algorithm  
  > "We used the multiscale algorithm in the clean process, with scales relevant to the features expected in the Saturn image (for example, 1” for the limb spectral data, and larger scales for the continuum data)." (January 2012 ALMA observations); "We chose the Clark algorithm to compute the synthesized beam." (January 2012 ALMA observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: combination of planet ellipse and ring ellipse masks for continuum; planet ellipse mask only for spectral cube  
  > "We cleaned the data within a combination of planet ellipse and ring ellipse masks for the continuum image, and only within a planet ellipse mask for the spectral cube, because there is no line emission in the rings." (January 2012 ALMA observations)
- multiscale scales: 1" for limb spectral data, larger scales for continuum data  
  > "with scales relevant to the features expected in the Saturn image (for example, 1” for the limb spectral data, and larger scales for the continuum data)." (January 2012 ALMA observations)
- continuum subtraction: subtracted from the visibilities  
  > "Similarly to the SMA data also, the continuum was subtracted from the visibilities to produce the continuum-subtracted spectral cube." (January 2012 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.04" x 1.34", PA -9.9 deg (ALMA); 5.0" x 4.7", PA 71.4 deg (SMA)  
  > "The compact configuration used for these observations resulted in a synthetic beam of 2.04” $\times$ 1.34” with a position angle of -9.9$^\circ$." (January 2012 ALMA observations); "The synthesized beam realized from the visibility data was 5.0” $\times$ 4.7” with a position angle of 71.4$^\circ$." (March 2010 SMA observations)
- final rms: 6.5 mJy/beam per spectral channel (ALMA)  
  > "The final spectral noise is 6.5 mJy/beam per spectral channel." (January 2012 ALMA observations)

### Inherited from earlier work

- Isothermal upward expansion of temperatures above 0.2 mbar and beacon longitude drift correction  
  > "Similarly to (cite: Lefour2025), we expanded the temperatures isothermally upward of the 0.2 mbar level" (Thermal fields); "We correct the beacon longitude to account for the beacon western drift (cite: Fletcher2012b) between January 14 and January 27 following (cite: Lefour2025)." (Thermal fields) [from (cite: Lefour2025)]
- Background composition of H2, He, CH4, NH3, and PH3, 3D line-by-line radiative transfer model, and ring emission/absorption parameters  
  > "The background composition we use in the radiative transfer calculations is similar to those used in (cite: Cavalie2019) and (cite: Lefour2025) for what concerns H$_2$, He, CH$_4$, NH$_3$, and PH$_3$." (Background composition and CO distribution model); "We use the line-by-line radiative transfer model of (cite: Cavalie2019), which accounts for the 3D ellipsoidal shape of Saturn." (Radiative transfer model); "All details relative to the various ring brightness temperatures and absorption coefficients can be found in (cite: Cavalie2019) (and references therein)." (Radiative transfer model) [from (cite: Cavalie2019) and (cite: Lefour2025)]
- Collision-induced absorption routines for H2-H2, H2-He, and H2-CH4 pairs  
  > "The continuum is mainly caused by the collision-induced absorption spectra of H$_2$-H$_2$, H$_2$-He, and H$_2$-CH$_4$ pairs. In this respect, we adopt the routines prescribed by (cite: Borysow1985; Borysow1988) and (cite: Borysow1986)." (Radiative transfer model) [from (cite: Borysow1985; Borysow1988) and (cite: Borysow1986)]
- Wind retrieval technique and systematics treatment  
  > "We use the wind retrieval technique developed by (cite: Cavalie2021) for ALMA observations of Jupiter. It was also applied to the May 2018 ALMA observations of Saturn (cite: Benmahi2022)" (Wind retrieval model) [from (cite: Cavalie2021) and (cite: Benmahi2022)]
- Temperature retrieval algorithm for equatorial semiannual oscillation  
  > "Using the retrieval algorithm of (cite: Fouchet2008) coupled with our radiative transfer model, we can better constrain the amplitude of the temperature oscillation" (CO meridional distribution in January 2012) [from (cite: Fouchet2008)]
- Wind contribution function calculation  
  > "The measured winds are located at the 0.2-1 mbar level (see Fig. 7), according to the wind contribution function calculation proposed by (cite: Lellouch2019)." (Stratospheric winds during the storm) [from (cite: Lellouch2019)]

### Not stated but needed to reproduce (our reading)

- Visibility weighting scheme (e.g., Briggs robust parameter) used during ALMA imaging
- Image pixel/cell size and image dimensions for ALMA and SMA cubes
- Self-calibration solution intervals and number of iterations for ALMA data
- Exact list of multiscale clean scales used for continuum imaging
- Specific parameters of the sine wave / polynomial fits used for baseline ripple removal on each extracted spectrum

## Analysis recipe

1. **Calibrate, concatenate, and image ALMA visibility data**: Calibrate bandpass, gain, phase, and flux; rescale uv distances and amplitudes of Jan 22 data to match Jan 14 apparent size and total flux; concatenate measurement sets; perform self-calibration, visibility continuum subtraction, and multiscale clean.  
  > "After the calibration of the bandpass, gain, phase, and flux, we corrected the variation of Saturn’s apparent size between January 14 and 22 by applying the relevant scaling factor on the uv distances in the January 22 data." (January 2012 ALMA observations); "We thus rescaled the January 22 amplitudes to obtain the same total planet flux as on January 14. This enabled us to concatenate the uv-tables from both dates into a single measurement set." (January 2012 ALMA observations); "We further processed the data to produce selfcalibrated continuum and continuum-subtracted spectral images." (January 2012 ALMA observations)
   - software: CASA
   - parameter: multiscale scale 1" for limb spectral data  
  > "We used the multiscale algorithm in the clean process, with scales relevant to the features expected in the Saturn image (for example, 1” for the limb spectral data, and larger scales for the continuum data)." (January 2012 ALMA observations)
   - assumption: No line emission in the rings  
  > "and only within a planet ellipse mask for the spectral cube, because there is no line emission in the rings." (January 2012 ALMA observations)
   - fitting: _not stated_
   - validation: Checked continuum model against observations within calibration uncertainties  
  > "We have thus checked that our continuum model, especially in the vicinity of the limb is consistent with the observations within calibration uncertainties (see Fig. 3)." (Radiative transfer model)
2. **Extract limb spectra and remove residual baseline ripples**: Apply pointing offset correction (+0.27" RA, +0.33" Dec for ALMA), extract spectra along the 1-bar planetary limb oversampling the synthesized beam by a factor of 4, and remove standing waves using sine waves or polynomial fits.  
  > "We choose to oversample the synthesized beam by a factor of 4, yielding 50 spectra along the Saturn limb to analyze." (March 2010 SMA observations); "We remove those either using sine waves, or alternatively polynomial fits because the narrow bandwidth sometimes make it difficult to constrain sine wave fit parameters." (March 2010 SMA observations); "We apply the relevant pointing correction before extracting the limb spectra, still applying a beam oversampling factor of 4" (January 2012 ALMA observations)
   - parameter: beam oversampling factor of 4; pointing offset +0.27" RA, +0.33" Dec (ALMA); primary beam correction factor 1.25 (SMA)  
  > "We consequently apply a primary beam correction of 1.25 to the flux densities of the continuum-subtracted spectra extracted at the limb from the spectral cube." (March 2010 SMA observations); "Using the continuum image (see Fig. 3), we find a residual pointing offset of +0.27” in right ascension and +0.33” in declination" (January 2012 ALMA observations); "We apply the relevant pointing correction before extracting the limb spectra, still applying a beam oversampling factor of 4" (January 2012 ALMA observations)
   - assumption: Limb defined as the 1-bar level  
  > "For spectral analysis of the CO line emission, we therefore only extract spectra along the limb, defined here as the 1-bar level." (March 2010 SMA observations)
   - fitting: Sine wave or polynomial fits to baseline ripples  
  > "We remove those either using sine waves, or alternatively polynomial fits because the narrow bandwidth sometimes make it difficult to constrain sine wave fit parameters." (March 2010 SMA observations)
   - validation: _not stated_
3. **Model radiative transfer and derive CO meridional distribution**: Use a 3D line-by-line radiative transfer model with Cassini/CIRS thermal fields and scale a 220-year-old comet impact vertical profile to fit limb spectra and derive CO mole fraction at 0.3 mbar.  
  > "we choose to adopt the physical profile of (cite: Cavalie2010) derived from atmospheric transport following a comet impact occurring $\sim$220 years before the observations, and to scale it to fit the spectra at each limb position" (Background composition and CO distribution model); "We use the line-by-line radiative transfer model of (cite: Cavalie2019), which accounts for the 3D ellipsoidal shape of Saturn." (Radiative transfer model)
   - parameter: N=30 spectral points for SMA, N=100 for ALMA; selection threshold chi^2/N < 9 (and < 4)  
  > "using the pointings for which the best fit for a given pointing on the limb satisfies $\chi^2/N$$<$9, where $N$ is the number of spectral data points used for the $\chi^2$ computation" (Prestorm meridional distribution); "For SMA data, $N$ is taken as 30, so that $\chi^2$ is computed over $\sim$25 MHz. For ALMA data, $N$ is taken as 100, because the spectral resolution is about four times better." (Footnote 3)
   - assumption: Tropospheric CO (1.2 ppb) is neglected; temperatures expanded isothermally upward of 0.2 mbar  
  > "Similarly to (cite: Lefour2025), we expanded the temperatures isothermally upward of the 0.2 mbar level" (Thermal fields); "For the CO vertical profile, we neglect any tropospheric CO (cite: Fouchet2017; Cavalie2024) in our calculations, because the tropospheric abundance of 1.2 ppb only produces a negligible and very broad absorption" (Background composition and CO distribution model)
   - fitting: Chi-square minimization rescaling the vertical profile  
  > "using the pointings for which the best fit for a given pointing on the limb satisfies $\chi^2/N$$<$9, where $N$ is the number of spectral data points used for the $\chi^2$ computation" (Prestorm meridional distribution)
   - validation: Tested stricter chi^2/N < 4 criterion and compared eastern and western limbs  
  > "When using a more restrictive criterion of $\chi^2/N$$<$4 to compute the mean CO mole fraction at 0.3 mbar, we find (1.4$\pm$0.8)$\times 10^{-7}$." (CO meridional distribution in January 2012)
4. **Retrieve stratospheric winds from Doppler shifts of ALMA limb spectra**: Fit a parametrized analytical function to observed CO lines within +/-1.5 MHz of the line peak to measure Doppler shifts, subtract beam-convolved planet rotation, and deproject line-of-sight velocities to zonal wind speeds.  
  > "It was also applied to the May 2018 ALMA observations of Saturn (cite: Benmahi2022), and it uses a parametrized analytical function to fit the observed lines and derive the wind-induced spectral shift." (Wind retrieval model); "After careful assessment, we thus choose to apply the wind retrieval algorithm only to a frequency range comprised within $\pm$1.5 MHz of the line peak." (Wind retrieval model); "The zonal wind speeds, after correcting for the projection factor caused by the sub-Earth point latitude in January 2012 (15.1$^\circ$N) and the relative longitude with respect to the central meridian, are displayed in Figs. 14 and 15" (Stratospheric winds during the storm)
   - parameter: Fitting frequency range within +/- 1.5 MHz of line peak; sub-Earth latitude 15.1 deg N  
  > "After careful assessment, we thus choose to apply the wind retrieval algorithm only to a frequency range comprised within $\pm$1.5 MHz of the line peak." (Wind retrieval model); "after correcting for the projection factor caused by the sub-Earth point latitude in January 2012 (15.1$^\circ$N)" (Stratospheric winds during the storm)
   - assumption: Systematic uncertainty of ~50 m/s caused by spectral baseline removal  
  > "The uncertainties in the derived values include the retrieval uncertainty (directly derived from the spectral noise) and other systematics discussed in detail in (cite: Cavalie2021), especially $\sim$50 m/s caused by the spectral baseline removal." (Stratospheric winds during the storm)
   - fitting: Parametrized analytical function fit over +/- 1.5 MHz  
  > "it uses a parametrized analytical function to fit the observed lines and derive the wind-induced spectral shift." (Wind retrieval model)
   - validation: Compared eastern and western limbs and compared with 2018 ALMA wind measurements and Cassini/CIRS thermal winds  
  > "The zonal wind speeds, after correcting for the projection factor caused by the sub-Earth point latitude in January 2012 (15.1$^\circ$N) and the relative longitude with respect to the central meridian, are displayed in Figs. 14 and 15 before and after averaging of the two limbs." (Stratospheric winds during the storm)

## Software

- **CASA** 4.7.2: Data reduction, calibration, uv-scaling, self-calibration, continuum subtraction, and multiscale clean imaging of the ALMA observations  
  > "We reduced the data with the Common Astronomy Software Applications (CASA) version 4.7.2." (January 2012 ALMA observations)
- **AIPS** : Imaging of the continuum-subtracted SMA visibility data  
  > "After continuum subtraction, the visibility data for the CO line spectral window were exported into AIPS (Astronomical Image Processing System) for imaging." (March 2010 SMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total planet continuum flux on January 14, 2012 (ALMA) | 978 | 14 | Jy | 1 | There is a small difference remaining on total planet flux between the two dates: 978$\pm$14 Jy on January 14 versus 951$\pm$12 Jy on January 22, both after selfcalibration. |
| Total planet continuum flux on January 22, 2012 (ALMA) | 951 | 12 | Jy | 1 | There is a small difference remaining on total planet flux between the two dates: 978$\pm$14 Jy on January 14 versus 951$\pm$12 Jy on January 22, both after selfcalibration. |
| Mean CO mole fraction at 0.3 mbar in March 2010 (SMA, chi^2/N < 9) | 1.7e-7 | 1.2e-7 | dimensionless | 3 | We can then only derive a mean CO mole fraction at the 0.3 mbar level, i.e., where the contribution function peaks, of (1.7$\pm$1.2)$\times 10^{-7}$ |
| Mean CO mole fraction at 0.3 mbar in January 2012 (ALMA, chi^2/N < 9) | 1.7e-7 | 0.7e-7 | dimensionless | 3 | The average CO mole fraction implied by the adopted and rescaled 220-year-old-comet-impact vertical profile is (1.7$\pm$0.7)$\times 10^{-7}$ at 0.3 mbar, i.e., where the contribution functions peak.; The CO mole fraction at 0.3 mbar is (1.7$\pm$0.7)$\times 10^{-7}$, when using the pointings for which the best fit satisfies $\chi^2/N$$<$9 and excluding those affected by ring shadowing. |
| Mean CO mole fraction at 0.3 mbar in January 2012 (ALMA, chi^2/N < 4) | 1.4e-7 | 0.8e-7 | dimensionless | 3 | When using a more restrictive criterion of $\chi^2/N$$<$4 to compute the mean CO mole fraction at 0.3 mbar, we find (1.4$\pm$0.8)$\times 10^{-7}$. |
| Prograde jet velocity at 50 deg S | 135 | 60 | m.s^-1 | 4 | We can identify two prograde jets, centered around 50$^\circ$S and 40$^\circ$S, with speeds of 135$\pm$60 m.s$^{-1}$ and 210$\pm$60 m.s$^{-1}$. |
| Prograde jet velocity at 40 deg S | 210 | 60 | m.s^-1 | 4 | We can identify two prograde jets, centered around 50$^\circ$S and 40$^\circ$S, with speeds of 135$\pm$60 m.s$^{-1}$ and 210$\pm$60 m.s$^{-1}$. |
| Equatorial prograde jet slowing relative to 2018 | 100 to 200 | not stated | m.s^-1 | 4 | The equatorial prograde jet is 100 to 200 m.s$^{-1}$ slower, and broader in latitude, than in quiescent conditions. |
| Beacon anticyclonic wind peak speed on eastern limb (33-47 deg N) | 60 | 15 | m.s^-1 | 4 | The peaks are symmetric in speed with values of 60$\pm$15 m.s$^{-1}$. |
| Retrograde flow speed on western limb (30-45 deg N) | -50 | 20 | m.s^-1 | 4 | On the opposite limb, the winds are tentatively found retrograde with an average speed of -50$\pm$20 m.s$^{-1}$ between 30$^\circ$N and 45$^\circ$N. |
| Prograde jet velocity at 50-67 deg N | 140 | 45 | m.s^-1 | 4 | A broad 140$\pm$45 m.s$^{-1}$ prograde jet, not seen in the thermal wind of (cite: Fletcher2012b) but evident as very strong windshear in Fig. 4 of (cite: Fletcher2018b), extends from 50$^\circ$N to 67$^\circ$N. |
| Retrograde polar jet peak velocity at 74 deg N | -220 | 80 | m.s^-1 | 4 | except a narrower retrograde jet that is located around 74$^\circ$N with a peak velocity of -220$\pm$80 m.s$^{-1}$. |

## Qualitative findings

- The meridional distribution of CO in Saturn's stratosphere is homogeneous within uncertainties and shows no significant perturbation in the beacon region.  
  > "Despite limitations resulting from the removal of baseline ripples, we find a relatively constant meridional distribution of CO." (Abstract); "We also find that the CO abundance has not been noticeably altered in the beacon." (Abstract)
- A ~0.1 Jy/beam CO absorption feature is detected at equatorial latitudes on the disk in the ALMA data, caused by a stratospheric thermal inversion associated with Saturn's semiannual oscillation.  
  > "An absorption feature of $\sim$0.1 Jy/beam is consistently detected at equatorial and near-equatorial latitudes from east to west." (CO meridional distribution in January 2012)
- The stratospheric beacon signature is tentatively detected as an anticyclonic wind feature sitting on a background retrograde flow.  
  > "Despite limitations in latitudinal resolution, we tentatively detect the signature of the beacon in the form of an anticyclone sitting on a retrograde flow." (Conclusion)

## Claim tuples

- H: Saturn's 2010-2011 stratospheric beacon and associated vertical winds altered the stratospheric CO distribution locally, similar to hydrocarbons and water. | E: Mapped CO (J=3-2) with SMA in March 2010 and CO (J=2-1) with ALMA in January 2012, fitting limb spectra with a rescaled comet-impact vertical profile. | R: Mean CO mole fraction at 0.3 mbar is (1.7+/-0.7)x10^-7 with a homogeneous meridional distribution and no significant difference between the storm region (20-50 deg N eastern vs western limb) and quiescent regions. | F: The CO abundance was not noticeably altered in the beacon. | **refuted**
- H: The stratospheric beacon vortex perturbed the stratospheric wind regime as an anticyclone drifting in a retrograde background flow. | E: Retrieved Doppler winds at 0.2-1 mbar from January 2012 ALMA CO (J=2-1) limb spectra. | R: Detected a retrograde peak (33-40 deg N) and prograde peak (40-47 deg N) of 60+/-15 m.s^-1 on the eastern limb, and a retrograde flow of -50+/-20 m.s^-1 on the western limb between 30 and 45 deg N. | F: The beacon is tentatively detected as an anticyclonic feature sitting on a retrograde flow, explaining its retrograde drift rate. | **supported**
- H: Storm-induced temperature perturbations injected westward momentum into the equatorial stratosphere, slowing the equatorial prograde jet. | E: Measured equatorial zonal wind speeds from January 2012 ALMA CO (J=2-1) Doppler shifts and compared them with May 2018 ALMA measurements. | R: The equatorial prograde jet in January 2012 is weaker by ~100 m.s^-1 in the southern part and up to 200 m.s^-1 in the northern hemisphere (0-20 deg N), and broader (extending to ~30 deg N), compared to 2018. | F: Confirms the slowing effect on the equatorial jet resulting from storm-induced temperature perturbations. | **supported**
- H: High-latitude and southern hemisphere stratospheric jets exist on Saturn, including a polar jet potentially linked to auroral activity or polar vortex dissipation. | E: Measured zonal wind profiles from 60 deg S to 85 deg N using January 2012 ALMA CO (J=2-1) limb spectra. | R: Detected prograde jets at 50 deg S (135+/-60 m.s^-1), 40 deg S (210+/-60 m.s^-1), and 50-67 deg N (140+/-45 m.s^-1), and a narrow retrograde jet at 74 deg N (-220+/-80 m.s^-1). | F: Several stratospheric prograde jets and a northern polar retrograde jet are detected for the first time, though their exact dynamical or auroral origin requires higher-resolution follow-up. | **supported**

## Reasoning

- Why this data: Interferometric millimeter/submillimeter heterodyne spectroscopy provides the spatial and spectral resolution required to resolve Saturn's limb CO emission and measure wind-induced Doppler shifts; observations were scheduled when the beacon was on the eastern limb to maximize S/N and limit longitudinal smearing.  
  > "The retrieval of stratospheric winds from spectral line observations requires the measurement of Doppler shifts induced by the winds on the spectral lines for a set of positions on the planet. Heterodyne spectroscopy in the millimeter range with an interferometer offers the necessary spatial and spectral resolutions to do so." (Introduction); "The observations were scheduled when Saturn’s beacon was located at the planetary eastern limb to increase S/N and limit apparent longitudinal smearing in the final images." (January 2012 ALMA observations)
- Why this method: Adopted a fixed template CO vertical profile because baseline ripple removal altered the broad line wings; restricted wind fitting to +/-1.5 MHz around the line peak to avoid line asymmetry caused by mixing disk and limb lines of sight within the ~1.7" beam.  
  > "Also, because of the limited bandpass quality of the SMA data, and to a less pronounced level, of the ALMA data, we cannot fully rely on the broad wing shape of the lines after the baseline ripple removal stage. We thus cannot reliably constrain the CO vertical profile." (Background composition and CO distribution model); "After careful assessment, we thus choose to apply the wind retrieval algorithm only to a frequency range comprised within $\pm$1.5 MHz of the line peak. This enables to have sufficient data points for the fit while using only the more symmetric part of the observed line." (Wind retrieval model)
- Alternative: Discarded January 9, 2012 ALMA observations from the final coadd because no additional bandpass calibration observations were executed on that date, reducing line sensitivity.  
  > "The lack of additional bandpass calibrator observations on January 9 significantly reduces the final line sensitivity in these observations, and we choose to discard them from the final coadd." (January 2012 ALMA observations)
- Alternative: Rejected applying the wind retrieval procedure to the 2010 SMA data because standing wave removal and lower spectral resolution caused uncertainties of several 100 m/s.  
  > "On the other hand, we choose not to apply it to the SMA data owing to the continuum ripple limitations. Their subtraction results in much too large uncertainties (several 100 m.s$^{-1}$) for a meaningful assessment of the stratospheric winds in 2010." (Wind retrieval model)
- How they decided it was enough: _not stated_
- Limitation (authors): Baseline ripple removal removed part of the broad wings of the CO line, limiting the quality of spectral fits and preventing retrieval of the CO vertical profile.  
  > "The limited quality of the fits is most probably a result from the baseline ripple removal stage of the data reduction, which removed part of the broad wings of the CO line." (Conclusion)
- Limitation (authors): Lack of short spacings in ALMA interferometric visibilities filters out disk-center flux, making quantitative analysis of the equatorial CO absorption feature uncertain.  
  > "The lack of short spacings in the interferometric visibilities inherently filters out a significant fraction of the total flux in the disk-center data. Consequently, the shape of the spectrum remains quite uncertain." (CO meridional distribution in January 2012)
- Limitation (authors): Coarse spatial resolution (~1.7" beam, PSR ~10, ~8 deg in latitude at the beacon) mixes disk and limb lines of sight, smooths wind peaks, and prevents detection of the quasiperiodic oscillation.  
  > "With a $\sim$1.7” beam, we have a planet spatial resolution (planet size/beam size; PSR) of about 10, when the 2018 observations of (cite: Benmahi2022) had a PSR of $\sim$40. This lower PSR results in mixing the contributions of disk and limb line-of-sights (LOS)" (Wind retrieval model); "(iii) our limited spatial resolution of about 8$^\circ$ at the latitude of the beacon which smooths wind peaks" (Stratospheric winds during the storm)
- Limitation (authors): Integration time of ~1 hr smooths velocities over 30 deg in longitude.  
  > "(iv) the integration time of 1 hr which smooths the velocities over 30$^\circ$ in longitude (the beacon longitudinal width was $\sim$50$^\circ$ ; see Fig. 6)." (Stratospheric winds during the storm)
- Limitation (authors): Saturn's rings shadow and contaminate the continuum and prevent wind measurements between 15 deg S and 31 deg S, and imperfect cleaning causes residuals at 20-40 deg N (west) and 40-50 deg S (east).  
  > "There are two regions at the limb where differences up to 2 Jy/beam are found. They are both located where the rings influence the continuum budget, one on the western limb between 20 and 40$^\circ$N and the other on the eastern limb between 40 and 50$^\circ$S." (Radiative transfer model); "The rings prevent meaningful measurements from 15$^\circ$S to 31$^\circ$S." (Stratospheric winds during the storm)
- Caveat (inferred, ours): Empirical sine/polynomial baseline ripple removal directly trades off with line wing amplitude and potentially induces systematic frequency shifts, which could affect both CO mole fractions and wind velocities.
- Caveat (inferred, ours): Using a 2018 northern summer solstice dataset as the quiescent baseline for 2012 northern spring winds conflates storm-induced perturbations with seasonal evolution.
- Caveat (inferred, ours): The beacon thermal field used to analyze January 14/22 ALMA data was taken on January 27 and shifted assuming a constant drift rate, neglecting any rapid thermal evolution over those 1-2 weeks.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Proprietary/in-house 3D radiative transfer code (Cavalié et al. 2019) and wind retrieval code (Cavalié et al. 2021)
- Missing: 2D/3D Cassini/CIRS temperature grids from Fletcher et al. (2012b, 2018b) formatted for the radiative transfer model
- Missing: Exact polynomial/sine baseline subtraction parameters per limb position
- Missing: Detailed CASA self-calibration and clean scripts (masks, cell size, weighting, multiscale parameters)
- Data volume (inferred): Small (~5-20 GB for a Cycle 0 compact configuration dataset with 16-18 antennas and ~2 hours total execution time)
- Score (inferred): 4/5, The ALMA data are public (Cycle 0 project 2011.0.00808.S) and the high-level methodology and key numerical results are clearly presented, but reproduction requires in-house radiative transfer and wind-retrieval codes, external Cassini/CIRS thermal grids, and manual per-spectrum baseline ripple fitting parameters that are not released.
- Rediscovery candidate: yes, Public Cycle 0 ALMA data with clear numeric targets (zonal wind velocities as a function of latitude and mean limb CO abundance); an agent could independently image the cube, extract limb spectra, and measure the Doppler shift profile to rediscover the equatorial jet slowing and high-latitude jets without needing the proprietary radiative transfer code.

## Links

- Method: (cite: Cavalie2019) (3D ellipsoidal line-by-line radiative transfer model of Saturn and ring emission/absorption parameters)
- Method: (cite: Cavalie2021) (Parametrized analytical wind retrieval technique and systematic uncertainty estimation)
- Method: (cite: Benmahi2022) (Application of the ALMA wind retrieval technique to Saturn's stratosphere)
- Method: (cite: Lellouch2019) (Wind contribution function calculation method)
- Method: (cite: Fouchet2008) (Temperature vertical profile retrieval algorithm used for the equatorial semiannual oscillation)
- Companion: (cite: Lefour2025) (Paper I of the series studying the temporal evolution of Saturn's stratosphere (water and temperatures) following the 2010-2011 Great Storm)
- Related: SMA project 2009B-S037

## Checks

```json
{
 "quotes": 115,
 "quotes_ok": 115,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 9,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 65,
  "rate": 0.73
 },
 "evidence_ok": true
}
```
