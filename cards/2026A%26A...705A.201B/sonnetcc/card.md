# The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): VII. Optically thick gas with broad CO gaussian local line profiles in the HD 121617 disc

`2026A&A...705A.201B` | Astronomy and Astrophysics 2026 | first author: Brennan, A. | arXiv: 2601.11824 | DOI: 10.1051/0004-6361/202556566

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: Are the 12CO and 13CO lines in the HD 121617 debris disc optically thick, and what do local line profiles imply for CO mass, temperature and mean molecular weight  
  > "We model local CO line profiles in the HD 121617 debris disc to investigate optical depth, CO mass, and temperature." (abstract)
- Target **HD 121617**: coordinates _not stated_; z/distance 117.9 ± 0.5 pc  
  > "HD 121617 is an A1V main-sequence star" (Introduction); "at a distance of 117.9 $\pm$ 0.5 pc (cite: Gaia(2023))" (Introduction); distance from Gaia (cite: Gaia(2023))  
  > "HD 121617 is an A1V main-sequence star" (Introduction); "at a distance of 117.9 $\pm$ 0.5 pc (cite: Gaia(2023))" (Introduction)

## Data provenance

- ALMA projects: 2022.1.00338.L, 2012.1.00142.S, 2012.1.00198.S, 2015.1.01260.S, 2016.1.00104.S, 2016.1.00195.S, 2016.1.00907.S, 2017.1.00167.S, 2017.1.00825.S, 2018.1.01222.S, 2019.1.00189.S
- bands: Band 7 (continuum windows at 344 and 333.2 GHz; CO windows near 345.8 and 331.3 GHz)  
  > "We observed HD 121617 in Band 7 during Cycle 9 as part of the ALMA survey ARKS large programme" (Observations)
- frequencies and spectral setup: 4 spectral windows: 2 continuum (344, 333.2 GHz; 31.256 MHz resolution); 12CO J=3-2 window at 345.796 GHz (30.518 kHz = 26 m/s, 58.59 MHz bandwidth); 13CO J=3-2 window at 331.3 GHz (975.563 kHz = 884 m/s, 1875 MHz bandwidth)  
  > "The correlator was configured with four spectral windows." (Observations); "within a window centred at 345.796 GHz, a spectral resolution of 30.518 kHz" (Observations); "within a window centred at 331.3 GHz, a resolution of 975.563 kHz" (Observations)
- continuum bandwidth: 1875 MHz per continuum window  
  > "Two windows were allocated for observing the dust continuum centred at 344 GHz and 333.2 GHz, with a bandwidth of 1875 MHz" (Observations)
- arrays: C-3 and C-6 antenna configurations  
  > "using the C-3 and C-6 antenna configurations" (Observations)
- configurations: C-3 and C-6  
  > "using the C-3 and C-6 antenna configurations" (Observations)
- baselines: _not stated_
- angular resolution: Beam 0.12 x 0.11 arcsec (12CO, PA -76.5 deg); 0.13 x 0.12 arcsec (13CO, PA -72.6 deg), robust = 0.5  
  > "0.12 $\times$ 0.11" (Table 1); "Note that the quoted beam sizes and RMS noise levels are specifically for robust = 0.5." (Table 1)
- max recoverable scale: _not stated_
- sensitivity: RMS 4.7 mJy/beam (12CO, 26 m/s channels); 14.8 mJy/beam (13CO, 884 m/s channels)  
  > "RMS noise level (mJy beam$^{-1}$) | $4.7$ | $14.8$" (Table 1)
- time on source: _not stated_
- observing dates: October 2022 to May 2023 (Cycle 9)  
  > "Observations were conducted between October 2022 and May 2023" (Observations)
- pi or archival as stated: ARKS large programme 2022.1.00338.L, PI S. Marino  
  > "project number 2022.1.00338.L, PI: S. Marino" (Observations)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- External data: Distance to HD 121617: 117.9 ± 0.5 pc  
  > "We fixed the distance parameter to the known literature value of 117.9" (Observational results) [from Gaia (cite: Gaia(2023))]
- External data: Stellar luminosity of 14 Lsun used for blackbody temperature estimate  
  > "given a stellar luminosity of 14 L$_{\odot}$ (cite: Matra(2025))" (Data comparison) [from (cite: Matra(2025))]
- External data: Integrated line fluxes 3.6 ± 0.4 Jy km/s (12CO) and 1.5 ± 0.2 Jy km/s (13CO)  
  > "For HD 121617, they derived an integrated line flux of 3.6 $\pm$ 0.4 Jy km s$^{-1}$ for $^{12}\textrm{CO}$" (Observational results) [from (cite: Sorcha_arks)]
- External data: Continuum radial profile from frank (non-parametric fit)  
  > "with the full procedure detailed in (cite: Yinuo_arks)" (Observational results) [from (cite: Yinuo_arks)]
- External data: ISM 12CO/13CO abundance ratio of ~77  
  > "ISM ratio of $\sim77$ (cite: Wilson(1994))" (Introduction) [from (cite: Wilson(1994))]
- External data: CO/H2 ratio of 1e-4 assumed for primordial-shielding case  
  > "assuming a CO/H$_{2}$ ratio of $1\times10^{-4}$ (cite: Kevin_Smith(2025))" (6.1 CO mass) [from (cite: Kevin_Smith(2025))]
- External data: CO self-shielding functions from the Leiden photodissociation database  
  > "We used the shielding functions from the Leiden database found at" (Footnote 5) [from (cite: Visser(2009))]
- External data: Earlier CO mass estimates (Moor 2017; Cataldi 2023) used for comparison  
  > "Additionally, (cite: Cataldi(2023)) reports a CO mass of" (6.1 CO mass) [from (cite: Moor(2017)); (cite: Cataldi(2023))]
- Simulation/model as data: RADMC-3D synthetic CO cubes (optically thin 12CO model; fitted 13CO model; 13CO model rescaled for 12CO) compared with the ARKS cubes  
  > "we created a full radiative transfer model of the CO emission using" (3D radiative transfer modelling)

## Processing

### Calibration

- pipeline or manual: Standard ALMA reduction with CASA; details deferred to ARKS papers  
  > "The calibration and imaging were done using the standard ALMA reduction tool Common Astronomy Software Applications (CASA version 6.4.1.12)." (Observations); "Full details on the observation setup, calibration, and imaging can be found in (cite: Seba_arks) and (cite: Sorcha_arks)." (Observations)
- casa version: CASA 6.4.1.12  
  > "Common Astronomy Software Applications (CASA version 6.4.1.12)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (CASA) for continuum image and line cubes  
  > "to extract the continuum image and the spectral cubes of different lines from the calibrated visibilities" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust = 0.5  
  > "task was used with Briggs weighting, and a robust parameter of 0.5" (Observations)
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
- final beam: 12CO 0.12 x 0.11 arcsec, PA -76.5 deg; 13CO 0.13 x 0.12 arcsec, PA -72.6 deg  
  > "0.12 $\times$ 0.11" (Table 1)
- final rms: 12CO 4.7 mJy/beam; 13CO 14.8 mJy/beam  
  > "RMS noise level (mJy beam$^{-1}$) | $4.7$ | $14.8$" (Table 1)

### Inherited from earlier work

- Observation setup, calibration and imaging details  
  > "Full details on the observation setup, calibration, and imaging can be found in (cite: Seba_arks) and (cite: Sorcha_arks)." (Observations) [from (cite: Seba_arks); (cite: Sorcha_arks)]
- Shifting emission to systemic velocity for velocity-integrated intensity maps  
  > "as described in (cite: Sorcha_arks)" (Observational results) [from (cite: Sorcha_arks)]
- Creation of velocity integrated and peak intensity maps  
  > "For further details on the creation of velocity integrated intensity and peak intensity maps, see (cite: Sorcha_arks)." (Observational results) [from (cite: Sorcha_arks)]
- Integrated line fluxes from spectrospatially stacked spectra with bootstrapped errors  
  > "In (cite: Sorcha_arks), the integrated line flux is calculated from the spectrospatially stacked spectra" (Observational results) [from (cite: Sorcha_arks)]
- Continuum radial profile (frank) procedure  
  > "with the full procedure detailed in (cite: Yinuo_arks)" (Observational results) [from (cite: Yinuo_arks)]
- Per-pixel/channel uncertainty scaling for spectrospatial correlation in the 13CO cube fit  
  > "to account for spectrospatial correlation (cite: Marino(2016))" (13CO RADMC-3D model) [from (cite: Marino(2016))]

### Not stated but needed to reproduce (our reading)

- Which of the 11 listed ALMA projects were actually used for the analysis (only 2022.1.00338.L is described)
- Line-free channels and continuum subtraction method for the CO cubes
- tclean cell size, image size, deconvolver, masks and cleaning threshold for the CO cubes
- Velocity-resampling and channel width of the delivered cubes beyond the 26 and 884 m/s resolutions
- Time on source, baseline range, maximum recoverable scale, flux and bandpass calibrators and any self-calibration
- Prior bounds for the emcee fits (velocity map, toy model, 13CO RADMC-3D)
- Likelihood definition for the velocity-map and toy-model fits
- RADMC-3D set-up: CO molecular data file, collisional rates, photon counts, grid, vertical and radial temperature profile for the optically thin model, treatment of the 13CO abundance
- How the 13CO RADMC-3D model was convolved spectrally for 884 m/s channels and the number of walkers, steps and burn-in for the 13CO cube fit
- Exact eddy and gofish settings (annulus alignment options, uncertainty estimates in stacked spectra)
- Code used for the toy model and analytic shear calculations is not released

## Analysis recipe

1. **Make moment, peak-intensity and linewidth maps**: Velocity-integrated intensity from the cube shifted to systemic velocity; peak intensity with the bettermoments quadratic method; linewidth map as integrated intensity divided by peak intensity converted to FWHM  
  > "This method identifies the channel with the peak intensity, fits a quadratic curve to the pixel as well as its two neighbouring pixels, and calculates the associated uncertainty." (Observational results); "generated by dividing the velocity integrated intensity map by the peak intensity map and converting it to FWHM, assuming a Gaussian line profile shape" (Observational results)
   - software: bettermoments, CASA
   - parameter: Integrate pixels with peak emission above 4 sigma; systemic velocity 7851 m/s  
  > "The shifted cube was then integrated along the velocity axis for all pixels with peak emission above a 4$\sigma$ threshold." (Observational results); "shifting the emission to the systemic velocity (7851 m s$^{-1}$)" (Observational results)
   - assumption: Gaussian line profile shape for the FWHM conversion  
  > "assuming a Gaussian line profile shape" (Observational results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive radial intensity profiles of CO and continuum**: Gas profiles by stacking spectra in annuli assuming Keplerian rotation then integrating; continuum profile with frank  
  > "which divides the disc gas emission into annuli and spectrospatially stacks the spectra within each annulus, assuming a Keplerian rotation pattern for the disc" (Observational results); "Then, we integrated over each annulus’s stacked spectrum to report integrated line intensity as a function of radius." (Observational results)
   - software: gofish, frank
   - assumption: Keplerian rotation for stacking  
  > "assuming a Keplerian rotation pattern for the disc" (Observational results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Keplerian model to the 12CO velocity map**: Velocity map from bettermoments Gaussian method (pixels below 5 sigma masked), fitted with a thin-disc Keplerian model for PA, inclination, stellar mass, systemic velocity, RA and Dec offsets  
  > "The velocity map was then produced using the Gaussian method, where a Gaussian is fitted to each pixel" (Observational results); "where all pixels with peak intensities below 5$\sigma$ are masked" (Observational results)
   - software: bettermoments, emcee
   - parameter: Distance fixed at 117.9 pc; 1500 steps, 32 walkers, 500 burn-in steps  
  > "We fixed the distance parameter to the known literature value of 117.9" (Observational results); "for 1500 steps with 32 walkers after an additional burn-in period of 500 steps" (Observational results)
   - assumption: Geometrically thin disc  
  > "assuming a geometrically thin disc" (Observational results)
   - fitting: emcee affine-invariant ensemble sampler with uniform priors; likelihood not stated  
  > "We employed uniform priors with well-defined boundaries, ensuring they were sufficiently distanced from the best-fit values." (Observational results)
   - validation: Compared with continuum geometry and stellar-model mass; convergence assessed visually  
  > "The PA, inclination, RA, and DEC offsets are consistent with those measured for the continuum" (Observational results); "and visually assessed convergence" (Observational results)
4. **Extract local line profiles in thin annuli**: Align spectra across azimuth to the stellar peak velocity using the Keplerian cos(phi) dependence, then average within 0.02 arcsec annuli  
  > "We aligned the spectra across different azimuths to the same (stellar) peak velocity" (4.1 Local line profile extraction); "Next, we averaged the aligned spectra to generate local spectral line profiles" (4.1 Local line profile extraction)
   - software: eddy
   - parameter: Annulus width 0.02 arcsec; inclination, PA, RA and Dec offsets from the Keplerian fit (Table 2)  
  > "annuli of $0.02\ensuremath{''}$ width" (4.1 Local line profile extraction); "We also adopted the inclination, PA, RA, and DEC-offset values from Table" (4.1 Local line profile extraction)
   - assumption: Local line shape independent of azimuth, admitted not to hold in the data  
  > "this method assumes the local spectral line shape at a given radius is independent of azimuth, which is not the case in our dataset" (4.1 Local line profile extraction)
   - fitting: _not stated_
   - validation: Profiles checked as function of azimuth before averaging; approximately Gaussian  
  > "The profiles are approximately Gaussian in shape, even before azimuthal averaging." (4.1 Local line profile extraction)
5. **Fit toy radiative-transfer model to local 12CO and 13CO profiles**: Simultaneous fit of 12CO and 13CO local profiles per annulus (0.32 to 0.98 arcsec) with I = B(Texc)(1-exp(-tau)), Gaussian tau profile with thermal width set by Tkin, convolved with Gaussian instrumental response  
  > "the emission is parametrised primarily by: the $^{12}\textrm{CO}$ optical depth, the $^{13}\textrm{CO}$ optical depth" (4.2 Local line profile modelling); "across each annulus from $0.32\ensuremath{''}$ to $0.98\ensuremath{''}$, with each annulus having a width of" (4.2 Local line profile modelling)
   - software: emcee
   - parameter: Free: tau0 for each isotopologue, Texc, Tkin, systemic velocity, and error-scaling factors f12 and f13  
  > "which are constant values by which we multiplied the uncertainties to account for the inaccuracy of error bars in the local spectra of" (4.2 Local line profile modelling)
   - assumption: Homogeneous gas filling the beam, thermal Doppler broadening, Boltzmann level populations at fitted Texc, same Tkin and Texc for both isotopologues  
  > "as arising from a homogeneous parcel of gas filling the beam in the absence of significant background radiation" (4.2 Local line profile modelling); "we calculate the level populations following the Boltzmann distribution, assuming a given excitation temperature, which we fitted for" (4.2 Local line profile modelling)
   - fitting: Bayesian MCMC as in the velocity map fit; priors not stated  
  > "We fitted the emission line profiles using a Bayesian MCMC approach" (4.2 Local line profile modelling)
   - validation: Best-fit model compared with data at 73 au; 13CO linewidth not reproduced, so model judged incomplete  
  > "fails to reproduce the observed linewidth" (4.2 Local line profile modelling)
6. **Optically thin RADMC-3D 12CO model compared qualitatively with data**: Gaussian CO surface density (r_peak 73 au, sigma 21 au, fixed from radial profile), Gaussian vertical profile in hydrostatic equilibrium, Keplerian velocity; mu, Tpeak and MCO adjusted by hand against FWHM and peak-intensity azimuthal profiles and disc-integrated spectrum  
  > "Since we did not formally fit the cube, these parameters were adjusted to achieve the best qualitative agreement with key features of our dataset." (5.1.2 Data comparison); "We assumed a Gaussian vertical profile with a vertically constant temperature, as expected from hydrostatic equilibrium." (5.1.1 Model assumptions)
   - software: RADMC-3D, emcee
   - parameter: Model cube 678 x 678 pixels of 0.0225 arcsec with 1182 channels of 13 m/s; spectral Gaussian FWHM = 2 x channel width; beam 0.12 x 0.11 arcsec  
  > "678 $\times$ 678 $0.0225\ensuremath{''}$ pixels with 1182 13 m s$^{-1}$ channels" (5.1.1 Model assumptions)
   - parameter: Azimuthal sections of 15 deg for data; Gaussian fits with 2000 steps and 100 burn-in  
  > "The fitting procedure consists of 2000 steps with a burn-in period of 100 steps due to faster convergence." (5.1.2 Data comparison)
   - assumption: LTE level populations; Keplerian rotation with 1.89 Msun  
  > "For simplicity, we assumed local thermodynamic equilibrium (LTE) to calculate the CO level populations." (5.1.1 Model assumptions)
   - fitting: Qualitative adjustment of three parameters; Gaussian FWHM and peak intensity fitted per azimuth with MCMC  
  > "We varied three parameters in our" (5.1.2 Data comparison)
   - validation: Model rejected as it needs unrealistically high temperature, cannot make the X-shape, and overestimates 13CO linewidths  
  > "it requires unrealistically high temperatures, cannot account for the X-shape" (5.1.2 Data comparison)
7. **Fit optically thick RADMC-3D model to the 13CO cube**: MCMC fit of 13CO cube with free R, delta R, T at 73 au, temperature power-law index beta, mu, CO mass, inclination, PA and stellar mass  
  > "$\mu$, the mean molecular weight" (5.2.1 13CO RADMC-3D model); "was carried out using MCMC, with an affine-invariant ensemble sampler implemented in the emcee package" (5.2.1 13CO RADMC-3D model)
   - software: RADMC-3D, emcee
   - parameter: Per-pixel/channel noise = cube RMS times sqrt(pixels per beam and channels per effective bandwidth)  
  > "the uncertainty per pixel and channel assumed to be equal to the cube’s RMS multiplied by the square root of the number of pixels per beam and the number of channels per effective bandwidth" (5.2.1 13CO RADMC-3D model)
   - assumption: LTE so kinetic temperature equals excitation temperature; Gaussian radial CO distribution; distance 117.9 pc  
  > "assuming LTE allows us to break this degeneracy by assuming that the kinetic temperature is the same as the excitation temperature (38 K)" (5.2.1 13CO RADMC-3D model)
   - fitting: emcee affine-invariant sampler; priors and chain length not stated  
  > "was carried out using MCMC, with an affine-invariant ensemble sampler implemented in the emcee package" (5.2.1 13CO RADMC-3D model)
   - validation: Residuals of moment maps and channel maps compared with data  
  > "is a very good fit to the data" (5.2.1 13CO RADMC-3D model)
8. **Test the 13CO model on 12CO by rescaling the mass**: Run RADMC-3D with the 13CO best-fit parameters and CO mass scaled by the ISM ratio 77  
  > "We scaled the mass by the ISM abundance ratio of 77" (5.2.2 12CO RADMC-3D model)
   - software: RADMC-3D
   - parameter: ISM 12CO/13CO = 77  
  > "We scaled the mass by the ISM abundance ratio of 77" (5.2.2 12CO RADMC-3D model)
   - assumption: ISM isotopologue abundance ratio applies  
  > "We, however, caution that different total CO masses/abundance ratios may also fit the data" (5.2.2 12CO RADMC-3D model)
   - fitting: _not stated_
   - validation: Residual maps inspected; reproduces the bulk of the 12CO emission except non-Keplerian structure  
  > "the model reproduces the data reasonably well given that the mass was simply scaled" (5.2.2 12CO RADMC-3D model)
9. **Convert to total CO mass and test CO photodissociation lifetime**: Scale 13CO mass by 77 to total CO; compute vertical CO column density from the 3D model and the self-shielding lifetime against the ISRF  
  > "from photodissociation from the ISRF experienced by a CO molecule in the midplane along the vertical direction (cite: Visser(2009))" (6.1 CO mass)
   - parameter: CO/H2 = 1e-4 for the primordial-shielding case  
  > "assuming a CO/H$_{2}$ ratio of $1\times10^{-4}$ (cite: Kevin_Smith(2025))" (6.1 CO mass)
   - assumption: CO self-shielding only (no other shielding species)  
  > "Assuming CO is self-shielding only (i.e. absence of other shielding species)" (6.1 CO mass)
   - fitting: _not stated_
   - validation: Compared with literature CO masses from Moor 2017 and Cataldi 2023  
  > "This value is higher than previous estimates in the literature." (6.1 CO mass)
10. **Analytical estimate of Keplerian shear broadening**: Gradient of projected Keplerian velocity in sky coordinates multiplied by beam size; convolved with Gaussian of 26 m/s instrumental width to predict azimuthal FWHM  
  > "evaluate this velocity difference by multiplying the gradient by the beam size in au" (9 Keplerian shear)
   - parameter: r_orb 73 au; M*, i, beam from HD 121617 ARKS data  
  > "we fix $r_{\rm orb}$ to 73 au as in our peak intensity annulus of HD 121617" (9 Keplerian shear)
   - assumption: Vertically thin disc; gradient constant across the beam; Keplerian velocity field  
  > "We assume that the disc is vertically thin (2D)" (9 Keplerian shear)
   - fitting: _not stated_
   - validation: Compared with data FWHM and RADMC-3D azimuthal pattern  
  > "compares well with `RADMC-3D` models and ARKS observations of the HD 121617 system" (9 Keplerian shear)

## Software

- **CASA** 6.4.1.12: Calibration and imaging (tclean)  
  > "The calibration and imaging were done using the standard ALMA reduction tool Common Astronomy Software Applications (CASA version 6.4.1.12)." (Observations)
- **tclean** : Continuum image and line cubes with Briggs weighting, robust 0.5  
  > "task was used with Briggs weighting, and a robust parameter of 0.5" (Observations)
- **bettermoments** : Peak intensity (quadratic) and velocity (Gaussian) maps  
  > "The velocity map was then produced using the Gaussian method, where a Gaussian is fitted to each pixel" (Observational results)
- **gofish** : Radial profiles by Keplerian stacking of spectra in annuli  
  > "which divides the disc gas emission into annuli and spectrospatially stacks the spectra within each annulus" (Observational results)
- **frank** : Continuum radial profile (procedure in Yinuo_arks)  
  > "with the full procedure detailed in (cite: Yinuo_arks)" (Observational results)
- **eddy** : Aligning spectra to a common velocity for local line profiles  
  > "We aligned the spectra across different azimuths to the same (stellar) peak velocity" (4.1 Local line profile extraction)
- **emcee** : MCMC sampling for velocity map, toy model and 13CO RADMC-3D fits  
  > "we used an affine-invariant ensemble sampler implemented through the" (Observational results)
- **RADMC-3D** : 3D radiative transfer models of CO cubes  
  > "Our model takes an assumed 3D CO density, temperature, and velocity structure and solves the radiative transfer equation to produce a simulated CO line emission cube." (3D radiative transfer modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO and 13CO radial detection extent | ~45 au to 125 au | not stated | au | 2 | are detected between $\sim$45 au and 125 au |
| Radial intensity peaks (13CO, 12CO, continuum) | ~72, ~73, ~75 | not stated | au | 2 | The $^{13}\textrm{CO}$ emission peaks at $\sim$72 au, $^{12}\textrm{CO}$ at $\sim$73 au and the continuum at $\sim$75 au. |
| Position angle (12CO velocity map Keplerian fit) | 59.6 | 0.01 | deg | 3 | Position angle (deg) / 59.6 $\pm$ 0.01 |
| Inclination (Keplerian fit) | 43.8 | 0.02 | deg | 3 | Inclination (deg) / 43.8 $\pm$ 0.02 |
| Stellar mass (Keplerian fit) | 1.89 | 0.001 | Msun | 3 | Stellar mass (M$_{\odot}$) / 1.89 $\pm$ 0.001 |
| System velocity v_BARY (Keplerian fit) | 7860 | 1 | m/s | 3 | $v_{\textrm{BARY}}$ (m s$^{-1}$) / 7860 $\pm$ 1 |
| 12CO local line FWHM at 0.61-0.63 arcsec | ~1092 | not stated | m/s | 4 | displaying a full width half maximum (FWHM) of $\sim1092$ m s$^{-1}$ |
| 12CO optical depth at line centre (toy model) | 0.50 | +0.13/-0.33 | dimensionless | 5 | $^{12}\textrm{CO}$ $\tau_{0}$ / $0.50_{-0.33}^{+0.13}$ |
| 13CO optical depth at line centre (toy model) | 0.30 | +0.12/-0.32 | dimensionless | 5 | $^{13}\textrm{CO}$ $\tau_{0}$ / $0.30_{-0.32}^{+0.12}$ |
| Excitation temperature (toy model) | 80 | +66/-14 | K | 5 | T$_{\textrm{exc}}$ (K) / $80_{-14}^{+66}$ |
| Kinetic temperature (toy model) | 600 | +38/-27 | K | 5 | T$_{\textrm{kin}}$ (K) / $600_{-27}^{+38}$ |
| Optically thin RADMC-3D model: peak optical depth, Tpeak, mu, CO mass | ~0.11; 380 K; 28; 1e-3 Mearth | not stated | dimensionless; K; dimensionless; Mearth | 6 | We find that an optically thin model with a peak optical depth of $\sim$0.11, $T_{\rm peak} = 380$ K, $\mu = 28$ (CO dominated), and $M_{\rm CO} = 10^{-3}$ M$_{\oplus}$ reproduces many key features of the data. |
| Peak radius R of 13CO Gaussian surface density | 74.4 | +0.2/-0.2 | au | 7 | $R$ (au) / $74.4_{-0.2}^{+0.2}$ |
| FWHM of 13CO Gaussian surface density | 17.3 | +0.9/-0.9 | au | 7 | $\Delta R$ (au) / $17.3_{-0.9}^{+0.9}$ |
| Temperature at 73 au (13CO model) | 38.1 | +1.3/-1.2 | K | 7 | $T_{73\ \mathrm{au}}$ (K) / $38.1_{-1.2}^{+1.3}$ |
| Temperature power-law index beta | -0.14 | +0.07/-0.07 | dimensionless | 7 | $\beta$ / $-0.14_{-0.07}^{+0.07}$ |
| Mean molecular weight mu | 12.6 | +1.3/-1.1 | dimensionless | 7 | We constrain the mean molecular weight to $12.6_{-1.1}^{+1.3}$, dependent on model assumptions. |
| log 13CO mass | -2.7 | +0.2/-0.1 | log10(Mearth) | 7 | $\log M_{^{13}\mathrm{CO}}$ (M$_\oplus$) / $-2.7_{-0.1}^{+0.2}$ |
| Inclination from 13CO cube fit | 44.4 | +0.2/-0.2 | deg | 7 | $i$ ($^\circ$) / $44.4_{-0.2}^{+0.2}$ |
| Stellar mass from 13CO cube fit | 1.915 | +0.009/-0.009 | Msun | 7 | $M_\star$ (M$_\odot$) / $1.915_{-0.009}^{+0.009}$ |
| 13CO mass (best-fit RADMC-3D) | 2e-3 | not stated | Mearth | 7 | a $^{13}$CO mass of $2 \times 10^{-3}$ M$_{\oplus}$ |
| 13CO peak optical depth of best-fit model | 26 | not stated | dimensionless | 7 | The best-fit model is optically thick, with a peak optical depth of 26 |
| 12CO peak optical depth of rescaled model | 3658 | not stated | dimensionless | 8 | leading to a peak optical depth for the $^{12}$CO model of 3658 |
| Total CO mass (13CO mass x 77) | 1.48e-1 | not stated | Mearth | 9 | which corresponds to a total CO mass of $1.48 \times 10^{-1}$ M$_{\oplus}$ assuming an interstellar |
| Vertical CO column density at disc radial peak | ~2e19 | not stated | cm^-2 | 9 | which gives a vertical column density of $\sim$ $2\times 10^{19}$ cm$^{-2}$ at the radial peak of the disc |
| CO lifetime with self-shielding only | ~0.07 | not stated | Myr | 9 | we find a CO lifetime of $\sim$0.07 Myr |
| Observed 12CO/13CO integrated intensity ratio at peak surface density | ~2.5 | not stated | dimensionless | 0 | integrated line intensity ratio of $\sim$2.5 at the peak surface density |
| Keplerian shear line broadening (analytic) | ~300-700 | not stated | m/s | 10 | we find Keplerian shear should produce broadening of $\sim300-700$ m s$^{-1}$ |

## Qualitative findings

- Velocity-integrated intensity and linewidth maps show an azimuthal X-shape at about +-45 and +-135 deg, attributed to Keplerian shear plus high optical depth  
  > "both showing an azimuthal X-shaped pattern, which we attribute to the azimuthal dependence of Keplerian shear, combined with high optical depth" (Conclusions)
- Azimuthally averaged profiles look Gaussian regardless of optical depth, so profile shape cannot separate thin from thick emission  
  > "Keplerian shear causes azimuthally averaged line profiles to appear Gaussian regardless of optical depth" (abstract)
- Both CO isotopologues are optically thick; C18O may also be optically thick in CO-rich debris discs  
  > "in the HD 121617 gas-bearing debris disc are optically thick, confirming literature expectations" (Conclusions)

## Claim tuples

- H: Do broad Gaussian local CO line profiles indicate optically thin gas? | E: Aligned and stacked spectra in 0.02 arcsec annuli; fitted a toy model and a RADMC-3D model including shear and projection | R: Local profiles are Gaussian and broad (FWHM ~1092 m/s at the peak); shear and its azimuthal dependence make averaged profiles Gaussian for both thin and thick models | F: Line profile shape alone cannot distinguish optically thin from thick emission | **supported**
- H: Is the CO emission optically thin or thick? | E: Fitted a RADMC-3D model to the 13CO cube and compared with an optically thin 12CO model | R: Optically thick model with T = 38 K, 13CO mass 2e-3 Mearth, peak tau 26 reproduces X-shape and 12CO/13CO linewidth difference; the thin model fails | F: Both 12CO and 13CO are optically thick | **supported**
- H: Can the 13CO model, rescaled by the ISM ratio, describe 12CO and give the CO mass? | E: Scaled the 13CO model mass by 77 and compared moment maps with 12CO data | R: Reproduces the bulk of 12CO emission except non-Keplerian structure; total CO mass 1.48e-1 Mearth | F: 12CO is reproduced but mass constraints are limited by high optical depth and model assumptions | **partially**
- H: Is the gas composition primordial (H2-dominated)? | E: Fitted the mean molecular weight mu through the scale height in the 13CO RADMC-3D fit | R: mu = 12.6 +1.3/-1.1, dependent on LTE and other model choices | F: Mean molecular weight is much higher than for H2-dominated gas, suggesting non-primordial composition | **partially**

## Reasoning

- Why this data: HD 121617 has detected CO and moderate inclination, reducing Keplerian shear; high spectral and spatial resolution needed  
  > "HD 121617 is a well-suited ARKS target due to its previously detected CO emission and moderate inclination, reducing the effect of Keplerian shear." (abstract)
- Why this method: A full 3D RADMC-3D model was built because the toy model ignores beam mixing and geometry  
  > "This model incorporates these effects to either confirm or challenge the results from Section" (3D radiative transfer modelling)
- Alternative: Optically thin RADMC-3D model rejected: needs unrealistically high temperature, cannot produce the X-shape or the 13CO/12CO linewidth difference  
  > "Thus, the optically thin model cannot explain our observations." (Conclusions)
- Alternative: Two-sided emission layers considered but not seen in 12CO channel maps  
  > "the $^{12}$CO channel maps show no indication of a two-sided emission structure at the spectrospatial resolution of our data" (4.1 Local line profile extraction)
- How they decided it was enough: Optically thin model adjusted until qualitative agreement; MCMC convergence for fits judged visually  
  > "these parameters were adjusted to achieve the best qualitative agreement with key features of our dataset" (5.1.2 Data comparison); "and visually assessed convergence" (Observational results)
- Limitation (authors): Keplerian fit uncertainties likely underestimated  
  > "We note that these uncertainties are likely underestimated." (Table 2)
- Limitation (authors): Mu and 13CO mass depend on the LTE assumption and radial and vertical model choices  
  > "we caution that its derivation is critically dependent on our LTE assumption" (5.2.1 13CO RADMC-3D model)
- Limitation (authors): Different total CO masses or abundance ratios may fit equally well given high optical depth  
  > "We, however, caution that different total CO masses/abundance ratios may also fit the data, given the high optical depth of both isotopologues." (5.2.2 12CO RADMC-3D model)
- Limitation (authors): Azimuthal averaging smooths azimuthal variation in line profile  
  > "the S/N boost from this method comes at the cost of averaging out azimuthal variation in the line profile and smoothing the observed line profile" (4.1 Local line profile extraction)
- Caveat (inferred, ours): The optically thin model was tuned by eye on three parameters, with no uncertainties, so its rejection rests on qualitative comparison
- Caveat (inferred, ours): mu of 12.6 is derived from a small vertical offset of the emitting layer that is not seen directly in channel maps
- Caveat (inferred, ours): Mass and temperature are degenerate for optically thick lines; the 38 K value follows from assumed LTE
- Caveat (inferred, ours): Non-Keplerian gas motion is not modelled, though residuals show it matters
- Caveat (inferred, ours): Isotopologue abundance ratio fixed to ISM 77 without testing alternatives

## Reproducibility

- Data public (paper): ARKS data available on the ARKS dataverse  
  > "The ARKS data used in this paper can be found in the" (Data availability)
- Products in archive: _not stated_
- Missing: RADMC-3D input files and set-up details (molecular data, grid, photon counts, temperature and abundance prescriptions)
- Missing: Prior ranges and chain details for the cube-level fits
- Missing: Calibration, imaging and moment-map details only in ARKS companion papers (Seba_arks, Sorcha_arks)
- Missing: No released analysis code for the toy model or shear calculation
- Data volume (inferred): Raw measurement sets for one Band 7 target in two configurations likely tens of GB; delivered ARKS cubes a few GB
- Score (inferred): 3/5, Data are public and many numeric results with uncertainties are given, but key RADMC-3D settings, priors and calibration details are missing or deferred to companion papers, and no code is released.
- Rediscovery candidate: no, Recipe is incomplete for the 3D radiative transfer fits and the optically thin model was tuned by eye, so the main results cannot be redone mechanically from the paper alone.

## Links

- Method: (cite: Seba_arks) (ARKS overview with observation setup, calibration and imaging)
- Method: (cite: Sorcha_arks) (ARKS CO gas paper with moment maps and stacked line fluxes)
- Method: (cite: Yinuo_arks) (Continuum radial profile procedure with frank)
- Method: (cite: Teague(2018)) (bettermoments)
- Method: (cite: Teague(2019_eddy)) (eddy spectral alignment)
- Method: (cite: RADMC3D(2012)) (RADMC-3D radiative transfer code)
- Companion: (cite: Seba_2arks) (Non-Keplerian gas kinematics of HD 121617 and mu consistency)
- Companion: (cite: Julien_arks) (Scattered light versus ALMA continuum offset)
- Companion: (cite: Josh_arks) (Continuum asymmetry in the ARKS sample)
- Companion: (cite: Philipp_arks) (Gas drag effects on dust and dust trapping)
- Related: ARKS (ALMA survey to Resolve exoKuiper belt Substructures, large programme 2022.1.00338.L)
- Related: ALMA MAPS (comparison of CO line ratios)

## Checks

```json
{
 "quotes": 161,
 "quotes_ok": 161,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 28,
 "numeric_problems": 0,
 "fill": {
  "facts": 125,
  "stated": 96,
  "rate": 0.768
 },
 "evidence_ok": true
}
```
