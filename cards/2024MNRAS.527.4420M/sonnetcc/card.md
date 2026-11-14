# The Quasar Feedback Survey: characterizing CO excitation in quasar host galaxies

`2024MNRAS.527.4420M` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Molyneux, S. J. | arXiv: 2310.10235 | DOI: 10.1093/mnras/stad3133

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Do AGN feedback (ionised outflows, radio jets) in 17 Type 2 quasars at z<0.2 impact the global molecular gas content and CO excitation (low-J and J_up=6,7 SLEDs)?  
  > "we are able to investigate the impact of AGN and AGN feedback mechanisms on the global molecular interstellar medium" (abstract); "With the addition of ancillary multi-wavelength data, we will explore the impact of feedback, if any, on the total molecular gas content and molecular gas excitation within the quasar host galaxies." (1 Introduction)
- Target **17 Type 2 quasars of the Quasar Feedback Survey (QFeedS)**: coordinates per-target J2000 RA/Dec listed in the sample table (not quoted here)  
  > "17 Type 2 quasars at $z <$ 0.2" (abstract); "The 17 targets were selected to be Type 2 quasars which are visible from the Very Large Telescope (VLT) and the Atacama Pathfinder EXperiment telescope (APEX)" (2 Sample selection); "We adopt $H_0=70$ km $\rm s^{-1}$  Mpc$^{-1}$, $\Omega_M=0.3$, and $\Omega_\Lambda=0.7$ throughout." (1 Introduction); z/distance z ~ 0.1-0.2 (SDSS redshifts, median z = 0.14)  
  > "17 Type 2 quasars at $z <$ 0.2" (abstract); "The 17 targets were selected to be Type 2 quasars which are visible from the Very Large Telescope (VLT) and the Atacama Pathfinder EXperiment telescope (APEX)" (2 Sample selection); "We adopt $H_0=70$ km $\rm s^{-1}$  Mpc$^{-1}$, $\Omega_M=0.3$, and $\Omega_\Lambda=0.7$ throughout." (1 Introduction); distance from SDSS redshifts; luminosity distance for H0=70, Omega_M=0.3, Omega_Lambda=0.7  
  > "17 Type 2 quasars at $z <$ 0.2" (abstract); "The 17 targets were selected to be Type 2 quasars which are visible from the Very Large Telescope (VLT) and the Atacama Pathfinder EXperiment telescope (APEX)" (2 Sample selection); "We adopt $H_0=70$ km $\rm s^{-1}$  Mpc$^{-1}$, $\Omega_M=0.3$, and $\Omega_\Lambda=0.7$ throughout." (1 Introduction)

## Data provenance

- ALMA projects: 2019.2.00194.S, 2016.1.01535.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA (Atacama Compact Array), twelve 7 m antennae  
  > "the ACA is a subset of the Atacama Large Millimeter/submillimeter Array (ALMA) comprising of twelve 7 metre antennae" (3 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ACA CO(1-0) beam 12-14 arcsec; ACA CO(3-2) for J1430+1339 beam 4.3 arcsec  
  > "The beam size of the ACA observations ranged between 12 – 14 arcsec." (3.1 CO(1-0) observations); "here a beam size of 4.3 arcsec and a maximal recoverable scale of 23 arcsec" (3.3 CO(3-2) Observations)
- max recoverable scale: 23 arcsec (ACA CO(3-2), J1430+1339); median recoverable scale of the ACA CO(1-0) observations 188 kpc  
  > "a maximal recoverable scale of 23 arcsec" (3.3 CO(3-2) Observations); "scales greater than 188kpc (median recoverable scale of the observations)" (5.1.2 Optical depth effects)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ACA CO(1-0): December 2019 - March 2020; ACA CO(3-2) (J1430+1339): 03 November 2016  
  > "acquired between December 2019 and March 2020" (3.1 CO(1-0) observations); "taken on 03 November 2016" (3.3 CO(3-2) Observations)
- pi or archival as stated: CO(1-0): PI Calistro-Rivera (2019.2.00194.S), 13 of 17 targets; CO(3-2) for J1430+1339: archival, PI Lansbury (2016.1.01535.S)  
  > "Thirteen out of our 17 targets have CO(1-0) ACA observations" (3.1 CO(1-0) observations); "we utilise archival CO(3-2) ACA observations" (3.3 CO(3-2) Observations)
- Line: CO J=1-0, 2-1, 3-2, 6-5, 7-6 (not stated)
- Other facility **APEX (SEPIA180, SEPIA345, SEPIA660)**: CO(2-1), CO(3-2), CO(6-5)/CO(7-6) single-dish spectra  
  > "observed with SEPIA180 on APEX between 09 December 2020 and 21 June 2021" (3.2 CO(2-1) Observations); "We observed 7 targets in either CO(6-5) or CO(7-6) using SEPIA660 on APEX" (3.4 CO(6-5) and CO(7-6) Observations)
- Other facility **VLT/MUSE**: [O III] (or Hbeta) spectra in 30 arcsec and 3 arcsec apertures for ionised-gas line profiles  
  > "We have also obtained MUSE VLT observations for these 17 quasars" (3.5 Ancillary Multiwavelength Data)
- Other facility **VLA**: 1-6 GHz radio data at 0.3-1 arcsec resolution (1.4 GHz luminosities, jets)  
  > "VLA radio data are available for all 17 quasars in the sample at 1–6 GHz and at a resolution of 0.3 – 1 arcsec" (3.5 Ancillary Multiwavelength Data)
- Other facility **SDSS**: redshifts used to define v = 0 and [O III] W80 line widths  
  > "Central frequencies (where $v$ = 0 km $\rm s^{-1}$ ) have been defined using the SDSS redshifts" (4.2 Spectral properties)
- External data: Comparison sample of non-AGN and AGN gas fractions (xCOLD GASS, EGNOG, GOALS, Combes+11 compilation)  
  > "We first utilise non-AGN and AGN from (cite: Tacconi18) to put the gas fractions of our sources in context" (4.1 Comparison samples) [from (cite: Tacconi18)]
- External data: Stellar masses from SED fitting  
  > "is the stellar mass obtained from SED fitting (cite: Jarvis20)" (4.3 Molecular gas masses) [from (cite: Jarvis20)]
- External data: High-z quasar and CO SLED compilations; thermalised and Milky Way reference SLEDs  
  > "From (cite: Carilli13) we utilise the compilation of high-$z$ quasars" (4.1 Comparison samples) [from (cite: Carilli13)]
- External data: z~1-2 starburst and main-sequence galaxy CO SLEDs  
  > "In our CO SLEDs (Section [\[sec:COSLEDs\]](#sec:COSLEDs)) we utilise the compilations by (cite: Valentino21) and (cite: Carilli13) to compare to our CO SLEDs." (4.1 Comparison samples) [from (cite: Valentino21)]
- External data: Line ratios of 40 local (U)LIRGs  
  > "analysed a sample 40 local (U)LIRGs" (4.1 Comparison samples) [from (cite: Montoya23)]
- External data: Line ratios of local star-forming galaxies compilation (r21 median 0.65) and models for temperature/density/optical depth  
  > "we also used a compilation of local star forming galaxies as a comparison (cite: Leroy22)" (4.1 Comparison samples) [from (cite: Leroy22)]
- External data: BASS hard X-ray selected AGN line ratios  
  > "we utilise the sample by (cite: Lamperti20)" (4.1 Comparison samples) [from (cite: Lamperti20)]
- External data: Local (U)LIRG line ratios at z <= 0.1  
  > "a sample of (U)LIRGs at $z$ $\leq$ 0.1 from (cite: Greve14)" (4.1 Comparison samples) [from (cite: Greve14)]
- External data: ALMA 0.2 arcsec CO(2-1) data and spectra for J1010+0612, J1100+0846, J1356+1026, J1430+1339  
  > "ALMA observations of the CO(2-1) at 0.2 arcsec resolution presented by (cite: Almeida21) are available" (4.2 Spectral properties) [from (cite: Almeida21)]
- External data: Archival APEX CO(2-1) observations of 9 targets, re-analysed from raw data  
  > "The remaining 9 targets had equivalent APEX archival CO(2-1) observations presented as a pilot sample by (cite: Jarvis20)" (3.2 CO(2-1) Observations) [from (cite: Jarvis20)]
- External data: L_bol/L_[OIII] = 3500 bolometric correction  
  > "we convert our \[O III\] luminosities to bolometric luminosities via the following equation: $\rm L_{bol}/L_{\rm [O~{\sc III}]}$ = 3500 (cite: Heckman04)" (4.4.2 Line ratios) [from (cite: Heckman04)]
- External data: L_IR,SF values indicating LIRG-like luminosities  
  > "From previous work (cite: Jarvis19), we also know that at least 8 of these 17 sample galaxies are consistent with being luminous infrared galaxies" (2 Sample selection) [from (cite: Jarvis19)]
- Simulation/model as data: Dense Gas Toolbox models and Leroy+22 simulated r32-r21 parameter space of temperature, density, optical depth  
  > "We present these data plotted over simulations of the expected parameter space covered for these line ratios based on variable temperature, densities and optical depths (cite: Leroy22)." (4.5 Gas temperature and density)

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

- task: tclean in CASA  
  > "We image the CO(1-0) emission using the TCLEAN function in CASA" (3.1 CO(1-0) observations)
- deconvolver: Hogbom  
  > "apply natural weighting with the Högbom deconvolver" (3.1 CO(1-0) observations)
- weighting robust: natural weighting  
  > "apply natural weighting with the Högbom deconvolver" (3.1 CO(1-0) observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: velocity bins of 100 km/s (non-detections) or 50 km/s (high S/N); a few cases different  
  > "Bin widths of 100 km $\rm s^{-1}$ were used for non-detections and 50 km $\rm s^{-1}$ bins were used if the S/N was high enough" (3.1 CO(1-0) observations)
- final beam: 12-14 arcsec (ACA CO(1-0)); 4.3 arcsec for ACA CO(3-2) of J1430+1339  
  > "The beam size of the ACA observations ranged between 12 – 14 arcsec." (3.1 CO(1-0) observations)
- final rms: ACA rms: median flux of the remaining spectrum with the line masked (values in appendix table at 100 km/s bins)  
  > "For ACA observations the rms was calculated by taking the median flux from the remaining spectra, whilst masking the line (where present)." (4.2 Spectral properties)

### Inherited from earlier work

- alpha_CO recipe (geometric mean of metallicity-dependent Genzel+12 and Bolatto+13 recipes) and mass-metallicity relation  
  > "following the $\alpha_{\rm CO}$ calculation from (cite: Tacconi18)" (4.3 Molecular gas masses); "Also following (cite: Tacconi18) we use the following mass metallicity relation from (cite: Genzel15)" (4.3 Molecular gas masses) [from (cite: Tacconi18), (cite: Genzel15)]
- Line luminosity equation L'CO  
  > "Line luminosities (L$'_{CO}$) are calculated using the following equation from (cite: Solomon97) (cite: Jarvis20)" (4.2 Spectral properties) [from (cite: Solomon97) (cite: Jarvis20)]
- Gas temperature and density modelling with the Dense Gas Toolbox  
  > "Using the Dense Gas Toolbox (cite: vandtak07; Leroy17; Johannes21)" (4.5 Gas temperature and density) [from (cite: vandtak07; Leroy17; Johannes21)]
- Sample definition and radio/optical ancillary data  
  > "For a full review and analysis of the radio data see (cite: Jarvis19; Jarvis21)." (3.5 Ancillary Multiwavelength Data) [from (cite: Jarvis19; Jarvis21)]
- ACA sensitivity estimates and project design; APEX CO(2-1) archival data  
  > "we have re-analysed the raw archival data from (cite: Jarvis20) using the new analysis techniques presented here for consistency" (3.2 CO(2-1) Observations) [from (cite: Jarvis20)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether archive-delivered or re-run calibration products were used for the ACA data
- tclean parameters beyond natural weighting and Hogbom: cell size, image size, mask, threshold, niter
- line-free channels / continuum subtraction (if any) for ACA CO(1-0) and the J1430+1339 CO(3-2) cube
- exact spectral setup (rest frequencies, spectral windows, channelisation) of the ACA observations
- how the 30 arcsec aperture was centred and whether primary-beam correction was applied before extracting spectra
- Gaussian-fit priors/initial guesses and fitting package for CO and MUSE [O III] line fitting
- MUSE data reduction and the stellar-mass/SFR inputs (from Jarvis+20, not reproduced here)
- Dense Gas Toolbox input settings (column density, line width, abundance)

## Analysis recipe

1. **image ACA CO(1-0) cubes**: tclean in CASA with natural weighting and Hogbom deconvolver; velocity bins of 50 or 100 km/s  
  > "We image the CO(1-0) emission using the TCLEAN function in CASA and apply natural weighting with the Högbom deconvolver." (3.1 CO(1-0) observations)
   - software: CASA tclean
   - parameter: bin widths 100 km/s for non-detections, 50 km/s if S/N high enough  
  > "Bin widths of 100 km $\rm s^{-1}$ were used for non-detections and 50 km $\rm s^{-1}$ bins were used if the S/N was high enough" (3.1 CO(1-0) observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **extract spectra in a common 30 arcsec aperture**: spectra extracted from the ACA cubes in an aperture matched to the APEX CO(2-1) beam (~30 arcsec diameter); curves of growth show flux flattens beyond 30 arcsec  
  > "we take an aperture equivalent to the APEX beam size when observing CO(2-1), which is $\sim$ 30 arcsec diameter" (3.1 CO(1-0) observations); "Beyond 30 arcsec the flux density flattens off in almost all cases" (3.1 CO(1-0) observations)
   - parameter: aperture ~30 arcsec diameter (~80 kpc at median z)  
  > "we extract spectra with an aperture diameter of $\sim$ 80 kpc at the median redshift" (3.1 CO(1-0) observations)
   - assumption: 30 arcsec aperture captures total flux; extraction at 3 sigma level would lose on average 60% of flux  
  > "we would measure on average 60% less flux when compared to the extraction at 30 arcsec" (3.1 CO(1-0) observations)
   - fitting: _not stated_
   - validation: curves of growth of ACA CO(1-0) for sources with integrated S/N > 5  
  > "we plot the curves of growth of the ACA CO(1-0)" (3.1 CO(1-0) observations)
3. **reduce APEX single-dish spectra and correct efficiencies**: CLASS reduction with template script; main-beam efficiency and Jy/K corrections per observing period; first-order baseline  
  > "The data was reduced using the standard procedures in the Continuum and Line Analysis Single-dish Software (CLASS) (cite: Pety05)." (3.2 CO(2-1) Observations); "Baselines were stable and we only had to fit a first order baseline to each scan before averaging them." (3.2 CO(2-1) Observations)
   - software: CLASS
   - parameter: overall calibration uncertainty 10%; pointing within 2 arcsec  
  > "We estimate the overall calibration uncertainty at 10%" (3.2 CO(2-1) Observations)
   - fitting: _not stated_
   - validation: beam size checked against pointing sources; efficiencies cross-checked against CO(3-2) line monitoring sources  
  > "cross-checked the result against the CO(3-2) flux of 8 line intensity monitoring sources" (3.2 CO(2-1) Observations)
4. **fit line profiles and classify detections**: fit 1, 2 or 3 Gaussians; V50 and W80 computed from the fits; detection S/N>=5, low-S/N detection 3<=S/N<5, otherwise non-detection; 3 sigma upper limits using line widths from other transitions or the mean sample W80  
  > "we fit either one, two, or three Gaussian components to the spectra where appropriate" (4.2 Spectral properties); "are defined as spectra which show lines with an integrated S/N $\geq$ 5." (4.2 Spectral properties)
   - software: python
   - parameter: mean CO W80 for upper limits: 397 km/s (CO(1-0)), 477 km/s (CO(2-1)), 507 km/s (CO(3-2))  
  > "the average CO $W_{80}$ in that transition for all targets is used, for which these values are 397 km $\rm s^{-1}$ for CO(1-0), 477 km $\rm s^{-1}$ for CO(2-1) and 507 km $\rm s^{-1}$ for CO(3-2)" (3.2 CO(2-1) Observations)
   - parameter: 3 sigma upper limits for non-detections  
  > "For those with non detections we choose to present the 3$\sigma$ upper limits for CO flux and luminosity." (4.2 Spectral properties)
   - assumption: line widths similar between transitions for the same target  
  > "assuming we should see similar line widths between transitions" (3.2 CO(2-1) Observations)
   - fitting: Gaussian components fitted in python; sampler, priors and likelihood not stated  
  > "We fit Gaussians using standard procedures in python to obtain the integrated flux values and corresponding uncertainties for each target." (3.2 CO(2-1) Observations)
   - validation: W80 from fits compared with W80 from data (17 of 21 within uncertainties); python Gaussian fits match CLASS fits; stacking of non-detections found no flux  
  > "17 of the $W_{80}$ values from the data are within the uncertainties of the $W_{80}$ from the fit" (4.2 Spectral properties); "the results of fitting Gaussians in python match that of the Gaussian fits produced in CLASS" (3.2 CO(2-1) Observations)
5. **derive line luminosities**: L'CO from the Solomon+97 equation using line rest frequency, luminosity distance, redshift and velocity-integrated flux  
  > "Line luminosities (L$'_{CO}$) are calculated using the following equation from (cite: Solomon97) (cite: Jarvis20)" (4.2 Spectral properties)
   - assumption: H0=70, Omega_M=0.3, Omega_Lambda=0.7  
  > "We adopt $H_0=70$ km $\rm s^{-1}$  Mpc$^{-1}$, $\Omega_M=0.3$, and $\Omega_\Lambda=0.7$ throughout." (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
6. **derive molecular gas masses and gas fractions**: M_CO = alpha_CO x L'CO(1-0), alpha_CO from metallicity via Genzel+15 mass-metallicity relation using SED stellar mass; CO(2-1) converted to CO(1-0) with the median r21 for CO(1-0)-undetected targets; gas fraction = M_CO/M_star  
  > "We calculate the CO(1-0) molecular gas masses using the mass–metallicity relation used by (cite: Tacconi18) (cite: Genzel15)" (4.3 Molecular gas masses); "Gas fractions are also presented in Table [1](#tab:gasfrac) calculated as $\rm M_{CO}/M_{\star}$." (4.3 Molecular gas masses)
   - parameter: median r21 = 1.06 used to convert CO(2-1) to CO(1-0)  
  > "(median line ratio of 1.06)" (4.3 Molecular gas masses)
   - assumption: alpha_CO as a function of metallicity (geometric mean of Genzel+12 and Bolatto+13 recipes)  
  > "taking the geometric mean of the metallicity-dependent $\alpha_{\rm CO}$ recipes of (cite: Genzel12) and (cite: Bolatto13)" (4.3 Molecular gas masses)
   - fitting: _not stated_
   - validation: compared with non-AGN and AGN gas fractions of Tacconi+18  
  > "We find that our sources are consistent with the comparison sample of non-AGN and AGN." (4.3 Molecular gas masses)
7. **measure CO line ratios and SLEDs**: line ratios r_xy = L'CO(x) / L'CO(y); CO SLEDs normalised to CO(1-0) (up to CO(3-2)) or to CO(2-1) (for J_up=6,7); compared with thermalised, Milky Way, starburst/main-sequence, high-z quasar and (U)LIRG samples  
  > "We can also investigate the excitation of the gas by calculating the ratios of line luminosities of different CO transitions." (4.4.2 Line ratios); "we plot the CO SLEDs extending to these higher transitions and normalise the SLED to CO(2-1) instead of CO(1-0)" (4.4.1 CO SLEDs)
   - fitting: _not stated_
   - validation: compared with literature medians; ratios computed per kinematic component for multi-component spectra  
  > "For targets within our sample which show multiple components in their CO spectra, we calculate the line ratios for these individual components" (4.4.2 Line ratios)
8. **constrain gas temperature and density**: Dense Gas Toolbox applied to 5 targets with first three CO transitions; fixed temperatures 10-50 K in 5 K steps; density and dense-gas fraction (>10^5 cm^-3) derived  
  > "by fixing the temperatures in 5 degree increments in the range of 10 – 50 K" (4.5 Gas temperature and density)
   - software: Dense Gas Toolbox
   - parameter: temperature grid 10-50 K, step 5 K; model maximum density 10^5 cm^-3  
  > "lead to the highest density provided in the model (10$^5$ cm$^{-3}$)" (4.5 Gas temperature and density)
   - fitting: _not stated_
   - validation: r32 vs r21 plotted over Leroy+22 simulated parameter space for optical depth  
  > "Specifically, the ratio of $r_{32}$ with $r_{21}$ gives hints as to these properties" (4.5 Gas temperature and density)
9. **compare CO and ionised gas kinematics**: V50 and W80 of CO lines compared with [O III] (or Hbeta) from MUSE spectra extracted in the same 30 arcsec aperture (and 3 arcsec versus SDSS); only S/N>5 CO lines used  
  > "We only perform this analysis on those with an integrated velocity integrated S/N greater than 5" (4.6 Comparing CO and ionised gas line profiles)
   - parameter: MUSE apertures 30 arcsec and 3 arcsec  
  > "we extracted \[O III\] spectra from the MUSE cubes at both 30 arcsec (to match our CO observations) as well as at 3 arcsec (to match the SDSS observations)" (4.6 Comparing CO and ionised gas line profiles)
   - fitting: 1-3 Gaussian components fitted to MUSE spectra  
  > "we fit either one, two, or three Gaussian components to the spectra where appropriate" (4.2 Spectral properties)
   - validation: MUSE 3 arcsec [O III] profiles consistent with SDSS within uncertainties  
  > "are consistent within uncertainties" (4.6 Comparing CO and ionised gas line profiles)

## Software

- **CASA** : tclean imaging of ACA CO(1-0) data  
  > "We image the CO(1-0) emission using the TCLEAN function in CASA" (3.1 CO(1-0) observations)
- **CLASS** : reduction of APEX single-dish spectra  
  > "The data was reduced using the standard procedures in the Continuum and Line Analysis Single-dish Software (CLASS) (cite: Pety05)." (3.2 CO(2-1) Observations)
- **python** : Gaussian fitting for integrated fluxes and uncertainties  
  > "We fit Gaussians using standard procedures in python to obtain the integrated flux values and corresponding uncertainties for each target." (3.2 CO(2-1) Observations)
- **Dense Gas Toolbox** : gas density and dense-gas fraction vs temperature  
  > "Using the Dense Gas Toolbox (cite: vandtak07; Leroy17; Johannes21), the density of the gas and the dense gas fraction" (4.5 Gas temperature and density)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median r21 = L'CO(2-1)/L'CO(1-0) | 1.06 | +0.53/-0.18 (84th/16th percentiles) | dimensionless | 7 | We observe median $r_{21}$, $r_{31}$ and $r_{32}$ ratios of 1.06$^{+0.53}_{-0.18}$, 0.77$^{+0.31}_{-0.20}$ and 0.61$^{+0.43}_{-0.21}$ respectively |
| median r31 | 0.77 | +0.31/-0.20 | dimensionless | 7 | We observe median $r_{21}$, $r_{31}$ and $r_{32}$ ratios of 1.06$^{+0.53}_{-0.18}$, 0.77$^{+0.31}_{-0.20}$ and 0.61$^{+0.43}_{-0.21}$ respectively |
| median r32 | 0.61 | +0.43/-0.21 | dimensionless | 7 | We observe median $r_{21}$, $r_{31}$ and $r_{32}$ ratios of 1.06$^{+0.53}_{-0.18}$, 0.77$^{+0.31}_{-0.20}$ and 0.61$^{+0.43}_{-0.21}$ respectively |
| r61 and r62 upper limits (7 targets with high-J data) | < 0.6 in all but one target | not stated | dimensionless | 7 | ($r_{61}$ and $r_{62}$ \< 0.6 in all but one target) |
| alpha_CO range in sample | 4.0 - 4.2 | not stated | Msun (K km/s pc^2)^-1 | 6 | are within the range 4.0 – 4.2 |
| molecular gas masses range | 0.36 - 5.50 x 10^10 | not stated | Msun | 6 | The molecular gas masses in our sample range from 0.36 – 5.50 $\times 10^{10}$ M$_\odot$ |
| gas fractions M_CO/M_star range | 0.06 - 1.4 | not stated | dimensionless | 6 | We find values in the range 0.06 – 1.4. |
| median W80 difference between [O III] and CO | ~200 (maximum ~650) | not stated | km/s | 9 | The median difference in $W_{80}$ between \[O III\] and CO is $\sim$ 200 km $\rm s^{-1}$ , with a maximum difference of $\sim$ 650 km $\rm s^{-1}$ |
| number of sources with CO(6-5) or CO(7-6) detection | 1 of 7 (J1430+1339) | not stated | dimensionless | 7 | only 1 source, J1430+1339, has a detection in either CO(6-5) or CO(7-6) |
| literature comparison: local star-forming galaxies median r21 | 0.65 | +0.18/-0.15 | dimensionless | 7 | a compilation of low-z samples found a median $r_{21}$ of 0.65 (cite: Leroy22) |
| flux lost if CO(1-0) extracted with a 3 sigma minimum level instead of the 30 arcsec aperture | 60% on average (range 25-89%) | not stated | percent | 2 | we would measure on average 60% less flux when compared to the extraction at 30 arcsec |

## Qualitative findings

- Gas fractions of the quasars are consistent with non-AGN and AGN from the literature  
  > "We find that our sources are consistent with the comparison sample of non-AGN and AGN." (4.3 Molecular gas masses)
- [O III] line profiles are consistent or broader than CO profiles in all cases  
  > "in all cases we observe consistent or broader \[O III\] line profiles than in the CO transitions" (4.6 Comparing CO and ionised gas line profiles)
- Only 2 of 17 sources show multiple CO components versus 13 of 17 in MUSE ionised gas  
  > "we identify 2 out of 17 sources with CO spectra that show multiple components in CO whereas in the MUSE ionised gas data we find 13 out of 17 sources with multiple components" (4.6 Comparing CO and ionised gas line profiles)

## Claim tuples

- H: Quasar feedback (ionised outflows, radio jets) changes global CO excitation relative to non-feedback galaxies | E: CO(1-0), (2-1), (3-2) line ratios and SLEDs from ACA and APEX compared with (U)LIRGs, AGN and star-forming galaxies | R: median r21 = 1.06, r31 = 0.77, r32 = 0.61, consistent with local (U)LIRGs and higher than star-forming galaxies | F: no significant impact of feedback on global CO excitation; any effect is localised | **supported**
- H: Quasar hosts have different molecular gas fractions from non-AGN galaxies | E: M_CO from CO(1-0) (or converted CO(2-1)) and SED stellar masses compared with Tacconi+18 | R: gas fractions 0.06-1.4, consistent with non-AGN and AGN | F: no difference in molecular gas fractions | **supported**
- H: High-J CO transitions (J_up = 6, 7) show higher excitation in these quasars as in high-z quasars | E: APEX SEPIA660 CO(6-5)/CO(7-6) for 7 targets normalised to CO(2-1) | R: 1 detection (J1430+1339), upper limits for 6; low excitation compared with high-z quasars | F: lower excitation than high-z quasars, attributed (suggested) to their higher bolometric luminosities | **supported**
- H: Ionised and molecular gas show different kinematics | E: V50 and W80 of CO compared with MUSE [O III] in 30 arcsec apertures | R: [O III] systematically broader than CO; median W80 difference ~200 km/s | F: larger impact of feedback on ionised than molecular gas, or cold clouds do not survive in hot winds | **supported**
- H: High r21 values reflect physical (optical depth) effects rather than resolved-out CO(1-0) flux | E: Compared with Montoya+23 (more nearby, more over-resolved) and discussed ACA recoverable scale | R: similar line ratios in Montoya+23 despite different resolution effects | F: optical depth effects may contribute; observational effects cannot be excluded | **partially**

## Reasoning

- Why this data: ACA CO(1-0) gives the ground-state reference; spectra extracted in a ~30 arcsec aperture matched to APEX to compare the same regions  
  > "Using this aperture consistently to extract the spectra allowed us to compare the fluxes obtained from the same regions" (3.1 CO(1-0) observations)
- Why this method: V50 and W80 from fits to the data chosen over measurements on the data because the fit W80 is mostly larger and closer to higher S/N literature values  
  > "we decide that the $W_{80}$ of the fits is more appropriate for this work" (4.2 Spectral properties)
- Alternative: CO(1-0) and CO(3-2) data of J1356+1026 from Sun+14 were excluded because of higher resolution and likely over-resolving the total CO emission  
  > "these are excluded from any analysis" (4.2 Spectral properties)
- Alternative: Jarvis+20 maximum-width method for upper limits replaced by a case-by-case approach using other transitions  
  > "The case by case approach based on information from the other CO lines for each target" (3.2 CO(2-1) Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): ACA CO(1-0) may resolve out extended emission, which could inflate r21  
  > "some of the CO(1-0) emission may be resolved out given the ACA spatial resolution" (5.1.2 Optical depth effects)
- Limitation (authors): J1430+1339 ACA CO(3-2) may be over-resolved and miss flux  
  > "there is a possibility it is slightly over resolved and perhaps missing flux" (3.3 CO(3-2) Observations)
- Limitation (authors): Small number of sources with the required data limits conclusions about correlations  
  > "it is hard to take strong conclusions from these investigations" (5.2 A localised impact on CO?)
- Limitation (authors): Low S/N limits the interpretation of multiple CO components  
  > "the lack of S/N in our CO data means that interpreting these multiple components is limited" (5.3 Comparing CO and ionised gas line profiles)
- Caveat (inferred, ours): Median line ratios rest on only 6-8 detections and the CO(1-0) ACA flux may miss extended emission, so r21 > 1 could be partly observational
- Caveat (inferred, ours): Comparison of 12-14 arcsec ACA with 30 arcsec APEX beams is only reliable if the 30 arcsec aperture captures total flux, which is tested only for S/N > 5 sources
- Caveat (inferred, ours): alpha_CO is a metallicity-based value (~4), whereas the text itself notes it may be lower in LIRGs/AGN, affecting gas fractions
- Caveat (inferred, ours): Claim of no feedback impact from global quantities cannot exclude localised effects and has no matched control sample of non-feedback quasars

## Reproducibility

- Data public (paper): Data available from the ESO Science Archive Facility; reduced data on reasonable request and in a Newcastle University repository  
  > "The data used in this work are available from the ESO Science Archive Facility" (Data Availability); "Data is also available at Newcastle University’s data repository" (Data Availability)
- Products in archive: All tables in digital form and .fits files of the spectra are available in the repository  
  > "Specifically, all tables in digital format and .fits files of the spectra are available." (Data Availability)
- Missing: CASA version and tclean parameters (cell, image size, mask, threshold, iterations) for ACA cubes
- Missing: aperture centring and exact spectral extraction procedure
- Missing: Gaussian fitting code/priors
- Missing: MUSE reduction products and SED-derived stellar masses (only cited)
- Missing: APEX raw data reduction details beyond template script and calibration notes
- Data volume (inferred): small to moderate: 13 ACA CO(1-0) datasets plus one ACA CO(3-2) dataset (a few GB each of calibrated cubes); APEX data are small spectra
- Score (inferred): 3/5, Public ACA and APEX data and a spectra repository exist, and the analysis equations are given, but CASA version, tclean parameters, extraction details and fitting code are not stated.
- Rediscovery candidate: no, The key ratios combine public APEX single-dish data with ACA cubes, and the imaging and extraction recipe is incomplete (no CASA version, masks, centring).

## Links

- Method: (cite: Tacconi18) (alpha_CO and gas fraction method followed for consistency)
- Method: (cite: Jarvis20) (earlier APEX CO(2-1) pilot, SED stellar masses and L'CO equation)
- Method: (cite: Pety05) (CLASS single-dish reduction)
- Companion: (cite: Jarvis21) (QFeedS sample definition and multi-wavelength data)
- Companion: (cite: Jarvis19) (VLA radio observations and L_IR for the sample)
- Companion: (cite: Almeida21) (high-resolution ALMA CO(2-1) for four targets)
- Related: Quasar Feedback Survey (QFeedS)

## Checks

```json
{
 "quotes": 124,
 "quotes_ok": 124,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 84,
  "rate": 0.718
 },
 "evidence_ok": true
}
```
