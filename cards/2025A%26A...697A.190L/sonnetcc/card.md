# The ALMA-ATOMS survey: A sample of weak hot core candidates identified through line stacking

`2025A&A...697A.190L` | Astronomy and Astrophysics 2025 | first author: Li, Zi-Yang | arXiv: 2504.06802 | DOI: 10.1051/0004-6361/202452762

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, astrochemistry
- Question: Identify hot cores in the ALMA-ATOMS sample with molecular line stacking, especially weak-emission candidates, to provide one of the largest hot core candidate samples  
  > "to identify hot cores, with a particular focus on weak-emission candidates, and to provide one of the largest samples of hot core candidates to date." (abstract)
- Target **146 ATOMS massive clumps (hot core candidates in 100 cores)**: coordinates not stated in text (peak positions of the 100 cores are tabulated in the additional tables)  
  > "A sample of 146 massive clumps was observed in the ALMA band 3 survey, the ALMA-ATOMS project" (2 Data); "The distances from the Sun are compiled in (cite: 2020MNRAS.496.2790L)." (Additional tables (Table notes)); z/distance per-source distances, tabulated in the additional tables  
  > "A sample of 146 massive clumps was observed in the ALMA band 3 survey, the ALMA-ATOMS project" (2 Data); "The distances from the Sun are compiled in (cite: 2020MNRAS.496.2790L)." (Additional tables (Table notes)); distance from compiled in (cite: 2020MNRAS.496.2790L)  
  > "A sample of 146 massive clumps was observed in the ALMA band 3 survey, the ALMA-ATOMS project" (2 Data); "The distances from the Sun are compiled in (cite: 2020MNRAS.496.2790L)." (Additional tables (Table notes))
- Target **I18032-2032 (G9.62+0.19), template/calibration source**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00685.S
- bands: Band 3 (3 mm)  
  > "A sample of 146 massive clumps was observed in the ALMA band 3 survey" (2 Data)
- frequencies and spectral setup: SPW 7: 97 536-99 442 MHz; SPW 8: 99 470-101 390 MHz; 1 875.00 MHz bandwidth each; ~1.6 km/s spectral resolution  
  > "The frequency ranges of SPW 7 and SPW 8 are 97 536 to 99 442 MHz and 99 470 to 101 390 MHz, respectively" (2 Data); "SPWs 7 and 8 have a large bandwidth of 1 875.00 MHz and a spectral resolution of $\sim$1.6 km s$^{-1}$." (2 Data)
- continuum bandwidth: _not stated_
- arrays: ACA and 12-m array observed; this work uses 12-m array data  
  > "Observations were conducted using both the Atacama Compact 7-meter Array (ACA) and the 12-meter array (C43-2 or C43-3 configurations) from September to mid-November 2019." (2 Data); "This work utilizes the 3 mm continuum data and the two wide-band line data cubes (SPWs 7 and 8) obtained from the 12-meter array" (2 Data)
- configurations: 12-m: C43-2 or C43-3  
  > "the 12-meter array (C43-2 or C43-3 configurations)" (2 Data)
- baselines: _not stated_
- angular resolution: ~1.2'' to 1.9'' across the 146 clumps  
  > "which have angular resolutions ranging from approximately 1.2$''$ to 1.9$''$" (2 Data)
- max recoverable scale: 14.5'' to 20.3''  
  > "with the maximum recoverable angular scale ranging from 14.5$''$ to 20.3$''$ across the 146 clumps." (2 Data)
- sensitivity: mean 1 sigma below 10 mJy/beam per channel (line); 0.4 mJy/beam (continuum)  
  > "The mean 1 $\sigma$ noise level is below 10 mJy beam$^{-1}$ per channel for line data and 0.4 mJy beam$^{-1}$ for the continuum." (2 Data)
- time on source: _not stated_
- observing dates: September to mid-November 2019  
  > "from September to mid-November 2019." (2 Data)
- pi or archival as stated: ALMA-ATOMS project, PI Tie Liu  
  > "the ALMA-ATOMS project (ALMA ID: 2019.1.00685.S; PI: Tie Liu)" (2 Data)
- Line: CH3OH multiple unblended transitions (CH3OH 2(1)-2(1) at 97582.898 MHz excluded) (several, 97.5-100.7 GHz; listed in Table 1)
- Line: CH3OCHO multiple unblended transitions (several, listed in Table 1)
- Line: C2H5CN multiple unblended transitions (several, listed in Table 1)
- Line: C2H5OH multiple unblended transitions (several, listed in Table 1)
- Line: CH3OCH3 multiple unblended transitions (several, listed in Table 1)
- Line: CH3COCH3 multiple unblended transitions (several, listed in Table 1)
- Line: CH3CHO multiple unblended transitions (several, listed in Table 1)
- Line: SiO 2-1 (not stated)
- Other facility **JPL molecular spectroscopy database**: Molecular line rest frequencies and line information accessed through XCLASS  
  > "All necessary molecular line information from the Jet Propulsion Laboratory" (3.1.2 Transitions and weights for stacking)
- External data: Strong sample of 60 hot cores previously identified in ATOMS  
  > "60 of which are identical to the strong sample previously identified by (cite: 2022MNRAS.511.3463Q)" (3.2.1 Identification) [from Qin et al. 2022 (cite: 2022MNRAS.511.3463Q)]
- External data: LTE-fitted column densities of the 60 strong hot cores, used for comparison with stacking results  
  > "with those derived by (cite: 2022MNRAS.511.3463Q) through LTE fitting for the 60 strong hot cores." (3.2.3 Column density) [from Qin et al. 2022 (cite: 2022MNRAS.511.3463Q)]
- External data: Source distances  
  > "The distances from the Sun are compiled in (cite: 2020MNRAS.496.2790L)." (Additional tables (Table notes)) [from Liu et al. 2020b (cite: 2020MNRAS.496.2790L)]
- External data: Typical COM line width of ~5 km/s (FWHM) in strong hot cores, used to set the integration range  
  > "for the strong sample of hot cores is approximately 5 km s$^{-1}$ (cite: 2020MNRAS.496.2790L)" (3.1.5 Integrated intensity maps of stacked cubes) [from Liu et al. 2020b (cite: 2020MNRAS.496.2790L)]
- External data: Molecular line spectroscopic data (rest frequencies etc.)  
  > "All necessary molecular line information from the Jet Propulsion Laboratory" (3.1.2 Transitions and weights for stacking) [from Pickett et al. 1998 (cite: 1998JQSRT..60..883P)]
- External data: Previously identified molecular species in G9.62+0.19, used to label the source-stacked template spectrum  
  > "We fit the template spectrum with the emissions of species already identified from G9.62+0.19" (5.1 Source-stacking spectrum of hot-cores) [from Liu et al. 2020b (cite: 2020MNRAS.496.2790L); Peng et al. 2022 (cite: 2022MNRAS.512.4419P)]
- Simulation/model as data: Noise-free XCLASS LTE model spectrum of G9.62+0.19 (standard spectrum) used for weights and column density calibration  
  > "A noise-free standard spectrum then modeled using XCLASS, adopting the fitted parameters" (3.1.1 Standard spectrum of G9.62+0.19)

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
- final beam: angular resolution ~1.2'' to 1.9''  
  > "which have angular resolutions ranging from approximately 1.2$''$ to 1.9$''$" (2 Data)
- final rms: mean 1 sigma below 10 mJy/beam per channel (line); 0.4 mJy/beam (continuum)  
  > "The mean 1 $\sigma$ noise level is below 10 mJy beam$^{-1}$ per channel for line data and 0.4 mJy beam$^{-1}$ for the continuum." (2 Data)

### Inherited from earlier work

- ALMA observations and data reduction  
  > "Details of ALMA observations and data reduction can be found in (cite: 2020MNRAS.496.2821L; 2020MNRAS.496.2790L)." (2 Data) [from (cite: 2020MNRAS.496.2821L; 2020MNRAS.496.2790L)]
- XCLASS LTE fitting of G9.62+0.19 hot core spectra  
  > "following (cite: 2022MNRAS.512.4419P), assuming local thermodynamic equilibrium (LTE)" (3.1.1 Standard spectrum of G9.62+0.19) [from (cite: 2022MNRAS.512.4419P)]
- Stacking procedure (rest frequency correction, coordinate axis reconstruction, reweighting, normalization)  
  > "This technique is implemented by correcting for the rest frequency, reconstructing the coordinate axis, and applying reweighting and normalization before stacking (cite: 2022ApJS..263...13L; 2024ApJS..271....3L)." (3.1 Spectral line stacking) [from (cite: 2022ApJS..263...13L; 2024ApJS..271....3L)]
- Weighting scheme giving highest S/N in the stacked cube  
  > "this set of weights could achieve the highest S/N for the stacked cube (cite: 2022ApJS..263...13L)" (3.1.4 Spectral stacking and normalization) [from (cite: 2022ApJS..263...13L)]

### Not stated but needed to reproduce (our reading)

- Source systemic velocities V_LSR used for each of the 146 clumps (value and origin)
- Calibration/imaging recipe and exact data products (pipeline vs manual, CASA version, continuum subtraction, line-free channels, robust weighting, cell size, taper, primary beam correction) are deferred to ATOMS papers
- Whether cubes were convolved to a common beam before stacking transitions at different frequencies, and the interpolation scheme used in the 1.25 km/s resampling
- Noise definition for the visual >~5 sigma CH3OH criterion (which rms, which map) and how 'compact' was judged for each source
- XCLASS version, fitting algorithm, priors, and fit uncertainties for the G9.62+0.19 standard spectrum (only best-fit values are tabulated)
- CASA version and imfit settings (region, initial guesses, fixed parameters) for the 2D Gaussian fits
- Type of correlation coefficient and fitting method for the column-density pair correlations and for CH3CHO vs SiO/H13CO+ maps; how 'as extended as' was decided; image matching for these comparisons
- Uncertainty propagation for stacking-derived column densities
- Zenodo location of the supplementary data is not given

## Analysis recipe

1. **Build standard hot core spectrum of G9.62+0.19 with XCLASS**: Extract peak spectra of G9.62+0.19 cores C1-C3 with CASA, fit with XCLASS assuming LTE, adopt fitted parameters as standard for each species, and model a noise-free standard spectrum  
  > "Their peak spectra are extracted using CASA (cite: 2007ASPC..376..127M; 2022PASP..134k4501C)" (3.1.1 Standard spectrum of G9.62+0.19); "following (cite: 2022MNRAS.512.4419P), assuming local thermodynamic equilibrium (LTE)" (3.1.1 Standard spectrum of G9.62+0.19)
   - software: CASA, XCLASS
   - parameter: Standard parameters from C1 for CH3OH, CH3OCHO, C2H5OH, CH3OCH3, CH3CHO; text says CH3COCH3 and C2H5OH from C2 and C3 respectively  
  > "the fitted parameters from C1 are adopted as the standard parameters." (3.1.1 Standard spectrum of G9.62+0.19); "We adopt the parameters of CH$_{3}$COCH$_{3}$ and C$_{2}$H$_{5}$OH from the fits of C2 and C3, respectively." (3.1.1 Standard spectrum of G9.62+0.19)
   - parameter: Table 1 standard values (source size '', Tk K, N x1e15 cm-2, dV km/s): CH3OH 1.6/100/200/5; CH3OCHO 1.2/123/32/5; C2H5CN 1.4/140/1.2/4.5 (C3); C2H5OH 1.6/100/9/4; CH3OCH3 1.6/95/30/4; CH3CHO 1.6/100/3.8/5; CH3COCH3 1.4/140/20/5 (C2)  
  > "For each species, the XCLASS fitting parameters, including source size, rotational temperature, column density, line width, as well as the core from which the spectrum is extracted, are listed in Table" (3.1.1 Standard spectrum of G9.62+0.19)
   - assumption: LTE valid because hot core densities exceed the ~1e6 cm-3 critical density  
  > "The size of a hot core is very compact, with number densities generally above this threshold; therefore, the LTE assumption is valid" (3.1.1 Standard spectrum of G9.62+0.19)
   - assumption: Adopted transitions are optically thin in the standard spectrum and assumed so in other hot cores  
  > "it is therefore natural to assume the same for other hot cores, especially those with weak COM emission" (3.1.1 Standard spectrum of G9.62+0.19)
   - assumption: In the optically thin limit, beam dilution scales column density and intensity equally so their ratio is unchanged  
  > "Note that, in the optically thin limit, both the column density and spectral intensity will be modified by the same beam dilution factor, and their ratio will remain unchanged." (3.1.1 Standard spectrum of G9.62+0.19)
   - fitting: XCLASS LTE fit; algorithm, priors and likelihood not stated  
  > "following (cite: 2022MNRAS.512.4419P), assuming local thermodynamic equilibrium (LTE)" (3.1.1 Standard spectrum of G9.62+0.19)
   - validation: _not stated_
2. **Select unblended transitions and derive stacking weights**: Keep transitions detected in G9.62+0.19 hot cores and unblended with other molecules; weight each by its peak brightness temperature on the XCLASS noise-free model spectrum  
  > "(2) unblended with transitions of any other molecular lines." (3.1.2 Transitions and weights for stacking); "The peak brightness temperatures of these transitions on the XCLASS-fitted noise-free spectra of G9.62+0.19 are adopted as the weights for line stacking in following analysis." (3.1.2 Transitions and weights for stacking)
   - software: XCLASS
   - parameter: Flux-to-brightness-temperature conversion T = 1.222e3 I/(nu^2 theta_maj theta_min), I in mJy/beam, nu in GHz, beam axes in arcsec  
  > "In XCLASS, the conversion between the brightness temperature (in K) and the flux intensity of a line is conducted using the following equation:" (3.1.2 Transitions and weights for stacking)
   - parameter: CH3OH 2(1)-2(1) at 97582.898 MHz excluded from stacking  
  > "It has a low $E_{\rm u}$ of 20 K, which makes its emission typically optically thick and extensively distributed in high-mass star-forming regions." (3.1.2 Transitions and weights for stacking)
   - parameter: Weights tabulated in Table 1  
  > "The weights are also listed in Table" (3.1.2 Transitions and weights for stacking)
   - fitting: _not stated_
   - validation: _not stated_
3. **Cut out and resample line cubes to a common velocity grid**: For each source and transition, cut a ~60 km/s cube centred on the rest frequency shifted by V_LSR, convert frequency to velocity, and resample to 1.25 km/s channels  
  > "For each ATOMS source, we cut out a spectral cube with a bandwidth of $\sim60$ km s$^{-1}$ for each transition selected above." (3.1.3 Resampling); "To align the velocity channels, we further resample the cut cube of each transition to a velocity resolution of 1.25 km s$^{-1}$." (3.1.3 Resampling)
   - parameter: Cube bandwidth ~60 km/s; velocity resolution 1.25 km/s; central frequency nu_c = nu_0 (1 - V_LSR/c)  
  > "where $V_{\rm LSR}$ is the systematic velocity of the source" (3.1.3 Resampling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Weighted stacking of transitions per species per source**: Average the resampled cubes of all transitions of a species with weights W_k: D = sum(W_k D_k)/sum(W_k)  
  > "is obtained by averaging the resampled cubes" (3.1.4 Spectral stacking and normalization)
   - parameter: Weights W_k from Table 1 (peak Tb of XCLASS model)  
  > "this set of weights could achieve the highest S/N for the stacked cube (cite: 2022ApJS..263...13L)" (3.1.4 Spectral stacking and normalization)
   - assumption: Optimal weighting assumes transition intensities proportional to the template and equal noise  
  > "if the intensities of the different transitions of the same species are proportional to those of the template spectra" (3.1.4 Spectral stacking and normalization)
   - fitting: _not stated_
   - validation: _not stated_
5. **Make moment 0 maps of the stacked cubes**: Integrate the stacked cubes over +/-5 km/s  
  > "After stacking, we integrated the emission for the stacked lines within a velocity range of $\pm 5$ km s$^{-1}$." (3.1.5 Integrated intensity maps of stacked cubes)
   - parameter: Integration range +/-5 km/s, chosen to match typical COM FWHM of ~5 km/s in strong hot cores  
  > "We chose this value because the typical COM line width, measured as the full width at half maximum (FWHM), for the strong sample of hot cores is approximately 5 km s$^{-1}$" (3.1.5 Integrated intensity maps of stacked cubes)
   - fitting: _not stated_
   - validation: Checked that the range covers most of the G9.62+0.19 stacked emission while avoiding blending  
  > "the adopted velocity range for integration covers the majority of the emission in the stacked spectra of G9.62+0.19 while avoiding blending." (3.1.5 Integrated intensity maps of stacked cubes)
6. **Identify hot core candidates from moment 0 maps**: Visual identification of strong (>~5 sigma), compact CH3OH emission; cores also need at least one other COM  
  > "An HMC candidate is visually identified by the presence of strong ($\gtrsim 5\sigma$), compact CH$_3$OH emission." (3.2.1 Identification); "We classify cores with dense emission of CH$_3$OH and at least one molecule from the other six molecules as hot core candidates." (abstract)
   - parameter: Compact = round morphology with central brightest part unresolved or partly resolved  
  > "a compact core is defined as one with a round morphology, where its central brightest part is not resolved or is only partly resolved under the current spatial resolution" (3.2.1 Identification)
   - fitting: _not stated_
   - validation: 60 of the 100 candidates coincide with the previously identified strong sample  
  > "60 of which are identical to the strong sample previously identified by (cite: 2022MNRAS.511.3463Q)" (3.2.1 Identification)
7. **Measure core sizes and peak fluxes with 2D Gaussian fits**: 2D Gaussian fit of the CH3OH moment 0 map of each of the 100 cores with CASA imfit; same procedure for the other six species  
  > "Two-dimensional Gaussian fitting is applied to the 100 cores on the Moment 0 maps of CH$_3$OH using the CASA" (3.2.2 Two-dimensional Gaussian fitting); "The same fitting procedure was applied for the other six COM species (if detected)." (3.2.2 Two-dimensional Gaussian fitting)
   - software: CASA
   - parameter: Beam-deconvolved size, position angle, peak and integrated flux adopted; theta_source = sqrt(ab) from deconvolved FWHM axes  
  > "The beam-deconvolved fitting parameters are adopted, including the source size" (3.2.2 Two-dimensional Gaussian fitting); "$\theta_{\rm source}=\sqrt{ab}$, where $a$ and $b$ represent the deconvolved major and minor FWHM axes of the cores" (3.2.2 Two-dimensional Gaussian fitting)
   - fitting: Gaussian least-squares via imfit; details not stated  
  > "Two-dimensional Gaussian fitting is applied to the 100 cores on the Moment 0 maps of CH$_3$OH using the CASA" (3.2.2 Two-dimensional Gaussian fitting)
   - validation: CH3CHO fits flagged as less reliable where extended emission is present  
  > "the emission of CH$_3$CHO displays extended components, making the fitting of CH$_3$CHO less reliable." (3.2.2 Two-dimensional Gaussian fitting)
8. **Derive column densities by scaling to the G9.62+0.19 standard**: N = (N_cali / I_cali) I, with I_cali the integrated (+/-5 km/s) stacked intensity of the standard spectrum and N_cali the XCLASS column density of G9.62+0.19; applied to moment maps and beam-deconvolved peak values  
  > "G9.62+0.19 is adopted as the calibration source to estimate the column densities of hot core candidates from their stacked emission." (3.2.3 Column density); "To evaluate the column density of each species, we use the following conversion formula:" (3.2.3 Column density); "enabling us to directly calculate the beam-deconvolved peak column density" (3.2.3 Column density)
   - parameter: N_cali values are the Table 1 column densities of the G9.62+0.19 core used for each species  
  > "is adopted as the standard column density (denoted as $N_{\rm cali}$) for the corresponding species." (3.2.3 Column density)
   - assumption: Same excitation conditions and optically thin emission as G9.62+0.19 for all candidates  
  > "the good agreement between the XCLASS fitting and the stacking conversion suggests comparable excitation conditions for different hot core candidates." (3.2.3 Column density)
   - fitting: _not stated_
   - validation: Compared with LTE-fit column densities of Qin et al. 2022 for the 60 strong cores; generally in good agreement  
  > "The results are generally in good agreement, supporting the reliability of column densities estimated through stacking." (3.2.3 Column density)
9. **Source-stack spectra of all 100 hot cores into a template spectrum**: Extract full-band SPW 7 and 8 spectra at the stacked CH3OH peak of each core, correct the frequency axis for V_LSR, resample to 0.49 MHz channels, average with equal weights, and fit with XCLASS  
  > "For each of the 100 hot core candidates, we extract the full-band spectra of SPW 7 and SPW 8 at the peak location of CH$_3$OH (after stacking)." (5.1 Source-stacking spectrum of hot-cores); "A source-stacking template spectrum is obtained by averaging these spectra with equal weighting." (5.1 Source-stacking spectrum of hot-cores)
   - software: XCLASS
   - parameter: Channel width 0.49 MHz  
  > "We then resample the spectra to have aligned channels with a channel width of 0.49 MHz." (5.1 Source-stacking spectrum of hot-cores)
   - fitting: XCLASS fit with species already identified in G9.62+0.19; details not stated  
  > "We fit the template spectrum with the emissions of species already identified from G9.62+0.19" (5.1 Source-stacking spectrum of hot-cores)
   - validation: _not stated_
10. **Correlate column densities between COM species**: Plot column densities of molecular pairs for strong and weak cores and compute correlation coefficients  
  > "show the correlations between the column densities of molecular pairs for the seven molecules, including both the strong hot cores and the weak candidates." (5.2 Correlations of complex molecules)
   - fitting: _not stated_
   - validation: Weak candidates lie at the low end of the linear trend defined by the whole sample, supporting the stacking-based column densities  
  > "This supports the validity of estimating column density through stacking" (5.2 Correlations of complex molecules)
11. **Compare CH3CHO distribution with SiO and H13CO+**: Compare moment 0 maps of stacked CH3CHO with SiO (2-1) and H13CO+ (1-0) and compute correlations of the integrated intensity maps for 43 sources where CH3CHO is as extended  
  > "We compare the integrated intensity maps of the stacked cube of CH$_3$CHO with those of SiO (2-1)" (5.3 Spatial distributions of complex molecular line emission); "To quantify this, we calculate the correlation between the integrated intensity maps of CH$_3$CHO, SiO" (5.3 Spatial distributions of complex molecular line emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Extracting peak spectra of G9.62+0.19 and 2D Gaussian fitting (imfit) of moment 0 maps  
  > "Their peak spectra are extracted using CASA (cite: 2007ASPC..376..127M; 2022PASP..134k4501C)" (3.1.1 Standard spectrum of G9.62+0.19); "Two-dimensional Gaussian fitting is applied to the 100 cores on the Moment 0 maps of CH$_3$OH using the CASA" (3.2.2 Two-dimensional Gaussian fitting)
- **XCLASS** : LTE fitting of G9.62+0.19 spectra, noise-free standard model, and fit of the source-stacked template spectrum  
  > "A noise-free standard spectrum then modeled using XCLASS, adopting the fitted parameters" (3.1.1 Standard spectrum of G9.62+0.19); "We fit the template spectrum with the emissions of species already identified from G9.62+0.19" (5.1 Source-stacking spectrum of hot-cores)
- **JPL molecular database** : Molecular line information accessed through XCLASS  
  > "All necessary molecular line information from the Jet Propulsion Laboratory" (3.1.2 Transitions and weights for stacking)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total hot core candidates (strong + new weak) | 100 (60 strong + 40 new weak) | not stated | dimensionless | 6 | In total, we identified 100 HMC candidates, 60 of which are identical to the strong sample previously identified by (cite: 2022MNRAS.511.3463Q), and the remaining 40 are weak candidates newly identified in this work. |
| Number of the 100 cores detected in each COM (CH3OH, CH3OCHO, C2H5CN, C2H5OH, CH3OCH3, CH3CHO, CH3COCH3) | 100, 90, 80, 46, 77, 59, 27 | not stated | dimensionless | 6 | In total, 100 hot cores show CH$_3$OH emission, 90 show CH$_3$OCHO emission, 80 show C$_2$H$_5$CN emission, 46 show C$_2$H$_5$OH emission, 77 show CH$_3$OCH$_3$ emission, 59 show CH$_3$CHO emission, and 27 show CH$_3$COCH$_3$ emission. |
| Number of the 40 new candidates with compact emission of CH3OCHO, C2H5CN, C2H5OH, CH3OCH3, CH3CHO, CH3COCH3 | 36, 29, 5, 25, 16, 1 | not stated | dimensionless | 6 | Specifically, 36 show CH$_3$OCHO emission, 29 display C$_2$H$_5$CN emission, 5 reveal C$_2$H$_5$OH emission, 25 demonstrate CH$_3$OCH$_3$ emission, 16 present CH$_3$CHO emission, and only one core shows CH$_3$COCH$_3$ emission. |
| CH3OH emission size range | 1092 to 46884 | not stated | AU | 7 | The sizes of molecular CH$_3$OH emission range from 1092 to 46884 AU for sources at different distances. |
| Deconvolved emission sizes: six COMs (excluding CH3CHO) / CH3CHO | 940 to 57 306 / 4 033 to 91 884 | not stated | AU | 7 | range from approximately 940 to 57 306 AU, while the deconvolved sizes for CH$_3$CHO range from 4 033 to 91 884 AU. |
| CH3OH column density range | 1.4e18 to 4.4e20 | not stated | cm^-2 | 8 | CH$_{3}$OH stands out with the highest column densities, ranging from 1.4$\times$10$^{18}$ to 4.4$\times$10$^{20}$ cm$^{-2}$. |
| CH3OCHO and CH3OCH3 column density ranges | 5.3e17 to 2.8e20 and 1.0e18 to 1.4e20 | not stated | cm^-2 | 8 | from 5.3$\times$10$^{17}$ to 2.8$\times$10$^{20}$ cm$^{-2}$ and from 1.0$\times$10$^{18}$ to 1.4$\times$10$^{20}$ cm$^{-2}$, respectively. |
| C2H5OH, CH3CHO and CH3COCH3 column density range | 1.3e17 to 5.9e19 | not stated | cm^-2 | 8 | ranging from 1.3$\times$10$^{17}$ to 5.9$\times$10$^{19}$ cm$^{-2}$. |
| C2H5CN column density range | 1.6e15 to 7.1e18 | not stated | cm^-2 | 8 | spans a range from 1.6$\times$10$^{15}$ to 7.1$\times$10$^{18}$ cm$^{-2}$ |
| Column density of weak candidates relative to strong sample | approximately one order of magnitude lower | not stated | dimensionless | 8 | These weak candidates exhibit column densities of COMs that are approximately one order of magnitude lower than those of the strong sample. |
| Correlation coefficients CH3OH-CH3OCHO, CH3OCHO-C2H5CN, CH3OCHO-CH3OCH3 | 0.89, 0.88, 0.94 | not stated | dimensionless | 10 | Their correlation coefficients are 0.89, 0.88, and 0.94, respectively. |
| Correlation coefficient C2H5OH-CH3OCHO | 0.86 | not stated | dimensionless | 10 | also exhibits a strong correlation (0.86) with CH$_3$OCHO |
| Correlation coefficient C2H5CN-CH3OCH3 | 0.86 | not stated | dimensionless | 10 | also shows a strong overall correlation with CH$_{3}$OCH$_{3}$, with a correlation coefficient of 0.86. |
| Number of sources where CH3CHO is extended like SiO and H13CO+ | 43 of 100 | not stated | dimensionless | 11 | Among the 100 hot cores in total, 43 exhibit extended CH$_3$CHO emission spatially correlated with SiO |
| Correlation of CH3CHO with H13CO+ maps in those 43 sources | exceeding 0.8 | not stated | dimensionless | 11 | with correlation coefficients exceeding 0.8. |

## Qualitative findings

- All hot core candidates show compact emission from at least one of the six COMs other than CH3OH  
  > "All hot core candidates display compact emission from at least one of the other six COM species." (abstract)
- For the weak candidates all species except CH3CHO are compact in the stacked image but not fully resolved spatially  
  > "all species except CH$_3$CHO show compact emission in the stacked image, which cannot be fully resolved spatially." (abstract)
- Stacking is faster and more sensitive than line fitting for finding weak hot cores  
  > "it is faster and more convenient, and allows for greater sensitivity to detect weaker hot cores." (abstract)

## Claim tuples

- H: Molecular line stacking can find weak hot cores missed by line-fitting selection in the ATOMS sample | E: Stack unblended transitions of seven COMs, make moment 0 maps and identify compact CH3OH cores | R: 100 candidates, 60 known strong and 40 new weak | F: 40 new hot core candidates identified | **supported**
- H: Stacking-based scaling gives reliable column densities | E: Scale G9.62+0.19 XCLASS column densities by stacked integrated intensity and compare with LTE fits of the 60 strong cores | R: Generally good agreement, with some discrepancy attributed to excitation and spatial differences | F: Stacking column densities consistent with previous fitting results | **supported**
- H: Weak candidates differ from strong hot cores in COM abundance | E: Compare stacked column densities across the sample | R: Weak candidates have COM column densities about an order of magnitude lower and lie at the low end of the correlation trends | F: Weak candidates are a lower-column-density extension of the hot core population | **supported**
- H: CH3OH is a precursor of other COMs and COMs share chemical environment | E: Correlate column densities between COM pairs across 100 cores | R: Strong correlations (0.89 CH3OH-CH3OCHO, 0.94 CH3OCHO-CH3OCH3, 0.88 CH3OCHO-C2H5CN) | F: COMs may share a similar chemical environment with CH3OH potentially a precursor | **partially**
- H: CH3CHO traces shocks rather than compact hot core gas | E: Compare stacked CH3CHO moment 0 maps with SiO and H13CO+ maps in 100 cores | R: 43 cores show extended CH3CHO correlated with H13CO+ (>0.8) and, in 8 sources, SiO (>0.8) | F: CH3CHO may form in widely distributed shock regions | **partially**

## Reasoning

- Why this data: ATOMS Band 3 survey provides an excellent dataset covering 146 massive clumps  
  > "providing an excellent dataset for identifying hot cores." (1 Introduction)
- Why this method: Stacking is faster and more sensitive than line fitting; species chosen because each has multiple transitions in the ATOMS band  
  > "Compared to spectral line fitting methods, it is faster and more convenient, and allows for greater sensitivity to detect weaker hot cores." (abstract); "These species were selected for spectral stacking because they all have multiple transitions covered by the ATOMS survey, ensuring a robust dataset for analysis." (1 Introduction)
- Alternative: CH3OH 2(1)-2(1) line excluded from stacking because it is typically optically thick and extended  
  > "It has a low $E_{\rm u}$ of 20 K, which makes its emission typically optically thick and extensively distributed in high-mass star-forming regions." (3.1.2 Transitions and weights for stacking)
- How they decided it was enough: _not stated_
- Limitation (authors): Weak candidates cannot be fully resolved spatially  
  > "which cannot be fully resolved spatially." (abstract)
- Limitation (authors): Unresolved optically thick regions may contribute to discrepancy with LTE-fit column densities  
  > "unresolved optically thick regions, which cannot be distinguished at the current resolution, may also contribute to the discrepancy." (3.2.3 Column density)
- Limitation (authors): Details of G9.62+0.19 hot cores unclear, so similarity of candidates' emitting regions and excitation to the template cannot be confirmed  
  > "we cannot confirm whether different hot core candidates exhibit similar distributions of emitting regions and excitation conditions." (3.2.3 Column density)
- Limitation (authors): CH3CHO Gaussian fits less reliable where extended emission is present  
  > "making the fitting of CH$_3$CHO less reliable." (3.2.2 Two-dimensional Gaussian fitting)
- Limitation (authors): Nitrogen versus oxygen differentiation remains uncertain because of limited angular resolution  
  > "remains uncertain due to the limited angular resolution in our observations" (5.2 Correlations of complex molecules)
- Caveat (inferred, ours): All column densities are scaled from one template core (G9.62+0.19), so they inherit its Tk, source size and optical-depth assumptions; no excitation temperature is derived per source
- Caveat (inferred, ours): Pair correlations between species may be partly built in because every N is proportional to a stacked intensity calibrated on the same template
- Caveat (inferred, ours): Candidate selection is visual (>~5 sigma, round morphology) with no stated completeness or false-positive test for the 40 weak cores
- Caveat (inferred, ours): Text says C2H5OH parameters come from C3 and CH3COCH3 from C2, while Table 1 labels C2H5OH as C1 and C2H5CN as C3
- Caveat (inferred, ours): No uncertainty budget for stacking-derived column densities or for the standard-spectrum fit
- Caveat (inferred, ours): Beam differences across frequencies in stacking and between SiO/H13CO+/CH3CHO maps are not discussed
- Caveat (inferred, ours): Correlation coefficient type and the 'as extended as' criterion for CH3CHO are not defined

## Reproducibility

- Data public (paper): Only derived data stated as available (article and Zenodo supplement); public status of ALMA raw data not stated  
  > "The derived data underlying this article are available in thearticle and in its online supplementary material on Zenodo." (Data Availability)
- Products in archive: _not stated_
- Missing: V_LSR per source
- Missing: Calibration and imaging settings (deferred to ATOMS papers) or the exact data products used
- Missing: XCLASS fit details and uncertainties for the template
- Missing: imfit settings and region choices
- Missing: Objective criteria for compact and extended classifications
- Missing: Correlation method details
- Missing: Software versions
- Missing: No analysis code released
- Data volume (inferred): Hundreds of GB to ~1 TB if calibrated 12-m SPW 7 and 8 cubes for 146 clumps are rebuilt from the archive; far less if only released products are used
- Score (inferred): 3/5, ALMA project code is given and the stacking recipe, weights and standard parameters are tabulated with numeric results, but calibration, imaging, V_LSR and selection details are deferred or missing and no code is released.
- Rediscovery candidate: yes, ALMA data are from a named project and the recipe (template, weights, resample, stack, moment 0, imfit, scaling) is largely complete with numeric tables, though visual selection and V_LSR are underspecified.

## Links

- Method: Liu et al. 2020a (cite: 2020MNRAS.496.2821L) (ATOMS observations and data reduction)
- Method: Liu et al. 2020b (cite: 2020MNRAS.496.2790L) (ATOMS survey overview, distances, previous hot core line identification)
- Method: Liu et al. 2022 (cite: 2022ApJS..263...13L) (Spectral stacking method and weights)
- Method: Liu et al. 2024a (cite: 2024ApJS..271....3L) (Stacking technique)
- Method: Peng et al. 2022 (cite: 2022MNRAS.512.4419P) (XCLASS LTE fitting of G9.62+0.19)
- Method: Moller et al. 2017 (cite: 2017A&A...598A...7M) (XCLASS software)
- Companion: Qin et al. 2022 (cite: 2022MNRAS.511.3463Q) (Catalog of 60 strong ATOMS hot cores with LTE-fit column densities used for comparison)
- Companion: Liu et al. 2024b (cite: 2024RAA....24b5009L) (ALMA-QUARKS Band 6 follow-up survey)
- Related: ALMA-ATOMS
- Related: ALMA-QUARKS
- Related: CoCCoa
- Related: DIHCA
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 128,
 "quotes_ok": 128,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 120,
  "stated": 78,
  "rate": 0.65
 },
 "evidence_ok": true
}
```
