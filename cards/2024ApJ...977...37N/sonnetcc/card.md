# Turbulent Pressure Heats Gas and Suppresses Star Formation in Galactic Bar Molecular Clouds

`2024ApJ...977...37N` | The Astrophysical Journal 2024 | first author: Nilipour, Andy | arXiv: 2410.09258 | DOI: 10.3847/1538-4357/ad8631

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation, astrochemistry
- Question: Are 20 warm, broad-line clouds with |l|<10 deg located in the Galactic bar, and how do temperature, turbulence, shocks, star formation and mass behave in them (including the CO-to-H2 X-factor)?  
  > "We measure gas temperatures, shocks, star formation rates, turbulent Mach numbers, and masses for these clouds." (abstract); "and to investigate where these clouds are located." (Introduction)
- Target **Nine clouds assumed to lie in the Galactic bar (G006.56, G005.75, G005.49, G005.38, G003.09, G003.02, G002.96, G002.51, G001.93)**: coordinates (l, b) per cloud in the cloud-locations table, e.g. G006.56 (6.56, -0.30), G003.09 (3.09, 0.16), G001.93 (1.93, 0.11)  
  > "We use a Galactic Center distance of $8178 \pm 26$ pc (cite: abuter_geometric_2019)" (3 Cloud Locations); "and an angle between the Galactic bar and the line of sight of $30^\circ \pm 2^\circ$ (cite: wegg_structure_2015) to calculate the distance and Galactocentric radius of each cloud." (3 Cloud Locations); z/distance Geometric distances 6.9-7.7 kpc (each +/- 1.0 kpc), e.g. G006.56 6.9 kpc, G003.09 7.5 kpc, G001.93 7.7 kpc  
  > "We use a Galactic Center distance of $8178 \pm 26$ pc (cite: abuter_geometric_2019)" (3 Cloud Locations); "and an angle between the Galactic bar and the line of sight of $30^\circ \pm 2^\circ$ (cite: wegg_structure_2015) to calculate the distance and Galactocentric radius of each cloud." (3 Cloud Locations); distance from Geometry of the bar: Galactic Center distance 8178 +/- 26 pc (abuter_geometric_2019), bar angle 30 +/- 2 deg (wegg_structure_2015), clouds assumed on the bar major axis, 1 kpc line-of-sight uncertainty  
  > "We use a Galactic Center distance of $8178 \pm 26$ pc (cite: abuter_geometric_2019)" (3 Cloud Locations); "and an angle between the Galactic bar and the line of sight of $30^\circ \pm 2^\circ$ (cite: wegg_structure_2015) to calculate the distance and Galactocentric radius of each cloud." (3 Cloud Locations)
- Target **Eleven clouds not in the bar (G008.67, G008.40, G006.92, G003.43, G358.48, G354.61, G353.41, G351.77, G351.58, G350.18, G350.10)**: coordinates (l, b) per cloud in the cloud-locations table, e.g. G008.67 (8.67, -0.37), G350.10 (350.10, 0.09)  
  > "We adopt previous distance measurements using Galactic kinematics or associations with nearby cloud complexes for the clouds not in the bar" (3 Cloud Locations); z/distance Distances 2.0-12.3 kpc, e.g. G008.67 3.4 +/- 0.3 kpc, G351.77 2.0 +/- 0.1 kpc, G354.61 12.3 +/- 2.2 kpc, G350.10 6.2 +/- 0.8 kpc  
  > "We adopt previous distance measurements using Galactic kinematics or associations with nearby cloud complexes for the clouds not in the bar" (3 Cloud Locations); distance from Literature kinematic or astrometric distances (ALMA-IMF, Gaia DR3 via reyes-reyes_benchmarking_2024, jones_h_2013, green_distances_2011, nandakumar_star-forming_2016); G003.43 and G358.48 adopt 2.5 kpc by the authors' estimate  
  > "We adopt previous distance measurements using Galactic kinematics or associations with nearby cloud complexes for the clouds not in the bar" (3 Cloud Locations)

## Data provenance

- ALMA projects: 2019.2.00068.S, 2021.2.00001.S, 2022.1.00591.S
- bands: _not stated_
- frequencies and spectral setup: Nine spectral windows between 215 and 230 GHz (rest frequencies 217.1050-231.9009 GHz), 0.25 GHz bandwidth each (2 GHz for H30alpha), 512-2048 channels  
  > "observations of various molecular lines between 215 and 230 GHz" (abstract); "The spectral windows used cover lines of several important molecules" (2.2 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA-ACA, 7 m array and Total Power (TP) antennas; only TP data analysed  
  > "using both the 7 m array and the TP antennas. We analyze the TP data in this work." (2.2 ALMA Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Native FWHM beams approximately 28-30 arcsec; smoothed to 31 arcsec  
  > "The native full width at half-maximum (FWHM) beam sizes of the observations are between approximately 28$''$ and 30$''$." (2.2 ALMA Observations and Data Reduction); "We smooth the cubes to all have the same beam size of 31$''$." (2.2 ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma rms 0.22 to 0.28 Jy/beam per 0.332 km/s channel (5.2 to 7.7 mK)  
  > "varies from about 0.22 to 0.28 Jy beam$^{-1}$" (2.2 ALMA Observations and Data Reduction); "the rms noise ranges from about 5.2 to 7.7 mK" (2.2 ALMA Observations and Data Reduction)
- time on source: _not stated_
- observing dates: 2021 May to 2023 May  
  > "The clouds were observed with the ALMA-ACA between 2021 May and 2023 May" (2.2 ALMA Observations and Data Reduction)
- pi or archival as stated: PI: Ott, J. (project codes listed; not described as archival)  
  > "2022.1.00591.S; PI: Ott, J.)" (2.2 ALMA Observations and Data Reduction)
- Line: SiO J=5-4 (217.1050 GHz)
- Line: H2CO J=3(21)-2(20) (218.7601 GHz)
- Line: H2CO J=3(03)-2(02) (218.2222 GHz)
- Line: HC3N J=24-23 (218.3247 GHz)
- Line: CH3OH J=4(22)-3(12) (218.4401 GHz)
- Line: C18O J=2-1 (219.5604 GHz)
- Line: 13CO J=2-1 (220.3987 GHz)
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: H30alpha radio recombination line (231.9009 GHz)
- Other facility **Mopra HOPS (H2O Southern Galactic Plane Survey)**: NH3 (1,1), (2,2), (3,3), (6,6) maps used for sample selection and ammonia temperatures  
  > "HOPS used the 22 m Mopra radio telescope, which has a main-beam FWHM of 2" (2.3.1 HOPS); "We selected 20 clouds from HOPS that may be in the Milky Way Galactic bar region." (2.1 Sample Selection)
- Other facility **Spitzer GLIMPSE (IRAC 4.5 and 8 micron)**: 10 arcmin cutouts from IRSA used to locate star formation  
  > "We use the cutout service of the Infrared Science Archive (IRSA) to take 10$'$ wide images containing the central location of each cloud in the 4.5 and 8 $\mu$m bands of the Infrared Array Camera (cite: fazio_infrared_2004) from GLIMPSE." (2.3.2 Spitzer)
- Other facility **Spitzer MIPSGAL (MIPS 24 micron)**: 30 arcmin 24 micron images regridded to GLIMPSE pixels, used for 24 micron SFR  
  > "We also take 30$'$ wide images of the same locations in the 24 $\mu$m band of MIPS" (2.3.2 Spitzer)
- External data: H2CO line-ratio to gas-temperature polynomial (RADEX-derived, n(H2)=1e4 cm^-3)  
  > "(cite: ginsburg_dense_2016) derived from the radiative transfer code RADEX (cite: van_der_tak_computer_2007)" (4.1.2 Formaldehyde Temperature); "This fit uses an assumed gas density of $n(\text{H}_2) = 10^4 \text{ cm}^{-3}$." (4.1.2 Formaldehyde Temperature) [from (cite: ginsburg_dense_2016); RADEX (cite: van_der_tak_computer_2007)]
- External data: Galactic electron-temperature gradient used for H II region electron temperatures  
  > "we use the Galactic disk electron temperature gradient from (cite: quireza_electron_2006)" (4.3 Star Formation) [from (cite: quireza_electron_2006)]
- External data: Electron density versus diameter relation log n_e = 2.8 - log D  
  > "We estimate the electron density using the fits of $n_e$ against diameter of Galactic HII regions by (cite: hunt_size-density_2009)." (4.3 Star Formation) [from (cite: hunt_size-density_2009)]
- External data: Tables of case B recombination coefficient and emissivity  
  > "we interpolate the tables of $\alpha_B$ and $\epsilon_\nu$ values published by (cite: storey_recombination_1995)" (4.3 Star Formation) [from (cite: storey_recombination_1995)]
- External data: 24 micron SFR calibration  
  > "We can also estimate the SFR in the clouds from 24 $\mu$m emission using the relationship from (cite: calzetti_calibration_2007)" (4.3 Star Formation) [from (cite: calzetti_calibration_2007)]
- External data: Q to SFR conversion 7.29e-54 Msun/yr per s^-1 (STARBURST99)  
  > "using a conversion from $Q$ to SFR of $7.29 \times 10^{-54} \text{ M}_\odot \text{yr}^{-1}/\text{s}^{-1}$ (cite: murphy_calibrating_2011)" (4.3 Star Formation) [from (cite: murphy_calibrating_2011); STARBURST99 (cite: leitherer_starburst99_1999)]
- External data: 12C/13C and 16O/18O isotope ratio gradients with Galactocentric radius  
  > "from (cite: wilson_abundances_1994)" (4.4.1 SiO) [from (cite: wilson_abundances_1994); (cite: langer_12c_1990)]
- External data: Standard CO-to-H2 X-factor 2.3e20 cm^-2 (K km/s)^-1  
  > "we multiply the integrated intensity by the CO-to-H~2~ X-factor of $2.3 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ derived by (cite: strong_radial_1988)" (4.5 Mass) [from (cite: strong_radial_1988)]
- External data: 12CO J=2-1/J=1-0 line ratio of 0.8  
  > "We also multiply by the factor 0.8, the typical ^12^CO $J=2 \to 1/J=1\to 0$ line ratio (cite: leroy_heracles_2009)." (4.5 Mass) [from (cite: leroy_heracles_2009)]
- External data: 12CO-to-H2 abundance ratio of 1e-4  
  > "where we have assumed a typical ^12^CO-to-H~2~ abundance ratio of $10^{-4}$ for dense clouds" (4.4.1 SiO) [from (cite: lacy_detection_1994; burgh_direct_2007)]
- External data: Turbulent heating temperature formula  
  > "and $V_\text{FWHM}$ is the observed FWHM line width (cite: ao_thermal_2013)" (5.3 What is Heating the Clouds?) [from (cite: ao_thermal_2013)]
- External data: Adopted ALMA-IMF kinematic distance for G008.67 (3.4 +/- 0.3 kpc) and G353.41 (2.0 +/- 0.7 kpc)  
  > "We adopt the ALMA-IMF kinematic distance of 3.4 $\pm$ 0.3 kpc." (3.1 Clouds Not in the Galactic Bar) [from ALMA-IMF (cite: motte_alma-imf_2022)]

## Processing

### Calibration

- pipeline or manual: Default ALMA Pipeline Reduction  
  > "We used the default ALMA Pipeline Reduction" (2.2 ALMA Observations and Data Reduction)
- casa version: CASA 6.2.1.7-6.4.1.12  
  > "(CASA) versions 6.2.1.7-6.4.1.12 (cite: the_casa_team_casa_2022)" (2.2 ALMA Observations and Data Reduction)
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
- cell size: 2.935 arcsec (13CO J=2-1 pixel size)  
  > "we also regrid the cubes to match the ^13^CO $J=2\to 1$ pixel size of 2.935$''$ and velocity resolution of 0.332 km s$^{-1}$" (2.2 ALMA Observations and Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted only if found in line-free channels  
  > "If found, the continuum was subtracted." (2.2 ALMA Observations and Data Reduction)
- line free channels: Selected visually per cloud (ranges not given)  
  > "We visually inspected and selected the velocity and channel ranges without any spectral features for the presence of continuum emission." (2.2 ALMA Observations and Data Reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All cubes smoothed to a common 31 arcsec beam  
  > "We smooth the cubes to all have the same beam size of 31$''$." (2.2 ALMA Observations and Data Reduction)
- final beam: 31 arcsec  
  > "We smooth the cubes to all have the same beam size of 31$''$." (2.2 ALMA Observations and Data Reduction)
- final rms: 0.22-0.28 Jy/beam (5.2-7.7 mK) in 0.332 km/s channels  
  > "varies from about 0.22 to 0.28 Jy beam$^{-1}$" (2.2 ALMA Observations and Data Reduction); "the rms noise ranges from about 5.2 to 7.7 mK" (2.2 ALMA Observations and Data Reduction)

### Inherited from earlier work

- Ammonia rotational temperature procedure  
  > "following the same procedure outlined in (cite: ott_temperature_2005)" (4.1.1 Ammonia Temperature) [from (cite: ott_temperature_2005)]
- HOPS ammonia catalog observation details  
  > "Further observation details about the HOPS ammonia catalog can be found in (cite: purcell_h2o_2012)." (2.3.1 HOPS) [from (cite: purcell_h2o_2012)]
- H2CO thermometer fit and assumed density of 1e4 cm^-3  
  > "(cite: ginsburg_dense_2016) derived from the radiative transfer code RADEX (cite: van_der_tak_computer_2007)" (4.1.2 Formaldehyde Temperature) [from (cite: ginsburg_dense_2016)]
- Distances for clouds not in the bar taken from earlier work  
  > "We adopt previous distance measurements using Galactic kinematics or associations with nearby cloud complexes for the clouds not in the bar" (3 Cloud Locations) [from ALMA-IMF (cite: motte_alma-imf_2022) and other kinematic distance papers]
- Optical depth check with constant 12C/13C = 40  
  > "we also perform the calculation assuming a constant R~C~ = 40 (cite: gramze_evidence_2023)" (5.5 X-Factor in the Bar) [from (cite: gramze_evidence_2023)]

### Not stated but needed to reproduce (our reading)

- Which ACA TP calibration products/scheduling blocks and pipeline versions per project were used, and whether the archive pipeline products or a re-run were used
- How the TP data were gridded and imaged by the pipeline (cell, convolution function, baseline fitting) before the authors' smoothing and regridding
- The line-free channel ranges and any continuum-subtraction fit order for each cloud
- Per-cloud 1 arcmin box centres and the exact box positions for H2CO, H30alpha and 24 micron integrations
- How HOPS NH3 moment maps and noise were produced (cube conversion, main-beam efficiency, baseline removal)
- Gaussian-fit initial guesses and software used for line widths and PV-diagram widths
- The PV extraction paths and widths for each cloud
- Which excitation temperature and partition function treatment were used for the quoted SiO, 13CO and C18O column densities
- The interpolation scheme, MIPSGAL mask interpolation method and integration details for 24 micron SFRs
- Whether ammonia ortho/para ratio assumptions, hyperfine handling or beam-filling corrections were applied to HOPS temperatures
- Software versions for pvextractor, spectral-cube, reproject and RADEX

## Analysis recipe

1. **Reduce, smooth and regrid ACA TP cubes**: Default ALMA pipeline; line-free ranges chosen by eye with continuum subtracted if found; cubes smoothed to a 31 arcsec beam and regridded to the 13CO pixel size and channel width  
  > "We used the default ALMA Pipeline Reduction" (2.2 ALMA Observations and Data Reduction); "We smooth the cubes to all have the same beam size of 31$''$." (2.2 ALMA Observations and Data Reduction)
   - software: CASA
   - parameter: pixel size 2.935 arcsec, channel width 0.332 km/s  
  > "we also regrid the cubes to match the ^13^CO $J=2\to 1$ pixel size of 2.935$''$ and velocity resolution of 0.332 km s$^{-1}$" (2.2 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment, ratio and PV maps**: Moment 0 integrated over the 13CO cloud velocity range with a 4 sigma_rms cutoff; moment 1, moment 2 and peak maps; line ratio maps vs 12CO and 13CO; PV diagrams  
  > "we set a cutoff at 4$\sigma_\text{rms}$, then integrate over the velocity range of the cloud in ^13^CO $J=2\to 1$" (2.3 ALMA Maps); "We also create position-velocity (PV) diagrams for each cube using the packages" (2.3 ALMA Maps)
   - software: spectral-cube, pvextractor
   - parameter: 4 sigma_rms pixel cutoff plus 5 sigma threshold on moment 0; sigma = sqrt(N) sigma_rms dv with N the full velocity-range channel count  
  > "we again use a 4$\sigma_\text{rms}$ pixel cutoff, as well as a 5$\sigma$ threshold on the moment 0 map" (2.3 ALMA Maps); "Here, $N$ is the number of channels integrated over for the moment 0 map, and $\Delta v = 0.332$ km s$^{-1}$ is the channel velocity width." (2.3 ALMA Maps)
   - parameter: PV velocity range = cloud range plus 20 km/s each side  
  > "with an extra 20 km s$^{-1}$ on each side" (2.3 ALMA Maps)
   - assumption: 13CO used for moment range because it is observed for all clouds and less contaminated than 12CO  
  > "which is observed for all clouds and is less contaminated with foreground and background emission than the more common isotopologue" (2.3 ALMA Maps)
   - fitting: _not stated_
   - validation: Ratio errors use a propagated-error approximation acknowledged as inexact  
  > "Although this equation does not hold under all circumstances, we use it as an approximation of the error for the integrated intensity ratios." (2.3 ALMA Maps)
3. **Derive ammonia rotational temperatures from HOPS**: Optically thin NH3 column densities from HOPS moment 0 maps give T12, T13, T36 maps; one value per cloud at brightest NH3 (3,3) pixel  
  > "so we assume that the ammonia emission is optically thin" (4.1.1 Ammonia Temperature); "we take the temperature and error at the brightest pixel in the NH~3~ (3,3) moment 0 map." (4.1.1 Ammonia Temperature)
   - parameter: HOPS moment 0 maps made with same velocity range as ALMA moment maps  
  > "We then make a moment 0 map of each region for all four ammonia lines using the same velocity range as used for the ALMA moment maps." (2.3.1 HOPS)
   - assumption: Optically thin NH3; para/ortho abundance ratio adds uncertainty  
  > "We note that the abundance ratio of para- and ortho-ammonia also introduces some additional uncertainty" (4.1.1 Ammonia Temperature)
   - fitting: _not stated_
   - validation: Rotation diagrams of the ammonia lines shown  
  > "We show rotation diagrams (or Boltzmann diagrams) of the ammonia lines" (4.1.1 Ammonia Temperature)
4. **Derive formaldehyde gas temperatures**: Ratio of H2CO 3(21)-2(20) to 3(03)-2(02) moment 0 maps with a 3 sigma cutoff, converted by the Ginsburg polynomial; value taken in a 1 arcmin box at the peak H2CO 3(03)-2(02) and also at the peak NH3 (3,3) pixel after regridding to HOPS resolution  
  > "Next, we calculate the gas temperature based on the line ratio of H~2~CO $(3_{21}-2_{20})$ to H~2~CO $(3_{03}-2_{02})$." (4.1.2 Formaldehyde Temperature); "We take the error on this temperature to be the mean of the temperature error map within the same box." (4.1.2 Formaldehyde Temperature)
   - software: RADEX
   - parameter: T_G = 590 R^2 + 2.88 R + 23.4 with n(H2) = 1e4 cm^-3  
  > "This fit uses an assumed gas density of $n(\text{H}_2) = 10^4 \text{ cm}^{-3}$." (4.1.2 Formaldehyde Temperature)
   - assumption: Constant H2 density of 1e4 cm^-3; weak density dependence for R <~ 0.3  
  > "although the gas temperature has only a weak density dependence for most of the line ratios we observe" (4.1.2 Formaldehyde Temperature)
   - fitting: _not stated_
   - validation: Errors likely underestimated where T > 80 K; no significant NH3 vs H2CO correlation found  
  > "These errors are likely underestimates for regions where the gas temperature is greater than about 80 K." (4.1.2 Formaldehyde Temperature); "but we find no significant correlation between the ammonia and formaldehyde temperature" (4.1.3 Ammonia versus Formaldehyde Temperature)
5. **Measure line widths, turbulence and Mach numbers**: Gaussian fit to the mean spectrum in the box at the peak H2CO 3(03)-2(02) pixel; subtract thermal and bulk (velocity-gradient) widths to get turbulent width; Mach number from v_rms/c_s  
  > "We calculate a line width for each ALMA line by fitting a Gaussian to the mean spectrum of the 1" (4.2 Turbulence); "We can estimate the contribution from ordered motion through the velocity gradients of the clouds" (4.2 Turbulence)
   - parameter: mean molecular weight mu = 2.34  
  > "$\mu = 2.34$ is the mean molecular weight of a molecular cloud (cite: syed_atomic_2020)" (4.2 Turbulence)
   - parameter: Velocity gradient from a plane fit to the H2CO 3(03)-2(02) moment 1 map; bulk contribution = gradient times beam size  
  > "We multiply this by the beam size in radians to estimate the contribution of bulk motion to the line width." (9 Velocity Gradient Fitting)
   - assumption: H2CO temperature taken as kinetic temperature; isotropic turbulence  
  > "Taking the calculated formaldehyde temperatures of each cloud to be representative of the kinetic temperature" (4.2 Turbulence); "assuming isotropic turbulence" (4.2 Turbulence)
   - fitting: Single Gaussian; double Gaussian for one cloud with two velocity components (wider taken)  
  > "One cloud exhibits two velocity components in its spectrum, so we fit a double Gaussian and take the wider of the two." (4.2 Turbulence)
   - validation: Errors from Gaussian fit propagated to Mach number  
  > "We take the errors in the total line widths to be the errors on the Gaussian fits, then propagate accordingly to get errors on the Mach numbers." (4.2 Turbulence)
6. **Estimate star formation rates and SFR surface densities**: Ionizing photon rate Q from H30alpha flux in a 1 arcmin box with electron temperature from the Galactic gradient and electron density from the size-density relation; 24 micron SFR from Calzetti relation in a 2 arcmin box; Q-to-SFR conversion of Murphy et al.; upper limits for nondetections  
  > "We can calculate the ionizing photon production rate, $Q$, from measurements of H30$\alpha$, via" (4.3 Star Formation); "We can also estimate the SFR in the clouds from 24 $\mu$m emission using the relationship from (cite: calzetti_calibration_2007)" (4.3 Star Formation)
   - software: reproject, STARBURST99
   - parameter: H30alpha cloud diameter = 4 times the sigma of a Gaussian fit to the PV diagram collapsed along velocity  
  > "We take the angular diameter of the cloud to be 4 times the standard deviation of the fitted Gaussian, then calculate a physical size using the distance to the cloud." (4.3 Star Formation)
   - parameter: Upper limit is 2 sigma, i.e. twice the Q computed from the noise  
  > "we take a 2$\sigma$ upper limit of twice this $Q$ value." (4.3 Star Formation)
   - assumption: Electron temperature from the Quireza gradient; electron density from Hunt et al. relation; Calzetti relation derived from extragalactic regions; 24 micron SFRs treated as lower limits because of masked pixels  
  > "This relation is derived from extragalactic star-forming regions, so it may not be fully applicable to the clouds in our sample" (4.3 Star Formation); "We thus treat the resultant SFR values as lower limits." (4.3 Star Formation)
   - fitting: Monte Carlo with normal distributions of T_e and n_e for errors on alpha_B and emissivity  
  > "We calculate errors on these values using a simple Monte Carlo simulation, assuming a normal distribution for $T_e$ and $n_e$." (4.3 Star Formation)
   - validation: Stromgren-sphere radius compared with measured H30alpha radius (internal consistency check)  
  > "this provides a check of internal consistency within the calculations." (4.3 Star Formation)
7. **Characterise shocks with SiO and CH3OH**: LTE column densities of SiO (and 13CO, C18O) assuming optically thin emission; SiO abundance relative to H2 from isotopologue CO columns; CH3OH/13CO line ratio as weak-shock tracer  
  > "We assume optically thin emission, LTE, a Rayleigh-Jeans approximation, and negligible background." (4.4.1 SiO); "We use the line ratio of CH~3~OH $J = 4_{22} \to 3_{12}$ to ^13^CO $J = 2\to 1$ to assess the weak shocks associated with methanol emission." (4.4.2 Methanol)
   - software: RADEX
   - parameter: SiO dipole moment 3.0982 Debye and rotational constant 21787.5 MHz; beam filling factor 1  
  > "the dipole moment is $\mu = 3.0982$ Debye (cite: raymonda_electric_1970) and the rotational constant is $B = 21787.5$ MHz (cite: lowry_manson_millimeter_1977)" (4.4.1 SiO); "We also assume the beam filling factor is 1, although it may be lower" (4.4.1 SiO)
   - assumption: 12CO/H2 = 1e-4; isotope ratios from Galactocentric radius  
  > "where we have assumed a typical ^12^CO-to-H~2~ abundance ratio of $10^{-4}$ for dense clouds" (4.4.1 SiO); "We use the ^12^C/^13^C and ^16^O/^18^O isotope abundance ratios, respectively, which increase with Galactocentric radius (cite: langer_12c_1990)." (4.4.1 SiO)
   - fitting: _not stated_
   - validation: RADEX shows LTE SiO column cannot explain the line, so SiO columns are lower limits  
  > "With RADEX, we find that the SiO column density derived from the LTE assumption is insufficient to explain the observed line intensity." (4.4.1 SiO)
8. **Estimate cloud masses**: H2 column maps from 13CO and C18O (optically thin LTE, isotope ratios, CO/H2 = 1e-4) and from 12CO with the standard X-factor and a 0.8 line ratio, integrated over the 5 sigma H2CO 3(03)-2(02) extent, times mu_H2 = 2.8  
  > "we calculate the column density maps of ^13^CO and C^18^O, assuming they are optically thin, then use ^12^C/^13^C and ^16^O/^18^O isotope abundance ratios" (4.5 Mass); "then multiply by the molecular weight per hydrogen molecule, $\mu_{\text{H}_2} = 2.8$" (4.5 Mass)
   - parameter: X-factor 2.3e20 cm^-2 (K km/s)^-1 for 12CO  
  > "we multiply the integrated intensity by the CO-to-H~2~ X-factor of $2.3 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ derived by (cite: strong_radial_1988)" (4.5 Mass)
   - assumption: Cloud extent set by H2CO 3(03)-2(02) because the cloud extent is unclear on CO maps; kinetic temperature for two clouds without H2CO 3(21)-2(20) taken from NH3 (3,3)-(1,1)  
  > "because the extent of the cloud is less clear on the CO maps, even for the less abundant isotopologues." (4.5 Mass); "we estimate the kinetic temperature to be the ammonia (3,3) - (1,1) temperature" (4.5 Mass)
   - fitting: _not stated_
   - validation: 13CO and C18O masses agree within a factor of about 2-3  
  > "agree to within a factor of about 2-3" (5.5 X-Factor in the Bar)
9. **Test whether turbulence can heat the clouds**: Compare observed H2CO temperatures with analytic turbulent-heating temperature using cloud size from a 2D circular Gaussian fit to H2CO 3(21)-2(20), measured velocity gradient and assumed density  
  > "which is a simplified analytic solution to the turbulence-dominated thermal equilibrium equation, assuming gas densities $n \leq 10^{5} \text{ cm}^{-3}$" (5.3 What is Heating the Clouds?); "we fit a circular two-dimensional Gaussian around the peak H~2~CO $(3_{21}-2_{20})$ emission to calculate the cloud angular diameter" (5.3 What is Heating the Clouds?)
   - parameter: assumed gas density 1e4 cm^-3  
  > "assume a gas density of $10^4 \text{ cm}^{-3}$" (5.3 What is Heating the Clouds?)
   - assumption: X-ray and cosmic-ray heating disfavored for bar and disk clouds  
  > "X-ray heating and cosmic ray heating can thus be disfavored as heating mechanisms in these clouds." (5.3 What is Heating the Clouds?)
   - fitting: _not stated_
   - validation: Turbulent heating is sufficient for clouds without detected star formation and generally insufficient for those with Spitzer detections  
  > "turbulent heating is generally sufficient to explain the observed temperatures of the clouds" (5.3 What is Heating the Clouds?)
10. **Test H2 density with RADEX**: RADEX H2CO line ratio at the NH3 T13 temperature, observed line width and derived H2CO column densities over n(H2)=10^2.5-10^7 cm^-3, interpolated to find the density matching the observed ratio  
  > "We use RADEX to calculate the $R_{\rm{H}_2 \rm{CO}}$ line ratio at the cloud" (5.1 Ammonia and Formaldehyde Thermometers)
   - software: RADEX
   - parameter: N(H2CO)/N(H2) = 1.2e-9  
  > "abundance ratio of $1.2 \times 10^{-9}$" (5.1 Ammonia and Formaldehyde Thermometers)
   - assumption: Single gas phase; NH3 T13 used as kinetic temperature  
  > "The uncertainty is compounded by the assumption of gas in a single phase in our calculations" (5.3 What is Heating the Clouds?)
   - fitting: Interpolation over RADEX grid (no sampler)  
  > "We then interpolate and attempt to calculate the H~2~ volume density given the observed line ratio for both column densities." (5.1 Ammonia and Formaldehyde Thermometers)
   - validation: Only four clouds have a matching density, and those are the four where H2CO and NH3 temperatures agree within uncertainties  
  > "We find that, for all but four of the clouds, there is no H~2~ density for which the expected line ratio from RADEX matches the observed line ratio." (5.1 Ammonia and Formaldehyde Thermometers)
11. **Classify cloud locations and derive the bar X-factor**: Clouds with NH3 (1,1) width above 10 km/s assumed on the bar major axis; two (G350.18, G350.10) reclassified; X-factor per bar cloud from the 13CO LTE mass; 12CO optical depth from the 12CO/13CO ratio by root finding  
  > "Although the locations are uncertain, we take the clouds with a NH~3~ (1,1) line width greater than 10 km s$^{-1}$ to lie along the Galactic bar." (3 Cloud Locations); "If we take the LTE mass estimate with ^13^CO to be more representative of the true cloud mass, then we can calculate an X-factor for each cloud in the bar" (5.5 X-Factor in the Bar); "We estimate the optical depth for each of the clouds using a root finding algorithm on the equation" (5.5 X-Factor in the Bar)
   - parameter: Optical depth uses the 1 arcmin box at peak 12CO and R_C from the Galactocentric-radius relation, also R_C = 40  
  > "we also perform the calculation assuming a constant R~C~ = 40 (cite: gramze_evidence_2023)" (5.5 X-Factor in the Bar)
   - assumption: 13CO LTE mass taken as closer to the true mass; uncertainty on the mean X-factor is the sample standard deviation  
  > "where the uncertainty is taken to simply be the standard deviation over the sample" (5.5 X-Factor in the Bar)
   - fitting: Root-finding for tau_12 (no sampler or priors)  
  > "using a root finding algorithm" (5.5 X-Factor in the Bar)
   - validation: Result compared with the Gramze et al. X-factor for G5; tau_12 re-derived with constant 12C/13C = 40  
  > "This value is consistent with that calculated by (cite: gramze_evidence_2023)" (5.5 X-Factor in the Bar)

## Software

- **CASA** 6.2.1.7-6.4.1.12: Default ALMA pipeline reduction  
  > "(CASA) versions 6.2.1.7-6.4.1.12 (cite: the_casa_team_casa_2022)" (2.2 ALMA Observations and Data Reduction)
- **spectral-cube** : Position-velocity diagram creation (with pvextractor)  
  > "We also create position-velocity (PV) diagrams for each cube using the packages" (2.3 ALMA Maps)
- **pvextractor** : Position-velocity diagram creation  
  > "We also create position-velocity (PV) diagrams for each cube using the packages" (2.3 ALMA Maps)
- **reproject** : Regridding MIPS 24 micron images to GLIMPSE pixel spacing  
  > "then regrid to match the pixel spacing of the GLIMPSE data using the" (2.3.2 Spitzer)
- **RADEX** : H2CO and SiO radiative-transfer modelling, H2 density test  
  > "We use RADEX to calculate the $R_{\rm{H}_2 \rm{CO}}$ line ratio at the cloud" (5.1 Ammonia and Formaldehyde Thermometers); "With RADEX, we find that the SiO column density derived from the LTE assumption is insufficient to explain the observed line intensity." (4.4.1 SiO)
- **STARBURST99** : Basis of the Q-to-SFR conversion taken from Murphy et al.  
  > "which is calculated using `STARBURST99` (cite: leitherer_starburst99_1999)" (4.3 Star Formation)
- **CARTA** : Listed in the Software section; specific use not stated  
  > "CARTA (cite: comrie_carta_2021)" (Software)
- **Astropy** : Listed in the Software section; specific use not stated  
  > "Astropy (cite: the_astropy_collaboration_astropy_2022)" (Software)
- **NumPy** : Listed in the Software section; specific use not stated  
  > "NumPy (cite: harris_array_2020)" (Software)
- **SciPy** : Listed in the Software section; specific use not stated  
  > "SciPy (cite: virtanen_scipy_2020)" (Software)
- **Matplotlib** : Listed in the Software section; specific use not stated  
  > "Matplotlib (cite: hunter_matplotlib_2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Turbulent Mach number range across clouds | 7 to 45 | not stated | dimensionless | 5 | The calculated Mach numbers range from 7 to 45. |
| Thermal FWHM line width range | ~0.4 to 1.6 | not stated | km/s | 5 | which range from $\sim 0.4$ to 1.6 km s$^{-1}$ |
| Turbulent FWHM line width range (H2CO) | ~4 to 25 | not stated | km/s | 5 | ranges between $\sim 4$ and 25 km s$^{-1}$ |
| rms velocity dispersion range of clouds | ~3-20 | not stated | km/s | 5 | The rms velocity dispersion range of the clouds is $\sim 3-20$ km s$^{-1}$ |
| Average angular offset between peak NH3 (3,3) and H2CO peak | 1.26 | not stated | arcmin | 4 | The average angular offset between the two peaks is 1.26 |
| Average physical offset between peak NH3 (3,3) and H2CO peak | 2.23 | not stated (likely large from distance errors) | pc | 4 | the average physical offset is 2.23 pc |
| H30alpha cloud sizes | 0.3 to 5 | not stated | pc | 6 | The resulting cloud sizes all lie within the range of 0.3 and 5 pc |
| Average r_H30alpha / r_Stromgren ratio | 2.2 | not stated | dimensionless | 6 | with an average $r_{\text{H30}\alpha}/r_S$ ratio of 2.2 |
| Average CO-to-H2 X-factor for bar clouds | 1.59e19 | 0.5e19 (standard deviation over the sample) | cm^-2 (K km/s)^-1 | 11 | the average of which is $(1.59 \pm 0.5) \times 10^{19}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ |
| Mean M(13CO)/M(C18O) for bar clouds (excluding one outlier) | 2 | not stated | dimensionless | 8 | the average ratio is $\text{M}_{\text{C}^{13}\text{O}}/\text{M}_{\text{C}^{18}\text{O}} = 2$ |
| Mean M(13CO)/M(C18O) for the 11 non-bar clouds | 0.5 | not stated | dimensionless | 8 | for the 11 clouds not on the bar, the average ratio is $\text{M}_{\text{C}^{13}\text{O}}/\text{M}_{\text{C}^{18}\text{O}} = 0.5$ |
| Number of clouds likely in the Galactic bar | 9 | not stated | dimensionless | 11 | Our reclassification of G350.18 and G350.10 leaves nine clouds as most likely to lie in the Galactic bar region. |
| 1 sigma rms noise per 0.332 km/s channel | 0.22 to 0.28 Jy/beam (5.2 to 7.7 mK) | not stated | Jy/beam | 1 | varies from about 0.22 to 0.28 Jy beam$^{-1}$ |

## Qualitative findings

- All clouds with detected star formation have relatively low Mach numbers; highly turbulent clouds are not star forming  
  > "we find that all the clouds with detected star formation are at relatively low Mach numbers; in other words, the highly turbulent clouds are not star forming." (5.2 Star Formation and Turbulence)
- Clouds with the highest ammonia temperatures (T13 > 50 K) all lack detected star formation  
  > "the clouds with the highest ammonia temperatures" (5.1 Ammonia and Formaldehyde Thermometers)
- Ammonia temperature correlates with Mach number; formaldehyde temperature does not  
  > "The ammonia temperature is well-correlated with the turbulent Mach number, whereas the formaldehyde temperature is not." (5.1 Ammonia and Formaldehyde Thermometers)
- 12CO optical depths of bar clouds are much lower than those outside the bar  
  > "We see that the optical depths of the clouds on the bar are significantly lower than those not on the bar" (5.5 X-Factor in the Bar)
- SiO abundances in many clouds exceed 1e-10, some 1e-9, indicating shocks  
  > "Many of the clouds in our sample exhibit SiO abundances above 10$^{-10}$, with some exceeding 10$^{-9}$" (4.4.1 SiO)

## Claim tuples

- H: Turbulence suppresses star formation in clouds in the Galactic bar | E: Compare Mach numbers from H2CO widths and temperatures with SFR surface density from H30alpha and 24 micron emission for 20 clouds | R: All clouds with detected star formation have low Mach numbers; the nine highly turbulent bar clouds show no star formation | F: Turbulent pressure is suppressing star formation in the bar clouds | **supported**
- H: What heats the clouds depends on whether star formation is present | E: Compare observed H2CO temperatures with analytic turbulent-heating temperatures | R: Turbulent heating suffices for clouds without star formation and is generally insufficient for star-forming clouds | F: Turbulence dominates heating in non-star-forming clouds; photoelectric heating dominates in star-forming clouds | **supported**
- H: NH3 and H2CO temperatures trace the same gas | E: Compare NH3 (HOPS) and H2CO (ALMA) temperatures and test with RADEX densities | R: No significant correlation; RADEX finds no consistent density for most clouds | F: The two thermometers probe different gas components and each transition traces a different phase | **supported**
- H: The CO-to-H2 X-factor in the Galactic bar is lower than the standard Galactic value | E: Calibrate X-factor from 13CO LTE masses of bar clouds and estimate 12CO optical depth | R: Average X-factor (1.59 +/- 0.5)e19 cm^-2 (K km/s)^-1 and low 12CO optical depth in bar clouds | F: X-factor in the bar is 10-20 times lower than the standard value, likely from low optical depth | **supported**
- H: Broad-line, warm NH3 clouds lie in the Galactic bar | E: Select clouds by NH3 (1,1) width above 10 km/s and check with geometry, distances and derived properties | R: Nine clouds are grouped as bar clouds; G350.18 and G350.10 reclassified; some clouds may be in the disk despite atypical properties | F: Nine clouds likely lie in the bar region with distance and location uncertain | **partially**

## Reasoning

- Why this data: Clouds picked for bright, large-scale NH3 (3,3) emission, implying warm gas, and often broad lines, suggesting a Galactic bar location; ACA observes several tracers of temperature, shocks, SF and turbulence  
  > "The clouds were selected on the basis of bright, large-scale NH~3~ (3,3) emission, which is only observed toward a few objects" (2.1 Sample Selection); "in order to probe physical parameters including temperature, shocks, ionization, star formation, and turbulence, and to investigate where these clouds are located." (Introduction)
- Why this method: 13CO used to define moment-map velocity range because it is detected in all clouds and less contaminated than 12CO; formaldehyde used as temperature probe since the ratio gives gas temperature  
  > "which is observed for all clouds and is less contaminated with foreground and background emission than the more common isotopologue" (2.3 ALMA Maps)
- Alternative: G350.18 and G350.10 first assigned to the bar by line width, then reclassified as probably beyond the bar extent; later retained as a separate population  
  > "we find that their Galactic longitudes are likely beyond the extent of the Galactic bar." (3.1 Clouds Not in the Galactic Bar); "We thus still consider these two clouds to be part of a separate population from the nine clouds in the bar region." (5.4 Where Are the Clouds Located?)
- Alternative: SiO column density computed under LTE treated as a lower limit instead of an actual value because the line is subthermally excited  
  > "we treat the SiO column densities calculated under the assumption of LTE as lower limits on the true column density" (4.4.1 SiO)
- Alternative: No 8 micron SFR derived because of metallicity and size dependence  
  > "so we do not calculate an SFR using the 8 $\mu$m emission from GLIMPSE." (4.3 Star Formation)
- How they decided it was enough: _not stated_
- Limitation (authors): NH3 and H2CO temperatures cannot be compared quantitatively because of a factor of four beam-size difference and peak offsets  
  > "A direct, quantitative comparison between the ammonia and formaldehyde temperature measurements is difficult because of the factor of four difference in beam size between the HOPS and ALMA data" (4.1.3 Ammonia versus Formaldehyde Temperature)
- Limitation (authors): 24 micron SFRs are lower limits because masked pixels around bright sources are interpolated  
  > "We thus treat the resultant SFR values as lower limits." (4.3 Star Formation)
- Limitation (authors): Errors on SFR likely underestimated because of IMF stochasticity for small clusters  
  > "are likely underestimates, as there is additional uncertainty from the stochastic distribution around the initial mass function (IMF) for small clusters." (4.3 Star Formation)
- Limitation (authors): H2CO temperature errors underestimated above 80 K  
  > "These errors are likely underestimates for regions where the gas temperature is greater than about 80 K." (4.1.2 Formaldehyde Temperature)
- Limitation (authors): Distances for non-bar clouds may be highly uncertain  
  > "noting that these distances may be highly uncertain." (3 Cloud Locations)
- Limitation (authors): Single-phase gas assumption is an oversimplification  
  > "The uncertainty is compounded by the assumption of gas in a single phase in our calculations, whereas the clouds are certainly much more complex." (5.3 What is Heating the Clouds?)
- Caveat (inferred, ours): Bar membership rests mainly on NH3 line width above 10 km/s and assumed positions on the bar major axis, so the SF-suppression result partly depends on this selection (circularity)
- Caveat (inferred, ours): The suppression claim relies on detection versus nondetection with no direct inverse Mach-SFR correlation
- Caveat (inferred, ours): Only the TP data were used; the 7 m data and its possible resolution gain are ignored
- Caveat (inferred, ours): H2CO temperatures assume 1e4 cm^-3, while the authors' own RADEX test finds no consistent density for most clouds
- Caveat (inferred, ours): Mach numbers use H2CO temperatures yet ammonia temperature is the one correlating, so the thermal/turbulent interpretation could be affected by gas-phase mixing
- Caveat (inferred, ours): The X-factor depends on 13CO LTE masses and Galactocentric isotope ratios with large coefficients' uncertainty (e.g. +/-82.6 intercept)
- Caveat (inferred, ours): Calzetti and Murphy SFR calibrations are galaxy-scale and may not apply to single clouds

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibrated ACA TP cubes and exact pipeline settings per project and cloud
- Missing: Per-cloud line-free channel ranges, PV paths and 1 arcmin/2 arcmin box positions
- Missing: HOPS NH3 map preparation details (efficiency, baselines)
- Missing: Analysis code and notebook not stated as released
- Missing: Software versions for the Python packages
- Data volume (inferred): Small: ACA total-power cubes for 20 fields (likely a few GB or less) plus Spitzer cutouts and HOPS maps
- Score (inferred): 3/5, Formulas, assumptions and most parameter values are given and the observations are identified by project code, but data public status, per-cloud selections and code are not stated, and results are mostly in tables.
- Rediscovery candidate: no, Public availability of the ACA data is not stated in the paper, and key per-cloud choices (channel ranges, boxes, PV paths) are missing, though the main results are numeric and the recipe is largely complete.

## Links

- Method: (cite: ott_temperature_2005) (Ammonia rotational temperature procedure)
- Method: (cite: ginsburg_dense_2016) (H2CO line ratio to temperature fit from RADEX)
- Method: (cite: purcell_h2o_2012) (HOPS ammonia catalog observation details)
- Companion: (cite: gramze_evidence_2023) (G5 cloud X-factor and optical depth, compared with this work)
- Companion: (cite: longmore_h2o_2017) (HOPS cloud selection and G350.10/G350.18 association)
- Related: HOPS (Mopra H2O Southern Galactic Plane Survey)
- Related: GLIMPSE
- Related: MIPSGAL
- Related: ATOMS
- Related: ALMA-IMF

## Checks

```json
{
 "quotes": 193,
 "quotes_ok": 193,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 148,
  "stated": 117,
  "rate": 0.791
 },
 "evidence_ok": true
}
```
