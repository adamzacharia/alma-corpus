# Discovery of ionized circumstellar gas emission around the long-period Cepheid ℓ Carinae with ALMA

`2025A&A...694L..15H` | Astronomy and Astrophysics 2025 | first author: Hocdé, V. | arXiv: 2501.19011 | DOI: 10.1051/0004-6361/202453221

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics
- Question: Is there ionized circumstellar gas around the Cepheid l Car, and what are its continuum flux, spectral index, H29alpha recombination line and temperature?  
  > "in order to investigate the presence and the characteristics of the ionized gas emission." (Introduction); "However, there is still no direct observational evidence of free-free emission toward Cepheids." (Introduction)
- Target **l Car (HD 84810, HIP 47854)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2023.1.00196.S, 2024.1.00315.S
- bands: Band 6, two spectral setups (Setup 1 and Setup 2)  
  > "Observations were conducted in two spectral setups in Band 6." (Observations of ℓ Car)
- frequencies and spectral setup: Setup 1: 211.6-215.3 and 227.6-231.4 GHz, ~10.7 km/s channels; Setup 2: 255.1-258.9 and 270.9-274.6 GHz, ~8.8 km/s channels; FDM continuum mode, 7.8 MHz after averaging 16 channels  
  > "The first setup, Setup 1, effectively covers simultaneously the spectral ranges 211.6–215.3 and 227.6–231.4 GHz at a channel binning of about 10.7 km s$^{-1}$." (Observations of ℓ Car); "The second spectral setup, Setup 2, covers higher frequencies, 255.1–258.9 and 270.9–274.6 GHz, at a channel binning of about 8.8 km s$^{-1}$." (Observations of ℓ Car); "with a coarse spectral resolution of 7.8 MHz which is the result of averaging 16 channels before the data were stored." (Observations of ℓ Car)
- continuum bandwidth: _not stated_
- arrays: ALMA main array  
  > "with the ALMA main array on 16 December 2023, 5 May, 1 July, 13 July, and 2 October 2024." (Observations of ℓ Car)
- configurations: No specific configuration requested; Setup 1 observed 3 times and Setup 2 3 times with different baseline lengths  
  > "The project was executed at ALMA without a specific requirement on the array configuration" (Observations of ℓ Car)
- baselines: 15 - 2516 m (before pipeline flagging); Setup 1 one epoch 15 - 99 m; Setup 2 one epoch 15 - 499 m  
  > "15 – 2516" (Table 1); "Baseline lengths represent datasets before pipeline flagging." (Table 1 notes)
- angular resolution: Natural weighting beams 0.70x0.59 arcsec (Setup 1), 0.37x0.30 arcsec (Setup 2), 0.46x0.39 arcsec (combined); uniform weighting 85 mas  
  > "0.70$\times$0.59" (Table 2); "At uniform weighting of the visibilities which give effective resolution of 85 mas, the map shows a single point source." (Results and discussion)
- max recoverable scale: _not stated_
- sensitivity: Image rms 10.4 (Setup 1), 9.60 (Setup 2), 7.06 (Setup 1+2) uJy/beam; no companion brighter than ~35 uJy (5 sigma)  
  > "7.06" (Table 2); "This confirms the absence of any companion of $\ell$ Car brighter than about 35 $\mu$Jy (5$\sigma$) in Band 6" (Results and discussion)
- time on source: 38 min per execution in Setup 1 (three executions); 44, 44 and 41 min in Setup 2  
  > "$t_{\rm on}$ is time on source." (Table 1 notes)
- observing dates: 2023-12-16 (two executions), 2024-05-05, 2024-07-01, 2024-07-13, 2024-10-02  
  > "with the ALMA main array on 16 December 2023, 5 May, 1 July, 13 July, and 2 October 2024." (Observations of ℓ Car)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.5 GHz)
- Line: H (radio recombination line) H29alpha (n=29) (256.4 GHz as stated in Sect. 2; reference frequency 256.302035 GHz in Sect. 3.2)
- Other facility **PIONIER/VLTI and VINCI/VLTI (literature)**: Uniform-disk angular diameters of l Car along the pulsation cycle  
  > "owing to interferometric observations in the $H$-band with PIONIER/VLTI (cite: anderson16lcar) and in the $K$-band with VINCI/VLTI (cite: kervella04a)" (Results and discussion)
- Other facility **Visible to far-IR photometry (Johnson, 2MASS, COBE, IRAC, VISIR, IRAS, MIPS, PACS, SPIRE; literature)**: Flux densities used to build the SED shown with the ALMA points  
  > "Flux density in Janskys (Jy) at different wavelengths with associated uncertainties." (Table 3)
- External data: Uniform-disk angular diameters of l Car (2.91+-0.04 mas for Setup 1)  
  > "the measured angular size is $\theta=2.91\pm0.04\,$mas (cite: anderson16lcar)" (Results and discussion) [from (cite: anderson16lcar); (cite: kervella04a)]
- External data: Effective temperature 5253+-38 K at phase 0.05  
  > "We found only one measurement given by (cite: Luck2018)" (Results and discussion) [from (cite: Luck2018)]
- External data: Interpolated effective temperatures at phases 0.65 and 0.26  
  > "we adopt interpolated values derived using the parallax-of-pulsation code" (Results and discussion) [from (cite: Merand2015)]
- External data: Pulsation period and reference epoch of maximum light  
  > "we derive the pulsation phase using recent pulsation period and reference epoch at maximum light as measured by" (Table 1 notes) [from (cite: gaia2023); rate of period change from (cite: Csorney2022)]
- External data: ATLAS9 atmosphere model for the SED  
  > "an ATLAS9 atmosphere model (cite: castelli2003) derived from the effective temperature and the angular diameter" (Results and discussion) [from (cite: castelli2003)]
- External data: Oscillator strength 5.8174132 for H29alpha  
  > "an oscillator strength of 5.8174132 (cite: Goldwire1968)" (Radio Recombination Line H29α) [from (cite: Goldwire1968)]
- External data: Catalog systemic velocity of l Car of 3.4 km/s  
  > "consistent with the catalog systemic velocity of $\ell$ Car of 3.4 km s$^{-1}$ in the same rest frame (cite: Anderson2024)" (Radio Recombination Line H29α) [from (cite: Anderson2024)]
- External data: Photometry for the SED (F07, S04, K09, I19, M24, H24)  
  > "I19: (cite: Neugebauer2019), S04: (cite: Smith2004), F07: (cite: Fouqué2007), K09: (cite: Kervella2009), M24: (cite: Marton2024), H24: (cite: Herschel2024)." (Table 3) [from (cite: Fouqué2007); (cite: Smith2004); (cite: Kervella2009); (cite: Neugebauer2019); (cite: Marton2024); (cite: Herschel2024)]
- Simulation/model as data: Thin ionized-gas envelope model of Hocde et al. for l Car (IR excess) overplotted on the SED  
  > "However, this spectral index is below the one derived in the model developed for $\ell$ Car and constrained by IR data (cite: Hocde2021)" (Results and discussion)

## Processing

### Calibration

- pipeline or manual: Default observatory pipeline in CASA  
  > "The visibilities were calibrated by the observatory using the default pipeline in CASA (cite: CASA)." (Observations of ℓ Car)
- casa version: CASA 6.6 (stated for imaging; calibration pipeline version not stated)  
  > "All imaging was done in CASA 6.6." (Observations of ℓ Car)
- pipeline version: _not stated_
- archive products used as is: Visibilities calibrated by the observatory  
  > "The visibilities were calibrated by the observatory using the default pipeline in CASA (cite: CASA)." (Observations of ℓ Car)
- flux calibrator: Quasars (flux and bandpass), unnamed  
  > "Our flux and bandpass calibration were performed using quasars" (Spectral index)
- flux scale uncertainty: About 10% claimed by the observatory; implies systematic error of about 0.4 in alpha for combined setups  
  > "for which the observatory claims flux accuracy of about 10% (cite: Francis)" (Spectral index); "this uncertainty translates to a systematic error in $\alpha$ of about 0.4." (Spectral index)
- self calibration: Phase self-calibration attempted but not adopted (insufficient S/N in individual tracks)  
  > "Self-calibration in phases was attempted but did not improve the image quality owing to insufficient signal-to-noise ratio in individual tracks." (Observations of ℓ Car)

### Imaging

- task: CASA tclean; mt-mfs with second-order (N=2) Taylor series for the spectral index  
  > "All imaging was done in CASA 6.6." (Observations of ℓ Car); "by applying a second-order ($N$=2) Taylor series." (Spectral index)
- deconvolver: _not stated_
- weighting robust: Natural weighting for most of the analysis; uniform weighting (85 mas) used to check for a single point source  
  > "Most of the analysis presented in this paper was done on images produced with natural weighting of visibilities" (Observations of ℓ Car); "At uniform weighting of the visibilities which give effective resolution of 85 mas, the map shows a single point source." (Results and discussion)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Setup 1, Setup 2 and Setup 1+2 continuum images combined; combination procedure not described  
  > "Flux densities for each Setup and for all continuum data combined are presented in Table" (Results and discussion)
- smoothing: _not stated_
- final beam: 0.70x0.59 arcsec (Setup 1), 0.37x0.30 arcsec (Setup 2), 0.46x0.39 arcsec (Setup 1+2), natural weighting  
  > "0.46$\times$0.39" (Table 2); "All values for maps obtained at natural weighting." (Table 2 notes)
- final rms: 10.4 / 9.60 / 7.06 uJy/beam (Setup 1 / Setup 2 / Setup 1+2); H29alpha moment map rms 6.63 mJy/beam km/s  
  > "7.06" (Table 2); "with rms noise of 6.63 mJy/beam km s$^{-1}$." (Radio Recombination Line H29α)

### Inherited from earlier work

- Realistic flux errors and cross-calibration behaviour of ALMA flux calibrators  
  > "all measurements are consistent within the more realistic statistical errors from practical applications, as shown by (cite: Francis)." (Fluxes in individual epochs) [from (cite: Francis)]
- General RRL profile (Gaussian convolved with Lorentzian) and electron-temperature transfer equation  
  > "a Lorentzian component due to electron pressure broadening, as outlined by (cite: Brocklehurst1972)." (Radio Recombination Line H29α); "With equation 2.124 in (cite: BookRRL2002)" (Radio Recombination Line H29α) [from (cite: Brocklehurst1972); (cite: BookRRL2002)]
- Free-free spectral index regimes (-0.1 optically thin, +2 optically thick, +0.6 for r^-2 wind, r^-3 density)  
  > "(cite: WrightBarlow1975; panagia1975; Olnon1975)" (Spectral index); "might be explained if the electron density scales as $n_e \propto r^{-3.0}$ (cite: panagia1975)." (Spectral index) [from (cite: WrightBarlow1975; panagia1975; Olnon1975)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: cell size, image size, niter, threshold, masks, gridder, spw/channel selection for the continuum
- How the six executions and the two setups were combined (concat, weights, uv ranges, per-setup versus joint cleaning)
- CASA version and pipeline version used by the observatory calibration, and the specific flux, bandpass and phase calibrators
- Whether the 20 percent peak contour used to average alpha was defined on the Setup 1+2 image, and the exact tclean reffreq and nterms settings
- Cube-making parameters for H29alpha: continuum subtraction method, line-free channels, velocity frame and channel width, and how the 55.3 km/s Gaussian was fitted
- Source of the 63 MHz line width and the integration limits used for the line flux
- Which effective temperature and diameter values were interpolated for phases 0.65 and 0.26 (SPIPS output not given)
- Rest frequency adopted for the H29alpha line (256.4 GHz in Sect. 2 versus 256.302035 GHz in Sect. 3.2)

## Analysis recipe

1. **Calibrate and image the continuum**: Observatory pipeline calibration in CASA, then tclean imaging with natural weighting for each setup and for setups combined  
  > "The visibilities were calibrated by the observatory using the default pipeline in CASA (cite: CASA)." (Observations of ℓ Car); "Most of the analysis presented in this paper was done on images produced with natural weighting of visibilities" (Observations of ℓ Car)
   - software: CASA, tclean
   - parameter: CASA 6.6 for imaging  
  > "All imaging was done in CASA 6.6." (Observations of ℓ Car)
   - parameter: Phase self-calibration not used  
  > "Self-calibration in phases was attempted but did not improve the image quality" (Observations of ℓ Car)
   - fitting: _not stated_
   - validation: Uniform-weighting map (85 mas) still shows a single point source  
  > "At uniform weighting of the visibilities which give effective resolution of 85 mas, the map shows a single point source." (Results and discussion)
2. **Measure continuum flux density and test variability**: Gaussian fit to continuum images (CASA imfit for individual epochs) and comparison of fluxes between epochs  
  > "Flux density was calculated by a Gaussian fit to continuum images." (Table 2 notes); "Flux densities were measured for each individual observation on restored images and using a Gaussian fit." (Fluxes in individual epochs)
   - software: CASA imfit
   - parameter: Image noise rms specified from image noise statistics in imfit  
  > "where the noise rms was specified based on image noise statistics." (Table 4 notes)
   - assumption: Stellar photosphere unresolved, total fluxes given  
  > "Stellar photospheric component is not resolved and total fluxes are given." (Table 2 notes)
   - fitting: Gaussian fit; errors from imfit  
  > "1$\sigma$ error is the statistical uncertainty of the fit taken from the CASA’s `imfit` procedure" (Table 4 notes)
   - validation: No variability above uncertainties between the three Setup 2 epochs; last epoch 30% higher but consistent within realistic errors  
  > "We do not find variability between these three epochs above our measurement uncertainties" (Results and discussion); "The fluxes measured for the last epoch in Setup 2, on 2 Oct 2024, are over 30% higher than in both earlier epochs." (Fluxes in individual epochs)
3. **Predict photospheric flux and quantify excess**: Rayleigh-Jeans black-body flux from effective temperature and uniform-disk angular diameter at each epoch's pulsation phase, compared with the ALMA flux  
  > "we derived the predicted flux assuming the emission follows the Rayleigh-Jeans regime of a black-body." (Results and discussion)
   - software: SPIPS
   - parameter: Teff 5253+-38 K (Setup 1, phase 0.06); theta_UD 2.91+-0.04 mas  
  > "5253$\pm$38" (Table 1); "$2.91\pm0.04$" (Table 1)
   - parameter: Teff at phases 0.65 and 0.26 interpolated with SPIPS  
  > "we adopt interpolated values derived using the parallax-of-pulsation code" (Results and discussion)
   - assumption: Limb-darkening neglected; uniform-disk diameter adopted  
  > "In the following, we will neglect the LD effect by adopting the UD angular diameter." (Results and discussion)
   - assumption: Millimeter continuum formed at similar photospheric radius as optical and IR  
  > "Hereafter we assume that the millimeter continuum is formed at a similar photospheric radius as the optical and the IR." (Results and discussion)
   - assumption: 10% uncertainty on predicted flux from the black-body assumption  
  > "assuming a conservative 10% uncertainty because of the black-body assumption." (Results and discussion)
   - fitting: _not stated_
   - validation: Upper limit on expected flux using maximum theta_UD of 3.2 mas gives about 1.9 mJy, still below measured flux  
  > "the upper limit for the flux density expected is $S_\nu\approx1.9\,$mJy." (Results and discussion)
4. **Derive the continuum spectral index**: tclean mt-mfs with nterms=2, alpha averaged over pixels within the 20% peak-flux contour; alternative log-log fit of the spectrum  
  > "by applying a second-order ($N$=2) Taylor series." (Spectral index); "we take the average value from pixels lying roughly within a contour of 20% peak flux as the representative $\alpha$" (Spectral index)
   - software: CASA, tclean
   - parameter: Uncertainty is the average 1 sigma error calculated in tclean over the same pixels  
  > "as the associated uncertainty, we take the corresponding average 1$\sigma$ error calculated in tclean" (Spectral index)
   - parameter: Systematic error of about 0.4 from 10% flux accuracy, giving alpha = +1.26+-0.44 (3 sigma)  
  > "We therefore hereafter adopt $\alpha$=+1.26$\pm$0.44 (3$\sigma$)." (Spectral index)
   - assumption: Excess attributed to free-free emission; S_nu proportional to nu^alpha  
  > "In the hypothesis that excess flux is caused by free-free emission, the spectral index $\alpha$ ($S_\nu \propto \nu^\alpha$)" (Spectral index)
   - fitting: Alternative: linear fit of log lambda vs log F_nu over the 20% contour spectrum  
  > "we generated a full spectrum of the map area within the 20% contour and fitted a line to the logarithmic version of the spectrum" (Spectral index fit)
   - validation: Alternative fit gives +1.78+-0.03, higher; CASA value favored because log fit is more prone to cross-setup calibration errors  
  > "we favor the result obtained in CASA." (Spectral index fit)
5. **Detect and characterise the H29alpha line**: Identify the feature in Setup 2, velocity-integrated map, Gaussian fit of the profile  
  > "Within our Setup 2 observations we found a spectral feature which we identify as H29$\alpha$" (Radio Recombination Line H29α); "A Gaussian fit to the feature yields a full width at half power (FWHM) of 55.3$\pm$7.5 km s$^{-1}$" (Radio Recombination Line H29α)
   - software: CASA
   - parameter: Reference frequency 256.302035 GHz, LSR velocities  
  > "At the reference frequency of 256.302035 GHz" (Radio Recombination Line H29α)
   - parameter: Coarse spectral sampling of 8.8 km/s  
  > "Due to a coarse spectral sampling (8.8 km s$^{-1}$) and a modest signal-to-noise ratio (SNR)" (Radio Recombination Line H29α)
   - assumption: Gaussian line profile only (no Lorentzian component) because of low SNR  
  > "Hereafter we assume only a Gaussian profile for simplicity, as the low SNR prevents more detailed modeling." (Radio Recombination Line H29α)
   - fitting: Gaussian fit; sampler and priors not stated  
  > "A Gaussian fit to the feature yields a full width at half power (FWHM) of 55.3$\pm$7.5 km s$^{-1}$" (Radio Recombination Line H29α)
   - validation: Line emission coincides spatially with continuum; central velocity consistent within 3 sigma with the catalog systemic velocity  
  > "The emission coincides spatially with the continuum emission of $\ell$ Car." (Radio Recombination Line H29α)
6. **Estimate electron temperature and brightness-temperature limits**: RRL transfer equation applied to the line to non-photospheric continuum flux ratio; lower brightness temperature limit from Rayleigh-Jeans formula assuming optically thick gas  
  > "With equation 2.124 in (cite: BookRRL2002), line width of 63 MHz, and an oscillator strength of 5.8174132 (cite: Goldwire1968), we find that an electron temperature of 23 500 K best explains the observed ratio" (Radio Recombination Line H29α)
   - parameter: Photosphere 1.5 mJy from black body with Teff 4850 K and 2.9 mas  
  > "The photospheric contribution was calculated as the blackbody radiation of a star with an effective temperature of 4850 K, and an angular diameter of 2.9 mas" (Radio Recombination Line H29α)
   - parameter: Line width 63 MHz  
  > "line width of 63 MHz" (Radio Recombination Line H29α)
   - assumption: Optically thin emission for both line and continuum components  
  > "Also, the formula assumes optically thin emission for both components." (Radio Recombination Line H29α)
   - fitting: _not stated_
   - validation: Uncertainty of about 10 000 K propagated from line-flux error; authors note Te could be considerably higher  
  > "we cannot exclude that the electron temperature is considerably higher than 23 500 K." (Radio Recombination Line H29α)

## Software

- **CASA** 6.6 (imaging): Observatory pipeline calibration, tclean imaging and imfit flux measurements  
  > "All imaging was done in CASA 6.6." (Observations of ℓ Car); "The visibilities were calibrated by the observatory using the default pipeline in CASA (cite: CASA)." (Observations of ℓ Car)
- **tclean (mt-mfs)** : Imaging and spectral index map  
  > "by applying a second-order ($N$=2) Taylor series." (Spectral index)
- **imfit** : Gaussian flux measurements with statistical errors  
  > "1$\sigma$ error is the statistical uncertainty of the fit taken from the CASA’s `imfit` procedure" (Table 4 notes)
- **SPIPS** : Interpolated effective temperatures at phases 0.65 and 0.26  
  > "we adopt interpolated values derived using the parallax-of-pulsation code" (Results and discussion)
- **Astropy** : Named as used in this research; specific use not given  
  > "This research also made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)
- **Aspro (JMMC)** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Combined continuum flux density (Setup 1+2) | 3.689 | 0.024 | mJy | 2 | with the flux density of $3.689\pm0.024$ mJy representing the midpoint of the covered frequencies. |
| Continuum flux density, Setup 1 | 3.306 | not stated | mJy | 2 | 3.306 |
| Continuum flux density, Setup 2 | 3.992 | not stated | mJy | 2 | 3.992 |
| Predicted photospheric flux, Setup 1 | 1.23 | 0.12 | mJy | 3 | we obtain an expected flux density for Setup 1 of $S_\nu$$=1.23\pm0.12\,$mJy assuming a conservative 10% uncertainty because of the black-body assumption. |
| Predicted photospheric flux, Setup 2 (mean of three epochs) | 1.77 | 0.18 | mJy | 3 | we derived an average predicted flux density of $S_\nu=1.77\pm0.18\,$mJy |
| Excess over photosphere, Setup 1 | 2.7 | not stated | dimensionless | 3 | we obtain a significant excess, 2.7 times brighter than the stellar photospheric continuum |
| Excess over photosphere, Setup 2 | 2.2 | not stated | dimensionless | 3 | the measured flux density is about 2.2 times higher than the stellar continuum. |
| Mean spectral index (Setup 1+2) | +1.26 | 0.06 (1 sigma); 0.44 (3 sigma, including flux calibration systematics) | dimensionless | 4 | We derived an average spectral index of $+1.26\pm$0.06 (1$\sigma$).; We therefore hereafter adopt $\alpha$=+1.26$\pm$0.44 (3$\sigma$). |
| Spectral index, Setup 1 only | +1.45 | 0.16 | dimensionless | 4 | $+1.45\pm0.16$ |
| Spectral index, Setup 2 only | +1.31 | 0.09 | dimensionless | 4 | $+1.31\pm 0.09$ |
| Spectral index, alternative log-log fit | +1.78 | 0.03 (1 sigma) | dimensionless | 4 | This resulted in $\alpha$=+1.78$\pm$0.03 (1$\sigma$) |
| H29alpha FWHM | 55.3 | 7.5 | km/s | 5 | A Gaussian fit to the feature yields a full width at half power (FWHM) of 55.3$\pm$7.5 km s$^{-1}$ and a line center at –6.2$\pm$3.2 km s$^{-1}$ (1$\sigma$, LSR). |
| H29alpha line centre (LSR) | -6.2 | 3.2 (1 sigma) | km/s | 5 | A Gaussian fit to the feature yields a full width at half power (FWHM) of 55.3$\pm$7.5 km s$^{-1}$ and a line center at –6.2$\pm$3.2 km s$^{-1}$ (1$\sigma$, LSR). |
| H29alpha velocity-integrated peak | 71.5 | rms 6.63 | mJy/beam km/s | 5 | The velocity-integrated emission has a peak at 71.5 mJy/beam km s$^{-1}$ on maps |
| H29alpha integrated line flux | 72.2 | not stated | mJy km/s | 5 | integrated over the spectral profile is 72.2 mJy km s$^{-1}$ |
| Line to non-photospheric continuum flux ratio | 0.45 | not stated | dimensionless | 6 | Our calculation therefore leads to a flux ratio of line to non-photospheric continuum of about 0.45. |
| Electron temperature | 23 500 | roughly 10 000 | K | 6 | we find that an electron temperature of 23 500 K best explains the observed ratio; roughly 10 000 K (propagated from error in the flux of the emission line) |
| Lower limit on mean brightness temperature (Setup 1 / Setup 2) | 14 000 / 11,000 | not stated | K | 6 | We find a lower limit of 14 000 K and 11,000 K for Setup 1 and 2 respectively |
| Upper limit on companion flux | 35 (5 sigma) | not stated | uJy | 1 | brighter than about 35 $\mu$Jy (5$\sigma$) in Band 6 |

## Qualitative findings

- Continuum is a single unresolved point source with no companion detected  
  > "Our ALMA observations result in a single unresolved point source at the position of $\ell$ Car" (Results and discussion)
- The H29alpha emission coincides spatially with the continuum and is centred on the stellar rest frame  
  > "We detected for the first time a RRL of H29$\alpha$ centered on the $\ell$ Car restframe" (Conclusions)
- Millimeter emission is not explained by the current ionized-shell model of Hocde et al., which could be improved with density gradient and temperature  
  > "which suggests that this model could be improved by inclusion of density gradient and temperature." (Conclusions)

## Claim tuples

- H: Does l Car show millimeter continuum emission above its photosphere? | E: ALMA Band 6 continuum in two setups compared with a Rayleigh-Jeans photospheric prediction | R: Measured about 3.5 mJy, 2.2-2.7 times the predicted photospheric flux | F: There is excess emission of ionized circumstellar origin | **supported**
- H: What emission mechanism produces the excess (spectral index)? | E: tclean mt-mfs spectral index averaged within the 20% contour | R: alpha = +1.26+-0.44 (3 sigma) | F: Partially optically thick ionized gas emission, similar to RSG chromospheres; steeper than a +0.6 wind | **partially**
- H: Is the ionized gas physically connected to the Cepheid? | E: Detection and Gaussian fit of H29alpha | R: Line centred on the stellar rest frame, FWHM 55.3+-7.5 km/s, Te of order few 10^4 K | F: Direct evidence for ionized gas connected to the star; gas temperature not compatible with X-ray emission | **supported**
- H: Does the millimeter emission vary with the pulsation cycle? | E: Compared three Setup 2 epochs at different pulsation phases | R: No variability above measurement uncertainties | F: The free-free emission is not directly linked to the pulsation | **partially**

## Reasoning

- Why this data: Higher frequencies give higher resolution and probe inner regions of the wind; setups chosen for spectral index and key lines  
  > "First, using higher frequencies increases the spatial resolution, which helps mitigate confusion from background sources and potential companions" (Introduction); "The spectral setup was designed not only to provide us with a good estimate of the continuum spectral index, but also to cover a few key spectral lines" (Observations of ℓ Car)
- Why this method: Spectral index is needed to discriminate between emission mechanisms  
  > "However, obtaining the spectral index is essential to differentiate these scenarios." (Introduction)
- Alternative: Log-log linear fit for alpha (+1.78) rejected in favour of CASA mt-mfs value  
  > "since the simple linear fit is more prone to calibration errors between the different frequency setups of the correlator" (Spectral index fit)
- Alternative: Full Gaussian plus Lorentzian RRL profile not used  
  > "Hereafter we assume only a Gaussian profile for simplicity, as the low SNR prevents more detailed modeling." (Radio Recombination Line H29α)
- How they decided it was enough: _not stated_
- Limitation (authors): Coarse spectral sampling and modest SNR make the H29alpha range likely overestimated  
  > "this range probably overestimates the spread of the emission." (Radio Recombination Line H29α)
- Limitation (authors): Electron temperature very uncertain; only one Teff measurement exists for l Car  
  > "but the uncertainty in this value is very large" (Radio Recombination Line H29α); "On the contrary the effective temperature of $\ell$ Car is not well characterized along the pulsation cycle." (Results and discussion)
- Limitation (authors): Combined-setup spectral index depends on baseband cross-calibration  
  > "When combining data from two different setups, the results depend quite strongly on the cross-calibration between the basebands." (Spectral index)
- Caveat (inferred, ours): Photospheric prediction rests on UD diameters and one literature Teff plus interpolated values; no mm-photosphere (radio photosphere) correction
- Caveat (inferred, ours): Spectral index differs between CASA mt-mfs (+1.26) and log-log fit (+1.78), and 20% contour averaging is ad hoc
- Caveat (inferred, ours): Epoch flux differences (up to 30%) are dismissed as consistent with errors; the Setup 2 epochs use different baselines and beams
- Caveat (inferred, ours): H29alpha detection is low S/N at coarse resolution; Te depends on an assumed 63 MHz width and optically thin treatment

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean imaging parameters and masks
- Missing: Procedure for combining the six executions and two setups
- Missing: Calibrator names and calibration pipeline version
- Missing: Cube and continuum-subtraction details for the H29alpha line
- Data volume (inferred): Six Band 6 executions of 38-44 min each, with baselines to 2.5 km and low-resolution FDM continuum windows; likely a few tens of GB of raw data in total
- Score (inferred): 3/5, Project codes and dates are given and the key numbers are listed, but the imaging parameters, setup combination and line-cube procedure are not, and data public status is not stated.
- Rediscovery candidate: no, The paper does not state that the data are public and key tclean and combination settings are missing, so the spectral index and line fit could not be reproduced exactly.

## Links

- Method: (cite: Francis) (Flux calibration accuracy and realistic errors for ALMA continuum)
- Method: (cite: BookRRL2002) (Radio recombination line transfer equation used for electron temperature)
- Method: (cite: Brocklehurst1972) (RRL profile with Gaussian and Lorentzian components)
- Companion: (cite: Hocde2020a); (cite: Hocde2021) (Ionized-gas envelope model for Cepheid IR excess compared with the ALMA result)
- Companion: (cite: Matthews2023) (First radio continuum detection of a Cepheid (delta Cep), variability comparison)
- Companion: (cite: Dent2024) (H30alpha emission from Betelgeuse used for comparison)

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
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 83,
  "rate": 0.776
 },
 "evidence_ok": true
}
```
