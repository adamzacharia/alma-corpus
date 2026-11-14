# Properties of giant molecular clouds in the strongly barred galaxy NGC 1300

`2020MNRAS.493.5045M` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Maeda, Fumiya | arXiv: 2002.08977 | DOI: 10.1093/mnras/staa556

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Do GMC properties (radius, velocity dispersion, mass, virial parameter) differ between bar, arm and bar-end regions of the strongly barred galaxy NGC 1300, where star formation efficiency differs?  
  > "Our main goals are to measure the properties of GMCs and investigate whether there are differences in the properties with environments." (Introduction); "we find that there is virtually no significant variations in GMC properties" (abstract)
- Target **NGC 1300 (western bar, arm and bar-end regions)**: coordinates Center 03h19m41.036s, -19d24m40.00s (J2000; Table 1); two pointings observed  
  > "$\rm 03^h19^m41^s.036$" (Table 1); "$\rm -19^\circ24^\prime40^{\prime\prime}.00$" (Table 1); "the distance to NGC 1300 of 20.7 Mpc" (4.2.1 Size, velocity width and CO luminosity); "We adopted the systemic velocity with corrections for" (Table 1); z/distance 20.7 Mpc  
  > "$\rm 03^h19^m41^s.036$" (Table 1); "$\rm -19^\circ24^\prime40^{\prime\prime}.00$" (Table 1); "the distance to NGC 1300 of 20.7 Mpc" (4.2.1 Size, velocity width and CO luminosity); "We adopted the systemic velocity with corrections for" (Table 1); distance from systemic velocity 1511 km/s (corrected for Virgo, Great Attractor, Shapley; cite: MouldEtAl00) with H0 = 73 km/s/Mpc  
  > "$\rm 03^h19^m41^s.036$" (Table 1); "$\rm -19^\circ24^\prime40^{\prime\prime}.00$" (Table 1); "the distance to NGC 1300 of 20.7 Mpc" (4.2.1 Size, velocity width and CO luminosity); "We adopted the systemic velocity with corrections for" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00248.S
- bands: Band 3  
  > "We used the Band 3 receiver with the central frequency of 114.664 GHz" (Observations and Data Reduction)
- frequencies and spectral setup: central frequency 114.664 GHz; channel width 244.1 kHz (~0.64 km/s); bandwidth 468.8 MHz (~1225 km/s)  
  > "We used the Band 3 receiver with the central frequency of 114.664 GHz, channel width of 244.1 kHz" (Observations and Data Reduction); "bandwidth of 468.8 MHz" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array (about 44 antennas)  
  > "with ALMA 12-m array at a high angular resolution of" (abstract); "For all observations, we used about 44 antennas with C43-5 configuration." (Observations and Data Reduction)
- configurations: C43-5  
  > "For all observations, we used about 44 antennas with C43-5 configuration." (Observations and Data Reduction)
- baselines: 15.1 m to 2.5 km  
  > "The projected baseline length ranged from 15.1 m to 2.5 km" (Observations and Data Reduction)
- angular resolution: 0.44 arcsec x 0.30 arcsec (~40 pc)  
  > "The final data cube has an angular resolution of $0.44^{\prime\prime} \times 0.30^{\prime\prime}$." (Observations and Data Reduction)
- max recoverable scale: ~21.4 arcsec at 115 GHz  
  > "which corresponds to a maximum recoverable scale (MRS) of $\sim 21.4^{\prime\prime}$ at 115 GHz" (Observations and Data Reduction)
- sensitivity: rms 0.51 mJy/beam (0.36 K) at 5 km/s  
  > "The resultant rms noise is 0.51 $\rm mJy~beam^{-1}$, corresponding to 0.36 K." (Observations and Data Reduction)
- time on source: 5.31 hours total (2.65 hours per position)  
  > "The total on-source time was 5.31 hours (2.65 hours for each position)." (Observations and Data Reduction)
- observing dates: 2017 Dec 30; 2018 Jan 6, 7, 13, 16 (seven execution blocks)  
  > "line observations of NGC 1300 on 2017 December 30 and 2018 January 6, 7, 13, and 16 with ALMA" (Observations and Data Reduction)
- pi or archival as stated: PI program, PI = F. Maeda (first author)  
  > "program ID: 2017.1.00248.S, PI = F. Maeda" (Observations and Data Reduction)
- Line: 12CO J=1-0 (not stated (central frequency 114.664 GHz; 115 GHz quoted))
- Other facility **Nobeyama 45-m telescope**: Single-dish 12CO(1-0) data (Maeda et al. 2018) used to estimate the ALMA flux recovery fraction  
  > "with those from Nobeyama 45-m single-dish telescope by (cite: Maeda:2018bg)" (5.2.2 Impact of the missing flux)
- Other facility **Plateau de Bure Interferometer + IRAM 30-m (M51 comparison data)**: M51 12CO(1-0) cube (Schinnerer et al. 2013) whose resolution and sensitivity are comparable, motivating the CPROPS setup  
  > "which was observed with the Plateau de Bure Interferometer and IRAM 30-m telescope at a spatial resolution of" (4.1 GMCs Identification)
- External data: M51 spiral-arm GMC catalog used as comparison sample  
  > "we compare the properties of GMCs in spiral arms of proto-type spiral galaxy of M51 by (cite: Colombo:2014ei)" (Introduction) [from (cite: Colombo:2014ei)]
- External data: NGC 1300 inclination 50.2 deg  
  > "(cite: England1989a)" (Table 1) [from (cite: England1989a)]
- External data: Morphology SB(s)bc  
  > "(cite: Sandae_Tammann)" (Table 1) [from (cite: Sandae_Tammann)]
- External data: Systemic velocity 1511 km/s with Virgo/Great Attractor/Shapley corrections, used for the 20.7 Mpc distance  
  > "(cite: MouldEtAl00)" (Table 1) [from (cite: MouldEtAl00)]
- External data: Nobeyama 45-m 12CO(1-0) single-pointing fluxes in NGC 1300  
  > "with those from Nobeyama 45-m single-dish telescope by (cite: Maeda:2018bg)" (5.2.2 Impact of the missing flux) [from (cite: Maeda:2018bg)]
- Simulation/model as data: Mock 3-D Gaussian GMCs (100 per realization, 12 repeats) observed with CASA simobserve under the same configuration and noise, to test CPROPS bias  
  > "We create a fits image with 100 mock GMCs centered in fixed positions." (CPROPS bias (Appendix)); "We repeated this procedure 12 times" (CPROPS bias (Appendix))
- Simulation/model as data: Noise-free simobserve of a circular Gaussian of 1.0 Jy with FWHM 100-1500 pc to derive flux recovery fraction versus size  
  > "we simulated ALMA observation of a mock Gaussian component." (5.2.2 Impact of the missing flux); "The FWHM was set from 100 pc to 1500 pc every 100 pc." (5.2.2 Impact of the missing flux)

## Processing

### Calibration

- pipeline or manual: observatory-provided calibration script run in CASA 5.1.1  
  > "We calibrated raw visibility data using the Common Astronomy Software Applications (CASA) ver. 5.1.1. and the observatory-provided calibration script." (Observations and Data Reduction)
- casa version: CASA 5.1.1 (calibration); CASA 5.4.0 (imaging)  
  > "We calibrated raw visibility data using the Common Astronomy Software Applications (CASA) ver. 5.1.1." (Observations and Data Reduction); "We reconstructed the two-field mosaic image using CASA ver. 5.4.0." (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (also bandpass); phase calibrator J0340-2119  
  > "Bandpass and phase were calibrated with J0423-0120 and J0340-2119, respectively." (Observations and Data Reduction); "J0423-0120 was also used as a flux calibrator." (Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: concat of the two pointings, then tclean (multiscale CLEAN) mosaic  
  > "First, we combined the calibrated visibility data of the 2 pointing positions using" (Observations and Data Reduction); "for imaging by adopting the factors of 1, 2, and 5 times the synthesized beam as multiscale parameter and Briggs weighting with robust = 0.5" (Observations and Data Reduction)
- deconvolver: multiscale CLEAN (Cornwell 2008)  
  > "CLEAN algorithm (cite: Cornwell2008), which models an image by a collection of multiple Gaussians with different FWHM values" (Observations and Data Reduction)
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with robust = 0.5" (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: 0.12 arcsec; channel width 5 km/s  
  > "we choose a velocity resolution of $5~\rm km~s^{-1}$ and a pixel size of $0.^{\prime\prime}12$" (Observations and Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 1, 2 and 5 times the synthesized beam  
  > "adopting the factors of 1, 2, and 5 times the synthesized beam as multiscale parameter" (Observations and Data Reduction)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to restored image; region with correction factor < 2.0 used  
  > "Finally, we applied the primary beam correction on the output restored image." (Observations and Data Reduction); "we used the region within the primary beam correction factor smaller than 2.0" (Observations and Data Reduction)
- array combination: 12-m only (no ACA); two pointings combined with concat  
  > "due to the lack of Atacama Compact Array (ACA) measurements" (5.2.2 Impact of the missing flux)
- smoothing: _not stated_
- final beam: 0.44 x 0.30 arcsec  
  > "The final data cube has an angular resolution of $0.44^{\prime\prime} \times 0.30^{\prime\prime}$." (Observations and Data Reduction)
- final rms: 0.51 mJy/beam (0.36 K) per 5 km/s channel  
  > "The resultant rms noise is 0.51 $\rm mJy~beam^{-1}$, corresponding to 0.36 K." (Observations and Data Reduction)

### Inherited from earlier work

- CPROPS parameters taken almost unchanged from the M51 GMC analysis for a like-for-like comparison  
  > "we adopt almost the same CPROPS parameters adopted in to make a proper comparison and minimize systematics" (4.1 GMCs Identification) [from M51 GMC study (reference omitted in the text; context cites Colombo et al. 2014, cite: Colombo:2014ei, and Schinnerer et al. 2013, cite: Schinnerer:2013jy)]
- CPROPS threshold t = 4.0 and edge e = 1.5  
  > "We chose $t = 4.0$ and $e = 1.5$ to ensure consistency with ." (4.1 GMCs Identification) [from M51 GMC study (reference omitted in the text)]
- Standard alpha_CO = 4.4 Msun/(K km/s pc^2) including helium factor 1.36  
  > "includes a factor of 1.36 to account for the presence of helium" (4.2.2 Derived Properties) [from M51 GMC study (reference omitted in the text, 'to ensure consistency with')]
- Density profile exponent n = 1 for virial mass  
  > "We assume that magnetic fields and external pressure are negligible." (4.2.2 Derived Properties) [from previous studies ('to ensure consistency with previous studies')]
- 50 bootstrap measurements for CPROPS uncertainties  
  > "found that 50 bootstrapping measurements provided a reliable estimation of the uncertainty, thus we adopted this number." (4.2.2 Derived Properties) [from reference omitted in the text (CPROPS uncertainty estimate)]
- CPROPS algorithm details (moment methods, extrapolation, deconvolution)  
  > "Details of the measurement method of CPROPS are described in (cite: RosolowskyLeroy)." (4.2.1 Size, velocity width and CO luminosity) [from (cite: RosolowskyLeroy)]
- M51 comparison sample extracted with the same selection criteria and box-and-whisker presentation  
  > "We use a box and whiskers plot as used for M51." (5.1 Variation of GMC physical properties with environment) [from M51 GMC catalog (cite: Colombo:2014ei)]

### Not stated but needed to reproduce (our reading)

- tclean niter, cleaning threshold, mask and gridder settings are not given
- Which channels or velocity range were cleaned, and how the 5 km/s cube was built (tclean width versus rebinning) are not stated
- No continuum subtraction or line-free channels are mentioned for the 12CO cube
- CPROPS parameters beyond THRESHOLD, EDGE, SIGDISCONT, NONUNIFORM and the one-channel island option are not given (e.g. minimum pixels, minimum area, fixed beam or other keywords)
- The M51 reference for the inherited CPROPS settings is missing in the text, so the exact parameter file cannot be reconstructed
- Polygon boundaries of the Bar, Arm and Bar-end regions are shown only graphically
- Source of the V-band/H-alpha comparison images is not given
- Flux-scale uncertainty and self-calibration are not stated
- Whether the 2017.1.00248.S data are publicly available is not stated
- Exact least-squares or fitting routine for the truncated power-law mass spectrum is not given

## Analysis recipe

1. **Calibrate and image the 12CO(1-0) two-field mosaic**: Observatory calibration script in CASA 5.1.1; concat of the two pointings; tclean multiscale CLEAN mosaic in CASA 5.4.0; primary-beam correction  
  > "We calibrated raw visibility data using the Common Astronomy Software Applications (CASA) ver. 5.1.1. and the observatory-provided calibration script." (Observations and Data Reduction); "We reconstructed the two-field mosaic image using CASA ver. 5.4.0." (Observations and Data Reduction)
   - software: CASA, concat, tclean
   - parameter: multiscale scales 1, 2, 5 x synthesized beam; Briggs robust = 0.5  
  > "adopting the factors of 1, 2, and 5 times the synthesized beam as multiscale parameter and Briggs weighting with robust = 0.5" (Observations and Data Reduction)
   - parameter: 5 km/s channels, 0.12 arcsec pixels  
  > "we choose a velocity resolution of $5~\rm km~s^{-1}$ and a pixel size of $0.^{\prime\prime}12$" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify GMCs in the cube**: 3-D clump finding with CPROPS: islands above threshold, watershed decomposition into clouds  
  > "we used 3-D clumps finding algorithm CPROPS (cite: RosolowskyLeroy) which is designed to identify GMCs well even at low sensitivities" (4.1 GMCs Identification); "CPROPS searches for local maxima within a box of three times the beam and channel width" (4.1 GMCs Identification)
   - software: CPROPS
   - parameter: THRESHOLD t = 4.0, EDGE e = 1.5  
  > "We chose $t = 4.0$ and $e = 1.5$ to ensure consistency with ." (4.1 GMCs Identification)
   - parameter: SIGDISCONT = 0.0 (each local maximum is an independent cloud)  
  > "to 0.0 which makes no attempt to merge the two local maxima into a single cloud" (4.1 GMCs Identification)
   - parameter: NONUNIFORM flag used for spatially varying rms noise  
  > "Thus, we calculated a spatially varying of the rms noise in the map by calling" (4.1 GMCs Identification)
   - parameter: Islands allowed with pixels above 4 sigma in only one channel  
  > "we allowed CPROPS to identify an island which has pixels above" (4.1 GMCs Identification)
   - fitting: _not stated_
   - validation: Visual inspection of line profiles; same search on the cube scaled by -1 found false positives only among single-channel detections (3 of 67)  
  > "We inspected the CO line profiles from each GMC CPROPS identified visually, and an obvious spurious signal was not found." (5 Basic properties of GMCs); "CPROPS identified three false positives which have pixels above" (5 Basic properties of GMCs)
3. **Measure and derive GMC physical properties**: CPROPS moment measurements extrapolated to zero sensitivity and deconvolved; L_CO from F_CO and distance; M_mol = alpha_CO L_CO; virial mass, surface density, virial parameter and scaling coefficient from R and sigma_v  
  > "CPROPS determines the size, velocity width and flux of GMCs using moment methods." (4.2.1 Size, velocity width and CO luminosity); "CPROPS corrects for the sensitivity by extrapolating GMC properties to those we would expect to measure with perfect sensitivity" (4.2.1 Size, velocity width and CO luminosity)
   - software: CPROPS
   - parameter: Distance 20.7 Mpc  
  > "the distance to NGC 1300 of 20.7 Mpc" (4.2.1 Size, velocity width and CO luminosity)
   - parameter: R = (3.4/sqrt(pi)) sigma_r  
  > "The effective radius of the GMC is defined as $R = (3.4/\sqrt{\pi})\sigma_{r}$" (4.2.1 Size, velocity width and CO luminosity)
   - parameter: Uncertainties from bootstrapping with 50 realizations  
  > "CPROPS estimates the uncertainty of these GMC properties using a bootstrapping method" (4.2.2 Derived Properties)
   - assumption: alpha_CO = 4.4 Msun (K km/s pc^2)^-1, including a factor 1.36 for helium  
  > "includes a factor of 1.36 to account for the presence of helium" (4.2.2 Derived Properties)
   - assumption: Spherical cloud with rho proportional to r^-n, n = 1; magnetic fields and external pressure negligible  
  > "We assume that magnetic fields and external pressure are negligible." (4.2.2 Derived Properties)
   - fitting: _not stated_
   - validation: Mock-GMC simulations (step 8)  
  > "In order to assess the reliability of the measurements of GMC properties, we simulated ALMA observation of mock GMCs" (5.2.1 CPROPS bias)
4. **Define mass-complete and resolved samples**: Mass-completeness limit from minimum detectable GMC; resolved sample requires Mmol >= 5e5 Msun and R > 15 pc, mass-complete sample Mmol > 2e5 Msun  
  > "The mass completeness limit is estimated to be $2.0 \times 10^5 ~M_\odot$" (5 Basic properties of GMCs); "we defined the GMCs with $M_{\rm mol} \geq 5.0 \times 10^5~M_\odot$ and $R > 15$ pc as a resolved sample" (5 Basic properties of GMCs)
   - fitting: _not stated_
   - validation: Ratio of directly measured to corrected radius examined versus radius; 154 of 233 GMCs resolved  
  > "We find that 154 of these 233 GMCs are resolved by the synthesized beam." (5 Basic properties of GMCs)
5. **Test environmental variation of GMC properties**: Two-sided two-sample K-S test between Bar, Arm and Bar-end; p-value and uncertainty from 100 resampled realizations (median and MAD)  
  > "We used the two-sided Kolmogorov-Smirnov (K-S) test to statistically evaluate differences in GMC property distributions for different environments in NGC 1300." (5.1 Variation of GMC physical properties with environment); "To estimate the uncertainties of the $p$-values, we made resampling with 100 realizations." (5.1 Variation of GMC physical properties with environment)
   - software: SciPy
   - parameter: Significant if p < 0.01, marginal for 0.01 to 0.05  
  > "the two cumulative distribution functions are considered to be significantly different if the $p$-value is less than 0.01" (5.1 Variation of GMC physical properties with environment)
   - parameter: T_peak uncertainty taken as the cube rms, 0.36 K  
  > "we applied rms noise of the data cube, 0.36 K as the uncertainty" (5.1 Variation of GMC physical properties with environment)
   - fitting: _not stated_
   - validation: Re-ran K-S test on catalog corrected for CPROPS bias; p-values do not change much  
  > "We retested the environmental variation of the GMC properties using the corrected catalog." (CPROPS bias (Appendix))
6. **Examine scaling relations**: Spearman rank correlation and ordinary least-squares fits for size-velocity dispersion, virial-luminous mass, size-mass and sigma_v^2/R versus Sigma_mol for resolved GMCs  
  > "we calculate the Spearman’s rank correlation coefficient" (6 Scaling relations); "represents the best-fitted line determined by the ordinary least-squares method" (6.2 Virial Equilibrium)
   - parameter: r_s >= 0.8 strong, 0.5 < r_s < 0.8 moderate  
  > "we regard $r_s \geq 0.8$ as a sign of strong correlation" (6 Scaling relations)
   - fitting: Ordinary least squares  
  > "represents the best-fitted line determined by the ordinary least-squares method" (6.2 Virial Equilibrium)
   - validation: _not stated_
7. **Fit cumulative GMC mass spectra**: Truncated power-law cumulative mass function (Williams and McKee 1997) fitted to GMCs above 5e5 Msun; errors from 100 resampled realizations  
  > "a truncated power-law is suitable as a cumulative mass spectrum" (7 GMC mass spectra); "Thus, we fitted the mass spectrum using the GMCs with" (7 GMC mass spectra)
   - parameter: 100 resampling realizations; median and MAD adopted as best fit and interval  
  > "The median and the MAD of 100 realizations for each parameter were adopted as the best-fitted value and the confidence interval" (7 GMC mass spectra)
   - fitting: Truncated power law with gamma, M_u, N_u free; fitting algorithm, priors and likelihood not stated  
  > "We fitted the cumulative GMC mass spectrum with equation" (7 GMC mass spectra)
   - validation: K-S test p-values as goodness of fit  
  > "We list the $p$-values of the K-S tests as an indication of the goodness-of-fit" (7 GMC mass spectra)
8. **Assess systematics: CPROPS bias and missing flux**: CASA simobserve of mock 3-D Gaussian GMCs followed by tclean and CPROPS; flux-recovery test with Gaussian sources and comparison with Nobeyama 45-m spectra  
  > "we simulate observation under the same configuration, pointings, and noise condition of our ALMA observations" (CPROPS bias (Appendix)); "We find that the average recovery fraction is 54 % with typical uncertainty of 5 %" (5.2.2 Impact of the missing flux)
   - software: CASA, simobserve, tclean, CPROPS
   - parameter: log Mmol 5.3-6.8, log R 1.5-2.2, log sigma_v 0.3-1.1; axis ratio 1.0; 12 repeats; S/N 4-10 extracted  
  > "$1.5\leq \log(R/[{\rm pc}]) \leq 2.2$" (CPROPS bias (Appendix)); "The GMCs are round clouds (i.e., axis ratio = 1.0)." (CPROPS bias (Appendix))
   - assumption: alpha_CO 4.4 for mock clouds  
  > "Here, we assume the CO-to-H$_2$ conversion factor of $4.4~M_\odot~(\rm K~km~s^{-1}~pc^2)^{-1}$." (CPROPS bias (Appendix))
   - fitting: _not stated_
   - validation: Correction factors applied to the catalog and K-S tests repeated; conclusions unchanged  
  > "Therefore, the over/underestimation of the measurements does not influence on the discussion about the environmental variation" (CPROPS bias (Appendix))

## Software

- **CASA** 5.1.1 (calibration); 5.4.0 (imaging): Calibration and imaging of the ALMA data, and simobserve simulations  
  > "We reconstructed the two-field mosaic image using CASA ver. 5.4.0." (Observations and Data Reduction)
- **tclean** : Multiscale CLEAN imaging of the mosaic and of the simulated data  
  > "for imaging by adopting the factors of 1, 2, and 5 times the synthesized beam as multiscale parameter" (Observations and Data Reduction)
- **concat** : Combining the two pointings' calibrated visibilities  
  > "First, we combined the calibrated visibility data of the 2 pointing positions using" (Observations and Data Reduction)
- **simobserve** : Simulating ALMA observations of mock GMCs and Gaussian components  
  > "we simulate observation under the same configuration, pointings, and noise condition of our ALMA observations" (CPROPS bias (Appendix))
- **CPROPS** : GMC identification and property measurement  
  > "we used 3-D clumps finding algorithm CPROPS (cite: RosolowskyLeroy) which is designed to identify GMCs well even at low sensitivities" (4.1 GMCs Identification)
- **SciPy** : stats.ks_2samp for the two-sample K-S tests  
  > "function of python’s Scipy package" (5.1 Variation of GMC physical properties with environment)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Image rms noise | 0.51 mJy/beam (0.36 K) | not stated | mJy/beam | 1 | The resultant rms noise is 0.51 $\rm mJy~beam^{-1}$, corresponding to 0.36 K. |
| Final beam | 0.44 x 0.30 | not stated | arcsec | 1 | The final data cube has an angular resolution of $0.44^{\prime\prime} \times 0.30^{\prime\prime}$. |
| Number of GMCs identified | 233 | not stated | dimensionless | 2 | CPROPS identified 233 GMCs in the data cube. |
| GMCs per environment (Bar, Arm, Bar-end) | 34, 119, 49 (31 in interarm) | not stated | dimensionless | 2 | We detected 34, 119, and 49 GMCs in |
| Mass completeness limit | 2.0e5 | not stated | Msun | 4 | The mass completeness limit is estimated to be $2.0 \times 10^5 ~M_\odot$ |
| Median T_peak, Bar | 2.2 | +0.2/-0.2 | K | 3 | $2.2^{+0.2}_{-0.2}$ |
| Median T_peak, Arm | 2.6 | +0.7/-0.4 | K | 3 | $2.6^{+0.7}_{-0.4}$ |
| Median T_peak, Bar-end | 3.5 | +0.8/-0.7 | K | 3 | $3.5^{+0.8}_{-0.7}$ |
| Median sigma_v, Bar | 5.7 | +0.8/-0.9 | km/s | 3 | $5.7^{+0.8}_{-0.9}$ |
| Median sigma_v, Arm | 5.0 | +1.5/-0.8 | km/s | 3 | $5.0^{+1.5}_{-0.8}$ |
| Median sigma_v, Bar-end | 5.6 | +2.0/-0.9 | km/s | 3 | $5.6^{+2.0}_{-0.9}$ |
| Median M_mol, Bar | 5.5e5 | +2.7/-1.8 (e5) | Msun | 3 | $5.5^{+2.7}_{-1.8}$ |
| Median M_mol, Arm | 5.1e5 | +4.6/-1.7 (e5) | Msun | 3 | $5.1^{+4.6}_{-1.7}$ |
| Median M_mol, Bar-end | 8.4e5 | +7.1/-3.4 (e5) | Msun | 3 | $8.4^{+7.1}_{-3.4}$ |
| Median alpha_vir, Bar | 2.3 | +0.6/-1.0 | dimensionless | 3 | $2.3^{+0.6}_{-1.0}$ |
| Median alpha_vir, Arm | 1.7 | +0.4/-0.7 | dimensionless | 3 | $1.7^{+0.4}_{-0.7}$ |
| Median alpha_vir, Bar-end | 1.3 | +0.9/-0.4 | dimensionless | 3 | $1.3^{+0.9}_{-0.4}$ |
| Fraction of unbound GMCs (alpha_vir > 2), Bar | 58 % | 8 % | percent | 3 | $58 \pm 8$ % of the GMCs in |
| Fraction of unbound GMCs, Arm and Bar-end | 33 % and 29 % | 4 % and 3 % | percent | 3 | $33 \pm 4$ % and $29 \pm 3$ % |
| K-S p-value M_mol, Bar vs Bar-end | 0.027 | 0.017 | dimensionless | 5 | $0.027 \pm 0.017 (0.037)$ |
| K-S p-value M_mol, Arm vs Bar-end | 0.007 | 0.004 | dimensionless | 5 | $0.007 \pm 0.004 (0.004)$ |
| K-S p-value alpha_vir, Bar vs Arm | 0.183 | 0.114 | dimensionless | 5 | $0.183 \pm 0.114 (0.050)$ |
| Spearman r_s, size versus velocity dispersion | -0.04 | not stated | dimensionless | 6 | the correlation is not seen ($r_s = -0.04$) |
| M_vir versus M_mol power-law index, whole region | 0.70 | 0.35 | dimensionless | 6 | $M_{\rm vir} \propto M_{\rm mol}^{0.70 \pm 0.35}$ in the whole region |
| Median P_int/k, Bar, Arm, Bar-end | 2.2, 2.9, 3.3 (x1e5) | +6.2/-1.4, +4.6/-2.5, +10.5/-1.6 | cm^-3 K | 6 | $2.2^{+6.2}_{-1.4}$, $2.9^{+4.6}_{-2.5}$, and $3.3^{+10.5}_{-1.6} \times 10^5~\rm cm^{-3}~K$ |
| Mass spectrum slope gamma, Bar | -1.97 | 0.20 | dimensionless | 7 | $-1.97 \pm 0.20$ |
| Mass spectrum slope gamma, Arm | -2.08 | 0.10 | dimensionless | 7 | $-2.08 \pm 0.10$ |
| Mass spectrum slope gamma, Bar-end | -1.66 | 0.07 | dimensionless | 7 | $-1.66 \pm 0.07$ |
| Upper cutoff mass M_u, Bar | 6.26e6 | 3.04e6 | Msun | 7 | $6.26 \pm 3.04$ |
| Upper cutoff mass M_u, Arm | 5.31e6 | 0.36e6 | Msun | 7 | $5.31 \pm 0.36$ |
| Upper cutoff mass M_u, Bar-end | 14.8e6 | 0.93e6 | Msun | 7 | $14.8 \pm 0.93$ |
| ALMA flux recovery fraction versus Nobeyama 45-m | 54 % | 5 % | percent | 8 | We find that the average recovery fraction is 54 % with typical uncertainty of 5 % |
| Overestimate of sigma_v by CPROPS for narrow lines | ~1.5 | not stated | dimensionless | 8 | CPROPS overestimates $\sigma_v$ by a factor of $\sim 1.5$ regardless of S/N |

## Qualitative findings

- GMCs are detected on the dark lanes in the bar region, where massive star formation is not seen  
  > "We detected GMCs associated with the dark lanes not only in the arm and bar-end regions but also in the bar region, where massive star formation is not seen." (abstract)
- GMC properties in NGC 1300 are roughly comparable to those in M51 spiral arms, especially in Bar-end  
  > "we find the properties of GMCs in NGC 1300 are roughly comparable to those in M51 spiral arms" (5.1 Variation of GMC physical properties with environment)
- Massive GMCs above 5e6 Msun are found only in Bar-end  
  > "In particular, GMCs more than" (7 GMC mass spectra)

## Claim tuples

- H: GMC physical properties differ between bar, arm and bar-end environments and explain SFE differences | E: CPROPS GMC catalog of 233 clouds, two-sided K-S tests between environments | R: Only T_peak differs significantly and M_mol marginally between Bar-end and the others; sigma_v, R, M_vir, Sigma_mol, alpha_vir and c show no significant variation | F: Systematic differences in GMC properties are not the cause of SFE differences with environment | **supported**
- H: GMCs in NGC 1300 resemble GMCs in a normal spiral galaxy (M51 arms) | E: Compare medians and quartiles of properties, scaling relations and mass spectra to the M51 catalog analysed with the same criteria | R: Properties are roughly comparable; Bar-end is very similar, Bar and Arm have median M_mol about 2 times lower | F: NGC 1300 GMCs are broadly similar to M51 arm GMCs, with Bar-end the closest | **supported**
- H: The GMC mass spectrum differs between environments | E: Truncated power-law fits to cumulative mass spectra | R: Bar and Arm have gamma about -2.0 and M_u about 5e6 Msun; Bar-end has a flatter slope (-1.66) and larger M_u | F: Massive GMCs are favoured in Bar-end, similar to M51 arms | **supported**
- H: Fast cloud-cloud collisions in the bar control the SFE | E: Discussion comparing results with a simulation (Fujimoto et al. in prep.) and single-dish velocity dispersions; no direct collision-speed measurement | R: No GMC property variation found; collision speeds not measured | F: Other mechanisms such as fast CCCs may control the SFE of GMCs | **partially**
- H: CPROPS biases and missing flux affect the environmental comparison | E: Mock-GMC simulations with simobserve and tclean; flux recovery versus Nobeyama 45-m; K-S re-tests on bias-corrected catalog | R: sigma_v overestimated by ~1.5 for narrow lines, R and M_mol underestimated by 10-20 %; p-values change little; 54 % flux recovery | F: Biases do not alter the environmental conclusions; GMC-scale flux is recovered but structures above ~700 pc are resolved out | **supported**

## Reasoning

- Why this data: A strongly barred galaxy shows clear absence of star formation in the bar, giving a clean test of environment effects on GMCs  
  > "A strongly barred galaxy is a suitable laboratory for studying the impact of the galactic environments on the GMCs properties" (Introduction)
- Why this method: CPROPS is built for low-sensitivity data and matches the M51 analysis; multiscale CLEAN reduces the negative bowl and recovers extended emission  
  > "which is designed to identify GMCs well even at low sensitivities" (4.1 GMCs Identification); "this method works well in reducing the depth of negative emission features" (Observations and Data Reduction)
- Alternative: Default SIGDISCONT > 0 rejected because it misses GMCs in CO-bright Bar-end; set to 0.0  
  > "CPROPS misses objects that visual inspection suggests are GMCs" (4.1 GMCs Identification)
- How they decided it was enough: _not stated_
- Limitation (authors): No ACA data, so about half the total CO flux is missed and structures larger than ~700 pc are resolved out  
  > "due to the lack of Atacama Compact Array (ACA) measurements" (5.2.2 Impact of the missing flux); "about half of the total flux was missed, which could affect the measurements of GMC properties" (5.2.2 Impact of the missing flux)
- Limitation (authors): Many cataloged sigma_v values may be overestimated by ~1.5 because lines are narrow compared to the channel width  
  > "Therefore, a large number of cataloged GMCs may be overestimated in the" (5.2.1 CPROPS bias)
- Limitation (authors): Only 154 of 233 GMCs are resolved; radii near the beam are highly uncertain  
  > "We find that 154 of these 233 GMCs are resolved by the synthesized beam." (5 Basic properties of GMCs)
- Caveat (inferred, ours): Many CPROPS settings are inherited from an unnamed M51 reference whose citation is missing in the text.
- Caveat (inferred, ours): Table 2 gives M_u(Bar-end) = 14.8 +/- 0.93 x1e6 Msun while the text gives (1.3 +/- 3.4) x1e7 Msun.
- Caveat (inferred, ours): Region masks (Bar, Arm, Bar-end) are drawn by hand, so environment assignment is not reproducible from the text alone.
- Caveat (inferred, ours): Roughly 70 % of GMCs are detected at S/N 4-7 and 67 of 233 have only single-channel peaks, so catalog completeness and sigma_v are sensitive to CPROPS settings.
- Caveat (inferred, ours): K-S tests with small samples per environment have limited power to detect real differences.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: GMC catalog tabulated in an appendix; no code or scripts released  
  > "The catalog of GMCs we identified is presented in Appendix" (Introduction)
- Missing: tclean niter, threshold, mask and gridder settings
- Missing: Full CPROPS parameter set and the M51 reference parameters
- Missing: Region mask polygons for Bar, Arm and Bar-end
- Missing: Exact fitting routine for the mass spectrum and OLS fits
- Missing: Statement that ALMA data are public and archive product versions
- Data volume (inferred): About 50-100 GB for the seven 12-m Band 3 execution blocks with 1920 channels (rough inference); final cube a few GB
- Score (inferred): 3/5, ALMA project code, CASA versions, key tclean choices, CPROPS threshold/edge/SIGDISCONT and full numeric tables are given; but cleaning depth, masks, region polygons and inherited M51 parameters are not.
- Rediscovery candidate: yes, Single project code (2017.1.00248.S, Cycle 5 data presumably public by now), imaging and CPROPS recipe mostly specified, and results are numeric tables and a published catalog allow checking; exact numbers may differ because of unstated settings.

## Links

- Method: (cite: RosolowskyLeroy) (CPROPS algorithm and bias correction)
- Method: (cite: Cornwell2008) (multiscale CLEAN)
- Method: (cite: Rich2008AJ) (multiscale CLEAN reduces negative bowl)
- Method: (cite: Stephens:1970ic) (K-S p-value approximation)
- Method: (cite: WilliamsMcKee1997ApJ) (truncated power-law mass spectrum)
- Companion: (cite: Maeda:2018bg) (Nobeyama 45-m 12CO(1-0) observations of NGC 1300 used for flux comparison)
- Companion: (cite: Colombo:2014ei) (M51 GMC catalog and CPROPS settings used for comparison)
- Companion: (cite: Hirota:2018jp) (GMC properties in barred galaxy M83)
- Companion: Fujimoto et al. 2019, submitted (hydrodynamical simulation of NGC 1300 with cloud-cloud collision speeds)
- Related: PHANGS
- Related: ALMA Cycle 7 ACA observations of NGC 1300 (PI: F. Maeda)

## Checks

```json
{
 "quotes": 164,
 "quotes_ok": 164,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 33,
 "numeric_problems": 0,
 "fill": {
  "facts": 114,
  "stated": 92,
  "rate": 0.807
 },
 "evidence_ok": true
}
```
