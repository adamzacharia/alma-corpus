# Rotational Spectrum and First Interstellar Detection of 2-methoxyethanol Using ALMA Observations of NGC 6334I

`2024ApJ...965L..23F` | The Astrophysical Journal Letters 2024 | first author: Fried, Zachary T. P. | arXiv: 2403.17341 | DOI: 10.3847/2041-8213/ad37ff

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Can the laboratory rotational spectrum of 2-methoxyethanol be extended to mm/sub-mm frequencies and used to search for the molecule toward NGC 6334I and IRAS 16293-2422B, and what do the abundance differences imply for formation chemistry?  
  > "The resulting rotational parameters permitted a search for this molecule in Atacama Large Millimeter/submillimeter Array (ALMA) observations toward the massive protocluster NGC 6334I" (abstract); "We also investigate physical differences between the two interstellar sources that could result in the observed abundance variations." (abstract)
- Target **NGC 6334I**: coordinates not stated (same coordinates as the methoxymethanol detection, cite: methoxy_detection)  
  > "These data were extracted from the same coordinates that were used to confirm the first interstellar detection of methoxymethanol (cite: methoxy_detection)." (Observational Analysis and Results); z/distance _not stated_; distance from _not stated_
- Target **IRAS 16293-2422B**: coordinates position offset by 0.5 arcsec from the continuum peak  
  > "we analysed the spectrum taken at a position offset by 0.5$''$ from the continuum peak" (Observational Analysis and Results); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00661.S, 2013.1.00278.S, 2012.1.00712.S
- bands: Band 4 (NGC 6334I); Band 7 (IRAS 16293-2422B, PILS)  
  > "25 rotational transitions are observed in the ALMA Band 4 data toward NGC 6334I" (abstract); "molecular signal is not observed in the Band 7 data toward IRAS 16293-2422B" (abstract)
- frequencies and spectral setup: NGC 6334I: four spws, each 937.500 MHz wide, centered at 130.50, 131.55, 144.47, 145.40 GHz (TOPO), 1.1 km/s resolution, 0.49 MHz channels. PILS: 329.1-362.9 GHz, ~0.2 km/s resolution  
  > "The data contain four spectral windows, each with a bandwidth of 937.500 MHz, central (TOPO) frequencies of 130.50, 131.55, 144.47, 145.40 GHz, respectively" (NGC 6334I Observations); "a spectral resolution of 1.1 km s$^{-1}$ corresponding to a channel width of 0.49 MHz" (NGC 6334I Observations); "covering frequencies from 329.1 to 362.9 GHz with an angular resolution of 0.5$''$ and spectral resolution of $\approx$0.2 km s$^{-1}$" (IRAS 16293-2422B Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: NGC 6334I: 0.15 - 5.2 km (unprojected)  
  > "with (unprojected) baseline lengths ranging from 0.15 - 5.2 km" (NGC 6334I Observations)
- angular resolution: NGC 6334I native (robust=0.5) 0.23 x 0.16 arcsec, convolved to 0.26 x 0.26 arcsec; PILS 0.5 arcsec  
  > "The native robust=0.5 angular resolution of the resulting continuum image and spectral line cubes was 0$^{\prime\prime}$.23$\times$ 0$^{\prime\prime}$.16." (NGC 6334I Observations); "with an angular resolution of 0.5$''$" (IRAS 16293-2422B Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: NGC 6334I: 2017-12-03 (1), 2018-12-07 (1), 2018-01-04 (2)  
  > "The data are comprised of four datasets obtained on 2017-12-03 (1), 2018-12-07 (1), and 2018-01-04 (2)." (NGC 6334I Observations)
- pi or archival as stated: NGC 6334I: Cycle 5 program 2017.1.00661.S; IRAS 16293B: PILS survey, project 2013.1.00278.S  
  > "The Band 4 data used in this paper are from the Cycle 5 ALMA program 2017.1.00661.S" (NGC 6334I Observations); "using observational data from the ALMA Protostellar Interferometry Line Survey, PILS ((cite: jor16); project id: 2013.1.00278.S)" (IRAS 16293-2422B Observations)
- Line: 2-methoxyethanol (CH3OCH2CH2OH) 25 transitions observed in Band 4 toward NGC 6334I, listed in Table B2 (e.g. J=25-24 and J=29-28, 28-27 a-type series) (within the Band 4 spws centered at 130.50, 131.55, 144.47, 145.40 GHz (Table B2 lists ~130.14 to 145.62 GHz))
- Line: 2-methoxyethanol (CH3OCH2CH2OH) eight predicted-brightest transitions in the PILS range toward IRAS 16293B (not detected) (329.1-362.9 GHz (PILS range))
- Other facility **PILS (ALMA Protostellar Interferometry Line Survey)**: ALMA Band 7 spectral survey data of IRAS 16293-2422 used for the non-detection and upper limit  
  > "PILS consists of an unbiased line survey of IRAS 16293-2422 using ALMA covering frequencies from 329.1 to 362.9 GHz" (IRAS 16293-2422B Observations)
- Other facility **Lille spectrometer (fast-scan mode)**: laboratory spectrum at 150-220, 230-330 and 370-500 GHz  
  > "The mm and sub-mm spectrum was predominately measured using the Lille spectrometer (cite: lille) with fast-scan mode (cite: fast_scan)" (Spectroscopic Analysis and Results)
- Other facility **MIT CP-FT mm-wave spectrometer**: laboratory spectrum at 68-85 GHz  
  > "The $68-85\,$GHz spectrum was recorded with a newly updated chirped-pulse Fourier transform (CP-FT) mm-wave spectrometer at MIT." (Spectroscopic Analysis and Results)
- Other facility **New College of Florida waveguide CP-FT spectrometer**: laboratory centimeter-wave spectrum at 8.7-26.5 GHz  
  > "centimeter-wave data from $8.7-26.5\,$GHz was collected at the New College of Florida using a waveguide-based CP-FT spectrometer (cite: ncf)" (Spectroscopic Analysis and Results)
- External data: Predicted column density of 2-methoxyethanol toward IRAS 16293B from the machine learning model (motivation for the search)  
  > "trained a machine learning model to map the molecular identities of the detected species to their observed column densities." (Introduction) [from (cite: fried)]
- External data: Earlier rotational constants and dipole moments for 2-methoxyethanol (Stark-modulated spectra, to ~40 GHz)  
  > "The authors measured 38 lines of the ground vibrational state of the most stable conformer in the frequency range of $8-26.5\,$GHz" (Introduction) [from (cite: buckley); (cite: caminati)]
- External data: Conformer geometries used as inputs to the quantum chemical calculations  
  > "Using their reported geometries as inputs (which were optimized using the complete basis set CBS-QB3 ab initio method)" (Quantum Chemical Calculations) [from (cite: conformers)]
- External data: Spectroscopic catalogs of the other 19 molecules in the NGC 6334I model, from JPL and CDMS  
  > "Catalogs obtained from the JPL spectroscopic database (cite: jpl_database)." (Appendix B); "All other catalogs were obtained from CDMS (cite: cdms_database)." (Appendix B) [from (cite: jpl_database); (cite: cdms_database)]
- External data: Methoxymethanol/methoxyethanol ratio in IRAS 16293B (>56) and methoxymethanol excitation temperature (130 K)  
  > "while it is $>56$ in IRAS 16293B (cite: eme_iras)" (Abundance Differences Between Sources); "the excitation temperature of methoxymethanol was found to be 130 K; (cite: eme_iras)" (Observational Analysis and Results) [from (cite: eme_iras)]
- External data: Methoxymethanol/methoxyethanol ratio ~31 in NGC 6334I  
  > "In NGC 6334I, this ratio is $\sim$31 (cite: methoxy_detection)" (Abundance Differences Between Sources) [from (cite: methoxy_detection)]
- External data: DME/methoxymethanol ratio of 1.7 and ethanol/methoxyethanol ratio >92 in IRAS 16293B  
  > "In IRAS 16293B, the DME/methoxymethanol ratio is 1.7 (cite: jor18; eme_iras)." (Abundance Differences Between Sources); "However, in IRAS 16293B, the ratio is $>92$ (cite: jor18)." (Abundance Differences Between Sources) [from (cite: jor18); (cite: eme_iras)]
- Simulation/model as data: Simulated emission spectrum of 20 molecules for NGC 6334I (single-excitation-temperature model) used to constrain Tex, linewidth, velocity and column density  
  > "A simulated emission spectrum comprised of 20 molecules was used to constrain the physical parameters necessary to model the molecular spectra" (Observational Analysis and Results)
- Simulation/model as data: LTE synthetic spectra for IRAS 16293B with single column density and Tex, 0.5 arcsec FWHM Gaussian source, 1 km/s FWHM linewidth, 2.6 km/s offset  
  > "that the emission has a Gaussian distribution with a FWHM of 0.5$''$, and the line width and offset is similar to other species identified in PILS (1 km s$^{-1}$ FWHM and 2.6 km s$^{-1}$, respectively)" (Observational Analysis and Results)

## Processing

### Calibration

- pipeline or manual: Cycle 6 ALMA Pipeline, then improved uv-continuum subtraction and iterative self-calibration (NGC 6334I)  
  > "The data were initially calibrated using the Cycle 6 ALMA Pipeline." (NGC 6334I Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 20% flux uncertainty per transition (flux calibration plus noise, added in quadrature)  
  > "We conservatively estimate that the flux uncertainty on any given transition is 20%" (Observational Analysis and Results); "which encompasses both the estimated flux calibration uncertainty and a measurement of the noise level of the observations in a nearby line-free region added in quadrature" (Observational Analysis and Results)
- self calibration: iterative self-calibration starting from the line-free continuum image; solutions applied to continuum-subtracted uv-data  
  > "used as the starting point for an iterative self-calibration, the solutions of which were also applied to the continuum-subtracted uv-data" (NGC 6334I Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "The native robust=0.5 angular resolution of the resulting continuum image and spectral line cubes" (NGC 6334I Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line-free channels identified and used to improve the default pipeline uv-continuum subtraction  
  > "Then line-free channels were identified and used to improve the default pipeline uv-continuum subtraction." (NGC 6334I Observations)
- line free channels: _not stated_
- primary beam correction: applied before analysis  
  > "primary beam correction was applied before beginning our analysis" (NGC 6334I Observations)
- array combination: _not stated_
- smoothing: convolved to a common angular resolution of 0.26 x 0.26 arcsec  
  > "The images were subsequently convolved to a common angular resolution of 0$^{\prime\prime}$.26$\times$ 0$^{\prime\prime}$.26" (NGC 6334I Observations)
- final beam: 0.26 x 0.26 arcsec (NGC 6334I)  
  > "convolved to a common angular resolution of 0$^{\prime\prime}$.26$\times$ 0$^{\prime\prime}$.26" (NGC 6334I Observations)
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration and continuum-subtraction workflow for the NGC 6334I data  
  > "(see e.g. (cite: Brogan18self))" (NGC 6334I Observations) [from (cite: Brogan18self)]
- Automated simultaneous fitting routine for all molecules in the NGC 6334I model  
  > "The parameters for all of the molecules were simultaneously fit by an automated routine as described in (cite: ngc_fitting)." (Observational Analysis and Results) [from (cite: ngc_fitting)]
- Extraction position for NGC 6334I spectra  
  > "These data were extracted from the same coordinates that were used to confirm the first interstellar detection of methoxymethanol (cite: methoxy_detection)." (Observational Analysis and Results) [from (cite: methoxy_detection)]
- MCMC population diagram procedure for Tex and N_T  
  > "following the procedures outlined in (cite: Loomis:2018:131), we performed a Markov Chain Monte Carlo analysis" (Observational Analysis and Results) [from (cite: Loomis:2018:131); population diagram (cite: Goldsmith:1999:209)]
- PILS survey data and further details of the survey  
  > "We refer to (cite: jor16) for further details about the survey and the data from it." (IRAS 16293-2422B Observations) [from (cite: jor16)]
- Level of theory for computed rotational constants  
  > "They determined that the $\omega$B97X-D/6-31+G(d) level of theory and basis set provided a strong balance between calculation uncertainty and efficiency." (Quantum Chemical Calculations) [from (cite: lee_bayesian)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA execution blocks / member OUS IDs and whether the archive pipeline products or a manual reprocessing were used for 2017.1.00661.S
- Which CASA version was used for self-calibration and imaging, and the tclean parameters (deconvolver, cell, image size, masks, niter, threshold)
- The actual line-free channel ranges and self-calibration solution intervals
- The sky coordinates of the NGC 6334I extraction position (only referenced to the methoxymethanol paper) and the aperture or pixel used
- The list of fitted parameters, priors and fit results for the other 19 molecules in the NGC 6334I model, and the velocity and linewidth values adopted
- MCMC settings (sampler, priors, number of walkers and steps, convergence criteria) and the partition function convention in the population diagram
- Which of the 25 transitions entered the population diagram and how blended lines were treated
- Details of the IRAS 16293B spectrum extraction from PILS (coordinates, continuum treatment) and the noise level used to set the 2.5e15 cm^-2 upper limit
- The spectroscopic catalog for 2-methoxyethanol (line list and dipole moments) is in supplementary material rather than described in the text; the dipole moment values used in the ALMA modelling are not stated
- Version of molsim

## Analysis recipe

1. **Quantum chemical conformer and rotational constant calculations**: Re-ran geometry and energy calculations for the 12 conformers (MP2/aug-cc-pVTZ, CCSD(T) single points), and computed A, B, C with wB97X-D/6-31+G(d); simulated spectra with SPCAT  
  > "The geometries and harmonic vibrational frequencies of these molecules were calculated using Gaussian 16 (cite: g16) with the MP2 level of theory and aug-cc-pVTZ basis set." (Quantum Chemical Calculations); "simulated rotational spectra were generated using SPCAT in Pickett’s CALPGM suite of programs (cite: spcat)" (Quantum Chemical Calculations)
   - software: Gaussian 16, SPCAT
   - parameter: Tight convergence criteria for geometry optimizations  
  > "Tight convergence criteria was used for the geometry optimizations." (Quantum Chemical Calculations)
   - fitting: _not stated_
   - validation: Computed A, B, C over-predict the experimental constants by 0.13%, 0.46% and 0.34%  
  > "as the $A$, $B$, and $C$ constants are over-predicted by only 0.13%, 0.46% and 0.34%, respectively." (Spectroscopic Analysis and Results)
2. **Measure and fit the laboratory rotational spectrum**: Assigned lines starting from the simulated spectrum using Buckley constants, then fit with least squares using A and S reductions (I^r representation)  
  > "The assignment of the ground vibrational state was initiated using the simulated spectrum that was generated from the rotational constants reported by (cite: buckley)." (Spectroscopic Analysis and Results); "These were analyzed with a least-squares fitting procedure using ASFIT (cite: asfit)." (Spectroscopic Analysis and Results)
   - software: ASFIT
   - parameter: Spectra at 8.7-26.5, 68-85 and 150-500 GHz; 2,172 distinct lines, 3,396 transitions in the fit; J'' = 2-102, Ka'' = 0-32  
  > "The transitions range from $J^{\prime\prime} = 2-102$ and $K_a^{\prime\prime} = 0-32$." (Spectroscopic Analysis and Results)
   - parameter: Higher-order terms kept only if they improved the RMS error by at least around 10%  
  > "Generally, higher order terms were removed unless their inclusion resulted in at least around a 10 % improvement of the RMS error of the fit." (Spectroscopic Analysis and Results)
   - assumption: Line frequency uncertainties of 50 kHz in all spectral ranges  
  > "The uncertainties of the line frequencies were estimated to be 50 kHz throughout the entire frequency range." (Appendix A)
   - fitting: Least-squares fit with 20 constants for both A and S reductions  
  > "Both fits include 20 constants." (Spectroscopic Analysis and Results)
   - validation: Comparison to earlier constants (agree within less than 0.001% for A, B, C) and theory  
  > "In fact, they agree within less than 0.001% in each case." (Spectroscopic Analysis and Results)
3. **Calibrate and image the NGC 6334I Band 4 data**: Cycle 6 pipeline calibration, improved uv-continuum subtraction using line-free channels, iterative self-calibration, imaging at robust=0.5, smoothing to 0.26 arcsec and primary beam correction  
  > "The data were initially calibrated using the Cycle 6 ALMA Pipeline." (NGC 6334I Observations); "The images were subsequently convolved to a common angular resolution of 0$^{\prime\prime}$.26$\times$ 0$^{\prime\prime}$.26" (NGC 6334I Observations)
   - software: ALMA Pipeline
   - parameter: robust = 0.5; common beam 0.26 x 0.26 arcsec  
  > "The native robust=0.5 angular resolution of the resulting continuum image and spectral line cubes" (NGC 6334I Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model the NGC 6334I spectrum with a multi-molecule simulation**: Single-excitation-temperature simulated spectra of 20 molecules in molsim fitted simultaneously by an automated routine to constrain Tex, linewidth, velocity and column density  
  > "The molecular spectra were simulated using the `molsim` package with a single-excitation temperature model." (Observational Analysis and Results); "The parameters for all of the molecules were simultaneously fit by an automated routine as described in (cite: ngc_fitting)." (Observational Analysis and Results)
   - software: molsim
   - parameter: All molecules fit with the same linewidth and velocity; methoxyethanol linewidths lie between 1.37 and 1.53 MHz  
  > "A decision was made separately to fit all of the molecules with the same linewidth and velocity" (Observational Analysis and Results); "The line widths for our frequency range lie between 1.37 and 1.53 MHz." (Observational Analysis and Results)
   - assumption: Source fills the beam  
  > "The source was assumed to fill the beam." (Observational Analysis and Results)
   - fitting: Automated simultaneous fit as in El-Abd et al. 2024; sampler and priors not stated here  
  > "The parameters for all of the molecules were simultaneously fit by an automated routine as described in (cite: ngc_fitting)." (Observational Analysis and Results)
   - validation: Assumption of common linewidth and velocity said to match all molecules in the model  
  > "this assumption is well-matched to all of the molecules in our model" (Observational Analysis and Results)
5. **Derive methoxyethanol Tex and column density with an MCMC population diagram**: MCMC to generate posterior distributions for a population diagram analysis of methoxyethanol alone  
  > "we performed a Markov Chain Monte Carlo analysis to generate posterior probability distributions for a population diagram analysis for just methoxyethanol" (Observational Analysis and Results)
   - parameter: Parameters of interest: N_T and Tex  
  > "To better explore the uncertainty space for the derived methoxyethanol parameters in particular ($N_T$ and $T_{ex}$)" (Observational Analysis and Results)
   - assumption: 20% flux uncertainty on each transition  
  > "We conservatively estimate that the flux uncertainty on any given transition is 20%" (Observational Analysis and Results)
   - fitting: MCMC following Loomis et al. 2018; priors and sampler not stated  
  > "following the procedures outlined in (cite: Loomis:2018:131), we performed a Markov Chain Monte Carlo analysis" (Observational Analysis and Results)
   - validation: _not stated_
6. **Search for methoxyethanol toward IRAS 16293B and set an upper limit**: Compared LTE synthetic spectra (Tex 100 to 150 K, also 300 K) to the PILS spectrum at a position offset 0.5 arcsec from the continuum peak; upper limit set by the synthetic spectrum that is not exceeded by the data  
  > "The plotted synthetic spectrum corresponds to a column density of $2.5\times10^{15}$ cm$^{-2}$, which represents the upper limit to the methoxyethanol column density toward this position." (Observational Analysis and Results)
   - parameter: Tex 100 to 150 K (methoxymethanol Tex 130 K); also tested 300 K  
  > "for an excitation temperature of 100 to 150 K (the excitation temperature of methoxymethanol was found to be 130 K; (cite: eme_iras))" (Observational Analysis and Results); "Searching for methoxyethanol at an excitation temperature of 300 K also does not reveal any detected lines" (Observational Analysis and Results)
   - assumption: LTE, single column density and Tex, Gaussian emission FWHM 0.5 arcsec, linewidth 1 km/s FWHM, offset 2.6 km/s  
  > "We calculate synthetic spectra assuming that the gas is in local thermodynamical equilibrium, that the emission can be reproduced with a single column density and excitation temperature" (Observational Analysis and Results)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare abundance ratios between NGC 6334I and IRAS 16293B**: Compared methoxymethanol/methoxyethanol, DME/methoxymethanol and ethanol/methoxyethanol ratios using literature values for IRAS 16293B and the NGC 6334I values from this work  
  > "A more informative metric to gauge the relative underproduction of 2-methoxyethanol in IRAS 16293B may therefore be the methoxymethanol/methoxyethanol ratios in these sources." (Abundance Differences Between Sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALMA Pipeline** Cycle 6: initial calibration of the NGC 6334I Band 4 data  
  > "The data were initially calibrated using the Cycle 6 ALMA Pipeline." (NGC 6334I Observations)
- **molsim** : simulating molecular spectra with a single-excitation temperature model  
  > "The molecular spectra were simulated using the `molsim` package with a single-excitation temperature model." (Observational Analysis and Results)
- **Gaussian 16** Revision C.01 (reference list): geometries, vibrational frequencies and rotational constants of 2-methoxyethanol conformers  
  > "The geometries and harmonic vibrational frequencies of these molecules were calculated using Gaussian 16 (cite: g16)" (Quantum Chemical Calculations)
- **SPCAT (CALPGM)** : simulating rotational spectra from calculated constants  
  > "simulated rotational spectra were generated using SPCAT in Pickett’s CALPGM suite of programs (cite: spcat)" (Quantum Chemical Calculations)
- **ASFIT** : least-squares fitting of the measured rotational transitions  
  > "These were analyzed with a least-squares fitting procedure using ASFIT (cite: asfit)." (Spectroscopic Analysis and Results)
- **JPL spectroscopic database** : catalogs for some model molecules  
  > "Catalogs obtained from the JPL spectroscopic database (cite: jpl_database)." (Appendix B)
- **CDMS** : catalogs for the other model molecules  
  > "All other catalogs were obtained from CDMS (cite: cdms_database)." (Appendix B)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 2-methoxyethanol column density toward NGC 6334I | 1.3e17 | +1.4/-0.9 e17 | cm^-2 | 5 | A column density of $1.3_{-0.9}^{+1.4} \times 10^{17}$ cm$^{-2}$ is derived at an excitation temperature of $143_{-39}^{+31}$ K. |
| 2-methoxyethanol excitation temperature toward NGC 6334I | 143 | +31/-39 | K | 5 | A column density of $1.3_{-0.9}^{+1.4} \times 10^{17}$ cm$^{-2}$ is derived at an excitation temperature of $143_{-39}^{+31}$ K. |
| Number of methoxyethanol transitions observed in NGC 6334I Band 4 | 25 (nine unblended or partially blended) | not stated | dimensionless | 4 | Overall, we observed 25 methoxyethanol transitions in the Band 4 observations of NGC 6334I.; Nine transitions are either completely unblended or only partially blended. |
| Methoxyethanol linewidth range in NGC 6334I | 1.37 to 1.53 | not stated | MHz | 4 | The line widths for our frequency range lie between 1.37 and 1.53 MHz. |
| Upper limit on methoxyethanol column density toward IRAS 16293B | 2.5e15 | upper limit | cm^-2 | 6 | The plotted synthetic spectrum corresponds to a column density of $2.5\times10^{15}$ cm$^{-2}$, which represents the upper limit to the methoxyethanol column density toward this position. |
| DME/methoxymethanol ratio toward the NGC 6334I position | 0.35 | not stated | dimensionless | 7 | However, this ratio is 0.35 toward the position of NGC 6334I investigated in this work. |
| Ethanol column density in NGC 6334I | 1.59e18 | not stated | cm^-2 | 4 | In NGC 6334I, this value is approximately 12 (with the derived ethanol column density being $1.59 \times 10^{18}$ cm$^{-2}$). |
| Ethanol/methoxyethanol ratio in NGC 6334I | ~12 | not stated | dimensionless | 7 | In NGC 6334I, this value is approximately 12 (with the derived ethanol column density being $1.59 \times 10^{18}$ cm$^{-2}$). |
| Lab fit: number of distinct lines / transitions in the fit | 2,172 lines / 3,396 transitions | not stated | dimensionless | 2 | In all, a total of 2,172 distinct lines were identified and measured.; Including blended lines, this corresponded to 3,396 transitions included in the fit. |
| Rotational constant A (A reduction) | 12982.3438 | (23) | MHz | 2 | 12982.3438(23) |
| Rotational constant B (A reduction) | 2742.50569 | (10) | MHz | 2 | 2742.50569(10) |
| Rotational constant C (A reduction) | 2468.107109 | (94) | MHz | 2 | 2468.107109(94) |
| Relative stability of tGg- conformer | 5.72 kJ/mol more stable than any other conformer | not stated | kJ/mol | 1 | The tGg- conformer was calculated to be 5.72 kJ/mol more stable than any other conformational arrangement of this molecule. |

## Qualitative findings

- First interstellar detection of 2-methoxyethanol toward NGC 6334I using ALMA Band 4 data  
  > "resulting in the first interstellar detection of 2-methoxyethanol" (abstract)
- No clear molecular signal toward IRAS 16293B; only an upper limit could be derived  
  > "A search for this molecule was also conducted in the ALMA data toward IRAS 16293B; however, clear molecular signal was not observed." (Introduction)
- Radical recombination and insertion reactions are proposed as plausible formation routes  
  > "We proceeded to discuss potential formation pathways of the molecule, especially focusing on those stemming from known interstellar precursors." (Conclusions)
- The machine learning model overpredicted the methoxyethanol column density toward IRAS 16293B  
  > "both overpredicted methoxyethanol to have a column density of $\sim$$10^{17}$ cm$^{-2}$ toward IRAS 16293B" (Validation of Machine Learning Prediction)

## Claim tuples

- H: 2-methoxyethanol is present in the interstellar medium toward the hot core NGC 6334I | E: Searched ALMA Band 4 data using the newly measured laboratory spectrum and a multi-molecule spectral model | R: 25 transitions observed, 9 unblended or partially blended; Tex = 143 K, N_T = 1.3e17 cm^-2 | F: First interstellar detection of 2-methoxyethanol | **supported**
- H: 2-methoxyethanol is detectable toward IRAS 16293B as predicted by the machine learning model | E: Compared LTE synthetic spectra to PILS Band 7 data | R: No clean lines; upper limit 2.5e15 cm^-2 | F: The molecule is not detected and the model prediction (~1e17 cm^-2) was an overprediction | **refuted**
- H: The relative abundance of 2-methoxyethanol differs between the high-mass NGC 6334I and the low-mass IRAS 16293B | E: Compared methoxymethanol/methoxyethanol, DME/methoxymethanol and ethanol/methoxyethanol ratios | R: Methoxymethanol/methoxyethanol ~31 vs >56; ethanol/methoxyethanol ~12 vs >92 | F: Methoxyethanol appears more efficiently produced in NGC 6334I; causes are discussed but not established | **partially**
- H: The rotational spectrum of 2-methoxyethanol can be extended beyond ~40 GHz into the mm/sub-mm for astronomical searches | E: Measured spectra at 8.7-26.5, 68-85 and 150-500 GHz and fit with ASFIT | R: 2,172 distinct lines (3,396 transitions) fit with 20 constants | F: Improved rotational parameters usable for interstellar searches | **supported**

## Reasoning

- Why this data: Machine learning prediction flagged 2-methoxyethanol as a strong candidate in IRAS 16293B; warm sources are needed since strongest transitions lie in the mm and sub-mm  
  > "The notable column density prediction for this molecule along with the simulated rotational parameters suggested that this molecule was a strong candidate for detection." (Introduction); "the strongest transitions of these species arise in the millimeter (mm) and submillimeter (sub-mm) regimes." (Introduction)
- Why this method: Microwave spectrum re-measured because chirped-pulse spectrometers are more sensitive than the earlier Stark-modulated ones  
  > "newer chirped-pulse Fourier transform spectrometers are generally more sensitive than the Stark-modulated spectrometers employed in the earlier studies" (Spectroscopic Analysis and Results)
- Alternative: Lab fit was run with both A and S reductions; they were of similar quality  
  > "The fits using the A and S reduction were ultimately of similar quality." (Spectroscopic Analysis and Results)
- Alternative: IRAS 16293B search repeated at 300 K excitation temperature, still no lines and a lower upper limit  
  > "the upper limit to the column density is even more stringent (lower) than what was found above" (Observational Analysis and Results)
- How they decided it was enough: _not stated_
- Limitation (authors): A-E split lines and perturbed high-Ka transitions were not included in the lab fit; excited vibrational states and other conformers not yet analysed  
  > "As of now, the split lines were not included in the fit" (Spectroscopic Analysis and Results)
- Limitation (authors): Several detected lines are weak  
  > "Several of these lines, however, appear to be quite weak in the spectrum." (Observational Analysis and Results)
- Limitation (authors): Gas-phase formation pathway effectiveness not fully understood; desorption behaviour of methoxyethanol unmeasured  
  > "the effectiveness of this proposed gas-phase pathway is still not fully understood and requires further study" (Possible Formation Pathways); "It is clear that further experiments of the desorption mechanisms and temperatures of these molecules are required to draw any definitive conclusions." (Abundance Differences Between Sources)
- Caveat (inferred, ours): Detection rests on 25 transitions of which only nine are unblended or partially blended; blending treatment is not described
- Caveat (inferred, ours): Column density depends on a source-fills-beam assumption and a single Tex, with large uncertainties (+1.4/-0.9e17)
- Caveat (inferred, ours): The IRAS 16293B upper limit is set by eye from one synthetic spectrum at one offset position with assumed source size
- Caveat (inferred, ours): Comparison of ratios across sources mixes different beams, positions and literature analyses
- Caveat (inferred, ours): Formation-route discussion is speculative with no modelling or quantitative test

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Computational outputs available in the Supplementary Information  
  > "All of the computational outputs are available in the Supplementary Information." (Quantum Chemical Calculations)
- Missing: Extraction coordinates for NGC 6334I and the full 20-molecule model parameters (in El-Abd et al. 2024 and Supplementary Information)
- Missing: MCMC settings and population diagram inputs (line selection, blending treatment)
- Missing: CASA version, imaging parameters and line-free channels
- Missing: IRAS 16293B extraction details and noise level
- Missing: Lab line list and dipole moments for the ALMA modelling (supplementary)
- Data volume (inferred): Roughly a few hundred GB raw for four Band 4 EBs plus PILS Band 7 products; imaged cubes much smaller (rough guess)
- Score (inferred): 2/5, The ALMA projects are named and the key results are numeric, but the model of the other 19 molecules, extraction coordinates, MCMC settings and imaging parameters are inherited or not stated, so the detection cannot be redone from the paper alone.
- Rediscovery candidate: no, The paper does not state that the data are public and the NGC 6334I model, extraction position and fit settings are deferred to other work or not given, so the main result cannot be redone from the paper's recipe.

## Links

- Method: El-Abd et al. 2024 (cite: ngc_fitting) (automated multi-molecule fitting routine for NGC 6334I)
- Method: Brogan, Hunter & Fomalont 2018 (cite: Brogan18self) (self-calibration and continuum subtraction workflow)
- Method: Loomis et al. 2018 (cite: Loomis:2018:131) (MCMC population diagram procedure)
- Method: Jorgensen et al. 2016 (cite: jor16) (PILS survey and data description)
- Method: Kisiel & Bialkowska-Jaworska 2019 (cite: asfit) (ASFIT spectral fitting)
- Companion: McGuire et al. 2017 (cite: methoxy_detection) (first detection of methoxymethanol toward NGC 6334I; position and comparison ratio)
- Companion: Manigand et al. 2020 (cite: eme_iras) (methoxymethanol and ethyl methyl ether in PILS toward IRAS 16293B)
- Companion: Fried et al. 2023 (cite: fried) (machine learning prediction that motivated the search)
- Related: PILS (ALMA Protostellar Interferometry Line Survey)
- Related: 2017.1.00661.S
- Related: 2012.1.00712.S (acknowledged only)

## Checks

```json
{
 "quotes": 124,
 "quotes_ok": 124,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00712.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 114,
  "stated": 79,
  "rate": 0.693
 },
 "evidence_ok": true
}
```
