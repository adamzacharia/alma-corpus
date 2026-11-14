# JWST and ALMA Discern the Assembly of Structural and Obscured Components in a High-redshift Starburst Galaxy

`2024ApJ...968...15L` | The Astrophysical Journal 2024 | first author: Liu, Zhaoxuan | arXiv: 2311.14809 | DOI: 10.3847/1538-4357/ad4096

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What triggers an extreme starburst at z~1.45 (PACS-819, 11x above the main sequence): major merger, minor merger or secular disk processes, using resolved JWST stellar mass/extinction maps and ALMA CO(5-4) and dust continuum  
  > "What triggers a starburst galaxy?" (Introduction); "we aim to advance our understanding of the trigger of the distant starbursts." (Introduction)
- Target **PACS-819**: coordinates _not stated_; z/distance z = 1.445  
  > "PACS-819 is a distant starburst galaxy at $z$ = 1.445, detected by *Herschel*/PACS" (2.1 PACS-819: a starburst galaxy at z=1.45); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01426.S
- bands: Band 6  
  > "and ALMA Band 6" (Introduction)
- frequencies and spectral setup: Four spectral windows per configuration: 217.99, 220.99, 233.60 and 235.60 GHz centres (2.000 GHz wide, 1.875 GHz for the 235.60 GHz window that contains CO 5-4); channels rebinned to 20 km/s (high-res cube) and 35 km/s (low-res cube)  
  > "6 | 217.99, 220.99 | 2.000, 2.000" (Table 1); "6 | 233.60, **235.60**$^{a}$ | 2.000, 1.875" (Table 1); "The central frequency in bold indicates the spectral window where the CO line falls." (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12 m array: 45/40 antennas (high-resolution/extended) and 42/43 antennas (low-resolution/compact)  
  > "observed with 1.46 hrs of total on-source integration time with 45/40 12 m antennas" (2.3 ALMA observations); "observed with 22.2 minutes with 42/43 12 m antennas" (2.3 ALMA observations)
- configurations: Compact and Extended configurations  
  > "Compact | 2016 Dec 16 &" (Table 1); "Extended | 2017 Aug 24 &" (Table 1)
- baselines: _not stated_
- angular resolution: Extended: 0.13 x 0.09 arcsec (continuum, Briggs 0.5), 0.12 x 0.09 arcsec (cube); Compact: 0.83 x 0.69 arcsec (continuum), 0.84 x 0.70 arcsec (cube)  
  > "35.4 + 16.9 + 35.4 | 0.13 $\times$ 0.09 | 0.01" (Table 1); "0.83 $\times$ 0.69 | 0.02" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms 0.02 (compact) and 0.01 (extended) mJy/beam; cube rms 0.54 (compact, 35 km/s channel) and 0.41 (extended, 20 km/s channel) mJy/beam  
  > "0.12 $\times$ 0.09 | 0.41" (Table 1); "The rms noise of the cube is calculated from the channel where the line is strongest" (Table 1)
- time on source: 1.46 hrs high-resolution; 22.2 minutes low-resolution  
  > "observed with 1.46 hrs of total on-source integration time with 45/40 12 m antennas" (2.3 ALMA observations); "PACS-819 was observed with 22.2 minutes" (2.3 ALMA observations)
- observing dates: Compact: 2016 Dec 16 & Apr 13; Extended: 2017 Aug 24 & Sep 02  
  > "Compact | 2016 Dec 16 &" (Table 1); "Extended | 2017 Aug 24 &" (Table 1)
- pi or archival as stated: Own ALMA Cycle 4 program, PI J. Silverman  
  > "With our ALMA Cycle 4 program (Proposal #2016.1.01426.S; PI J. Silverman)" (2.3 ALMA observations)
- Line: CO J=5-4 (576.27 GHz)
- Other facility **JWST NIRCam+MIRI (COSMOS-Web, GO #1727)**: NIRCam F115W/F150W/F277W/F444W and MIRI F770W images for stellar mass, extinction and morphology  
  > "Images with four NIRCam filters (F115W, F150W, F277W, and F444W) are available." (2.2 JWST (+HST) imaging from COSMOS-Web); "on April 10th, PACS-819 was observed with MIRI/F770W." (2.2 JWST (+HST) imaging from COSMOS-Web)
- Other facility **HST/ACS**: F606W and F814W rest-frame UV/optical images  
  > "PACS-819 was observed in F606W and F814W as a part of the HST Cycle 19" (2.2 JWST (+HST) imaging from COSMOS-Web)
- Other facility **HST G141 grism**: Grism spectra of two neighbouring galaxies to test for interaction  
  > "the area around PACS-819 has been observed with HST G141 GRISM (PI: Lemaux; #16684)." (Local environment of PACS-819)
- Other facility **Herschel/PACS**: Detection and total IR luminosity / SFR of PACS-819  
  > "detected by *Herschel*/PACS (cite: rodighiero_lesser_2011)" (2.1 PACS-819: a starburst galaxy at z=1.45)
- Other facility **Subaru FMOS-COSMOS**: Near-infrared spectroscopic survey that includes PACS-819  
  > "included in our FMOS-COSMOS near-infrared spectroscopic survey of star-forming galaxies with the Subaru Telescope" (2.1 PACS-819: a starburst galaxy at z=1.45)
- Other facility **Chandra and XMM-Newton**: X-ray survey non-detection used to argue against AGN  
  > "There is no detection in the previous X-ray survey with $Chandra$ and XMM-$Newton$ in the COSMOS field" (2.4 AGN)
- External data: Stellar mass of PACS-819, 10^10.7 +/- 0.1 Msun, from SED fitting  
  > "from a comprehensive SED fitting conducted by (cite: liu_co_2021)" (2.1 PACS-819: a starburst galaxy at z=1.45) [from (cite: liu_co_2021)]
- External data: Herschel/TIR-based SFR of 533 (+68/-60) Msun/yr  
  > "derived from $L_{\text{TIR}}$ (cite: silverman_molecular_2018)" (2.1 PACS-819: a starburst galaxy at z=1.45) [from (cite: silverman_molecular_2018)]
- External data: Gas-to-dust ratio of 35 from another starburst at z=1.5  
  > "Given the gas-to-dust ratio of 35 estimated from the study of another starburst of similar redshift (z=1.5) in our survey (cite: silverman_concurrent_2018)" (4.2 Gas fraction) [from (cite: silverman_concurrent_2018)]
- External data: Dust mass absorption coefficient at 500 micron, 0.051 m^2/kg  
  > "at 500 $\mu m$ is 0.051 $\, \text{m}^2/\text{kg}$, as estimated by the Herschel Reference Survey" (4.2 Gas fraction) [from (cite: clark_empirical_2016)]
- External data: Linear L_TIR vs L'CO(5-4) relation (+2.52 offset, 0.2 dex scatter)  
  > "We then convert the CO luminosity to TIR luminosity by the linear relation in (cite: daddi_co_2015)" (4.1 sSFR); "We note that there is a scatter of 0.2 dex in this relation that we need to take into account here." (4.1 sSFR) [from (cite: daddi_co_2015)]
- External data: Mass-weighted mean mass-to-light ratio and <U>=30 from SED fitting  
  > "estimated by the SED fitting from (cite: liu_co_2021)" (4.2 Gas fraction) [from (cite: liu_co_2021)]
- External data: <U> to T_dust relation, giving T_dust = 33 K  
  > "as in (cite: magdis_evolving_2012)" (4.2 Gas fraction) [from (cite: magdis_evolving_2012)]
- External data: Main-sequence relation used to define 11x above MS  
  > "These measurements place PACS-819 just over 10 times above the MS (cite: speagle_highly_2014)" (2.1 PACS-819: a starburst galaxy at z=1.45) [from (cite: speagle_highly_2014)]
- External data: Velocity anomalies and non-circular motions of PACS-819 from an independent kinematic analysis  
  > "analyze the velocity anomalies of PACS-819 in detail and conclude that these anomalies are non-circular features rotating faster or slower than the disk." (3.3 Model kinematic fitting) [from (cite: rizzo_alma-alpaka_2023)]
- External data: COSMOS-Web JWST images, recalibrated and reduced to 30 mas/pixel  
  > "The data used in this study is recalibrated by the COSMOS-Web team and reduced to a spatial scale of 30 mas/pixel (Franco in prep.)." (2.2 JWST (+HST) imaging from COSMOS-Web) [from (cite: casey_cosmos-web_2023)]
- External data: COSMOS2020 photometric redshifts of neighbouring galaxies  
  > "According to the COSMOS2020 catalog (cite: weaver_cosmos2020_2022), they are likely foreground galaxies" (Local environment of PACS-819) [from (cite: weaver_cosmos2020_2022)]
- External data: Keck/DEIMOS spectroscopic redshift of 1.445 for a neighbouring galaxy  
  > "the former galaxy is reported to have a spectroscopic redshift of 1.445 based on a slit spectrum acquired with Keck/DEIMOS (cite: masters_complete_2019)" (Local environment of PACS-819) [from (cite: masters_complete_2019)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2 for reduction and recalibration of the raw data; CASA 6.2.1 for measurements and analysis  
  > "We use the Common Astronomy Software Applications (CASA 4.7.2) to carry out the reduction and recalibration of the raw data." (2.3 ALMA observations); "Our measurements and analysis are processed by CASA 6.2.1" (2.3 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in multifrequency synthesis (mfs) mode for the continuum  
  > "algorithm in multifrequency synthesis" (2.3.2 Continuum)
- deconvolver: multiscale  
  > "deconvolver to detect the extended emission" (2.3.2 Continuum)
- weighting robust: Cube (high-res): Briggs 0.5; continuum high-res: natural and Briggs 0.5; continuum low-res: Briggs 0.5  
  > "weighting factor of 0.5 to achieve a higher resolution and optimize the sensitivity for substructures in the gas distribution" (2.3.1 CO (J=5–4)); "opted for natural weighting to maximize the signal-to-noise ratio and a 0.5 Briggs weighting for a higher resolution." (2.3.2 Continuum); "For the low-resolution observation, we only applied the 0.5 Briggs weighting for its high signal-to-noise ratio." (2.3.2 Continuum)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh mask for high-resolution continuum images  
  > "For high-resolution images, we utilized the" (2.3.2 Continuum); "mask and opted for natural weighting" (2.3.2 Continuum)
- multiscale scales: _not stated_
- continuum subtraction: Continuum image made from line-free channels only (no line subtraction recipe given)  
  > "covering all channels without emission lines." (2.3.2 Continuum)
- line free channels: Range of 4xFWHM centered at the line centroid flagged in the dirty cubes, based on the ALMA data release products  
  > "centered at the line centroid in the dirty cubes, based on the ALMA data release products" (2.3.2 Continuum)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cube rebinned in velocity to 20 km/s (high-res, 4x native) and 35 km/s (low-res, 7x native)  
  > "(4 times the native resolution) to enhance the signal-to-noise ratio" (2.3.1 CO (J=5–4)); "(7 times the native resolution) to detect internal structures" (2.3.1 CO (J=5–4))
- final beam: Compact 0.83 x 0.69 arcsec; Extended 0.13 x 0.09 arcsec (continuum); cube 0.84 x 0.70 and 0.12 x 0.09 arcsec  
  > "0.83 $\times$ 0.69 | 0.02" (Table 1); "0.12 $\times$ 0.09 | 0.41" (Table 1)
- final rms: Continuum 0.02 / 0.01 mJy/beam (compact/extended); cube 0.54 / 0.41 mJy/beam  
  > "35.4 + 16.9 + 35.4 | 0.13 $\times$ 0.09 | 0.01" (Table 1); "0.12 $\times$ 0.09 | 0.41" (Table 1)

### Inherited from earlier work

- Stellar mass 10^10.7 Msun taken from earlier SED fitting  
  > "from a comprehensive SED fitting conducted by (cite: liu_co_2021)" (2.1 PACS-819: a starburst galaxy at z=1.45) [from (cite: liu_co_2021)]
- SFR from L_TIR (Herschel) taken from earlier work  
  > "derived from $L_{\text{TIR}}$ (cite: silverman_molecular_2018)" (2.1 PACS-819: a starburst galaxy at z=1.45) [from (cite: silverman_molecular_2018)]
- Substructure (aperture) SED fitting method for clump masses  
  > "We adopt the method described in (cite: kalita_rest-frame_2023) to determine the mass of the substructures with aperture SED fitting." (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure) [from (cite: kalita_rest-frame_2023)]
- 10% systematic uncertainty in SED fitting  
  > "We introduced 10% systematic uncertainty, as suggested by (cite: abdurrouf_understanding_2017)." (2.2.1 SED fitting) [from (cite: abdurrouf_understanding_2017)]
- Dust attenuation law in SED fitting  
  > "Dust modeling follows the method of (cite: calzetti_dust_2000)" (2.2.1 SED fitting) [from (cite: calzetti_dust_2000)]
- Mean mass-to-light ratio and <U>=30 used for dust temperature  
  > "estimated by the SED fitting from (cite: liu_co_2021)" (4.2 Gas fraction) [from (cite: liu_co_2021)]
- HST F814W reduction approach  
  > "following the approaches first described in (cite: koekemoer_candels_2011)" (2.2 JWST (+HST) imaging from COSMOS-Web) [from (cite: koekemoer_candels_2011)]
- Observing program description and gas-to-dust ratio  
  > "we acquired high- and low-resolution ALMA observations of three starbursts well above the MS: PACS-819, PACS-830, and PACS-787 (cite: silverman_concurrent_2018)" (2.3 ALMA observations) [from (cite: silverman_concurrent_2018)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration: whether the pipeline or manual scripts were used, calibrators, flux scale accuracy and any self-calibration are not given
- Number of iterations, threshold, cell size, image size and multiscale scales for tclean are not given
- Which channels were treated as line-free and the exact continuum frequency range actually used
- Imfit starting guesses and regions; how the CO moment-0 and total flux were integrated (aperture, mask)
- 3DBarolo full parameter file (ring radii and widths, FREE parameters, SEARCH threshold, NORMALIZE, number of rings)
- Exact pixedfit and bagpipes configuration (SFH priors on tau and age, prior ranges for mass, fit sampler) and the PSFs used
- Luminosity distance and the exact conversion from CO flux density to L'CO in each pixel
- The 1.3 mm dust-mass equation flux scaling, rest frequency used for B_nu and how the 500 micron kappa was extrapolated to the observed band
- Details of annuli and masking used for the resolved KS relation
- Coordinates of PACS-819
- The COSMOS-Web JWST reduction (Franco in prep.) is unpublished

## Analysis recipe

1. **recalibrate ALMA data and image CO cubes and continuum**: Reduction and recalibration of raw data in CASA 4.7.2; images and cubes made with tclean (Briggs 0.5 for the cube; natural and Briggs 0.5 for the continuum, multiscale deconvolver, mfs over line-free channels); cubes rebinned to 20 and 35 km/s  
  > "to carry out the reduction and recalibration of the raw data." (2.3 ALMA observations); "covering all channels without emission lines." (2.3.2 Continuum)
   - software: CASA, tclean
   - parameter: Briggs weighting factor 0.5 for the high-resolution cube  
  > "weighting factor of 0.5 to achieve a higher resolution and optimize the sensitivity for substructures in the gas distribution" (2.3.1 CO (J=5–4))
   - parameter: Line-containing range of 4xFWHM about the line centroid flagged for continuum  
  > "centered at the line centroid in the dirty cubes, based on the ALMA data release products" (2.3.2 Continuum)
   - fitting: _not stated_
   - validation: No significant missing flux when comparing with the low-resolution total flux  
  > "we confirm there is no significant missing flux" (4.1 sSFR)
2. **measure CO and continuum fluxes and sizes**: imfit with an elliptical Gaussian model for CO; multiple 2D Gaussians (Gaussian plus point source for the compact core) on the natural-weighted continuum image  
  > "to generate a model based on an elliptical Gaussian function." (2.3.1 CO (J=5–4)); "A Gaussian model combined with a point source yielded a satisfactory result to describe its compact core." (2.3.2 Continuum)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Added a point-source component to test for an unresolved core  
  > "A point-source component is added to model a potential unresolved central component" (2.3.1 CO (J=5–4))
3. **extract CO spectrum and make red/blue moment-0 maps**: CASA specflux spectrum with a Gaussian fit using astropy models; two moment 0 maps from red and blue intervals with spectral-cube  
  > "to extract spectra centered on the CO (J=5–4) emission line" (3.2 Galaxy kinematics with ALMA using CO J=5–4); "python package to produce two moment 0 maps by collapsing data over both redward and blueward narrow intervals" (3.2 Galaxy kinematics with ALMA using CO J=5–4)
   - software: CASA specflux, astropy, spectral-cube
   - parameter: Initial Gaussian estimates (mean, amplitude, standard deviation) taken from the CASA viewer; all parameters free  
  > "package to fit the Gaussian models, allowing all parameters to vary." (3.2 Galaxy kinematics with ALMA using CO J=5–4)
   - fitting: Gaussian models for the double-peak profile, all parameters free  
  > "package to fit the Gaussian models, allowing all parameters to vary." (3.2 Galaxy kinematics with ALMA using CO J=5–4)
   - validation: _not stated_
4. **fit the 3D kinematic disk model**: 3DBarolo tilted-ring fit in 3D, SEARCH masking and LOCAL normalization; PA and INC grid-searched (5 and 15 degree steps), PA fixed to 128 and INC to 45 degrees; Vrot free, sigma_gas constrained above 20 km/s  
  > "Specifically, we used the SEARCH method to mask the data cube and set the normalization as LOCAL to generate an asymmetry model for our clumpy case." (3.3 Model kinematic fitting); "We fixed PA as 128 degrees, as it was easier to judge from the velocity field, and searched for the best INC, ultimately fixing it as 45 degrees." (3.3 Model kinematic fitting)
   - software: 3DBarolo
   - parameter: System velocity fixed to 0; redshift and rest-frame frequency input; RA and Dec fixed due to S/N  
  > "We fixed the system velocity to 0 and input the redshift and rest-frame frequency of our emission line." (3.3 Model kinematic fitting); "Due to our S/N limitations, we fixed the RA and Dec of the model" (3.3 Model kinematic fitting)
   - parameter: INC step 5 degrees, PA step 15 degrees  
  > "with each INC varying by 5 degrees and each PA varying by 15 degrees" (3.3 Model kinematic fitting)
   - fitting: Tilted-ring model fit; grid search over INC and PA  
  > "This software fits the gas with a tilted ring model in 3D" (3.3 Model kinematic fitting)
   - validation: Data, model and residual maps, and position-velocity maps compared; dispersion modelled with less precision  
  > "while dispersion was modeled with less precision due to the challenging nature of modeling it accurately." (3.3 Model kinematic fitting)
5. **build resolved stellar mass, A_V and SFR maps from JWST+HST pixels**: Images PSF-matched to F444W at 40 mas/pixel with piXedfit_images, pixels binned to S/N >= 10 in F150W, F277W and F444W (min bin size 1 pixel), then pixel-by-pixel SED fitting with bagpipes (delayed-exponential SFH first, then constant SFH)  
  > "downgrading all images to match the PSF (point spread function) of F444W and the pixel scale of F606W at 40 mas/pixel." (2.2.1 SED fitting); "we requested all bins to have an S/N $\ge$ 10 in F150W, F277W and F444W" (2.2.1 SED fitting)
   - software: pixedfit, bagpipes, PSFEx
   - parameter: Metallicity fixed to solar Z=0.02  
  > "we fix the metallicity to solar (Z=0.02) to simplify our model when only six bands are available." (2.2.1 SED fitting)
   - parameter: A_V between 0 and 4 mag; ionization parameter U fixed to 1e-3  
  > "with $A_V$ varying between 0 and 4 magnitudes" (2.2.1 SED fitting); "we fixed the ionization parameter U for the nebular emission to be $10^{-3}$ as the default." (2.2.1 SED fitting)
   - parameter: Constant SFH: turn-on time 100 Myr to age of Universe, turn-off 1 Myr  
  > "we further simplified the model to a constant SFH, with a variable turning-on time from 100 Myr to the age of the Universe and a turning-off time at 1 Myr" (2.2.1 SED fitting)
   - assumption: Chabrier IMF  
  > "We use a (cite: chabrier_galactic_2003) IMF for estimating the stellar masses and SFRs." (Introduction)
   - assumption: Dust continuum not included because a single FIR band cannot constrain a FIR model  
  > "We did not include the dust continuum because it is hard to derive an accurate FIR model with only one band." (2.2.1 SED fitting)
   - fitting: bagpipes SED fitting with 10% systematic uncertainty; sampler and priors beyond those listed not stated  
  > "We introduced 10% systematic uncertainty, as suggested by (cite: abdurrouf_understanding_2017)." (2.2.1 SED fitting)
   - validation: UVJ color map of best-fit SEDs used to confirm the whole galaxy is star-forming; sum of the mass map compared with previous total  
  > "The sum of the stellar mass map is in agreement with that reported previously" (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure)
6. **remove smooth component of F444W with Sersic fit**: Single Sersic profile fit to F444W with Galight to isolate residual spiral-like features  
  > "we fit the galaxy with a single Sérsic profile using Galight (cite: 2020ApJ...888...37D)" (3.1 Unveiling the stellar components with JWST)
   - software: Galight
   - fitting: _not stated_
   - validation: _not stated_
7. **measure stellar mass of the blue arc and green clump**: Segmentation from F115W (3 sigma threshold, deblending with 5 connected pixels) after subtracting a 3-pixel FWHM Gaussian-smoothed image; Photutils annular background subtraction; aperture SED fit with a constant SFH  
  > "We then set a 3$\sigma$ detection threshold and perform source deblending with the minimum number of connected pixels set to 5." (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure); "Our background estimate is based on annular regions with the two clumps being masked." (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure)
   - software: Photutils, bagpipes
   - parameter: Flux error set to 10% of the flux  
  > "Therefore, we set the error to be 10$\%$ of the flux before background subtraction." (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure)
   - assumption: Green component background estimated from a 1-pixel wide annulus gives an upper limit on its flux  
  > "thus estimating an upper-limit for the flux of the" (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure)
   - fitting: SED fit repeated with constant SFH using photometry within each segmentation region  
  > "and employ a constant SFH model." (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure)
   - validation: _not stated_
8. **derive SFR and sSFR maps from CO(5-4)**: Per-pixel L'CO from the CO(5-4) map, converted to L_TIR with the Daddi et al. linear relation, then to SFR with the Kennicutt/Hao/Murphy TIR calibration; SFR map convolved to the F444W PSF, reprojected to the stellar-mass grid and divided by the stellar mass map  
  > "We then convert the CO luminosity to TIR luminosity by the linear relation in (cite: daddi_co_2015)" (4.1 sSFR); "the SFR image is convolved by a Gaussian kernel to match the FWHM based on an empirical PSF model for the JWST/F444W filter using stars within the JWST image." (4.1 sSFR)
   - parameter: Regions below 3 sigma_rms masked  
  > "In subsequent analyses, we mask regions with emission at low S/N" (4.1 sSFR)
   - assumption: LambdaCDM with H0=70, OmegaL=0.7, OmegaM=0.3  
  > "we follow the standard $\Lambda\mathrm{CDM}$ model by assuming $H_{0}=70 \mathrm{~km} \mathrm{~s}^{-1} \mathrm{Mpc}^{-1}, \Omega_{\Lambda}=0.7, \Omega_{\mathrm{M}}=0.3$" (Introduction)
   - assumption: L_TIR-L'CO relation has 0.2 dex scatter  
  > "We note that there is a scatter of 0.2 dex in this relation that we need to take into account here." (4.1 sSFR)
   - fitting: _not stated_
   - validation: Total SFR compared with the Herschel-based value and low-resolution flux for missing flux  
  > "Our derived SFR confirms that PACS-819 is a starburst" (4.1 sSFR)
9. **derive dust mass, gas mass and gas fraction maps from continuum**: Blackbody dust mass from the 1.3 mm continuum flux with T_dust = 33 K and kappa(500 um) = 0.051 m^2/kg, times a gas-to-dust ratio of 35; gas map regridded and smoothed to the F444W image and divided by the stellar mass map  
  > "We adopt the black body emission model to infer the dust mass" (4.2 Gas fraction); "we regrid and smooth the gas map to match the F444W image and then simply divide the gas and stellar maps" (4.2 Gas fraction)
   - assumption: T_dust = 33 K  
  > "dust temperature $\mathrm{T_{dust}}$ of 33 K" (4.2 Gas fraction)
   - assumption: kappa at 500 micron = 0.051 m^2/kg  
  > "at 500 $\mu m$ is 0.051 $\, \text{m}^2/\text{kg}$, as estimated by the Herschel Reference Survey" (4.2 Gas fraction)
   - assumption: Gas-to-dust ratio 35  
  > "Given the gas-to-dust ratio of 35 estimated from the study of another starburst of similar redshift (z=1.5) in our survey (cite: silverman_concurrent_2018)" (4.2 Gas fraction)
   - fitting: _not stated_
   - validation: Compared with the CO(2-1) gas mass of 4.6e10 Msun  
  > "This is comparable to the gas mass of $4.6 \times 10^{10}M_{\odot}$ assessed using CO (J=2–1)" (4.2 Gas fraction)
10. **derive depletion time map and resolved KS relation**: Depletion time map from gas mass over SFR maps (CO and continuum made with the same 0.5 weighting); circular annuli with radii 1-4 times half the beam major axis FWHM for the KS relation  
  > "In order to reduce the influence of beam size, we use the same weighting factor (0.5) when generating the continuum and CO (J=5–4) maps." (4.3 Resolved KS relation)
   - assumption: Spatially varying gas-to-dust conversion factor is not modelled  
  > "affected by a spatially varying gas-to-dust conversion factor which is beyond the scope of this work." (4.3 Resolved KS relation)
   - fitting: _not stated_
   - validation: Annulus-based depletion times agree with the map  
  > "In agreement with the above-mentioned depletion times, all our aperture measurements indicate a depletion time around 120 Myr." (4.3 Resolved KS relation)

## Software

- **CASA** 4.7.2 (reduction and recalibration); 6.2.1 (measurements and analysis): ALMA reduction, tclean imaging, imfit fluxes and specflux spectra  
  > "We use the Common Astronomy Software Applications (CASA 4.7.2) to carry out the reduction and recalibration of the raw data." (2.3 ALMA observations); "Our measurements and analysis are processed by CASA 6.2.1" (2.3 ALMA observations)
- **3DBarolo** : Tilted-ring 3D kinematic modelling of CO(5-4)  
  > "This software fits the gas with a tilted ring model in 3D" (3.3 Model kinematic fitting)
- **spectral-cube** : Moment-0 maps over red and blue velocity intervals  
  > "python package to produce two moment 0 maps by collapsing data over both redward and blueward narrow intervals" (3.2 Galaxy kinematics with ALMA using CO J=5–4)
- **astropy** : Gaussian fits to the CO spectrum  
  > "package to fit the Gaussian models, allowing all parameters to vary." (3.2 Galaxy kinematics with ALMA using CO J=5–4)
- **pixedfit** : Pixel-by-pixel SED fitting workflow, image processing and binning  
  > "we employ spatially resolved spectral energy distribution (SED) fitting on a pixel-by-pixel basis using two different software packages" (2.2.1 SED fitting)
- **bagpipes** : SED fitting of rebinned photometric cubes  
  > "for SED fitting, implementing a simple model due to the limited number of bands." (2.2.1 SED fitting)
- **PSFEx** : JWST PSFs  
  > "The JWST PSFs were generated using PSFEx (cite: 2011ASPC..442..435B)." (2.2.1 SED fitting)
- **Galight** : Single Sersic fit of F444W  
  > "we fit the galaxy with a single Sérsic profile using Galight (cite: 2020ApJ...888...37D)" (3.1 Unveiling the stellar components with JWST)
- **Photutils** : Background estimation for the blue and green components  
  > "Our background estimate is based on annular regions with the two clumps being masked." (3.1.1 Spatially-resolved SED fitting and stellar masses of each structure)
- **GRIZLI** 1.8.2: HST F606W reduction and HST grism data processing  
  > "We utilized the F606W image at 40 mas/pixel, as reduced using the GRIZLI software" (2.2 JWST (+HST) imaging from COSMOS-Web); "Brammer, G. 2023, grizli, 1.8.2, Zenodo" (References)
- **EAZY** : Redshift fits to grism spectra and COSMOS2020 photometric redshifts  
  > "Unfortunately, we encountered some issues in determining their spectroscopic redshifts when fitting the extracted spectra with" (Local environment of PACS-819)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum total flux | 0.639 | 0.048 | mJy | 2 | 0.639 $\pm$ 0.048 / $\mathrm{mJy}$ / total flux of the underlying continuum |
| CO(5-4) intensity | 2.92 | 0.31 | Jy km/s | 2 | 2.92 $\pm$ 0.31 / $\mathrm{Jy}\,\mathrm{km}\,\mathrm{s}^{-1}$ / CO (5-4) intensity |
| Circularized effective radius of CO(5-4) | 1.21 | 0.11 | kpc | 2 | 1.21 $\pm$ 0.11 / kpc / Effective radius of CO (5-4); circularized |
| Circularized effective radius of continuum | 1.08 | 0.11 | kpc | 2 | 1.08 $\pm$ 0.11 / kpc / Effective radius of continuum; circularized |
| CO empirical line FWHM | 417.7 | not stated | km/s | 3 | The empirical FWHM of the entire line region was found to be 417.7 |
| Double-peak FWHMs (low- and high-frequency wings) | 190.0 and 189.2 | not stated | km/s | 3 | are 190.0 $\text{km}\,\text{s}^{-1}$ and 189.2 $\text{km}\,\text{s}^{-1}$ for the low- and high-frequency wings, respectively. |
| Disk position angle and inclination (CO, 3DBarolo) | PA = 128 deg (fixed), i = 45 deg | i: 10 deg | degrees | 4 | We fixed PA as 128 degrees, as it was easier to judge from the velocity field, and searched for the best INC, ultimately fixing it as 45 degrees.; $45 \pm 10$ / degrees / Disk inclination (CO) |
| Rotation-to-dispersion ratio Vrot/sigma_gas (Conclusions) | ~5 | not stated | dimensionless | 4 | Based on analysis with 3DBarolo, the 3D distribution of the CO J = 5 – 4 emission exhibits large disk-like rotation with $V_{rot}/\sigma_{gas}\sim5$. |
| Sersic index and half-light radius of F444W | n = 1.5, r_e = 1.52 kpc | not stated | dimensionless; kpc | 6 | The main galaxy has a Sérsic index of 1.5 and a half-light radius of 1.52 kpc. |
| Stellar mass of blue arc | log M* = 8.81 | +0.12/-0.13 | log Msun | 7 | First, the blue arc (to the southwest) is less massive ($log~M_*=8.81_{-0.13}^{+0.12}$ |
| Stellar mass of green clump | 10^9.18 | +0.23/-0.24 dex | Msun | 7 | $10^{9.18_{-0.24}^{+0.23}}~M_{\odot}$ |
| Total SFR from CO(5-4) | 626 | 142 | Msun/yr | 8 | we derive a total SFR of 626 $\pm$ 142 |
| Resolved sSFR | 2-6e-8 | not stated | 1/yr | 8 | the sSFR map has values around 2–6$\times10^{-8} \,\mathrm{yr}^{-1}$ |
| CO(5-4) luminosity | 1.3e10 | 0.1e10 | K km/s pc^2 | 8 | $1.3\pm0.1\times10^{10}$ / $\mathrm{K}\, \mathrm{km}\, \mathrm{s}{ }^{-1} \,\mathrm{pc}^{2}$ / CO (5-4) luminosity |
| Integrated gas mass from continuum | 4.6e10 | 0.3e10 | Msun | 9 | the integrated gas mass is approximated at 4.6 $\pm$ 0.3 $\times 10^{10}M_{\odot}$ |
| Peak gas fraction in the core | ~3 | not stated | dimensionless | 9 | the core region exhibits a high gas fraction peaking at $\sim$3 |
| Resolved depletion time in central region | ~120 | not stated | Myr | 10 | A central elongated region, running almost East to West, of the disk looks uniform at about 120 Myr with two clumps having longer depletion times over 150 Myr. |
| Integrated depletion time (Table 2) | 73 | 10 | Myr | 10 | 73 $\pm$ 10 / Myr |

## Qualitative findings

- Red and near-IR JWST images show a smooth central mass concentration and spiral-like features rather than merger-like tidal tails, unlike HST/ACS rest-UV  
  > "the redder NIRCam and MIRI images reveal a smooth central mass concentration and spiral-like features, atypical for such an intense starburst." (abstract)
- CO and dust continuum are co-spatial with a heavily obscured core, partially surrounded by less obscured structures: a blue arc and a CO-detected clump  
  > "a massive clump (detected in CO), likely a recently accreted low-mass satellite." (abstract)
- No AGN contribution is found  
  > "we conclude that the AGN activity is not likely to be present." (2.4 AGN)

## Claim tuples

- H: Is the extreme starburst PACS-819 driven by an ongoing major merger? | E: Resolved JWST/HST SED fitting for stellar mass, aperture masses of the blue arc and green clump, Sersic residuals and CO kinematics | R: The obscured red component holds at least ~90% of the stellar mass, the other components are about 1% and at most ~5% | F: A major merger is disfavoured; the galaxy resembles a typical star-forming disk | **supported**
- H: Does the CO(5-4) kinematics show a rotating disk? | E: 3DBarolo tilted-ring fit to the 20 km/s CO cube, spectra and moment maps | R: S-shaped PV diagram, Vrot/sigma_gas of about 5, with kinematic anomalies at the green clump and cube edges | F: Rotation-dominated disk with kinematic anomalies likely from interactions or accretion | **supported**
- H: Do the starburst properties (gas fraction, depletion time) persist at resolved scales? | E: CO-based SFR map, continuum-based gas map divided by JWST stellar mass, depletion time map and annuli | R: Core gas fraction peaks at about 3 and depletion time is about 120 Myr across the system | F: High gas fractions and short depletion times extend over the system, similar to local starbursts | **supported**
- H: Is the green clump an accreted satellite or a product of violent disk instability? | E: Compare clump velocity offset and dispersion excess in 3DBarolo maps and its JWST/CO properties | R: Clump is kinematically offset with a dispersion excess and has low mass | F: Past accretion of a low-mass satellite favoured over VDI, not firmly established | **partially**

## Reasoning

- Why this data: Strong CO(2-1) detection motivated a higher-resolution ALMA follow-up; JWST resolves stellar populations hidden behind dust  
  > "the high S/N CO (J=2–1) detection prompted our request for a higher-resolution observation with ALMA." (2.1 PACS-819: a starburst galaxy at z=1.45); "With the advent of JWST, it is possible to shed light on the stellar populations hidden behind the dust veil in the distant Universe." (Introduction)
- Why this method: Pixel-by-pixel SED fitting to exploit the high-resolution images; 3DBarolo to interpret kinematics of few resolved elements  
  > "To address the source complexity and make full use of the high-resolution images, we employ spatially resolved spectral energy distribution (SED) fitting on a pixel-by-pixel basis" (2.2.1 SED fitting)
- Alternative: Major merger, minor merger and violent disk instability considered; major merger and VDI disfavoured  
  > "By disfavouring a direct major merger event, the next likely process is ongoing minor merging." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas-to-dust ratio from another galaxy; depletion-time variations likely within uncertainties  
  > "we caution that these variations in depletion time are likely to be within the uncertainties" (4.3 Resolved KS relation)
- Limitation (authors): S/N limited the 3DBarolo fit (centre fixed), and dispersion is modelled less precisely  
  > "Due to our S/N limitations, we fixed the RA and Dec of the model" (3.3 Model kinematic fitting); "while dispersion was modeled with less precision due to the challenging nature of modeling it accurately." (3.3 Model kinematic fitting)
- Limitation (authors): Dust continuum could not be included in SED fitting because only one FIR band  
  > "We did not include the dust continuum because it is hard to derive an accurate FIR model with only one band." (2.2.1 SED fitting)
- Caveat (inferred, ours): Table 2 gives tau_depl = 73 +/- 10 Myr while the text and abstract give ~120 Myr; the two are not reconciled
- Caveat (inferred, ours): Vrot/sigma_gas is ~5 in the Conclusions but ~4 in the Discussion; no uncertainties are given
- Caveat (inferred, ours): SFR is derived from CO(5-4) via a L_TIR-L'CO relation with 0.2 dex scatter, so the SFR maps are indirect; the Table 2 SFR (626) differs from Herschel (533)
- Caveat (inferred, ours): Gas mass relies on a single-band Rayleigh-Jeans-like dust estimate with an assumed T_dust (33 K), a 500 micron kappa and a gas-to-dust ratio from another galaxy
- Caveat (inferred, ours): Stellar mass maps depend on a simple six-band SED model with fixed solar metallicity
- Caveat (inferred, ours): No ALMA calibration, self-calibration or tclean details are given, limiting exact reproduction

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA data release products referenced for line-flagging; archive project 2016.1.01426.S named  
  > "centered at the line centroid in the dirty cubes, based on the ALMA data release products" (2.3.2 Continuum); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01426.S." (Acknowledgements)
- Missing: Full tclean parameters (cell, image size, scales, thresholds, masks), line-free channel list and self-calibration
- Missing: 3DBarolo input parameter file and ring setup
- Missing: bagpipes/pixedfit priors and sampler settings, PSFs and binning maps
- Missing: COSMOS-Web reduced JWST images (reduction by Franco et al. in preparation)
- Missing: Luminosity distance and the exact pixel-wise L'CO and dust-mass implementations
- Data volume (inferred): Two Band 6 configurations (about 1.5 h and 22 min on source) plus public JWST/HST images; roughly tens of GB of ALMA raw data and a few GB of images
- Score (inferred): 3/5, ALMA project code and many numerical results given with clear steps, but ALMA calibration/tclean settings, 3DBarolo configuration and SED priors are missing, the JWST reduction is unpublished, and Table 2 and the text disagree on depletion time
- Rediscovery candidate: no, The paper does not state data are public and the recipe omits key calibration, imaging and fitting settings; several results depend on unpublished or external inputs

## Links

- Method: Teodoro & Fraternali 2015 (cite: teodoro_3dbarolo_2015) (3DBarolo kinematic fitting)
- Method: Abdurro'uf et al. 2021 (cite: abdurrouf_introducing_2021) (pixedfit pixel-by-pixel SED fitting)
- Method: Carnall et al. 2018 (cite: carnall_inferring_2018) (bagpipes SED fitting)
- Method: Kalita et al. 2023 (cite: kalita_rest-frame_2023) (aperture SED fitting of substructures)
- Method: Daddi et al. 2015 (cite: daddi_co_2015) (L_TIR-L'CO(5-4) relation)
- Companion: Silverman et al. 2018b (cite: silverman_concurrent_2018) (Same ALMA program and gas-to-dust ratio)
- Companion: Silverman et al. 2018a (cite: silverman_molecular_2018) (CO(2-1) detection, Herschel SFR and gas mass of PACS-819)
- Companion: Rizzo et al. 2023 (cite: rizzo_alma-alpaka_2023) (Independent kinematic analysis of PACS-819)
- Companion: Liu et al. 2021 (cite: liu_co_2021) (Stellar mass and SED fit)
- Companion: Casey et al. 2023 (cite: casey_cosmos-web_2023) (COSMOS-Web JWST survey)
- Related: COSMOS-Web (JWST GO #1727)
- Related: FMOS-COSMOS
- Related: COSMOS
- Related: ALMA-ALPAKA

## Checks

```json
{
 "quotes": 170,
 "quotes_ok": 170,
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
  "facts": 136,
  "stated": 108,
  "rate": 0.794
 },
 "evidence_ok": true
}
```
