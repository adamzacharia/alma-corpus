# Protostellar Outflows at the EarliesT Stages (POETS) VI. Evidence of disk-wind in G11.92-0.61 MM1

`2025A&A...694A..92B` | Astronomy and Astrophysics 2025 | first author: Bayandina, O. S. | arXiv: 2501.17482 | DOI: 10.1051/0004-6361/202452843

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Estimate the physical parameters of the massive protostellar system G11.92-0.61 MM1 and constrain the wind-launching mechanism (disk-wind vs X-wind)  
  > "We performed a detailed analysis of the disk-wind candidate G11.92-0.61 MM1 by estimating the physical parameters of the massive protostellar system and constraining the wind-launching mechanism." (abstract)
- Target **G11.92-0.61 MM1 (MM1a, MM1b)**: coordinates MM1a RA(J2000) 18:13:58.1106, Dec(J2000) -18:54:20.199  
  > "Located in the Galactic plane, at a distance of $3.37^{+0.39}_{-0.32}$ kpc (cite: Sato2014)" (Introduction); "18:13:58.1106$\pm$0.0001" (Table 1 (continuum sources)); "-18:54:20.199$\pm$0.001" (Table 1 (continuum sources)); z/distance 3.37 (+0.39/-0.32) kpc  
  > "Located in the Galactic plane, at a distance of $3.37^{+0.39}_{-0.32}$ kpc (cite: Sato2014)" (Introduction); "18:13:58.1106$\pm$0.0001" (Table 1 (continuum sources)); "-18:54:20.199$\pm$0.001" (Table 1 (continuum sources)); distance from Sato et al. 2014 (cite: Sato2014)  
  > "Located in the Galactic plane, at a distance of $3.37^{+0.39}_{-0.32}$ kpc (cite: Sato2014)" (Introduction); "18:13:58.1106$\pm$0.0001" (Table 1 (continuum sources)); "-18:54:20.199$\pm$0.001" (Table 1 (continuum sources))

## Data provenance

- ALMA projects: 2019.1.01639.S
- bands: Band 6 (1.3 mm continuum)  
  > "five spectral windows centred at 220.63, 222.15, 221.44, 219.91, and 219.44 GHz in Band 6" (2 Observations and data reduction); "as well as the 1.3 mm continuum" (abstract)
- frequencies and spectral setup: 5 spectral windows centred at 220.63, 222.15, 221.44, 219.91, 219.44 GHz; 960 channels of ~0.6 MHz each; ~0.7 km/s spectral resolution  
  > "The spectral setup consisted of five spectral windows centred at 220.63, 222.15, 221.44, 219.91, and 219.44 GHz in Band 6." (2 Observations and data reduction); "Each spectral window was sampled with 960 channels each of $\sim$0.6 MHz wide, providing a spectral resolution of $\sim$0.7 km s$^{-1}$." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA, 45 antennas  
  > "The array configuration was C43-9/10 with 45 antennas." (2 Observations and data reduction)
- configurations: C43-9/10  
  > "The array configuration was C43-9/10 with 45 antennas." (2 Observations and data reduction)
- baselines: _not stated_
- angular resolution: 28 mas x 25 mas, PA=-66 deg (~100 au at 3.37 kpc)  
  > "The observations provided a synthesised beam with a size of 28 mas $\times$ 25 mas, and PA=-66$^{\circ}$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum image rms ~0.1 mJy/beam  
  > "the rms of the continuum image is $\sim$0.1 mJy beam$^{-1}$" (Table 1 notes)
- time on source: 1.5 hours total observing time  
  > "for a total observing time of 1.5 hours" (2 Observations and data reduction)
- observing dates: September 29, 2021  
  > "were conducted on September 29, 2021" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CH3CN v8=1 and v=0, J=12-11 (K ladders) (not stated)
- Line: CH3OH vt=0 8(0,8)-7(1,6) E (not stated)
- Line: SO2 not stated (not stated)
- Line: SO not stated (not stated)
- External data: 22 GHz water maser proper motions, used to adopt an outflow velocity of ~30 km/s and overplotted in Fig. 9  
  > "We can assume a reasonable value of $\sim$30 km s$^{-1}$ based on the 22 GHz water maser proper motions estimated in (cite: Moscadelli2019)." (Disk-wind evidence); "as well as the 22 GHz water masers from (cite: Moscadelli2019)" (Disk-wind evidence) [from Moscadelli et al. 2019 (cite: Moscadelli2019)]
- External data: Mean CH3CN and CH3OH column densities from the CORE survey, used to compute abundances and then H2 column densities  
  > "The abundances are calculated from the average column densities reported in (cite: Gieser2021)." (Table 2 notes); "based on the typical column densities presented in Fig. 8 of (cite: Gieser2021)" (3.2 Molecular lines) [from Gieser et al. 2021 (cite: Gieser2021)]
- External data: Source distance of 3.37 kpc  
  > "Located in the Galactic plane, at a distance of $3.37^{+0.39}_{-0.32}$ kpc (cite: Sato2014)" (Introduction) [from Sato et al. 2014 (cite: Sato2014)]
- External data: Source luminosity of ~10^4 Lsun, used to check the 20 Msun central mass  
  > "agrees with the luminosity of the source of $\sim$10$^4$ L$_{\rm sun}$ (cite: Cyganowski2011; Moscadelli2016; Ilee2018)" (Discussion) [from Cyganowski et al. 2011; Moscadelli et al. 2016; Ilee et al. 2018 (cite: Cyganowski2011; Moscadelli2016; Ilee2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 and J1830-1606 (flux, delay and bandpass); J1825-1718 phase calibrator  
  > "Two sources, J1924-2914 and J1830-1606, were observed as flux, delay, and bandpass calibrators." (2 Observations and data reduction); "The quasar J1825-1718 was used as phase calibrator." (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean for line cubes and continuum; immoments for moment maps; imfit for peak positions  
  > "The spectral line and continuum images were created using the CASA task *tclean* with natural weighting." (2 Observations and data reduction); "we computed Moment 0 and 1 maps using the CASA task *immoments*" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The spectral line and continuum images were created using the CASA task *tclean* with natural weighting." (2 Observations and data reduction)
- uv taper: visibilities tapered to give ~0.15 arcsec synthesised beam (lower-resolution cubes for peak maps and outflow PV cuts)  
  > "the visibilities to create lower resolution cubes with the synthesised beam of $\sim$0.15$''$" (2 Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: moment maps: velocity range includes the target line only; threshold 5 sigma rms  
  > "The velocity range was chosen to include the target line only, and the threshold was set at a 5$\sigma$ rms level." (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 28 mas x 25 mas, PA=-66 deg  
  > "a synthesised beam with a size of 28 mas $\times$ 25 mas, and PA=-66$^{\circ}$" (2 Observations and data reduction)
- final rms: ~0.1 mJy/beam (continuum)  
  > "the rms of the continuum image is $\sim$0.1 mJy beam$^{-1}$" (Table 1 notes)

### Inherited from earlier work

- Per-channel 2D Gaussian peak-fitting method for locating line emission  
  > "This method was previously used in, for example, (cite: Moscadelli2019)." (3.4 Keplerian disk approximation) [from (cite: Moscadelli2019)]
- Planar Keplerian model used to fit all peaks  
  > "(2) a planar Keplerian model (cite: Sanchez2013) that fits all peaks" (3.4 Keplerian disk approximation) [from (cite: Sanchez2013)]
- Dust mass and H2 column density from the standard approach of Hildebrand and Eqs. (1) and (2) of Schuller  
  > "we can use the standard approach of (cite: Hildebrand1983)" (3.1 1.3 mm continuum); "by applying Eqs. (1) and (2) from (cite: Schuller2009)" (3.1 1.3 mm continuum) [from (cite: Hildebrand1983); (cite: Schuller2009)]
- Outflow kinematic profile method (PV cuts perpendicular to outflow axis)  
  > "following the methods that have proven to be effective for low-mass protostars (for example, (cite: Zhang2018))" (4.2 Kinematic profiles of the molecular outflow) [from (cite: Zhang2018)]
- Launching radius from specific angular momentum, jet velocity and central mass  
  > "we adopted the approach presented in (cite: Lee2017)" (4.3 Disk-wind evidence) [from (cite: Lee2017)]
- Magnetic lever arm from Eq. (10) of Ferreira et al.  
  > "we used Eq. (10) from (cite: Ferreira2006)" (4.3 Disk-wind evidence) [from (cite: Ferreira2006)]
- PV-diagram Keplerian fit with the KeplerFit script  
  > "using the KeplerFit script from (cite: Bosco2019)" (4.3 Disk-wind evidence) [from (cite: Bosco2019)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used; self-calibration if any
- tclean cell size, image size, deconvolver, threshold, niter, masks and primary-beam correction
- continuum-subtraction method and line-free channels used to make the 1.3 mm continuum image and line cubes
- uv-taper parameters (e.g. taper in arcsec) used to reach the 0.15 arcsec beam
- rest frequencies and catalogue entries (JPL line list is only named) for the SO and SO2 transitions
- MADCUBA SLIM setup: initial parameters, line widths, source size / beam-dilution treatment, how the fit was run
- dust opacity law, gas-to-dust ratio and dust temperature handling used with the Schuller equations
- exact positions of the PV cut slices, cut widths and how emission peaks in PV diagrams were identified
- fitting code, optimiser, weights and parameter uncertainties for the linear and planar Keplerian fits
- KeplerFit inputs for the SO velocity spike; inputs and numerical values entering Lee (2017) and Ferreira (2006) formulas; units of R_A
- which channels and error handling went into the imfit peak maps

## Analysis recipe

1. **measure the 1.3 mm continuum sources**: Image the continuum with tclean and list position, size, PA and fluxes of detected sources  
  > "the parameters of the detected continuum sources are listed in Table" (3.1 1.3 mm continuum)
   - software: CASA tclean
   - parameter: natural weighting  
  > "The spectral line and continuum images were created using the CASA task *tclean* with natural weighting." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **estimate dust-traced gas mass and H2 column density**: Optically thin dust emission with Schuller et al. Eqs. (1) and (2)  
  > "by applying Eqs. (1) and (2) from (cite: Schuller2009) to estimate the total gas mass and column density of H$_2$" (3.1 1.3 mm continuum)
   - parameter: Distance 3.37 kpc  
  > "a linear resolution of $\sim$100 au at the distance of 3.37 kpc to the source" (2 Observations and data reduction)
   - assumption: Dust optically thin, in thermal equilibrium with gas at ~300 K  
  > "assuming that the dust is optically thin and in thermal equilibrium with the gas at average temperature of $\sim$300 K" (3.1 1.3 mm continuum)
   - fitting: _not stated_
   - validation: Compared with lower-resolution 1.3 mm results of Ilee et al. 2018; flagged as possible lower limits  
  > "These numbers are close to the ones obtained in the lower-resolution 1.3 mm continuum observations of (cite: Ilee2018)." (3.1 1.3 mm continuum)
3. **derive Tex and column densities from molecular spectra**: Extract spectra over a beam-sized area ~0.05 arcsec SW of the continuum peak and fit with SLIM under LTE  
  > "we selected an area of the size of the synthesised beam ($\sim$30 mas) shifted by $\sim$0.05$''$ to the SW of the continuum peak" (3.2 Molecular lines); "for each data cube we extracted spectra integrated over the selected area with the Spectral Profile plotting tool of the CASA image viewer" (3.2 Molecular lines)
   - software: CASA, MADCUBA (SLIM), CARTA
   - parameter: CH3CN v8=1 (14 lines) fitted together; CH3CN v=0 low-K (0-3) and high-K (4-9) fitted separately; CH3OH fitted with two weaker lines  
  > "We fitted all 14 lines of CH$_3$CN $\varv_8=1$ simultaneously, while low ($K$ = 0 to 3) and high-$K$ ($K$ = 4 to 9) CH$_3$CN $\varv=0$ transition were fitted separately" (3.2 Molecular lines)
   - assumption: Local thermodynamic equilibrium  
  > "under the assumption of local thermodynamic equilibrium" (Table 2 notes)
   - fitting: SLIM non-linear fit adjusting Tex and N; no sampler or priors stated  
  > "SLIM performs a non-linear fit to the observed spectra, accounting for line opacity, beam dilution, and line blending effects" (3.2 Molecular lines); "the fitting process directly adjusts T$_{ex}$ and N to reproduce the observed line intensities and their ratios" (Table 2 notes)
   - validation: Column densities consistent with CORE survey means (Gieser et al. 2021)  
  > "are consistent, within the uncertainties, with the mean column densities reported in the CORE survey of high-mass star-forming regions" (3.2 Molecular lines)
4. **estimate H2 column densities from molecular abundances**: Compare fitted CH3CN and CH3OH column densities with abundances from typical column densities in Gieser et al. 2021 Fig. 8  
  > "we compared our estimated column densities of CH$_3$CN and CH$_3$OH listed in Table [\[tab:l-param\]](#tab:l-param) with the abundances of these molecules" (3.2 Molecular lines)
   - fitting: _not stated_
   - validation: _not stated_
5. **make moment maps and PV diagrams**: CASA immoments for moment 0 and 1; GILDAS for PV diagrams along the disk plane (PA ~130 deg)  
  > "we computed Moment 0 and 1 maps using the CASA task *immoments*" (2 Observations and data reduction); "we produced position–velocity (PV) diagrams for the line data using the GILDAS[^3] software" (2 Observations and data reduction)
   - software: CASA immoments, GILDAS
   - parameter: 5 sigma rms threshold, velocity range includes target line only  
  > "The velocity range was chosen to include the target line only, and the threshold was set at a 5$\sigma$ rms level." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
6. **build peak maps of line emission per channel**: Fit a 2D Gaussian (imfit) to the emission peak in each channel for six lines; use tapered cubes (~0.15 arcsec beam) when emission is diffuse or weak  
  > "we fitted with a 2D Gaussian the emission peaks in each channel of the data cubes of six spectral lines" (3.4 Keplerian disk approximation); "Then we fitted the emission peaks in each channel with the task *imfit*" (2 Observations and data reduction)
   - software: CASA imfit
   - parameter: Line selection: compact, isolated, peak flux density above 5 sigma  
  > "(1) compactness (the emission should have a defined peak), (2) isolation in the spectrum (heavily blended lines were excluded from the analysis), (3) intensity (peak flux density above 5$\sigma$)" (3.4 Keplerian disk approximation)
   - parameter: Position uncertainties from ~0.8 mas to ~8 mas  
  > "which yielded position uncertainties from $\sim$0.8 mas ($\sim$3 au) for bright and compact emission and up to $\sim$8 mas ($\sim$30 au) for weak, extended emission" (2 Observations and data reduction)
   - fitting: 2D Gaussian per channel via imfit  
  > "we fitted with a 2D Gaussian the emission peaks in each channel of the data cubes" (3.4 Keplerian disk approximation)
   - validation: _not stated_
7. **fit Keplerian rotation to disk peak map**: Linear Keplerian fit to high-velocity peaks and planar Keplerian fit to all peaks (gives inclination)  
  > "(1) a linear Keplerian model that takes into account only high velocity blue- and redshifted peaks" (3.4 Keplerian disk approximation); "(2) a planar Keplerian model (cite: Sanchez2013) that fits all peaks and provides, in particular, an estimate of the inclination angle of the disk" (3.4 Keplerian disk approximation)
   - parameter: Linear fit free parameters: X0, V_star, M; PA fixed to 130 deg  
  > "The offset position of the central source along the X-axis ($X_0$), the systemic velocity (V$_{\rm star}$), and central source mass (M) were the free parameters of the linear Keplerian fit" (3.4 Keplerian disk approximation)
   - parameter: Planar fit free parameters: X0, Y0, V_star, PA, inclination, M  
  > "The free parameters of the planar Keplerian fit were: the position of the central source on the plane of the sky ($X_0$, $Y_0$), the central velocity (V$_{\rm star}$)" (3.4 Keplerian disk approximation)
   - assumption: Peak map represents a rotating disk  
  > "Assuming that the obtained peak map represents a rotating disk, we can determine the mass of the central object and the geometry of the disk." (3.4 Keplerian disk approximation)
   - fitting: _not stated_
   - validation: Planar mass ~20 Msun agrees with linear-fit mass corrected for the best-fit inclination ~30 deg; fit with CH3CN only is inconsistent  
  > "which is in good agreement with the result of the linear Keplerian fit corrected for a best-fit disk inclination of $\sim$30$^{\circ}$" (3.4 Keplerian disk approximation)
8. **measure outflow kinematic profiles from SO and SO2**: PV diagrams of cuts perpendicular to the outflow axis; peaks of red and blue parts give R_red, R_blue, V_red, V_blue; derive R_out, R_med, V_med, V_rot and specific angular momentum j = R_out V_rot  
  > "For these two peaks, we measure the offsets from the central source position (R$_{\rm red}$ and R$_{\rm blue}$) and corresponding local standard of rest velocity (V$_{\rm red}$ and V$_{\rm blue}$)." (4.2 Kinematic profiles of the molecular outflow); "We also calculated the specific angular momentum j as R$_{\rm out}$V$_{\rm rot}$" (4.2 Kinematic profiles of the molecular outflow)
   - software: GILDAS
   - parameter: 0.15 arcsec synthesised beam data; cut step 0.15 arcsec (~500 au)  
  > "the step for the cuts was set to 0.15$''$ ($\sim$500 au)" (4.2 Kinematic profiles of the molecular outflow)
   - parameter: Errors from spatial (0.15 arcsec, 500 au) and spectral (0.35 km/s) resolution  
  > "Our errors on the offset and velocity were determined by the spatial (0.15$''$ or 500 au) and spectral (0.35 km s$^{-1}$) resolution, respectively." (4.2 Kinematic profiles of the molecular outflow)
   - assumption: SO2 and SO trace the walls of rotating outflow cavities in each lobe  
  > "Assuming that both SO$_2$ and SO emissions trace the walls of the rotating outflow cavities for each of the two outflow lobes" (4.2 Kinematic profiles of the molecular outflow)
   - fitting: Linear fit to R_out versus z for the launching radius R0; fits to V_rot trend  
  > "A linear fit to the R$_{\rm out}$ data provides us with an estimate of the outflow launching radius (R$_0$)" (4.2 Kinematic profiles of the molecular outflow)
   - validation: V_med of SO and SO2 compared with V_star from the Keplerian fits  
  > "which agrees well with the V$_{\rm star}$ estimated from the Keplerian fits" (4.2 Kinematic profiles of the molecular outflow)
9. **test Keplerian rotation at the SO velocity spike**: PV diagram slice at PA=130 deg through the SO velocity spike (~0.3 arcsec NE), fitted with KeplerFit  
  > "Fitting of the PV diagram for the SO emission at the velocity spike position using the KeplerFit script from (cite: Bosco2019) returned a central source mass of 15 $M_{\odot}$" (4.3 Disk-wind evidence)
   - software: KeplerFit
   - fitting: _not stated_
   - validation: Mass of 15 Msun consistent with the disk analysis  
  > "this is consistent with what obtained from the disk analysis (see Table [1](#tab:disk)), suggesting a common origin" (4.3 Disk-wind evidence)
10. **derive wind launching radius and magnetic lever arm**: Lee et al. 2017 approach with specific angular momentum, outflow velocity and central mass; lever arm from Eq. (10) of Ferreira et al. 2006  
  > "where the jet launching radius is constrained by the specific angular momentum of the jet (j), jet expansion velocity, and mass of the central object (M)" (4.3 Disk-wind evidence); "we used Eq. (10) from (cite: Ferreira2006)" (4.3 Disk-wind evidence)
   - parameter: Mass 15 Msun (not inclination-corrected); j ~4500 (NE) and ~1600 (SW) au km/s  
  > "as well as the mass of the protostar 15 $M_{\odot}$ (without correcting for the inclination as we did not consider it in the calculations of the angular momentum)" (4.3 Disk-wind evidence)
   - parameter: Outflow velocity ~30 km/s (also tested ~100 km/s)  
  > "we recalculated R$_0$ using the same parameters but an outflow velocity of $\sim$100 km s$^{-1}$" (4.3 Disk-wind evidence)
   - assumption: Outflow velocity ~30 km/s assumed from water maser proper motions  
  > "We can assume a reasonable value of $\sim$30 km s$^{-1}$ based on the 22 GHz water maser proper motions estimated in (cite: Moscadelli2019)." (4.3 Disk-wind evidence)
   - fitting: _not stated_
   - validation: Lever arm in typical 2-10 range for massive disk-winds; X-wind needs much smaller radii  
  > "Such $\lambda$ are in good agreement with the typical values (between 2-10) expected for disk-winds in massive protostars." (4.3 Disk-wind evidence)

## Software

- **CASA** : Imaging (tclean), moment maps (immoments), peak fitting (imfit), spectral extraction  
  > "Imaging and data cubes analysis were performed with the Common Astronomy Software Applications (CASA[^2]; (cite: CASA2022)) package." (2 Observations and data reduction)
- **CARTA** : Spectral line identification  
  > "Spectral line identification was performed in the Cube Analysis and Rendering Tool for Astronomy (CARTA[^1]; (cite: Comrie2020))" (2 Observations and data reduction)
- **MADCUBA (SLIM)** : Line identification and LTE modelling of molecular spectra (Tex, column density)  
  > "The molecular line data modelling and estimation of the physical parameters were carried out using the SLIM tool of MADCUBA." (2 Observations and data reduction)
- **GILDAS** : Position-velocity diagrams  
  > "we produced position–velocity (PV) diagrams for the line data using the GILDAS[^3] software" (2 Observations and data reduction)
- **KeplerFit** : Keplerian fit to the SO PV diagram at the velocity spike  
  > "using the KeplerFit script from (cite: Bosco2019)" (4.3 Disk-wind evidence)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MM1a 1.3 mm integrated flux density | 57.8 | 1.4 | mJy | 1 | 57.8$\pm$1.4 |
| MM1a 1.3 mm peak flux density | 10.3 | 0.2 | mJy/beam | 1 | 10.3$\pm$0.2 |
| MM1b 1.3 mm integrated flux density (tentative, ~5 sigma) | 1.0 | 0.2 | mJy | 1 | 1.0$\pm$0.2; The flux density of MM1b is $\sim$1 mJy, corresponding to $\sim$5$\sigma$ level, and thus the detection is marginal. |
| MM1a continuum size and PA | ~0.16 arcsec (~500 au), PA ~130 deg | not stated | arcsec; deg | 1 | NW-SE elongated region of $\sim$0.16$''$ ($\sim$500 au) with PA $\sim$130$^{\circ}$ |
| Gas mass from 1.3 mm dust continuum | ~2.5 | not stated | Msun | 2 | we derive $M$ $\sim$2.5 $M_{\odot}$ and $N_{\rm H_2}$ = $\sim$1$\times$10$^{23}$ cm$^{-2}$ |
| H2 column density from dust continuum | ~1e23 | not stated | cm^-2 | 2 | we derive $M$ $\sim$2.5 $M_{\odot}$ and $N_{\rm H_2}$ = $\sim$1$\times$10$^{23}$ cm$^{-2}$ |
| Tex, CH3CN v8=1 J=12-11 | 333 | 21 | K | 3 | 333$\pm$21 |
| Tex, CH3CN v=0 K=4 to 9 | 327 | 19 | K | 3 | 327$\pm$19 |
| Tex, CH3OH 8(0,8)-7(1,6) E | 285 | 15 | K | 3 | 285$\pm$15 |
| Tex, CH3CN v=0 K=0 to 3 | 248 | 10 | K | 3 | 248$\pm$10 |
| Column density, CH3CN v8=1 | 5e15 | 0.2e15 | cm^-2 | 3 | 5$\pm$0.2 |
| Column density, CH3OH | 500e15 | 80e15 | cm^-2 | 3 | 500$\pm$80 |
| H2 column density implied by CH3CN and by CH3OH | ~1e24 (CH3CN), ~1e26 (CH3OH) | not stated | cm^-2 | 4 | The obtained values of $\sim$10$^{24}$ cm$^{-2}$ from CH$_3$CN and $\sim$10$^{26}$ cm$^{-2}$ from CH$_3$OH |
| Central mass, linear Keplerian fit (not inclination-corrected) | ~15 | not stated | Msun | 7 | The fitted mass of the central source is $\sim$15 $M_{\odot}$ without consideration of the disk inclination angle. |
| Systemic velocity V_star | 34.5 | not stated | km/s | 7 | V$_{\rm star}$=34.5 km s$^{-1}$ |
| Central mass, planar Keplerian fit | ~20 | not stated | Msun | 7 | From the Keplerian planar fit, we obtained the best-fit mass of the central source of $\sim$20 $M_{\odot}$ |
| Disk inclination (planar fit, with CH3OH) and mass/inclination without CH3OH | ~32 deg with CH3OH (20 Msun); ~55 deg and ~35 Msun without CH3OH | not stated | deg; Msun | 7 | The Keplerian fit of our data provided a central mass of $\sim$20 $M_{\odot}$ and disk inclination $\sim$32$^{\circ}$ with CH$_3$OH and $\sim$35 $M_{\odot}$ and disk inclination $\sim$55$^{\circ}$ without it |
| Radius of Keplerian region (inner, high-velocity CH3CN) | <300 | not stated | au | 7 | high-velocity emissions trace the inner $<$300 au radii of the disk, which are dominated by Keplerian rotation |
| Maximum outflow radius R_out, NE and SW lobes | ~1400 (NE), ~930 (SW) | not stated | au | 8 | with the maximum R$_{\rm out}$ for the NE lobe being $\sim$1400 au, while the emission from the SW lobe has a maximum R$_{\rm out}$ of $\sim$930 au |
| Outflow launching radius R0 from linear fit to R_out | ~260 (NE), ~340 (SW) | not stated | au | 8 | which is $\sim$260 au for the NE lobe, and $\sim$340 au for the SW lobe |
| Median outflow velocity V_med | 34.4 | 0.5 | km/s | 8 | V$_{\rm med}$ = 34.4$\pm$0.5 km s$^{-1}$ |
| Mean specific angular momentum, NE lobe (main text) | ~4500 | 690 | au km/s | 8 | in the NE lobe, the mean of the specific angular momentum is $\sim$4500$\pm$690 au km s$^{-1}$ |
| Mean specific angular momentum, SW lobe (main text) | ~1600 | 200 | au km/s | 8 | For the SW lobe, the mean specific angular momentum is $\sim$1600$\pm$200 au km s$^{-1}$. |
| Specific angular momentum quoted in Conclusions (NE, SW) | ~4720 (NE), ~1420 (SW) | not stated | au km/s | 8 | $\sim$4720 au km s$^{-1}$ for the NE lobe and $\sim$1420 au km s$^{-1}$ for the SW lobe |
| Decrease in V_rot along outflow | ~1.5 | not stated | km/s over ~1500 au | 8 | A decrease in the rotation velocity of $\sim$1.5 km s$^{-1}$ over $\sim$1500 au is found in both lobes of the outflow. |
| Central mass from KeplerFit of SO PV at velocity spike | 15 | not stated | Msun | 9 | returned a central source mass of 15 $M_{\odot}$ |
| Wind launching radius at outflow velocity ~30 km/s | ~50 (SW), ~100 (NE) | not stated | au | 10 | Using these estimates, we get R$_0$ $\sim$50 au for the SW lobe and $\sim$100 au for the NE lobe. |
| Wind launching radius at outflow velocity ~100 km/s | ~10 (SW), ~20 (NE) | not stated | au | 10 | We get $\sim$10 au for the SW lobe and $\sim$20 au for the NE lobe. |
| Magnetic lever arm lambda | ~2.4 (SW), ~4 (NE) | not stated | dimensionless | 10 | we obtain $\lambda$ of $\sim$2.4 and $\sim$4, and R$_A$ of $\sim$80 and $\sim$200 for the SW and NE lobe, respectively |
| Extent of SO and SO2 outflow emission | ~3400 | not stated | au | 0 | A strong collimated SO$_2$ and SO outflow from MM1a is probed up to $\sim$3400 au from MM1a. |

## Qualitative findings

- The disk is resolved into an inner Keplerian region and an outer sub-Keplerian region traced by mid-velocity CH3CN  
  > "the inner region ($<$300 au) is traced by high-velocity emission of high-excitation CH$_3$CN lines and shows a Keplerian rotation" (abstract)
- MM1b is a distinct source, not a disk fragment  
  > "The source MM1b appears to be a distinct source rather than a disk fragment as no molecular emission associated with MM1b and no connection between MM1a and MM1b are detected." (Conclusions)
- SO and SO2 outflow rotates with roughly constant specific angular momentum, consistent with an MHD disk-wind  
  > "The observed conservation of specific angular momentum indicates the presence of differential rotation along the outflow." (4.2 Kinematic profiles of the molecular outflow)
- Water masers trace the launching base of the outflow but not the disk-wind streamlines  
  > "the 22 GHz water masers trace the launching base of the outflow but, unfortunately, not the streamlines of a disk-wind" (4.3 Disk-wind evidence)

## Claim tuples

- H: Does the MM1 disk have a central mass as large as earlier estimates (~40 Msun)? | E: Peak maps of six CH3CN and CH3OH lines fitted with linear and planar Keplerian models | R: Central mass ~20 Msun (planar) and ~15 Msun (linear, uncorrected), inclination ~32 deg | F: Central mass is about half of previous lower-resolution estimates and consistent with ~1e4 Lsun luminosity | **supported**
- H: Does the disk show one kinematic regime across all radii? | E: Keplerian fits to high-velocity and mid-velocity peaks of CH3CN, plus PV diagrams | R: High-velocity emission at <300 au follows Keplerian rotation; mid-velocity emission at >300 au is sub-Keplerian | F: Two distinct velocity fields exist in the disk | **supported**
- H: Is MM1b a fragment of the MM1a disk? | E: 1.3 mm continuum imaging and molecular line maps at the MM1b position | R: MM1b is a ~1 mJy (~5 sigma) marginal detection with no molecular emission and no connection to MM1a | F: MM1b appears to be a distinct source rather than a disk fragment | **partially**
- H: Does the SO/SO2 outflow rotate and conserve specific angular momentum along the lobes? | E: PV diagrams perpendicular to the outflow axis at 0.15 arcsec steps in each lobe | R: V_rot decreases by ~1.5 km/s over ~1500 au while mean j is ~4500 au km/s (NE) and ~1600 au km/s (SW) | F: The outflow rotates about its axis with approximately constant specific angular momentum | **supported**
- H: Is the wind launched by an X-wind or a disk-wind mechanism? | E: Launching radius from specific angular momentum, central mass and assumed outflow velocity (Lee et al. 2017 approach), plus lever arm | R: R0 ~50-100 au for ~30 km/s and ~10-20 au for ~100 km/s; lambda ~2.4-4 | F: Launching radii are consistent with a disk-wind and not with an X-wind | **supported**

## Reasoning

- Why this data: Higher-angular-resolution ALMA observations of the high-mass core to clarify its structure and properties  
  > "In this article we present the results of our higher-angular-resolution ALMA observations of the high-mass core G11.92-0.61 MM1." (Introduction)
- Why this method: SLIM chosen over rotational diagram because it handles opacity, beam dilution, blending and multiple excitation  
  > "we employed the SLIM task of the MADCUBA package and not the rotational diagram method, since the latter assumes optically thin emission and a single excitation temperature" (3.2 Molecular lines)
- Alternative: X-wind origin rejected: required launching radii are a fraction of an au, inconsistent with the estimates  
  > "These estimates are not consistent with the X-wind model, which requires much smaller radii, of a fraction of a au." (4.3 Disk-wind evidence)
- Alternative: Streamer (infall) interpretation of the X-shaped structure discarded because it aligns with the outflow and is seen in outflow tracers  
  > "However, we discard this possibility as the detected structure is clearly aligned with the large-scale outflow and is clearly seen in outflow tracers" (4.2 Kinematic profiles of the molecular outflow)
- Alternative: Planar Keplerian fit using only the inner-ellipse peaks (without extended CH3CN K=4 and CH3OH) rejected as inconsistent, giving ~56 deg inclination  
  > "we obtain an inconsistent fit with the linear distribution of high-velocity spots offset from the disk’s major axis and a large disk inclination of $\sim$56$^{\circ}$" (3.4 Keplerian disk approximation)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust-derived mass and column density may be lower limits since continuum emission could be resolved out  
  > "we note that our estimates may be lower limits because part of the continuum emission could have been resolved out" (3.1 1.3 mm continuum)
- Limitation (authors): Spectral fit at the continuum peak was complicated by multiple kinematic components, so an offset position was used  
  > "as the fit towards the continuum peak turned out to be complicated by the presence of multiple kinematic components at this position" (3.2 Molecular lines)
- Limitation (authors): MM1b detection is marginal  
  > "and thus the detection is marginal" (3.1 1.3 mm continuum)
- Limitation (authors): Outflow velocity is not measured in these data and the mass was not inclination-corrected in the launching-radius estimate  
  > "The only parameter that we have not evaluated directly with our data is the outflow velocity." (4.3 Disk-wind evidence)
- Caveat (inferred, ours): Central mass depends strongly on whether CH3OH is included (20 vs ~35 Msun), so the factor-of-two reduction is tracer dependent
- Caveat (inferred, ours): Launching radius rests on an assumed outflow velocity (30 vs 100 km/s) and an uncorrected 15 Msun mass, spanning 10-100 au
- Caveat (inferred, ours): No fit uncertainties or sampler are given for the Keplerian fits
- Caveat (inferred, ours): Specific angular momentum values differ between main text (4500, 1600) and Conclusions (4720, 1420)
- Caveat (inferred, ours): Emission lines are mostly single lines for SO and SO2, so excitation and opacity are unconstrained
- Caveat (inferred, ours): Spectra taken at one offset position are used to characterise the whole disk

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: calibration pipeline and CASA version, self-calibration
- Missing: cell size, image size, deconvolver and cleaning thresholds
- Missing: continuum-subtraction and line-free channel choices
- Missing: uv-taper values
- Missing: MADCUBA SLIM fit setup
- Missing: Keplerian fit code and uncertainty treatment
- Missing: PV cut geometry and peak identification for the outflow profiles
- Data volume (inferred): One 1.5 hr Band 6 execution with five 960-channel spectral windows at 28 mas resolution; likely tens to a few hundred GB of raw/calibrated data, cubes at ~mas pixels several GB each
- Score (inferred): 3/5, Single ALMA project code is given and the numeric results are listed, but imaging parameters, continuum subtraction, SLIM setup and Keplerian fit details are missing, and several steps rest on inherited methods.
- Rediscovery candidate: no, The paper does not state data availability, and the recipe leaves out imaging, line-free channels and fit settings, so an independent redo would require many unstated choices.

## Links

- Method: Moscadelli et al. 2019 (cite: Moscadelli2019) (Per-channel 2D Gaussian peak-map method; water maser proper motions)
- Method: Sanchez-Monge et al. 2013 (cite: Sanchez2013) (Planar Keplerian model)
- Method: Lee et al. 2017 (cite: Lee2017) (Launching radius from specific angular momentum)
- Method: Ferreira et al. 2006 (cite: Ferreira2006) (Magnetic lever arm Eq. (10))
- Method: Bosco et al. 2019 (cite: Bosco2019) (KeplerFit script)
- Method: Zhang et al. 2018 (cite: Zhang2018) (Outflow kinematic profile approach)
- Method: Schuller et al. 2009 (cite: Schuller2009) (Dust mass and column density equations)
- Method: Martin et al. 2019 (cite: Martin2019) (MADCUBA package)
- Companion: Ilee et al. 2016 (cite: Ilee2016) (Earlier SMA/VLA study of the MM1 disk and outflow)
- Companion: Ilee et al. 2018 (cite: Ilee2018) (Earlier lower-resolution ALMA study of MM1 giving ~40 Msun)
- Companion: Moscadelli et al. 2016; 2019 (cite: Moscadelli2016; Moscadelli2019) (POETS water maser studies of G11.92-0.61)
- Companion: Cyganowski et al. 2011 (cite: Cyganowski2011) (Earlier (sub-)millimetre observations and outflow of the region)
- Related: POETS (Protostellar Outflows at the EarliesT Stages)
- Related: CORE survey (Gieser et al. 2021)

## Checks

```json
{
 "quotes": 146,
 "quotes_ok": 146,
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
  "facts": 117,
  "stated": 84,
  "rate": 0.718
 },
 "evidence_ok": true
}
```
