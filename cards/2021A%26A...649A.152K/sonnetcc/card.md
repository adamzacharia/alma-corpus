# The ALPINE-ALMA [CII] survey. Obscured star formation rate density and main sequence of star-forming galaxies at z &gt; 4

`2021A&A...649A.152K` | Astronomy and Astrophysics 2021 | first author: Khusanova, Y. | arXiv: 2007.08384 | DOI: 10.1051/0004-6361/202038944

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Measure the dust-obscured SFR density (SFRD_IR) at z>4 from stacked ALPINE rest-frame FIR continuum, and constrain the main sequence and sSFR evolution at z~4.5 and z~5.5  
  > "We also determine their average and individual SFRs and constrain the main sequence over the stellar mass range" (1.2 Main sequence and sSFR at z>4); "we use a large sample of 118 galaxies observed in the rest-frame FIR with ALMA to determine the" (1.2 Main sequence and sSFR at z>4)
- Target **ALPINE target sample (118 UV-selected star-forming galaxies in COSMOS and ECDFS)**: coordinates _not stated_; z/distance secure spectroscopic redshifts; analysed in bins z~4.5 and z~5.5  
  > "In total, 118 galaxies were observed in the period from May 2018 to January 2019" (2 Data); "The galaxies in ALPINE are chosen in the two well-studied fields, Cosmic Evolution Survey" (2 Data); "All targets have secure spectroscopic redshifts from the rest-frame UV spectra and are imaged with both space and ground-based instruments" (2 Data); distance from spectroscopic redshifts from rest-frame UV spectra (VUDS, DEIMOS 10K)  
  > "In total, 118 galaxies were observed in the period from May 2018 to January 2019" (2 Data); "The galaxies in ALPINE are chosen in the two well-studied fields, Cosmic Evolution Survey" (2 Data); "All targets have secure spectroscopic redshifts from the rest-frame UV spectra and are imaged with both space and ground-based instruments" (2 Data)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam sizes do not exceed 1.6 arcsec  
  > "Since the beam sizes in ALPINE do not exceed 1.6 arcsec" (3.1 Stacking of the rest-frame FIR continuum images)
- max recoverable scale: _not stated_
- sensitivity: 50 μJy/beam at 4.4<z<4.6; 28 μJy/beam at 5.1<z<5.8 (continuum)  
  > "We reached a sensitivity of 50 μJy/beam" (2 Data); "28μJy/beam at 5.1" (2 Data)
- time on source: _not stated_
- observing dates: May 2018 to January 2019  
  > "In total, 118 galaxies were observed in the period from May 2018 to January 2019" (2 Data)
- pi or archival as stated: ALMA Large Program (ALPINE)  
  > "The ALMA Large Program to INvestigate" (1.2 Main sequence and sSFR at z>4)
- Line: [CII] 158 μm (not stated)
- Other facility **VUDS and DEIMOS 10K spectroscopic surveys**: Parent samples and spectroscopic redshifts of the targets  
  > "The targets were primarily selected from two large spectroscopic surveys" (2 Data)
- Other facility **COSMOS photometric catalog and 3D-HST catalog**: Photometry for SED fitting (stellar masses, SFRs, FUV luminosities) in COSMOS and ECDFS  
  > "was used for targets in the COSMOS field" (2 Data); "was used for the ECDFS" (2 Data)
- Other facility **Herschel stacks**: Stacks of Herschel data at z>4 used to test dust SED templates  
  > "made stacks of Herschel data for galaxies at" (Conversion of FIR flux to IR luminosity)
- External data: SED-fitting physical properties (stellar masses, SFRs, rest-frame FUV luminosities) of ALPINE galaxies  
  > "analyzed the multi-wavelength ancillary data in both fields and derived the physical properties of galaxies using SED fitting" (2 Data) [from (cite: Faisst2020)]
- External data: Proxy density functions: UVLFs (Bouwens+15, Finkelstein+15, Ono+18, Pello+18, Khusanova+20) and GSMFs (Song+16, Davidzon+17, Wright+18)  
  > "We do not favor any particular UVLF or GSMF, but use several of them" (4.1 Proxy number density) [from (cite: bouwens_uv_2015; Finkelstein2015; Ono2018; Pello2018; Khusanova2020VUDS; Song2016; Davidzon2017; Wright2018)]
- External data: Dust SED templates used to convert 160 μm flux to L_IR  
  > "There are numerous dust SED templates available in the literature" (Conversion of FIR flux to IR luminosity) [from (cite: Magdis2012; Bethermin2017; AlvarezMarquez2016; Casey2018; Schreiber2018; DeRossi2018; AlvarezMarquez2019)]
- External data: Herschel stacks at z>4 against which templates are compared (chi2)  
  > "made stacks of Herschel data for galaxies at" (Conversion of FIR flux to IR luminosity) [from (cite: Bethermin2020)]
- External data: Main sequence SFR-mass relation used to convert 0.03L* and 100L* limits to mass limits  
  > "Then we use the relation between SFR and mass from the main sequence fit in" (3.2.3 Integration limits) [from (cite: Khusanova2020VUDS)]
- External data: Total SFRD formalism and dust-corrected SFRD curve used as comparison  
  > "The total SFRD can be defined as" (3.2 SFRD measurement: method description) [from (cite: madau_cosmic_2014)]
- Simulation/model as data: Fake Gaussian sources injected into continuum images to test stacking  
  > "we generated a number of fake sources on the images avoiding the center" (3.1 Stacking of the rest-frame FIR continuum images)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The ALMA data were calibrated with the standard ALMA pipeline." (2 Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We then produced the continuum maps, using the task" (2 Data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used natural weighting to maximize SNR." (2 Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Channels at the [CII] position excluded; for non-detections, data within 500 km/s of the expected line position excluded; for detections, a window around the line defined manually  
  > "To produce continuum maps, we excluded all the channels that correspond to the position of the" (2 Data); "excluded data within 500 km/s around the expected position of" (2 Data); "we manually defined the window around the detected emission line" (2 Data)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: beam sizes in ALPINE do not exceed 1.6 arcsec  
  > "Since the beam sizes in ALPINE do not exceed 1.6 arcsec" (3.1 Stacking of the rest-frame FIR continuum images)
- final rms: _not stated_

### Inherited from earlier work

- Details of ALMA data reduction  
  > "More detail on data reduction can be found in" (2 Data) [from (cite: Bethermin2020)]
- Details of SED fitting of ALPINE galaxies  
  > "More detail about the SED fitting of ALPINE galaxies can be found in" (2 Data) [from (cite: Faisst2020)]
- Fake-source FWHM range 0.8 to 1.6 arcsec  
  > "The sources are Gaussian and their FWHM were allowed to vary from 0.8 to 1.6 arcsec" (3.1 Stacking of the rest-frame FIR continuum images) [from (cite: Bethermin2020)]
- Position-offset scatter of 0.12 arcsec for fake sources  
  > "we added random offsets sampled from a Gaussian with $\sigma=0.12$ arcsec" (3.1 Stacking of the rest-frame FIR continuum images) [from (cite: Faisst2020)]
- SFR conversion factors kappa_FUV and kappa_IR (Chabrier IMF)  
  > "The conversion factors are $\kappa_{FUV}=1.5*10^{-10}M_{\odot}year^{-1}L_{\odot}^{-1}$ and $\kappa_{IR}=10^{-10}M_{\odot}year^{-1}L_{\odot}^{-1}$" (3.2 SFRD measurement: method description) [from (cite: kennicutt_global_1998)]
- Bootstrap uncertainty relation between sigma_boot, sigma_phot and population variance  
  > "the bootstrap uncertainty $\sigma_{boot}$ and the photometric noise $\sigma_{phot}$ are related as:" (3.1 Stacking of the rest-frame FIR continuum images) [from (cite: Bethermin2012)]

### Not stated but needed to reproduce (our reading)

- CASA version and ALMA pipeline version
- ALMA project code(s), spectral windows and continuum bandwidth actually used per target
- tclean parameters other than natural weighting (cell, image size, niter, threshold, masking, primary beam correction); continuum maps are taken from Bethermin2020
- Per-target manually defined [CII] windows for detected sources
- Exact bin edges and membership of each stack in mass and M_FUV (only 6-13 galaxies per bin is given)
- How images are weighted and aligned (pixel grid, positions) in the mean stack
- Individual stellar masses, M_FUV and mean redshifts of each stack (from Faisst2020 catalogue)
- emcee set-up: priors, number of walkers and steps, likelihood form and how upper limits enter
- Parameter values of each UVLF/GSMF (Schechter or DPL) and how their uncertainties were sampled
- Which templates enter the mean f_temp and the weighting used for combining PDFs
- Number of main-sequence mass bins and the fit method (priors/likelihood) for the slope
- The Herschel stack fluxes used for the template chi2 test

## Analysis recipe

1. **Make rest-frame FIR continuum maps**: Exclude [CII] channels, then image with tclean using natural weighting  
  > "To produce continuum maps, we excluded all the channels that correspond to the position of the" (2 Data); "We then produced the continuum maps, using the task" (2 Data)
   - software: CASA, tclean
   - parameter: natural weighting  
  > "We used natural weighting to maximize SNR." (2 Data)
   - parameter: non-detections: exclude data within 500 km/s of expected [CII]  
  > "excluded data within 500 km/s around the expected position of" (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack continuum images and measure mean flux**: Mean stacks of all targeted galaxies (detections and non-detections) aligned on UV positions; flux in a 3 arcsec diameter aperture; bootstrap errors  
  > "Here we use the mean stacks of continuum images." (3.1 Stacking of the rest-frame FIR continuum images); "We only use the targeted galaxies and their UV-positions for alignment." (3.1 Stacking of the rest-frame FIR continuum images); "the flux is measured using an aperture of 3 arcsec diameter" (3.1 Stacking of the rest-frame FIR continuum images)
   - parameter: bootstrap: 1000 resamplings, mean and standard deviation give flux and sigma_boot  
  > "We repeat the procedure 1000 times and find the average and standard deviation of the measurement" (3.1 Stacking of the rest-frame FIR continuum images)
   - parameter: 6-13 galaxies per bin  
  > "but to include enough galaxies (6-13) in the bin to have robust average flux measurements" (4.2 <L_IR>-proxy relation)
   - parameter: photometric noise from random apertures in the field, with serendipitous sources and centre masked  
  > "The apertures are then placed at random positions, away from serendipitous sources." (3.1 Stacking of the rest-frame FIR continuum images)
   - fitting: _not stated_
   - validation: Field flux compatible with zero; fake-source recovery test (step 3)  
  > "The average flux in the field is compatible with zero as expected" (3.1 Stacking of the rest-frame FIR continuum images)
3. **Test stacking with injected fake sources**: Inject Gaussian fake sources with random position offsets, stack with the same procedure, compare F_out to F_in via Delta F / sigma_out  
  > "we generated a number of fake sources on the images avoiding the center" (3.1 Stacking of the rest-frame FIR continuum images); "Fig. [1](#test_fig) shows the distribution of $\Delta{F}/\sigma_{out}=(F_{out}-F_{in})/\sigma_{out}$." (3.1 Stacking of the rest-frame FIR continuum images)
   - parameter: 250 trials; F_in 0.01 to 0.18 mJy; 6 to 13 images per stack  
  > "We performed the procedure 250 times, varying the $F_{in}$ flux value in the range from 0.01 to 0.18 mJy or $\sim$0.25-3.5$\sigma_{phot}$ and the number of images from 6 to 13 (as we used later for the stacks)." (3.1 Stacking of the rest-frame FIR continuum images)
   - assumption: Gaussian sources, FWHM 0.8 to 1.6 arcsec; position offsets Gaussian with sigma 0.12 arcsec  
  > "The sources are Gaussian and their FWHM were allowed to vary from 0.8 to 1.6 arcsec" (3.1 Stacking of the rest-frame FIR continuum images)
   - fitting: _not stated_
   - validation: Mean of Delta F/sigma_out -0.03 (compatible with zero), standard deviation 1.13  
  > "The mean of the distribution is -0.03 and the standard deviation is 1.13." (3.1 Stacking of the rest-frame FIR continuum images)
4. **Convert 160 um flux to total IR luminosity**: Scale the flux to a dust SED template at the mean redshift of the stack and integrate 8-1000 um; use the mean conversion factor of templates passing a Herschel-stack chi2 test  
  > "To convert the rest-frame 160 μm flux to IR luminosity, we scale our flux measurement to the dust SED template and then integrate it from 8 to 1000 μm." (Conversion of FIR flux to IR luminosity); "we use the mean redshift of galaxies in stacks for that conversion" (Conversion of FIR flux to IR luminosity)
   - parameter: templates with reduced chi2 > 1.5 in at least one redshift bin discarded  
  > "We discard the templates with reduced $\chi^2$ \> 1.5 in at least one of the redshift bins" (Conversion of FIR flux to IR luminosity)
   - parameter: <f_temp> = 0.13 +/- 0.02 (z~4.5), 0.12 +/- 0.03 (z~5.5)  
  > "We use average conversion factors $\langle f_{temp, z\sim4.5} \rangle = 0.13 \pm 0.02$ and $\langle f_{temp, z\sim5.5} \rangle = 0.12 \pm 0.03$" (3.2.1 Measuring IR luminosity density)
   - assumption: L_IR depends on the chosen dust SED template since only one SED point is measured  
  > "Since we only obtain a measurement of one point in SED, our conversion to IR luminosity will depend on dust SED templates." (Conversion of FIR flux to IR luminosity)
   - fitting: _not stated_
   - validation: Templates compared with Herschel stacks; modified blackbody fit to the stacks gives T_dust 41 +/- 1 K (z~4.5) and 43 +/- 5 K (z~5.5)  
  > "We tested a number of templates against the stacking of Herschel data and only used the ones, which are compatible with the Herschel stacks" (4.3.3 The total SFRD)
5. **Fit the <L_IR>-proxy relation**: Power-law fit of average L_IR against M* or M_FUV in bins, with upper limits for negative stacks and for mass bins below the completeness limit  
  > "We fit this relation with a power law using the MCMC method with" (4.2 <L_IR>-proxy relation); "we use 3.5$\sigma_{phot}$ upper limits only when the measured fluxes of the stack have negative values." (4.2 <L_IR>-proxy relation)
   - software: emcee, python
   - parameter: mass bins below log M_lim/Msun = 9.6 treated as upper limits (flux + 3 sigma)  
  > "we consider the results as upper limits in bins below $\log M_{lim}/M_{\odot}=9.6$" (4.2 <L_IR>-proxy relation)
   - assumption: the fit must not go above upper limits at each step  
  > "checking at each step that the fit does not go above upper limits" (4.2 <L_IR>-proxy relation)
   - fitting: emcee MCMC power-law fit; priors and likelihood not stated; chains reused for SFRD  
  > "We use the MCMC chains later when deriving the $SFRD_{IR}$." (4.2 <L_IR>-proxy relation)
   - validation: Two points below M_lim excluded from the fit agree with the power law  
  > "are in a very good agreement with the power law fit to the points above $M_{lim}$" (4.2 <L_IR>-proxy relation)
6. **Integrate L_IR-proxy relation with proxy density to get SFRD_IR**: rho_IR = integral of <L_IR>(x) phi(x) dx using each UVLF or GSMF; MCMC chains give an SFRD_IR chain/PDF; lower limit over observed range, total by extrapolation; PDFs from different density functions combined  
  > "convolving the volume density distribution of this proxy with the mean LIR-proxy relation" (3.2.1 Measuring IR luminosity density); "we use the MCMC chains of fit parameters to produce a resulting $SFRD_{IR}$ chain." (4.3.1 The lower limit); "we combine the PDFs obtained with different proxy density functions from the literature" (4.3.2 Extrapolated SFRD_IR)
   - parameter: lower limit range: 8.35 <= log(M*/Msun) <= 10.5 and -23.3 <= M_FUV <= -20.0  
  > "The integration limits are $8.35\leq\log(M_*/M_{\odot})\leq10.5$ for masses and $-23.3\leq M_{FUV}\leq-20.0$ for FUV magnitudes." (4.3.1 The lower limit)
   - parameter: extrapolation range 0.03L* to 100L*: M_FUV = -17 to -26; log(M*/Msun) = 6.0 to 12.4  
  > "These are $M_{FUV}=-17$ and $M_{FUV}=-26$, respectively." (3.2.3 Integration limits); "$\log(M_*/M_{\odot})=6.0$ for the lower limit and $\log(M_*/M_{\odot})=12.4$ for the upper limit" (3.2.3 Integration limits)
   - parameter: reported lower limit = lowest PDF value minus 1 sigma  
  > "we show the lowest value minus 1$\sigma$ as our lower limits for the IR contribution to SFRD." (4.3.1 The lower limit)
   - assumption: L_IR-proxy relation is the same at all FUV magnitudes and masses when extrapolating  
  > "we assume that the $\langle L_{IR}\rangle-proxy$ relation is the same at all FUV-magnitudes and masses" (4.3.2 Extrapolated SFRD_IR)
   - fitting: _not stated_
   - validation: Results with the two proxies and different density functions agree within the errors  
  > "The measurements obtained with FUV as well as $M_*$ as a proxy agree well with each other within the errors in both redshift bins." (4.3 Infrared contribution to SFRD)
7. **Total SFRD and obscured fraction**: Sum SFRD_UV,uncorr and SFRD_IR from ALPINE; average literature and ALPINE points per redshift bin to get SFRD_IR / total SFRD  
  > "by summing the $SFRD_{UV,uncorr}$ with the $SFRD_{IR}$ from ALPINE" (4.3.3 The total SFRD); "to calculate the average $SFRD_{IR}$ and $SFRD_{UV,uncorr}$ in each redshift bin and the ratio of $SFRD_{IR}$ to the total SFRD" (4.3.3 The total SFRD)
   - assumption: Chabrier IMF to convert luminosities to SFRs  
  > "initial mass function (IMF) to convert luminosities to SFRs" (1.2 Main sequence and sSFR at z>4)
   - fitting: _not stated_
   - validation: Compared with dust-corrected FUV SFRD from literature, Gruppioni+20 and Loiacono+20; agree within errors  
  > "The results are in agreement with the FUV based estimates corrected for dust attenuation from the literature within the error bars at both redshifts." (4.3.3 The total SFRD)
8. **Derive main sequence and sSFR**: In each mass bin, average SFR = kappa_FUV <L1600> + kappa_IR <L_IR>; power-law fit of SFR against mass in two redshift bins; sSFR measured in 9.6<log M*<9.8  
  > "In each mass bin, we derive average SFR as $\langle SFR\rangle=\kappa_{FUV}\langle L_{1600}\rangle+\kappa_{IR}\langle L_{IR}\rangle$." (5 Star-forming main sequence and sSFR evolution); "We fitted the relation between SFR and mass with a power law" (5 Star-forming main sequence and sSFR evolution); "We measured the sSFR in the mass range $9.6<\log(M_*/M_{\odot})<9.8$ as in" (5 Star-forming main sequence and sSFR evolution)
   - parameter: two redshift bins 4.4<z<4.7 and 5.1<z<5.8; stacked results below the completeness limit treated as upper limits (only three points fitted at z~5.5)  
  > "Therefore, we only used three points to fit our data and the fit is subject to larger uncertainties." (5 Star-forming main sequence and sSFR evolution)
   - assumption: LambdaCDM, Omega_L=0.70, Omega_m=0.30, h=0.7  
  > "Throughout the paper, we use a $\Lambda$CDM cosmology with $\Omega_{\Lambda}=0.70$, $\Omega_m=0.30$ and $h=0.7$." (1.2 Main sequence and sSFR at z>4)
   - fitting: power-law fit; method not stated  
  > "We fitted the relation between SFR and mass with a power law" (5 Star-forming main sequence and sSFR evolution)
   - validation: Compared with literature main sequences (Santini+17, Tasca+15, Heinis+13, Khusanova+20, Schreiber+15) and sSFR measurements  
  > "The main sequence is well-defined and is in very good agreement with previous results from the literature" (5 Star-forming main sequence and sSFR evolution)

## Software

- **CASA** : ALMA data reduction and continuum imaging  
  > "The CASA software was used for the data reduction" (2 Data)
- **tclean** : making continuum maps  
  > "We then produced the continuum maps, using the task" (2 Data)
- **ALMA pipeline** : calibration of the ALMA data  
  > "The ALMA data were calibrated with the standard ALMA pipeline." (2 Data)
- **emcee** : MCMC power-law fits of the L_IR-proxy relation  
  > "We fit this relation with a power law using the MCMC method with" (4.2 <L_IR>-proxy relation)
- **LePhare** : SED fitting of ALPINE galaxies (stellar masses, SFRs, FUV luminosities), done in Faisst+20  
  > "The SED fitting is performed with the LePhare package" (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Targets detected at SNR>=3.5 (95% purity) | 23 of 118 (19%) | not stated | galaxies | 1 | Only 23 out of 118 (19%) of the ALPINE targets are detected with such significance. |
| Photometric noise sigma_phot on stacks (typically 8 images) | 0.05 | not stated | mJy | 2 | is on average $\sigma_{phot}=0.05$ mJy for the typical number of stacked images (8) |
| Average field flux | 0.1 | 50.0 | μJy | 2 | ($F_{field}=0.1\pm50.0$ μJy) |
| Stacking test: mean of Delta F / sigma_out | -0.03 | standard deviation 1.13 | dimensionless | 3 | The mean of the distribution is -0.03 and the standard deviation is 1.13. |
| Mean f_temp (z~4.5) | 0.13 | 0.02 | dimensionless | 4 | We define the mean conversion factors from the remaining templates $\langle f_{temp, z\sim4.5} \rangle = 0.13 \pm 0.02$ |
| Mean f_temp (z~5.5) | 0.12 | 0.03 | dimensionless | 4 | $\langle f_{temp, z\sim5.5} \rangle = 0.12 \pm 0.03$ |
| T_dust from modified blackbody fit to Herschel stacks (z~4.5) | 41 | 1 | K | 4 | The best fit of modified black body to these stacks gives the dust temperature $T_{dust}=41\pm1$ K at $z\sim4.5$ and $T_{dust}=43\pm5$ K at $z\sim5.5$ |
| T_dust from modified blackbody fit to Herschel stacks (z~5.5) | 43 | 5 | K | 4 | The best fit of modified black body to these stacks gives the dust temperature $T_{dust}=41\pm1$ K at $z\sim4.5$ and $T_{dust}=43\pm5$ K at $z\sim5.5$ |
| Stellar mass completeness limit log M_lim/Msun | 9.6 | not stated | dex(Msun) | 5 | the mass limit is $\log M_{lim}/M_{\odot}=9.6$ at both redshifts |
| Population variance in L_IR-M_FUV bins, z~4.5 | ~0.91 | not stated | dex | 5 | The population variance at $z\sim4.5$ is $\sim0.91$ dex on average and at $z\sim5.5$ it is $\sim0.47$ dex |
| Population variance, z~5.5 | ~0.47 | not stated | dex | 5 | The population variance at $z\sim4.5$ is $\sim0.91$ dex on average and at $z\sim5.5$ it is $\sim0.47$ dex |
| log SFRD_IR lower limit, z~4.5 (UVLF+GSMF combined) | -2.44 | not stated | log(Msun/yr/Mpc^3) | 6 | We determined the robust lower limits $\log SFRD_{IR} (M_{\odot}yr^{-1}Mpc^{-3}) =-2.44$ and $\log SFRD_{IR} (M_{\odot}yr^{-1}Mpc^{-3}) =-2.67$ at z$\sim$4.5 and 5.5 respectively |
| log SFRD_IR lower limit, z~5.5 (UVLF+GSMF combined) | -2.67 | not stated | log(Msun/yr/Mpc^3) | 6 | We determined the robust lower limits $\log SFRD_{IR} (M_{\odot}yr^{-1}Mpc^{-3}) =-2.44$ and $\log SFRD_{IR} (M_{\odot}yr^{-1}Mpc^{-3}) =-2.67$ at z$\sim$4.5 and 5.5 respectively |
| log SFRD_IR extrapolated total, z~4.5, GSMF (mass proxy) combined | -1.07 | +0.28/-0.23 | log(Msun/yr/Mpc^3) | 6 | $-1.07_{-0.23}^{+0.28}$ |
| log SFRD_IR extrapolated total, z~5.5, GSMF (mass proxy) combined | -1.50 | +0.38/-0.39 | log(Msun/yr/Mpc^3) | 6 | $-1.50_{-0.39}^{+0.38}$ |
| log SFRD_IR extrapolated total, z~4.5, UVLF (M_FUV proxy) combined | -1.48 | +0.24/-0.25 | log(Msun/yr/Mpc^3) | 6 | $-1.48_{-0.25}^{+0.24}$ |
| log SFRD_IR extrapolated total, z~5.5, UVLF (M_FUV proxy) combined | -1.64 | +0.23/-0.24 | log(Msun/yr/Mpc^3) | 6 | $-1.64_{-0.24}^{+0.23}$ |
| log SFRD_IR total, z~4.5, UVLF+GSMF combined | -1.28 | +0.38/-0.36 | log(Msun/yr/Mpc^3) | 6 | $-1.28_{-0.36}^{+0.38}$ |
| log SFRD_IR total, z~5.5, UVLF+GSMF combined | -1.60 | +0.36/-0.28 | log(Msun/yr/Mpc^3) | 6 | $-1.60_{-0.28}^{+0.36}$ |
| Dust-obscured fraction of SFRD, z~4.5 | 68% | +18/-25 % | percent | 7 | We find the infrared contribution to the total SFRD equal to $68_{-25}^{+18}\%$ and $61_{-25}^{+20}\%$ at z$\sim$4.5 and z$\sim$5.5 respectively. |
| Dust-obscured fraction of SFRD, z~5.5 | 61% | +20/-25 % | percent | 7 | We find the infrared contribution to the total SFRD equal to $68_{-25}^{+18}\%$ and $61_{-25}^{+20}\%$ at z$\sim$4.5 and z$\sim$5.5 respectively. |
| Main-sequence slope alpha, z~4.5 | 0.99 | 0.08 | dimensionless | 8 | found a slope $\alpha=0.99\pm0.08$ at z$\sim$4.5 |
| Main-sequence slope alpha, z~5.5 | 0.66 | 0.21 | dimensionless | 8 | At z$\sim$5.5, we obtain a shallower slope $\alpha=0.66\pm0.21$. |
| log sSFR at 9.6<log M*<9.8, z~4.5 | -8.4 | 0.18 | log(Gyr^-1) | 8 | The average sSFR is $\log{sSFR}(Gyr^{-1})=-8.4\pm0.18$ and $\log{sSFR}(Gyr^{-1})=-8.45\pm0.16$ at z$\sim$4.5 and z$\sim$5.5 respectively. |
| log sSFR at 9.6<log M*<9.8, z~5.5 | -8.45 | 0.16 | log(Gyr^-1) | 8 | The average sSFR is $\log{sSFR}(Gyr^{-1})=-8.4\pm0.18$ and $\log{sSFR}(Gyr^{-1})=-8.45\pm0.16$ at z$\sim$4.5 and z$\sim$5.5 respectively. |

## Qualitative findings

- L_IR is well correlated with both M* and M_FUV, and the L_IR-M* relation evolves more strongly with redshift than L_IR-M_FUV  
  > "The $\langle L_{IR}\rangle$ is clearly well correlated with both proxies." (4.2 <L_IR>-proxy relation); "Interestingly, we observe a stronger evolution with redshift of the $L_{IR}-M_*$ relation than the $L_{IR}-M_{FUV}$ relation." (4.2 <L_IR>-proxy relation)
- Individual continuum detections mostly lie above the stacked main sequence, so stacking is needed for unbiased average SFRs  
  > "As expected, most of them are above the main sequence since they represent the brightest galaxies with high SFRs." (5 Star-forming main sequence and sSFR evolution)
- Lower-limit SFRD_IR at z~5.5 is far above the Koprowski+17 extrapolation  
  > "these results are in severe disagreement with the results by" (4.3.1 The lower limit)

## Claim tuples

- H: How large is the dust-obscured SFRD at z>4 in a UV-selected sample? | E: Stack ALPINE continuum by mass or M_FUV bins, convert to L_IR, integrate with literature UVLF/GSMF | R: log SFRD_IR lower limits -2.44 (z~4.5) and -2.67 (z~5.5); extrapolated totals about -1.1 to -1.6 | F: Dust-obscured star formation is substantial at z>4 (68% and 61% of total SFRD) | **supported**
- H: Does SFRD_IR drop steeply at z>4 as in IR luminosity function studies? | E: Compare ALPINE lower limits with the Koprowski+17 extrapolation | R: ALPINE lower limit at z~5.5 is log SFRD_IR = -2.67 versus -3.95 extrapolated from Koprowski+17 | F: A very steep decline of SFRD_IR is disfavoured; SFRD_IR approaches SFRD_FUV,uncorr but only possibly crosses it at z>5 | **supported**
- H: Is the total SFRD at z>4 consistent with the Madau and Dickinson fit? | E: Sum SFRD_FUV,uncorr and ALPINE SFRD_IR | R: 0.5 dex and 0.3 dex above the Madau and Dickinson fit, 1.4 and 1.2 sigma tension at z~4.5 and 5.5 | F: Total SFRD evolution at z>4 is possibly shallower than the best fit, but the uncertainties preclude firm conclusions | **partially**
- H: What is the main sequence slope at z~4.5 and z~5.5 from stacked FUV+IR SFRs, and does it evolve? | E: Power-law fit of average SFR vs mass in two redshift bins | R: alpha = 0.99+/-0.08 (z~4.5) and 0.66+/-0.21 (z~5.5), difference 1.5 sigma | F: No significant evolution of the main sequence slope between z~4.5 and z~5.5; agrees with earlier UV, optical and Herschel results | **supported**
- H: Does sSFR rise steeply with redshift at z>4 as cold-accretion models predict? | E: Average sSFR at 9.6<log M*<9.8 at z~4.5 and z~5.5 | R: log sSFR = -8.4+/-0.18 and -8.45+/-0.16 Gyr^-1 | F: sSFR evolution is shallower or absent versus cold-accretion expectations; other mechanisms must matter | **supported**

## Reasoning

- Why this data: ALPINE is a large UV-selected representative sample observed in rest-frame FIR, allowing direct L_IR rather than IRX-beta  
  > "allows estimating SFRs without relying on IRX-$\beta$ relation and by directly measuring the total infrared luminosities" (1.2 Main sequence and sSFR at z>4)
- Why this method: Stacking is used because most targets are not individually detected; proxy-based integration is used because ALPINE is not volume-limited so an IR LF cannot be built  
  > "Therefore, we used stacking to measure the average flux of galaxies with similar physical properties." (3.1 Stacking of the rest-frame FIR continuum images); "Since ALPINE is not a volume-limited sample, it is rather difficult to determine the IR LF from the target sample" (3.2.1 Measuring IR luminosity density)
- Alternative: Other continuum flux methods (Gaussian fit in map and uv plane, peak flux) were tested by Bethermin+20; peak flux inconsistent; only aperture photometry usable on stacks  
  > "has tested three other methods of continuum flux measurements in addition to aperture photometry" (3.1 Stacking of the rest-frame FIR continuum images)
- Alternative: Dust SED templates with reduced chi2 > 1.5 against Herschel stacks were discarded; DeRossi+18 used only for 5<z<6  
  > "We discard the templates with reduced $\chi^2$ \> 1.5 in at least one of the redshift bins" (Conversion of FIR flux to IR luminosity)
- How they decided it was enough: _not stated_
- Limitation (authors): Low-mass bins are biased toward high SFR because of the FUV selection, so they are upper limits  
  > "Below this limit we are likely to miss galaxies with faint FUV magnitudes, biasing SFR towards higher values." (3.2.2 The choice of proxy)
- Limitation (authors): Highly obscured IR-bright galaxies missing from the FUV-selected sample are not included  
  > "Since we used a sample of galaxies detected in FUV, we did not take into account the contribution from highly obscured and purely IR galaxies" (4.3.3 The total SFRD)
- Limitation (authors): L_IR conversion relies on one point of the IR SED and dust SED templates  
  > "the conversion from the 160 μm flux to $L_{IR}$ in this work is based only on one point in the infrared SED" (4.3.3 The total SFRD)
- Caveat (inferred, ours): Conclusions quote mass-proxy totals as -1.07 and -1.48 but Table 2 gives GSMF z~5.5 = -1.50 and UVLF z~4.5 = -1.48, so the text and table mix up proxies
- Caveat (inferred, ours): Bin edges, membership and per-bin fluxes are not tabulated, so stacks cannot be rebuilt from the text
- Caveat (inferred, ours): Mass-proxy results rely on SED-fit masses and extrapolation over about 6 dex in mass
- Caveat (inferred, ours): Main-sequence slope at z~5.5 rests on three points and has large uncertainty
- Caveat (inferred, ours): L_IR from a single 160 um flux point; T_dust and template choice dominate systematics

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data products made available at the CESAM data center  
  > "This work is based on data products made available at the CESAM data center" (Acknowledgements)
- Missing: ALMA project code(s), CASA/pipeline versions and tclean parameters (deferred to Bethermin+20)
- Missing: Per-bin stellar mass, M_FUV and stacked flux tables
- Missing: emcee priors, likelihood and chain settings
- Missing: UVLF/GSMF parameter values and sampling of their uncertainties
- Missing: Stacking code is described but not stated to be released
- Data volume (inferred): Not stated; 118 targets, so roughly tens to hundreds of GB of visibilities, or a few GB if starting from released continuum images
- Score (inferred): 3/5, Final numbers and methods are given, but bin definitions, project code, imaging parameters and fit settings are deferred or missing, and stacking code is not stated as public
- Rediscovery candidate: no, Paper prints no project code or public-data statement and omits the bin definitions and fit settings needed to redo the stacks; results are numeric but recipe is incomplete

## Links

- Method: (cite: Bethermin2020) (ALPINE data reduction, continuum measurement methods and Herschel stacks)
- Method: (cite: Faisst2020) (SED fitting, stellar masses, SFRs and FUV luminosities of ALPINE galaxies)
- Method: (cite: lefevre_alpine_2019) (ALPINE survey design and sample selection)
- Companion: (cite: Gruppioni2020) (SFRD_IR from non-target ALPINE sources, compared with this work)
- Companion: (cite: Loiacono2020) ([CII] luminosity function SFRD of non-target sources, compared with this work)
- Companion: (cite: Khusanova2020VUDS) (VUDS UVLF and main sequence used for density function and integration limits)
- Companion: (cite: Fujimoto2020) (Radial profiles showing ALPINE sources are compact in the rest-frame FIR)
- Related: ALPINE (ALMA Large Program to INvestigate [CII] at Early times)
- Related: VUDS
- Related: DEIMOS 10K Spectroscopic Survey
- Related: CANDELS
- Related: COSMOS
- Related: ECDFS

## Checks

```json
{
 "quotes": 137,
 "quotes_ok": 137,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00428.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 25,
 "numeric_problems": 0,
 "fill": {
  "facts": 115,
  "stated": 80,
  "rate": 0.696
 },
 "evidence_ok": true
}
```
