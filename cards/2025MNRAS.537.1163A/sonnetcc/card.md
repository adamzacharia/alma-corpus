# The onset of bar formation in a massive galaxy at z ~ 3.8

`2025MNRAS.537.1163A` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Amvrosiadis, A. | arXiv: 2404.01918 | DOI: 10.1093/mnras/staf048

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Morphology and kinematics of the strongly lensed massive dusty star-forming galaxy SPT at z = 3.762: is there a bar and a rotating disc, and how baryon dominated is it  
  > "We examine the morphological and kinematical properties of SPT, a strongly lensed, massive, dusty, star-forming galaxy at $z = 3.762$." (abstract); "The kinematics confirm the presence of the bar and of the regularly rotating disc." (abstract)
- Target **SPT (SPT-2147)**: coordinates _not stated_; z/distance z = 3.762 (source); lens z = 0.84  
  > "SPT, a $z = 3.762$, massive DSFG, strongly lensed by a, z = 0.84, early-type galaxy (ETG)" (1 Introduction); "SPT was originally discovered in the South Pole Telescope (SPT) survey" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01060.S, 2019.1.00471.S
- bands: Band 8 continuum (2019.1.00471); [CII], CO(7-6), [CI](2-1) from 2018.1.01060.S (band not stated)  
  > "These data come from proposal 2019.1.00471, and achieve a resolution of $\sim0.1\,\mathrm{arcsec}$ in band 8." (2.1.3 ALMA)
- frequencies and spectral setup: [CII] velocity resolution ~6 km/s (reconstructed in ~30 km/s channels)  
  > "and was observed at higher velocity resolution, $\sim 6$ $\rm km \, s^{-1}$ instead of $\sim 100$ $\rm km \, s^{-1}$ for the H$\alpha$ cube" (4.2 Kinematics)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: continuum taken in different antenna configurations (specific configurations not stated)  
  > "Continuum observations were taken using different antenna configurations, leading to different resolutions." (2.1.3 ALMA)
- baselines: _not stated_
- angular resolution: ~0.1 arcsec (band 8 continuum); ~0.25 arcsec ([CII])  
  > "These data come from proposal 2019.1.00471, and achieve a resolution of $\sim0.1\,\mathrm{arcsec}$ in band 8." (2.1.3 ALMA); "The \[Cii\] emission line observations were carried out as part of proposal 2018.1.01060.S and achieve a resolution of $\sim0.25\,\mathrm{arcsec}$." (2.1.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA data  
  > "Our datasets, which come from a variety of instruments (newly obtained from JWST and archival from HST and ALMA), trace different components of the galaxy" (Conclusions)
- Line: [CII] [CII] (transition not further specified) (not stated)
- Line: CO 7-6 (not stated)
- Line: [CI] 2-1 (not stated)
- Other facility **JWST (NIRCam, MIRI, NIRSpec; TEMPLATES ERS program ID 1355)**: Stellar continuum images (NIRCam F200W-F444W, MIRI F560W-F2100W) and NIRSpec IFU Halpha map; archival, default pipeline reduction  
  > "We use the archival data, which were reduced with the default pipeline." (2.1.1 JWST)
- Other facility **HST WFC3 F140W**: Rest-frame UV image; background source too faint (SNR_peak ~3) so not used in the analysis  
  > "Therefore, we will not use these data for the rest of this work." (2.1.2 HST)
- Other facility **Herschel, LABOCA, SPT**: Unresolved sub-mm fluxes used in the SED fit  
  > "since some of our observations, specifically in the sub-mm regime (from Herschel, LABOCA and SPT), do not resolve the source" (2.2.1 SED fitting)
- External data: CO(2-1) line luminosity L_CO(2-1) = (1.6 +/- 0.3)e11 K km/s pc^2 (previous observations of SPT)  
  > "observations of the CO(2$-$1) emission line have previously been obtained for SPT (cite: 2016MNRAS.457.4406A; 2022A&A...663A..22G)" (2.2.2 Gas mass) [from (cite: 2016MNRAS.457.4406A; 2022A&A...663A..22G)]
- External data: CO(2-1)/CO(1-0) line ratio r21 = 0.84 +/- 0.13  
  > "for which we adopt the value $r_{21} = 0.84 \pm 0.13$ (cite: 2013MNRAS.429.3047B)" (2.2.2 Gas mass) [from (cite: 2013MNRAS.429.3047B)]
- External data: CO-H2 conversion factor alpha_CO = 1.0  
  > "for which we adopt the value, $\alpha_{\rm CO} = 1.0$ (cite: 2021MNRAS.501.3926B)" (2.2.2 Gas mass) [from (cite: 2021MNRAS.501.3926B)]
- External data: Previously measured far-infrared/submm fluxes used in the SED fit (Herschel, LABOCA, SPT); individual citations not given  
  > "as well as previously measured fluxes at far-infrared/submm wavelengths" (Conclusions) [from not stated]
- External data: Earlier dynamical mass Mdyn = (25 +/- 4)e10 Msun from lower-resolution CO(7-6), used for comparison  
  > "This value is smaller than the value reported by (cite: 2022A&A...663A..22G)" (4.2.1 Dynamical modelling) [from (cite: 2022A&A...663A..22G)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "We calibrate the data using the ALMA pipeline in the Common Astronomy Software Applications package (cite: 2007ASPC..376..127M)." (2.1.3 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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

- Phases of the PyAutoLens lens-modelling pipeline (SIS+shear then pixelated source, priors passed between phases)  
  > "have been described in previous papers that make use of the same software (cite: 2022MNRAS.517.3275E; 2022RAA....22b5014C), and are the same steps that we take in this work." (3 Strong Lensing Analysis) [from (cite: 2022MNRAS.517.3275E; 2022RAA....22b5014C)]
- Final imaging phase uses an MGE lens-light model  
  > "the final phase of our imaging pipeline uses an MGE model for the lens galaxy light instead of a Sérsic profile (cite: 2024arXiv240316253H)" (3.2.2 Pipeline) [from (cite: 2024arXiv240316253H)]
- Voronoi mesh source reconstruction with regularization  
  > "The lensing-corrected source surface brightness distribution is reconstructed on an irregular Voronoi mesh (cite: 2015MNRAS.452.2940N)." (3.2.1 Background source) [from (cite: 2015MNRAS.452.2940N)]
- Bar criteria and ellipse-fitting approach  
  > "Similarly to (cite: 2023ApJ...945L..10G), we apply an ellipse fitting technique to the reconstructed F444W, F1280W and \[Cii\] emission line distributions." (5.1 Bars) [from (cite: 2023ApJ...945L..10G)]
- SED modelling approach (MAGPHYS high-z version)  
  > "we perform SED modelling using the high-redshift version of the publicly available software magphys (cite: 2015ApJ...806..110D; 2019ApJ...882...61B)" (2.2.1 SED fitting) [from (cite: 2015ApJ...806..110D; 2019ApJ...882...61B)]
- Asymmetric drift correction in 3DBarolo  
  > "by enabling the asymmetric drift correction functionality (cite: 2007ApJ...657..773V)" (4.2.1 Dynamical modelling) [from (cite: 2007ApJ...657..773V)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and pipeline version, and any manual flagging or reprocessing
- Which ALMA execution blocks / measurement sets are used for the band 8 continuum and [CII] data
- Rest frequencies and band/spectral windows for [CII], CO(7-6), [CI](2-1)
- tclean settings (weighting, robust, cell, image size, deconvolver, masks) for the visualization images
- Continuum subtraction and line-free channels for the [CII] cube
- Visibility binning/averaging and uv weighting used for the uv-plane lens reconstruction
- Magnification values (mean and per tracer) and source-plane pixel counts of the Voronoi mesh
- Priors, nested sampler settings (dynesty is only listed in the software citations) and regularization coefficient values
- Which pixel/bins define the radial profile averages and the common centre coordinates
- Number of rings (nradii) used in 3DBarolo (left blank in the config table)
- Photutils ellipse fitting parameters (step, minimum SMA, sigma clipping)
- Source coordinates of SPT-2147 and the origin of the redshift
- Photometry table used in the SED fit, including the magnification-correction steps for LIR/SFR/M*

## Analysis recipe

1. **Calibrate ALMA data and make visualization images**: ALMA pipeline calibration in CASA; cleaned images made only for visualization  
  > "We calibrate the data using the ALMA pipeline in the Common Astronomy Software Applications package (cite: 2007ASPC..376..127M)." (2.1.3 ALMA); "For visualization purposes we produce cleaned images of both the dust continuum and \[Cii\] line emission" (2.1.3 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Prepare JWST images and Halpha map**: Subtract a constant background from each NIRCam/MIRI image (Gaussian fit to the pixel flux histogram below the peak); NIRSpec cube continuum-subtracted with a 2nd-order polynomial, then Halpha+[NII] deblended with 3 Gaussians per pixel  
  > "To estimate this background we fit a Gaussian function to the distribution of all pixel fluxes and subtract the best-fitting mean value from each image." (2.1.1 JWST); "we fit a model consisting of three Gaussian profiles to each individual pixel of the observed cube" (2.1.1 JWST)
   - parameter: Continuum fit only in a window around Halpha (3.0 to 3.3 micron observed) after masking the line  
  > "we only fit the continuum in the frequency range, 3.0 $\mu$m" (2.1.1 JWST)
   - parameter: NII doublet centres fixed relative to Halpha; all three line widths tied  
  > "In addition, we assume that the widths of all three lines are the same" (2.1.1 JWST)
   - fitting: Gaussian line fits per pixel; sampler not stated  
  > "we fit a model consisting of three Gaussian profiles to each individual pixel of the observed cube" (2.1.1 JWST)
   - validation: Data, model and residual moment-0 maps compared (Figure 2)  
  > "From left to right the first three panels show the data, best-fitting model and residuals." (2.1.1 JWST)
3. **Fit the SED for stellar mass, SFR and LIR**: MAGPHYS high-redshift SED fit to fluxes from rest-frame 0.42 micron to ~630 micron, before magnification correction  
  > "we perform SED modelling using the high-redshift version of the publicly available software magphys" (2.2.1 SED fitting); "We note that the SED fitting was performed prior to correcting the observed fluxes for magnification" (2.2.1 SED fitting)
   - software: magphys
   - parameter: Upper limits not used in the fit  
  > "If only upper limits exist in some band these were not used in the fitting process" (2.2.1 SED fitting)
   - assumption: Chabrier IMF; energy balance between UV/optical and IR  
  > "which assumes a Chabrier IMF and employs an energy balance technique whereby all of the UV/optical emission from newly born stars is deemed to be absorbed by dust and re-emitted at infrared wavelengths." (2.2.1 SED fitting)
   - fitting: _not stated_
   - validation: Overall chi2 ~ 3; agreement with previous measurements of LIR, SFR and M*  
  > "The best-fit model provides a good fit to the data across the whole spectrum, with a overall goodness of fit, $\chi^2 \sim 3$." (2.2.1 SED fitting)
4. **Derive molecular gas mass from CO(2-1)**: Mgas = 1.36 alpha_CO r21 L_CO(2-1) using literature CO(2-1) luminosity  
  > "Here we use the CO(2$-$1) emission line luminosity, $L_{\rm CO(2-1)} = (1.6 \pm 0.3) \times 10^{11} {\rm (K \, km \, s^{-1} \, pc^{2})}$, to estimate the molecular gas mass from" (2.2.2 Gas mass)
   - parameter: r21 = 0.84 +/- 0.13  
  > "for which we adopt the value $r_{21} = 0.84 \pm 0.13$ (cite: 2013MNRAS.429.3047B)" (2.2.2 Gas mass)
   - assumption: alpha_CO = 1.0  
  > "for which we adopt the value, $\alpha_{\rm CO} = 1.0$ (cite: 2021MNRAS.501.3926B)" (2.2.2 Gas mass)
   - assumption: Factor 1.36 for helium  
  > "The factor of 1.36 accounts for the abundance of Helium." (2.2.2 Gas mass)
   - fitting: _not stated_
   - validation: Gas fraction f_gas = 0.45 +/- 0.12 compared with previous SMG/DSFG estimates  
  > "which is on the high end but consistent with previous estimates for SMGs/DSFGs (cite: 2021MNRAS.501.3926B)" (2.2.2 Gas mass)
5. **Build the lens mass model from NIRCam F444W**: PyAutoLens: elliptical power-law mass plus external shear fitted to the F444W image; lens light subtracted (MGE in the final phase); phased pipeline starting from SIS+shear  
  > "In order to build a mass model for the lensing galaxy we choose the F444W filter image from JWST/NIRCam." (3 Strong Lensing Analysis); "For the mass distribution of the lensing galaxy we consider an elliptical power-law model (EPL) with an external shear." (3.2 Foreground mass & background source)
   - software: PyAutoLens
   - parameter: Source reconstructed on Voronoi mesh with constant regularization (coefficient lambda_reg)  
  > "In this work we use a constant regularization scheme, where the level of regularization is controlled by the coefficient, $\lambda_{\rm reg}$." (3.2.1 Background source)
   - parameter: Initial phase: SIS + shear mass and single Sersic source; later phases inherit priors  
  > "In the initial phase of our pipeline, we fit an SIS + shear profile for the mass distribution of the lensing galaxy and a single Sérsic profile for the background source." (3.2.2 Pipeline)
   - assumption: Spatially flat LCDM, H0 = 67.8, Omega_M = 0.308 (Planck 2016)  
  > "we adopt a spatially-flat $\Lambda$-CDM cosmology with H$_0=67.8 \pm 0.9\,\mathrm{km}\,\mathrm{s}^{-1}\,\mathrm{Mpc}^{-1}$" (1 Introduction)
   - assumption: Ignoring a small compact line-of-sight source; its SIS Einstein radius converged to negligible value  
  > "Therefore, for the remainder of this work we ignore the presence of this compact source" (3.2 Foreground mass & background source)
   - fitting: Non-linear search sampler and priors not stated (priors passed between phases)  
  > "inheriting from the previous phase in the form of priors" (3.2.2 Pipeline)
   - validation: Mass model independently derived from ALMA dust continuum agrees with F444W model; systematics discussed  
  > "We independently modelled the dust continuum emission from high-resolution ALMA observations and found that the best-fitting mass model parameters are in good agreement with those derived from the F444W NIRCam image." (Footnote 4)
6. **Reconstruct source-plane stars, dust and gas**: Fixed F444W mass model applied to NIRCam/MIRI images and to ALMA band 8 continuum and [CII] visibilities fitted directly in uv-space  
  > "When reconstructing the dust continuum and \[Cii\] line emission distributions with ALMA we make use of the latter approach." (3 Strong Lensing Analysis); "using a fixed mass model for the lensing galaxy" (4 Results)
   - software: PyAutoLens, PyNUFFT
   - assumption: Common centre set at the shared stellar and dust peak  
  > "Both the stellar and dust continuum distribution peak at the same location, which we used as the common centre for all reconstructions." (Footnote 5)
   - fitting: _not stated_
   - validation: Same mass model for all datasets so slope-size degeneracy not expected to introduce artifacts  
  > "However, since all datasets are reconstructed using the same mass model, this is not expected to introduce artifacts in the reconstructions." (3.2.3 Lens modelling systematics)
7. **Build [CII] velocity and dispersion maps**: Reconstruct each ~30 km/s channel in the uv-plane, then fit a Gaussian to the spectrum of each Voronoi cell for velocity and dispersion  
  > "first reconstructing (in the $uv$-plane) each individual channel of the emission line cube, where we binned the emission in channels of velocity width $\sim 30$ $\rm km \, s^{-1}$ to further increase the signal-to-noise ratio" (4.2 Kinematics); "we fit the spectrum of each reconstructed Voronoi cell with a Gaussian profile" (4.2 Kinematics)
   - software: PyAutoLens
   - parameter: Pixels shown only where SNR_G > 5 (SNR_G^2 = chi2_G - chi2_line)  
  > "we are only showing pixels for which ${\rm SNR}_{\rm G} > 5$." (4.2 Kinematics)
   - fitting: Gaussian per cell; comparison with straight-line chi2  
  > "we compared its goodness-of-fit (i.e. $\chi^2$) to that of a straight line going through the abscissa" (4.2 Kinematics)
   - validation: ~20 independent resolution elements across the disc, so gradient not from beam smearing  
  > "(we have $\sim$ 20 independent resolution elements across the area of the disc)" (4.2 Kinematics)
8. **Fit 3D tilted-ring model to the reconstructed [CII] cube**: 3DBarolo tilted-ring fit to the reconstructed cube interpolated onto a regular grid; fiducial configuration in Table (radsep 0.025 arcsec, 3dfit true, ftype 2, wfunc 2, ltype 1, norm local, twostage true, adrift true)  
  > "The main function of this code is to iteratively fit a 3D tilted-ring model to an observed data cube" (4.2.1 Dynamical modelling); "we first need to interpolate it onto a regular grid of pixels" (4.2.1 Dynamical modelling)
   - software: 3DBarolo
   - parameter: radsep = 0.025 arcsec  
  > "radsep | 0.025 | $\mathrm{arcsec}$ | Inter-ring spacing." (Table 3DBarolo config)
   - parameter: Initial guesses vrot 330, vdisp 37 km/s, inc 47 deg, pa 115 deg; free: vrot vdisp inc pa vsys  
  > "inc | 47.0 | $\mathrm{deg}$ | Initial guess for inclination." (Table 3DBarolo config); "pa | 115.0 | $\mathrm{deg}$ | Initial guess for position angle." (Table 3DBarolo config)
   - parameter: wfunc = 2 (cos^2 weighting), ftype = 2, norm = local, twostage = true, regtype = 1  
  > "Pixels weighted by angular distance $\theta_{\rm maj}$ from major axis as $\cos^2\theta_{\rm maj}$." (Table 3DBarolo config)
   - parameter: Disc scale height z0 = 0.0138 arcsec (100 pc)  
  > "z0 | 0.0138 | $\mathrm{arcsec}$ | Disc scale height, equivalent to $100\,\mathrm{pc}$" (Table 3DBarolo config)
   - assumption: Radial flows not modelled (vrad = 0); locally axisymmetric model  
  > "Radial flows are not modelled." (Table 3DBarolo config)
   - fitting: 3DBarolo ring-by-ring minimization of |model - data| with geometric regularization  
  > "Figure of merit for minimization set to $|{\rm model}-{\rm data}|$" (Table 3DBarolo config)
   - validation: Variant models (ftype, norm, regtype, weighting, vrad) changed the rotation curve by <~10 per cent mostly; uniform weighting and radial-flow variants changed it more  
  > "In most cases the influence of alternative assumptions was small, e.g. $\lesssim 10$ per cent in the rotation curve amplitude at fixed radius." (Details of kinematic modelling)
9. **Derive dynamical mass and baryon fraction**: Mdyn = 2.32e5 Vc^2 r Msun with Vc from 3DBarolo (asymmetric-drift corrected, mean of 5 outer rings) at r = 4 kpc; compared with stellar plus gas mass  
  > "{M}_{\rm dyn} = 2.32 \times 10^5" (4.2.1 Dynamical modelling); "where $V_{\rm c}$ is the circular velocity and $r$ is the radius at which we compute the dynamical mass." (4.2.1 Dynamical modelling)
   - software: 3DBarolo
   - parameter: r = 4 kpc (extent of the region probed dynamically)  
  > "which is the extent of the region where we probe the dynamics of our galaxy" (4.2.1 Dynamical modelling)
   - assumption: Integrated stellar and gas masses are assumed to lie within the 4.0 kpc aperture  
  > "In order to make this estimate we assume that the stellar and gas masses that we measure for our source" (4.2.2 The dynamics of SPT)
   - fitting: _not stated_
   - validation: Mbar/Mdyn treated as an upper limit since gas may extend beyond 4 kpc  
  > "Therefore, the ratio of baryonic to total mass should be considered as an upper limit." (4.2.2 The dynamics of SPT)
10. **Measure radial profiles and sizes**: Single/double Sersic fits to the averaged 1D profiles of stars, dust, [CII]; curves of growth for half-light radii (also Halpha)  
  > "We fit a single/double Sérsic model to the average 1D profile" (4.1.1 1D profiles); "We can use this to estimate the half-light radius of each component." (4.1.1 1D profiles)
   - fitting: _not stated_
   - validation: Curve-of-growth sizes consistent with Sersic fits  
  > "The sizes measured from the curves of growth are consistent with our findings from the 1D Sérsic profiles." (4.1.1 1D profiles)
11. **Ellipse fitting to identify the bar and its length**: Photutils ellipse fitting of reconstructed F444W, F1280W and [CII]; centre free then fixed to median from F444W; bar criteria on ellipticity and position angle  
  > "We make use of the in PHOTUTILS from Astropy package (Bradley et al. 2020)." (5.1 Bars); "We then run the algorithm a second time, fixing the centre of the ellipses to the median value estimated in the initial run." (5.1 Bars)
   - software: Photutils, Astropy
   - parameter: Bar criterion (i): ellipticity rises to e_max > 0.25 with roughly constant PA; criterion (ii): ellipticity drops by at least 0.1 and PA changes by at least 10 deg at bar-disc transition  
  > "(i) the ellipticity gradually increases in the bar-dominated region, reaching a maximum value $e_{\rm max} > 0.25$, while the position angle remains relatively constant." (5.1 Bars)
   - fitting: _not stated_
   - validation: F1280W reconstruction used to check dust obscuration in F444W; [CII] ellipticity consistent with a bar  
  > "The reason for attributing the decrease in surface brightness to dust is that the F1280W reconstruction does not show the same behavior" (5.1 Bars)

## Software

- **CASA** : ALMA pipeline calibration  
  > "We calibrate the data using the ALMA pipeline in the Common Astronomy Software Applications package (cite: 2007ASPC..376..127M)." (2.1.3 ALMA)
- **magphys (high-z version)** : SED fitting  
  > "we perform SED modelling using the high-redshift version of the publicly available software magphys" (2.2.1 SED fitting)
- **PyAutoLens** : Lens modelling, lens light subtraction and source reconstruction (imaging and uv-plane)  
  > "using the open-source software PyAutoLens" (3 Strong Lensing Analysis)
- **3DBarolo** 1.6.9 (git commit 171b30b379fdc76e402cb0c8cf6d8cbb8e784196): 3D tilted-ring kinematic modelling of the [CII] cube  
  > "The main function of this code is to iteratively fit a 3D tilted-ring model to an observed data cube" (4.2.1 Dynamical modelling); "Version 1.6.9; git commit ID 171b30b379fdc76e402cb0c8cf6d8cbb8e784196." (Footnote 6)
- **Photutils (Astropy)** : Ellipse fitting of reconstructions  
  > "We make use of the in PHOTUTILS from Astropy package (Bradley et al. 2020)." (5.1 Bars)
- **Dynesty** : _not stated_
- **PyAutoFit** : _not stated_
- **PyAutoGalaxy** : _not stated_
- **PyNUFFT** : _not stated_
- **Scikit-image** : _not stated_
- **Colossus** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamical mass within 4 kpc | (9.7 +/- 2.0)e10 | 2.0e10 | Msun | 9 | Dynamical modeling yields a dynamical mass, ${M}_{\rm dyn} = (9.7 \pm 2.0) \times 10^{10}$ ${\rm M}_{\odot}$ |
| V/sigma | 9.8 | 1.2 | dimensionless | 8 | we estimate a ratio of rotational velocity to velocity dispersion of, $V / \sigma = 9.8 \pm 1.2$. |
| Maximum rotational velocity Vmax | 313 | 5 | km/s | 8 | $V_{\rm max} = 313 \pm 5 \, {\rm km \, s^{-1}}$ |
| Velocity dispersion sigma (5 outer rings) | 32 | 4 | km/s | 8 | $\sigma = 32 \pm 4 \, {\rm km \, s^{-1}}$ |
| Circular velocity Vc (asymmetric-drift corrected) | 327 | 3 | km/s | 8 | ${V}_{\rm c} = 327 \pm 3 \, {\rm km \, s^{-1}}$ |
| Inclination range of fitted rings | 48 to 50 | not stated | deg | 8 | varying between 48 and 50 degrees |
| Stellar mass | (6.3 +/- 0.9)e10 | 0.9e10 | Msun | 3 | ${M}_{\star} = (6.3 \pm 0.9) \times 10^{10}$ $\rm{M}_{\odot}$ |
| Star formation rate | 781 | 99 | Msun/yr | 3 | ${\rm SFR} = 781 \pm 99$ ${\rm M_{\odot} yr^{-1}}$, after correcting for magnification |
| Infrared luminosity LIR | (9.4 +/- 1.4)e12 | 1.4e12 | Lsun | 3 | (9.4 $\pm$ 1.4) $\times \, 10^{12}$ |
| Stellar population age | 0.8 | 0.1 | Gyr | 3 | 0.8 $\pm$ 0.1 |
| Molecular gas mass before magnification correction | (1.8 +/- 0.4)e11 | 0.4e11 | Msun | 4 | $M_{\rm gas} = (1.8 \pm 0.4) \times 10^{11}$ ${\rm M_{\odot}}$ |
| Molecular gas mass (magnification corrected) | (2.8 +/- 0.7)e10 | 0.7e10 | Msun | 4 | (2.8 $\pm$ 0.7) $\times \, 10^{10}$ |
| Gas fraction | 0.45 | 0.12 | dimensionless | 4 | $\rm f_{\rm gas} = 0.45 \pm 0.12$ |
| Baryonic mass (stars + gas) | (9.1 +/- 1.1)e10 | 1.1e10 | Msun | 9 | we estimate a total baryonic mass (stars $+$ gas) of ${M}_{\rm b} = \left( 9.1 \pm 1.1 \right) \times 10^{10}$ |
| Mbar/Mdyn within 4.0 kpc | 0.9 | 0.2 | dimensionless | 9 | we derive a baryonic-to-total mass ratio of ${M}_{\rm bar} / {M}_{\rm dyn} = 0.9 \pm 0.2$ within 4.0 kpc. |
| Dark matter fraction within 4.0 kpc | <30 | not stated | per cent | 9 | the dark matter fraction, $f_{\rm DM}$, within 4.0 kpc is $<30$ per cent |
| Einstein radius (F444W mass model) | 1.175 | 0.003 | arcsec | 5 | 1.175 $\pm$ 0.003 |
| EPL slope alpha (F444W mass model) | 2.05 | 0.04 | dimensionless | 5 | 2.05 $\pm$ 0.04 |
| Stellar central Sersic component (n, r_e) | n = 1.32, r_e = 0.72 | 0.04 (n), 0.01 (r_e) | kpc (r_e) | 10 | $n = 1.32 \pm 0.04$ and $r_{\rm e} = 0.72 \pm 0.01$ kpc for the central component of the double Sérsic model |
| Stellar extended Sersic component (n, r_e) | n = 0.25, r_e = 1.96 | 0.01 (n), 0.03 (r_e) | kpc (r_e) | 10 | $n = 0.25 \pm 0.01$ and $r_{\rm e} = 1.96 \pm 0.03$ kpc for the extended component |
| Dust continuum Sersic components (central n, r_e; extended n, r_e) | central n = 0.97, r_e = 0.72; extended n = 0.29, r_e = 1.80 | 0.01, 0.01; 0.04, 0.04 | kpc (r_e) | 10 | $n = 0.97 \pm 0.01$ and $r_{\rm e} = 0.72 \pm 0.01$ kpc for the central, and $n = 0.29 \pm 0.04$ and $r_{\rm e} = 1.80 \pm 0.04$ kpc for the extended components |
| [CII] single Sersic (n, r_e) | n = 0.64, r_e = 2.67 | 0.02 (n), 0.07 (r_e) | kpc (r_e) | 10 | has $n = 0.64 \pm 0.02$ and $r_{\rm e} = 2.67 \pm 0.07$ kpc |
| Fraction of dust continuum in extended component | ~20 | not stated | per cent | 10 | $\sim$20 per cent of the dust continuum emission is associated with an extended component |
| Bar length | ~1.5 | not stated | kpc | 11 | we estimate a bar length of $L_{\rm bar} \sim 1.5$ kpc |
| Disc mass fraction | 50 - 80 | not stated | per cent | 9 | we constrain the disc mass fraction in SPT in the range of, $f_{\rm disc} = 50 - 80$ per cent |

## Qualitative findings

- Stellar and [CII] gas distributions show a central linear (bar) structure; the dust continuum is compact and centrally concentrated  
  > "The imaging reveals a central bar structure in the stars and gas embedded within an extended disc with a spiral arm-like feature." (abstract)
- Velocity and dispersion maps show a regularly rotating disc with no sign of a recent close interaction  
  > "we can confidently state that the source did not experience a close-proximity interaction with another massive galaxy in its recent past" (4.2.2 The dynamics of SPT)
- SPT is a starburst, with SFR more than 4 times above the main sequence  
  > "It’s SFR is more that $\times 4$ above the main-sequence of star-formation galaxies at z=3.78" (2.2.1 SED fitting)

## Claim tuples

- H: SPT hosts a bar | E: Source-plane reconstructions of F444W, MIRI F1280W and [CII] plus photutils ellipse fitting against literature bar criteria | R: Elongated central structure; [CII] ellipses with e ~ 0.8 out to ~1.5 kpc then drop of ~0.3; L_bar ~1.5 kpc | F: SPT is a barred spiral; the bar is seen more clearly in gas than stars | **supported**
- H: The gas kinematics are those of a regularly rotating, rotation-dominated disc | E: 3DBarolo tilted-ring model of the reconstructed [CII] cube | R: Vc = 327 +/- 3 km/s, sigma = 32 +/- 4 km/s, V/sigma = 9.8 +/- 1.2 | F: Rotation dominated disc with cold dispersion, similar to other DSFGs | **supported**
- H: SPT is baryon dominated within 4 kpc | E: Compare SED stellar mass plus CO(2-1)-based gas mass with Mdyn from 3DBarolo | R: Mbar/Mdyn = 0.9 +/- 0.2; f_DM < 30 per cent | F: Consistent with a baryon-dominated galaxy, but the ratio is an upper limit | **partially**
- H: SPT has spiral arm structure | E: Source-plane Halpha and F444W reconstructions and radial profiles | R: A spiral arm east of centre in Halpha with its base in F444W; a bump near r ~ 1.5 kpc in 1D profiles | F: Evidence for at least one spiral arm; possibly m = 1 | **partially**
- H: Bar formation can begin earlier and in more gas-rich galaxies than previously thought | E: Compare disc mass fraction, stellar age and gas fraction with idealised bar-formation simulations from literature | R: f_disc = 50-80 per cent, stellar age ~0.8 Gyr, f_gas = 0.45 +/- 0.12 | F: Tentative bar formation timescale of ~0.8 Gyr | **partially**

## Reasoning

- Why this data: Highest-resolution ALMA continuum in the archive chosen to complement JWST  
  > "In order to best complement our data from JWST, we make use of the highest resolution ALMA continuum dataset available in the archive." (2.1.3 ALMA)
- Why this method: [CII] chosen over Halpha for kinematics: higher SNR and finer velocity resolution; F444W chosen for the lens mass model because lens light is weaker and source SNR higher  
  > "The reason for choosing the \[Cii\] over the H$\alpha$ emission line is two fold: it has a higher signal-to-noise ratio" (4.2 Kinematics); "As for choosing the F444W filter out of four filter images observed with NIRCam, the reason is twofold." (3 Strong Lensing Analysis)
- Alternative: Extra SIS mass component for the compact foreground source tried and dropped (Einstein radius converged to negligible value)  
  > "We tried including an additional component in the mass model, specifically a spherical Singular Isothermal Sphere" (3.2 Foreground mass & background source)
- Alternative: Free radial-flow component in 3DBarolo tried but outcome depended strongly on initial guess  
  > "but found that the outcome was very sensitive to the initial guess provided" (Details of kinematic modelling)
- Alternative: Uniform pixel weighting in 3DBarolo gave lower inclination and peak rotation near 400 km/s, judged biased by the bar  
  > "using a uniform weighting for all pixels leads to a preference for a lower inclination and a higher rotation curve amplitude" (Details of kinematic modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Mbar/Mdyn is an upper limit since the unresolved CO(2-1) gas may extend beyond 4 kpc  
  > "This is not necessarily true as the molecular gas distribution could extend beyond 4.0 kpc" (4.2.2 The dynamics of SPT)
- Limitation (authors): The axisymmetric 3DBarolo model fails to capture the bar-dominated kinematics  
  > "our model (locally axisymmetric) model fails to capture the detailed kinematics of the galaxy that are dominated by an $m=2$ non-axisymmetric feature" (Details of kinematic modelling)
- Limitation (authors): Lens mass model is a power law without angular complexity; slope-size degeneracy can bias source size  
  > "This type of systematic can lead to a biased estimate of the source’s size." (3.2.3 Lens modelling systematics)
- Limitation (authors): MIRI reconstructions are too low in resolution to resolve the bar  
  > "but due to resolution limitations the feature is not fully resolved" (5.1 Bars)
- Caveat (inferred, ours): Bar identification rests on visual structure and ellipse fitting in reconstructed source-plane maps, with F444W ellipses failing the standard criteria in the central 0.5 kpc
- Caveat (inferred, ours): Stellar and gas masses are global values compared against a 4 kpc dynamical mass; gas mass uses a CO(2-1) to CO(1-0) ratio and alpha_CO = 1.0 with no uncertainty propagated from alpha_CO
- Caveat (inferred, ours): Dynamical mass depends on the inclination from an axisymmetric fit to a barred system; the uniform-weighting variant shows large sensitivity
- Caveat (inferred, ours): No ALMA imaging or reconstruction parameters given, so the visibility-plane modelling cannot be checked
- Caveat (inferred, ours): The tentative bar formation timescale equates stellar age (0.8 Gyr, very uncertain) with disc formation

## Reproducibility

- Data public (paper): All data used are publicly available  
  > "All data used in this work are publicly available." (Data Availability)
- Products in archive: _not stated_
- Code: PyAutoLens and 3DBarolo are public; paper-specific scripts and lens/dynamical model outputs not stated  
  > "using the open-source software PyAutoLens" (3 Strong Lensing Analysis); "we use the publicly available software" (4.2.1 Dynamical modelling)
- Missing: ALMA measurement sets, pipeline version and imaging/uv-processing settings
- Missing: Lens model priors, sampler settings and magnification maps
- Missing: Full mass-model parameters beyond Table 2 and the source mesh settings
- Missing: Number of 3DBarolo rings and which rings were averaged for Vmax and sigma beyond 'five outer rings'
- Missing: SED photometry table
- Data volume (inferred): ALMA raw data for two projects likely tens of GB (Band 8 continuum and [CII]/CO/[CI] cubes); JWST NIRCam/MIRI/NIRSpec products a few GB
- Score (inferred): 3/5, Data are public and key numbers are reported, and the 3DBarolo configuration is tabulated, but ALMA processing, uv-plane lens-modelling inputs and sampler settings are not given and rely on earlier papers.
- Rediscovery candidate: no, Public data and numeric results, but ALMA processing and the lens-model reconstruction recipe are incomplete, so the kinematic results cannot be redone from the paper alone.

## Links

- Method: (cite: 2015MNRAS.452.2940N; 2018MNRAS.478.4738N; 2021JOSS....6.2825N) (PyAutoLens lens modelling and Voronoi source reconstruction)
- Method: (cite: 2022MNRAS.517.3275E; 2022RAA....22b5014C) (Describe the phased lens-modelling pipeline reused here)
- Method: (cite: 2015MNRAS.451.3021D) (3DBarolo tilted-ring code)
- Method: (cite: 2015ApJ...806..110D; 2019ApJ...882...61B) (MAGPHYS SED fitting)
- Companion: (cite: 2022A&A...663A..22G) (Earlier CO(7-6) dynamical mass and CO(2-1) data for this source)
- Companion: (cite: 2016MNRAS.457.4406A) (Earlier CO(2-1) observations of this source)
- Companion: (cite: 2023ApJ...945L..10G) (Ellipse-fitting bar criteria applied here)
- Companion: (cite: 2023arXiv230710412B) (NIRSpec emission lines detected in this source)
- Related: JWST TEMPLATES Early Release Science program (ID 1355, PI Jane Rigby)
- Related: South Pole Telescope survey (SPT)
- Related: ALMA 2018.1.01060.S and 2019.1.00471.S

## Checks

```json
{
 "quotes": 143,
 "quotes_ok": 143,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 25,
 "numeric_problems": 0,
 "fill": {
  "facts": 133,
  "stated": 87,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
