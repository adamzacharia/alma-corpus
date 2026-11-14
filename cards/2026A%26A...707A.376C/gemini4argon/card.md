# MIRACLE: II. Unveiling the multiphase gas interplay in the circumnuclear region of NGC 1365 via multicloud modeling

`2026A&A...707A.376C` | Astronomy and Astrophysics 2026 | first author: Ceci, M. | arXiv: 2507.08077 | DOI: 10.1051/0004-6361/202556352

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Characterize the multiphase gas (ionized atomic, warm and cold molecular) kinematics, morphology, physical conditions, and energetics in the circumnuclear region of NGC 1365 to understand AGN feedback and its impact on galaxy evolution.  
  > "Specifically, we combined spatially resolved spectroscopic data from JWST/MIRI, VLT/MUSE, and ALMA to provide a multiphase characterization of the ionized atomic and the warm and cold molecular gas phases." (abstract); "In particular, it allows for a detailed characterization of the kinematics, morphology, and energetics of the circumnuclear environment in NGC 1365, ultimately contributing to a deeper understanding of AGN feedback and its impact on galaxy evolution." (Introduction)
- Target **NGC 1365**: coordinates RA = 03h33m36.37s, Dec = -36d08m25.37s  
  > "This dusty barred spiral galaxy (SB(s)b; (cite: deVaucouleurs1991)) is located in the Fornax cluster (cite: Jones1980) at a distance of 19.57 Mpc (cite: Jacobs09; Anand2021) (1$\sim$ 95 pc)." (Introduction); "With a redshift of z = 0.005457 (cite: Bureau1996), NGC 1365 is classified as a Seyfert 1.8 galaxy (cite: Veron2006), with signatures of both AGN activity and SF in its central regions." (Introduction); "We find the nuclear position to be RA = 03h33m36.37s and Dec = -36d08m25.37s, in good agreement with the values reported by (cite: Liu2023)." (ALMA); z/distance 19.57 Mpc; z = 0.005457  
  > "This dusty barred spiral galaxy (SB(s)b; (cite: deVaucouleurs1991)) is located in the Fornax cluster (cite: Jones1980) at a distance of 19.57 Mpc (cite: Jacobs09; Anand2021) (1$\sim$ 95 pc)." (Introduction); "With a redshift of z = 0.005457 (cite: Bureau1996), NGC 1365 is classified as a Seyfert 1.8 galaxy (cite: Veron2006), with signatures of both AGN activity and SF in its central regions." (Introduction); "We find the nuclear position to be RA = 03h33m36.37s and Dec = -36d08m25.37s, in good agreement with the values reported by (cite: Liu2023)." (ALMA); distance from (cite: Jacobs09; Anand2021) for distance; (cite: Bureau1996) for redshift  
  > "This dusty barred spiral galaxy (SB(s)b; (cite: deVaucouleurs1991)) is located in the Fornax cluster (cite: Jones1980) at a distance of 19.57 Mpc (cite: Jacobs09; Anand2021) (1$\sim$ 95 pc)." (Introduction); "With a redshift of z = 0.005457 (cite: Bureau1996), NGC 1365 is classified as a Seyfert 1.8 galaxy (cite: Veron2006), with signatures of both AGN activity and SF in its central regions." (Introduction); "We find the nuclear position to be RA = 03h33m36.37s and Dec = -36d08m25.37s, in good agreement with the values reported by (cite: Liu2023)." (ALMA)

## Data provenance

- ALMA projects: 2016.1.00296.S
- bands: Band 7  
  > "To trace the cold molecular gas, we used archival ALMA 12-m Band 7 observations (program 2016.1.00296.S, PI F.Combes; (cite: Combes_2019)) of the CO J=$3\rightarrow2$ transition at 345.796GHz (rest-frame)." (Overview of observations and data analysis)
- frequencies and spectral setup: CO(3-2) spectral window (342.99-344.86 GHz), spectral channel width ~8 km s^-1  
  > "For the CO(3–2) spectral window ($342.99-344.86$ GHz), we subtracted a constant continuum level estimated from the emission line-free channels in the *uv* plane." (ALMA); "The final datacube has a spectral channel width of $\sim$8 km s$^{-1}$, a pixel size of 0.05, a FoV of 25 in diameter, and a root mean square of 1.5 mJy beam$^{-1}$ per channel." (ALMA)
- continuum bandwidth: _not stated_
- arrays: 12-m  
  > "To trace the cold molecular gas, we used archival ALMA 12-m Band 7 observations (program 2016.1.00296.S, PI F.Combes; (cite: Combes_2019)) of the CO J=$3\rightarrow2$ transition at 345.796GHz (rest-frame)." (Overview of observations and data analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.30" (0.35" x 0.31" final beam, corresponding to ~37 pc)  
  > "In this work, we use the observations with resolution $\sim0.30$ corresponding to 30 pc, which better match the MIRI MRS spatial resolution and provide a maximum recoverable scale of 2.9." (ALMA); "The data were cleaned using the `tclean` task in `CASA`, with briggs weighting scheme with a robust parameter of 0.5, which resulted in a beam with a FWHM of 0.35$\times$ 0.31(beam PA = -71$^{\circ}$), corresponding to $\sim$37 pc in physical scale." (ALMA)
- max recoverable scale: 2.9"  
  > "In this work, we use the observations with resolution $\sim0.30$ corresponding to 30 pc, which better match the MIRI MRS spatial resolution and provide a maximum recoverable scale of 2.9." (ALMA)
- sensitivity: 1.5 mJy beam^-1 per ~8 km s^-1 channel  
  > "The final datacube has a spectral channel width of $\sim$8 km s$^{-1}$, a pixel size of 0.05, a FoV of 25 in diameter, and a root mean square of 1.5 mJy beam$^{-1}$ per channel." (ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival (PI F. Combes)  
  > "To trace the cold molecular gas, we used archival ALMA 12-m Band 7 observations (program 2016.1.00296.S, PI F.Combes; (cite: Combes_2019)) of the CO J=$3\rightarrow2$ transition at 345.796GHz (rest-frame)." (Overview of observations and data analysis)
- Line: CO J=3->2 (345.796 GHz)
- Other facility **JWST/MIRI**: MRS integral-field spectroscopy (4.9-27.9 um) from program 6138 (MIRACLE) retrieved from MAST  
  > "NGC 1365 was observed on 8 December 2024 as part of the “Mid-IR Activity of Circumnuclear Line Emission” (MIRACLE; JWST GO program 6138; Co-PIs: C. Marconcini and A. Feltre), aimed at tracing the mid-IR emission by exploiting MIRI/MRS data" (Overview of observations and data analysis); "We downloaded the uncalibrated science and background observations through the Barbara A. Mikulski Archive for Space Telescopes (MAST) portal." (JWST/MIRI)
- Other facility **VLT/MUSE**: Wide Field Mode optical IFU spectroscopy (4800-9300 A) from program 094.B-0321(A) (MAGNUM survey) retrieved from the ESO archive  
  > "The MUSE IFU observations of NGC 1365 were obtained on the 12th October 2014, under program 094.B-0321(A) (PI A. Marconi) and are part of the “Measuring AGN Under MUSE” (MAGNUM) survey" (Overview of observations and data analysis); "The data were retrieved from the ESO archive and were already processed automatically using the standard MUSE pipeline (v1.6), with an average PSF FWHM of 0.8." (MUSE Wide Field Mode)
- External data: Mid-IR line ratio model predictions for AGN, SF galaxies, and shocks  
  > "we show the contours of line ratio model predictions for AGN (cite: Feltre+23), SF galaxies (cite: Gutkin2016), and shocks (cite: Alarie2019)" (Resolved diagnostic diagrams for gas excitation) [from (cite: Feltre+23), (cite: Gutkin2016), (cite: Alarie2019)]
- External data: E-MILES stellar templates and broad [Fe II] emission template for MUSE pPXF continuum/BLR fitting  
  > "Using the penalized PiXel-Fitting (pPXF, (cite: Cappellari2004)) code, we fit simultaneously the continuum and gas emission in the wavelength range 4800-9200 , convolving a linear combination of stellar templates (E-MILES; for details see (cite: Vazdekis2016)) with a Gaussian velocity distribution." (MUSE WFM emission line fitting); "The BLR model consists of two independent components: a broad ($\sigma$>1000 km s$^{-1}$) Gaussian component for the broad Balmer lines (i.e., H$\alpha$ and H$\beta$) and a template of broad [Fe II] emission features by (cite: BorosonGreen1992)." (MUSE WFM emission line fitting) [from (cite: Vazdekis2016), (cite: BorosonGreen1992)]
- External data: BPASS v2.3 stellar population models used as incident spectra for SF photoionization grids  
  > "As is described in (cite: Marconi+2024), the incident spectra for the SF model grids are stellar population models from BPASS v2.3 (cite: Byrne2022; Stanway&Eldridge2018) including binary stellar evolution." (Model grids of AGNs and SF) [from (cite: Byrne2022; Stanway&Eldridge2018)]
- Simulation/model as data: CLOUDY single-cloud photoionization model grids (AGN and SF) used within the HOMERUN framework  
  > "The HOMERUN models the line emission with a weighted combination of multiple CLOUDY single-cloud photoionization models (cite: Ferland1998), iterating over different gas metallicities and incident radiation fields." (HOMERUN modeling approach)

## Processing

### Calibration

- pipeline or manual: calibrated measurement sets retrieved from European ALMA Regional Center service  
  > "We retrieved the calibrated measurement sets using the dedicated service provided by the European ALMA Regional Center (cite: Hatzimi_2015)." (ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA v6.1.1  
  > "Imaging was performed using the Common Astronomy Software Applications (`CASA`) v6.1.1 (cite: CASATeam2022)." (ALMA); "The data were cleaned using the `tclean` task in `CASA`, with briggs weighting scheme with a robust parameter of 0.5, which resulted in a beam with a FWHM of 0.35$\times$ 0.31(beam PA = -71$^{\circ}$), corresponding to $\sim$37 pc in physical scale." (ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs weighting with robust = 0.5  
  > "The data were cleaned using the `tclean` task in `CASA`, with briggs weighting scheme with a robust parameter of 0.5, which resulted in a beam with a FWHM of 0.35$\times$ 0.31(beam PA = -71$^{\circ}$), corresponding to $\sim$37 pc in physical scale." (ALMA)
- uv taper: _not stated_
- cell size: 0.05"  
  > "The final datacube has a spectral channel width of $\sim$8 km s$^{-1}$, a pixel size of 0.05, a FoV of 25 in diameter, and a root mean square of 1.5 mJy beam$^{-1}$ per channel." (ALMA)
- image size: FoV of 25" in diameter  
  > "The final datacube has a spectral channel width of $\sim$8 km s$^{-1}$, a pixel size of 0.05, a FoV of 25 in diameter, and a root mean square of 1.5 mJy beam$^{-1}$ per channel." (ALMA)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: constant continuum level estimated from emission line-free channels subtracted in the uv plane  
  > "For the CO(3–2) spectral window ($342.99-344.86$ GHz), we subtracted a constant continuum level estimated from the emission line-free channels in the *uv* plane." (ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.35" x 0.31" (PA = -71 deg)  
  > "The data were cleaned using the `tclean` task in `CASA`, with briggs weighting scheme with a robust parameter of 0.5, which resulted in a beam with a FWHM of 0.35$\times$ 0.31(beam PA = -71$^{\circ}$), corresponding to $\sim$37 pc in physical scale." (ALMA)
- final rms: 1.5 mJy beam^-1 per ~8 km s^-1 channel  
  > "The final datacube has a spectral channel width of $\sim$8 km s$^{-1}$, a pixel size of 0.05, a FoV of 25 in diameter, and a root mean square of 1.5 mJy beam$^{-1}$ per channel." (ALMA)

### Inherited from earlier work

- JWST/MIRI MRS data reduction and PSF deconvolution methodology  
  > "We summarize the data reduction in Appendix 6.1, referring to (cite: MIRACLE_NGC424) for a detailed description." (Overview of observations and data analysis); "The deconvolution procedure is composed by a wavelength-dependent alignment, rotation and flux normalization between the PSFs and our flux maps, following a similar methodology of (cite: MIRACLE_NGC424)." (MIRI datacubes corrections) [from (cite: MIRACLE_NGC424)]
- MUSE data reduction pipeline and emission line analysis procedure  
  > "We applied the same data reduction pipeline that has been extensively applied in previous works (cite: Venturi_2018; Mingozzi2019), and which has been validated and described in detail therein." (Overview of observations and data analysis); "MUSE data were analyzed as already described in previous works of the MAGNUM program (cite: Venturi_2018; Mingozzi2019)." (MUSE WFM emission line fitting) [from (cite: Venturi_2018; Mingozzi2019)]
- Analytical/classical ionized outflow mass derivation method  
  > "In this appendix we present an analytical mass estimation for the" (Ionized gas mass estimate) [from (cite: Carniani2015)]

### Not stated but needed to reproduce (our reading)

- Exact frequency/channel ranges used as emission line-free channels for ALMA uv-plane continuum subtraction
- Stopping threshold, niter, deconvolver, and masking parameters used in CASA tclean for ALMA CO(3-2) imaging
- Which specific execution blocks of ALMA project 2016.1.00296.S correspond to the ~0.30 arcsec resolution configuration used

## Analysis recipe

1. **Reduce, align, reproject, and stitch multi-band datacubes (ALMA, MIRI, MUSE)**: Image ALMA CO(3-2) cube in CASA and fit a 2D Gaussian to the central 2"x2" CO(3-2) flux map to define the nuclear astrometric reference; reduce MIRI MRS cubes with JWST pipeline v1.16.0, align MIRI and MUSE astrometry to the ALMA nuclear coordinates, reproject MIRI cubes to a common pixel grid, and stitch MIRI sub-band fluxes to Ch4 LONG.  
  > "Finally, we fit the central $2\text{\arcsec}\times2\text{\arcsec}$ of the CO(3-2) flux map (see Appendix 8.3) with a Gaussian profile to determine the coordinates of the nucleus, taking advantage of the high astrometric accuracy provided by ALMA." (ALMA); "We used the `reproject exact` function to ensure flux conservation during the resampling process." (MIRI datacubes corrections); "To address this, we implemented a stitching procedure between each pair of datacubes by rescaling the flux of the bluer datacube to match the median flux value of the overlapping spectral channels of the redder datacube." (MIRI datacubes corrections)
   - software: CASA, tclean, JWST Science Calibration Pipeline, MUSE pipeline, reproject, WebbPSF
   - parameter: ALMA nuclear position RA = 03h33m36.37s, Dec = -36d08m25.37s; MUSE shift (-0.78", +0.22"); MIRI shifts (+0.0086", -0.2655"), (+0.0256", -0.2713"), (-0.0300", -0.299")  
  > "The applied corrections were $\Delta$RA and $\Delta$Dec shifts of (-0.78, +0.22)." (MUSE Wide Field Mode); "We find the nuclear position to be RA = 03h33m36.37s and Dec = -36d08m25.37s, in good agreement with the values reported by (cite: Liu2023)." (ALMA); "The applied corrections were $\Delta$RA and $\Delta$Dec shifts of (+0.0086, -0.2655), (+0.0256, -0.2713), and (-0.0300, -0.299) for the SHORT, MEDIUM, and LONG channels, respectively." (MIRI datacubes corrections)
   - assumption: _not stated_
   - fitting: 2D Gaussian fit to ALMA CO(3-2) central 2"x2" flux map and to collapsed MIRI Ch3 PSFs  
  > "Finally, we fit the central $2\text{\arcsec}\times2\text{\arcsec}$ of the CO(3-2) flux map (see Appendix 8.3) with a Gaussian profile to determine the coordinates of the nucleus, taking advantage of the high astrometric accuracy provided by ALMA." (ALMA); "We collapsed the datacubes along the spectral dimension and fit the PSFs with a 2D Gaussian model." (MIRI datacubes corrections)
   - validation: Relative flux conservation error after spatial rebinning is below 1%  
  > "The relative flux conservation error is below the 1$\%$, so negligible respect the original flux." (MIRI datacubes corrections)
2. **Fit emission lines spaxel-by-spaxel and generate moment maps across ALMA, MIRI, and MUSE**: Fit ALMA CO(3-2) with a single Gaussian per spaxel; smooth MIRI cubes with a 1-pixel Gaussian kernel, subtract a linear local continuum, and fit 1-2 Gaussians per spaxel; Voronoi-bin MUSE cubes to S/N>=70, subtract stellar+BLR continuum using pPXF, and fit 1-3 Gaussians per spaxel.  
  > "We followed a three-step procedure: first, we applied spatial smoothing to enhance the S/N; second, we subtracted the local continuum around the brightest emission lines; finally, we performed spaxel-by-spaxel Gaussian fitting of the residual emission." (JWST/MIRI MRS emission line fitting); "In this case, we used up to three Gaussian components to reproduce the complex line profiles and adopted a p-value of 0.9." (MUSE WFM emission line fitting); "We fit the CO(3-2) line profile in each spaxel using a single Gaussian profile, which is sufficient to reproduce the symmetric line profile." (ALMA emission line fitting)
   - software: pPXF, dust_extinction
   - parameter: KS test threshold p-value = 0.7 for MIRI (1-2 Gaussians) and p-value = 0.9 for MUSE (up to 3 Gaussians)  
  > "Each emission line is modeled with both a single and a double Gaussian component, and then we applied a Kolmogorov-Smirnov (KS) test on the residuals to choose the optimal number of Gaussian components in each spaxel, adopting a threshold p-value of 0.7" (JWST/MIRI MRS emission line fitting); "In this case, we used up to three Gaussian components to reproduce the complex line profiles and adopted a p-value of 0.9." (MUSE WFM emission line fitting)
   - assumption: Case-B hydrogen recombination ratio Halpha/Hbeta = 2.86 and G23 attenuation law for optical dust correction  
  > "Finally, we corrected the optical emission-line fluxes for dust attenuation using the Balmer decrement (i.e., H$\alpha$/H$\beta$), assuming a case-B hydrogen recombination value of 2.86 for this ratio (cite: Osterbrock2006) and adopting the G23 attenuation law." (MUSE WFM emission line fitting)
   - fitting: Multi-Gaussian spectral line fitting with component number selected via Kolmogorov-Smirnov test on residuals  
  > "Each emission line is modeled with both a single and a double Gaussian component, and then we applied a Kolmogorov-Smirnov (KS) test on the residuals to choose the optimal number of Gaussian components in each spaxel, adopting a threshold p-value of 0.7" (JWST/MIRI MRS emission line fitting)
   - validation: Tested mid-IR extinction impact with A_V ~ 3 and found mid-IR line ratio variations are within errors  
  > "However, we find that the resulting variations in the mid-IR line ratios are within the errors, including those involving emission lines at distant wavelengths" (JWST/MIRI MRS emission line fitting)
3. **Construct resolved diagnostic diagrams and derive electron density maps and aperture values**: Match FoV, pixel scale, and PSF across emission lines using WebbPSF deconvolution/convolution, compare mid-IR and optical BPT line ratios to AGN/SF/shock grids, and compute electron densities from [Ne V]24um/14um and [S II]6716/6731 using PyNeb.  
  > "In practice, for each diagnostic diagram we adopted the FoV, pixel size, and PSF corresponding to the worst case among the lines involved, as is described below." (Resolved diagnostic diagrams for gas excitation); "using PyNeb (cite: Luridiana+2015), assuming an electron temperature $T_e = 10^4$ K" (Electron density estimation)
   - software: PyNeb, WebbPSF
   - parameter: 1.5" (~140 pc) radius aperture centered on the outflow region for integrated optical/mid-IR density comparison  
  > "For a quantitative comparison between the optical and mid-IR tracers, we measured the electron density from integrated spectra extracted within a 1.5($\sim$ 140 pc) radius aperture centered on the outflow region (see Fig. 6), using both the mid-IR and optical tracers." (Electron density estimation)
   - assumption: Electron temperature T_e = 10^4 K; metallicity cut Z > 0.006 for diagnostic grids  
  > "We include all available model grids, applying only a metallicity cut of $Z > 0.006$ (see (cite: Feltre+23) for further details on the models)." (Resolved diagnostic diagrams for gas excitation); "using PyNeb (cite: Luridiana+2015), assuming an electron temperature $T_e = 10^4$ K" (Electron density estimation)
   - fitting: _not stated_
   - validation: Compared mid-IR [Ne V] density with optical [S II] density and Spitzer/IRS literature measurements  
  > "From the mid-IR [Ne V] line ratio, we estimate an electron density of (750$\pm$440) cm$^{-3}$, while from the [S II] lines we find a consistent value of (350$\pm$40) cm$^{-3}$." (Electron density estimation)
4. **Model optical and mid-IR line fluxes with HOMERUN and kinematic outflow structure with MOKA3D to derive outflow mass and energetics**: Fit 60 optical+mid-IR emission lines in the 1.5" radius aperture using HOMERUN (combining dust-free AGN and dusty SF CLOUDY model grids) to derive ionized gas masses, and fit [Ne V]14um and [O III]5007A cubes with MOKA3D to obtain deprojected outflow velocities and energetics.  
  > "We fit the fluxes of 60 ionized and neutral atomic emission lines measured from the MIRI and MUSE spectra (32 from MIRI and 28 from MUSE, see Figs. 2 and 9) extracted within a 1.5 radius aperture centered on the outflow region (see Fig. 6)." (HOMERUN fitting results); "We inferred the [Ne V]$\lambda 14\mu\mathrm{m}$ and [O III]$\lambda 5007\text{\AA}$ intrinsic (i.e., de-projected) radial velocities of the outflow (v$_\mathrm{out}$) using the 3D multicloud $\mathrm{MOKA^{3D}}$ kinematic model (cite: Marconcini2023)." (Outflow energetics)
   - software: HOMERUN, CLOUDY, BPASS, MOKA3D
   - parameter: MOKA3D conical outflow maximum extension = 5 arcsec (~470 pc), PA = 235 deg; energetics radial extent Delta R = 284 pc (~3")  
  > "To reproduce the outflow features in NGC 1365, we adopted a conical outflow morphology with maximum extension of 5 arcsec ($\sim$ 470 pc) and position angle of 235$^{\circ}$." (Outflow energetics); "So, adopting $\Delta$R = 284 pc ($\sim$ 3, i.e., the sky-projected extension of the 1.5 radius aperture)" (Outflow energetics)
   - assumption: Outflowing gas is fully ionized by the AGN (dust-free AGN clouds, dusty SF clouds with equal metallicity); constant flux density over time in each spaxel  
  > "Both components were assumed to have the same metallicity; however, while we adopted dust-free models for the AGN component, we included dust in the SF models and corrected gas-phase metallicities using the depletion factors listed in Table 7.8 of Hazy 1 (Cloudy v23.1)." (Model grids of AGNs and SF); "In this way, under the assumption that the outflowing gas is fully ionized by the AGN, we avoided including the contribution from systemic or SF-related components, ensuring that the derived masses trace the outflowing gas itself." (Ionized gas mass from HOMERUN)
   - fitting: Non-negative least squares without regularization in HOMERUN minimizing reduced-chi2 loss function L_min; 3D spaxel-by-spaxel kinematic fitting in MOKA3D  
  > "This is achieved by solving a non-negative least squares problem, whereby the weights of each cloud are constrained to be non-negative." (HOMERUN modeling approach); "This loss function is effectively a reduced $\chi^2$ statistic, so values $\lesssim 1$ indicate a statistically good fit." (HOMERUN modeling approach)
   - validation: Majority of 60 lines reproduced within 15% accuracy (L_min = 0.6); MOKA3D reproduces observed moment maps with discrepancies below 5%  
  > "The unique approach of HOMERUN enables us to reproduce at the same time 60 different emission lines in different ionization stages, with the majority of them reproduced with better than 15$\%$ accuracy." (HOMERUN fitting results); "With $\mathrm{MOKA^{3D}}$ we reproduce the line emission on a spaxel-by-spaxel basis, which as a consequence guarantee that the model reproduces the observed moment maps, with discrepancies between observed and modeled moment maps below 5$\%$." (Outflow energetics)

## Software

- **CASA** v6.1.1: ALMA CO(3-2) continuum subtraction and imaging  
  > "Imaging was performed using the Common Astronomy Software Applications (`CASA`) v6.1.1 (cite: CASATeam2022)." (ALMA)
- **tclean** : Cleaning the ALMA CO(3-2) datacube  
  > "The data were cleaned using the `tclean` task in `CASA`, with briggs weighting scheme with a robust parameter of 0.5, which resulted in a beam with a FWHM of 0.35$\times$ 0.31(beam PA = -71$^{\circ}$), corresponding to $\sim$37 pc in physical scale." (ALMA)
- **JWST Science Calibration Pipeline** 1.16.0 (CRDS context 1298): Reducing JWST/MIRI MRS science and background observations  
  > "The data reduction process was performed using the JWST Science Calibration Pipeline (cite: Bushouse2022_pipeline) version $1.16.0$ with JWST Calibration Reference Data System context file 1298." (JWST/MIRI)
- **MUSE pipeline** v1.6: Automatic processing of archival VLT/MUSE observations  
  > "The data were retrieved from the ESO archive and were already processed automatically using the standard MUSE pipeline (v1.6), with an average PSF FWHM of 0.8." (MUSE Wide Field Mode)
- **PyNeb** : Deriving electron density and line emissivities from [Ne V] and [S II] line ratios  
  > "using PyNeb (cite: Luridiana+2015), assuming an electron temperature $T_e = 10^4$ K" (Electron density estimation); "Assuming a typical temperature (T$_e \simeq 10^4 K$), from the [Ne V]$\lambda 24\mu\mathrm{m}$/[Ne V]$\lambda 14\mu\mathrm{m}$ line ratio we find an electron density of n$_e$ = (750$\pm$440) cm$^{-3}$ in the 1.5" radius aperture and estimate a line emissivity of $\gamma_\text{[Ne\,V]} = 1.93 \times 10^{-20}$ erg s$^{-1}$ cm$^{3}$ making use of PyNeb (cite: Luridiana+2015)." (Ionized gas mass estimate)
- **HOMERUN** : Multicloud photoionization modeling of 60 optical and mid-IR emission lines and ionized gas mass estimation  
  > "Specifically, we employed the Highly Optimized Multi-cloud Emission-line Ratios Using photo-ionizatioN (HOMERUN) modeling framework developed by (cite: Marconi+2024)." (Photoionization modeling with HOMERUN)
- **CLOUDY** v23.1: Generating single-cloud photoionization model grids used by HOMERUN  
  > "Both components were assumed to have the same metallicity; however, while we adopted dust-free models for the AGN component, we included dust in the SF models and corrected gas-phase metallicities using the depletion factors listed in Table 7.8 of Hazy 1 (Cloudy v23.1)." (Model grids of AGNs and SF); "The HOMERUN models the line emission with a weighted combination of multiple CLOUDY single-cloud photoionization models (cite: Ferland1998), iterating over different gas metallicities and incident radiation fields." (HOMERUN modeling approach)
- **BPASS** v2.3: Providing stellar population incident spectra for SF photoionization model grids  
  > "As is described in (cite: Marconi+2024), the incident spectra for the SF model grids are stellar population models from BPASS v2.3 (cite: Byrne2022; Stanway&Eldridge2018) including binary stellar evolution." (Model grids of AGNs and SF)
- **MOKA3D** : 3D multicloud kinematic modeling of the [Ne V] and [O III] outflow  
  > "We inferred the [Ne V]$\lambda 14\mu\mathrm{m}$ and [O III]$\lambda 5007\text{\AA}$ intrinsic (i.e., de-projected) radial velocities of the outflow (v$_\mathrm{out}$) using the 3D multicloud $\mathrm{MOKA^{3D}}$ kinematic model (cite: Marconcini2023)." (Outflow energetics)
- **pPXF** : Simultaneous stellar continuum and gas emission line fitting in MUSE datacubes  
  > "Using the penalized PiXel-Fitting (pPXF, (cite: Cappellari2004)) code, we fit simultaneously the continuum and gas emission in the wavelength range 4800-9200 , convolving a linear combination of stellar templates (E-MILES; for details see (cite: Vazdekis2016)) with a Gaussian velocity distribution." (MUSE WFM emission line fitting)
- **WebbPSF** v.1.4.0: Generating MIRI MRS PSF model cubes for deconvolution and PSF matching  
  > "To ensure consistent spatial resolution, we firstly downloaded the MIRI MRS PSF model cube using the *WebbPSF* tool v.1.4.0 (cite: Perrin2014), which provide a model cube spatially oversampled of a factor of 4 with respect to the observations (i.e., 0.05 /pixel for Ch3)." (MIRI datacubes corrections)
- **dust_extinction** : Applying the G23 dust attenuation curve to optical and mid-IR emission lines  
  > "To test the potential impact of dust attenuation, we applied an extinction correction to the mid-IR emission lines using the G23 (cite: Gordon09; Gordon21; Gordon+2023; Fitzpatrick19; Decleir22) attenuation curve, from the *dust$\_$extinction* package (cite: Gordon24_dustextinction_package)" (JWST/MIRI MRS emission line fitting)
- **reproject** : Flux-conserving spatial rebinning of MIRI datacubes via reproject exact  
  > "We used the `reproject exact` function to ensure flux conservation during the resampling process." (MIRI datacubes corrections)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Electron density from [Ne V]24um/[Ne V]14um (1.5" radius outflow aperture) | 750 | 440 | cm^-3 | 3 | We derived the electron density from the [Ne V]$\lambda 24\mu\mathrm{m}$/[Ne V]$\lambda 14\mu\mathrm{m}$ line ratio, finding a median value of (750$\pm$440) cm$^{-3}$, consistent with previous estimates obtained from the optical [S II] doublet.; From the mid-IR [Ne V] line ratio, we estimate an electron density of (750$\pm$440) cm$^{-3}$, while from the [S II] lines we find a consistent value of (350$\pm$40) cm$^{-3}$. |
| Electron density from [S II] doublet (1.5" radius outflow aperture) | 350 | 40 | cm^-3 | 3 | From the mid-IR [Ne V] line ratio, we estimate an electron density of (750$\pm$440) cm$^{-3}$, while from the [S II] lines we find a consistent value of (350$\pm$40) cm$^{-3}$. |
| Median electron density log(n_e/cm^-3) across MIRI FoV from [Ne V] ratio | 2.7 | 0.5 | dex (log(cm^-3)) | 3 | Across the FoV, we estimate a median electron density of log($n_e$/cm$^{-3}$) = (2.7 $\pm$ 0.5), with a peak of log($n_e$/cm$^{-3}$)$\sim$3.5 at the nucleus. |
| HOMERUN best-fit oxygen abundance 12+log(O/H) | 8.91 | not stated | dimensionless | 4 | The minimum of the curve is found for the minimum loss function of $\mathcal{L}_\mathrm{min}$ = 0.6, corresponding to 12+log(O/H) = 8.91. |
| HOMERUN AGN component mean parameters (A_V, log(n_H/cm^-3), log(U)) | 1.4, 2.9, -1.4 | not stated | mag, dex, dex | 4 | The data are best matched by a SF component with mean $\rm A_V$ = 3.3, $\rm log(n_H$ / cm$^{-3}$) = 1.3, and $\rm log(U)$ = -3.3 and an AGN component with mean $\rm A_V$ = 1.4, $\rm log(n_H$ / cm$^{-3}$) = 2.9, and $\rm log(U)$ = -1.4 (see Fig. 7). |
| HOMERUN SF component mean parameters (A_V, log(n_H/cm^-3), log(U)) | 3.3, 1.3, -3.3 | not stated | mag, dex, dex | 4 | The data are best matched by a SF component with mean $\rm A_V$ = 3.3, $\rm log(n_H$ / cm$^{-3}$) = 1.3, and $\rm log(U)$ = -3.3 and an AGN component with mean $\rm A_V$ = 1.4, $\rm log(n_H$ / cm$^{-3}$) = 2.9, and $\rm log(U)$ = -1.4 (see Fig. 7). |
| Ionized outflow mass M_[Ne V] from HOMERUN | 109 | 2 | 10^3 M_sun | 4 | We computed an outflow mass of $\rm M_{[Ne V]}$ = (109 $\pm$ 2) $\times$ 10$^{3}$ $\mathrm{M_\odot}$ and $\rm M_{[O III]}$ = (88 $\pm$ 9) $\times$ 10$^{3}$ $\mathrm{M_\odot}$ within the 1.5 radius aperture. |
| Ionized outflow mass M_[O III] from HOMERUN | 88 | 9 | 10^3 M_sun | 4 | We computed an outflow mass of $\rm M_{[Ne V]}$ = (109 $\pm$ 2) $\times$ 10$^{3}$ $\mathrm{M_\odot}$ and $\rm M_{[O III]}$ = (88 $\pm$ 9) $\times$ 10$^{3}$ $\mathrm{M_\odot}$ within the 1.5 radius aperture. |
| Ionized outflow mass M_[Ne V] from classic/standard method | 2.6 | 1.0 | 10^3 M_sun | 4 | Overall, with the classic method we find in the same spatial region $\rm M_{[Ne V]}$ = (2.6 $\pm$ 1.0) $\times$ 10$^{3}$ $\mathrm{M_\odot}$ and $\rm M_{[O III]}$ = (20 $\pm$ 7) $\times$ 10$^{4}$ $\mathrm{M_\odot}$. |
| Ionized outflow mass M_[O III] from classic/standard method | 20 | 7 | 10^4 M_sun | 4 | Overall, with the classic method we find in the same spatial region $\rm M_{[Ne V]}$ = (2.6 $\pm$ 1.0) $\times$ 10$^{3}$ $\mathrm{M_\odot}$ and $\rm M_{[O III]}$ = (20 $\pm$ 7) $\times$ 10$^{4}$ $\mathrm{M_\odot}$. |
| [Ne V]14um intrinsic outflow velocity v_out from MOKA3D | 390 | 35 | km s^-1 | 4 | We found that the best-fit parameters that reproduce the [Ne V]$\lambda 14\mu\mathrm{m}$ outflow features in NGC 1365 are $\beta$ = 82 $\pm$ 6$^{\circ}$, and v$_{\rm out}$ = 390 $\pm$ 35 km s$^{-1}$, consistent with the results in (cite: Marconcini2025_nat). |
| [Ne V]14um outflow cone inclination beta from MOKA3D | 82 | 6 | deg | 4 | We found that the best-fit parameters that reproduce the [Ne V]$\lambda 14\mu\mathrm{m}$ outflow features in NGC 1365 are $\beta$ = 82 $\pm$ 6$^{\circ}$, and v$_{\rm out}$ = 390 $\pm$ 35 km s$^{-1}$, consistent with the results in (cite: Marconcini2025_nat). |
| [O III]5007A intrinsic outflow velocity v_out from MOKA3D | 470 | 40 | km s^-1 | 4 | Moreover, we used $\mathrm{MOKA^{3D}}$ to fit the [O III]$\lambda 5007\text{\AA}$ spatially resolved emission assuming the same outflow geometry as for the [Ne V]$\lambda 14\mu\mathrm{m}$ emission and found $\beta$ = 84 $\pm$ 5$^{\circ}$, and v$_{\rm out}$ = 470 $\pm$ 40 km s$^{-1}$. |
| [O III]5007A outflow cone inclination beta from MOKA3D | 84 | 5 | deg | 4 | Moreover, we used $\mathrm{MOKA^{3D}}$ to fit the [O III]$\lambda 5007\text{\AA}$ spatially resolved emission assuming the same outflow geometry as for the [Ne V]$\lambda 14\mu\mathrm{m}$ emission and found $\beta$ = 84 $\pm$ 5$^{\circ}$, and v$_{\rm out}$ = 470 $\pm$ 40 km s$^{-1}$. |
| Mass outflow rate Mdot_[Ne V] from HOMERUN+MOKA3D | 1.72 | 0.20 | 10^-1 M_sun yr^-1 | 4 | From HOMERUN, we calculated consistent mass outflow rates for [Ne V]$\lambda 14\mu\mathrm{m}$ and [O III]$\lambda 5007\text{\AA}$, namely $\dot{\rm M}_{[Ne~V]}$ = $\left(1.72~\pm~0.20\right)~\times~10^{-1}$ M$_\odot$ yr$^{-1}$ and $\dot{\rm M}_{[O~III]}$ = $\left(1.68~\pm~0.31\right)~\times~10^{-1}$ M$_\odot$ yr$^{-1}$, respectively. |
| Mass outflow rate Mdot_[O III] from HOMERUN+MOKA3D | 1.68 | 0.31 | 10^-1 M_sun yr^-1 | 4 | From HOMERUN, we calculated consistent mass outflow rates for [Ne V]$\lambda 14\mu\mathrm{m}$ and [O III]$\lambda 5007\text{\AA}$, namely $\dot{\rm M}_{[Ne~V]}$ = $\left(1.72~\pm~0.20\right)~\times~10^{-1}$ M$_\odot$ yr$^{-1}$ and $\dot{\rm M}_{[O~III]}$ = $\left(1.68~\pm~0.31\right)~\times~10^{-1}$ M$_\odot$ yr$^{-1}$, respectively. |

## Qualitative findings

- Cold molecular gas (CO 3-2) and warm molecular gas (H2 pure-rotational lines) trace the rotating circumnuclear ring and stellar disk without evidence of a molecular outflow.  
  > "The cold molecular gas traced by the CO(3-2) transition shares the same ordered kinematics of the stellar galaxy disk (cite: Venturi_2018), with no evidence of outflowing material." (Conclusions); "The same conclusion holds for the warm molecular gas traced by the H$_2$ pure-rotational transitions, with the exception of a peculiar high-$\sigma$ unresolved region located southward of the nucleus." (Conclusions)
- Ionized gas morphology and kinematics stratify by ionization potential: low-IP (<25 eV) species trace the rotating disk and circumnuclear ring, while high-IP (>54 eV) species trace the bipolar outflow including the dust-obscured NW receding counter-cone.  
  > "Low-IP species ($\leq$ 25 eV) mainly trace the rotating disk, while higher-IP species (up to $\sim$120 eV) trace the outflowing gas." (abstract); "The [Ne V]$\lambda 14\mu\mathrm{m}$ emission also reveals the NW receding counterpart of the ionization cone, which is undetected in [O III]$\lambda 5007\text{\AA}$ due to large extinction caused by the galaxy disk at optical wavelengths." (Conclusions)
- Mid-IR diagnostic diagrams penetrate central dust obscuration to reveal AGN ionization at the nucleus and shock/AGN interaction zones at the edge of the circumnuclear ring, whereas optical BPT diagrams at the nucleus appear SF-dominated due to dust extinction.  
  > "In the nuclear region, the optical BPT appears to be dominated by SF due to strong dust obscuration, as is indicated by the Balmer decrement (see Appendix 9 and Fig. 12). In contrast, mid-IR diagnostics can penetrate the dust screen and clearly reveal AGN ionization at the nucleus." (Resolved diagnostic diagrams for gas excitation)

## Claim tuples

- H: Cold and warm molecular gas and ionized gas species across different ionization potentials trace distinct kinematic components (rotating disk vs. bipolar AGN outflow) in the circumnuclear region of NGC 1365. | E: Fit emission lines spaxel-by-spaxel in JWST/MIRI MRS, VLT/MUSE, and ALMA CO(3-2) datacubes to produce moment maps and velocity channel maps across gas phases and ionization potentials. | R: CO(3-2), H2 0-0 S(1)-S(7), and low-IP (<25 eV) ionized lines follow stellar disk rotation (~110-120 km s^-1) in the circumnuclear ring, while high-IP (>54 eV) lines like [Ne V]14um trace the SE-NW bipolar outflow (up to -120/+100 km s^-1, sigma up to ~170 km s^-1) and reveal the obscured NW receding cone. | F: Molecular and low-IP ionized gas trace the rotating disk with no molecular outflow in the circumnuclear region, whereas high-IP ionized species trace the AGN-driven biconical outflow through the dust. | **supported**
- H: Spatially resolved mid-IR line ratios can penetrate nuclear dust obscuration in NGC 1365 to reveal the true ionizing mechanism and gas density compared to optical diagnostics. | E: Construct PSF-matched mid-IR diagnostic diagrams ([O IV]/[Ne II], [Ne III]/[Ne II], [Ne V]/[Ne II]) and compare with optical MUSE BPT diagrams; compute electron densities from [Ne V]24um/14um and [S II]6716/6731 using PyNeb. | R: Mid-IR diagnostic maps show AGN and shock/AGN excitation in the central region where optical BPT diagrams appear SF-dominated (with A_V up to 3.7 mag); [Ne V]24um/14um yields n_e = (750 +/- 440) cm^-3 in the outflow aperture compared to (350 +/- 40) cm^-3 from [S II]. | F: Mid-IR diagnostics penetrate the nuclear dust screen to reveal central AGN ionization and denser gas closer to the AGN that are obscured or diluted in optical tracers. | **supported**
- H: Combining multicloud photoionization modeling (HOMERUN) with 3D kinematic modeling (MOKA3D) overcomes the inconsistencies of classical single-density/single-ionization outflow mass and energetics estimates. | E: Simultaneously fit 60 optical and mid-IR emission lines in a 1.5" aperture with HOMERUN and fit 3D outflow kinematics of [Ne V]14um and [O III]5007A with MOKA3D, comparing derived outflow masses and rates against the classical method. | R: HOMERUN+MOKA3D yields consistent ionized outflow masses (M_[Ne V] = 109 +/- 2 x 10^3 M_sun, M_[O III] = 88 +/- 9 x 10^3 M_sun) and mass outflow rates (~0.17 M_sun yr^-1) for both tracers, whereas the classical method gives discrepant masses by a factor of ~75 between [Ne V] (2.6 x 10^3 M_sun) and [O III] (20 x 10^4 M_sun). | F: Self-consistent multicloud photoionization and 3D kinematic modeling reconciles optical and mid-IR outflow tracers and shows that classical methods severely underestimate outflow masses for high-ionization species like [Ne V]. | **supported**

## Reasoning

- Why this data: Combining JWST/MIRI MRS, VLT/MUSE, and ALMA ~0.30" CO(3-2) data traces ionized atomic, warm molecular, and cold molecular gas at matched spatial resolution across obscured nuclear regions.  
  > "For NGC 1365, we combined data from the Medium-Resolution Spectrometer (MRS; (cite: Rieke2015; Labiano_21)) of MIRI with integral-field optical spectroscopy from VLT/MUSE and millimeter observations from ALMA." (Introduction); "In this work, we use the observations with resolution $\sim0.30$ corresponding to 30 pc, which better match the MIRI MRS spatial resolution and provide a maximum recoverable scale of 2.9." (ALMA)
- Why this method: HOMERUN+MOKA3D self-consistently decomposes superposed AGN and SF ionization components across 60 lines without assuming fixed ionization fractions or single densities, while 3D kinematic modeling accounts for outflow geometry and projection.  
  > "Lastly, we applied, for the first time, a fully self-consistent combination of state-of-the-art photoionization and kinematic models (HOMERUN+$\mathrm{MOKA^{3D}}$) to estimate the intrinsic physical outflow properties, kinematics, and energetics - overcoming the limitations of classical methods based on oversimplified assumptions." (abstract)
- Alternative: CO(1-0) molecular outflow interpretation by Gao et al. (2021) is rejected in favor of noncircular bar-driven inflowing motions  
  > "This finding, which is consistent with the lack of any molecular outflow in the circumnuclear region (cite: Combes_2019), is in contrast to the CO (1-0) wind reported by (cite: Gao2021)." (Multiphase gas kinematics); "Their outflow interpretation was based on velocity residuals from a rotating disk model on larger spatial scales, which resemble those observed in H$\alpha$ and are more likely due to noncircular inflowing motions along the bar (see their Fig. 6)." (Multiphase gas kinematics)
- Alternative: Shock photoionization models were excluded from the HOMERUN multiline fitting because photoionizing shocks are inefficient in powering AGN narrow-line emission and shock grids largely overlap with AGN and SF grids  
  > "However, (cite: Laor1998) showed that photoionizing shocks are extremely inefficient in powering the narrow line emission in AGNs." (Resolved diagnostic diagrams for gas excitation); "For these reasons, in Section 3.5 we consider only AGN and SF grids to model the optical and mid-IR emission lines." (Resolved diagnostic diagrams for gas excitation)
- Alternative: Nuclear torus differential IR extinction explanation by Dudik et al. (2007) for [Ne V] ratios in the low-density limit is ruled out in favor of Spitzer/IRS aperture loss effects  
  > "Exploiting the spatially resolved [Ne V] emission in our data and the density values in the nuclear region, we can rule out this interpretation." (Density comparison with IRS observations); "This means that the SH module surely lost part of the [Ne V]$\lambda 14\mu\mathrm{m}$ flux, leading to an artificially enhancement of the [Ne V]$\lambda 24\mu\mathrm{m}$/[Ne V]$\lambda 14\mu\mathrm{m}$ line ratio." (Density comparison with IRS observations)
- How they decided it was enough: _not stated_
- Limitation (authors): MIRI Ch3 FoV includes some AGN-illuminated disk gas not part of the outflow, though all gas in the ionization cone is assumed to be outflowing in the analysis.  
  > "Although in this analysis we focus on the FoV of Ch3, which also includes a fraction of disk gas illuminated by the AGN and not part of the outflow, it would be more accurate to refer to this region as the ionization cone rather than calling it outflow. However, we will assume in the following that all the gas in the ionization cone is in outflow." (Multiphase gas kinematics)
- Limitation (authors): Strong nuclear continuum emission dominates the spectra at the galaxy nucleus, causing an apparent lack of line emission in some moment maps.  
  > "Note that while some lines appear to lack emission in the nuclear region of the galaxy in the moment maps, this is because the spectra are dominated by strong continuum emission rather than a genuine absence of emission." (Multiphase gas kinematics)
- Limitation (authors): Low S/N of mid-IR hydrogen recombination lines (Pf-alpha and Hu-alpha) prevents deriving a spatially resolved extinction map directly from the mid-IR spectra.  
  > "Unfortunately, in our data the S/N of the Pf$\alpha$ and Hu$\alpha$ (i.e., H I (6−5) at 7.46 $\mu$m and H I (7−6) at 12.37 $\mu$m, respectively) is too low to derive a reliable extinction map directly from the mid-IR spectra." (JWST/MIRI MRS emission line fitting)
- Limitation (authors): HOMERUN mass-luminosity scaling relations derived for NGC 1365 are customized to its specific physical conditions and are not universally applicable to other AGNs without dedicated fitting.  
  > "They are derived specifically from the HOMERUN multicloud modeling customized for the physical conditions and emission properties of NGC 1365. Therefore, applying these relations to other galaxies requires performing a dedicated HOMERUN fit" (Ionized gas mass from HOMERUN)
- Caveat (inferred, ours): Assuming all AGN-ionized gas within the 1.5 arcsec aperture is outflowing (rather than partially systemic illuminated disk gas) may overestimate the total outflowing mass and energetics.
- Caveat (inferred, ours): The HOMERUN modeling is performed on an integrated 1.5 arcsec radius aperture rather than spaxel-by-spaxel, whereas MOKA3D kinematics are fit spaxel-by-spaxel.

## Reproducibility

- Data public (paper): JWST/MIRI data public on MAST (doi:10.17909/b4w1-hk44) with zero exclusive access; reduced MIRI cubes at CDS; moment maps on Zenodo (record 17535125); MUSE and ALMA data retrieved from public ESO and ALMA archives.  
  > "The reduced MIRI IFU datacubes used in this work are available at the CDS via anonymous ftp" (Data availability); "The specific observations analyzed can be accessed via doi: <https://doi.org/10.17909/b4w1-hk44>" (Acknowledgements)
- Products in archive: _not stated_
- Code: Python code for JWST/MIRI datacube stitching and flux alignment released on GitHub (https://github.com/matteo-ceci/JWST-MIRI_stitching_code)  
  > "This algorithm, written in Python, is available for download." (Overview of observations and data analysis)
- Missing: Availability and exact configuration scripts for the HOMERUN and MOKA3D modeling codes
- Missing: Exact ALMA uv continuum subtraction channel ranges and tclean stopping criteria
- Data volume (inferred): ~10-50 GB (calibrated ALMA MS for 2016.1.00296.S, archival MUSE cube, and 12 JWST/MIRI MRS datacubes)
- Score (inferred): 78/5, All raw datasets (ALMA, JWST/MIRI, VLT/MUSE) and reduced MIRI cubes/moment maps are publicly archived, the MIRI stitching script is on GitHub, and key imaging, fitting, and photoionization grid parameters are well documented, though HOMERUN and MOKA3D codes are not publicly linked.
- Rediscovery candidate: yes, Public archival data across ALMA, JWST, and VLT with clear quantitative benchmarks (nuclear coordinates, emission line fluxes in 60 lines, PyNeb electron densities, and outflow masses/velocities).

## Links

- Method: (cite: Marconi+2024) (Developed the HOMERUN multicloud photoionization modeling framework used to fit the 60 optical and mid-IR emission lines)
- Method: (cite: Marconcini2023) (Developed the MOKA3D 3D multicloud kinematic modeling tool used to derive intrinsic outflow velocities and geometry)
- Method: (cite: Feltre+23) (Proposed the mid-IR emission line diagnostic diagrams and AGN photoionization grids used for resolved excitation analysis)
- Method: (cite: Carniani2015) (Standard analytical formalism used to compute classical [Ne V] and [O III] ionized outflow masses)
- Companion: (cite: MIRACLE_NGC424) (MIRACLE Paper I providing the detailed description of the JWST/MIRI MRS data reduction and PSF deconvolution methodology)
- Related: MIRACLE (Mid-IR Activity of Circumnuclear Line Emission, JWST GO 6138)
- Related: MAGNUM (Measuring AGN Under MUSE)
- Related: PHANGS (Physics at High Angular resolution in Nearby GalaxieS)

## Checks

```json
{
 "quotes": 141,
 "quotes_ok": 141,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 19,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 73,
  "rate": 0.76
 },
 "evidence_ok": true
}
```
