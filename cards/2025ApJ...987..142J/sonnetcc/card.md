# A JWST/MIRI View of the Interstellar Medium in M83. I. Resolved Molecular Hydrogen Properties, Star Formation, and Feedback

`2025ApJ...987..142J` | The Astrophysical Journal 2025 | first author: Jones, Logan H. | arXiv: 2410.09020 | DOI: 10.3847/1538-4357/adce71

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Distribution, kinematics and excitation of warm H2 in the nuclear starburst of M83 at ~3 pc per spaxel from JWST/MIRI MRS, with [Ne II]/[Ne III] as SFR and hardness tracers, and links to molecular gas mass and cluster ages; ALMA CO(2-1) is used only as a qualitative comparison  
  > "IFU spectroscopy reveals a clumpy reservoir of warm" (abstract); "In this work, we return to the same dataset to inspect the properties of the warm" (Introduction)
- Target **M83 nuclear starburst region (four MRS pointings, central ~200x200 pc)**: coordinates optical nucleus (RA, Dec) = (13:17:0.887, -29:51:55.921) as measured from MRS data (the paper later prints RA 13:37:00.5 for sources in the same field)  
  > "As the nearest face-on spiral galaxy with a nuclear starburst ($D$ = 4.6 Mpc, (cite: Saha06))" (Introduction); "We began by assuming a systemic redshift of $z$ = 0.001733 (cite: MeyerHipass)" (3.1 PAHs, Dust Continuum, and Attenuation); "($\alpha$, $\delta$) = (13:17:0.887, -29:51:55.921) as measured from our MRS data" (3.1 PAHs, Dust Continuum, and Attenuation); z/distance D = 4.6 Mpc; z = 0.001733  
  > "As the nearest face-on spiral galaxy with a nuclear starburst ($D$ = 4.6 Mpc, (cite: Saha06))" (Introduction); "We began by assuming a systemic redshift of $z$ = 0.001733 (cite: MeyerHipass)" (3.1 PAHs, Dust Continuum, and Attenuation); "($\alpha$, $\delta$) = (13:17:0.887, -29:51:55.921) as measured from our MRS data" (3.1 PAHs, Dust Continuum, and Attenuation); distance from Saha06 (distance); MeyerHipass (redshift)  
  > "As the nearest face-on spiral galaxy with a nuclear starburst ($D$ = 4.6 Mpc, (cite: Saha06))" (Introduction); "We began by assuming a systemic redshift of $z$ = 0.001733 (cite: MeyerHipass)" (3.1 PAHs, Dust Continuum, and Attenuation); "($\alpha$, $\delta$) = (13:17:0.887, -29:51:55.921) as measured from our MRS data" (3.1 PAHs, Dust Continuum, and Attenuation)

## Data provenance

- ALMA projects: 2013.1.01161.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA project 2013.1.01161.S, PI Sakamoto (CO(2-1) used for qualitative comparison)  
  > "CO(2-1) emission (ALMA pID 2013.1.01161.S, PI Sakamoto)" (5.3 A Massive, Obscured Point Source)
- Line: CO J=2-1 (not stated)
- Other facility **JWST/MIRI MRS (GO 02219)**: Four-pointing 2x2 MRS IFU mosaic of the M83 nucleus, the primary dataset  
  > "We use the MIRI/MRS observations from program GO 02219 (PI: Hernandez), which were obtained between 2022 July 5 – 9." (2 Observations)
- Other facility **JWST/NIRCam and MIRI imaging (FEAST, GO 1783)**: Imaging of stellar populations, embedded star formation and PAH emission used for qualitative comparison  
  > "as part of the FEAST program (GO 1783, PI A. Adamo; Adamo et al., in prep.)" (Introduction)
- Other facility **HST/COS archival FUV spectroscopy (programs 11579, 14681, 15193)**: Integrated FUV spectra of four cluster groupings used to estimate cluster ages and mass  
  > "To further investigate the possible age gradient, we have analyzed archival" (5.4 Gaseous Confirmation of a Stellar Age Gradient?)
- External data: H2 power-law temperature excitation model used for warm H2 mass  
  > "we use the H$_2$ excitation model of (cite: Togi16) (hereafter TS16)" (4.1 H2 Excitation Modeling) [from Togi & Smith 2016 (cite: Togi16)]
- External data: Starburst99 SSP templates (2, 10, 100 Myr) for the stellar continuum in CAFE  
  > "The stellar model consists of a mixture of 2, 10, and 100 Myr-old single stellar population (SSP) templates from Starburst99 (cite: starburst99)." (3.1 PAHs, Dust Continuum, and Attenuation) [from (cite: starburst99)]
- External data: Ossenkopf et al. extinction curve  
  > "we assumed the (cite: Ossenkopf92) extinction curve" (3.1 PAHs, Dust Continuum, and Attenuation) [from (cite: Ossenkopf92)]
- External data: Metallicity-dependent [Ne II]/[Ne III] to SFR relation  
  > "derive SFRs per spaxel using the relation presented in (cite: Zhuang19)" (4.3 Star Formation Rates) [from (cite: Zhuang19)]
- External data: Gas-phase metallicity Z = 2 Zsun adopted for the SFR relation  
  > "We use the extinction-corrected line luminosities and an assumed gas-phase metallicity of $Z = 2\times Z_{\odot}$ (cite: Hernandez21)" (4.3 Star Formation Rates) [from (cite: Hernandez21)]
- External data: CO(1-0) observations used to derive M_H2(CO) for comparison  
  > "Using the CO(1-0) observations of (cite: Hirota18)" (5.2 Potential CO-dark Molecular Gas) [from (cite: Hirota18)]
- External data: Galactic alpha_CO = 3.2 Msun (K km/s pc^2)^-1 adopted for M_H2(CO)  
  > "In that work they assume a Galactic $\alpha_{\mathrm{CO}}$ = 3.2 $M_{\odot}$" (5.1 Molecular Gas Contents of M83's Nuclear Region) [from TS16 (cite: Togi16), also adopted in H23 (cite: Hernandez23)]
- External data: Systemic redshift z = 0.001733 (519 km/s)  
  > "corresponding to a recession velocity of 519 km s$^{-1}$ (cite: MeyerHipass)" (4 Analysis) [from (cite: MeyerHipass)]
- External data: MRS PSF FWHM versus wavelength (Equation 1) used for the common-resolution smoothing  
  > "which is the PSF FWHM of MRS at our long-wavelength cutoff of 20.68 $\mu$m (see Equation 1 of (cite: Law23))" (2 Observations) [from (cite: Law23)]
- External data: MRS spectral resolution (Equation 1) used for instrumental broadening correction  
  > "using Equation 1 of (cite: OJones23) to determine the spectral resolution at the wavelength of each line except for S(1)" (4 Analysis) [from (cite: OJones23)]
- External data: Stellar age 8.6 Myr for the faint Region 3 area  
  > "8.6 Myr in the photometric analysis from (cite: Knapen10)" (4.3 Star Formation Rates) [from (cite: Knapen10)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation strategy and program details taken from the earlier H23 paper  
  > "Additional details on the observation strategy are given in H23, though we summarize the most important points below." (2 Observations) [from H23 (cite: Hernandez23)]
- Fixed upper temperature T_u = 2000 K for the H2 power-law model  
  > "thus assume a fixed $T_u$ = 2000 K, which we also adopt in this work" (4.1 H2 Excitation Modeling) [from TS16 (cite: Togi16)]
- Galactic alpha_CO = 3.2 adopted for M_H2(CO)  
  > "which we also adopted in H23 and the present work" (5.1 Molecular Gas Contents of M83's Nuclear Region) [from TS16 (cite: Togi16) and H23 (cite: Hernandez23)]
- Line S/N noise estimate method  
  > "in a manner similar to that used in (cite: DelPino23)" (3.2 Emission Line Maps) [from (cite: DelPino23)]
- F-test used to choose one or two Gaussian components  
  > "we compare the reduced-$\chi^2$ of the two fits in a statistical $F$-test, following (cite: Westmoquette07)" (4.3 Star Formation Rates) [from (cite: Westmoquette07)]
- Starting CAFE parameter file (MIRI-optimized starburst) that the authors then modified  
  > "We used a modified version of the MIRI-optimized starburst parameter file in" (3.1 PAHs, Dust Continuum, and Attenuation) [from CAFE (cite: cafe; Diaz-Santos et al., in prep.)]

### Not stated but needed to reproduce (our reading)

- The modified CAFE parameter file (which parameters were changed from the MIRI-optimized starburst file) and the CAFE version
- The Python TS16 implementation (footnote link is TBD)
- Exact local continuum windows and fit bounds used for the specutils Gaussian line fits, and initial guesses
- Which of the three reduced channel-1 cube products and any bad-pixel or background-subtraction options were used in the JWST pipeline, beyond the version number
- Reduction and imaging details of the ALMA CO(2-1) cube from 2013.1.01161.S (it is shown but its processing, beam and sensitivity are not given)
- How the CO-based total gas mass M_H2(CO) = 1.715e7 Msun over the FOV was computed from the Hirota et al. CO(1-0) map (aperture, mask, line ratio if any)
- Which spaxels were included in the integrated-light spectrum fit versus resolved sum, and the exact FOV mask

## Analysis recipe

1. **reduce MRS cubes and match resolution**: Standard JWST pipeline reduction of MRS data with a dedicated background pointing, residual fringe correction, wavelength axis truncated at 20.68 um, and convolution of every slice to a common 0.788 arcsec FWHM  
  > "We also applied residual fringe corrections available in the" (2 Observations); "We opted to truncate the wavelength axis of our combined data cube at 20.68 $\mu$m (the blue limit of band 4B)" (2 Observations); "we spatially smoothed our data cube to a common resolution of 0.788$''$ FWHM" (2 Observations)
   - software: JWST calibration pipeline
   - parameter: pipeline version 1.10.2, spatial pixels gridded to 0.13 arcsec  
  > "pipeline (version 1.10.2), with the spatial pixels gridded to a common scale of" (2 Observations)
   - parameter: Only the channel 1 field of view is retained  
  > "we also restrict ourselves only to the parts of our IFU data cube covered by MRS channel 1" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **model PAHs, dust continuum and attenuation per spaxel**: CAFE fits of stellar, cool and warm dust continua and PAH Drude profiles per spaxel, giving a wavelength-dependent attenuation curve  
  > "We use the Continuum and Feature Extraction software" (3.1 PAHs, Dust Continuum, and Attenuation); "Our primary dust model includes emission and absorption from cool (40 – 100 K) and warm (100 – 400 K) dust and assumes a screen geometry." (3.1 PAHs, Dust Continuum, and Attenuation)
   - software: CAFE
   - parameter: ~70 highly obscured Region 2 spaxels fit with a single 40 - 100 K dust component  
  > "For these $\sim$70 spaxels, we instead fitted the spectra with a single dust component with temperatures between 40 – 100 K." (3.1 PAHs, Dust Continuum, and Attenuation)
   - parameter: PAH Drude centroids vary up to 500 km/s; widths vary up to +/-20% of the default  
  > "We allow the centroid of the Drude profiles to vary by up to 500 km s$^{-1}$" (3.1 PAHs, Dust Continuum, and Attenuation); "We also allow the width of each component to vary by up to $\pm$20% of their default value in" (3.1 PAHs, Dust Continuum, and Attenuation)
   - assumption: Systemic redshift z = 0.001733  
  > "We began by assuming a systemic redshift of $z$ = 0.001733 (cite: MeyerHipass)" (3.1 PAHs, Dust Continuum, and Attenuation)
   - assumption: Ossenkopf et al. extinction curve  
  > "we assumed the (cite: Ossenkopf92) extinction curve" (3.1 PAHs, Dust Continuum, and Attenuation)
   - assumption: Galactic interstellar radiation field illuminates all dust components  
  > "we assume a Galactic interstellar radiation field as the illuminating source for all model dust components" (3.1 PAHs, Dust Continuum, and Attenuation)
   - fitting: _not stated_
   - validation: Residuals of +/-5% in line-free regions, with failures in the 6 - 6.6 and 11 - 13 um PAH complexes  
  > "produces acceptable model fits across the wavelength range we consider in this work (with residuals of $\pm$5% in line-free regions)" (3.1 PAHs, Dust Continuum, and Attenuation)
3. **fit emission lines and de-redden**: Subtract the CAFE dust+PAH model, fit local continuum, fit one Gaussian per H2 line and one or two Gaussians to [Ne II] 12.81 and [Ne III] 15.56 um, integrate the Gaussian for flux, divide by the CAFE attenuation fraction  
  > "We perform a local continuum fitting and subtraction in the vicinity of the lines analyzed in this work." (3.2 Emission Line Maps); "multiply the observed flux and flux uncertainty by (1/$A$) to recover the intrinsic, de-reddened line flux" (3.2 Emission Line Maps)
   - software: specutils
   - parameter: S/N > 3 for all lines and components; noise from RMS in 0.03 um windows times 2x FWHM  
  > "we measure the RMS flux density in 0.03 $\mu$m-wide windows in the pseudo-continuum around each line, then multiply this value by 2$\times$ the FWHM of the line" (3.2 Emission Line Maps); "Unless otherwise specified, we adopt a threshold of S/N $>3$ for all lines and line components" (3.2 Emission Line Maps)
   - parameter: Resolving power R = 3300 adopted for S(1) and lines at ~15 - 17 um  
  > "leading us to adopt $R$ = 3300 for the S(1) transition and other lines in this wavelength interval" (4 Analysis)
   - assumption: H2 line kinematics are not tied between lines  
  > "All fits were allowed to vary independently (i.e., the kinematics of the H$_2$ lines are not tied)." (3.2 Emission Line Maps)
   - fitting: Gaussian line fits via specutils; no sampler or priors stated  
  > "to fit a single Gaussian to each of the H$_2$ transitions listed in Table" (3.2 Emission Line Maps)
   - validation: _not stated_
4. **fit the H2 power-law excitation model**: TS16 power-law temperature distribution fit to S(1)-normalised upper-level column densities for slope n and lower bound T_l, with T_u fixed at 2000 K  
  > "the model assumes that the rotational temperatures of H$_2$ gas follow a power-law distribution" (4.1 H2 Excitation Modeling); "Both the observed and predicted columns are normalized to the S(1) line for the fitting procedure." (4.1 H2 Excitation Modeling)
   - software: Python adaptation of TS16, scipy curve_fit
   - parameter: Only pixels with four or more H2 line detections and delta n / n < 25% retained  
  > "we consider only those pixels with four or more H$_2$ line detections" (4.1 H2 Excitation Modeling)
   - parameter: T_u = 2000 K  
  > "thus assume a fixed $T_u$ = 2000 K, which we also adopt in this work" (4.1 H2 Excitation Modeling)
   - fitting: Trust Region Reflective least squares via scipy curve_fit (IDL original used Levenberg-Marquardt); priors not stated  
  > "the choice of minimization algorithm (the Levenberg-Marquardt algorithm in IDL vs. the Trust Region Reflective algorithm in" (4.1 H2 Excitation Modeling)
   - validation: Python version reproduces the IDL n, T_l and masses to within 1% on the TS16 sample  
  > "yields best-fit values of $n$, $T_l$, and H$_2$ masses $M (T > T_l)$ that are identical to the original implementation in IDL" (4.1 H2 Excitation Modeling)
5. **derive H2 masses and compare with CO**: Use TS16 Equations 9 and 14 per spaxel with three lower-bound definitions (best-fit T_l, 200 K, 80 K), also 50 K, repeated on the integrated spectrum; then find T_cal where M_H2 equals M_H2(CO)  
  > "we can then use Equations 9 and 14 in TS16 to derive total H$_2$ column densities and masses per spaxel" (4.2 Warm H2 Mass Estimates); "We iterated over values of $T_{l}^{'}$ to find a range of temperatures that satisfy" (5.2 Potential CO-dark Molecular Gas)
   - software: Python adaptation of TS16
   - parameter: Only the uncertainty on n (not T_l) is propagated to the mass  
  > "Unless otherwise specified, we propagate only the uncertainty on $n$ (and not $T_l$) to the gas mass estimates." (4.2 Warm H2 Mass Estimates)
   - assumption: Galactic alpha_CO = 3.2 Msun (K km/s pc^2)^-1 for M_H2(CO)  
  > "In that work they assume a Galactic $\alpha_{\mathrm{CO}}$ = 3.2 $M_{\odot}$" (5.1 Molecular Gas Contents of M83's Nuclear Region)
   - fitting: _not stated_
   - validation: Resolved and integrated-spectrum masses compared; they agree for the best-fit T_l but only marginally for 200 K and 80 K  
  > "the H$_2$ masses estimated from our integrated spectrum are at best only marginally consistent within uncertainties with those from our resolved analysis" (4.2 Warm H2 Mass Estimates)
6. **derive star formation rates from neon lines**: F-test chooses single or double Gaussian per line, then the Zhuang et al. 2019 relation converts extinction-corrected [Ne II] and [Ne III] luminosities to SFR and Sigma_SFR  
  > "we adopt the two-component fit if the reduced-$\chi^2$ is lowered by a factor of at least 3.289 compared to the one-component fit" (4.3 Star Formation Rates); "derive SFRs per spaxel using the relation presented in (cite: Zhuang19)" (4.3 Star Formation Rates)
   - parameter: F-test significance alpha = 0.10; S/N > 3 applied after the F-test  
  > "Only after application of the $F$-test do we then apply our detection threshold of S/N $>$ 3" (4.3 Star Formation Rates)
   - assumption: Z = 2 Zsun; distance of M83 from Saha06  
  > "We use the extinction-corrected line luminosities and an assumed gas-phase metallicity of $Z = 2\times Z_{\odot}$ (cite: Hernandez21)" (4.3 Star Formation Rates)
   - fitting: _not stated_
   - validation: _not stated_
7. **estimate cluster ages from HST/COS spectra**: Full-spectrum fitting of the four archival COS pointings with SESAMME, assuming one dominant stellar population per spectrum  
  > "uses Markov Chain Monte Carlo methods to obtain estimates of the cluster age, metallicity, E(B-V) values" (5.4 Gaseous Confirmation of a Stellar Age Gradient?)
   - software: SESAMME
   - parameter: COS aperture of 2.5 arcsec encompassing multiple clusters  
  > "which encompass multiple star clusters in a single 2$''$.5 aperture" (5.4 Gaseous Confirmation of a Stellar Age Gradient?)
   - assumption: Single dominant stellar population per input spectrum  
  > "this means that our analysis then assumes a single dominant stellar population when inferring the stellar properties of the FUV integrated-light spectra" (5.4 Gaseous Confirmation of a Stellar Age Gradient?)
   - fitting: MCMC (sampler and priors not stated)  
  > "uses Markov Chain Monte Carlo methods to obtain estimates of the cluster age, metallicity, E(B-V) values" (5.4 Gaseous Confirmation of a Stellar Age Gradient?)
   - validation: _not stated_
8. **qualitative comparison with ALMA CO(2-1)**: ALMA CO(2-1) emission from project 2013.1.01161.S is shown beside the H2 S(1) FWHM map and JWST imaging to relate the H2 point source and warm H2 to cold gas; no reduction or measurement from the ALMA data is described  
  > "including the FWHM map of the H$_2$ S(1) line; CO(2-1) emission (ALMA pID 2013.1.01161.S, PI Sakamoto)" (5.3 A Massive, Obscured Point Source); "the spatial coincidence of the H$_2$ source with CO-emitting gas" (5.3 A Massive, Obscured Point Source)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **JWST calibration pipeline** 1.10.2: Reducing MRS observations to cubes, stitched with output type multi  
  > "pipeline (version 1.10.2), with the spatial pixels gridded to a common scale of" (2 Observations)
- **CAFE** : Modelling PAH features, dust continuum and extinction per spaxel  
  > "We use the Continuum and Feature Extraction software" (3.1 PAHs, Dust Continuum, and Attenuation)
- **Starburst99** : SSP templates for the stellar component in CAFE  
  > "single stellar population (SSP) templates from Starburst99 (cite: starburst99)" (3.1 PAHs, Dust Continuum, and Attenuation)
- **specutils** : Fitting Gaussian profiles to H2 and neon lines  
  > "to fit a single Gaussian to each of the H$_2$ transitions listed in Table" (3.2 Emission Line Maps)
- **scipy curve_fit** : Trust Region Reflective minimisation in the Python TS16 implementation  
  > "the choice of minimization algorithm (the Levenberg-Marquardt algorithm in IDL vs. the Trust Region Reflective algorithm in" (4.1 H2 Excitation Modeling)
- **SESAMME** : Full-spectrum fitting of HST/COS cluster spectra for age, metallicity, E(B-V), mass  
  > "uses Markov Chain Monte Carlo methods to obtain estimates of the cluster age, metallicity, E(B-V) values" (5.4 Gaseous Confirmation of a Stellar Age Gradient?)
- **Astropy** : General analysis (named in the software acknowledgment)  
  > "and Astropy (cite: Astropy13; Astropy18; Astropy22) in our analyses" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Warm H2 mass, T_l' = best-fit T_l (resolved sum) | 1.50e5 | +0.09/-0.09 e5 | Msun | 5 | (1) $1.50^{+0.09}_{-0.09} \times 10^5 M_{\odot}$ for a variable $T_{l}^{'}$ |
| H2 mass, T_l' = 200 K (resolved sum) | 2.26e5 | +0.17/-0.19 e5 | Msun | 5 | $2.26^{+0.17}_{-0.19} \times 10^5 M_{\odot}$ for $T_{l}^{'}$ = 200 K |
| H2 mass, T_l' = 80 K (resolved sum) | 7.93e6 | +3.52/-2.59 e6 | Msun | 5 | yields (3) $7.93^{+3.52}_{-2.59} \times 10^6 M_{\odot}$ |
| H2 mass, T_l' = 50 K (resolved sum) | 8.17e7 | +8.67/-4.04 e7 | Msun | 5 | we obtain $M_{H2}(T > 50$ K) = $8.17^{+8.67}_{-4.04} \times 10^7 M_{\odot}$ |
| Median power-law slope n across FOV | 5.75 | 0.64 (1 sigma range) | dimensionless | 4 | The median slope and 1$\sigma$ range across our FOV, $n = 5.75 \pm 0.64$, |
| Best-fit T_l range across FOV | 130 - 343 K, median 247 K | not stated | K | 4 | vary from $\sim$130 – 343 K (median 247 K) |
| Integrated spectrum best-fit T_l | 215.2 | 26.2 | K | 4 | the best-fit value of $T_l$ (215.2 $\pm$ 26.2 K) |
| Integrated spectrum power-law slope n | 5.10 | 0.26 | dimensionless | 4 | the power-law slope $n$ = 5.10 $\pm$ 0.26 |
| Integrated spectrum H2 mass, T_l' = 215.2 K | 1.54e5 | +0.06/-0.07 e5 | Msun | 5 | $1.54^{+0.06}_{-0.07} \times 10^5 M_{\odot}$ for $T_{l}^{'}$ = 215.2 K |
| Integrated spectrum H2 mass, T_l' = 200 K | 1.84e5 | +0.09/-0.09 e5 | Msun | 5 | (2) $1.84^{+0.09}_{-0.09} \times 10^5 M_{\odot}$ for $T_{l}^{'}$ = 200 K |
| Integrated spectrum H2 mass, T_l' = 80 K | 4.47e6 | +0.98/-0.84 e6 | Msun | 5 | (3) $4.47^{+0.98}_{-0.84} \times 10^6 M_{\odot}$ for $T_{l}^{'}$ = 80 K. |
| CO-based molecular gas mass in the FOV | 1.715e7 | not stated | Msun | 5 | consistent with $M_{H2}$(CO) = 1.715$\times 10^7 M_{\odot}$ within the uncertainties |
| Calibration temperature T_cal, resolved analysis | 60 - 70 | range consistent within uncertainties | K | 5 | a range of temperatures $T_{cal}$ (60 – 70 K) yield an H$_2$ mass estimate |
| Calibration temperature T_cal, integrated spectrum | 57 | not stated | K | 5 | we find that $T_{cal}$ = 57 K provides the best match to $M_{H2}$(CO) |
| Total H2 mass at T_l' = 50 K relative to M_H2(CO) | ~4.7 | not stated | dimensionless | 5 | At $T_{l}^{'}$ = 50 K, the total $M_{H2}$ mass is a factor of $\sim$4.7 higher than that inferred from CO observations |
| Median tau_warm at 14 um across FOV | 0.64 | not stated | dimensionless | 2 | the median optical depth across our FOV is fairly low ($\tau_{warm} \sim$ 0.64) |
| tau_warm in the integrated spectrum | 0.49 | not stated | dimensionless | 2 | modest attenuation ($\tau_{warm}$ = 0.49) inferred by |
| Fraction of [Ne II] flux in the secondary component | ~23% on average | not stated | % | 6 | The secondary component contributes $\sim$23% of the total |
| Peak Sigma_SFR in Region 2 | ~75 | not stated | Msun yr^-1 kpc^-2 | 6 | reaching up to 75 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ in $3\times3$ pc$^2$ pixels |
| Lowest Sigma_SFR | ~1 | not stated | Msun yr^-1 kpc^-2 | 6 | with SFR densities as low as $\sim$1 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ |
| Cluster age and mass of most massive COS population (Region 2) | age 2 Myr; mass 1.13e6 Msun | age +/-1 Myr; mass +/-0.02e6 | Myr; Msun | 7 | with a mass estimate of 1.13 ($\pm$ 0.02) $\times$ 10$^{6}$ M$_\odot$ and an age of 2 $\pm$ 1 Myr |
| H2 S(1) point source core FWHM | >150 | not stated | km/s | 3 | with a FWHM of $>$150 km s$^{-1}$ at its core |

## Qualitative findings

- Warm H2 (>200 K) is a clumpy reservoir, with the most excited H2 near the optical nucleus and groupings of young massive clusters  
  > "with the most excited emission coincident with the optical nucleus and with groupings of young, massive star clusters" (6 Conclusions)
- A kinematically distinct H2 S(1) point source near CO(2-1) emission is proposed to be a forming or fully embedded star cluster  
  > "which we propose is a forming or fully-embedded star cluster given its location with respect to the CO (2-1) emission" (6 Conclusions)

## Claim tuples

- H: How much warm H2 is in the M83 nuclear region and how is it excited at ~3 pc scale? | E: TS16 power-law fits per spaxel to MRS H2 S(1)-S(7) lines, mass integrated down to several T_l' | R: Warm H2 (T > 200 K) ~2.26e5 Msun, median n = 5.75, T_l 130 - 343 K | F: The warm H2 reservoir is a ~1% fraction of the CO-based molecular gas mass and most excited near the nucleus and young clusters | **supported**
- H: Does extrapolating the H2 power law to cold temperatures imply CO-dark gas? | E: Compare M_H2(T > T_l') with M_H2(CO) from Hirota et al. CO(1-0) with Galactic alpha_CO | R: T_l' = 50 K gives ~4.7 times the CO-based mass; T_cal ~57 - 70 K matches CO | F: About 79% of molecular gas could be CO-dark, or alpha_CO is higher than Galactic, depending on the extrapolation | **partially**
- H: Does the inferred H2 mass depend on the physical scale probed? | E: Same CAFE plus TS16 analysis on spaxels and on the integrated spectrum | R: Equal for the best-fit T_l, lower in the integrated case for T_l' = 200 and 80 K | F: Hints of scale dependence within the TS16 framework | **partially**
- H: Is the H2 S(1) kinematic point source an embedded star cluster? | E: Compare S(1) FWHM and velocity maps with ALMA CO(2-1) and JWST FEAST imaging | R: Compact (<~5 pc) source with FWHM >150 km/s, coincident with CO-emitting gas and young cluster ages | F: Speculated to be a forming or fully embedded cluster | **partially**
- H: Do SFR maps and cluster ages support an age gradient in the nuclear ringlet? | E: [Ne II] and [Ne III] SFR maps plus SESAMME fits to four HST/COS pointings | R: Sigma_SFR up to ~75 in Region 2 with 2 +/- 1 Myr clusters; lowest SFR in Region 3 with older populations | F: Supports a star-forming ringlet with a mild age gradient | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Emission lines were not fit together with PAHs and continuum to save computation  
  > "We did not fit emission lines simultaneously with PAHs and mid-IR continua for the sake of computational efficiency" (3.1 PAHs, Dust Continuum, and Attenuation)
- Alternative: Two-component dust model rejected for ~70 obscured Region 2 spaxels because of physically implausible fits  
  > "we found that the two-component dust model produced physically implausible fits" (3.1 PAHs, Dust Continuum, and Attenuation)
- How they decided it was enough: _not stated_
- Limitation (authors): No S(0) line, so the sensitivity temperature cannot be constrained as in TS16  
  > "We therefore cannot directly constrain a sensitivity temperature comparable to that in TS16 for the observations presented here." (5.1 Molecular Gas Contents of M83's Nuclear Region)
- Limitation (authors): COS ages assume a single dominant stellar population per aperture  
  > "this means that our analysis then assumes a single dominant stellar population when inferring the stellar properties of the FUV integrated-light spectra" (5.4 Gaseous Confirmation of a Stellar Age Gradient?)
- Limitation (authors): Flux calibration discontinuities across MRS bands forced truncation at 20.68 um  
  > "which we attribute to issues with flux calibration across bands within the MRS pipeline" (2 Observations)
- Limitation (authors): A direct pixel-level comparison with ALMA CO data is not done  
  > "While a direct comparison of pixel-level gas masses between our MRS observations and CO data from ALMA is beyond the scope of this work" (5.2 Potential CO-dark Molecular Gas)
- Caveat (inferred, ours): ALMA data are used only qualitatively; M_H2(CO) comes from Hirota et al. CO(1-0), so the CO-dark fraction rests on a Galactic alpha_CO the authors argue is probably too high
- Caveat (inferred, ours): CO-dark claim depends strongly on extrapolating the power law below T_l, with large uncertainties at 50 K
- Caveat (inferred, ours): The median tau_warm is given as 0.64 in Section 3.1 and 0.60 in Section 4.2, and RA is printed as 13:17 and 13:37 for sources in the same field
- Caveat (inferred, ours): H2 mass uncertainty propagates only n, not T_l
- Caveat (inferred, ours): The Zhuang et al. SFR calibration covers ages up to 2.5 Myr while parts of the field are older

## Reproducibility

- Data public (paper): JWST data are in MAST; ALMA public status not stated  
  > "all JWST data used in this paper can be found in MAST:10.17909/a61h-f081" (2 Observations)
- Products in archive: _not stated_
- Code: Python adaptation of the TS16 model released for community use, but link is TBD  
  > "For this work we created a Python adaptation of the TS16 model, which we release for community use" (4.1 H2 Excitation Modeling); "Link TBD" (Footnotes)
- Missing: Modified CAFE parameter file and CAFE version
- Missing: Working link to the Python TS16 code
- Missing: ALMA CO(2-1) data processing and the CO-based mass computation
- Data volume (inferred): JWST MRS cubes for four pointings and three gratings, likely several GB to tens of GB; ALMA CO(2-1) cube is not needed for the numeric results
- Score (inferred): 3/5, JWST data are public and the TS16 analysis is described with numeric results, but the modified CAFE setup and code link are missing and ALMA plays only a qualitative role
- Rediscovery candidate: no, The ALMA data are not central, and the modified CAFE configuration and TS16 code link are not given, so the main numbers cannot be redone from the paper alone

## Links

- Method: Togi & Smith 2016 (cite: Togi16) (H2 power-law excitation model)
- Method: (cite: cafe) (CAFE continuum and PAH fitting)
- Method: Jones et al. 2023a (cite: Jones2023) (SESAMME full-spectrum cluster fitting)
- Method: Zhuang et al. 2019 (cite: Zhuang19) (Neon-line SFR relation)
- Companion: Hernandez et al. 2023 (cite: Hernandez23) (First paper on the same MRS dataset, with integrated regional spectra)
- Companion: Hirota et al. 2018 (cite: Hirota18) (CO(1-0) data used for M_H2(CO))
- Companion: Adamo et al., in prep. (JWST FEAST imaging of M83)
- Related: JWST GO 02219
- Related: JWST FEAST (GO 1783)
- Related: ALMA 2013.1.01161.S
- Related: HST/COS programs 11579, 14681, 15193

## Checks

```json
{
 "quotes": 125,
 "quotes_ok": 125,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2022.1.00951.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 120,
  "stated": 74,
  "rate": 0.617
 },
 "evidence_ok": true
}
```
