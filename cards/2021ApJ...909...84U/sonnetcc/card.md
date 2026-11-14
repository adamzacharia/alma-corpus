# Internal Structure of Molecular Gas in a Main-sequence Galaxy With a UV Clump at z = 1.45

`2021ApJ...909...84U` | The Astrophysical Journal 2021 | first author: Ushio, Kaito | arXiv: 2101.08396 | DOI: 10.3847/1538-4357/abdd1f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Internal distribution and properties of molecular gas (CO(2-1), CO(5-4), R52 ratio, rotation, gas fraction profile) in a massive main-sequence galaxy with a UV clump at z = 1.45, compared with the stellar distribution  
  > "aiming at examining the internal distribution and properties of molecular gas in the galaxy" (abstract); "Through model fittings, we compare properties of molecular gas and stellar distributions, and also reveal the radial profile of gas mass fraction." (1 Introduction)
- Target **SXDS1_13015**: coordinates R.A. (J2000) 02h17m13.62s; decl. (J2000) printed as '09 deg 40' 0'' (sign and degree part garbled in the text); peak pixel of the CO(2-1) 0th moment map  
  > "$\rm 02^{h}17^{m}13.62^{s}$" (Table 1); "$^\circ$09$'$40.$''$0" (Table 1); "At the redshift of our sample galaxy ($z = 1.450$), the linear scale is $8.45 \ \rm kpc \, arcsec^{-1}$" (1 Introduction); "the central frequency of the observed CO(2-1) emission line ($94.097 \pm 0.008 \ \rm GHz$, corresponding to the redshift of $1.4500 \pm 0.0002$)" (4.1 Molecular Gas Properties); z/distance z = 1.450 (z_CO = 1.4500 +/- 0.0002); 8.45 kpc/arcsec  
  > "$\rm 02^{h}17^{m}13.62^{s}$" (Table 1); "$^\circ$09$'$40.$''$0" (Table 1); "At the redshift of our sample galaxy ($z = 1.450$), the linear scale is $8.45 \ \rm kpc \, arcsec^{-1}$" (1 Introduction); "the central frequency of the observed CO(2-1) emission line ($94.097 \pm 0.008 \ \rm GHz$, corresponding to the redshift of $1.4500 \pm 0.0002$)" (4.1 Molecular Gas Properties); distance from Redshift from the CO(2-1) line centre; distance/scale from flat cosmology (Omega_M = 0.3, Omega_Lambda = 0.7, H0 = 70 km/s/Mpc)  
  > "$\rm 02^{h}17^{m}13.62^{s}$" (Table 1); "$^\circ$09$'$40.$''$0" (Table 1); "At the redshift of our sample galaxy ($z = 1.450$), the linear scale is $8.45 \ \rm kpc \, arcsec^{-1}$" (1 Introduction); "the central frequency of the observed CO(2-1) emission line ($94.097 \pm 0.008 \ \rm GHz$, corresponding to the redshift of $1.4500 \pm 0.0002$)" (4.1 Molecular Gas Properties)

## Data provenance

- ALMA projects: 2015.1.01129.S, 2011.0.00648.S
- bands: CO(2-1): Band 3; CO(5-4): Band 6  
  > "The observed frequency range was $93.598 - 94.535 \, \rm GHz$ (band 3)" (3.1 CO Data); "The observed frequency range was $222.094 - 252.583 \, \rm GHz$ (band 6)" (3.1 CO Data)
- frequencies and spectral setup: CO(2-1) Cycle 3: 93.598-94.535 GHz, bandwidth 937.5 MHz, 564.453 kHz resolution (1.8 km/s); CO(5-4) Cycle 0: 222.094-252.583 GHz, 488.28 kHz (~0.6 km/s)  
  > "with bandwidth of 937.5 MHz and spectral resolution of 564.453 kHz, corresponding to a velocity range and resolution of $2988 \ \rm km \, s^{-1}$ and $1.8 \ \rm km \, s^{-1}$, respectively." (3.1 CO Data); "the spectral resolution was 488.28 kHz ($\sim 0.6 \ \rm km \, s^{-1}$)" (3.1 CO Data)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 41 antennas (CO(2-1) data)  
  > "The number of 12 m antennas was 41." (3.1 CO Data)
- configurations: _not stated_
- baselines: CO(2-1): 15.1 m to 1.8 km  
  > "The length of the longest and shortest baseline was 1.8 km and 15.1 m, respectively" (3.1 CO Data)
- angular resolution: CO(2-1): ~0.55 arcsec; CO(5-4): ~0.7 arcsec (as stated for the observations)  
  > "corresponding to an angular resolution of $\sim 0.\ensuremath{''}55$ and a maximum recoverable scale of $\sim 11\ensuremath{''}$." (3.1 CO Data); "the angular resolution was $\sim$ 0.$''$7" (3.1 CO Data)
- max recoverable scale: ~11 arcsec (CO(2-1))  
  > "corresponding to an angular resolution of $\sim 0.\ensuremath{''}55$ and a maximum recoverable scale of $\sim 11\ensuremath{''}$." (3.1 CO Data)
- sensitivity: 0.18 mJy/beam (CO(2-1)) and 0.91 mJy/beam (CO(5-4)) per 25 km/s channel  
  > "The noise levels of CO(2-1) and CO(5-4) at the velocity width of $25 \ \rm km \, s^{-1}$ were $0.18 \, \rm mJy \, beam^{-1}$ and $0.91 \, \rm mJy \, beam^{-1}$, respectively." (3.1 CO Data)
- time on source: CO(2-1): 4.7 hours; CO(5-4): ~10 minutes  
  > "The total on-source time was 4.7 hours." (3.1 CO Data); "the on-source time was $\sim$ 10 minutes" (3.1 CO Data)
- observing dates: CO(2-1): 2016 August 24 and September 3 (Cycle 3); CO(5-4): Cycle 0 (dates not stated)  
  > "toward SXDS1_13015 were made with ALMA on 2016 August 24 and September 3 during the ALMA Cycle3 (ID: 2015.1.01129.S, PI: K. Ohta)." (3.1 CO Data)
- pi or archival as stated: PI: K. Ohta for both projects (the paper does not say archival)  
  > "during the ALMA Cycle3 (ID: 2015.1.01129.S, PI: K. Ohta)" (3.1 CO Data); "The observation was conducted during the ALMA Cycle 0 (ID: 2011.0.00648.S, PI: K. Ohta)" (3.1 CO Data)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 12CO J=5-4 (not stated)
- Other facility **HST (ACS V606, WFC3 J125 and H160), CANDELS**: Archival drizzled images used for the UV clump, stellar morphology and Sersic fits  
  > "We used the archival ACS $V_{606}$, WFC3 $J_{125}$ and $H_{160}$ data on CANDELS website" (3.2 HST Data); "The images are drizzled and the pixel scales are $0.\ensuremath{''}03$ for $V_{606}$, and $0.\ensuremath{''}06$ for $J_{125}$ and $H_{160}$." (3.2 HST Data)
- Other facility **Subaru FMOS (via Yabe12)**: Near-infrared spectroscopy giving Halpha, gas metallicity (N2) and sample selection for the target  
  > "Using the Fiber Multi-Object Spectrograph (FMOS) on the Subaru telescope, (cite: Yabe12) made near-infrared spectroscopic observations of" (2 Sample Galaxy); "the gas metallicities were derived based on N2 method (cite: Pettini04)" (2 Sample Galaxy)
- External data: Stellar mass (SED fitting, Bruzual03 models, Salpeter IMF corrected with factor 0.58) and SFR from rest-UV luminosity for SXDS1_13015  
  > "The stellar masses were derived by spectral energy distribution (SED) fittings with optical to mid-infrared data, adopting the stellar population synthesis model by (cite: Bruzual03) and the IMF by (cite: Salpeter55)." (2 Sample Galaxy); "After correcting the difference of the adopted IMF with the factor of 0.58 (cite: Speagle14)" (2 Sample Galaxy) [from Yabe12 (cite: Yabe12); Speagle14 (cite: Speagle14) for the IMF factor]
- External data: Gas-phase metallicity 12+log(O/H) = 8.85 from the N2 method (Pettini04 calibration)  
  > "the gas metallicities were derived based on N2 method (cite: Pettini04)" (2 Sample Galaxy); "$8.85 \pm 0.04$" (Table 1) [from Yabe12 (cite: Yabe12); Pettini04 (cite: Pettini04)]
- External data: Metallicity-dependent CO-to-H2 conversion factor, Equation (7) of Genzel15  
  > "we adopt the Equation (7) of (cite: Genzel15)" (4.1.1 Total Flux and Molecular Gas Mass) [from Genzel15 (cite: Genzel15)]
- External data: CO(5-4) ALMA Cycle 0 data and its calibration (CASA 4.2)  
  > "The raw visibility data of CO(5-4) was calibrated with CASA version 4.2 by (cite: Seko16)." (3.1 CO Data) [from Seko16 (cite: Seko16)]
- External data: Median stellar mass surface density profiles of galaxies at different redshifts for comparison  
  > "the derived profile of SXDS1_13015 is plotted with the median profiles of galaxies at different redshifts by (cite: Patel13)" (4.2 Stellar Distribution) [from Patel13 (cite: Patel13)]
- External data: CO and optical half-light radii of field main-sequence and sBzK galaxies  
  > "The field sample includes 12 main sequence galaxies at $z \sim 1 - 1.5$ by (cite: Tacconi13) and 3 sBzK galaxies by (cite: Daddi10)." (4.3.2 CO and Optical Half-light Radii) [from Tacconi13 (cite: Tacconi13); Daddi10 (cite: Daddi10)]
- External data: CO and optical half-light radii of 4 cluster galaxies at z ~ 1.6  
  > "The cluster sample consists of 4 cluster galaxies at $z \sim 1.6$ by (cite: Noble19)" (4.3.2 CO and Optical Half-light Radii) [from Noble19 (cite: Noble19)]
- Simulation/model as data: Hydrodynamic simulation of a clumpy high-z galaxy with LVG CO excitation modelling used only for qualitative comparison with the high R52 in the UV clump  
  > "is qualitatively consistent with the CO excitation ladder modeled by a large velocity gradient analysis of the hydrodynamically simulated high-$z$ clumpy galaxy (cite: Bournaud15)" (4.1.2 Spatial Distribution of R52)

## Processing

### Calibration

- pipeline or manual: CO(2-1): CASA with the observatory-provided calibration script; CO(5-4): calibrated by Seko16  
  > "The raw visibility data of CO(2-1) was calibrated with the Common Astronomy Software Applications (cite: McMullin07) version 4.7.2 and the observatory-provided calibration script." (3.1 CO Data); "The raw visibility data of CO(5-4) was calibrated with CASA version 4.2 by (cite: Seko16)." (3.1 CO Data)
- casa version: CASA 4.7.2 (CO(2-1) calibration); CASA 4.2 (CO(5-4) calibration); CASA 5.4.0 (imaging)  
  > "The imagings of the ALMA data were carried out using CASA version 5.4.0." (3.1 CO Data); "The raw visibility data of CO(5-4) was calibrated with CASA version 4.2 by (cite: Seko16)." (3.1 CO Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623 and J0238-1636 (flux, bandpass, amplitude; CO(2-1) data); phase calibrators J0209-0438 and J0215-0222  
  > "J0006-0623 and J0238-1636 were used as the flux, bandpass, and amplitude calibrators." (3.1 CO Data); "The phase calibrators were J0209-0438 and J0215-0222." (3.1 CO Data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA uvcontsub and tclean (version 5.4.0)  
  > "we used the CASA tasks `uvcontsub` and `tclean`" (3.1 CO Data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5; channel width 25 km/s  
  > "using the `tclean` with weighting of briggs (${\tt robust} = 0.5$) and channel width of $25 \ \rm km \, s^{-1}$" (3.1 CO Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 3 sigma-clean channel maps (mask details not stated)  
  > "we made $3\sigma$-clean channel maps of CO(2-1) and CO(5-4)" (3.1 CO Data)
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted in the CO(5-4) data with uvcontsub  
  > "Firstly, continuum emission in CO(5-4) data was subtracted with the `uvcontsub`." (3.1 CO Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO(2-1) map convolved to the CO(5-4) beam to build the R52 map  
  > "We made the $R_{52}$ map by dividing the CO(5-4) 0th moment map by the CO(2-1) map convolved to the same beam size as CO(5-4) data." (4.1.2 Spatial Distribution of R52)
- final beam: CO(2-1) 0.61 x 0.52 arcsec (~4.8 kpc); CO(5-4) 0.84 x 0.60 arcsec (~6.0 kpc)  
  > "The synthesized beam sizes of CO(2-1) and CO(5-4) channel maps were $0.\ensuremath{''}61 \times 0.\ensuremath{''}52$ ($\sim 4.8 \ \rm kpc$) and $0.\ensuremath{''}84 \times 0.\ensuremath{''}60$ ($\sim 6.0 \ \rm kpc$), respectively." (3.1 CO Data)
- final rms: 0.18 mJy/beam (CO(2-1)) and 0.91 mJy/beam (CO(5-4)) at 25 km/s  
  > "The noise levels of CO(2-1) and CO(5-4) at the velocity width of $25 \ \rm km \, s^{-1}$ were $0.18 \, \rm mJy \, beam^{-1}$ and $0.91 \, \rm mJy \, beam^{-1}$, respectively." (3.1 CO Data)

### Inherited from earlier work

- Details of the CO(5-4) observations (Cycle 0 project 2011.0.00648.S)  
  > "The details of CO(5-4) observations are described by (cite: Seko16)." (3.1 CO Data) [from (cite: Seko16)]
- Calibration of the CO(5-4) raw visibilities in CASA 4.2  
  > "The raw visibility data of CO(5-4) was calibrated with CASA version 4.2 by (cite: Seko16)." (3.1 CO Data) [from (cite: Seko16)]
- Stellar mass, SFR and metallicity of the target taken from the earlier FMOS sample  
  > "The SFRs were derived from extinction-corrected rest UV luminosity densities by using a conversion factor by (cite: Kennicutt98annurev)" (2 Sample Galaxy) [from (cite: Yabe12)]
- Metallicity-dependent alpha_CO prescription  
  > "we adopt the Equation (7) of (cite: Genzel15)" (4.1.1 Total Flux and Molecular Gas Mass) [from (cite: Genzel15)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub in the CO(5-4) data, and whether any continuum subtraction was done for CO(2-1)
- Image size, cell size, tclean niter/threshold and the clean mask beyond '3 sigma'
- Primary-beam correction and flux-scale handling for the two datasets, and the CASA 4.2 calibration choices for CO(5-4) (only in Seko16)
- Velocity range and masking used to build the CO(2-1) and CO(5-4) integrated-intensity (0th moment) maps
- GalPaK3D settings: version, priors, sampler/chain length, initial guesses, and the systematic error added in quadrature
- simobserve configuration (array configs, integration times, noise model) for the 100 simulated cubes and the R52 position/velocity uncertainty tests
- GALFIT details: initial guesses, sky values, masks, the PSF stars and the M/L conversion to mass surface density
- Exact source of the stellar mass (1.2e11 Msun) and SFR used in f_gas and depletion time (value after IMF correction is given in rounded form in the text)
- Declination of the target (printed incompletely in Table 1) and exact HST-ALMA astrometric shift procedure
- How the CO(5-4) flux was measured differently from Seko16 (velocity width and reduction details)

## Analysis recipe

1. **Calibrate and image the CO cubes**: Calibrate with observatory script (CO(2-1)) and Seko16 calibration (CO(5-4)); continuum-subtract CO(5-4) with uvcontsub; 3 sigma-clean tclean channel maps at 25 km/s  
  > "After that, we made $3\sigma$-clean channel maps of CO(2-1) and CO(5-4) using the `tclean` with weighting of briggs (${\tt robust} = 0.5$) and channel width of $25 \ \rm km \, s^{-1}$." (3.1 CO Data)
   - software: CASA 4.7.2, CASA 4.2, CASA 5.4.0, uvcontsub, tclean
   - parameter: Briggs weighting robust = 0.5; channel width 25 km/s  
  > "with weighting of briggs (${\tt robust} = 0.5$) and channel width of $25 \ \rm km \, s^{-1}$" (3.1 CO Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure total CO(2-1) and CO(5-4) fluxes**: Fit an elliptical Gaussian to the integrated intensity maps within a 1.5 arcsec diameter circle centred on the CO(2-1) peak  
  > "are derived by fitting an elliptical Gaussian model to the respective integrated intensity maps." (4.1.1 Total Flux and Molecular Gas Mass); "We use the data in a 1.$''$5 diameter circle centered on the peak of the CO(2-1) integrated intensity map." (4.1.1 Total Flux and Molecular Gas Mass)
   - fitting: Elliptical Gaussian model fit to moment-0 maps; priors/likelihood not stated  
  > "are derived by fitting an elliptical Gaussian model to the respective integrated intensity maps." (4.1.1 Total Flux and Molecular Gas Mass)
   - validation: Compared with GalPaK3D best-fit flux (consistent); CO(5-4) flux differs from Seko16  
  > "is consistent with that derived from the two-dimensional Gaussian fitting to the integrated intensity map" (4.1.3 Fitting a Rotating Disk Model); "The CO(5-4) flux value is different from that derived by (cite: Seko16) because of the differences of the adopted velocity width and the data reduction." (4.1.1 Total Flux and Molecular Gas Mass)
3. **Derive CO(1-0) luminosity, molecular gas mass, gas fraction and depletion time**: L'CO(1-0) from CO(2-1) flux with R21 = 2; M_mol = alpha_CO L'CO(1-0) with metallicity-dependent alpha_CO; f_gas = M_mol/(M_mol+M_star); depletion time = M_mol/SFR  
  > "The gas depletion time ($\tau_{\rm depl} = M_{\rm mol}/{\rm SFR}$) of the galaxy" (4.1.1 Total Flux and Molecular Gas Mass); "Because the CO excitation ladder of the galaxy is similar to that of the Milky Way, we assume $R_{21} = 2$." (4.1.1 Total Flux and Molecular Gas Mass)
   - parameter: alpha_CO from Equation (7) of Genzel15 using 12+log(O/H) on the Pettini04 scale  
  > "we adopt the Equation (7) of (cite: Genzel15)" (4.1.1 Total Flux and Molecular Gas Mass)
   - parameter: alpha_CO = 2.58 Msun (K km/s pc^2)^-1  
  > "The $\alpha_{\rm CO}$ of SXDS1_13015 is calculated to be $2.58\ M_{\ensuremath{\odot}} \rm (K\, km\,s^{-1}\, pc^2)^{-1}$." (4.1.1 Total Flux and Molecular Gas Mass)
   - assumption: R21 = CO(2-1)/CO(1-0) flux ratio of 2 (Milky Way like)  
  > "We adopt CO(2-1)/CO(1-0) flux ratio of 2 (the Milky Way like value)." (Table 2)
   - assumption: alpha_CO includes a 36% mass contribution of helium  
  > "where $\alpha_{\rm CO}$ includes a 36% mass contribution of helium" (4.1.1 Total Flux and Molecular Gas Mass)
   - assumption: Flat cosmology with Omega_M = 0.3, Omega_Lambda = 0.7, H0 = 70 km/s/Mpc; Chabrier IMF  
  > "we adopt a flat cosmology with $\Omega_{M} = 0.3, \ \Omega_{\Lambda} = 0.7$ and $H_0 = 70 \ \rm km \, s^{-1} \, Mpc^{-1}$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build the CO(5-4)/CO(2-1) ratio (R52) map**: Divide CO(5-4) 0th moment map by CO(2-1) map convolved to the CO(5-4) beam, in pixels with S/N > 2.5 in CO(5-4)  
  > "We made the $R_{52}$ map by dividing the CO(5-4) 0th moment map by the CO(2-1) map convolved to the same beam size as CO(5-4) data." (4.1.2 Spatial Distribution of R52); "The $R_{52}$ is calculated in pixels with ${\rm S/N} > 2.5$ in the CO(5-4) map." (4.1.2 Spatial Distribution of R52)
   - software: CASA
   - parameter: S/N > 2.5 threshold in the CO(5-4) map; also a map in the velocity range -250 to 0 km/s  
  > "We show the 0th moment maps integrated over the velocity range of $-250 \ \rm km \, s^{-1}$ to $0 \ \rm km \, s^{-1}$ in Figure [5](#fig:negvel_mom0)." (4.1.2 Spatial Distribution of R52)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test significance of CO(5-4) peak offset and velocity shift; align HST to ALMA**: Simulate CO(5-4) observations with simobserve of a Gaussian mimicking the CO(5-4) distribution and line profile to get 1-sigma uncertainties on peak position and velocity; shift HST astrometry assuming the J125 peak coincides with the CO(2-1) moment-0 peak  
  > "We performed simulations of CO(5-4) observation with CASA task `simobserve` assuming a gaussian distribution mimicking the CO(5-4) distribution and line profile." (4.1.2 Spatial Distribution of R52); "We assume the peak of $J_{125}$ image coincides with the peak of the CO(2-1) 0th moment map" (4.1.2 Spatial Distribution of R52)
   - software: CASA simobserve
   - parameter: HST offset (dRA, dDec) = (+0.058, -0.198) arcsec  
  > "The offset is $(\Delta{\rm R.A.}, \Delta{\rm Dec.}) = (+0.\ensuremath{''}058, -0.\ensuremath{''}198)$." (4.1.2 Spatial Distribution of R52)
   - assumption: J125 peak coincides with CO(2-1) peak because CO(2-1) has a symmetric profile and high S/N  
  > "because the CO(2-1) shows a good symmetry in the line profile and S/N of the image is high" (4.1.2 Spatial Distribution of R52)
   - fitting: _not stated_
   - validation: Offset 0.15 arcsec = ~3.8 sigma and velocity difference ~150 km/s = ~5 sigma, so judged real  
  > "Thus the offset and the peak velocity difference are considered to be real." (4.1.2 Spatial Distribution of R52)
6. **Fit a rotating disk to the CO(2-1) cube**: GalPaK3D disk model (exponential flux profile n=1, hyperbolic tangent rotation curve) convolved with PSF and LSF fit to the CO(2-1) channel cube; uncertainties from 100 simulated cubes with random noise seeds, combined in quadrature with systematic error  
  > "We fit a disk model whose radial flux profile is exponential (Sérsic index $n=1$) and radial rotational velocity profile is hyperbolic tangent to the CO(2-1) channel map." (4.1.3 Fitting a Rotating Disk Model); "In order to estimate the uncertainties on the best-fit parameters, we created 100 cleaned cubes by simulating observations of the best-fit disk model with `simobserve` by changing the noise seeds randomly." (4.1.3 Fitting a Rotating Disk Model)
   - software: GalPaK3D, CASA simobserve
   - parameter: PSF = synthesized beam 0.61 x 0.53 arcsec, PA = 79 deg; LSF = 25 km/s channel  
  > "PSF and LSF correspond to the synthesized beam ($0.\ensuremath{''}61 \times 0.\ensuremath{''}53$, ${\rm PA} = 79\ensuremath{^\circ}$) and the channel bin (velocity width is $25 \ \rm km \, s^{-1}$), respectively." (4.1.3 Fitting a Rotating Disk Model)
   - parameter: Free parameters: central position, central frequency, total flux, r1/2, inclination, PA, turnover radius, Vmax, constant sigma0  
  > "The fitting parameters are central position, central frequency, total flux, half-light radius ($r_{1/2}$), inclination, position angle, turnover radius ($r_{t}$)" (4.1.3 Fitting a Rotating Disk Model)
   - assumption: Velocity dispersion constant over the disk; sigma0 poorly constrained because of beam smearing  
  > "Due to the large beam size, the observed line width seems to be largely affected by beam smearing effect, and it is hard to constrain the intrinsic velocity dispersion well." (4.1.3 Fitting a Rotating Disk Model)
   - fitting: Disk model convolved with 2D PSF and 1D LSF fit to the data cube; sampler, priors and likelihood not stated  
  > "by fitting a disk model convolved with two-dimensional PSF and one-dimensional line spread function (LSF) to a given data cube" (4.1.3 Fitting a Rotating Disk Model)
   - validation: Residual map and line profile show the disk model represents the data; fit with fixed sigma0 ~ 50 km/s reproduces the line profile without changing r1/2  
  > "The residuals demonstrate that the CO(2-1) distribution of the galaxy is well represented by the rotating disk model." (4.1.3 Fitting a Rotating Disk Model); "In fact, the observed line profile is well reproduced without changing other output parameters such as $r_{1/2}$, even if we fit a disk model with a fixed $\sigma_{0} \sim 50 \ \rm km \, s^{-1}$" (4.1.3 Fitting a Rotating Disk Model)
7. **Fit Sersic models to HST J125 and H160 images**: GALFIT single-component Sersic fit and two-component fit with bulge n=4 and disk n=1 (disk position, PA and axis ratio fixed to the single-component values) in a ~2.5 x 2.5 arcsec region with PSFs from stacked stars  
  > "we fit Sérsic profile models to HST WFC3/IR $J_{125}$ and $H_{160}$ band images using GALFIT (cite: Peng02)." (4.2 Stellar Distribution); "In this fitting, Sérsic indices are fixed to be $n=4$ for bulge and $1$ for disk" (4.2 Stellar Distribution)
   - software: GALFIT
   - parameter: PSF from stacking four (J125) or six (H160) unsaturated stars; ~2.5 x 2.5 arcsec boxy fitting region; neighbours masked  
  > "Four(Six) bright but unsaturated stars in the $J_{125}$($H_{160}$) image of the CANDELS-UDS field are stacked to construct the PSFs for the fittings." (4.2 Stellar Distribution); "The pixels contaminated by neighboring objects are masked out." (4.2 Stellar Distribution)
   - assumption: Bulge n=4 and disk n=1 fixed because the galaxy has a rotating gas disk and appears to have a bulge and disk in HST  
  > "because the galaxy has a rotating gas disk and seems to consist of the bulge and disk in the HST composite image" (4.2 Stellar Distribution)
   - fitting: GALFIT least-squares Sersic fits; sampler/priors not stated  
  > "The fitting parameters are central position, total magnitude, half-light radius ($R_{1/2}$), Sérsic index ($n$), axial ratio, and position angle." (4.2 Stellar Distribution)
   - validation: Uncertainties from varying the sky level, the PSF stars and the fitting region size  
  > "Uncertainties are estimated by changing sky level within its error, stars to construct the PSFs and the size of the fitting region." (Table 4)
8. **Compare gas and stellar radial profiles, f_gas(r) and dynamical masses**: Combine GalPaK3D gas model and GALFIT stellar model into intrinsic radial surface profiles and f_gas at each radius; Mdyn(r) ~ r v_rot^2 / G at r1/2, 2 r1/2, 3 r1/2; inner gas and stellar masses scaled by J125 luminosity within r  
  > "we obtain intrinsic radial surface distributions of the molecular gas as well as the stellar component in SXDS1_13015" (4.3.1 Modeled Gas and Stellar Distributions); "assuming the inner mass ($m(<r)$) is proportional to the luminosity within the radius ($L(<r)$) in $J_{125}$ image" (4.3.1 Modeled Gas and Stellar Distributions)
   - assumption: Constant mass-to-luminosity ratio for the stellar mass surface density  
  > "Assuming a constant mass-to-luminosity ratio, we derived the stellar mass surface density profile of SXDS1_13015 from $J_{125}$ distribution modeled with the single component model." (4.2 Stellar Distribution)
   - fitting: _not stated_
   - validation: Uncertainty on gas profile from the 100 simulated-cube GalPaK3D fits; stellar from stellar mass and GALFIT parameter uncertainties  
  > "The uncertainty on the molecular gas surface distribution is estimated with radial profiles derived from $\rm GalPaK^{3D}$ fitting to the 100 simulated cubes" (4.3.1 Modeled Gas and Stellar Distributions)
9. **Compare CO and optical half-light radii with literature samples**: Place the target on the optical versus CO half-light radius plane with field and cluster galaxies at z ~ 1-1.6 from the literature  
  > "Figure [10](#fig:radius_comparison) (left) shows the location of SXDS1_13015 in optical versus CO half-light radius plane compared to other field and cluster galaxies at $z \sim 1 - 1.6$." (4.3.2 CO and Optical Half-light Radii)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (CO(2-1) calibration); 4.2 (CO(5-4) calibration); 5.4.0 (imaging): Calibration of the raw visibilities and imaging  
  > "The imagings of the ALMA data were carried out using CASA version 5.4.0." (3.1 CO Data); "The raw visibility data of CO(2-1) was calibrated with the Common Astronomy Software Applications (cite: McMullin07) version 4.7.2" (3.1 CO Data)
- **uvcontsub** : Continuum subtraction in the CO(5-4) data  
  > "Firstly, continuum emission in CO(5-4) data was subtracted with the `uvcontsub`." (3.1 CO Data)
- **tclean** : Cleaned CO(2-1) and CO(5-4) channel maps  
  > "we used the CASA tasks `uvcontsub` and `tclean`" (3.1 CO Data)
- **simobserve** : Simulating CO(5-4) observations for position/velocity uncertainties and 100 simulated CO(2-1) cubes for GalPaK3D errors  
  > "We performed simulations of CO(5-4) observation with CASA task `simobserve`" (4.1.2 Spatial Distribution of R52); "we created 100 cleaned cubes by simulating observations of the best-fit disk model with `simobserve`" (4.1.3 Fitting a Rotating Disk Model)
- **GalPaK3D** : Fitting a rotating disk model to the CO(2-1) cube to get intrinsic size and kinematics  
  > "we fit a rotating disk model by using" (4.1.3 Fitting a Rotating Disk Model)
- **GALFIT** : Sersic fits to the HST J125 and H160 images  
  > "we fit Sérsic profile models to HST WFC3/IR $J_{125}$ and $H_{160}$ band images using GALFIT (cite: Peng02)." (4.2 Stellar Distribution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) flux | 1.03 | 0.05 | Jy km/s | 2 | The total CO(2-1) and CO(5-4) flux of SXDS1_13015 are estimated to be $(1.03 \pm 0.05) \ \rm Jy \, km \, s^{-1}$ and $(1.16 \pm 0.17) \ \rm Jy \, km \, s^{-1}$, respectively. |
| Total CO(5-4) flux | 1.16 | 0.17 | Jy km/s | 2 | The total CO(2-1) and CO(5-4) flux of SXDS1_13015 are estimated to be $(1.03 \pm 0.05) \ \rm Jy \, km \, s^{-1}$ and $(1.16 \pm 0.17) \ \rm Jy \, km \, s^{-1}$, respectively. |
| Beam-deconvolved FWHM of CO(2-1) source | 4.0 | 0.5 | kpc | 2 | The beam-deconvolved FWHM of the CO(2-1) source is $4.0 \pm 0.5 \ \rm kpc$. |
| Galaxy-integrated R52 (CO(5-4)/CO(2-1) flux ratio) | 1.1 | 0.2 | dimensionless | 2 | $R_{52}$ of the galaxy is $1.1 \pm 0.2$, which suggests the CO excitation ladder of the galaxy is similar to that of the Milky Way rather than sBzK galaxies at $z \sim 1.5$. |
| Total CO(1-0) luminosity L'CO(1-0) | 5.62e10 | 0.27e10 | K km/s pc^2 | 3 | The calculated total CO(1-0) luminosity of SXDS1_13015 is $(5.62 \pm 0.27) \times 10^{10} \ {\rm K\, km\,s^{-1} \, pc^2}$. |
| CO-to-H2 conversion factor alpha_CO | 2.58 | not stated | Msun (K km/s pc^2)^-1 | 3 | The $\alpha_{\rm CO}$ of SXDS1_13015 is calculated to be $2.58\ M_{\ensuremath{\odot}} \rm (K\, km\,s^{-1}\, pc^2)^{-1}$. |
| Total molecular gas mass | 1.45e11 | 0.07e11 | Msun | 3 | The resulting total molecular gas mass is $(1.45 \pm 0.07) \times 10^{11} \ M_{\ensuremath{\odot}}$ and the gas mass fraction is $f_{\rm gas} = 0.55 \pm 0.08$. |
| Gas mass fraction f_gas (galaxy total) | 0.55 | 0.08 | dimensionless | 3 | the gas mass fraction is $f_{\rm gas} = 0.55 \pm 0.08$ |
| Gas depletion time | 1.1 | 0.3 | Gyr | 3 | of the galaxy is estimated to be $= 1.1 \pm 0.3 \ \rm Gyr$ |
| Peak R52 in the UV clump | ~2.2 | not stated | dimensionless | 4 | The peak of the CO(5-4)/CO(2-1) flux ratio ($R_{52} \sim 2.2$) is significantly larger than the $R_{52}$ averaged over SXDS1_13015 and that of the Milky Way. |
| Offset between CO(5-4) and CO(2-1) peaks | ~0.15 | 1-sigma position uncertainty ~0.04 arcsec (~3.8 sigma) | arcsec | 5 | observed offset between the peak positions of CO(5-4) and CO(2-1) is $\sim 0.15 \ \rm arcsec$ which corresponds to $\sim 3.8 \sigma$.; the 1-$\sigma$ uncertainty of the peak position of CO(5-4) is $\sim 0.04 \ \rm arcsec$ |
| GalPaK3D total CO(2-1) flux | 1.10 | 0.05 | Jy km/s | 6 | The best-fit flux ($1.10 \pm 0.05 \ \rm Jy \, km \, s^{-1}$) |
| CO(2-1) half-light radius r1/2 (GalPaK3D) | 2.30 | 0.12 | kpc | 6 | The best-fit $r_{1/2} = 2.30 \pm 0.12 \ \rm kpc$ |
| Disk inclination (GalPaK3D) | 47.6 | 6.5 | deg | 6 | $47.6 \pm 6.5$ |
| Disk position angle (GalPaK3D) | 42.8 | 2.0 | deg | 6 | $42.8 \pm 2.0$ |
| Turnover radius r_t (GalPaK3D) | 0.48 | 0.22 | kpc | 6 | $0.48 \pm 0.22$ |
| Inclination-corrected maximum rotational velocity Vmax | 350 | 30 | km/s | 6 | The best-fit $V_{\rm max}$ and $\sigma_0$ are $350 \pm 30 \ \rm km \, s^{-1}$ and $2.7 \pm 8.7 \ \rm km \, s^{-1}$, respectively. |
| Velocity dispersion sigma0 (GalPaK3D, judged unreliable) | 2.7 | 8.7 | km/s | 6 | The best-fit $V_{\rm max}$ and $\sigma_0$ are $350 \pm 30 \ \rm km \, s^{-1}$ and $2.7 \pm 8.7 \ \rm km \, s^{-1}$, respectively. |
| J125 single Sersic index n | 2.04 | 0.19 | dimensionless | 7 | $2.04 \pm 0.19$ |
| J125 single Sersic half-light radius R1/2 | 3.54 | 0.15 | kpc | 7 | $3.54 \pm 0.15$ |
| H160 single Sersic index n | 1.76 | 0.11 | dimensionless | 7 | $1.76 \pm 0.11$ |
| H160 single Sersic half-light radius R1/2 | 3.22 | 0.07 | kpc | 7 | $3.22 \pm 0.07$ |
| J125 bulge-to-disk luminosity ratio | 0.38 | +0.11/-0.08 | dimensionless | 7 | $0.38^{+0.11}_{-0.08}$ |
| H160 bulge-to-disk luminosity ratio | 0.36 | +0.11/-0.08 | dimensionless | 7 | $0.36^{+0.11}_{-0.08}$ |
| Radial f_gas from centre to 3 r1/2 | ~0.6 at centre to ~0.2 at ~3 r1/2 | not stated | dimensionless | 8 | decreases with increasing galactocentric radius from $\sim 0.6$ at the central region to $\sim 0.2$ at $\sim 3 \times r_{1/2}$ |
| Dynamical mass within r1/2, 2 r1/2, 3 r1/2 | ~(0.7, 1.3, 2.0)e11 | not stated | Msun | 8 | are estimated to be $\sim (0.7,\ 1.3,\ 2.0) \times 10^{11} \ M_{\ensuremath{\odot}}$ |
| Baryon fraction within r1/2, 2 r1/2, 3 r1/2 | ~0.61, 0.59, 0.53 | not stated | dimensionless | 8 | are estimated to be $\sim 0.61,\ 0.59,\ 0.53$ |
| CO-to-optical half-light radius ratios (F125W, F160W) | 0.65 (F125W); 0.71 (F160W) | 0.04 each | dimensionless | 9 | $R_{1/2,\rm CO}/R_{1/2,\rm F125W} = 0.65 \pm 0.04$, $R_{1/2,\rm CO}/R_{1/2,\rm F160W} = 0.71 \pm 0.04$ |

## Qualitative findings

- The double-peaked CO(2-1) profile and velocity gradient indicate a rotating molecular gas disk  
  > "The symmetric double-peak line profile of CO(2-1) implies the galaxy has a rotating gas disk." (4.1 Molecular Gas Properties)
- The CO(5-4) peak shows a ~0.15 arcsec offset and an asymmetric profile attributed to the UV clump  
  > "These features are originated from the presence of the UV clump as described later" (4.1 Molecular Gas Properties)
- Molecular gas is more centrally concentrated than stars and seems associated with the bulge rather than the stellar disk  
  > "seems to associate with the bulge rather than the stellar disk" (4.3.1 Modeled Gas and Stellar Distributions)

## Claim tuples

- H: Is the CO excitation of the galaxy Milky Way-like or enhanced like sBzK galaxies? | E: Measured total CO(2-1) and CO(5-4) fluxes from elliptical Gaussian fits to moment-0 maps | R: R52 = 1.1 +/- 0.2 | F: CO excitation ladder is similar to that of the Milky Way rather than sBzK galaxies at z ~ 1.5 | **supported**
- H: Does the UV clump have higher CO excitation (density and/or temperature) than the rest of the galaxy? | E: Built an R52 map (CO(5-4)/CO(2-1) at matched beam) and tested the offset with simobserve simulations | R: R52 peaks at ~2.2 at the UV clump position, ~0.3 arcsec north of the CO(2-1) peak; offset ~3.8 sigma | F: Gas density and/or temperature is higher in the UV clump, qualitatively consistent with a clumpy-galaxy simulation | **supported**
- H: Is the CO(2-1) distribution consistent with a rotating disk, and what is its size? | E: GalPaK3D disk-model fit to the CO(2-1) cube with uncertainties from 100 simulated cubes | R: Residuals small; r1/2 = 2.30 +/- 0.12 kpc, Vmax = 350 +/- 30 km/s | F: The CO(2-1) distribution is well represented by a rotating disk with half-light radius 2.3 kpc | **supported**
- H: Is the molecular gas distributed differently from the stars, and how does f_gas vary with radius? | E: Compared GalPaK3D gas profile with GALFIT stellar profiles from HST J125/H160 and computed radial f_gas | R: f_gas falls from ~0.6 at the centre to ~0.2 at ~3 r1/2; CO half-light radius is 0.65-0.71 of the optical radius | F: Molecular gas is more centrally concentrated than stars, suggesting the galaxy is forming its bulge | **supported**

## Reasoning

- Why this data: Combine multi-transition CO with high-resolution HST to study CO(5-4)/CO(2-1) in the UV clump  
  > "Combining multitransition CO data and high-resolution HST data of the galaxy, we also study CO(5-4)/CO(2-1) flux ratio in the UV clump." (1 Introduction)
- Why this method: Fit a rotating disk model to remove beam smearing and recover intrinsic gas distribution and kinematics  
  > "In order to eliminate the effect of beam smearing and derive the intrinsic molecular gas distribution and kinematic properties of the galaxy, we fit a rotating disk model by using" (4.1.3 Fitting a Rotating Disk Model)
- Alternative: A GalPaK3D fit with sigma0 fixed to ~50 km/s reproduces the line profile equally well, so the free-fit sigma0 = 2.7 km/s is not trusted  
  > "In fact, the observed line profile is well reproduced without changing other output parameters such as $r_{1/2}$, even if we fit a disk model with a fixed $\sigma_{0} \sim 50 \ \rm km \, s^{-1}$" (4.1.3 Fitting a Rotating Disk Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Best-fit velocity dispersion is unreliable; beam smearing from the large beam  
  > "The value is considered not to be reliable." (4.1.3 Fitting a Rotating Disk Model); "it is hard to constrain the intrinsic velocity dispersion well" (4.1.3 Fitting a Rotating Disk Model)
- Limitation (authors): Stellar surface density within ~1 kpc is poorly recovered because the HST PSF HWHM is comparable to that scale  
  > "it is possible that the profile is not sufficiently recovered within this scale." (4.2 Stellar Distribution)
- Limitation (authors): CO(5-4) flux differs from the earlier Seko16 measurement because of velocity width and data reduction differences  
  > "The CO(5-4) flux value is different from that derived by (cite: Seko16) because of the differences of the adopted velocity width and the data reduction." (4.1.1 Total Flux and Molecular Gas Mass)
- Caveat (inferred, ours): The Summary says R21 = 1 (Milky Way value) while Section 4.1.1, Table 2 and the abstract use R21 = 2; the mass quoted depends on this assumption and the text is inconsistent
- Caveat (inferred, ours): Gas mass relies on an assumed R21 = 2 and a metallicity-dependent alpha_CO from a single calibration; no CO(1-0) or dust-based cross-check of alpha_CO
- Caveat (inferred, ours): R52 map uses CO(5-4) at 0.84 x 0.60 arcsec vs 4.8-6 kpc beams, so the UV-clump excitation peak (~0.3 arcsec offset) is a sub-beam feature; ALMA-HST astrometry is tied by assuming J125 peak = CO(2-1) peak
- Caveat (inferred, ours): CO(5-4) data are only ~10 minutes on source (rms 0.91 mJy/beam), so R52 map S/N is limited
- Caveat (inferred, ours): Stellar surface density uses a constant M/L and a single-component or fixed n=4/n=1 two-component decomposition, which drives the 'gas associated with bulge' conclusion
- Caveat (inferred, ours): A single galaxy is studied, so generalising to main-sequence clumpy galaxies is not supported statistically

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Line-free channel ranges for uvcontsub, clean mask, niter, threshold, image and cell sizes
- Missing: GalPaK3D and GALFIT run configurations (priors, initial guesses, PSF star choices, masks)
- Missing: Moment-map velocity windows and primary-beam handling
- Missing: simobserve inputs for the 100 simulated cubes
- Missing: Definition of the systematic error added to GalPaK3D uncertainties
- Missing: Whether the data are in the public ALMA archive (not stated by the paper)
- Data volume (inferred): Two ALMA projects: Cycle 3 Band 3 12-m (4.7 h on source, 41 antennas) plus a short Cycle 0 Band 6 execution; roughly tens of GB of raw data, a few GB for calibrated cubes; HST CANDELS cutouts are small
- Score (inferred): 3/5, Both projects are named and a good part of the recipe is given (CASA versions, robust, channel width, GalPaK3D and GALFIT set-up, numeric tables), but imaging masks, line-free channels, fitting priors and the CO(5-4) calibration (in Seko16) are missing, and the R21 value is internally inconsistent
- Rediscovery candidate: yes, ALMA Cycle 0 and Cycle 3 data of named projects are normally in the public archive, the key results (fluxes, R52, GalPaK3D parameters, f_gas) are numeric, and the recipe is mostly complete, although the paper does not itself state public availability

## Links

- Method: Seko16 (cite: Seko16) (Describes the CO(5-4) Cycle 0 observations and calibration inherited here)
- Method: Bouche15 (cite: Bouche15) (GalPaK3D disk fitting code)
- Method: Peng02 (cite: Peng02) (GALFIT Sersic fitting code)
- Method: Genzel15 (cite: Genzel15) (Equation (7) metallicity-dependent alpha_CO)
- Companion: Yabe12 (cite: Yabe12) (FMOS sample providing stellar mass, SFR and metallicity of the target)
- Companion: Seko16 (cite: Seko16) (Earlier ALMA CO(5-4) and dust observations of the same galaxy)
- Companion: Cibinel17 (cite: Cibinel17) (CO(5-4) of a clumpy main-sequence galaxy at z ~ 1.5, compared for UV-clump detection)
- Related: ALMA Cycle 3 project 2015.1.01129.S (PI K. Ohta)
- Related: ALMA Cycle 0 project 2011.0.00648.S (PI K. Ohta)
- Related: CANDELS (HST UDS field)
- Related: Subaru-XMM/Newton Deep Survey (SXDS/UDS)
- Related: Subaru FMOS spectroscopic sample of Yabe12

## Checks

```json
{
 "quotes": 161,
 "quotes_ok": 161,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 28,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 85,
  "rate": 0.759
 },
 "evidence_ok": true
}
```
