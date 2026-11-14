# Vortex-like kinematic signal, spirals, and beam smearing effect in the HD 142527 disk

`2021A&A...650A..59B` | Astronomy and Astrophysics 2021 | first author: Boehler, Y. | arXiv: 2103.13474 | DOI: 10.1051/0004-6361/202040089

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Do the 13CO and C18O J=3-2 gas kinematics of the HD 142527 circumbinary disk show deviations from Keplerian rotation consistent with a large vortex around the dust crescent, and can beam smearing explain them instead?  
  > "Using $^{13}$CO and C$^{18}$O J = 3-2 transition lines, we detect kinematic deviations to the Keplerian rotation, which are consistent with the presence of a large vortex around the dust crescent" (abstract); "In Sect. [4](#sec:bias), we examine biases in the measurement of the gas velocity due to beam smearing and inspect how they may compare with the current observations around the horseshoe structure." (1 Introduction)
- Target **HD 142527**: coordinates center of rotation (15h 56min 41.872s -42d 19min 23.694s), 40 mas south and 20 mas west of the phase center  
  > "The binary system HD 142527 is located at 157 $\pm$ 2 pc, based on the stellar parallax (cite: Gaia2018)" (1 Introduction); "kept the value of the center of rotation ($x_0$,$y_0$) $=$ (15h 56min 41.872s -42d 19min 23.694s) located 40 mas south and 20 mas west of the phase center" (2.2 Overview of the gas kinematics); z/distance 157 +/- 2 pc  
  > "The binary system HD 142527 is located at 157 $\pm$ 2 pc, based on the stellar parallax (cite: Gaia2018)" (1 Introduction); "kept the value of the center of rotation ($x_0$,$y_0$) $=$ (15h 56min 41.872s -42d 19min 23.694s) located 40 mas south and 20 mas west of the phase center" (2.2 Overview of the gas kinematics); distance from Gaia stellar parallax (cite: Gaia2018)  
  > "The binary system HD 142527 is located at 157 $\pm$ 2 pc, based on the stellar parallax (cite: Gaia2018)" (1 Introduction); "kept the value of the center of rotation ($x_0$,$y_0$) $=$ (15h 56min 41.872s -42d 19min 23.694s) located 40 mas south and 20 mas west of the phase center" (2.2 Overview of the gas kinematics)

## Data provenance

- ALMA projects: 2012.1.00725.S
- bands: Band 7 (~345 GHz)  
  > "line emission obtained in ALMA band 7 ($\sim345$ GHz)" (2.1 Morphology of the dust and gas emission)
- frequencies and spectral setup: channel width ~110 m/s; wavelength ~0.9 mm  
  > "well below the channel width of $\sim$ 110 m s$^{-1}$ in the observations" (3.1 Preliminary analysis); "at a spatial resolution of 0.3$''$ and at a wavelength of $\sim$ 0.9 millimeter" (6 Conclusion)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.3 arcsec (spatial resolution of the 13CO and C18O J=3-2 data)  
  > "Based on $^{13}$CO and C$^{18}$O J=3-2 data at a spatial resolution of 0.3$''$" (5.1 Observations and theories regarding the possible existence of a large vortex around HD 142527)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 13CO J=3-2 (not stated)
- Line: C18O J=3-2 (not stated)
- Other facility **Gaia**: stellar parallax distance of 157 +/- 2 pc  
  > "is located at 157 $\pm$ 2 pc, based on the stellar parallax (cite: Gaia2018)" (1 Introduction)
- External data: Disk inclination of 27 deg (held fixed in the fits)  
  > "has an inclination of 27$^{\circ}$ (cite: Fuka2013)" (2.1 Morphology of the dust and gas emission) [from (cite: Fuka2013)]
- External data: Stellar parallax distance 157 +/- 2 pc  
  > "is located at 157 $\pm$ 2 pc, based on the stellar parallax (cite: Gaia2018)" (1 Introduction) [from (cite: Gaia2018)]
- External data: Disk and dust parameters used to build the RADMC-3D model  
  > "based on the parameters previously determined in the studies of (cite: Boeh2017), (cite: Soon2019), and (cite: Yen2020)" (4.1 Velocity deviations are also observed in pure Keplerian disks) [from (cite: Boeh2017), (cite: Soon2019), (cite: Yen2020)]
- External data: Dust optical depth of ~2-3 at 0.9 mm in the dust concentration  
  > "which is optically thick at 0.9 millimeter with $\tau_{Dust}$ $\sim$ 2-3 (cite: Muto2015; Boeh2017)" (4.3 Dust also affects the measured gas velocity) [from (cite: Muto2015; Boeh2017)]
- External data: Near-IR and CO spirals S1 and S4 used for comparison with the kinematic arcs  
  > "which may be the dynamical counterpart of the spiral S4 recently observed by (cite: Garg2020)" (2.2 Overview of the gas kinematics) [from (cite: Fuka2013), (cite: Chri2014), (cite: Garg2020)]
- Simulation/model as data: 3D RADMC-3D model of the circumbinary disk in pure Keplerian rotation, convolved to 0.1 and 0.3 arcsec, used to quantify velocity biases from beam smearing  
  > "we carried out a 3D model of the circumbinary disk around HD 142527, performed using the software RADMC3D (cite: Dull2012)" (4.1 Velocity deviations are also observed in pure Keplerian disks); "The resulting signal is then convolved by a Gaussian of 0.1$''$ and 0.3$''$" (4.1 Velocity deviations are also observed in pure Keplerian disks)
- Simulation/model as data: Analytic vortex velocity model (Gaussian velocity profile on elliptic streamlines) compared to the observed velocity residuals  
  > "to use a simple model to constrain the main parameters of a possible vortex, such as its position, size, aspect ratio, and velocity" (3.2 Vortex model); "The exact vortex velocity profile cannot be measured from our current data, and we assume it has a Gaussian profile." (3.2 Vortex model)

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: per pixel in the integrated emission maps, only channels above 5 sigma kept  
  > "we only kept the channels with a signal-to-noise higher than 5 $\sigma$" (2.1 Morphology of the dust and gas emission)
- multiscale scales: _not stated_
- continuum subtraction: interpolation of the dust emission from adjacent line-free channels  
  > "the emission that we subtract is the interpolation of the dust emission from adjacent line-free channels and is essentially a flat spectrum compared to the width of the line" (4.3 Dust also affects the measured gas velocity)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: spatial resolution of 0.3 arcsec (beam shape not stated)  
  > "Based on $^{13}$CO and C$^{18}$O J=3-2 data at a spatial resolution of 0.3$''$" (5.1 Observations and theories regarding the possible existence of a large vortex around HD 142527)
- final rms: _not stated_

### Inherited from earlier work

- Observational setup and data calibration (and the continuum subtraction) of the HD 142527 ALMA data  
  > "We refer the reader to this paper for a description of the observational setup and data calibration." (2.1 Morphology of the dust and gas emission) [from (cite: Boeh2017)]
- Disk and dust parameters of the RADMC-3D toy model, including grain properties  
  > "They were inspired by the analysis in (cite: Boeh2017), using the same grain properties" (A 3D toy model for HD 142527) [from (cite: Boeh2017), (cite: Soon2019), (cite: Yen2020)]
- Eddy MCMC code used for the Keplerian fit  
  > "We used the software Eddy described in (cite: Teag2019a) which is based on an MCMC method" (2.2 Overview of the gas kinematics) [from (cite: Teag2019a)]
- Intensity-weighted velocity (moment 1) method in CASA  
  > "The velocity was obtained using the intensity weighted method, or moment 1 of the velocity in CASA (cite: McMu2007)." (2.2 Overview of the gas kinematics) [from (cite: McMu2007)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging recipe of the 2012.1.00725.S data (CASA version, calibrators, self-calibration, robust, uv taper, cell and image size, clean threshold): all deferred to Boeh2017
- Synthesized beam size and shape and per-channel rms of the 13CO and C18O cubes
- Line-free channels used for continuum subtraction and the exact channel range used for moment 1
- How the 5 sigma per-pixel threshold was set (rms estimate, which channels)
- Eddy settings: priors, walkers, burn-in, radial bins, masks, pixel selection and any smoothing
- Chi-square fit setup along the major and minor axes (sampling, azimuth range, errors used)
- How the vortex parameters were chosen (no formal fit is described) and how models A, B and C were compared with the data quantitatively
- RADMC-3D setup: stellar and companion properties, dust opacities, gas temperature and abundances, line setup, velocity binning used for the 25 m/s case versus 10 m/s
- How the model velocity maps were measured (moment 1 clipping, same as observations or not)

## Analysis recipe

1. **Make 13CO and C18O integrated-intensity and velocity maps**: Moment 0 maps and intensity-weighted (moment 1) velocity maps in CASA, keeping per pixel only channels above 5 sigma  
  > "The velocity was obtained using the intensity weighted method, or moment 1 of the velocity in CASA (cite: McMu2007)." (2.2 Overview of the gas kinematics); "we only kept the channels with a signal-to-noise higher than 5 $\sigma$" (2.1 Morphology of the dust and gas emission)
   - software: CASA
   - parameter: channel width ~110 m/s  
  > "well below the channel width of $\sim$ 110 m s$^{-1}$ in the observations" (3.1 Preliminary analysis)
   - fitting: _not stated_
   - validation: Compared with the peak-emission method; results in general agreement  
  > "The results between both methods and molecules are in general agreement" (Comparison of the peak and intensity weighted methods)
2. **Fit Keplerian rotation to the velocity map**: Eddy MCMC fit at R >= 150 au to fix center of rotation and PA, then chi-square fit along major and minor axes between 100 and 400 au for stellar mass and systemic velocity  
  > "We used the software Eddy described in (cite: Teag2019a) which is based on an MCMC method, and takes into account the signal-to-noise in each pixel of the image." (2.2 Overview of the gas kinematics); "Second, we used a chi-square method along the minor and major axes of the disk to fit the mass and the systemic velocity V$_{lsr}$ of the system between 100 and 400 au" (2.2 Overview of the gas kinematics)
   - software: Eddy
   - parameter: inclination fixed to 27 deg; fit binary mass, systemic velocity, PA and center of rotation  
  > "We fixed the disk inclination to 27$^{\circ}$ and fit the mass of the binary, the systemic velocity of the system, the PA of the disk, and the center of rotation." (2.2 Overview of the gas kinematics)
   - parameter: inner 100 au discarded  
  > "We discarded the inner 100 au of the system" (2.2 Overview of the gas kinematics)
   - parameter: first step uses R >= 150 au  
  > "we used the MCMC code Eddy well outside from the cavity (i. e., R $\geq$ 150 au)" (2.2 Overview of the gas kinematics)
   - assumption: geometrically thin disk (gas scale height not fitted)  
  > "We used a geometrically thin disk for the fit because we could not precisely constrain the gas scale height" (2.2 Overview of the gas kinematics)
   - assumption: distance of 157 pc  
  > "taking a distance of 157 pc for the system" (2.1 Morphology of the dust and gas emission)
   - fitting: MCMC (Eddy) weighted by per-pixel signal-to-noise for the center and PA; chi-square without radial S/N weighting for mass and V_lsr; priors and likelihood not stated  
  > "without taking radial variations of the signal-to-noise ratio into account" (2.2 Overview of the gas kinematics); "takes into account the signal-to-noise in each pixel of the image" (2.2 Overview of the gas kinematics)
   - validation: Fit result compared across radial ranges; kinematic features checked to be independent of the fitting procedure  
  > "Large discrepancies were found depending on the radial distance range considered." (2.2 Overview of the gas kinematics); "They are present independently of the exact fitting procedure used" (2.2 Overview of the gas kinematics)
3. **Map velocity deviations from Keplerian rotation and identify kinematic features**: Subtract projected Keplerian velocity to get a 2D residual map and radial cuts at different azimuths; compare 13CO and C18O  
  > "Radial cuts of the velocity deviations at different azimuthal angles are shown in" (3.1 Preliminary analysis); "The velocities measured using the $^{13}$CO and C$^{18}$O lines give very similar values, with differences no larger than 20-30 m s$^{-1}$ between $\sim$ 100 and $\sim$ 350 au." (3.1 Preliminary analysis)
   - software: Eddy
   - assumption: vertical motions neglected in the radial Doppler-shifted structure  
  > "at first order, they can probably be neglected in the radial Doppler-shifted structure" (3.1 Preliminary analysis)
   - fitting: _not stated_
   - validation: Both isotopologues give consistent velocities  
  > "This suggests that both isotopologues emit from a similar altitude" (3.1 Preliminary analysis)
4. **Compare the velocity residuals with an analytic vortex model**: Vortex with Gaussian velocity profile on elliptic streamlines, projected along the line of sight; three configurations (A, B, C) compared with the observed polar map between 100 and 350 au  
  > "The exact vortex velocity profile cannot be measured from our current data, and we assume it has a Gaussian profile." (3.2 Vortex model); "we applied our vortex prescription to three different possibilities, whose parameters are given in Table" (3.3 Comparison of the observations with the vortex model)
   - parameter: R_v = 42 au, W_v = 26 au, azimuthal-to-radial aspect ratio ~5 (models A and B)  
  > "with R$_v$ $=$ 42 au, W$_v$ $=$ 26 au, and an azimuthal-to-radial aspect ratio of $\sim$ 5" (3.3 Comparison of the observations with the vortex model)
   - parameter: maximum vortex velocity set to 350 m/s  
  > "The maximum velocity reached by the vortex is set to 350 m s$^{-1}$" (3.3 Comparison of the observations with the vortex model)
   - parameter: Model A centered at r = 185 au, theta = 50 deg; Model B at r = 185 au, theta = -20 deg  
  > "in model A and at the position of the secondary maximum ($r =$ 185 au, $\theta =$ -20$^{\circ}$) in model B" (3.3 Comparison of the observations with the vortex model)
   - assumption: Vmax comparable to local sound speed for T = 30-40 K, mu = 2.3  
  > "This value is comparable to the local sound speed for a temperature of 30-40 K at the horseshoe position" (3.3 Comparison of the observations with the vortex model)
   - fitting: _not stated_
   - validation: Single large vortex near the secondary dust maximum favored over the two-vortex Model C  
  > "our comparison favors the option of a large and single vortex" (3.3 Comparison of the observations with the vortex model)
5. **Quantify beam-smearing velocity biases with a Keplerian radiative transfer model**: RADMC-3D 3D model of the circumbinary disk in pure Keplerian rotation, ray-traced and convolved to 0.1 and 0.3 arcsec; measure velocity deviations and the beam-edge emission ratio I_out/I_in  
  > "The resulting signal is then convolved by a Gaussian of 0.1$''$ and 0.3$''$ in order to reproduce typical spatial resolutions of molecular lines in ALMA observations." (4.1 Velocity deviations are also observed in pure Keplerian disks); "this variation can be estimated by the emission ratio I$_\mathrm{out}$/I$_\mathrm{in}$ between the outer and inner edges of the synthesized beams" (4.2 Line intensity gradients skew measured velocities through beam smearing)
   - software: RADMC-3D
   - parameter: grid cells of 1 au in radius, 2 deg in azimuth and 1 deg in elevation  
  > "using cells of 1 au in radius, 2$^\circ$ in azimuth and 1$^\circ$ in elevation" (A 3D toy model for HD 142527)
   - parameter: ray-tracing pixel size 20 mas, velocity resolution 10 m/s  
  > "we performed the ray-tracing in a square grid with a pixel size of 20 mas and a velocity resolution of 10 m s$^{-1}$" (A 3D toy model for HD 142527)
   - parameter: ideal observations without noise at 25 m/s velocity resolution for Figure 6  
  > "(i.e., without noise and at a velocity resolution of 25 m s$^{-1}$)" (4.1 Velocity deviations are also observed in pure Keplerian disks)
   - assumption: pure Keplerian rotation around a single star of 2.36 Msun, inclination 27 deg, PA -19 deg  
  > "the gas is in pure Keplerian rotation around a single star of 2.36 $M_\odot$" (A 3D toy model for HD 142527); "We assume a disk inclination of 27$^\circ$ and a PA of -19$^\circ$." (A 3D toy model for HD 142527)
   - assumption: no shadowing by the inner disk in the temperature calculation  
  > "No shadowing effect by the inner disk has been taken into account in this step." (A 3D toy model for HD 142527)
   - fitting: _not stated_
   - validation: Model deviations compared with the observed pattern at R > 150 au  
  > "At a radius larger than 150 au, the observed kinematic signal is similar to the velocity pattern seen in the pure Keplerian model at 0.3$''$" (4.1 Velocity deviations are also observed in pure Keplerian disks)
6. **Test whether beam smearing, dust and continuum subtraction, and pressure gradients can mimic the vortex signal**: Compare velocity deviations in the model by radial region with the flux ratio after continuum subtraction, then compare model and observed amplitudes and radii of the feature  
  > "the measured velocity deviations are in good agreement with the flux variations measured after continuum-subtraction" (4.3 Dust also affects the measured gas velocity); "these artifacts are of lower amplitude in our model, with velocities reaching 90 m s$^{-1}$ on the inner side and 20 m s$^{-1}$ on the outer side" (4.4 Beam smearing and gas pressure gradients may also explain the vortex-like kinematic feature)
   - software: RADMC-3D
   - assumption: gas surface density three to five times larger on the northern side of the disk, with radial pressure gradients adding non-Keplerian motions  
  > "With a gas surface density three to five times larger on the northern side of the disk, significant non-Keplerian motions may appear" (4.4 Beam smearing and gas pressure gradients may also explain the vortex-like kinematic feature)
   - fitting: _not stated_
   - validation: Beam smearing alone judged unlikely to explain the signal; beam smearing plus pressure gradients cannot be excluded  
  > "It therefore appears unlikely that the beam smearing effect alone can produce the azimuthal velocity deviations." (4.4 Beam smearing and gas pressure gradients may also explain the vortex-like kinematic feature)

## Software

- **CASA** : moment 1 (intensity-weighted) velocity maps  
  > "moment 1 of the velocity in CASA (cite: McMu2007)" (2.2 Overview of the gas kinematics)
- **Eddy** : MCMC fit of Keplerian rotation (center, PA) to the velocity map  
  > "We used the software Eddy described in (cite: Teag2019a) which is based on an MCMC method" (2.2 Overview of the gas kinematics)
- **RADMC-3D** : 3D radiative transfer model of the disk to test beam smearing  
  > "performed using the software RADMC3D (cite: Dull2012)" (4.1 Velocity deviations are also observed in pure Keplerian disks)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Binary mass, R = 100-200 au (Eddy) | 2.53 | 0.04 | Msun | 2 | For R between 100 and 200 au, we obtain a binary mass of 2.53 $\pm$ 0.04 M$_\odot$ |
| Binary mass, R > 200 au (Eddy) | 2.29 | 0.07 | Msun | 2 | where for R $>$ 200 au, we obtain a binary mass of 2.29 $\pm$ 0.07 M$_\odot$ |
| Binary mass, fit over the whole circumbinary disk | 2.48 | 0.03 | Msun | 2 | yielding a binary mass of 2.48 $\pm$ 0.03 M$_\odot$ |
| Binary mass, adopted chi-square fit 100-400 au | 2.36 | 0.07 | Msun | 2 | and obtain a binary mass of 2.36 $\pm$ 0.07 M$_\odot$, and a V$_{lsr}$ of 3730 $\pm$ 20 m s$^{-1}$ |
| Systemic velocity V_lsr | 3730 | 20 | m/s | 2 | and a V$_{lsr}$ of 3730 $\pm$ 20 m s$^{-1}$ |
| Disk position angle (Eddy, R >= 150 au) | 161.1 | 0.4 | deg | 2 | of the PA $=$ 161.1$^{\circ}$ $\pm$ 0.4$^{\circ}$ of the disk |
| Dust continuum peak (theta = 52 deg) | 93 mJy/beam (34.0 K) | not stated | mJy/beam | 0 | a maximum in emission of 93 mJy beam$^{-1}$, or 34.0 K in brightness temperature |
| Dust continuum secondary maximum (theta = -20 deg) | 71 mJy/beam (27.5 K) | not stated | mJy/beam | 0 | with a value of 71 mJy beam$^{-1}$ (or 27.5 K) |
| Maximum projected velocity deviation of the main kinematic structure | 160 | not stated | m/s | 3 | a large radial Doppler-shifted structure in the north of the disk with projected velocities up to 160 m s$^{-1}$ |
| Velocity deviation of the main structure after deprojection | 0.35 | not stated | km/s | 3 | or of 0.35 km s$^{-1}$ after deprojection, about 10% of the background Keplerian rotation |
| Transition radius between super- and sub-Keplerian regimes | 185 | not stated | au | 3 | The transition radius between these two regimes is at 185 au |
| Maximum projected velocity deviations along the spiral arcs | ~50 | not stated | m/s | 3 | All these arcs and spirals have maximum projected velocity deviations on the order of 50 m s$^{-1}$. |
| Vortex radial parameters R_v and W_v | R_v = 42, W_v = 26 | not stated | au | 4 | with R$_v$ $=$ 42 au, W$_v$ $=$ 26 au |
| Vortex azimuthal-to-radial aspect ratio | ~5 | not stated | dimensionless | 4 | an azimuthal-to-radial aspect ratio of $\sim$ 5 |
| Vortex extent (radial and azimuthal) | +/-40 au radially, ~200 deg azimuthally | not stated | au, deg | 4 | Its very large size, of about $\pm$ 40 au radially and $\sim$ 200$^\circ$ azimuthally |
| Vortex maximum velocity adopted (deprojected) | 350 | not stated | m/s | 4 | The maximum velocity reached by the vortex is set to 350 m s$^{-1}$ |
| Beam-smearing velocity deviation in Keplerian model at 0.3 arcsec | 20-80 | not stated | m/s | 5 | instead of only 20-80 m s$^{-1}$ in our models |
| Ratio of velocity deviations at 0.3 arcsec to 0.1 arcsec along northern major axis | ~3 | not stated | dimensionless | 5 | the velocity deviations at 0.1$''$ are about three times smaller than at 0.3$''$ |
| Beam-smearing artifact amplitude at inner and outer side of the model feature | 90 (inner), 20 (outer) | not stated | m/s | 6 | with velocities reaching 90 m s$^{-1}$ on the inner side and 20 m s$^{-1}$ on the outer side |

## Qualitative findings

- Three spiral-like kinematic features are detected in the outer disk, two probably related to spirals S1 and S4  
  > "Three spiral-like kinematic features are also detected in the outer region of the circumbinary disk at R between 200 and 450 au." (6 Conclusion)
- Pure Keplerian rotation models already show measurable velocity deviations because of finite resolution and radial emission gradients (beam smearing)  
  > "The spurious velocity deviations in the models are then explained by the finite spatial resolution of the observations and the radial gradient of the molecular line emission." (4.2 Line intensity gradients skew measured velocities through beam smearing)
- Higher resolution (0.1 arcsec) would reduce the beam-smearing effect by a factor of ~3  
  > "would decrease by a factor of $\sim$ 3 the current beam smearing effect along the major axis of the disk" (6 Conclusion)

## Claim tuples

- H: Does the gas kinematics around the HD 142527 dust crescent show a vortex signature? | E: Fit Keplerian rotation to 13CO moment 1 maps, map residuals, compare with an analytic vortex model (models A-C) | R: Radial Doppler-shifted structure with projected deviations up to ~160 m/s; model with a large single vortex (R_v = 42 au, aspect ratio ~5, Vmax 350 m/s) reproduces its morphology better than two smaller vortices | F: The signal is consistent with a large anticyclonic vortex near R ~185 au | **partially**
- H: Are there spiral kinematic features in the outer disk? | E: Residual velocity map after Keplerian subtraction, compared with published spirals | R: Redshifted and blueshifted arcs of ~180 deg with deviations of ~50 m/s | F: Three spiral-like kinematic features, two linked to spirals S1 and S4 | **supported**
- H: Can beam smearing alone produce the observed azimuthal velocity deviations? | E: RADMC-3D pure Keplerian model convolved to 0.1 and 0.3 arcsec, compared with the observed deviations | R: Model artifacts reach 90 m/s (inner) and 20 m/s (outer) at 215 au versus ~150-160 m/s at 185 au in the observations | F: Beam smearing alone is unlikely to explain the signal | **supported**
- H: Can beam smearing combined with gas pressure gradients mimic the vortex signal, so the two scenarios cannot be separated? | E: Compare model artifacts and expected pressure-gradient deviations with the observed feature | R: Both processes predict super-Keplerian inside and sub-Keplerian outside the horseshoe, and blueshifted emission at similar angles | F: The vortex and the beam-smearing-plus-pressure-gradient scenarios cannot currently be distinguished at 0.3 arcsec | **partially**
- H: Does higher spatial resolution reduce velocity biases from beam smearing? | E: Compare model velocity deviations at 0.1 and 0.3 arcsec | R: Deviations at 0.1 arcsec about three times smaller | F: Observations at 0.1 arcsec would reduce the beam smearing effect by a factor of ~3 | **supported**

## Reasoning

- Why this data: HD 142527 is a good target for finding a vortex because of dust trapping indications and the large bright disk  
  > "make of this system the perfect target to look for the existence of a vortex in a protoplanetary disk" (1 Introduction)
- Why this method: Intensity-weighted velocity (moment 1) chosen because the peak method was more sensitive to rms noise  
  > "This is the method we favored in the present work as the peak emission method appeared more sensitive to the rms noise within our data." (2.2 Overview of the gas kinematics)
- Alternative: Two smaller vortices at the two dust maxima (Model C) rejected: does not reproduce the morphology and would have a small aspect ratio  
  > "The model with two vortices, on the contrary, does not reproduce the morphology of the kinematic signal." (3.3 Comparison of the observations with the vortex model)
- Alternative: Peak-emission velocity method considered but not adopted  
  > "the peak emission method appeared more sensitive to the rms noise within our data" (2.2 Overview of the gas kinematics)
- Alternative: Global fit weighted toward small radii rejected to avoid biasing toward specific radii  
  > "Therefore, to avoid biasing toward any specific radii, we proceeded in two steps." (2.2 Overview of the gas kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Vortex and beam-smearing-plus-pressure-gradient scenarios currently very difficult to differentiate  
  > "It is then currently very difficult to assess if the signal is due to a real vortex or is produced by beam smearing associated with gas pressure gradients." (4.4 Beam smearing and gas pressure gradients may also explain the vortex-like kinematic feature)
- Limitation (authors): Vortex velocity profile not measurable from the data (Gaussian assumed)  
  > "The exact vortex velocity profile cannot be measured from our current data, and we assume it has a Gaussian profile." (3.2 Vortex model)
- Limitation (authors): Gas scale height could not be constrained, thin disk used  
  > "We used a geometrically thin disk for the fit because we could not precisely constrain the gas scale height" (2.2 Overview of the gas kinematics)
- Limitation (authors): Line emission in the north partly lost to continuum subtraction and dust absorption  
  > "is an artifact mainly produced by the continuum subtraction method" (2.1 Morphology of the dust and gas emission)
- Caveat (inferred, ours): The vortex model is compared by eye to the residual map; no fit, uncertainties or goodness of fit are given for the vortex parameters
- Caveat (inferred, ours): Derived binary mass varies from 2.29 to 2.53 Msun depending on radial range, so residual maps depend on the Keplerian fit choice
- Caveat (inferred, ours): Beam-smearing model is a toy model not matched to the actual beam, noise, continuum subtraction and channelization of the data
- Caveat (inferred, ours): Observational setup, calibration and imaging are not described here, so the data quality cannot be judged from this paper alone
- Caveat (inferred, ours): Only the 13CO and C18O J=3-2 lines at a single resolution are available, limiting separation of vortex and artifacts

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters of the 2012.1.00725.S data (described only in Boeh2017)
- Missing: Synthesized beam, rms and exact moment-1 clipping used
- Missing: Eddy fit configuration and chi-square fit details
- Missing: Procedure for choosing and comparing vortex model parameters
- Missing: RADMC-3D input files and line-modeling details
- Data volume (inferred): One ALMA Band 7 project (2012.1.00725.S); probably tens of GB raw, a few GB of calibrated measurement sets and cubes
- Score (inferred): 3/5, Project code, Keplerian fit steps and numeric results are given, and the vortex parameters are in Table 1, but calibration and imaging are deferred to Boeh2017 and the vortex comparison is not a formal fit.
- Rediscovery candidate: no, Imaging settings are missing and the main vortex claim rests on a by-eye model comparison rather than a fully specified numeric recipe, although the Keplerian mass and V_lsr fit could be redone.

## Links

- Method: (cite: Boeh2017) (Observational setup, calibration and earlier analysis of the same ALMA data)
- Method: (cite: Teag2019a) (Eddy code used for the Keplerian fit)
- Method: (cite: Teag2018c) (Velocity measurement methods, peak emission and effect of continuum subtraction)
- Method: (cite: McMu2007) (CASA, used for the moment 1 velocity maps)
- Method: (cite: Dull2012) (RADMC-3D radiative transfer code)
- Companion: (cite: Yen2020) (C18O J=1-0 kinematics and model parameters of HD 142527)
- Companion: (cite: Soon2019) (Dust spectral index variation and model parameters)
- Companion: (cite: Garg2020) (12CO J=2-1 spirals S1 and S4 compared with the kinematic arcs)
- Companion: (cite: Muto2015) (Horseshoe dust and gas surface density)
- Related: ALMA project 2012.1.00725.S

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
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 67,
  "rate": 0.65
 },
 "evidence_ok": true
}
```
