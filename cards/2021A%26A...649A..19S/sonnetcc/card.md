# Measuring the ratio of the gas and dust emission radii of protoplanetary disks in the Lupus star-forming region

`2021A&A...649A..19S` | Astronomy and Astrophysics 2021 | first author: Sanchis, E. | arXiv: 2101.11307 | DOI: 10.1051/0004-6361/202039733

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How large are the 12CO gas disks relative to the dust continuum disks across the Lupus population, and what does the CO/dust size ratio say about dust evolution (radial drift)?  
  > "In this work, we expand over the previous study of the gas and dust content in the protoplanetary disk population of Lupus" (Introduction); "We have investigated the relative extent of gas and dust in a large sample of protoplanetary disks of the Lupus clouds, in order to constrain the evolutionary stage of the disk population." (Conclusions)
- Target **Lupus protoplanetary disks (100 YSOs in the ALMA dataset, 42 with CO and dust radii; 9 BDs in the dataset)**: coordinates _not stated_; z/distance median 158.5 pc for Lupus; per-disk distances 136.9-175.8 pc in the results table  
  > "Lupus is one of the closest SFRs, at a median distance of $158.5$ pc (cite: gaiacollaboration2018)." (2 Sample selection); "the selected ALMA dataset is composed by $100$ protoplanetary disks around YSOs in the Lupus clouds, 9 of which are BDs." (2 Sample selection); "taking into account the distance from the precise Gaia DR$2$ parallaxes" (2 Sample selection); distance from Gaia DR2 parallaxes (cite: gaiacollaboration2018)  
  > "Lupus is one of the closest SFRs, at a median distance of $158.5$ pc (cite: gaiacollaboration2018)." (2 Sample selection); "the selected ALMA dataset is composed by $100$ protoplanetary disks around YSOs in the Lupus clouds, 9 of which are BDs." (2 Sample selection); "taking into account the distance from the precise Gaia DR$2$ parallaxes" (2 Sample selection)

## Data provenance

- ALMA projects: 2015.1.00222.S, 2016.1.01239.S, 2013.1.00226.S, 2013.1.01020.S, 2017.1.01243.S, 2013.1.00220.S, 2013.1.00694.S, 2013.1.00663.S, 2016.1.00484.L, 2013.1.00798.S
- bands: Band 6 (12CO 2-1) for CO; Band 7 (12CO 3-2 for 3 BDs); Band 7 continuum (~0.89 mm); Band 6 continuum (~1.33 mm) only for comparison  
  > "The CO radial extent of the disks is measured from archival ALMA observations covering the $\ce{^{12}CO}$ $J = 2-1$ rotational line in Band 6 (at $230.538$ GHz)." (3 Observations); "For $3$ sources, the $J = 3-2$ rotational transition in Band 7 (at $345.796$ GHz) is used instead." (3 Observations); "The dust sizes are obtained based on modeling of archival observations of dust continuum in ALMA Band $7$ (centered at $\sim 0.89$ mm)." (3 Observations)
- frequencies and spectral setup: 12CO 2-1 at 230.538 GHz; 12CO 3-2 at 345.796 GHz; Band 7 continuum ~335 GHz  
  > "The CO radial extent of the disks is measured from archival ALMA observations covering the $\ce{^{12}CO}$ $J = 2-1$ rotational line in Band 6 (at $230.538$ GHz)." (3 Observations); "For $3$ sources, the $J = 3-2$ rotational transition in Band 7 (at $345.796$ GHz) is used instead." (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Table 1: 12CO 2-1 ~0.24x0.23 arcsec (Lupus Disk survey); 12CO 3-2 ~0.36x0.33 arcsec (BD disks); Band 7 continuum ~0.34x0.30 arcsec (Lupus Disk survey)  
  > "$\sim0.24 \times 0.23$" (Table 1); "$\sim0.36 \times 0.33$" (Table 1); "$\sim0.34 \times 0.30$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Averages: Band 7 beam FWHM 0.32 arcsec and rms ~0.3 mJy; Band 6 beam 0.23 arcsec and ~0.1 mJy  
  > "(on average, Band 7 observations with beam size FWHM of $0.{}^{\prime}{}^{\prime}32$ and rms of $\sim$0.3 mJy, Band6 with $0.{}^{\prime}{}^{\prime}23$ and $\sim0.1$mJy)" (4.3 Gas/dust size ratio results)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA observations from several PI programmes (Williams, van Terwisga, Oberg, Tsukagoshi, Testi, Cleeves, Canovas, Andrews)  
  > "The CO radial extent of the disks is measured from archival ALMA observations covering the" (3 Observations)
- Line: 12CO J = 2-1 (230.538 GHz)
- Line: 12CO J = 3-2 (345.796 GHz)
- Other facility **Gaia DR2**: Parallax distances used to recompute stellar luminosities and masses  
  > "taking into account the distance from the precise Gaia DR$2$ parallaxes" (2 Sample selection)
- Other facility **VLT/SPHERE**: Near-infrared scattered-light disk extents for five disks, compared with the ALMA sizes  
  > "Five disks in our sample have been recently observed with VLT/SPHERE" (4.2 Dust size results)
- External data: Dust R_dust (68, 90, 95%) for the 10 disks with detected 12CO that were already modelled in the Lupus completion and BD surveys  
  > "In the present work, we take the $R_{\mathrm{dust}}$ results of (cite: sanchis+2020a) for the 10 disks with detected $\ce{^{12}CO}$" (3.2 Dust modeling) [from (cite: sanchis+2020a)]
- External data: Stellar properties (spectral type, Teff, etc.) of the sample  
  > "The stellar properties were taken from (cite: alcala+2014; alcala+2017) and (cite: muzic+2014)" (2 Sample selection) [from (cite: alcala+2014; alcala+2017) and (cite: muzic+2014)]
- External data: Pre-main-sequence evolutionary models used to interpolate stellar masses  
  > "The stellar mass is primarily interpolated from the pre-main sequence models of (cite: baraffe+2015)" (2 Sample selection) [from (cite: baraffe+2015); (cite: siess+2000) for masses above 1.4 Msun]
- External data: 22 R90 CO sizes from keplerian-masked curve-of-growth, used for comparison  
  > "we compare our results to the $22$ $R_{90\%}^{\mathrm{CO}}$ sizes from (cite: ansdell+2018)" (4.1 CO size results) [from (cite: ansdell+2018)]
- External data: Gas/dust size-ratio threshold of 4 above which radial drift is required  
  > "(cite: trapman+2019) showed that disks with gas/dust size ratios above 4 can only be explained if grain growth and subsequent radial drift has occurred." (1 Introduction) [from (cite: trapman+2019)]
- External data: Average CO temperature of 30 K for the optically thick CO line  
  > "This $T_{\mathrm{CO}}$ is based on the results in (cite: pinte+2018a)" (5.3 Optically thick emission and CO temperature) [from (cite: pinte+2018a)]
- External data: Dust opacity kappa_890um = 2 cm^2 g^-1 and dust temperature 20 K adopted for dust masses  
  > "and a dust optical depth of $\kappa_{890\mu m}$ = 2 $\mathrm{cm}^2 \mathrm{g}^{-1}$ (cite: ricci+2014; testi+2016; sanchis+2020a)" (5.2 Possible correlations) [from (cite: ricci+2014; testi+2016; sanchis+2020a)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "The uncertainty considered for the $M_{\mathrm{dust}}$ is the $10\%$ associated to the flux calibrator uncertainty of the ALMA observations." (5.2 Possible correlations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robustness = +0.5 (12CO channel maps)  
  > "The $\ce{^{12}CO}$ channel maps are built after subtracting the continuum and cleaning with a Briggs weighting and robustness = +0.5." (3 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Integrated (moment zero) map = sum of channels with emission above the noise around the source; channel range chosen by visual inspection of channel maps and spectrum  
  > "The integrated map is obtained by summing up all the channels showing emission above noise level around the known position of the object; the range of channels are selected based on visual examination of channel map and spectrum." (3.1 CO modeling)
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted before building 12CO channel maps  
  > "The $\ce{^{12}CO}$ channel maps are built after subtracting the continuum and cleaning with a Briggs weighting and robustness = +0.5." (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Interferometric (uv-plane) Nuker dust modelling with Galario + MCMC; the paper uses 'identical methodology' for the remaining disks  
  > "We refer to (cite: sanchis+2020a) for the detailed description of the interferometric modeling" (3.2 Dust modeling); "model the remaining disks of the Lupus population using identical methodology" (3.2 Dust modeling) [from (cite: sanchis+2020a)]
- Sample selection for the ALMA surveys  
  > "Details on the sample selection for the ALMA surveys are to be found in (cite: ansdell+2016; ansdell+2018) for the stellar objects, and (cite: sanchis+2020a) for the BDs." (2 Sample selection) [from (cite: ansdell+2016; ansdell+2018); (cite: sanchis+2020a)]
- Observation details and array configurations are given in the cited reference papers  
  > "and the corresponding references that describe the observations and the instrument configuration." (3 Observations) [from (cite: ansdell+2018), (cite: vanterwisga+2018), (cite: cleeves+2016), (cite: canovas+2016), (cite: sanchis+2020a), (cite: ansdell+2016), (cite: andrews+2018dsharp)]
- Stellar mass uncertainty from a Monte Carlo procedure  
  > "The stellar mass uncertainty is obtained from a Monte Carlo procedure as in (cite: alcala+2017)." (2 Sample selection) [from (cite: alcala+2017)]
- Nuker profile as empirical emission model  
  > "the so-called Nuker profile model (cite: lauer+1995; tripathi+2017) is used instead." (3.1 CO modeling) [from (cite: lauer+1995; tripathi+2017)]
- Size definition as radius enclosing a fraction of total flux  
  > "This definition has been recently used to characterize large samples of disks from ALMA observations (cite: tazzari+2017; andrews2018A; hendler+2020)" (3.1.1 Size definition) [from (cite: tazzari+2017; andrews2018A; hendler+2020)]
- Optically thin, Rayleigh-Jeans dust mass formula  
  > "The dust disk mass is computed assuming that the emission is optically thin and in the Rayleigh-Jeans regime (cite: beckwith+1990)" (5.2 Possible correlations) [from (cite: beckwith+1990)]

### Not stated but needed to reproduce (our reading)

- Per-disk 12CO channel ranges used to build the integrated maps (only 'visual examination' is stated)
- CASA version and calibration route (pipeline vs manual); whether archive products were used as is
- tclean/imaging parameters for CO cubes: cell size, image size, deconvolver, masks, spectral resolution, uv taper
- Continuum-subtraction details: line-free channels and order of the fit
- Which archival datasets (and execution blocks) feed each disk when several projects cover the same source
- Nuker fit in the image plane: free-parameter starting values, bounds, optimiser settings; how the elliptical Gaussian centre is fixed for the Nuker fit
- Numerical values of the mu +/- sigma residual-criterion limits and the exact residual definition applied per disk
- MCMC details for the dust uv fits (walkers, steps, priors, burn-in, uv range) are only given by reference to Sanchis et al. 2020a
- How CO fluxes were corrected for inclination and which inclinations were used
- How upper limits (95th percentile) are computed for undetected or unresolved sizes
- Disk-to-star bookkeeping for the 100-disk sample (which disks lack CO or dust sizes and why, beyond the listed exclusions)

## Analysis recipe

1. **Build integrated CO maps from archival cubes**: Continuum-subtracted 12CO channel maps cleaned with Briggs weighting (robust +0.5); sum of the channels with emission to make a moment zero map  
  > "The $\ce{^{12}CO}$ channel maps are built after subtracting the continuum and cleaning with a Briggs weighting and robustness = +0.5." (3 Observations); "The integrated map is obtained by summing up all the channels showing emission above noise level around the known position of the object; the range of channels are selected based on visual examination of channel map and spectrum." (3.1 CO modeling)
   - parameter: robust = +0.5  
  > "The $\ce{^{12}CO}$ channel maps are built after subtracting the continuum and cleaning with a Briggs weighting and robustness = +0.5." (3 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit CO integrated maps with elliptical Gaussian or Nuker model**: Elliptical Gaussian fit in the image plane with imfit; for disks poorly described by a Gaussian, the azimuthally averaged emission is fitted with a Nuker profile; outer edge of the Nuker model set where the average profile first reaches zero  
  > "The CO emission of each disk is primarily modeled by fitting the integrated line map to an elliptical Gaussian function in the image plane." (3.1 CO modeling); "task from CASA software (cite: mcmullin+2007) was used." (3.1 CO modeling); "The outer edge of the Nuker model is set as the radius in which the azimuthally average profile first reaches zero." (3.1 CO modeling)
   - software: CASA (imfit), scipy.optimize
   - assumption: Empirical profiles with no assumption on disk kinematics (no Keplerian masking)  
  > "We avoid this approach in order to keep our analysis as general as possible, without any assumptions on the disk physics." (3.1.1 Size definition)
   - fitting: imfit gives parameter values with uncertainties for the Gaussian; Nuker fit by scipy.optimize on the azimuthally averaged profile  
  > "[^1]: using `scipy.optimize` Python module" (3.1 CO modeling)
   - validation: _not stated_
3. **Derive CO radii enclosing 68/90/95% of flux and uncertainties**: Deprojected model profile -> cumulative flux; R68/R90/R95 where cumulative flux reaches the fraction of total model flux. Gaussian uncertainty from major-axis FWHM error; Nuker uncertainty from 1000 Monte Carlo realisations  
  > "The fractions considered are the 68, 90 and $95\%$ for easy comparison with previous works." (3.1.1 Size definition); "The uncertainty of the CO sizes are obtained from the major-axis FWHM error on the Gaussian fits." (3.1.1 Size definition); "1000 realizations of the free parameters are drawn from a random normal distribution" (3.1.1 Size definition)
   - parameter: R90 ~ 1.42 R68 and R95 ~ 1.62 R68 for Gaussian models; 1000 Monte Carlo draws for Nuker models  
  > "By definition of the Gaussian function, there is a constant relation between the $R_{68\%}$ and the two other radii ($R_{90\%}$, $R_{95\%}$)" (4.1 CO size results)
   - fitting: _not stated_
   - validation: Exclusions: disks with model peak below 3 times the rms of the moment zero map, cloud-covered maps, close binaries  
  > "We exclude the results from disks with model peak below 3 times the rms of the observed moment zero map" (4.1 CO size results)
4. **Calibrate CO-size systematics with DSHARP and choose Gaussian vs Nuker**: uv-plane Nuker (and Gaussian) fits of spectrally integrated DSHARP CO visibilities give fiducial sizes for 6 disks; compare with image-plane Gaussian fits of the lower-resolution data; a residual-based criterion decides which disks use a Gaussian and which a Nuker model  
  > "channels with line emission are continuum-subtracted and then spectrally integrated; the resulting visibilities are then modeled by a Nuker profile model." (3.1.2 CO size uncertainties); "we developed a criterion that evaluates the quality of the model, based on the amount of residuals (difference between observed and modeled emission)." (3.1.2 CO size uncertainties); "otherwise the emission is fitted to a Nuker function" (3.1.2 CO size uncertainties)
   - software: Galario, emcee-style affine-invariant MCMC (as cited, not named)
   - parameter: 200 independent walkers for thousands of steps; baselines > 1000 klambda excluded  
  > "This is done for 200 independent walkers for thousands of steps." (7 Interferometric modeling of DSHARP line emission); "Due to expensive computation time required to model the large set of visibilities from DSHARP observations, baselines $> 1000$ $k\lambda$ are excluded from the fit." (7 Interferometric modeling of DSHARP line emission)
   - assumption: DSHARP uv-plane Nuker sizes treated as fiducial CO sizes  
  > "The radii based on the interferometric modeling of the DSHARP data are considered as the fiducial CO sizes of the disks." (8 Results of CO sizes using different methodology)
   - fitting: Galario computes chi^2 between observed and synthetic visibilities; affine-invariant MCMC; median and 16th/84th percentiles of the chains give values and uncertainties  
  > "The `Galario` package (cite: tazzari+2018) is used to convert the empirical model into synthetic visibilities" (7 Interferometric modeling of DSHARP line emission); "The median of each parameter histogram are taken as the best value of the parameter, and the $16$th and $84$th percentiles are used as lower and upper uncertainties." (7 Interferometric modeling of DSHARP line emission)
   - validation: Image-plane CO sizes agree with fiducial uv-plane sizes within ~0-30% when residuals are inside the mu +/- sigma range  
  > "In summary, our modeling in the image plane typically allows to measure the CO sizes for the Lupus disk sample with an uncertainty $\lesssim30\%$" (3.1.2 CO size uncertainties)
5. **Measure dust radii by uv-plane Nuker fits**: Continuum visibilities fitted in the uv-plane with a Nuker profile using Galario and MCMC, following Sanchis et al. 2020a; R68/R90/R95 as for CO  
  > "package (cite: tazzari+2018) was used in combination with a Monte Carlo Markov Chain procedure to model the continuum emission of the BD disks and sources from the Lupus disk completion survey." (3.2 Dust modeling); "model the remaining disks of the Lupus population using identical methodology" (3.2 Dust modeling)
   - software: Galario
   - fitting: MCMC fit of Nuker model in the uv-plane (details in Sanchis et al. 2020a)  
  > "We refer to (cite: sanchis+2020a) for the detailed description of the interferometric modeling" (3.2 Dust modeling)
   - validation: Image-plane Nuker fits for a number of resolved disks agree to ~5%; sizes compared with literature  
  > "Nevertheless, we tested the resulting dust sizes when modeling to a Nuker function in the image plane for a number of resolved disks." (3.2 Dust modeling)
6. **Compute gas/dust size ratios and population statistics**: Ratio R68(CO)/R68(dust) per disk; median and dispersion excluding upper limits; Anderson-Darling test of CO vs dust size distributions; Spearman, Pearson and Shapiro-Wilk tests of ratio vs stellar mass, disk mass, R_dust, R_CO  
  > "excluding disks with an upper limit value in CO and/or dust size." (4.3 Gas/dust size ratio results); "For this examination we make use of the Spearman and Pearson correlation coefficients (cite: hendler+2020)." (5.2 Possible correlations)
   - software: scipy.stats
   - parameter: Null hypothesis rejected when p < 0.05; objects with upper limits excluded  
  > "If the p-value of a given test is below 0.05, the null hypothesis of the respective test is rejected." (5.2 Possible correlations); "For each relationship, the tests are performed by excluding all objects with upper limits in the CO size or the dust size." (5.2 Possible correlations)
   - fitting: _not stated_
   - validation: Results repeated with R90 radii and with a 0.7-1.1 Msun sub-sample to limit completeness bias  
  > "The size ratio median in this mass range remains 2.5, with a dispersion of 2." (4.3 Gas/dust size ratio results)
7. **Estimate dust and total disk masses**: Optically thin Rayleigh-Jeans dust mass; total disk mass from dust mass with a gas-to-dust ratio of 100  
  > "The dust disk mass is computed assuming that the emission is optically thin and in the Rayleigh-Jeans regime (cite: beckwith+1990)" (5.2 Possible correlations); "The total disk mass is approximated from the dust disk mass, assuming a gas-to-dust ratio of 100." (5.2 Possible correlations)
   - parameter: dust temperature 20 K  
  > "with an average temperature on the dust mid-plane of 20 K (cite: pascucci+2016; ansdell+2016; ansdell+2018; sanchis+2020a)" (5.2 Possible correlations)
   - parameter: kappa_890um = 2 cm^2 g^-1  
  > "and a dust optical depth of $\kappa_{890\mu m}$ = 2 $\mathrm{cm}^2 \mathrm{g}^{-1}$ (cite: ricci+2014; testi+2016; sanchis+2020a)" (5.2 Possible correlations)
   - assumption: Gas-to-dust ratio 100  
  > "The total disk mass is approximated from the dust disk mass, assuming a gas-to-dust ratio of 100." (5.2 Possible correlations)
   - fitting: _not stated_
   - validation: Authors call it a big approximation useful for an overall idea of disk mass  
  > "While this is a big approximation for the disk mass, it is useful in order to have an overall understanding of the available disk mass." (5.2 Possible correlations)
8. **Compare CO flux vs size with optically thick constant-temperature profiles**: Grid of optically thick, radially constant-temperature CO emission profiles (30 K and 20 K) with increasing outer edge; R68 of each profile gives the line plotted against modelled CO flux and R68  
  > "This line is composed by a grid of optically thick emission profiles with constant temperature." (5.3 Optically thick emission and CO temperature); "we have plotted an orange line representing optically thick emission with an average CO temperature ($T_{\mathrm{CO}}$) of 30 K" (5.3 Optically thick emission and CO temperature)
   - parameter: T_CO = 30 K (20 K as CO freeze-out reference)  
  > "This $T_{\mathrm{CO}}$ is based on the results in (cite: pinte+2018a)" (5.3 Optically thick emission and CO temperature)
   - assumption: Face-on optically thick emission; temperature constant with radius  
  > "The optically thick line plotted assumes a face-on orientation" (5.3 Optically thick emission and CO temperature)
   - fitting: _not stated_
   - validation: Spearman correlation between CO flux and size, p = 3e-5  
  > "The Spearman test provides a very low p-value (of 3e-5, obtained by excluding CO size upper limits)." (5.3 Optically thick emission and CO temperature)

## Software

- **CASA** : imfit for elliptical Gaussian fits to the integrated CO maps  
  > "task from CASA software (cite: mcmullin+2007) was used." (3.1 CO modeling)
- **Galario** : Convert empirical models to synthetic visibilities and compute chi^2 in uv-plane dust and DSHARP CO fits  
  > "The `Galario` package (cite: tazzari+2018) is used to convert the empirical model into synthetic visibilities" (7 Interferometric modeling of DSHARP line emission)
- **scipy.optimize** : Fitting the Nuker profile to the azimuthally averaged CO emission  
  > "using `scipy.optimize` Python module" (Footnote 1)
- **scipy.stats** : Anderson-Darling, Spearman, Pearson and Shapiro-Wilk tests  
  > "The `scipy.stats` Python module[^3] is used to perform the aforementioned tests." (5.2 Possible correlations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of disks with measured CO and dust radii | 42 | not stated | disks | 2 | However, our analysis concentrates on the 42 disks whose CO and dust radii could be measured. |
| Median R68(CO)/R68(dust), entire sample | 2.5 | dispersion 1.5 (standard deviation) | dimensionless | 6 | The median value of the size ratio is $2.5$ for the entire population and for a sub-sample with high completeness.; The dispersion of this sample (considered as the standard deviation of the size ratio sample) is relatively high, of $1.5$, raised by the few disks with very high size ratios. |
| Median R90(CO)/R90(dust), entire sample | 2.7 | dispersion 1.5 | dimensionless | 6 | The median and dispersion of the size ratio when using the $R_{90\%}$ CO and dust radii are slightly larger, 2.7 and 1.5 respectively. |
| Median R68 size ratio, 0.7-1.1 Msun sub-sample (8 disks) | 2.5 | dispersion 2 | dimensionless | 6 | The size ratio median in this mass range remains 2.5, with a dispersion of 2. |
| Anderson-Darling probability that CO and dust R68 come from the same parent distribution | < 0.001% | not stated | percent | 6 | The Anderson–Darling test[^2] yields a \<$0.001\%$ probability that the two radii histograms are drawn by the same parent distribution. |
| Fraction of disks with size ratio above 4 | ~15% (entire population); ~13% if uncertainties are strictly above 4 | not stated | percent | 6 | The fraction of disks with size ratios above the threshold value of 4 is $\sim$15$\%$ for the entire population ($\sim$13$\%$ if we only consider disks whose size ratio uncertainties are strictly above 4). |
| Spearman p-value, size ratio vs R_dust (all disks without upper limits) | 0.002 (monotonic) | not stated | dimensionless | 6 | Monotonic (0.002) |
| Spearman p-value, CO flux vs CO size | 3e-5 | not stated | dimensionless | 8 | The Spearman test provides a very low p-value (of 3e-5, obtained by excluding CO size upper limits). |
| Median size ratio of disks around very low-mass stars (<0.2 Msun) | 3.1 | dispersion 0.4 | dimensionless | 6 | The median size ratio of disks around very low-mass stars is 3.1 (with a dispersion of 0.4), larger than the mean value of the entire population. |
| R68(CO)/R68(dust) of Sz 75 | 8.0 | 0.9 | dimensionless | 6 | $8.0 \pm 0.9$ |
| Accuracy of image-plane CO sizes relative to fiducial DSHARP sizes | uncertainty of at most ~30% when Gaussian residuals are in range | not stated | percent | 4 | In summary, our modeling in the image plane typically allows to measure the CO sizes for the Lupus disk sample with an uncertainty $\lesssim30\%$ |
| Dust R90 in this work relative to Ansdell et al. 2018 | ~22% shorter | not stated | percent | 5 | Indeed, the $R_{90\%}^{\mathrm{dust}}$ in this work is $\sim22\%$ shorter than the tabulated sizes in (cite: ansdell+2018). |
| Size difference, image-plane vs uv-plane Gaussian modelling of DSHARP CO | 2% on average | not stated | percent | 4 | The difference in size is negligible for every disk, $2\%$ on average |

## Qualitative findings

- CO disks are systematically larger than dust disks in Lupus  
  > "A difference between the CO disk and the dust disk sizes becomes apparent from the figure." (4.3 Gas/dust size ratio results)
- Gaussian image-plane modelling failing to reproduce extended emission is the most limiting effect on CO size accuracy  
  > "Hence, the Gaussian modeling not reproducing the observed emission of certain objects is the most limiting effect on the CO size determination." (3.1.2 CO size uncertainties)
- The curve-of-growth method overestimates dust extent, explaining the lower size ratio of Ansdell et al. 2018  
  > "The curve of growth method typically overestimates the dust extent." (4.3 Gas/dust size ratio results)
- Lack of strong correlations between size ratio and stellar or disk properties  
  > "The results of these statistical tests show a remarkable lack of strong correlations between the size ratio and the investigated properties." (5.2 Possible correlations)

## Claim tuples

- H: Are Lupus CO gas disks more extended than the dust disks, and by how much? | E: Measure R68 for 12CO (image-plane Gaussian/Nuker) and dust (uv-plane Nuker) for 42 disks and compare | R: Median R68 CO/dust ratio 2.5 with dispersion 1.5; Anderson-Darling p < 0.001% | F: CO disks are systematically larger than dust disks | **supported**
- H: Does a substantial fraction of Lupus disks show size ratios requiring dust evolution (ratio > 4)? | E: Count disks with R68 CO/dust above the Trapman et al. 2019 threshold of 4 | R: ~15% of the population (6 disks named) above 4 | F: A considerable fraction of Lupus disks have undergone radial drift and dust evolution | **supported**
- H: Is the size ratio correlated with stellar mass, disk mass, R_dust or R_CO? | E: Spearman, Pearson and Shapiro-Wilk tests with upper limits excluded, with and without disks above ratio 4 | R: Only R_dust shows a (tentative) monotonic anti-correlation; stellar mass hints at one at p ~0.06-0.07 after excluding ratio > 4 | F: Most disks have similar ratios (~2-4) independent of stellar and disk properties | **partially**
- H: Can CO sizes be measured reliably in the image plane with Gaussian or Nuker models? | E: Compare image-plane sizes with uv-plane Nuker fits of higher-resolution DSHARP CO data for six disks | R: Sizes agree within ~0-30% when the residual criterion is satisfied | F: Image-plane modelling gives CO sizes good to <~30% | **supported**
- H: Why is the median size ratio higher than the ~2 of Ansdell et al. 2018? | E: Rerun curve-of-growth on Band 6 and Band 7 continuum maps and compare with uv-plane Nuker dust sizes | R: Curve-of-growth reproduces the earlier dust sizes in both bands; Band 7 sizes only ~6% larger | F: The dust-size method, not the ALMA band, explains the difference | **supported**
- H: What is the temperature of the CO emitting layer? | E: Compare modelled CO flux vs R68 against optically thick constant-temperature profiles at 30 K and 20 K | R: About a third of the disks are crossed by the 30 K line; about half lie on the right of it | F: Consistent with ~30 K on average, though some disks may be colder; exact determination is difficult | **partially**

## Reasoning

- Why this data: 12CO is abundant and self-shielded, so suited to trace gas extent  
  > "The CO emission from these lines is appropriate for the study of the gas extent due to its abundance." (1 Introduction)
- Why this method: Empirical image-plane CO modelling avoids assumptions on disk physics and works for low-S/N CO, increasing the number of disks with measured CO sizes  
  > "We avoid this approach in order to keep our analysis as general as possible, without any assumptions on the disk physics." (3.1.1 Size definition); "This modeling is appropriate for the CO disks characterization due to the low S/N for the bulk of the sample." (3.1 CO modeling); "The integrated CO emission is modeled to empirical functions, this allows us to increase the number of disks with characterized CO compared to previous studies." (1 Introduction)
- Alternative: Curve of growth on Keplerian-masked moment zero maps (Ansdell et al. 2018) not used; sizes of faint sources are hard to get that way  
  > "In that work, the CO size was estimated from the curve of growth of keplerian masked moment zero maps." (3.1.1 Size definition); "Additionally, sizes of fainter sources are difficult to measure using the curve of growth, since there is no clear end of the disk emission in the curve of growth." (3.1.1 Size definition)
- How they decided it was enough: _not stated_
- Limitation (authors): CO sizes may differ from the true size by 0 to ~30%  
  > "However, CO sizes based on this dataset might have a discrepancy with respect to the true CO size between 0 and $\sim30\%$" (4.3 Gas/dust size ratio results)
- Limitation (authors): Selection effect toward larger CO sizes  
  > "There is a selection effect toward larger CO sizes, since it is more difficult to detect and measure CO sizes as small as the dust sizes." (4.3 Gas/dust size ratio results)
- Limitation (authors): Size-ratio vs R_dust anti-correlation may be boosted because R_dust is the denominator of the ratio  
  > "However, this result should be taken with caution, since the Y-axis (the size ratio) is dependent on the X-axis" (5.2 Possible correlations)
- Caveat (inferred, ours): Gas/dust size ratio mixes optical-depth and dust-evolution effects; the 4 threshold comes from one grid of thermo-chemical models
- Caveat (inferred, ours): Heterogeneous resolution and sensitivity across eight ALMA datasets; no beam-size correction for compact disks
- Caveat (inferred, ours): CO R68 from moment zero maps includes cloud absorption, outflows and non-Keplerian emission (e.g., Sz 83, Sz 82)
- Caveat (inferred, ours): Gaussian-vs-Nuker choice depends on a residual criterion tuned on only six DSHARP disks
- Caveat (inferred, ours): Statistical tests ignore uncertainties on the size ratio

## Reproducibility

- Data public (paper): Archival ALMA observations from the listed project codes  
  > "The CO radial extent of the disks is measured from archival ALMA observations covering the" (3 Observations)
- Products in archive: _not stated_
- Missing: Per-disk CO channel ranges and cleaning/imaging parameters
- Missing: CASA version and calibration route for each archival dataset
- Missing: Residual criterion thresholds and Nuker fit starting values or bounds
- Missing: Dust uv-fit setup (priors, walkers, steps) is deferred to Sanchis et al. 2020a
- Missing: No code or fitted-model files stated as released
- Data volume (inferred): Order of 100-300 GB for ~10 archival projects (Lupus Disk surveys plus DSHARP), or tens of GB if only the Band 6 and Band 7 survey data are reprocessed
- Score (inferred): 3/5, Public archival data and numeric tables, but imaging settings, channel ranges, residual cutoffs and dust uv-fit details are missing or inherited, so exact reproduction is only moderate (scale 1-5).
- Rediscovery candidate: no, Data are public and results numeric, but the recipe depends on unstated channel ranges, imaging parameters and the inherited dust uv-fit procedure.

## Links

- Method: (cite: sanchis+2020a) (Dust uv-plane Nuker modelling with Galario and MCMC, and dust sizes for 10 disks)
- Method: (cite: tazzari+2018) (Galario package)
- Method: (cite: trapman+2019) (Thermo-chemical models giving the size-ratio threshold of 4)
- Method: (cite: tripathi+2017) (Nuker profile for disk emission)
- Companion: (cite: ansdell+2018) (Previous Lupus gas and dust size study (Band 6 data and curve-of-growth sizes))
- Companion: (cite: ansdell+2016) (Lupus Band 7 disk survey)
- Companion: (cite: vanterwisga+2018) (Lupus completion survey)
- Companion: (cite: andrews+2018dsharp) (DSHARP data used for CO size calibration)
- Companion: (cite: huang+2020) (Dynamical analysis of Sz 83 CO emission)
- Related: ALMA Lupus Disk Survey (Band 6 and Band 7)
- Related: Lupus Completion Disk survey
- Related: Lupus BD Disks survey
- Related: DSHARP

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 136,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 71,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
