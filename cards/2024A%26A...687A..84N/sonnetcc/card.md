# Core to ultracompact HII region evolution in the W49A massive protocluster

`2024A&A...687A..84N` | Astronomy and Astrophysics 2024 | first author: Nony, T. | arXiv: 2404.02250 | DOI: 10.1051/0004-6361/202449279

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Identify and characterize cores in the high-mass protocluster W49, determine their evolutionary stages and measure the associated lifetimes  
  > "We aim to identify and characterize cores in the high-mass proto-cluster W49, determine their evolutionary stages and measure the associated lifetimes." (abstract)
- Target **W49A (W49N, W49SW and outskirts)**: coordinates _not stated_; z/distance 11.1 kpc  
  > "W49A, located at a distance of 11.1 kpc from the Sun (cite: 2013ApJ...775...79Z)" (1 Introduction); distance from (cite: 2013ApJ...775...79Z)  
  > "W49A, located at a distance of 11.1 kpc from the Sun (cite: 2013ApJ...775...79Z)" (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00620.S
- bands: Band 6 (1.3 mm)  
  > "Observations of W49A at 1.3 mm (Band 6) were carried out with ALMA in Cycle 5" (2.1 ALMA data)
- frequencies and spectral setup: four spectral windows (Spws); Spw 2 covers H30alpha at 231.9 GHz; Spw 0 and Spw 3 used for CH3OCHO lines  
  > "The Spw 2 band covers the H30$\alpha$ line at 231.9 GHz. We also used the Spw 0 and Spw 3 bands to analyze CH$_3$OCHO lines." (2.1 ALMA data)
- continuum bandwidth: 1.23 GHz (line-free channels from the four Spws)  
  > "from the four spectral windows (hereafter Spws) of the dataset, summing up to a bandwidth of 1.23 GHz" (2.1 ALMA data)
- arrays: 12-m array  
  > "The maximum recoverable scale of the 12-m array configuration used in this work is about 11$\ensuremath{''}$." (2.1 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.29" x 0.24" (continuum, about 2900 au at 11.1 kpc); about 0.24" (line cubes)  
  > "The final beam of the 1.3 mm continuum image has a FWHM size of $0.29\ensuremath{''} \times 0.24\ensuremath{''}$ ($\approx 2900$ au at 11.1 kpc)." (2.1 ALMA data); "The cubes across the four bands have a spatial resolution of approximately 0.24$\ensuremath{''}$ (2750 au)" (2.1 ALMA data)
- max recoverable scale: about 11 arcsec  
  > "The maximum recoverable scale of the 12-m array configuration used in this work is about 11$\ensuremath{''}$." (2.1 ALMA data)
- sensitivity: continuum rms 0.38 mJy/beam; line cubes 1.6 mJy/beam (0.6 K) per 0.65 km/s channel  
  > "The rms noise measured in regions far away from the brightest emission, where the map is not limited by dynamic range, is of 0.38 mJy beam$^{-1}$" (2.1 ALMA data); "a channel width of 0.65 km s$^{-1}$, and an rms noise of 1.6 mJy beam$^{-1}$ (0.6 K) per channel." (2.1 ALMA data)
- time on source: _not stated_
- observing dates: between 2017 and 2018 (Cycle 5)  
  > "were carried out with ALMA in Cycle 5 (project 2016.1.00620.S, PIs: Ginsburg, Galván-Madrid) between 2017 and 2018." (2.1 ALMA data)
- pi or archival as stated: project 2016.1.00620.S, PIs: Ginsburg, Galván-Madrid  
  > "(project 2016.1.00620.S, PIs: Ginsburg, Galván-Madrid)" (2.1 ALMA data)
- Line: H30alpha H30alpha recombination line (231.9009 GHz)
- Line: CH3OCHO (methyl formate) 17(3,14) - 16(3,13) doublet (218.281 and 218.298 GHz)
- Other facility **VLA (A-array, X band 3.3 cm continuum)**: 3.3 cm continuum image used to trace free-free emission from H/UC HII regions  
  > "We used the VLA A-array continuum image at 3.3 cm (X Band) presented in (cite: 2020AJ....160..234D)." (2.2 VLA data)
- External data: VLA X-band 3.3 cm continuum image (original resolution 0.16 arcsec), made to study W49N  
  > "We used the VLA A-array continuum image at 3.3 cm (X Band) presented in (cite: 2020AJ....160..234D). This image was created with the purpose of only studying W49N." (2.2 VLA data) [from (cite: 2020AJ....160..234D)]
- External data: Dendrogram catalog of 79 H/UC HII regions in W49N from the X-band image, used to complement core identification  
  > "Juárez-Gama et al. (in prep.) used this image to provide a dendrogram catalog of H/UC HII regions and their physical properties in W49N." (2.2 VLA data) [from Juárez-Gama et al. (in prep.)]
- External data: Typical H/UC HII region lifetime of 3e5 yr from Galaxy-wide surveys, used to scale lifetimes  
  > "Using the typical lifetime for H/UC HII regions of $3\times10^5$ yr, calculated from Galaxy-wide surveys (cite: 2002ARA&A..40...27C; 2011ApJ...730L..33M)" (5.3 Lifetimes) [from (cite: 2002ARA&A..40...27C; 2011ApJ...730L..33M)]
- External data: Distance to W49A of 11.1 kpc  
  > "W49A, located at a distance of 11.1 kpc from the Sun (cite: 2013ApJ...775...79Z)" (1 Introduction) [from (cite: 2013ApJ...775...79Z)]
- External data: Electron temperature Te = 7000 K adopted for free-free calculations  
  > "where the electron temperature is $T_\mathrm{e} = 7000$ K (e.g. (cite: 2023MNRAS.520.3245Z))" (4.2 Free-free emission in ALMA Band 6) [from (cite: 2023MNRAS.520.3245Z)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.4 (continuum processing)  
  > "version 5.4 (cite: 2022CASA) using the imaging and self-calibration pipeline developed by the ALMA-IMF consortium" (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: three iterations of cleaning and phase self-calibration, one iteration of amplitude self-calibration  
  > "We performed three iterations of cleaning and phase self-calibration and one iteration of amplitude self-calibration, using model masks of increasing size and decreasing cleaning thresholds" (2.1 ALMA data)

### Imaging

- task: tclean (continuum, ALMA-IMF pipeline); IMAGER in GILDAS (line cubes)  
  > "with two Taylor terms, a robust parameter of 0, and scales up to nine times larger than the synthesized beam" (2.1 ALMA data); "Cleaning was performed using Clark deconvolution and 0.1 robust weighting." (2.1 ALMA data)
- deconvolver: Multi-term (Multi Scale) Multi-Frequency Synthesis with two Taylor terms (continuum); Clark (line cubes)  
  > "We used the Multi-term (Multi Scale) Multi-Frequency Synthesis deconvolver of" (2.1 ALMA data); "Cleaning was performed using Clark deconvolution and 0.1 robust weighting." (2.1 ALMA data)
- weighting robust: robust = 0 (continuum); robust = 0.1 (line cubes)  
  > "with two Taylor terms, a robust parameter of 0, and scales up to nine times larger than the synthesized beam" (2.1 ALMA data); "Cleaning was performed using Clark deconvolution and 0.1 robust weighting." (2.1 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: model masks of increasing size and decreasing cleaning thresholds across self-calibration iterations  
  > "using model masks of increasing size and decreasing cleaning thresholds" (2.1 ALMA data)
- multiscale scales: scales up to nine times larger than the synthesized beam  
  > "scales up to nine times larger than the synthesized beam" (2.1 ALMA data)
- continuum subtraction: continuum and line emission separated in each image-plane pixel with the method of Molet et al. 2019 and Brouillet et al. 2022  
  > "We have used the method presented in (cite: 2019Molet) and (cite: 2022Brouillet) to separate the continuum and spectral line emission in each pixel of the image plane." (2.1 ALMA data)
- line free channels: a selection of line-free channels from the four Spws (channels not listed)  
  > "The continuum map has been produced using a selection of line-free channels" (2.1 ALMA data)
- primary beam correction: applied to the VLA X-band image, which was then regridded to the ALMA image frame  
  > "then corrected it for its primary-beam response and regridded it to the ALMA image frame." (2.2 VLA data)
- array combination: _not stated_
- smoothing: VLA X-band image smoothed from 0.16 arcsec to the B6 resolution (0.26 arcsec)  
  > "We smoothed this image from its original angular resolution (0.16$\ensuremath{''}$) to the resolution of the B6 ALMA continuum image (0.26$\ensuremath{''}$)" (2.2 VLA data)
- final beam: 0.29" x 0.24" (1.3 mm continuum)  
  > "The final beam of the 1.3 mm continuum image has a FWHM size of $0.29\ensuremath{''} \times 0.24\ensuremath{''}$ ($\approx 2900$ au at 11.1 kpc)." (2.1 ALMA data)
- final rms: 0.38 mJy/beam (continuum); 1.6 mJy/beam per channel (line cubes)  
  > "is of 0.38 mJy beam$^{-1}$" (2.1 ALMA data); "an rms noise of 1.6 mJy beam$^{-1}$ (0.6 K) per channel." (2.1 ALMA data)

### Inherited from earlier work

- Continuum imaging and self-calibration pipeline, including the line-free channel selection (cleanest maps)  
  > "using the imaging and self-calibration pipeline developed by the ALMA-IMF consortium (described in detail in (cite: Ginsburg22))" (2.1 ALMA data); "The continuum map has been produced using a selection of line-free channels" (2.1 ALMA data) [from the ALMA-IMF consortium pipeline, (cite: Ginsburg22)]
- Separation of continuum and line emission per pixel  
  > "We have used the method presented in (cite: 2019Molet) and (cite: 2022Brouillet) to separate the continuum and spectral line emission in each pixel of the image plane." (2.1 ALMA data) [from (cite: 2019Molet) and (cite: 2022Brouillet)]
- getsf post-selection filters for robust core detection and measurement  
  > "We found 129 cores passing the post-selection filters for robust detection and measurements recommended by (cite: 2021Mensh)" (3.1 Core catalog) [from (cite: 2021Mensh)]
- Methyl formate method for identifying hot molecular cores  
  > "We used methyl formate (CH$_3$OCHO) as a signature of hot molecular core emission, following the method described in (cite: 2022Brouillet)" (3.3 Identification of hot molecular cores) [from (cite: 2022Brouillet)]
- Free-free map from H30alpha moment 0 map  
  > "We also constructed a pixel by pixel free-free map $I_\mathrm{ff,RL}$ using the moment 0 of the H30$\alpha$ recombination line (cite: Wilson09; 2019ApJ...871..185L)" (4.2 Free-free emission in ALMA Band 6) [from (cite: Wilson09; 2019ApJ...871..185L)]
- VLA X-band 3.3 cm continuum image (processing not described here)  
  > "We used the VLA A-array continuum image at 3.3 cm (X Band) presented in (cite: 2020AJ....160..234D)." (2.2 VLA data) [from (cite: 2020AJ....160..234D)]

### Not stated but needed to reproduce (our reading)

- Which channels were treated as line-free for the continuum image (set by the ALMA-IMF pipeline, Ginsburg et al. 2022)
- Array configurations, baseline range, time on source and calibrators for project 2016.1.00620.S
- Pipeline or manual calibration and the CASA pipeline version of the delivered data
- Flux-scale uncertainty of ALMA and VLA data
- getsf version, spatial-scale and size parameters, and how the continuum map rms was passed to getsf
- How VLA X-band and ALMA maps were registered and how the VLA flux was measured for core fluxes
- Parameters of the continuum/line separation method of Molet et al. 2019 and Brouillet et al. 2022
- Settings of the synthetic-spectrum fit used to verify the methyl formate detections (software, Tex, column density, line width), and the detection criterion for the methyl formate doublet
- Image size and phase center for the mosaic cubes; field list
- Methods and software for the Gaussian fits to the H30alpha spectra
- Juarez-Gama et al. (in prep.) dendrogram catalog of H/UC HII regions, not yet published
- Derivation of the 2e4 yr coexistence time beyond the cited reference

## Analysis recipe

1. **make 1.3 mm continuum image**: ALMA-IMF imaging and self-calibration pipeline on line-free channels of the four Spws  
  > "using the imaging and self-calibration pipeline developed by the ALMA-IMF consortium (described in detail in (cite: Ginsburg22))" (2.1 ALMA data)
   - software: CASA 5.4, tclean
   - parameter: three iterations of cleaning and phase self-calibration, one of amplitude self-calibration  
  > "We performed three iterations of cleaning and phase self-calibration and one iteration of amplitude self-calibration" (2.1 ALMA data)
   - parameter: MTMFS deconvolver, two Taylor terms, robust 0, scales up to nine times the synthesized beam  
  > "with two Taylor terms, a robust parameter of 0, and scales up to nine times larger than the synthesized beam" (2.1 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **make line cubes and separate continuum from lines**: IMAGER (GILDAS) with Clark deconvolution; per-pixel continuum/line separation  
  > "Cleaning was performed using Clark deconvolution and 0.1 robust weighting." (2.1 ALMA data); "We have used the method presented in (cite: 2019Molet) and (cite: 2022Brouillet) to separate the continuum and spectral line emission in each pixel of the image plane." (2.1 ALMA data)
   - software: GILDAS, IMAGER
   - parameter: 0.65 km/s channels, 0.24 arcsec resolution, 1.6 mJy/beam rms per channel  
  > "a channel width of 0.65 km s$^{-1}$, and an rms noise of 1.6 mJy beam$^{-1}$ (0.6 K) per channel." (2.1 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
3. **match VLA X-band image to ALMA band 6**: smooth VLA image to B6 resolution, correct for primary beam, regrid to ALMA frame  
  > "then corrected it for its primary-beam response and regridded it to the ALMA image frame." (2.2 VLA data)
   - parameter: 0.16 arcsec smoothed to 0.26 arcsec  
  > "We smoothed this image from its original angular resolution (0.16$\ensuremath{''}$) to the resolution of the B6 ALMA continuum image (0.26$\ensuremath{''}$)" (2.2 VLA data)
   - fitting: _not stated_
   - validation: _not stated_
4. **extract core catalog**: getsf multi-scale source extraction on the 1.3 mm continuum image  
  > "algorithm (cite: 2021Mensh) to extract sources from the 1.3 mm continuum images" (3.1 Core catalog)
   - software: getsf
   - parameter: post-selection filters: background-subtracted peak S/N > 2, size < 4 x beam FWHM, ellipticity < 2  
  > "signal-to-noise for the background-subtracted peak larger than two, source size smaller than four times the FWHM beamsize, and ellipticity smaller than two." (3.1 Core catalog)
   - fitting: _not stated_
   - validation: _not stated_
5. **measure core fluxes in B6 and X band**: getsf peak and integrated fluxes; second set from direct maximum and sum of pixel intensities within the core FWHM, with correction constant c  
  > "to measure the peak intensity and integrated flux of the cores in the ALMA B6" (3.1 Core catalog); "We set the constant c=1/ln(2) to account for the core extension beyond its FWHM." (3.1 Core catalog)
   - software: getsf
   - parameter: c = 1/ln(2)  
  > "We set the constant c=1/ln(2) to account for the core extension beyond its FWHM." (3.1 Core catalog)
   - fitting: _not stated_
   - validation: _not stated_
6. **detect H30alpha emission in cores**: two methods: Gaussian fits to the spectrum at each core, and clipped moment 0 maps integrated from -50 to +50 km/s  
  > "performed Gaussian fitting to measure the line systemic velocity, the FWHM line width $\Delta V$, and the peak brightness temperature $T_\mathrm{B}$." (3.2.1 Detection of the H30alpha line); "which we constructed by integrating in velocity from $-50~\ensuremath{\rm km\,s^{-1}}$ to $+50~\ensuremath{\rm km\,s^{-1}}$" (3.2.1 Detection of the H30alpha line)
   - parameter: strong detection T_B > 2 K, weak 0.8-2 K; line width > 20 km/s to reject molecular-line contamination  
  > "We then separated cores with brightness temperature $T_\mathrm{B} > 2$ K (38 cores) from cores with $T_\mathrm{B}$ between 0.8 and 2 K (14 cores)." (3.2.1 Detection of the H30alpha line); "we further applied a threshold for the linewidth of $\Delta V>20~\ensuremath{\rm km\,s^{-1}}$" (3.2.1 Detection of the H30alpha line)
   - parameter: moment 0 thresholds 5 sigma = 0.4 Jy/beam km/s (centre) and 0.1 Jy/beam km/s (SW)  
  > "we defined two reference thresholds, 5$\sigma_{\rm ctr}=0.4$ Jy beam$^{-1}$$\ensuremath{\rm km\,s^{-1}}$ in the center, 5$\sigma_{\rm sw}=0.1$ Jy beam$^{-1}$$\ensuremath{\rm km\,s^{-1}}$ in the South West (SW) region" (3.2.1 Detection of the H30alpha line)
   - fitting: Gaussian fit to each core spectrum (details not stated)  
  > "performed Gaussian fitting to measure the line systemic velocity, the FWHM line width $\Delta V$, and the peak brightness temperature $T_\mathrm{B}$." (3.2.1 Detection of the H30alpha line)
   - validation: visual inspection of tentative detections; all 29 strong detections also detected in moment 0 maps  
  > "All the 29 cores with a strong H30$\alpha$ line detection are also detected in the moment 0 maps and qualify as robust H30$\alpha$ detections." (3.2.1 Detection of the H30alpha line)
7. **detect free-free cm emission in cores**: robust detection if both background-subtracted peak and maximum X-band intensity exceed 3 sigma  
  > "We defined the criterion for a robust detection and measurement in X band as $S^{\rm peak}_{\rm BX} > 3\sigma_{\rm BX}$ and $F^{\rm max}_{\rm BX} > 3\sigma_{\rm BX}$" (3.2.2 Detection of free-free centimeter emission)
   - parameter: sigma_BX = 0.22 mJy/beam, from median absolute deviation  
  > "where $\sigma_{\rm BX}=0.22$ mJy beam$^{-1}$ is the noise in the X band maps convolved to the B6 angular resolution, measured using the median absolute deviation." (3.2.2 Detection of free-free centimeter emission)
   - fitting: _not stated_
   - validation: _not stated_
8. **identify hot molecular cores**: methyl formate doublet as HMC tracer, following Brouillet et al. 2022  
  > "We have based the identification on the CH$_3$OCHO (17$_{3,14}$ – 16$_{3,13}$) doublet at 218.281 and 218.298 GHz, with an upper-level energy $E_{\rm u}$ of 99.7 K." (3.3 Identification of hot molecular cores)
   - assumption: methyl formate is a good compromise between widespread detectability and reliability in tracing HMCs  
  > "This study showed that this molecule offers a good compromise between widespread detectability and reliability in tracing HMC." (3.3 Identification of hot molecular cores)
   - fitting: synthetic spectrum fit of the methyl formate lines in Spw 3 (details not stated)  
  > "We have further verified our detections with a synthetic spectrum fitting the numerous methyl formate lines in Spw 3." (3.3 Identification of hot molecular cores)
   - validation: verified with a synthetic spectrum fit  
  > "We have further verified our detections with a synthetic spectrum fitting the numerous methyl formate lines in Spw 3." (3.3 Identification of hot molecular cores)
9. **derive free-free fraction, spectral index and emission measure**: scale X-band flux to 1.3 mm with alpha = -0.1 (lower limit); build free-free map from H30alpha moment 0; compute P_ff, alpha_ff and EM  
  > "We took a spectral index $\alpha=-0.1$, assuming that the free-free emission is optically thin all the way from 3 cm to 1 mm." (4.2 Free-free emission in ALMA Band 6); "We defined their percentage of free-free emission in B6 as $P_\mathrm{ff}=\,F_\mathrm{ff,RL}/F_\mathrm{B6}$." (4.2 Free-free emission in ALMA Band 6)
   - parameter: Te = 7000 K, N_He/N_H = 0.08  
  > "where the electron temperature is $T_\mathrm{e} = 7000$ K (e.g. (cite: 2023MNRAS.520.3245Z)), the helium to hydrogen number ratio is $N_\mathrm{He}/N_\mathrm{H} = 0.08$" (4.2 Free-free emission in ALMA Band 6)
   - parameter: tau_ff = 1.5 for six cores with T_B near or above Te (EM lower limits)  
  > "We computed for these six cores a lower limit of the emission measure using an opacity $\tau_\mathrm{ff}=1.5$ in line with the rest of the core sample." (4.2 Free-free emission in ALMA Band 6)
   - assumption: free-free emission optically thin from 3 cm to 1 mm for the cm-based estimate; constant Te = 7000 K  
  > "The fluxes calculated in this way are thus lower limits to the free-free emission in the ALMA image." (4.2 Free-free emission in ALMA Band 6); "we used a constant electron temperature $T_\mathrm{e} = 7000$ K" (4.2 Free-free emission in ALMA Band 6)
   - fitting: _not stated_
   - validation: two independent free-free estimates (X band and H30alpha) compared  
  > "We then obtained a second evaluation of the free-free emission in B6 by measuring on the $I_\mathrm{ff,RL}$ map the integrated fluxes of the cores" (4.2 Free-free emission in ALMA Band 6)
10. **classify cores by evolutionary stage**: four types from presence of HMC and/or H/UC HII emission (a: neither, b: HMC only, c: both, d: H/UC HII only)  
  > "to build a classification of the dust cores into four types: $a/$ cores without either HMC or H/UC HII region, $b/$ cores associated with a HMC but without H/UC HII emission" (4.3 Core classification)
   - assumption: cores of type b to d host high-mass protostars; type a cores are prestellar or low-mass protostellar  
  > "From stage $b/$ onward, all cores are expected to harbor a high-mass ($\gtrsim 8~\ensuremath{M_{\odot}}$) protostar." (5.1 Evolution of Star Forming Cores in W49A)
   - fitting: _not stated_
   - validation: _not stated_
11. **derive statistical lifetimes**: ratio of numbers of objects in a phase to number of H/UC HII objects, times the H/UC HII lifetime  
  > "the relative number of HMCs to H/UC HII regions (17/85) provides an estimation of their statistical lifetime." (5.3 Lifetimes); "$\tau_\mathrm{proto} \simeq 40/85\,\times\,3\,10^5 \simeq 1.4\times10^5$ yr" (5.3 Lifetimes)
   - parameter: H/UC HII lifetime 3e5 yr; 109 cores in W49N; 28 cores with H/UC HII plus 57 HII without cores = 85  
  > "Summing up 28 cores with H/UC HII regions and 57 H/UC HII regions not associated to a dust core, 85 objects fall in the H/UC HII regions category." (5.3 Lifetimes)
   - assumption: constant star formation; HMCs are precursors of H/UC HII regions  
  > "Under the hypothesis of constant star-formation and assuming that HMCs are precursors of H/UC HII regions" (5.3 Lifetimes)
   - fitting: _not stated_
   - validation: compared with earlier estimates for W49 and Sgr B2  
  > "The ratio of 17 HMCs to 85 H/UC HII we find in W49, and thus the inferred lifetime, are smaller than previous estimations in the same region" (5.3 Lifetimes)
12. **test statistical differences between core groups**: binomial confidence intervals, KS test, Pearson and Spearman correlations  
  > "Using uncertainties from the binomial distribution, we measured the 75% confidence interval for the percentage of cores containing high-mass protostars" (5.1 Evolution of Star Forming Cores in W49A); "We have verified with a KS test that the distributions are statistically distinct" (5.2 Ionization evolution within dust cores)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4: continuum imaging and self-calibration (ALMA-IMF pipeline)  
  > "version 5.4 (cite: 2022CASA) using the imaging and self-calibration pipeline developed by the ALMA-IMF consortium" (2.1 ALMA data)
- **tclean** : continuum deconvolution (MTMFS, two Taylor terms)  
  > "We used the Multi-term (Multi Scale) Multi-Frequency Synthesis deconvolver of" (2.1 ALMA data); "with two Taylor terms, a robust parameter of 0, and scales up to nine times larger than the synthesized beam" (2.1 ALMA data)
- **IMAGER (GILDAS)** : imaging of the four spectral-window line cubes with Clark deconvolution  
  > "Cleaning was performed using Clark deconvolution and 0.1 robust weighting." (2.1 ALMA data); "This work is based on an analysis carried out with the GILDAS, IMAGER and CASSIS softwares, as well as the CDMS and JPL spectroscopic databases." (Acknowledgements)
- **getsf** : core extraction and flux measurements  
  > "algorithm (cite: 2021Mensh) to extract sources from the 1.3 mm continuum images" (3.1 Core catalog); "to measure the peak intensity and integrated flux of the cores in the ALMA B6" (3.1 Core catalog)
- **CASSIS** : named among the analysis software (specific use not stated)  
  > "This work is based on an analysis carried out with the GILDAS, IMAGER and CASSIS softwares, as well as the CDMS and JPL spectroscopic databases." (Acknowledgements)
- **CDMS and JPL spectroscopic databases** : spectroscopic data (specific use not stated)  
  > "as well as the CDMS and JPL spectroscopic databases." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| number of cores in 1.3 mm catalog | 129 | not stated | dimensionless | 4 | We found 129 cores passing the post-selection filters for robust detection and measurements recommended by (cite: 2021Mensh) |
| 1.3 mm continuum beam | 0.29 x 0.24 | not stated | arcsec | 1 | The final beam of the 1.3 mm continuum image has a FWHM size of $0.29\ensuremath{''} \times 0.24\ensuremath{''}$ ($\approx 2900$ au at 11.1 kpc). |
| continuum rms | 0.38 | not stated | mJy/beam | 1 | is of 0.38 mJy beam$^{-1}$ |
| cores with robust X-band 3.3 cm detection (of 109 in the VLA field) | 27 | not stated | dimensionless | 7 | Out of the 109 cores lying in the field of view of the X band map, 27 have a robust detection at 3.3 cm. |
| cores with strong / weak H30alpha detection | 29 strong, 9 weak | not stated | dimensionless | 6 | This gave us 29 remaining cores with strong H30$\alpha$ detection ($T_\mathrm{B} > 2$ K) and 9 with a weak detection. |
| cores with H/UC HII region (plus tentative candidates) | 36 (plus 4 tentative) | not stated | dimensionless | 9 | We identified a total of 36 cores associated with H/UC HII regions over the entire ALMA mosaic, as well as four other cores tentatively associated with H/UC HII regions. |
| cores with hot molecular core emission | 19 (17 in X-band field of view, 2 in south-west) | not stated | dimensionless | 8 | We found 19 dust cores with HMC emission within the entire ALMA mosaic, that is 17 within the field of view of the X band map and 2 in the south-western region. |
| core counts by type a, b, c, d over full mosaic (candidates counted as H/UC HII in parentheses version) | a 77 (81), b 12, c 7, d 33 (29) | not stated | dimensionless | 10 | the number counts of each type are $a/$: 77 (81), $b/$: 12, $c/$: 7, and $d/$: 33 (29) |
| core counts by type within X-band field of view | a 69 (70), b 12, c 5, d 23 (22) | not stated | dimensionless | 10 | Within the smaller field of view of the VLA X band map, the statistics are 69 (70), 12, 5 and 23 (22). |
| percentage of free-free emission in B6, P_ff | 22 to 96 | not stated | % | 9 | $P_\mathrm{ff}$ ranges from 22 to 96%. |
| emission measure of cores with H/UC HII regions | 4.5e6 to 3.1e8 | not stated | pc cm^-6 | 9 | The emission measures of cores with H/UC HII regions range from 4.5$\,\times\,10^6$ to 3.1$\,\times\,10^8$ pc cm$^{-6}$ |
| free-free spectral index from 3.3 cm to 1.3 mm | about -0.1 to 1 | not stated | dimensionless | 9 | The spectral indexes from 3.3 cm to 1.3 mm range from 1, for the youngest cores with partially optically thick free-free emission, to about -0.1 |
| median dust flux of cores with HMC and/or H/UC HII vs others | 2.2e-2 and 6.9e-3 | not stated | Jy | 12 | The median dust flux of the two distributions are $2.2 \times 10^{-2}$ Jy and $6.9 \times 10^{-3}$ Jy, respectively. |
| KS test p-value between dust flux distributions | 4e-7 | not stated | dimensionless | 12 | We have verified with a KS test that the distributions are statistically distinct ($p$-value of $4 \times 10^{-7}$). |
| 75% confidence interval of high-mass protostar fraction among cores | 30-42 in W49N; 30-75 in W49SW and outskirts | not stated | % | 12 | we measured the 75% confidence interval for the percentage of cores containing high-mass protostars (stages $b/$ to $d/$) to be \[30-42\]% in W49N and \[30-75\]% in W49SW and the W49 outskirts. |
| statistical lifetime of the HMC phase in W49N | 6e4 | not stated | yr | 11 | we estimate the lifetime of the HMC phase to be $\tau_\mathrm{HMC} \simeq (17/85) \cdot (3 \times 10^5) = 6\times10^4$ yr |
| statistical lifetime of the massive protostellar phase in W49N | 1.4e5 | not stated | yr | 11 | $\tau_\mathrm{proto} \simeq 40/85\,\times\,3\,10^5 \simeq 1.4\times10^5$ yr |
| coexistence time of HMC and H/UC HII region | 2e4 | not stated | yr | 11 | The period during which HMCs and H/UC HII regions coexist in W49A (5 cores out of 17) appears to be very short, $\simeq 2\times10^4$ yr (cite: 2021MNRAS.505.2801L). |

## Qualitative findings

- Good agreement between the two ionized-gas tracers (X band and H30alpha), with 23 common detections and only four cores detected at 3.3 cm but not in H30alpha  
  > "with 23 common detections and only four cores detected at 3.3 cm and not in H30$\alpha$" (abstract)
- Rapid dispersal of the inner molecular envelope once the HC HII region forms  
  > "This indicates a rapid dispersal of the inner molecule envelope once the HC HII is formed." (abstract)
- Relative abundance of high-mass protostars not statistically different between the centre of W49A and its periphery  
  > "Therefore, the relative abundance of high-mass protostars does not appear to be statistically different between the center of W49A and its periphery." (5.1 Evolution of Star Forming Cores in W49A)

## Claim tuples

- H: Cores in W49 can be catalogued at 1.3 mm and linked to ionized gas (H/UC HII regions) and hot molecular cores | E: getsf extraction on the ALMA 1.3 mm continuum; association with VLA 3.3 cm continuum and H30alpha; methyl formate for HMCs | R: 129 cores; 36 with H/UC HII regions plus 4 tentative; 19 with HMC emission | F: The two ionized-gas tracers agree well and the 52 cores with an H/UC HII region and/or HMC are assumed to be high-mass protostellar cores | **supported**
- H: The statistical lifetimes of the HMC and massive protostellar phases can be derived from number counts relative to H/UC HII regions | E: ratio of 17 HMCs and 40 high-mass protostellar cores to 85 H/UC HII objects in W49N, scaled by 3e5 yr | R: HMC phase about 6e4 yr; massive protostellar phase about 1.4e5 yr | F: Lifetimes are about 6e4 yr and 1.4e5 yr, the latter about two times lower than a literature value | **supported**
- H: HMCs and H/UC HII regions coexist only briefly | E: fraction of HMC cores that also host an H/UC HII region (5 of 17) | R: coexistence of about 2e4 yr | F: Rapid dispersal of the inner molecular envelope once the HC HII region is formed | **supported**
- H: Free-free spectral index and free-free fraction trace an evolutionary sequence (older HII regions optically thin with larger P_ff) | E: compare P_ff with free-free spectral index between 3.3 cm and 1.3 mm for cores with both measurements | R: optically thin cores have P_ff of 30-80%, optically thicker cores 55-65%; the expected anti-correlation is not observed | F: Early evolution of HII regions is not necessarily monotonic | **refuted**
- H: Core envelope mass grows together with the central protostar | E: compare dust flux with free-free flux and with core class; KS test, Pearson and Spearman correlations | R: dust flux higher for cores with HMC and/or H/UC HII; correlation coefficients above 0.8 | F: Central (proto)star mass may grow simultaneously with the gas envelope, but dust temperature could also explain it | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: getsf chosen as suited to complex protocluster environments; methyl formate chosen as a HMC tracer balancing detectability and reliability  
  > "It is therefore well suited to find cores in complex environments such as high-mass star-forming regions." (3.1 Core catalog); "This study showed that this molecule offers a good compromise between widespread detectability and reliability in tracing HMC." (3.3 Identification of hot molecular cores)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust flux depends on dust temperature, which is not measured; firmer conclusions need core temperatures  
  > "Detailed measurements of core temperatures, which are beyond the scope of this work, are thus needed to draw firmer conclusions." (5.2 Ionization evolution within dust cores)
- Limitation (authors): Protostellar phase lifetime may be a lower limit if HMC or H/UC HII detections are missed  
  > "Our estimation of the lifetime of the massive protostellar phase may be a lower limit if we are missing detections of HMCs or H/UC HII regions." (5.3 Lifetimes)
- Limitation (authors): Small number of objects in W49SW and the outskirts prevents stronger statements  
  > "The small number of objects in W49SW and the W49 outskirts forbids us to make a stronger statement" (5.1 Evolution of Star Forming Cores in W49A)
- Caveat (inferred, ours): Lifetimes rest on a single assumed H/UC HII lifetime (3e5 yr) and constant star formation, with no propagated uncertainty on the 6e4 and 1.4e5 yr values
- Caveat (inferred, ours): HMC detection relies on one methyl formate doublet with no stated detection threshold
- Caveat (inferred, ours): No uncertainties given for fluxes, P_ff, spectral indices or emission measures
- Caveat (inferred, ours): Core fluxes measured at 1.3 mm mix dust and free-free emission; Te fixed at 7000 K for all cores

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Line-free channel list and detailed ALMA-IMF pipeline settings
- Missing: getsf parameters and version
- Missing: VLA X-band image (processed by De Pree et al. 2020) and the unpublished dendrogram catalog
- Missing: Settings of the synthetic spectrum fit and HMC detection criterion
- Missing: Calibration details and array configurations for project 2016.1.00620.S
- Data volume (inferred): Probably hundreds of GB for the raw ALMA measurement sets of a 28-field Band 6 mosaic with four 1.875 GHz spectral windows; tens of GB for cubes (estimate)
- Score (inferred): 3/5, Continuum recipe is inherited from a published pipeline paper and the core catalog table is given, but line-free channels, getsf settings, HMC criteria and VLA processing are not fully given
- Rediscovery candidate: no, Data public status is not stated in the paper and several steps (VLA image, unpublished HII catalog, HMC criteria, line-free channels) are underspecified for a full redo

## Links

- Method: Ginsburg et al. 2022, A&A, 662, A9 (cite: Ginsburg22) (ALMA-IMF imaging and self-calibration pipeline used for the continuum map)
- Method: Men'shchikov 2021, A&A, 649, A89 (cite: 2021Mensh) (getsf source extraction algorithm and post-selection filters)
- Method: Brouillet et al. 2022, A&A, 665, A140 (cite: 2022Brouillet) (methyl formate method for identifying hot molecular cores and continuum/line separation)
- Method: Molet et al. 2019, A&A, 626, A132 (cite: 2019Molet) (method to separate continuum and line emission per pixel)
- Companion: De Pree et al. 2020, AJ, 160, 234 (cite: 2020AJ....160..234D) (source of the VLA X-band 3.3 cm image)
- Companion: Juárez-Gama et al. (in prep.) (dendrogram catalog of H/UC HII regions in W49N used alongside the core catalog)
- Companion: Nony et al. 2023, A&A, 674, A75 (cite: 2023Nony) (earlier getsf core study cited for core mass growth with evolution)
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 134,
 "quotes_ok": 134,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 119,
  "stated": 84,
  "rate": 0.706
 },
 "evidence_ok": true
}
```
