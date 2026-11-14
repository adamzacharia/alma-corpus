# The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): VIII. A dust arc and non-Keplerian gas kinematics in HD 121617

`2026A&A...705A.202M` | Astronomy and Astrophysics 2026 | first author: Marino, S. | arXiv: 2601.11711 | DOI: 10.1051/0004-6361/202556493

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: Characterise the dust arc, the dust and CO gas distributions, and the gas kinematics (non-Keplerian rotation) of the gas-rich exoKuiper belt HD 121617, to constrain the arc origin and the gas origin  
  > "In this paper, we analyse in detail the dust and gas distributions and the gas kinematics of this system." (abstract)
- Target **HD 121617**: coordinates _not stated_; z/distance 118 pc  
  > "This system is composed of a 16 Myr old A1V type star at 118 pc (cite: Pecaut2016; Houk1978; gaiadr3)" (Introduction); distance from cited as (cite: Pecaut2016; Houk1978; gaiadr3), not separated per quantity  
  > "This system is composed of a 16 Myr old A1V type star at 118 pc (cite: Pecaut2016; Houk1978; gaiadr3)" (Introduction)

## Data provenance

- ALMA projects: 2022.1.00338.L
- bands: Band 7 (0.89 mm)  
  > "HD 121617 was observed in band 7 (0.89 mm) between October 2022 and May 2023" (2 Dust and gas distribution)
- frequencies and spectral setup: four spectral windows: dust continuum plus 12CO and 13CO J=3-2; spectral resolution 26 m/s (12CO, 13 m/s channels) and 850 m/s (13CO)  
  > "The observations included four spectral windows targeting the dust continuum emission that is dominated by millimetre-sized grains and the $^{12}$CO and $^{13}$CO gas J=3-2 emission." (2 Dust and gas distribution); "The $^{12}$CO and $^{13}$CO observations had a spectral resolution of 26 and 850 m/s, respectively." (2 Dust and gas distribution); "with a resolution of 26 m/s (13 m/s channels)" (3 CO gas kinematics)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: two antenna configurations (small and large scale structures)  
  > "using two antenna configurations to sample small and large scale structures" (2 Dust and gas distribution)
- baselines: _not stated_
- angular resolution: 0.12 arcsec (14 au)  
  > "0.12$''$ (14 au) resolution" (abstract)
- max recoverable scale: ~5 arcsec (600 au)  
  > "a maximum recoverable scale of ${\sim}5$$''$ or 600 au" (2 Dust and gas distribution)
- sensitivity: peak S/N of ALMA dust, 12CO and 13CO images: 24, 21, 19  
  > "The peak signal-to-noise (S/N) of the SPHERE image, ALMA dust, $^{12}$CO, and $^{13}$CO images is 10, 24, 21, and 19, respectively." (2 Dust and gas distribution)
- time on source: _not stated_
- observing dates: October 2022 to May 2023  
  > "HD 121617 was observed in band 7 (0.89 mm) between October 2022 and May 2023" (2 Dust and gas distribution)
- pi or archival as stated: ARKS Large Program 2022.1.00338.L, PI S. Marino (new ARKS observations)  
  > "we use the new ALMA images obtained as part of ARKS (2022.1.00338.L, PI: S. Marino, co-PIs: A. M. Hughes & L. Matrà)" (2 Dust and gas distribution)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Other facility **VLT/SPHERE (IRDIS, J band polarised scattered light)**: Re-reduced Q_phi image at 1.25 um, 0.04 arcsec (5 au) resolution, observed 18 April 2018, tracing micron-sized grains  
  > "we used VLT/SPHERE polarised data that traces the scattered light by small micron-sized grains" (2 Dust and gas distribution); "obtained using IRDIS on 18 April 2018 and achieving a resolution of" (2 Dust and gas distribution)
- External data: SPHERE scattered-light image, originally presented in Perrot2023 and re-reduced in ARKS  
  > "The data were originally presented in (cite: Perrot2023) and re-reduced by (cite: scat_arks) as part of ARKS." (2 Dust and gas distribution) [from (cite: Perrot2023); (cite: scat_arks)]
- External data: Stellar mass 1.90 +/- 0.01 Msun from stellar evolution models  
  > "These values are well in agreement with the $1.90\pm0.01\ M_{\odot}$ inferred using stellar evolution models (cite: overview_arks)." (3.2 De-projected azimuthal velocity) [from (cite: overview_arks)]
- External data: Gas temperature profile beta=-0.14, T0=38 K, r0=73 au from fit to the 13CO cube  
  > "We assume that $\beta=-0.14$, $T_{0}=38$ K, and $r_0$=73 au as found in (cite: line_arks) by fitting the $^{13}$CO data cube." (3.3 Retrieving the radial density profile) [from (cite: line_arks)]
- External data: Dust mass 0.21 +/- 0.02 Mearth from SED fit (comparison value)  
  > "The derived value agrees well with the dust mass of $0.21\pm0.02\ M_{\oplus}$ derived by (cite: Perrot2023) fitting the spectral energy distribution." (2.2 Arc parametric fit to continuum emission) [from (cite: Perrot2023)]
- External data: Eccentricity of 0.03 for the small-grain scattered-light belt  
  > "a narrow belt of small dust grains and a potential small eccentricity of 0.03" (Introduction) [from (cite: Perrot2023; scat_arks)]
- Simulation/model as data: Synthetic 12CO J=3-2 cubes of Keplerian and pressure-supported (non-Keplerian) gas rings made with DISC2RADMC and simulated ALMA observations, used to test the kinematic method  
  > "We start by simulating synthetic image cubes using DISC2RADMC (cite: Marino2022)." (Appendix 12CO radiative transfer models); "We use these synthetic cubes to simulate ALMA observations using the task SIMOBSERVE in CASA (cite: casa)" (Appendix 12CO radiative transfer models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Clean algorithm (details deferred to ARKS I and IV)  
  > "Imaging of the continuum and CO data was performed using the Clean algorithm (cite: overview_arks; gas_arks)." (2 Dust and gas distribution)
- deconvolver: _not stated_
- weighting robust: robust = 0.5 for the 12CO cube used for kinematics (robust = 2 cubes mentioned as lower resolution)  
  > "We use the clean data cube corresponding to a robust value of 0.5 (cite: gas_arks)." (3 CO gas kinematics); "They are stronger in lower-resolution cubes (with a robust parameter of 2)" (3.1 2D velocity map)
- uv taper: _not stated_
- cell size: pixel size = 20% of the beam size  
  > "We divided the disc into a set of concentric annuli spaced by 20% of the beam size (same as the pixel size)" (3.2 De-projected azimuthal velocity)
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

- Imaging of continuum and CO data  
  > "Imaging of the continuum and CO data was performed using the Clean algorithm (cite: overview_arks; gas_arks)." (2 Dust and gas distribution) [from (cite: overview_arks; gas_arks)]
- Radial profiles extracted from the CLEAN images with the same approach as ARKS radial-profile paper  
  > "extracted directly from the CLEAN images using the same approach as presented in (cite: rad_arks)" (2.1 Radial and azimuthal profiles) [from (cite: rad_arks)]
- Visibility-based parametric dust fit approach (disc2radmc + MCMC)  
  > "we fitted a parametric model to the continuum visibilities following the same approach as in (cite: overview_arks)" (2.2 Arc parametric fit to continuum emission) [from (cite: overview_arks)]
- Dust size distribution 1 um to 1 cm with exponent -3.5 (and composition/opacity setup)  
  > "As in (cite: overview_arks), we modelled the dust as a size distribution from 1 $\mu$m to 1 cm, with a power law exponent of -3.5." (2.2 Arc parametric fit to continuum emission) [from (cite: overview_arks)]
- Self-subtraction of the scattered-light azimuthal profile by mirroring about the semi-minor axis  
  > "we self-subtracted the emission mirroring the azimuthal profile with respect to the semi-minor axis at the near side of the ring (cite: scat_arks)" (2.1 Radial and azimuthal profiles) [from (cite: scat_arks)]
- Gas temperature parameters beta, T0, r0 for the density retrieval  
  > "We assume that $\beta=-0.14$, $T_{0}=38$ K, and $r_0$=73 au as found in (cite: line_arks) by fitting the $^{13}$CO data cube." (3.3 Retrieving the radial density profile) [from (cite: line_arks)]
- Pixel size and mask conventions for simulated cube imaging follow ARKS gas paper  
  > "a Keplerian mask and the same pixel size as in (cite: gas_arks)" (Appendix 12CO radiative transfer models) [from (cite: gas_arks)]

### Not stated but needed to reproduce (our reading)

- MCMC priors and bounds for all dust-model parameters, number of walkers/steps, burn-in and convergence criteria
- Which continuum image/visibility set was fitted, weighting, and how the stellar position/phase centre was handled in the fit
- Vertical structure (aspect ratio) and temperature or grid settings of the disc2radmc dust model used for the arc fit
- How the arc mass fraction (13%) was computed from the posterior
- Continuum subtraction and line-free channels for the CO cubes, and the CASA/pipeline version used for calibration
- BETTERMOMENTS settings (spectral range, clipping, noise estimate, mask) for the Gaussian moment-1 map
- EDDY settings (initial guesses, bounds, uncertainty estimation, radial range, minimum pixels per annulus, number of pixels resampled)
- Exact wedge/annulus definitions and radial bin widths for the azimuthal velocity extraction
- Kinematic-density retrieval: radial range, integration constant and normalisation, smoothing of the velocity profile
- Rest frequencies of 12CO and 13CO J=3-2 and the velocity reference used
- Input density, noise level and Keplerian mask parameters of the simulated cubes beyond the quoted Gaussian ring

## Analysis recipe

1. **Extract radial and azimuthal profiles of dust, CO and scattered light**: Radial and azimuthal intensity profiles from the SPHERE image, ARKS continuum and 12CO/13CO moment 0 images, using wedges for radial profiles and an averaged annulus for azimuthal profiles  
  > "we extracted radial and azimuthal intensity profiles from the SPHERE scattered light image, ARKS dust continuum image, and ARKS $^{12}$CO and $^{13}$CO J=3-2 moment 0 images" (2.1 Radial and azimuthal profiles)
   - parameter: ALMA radial profiles: two opposing 120 deg wide wedges along the major axis (SPHERE: 60 deg wedges)  
  > "For the ALMA dust continuum and CO images we use two opposing 120 wide wedges aligned with the disc major axis" (footnote 2)
   - parameter: Azimuthal profiles averaged over 65-90 au with a rolling azimuthal window of 40 deg  
  > "The profiles are extracted by averaging the emission between 65 and 90 au (roughly the FWHM of the millimetre emission)" (2.1 Radial and azimuthal profiles); "using a rolling azimuthal window of 40 projected in the sky plane" (2.1 Radial and azimuthal profiles)
   - assumption: Images are well centred on the stars (stellar location uncertainty <~10 mas for ALMA)  
  > "and assuming the images to be well centred on the stars" (2.1 Radial and azimuthal profiles); "we know the star should be at the centre with an uncertainty of ${\lesssim}10$ mas" (footnote 3)
   - fitting: _not stated_
   - validation: Residual profiles checked with different assumed stellar locations  
  > "The residual is still significant if we assume a different stellar location" (2.1 Radial and azimuthal profiles)
2. **Fit an axisymmetric plus arc model to the continuum visibilities**: Parametric disc2radmc density model, radiative-transfer image, Fourier transform and likelihood with Galario, MCMC sampling  
  > "Simply put, we used a parametric model to define the disc density distribution, produced a synthetic image using radiative transfer calculations, Fourier transformed the image and calculated the model likelihood using Galario (cite: galario)" (2.2 Arc parametric fit to continuum emission)
   - software: disc2radmc, Galario, emcee
   - parameter: Axisymmetric component: double power law fitted to the azimuthally averaged radial profile  
  > "which was found to provide a good fit to the azimuthally averaged radial profile (cite: rad_arks)" (2.2 Arc parametric fit to continuum emission)
   - parameter: Arc component: 2D Gaussian in r and azimuth, with separate azimuthal widths on the leading and trailing sides  
  > "described as a 2D Gaussian as a function of $r$ and the azimuthal angle, $\phi$, measured anti-clockwise in the plane of the disc from the SW ansa" (2.2 Arc parametric fit to continuum emission); "Furthermore, we split $\sigma_\phi$ into two parameters to allow the arc to be azimuthally asymmetric as the azimuthal profile suggests." (2.2 Arc parametric fit to continuum emission)
   - parameter: Free parameters also include inclination, position angle, and RA/Dec offsets  
  > "Finally, we also leave as free parameters the disc inclination and position angle (longitude of ascending node), and RA and Dec offsets." (2.2 Arc parametric fit to continuum emission)
   - parameter: Dust opacity 1.9 cm2/g at 0.89 mm  
  > "This results in an opacity of 1.9 cm$^{2}$ g$^{-1}$ at 0.89 mm (the only wavelength being fitted here)." (2.2 Arc parametric fit to continuum emission)
   - assumption: Dust size distribution 1 um to 1 cm, exponent -3.5  
  > "we modelled the dust as a size distribution from 1 $\mu$m to 1 cm, with a power law exponent of -3.5" (2.2 Arc parametric fit to continuum emission)
   - assumption: Composition 70% astrosilicates, 15% crystalline water ice, 15% amorphous carbon by mass  
  > "We assumed a dust composition made of 70% astrosilicates, 15% crystalline water ice, and 15% amorphous carbon by mass (cite: Draine2003; LiGreenberg1998)." (2.2 Arc parametric fit to continuum emission)
   - assumption: Compact spherical grains, Mie opacities  
  > "We assumed grains to be compact and spherical and used Mie theory to calculate their opacities." (2.2 Arc parametric fit to continuum emission)
   - fitting: Affine Invariant MCMC Ensemble sampler (emcee); priors not stated  
  > "sampled the posterior distribution using the Python package EMCEE (cite: emcee) to fit the free parameters using the Affine Invariant MCMC Ensemble sampler (cite: Goodman2010)" (2.2 Arc parametric fit to continuum emission)
   - validation: Model, beam-convolved model and residual maps compared; only a few 3-sigma negatives at SW  
  > "Overall, we find a good match between the observed morphology and the model." (2.2 Arc parametric fit to continuum emission)
3. **Fit a Keplerian model to the 12CO line-of-sight velocity map**: Gaussian-method moment 1 map with BETTERMOMENTS from the robust 0.5 cube, then Keplerian fit with EDDY for orientation, systemic velocity and stellar mass  
  > "We extracted a 2D line-of-sight velocity map from the clean cube using the package BETTERMOMENTS and the Gaussian method that fits a Gaussian line profile to each pixel (cite: bettermoments; bettermoments_unc)." (3.1 2D velocity map); "We fitted a Keplerian model to this velocity map using the EDDY package (cite: eddy) to determine the orientation of the system, systemic velocity, and stellar mass." (3.1 2D velocity map)
   - software: BETTERMOMENTS, EDDY
   - parameter: Cube: 12CO clean cube with robust 0.5  
  > "We use the clean data cube corresponding to a robust value of 0.5 (cite: gas_arks)." (3 CO gas kinematics)
   - assumption: Emission arises from the midplane (elevated-surface models gave heights consistent with zero)  
  > "Therefore, for the following analysis, we assume that the emission arises from the midplane." (3.1 2D velocity map)
   - fitting: EDDY Keplerian fit; reported uncertainties <1% but likely underestimated because pixel correlation is ignored  
  > "The uncertainties on these values extracted by EDDY are below 1%, but they are likely underestimated as they do not take into account the spatial correlation between pixels." (3.1 2D velocity map)
   - validation: Inclination and PA compared with the dust-derived values; stellar mass compared with ARKS I value  
  > "The derived values for the inclination and position angle are consistent with those derived for the dust emission" (3.1 2D velocity map)
4. **Extract de-projected azimuthal, radial and vertical velocities versus radius**: EDDY in concentric annuli using the Gaussian line centroid and the simple harmonic oscillator (SHO) method for 3D velocities  
  > "We used the Gaussian method to derive the line centroid and the ‘simple harmonic oscillator (SHO)’ method to derive the 3D velocities at each radius." (3.2 De-projected azimuthal velocity)
   - software: EDDY
   - parameter: Annuli spaced by 20% of the beam size, oriented at the disc PA and inclination from the Keplerian fit  
  > "We divided the disc into a set of concentric annuli spaced by 20% of the beam size (same as the pixel size) and oriented at the same position angle and inclination as the disc" (3.2 De-projected azimuthal velocity)
   - parameter: Fit restricted to position angles within 20 deg of the major axis  
  > "we also restricted the fit to position angles within 20$^\circ$ from the major axis of the disc" (3.2 De-projected azimuthal velocity)
   - assumption: Systemic velocity fixed to the value from the Keplerian fit (vertical/systemic degeneracy)  
  > "we can fix and approximate the systemic velocity to be the systemic velocity extracted from the Keplerian fit" (3.2 De-projected azimuthal velocity)
   - fitting: EDDY run ten times with disc orientation drawn from the Keplerian-fit posterior, each with ten retrievals on random pixel subsets per annulus  
  > "we ran EDDY ten times, randomising the disc orientation according to the posterior distribution of the Keplerian fit." (3.2 De-projected azimuthal velocity); "For each orientation, EDDY performs ten retrievals using a different random sample of pixels within each annulus" (3.2 De-projected azimuthal velocity)
   - validation: Compared with the profile from a simulated beam-smeared Keplerian observation; result also seen when fitting all azimuths or the moment 1 map  
  > "This finding is also present if we fit all azimuths, although less strongly, and if we fit the moment 1 instead of the cube." (3.2 De-projected azimuthal velocity)
5. **Retrieve the gas radial density profile from the Keplerian deviations**: Use the deviation of v_phi from Keplerian as a proxy for the radial pressure gradient, solve the midplane force balance for d ln(rho)/dr and integrate over r  
  > "we aim to retrieve the gas density profile using the Keplerian deviations as a proxy for the pressure gradient." (3.3 Retrieving the radial density profile); "Integrating the right-hand side over $r$, we obtain $\ln[\rho(r)]$ plus a constant that becomes a normalisation factor." (3.3 Retrieving the radial density profile)
   - parameter: beta=-0.14, T0=38 K, r0=73 au (from ARKS 13CO fit)  
  > "We assume that $\beta=-0.14$, $T_{0}=38$ K, and $r_0$=73 au as found in (cite: line_arks) by fitting the $^{13}$CO data cube." (3.3 Retrieving the radial density profile)
   - parameter: M_star = 1.91 Msun so that Keplerian speed at 75 au equals the measured azimuthal velocity  
  > "Moreover, we assume that $M_\star=1.91\ M_\odot$, which makes the Keplerian speed at the arc location (75 au) the same as the extracted azimuthal velocity." (3.3 Retrieving the radial density profile)
   - assumption: Mean molecular weight mu = 14 (C and O dominated, secondary gas) or 2.3 (H2 dominated, primordial); midplane z=0; power-law temperature  
  > "we assume two values for $\mu$: 14 for a disc dominated by C and O (secondary gas), and 2.3 for an H$_2$-dominated disc (primordial gas)." (3.3 Retrieving the radial density profile)
   - fitting: _not stated_
   - validation: Retrieved profile compared with the 13CO density profile; method tested on simulated models where it recovered the input density  
  > "For both non-Keplerian models, the derived profiles reproduce well the true input profile despite the effects of beam smearing and optical depth effects." (Appendix 12CO radiative transfer models)
6. **Validate the kinematic method with simulated Keplerian and pressure-supported observations**: Synthetic 12CO cubes from DISC2RADMC, simulated ALMA observations with CASA simobserve, imaged with tclean, then processed like the data (velocity map, Keplerian residuals, azimuthal velocities)  
  > "The simulated ALMA observations are then imaged using TCLEAN using a Briggs weighting, a robust parameter of 0.5, a Keplerian mask and the same pixel size as in (cite: gas_arks)." (Appendix 12CO radiative transfer models); "Finally, we follow the same procedure as with the real data, and extract the line-of-sight velocities, residuals after a Keplerian model subtraction, and azimuthal velocities from the simulated observations." (Appendix 12CO radiative transfer models)
   - software: disc2radmc, CASA, tclean
   - parameter: Cubes with 26 m/s spectral resolution and 10 mas spatial resolution  
  > "We simulate image cubes with a spectral resolution of 26 m/s and spatial resolution of 10 mas." (Appendix 12CO radiative transfer models)
   - parameter: Gaussian radial surface density centred at 74 au, FWHM 17 au, aspect ratio h=0.05, 1.91 Msun star  
  > "The gas is distributed with a Gaussian radial surface density distribution, centred at 74 au, with a FWHM of 17 au (cite: line_arks), and a vertical aspect ratio $h=0.05$." (Appendix 12CO radiative transfer models)
   - assumption: LTE, kinetic and excitation temperature 38 K at the belt centre decaying with exponent -0.14; mu = 14 or 2.3; radial and vertical velocities zero  
  > "The gas is assumed to be in local thermodynamic equilibrium, and we set the kinetic and excitation temperature at the belt centre to be 38 K" (Appendix 12CO radiative transfer models); "The radial and vertical velocities are set to zero." (Appendix 12CO radiative transfer models)
   - fitting: No fit to the data with these models, by design  
  > "While we do not attempt to fit the data with these models due to strong degeneracies between model parameters" (Appendix 12CO radiative transfer models)
   - validation: Simulations confirm the observed residual pattern matches pressure-gradient velocity deviations and not pure Keplerian rotation  
  > "Our simulations confirm that the observed pattern is consistent with velocity deviations due to the pressure gradient of a gas ring, and inconsistent with a purely Keplerian rotation pattern." (3.2 De-projected azimuthal velocity)

## Software

- **disc2radmc** : Parametric disc model and radiative-transfer images for the continuum arc fit; synthetic 12CO cubes for the kinematic tests  
  > "We start by simulating synthetic image cubes using DISC2RADMC (cite: Marino2022)." (Appendix 12CO radiative transfer models); "we used a parametric model to define the disc density distribution, produced a synthetic image using radiative transfer calculations" (2.2 Arc parametric fit to continuum emission)
- **Galario** : Fourier transform of the model image and likelihood against the visibilities  
  > "Fourier transformed the image and calculated the model likelihood using Galario (cite: galario)" (2.2 Arc parametric fit to continuum emission)
- **emcee** : Affine invariant MCMC sampling of the dust model posterior  
  > "sampled the posterior distribution using the Python package EMCEE (cite: emcee)" (2.2 Arc parametric fit to continuum emission)
- **BETTERMOMENTS** : Line-of-sight velocity (moment 1) map with the Gaussian method  
  > "using the package BETTERMOMENTS and the Gaussian method that fits a Gaussian line profile to each pixel" (3.1 2D velocity map)
- **EDDY** : Keplerian fit to the velocity map and annulus-by-annulus 3D velocity retrieval  
  > "We fitted a Keplerian model to this velocity map using the EDDY package (cite: eddy)" (3.1 2D velocity map); "To constrain and deproject the gas velocities as a function of radius, we used the EDDY package (cite: eddy)" (3.2 De-projected azimuthal velocity)
- **CASA** : simobserve task to simulate ALMA observations of the model cubes  
  > "using the task SIMOBSERVE in CASA (cite: casa)" (Appendix 12CO radiative transfer models)
- **tclean** : Imaging the simulated observations with Briggs weighting, robust 0.5 and a Keplerian mask  
  > "The simulated ALMA observations are then imaged using TCLEAN using a Briggs weighting, a robust parameter of 0.5, a Keplerian mask" (Appendix 12CO radiative transfer models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Axisymmetric component peak radius r0 | 70 | +/-1 | au | 2 | we find it is centred at $r_0=70\pm1$ au |
| Outer slope alpha_2 of the axisymmetric component | -6.5 | +/-0.3 | dimensionless | 2 | outer slope $\alpha_2=-6.5\pm0.3$ |
| Total dust mass | 0.233 | +/-0.004 (excludes opacity uncertainty) | Earth masses | 2 | The total dust mass is constrained to be $0.233\pm0.004\ M_{\oplus}$ |
| Arc peak radius r_c | 75 | +/-1 | au | 2 | the arc peak, $r_{\rm c}$, is centred at $75\pm1$ au |
| Arc azimuth phi_c (from SW ansa) | 28 | +10/-11 | degrees | 2 | $\phi_{\rm c}$, of $28^{+10}_{-11}$ |
| Arc radial width sigma_r | 1.0 | +1.2/-0.5 | au | 2 | with a standard deviation of $1.0^{+1.2}_{-0.5}$ au (a FWHM of $2.4^{+2.8}_{-1.2}$ au) |
| Arc radial FWHM | 2.4 | +2.8/-1.2 | au | 2 | with a standard deviation of $1.0^{+1.2}_{-0.5}$ au (a FWHM of $2.4^{+2.8}_{-1.2}$ au) |
| Arc radial width sigma_r 3-sigma upper limit | 5.4 | not stated | au | 2 | and a 3$\sigma$ upper limit of 5.4 au |
| Arc azimuthal width sigma_phi,2 (trailing side) | 59 | +/-14 | degrees | 2 | with a standard deviation of $59\pm14$ ($\sigma_{\phi,2}$) on the trailing side versus $13^{+12}_{-9}$ on the leading side ($\sigma_{\phi,1}$) |
| Arc azimuthal width sigma_phi,1 (leading side) | 13 | +12/-9 | degrees | 2 | with a standard deviation of $59\pm14$ ($\sigma_{\phi,2}$) on the trailing side versus $13^{+12}_{-9}$ on the leading side ($\sigma_{\phi,1}$) |
| Arc azimuthal FWHM | 85 | +18/-21 | degrees | 2 | to be $85^{+18}_{-21}$, confirming the wide azimuthal extension of this dust overdensity |
| Arc fraction of total dust mass | 13 | +/-1 | percent | 2 | the overall millimetre dust mass contribution of the arc is $13\pm1\%$ of the total dust mass of 0.23 $M_{\oplus}$ |
| Dust-derived inclination | 44.8 | +/-0.6 | degrees | 2 | consistent with those derived for the dust emission ($44.8\pm0.6\degree$ and $58.5\pm0.8\degree$, respectively) |
| Dust-derived position angle | 58.5 | +/-0.8 | degrees | 2 | consistent with those derived for the dust emission ($44.8\pm0.6\degree$ and $58.5\pm0.8\degree$, respectively) |
| 12CO radial emission peak | 73 | not stated | au | 1 | The $^{12}$CO emission profile, on the other hand, peaks at a radius of 73 au that is similar to the peak radius of large dust grains (74 au). |
| Millimetre dust radial peak | 74 | not stated | au | 1 | The $^{12}$CO emission profile, on the other hand, peaks at a radius of 73 au that is similar to the peak radius of large dust grains (74 au). |
| Radial FWHM of small (scattered light) dust | 12 | not stated | au | 1 | compared to the 12 au for the small and 22 au for the large dust components |
| Radial FWHM of large (millimetre) dust | 22 | not stated | au | 1 | compared to the 12 au for the small and 22 au for the large dust components |
| 13CO radial FWHM | 37 | not stated | au | 1 | The $^{13}$CO emission is less extended with a FWHM of 37 au compared to the $^{12}$CO |
| Position angle of the millimetre dust azimuthal peak | ~250 | not stated | degrees | 1 | peaks at a position angle (PA) of ${\sim}250\degree$ |
| Peak excess of the dust arc over average intensity beyond the arc (observed) | ~40 | not stated | percent | 1 | The peak excess is about ${\sim}40\%$ of the average intensity beyond the arc. |
| Keplerian fit position angle | 59.6 | <1% (likely underestimated) | degrees | 3 | The best-fit values are -3 mas for the RA offset, 20 mas for the Dec offset, 59.6 for the position angle, 43.8 for the inclination |
| Keplerian fit inclination | 43.8 | <1% (likely underestimated) | degrees | 3 | The best-fit values are -3 mas for the RA offset, 20 mas for the Dec offset, 59.6 for the position angle, 43.8 for the inclination |
| Keplerian fit stellar mass | 1.89 | <1% (likely underestimated) | Msun | 3 | 43.8 for the inclination, 1.89 $M_\odot$ for the stellar mass, and 7.86 km/s for the system line of sight velocity in the Barycentric reference frame |
| Keplerian fit systemic velocity (barycentric) | 7.86 | <1% (likely underestimated) | km/s | 3 | 43.8 for the inclination, 1.89 $M_\odot$ for the stellar mass, and 7.86 km/s for the system line of sight velocity in the Barycentric reference frame |
| Deviation of azimuthal velocity from Keplerian (as measured) | ~1 | not stated | percent of Keplerian speed | 4 | Overall, we find deviations of the order of 1% with the azimuthal velocity decreasing with radius faster than Keplerian. |
| Deviation from Keplerian speed towards 65 and 85 au after accounting for beam smearing (estimate) | ~2 | not stated | percent of Keplerian speed | 4 | closer to 2% the Keplerian speed towards 65 and 85 au |
| Upper limit on global radial and vertical velocities | <1 | not stated | percent of Keplerian speed | 4 | consistent with zero at all radii with upper limits below 1% of the Keplerian speed |
| Width of kinematic density profile for mu=2.3 relative to 13CO density distribution | ~3 | not stated | dimensionless | 5 | appears ${\sim}3$ times wider than the $^{13}$CO density distribution |
| Best-fit stellar mass of simulated Keplerian, mu=14 and mu=2.3 models (input 1.91 Msun) | 1.93, 1.93, 1.80 | not stated | Msun | 6 | The best-fit $M_{\star}$ for the Keplerian, and non-Keplerian $\mu=14$, and $\mu=2.3$ models was 1.93, 1.93 and 1.80 $M_{\odot}$ |

## Qualitative findings

- The arc is much less pronounced or absent in small grains (scattered light) and in CO gas  
  > "we conclude that the arc is much less pronounced or absent for small grains and gas" (abstract)
- First well-resolved non-Keplerian gas kinematics in a debris disc  
  > "This paper presents the first well-resolved non-Keplerian gas kinematics in a debris disc." (4.5 Non-Keplerian kinematics in debris discs)
- Eccentricity of the CO emission cannot be confirmed  
  > "Therefore, we cannot confirm this eccentricity in the CO emission." (2.1 Radial and azimuthal profiles)
- Millimetre-dust eccentricity can be neither confirmed nor ruled out  
  > "Therefore, we can neither confirm nor rule out that the millimetre emission is eccentric." (2.1 Radial and azimuthal profiles)

## Claim tuples

- H: Is the millimetre dust asymmetry in HD 121617 a narrow, azimuthally extended and asymmetric arc? | E: Parametric axisymmetric plus 2D-Gaussian arc model fitted to the 0.89 mm continuum visibilities with disc2radmc, Galario and emcee | R: Arc radial width ~1-5 au at 75 au, azimuthal FWHM 85 (+18/-21) deg, trailing side wider, 13 +/- 1% of the 0.233 Mearth dust mass | F: The arc is radially narrow, azimuthally extended and asymmetric | **supported**
- H: Is the arc also present in small grains (scattered light) and in the CO gas? | E: Radial and azimuthal profiles from SPHERE, ARKS continuum and 12CO/13CO moment 0 and moment 8 images | R: No significant azimuthal asymmetry in 12CO and 13CO beyond a four-lobed shear modulation; at most a 2-sigma, ~20% excess in self-subtracted scattered light | F: The arc is much less pronounced or absent for small grains and gas (optical depth prevents ruling out a hidden gas overdensity) | **supported**
- H: Does the CO gas show non-Keplerian rotation? | E: Keplerian fit to the 12CO velocity map, EDDY de-projection of azimuthal velocity, comparison with simulated Keplerian and pressure-supported observations | R: Azimuthal velocity falls faster with radius than Keplerian (~1-2%), super-Keplerian inside and sub-Keplerian outside the ring; radial and vertical velocities consistent with zero | F: Deviations are consistent with the pressure gradient of a narrow gas ring and inconsistent with purely Keplerian rotation | **supported**
- H: Do the kinematics reveal whether the gas is primordial (H2-dominated) or secondary (CO-dominated)? | E: Retrieve the gas density profile from the Keplerian deviations for mu=14 and mu=2.3 and compare with the 13CO density profile | R: mu=14 reproduces the 13CO density profile; mu=2.3 gives a profile ~3 times wider, which may still be allowed if CO photodissociation changes the CO distribution | F: The kinematics alone cannot distinguish primordial from secondary gas, though a CO-dominated gas is preferred if 13CO traces the total gas | **partially**
- H: What produces the dust arc: a vortex, a giant collision or planet-disc interaction via mean-motion resonances? | E: Qualitative comparison of the measured arc properties and gas and small-grain distributions with model expectations from the literature | R: Properties are roughly consistent with a vortex if gas mass is >~20 Mearth; a giant collision alone is unlikely to explain all observables; resonance trapping by a migrating planet remains possible | F: Vortex (requiring primordial gas) or planet-disc resonances are viable; testing needs future clump-rotation and gas-mass measurements | **partially**

## Reasoning

- Why this data: Low inclination and high CO flux make HD 121617 the best ARKS target for dust/gas asymmetries and kinematics; only the high-velocity-resolution 12CO cube is suitable for kinematics  
  > "HD 121617’s low inclination and high CO flux make it the ideal ARKS target to study dust and gas asymmetries, as well as gas kinematics in exoKuiper belts." (Introduction); "This means that only the $^{12}$CO data is suitable for a detailed analysis of its kinematics." (2 Dust and gas distribution)
- Why this method: Two-component parametric arc model chosen for flexibility to constrain radial and azimuthal widths  
  > "This parametrisation offers adequate flexibility to constrain the radial and azimuthal widths of the arc." (2.2 Arc parametric fit to continuum emission)
- Alternative: Elevated emission surface in the Keplerian model rejected: fitted heights consistent with zero, so midplane assumed  
  > "We also explored models with an elevated emission surface as commonly found in protoplanetary discs (cite: Teague2018), but we found height values consistent with zero." (3.1 2D velocity map)
- Alternative: Giant-collision origin of the arc disfavoured by trailing-side asymmetry and absence of small-grain overdensity  
  > "However, the fact that it is asymmetric, with the trailing side being more extended or denser, is inconsistent with the collisional scenario." (4.4 A giant collision as the origin of the arc)
- How they decided it was enough: No best-fit gas model attempted because of degeneracies between beam, optical depth, photodissociation and density/sound speed  
  > "we do not attempt to find a perfect fit between the kinematically derived density and the emission profile" (3.3 Retrieving the radial density profile)
- Limitation (authors): Kinematic fit uncertainties likely underestimated (pixel correlation ignored)  
  > "The uncertainties on these values extracted by EDDY are below 1%, but they are likely underestimated as they do not take into account the spatial correlation between pixels." (3.1 2D velocity map)
- Limitation (authors): Dust mass uncertainty excludes opacity uncertainty  
  > "we note that the small uncertainties do not include the uncertainties in the assumed dust opacity" (2.2 Arc parametric fit to continuum emission)
- Limitation (authors): Beam smearing biases the extracted azimuthal velocity profile, so deviations are probably underestimated  
  > "an important caveat to note is that the true azimuthal velocity profile is likely steeper than the extracted one because the latter is affected by beam smearing" (3.3 Retrieving the radial density profile)
- Limitation (authors): Optically thick CO cannot rule out a hidden gas-density asymmetry  
  > "we cannot rule out the presence of an asymmetry in the gas density distribution similar to that seen in the millimetre-sized dust" (2.1 Radial and azimuthal profiles)
- Caveat (inferred, ours): Arc parameters depend on a single assumed dust opacity and size distribution; MCMC priors and convergence are not reported
- Caveat (inferred, ours): Kinematic deviations of 1-2% are near the sensitivity limit and are sensitive to the adopted stellar mass (1.89 vs 1.91 Msun shifts the pressure maximum from 75 to 83 au)
- Caveat (inferred, ours): Density retrieval assumes midplane emission, an ISM-like power-law temperature from the 13CO fit and no radial or vertical flows, so the mu constraint is model dependent
- Caveat (inferred, ours): Simulated models were not fitted, so the pressure-support interpretation is qualitative rather than a statistical test

## Reproducibility

- Data public (paper): ARKS images (continuum, CO cubes, SPHERE) released on the ARKS Harvard Dataverse; no raw-data or calibration recipe given  
  > "The ARKS data used in this paper and others can be found in the" (Data availability); "The continuum image used in this work can be found within the" (Data availability); "The CO gas images used in this work can be found within the" (Data availability)
- Products in archive: _not stated_
- Code: disc2radmc is public on GitHub; no analysis scripts for this paper stated  
  > "github.com/SebaMarino/disc2radmc" (2.2 Arc parametric fit to continuum emission)
- Missing: MCMC priors, walker counts and convergence settings
- Missing: BETTERMOMENTS and EDDY run settings (masks, bounds, radial grid)
- Missing: Continuum image details (robust, beam) and calibration/CASA version in this paper (deferred to ARKS I and IV)
- Missing: Details of the simulated cube set-up (noise, mask, antenna configurations)
- Data volume (inferred): Released CLEAN images and cubes are likely a few GB; reprocessing raw Band 7 measurement sets would be tens of GB
- Score (inferred): 3/5, Final images are public and the kinematic and arc-fit methods are described with numeric results, but priors, run settings and imaging details are deferred to companion ARKS papers or missing
- Rediscovery candidate: yes, Public ARKS images/cubes, named packages (BETTERMOMENTS, EDDY, disc2radmc, Galario, emcee) and numeric outputs (arc parameters, Keplerian fit values) allow redoing the main fits and velocity analysis

## Links

- Method: (cite: overview_arks) (ARKS overview: imaging, stellar properties, and the visibility-fitting approach and dust model reused here)
- Method: (cite: gas_arks) (ARKS gas paper: CO cube imaging, robust 0.5 cubes and pixel size)
- Method: (cite: rad_arks) (Radial profile extraction approach and the double power-law dust model)
- Method: (cite: scat_arks) (Re-reduction of the SPHERE image and self-subtraction method)
- Method: (cite: Marino2022) (disc2radmc code used for the models and simulations)
- Companion: (cite: line_arks) (Companion ARKS paper on CO line modelling: temperature profile, mu and CO mass)
- Companion: (cite: vortex_arks) (Companion ARKS paper with hydrodynamical vortex simulations and gas-mass constraints)
- Companion: (cite: asym_arks) (ARKS paper reporting asymmetries in 10/24 belts including the HD 121617 arc)
- Companion: (cite: Perrot2023) (Earlier SPHERE scattered-light study of HD 121617)
- Related: ARKS (ALMA Large Program 2022.1.00338.L)
- Related: REASONS survey (Matra2025)

## Checks

```json
{
 "quotes": 148,
 "quotes_ok": 148,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 30,
 "numeric_problems": 0,
 "fill": {
  "facts": 114,
  "stated": 87,
  "rate": 0.763
 },
 "evidence_ok": true
}
```
