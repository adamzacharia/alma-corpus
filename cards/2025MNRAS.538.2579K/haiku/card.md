# ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions - XXI. A large-sample observational study of ethanol and dimethyl ether in hot cores

`2025MNRAS.538.2579K` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Kou, Zhiping | arXiv: 2503.07126 | DOI: 10.1093/mnras/staf408

Card schema 1.0 | model claude-haiku-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Are ethanol (EA) and dimethyl ether (DE) chemically linked to their possible precursor CH3OH across a large sample of 60 hot cores, and do chemical models reproduce their abundances?  
  > "We present a deep line survey of two isomers of" (abstract); "Compared with chemical models, the three different warm-up timescale models result in the systematic overproduction of EA and the systematic underproduction of DE." (abstract)
- Target **ATOMS hot-core sample (60 hot cores)**: coordinates not stated in text (per-source positions are in the observations table)  
  > "resulting in the identification of a total of 60 hot cores, with 45 being newly detected" (Hot core sample); "distances from the Sun" (Hot core sample); z/distance not stated per source; sample spans distances from the Sun of about 1-12 kpc as stated  
  > "resulting in the identification of a total of 60 hot cores, with 45 being newly detected" (Hot core sample); "distances from the Sun" (Hot core sample); distance from see Table A1 in (cite: 2020MNRAS.496.2790LiuT)  
  > "resulting in the identification of a total of 60 hot cores, with 45 being newly detected" (Hot core sample); "distances from the Sun" (Hot core sample)

## Data provenance

- ALMA projects: 2019.1.00685.S
- bands: ALMA Band 3 (3 mm)  
  > "The observations were carried out with ALMA band 3 towards 146 Infrared Astronomical Satellite (IRAS) clumps" (Observations)
- frequencies and spectral setup: Eight spectral windows; SPWs 1-6 high resolution (58.59 MHz each); SPWs 7-8 broad, covering 97536-99442 MHz and 99470-101390 MHz  
  > "Eight spectral windows (SPWs) were configured" (Observations); "The frequency ranges of SPWs 7 and 8 are 97536-99442 MHz and 99470-101390 MHz respectively." (Observations)
- continuum bandwidth: SPWs 7-8, 1875 MHz each, spectral resolution about 1.6 km/s  
  > "2 broad bandwidth windows (SPWs 7-8, bandwidth 1875 MHz with spectral resolution" (Observations)
- arrays: ACA 7-m and 12-m array; only 12-m data used in this study  
  > "Atacama Compact 7-m Array (ACA) and 12-m array (C43-2 or C43-3 configurations) observations were conducted" (Observations); "In this study, we only employ 12 m array data as hot cores typically have smaller source sizes" (Observations)
- configurations: C43-2 or C43-3 (12-m array)  
  > "12-m array (C43-2 or C43-3 configurations)" (Observations)
- baselines: _not stated_
- angular resolution: about 1.2 to 1.9 arcsec (12-m array)  
  > "The angular resolution and maximum recovered angular scale for the 12-m array observations are" (Observations)
- max recoverable scale: about 14.5 to 20.3 arcsec (12-m array)  
  > "The angular resolution and maximum recovered angular scale for the 12-m array observations are" (Observations)
- sensitivity: mean 1 sigma rms better than 10 mJy/beam per channel for spectral lines (SPWs 7 and 8)  
  > "are better than 10 mJy beam" (Observations)
- time on source: typical on-source times of 3 minutes (12-m array) and 8 minutes per source (ACA 7-m)  
  > "typical on-source times of 3 minutes for 12-m array and 8 minutes per source for ACA 7-m array" (Observations)
- observing dates: late September to mid-November 2019  
  > "from late September to mid-November 2019" (Observations)
- pi or archival as stated: PI Tie Liu; data first presented by Liu et al. 2020 (two papers)  
  > "The data were first presented by (cite: 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT)" (Observations)
- Line: C2H5OH (ethanol, EA) not stated for this line (moment 0 map line) (100990 MHz)
- Line: CH3OCH3 (dimethyl ether, DE) not stated for this line (moment 0 map line) (99324 MHz)
- Line: H40alpha recombination line H40alpha (99022.952 MHz)
- External data: CH3OH column densities of the sample taken from a previous ATOMS paper  
  > "we take the column densities of methanol in our sample from" (Comparison with other sources and parameter correlations) [from (cite: 2022MNRAS.511.3463Qin)]
- External data: EA, DE and CH3OH column densities and rotation temperatures of hot cores and hot corinos from the literature, compiled in Table A.4 (28 sources used)  
  > "gather data from other hot cores and hot corinos reported in the literature, where interferometric observations are conducted with reliable source sizes estimated" (Comparison with other sources and parameter correlations) [from literature compilation in Table A.4; individual citations not given in the text]
- External data: Hot-core luminosities and distances for the sample  
  > "see Table A1 in (cite: 2020MNRAS.496.2790LiuT)" (Hot core sample) [from (cite: 2020MNRAS.496.2790LiuT)]
- External data: Hydrogen column densities for each source  
  > "The hydrogen column densities were obtained from" (Results and Statistical Analysis) [from (cite: 2025A&A...694A.166C)]
- External data: Spectroscopic line data from CDMS and JPL databases  
  > "Cologne Database for Molecular Spectroscopy (CDMS" (Line identification) [from (cite: 2005JMoSt.742..215M); (cite: 1998JQSRT..60..883Pickett)]
- External data: Associated Ultra-Compact HII region status of 24 of the 60 hot cores  
  > "Of the 60 hot cores, 24 are associated with Ultra-Compact Hii regions" (Hot core sample) [from (cite: 2022MNRAS.511.3463Qin; 2023MNRAS.520.3245Z)]
- Simulation/model as data: Chemical models of G22 (2022ApJS..259....1G) and three warm-up timescale models used for comparison with observed EA and DE abundances  
  > "Compared with chemical models, the three different warm-up timescale models result in the systematic overproduction of EA and the systematic underproduction of DE." (abstract); "The models of (cite: 2022ApJS..259....1G) have shown that DE is predominantly formed through both the ice and gas phases" (Introduction)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6 is stated for tclean imaging; the calibration software version is not stated  
  > "Visibility data from the ALMA 12-m arrays are cleaned using the CASA 5.6 tclean task." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: not stated in this paper; referred to the earlier papers by Liu et al. 2020  
  > "where more details about the spectral setups, flux and phase calibrators can be found" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Visibility data from the ALMA 12-m arrays are cleaned using the CASA 5.6 tclean task." (Observations)
- deconvolver: multiscale  
  > "and a multiscale deconvolver" (Observations)
- weighting robust: natural weighting (robust value not applicable as stated)  
  > "This was done by applying the natural weighting, setting the gridder with the" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: not applied to the spectra; continuum contribution neglected in line fitting (correction factors 0.99-1.1)  
  > "Thus, we neglect continuum emission and dust attenuation in our spectral line fitting." (Line identification)
- line free channels: continuum images made from line-free channels of SPWs 7-8 centred at 99.4 GHz; channel selection not stated  
  > "SPWs 7-8 were used to create continuum images from the line-free channels centred at 99.4 GHz" (Observations)
- primary beam correction: all images corrected for the primary beam; gridder pblimit parameter 0.2  
  > "All images are corrected for the primary beam." (Observations)
- array combination: 12-m array only; ACA 7-m data not used  
  > "In this study, we only employ 12 m array data as hot cores typically have smaller source sizes" (Observations)
- smoothing: _not stated_
- final beam: about 1.2 to 1.9 arcsec angular resolution (12-m array)  
  > "The angular resolution and maximum recovered angular scale for the 12-m array observations are" (Observations)
- final rms: better than 10 mJy/beam per channel for spectral lines  
  > "are better than 10 mJy beam" (Observations)

### Inherited from earlier work

- Data reduction, spectral setup and flux/phase calibrator details taken from earlier ATOMS papers  
  > "The data were first presented by (cite: 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT), where more details about the spectral setups, flux and phase calibrators can be found." (Observations) [from 2020MNRAS.496.2790LiuT; 2020MNRAS.496.2821LiuT]
- Line identification and calculation procedure for EA and DE  
  > "we use the same procedure to identify and calculate parameters for EA and DE, as described in" (Line identification) [from 2022MNRAS.511.3463Qin]
- Deconvolved continuum source sizes used as molecular source sizes  
  > "we take deconvolved angular sizes of the continuum sources as source sizes" (Line identification) [from 2022MNRAS.511.3463Qin]
- Continuum contribution correction (Eq. 5)  
  > "We have estimated the continuum contribution to the line emission using Eq. (5) from the paper of" (Line identification) [from 2020A&A...635A..48Manigand]
- Dust opacity equation (Eq. 4) for dust optical depth  
  > "To evaluate the dust attenuation, we used the dust opacity equation" (Line identification) [from 2021A&A...651A...9Moller]
- Hydrogen column densities from Tables C1-C4  
  > "The hydrogen column densities were obtained from" (Line identification) [from 2025A&A...694A.166C]
- Local noise calculation method for each window  
  > "The method for calculating the local noise for each window was adopted from" (Additional figures) [from 2021NatAs...5..188Loomis]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline or script, CASA version used for calibration, and flux, bandpass and phase calibrators for each source (only referred to earlier papers).
- Robust weighting value (only natural weighting named) and cell size, image size and mask used for the continuum and line cubes.
- Which channels are line-free for continuum imaging of SPWs 7-8 and whether any continuum subtraction was applied to the spectral cubes.
- Per-source continuum flux and deconvolved source size values used as fixed source sizes in XCLASS (only a reference table is cited).
- Per-source velocity offsets and fixed line-width values used in the MAGIX step.
- MAGIX priors, parameter bounds, MCMC walker and step settings, and convergence criteria.
- Which EA and DE transitions were used for each source and the 3-sigma detection criterion applied to each line.
- Per-source hydrogen column densities taken from the cited H2 column-density paper, needed for the abundance ratios.
- Spectroscopic partition function and the exact XCLASS database version and update used for the line catalogues.
- Source list of the 28 literature sources with their individual column densities and source sizes (Table A.4 citations not given in text).
- Detailed definition of the Pearson correlation sample and any treatment of upper limits or non-detections.

## Analysis recipe

1. **reduce and image the 12-m data**: Calibrated 12-m array data imaged with CASA tclean using natural weighting and a multiscale deconvolver; images primary-beam corrected; continuum made from SPWs 7-8 line-free channels  
  > "This was done by applying the natural weighting, setting the gridder with the" (Observations); "SPWs 7-8 were used to create continuum images from the line-free channels centred at 99.4 GHz" (Observations)
   - software: CASA
   - parameter: natural weighting; gridder pblimit 0.2  
  > "This was done by applying the natural weighting, setting the gridder with the" (Observations)
   - parameter: 12-m array data only  
  > "In this study, we only employ 12 m array data as hot cores typically have smaller source sizes" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **extract spectra for each hot core**: Spectra extracted from an area equal to the beam size, centred on the continuum peak  
  > "The spectra of our sample were extracted from an area corresponding to the size of the beam, centred on the peak of the continuum." (Observations)
   - parameter: aperture equal to beam size, centred on continuum peak  
  > "The spectra of our sample were extracted from an area corresponding to the size of the beam, centred on the peak of the continuum." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **first-pass line identification and LTE fit of EA and DE**: LTE spectral fits with XCLASS; source size fixed from continuum; rotation temperature, column density and line width set free and adjusted manually; velocity offset set against CH3OH line  
  > "Then, three parameters: rotation temperature, column density, and line width are set to be free parameters" (Line identification); "The rotation temperature, column density, and line width were manually adjusted to achieve a reasonable match between the synthetic and observed spectra." (Line identification)
   - software: XCLASS
   - parameter: velocity offsets referenced to CH3OH 13(-2,12)-12(-3,10) E line at 100.6389 GHz  
  > "at 100.6389 GHz" (Line identification)
   - parameter: source sizes from deconvolved continuum sizes  
  > "we take deconvolved angular sizes of the continuum sources as source sizes" (Line identification)
   - assumption: Local thermodynamic equilibrium  
  > "Assuming molecular gas is in local thermodynamic equilibrium (LTE) and solving the radiative transfer equation" (Line identification)
   - assumption: Continuum contribution negligible (correction factors 0.99-1.1); dust optical depth below 0.08  
  > "The correction factors range from 0.99-1.1." (Line identification); "The dust optical depths in our sample are less than 0.08." (Line identification)
   - fitting: manual adjustment to match synthetic and observed spectra  
  > "were manually adjusted to achieve a reasonable match between the synthetic and observed spectra." (Line identification)
   - validation: blending checked by plotting modelled CH3OH, C2H5CN and CH3OCHO spectra from earlier work  
  > "in order to assess the potential blending issue" (Line identification)
4. **optimise rotation temperature and column density**: Second step with line width fixed from step 3; MAGIX optimisation of rotation temperature and column density; errors from LM and MCMC  
  > "In the second step, the line width is set as a fixed parameter based on the first step." (Line identification); "the Levenberg-Marquardt algorithm (LM) and the Markov chain Monte Carlo algorithm (MCMC) are employed to estimate the errors" (Line identification)
   - software: MAGIX, XCLASS
   - parameter: line width fixed from first step  
  > "In the second step, the line width is set as a fixed parameter based on the first step." (Line identification)
   - fitting: Levenberg-Marquardt for optimisation; MCMC for error estimates; priors not stated  
  > "the Levenberg-Marquardt algorithm (LM) and the Markov chain Monte Carlo algorithm (MCMC) are employed to estimate the errors" (Line identification)
   - validation: where MAGIX did not converge, first-step results are reported  
  > "In some sources, the MAGIX calculations do not converge, so we show the results from the first step." (Line identification)
5. **set column density where temperature is unconstrained**: Column densities computed at 100, 150 and 200 K; 150 K adopted as the median value; where only one or two lines are detected the temperature is not constrained  
  > "We calculated the column densities using three different temperatures (100 K, 150 K, and 200 K)" (Line identification); "We chose a median value of 150 K to derive their column densities." (Line identification)
   - parameter: adopted temperature 150 K for column densities  
  > "We chose a median value of 150 K to derive their column densities." (Line identification)
   - assumption: column density varies by less than 20% across 100-200 K  
  > "with the variation remaining within 20%" (Line identification)
   - fitting: _not stated_
   - validation: sensitivity test over three temperatures  
  > "which showed a slight increase in column density, with the variation remaining within 20%." (Line identification)
6. **correlate EA, DE and CH3OH column densities and abundance ratios**: Pearson correlation coefficients between column densities and between rotation temperatures; EA/DE ratio plotted against CH3OH column density; abundances relative to CH3OH compared with literature  
  > "Rotation temperatures between EA and DE show no correlation" (Statistical analysis); "we find strong column density correlations among EA and DE" (abstract)
   - parameter: sample of 39 sources from groups A and B plus 28 literature sources (67 total) for EA/DE ratio analysis  
  > "we include all 39 sources from groups A and B, as well as 28 sources from the literature" (Comparison with other sources and parameter correlations)
   - fitting: Pearson correlation coefficient (no fit)  
  > "Pearson’s co-efficient" (Statistical analysis)
   - validation: _not stated_
7. **compare abundances with chemical models and formation experiments**: Qualitative comparison of observed EA and DE abundance trends against warm-up timescale models and radical-radical recombination experiments  
  > "Experimental studies showed that EA and DE are formed via radical" (Implications for the chemistry of EA and DE); "Compared with chemical models, the three different warm-up timescale models result in the systematic overproduction of EA and the systematic underproduction of DE." (abstract)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: Calibration and imaging of the ALMA 12-m data; tclean imaging with natural weighting and multiscale deconvolution  
  > "The data were calibrated and imaged using the Common Astronomy Software Applications package (CASA; (cite: 2007ASPC..376..127McMullin))." (Observations); "Visibility data from the ALMA 12-m arrays are cleaned using the CASA 5.6 tclean task." (Observations)
- **XCLASS** 1.2.5: LTE identification and fitting of EA and DE lines; updated embedded spectroscopic database with UpdateDatabase task  
  > "We used the XCLASS version 1.2.5 for the line fitting" (Line identification); "We upgraded this database file by using the XCLASS task UpdateDatabase." (Line identification)
- **MAGIX** : Optimisation of rotation temperature and column density with LM and MCMC error estimation  
  > "We then employ the Modeling and Analysis Generic Interface for eXternal numerical codes (MAGIX" (Line identification)
- **CDMS catalogue** : Spectroscopic line data for XCLASS  
  > "Cologne Database for Molecular Spectroscopy (CDMS" (Line identification)
- **JPL molecular database** : Spectroscopic line data for XCLASS  
  > "the Jet Propulsion Laboratory molecular databases (JPL" (Line identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| number of hot cores with EA detected | 40 | not stated | count | 3 | EA is detected in 40 hot cores and DE is detected in 59 hot cores. |
| number of hot cores with DE detected | 59 | not stated | count | 3 | EA is detected in 40 hot cores and DE is detected in 59 hot cores. |
| number of hot cores with EA and DE both detected | 39 | not stated | count | 3 | Of these, EA and DE are simultaneously detected in 39 hot cores. |
| average rotation temperature of EA (25 sources, groups A and B) | 167 | ±14 (as stated) | K | 4 | The rotation temperatures for EA range from 117 to 215 K with an average value of |
| average rotation temperature of DE (25 sources, groups A and B) | 136 | ±12 (as stated) | K | 4 | while the rotation temperatures for DE range from 102 to 197 K with an average value of |
| average rotation temperature of EA (40 hot cores) | 154 | not stated | K | 4 | Rotation temperatures towards 40 hot cores range from 91 to 215 K with an average value of 154 K. |
| average rotation temperature of DE (59 hot cores) | 143 | not stated | K | 4 | Rotation temperatures towards 59 hot cores range from 102 to 197 K, with an average value of 143 K. |
| average column density of EA (25 sources) | 1.9e17 | ±0.1e17 (as stated) | cm^-2 | 5 | The average column densities of EA and DE are at the same order of magnitude. |
| average column density of DE (25 sources) | 4.2e17 | ±0.1e17 (as stated) | cm^-2 | 5 | The average column densities of EA and DE are at the same order of magnitude. |
| column density range of EA (40 hot cores) | 6.5e15 to 1.3e18 | not stated | cm^-2 | 5 | Column densities towards 40 hot cores range from 6.5 |
| column density range of DE (59 hot cores) | 1.2e16 to 2.2e18 | not stated | cm^-2 | 5 | Column densities towards 59 hot cores range from 1.2 |
| Pearson correlation coefficient, column density EA vs DE | 0.92 | not stated | dimensionless | 6 | we find strong column density correlations among EA and DE |
| Pearson correlation coefficient, column density EA vs CH3OH | 0.82 | not stated | dimensionless | 6 | we find strong column density correlations among EA and DE |
| Pearson correlation coefficient, column density DE vs CH3OH | 0.80 | not stated | dimensionless | 6 | we find strong column density correlations among EA and DE |
| Pearson correlation coefficient, rotation temperature EA vs column density EA | 0.4 | not stated | dimensionless | 6 | for EA between rotation temperatures and column densities is 0.4 |
| Pearson correlation coefficient, rotation temperature DE vs column density DE | 0.5 | not stated | dimensionless | 6 | for DE between rotation temperatures and column densities is 0.5 |
| Pearson correlation coefficient, rotation temperature EA vs DE | 0.44 | not stated | dimensionless | 6 | Rotation temperatures between EA and DE show no correlation |
| EA/DE column density ratio, average | 0.60 | not stated | dimensionless | 6 | ranging from 0.1 to 2.1 with an average value of 0.60. |
| EA/DE column density ratio, range | 0.1 to 2.1 | not stated | dimensionless | 6 | The column density ratios of EA to DE are within one order of magnitude, ranging from 0.1 to 2.1 |
| relative abundance f(CH3OH) of EA | 0.02 to 0.19 | not stated | dimensionless | 6 | The relative abundances range from 0.02 to 0.19 for EA and from 0.06 to 0.29 for DE, respectively |
| relative abundance f(CH3OH) of DE | 0.06 to 0.29 | not stated | dimensionless | 6 | The relative abundances range from 0.02 to 0.19 for EA and from 0.06 to 0.29 for DE, respectively |
| average rotation temperature of EA in this sample vs literature sources (sample comparison, 25 sources) | 167 (this sample) vs 171 (literature) | ±14 and ±12 (as stated) | K | 6 | The average rotation temperatures of EA and DE in our sample are |
| average rotation temperature of DE in this sample vs literature sources (sample comparison, 25 sources) | 131 (this sample) vs 136 (literature) | ±11 and ±12 (as stated) | K | 6 | The average rotation temperatures of EA and DE in our sample are |
| source counts by group: A (EA and DE, no Hii region) / B (EA and DE, Hii region) | 25 / 14 | not stated | count | 3 | Group A: 25 sources without associated Hii regions detected both EA and DE.; Group B: 14 sources associated with Hii regions have both EA and DE detections. |

## Qualitative findings

- EA and DE column densities correlate strongly with CH3OH and with each other, and the EA/DE ratio stays nearly constant across hot cores and hot corinos.  
  > "The column density ratios of EA/DE versus the column densities of CH$_3$OH remain nearly constant with values within" (abstract); "could be chemically linked" (abstract)
- The EA/DE ratio does not depend on the source rotation temperature, which the authors read as independence from the physical environment.  
  > "The nearly stable ratios suggest that the EA/DE ratio does not depend on the physical environment." (Implications for the chemistry of EA and DE)
- Reactions of radical products of CH3OH dissociation may be the predominant production route for EA and DE.  
  > "The comparison with experiments suggests that reactions involving the radical products" (Conclusions)

## Claim tuples

- H: EA, DE and CH3OH are chemically linked, with CH3OH a possible precursor. | E: Column density correlations among EA, DE and CH3OH across the sample and comparison with literature hot cores and hot corinos. | R: Pearson rho = 0.92 (EA-DE), 0.82 (EA-CH3OH), 0.80 (DE-CH3OH); EA/DE ratio nearly constant with CH3OH column density. | F: Strong correlations and stable ratios suggest a chemical link with CH3OH as a possible precursor. | **partially**
- H: Chemical models of warm-up timescale reproduce the observed EA and DE abundances. | E: Comparison of observed EA and DE abundances with three warm-up timescale models. | R: Models overproduce EA and underproduce DE systematically. | F: Large sample observations provide crucial constraints on chemical models. | **supported**
- H: EA and DE have different rotation temperatures and column densities. | E: LTE fits with XCLASS and MAGIX for EA and DE across the sample. | R: Average rotation temperature of EA is higher than DE; average column density of EA is lower than DE. | F: EA is warmer and less abundant than DE on average. | **supported**
- H: EA/DE ratio is independent of physical environment. | E: Plot of EA/DE ratio against rotation temperatures of EA and DE for hot cores and hot corinos. | R: No obvious upward or downward trend of EA/DE with rotation temperature. | F: EA/DE ratio stays within one order of magnitude regardless of environment. | **partially**
- H: Radical-radical recombination of CH3OH photoproducts is the main route to EA and DE. | E: Comparison of observed EA/DE ratios with experimental radical-radical recombination yields. | R: Experimental ratios give EA and DE within the same order of magnitude; observed ratios are consistent with this. | F: Reactions of CH3OH dissociation radicals may be the predominant mechanism. | **partially**

## Reasoning

- Why this data: Large-sample EA and DE observations with similar resolution and the same spectral coverage were lacking, so the ATOMS survey was used.  
  > "large sample observations of EA and DE molecules with similar spatial resolutions and the same spectral coverage are still lacking" (Introduction)
- Why this method: XCLASS LTE fits with MAGIX optimisation were used for line identification and parameters.  
  > "We used the XCLASS version 1.2.5 for the line fitting" (Line identification)
- Alternative: Continuum emission and dust attenuation were neglected rather than corrected in the line fitting.  
  > "Thus, we neglect continuum emission and dust attenuation in our spectral line fitting." (Line identification)
- Alternative: ACA 7-m data were not used; only 12-m array data were employed.  
  > "In this study, we only employ 12 m array data as hot cores typically have smaller source sizes" (Observations)
- How they decided it was enough: Column density sensitivity to the adopted temperature was tested over 100-200 K, with variation within 20%.  
  > "which showed a slight increase in column density, with the variation remaining within 20%." (Line identification)
- Limitation (authors): MAGIX fits did not converge in some sources, so first-step results are shown for those.  
  > "In some sources, the MAGIX calculations do not converge, so we show the results from the first step." (Line identification)
- Limitation (authors): Continuum-based source sizes may bias molecular column densities where line emission is more or less compact than the continuum.  
  > "the adopted source sizes from the continuum may lead to an underestimation of molecular column densities" (Line identification)
- Limitation (authors): Absence of EA in some sources cannot be confirmed because the lowest-energy EA line (18 K) is not covered.  
  > "observations at other wavelengths are needed to confirm the absence of EA in these sources" (Results and Statistical Analysis)
- Caveat (inferred, ours): Source sizes are taken from continuum, not measured for each molecule, which can bias column densities in both directions.
- Caveat (inferred, ours): Column densities depend on an assumed temperature for sources where only one or two lines are detected; the 150 K choice is a median, not a fit.
- Caveat (inferred, ours): Pearson coefficients are used with small and heterogeneous samples (39 ATOMS plus 28 literature sources), and no significance or non-detection treatment is given.
- Caveat (inferred, ours): Reported DE averages differ between sections (136 K for 25 sources in one place, 131 K in another; 4.2e17 vs 2.2e17 cm-2 for different subsets), which may confuse comparison.
- Caveat (inferred, ours): The triple-peaked DE line shape from overlapping EA and AE sub-states may bias DE fits, and blending with CH3OCHO and other species is flagged but not removed.
- Caveat (inferred, ours): Chemical-model comparison is qualitative and does not give a quantitative model fit.

## Reproducibility

- Data public (paper): Raw data are stated to be in the ALMA archive  
  > "The raw data are available in ALMA archive." (Data Availability)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Calibration scripts and calibrator details (deferred to earlier papers).
- Missing: Per-source XCLASS input parameters (source sizes, velocity offsets, line widths, temperatures) and MAGIX settings and priors.
- Missing: Full list of fitted transitions and blending decisions per source.
- Missing: Continuum image parameters (cell, size, line-free channels) and the H2 column densities used for abundances.
- Missing: The literature compilation of EA, DE and CH3OH column densities with individual citations.
- Data volume (inferred): Tens of GB (inferred: 12-m array data for 146 sources in Band 3, reduced to two broad spectral windows).
- Score (inferred): 3/5, Main results are numeric and the line-fitting approach is described, but calibration, per-source fit inputs and MAGIX settings are missing or deferred to earlier papers.
- Rediscovery candidate: no, Raw data are stated to be public, and results are numeric, but the per-source fitting inputs, calibration details and literature sample are not complete enough to redo the analysis.

## Links

- Method: (cite: 2017A&A...598A...7Moller) (XCLASS software used for line identification and LTE fitting)
- Method: (cite: 2013A&A...549A..21Moller) (MAGIX used for optimised rotation temperature and column density fits)
- Method: (cite: 2022MNRAS.511.3463Qin) (Line identification procedure, source sizes, methanol column densities and hot core sample)
- Method: (cite: 2020A&A...635A..48Manigand) (Continuum contribution correction (Eq. 5))
- Method: (cite: 2021A&A...651A...9Moller) (Dust opacity equation (Eq. 4) for dust optical depth)
- Method: (cite: 2021NatAs...5..188Loomis) (Local noise calculation method)
- Method: (cite: 2007ASPC..376..127McMullin) (CASA software reference)
- Companion: (cite: 2020MNRAS.496.2790LiuT) (First presentation of the ATOMS Band 3 data and spectral setups)
- Companion: (cite: 2020MNRAS.496.2821LiuT) (First presentation of the ATOMS Band 3 data and spectral setups)
- Companion: (cite: 2022ApJS..259....1G) (Chemical model (G22) compared with the observed EA and DE)
- Companion: (cite: 2023MNRAS.520.3245Z) (Source classification of UCHII association for the hot core sample)
- Related: ATOMS (ALMA Three-millimeter Observations of Massive Star-forming regions)

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 136,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 81,
  "rate": 0.786
 },
 "evidence_ok": true
}
```

## Figures

- **Figure 1** (scatter_or_relation, 2 panel(s), data): Rotation temperature versus column density for EA (left) and DE (right), with weighted least-squares fits; orange points are sources where rotation temperature and column density were not optimised and were excluded from the fits.
  - axes: x (left and right): rotation temperature Trot [K]; y left: EA column density N(EA) [cm-2]; y right: DE column density N(DE) [cm-2]
  - supports step 4
  - read off the plot: approx. EA peak column density about 1.3e18 cm-2 at Trot about 185 K; approx. DE peak column density about 2.5e18 cm-2 at Trot about 183 K; approx. DE fitted line rising from about 1e17 cm-2 at 105 K to about 2.5e18 cm-2 at 200 K; approx. EA fitted line from about 5e16 cm-2 at 90 K to about 2e17 cm-2 at 220 K
- **Figure 2** (histogram, 2 panel(s), data): Left: distribution of rotation temperatures for DE and EA with their means marked; right: EA rotation temperature plotted against DE rotation temperature with an equality line.
  - axes: x (left): rotation temperature [K]; y (left): number of sources [count]; x (right): DE rotation temperature [K]; y (right): EA rotation temperature [K]
  - supports step 4
  - validation: The right panel compares EA and DE rotation temperatures per source against the equality line to test whether the two species share a temperature.
  - read off the plot: approx. mean DE rotation temperature 136 K; approx. mean EA rotation temperature 167 K; approx. DE histogram peak of 7 sources near 140-150 K; approx. EA histogram peak of 7 sources near 165-185 K
  - reproduction target
- **Figure 3** (scatter_or_relation, 3 panel(s), data): Correlations of column densities among DE, EA and CH3OH across this work, other hot cores and hot corinos, with Pearson coefficients and one- and two-sigma bands around linear fits.
  - axes: x (a): DE column density N(DE) [cm-2]; x (b, c): CH3OH column density N(CH3OH) [cm-2]; y (a, b): EA column density N(EA) [cm-2]; y (c): DE column density N(DE) [cm-2]
  - supports step 6
  - read off the plot: approx. Pearson coefficient 0.92 for EA vs DE; approx. Pearson coefficient 0.82 for EA vs CH3OH; approx. Pearson coefficient 0.80 for DE vs CH3OH; approx. largest plotted N(CH3OH) about 3e20 cm-2
  - reproduction target
- **Figure 4** (scatter_or_relation, 1 panel(s), data): Column density ratio EA/DE against CH3OH column density for this work, other hot cores and hot corinos, with the mean ratio and a linear fit.
  - axes: x: CH3OH column density N(CH3OH) [cm-2]; y: column density ratio N(EA)/N(DE) [dimensionless]; reference line: mean EA/DE ratio 0.60 and EA/DE = 1 [dimensionless]
  - supports step 6
  - read off the plot: approx. mean N(EA)/N(DE) 0.60; approx. fitted ratio near 0.5 at 1e17 cm-2 and 0.45 at 3e20 cm-2; approx. this-work ratios mostly 0.1 to 0.6 near 1e18 cm-2; approx. hot corino ratio up to about 2 near 3e17 cm-2
  - reproduction target
- **Figure 5** (scatter_or_relation, 2 panel(s), data): Relationship between the EA/DE column density ratio and the rotation temperature of EA (upper) and of DE (lower), with linear fits.
  - axes: x (a): rotation temperature of EA [K]; x (b): rotation temperature of DE [K]; y (both): column density ratio N(EA)/N(DE) [dimensionless]
  - supports step 6
  - read off the plot: approx. EA/DE fit rising from about 0.25 at 80 K to about 0.9 at 330 K; approx. hot corino point near 2 at about 330 K; approx. this-work ratios mostly 0.1 to 1 at 130-180 K
- **Figure 6** (scatter_or_relation, 2 panel(s), data, model): Left: CH3OH column density against EA/CH3OH ratio; right: CH3OH column density against DE/CH3OH ratio, with horizontal lines for mean ratios and for simulated warm-up timescale predictions from Garrod et al. 2022.
  - axes: x (both): CH3OH column density N(CH3OH) [cm-2]; y left: column density ratio N(EA)/N(CH3OH) [dimensionless]; y right: column density ratio N(DE)/N(CH3OH) [dimensionless]
  - supports step 7
  - validation: Compares observed abundance ratios with model predictions for fast, medium and slow warm-up timescales.
  - read off the plot: approx. EA/CH3OH mean 0.050 (Mean Value 5.0e-2); approx. DE/CH3OH mean 0.11 (Mean Value 1.1e-1); approx. model DE/CH3OH fast 0.010, medium 0.017, slow 0.026; approx. model EA/CH3OH fast 0.061, medium 0.065, slow 0.080
  - reproduction target
