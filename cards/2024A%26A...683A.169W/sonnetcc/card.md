# JWST discovers an AGN ionization cone but only weak radiatively driven feedback in a powerful z ≈ 3.5 radio-loud AGN

`2024A&A...683A.169W` | Astronomy and Astrophysics 2024 | first author: Wang, Wuji | arXiv: 2401.02479 | DOI: 10.1051/0004-6361/202348531

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: How do jet and radiative (quasar-mode) feedback affect the warm ionized ISM of the z~3.5 radio-loud AGN 4C+19.71, studied with JWST NIRSpec IFU line-ratio diagnostics and outflow estimates (ALMA Band 8 only locates the dust)  
  > "Finally, we discuss the impact of the jet on the ISM using line-ratio diagnostics and summarize in Section" (Introduction)
- Target **4C+19.71**: coordinates _not stated_; z/distance z = 3.5892 +/- 0.0004  
  > "we use $z=3.5892\pm0.0004$ as determined from atomic carbon, $[C i]$(1-0)" (Introduction); distance from [C I](1-0) systemic redshift from earlier work (cite: Falkendal_2021; kolwa2023)  
  > "we use $z=3.5892\pm0.0004$ as determined from atomic carbon, $[C i]$(1-0)" (Introduction)

## Data provenance

- ALMA projects: 2021.1.00576.S
- bands: Band 8  
  > "We also present the ALMA Band 8 observation of 4C+19.71." (2 4C+19.71, observation and data processing)
- frequencies and spectral setup: archived image at 400.3 GHz (observed frame)  
  > "we use only the archived image at $\nu_{\rm obs}=$400.3 GHz to show the position of the cold dust emission" (2 4C+19.71, observation and data processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam FWHM ~0.2 arcsec  
  > "with $\rm beam_{FWHP}\simeq0.2\ensuremath{''}$ and S/N$\simeq10$" (3.2 Continuum emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: UT 2022 June 17  
  > "This observation was carried out under program ID 2021.1.00576.S (PI: Wuji Wang) on UT 2022 June 17." (2 4C+19.71, observation and data processing)
- pi or archival as stated: PI program (PI: Wuji Wang); only the archived image is used here  
  > "This observation was carried out under program ID 2021.1.00576.S (PI: Wuji Wang) on UT 2022 June 17." (2 4C+19.71, observation and data processing); "we use only the archived image at $\nu_{\rm obs}=$400.3 GHz" (2 4C+19.71, observation and data processing)
- Other facility **JWST NIRSpec IFU (G235H/F170LP), program GO 1970**: Primary data: IFU cube of the rest-frame optical emission lines, observed UT 2022 October 30, 3.7 h on source  
  > "The observation of 4C+19.71 was conducted on UT 2022 October 30 with NIRSpec in IFU mode (cite: Boeker_2022; Jakobsen_2022)." (2 4C+19.71, observation and data processing); "We selected G235H/F170LP as the disperser/filter setup" (2 4C+19.71, observation and data processing); "The total on-source exposure time was 3.7 h." (2 4C+19.71, observation and data processing)
- Other facility **MAST**: Source of the raw JWST data  
  > "We downloaded the raw data from the Mikulski Archive for Space Telescopes (MAST)." (2 4C+19.71, observation and data processing)
- Other facility **HST WFPC2**: Reference image for aligning the NIRSpec WCS  
  > "to the Hubble Space Telescope (*HST*) WFPC2 image and used this new WCS in the following analysis" (2 4C+19.71, observation and data processing)
- Other facility **Gaia DR3**: Astrometric correction of the HST image  
  > "The astrometry of the *HST* image was corrected by cross-matching with *Gaia* DR3 targets" (2 4C+19.71, observation and data processing)
- External data: Systemic redshift z=3.5892 from [C I](1-0)  
  > "we use $z=3.5892\pm0.0004$ as determined from atomic carbon, $[C i]$(1-0)" (Introduction) [from (cite: Falkendal_2021; kolwa2023)]
- External data: Keck spectropolarimetry spectrum of Cygnus A nucleus used for comparison  
  > "Using the spectropolarimeter on the Keck telescope, (cite: Ogle_1997) observed the nebular emission lines of Cygnus A." (4.1 Comparison to Cygnus A) [from (cite: Ogle_1997)]
- External data: HST WFPC2/F702W image of the field  
  > "A previous *HST* image (WFPC2/F702W) indicates other two objects in the NIRSpec IFU FoV (cite: Pentericci_1999)." (3.2 Continuum emission) [from (cite: Pentericci_1999)]
- External data: Dusty radiation-pressure dominated photoionization model grids  
  > "We overlay the (cite: Groves_2004_model) dusty radiation-pressure dominated model grids on the diagnostic diagrams." (4.2 Line ratio diagnostics and ionization mechanisms) [from (cite: Groves_2004_model)]
- External data: Shock+precursor models  
  > "we find a part of them are roughly consistent with the “shock+precursor” models (cite: Allen_2008)" (4.2 Line ratio diagnostics and ionization mechanisms) [from (cite: Allen_2008)]
- External data: Fiducial electron density n_e = 500 cm^-3  
  > "We use the fiducial value $n_{e}=500\,\mathrm{cm^{-3}}$ from (cite: Nesvadba_2017b)." (4.3 Inefficient quasar-driven outflow at nucleus) [from (cite: Nesvadba_2017b)]
- External data: Infrared AGN luminosity L_AGN^IR = 10^10.91 Lsun and conversion factor 6 used to get L_bol  
  > "If we use the infrared AGN luminosity, $L_{\rm AGN}^{\rm IR}=10^{10.91}\,L_{\odot}$, and assume a conversion factor, $\kappa_{\rm AGN}^{\rm bol}=6$" (4.3 Inefficient quasar-driven outflow at nucleus) [from (cite: Drouart_2014; Falkendal_2019)]
- External data: NIRSpec IFU PSF FWHM as function of wavelength  
  > "We mark the full width at half maximum (FWHM) of the PSF constructed in (cite: Vayner_2023Q3D_2)" (2 4C+19.71, observation and data processing) [from (cite: Vayner_2023Q3D_2)]
- Simulation/model as data: Groves et al. 2Zsun and 0.5Zsun dusty radiation-pressure photoionization grids and Allen et al. shock+precursor models overlaid on line-ratio diagrams, not fitted quantitatively  
  > "The goal is not to perform a quantitative comparison, but rather to test which parameter(s) could be responsible for the line ratio differences." (4.2 Line ratio diagnostics and ionization mechanisms)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Only the archived ALMA image at 400.3 GHz is used  
  > "we use only the archived image at $\nu_{\rm obs}=$400.3 GHz to show the position of the cold dust emission" (2 4C+19.71, observation and data processing)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- JWST NIRSpec IFU processing follows the procedure of the cited work, with the emsm cube build and a reproject-based combination script  
  > "Our procedure is similar to (cite: Vayner_2023Q3D), executing the standard first and second stages of the pipeline with one modification." (2 4C+19.71, observation and data processing); "We instead used the script from (cite: Vayner_2023Q3D), who applied the Python package `reproject`" (2 4C+19.71, observation and data processing) [from (cite: Vayner_2023Q3D)]
- Gaussian component fitting with shared centroid and width per component  
  > "The centroid (width) of each corresponding Gaussian component is set to be the same (cite: Vayner_2023Q3D)." (B Emission line list) [from (cite: Vayner_2023Q3D)]
- Extinction map from Halpha/Hbeta with Calzetti law and intrinsic ratio 3.1  
  > "The map is constructed using an intrinsic flux ratio of 3.1 assuming Case B recombination in AGN ionization and a (cite: Calzetti_2000) extinction law following (cite: Vayner_2023Q3D)." (4.2 Line ratio diagnostics and ionization mechanisms) [from (cite: Vayner_2023Q3D)]
- Ionized outflow mass, rate, momentum and kinetic luminosity equations and assumptions (T_e, emissivity)  
  > "We follow (cite: Vayner_2023Q3D_2) and use the following equation to calculate the ionized outflow gas mass" (4.3 Inefficient quasar-driven outflow at nucleus); "we use the value of $2\times 10^{-25} \mathrm{erg\, cm^3\,s^{-1}}$ for $T_{e}\simeq15\,000\,$K (cite: Vayner_2023Q3D_2)" (4.3 Inefficient quasar-driven outflow at nucleus) [from (cite: Vayner_2023Q3D_2; Osterbrock_2006)]
- Detailed ALMA analysis deferred to a forthcoming paper  
  > "A detailed analysis of the ALMA observations is beyond the scope of this paper and will be presented in a forthcoming paper." (2 4C+19.71, observation and data processing) [from forthcoming paper on the ALMA observations (not cited)]

### Not stated but needed to reproduce (our reading)

- Which ALMA archive product (pipeline continuum image, version, calibration/imaging parameters) provided the 400.3 GHz image, its rms and the beam parameters
- ALMA continuum peak flux density and S/N (only S/N~10 and beam ~0.2 arcsec are given)
- q3dfit configuration: initial guesses, line-width and velocity bounds, continuum model per spaxel, how spaxel fits were visually selected
- Exact aperture position on the sky and rule for aligning the aperture with the brightest [O III] blob
- Radiative-transfer or grid parameters (alpha, U) for the Groves model tracks as drawn, and the shock model magnetic parameters
- How the foreground galaxy G1 centroid and HST centroid were fitted beyond 2D Gaussian (box size, filters)
- Sigma_v value used in v_ion for each component (derived from FWHM but not tabulated)

## Analysis recipe

1. **reduce NIRSpec IFU data to a combined cube**: JWST pipeline stages 1 and 2 with emsm cube build, then combine exposures with the reproject-based script with 2-sigma clipping  
  > "The data were processed with the *JWST* Science Calibration pipeline[^1] (v1.9.4) with the Calibration Reference Data System (CRDS) context file jwst_1041.pmap." (2 4C+19.71, observation and data processing); "to reduce the low-frequency ripples due to undersampling" (2 4C+19.71, observation and data processing)
   - software: jwst pipeline, reproject
   - parameter: sigma clipping 2 sigma when combining cubes  
  > "During this step, sigma clipping ($2\sigma$) was also included to reject outliers." (2 4C+19.71, observation and data processing)
   - parameter: pixel scale 0.05 arcsec  
  > "The data cube was resampled to have a pixel scale of 0.05$''$." (2 4C+19.71, observation and data processing)
   - parameter: standard star TYC 4433-1800-1 (PID 1128) used for flux calibration  
  > "We processed the raw NIRSpec IFU data of the standard star TYC 4433-1800-1 (PID 1128) for flux calibration." (2 4C+19.71, observation and data processing)
   - fitting: _not stated_
   - validation: _not stated_
2. **correct NIRSpec WCS using HST**: Align the continuum position of the west foreground galaxy G1 in the cube to the Gaia-corrected HST WFPC2 image by matching 2D Gaussian centroids  
  > "We aligned the continuum emission position of the west foreground galaxy in our NIRSpec cube to the Hubble Space Telescope (*HST*) WFPC2 image and used this new WCS in the following analysis" (2 4C+19.71, observation and data processing); "This was done by matching the centroids of the fitted 2D Gaussian profile." (A Astrometric correction)
   - software: pysiaf
   - parameter: final shift dRA = 0.43 arcsec, dDec = -0.22 arcsec relative to pipeline WCS  
  > "Our final WCS solution resulted in a shift of $\Delta$RA$=0.43\ensuremath{''}$ and $\Delta$Dec$=-0.22\ensuremath{''}$ compared to the pipeline output WCS." (2 4C+19.71, observation and data processing)
   - fitting: _not stated_
   - validation: Extinction peak coincides with ALMA dust; also compared with pysiaf-based corrections  
  > "This spatial coincidence also validates our manual astrometry correction based on foreground galaxy" (4.2 Line ratio diagnostics and ionization mechanisms)
3. **locate the ALMA dust continuum and its position uncertainty**: Overlay the archived ALMA Band 8 image on the IFU maps; position uncertainty from beam/(S/N)/0.9  
  > "We overlay in Fig. [1](#fig:IFU+spec)b the continuum emission detected in our ALMA Band 8 observation" (3.2 Continuum emission); "is estimated using $\mathrm{pos_{acc}=beam_{FWHP}/(S/N)/0.9}$ with $\rm beam_{FWHP}\simeq0.2\ensuremath{''}$ and S/N$\simeq10$" (3.2 Continuum emission)
   - assumption: ALMA continuum assumed to trace cold dust heated by newly formed stars  
  > "which likely indicates the location of the cold dust emission heated by the newly formed stellar population" (3.2 Continuum emission)
   - fitting: _not stated_
   - validation: AGN position from NIRSpec continuum agrees with ALMA dust position within uncertainties  
  > "agrees with the ALMA dust location within their uncertainties" (3.2 Continuum emission)
4. **extract and fit the nuclear 1D spectrum**: Sum a 0.2x0.2 arcsec (4x4 pix) aperture near the continuum peak and fit with q3dfit using three Gaussian kinematic components  
  > "We extracted a spectrum from a $0.2\ensuremath{''}\times0.2\ensuremath{''}$ or $1.4\times1.4\,\mathrm{kpc}^{2}$ ($4\times4$ pix$^{2}$) square aperture near the position of the continuum emission peak." (3.3 Emission line identification); "We fitted the spectrum with `q3dfit`. We used three kinematic components." (3.3 Emission line identification)
   - software: q3dfit
   - parameter: continuum: third-order polynomial; lines with S/N>10 fitted with Gaussians; max three components  
  > "The continuum is modeled by a third order polynomial and the emission lines (S/N$>10$) are fitted with Gaussian profiles." (B Emission line list); "We set the maximum number of the Gaussian components to be three for the fit." (B Emission line list)
   - parameter: [O II] 3726,3729 flux ratio fixed 1:1; 3-sigma upper limits for low S/N lines  
  > "For the doublet $[O ii]3726,3729$, we set the flux ratio to be $1:1$ and report the summation since they are spectrally unresolved." (B Emission line list)
   - fitting: q3dfit Gaussian fit; uncertainties are the direct 1 sigma output of q3dfit  
  > "The reported uncertainty is the direct $1\sigma$ output of `q3dfit`." (Table 4 caption)
   - validation: _not stated_
5. **build line-ratio maps and diagnostic diagrams**: Fit the cube per spaxel with q3dfit, with 3, 2 and 1 as the maximum number of Gaussians, choose best fit by visual inspection, and compare ratios to model grids and Kewley 2006 classification  
  > "Following (cite: Vayner_2023Q3D), we ran the fit with 3, 2 and 1 as the maximum number allowed Gaussian components. We performed a visual inspection to determine the best fit for each spaxel." (4.2 Line ratio diagnostics and ionization mechanisms)
   - software: q3dfit
   - parameter: fitted region from [O III] narrow-band image with S/N > 5  
  > "The fitted region was selected based on the \[O iii\] narrow-band image with a S/N cut of $>5$" (4.2 Line ratio diagnostics and ionization mechanisms)
   - parameter: lines fitted simultaneously with the same velocity shift and width per component  
  > "These lines are fitted simultaneously with the same velocity shift and line width for the corresponding components (cite: Zakamska_2016b)." (4.2 Line ratio diagnostics and ionization mechanisms)
   - parameter: shock models: pre-shock density 100 cm^-3, v_shock >= 200 km/s  
  > "We choose the models with pre-shock number density, $n=100\,\mathrm{cm^{-3}}$ (cite: DeBreuck_2000)." (4.2 Line ratio diagnostics and ionization mechanisms)
   - assumption: 2 Zsun Groves model grids chosen as indicated by [N II]/Halpha  
  > "We chose the $2Z_{\odot}$ models (black) as indicated by the $[N ii]/\mathrm{H\alpha}$ ratios" (4.2 Line ratio diagnostics and ionization mechanisms)
   - fitting: _not stated_
   - validation: _not stated_
6. **map dust attenuation and correct line ratios**: E(B-V) map from fitted Halpha/Hbeta ratio; line ratio maps dust-corrected with it  
  > "The line ratios shown in Fig. [4](#fig:q3dfit_line_ratio_map)bc are corrected for the dust attenuation based on this $E(B-V)$ map." (4.2 Line ratio diagnostics and ionization mechanisms)
   - assumption: intrinsic Halpha/Hbeta = 3.1 (Case B), Calzetti extinction law  
  > "The map is constructed using an intrinsic flux ratio of 3.1 assuming Case B recombination in AGN ionization and a (cite: Calzetti_2000) extinction law following (cite: Vayner_2023Q3D)." (4.2 Line ratio diagnostics and ionization mechanisms)
   - fitting: _not stated_
   - validation: High E(B-V) coincides with ALMA dust continuum  
  > "coincident with our ALMA dust continuum (pink contours in Fig. [4](#fig:q3dfit_line_ratio_map)a)" (4.2 Line ratio diagnostics and ionization mechanisms)
7. **estimate ionized outflow mass, rate, energetics and coupling efficiency**: Red and blue components of the nuclear spectrum taken as outflowing clouds; M_ion from Halpha luminosity, Mdot = M v / dR, momentum flux and kinetic luminosity, efficiency = L_kin / L_bol  
  > "we focus on the red and blue components (Table [1](#tab:1Demission_kine) and [4](#tab:emissionline)) and assume them to be the redshifted and blueshifted outflow clouds" (4.3 Inefficient quasar-driven outflow at nucleus); "We report the summation of the red and blue components as the estimated total outflow rate." (4.3 Inefficient quasar-driven outflow at nucleus)
   - parameter: dR = half of the extraction aperture size, 0.7 kpc  
  > "For the distance $\Delta R$, we use half of the physical size of the extraction aperture, $0.7\,$kpc." (4.3 Inefficient quasar-driven outflow at nucleus)
   - parameter: v_ion = |dv| + sigma_v  
  > "For the velocity, we use the $v_{\rm ion} = |\Delta v|+\sigma_{v}$ (cite: Rupke_2013; Vayner_2023Q3D_2)." (4.3 Inefficient quasar-driven outflow at nucleus)
   - assumption: T_e ~ 15000 K  
  > "We assume an electron temperature $T_{e}\simeq15\,000\,$K" (4.3 Inefficient quasar-driven outflow at nucleus)
   - assumption: n_e = 500 cm^-3 fiducial  
  > "We use the fiducial value $n_{e}=500\,\mathrm{cm^{-3}}$ from (cite: Nesvadba_2017b)." (4.3 Inefficient quasar-driven outflow at nucleus)
   - assumption: L_bol from infrared AGN luminosity with conversion factor 6  
  > "the bolometric luminosity of 4C+19.71 is estimated to be $L_{\rm bol}\sim2.5\times10^{47}\,\mathrm{erg\,s^{-1}}$" (4.3 Inefficient quasar-driven outflow at nucleus)
   - fitting: _not stated_
   - validation: Sensitivity checked by using n_e from the observed [S II] ratio (efficiency becomes ~1e-7) and by raising the speed by a factor of three  
  > "If we nevertheless use $n_{e}$ based on our estimation, the radiative coupling efficiency becomes $\sim10^{-7}$" (E Estimation of electron density)

## Software

- **JWST Science Calibration pipeline** v1.9.4: Stages 1 and 2 processing of NIRSpec IFU raw data, CRDS context jwst_1041.pmap  
  > "The data were processed with the *JWST* Science Calibration pipeline[^1] (v1.9.4) with the Calibration Reference Data System (CRDS) context file jwst_1041.pmap." (2 4C+19.71, observation and data processing)
- **reproject** : Combining exposure cubes into the final cube (script from Vayner et al.)  
  > "We instead used the script from (cite: Vayner_2023Q3D), who applied the Python package `reproject`" (2 4C+19.71, observation and data processing)
- **q3dfit** : Fitting emission lines in per-spaxel and 1D spectra  
  > "The per-spatial-pixel (spaxel) spectra are fitted using `q3dfit` (cite: Rupke_2023q3dfit)" (3.1 Morphology of the extended ionized nebula)
- **IFSFIT** : Software on which q3dfit is based  
  > "which is a Python tool for analyzing *JWST* IFU data based on the software `IFSFIT`" (3.1 Morphology of the extended ionized nebula)
- **pysiaf** : Projecting the NIRSpec V2/V3 offset to RA/Dec when testing WCS corrections  
  > "This offset projection to sky (RA, Dec) coordinates could then be calculated using `pysiaf` by assuming the targeted RA and Dec of the IFU pointing is correct." (A Astrometric correction)
- **matplotlib** : Named in acknowledgements; specific use not stated  
  > "`matplotlib` (cite: Hunter_2007); `SciPy` (cite: virtanen2020scipy); `NumPy` (cite: harris2020numpy); `Astropy` (cite: Astropy_2018); `LMFIT` (cite: newville2016)." (Acknowledgements)
- **SciPy** : Named in acknowledgements; specific use not stated  
  > "`matplotlib` (cite: Hunter_2007); `SciPy` (cite: virtanen2020scipy); `NumPy` (cite: harris2020numpy); `Astropy` (cite: Astropy_2018); `LMFIT` (cite: newville2016)." (Acknowledgements)
- **NumPy** : Named in acknowledgements; specific use not stated  
  > "`matplotlib` (cite: Hunter_2007); `SciPy` (cite: virtanen2020scipy); `NumPy` (cite: harris2020numpy); `Astropy` (cite: Astropy_2018); `LMFIT` (cite: newville2016)." (Acknowledgements)
- **Astropy** : Named in acknowledgements; specific use not stated  
  > "`matplotlib` (cite: Hunter_2007); `SciPy` (cite: virtanen2020scipy); `NumPy` (cite: harris2020numpy); `Astropy` (cite: Astropy_2018); `LMFIT` (cite: newville2016)." (Acknowledgements)
- **LMFIT** : Named in acknowledgements; specific use not stated  
  > "`matplotlib` (cite: Hunter_2007); `SciPy` (cite: virtanen2020scipy); `NumPy` (cite: harris2020numpy); `Astropy` (cite: Astropy_2018); `LMFIT` (cite: newville2016)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1 sigma ALMA Band 8 dust position uncertainty | ~0.02 | not stated | arcsec | 3 | The $1\sigma$ uncertainty, $\sim0.02\ensuremath{''}$, of the ALMA dust position is estimated using |
| WCS shift applied to the NIRSpec cube (dRA, dDec) | 0.43, -0.22 | not stated | arcsec | 2 | Our final WCS solution resulted in a shift of $\Delta$RA$=0.43\ensuremath{''}$ and $\Delta$Dec$=-0.22\ensuremath{''}$ compared to the pipeline output WCS. |
| Velocity shift of central, red, blue components at nucleus | 238, 572, -148 | 10, 30, 20 | km/s | 4 | 238$\pm10$ / 572$\pm30$ / -148$\pm20$ |
| FWHM of central, red, blue components at nucleus | 445, 412, 1669 | 10, 30, 20 | km/s | 4 | 445$\pm10$ / 412$\pm30$ / 1669$\pm20$ |
| Number of emission lines (doublets) identified with S/N>3 | ~24 | not stated | dimensionless | 4 | We identify $\sim24$ emission lines (doublets) with S/N$>3$. |
| E(B-V) around the AGN position | ~1 | not stated | mag | 6 | We find that there is a dusty region with high $E(B-V)$$\sim1$ around the AGN position |
| Outflow velocities of red and blue components relative to central | 334, -386 | not stated | km/s | 7 | $\Delta v_{\rm red}=334\,\mathrm{km\,s^{-1}}$ and $\Delta v_{\rm blue}=-386\,\mathrm{km\,s^{-1}}$ |
| Ionized outflow mass (red, blue) | 1e5, 1e6 | not stated | Msun | 7 | we find $M_{\rm ion} = 10^5$ and $10^6$ M$_\odot$  for the red and blue components, respectively. |
| Total ionized outflow rate | 2 | not stated | Msun/yr | 7 | This gives a total $\dot{M}_{\rm ion}$ of $2\,\mathrm{M_{\odot}\,yr^{-1}}$. |
| Outflow momentum flux and kinetic luminosity | 1.5e34 dyne, 8.0e41 erg/s | not stated | dyne; erg/s | 7 | We calculate values for $\dot{P}_{\rm ion}^{\text {outflow }}$ and $L_{\rm ion}^{\text{kinetic}}$ of $1.5\times10^{34}\,\mathrm{dyne}$ and $8.0\times10^{41}\,\mathrm{erg\,s^{-1}}$, respectively. |
| Bolometric luminosity of 4C+19.71 | ~2.5e47 | not stated | erg/s | 7 | the bolometric luminosity of 4C+19.71 is estimated to be $L_{\rm bol}\sim2.5\times10^{47}\,\mathrm{erg\,s^{-1}}$ |
| Radiative coupling efficiency L_kin/L_bol (fiducial n_e) | ~1e-5 | not stated | dimensionless | 7 | is $\sim 10^{-5}$ |
| Radiative coupling efficiency using observed [S II]-based n_e | ~1e-7 | not stated | dimensionless | 7 | the radiative coupling efficiency becomes $\sim10^{-7}$ |
| [O III] flux-weighted redshift of low-velocity components | 3.5908 | 0.0017 | dimensionless | 5 | The redshift is $z_{[O III]}=3.5908\pm0.0017$ which corresponds to $108\pm114\,\mathrm{km\,s^{-1}}$ |
| Electron density of the central component from [S II] | ~800 | not stated | cm^-3 | 4 | $n_{e}$ of the central component is $\sim800\,\mathrm{cm^{-3}}$ |
| Dynamical mass of the southern high-velocity region (rotating-disk assumption) | ~2e11 | not stated | Msun | 5 | this would imply a dynamical mass of $\sim2\times 10^{11}\,\mathrm{M_{\odot}}$ |

## Qualitative findings

- Line-ratio diagnostics show the inner ionized ISM is dominated by photoionization from the hidden AGN, with a possible contribution from shocks in the north and east  
  > "Our results show that the inner part of the ionized ISM in the $z\sim3.5$ radio-loud AGN is dominated by photons from the hidden AGN with potential evidence for shock ionization." (4.2 Line ratio diagnostics and ionization mechanisms)
- The nuclear spectrum resembles that of Cygnus A and is dominated by the (possibly scattered) light of the hidden AGN  
  > "the spectrum is dominated by the (possibly scattered) light of the hidden AGN" (4.1 Comparison to Cygnus A)
- NIRSpec position of the AGN continuum agrees with the ALMA Band 8 dust position within uncertainties  
  > "agrees with the ALMA dust location within their uncertainties" (3.2 Continuum emission)

## Claim tuples

- H: What powers the ionization of the ISM within ~30 kpc of the hidden quasar in 4C+19.71 | E: Line-ratio maps and diagnostic diagrams from q3dfit fits compared with Groves photoionization grids, Kewley 2006 classification and Allen shock models | R: Most spaxels fall in the AGN-photoionized region, with higher U along the north-south cone than in the east-west region; some north and east spaxels are consistent with shock+precursor models | F: AGN photoionization dominates, structured as an ionization cone along the jet axis, with possible shock ionization | **supported**
- H: How efficiently is the radiatively driven (quasar-mode) outflow coupled to the AGN at the nucleus | E: Red and blue components of the 1D nuclear spectrum converted into ionized outflow mass, rate and kinetic luminosity, divided by L_bol | R: Mdot ~2 Msun/yr, L_kin ~8.0e41 erg/s, L_kin/L_bol ~1e-5 | F: The radiative coupling is very inefficient, lower than most reported cases | **supported**
- H: Which feedback mode (jet or radiation) drives the outflow in this HzRG | E: Compared the small-scale NIRSpec energetics with larger-scale SINFONI jet-driven values from earlier work | R: NIRSpec-based efficiency is ~2 to 3 dex lower than the jet kinetic coupling on larger scales | F: Mechanical jet feedback leads, acting in the radio lobes beyond the galactic scale; this rests on literature comparison and a limited FoV | **partially**
- H: Is there dust near the AGN that is traced by both Balmer decrement and ALMA continuum | E: E(B-V) map from Halpha/Hbeta compared with the ALMA Band 8 continuum position | R: High E(B-V) ~1 around the AGN position coincides with the ALMA dust continuum | F: Dust is important for extinction near the AGN, and the manual WCS correction is validated | **supported**

## Reasoning

- Why this data: Targets chosen with similar redshifts to cover many emission lines in one NIRSpec setting  
  > "We selected them to have similar redshifts ($z\simeq3.5$) to maximize the number of emission lines in a single observational setting." (2 4C+19.71, observation and data processing)
- Why this method: Custom cube combination used because the pipeline third stage rejects the bright emission peak  
  > "because the third stage of the pipeline falsely rejects the bright emission peak while keeping some noise spikes" (2 4C+19.71, observation and data processing)
- Alternative: Pipeline-based WCS corrections (Correction1, Correction2 variants) were tested but the manual HST-based alignment was kept because the direction of the offset is not well understood  
  > "Since the direction of the error is not well-understood, we use the manual match in this paper." (A Astrometric correction)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data are used only for a dust position; detailed ALMA analysis deferred  
  > "A detailed analysis of the ALMA observations is beyond the scope of this paper and will be presented in a forthcoming paper." (2 4C+19.71, observation and data processing)
- Limitation (authors): NIRSpec FoV is only sensitive to central clumps, not extended diffuse emission or the jet hot spots  
  > "Our NIRSpec IFU data is only sensitive to the central clumps, $\lesssim20\,$kpc, but not to extended diffuse emission." (4.3 Inefficient quasar-driven outflow at nucleus)
- Limitation (authors): Outflow mass is uncertain because it scales inversely with n_e  
  > "One of the main uncertainties is the estimation of $M_{\text {ion}}$, which is inversely proportional to $n_{e}$." (4.3 Inefficient quasar-driven outflow at nucleus)
- Limitation (authors): The systemic redshift from [C I] is uncertain because of the large ALMA beam and faint flux  
  > "Given its relatively faint flux and large observed beam size, it is unclear whether this traces the “authentic” redshift of the host galaxy." (D Systemic redshift based on ionized gas)
- Caveat (inferred, ours): Outflow identification rests on two Gaussian components in one 0.2 arcsec aperture; red/blue components could be non-outflow kinematics, and no uncertainties are propagated on the efficiency
- Caveat (inferred, ours): Fiducial n_e = 500 cm^-3 differs by up to two orders of magnitude from the [S II]-derived value, so the efficiency is only an order-of-magnitude estimate
- Caveat (inferred, ours): The conclusion that jet feedback dominates relies on comparison with SINFONI results at larger scales rather than a matched measurement
- Caveat (inferred, ours): Line-ratio model comparison is qualitative and the shock-model identification is acknowledged as non-decisive
- Caveat (inferred, ours): The ALMA part cannot be checked: no flux, rms or imaging details are given

## Reproducibility

- Data public (paper): JWST raw data downloaded from MAST; ALMA image taken from the archive  
  > "We downloaded the raw data from the Mikulski Archive for Space Telescopes (MAST)." (2 4C+19.71, observation and data processing); "we use only the archived image at $\nu_{\rm obs}=$400.3 GHz" (2 4C+19.71, observation and data processing)
- Products in archive: Archived ALMA image used  
  > "we use only the archived image at $\nu_{\rm obs}=$400.3 GHz to show the position of the cold dust emission" (2 4C+19.71, observation and data processing)
- Missing: ALMA image product identity, rms and beam
- Missing: q3dfit configuration files and per-spaxel fit selection (done by visual inspection)
- Missing: Exact astrometric alignment procedure scripts
- Missing: sigma_v values used for v_ion
- Data volume (inferred): ALMA: one archived Band 8 continuum image (small, well under 1 GB); JWST: raw NIRSpec IFU exposures of one program (order of a few GB)
- Score (inferred): 3/5, JWST data are public in MAST with a stated pipeline version and CRDS context, and the outflow chain gives equations and numbers; but q3dfit settings are unstated, spaxel fits were visually selected, and the ALMA product is not specified.
- Rediscovery candidate: no, ALMA plays a minor role (a dust position overlay), and the JWST fitting recipe lacks enough settings and relies on visual selection.

## Links

- Method: (cite: Vayner_2023Q3D) (NIRSpec IFU processing, reproject combination script, fitting approach and extinction recipe followed)
- Method: (cite: Rupke_2023q3dfit) (q3dfit software used for all line fits)
- Method: (cite: Vayner_2023Q3D_2) (Outflow mass, rate and energetics equations and assumptions, and NIRSpec PSF)
- Companion: (cite: kolwa2023) ([C I](1-0) systemic redshift and molecular gas in the host)
- Companion: (cite: Falkendal_2021) (Earlier ALMA [C I] observation and Lyman-alpha nebula of the target)
- Companion: (cite: Nesvadba_2017b) (SINFONI kinematics and fiducial n_e used for the outflow comparison)
- Companion: (cite: wang2023) (Companion study of HzRG gas around this class of targets)
- Related: JWST Cycle 1 GO program 1970 (PI: Wuji Wang), four HzRGs
- Related: ALMA 2021.1.00576.S (PI: Wuji Wang)

## Checks

```json
{
 "quotes": 113,
 "quotes_ok": 113,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 78,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
