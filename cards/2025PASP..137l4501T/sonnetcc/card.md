# The ViSta Method for Stacking in the Fourier Domain and its Application to the Dusty Star-forming Galaxies in the ALMA Science Archive

`2025PASP..137l4501T` | Publications of the Astronomical Society of the Pacific 2025 | first author: Torsello, Martina | arXiv: 2511.16753 | DOI: 10.1088/1538-3873/ae1faf

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Can visibilities of galaxies at different redshifts be stacked directly in the Fourier domain after shifting them to the rest frame (ViSta), and does this recover faint line emission better than image-plane stacking, as tested on simulated data and on CO(3-2) in a sample of dusty star-forming galaxies from the ALMA archive?  
  > "By stacking visibilities of galaxies with secure spectroscopic redshifts directly in the Fourier domain and transforming them into the rest-frame, we can enhance the stacked signal, suppress noise, and improve image reconstruction" (abstract); "Finally, we applied ViSta to a sample of dusty star-forming galaxies (DSFGs) observed with the Atacama Large Millimeter/sub-millimeter Array (ALMA) to detect the CO(3-2) emission line" (abstract)
- Target **Real sample: 21 HerBS dusty star-forming galaxies (HerBS-11 ... HerBS-209)**: coordinates Per-source RA/Dec listed in Table 1 (sexagesimal); not repeated in the text  
  > "The sample consists of 21 partially resolved or unresolved galaxies, four of which had two available observations, in the redshift range of $z\sim 1.407 - 2.73$ and angular resolutions between 0.25 and 2.8" (Application to a real case); "Detailed information for each source, including coordinates, resolution, and spectroscopic redshift, is provided in Table" (Application to a real case); "which provided spectroscopic redshifts through ALMA spectral scans" (Application to a real case); z/distance z_spec = 1.407-2.73 (per-source values in Table 1); reference redshift 2.5 used for the D_L correction  
  > "The sample consists of 21 partially resolved or unresolved galaxies, four of which had two available observations, in the redshift range of $z\sim 1.407 - 2.73$ and angular resolutions between 0.25 and 2.8" (Application to a real case); "Detailed information for each source, including coordinates, resolution, and spectroscopic redshift, is provided in Table" (Application to a real case); "which provided spectroscopic redshifts through ALMA spectral scans" (Application to a real case); distance from Spectroscopic redshifts from the BEARS I, II and III studies (ALMA spectral scans)  
  > "The sample consists of 21 partially resolved or unresolved galaxies, four of which had two available observations, in the redshift range of $z\sim 1.407 - 2.73$ and angular resolutions between 0.25 and 2.8" (Application to a real case); "Detailed information for each source, including coordinates, resolution, and spectroscopic redshift, is provided in Table" (Application to a real case); "which provided spectroscopic redshifts through ALMA spectral scans" (Application to a real case)
- Target **Mock sample: 50 simulated galaxies (point-like and 5 arcsec FWHM Gaussian)**: coordinates _not stated_; z/distance random z between 2 and 4  
  > "on a sample of 50 simulated galaxies" (5.1 Building simulated ALMA dataset); "Each of the mock galaxies is assigned a random value of redshift between 2-4" (5.1 Building simulated ALMA dataset); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.01477.S, 2021.1.01628.S, 2022.1.00432.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m antennas assumed for the primary-beam model; ALMA 12-meter array  
  > "The primary beam (PB) response of an ALMA 12-meter antenna can be approximated by a normalized symmetric Gaussian function that depends on the observing frequency" (3.1 Centering)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.25 to 2.8 arcsec across the real sample; worst resolution (common convolution beam) 5.063 x 2.820 arcsec  
  > "angular resolutions between 0.25 and 2.8" (Application to a real case); "corresponding to a synthesized beam of $5.063^{\prime\prime} \times 2.820^{\prime\prime}$" (Application to a real case)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data from three projects (PIs S. Urquhart, T. Bakx, T. Bakx); sources taken from the BEARS I-III samples  
  > "This paper makes use of the following ALMA data" (Summary and outlook (acknowledgements)); "The selected sources are part of the sample analyzed in the BEARS I, II, and III studies" (Application to a real case)
- Line: CO J=3-2 (not stated)
- Other facility **EU ARC CalMS service**: Calibrated measurement sets for archival products and ARI-L project products  
  > "We mostly retrieved calibrated datasets by exploiting the EU ARC CalMS service" (Footnote 1)
- External data: Spectroscopic redshifts of the sources (from ALMA spectral scans), plus SED constraints and line detections for the sample  
  > "which provided spectroscopic redshifts through ALMA spectral scans" (Application to a real case) [from BEARS I, II and III (cite: bearsI; bearsII; bearsIII)]
- External data: Literature line properties used as a consistency comparison for the stacked CO(3-2) line  
  > "The resulting line properties are broadly consistent with other estimates in the literature" (Application to a real case) [from (cite: bearsIII; spilker2014)]
- Simulation/model as data: 50 mock sources per case (point-like; and 5 arcsec FWHM Gaussian), z random between 2 and 4, flat continuum 0.6 mJy per channel plus a Gaussian line of peak 2 mJy in the 20 central channels  
  > "The continuum is modeled as a flat component with an intensity of $0.6$ mJy per channel across the full bandwidth." (5.1 Building simulated ALMA dataset); "The line emission is added on top of the continuum and modeled as a Gaussian profile centered on the source position, confined to the 20 central spectral channels, with a peak flux of $2$ mJy." (5.1 Building simulated ALMA dataset); "we model a spatially resolved Gaussian source with a FWHM of $5^{\prime\prime}$" (5.1 Building simulated ALMA dataset)
- Simulation/model as data: Sky model cubes of 100 channels, 1 MHz wide, 512x512 pixels, reference frequency 345.7598 GHz, observed with simobserve using ALMA cycle 11 configurations 2 to 5 (baselines up to 314 m to 1400 m)  
  > "The input sky models consist of spectral cubes with 100 channels, each 1 MHz wide." (5.1 Building simulated ALMA dataset); "with $n$ ranging from 2 (corresponding to configurations with baselines up to 314 m) to 5 (with baselines up to 1400 m)" (5.1 Building simulated ALMA dataset)
- Simulation/model as data: Noise added as separate MSs without noise then corrupted with custom Python functions (per-antenna atmospheric temperature and opacity, up to 10% random variations of key parameters)  
  > "we choose to generate the MS for each mock source without noise and then corrupt them using custom Python functions." (5.1 Building simulated ALMA dataset); "with random variations of up to 10% applied to key observational parameters" (5.1 Building simulated ALMA dataset)

## Processing

### Calibration

- pipeline or manual: Calibrated datasets mostly retrieved from the EU ARC CalMS service (archival and ARI-L products); calibration procedure itself not described  
  > "We mostly retrieved calibrated datasets by exploiting the EU ARC CalMS service" (Footnote 1); "After calibrating each dataset" (3 Applications to the ALMA Science Archive)
- casa version: CASA 6.6 (main analysis); CASA v.6 for simobserve  
  > "we mainly employed version 6.6 of the Common Astronomy Software Applications (CASA) package" (3 Applications to the ALMA Science Archive)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (dirty image with niter=0 first; cube mode for lines, mfs for continuum); threshold typically 3 sigma  
  > "The final step involves transforming the stacked visibilities into the image plane using the casatasks.tclean() task from the CASA software package" (3.8 Imaging); "The threshold is typically set at a level of $3\sigma$." (3.8 Imaging)
- deconvolver: Hogbom  
  > "We use the Hogbom algorithm, a classic cleaning method suitable for fields dominated by point sources or compact emission." (3.8 Imaging)
- weighting robust: natural weighting (no robust value)  
  > "Furthermore, we select natural weighting to enhance sensitivity at the expense of resolution" (5.2.1 Unresolved Source)
- uv taper: _not stated_
- cell size: 1/5 of the major axis of the restoring beam  
  > "We define the cell size to be $1/5$ of the major axis of the restoring beam." (3.8 Imaging)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Not done for the real-sample line stacking (to avoid biasing the line); a continuum image was made separately as post-processing  
  > "Moreover, we did not subtract the continuum to avoid biasing the line emission." (6 Application to a real case)
- line free channels: _not stated_
- primary beam correction: Each visibility divided by the Gaussian primary-beam attenuation at its original position in the field (before stacking)  
  > "we divide each visibility by the correction for primary beam attenuation that it would have experienced at its original position in the field of view." (3.1 Centering)
- array combination: Rest-framed MSs concatenated into one MS with CASA concat  
  > "After this rescaling, the measurement sets are concatenated using the CASA" (3.5 Stacking)
- smoothing: For SNR comparison all datasets convolved to the worst angular resolution of the sample  
  > "convolve all datasets to the worst angular resolution available" (6 Application to a real case)
- final beam: 5.063 x 2.820 arcsec (worst-resolution common beam)  
  > "corresponding to a synthesized beam of $5.063^{\prime\prime} \times 2.820^{\prime\prime}$" (6 Application to a real case)
- final rms: _not stated_

### Inherited from earlier work

- Reference redshift 2.5 for the luminosity-distance correction, chosen for consistency with previous DSFG stacking analyses  
  > "we did apply a correction for luminosity distance differences, adopting a reference redshift of 2.5" (6 Application to a real case) [from (cite: bearsIII; spilker2014)]
- Source selection, coordinates and spectroscopic redshifts come from the BEARS studies  
  > "The selected sources are part of the sample analyzed in the BEARS I, II, and III studies" (6 Application to a real case) [from (cite: bearsI; bearsII; bearsIII)]
- Calibrated MSs obtained from the ARI-L/CalMS products  
  > "We mostly retrieved calibrated datasets by exploiting the EU ARC CalMS service" (Footnote 1) [from (cite: massardi21)]
- Source-size estimation for the real sample follows the simulation approach (moment-0 map + 2D Gaussian fit), except the uvmultifit case where size is left free per channel  
  > "As we can estimate an approximate source size from the zero order moment maps for our sample, we used the same approach as the simulations" (6 Application to a real case) [from Sect. 5.2.2.2 of this paper]

### Not stated but needed to reproduce (our reading)

- Which MSs (and spectral windows) of the three projects were used for each HerBS source, and the ALMA band(s) of the real observations
- How the source positions were refined per source (Gaussian fit to own continuum vs another archival observation)
- CO(3-2) rest frequency and velocity-axis definition used for the stacked spectra (mu, sigma in km/s)
- Final channel width and number of channels of the stacked cube, and which spectral window was chosen per MS
- tclean parameters for the real data: imsize, niter, exact threshold, restoringbeam handling
- uvmultifit settings for the real data: initial guesses, size priors, bounds, whether Monte Carlo perturbation was used
- Region and aperture definition used to extract flux density from moment-0 maps for each source
- How D_L was computed (the cosmology is given only as rounded values h approx 0.67, Omega_m approx 0.3)
- How the one-fourth data subset was selected (which integrations or scans)
- Per-observation sensitivity sigma_k values used in the threshold estimate
- Flux-scale calibration choices and uncertainties of the archival MSs
- Version or commit of the ViSta code used for the paper results

## Analysis recipe

1. **Select sample and obtain calibrated measurement sets**: 21 DSFGs with CO(3-2) from ALMA archival projects; calibrated MSs retrieved (mostly) from the EU ARC CalMS service; coordinates and observations checked  
  > "The sample consists of 21 partially resolved or unresolved galaxies, four of which had two available observations" (Application to a real case); "We mostly retrieved calibrated datasets by exploiting the EU ARC CalMS service" (Footnote 1)
   - software: CASA
   - parameter: Unlensed or moderately resolved sources only; spectroscopic redshift required  
  > "Therefore, we select only unlensed and moderately resolved sources that meet the above criteria." (2 The ViSta method)
   - fitting: _not stated_
   - validation: Coordinates and absence of instrumental issues or artifacts verified per source  
  > "For each source, we verified the accuracy of its coordinates and ensured that every observation was free from instrumental issues or artifacts." (Application to a real case)
2. **Center each source at the phase center and correct for primary beam**: phaseshift to the source position, then PHASE_DIR/REFERENCE_DIR/DELAY_DIR and POINTING directions set to zero; visibilities divided by the Gaussian primary-beam response at the source offset  
  > "This phase center shift is performed using the casatasks.phaseshift() function, which is applied to each input MS of the sample" (3.1 Centering); "we divide each visibility by the correction for primary beam attenuation that it would have experienced at its original position in the field of view." (3.1 Centering)
   - software: CASA, casatasks.phaseshift, Python
   - parameter: Primary beam PB(theta) = exp[-4 ln2 (theta nu d / 1.2 c)^2] for a 12-m antenna  
  > "The primary beam (PB) response of an ALMA 12-meter antenna can be approximated by a normalized symmetric Gaussian function that depends on the observing frequency" (3.1 Centering)
   - assumption: Primary beam approximated by a normalized symmetric Gaussian  
  > "can be approximated by a normalized symmetric Gaussian function" (3.1 Centering)
   - fitting: _not stated_
   - validation: _not stated_
3. **Shift visibilities to the rest frame**: Frequencies and dependent SPECTRAL_WINDOW parameters scaled by (1+z); UVW, antenna positions and dish diameter divided by (1+z)  
  > "This transformation requires modifying the frequencies, along with all dependent parameters (for example, the channel spectral resolution and the total bandwidth) by applying the corrective factor $(1+z)$." (3.2 Restframing); "In particular, the visibility coordinates in the main table UVW, the antenna positions in the ANTENNA table POSITION, and the dish diameter DISHDIAMETER must be divided by the corrective factor $1+z$." (3.2 Restframing)
   - software: Python, CASA
   - assumption: Spectroscopic redshift of each source is accurate  
  > "even small errors of a few percent can cause a flux loss of nearly 50% and lead to an increasingly significant broadening of the emission line" (2 The ViSta method)
   - fitting: _not stated_
   - validation: On a mock source the rest-framed image is effectively identical to the original, differing only by the shift to rest-frame frequency  
  > "the resulting image is effectively identical to the original, differing only by the shift to the rest-frame frequency" (5.1 Building simulated ALMA dataset)
4. **Rebin and regrid the spectral axis to a common grid**: mstransform to a common spectral resolution (optional Hanning smoothing first); flagged dummy channels added with flagdata and concat so all MSs have equal channel count, then mstransform to cut and regrid  
  > "to match the widest spectral resolution among the sample and returns a rebinned measurement set" (3.3 Rebinning); "Next, we merge these flagged MS copies back into the original dataset using casatasks.concat()" (3.4 Regridding); "we apply casatasks.mstransform() to cut the measurement set and extract our final spectral cube" (3.4 Regridding)
   - software: CASA, casatasks.mstransform, casatasks.hanningsmooth, casatasks.flagdata, casatasks.concat
   - parameter: Common finer spectral grid set by the dataset with the highest native resolution  
  > "We adopt the spectral sampling of the dataset with the highest native resolution in order to prevent undersampling and preserve the fidelity of narrow spectral features." (2 The ViSta method)
   - fitting: _not stated_
   - validation: _not stated_
5. **Rescale flux to a common reference redshift and concatenate**: Each visibility multiplied by w = D_L^2(z_source)/D_L^2(z_common) x (1+z_common)/(1+z_source), then concat; OBSERVATION table unified so all scans form one observation  
  > "Before combining the measurement sets, we rescale the visibilities of each observation by multiplying them by a correction factor to adjust the flux densities to a common reference redshift." (3.5 Stacking); "we modify the OBSERVATION table so that all scans appear as part of a single observation" (3.5 Stacking)
   - software: CASA, casatasks.concat, casatasks.mstransform
   - parameter: Reference redshift z_common = 2.5 for the real sample  
  > "we did apply a correction for luminosity distance differences, adopting a reference redshift of 2.5" (6 Application to a real case)
   - assumption: No lensing-magnification or other flux-normalization correction applied to the real sample  
  > "as we only applied a correction for the luminosity distance but did not account for other factors such as flux normalization or lensing magnification" (6 Application to a real case)
   - assumption: Flat LambdaCDM with h approx 0.67, Omega_m approx 0.3, Omega_Lambda approx 0.7  
  > "with round parameter values $h\approx 0.67$, $\Omega_m\approx 0.3$ and $\Omega_{\Lambda}\approx 0.7$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
6. **Apply channel-coverage weights**: Per-channel weight w(nu) = sqrt(N_coverage(nu)/N), with weights of repeated observations of the same source divided by the number of repeats  
  > "we account for the number of observations that cover each frequency and apply corresponding statistical weights to each channel." (3.7 Weighting); "We applied a weighting scheme to account for varying frequency coverage across observations and to avoid multiple counting sources with duplicate observations" (6 Application to a real case)
   - software: Python
   - fitting: _not stated_
   - validation: _not stated_
7. **Extract the stacked CO(3-2) spectrum and fit the line**: Three methods: ViSta-uvFit (uvmultifit with a Gaussian model, spatial parameters free in each channel, one fit per channel); ViSta-ImFit (tclean of stacked MS, flux from moment-0-derived size); ImSta-ImFit (classical image stacking). A Gaussian (mu, sigma, A, continuum C) is fitted to each stacked spectrum; a continuum image was also made as post-processing  
  > "We instead kept the spatial parameters of the Gaussian model free in each channel." (6 Application to a real case); "We can model this spectrum by fitting a Gaussian profile, facilitating the characterization of spectral features directly from the visibility data." (3.7 Spectral line fitting in the visibility domain); "As an additional test, we explored estimating the continuum as a post-processing step of the ViSta method." (6 Application to a real case)
   - software: CASA, UVMultiFit, tclean, imfit
   - parameter: uvmultifit with OneFitPerChannel = True, write = residuals; Gaussian or delta model  
  > "The fitting procedure is performed on a per-channel basis by setting OneFitPerChannel = True, providing an estimate of the flux density and its associated uncertainty for each spectral channel." (3.7 Spectral line fitting in the visibility domain)
   - parameter: Natural weighting, Hogbom, cell = 1/5 of the beam major axis  
  > "We define the cell size to be $1/5$ of the major axis of the restoring beam." (3.8 Imaging)
   - assumption: Source size from zero-order moment maps for the image-plane methods  
  > "As we can estimate an approximate source size from the zero order moment maps for our sample, we used the same approach as the simulations" (6 Application to a real case)
   - fitting: Gaussian line profile (mu, sigma, A, C) fitted to the stacked spectra; sampler, priors and likelihood not stated for the real sample  
  > "We can model this spectrum by fitting a Gaussian profile" (3.7 Spectral line fitting in the visibility domain)
   - validation: The three methods agree to roughly 10% in sigma and amplitude; peak position within 3 spectral channels  
  > "The velocity dispersion and the amplitude of the spectral line show good agreement across methods, with differences of approximately 10% in both cases." (6 Application to a real case)
8. **Compare visibility and image stacking SNR at the worst common resolution**: Convolve all datasets to the worst angular resolution, then compare spectra and RMS noise of ViSta-ImFit and ImSta-ImFit  
  > "convolve all datasets to the worst angular resolution available" (6 Application to a real case); "stacking in the uv-plane yields a more effective suppression of noise" (6 Application to a real case)
   - software: CASA, imfit
   - parameter: Common beam 5.063 x 2.820 arcsec  
  > "corresponding to a synthesized beam of $5.063^{\prime\prime} \times 2.820^{\prime\prime}$" (6 Application to a real case)
   - fitting: _not stated_
   - validation: Same procedure was first tested on simulated data  
  > "we refer to the procedure described in Sect. [5.2.2.3](#sec:lowest_res)" (6 Application to a real case)
9. **Test with artificially reduced sensitivity**: One fourth of the available data of each observation selected, analysis repeated at native resolution and at the worst resolution  
  > "we selected one fourth of the available data for each observation and repeated the analysis" (6 Application to a real case)
   - software: CASA
   - fitting: _not stated_
   - validation: SNR gain of ViSta over image stacking grows from about 39% (full data) to about 53% (reduced data)  
  > "the SNR increases from 3.41 to 5.24, resulting in a relative gain of about 53%" (6 Application to a real case)
10. **Validate ViSta on simulated ALMA datasets**: 50 mock sources per case simulated with simobserve plus custom noise; compare ViSta-uvFit, ViSta-ImFit and ImSta-ImFit for unresolved and resolved (5 arcsec FWHM) sources at native size, fitted size and lowest resolution, and for continuum  
  > "to simulate ALMA observation for each source" (5.1 Building simulated ALMA dataset); "we will refer to as ViSta-uvFit, and in the image domain after imaging the stacked data, referred to as ViSta-ImFit" (5.2 Results)
   - software: CASA, simobserve, UVMultiFit, imfit, Python
   - parameter: Unresolved case: flux taken as peak value in the image; resolved case: flux in circular aperture of radius 3 sigma of the Gaussian  
  > "using a circular aperture with a radius of 3$\sigma$ (where $\sigma$ is the standard deviation of the Gaussian profile)" (5.2.2.1 Native Source Size at Native Resolution)
   - assumption: Continuum subtraction and weighting skipped; no redshift flux-scaling correction because all mock fluxes equal  
  > "We did not perform any correction for flux scaling due to redshift differences" (5.1 Building simulated ALMA dataset)
   - fitting: Gaussian spectral fit obtained by a Monte Carlo approach perturbing data by their uncertainties and averaging the fits  
  > "The fit was obtained through a Monte Carlo approach, by perturbing the data according to their uncertainties and averaging the resulting fits." (5.2.1 Unresolved Source)
   - validation: Compared with the expected average emission from uncorrupted observations (about 90% accuracy for point sources)  
  > "recovering the true emission with about 90% accuracy" (5.2.1 Unresolved Source)

## Software

- **CASA** 6.6: Handling and manipulating MSs, imaging and analysis (main analysis in version 6.6; simobserve in CASA v.6)  
  > "we mainly employed version 6.6 of the Common Astronomy Software Applications (CASA) package, which is the primary data processing software for ALMA" (3 Applications to the ALMA Science Archive)
- **casatasks.phaseshift** : Shifting the phase center to the refined source position  
  > "This phase center shift is performed using the casatasks.phaseshift() function, which is applied to each input MS of the sample" (3.1 Centering)
- **casatasks.mstransform** : Spectral rebinning, regridding and extraction of a single observation ID  
  > "Initially, the spectral resolution of each observation is adjusted using the casatasks.mstransform() tool" (3.3 Rebinning)
- **casatasks.hanningsmooth** : Optional Hanning smoothing before rebinning  
  > "one can first apply a Hanning smoothing filter with casatasks.hanningsmooth()" (3.3 Rebinning)
- **casatasks.flagdata** : Flagging copies of the MS to create placeholder channels  
  > "we then run casatasks.flagdata(), the all-purpose CASA flagging task that marks data as invalid" (3.4 Regridding)
- **casatasks.concat** : Concatenating the rest-framed MSs into the stacked dataset  
  > "After this rescaling, the measurement sets are concatenated using the CASA" (3.5 Stacking)
- **casatasks.uvcontsub** : Optional uv-domain continuum fitting and subtraction (zero-order polynomial typical); not used for the real-sample line stacking  
  > "This is achieved using casatasks.uvcontsub, which performs continuum fitting and subtraction in the" (3.6 Continuum Subtraction and analysis)
- **tclean** : Imaging stacked visibilities into cubes (cube mode) or continuum images (mfs)  
  > "The final step involves transforming the stacked visibilities into the image plane using the casatasks.tclean() task from the CASA software package" (3.8 Imaging)
- **casatasks.imfit** : Two-dimensional Gaussian fit of images to measure flux and size  
  > "it is preferable to perform a two-dimensional Gaussian fit with casatasks.imfit()" (4.2 Partially-Resolved Sources)
- **casatasks.imstat** : Direct flux measurement within a tailored aperture when the size is known  
  > "one could measure the flux density directly using casatasks.imstat()" (4.2 Partially-Resolved Sources)
- **simobserve** CASA v.6: Simulating ALMA observations of the mock sources  
  > "in the Common Application Software for Astronomy (CASA) v.6 to simulate ALMA observation for each source" (5.1 Building simulated ALMA dataset)
- **UVMultiFit** : Fitting Gaussian or delta models directly to stacked visibilities per channel  
  > "we utilize the UVMultiFit package, a versatile tool designed to fit models directly on interferometric visibility data within the CASA environment" (3.7 Spectral line fitting in the visibility domain)
- **CARTA** : Visualizing the stacked image products  
  > "These products can then be visualized with an image viewer such as CARTA, to analyze the spatial and spectral properties of the detected emission." (3.8 Imaging)
- **Astropy, SciPy, NumPy, Matplotlib** : Data structures and units, numerical computation and plotting  
  > "including Astropy for managing astronomical data structures and units, SciPy and NumPy for numerical computations, and Matplotlib for data visualization." (3 Applications to the ALMA Science Archive)
- **ViSta** : The authors' visibility stacking code (GitHub repository martitors/ViSta)  
  > "https://github.com/martitors/ViSta" (Summary and outlook)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak SNR of stacked central channel, 50 mock point sources (ViSta-ImFit) | 17.3 | not stated | dimensionless | 10 | giving a final peak SNR of approximately $17.3$ on stacking |
| Reduction of average channel rms from stacking 50 mock datasets | factor ~8 (from ~1.2 mJy) | not stated | dimensionless | 10 | by a factor $\sim 8$ consistent with this scaling |
| Accuracy of recovered line emission for point sources, all three methods | about 90% | not stated | percent | 10 | recovering the true emission with about 90% accuracy |
| Central-channel flux densities at lowest resolution (two methods as listed, mock extended source) | 2.070 and 2.566 | not stated | mJy | 10 | respectively $2.070$ and $2.566$ mJy |
| Gain of ViSta over image-plane stacking in the central channel (mock extended source, lowest resolution) | ~54% | not stated | percent | 10 | a gain of $\sim54\%$ in the central channel compared to the image-plane stacking |
| Mock continuum peak SNR, ImSta-ImFit | 6.966 (peak 0.404 mJy/beam, rms 0.058 mJy/beam) | not stated | dimensionless | 10 | the peak flux is $0.404$ mJy/beam with an RMS noise of $0.058$ mJy/beam, giving a SNR of 6.966 |
| Mock continuum peak SNR, ViSta-ImFit | 8.216 (peak 0.419 mJy/beam, rms 0.051 mJy/beam) | not stated | dimensionless | 10 | the peak flux is $0.419$ mJy/beam and the RMS noise $0.051$ mJy/beam, resulting in a SNR of 8.216 |
| Gaussian fit to stacked CO(3-2), ViSta-uvFit: mu, sigma, A, C | mu = -16.8184 km/s; sigma = 264.9165 km/s; A = 4.5835 mJy; C = 0.4636 mJy | not stated (omitted in table) | km/s, km/s, mJy, mJy | 7 | -16.8184 / 264.9165 / 4.5835 / 0.4636 |
| Gaussian fit to stacked CO(3-2), ViSta-ImFit: mu, sigma, A, C | mu = -52.6187 km/s; sigma = 317.8469 km/s; A = 4.9921 mJy; C = 0.2579 mJy | not stated (omitted in table) | km/s, km/s, mJy, mJy | 7 | -52.6187 / 317.8469 / 4.9921 / 0.2579 |
| Gaussian fit to stacked CO(3-2), ImSta-ImFit: mu, sigma, A, C | mu = 3.3452 km/s; sigma = 262.5233 km/s; A = 5.0738 mJy; C = 0.3467 mJy | not stated (omitted in table) | km/s, km/s, mJy, mJy | 7 | 3.3452 / 262.5233 / 5.0738 / 0.3467 |
| Average continuum flux density of the stacked real sample | 0.832 | 0.064 | mJy | 7 | we estimate a continuum average flux density of $0.832 \pm 0.064$ mJy |
| Peak SNR gain, ViSta-ImFit vs ImSta-ImFit at worst resolution, full-sensitivity data | 7.837 to 10.924 (~39%) | not stated | dimensionless | 8 | Quantitatively, the SNR increases from 7.837 for; corresponding to an improvement of approximately 39% |
| Peak SNR gain, ViSta-ImFit vs ImSta-ImFit at worst resolution, one-fourth data | 3.41 to 5.24 (~53%) | not stated | dimensionless | 9 | the SNR increases from 3.41 to 5.24, resulting in a relative gain of about 53% |
| Worst angular resolution (common convolution beam) of the real sample | 5.063 x 2.820 | not stated | arcsec | 8 | corresponding to a synthesized beam of $5.063^{\prime\prime} \times 2.820^{\prime\prime}$ |

## Qualitative findings

- For unresolved mock sources ViSta-uvFit, ViSta-ImFit and ImSta-ImFit all recover the Gaussian line profile; they slightly overestimate the (weak) continuum  
  > "All three methods successfully reproduce the Gaussian line profile" (5.2.1 Unresolved Source); "However, they appear to slightly overestimate the continuum level." (5.2.1 Unresolved Source)
- For extended mock sources ViSta-uvFit gives the closest match to the expected profile, while ViSta-ImFit slightly overestimates the peak because of heterogeneous beams  
  > "The direct visibility‑plane extraction via Vista-uvFit provides the closest match to the expected profile" (5.2.2.1 Native Source Size at Native Resolution)
- On the real DSFG sample the three methods give consistent line parameters, broadly consistent with literature, but the paper stresses this is a method test, not a definitive flux  
  > "This application to the real dataset is intended primarily as a test and comparison of the ViSta method" (6 Application to a real case)

## Claim tuples

- H: ViSta performs as well as image-plane stacking for point-like sources | E: 50 simulated point-like sources stacked with ViSta-uvFit, ViSta-ImFit and ImSta-ImFit | R: All three methods recover the line with about 90% accuracy; peak SNR of 17.3 after stacking 50 sources | F: ViSta is reliable for unresolved sources with performance comparable to classical stacking | **supported**
- H: ViSta is better than image-plane stacking for faint, extended sources below the noise level | E: Mock 5 arcsec Gaussian sources analysed at native size, fitted size and lowest common resolution, plus continuum | R: ViSta gives lower noise and more accurate flux; continuum peak SNR 8.216 vs 6.966 (about 18% gain) | F: Visibility-domain stacking preserves faint extended emission better | **supported**
- H: ViSta and image stacking give consistent CO(3-2) line properties when the sources are individually detected | E: Stacking 21 archival HerBS galaxies with ViSta-uvFit, ViSta-ImFit and ImSta-ImFit and fitting a Gaussian | R: sigma ~265, ~318 and ~263 km/s and amplitudes 4.58 to 5.07 mJy; sigma and amplitude agree to ~10% | F: The methods give similar flux estimates, consistent with prior literature | **supported**
- H: ViSta gains more over image stacking as individual sources become undetectable | E: Used one fourth of the data per observation and convolved to the worst resolution | R: SNR gain rises from about 39% (full data) to about 53% (one-fourth data) | F: Visibility stacking becomes progressively more advantageous in the noise-dominated regime | **supported**

## Reasoning

- Why this data: Archival ALMA data of DSFGs are numerous but inhomogeneous, so stacking them could allow detection of faint lines  
  > "Stacking of archival datasets could be a gold mine for investigating the DSFG population and improving the detectability of the spectral lines discussed above." (Introduction)
- Why this method: Stacking before imaging avoids non-Gaussian noise and imaging approximations of image-plane stacking  
  > "is demonstrated to be more efficient than stacking in the image domain" (Introduction); "the noise no longer remains Gaussian upon imaging the visibilities" (Introduction)
- Alternative: Classical image-plane stacking (ImSta-ImFit) used as the baseline comparison  
  > "These results will then be compared with those obtained from the classical image-plane stacking procedure" (5.1 Building simulated ALMA dataset)
- Alternative: Continuum subtraction and channel weighting are optional and may suppress marginal lines, so they were skipped in the simulations  
  > "continuum removal may not be recommended when the line emission does not significantly stand out from the continuum" (2 The ViSta method)
- How they decided it was enough: _not stated_
- Limitation (authors): The real-sample result is not a precise line measurement: only the luminosity-distance correction was applied, with no flux normalization or lensing correction  
  > "the result presented in this paper should not be interpreted as a precise measurement of the line emission" (6 Application to a real case)
- Limitation (authors): Handling of strongly lensed and highly resolved sources is still under investigation and not yet validated  
  > "However, these strategies are yet to be further validated and could be refined by future studies." (4.3 Resolved and High-Resolution Sources)
- Limitation (authors): Stacked data products can exceed several hundred gigabytes, beyond standard tools  
  > "stacked data products can exceed several hundred gigabytes" (Summary and outlook)
- Caveat (inferred, ours): The real sample is small (21 sources, 25 observations) and all sources were detected individually, so the main real-data comparison is not a low-SNR test
- Caveat (inferred, ours): The quoted 54% gain for the mock extended source does not follow from flux densities 2.070 and 2.566 mJy (about 24%); the metric is unclear
- Caveat (inferred, ours): No uncertainties given for the Gaussian fit parameters in Table 2, so agreement between methods cannot be judged statistically
- Caveat (inferred, ours): Best-fit mu differs by about 50 km/s between methods; no systematic study of sources of this offset
- Caveat (inferred, ours): No lensing, flux-scale or per-source SNR weighting applied, so the stacked flux is not physically calibrated
- Caveat (inferred, ours): Simulations use identical sources at fixed offsets with uniform properties; real heterogeneity (sizes, line widths) is not tested
- Caveat (inferred, ours): SNR comparison depends on the choice of aperture and convolution to a common beam, which favors a particular estimator

## Reproducibility

- Data public (paper): Data are archival ALMA observations stored in the ALMA Science Archive  
  > "a small sample of DSFG observations stored in the ASA" (Introduction)
- Products in archive: Calibrated MSs obtained via the EU ARC CalMS service  
  > "We mostly retrieved calibrated datasets by exploiting the EU ARC CalMS service" (Footnote 1)
- Code: Basic ViSta code released on GitHub (martitors/ViSta)  
  > "will be made available at the time of publication" (Summary and outlook); "https://github.com/martitors/ViSta" (Summary and outlook)
- Missing: Mapping from each HerBS source to the specific MS and spectral window in the three projects
- Missing: uvmultifit and tclean settings for the real sample (priors, imsize, niter, threshold)
- Missing: Exact aperture/region definitions for flux extraction
- Missing: CO(3-2) rest frequency and velocity convention used
- Missing: The exact subset of data used in the one-fourth sensitivity test
- Missing: Version of the ViSta code used
- Data volume (inferred): Likely tens of GB of calibrated MSs for 25 observations of 21 sources (CalMS products); stacked intermediates add more
- Score (inferred): 3/5, Public archival data, named projects and sources, a detailed step-by-step recipe, released code and numeric results; but many real-data settings (spectral windows, fit priors, apertures, subset choice) are not given
- Rediscovery candidate: yes, Data are public in the ALMA archive, the pipeline is described step by step with released code, and the results (SNR gains, Gaussian parameters) are numeric; the simulations are fully specified

## Links

- Method: (cite: Hill2024) (Reported a gain of about 1.2 from uv-plane over image-plane stacking in an ALMA archival combination analysis)
- Method: (cite: massardi21) (ARI-L project products used as calibrated data)
- Method: (cite: uvmultifit) (UVMultiFit package for visibility-domain fits)
- Companion: BEARS I, II, III (cite: bearsI; bearsII; bearsIII) (Source sample, spectroscopic redshifts and comparison for the CO(3-2) line properties)
- Companion: Torsello et al. in prep. (Planned application of ViSta to CO SLEDs and line ratios in DSFGs)
- Related: BEARS I-III
- Related: HerBS
- Related: ARI-L (CalMS products)

## Checks

```json
{
 "quotes": 146,
 "quotes_ok": 146,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 124,
  "stated": 89,
  "rate": 0.718
 },
 "evidence_ok": true
}
```
