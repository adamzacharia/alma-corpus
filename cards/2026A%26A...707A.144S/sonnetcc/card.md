# Spatially resolved star formation relations in local luminous infrared galaxies along the complete merger sequence

`2026A&A...707A.144S` | Astronomy and Astrophysics 2026 | first author: Sánchez-García, M. | arXiv: 2601.08980 | DOI: 10.1051/0004-6361/202555198

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How do spatially resolved star formation relations (KS law, SFE vs gas boundedness and velocity dispersion) at ~100 pc scales in 27 nearby LIRGs change along the merger sequence, using beam-sized regions versus physical gas clumps  
  > "we study the relations between star-formation (SF) and molecular gas surface density as a function of the interaction stage by (1) defining beam-sized (unresolved, line-of-sight) regions and (2) identifying actual gas clumps and physical structures within the galaxies." (abstract)
- Target **27 individual galaxies in 23 GOALS LIRG systems (isolated, pairs, early/mid/late mergers)**: coordinates per-galaxy RA/Dec in Table 1 (from Stierwalt2013)  
  > "Our sample is drawn from the Great Observatories All-sky LIRG Survey" (2.1 Sample selection); "Col. (3) and (4): right ascension (hours, minutes, seconds) and declination (degrees, arcminutes, arcseconds) from (cite: Stierwalt2013). Col. (5): Redshift (cite: Stierwalt2013). Col. (6): Luminosity distance from (cite: Armus2009)." (Table 1 notes); z/distance per-galaxy z and D_L (Mpc) in Table 1  
  > "Our sample is drawn from the Great Observatories All-sky LIRG Survey" (2.1 Sample selection); "Col. (3) and (4): right ascension (hours, minutes, seconds) and declination (degrees, arcminutes, arcseconds) from (cite: Stierwalt2013). Col. (5): Redshift (cite: Stierwalt2013). Col. (6): Luminosity distance from (cite: Armus2009)." (Table 1 notes); distance from Redshift and coordinates from Stierwalt2013; luminosity distance from Armus2009  
  > "Our sample is drawn from the Great Observatories All-sky LIRG Survey" (2.1 Sample selection); "Col. (3) and (4): right ascension (hours, minutes, seconds) and declination (degrees, arcminutes, arcseconds) from (cite: Stierwalt2013). Col. (5): Redshift (cite: Stierwalt2013). Col. (6): Luminosity distance from (cite: Armus2009)." (Table 1 notes)

## Data provenance

- ALMA projects: 2013.1.00243.S, 2013.1.00271.S, 2015.1.00714.S, 2017.1.00255.S, 2017.1.00395.S
- bands: Band 6  
  > "We used ALMA Band 6 observations of the CO(2–1) emission line from ALMA proposal 2017.1.00395.S (PI: T. Díaz-Santos)" (2.2 CO(2–1) ALMA data)
- frequencies and spectral setup: Final cubes with 7.8 MHz (~10 km/s) channels; CO(2-1)  
  > "The final data cubes have channels of 7.8 MHz ($\sim$10 km s$^{-1}$) for the sample." (2.2 CO(2–1) ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 13 of 23 systems compact + extended; 10 extended only  
  > "13 were observed using two configurations, compact and extended, and 10 using only the extended configuration." (2.2 CO(2–1) ALMA data)
- baselines: _not stated_
- angular resolution: 48–112 pc (~0.1-0.3 arcsec, per-galaxy beams in Table 2); common ~90 pc scale for part of sample  
  > "providing a spatial resolution of 48–112 pc" (2.2 CO(2–1) ALMA data)
- max recoverable scale: ~6'' to ~11'' (~1.4-3.5 kpc) for compact+extended; ~3'' (~1.1 kpc) for extended-only  
  > "The maximum recoverable scale (MRS) for the compact plus extended configuration data ranges between $\sim$6$\ensuremath{''}$ and $\sim$11$\ensuremath{''}$ ($\sim$1.4 and 3.5 kpc)." (2.2 CO(2–1) ALMA data); "In the case of the extended-only configuration observations, the MRS is $\sim$3$\ensuremath{''}$ ($\sim$1.1 kpc)." (2.2 CO(2–1) ALMA data)
- sensitivity: 1 sigma line sensitivity per ~10 km/s channel, per galaxy in Table 2 (0.21 to 0.89 mJy/beam)  
  > "Col. (5): 1$\sigma$ line sensitivity per channel (width of $\sim$ 10 km/s) of the CO(2–1) observations." (Table 2 notes)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Five ALMA projects with different PIs; sample completed with data described in SG2022  
  > "Principal investigator of the ALMA project: MPS: Miguel Pereira-Santaella (2017.1.00255.S), KS: Kazimierz Sliwa (2015.1.00714.S), LC1: Luis Colina (2013.1.00271.S), LC2: Luis Colina (2013.1.00243.S) and TDS: Tanio Díaz-Santos (2017.1.00395.S)" (Table 2 notes); "completed the sample with the data described in (cite: SG2022)" (2.2 CO(2–1) ALMA data)
- Line: CO J = 2-1 (not stated)
- Other facility **HST (NICMOS and WFC3)**: Archival continuum-subtracted narrow-band Paα 1.87 um (NICMOS) and Paβ 1.28 um (WFC3) images tracing star formation  
  > "We used the continuum subtracted NIR narrow-band Pa$\alpha$ 1.87 $\mu$m and Pa$\beta$ 1.28 $\mu$m images taken with the NICMOS and WFC3 instruments, respectively" (2.3 HST/NICMOS and HST/WFC3 data)
- Other facility **VLT/SINFONI**: Brδ and Brγ line maps used to derive A_K for extinction correction of Paα/Paβ  
  > "we use the Br$\delta$ and Br$\gamma$ line maps observed with the SINFONI instrument on the Very Large Telescope (VLT) to derive A$_{K}$." (3.2 Calculating physical properties)
- Other facility **Spitzer 3.6 um**: Images used to estimate galaxy inclinations  
  > "The inclination is estimated from Spitzer 3.6 $\mu$m band images, which have a PSF of $\sim$1.7$\ensuremath{''}$" (3.2 Calculating physical properties)
- Other facility **Gaia DR3**: Catalogue for HST astrometry correction  
  > "corrected the astrometry using stars within the NICMOS FoV" (2.3 HST/NICMOS and HST/WFC3 data)
- Other facility **GOALS**: Parent LIRG sample  
  > "Our sample is drawn from the Great Observatories All-sky LIRG Survey" (2.1 Sample selection)
- External data: Coordinates, redshifts, IR luminosities and merger-stage classification of the sample  
  > "The merger stage classification of our sample is based on (cite: Stierwalt2013), except for three objects" (2.1 Sample selection) [from (cite: Stierwalt2013)]
- External data: Luminosity distances of the sample  
  > "Col. (6): Luminosity distance from (cite: Armus2009)." (Table 1 notes) [from (cite: Armus2009)]
- External data: CO(2-1)/CO(1-0) ratio R21 = 0.7 from single-dish CO of IC 4687  
  > "we use a CO(2–1)/CO(1–0) ratio (R$_{21}$) of 0.7, obtained from single-dish CO data of the LIRG IC 4687 (cite: Albrecht2007)." (3.2 Calculating physical properties) [from (cite: Albrecht2007)]
- External data: Galactic CO-to-H2 conversion factor 4.35  
  > "We also use a Galactic CO-to-H$_{2}$ conversion factor, $\alpha^{1-0}_{CO}$ = 4.35 M$_{\odot}$pc$^{-2}$(K km s$^{-1}$)$^{-1}$ (cite: Bolatto2013)." (3.2 Calculating physical properties) [from (cite: Bolatto2013)]
- External data: Halpha SFR calibration, Kroupa IMF, Halpha/Paalpha = 8.6 and Halpha/Pabeta = 17.6  
  > "we use the H$\alpha$ calibration (cite: Kennicutt2012), which assumes a (cite: Kroupa2001) initial mass function, and a H$\alpha$/Pa$\alpha$ ratio of 8.6 and a H$\alpha$/Pa$\beta$ ratio of 17.6 (cite: Osterbrock2006)." (3.2 Calculating physical properties) [from (cite: Kennicutt2012); (cite: Kroupa2001); (cite: Osterbrock2006)]
- External data: SINFONI Brδ/Brγ maps (FoV 8x8 to 12x12 arcsec) used for extinction  
  > "These maps have effective FoV between 8$\ensuremath{''}\times8\ensuremath{''}$ and 12$\ensuremath{''}\times12\ensuremath{''}$ (cite: piqueras2013)." (3.2 Calculating physical properties) [from (cite: piqueras2013)]
- External data: Reduction of HST Paβ images  
  > "For details on the data reduction we refer the reader to (cite: SG2022) for Pa$\alpha$ observations and (cite: Larson2020) for Pa$\beta$ observations." (2.3 HST/NICMOS and HST/WFC3 data) [from (cite: Larson2020)]
- External data: Spitzer-based inclination method and values  
  > "as presented in (cite: Pereira2011)" (3.2 Calculating physical properties) [from (cite: Pereira2011)]
- External data: sigma_v-dependent alpha_CO prescription (log alpha_CO = -0.59 log sigma + 0.90) used only in a robustness test  
  > "By applying the $\sigma_{v}$-based $\alpha_{CO}$ prescription" (7 Comparison and effects of the selected CO-to-H2 conversion factor) [from (cite: Teng2023; Teng2024)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA data reduction software CASA (pipeline vs manual not specified)  
  > "The data were calibrated using the standard ALMA data reduction software, CASA" (2.2 CO(2–1) ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% for ALMA fluxes  
  > "We assume an uncertainty of about 10% for the ALMA fluxes" (3.2 Calculating physical properties)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "For the cleaning we used the Briggs weighting with a robustness parameter of 0.5" (2.2 CO(2–1) ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, order 0 baseline  
  > "We subtracted the continuum emission in the *uv* plane using an order 0 baseline." (2.2 CO(2–1) ALMA data)
- line free channels: _not stated_
- primary beam correction: applied to data cubes  
  > "We applied the primary beam correction to the data cubes." (2.2 CO(2–1) ALMA data)
- array combination: _not stated_
- smoothing: Cubes of 30% of the sample (resolution better than 80 pc) convolved to 90 pc; 5 objects (19%) kept at original resolution up to ~110 pc  
  > "We convolved to 90 pc the data cubes of 30% of the sample with spatial resolutions higher than 80 pc." (2.2 CO(2–1) ALMA data)
- final beam: 48–112 pc, per-galaxy beams in Table 2  
  > "providing a spatial resolution of 48–112 pc" (2.2 CO(2–1) ALMA data)
- final rms: 1 sigma per ~10 km/s channel, per galaxy in Table 2  
  > "Col. (5): 1$\sigma$ line sensitivity per channel (width of $\sim$ 10 km/s) of the CO(2–1) observations." (Table 2 notes)

### Inherited from earlier work

- Moment 0/2 map methodology (3xRMS masked maps, code on GitHub)  
  > "We use the first method to follow the methodology of (cite: SG2022) and extend the study to a larger sample of galaxies." (2.2 CO(2–1) ALMA data) [from (cite: SG2022)]
- Reduction of HST Paα images  
  > "For details on the data reduction we refer the reader to (cite: SG2022) for Pa$\alpha$ observations and (cite: Larson2020) for Pa$\beta$ observations." (2.3 HST/NICMOS and HST/WFC3 data) [from (cite: SG2022); (cite: Larson2020)]
- Extinction correction method using SINFONI Br lines  
  > "For an in-depth explanation of the extinction correction method, we refer the reader to (cite: SG2022)." (3.2 Calculating physical properties) [from (cite: SG2022)]
- Beam-sized region definition (non-overlapping apertures on CO maxima)  
  > "With this method we obtain independent, unresolved, non-overlapping regions centred on local emission maxima that cover all the CO emission in each galaxy (cite: SG2022)." (3.1.1 Beam-sized region analysis) [from (cite: SG2022)]
- Calibration and imaging of the 13 galaxies also in SG2022 (two configurations)  
  > "completed the sample with the data described in (cite: SG2022)" (2.2 CO(2–1) ALMA data) [from (cite: SG2022)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual scripts were used for calibration
- Flux, bandpass and phase calibrators and any self-calibration
- Spectral setup: rest frequency, number of windows, continuum bandwidth, line-free channels for the order-0 continuum fit
- tclean parameters: deconvolver, cell size, image size, threshold, masks, multiscale scales, and how compact and extended configurations were combined
- Observing dates, time on source and baseline ranges per project
- How RMS_CO and RMS_Pa background noise were measured (region, per channel or per map)
- Astrodendro version and how clump SFR/mass were summed over leaf pixels
- How clump effective radius and sigma_v were derived (beam deconvolution, moment-2 weighting)
- Per-galaxy A_K values and how the SINFONI extinction was applied to regions outside the SINFONI FoV
- MARS fit settings (number of breakpoints, selection criterion) and ODR weighting/uncertainties
- How AGN pixels were masked
- Details of the sigma_v-dependent alpha_CO prescription, given as private communication

## Analysis recipe

1. **Calibrate and image CO(2-1) cubes**: Calibration with CASA; uv-plane continuum subtraction; cleaning with Briggs weighting  
  > "The data were calibrated using the standard ALMA data reduction software, CASA" (2.2 CO(2–1) ALMA data); "For the cleaning we used the Briggs weighting with a robustness parameter of 0.5" (2.2 CO(2–1) ALMA data)
   - software: CASA
   - parameter: robust = 0.5  
  > "a robustness parameter of 0.5" (2.2 CO(2–1) ALMA data)
   - parameter: Continuum subtracted in uv plane with order 0 baseline  
  > "We subtracted the continuum emission in the *uv* plane using an order 0 baseline." (2.2 CO(2–1) ALMA data)
   - parameter: Channels of 7.8 MHz (~10 km/s)  
  > "The final data cubes have channels of 7.8 MHz ($\sim$10 km s$^{-1}$) for the sample." (2.2 CO(2–1) ALMA data)
   - fitting: _not stated_
   - validation: Integrated ALMA fluxes agree with single-dish CO(2-1) within 15% for a few objects  
  > "the integrated ALMA and single-dish fluxes agree within 15%" (2.2 CO(2–1) ALMA data)
2. **Homogenise spatial resolution of ALMA and HST maps**: Convolve ALMA cubes to a common ~90 pc scale where finer; convolve HST images with a Gaussian kernel to the ALMA resolution  
  > "A common spatial scale of $\sim$90 pc was defined in order to have a homogeneous data set." (2.2 CO(2–1) ALMA data); "were convolved with a Gaussian kernel to match the resolution of the ALMA maps at $\sim$100 pc." (2.3 HST/NICMOS and HST/WFC3 data)
   - parameter: 30% of sample with resolution better than 80 pc convolved to 90 pc; 5 objects (19%) left at original resolution up to ~110 pc  
  > "There are 5 objects (three sources where two of them are galaxy pairs), representing 19% of the sample, with an original resolution of up to $\sim$110 pc." (2.2 CO(2–1) ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Prepare HST Paα/Paβ images**: Background subtraction, astrometric alignment to Gaia DR3 stars (or to ALMA features for three objects), rotation to north-up  
  > "To obtain the final images, we subtracted the background emission and corrected the astrometry using stars within the NICMOS FoV" (2.3 HST/NICMOS and HST/WFC3 data); "After that, the images were rotated to have the standard north-up, east-left orientation." (2.3 HST/NICMOS and HST/WFC3 data)
   - parameter: Three objects (MCG-02-33-098 E/W, IC4518 E) aligned to ALMA continuum and CO(2-1) features instead of Gaia stars  
  > "we adjusted the astrometry using the NICMOS counterparts of multiple bright structures detected in both the ALMA continuum and CO(2–1) maps." (2.3 HST/NICMOS and HST/WFC3 data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Make CO(2-1) moment 0 and 2 maps**: Two versions: channel pixels masked below 3xRMS, and unmasked  
  > "i) masking pixels in each channel map with fluxes \< 3$\times$RMS$_{CO}$, where RMS$_{CO}$ is the background noise" (2.2 CO(2–1) ALMA data); "ii) without applying any masking or clipping to the data." (2.2 CO(2–1) ALMA data)
   - software: moment_maps (GitHub code of SG2022)
   - parameter: 3xRMS_CO clipping for method i  
  > "masking pixels in each channel map with fluxes \< 3$\times$RMS$_{CO}$" (2.2 CO(2–1) ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
5. **Define beam-sized regions and extract SFR**: Circular apertures of ~100 pc diameter on CO moment-0 maxima (3xRMS map), non-overlapping, placed in order of descending pixel intensity; applied to Pa maps  
  > "we define circular apertures centred on local maxima in the CO(2–1) emission maps constructed with the 3$\times$RMS$_{CO}$ procedure" (3.1.1 Beam-sized region analysis); "Then we defined circular regions using as centre the pixels in order of descending intensity to prevent any overlap between the regions." (3.1.1 Beam-sized region analysis)
   - parameter: Aperture diameter ~100 pc  
  > "The apertures have a fixed diameter of $\sim$100 pc, corresponding to the spatial resolution of the data." (3.1.1 Beam-sized region analysis)
   - parameter: Pa detection when above 3xRMS_Pa  
  > "We considered Pa$\alpha$ and Pa$\beta$ as detections when the line emission is above 3$\times$RMS$_{Pa}$." (3.1.1 Beam-sized region analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **Identify molecular gas clumps with dendrograms**: Astrodendro on non-masked CO(2-1) moment-0 maps; leaves taken as clumps; same leaf footprints applied to Pa maps  
  > "We applied Astrodendro to the non-masked CO(2–1) moment-0 maps, i.e., without any 3$\times$RMS$_{CO}$ clipping" (3.1.2 Dendrogram analysis); "we measure the hydrogen recombination line emission from the Pa$\alpha$ and Pa$\beta$ maps using the same spatial coordinates and leaf structures identified in the CO(2–1) clumps." (3.1.2 Dendrogram analysis)
   - software: Astrodendro
   - parameter: min_value = 1xRMS_CO, min_delta = 1xRMS_CO, min_npix = 80% of a beam area; final clumps must exceed 3xRMS_CO  
  > "`min_value` = 1$\times$RMS$_{CO}$ (see below for further constraints), `min_delta` = 1$\times$RMS$_{CO}$, `min_npix` = 80$\%$ of a beam (PSF) area for ALMA data." (3.1.2 Dendrogram analysis); "we impose a final constraint that all identified clumps must have an emission greater than 3$\times$RMS$_{CO}$, to avoid noise spikes." (3.1.2 Dendrogram analysis)
   - fitting: _not stated_
   - validation: Compared clump identification between single and combined configurations (IC 5179); also tested alternative thresholds for central regions  
  > "We find consistent clump identification between both datasets." (3.1.2 Dendrogram analysis); "We tested several combinations of parameters in the clump-finding algorithm to evaluate whether this absence could be driven by the merging of bright structures" (4.1.1 Kennicutt-Schmidt law)
7. **Derive gas mass, SFR, extinction and inclination corrections**: Gas mass from CO(2-1) with R21 and Galactic alpha_CO; SFR from extinction-corrected Paα/Paβ via the Halpha calibration; surface densities corrected for inclination from Spitzer 3.6 um isophote fits  
  > "we use a CO(2–1)/CO(1–0) ratio (R$_{21}$) of 0.7, obtained from single-dish CO data of the LIRG IC 4687 (cite: Albrecht2007)." (3.2 Calculating physical properties); "All the $\Sigma_{H_{2}}$ and $\Sigma_{SFR}$ values are corrected for the inclination of each galaxy" (3.2 Calculating physical properties)
   - software: isophote (photutils)
   - parameter: R21 = 0.7; alpha_CO(1-0) = 4.35 Msun pc^-2 (K km/s)^-1  
  > "We also use a Galactic CO-to-H$_{2}$ conversion factor, $\alpha^{1-0}_{CO}$ = 4.35 M$_{\odot}$pc$^{-2}$(K km s$^{-1}$)$^{-1}$ (cite: Bolatto2013)." (3.2 Calculating physical properties)
   - parameter: Halpha/Paα = 8.6, Halpha/Paβ = 17.6; Kennicutt2012 calibration with Kroupa IMF  
  > "a H$\alpha$/Pa$\alpha$ ratio of 8.6 and a H$\alpha$/Pa$\beta$ ratio of 17.6 (cite: Osterbrock2006)" (3.2 Calculating physical properties)
   - parameter: A_K from SINFONI Brδ and Brγ maps, range 0.95±0.60 to 1.98±1.29 mag  
  > "The estimated A$_{K}$ values in this work range from 0.95$\pm$0.60 to 1.98$\pm$1.29 mag." (3.2 Calculating physical properties)
   - assumption: Galactic alpha_CO appropriate (not ULIRG-like) for the sample; metallicity gradient effect 20-30% at r<5 kpc  
  > "We do not expect that a lower conversion factor typical of ULIRGs (cite: Papadopoulos2012) is appropriate for our targets." (3.2 Calculating physical properties); "the expected variation in the conversion factor due to metallicity gradients at $r<5$ kpc is 20-30$\%$." (3.2 Calculating physical properties)
   - assumption: Flux uncertainties ~10% for ALMA and ~15-20% for NICMOS  
  > "We assume an uncertainty of about 10% for the ALMA fluxes (see ALMA Technical Handbook [^8]), and $\sim$15–20% for the NICMOS fluxes (cite: AH2006; Boker1999)." (3.2 Calculating physical properties)
   - fitting: Inclination = mean of fitted-ellipse values unaffected by PSF or structure; uncertainty = standard deviation  
  > "the inclination value is determined as the mean inclination of the fitted ellipses that are unaffected by the PSF of the images or the structure of the galaxy." (3.2 Calculating physical properties)
   - validation: Verified main conclusions do not change significantly when inclination correction is omitted for mid/late mergers  
  > "We also verified that our main conclusions do not change significantly when the inclination correction is omitted for these systems." (3.2 Calculating physical properties)
8. **Derive boundedness, SFE, velocity dispersion and clump size**: Velocity dispersion from CO(2-1) moment 2; boundedness b = Sigma_mol/sigma_v^2; SFE = Sigma_SFR/Sigma_H2 = 1/t_dep; clump effective radius from Astrodendro area  
  > "the velocity dispersion ($\sigma_{v}$) obtained from the CO(2–1) moment 2" (3.2 Calculating physical properties); "we calculate the star formation efficiency as SFE = $\Sigma_{SFR}$/$\Sigma_{H_{2}}$ = $t_{\rm dep}^{-1}$" (3.2 Calculating physical properties); "The effective radius of the gas clumps is calculated from the area of the clumps, as determined by the Astrodendro algorithm." (3.2 Calculating physical properties)
   - software: Astrodendro
   - fitting: _not stated_
   - validation: _not stated_
9. **Fit Kennicutt-Schmidt relations per galaxy and per merger stage**: ODR power-law fits of Sigma_SFR vs Sigma_H2; MARS used to find breakpoints for dual (two-branch) behaviour; Spearman rank correlations  
  > "We fit the data points using the orthogonal distance regression (cite: Boggs1987) method, which minimises the orthogonal distances from the data points to the regression line." (4.1.1 Kennicutt-Schmidt law); "These two branches were identified using the Multivariate Adaptive Regression Splines (cite: Friedman1991) fit" (4.1.1 Kennicutt-Schmidt law); "Spearman’s rank correlation coefficient $\rho_{sp}$ (two-sided p-values)" (Table 3 notes)
   - software: ODR (Boggs1987), MARS (Friedman1991)
   - parameter: Mean and error bars from the mean absolute deviation for log Sigma_H2 and log Sigma_SFR per merger stage  
  > "the mean and error bars (from the mean absolute deviation)" (Table 3 notes)
   - assumption: Upper limits and non-detections excluded  
  > "We do not include in our analysis upper limits." (4.1.1 Kennicutt-Schmidt law)
   - fitting: Orthogonal distance regression (priors/likelihood not applicable); MARS for multi-slope breaks  
  > "We fit the data points using the orthogonal distance regression (cite: Boggs1987) method" (4.1.1 Kennicutt-Schmidt law)
   - validation: Compared single-trend vs dual behaviour between methods; scatter around ODR fit quantified by standard deviation of orthogonal distances  
  > "We quantify the scatter around the best-fit K–S relation using the standard deviation of the orthogonal distances between the data points and the ODR fit" (Appendix 10 Comparison between region-based and clump-based measurements)
10. **Test robustness to array configuration and alpha_CO choice**: Compare clumps and fluxes from one vs two 12 m configurations (IC 5179, NGC 7469); redo KS analysis with sigma_v-dependent alpha_CO (NGC 5135 example) and with alpha_CO = 0.8  
  > "To evaluate the influence of using one or two configurations on clump detection, we compared the identified regions (clumps) in observations of IC 5179 using different configurations" (Appendix 6); "As an example, Fig. [14](#fig:ap2) shows the KS plot for the galaxy NGC5135." (Appendix 7)
   - parameter: alpha_CO relation log alpha_CO = -0.59(±0.04) log sigma_v + 0.90(±0.03), 90 pc scale  
  > "log_{10} \alpha_{co} = -0.59  (\pm 0.04) ~ log <\sigma_{v}>_{90pc} + ~0.90 (\pm 0.03)" (Appendix 7)
   - assumption: Fixed alpha_CO adopted where sigma_v exceeds the range explored by PHANGS (~35 km/s)  
  > "The PHANGS sample covers values of velocity dispersion up to $\sim$35 km/s, whereas the galaxies in our sample exceed this range of values." (Appendix 7)
   - fitting: _not stated_
   - validation: Dual behaviour and single clump power law are retained; main results unaffected  
  > "we can conclude that the different prescriptions for the conversion factor do not affect the main results of this work." (Appendix 7)

## Software

- **CASA** : Calibration and cleaning of ALMA data  
  > "The data were calibrated using the standard ALMA data reduction software, CASA" (2.2 CO(2–1) ALMA data)
- **Astrodendro** : Identifying CO(2-1) clumps via dendrogram leaves  
  > "To identify physical clumps and measure their properties, we use the Python code `Astrodendro` (cite: Rosolowsky2008)." (3.1.2 Dendrogram analysis)
- **isophote (photutils)** : Elliptical isophote fitting of Spitzer 3.6 um images for inclination  
  > "We use the elliptical isophote fitting from the `isophote`[^7] package in Python" (3.2 Calculating physical properties)
- **moment_maps (GitHub code)** : Moment 0 and 2 maps with 3xRMS masking  
  > "for more details, see (cite: SG2022); the code is available on GitHub" (2.2 CO(2–1) ALMA data)
- **Multivariate Adaptive Regression Splines (MARS)** : Identifying breakpoints of dual KS branches  
  > "These two branches were identified using the Multivariate Adaptive Regression Splines (cite: Friedman1991) fit" (4.1.1 Kennicutt-Schmidt law)
- **Orthogonal distance regression (ODR)** : Fitting KS power laws  
  > "We fit the data points using the orthogonal distance regression (cite: Boggs1987) method" (4.1.1 Kennicutt-Schmidt law)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of beam-sized CO regions | more than 4000 | not stated | count | 5 | In total, we obtain more than 4000 regions for the whole sample. |
| Number of molecular gas clumps (Astrodendro) | 1027 | not stated | count | 6 | we identify a total of 1027 clumps in our sample of galaxies. |
| Clump size range / median | 89 to 694 pc (one clump 1068 pc); median 154 pc | not stated | pc | 6 | The sizes of these molecular gas clumps range from 89 to 694 pc, except for a clump in the galaxy IRAS15206–6256 N, which reaches 1068 pc. The median clump size in our sample is 154 pc. |
| Galaxies with dual KS behaviour (beam-sized regions) | 9 galaxies (~33%) of 27 | not stated | count | 9 | This behaviour is observed in 9 galaxies ($\sim$33%) of our galaxy sample. |
| Range of per-galaxy KS slopes | 0.39 to 3.36 | 0.07 and 0.44 at the ends | dimensionless | 9 | we obtain a wide range of slopes from sub-linear (0.39$\pm$0.07) up to super-linear (3.36$\pm$0.44). |
| Scatter of per-galaxy clump KS relation | 0.10–0.25 | not stated | dex | 9 | a significantly smaller scatter, in the range of 0.10–0.25 dex |
| Median depletion timescales | 0.2–1.2 | not stated | Gyr | 8 | We obtain median depletion timescales of 0.2–1.2 Gyr in our sample using a Galactic $\alpha_{CO}$ conversion factor. |
| KS slope, all clumps | 1.31 | 0.03 | dimensionless | 9 | Our clump-based analysis (left panel) yields a superlinear slope (N = 1.31 $\pm$ 0.03, $\rho_{s}$ = 0.64) |
| KS slope, all beam-sized regions | 1.04 | 0.02 | dimensionless | 9 | the region-based analysis (right panel) results in a slope close to linear (N = 1.04 $\pm$ 0.02, $\rho_{s}$ = 0.73) |
| Scatter around KS fit: clumps vs regions | 0.21 vs 0.28 | not stated | dex | 9 | finding 0.21 dex for the clump-based measurements and 0.28 dex for the region-based ones |
| Clump KS slope, isolated galaxies | 1.01 | 0.05 | dimensionless | 9 | Isolated / 0.79 / 2.89 $\pm$ 0.38 / 0.25 $\pm$ 0.43 / 1.01 $\pm$ 0.05 |
| Clump KS slope, early-stage mergers | 1.78 | 0.08 | dimensionless | 9 | Early-stage / 0.46 / 2.73 $\pm$ 0.24 / 0.11 $\pm$ 0.49 / 1.78 $\pm$ 0.08 |
| Clump KS slope, late-stage mergers | 1.48 | 0.09 | dimensionless | 9 | Late-stage / 0.84 / 3.62 $\pm$ 0.41 / 1.05 $\pm$ 0.76 / 1.48 $\pm$ 0.09 |
| Gap in mean log Sigma_H2 and Sigma_SFR between late-stage mergers and earlier stages (clumps) | more than 0.5 | not stated | dex | 9 | we find a gap of more than 0.5 dex between late-stage mergers and earlier stages |
| SFE vs b slope (clumps), mid-stage mergers | 0.67 | 0.11 | dimensionless | 9 | Mid-stage / 0.44 / -0.72 $\pm$ 0.61 / -2.72 $\pm$ 0.46 / 0.67 $\pm$ 0.11 |
| SFE vs b slope (clumps), late-stage mergers | 0.66 | 0.05 | dimensionless | 9 | Late-stage / 0.61 / 0.47 $\pm$ 0.36 / -2.57 $\pm$ 0.41 / 0.66 $\pm$ 0.05 |
| Mean clump velocity dispersion, early-stage mergers | 103.50 | 32.37 (mean absolute deviation) | km/s | 9 | Early-stage / 0.13 / 103.50 $\pm$ 32.37 |
| Shift in Sigma_H2 axis with sigma_v-based alpha_CO (NGC 5135) | ~0.55 (depletion time changes by factor ~3.7) | not stated | dex | 10 | with a shift of $\sim$ 0.55 dex. This implies that the depletion time changes by a factor of approximately 3.7. |
| Flux difference between two 12 m configurations (IC 5179) and 12m vs 12m+7m (NGC 7469) | ~8.5% and ~23.2% | not stated | percent | 10 | the flux difference between the two 12 m configurations corresponds to a modest loss of $\sim$8.5%; finding a flux difference of $\sim$23.2% |

## Qualitative findings

- Clump-based KS relation is a single trend in all galaxies, while beam-sized regions show dual behaviour in ~33% of galaxies  
  > "In contrast, when using physical gas clumps, the duality disappears and all galaxies show a single trend." (abstract)
- Clumps in late-stage mergers are mainly near the nucleus  
  > "Clumps in late-stage mergers are predominantly located at small distances from the nucleus, confirming that most of the activity is concentrated in the central regions." (abstract)
- Clump self-gravity starts to regulate SF between early and mid merger stages  
  > "indicating that clump self-gravity only starts to regulate the star formation process between the early- and mid-merger stages." (abstract)

## Claim tuples

- H: Does the resolved KS relation show one or two behaviours, and does this depend on how regions are defined | E: Per-galaxy KS fits for beam-sized regions and Astrodendro clumps | R: 9 of 27 galaxies show two branches with beam-sized regions; all galaxies show one trend with clumps | F: Duality is a feature of the beam-sized (line-of-sight) selection; physical clumps give a single relation | **supported**
- H: Does the clump KS slope change along the merger sequence | E: Clump KS fits by merger stage | R: Slope about 1 in isolated galaxies and steeper (1.48-1.79) in early to late mergers; beam-sized region slopes stay near 1 | F: SF efficiency of clumps increases as the merger progresses | **supported**
- H: Do late-stage mergers have higher gas and SFR surface densities | E: Mean log Sigma_H2 and Sigma_SFR per merger stage | R: Gap of more than 0.5 dex between late-stage mergers and earlier stages | F: Gas concentrates in the central kiloparsecs as the merger advances, with higher SFR | **supported**
- H: Does clump self-gravity (boundedness) regulate SFE, and does this change with merger stage | E: SFE vs b for clumps by merger stage | R: Correlation shifts from negative or flat in early stages to positive in mid and late stages | F: Self-gravity regulates SFE only from mid/late merger stages | **supported**
- H: Are the conclusions sensitive to the adopted CO-to-H2 conversion factor | E: Re-did KS analysis with sigma_v-dependent alpha_CO and with alpha_CO = 0.8 | R: Dual behaviour and single clump power law retained; x-axis shifts by ~0.55 dex | F: Main results do not depend on alpha_CO prescription | **supported**

## Reasoning

- Why this data: Near-IR recombination lines suffer less extinction than optical lines in dusty LIRG nuclei, and CO(2-1) at ~100 pc resolves GMC scales  
  > "Hydrogen recombination lines in the near-infrared – such as Pa$\alpha$, Pa$\beta$, or Br$\gamma$ – are well suited for this purpose" (Introduction)
- Why this method: Clumps via dendrograms give physically meaningful structures versus beam-sized regions that maximise number statistics  
  > "These results provide two complementary perspectives when studying the star formation process: one that maximises the number statistics (beam-sized regions), and another that focuses on actual structures associated to gas clumps" (abstract)
- Alternative: ULIRG-like low alpha_CO rejected as default for this sample; tested alpha_CO = 0.8 and sigma_v-based alpha_CO in robustness checks  
  > "We do not expect that a lower conversion factor typical of ULIRGs (cite: Papadopoulos2012) is appropriate for our targets." (3.2 Calculating physical properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Extended-only configuration data lose flux at scales beyond ~2.5 arcsec (~1.2 kpc)  
  > "However, we expect to lose flux at scales larger than $\sim$2.5" ($\sim$ 1.2 kpc)." (Appendix 6)
- Limitation (authors): Central regions of dual galaxies cannot be separated into multiple clumps at the current resolution  
  > "Higher-resolution observations are needed in order to disentangle physical gas clumps at the core of these galaxies." (4.1.1 Kennicutt-Schmidt law)
- Limitation (authors): Inclination correction less reliable for disturbed mid/late mergers  
  > "the inclination correction becomes less reliable." (3.2 Calculating physical properties)
- Caveat (inferred, ours): Single Galactic alpha_CO for all galaxies and regions, while ULIRG-like values may apply to nuclei; mass-based quantities (Sigma_H2, b, SFE) scale with it
- Caveat (inferred, ours): Clump KS slopes by merger stage rest on few galaxies per stage (e.g. 4-5 mid/late), so stage trends mix galaxy-to-galaxy variation
- Caveat (inferred, ours): Pa-alpha and Pa-beta samples differ and map onto different merger stages (Paα mostly isolated/early, Paβ mid/late), confounding stage with tracer, instrument and extinction correction
- Caveat (inferred, ours): Compact-configuration data exist for only 13 of 23 systems, so clump detection and flux completeness differ across the sample (up to ~23% flux difference in a test)
- Caveat (inferred, ours): Extinction (A_K) taken from SINFONI maps of small FoV; applying it across the whole galaxy is not described

## Reproducibility

- Data public (paper): ALMA data identified by project code; HST images are archival  
  > "which has archival NIR observations from HST" (2.1 Sample selection); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00243.S, ADS/JAO.ALMA#2013.1.00271.S, ADS/JAO.ALMA#2015.1.00714.S, ADS/JAO.ALMA#2017.1.00255.S, ADS/JAO.ALMA#2017.1.00395.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: Moment-map code on GitHub (itsmariasg/moment_maps)  
  > "the code is available on GitHub" (2.2 CO(2–1) ALMA data)
- Code: Clump catalogue (Table 6) available at the CDS  
  > "The catalogue of molecular gas clumps identified in this work, including their main physical properties, is provided as Table 6." (Data availability)
- Missing: CASA version, calibration and tclean parameters, and masks for the cubes
- Missing: How compact and extended configuration data were combined
- Missing: Extinction correction details (deferred to SG2022) and per-galaxy A_K
- Missing: Astrodendro version and exact clump SFR/mass summation
- Missing: MARS fitting settings
- Missing: The sigma_v-dependent alpha_CO prescription (private communication)
- Data volume (inferred): Five ALMA Band 6 projects, 23 systems, 12 m (some with 7 m) cubes: likely hundreds of GB of raw/calibrated data; plus small HST narrow-band images
- Score (inferred): 3/5, Public ALMA and HST data, explicit dendrogram parameters, alpha_CO, SFR calibration and numeric tables, but calibration and imaging details, CASA version and extinction correction are deferred to SG2022 or not given.
- Rediscovery candidate: no, Recipe for the headline numbers depends on SG2022 for extinction and region/cube preparation, and imaging parameters are missing, so a faithful redo cannot be built from this paper alone.

## Links

- Method: Rosolowsky2008 (Astrodendro dendrogram algorithm)
- Method: SG2022 (Earlier paper whose data, moment-map code, extinction correction and region method are reused)
- Companion: SG2022 (Earlier resolved KS study of part of the sample)
- Companion: Larson2020 (Source of HST Paβ reductions and SFR-size relation comparison)
- Related: GOALS (Great Observatories All-sky LIRG Survey)
- Related: PHANGS
- Related: Xtreme Scientific Project database

## Checks

```json
{
 "quotes": 145,
 "quotes_ok": 145,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 125,
  "stated": 91,
  "rate": 0.728
 },
 "evidence_ok": true
}
```
