# Spatially resolved dust properties and quasar-galaxy decomposition of a hyper-luminous infrared galaxy at z = 4.4

`2023MNRAS.523.4654T` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Tsukui, Takafumi | arXiv: 2302.07272 | DOI: 10.1093/mnras/stad1464

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Derive resolved dust temperature maps of the z=4.4 quasar host BRI 1335-0417, separate AGN-heated warm dust (unresolved point source) from star-formation-heated cold dust, and re-estimate the SFR and SFR surface density  
  > "this paper aims to (1) derive a resolved dust temperature map and clarify the heating source of the dust, (2) separate the warm dust heated by AGN and cold dust associated with the host galaxy" (1 Introduction)
- Target **BRI 1335-0417**: coordinates RA = 204.514232 deg, Dec = -4.543055 deg (reference position for offsets)  
  > "a quasar host galaxy at a redshift of $z = 4.4704$ (cite: Guilloteau1997-xe)" (1 Introduction); "the RA and Dec offsets are given relative to the position RA$=204.514232$ deg and Dec$=-4.543055$ deg" (3.1 The resolved FIR continuum and [C II] emission); "providing an angular size distance $D_\mathrm{A}=1375$ Mpc and a luminosity distance $D_\mathrm{L}=40202$ Mpc at the redshift of 4.4074." (1 Introduction); z/distance z = 4.4704 (also printed as 4.4074 in the cosmology sentence); D_A = 1375 Mpc, D_L = 40202 Mpc  
  > "a quasar host galaxy at a redshift of $z = 4.4704$ (cite: Guilloteau1997-xe)" (1 Introduction); "the RA and Dec offsets are given relative to the position RA$=204.514232$ deg and Dec$=-4.543055$ deg" (3.1 The resolved FIR continuum and [C II] emission); "providing an angular size distance $D_\mathrm{A}=1375$ Mpc and a luminosity distance $D_\mathrm{L}=40202$ Mpc at the redshift of 4.4074." (1 Introduction); distance from redshift from Guilloteau et al. 1997 (cite: Guilloteau1997-xe); flat LCDM with H0 = 70 km/s/Mpc, Omega_M = 0.3  
  > "a quasar host galaxy at a redshift of $z = 4.4704$ (cite: Guilloteau1997-xe)" (1 Introduction); "the RA and Dec offsets are given relative to the position RA$=204.514232$ deg and Dec$=-4.543055$ deg" (3.1 The resolved FIR continuum and [C II] emission); "providing an angular size distance $D_\mathrm{A}=1375$ Mpc and a luminosity distance $D_\mathrm{L}=40202$ Mpc at the redshift of 4.4074." (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00394.S, 2018.1.01103.S
- bands: Band 4 (2080 um), Band 7 (869 um), Band 9 (484 um)  
  > "ALMA Band 4, Band 7, and Band 9 observations of BRI 1335-0417 were carried out as part of the programs" (2.1 ALMA imaging); "observing wavelength 2080 $\ensuremath{\mu}m$ in Band 4, 869 $\ensuremath{\mu}m$ in Band 7, and 484 $\ensuremath{\mu}m$ in Band 9" (2.1 ALMA imaging)
- frequencies and spectral setup: Observations targeted CO(7-6) (Band 4) and [C II] (Band 7) lines plus underlying continuum; continuum at rest-frame 385, 161, 90 um for Band 4, 7, 9  
  > "These observations targeted emission lines, including CO(7-6) (Band 4) and \[C II\] (Band 7)" (2.1 ALMA imaging); "corresponding to rest-frame 385 $\ensuremath{\mu}m$, 161 $\ensuremath{\mu}m$, 90 $\ensuremath{\mu}m$, respectively" (2.1 ALMA imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Synthesized beams (maj/min/PA, arcsec/arcsec/deg): Band 4 0.21/0.14/85; Band 7 0.19/0.16/75; Band 9 0.21/0.16/-53; [CII] 0.19/0.16/82; CO(7-6) 0.23/0.16/84  
  > "(Band 4) | 6.58 | 0.21/0.14/85" (Table 1); "(Band 7) | 25.9 | 0.19/0.16/75" (Table 1); "(Band 9) | 186 | 0.21/0.16/-53" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Rms noise (uJy/beam): Band 4 6.58; Band 7 25.9; Band 9 186; [CII] 389; CO(7-6) 101  
  > "(Band 4) | 6.58 | 0.21/0.14/85" (Table 1); "(Band 7) | 25.9 | 0.19/0.16/75" (Table 1); "(Band 9) | 186 | 0.21/0.16/-53" (Table 1)
- time on source: Band 7: 1 h (other bands not stated)  
  > "The relatively short (1h) Band 7 observation relying on the brightness of the source" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
- observing dates: _not stated_
- pi or archival as stated: PI = González López, Jorge; data public in ALMA archive  
  > "#2017.1.00394.S, and #2018.1.01103.S (PI=González López, Jorge)." (2.1 ALMA imaging); "The ALMA data we use in this work are publicly available in <https://almascience.nrao.edu/aq/>." (Data Availability)
- Line: CO 7-6 (not stated)
- Line: C+ [C II] (not stated)
- Other facility **HST STIS/50CCD (GO-8572)**: Archival optical image used for visualization and pointing check of the quasar (consistent with point source)  
  > "The data were taken as a part of program GO-8572 (PI=L. Storrie-Lombardi) in January 2001" (2.2 HST imaging); "we only use the data for visualization purposes" (2.2 HST imaging)
- Other facility **Gaia**: Astrometric calibration of the HST image offset  
  > "We identify the BRI 1335-0417 in the image using three Gaia sources available in the field of view" (2.2 HST imaging)
- Other facility **Herschel PACS/SPIRE**: Integrated FIR photometry (PACS 70, 160; SPIRE 250 used; SPIRE 350 and 500 excluded for blending)  
  > "HERSCHEL PACS 160 | 160 | 20.976 | 7.838 | HPPSC" (Table A1); "because BRI 1335-0417 is not sufficiently separated from a nearby bright source at" (3.3 Global SED of the galaxy)
- Other facility **Spitzer IRAC/MIPS**: Mid-IR photometry for the global SED  
  > "Spitzer MIPS24 | 24.00 | 1.484 | 0.215 | SEIP" (Table A1)
- Other facility **VLA**: Radio photometry (from literature) for the global SED  
  > "VLA | 61685 | 0.076 | 0.011 | (cite: Carilli1999-mo)" (Table A1)
- Other facility **IRAM interferometer**: 1350 um photometry point from literature  
  > "IRAM interferometer | 1350 | 5.6 | 1.1 | (cite: Guilloteau1997-xe)" (Table A1)
- Other facility **Pan-STARRS1, VISTA, 2MASS, WISE**: Optical/near-IR photometry (from literature) for the panchromatic SED  
  > "Pan-STARRS1-g | 0.477 | 0.0099 | 3.100e-04 | (cite: Chambers2016-ik)" (Table A1); "WISE W1 | 3.350 | 0.140 | 7.000e-03 | (cite: Lasker2021-lr)" (Table A1)
- External data: ALMA Band 6/3 photometry at 1110 um (9.0 mJy) and 2012 um (1.17 mJy) used as SED points  
  > "ALMA | 1110 | 9.0 | 0.9 | (cite: Lu2018-fd)" (Table A1); "ALMA | 2012 | 1.17 | 0.12 | (cite: Lu2018-fd)" (Table A1) [from (cite: Lu2018-fd)]
- External data: Total molecular gas mass from CO(2-1), used for the gas-to-dust ratio  
  > "if we adopt a total gas mass derived by (cite: Jones2016-cj) from CO (2-1)" (3.3 Global SED of the galaxy) [from (cite: Jones2016-cj)]
- External data: Disk geometry (position angle 7.6 deg, inclination 37.3 deg) from [C II] kinematic modelling  
  > "We calculate the de-projected radius using the thin disk geometry proposed in (cite: tsukui2021-vl) (Position angle 7.6 deg, inclination 37.3 deg)" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED) [from (cite: tsukui2021-vl)]
- External data: Previous SFR estimate 5040 +/- 1300 Msun/yr from unresolved SED  
  > "from modelling of the spatially-unresolved spectral energy distribution (SED) with thermal dust and synchrotron emission components (cite: Wagg2014-bh)" (1 Introduction) [from (cite: Wagg2014-bh)]
- External data: Dust opacity kappa_0 = 5.1 cm^2/g at nu_0 = 1199.1 GHz  
  > "$\kappa_0=5.1$ cm$^2$ g$^{-1}$ is the dust opacity at a reference frequency $\nu_0=1199.1$ GHz (cite: Draine2007-ou)" (3.2 Dust SED modelling) [from (cite: Draine2007-ou)]
- External data: alpha_CO = 0.8 and r21 = 0.85 used for CO-based gas mass  
  > "using the standard conversion factor for SMGs $\alpha_{\mathrm{CO}}=0.8$ M$_\odot$ pc$^{-2}$/ (K km s$^{-1}$) (cite: Bolatto2013-ch)" (3.3 Global SED of the galaxy); "(cite: Carilli2013-im)" (3.3 Global SED of the galaxy) [from (cite: Bolatto2013-ch); (cite: Carilli2013-im)]
- External data: [C II] mass-to-light ratio for gas mass tracer comparison: M_gas/L_[CII] = 30 Msun/Lsun  
  > "(cite: Zanella2018-er) proposed the \[C II\] luminosity as a molecular gas mass tracer" (3.5 Comparison of the derived dust mass profile and other gas mass tracer profiles) [from (cite: Zanella2018-er)]
- External data: [C II]-SFR calibration used to compare SFR surface density  
  > "using the calibration of (cite: De_Looze2011-jm)" (4.3 AGN-subtracted dust properties) [from (cite: De_Looze2011-jm)]
- External data: Herschel/Spitzer/optical/VLA catalogue photometry listed in Table A1 (not measured by the authors)  
  > "The photometric data from Spitzer and Herschel we use in this work are publicly available at doi:" (Data Availability) [from (cite: Marton2017-nl); SEIP; (cite: Chambers2016-ik); (cite: Lasker2021-lr); (cite: Carilli1999-mo)]
- Simulation/model as data: STARDUST templates: QSO template, AGN-heated dust template (Mullaney et al. 2011) and cold dust template (Draine & Li 2007)  
  > "a QSO template dominating in the rest-frame UV to optical bands (cite: 2016ApJ...817...55S), an AGN-heated dust component (cite: Mullaney2011-sn) dominating in the rest-frame MIR bands" (4.2.2 Stardust panchromatic SED modelling)

## Processing

### Calibration

- pipeline or manual: Standard CASA pipeline calibration  
  > "We performed standard calibration and data reduction using the Common Astronomy Software Application (CASA; (cite: CASA_Team2022-cl)) pipeline" (2.1 ALMA imaging)
- casa version: CASA 5.1.1-5 (Band 7); CASA 5.4.0-70 (Band 4 and Band 9)  
  > "We used the same CASA version as used in the quality assurance at the ALMA Observatory, which is 5.1.1-5 for Band 7, and 5.4.0-70 for Band 4 and Band 9 data" (2.1 ALMA imaging (footnote))
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Flux and bandpass: J1337-1257 (Band 4, 7), J1256-0547 (Band 9); phase: J1332-0509 (Band 4), J1336-0829 (Band 7, 9)  
  > "The flux and bandpass were calibrated using the quasars J1337-1257 for Band 4 and Band 7, and J1256-0547 for Band 9 data." (2.1 ALMA imaging); "The phase was calibrated using the quasars J1332-0509 for Band 4 and J1336-0829 for Band 7 and Band 9." (2.1 ALMA imaging)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 1.0 for CO(7-6) cube; robust = 0.5 for all others  
  > "The visibility data were weighted using a Briggs weighting scheme with a robust parameter of 1.0 for the CO(7-6) line data cube to improve the sensitivity and 0.5 for others" (2.1 ALMA imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Linear fit to line-free channels, subtracted in the visibility plane  
  > "We estimated the flux density of the underlying continuum emission by fitting a linear function to the identified line-free channels and subtracted it from the data cube in the visibility plane." (2.1 ALMA imaging)
- line free channels: Identified with HIF_FINDCONT in CASA, plus manual removal of channels hit by atmospheric absorption (ranges not given)  
  > "We identified line-free channels using the HIF\_FINDCONT task in CASA and additionally removed channels affected by atmospheric absorption." (2.1 ALMA imaging)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Images convolved to the smallest common beam with COMMON_BEAM in SPECTRAL-CUBE  
  > "we convolved images to have the same spatial resolution with the smallest common beam size, using COMMON\_BEAM in the SPECTRAL-CUBE package." (2.1 ALMA imaging)
- final beam: Matched beam 0.21 x 0.18 arcsec, PA 114 deg ([CII], 161 um, 90 um); 0.24 x 0.18 arcsec, PA 94 deg for CO(7-6) comparison  
  > "(beam area of 1.92 kpc$^2$, and effective radius of 0.78kpc)" (2.1 ALMA imaging); "(beam area of 2.3 kpc$^2$ and effective radius of 0.85kpc)" (2.1 ALMA imaging)
- final rms: Band 4 6.58, Band 7 25.9, Band 9 186 uJy/beam  
  > "(Band 4) | 6.58 | 0.21/0.14/85" (Table 1); "(Band 9) | 186 | 0.21/0.16/-53" (Table 1)

### Inherited from earlier work

- Band 7 (rest-frame 161 um) data previously presented, and Z-shaped spiral structure, disk kinematics  
  > "in addition to the earlier Band 7 ($\sim 869\ensuremath{\mu}m$) data presented in ((cite: tsukui2021-vl); PI=González López, Jorge)" (1 Introduction) [from (cite: tsukui2021-vl)]
- Disk geometry for deprojection (PA 7.6 deg, inclination 37.3 deg)  
  > "We calculate the de-projected radius using the thin disk geometry proposed in (cite: tsukui2021-vl)" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED) [from (cite: tsukui2021-vl)]
- CMB-corrected greybody formalism and temperature conversion  
  > "As described in (cite: Da_Cunha2013-yv), these two temperatures are related as" (3.2 Dust SED modelling) [from (cite: Da_Cunha2013-yv); (cite: Walter2022-uh)]
- Masked-moment method for [C II] template  
  > "we make a \[C II\] moment map by the masked moment method ((cite: Dame2011-nv)" (4.1 Image decomposition of Band 7 and Band 9 continuum images) [from (cite: Dame2011-nv)]
- Noise-correlated Monte Carlo with ESSENCE package  
  > "randomly generate noise maps with the same correlation properties characterized by the noise ACF using the ESSENCE package (cite: Tsukui2022-ne; 2023arXiv230103579T)" (4.1 Image decomposition of Band 7 and Band 9 continuum images) [from (cite: Tsukui2022-ne); (cite: 2023arXiv230103579T)]
- STARDUST SED fitting code (original, before the authors' modification)  
  > "the more realistic galaxy SED fitting code STARDUST (cite: Kokorev2021-yp)" (4.2.2 Stardust panchromatic SED modelling) [from (cite: Kokorev2021-yp)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters for tclean: cell size, image size, phase centre, niter, threshold, masks, deconvolver, spectral channel widths
- Exact line-free channel ranges / continuum frequency ranges for each band
- Self-calibration (if any) and absolute flux scale uncertainty adopted for each band
- Primary-beam correction details and exact aperture centring for the 2x2 arcsec integrated flux measurements
- Algorithm and bounds for the per-pixel greybody fit (optimizer, initial values, parameter ranges)
- emcee settings: number of walkers, steps, burn-in, prior ranges, likelihood treatment of upper limits
- STARDUST modification details; the modified code is not released until publication, and template versions are not given
- Flux extraction for Herschel/Spitzer/optical points beyond catalogue names; how the Band 4 continuum entered the global SED
- Treatment of the redshift discrepancy (z = 4.4704 vs 4.4074 in the cosmology sentence)
- Masked-moment threshold and kernel choices beyond the stated 2x beam and 2x channel width; noise map region used for the ACF

## Analysis recipe

1. **Calibrate and image continuum and line cubes**: CASA pipeline calibration, continuum from line-free channels with linear fit subtraction, then imaging with Briggs weighting; line maps by summing channels and per-pixel single Gaussian fits  
  > "We then imaged the line-free channels to produce continuum images and the continuum-subtracted data to produce emission line cubes." (2.1 ALMA imaging); "The mean velocity and the velocity dispersion of the emission line are extracted by fitting a single Gaussian to the spectrum at each pixel." (2.1 ALMA imaging)
   - software: CASA, hif_findcont
   - parameter: robust = 1.0 for CO(7-6), 0.5 for others  
  > "a robust parameter of 1.0 for the CO(7-6) line data cube to improve the sensitivity and 0.5 for others" (2.1 ALMA imaging)
   - parameter: line maps from summing channels over -400 to 400 km/s; pixels kept if detected above 4 sigma in at least 4 channels  
  > "We only use pixels where the signal is detected more than 4 $\sigma$ over at least 4 channels." (2.1 ALMA imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Match resolution of all images and cubes**: Convolve to the smallest common beam  
  > "we convolved images to have the same spatial resolution with the smallest common beam size, using COMMON\_BEAM in the SPECTRAL-CUBE package." (2.1 ALMA imaging)
   - software: spectral-cube
   - parameter: same phase centre and pixel size used for all data products  
  > "the same phase centre and pixel size are used to image the visibility data so that all data products have the same pixel coordinates" (2.1 ALMA imaging)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit the global (spatially integrated) SED with a single greybody**: Integrate flux in a 2 arcsec x 2 arcsec box, then fit a single optically thin greybody (T, M_dust, beta free) to the photometry; 160 um Herschel point excluded because of warm dust excess  
  > "We measured the integrated flux densities by summing over the" (3.3 Global SED of the galaxy); "we fit the SED with a single greybody in the optically thin limit" (3.3 Global SED of the galaxy); "Therefore, we repeat the fit with the 160 $\ensuremath{\mu}m$ band flux excluded" (3.3 Global SED of the galaxy)
   - parameter: Herschel SPIRE 350 and 500 um excluded because of blending  
  > "because BRI 1335-0417 is not sufficiently separated from a nearby bright source at" (3.3 Global SED of the galaxy)
   - assumption: gas-to-dust ratio uses Jones et al. CO(2-1) gas mass with alpha_CO = 0.8 and r21 = 0.85  
  > "a ratio of $\mathrm{r}_{21}=L_{\mathrm{CO}(2 \rightarrow 1)}^{\prime} / L_{\mathrm{CO}(1 \rightarrow 0)}^{\prime}=0.85$ for SMGs" (3.3 Global SED of the galaxy)
   - fitting: _not stated_
   - validation: Compared with previous beta and L_TIR values from the literature  
  > "are consistent with the previously derived values for this galaxy" (3.3 Global SED of the galaxy)
4. **Derive per-pixel dust temperature and surface density maps**: Fit a CMB-corrected greybody to rest-frame 161 and 90 um images in each pixel with beta fixed at the global value, solving for Sigma_dust and T_dust  
  > "With flux densities measured in two bands and the fiducial dust emissivity" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED); "we choose to use the best estimate of $\beta=2.14\pm0.17$ obtained with the global SED modelling as a fiducial value in this paper" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED)
   - parameter: Band 4 (385 um) not used for the resolved fit because of lowest sensitivity  
  > "However, the rest-frame 385 $\ensuremath{\mu}m$ data has the worst sensitivity in terms of the minimal detectable SFR" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED)
   - parameter: only pixels with 68% interval on T_dust below 10 K kept  
  > "We only show and use pixels where the 68% confidence interval for the dust temperature is smaller than 10K." (3.4 Intrinsic dust properties derived from the spatially resolved dust SED)
   - assumption: kappa_0 = 5.1 cm^2/g at 1199.1 GHz (Draine & Li 2007); CMB temperature correction at z = 4.4704  
  > "$\kappa_0=5.1$ cm$^2$ g$^{-1}$ is the dust opacity at a reference frequency $\nu_0=1199.1$ GHz (cite: Draine2007-ou)" (3.2 Dust SED modelling)
   - fitting: Monte Carlo resampling, 300 trials, flux drawn from Gaussians and beta drawn from N(2.14, 0.17); 1 sigma from central 68%  
  > "we repeat the fit 300 times using fluxes randomly drawn from a Gaussian distribution centred on the best fit measured value" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED); "We report the width of the central 68% of these 300 trials as our $1\sigma$ uncertainties on $T_\mathrm{dust}$ and $\Sigma_\mathrm{dust}$." (3.4 Intrinsic dust properties derived from the spatially resolved dust SED)
   - validation: Isoflux-line plots for three example regions show T and Sigma_dust constrained near the intersection  
  > "The intersection of the two black lines corresponds to the most likely solution of $\Sigma_\mathrm{dust}$ and $T_\mathrm{dust}$" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED)
5. **Radial temperature profile and gas-tracer profile comparison**: De-project radius with thin-disk geometry from [C II] kinematics; compare dust-derived, CO(7-6)-derived and [C II]-derived gas profiles normalised at about 2 kpc  
  > "We calculate the de-projected radius using the thin disk geometry proposed in (cite: tsukui2021-vl) (Position angle 7.6 deg, inclination 37.3 deg)" (3.4 Intrinsic dust properties derived from the spatially resolved dust SED); "Both the dust-derived and CO-derived gas mass profiles are steeper than that estimated from the \[C II\] line." (3.5 Comparison of the derived dust mass profile and other gas mass tracer profiles)
   - parameter: CO comparison done at common 0.24 x 0.18 arcsec resolution  
  > "For the comparison with CO(7-6) all data are convolved to the common" (2.1 ALMA imaging)
   - assumption: constant emissivity per unit mass for line tracers; constant dust-to-gas ratio for dust  
  > "we assume a constant emissivity per unit mass, while for the latter we assume a constant dust-to-gas ratio" (3.5 Comparison of the derived dust mass profile and other gas mass tracer profiles)
   - fitting: _not stated_
   - validation: _not stated_
6. **Test systematics of the resolved measurements**: Vary absolute flux scales by 10% in opposite directions and vary beta over 1 to 2.5 to see effect on temperature and dust mass profiles  
  > "Considering the worst possible case, when the true Band 7 flux and Band 9 flux are 10% higher and lower than the observed values, respectively" (3.7 Systematic error of the spatially resolved measurements); "We investigate the effect on the derived dust temperature and mass profiles if the $\beta$ value changes across the galaxy from 1 to 2.5." (3.7 Systematic error of the spatially resolved measurements)
   - fitting: _not stated_
   - validation: Systematic error from absolute flux estimated as +2.7 K / -2.0 K  
  > "the systematic error due to the absolute flux uncertainty is estimated to be +2.7K/$-2.0$K" (3.7 Systematic error of the spatially resolved measurements)
7. **Decompose Band 7 and Band 9 continuum images into point source plus host**: Fit three components (PSF-scaled point source, PSF-convolved circular Gaussian, and a [C II] moment-0 template for the disk) to each continuum image  
  > "where the model has only 6 parameters: the central coordinates of the PSF and Gaussian components" (4.1 Image decomposition of Band 7 and Band 9 continuum images); "to the observed Band 7 and Band 9 continuum images with simple" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
   - software: ESSENCE
   - parameter: [C II] cube convolved to continuum resolution; masked moment: kernel 2x beam and 2x channel width, mask threshold = rms of original cube  
  > "convolution with a kernel of 2 times the beam size and 2 times the spectral channel width, then masking with a threshold set to the rms of the original cube" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
   - assumption: [C II] moment map traces the distribution of star-formation-heated dust  
  > "using the observed \[C II\] moment0 map as a template tracing the dust distribution heated by the star formation in the galaxy" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
   - fitting: chi-square minimisation; uncertainties from 300 Monte Carlo realisations of noise generated with the measured noise ACF (ESSENCE)  
  > "(3) repeat the fitting procedure 300 times with different random realizations of the noise" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
   - validation: BIC prefers the three-component fit; total model flux matches measured flux; point source position matches optical quasar and temperature peak  
  > "evaluation of the Bayesian information criterion (BIC) indicates that this three-component fit is preferred over any alternatives omitting one of the components" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
8. **Fit the SED of AGN-heated and host dust using the decomposition**: Fit two greybodies (optically thin, then cold dust with free tau_161um) simultaneously to integrated SED and to point-source fluxes at 161 and 90 um; also run modified STARDUST panchromatic fits  
  > "The sum of the two greybody functions (AGN-heated dust and colder dust heated by star formation) is fitted to the spatially integrated fluxes" (4.2.1 Two greybody components SED modelling); "We fit the model again with the same procedure for the above optically thin case, but with a prior constraint that the cold dust temperature cannot exceed the warm dust temperature." (4.2.1 Two greybody components SED modelling); "we modified the code to accept the point source fluxes as independent constraints to be fitted with the AGN-heated dust component" (4.2.2 Stardust panchromatic SED modelling)
   - software: emcee, STARDUST
   - parameter: Optically thin model has 6 free parameters (T, M_dust, beta for each component)  
  > "This model has 6 free parameters" (4.2.1 Two greybody components SED modelling)
   - parameter: Adopted final values: two greybodies with free optical thickness for cold component  
  > "As final values for the remainder of this paper, we adopt the best-fit model parameters derived from the two greybodies fit with a free optical thickness" (4.2.3 Conclusion of the SED fitting results)
   - assumption: AGN-heated dust modelled as optically thin greybody with free beta, instead of torus models  
  > "This motivates us to consider a simpler model where we fit the AGN-dust component with a greybody spectrum in the optically thin limit but with a free dust emissivity index" (4.2.1 Two greybody components SED modelling)
   - fitting: emcee with uniform priors  
  > "We compute the distribution of their posteriors for a uniform prior distribution using the EMCEE package (cite: Foreman-Mackey2013-yn)." (4.2.1 Two greybody components SED modelling)
   - validation: Three methods give consistent AGN contribution and SFR; QSO template without extinction preferred over stellar template (chi-square larger by 536); fit without decomposition gives SFR much higher  
  > "all three methods of SED modelling that include the spatially-resolved constraints provide consistent estimates of the AGN contribution" (4.2.3 Conclusion of the SED fitting results); "but this results in a $\chi^2$ value that is larger by 536, with 16 degrees of freedom" (4.2.2 Stardust panchromatic SED modelling)
9. **Make AGN-subtracted dust maps and SFR surface density**: Subtract best-fit point-source model from the 161 and 90 um images and repeat the per-pixel greybody fit; convert Sigma_TIR to Sigma_SFR  
  > "in each pixel, we subtract our best-fitting model estimate of the contribution from the point-like AGN-heated dust" (4.3 AGN-subtracted dust properties); "assuming the (cite: Chabrier2003-el) initial mass function" (4.3 AGN-subtracted dust properties)
   - parameter: same fiducial beta = 2.14 +/- 0.17; Monte Carlo includes point-source parameter uncertainties  
  > "but also our uncertainties on the properties of the point source component" (4.3 AGN-subtracted dust properties)
   - assumption: Chabrier IMF in the TIR to SFR conversion  
  > "assuming the (cite: Chabrier2003-el) initial mass function" (4.3 AGN-subtracted dust properties)
   - fitting: Monte Carlo as in step 4  
  > "We again use Monte Carlo simulations to propagate the uncertainties" (4.3 AGN-subtracted dust properties)
   - validation: Integrated SFR from the resolved map (with [CII]-based SFR where dust is unavailable) compared with the SED result  
  > "consistent with the SED modelling result" (4.3 AGN-subtracted dust properties)
10. **Kennicutt-Schmidt relation and depletion times**: Convert dust mass surface density to gas surface density with the global gas-to-dust ratio and plot against AGN-subtracted Sigma_SFR per pixel  
  > "The gas mass is derived by converting the spatially resolved dust mass surface density in Fig." (5.1 Implications for the dynamics and history of BRI 1335-0417); "to a total mass surface density assuming the same gas-to-dust ratio of" (5.1 Implications for the dynamics and history of BRI 1335-0417)
   - assumption: gas-to-dust ratio of 54.2 +/- 9.3 applied uniformly  
  > "to a total mass surface density assuming the same gas-to-dust ratio of" (5.1 Implications for the dynamics and history of BRI 1335-0417)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1-5 (Band 7); 5.4.0-70 (Band 4, Band 9): Pipeline calibration and imaging of ALMA data  
  > "We performed standard calibration and data reduction using the Common Astronomy Software Application (CASA; (cite: CASA_Team2022-cl)) pipeline" (2.1 ALMA imaging)
- **hif_findcont (HIF_FINDCONT)** : Identify line-free channels  
  > "We identified line-free channels using the HIF\_FINDCONT task in CASA" (2.1 ALMA imaging)
- **spectral-cube** : COMMON_BEAM convolution to a common resolution  
  > "using COMMON\_BEAM in the SPECTRAL-CUBE package." (2.1 ALMA imaging)
- **ESSENCE** : Generate noise maps with realistic correlation for Monte Carlo errors  
  > "randomly generate noise maps with the same correlation properties characterized by the noise ACF using the ESSENCE package" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
- **emcee** : Posterior sampling for two-greybody SED fits  
  > "We compute the distribution of their posteriors for a uniform prior distribution using the EMCEE package" (4.2.1 Two greybody components SED modelling)
- **STARDUST** modified by authors (not yet released): Panchromatic UV-to-FIR SED fit with QSO, AGN dust and cold dust templates, modified to accept point-source fluxes  
  > "we modified the code to accept the point source fluxes as independent constraints to be fitted with the AGN-heated dust component" (4.2.2 Stardust panchromatic SED modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust temperature of the central pixel (single-greybody resolved fit, before AGN subtraction) | 57.1 | 0.3 | K | 4 | The dust temperature of the central pixel is well constrained to be $57.1 \pm 0.3$ K |
| Median dust temperature at large radius | 38 | spread 30 to 45 K | K | 5 | the temperature profile becomes flat with a median temperature of 38K and a large spread of values from 30 to 45 K |
| Global single-greybody dust temperature (160 um excluded) | 39.0 | +3.4/-2.9 | K | 3 | a dust temperature $T_{\mathrm{dust}} = 39.0_{-2.9}^{+3.4}$K and an emissivity index $\beta=2.14\pm0.17$ |
| Global emissivity index beta | 2.14 | 0.17 | dimensionless | 3 | an emissivity index $\beta=2.14\pm0.17$ |
| Global total FIR luminosity L_TIR | 2.7e13 | +0.4/-0.3 (1e13) | Lsun | 3 | the computed total FIR luminosity $L_{\mathrm{TIR}}=2.7_{-0.3}^{+0.4}\times 10^{13} L_\odot$ |
| Gas-to-dust mass ratio (global) | 54.2 | 9.3 | dimensionless | 3 | The gas-to-dust mass ratio is found to be 54.2$\pm 9.3$ if we adopt |
| Gas-to-dust ratio needed to match CO and dust at 2 kpc | 44 | 24 | dimensionless | 5 | would require a gas-to-dust ratio 44 $\pm$ 24 |
| Systematic temperature error from absolute flux scale | +2.7/-2.0 | not stated | K | 6 | the systematic error due to the absolute flux uncertainty is estimated to be +2.7K/$-2.0$K |
| Point source flux, Band 7 (161 um) and Band 9 (90 um) | 3.09 (Band 7); 10.87 (Band 9) | +0.09/-0.08 (Band 7); +0.85/-1.18 (Band 9) | mJy | 7 | 3.09$^{+0.09}_{-0.08}$ & 10.87$^{+0.85}_{-1.18}$ |
| Gaussian component size sigma, Band 7 and Band 9 | 787 (Band 7); 777 (Band 9) | +18/-17 (Band 7); +66/-75 (Band 9) | pc | 7 | 787$^{+18}_{-17}$ & 777$^{+66}_{-75}$ |
| Measured total flux, Band 7 and Band 9 | 20.54 (Band 7); 52.92 (Band 9) | 0.27 (Band 7); 2.13 (Band 9) | mJy | 7 | 20.54$\pm$0.27& 52.92$\pm$2.13 |
| Point source fraction of integrated flux (161 um, 90 um) | 15% (161 um); 21% (90 um) | not stated | percent | 7 | The contribution of the point sources to the integrated flux over the image is small, 15% and 21% in rest-frame |
| Point source fraction of flux in the central resolution element (161 um, 90 um) | 49.8 (161 um); 56.7 (90 um) | +1.5/-1.3 (161 um); as printed -6.1/+4.5 (90 um) | percent | 7 | contributing 49.8$_{-1.3}^{+1.5}$% and 56.7$^{-6.1}_{+4.5}$% |
| Warm (AGN-heated) dust temperature, adopted two-greybody fit with free tau | 87.1 | +34.1/-18.3 | K | 8 | with dust temperatures of 87.1$^{+34.1}_{-18.3}$ K (warm component) and 52.6$^{+10.3}_{-11.0}$ K (cold component) |
| Cold dust temperature, adopted two-greybody fit with free tau | 52.6 | +10.3/-11.0 | K | 8 | 52.6$^{+10.3}_{-11.0}$ K (cold component) |
| Cold dust temperature, optically thin two-greybody fit | 29.3 | +4.5/-3.6 | K | 8 | the temperature of the cold dust component is $T_{\mathrm{dust}}=29.3^{+4.5}_{-3.6}$ K |
| Dust emissivity indices of warm and cold components (adopted fit) | 0.91 (warm); 2.56 (cold) | +0.56/-0.49 (warm); +0.37/-0.30 (cold) | dimensionless | 8 | $\beta_{\mathrm{dust}}=0.91^{+0.56}_{-0.49}$ and $\beta_{\mathrm{dust}}=2.56^{+0.37}_{-0.30}$ for the warm and cold components, respectively |
| SFR of the host from cold dust component (adopted) | 1700 | +500/-400 | Msun/yr | 8 | The star formation rate (SFR) estimated from the cold dust component is $1700_{-400}^{+500} M_\odot$ yr$^{-1}$ |
| AGN fraction of L_IR (adopted) | 53 | +14/-15 | percent | 8 | a large AGN contribution ($53^{+14}_{-15}$%) |
| STARDUST SFR with decomposition constraints | 1.77 | 0.02 | 1e3 Msun/yr | 8 | $1.77\pm{0.02}$ |
| STARDUST AGN-subtracted SFR without decomposition constraints | 5260 | 31 | Msun/yr | 8 | STARDUST provides a best-fit model with a AGN subtracted SFR of 5260$\pm31M_{\odot}$ |
| Integrated SFR from the resolved map | 1476 | not stated | Msun/yr | 9 | The resulting integrated SFR is $\sim1476 M_{\odot}$ yr$^{-1}$ |
| Gas depletion time range in the Kennicutt-Schmidt diagram | 50-200 | not stated | Myr | 10 | with a constant gas depletion time of 50-200 Myr |

## Qualitative findings

- The steep central temperature gradient in the single-greybody map is entirely due to the unresolved warm dust; after point source subtraction the temperature profile is flat with only a slight central increase  
  > "The flat dust temperature indicates that the steep gradient in Fig." (4.3 AGN-subtracted dust properties)
- High-temperature peaks coincide with enhanced [C II] velocity dispersion along the disk minor axis; AGN wind vs anisotropic accretion not distinguished  
  > "With current data, we cannot conclude whether the feature is due to the AGN wind heating the dust" (6 Conclusion and summary)
- A QSO template without dust extinction fits the UV-to-optical SED better than a stellar template  
  > "Our STARDUST calculation also finds that a QSO template without dust extinction" (4.2.2 Stardust panchromatic SED modelling)

## Claim tuples

- H: Is the steep central dust temperature rise caused by AGN-heated dust? | E: Per-pixel greybody fit to 161 and 90 um images, then decomposition into point source plus host and refit after point source subtraction | R: Central T = 57.1 K before subtraction; profile flat afterwards | F: The temperature gradient is due to an unresolved warm dust component associated with the AGN | **supported**
- H: Does a two-component dust model including AGN-heated warm dust describe the global SED better, and how does it change the SFR? | E: Two-greybody fits (thin and with free tau) and STARDUST fits constrained by decomposed point source fluxes | R: SFR 1700 (+500/-400) Msun/yr, AGN contribution 53 percent | F: Previous SFR (5040 Msun/yr) overestimated by about a factor of three | **supported**
- H: Is a distinct unresolved component required in the dust continuum images? | E: Three-component image decomposition (point source, Gaussian, [C II] template) of Band 7 and Band 9 images | R: Point source gives 15 and 21 percent of total flux but about 50 to 57 percent in the central beam, at the quasar position | F: A point source coincident with the optical quasar and temperature peak is present in both bands | **supported**
- H: Does removing the point source change the central SFR surface density and the star formation regime? | E: AGN-subtracted maps; Kennicutt-Schmidt diagram using dust-derived gas surface density | R: Central Sigma_SFR reduced by over a factor of three; pixels lie on a roughly linear sequence with depletion time of 50-200 Myr | F: The galaxy is a typical starburst with longer depletion time than previously estimated, consistent with settled disk kinematics | **supported**
- H: What causes the high-temperature regions in the outer disk correlated with velocity dispersion? | E: Compare temperature and [C II] velocity dispersion maps; single Gaussian fit at high-temperature peaks | R: High-T peaks coincide with enhanced dispersion along minor axis; no additional line components required | F: AGN-driven outflow or anisotropic accretion are both possible | **partially**

## Reasoning

- Why this data: Multiple continuum bands give many resolution elements for spatially resolved dust properties  
  > "Multiple continuum images provide a number of resolution elements over the galaxy, making it possible to investigate the spatially resolved physical properties of dust" (1 Introduction)
- Why this method: [C II] moment-0 template needs only one parameter and captures arms and bar not representable by analytic models  
  > "(1) there is only one parameter (total flux), (2) the \[C II\] emission captures disk substructures like arms and a bar" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
- Alternative: Alternative of a stellar template for the UV-to-optical SED rejected in favour of the QSO template  
  > "This difference in $\chi^2$ is highly significant and strongly favours the quasar template." (4.2.2 Stardust panchromatic SED modelling)
- Alternative: Spatially varying beta (radial decrease from 2.5 to 1.0) considered but judged unlikely to remove the gradient  
  > "However, the scenario is unlikely because it contradicts the generally observed anti-correlation of the temperature and" (3.7 Systematic error of the spatially resolved measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolved fluxes are beam-averaged and luminosity-weighted, which flattens intrinsic distributions  
  > "It is expected that such spatial smoothing by the beam acts to flatten any intrinsic distribution." (3.7 Systematic error of the spatially resolved measurements)
- Limitation (authors): Short Band 7 observation not sensitive to faint extended structure out to 10 kpc  
  > "is not sensitive enough to probe the faint structure out to 10 kpc in BRI 1335-0417" (4.1 Image decomposition of Band 7 and Band 9 continuum images)
- Limitation (authors): Sensitivity and resolution too low to test small-scale clumps in temperature-enhanced regions  
  > "cannot be addressed with the current data due to sensitivity and resolution limits" (3.6 The correlation of the temperature map and velocity dispersion map)
- Limitation (authors): Optically thin integrated fit gives lower cold-dust temperature than resolved results; integrated tau of limited meaning  
  > "This is expected due to the optically thin assumption we adopted in the SED modelling" (4.2.1 Two greybody components SED modelling)
- Caveat (inferred, ours): Fiducial beta fixed from the global SED (with the 160 um point excluded) for all pixels, so spatial beta gradients are not constrained
- Caveat (inferred, ours): AGN warm component temperature is poorly constrained (87 +34/-18 K) and rests on only two point-source fluxes plus the integrated SED
- Caveat (inferred, ours): Decomposition assumes [C II] morphology equals cold dust morphology, even though a central [CII]/FIR deficit is admitted
- Caveat (inferred, ours): Dust-based gas surface density assumes a constant gas-to-dust ratio from a single global CO(2-1) based estimate with alpha_CO = 0.8
- Caveat (inferred, ours): Inconsistent redshift values printed (4.4704 vs 4.4074) and 57.1 vs 57.7 K central temperature between text and conclusions

## Reproducibility

- Data public (paper): ALMA data public in the ALMA archive; HST in MAST; Spitzer and Herschel photometry public  
  > "The ALMA data we use in this work are publicly available in <https://almascience.nrao.edu/aq/>." (Data Availability); "The HST data we use in this work can be obtained in" (Data Availability)
- Products in archive: _not stated_
- Code: Modified STARDUST code to be released on GitHub upon publication (not yet available at time of writing)  
  > "The modified STARDUST code will be available at the GitHub repository <https://github.com/takafumi291>, upon publication" (4.2.2 Stardust panchromatic SED modelling (footnote))
- Missing: tclean imaging parameters (cell, image size, niter, threshold, masks) and line-free channel ranges
- Missing: Per-pixel fit optimizer details and emcee configuration (walkers, steps, priors)
- Missing: Modified STARDUST source and template versions
- Missing: Exact integrated-flux aperture and primary beam treatment
- Missing: Band 4 and 9 observing time, array configuration and execution details
- Data volume (inferred): Moderate: three ALMA bands of one source, likely tens of GB of raw/calibrated visibilities; pipeline products only a few GB
- Score (inferred): 3/5, Public ALMA data, numeric results, a clear stepwise recipe and key parameters (robust, Monte Carlo counts, kernel choices) are given, but imaging and fitting settings and the modified STARDUST code are missing.
- Rediscovery candidate: yes, Data are public, the per-pixel greybody map and the image decomposition are specified well enough to redo, and the headline results (T maps, point source fluxes, SFR) are numeric.

## Links

- Method: (cite: tsukui2021-vl) (Earlier analysis of the Band 7 data, disk geometry and [C II] kinematics reused here)
- Method: (cite: Kokorev2021-yp) (STARDUST SED fitting code that the authors modified)
- Method: (cite: Walter2022-uh) (Greybody formalism with CMB correction used for resolved dust modelling)
- Companion: (cite: Jones2016-cj) (CO(2-1) gas mass and earlier depletion-time estimate for the same galaxy)
- Companion: (cite: Wagg2014-bh) (Previous SFR and beta from the unresolved SED)
- Related: ALMA 2017.1.00394.S
- Related: ALMA 2018.1.01103.S
- Related: HST GO-8572

## Checks

```json
{
 "quotes": 170,
 "quotes_ok": 170,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 23,
 "numeric_problems": 0,
 "fill": {
  "facts": 130,
  "stated": 99,
  "rate": 0.762
 },
 "evidence_ok": true
}
```
