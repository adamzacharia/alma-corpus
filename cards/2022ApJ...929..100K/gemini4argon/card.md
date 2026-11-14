# Multiwavelength and Multi-CO View of the Minor Merger Driven Star Formation in the Nearby LIRG NGC 3110

`2022ApJ...929..100K` | The Astrophysical Journal 2022 | first author: Kawana, Yuka | arXiv: 2203.10303 | DOI: 10.3847/1538-4357/ac5f41

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: To better understand the physical properties of molecular gas, including the CO-to-H2 conversion factor (alpha_CO), and their relation to minor-merger-driven star formation in the nearby interacting LIRG NGC 3110.  
  > "In order to better understand the missing properties of molecular gas, including $\alpha_{\rm CO}$, and the relation to star formation in merging galaxies, we have conducted multi-CO ALMA observations toward NGC 3110." (Introduction)
- Target **NGC 3110**: coordinates _not stated_; z/distance D_L = 69.4 Mpc  
  > "A gas-rich nearby interacting galaxy NGC 3110 ($D_{\rm L}$ = 69.4 Mpc; 1$''$ = 325 pc), which is classified as a nearby luminous infrared galaxy (LIRG) ($L_{\rm IR}$ = 10$^{11.1}$ $L_{\odot}$; (cite: Armus09))" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01172.S, 2013.0.01172.S
- bands: Band 3 (2.9 mm) and Band 6 (1.3 mm)  
  > "The main targeted lines are $J$ = 1–0 (Band 3) and 2–1 (Band 6) transitions of $^{12}$CO, $^{13}$CO, and C$^{18}$O." (ALMA Observations); "We detected 2.9 mm (Band 3) and 1.3 mm (Band 6) continuum emission toward the central bar-like structure and some parts of the arms in NGC 3110" (Band 3 and 6 Continuum Emission)
- frequencies and spectral setup: 4 spectral setups; 4 spws per tuning covering both sidebands; each spw 1.875 GHz bandwidth with 7.812 MHz resolution  
  > "We set four spectral setups whose upper sideband were tuned to $^{12}$CO or $^{13}$CO." (ALMA Observations); "Each tuning had four spectral windows (spws) to cover both sidebands. All spws had a bandwidth of 1.875 GHz with 7.812 MHz resolution." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array (29-41 antennas for Band 3, 35-38 antennas for Band 6)  
  > "The assigned antenna configurations for the Band 3 and Band 6 observations had 29–41 and 35–38 12 m antennas" (ALMA Observations)
- configurations: _not stated_
- baselines: 15-558 m (or 15-639 m in Table 1) for Band 3; 15-348 m (or 15-349 m in Table 1) for Band 6  
  > "with the projected baseline length between 15–558 m and 15–348 m, respectively." (ALMA Observations); "| B3 | 2014 Jun. 28 | 57.2 | 29 | 19–639 | 40–70 | 107.529 | 95.669 | 26.6 | Ceres | J1058+0133 | J1008+0621 |" (Table 1)
- angular resolution: 1.16" x 1.14" to 1.81" x 1.43" native; convolved to 2.0"  
  > "Then, we convolve all the ALMA line and continuum maps to 2.0$''$ resolution." (Data Reduction); "| $^{12}$CO ($J$ = 1–0) | 113.360 | 5.5 | natural | 1.81 $\times$ 1.43 ($-$82) | 20 | 1.2 | 303.34 $\pm$ 1.91 |" (Table 2)
- max recoverable scale: ~10.7" (3.5 kpc) after truncating uv range below 10 klambda  
  > "Before making line intensity ratio maps, we flagged the $uv$ range below 10 k$\lambda$, so that the maximum recoverable scale (MRS) of each ALMA image is the same." (Data Reduction); "Since the truncated $uv$ range at 10 k$\lambda$ corresponds to the MRS of $\sim$10.7$''$ (3.5 kpc), we do not consider the missing flux effect on structures smaller than 10.7$''$." (Data Reduction)
- sensitivity: 0.4 to 1.2 mJy beam^-1 per channel (20 or 40 km s^-1)  
  > "| $^{12}$CO ($J$ = 1–0) | 113.360 | 5.5 | natural | 1.81 $\times$ 1.43 ($-$82) | 20 | 1.2 | 303.34 $\pm$ 1.91 |" (Table 2); "| C$^{18}$O ($J$ = 2–1) | 215.920 | 15.8 | natural | 1.59 $\times$ 0.93 (+80) | 40 | 0.4 | 7.59 $\pm$ 0.25 |" (Table 2)
- time on source: Band 3: 26.6 min, 28.1 min, 23.0 min; Band 6: 17.5x3 min, 14.7x3 min  
  > "| B3 | 2014 Jun. 28 | 57.2 | 29 | 19–639 | 40–70 | 107.529 | 95.669 | 26.6 | Ceres | J1058+0133 | J1008+0621 |" (Table 1); "| B6 | 2014 Dec. 8 | 28.6 | 35 | 15–349 | 65–115 | 229.970 | 215.805 | 17.5$\times$3 | Ganymede | J1037-2934 | J1011-0423 |" (Table 1)
- observing dates: 2014 Jun. 28, 2014 Dec. 8, 2014 Dec. 10, 2015 Mar. 9, 2015 May. 16  
  > "All data were obtained during 2014–2015." (ALMA Observations); "| B3 | 2014 Jun. 28 | 57.2 | 29 | 19–639 | 40–70 | 107.529 | 95.669 | 26.6 | Ceres | J1058+0133 | J1008+0621 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J = 1-0 (113.360 GHz (observed))
- Line: 12CO J = 2-1 (226.716 GHz (observed))
- Line: 13CO J = 1-0 (108.374 GHz (observed))
- Line: 13CO J = 2-1 (216.744 GHz (observed))
- Line: C18O J = 2-1 (215.920 GHz (observed))
- Line: C18O J = 1-0 (not stated)
- Other facility **Okayama Astrophysical Observatory (OAO) 188 cm telescope**: H alpha map (spatial resolution 1.35")  
  > "In addition to the ALMA data, we use the H$\alpha$ map obtained with Okayama Astrophysical Observatory (OAO) 188 cm telescope." (Ancillary Data)
- Other facility **Karl G. Jansky Very Large Array (VLA)**: 1.4 GHz radio continuum map from VLA Data Archive  
  > "We also download the 1.4 GHz radio continuum map taken by Karl G. Jansky Very Large Array (VLA) from VLA Data Archive" (Ancillary Data)
- Other facility **Very Large Telescope (VLT)**: K-band map providing spatial distribution of super star clusters (SSCs)  
  > "Furthermore, we use a high-quality $K$-band map obtained by Very Large Telescope (VLT) (see (cite: Randriamanakoto13) for details of the data), which provides the spatial distribution of SSCs." (Ancillary Data)
- External data: H alpha map of NGC 3110  
  > "In addition to the ALMA data, we use the H$\alpha$ map obtained with Okayama Astrophysical Observatory (OAO) 188 cm telescope. The observations and data reduction are described in detail in (cite: Hattori04)." (Ancillary Data) [from (cite: Hattori04)]
- External data: VLT K-band map and super star cluster (SSC) candidate spatial distribution  
  > "Furthermore, we use a high-quality $K$-band map obtained by Very Large Telescope (VLT) (see (cite: Randriamanakoto13) for details of the data), which provides the spatial distribution of SSCs." (Ancillary Data) [from (cite: Randriamanakoto13)]
- External data: Single-dish 12CO(1-0) total integrated flux measurement (395 +/- 79 Jy km s^-1)  
  > "However, we caution that our $^{12}$CO($1\text{--}0$) data miss some extended emission (recovered flux $=$ 77 $\pm$ 15 %) compared to single dish measurement (395 $\pm$ 79 Jy km s$^{-1}$; (cite: Sanders91))" (Data Reduction) [from (cite: Sanders91)]
- External data: Upper state energies and Einstein coefficients for RADEX non-LTE modeling from Leiden Atomic and Molecular Database  
  > "The upper state energies and the Einstein coefficients were taken from the *Leiden Atomic and Molecular Database* (cite: Schoier05)." (Non-LTE Calculation using RADEX) [from (cite: Schoier05)]
- External data: Molecular transition parameters from Splatalogue and Cologne Database for Molecular Spectroscopy  
  > "We took the transition parameters necessary for calculating the equation from Splatalogue and the *Cologne Database for Molecular Spectroscopy* (cite: Muller01; Muller05)." (LTE Mass Derivation) [from (cite: Muller01; Muller05)]
- Simulation/model as data: RADEX non-LTE radiative transfer model grids for gas kinetic temperature, volume density, and column density  
  > "We used the non-local thermodynamic equilibrium (LTE) radiative transfer code `RADEX` (cite: vanderTak07) and compare with the observed line ratios." (Non-LTE Calculation using RADEX)

## Processing

### Calibration

- pipeline or manual: ALMA Calibration Pipeline with additional manual flagging in CASA  
  > "Thus, we carefully checked the visibility data and then flagged some data points whose amplitude deviated from the average value around a given baseline length." (Data Reduction); "`ALMA Calibration Pipeline`, `astropy` (cite: Astropy13; Astropy18), `CASA` (cite: McMullin07)" (Software)
- casa version: 4.2.2  
  > "Data calibration and imaging were done using the Common Astronomy Software Applications package (`CASA`) version 4.2.2 (cite: McMullin07)." (Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres, Ganymede, J1058+015 (Band 3); Ganymede, Callisto (Band 6)  
  > "| B3 | 2014 Jun. 28 | 57.2 | 29 | 19–639 | 40–70 | 107.529 | 95.669 | 26.6 | Ceres | J1058+0133 | J1008+0621 |" (Table 1); "| B6 | 2014 Dec. 10 | 27.3 | 38 | 15–349 | 65–135 | 242.443 | 227.702 | 14.7$\times$3 | Callisto | J1037-2934 | J1011-0423 |" (Table 1)
- flux scale uncertainty: 5% for Band 3 and 10% for Band 6  
  > "Throughout this paper, we adopt the typical systematic errors on the absolute flux calibration of 5% and 10% for the Band 3 and Band 6 data, respectively (cite: Lundgren13)." (Data Reduction)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We used the CASA task `tclean` in multi-scale mode to make use of the multiscale CLEAN deconvolution algorithm (cite: Cornwell08)." (Data Reduction)
- deconvolver: multiscale  
  > "We used the CASA task `tclean` in multi-scale mode to make use of the multiscale CLEAN deconvolution algorithm (cite: Cornwell08)." (Data Reduction)
- weighting robust: natural weighting (robust = 2.0)  
  > "Images were reconstructed with the natural $uv$ (robustness parameter = 2.0) weighting and the velocity resolution of 20 or 40 km s$^{-1}$ depending on the achieved signal-to-noise ratio of the targeted lines." (Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: For moment maps: 12CO(1-0) cube clipped at 3 sigma, converted to 1/0 mask, expanded by convolving with 2.0" beam, applied with 2.5 sigma clipping for 12CO and 1.5 sigma for fainter lines  
  > "After imaging, we created moment maps following the steps described here: (1) clip the $^{12}$CO($1\text{--}0$) datacube at 3$\sigma$ (see Table 2), (2) convert the clipped cube to a 1/0 mask, (3) expand the mask by convolving by 2.0$''$ beam" (Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: uv-domain subtraction fitting line-free channels in both USB and LSB with a first-order polynomial  
  > "Continuum emission was subtracted in the $uv$ domain by fitting the line-free channels in both upper sideband and lower sideband with a first order polynomial function." (Data Reduction)
- line free channels: _not stated_
- primary beam correction: applied before making all maps and flux measurements  
  > "We made all maps and flux measurements after correcting for the primary beam attenuation." (Data Reduction)
- array combination: _not stated_
- smoothing: convolved all ALMA line and continuum maps to 2.0" resolution  
  > "Then, we convolve all the ALMA line and continuum maps to 2.0$''$ resolution." (Data Reduction)
- final beam: 2.0" (convolved); native beams 1.16" x 1.14" to 1.81" x 1.43"  
  > "Then, we convolve all the ALMA line and continuum maps to 2.0$''$ resolution." (Data Reduction); "| $^{12}$CO ($J$ = 1–0) | 113.360 | 5.5 | natural | 1.81 $\times$ 1.43 ($-$82) | 20 | 1.2 | 303.34 $\pm$ 1.91 |" (Table 2)
- final rms: 12CO(1-0): 1.2 mJy/beam; 12CO(2-1): 1.2 mJy/beam; 13CO(1-0): 1.1 mJy/beam; 13CO(2-1): 0.7 mJy/beam; C18O(2-1): 0.4 mJy/beam  
  > "| $^{12}$CO ($J$ = 1–0) | 113.360 | 5.5 | natural | 1.81 $\times$ 1.43 ($-$82) | 20 | 1.2 | 303.34 $\pm$ 1.91 |" (Table 2); "| C$^{18}$O ($J$ = 2–1) | 215.920 | 15.8 | natural | 1.59 $\times$ 0.93 (+80) | 40 | 0.4 | 7.59 $\pm$ 0.25 |" (Table 2)

### Inherited from earlier work

- Statistical noise per aperture formula  
  > "The statistical noise (i.e., sensitivity) per aperture, $\sigma_{\rm stat}(I_{\rm area})$, was calculated by the following equation (cite: Hainline04)," (Nyquist-sampled Aperture Photometry) [from (cite: Hainline04)]
- 90% confidence area in parameter space as uncertainty for RADEX derived parameters  
  > "We regard the 90% confidence area in the parameter space as the uncertainty of the derived $T_{\rm kin}$ and $n_{\rm H_2}$ following the standard way (cite: Sliwa14)." (Non-LTE Calculation using RADEX) [from (cite: Sliwa14)]
- ISM molecular gas mass derivation from Rayleigh-Jeans dust continuum emission  
  > "One of the other methods to estimate the molecular gas mass is to utilize the Rayleigh-Jeans part of the thermal dust continuum emission as described by (cite: Scoville16)." (ISM Mass Derivation) [from (cite: Scoville16)]
- Extinction-corrected H alpha luminosity and SFR calibration using H alpha and 1.4 GHz continuum  
  > "In order to estimate extinction-corrected H$\alpha$ luminosity ($L({\rm H_{\alpha}})_{\rm corr}$), we used the prescription described by (cite: Kennicutt09)," (SFR Derivation and Extinction Correction); "Then, we measure extinction-corrected SFR at each aperture using the following equation (see (cite: Kennicutt12) for a review)," (SFR Derivation and Extinction Correction) [from (cite: Kennicutt09); (cite: Kennicutt12)]

### Not stated but needed to reproduce (our reading)

- Exact baseline lengths and amplitude thresholds used for custom visibility flagging to remove periodic linear patterns
- Pixel cell size and image dimensions in tclean
- Multiscale CLEAN scales and stopping threshold/niter in tclean
- Exact frequency/channel ranges used as line-free channels for uv continuum subtraction and MFS continuum imaging
- Continuum map RMS noise levels for Band 3 (2.9 mm) and Band 6 (1.3 mm)
- Exact coordinates/grid center of the hexagonal Nyquist-sampled 3.0" apertures
- Which specific line ratios were input into the RADEX chi-square minimization
- Galaxy inclination and position angle used to compute deprojected galactocentric radii

## Analysis recipe

1. **Calibrate and image ALMA line and continuum data and create moment maps**: Flag anomalous visibility amplitudes, subtract continuum in uv domain, image lines and continuum with multiscale tclean using natural weighting, flag uv < 10 klambda for line ratio maps, correct primary beam, convolve to 2.0", and create masked moment maps.  
  > "Images were reconstructed with the natural $uv$ (robustness parameter = 2.0) weighting and the velocity resolution of 20 or 40 km s$^{-1}$ depending on the achieved signal-to-noise ratio of the targeted lines." (Data Reduction); "Before making line intensity ratio maps, we flagged the $uv$ range below 10 k$\lambda$, so that the maximum recoverable scale (MRS) of each ALMA image is the same." (Data Reduction); "We made all maps and flux measurements after correcting for the primary beam attenuation. Then, we convolve all the ALMA line and continuum maps to 2.0$''$ resolution." (Data Reduction)
   - software: CASA, tclean, ALMA Calibration Pipeline
   - parameter: robust = 2.0 (natural weighting)  
  > "Images were reconstructed with the natural $uv$ (robustness parameter = 2.0) weighting" (Data Reduction)
   - parameter: velocity resolution = 20 or 40 km s^-1  
  > "and the velocity resolution of 20 or 40 km s$^{-1}$ depending on the achieved signal-to-noise ratio of the targeted lines." (Data Reduction)
   - parameter: uv range cutoff = 10 klambda for line ratios  
  > "Before making line intensity ratio maps, we flagged the $uv$ range below 10 k$\lambda$, so that the maximum recoverable scale (MRS) of each ALMA image is the same." (Data Reduction)
   - parameter: convolved beam = 2.0"  
  > "Then, we convolve all the ALMA line and continuum maps to 2.0$''$ resolution." (Data Reduction)
   - assumption: Flux calibration systematic errors of 5% (Band 3) and 10% (Band 6)  
  > "Throughout this paper, we adopt the typical systematic errors on the absolute flux calibration of 5% and 10% for the Band 3 and Band 6 data, respectively (cite: Lundgren13)." (Data Reduction)
   - fitting: First-order polynomial fit to line-free channels in USB and LSB in uv domain for continuum subtraction  
  > "Continuum emission was subtracted in the $uv$ domain by fitting the line-free channels in both upper sideband and lower sideband with a first order polynomial function." (Data Reduction)
   - validation: Compared total 12CO(1-0) recovered flux (77 +/- 15%) against single-dish measurement (395 +/- 79 Jy km s^-1)  
  > "However, we caution that our $^{12}$CO($1\text{--}0$) data miss some extended emission (recovered flux $=$ 77 $\pm$ 15 %) compared to single dish measurement (395 $\pm$ 79 Jy km s$^{-1}$; (cite: Sanders91))" (Data Reduction)
2. **Perform hexagonal Nyquist-sampled aperture photometry and compute line ratios**: Extract integrated line intensities, brightness temperatures, luminosities, and line ratios across ALMA and ancillary maps using a hexagonal grid of 3.0" diameter apertures separated by 1.5", keeping data points > 3 sigma.  
  > "a hexagonal Nyquist sampling (aperture diameter $=$ 3.0$''$, aperture separation $=$ 1.5$''$) was performed on all data taken by ALMA and complementary data from the OAO (H$\alpha$), VLT ($K$-band), and VLA (radio continuum) observations." (Nyquist-sampled Aperture Photometry); "The Nyquist-sampled data points with flux stronger than 3$\sigma$ will be used to derive physical parameters (Section 4) and to reconstruct physical parameter images." (Nyquist-sampled Aperture Photometry)
   - parameter: aperture diameter = 3.0", aperture separation = 1.5", SNR threshold = 3 sigma  
  > "a hexagonal Nyquist sampling (aperture diameter $=$ 3.0$''$, aperture separation $=$ 1.5$''$) was performed on all data" (Nyquist-sampled Aperture Photometry); "The Nyquist-sampled data points with flux stronger than 3$\sigma$ will be used to derive physical parameters" (Nyquist-sampled Aperture Photometry)
   - assumption: D_L = 69.4 Mpc; statistical and systematic errors are independent  
  > "where we assume that both errors are independent." (Nyquist-sampled Aperture Photometry); "where $D_{\rm L}$ is the luminosity distance ($=$ 69.4 Mpc), and $z$ is the redshift (cite: Solomon05)." (Nyquist-sampled Aperture Photometry)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model non-LTE molecular gas excitation using RADEX**: Compare observed CO line ratios with non-LTE radiative transfer model grids generated by RADEX to derive gas kinetic temperature (T_kin) and H2 volume density (n_H2) at each aperture.  
  > "We used the non-local thermodynamic equilibrium (LTE) radiative transfer code `RADEX` (cite: vanderTak07) and compare with the observed line ratios." (Non-LTE Calculation using RADEX); "After deriving best-fit values at each aperture via a $\chi^2$ minimization, we made Nyquist-sampled $T_{\rm kin}$ and $n_{\rm H_2}$ images as shown in Figures 6 top-left and top-center." (Non-LTE Calculation using RADEX)
   - software: RADEX
   - parameter: T_kin = 5-205 K, n_H2 = 10^2.0 - 10^7.0 cm^-3, N_H2 = 10^22.0 - 10^22.5 cm^-2  
  > "We made model grids within a range of the gas kinetic temperature ($T_{\rm kin}$) $=$ 5-205 K, the gas volume density ($n_{\rm H_2}$) $=$ 10$^{2.0}$-10$^{7.0}$ cm$^{-3}$, and H$_2$ gas column densities ($N_{\rm H_2}$) $=$ 10$^{22.0}$-10$^{22.5}$ cm$^{-2}$." (Non-LTE Calculation using RADEX)
   - assumption: Single-phase ISM, expanding sphere geometry with dv = 100 km s^-1, T_bg = 2.73 K, [CO]/[H2] = 3 x 10^-4, [CO]/[13CO] = 70  
  > "assuming a single-phase ISM (i.e., the gas physics can be represented by a single set of the excitation parameters), an expanding sphere geometry ($dv$ $=$ 100 km s$^{-1}$), the cosmic microwave background temperature ($T_{\rm bg}$ = $T_{\rm CMB}$ $=$ 2.73K)" (Non-LTE Calculation using RADEX); "and \[CO\]/\[H$_2$\] ($=$ 3 $\times$ 10$^{-4}$) and \[CO\]/\[$^{13}$CO\] ($=$ 70) abundances which are same as those applied for the LTE calculation described later." (Non-LTE Calculation using RADEX)
   - fitting: chi^2 minimization with 90% confidence area as uncertainty  
  > "After deriving best-fit values at each aperture via a $\chi^2$ minimization, we made Nyquist-sampled $T_{\rm kin}$ and $n_{\rm H_2}$ images" (Non-LTE Calculation using RADEX); "We regard the 90% confidence area in the parameter space as the uncertainty of the derived $T_{\rm kin}$ and $n_{\rm H_2}$ following the standard way (cite: Sliwa14)." (Non-LTE Calculation using RADEX)
   - validation: _not stated_
4. **Derive H2 gas masses and calibrate the CO-to-H2 conversion factor (alpha_CO)**: Estimate H2 gas masses via two independent methods: (1) LTE calculation from optically-thin 13CO transitions assuming fixed T_rot = 15 K, and (2) Rayleigh-Jeans 1.3 mm dust continuum emission following Scoville et al. (2016). Compare both with L'_CO(1-0) to determine alpha_CO.  
  > "In this paper, we estimate H$_2$ gas mass ($M_{\rm H_2}$) with two different methods and then compare with $L'_{\rm CO(1-0)}$." (The CO-to-H$_2$ Conversion Factor); "In this paper, we estimate H$_2$ gas mass ($M_{\rm H_2}$) with two different methods and then compare with $L'_{\rm CO(1-0)}$." (The CO-to-H$_2$ Conversion Factor); "We derived molecular ISM masses ($M_{\rm ISM}$) from the 1.3 mm dust continuum emission using the following equation;" (ISM Mass Derivation)
   - parameter: T_rot = T_d = 15 K; alpha_850 = 6.7 x 10^19 erg s^-1 Hz^-1 M_sun^-1; nu_obs = 235 GHz; adopted constant alpha_CO = 1.7 M_sun (K km s^-1 pc^2)^-1  
  > "where $S_{\rm\nu_{obs}}$ is the observed continuum flux, $\nu_{\rm 850\mu m}$ is 353 GHz, $\nu_{\rm obs}$ is the observed frequency (= 235 GHz), $\alpha_{\rm 850}$ is the calibration constant corresponding to 6.7 $\times$ 10$^{19}$ erg s$^{-1}$ Hz$^{-1}$ $M_{\odot}^{-1}$" (ISM Mass Derivation); "Here, we adopt $T_{\rm d}$ $=$ $T_{\rm rot}$ (= 15 K) in order to estimate $\alpha_{\rm ISM}$ (= $M_{\rm ISM}$/$L'_{\rm CO(1-0)}$)" (ISM Mass Derivation); "In this paper, we adopt a fixed $\alpha_{\rm CO}$ of 1.7 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ when measuring gas masses." (Appropriate $\alpha_{\rm CO}$ for NGC 3110)
   - assumption: 13CO is optically thin in LTE; [13CO]/[H2] = 4.3 x 10^-6 ([12CO]/[13CO] = 70, [12CO]/[H2] = 3.0 x 10^-4); Helium factor = 1.36; T_d = T_rot = 15 K  
  > "Here we assumed \[$^{13}$CO\]/\[H$_2$\] $=$ 4.3 $\times$ 10$^{-6}$, that is similar to the standard value observed in Galactic warm, star-forming molecular clouds (\[$^{12}$CO\]/\[$^{13}$CO\] $=$ 70, \[$^{12}$CO\]/\[H$_2$\] $=$ 3.0 $\times$ 10$^{-4}$; e.g., (cite: Blake87; Lacy94))." (LTE Mass Derivation); "We multiply by 1.36 to account for the Helium abundance relative to hydrogen." (LTE Mass Derivation)
   - fitting: Gaussian fit to the histogram of alpha_ISM(T_rot) yielding peak = 1.73 and dispersion = 0.48  
  > "Figure 7 (right) shows the histogram of $\alpha_{\rm ISM}$($T_{\rm rot}$) with a best-fit Gaussian (peak $=$ 1.73 and dispersion $=$ 0.48)." (Appropriate $\alpha_{\rm CO}$ for NGC 3110)
   - validation: Checked upper limit alpha_LTE(T_kin) using RADEX T_kin; tested impact of spatially varying alpha_LTE(T_rot) vs constant alpha_CO in Appendix A.  
  > "Indeed, we confirmed that $\alpha_{\rm LTE}$($T_{\rm kin}$) are $\gtrsim$2 times larger than $\alpha_{\rm LTE}$($T_{\rm rot}$)." (LTE Mass Derivation); "However, we confirm that the varying $\alpha_{\rm CO}$ does not strongly affect the trends of the region “A" discussed in the main text. Thus, both the constant and varying $\alpha_{\rm CO}$ measurements lead to the same conclusions of this paper." (Scatter plots with varying $\alpha_{\rm CO}$)
5. **Compute millimeter spectral index, extinction-corrected SFR, SFE, and SSC surface density**: Calculate millimeter spectral index between 1.3 mm and 2.9 mm continuum; compute extinction-corrected SFR from OAO H alpha and VLA 1.4 GHz continuum; compute Sigma_H2 (using untruncated 12CO(1-0) data and fixed alpha_CO = 1.7), SFE (= Sigma_SFR / Sigma_H2), and Sigma_SSC across apertures.  
  > "We note that we use the original (i.e., untruncated) data for the gas mass measurement in this paper, although for all works requiring any line ratio we use the truncated data." (Data Reduction); "Based on our Band 3 and Band 6 data, we can roughly study the continuum property using the following equation:" (Spectral Index: Two Thermal Components); "In order to estimate extinction-corrected H$\alpha$ luminosity ($L({\rm H_{\alpha}})_{\rm corr}$), we used the prescription described by (cite: Kennicutt09)," (SFR Derivation and Extinction Correction)
   - parameter: L(H_alpha)_corr = L(H_alpha)_obs + 0.39 x 10^13 L(1.4GHz); SFR = L(H_alpha)_corr / 10^41.27  
  > "\frac{L({\rm H_{\alpha}})_{\rm corr}}{\rm erg\:s^{-1}} = L({\rm H_{\alpha}})_{\rm obs} + 0.39 \times 10^{13}L(\rm 1.4GHz)," (SFR Derivation and Extinction Correction); "\frac{\rm SFR}{\rm M_{\odot}\:yr^{-1}} = \frac{L({\rm H_{\alpha}})_{\rm corr}}{10^{41.27}}." (SFR Derivation and Extinction Correction)
   - assumption: Global H alpha + 1.4 GHz extinction correction prescription holds for 3.0" (~1 kpc) apertures; fixed alpha_CO = 1.7 M_sun (K km s^-1 pc^2)^-1  
  > "We caution that the employed extinction-correction prescription is based on the global measurements (see (cite: Kennicutt09)), and therefore our spatially-resolved SFRs are uncertain." (SFR Derivation and Extinction Correction)
   - fitting: _not stated_
   - validation: Confirmed total SFR (~18 M_sun yr^-1) agrees with literature IR SED (~24 M_sun yr^-1) and H alpha + 24 um / 24 um values (19.7 and 21.2 M_sun yr^-1), and compared SFE with Espada et al. (2018).  
  > "However, we confirmed that the measured total SFR is in agreement with values derived in the literature: (cite: U12) derived $\sim$24 $M_{\odot}$ yr$^{-1}$ based on the IR SED, and (cite: Espada18) derived 19.7 $M_{\odot}$ yr$^{-1}$ and 21.2 $M_{\odot}$ yr$^{-1}$" (SFR Derivation and Extinction Correction); "Our SFE values are consistent with previous SFE values (cite: Espada18) if we use the same $\alpha_{\rm CO}$ they assumed (i.e., 4.3 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$instead of 1.7 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$)." (Kennicutt-Schmidt Relation)

## Software

- **ALMA Calibration Pipeline** : Initial calibration of ALMA visibility data  
  > "`ALMA Calibration Pipeline`, `astropy` (cite: Astropy13; Astropy18), `CASA` (cite: McMullin07), `matplotlib` (cite: Hunter07), `numpy` (cite: Oliphant06), `scipy` (cite: Virtanen20)" (Software)
- **CASA** 4.2.2: Data calibration, manual visibility flagging, uv continuum subtraction, and imaging  
  > "Data calibration and imaging were done using the Common Astronomy Software Applications package (`CASA`) version 4.2.2 (cite: McMullin07)." (Data Reduction)
- **tclean** : Multiscale CLEAN deconvolution for line and continuum imaging  
  > "We used the CASA task `tclean` in multi-scale mode to make use of the multiscale CLEAN deconvolution algorithm (cite: Cornwell08)." (Data Reduction)
- **RADEX** : Non-LTE radiative transfer calculations to derive T_kin and n_H2  
  > "We used the non-local thermodynamic equilibrium (LTE) radiative transfer code `RADEX` (cite: vanderTak07) and compare with the observed line ratios." (Non-LTE Calculation using RADEX)
- **astropy** : General astronomical data analysis (listed in Software section)  
  > "`ALMA Calibration Pipeline`, `astropy` (cite: Astropy13; Astropy18), `CASA` (cite: McMullin07), `matplotlib` (cite: Hunter07), `numpy` (cite: Oliphant06), `scipy` (cite: Virtanen20)" (Software)
- **matplotlib** : Plotting and visualization (listed in Software section)  
  > "`ALMA Calibration Pipeline`, `astropy` (cite: Astropy13; Astropy18), `CASA` (cite: McMullin07), `matplotlib` (cite: Hunter07), `numpy` (cite: Oliphant06), `scipy` (cite: Virtanen20)" (Software)
- **numpy** : Numerical calculations (listed in Software section)  
  > "`ALMA Calibration Pipeline`, `astropy` (cite: Astropy13; Astropy18), `CASA` (cite: McMullin07), `matplotlib` (cite: Hunter07), `numpy` (cite: Oliphant06), `scipy` (cite: Virtanen20)" (Software)
- **scipy** : Scientific computing (listed in Software section)  
  > "`ALMA Calibration Pipeline`, `astropy` (cite: Astropy13; Astropy18), `CASA` (cite: McMullin07), `matplotlib` (cite: Hunter07), `numpy` (cite: Oliphant06), `scipy` (cite: Virtanen20)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total integrated flux of 12CO(1-0) | 303.34 | 1.91 | Jy km s^-1 | 1 | / $^{12}$CO ($J$ = 1–0) / 113.360 / 5.5 / natural / 1.81 $\times$ 1.43 ($-$82) / 20 / 1.2 / 303.34 $\pm$ 1.91 / |
| Recovered flux fraction of 12CO(1-0) | 77 | 15 | % | 1 | However, we caution that our $^{12}$CO($1\text{--}0$) data miss some extended emission (recovered flux $=$ 77 $\pm$ 15 %) compared to single dish measurement (395 $\pm$ 79 Jy km s$^{-1}$; (cite: Sanders91)) |
| Total integrated flux of 12CO(2-1) | 854.84 | 1.83 | Jy km s^-1 | 1 | / $^{12}$CO ($J$ = 2–1) / 226.716 / 16.6 / natural / 1.68 $\times$ 0.93 (+74) / 20 / 1.2 / 854.84 $\pm$ 1.83 / |
| Total integrated flux of 13CO(1-0) | 10.08 | 0.69 | Jy km s^-1 | 1 | / $^{13}$CO ($J$ = 1–0) / 108.374 / 5.3 / natural / 1.16 $\times$ 1.14 ($-$32) / 20 / 1.1 / 10.08 $\pm$ 0.69 / |
| Total integrated flux of 13CO(2-1) | 38.01 | 0.57 | Jy km s^-1 | 1 | / $^{13}$CO ($J$ = 2–1) / 216.744 / 15.9 / natural / 1.59 $\times$ 0.93 (+80) / 20 / 0.7 / 38.01 $\pm$ 0.57 / |
| Total integrated flux of C18O(2-1) | 7.59 | 0.25 | Jy km s^-1 | 1 | / C$^{18}$O ($J$ = 2–1) / 215.920 / 15.8 / natural / 1.59 $\times$ 0.93 (+80) / 40 / 0.4 / 7.59 $\pm$ 0.25 / |
| Average 12R_21/10 line intensity ratio | 0.8 | not stated | dimensionless | 2 | The $^{\rm 12}R_{21/10}$ shows a smooth distribution over the entire arms and bar-like elongation ($\sim$0.8 on average). |
| 13R_21/10 line intensity ratio (center / ends of elongation / southern arm) | 1.0 / 0.7 / 0.4 | not stated | dimensionless | 2 | The $^{\rm 13}R_{21/10}$ peaks at the center ($\sim$1.0) with lower values at the ends of the elongation ($\sim$0.7) and the southern arm ($\sim$0.4). |
| Median and average 13CO rotation temperature (T_rot) | 15.1 (median), 15.4 (average) | not stated | K | 4 | The median and average $T_{\rm rot}$ are 15.1 K and 15.4 K, respectively. |
| LTE-based CO-to-H2 conversion factor (alpha_LTE) 50th percentile | 1.69 | +0.52/-0.39 (16th-84th percentiles: 1.30-2.21) | M_sun (K km s^-1 pc^2)^-1 | 4 | The derived 16$^{th}$–50$^{th}$–84$^{th}$ percentiles of $\alpha_{\rm LTE}$ ($=$ $M_{\rm LTE}$/$L'_{\rm CO(1-0)}$) are 1.30–1.69–2.21 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$. |
| Dust-based CO-to-H2 conversion factor (alpha_ISM) 50th percentile | 1.48 | +0.78/-0.40 (16th-84th percentiles: 1.08-2.26) | M_sun (K km s^-1 pc^2)^-1 | 4 | The derived 16$^{th}$–50$^{th}$–84$^{th}$ percentiles of $\alpha_{\rm ISM}$ are 1.08–1.48–2.26 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$. |
| Best-fit Gaussian peak of alpha_ISM(T_rot) and adopted typical alpha_CO | 1.73 (Gaussian peak), 1.7 (adopted) | 0.48 (Gaussian dispersion) | M_sun (K km s^-1 pc^2)^-1 | 4 | Figure 7 (right) shows the histogram of $\alpha_{\rm ISM}$($T_{\rm rot}$) with a best-fit Gaussian (peak $=$ 1.73 and dispersion $=$ 0.48). In this paper, we adopt a fixed $\alpha_{\rm CO}$ of 1.7 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ |
| Total extinction-corrected SFR of NGC 3110 | 18 | not stated | M_sun yr^-1 | 5 | The derived total SFR from the extinction-corrected H$\alpha$ data (i.e., summed over all independent apertures) is $\sim$18 $M_{\odot}$ yr$^{-1}$(Figure 6 middle-left). |
| Star formation efficiency (SFE) at southern arm tip (region A) | 10^-8.2 | not stated | yr^-1 | 5 | These parameters show a peak at the southern part of the southern spiral arm (SFE $\sim$ 10$^{-8.2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SFR}$}$ $\sim$ 10$^{-0.6}$$M_{\odot}$ kpc$^{-2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SSC}$}$ $\sim$ 6.0 kpc$^{-2}$) |
| SFR surface density (Sigma_SFR) at southern arm tip (region A) | 10^-0.6 | not stated | M_sun kpc^-2 yr^-1 | 5 | These parameters show a peak at the southern part of the southern spiral arm (SFE $\sim$ 10$^{-8.2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SFR}$}$ $\sim$ 10$^{-0.6}$$M_{\odot}$ kpc$^{-2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SSC}$}$ $\sim$ 6.0 kpc$^{-2}$) |
| Super star cluster surface density (Sigma_SSC) at southern arm tip (region A) | 6.0 | not stated | kpc^-2 | 5 | These parameters show a peak at the southern part of the southern spiral arm (SFE $\sim$ 10$^{-8.2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SFR}$}$ $\sim$ 10$^{-0.6}$$M_{\odot}$ kpc$^{-2}$ yr$^{-1}$, $\mbox{$\Sigma_{\rm SSC}$}$ $\sim$ 6.0 kpc$^{-2}$) |
| Millimeter spectral index (1.3 mm to 2.9 mm) in central region (< 3 kpc) vs southern arm tip (region A) | 1-3 (center), ~0.5 (region A) | not stated | dimensionless | 5 | The data points with the deprojected radius $<$ 3 kpc (yellow to red color) tend to distribute around the spectral index $\sim$1–3, indicating dusty star formation at the central region of NGC 3110.; In contrast to the center, the outer part, especially the region “A", shows much lower spectral index ($\sim$0.5), implying that 2.9 mm continuum from the region “A" is likely to be significantly contaminated by the free-free emission |

## Qualitative findings

- A bright central north-south bar-like elongated structure, a northern shorter arm, and a southern longer arm are detected in 12CO, 13CO, and C18O, along with diffuse flocculent inter-arm components in 12CO and an S-shaped non-circular velocity pattern.  
  > "We confirm a bright central north-south bar-like elongated structure, a northern shorter arm and a southern longer arm in all the $^{12}$CO, $^{13}$CO, and C$^{18}$O lines" (Results); "The $^{12}$CO velocity fields show rotating disk-like signature with a “S"-shape non-circular motion, indicating the presence of inflow motions and/or a warped disk" (Results)
- The southern tip of the southern arm (region A) is an active and young star-forming region dominated by thermal free-free emission at 2.9 mm, whereas the central region is a site of dusty, long-continued star formation.  
  > "Those measurements imply that the peak of the southern arm is an active and young star-forming region, whereas the central part of NGC 3110 is a site of long-continued star formation." (Abstract)
- Adopting a spatially varying LTE-based alpha_CO versus a constant alpha_CO does not alter the qualitative trends on the Kennicutt-Schmidt relation or the conclusions regarding region A.  
  > "However, we confirm that the varying $\alpha_{\rm CO}$ does not strongly affect the trends of the region “A" discussed in the main text. Thus, both the constant and varying $\alpha_{\rm CO}$ measurements lead to the same conclusions of this paper." (Scatter plots with varying $\alpha_{\rm CO}$)

## Claim tuples

- H: The CO-to-H2 conversion factor (alpha_CO) in the interacting LIRG NGC 3110 is lower than the standard Milky Way disk value, similar to other (U)LIRGs. | E: Derive H2 column densities and masses across 3.0" Nyquist-sampled apertures using both optically-thin 13CO LTE radiative transfer and 1.3 mm Rayleigh-Jeans dust continuum emission, and compare with 12CO(1-0) luminosity. | R: The 16th-50th-84th percentiles are 1.30-1.69-2.21 M_sun (K km s^-1 pc^2)^-1 for alpha_LTE and 1.08-1.48-2.26 M_sun (K km s^-1 pc^2)^-1 for alpha_ISM, with a Gaussian peak of 1.73 for alpha_ISM(T_rot). | F: A typical conversion factor of alpha_CO = 1.7 M_sun (K km s^-1 pc^2)^-1 characterizes the disk of NGC 3110, consistent with other (U)LIRGs, and choosing constant vs varying alpha_CO does not change the star formation conclusions. | **supported**
- H: Off-nuclear starburst activity at the southern tip of the southern spiral arm (region A) is a young, active star-forming complex compared to the central starburst. | E: Measure 1-kpc scale SFE, Sigma_SFR, Sigma_SSC, and the 1.3 mm to 2.9 mm continuum spectral index across the galaxy disk. | R: Region A exhibits the highest SFE (~10^-8.2 yr^-1, ~4 times higher than the nuclear average), high Sigma_SFR (~10^-0.6 M_sun kpc^-2 yr^-1) and Sigma_SSC (~6.0 kpc^-2), and a shallow millimeter spectral index (~0.5) compared to the central region (1-3). | F: The shallow spectral index indicates significant thermal free-free emission from young H II regions (< 10 Myr) in region A, whereas the central region is a site of dusty, long-continued star formation. | **supported**
- H: During the early stage of a minor galaxy-galaxy interaction, tidal fragmentation along the main galaxy's arms drives active off-nuclear star formation while gas inflow feeds dusty nuclear starbursts. | E: Compare the multi-CO clumpy gas morphology, SSC distribution, and relative ages of star-forming regions in NGC 3110 with published hydrodynamical minor merger simulations. | R: Clumpy CO isotopologue structures along the asymmetric arms and young star formation at region A match simulation predictions of tidally induced transient arms formed ~150 Myr after closest approach with MCG-01-26-013. | F: Ongoing tidal interaction with companion galaxy MCG-01-26-013 triggers gas fragmentation and young star formation at the southern arm tip as well as gas inflow driving the central dusty starburst. | **supported**

## Reasoning

- Why this data: Low-J 12CO, 13CO, and C18O lines trace the total column density, diffuse molecular ISM properties, and spatially varying alpha_CO at ~1 kpc resolution in a prototype early-stage minor merger LIRG rich in SSCs.  
  > "For nearby galaxies, low-$J$ $^{12}$CO, $^{13}$CO, and C$^{18}$O lines ($n$ $\simeq$ 10$^2$-10$^3$ cm$^{-3}$) are usually employed to trace the total column density and the response of H$_2$ gas to violent merger events." (Introduction); "In order to better understand the missing properties of molecular gas, including $\alpha_{\rm CO}$, and the relation to star formation in merging galaxies, we have conducted multi-CO ALMA observations toward NGC 3110." (Introduction)
- Why this method: Hexagonal Nyquist sampling with 3.0" apertures decreases correlated data points and unifies photometry across multi-telescope datasets; flagging uv < 10 klambda matches the maximum recoverable scale across bands before taking line ratios.  
  > "Before making line intensity ratio maps, we flagged the $uv$ range below 10 k$\lambda$, so that the maximum recoverable scale (MRS) of each ALMA image is the same." (Data Reduction); "In order to decrease the number of correlated data points and to unify the flux measurement method among images taken with different telescopes, a hexagonal Nyquist sampling (aperture diameter $=$ 3.0$''$, aperture separation $=$ 1.5$''$) was performed" (Nyquist-sampled Aperture Photometry)
- Alternative: C18O(1-0) was covered by one tuning but rejected from analysis due to marginal detection only around the very center.  
  > "We note that C$^{18}$O($1\text{--}0$), which is also covered by one of our tunings, was marginally detected only around the very center, and thus we do not utilize this line in this paper." (Results)
- Alternative: Deriving LTE gas mass using RADEX-derived T_kin instead of constant T_rot = 15 K was tested as an upper limit, and spatially varying alpha_LTE(T_rot) was tested in Appendix A against constant alpha_CO = 1.7.  
  > "Here we also derived $\alpha_{\rm LTE}$ using $T_{\rm kin}$ ($=$ $\alpha_{\rm LTE}$($T_{\rm kin}$)) derived in Section 4.1, instead of the fixed $T_{\rm rot}$, based on a reasonable assumption that CO excitation is entirely dominated by collision with H$_2$." (LTE Mass Derivation); "In order to discuss how these plots change when we apply the spatially varying $\alpha_{\rm CO}$, we reconstruct these with $\alpha_{\rm LTE}$($T_{\rm rot}$) in Figure 9." (Scatter plots with varying $\alpha_{\rm CO}$)
- How they decided it was enough: _not stated_
- Limitation (authors): 12CO(1-0) data miss ~23% of extended emission compared to single-dish measurements (recovered flux = 77 +/- 15%), which may affect measurements on 3.0" apertures.  
  > "However, we caution that our $^{12}$CO($1\text{--}0$) data miss some extended emission (recovered flux $=$ 77 $\pm$ 15 %) compared to single dish measurement (395 $\pm$ 79 Jy km s$^{-1}$; (cite: Sanders91)), which may affect our measurements on 3.0$''$ apertures" (Data Reduction)
- Limitation (authors): The SNR of the 13CO(1-0) map is insufficient to measure the spatial distribution of T_rot across the galaxy, requiring a constant T_rot = 15 K assumption that artificially increases alpha_LTE in the central kpc.  
  > "We explain that this increasing trend is due to the assumed constant $T_{\rm rot}$." (Appropriate $\alpha_{\rm CO}$ for NGC 3110); "Although one of our original motivations to observe multiple transitions is to study the temperature effect on the gas mass measurements around the galaxy centers, the signal-to-noise ratios of our $^{13}$CO($1\text{--}0$) map is insufficient to measure the spatial $T_{\rm rot}$ distribution." (Appropriate $\alpha_{\rm CO}$ for NGC 3110)
- Limitation (authors): Assuming fixed Galactic abundance ratios ([13CO]/[H2] = 4.3 x 10^-6) without sophisticated modeling.  
  > "In order to accurately constrain the abundance ratios in NGC 3110, we need a more sophisticated modeling with increasing the number of input maps and their quality." (LTE Mass Derivation)
- Limitation (authors): The H alpha + 1.4 GHz extinction-correction prescription is calibrated on global galaxy measurements, making spatially resolved 1-kpc SFRs uncertain.  
  > "We caution that the employed extinction-correction prescription is based on the global measurements (see (cite: Kennicutt09)), and therefore our spatially-resolved SFRs are uncertain." (SFR Derivation and Extinction Correction)
- Limitation (authors): The discussion of the shallow millimeter spectral index in region A relies on a single aperture data point.  
  > "We note that the discussion of the spectral index in the region “A" is based on a single data point as shown in the top-right panel of Figure 8." (Star Formation at the Tip of the Southern Arm)
- Caveat (inferred, ours): Custom manual flagging of visibilities to remove 'periodical linear patterns' is described only qualitatively without specifying exact baseline ranges or amplitude clipping thresholds.
- Caveat (inferred, ours): Assuming a constant dust temperature and rotation temperature of 15 K across both the starburst nucleus and outer tidal arm likely biases both alpha_LTE and alpha_ISM in the warmer central region.
- Caveat (inferred, ours): The Scoville et al. (2016) 1.3 mm ISM mass calibration assumes pure thermal dust emission, but the authors show that millimeter continuum in region A has a significant free-free contribution.

## Reproducibility

- Data public (paper): ALMA cycle 2 data (ID: 2013.1.01172.S / ADS/JAO.ALMA#2013.0.01172.S) and archival VLA 1.4 GHz continuum image from NRAO VLA Archive Survey  
  > "Observations of $^{12}$CO and its isotopologues toward NGC 3110 were carried out during the ALMA cycle 2 period (ID: 2013.1.01172.S)." (ALMA Observations); "We also download the 1.4 GHz radio continuum map taken by Karl G. Jansky Very Large Array (VLA) from VLA Data Archive" (Ancillary Data)
- Products in archive: _not stated_
- Missing: OAO 188 cm H alpha FITS map (Hattori et al. 2004) and VLT K-band SSC catalog/map (Randriamanakoto et al. 2013) are not in public archives by default
- Missing: Exact visibility flagging commands used to suppress periodic linear artifacts
- Missing: Exact tclean parameters (cell size, imsize, multiscale scales, stopping thresholds)
- Missing: Exact hexagonal aperture coordinates and galaxy deprojection parameters (inclination, PA)
- Data volume (inferred): ~10-30 GB (5 Cycle 2 12m execution blocks across Band 3 and Band 6)
- Score (inferred): 68/5, ALMA project code, calibration/imaging software (CASA 4.2.2), weighting, smoothing beam, uv-clipping, aperture sizes, and all analytic formulas for LTE mass, ISM mass, RADEX grid bounds, and SFR are explicitly written out. However, custom manual flagging details, tclean deconvolution parameters, and external OAO/VLT maps are not directly provided.
- Rediscovery candidate: yes, The ALMA Cycle 2 dataset (2013.1.01172.S) is public, and the core ALMA-only numeric results—integrated line fluxes for 5 CO isotopologue transitions, line ratios, T_rot, alpha_LTE, alpha_ISM, and millimeter spectral indices—are derived via explicitly stated equations on 2.0" convolved maps.

## Links

- Method: (cite: Hainline04) (Formula for statistical noise per aperture in integrated intensity maps)
- Method: (cite: Solomon05) (Formula for CO line luminosity L'_line)
- Method: (cite: vanderTak07) (RADEX non-LTE radiative transfer code)
- Method: (cite: Goldsmith99; Watanabe14; Nakajima18) (LTE rotational temperature and column density derivation from optically-thin lines)
- Method: (cite: Scoville16) (Rayleigh-Jeans dust continuum calibration for molecular ISM mass)
- Method: (cite: Kennicutt09); (cite: Kennicutt12) (Extinction-corrected H alpha + 1.4 GHz continuum SFR calibration)
- Companion: (cite: Espada10; Espada18) (Prior SMA 12CO(2-1) observations and hydrodynamical minor merger simulations of NGC 3110 by co-authors that defined the ALMA pointings and physical framework)

## Checks

```json
{
 "quotes": 155,
 "quotes_ok": 155,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 2,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.0.01172.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 82,
  "rate": 0.804
 },
 "evidence_ok": true
}
```
