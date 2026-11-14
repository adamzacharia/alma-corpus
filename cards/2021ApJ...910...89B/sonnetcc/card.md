# The Physical Drivers of the Luminosity-weighted Dust Temperatures in High-redshift Galaxies

`2021ApJ...910...89B` | The Astrophysical Journal 2021 | first author: Burnham, Anne D. | arXiv: 2102.06250 | DOI: 10.3847/1538-4357/abe401

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Does luminosity-weighted dust temperature (lambda_peak) correlate more tightly with star-formation surface density / L_IR (SFR) than with sSFR or distance from the main sequence, using resolved 870 um sizes of seven COSMOS DSFGs plus eleven ALESS sources  
  > "to investigate the hypothesis that dust temperature maps directly to other observable characteristics such as galaxy size, morphology, star-formation surface density, and sSFR." (1 Introduction)
- Target **Seven COSMOS SCUBA-2 DSFGs (450.03, 850.04, 450.14, 850.60, 850.95, 850.25, 450.09)**: coordinates _not stated_; z/distance z = 1.4-4.6 (per-source z in Table 1)  
  > "Seven unlensed, spectroscopically-confirmed DSFGs were chosen from 400 arcmin$^2$ SCUBA-2 450 $\mu$m and 850 $\mu$m maps of the inner COSMOS field (cite: casey13a)." (3.1 Sample Selection); "updated information on this sample gives a total spanned redshift range of $1.4<z<4.6$." (3.1 Sample Selection); distance from spectroscopic redshifts from (cite: casey17a); 450.03 and 850.04 revised (see their entries)  
  > "Seven unlensed, spectroscopically-confirmed DSFGs were chosen from 400 arcmin$^2$ SCUBA-2 450 $\mu$m and 850 $\mu$m maps of the inner COSMOS field (cite: casey13a)." (3.1 Sample Selection); "updated information on this sample gives a total spanned redshift range of $1.4<z<4.6$." (3.1 Sample Selection)
- Target **450.03 (AzTEC2)**: coordinates _not stated_; z/distance z = 4.61 (Table 1 gives 4.629)  
  > "but is now confirmed to sit at $z=4.61$ from a serendipitous detection of \[CII\] in our ALMA data and concurrent confirmation via CO(5-4) line emission from NOEMA observations (cite: jimenez20)." (3.1 Sample Selection); distance from [CII] in the ALMA data plus NOEMA CO(5-4) (cite: jimenez20)  
  > "but is now confirmed to sit at $z=4.61$ from a serendipitous detection of \[CII\] in our ALMA data and concurrent confirmation via CO(5-4) line emission from NOEMA observations (cite: jimenez20)." (3.1 Sample Selection)
- Target **850.04**: coordinates _not stated_; z/distance z = 3.31 (+0.76/-0.81), photometric  
  > "The redshift for source 850.04 was originally estimated to be $z=1.436$, but closer inspection reveals a more likely redshift solution of $z=3.31^{+0.76}_{-0.81}$, which is a photometric redshift from the (cite: laigle16a) COSMOS catalog." (3.1 Sample Selection); distance from COSMOS catalog (cite: laigle16a)  
  > "The redshift for source 850.04 was originally estimated to be $z=1.436$, but closer inspection reveals a more likely redshift solution of $z=3.31^{+0.76}_{-0.81}$, which is a photometric redshift from the (cite: laigle16a) COSMOS catalog." (3.1 Sample Selection)
- Target **ALESS comparison sample (eleven sources: ALESS 3.1, 5.1, 9.1, 10.1, 15.1, 17.1, 29.1, 39.1, 45.1, 67.1, 112.1)**: coordinates _not stated_; z/distance z = 0.76-4.50 (Table 1)  
  > "We also include eleven ALESS sources in our analysis from (cite: hodge16a)" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00568.S
- bands: Band 7 (870 um, 345 GHz)  
  > "The observations targeted dust continuum emission at the nominal band 7 frequency centered at 345 GHz or 870 $\mu$m." (3.2 ALMA Data)
- frequencies and spectral setup: "single continuum" spectral mode; primary beam 17.3'' FWHM  
  > "At this frequency, ALMA has a 17.3$''$ primary beam (FWHM), and we utilized the “single continuum” spectral mode." (3.2 ALMA Data)
- continuum bandwidth: _not stated_
- arrays: 36 antennas  
  > "The compact and extended configurations had maximum baselines of 462.9 m  and 1.8 km, respectively, with 36 antennas." (3.2 ALMA Data)
- configurations: compact (C36-3) and extended (C36-6)  
  > "With a requested spatial resolution of 0.1$''$, observations were made in both compact (C36-3) and extended (C36-6) configurations." (3.2 ALMA Data)
- baselines: maximum baselines 462.9 m (compact) and 1.8 km (extended)  
  > "The compact and extended configurations had maximum baselines of 462.9 m  and 1.8 km, respectively, with 36 antennas." (3.2 ALMA Data)
- angular resolution: requested 0.1''; compact-only images 0.68'' x 0.49''; combined images 0.24'' x 0.27''  
  > "The resulting images have a resolution of 0.68$''$ $\times$ 0.49$''$." (3.2 ALMA Data); "The resulting resolution is 0.24$''$ $\times$ 0.27$''$." (3.2 ALMA Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Cycle 3 program 2015.1.00568.S (PI Casey)  
  > "Observations of these seven DSFGs were carried out as part of the ALMA Cycle 3 program 2015.1.00568.S (PI Casey)." (3.2 ALMA Data)
- Line: [CII] not stated (not stated)
- Other facility **Herschel SPIRE, SCUBA-2, Spitzer 24 um (SED photometry)**: Photometric points used together with ALMA 870 um in the SED fits  
  > "The photometric points used in the fitting include ALMA (870 $\mu$m), Herschel SPIRE (250, 350, 500 $\mu$m), SCUBA-2 (450, 850 $\mu$m), and Spitzer (24 $\mu$m)." (4.3 SED Integrated Dust Temperature)
- Other facility **NOEMA**: CO(5-4) confirmation of z = 4.61 for 450.03  
  > "concurrent confirmation via CO(5-4) line emission from NOEMA observations (cite: jimenez20)." (3.1 Sample Selection)
- Other facility **SCUBA-2 (JCMT) and LABOCA**: Single-dish 850 um (COSMOS) and 870 um (ALESS) flux densities used to check ALMA flux densities  
  > "we compare the flux densities as measured by ALMA to the single-dish flux densities obtained for the COSMOS sources from SCUBA-2 at 850 $\mu$m using the single-dish JCMT and for the ALESS sources from LABOCA at 870 $\mu$m." (4.1 ALMA 870 um Flux Densities)
- External data: ALESS 870 um flux densities and dust sizes (Gaussian FWHM) for the eleven ALESS sources  
  > "ALESS flux densities are from (cite: swinbank14a), and sizes are from (cite: hodge16a) derived in a fully consistent manner as for our COSMOS sample." (Table 1 caption) [from (cite: swinbank14a); (cite: hodge16a)]
- External data: Stellar masses: COSMOS sample from Casey et al., ALESS sources from da Cunha et al. (MAGPHYS)  
  > "The stellar masses of the COSMOS sample are presented in (cite: casey17a), and for the ALESS sources they are presented in (cite: dacunha15a)." (4.4 Star Formation Rates and Stellar Masses) [from (cite: casey17a); (cite: dacunha15a)]
- External data: Spectroscopic redshifts of the COSMOS sources  
  > "The DSFGs were selected at the time for having known spectroscopic redshifts between $z = 1-3$ (cite: casey17a)" (3.1 Sample Selection) [from (cite: casey17a)]
- External data: Cosmic time-dependent main-sequence fits for z = 1-5, used for D_MS  
  > "Also shown also are the cosmic time-dependent best fits from (cite: speagle14a) for redshifts $z =$ 1, 2, 3, 4, and 5." (4.4 Star Formation Rates and Stellar Masses) [from (cite: speagle14a)]
- External data: COSMOS data (1.5 <= z <= 2.5) used to fit a quadratic main sequence  
  > "applied to COSMOS data (1.5 $\leq$ z $\leq$ 2.5) from (cite: laigle16a)." (4.4 Star Formation Rates and Stellar Masses) [from (cite: laigle16a)]
- External data: Literature L_IR-lambda_peak power law (eta = -0.068 +/- 0.001, log lambda_0 = 2.012) used for comparison and to infer size-L_IR relation  
  > "they found $\eta$ = –0.068 $\pm$ 0.001 and $\log(\lambda_{0}/\mu\!m)=2.012$." (5.2.2 lambda_peak vs. L_IR or SFR) [from (cite: casey18b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "using the Common Astronomy Software Applications (CASA) version 4.5.3." (3.2 ALMA Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "we imaged the compact-configuration data using the CLEAN algorithm of CASA with Briggs weighting and robust = 2 (equivalent to natural weighting) and applied a primary beam correction." (3.2 ALMA Data)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 2 (natural) for compact-only images used for flux densities; robust = 1 for combined compact+extended images used for sizes  
  > "we imaged the compact-configuration data using the CLEAN algorithm of CASA with Briggs weighting and robust = 2 (equivalent to natural weighting)" (3.2 ALMA Data); "Thus, we adopt a robust value of 1 for the full sample as it maximizes the source signal-to-noise for the most extended source in the sample (850.95) while maintaining a relative high angular resolution." (3.2 ALMA Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "and applied a primary beam correction." (3.2 ALMA Data)
- array combination: raw compact and extended data combined, then reduced and calibrated the same way  
  > "We created a higher resolution set of maps by combining the raw data from the compact and extended configurations, then reducing and calibrating the data using the same method described above." (3.2 ALMA Data)
- smoothing: _not stated_
- final beam: compact 0.68'' x 0.49''; combined 0.24'' x 0.27''  
  > "The resulting images have a resolution of 0.68$''$ $\times$ 0.49$''$." (3.2 ALMA Data); "The resulting resolution is 0.24$''$ $\times$ 0.27$''$." (3.2 ALMA Data)
- final rms: _not stated_

### Inherited from earlier work

- Flux-density measurement method (mask, aperture summation)  
  > "Total integrated flux densities were measured directly from the compact ALMA data using a method similar to the one described in (cite: hodge16a)." (4.1 ALMA 870 um Flux Densities) [from (cite: hodge16a)]
- Gaussian size measurement of the ALESS sources, same technique as here  
  > "The Gaussian profiles of the ALESS sources included in our analysis were measured via the same technique used here (cite: hodge16a)" (4.2 Measuring Dust Sizes and Morphology) [from (cite: hodge16a)]
- SED fitting technique (single-temperature modified blackbody plus mid-IR power law)  
  > "SEDs in this work were fitted using the technique described in (cite: casey12a)" (4.3 SED Integrated Dust Temperature) [from (cite: casey12a)]
- Mid-IR power-law slope fixed to alpha_MIR = 2  
  > "representative of the average measured power law slope for local LIRGs and ULIRGs that have well-sampled mid-IR SEDs (cite: u12a)." (4.3 SED Integrated Dust Temperature) [from (cite: u12a)]
- Fixed opacity model with tau = 1 at 200 um  
  > "here we adopt a fixed opacity model for all SEDs such that $\tau$=1 at 200 $\mu$m following (cite: conley11a)." (4.3 SED Integrated Dust Temperature) [from (cite: conley11a)]
- SFR conversion log(C_IR) = 43.41  
  > "the logarithmic constant of conversion, $\rm \log(C_{IR}) = 43.41$ from (cite: kennicutt12)." (4.4 Star Formation Rates and Stellar Masses) [from (cite: kennicutt12)]
- Stellar masses derived with MAGPHYS using Bruzual & Charlot models, uniformly for both samples  
  > "All stellar masses used in this study are derived with MAGPHYS (cite: dacunha15a; dacunha08) in a uniform fashion using stellar population models from (cite: bruzual03)." (4.4 Star Formation Rates and Stellar Masses) [from (cite: dacunha15a; dacunha08; bruzual03)]
- Quadratic main-sequence functional form  
  > "a quadratic function of the form used in (cite: whitaker14a) applied to COSMOS data" (4.4 Star Formation Rates and Stellar Masses) [from (cite: whitaker14a)]

### Not stated but needed to reproduce (our reading)

- Whether the calibration used the ALMA pipeline or a manual script, calibrator names, and flux-scale uncertainty
- Whether any self-calibration was done on the continuum data, and the solution intervals
- Spectral windows and channels used for the continuum image, and how the serendipitous [CII] line in 450.03 was excluded
- CLEAN image size, cell size, threshold, number of iterations, masking, and the uv range of the combined data
- Per-source image rms noise and the beam of each source image
- The Herschel, SCUBA-2 and Spitzer photometric values and their sources, used as SED inputs for each COSMOS and ALESS source
- Wavelength range used to integrate L_IR, and how the SED-fit uncertainties on lambda_peak and L_IR were derived
- Method used to fit the linear relations and to compute the quoted correlation 'significance' in sigma (estimator, treatment of x and y errors)
- Parameters of the MCMC fit of the quadratic main sequence and exact formula for D_MS
- GALFIT and IMFIT setup: initial guesses, PSF or beam treatment, fit regions, and Sersic indices per source
- Source coordinates and phase centres

## Analysis recipe

1. **Calibrate and image the ALMA Band 7 data**: Compact-configuration data calibrated and imaged with CASA CLEAN (Briggs robust 2, primary beam corrected); compact + extended data combined and imaged with robust 1 for the size measurements  
  > "we imaged the compact-configuration data using the CLEAN algorithm of CASA with Briggs weighting and robust = 2 (equivalent to natural weighting) and applied a primary beam correction." (3.2 ALMA Data); "We created a higher resolution set of maps by combining the raw data from the compact and extended configurations, then reducing and calibrating the data using the same method described above." (3.2 ALMA Data)
   - software: CASA 4.5.3, CLEAN
   - parameter: robust = 1 adopted for the combined data; sizes found independent of robust  
  > "We tested different robust values with the CLEAN algorithm and found the resulting size of each source to be consistent and independent of the robust parameter." (3.2 ALMA Data)
   - parameter: antennas with irregular amplitudes flagged  
  > "During calibration, data from antennas with irregular amplitudes were flagged." (3.2 ALMA Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure total 870 um flux densities**: Aperture summation on compact-data images: convert Jy/beam to mJy/pixel, mask emission below 2 sigma, sum contiguous emission within a radius of 3 x b_maj  
  > "We converted the maps from Jy beam$^{-1}$ to mJy pixel$^{-1}$ and masked emission less than 2$\sigma$." (4.1 ALMA 870 um Flux Densities); "We then summed contiguous emission within an aperture of radius 3 $\times$ $b_{\rm maj}$, where $b_{\rm maj}$ is the FWHM (major axis) of the synthesized beam." (4.1 ALMA 870 um Flux Densities)
   - software: CASA IMFIT (cross-check)
   - parameter: aperture radius 3 x b_maj; mask below 2 sigma  
  > "We then summed contiguous emission within an aperture of radius 3 $\times$ $b_{\rm maj}$, where $b_{\rm maj}$ is the FWHM (major axis) of the synthesized beam." (4.1 ALMA 870 um Flux Densities)
   - assumption: Both components of 450.03 (separated by 3'' at the same redshift) included in the total  
  > "Source 450.03 is composed of two sources separated by 3$''$  at the same redshift (cite: jimenez20), both of which were included in the total reported flux density." (4.1 ALMA 870 um Flux Densities)
   - fitting: _not stated_
   - validation: Compared with IMFIT flux densities (ratio 0.96 +/- 0.10) and with single-dish SCUBA-2/LABOCA flux densities (ratio 0.94 +/- 0.21)  
  > "The average ratio between IMFIT and aperture flux density measurements was $0.96\pm0.10$." (4.1 ALMA 870 um Flux Densities); "The average ratio of ALMA to single-dish flux densities was $0.94\pm0.21$" (4.1 ALMA 870 um Flux Densities)
3. **Measure dust sizes and morphology**: Image-plane 2D Gaussian fits (CASA IMFIT) and Sersic fits (GALFIT) on the combined-data maps; IMFIT FWHM/2 adopted as half-light radius R_e in the analysis; uv-plane UVMODELFIT Gaussian fits as a check  
  > "The Sersic model was applied using GALFIT, and the Gaussian model was applied using CASA IMFIT." (4.2 Measuring Dust Sizes and Morphology); "are equivalent to these FWHM measurements divided by two." (4.2 Measuring Dust Sizes and Morphology)
   - software: GALFIT, CASA IMFIT, CASA UVMODELFIT
   - parameter: IMFIT results used in the analysis because GALFIT errors are underestimated  
  > "It is a known problem that errors from GALFIT are underestimated; therefore, we used the IMFIT results in our analysis" (4.2 Measuring Dust Sizes and Morphology)
   - assumption: Sizes trace mass-weighted dust on the Rayleigh-Jeans tail, not luminosity-weighted sizes; five of 18 sources at z > 3 may probe optically thick regime  
  > "The sizes measured here are the mass-weighted sizes–measured on the Rayleigh-Jeans tail of the SED–rather than the luminosity-weighted sizes" (4.2 Measuring Dust Sizes and Morphology)
   - fitting: _not stated_
   - validation: UVMODELFIT and IMFIT agree within uncertainties for four sources; discrepancies for 450.03, 850.25 and 850.95 explained; median uv/image FWHM ratio 0.81 +/- 0.08  
  > "The UVMODELFIT and IMFIT measurements agree within uncertainties for four of our sources." (4.2 Measuring Dust Sizes and Morphology); "FWHMs is 0.81 $\pm$ 0.08." (4.2 Measuring Dust Sizes and Morphology)
4. **Fit SEDs for lambda_peak and L_IR**: Single-temperature modified blackbody plus mid-IR power law (alpha_MIR = 2 fixed), fitted to ALMA, SPIRE, SCUBA-2 and 24 um photometry; same procedure for the ALESS sources  
  > "SEDs in this work were fitted using the technique described in (cite: casey12a), based on a single dust temperature modified blackbody fit with a mid-infrared power law shortward of $\sim$ 70 $\mu$m in the rest frame." (4.3 SED Integrated Dust Temperature); "Fitting SEDs for both the COSMOS SCUBA-2 DSFGs and the ALESS sources was done in a fully consistent manner." (4.3 SED Integrated Dust Temperature)
   - parameter: alpha_MIR = 2 fixed  
  > "we fix the mid-infrared power law slope to $\alpha_{\rm MIR}=2$" (4.3 SED Integrated Dust Temperature)
   - parameter: points weighted by signal-to-noise (24 um S/N capped at 10)  
  > "Points are weighted relative to their signal-to-noise, with exception of the" (4.3 SED Integrated Dust Temperature)
   - assumption: Optically thick SED with tau = 1 at 200 um for all sources  
  > "here we adopt a fixed opacity model for all SEDs such that $\tau$=1 at 200 $\mu$m following (cite: conley11a)." (4.3 SED Integrated Dust Temperature)
   - fitting: _not stated_
   - validation: Opacity check from 870 um flux, sizes, a fixed 25 K mass-weighted temperature and Li & Draine opacities: lambda(tau=1) from 10-300 um, average 80 +/- 50 um; uniform assumption kept  
  > "we infer that the wavelength at which the SEDs become optically thick to vary from 10–300 $\mu$m (with an average $\lambda(\tau=1)=80\pm50$ $\mu$m)." (4.3 SED Integrated Dust Temperature)
5. **Derive SFR, stellar mass, sSFR and distance to the main sequence**: SFR from L_IR with log(C_IR) = 43.41; M_star from MAGPHYS; sSFR = SFR/M_star; D_MS as orthogonal distance in the log M_star-log SFR plane to the Speagle et al. main sequence at each source's redshift  
  > "Star formation rates (SFRs) were calculated using the total infrared luminosities derived from the SED fits in section" (4.4 Star Formation Rates and Stellar Masses); "We also calculated the specific star formation rate (sSFR), where sSFR = SFR/ M$_\star$." (4.4 Star Formation Rates and Stellar Masses); "D$_{\rm MS}$ represents the orthogonal distance between the main sequence at the source’s redshift and its measured value in the $\log$ M$_\star$–$\log$SFR plane." (4.4 Star Formation Rates and Stellar Masses)
   - software: MAGPHYS
   - assumption: Kroupa IMF, Kennicutt & Evans scaling relations  
  > "Where SFRs are used, we assume a Kroupa IMF (cite: kroupa03a) and scaling relations drawn from (cite: kennicutt12)." (1 Introduction)
   - assumption: H0 = 70 km/s/Mpc, Omega_M = 0.3, Omega_Lambda = 0.7  
  > "We assume a concordance cosmology throughout this paper, adopting $H_{0}=70\,$km s$^{-1}$ Mpc, $\Omega_{M}=0.3$, and $\Omega_{\Lambda}=0.7$." (1 Introduction)
   - fitting: MCMC used to fit a quadratic main sequence to the COSMOS data (priors, likelihood not stated)  
  > "We applied a Markov Chain Monte Carlo (MCMC) approach to derive the parameters of the fit for the broader COSMOS data set." (4.4 Star Formation Rates and Stellar Masses)
   - validation: D_MS computed also with the quadratic Whitaker form; conclusions unchanged  
  > "we note that computing D$_{\rm MS}$ using a quadratic form of the main sequence as in (cite: whitaker14a) produces similar results" (4.4 Star Formation Rates and Stellar Masses)
6. **Test correlations of lambda_peak with Sigma_IR, L_IR (SFR), sSFR and D_MS and compare with Stefan-Boltzmann expectation**: Linear fits in log-log space of each quantity against lambda_peak; significance quoted as deviation of the model from no correlation (horizontal line); measured Sigma_IR-lambda_peak relation compared with the Stefan-Boltzmann disk-screen and Wien-law expectations  
  > "We calculate the significance of each correlation as the deviation of the model from no correlation, or a horizontal line in the given parameter space." (5.2 What correlates best with dust temperature?)
   - parameter: Sigma_IR = L_IR / (pi R_e^2) with R_e the half-light radius  
  > "Where $\Sigma_{\rm IR}$ is the IR luminosity surface density, =$L_{\rm IR}/\pi R_{e}^2$." (5.1 Expected Relationship)
   - assumption: Disk-like geometry: uniform planar UV emission under an optically thick screen, giving log Sigma_IR = log(sigma) + 4 log(T_dust)  
  > "If instead of a spherical shell we assume some uniform planar distribution of UV emission underneath an optically thick screen (as in a galaxy disk, with half-light radius $R_{e}$) we would expect the following relationship instead:" (5.1 Expected Relationship)
   - fitting: _not stated_
   - validation: Repeated for a reduced sample 1.44 <= z <= 2.86; also with circularized or Sersic radii and without 450.03 and 450.14  
  > "we recalculated the correlations based on a reduced sample with $1.44 \leqslant z \leqslant 2.86$, removing the high-$z$ and low-$z$ extrema from the sample." (5.2 What correlates best with dust temperature?); "is unaffected by calculating $\Sigma_{\rm IR}$ with circularized radii or effective radii from Sersic fitting rather than FWHMs from Gaussian fitting." (5.2.1 lambda_peak vs. Sigma_IR)

## Software

- **CASA** 4.5.3: Calibration and imaging (CLEAN) of the ALMA data  
  > "using the Common Astronomy Software Applications (CASA) version 4.5.3." (3.2 ALMA Data)
- **CASA IMFIT** : Image-plane 2D Gaussian size fits (adopted sizes) and flux-density cross-check  
  > "The Sersic model was applied using GALFIT, and the Gaussian model was applied using CASA IMFIT." (4.2 Measuring Dust Sizes and Morphology)
- **CASA UVMODELFIT** : uv-plane Gaussian size check  
  > "The UVMODELFIT and IMFIT measurements agree within uncertainties for four of our sources." (4.2 Measuring Dust Sizes and Morphology)
- **GALFIT** : Sersic profile fits to the ALMA maps (Sersic index and effective radius)  
  > "Dust emission half-light effective radii (R$_{\rm e}$) were measured using GALFIT on the ALMA maps in the image plane." (4.2 Measuring Dust Sizes and Morphology)
- **MAGPHYS** : Stellar masses (and reruns for the two sources with corrected redshifts)  
  > "For the two sources for which the redshifts were corrected, we reran the MAGPHYS modeling accordingly." (4.4 Star Formation Rates and Stellar Masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median 870 um flux density of the seven COSMOS sources | 5.8 | 3.7 | mJy | 2 | The median flux density of our seven sources is 5.8 $\pm$ 3.7 mJy at 870$\mu$m. |
| Average ratio IMFIT to aperture flux density | 0.96 | 0.10 | dimensionless | 2 | The average ratio between IMFIT and aperture flux density measurements was $0.96\pm0.10$. |
| Average ratio ALMA to single-dish flux density | 0.94 | 0.21 | dimensionless | 2 | The average ratio of ALMA to single-dish flux densities was $0.94\pm0.21$ |
| S_870, 450.03 | 19.12 | 0.16 | mJy | 2 | 19.12$\pm$0.16 |
| S_870, 850.04 | 13.67 | 0.12 | mJy | 2 | 13.67$\pm$0.12 |
| S_870, 450.14 | 2.05 | 0.03 | mJy | 2 | 2.05$\pm$0.03 |
| S_870, 850.60 | 2.21 | 0.04 | mJy | 2 | 2.21$\pm$0.04 |
| S_870, 850.95 | 1.21 | 0.03 | mJy | 2 | 1.21$\pm$0.03 |
| S_870, 850.25 | 5.76 | 0.05 | mJy | 2 | 5.76$\pm$0.05 |
| S_870, 450.09 | 6.07 | 0.07 | mJy | 2 | 6.07$\pm$0.07 |
| R_e (IMFIT half-light radius), 450.03 (total circularized, both components) | 1.35 | 0.06 | kpc | 3 | 1.35$^{b}$$\pm$0.06 |
| R_e (IMFIT), 850.04 | 1.94 | 0.12 | kpc | 3 | 1.94$\pm$0.12 |
| R_e (IMFIT), 450.14 | 2.8 | 0.4 | kpc | 3 | 2.8$\pm$0.4 |
| R_e (IMFIT), 850.60 | 1.81 | 0.28 | kpc | 3 | 1.81$\pm$0.28 |
| R_e (IMFIT), 850.95 | 6.1 | 1.4 | kpc | 3 | 6.1$\pm$1.4 |
| R_e (IMFIT), 850.25 | 2.76 | 0.22 | kpc | 3 | 2.76$\pm$0.22 |
| R_e (IMFIT), 450.09 | 1.04 | 0.07 | kpc | 3 | 1.04$\pm$0.07 |
| Median GALFIT effective radius | 0.32 | 0.09 | arcsec | 3 | The effective radii measured by GALFIT range from 0.13$''$$-$0.69$''$ with a median of R$_{\rm e}$$=$ 0.32$''$ $\pm$ 0.09$''$. |
| Median GALFIT effective radius, physical | 2.7 | 0.8 | kpc | 3 | (median R$_{\rm e}$$= 2.7 \pm$ $0.8$ kpc) |
| Median Gaussian FWHM (IMFIT), full sample | 3.9 | 1.6 | kpc | 3 | The median Gaussian profile has a FWHM $= 3.9 \pm 1.6$ kpc. |
| Median Sersic index | 0.8 | 0.4 | dimensionless | 3 | The Sersic indices of our sources range from $n=$0.3 to 2.1, with a median of $n = 0.8 \pm 0.4$. |
| Median ratio of uv-plane to image-plane Gaussian FWHM | 0.81 | 0.08 | dimensionless | 3 | FWHMs is 0.81 $\pm$ 0.08. |
| lambda_peak, 450.03 | 71.4 | 7.8 | um | 4 | 71.4$\pm$7.8 |
| lambda_peak, 850.04 | 98 | 9 | um | 4 | 98$\pm$9 |
| lambda_peak, 450.14 | 130 | 30 | um | 4 | 130$\pm$30 |
| lambda_peak, 850.60 | 75 | 9 | um | 4 | 75$\pm$9 |
| lambda_peak, 850.95 | 98 | 22 | um | 4 | 98$\pm$22 |
| lambda_peak, 850.25 | 117 | 20 | um | 4 | 117$\pm$20 |
| lambda_peak, 450.09 | 71 | 10 | um | 4 | 71$\pm$10 |
| Average wavelength where SEDs become optically thick, lambda(tau=1) | 80 | 50 | um | 4 | (with an average $\lambda(\tau=1)=80\pm50$ $\mu$m). |
| log Sigma_IR vs log lambda_peak: intercept | 18.78 | 0.33 | dimensionless (log of L_sun kpc^-2 at log lambda_peak = 0) | 6 | (18.78\pm0.33) |
| log Sigma_IR vs log lambda_peak: slope | -3.80 | 0.16 | dimensionless | 6 | (3.80\pm0.16)\log(\lambda_{\rm peak}/\mu\!m) |
| Correlation significance lambda_peak vs Sigma_IR | 24 | not stated | sigma | 6 | The overall strength of the correlation is 24$\sigma$. |
| Deviation of measured slope from disk Stefan-Boltzmann expectation | 2.4 | not stated | sigma | 6 | The slope of this relation is a 2.4$\sigma$ deviation from expectation in Equation |
| log L_IR vs log lambda_peak: intercept | 18.2 | 0.3 | dimensionless (log L_sun at log lambda_peak = 0) | 6 | \log(L_{\rm IR}/L_\odot) = (18.2\pm0.3) - (2.81\pm0.16)\log(\lambda_{\rm peak}/\mu\!m) |
| log L_IR vs log lambda_peak: slope | -2.81 | 0.16 | dimensionless | 6 | \log(L_{\rm IR}/L_\odot) = (18.2\pm0.3) - (2.81\pm0.16)\log(\lambda_{\rm peak}/\mu\!m) |
| Correlation significance lambda_peak vs L_IR | 18 | not stated | sigma | 6 | This correlation carries an overal significance of 18$\sigma$. |
| Size-luminosity scaling R_e proportional to L_IR^x, exponent x | 0.37 | 0.03 | dimensionless | 6 | R$_{\rm e}$ $\propto$ L$_{\rm IR}$$^{0.37\pm0.03}$. |
| log sSFR vs log lambda_peak: intercept | 3.4 | 0.4 | dimensionless (log Gyr^-1 at log lambda_peak = 0) | 6 | (3.4\pm0.4) |
| log sSFR vs log lambda_peak: slope | -1.43 | 0.20 | dimensionless | 6 | (1.43\pm0.20)\log(\lambda_{\rm peak}/\mu\!m) |
| log D_MS vs log lambda_peak: intercept and slope | 1.5 and -0.54 | 0.4 and 0.21 | dimensionless | 6 | \log(D_{\rm MS}) = (1.5\pm0.4) - (0.54\pm0.21)\log(\lambda_{\rm peak}/\mu\!m) |
| Correlation significances: lambda_peak vs D_MS and vs sSFR | 3 and 7 | not stated | sigma | 6 | We find that the  $\lambda_{\rm peak}$ vs. D$_{\rm MS}$ and  $\lambda_{\rm peak}$ vs. sSFR relationships correlate with 3$\sigma$ and 7$\sigma$ significance, respectively. |
| Correlation significances: lambda_peak vs SFR and vs Sigma_IR | 18 and 24 | not stated | sigma | 6 | In contrast, the  $\lambda_{\rm peak}$ vs. SFR and  $\lambda_{\rm peak}$ vs. $\Sigma_{\rm IR}$ relationships carry an 18$\sigma$ and 24$\sigma$ correlation significance, respectively. |
| Correlation significances in the reduced-redshift sample (1.44 <= z <= 2.86): Sigma_IR and SFR | 16 and 18 | not stated | sigma | 6 | the significance of the  $\lambda_{\rm peak}$–$\Sigma_{\rm IR}$ and  $\lambda_{\rm peak}$–SFR correlations are reduced somewhat to 16$\sigma$ and 18$\sigma$ significance, respectively |

## Qualitative findings

- Sizes at 870 um are mostly moderately resolved; the median Sersic index implies a non-Gaussian, exponential-disk morphology consistent with the ALESS sources  
  > "Most of our sources are moderately resolved—more than two beams across in size—so size measurements are unlikely to be affected by fitting methods." (4.2 Measuring Dust Sizes and Morphology); "implies a non-Gaussian, exponential disk morphology." (6 Conclusions)
- Dust temperature (lambda_peak) is not a reliable indicator of position on the main sequence or evolutionary class; dust geometry is more important  
  > "we infer that dust temperature is not necessarily a reliable indication of where a galaxy sits on the main sequence and should not be used to infer evolutionary class" (6 Conclusions)
- The measured Sigma_IR-lambda_peak relation matches Stefan-Boltzmann-like scaling, Sigma_IR proportional to lambda_peak^-4  
  > "We conclude that galaxies’ dust emission properties can be well described by a Stefan-Boltzmann like law" (6 Conclusions)

## Claim tuples

- H: lambda_peak correlates more tightly with Sigma_IR and L_IR (SFR) than with sSFR or distance to the main sequence | E: Fit log-log linear relations of lambda_peak against Sigma_IR, L_IR, sSFR and D_MS for 7 COSMOS plus 11 ALESS DSFGs and compare correlation significances | R: 24 sigma (Sigma_IR), 18 sigma (SFR), 7 sigma (sSFR), 3 sigma (D_MS); the ordering holds in the reduced-redshift sample | F: Star-formation surface density is the more fundamental driver of luminosity-weighted dust temperature | **supported**
- H: The Sigma_IR-lambda_peak relation follows a galaxy-scale Stefan-Boltzmann law | E: Compare the measured relation with disk-screen and Wien-law expectations | R: Slope deviates 2.4 sigma and intercept 4.3 sigma from the disk-screen expectation; 1.3 sigma and 0.7 sigma from the direct Wien expectation | F: Dust emission is approximately a Stefan-Boltzmann-like law with Sigma_IR proportional to lambda_peak^-4, implying optically thick emission near the SED peak | **partially**
- H: Dust temperature traces position on the galaxy main sequence (sSFR or D_MS), as claimed in the literature | E: Correlate lambda_peak with sSFR, D_MS and Delta log sSFR_MS, and with stellar mass | R: Weak correlations (3-7 sigma, 1-4 sigma for alternate D_MS definitions); no significant correlation with stellar mass | F: No clear evidence that dust temperature correlates strongly with main-sequence position | **supported**
- H: Resolved 870 um dust emission in these DSFGs has non-Gaussian, exponential-disk morphology and typical sizes similar to ALESS sources | E: GALFIT Sersic and IMFIT Gaussian fits to the 0.24'' maps | R: Median Sersic n = 0.8 +/- 0.4; median Gaussian FWHM 3.9 +/- 1.6 kpc | F: Median size agrees with ALESS sources despite the ALESS sources being brighter | **supported**
- H: The L_IR-lambda_peak relation of this sample matches that of much larger literature samples | E: Fit log L_IR against log lambda_peak and compare with the Casey et al. power law | R: Slope -2.81 +/- 0.16, steeper than the literature relation | F: Steepness attributed to selection of sources suited to high-resolution follow-up, so larger samples are better calibrated | **partially**

## Reasoning

- Why this data: High-SFR sources are the only ones for which high-resolution dust size measurements are feasible with a reasonable ALMA time investment; the sample spans a wide range of dust SEDs  
  > "sources with high SFRs are the only ones for which the high spatial resolution measurements made in this paper are possible with a reasonable investment in ALMA time." (3.3 Biases in the Sample?)
- Why this method: Image-plane size measurements justified because most sources are more than two beams across; robust = 1 chosen to maximise S/N of the most extended source while keeping resolution  
  > "Thus, making measurements in the image plane rather than the" (4.2 Measuring Dust Sizes and Morphology); "Thus, we adopt a robust value of 1 for the full sample as it maximizes the source signal-to-noise for the most extended source in the sample (850.95) while maintaining a relative high angular resolution." (3.2 ALMA Data)
- Alternative: Different CLEAN robust values tested; sizes independent of robust  
  > "We tested different robust values with the CLEAN algorithm and found the resulting size of each source to be consistent and independent of the robust parameter." (3.2 ALMA Data)
- Alternative: GALFIT sizes not used in the analysis (errors underestimated); IMFIT sizes adopted  
  > "It is a known problem that errors from GALFIT are underestimated; therefore, we used the IMFIT results in our analysis" (4.2 Measuring Dust Sizes and Morphology)
- Alternative: Quadratic Whitaker-form main sequence tested instead of Speagle et al. curves; conclusions unchanged  
  > "we note that computing D$_{\rm MS}$ using a quadratic form of the main sequence as in (cite: whitaker14a) produces similar results" (4.4 Star Formation Rates and Stellar Masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Requested 0.12'' resolution not reached, even with robust = 0  
  > "This does not meet the requested 0.12$''$ resolution, but even with a robust value of 0, the spatial resolution is still not as good as requested." (3.2 ALMA Data)
- Limitation (authors): Sizes are mass-weighted on the Rayleigh-Jeans tail, not luminosity-weighted sizes at the SED peak  
  > "The sizes measured here are the mass-weighted sizes–measured on the Rayleigh-Jeans tail of the SED–rather than the luminosity-weighted sizes" (4.2 Measuring Dust Sizes and Morphology)
- Limitation (authors): Sample may be biased toward high-SFR galaxies, limiting dynamic range in L_IR  
  > "The sample (both COSMOS and ALESS DSFGs) could be seen as biased toward galaxies with high SFRs" (3.3 Biases in the Sample?)
- Limitation (authors): Stellar masses of DSFGs are highly uncertain  
  > "Note that the stellar masses of DSFGs are often highly uncertain, though not necessarily systematically so" (4.4 Star Formation Rates and Stellar Masses)
- Caveat (inferred, ours): Only 18 sources (7 new), selected for a wide lambda_peak range; correlation 'sigma' values depend on an undescribed fit and significance estimator
- Caveat (inferred, ours): Sigma_IR and lambda_peak both come from the same SED fit and share L_IR, so errors are correlated and part of the correlation may be built in
- Caveat (inferred, ours): Sizes are mass-weighted RJ-tail sizes (and optically thick for z > 3 sources) used as proxy for the SFR-weighted size
- Caveat (inferred, ours): Fixed tau = 1 at 200 um and fixed mid-IR slope drive lambda_peak and L_IR; the paper's own opacity check shows lambda(tau=1) varies 10-300 um
- Caveat (inferred, ours): Mixed ALMA datasets (new data and ALESS data from another program) with different depths and different uv coverage; compact-only vs combined imaging differences not quantified

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration recipe, flux calibrator and flux-scale uncertainty
- Missing: Full CLEAN parameters (image size, cell size, threshold, masks, spws)
- Missing: SED input photometry and fit uncertainties for every source
- Missing: Regression and significance method for the quoted relations
- Missing: Stellar masses and ALESS measurements must be taken from other papers
- Data volume (inferred): Two Band 7 configurations (C36-3 and C36-6) of continuum data for 7 targets, probably tens of GB of raw data (inferred guess)
- Score (inferred): 3/5, One public-style ALMA project code, imaging choices partly stated (robust, software version, aperture method), and a numeric table of fluxes and sizes; but calibration, SED photometry and regression details are missing, and ALESS and stellar-mass inputs come from other papers.
- Rediscovery candidate: no, The paper does not state that the data are public, and the SED photometry and fit/significance procedures needed for the main correlation results are not given in enough detail to redo them.

## Links

- Method: (cite: casey12a) (SED fitting technique used for lambda_peak and L_IR)
- Method: (cite: hodge16a) (Flux-density method and ALESS sizes measured the same way)
- Method: (cite: peng10a) (GALFIT)
- Method: (cite: dacunha15a) (MAGPHYS stellar masses)
- Companion: (cite: casey17a) (COSMOS SCUBA-2 sample, spectroscopic redshifts and COSMOS stellar masses)
- Companion: (cite: jimenez20) (z = 4.61 confirmation and two-component nature of 450.03)
- Companion: (cite: casey18b) (L_IR-lambda_peak relation used for comparison)
- Related: ALESS (ALMA LESS) survey
- Related: SCUBA-2 COSMOS survey
- Related: COSMOS field

## Checks

```json
{
 "quotes": 151,
 "quotes_ok": 151,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 44,
 "numeric_problems": 0,
 "fill": {
  "facts": 115,
  "stated": 80,
  "rate": 0.696
 },
 "evidence_ok": true
}
```
