# A Massive, Clumpy Molecular Gas Distribution and Displaced AGN in Zw 3146

`2021ApJ...910...53V` | The Astrophysical Journal 2021 | first author: Vantyghem, A. N. | arXiv: 2102.02300 | DOI: 10.3847/1538-4357/abe306

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, agn_and_quasars
- Question: How is the molecular gas in the Zw 3146 BCG distributed relative to the X-ray cavities, and why are the molecular gas and the mm continuum (AGN) source offset?  
  > "Here we present a new ALMA observation targeting the CO(1-0) emission line in the BCG of Zw 3146, which is one of the most extreme cool core clusters and brightest CO emitters known." (Introduction); "The molecular gas and continuum source are mutually offset by 2.6 kpc, with no detected line emission coincident with the continuum source." (abstract)
- Target **Zw 3146 BCG (2MASX J10233960+0411116)**: coordinates R.A. 10:23:39.6340, decl. +4:11:10.660 (BCG position given in the paper)  
  > "The BCG of the ZwCl 3146 galaxy cluster (2MASX J10233960+0411116" (Observations and Data Reduction); "R.A.: 10:23:39.6340, decl.: +4:11:10.660" (Observations and Data Reduction); "At the redshift of Zw 3146 ($z=0.29007$), the angular scale is $1''=4.35\rm\; kpc$ and the luminosity distance is $1500\rm\; Mpc$." (Introduction); "Throughout this work we assume a standard $\Lambda$-CDM cosmology with $H_0=70\hbox{$\hbox{$\rm\; km\rm\; s^{-1}\,$}\rm\; Mpc^{-1}\,$}$, $\Omega_{{\rm m}, 0}=0.3$, and $\Omega_{\Lambda, 0}=0.7$." (Introduction); z/distance z = 0.29007 (molecular gas); luminosity distance 1500 Mpc; 1'' = 4.35 kpc  
  > "The BCG of the ZwCl 3146 galaxy cluster (2MASX J10233960+0411116" (Observations and Data Reduction); "R.A.: 10:23:39.6340, decl.: +4:11:10.660" (Observations and Data Reduction); "At the redshift of Zw 3146 ($z=0.29007$), the angular scale is $1''=4.35\rm\; kpc$ and the luminosity distance is $1500\rm\; Mpc$." (Introduction); "Throughout this work we assume a standard $\Lambda$-CDM cosmology with $H_0=70\hbox{$\hbox{$\rm\; km\rm\; s^{-1}\,$}\rm\; Mpc^{-1}\,$}$, $\Omega_{{\rm m}, 0}=0.3$, and $\Omega_{\Lambda, 0}=0.7$." (Introduction); distance from Derived from the redshift with H0 = 70 km/s/Mpc, Omega_m = 0.3, Omega_Lambda = 0.7  
  > "The BCG of the ZwCl 3146 galaxy cluster (2MASX J10233960+0411116" (Observations and Data Reduction); "R.A.: 10:23:39.6340, decl.: +4:11:10.660" (Observations and Data Reduction); "At the redshift of Zw 3146 ($z=0.29007$), the angular scale is $1''=4.35\rm\; kpc$ and the luminosity distance is $1500\rm\; Mpc$." (Introduction); "Throughout this work we assume a standard $\Lambda$-CDM cosmology with $H_0=70\hbox{$\hbox{$\rm\; km\rm\; s^{-1}\,$}\rm\; Mpc^{-1}\,$}$, $\Omega_{{\rm m}, 0}=0.3$, and $\Omega_{\Lambda, 0}=0.7$." (Introduction)
- Target **Zw 3146 mm continuum source (AGN)**: coordinates R.A. 10:23:39.5948, decl. +4:11:11.032  
  > "A single, unresolved source was identified (R.A.: 10:23:39.5948, decl.: +4:11:11.032), which had a total integrated flux density of $133\pm13 \rm\; \mu Jy$." (Millimetre Continuum); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01056.S
- bands: Band 3, centered on CO(1-0) at 89.316 GHz  
  > "was observed with ALMA in Band 3 (Cycle 4, ID 2018.1.01056.S, PI Vantyghem), centered on the CO(1-0) line at $89.316\rm\; GHz$." (Observations and Data Reduction)
- frequencies and spectral setup: One FDM spectral window for CO (1.875 GHz bandwidth, 488 kHz = 1.6 km/s resolution) plus three TDM basebands (2 GHz each, 15.625 MHz resolution) for continuum  
  > "A single spectral window in the frequency division correlator mode was used to study the CO spectral line with 1.875 GHz bandwidth and 488 kHz" (Observations and Data Reduction); "An additional three basebands with the time division correlator mode, each with a 2 GHz bandwidth and frequency resolution of $15.625\rm\; MHz$, were employed in order to measure the continuum source." (Observations and Data Reduction)
- continuum bandwidth: three basebands, 2 GHz bandwidth each  
  > "each with a 2 GHz bandwidth and frequency resolution of $15.625\rm\; MHz$" (Observations and Data Reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 41 to 3637 m; 41-44 antennas  
  > "41-44 antennas were used in these observations, with baselines ranging from $41$ to $3637\rm\; m$." (Observations and Data Reduction)
- angular resolution: 0.30 x 0.26 arcsec, P.A. -79.5 deg (final CO(1-0) cube)  
  > "The final CO(1-0) data cube had a synthesized beam of $0.30\times0.26$ arcsec (P.A. $-79.5^{\circ}$) and was binned to a velocity resolution of $20\hbox{$\rm\; km\rm\; s^{-1}\,$}$." (Observations and Data Reduction)
- max recoverable scale: 10 arcsec  
  > "This corresponds to a maximum recoverable scale of $10''$." (Observations and Data Reduction)
- sensitivity: line cube RMS 2.4 mJy/beam (20 km/s channels); continuum RMS 7.5 uJy/beam  
  > "The RMS noise in line-free channels was $2.4\rm\; mJy~{\rm beam}^{-1}$." (Observations and Data Reduction); "Given the RMS in the continuum image of $7.5\hbox{$\rm\; \mu Jy\rm\; beam^{-1}\,$}$, any source brighter than $22.5\rm\; \mu Jy$ would be detected in our observations." (Emission from a lobe)
- time on source: 106 minutes total on-source  
  > "with a total on-source integration time of 106 minutes" (Observations and Data Reduction)
- observing dates: 15-19 August 2019, three observing blocks  
  > "The observations were conducted in three blocks from 15-19 August 2019" (Observations and Data Reduction)
- pi or archival as stated: New observation, PI Vantyghem (an author)  
  > "We present a recent ALMA observation of the CO(1-0) line emission in the central galaxy of the Zw 3146 galaxy cluster" (abstract); "was observed with ALMA in Band 3 (Cycle 4, ID 2018.1.01056.S, PI Vantyghem)" (Observations and Data Reduction)
- Line: CO J=1-0 (not stated (observation centered on 89.316 GHz))
- Other facility **Chandra**: Archival X-ray data used for the cavity search, taken from reductions by Hogan17a and Pulido18  
  > "we present a new search for cavities in Zw 3146 using the *Chandra* data reduced by (cite: Hogan17a) and (cite: Pulido18)." (X-ray Cavities)
- Other facility **HST (WFPC2 F606W, ACS/SBC F140LP and F165LP)**: Optical, Ly-alpha and FUV images compared with the CO map  
  > "*HST* WFPC2 F606W, Ly-$\alpha$ (*HST* ACS/SBC F140LP), and FUV (*HST* ACS/SBC F165LP) images (cite: ODea10; Tremblay15)" (Molecular Gas Distribution and Kinematics)
- Other facility **DECaLS (Legacy Survey)**: r-band image used as a tracer of the stellar continuum and galactic center  
  > "we obtained a Dark Energy Camera Legacy Survey (*DECaLS*) $r$-band image" (The Molecular Gas-AGN Offset)
- Other facility **VLA and BIMA**: Lower-frequency continuum flux densities for the SED  
  > "flux measurements at lower frequencies, which were obtained from either the VLA or BIMA (cite: Egami06; Coble07; Giacintucci14)" (Millimetre Continuum)
- Other facility **XMM-Newton RGS**: Archival spectral analysis of cooling rate (Liu et al. in preparation)  
  > "a recent spectral analysis conducted using archival data from the *XMM-Newton* Reflection Grating Spectrometer, following the prescription of (cite: Liu19)" (Origin of the Molecular Gas)
- Other facility **IRAM-30m and OVRO**: Earlier CO(1-0) integrated fluxes used to estimate recovered flux fraction  
  > "with the IRAM-30m telescope and Owens Valley Radio Telescope (OVRO) yielded CO(1-0) integrated fluxes of" (Molecular Gas Mass)
- External data: Earlier CO(1-0) integrated fluxes: IRAM-30m 5.2+-1.2 Jy km/s, OVRO 5.7+-0.9 Jy km/s  
  > "yielded CO(1-0) integrated fluxes of $5.2\pm1.2\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ and $5.7\pm0.9\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$, respectively (cite: Edge01; Edge03)" (Molecular Gas Mass) [from (cite: Edge01; Edge03)]
- External data: Nebular redshift 0.29060+-0.00010 of the emission-line nebula  
  > "Previous works on Zw 3146 generally adopted a redshift of $0.29060\pm0.00010$, which was determined from the emission-line nebula (cite: Allen92)." (Systemic Velocity) [from (cite: Allen92)]
- External data: Deprojected thermodynamic radial profiles of the ICM used for cavity pressure, temperature and density  
  > "All necessary thermodynamic quantities were obtained by interpolating the deprojected radial profiles from (cite: Pulido18)." (X-ray Cavities) [from (cite: Pulido18)]
- External data: Cluster mass profile used for the acceleration under gravity  
  > "The acceleration under gravity at radius $R$ was determined using the cluster mass profile from (cite: Pulido18)." (X-ray Cavities) [from (cite: Pulido18)]
- External data: Lower-frequency (VLA, BIMA) continuum flux measurements for the SED  
  > "flux measurements at lower frequencies, which were obtained from either the VLA or BIMA (cite: Egami06; Coble07; Giacintucci14)" (Millimetre Continuum) [from (cite: Egami06; Coble07; Giacintucci14)]
- External data: Black hole mass 1.6e9 Msun of the BCG, estimated from 2MASS K-band magnitude  
  > "The black hole mass in the Zw 3146 BCG, estimated using the 2MASS K-band magnitude, is $M_{\bullet} = 1.6\ensuremath{\times 10^{9}} \hbox{$\rm\thinspace M_{\odot}$}$ (cite: Main17)." (Acceleration by an asymmetric radio jet) [from (cite: Main17)]
- External data: 31 GHz source density of 16.7 per square degree for flux >= 1 mJy  
  > "we have instead used a $31\rm\; GHz$ survey of known extragalactic sources (cite: Mason09)." (The SMBH of a secondary galaxy) [from (cite: Mason09)]
- External data: Spectral index of 0.4 used to scale 31 GHz flux to 100 GHz  
  > "assuming a spectral index of 0.4 (cite: Marriage11)" (The SMBH of a secondary galaxy) [from (cite: Marriage11)]
- External data: Galactic CO-to-H2 conversion factor X_CO,gal = 2e20 cm^-2 (K km/s)^-1  
  > "Its nominal value is the mean empirically-derived Galactic value, $X_{\rm CO, gal} = 2\ensuremath{\times 10^{20}}\hbox{$\rm\; cm^{-2}\,$}(\rm\; K\hbox{$\rm\; km\rm\; s^{-1}\,$})^{-1}$ (cite: Bolatto13)." (Molecular Gas Mass) [from (cite: Bolatto13)]
- External data: Star formation rate of 70 Msun/yr  
  > "The SFR in Zw 3146, $70\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ (cite: Egami06)" (Molecular Gas Mass) [from (cite: Egami06)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline reduction scripts  
  > "The observations were calibrated in casa version 5.4.0 (cite: casa) using the pipeline reduction scripts." (Observations and Data Reduction)
- casa version: CASA 5.4.0  
  > "The observations were calibrated in casa version 5.4.0 (cite: casa) using the pipeline reduction scripts." (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration attempted but gave no S/N improvement (continuum too faint)  
  > "Additional phase self-calibration was attempted, but the continuum source was too faint to provide an improvement in signal-to-noise." (Observations and Data Reduction)

### Imaging

- task: uvcontsub and clean  
  > "Continuum-subtracted data cubes were created using uvcontsub and clean." (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Images of the line emission were reconstructed using Briggs weighting with a robust parameter of 0.5." (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub (visibility-plane)  
  > "Continuum-subtracted data cubes were created using uvcontsub and clean." (Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: Spectra corrected for primary beam response and instrumental broadening  
  > "All spectra have been corrected for the response of the primary beam and instrumental broadening." (Table of spectral fits)
- array combination: _not stated_
- smoothing: Binned to a velocity resolution of 20 km/s  
  > "and was binned to a velocity resolution of $20\hbox{$\rm\; km\rm\; s^{-1}\,$}$" (Observations and Data Reduction)
- final beam: 0.30 x 0.26 arcsec, P.A. -79.5 deg  
  > "The final CO(1-0) data cube had a synthesized beam of $0.30\times0.26$ arcsec (P.A. $-79.5^{\circ}$)" (Observations and Data Reduction)
- final rms: 2.4 mJy/beam in line-free channels  
  > "The RMS noise in line-free channels was $2.4\rm\; mJy~{\rm beam}^{-1}$." (Observations and Data Reduction)

### Inherited from earlier work

- Chandra data reduction  
  > "we present a new search for cavities in Zw 3146 using the *Chandra* data reduced by (cite: Hogan17a) and (cite: Pulido18)." (X-ray Cavities) [from (cite: Hogan17a); (cite: Pulido18)]
- Gaussian gradient magnitude filtering of the X-ray image  
  > "we have processed this image using the gaussian gradient magnitude algorithm (cite: Sanders16a; Sanders16b) with a radially-dependent filtering kernel." (X-ray Cavities) [from (cite: Sanders16a; Sanders16b)]
- Qualitative cavity figure of merit scheme  
  > "A qualitative figure of merit (FOM), which describes a cavity’s contrast with its surroundings, was provided for each cavity (cite: Rafferty06)." (X-ray Cavities) [from (cite: Rafferty06)]
- Cavity age estimators (sound crossing and buoyant rise time)  
  > "The cavity age was estimated using both the sound crossing time and buoyant rise time (cite: Birzan04)." (X-ray Cavities) [from (cite: Birzan04)]
- Drag coefficient C = 0.75 in the buoyant rise time  
  > "Here $C=0.75$ is the drag coefficient (cite: Churazov01)" (X-ray Cavities) [from (cite: Churazov01)]
- CO flux to molecular mass conversion  
  > "The integrated flux ($S_{\rm CO}\Delta v$) of the CO(1-0) line can be converted to molecular gas mass through (cite: Solomon87; Solomon05; Bolatto13)" (Molecular Gas Mass) [from (cite: Solomon87; Solomon05; Bolatto13)]
- Adoption of the Galactic X_CO as standard practice  
  > "Lacking an independent calibration of $X_{\rm CO}$ in BCGs, we follow standard practice by adopting the Galactic value throughout this work." (Molecular Gas Mass) [from (cite: Bolatto13)]
- XMM-Newton RGS cooling-rate analysis prescription  
  > "following the prescription of (cite: Liu19)" (Origin of the Molecular Gas) [from (cite: Liu19); Liu et al. in preparation]

### Not stated but needed to reproduce (our reading)

- Flux, bandpass and phase calibrator names and the per-execution-block configurations (not given)
- Pipeline version (only CASA 5.4.0 is stated)
- Number of spectral windows and exact rest-frame frequency or velocity axis used for CO(1-0)
- uvcontsub line-free channel ranges and fit order
- clean cell size, image size, niter, threshold, masking and deconvolver for the line cube
- Whether the cube was primary-beam corrected before fitting and how instrumental broadening was modelled
- uv range, weighting and beam for the 96.193 GHz continuum image
- Initial guesses and bounds of the Gaussian fits, and how the Monte Carlo significance test was set up
- Exact boxes used for the Central Clump and Clumps 1-3 spectra
- Chandra observation IDs and exposure used for the cavity images
- Ellipse parameters (centres, position angles) of the six cavities and the radial profile values used
- Literature flux densities for the SED, and the frequencies used in the power-law fit

## Analysis recipe

1. **Calibrate and image the CO(1-0) cube and continuum**: CASA pipeline calibration, uvcontsub continuum subtraction, clean imaging with Briggs weighting  
  > "The observations were calibrated in casa version 5.4.0 (cite: casa) using the pipeline reduction scripts." (Observations and Data Reduction); "Continuum-subtracted data cubes were created using uvcontsub and clean." (Observations and Data Reduction)
   - software: CASA 5.4.0, uvcontsub, clean
   - parameter: robust = 0.5  
  > "Images of the line emission were reconstructed using Briggs weighting with a robust parameter of 0.5." (Observations and Data Reduction)
   - parameter: velocity binning to 20 km/s  
  > "and was binned to a velocity resolution of $20\hbox{$\rm\; km\rm\; s^{-1}\,$}$" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Phase self-calibration was attempted but did not improve S/N  
  > "Additional phase self-calibration was attempted, but the continuum source was too faint to provide an improvement in signal-to-noise." (Observations and Data Reduction)
2. **Measure the molecular gas systemic redshift**: Extract a spectrum from a 3'' x 3'' region and fit a single Gaussian  
  > "This was determined by extracting a spectrum from a $3''\times 3''$ region that encompasses all of the observed line emission" (Systemic Velocity)
   - parameter: 3'' x 3'' extraction region  
  > "This was determined by extracting a spectrum from a $3''\times 3''$ region that encompasses all of the observed line emission" (Systemic Velocity)
   - fitting: Single Gaussian fit giving molecular gas redshift 0.29007 +- 0.00003  
  > "A single-gaussian fitted to the spectrum yields a molecular gas redshift of $0.29007\pm0.00003$." (Systemic Velocity)
   - validation: Consistent with earlier CO(1-0) centroids  
  > "This is consistent with the CO(1-0) velocity centroids measured in previous work (cite: Edge01)." (Systemic Velocity)
3. **Derive total CO flux and molecular gas mass**: Fit the integrated spectrum from a 13 x 13 kpc box with a single Gaussian and convert the integrated flux to mass with the X_CO relation  
  > "A spatially-integrated CO(1-0) spectrum was extracted from a $13\times 13\rm\; kpc$ ($3''\times 3''$) box containing all of the detected line emission." (Molecular Gas Mass); "The integrated flux ($S_{\rm CO}\Delta v$) of the CO(1-0) line can be converted to molecular gas mass through (cite: Solomon87; Solomon05; Bolatto13)" (Molecular Gas Mass)
   - parameter: Luminosity distance 1500 Mpc at z = 0.29007  
  > "At the redshift of Zw 3146 ($z=0.29007$), the angular scale is $1''=4.35\rm\; kpc$ and the luminosity distance is $1500\rm\; Mpc$." (Introduction)
   - assumption: Galactic X_CO = 2e20 cm^-2 (K km/s)^-1  
  > "Its nominal value is the mean empirically-derived Galactic value, $X_{\rm CO, gal} = 2\ensuremath{\times 10^{20}}\hbox{$\rm\; cm^{-2}\,$}(\rm\; K\hbox{$\rm\; km\rm\; s^{-1}\,$})^{-1}$ (cite: Bolatto13)." (Molecular Gas Mass); "Lacking an independent calibration of $X_{\rm CO}$ in BCGs, we follow standard practice by adopting the Galactic value throughout this work." (Molecular Gas Mass)
   - fitting: Single Gaussian fit to the spatially integrated spectrum  
  > "is best-fit by a single Gaussian with total flux $2.78\pm0.17\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$. This corresponds to $5.05\pm0.50\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas." (Molecular Gas Mass)
   - validation: Compared with earlier single-dish and OVRO fluxes: ALMA recovers about 50%, attributed to missing large-scale flux  
  > "Our ALMA observation recovers 50% of this flux" (Molecular Gas Mass); "This suggests that our ALMA observations are missing large-scale flux, predominantly on scales of $\sim5''$ ($22\rm\; kpc$)." (Molecular Gas Mass)
4. **Map integrated flux, velocity and FWHM pixel by pixel**: Fit spectra from individual pixels (each averaged over a synthesized-beam-sized box) with up to two Gaussians  
  > "Maps of integrated flux, velocity, and FWHM of the CO(1-0) line were created by fitting the spectra extracted from individual pixels within the data cube." (Molecular Gas Distribution and Kinematics); "Each spectrum was averaged over a box the size of the synthesized beam." (Molecular Gas Distribution and Kinematics)
   - parameter: Monte Carlo with 10000 iterations, 5 sigma detection threshold for each component  
  > "The significance of each velocity component was tested using a Monte Carlo analysis employing 10000 iterations, with a detection requiring $5\sigma$ significance." (Molecular Gas Distribution and Kinematics)
   - assumption: Instrumental broadening incorporated into the model  
  > "Instrumental broadening has been incorporated into the model." (Molecular Gas Distribution and Kinematics)
   - fitting: Up to two Gaussian components per pixel; the second only attempted if one was required; one component sufficed everywhere  
  > "We found that a single Gaussian component was sufficient to accurately model the spectrum for each pixel." (Molecular Gas Distribution and Kinematics)
   - validation: _not stated_
5. **Isolate the molecular extensions by subtracting the unresolved central source and fit clump spectra**: Subtract a scaled, tophat-convolved beam image centred on the brightest pixel from the integrated flux map, then fit spectra of the clumps  
  > "First we created an image of the beam centered on the pixel with the largest integrated flux." (Molecular Gas Distribution and Kinematics); "The image was then scaled to match the flux of the brightest pixel and subtracted from the integrated flux map." (Molecular Gas Distribution and Kinematics)
   - parameter: Beam image convolved with a beam-shaped tophat kernel  
  > "This image was further convolved with a beam-shaped tophat kernel, as the pixel-based spectral fitting used to create the maps extracts the emission from a region of this shape." (Molecular Gas Distribution and Kinematics)
   - assumption: The central peak is an unresolved point source  
  > "The molecular extensions can be better visualized by subtracting the contribution from an unresolved point source coincident with the CO(1-0) peak." (Molecular Gas Distribution and Kinematics)
   - fitting: Gaussian fits to the spectrum of each region, listed in the spectra table (chi^2/dof given)  
  > "The corresponding spectra are shown in Fig. [5](#fig:clump_spectra), and their spectral fits are listed in Table [\[tab:spectra\]](#tab:spectra)." (Molecular Gas Distribution and Kinematics)
   - validation: Result compared with PKS0745-191 CO(1-0) and CO(3-2)  
  > "Subtracting the central, unresolved emission from the PKS0745-191 CO(1-0) data (see Section [3.2](#sec:kinematics) for the same analysis on Zw 3146), $52\%$ of the total flux can be attributed to an unresolved clump at the peak emission position." (Comparison to other BCGs)
6. **Measure the 3 mm continuum and fit its SED**: Image line-free channels at 96.193 GHz in a 40'' square, fit a 2D Gaussian, then fit a power law to the SED with lower-frequency literature fluxes  
  > "An image of the continuum at $96.193\rm\; GHz$ ($3.1166\rm\; mm$) was created by imaging the line-free channels in a square region measuring $40''$ on each side." (Millimetre Continuum); "A two-dimensional gaussian fit to the continuum flux yielded an accuracy for the centroid of $0.006$ arcseconds." (Millimetre Continuum)
   - parameter: Contours start at 3 sigma with sigma = 7.45 uJy/beam, steps of 4 sigma  
  > "These contours begin at $3\sigma$, where $\sigma=7.45\hbox{$\rm\; \mu Jy\rm\; beam^{-1}\,$}$, and increase in $4\sigma$ steps." (Millimetre Continuum)
   - assumption: Power law S_nu proportional to nu^-alpha  
  > "Following the convention $S_{\nu} \propto \nu^{-\alpha}$" (Footnote 1)
   - fitting: Power-law fit to the SED giving alpha = 0.685 +- 0.063  
  > "The spectral energy distribution (SED) is best fit by a power law with spectral index[^1] $\alpha = 0.685\pm0.063$, which is a typical value for an AGN (cite: Hogan15a)." (Millimetre Continuum)
   - validation: No absorption against the continuum source detected at native velocity resolution  
  > "We searched for, but did not detect, evidence for absorption against the continuum source using the native velocity resolution of the observations." (Millimetre Continuum)
7. **Quantify and check the gas-continuum offset**: Compare CO and continuum peak positions; check against VLA positions and the DECaLS r-band stellar centre  
  > "The two peaks are $2.6\rm\; kpc$ ($0.6''$) apart, and only a minimal overlap is present in the fainter reaches of the two distributions." (The Molecular Gas-AGN Offset)
   - assumption: Offset cannot come from phase calibration because line and continuum share the same observation  
  > "This offset cannot originate from a phase calibration issue, as the continuum and line measurements are obtained from the same observation." (The Molecular Gas-AGN Offset)
   - fitting: _not stated_
   - validation: VLA 4.9 GHz centroid lies 0.3'' SSW of the ALMA continuum; DECaLS shows the gas at the galactic center  
  > "In a VLA 4.9 GHz observation the continuum centroid is $0.3''$ SSW of the ALMA continuum source (cite: ODea10)." (The Molecular Gas-AGN Offset); "It is the molecular gas that is coincident with the galactic center, not the continuum emission from the AGN." (The Molecular Gas-AGN Offset)
8. **Identify X-ray cavities and derive their energetics**: Apply a GGM filter to the Chandra image, manually identify cavities as ellipses, then compute enthalpy 4pV, ages and power from interpolated deprojected profiles  
  > "We manually identified six candidate X-ray cavities using a combination of the GGM filtered image and original X-ray image." (X-ray Cavities); "The enthalpy required to inflate a cavity filled with relativistic gas is given by $E_{\rm cav}=4pV$, where $p$ is the cavity pressure and $V$ is its volume." (X-ray Cavities)
   - software: gaussian gradient magnitude algorithm
   - parameter: Volume from geometric mean of oblate and prolate geometries; 15% uncertainty in semiaxes a and b  
  > "First, a $15\%$ uncertainty was assumed in both $a$ and $b$ and propagated." (X-ray Cavities)
   - parameter: Mean cavity power = E_cav / t_buoy  
  > "The buoyancy time was used to determine the mean cavity power, $P_{\rm cav} = E_{\rm cav}/t_{\rm buoy}$." (X-ray Cavities)
   - assumption: Cavity in pressure balance with the surrounding gas  
  > "The cavity was assumed to be in pressure balance with the surrounding gas." (X-ray Cavities)
   - assumption: Efficiency epsilon = 0.1 for accreted mass  
  > "which we assume to be $0.1$" (X-ray Cavities)
   - fitting: _not stated_
   - validation: Sound crossing and buoyancy times agree within 20% for all cavities  
  > "The two timescales agree to within $20\%$ for all cavities." (X-ray Cavities)
9. **Test explanations for the gas-continuum offset**: Chance-alignment probability from 1000 randomly populated fields; momentum-thrust acceleration from cavity D versus restoring acceleration of a singular isothermal sphere  
  > "We then randomly populated 1000 fields each with a source density of $16.7\deg^{-2}$." (The SMBH of a secondary galaxy); "Assuming the BCG is represented by a singular isothermal sphere with velocity dispersion $\sigma_{\ast}=300\hbox{$\rm\; km\rm\; s^{-1}\,$}$" (Acceleration by an asymmetric radio jet)
   - assumption: 31 GHz source density scaled to 100 GHz  
  > "we have instead used a $31\rm\; GHz$ survey of known extragalactic sources (cite: Mason09)." (The SMBH of a secondary galaxy)
   - fitting: _not stated_
   - validation: Chance alignment probability 1.2e-6 and jet acceleration 40 times too small, so both disfavoured  
  > "This exercise results in a probability of $1.2\ensuremath{\times 10^{-6}}$ that two sources are separated by $<0.6''$." (The SMBH of a secondary galaxy); "An asymmetric jet can therefore not account for the $2.6\rm\; kpc$ displacement of the continuum source." (Acceleration by an asymmetric radio jet)

## Software

- **CASA** 5.4.0: Calibration with the pipeline reduction scripts and imaging  
  > "The observations were calibrated in casa version 5.4.0 (cite: casa) using the pipeline reduction scripts." (Observations and Data Reduction)
- **uvcontsub** : Continuum subtraction before imaging  
  > "Continuum-subtracted data cubes were created using uvcontsub and clean." (Observations and Data Reduction)
- **clean** : Imaging the continuum-subtracted data cubes  
  > "Continuum-subtracted data cubes were created using uvcontsub and clean." (Observations and Data Reduction)
- **gaussian gradient magnitude (GGM) algorithm** : Edge-enhancing filter on the Chandra surface brightness image  
  > "we have processed this image using the gaussian gradient magnitude algorithm (cite: Sanders16a; Sanders16b) with a radially-dependent filtering kernel." (X-ray Cavities)
- **Legacy Survey sky viewer** : Obtaining the DECaLS r-band image  
  > "we obtained a Dark Energy Camera Legacy Survey (*DECaLS*) $r$-band image using the legacy skyviewer" (The Molecular Gas-AGN Offset)
- **Astropy** : Acknowledged as used in this research; specific use not stated  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy." (Acknowledgments)
- **APLpy** : Plotting package for Python, acknowledged as used  
  > "This research made use of APLpy, an open-source plotting package for Python hosted at http://aplpy.github.com." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas redshift | 0.29007 | 0.00003 | dimensionless | 2 | A single-gaussian fitted to the spectrum yields a molecular gas redshift of $0.29007\pm0.00003$. |
| Molecular gas blueshift relative to nebular redshift | 158 | 30 | km/s | 2 | The molecular gas rest frame is blueshifted by $158\pm30\hbox{$\rm\; km\rm\; s^{-1}\,$}$ from this nebular redshift. |
| Total CO(1-0) integrated flux (all emission) | 2.78 | 0.17 | Jy km/s | 3 | is best-fit by a single Gaussian with total flux $2.78\pm0.17\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$. This corresponds to $5.05\pm0.50\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas. |
| Total molecular gas mass (Galactic X_CO) | 5.05e10 | 0.50e10 | Msun | 3 | is best-fit by a single Gaussian with total flux $2.78\pm0.17\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$. This corresponds to $5.05\pm0.50\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas. |
| FWHM of integrated CO(1-0) line (all emission) | 353 | 24 | km/s | 3 | $353\pm24$ |
| Fraction of earlier CO(1-0) flux recovered by ALMA | 50% | not stated | percent | 3 | Our ALMA observation recovers 50% of this flux |
| Gas mass, Central Clump | 36.4e8 | 2.3e8 | Msun | 5 | $36.4\pm2.3$ |
| Gas mass, Clump 1 | 52.7e8 | 3.7e8 | Msun | 5 | $52.7\pm3.7$ |
| Gas mass, Clump 2 | 78.3e8 | 6.7e8 | Msun | 5 | $78.3\pm6.7$ |
| Gas mass, Clump 3 | 83.7e8 | 7.1e8 | Msun | 5 | $83.7\pm7.1$ |
| Integrated flux, Central Clump | 0.201 | 0.013 | Jy km/s | 5 | $0.201\pm0.013$ |
| Integrated flux, Clump 1 | 0.289 | 0.02 | Jy km/s | 5 | $0.289\pm0.02$ |
| Integrated flux, Clump 2 | 0.429 | 0.036 | Jy km/s | 5 | $0.429\pm0.036$ |
| Integrated flux, Clump 3 | 0.46 | 0.04 | Jy km/s | 5 | $0.46\pm0.04$ |
| Fraction of CO(1-0) flux in the unresolved central source | 22% | not stated | percent | 5 | The unresolved emission subtracted from the integrated flux map amounted to 22% of the total flux. |
| Fraction of total CO flux in outer filament portions | 40% | not stated | percent | 5 | account for $40\%$ of the total flux |
| 3 mm continuum integrated flux density at 96.193 GHz | 133 | 13 | uJy | 6 | A single, unresolved source was identified (R.A.: 10:23:39.5948, decl.: +4:11:11.032), which had a total integrated flux density of $133\pm13 \rm\; \mu Jy$. |
| Continuum centroid accuracy | 0.006 | not stated | arcsec | 6 | A two-dimensional gaussian fit to the continuum flux yielded an accuracy for the centroid of $0.006$ arcseconds. |
| Continuum SED spectral index alpha | 0.685 | 0.063 | dimensionless | 6 | The spectral energy distribution (SED) is best fit by a power law with spectral index[^1] $\alpha = 0.685\pm0.063$, which is a typical value for an AGN (cite: Hogan15a). |
| Gas-continuum offset | 2.6 kpc (0.6 arcsec) | not stated | kpc | 7 | The two peaks are $2.6\rm\; kpc$ ($0.6''$) apart, and only a minimal overlap is present in the fainter reaches of the two distributions. |
| Cavity A 4pV | 161 | +58/-56 | 1e58 erg | 8 | $161^{+58}_{-56}$ |
| Cavity A buoyant rise time | 41.2 | 2.8 | Myr | 8 | $41.2\pm2.8$ |
| Cavity A mean power | 12.4 | +4.6/-4.4 | 1e44 erg/s | 8 | $12.4^{+4.6}_{-4.4}$ |
| Cavity B 4pV | 214 | +77/-74 | 1e58 erg | 8 | $214^{+77}_{-74}$ |
| Cavity B buoyant rise time | 36.3 | 2.4 | Myr | 8 | $36.3\pm2.4$ |
| Cavity B mean power | 18.7 | +6.9/-6.6 | 1e44 erg/s | 8 | $18.7^{+6.9}_{-6.6}$ |
| Cavity C 4pV | 204 | +86/-68 | 1e58 erg | 8 | $204^{+86}_{-68}$ |
| Cavity C buoyant rise time | 71.2 | +4.4/-4.3 | Myr | 8 | $71.2^{+4.4}_{-4.3}$ |
| Cavity C mean power | 9.08 | +3.9/-3.1 | 1e44 erg/s | 8 | $9.08^{+3.9}_{-3.1}$ |
| Cavity D 4pV | 30.6 | 11 | 1e58 erg | 8 | $30.6\pm11$ |
| Cavity D buoyant rise time | 6.68 | +0.62/-0.6 | Myr | 8 | $6.68^{+0.62}_{-0.6}$ |
| Cavity D mean power | 14.5 | +5.5/-5.3 | 1e44 erg/s | 8 | $14.5^{+5.5}_{-5.3}$ |
| Cavity E 4pV | 86.6 | +31/-29 | 1e58 erg | 8 | $86.6^{+31}_{-29}$ |
| Cavity E buoyant rise time | 52.1 | 3.3 | Myr | 8 | $52.1\pm3.3$ |
| Cavity E mean power | 5.27 | +1.9/-1.8 | 1e44 erg/s | 8 | $5.27^{+1.9}_{-1.8}$ |
| Cavity F 4pV | 118 | +40/-39 | 1e58 erg | 8 | $118^{+40}_{-39}$ |
| Cavity F buoyant rise time | 77.9 | +4.8/-4.7 | Myr | 8 | $77.9^{+4.8}_{-4.7}$ |
| Cavity F mean power | 4.8 | 1.6 | 1e44 erg/s | 8 | $4.8\pm1.6$ |
| Total accreted gas mass needed for the outbursts | 4.6e7 | not stated | Msun | 8 | The total accreted gas mass of $4.6\ensuremath{\times 10^{7}}\hbox{$\rm\thinspace M_{\odot}$}$ can easily be supplied by the observed $5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ of molecular gas. |
| Total hot gas mass displaced by the cavities | 1.3e11 | not stated | Msun | 8 | Combined, the cavities displace a total of $1.3\ensuremath{\times 10^{11}}\hbox{$\rm\thinspace M_{\odot}$}$ of hot gas. |
| Probability of chance alignment of a background source within 0.6 arcsec | 1.2e-6 | not stated | dimensionless | 9 | This exercise results in a probability of $1.2\ensuremath{\times 10^{-6}}$ that two sources are separated by $<0.6''$. |
| Black hole acceleration from cavity D one-sided jet | 1.5e-8 | not stated | cm s^-2 | 9 | evaluates to $1.5\ensuremath{\times 10^{-8}}\hbox{$\rm\; cm\rm\; s^{-2}\,$}$. |
| Restoring gravitational acceleration at 1 kpc displacement | 5.8e-7 | not stated | cm s^-2 | 9 | at a displacement of $R=1\rm\; kpc$ is $5.8\ensuremath{\times 10^{-7}}\hbox{$\rm\; cm\rm\; s^{-2}\,$}$. |

## Qualitative findings

- The molecular extensions show no clear velocity gradients  
  > "These extensions do not exhibit any clear velocity gradients." (Molecular Gas Distribution and Kinematics)
- No other CO(1-0) emission was detected in the primary beam  
  > "No other CO(1-0) line emission was detected throughout the $70''$ primary beam of these observations." (Molecular Gas Mass)
- No absorption against the continuum source was detected  
  > "We searched for, but did not detect, evidence for absorption against the continuum source using the native velocity resolution of the observations." (Millimetre Continuum)
- The molecular gas, not the continuum source, sits at the galactic center  
  > "It is the molecular gas, not the continuum source, that lies at the gravitational center of the brightest cluster galaxy." (abstract)
- The cavities could have lifted enough hot gas to form the whole cold reservoir  
  > "Thus these cavities could have initiated the formation of the entire $5\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$ reservoir of cold gas." (Origin of the Molecular Gas)

## Claim tuples

- H: Does the Zw 3146 BCG host a massive, compact molecular gas reservoir with filamentary structure like other BCGs? | E: ALMA Band 3 CO(1-0) cube, integrated spectrum, pixel-wise Gaussian maps and beam subtraction | R: 5.05e10 Msun within the central 4 kpc, marginally resolved into three extensions | F: The gas is compact and resembles filaments seen in similar systems, though none of the extensions is resolved | **supported**
- H: Do the molecular extensions form from ICM uplifted in the wakes of rising X-ray cavities (stimulated feedback)? | E: Manual identification of six Chandra cavities and comparison of displaced hot gas mass with molecular masses | R: Each extension trails a cavity; cavities displaced 1.3e11 Msun of hot gas, more than the 5e10 Msun cold gas | F: Stimulated feedback can contribute but many feedback cycles are needed for the whole reservoir | **partially**
- H: Is the molecular gas in ordered motion (a rotating disk)? | E: Pixel-wise Gaussian fits for velocity and FWHM maps and the integrated line profile | R: No clear velocity gradients and no double-horned profile | F: No ordered motion is seen; any disk would have to be unresolved | **supported**
- H: Is the mm continuum (AGN) source coincident with the molecular gas and galactic center? | E: Compare CO and 96 GHz continuum peaks and a DECaLS r-band stellar image | R: The peaks are 2.6 kpc apart; gas coincides with the stellar centroid | F: The continuum source is displaced from the galactic center and the gas | **supported**
- H: What causes the displacement of the continuum source: lobe, secondary galaxy, gravitational-wave recoil or asymmetric jet? | E: Chance alignment Monte Carlo on source density, spectral index argument, and acceleration estimates | R: Chance alignment probability 1.2e-6; jet acceleration 40 times too small; HST features suggest a merger | F: A merger remnant nucleus or a recent gravitational-wave recoil is favoured; asymmetric jet, lobe and chance alignment are unlikely | **partially**

## Reasoning

- Why this data: Zw 3146 has a very massive reservoir and strong AGN feedback, so it is a prime candidate for filaments trailing cavities  
  > "The combination of a massive reservoir of molecular gas and powerful AGN feedback make Zw 3146 a prime candidate to contain molecular filaments trailing X-ray cavities, as observed in other BCGs." (Introduction)
- Why this method: Galactic X_CO adopted because no independent X_CO calibration exists for BCGs  
  > "Lacking an independent calibration of $X_{\rm CO}$ in BCGs, we follow standard practice by adopting the Galactic value throughout this work." (Molecular Gas Mass)
- Alternative: Four origins for the gas-continuum offset were considered (jet lobe, secondary galaxy, gravitational-wave recoil, asymmetric jet); the lobe, chance background source and asymmetric jet are disfavoured  
  > "The first two attribute the continuum emission to a source other than the SMBH of the BCG, namely emission from a single lobe of a radio jet or the nucleus of a secondary galaxy." (Origin of the Molecular Gas-AGN Offset)
- Alternative: A second Gaussian component per pixel was allowed but not needed  
  > "We allowed for the possibility of multiple coincident velocity structures by fitting each spectrum with up to two Gaussian components." (Molecular Gas Distribution and Kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA misses large-scale flux (about half of earlier CO flux, scales around 5 arcsec)  
  > "This suggests that our ALMA observations are missing large-scale flux, predominantly on scales of $\sim5''$ ($22\rm\; kpc$)." (Molecular Gas Mass)
- Limitation (authors): True gas morphology cannot be determined without higher resolution data  
  > "Without additional higher resolution observations of Zw 3146 we cannot conclusively determine its true molecular gas morphology." (Comparison to other BCGs)
- Limitation (authors): A molecular disk cannot be ruled out  
  > "Nevertheless, we are unable to rule out the presence of a molecular disk." (Comparison to other BCGs)
- Limitation (authors): Cavity D proximity to the cluster center gives a strong systematic effect on its age and power  
  > "Note that the proximity of cavity D to the cluster center has a strong systematic effect on the cavity age, and therefore its power." (X-ray Cavities)
- Limitation (authors): X_CO not calibrated in BCGs; Galactic value adopted  
  > "Lacking an independent calibration of $X_{\rm CO}$ in BCGs, we follow standard practice by adopting the Galactic value throughout this work." (Molecular Gas Mass)
- Caveat (inferred, ours): Gas masses depend on the Galactic X_CO and the 50% recovered flux makes them lower limits on the total reservoir
- Caveat (inferred, ours): Table mass uncertainty for all emission (504+-30 e8 Msun) differs from the text value 5.05+-0.50e10 Msun, so the error budget is unclear
- Caveat (inferred, ours): Cavity identification is manual and qualitative, so cavity sizes and energetics carry unquantified systematics
- Caveat (inferred, ours): Chance-alignment probability uses a 31 GHz source density extrapolated to 100 GHz with an assumed index and a 1 mJy limit
- Caveat (inferred, ours): Clump spectra are from unresolved extensions, so the 'filament' interpretation is tentative
- Caveat (inferred, ours): Project listed as Cycle 4 with a 2018 code and 2019 dates, which is internally inconsistent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibrator names, execution block details and full clean parameters
- Missing: uvcontsub line-free channels
- Missing: Pixel-fitting code and Monte Carlo set-up
- Missing: Chandra obsids and the cavity ellipse parameters
- Missing: Literature SED fluxes
- Missing: Liu et al. in preparation cooling rates
- Data volume (inferred): Roughly 20-40 GB raw for three Band 3 execution blocks; about 10 GB calibrated; Chandra data additional
- Score (inferred): 3/5, The ALMA project code, CASA version, robust value and beam are given and results are numeric, but clean parameters, line-free channels, calibrators and the Chandra reduction come from other works or are unstated.
- Rediscovery candidate: yes, The ALMA project is identified and the CO(1-0) flux, redshift, gas mass and continuum flux are numeric and derivable from the cube with the stated robust and velocity binning; the X-ray cavity part needs earlier reductions.

## Links

- Method: (cite: Hogan17a); (cite: Pulido18) (Chandra data reduction, deprojected profiles and mass profile used for the cavity analysis)
- Method: (cite: Sanders16a; Sanders16b) (Gaussian gradient magnitude edge-enhancing algorithm)
- Method: (cite: Rafferty06) (Cavity figure of merit scheme and earlier Zw 3146 cavities)
- Method: (cite: Birzan04) (Sound crossing and buoyant rise time prescriptions)
- Method: (cite: Liu19) (XMM-Newton RGS cooling-rate analysis prescription)
- Companion: (cite: Russell16) (PKS0745-191 CO(1-0) and CO(3-2) compared with Zw 3146)
- Companion: (cite: Russell19) (ALMA BCG sample for filament fractions and hot versus cold gas masses)
- Companion: (cite: ODea10) (VLA 4.9 GHz position and HST images of Zw 3146)
- Related: Legacy Survey DECaLS
- Related: Chandra archival observations of Zw 3146

## Checks

```json
{
 "quotes": 187,
 "quotes_ok": 187,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 43,
 "numeric_problems": 0,
 "fill": {
  "facts": 133,
  "stated": 109,
  "rate": 0.82
 },
 "evidence_ok": true
}
```
